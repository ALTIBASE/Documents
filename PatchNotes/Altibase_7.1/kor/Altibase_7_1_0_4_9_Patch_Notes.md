<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Altibase 7.1.0.4.9 Patch Notes](#altibase-71049-patch-notes)
  - [New Features](#new-features)
    - [BUG-47821 iloader에서 EWKB 형식을 지원합니다.](#bug-47821iloader%EC%97%90%EC%84%9C-ewkb-%ED%98%95%EC%8B%9D%EC%9D%84-%EC%A7%80%EC%9B%90%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-48288 타 제품과 동일한 이름의 힌트를 Altibase 만 인식할 수 있는 방법을 제공합니다.](#bug-48288%ED%83%80-%EC%A0%9C%ED%92%88%EA%B3%BC-%EB%8F%99%EC%9D%BC%ED%95%9C-%EC%9D%B4%EB%A6%84%EC%9D%98-%ED%9E%8C%ED%8A%B8%EB%A5%BC-altibase-%EB%A7%8C-%EC%9D%B8%EC%8B%9D%ED%95%A0-%EC%88%98-%EC%9E%88%EB%8A%94-%EB%B0%A9%EB%B2%95%EC%9D%84-%EC%A0%9C%EA%B3%B5%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-48323 aexport 에서 SRID를 지원해야 합니다](#bug-48323aexport-%EC%97%90%EC%84%9C-srid%EB%A5%BC-%EC%A7%80%EC%9B%90%ED%95%B4%EC%95%BC-%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-48348 partial CSE 기능 추가](#bug-48348partial-cse-%EA%B8%B0%EB%8A%A5-%EC%B6%94%EA%B0%80)
    - [BUG-48357 iloader out 인자에 -WKB 옵션을 추가합니다.](#bug-48357iloader-out-%EC%9D%B8%EC%9E%90%EC%97%90--wkb-%EC%98%B5%EC%85%98%EC%9D%84-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-47870 동일한 디스크 테이블을 가진 이중화 객체 두 개 중 한 개를 삭제하면 이중화가 전송되지 않습니다.](#bug-47870%EB%8F%99%EC%9D%BC%ED%95%9C-%EB%94%94%EC%8A%A4%ED%81%AC-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%9D%84-%EA%B0%80%EC%A7%84-%EC%9D%B4%EC%A4%91%ED%99%94-%EA%B0%9D%EC%B2%B4-%EB%91%90-%EA%B0%9C-%EC%A4%91-%ED%95%9C-%EA%B0%9C%EB%A5%BC-%EC%82%AD%EC%A0%9C%ED%95%98%EB%A9%B4-%EC%9D%B4%EC%A4%91%ED%99%94%EA%B0%80-%EC%A0%84%EC%86%A1%EB%90%98%EC%A7%80-%EC%95%8A%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-48090 __OPTIMIZER_VIEW_TARGET_ENABLE = 1 에서 WITH 절과 서브쿼리가 사용된 쿼리 수행 시 결과 오류가 발생할 수 있습니다.](#bug-48090__optimizer_view_target_enable--1-%EC%97%90%EC%84%9C-with-%EC%A0%88%EA%B3%BC-%EC%84%9C%EB%B8%8C%EC%BF%BC%EB%A6%AC%EA%B0%80-%EC%82%AC%EC%9A%A9%EB%90%9C-%EC%BF%BC%EB%A6%AC-%EC%88%98%ED%96%89-%EC%8B%9C-%EA%B2%B0%EA%B3%BC-%EC%98%A4%EB%A5%98%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-48179 삼중화 이상의 Altibase 이중화 환경에서 이중화 대상 테이블에 TRUNCATE 수행 시 ERR-11041 : A deadlock situation has been detected. 에러가 발생할 수 있습니다.](#bug-48179%EC%82%BC%EC%A4%91%ED%99%94-%EC%9D%B4%EC%83%81%EC%9D%98-altibase-%EC%9D%B4%EC%A4%91%ED%99%94-%ED%99%98%EA%B2%BD%EC%97%90%EC%84%9C-%EC%9D%B4%EC%A4%91%ED%99%94-%EB%8C%80%EC%83%81-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90-truncate-%EC%88%98%ED%96%89-%EC%8B%9C-err-11041--a-deadlock-situation-has-been-detected-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-48300 CONNECT BY 절이 포함된 SQL 수행 시 ERR-3111D : There are too many DML statements in the stored procedure, or the SQL query is too long. 에러가 발생할 수 있습니다.](#bug-48300connect-by-%EC%A0%88%EC%9D%B4-%ED%8F%AC%ED%95%A8%EB%90%9C-sql-%EC%88%98%ED%96%89-%EC%8B%9C-err-3111d--there-are-too-many-dml-statements-in-the-stored-procedure-or-the-sql-query-is-too-long-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-48333 세션 타임아웃 조건에서도 세션이 종료되지 않아, 무한대기(HANG) 현상이 발생합니다.](#bug-48333%EC%84%B8%EC%85%98-%ED%83%80%EC%9E%84%EC%95%84%EC%9B%83-%EC%A1%B0%EA%B1%B4%EC%97%90%EC%84%9C%EB%8F%84-%EC%84%B8%EC%85%98%EC%9D%B4-%EC%A2%85%EB%A3%8C%EB%90%98%EC%A7%80-%EC%95%8A%EC%95%84-%EB%AC%B4%ED%95%9C%EB%8C%80%EA%B8%B0hang-%ED%98%84%EC%83%81%EC%9D%B4-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-48337 UNION ALL 에서 서로 다른 데이터 타입의 컬럼이 사용된 경우 Altibase 서버가 비정상 종료합니다.](#bug-48337union-all-%EC%97%90%EC%84%9C-%EC%84%9C%EB%A1%9C-%EB%8B%A4%EB%A5%B8-%EB%8D%B0%EC%9D%B4%ED%84%B0-%ED%83%80%EC%9E%85%EC%9D%98-%EC%BB%AC%EB%9F%BC%EC%9D%B4-%EC%82%AC%EC%9A%A9%EB%90%9C-%EA%B2%BD%EC%9A%B0-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-48355 AltibaseDatabaseMeta 객체가 생성될 때마다 V$RESERVED_WORDS 를 조회하는 문제를 수정합니다.](#bug-48355altibasedatabasemeta-%EA%B0%9D%EC%B2%B4%EA%B0%80-%EC%83%9D%EC%84%B1%EB%90%A0-%EB%95%8C%EB%A7%88%EB%8B%A4-vreserved_words-%EB%A5%BC-%EC%A1%B0%ED%9A%8C%ED%95%98%EB%8A%94-%EB%AC%B8%EC%A0%9C%EB%A5%BC-%EC%88%98%EC%A0%95%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-48360 Altibase.jdbc.driver.cm.CmChannel.sendPacket() 에서 예외가 발생한 경우 통신 버퍼 상태 이상으로 프로토콜이 유실될 수 있습니다.](#bug-48360altibasejdbcdrivercmcmchannelsendpacket-%EC%97%90%EC%84%9C-%EC%98%88%EC%99%B8%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%9C-%EA%B2%BD%EC%9A%B0-%ED%86%B5%EC%8B%A0-%EB%B2%84%ED%8D%BC-%EC%83%81%ED%83%9C-%EC%9D%B4%EC%83%81%EC%9C%BC%EB%A1%9C-%ED%94%84%EB%A1%9C%ED%86%A0%EC%BD%9C%EC%9D%B4-%EC%9C%A0%EC%8B%A4%EB%90%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-48370 DB Link 쿼리를 수행하는 세션에서 TRCLOG_DETAIL_PREDICATE = 1 설정 후 원격 테이블 조회 시 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-48370db-link-%EC%BF%BC%EB%A6%AC%EB%A5%BC-%EC%88%98%ED%96%89%ED%95%98%EB%8A%94-%EC%84%B8%EC%85%98%EC%97%90%EC%84%9C-trclog_detail_predicate--1-%EC%84%A4%EC%A0%95-%ED%9B%84-%EC%9B%90%EA%B2%A9-%ED%85%8C%EC%9D%B4%EB%B8%94-%EC%A1%B0%ED%9A%8C-%EC%8B%9C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-48390 INDEX_BUILD_THREAD_COUNT 프로퍼티의 기본값이 1로 설정되는 문제가 있습니다.](#bug-48390index_build_thread_count-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0%EC%9D%98-%EA%B8%B0%EB%B3%B8%EA%B0%92%EC%9D%B4-1%EB%A1%9C-%EC%84%A4%EC%A0%95%EB%90%98%EB%8A%94-%EB%AC%B8%EC%A0%9C%EA%B0%80-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-48393 리눅스에서 ST_Transfrom 함수를 사용할 수 없는 문제가 있습니다.](#bug-48393%EB%A6%AC%EB%88%85%EC%8A%A4%EC%97%90%EC%84%9C-st_transfrom-%ED%95%A8%EC%88%98%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%A0-%EC%88%98-%EC%97%86%EB%8A%94-%EB%AC%B8%EC%A0%9C%EA%B0%80-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Altibase 7.1.0.4.9 Patch Notes
==============================

New Features
------------

### BUG-47821 iloader에서 EWKB 형식을 지원합니다. 

-   **module** : ux-iloader

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **증상** : iloader에서 EWKB 형식의 공간 데이터를 in/out 할 수 있도록 지원합니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    DROP TABLE T1;
    CREATE TABLE T1(I1 GEOMETRY(1000) SRID 4326);
    INSERT INTO T1 VALUES(GEOMETRY'POINT(1 1)');
    INSERT INTO T1 VALUES(GEOMETRY'SRID=4326;POINT(1 1)');
    INSERT INTO T1 VALUES(GEOMETRY'LINESTRING(1 1, 2 2, 1 1)');
    INSERT INTO T1 VALUES(GEOMETRY'SRID=4326;LINESTRING(1 1, 2 2, 1 1)');
    
    SET VERTICAL ON;
    SELECT * FROM GEOMETRY_COLUMNS WHERE F_TABLE_NAME = 'T1' ORDER BY 1, 2, 3;
    
    SELECT SRID(I1), ASEWKT(I1,100) FROM T1;
    
    $ aexport -S 127.0.0.1 -U SYS -P MANAGER
    $ sh run_il_out.sh
    
    DROP TABLE T1;
    
    $ isql -s 127.0.0.1 -u sys -p manager -f all_crt_tbl.sql
    $ sh run_il_in.sh
    
    SET VERTICAL ON;
    SELECT * FROM GEOMETRY_COLUMNS WHERE F_TABLE_NAME = 'T1' ORDER BY 1, 2, 3;
    SELECT SRID(I1), ASEWKT(I1,100) FROM T1;
    ```

  - **수행 결과**

    ```sql
    iSQL> SELECT * FROM GEOMETRY_COLUMNS WHERE F_TABLE_NAME = 'T1' ORDER BY 1, 2, 3;
    F_TABLE_SCHEMA    : SYS
    F_TABLE_NAME      : T1
    F_GEOMETRY_COLUMN : I1
    COORD_DIMENSION   : 2
    SRID              : 0
    1 row selected.
    
    iSQL> SELECT SRID(I1), ASEWKT(I1,100) FROM T1;
    SRID(I1)       : 0
    ASEWKT(I1,100) : SRID=0;POINT(1 1)
    SRID(I1)       : 0
    ASEWKT(I1,100) : SRID=0;POINT(1 1)
    SRID(I1)       : 0
    ASEWKT(I1,100) : SRID=0;LINESTRING(1 1, 2 2, 1 1)
    SRID(I1)       : 0
    ASEWKT(I1,100) : SRID=0;LINESTRING(1 1, 2 2, 1 1)
    4 rows selected.
    ```

  -   **예상 결과**

      ```sql
      iSQL> SELECT * FROM GEOMETRY_COLUMNS WHERE F_TABLE_NAME = 'T1' ORDER BY 1, 2, 3;
      GEOMETRY_COLUMNS.F_TABLE_SCHEMA    : SYS
      GEOMETRY_COLUMNS.F_TABLE_NAME      : T1
      GEOMETRY_COLUMNS.F_GEOMETRY_COLUMN : I1
      GEOMETRY_COLUMNS.COORD_DIMENSION   : 2
      GEOMETRY_COLUMNS.SRID              : 4326
      1 row selected.
      
      iSQL> SELECT SRID(I1), ASEWKT(I1,100) FROM T1;
      SRID(I1)       : 0
      ASEWKT(I1,100) : SRID=0;POINT(1 1)
      SRID(I1)       : 4326
      ASEWKT(I1,100) : SRID=4326;POINT(1 1)
      SRID(I1)       : 0
      ASEWKT(I1,100) : SRID=0;LINESTRING(1 1, 2 2, 1 1)
      SRID(I1)       : 4326
      ASEWKT(I1,100) : SRID=4326;LINESTRING(1 1, 2 2, 1 1)
      4 rows selected.
      ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48288 타 제품과 동일한 이름의 힌트를 Altibase 만 인식할 수 있는 방법을 제공합니다.

- **module** : qp

- **Category** : Enhancement

- **재현 빈도** : Always

- **증상** :  타 제품과 동일한 이름의 힌트를 Altibase 만 인식할 수 있는 방법을 제공합니다. 

  - 모든 힌트에 ALTI_ 접두사를 사용합니다. 

  - 두 개 이상의 키워드로 구성된 힌트의 경우 공란을 언더바(under bar)로 변경 후 ALTI_ 접두사를 추가합니다.   

    예) NO INDEX -> ALTI_NO_INDEX 

- **재현 방법**

-   **재현 절차**
    
-   **수행 결과**
    
- **예상 결과**

- **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48323 aexport 에서 SRID를 지원해야 합니다

-   **module** : ux-aexport

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **증상** : aexport가 생성하는 CREATE TABLE DDL에 SRID를 지원합니다.

- **재현 방법**

  - **재현 절차**

    ```sql
    CREATE TABLE BUG_48323 (i1 INT PRIMARY KEY, i2 GEOMETRY(1000) SRID 4326);
    SET VERTICAL ON;
    
    SELECT F_GEOMETRY_COLUMN, SRID
      FROM GEOMETRY_COLUMNS
     WHERE F_TABLE_SCHEMA = 'SYS'
       AND F_TABLE_NAME = 'BUG_48323';
    F_GEOMETRY_COLUMN : I2
    SRID : 4326
    1 row selected.
    
    $ aexport -s 127.0.0.1 -u sys -p manager -object SYS.BUG_48323
    
    DROP TABLE BUG_48323;
    
    $ is -f SYS_BUG_48323_CRT.sql
    ```

  - **수행 결과**

    ```sql
    SET VERTICAL ON;
    SELECT F_GEOMETRY_COLUMN, SRID
      FROM GEOMETRY_COLUMNS
     WHERE F_TABLE_SCHEMA = 'SYS'
       AND F_TABLE_NAME = 'BUG_48323';
    F_GEOMETRY_COLUMN : I2
    SRID : 0
    1 row selected.
    ```

  -   **예상 결과**

      ```sql
      SET VERTICAL ON;
      SELECT F_GEOMETRY_COLUMN, SRID
        FROM GEOMETRY_COLUMNS
       WHERE F_TABLE_SCHEMA = 'SYS'
         AND F_TABLE_NAME = 'BUG_48323';
      F_GEOMETRY_COLUMN : I2
      SRID : 4326
      1 row selected.
      ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48348 partial CSE 기능 추가

-   **module** : qp-dml-pvo

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **증상** : partial CSE 기능 추가

- **재현 방법**

  - **재현 절차**

    ```sql
    CREATE TABLE T1 ( I1 INT, I2 INT);
    ALTER SESSION SET TRCLOG_DETAIL_PREDICATE = 1;
    
    SELECT *
      FROM T1
     WHERE (I1 = 1 AND I2 = 1)
        OR (I1 = 1 AND I2 = 2)
        OR (I1 = 1 AND I2 = 2);
    ```

  - **수행 결과**

    ```sql
    ALTER SESSION SET __OPTIMIZER_ELIMINATE_COMMON_SUBEXPRESSION = 2;
    [ERR-51214 : The ulnSetConnAttributeForDbc of client-side sharding failed due to the following reason: Attribute is invalid.]
    ```

  -   **예상 결과**

      ```sql
      ALTER SESSION SET __OPTIMIZER_ELIMINATE_COMMON_SUBEXPRESSION = 2;
      Alter success.
      
      SELECT *
        FROM T1
       WHERE (I1 = 1 AND I2 = 1)
          OR (I1 = 1 AND I2 = 2)
          OR (I1 = 1 AND I2 = 2);
      T1.I1       T1.I2
      ---------------------------
      No rows selected.
      ------------------------------------------------------------
      PROJECT ( COLUMN_COUNT: 2, TUPLE_SIZE: 8, COST: BLOCKED )
       SCAN ( TABLE: SYS.T1, FULL SCAN, ACCESS: 0, COST: BLOCKED )
        [ FILTER ]
        AND
         OR
          I2 = 1
          I2 = 2
         OR
          I1 = 1
          I2 = 2
         OR
          I2 = 1
          I1 = 1
         OR
          I1 = 1
          I1 = 1
      ------------------------------------------------------------
      ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48357 iloader out 인자에 -geom WKB 옵션을 추가합니다.

-   **module** : ux-iloader

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **증상** : iloader out 인자에 -geom WKB 옵션을 추가합니다. Altibase 7.1.0.4.0 이상에서 제공하는 EWKB(Extended Well-KnownBinary) 형식의 공간 데이터를 WKB(Well-Known Binary) 형식으로 다운로드할 때 이 옵션을 사용합니다. 
    
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

### BUG-47870 동일한 디스크 테이블을 가진 이중화 객체 두 개 중 한 개를 삭제하면 이중화가 전송되지 않습니다.

-   **module** : rp

-   **Category** : Testcase Error

-   **재현 빈도** : Always

-   **증상** : 동일한 디스크 파티션 테이블을 가진 이중화 객체 두 개 중 한 개를 삭제(DROP REPLICATION)한 경우, 이중화 정보 업데이트 오류로 이중화가 전송되지 않는 문제를 수정했습니다.
    
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

### BUG-48090 __OPTIMIZER_VIEW_TARGET_ENABLE = 1 에서 WITH 절과 서브쿼리가 사용된 쿼리 수행 시 결과 오류가 발생할 수 있습니다.

-   **module** : qp-select-pvo

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : __OPTIMIZER_VIEW_TARGET_ENABLE = 1 에서 WITH 절과 서브쿼리가 사용된 쿼리 수행 시 결과 오류가 발생하는 현상을 수정하였습니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    DROP TABLE t1;
    DROP TABLE t2;
    CREATE TABLE t1 ( c1 VARCHAR(20) );
    CREATE TABLE t2 ( c1 VARCHAR(20), c2 VARCHAR(20) );
    INSERT INTO t1 VALUES ( 'AT100' );
    INSERT INTO t1 VALUES ( 'OT100' );
    INSERT INTO t1 VALUES ( 'BT100' );
    INSERT INTO t1 VALUES ( 'OT100' );
    INSERT INTO t1 VALUES ( 'CT100' );
    INSERT INTO t2 VALUES ( 'AT100', 'Unexpected result 1' );
    INSERT INTO t2 VALUES ( 'OT100', 'Expected result 1' );
    INSERT INTO t2 VALUES ( 'BT100', 'Unexpected result 2' );
    INSERT INTO t2 VALUES ( 'OT100', 'Expected result 2' );
    INSERT INTO t2 VALUES ( 'CT100', 'Unexpected result 3' );
    var v1 varchar(20);
    exec :v1 := 'N';
    1) 
    PREPARE
    WITH w1 ( c1, c2 )
    AS (
        SELECT ' ' AS c1, 'x' AS c2
        FROM DUAL
        UNION ALL
        SELECT ' ' AS c1, 'x' AS c2
        FROM DUAL
        INNER JOIN w1 ON c2 = w1.c1
        )
        , w2
    AS (
        SELECT ' ' AS c1, 'x' AS c2
        FROM DUAL
        INNER JOIN w1 ON c2 = w1.c1
        UNION
        SELECT c1, 'x' AS c2
        FROM t1
        WHERE c1 NOT IN (
                SELECT c2
                FROM w1
                )
        )
    SELECT /*+ no_plan_cache */ c2
    FROM t2
    WHERE t2.c1 IN (
            SELECT c1
            FROM w2
            )
        AND (
            t2.c1 = 'OT100'
            OR (
                :v1 = 'Y'
                AND t2.c1 IN (
                    SELECT c1
                    FROM w2
                    )
                )
            );
    2) 
    WITH w1
    AS (
        SELECT 'w1c1' w1c1
            ,'w1c2' w1c2
        FROM dual
        )
        ,w2
    AS (
        SELECT w1c1 w2c1
            ,(
                SELECT w1c2
                FROM dual
                ) w2c2
            ,'w2c3' w2c3
        FROM w1
        )
        ,w3
    AS (
        SELECT w2c2 w3c2
        FROM w2
        )
    SELECT (
            SELECT w3.w3c2
            FROM w3 LIMIT 1
            ) AS w3c2
    FROM DUAL;
    3)
    WITH w1
    AS (
        SELECT 'w1c1' w1c1
            ,'w1c2' w1c2
        FROM dual
        )
        ,w2
    AS (
        SELECT w1c1 w2c1
            ,(
                SELECT w1c2
                FROM dual
                ) w2c2
            ,'w2c3' w2c3
        FROM w1
        )
        ,w3
    AS (
        SELECT 'w1c1value' AS w3c1, w2c2 w3c2
        FROM w2
        )
    SELECT w3c2
    FROM w3 WHERE w3c1 NOT IN (SELECT w3.w3c2
            FROM w3);
    4)
    WITH w1
    AS (
        SELECT 'w1c1' w1c1
            ,'w1c2' w1c2
        FROM dual
        )
        ,w2
    AS (
        SELECT w1c1 w2c1
            ,(
                SELECT w1c2
                FROM dual
                ) w2c2
            ,'w2c3' w2c3
        FROM w1
        )
        ,w3
    AS (
        SELECT 'w1c1value' AS w3c1, w2c2 w3c2
        FROM w2
        )
    SELECT w3c2
    FROM w3 WHERE w3c1 IN (SELECT w3.w3c1
            FROM w3);
    ```

  - **수행 결과**

    ```sql
    1) No rows selected.
    2) 1 row selected.
    3) No rows selected.
    4) 1 row selected.
    ```

  -   **예상 결과**

      ```sql
      1) 
      Expected result 1
      Expected result 2
      2 rows selected.
      2)
      w1c2
      1 row selected.
      3)
      w1c2
      1 row selected.
      4)
      w1c2
      1 row selected.
      ```

- **Workaround**

  ```sql
  ALTER SYSTEM SET __OPTIMIZER_VIEW_TARGET_ENABLE = 0;
  ```

- **변경사항**

  -   Performance view

  -   Property

  -   Compile Option

  -   Error Code

### BUG-48179 삼중화 이상의 Altibase 이중화 환경에서 이중화 대상 테이블에 TRUNCATE 수행 시 ERR-11041 : A deadlock situation has been detected. 에러가 발생할 수 있습니다.

-   **module** : rp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : 삼중화 이상의 Altibase 이중화 환경에서 DDL_LOCK_TIMEOUT 프로퍼티를 0 이 아닌 값으로 설정 후 이중화 대상 테이블에 TRUNCATE 수행할 경우 데드락(deadlock) 에러가 발생할 수 있습니다. DDL_LOCK_TIMEOUT 설정에 따라 이중화 동작에 데드락을 유발하는 문제를 수정하였습니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    삼중화 환경
    ALTER SYSTEM SET REPLICATION_DDL_ENABLE=1;
    ALTER SYSTEM SET DDL_LOCK_TIMEOUT=60;
    TRUNCATE TABLE T1;
    ```

  - **수행 결과**

    ```sql
    ERR-11041 : A deadlock situation has been detected.
    ```

  -   **예상 결과**

      ```sql
      Alter success.
      ```

