Altibase 7.1.0.11.0 Patch Notes
===============================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-52430 Added a feature to enable or disable Sender IP verification during the ALA handshake process](#bug-52430)
    - [BUG-52456 Removed the `-direct` option from iloader](#bug-52456)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-51901 Fixed a HANG issue during replication of large LOB data with ALA REPLICATION SYNC](#bug-51901)
    - [BUG-52360 Fixed incorrect query results when unnesting subqueries containing aggregate functions](#bug-52360)
    - [BUG-52378 Fixed an issue where the server would crash when using aggregate functions in a WITH clause under certain conditions](#bug-52378)
    - [BUG-52382 Improved error handling when free pages are exhausted in the temporary tablespace](#bug-52382)
    - [BUG-52384 Fixed an issue where trigger statement objects were not reused when repeatedly executing the same prepared statement with different bind values](#bug-52384)
    - [BUG-52395 Fixed INSERT failures after running GATHER_TABLE_STATS on a standby server in a replication environment with partitioned tables using global indexes](#bug-52395)
    - [BUG-52397 Fixed a server crash caused by memory corruption when processing NCHAR and NVARCHAR data in UTF8 character set environment](#bug-52397)
    - [BUG-52466 Fixed incorrect results during index access after recreating a primary key constraint on a temporary table in a volatile tablespace](#bug-52466)
    - [BUG-52484 Fixed a server crash that could occur while printing diagnostic information after receiving an invalid protocol header](#bug-52484)
    - [BUG-52499 Fixed an issue where using `audit` could cause the server to crash due to a memory error](#bug-52499)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [Compatibility](#compatibility)
    - [Altibase Server Properties](#altibase-server-properties)
    - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-52430<a name=bug-52430></a> Added a feature to enable or disable Sender IP verification during the ALA handshake process

-   **module** : rp-ala

-   **Category** : Functionality

-   **Reproducibility** : Always

-   **Description** : Added a feature that allows you to choose whether to verify the Sender IP during the ALA handshake process. The newly added `ALA_SetVerifySenderIP()` function can be used to enable or disable Sender IP verification. The default is Verify (`ALA_TRUE`).
    
    In addition, properties for configuring the same functionality have been added to oraAdapter and jdbcAdapter.
    
    - `ALA_VERIFY_SENDER_IP` (0: Do not verify, 1: Verify)

-   **Changes**

    -   Property
        -   ALA\_VERIFY\_SENDER\_IP (Adapter Properties)
            -   Value range: 0, 1
                -   1: (default) Verify
                -   0: Do not verify

### BUG-52456<a name=bug-52456></a> Removed the `-direct` option from iloader

-   **module** : ux-iloader
-   **Category** : Functionality
-   **Reproducibility** : Always
-   **Description** : The `-direct` option has been removed from `iloader`. This option is no longer available.

Fixed Bugs
==========

### BUG-51901<a name=bug-51901></a> Fixed a HANG issue during replication of large LOB data with ALA REPLICATION SYNC

-   **module** : rp-jdbcAdapter
-   **Category** : Hang
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where a HANG could occur while replicating large LOB data using ALA REPLICATION SYNC.

### BUG-52360<a name=bug-52360></a> Fixed incorrect query results when unnesting subqueries containing aggregate functions

-   **module** : qp-select-pvo

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where SQL queries could return incorrect results when unnesting a subquery containing aggregate functions if the subquery referenced two or more outer tables.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    DROP TABLE t1;
    DROP TABLE t2;
    
    CREATE TABLE T1 (
        ID          VARCHAR(16),
        C1  VARCHAR(16),
        C2        VARCHAR(14),
        C3        VARCHAR(20),
        C4    VARCHAR(20),
        C5    VARCHAR(100),
        C6          CHAR(1),
        C7    VARCHAR(10)
    );
    CREATE UNIQUE INDEX T1_PK
        ON T1 (
            ID ASC,
            C2 ASC
        );
    CREATE INDEX T1_IX01
        ON T1 (
            C3 ASC
        );
    CREATE INDEX T1_IX02
        ON T1 (
            C7 ASC
        );
    CREATE INDEX T1_IX03
        ON T1 (
            C2 ASC
        );
    
    CREATE TABLE T2 (
        C1  VARCHAR(16),
        C2        VARCHAR(14)
    );
    CREATE UNIQUE INDEX T2_PK
        ON T2 (
            C1 ASC,
            C2 ASC
        );
    CREATE INDEX T2_IX03
        ON T2 (
            C2 ASC
        );
    INSERT INTO T1 VALUES (
        'G1',
        'P_NEW',
        '20260527072107',
        'WA',
        'WC',
        'C1',
        'N',
        '1000062151'
    );
    INSERT INTO T1 VALUES (
        'G1',
        'P_OLD',
        '20260527072000',
        'WC',
        'WB',
        'C1',
        'N',
        '1000062150'
    );
    INSERT INTO T2 VALUES ('P_NEW', '20260527071728');
    INSERT INTO T2 VALUES ('P_OLD', '20260518065820');
    INSERT INTO T2 VALUES ('P_OLD', '20260518070054');
    INSERT INTO T2 VALUES ('P_OLD', '20260519020748');
    
    SELECT A.C7
      FROM T1 A
           JOIN T2 B
             ON A.C1 = B.C1
           JOIN T1 C
             ON A.ID = C.ID
            AND A.C4 = C.C3
           JOIN T2 D
             ON C.C1 = D.C1
            AND D.C2 = (SELECT MAX(C2)
                                FROM T2
                               WHERE C1 = C.C1
                                 AND C2 <= A.C2)
     WHERE A.C7 = '1000062151'
       AND A.C5 LIKE '%C1%'
       AND A.C6 = 'N';
    ```

  - **Actual Results**

    ```sql
    C7
    ----------------
    1000062151
    1000062151
    1000062151
    3 rows selected.
    ```

  -   **Expected Results**

      ```sql
      C7
      ----------------
      1000062151
      1 row selected.
      ```

-   **Workaround**

        use /*+ no_unnest */

### BUG-52378<a name=bug-52378></a> Fixed an issue where the server would crash when using aggregate functions in a WITH clause under certain conditions

-   **module** : qp-select-pvo
-   **Category** : Fatal
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where the server could terminate unexpectedly when executing SQL queries that use a `WITH` clause together with `UNION ALL`, `GROUP BY`, and multiple aggregate functions (for example, `MAX` and `COUNT`) under specific conditions.

### BUG-52382<a name=bug-52382></a> Improved error handling when free pages are exhausted in the temporary tablespace

-   **module** : sm-disk-resource
-   **Category** : Hang
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where a query could hang indefinitely instead of terminating when free pages in the temporary tablespace used internally by disk tables were exhausted.

### BUG-52384<a name=bug-52384></a> Fixed an issue where trigger statement objects were not reused when repeatedly executing the same prepared statement with different bind values

-   **module** : qp-psm-trigger-execute

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : When repeatedly executing the same Prepared Statement while changing only the bind values, trigger  Statement objects were not reused and new Statement objects were allocated for each execution. As a result, the number of Statement objects in the session could continue to increase, potentially causing the `There are too many statements in the session` error. After the fix, previously allocated trigger Statement objects are properly released, preventing unnecessary growth in the number of Statement objects during repeated execution.

### BUG-52395<a name=bug-52395></a> Fixed INSERT failures after running GATHER_TABLE_STATS on a standby server in a replication environment with partitioned tables using global indexes

-   **module** : rp-receiver
-   **Category** : Functional Error
-   **Reproducibility** : Always
-   **Description** : In a replication environment with partitioned tables using Global Indexes, fixed an issue where INSERT failed after executing GATHER_TABLE_STATS on the standby server, causing replication to not proceed normally.

### BUG-52397<a name=bug-52397></a> Fixed a server crash caused by memory corruption when processing NCHAR and NVARCHAR data in UTF8 character set environment

-   **module** : qp-ddl-dcl-execute
-   **Category** : Fatal
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where the server could terminate unexpectedly due to memory corruption when processing `NCHAR` or `NVARCHAR` data in UTF8 character set environments.

### BUG-52466<a name=bug-52466></a> Fixed incorrect results during index access after recreating a primary key constraint on a temporary table in a volatile tablespace

-   **module** : qp-dml-pvo

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an issue that could cause incorrect results during index access after recreating a Primary Key constraint on a Temporary Table in a Volatile Tablespace.

### BUG-52484<a name=bug-52484></a> Fixed a server crash that could occur while printing diagnostic information after receiving an invalid protocol header

-   **module** : mm
-   **Category** : Fatal
-   **Reproducibility** : Rare
-   **Description** : Fixed a server crash that could occur while printing diagnostic information after receiving an invalid protocol header. This issue could occur when a client version 6.1.1 or earlier sent an incorrect value instead of the A5 protocol header signature value (0x06). The server has been improved so that it no longer terminates abnormally when an invalid header is received.

### BUG-52499<a name=bug-52499></a> Fixed an issue where using `audit` could cause the server to crash due to a memory error

-   **module** : mm-statement
-   **Category** : Memory Error
-   **Reproducibility** : Rare
-   **Description** : In environments using `audit`, when executing a statement using the Direct Execute method, a memory error could occur during the statement cleanup process, potentially causing the server abnormal termination. This issue has been resolved.

Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 7.1.0.11.0       | 6.5.1                   | 8.12.1       | 7.1.7               | 7.4.7                        |

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

#### Added Properties

-   ALA\_VERIFY\_SENDER\_IP (ALA Properties)
    -   Value range: 0, 1
        -   1: (default) Verify
        -   0: Do not verify

#### Changed Properties

No properties changed.

#### Deleted Properties

No properties deleted.

### Performance Views

No performance views added/changed/deleted.
