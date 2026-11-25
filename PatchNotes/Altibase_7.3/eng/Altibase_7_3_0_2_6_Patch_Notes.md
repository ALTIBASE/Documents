Altibase 7.3.0.2.6 Patch Notes
==============================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-52383 Improved behavior according to the extent size setting of the temporary tablespace](#bug-52383)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-52436 Fixed an issue where the DML execution order could be reversed when using the Parallel Applier in the replication Receiver](#bug-52436)
    - [BUG-52548 Fixed an issue where a NullPointerException occurred when calling CallableStatement name-based parameter APIs in the JDBC driver](#bug-52548)
    - [BUG-52617 Fixed an issue where UPDATE is performed on a read-only partition during FAST SIMPLE QUERY processing](#bug-52617)
    - [BUG-52629 Fixed an issue where SELECT FOR UPDATE returns incorrect results when filtering on a CLOB column of a partitioned table](#bug-52629)
    - [BUG-52639 Fixed an integer overflow in the LIMIT clause](#bug-52639)
    - [BUG-52644 Fixed an issue where ERR-31455 (Failed to work because an internal exception occurred from an OS) occurs when querying a partitioned table](#bug-52644)
    - [BUG-52669 Removed the REPLICATION_SYNC_APPLY_METHOD property after removing the Direct-Path INSERT feature](#bug-52669)
    - [BUG-52675 Fixed an issue that could cause the server to shut down when replicating LOB data in SQL Apply mode](#bug-52675)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [Compatibility](#compatibility)
    - [Properties](#properties)
    - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-52383<a name=bug-52383></a> Improved behavior according to the extent size setting of the temporary tablespace

-   **module** : sm-disk-resource
-   **Category** : Enhancement
-   **Reproducibility** : Always
-   **description** : A full scan of a temporary table now works correctly even when the extent sizes of the temporary tablespace and the temporary table are different. Previously, the scan fetched data in chunks equal to the extent size of the temporary tablespace. It now fetches data in units of up to 64 pages.

Fixed Bugs
==========

### BUG-52436<a name=bug-52436></a> Fixed an issue where the DML execution order could be reversed when using the Parallel Applier in the replication Receiver

-   **module** : rp-receiver
-   **Category** : Testcase Fail
-   **Reproducibility** : Rare
-   **description** : Fixed an issue where the DML execution order could be reversed when Redo logs were recorded with Group Commit and the Parallel Applier was used in the replication Receiver.

### BUG-52548<a name=bug-52548></a> Fixed an issue where a NullPointerException occurred when calling CallableStatement name-based parameter APIs in the JDBC driver

-   **module** : mm-jdbc
-   **Category** : Functionality
-   **Reproducibility** : Always
-   **description** : The Altibase JDBC driver does not support name-based parameter binding for CallableStatement. Previously, calling a name-based parameter API caused a `NullPointerException`. It now throws a `SQLFeatureNotSupportedException`.

-   **How to reproduce this bug**

    -   **Reproduction conditions**

        ```java
        CallableStatement sStmt =
            conn.prepareCall("EXEC PROC1(:I1_IN, :I2_OUT, :I3_OUT)");
        sStmt.setInt(1, 1);
        sStmt.registerOutParameter(2, Types.VARCHAR);
        sStmt.registerOutParameter(3, Types.VARCHAR);
        sStmt.execute();
        sStmt.getCharacterStream("I3_OUT");
        ```
    -   **Actual Results**

        `java.lang.NullPointerException` occurs.

    -   **Expected Results**

        `SQLFeatureNotSupportedException` occurs.

-   **Workaround** : Use an index-based API such as `sStmt.getCharacterStream(3)` instead of the name-based API.
### BUG-52617<a name=bug-52617></a> Fixed an issue where UPDATE is performed on a read-only partition during FAST SIMPLE QUERY processing

-   **module** : qp-dml-execute
-   **Category** : Functional Error
-   **Reproducibility** : Always
-   **description** : Fixed an issue where UPDATE could be performed on a partition set to read-only during FAST SIMPLE QUERY processing when the `EXECUTOR_FAST_SIMPLE_QUERY` property was set to `2`.

-   **How to reproduce this bug**

    -   **Reproduction conditions**

        ```sql
        CREATE TABLE T0 ( ID INTEGER, K INTEGER )
        PARTITION BY RANGE ( ID )
        (
          PARTITION P1 VALUES LESS THAN (100),
          PARTITION P2 VALUES LESS THAN (200),
          PARTITION P9 VALUES DEFAULT
        );
        INSERT INTO T0(ID, K) SELECT LEVEL, LEVEL FROM DUAL CONNECT BY LEVEL <= 10;
        INSERT INTO T0(ID, K) SELECT LEVEL + 100, LEVEL + 100 FROM DUAL CONNECT BY LEVEL <= 10;
        COMMIT;
        ALTER TABLE T0 ACCESS PARTITION P1 READ APPEND;
        UPDATE T0 SET K = K + 1 WHERE 1 = 1;
        UPDATE T0 SET K = K + 1;
        ```
    -   **Actual Results**

        ```sql
        iSQL> UPDATE T0 SET K = K + 1 WHERE 1 = 1;
        [ERR-313D6 : Unable to update table or partition P1]
        iSQL> UPDATE T0 SET K = K + 1;
        20 rows updated.
        ```

    -   **Expected Results**

        ```sql
        iSQL> UPDATE T0 SET K = K + 1 WHERE 1 = 1;
        [ERR-313D6 : Unable to update table or partition P1]
        iSQL> UPDATE T0 SET K = K + 1;
        [ERR-313D6 : Unable to update table or partition P1]
        ```
### BUG-52629<a name=bug-52629></a> Fixed an issue where SELECT FOR UPDATE returns incorrect results when filtering on a CLOB column of a partitioned table

-   **module** : qp-dml-pvo
-   **Category** : Enhancement
-   **Reproducibility** : Always
-   **description** : Fixed an issue where SELECT FOR UPDATE with an `IS NOT NULL` condition on a CLOB column of a partitioned table also returned rows in which the column value was NULL.

-   **How to reproduce this bug**

    -   **Reproduction conditions**

        ```sql
        CREATE TABLE T0 ( ID INTEGER, C CLOB )
        PARTITION BY RANGE ( ID )
        (
          PARTITION P1 VALUES LESS THAN ( 10 ),
          PARTITION P2 VALUES DEFAULT
        ) TABLESPACE SYS_TBS_MEM_DATA;
        INSERT INTO T0 VALUES ( 1, 'x' );
        INSERT INTO T0 VALUES ( 2, NULL );
        INSERT INTO T0 VALUES ( 11, 'x' );
        INSERT INTO T0 VALUES ( 12, NULL );

        SELECT ID FROM T0 WHERE C IS NOT NULL ORDER BY ID;
        SELECT ID FROM T0 WHERE C IS NOT NULL ORDER BY ID FOR UPDATE;
        ```
    -   **Actual Results**

        ```sql
        iSQL> SELECT ID FROM T0 WHERE C IS NOT NULL ORDER BY ID;
        ID
        -------------
        1
        11
        2 rows selected.
        iSQL> SELECT ID FROM T0 WHERE C IS NOT NULL ORDER BY ID FOR UPDATE;
        ID
        -------------
        1
        2
        11
        12
        4 rows selected.
        ```

    -   **Expected Results**

        ```sql
        iSQL> SELECT ID FROM T0 WHERE C IS NOT NULL ORDER BY ID FOR UPDATE;
        ID
        -------------
        1
        11
        2 rows selected.
        ```
### BUG-52639<a name=bug-52639></a> Fixed an integer overflow in the LIMIT clause

-   **module** : qp-select-pvo
-   **Category** : Enhancement
-   **Reproducibility** : Always
-   **description** : Fixed an issue where an integer overflow occurred when a value outside the 32-bit integer range was specified in the LIMIT clause.

### BUG-52644<a name=bug-52644></a> Fixed an issue where ERR-31455 (Failed to work because an internal exception occurred from an OS) occurs when querying a partitioned table

-   **module** : qp-select-pvo
-   **Category** : Fatal
-   **Reproducibility** : Always
-   **description** : Fixed an issue where `ERR-31455` occurred when querying a partitioned table with both the INDEX hint for a local index and the FULL SCAN hint, together with ORDER BY and LIMIT clauses.

-   **How to reproduce this bug**

    -   **Reproduction conditions**

        ```sql
        CREATE TABLE T0 ( ID INTEGER, V INTEGER )
        PARTITION BY RANGE ( ID )
        (
          PARTITION P1 VALUES LESS THAN ( 100 ),
          PARTITION P2 VALUES DEFAULT
        ) TABLESPACE SYS_TBS_MEM_DATA;
        INSERT INTO T0 SELECT LEVEL, LEVEL FROM DUAL CONNECT BY LEVEL <= 300;
        CREATE INDEX IDX0 ON T0 ( V ) LOCAL ( PARTITION IDX0_P1 ON P1, PARTITION IDX0_P2 ON P2 );

        SELECT /*+ INDEX(T0, IDX0) FULL SCAN(T0) */ V FROM T0 ORDER BY V LIMIT 1;
        ```
    -   **Actual Results**

        ```text
        [ERR-31455 : Failed to work because an internal exception occurred from an OS.[Contact Altibase's Support Center]]
        ```

    -   **Expected Results**

        The query returns its result normally without `ERR-31455`.
### BUG-52669<a name=bug-52669></a> Removed the REPLICATION_SYNC_APPLY_METHOD property after removing the Direct-Path INSERT feature

-   **module** : rp-receiver
-   **Category** : Functionality
-   **Reproducibility** : Unknown
-   **description** : Direct-Path INSERT has been removed, so we have removed the REPLICATION_SYNC_APPLY_METHOD property associated with that feature.

### BUG-52675<a name=bug-52675></a> Fixed an issue that could cause the server to shut down when replicating LOB data in SQL Apply mode

-   **module** : rp
-   **Category** : Fatal
-   **Reproducibility** : Always
-   **description** : Fixed an issue that could cause the server to shut down when a LOB data change was sent from the sender during replication in SQL Apply mode, but the corresponding LOB column had not yet been created in the table on the receiver.

Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 7.3.0.2.6        | 7.3.0                   | 9.4.1        | 7.1.8               | 7.4.9                        |

> You can check the module version change history in [Version_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.3/Altibase_7_3_Version_Histories.md).

### Compatibility

#### Database binary version

The database binary version has not changed.

> The database binary version indicates the compatibility of database image files and log files. If this version is different, the database must be reorganized when patching or upgrading.

#### Meta Version

The meta version has not changed.

> If you want to roll back the patch, see [Meta Downgrade](https://manual.altibase.com/7.3/en/start-here/install/3.-Uninstalling-Altibase-and-Meta-Downgrade/#meta-downgrade).

#### CM protocol Version

The communication protocol version has not changed.

#### Replication protocol Version

The replication protocol version has not changed.

### Properties

#### Deleted Properties

-   REPLICATION_SYNC_APPLY_METHOD

### Performance Views

No performance views were added, changed, or deleted.