- **Workaround**

      아래 2가지 방법 중 한 가지를 선택 적용하면 deadlock 에러를 회피할 수 있습니다.
      1. 이중화를 중지하고 TRUNCATE를 수행한다.
      2. ALTER SYSTEM SET DDL_LOCK_TIMEOUT = 0 설정 후 TRUNCATE 를 수행한다.

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48300 CONNECT BY 절이 포함된 SQL 수행 시 ERR-3111D : There are too many DML statements in the stored procedure, or the SQL query is too long. 에러가 발생할 수 있습니다.

-   **module** : qp-dml-pvo

-   **Category** : Efficiency

-   **재현 빈도** : Always

-   **증상** : 옵티마이저에서 CONNECT BY 절 처리 시 불필요한 자원 사용으로 ERR-3111D : There are too many DML statements in the stored procedure, or the SQL query is too long. 에러가 발생하는 현상을 수정하였습니다.
    
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

### BUG-48333 세션 타임아웃 조건에서도 세션이 종료되지 않아, 무한대기(HANG) 현상이 발생합니다.

-   **module** : sm-disk-index

-   **Category** : Hang

-   **재현 빈도** : Rare

-   **증상** : 세션 타임아웃 조건에서도 세션이 종료되지 않는 문제가 있어, timeout을 확인하는 코드를 추가합니다.
    
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

