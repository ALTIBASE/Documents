Altibase 7.3.0.2.5 Patch Notes
==============================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Fixed Bugs](#fixed-bugs)
  - [BUG-52533 Failure to rebuild replication metadata when the Table OID changes during DDL Sync](#bug-52533)
  - [BUG-52553 Server shutdown when a commit fails during DDL execution](#bug-52553)
  - [BUG-52560 Server shutdown when a commit fails during DDL execution](#bug-52560)
  - [BUG-52573 Remove the "-lightmode" option from the iLoader help](#bug-52573)
  - [BUG-52575 Sender shutdown when an invalid update log is read during replication](#bug-52575)
  - [BUG-52589 Fixed an issue where incorrect results are returned when using Disk Hash Temp Table in GROUP BY operations](#bug-52589)
  - [BUG-52603 Fixed security vulnerability KVE-2026-2355 (Stack Buffer Overflow in Replication Receive Processing](#bug-52603)
  - [BUG-52620 Separate altiMon from the server package](#bug-52620)
  - [BUG-52621 Server shutdown due to an invalid Table OID reference when restarting replication after DDL execution](#bug-52621)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [Compatibility](#compatibility)
  - [Altibase Server Properties](#altibase-server-properties)
  - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Fixed Bugs
==========

Fixed Bugs
----------

### BUG-52533<a name=bug-52533></a> Failure to rebuild replication metadata when the Table OID changes during DDL Sync

-   **module** : rp
-   **Category** : Fatal
-   **Reproducibility** : Always
-   **description** : Replication metadata was not rebuilt when the Table OID changed during DDL Sync, which could cause problems. This issue has been fixed so that replication metadata is rebuilt when the Table OID changes during DDL Sync. A related error code has also been added.

### BUG-52553<a name=bug-52553></a> Server shutdown when a commit fails during DDL execution

-   **module** : qp-ddl-dcl-execute
-   **Category** : Fatal
-   **Reproducibility** : Always
-   **description** : Fixed an issue that could cause the server to shut down abnormally if a commit failed during DDL execution.

### BUG-52560<a name=bug-52560></a> Column order not preserved when creating a schema in the Altibase Source Connector for Kafka

-   **module** : rp-kafkaConnector
-   **Category** : Functional Error
-   **Reproducibility** : Always
-   **description** : Fixed an issue in which columns could be registered in a different order from the source table when creating a schema in the Altibase Source Connector for Kafka. Previously, primary key and non-primary key columns could appear in a different order. The schema is now created in the same column order as the source table.

### BUG-52573<a name=bug-52573></a> Remove the "-lightmode" option from the iLoader help

-   **module** : ux-iloader
-   **Category** : Usability
-   **Reproducibility** : Always
-   **description** : Removed the "-lightmode" option from the iLoader help.

### BUG-52575<a name=bug-52575></a> Sender shutdown when an invalid update log is read during replication

-   **module** : rp

-   **Category** : Fatal

-   **Reproducibility** : Impossible

-   **description** : Fixed an issue in which the server could shut down abnormally with a FATAL error when an invalid update log was read during replication. The Sender now logs an error and shuts down when an invalid update log is detected.
    
    ERR-11069(errno=62) Internal server error in the storage manager
    ([smiLogRec::analyzeColumnMVImageMemory] Column Count is 0(zero) at
    [LSN: 16818,50008944)])

### BUG-52589<a name=bug-52589></a> Fixed an issue where incorrect results are returned when using Disk Hash Temp Table in GROUP BY operations

-   **module** : sm-disk-resource
-   **Category** : Reliability
-   **Reproducibility** : Always
-   **description** : Fixed an issue in which SQL queries could return incorrect results when using Disk Hash Temp Table during GROUP BY operations under certain conditions.

### BUG-52603<a name=bug-52603></a> Fixed security vulnerability KVE-2026-2355 (Stack Buffer Overflow in Replication Receive Processing)

-   **module** : id
-   **Category** : Maintainability
-   **Reproducibility** : Always
-   **description** : Fixed security vulnerability KVE-2026-2355, which could cause a stack buffer overflow because the output buffer boundary was not checked when decompressing data in the replication receive processing path.

### BUG-52620<a name=bug-52620></a> Separate altiMon from the server package

-   **module** : ux-altiMon
-   **Category** : Maintainability
-   **Reproducibility** : Always
-   **description** : The altiMon binary has been separated from the server package and is no longer included in the package.

### BUG-52621<a name=bug-52621></a> Server shutdown due to an invalid Table OID reference when restarting replication after DDL execution

-   **module** : rp
-   **Category** : Fatal
-   **Reproducibility** : Unknown
-   **description** : Fixed an issue in which an invalid OID could be used to retrieve table information through an old replication item when replication was restarted after DDL execution, potentially causing the server to shut down abnormally.

Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 7.3.0.2.5        | 7.3.0                   | 9.4.1        | 7.1.8               | 7.4.9                        |

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
