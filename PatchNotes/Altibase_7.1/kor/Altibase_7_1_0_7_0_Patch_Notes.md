Altibase 7.1.0.7.0 Patch Notes
==============================

<br/>

<br/>

# Table of Contents  

- [New Features](#new-features)
  - [BUG-49593 SQL 함수로 날짜시간함수 TIMESTAMPADD를 지원합니다.](#bug-49593sql-%ED%95%A8%EC%88%98%EB%A1%9C-%EB%82%A0%EC%A7%9C%EC%8B%9C%EA%B0%84%ED%95%A8%EC%88%98-timestampadd%EB%A5%BC-%EC%A7%80%EC%9B%90%ED%95%A9%EB%8B%88%EB%8B%A4)
- [Fixed Bugs](#fixed-bugs)
  - [BUG-49488 LOB 데이터 타입를 포함한 setBytes()를 executeBatch()로 처리하는 경우 java.lang.ClassCastException: Altibase.jdbc.driver.datatype.ListBufferHandle 에러가 발생합니다.](#bug-49488lob-%EB%8D%B0%EC%9D%B4%ED%84%B0-%ED%83%80%EC%9E%85%EB%A5%BC-%ED%8F%AC%ED%95%A8%ED%95%9C-setbytes%EB%A5%BC-executebatch%EB%A1%9C-%EC%B2%98%EB%A6%AC%ED%95%98%EB%8A%94-%EA%B2%BD%EC%9A%B0-javalangclasscastexception-altibasejdbcdriverdatatypelistbufferhandle-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49545 AIX에서 Altibase 7.1.0.6.0 이상 버전을 사용하는 경우 쿼리 옵티마이저 Fault Tolerance 기능 수행 후 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-49545aix%EC%97%90%EC%84%9C-altibase-71060-%EC%9D%B4%EC%83%81-%EB%B2%84%EC%A0%84%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94-%EA%B2%BD%EC%9A%B0-%EC%BF%BC%EB%A6%AC-%EC%98%B5%ED%8B%B0%EB%A7%88%EC%9D%B4%EC%A0%80-fault-tolerance-%EA%B8%B0%EB%8A%A5-%EC%88%98%ED%96%89-%ED%9B%84-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-49557 이중화 객체에 DDL 수행 시 The table structure has been modified. 에러가 반복되는 경우 altibase\_qp.log에 로그가 과도하게 출력되는 현상을 개선합니다.](#bug-49557%EC%9D%B4%EC%A4%91%ED%99%94-%EA%B0%9D%EC%B2%B4%EC%97%90-ddl-%EC%88%98%ED%96%89-%EC%8B%9C-the-table-structure-has-been-modified-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%98%EB%B3%B5%EB%90%98%EB%8A%94-%EA%B2%BD%EC%9A%B0-altibase_qplog%EC%97%90-%EB%A1%9C%EA%B7%B8%EA%B0%80-%EA%B3%BC%EB%8F%84%ED%95%98%EA%B2%8C-%EC%B6%9C%EB%A0%A5%EB%90%98%EB%8A%94-%ED%98%84%EC%83%81%EC%9D%84-%EA%B0%9C%EC%84%A0%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49611 WITH 절과 조인하는 SQL 수행 시 메모리 참조 오류로 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-49611with-%EC%A0%88%EA%B3%BC-%EC%A1%B0%EC%9D%B8%ED%95%98%EB%8A%94-sql-%EC%88%98%ED%96%89-%EC%8B%9C-%EB%A9%94%EB%AA%A8%EB%A6%AC-%EC%B0%B8%EC%A1%B0-%EC%98%A4%EB%A5%98%EB%A1%9C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-49618 병렬 질의에 집계 함수를 포함한 경우 동시성 문제로 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-49618%EB%B3%91%EB%A0%AC-%EC%A7%88%EC%9D%98%EC%97%90-%EC%A7%91%EA%B3%84-%ED%95%A8%EC%88%98%EB%A5%BC-%ED%8F%AC%ED%95%A8%ED%95%9C-%EA%B2%BD%EC%9A%B0-%EB%8F%99%EC%8B%9C%EC%84%B1-%EB%AC%B8%EC%A0%9C%EB%A1%9C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
  - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
  - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

New Features
============

### BUG-49593 SQL 함수로 날짜시간함수 TIMESTAMPADD를 지원합니다.

-   **module** : mt-function

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : SQL 함수로 날짜시간함수 TIMESTAMPADD를 지원합니다.

    TIMESTAMPADD 함수에 관한 보다 자세한 설명은 [Altibase\_7.1 SQL Reference](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase\_7.1/kor/SQL%20Reference.md\#timestampadd) 매뉴얼에서 확인할 수 있습니다.
    
    TIMESTAMPADD 함수 추가로 TIMESTAMPADD 이름을 가진 객체(테이블, 인덱스, 저장 프로시저, 저장 함수 등) 생성이 불가합니다. 또한, Altibase 7.1.0.7.0 이전 버전에서 TIMESTAMPADD 이름을 가진 객체를 생성한 경우, Altibase 7.1.0.7.0 부터는 사용할 수 없습니다. 

    Altibase 7.1.0.7.0 이상에서 TIMESTAMPADD 이름을 가진 객체를 생성하거나 사용하는 경우 ERR-31001 : SQL syntax error 에러가
    발생합니다.
    
-   **재현 방법**

    -   **재현 절차**

            SELECT TIMESTAMPADD( SQL_TSI_DAY,1, TO_DATE('2003-01-02', 'YYYY-MM-DD')) FROM DUAL;

    -   **수행 결과**

            ERROR at line 1:ORA-00904: "TIMESTAMPADD": invalid identifier

    -   **예상 결과**

            '2003-01-03'

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

Fixed Bugs
==========

### BUG-49488 LOB 데이터 타입를 포함한 setBytes()를 executeBatch()로 처리하는 경우 java.lang.ClassCastException: Altibase.jdbc.driver.datatype.ListBufferHandle 에러가 발생합니다.

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : LOB 데이터 타입를 포함한 setBytes()를 executeBatch()로 실행하는 경우 java.lang.ClassCastException:
    Altibase.jdbc.driver.datatype.ListBufferHandle 에러가 발생하는 현상을 수정합니다.
    
    setBytes()를 executeBatch()로 실행하면 바이너리 타입으로 처리하는데 BLOB으로 처리할 수 있는 JDBC 연결 속성 BATCH\_SETBYTES\_USE\_LOB을 추가합니다. 보다 자세한 설명은 [JDBC User's Manual](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/JDBC%20User's%20Manual.md#batch_setbytes_use_lob) 에서 확인할 수 있습니다.

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

### BUG-49545 AIX에서 Altibase 7.1.0.6.0 ~ 7.1.0.6.7 버전을 사용하는 경우 쿼리 옵티마이저 Fault Tolerance 기능 수행 후 Altibase 서버가 비정상 종료할 수 있습니다.

-   **module** : id

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : AIX에서 Altibase 7.1.0.6.0 ~ 7.1.0.6.7 버전을 사용하는 경우 쿼리 옵티마이저 Fault Tolerance 기능 수행 후 Altibase 서버가 비정상 종료하는 현상을 수정합니다.
    
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

### BUG-49557 이중화 객체에 DDL 수행 시 The table structure has been modified. 에러가 반복되는 경우 altibase\_qp.log에 로그가 과도하게 출력되는 현상을 개선합니다.

-   **module** : rp-control

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : 이중화 객체에 DDL 수행 시 The table structure has been modified. 에러가 반복되는 경우 altibase\_qp.log에 로그가 과도하게 기록되는 현상을 개선합니다.
    
    The table structure has been modified. 에러는 보통 재시도하면 해결되는 종류의 에러로, 실패 시 재시도를 무한 반복합니다.
    지속적인 재시도에도 실패하는 경우 실패 처리하는 프로퍼티를 추가합니다. 히든 프로퍼티로 매뉴얼에 설명을 추가하지 않습니다.
    
    - 이름
    
      REPLICATION\_DDL\_REBUILD\_ERROR\_MAX\_COUNT

    - 설명

      이중화 객체에 DDL 수행 시 The table structure has been modified. 에러가 반복되는 경우 재시도 횟수를 설정합니다. 설정값을 초과하는 경우 ERR-61069 : Internal server error in replication module (The number of DDL rebuild attempts
      RPU\_REPLICATION\_DDL\_REBUILD\_ERROR\_MAX\_COUNTT was exceeded.).에러가 발생합니다. 0으로 설정하면 재시도하지 않으며 1 이상 설정 시 설정값만큼 재시도 후 실패 처리합니다. 
    
    - 값  
    
      0 \~ 65534
    
    - 기본값
    
      10 
    
    - 속성
    
      읽기 전용, **비공개**
    
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

### BUG-49611 WITH 절과 조인하는 SQL 수행 시 메모리 참조 오류로 Altibase 서버가 비정상 종료할 수 있습니다.

-   **module** : qp

-   **Category** : Fatal

-   **재현 빈도** : Rare

-   **설명** : WITH 절과 조인하는 SQL 수행 시 메모리 참조 오류로 Altibase 서버가 비정상 종료하는 현상을 수정합니다.
    
-   **재현 방법**

    -   **재현 절차**

            DROP TABLE COMM_SN_SUBINFO;
            CREATE TABLE COMM_SN_SUBINFO(
                    SVCNB VARCHAR(6) FIXED ,
                    SUBNB VARCHAR(20) FIXED ,
                    SUBKIND INTEGER FIXED,
                    COM_NAME VARCHAR(50) VARIABLE,
                    OFC_CD VARCHAR(10) FIXED,
                    OFC_NAME VARCHAR(50) VARIABLE,
                    AGNC_NAME VARCHAR(50) VARIABLE,
                    END_DATE DATE FIXED,
                    BEGIN_DATE DATE VARIABLE,
                    CUST_NO VARCHAR(22) VARIABLE,
                    SVC_OPT1 VARCHAR(16) VARIABLE,
                    SVC_OPT2 VARCHAR(16) VARIABLE,
                    PARANB VARCHAR(20) VARIABLE,
                    SVCSTATUS INTEGER VARIABLE,
                    VXMURLPSTN VARCHAR(128) VARIABLE,
                    VXMLURLMOBILE VARCHAR(128) VARIABLE,
                    CHAKIND VARCHAR(10) VARIABLE,
                    COM_MODE VARCHAR(6) VARIABLE,
                    CHANB VARCHAR(20) VARIABLE,
                    STORE_OWNER_NO VARCHAR(20) VARIABLE,
                    STORE_NAME VARCHAR(50) VARIABLE );
            DROP INDEX PK_COMM_SN_SUBINFO;
            CREATE UNIQUE INDEX PK_COMM_SN_SUBINFO ON COMM_SN_SUBINFO( SUBNB );
            INSERT INTO COMM_SN_SUBINFO ( SUBNB ) SELECT LEVEL FROM DUAL CONNECT BY LEVEL < 10;
            DROP TABLE COMM_FP_SUBINFO;
            CREATE TABLE COMM_FP_SUBINFO(
                    SVCNB VARCHAR(6) FIXED ,
                    SUBNB VARCHAR(20) FIXED ,
                    SUBKIND INTEGER FIXED,
                    COM_NAME VARCHAR(50) VARIABLE,
                    OFC_CD VARCHAR(10) FIXED,
                    OFC_NAME VARCHAR(50) VARIABLE,
                    AGNC_NAME VARCHAR(50) VARIABLE,
                    END_DATE DATE FIXED,
                    BEGIN_DATE DATE VARIABLE,
                    CUST_NO VARCHAR(22) VARIABLE,
                    SVC_OPT1 VARCHAR(16) VARIABLE,
                    SVC_OPT2 VARCHAR(16) VARIABLE,
                    PARANB VARCHAR(20) VARIABLE,
                    SVCSTATUS INTEGER VARIABLE,
                    VXMURLPSTN VARCHAR(128) VARIABLE,
                    VXMLURLMOBILE VARCHAR(128) VARIABLE,
                    CHAKIND VARCHAR(10) VARIABLE,
                    COM_MODE VARCHAR(6) VARIABLE,
                    CHANB VARCHAR(20) VARIABLE,
                    STORE_OWNER_NO VARCHAR(20) VARIABLE,
                    STORE_NAME VARCHAR(50) VARIABLE );
            DROP INDEX PK_COMM_FP_SUBINFO;
            CREATE UNIQUE INDEX PK_COMM_FP_SUBINFO ON COMM_FP_SUBINFO( SUBNB );
            INSERT INTO COMM_FP_SUBINFO ( SUBNB ) SELECT LEVEL FROM DUAL CONNECT BY LEVEL < 10;
            var v1 varchar(10);
            exec :v1:= '1';
            prepare WITH SEARCH_NB_TBL AS (
                   SELECT
                   TO_CHAR(regexp_substr(CAST(:v1 AS VARCHAR(10000)),'[^,]+', 1, level)) AS SEARCH_NB
                   FROM DUAL
                   CONNECT BY regexp_substr(:v1, '[^,]+', 1, LEVEL) IS NOT NULL
            )
            SELECT SUBNB
                 , CUST_NO
              FROM COMM_SN_SUBINFO A
                 , SEARCH_NB_TBL ST
             WHERE A.SUBNB = ST.SEARCH_NB
             UNION
            SELECT SUBNB
                 , CUST_NO
              FROM COMM_FP_SUBINFO B
                 , SEARCH_NB_TBL ST
             WHERE B.SUBNB = ST.SEARCH_NB;

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49618 병렬 질의에 집계 함수를 포함한 경우 동시성 문제로 Altibase 서버가 비정상 종료할 수 있습니다.

-   **module** : qp-select-execute

-   **Category** : Fatal

-   **재현 빈도** : Rare

-   **설명** : 병렬 질의에 집계 함수를 포함한 경우 동시성 문제로 Altibase 서버가 비정상 종료할 수 있습니다.
    
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
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    7.1.0.7.0     |          6.5.1          |    8.10.1    |        7.1.7        |            7.4.7             |

> Altibase 7.1 패치 버전별 히스토리는 [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7_1_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

#### Meta Version

메타 버전은 변경되지 않았다.

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