### BUG-48337 UNION ALL 에서 서로 다른 데이터 타입의 컬럼이 사용된 경우 Altibase 서버가 비정상 종료합니다.

-   **module** : qp-dml-execute

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **증상** : UNION ALL 에서 서로 다른 데이터 타입의 컬럼이 사용된 경우 데이터 타입 변환 과정에서 Altibase 서버가 비정상 종료하는 문제를 수정합니다.
    
-   **재현 방법**

    -   **재현 절차**

        ```sql
        DROP TABLE IE_IINVOICE_MST_X10005;
        CREATE TABLE IE_IINVOICE_MST_X10005( 
        COMPANY_CD  VARCHAR(28) NOT NULL,
        PARTNER_CD  VARCHAR(80) NOT NULL,
        INVC_NO     VARCHAR(80) NOT NULL,
        INVC_SQ     VARCHAR(5)  NOT NULL,
        SHIPNG_QT   VARCHAR(80)
        ) TABLESPACE SYS_TBS_DISK_DATA;
        
        INSERT INTO IE_IINVOICE_MST_X10005(COMPANY_CD, PARTNER_CD, INVC_NO, INVC_SQ ) SELECT LEVEL, LEVEL, LEVEL, LEVEL FROM DUAL CONNECT BY LEVEL < 10;
        
        DROP TABLE IE_IINVOICE_DTL_X10005;
        CREATE TABLE IE_IINVOICE_DTL_X10005( 
        COMPANY_CD  VARCHAR(28) NOT NULL,
        PARTNER_CD  VARCHAR(80) NOT NULL,
        INVC_NO     VARCHAR(80) NOT NULL,
        INVC_SQ     VARCHAR(5) NOT NULL,
        SHIPNG_QT   VARCHAR(80)
        ) TABLESPACE SYS_TBS_DISK_DATA;
        
        INSERT INTO IE_IINVOICE_DTL_X10005( COMPANY_CD, PARTNER_CD, INVC_NO, INVC_SQ ) SELECT LEVEL, LEVEL, LEVEL, LEVEL FROM DUAL CONNECT BY LEVEL < 10;
        
        SELECT /*+   */T.COMPANY_CD
             , SUM(T.LETCRDT_ESTBL_QT) LETCRDT_ESTBL_QT
          FROM (SELECT IIVM.COMPANY_CD
                     , - IIVD.SHIPNG_QT LETCRDT_ESTBL_QT
                  FROM IE_IINVOICE_MST_X10005 IIVM 
                  LEFT OUTER JOIN IE_IINVOICE_DTL_X10005 IIVD ON IIVD.COMPANY_CD = IIVM.COMPANY_CD
                 WHERE IIVM.COMPANY_CD = '1'
                   AND IIVM.INVC_NO = '1'
                 UNION ALL (SELECT '1' COMPANY_CD, -100 LETCRDT_ESTBL_QT
                              FROM DUAL
                             UNION ALL
                            SELECT '2' COMPANY_CD, -200 LETCRDT_ESTBL_QT
                              FROM DUAL) ) T
          WHERE COALESCE(LETCRDT_ESTBL_QT, 0) > 0
          GROUP BY T.COMPANY_CD;
        ```
    
