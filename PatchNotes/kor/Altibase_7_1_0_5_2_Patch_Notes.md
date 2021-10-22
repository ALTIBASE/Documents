
**Table of Contents**  

- [Altibase 7.1.0.5.2 Patch Notes](#altibase-71052-patch-notes)
  - [New Features](#new-features)
    - [BUG-48380 newJDBC fetch 성능을 개선합니다.](#bug-48380newjdbc-fetch-%EC%84%B1%EB%8A%A5%EC%9D%84-%EA%B0%9C%EC%84%A0%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-48510 메모리 테이블 INDEX SCAN, FULL SCAN 성능을 개선합니다.](#bug-48510%EB%A9%94%EB%AA%A8%EB%A6%AC-%ED%85%8C%EC%9D%B4%EB%B8%94-index-scan-full-scan-%EC%84%B1%EB%8A%A5%EC%9D%84-%EA%B0%9C%EC%84%A0%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-42525 installer 에서 DB\_NAME 변경시 알파벳이 아닌 값이 들어올 경우 DB 가 생성되지 않습니다.](#bug-42525installer-%EC%97%90%EC%84%9C-db%5C_name-%EB%B3%80%EA%B2%BD%EC%8B%9C-%EC%95%8C%ED%8C%8C%EB%B2%B3%EC%9D%B4-%EC%95%84%EB%8B%8C-%EA%B0%92%EC%9D%B4-%EB%93%A4%EC%96%B4%EC%98%AC-%EA%B2%BD%EC%9A%B0-db-%EA%B0%80-%EC%83%9D%EC%84%B1%EB%90%98%EC%A7%80-%EC%95%8A%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-48433 dumptrc 수행 시 altibase\_error.log 에 콜스택과 OS 에러 메시지가 섞이는 문제를 개선합니다.](#bug-48433dumptrc-%EC%88%98%ED%96%89-%EC%8B%9C-altibase%5C_errorlog-%EC%97%90-%EC%BD%9C%EC%8A%A4%ED%83%9D%EA%B3%BC-os-%EC%97%90%EB%9F%AC-%EB%A9%94%EC%8B%9C%EC%A7%80%EA%B0%80-%EC%84%9E%EC%9D%B4%EB%8A%94-%EB%AC%B8%EC%A0%9C%EB%A5%BC-%EA%B0%9C%EC%84%A0%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-48523 세션 종료 시 statement 객체가 정리되지 않은 경우 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-48523%EC%84%B8%EC%85%98-%EC%A2%85%EB%A3%8C-%EC%8B%9C-statement-%EA%B0%9D%EC%B2%B4%EA%B0%80-%EC%A0%95%EB%A6%AC%EB%90%98%EC%A7%80-%EC%95%8A%EC%9D%80-%EA%B2%BD%EC%9A%B0-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-48526 임의의 인덱스 키가 WHERE 절에 2번 이상 사용되고 OR 조건에 호스트 변수를 사용한 경우 결과 오류가 발생합니다.](#bug-48526%EC%9E%84%EC%9D%98%EC%9D%98-%EC%9D%B8%EB%8D%B1%EC%8A%A4-%ED%82%A4%EA%B0%80-where-%EC%A0%88%EC%97%90-2%EB%B2%88-%EC%9D%B4%EC%83%81-%EC%82%AC%EC%9A%A9%EB%90%98%EA%B3%A0-or-%EC%A1%B0%EA%B1%B4%EC%97%90-%ED%98%B8%EC%8A%A4%ED%8A%B8-%EB%B3%80%EC%88%98%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%9C-%EA%B2%BD%EC%9A%B0-%EA%B2%B0%EA%B3%BC-%EC%98%A4%EB%A5%98%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)



Altibase 7.1.0.5.2 Patch Notes
================================

New Features
------------

### BUG-48380 newJDBC fetch 성능을 개선합니다.

-   **module** : mm-jdbc
-   **Category** : Enhancement
-   **재현 빈도** : Always
-   **증상** : newJDBC fetch 성능 향상을 위해 ResultSet 객체 사용 방식을 개선합니다. 
    이 기능을 이용하기 위해서 반드시 JDBC 드라이버를 패치하고 연결 속성 reuse_resultset=true 를 추가해야 합니다. 
-   **재현 방법**
-   **재현 절차**
    
-   **수행 결과**
    
-   **예상 결과**
-   **Workaround**
-   **변경사항**

  - Performance view

  - Property

    - JDBC 연결속성 추가
       * reuse_resultset
       * 설명 : [JDBC 매뉴얼](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/JDBC.md#reuse_resultset)
       * 값 
           * false : ResultSet 재사용 안 함 (기본값)
           * true  : ResultSet 재사용

  - Compile Option

  - Error Code

### BUG-48510 메모리 테이블 INDEX SCAN, FULL SCAN 성능을 개선합니다.

-   **module** : sm-mem-index

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **증상** : 메모리 테이블 INDEX SCAN, FULL SCAN 성능을 개선합니다.

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

Fixed Bugs
----------

### BUG-42525 installer 에서 DB\_NAME 변경시 알파벳이 아닌 값이 들어올 경우 DB 가 생성되지 않습니다.

-   **module** : installer

-   **Category** : Enhancement

-   **재현 빈도** : Rare

-   **증상** : Installer 이용하여 DB 생성 시, DB\_NAME 에 알파벳과 숫자 이외에 문자가 들어올 경우 에러가 발생합니다. DB\_NAME 생성 시 Altibase 객체 이름 규칙 따르도록 Installer를 수정합니다.
    
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

### BUG-48433 dumptrc 수행 시 altibase\_error.log 에 콜스택과 OS 에러 메시지가 섞이는 문제를 개선합니다.

-   **module** : id

-   **Category** : Fatal

-   **재현 빈도** : Unknown

-   **증상** : dumptrc 수행 시 altibase\_error.log 에 콜스택과 OS 에러 메시지가 섞이는 문제를 개선합니다.
    
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

### BUG-48523 세션 종료 시 statement 객체가 정리되지 않은 경우 Altibase 서버가 비정상 종료할 수 있습니다.

-   **module** : sm\_transaction

-   **Category** : Fatal

-   **재현 빈도** : Rare

-   **증상** : 세션 종료 시 statement 객체가 정리되지 않은 경우 Altibase 서버가 비정상 종료하는 문제를 수정합니다.
    
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

### BUG-48526 임의의 인덱스 키가 WHERE 절에 2번 이상 사용되고 OR 조건에 호스트 변수를 사용한 경우 결과 오류가 발생합니다.

-   **module** : qp-select

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : 임의의 인덱스 키가 WHERE 절에 2번 이상 사용되고 OR 조건에 호스트 변수를 사용한 경우 결과 오류가 발생합니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    DROP TABLE  NECDEXTERN_M;
    CREATE TABLE NECDEXTERN_M 
    (
       RECV_NO      NUMERIC(4)  FIXED,
       RECV_NM      CHAR(40)    FIXED,
       COMP_CD      CHAR(3)     FIXED,
       RTIME        CHAR(6)     FIXED,
       ORD_CLS      CHAR(1)     FIXED,
       OK_GB        CHAR(1)     FIXED,
       RJCT_CD      CHAR(5)     FIXED,
       COMP_EMP_NM  CHAR(20)    FIXED,
       FIX_YN       CHAR(1)     FIXED
    );
    ALTER TABLE NECDEXTERN_M ADD CONSTRAINT PK_NECDEXTERN_M PRIMARY KEY ( RECV_NO );
    
    DROP INDEX IDX_NECDEXTERN_M_1;
    CREATE INDEX IDX_NECDEXTERN_M_1 ON NECDEXTERN_M ( OK_GB ASC, RECV_NO ASC );
    
    INSERT INTO NECDEXTERN_M VALUES(1, '', 'ABC', '', '', '1', '', '', '');
    INSERT INTO NECDEXTERN_M VALUES(2, '', 'ABC', '', '', '0', '', '', '');
    INSERT INTO NECDEXTERN_M VALUES(3, '', 'ABC', '', '', '0', '', '', '');
    INSERT INTO NECDEXTERN_M VALUES(4, '', 'ABC', '', '', '0', '', '', '');
    
    VAR s_dno CHAR(1);
    EXEC :s_dno := '0';
    
    ALTER SESSION SET EXPLAIN PLAN = ON;
    ALTER SESSION SET TRCLOG_DETAIL_PREDICATE = 1;
    ALTER SYSTEM SET __OPTIMIZER_OR_VALUE_INDEX = 1;
    
    PREPARE SELECT /*+ CNF */ A.RECV_NO, A.OK_GB
              FROM NECDEXTERN_M A
             WHERE ((:s_dno  = '0' AND A.OK_GB = '0') 
                OR (:s_dno  = '1' AND A.OK_GB IN ('1', '2') ))
             ORDER BY A.RECV_NO;
    ```

  - **수행 결과**

    ```sql
    RECV_NO     OK_GB  
    ----------------------
    1           1  
    2           0  
    3           0  
    4           0  
    4 rows selected.
    ```

  -   **예상 결과**

      ```sql
      RECV_NO     OK_GB
      ----------------------
      2           0
      3           0
      4           0
      3 rows selected.
      ```

- **Workaround**

  ```sql
  ALTER SYSTEM SET __OPTIMIZER_OR_VALUE_INDEX = 0;
  ```

- **변경사항**

  -   Performance view

  -   Property

  -   Compile Option

  -   Error Code

Changes
-------

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    7.1.0.5.2     |          6.5.1          |    8.9.1     |        7.1.7        |            7.4.6             |

> Altibase 7.1 패치 버전별 히스토리는 [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7_1_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

> 패치를 롤백하려는 경우, [메타다운그레이드](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Installation.md#%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9Cmeta-downgrade)를 참고한다.

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
