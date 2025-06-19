Altibase 7.1.0.5.0 Patch Notes
==============================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [New Features](#new-features)
  - [BUG-48336 Adds a feature to exclude conditions for subquery unnesting targets.](#bug-48336%C2%A0adds-a-feature-to-exclude-conditions-for-subquery-unnesting-targets)
  - [BUG-48358 Added aexport property ILOADER_GEOM_FORMAT.](#bug-48358%C2%A0added-aexport-property-iloader_geom_format)
- [Fixed Bugs](#fixed-bugs)
  - [BUG-48381 Fixed an issue where a subquery containing set operators would be transformed into DNF (Disjunctive Normal Form) during query transformation.](#bug-48381%C2%A0fixed-an-issue-where-a-subquery-containing-set-operators-would-be-transformed-into-dnf-disjunctive-normal-form-during-query-transformation)
  - [BUG-48405 Fixed an issue where the server would shut down when two or more LEFT OUTER JOIN were used along with other JOIN types, and the OPTIMIZER_ANSI_JOIN_ORDERING property was set to 1.](#bug-48405%C2%A0fixed-an-issue-where-the-server-would-shut-down-when-two-or-more-left-outer-join-were-used-along-with-other-join-types-and-the-optimizer_ansi_join_ordering-property-was-set-to-1)
  - [BUG-48419 Fixed an issue where the subquery unnesting optimization was being used when the View Merging optimization was applied, when it shouldn't be.](#bug-48419%C2%A0fixed-an-issue-where-the-subquery-unnesting-optimization-was-being-used-when-the-view-merging-optimization-was-applied-when-it-shouldnt-be)
  - [BUG-48429 Add debugging information to analyze the issue where sessions are not terminated under session timeout conditions](#bug-48429%C2%A0add-debugging-information-to-analyze-the-issue-where-sessions-are-not-terminated-under-session-timeout-conditions)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [Compatibility](#compatibility)
  - [Altibase Server Properties](#altibase-server-properties)
  - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
------------

### BUG-48336 Adds a feature to exclude conditions for subquery unnesting targets.

-   **module** : qp-dml-pvo

-   **Category** : Functionality

-   **Reproducibility** : Always

-   **Description** : A feature is added to exclude conditions from subquery unnesting targets, preventing unnesting in cases where the performance of subquery unnesting is slow.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    DROP TABLE T1;   
    CREATE TABLE T1 ( I1 INT, I2 INT, I3 INT, I4 INT) ;
    INSERT INTO T1 (SELECT LEVEL, LEVEL, MOD(LEVEL,10), LEVEL FROM DUAL CONNECT BY LEVEL <= 100000);
    ALTER SESSION SET EXPLAIN PLAN = ON;
    ALTER SYSTEM SET __OPTIMIZER_UNNEST_COMPATIBILITY = 0;
    SELECT COUNT(*)
     FROM T1 A LEFT OUTER JOIN T1 B ON A.I1 = B.I1
          LEFT OUTER JOIN T1 C ON B.I1 = C.I1 LEFT OUTER JOIN T1 D ON C.I1 = D.I1 LEFT OUTER JOIN T1 E ON D.I1 = E.I1
     WHERE A.I2 IN (SELECT /*+ NO_INVERSE_JOIN */ I2
                      FROM T1 F
                     WHERE I3 = 0);
    ```

  - **Actual Results**

    ```sql
    10000 rows selected.
    ------------------------------------------------------------
    PROJECT ( COLUMN_COUNT: 20, TUPLE_SIZE: 80, COST: 562517886347943.06 )
     SEMI-JOIN ( METHOD: HASH, COST: 559615345990377.81 )
      LEFT-OUTER-JOIN INVERSE ( METHOD: HASH, COST: 43964924059972.31 )
       SCAN ( TABLE: SYS.T1 E, FULL SCAN, ACCESS: 100000, COST: 116.76 )
       HASH ( ITEM_SIZE: 48, ITEM_COUNT: 100000, BUCKET_COUNT: 16384, ACCESS: 100000, COST: 43964924059972.31 )
        LEFT-OUTER-JOIN INVERSE ( METHOD: HASH, COST: 42930304986.08 )
         SCAN ( TABLE: SYS.T1 D, FULL SCAN, ACCESS: 100000, COST: 116.76 )
         HASH ( ITEM_SIZE: 40, ITEM_COUNT: 100000, BUCKET_COUNT: 16384, ACCESS: 100000, COST: 42930304986.08 )
    LEFT-OUTER-JOIN INVERSE ( METHOD: HASH, COST: 41920810.10 )
    SCAN ( TABLE: SYS.T1 C, FULL SCAN, ACCESS: 100000, COST: 116.76 )
    HASH ( ITEM_SIZE: 32, ITEM_COUNT: 100000, BUCKET_COUNT: 16384, ACCESS: 100000, COST: 41920810.10 )
    LEFT-OUTER-JOIN ( METHOD: HASH, COST: 41243.85 )
    SCAN ( TABLE: SYS.T1 A, FULL SCAN, ACCESS: 100000, COST: 116.76 )
    HASH ( ITEM_SIZE: 24, ITEM_COUNT: 100000, BUCKET_COUNT: 16384, ACCESS: 100000, COST: 41243.85 )
    SCAN ( TABLE: SYS.T1 B, FULL SCAN, ACCESS: 100000, COST: 116.76 )
      HASH ( ITEM_SIZE: 24, ITEM_COUNT: 10000, BUCKET_COUNT: 1024, ACCESS: 10000, COST: 559615345990377.81 )
       SCAN ( TABLE: SYS.T1 $$1_$$VIEW1_$F, FULL SCAN, ACCESS: 100000, COST: 120.72 )
    ------------------------------------------------------------
    ```

  -   **Expected Results**

      ```sql
      10000 rows selected.
      ------------------------------------------------------------
      PROJECT ( COLUMN_COUNT: 20, TUPLE_SIZE: 80, COST: 24330109213100.52 )
       LEFT-OUTER-JOIN INVERSE ( METHOD: HASH, COST: 14654974687883.07 )
        SCAN ( TABLE: SYS.T1 E, FULL SCAN, ACCESS: 100000, COST: 116.76 )
        HASH ( ITEM_SIZE: 48, ITEM_COUNT: 10000, BUCKET_COUNT: 1024, ACCESS: 10000, COST: 14654974687883.07 )
         LEFT-OUTER-JOIN INVERSE ( METHOD: HASH, COST: 14310102575.13 )
          SCAN ( TABLE: SYS.T1 D, FULL SCAN, ACCESS: 100000, COST: 116.76 )
          HASH ( ITEM_SIZE: 40, ITEM_COUNT: 10000, BUCKET_COUNT: 1024, ACCESS: 10000, COST: 14310102575.13 )
           LEFT-OUTER-JOIN INVERSE ( METHOD: HASH, COST: 13974203.94 )
      SCAN ( TABLE: SYS.T1 C, FULL SCAN, ACCESS: 100000, COST: 116.76 )
      HASH ( ITEM_SIZE: 32, ITEM_COUNT: 10000, BUCKET_COUNT: 1024, ACCESS: 10000, COST: 13974203.94 )
      LEFT-OUTER-JOIN ( METHOD: HASH, COST: 14035.99 )
      SCAN ( TABLE: SYS.T1 A, FULL SCAN, ACCESS: 100000, COST: 242.89 )
      ::SUB-QUERY BEGIN
      PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: 120.85 )
      HASH ( ITEM_SIZE: 24, ITEM_COUNT: 10000, BUCKET_COUNT: 16384, ACCESS: 10000, COST: 0.00 )
      VIEW ( ACCESS: 10000, COST: 0.00 )
      PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: 120.85 )
      SCAN ( TABLE: SYS.T1 F, FULL SCAN, ACCESS: 100000, COST: 120.72 )
      ::SUB-QUERY END
      HASH ( ITEM_SIZE: 24, ITEM_COUNT: 100000, BUCKET_COUNT: 16384, ACCESS: 10000, COST: 14035.99 )
      SCAN ( TABLE: SYS.T1 B, FULL SCAN, ACCESS: 100000, COST: 116.76 )
      ------------------------------------------------------------
      ```

- **Workaround**

  ```sql
  -- Use "NO_UNNEST" hint 
  SELECT COUNT(*)
   FROM T1 A LEFT OUTER JOIN T1 B ON A.I1 = B.I1
        LEFT OUTER JOIN T1 C ON B.I1 = C.I1 LEFT OUTER JOIN T1 D ON C.I1 = D.I1 LEFT OUTER JOIN T1 E ON D.I1 = E.I1
   WHERE A.I2 IN (SELECT /*+ NO_INVERSE_JOIN NO_UNNEST */ I2
                    FROM T1 F
                   WHERE I3 = 0);
  ```
  
- **Changes**

  - Performance view

  - Property

  - Compile Option

  -   Error Code

### BUG-48358 Added aexport property ILOADER_GEOM_FORMAT.

-   **module** : ux-aexport

-   **Category** : Enhancement

-   **Reproducibility** : Always

- **Description** : When the ILOADER_GEOM_FORMAT = WKB option is used in the aexport.properties file, the run_il_out.sh file will store the iloader command with the -geom WKB option.

  This is used when spatial data is input in the EWKT (Extended Well-Known Text) format in Altibase 7.1.0.4.0 or later.

  ```sql
  CREATE TABLE TB3(ID INTEGER PRIMARY KEY, OBJ GEOMETRY);
      
  // The data with IDs 121 and 123 are input in the WKT format, while the data with IDs 122 and 124 are input in the EWKT format.
  INSERT INTO TB3 VALUES (121, ST_POLYGONFROMTEXT('POLYGON((10 10, 10 20, 20 20, 20 15, 10 10))'));
  INSERT INTO TB3 VALUES (122, ST_POLYGONFROMTEXT('POLYGON((10 10, 10 20, 20 20, 20 15, 10 10))', 100));
  INSERT INTO TB3 VALUES (123, ST_POLYGONFROMTEXT('MULTILINESTRING((10 10, 20 20), (15 15, 30 15))'));
  INSERT INTO TB3 VALUES (124, ST_POLYGONFROMTEXT('SRID=100;POLYGON((10 10, 10 20, 20 20, 20 15, 10 10))'));
  ```
  
- **How to reproduce this bug**
  - **Reproduction conditions**
  - **Actual Results**
  - **Expected Results**

-   **Workaround**

- **Changes**

  -   Performance view

  -   Property
      -   New
          -   ILOADER_GEOM_FORMAT
              -   Description : This property is used to export spatial data in the Well-Known Binary (WKB) format. When setting `ILOADER_GEOM = WKB` and performing `aexport`, you can verify that the generated `run_il_out.sh` file includes the `-geom WKB` option.
      
  -   Compile Option
  
  -   Error Code

Fixed Bugs
----------

### BUG-48381 Fixed an issue where a subquery containing set operators would be transformed into DNF (Disjunctive Normal Form) during query transformation.

-   **module** : qp-select-pvo

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where a subquery containing set operators would be transformed into DNF (Disjunctive Normal Form) during query transformation, causing the error:
    
    ERR-31455: Failed to work because an internal exception occurred from an OS. [Contact Altibase's Support Center]
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    DROP TABLE t1;
    DROP TABLE t2;
    CREATE TABLE t1 (i1 INT, i2 INT, i3 INT, i4 INT);
    CREATE TABLE t2 (i1 INT, i2 INT, i3 INT);
    
    ALTER TABLE t1 ADD PRIMARY KEY (i1, i2, i3);
    
    SELECT *
      FROM t1
     WHERE i1 = :A
       AND i2 = (SELECT i2 FROM t1 WHERE i1 = 1
                  UNION ALL
                 SELECT i2 FROM t2 WHERE i1 < 0)
       AND i3 IN (1,2,3,4,5,6,7,8,9,10);
    ```

  - **Actual Results**

    ```sql
    [ERR-31455 : Failed to work because an internal exception occurred from an OS.[Contact Altibase's Support Center]]
    ```

  -   **Expected Results**

          no error

- **Workaround**

      use /*+ full scan(t1) */ hint
      or
      set the property "__OPTIMIZER_ELIMINATE_COMMON_SUBEXPRESSION" to 0. 

- **Changes**

  -   Performance view

  -   Property

  -   Compile Option

  -   Error Code

### BUG-48405 Fixed an issue where the server would shut down when two or more LEFT OUTER JOIN were used along with other JOIN types, and the OPTIMIZER_ANSI_JOIN_ORDERING property was set to 1.

-   **module** : qp-select-pvo

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where the server would shut down when two or more LEFT OUTER JOIN were used along with other JOIN types, and the OPTIMIZER_ANSI_JOIN_ORDERING property was set to 1.

- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    DROP TABLE t1;
    CREATE TABLE t1 (i1 INT, i2 INT, i3 INT);
    
    INSERT INTO t1 VALUES (1, 1, 1);
    
    ALTER SYSTEM SET OPTIMIZER_ANSI_JOIN_ORDERING = 1;
    
    SELECT /*+ USE_HASH(D C) */ *
      FROM t1 a LEFT OUTER JOIN t1 b ON a.i1 = b.i1 INNER JOIN t1 c ON a.i1 = c.i1     LEFT OUTER JOIN t1 d ON d.i1 = a.i1
       AND d.i2 <= c.i2
       AND d.i3 >= c.i3;
    ```

  -   **Actual Results**

          Server shut down.

  -   **Expected Results**

      ```sql
      I1          I2          I3          I1          I2          I3          I1          I2          I3          I1          I2          I3          
      -------------------------------------------------------------------------------------------------------------------------------------------------------------
      1           1           1           1           1           1           1           1           1           1           1           1           
      1 row selected.
      ```

- **Workaround**

  ```sql
  SELECT /*+ USE_HASH(C D) */ *
    FROM t1 a LEFT OUTER JOIN t1 b ON a.i1 = b.i1 INNER JOIN t1 c ON a.i1 = c.i1     LEFT OUTER JOIN t1 d ON d.i1 = a.i1
     AND d.i2 <= c.i2
     AND d.i3 >= c.i3;
  ```

- **Changes**

  -   Performance view

  -   Property

  -   Compile Option

  -   Error Code

### BUG-48419 Fixed an issue where the subquery unnesting optimization was being used when the View Merging optimization was applied, when it shouldn't be.

-   **module** : qp-select-pvo

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where the subquery unnesting optimization was being used when the View Merging optimization was applied, when it shouldn't be. 

- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    CREATE TABLE T1 (I1 INT, I2 INT, I3 INT);
    CREATE TABLE T2 (I1 INT, I2 INT, I3 INT);
    
    ALTER SYSTEM SET __OPTIMIZER_UNNEST_COMPATIBILITY = 0;
    ALTER SESSION SET EXPLAIN PLAN = ONLY;
    
    WITH TMP_HDD
    AS
    (SELECT *
       FROM T1 A LEFT OUTER JOIN T1 B ON A.I2 = B.I2
      WHERE A.I1 IN (SELECT I1 FROM T2) )
    SELECT /*+ NO_PLAN_CACHE */ *
    FROM TMP_HDD ;
    ```

  - **Actual Results**

    ```sql
    ------------------------------------------------------------
    PROJECT ( COLUMN_COUNT: 6, TUPLE_SIZE: 24, COST: BLOCKED )
     SEMI-JOIN INVERSE ( METHOD: HASH, COST: BLOCKED )
      SCAN ( TABLE: SYS.T2 $$1_$$VIEW1_$T2, FULL SCAN, ACCESS: 0, COST: BLOCKED )
      HASH ( ITEM_SIZE: BLOCKED, ITEM_COUNT: 0, BUCKET_COUNT: 5243392, ACCESS: 0, COST: BLOCKED )
       LEFT-OUTER-JOIN ( METHOD: HASH, COST: BLOCKED )
        SCAN ( TABLE: SYS.T1 A, FULL SCAN, ACCESS: 0, COST: BLOCKED )
        HASH ( ITEM_SIZE: 0, ITEM_COUNT: 0, BUCKET_COUNT: 5120, ACCESS: 0, COST: BLOCKED )
         SCAN ( TABLE: SYS.T1 B, FULL SCAN, ACCESS: 0, COST: BLOCKED )
    ------------------------------------------------------------
    ```

  -   **Expected Results**

      ```sql
      ------------------------------------------------------------
      PROJECT ( COLUMN_COUNT: 6, TUPLE_SIZE: 24, COST: BLOCKED )
       VIEW ( TMP_HDD, ACCESS: 0, COST: BLOCKED )
        PROJECT ( COLUMN_COUNT: 6, TUPLE_SIZE: 24, COST: BLOCKED )
         LEFT-OUTER-JOIN ( METHOD: HASH, COST: BLOCKED )
          SCAN ( TABLE: SYS.T1 A, FULL SCAN, ACCESS: 0, COST: BLOCKED )
           ::SUB-QUERY BEGIN
           PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: BLOCKED )
            HASH ( ITEM_SIZE: 0, ITEM_COUNT: 0, BUCKET_COUNT: 1024, ACCESS: 0, COST: BLOCKED )
             VIEW ( ACCESS: 0, COST: BLOCKED )
              PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: BLOCKED )
               SCAN ( TABLE: SYS.T2, FULL SCAN, ACCESS: 0, COST: BLOCKED )
           ::SUB-QUERY END
          HASH ( ITEM_SIZE: 0, ITEM_COUNT: 0, BUCKET_COUNT: 5120, ACCESS: 0, COST: BLOCKED )
           SCAN ( TABLE: SYS.T1 B, FULL SCAN, ACCESS: 0, COST: BLOCKED )
      ------------------------------------------------------------
      ```

- **Workaround**

  ```sql
  WITH TMP_HDD
  AS
  (SELECT /*+ NO_MERGE */ *
     FROM T1 A LEFT OUTER JOIN T1 B ON A.I2 = B.I2
    WHERE A.I1 IN (SELECT I1 FROM T2) )
  SELECT /*+ NO_PLAN_CACHE */ *
  FROM TMP_HDD ;
  ```
  
-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48429 Add debugging information to analyze the issue where sessions are not terminated under session timeout conditions

-   **module** : sm-disk-index

-   **Category** : Hang

-   **Reproducibility** : Rare

-   **Description** : Add debugging information to analyze the issue where sessions are not terminated under session timeout conditions
    
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
| 7.1.0.5.0        | 6.5.1                   | 8.9.1        | 7.1.7               | 7.4.6                        |

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
