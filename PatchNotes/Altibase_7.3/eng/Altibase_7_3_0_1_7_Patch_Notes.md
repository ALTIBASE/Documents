Altibase 7.3.0.1.7 Patch Notes
================================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-52066 Added a feature to output queries executed just before an abnormal termination.](#bug-52066)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-52087 Fixed an error that could occur when using UNION ALL in a view where the ROW_NUMBER() function is used.](#bug-52087)
    - [BUG-52091 Fixed a concurrency issue that could occur during metadata processing in a replication environment.](#bug-52091)
    - [BUG-52111 Improved the help output of the `abm -h` command.](#bug-52111)
    - [BUG-52141 Fixed an issue where tablespace DDL extraction failed when the size exceeded 64KB.](#bug-52141)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [Compatibility](#compatibility)
    - [Properties](#properties)
    - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# New Features

### BUG-52066<a name=bug-52066></a> Added a feature to output queries executed just before an abnormal termination.

-   **module** : mm
-   **Category** : Other
-   **Reproducibility** : Rare
-   **Description** : Added a feature that outputs the queries executed immediately before a server crash from the signal handler.
     This feature can be enabled using the `__QUERY_BUCKET_FLAG` property, and the output queries can be found in the `dumptrc` or `altibase_error.log` file.                                

Fixed Bugs
==========

### BUG-52087<a name=bug-52087></a> Fixed an error that could occur when using UNION ALL in a view where the ROW_NUMBER() function is used.

-   **module** : qp
-   **Category** : Fatal
-   **Reproducibility** : Rare
-   **Description** : Fixed an issue where an error could occur under certain conditions when executing a query that includes `UNION ALL` in a view using the `ROW_NUMBER()` function.

### BUG-52091<a name=bug-52091></a> Fixed a concurrency issue that could occur during metadata processing in a replication environment.

-   **module** : rp
-   **Category** : Fatal
-   **Reproducibility** : Rare
-   **Description** : Fixed a concurrency issue that could occur during metadata processing in a replication environment.

### BUG-52111<a name=bug-52111></a> Improved the help output of the `abm -h` command.

-   **module** : ux-abm
-   **Category** : Other
-   **Reproducibility** : Always
-   **Description** : Improved the help output of the `abm -h` command by removing unnecessary content.

### BUG-52141<a name=bug-52141></a> Fixed an issue where tablespace DDL extraction failed when the size exceeded 64KB.

-   **module** : ux-aexport
-   **Category** : Functional Error
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where tablespace DDL extraction failed when the DDL size exceeded 64KB due to the VARCHAR size limitation of DBMS_METADATA package.

# Changes

### Version Info

| **Altibase Version** | **Database Binary Version** | **Meta Version** | **CM Protocol Version** | **Replication Protocol Version** |
| -------------------- | --------------------------- | ---------------- | ----------------------- | -------------------------------- |
| 7.3.0.1.7            | 7.3.0                       | 9.4.1            | 7.1.8                   | 7.4.9                            |

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
