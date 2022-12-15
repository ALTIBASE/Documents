# Altibase 7.1.0.7.4 Patch Notes

<br/>

<br/>

# **Table of Contents** 

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Fixed Bugs](#fixed-bugs)
    - [BUG-46674 Addresses misaligned memory allocation issues when the memory pooling feature is disabled (USE_MEMORY_POOL = 0).](#bug-46674addresses-misaligned-memory-allocation-issues-when-the-memory-pooling-feature-is-disabled-use_memory_pool--0)
    - [BUG-49614 When THREAD_REUSE_ENABLE=0 is set and Altibase server is running, inaccurate memory statistics information is output to V$MEMSTAT.](#bug-49614when-thread_reuse_enable0-is-set-and-altibase-server-is-running-inaccurate-memory-statistics-information-is-output-to-vmemstat)
    - [BUG-49646 Resolves an error that occurs when one of the join tables used in a view object is dropped and recreated as a partitioned table with a primary key.](#bug-49646resolves-an-error-that-occurs-when-one-of-the-join-tables-used-in-a-view-object-is-dropped-and-recreated-as-a-partitioned-table-with-a-primary-key)
    - [BUG-49681 Altibase server may be terminated abnormally due to concurrency issues when buffer replacement occurs due to insufficient buffer pool while processing a transaction accessing a disk tablespace.](#bug-49681altibase-server-may-be-terminated-abnormally-due-to-concurrency-issues-when-buffer-replacement-occurs-due-to-insufficient-buffer-pool-while-processing-a-transaction-accessing-a-disk-tablespace)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [Altibase Server Properties](#altibase-server-properties)
    - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Fixed Bugs
==========

### BUG-46674 Addresses misaligned memory allocation issues when the memory pooling feature is disabled (USE_MEMORY_POOL = 0).

-  **module** : id

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixes a phenomenon in which Altibase server abnormally terminates when memory pooling is disabled by setting the Altibase server property USE_MEMORY_POOL to 0, and an unaligned address value is allocated when memory allocation requires an aligned address value.
    
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

### BUG-49614 When THREAD_REUSE_ENABLE=0 is set and Altibase server is running, inaccurate memory statistics information is output to V$MEMSTAT.

-   **module** : id

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Improve the phenomenon that incorrect memory statistics information is output to ALLOC_SIZE of V$MEMSTAT when the thread reuse function is not used by setting the Altibase server property THREAD_REUSE_ENABLE=0.
    
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

### BUG-49646 Resolves an error that occurs when one of the join tables used in a view object is dropped and recreated as a partitioned table with a primary key.

-   **module** : qp-ddl-dcl-pvo

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixes an abnormal termination of the Altibase server when one of the join tables used in a view object is deleted and recreated as a partitioned table with a primary key.      
    
    This bug occurs when performing the procedure below.
    
    1. Use joins and USE_INDEX_NL hint when creating view objects
    2. Drop base table accessed from view
    3. Create a partitioned table with a primary key or unique key with the same name as the deleted base table.

-   **How to reproduce this bug**

    -   **Reproduction conditions**

            DROP TABLE T1;
            DROP VIEW  V1;
            CREATE TABLE T1 ( I1 INTEGER );
            CREATE TABLE T2 ( I1 INTEGER );
            CREATE VIEW V1 AS
            SELECT /*+ USE_INDEX_NL(T1, T2) */ T1.I1 I1
                 , T2.I1 I2
              FROM T1 T1
                 , T1 T2
             WHERE T1.I1 = T2.I1;
            DROP TABLE T1;
            CREATE TABLE T1
            (
              I1 INTEGER PRIMARY KEY
            )
            PARTITION BY RANGE( I1 )
            (
              PARTITION P1 VALUES LESS THAN ( 100 ),
              PARTITION P2 VALUES DEFAULT
            );

    -   **Actual Results**

            Altibase server abnormal termination

    -   **Expected Results**

            Create success.

-   **Workaround**

        Remove USE_INDEX_NL

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49681 Altibase server may be terminated abnormally due to concurrency issues when buffer replacement occurs due to insufficient buffer pool while processing a transaction accessing a disk tablespace.

-   **module** : sm-disk-page

-   **Category** : Assert

-   **Reproducibility** : Rare

-   **Description** : Fixes a phenomenon in which the Altibase server abnormally terminates due to a concurrency problem when a buffer replacement occurs due to insufficient buffer pool while processing a transaction accessing a disk tablespace. 

    If the Altibase server is abnormally terminated due to this bug, the following log is output to altibase_error.log.

    ```
    BCB Info..
    mID 7922
    mState 2
    mFrame 7fc8d69a4000
    mSpaceID 6
    ...
    
    IDE_ASSERT( 0 ), [sdbBufferPool.cpp:852], errno=[16]
    errno=[16]
    
    [ASSERT] ERROR LINE => [sdbBufferPool.cpp:852]
    ERR-0109e(errno=16) Internal server error.
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

Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    7.1.0.7.4     |          6.5.1          |    8.10.1    |        7.1.7        |            7.4.7             |

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
