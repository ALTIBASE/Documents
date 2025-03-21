# Altibase 7.1.0.9.0 Patch Notes

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-50503<a name=bug-50503></a> New property - AKU_REPLICATION_RESET_AT_END added to AKU

-   **module** : aku

-   **Category** : Enhancement

-   **Reproducibility** : Always

-   **Description** : New property - AKU_REPLICATION_RESET_AT_END has been added to the aku.conf file. This property allows you to configure whether to perform a replication RESET when executing the `aku -p end` command on a slave pod. It does not affect the master pod.
    
    The possible values for this setting are:
    
    * 0 : Do not perform RESET
    
    * 1 (default): Perform RESET
    
-   **How to reproduce this bug**

    -   **Reproduction conditions**

    -   **Actual Results**

    -   **Expected Results**

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
        -   추가
            -   AKU_REPLICATION_RESET_AT_END
                -   Default value : 1
                -   Range : [0,1]
                -   Description: This property determines whether to perform a reset of the replication information or not by using RESET command. If this value is set to 1, the replication information is reset. If this value is set to 0, the replication information is not reset.
    -   Compile Option
    -   Error Code

### BUG-50557<a name=bug-50557></a> Support for Long Long type for array host variables in applications using BIGINT arrays in stored procedures on Windows environment.

-   **module** : mm-apre

-   **Category** : Portability

-   **Reproducibility** : Always

-   **Description** : For stored procedures using BIGINT arrays in Windows and 32-bit Linux environments, the application must use the Long Long data type for array host variables. If Long type is used instead, the error [ERR-31471 : Index out of range for host language array.] will occur. This update ensures proper support for the Long Long data type when handling BIGINT arrays in these environments.

-   **How to reproduce this bug**
    -   **Reproduction conditions**
    
    -   **Actual Results**
    
    -   **Expected Results**
    
-   **Workaround**

-   **변경사항**
    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50604<a name=bug-50604></a> Support case sensitivity in PSM syntax

-   **module** : qp-psm-trigger-pvo

-   **Category** : Enhancement

-   **Reproducibility** : Always

-   **Description** : A new property, **PSM_CASE_SENSITIVE_MODE**, has been added to enable case sensitivity when referencing columns of %ROWTYPE or RECORD types in PSM syntax. When this property is set to 1, the case of column names will be respected. This setting also applies when using the LABEL statement. Additionally, a bug has been fixed where the query conversion was incorrect when referencing %ROWTYPE or RECORD type column names using double quotes (`""`) in PSM.
    
-   **How to reproduce this bug**

    -   **Reproduction conditions**

            drop table "tT";
            CREATE TABLE "tT" (
            "t" int,
            "T" int
            );
            CREATE OR REPLACE PROCEDURE proc1
            AS
                r1 "tT"%ROWTYPE;
            BEGIN
                r1."t" := 10;
            END;
            /

    -   **Actual Results**

            [ERR-31182 : Duplicate column name
            In procedure SYS.PROC1
            0005 :     R1."t" := 10;
                      ^    ^
            ]

    -   **Expected Results**

            Create success.

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
        -   PSM_CASE\_SENSITIVE_MODE
            -   Default value : 0
            -   Range : [0,1]
            -   Description: A property that determines whether to distinguish between uppercase and lowercase when referencing column names, LABEL names, etc., of %ROWTYPE and RECORD types within PSM. Setting it to 0 disables case sensitivity, while setting it to 1 enables case sensitivity.
        
    -   Compile Option
-   Error Code

### BUG-50606<a name=bug-50606></a> The Altibase 7.1.0.9.0 JDBC driver is available for download from the Maven Central Repository.

-   **module** : mm-jdbc

-   **Category** : Enhancement

-   **Reproducibility** : Always

-   **Description** : Now the Altibase 7.1.0.9.0 JDBC driver is available for download from the Maven Central Repository.
    
-   **How to reproduce this bug**
    -   **Reproduction conditions**
    
    -   **Actual Results**
    
    -   **Expected Results**
    
-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50608<a name=bug-50608></a> Support case-sensitivity when creating private synonyms

-   **module** : qp-ddl-dcl-pvo

-   **Category** : Enhancement

-   **Reproducibility** : Always