-   **수행 결과**
    
        Altibase 서버 비정상 종료
    
-   **예상 결과**
    
    ```sql
    COMPANY_CD                    LETCRDT_ESTBL_QT 
    --------------------------------------------------
    No rows selected.
    ```
    
- **Workaround**

  ```sql
  UNION ALL 에서 사용한 괄호를 삭제합니다. 
  
  SELECT /*+   */T.COMPANY_CD
       , SUM(T.LETCRDT_ESTBL_QT) LETCRDT_ESTBL_QT
    FROM (SELECT IIVM.COMPANY_CD
               , - IIVD.SHIPNG_QT LETCRDT_ESTBL_QT
            FROM IE_IINVOICE_MST_X10005 IIVM 
            LEFT OUTER JOIN IE_IINVOICE_DTL_X10005 IIVD ON IIVD.COMPANY_CD = IIVM.COMPANY_CD
           WHERE IIVM.COMPANY_CD = '1'
             AND IIVM.INVC_NO = '1'
           UNION ALL
                      SELECT '1' COMPANY_CD
                                   , -100 LETCRDT_ESTBL_QT
                                FROM DUAL
                               UNION ALL
                      SELECT '2' COMPANY_CD
                                   , -200 LETCRDT_ESTBL_QT
                                FROM DUAL ) T
    WHERE COALESCE(LETCRDT_ESTBL_QT, 0) > 0
    GROUP BY T.COMPANY_CD;
  ```

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48355 AltibaseDatabaseMeta 객체가 생성될 때마다 V$RESERVED_WORDS 를 조회하는 문제를 수정합니다.

