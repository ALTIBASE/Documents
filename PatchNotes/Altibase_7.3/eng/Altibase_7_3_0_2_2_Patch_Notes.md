Altibase 7.3.0.2.2 Patch Notes
================================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Fixed Bugs](#fixed-bugs)
    - [BUG-51901 Fixed a HANG issue during replication of large LOB data with ALA REPLICATION SYNC](#bug-51901)
    - [BUG-52337 Enhanced client information logging in the trace log for ERR-4203, ERR-71018, and ERR-71019](#bug-52337)
    - [BUG-52345 Improved the trace log output for disk index build](#bug-52345)
    - [BUG-52360 Fixed incorrect query results when unnesting subqueries containing aggregate functions](#bug-52360)
    - [BUG-52378 Fixed an issue where the server would crash when using aggregate functions in a WITH clause under certain conditions](#bug-52378)
    - [BUG-52382 Improved error handling when free pages are exhausted in the temporary tablespace](#bug-52382)
    - [BUG-52395 Fixed INSERT Failures After Running GATHER_TABLE_STATS on a Standby Server in a Replication Environment with Partitioned Tables Using Global Indexes](#bug-52395)
    - [BUG-52397 Fixed a server crash caused by memory corruption when processing NCHAR and NVARCHAR data in UTF8 character set environment](#bug-52397)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Fixed Bugs
==========

### BUG-51901<a name=bug-51901></a> Fixed a HANG issue during replication of large LOB data with ALA REPLICATION SYNC

-   **module** : rp-jdbcAdapter
-   **Category** : Hang
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where a HANG could occur while replicating large LOB data using ALA REPLICATION SYNC.

### BUG-52337<a name=bug-52337></a> Enhanced client information logging in the trace log for ERR-4203, ERR-71018, and ERR-71019

-   **module** : mm

-   **Category** : Enhancement

-   **Reproducibility** : Always

- **Description** : Improved the trace log output when `ERR-4203`, `ERR-71018`, or `ERR-71019` occurs due to an unexpected client termination.

  Previously, only the session ID and minimal connection information were recorded in the trace log. Now, when an unexpected client termination is detected, additional client information is logged, including the client address, client PID, package version, protocol version, client type, and application information (AppInfo), along with the session ID. This enhancement makes troubleshooting and root cause analysis easier.

- **How to reproduce this bug**

  -   **Reproduction conditions**

          kill -9 client_pid

  - **Actual Results**

    ```bash
    [2026/05/06 09:02:35 C5120E6] [PID:84561] (Thread-139985260955392] [LWP-86862]
    ERR-4203(errno=11) The session has been disconnected by the client
    Session ID : 2941
    Client Info : IPC
    ```

  -   **Expected Results**

      ```bash
      [2026/05/06 09:02:35 C5120E6] [PID:84561] (Thread-139985260955392] [LWP-86862]
      ERR-4203(errno=11) The session has been disconnected by the client
      Session ID : 2
      Client Info : TCP 127.0.0.1:44621
      Client PID : 3511
      Client Package : 8.2.0.0.0
      Client Protocol : 7.1.9
      Client Type : CLI-64LE
      Client AppInfo :
      ```

### BUG-52345<a name=bug-52345></a> Improved the trace log output for disk index build

-   **module** : sm
-   **Category** : Other
-   **Reproducibility** : Always
-   **Description** : Updated the trace log (`altibase_sm.log`) output during the bottom-up disk index build as follows:
    -   Removed:
        -   NEW ALLOC PAGE CNT

        -   PREPARE NODE COUNT

    -   Added:
        - ALLOC PAGE COUNT (Total number of allocated pages)
    -   Changed"
        - REUSABLE PAGE COUNT → FREE PAGE COUNT (Number of reusable pages)

### BUG-52360<a name=bug-52360></a> Fixed incorrect query results when unnesting subqueries containing aggregate functions

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

### BUG-52382<a name=bug-52382></a> Improved error handling when free pages are exhausted in the temporary tablespace

-   **module** : sm-disk-resource
-   **Category** : Hang
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where a query could hang indefinitely instead of terminating when free pages in the temporary tablespace used internally by disk tables were exhausted.

### BUG-52395<a name=bug-52395></a> Fixed INSERT Failures After Running GATHER_TABLE_STATS on a Standby Server in a Replication Environment with Partitioned Tables Using Global Indexes

-   **module** : rp-receiver
-   **Category** : Functional Error
-   **Reproducibility** : Always
-   **Description** : In a replication environment with partitioned tables using Global Indexes, fixed an issue where INSERT failed after executing GATHER_TABLE_STATS on the standby server, causing replication to not proceed normally.

### BUG-52397<a name=bug-52397></a> Fixed a server crash caused by memory corruption when processing NCHAR and NVARCHAR data in UTF8 character set environment

-   **module** : qp-ddl-dcl-execute
-   **Category** : Fatal
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where the server could terminate unexpectedly due to memory corruption when processing `NCHAR` or `NVARCHAR` data in UTF8 character set environments.

Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 7.3.0.2.2        | 7.3.0                   | 9.4.1        | 7.1.8               | 7.4.9                        |

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
