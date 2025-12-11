# Altibase 7.3.0.1.3 Patch Notes

- [New Features](#new-features)
  - [BUG-51467 Improved logging in altibase_error.log on Abnormal server shutdown](#bug-51467)
  - [BUG-51698 Added a new utility, altiEncrypt, to encrypt passwords in dblink, aku, and Adapter](#bug-51698)
  - [BUG-51864 Altibase Connector for Kafka (Altibase Connector) provided](#bug-51864)
- [Fixed Bugs](#fixed-bugs)
  - [BUG-50945 "ERR-01003 : Unexpected end of string" error occurs when EMPTY_CLOB() is used as an argument within the SUBSTR function.](#bug-50945)
  - [BUG-50976 Incorrect value is entered when executing a MERGE INTO statement on a CLOB column.](#bug-50976)
  - [BUG-51015 Fixed a result error that occurred when executing a query using a scalar subquery along with GROUP BY and ORDER BY under specific conditions using the GROUP_SORT hint](#bug-51015)
  - [BUG-51540 Memory index AGING containing a VARIABLE column may fail.](#bug-51540)
  - [BUG-51804 Fixed an issue where unexpected behavior could occur if the server is forcibly terminated after creating a memory table containing a VARIABLE column (before the FLUSH stage).](#bug-51804)
  - [BUG-51834 Fixed an error where the `V$DISK_TEMP_STAT.TBS_ID` value was queried as 0](#bug-51834)
  - [BUG-51841 Fixed a deadlock-like waiting behavior occurring during the startup process of replication in JDBCAdapter environments where ALA_SENDER_REPLICATION_PORT is set.](#bug-51841)
  - [BUG-51849 Fixed a result error caused by an incorrectly applied CONSTANT FILTER in the INVERSE HASH plan of ANTI JOIN.](#bug-51849)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [Compatibility](#compatibility)
  - [Properties](#properties)
  - [Performance Views](#performance-views)

# New Features

### BUG-51467<a name=bug-51467></a> Improved logging in altibase_error.log on Abnormal server shutdown

- **module**: mm

- **Category**: Functionality

- **Reproducibility**: Always

- **Description**: Enhanced the logging behavior so that, in addition to the call stack, client information is also recorded in altibase_error.log when the server shuts down abnormally.

  The following client informations are recorded:

  - CliPkgVer: Client Version
  - CliProtoVer: Client Communication Protocol Version
  - CliType: Client Type
  - AppInfo: Application Information

- Examples - altibase_error.log

  ```bash
  Client information is additionally logged below the existing call stack information.
  BEGIN-DUMP Diagnostic Information ===============
      Statement: 00007F75D24A9808                  
      Session: 000000000A22F148                    
          CliPkgVer: 7.3.0.1.3                     
          CliProtoVer: 7.1.8                       
          CliType: CLI-64LE                        
          AppInfo: isql                                
      Task: 000000000A16EF00                       
      Link: 00007F74E0000990                       
          ConnType: 1                              
  END-DUMP Diagnostic Information =================
  ```

### BUG-51698<a name=bug-51698></a> Added a new utility, altiEncrypt, to encrypt passwords in dblink, aku, and Adapter

- **module**: rp
- **Category**: Functionality
- **Reproducibility**: Always
- **Description**: 
- The password encryption tool `altiEncrypt` has been added.
  Using `altiEncrypt`, user can now encrypt the `PASSWORD` values in the dblink, aku, and Adapter configuration (conf) files and set them securely.

### BUG-51864<a name=bug-51864></a> Altibase Connector for Kafka (Altibase Connector) provided

- **module**: rp-kafkaConnector
- **Category**: Other
- **Reproducibility**: Always
- **Description**: Altibase Connector for Kafka (Altibase Connector), compatible with the Confluent JDBC connector protocol, has been developed. The Altibase Connector enables replication of modified Altibase data to other databases, or replication of modified data from other databases to Altibase, via Kafka. The Altibase Connector consists of two types of connectors:
  - **Altibase Source Connector**: Streams modified Altibase data to Kafka for replication to other databases.
  - **Altibase Sink Connector**: Applies modified data from other databases, received via Kafka, to Altibase and other supported sink databases.

# Fixed Bugs

### BUG-50945<a name=bug-50945></a> [ERR-01003 : Unexpected end of string] error occurs when EMPTY_CLOB() is used as an argument within the SUBSTR function.

- **module**: mt-function

- **Category**: Functional Error

- **Reproducibility**: Always

- **Description**: Fixed the [ERR-01003 : Unexpected end of string] error that occurred when `EMPTY_CLOB()` was used as an argument within the `SUBSTR` function.

- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    SELECT substr( empty_clob(), 1, 1 ) FROM dual;
    ```

  - **Actual Results**

    ```sql
    [ERR-01003 : Unexpected end of string]
    ```

  - **Expected Results**

    ```sql
    iSQL> SELECT SUBSTR( EMPTY_CLOB(), 1, 1 ) FROM dual;
    SUBSTRB(EMPTY_CLOB(),1,1)
    -----------------------------
    1 row selected.
    ```

- **Workaround**

### BUG-50976<a name=bug-50976></a> Incorrect value is entered when executing a MERGE INTO statement on a CLOB column.

- **module**: qp-dml-pvo

- **Category**: Functionality

- **Reproducibility**: Always

- **Description**: Fixed an issue where an incorrect value was entered when executing a `MERGE INTO` statement on a CLOB column.

- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    drop table t1;
    drop table t2;
    create table t1( i1 clob, i2 clob );
    create table t2( i1 clob, i2 clob );
    insert into t1 values( '1', '1' );
    insert into t2 values( '1', '1' );
    insert into t2 values( '22', null);
    merge into t1 using t2 on (length(t1.i1) = length(t2.i1))
    when matched then
    update set t1.i2 = t1.i2 || t2.i2
    when not matched then
    insert (i1,i2) values (t2.i1, t2.i2);
    select i1 from t1;
    ```

  - **Actual Results**

    ```sql
    I1
    -----------------------------------------------------------------------------------
    1
    2 rows selected.
    ```

  - **Expected Results**

    ```sql
    I1
    -----------------------------------------------------------------------------------
    1
    22
    2 rows selected.
    ```

- **Workaround**

### BUG-51015<a name=bug-51015></a> Fixed a result error that occurred when executing a query using a scalar subquery along with GROUP BY and ORDER BY under specific conditions using the GROUP_SORT hint.

- **module**: qp-dml-pvo
- **Category**: Functional Error
- **Reproducibility**: Always
- **Description**: Fixed a result error that occurred when executing a query using a scalar subquery along with `GROUP BY` and `ORDER BY` under specific conditions using the `GROUP_SORT` hint. This bug only occurred when:
  - A scalar subquery was used in the target clause of the `SELECT` statement.
  - The alias of a scalar subquery was used in the aggregate functions and the `ORDER BY` clause of the outer query.
  - The execution plan was specified as `GROUP_SORT`.

### BUG-51540<a name=bug-51540></a> Memory index AGING containing a VARIABLE column may fail.

- **module**: sm
- **Category**: Functional Error
- **Reproducibility**: Always
- **Description**: Fixed the issue where memory index AGING failed when a memory index contained a `VARIABLE` column.

### BUG-51804<a name=bug-51804></a> Fixed an issue where unexpected behavior could occur if the server is forcefully terminated after creating a memory table containing a VARIABLE column (before the FLUSH stage)

- **module**: sm
- **Category**: Other
- **Reproducibility**: Always
- **Description**: Fixed an issue where unexpected behavior could occur if the server is forcefully terminated after creating a memory table with a `VARIABLE` column (before the FLUSH stage).

### BUG-51834<a name=bug-51834></a> Fixed an error where the `V$DISK_TEMP_STAT.TBS_ID` value was queried as 0

-   **module** : sm

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an error where the `V$DISK_TEMP_STAT.TBS_ID` value was incorrectly queried as 0.

### BUG-51841<a name=bug-51841></a> Fixed a deadlock-like waiting behavior occurring during the startup process of replication in JDBCAdapter environments where ALA_SENDER_REPLICATION_PORT is set.

-   **module** : rp-ala

-   **Category** : Hang

-   **Reproducibility** : Frequence

-   **Description** : Fixed a deadlock-like waiting issue that occurred during the replication startup process in JDBCAdapter environments where ALA_SENDER_REPLICATION_PORT was set. Additionally, changed the property used to wait for an ACK during the replication handshake from REPLICATION_RECEIVE_TIMEOUT to REPLICATION_CONNECT_TIMEOUT.
    - Before: REPLICATION\_RECEIVE_TIMEOUT (default 7200 seconds)

    - After: REPLICATION\_CONNECT\_TIMEOUT (default 10 seconds)

### BUG-51849 Fixed a result error caused by an incorrectly applied CONSTANT FILTER in the INVERSE HASH plan of ANTI JOIN.

- **module** : qp-dml-pvo

- **Category** : Functional Error

- **Reproducibility** : Always

- **Description** : Fixed an issue where the CONSTANT FILTER was incorrectly applied during INVERSE HASH plan generation for ANTI JOIN, resulting in incorrect query results.

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

# Changes

### Version Info

| **Altibase Version** | **Database Binary Version** | **Meta Version** | **CM Protocol Version** | **Replication Protocol Version** |
| -------------------- | --------------------------- | ---------------- | ----------------------- | -------------------------------- |
| 7.3.0.1.3            | 7.3.0                       | 9.4.1            | 7.1.8                   | 7.4.9                            |

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

### Altibase Server Properties

No properties added/changed/deleted.

### Performance Views

No performance views added/changed/deleted.