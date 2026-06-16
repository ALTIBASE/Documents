Altibase 7.1.0.10.9 Patch Notes
===============================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-52165 Enhanced Diagnostic Information for Abnormal Termination](#bug-52165)
    - [BUG-52321 Support for Debezium-Format Messages in the Altibase Source Connector](#bug-52321)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-52314 Added Diagnostic Messages to altibase_qp.log for ERR-010A3 During External Procedure Execution](#bug-52314)
    - [BUG-52316 Fixed Server Crash During Disconnect Audit Processing](#bug-52316)
    - [BUG-52320 Improved Handling of Deadlocks During Replication Table Sync](#bug-52320)
    - [BUG-52337 Improved client information logging in trc logs when ERR-4203, ERR-71018, or ERR-71019 occurs](#bug-52337)
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

### BUG-52314<a name=bug-52314></a> Added Diagnostic Messages to altibase_qp.log for ERR-010A3 During External Procedure Execution

- **module** : qp-select

- **Category** : Functional Error

- **Reproducibility** : Always

- **Description** : Added diagnostic messages to **altibase_qp.log** to facilitate root cause analysis when **ERR-010A3: Failed to start an agent process** occurs during External Procedure execution. Depending on the cause of the agent startup failure, one of the following messages is recorded:

  - **Failed to open agent path.** : The agent executable (**extprocAgent**) does not exist or lacks the execution permission.
  - **Failed to fork process.** : The attempt to fork the agent process failed.
  - **Invalid Agent Process.** : The agent process does not exist or is in an invalid state.

  On Linux systems, errno information is also recorded when a system call fails.

### BUG-52316<a name=bug-52316></a> Fixed Server Crash During Disconnect Audit Processing

-   **module** : mm
-   **Category** : Functional Error
-   **Reproducibility** : Rare
-   **Description** : Fixed an issue where the server could terminate abnormally during Disconnect Audit processing when the Session object was NULL.

### BUG-52320<a name=bug-52320></a> Improved Handling of Deadlocks During Replication Table Sync

-   **module** : rp
-   **Category** : Functional Error
-   **Reproducibility** : Rare
-   **Description** : Fixed an issue where a deadlock could occur when performing Sync on a replication target table while INSERT operations were in progress. Previously, Sync failed after waiting for the duration specified by `REPLICATION_SYNC_LOCK_TIMEOUT`. The behavior has been improved so that Sync fails immediately when the required Table IS Lock cannot be acquired.

### BUG-52337<a name=bug-52337></a> Improved client information logging in trc logs when ERR-4203, ERR-71018, or ERR-71019 occurs

-   **module** : mm

-   **Category** : Enhancement

-   **Reproducibility** : Always

-   **Description** : mproved the trc log output for cases where a client terminates abnormally, causing ERR-4203, ERR-71018, or ERR-71019. Previously, only the session ID and minimal connection information were recorded in the trc log. With this enhancement, when an abnormal client termination is detected, additional client information is logged, including the client address, client PID, package version, protocol version, client type, and application information (AppInfo), along with the session ID. This improvement makes troubleshooting and root cause analysis easier.

- **How to reproduce this bug**

  -   **Reproduction conditions**

          kill -9 client_pid

  - **Actual Results**

        [2026/05/06 09:02:35 C5120E6] [PID:84561] (Thread-139985260955392] [LWP-86862]
        ERR-4203(errno=11) The session has been disconnected by the client
        Session ID : 2941
        Client Info : IPC

  -   **Expected Results**

          [2026/05/06 09:02:35 C5120E6] [PID:84561] (Thread-139985260955392] [LWP-86862]
          ERR-4203(errno=11) The session has been disconnected by the client
          Session ID : 2
          Client Info : TCP 127.0.0.1:44621
          Client PID : 3511
          Client Package : 8.2.0.0.0
          Client Protocol : 7.1.9
          Client Type : CLI-64LE
          Client AppInfo :

Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 7.1.0.10.9       | 6.5.1                   | 8.12.1       | 7.1.7               | 7.4.7                        |

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

No properties added/changed/deleted.

### Performance Views

No performance views added/changed/deleted.
