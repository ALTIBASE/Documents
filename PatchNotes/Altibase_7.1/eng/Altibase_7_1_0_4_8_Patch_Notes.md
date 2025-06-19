Altibase 7.1.0.4.8 Patch Notes
==============================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [New Features](#new-features)
  - [BUG-46787 Improved error message logged in altibase_boot.log when a connection attempt is made from an IP address blocked by the ACL (Access Control List).](#bug-46787%C2%A0improved-error-message-logged-in-altibase_bootlog-when-a-connection-attempt-is-made-from-an-ip-address-blocked-by-the-acl-access-control-list)
  - [BUG-48208 Removed TIMESTAMP-related constraints in triggers and PSMs, enabling tables with TIMESTAMP columns to be included.](#bug-48208%C2%A0removed-timestamp-related-constraints-in-triggers-and-psms-enabling-tables-with-timestamp-columns-to-be-included)
  - [BUG-48230 Improved performance during parallel DEQUEUE execution.](#bug-48230%C2%A0improved-performance-during-parallel-dequeue-execution)
  - [BUG-48292 Added a log to oraAdapter.trc to record the last SN applied when oraAdapter is terminated.](#bug-48292%C2%A0added-a-log-to-oraadaptertrc-to-record-the-last-sn-applied-when-oraadapter-is-terminated)
- [Fixed Bugs](#fixed-bugs)
  - [BUG-48234 Fixed an issue with calculating the cost of processing a JOIN when a Recursive WITH statement includes a JOIN clause, causing the WITH statement to take longer to execute.](#bug-48234%C2%A0fixed-an-issue-with-calculating-the-cost-of-processing-a-join-when-a-recursive-with-statement-includes-a-join-clause-causing-the-with-statement-to-take-longer-to-execute)
  - [BUG-48253 Resolved an issue where performing another CLI function in the same session while waiting for a response from the Altibase server caused a hang.**module** : mm-cli](#bug-48253%C2%A0resolved-an-issue-where-performing-another-cli-function-in-the-same-session-while-waiting-for-a-response-from-the-altibase-server-caused-a-hangmodule--mm-cli)
  - [BUG-48273 Fixed an issue where the server could shut down unexpectedly during the aggregation function processing in the PIVOT clause.](#bug-48273%C2%A0fixed-an-issue-where-the-server-could-shut-down-unexpectedly-during-the-aggregation-function-processing-in-the-pivot-clause)
  - [BUG-48275 Fixed an issue where an incorrect error message was displayed during recovery when the __EMERGENCY_STARTUP_POLICY property was disabled.](#bug-48275%C2%A0fixed-an-issue-where-an-incorrect-error-message-was-displayed-during-recovery-when-the-__emergency_startup_policy-property-was-disabled)
  - [BUG-48280 Fixed an issue where a NullPointerException error occurred when executing a DEQUEUE statement using the executeQuery function.](#bug-48280-fixed-an-issue-where-a-nullpointerexception-error-occurred-when-executing-a-dequeue-statement-using-the-executequery-function)
  - [BUG-48287F ixed the issue where a hang occurs due to the REPLICATION_SYNC_LOG property in offline replication.](#bug-48287f-ixed-the-issue-where-a-hang-occurs-due-to-the-replication_sync_log-property-in-offline-replication)
  - [BUG-48299 Change the maximum number of columns allowed in a single SQL from 32,768 to 65,535.](#bug-48299%C2%A0change-the-maximum-number-of-columns-allowed-in-a-single-sql-from-32768-to-65535)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [Compatibility](#compatibility)
  - [Altibase Server Properties](#altibase-server-properties)
  - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
------------

### BUG-46787 Improved error message logged in altibase_boot.log when a connection attempt is made from an IP address blocked by the ACL (Access Control List).

-   **module** : mm

-   **Category** : Functionality

-   **Reproducibility** : Always

-   **Description** : The error message recorded in altibase_boot.log when attempting to connect to the Altibase server from a blocked IP address has been changed.
    
    The client IP address that attempted to connect after the ACL configuration is now included in the log.
    
    * Before
    
      ERR-410e9(errno=0) Connection is not permitted by the ACCESS\_LIST:0.0.0.0
    
    Dispatcher callback failed
    
    * After
    
      ERR-410e9(errno=0) Connection is not permitted by the ACCESS\_LIST:0.0.0.0 **( IP : *Client IP Address* )**
    
    Dispatcher callback failed    

- **How to reproduce this bug**

  -   **Reproduction conditions**

          1) altibase.properties
             ACCESS_LIST = DENY, 0.0.0.0, 0.0.0.0         # Block all access other than 127.0.0.1
          2) Attempting to connect from a blocked IP
             $ is -s 192.168.1.145 -port 20300
      
  - **Actual Results**

    ```bash
    ERR-410e9(errno=0) Connection is not permitted by the ACCESS_LIST: 0.0.0.0
    Dispatcher callback failed                                                                      
    ```
  
  -   **Expected Results**

      ```bash
      ERR-410e9(errno=0) Connection is not permitted by the ACCESS_LIST: 0.0.0.0 ( IP : Client IP Address )
      Dispatcher callback failed
      ```
  
-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48208 Removed TIMESTAMP-related constraints in triggers and PSMs, enabling tables with TIMESTAMP columns to be included.

-   **module** : qp-psm-trigger-pvo

-   **Category** : Enhancement

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where creating triggers and PSMs with tables containing TIMESTAMP columns resulted in **[ERR-31028: Unable to create a column with the specified data type]**. The TIMESTAMP-related constraints have been removed to allow trigger and PSM creation.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    DROP TRIGGER i3;
    DROP TABLE test_tri CASCADE;
    CREATE TABLE test_tri (c1 INTEGER, c2 TIMESTAMP);
    CREATE TRIGGER i3
    BEFORE INSERT ON test_tri
    REFERENCING NEW ROW NEW_ROW
    FOR EACH ROW
    AS BEGIN
    NEW_ROW.c2 := '2020100500' ;
    END;
    /
    ```

  - **Actual Results**

    ```sql
    [ERR-31028 : Unable to create a column with the specified data type.
    In trigger SYS.I3
    0003 : referencing new row NEW_ROW
                              ^      ^
    ]
    ```

  -   **Expected Results**

      ```SQL
      Create success.
      ```

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48230 Improved performance during parallel DEQUEUE execution.

-   **module** : sm

-   **Category** : Enhancement

-   **Reproducibility** : Always

-   **Description** : Improved performance during parallel DEQUEUE execution when more than 8 clients are involved.
    
    Eliminated bottlenecks in parallel DEQUEUE processing to enhance performance.
    
    Disk QUEUE table support has been discontinued.
    
    After applying this patch, the following error will occur when specifying a disk tablespace in the CREATE QUEUE statement: ERR-311E5: The table is not a memory or volatile table.
    
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

### BUG-48292 Added a log to oraAdapter.trc to record the last SN applied when oraAdapter is terminated.

-   **module** : rp-oraAdapter

-   **Category** : Enhancement

-   **Reproducibility** : Always

-   **Description** : Added a log in oraAdapter.trc to record the last applied SN, addressing the issue where the last applied SN could not be confirmed when oraAdapter terminates due to an Altibase server failure.
    
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

Fixed Bugs
----------

### BUG-48234 Fixed an issue with calculating the cost of processing a JOIN when a Recursive WITH statement includes a JOIN clause, causing the WITH statement to take longer to execute.

-   **module** : qp-dml-execute

-   **Category** : Efficiency

-   **Reproducibility** : Always

-   **Description** : Fixed an issue with calculating the cost of processing a JOIN when a Recursive WITH statement includes a JOIN clause, causing the WITH statement to take longer to execute.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    DROP TABLE pm_eq_dtl;
    CREATE TABLE pm_eq_dtl 
    (
        company_cd      VARCHAR(28)     FIXED, 
        eqp_cd          VARCHAR(200)    VARIABLE, 
        vlid_to_dt      VARCHAR(32)     VARIABLE, 
        vlid_from_dt    VARCHAR(32)     VARIABLE, 
        eqp_tab_no_dc   VARCHAR(400)    VARIABLE, 
        plant_cd        VARCHAR(28)     FIXED, 
        plan_plant_cd   VARCHAR(28)     FIXED, 
        plangrp_cd      VARCHAR(28)     FIXED, 
        wc_cd           VARCHAR(28)     FIXED, 
        maint_wc_cd     VARCHAR(28)     FIXED, 
        wc_plant_cd     VARCHAR(28)     FIXED, 
        up_eqp_cd       VARCHAR(28)     FIXED 
    );
    ALTER TABLE pm_eq_dtl ADD PRIMARY KEY (company_cd, eqp_cd, vlid_to_dt);
    
    INSERT INTO pm_eq_dtl (company_cd, eqp_cd, vlid_to_dt, up_eqp_cd)
    SELECT '1000', LEVEL, '99991231', NULL FROM DUAL CONNECT BY LEVEL < 16317;
    
    INSERT INTO pm_eq_dtl (company_cd, eqp_cd, vlid_to_dt, up_eqp_cd)
    SELECT '1000', LEVEL*100000, '99991231', LEVEL FROM DUAL CONNECT BY LEVEL < 143358;
    
    WITH cte_lvl(company_cd, eqp_cd, lvl) 
    AS
    (SELECT company_cd, eqp_cd, 6 lvl
       FROM pm_eq_dtl
      WHERE company_cd = '1000'
        AND vlid_to_dt = '99991231'
        AND up_eqp_cd IS NULL
      UNION ALL
     SELECT a.company_cd, a.eqp_cd, b.lvl+1 lvl
       FROM pm_eq_dtl a INNER JOIN cte_lvl b ON b.company_cd = a.company_cd
        AND b.eqp_cd = a.up_eqp_cd
      WHERE a.company_cd = '1000'
        AND a.vlid_to_dt = '99991231'
        AND a.up_eqp_cd IS NOT NULL 
    ) 
    SELECT COUNT(*) FROM cte_lvl;
    ```

  -   **Actual Results**

  -   **Expected Results**

      ```sql
      COUNT(*)             
      -----------------------
      32633
      ```
  
- **Workaround**

  ```sql
  WITH cte_lvl(company_cd, eqp_cd, lvl) 
  AS
  (SELECT company_cd, eqp_cd, 6 lvl
     FROM pm_eq_dtl
    WHERE company_cd = '1000'
      AND vlid_to_dt = '99991231'
      AND up_eqp_cd IS NULL
    UNION ALL
   SELECT /*+ USE_HASH(a, b) */ a.company_cd, a.eqp_cd, b.lvl+1 lvl
     FROM pm_eq_dtl a INNER JOIN cte_lvl b ON b.company_cd = a.company_cd
      AND b.eqp_cd = a.up_eqp_cd
    WHERE a.company_cd = '1000'
      AND a.vlid_to_dt = '99991231'
      AND a.up_eqp_cd IS NOT NULL 
  ) 
  SELECT COUNT(*) FROM cte_lvl;
  ```

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48253 Resolved an issue where performing another CLI function in the same session while waiting for a response from the Altibase server caused a hang.**module** : mm-cli

-   **Category** : Functionality

-   **Reproducibility** : Always

-   **Description** : Resolved an issue where performing another CLI function in the same session while waiting for a response from the Altibase server caused a hang.
    
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
        -   New
            -   ERR-51099 Lock sequence error. 
            -   Cause: invalid Lock call sequence.
            -   Action: Try disconnect and reconnect 

### BUG-48273 Fixed an issue where the server could shut down unexpectedly during the aggregation function processing in the PIVOT clause.

-   **module** : qp-select-execute

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where the server could shut down unexpectedly during the aggregation function processing in the PIVOT clause.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    DROP TABLE t14;
    CREATE TABLE t14 (
    rslt_reprt_pk   NUMERIC(22),
    evl_score       VARCHAR(5),
    chklist_item_pk NUMERIC(22)
    ) TABLESPACE SYS_TBS_DISK_DATA;
    
    INSERT INTO t14 VALUES( 205, '1', 135);
    INSERT INTO t14 VALUES( 205, NULL, 1349);
    INSERT INTO t14 VALUES( 205, NULL, 1340);
    INSERT INTO t14 VALUES( 205, NULL, 1341);
    INSERT INTO t14 VALUES( 205, '1', 134);
    INSERT INTO t14 VALUES( 205, NULL, 1339);
    INSERT INTO t14 VALUES( 205, NULL, 1330);
    INSERT INTO t14 VALUES( 205, NULL, 1331);
    INSERT INTO t14 VALUES( 205, '1', 133);
    INSERT INTO t14 VALUES( 205, NULL, 1329);
    INSERT INTO t14 VALUES( 205, NULL, 1320);
    INSERT INTO t14 VALUES( 205, NULL, 1321);
    INSERT INTO t14 VALUES( 205, '1', 132);
    INSERT INTO t14 VALUES( 205, NULL, 1319);
    INSERT INTO t14 VALUES( 205, NULL, 1310);
    INSERT INTO t14 VALUES( 205, NULL, 1311);
    INSERT INTO t14 VALUES( 205, '1', 131);
    INSERT INTO t14 VALUES( 205, 'A', 13);
    INSERT INTO t14 VALUES( 205, NULL, 1269);
    INSERT INTO t14 VALUES( 205, NULL, 1260);
    
    DROP TABLE t24;
    CREATE TABLE t24 (
    rslt_reprt_pk       NUMERIC(22),
    chk_oprtn_pk        NUMERIC(22),
    last_trsct_sttus_cd VARCHAR(2)
    ) TABLESPACE SYS_TBS_DISK_DATA;
    
    INSERT INTO t24 VALUES(196, 612, '02');
    INSERT INTO t24 VALUES(203, 683, '02');
    INSERT INTO t24 VALUES(205, 717, '07');
    INSERT INTO t24 VALUES(224, 726, '03');
    INSERT INTO t24 VALUES(232, 751, '02');
    INSERT INTO t24 VALUES(243, 808, '02');
    INSERT INTO t24 VALUES(251, 811, '05');
    INSERT INTO t24 VALUES(314, 1002, '03');
    INSERT INTO t24 VALUES(345, 937, '02');
    INSERT INTO t24 VALUES(347, 933, '02');
    INSERT INTO t24 VALUES(353, 820, '02');
    INSERT INTO t24 VALUES(356, 819, '03');
    INSERT INTO t24 VALUES(357, 999, '02');
    INSERT INTO t24 VALUES(363, 998, '03');
    INSERT INTO t24 VALUES(365, 959, '02');
    INSERT INTO t24 VALUES(386, 951, '02');
    INSERT INTO t24 VALUES(388, 994, '02');
    INSERT INTO t24 VALUES(182, 596, '06');
    INSERT INTO t24 VALUES(208, 729, '08');
    INSERT INTO t24 VALUES(247, 815, '06');
    
    DROP TABLE t34;
    CREATE TABLE t34 (
    rslt_reprt_pk NUMERIC(22)
    ) TABLESPACE SYS_TBS_DISK_DATA;
    INSERT INTO t34 VALUES(196);
    INSERT INTO t34 VALUES(203);
    INSERT INTO t34 VALUES(205);
    INSERT INTO t34 VALUES(205);
    INSERT INTO t34 VALUES(205);
    INSERT INTO t34 VALUES(224);
    
    SELECT /*+ USE_HASH( t34, tt4 ) */ * 
      FROM t34, 
           (SELECT *
              FROM (SELECT a.rslt_reprt_pk,
                           a.chklist_item_pk,
                           a.evl_score,
                           b.chk_oprtn_pk
                      FROM t14 a ,
                           t24 b
                     WHERE a.rslt_reprt_pk = b.rslt_reprt_pk
                       AND b.last_trsct_sttus_cd = '07'
                   ) 
             PIVOT ( MAX(evl_score) FOR chklist_item_pk IN (
             11, 111, 112, 113, 114, 115, 12, 124, 121, 122, 123, 125, 126, 13, 134, 136, 135, 133, 132, 131,
             22, 221, 222, 223, 23, 233, 234, 231, 232, 21, 211, 212,      
             32, 321, 322, 31, 311, 41, 411, 414, 413, 412, 42, 424, 421, 423, 422, 43, 431,
             52, 521, 522, 523, 53, 533, 534, 532, 531, 51, 511, 512, 513))
           ) tt4
      WHERE t34.rslt_reprt_pk = tt4.rslt_reprt_pk
    ;
    ```

  -   **Actual Results**

          Server shut down

  -   **Expected Results**

      ```SQL
      RSLT_REPRT_PK RSLT_REPRT_PK CHK_OPRTN_PK 11          111         112         113         114         115         12          124         121         122         123         125         126         13          134         136         135         133         132         131         22          221         222         223         23          233         234         231         232         21          211         212         32          321         322         31          311         41          411         414         413         412         42          424         421         423         422         43          431         52          521         522         523         53          533         534         532         531         51          511         512         513         
      -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
      205         205         717                                                                                                                                                                     A           1                       1           1           1           1                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
      205         205         717                                                                                                                                                                     A           1                       1           1           1           1                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
      205         205         717                                                                                                                                                                     A           1                       1           1           1           1                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
      3 rows selected.
      ```

- **Workaround**

  ```sql
  change hint
  /*+ USE_HASH( t34, tt4 ) */ to /*+ USE_HASH( tt4, t34  ) */
  ```

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48275 Fixed an issue where an incorrect error message was displayed during recovery when the __EMERGENCY_STARTUP_POLICY property was disabled.

-   **module** : sm\_recovery

-   **Category** : Message Error

-   **Reproducibility** : Rare

-   **Description** : Fixed an issue where an incorrect error message was displayed during recovery when the __EMERGENCY_STARTUP_POLICY property was disabled.
    
- **How to reproduce this bug**
  -   **Reproduction conditions**
      
  -   **Actual Results**
      
  -   **Expected Results**

-   **Workaround**

- **Changes**

-   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48280 Fixed an issue where a NullPointerException error occurred when executing a DEQUEUE statement using the executeQuery function.

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where a NullPointerException error occurred when executing a DEQUEUE statement using the executeQuery function. To apply this bug fix, the Altibase JDBC driver must be patched to version 7.1.0.4.8 or higher.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```java
    CREATE QUEUE q1 (c1 INTEGER, c2 VARCHAR(10));
    [THREAD1]
    Connection sConn = getConnection();
    Statement sStmt = sConn.createStatement();
    ResultSet sRs = sStmt.executeQuery("DEQUEUE c1, c2 FROM q1 WAIT 10");
    while( sRS.next() )
    {
        System.out.println( "  EmpName : " + sRS.getInt(1) + " " + sRS.getString(2) );
    }
    [THREAD2]
    ENQUEUE INTO q1(c1, c2) VALUES (1, 'AAA');
    ```

  - **Actual Results**

    ```java
    Exception in thread "main" java.lang.NullPointerException    
    at Altibase.jdbc.driver.datatype.RowHandle.initToStore(RowHandle.java:71)   
    at Altibase.jdbc.driver.AltibaseForwardOnlyResultSet.next(AltibaseForwardOnlyResultSet.java:264)    
    at DequeueTest.main(DequeueTest.java:59)
    ```

  -   **Expected Results**

      ```JAVA
      EmpName : 1 aaa
      ```

-   **Workaround**

        perform a DEQUEUE statement using the execute() and getResultSet() methods.

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48287F ixed the issue where a hang occurs due to the REPLICATION_SYNC_LOG property in offline replication.

-   **module** : rp

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed the issue where a hang occurs due to the REPLICATION_SYNC_LOG property in offline replication. The REPLICATION_SYNC_LOG property will no longer affect offline replication.
    
-   **How to reproduce this bug**

    -   **Reproduction conditions**

    -   **Actual Results**
    
    -   **Expected Results**
    
-   **Workaround**

        Set REPLICATION_SYNC_LOG to 0.

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48299 Change the maximum number of columns allowed in a single SQL from 32,768 to 65,535.

-   **module** : qp-select-pvo

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Change the maximum number of columns allowed in a single SQL from 32,768 to 65,535.
    
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

Changes
-------

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    7.1.0.4.8     |          6.5.1          |    8.9.1     |        7.1.7        |            7.4.6             |

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