-   **Description** : The ability to distinguish between uppercase and lowercase characters when creating private synonyms has been added. Previously, the case of the name was not distinguished, preventing the creation of synonyms with the same name, but with this patch, it is now possible.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    create or replace procedure "proc4" as
    begin
      println('proc4');
    end;
    /
    create synonym proc4 for sys."proc4";
    ```

  - **Actual Results**

    ```sql
    [ERR-31208 : Unable to create a synonym with the same name as the object]
    ```

  -   **Expected Results**

      ```sql
      Create success.
      ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

Fixed Bugs
==========

### BUG-49699<a name=bug-49699></a> Fixed issue where the BUILD OFFLINE META command fails when DDL statements (including SPLIT, MERGE, or DROP PARTITION) exist in the JDBC Adapter log with OFFLINE ENABLE.

-   **module** : rp-jdbcAdapter

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : If DDL statements (including SPLIT, MERGE, or DROP PARTITION) existed in the JDBC Adapter log with the offline option, the number of replication table names and user names did not match, causing the BUILD OFFLINE META command in the Offline Adapter to fail. This issue has been fixed so that the command no longer fails.
    
-   **How to reproduce this bug**
    -   **Reproduction conditions**
    
    -   **Actual Results**
    
    -   **Expected Results**
    
-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code
        -   467,rpERR\_ABORT\_RPC\_USER\_OR\_TABLE\_MISMATCH = The table
            name and user name for offline replication do not match the
            meta file.(table name: \<0%s\>, user name: \<1%s\>) 
            \# \*Cause: 
            \#   - The offline replication meta information
            configuration fails due to a mismatch between the table name
            and user name compared to the information in the meta file.
            \# \*Action:
            \#   - Check the table name and user name for offline
            replication and configure the replication that matches the
            meta file.

### BUG-50365<a name=bug-50365></a> Fixed an issue where the server could abnormally shut down due to a bug in the column constraint validation logic for hybrid partitioned tables.

-   **module** : qp

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where the server could abnormally shut down due to a bug in the column constraint validation logic for hybrid partitioned tables.
    
-   **How to reproduce this bug**

    -   **Reproduction conditions**

    -   **Actual Results**

    -   **Expected Results**

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50427<a name=bug-50427></a> Support for Preserved Order Optimization when using ORDER BY on RANGE PARTITION.

-   **module** : qp

-   **Category** : Enhancement

-   **Reproducibility** : Always

-   **Description** : 
    
-   Support for Preserved Order Optimization in RANGE PARTITION tables with local indexes has been added, allowing optimized execution of ORDER BY, GROUP BY, and JOIN operations. This feature can be enabled by setting the hidden property `RANGE_PARTITION_USABLE_LOCAL_INDEX` to 1.

    When this feature is enabled, the execution plan will change for partitioned tables that meet the following conditions:

    - In a RANGE PARTITION table, when the partition key is used in the WHERE clause condition and the same partition key is used in ORDER BY or GROUP BY.

    However, this feature is only applicable when there is a single partition key. It does not apply to Parallel Query or Merge Join operations.

- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    DROP TABLE T1;
    DROP INDEX IDX1;
    CREATE TABLE T1 ( I1 INT, I2 INT, I3 INT )
    PARTITION BY RANGE ( I1 )
        (
         PARTITION P1 VALUES LESS THAN (10)
         , PARTITION P2 VALUES LESS THAN (20)
         , PARTITION P3 VALUES LESS THAN (30)
         , PARTITION P4 VALUES LESS THAN (40)
         , PARTITION P_MAX VALUES DEFAULT
        );
    
    INSERT INTO T1 SELECT LEVEL, LEVEL, LEVEL FROM DUAL CONNECT BY LEVEL < 50;
    CREATE UNIQUE INDEX IDX1 ON T1 ( I1 ) LOCAL;
    
    SELECT * FROM T1 WHERE I1 > 20 ORDER BY I1 DESC;
    ```
    
  - **Actual Results**
  
    ```sql
    PROJECT ( COLUMN_COUNT: 3, TUPLE_SIZE: 12, COST: 0.04 )
     SORT ( ITEM_SIZE: ??, ITEM_COUNT: ??, ACCESS: ??, COST: 0.04 )
      PARTITION-COORDINATOR ( TABLE: SYS.T1, PARTITION: 3/5, ACCESS: ??, COST: 0.03 )
       SCAN ( PARTITION: P_MAX, INDEX: SYS.IDX1, RANGE SCAN, ACCESS: ??, COST: 0.01 )
       SCAN ( PARTITION: P4, INDEX: SYS.IDX1, RANGE SCAN, ACCESS: ??, COST: 0.01 )
       SCAN ( PARTITION: P3, INDEX: SYS.IDX1, RANGE SCAN, ACCESS: ??, COST: 0.01 )
    ```
  
  -   **Expected Results**
  
      ```sql
      PROJECT ( COLUMN_COUNT: 3, TUPLE_SIZE: 12, COST: 0.04 )
        PARTITION-COORDINATOR ( TABLE: SYS.T1, PARTITION: 3/5, ACCESS: ??, COST: 0.03 )
         SCAN ( PARTITION: P_MAX, INDEX: SYS.IDX1, RANGE SCAN, ACCESS: ??, COST: 0.01 )
         SCAN ( PARTITION: P4, INDEX: SYS.IDX1, RANGE SCAN, ACCESS: ??, COST: 0.01 )
         SCAN ( PARTITION: P3, INDEX: SYS.IDX1, RANGE SCAN, ACCESS: ??, COST: 0.01 )
      ```
  
-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50435<a name=bug-50435></a> Fixed issue where an unexpected error occurred during the view merge step in the optimization process of multiple subqueries.

-   **module** : qp

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed issue where the error **[ERR-31455: Failed to work because an internal exception occurred from an OS. [Contact Altibase's Support Center]]** occurred during the view merge step in the optimization process of multiple subqueries involving views.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    DROP TABLE T1 CASCADE;
    CREATE TABLE T1( I1 INTEGER, I2 INTEGER );
    ALTER TABLE T1 ADD CONSTRAINT T1_PK PRIMARY KEY( I1 );
    SELECT I1 FROM T1 WHERE I1 IN ( SELECT I1 FROM ( SELECT DISTINCT I1 FROM T1 ) WHERE I1 = 1 OR I2 = 1 );
    ```

  - **Actual Results**

    ```sql
    [ERR-31455 : Failed to work because an internal exception occurred from an OS.[Contact Altibase's Support Center]]
    ```

  -   **Expected Results**

      ```sql
      No rows selected.
      ```

- **Workaround**

  ```sql
  SELECT I1 FROM T1 WHERE I1 IN ( SELECT /*+ no_unnest */ I1 FROM ( SELECT DISTINCT I1 FROM T1 ) WHERE I1 = 1 OR I2 = 1 );
  또는
  SELECT I1 FROM T1 WHERE I1 IN ( SELECT I1 FROM ( SELECT /*+ no_merge */ DISTINCT I1 FROM T1 ) WHERE I1 = 1 OR I2 = 1 );
  ```

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50442<a name=bug-50442></a>Fixed issue where an abnormal server shutdown occurred when using SIMPL_QUERY optimization on partitioned tables.

