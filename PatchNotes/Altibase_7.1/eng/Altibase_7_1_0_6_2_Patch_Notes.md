Altibase 7.1.0.6.2 Patch Notes
==============================

<br/>

<br/>

# Table Of Contents

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Fixed Bugs](#fixed-bugs)
    - [BUG-49266 Fix memory initialization error in transaction processing function.](#bug-49266fix-memory-initialization-error-in-transaction-processing-function)
    - [BUG-49273 A result value error may occur if a view where view merging has occurred is used with a set operator.](#bug-49273a-result-value-error-may-occur-if-a-view-where-view-merging-has-occurred-is-used-with-a-set-operator)
    - [BUG-49287 When the transaction segments of the remote server are all in use and the replication receiver reflects the update transaction to the disk table, an infinite wait occurs.](#bug-49287when-the-transaction-segments-of-the-remote-server-are-all-in-use-and-the-replication-receiver-reflects-the-update-transaction-to-the-disk-table-an-infinite-wait-occurs)
    - [BUG-49320 If an index node is split during 'ALTER INDEX ~ REORGANIZE', the index structure may be corrupted and consistency errors may occur in SQL execution results.](#bug-49320if-an-index-node-is-split-during-alter-index--reorganize-the-index-structure-may-be-corrupted-and-consistency-errors-may-occur-in-sql-execution-results)
    - [BUG-49322 If COUNT(column_name) KEEP is used, the Altibase server may terminate abnormally.](#bug-49322if-countcolumn_name-keep-is-used-the-altibase-server-may-terminate-abnormally)
    - [BUG-49332 Prevents the possibility of abnormal termination of Altibase server when xLog is modified due to network packet tampering during duplication.](#bug-49332prevents-the-possibility-of-abnormal-termination-of-altibase-server-when-xlog-is-modified-due-to-network-packet-tampering-during-duplication)
    - [BUG-49334 Altibase server abnormally terminates when a memory reference error occurs in C/C++ External Procedures.](#bug-49334altibase-server-abnormally-terminates-when-a-memory-reference-error-occurs-in-cc-external-procedures)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [Altibase Server Properties](#altibase-server-properties)
    - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->





Fixed Bugs
==========

### BUG-49266 Fix memory initialization error in transaction processing function.

-   **module** : sm

-   **Category** : Memory Error

-   **Reproducibility** : Always

-   **Description** : A memory initialization error that exists in the transaction processing function is corrected to eliminate the possibility of abnormal termination of the Altibase server.

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

### BUG-49273 A result value error may occur if a view where view merging has occurred is used with a set operator.

-   **module** : qp-dml-pvo

-   **Category** : Functional Error

-   **Reproducibility** : Rare

-   **Description** : Fixes a bug where a result value error occurs when a view with view merging is used with a set operator.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    DROP TABLE T1;
    CREATE TABLE T1 ( C1 INT, C2 INT, C3 INT);
    
    INSERT INTO T1 VALUES( 1, 2, 3);
    INSERT INTO T1 VALUES( 2, 3, 4);
    
    WITH WITH_1 
    AS 
    (SELECT C1, C2
       FROM (SELECT /*+ no_merge */ A.C1, A.C2
               FROM T1 A) C 
    )
    SELECT c1
      FROM (SELECT NULL, C1
              FROM WITH_1
             UNION ALL
            SELECT NULL, C1
              FROM WITH_1 ) v1 
    ;
    ```

  - **Actual Results**

    ```sql
    C1
    --------------
    
    
    
    
    4 rows selected.
    ```

  -   **Expected Results**

      ```sql
      C1
      --------------
      1
      2
      1
      2
      4 rows selected.
      ```

- **Workaround**

  ```sql
  /*+ NO_MERGE(WITH_1) */
  ```

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49287 When the transaction segments of the remote server are all in use and the replication receiver reflects the update transaction to the disk table, an infinite wait occurs.

-   **module** : rp-receiver

-   **Category** : Hang

-   **Reproducibility** : Always

-   **Description** : Fixes a bug where the replication receiver waits indefinitely when reflecting a update transaction to the disk table while the remote server's transaction segments are all in use. If all transaction segments of the remote server are in use, the following error message appears in $ALTIBASE_HOME/trc/altibase_boot.log.
    
    ~~~bash
    TRANSACTION_SEGMENT_COUNT is full !!
    Transaction (TID:169992) is waiting for TXSegs allocation.
    ~~~
    
    When the above phenomenon occurs, the replication receiver waits for about 10 seconds and then cancels the operation and terminates the replication receiver.
    
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

### BUG-49320 If an index node is split during 'ALTER INDEX ~ REORGANIZE', the index structure may be corrupted and consistency errors may occur in SQL execution results.

-   **module** : sm-mem-index

-   **Category** : Functionality

-   **Reproducibility** : Always

-   **Description** : Fixed a bug where the index structure was corrupted when an index node was split during 'ALTER INDEX ~ REORGANIZE', resulting in consistency errors in SQL execution results.
    
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

### BUG-49322 If COUNT(column_name) KEEP is used, the Altibase server may terminate abnormally.

-   **module** : mt-function

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixes a bug where the Altibase server abnormally terminates when 'COUNT(column_name) KEEP' is used.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    DROP TABLE t1; 
    CREATE TABLE T1 ( I1 INTEGER PRIMARY KEY, I2 INTEGER );
    INSERT INTO T1 VALUES ( 5, 5 );
    INSERT INTO T1 VALUES( 3, 3 );
    SELECT COUNT(I1) KEEP ( DENSE_RANK LAST ORDER BY I2 DESC ) FROM T1;
    ```

  -   **Actual Results**

          Altibase server abnormally terminates.

  -   **Expected Results**

      ```sql
      COUNT(I1)KEEP(DENSE_RANKLASTORDERBYI2DESC) 
      ---------------------------------------------
      1                    
      1 row selected.
      ```

-   **Workaround**

        OPTIMIZER_COUNT_COLUMN_TO_COUNT_ASTAR = 0

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49332 Prevents the possibility of abnormal termination of Altibase server when xLog is modified due to network packet tampering during duplication.

-   **module** : rp-receiver

-   **Category** : Functional Error

-   **Reproducibility** : Unknown

-   **Description** : Prevents the possibility of abnormal termination of Altibase server when xLog is modified due to network packet tampering during duplication.

    ```bash
    [2021/09/28 18:08:58 F5FD][PID:187816][Thread-140133571839744][LWP-189001]
    transaction abort error [TID : 61783414]
    [2021/09/28 18:08:58 F5FE][PID:187816][Thread-140133571839744][LWP-189001]
    ERR-1104d(errno=62) An update statement already exists.
    ```

    This phenomenon only occurs when someone manipulates xlog in the middle of the network, and does not occur under normal situation. If this bug is reflected, the replication receiver terminates with the following error, and then restarted by the replication sender to start replication again.

    ```bash
    [2021/10/01 19:51:32 59F][PID:30274][Thread-1417512704][LWP-30388]
    ERR-61069(errno=62) Internal server error in replication module
    ([rpsSmExecutor::convertValueToOID] Column not found [CID: 0] at [Remote SN: 8590708662, TID: 49988, TABLEID: 4461760]).
    [2021/10/01 19:51:32 5A0][PID:30274][Thread-1417512704][LWP-30388]
    UPDATE SYS.T1 SET I1 = '100' WHERE PK = 1; (TID : 49988)
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

### BUG-49334 Altibase server abnormally terminates when a memory reference error occurs in C/C++ External Procedures.

-   **module** : qp-psm-trigger-execute

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixes a bug where the Altibase server abnormally terminates due to lack of exception handling when a memory reference error occurs in C/C++ External Procedures.
    
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
|    7.1.0.6.2     |          6.5.1          |    8.10.1    |        7.1.7        |            7.4.6             |

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
