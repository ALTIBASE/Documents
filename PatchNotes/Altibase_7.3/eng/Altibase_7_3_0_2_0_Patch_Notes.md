Altibase 7.3.0.2.0 Patch Notes
==============================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-52233 Add GZIP_COMP_LEVEL property for gzip compression level configuration](#bug-52233)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-51905 Fixed replication issue for disk tables with LOB columns in adapter](#bug-51905)
    - [BUG-52106 Fixed missing server error messages during incremental backup in abm](#bug-52106)
    - [BUG-52122 Fixed incorrect error message when Change Tracking is disabled in abm](#bug-52122)
    - [BUG-52168 Fixed performance issue for disk table DML after expanding BUFFER AREA SIZE](#bug-52168)
    - [BUG-52220 Fixed server crash when executing DROP COLUMN on replicated disk tables with LOB and Supplemental Log](#bug-52220)
    - [BUG-52226 Fixed standby server crash during DELETE log processing in SQL_APPLY mode](#bug-52226)
    - [BUG-52236 Fixed ASSERT failure when handling bind-less requests from older client](#bug-52236)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [Compatibility](#compatibility)
    - [Properties](#properties)
    - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-52233<a name=bug-52233></a> Add GZIP_COMP_LEVEL property for gzip compression level configuration

-   **module** : ux-abm
-   **Category** : Functionality
-   **Reproducibility** : Always
-   **Description** : Added the `GZIP_COMP_LEVEL` property to `abm.properties` file for configuring the gzip compression level in abm (default: 6).

Fixed Bugs
==========

### BUG-51905<a name=bug-51905></a> Fixed replication issue for disk tables with LOB columns in adapter

-   **module** : rp-jdbcAdapter
-   **Category** : Functional Error
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where replication failed for disk tables containing LOB columns in the adapter.

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

### BUG-52168<a name=bug-52168></a> Fixed performance issue for disk table DML after expanding BUFFER AREA SIZE

- **module** : sm
- **Category** : Functional Error
- **Reproducibility** : Always
- **Description** : Fixed an issue where DML performance on disk tables did not improve after expanding the DISK BUFFER AREA SIZE during service.

### BUG-52220<a name=bug-52220></a> Fixed server crash when executing DROP COLUMN on replicated disk tables with LOB and Supplemental Log

- **module** : sm
- **Category** : Fatal
- **Reproducibility** : Always
- **Description** : Fixed an issue where the server could crash when executing a DROP COLUMN statement on a disk table containing LOB columns and Supplemental Log, when the table is included in replication.

### BUG-52226<a name=bug-52226></a> Fixed standby server crash during DELETE log processing in SQL_APPLY mode

- **module** : rp-receiver
- **Category** : Fatal
- **Reproducibility** : Always
- **Description** : Fixed an issue where the standby server could crash during DELETE log processing when operating in SQL_APPLY mode in a replication environment with Supplemental Log enabled on the table.

### BUG-52236<a name=bug-52236></a> Fixed ASSERT failure when handling bind-less requests from older client

- **module** : qp
- **Category** : Assert
- **Reproducibility** : Always
- **Description** : Resolved a server abnormal termination (ASSERT) that occurred when a v7.3 server processed a request without bind values from a v6.1.1 client. The server now handles these protocols correctly.

Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 7.3.0.2.0        | 7.3.0                   | 9.4.1        | 7.1.8               | 7.4.9                        |

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
