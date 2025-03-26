Altibase 7.1.0.4.9 Patch Notes
==============================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [New Features](#new-features)
  - [BUG-47821 iloader now supports the EWKB format.](#bug-47821%C2%A0iloader-now-supports-the-ewkb-format)
  - [BUG-48323 Support for SRID in aexport](#bug-48323%C2%A0support-for-srid-in-aexport)
  - [BUG-48348 Support for CSE(Common Subexpression Elimination)](#bug-48348%C2%A0support-for-csecommon-subexpression-elimination)
  - [BUG-48357 Added the -geom WKB option to the iloader out parameter.](#bug-48357%C2%A0added-the--geom-wkb-option-to-the-iloader-out-parameter)
- [Fixed Bugs](#fixed-bugs)
  - [BUG-47870 Fixed an issue where the replication would not be transmitted when deleting one of the two replication objects with the same disk table.](#bug-47870%C2%A0fixed-an-issue-where-the-replication-would-not-be-transmitted-when-deleting-one-of-the-two-replication-objects-with-the-same-disk-table)
  - [BUG-48090 Fixed an issue where a query with a WITH clause and a subquery resulted in an error when __OPTIMIZER_VIEW_TARGET_ENABLE was set to 1.](#bug-48090%C2%A0fixed-an-issue-where-a-query-with-a-with-clause-and-a-subquery-resulted-in-an-error-when-__optimizer_view_target_enable-was-set-to-1)
  - [BUG-48179 Fixed a deadlock error that occurred when performing a TRUNCATE on a replication target table in a triple or higher replication environment.](#bug-48179%C2%A0fixed-a-deadlock-error-that-occurred-when-performing-a-truncate-on-a-replication-target-table-in-a-triple-or-higher-replication-environment)
  - [BUG-48300 Fixed an issue in the optimizer where unnecessary resource usage during the processing of the `CONNECT BY` clause caused the error [ERR-3111D: There are too many DML statements in the stored procedure, or the SQL query is too long].](#bug-48300%C2%A0fixed-an-issue-in-the-optimizer-where-unnecessary-resource-usage-during-the-processing-of-the-connect-by-clause-caused-the-error-err-3111d-there-are-too-many-dml-statements-in-the-stored-procedure-or-the-sql-query-is-too-long)
  - [BUG-48333 Added code to check for session timeout to resolve the issue where sessions were not terminating under session timeout conditions.](#bug-48333%C2%A0added-code-to-check-for-session-timeout-to-resolve-the-issue-where-sessions-were-not-terminating-under-session-timeout-conditions)
  - [BUG-48337 Fixed an issue where the server would shut down when columns with different data types were used in a UNION ALL operation.](#bug-48337%C2%A0fixed-an-issue-where-the-server-would-shut-down-when-columns-with-different-data-types-were-used-in-a-union-all-operation)
  - [BUG-48355 Fixed an issue where V$RESERVED_WORDS was queried every time an AltibaseDatabaseMeta object was created.](#bug-48355%C2%A0fixed-an-issue-where-vreserved_words-was-queried-every-time-an-altibasedatabasemeta-object-was-created)
  - [BUG-48360 Fixed an issue where a protocol loss could occur due to abnormal communication buffer state when an exception occurs in Altibase.jdbc.driver.cm.CmChannel.sendPacket().](#bug-48360%C2%A0fixed-an-issue-where-a-protocol-loss-could-occur-due-to-abnormal-communication-buffer-state-when-an-exception-occurs-in-altibasejdbcdrivercmcmchannelsendpacket)
  - [BUG-48370 Fixed an issue where the server could shut down abnormally when executing a DB Link query in a session with TRCLOG_DETAIL_PREDICATE = 1 set, while accessing a remote table.](#bug-48370%C2%A0fixed-an-issue-where-the-server-could-shut-down-abnormally-when-executing-a-db-link-query-in-a-session-with-trclog_detail_predicate--1-set-while-accessing-a-remote-table)
  - [BUG-48390 Fixed an issue where the thread count for index build was set too low, resulting in poor build performance.](#bug-48390%C2%A0fixed-an-issue-where-the-thread-count-for-index-build-was-set-too-low-resulting-in-poor-build-performance)
  - [BUG-48393 Fixed an issue in Altibase 7.1.0.4.5 and later where the ST_Transform function could not be used on Linux.](#bug-48393%C2%A0fixed-an-issue-in-altibase-71045-and-later-where-the-st_transform-function-could-not-be-used-on-linux)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [Compatibility](#compatibility)
  - [Altibase Server Properties](#altibase-server-properties)
  - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
------------

### BUG-47821 iloader now supports the EWKB format.

-   **module** : ux-iloader

-   **Category** : Functionality

-   **Reproducibility** : Always

-   **Description** : iloader now supports the EWKB format.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

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

  - **Actual Results**

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

  -   **Expected Results**

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

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48323 Support for SRID in aexport

-   **module** : ux-aexport

-   **Category** : Functionality

-   **Reproducibility** : Always

-   **Description** : Support for SRID in aexport.

- **How to reproduce this bug**

  - **Reproduction conditions**

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

  - **Actual Results**

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

  -   **Expected Results**

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

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48348 Support for CSE(Common Subexpression Elimination)

-   **module** : qp-dml-pvo

-   **Category** : Enhancement

-   **Reproducibility** : Always

-   **Description** : Support for CSE(Common Subexpression Elimination)

- **How to reproduce this bug**

  - **Reproduction conditions**

  - **Actual Results**
  
  - **Expected Results**
  
-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48357 Added the -geom WKB option to the iloader out parameter.

-   **module** : ux-iloader

-   **Category** : Enhancement

-   **Reproducibility** : Always

-   **Description** : iloader out 인자에 -geom WKB 옵션을 추가합니다. Altibase 7.1.0.4.0 이상에서 제공하는 EWKB(Extended Well-KnownBinary) 형식의 공간 데이터를 WKB(Well-Known Binary) 형식으로 다운로드할 때 이 옵션을 사용합니다. 
    
- #### How to reproduce this bug

  -   **Reproduction conditions**

  -   **Actual Results**

  -   **Expected Results**
-   **Workaround**

-   **Changes**

    -   Performance view

    -   Property

    -   Compile Option

    -   Error Code

Fixed Bugs
----------

### BUG-47870 Fixed an issue where the replication would not be transmitted when deleting one of the two replication objects with the same disk table.

-   **module** : rp

-   **Category** : Testcase Error

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where the replication would not be transmitted when deleting one of the two replication objects with the same disk table.
    
-   **How to reproduce this bug**

    -   **Reproduction conditions**

    -   **Actual Results**

    -   **Expected Results**

-   **Workaround**

-   **Changes**

    -   Performance view

    -   Property

    -   Compile Option

    -   Error Code

### BUG-48090 Fixed an issue where a query with a WITH clause and a subquery resulted in an error when __OPTIMIZER_VIEW_TARGET_ENABLE was set to 1.

-   **module** : qp-select-pvo

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where a query with a WITH clause and a subquery resulted in an error when __OPTIMIZER_VIEW_TARGET_ENABLE was set to 1.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

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

  - **Actual Results**

    ```sql
    1) No rows selected.
    2) 1 row selected.
    3) No rows selected.
    4) 1 row selected.
    ```

  -   **Expected Results**

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

- **Changes**

  -   Performance view

  -   Property

  -   Compile Option

  -   Error Code

### BUG-48179 Fixed a deadlock error that occurred when performing a TRUNCATE on a replication target table in a triple or higher replication environment.

-   **module** : rp

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : In a replication environment with triple or higher replication, setting the DDL_LOCK_TIMEOUT property to a non-zero value and performing a TRUNCATE on a replication target table may result in a deadlock error. The issue causing deadlock in replication operations based on the DDL_LOCK_TIMEOUT setting has been fixed.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

  - **Actual Results**
  
  - **Expected Results**
  
- **Workaround**

      To avoid the deadlock error, you can apply one of the following two methods:
      1. Stop replication and perform TRUNCATE.
      2. Set ALTER SYSTEM SET DDL_LOCK_TIMEOUT = 0 and then perform TRUNCATE.

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48300 Fixed an issue in the optimizer where unnecessary resource usage during the processing of the `CONNECT BY` clause caused the error [ERR-3111D: There are too many DML statements in the stored procedure, or the SQL query is too long].

-   **module** : qp-dml-pvo

-   **Category** : Efficiency

-   **Reproducibility** : Always

-   **Description** : Fixed an issue in the optimizer where unnecessary resource usage during the processing of the `CONNECT BY` clause caused the error **[ERR-3111D: There are too many DML statements in the stored procedure, or the SQL query is too long]**.
    
-   **How to reproduce this bug**

    -   **Reproduction conditions**

    -   **Actual Results**

    -   **Expected Results**

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48333 Added code to check for session timeout to resolve the issue where sessions were not terminating under session timeout conditions.

-   **module** : sm-disk-index

-   **Category** : Hang

-   **Reproducibility** : Rare

-   **Description** : Added code to check for session timeout to resolve the issue where sessions were not terminating under session timeout conditions.
    
-   **How to reproduce this bug**

    -   **Reproduction conditions**

    -   **Actual Results**

    -   **Expected Results**

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48337 Fixed an issue where the server would shut down when columns with different data types were used in a UNION ALL operation.

-   **module** : qp-dml-execute

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where the server would shut down when columns with different data types were used in a UNION ALL operation.
    
-   **How to reproduce this bug**

    -   **Reproduction conditions**

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
    
-   **Actual Results**
    
        Server shut down
    
-   **Expected Results**
    
    ```sql
    COMPANY_CD                    LETCRDT_ESTBL_QT 
    --------------------------------------------------
    No rows selected.
    ```
    
- **Workaround**

  ```sql
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
  
-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48355 Fixed an issue where V$RESERVED_WORDS was queried every time an AltibaseDatabaseMeta object was created.

-   **module** : mm-jdbc

-   **Category** : Functionality

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where V$RESERVED_WORDS was queried every time an AltibaseDatabaseMeta object was created.
    
-   **How to reproduce this bug**

    -   **Reproduction conditions**

    -   **Actual Results**

    -   **Expected Results**

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48360 Fixed an issue where a protocol loss could occur due to abnormal communication buffer state when an exception occurs in Altibase.jdbc.driver.cm.CmChannel.sendPacket().

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where protocol loss occurred due to abnormal communication buffer state when an exception occurred in Altibase.jdbc.driver.cm.CmChannel.sendPacket(). This issue could cause abnormal data processing, potentially leading to an Altibase server shutdown.
    
    To apply this fix, update the JDBC driver to version 7.1.0.4.9 or higher.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

  -   **Actual Results**
  
  - **Expected Results**
  
-   **Workaround**

- **Changes**

  -   Performance view

  -   Property

  -   Compile Option

  -   Error Code

### BUG-48370 Fixed an issue where the server could shut down abnormally when executing a DB Link query in a session with TRCLOG_DETAIL_PREDICATE = 1 set, while accessing a remote table.

-   **module** : qp-dml-execute

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** :  Fixed an issue where the server could shut down abnormally when executing a DB Link query in a session with TRCLOG_DETAIL_PREDICATE = 1 set, while accessing a remote table. 
    
-   **How to reproduce this bug**

    -   **Reproduction conditions**

    -   **Actual Results**

    -   **Expected Results**

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48390 Fixed an issue where the thread count for index build was set too low, resulting in poor build performance.

-   **module** : id

-   **Category** : Maintainability

-   **Reproducibility** : Unknown

-   **Description** : Fixed an issue where the default value of the INDEX_BUILD_THREAD_COUNT property was set to 1 starting from version 7.1.0.4.5 due to an internal function returning the number of CPU cores. This caused the index build thread count to be too low, resulting in poor build performance. This patch resolves the issue.
    
-   **How to reproduce this bug**
    -   **Reproduction conditions**
    
    -   **Actual Results**
    
    -   **Expected Results**
    
-   **Workaround**

-   **Changes**
-   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48393 Fixed an issue in Altibase 7.1.0.4.5 and later where the ST_Transform function could not be used on Linux.

-   **module** : st-spatial

-   **Category** : Compile Error

-   **Reproducibility** : Always

-   **Description** : Fixed an issue in Altibase 7.1.0.4.5 and later where the ST_Transform function could not be used on Linux. ST_Transform function is now available for use on Linux.
    
-   **How to reproduce this bug**
-   **Reproduction conditions**
    
-   **Actual Results**
    
-   **Expected Results**
    
-   **Workaround**

-   **Changes**
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

> You can check the module version change history in [Version_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.1/Altibase_7_1_Version_Histories.md).

### Compatibility

#### Database binary version

The database binary version has not changed.

> The database binary version indicates the compatibility of database image files and log files. If this version needs to be patched to a different version, the database must be reorganized.

#### Meta Version

The meta version has not changed.

> If you want to roll back the patch after patching to a version with a changed meta version, see [Meta Downgrade](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/eng/Installation Guide.md#meta-downgrade).

#### CM protocol Version

The cm protocol version has not changed.

#### Replication protocol Version

The replication protocol version has not changed.

### Altibase Server Properties

#### Added properties

#### Changed properties

#### Deleted properties

### Performance Views

#### Added performance views

#### Changed performance views

#### Deleted performance views
