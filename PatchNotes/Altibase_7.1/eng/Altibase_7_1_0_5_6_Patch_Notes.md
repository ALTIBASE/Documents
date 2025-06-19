<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Altibase 7.1.0.5.6 Patch Notes](#altibase-71056-patch-notes)
  - [New Features](#new-features)
    - [BUG-48888 Added JDBC driver (Altibase42.jar) that supports JDBC API Specification 4.2.](#bug-48888-added-jdbc-driver-altibase42jar-that-supports-jdbc-api-specification-42)
    - [BUG-48905 Improved query performance when using the analytical function ROW_NUMBER as the same meaning as LIMIT k.](#bug-48905-improved-query-performance-when-using-the-analytical-function-row_number-as-the-same-meaning-as-limit-k)
    - [BUG-48944 Optimize how nested LEFT OUTER JOINs are performed.](#bug-48944-optimize-how-nested-left-outer-joins-are-performed)
    - [BUG-48971 Improves the phenomenon where the possibility of FULL SCAN increases due to incorrect NDV (Number of Distinct Value) setting when collecting statistics for a table with no records.](#bug-48971-improves-the-phenomenon-where-the-possibility-of-full-scan-increases-due-to-incorrect-ndv-number-of-distinct-value-setting-when-collecting-statistics-for-a-table-with-no-records)
    - [BUG-48995 Offline Option meta replication feature has been added to Adapter for Oracle and Adapter for JDBC.](#bug-48995-offline-option-meta-replication-feature-has-been-added-to-adapter-for-oracle-and-adapter-for-jdbc)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-48902 When using the CONVERT function, if source_char_set exceeds dest_char_set, the Altibase server terminates abnormally.](#bug-48902-when-using-the-convert-function-if-source_char_set-exceeds-dest_char_set-the-altibase-server-terminates-abnormally)
    - [BUG-48920 Altibase server may terminate abnormally when index structure changes occur to utilize index node space during disk index key insertion process.](#bug-48920-altibase-server-may-terminate-abnormally-when-index-structure-changes-occur-to-utilize-index-node-space-during-disk-index-key-insertion-process)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [Compatibility](#compatibility)
    - [Altibase Server Properties](#altibase-server-properties)
    - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->



Altibase 7.1.0.5.6 Patch Notes
==============================

New Features
----------

### BUG-48888 Added JDBC driver (Altibase42.jar) that supports JDBC API Specification 4.2.

- **module** : mm-jdbc

- **Category** : Enhancement

- **Reproducibility** : Always

- **Description** : Added Altibase JDBC driver (Altibase42.jar) that supports JDBC API Specification 4.2. JRE 1.8 or higher is required to use Altibase42.jar.

  For more detailed information, see the JDBC User's Manual.

  - [JDBC User’s Manual - 6.JDBC 4.2 API References](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/eng/JDBC%20User's%20Manual.md#6-jdbc-42-api-references)

- **How to reproduce this bug**

  - **Reproduction conditions**
  - **Actual Results**
  - **Expected Results**

- **Workaround**

- **Changes**

  - Performance view
  - Property
  - Compile Option
  - Error Code

### BUG-48905 Improved query performance when using the analytical function ROW_NUMBER as the same meaning as LIMIT k.

- **module** : qp-dml-execute

- **Category** : Enhancement

- **Reproducibility** : Always

- **Description** : Improved query performance when using the analytic function ROW_NUMBER with the same meaning as LIMIT k. Query performance was improved when a bind variable was used in the last value condition of LIMIT.

- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    var a integer
    var b integer
    exec :a := 5;
    exec :b := 0;
    DROP TABLE T1;
    CREATE TABLE T1 ( I1 INT PRIMARY KEY, I2 INT, I3 INT);
    INSERT INTO T1 ( SELECT LEVEL, 100-LEVEL, MOD(LEVEL, 2) FROM DUAL CONNECT BY LEVEL <= 2000000);
    
    SET LINESIZE 1024
    SET COLSIZE 10
    SET TIMING ON
    ALTER SESSION SET EXPLAIN PLAN = ON;
    ALTER SESSION SET TRCLOG_DETAIL_PREDICATE = 1;
    PREPARE SELECT I1, I2, I3
     FROM ( SELECT T1.*
                ,  ROW_NUMBER() OVER (ORDER BY I2, I3) AS RN
            FROM T1)
     WHERE RN < :A  AND RN > :B;
    ```

  - **Actual Results**

    ```sql
    I1          I2          I3          
    ----------------------------------------
    2000000     -1999900    0           
    1999999     -1999899    1           
    1999998     -1999898    0           
    1999997     -1999897    1           
    4 rows selected.
    ------------------------------------------------------------
    PROJECT ( COLUMN_COUNT: 3, TUPLE_SIZE: 12, COST: 280.00 )
     FILTER
      [ FILTER ]
      AND
       RN > :B
       RN < :A
      VIEW ( ACCESS: 2000000, COST: 279.56 )
       PROJECT ( COLUMN_COUNT: 4, TUPLE_SIZE: 24, COST: 152.24 )
        WINDOW SORT ( ITEM_SIZE: 24, ITEM_COUNT: 2000000, ACCESS: 5999999, SORT_COUNT: 1, COST: 146.97 )
         [ ANALYTIC FUNCTION INFO ]
         SORT_KEY[0]: (I2,I3)
          ROW_NUMBER() OVER (ORDER BY I2, I3)
         SCAN ( TABLE: SYS.T1, FULL SCAN, ACCESS: 2000000, COST: 116.76 )
    ------------------------------------------------------------
    elapsed time : 1.54
    ```

  - **Expected Results**

    ```sql
    I1          I2          I3          
    ----------------------------------------
    2000000     -1999900    0           
    1999999     -1999899    1           
    1999998     -1999898    0           
    1999997     -1999897    1           
    4 rows selected.
    ------------------------------------------------------------
    PROJECT ( COLUMN_COUNT: 3, TUPLE_SIZE: 12, COST: 283.52 )
     FILTER
      [ FILTER ]
      AND
       RN > :B
       RN < :A
      VIEW ( ACCESS: 5, COST: 282.20 )
       PROJECT ( COLUMN_COUNT: 4, TUPLE_SIZE: 24, COST: 154.88 )
        WINDOW SORT ( ITEM_SIZE: 24, ITEM_COUNT: 5, ACCESS: 14, SORT_COUNT: 1, COST: 146.97 )
         [ ANALYTIC FUNCTION INFO ]
         SORT_KEY[0]: (I2,I3)
          ROW_NUMBER_LIMIT(:A) OVER (ORDER BY I2, I3)
         SCAN ( TABLE: SYS.T1, FULL SCAN, ACCESS: 2000000, COST: 116.76 )
    ------------------------------------------------------------
    elapsed time : 0.39
    ```

- **Workaround**

  ```sql
  PREPARE SELECT I1, I2, I3
   FROM ( SELECT T1.*
              ,  ROW_NUMBER() OVER (ORDER BY I2, I3) AS RN
          FROM T1)
   WHERE RN < 5  AND RN > :B;
  ```

- **Changes**

  - Performance view
  - Property
  - Compile Option
  - Error Code

### BUG-48944 Optimize how nested LEFT OUTER JOINs are performed.

- **module** : qp-dml-execute

- **Category** : Efficiency

- **Reproducibility** : Always

- **Description** : Eliminates unnecessary table reads in nested LEFT OUTER JOINs. 

  To use the optimizations made in this bug, you need to set __LEFT_OUTER_SKIP_RIGHT_ENABLE = 1.

- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    DROP TABLE A;
    DROP TABLE B;
    DROP TABLE C;
    DROP TABLE D;
    CREATE TABLE A(i1 INTEGER, i2 INTEGER);
    CREATE TABLE B(i1 INTEGER, i2 INTEGER);
    CREATE TABLE C(i1 INTEGER, i2 INTEGER);
    CREATE TABLE D(i1 INTEGER, i2 INTEGER);
    INSERT INTO A SELECT LEVEL, LEVEL FROM DUAL CONNECT BY LEVEL <= 100;
    INSERT INTO B SELECT LEVEL, LEVEL FROM DUAL CONNECT BY LEVEL <= 100;
    INSERT INTO C SELECT LEVEL, LEVEL FROM DUAL CONNECT BY LEVEL <= 100;
    INSERT INTO D SELECT LEVEL, LEVEL FROM DUAL CONNECT BY LEVEL <= 100;
    ALTER TABLE A ADD CONSTRAINT IX_A_PK PRIMARY KEY( i1 );
    ALTER TABLE B ADD CONSTRAINT IX_B_PK PRIMARY KEY( i1 );
    ALTER TABLE C ADD CONSTRAINT IX_C_PK PRIMARY KEY( i1 );
    ALTER TABLE D ADD CONSTRAINT IX_D_PK PRIMARY KEY( i1 );
    
    set colsize 20;
    set linesize 200;
    ALTER SESSION SET EXPLAIN PLAN = ON;
    ALTER SESSION SET TRCLOG_DETAIL_INFORMATION = 1;
    SELECT /*+ USE_NL(A B C D) */
           SUM(1)
         , SUM(NVL2(A.i2,1,0))
         , SUM(NVL2(B.i2,1,0))
         , SUM(NVL2(C.i2,1,0))
         , SUM(NVL2(D.i2,1,0))
      FROM A
           LEFT OUTER JOIN B ON B.i1 = A.i1 AND B.i2 = -1
           LEFT OUTER JOIN C ON C.i1 = B.i1
           LEFT OUTER JOIN D ON D.i1 = C.i1
      WHERE 1=1 AND A.i1 BETWEEN 10 AND 20;
    ```

  - **Actual Results**

    ```sql
    ------------------------------------------------------------
    PROJECT ( COLUMN_COUNT: 5, TUPLE_SIZE: 40, COST: 672716084.89 )
     GROUP-AGGREGATION ( ITEM_SIZE: 96, GROUP_COUNT: 1, BUCKET_COUNT: 1, ACCESS: 1, COST: 672716084.89 )
      LEFT-OUTER-JOIN ( METHOD: INDEX_NL, COST: 9558146.46 )
       LEFT-OUTER-JOIN ( METHOD: INDEX_NL, COST: 9459.99 )
        LEFT-OUTER-JOIN ( METHOD: INDEX_NL, COST: 136.01 )
         SCAN ( TABLE: SYS.A, INDEX: SYS.IX_A_PK, RANGE SCAN, ACCESS: 11, COST: 0.01 )
          [ FIXED KEY ]
          AND
           OR
            A.I1 BETWEEN 10 AND 20
         SCAN ( TABLE: SYS.B, INDEX: SYS.IX_B_PK, RANGE SCAN, ACCESS: 22, COST: 120.72 )
          [ VARIABLE KEY ]
          OR
           AND
            B.I1 = A.I1
          [ FILTER ]
          B.I2 = -1
        SCAN ( TABLE: SYS.C, INDEX: SYS.IX_C_PK, RANGE SCAN, ACCESS: 11, COST: 116.76 )
         [ VARIABLE KEY ]
         OR
          AND
           C.I1 = B.I1
       SCAN ( TABLE: SYS.D, INDEX: SYS.IX_D_PK, RANGE SCAN, ACCESS: 11, COST: 116.76 )
        [ VARIABLE KEY ]
        OR
         AND
          D.I1 = C.I1
    ------------------------------------------------------------
    ```

  - **Expected Results**

    ```sql
    ------------------------------------------------------------
    PROJECT ( COLUMN_COUNT: 5, TUPLE_SIZE: 40, COST: 672716084.89 )
     GROUP-AGGREGATION ( ITEM_SIZE: 96, GROUP_COUNT: 1, BUCKET_COUNT: 1, ACCESS: 1, COST: 672716084.89 )
      LEFT-OUTER-JOIN ( METHOD: INDEX_NL, SKIP RIGHT COUNT: 11, COST: 9558146.46 )
       LEFT-OUTER-JOIN ( METHOD: INDEX_NL, SKIP RIGHT COUNT: 11, COST: 9459.99 )
        LEFT-OUTER-JOIN ( METHOD: INDEX_NL, COST: 136.01 )
         SCAN ( TABLE: SYS.A, INDEX: SYS.IX_A_PK, RANGE SCAN, ACCESS: 11, COST: 0.01 )
          [ FIXED KEY ]
          AND
           OR
            A.I1 BETWEEN 10 AND 20
         SCAN ( TABLE: SYS.B, INDEX: SYS.IX_B_PK, RANGE SCAN, ACCESS: 22, COST: 120.72 )
          [ VARIABLE KEY ]
          OR
           AND
            B.I1 = A.I1
          [ FILTER ]
          B.I2 = -1
        SCAN ( TABLE: SYS.C, INDEX: SYS.IX_C_PK, RANGE SCAN, ACCESS: 11, COST: 116.76 )
         [ VARIABLE KEY ]
         OR
          AND
           C.I1 = B.I1
       SCAN ( TABLE: SYS.D, INDEX: SYS.IX_D_PK, RANGE SCAN, ACCESS: 11, COST: 116.76 )
        [ VARIABLE KEY ]
        OR
         AND
          D.I1 = C.I1
    ------------------------------------------------------------
    ```

- **Workaround**

- **Changes**

  - Performance view
  - Property
  - Compile Option
  - Error Code

### BUG-48971 Improves the phenomenon where the possibility of FULL SCAN increases due to incorrect NDV (Number of Distinct Value) setting when collecting statistics for a table with no records.

- **module** : qp-select-pvo
- **Category** : Functional Error
- **Reproducibility** : Frequence
- **Description** : Improves the phenomenon where NDV (Number of Distinct Value) is calculated incorrectly when collecting statistics for a table with no records. If NDV is calculated incorrectly, selecting FULL SCAN over INDEX SCAN may affect query performance.
- **How to reproduce this bug**
  - **Reproduction conditions**
  - **Actual Results**
  - **Expected Results**
- **Workaround**
- **Changes**
  - Performance view
  - Property
  - Compile Option
  - Error Code

### BUG-48995 Offline Option meta replication feature has been added to Adapter for Oracle and Adapter for JDBC.

- **module** : dm

- **Category** : Other

- **Reproducibility** : Always

- **Description** : When an Altibase server failure occurs while running Adapter for Oracle or Adapter for JDBC, you can synchronize data that could not be synchronized using the Offline Option function.

  To use this feature, the following conditions must be met:

  - Use the META_LOGGING option when creating a duplication object
  - Configuring Altibase duplication environment with Active-Standby

- **How to reproduce this bug**

  - **Reproduction conditions**
  - **Actual Results**
  - **Expected Results**

- **Workaround**

- **Changes**

  - Performance view
  - Property
  - Compile Option
  - Error Code

Fixed Bugs
----------

### BUG-48902 When using the CONVERT function, if source_char_set exceeds dest_char_set, the Altibase server terminates abnormally.

- **module** : qp

- **Category** : Fatal

- **Reproducibility** : Always

- **Description** : Fixes the phenomenon in which the Altibase server terminates abnormally due to lack of exception handling when the source_char_set exceeds the dest_char_set when using the CONVERT function.

- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    DROP TABLE BUG_48902;         
    CREATE TABLE BUG_48902(I1 DECIMAL);
    INSERT INTO BUG_48902 VALUES ( -3 );
    SELECT CONVERT(I1, 'UTF8', 'UTF8' ) FROM BUG_48902;
    ```

  - **Actual Results**

    ```
    ERR-91015 : Communication failure.
    ```

  - **Expected Results**

    ```
    ERR-2101D : Invalid data length
    ```

- **Workaround**

- **Changes**

  - Performance view
  - Property
  - Compile Option
  - Error Code

### BUG-48920 Altibase server may terminate abnormally when index structure changes occur to utilize index node space during disk index key insertion process.

- **module** : sm
- **Category** : Assert
- **Reproducibility** : Rare
- **Description** : Fixes the phenomenon in which the Altibase server terminates abnormally when the index structure is changed to utilize index node space during the disk index key insertion process.
- **How to reproduce this bug**
  - **Reproduction conditions**
  - **Actual Results**
  - **Expected Results**
- **Workaround**
- **Changes**
  - Performance view
  - Property
  - Compile Option
  - Error Code

## Changes

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 7.1.0.5.6        | 6.5.1                   | 8.9.1        | 7.1.7               | 7.4.6                        |

> You can check the module version change history in [Version_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.1/Altibase_7_1_Version_Histories.md).

### Compatibility

#### Database binary version

The database binary version has not changed.

> The database binary version indicates the compatibility of database image files and log files. If this version needs to be patched to a different version, the database must be reorganized.

#### Meta Version

The meta version has not changed.

> If you want to roll back the patch after patching to a version with a changed meta version, see [Meta Downgrade](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/eng/Installation%20Guide.md#meta-downgrade).

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
