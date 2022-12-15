# Altibase 7.1.0.5.7 Patch Notes

<br/>

<br/>



# Table of Contents 

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [New Features](#new-features)
    - [BUG-48431 Improved JDBC driver performance by optimizing unnecessary communication protocols when using deferred prepare.](#bug-48431improved-jdbc-driver-performance-by-optimizing-unnecessary-communication-protocols-when-using-deferred-prepare)
    - [BUG-48515 Provides a function to limit the number of sessions from the same IP.](#bug-48515provides-a-function-to-limit-the-number-of-sessions-from-the-same-ip)
    - [BUG-48618 Add iSQL command line option -KEEP_SYSDBA.](#bug-48618add-isql-command-line-option--keep_sysdba)
    - [BUG-49028 Add replication syntax related to offline option in APRE C/C++ Precompiler and aexport.](#bug-49028add-replication-syntax-related-to-offline-option-in-apre-cc-precompiler-and-aexport)
    - [BUG-49032 In the Altibase replication environment, performance views have been added that allow you to check replication-related meta table information of remote servers.](#bug-49032in-the-altibase-replication-environment-performance-views-have-been-added-that-allow-you-to-check-replication-related-meta-table-information-of-remote-servers)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-48460 Altibase server startup fails at the undo stage during restart recovery due to tablespaces in the DISCARD state.](#bug-48460altibase-server-startup-fails-at-the-undo-stage-during-restart-recovery-due-to-tablespaces-in-the-discard-state)
    - [BUG-48523 If the statement object is not closed when the session ends, the Altibase server may terminate abnormally.](#bug-48523if-the-statement-object-is-not-closed-when-the-session-ends-the-altibase-server-may-terminate-abnormally)
    - [BUG-49029 If the OVER clause is omitted when using the COUNT KEEP function, the Altibase server may terminate abnormally.](#bug-49029if-the-over-clause-is-omitted-when-using-the-count-keep-function-the-altibase-server-may-terminate-abnormally)
    - [BUG-49031 Altibase server abnormally terminates when querying V$SNAPSHOT if there is a memory tablespace in the OFFLINE state.](#bug-49031altibase-server-abnormally-terminates-when-querying-vsnapshot-if-there-is-a-memory-tablespace-in-the-offline-state)
    - [BUG-49060 Change the permissions of the altibase_ipc.log file to -rw-r--r--.](#bug-49060change-the-permissions-of-the-altibase_ipclog-file-to--rw-r--r--)
    - [BUG-49061 Change the permissions of the syspassword file to -rw-r--r--.](#bug-49061change-the-permissions-of-the-syspassword-file-to--rw-r--r--)
    - [BUG-49062 When using sequences in a lookup transaction, a timeout error occurs and the session is terminated.](#bug-49062when-using-sequences-in-a-lookup-transaction-a-timeout-error-occurs-and-the-session-is-terminated)
    - [BUG-49071 When adding a replication target to a replication object, an incorrect error message occurs if the object owner name is incorrect.](#bug-49071when-adding-a-replication-target-to-a-replication-object-an-incorrect-error-message-occurs-if-the-object-owner-name-is-incorrect)
    - [BUG-49077 If the SELECT COUNT(*) statement is executed when the isolation level is REPEATABLE READ, an error(ERR-0109E: Internal server error.) occurs.](#bug-49077if-the-select-count-statement-is-executed-when-the-isolation-level-is-repeatable-read-an-errorerr-0109e-internal-server-error-occurs)
    - [BUG-49082 Roll back BUG-48523.](#bug-49082roll-back-bug-48523)
    - [BUG-49087 If an exception occurs when closing the JDBC connection object, the socket fd (file descriptor) is not cleaned up.](#bug-49087if-an-exception-occurs-when-closing-the-jdbc-connection-object-the-socket-fd-file-descriptor-is-not-cleaned-up)
    - [BUG-49095 Altibase server abnormally terminates when the reserved word _PROWID is used for a materialized view.](#bug-49095altibase-server-abnormally-terminates-when-the-reserved-word-_prowid-is-used-for-a-materialized-view)
    - [BUG-49106 Altibase server abnormally terminates when deleting a view table created using the UNION clause.](#bug-49106altibase-server-abnormally-terminates-when-deleting-a-view-table-created-using-the-union-clause)
    - [BUG-49107 Altibase server abnormally terminates under certain circumstances when performing HASH operation on DISK TEMP TABLE.](#bug-49107altibase-server-abnormally-terminates-under-certain-circumstances-when-performing-hash-operation-on-disk-temp-table)
    - [BUG-49109 A trace log is added to analyze the cause of the Altibase server abnormal termination that occurred during the operation of the garbage collection thread in the volatile table.](#bug-49109a-trace-log-is-added-to-analyze-the-cause-of-the-altibase-server-abnormal-termination-that-occurred-during-the-operation-of-the-garbage-collection-thread-in-the-volatile-table)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [Compatibility](#compatibility)
    - [Altibase Server Properties](#altibase-server-properties)
    - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-48431 Improved JDBC driver performance by optimizing unnecessary communication protocols when using deferred prepare.

-   **module** : mm-jdbc

-   **Category** : Enhancement

-   **Reproducibility** : Always

-   **Description** : Improved JDBC driver performance by optimizing unnecessary communication protocols when using deferred prepare. Altibase JDBC Driver needs to be patched to apply this bug.
    
-   **How to reproduce this bug**
    -   Reproduction conditions
        
    -   Actual Results
        
    -   Expected Results

-   **Workaround**

-   **Changes**
    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48515 Provides a function to limit the number of sessions from the same IP.

-   **module** : mm

-   **Category** : Functionality

-   **Reproducibility** : Always

- **Description** : Provides a function to limit the number of sessions of the same IP. This feature can be enabled by adding a "limit" entry to the ACCESS_LIST property.

  `ACCESS_LIST = operation, address, mask, [limit]`

  If the number of sessions accessed from *address* exceeds the *limit*, new connections are not allowed. At this time, on the Altibase client side, ERR-91015: Communication failure. An error occurs and connection to the Altibase server fails. And on the Altibase server side, the following message is left in the altibase_boot.log.
  
  ```bash
  ERR-410f0(errno=0) New connection try exceeds ACL limit: ( IP :192.168.1.203, ACL: 192.168.1.203, Limit : 2, Connected : 2 )
  Dispatcher callback failed
  ```
  
- **How to reproduce this bug**

  -   Reproduction conditions
  -   Actual Results
  -   Expected Results

-   **Workaround**

- **Changes**

  - Performance view
    - Changes in V$ACCESS_LIST

      Added LIMIT and CONNECTED columns.

      - LIMIT

        The maximum number of sessions that can access the Altibase server from the accessible IP address range specified in The maximum number of connected sessions.
        
      - CONNECTED
      
        Number of currently connected sessions corresponding to ACCESS_LIST.
      
    
  -   Property
      -   Changes in ACCESS_LIST
  
          Added limit items.
  
          `ACCESS_LIST = operation, address, mask, [limit]`
  
          limit is an optional item. Specifies the maximum number of sessions allowed to access the Altibase server from the accessible IP address range specified in ACCESS_LIST.
  
  - Compile Option
  
  - Error Code
  
    If you try to connect to the Altibase server by exceeding the set number of sessions, the following error message appears in the Altibase client.
  
    ```bash
    0x410FD ( 266493) mmERR_ABORT_IP_ACL_CONNECT_OVER New connection try exceeds ACL limit: ( IP : <0%s>, ACL: <1%s>, Limit : <2%d>, Connected : <3%d> ) 
    # *Cause: New connection try aborted because it exceeds access control list (ACL) limit.
    # *Action: Change the limit value of the ACCESS_LIST.
    ```
  
    

### BUG-48618 Add iSQL command line option -KEEP_SYSDBA.

-   **module** : ux-isql

-   **Category** : Usability

-   **Reproducibility** : Always

-   **Description** : Add -KEEP_SYSDBA option to maintain administrator mode when connecting to Altibase server in sysdba mode in iSQL. When executing the startup service command in sysdba mode, if the -KEEP_SYSDBA option is not used, the administrator mode is changed to normal user mode, and if the -KEEP_SYSDBA option is used, the administrator mode is maintained. The iSQL binary files need to be patched to reflect this bug.
    
-   **How to reproduce this bug**
    -   Reproduction conditions
    
    -   Actual Results
    
    -   Expected Results
    
-   **Workaround**

-   **Changes**
    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49028 Add replication syntax related to offline option in APRE C/C++ Precompiler and aexport.

-   **module** : rp

-   **Category** : Other

-   **Reproducibility** : Always

-   **Description** : Add replication syntax related to offline option in APRE C/C++ Precompiler and aexport. If you want to fix this bug, you need to patch apre and aexport .
    
    CREATE REPLICATION ala_replication_name FOR ANALYSIS OPTIONS **META_LOGGING**
    
    ​          WITH 'remote_host_ip', remote_host_port_no 
    
    ​          FROM user_name.table_name TO user_name.table_name;          
    
    ALTER REPLICATION ala_replication_name **BUILD OFFLINE META [AT SN(sn)]**;
    
    ALTER REPLICATION ala_replication_name **RESET OFFLINE META**;

-   **How to reproduce this bug**

    -   Reproduction conditions

    -   Actual Results

    -   Expected Results

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49032 In the Altibase replication environment, performance views have been added that allow you to check replication-related meta table information of remote servers.

-   **module** : rp

-   **Category** : Usability

-   **Reproducibility** : Always

-   **Description** : In the Altibase replication environment, 6 performance views have been added that allow you to check replication-related meta table information of remote servers. When replication does not operate normally, meta information errors can be checked. These performance views can only be queried from the server where the Receiver thread is running.
    
    - V$REPL_REMOTE_META_REPLICATIONS
    - V$REPL_REMOTE_META_ITEMS
    - V$REPL_REMOTE_META_COLUMNS
    - V$REPL_REMOTE_META_INDEX_COLUMNS
    - V$REPL_REMOTE_META_INDICES
    - V$REPL_REMOTE_META_CHECKS       
    
-   **How to reproduce this bug**

    -   Reproduction conditions

    -   Actual Results

    -   Expected Results

-   **Workaround**

- **Changes**

    - Performance view

      Six performance views have been added to check replication-related meta table information of remote servers.

      - V$REPL_REMOTE_META_REPLICATIONS
      
        Shows the information of the SYS_REPLICATIONS_ meta table, which records the replication-related information of the remote server.
      
      - V$REPL_REMOTE_META_ITEMS

        Shows the SYS_REPL_ITEMS_ meta table information that contains information related to the replication target table of the remote server.

      - V$REPL_REMOTE_META_COLUMNS

        Shows the SYS_REPL_OLD_COLUMNS_ meta table information that contains the information of the replication target column being replicated by the replication sender thread of the remote server.

      - V$REPL_REMOTE_META_INDEX_COLUMNS

        Shows the SYS_REPL_OLD_INDEX_COLUMNS_ meta table information, which contains the information of the replication target index column currently being used by the replication sender thread of the remote server.

      - V$REPL_REMOTE_META_INDICES

        Shows the information of the SYS_REPL_OLD_INDICES_ meta table that contains the information of the replication target index being replicated by the replication sender thread of the remote server.

      - V$REPL_REMOTE_META_CHECKS

        Shows information on the constraints of the replication table currently being replicated by the replication sender thread of the remote server.

    -   Property
        
    -   Compile Option
        
    -   Error Code

Fixed Bugs
==========

### BUG-48460 Altibase server startup fails at the undo stage during restart recovery due to tablespaces in the DISCARD state.

-   **module** : sm

-   **Category** : Fatal

-   **Reproducibility** : Rare

-   **Description** : Fixes a phenomenon in which the Altibase server fails to start at the undo stage during restart recovery due to a tablespace in DISCARD state.
    
-   **How to reproduce this bug**
    -   Reproduction conditions
        
    -   Actual Results
        
    -   Expected Results

-   **Workaround**

-   **Changes**
    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48523 If the statement object is not closed when the session ends, the Altibase server may terminate abnormally.

-   **module** : sm_transaction

-   **Category** : Fatal

-   **Reproducibility** : Rare

-   **Description** : Fixes a phenomenon in which the Altibase server abnormally terminates when the statement object is not terminated when the session is closed.
    
-   **How to reproduce this bug**

    -   Reproduction conditions

    -   Actual Results

    -   Expected Results

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49029 If the OVER clause is omitted when using the COUNT KEEP function, the Altibase server may terminate abnormally.

-   **module** : qp-select-pvo

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixes a phenomenon in which the Altibase server abnormally terminates when the OVER clause is omitted when using the COUNT KEEP function.
    
- **How to reproduce this bug**

  - Reproduction conditions

    ```sql
    DROP TABLE BUG_49029;
    CREATE TABLE BUG_49029 ( I1 VARCHAR(1000), I2 VARCHAR(1000), I3 VARCHAR(2000), PRIMARY KEY(I1));
    
    SELECT COUNT(I1) KEEP ( DENSE_RANK FIRST ORDER BY I2, I3 NULLS FIRST) 
      FROM BUG_49029;
    ```

  - Actual Results

    The error below occurs or the Altibase server abnormally terminates.

    ```
    ERR-31455 : Failed to work because an internal exception occurred from an OS.[Contact Altibase's Support Center]
    ```

  -   **Expected Results**

      ```sql
      COUNT(I1)KEEP(DENSE_RANKFIRSTORDERBYI2,I3N 
      ---------------------------------------------
      0                    
      1 row selected.
      ```

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49031 Altibase server abnormally terminates when querying V$SNAPSHOT if there is a memory tablespace in the OFFLINE state.

-   **module** : sm

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixes a phenomenon in which the ALTIBASE HDB server abnormally terminates when querying V$SNAPSHOT when there is a memory tablespace in the OFFLINE state.
    
-   **How to reproduce this bug**

    -   Reproduction conditions

    -   Actual Results

    -   Expected Results

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49060 Change the permissions of the altibase_ipc.log file to -rw-r--r--.

-   **module** : cm-ipc
-   **Category** : Maintainability
-   **Reproducibility** : Always
-   **Description**: Change the permissions of the $ALTIBASE_HOME/trc/altibase_ipc.log file to enhance database security.
    - Current : rw-rw-rw- 
    - Change : -rw-r--r--
-   **How to reproduce this bug**
-   Reproduction conditions
    
-   Actual Results
    
-   Expected Results
-   **Workaround**
-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49061 Change the permissions of the syspassword file to -rw-r--r--.

-   **module** : ux-isql
-   **Category** : Maintainability
-   **Reproducibility** : Always
-   **Description** : Change the permissions of the $ALTIBASE_HOME/conf/syspassword file to enhance database security.
    - Current : rw-rw-rw- 
    - Change : -rw-r--r--
-   **How to reproduce this bug**
    -   Reproduction conditions

    -   Actual Results

    -   Expected Results
-   **Workaround**
-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49062 When using sequences in a lookup transaction, a timeout error occurs and the session is terminated.

-   **module** : sm

-   **Category** : Functional Error

-   **Reproducibility** : Rare

-   **Description** : If the CACHE clause is used in creating/altering a sequence object, an UPDATE statement is executed internally when using a sequence. As a result, the lookup transaction performed by the user is changed to a change transaction, and the session is terminated due to UTRANS_TIMEOUT setting. Private properties must be applied to apply the fixed bug. If necessary, contact the Altibase Technical Support Center.
    
-   **How to reproduce this bug**

    -   Reproduction conditions

    -   Actual Results

    -   Expected Results

-   **Workaround**

- **Changes**

     -   Performance view
     - Property
       
     - Compile Option
     - Error Code

### BUG-49071 When adding a replication target to a replication object, an incorrect error message occurs if the object owner name is incorrect.

-   **module** : rp

-   **Category** : Message Error

-   **Reproducibility** : Always

-   **Description** : When adding a replication target to a replication object, the error message "The primary key column count of the replicated table does not match" occurs if the object owner name is incorrect. Modify the "The user name of the replicated table's owner does not match" error message appropriate for the situation.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    CREATE TABLE T1 (I1 INTEGER PRIMARY KEY, I2 INTEGER);
    CREATE TABLE T2 (I1 INTEGER, I2 INTEGER);
    ALTER TABLE T2 ADD CONSTRAINT PK_T2 PRIMARY KEY (I1, I2);
    CREATE REPLICATION REP1 WITH '127.0.0.1', 27172 FROM SYS.T1 TO SYS.T1;
    ALTER REPLICATION REP1 ADD TABLE FROM SYS.T2 TO SCOTT.T2;
    ALTER REPLICATION REP1 START;
    ```

  - **Actual Results**

    ```sql
    ERR-6100D : [Sender] Failed to handshake with the peer server (The primary key column count of the replicated table does not match [T1(1):T2(2)].)
    ```

  -   **Expected Results**

      ```sql
      ERR-6100D : [Sender] Failed to handshake with the peer server (The user name of the replicated table's owner does not match [T2(SYS):T2(SCOTT)].)
      ```

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49077 If the SELECT COUNT(*) statement is executed when the isolation level is REPEATABLE READ, an error(ERR-0109E: Internal server error.) occurs.

-   **module** : qp

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixes a bug where an error (ERR-0109E: Internal server error.) occurs when a SELECT COUNT(*) statement is executed while the isolation level is REPEATABLE READ.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    CREATE TABLE BUG_49077 ( IDX INTEGER , PARENT_IDX INTEGER ) TABLESPACE SYS_TBS_DISK_DATA;
    INSERT INTO BUG_49077 VALUES( 1, 0 );
    INSERT INTO BUG_49077 VALUES( 1, 0 );
    INSERT INTO BUG_49077 VALUES( 1, 0 );
    INSERT INTO BUG_49077 VALUES( 1, 0 );
    INSERT INTO BUG_49077 VALUES( 1, 0 );
    AUTOCOMMIT OFF;
    SET TRANSACTION ISOLATION LEVEL REPEATABLE READ;
    SELECT COUNT ( * ) FROM BUG_49077 WHERE IDX = 1;
    COMMIT;
    AUTOCOMMIT ON;
    ```

  - **Actual Results**

    ```sql
    iSQL> SELECT COUNT ( * ) FROM BUG_49077 WHERE IDX = 1;
    [ERR-0109E : Internal server error.]
    ```

  -   **Expected Results**

      ```sql
      iSQL> SELECT COUNT ( * ) FROM BUG_49077 WHERE IDX = 1;
      COUNT                
      -----------------------
      5                    
      1 row selected.
      ```

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49082 Roll back BUG-48523.

-   **module** : sm_transaction

-   **Category** : Fatal

-   **Reproducibility** : Rare

-   **Description** : A bug was found that caused the Altibase server to abnormally terminate due to BUG-48523, so BUG-48523 is rolled back.
    This bug has been exposed in the versions below.
    - Altibase 7.1.0.5.2 ~ 7.1.0.5.6
    
-   **How to reproduce this bug**
    -   Reproduction conditions
    
    -   Actual Results
    
    -   Expected Results
    
-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49087 If an exception occurs when closing the JDBC connection object, the socket fd (file descriptor) is not cleaned up.

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed a bug where the socket fd (file descriptor) was not cleaned up when an exception occurred when closing the JDBC connection object. If you want to reflect this bug, you need to patch the Altibase JDBC Driver.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```java
    AltibaseConnection sConn = (AltibaseConnection)getConnection("21165"); 
                       // First connection successful
    try
    {
        sConn.close(); // Exception thrown during close
    }
    catch (SQLException aEx)
    {
        System.out.println(aEx.getMessage());
    }
    CmChannel sChannel = sConn.channel();
    System.out.println("Socket FD ===>" + sChannel.getSocketFD()); 
                       // socket is not cleaned up, socket fd remains
    ```

  - **Actual Results**

    ```java
    Communication link failure: There was no response from the server, and the channel has reached end-of-stream.
    Socket FD ===>42
    ```

  -   **Expected Results**

      ```java
      Communication link failure: There was no response from the server, and the channel has reached end-of-stream.
      Exception in thread "main" java.sql.SQLException: Connection already closed.
      ```

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49095 Altibase server abnormally terminates when the reserved word _PROWID is used for a materialized view.

-   **module** : qp-dml-pvo

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : You cannot use the reserved word _PROWID in a materialized view, so Fixed an error message to occur.
    
    - Error message : ERR-31385: _PROWID is not supported.
    
- **How to reproduce this bug**

  - Reproduction conditions

    ```sql
    CREATE TABLE T1 (I1 INT, I2 INT);
    WITH W3 
    AS ( SELECT /*+ */ _PROWID AS i2 FROM T1 )
    SELECT E.I2, F.I2 FROM W3 E, W3 F;
    ```

  - Actual Results

    `ERR-91015 : Communication failure.` occurs and the Altibase server abnormally terminates or `ERR-31455 : Failed to work because an internal exception occurred from an OS.[Contact Altibase's Support Center]`error message occurs.

  -   Expected Results

      Since the _PROWID reserved word cannot be used, an error message must be displayed.
      
      ```sql
      ERR-31385 : _PROWID is not supported.
      ```

- **Workaround**

  You can avoid this bug by using the NO_MATERIALIZE hint.

  ```sql
  WITH W3 
  AS ( SELECT /*+ NO_MATERIALIZE */ _PROWID AS i2 FROM T1 )
  SELECT E.I2, F.I2 FROM W3 E, W3 F;
  I2                   I2                   
  ---------------------------------------------
  592710729729         592710729729         
  1 row selected.
  ```

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49106 Altibase server abnormally terminates when deleting a view table created using the UNION clause.

-   **module** : qp

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixed a bug so that the error message 'ERR-313A4: Cannot modify a column for a non key-preserved table' occurs because view tables using the UNION clause cannot be DELETE.
    
- **How to reproduce this bug**

  - Reproduction conditions

    ```sql
    CREATE TABLE M2 ( I1 INTEGER, I2 INTEGER );
    CREATE OR REPLACE VIEW V1 
    AS 
    SELECT * FROM M2 UNION SELECT * FROM M2;
    
    DELETE FROM V1 WHERE T2_I2=4;
    ```

  - Actual Results

    `ERR-91015 : Communication failure.` occurs and the Altibase server abnormally terminates or `ERR-31455 : Failed to work because an internal exception occurred from an OS.[Contact Altibase's Support Center]`error message occurs.

  -   Expected Results

      ```sql
      ERR-313A4 : Cannot modify a column for a non key-preserved table
      ```

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49107 Altibase server abnormally terminates under certain circumstances when performing HASH operation on DISK TEMP TABLE.

-   **module** : sm

-   **Category** : Fatal

-   **Reproducibility** : Unknown

-   **Description** : Avoid abnormal termination of the Altibase server under certain circumstances when performing HASH operation in DISK TEMP TABLE, and add a log to analyze the cause. When this bug occurs, the following log is left in altibase_dump.log. You need to apply private properties to leave logs. If necessary, contact the Altibase Technical Support Center.
    
    ```bash
    DUMP HASH WASEGMENT:
    WASegPtr              : 0x7fb19e2031d8
    SpaceID               : 4
    Type                  : 1 HASH
    HashSlotCount         : 65536
    InMemory              : OutMemory
    Unique                : 0
    OpenCursorType        : 0
    EndWPID               : 384
    InsertGroup BeginWPID : 128
    InsertGroup EndWPID   : 320
    InsertGroup ReuseWPID : 131
    FetchGroup BeginWPID  : 384
    FetchGroup EndWPID    : 384
    FetchGroup ReuseWPID  : 384
    SubHashGroup BeginWPID : 320
    SubHashGroup EndWPID   : 384
    SubHashGroup ReuseWPID : 352
    WAExtentListCount     : 8
    MaxWAExtentCount      : 6
    AllocWAPageCount      : 384
    NPageHashBucketCnt    : 384
    NPageCount            : 386
    SubHashPageCount      : 64
    SubHashBuildCount     : 3
    HashSlotPageCount     : 128
    ```

-   **How to reproduce this bug**

    -   Reproduction conditions

    -   Actual Results

    -   Expected Results

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    
-   Compile Option
    
- Error Code

### BUG-49109 A trace log is added to analyze the cause of the Altibase server abnormal termination that occurred during the operation of the garbage collection thread in the volatile table.

-   **module** : sm

-   **Category** : Fatal

-   **Reproducibility** : Rare

-   **Description** : A trace log is added to analyze the cause of the Altibase server abnormal termination that occurred during the operation of the garbage collection thread in the volatile table.
    
    When an abnormal termination of the Altibase server due to this bug occurs, the following log is output to altibase_error.log.

    ```bash
    smpFixedPageList::setFreeSlot
    CreateSCN    : ...
    LimitSCN      : ...
    NextOIDIsNULL : ...
    ```

-   **How to reproduce this bug**

    -   Reproduction conditions

    -   Actual Results

    -   Expected Results

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
|    7.1.0.5.7     |          6.5.1          |    8.9.1     |        7.1.7        |            7.4.6             |

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

- ACCESS_LIST

#### Deleted properties

### Performance Views

#### Added performance views

- V$REPL_REMOTE_META_REPLICATIONS

- V$REPL_REMOTE_META_ITEMS

- V$REPL_REMOTE_META_COLUMNS

- V$REPL_REMOTE_META_INDEX_COLUMNS

- V$REPL_REMOTE_META_INDICES

- V$REPL_REMOTE_META_CHECKS

#### Changed performance views

- V$ACCESS_LIST

#### Deleted performance views
