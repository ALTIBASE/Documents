Altibase 7.3.0.1.9 Patch Notes
================================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-52215 Added functionality to specify the abm log (abm.log) path](#bug-52215)
    - [BUG-52224 Added log messages related to Replication Give-up](#bug-52224)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-48937 Fixed a failure in deleting backup files when user-created directories exist in the incremental backup directory](#bug-48937)
    - [BUG-51953 Improved behavior to stop the replication receiver if memory tablespace resources are insufficient](#bug-51953)
    - [BUG-52181 Fixed the replication give-up failure when the log file count exceeds REPLICATION_MAX_LOGFILE](#bug-52181)
    - [BUG-52213 Improvement to Prevent Incorrect Accumulated Time in Statistics](#bug-52213)
    - [BUG-52190 Fix for Abnormal Lock Release Depending on SELECT Execution Order in Non-AutoCommit Mode](#bug-52190)
    - [BUG-52219 Fixed incorrect variable column padding when generating Supplemental Logs](#bug-52219)
    - [BUG-52230 Fixed "Meta table crashed" error when SYS revokes Role privileges granted by another user](#bug-52230)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [Compatibility](#compatibility)
    - [Properties](#properties)
    - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-52215<a name=bug-52215></a> Added functionality to specify the abm log (abm.log) path

-   **module** :

-   **Category** : Functionality

-   **Reproducibility** : Always

-   **Description** : A `-log_path` option has been added to allow specifying the path where the `abm.log` file is created.
     If `-log_path` is not specified, the `abm.log` file is created in the current working directory where abm is executed.
    
    Additionally, an `abm.properties` file has been added, and the log path can also be configured via the `LOG_PATH` property within this file.

### BUG-52224<a name=bug-52224></a> Added log messages related to Replication Give-up

- **module** : rp-sender

- **Category** : Enhancement

- **Reproducibility** : Always

- **Description** :  When the `REPLICATION_MAX_LOGFILE` property is set to 1 or higher, new log messages have been added to provide visibility when a Give-up occurs and when the Replication SENDER restarts after a Give-up.REPLICATION_MAX_LOGFILE 프로퍼티 값을 1 이상으로 설정한 이후, Give-up이 발생했을 때 확인할 수 있는 로그 메시지와 Give-up
  이후 이중화 SENDER가 재시작되었을 때 확인할 수 있는 로그 메시지가 추가 되었습니다.

  로그 메시지는 아래와 같이 추가되었습니다.

  -   Give-up Start: **[Manager] Replication {replication_name} Sender Give-up Start.**
  -   Give-up End: **[Manager] Replication {replication_name} Sender Give-up End.**
  -   Sender Restart during Give-up: **[Manager] Replication {replication_name} Restarts Sender After Give-up.**

Fixed Bugs
==========

### BUG-48937<a name=bug-48937></a> Fixed a failure in deleting backup files when user-created directories exist in the incremental backup directory

- **module** : sm

- **Category** : Message Error

- **Reproducibility** : Always

- **Description** : Fixed an issue where the statement `ALTER DATABASE DELETE OBSOLETE BACKUP FILES;` failed with `[ERR-41082: Internal server error]` if the incremental backup directory contained user-created subdirectories. Now, the statement executes successfully even if user-created directories exist; those directories are preserved. 

  Additionally, information about directories that could not be deleted is recorded in the `altibase_sm.log` file under the `trc` directory.

  - Example log message in `altibase_sm.log`:

    [BackupInfoMgr] Unable to delete <backup_path> (errno=39)

### BUG-51953<a name=bug-51953></a> Improved behavior to stop the replication receiver if memory tablespace resources are insufficient

-   **module** : rp

-   **Category** : Enhancement

-   **Reproducibility** : Always

-   **Description** : When the replication fails due to insufficient memory tablespace resources, the behavior has been changed.
    
    Previously, such errors were treated as conflicts. After the fix, the replication receiver is stopped instead.
    
    This applies to the following cases:
    
    -   Auto-extension of the memory tablespace is disabled
        (smERR_ABORT_UNABLE_TO_EXTEND_CHUNK_WHEN_AUTO_EXTEND_OFF)
    -   The memory tablespace size exceeds MEM_MAX_TBS_SIZE
        (smERR_ABORT_UNABLE_TO_EXTEND_CHUNK_MORE_THAN_MEM_MAX_DB_SIZE)
    -   The memory tablespace exceeds its maximum size
        (smERR_ABORT_UNABLE_TO_EXTEND_CHUNK_MORE_THAN_TBS_MAXSIZE )

### BUG-52181<a name=bug-52181></a> Fixed the replication give-up failure when the log file count exceeds REPLICATION_MAX_LOGFILE

- **module** : rp-sender

- **Category** : Functional Error

- **Reproducibility** : Always

- **Description1** : In a replication environment where `REPLICATION_MAX_LOGFILE` is set to 1 or higher,
   if the number of log files exceeds the value of the `REPLICATION_MAX_LOGFILE` property, a give-up is triggered during checkpoint execution.

  This issue has been fixed where the give-up operation failed due to a timeout during this process.

### BUG-52213<a name=bug-52213></a> Improvement to Prevent Incorrect Accumulated Time in Statistics

-   **module** : id
-   **Category** : Enhancement
-   **Reproducibility** : Unknown
-   **Description** : Improved to prevent incorrect accumulated time from being recorded in statistics.

### BUG-52190<a name=bug-52190></a> Fix for Abnormal Lock Release Depending on SELECT Execution Order in Non-AutoCommit Mode

-   **module** : sm
-   **Category** : Fatal
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where IS_LOCK was released abnormally depending on the execution order of SELECT statements within a single transaction in Non-AutoCommit mode.

### BUG-52219<a name=bug-52219></a> Fixed incorrect variable column padding when generating Supplemental Logs

-   **module** : sm
-   **Category** : Functional Error
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where `UPDATE` statements failed due to incorrect handling of variable column padding during the generation of Supplemental Logs.

### BUG-52230<a name=bug-52230></a> Fixed "Meta table crashed" error when SYS revokes Role privileges granted by another user

-   **module** : qp-ddl-dcl-execute

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where `[ERR-31015: The meta table crashed.]` occurred when the `SYS` account attempted to revoke object privileges from a Role that were originally granted by the Role owner (another user).
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    ## Create userA user , role 
    create user userA identified by userA;
    create role r_userA;
    
    ## connect by userA and create userA.T1
    connect userA/userA;
    create table T1(c1 integer primary key, c2 varchar(10), c3 varchar(10));
    
    ## userA user grants the privileges to r_userA
    grant delete, insert, select, update on userA.T1 to r_userA; 
    
    ## sys user try to revoke the privileges from r_userA
    connect sys/manager;
    revoke delete, insert, select, update on userA.T1 from r_userA;
    ```

  - **Actual Results**

        [ERR-31015 : The meta table crashed.
        0001 : revoke delete, insert, select, update on userA.T1 from R_userA
        ^ ^
        ]

  - **Expected Results**

    ```
    Revoke success.
    ```

-   **Workaround**

        Grant and revoke privileges using the SYS user.

# Changes

### Version Info

| **Altibase Version** | **Database Binary Version** | **Meta Version** | **CM Protocol Version** | **Replication Protocol Version** |
| -------------------- | --------------------------- | ---------------- | ----------------------- | -------------------------------- |
| 7.3.0.1.9            | 7.3.0                       | 9.4.1            | 7.1.8                   | 7.4.9                            |

### Compatibility

#### Database binary version

The database binary version has not changed.

> The database binary version indicates the compatibility of database image files and log files. If this version needs to be patched to a different version, the database must be reorganized.

#### Meta Version

The meta version has not changed.

> If you want to roll back the patch after patching to a version with a changed meta version, see [Meta Downgrade](https://manual.altibase.com/7.3/en/start-here/install/3.-Uninstalling-Altibase-and-Meta-Downgrade/#meta-downgrade).

#### CM protocol Version

The cm protocol version has not changed.

#### Replication protocol Version

The replication protocol version has not changed.

### Properties

No properties added/changed/deleted.

### Performance Views

No performance views added/changed/deleted.
