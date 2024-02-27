Altibase 7.3.0.0.5 Patch Notes
================================
<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Fixed Bugs](#fixed-bugs)
    - [BUG-50130 패키지 인스톨러 설치시, 저장 패키지 생성 구문에서 오류가 발생합니다.](#bug-50130)
    - [BUG-50767 alter system set으로 REPLICATION\_ACK\_XLOG\_COUNT 값을 변경 시 값이 변경되지 않습니다.](#bug-50767)
    - [BUG-50768 인덱스의 DISABLE 상태를 V\$에 출력합니다.](#bug-50768)
    - [BUG-50778 column info Protocol 처리 시 column count 함수 예외 처리 추가](#bug-50778)
    - [BUG-50783 procedure 실행 중 Table에 DDL 발생 시 Invalid use of host variables error 발생](#bug-50783)

- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#호환성)
    - [프로퍼티](#프로퍼티)
    - [성능 뷰](#성능-뷰)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Fixed Bugs
==========

### BUG-50130<a name=bug-50130></a> 패키지 인스톨러 설치시, 저장 패키지 생성 구문에서 오류가 발생합니다.

- **module** : qp
- **Category** : Functional Error
- **재현 빈도** : Always
- **설명** : 저장 패키지 생성 구문에 불필요한 파일이 포함되어 있어서, 주석처리하고 수행되지 않도록 수정합니다.
- **재현 방법**
  - **재현 절차**
  - **수행 결과**
  - **예상 결과**
- **Workaround**
- **변경사항**
  - Performance view
  - Property
  - Compile Option
  - Error Code

### BUG-50767<a name=bug-50767></a> alter system set으로 REPLICATION\_ACK\_XLOG\_COUNT 값을 변경 시 값이 변경되지 않습니다.

-   **module** : rp
-   **Category** : Functional Error
-   **재현 빈도** : Always
-   **설명** : alter system set으로 REPLICATION\_ACK\_XLOG\_COUNT 값을 변경할 때 값이 변경되지 않는 문제를 수정하였습니다.
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

### BUG-50768<a name=bug-50768></a> 인덱스의 DISABLE 상태를 V\$에 출력합니다.

-   **module** : sm

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : 인덱스의 DISABLE 상태를 V$MEM_BTREE_HEADER, V$VOL_BTREE_HEADER, V$DISK_BTREE_HEADER에 출력합니다.

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

### BUG-50778<a name=bug-50778></a> column info Protocol 처리 시 column count 함수 예외 처리 추가

-   **module** : qp

-   **Category** : Fatal

-   **재현 빈도** : Rare

-   **설명** : column info Protocol 처리 시 column count 함수 예외 처리를 추가하였습니다.
    
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

### BUG-50783<a name=bug-50783></a> procedure 실행 중 Table에 DDL 발생 시 Invalid use of host variables error 발생

-   **module** : qp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : procedure 실행 중 Table에  DDL 발생 시  Invalid use of host variables error가 발생하는 것을 수정하였습니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    - session 1
    create table t1 (i1 integer);
    insert into t1 values(1);
    create or replace procedure proc1 as
    var1 integer;
    var2 integer;
    begin
      var1 := 1;
      for i in 1 .. 10 loop
      select var1 into var2 from t1;
      println(var2);
      sleep(2);
      var1 := var1 + 1;
      end loop;
    end;
    /
    exec proc1;
    -- session 2
    alter table t1 add (i2 integer);
    alter table t1 drop i2;
    ```

  - **수행 결과**

    ```sql
    [ERR-3123B : Invalid use of host variables
    0001 : select :B0 from T1;
                 ^  ^
    at "SYS.PROC1", line 7]
    ```

  -   **예상 결과**

      ```sql
      no error
      ```

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
| 7.3.0.0.5        | 7.3.0                   | 9.3.1        | 7.1.8               | 7.4.9                        |

> Altibase 7.3 패치 버전별 히스토리는 [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.3/Altibase_7_3_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

> 패치를 롤백하려는 경우, [메타다운그레이드](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/Installation%20Guide.md#%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9Cmeta-downgrade)를 참고한다.

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
