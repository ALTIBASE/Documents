# Altibase 7.1.0.8.3 Patch Notes

<br/>

<br>

# Table of Contents

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [New Features](#new-features)
    - [BUG-49600 Supports `Connection.createBlob()` and `createClob()` methods of the JDBC 4.0 API.](#bug-49600%C2%A0supports-connectioncreateblob-and-createclob-methods-of-the-jdbc-40-api)
    - [BUG-49985 Improved memory efficiency when using an empty group in the `GROUP BY GROUPING SETS` clause.](#bug-49985%C2%A0improved-memory-efficiency-when-using-an-empty-group-in-the-group-by-grouping-sets-clause)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-48074 In Windows environment, when load balancing is enabled, the server is not selected randomly.](#bug-48074%C2%A0in-windows-environment-when-load-balancing-is-enabled-the-server-is-not-selected-randomly)
    - [BUG-49732 Altibase server abnormally terminates when changing the tablespace of a table that has compressed columns and an index with compressed columns as keys.](#bug-49732%C2%A0altibase-server-abnormally-terminates-when-changing-the-tablespace-of-a-table-that-has-compressed-columns-and-an-index-with-compressed-columns-as-keys)
    - [BUG-50013 Adds a property to configure the format for outputting DML information in adapter logs (`jdbcAdapter.trc` or `oraAdapter.trc`).](#bug-50013%C2%A0adds-a-property-to-configure-the-format-for-outputting-dml-information-in-adapter-logs-jdbcadaptertrc-or-oraadaptertrc)
    - [BUG-50025 Fixes a bug where executing `STARTUP SERVICE` immediately after `CREATE DATABASE` could cause the Altibase server to terminate abnormally or result in an `ERR-11110: The index is inconsistent` error.](#bug-50025%C2%A0fixes-a-bug-where-executing-startup-service-immediately-after-create-database-could-cause-the-altibase-server-to-terminate-abnormally-or-result-in-an-err-11110-the-index-is-inconsistent-error)
    - [BUG-50033 When starting the adapter, a core file is generated if the ALA log file cannot be opened.](#bug-50033%C2%A0when-starting-the-adapter-a-core-file-is-generated-if-the-ala-log-file-cannot-be-opened)
    - [BUG-50057 An error occurs when using the `ROLLUP` function, aggregate functions, and the `ORDER BY` clause together.](#bug-50057%C2%A0an-error-occurs-when-using-the-rollup-function-aggregate-functions-and-the-order-by-clause-together)
    - [BUG-50058 Fixed a memory reference error where the replication receiver thread may not terminate when executing `DROP REPLICATION`.](#bug-50058%C2%A0fixed-a-memory-reference-error-where-the-replication-receiver-thread-may-not-terminate-when-executing-drop-replication)
    - [BUG-50059 Changes the behavior of `aku -p end`. Replication is stopped after performing the replication `FLUSH` command.](#bug-50059%C2%A0changes-the-behavior-of-aku--p-end-replication-is-stopped-after-performing-the-replication-flush-command)
    - [BUG-50061 Modifies the exception handling when using set operators in an updatable view.](#bug-50061%C2%A0modifies-the-exception-handling-when-using-set-operators-in-an-updatable-view)
    - [BUG-50071 An `ERR-31455` error may occur, or the Altibase server may terminate abnormally, if a subquery in the `SET` clause references multiple update targets.](#bug-50071%C2%A0an-err-31455-error-may-occur-or-the-altibase-server-may-terminate-abnormally-if-a-subquery-in-the-set-clause-references-multiple-update-targets)
    - [BUG-50082 Changes the behavior of `aku -p start` on a slave pod that terminated abnormally. The `FLUSH` command is executed after starting replication.](#bug-50082%C2%A0changes-the-behavior-of-aku--p-start-on-a-slave-pod-that-terminated-abnormally-the-flush-command-is-executed-after-starting-replication)
    - [BUG-50090 The following behavior of the `Statement` object returns `true` from `getMoreResults()` when the result is not a `ResultSet` object.](#bug-50090%C2%A0the-following-behavior-of-the-statement-object-returns-true-from-getmoreresults-when-the-result-is-not-a-resultset-object)
    - [BUG-50094 Changes the behavior of the `ADD COLUMN` operation for memory tables.](#bug-50094%C2%A0changes-the-behavior-of-the-add-column-operation-for-memory-tables)
    - [BUG-50096 After a DDL replication failure, the replication sender may not start due to abnormal behavior of the HeartBeat thread.](#bug-50096%C2%A0after-a-ddl-replication-failure-the-replication-sender-may-not-start-due-to-abnormal-behavior-of-the-heartbeat-thread)
    - [BUG-50106 In iSQL, after executing `SET PARTITIONS ON`, performing the `desc` command results in the error `ERR-31002: A single-row subquery has returned more than one row.`](#bug-50106%C2%A0in-isql-after-executing-set-partitions-on-performing-the-desc-command-results-in-the-error-err-31002-a-single-row-subquery-has-returned-more-than-one-row)
    - [BUG-50131 Adds exception handling for the issue where the Altibase server crashes during conditional checks.](#bug-50131%C2%A0adds-exception-handling-for-the-issue-where-the-altibase-server-crashes-during-conditional-checks)
    - [BUG-50076 Fixed the build failure issue on Linux 32-bit platforms in Altibase 7.1.0.7.3 and later versions.](#bug-50076%C2%A0fixed-the-build-failure-issue-on-linux-32-bit-platforms-in-altibase-71073-and-later-versions)
    - [BUG-49996 Fixed the issue where the error message "PCRE2 error:" is displayed.](#bug-49996%C2%A0fixed-the-issue-where-the-error-message-pcre2-error-is-displayed)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [Compatibility](#compatibility)
    - [Altibase Server Properties](#altibase-server-properties)
    - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-49600 Supports `Connection.createBlob()` and `createClob()` methods of the JDBC 4.0 API.

#### module

`mm-jdbc`

#### Category 

`Enhancement`

#### Reproducibility

``Always``

#### Description

Supports the `Connection.createBlob()` and `createClob()` methods of the JDBC 4.0 API. To use this features, you need to patch the JDBC driver (Altibase42.jar) that partially supports JDBC 4.2.

#### How to reproduce this bug

-   **Reproduction conditions**

    ~~~sql
    CREATE TABLE t1 (c1 int, c2 clob, c3 blob);
    ~~~

    ```java
    Connection sConn = getConnection("20300");
    sConn.setAutoCommit(false);
    Clob sClob = sConn.createClob();
    sClob.setString(1, "dsfjsdkfsdkfjds;fsdkfs");
    Blob sBlob = sConn.createBlob();
    sBlob.setBytes(1, "dfkjsdlkfjsdfkjsdkfljsdfsd".getBytes());
    PreparedStatement sStmt = sConn.prepareStatement("INSERT INTO t1 VALUES (?, ?, ?)");
    sStmt.setInt(1, 1);
    sStmt.setClob(2, sClob);
    sStmt.setBlob(3, sBlob);
    sStmt.executeUpdate();
    sConn.commit();
    ```

    ~~~sql
    SELECT c1,length(c2), binary_length(c3) FROM t1;
    ~~~

-   **Actual Results**

    ```java
    Exception in thread "main" java.sql.SQLFeatureNotSupportedException: 
    	at Altibase.jdbc.driver.ex.Error.createSQLFeatureNotSupportedException(Error.java:785)
    	at Altibase.jdbc.driver.AbstractConnection.createClob(AbstractConnection.java:34)
    	at GetLobTest.doTest(GetLobTest.java:15)
    	at GetLobTest.main(GetLobTest.java:8)
    ```

-   **Expected Results**

    ```sql
    C1          LENGTH(C2)           BINARY_LENGTH(C3)
    ----------------------------------------------------------
    1           22                   26
    1 row selected.
    ```



### BUG-49985 Improved memory efficiency when using an empty group in the `GROUP BY GROUPING SETS` clause.

#### module

`qp-select`

#### Category  

`Enhancement`

#### Reproducibility 

`Always`

#### Description  

Reduced memory allocation time and improved memory efficiency when using an empty group in the `GROUP BY GROUPING SETS` clause.


#### How to reproduce this bug

-   **Reproduction conditions**

        ALTER SESSION SET EXPLAIN PLAN = ON;
        CREATE TABLE T1 ( I1 INTEGER, I2 INTEGER );
        SELECT I1,SUM(I2)
          FROM T1
         GROUP BY GROUPING SETS ( I1, () );

-   **Actual Results**

        I1          SUM(I2)
        ------------------------------------
        No rows selected.
        ------------------------------------------------------------
        PROJECT ( COLUMN_COUNT: 2, TUPLE_SIZE: 16, COST: 388.69 )
         VIEW ( ACCESS: 0, COST: 386.03 )
          BAG-UNION
           PROJECT ( COLUMN_COUNT: 2, TUPLE_SIZE: 16, COST: 130.13 )
            GROUP-AGGREGATION ( ITEM_SIZE: 40, GROUP_COUNT: 0, BUCKET_COUNT: 1024, ACCESS: 0, COST: 130.06 )
             SCAN ( TABLE: SYS.T1, FULL SCAN, ACCESS: 0, COST: 116.76 )
           PROJECT ( COLUMN_COUNT: 2, TUPLE_SIZE: 16, COST: 135.34 )
            GROUP-AGGREGATION ( ITEM_SIZE: 32, GROUP_COUNT: 0, BUCKET_COUNT: 5120, ACCESS: 0, COST: 130.06 )
             SCAN ( TABLE: SYS.T1, FULL SCAN, ACCESS: 0, COST: 116.76 )
        ------------------------------------------------------------

-   **Expected Results**

        I1          SUM(I2)
        ------------------------------------
        No rows selected.
        ------------------------------------------------------------
        PROJECT ( COLUMN_COUNT: 2, TUPLE_SIZE: 16, COST: 260.21 )
         VIEW ( ACCESS: 1, COST: 260.19 )
          BAG-UNION
           PROJECT ( COLUMN_COUNT: 2, TUPLE_SIZE: 16, COST: 130.13 )
            GROUP-AGGREGATION ( ITEM_SIZE: 40, GROUP_COUNT: 0, BUCKET_COUNT: 1024, ACCESS: 0, COST: 130.06 )
             SCAN ( TABLE: SYS.T1, FULL SCAN, ACCESS: 0, COST: 116.76 )
           PROJECT ( COLUMN_COUNT: 2, TUPLE_SIZE: 16, COST: 130.06 )
            GROUP-AGGREGATION ( ITEM_SIZE: 32, GROUP_COUNT: 1, BUCKET_COUNT: 1, ACCESS: 1, COST: 130.06 )
             SCAN ( TABLE: SYS.T1, FULL SCAN, ACCESS: 0, COST: 116.76 )
        ------------------------------------------------------------



Fixed Bugs
==========

### BUG-48074 In Windows environment, when load balancing is enabled, the server is not selected randomly.

#### module

``mm-cli``

#### Category

``Functional Error``

#### Reproducibility

`Always`

#### Description

In a Windows environment, when load balancing is enabled, the server is not selected randomly.

#### How to reproduce this bug

-   **Reproduction conditions**

-   **Actual Results** 

-   **Expected Results**

#### Workaround

`N/A`

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-49732 Altibase server abnormally terminates when changing the tablespace of a table that has compressed columns and an index with compressed columns as keys.

#### module

``sm``

#### Category

``Fatal``

#### Reproducibility

`Always`

#### Description

Altibase server abnormally terminates when changing the tablespace of a table that has compressed columns and an index with compressed columns as keys. This bug occurs only in memory tables.

#### How to reproduce this bug

-   **Reproduction conditions**

        CREATE TABLE T1 ( I1 CHAR(10), I2 NUMBER(2) ) COMPRESS (I1);
        CREATE MEMORY TABLESPACE USER_MEM_TBS SIZE 1G AUTOEXTEND ON;
        CREATE INDEX T1_I1 ON T1(I1);
        INSERT INTO T1 VALUES (3,3);
        ALTER TABLE T1 ALTER TABLESPACE USER_MEM_TBS;

-   **Actual Results**

        ERR-91015 : Communication failure. 

-   **Expected Results**

        Alter success.

#### Workaround

`N/A`

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50013 Adds a property to configure the format for outputting DML information in adapter logs (`jdbcAdapter.trc` or `oraAdapter.trc`).

`rp-jdbcAdapter`

#### Category  

`Enhancement`

#### Reproducibility 

`Always`

#### Description 

Adds a property to configure the format for outputting DML information in adapter logs (`jdbcAdapter.trc` or `oraAdapter.trc`).

- ADAPTER_XLOG_WRITE_TYPE 

  - Description: DML 정보를 출력하는 형식을 설정하는 프로퍼티이다. 
    - 0: It outputs table and column information recorded in XLog
    - 1: It outputs in SQL statement format.

  - Default value : 0

  - examples

    - ADAPTER_XLOG_WRITE_TYPE = 0 
  
      ~~~bash
      [2020-06-17 14:25:13] com.mysql.jdbc.MysqlDataTruncation: Data truncation: Out of range value for column 'market_disp_seq' at row 1
      [2020-06-17 14:25:13] INSERT : 
      [2020-06-17 14:25:13] Table name tcate
      [2020-06-17 14:25:13] Table Id 2
      [2020-06-17 14:25:13] Column count 17
      [2020-06-17 14:25:13] Column name CATE_C
      [2020-06-17 14:25:13] Hidden Column NO
      [2020-06-17 14:25:13] Column value '220348'
      [2020-06-17 14:25:13] Column name NGROUPSEQ
      [2020-06-17 14:25:13] Hidden Column NO
      [2020-06-17 14:25:13] Column value '0'
      [2020-06-17 14:25:13] Column name PCATE_C
      [2020-06-17 14:25:13] Hidden Column NO
      [2020-06-17 14:25:13] Column value '0'
      [2020-06-17 14:25:13] Column name CATE_N
      [2020-06-17 14:25:13] Hidden Column NO
      [2020-06-17 14:25:13] Column value
      [2020-06-17 14:25:13] -------------------
      [2020-06-17 14:25:13] '취미'
      [2020-06-17 14:25:13] -------------------
      ~~~

    - ADAPTER_XLOG_WRITE_TYPE = 1
  
      ~~~bash
      INSERT INTO INI.BC_CDR VALUES ( '148946461353114', '0502859198', '1', '2001', '2017031413101300', '2017031413101402', '01022223333', '01093488256', '11112222', '33334444', '0', TO_DATE('(null)(null)', 'YYYY-MM-DD HH:MI:SSSSSSSS') );
      ~~~


#### How to reproduce this bug

-   **Reproduction conditions**

-   **Actual Results**

-   **Expected Results**

#### Workaround

`N/A`

#### Changes

-   Performance view
-   Property
    
-   Compile Option
-   Error Code

### BUG-50025 Fixes a bug where executing `STARTUP SERVICE` immediately after `CREATE DATABASE` could cause the Altibase server to terminate abnormally or result in an `ERR-11110: The index is inconsistent` error.

#### module

`sm`

#### Category  

`Assert`

#### Reproducibility 

`Frequence`

#### Description  

Fixes a bug where executing `STARTUP SERVICE` immediately after `CREATE DATABASE` could cause the Altibase server to terminate abnormally or result in an `ERR-11110: The index is inconsistent` error.

To work around this bug, you should perform the `STARTUP SERVICE` in the following order:

(1) CREATE DATABASE

(2) SHUTDOWN ABORT

(3) STARTUP SERVICE


#### How to reproduce this bug

-   **Reproduction conditions**

    ```sql
    $ is -sysdba
    iSQL(sysdba)> STARTUP PROCESS; 
    iSQL(sysdba)> CREATE DATABASE MYDB INITSIZE=50M NOARCHIVELOG CHARACTER SET UTF8 NATIONAL CHARACTER SET UTF16;
    iSQL(sysdba)> STARTUP SERVICE;
    iSQL(sysdba)> CREATE USER ALTITEST IDENTIFIED BY ALTITEST;
    iSQL(sysdba)> DROP USER ALTITEST;
    ```

-   **Actual Results**

    Altibase 서버 비정상 종료 또는

    ~~~sql
    iSQL(sysdba)> DROP USER ALTITEST;
    [ERR-11110 : The index is inconsistent]
    ~~~

-   **Expected Results**

    ```sql
    iSQL(sysdba)> DROP USER ALTITEST;
    Drop success.
    ```

#### Workaround

데이터베이스를 생성한 후 SHUTDOWN ABORT 명령 수행하고 STARTUP을 수행합니다.

```sql
$ is -sysdba
iSQL(sysdba)> STARTUP PROCESS; 
iSQL(sysdba)> CREATE DATABASE MYDB INITSIZE=50M NOARCHIVELOG CHARACTER SET UTF8 NATIONAL CHARACTER SET UTF16;
iSQL(sysdba)> SHUTDOWN ABORT;
iSQL(sysdba)> STARTUP SERVICE;
iSQL(sysdba)> CREATE USER ALTITEST IDENTIFIED BY ALTITEST;
iSQL(sysdba)> DROP USER ALTITEST;
```

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50033 When starting the adapter, a core file is generated if the ALA log file cannot be opened.

#### module

`rp-ala`

#### Category

`Assert`

#### Reproducibility 

`Rare`

#### Description 

When starting the adapter, if the ALA log file cannot be opened, the adapter process receives a signal, is forcibly terminated, and a core file is generated. The exception handling has been modified to improve this, so that the following error message is output in the adapter trace log (e.g., `jdbcAdapter.trc`):

`ALA library error: 335873, Failed to open log file`


#### How to reproduce this bug

-   **Reproduction conditions**

-   **Actual Results**

-   **Expected Results**

#### Workaround

`N/A`

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50057 An error occurs when using the `ROLLUP` function, aggregate functions, and the `ORDER BY` clause together.

#### module

`qp-select`

#### Category 

`Functional Error`

#### Reproducibility 

`Frequence`

#### Description  

Fixed the result error that occurs when using the `ROLLUP` function, aggregate functions, and the `ORDER BY` clause together. After the patch, the results may differ when executing queries that satisfy the bug conditions.


#### How to reproduce this bug

-   **Reproduction conditions**

    ```sql
    DROP TABLE T1;
    CREATE TABLE T1( I1 VARCHAR(10), I2 VARCHAR(10), I3 VARCHAR(10) );
    INSERT INTO T1 VALUES(1,1,1);
    INSERT INTO T1 VALUES(1,2,2);
    INSERT INTO T1 VALUES(3,2,1);
    INSERT INTO T1 VALUES(10,2,1);
    SELECT /*+ NO_PLAN_CACHE */ TO_CHAR(COUNT(*) )
      FROM T1
     GROUP BY ROLLUP(I1), I2
     ORDER BY 1;
    ```

-   **Actual Results**

    ```sql
    TO_CHAR(COUNT(*))  
    ---------------------
    0           
    0           
    0           
    0           
    0           
    0           
    6 rows selected.
    ```

-   **Expected Results**

    ```sql
    TO_CHAR(COUNT(*))  
    ---------------------
    1
    1
    1
    1
    1
    3
    6 rows selected.
    ```

#### Workaround

`N/A`

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50058 Fixed a memory reference error where the replication receiver thread may not terminate when executing `DROP REPLICATION`.

#### module

`rp`

#### Category 

`Memory Error`

#### Reproducibility 

`Unknown`

#### Description  

Fixed a memory reference error where the replication receiver thread may not terminate when executing `DROP REPLICATION`. 


#### How to reproduce this bug

-   **Reproduction conditions**

-   **Actual Results**

-   **Expected Results**

#### Workaround

`N/A`

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50059 Changes the behavior of `aku -p end`. Replication is stopped after performing the replication `FLUSH` command.

#### module

`aku`

#### Category  

`Reliability`

#### Reproducibility 

`Always`

#### Description

Changes the behavior of `aku -p end`. To prevent potential data inconsistencies, the `ALTER REPLICATION ~ FLUSH ALL` command is executed on the replication object of the pod where `aku -p end` is performed, to transmit all changed data to other pods before stopping replication.

Due to the added FLUSH operation, the execution of `aku -p end` may take longer than before the bug was addressed.

A new `aku` property, `AKU_FLUSH_AT_END`, has been added. The default value is `1`. 

This property determines whether to execute the `ALTER REPLICATION ~ FLUSH ALL` command to eliminate replication gaps when executing the `aku -p end` command on a slave pod. Setting it to `1` will eliminate replication gaps using the FLUSH ALL command, while setting it to `0` will not.


#### How to reproduce this bug

-   **Reproduction conditions**

-   **Actual Results**

-   **Expected Results**

#### Workaround

`N/A`

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50061 Modifies the exception handling when using set operators in an updatable view.

#### module

`qp`

#### Category 

`Functional Error`

#### Reproducibility

`Always`

#### Description

Improved the error message to correctly reflect the constraint that a view using set operators cannot be used as an updatable view. The error message has been changed as follows:

- Before

  ERR-31455 : Failed to work because an internal exception occurred from an OS.[Contact Altibase's Support Center]

- After

  ERR-313A4 : Cannot modify a column for a non key-preserved table


#### How to reproduce this bug

-   **Reproduction conditions**

    ```sql
    CREATE TABLE D1(I1 INTEGER, I2 INTEGER);
    CREATE OR REPLACE VIEW V1 AS SELECT * FROM D1 UNION SELECT * FROM D1;
    DELETE FROM (SELECT * FROM V1);
    ```

-   **Actual Results**

    ```sql
    ERR-31455 : Failed to work because an internal exception occurred from an OS.[Contact Altibase's Support Center]
    ```

-   **Expected Results**

    ```sql
    ERR-313A4 : Cannot modify a column for a non key-preserved table
    ```

#### Workaround

`N/A`

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50071 An `ERR-31455` error may occur, or the Altibase server may terminate abnormally, if a subquery in the `SET` clause references multiple update targets.

#### module

`qp-dml-pvo`

#### Category  

`Fatal`

#### Reproducibility 

`Always`

#### Description 

Fixes a bug where an `ERR-31455: Failed to work because an internal exception occurred from an OS` error occurs, or the Altibase server terminates abnormally, when a subquery in the `SET` clause references multiple update targets. This bug occurs when the simple view merging feature is enabled.


#### How to reproduce this bug

-   **Reproduction conditions**

-   **Actual Results**

-   **Expected Results**

#### Workaround

`N/A`

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50082 Changes the behavior of `aku -p start` on a slave pod that terminated abnormally. The `FLUSH` command is executed after starting replication.

#### module

`aku`

#### Category  

`Reliability`

#### Reproducibility 

`Unknown`

#### Description  

Changes the behavior of `aku -p start` on a slave pod that terminated abnormally.

A slave pod that terminated abnormally refers to one where the `aku -p end` command was not executed or did not complete normally, leaving replication information in Altibase. If previous replication data remains, data inconsistencies may occur after restarting the slave pod, so synchronization of previous data is added.

1. When executing `aku -p start` on the slave pod, the Altibase server property `ADMIN_MODE` is set to 1 to block access for database users and forcefully terminate any connected sessions.
2. The replication is started on the slave pod executing `aku -p start`, and the `ALTER REPLICATION ~ FLUSH ALL` command is executed. This command sends data that was not synchronized to other pods.
3. The remote pod executes `ALTER REPLICATION ~ FLUSH WAIT *wait_time*` to the slave pod where `aku -p start` was performed.
4. The `ADMIN_MODE` property of the Altibase server on the slave pod where `aku -p start` was executed is set back to 0 to allow access for database users.

Due to these changes, the execution time of the `aku -p start` command may be longer than before the bug was addressed.

Related to this, new `aku` properties `AKU_FLUSH_AT_START` and `AKU_FLUSH_TIMEOUT_AT_START` have been added.


#### How to reproduce this bug

-   **Reproduction conditions**

-   **Actual Results**

-   **Expected Results**

#### Workaround

`N/A`

#### Changes

-   Performance view
-   Property
    
-   Compile Option
-   Error Code

### BUG-50090 The following behavior of the `Statement` object returns `true` from `getMoreResults()` when the result is not a `ResultSet` object.

#### module

`mm-jdbc`

#### Category  

`Functional Error`

#### Reproducibility 

`Always`

#### Description   

Fixed a bug where `getMoreResults()` returns `true` when the next result of the `Statement` object is not a `ResultSet` object. It has been corrected to return `false` according to the JDBC API.

To reflect this fix, the Altibase JDBC driver needs to be patched.

The behavior of the `getMoreResults()` method will change in Altibase JDBC driver version 7.1.0.8.3 or higher with this fix.

- Before : Returns true for the number of ResultSet objects.

- After : Returns true for the number of ResultSet objects minus 1.


#### How to reproduce this bug

-   **Reproduction conditions**

-   **Actual Results**

-   **Expected Results**

#### Workaround

`N/A`

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50094 Changes the behavior of the `ADD COLUMN` operation for memory tables.

#### module

`qp`

#### Category  

`Functional Error`

#### Reproducibility 

`Always`

#### Description 

In Altibase 7.1.0.8.3 and higher, the behavior of the `ADD COLUMN` operation for memory tables is as follows:

The 'real-time DDL' operation is determined based on the size of the column to be added.

- **When 'real-time DDL' operates:**

  If the size of the column to be added exceeds the size specified in `MEMORY_VARIABLE_COLUMN_IN_ROW_SIZE`, the column is created as a VARIABLE column, and real-time DDL operates.

- **When 'real-time DDL' does not operate:**

  If the size of the column to be added is less than or equal to the size specified in `MEMORY_VARIABLE_COLUMN_IN_ROW_SIZE`, the column is created as a FIXED column, and real-time DDL does not operate.

  If real-time DDL does not operate, the `ADD COLUMN` operation is processed as follows:

  - The target table is internally reconstructed.
  - During this process, an X lock is acquired on the target table, so the table cannot be accessed until the `ADD COLUMN` operation is completed.
  - Memory usage increases in proportion to the size of the target data.

If you wish to revert to the behavior prior to Altibase 7.1.0.8.3, please contact the Altibase Technical Support Center.


#### How to reproduce this bug

-   **Reproduction conditions**

-   **Actual Results**

-   **Expected Results**

#### Workaround

`N/A`

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50096 After a DDL replication failure, the replication sender may not start due to abnormal behavior of the HeartBeat thread.

#### module

`rp`

#### Category  

`Functional Error`

#### Reproducibility 

`Always`

#### Description  

Fixed the issue where the replication sender does not start due to the HeartBeat thread not terminating properly when replication is stopped after a DDL replication failure.


#### How to reproduce this bug

-   **Reproduction conditions**

-   **Actual Results**

-   **Expected Results**

#### Workaround

`N/A`

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50106 In iSQL, after executing `SET PARTITIONS ON`, performing the `desc` command results in the error `ERR-31002: A single-row subquery has returned more than one row.`

#### module

`ux-isql`

#### Category

`Functional Error`

#### Reproducibility

`Always`

#### Description

Fixed the issue where executing the `desc` command in iSQL after running `SET PARTITIONS ON` results in the error `ERR-31002: A single-row subquery has returned more than one row.`


#### How to reproduce this bug

-   **Reproduction conditions**

    ```sql
    CONNECT SYS/MANAGER
    CREATE TABLE T1 (C1 INTEGER, C2 INTEGER);
    
    CREATE USER USER1 IDENTIFIED BY USER1;
    CONNECT USER1/USER1
    CREATE TABLE T1 (C1 INTEGER, C2 INTEGER);
    SET PARTITIONS ON;
    DESC T1;
    ```

-   **Actual Results**

    ```sql
    DESC T1;
    [ TABLESPACE : SYS_TBS_MEM_DATA ]
    [ ATTRIBUTE ]
    ------------------------------------------------------------------------------
    NAME                                     TYPE                        IS NULL
    ------------------------------------------------------------------------------
    C1                                       INTEGER         FIXED
    C2                                       INTEGER         FIXED
    T1 has no index
    T1 has no primary key
    [ERR-31002 : A single-row subquery has returned more than one row.]
    ```

-   **Expected Results**

    ```sql
    DESC T1;
    [ TABLESPACE : SYS_TBS_MEM_DATA ]
    [ ATTRIBUTE ]
    ------------------------------------------------------------------------------
    NAME                                     TYPE                        IS NULL
    ------------------------------------------------------------------------------
    C1                                       INTEGER         FIXED
    C2                                       INTEGER         FIXED
    T1 has no index
    T1 has no primary key
    ```

#### Workaround

`N/A`

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50131 Adds exception handling for the issue where the Altibase server crashes during conditional checks.

#### module

`qp-dml-execute`

#### Category  

`Fatal`

#### Reproducibility 

`Impossible`

#### Description

Adds exception handling for the issue where the Altibase server crashes during conditional checks.


#### How to reproduce this bug

-   **Reproduction conditions**

-   **Actual Results**

-   **Expected Results**

#### Workaround

`N/A`

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50076 Fixed the build failure issue on Linux 32-bit platforms in Altibase 7.1.0.7.3 and later versions.

-   **module** : sm

-   **Category** : Compile Error

-   **Reproducibility** : Always

-   **Description** : The compilation error issue on Linux 32-bit platforms in Altibase versions 7.1.0.7.3 to 7.1.0.8.2 has been fixed. You can now download the Linux 32-bit client package.

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

### BUG-49996 Fixed the issue where the error message "PCRE2 error:" is displayed.

- **module** : st

- **Category** : Other

- **Reproducibility** : Always

- **Description** : Fixed the issue where the error message "PCRE2:" is displayed and modifies the content of the cause.

  (Before)

  ```
  SQL> select regexp_like('c', '[');
  
  [ERR-2106C : PCRE2 error: missing terminating ] for character class (occurred in qsfPCRERegExp::expCompile4Estimate)
  
  0001 : select REGEXP_LIKE('c', '[')
  ```

  (After)

  ```
  SQL> select regexp_like('c', '[');
  
  [ERR-2106C : error: missing terminating ] for character class (occurred in qsfPCRERegExp::expCompile4Estimate)
  
  0001 : select REGEXP_LIKE('c', '[')
  ```

- **How to reproduce this bug**

  -   **Reproduction conditions**

  -   **Actual Results**

  -   **Expected Results**

- **Workaround**

- **Changes**

  - Performance view

  - Property

  - Compile Option

  - Error Code

    - Changes
  - before: [ERR-2106C : PCRE2 error: missing terminating ]
      - after: [ERR-2106C : error: missing terminating ]

    


Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    7.1.0.8.3     |          6.5.1          |    8.10.1    |        7.1.7        |            7.4.7             |

> You can check the module version change history in [Version_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.1/Altibase_7_1_Version_Histories.md).

### Compatibility

#### Database binary version

The database binary version has not changed.

> The database binary version indicates the compatibility of database image files and log files. If this version needs to be patched to a different version, the database must be reorganized.

#### Meta Version

The meta version has not changed.

> If you want to roll back the patch after patching to a version with a changed meta version, see [Meta Downgrade](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/eng/Installation Guide.md#meta-downgrade).

#### CM protocol Version

The cm protocol version has not changed.

#### Replication protocol Version

The replication protocol version has not changed.

### Altibase Server Properties

#### Added properties

#### Changed properties

#### Deleted properties

### Performance Views

#### Added performance views

#### Changed performance views

#### Deleted performance views
