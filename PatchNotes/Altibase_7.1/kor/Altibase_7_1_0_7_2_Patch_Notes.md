Altibase 7.1.0.7.2 Patch Notes
==============================

<br/>

<br/>

# **Table of Contents** 

- [Altibase 7.1.0.7.2 Patch Notes](#altibase-71072-patch-notes)
- [New Features](#new-features)
  - [BUG-49567 Adapter for Oracle에서 지원하는 데이터 타입에 LOB을 추가합니다.](#bug-49567adapter-for-oracle%EC%97%90%EC%84%9C-%EC%A7%80%EC%9B%90%ED%95%98%EB%8A%94-%EB%8D%B0%EC%9D%B4%ED%84%B0-%ED%83%80%EC%9E%85%EC%97%90-lob%EC%9D%84-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49616 Altibase 7.1 Standard Edition, Enterprise Edition에서 라이센스 발급 기준으로 MEM\_MAX\_DB\_SIZE를 추가합니다.](#bug-49616altibase-71-standard-edition-enterprise-edition%EC%97%90%EC%84%9C-%EB%9D%BC%EC%9D%B4%EC%84%BC%EC%8A%A4-%EB%B0%9C%EA%B8%89-%EA%B8%B0%EC%A4%80%EC%9C%BC%EB%A1%9C-mem_max_db_size%EB%A5%BC-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
- [Fixed Bugs](#fixed-bugs)
  - [BUG-49546 DatabaseMetaData.getColumns 메서드의 반환 결과 중 DATA\_TYPE의 값을 정의하는 연결 속성 getcolumns\_return\_jdbctype을 추가합니다.](#bug-49546databasemetadatagetcolumns-%EB%A9%94%EC%84%9C%EB%93%9C%EC%9D%98-%EB%B0%98%ED%99%98-%EA%B2%B0%EA%B3%BC-%EC%A4%91-data_type%EC%9D%98-%EA%B0%92%EC%9D%84-%EC%A0%95%EC%9D%98%ED%95%98%EB%8A%94-%EC%97%B0%EA%B2%B0-%EC%86%8D%EC%84%B1-getcolumns_return_jdbctype%EC%9D%84-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49549 파티션드 테이블에 사용한 집계 함수가 병렬 수행될 경우 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-49549%ED%8C%8C%ED%8B%B0%EC%85%98%EB%93%9C-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90-%EC%82%AC%EC%9A%A9%ED%95%9C-%EC%A7%91%EA%B3%84-%ED%95%A8%EC%88%98%EA%B0%80-%EB%B3%91%EB%A0%AC-%EC%88%98%ED%96%89%EB%90%A0-%EA%B2%BD%EC%9A%B0-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-49559 복합 인덱스가 있는 테이블에 ROW\_NUMBER 함수를 사용한 경우 중복된 정렬 작업을 제거하여 SQL 수행 성능을 개선합니다.](#bug-49559%EB%B3%B5%ED%95%A9-%EC%9D%B8%EB%8D%B1%EC%8A%A4%EA%B0%80-%EC%9E%88%EB%8A%94-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90-row_number-%ED%95%A8%EC%88%98%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%9C-%EA%B2%BD%EC%9A%B0-%EC%A4%91%EB%B3%B5%EB%90%9C-%EC%A0%95%EB%A0%AC-%EC%9E%91%EC%97%85%EC%9D%84-%EC%A0%9C%EA%B1%B0%ED%95%98%EC%97%AC-sql-%EC%88%98%ED%96%89-%EC%84%B1%EB%8A%A5%EC%9D%84-%EA%B0%9C%EC%84%A0%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49601 User Defined Type을 지원하지 않을 때 DatabaseMetaData.getUDTs()에서 SQLFeatureNotSupported 예외 대신 빈 ResultSet을 반환하도록 변경합니다.](#bug-49601user-defined-type%EC%9D%84-%EC%A7%80%EC%9B%90%ED%95%98%EC%A7%80-%EC%95%8A%EC%9D%84-%EB%95%8C-databasemetadatagetudts%EC%97%90%EC%84%9C-sqlfeaturenotsupported-%EC%98%88%EC%99%B8-%EB%8C%80%EC%8B%A0-%EB%B9%88-resultset%EC%9D%84-%EB%B0%98%ED%99%98%ED%95%98%EB%8F%84%EB%A1%9D-%EB%B3%80%EA%B2%BD%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49602 Updatable ResultSet 객체의 결과가 0건인 경우에도 ResultSet.insertRow() 메소드가 동작해야 합니다.](#bug-49602updatable-resultset-%EA%B0%9D%EC%B2%B4%EC%9D%98-%EA%B2%B0%EA%B3%BC%EA%B0%80-0%EA%B1%B4%EC%9D%B8-%EA%B2%BD%EC%9A%B0%EC%97%90%EB%8F%84-resultsetinsertrow-%EB%A9%94%EC%86%8C%EB%93%9C%EA%B0%80-%EB%8F%99%EC%9E%91%ED%95%B4%EC%95%BC-%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49603 SQL 문에 데이터베이스 소유자가 명시된 경우 Updatable ResultSet 객체에서 java.sql.SQLException: Table or view was not found 에러가 발생합니다.](#bug-49603sql-%EB%AC%B8%EC%97%90-%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4-%EC%86%8C%EC%9C%A0%EC%9E%90%EA%B0%80-%EB%AA%85%EC%8B%9C%EB%90%9C-%EA%B2%BD%EC%9A%B0-updatable-resultset-%EA%B0%9D%EC%B2%B4%EC%97%90%EC%84%9C-javasqlsqlexception-table-or-view-was-not-found-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49605 Updatable ResultSet을 이용해 데이터 입력 시 Unsupported type conversion SQLException 에러가 발생하는 현상을 수정합니다.](#bug-49605updatable-resultset%EC%9D%84-%EC%9D%B4%EC%9A%A9%ED%95%B4-%EB%8D%B0%EC%9D%B4%ED%84%B0-%EC%9E%85%EB%A0%A5-%EC%8B%9C-unsupported-type-conversion-sqlexception-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%98%EB%8A%94-%ED%98%84%EC%83%81%EC%9D%84-%EC%88%98%EC%A0%95%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49613 = 연산자와 CAST 연산자에 사용된 서브쿼리의 결과가 NULL일 때 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-49613-%EC%97%B0%EC%82%B0%EC%9E%90%EC%99%80-cast-%EC%97%B0%EC%82%B0%EC%9E%90%EC%97%90-%EC%82%AC%EC%9A%A9%EB%90%9C-%EC%84%9C%EB%B8%8C%EC%BF%BC%EB%A6%AC%EC%9D%98-%EA%B2%B0%EA%B3%BC%EA%B0%80-null%EC%9D%BC-%EB%95%8C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-49619 디스크 인덱스에서 언두 테이블스페이스를 사용하는 경우 다른 트랜젝션에 의해 언두 영역이 재사용되어 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-49619%EB%94%94%EC%8A%A4%ED%81%AC-%EC%9D%B8%EB%8D%B1%EC%8A%A4%EC%97%90%EC%84%9C-%EC%96%B8%EB%91%90-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%8A%A4%ED%8E%98%EC%9D%B4%EC%8A%A4%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94-%EA%B2%BD%EC%9A%B0-%EB%8B%A4%EB%A5%B8-%ED%8A%B8%EB%9E%9C%EC%A0%9D%EC%85%98%EC%97%90-%EC%9D%98%ED%95%B4-%EC%96%B8%EB%91%90-%EC%98%81%EC%97%AD%EC%9D%B4-%EC%9E%AC%EC%82%AC%EC%9A%A9%EB%90%98%EC%96%B4-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-49620 NVL_EQUAL(expr1, exp2, expr3)에서 expr1에 인덱스가 존재하고 expr2의 컬럼의 데이터 타입이 expr1과 다른 경우 테이블 스캔 방식을 변경하여 제품의 안정성을 향상합니다.](#bug-49620nvl_equalexpr1-exp2-expr3%EC%97%90%EC%84%9C-expr1%EC%97%90-%EC%9D%B8%EB%8D%B1%EC%8A%A4%EA%B0%80-%EC%A1%B4%EC%9E%AC%ED%95%98%EA%B3%A0-expr2%EC%9D%98-%EC%BB%AC%EB%9F%BC%EC%9D%98-%EB%8D%B0%EC%9D%B4%ED%84%B0-%ED%83%80%EC%9E%85%EC%9D%B4-expr1%EA%B3%BC-%EB%8B%A4%EB%A5%B8-%EA%B2%BD%EC%9A%B0-%ED%85%8C%EC%9D%B4%EB%B8%94-%EC%8A%A4%EC%BA%94-%EB%B0%A9%EC%8B%9D%EC%9D%84-%EB%B3%80%EA%B2%BD%ED%95%98%EC%97%AC-%EC%A0%9C%ED%92%88%EC%9D%98-%EC%95%88%EC%A0%95%EC%84%B1%EC%9D%84-%ED%96%A5%EC%83%81%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49632 반환 데이터 타입이 LOB인 저장 함수가 ORDER BY/GROUP BY/윈도우 함수의 PARTITION BY 하위절에 사용될 때 예외 처리를 변경하여 제품의 안정성을 향상합니다.](#bug-49632%EB%B0%98%ED%99%98-%EB%8D%B0%EC%9D%B4%ED%84%B0-%ED%83%80%EC%9E%85%EC%9D%B4-lob%EC%9D%B8-%EC%A0%80%EC%9E%A5-%ED%95%A8%EC%88%98%EA%B0%80-order-bygroup-by%EC%9C%88%EB%8F%84%EC%9A%B0-%ED%95%A8%EC%88%98%EC%9D%98-partition-by-%ED%95%98%EC%9C%84%EC%A0%88%EC%97%90-%EC%82%AC%EC%9A%A9%EB%90%A0-%EB%95%8C-%EC%98%88%EC%99%B8-%EC%B2%98%EB%A6%AC%EB%A5%BC-%EB%B3%80%EA%B2%BD%ED%95%98%EC%97%AC-%EC%A0%9C%ED%92%88%EC%9D%98-%EC%95%88%EC%A0%95%EC%84%B1%EC%9D%84-%ED%96%A5%EC%83%81%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49633 집계 함수에 DISTINCT 키워드를 사용한 SQL 수행 시 DISTINCT 처리를 위한 메모리 과다 사용으로 SQL 수행 성능이 하락합니다.](#bug-49633%EC%A7%91%EA%B3%84-%ED%95%A8%EC%88%98%EC%97%90-distinct-%ED%82%A4%EC%9B%8C%EB%93%9C%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%9C-sql-%EC%88%98%ED%96%89-%EC%8B%9C-distinct-%EC%B2%98%EB%A6%AC%EB%A5%BC-%EC%9C%84%ED%95%9C-%EB%A9%94%EB%AA%A8%EB%A6%AC-%EA%B3%BC%EB%8B%A4-%EC%82%AC%EC%9A%A9%EC%9C%BC%EB%A1%9C-sql-%EC%88%98%ED%96%89-%EC%84%B1%EB%8A%A5%EC%9D%B4-%ED%95%98%EB%9D%BD%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49636 Altibase 서버 프로퍼티 ARCHIVE\_FULL\_ACTION 설정 값에 따른 아카이브로그 쓰레드의 동작을 개선합니다.](#bug-49636altibase-%EC%84%9C%EB%B2%84-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0-archive_full_action-%EC%84%A4%EC%A0%95-%EA%B0%92%EC%97%90-%EB%94%B0%EB%A5%B8-%EC%95%84%EC%B9%B4%EC%9D%B4%EB%B8%8C%EB%A1%9C%EA%B7%B8-%EC%93%B0%EB%A0%88%EB%93%9C%EC%9D%98-%EB%8F%99%EC%9E%91%EC%9D%84-%EA%B0%9C%EC%84%A0%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49647 Ubuntu 16, Ubuntu 18에서 altiMon 실행 시 com.altibase.picl.LibLoader.OsNotSupportedException 에러가 발생합니다.](#bug-49647ubuntu-16-ubuntu-18%EC%97%90%EC%84%9C-altimon-%EC%8B%A4%ED%96%89-%EC%8B%9C-comaltibasepicllibloaderosnotsupportedexception-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49655 디스크 테이블 및 디스크 인덱스에서 사용 중인 데이터 페이지수를 조회할 수 있도록 X\$SEGMENT에 TOTAL\_USED\_PAGE\_CNT 컬럼을 추가합니다.](#bug-49655%EB%94%94%EC%8A%A4%ED%81%AC-%ED%85%8C%EC%9D%B4%EB%B8%94-%EB%B0%8F-%EB%94%94%EC%8A%A4%ED%81%AC-%EC%9D%B8%EB%8D%B1%EC%8A%A4%EC%97%90%EC%84%9C-%EC%82%AC%EC%9A%A9-%EC%A4%91%EC%9D%B8-%EB%8D%B0%EC%9D%B4%ED%84%B0-%ED%8E%98%EC%9D%B4%EC%A7%80%EC%88%98%EB%A5%BC-%EC%A1%B0%ED%9A%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EB%8F%84%EB%A1%9D-xsegment%EC%97%90-total_used_page_cnt-%EC%BB%AC%EB%9F%BC%EC%9D%84-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
  
- [Changes](#changes)
  - [Version Info](#version-info)
  - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
  - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
  - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)



New Features
============

### BUG-49567 Adapter for Oracle에서 지원하는 데이터 타입에 LOB을 추가합니다.

-   **module** : rp-oraAdapter

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : Adapter for Oracle에서 지원하는 데이터 타입에 LOB을 추가합니다.
    
    LOB 데이터 타입 지원 관련한 Adapter for Oracle 동작 및 제약 사항은 Adapter for Oracle 매뉴얼을 참고하시기 바랍니다.
    
    [Adapter for Oracle User’s Manual - 2.설치와 설정 - 프로퍼티 - ORACLE\_ARRAY\_DML\_MAX\_SIZE](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase\_7.1/kor/Adapter%20for%20Oracle%20User's%20Manual.md\#oracle\_array\_dml\_max\_size)
    
    [Adapter for Oracle User’s Manual - 2.설치와 설정 - 프로퍼티 - ORACLE\_ERROR\_RETRY\_COUNT](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase\_7.1/kor/Adapter%20for%20Oracle%20User's%20Manual.md\#oracle\_error\_retry\_count-%EB%8B%A8%EC%9C%84-%ED%9A%9F%EC%88%98)
    
    [Adapter for Oracle User’s Manual - 2.설치와 설정 - 프로퍼티 - ORACLE\_SKIP\_ERROR](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase\_7.1/kor/Adapter%20for%20Oracle%20User's%20Manual.md\#oracle\_skip\_error) 
    
    [Adapter for Oracle User’s Manual - 2.설치와 설정 - 프로퍼티 - ADAPTER\_LOB\_TYPE\_SUPPORT](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase\_7.1/kor/Adapter%20for%20Oracle%20User's%20Manual.md\#adapter\_lob\_type\_support)
    
    [Adapter for Oracle User’s Manual - 3.사용법 - oraAdapter 제약조건 - LOB 데이터 타입 제약 사항](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase\_7.1/kor/Adapter%20for%20Oracle%20User's%20Manual.md\#lob-%EB%8D%B0%EC%9D%B4%ED%84%B0-%ED%83%80%EC%9E%85-%EC%A0%9C%EC%95%BD-%EC%82%AC%ED%95%AD)
    
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

### BUG-49616 Altibase 7.1 Standard Edition, Enterprise Edition에서 라이센스 발급 기준으로 MEM\_MAX\_DB\_SIZE를 추가합니다.

-   **module** : id

-   **Category** : Enhancement

-   **재현 빈도** : Unknown

-   **설명** : Altibase 7.1 Standard Edition, Enterprise Edition에서 라이센스 발급 기준으로 MEM\_MAX\_DB\_SIZE를 추가합니다.
    
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
==========

### BUG-49546 DatabaseMetaData.getColumns 메서드의 반환 결과 중 DATA\_TYPE의 값을 정의하는 연결 속성 getcolumns\_return\_jdbctype을 추가합니다.

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : DatabaseMetaData.getColumns 메서드의 반환 결과 중 DATA\_TYPE의 값을 정의하는 연결 속성 [getcolumns\_return\_jdbctype](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/JDBC%20User's%20Manual.md#getcolumns_return_jdbctype)을 추가합니다.

    - 연결 속성 이름

      getcolumns\_return\_jdbctype

    - 설명

      DatabaseMetaData.getColumns 메서드의 반환 결과 중 DATA\_TYPE의 값을 정의한다.

      true는 JDBC API에서 정의한 java.sql.Types의 SQL 데이터 형식으로 반환하고 false는 V\$DATATYPE에 정의된 데이터 타입 형식으로 반환한다.  

    - 기본값

      false

    본 버그를 적용하려면 Altibase JDBC 드라이버를 Altibase 7.1.0.7.2 이상으로 패치하고 연결 속성 getcolumns_return_jdbctype을 추가해야 합니다. 

-   **재현 방법**

    -   **재현 절차**

        ```sql
        iSQL> CREATE TABLE T1 (C1 CLOB, C2 BLOB);
        ```

        ```java
        Connection sConn = getConnection("20300");
        DatabaseMetaData sMeta = sConn.getMetaData();
        ResultSet sRs = sMeta.getColumns(null, "SYS", "T1", "%");
        while (sRs.next())
        {
            String sColumName = sRs.getString("COLUMN_NAME");
            String sDataType = sRs.getString("DATA_TYPE");
            System.out.println("COLUMN_NAME==>" + sColumName);
            System.out.println("DATA_TYPE==>" + sDataType);
        }
        ```

    -   **수행 결과**

        ```java
        COLUMN_NAME==>C1
        DATA_TYPE==>40
        COLUMN_NAME==>C2
        DATA_TYPE==>30
        ```

    -   **예상 결과**

        ```java
        COLUMN_NAME==>C1
        DATA_TYPE==>2005
        COLUMN_NAME==>C2
        DATA_TYPE==>2004
        ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49549 파티션드 테이블에 사용한 집계 함수가 병렬 수행될 경우 Altibase 서버가 비정상 종료할 수 있습니다.

-   **module** : qp

-   **Category** : Fatal

-   **재현 빈도** : Frequence

-   **설명** : 파티션드 테이블에 사용한 집계 함수가 병렬 수행될 경우 Altibase 서버가 비정상 종료하는 현상을 수정합니다.
    
-   **재현 방법**

    -   **재현 절차**

        ```sql
        DROP TABLE t1 cascade;
        CREATE TABLE T1( I1 INTEGER, I2 INTEGER ) PARTITION BY HASH(I1)
         ( PARTITION P1, PARTITION P2 );
        ALTER TABLE T1 PARALLEL 2;
        VAR V1 integer;
        PREPARE SELECT /*+ no_plan_cache */ COUNT(*) FROM T1 WHERE (I1=:V1 OR I1=999) AND (I2=1 OR I2=2);
        ```

    -   **수행 결과**

            Altibase 서버 비정상 종료

    -   **예상 결과**

        ```sql
        COUNT(*)             
        -----------------------
        0                    
        1 row selected.
        ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49559 복합 인덱스가 있는 테이블에 ROW\_NUMBER 함수를 사용한 경우 중복된 정렬 작업을 제거하여 SQL 수행 성능을 개선합니다.

-   **module** : qp

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : 복합 인덱스가 있는 테이블에 ROW\_NUMBER 함수를 사용한 경우 중복된 정렬 작업을 피하고자 Preserved Order 기능을 추가하여 SQL
    수행 성능을 개선하였습니다.
    
    > 참고 : Preserved Order 기능
    >
    > Altibase는 이미 정렬된 테이블을 ORDER BY 구문으로 똑같이 정렬시킬 때 중복된 정렬 작업을 피하기 위해 Preserved Order라는 개념을 사용합니다. 예를 들어 테이블 t1에 i1 컬럼이 Ascending 정렬된 인덱스를 가지고 있을 때, i1 컬럼을 ORDER BY 구문으로 Ascending 정렬하면 따로 정렬 작업을 수행하지 않고 그대로 읽도록 하는 개념입니다.
    
    관련하여 히든 프로퍼티 \_\_OPTIMIZER\_ROW\_NUMBER 가 추가되었습니다. 히든 프로퍼티로 매뉴얼에 설명을 추가하지 않습니다.
    
    - 이름
    
      \_\_OPTIMIZER\_ROW\_NUMBER

    - 설명
    
      본 버그에서 추가된 기능 사용 여부를 결정합니다.
    
    - 값
    
      - 0 : Preserved Order 기능을 사용하지 않음.
    
      - 1 : Preserved Order 기능을 사용함.
    
    - 기본값
    
      - 0
    
    - 속성
    
      변경 가능, 비공개
    
    Altibase 6.5.1, Altibase 7.1에서 이전 버전과의 호환성을 위해 이 프로퍼티 기본값 0 으로 개선한 기능 사용이 비활성화되어 있습니다. Altibase 6.5.1.9.1 이상, Altibase 7.1.0.7.2 이상에서 이 버그에서 개선한 기능을 사용하려면 이 프로퍼티 값을 1로 설정해야 합니다. 프로퍼티 설정값을 1로 설정하면, 이 버그의 영향을 받은 SQL 문의 실행 계획에서 WINDOW SORT 노드의 SORT\_COUNT 수가 줄어듭니다.
    
    이 프로퍼티 변경은 ALTER SYSTEM 으로 변경할 수 있습니다. 기본값과 다른 값을 영구 적용하고자 할 경우 altibase.properties 에 추가하고 Altibase 서버를 재시작해야 합니다. 
    
-   **재현 방법**

    -   **재현 절차**

        ```sql
        DROP TABLE T1;
        CREATE TABLE T1 ( I1 INT, I2 INT, I3 INT, I4 INT);
        DROP INDEX IDX1;
        CREATE INDEX IDX1 ON T1 (  I1, I2, I3 DESC );
        ALTER SESSION SET EXPLAIN PLAN = ON;
        SELECT ROW_NUMBER() OVER ( ORDER BY I3 DESC ), * FROM T1 WHERE I1 = 1 AND I2 = 2;
        ```

    -   **수행 결과**

        ```sql
        ------------------------------------------------------------
        PROJECT ( COLUMN_COUNT: 5, TUPLE_SIZE: 24, COST: 0.26 )
         WINDOW SORT ( ITEM_SIZE: 24, ITEM_COUNT: 0, ACCESS: 0, SORT_COUNT: 1, COST: 0.19 )
          SCAN ( TABLE: SYS.T1, INDEX: SYS.IDX1, RANGE SCAN, ACCESS: 0, COST: 0.01 )
        ------------------------------------------------------------
        ```

    -   **예상 결과**

        SORT_COUNT 가 줄어듭니다.
        
        ```sql
        ------------------------------------------------------------
        PROJECT ( COLUMN_COUNT: 5, TUPLE_SIZE: 24, COST: 0.26 )
         WINDOW SORT ( ITEM_SIZE: 24, ITEM_COUNT: 0, ACCESS: 0, SORT_COUNT: 0, COST: 0.19 )
          SCAN ( TABLE: SYS.T1, INDEX: SYS.IDX1, RANGE SCAN, ACCESS: 0, COST: 0.01 )
        ------------------------------------------------------------
        ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49601 User Defined Type을 지원하지 않을 때 DatabaseMetaData.getUDTs()에서 SQLFeatureNotSupported 예외 대신 빈 ResultSet을 반환하도록 변경합니다.

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : JDBC specification에 따라 User Defined Type을 지원하지 않을 때 DatabaseMetaData.getUDTs()에서 SQLFeatureNotSupported 예외 대신 빈 ResultSet을 반환하도록 변경합니다.
    
    - 참고 : https://docs.oracle.com/javame/config/cdc/opt-pkgs/api/jsr169/java/sql/DatabaseMetaData.html
    
    본 버그를 적용하려면 Altibase JDBC 드라이버를 7.1.0.7.2 이상으로 패치해야 합니다.
    
-   **재현 방법**

    -   **재현 절차**

        ```java
        Connection sConn = getConnection("20300");
        DatabaseMetaData sMeta = sConn.getMetaData();
        ResultSet sRs = sMeta.getUDTs(null, null, null, null);
        System.out.println("sRs.next()==>" + sRs.next());
        ```

    -   **수행 결과**

        ```java
        Exception in thread "main" java.sql.SQLFeatureNotSupportedException: User defined type
        ```

    -   **예상 결과**

        ```java
        sRs.next()==>false
        ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49602 Updatable ResultSet 객체의 결과가 0건인 경우에도 ResultSet.insertRow() 메소드가 동작해야 합니다.

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : Updatable ResultSet 객체의 결과가 0건인 경우에도 ResultSet.insertRow() 메소드가 동작하지 않는 현상을 개선합니다. 
    
    이 버그의 영향을 받는 ResultSet 객체의 스크롤 및 업데이트 허용 옵션은 아래와 같습니다. 
    
    - 스크롤 옵션
      - TYPE_FORWARD_ONLY
      - TYPE_SCROLL_INSENSITIVE
    - 업데이트 허용 옵션
      - CONCUR_UPDATABLE
    
    이 버그를 적용하려면 Altibase JDBC 드라이버를 Altibase 7.1.0.7.2 이상으로 패치해야 합니다. 
    
-   **재현 방법**

    -   **재현 절차**

        ```sql
        iSQL> CREATE TABLE T1 (C1 INT, C2 VARCHAR(10));
        ```

        ```java
        Connection sConn = getConnection("20300");
        Statement sStmt = sConn.createStatement(ResultSet.TYPE_FORWARD_ONLY,
                                                ResultSet.CONCUR_UPDATABLE);
        ResultSet sRs = sStmt.executeQuery("SELECT c1, c2 FROM t1");
        sRs.moveToInsertRow();
        sRs.updateObject(1, 1);
        sRs.updateObject(2, "test..");
        sRs.insertRow(); 
        ```

        ```sql
        iSQL> SELECT * FROM t1;
        ```

    -   **수행 결과**

        ```sql
        iSQL> SELECT * FROM t1;
        C1          C2
        ---------------------------
        No rows selected.
        ```

    -   **예상 결과**

        ```sql
        iSQL> SELECT * FROM t1;
        C1          C2
        ---------------------------
        1           test..
        1 row selected.
        ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49603 SQL 문에 데이터베이스 소유자가 명시된 경우 Updatable ResultSet 객체에서 java.sql.SQLException: Table or view was not found 에러가 발생합니다.

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : SQL 문에 데이터베이스 소유자가 명시된 경우 Updatable ResultSet 객체에서 java.sql.SQLException: Table or view was not found 에러가 발생하는 현상을 수정합니다.
    
    > Updatable ResultSet 객체 : 업데이트 허용(CONCUR_UPDATABLE) 옵션을 사용한 ResultSet 객체
    
    본 버그를 적용하려면 Altibase JDBC 드라이버를 7.1.0.7.2 이상으로 패치해야 합니다.
    
-   **재현 방법**

    -   **재현 절차**

        ```sql
        iSQL> CREATE USER altitest IDENTIFIED BY altitest;
        Create success.
        iSQL> CONNECT altitest;
        Write Password :
        Connect success.
        iSQL> CREATE TABLE T2 (C1 INT, C2 VARCHAR(10));
        Create success.
        ```

        ```java
        Connection sConn = getConnection("20300"); // connect with SYS
        Statement sStmt = sConn.createStatement(ResultSet.TYPE_FORWARD_ONLY,
                                                ResultSet.CONCUR_UPDATABLE);
        ResultSet sRs = sStmt.executeQuery("SELECT c1, c2 FROM altitest.t2");
        sRs.moveToInsertRow();
        sRs.updateObject(1, 1);
        sRs.updateObject(2, "test..");
        sRs.insertRow(); 
        ```
        
    -   **수행 결과**
    
        ```java
        Exception in thread "main" java.sql.SQLException: Table or view was not found : 
        0001 : DELETE FROM T2 WHERE _PROWID=?
                          ^ ^
            at Altibase.jdbc.driver.ex.Error.processServerError(Error.java:397)
            at Altibase.jdbc.driver.AltibasePreparedStatement.prepare(AltibasePreparedStatement.java:139)
            at Altibase.jdbc.driver.AltibasePreparedStatement.(AltibasePreparedStatement.java:94)
            at Altibase.jdbc.driver.AltibaseConnection.prepareStatement(AltibaseConnection.java:1346)
            at Altibase.jdbc.driver.AltibaseUpdatableResultSet.(AltibaseUpdatableResultSet.java:66)
            at Altibase.jdbc.driver.AltibaseResultSet.createResultSet(AltibaseResultSet.java:90)
            at Altibase.jdbc.driver.AltibaseStatement.processExecutionQueryResult(AltibaseStatement.java:414)
            at Altibase.jdbc.driver.AltibaseStatement.executeQuery(AltibaseStatement.java:754)
        ```
    
    -   **예상 결과**
    
            정상적으로 insert 성공
    
-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49605 Updatable ResultSet을 이용해 데이터 입력 시 Unsupported type conversion SQLException 에러가 발생하는 현상을 수정합니다.

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : Updatable ResultSet 객체를 이용해 데이터 입력 시 Unsupported type conversion SQLException 에러가 발생하는 현상을 수정합니다. 
    
    > Updatable ResultSet 객체 : 업데이트 허용(CONCUR_UPDATABLE) 옵션을 사용한 ResultSet 객체
    
    본 버그를 적용하려면 Altibase JDBC 드라이버를 7.1.0.7.2 이상으로 패치해야 합니다.
    
-   **재현 방법**

    -   **재현 절차**

        ```java
        CommonBinaryColumn.setValueSub(Duration);
        CommonBinaryColumn.setValueSub(ByteArrayInputStream;
        CommonCharVarcharColumn.setValueSub(Clob);
        CommonCharVarcharColumn.setValueSub(StringReader);
        CommonCharVarcharColumn.setValueSub(ByteArrayInputStream)FloatColumn.getObjectSub();
        TimestampColumn.setValueSub(Time);
        ```

    -   **수행 결과**

            Unsupported type conversion SQLException 발생

    -   **예상 결과**

            정상 처리

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49613 = 연산자와 CAST 연산자에 사용된 서브쿼리의 결과가 NULL일 때 Altibase 서버가 비정상 종료할 수 있습니다.

-   **module** : qp

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : = 연산자와 CAST 연산자에 사용된 서브쿼리의 결과가 NULL일 때 Altibase 서버가 비정상 종료하는 현상을 수정합니다.
    
-   **재현 방법**

    -   **재현 절차**

        ```sql
        CREATE TABLE T1 ( I1 INTEGER, I2 INTEGER, I3 INTEGER ) TABLESPACE SYS_TBS_DISK_DATA;
        INSERT INTO T1 VALUES (1, 1, NULL);
        CREATE TABLE T2 ( I1 INTEGER ) TABLESPACE SYS_TBS_DISK_DATA;
        SELECT * FROM T1 WHERE I1 = (SELECT DISTINCT I1 || I2 FROM T2);
        ```

    -   **수행 결과**

            [ERR-91015 : Communication failure.]

    -   **예상 결과**

            No rows selected.

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49619 디스크 인덱스에서 언두 테이블스페이스를 사용하는 경우 다른 트랜젝션에 의해 언두 영역이 재사용되어 Altibase 서버가 비정상 종료할 수 있습니다.

-   **module** : sm-disk-index

-   **Category** : Fatal

-   **재현 빈도** : Rare

-   **설명** : 디스크 인덱스에서 언두 테이블스페이스를 사용하는 경우 다른 트랜젝션에 의해 언두 영역이 재사용되어 Altibase 서버가 비정상 종료하는 현상을 수정합니다.
    
    본 버그로 인한 Altibase 서버 비정상 종료 발생 시 트레이스 로그에 아래와 같은 로그가 기록됩니다.

    - altibase\_error.log
    
      ```bash
      [ASSERT] ERROR LINE => [sdnIndexCTL.cpp:2208]
      ```
    
    - altibase\_boot.log 에 아래와 같은 형태의 인덱스 및 언두 페이지 정보 기록
    
      ```bash
      [2022/02/09 16:42:10] [Thread-28749] [Level-0]
        Undo PageID               : 56023
        Undo Slot Number          : 91
        UndoRec Hdr Type          : 2
        Chained CTS's Commit SCN  : 61801506952
        Min DskView SCN           : 61801348159
      ```
    
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

### BUG-49620 NVL_EQUAL(expr1, exp2, expr3)에서 expr1에 인덱스가 존재하고 expr2의 컬럼의 데이터 타입이 expr1과 다른 경우 테이블 스캔 방식을 변경하여 제품의 안정성을 향상합니다.

-   **module** : qp

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : NVL\_EQUAL(expr1, exp2, expr3)에서 expr1에 인덱스가 존재하고 expr2의 컬럼의 데이터 타입이 expr1과 다른 경우 Altibase 서버가 비정상 종료하는 현상을 수정합니다.
    
-   **재현 방법**

    -   **재현 절차**

        ```sql
        CREATE TABLE T1( I1 INTEGER, I2 VARCHAR(10) ) PARTITION BY HASH( I1 ) ( PARTITION P1, PARTITION P2 TABLESPACE SYS_TBS_MEM_DATA, PARTITION P3 ) TABLESPACE SYS_TBS_DISK_DATA;
        CREATE INDEX IDX1 ON T1(I1) LOCAL;
        SELECT * FROM T1 WHERE NVL_EQUAL(I1,I2,2);
        ```

    -   **수행 결과**

        ```sql
        Altibase 서버 비정상 종료
        
        ALTER SESSION SET EXPLAIN PLAN = ONLY; 수행 후 SELECT 수행 시 실행 계획
        ------------------------------------------------------------
        PROJECT ( COLUMN_COUNT: 2, TUPLE_SIZE: 16, COST: 58.66 )
         PARTITION-COORDINATOR ( TABLE: SYS.T1, PARTITION: 3/3, ACCESS: ??, COST: 57.87 )
          SCAN ( PARTITION: P3, INDEX: SYS.IDX1, RANGE SCAN, ACCESS: ??, COST: 23.09 )
          SCAN ( PARTITION: P2, INDEX: SYS.IDX1, RANGE SCAN, ACCESS: ??, COST: 11.69 )
          SCAN ( PARTITION: P1, INDEX: SYS.IDX1, RANGE SCAN, ACCESS: ??, COST: 23.09 )
        ------------------------------------------------------------
        ```

    -   **예상 결과**

        ```sql
        I1          I2          
        ---------------------------
        No rows selected.
        
        
        ALTER SESSION SET EXPLAIN PLAN = ONLY; 수행 후 SELECT 수행 시 실행 계획
        ------------------------------------------------------------
        PROJECT ( COLUMN_COUNT: 2, TUPLE_SIZE: 16, COST: 386.68 )
         PARTITION-COORDINATOR ( TABLE: SYS.T1, PARTITION: 3/3, FULL SCAN, ACCESS: 0, COST: 385.88 )
          SCAN ( PARTITION: P3, FULL SCAN, ACCESS: 0, DISK_PAGE_COUNT: 64, COST: 129.28 )
          SCAN ( PARTITION: P2, FULL SCAN, ACCESS: 0, COST: 127.32 )
          SCAN ( PARTITION: P1, FULL SCAN, ACCESS: 0, DISK_PAGE_COUNT: 64, COST: 129.28 )
        ------------------------------------------------------------
        ```

        

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49632 반환 데이터 타입이 LOB인 저장 함수가 ORDER BY/GROUP BY/윈도우 함수의 PARTITION BY 하위절에 사용될 때 예외 처리를 변경하여 제품의 안정성을 향상합니다.

-   **module** : qp

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : 반환 데이터 타입이 LOB인 저장 함수가 ORDER BY/GROUP BY/윈도우 함수의 PARTITION BY 하위절에 사용될 때 Altibase 서버가 비정상 종료하는 현상을 개선합니다.
    
-   **재현 방법**

    -   **재현 절차**

        ```sql
        CREATE TABLE T1( I1 CHAR(10), I2 CHAR(10), I3 CHAR(10), I4 CHAR(10) ) TABLESPACE SYS_TBS_MEM_DATA;
        CREATE FUNCTION FUNC1
        (V1 CLOB) 
        RETURN CLOB 
        AS
          V2 CLOB; 
        BEGIN 
          V2 := V1; 
          RETURN V2; 
        END;
        /
        INSERT INTO T1(I2) VALUES (637);
        SELECT GROUPING_ID(FUNC1(I1)) 
          FROM T1 
         GROUP BY GROUPING SETS(1), FUNC1(I1);
        ```

    -   **수행 결과**

            Altibase 서버 비정상 종료

    -   **예상 결과**

        ```sql
        [ERR-3123E : An incomparable data type (GEOMETRY,LOB) cannot be used in a SELECT statement that has a DISTINCT clause.]
        ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49633 집계 함수에 DISTINCT 키워드를 사용한 SQL 수행 시 DISTINCT 처리를 위한 메모리 과다 사용으로 SQL 수행 성능이 하락합니다.

-   **module** : qp-select

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** :

    집계 함수에 DISTINCT 키워드를 사용한 SQL 수행 시 DISTINCT 처리를 위한 해시 버킷 수 과다 사용으로 메모리 사용이 증가하여 SQL 수행 성능이 하락하는 현상을 개선합니다. 본 버그 현상이 발생하는 경우 운영 환경에 적합한 해시 버킷 수를 설정할 수 있는 프로퍼티를 제공합니다. 히든 프로퍼티로 매뉴얼에 설명을 추가하지 않습니다.
    
    - 프로퍼티 추가 

      - 이름
    
        \_\_AGGREGATION\_DISTINCT\_BUCKET\_COUNT\_MAX
    
      - 설명
    
        집계 함수에서 DISTINCT 처리를 위한 최대 해시 버킷 수를 지정하는 프로퍼티이다. 
    
      - 값
    
        1 \~ 102400000
    
      - 기본값
    
        102400000

      - 속성

        변경 가능, 비공개

    
    또한, SQL에서 사용된 해시 버킷 수를 실행 계획에 표시합니다. 이 값을 참고하여  _\_AGGREGATION\_DISTINCT\_BUCKET\_COUNT\_MAX 설정할 수 있습니다. DISTINCT 키워드가 집계 함수, OVER, GROUP BY ROLLUP, GROUP BY CUBE와 함께 사용한 SQL의 실행 계획에서 확인할 수 있습니다. 
    
    - 영향을 받는 SQL 예시
    
      ```sql
      SELECT COUNT(DISTINCT i1) FROM t1;
      SELECT SUM( DISTINCT I2 ) OVER ( PARTITION BY I1 ) FROM T1;
      SELECT SUM( DISTINCT I2 ) FROM T1 GROUP BY ROLLUP ( I1, I3, I4 );
      SELECT SUM( DISTINCT I2 ) FROM T1 GROUP BY CUBE ( I1, I3, I4 );
      ```
    
    \_\_AGGREGATION\_DISTINCT\_BUCKET\_COUNT\_MAX 프로퍼티의 기본값은 102400000 입니다. 운영 중 이보다 작게 설정하기를 원할 경우 ALTER SYSTEM 으로 변경할 수 있습니다. 영구적으로 작은 값을 설정하려면 altibase.properties에 추가한 후 Altibase 서버를 재구동해야 합니다.
    
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

### BUG-49636 Altibase 서버 프로퍼티 ARCHIVE\_FULL\_ACTION 설정 값에 따른 아카이브로그 쓰레드의 동작을 개선합니다.

-   **module** : sm

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : 디스크 공간 부족으로 로그 파일 백업이 실패하는 경우 ARCHIVE\_FULL\_ACTION 설정 값에 따른 아카이브로그 쓰레드의 동작을 
    개선합니다.

    **ARCHIVE\_FULL\_ACTION 설정 값에 따른 동작 차이**

    - ARCHIVE\_FULL\_ACTION = 0 
      - 변경 전 : 디스크 공간 부족 발생으로 로그 파일 백업이 실패하는 경우 백업이 성공할 때까지 대기합니다.
      - 변경 후 : 디스크 공간 부족 발생으로 로그 파일 백업이 실패하는 경우 트레이스 로그(altibase_sm.log)에 기록하고 다음 로그 파일 백업을 시도합니다.

    - ARCHIVE\_FULL\_ACTION = 1 
      - 변경이 없습니다.

    - ARCHIVE\_FULL\_ACTION = 2
      - 설정값 2가 추가되었습니다. 디스크 공간 부족 실패 외에 다른 이유로 로그 파일 백업이 실패하는 경우 트레이스 로그(altibase\_sm.log)에 에러 메시지를 출력하고 다음 로그 파일의 백업을 시도합니다.

    **ARCHIVE\_FULL\_ACTION 속성 변경**

    읽기 전용에서 변경 가능으로 변경합니다.

    - 변경 전

      ```sql
      iSQL> ALTER SYSTEM SET ARCHIVE_FULL_ACTION = 2;
      [ERR-0104E : The property [ARCHIVE_FULL_ACTION] is read-only.]
      ```

    - 변경 후

      ```sql
      iSQL> ALTER SYSTEM SET ARCHIVE_FULL_ACTION = 2;
      Alter success
      ```

    ARCHIVE\_FULL\_ACTION 설정 값에 관한 설명은 [General Reference-1.Data Types & Altibase Properties](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/General%20Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#archive_full_action)에서도 확인할 수 있습니다.

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

### BUG-49647 Ubuntu 16, Ubuntu 18에서 altiMon 실행 시 com.altibase.picl.LibLoader.OsNotSupportedException 에러가 발생합니다.

-   **module** : ux-altiMon

-   **Category** : Portability

-   **재현 빈도** : Always

-   **설명** : Linux kernel 4 미지원으로 Ubuntu 16, Ubuntu 18에서 altiMon 실행 시 com.altibase.picl.LibLoader.OsNotSupportedException 에러가 발생합니다.

    altiMon에서 Linux kernel 4.x 지원하도록 추가합니다.

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

### BUG-49655 디스크 테이블 및 디스크 인덱스에서 사용 중인 데이터 페이지수를 조회할 수 있도록 X\$SEGMENT에 TOTAL\_USED\_PAGE\_CNT 컬럼을 추가합니다.

-   **module** : sm

-   **Category** : Other

-   **재현 빈도** : Always

-   **설명** : 디스크 테이블 및 디스크 인덱스에서 사용 중인 데이터 페이지 수를 조회할 수 있도록 X\$SEGMENT에 TOTAL\_USED\_PAGE\_CNT
    컬럼을 추가합니다. TOTAL\_USED\_PAGE\_CNT 컬럼은 메타 페이지와 FREE 페이지를 제외한 데이터만 있는 페이지 수를 의미합니다.

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
|    7.1.0.7.2     |          6.5.1          |    8.10.1    |        7.1.7        |            7.4.7             |

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

Replication 프로토콜 버전은 변경되지 않았다..

### 프로퍼티

#### 추가된 프로퍼티

#### 변경된 프로퍼티

#### 삭제된 프로퍼티

### 성능 뷰

#### 추가된 성능 뷰

#### 변경된 성능 뷰

#### 삭제된 성능 뷰
