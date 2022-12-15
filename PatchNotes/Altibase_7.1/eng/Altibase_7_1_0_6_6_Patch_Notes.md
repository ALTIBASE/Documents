Altibase 7.1.0.6.6 Patch Notes
==============================

<br/>

<br/>

# Table Of Contents

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Fixed Bugs](#fixed-bugs)
    - [BUG-49039 If there is a disabled index, the Altibase server abnormally terminates when querying V$SEGMENT.](#bug-49039-if-there-is-a-disabled-index-the-altibase-server-abnormally-terminates-when-querying-v$segment)
    - [BUG-49423 If the statement object is not cleaned up during SQL PLAN CACHE processing, the Altibase server may abnormally terminate or CPU usage may increase.](#bug-49423-if-the-statement-object-is-not-cleaned-up-during-sql-plan-cache-processing-the-altibase-server-may-abnormally-terminate-or-cpu-usage-may-increase)
    - [BUG-49433 If the statement object is not cleaned up when a transaction is committed, the Altibase server may abnormally terminate.](#bug-49433-if-the-statement-object-is-not-cleaned-up-when-a-transaction-is-committed-the-altibase-server-may-abnormally-terminate)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [Altibase Server Properties](#altibase-server-properties)
    - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->



Fixed Bugs
==========

### BUG-49039 If there is a disabled index, the Altibase server abnormally terminates when querying V$SEGMENT.

-   **module** : sm

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixes a bug where the Altibase server abnormally terminates when querying V$SEGMENT if there is a disabled index.

- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    CREATE TABLE D1 ( I1 INTEGER, I2 CHAR(3000), I3 INTEGER ) TABLESPACE SYS_TBS_DISK_DATA;
    CREATE INDEX D1_I1_I2 ON D1(I1,I2);
    ALTER TABLE D1 ALL INDEX DISABLE;
    SELECT COUNT(*) FROM V$SEGMENT;
    ```

  - **Actual Results**

    ```
    Altibase server abnormal termination
    ```

  - **Expected Results**

    ```
    Execute SQL statement normally
    ```

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49423 If the statement object is not cleaned up during SQL PLAN CACHE processing, the Altibase server may abnormally terminate or CPU usage may increase.

- **module** : mm-plancache

- **Category** : Maintainability

- **Reproducibility** : Frequence

- **Description** : Fixes a phenomenon in which the Altibase server abnormally terminates or CPU usage increases when statement objects are not cleaned up during SQL PLAN CACHE processing. When an abnormal shutdown of the Altibase server due to this bug occurs, the following log is left in altibase_error.log.
  
  ```bash
  IDE_ASSERT( aTrans->mStatus == SMX_TX_END ), [smxTransMgr.h:272], errno=[2]
  [[ASSERT] ERROR LINE => [smxTransMgr.h:272]
  ```
  
  You may also see an increase in CPU utilization even though there are few or no SQL statements being executed.
  
- **How to reproduce this bug**

  - **Reproduction conditions**

  - **Actual Results**

  - **Expected Results**

- **Workaround**

- **Changes**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

### BUG-49433 If the statement object is not cleaned up when a transaction is committed, the Altibase server may abnormally terminate.

-   **module** : sm

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixes a bug in which the Altibase server abnormally terminates when a statement object is not cleaned up when a transaction commit is performed. The statement object is forcibly cleaned up and the call stack for problem analysis is recorded in the Altibase trace log.
    
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
|    7.1.0.6.6     |          6.5.1          |    8.10.1    |        7.1.7        |            7.4.7             |

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