-   **module** : mm-jdbc

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **증상** : AltibaseDatabaseMetadata가 생성될 때마다 v$reserved를 조회하는 경우, 불필요한 자원이 낭비되는 문제가 있어 수정합니다.
    
-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

            AltibaseDatabaseMetadata 객체 생성될 때마다 SELECT keyword FROM v$reserved_words 수행

    -   **예상 결과**

            SELECT keyword FROM v$reserved_words 를 매번 수행하지 않고 AltibaseDatabaseMetadata 최초 객체 생성시 한번만 실행.

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48360 Altibase.jdbc.driver.cm.CmChannel.sendPacket() 에서 예외가 발생한 경우 통신 버퍼 상태 이상으로 프로토콜이 유실될 수 있습니다.

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : Altibase.jdbc.driver.cm.CmChannel.sendPacket() 에서 예외가 발생한 경우 통신 버퍼 상태 이상으로 프로토콜이 유실되는 문제를 수정했습니다. 이 현상이 발생한 경우 비정상적인 데이터 처리로Altibase 서버가 비정상 종료할 수 있습니다.
    
    이 버그 적용하려면 JDBC 드라이버를 7.1.0.4.9 이상으로 패치 해야 합니다.
    
- **재현 방법**

  - **재현 절차**

    ```java
    stmt.executeQuery("SELECT keyword FROM v$reserved_words");
    stmt.executeQuery("SELECT keyword FROM v$reserved_words");
    stmt.executeQuery("SELECT keyword FROM v$reserved_words"); // 여기서 소켓 전송시 SocketException 발생
    stmt.executeQuery("SELECT keyword FROM v$reserved_words");
    ```

  -   **수행 결과**

          4번째 execute를 하면서 버퍼의 상태가 초기화 되지 않아 헤더사이즈(16byte)만큼 유실 발생

  -   **예상 결과**

          소켓 전송 시 예외가 나더라도 프로토콜 유실이 발생하지 말아야 함.

