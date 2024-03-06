# Altibase 7.1.0.9.1 Patch Notes

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Fixed Bugs](#fixed-bugs)
    - [BUG-50621 함수기반 인덱스를 생성하는 수식이 지나치게 긴 경우, 서버 비정상 종료가 발생합니다.](#bug-50621)
    - [BUG-50659 ORDER BY 가 SELECT 절의 외부 참조가 있는 SUBQUERY를 alias로 참조 시 결과 오류가 발생합니다.](#bug-50659)
    - [BUG-50663 LobCursorList 에서 ID_SERIAL_XXX 함수를 제거합니다.](#bug-50663)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Fixed Bugs
==========

### BUG-50621<a name=bug-50621></a> 함수기반 인덱스를 생성하는 수식이 지나치게 긴 경우, 서버 비정상 종료가 발생합니다.

-   **module** : qp-ddl-dcl-pvo

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : 함수기반 인덱스를 생성하는 수식이 지나치게 긴 경우, 서버가 비정상 종료되는 문제를 수정합니다.
    
-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**
    
    -   **예상 결과**
    
-   **Workaround**

-   **변경사항**
    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50659<a name=bug-50659></a> ORDER BY 가 SELECT 절의 외부 참조가 있는 SUBQUERY를 alias로 참조 시 결과 오류가 발생합니다.

-   **module** : qp

-   **Category** : Reliability

-   **재현 빈도** : Always

-   **설명** : ORDER BY 절에서 SELECT 절의 외부 참조가 있는 서브쿼리를 alias로 참조할 때 결과 오류가 발생하는 문제를 수정합니다.
    
    이 버그는 아래의 4가지 조건이 모두 만족한 경우에만 발생합니다.
    
    1. 디스크 테이블에서 ORDER BY시 디스크 템프를 사용한 경우
    2. 서브쿼리의 alias를 ORDER BY에 사용한 경우
    3. SELECT의 target에 서브쿼리가 2개 이상 사용되고, 그 중에 ORDER BY 절에 사용된 alias 의 서브쿼리보다 앞에 있는 서브쿼리에서 외부참조 컬럼이 사용된 경우 
    4. 서브쿼리에 사용된 외부 참조 컬럼이 FROM 절의 인라인 뷰(Inline View)나 일반 뷰에 사용되면서, 뷰머지(View Merge)로 동작한 경우
    
- **재현 방법**

  - **재현 절차**

    ```sql
    drop table tb1;
    drop table tb2;
    drop table tb3;
    CREATE TABLE TB1 ( TB1_C1 VARCHAR(10) PRIMARY KEY,
                       TB1_C2 VARCHAR(10) NOT NULL,
                       TB1_C3 VARCHAR(10) NOT NULL )
    tablespace sys_tbs_disk_data
    ;
    insert into tb1 values ('aaa','aaa','aaa');
    insert into tb1 values ('bbb','aaa','bbb');
    insert into tb1 values ('ccc','aaa','ccc');
    insert into tb1 values ('ddd','ccc','ddd');
    insert into tb1 values ('eee','eee','eee');
    CREATE TABLE TB2 ( TB2_C1 VARCHAR(10) PRIMARY KEY,
                       TB2_C2 VARCHAR(10) NOT NULL,
                       TB2_C3 VARCHAR(10) NOT NULL,
                       TB2_C4 NUMERIC(5,2),
                       TB2_C5 DATE DEFAULT SYSDATE )
    tablespace sys_tbs_disk_data;
    insert into tb2 values('aaa','aaa','aaa',1,sysdate);
    insert into tb2 values('bbb','aaa','bbb',1,sysdate);
    insert into tb2 values('ccc','bbb','ccc',1,sysdate);
    insert into tb2 values('eee','eee','eee',1,sysdate);
    insert into tb2 values('fff','eee','fff',1,sysdate);
    CREATE TABLE Tb3 ( TB3_C1 VARCHAR(10) PRIMARY KEY,
                      TB3_C2 VARCHAR(10) NOT NULL )
    tablespace sys_tbs_disk_data;
    insert into tb3 values ( 'aaa','aaa' );
    insert into tb3 values ( 'bbb','bbb' );
    insert into tb3 values ( 'ccc','ccc' );
    insert into tb3 values ( 'fff','fff' );
    SELECT 
     (SELECT X.TB1_C3 FROM TB1 X WHERE X.TB1_C1 = A.TB2_C1)
    ,(SELECT X.TB1_C2 FROM TB1 X WHERE X.TB1_C1 = A.TB2_C1)  AS AAAA
    FROM TB2 A
    WHERE EXISTS (SELECT  1 FROM TB3 X WHERE X.TB3_C2 = A.TB2_C1 )
    ORDER BY AAAA ASC;
    ```

  - **수행 결과**

    ```sql
    aaa
    ccc
    bbb
    4 rows selected.
    ```

  -   **예상 결과**

      ```sql
      aaa         aaa
      ccc         aaa
      bbb         aaa
      4 rows selected.
      ```

- **Workaround**

  ```sql
  SELECT 
   (SELECT X.TB1_C3 FROM TB1 X WHERE X.TB1_C1 = A.TB2_C1)
  ,(SELECT X.TB1_C2 FROM TB1 X WHERE X.TB1_C1 = A.TB2_C1)  AS AAAA
  FROM TB2 A
  WHERE EXISTS (SELECT /*+ no_unnest */ 1 FROM TB3 X WHERE X.TB3_C2 = A.TB2_C1 )
  ORDER BY AAAA ASC;
  ```

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50663<a name=bug-50663></a> LobCursorList 에서 ID_SERIAL_XXX 함수를 제거합니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Unknown

-   **설명** : 내부적으로 LobCursorList를 관리하기 위해 사용되는 함수들의 동시성 문제가 발견되어, 동시성 제어를 위한 함수로 수정하였습니다.

-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**
    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 7.1.0.9.1        | 6.5.1                   | 8.11.1       | 7.1.7               | 7.4.7                        |

 > Altibase 7.1 패치 버전별 히스토리는 [Version_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.1/Altibase_7_1_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의
> 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는
> 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

> 패치를 롤백하려는 경우, [메타다운그레이드](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Installation%20Guide.md#%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9Cmeta-downgrade)를 참고한다.

#### CM protocol Version

통신 프로토콜 버전은 변경되지 않았다.

#### Replication protocol Version

Replication 프로토콜 버전은 변경되지 않았다.

### 프로퍼티

#### 추가된 프로퍼티

#### 변경된 프로퍼티

#### 삭제된 프로퍼티

### 성능 뷰

#### 추가된 성능 뷰

#### 변경된 성능 뷰

#### 삭제된 성능 뷰
