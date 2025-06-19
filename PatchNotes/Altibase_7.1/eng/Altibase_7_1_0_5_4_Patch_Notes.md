<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Altibase 7.1.0.5.4 Patch Notes](#altibase-71054-patch-notes)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-48746 Fixed an issue where the Altibase server shut down abnormally when executing `ALTER REPLICATION ~ SYNC`, with the error `ERR-11089(errno=62) Invalid column size` being logged in `altibase_rp_conflict.log`.](#bug-48746%C2%A0fixed-an-issue-where-the-altibase-server-shut-down-abnormally-when-executing-alter-replication--sync-with-the-error-err-11089errno62-invalid-column-size-being-logged-in-altibase_rp_conflictlog)
    - [BUG-48761 Fixed an issue that caused the Altibase server to abnormally shut down if the online logfile open() failed.](#bug-48761%C2%A0fixed-an-issue-that-caused-the-altibase-server-to-abnormally-shut-down-if-the-online-logfile-open-failed)
    - [BUG-48792 Fixed a result error when the SELECT DISTINCT and GROUP BY CUBE clauses were used in a view.](#bug-48792%C2%A0fixed-a-result-error-when-the-select-distinct-and-group-by-cube-clauses-were-used-in-a-view)
    - [BUG-48800 Fixed an issue where a SELECT statement that specified a partition in the FORM clause and used a condition in the WHERE clause that was not a range of partition keys resulted in a result error.](#bug-48800%C2%A0fixed-an-issue-where-a-select-statement-that-specified-a-partition-in-the-form-clause-and-used-a-condition-in-the-where-clause-that-was-not-a-range-of-partition-keys-resulted-in-a-result-error)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [Compatibility](#compatibility)
    - [Altibase Server Properties](#altibase-server-properties)
    - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->



Altibase 7.1.0.5.4 Patch Notes
==============================

Fixed Bugs
----------

### BUG-48746 Fixed an issue where the Altibase server shut down abnormally when executing `ALTER REPLICATION ~ SYNC`, with the error `ERR-11089(errno=62) Invalid column size` being logged in `altibase_rp_conflict.log`.

-   **module** : sm

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where the Altibase server shut down abnormally when executing `ALTER REPLICATION ~ SYNC`, with the error `ERR-11089(errno=62) Invalid column size` being logged in `altibase_rp_conflict.log`.

- **How to reproduce this bug**

  - **Reproduction conditions**

  - **Actual Results**
  
  - **Expected Results**
  
    
  
- **Workaround**

  ```
  Change VARIABLE column to FIXED
  ```

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48761 Fixed an issue that caused the Altibase server to abnormally shut down if the online logfile open() failed.

-   **module** : sm

-   **Category** : Fatal

-   **Reproducibility** : Rare

-   **Description** : Fixed an issue that caused the server to unexpectedly shut down when trying to open() an online log file and failing due to insufficient filesystem capacity or a limit on the number of files to open.
    
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

### BUG-48792 Fixed a result error when the SELECT DISTINCT and GROUP BY CUBE clauses were used in a view.

-   **module** : qp-dml-execute

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed a result error when the SELECT DISTINCT and GROUP BY CUBE clauses were used in a view.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    DROP TABLE T1;
    CREATE TABLE T1( I1 INTEGER, I2 INTEGER, I3 INTEGER, I4 INTEGER );
    INSERT INTO T1 VALUES (1,1,1,1);
    INSERT INTO T1 VALUES (1,1,1,2);
    INSERT INTO T1 VALUES (1,1,2,3);
    INSERT INTO T1 VALUES (1,2,2,4);
    INSERT INTO T1 VALUES (2,2,3,5);
    INSERT INTO T1 VALUES (2,2,3,6);
    INSERT INTO T1 VALUES (2,3,4,7);
    INSERT INTO T1 VALUES (2,3,4,8);
    INSERT INTO T1 VALUES (3,1,1,1);
    INSERT INTO T1 VALUES (3,1,1,2);
    SELECT * FROM ( SELECT /*+*/ DISTINCT I1, COUNT( I2) FROM T1 GROUP BY CUBE(I1) ) ;
    ```

  - **Actual Results**

    ```sql
    I1          COUNT( I2)
    ------------------------------------
    3           10
    3           4
    3           4
    3           2
    4 rows selected.
    ```

  -   **Expected Results**

      ```sql
      I1          COUNT( I2)
      ------------------------------------            
                  10
      1           4
      2           4
      3           24
      rows selected.
      ```

- **Workaround**

  ```sql
  use "GROUP BY GROUPING SETS" clause
  ```

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48800 Fixed an issue where a SELECT statement that specified a partition in the FORM clause and used a condition in the WHERE clause that was not a range of partition keys resulted in a result error.

-   **module** : qp-dml-pvo

-   **Category** : Functional Error

-   **Reproducibility** : Frequence

-   **Description** : FORM 절에 파티션을 지정하고 WHERE 절에서 파티션 키 범위가 아닌 조건을 사용한 SELECT 문에서 결과 오류가 발생할 수 있습니다.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    DROP TABLE T1;
    CREATE TABLE T1 (I1 INT, I2 INT)
         PARTITION BY RANGE(I1)
         (
             PARTITION P1 VALUES LESS THAN (100),
             PARTITION P2 VALUES LESS THAN (200),
             PARTITION P3 VALUES DEFAULT
         );
    INSERT INTO T1 VALUES ( 130, 100 );
    SELECT /*+ NO_EXEC_FAST */ * FROM T1 PARTITION(P1) WHERE I1 = 130;
    ALTER TABLE T1 MERGE PARTITIONS P1, P2 INTO PARTITION P1;
    SELECT /*+ NO_EXEC_FAST */ * FROM T1 PARTITION(P1) WHERE I1 = 130;
    ```

  - **Actual Results**

    ```sql
    T1.I1       T1.I2
    ---------------------------
    No rows selected.
    ------------------------------------------------------------
    PROJECT ( COLUMN_COUNT: 2, TUPLE_SIZE: 8, COST: BLOCKED )
     PARTITION-COORDINATOR ( TABLE: SYS.T1, PARTITION: 0/3, FULL SCAN, ACCESS: 0, COST: BLOCKED )
    ------------------------------------------------------------
    
    T1.I1       T1.I2
    ---------------------------
    No rows selected.
    ------------------------------------------------------------
    PROJECT ( COLUMN_COUNT: 2, TUPLE_SIZE: 8, COST: BLOCKED )
     PARTITION-COORDINATOR ( TABLE: SYS.T1, PARTITION: 0/3, FULL SCAN, ACCESS: 0, COST: BLOCKED )
    ------------------------------------------------------------
    ```
    
  -   **Expected Results**

      ```sql
      T1.I1       T1.I2
      ---------------------------
      No rows selected.
      ------------------------------------------------------------
      PROJECT ( COLUMN_COUNT: 2, TUPLE_SIZE: 8, COST: BLOCKED )
       PARTITION-COORDINATOR ( TABLE: SYS.T1, PARTITION: 0/3, FULL SCAN, ACCESS: 0, COST: BLOCKED )
      ------------------------------------------------------------
      
      T1.I1       T1.I2
      ---------------------------
      130         100
      1 row selected.
      ------------------------------------------------------------
      PROJECT ( COLUMN_COUNT: 2, TUPLE_SIZE: 8, COST: BLOCKED )
       PARTITION-COORDINATOR ( TABLE: SYS.T1, PARTITION: 1/2, FULL SCAN, ACCESS: 1, COST: BLOCKED )
        SCAN ( PARTITION: P1, FULL SCAN, ACCESS: 1, COST: BLOCKED )
      ------------------------------------------------------------
      ```
  
- **Workaround**

  ```sql
  USE "NO_PLAN_CACHE" hint
  
  iSQL> SELECT /*+ NO_EXEC_FAST NO_PLAN_CACHE */ * FROM T1 PARTITION(P1) WHERE I1 = 130;
  I1          I2          
  ---------------------------
  130         100         
  1 row selected.
  ```

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

Changes
-------

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    7.1.0.5.4     |          6.5.1          |    8.9.1     |        7.1.7        |            7.4.6             |

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
