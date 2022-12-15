# Altibase 7.1.0.6.5 Patch Notes

<br/>

<br/>

# **Table of Contents**  

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [New Features](#new-features)
    - [BUG-49330 Improve the execution plan of WITH clauses or VIEWs with set operators.](#bug-49330-improve-the-execution-plan-of-with-clauses-or-views-with-set-operators)
    - [BUG-49398 Adds a function to retry when DDL execution temporarily fails due to table lock acquisition failure or deadlock during DDL replication execution.](#bug-49398-adds-a-function-to-retry-when-ddl-execution-temporarily-fails-due-to-table-lock-acquisition-failure-or-deadlock-during-ddl-replication-execution)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-48756 In AUTOCOMMIT OFF mode, the Altibase server may abnormally terminate when executing a SQL statement that accesses a general table after executing an SQL statement that searches meta tables.](#bug-48756-in-autocommit-off-mode-the-altibase-server-may-abnormally-terminate-when-executing-a-sql-statement-that-accesses-a-general-table-after-executing-an-sql-statement-that-searches-meta-tables)
    - [BUG-49141 orrectly changes the memory manager used by DDL statement validation related to replication objects.](#bug-49141-orrectly-changes-the-memory-manager-used-by-ddl-statement-validation-related-to-replication-objects)
    - [BUG-49418 Change the operation of the date time function DATEDIFF according to the manual description so that an error occurs when date_field_name is SECOND and the result exceeds 2144448000 seconds.](#bug-49418-change-the-operation-of-the-date-time-function-datediff-according-to-the-manual-description-so-that-an-error-occurs-when-date_field_name-is-second-and-the-result-exceeds-2144448000-seconds)
    - [BUG-49424 If the number of columns in replication target tables is different between the local server and the remote server, the Altibase server may abnormally terminate when performing a replication transaction on the remote server.](#bug-49424-if-the-number-of-columns-in-replication-target-tables-is-different-between-the-local-server-and-the-remote-server-the-altibase-server-may-abnormally-terminate-when-performing-a-replication-transaction-on-the-remote-server)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [Altibase Server Properties](#altibase-server-properties)
    - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->



New Features
============

### BUG-49330 Improve the execution plan of WITH clauses or VIEWs with set operators.

-   **module** : qp-select

-   **Category** : Enhancement

-   **Reproducibility** : Always

-   **Description** : The execution plan has been improved by removing unnecessary execution nodes when using set operators in the WITH clause or VIEW. Do not create unnecessary PROJECT nodes and VIEW nodes. Among the set operators, UNION ALL, INTERSECT, and MINUS excluding UNION are applicable. This bug may not apply if LIMIT, LOOP clauses are used. You need to change the private property to apply this bug. If necessary, please contact the Altibase Technical Support Center.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    DROP TABLE T1;
    CREATE TABLE T1 ( I1 INTEGER , I2 INTEGER, I3 INTEGER );
    INSERT INTO T1 VALUES ( 1, 11, 21);
    INSERT INTO T1 VALUES ( 2, 12, 22);
    INSERT INTO T1 VALUES ( 3, 13, 33);
    ALTER SESSION SET EXPLAIN PLAN = ON;
    WITH W1 AS 
    (
      SELECT I1 FROM T1
      UNION ALL
      SELECT I2 FROM T1
      UNION ALL
      SELECT I3 FROM T1 
    )
    SELECT * FROM W1;
    ```

  - **Actual Results**

    ```sql
    iSQL> WITH W1 AS 
        2 (
        3   SELECT I1 FROM T1
        4   UNION ALL
        5   SELECT I2 FROM T1
        6   UNION ALL
        7   SELECT I3 FROM T1 
        8 )
        9 SELECT * FROM W1;
    I1          
    --------------
    1           
    2           
    3           
    11          
    12          
    13          
    21          
    22          
    33          
    9 rows selected.
    ------------------------------------------------------------
    PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: 712.44 )
     VIEW ( W1, ACCESS: 9, COST: 708.49 )
      PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: 358.20 )
       VIEW ( ACCESS: 9, COST: 354.24 )
        BAG-UNION
         PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: 118.08 )
          SCAN ( TABLE: SYS.T1, FULL SCAN, ACCESS: 3, COST: 116.76 )
         PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: 118.08 )
          SCAN ( TABLE: SYS.T1, FULL SCAN, ACCESS: 3, COST: 116.76 )
         PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: 118.08 )
          SCAN ( TABLE: SYS.T1, FULL SCAN, ACCESS: 3, COST: 116.76 )
    ------------------------------------------------------------
    ```

  -   **Expected Results**

      ```sql
      iSQL> WITH W1 AS 
          2 (
          3   SELECT I1 FROM T1
          4   UNION ALL
          5   SELECT I2 FROM T1
          6   UNION ALL
          7   SELECT I3 FROM T1 
          8 )
          9 SELECT * FROM W1;
      W1.I1
      --------------
      1
      2
      3
      11
      12
      13
      21
      22
      33
      9 rows selected.
      ------------------------------------------------------------
      PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: BLOCKED )
       VIEW ( W1, ACCESS: 9, COST: BLOCKED )
          BAG-UNION
           PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: BLOCKED )
            SCAN ( TABLE: SYS.T1, FULL SCAN, ACCESS: 3, COST: BLOCKED )
           PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: BLOCKED )
            SCAN ( TABLE: SYS.T1, FULL SCAN, ACCESS: 3, COST: BLOCKED )
           PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: BLOCKED )
            SCAN ( TABLE: SYS.T1, FULL SCAN, ACCESS: 3, COST: BLOCKED )
      ------------------------------------------------------------
      ```

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49398 Adds a function to retry when DDL execution temporarily fails due to table lock acquisition failure or deadlock during DDL replication execution.

-   **module** : rp

-   **Category** : Other

-   **Reproducibility** : Always

-   **Description** : 
    
    This bug applies to a replication environment that satisfies all of the conditions below. 
    
    - REPLICATION_DDL_SYNC = 1
    - REPLICATION_DDL_ENABLE = 1
    
    **Added retry function in case of DDL replication failure**
    
    Adds a function to retry when DDL execution temporarily fails due to table lock acquisition failure or deadlock during DDL replication.
    
    The difference in operation by version of Altibase 7.1 before and after applying this bug is as follows.
    
    - Altibase 7.1.0.6.4 or earlier   
      
      Abort DDL replication as soon as a temporary DDL failure occurs.
      
    - Altibase 7.1.0.6.5 or higher
      
      In the event of a transient DDL failure, DDL replication execution is retried for the duration of the REPLICATION_DDL_SYNC_TIMEOUT property. Abort DDL replication if not successful within the REPLICATION_DDL_SYNC_TIMEOUT property time.
      
      
    
    **replication protocol version change**  
    The patch version of the replication protocol version has been changed from 7.4.6 to 7.4.7 with the addition of the replication function. For the DDL replication function, all three digits of the replication protocol version of the replication target server must match.
    
    
    
    **Precautions when patching**
    
    The replication DDL copy function must be stopped when patching.
    
    You cannot use the dual DDL replication function between Altibase 7.1.0.6.4 or earlier and Altibase 7.1.0.6.5 or later. After applying this bug to all replication target servers, you must use the DDL replication function.
    
    The log below is recorded when duplicate DDL replication is performed between Altibase servers with different duplicate protocol versions.
    
    - Altibase client error
    
      ```
      ERR-61186 : A DDL synchronization receives the error message from the remote server (REPLICATION_NAME : Different replication protocols).]
      ```
    
    - Altibase Server Trace Log(altibase_rp.log)
    
      ```
      [DDLSyncManager] DDL sync failure : Different replication protocols 
      ```
    
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

Fixed Bugs
==========

### BUG-48756 In AUTOCOMMIT OFF mode, the Altibase server may abnormally terminate when executing a SQL statement that accesses a general table after executing an SQL statement that searches meta tables.

-   **module** : qp

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : In AUTOCOMMIT OFF mode, the Altibase server abnormally terminates when executing a SQL statement that accesses a general table after executing an SQL statement that searches meta tables. Fixed a problem that occurred in the transaction reuse process.
    
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

### BUG-49141 orrectly changes the memory manager used by DDL statement validation related to replication objects.

-   **module** : rp
-   **Category** : Memory Error
-   **Reproducibility** : Always
-   **Description** : Correctly changes the memory manager used by DDL statement validation related to replication objects. When the DDL statement below is executed, the display of memory usage changes from Query_Execute to Query_Prepare in V$MEMSTAT.
    - CREATE REPLICATION 
    - ALTER REPLICATION *replication\_name* ADD TABLE
    - ALTER REPLICATION *replication\_name* DROP TABLE
    - ALTER REPLICATION *replication\_name* SYNC
    - DROP REPLICATION
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

### BUG-49418 Change the operation of the date time function DATEDIFF according to the manual description so that an error occurs when date_field_name is SECOND and the result exceeds 2144448000 seconds.

-   **module** : qp

-   **Category** : Functionality

-   **Reproducibility** : Always

-   **Description** : When the third argument date_field_name of the DATEDIFF function is SECOND, an error occurs when the difference between enddate and startdate exceeds 2144448000 seconds, which is 68 years based on a normal year (365 days).

    > Reference : [Altibase 7.1 SQL Reference - DATEDIFF](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/eng/SQL%20Reference.md#datediff)

-   **How to reproduce this bug**

    -   **Reproduction conditions**

        ```sql
        SELECT DATEDIFF('27-SEP-2005', '30-DEC-2074', 'SECOND') FROM DUAL;
        ```

    -   **Actual Results**

        ```sql
        DATEDIFF('27-SEP-2005','30-DEC-2074','SECO 
        ---------------------------------------------
        2185574400           
        1 row selected.
        ```

    -   **Expected Results**

        ```sql
        [ERR-2102D : The interval between startdate and enddate exceeded 68 years. 
        0001 : SELECT DATEDIFF('27-SEP-2005', '30-DEC-2074', 'SECOND') FROM DUAL
                     ^                                               ^
        ]
        ```

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49424 If the number of columns in replication target tables is different between the local server and the remote server, the Altibase server may abnormally terminate when performing a replication transaction on the remote server.

-   **module** : rp

-   **Category** : Fatal

-   **Reproducibility** : Rare

-   **Description** : If the number of columns in replication target tables is different between the local server and the remote server, the Altibase server may abnormally terminate when performing a replication transaction on the remote server. A column analysis error in Receiver has been corrected.

    This bug occurs in the version where BUG-47458 bug is reflected. The bug exposure patch version for each Altibase version is as follows.

    - Altibase 7.1.0.3.1 ~ 7.1.0.6.4

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
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    7.1.0.6.5     |          6.5.1          |    8.10.1    |        7.1.7        |         ***7.4.7***          |

> You can check the module version change history in [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.1/Altibase_7_1_Version_Histories.md).

#### Compatibility

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

#### Added Properties

#### Changed Properties

#### Deleted Properties

### Performance Views

#### Added Performance Views

#### Changed Performance Views

#### Deleted Performance Views