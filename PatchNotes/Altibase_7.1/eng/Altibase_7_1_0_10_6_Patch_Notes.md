# Altibase 7.1.0.10.6 Patch Notes

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-51698 Support for Encrypting PASSWORD in dblink, AKU, and Adapter Configuration Files Using altiEncrypt](#bug-51698)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-51015 Fixed a result error that occurred when executing a query using a scalar subquery together with GROUP BY and ORDER BY under specific conditions using the GROUP_SORT hint.](#bug-51015)
    - [BUG-51834 Fixed an error where the `V$DISK_TEMP_STAT.TBS_ID` value was queried as 0](#bug-51834)
    - [BUG-51841 Fixed a deadlock-like waiting behavior occurring during the startup process of replication in JDBCAdapter environments where ALA_SENDER_REPLICATION_PORT is set.](#bug-51841)
    - [BUG-51849 Fixed a result error caused by an incorrectly applied CONSTANT FILTER in the INVERSE HASH plan of ANTI JOIN.](#bug-51849)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [Compatibility](#compatibility)
    - [Altibase Server Properties](#altibase-server-properties)
    - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-51698<a name=bug-51698></a> Support for Encrypting PASSWORD in dblink, AKU, and Adapter Configuration Files Using altiEncrypt

- **module**: rp
- **Category**: Functionality
- **Reproducibility** : Always
- **Description**: The password encryption tool **`altiEncrypt`** has been added.
  Using `altiEncrypt`, user can now encrypt the `PASSWORD` values in the **dblink**, **AKU**, and **Adapter** configuration (conf) files and set them securely.

- **How to reproduce this bug**
  -   **Reproduction conditions**

  -   **Actual Results**

  -   **Expected Results**

- **Workaround**

- **Changes**
  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

Fixed Bugs
==========

### BUG-51015<a name=bug-51015></a> Fixed a result error that occurred when executing a query using a scalar subquery together with GROUP BY and ORDER BY under specific conditions using the GROUP_SORT hint.

-   **module** : qp-dml-pvo
-   **Category** : Functional Error
-   **Reproducibility** : Always
-   **Description** : Fixed a result error that occurred when executing a query using a scalar subquery together with `GROUP BY` and `ORDER BY` under specific conditions using the `GROUP_SORT` hint. This bug only occurs when the following conditions are met:
    -   A scalar subquery is used in the target clause of the SELECT statement
    -   The scalar subquery's alias is used in the aggregate function or ORDER BY clause of the parent query
    -   The execution plan is specified as GROUP_SORT
-   **How to reproduce this bug**
    -   **Reproduction conditions**
    
    -   **Actual Results**
    
    -   **Expected Results**
-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-51834<a name=bug-51834></a> Fixed an error where the `V$DISK_TEMP_STAT.TBS_ID` value was queried as 0

-   **module** : sm

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an error where the **`V$DISK_TEMP_STAT.TBS_ID`** value was incorrectly queried as 0.

-   **How to reproduce this bug**
    -   **Reproduction conditions**
    
    -   **Actual Results**
    
    -   **Expected Results**
    
-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-51841<a name=bug-51841></a> Fixed a deadlock-like waiting behavior occurring during the startup process of replication in JDBCAdapter environments where ALA_SENDER_REPLICATION_PORT is set.

-   **module** : rp-ala

-   **Category** : Hang

-   **Reproducibility** : Frequence

-   **Description** : Fixed a deadlock-like waiting issue that occurred during the replication startup process in JDBCAdapter environments where ALA_SENDER_REPLICATION_PORT was set. Additionally, changed the property used to wait for an ACK during the replication handshake from REPLICATION_RECEIVE_TIMEOUT to REPLICATION_CONNECT_TIMEOUT.
    - Before: REPLICATION\_RECEIVE_TIMEOUT (default 7200 seconds)
    
    - After: REPLICATION\_CONNECT\_TIMEOUT (default 10 seconds)
    
-   **How to reproduce this bug**
    -   **Reproduction conditions**
    
    -   **Actual Results**
    
    -   **Expected Results**
    
-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-51849 Fixed a result error caused by an incorrectly applied CONSTANT FILTER in the INVERSE HASH plan of ANTI JOIN.

-   **module** : qp-dml-pvo

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where the CONSTANT FILTER was incorrectly applied during INVERSE HASH plan generation for ANTI JOIN, resulting in incorrect query results.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    drop table t1;
    drop table t2;
    create table t1(i1 integer , i2 integer);
    create index t1_i2_idx on t1(i2);
    create table t2(i1 integer, i2 integer);
    create index t2_i2_idx on t2(i2);
    insert into t1 select level, mod(level, 10)+1 from dual connect by level <= 100;
    insert into t1 values (999, 999);
    insert into t1 values (1000, null);
    insert into t2 select level, level+1 from dual connect by level <= 20;
    insert into t2 values (99, 99);
    insert into t2 values (100, null);
    drop table t3;
    create table t3 (i1 integer, i2 integer);
    SELECT * from (
    SELECT t1.*
      FROM t1
     WHERE 'N' = 'Y' AND NOT EXISTS (SELECT  /*+ INVERSE_JOIN */  1
                         FROM t2
                        WHERE t2.i1 = t1.i2)) X
    LEFT OUTER JOIN ( SELECT * FROM T3 ) Y ON X.i1 = Y.i1;
    ```

  - **Actual Results**

    ```
    102 rows selected.
    ```

  - **Expected Results**

    ```
    No rows selected.
    ```

- **Workaround**

  -   Use `/*+ NO_INVERSE_JOIN */` hint

- **Changes**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 7.1.0.10.6       | 6.5.1                   | 8.12.1       | 7.1.7               | 7.4.7                        |

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
