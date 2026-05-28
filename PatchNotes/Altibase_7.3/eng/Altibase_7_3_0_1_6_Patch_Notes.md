Altibase 7.3.0.1.6 Patch Notes
==============================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-52085 Altibase Backup Manager](#bug-52085)
    - [BUG-52026 Enhance the output of diagnostic information for analysis when a “Malformed packet” error or a protocol header error occurs.](#bug-52026)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-49298 Fixed unnecessary log output during replication conflict (Not Support Data Type).](#bug-49298)
    - [BUG-51529 Fixed an intermittent communication error (Protocol header error) that occurred during adapter execution.](#bug-51529)
    - [BUG-51792 Fixed to not adjust the redo point when encountering a TBS Update log during Incomplete Recovery.](#bug-51792)
    - [BUG-52046 Fixed an issue where an error may occur during disk hash temp table insertion when a single record length is 2.5MB or more.](#bug-52046)
    - [BUG-52050 Fixed an issue where, when performing DDL Sync from two servers to a single remote server, an incorrect error message was returned upon failure of the second DDL statement.](#bug-52050)
    - [BUG-52083 Fixed an issue where, if the value of the REPLICATION_MAX_LOGFILE property was 1 or higher, all committed log files were deleted during a checkpoint, regardless of the number of log files.](#bug-52083)
    - [BUG-52086 Fixed an issue where ServiceThread may reference invalid memory in an IPC connection environment.](#bug-52086)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [Compatibility](#compatibility)
    - [Properties](#properties)
    - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-52085<a name=bug-52085></a> Altibase Backup Manager

-   **module** : ux-abm
-   **Category** : Functionality
-   **Reproducibility** : Always
-   **Description** : The abm utility is provided to efficiently perform backups and securely manage backup files. Through its intuitive interface, users can easily perform backup operations as well as file compression, encryption, and decryption. For more information, refer to the **[Utilities Manual - abm]((https://manual.altibase.com/7.3/en/tools/util/6.-abm/))**.

### BUG-52026<a name=bug-52026></a> Enhance the output of diagnostic information for analysis when a “Malformed packet” error or a protocol header error occurs.

- **module** : cm
- **Category** : Functionality
- **Reproducibility** : Unknown
- **Description** : Session information is now logged to aid analysis when a Protocol header error occurs. In addition, the Client PID is now included in the session information.

Fixed Bugs
==========

### BUG-49298<a name=bug-49298></a> Fixed unnecessary log output during replication conflict (Not Support Data Type)

- **module** : rp

- **Category** : Functional Error

- **Reproducibility** : Always

- **Description** : Fixed an issue where unnecessary logs were generated in `$ALTIBASE_HOME/trc/altibase_rp.log` during replication conflicts when columns of type BLOB, CLOB, GEOMETRY, or JSON exist.

  ```bash
  ERR-61069(errno=62) Internal server error in replication module (Not Support Data Type( id : 40 )).
  ```

  Also improved logging in `altibase_rp_conflict.log` to include the data type ID, e.g.:

  ```
  <None printable data( id : 30 )>
  ```

### BUG-51529<a name=bug-51529></a> Fixed an intermittent communication error (Protocol header error) that occurred during adapter execution.

-   **module** : rp-jdbcAdapter
-   **Category** : Functional Error
-   **Reproducibility** : Always
-   **Description** : Fixed an intermittent communication error (Protocol header error) that occurred during adapter execution.

### BUG-51792<a name=bug-51792></a> Fixed to not adjust the redo point when encountering a TBS Update log during Incomplete Recovery.

-   **module** : sm
-   **Category** : Fatal
-   **Reproducibility** : Always
-   **Description** : Fixed so that the Redo point is not adjusted when a TBS Update log is encountered during Incomplete Recovery.

### BUG-52046<a name=bug-52046></a> Fixed an issue where an error may occur during disk hash temp table insertion when a single record length is 2.5MB or more.

-   **module** : sm
-   **Category** : Functional Error
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where an error could occur during disk hash temp table insertion when a single record's length was 2.5MB or more.

### BUG-52050<a name=bug-52050></a> Fixed an issue where, when performing DDL Sync from two servers to a single remote server, an incorrect error message was returned upon failure of the second DDL statement.

-   **module** : rp
-   **Category** : Fatal
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where, when performing DDL Sync from two servers to a single remote server, an incorrect error message was returned upon failure of the second DDL statement.

### BUG-52083<a name=bug-52083></a> Fixed an issue where, if the value of the REPLICATION_MAX_LOGFILE property was 1 or higher, all committed log files were deleted during a checkpoint, regardless of the number of log files.

-   **module** : rp-sender
-   **Category** : Functional Error
-   **Reproducibility** : Always
-   **Description** : Fixed a behavior error related to the REPLICATION_MAX_LOGFILE property.

### BUG-52086<a name=bug-52086></a> Fixed an issue where ServiceThread may reference invalid memory in an IPC connection environment.

-   **module** : mm
-   **Category** : Memory Error
-   **Reproducibility** : Rare
-   **Description** : Fixed an issue where ServiceThread could reference invalid memory in an IPC connection environment..

# Changes

### Version Info

| **Altibase Version** | **Database Binary Version** | **Meta Version** | **CM Protocol Version** | **Replication Protocol Version** |
| -------------------- | --------------------------- | ---------------- | ----------------------- | -------------------------------- |
| 7.3.0.1.6            | 7.3.0                       | 9.4.1            | 7.1.8                   | 7.4.9                            |

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