-   **module** : qp

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixed issue causing abnormal server shutdown when using SIMPL_QUERY optimization on partitioned tables with simple DML queries.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    Alter System set EXECUTOR_FAST_SIMPLE_QUERY = 2;
    CREATE MEMORY DATA TABLESPACE PDT_TBS SIZE 128M AUTOEXTEND ON NEXT 128M;
    CREATE TABLE T1 ( ENABLE INTEGER, I1 INTEGER, I2 INTEGER, I3 INTEGER) PARTITION BY RANGE(ENABLE,I1,I2,I3) ( PARTITION P1 VALUES DEFAULT TABLESPACE PDT_TBS ) TABLESPACE SYS_TBS_DISK_DATA;
    INSERT INTO T1(I2) VALUES (933);
    UPDATE T1 SET I1 = I1 + 1;
    ```

  -   **Actual Results**

          [ERR-91015 : Communication failure.]

  -   **Expected Results**

          1 row inserted.

- **Workaround**

  ```sql
  ALTER SYSTEM SET EXECUTOR_FAST_SIMPLE_QUERY = 1; // Simple Query Fast Execution is not performed on partitioned tables.
  또는
  ALTER SYSTEM SET EXECUTOR_FAST_SIMPLE_QUERY = 0; // Simple Query Fast Execution is not performed.
  ```

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50480<a name=bug-50480></a> Fixed the issue where the JDBC Adapter terminates abnormally when the JDBC_CONNECTION_URL is invalid.

-   **module** : rp-jdbcAdapter

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixed the issue where the JDBC Adapter terminates abnormally when the JDBC_CONNECTION_URL is invalid.
    
-   **How to reproduce this bug**

    -   **Reproduction conditions**

    -   **Actual Results**

    -   **Expected Results**

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50489<a name=bug-50489></a> Fixed the issue where the server shut down abnormally while the Adapter was operating with OFFLINE ENABLE in the HP-UX environment.

Fixed the issue where the adapter terminated abnormally on HP hardware when failing to open the metafile while operating with the offline enable

-   **module** : rp
-   **Category** : Fatal
-   **Reproducibility** : Always
-   **Description** : An issue occurred when an adapter with OFFLINE ENABLE set tried to open a metadata file during operation, but failed when the file was missing. This failure caused the Altibase server to shut down abnormally due to an internal bug. The issue has now been fixed.
-   **How to reproduce this bug**
    -   **Reproduction conditions**

    -   **Actual Results**

    -   **Expected Results**

-   **Workaround**
-   **변경사항**
    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50509<a name=bug-50509></a> Fixed the issue where Eager Replication failed to start on a system with a single CPU.

-   **module** : rp-sender
-   **Category** : Functional Error
-   **Reproducibility** : Always
-   **Description** : When performing replication in EAGER mode, multiple sender threads are created to perform parallel tasks, and the number of threads created is determined by the value of the REPLICATION_EAGER_PARALLEL_FACTOR property. At least two threads should be created, but the minimum value of REPLICATION_EAGER_PARALLEL_FACTOR was set to 1, causing replication to fail to start in environments with a single CPU. To resolve this issue, the minimum value of the REPLICATION_EAGER_PARALLEL_FACTOR property has been changed to 2.
-   **How to reproduce this bug**

    -   **Reproduction conditions**

    -   **Actual Results**

    -   **Expected Results**
-   **Workaround**
-   **변경사항**

    -   Performance view
    -   Property
        - changes on REPLICATION\_EAGER\_PARALLEL\_FACTOR
        
                  -   Min: 1 -> 2
        
          -   Range : [1,512] -> [2,512]
    -   Compile Option
-   Error Code

### BUG-50517<a name=bug-50517></a> Fixed the issue where the  information of Calendar was modified when calling AltibasePreparedStatement.setDate(int, Date, Calendar).

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed the issue where the information of Calendar was modified when calling AltibasePreparedStatement.setDate(int, Date, Calendar).
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```java
    Connection sConn = getConnection("20300");
    PreparedStatement sStmt = sConn.prepareStatement("INSERT INTO t1 VALUES (?, ?)");
    sStmt.setInt(1, 1);
    java.util.Date sNow = new java.util.Date();
    Date sDate = new java.sql.Date(sNow.getTime());
    Calendar sCal = Calendar.getInstance();
    System.out.println("before setDate() sCal getTimeInMillis()===>" + sCal.getTimeInMillis());
    sStmt.setDate(2, sDate, sCal);
    System.out.println("after setDate() sCal getTimeInMillis()===>" + sCal.getTimeInMillis());
    ```

  - **Actual Results**

    ```java
    before setDate() sCal getTimeInMillis()===>1690534207569
    after setDate() sCal getTimeInMillis()===>1690470000000
    ```

  -   **Expected Results**

      ```java
      before setDate() sCal getTimeInMillis()===>1690534207569
      after setDate() sCal getTimeInMillis()===>1690534207569
      ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50530<a name=bug-50530></a> Fixed the issue where the server would shut down abnormally when performing DDL on a disabled index.

