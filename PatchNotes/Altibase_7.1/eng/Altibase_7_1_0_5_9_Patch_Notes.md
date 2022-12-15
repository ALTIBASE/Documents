# Altibase 7.1.0.5.9 Patch Notes

<br/>

<br/>



# **Table of Contents** 

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Fixed Bugs](#fixed-bugs)
    - [BUG-49102 If you perform SPLIT PARTITION on a RANGE partitioned table with more than one partitioning key and then perform the COPY_TABLE_STATS procedure, incorrect results may occur.](#bug-49102-if-you-perform-split-partition-on-a-range-partitioned-table-with-more-than-one-partitioning-key-and-then-perform-the-copy_table_stats-procedure-incorrect-results-may-occur)
    - [BUG-49143 The ping method of the JDBC driver is improved to work in prepared mode as well.](#bug-49143-the-ping-method-of-the-jdbc-driver-is-improved-to-work-in-prepared-mode-as-well)
    - [BUG-49155 There is a concurrency problem when replacing trace log files.](#bug-49155-there-is-a-concurrency-problem-when-replacing-trace-log-files)
    - [BUG-49181 In a replication environment using the DDL replication function, if V$REPRECEIVER is queried while executing a DDL statement, the Altibase server may be terminated abnormally.](#bug-49181-in-a-replication-environment-using-the-ddl-replication-function-if-vrepreceiver-is-queried-while-executing-a-ddl-statement-the-altibase-server-may-be-terminated-abnormally)
    - [BUG-49200 The memory usage restriction function does not work normally.](#bug-49200-the-memory-usage-restriction-function-does-not-work-normally)
    - [BUG-49213 Improves internal exception handling when DDL replication fails.](#bug-49213-improves-internal-exception-handling-when-ddl-replication-fails)
    - [BUG-49217 Improve Adapter for JDBC, Adapter for Oracle to replicate data by separating column names.](#bug-49217-improve-adapter-for-jdbc-adapter-for-oracle-to-replicate-data-by-separating-column-names)
    - [BUG-49224 In a replication active-active environment using the DDL replication function, if a DDL statement fails due to DDL_LOCK_TIMEOUT on the remote server, the Altibase server on the local server may terminate abnormally.](#bug-49224-in-a-replication-active-active-environment-using-the-ddl-replication-function-if-a-ddl-statement-fails-due-to-ddl_lock_timeout-on-the-remote-server-the-altibase-server-on-the-local-server-may-terminate-abnormally)
    - [BUG-49233 Change the exception thrown when calling a function not supported by Altibase42.jar.](#bug-49233-change-the-exception-thrown-when-calling-a-function-not-supported-by-altibase42jar)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [Compatibility](#compatibility)
    - [Altibase Server Properties](#altibase-server-properties)
    - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->



Fixed Bugs
==========

### BUG-49102 If you perform SPLIT PARTITION on a RANGE partitioned table with more than one partitioning key and then perform the COPY_TABLE_STATS procedure, incorrect results may occur.

-   **module** : qp

-   **Category** : Functional Error

-   **Reproducibility** : Frequence

-   **Description** : Fixes a bug where performing a SPLIT PARTITION and performing a COPY_TABLE_STATS procedure on a RANGE partitioned table with more than one partitioning key gives incorrect results.
    
-   **How to reproduce this bug**
    
    - **Reproduction conditions**

      ```sql
      DROP TABLE T1 CASCADE;
      
      CREATE TABLE T1
      (
          I1   INTEGER,
          I2   INTEGER
      )
      PARTITION BY RANGE( I1, I2 )
      (
          PARTITION P1   VALUES LESS THAN (  101,10 ),
          PARTITION P2   VALUES LESS THAN (  201,20 ),
          PARTITION P3   VALUES LESS THAN (  301,30 ),
          PARTITION PMAX VALUES LESS THAN ( 1001,40 ),
          PARTITION DEF VALUES DEFAULT 
      ) TABLESPACE SYS_TBS_DISK_DATA;
      
      INSERT INTO T1 SELECT LEVEL, 1 FROM DUAL CONNECT BY LEVEL <= 1000;
      
      EXEC GATHER_TABLE_STATS('SYS', 'T1');
      
      ALTER TABLE T1 SPLIT PARTITION PMAX AT ( 400, 40 ) INTO ( PARTITION P4, PARTITION PMAX );
      
      -- You need to install two save packages, DBMS_CONCURRENT_EXEC, and DBMS_STATS to perform the statement below.
      EXEC DBMS_STATS.COPY_TABLE_STATS('SYS', 'T1', 'P3', 'P4');
      ```
    
    - **Actual Results**
    
      ```sql
      SELECT PARTITION_NAME, NUM_DIST, NUM_NULL, AVG_LEN, MIN,MAX
        FROM V$DBMS_STATS S, SYSTEM_.SYS_TABLE_PARTITIONS_ T
       WHERE S.TYPE = 'C' AND S.TARGET_ID = T.PARTITION_OID
       ORDER BY 1, MIN, MAX; 
      PARTITION_NAME   NUM_DIST             NUM_NULL             AVG_LEN              MIN            MAX      
      --------------------------------------------------------------------------------------------------------
      P1               1                    0                    4                    1              1        
      P1               101                  0                    4                    1              101      
      P2               1                    0                    4                    1              1        
      P2               100                  0                    4                    102            201      
      P3               1                    0                    4                    1              1        
      P3               100                  0                    4                    202            301      
      P4               100                  0                    4                    30             40       
      P4               1                    0                    4                    301            400      
      PMAX             1                    0                    4                    1              1        
      PMAX             699                  0                    4                    302            1000   
      ```
    
    -   **Expected Results**
    
        ```sql
        SELECT PARTITION_NAME, NUM_DIST, NUM_NULL, AVG_LEN, MIN,MAX
          FROM V$DBMS_STATS S, SYSTEM_.SYS_TABLE_PARTITIONS_ T
         WHERE S.TYPE = 'C' AND S.TARGET_ID = T.PARTITION_OID
         ORDER BY 1, MIN, MAX; 
        PARTITION_NAME   NUM_DIST             NUM_NULL             AVG_LEN              MIN            MAX      
        --------------------------------------------------------------------------------------------------------
        P1               1                    0                    4                    1              1        
        P1               101                  0                    4                    1              101      
        P2               1                    0                    4                    1              1        
        P2               100                  0                    4                    102            201      
        P3               1                    0                    4                    1              1        
        P3               100                  0                    4                    202            301      
        P4               1                    0                    4                    30             40       
        P4               100                  0                    4                    301            400      
        PMAX             1                    0                    4                    1              1        
        PMAX             699                  0                    4                    302            1000
        ```
    
-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49143 The ping method of the JDBC driver is improved to work in prepared mode as well.

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : The JDBC ping method operates on Statement.executeQuery().
    In the case of a specific connection pool (e.g. Tomcat DBCP2), it is improved to operate in prepared mode to support that validation query operates in prepared mode.

    The JDBC driver must be patched to apply this bug.

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

### BUG-49155 There is a concurrency problem when replacing trace log files.

-   **module** : id

-   **Category** : Reliability

-   **Reproducibility** : Rare

-   **Description** : Fix concurrency issues when replacing trace log files.
    
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

### BUG-49181 In a replication environment using the DDL replication function, if V$REPRECEIVER is queried while executing a DDL statement, the Altibase server may be terminated abnormally.

-   **module** : rp

-   **Category** : Fatal

-   **Reproducibility** : Rare

-   **Description** : In a replication environment where the DDL replication function is used (REPLICATION_DDL_SYNC = 1), a bug in which the Altibase server abnormally terminates due to a concurrency problem when V$REPRECEIVER is queried while executing a DDL statement is fixed.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

        Setting Altibase server property REPLICATION_DDL_SYNC = 1 in Altibase replication environment
        Query V$REPRECEIVER during TRUNCATE table
    
  -   **Actual Results**
  
          Altibase server terminates abnormally.
  
  -   **Expected Results**
  
          Normally V$REPRECEIVER is queried.
  
-   **Workaround**

        Do not query V$REPRECEIVER, during DDL statement execution when REPLICATION_DDL_SYNC = 1 is set.

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49200 The memory usage restriction function does not work normally.

-   **module** : id

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixes a bug where the memory usage restriction function does not work normally. If an error does not occur because the memory usage is low when executing SQL including memory tables, it may fail due to PREPARE_STMT_MEMORY_MAXIMUM and EXECUTE_STMT_MEMORY_MAXIMUM after patching.

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

### BUG-49213 Improves internal exception handling when DDL replication fails.

-   **module** : rp

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Improves internal exception handling when DDL replication fails.

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

### BUG-49217 Improve Adapter for JDBC, Adapter for Oracle to replicate data by separating column names.

-   **module** : rp-jdbcAdapter

-   **Category** : Other

-   **Reproducibility** : Always

-   **Description** : Improve Adapter for JDBC, Adapter for Oracle to replicate data by separating column names.
    
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

### BUG-49224 In a replication active-active environment using the DDL replication function, if a DDL statement fails due to DDL_LOCK_TIMEOUT on the remote server, the Altibase server on the local server may terminate abnormally.

-   **module** : rp

-   **Category** : Other

-   **Reproducibility** : Rare

-   **Description** : In a replication active-active environment using the DDL replication function, a bug in which the Altibase server of the local server abnormally terminates when a DDL statement fails due to DDL_LOCK_TIMEOUT in the remote server is fixed.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

        It is an Altibase replication active-active environment and DDL replication function is used (REPLICATION_DDL_SYNC = 1)
        
        TRUNCATE on table T1 on local server
        INSERT into table T1 from remote server
        TRUNCATE failures on the local server
        INSERT into table T1 from remote server

  -   **Actual Results**

          Altibase server abnormally terminated.

  -   **Expected Results**

          Replication operates normally after truncate failure

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49233 Change the exception thrown when calling a function not supported by Altibase42.jar.

-   **module** : mm-jdbc

-   **Category** : Functionality

-   **Reproducibility** : Always

-   **Description** : Change to throw SQLFeatureNotSupportedException instead of SQLException when calling a feature not supported by Altibase42.jar. The JDBC driver(Altibase42.jar) must be patched to apply this bug.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```java
    Connection sConn = getConnection();sConn.setTypeMap(new HashMap());
    ```

  - **Actual Results**

    ```java
    Exception in thread "main" java.sql.SQLException: Unsupported feature: User defined type
    ```

  -   **Expected Results**

      ```java
      Exception in thread "main" java.sql.SQLFeatureNotSupportedException: User defined type
      ```

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    7.1.0.5.9     |          6.5.1          |    8.9.1     |        7.1.7        |            7.4.6             |

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

#### Added properties

#### Changed properties

#### Deleted properties

### Performance Views

#### Added performance views

#### Changed performance views

#### Deleted performance views
