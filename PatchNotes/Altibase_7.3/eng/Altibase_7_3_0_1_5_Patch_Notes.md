Altibase 7.3.0.1.5 Patch Notes
==============================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-51873 Altibase Connector for Kafka now supports automatic restart functionality.](#bug-51873)
    - [BUG-51888 The maximum allowed length for encrypted PASSWORD used in dblink, aku, and Adapter has been extended to 256 characters.](#bug-51888)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-50643 Fixed issue where last LOB column value becomes NULL during SYNC conflict.](#bug-50643)
    - [BUG-51977 Fixed an issue where SQLDriverConnectW() returns SQL_SUCCESS_WITH_INFO even when the connection fails.](#bug-51977)
    - [BUG-51989 Fixed an issue where some rows are not updated when performing Multiple Table Update on a disk table with indexes.](#bug-51989)
    - [BUG-51992 Improved to log diagnostic information in altibase_dump.log when Row TimeStamping fails.](#bug-51992)
    - [BUG-51994 Fixed a result error where some results were missing when executing nested Left Outer Join statements.](#bug-51994)
    - [BUG-52002 Fixed abnormal termination during record update processing when a conflict occurs during SYNC in SQL_APPLY mode.](#bug-52002)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [Compatibility](#compatibility)
    - [Properties](#properties)
    - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-51873<a name=bug-51873></a> Altibase Connector for Kafka now supports automatic restart functionality.

-   **module** :
-   **Category** : Functionality
-   **Reproducibility** : Always
-   **Description** : Altibase Source Connector for Kafka now supports automatic connector restart upon receiving a DDL message. To enable this feature, set the `restart.ddl` property to `true`. The default value is `false`.

### BUG-51888<a name=bug-51888></a> The maximum allowed length for encrypted PASSWORD used in dblink, aku, and Adapter has been extended to 256 characters.

-   **module** : rp
-   **Category** : Enhancement
-   **Reproducibility** : Always
-   **Description** : The maximum allowed length of the encrypted PASSWORD used in dblink, aku, and Adapter has been changed to 256 characters. Note that altiEncrypt supports password input of up to 128 characters in length, and generates an encrypted PASSWORD of up to 256 characters.

Fixed Bugs
==========

### BUG-50643<a name=bug-50643></a> Fixed issue where last LOB column value becomes NULL during SYNC conflict.

- **module** : rp

- **Category** : Functional Error

- **Reproducibility** : Always

- **Description** : Fixed an issue where the last LOB column value of the previously inserted record becomes NULL when a conflict occurs during SYNC on tables with LOB columns.

  This issue only occurred when the conflict happened on the second or subsequent records, not the first record.
   It no longer occurs after applying this patch.

### BUG-51977<a name=bug-51977></a> Fixed an issue where SQLDriverConnectW() returns SQL_SUCCESS_WITH_INFO even when the connection fails.

-   **module** : mm-cli
-   **Category** : Functional Error
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where `SQLDriverConnectW()` returned `SQL_SUCCESS_WITH_INFO` even when connection failed due to invalid IP address and small buffer size.

### BUG-51989<a name=bug-51989></a> Fixed an issue where some rows are not updated when performing Multiple Table Update on a disk table with indexes.

- **module** : sm\_index

- **Category** : Functional Error

- **Reproducibility** : Always

- **Description** : Fixed an issue where some rows were not updated when performing Multiple Table Update on a disk table that has indexes.

- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    drop table t1;
    drop table t2;
    create table t1 ( i1 varchar(40), i2 varchar(10), SBI_ORDER_ID varchar(10) ) tablespace sys_tbs_disk_data;
    create index idx1 on t1 ( SBI_ORDER_ID );
    create table t2 ( i1 varchar(40), SBI_ORDER_ID varchar(10) ) tablespace sys_tbs_disk_data;
    create index idx2 on t2 ( SBI_ORDER_ID );
    
    insert into t1 select level, 10, '6000000077' from dual connect by level < 3;
    insert into t2 select level, '6000000077' from dual connect by level < 3;
    
    update t1 a, t2 b set a.i1 = 'AA', b.i1 = 'BB' where A.SBI_ORDER_ID = B.SBI_ORDER_ID and a.SBI_ORDER_ID = '6000000077';
    ```

  - **Actual Results**

        3 rows updated.

  - **Expected Results**

        4 rows updated.

- **Workaround**

      NO INDEX

### BUG-51992<a name=bug-51992></a>Improved to log diagnostic information in altibase_dump.log when Row TimeStamping fails.

-   **module** : sm
-   **Category** : Fatal
-   **Reproducibility** : Unknown
-   **Description** : When Row Timestamping fails, diagnostic information for analysis is recorded in `altibase_dump.log`.

### BUG-51994<a name=bug-51994></a> Fixed a result error where some results were missing when executing nested Left Outer Join statements

- **module** : qp

- **Category** : Functional Error

- **Reproducibility** : Always

- **Description** : Fixed an issue where some results could be missing due to a Join predicate processing error when executing nested Left Outer Join statements.

- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    drop table t1;
    drop table t2;
    drop table t3;
    drop table t4;
    
    create table t1 (c1 integer primary key, c2 char(10), c3 char(10));
    create table t2 (c1 integer primary key, c2 char(10), c3 char(10));
    create table t3 (c1 integer primary key, c2 char(10), c3 char(10));
    create table t4 (c1 integer primary key, c2 char(10), c3 char(10));
    insert into t1 values (1,1,null);
    insert into t2 values (1,1,24);
    insert into t4 values (1,1,24);
    
    select t2.*, t3.*, t4.* from t1
              left outer join  t2 on t1.c1 = t2.c1
              left outer join  t3 on t1.c1 = t3.c1
              left outer join  t4 on
              (t4.c2=t3.c2 and t4.c3 = t3.c3)
              or
              (t4.c2=t2.c2 and t4.c3 = t2.c3)
              ;
    ```

  - **Actual Results**

    ```sql
    C1          C2          C3          C1          C2          C3
    -------------------------------------------------------------------------------
    C1          C2          C3
    ----------------------------------------
    1           1           24
    1 row selected.
    ```

  - **Expected Results**

    ```sql
    C1          C2          C3          C1          C2          C3
    -------------------------------------------------------------------------------
    C1          C2          C3
    ----------------------------------------
    1           1           24
    1           1           24
    1 row selected.
    ```

- **Workaround**

  None

### BUG-52002<a name=bug-52002></a> Fixed abnormal termination during record update processing when a conflict occurs during SYNC in SQL_APPLY mode.

-   **module** : rp
-   **Category** : Fatal
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where the server terminated abnormally when a record update occurred according to the conflict resolution policy during SYNC execution in SQL_APPLY mode when a conflict was detected.

# Changes

### Version Info

| **Altibase Version** | **Database Binary Version** | **Meta Version** | **CM Protocol Version** | **Replication Protocol Version** |
| -------------------- | --------------------------- | ---------------- | ----------------------- | -------------------------------- |
| 7.3.0.1.5            | 7.3.0                       | 9.4.1            | 7.1.8                   | 7.4.9                            |

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
