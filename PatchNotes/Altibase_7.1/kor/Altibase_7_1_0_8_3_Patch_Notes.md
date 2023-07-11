# Altibase 7.1.0.8.3 Patch Notes

<br/>

<br>

# Table of Contents

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [New Features](#new-features)
    - [BUG-49600 JDBC 4.0 API의 Connection.createBlob(), createClob()을 지원합니다.](#bug-49600jdbc-40-api%EC%9D%98-connectioncreateblob-createclob%EC%9D%84-%EC%A7%80%EC%9B%90%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-49985 GROUP BY GROUPING SETS 절에 빈 그룹(Empty Group)을 사용할 때 메모리 효율성을 개선합니다.](#bug-49985group-by-grouping-sets-%EC%A0%88%EC%97%90-%EB%B9%88-%EA%B7%B8%EB%A3%B9empty-group%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%A0-%EB%95%8C-%EB%A9%94%EB%AA%A8%EB%A6%AC-%ED%9A%A8%EC%9C%A8%EC%84%B1%EC%9D%84-%EA%B0%9C%EC%84%A0%ED%95%A9%EB%8B%88%EB%8B%A4)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-48074 윈도우 환경에서 loadbalance가 on일때 랜덤하게 서버가 선택되지 않습니다.](#bug-48074%EC%9C%88%EB%8F%84%EC%9A%B0-%ED%99%98%EA%B2%BD%EC%97%90%EC%84%9C-loadbalance%EA%B0%80-on%EC%9D%BC%EB%95%8C-%EB%9E%9C%EB%8D%A4%ED%95%98%EA%B2%8C-%EC%84%9C%EB%B2%84%EA%B0%80-%EC%84%A0%ED%83%9D%EB%90%98%EC%A7%80-%EC%95%8A%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-49732 압축 컬럼과 압축 컬럼이 키인 인덱스를 가진 테이블의 테이블스페이스를 변경할 때 Altibase 서버가 비정상 종료합니다.](#bug-49732%EC%95%95%EC%B6%95-%EC%BB%AC%EB%9F%BC%EA%B3%BC-%EC%95%95%EC%B6%95-%EC%BB%AC%EB%9F%BC%EC%9D%B4-%ED%82%A4%EC%9D%B8-%EC%9D%B8%EB%8D%B1%EC%8A%A4%EB%A5%BC-%EA%B0%80%EC%A7%84-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%9D%98-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%8A%A4%ED%8E%98%EC%9D%B4%EC%8A%A4%EB%A5%BC-%EB%B3%80%EA%B2%BD%ED%95%A0-%EB%95%8C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50013 Adapter 로그(jdbcAdapter.trc 또는 oraAdapter.trc)에 DML 정보를 출력하는 형식을 설정하는 프로퍼티를 추가합니다.](#bug-50013adapter-%EB%A1%9C%EA%B7%B8jdbcadaptertrc-%EB%98%90%EB%8A%94-oraadaptertrc%EC%97%90-dml-%EC%A0%95%EB%B3%B4%EB%A5%BC-%EC%B6%9C%EB%A0%A5%ED%95%98%EB%8A%94-%ED%98%95%EC%8B%9D%EC%9D%84-%EC%84%A4%EC%A0%95%ED%95%98%EB%8A%94-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0%EB%A5%BC-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50025 CREATE DATABASE 수행 후 바로 STARTUP SERVICE를 수행하면 Altibase 서버가 비정상 종료하거나 ERR-11110 : The index is inconsistent 에러가 발생합니다.](#bug-50025create-database-%EC%88%98%ED%96%89-%ED%9B%84-%EB%B0%94%EB%A1%9C-startup-service%EB%A5%BC-%EC%88%98%ED%96%89%ED%95%98%EB%A9%B4-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%98%EA%B1%B0%EB%82%98-err-11110--the-index-is-inconsistent-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50033 adapter를 시작할 때​ ALA 로그 파일을 오픈할 수 없으면 코어 파일이 생성됩니다.](#bug-50033adapter%EB%A5%BC-%EC%8B%9C%EC%9E%91%ED%95%A0-%EB%95%8C%E2%80%8B-ala-%EB%A1%9C%EA%B7%B8-%ED%8C%8C%EC%9D%BC%EC%9D%84-%EC%98%A4%ED%94%88%ED%95%A0-%EC%88%98-%EC%97%86%EC%9C%BC%EB%A9%B4-%EC%BD%94%EC%96%B4-%ED%8C%8C%EC%9D%BC%EC%9D%B4-%EC%83%9D%EC%84%B1%EB%90%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50057 ROLLUP 함수와 집계 함수 그리고 ORDER BY 절을 함께 사용하면 결과 오류가 발생합니다.](#bug-50057rollup-%ED%95%A8%EC%88%98%EC%99%80-%EC%A7%91%EA%B3%84-%ED%95%A8%EC%88%98-%EA%B7%B8%EB%A6%AC%EA%B3%A0-order-by-%EC%A0%88%EC%9D%84-%ED%95%A8%EA%BB%98-%EC%82%AC%EC%9A%A9%ED%95%98%EB%A9%B4-%EA%B2%B0%EA%B3%BC-%EC%98%A4%EB%A5%98%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50058 DROP REPLICATION 수행 시 이중화 수신자 쓰레드가 종료되지 않을 수 있는 메모리 참조 오류를 수정합니다.](#bug-50058drop-replication-%EC%88%98%ED%96%89-%EC%8B%9C-%EC%9D%B4%EC%A4%91%ED%99%94-%EC%88%98%EC%8B%A0%EC%9E%90-%EC%93%B0%EB%A0%88%EB%93%9C%EA%B0%80-%EC%A2%85%EB%A3%8C%EB%90%98%EC%A7%80-%EC%95%8A%EC%9D%84-%EC%88%98-%EC%9E%88%EB%8A%94-%EB%A9%94%EB%AA%A8%EB%A6%AC-%EC%B0%B8%EC%A1%B0-%EC%98%A4%EB%A5%98%EB%A5%BC-%EC%88%98%EC%A0%95%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50059 aku -p end 수행 동작을 변경합니다. 이중화 FLUSH 명령을 수행한 후에 이중화를 중지합니다.](#bug-50059aku--p-end-%EC%88%98%ED%96%89-%EB%8F%99%EC%9E%91%EC%9D%84-%EB%B3%80%EA%B2%BD%ED%95%A9%EB%8B%88%EB%8B%A4-%EC%9D%B4%EC%A4%91%ED%99%94-flush-%EB%AA%85%EB%A0%B9%EC%9D%84-%EC%88%98%ED%96%89%ED%95%9C-%ED%9B%84%EC%97%90-%EC%9D%B4%EC%A4%91%ED%99%94%EB%A5%BC-%EC%A4%91%EC%A7%80%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50061 updatable view에 집합 연산자를 사용했을 때 예외 처리를 변경합니다.](#bug-50061updatable-view%EC%97%90-%EC%A7%91%ED%95%A9-%EC%97%B0%EC%82%B0%EC%9E%90%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%96%88%EC%9D%84-%EB%95%8C-%EC%98%88%EC%99%B8-%EC%B2%98%EB%A6%AC%EB%A5%BC-%EB%B3%80%EA%B2%BD%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50071 SET 절의 서브쿼리에서 multiple update의 대상을 참조하면 ERR-31455 에러가 발생하거나 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-50071set-%EC%A0%88%EC%9D%98-%EC%84%9C%EB%B8%8C%EC%BF%BC%EB%A6%AC%EC%97%90%EC%84%9C-multiple-update%EC%9D%98-%EB%8C%80%EC%83%81%EC%9D%84-%EC%B0%B8%EC%A1%B0%ED%95%98%EB%A9%B4-err-31455-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%98%EA%B1%B0%EB%82%98-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-50082 비정상적으로 종료된 슬레이브 파드에서 aku -p start 수행 동작을 변경합니다. 이중화 시작 후 FLUSH 명령을 수행합니다.](#bug-50082%EB%B9%84%EC%A0%95%EC%83%81%EC%A0%81%EC%9C%BC%EB%A1%9C-%EC%A2%85%EB%A3%8C%EB%90%9C-%EC%8A%AC%EB%A0%88%EC%9D%B4%EB%B8%8C-%ED%8C%8C%EB%93%9C%EC%97%90%EC%84%9C-aku--p-start-%EC%88%98%ED%96%89-%EB%8F%99%EC%9E%91%EC%9D%84-%EB%B3%80%EA%B2%BD%ED%95%A9%EB%8B%88%EB%8B%A4-%EC%9D%B4%EC%A4%91%ED%99%94-%EC%8B%9C%EC%9E%91-%ED%9B%84-flush-%EB%AA%85%EB%A0%B9%EC%9D%84-%EC%88%98%ED%96%89%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50090 Statement 객체의 다음 결과가 ResultSet 객체가 아닐 때 getMoreResults()에서 true를 반환합니다.](#bug-50090statement-%EA%B0%9D%EC%B2%B4%EC%9D%98-%EB%8B%A4%EC%9D%8C-%EA%B2%B0%EA%B3%BC%EA%B0%80-resultset-%EA%B0%9D%EC%B2%B4%EA%B0%80-%EC%95%84%EB%8B%90-%EB%95%8C-getmoreresults%EC%97%90%EC%84%9C-true%EB%A5%BC-%EB%B0%98%ED%99%98%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50094 메모리 테이블의 ADD COLUMN 수행 동작을 변경합니다.](#bug-50094%EB%A9%94%EB%AA%A8%EB%A6%AC-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%9D%98-add-column-%EC%88%98%ED%96%89-%EB%8F%99%EC%9E%91%EC%9D%84-%EB%B3%80%EA%B2%BD%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50096 DDL 복제 실패 이후 HeartBeat 쓰레드의 비정상적인 동작으로 이중화 송신자가 시작되지 않을 수 있습니다.](#bug-50096ddl-%EB%B3%B5%EC%A0%9C-%EC%8B%A4%ED%8C%A8-%EC%9D%B4%ED%9B%84-heartbeat-%EC%93%B0%EB%A0%88%EB%93%9C%EC%9D%98-%EB%B9%84%EC%A0%95%EC%83%81%EC%A0%81%EC%9D%B8-%EB%8F%99%EC%9E%91%EC%9C%BC%EB%A1%9C-%EC%9D%B4%EC%A4%91%ED%99%94-%EC%86%A1%EC%8B%A0%EC%9E%90%EA%B0%80-%EC%8B%9C%EC%9E%91%EB%90%98%EC%A7%80-%EC%95%8A%EC%9D%84-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-50106 iSQL에서 desc 명령을 수행하면 ERR-31002 : A single-row subquery has returned more than one row. 에러가 발생합니다.](#bug-50106isql%EC%97%90%EC%84%9C-desc-%EB%AA%85%EB%A0%B9%EC%9D%84-%EC%88%98%ED%96%89%ED%95%98%EB%A9%B4-err-31002--a-single-row-subquery-has-returned-more-than-one-row-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50131 조건절 검사 시 Altibase 서버가 비정상 종료하는 현상에 대한 예외처리를 추가합니다.](#bug-50131%EC%A1%B0%EA%B1%B4%EC%A0%88-%EA%B2%80%EC%82%AC-%EC%8B%9C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%98%EB%8A%94-%ED%98%84%EC%83%81%EC%97%90-%EB%8C%80%ED%95%9C-%EC%98%88%EC%99%B8%EC%B2%98%EB%A6%AC%EB%A5%BC-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50076 Altibase 7.1.0.7.3 이후 linux 32bit 에서 빌드 실패 문제를 수정 합니다.](#bug-50076-altibase-7.1.0.7.3-이후-linux-32bit-에서-빌드-실패-문제를-수정-합니다.)
    - [BUG-49996 에러메시지에 PCRE2 error: 가 출력되는 문제를 수정합니다.](#bug-49996-에러메시지에-pcre2-error:-가-출력되는-문제를-수정합니다.)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-49600 JDBC 4.0 API의 Connection.createBlob(), createClob()을 지원합니다.

#### module

`mm-jdbc`

#### Category 

`Enhancement`

#### 재현 빈도

``Always``

#### 설명

JDBC 4.0 API의 Connection.createBlob(), createClob()을 지원합니다.

관련 설명은 [Altibase 7.1 : JDBC User's Manual - createBlob(), createClob()을 이용한 LOB 사용]((https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/JDBC%20User's%20Manual.md#createblob-createclob%EC%9D%84-%EC%9D%B4%EC%9A%A9%ED%95%9C-lob-%EC%82%AC%EC%9A%A9))에서 확인할 수 있습니다.

이 버그에서 추가된 기능을 사용하려면 JDBC 4.2를 부분 지원하는 JDBC 드라이버(Altibase42.jar)를 패치해야 합니다.

#### 재현 방법

-   **재현 절차**

    ~~~sql
    CREATE TABLE t1 (c1 int, c2 clob, c3 blob);
    ~~~

    ```java
    Connection sConn = getConnection("20300");
    sConn.setAutoCommit(false);
    Clob sClob = sConn.createClob();
    sClob.setString(1, "dsfjsdkfsdkfjds;fsdkfs");
    Blob sBlob = sConn.createBlob();
    sBlob.setBytes(1, "dfkjsdlkfjsdfkjsdkfljsdfsd".getBytes());
    PreparedStatement sStmt = sConn.prepareStatement("INSERT INTO t1 VALUES (?, ?, ?)");
    sStmt.setInt(1, 1);
    sStmt.setClob(2, sClob);
    sStmt.setBlob(3, sBlob);
    sStmt.executeUpdate();
    sConn.commit();
    ```

    ~~~sql
    SELECT c1,length(c2), binary_length(c3) FROM t1;
    ~~~

    

-   **수행 결과**

    ```java
    Exception in thread "main" java.sql.SQLFeatureNotSupportedException: 
    	at Altibase.jdbc.driver.ex.Error.createSQLFeatureNotSupportedException(Error.java:785)
    	at Altibase.jdbc.driver.AbstractConnection.createClob(AbstractConnection.java:34)
    	at GetLobTest.doTest(GetLobTest.java:15)
    	at GetLobTest.main(GetLobTest.java:8)
    ```

-   **예상 결과**

    ```sql
    C1          LENGTH(C2)           BINARY_LENGTH(C3)
    ----------------------------------------------------------
    1           22                   26
    1 row selected.
    ```



### BUG-49985 GROUP BY GROUPING SETS 절에 빈 그룹(Empty Group)을 사용할 때 메모리 효율성을 개선합니다.

#### module

`qp-select`

#### Category  

`Enhancement`

#### 재현 빈도 

`Always`

#### 설명  

GROUP BY GROUPING SETS 절에 빈 그룹(Empty Group)을 사용할 때 메모리 할당 시간을 감소하고 메모리 사용 효율을 개선합니다.


#### 재현 방법

-   **재현 절차**

        ALTER SESSION SET EXPLAIN PLAN = ON;
        CREATE TABLE T1 ( I1 INTEGER, I2 INTEGER );
        SELECT I1,SUM(I2)
          FROM T1
         GROUP BY GROUPING SETS ( I1, () );

-   **수행 결과**

        I1          SUM(I2)
        ------------------------------------
        No rows selected.
        ------------------------------------------------------------
        PROJECT ( COLUMN_COUNT: 2, TUPLE_SIZE: 16, COST: 388.69 )
         VIEW ( ACCESS: 0, COST: 386.03 )
          BAG-UNION
           PROJECT ( COLUMN_COUNT: 2, TUPLE_SIZE: 16, COST: 130.13 )
            GROUP-AGGREGATION ( ITEM_SIZE: 40, GROUP_COUNT: 0, BUCKET_COUNT: 1024, ACCESS: 0, COST: 130.06 )
             SCAN ( TABLE: SYS.T1, FULL SCAN, ACCESS: 0, COST: 116.76 )
           PROJECT ( COLUMN_COUNT: 2, TUPLE_SIZE: 16, COST: 135.34 )
            GROUP-AGGREGATION ( ITEM_SIZE: 32, GROUP_COUNT: 0, BUCKET_COUNT: 5120, ACCESS: 0, COST: 130.06 )
             SCAN ( TABLE: SYS.T1, FULL SCAN, ACCESS: 0, COST: 116.76 )
        ------------------------------------------------------------

-   **예상 결과**

        I1          SUM(I2)
        ------------------------------------
        No rows selected.
        ------------------------------------------------------------
        PROJECT ( COLUMN_COUNT: 2, TUPLE_SIZE: 16, COST: 260.21 )
         VIEW ( ACCESS: 1, COST: 260.19 )
          BAG-UNION
           PROJECT ( COLUMN_COUNT: 2, TUPLE_SIZE: 16, COST: 130.13 )
            GROUP-AGGREGATION ( ITEM_SIZE: 40, GROUP_COUNT: 0, BUCKET_COUNT: 1024, ACCESS: 0, COST: 130.06 )
             SCAN ( TABLE: SYS.T1, FULL SCAN, ACCESS: 0, COST: 116.76 )
           PROJECT ( COLUMN_COUNT: 2, TUPLE_SIZE: 16, COST: 130.06 )
            GROUP-AGGREGATION ( ITEM_SIZE: 32, GROUP_COUNT: 1, BUCKET_COUNT: 1, ACCESS: 1, COST: 130.06 )
             SCAN ( TABLE: SYS.T1, FULL SCAN, ACCESS: 0, COST: 116.76 )
        ------------------------------------------------------------



Fixed Bugs
==========

### BUG-48074 윈도우 환경에서 loadbalance가 on일때 랜덤하게 서버가 선택되지 않습니다. 

#### module

``mm-cli``

#### Category

``Functional Error``

#### 재현 빈도

`Always`

#### 설명

윈도우 환경에서 loadbalance가 on일때 Altibase 서버가 랜덤하게 선택되지 않는 버그를 수정합니다.

#### 재현 방법

-   **재현 절차**

-   **수행 결과** 

-   **예상 결과**

#### Workaround

`없음`

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-49732 압축 컬럼과 압축 컬럼이 키인 인덱스를 가진 테이블의 테이블스페이스를 변경할 때 Altibase 서버가 비정상 종료합니다.

#### module

``sm``

#### Category

``Fatal``

#### 재현 빈도

`Always`

#### 설명

압축 컬럼과 압축 컬럼이 키인 인덱스를 가진 테이블의 테이블스페이스를 변경할 때 Altibase 서버가 비정상 종료하는 버그를 수정합니다. 또한 인덱스를 가진 테이블의 테이블스페이스를 변경할 때 인덱스 생성 과정을 개선하여 ALTER TABLESPACE 수행 성능을 개선하였습니다.

이 버그는 메모리 테이블에서만 발생합니다.

#### 재현 방법

-   **재현 절차**

        CREATE TABLE T1 ( I1 CHAR(10), I2 NUMBER(2) ) COMPRESS (I1);
        CREATE MEMORY TABLESPACE USER_MEM_TBS SIZE 1G AUTOEXTEND ON;
        CREATE INDEX T1_I1 ON T1(I1);
        INSERT INTO T1 VALUES (3,3);
        ALTER TABLE T1 ALTER TABLESPACE USER_MEM_TBS;

-   **수행 결과**

        ERR-91015 : Communication failure. 

-   **예상 결과**

        Alter success.

#### Workaround

`없음`

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50013 Adapter 로그(jdbcAdapter.trc 또는 oraAdapter.trc)에 DML 정보를 출력하는 형식을 설정하는 프로퍼티를 추가합니다.

#### module

`rp-jdbcAdapter`

#### Category  

`Enhancement`

#### 재현 빈도 

`Always`

#### 설명 

Adapter 로그(jdbcAdapter.trc 또는 oraAdapter.trc)에 DML 정보를 출력하는 형식을 설정하는 프로퍼티를 추가합니다.

- Adapter 프로퍼티 : ADAPTER_XLOG_WRITE_TYPE 

  DML 정보를 출력하는 형식을 설정한다. 0 또는 1을 설정할 수 있으며 기본값을 0이다. 

  0은 XLog에 기록된 테이블, 컬럼 정보들을 출력하고 1은 SQL 구문으로 출력한다. 

  - 출력 예 

    - ADAPTER_XLOG_WRITE_TYPE = 0 

      ~~~bash
      [2020-06-17 14:25:13] com.mysql.jdbc.MysqlDataTruncation: Data truncation: Out of range value for column 'market_disp_seq' at row 1
      [2020-06-17 14:25:13] INSERT : 
      [2020-06-17 14:25:13] Table name tcate
      [2020-06-17 14:25:13] Table Id 2
      [2020-06-17 14:25:13] Column count 17
      [2020-06-17 14:25:13] Column name CATE_C
      [2020-06-17 14:25:13] Hidden Column NO
      [2020-06-17 14:25:13] Column value '220348'
      [2020-06-17 14:25:13] Column name NGROUPSEQ
      [2020-06-17 14:25:13] Hidden Column NO
      [2020-06-17 14:25:13] Column value '0'
      [2020-06-17 14:25:13] Column name PCATE_C
      [2020-06-17 14:25:13] Hidden Column NO
      [2020-06-17 14:25:13] Column value '0'
      [2020-06-17 14:25:13] Column name CATE_N
      [2020-06-17 14:25:13] Hidden Column NO
      [2020-06-17 14:25:13] Column value
      [2020-06-17 14:25:13] -------------------
      [2020-06-17 14:25:13] '취미'
      [2020-06-17 14:25:13] -------------------
      ~~~

    - ADAPTER_XLOG_WRITE_TYPE = 1

      ~~~bash
      INSERT INTO INI.BC_CDR VALUES ( '148946461353114', '0502859198', '1', '2001', '2017031413101300', '2017031413101402', '01022223333', '01093488256', '11112222', '33334444', '0', TO_DATE('(null)(null)', 'YYYY-MM-DD HH:MI:SSSSSSSS') );
      ~~~


#### 재현 방법

-   **재현 절차**

-   **수행 결과**

-   **예상 결과**

#### Workaround

`없음`

#### 변경사항

-   Performance view
-   Property
    
-   Compile Option
-   Error Code

### BUG-50025 CREATE DATABASE 수행 후 바로 STARTUP SERVICE를 수행하면 Altibase 서버가 비정상 종료하거나 ERR-11110 : The index is inconsistent 에러가 발생합니다.

#### module

`sm`

#### Category  

`Assert`

#### 재현 빈도 

`Frequence`

#### 설명  

CREATE DATABASE 수행 후 바로 STARTUP SERVICE를 수행하면 Altibase 서버가 비정상 종료하거나 ERR-11110 : The index is inconsistent 에러가 발생하는 버그를 수정합니다.

이 버그를 회피하려면 아래 순서로 STARTUP SERVICE를 수행해야 합니다.

(1) CREATE DATABASE

(2) SHUTDOWN ABORT

(3) STARTUP SERVICE


#### 재현 방법

-   **재현 절차**

    ```sql
    $ is -sysdba
    iSQL(sysdba)> STARTUP PROCESS; 
    iSQL(sysdba)> CREATE DATABASE MYDB INITSIZE=50M NOARCHIVELOG CHARACTER SET UTF8 NATIONAL CHARACTER SET UTF16;
    iSQL(sysdba)> STARTUP SERVICE;
    iSQL(sysdba)> CREATE USER ALTITEST IDENTIFIED BY ALTITEST;
    iSQL(sysdba)> DROP USER ALTITEST;
    ```

-   **수행 결과**

    Altibase 서버 비정상 종료 또는

    ~~~sql
    iSQL(sysdba)> DROP USER ALTITEST;
    [ERR-11110 : The index is inconsistent]
    ~~~

-   **예상 결과**

    ```sql
    iSQL(sysdba)> DROP USER ALTITEST;
    Drop success.
    ```

#### Workaround

데이터베이스를 생성한 후 SHUTDOWN ABORT 명령 수행하고 STARTUP을 수행합니다.

```sql
$ is -sysdba
iSQL(sysdba)> STARTUP PROCESS; 
iSQL(sysdba)> CREATE DATABASE MYDB INITSIZE=50M NOARCHIVELOG CHARACTER SET UTF8 NATIONAL CHARACTER SET UTF16;
iSQL(sysdba)> SHUTDOWN ABORT;
iSQL(sysdba)> STARTUP SERVICE;
iSQL(sysdba)> CREATE USER ALTITEST IDENTIFIED BY ALTITEST;
iSQL(sysdba)> DROP USER ALTITEST;
```

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50033 adapter를 시작할 때​ ALA 로그 파일을 오픈할 수 없으면 코어 파일이 생성됩니다.

#### module

`rp-ala`

#### Category

`Assert`

#### 재현 빈도 

`Rare`

#### 설명 

adapter를 시작할 때​ ALA 로그 파일을 오픈할 수 없으면 시그널을 받고 adapter 프로세스가 강제 종료되며 코어 파일이 생성됩니다. 예외 처리를 변경하여 adapter 트레이스 로그(예, jdbcAdapter.trc)에 다음과 같은 에러 메시지를 출력하도록 개선하였습니다.

`ALA library error: 335873, Failed to open log file`


#### 재현 방법

-   **재현 절차**

-   **수행 결과**

-   **예상 결과**

#### Workaround

`없음`

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50057 ROLLUP 함수와 집계 함수 그리고 ORDER BY 절을 함께 사용하면 결과 오류가 발생합니다.

#### module

`qp-select`

#### Category 

`Functional Error`

#### 재현 빈도 

`Frequence`

#### 설명  

ROLLUP 함수와 집계 함수 그리고 ORDER BY 절을 함께 사용할 때 발생하는 결과 오류를 수정합니다. 패치 후 버그 조건에 만족하는 질의문 수행 시 결과가 달라질 수 있습니다.


#### 재현 방법

-   **재현 절차**

    ```sql
    DROP TABLE T1;
    CREATE TABLE T1( I1 VARCHAR(10), I2 VARCHAR(10), I3 VARCHAR(10) );
    INSERT INTO T1 VALUES(1,1,1);
    INSERT INTO T1 VALUES(1,2,2);
    INSERT INTO T1 VALUES(3,2,1);
    INSERT INTO T1 VALUES(10,2,1);
    SELECT /*+ NO_PLAN_CACHE */ TO_CHAR(COUNT(*) )
      FROM T1
     GROUP BY ROLLUP(I1), I2
     ORDER BY 1;
    ```

-   **수행 결과**

    ```sql
    TO_CHAR(COUNT(*))  
    ---------------------
    0           
    0           
    0           
    0           
    0           
    0           
    6 rows selected.
    ```

-   **예상 결과**

    ```sql
    TO_CHAR(COUNT(*))  
    ---------------------
    1
    1
    1
    1
    1
    3
    6 rows selected.
    ```

#### Workaround

`없음`

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50058 DROP REPLICATION 수행 시 이중화 수신자 쓰레드가 종료되지 않을 수 있는 메모리 참조 오류를 수정합니다.

#### module

`rp`

#### Category 

`Memory Error`

#### 재현 빈도 

`Unknown`

#### 설명  

DROP REPLICATION 수행 시 이중화 수신자 쓰레드가 종료되지 않을 수 있는 메모리 참조 오류를 수정합니다. 이 버그가 발생할 가능성은 매우 낮습니다.


#### 재현 방법

-   **재현 절차**

-   **수행 결과**

-   **예상 결과**

#### Workaround

`없음`

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50059 aku -p end 수행 동작을 변경합니다. 이중화 FLUSH 명령을 수행한 후에 이중화를 중지합니다.

#### module

`aku`

#### Category  

`Reliability`

#### 재현 빈도 

`Always`

#### 설명

aku -p end 수행 동작을 변경합니다. 데이터 불일치가 발생할 가능성을 방지하기 위해, 이중화를 중지하기 전에 aku -p end를 수행한 해당 파드의 이중화 객체에 ALTER REPLICATION ~ FLUSH ALL 명령을 수행하여 변경 데이터를 모두 다른 파드로 전송합니다.

추가된 FLUSH 동작으로 aku -p end 수행이 본 버그를 반영하기 전보다 오래 걸릴 수 있습니다. 

관련하여 aku 프로퍼티 AKU_FLUSH_AT_END가 추가되었습니다.

슬레이브 파드에서 aku -p end 명령을 수행할 때 ALTER REPLICATION ~ FLUSH ALL 명령을 수행하여 이중화 갭을 제거할 것인지 설정합니다. 1 이면 이중화 FLUSH ALL 명령으로 이중화 갭을 제거하고 0이면 제거하지 않습니다. 기본값은 1입니다. 


#### 재현 방법

-   **재현 절차**

-   **수행 결과**

-   **예상 결과**

#### Workaround

`없음`

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50061 updatable view에 집합 연산자를 사용했을 때 예외 처리를 변경합니다.

#### module

`qp`

#### Category 

`Functional Error`

#### 재현 빈도

`Always`

#### 설명

집합 연산자를 사용한 뷰는 updatable view로 사용할 수 없는 제약 사항에 따라 올바른 에러 메시지를 반환하도록 개선합니다. 이 버그를 반영하기 전/후 에러 메시지는 아래와 같습니다. 

- 버그 반영 전

  ERR-31455 : Failed to work because an internal exception occurred from an OS.[Contact Altibase's Support Center]

- 버그 반영 후

  ERR-313A4 : Cannot modify a column for a non key-preserved table


#### 재현 방법

-   **재현 절차**

    ```sql
    CREATE TABLE D1(I1 INTEGER, I2 INTEGER);
    CREATE OR REPLACE VIEW V1 AS SELECT * FROM D1 UNION SELECT * FROM D1;
    DELETE FROM (SELECT * FROM V1);
    ```

-   **수행 결과**

    ```sql
    ERR-31455 : Failed to work because an internal exception occurred from an OS.[Contact Altibase's Support Center]
    ```

-   **예상 결과**

    ```sql
    ERR-313A4 : Cannot modify a column for a non key-preserved table
    ```

#### Workaround

`없음`

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50071 SET 절의 서브쿼리에서 multiple update의 대상을 참조하면 ERR-31455 에러가 발생하거나 Altibase 서버가 비정상 종료할 수 있습니다.

#### module

`qp-dml-pvo`

#### Category  

`Fatal`

#### 재현 빈도 

`Always`

#### 설명 

SET 절의 서브쿼리에서 multiple update의 대상을 참조하면 ERR-31455 : Failed to work because an internal exception occurred from an OS. 에러가 발생하거나 Altibase 서버가 비정상 종료하는 버그를 수정합니다.  이 버그는 simple view merging 기능이 활성화되어 있을 때 발생합니다.


#### 재현 방법

-   **재현 절차**

-   **수행 결과**

-   **예상 결과**

#### Workaround

`없음`

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50082 비정상적으로 종료된 슬레이브 파드에서 aku -p start 수행 동작을 변경합니다. 이중화 시작 후 FLUSH 명령을 수행합니다.

#### module

`aku`

#### Category  

`Reliability`

#### 재현 빈도 

`Unknown`

#### 설명  

비정상적으로 종료된 슬레이브 파드에서 aku -p start 를 수행할 때 aku의 동작을 변경합니다.

비정상적으로 종료된 슬레이브 파드는 aku -p end 명령을 수행하지 않았거나 정상적으로 완료하지 않아 Altibase에 이중화 정보가 남아있는 파드를 말합니다. 이전의 이중화 정보가 남아있으면 슬레이브 파드를 다시 시작한 후에 데이터 불일치가 발생할 수 있으므로 이전 데이터를 동기화하는 작업을 추가합니다.

1. aku -p start 명령을 수행한 슬레이드 파드에서 Altibase 서버 프로퍼티 ADMIN_MODE를 1로 설정하여 데이터베이스 사용자의 접근을 막고, 접속된 세션을 강제 종료한다.
2. aku -p start 명령을 수행한 슬레이드 파드에서 이중화를 시작하고 ALTER REPLICATION ~ FLUSH ALL을 수행한다. 이 명령은 다른 파드로 동기화하지 못한 데이터를 전송한다. 
3. 원격 파드에서 aku -p start 명령을 수행한 슬레이드 파드로 ALTER REPLICATION ~ FLUSH WAIT *wait_time*을 수행한다.
4. aku -p start 명령을 수행한 슬레이드 파드에서 Altibase 서버 프로퍼티 ADMIN_MODE를 0으로 설정하여 데이터베이스 사용자의 접속을 허용한다.

위와 같이 변경된 동작으로 aku -p start 명령 수행 시간이 버그 반영 전보다 오래 걸릴 수 있습니다.

관련하여 aku 프로퍼티 AKU_FLUSH_AT_START, AKU_FLUSH_TIMEOUT_AT_START가 추가되었습니다.

aku 프로퍼티 설명은 [Altibase_7.1 Utilities Manual - aku-설정-파일](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Utilities%20Manual.md#aku-%EC%84%A4%EC%A0%95-%ED%8C%8C%EC%9D%BC)을 참고히시기 바랍니다.


#### 재현 방법

-   **재현 절차**

-   **수행 결과**

-   **예상 결과**

#### Workaround

`없음`

#### 변경사항

-   Performance view
-   Property
    
-   Compile Option
-   Error Code

### BUG-50090 Statement 객체의 다음 결과가 ResultSet 객체가 아닐 때 getMoreResults()에서 true를 반환합니다.

#### module

`mm-jdbc`

#### Category  

`Functional Error`

#### 재현 빈도 

`Always`

#### 설명   

Statement 객체의 다음 결과가 ResultSet 객체가 아닐 때 getMoreResults()에서 true를 반환하는 버그를 수정합니다. JDBC API에 따라 false를 반환하도록 수정합니다.

이 버그를 반영하려면 Altibase JDBC 드라이버를 패치해야 합니다.

이 버그가 반영된 Altibase JDBC 드라이버 7.1.0.8.3 이상에서 getMoreResults() 메소드의 수행 결과가 달라집니다.

- 기존 : 최대 ResultSet 객체 수 만큼 true를 반환

- 변경 : ResultSet 객체 수 - 1 만큼 true를 반환


#### 재현 방법

-   **재현 절차**

-   **수행 결과**

-   **예상 결과**

#### Workaround

`없음`

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50094 메모리 테이블의 ADD COLUMN 수행 동작을 변경합니다.

#### module

`qp`

#### Category  

`Functional Error`

#### 재현 빈도 

`Always`

#### 설명 

Altibase 7.1 에는 메모리 테이블의 칼럼을 추가할 때 다른 트랜잭션에 영향을 주지 않는 '실시간 DDL' 기능이 추가되었습니다.

이 기능은 추가할 컬럼의 크기에 상관없이 무조건 VARIABLE로 컬럼을 생성하는 부분에서 아래와 같은 문제점이 발견되어 ADD COLUMN의 내부 동작을 변경합니다.

(1) DESC table_name 명령을 수행할 때 CREATE로 생성한 컬럼과 추가된 컬럼의 저장 정보가 다름

(2) INTEGER와 같은 FIXED 기반의 데이터 타입도 VARIABLE로 저장되며 테이블 크기 증가

(3) 테이블 크기 증가로 변경 트랜잭션 성능 저하

 

Altibase 7.1.0.8.3 이상에서 메모리 테이블의 ADD COLUMN 수행 동작은 다음과 같습니다. 

 '실시간 DDL' 수행 조건이 추가할 컬럼의 크기에 따라 결정됩니다.

- '실시간 DDL' 동작하는 경우

  추가할 컬럼의 크기가 MEMORY_VARIABLE_COLUMN_IN_ROW_SIZE에서 지정한 크기보다 크면 VARIABLE 컬럼으로 생성되고 실시간 DDL이 동작합니다.

- '실시간 DDL' 동작하지 않는 경우

  추가할 컬럼의 크기가 MEMORY_VARIABLE_COLUMN_IN_ROW_SIZE에서 지정한 크기보다 작거나 같으면 FIXED 컬럼으로 생성하고 실시간 DDL이 동작하지 않습니다.

  실시간 DDL이 동작하지 않으면 ADD COLUMN 수행은 아래와 같이 처리됩니다.

  - 내부적으로 대상 테이블을 재구성합니다.

  - 이때, 대상 테이블에 X 잠금을 획득하므로 ADD COLUMN 작업이 완료할 때까지 대상 테이블에 접근할 수 없습니다.

  - 대상 데이터 크기에 비례하여 메모리 사용량이 증가합니다.

 Altibase 7.1.0.8.3 이전 버전과 같이 동작하게 하려면 Altibase 기술 지원 센터로 문의해주시기 바랍니다.


#### 재현 방법

-   **재현 절차**

-   **수행 결과**

-   **예상 결과**

#### Workaround

`없음`

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50096 DDL 복제 실패 이후 HeartBeat 쓰레드의 비정상적인 동작으로 이중화 송신자가 시작되지 않을 수 있습니다.

#### module

`rp`

#### Category  

`Functional Error`

#### 재현 빈도 

`Always`

#### 설명  

DDL 복제 실패 후 이중화를 종료할 때 HeartBeat 쓰레드가 정상적으로 종료되지 않는 문제로, 이중화 송신자가 시작되지 않는 현상을 수정합니다.


#### 재현 방법

-   **재현 절차**

-   **수행 결과**

-   **예상 결과**

#### Workaround

`없음`

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50106 iSQL에서 desc 명령을 수행하면 ERR-31002 : A single-row subquery has returned more than one row. 에러가 발생합니다.

#### module

`ux-isql`

#### Category

`Functional Error`

#### 재현 빈도

`Always`

#### 설명

iSQL에서 desc 명령을 수행하면 ERR-31002 : A single-row subquery has returned more than one row. 에러가 발생하는 버그를 수정합니다. 이 버그는 아래 조건을 만족할 때 발생합니다.

- 서로 다른 데이터베이스 사용자가 같은 이름의 테이블 A를 생성

- iSQL에서 SET PARTITIONS ON 수행 후

- DESC A 수행


#### 재현 방법

-   **재현 절차**

    ```sql
    CONNECT SYS/MANAGER
    CREATE TABLE T1 (C1 INTEGER, C2 INTEGER);
    
    CREATE USER USER1 IDENTIFIED BY USER1;
    CONNECT USER1/USER1
    CREATE TABLE T1 (C1 INTEGER, C2 INTEGER);
    SET PARTITIONS ON;
    DESC T1;
    ```

-   **수행 결과**

    ```sql
    DESC T1;
    [ TABLESPACE : SYS_TBS_MEM_DATA ]
    [ ATTRIBUTE ]
    ------------------------------------------------------------------------------
    NAME                                     TYPE                        IS NULL
    ------------------------------------------------------------------------------
    C1                                       INTEGER         FIXED
    C2                                       INTEGER         FIXED
    T1 has no index
    T1 has no primary key
    [ERR-31002 : A single-row subquery has returned more than one row.]
    ```

-   **예상 결과**

    ```sql
    DESC T1;
    [ TABLESPACE : SYS_TBS_MEM_DATA ]
    [ ATTRIBUTE ]
    ------------------------------------------------------------------------------
    NAME                                     TYPE                        IS NULL
    ------------------------------------------------------------------------------
    C1                                       INTEGER         FIXED
    C2                                       INTEGER         FIXED
    T1 has no index
    T1 has no primary key
    ```

#### Workaround

`없음`

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50131 조건절 검사 시 Altibase 서버가 비정상 종료하는 현상에 대한 예외처리를 추가합니다.

#### module

`qp-dml-execute`

#### Category  

`Fatal`

#### 재현 빈도 

`Impossible`

#### 설명

조건절 검사 시 Altibase 서버가 비정상 종료하는 현상에 대한 예외처리를 추가합니다.


#### 재현 방법

-   **재현 절차**

-   **수행 결과**

-   **예상 결과**

#### Workaround

`없음`

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50076 Altibase 7.1.0.7.3 이후 linux 32bit 에서 빌드 실패 문제를 수정 합니다.

-   **module** : sm

-   **Category** : Compile Error

-   **재현 빈도** : Always

-   **설명** : Altibase 7.1.0.7.3 이후 linux 32bit 에서 컴파일 오류 발생하는 문제를 수정하였습니다. 이 버그의 수정으로 Altibase 7.1.0.7.3 ~7.1.0.8.2 에서 linux 32bit 클라이언트 패키지를 전달할수 없던 문제가 해결되었습니다.

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

### BUG-49996 에러메시지에 PCRE2 error: 가 출력되는 문제를 수정합니다.

- **module** : st

- **Category** : Other

- **재현 빈도** : Always

- **설명** : 에러메시지에 PCRE2: 가 출력되는 문제를 수정하고, cause의 내용을 수정합니다.

  (기존)

  SQL> select regexp_like('c', '[');

  [ERR-2106C : PCRE2 error: missing terminating ] for character class (occurred in qsfPCRERegExp::expCompile4Estimate)

  0001 : select REGEXP_LIKE('c', '[')

  (변경)

  SQL> select regexp_like('c', '[');

  [ERR-2106C : error: missing terminating ] for character class (occurred in qsfPCRERegExp::expCompile4Estimate)

  0001 : select REGEXP_LIKE('c', '[')

- **재현 방법**

  -   **재현 절차**

  -   **수행 결과**

  -   **예상 결과**

- **Workaround**

- **변경사항**

  - Performance view

  - Property

  - Compile Option

  - Error Code

    에러메시지가 변경되었습니다.

    (기존) [ERR-2106C : PCRE2 error: missing terminating ]

    (변경) [ERR-2106C : error: missing terminating ]

    

Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    7.1.0.8.3     |          6.5.1          |    8.10.1    |        7.1.7        |            7.4.7             |

> Altibase 7.1 패치 버전별 히스토리는 [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.1/Altibase_7_1_Version_Histories.md) 에서 확인할 수 있다.

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

* AKU_FLUSH_AT_END

#### 변경된 프로퍼티

#### 삭제된 프로퍼티

### 성능 뷰

#### 추가된 성능 뷰

#### 변경된 성능 뷰

#### 삭제된 성능 뷰