-   **Workaround**

- **변경사항**

  -   Performance view

  -   Property

  -   Compile Option

  -   Error Code

### BUG-48370 DB Link 쿼리를 수행하는 세션에서 TRCLOG_DETAIL_PREDICATE = 1 설정 후 원격 테이블 조회 시 Altibase 서버가 비정상 종료할 수 있습니다.

-   **module** : qp-dml-execute

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **증상** :  DB Link 쿼리를 수행하는 세션에서 TRCLOG_DETAIL_PREDICATE = 1 설정 후 원격 테이블 조회 시 Altibase 서버가 비정상 종료하는 현상을 수정합니다. 
    
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

### BUG-48390 INDEX_BUILD_THREAD_COUNT 프로퍼티의 기본값이 1로 설정되는 문제가 있습니다.

-   **module** : id

-   **Category** : Maintainability

-   **재현 빈도** : Unknown

-   **증상** : CPU코어갯수를 리턴하는 내부함수의 문제로 인해, 7.1.0.4.5부터 INDEX_BUILD_THREAD_COUNT 프로퍼티의 기본값이 1로 설정되는 문제가 있습니다. 이로 인해 인덱스 빌드시 쓰레드 갯수가 너무 작게 설정되어 빌드성능이 나오지 않는 문제가 있었으며, 본패치는 해당문제를 해결합니다.
    
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

### BUG-48393 리눅스에서 ST_Transfrom 함수를 사용할 수 없는 문제가 있습니다.

-   **module** : st-spatial

-   **Category** : Compile Error

-   **재현 빈도** : Always

-   **증상** : Altibase 7.1.0.4.5 이상에서, 리눅스에서 ST_Transfrom 함수를 사용할 수 없는 문제를 수정하였습니다.
    
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
-------

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 7.1.0.4.9        | 6.5.1                   | 8.9.1        | 7.1.7               | 7.4.6                        |

> Altibase 7.1 패치 버전별 히스토리는 [Version_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7_1_Version_Histories.md)에서 확인할 수 있다.

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

추가/변경/삭제된 프로퍼티 없음

### 성능 뷰

추가/변경/삭제된 성능뷰 없음
