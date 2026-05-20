Altibase 8.1.0.0.2 Patch Notes
================================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-52206 Expanded JSON Data Type Support in Log Analyzer (ALA) and Adapter](#bug-52206)
    - [BUG-52215 Added abm.log Path Configuration Feature](#bug-52215)
    - [BUG-52233 Added gzip Compression Level Configuration in abm](#bug-52233)
    - [BUG-52224 Added Log Messages for Replication Give-up Events](#bug-52224)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-48937 Fixed a failure in deleting backup files when user-created directories exist in the incremental backup directory](#bug-48937)
    - [BUG-51201 Fixed an issue where XLog application order could be reversed depending on partition order if replication target partitions are not divided by PK.](#bug-51201)
    - [BUG-51324 Fixed performance degradation when collecting disk index statistics in parallel.](#bug-51324)
    - [BUG-51953 Improved behavior to stop the replication receiver if memory tablespace resources are insufficient.](#bug-51953)
    - [BUG-52106 Fixed missing server error messages during incremental backup in abm](#bug-52106)
    - [BUG-52122 Fixed incorrect error message when Change Tracking is disabled in abm](#bug-52122)
    - [BUG-52119 Fixed UPDATE Failure During Replication Through jdbcAdapter with SUPPLEMENTAL LOG Enabled](#bug-52119)
    - [BUG-52140 Fixed Core Dump When View DDL Exceeds 100 Bytes in `VIEW_FORCE=ON` Environment](#bug-52140)
    - [BUG-52152 Fixed Malformed Query Output in Logs When Error Occurs During UPDATE/DELETE in adapter](#bug-52152)
    - [BUG-52163 Fixed EMPTY_CLOB() Handling Error for Temporary LOB in CLI Environment](#bug-52163)
    - [BUG-52168 Fixed performance issue for disk table DML after expanding BUFFER AREA SIZE](#bug-52168)
    - [BUG-52171 Fixed a server crash when renaming a table that has a trigger using SQL functions.](#bug-52171)
    - [BUG-52181 Fixed an issue where Give-up could fail during data replication in a REPLICATION_MAX_LOGFILE configuration](#bug-52181)
    - [BUG-52188 Improved stability of diagnostic dump information collection during abnormal termination](#bug-52188)
    - [BUG-52189 Fixed Error When Using EMPTY_CLOB() in JSON Functions](#bug-52189)
    - [BUG-52190 Fix for Abnormal Lock Release Depending on SELECT Execution Order in Non-AutoCommit Mode](#bug-52190)
    - [BUG-52192 Improved error messages when system call fails during file backup.](#bug-52192)
    - [BUG-52213 Improvement to Prevent Incorrect Accumulated Time in Statistics](#bug-52213)
    - [BUG-52219 Fixed incorrect variable column padding when generating Supplemental Logs](#bug-52219)
    - [BUG-52220 Fixed server crash when executing DROP COLUMN on replicated disk tables with LOB and Supplemental Log](#bug-52220)
    - [BUG-52226 Fixed standby server crash during DELETE log processing in SQL_APPLY mode](#bug-52226)
    - [BUG-52229 Fixed \[ERR-314B8 : Failed to seek a Session Temporary LOB.] error during Temporary LOB concat pperation](#bug-52229)
    - [BUG-52230 Fixed \[ERR-31015 : The meta table crashed.] error when SYS revokes Role privileges granted by another user](#bug-52230)
    - [BUG-52236 Fixed ASSERT failure when handling bind-less requests from older client](#bug-52236)
    - [BUG-52261 Fixed timeout issue when concurrently executing UPDATE Statements with EMPTY_CLOB() or EMPTY_BLOB() in oraAdapter](#bug-52261)
    - [BUG-52262 Fixed abnormal server termination when an invalid protocol header is received during connection from an older client (6.1.1 or earlier).](#bug-52262)
    - [BUG-52284 Fixed DBMS_METADATA Failure in aexport When All Public Synonyms Are Removed](#bug-52284)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [Compatibility](#compatibility)
    - [Altibase Server Properties](#altibase-server-properties)
    - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# New Features

### BUG-52206<a name=bug-52206></a> Expanded JSON Data Type Support in Log Analyzer (ALA) and Adapter

- **module** : rp

- **Category** : Other

- **Reproducibility** : Always

- **Description** : Altibase Log Analyzer (ALA) and Adapter (oraAdapter, jdbcAdapter) now support the JSON data type in replication environments.

  During replication through ALA and Adapter, JSON data is converted to CLOB format and transferred through logs. Therefore, the target column mapped to the JSON data type in the target database must be configured as a CLOB type.

- **Changes**

  - Performance view

  - Property

    - Added [REPLICATION_JSON_MEMPOOL_ELEMENT_COUNT](https://manual.altibase.com/8.1/ref/general/2.-Altibase-Properties/Replication-Properties/#replication_json_mempool_element_count) 

      - Description: Specifies the number of mempool elements (each element size: 64 KB) used for JSON-to-CLOB conversion during replication of tables containing JSON columns through Log Analyzer.

        This property should be configured by considering the trade-off between memory usage and system call overhead. A smaller value reduces memory waste but may increase system call overhead when processing large data. A larger value reduces system call overhead but increases memory usage.

      -   Default Value: 1
      -   Range: 1~2<sup>10</sup>

  - Compile Option

  - Error Code

### BUG-52215<a name=bug-52215></a> Added abm.log Path Configuration Feature

- **module** : ux-abm

- **Category** : Functionality

- **Reproducibility** : Always

- **Description** : Added the `-log_path` option to specify the directory where the `abm.log` file is created. If `-log_path` is not specified, the `abm.log` file is created in the current working directory where abm is executed.

  Additionally, the `abm.properties` file has been added, and the `LOG_PATH` property in this file can also be used to specify the log file path.

### BUG-52233<a name=bug-52233></a> Added gzip Compression Level Configuration in abm

-   **module** : ux-abm
-   **Category** : Functionality
-   **Reproducibility** : Always
-   **Description** : Users can now configure the gzip compression level in abm. A `GZIP_COMP_LEVEL` property has been added to `abm.properties` for this purpose. The default value is `6`.

### BUG-52224<a name=bug-52224></a> Added Log Messages for Replication Give-up Events

- **module** : rp-sender
- **Category** : Enhancement
- **Reproducibility** : Always
- **Description** : When `REPLICATION_MAX_LOGFILE` is set to 1 or higher, the following log messages have been added to help identify Give-up events and subsequent Sender restarts:
- Give-up start: **[Manager] Replication {replication_name} Sender Give-up Start.**
  - Give-up end: **[Manager] Replication {replication_name} Sender Give-up End.**
- Sender restart after Give-up: **[Manager] Replication {replication_name} Restarts Sender After Give-up.**

Fixed Bugs
==========

### BUG-48937<a name=bug-48937></a> Fixed a failure in deleting backup files when user-created directories exist in the incremental backup directory

-   **module** : sm

-   **Category** : Message Error

-   **Reproducibility** : Always

- **Description** : Fixed an issue where the statement `ALTER DATABASE DELETE OBSOLETE BACKUP FILES;` failed with `[ERR-41082: Internal server error]` if the incremental backup directory contained user-created subdirectories. Now, the statement executes successfully even if user-created directories exist; those directories are preserved.

  Additionally, information about directories that could not be deleted is recorded in the `altibase_sm.log` file under the `trc` directory.

  - Example log message in `altibase_sm.log`:

    ```bash
    [BackupInfoMgr] Unable to delete <backup_path> (errno=39)
    ```

### BUG-51201<a name=bug-51201></a> Fixed an issue where XLog application order could be reversed depending on partition order if replication target partitions are not divided by PK.

-   **module** : rp-jdbcAdapter
-   **Category** : Functional Error
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where XLogs could be applied in reverse order in the adapter. This could occur when the replication target partitions of the Active server were not partitioned by Primary Key (PK), depending on the partition order.

### BUG-51324<a name=bug-51324></a> Fixed performance degradation when collecting disk index statistics in parallel.

-   **module** : sm
-   **Category** : Other
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where more time was consumed when collecting disk index statistics in parallel.

### BUG-51953<a name=bug-51953></a> Improved behavior to stop the replication receiver if memory tablespace resources are insufficient

- **module** : rp

- **Category** : Enhancement

- **Reproducibility** : Always

- **Description** : When the replication fails due to insufficient memory tablespace resources, the behavior has been changed.

  Previously, such errors were treated as conflicts. After the fix, the replication receiver is stopped instead.

  This applies to the following cases:

  - Auto-extension of the memory tablespace is disabled (smERR_ABORT_UNABLE_TO_EXTEND_CHUNK_WHEN_AUTO_EXTEND_OFF)
  - The memory tablespace size exceeds MEM_MAX_TBS_SIZE (smERR_ABORT_UNABLE_TO_EXTEND_CHUNK_MORE_THAN_MEM_MAX_DB_SIZE)
  - The memory tablespace exceeds its maximum size (smERR_ABORT_UNABLE_TO_EXTEND_CHUNK_MORE_THAN_TBS_MAXSIZE )

### BUG-52106<a name=bug-52106></a> Fixed missing server error messages during incremental backup in abm

-   **module** : ux-abm
-   **Category** : Functionality
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where server error messages were not displayed during incremental backup execution.

### BUG-52122<a name=bug-52122></a> Fixed incorrect error message when Change Tracking is disabled in abm

-   **module** : ux-abm
-   **Category** : Functional Error
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where incorrect error messages were displayed when Change Tracking was disabled.

### BUG-52119<a name=bug-52119></a> Fixed UPDATE Failure During Replication Through jdbcAdapter with SUPPLEMENTAL LOG Enabled

-   **module** : rp-jdbcAdapter
-   **Category** : Functional Error
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where UPDATE statements could fail while applying replication changes to target tables through jdbcAdapter when SUPPLEMENTAL LOG was enabled.

### BUG-52140<a name=bug-52140></a> Fixed Core Dump When View DDL Exceeds 100 Bytes in `VIEW_FORCE=ON` Environment

-   **module** : ux-aexport
-   **Category** : Functional Error
-   **Reproducibility** : Unknown
-   **Description** : Fixed an issue where a core file could be generated and the export process could terminate during aexport execution when the View DDL exceeded 100 bytes in a `VIEW_FORCE=ON` environment.

### BUG-52152<a name=bug-52152></a> Fixed Malformed Query Output in Logs When Error Occurs During UPDATE/DELETE in adapter

-   **module** : rp-jdbcAdapter
-   **Category** : Enhancement
-   **Reproducibility** : Always
-   **Description** : When the `ADAPTER_XLOG_WRITE_TYPE` property was set to `1` and an error occurred during UPDATE/DELETE execution, whitespace in the SQL recorded to the log file was incorrectly handled, making the SQL unusable as-is. The following issues have been fixed:
    - Missing whitespace before `AND` when the WHERE clause contains two or more PK conditions
    - Unnecessary whitespace added after `NULL` values

### BUG-52163<a name=bug-52163></a> Fixed EMPTY_CLOB() Handling Error for Temporary LOB in CLI Environment

-   **module** : qp-select-execute
-   **Category** : Functional Error
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where an error could occur while processing `EMPTY_CLOB()` for Temporary LOB in a CLI environment.

### BUG-52168<a name=bug-52168></a> Fixed performance issue for disk table DML after expanding BUFFER AREA SIZE

-   **module** : sm
-   **Category** : Functional Error
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where DML performance on disk tables did not improve after expanding the DISK BUFFER AREA SIZE during service.

### BUG-52171<a name=bug-52171></a> Fixed a server crash when renaming a table that has a trigger using SQL functions.

-   **module** : qp-psm-trigger-execute

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where the server could crash when renaming a table that has a trigger using SQL functions.
    
- **How to reproduce this bug**

  - ****Reproduction conditions****

    ```sql
    create table t1 (c1 integer);
    create or replace trigger trig_on_t1
    before insert on t1
    referencing new as new_row
    for each row
    as
    var1 varchar(10);
    begin
      var1 := nvl('a', 'a');
    end;
    /
    rename t1 to tx;
    ```

  -   **Actual Results**

          [ERR-91015 : Communication failure.]

  -   **Expected Results**

          Rename success.

-   **Workaround**

        Drop the trigger, rename the table, and then recreate the trigger.

### BUG-52181<a name=bug-52181></a> Fixed an issue where Give-up could fail during data replication in a REPLICATION_MAX_LOGFILE configuration

-   **module** : rp-sender
-   **Category** : Functional Error
-   **Reproducibility** : Frequence
-   **Description** : Fixed an issue where Give-up could fail when replication is in progress and records are being applied to the standby server in an environment where the `REPLICATION_MAX_LOGFILE` property is set to 1 or higher.

### BUG-52188<a name=bug-52188></a> Improved stability of diagnostic dump information collection during abnormal termination

-   **module** : mm

-   **Category** : Reliability

-   **Reproducibility** : Rare

-   **Description** : Fixed an issue where session and task diagnostic information could be missing under certain conditions during abnormal termination. Additionally, the diagnostic dump was enhanced to include communication read buffer data and the service thread's Statement ID information to aid failure analysis.

### BUG-52189<a name=bug-52189></a> Fixed Error When Using EMPTY_CLOB() in JSON Functions

-   **module** : qp-dml-execute

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where an error could occur when using `EMPTY_CLOB()` in JSON functions.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    DROP TABLE BUG_XXXXX;
    CREATE TABLE BUG_XXXXX(C1 INTEGER, C2 CLOB);
    INSERT INTO BUG_XXXXX VALUES ( 1, 1 );
    INSERT INTO BUG_XXXXX VALUES ( 2, '' );
    INSERT INTO BUG_XXXXX VALUES ( 3, NULL );
    INSERT INTO BUG_XXXXX VALUES ( 4, EMPTY_CLOB() );
    SELECT JSON_ARRAY( C2 RETURNING CLOB ) FROM BUG_XXXXX;
    ```

  - **Actual Results**

    ```sql
    JSON_ARRAY(C2RETURNINGCLOB)
    -----------------------------------------------------------------------------------
    ["1"]
    [null]
    [null]
    [ERR-110D0 : The lob size is bigger than the maximum lob size]
    3 rows selected.
    ```

  -   **Expected Results**

      ```sql
      JSON_ARRAY(C2RETURNINGCLOB)
      -----------------------------------------------------------------------------------
      ["1"]
      [null]
      [null]
      [""]
      4 rows selected.
      ```

-   **Workaround**

        NONE

### BUG-52190<a name=bug-52190></a> Fix for Abnormal Lock Release Depending on SELECT Execution Order in Non-AutoCommit Mode

-   **module** : sm
-   **Category** : Fatal
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where IS_LOCK was released abnormally depending on the execution order of SELECT statements within a single transaction in Non-AutoCommit mode.

### BUG-52192<a name=bug-52192></a> Improved error messages when system call fails during file backup.

-   **module** : sm
-   **Category** : Enhancement
-   **Reproducibility** : Always
-   **Description** : Previously, when a system call failed during file backup, detailed information was not sufficiently recorded in the log, making it difficult to determine the exact cause. It has been improved to output more detailed error messages, including information about the failed system call.

### BUG-52213<a name=bug-52213></a> Improvement to Prevent Incorrect Accumulated Time in Statistics

-   **module** : id
-   **Category** : Enhancement
-   **Reproducibility** : Unknown
-   **Description** : Improved to prevent incorrect accumulated time from being recorded in statistics.

### BUG-52219<a name=bug-52219></a> Fixed incorrect variable column padding when generating Supplemental Logs

-   **module** : sm
-   **Category** : Functional Error
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where `UPDATE` statements failed due to incorrect handling of variable column padding during the generation of Supplemental Logs.

### BUG-52220<a name=bug-52220></a> Fixed server crash when executing DROP COLUMN on replicated disk tables with LOB and Supplemental Log

-   **module** : sm
-   **Category** : Fatal
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where the server could crash when executing a DROP COLUMN statement on a disk table containing LOB columns and Supplemental Log, when the table is included in replication.

### BUG-52226<a name=bug-52226></a> Fixed standby server crash during DELETE log processing in SQL_APPLY mode

-   **module** : rp-receiver
-   **Category** : Fatal
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where the standby server could crash during DELETE log processing when operating in SQL_APPLY mode in a replication environment with Supplemental Log enabled on the table.

### BUG-52229<a name=bug-52229></a> Fixed [ERR-314B8 : Failed to seek a Session Temporary LOB.] error during Temporary LOB concat pperation

-   **module** : qp-select-pvo
-   **Category** : Functional Error
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where an error could occur during concat (`||`) operations on Temporary LOB.

### BUG-52230<a name=bug-52230></a> Fixed [ERR-31015 : The meta table crashed.] error when SYS revokes Role privileges granted by another user

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

    ```sql
    [ERR-31015 : The meta table crashed.
    0001 : revoke delete, insert, select, update on userA.T1 from R_userA
    ^ ^
    ]                                                    ^        ^]
    ```

  - **Expected Results**

    ```
    Revoke success.
    ```

-   **Workaround**

        Grant and revoke privileges using the SYS user.

### BUG-52236<a name=bug-52236></a> Fixed ASSERT failure when handling bind-less requests from older client

-   **module** : qp
-   **Category** : Assert
-   **Reproducibility** : Always
-   **Description** : Resolved a server abnormal termination (ASSERT) that occurred when a v7.3 server processed a request without bind values from a v6.1.1 client. The server now handles these protocols correctly.

### BUG-52261<a name=bug-52261></a> Fixed timeout issue when concurrently executing UPDATE Statements with EMPTY_CLOB() or EMPTY_BLOB() in oraAdapter

-   **module** : rp-oraAdapter
-   **Category** : Testcase Fail
-   **Reproducibility** : Frequence
-   **Description** : Fixed an issue where a timeout could occur when concurrently executing UPDATE statements containing `EMPTY_CLOB()` or `EMPTY_BLOB()` in oraAdapter.

### BUG-52262<a name=bug-52262></a> Fixed abnormal server termination when an invalid protocol header is received during connection from an older client (6.1.1 or earlier).

-   **module** : cm
-   **Category** : Fatal
-   **Reproducibility** : Rare
-   **Description** : Fixed an issue where the server could terminate abnormally in certain situations when an invalid protocol header value was received during a connection from an older client (version 6.1.1 or earlier).

### BUG-52284<a name=bug-52284></a> Fixed DBMS_METADATA Failure in aexport When All Public Synonyms Are Removed

-   **module** :
-   **Category** : Functional Error
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where DBMS_METADATA-related operations could fail during aexport execution when all public synonyms had been removed.

Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 8.1.0.0.2        | 8.1.0                   | 10.1.1       | 7.1.9               | 7.4.9                        |

### Compatibility

#### Database binary version

The database binary version has not changed.

> The database binary version indicates the compatibility of database image files and log files. If this version needs to be patched to a different version, the database must be reorganized.

#### Meta Version

The meta version has not changed.

> If you want to roll back the patch after patching to a version with a changed meta version, see [Meta Downgrade](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_8.1/eng/Installation%20Guide.md#meta-downgrade).

#### CM protocol Version

The cm protocol version has not changed.

#### Replication protocol Version

The replication protocol version has not changed.

### Altibase Server Properties

No properties added/changed/deleted.

### Performance Views

No performance views added/changed/deleted.