-   **module** : sm

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixed the issue where the server would shut down abnormally when performing DDL on a disabled index. Additionally, a bug was fixed in the statistics collection procedure for disabled indexes, where it internally ignored the disabled indexes and incorrectly processed them as successful. After this patch, performing the statistics collection procedure on a disabled index will now return the error message: **[ERR-11084: The Index is disabled.]**.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    CREATE TABLE T1( I1 CHAR(12), I2 NUMBER(9,3), I3 CHAR DEFAULT 'C', I4 NUMBER(9,3)) TABLESPACE SYS_TBS_DISK_DATA;
    ALTER TABLE T1 ALL INDEX DISABLE;
    CREATE INDEX T1_IDX3 ON T1(I3, I2);
    EXEC GATHER_INDEX_STATS('SYS','T1_IDX3');
    ```

  -   **Actual Results**

          Execute success.

  -   **Expected Results**

          [ERR-11084 : The Index is disabled.]

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50533<a name=bug-50533></a>  Fixed the issue where the audit log was not recorded when attempting to connect to an Altibase 7.1 server using an Altibase 6.1.1 client and the connection failed.

-   **module** : mm-altiaudit

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed the issue where the audit log was not recorded when attempting to connect to an Altibase 7.1 server using an Altibase 6.1.1 client and the connection failed.

- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    --1. Altibase 7.1 Server side: connect using isql
    iSQL>audit connect, disconnect;
    iSQL>ALTER SYSTEM START AUDIT;
    --2. Altibase 6.1.1 Client side : attempt to connect to Altibase 7.1 server using isql (with wrong password)
    --3. Altibase 7.1 Server side
    iSQL>ALTER SYSTEM STOP AUDIT;
    --4. check the audit log in $ALTIBASE_HOME/trc/ 
    ```

  -   **Actual Results**

  -   **Expected Results**

-   **Workaround**

-   **변경사항**

    -   Performance view
        
    -   Property
    -   Compile Option
-   Error Code

### BUG-50541<a name=bug-50541></a> Fixed the issue where the server would shut down abnormally when exceeding the query stack during the query validation process.

-   **module** : qp

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixed the issue where the server would shut down abnormally when exceeding the query stack during the query validation process.

-   **How to reproduce this bug**

    -   **Reproduction conditions**

    -   **Actual Results**

    -   **Expected Results**

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50554<a name=bug-50554></a> Fixed the issue where error codes were missing in the audit records when AUDIT_OUTPUT_METHOD was set to 1.

-   **module** : mm

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed the issue where the SQL Return code was missing in the audit records when AUDIT_OUTPUT_METHOD was set to 1 and audit was logged to syslog.
    -   Before
        -   SYS,0,127.0.0.1,,,CONNECT,0,0,0,0,2,0,1,**0**,0,0,0,0,0,0,0,0,0,0,"CONNECT"
    
    -   After
        -   SYS,0,127.0.0.1,,,CONNECT,0,0,0,0,2,0,1,**266286**,0,0,0,0,0,0,0,0,0,0,"CONNECT"
    
-   **How to reproduce this bug**
    -   **Reproduction conditions**

    -   **Actual Results**

    -   **Expected Results**

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50576<a name=bug-50576></a> The issue has been fixed so that the last replication partition cannot be deleted.

-   **module** : rp

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : 
    
-   There was an issue where, if there was only one replication partition and it was deleted, starting the replication would fail due to invalid replication metadata. To resolve this, it is now not possible to delete the only replication partition.

    If an attempt is made to delete the last replication partition, the following error message will be displayed:

    **ERR-611D : Unable to drop the partition because it is the only one replication partition.**

    To delete the partition, either delete the replication object or add another replication partition before deletion.

-   **How to reproduce this bug**

    -   **Reproduction conditions**

    -   **Actual Results**
    
    -   **Expected Results**
    
-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50581<a name=bug-50581></a>  Fixed issue where [ERR-31129 : Procedure or function not found] error occurs when using TIMESTAMPADD function in lowercase.

-   **module** : qp

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed issue where [ERR-31129 : Procedure or function not found] error occurs when using TIMESTAMPADD function in lowercase.

- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    ALTER SESSION SET DEFAULT_DATE_FORMAT = 'YYYY-MM-DD HH:MI:SS:SSSSSS';
    SELECT /*+ NO_PLAN_CACHE */ timestampadd( SQL_TSI_MICROSECOND, 1, '2020-01-10' ) FROM dual;
    ```

  - **Actual Results**

    ```sql
    [ERR-31129 : Procedure or function not found :
    0001 : SELECT /*+ NO_PLAN_CACHE */ timestampadd( SQL_TSI_MICROSECOND, 1, '2020-01-10' ) FROM DUAL
                                      ^           ^
    .]
    ```

  -   **Expected Results**

      ```sql
      TIMESTAMPADD(SQL_TSI_MICROSECOND,1,'2020-0
      ---------------------------------------------
      2020-01-10 00:00:00:000001
      1 row selected.
      ```

- **Workaround**

  ```sql
  SELECT /*+ NO_PLAN_CACHE */ TIMESTAMPADD( SQL_TSI_MICROSECOND, 1, '2020-01-10' ) 
  FROM dual;
  ```

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50589<a name=bug-50589></a> Fixed issue where trace logs restart from altibase_boot.log-0 after server restart, following altibase_boot.log-2

-   **module** : id

-   **Category** : Functional Error

-   **Reproducibility** : Rare

-   **Description** : There is an issue where, after the trace log is written up to altibase_boot.log-2, the server restarts and begins logging again from altibase_boot.log-0. The issue has been fixed so that the trace log is recorded in sequence, even after the server restarts.
    
-   **How to reproduce this bug**
    -   **Reproduction conditions**
    
    -   **Actual Results**
    
    -   **Expected Results**
    
-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50595<a name=bug-50595></a> Fixed an issue where memory increases when executing the same query with the NO_PLAN_CACHE hint multiple times.

-   **module** : mm-plancache

-   **Category** : Memory Error

-   **Reproducibility** : Always

-   **Description** : There was an issue where executing the same query multiple times with the NO_PLAN_CACHE hint caused the number of childPCOs to increase internally. As a result, memory usage grew with each execution. This issue has now been fixed.
    
-   **How to reproduce this bug**
    -   **Reproduction conditions**
    
    -   **Actual Results**
    
    -   **Expected Results**
    
-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50597<a name=bug-50597></a>Fixed the issue where incorrect date column values were returned in JDBC depending on the time zone.

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed the issue where incorrect date column values were returned in JDBC depending on the time zone.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```java
    create table theentity
    (
        theid    integer not null,
        thevalue date,
        primary key (theid)
    );
    
    Connection sConn = getConnection("21165");
    PreparedStatement sPstmt = sConn.prepareStatement("INSERT INTO theentity (theid, thevalue) VALUES ( ? , ? )");
    Timestamp sTimestamp = Timestamp.from(OffsetDateTime.of(2018, 3, 25, 2, 0, 0, 0, ZoneOffset.UTC ).toInstant());
    sPstmt.setInt(1, 1);
    sPstmt.setTimestamp(2, sTimestamp, Calendar.getInstance(TimeZone.getTimeZone("UTC")));
    sPstmt.execute();
    sPstmt.close();
    
    sPstmt = sConn.prepareStatement("select ewi1_0.theid, ewi1_0.thevalue \n" +
                                            "from theentity ewi1_0 \n" +
                                            "where ewi1_0.theid = ?");
    sPstmt.setInt(1, 1);
    ResultSet sRs = sPstmt.executeQuery();
    if (sRs.next())
    {
        Calendar aCal = Calendar.getInstance( TimeZone.getTimeZone( "UTC" ) );
        Timestamp sCol = sRs.getTimestamp(2, aCal);
        Instant sInstant = sCol.toInstant();
        System.out.println("Instant====>" + sInstant);
    }
    
    // Set timezone to Europe/Paris when running java
    java -Duser.timezone="Europe/Paris" InstantTest
    ```

  - **Actual Results**

    ```java
    Instant====>2018-03-25T03:00:00Z
    ```

  -   **Expected Results**

      ```java
      Instant====>2018-03-25T02:00:00Z
      ```

-   **Workaround**

        Omit timezone or set to Asia/Seoul

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50601<a name=bug-50601></a> Fixes an issue where a column used in an aggregate function has an index, and a subquery containing this aggregate function causes a result error in the SubQuery Unnest optimization.

-   **module** : qp

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixes an issue where a column used in an aggregate function has an index, and a subquery containing this aggregate function causes a result error in the SubQuery Unnest optimization.

-   **How to reproduce this bug**

    -   **Reproduction conditions**

        ```sql
        drop table t1;
        drop table t2;
        CREATE TABLE T1
        (
            I1            integer not null,
            I2        smallint,
            I3  integer not null,
            I4 integer not null,
            primary key (I1, I3, I4)
        );
        
        CREATE TABLE T2
        (
            I1     integer not null,
            I2 smallint,
            I3      integer not null,
            I4    varchar(8),
            primary key (I1, I3)
        );
        
        INSERT INTO T1(I2, I4, I1, I3) values (0, 2, 21, 1);
        INSERT INTO T1(I2, I4, I1, I3) values (2, 2, 23, 1);
        INSERT INTO T2(I2, I4, I1, I3) values (0, 'aaaaa', 21, 2);
        INSERT INTO T2(I2, I4, I1, I3) values (1, 'bbbbb', 22, 2);
        INSERT INTO T2(I2, I4, I1, I3) values (2, 'bbbbb', 23, 2);
        
        SELECT 
               T1.I1 as T1_I1,
               T2.I4 as T2_I4
        FROM T1,
             T2
        WHERE T1.I4 = T2.I3
          and T1.I3 = 1
          and (
                (
                            T2.I1 = (SELECT /*+no_unnest */ max(b.I1)
                                           from T2 b
                                           where b.I1 <= 23
                                             and T2.I3 = b.I3)
                        and T1.I1 = (SELECT max(a.I1)
                                            from T1 a
                                            where a.I1 < 23
                                              and T1.I3 = a.I3
                                              and T1.I4 = a.I4)
                        and T1.I2 != 2
                        and T2.I2 != 2
                    )
                or (
                            T1.I1 = 23
                        and T2.I1 = 23
                        and T1.I2 = 2
                        and T2.I2 = 2
                    )
            );
        ```
        
    -   **Actual Results**
    
        ```sql
        T1_I1       T2_I4
        -------------------------
        21          aaaaa
        21          bbbbb
        23          bbbbb
        3 rows selected.
        ```
        
    -   **Expected Results**
    
        ```sql
        T1_I1       T2_I4
        -------------------------
        23          bbbbb
        1 row selected.
        ```
    
-   **Workaround**

    ```sql
    -- use hint /*+ no_unnest */ 
    select 
           T1.I1 as T1_I1,
           T2.I4 as T2_I4
    from T1,
         T2
    where T1.I4 = T2.I3
      and T1.I3 = 1
      and (
            (
                        T2.I1 = (select /*+no_unnest */ max(b.I1)
                                       from T2 b
                                       where b.I1 <= 23
                                         and T2.I3 = b.I3)
                    and T1.I1 = (select /*+no_unnest */ max(a.I1)
                                        from T1 a
                                        where a.I1 < 23
                                          and T1.I3 = a.I3
                                          and T1.I4 = a.I4)
                    and T1.I2 != 2
                    and T2.I2 != 2
                )
            or (
                        T1.I1 = 23
                    and T2.I1 = 23
                    and T1.I2 = 2
                    and T2.I2 = 2
                )
        );
    ```
    
-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50607<a name=bug-50607></a> Fixed the issue in PSM where recursive loops using LABEL and GOTO caused an infinite loop, preventing SQL Cancel from working.

-   **module** : qp-psm-trigger-execute

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed the issue where recursive loops implemented using LABEL and GOTO in PSM could cause a hang due to an infinite loop, and SQL Cancel would not work in this case.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

        BEGIN
          <>
          BEGIN
            GOTO L1;
          END;
        END;
        /

  -   **Actual Results**

  - **Expected Results**

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50617<a name=bug-50617></a> Fixed an issue where a SYNC Fail occurs when a conflict occurs and Replace operation is repeatedly performed during replication SYNC. 

-   **module** : rp-receiver

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : During replication SYNC, if continuous conflicts occur and the Replace operation is repeatedly performed, a SYNC failure may occur. This issue has now been fixed.
    
-   **How to reproduce this bug**

    -   **Reproduction conditions**

    -   **Actual Results**

    -   **Expected Results**

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50642<a name=bug-50642></a> Fixes the issue where the com.altibase.picl.LibLoader.OsNotSupportedException error occurred when running altiMon on Linux kernel 5.

-   **module** : ux-altiMon

-   **Category** : Usability

-   **Reproducibility** : Always

-   **Description** : Fixes the issue where the com.altibase.picl.LibLoader.OsNotSupportedException error occurred when running altiMon on Linux kernel 5. Now altiMon is able to run on Linux kernel 5 and above.
    
-   **How to reproduce this bug**

    -   **Reproduction conditions**

    -   **Actual Results**

    -   **Expected Results**

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 7.1.0.9.0        | 6.5.1                   | 8.11.1       | 7.1.7               | 7.4.7                        |

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

#### Changed Properties

#### Deleted Properties

### Performance Views

#### Added Performance Views

#### Changed Performance Views

#### Deleted Performance Views
