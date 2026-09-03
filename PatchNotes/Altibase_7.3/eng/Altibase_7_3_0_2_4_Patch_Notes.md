Altibase 7.3.0.2.4 Patch Notes
================================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Fixed Bugs](#fixed-bugs)
  - [BUG-52444 Remove the `-lightmode` Option from iloader.](#bug-52444)
  - [BUG-52456 Remove the `-direct` Option from iloader.](#bug-52456)
  - [BUG-52499 Fixed an issue where using `audit` could cause the server to crash due to a memory error](#bug-52499)
  - [BUG-52502 Fixed an issue with Level 1 incremental backups failing.](#bug-52502)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [Compatibility](#compatibility)
  - [Altibase Server Properties](#altibase-server-properties)
  - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Fixed Bugs
==========

### BUG-52444<a name=bug-52444></a> Remove the `-lightmode` Option from iloader.

-   **module** : ux-iloader
-   **Category** : Functionality
-   **Reproducibility** : Always
-   **Description** : The `-lightmode` option has been removed from `iloader`. This option is no longer available.

### BUG-52456<a name=bug-52456></a> Remove the `-direct` Option from iloader.

-   **module** : ux-iloader
-   **Category** : Functionality
-   **Reproducibility** : Always
-   **Description** : The `-direct` option has been removed from `iloader`. This option is no longer available.

### BUG-52499<a name=bug-52499></a> Fixed an issue where using `audit` could cause the server to crash due to a memory error.

-   **module** : mm-statement
-   **Category** : Memory Error
-   **Reproducibility** : Rare
-   **Description** : In environments using `audit`, when executing a statement using the Direct Execute method, a memory error could occur during the statement cleanup process, potentially causing the server abnormal termination. This issue has been resolved.

### BUG-52502<a name=bug-52502></a> Fixed an issue with Level 1 incremental backups failing.

-   **module** : sm
-   **Category** : Fatal
-   **Reproducibility** : Always
-   **Description** : When a Level 1 incremental backup was performed while multiple sessions were concurrently modifying data, a concurrency issue during change tracking could cause an `ERR-42000` error and cause the backup to fail. This issue has been fixed so that Level 1 incremental backups can be performed successfully even when data modifications occur concurrently across multiple sessions.

Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 7.3.0.2.4        | 7.3.0                   | 9.4.1        | 7.1.8               | 7.4.9                        |

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
