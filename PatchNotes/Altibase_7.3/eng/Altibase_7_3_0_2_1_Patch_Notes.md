# Altibase 7.3.0.2.1 Patch Notes

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-52165 Enhanced Diagnostic Information for Abnormal Termination](#bug-52165)
    - [BUG-52321 Support for Debezium-Format Messages in the Altibase Source Connector](#bug-52321)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-52244 Fixed an issue where unnecessary locks were acquired on the META TABLE during HARD PREPARE](#bug-52244)
    - [BUG-52257 Improved Last Query Logging for UTrans Timeout](#bug-52257)
    - [BUG-52261 Fixed Timeout Issue When Concurrently Executing UPDATE Statements Containing EMPTY_CLOB() or EMPTY_BLOB() in oraAdapter](#bug-52261)
    - [BUG-52262 Fixed abnormal server termination when an invalid protocol header is received during connection from an older client (6.1.1 or earlier).](#bug-52262)
    - [BUG-52284 Fixed DBMS_METADATA Failure in aexport When All Public Synonyms Are Removed](#bug-52284)
    - [BUG-52314 Added Diagnostic Messages to altibase_qp.log for ERR-010A3 During External Procedure Execution](#bug-52314)
    - [BUG-52316 Fixed Server Crash During Disconnect Audit Processing](#bug-52316)
    - [BUG-52318 Fixed Intermittent Replication Sync Failures During SSL Communication](#bug-52318)
    - [BUG-52320 Improved Handling of Deadlocks During Replication Table Sync](#bug-52320)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [Compatibility](#compatibility)
    - [Altibase Server Properties](#altibase-server-properties)
    - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-52165<a name=bug-52165></a> Enhanced Diagnostic Information for Abnormal Termination

-   **module** : id
-   **Category** : Enhancement
-   **Reproducibility** : Always
-   **Description** : Improved diagnostic information recorded in the trace log when the server terminates abnormally due to signals such as SIGSEGV. Statement timing information, cursor information, and transaction lock information are now included to facilitate root cause analysis.

### BUG-52321<a name=bug-52321></a> Support for Debezium-Format Messages in the Altibase Source Connector

-   **module** : rp-kafkaConnector
-   **Category** : Functionality
-   **Reproducibility** : Always
-   **Description** : Added a hidden property that allows the Altibase Source Connector to publish messages in Debezium format. The default format remains the existing Confluent JDBC Connector format, and no behavior changes occur unless the option is explicitly enabled.

Fixed Bugs
==========

### BUG-52244<a name=bug-52244></a> Fixed an issue where unnecessary locks were acquired on the META TABLE during HARD PREPARE

-   **module** : sm
-   **Category** : Functional Error
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where locks were unnecessarily acquired on META TABLEs during the HARD PREPARE process.

### BUG-52257<a name=bug-52257></a> Improved Last Query Logging for UTrans Timeout

-   **module** : mm
-   **Category** : Enhancement
-   **Reproducibility** : Rare
-   **Description** : Fixed an issue where the **Last Query** field could be logged as **"(null)"** when a statement had already been freed before a UTrans Timeout occurred. The last executed SQL statement is now recorded in the log when a Utrans Timeout occurs.

### BUG-52261<a name=bug-52261></a> Fixed Timeout Issue When Concurrently Executing UPDATE Statements Containing EMPTY_CLOB() or EMPTY_BLOB() in oraAdapter

-   **module** : rp-oraAdapter
-   **Category** : Testcase Fail
-   **Reproducibility** : Frequence
-   **Description** : Fixed an issue where timeout errors could occur when multiple UPDATE statements containing EMPTY_CLOB() or EMPTY_BLOB() were executed concurrently in oraAdapter.

### BUG-52262<a name=bug-52262></a> Fixed abnormal server termination when an invalid protocol header is received during connection from an older client (6.1.1 or earlier).

-   **module** : cm
-   **Category** : Fatal
-   **Reproducibility** : Rare
-   **Description** : Fixed an issue where the server could terminate abnormally in certain situations when an invalid protocol header value was received during a connection from an older client (version 6.1.1 or earlier).

### BUG-52284<a name=bug-52284></a> Fixed DBMS_METADATA Failure in aexport When All Public Synonyms Are Removed

-   **module** : ux-dbms_metadata
-   **Category** : Functional Error
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where DBMS_METADATA-related operations could fail during aexport execution when all public synonyms had been removed.

### BUG-52314<a name=bug-52314></a> Added Diagnostic Messages to altibase_qp.log for ERR-010A3 During External Procedure Execution

- **module** : qp-select

- **Category** : Functional Error

- **Reproducibility** : Always

-   **Description** : Added diagnostic messages to **altibase_qp.log** to facilitate root cause analysis when **ERR-010A3: Failed to start an agent process** occurs during External Procedure execution. Depending on the cause of the agent startup failure, one of the following messages is recorded:
    
    - **Failed to open agent path.** : The agent executable (**extprocAgent**) does not exist or lacks the execution permission.
    - **Failed to fork process.** : The attempt to fork the agent process failed.
    - **Invalid Agent Process.** : The agent process does not exist or is in an invalid state.
    
    On Linux systems, errno information is also recorded when a system call fails.

### BUG-52316<a name=bug-52316></a> Fixed Server Crash During Disconnect Audit Processing

-   **module** : mm
-   **Category** : Functional Error
-   **Reproducibility** : Rare
-   **Description** : Fixed an issue where the server could terminate abnormally during Disconnect Audit processing when the Session object was NULL.

### BUG-52318<a name=bug-52318></a> Fixed Intermittent Replication Sync Failures During SSL Communication

-   **module** : rp
-   **Category** : Functional Error
-   **Reproducibility** : Rare
-   **Description** : Fixed an issue where Replication Sync could intermittently fail due to transient communication errors in SSL environments.

### BUG-52320<a name=bug-52320></a> Improved Handling of Deadlocks During Replication Table Sync

-   **module** : rp
-   **Category** : Functional Error
-   **Reproducibility** : Rare
-   **Description** : Fixed an issue where a deadlock could occur when performing Sync on a replication target table while INSERT operations were in progress. Previously, Sync failed after waiting for the duration specified by `REPLICATION_SYNC_LOCK_TIMEOUT`. The behavior has been improved so that Sync fails immediately when the required Table IS Lock cannot be acquired.

Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 7.3.0.2.1        | 7.3.0                   | 9.4.1        | 7.1.8               | 7.4.9                        |

> You can check the module version change history in [Version_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.3/Altibase_7_3_Version_Histories.md).

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
