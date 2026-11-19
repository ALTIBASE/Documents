Altibase 7.1.0.11.1 Patch Notes
===============================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-52383 Improved behavior according to the extent size setting of the temporary tablespace](#bug-52383)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-52533 Failure to rebuild replication metadata when the Table OID changes during DDL Sync](#bug-52533)
    - [BUG-52548 Fixed an issue where a NullPointerException occurred when calling CallableStatement name-based parameter APIs in the JDBC driver](#bug-52548)
    - [BUG-52553 Server shutdown when a commit fails during DDL execution](#bug-52553)
    - [BUG-52575 Sender shutdown when an invalid update log is read during replication](#bug-52575)
    - [BUG-52589 Fixed an issue where incorrect results are returned when using Disk Hash Temp Table in GROUP BY operations](#bug-52589)
    - [BUG-52617 Fixed an issue where UPDATE is performed on a read-only partition during FAST SIMPLE QUERY processing](#bug-52617)
    - [BUG-52620 Separate altiMon from the server package](#bug-52620)
    - [BUG-52629 Fixed an issue where SELECT FOR UPDATE returns incorrect results when filtering on a CLOB column of a partitioned table](#bug-52629)
    - [BUG-52639 Fixed an integer overflow in the LIMIT clause](#bug-52639)
    - [BUG-52644 Fixed an issue where ERR-31455 (Failed to work because an internal exception occurred from an OS) occurs when querying a partitioned table](#bug-52644)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [Compatibility](#compatibility)
    - [Altibase Server Properties](#altibase-server-properties)
    - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-52383<a name=bug-52383></a> Improved behavior according to the extent size setting of the temporary tablespace

-   **module** : sm-disk-resource
-   **Category** : Enhancement
-   **Reproducibility** : Always
-   **Description** : Improved the fetch behavior so that a full scan of a temporary table runs correctly even when the extent size of the temporary tablespace differs from that of the temporary table. Previously, a full scan fetched as many pages as the extent size of the temporary tablespace at a time. Now, it fetches up to 64 pages at a time.

Fixed Bugs
==========

### BUG-52533<a name=bug-52533></a> Failure to rebuild replication metadata when the Table OID changes during DDL Sync

-   **module** : rp
-   **Category** : Fatal
-   **Reproducibility** : Always
-   **Description** : Replication metadata was not rebuilt when the Table OID changed during DDL Sync, which could cause problems. This issue has been fixed so that replication metadata is rebuilt when the Table OID changes during DDL Sync.

### BUG-52548<a name=bug-52548></a> Fixed an issue where a NullPointerException occurred when calling CallableStatement name-based parameter APIs in the JDBC driver

-   **module** : mm-jdbc
-   **Category** : Functionality
-   **Reproducibility** : Always
- **Description** : The Altibase JDBC driver does not support name-based parameter binding in `CallableStatement`.

  Previously, calling a name-based parameter API resulted in a `NullPointerException`. This has been fixed so that the appropriate exception is thrown depending on the JDBC driver:

  * Altibase.jar: `SQLException(Unsupported feature)`
  * Altibase42.jar: `SQLFeatureNotSupportedException`

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

         `SQLException(Unsupported feature)` or `SQLFeatureNotSupportedException` occurs.

-   **Workaround** : Use an index-based API such as `sStmt.getCharacterStream(3)` instead of the name-based API.

### BUG-52553<a name=bug-52553></a> Server shutdown when a commit fails during DDL execution

-   **module** : qp-ddl-dcl-execute
-   **Category** : Fatal
-   **Reproducibility** : Always
-   **Description** : Fixed an issue that could cause the server to shut down abnormally if a commit failed during DDL execution.

### BUG-52575<a name=bug-52575></a> Sender shutdown when an invalid update log is read during replication

-   **module** : rp
-   **Category** : Fatal
-   **Reproducibility** : Impossible
-   **Description** : Fixed an issue in which the server could shut down abnormally with a FATAL error when an invalid update log was read during replication. The Sender now logs an error and shuts down when an invalid update log is detected.

    If an error like the following is recorded in `altibase_rp.log`, drop the replication and then recreate it.

    ```text
    ERR-11069(errno=62) Internal server error in the storage manager (... Column Count is 0(zero) ...)
    ```

### BUG-52589<a name=bug-52589></a> Fixed an issue where incorrect results are returned when using Disk Hash Temp Table in GROUP BY operations

-   **module** : sm-disk-resource
-   **Category** : Reliability
-   **Reproducibility** : Always
-   **Description** : Fixed an issue in which SQL queries could return incorrect results when using Disk Hash Temp Table during GROUP BY operations under certain conditions.

### BUG-52617<a name=bug-52617></a> Fixed an issue where UPDATE is performed on a read-only partition during FAST SIMPLE QUERY processing

-   **module** : qp-dml-execute
-   **Category** : Functional Error
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where an UPDATE was performed on a partition set to read-only during FAST SIMPLE QUERY processing when the `EXECUTOR_FAST_SIMPLE_QUERY` property was set to `2`.

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

### BUG-52620<a name=bug-52620></a> Separate altiMon from the server package

-   **module** : ux-altiMon
-   **Category** : Maintainability
-   **Reproducibility** : Always
-   **Description** : The altiMon binary has been separated from the server package and is no longer included in the package.

### BUG-52629<a name=bug-52629></a> Fixed an issue where SELECT FOR UPDATE returns incorrect results when filtering on a CLOB column of a partitioned table

-   **module** : qp-dml-pvo
-   **Category** : Enhancement
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where SELECT FOR UPDATE on a partitioned table returned rows whose CLOB column value was NULL even though the `IS NOT NULL` condition was specified on that column.

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
-   **Description** : Fixed an issue where an integer overflow occurred when a value exceeding the 32-bit integer range was specified in the LIMIT clause.

### BUG-52644<a name=bug-52644></a> Fixed an issue where ERR-31455 (Failed to work because an internal exception occurred from an OS) occurs when querying a partitioned table

-   **module** : qp-select-pvo
-   **Category** : Fatal
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where `ERR-31455` occurred when a query on a partitioned table specified both an INDEX hint on a local index and a FULL SCAN hint, together with ORDER BY and LIMIT clauses.

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

        ```sql
        [ERR-31455 : Failed to work because an internal exception occurred from an OS.[Contact Altibase's Support Center]]
        ```

    -   **Expected Results**

        The query returns its result normally without `ERR-31455`.

Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 7.1.0.11.1       | 6.5.1                   | 8.12.1       | 7.1.7               | 7.4.7                        |

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
