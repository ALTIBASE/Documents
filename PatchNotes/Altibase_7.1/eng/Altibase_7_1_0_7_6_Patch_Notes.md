# Altibase 7.1.0.7.6 Patch Notes

<br/>

<br/>

# **Table of Contents** 

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [New Features](#new-features)
    - [BUG-49645 Adds the ability to assign static IP addresses to duplicate senders.](#bug-49645adds-the-ability-to-assign-static-ip-addresses-to-duplicate-senders)
    - [BUG-49747 Adds the ability to set the same cost calculation formula as the Altibase 6.3.1 optimizer in Altibase 7 or later.](#bug-49747adds-the-ability-to-set-the-same-cost-calculation-formula-as-the-altibase-631-optimizer-in-altibase-7-or-later)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-49451 [ERR-31248: Mismatched bind column count] error occurs when a host variable or local variable is used in the LOOP clause of an SQL statement used in a stored procedure body.](#bug-49451err-31248-mismatched-bind-column-count-error-occurs-when-a-host-variable-or-local-variable-is-used-in-the-loop-clause-of-an-sql-statement-used-in-a-stored-procedure-body)
    - [BUG-49556 If parameter information is retrieved using the ParameterMetaData method without setting the parameter value, a NullPointerException error occurs.](#bug-49556if-parameter-information-is-retrieved-using-the-parametermetadata-method-without-setting-the-parameter-value-a-nullpointerexception-error-occurs)
    - [BUG-49573 Improves a memory error that occurs when a function-based index is used on the target table and a subquery is used in the SET clause in the multiple update statement.](#bug-49573improves-a-memory-error-that-occurs-when-a-function-based-index-is-used-on-the-target-table-and-a-subquery-is-used-in-the-set-clause-in-the-multiple-update-statement)
    - [BUG-49690 ALTER REPLICATION replication_name BUILD OFFLINE META When executing the META statement, the error message returned when the sender metafile or Restart SN file is invalid is improved.](#bug-49690alter-replication-replication_name-build-offline-meta-when-executing-the-meta-statement-the-error-message-returned-when-the-sender-metafile-or-restart-sn-file-is-invalid-is-improved)
    - [BUG-49718 Adds exception handling when setting index statistics information for inactive indexes.](#bug-49718adds-exception-handling-when-setting-index-statistics-information-for-inactive-indexes)
    - [BUG-49722 Add exception handling when the PRIMARY KEY is different between replication target tables in SQL reflection mode and offline replication.](#bug-49722add-exception-handling-when-the-primary-key-is-different-between-replication-target-tables-in-sql-reflection-mode-and-offline-replication)
    - [BUG-49725 If replication SYNC operation fails due to failure to acquire table lock, [ERR-61152 (errno=16) Replication synchronization failed. Check whether the index on the remote server is consistent.] error occurs.](#bug-49725if-replication-sync-operation-fails-due-to-failure-to-acquire-table-lock-err-61152-errno16-replication-synchronization-failed-check-whether-the-index-on-the-remote-server-is-consistent-error-occurs)
    - [BUG-49728 In the process of inserting a disk index key, the index structure is changed to utilize the index node space, and the Altibase server abnormally terminates in the process of calculating the index key insertion position.](#bug-49728in-the-process-of-inserting-a-disk-index-key-the-index-structure-is-changed-to-utilize-the-index-node-space-and-the-altibase-server-abnormally-terminates-in-the-process-of-calculating-the-index-key-insertion-position)
    - [BUG-49739 A session that performed a CREATE AS SELECT statement using MERGE JOIN is not forced to close with SESSION CLOSE.](#bug-49739a-session-that-performed-a-create-as-select-statement-using-merge-join-is-not-forced-to-close-with-session-close)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [Altibase Server Properties](#altibase-server-properties)
    - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

<br/>

New Features
============

### BUG-49645 Adds the ability to assign static IP addresses to duplicate senders.

-   **module** : rp

-   **Category** : Enhancement

-   **Reproducibility** : Always

-   **Description** : Adds the ability to assign static IP addresses to duplicate senders. This function is provided for a special purpose, so if you want more details, please contact the Altibase Technical Support Center.
    
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

### BUG-49747 Adds the ability to set the same cost calculation formula as the Altibase 6.3.1 optimizer in Altibase 7 or later.

-   **module** : qp

-   **Category** : Other

-   **Reproducibility** : Always

-   **Description** : Adds the ability to set the same cost calculation formula as the Altibase 6.3.1 optimizer in Altibase 7 or later.

    This bug can be found by users who are major version upgrading from Altibase 6.3.1 to Altibase 7 or higher, and SQL execution performance becomes slower than Altibase 6.3.1 after upgrade. Altibase 7 version users do not need to know the content of this bug.

    For this bug, Altibase 7 and later use the cost calculation formula of the Altibase 6.3.1 optimizer, and tried to produce the same execution plan as Altibase 6.3.1 as much as possible. However, since the cost calculation formula, which is part of the optimizer, is identical, the difference between Altibase 6.3.1 and Altibase 7 can be analyzed except for the calculation formula.

    This function is provided for a special purpose, so if you want more details, please contact the Altibase Technical Support Center.

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

<br/>

Fixed Bugs
==========

### BUG-49451 [ERR-31248: Mismatched bind column count] error occurs when a host variable or local variable is used in the LOOP clause of an SQL statement used in a stored procedure body.

-   **module** : qp-psm-trigger-execute

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixes a problem that [ERR-31248: Mismatched bind column count] error occurs when using a host variable or local variable in the LOOP clause of an SQL statement used in a stored procedure body.
    
-   **How to reproduce this bug**

    -   **Reproduction conditions**

        ```sql
        VAR VAR1 INTEGER;
        VAR VAR2 INTEGER;
        EXEC :VAR2 := 1;
        
        BEGIN
          SELECT 1 INTO :VAR1 FROM DUAL LOOP :VAR2;
        END;
        /
        ```

    -   **Actual Results**

        ```sql
        iSQL> VAR VAR1 INTEGER;
        iSQL> VAR VAR2 INTEGER;
        iSQL> EXEC :VAR2 := 1;
        Execute success.
        iSQL>
        iSQL> BEGIN
            2   SELECT 1 INTO :VAR1 FROM DUAL LOOP :VAR2;
            3 END;
            4 /
        [ERR-31248 : Mismatched bind column count
        at "SYS.ANONYMOUS_BLOCK", line 2]
        iSQL>
        iSQL> PRINT VAR;
        [ HOST VARIABLE ]
        -------------------------------------------------------
        NAME                 TYPE                 VALUE
        -------------------------------------------------------
        VAR1                 INTEGER
        VAR2                 INTEGER              1            1
        ```

    -   **Expected Results**

        ```sql
        iSQL> VAR VAR1 INTEGER;
        iSQL> VAR VAR2 INTEGER;
        iSQL> EXEC :VAR2 := 1;
        Execute success.
        iSQL>
        iSQL> BEGIN
            2   SELECT 1 INTO :VAR1 FROM DUAL LOOP :VAR2;
            3 END;
            4 /
        Execute success.
        iSQL>
        iSQL> PRINT VAR;
        [ HOST VARIABLE ]
        -------------------------------------------------------
        NAME                 TYPE                 VALUE
        -------------------------------------------------------
        VAR1                 INTEGER              1
        VAR2                 INTEGER              1
        ```

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49556 If parameter information is retrieved using the ParameterMetaData method without setting the parameter value, a NullPointerException error occurs.

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Change PreparedStatement.getParameterMetaData() to work without setting parameter values.
    
    Depending on your Spring JDBC version, if you get this error, you need to set spring.jdbc.getParameterType.ignore value to true. You do not need to set spring.jdbc.getParameterType.ignore=true if you use the Altibase JDBC Driver corresponding to the version below.
    
    - Altibase 6.5.1.9.2 or higher
    
    - Altibase 7.1.0.7.6 or higher

-   **How to reproduce this bug**

    -   **Reproduction conditions**

        ```java
        CREATE TABLE t1 (c1 INT, c2 VARCHAR(10));
        
        Connection sConn = getConnection("20300");
        PreparedStatement sStmt = sConn.prepareStatement("INSERT INTO t1 VALUES (?, ?)");
        ParameterMetaData sMeta = sStmt.getParameterMetaData();
        System.out.println("parameter type===>" + sMeta.getParameterType(2));
        ```

    -   **Actual Results**

        ```java
        Exception in thread "main" java.lang.NullPointerException
        	at Altibase.jdbc.driver.AltibaseParameterMetaData.getParameterType(AltibaseParameterMetaData.java:66)
        	at ParameterBindingTest.doTest(ParameterBindingTest.java:16)
        	at ParameterBindingTest.main(ParameterBindingTest.java:8)
        ```

    -   **Expected Results**

        If the parameter metadata is retrieved normally and Spring JDBC, it is not necessary to set the value of spring.jdbc.getParameterType.ignore to true.

-   **Workaround**

    For Spring JDBC, set the value of spring.jdbc.getParameterType.ignore to true.

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49573 Improves a memory error that occurs when a function-based index is used on the target table and a subquery is used in the SET clause in the multiple update statement.

-   **module** : qp-dml-pvo

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Improves a phenomenon in which the Altibase server abnormally terminates due to a memory error when a function-based index is used on the target table in the multiple update statement and a subquery is used in the SET clause.
    
-   **How to reproduce this bug**

    -   **Reproduction conditions**

        ```sql
        CREATE TABLE T3( I1 VARCHAR, I2 VARCHAR, I3 VARCHAR, I4 VARCHAR ) ;
        CREATE TABLE T1 (I1 INTEGER, I2 INTEGER);
        CREATE TABLE T2 (I1 INTEGER, I2 INTEGER);
        
        CREATE INDEX T3_IDX28 ON T3( I3+2 DESC, I4||'C' DESC ) ;
        CREATE INDEX T3_IDX23 ON T3( I3+2, I4||'C' ) ;
        
        UPDATE T1 LEFT OUTER JOIN T3 ON T1.I1 = T3.I1 SET ( T1.I2, T3.I3 ) = ( SELECT 
        T2.I1, T2.I1 FROM T2 );
        
        INSERT INTO T1 VALUES (1, 2);
        ```

    -   **Actual Results**

            frequently fatal

    -   **Expected Results**

            no rows updated.
            1 rows inserted.

-   **Workaround**

    ```sql
    UPDATE T1 LEFT OUTER JOIN T3 ON T1.I1 = T3.I1
    SET T1.i2 = ( SELECT T2.I1 FROM T2 )
      , T3.i2 = ( SELECT T2.I1 FROM T2 );
    ```

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49690 ALTER REPLICATION replication_name BUILD OFFLINE META When executing the META statement, the error message returned when the sender metafile or Restart SN file is invalid is improved.

-   **module** : rp-oraAdapter

-   **Category** : Usability

-   **Reproducibility** : Always

-   **Description** : ALTER REPLICATION replication_name BUILD OFFLINE META When executing the META statement, the error message returned when the sender metafile or Restart SN file is invalid is improved.
    
-   **How to reproduce this bug**

    -   **Reproduction conditions**
    -   **Actual Results**
        -   When both sender metafiles are invalid
            -   ERR-611B3 : There is no valid meta file.

        -   Restart SN when all files are invalid
            -   ERR-611B4 : There is no valid sn file.
    -   **Expected Results**
        -   When both sender metafiles are invalid
            -   ERR-611B3 : Invalid sender meta files. (Replication name: *replication_name*, File name: *replication_name*_META_NEW.bin, *replication_name*_META_OLD.bin )
        -   Restart SN when all files are invalid
            -   ERR-611B4 : Invalid Restart SN files. (Replication name: *replication_name*, File name: *replication_name*_SN_NEW.bin, *replication_name*_SN_OLD.bin )

-   **Workaround**

-   **Changes**

    -   Performance view
    
    -   Property
    
    -   Compile Option
    
    -   Error Code
        -   Added error messages.
            
            ```
            0x611B3 ( 397747) rpERR_ABORT_ERR_NO_VALID_METAFILE Invalid sender meta files. (Replication name: <0%s>, File name: <1%s>META_NEW.bin, <2%s>META_OLD.bin ) 
            # *Cause:
            # - Sender meta files do not exist or are invalid.
            # *Action:
            # - 'BUILD OFFLINE META' failed. Verify the altibase_rp.log.
            ```
            
            ```
            0x611B4 ( 397748) rpERR_ABORT_ERR_NO_VALID_SNFILE Invalid Restart SN files. (Replication name: <0%s>, File name: <1%s>SN_NEW.bin, <2%s>SN_OLD.bin ) 
            # *Cause:
            # - Restart SN files do not exist or are invalid.
            # *Action:
            # - 'BUILD OFFLINE META' failed. Verify the altibase_rp.log.
            ```

### BUG-49718 Adds exception handling when setting index statistics information for inactive indexes.

-   **module** : sm

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixes a phenomenon in which the Altibase server abnormally terminates when index statistics information is set (SET_INDEX_STATS) for an index in an inactive state. Adds exception handling to ignore even if index statistics information is set in the case of an inactive index.
    
-   **How to reproduce this bug**

    -   **Reproduction conditions**

        ```sql
        DROP TABLE T1;
        CREATE TABLE T1 (I1 INTEGER);
        ALTER TABLE T1 ALL INDEX DISABLE;
        CREATE INDEX T1_IDX ON T1(I1);
        EXEC SET_INDEX_STATS('SYS', 'T1_IDX', NULL, NULL, 30, NULL, NULL, NULL, TRUE);
        ```

    -   **Actual Results**

        ```sql
        [ERR-91015 : Communication failure.]
        ```

    -   **Expected Results**

            Execute success.

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49722 Add exception handling when the PRIMARY KEY is different between replication target tables in SQL reflection mode and offline replication.

-   **module** : rp

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Exception handling is added for the following two situations where replication target tables succeed even though the PRIMARY KEY is different.
    
    - When replication is started in SQL reflection mode (REPLICATION_SQL_APPLY_ENABLE = 1)
    - When the Adapter performs BUILD OFFLINE META
    
    After reflecting this bug, the following error message occurs.
    
    - Example when replication is started in SQL reflection mode
    
      - replication sender side
    
        - At start of redundancy
    
          [ERR-6100D : [Sender] Failed to handshake with the peer server (The index column ID of the replicated table does not match. [*local_table_name*(Name:*local_index_name*, ID:*local_column_order*):*remote_table_name*(Name:*remote_index_name*, ID:*remote_column_order*)].)] error occurs.
    
        - sender side altibase_rp.log
          - ERR-6209b(errno=11) Replication meta is different
    
      - Replication receiver side altibase_rp.log
    
        ERR-610de(errno=11) NOT NULL constraints of the replicated table's column does not match. [*remote_table_name*.*remote_column_name*(*remote_column_attribute_flag*):*local_table_name*.*local_column_name*(*local_column_attribute_flag*)].
    
        ERR-610e8(errno=11) The index column ID of the replicated table does not match. [*remote_table_name*(Name:*remote_index_name*, ID:*remote_column_order*):*local_table_name*(Name:*local_index_name*, ID:*local_column_order*)].
    
        ERR-61031(errno=11) [Receiver] Meta information does not match
    
    Both local and remote servers must be patched for this bug to take effect.
    
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

### BUG-49725 If replication SYNC operation fails due to failure to acquire table lock, [ERR-61152 (errno=16) Replication synchronization failed. Check whether the index on the remote server is consistent.] error occurs.

-   **module** : rp

-   **Category** : Message Error

-   **Reproducibility** : Always

-   **Description** : If replication SYNC operation fails due to failure to acquire table lock, [ERR-61152 (errno=16) Replication synchronization failed. Check whether the index on the remote server is consistent.] error occurs. This bug has been fixed.
    
    ```bash
    [2022/05/12 01:11:18 B07A5858][PID:56396][Thread-70155392943552][LWP-56623]
    [SenderSyncParallel] Failed to lock table for replication synchronization. (User:user_name, Table:table_name, Partition:partition_name)
    [2022/05/12 01:11:18 B07A5859][PID:56396][Thread-70155392943552][LWP-56623]
    ERR-11075(errno=16) The transaction has exceeded the lock timeout specified by the user.
    
    [2022/05/12 01:11:18 B07A585A][PID:56396][Thread-70155392943552][LWP-56623]
    [SenderSyncParallel] Error in allocSCN()
    [2022/05/12 01:11:18 B07A585B][PID:56396][Thread-70155392943552][LWP-56623]
    [SenderSyncParallel] Error in syncParallel()
    [2022/05/12 01:11:18 B07A585C][PID:56396][Thread-70155392943552][LWP-56623]
    ERR-61011(errno=16) [Sender] Failed to start sync
    
    [2022/05/12 01:11:18 B07A585D][PID:56396][Thread-70155392943552][LWP-56623]
    ERR-61152(errno=16) Replication synchronization failed. Check whether the index on the remote server is consistent.
    
    [2022/05/12 01:11:18 B07A585E][PID:56396][Thread-70155392943552][LWP-56623]
    ERR-61011(errno=16) [Sender] Failed to start sync
    ```
    
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

### BUG-49728 In the process of inserting a disk index key, the index structure is changed to utilize the index node space, and the Altibase server abnormally terminates in the process of calculating the index key insertion position.

-   **module** : sm-disk-index

-   **Category** : Fatal

-   **Reproducibility** : Rare

-   **Description** : In the process of inserting a disk index key, the index structure is changed to utilize the space of the index node, and the Altibase server abnormally terminates in the process of calculating the index key insertion position.
    
    When an abnormal shutdown of the Altibase server occurs due to this bug, the following log is generated in altibase_error.log.

    ```bash
    -sdnRuntimeHeader (disk common)
    mTableTSID                : 45
    mIndexTSID                : 47
    mMetaRID                  : 667252498528
    mTableOID                 : 99865440
    mIndexID                  : 49577
    ...중략...
    
    BEGIN-STACK [NORMAL] ============================
    Caller[1] 000000010001D7A4      => .iduStack::dumpStack(const iduSignalDef*,siginfo_t*,ucontext_t*,idBool,char*,idBool)
    Caller[2] 0000000100026FEC      => .ideLog::writeErrorTraceInternal(unsigned int,ideLogModule,unsigned int,const char*,const char*,unsigned int,const char*,char*)
    Caller[3] 0000000100026D34      => .ideLog::writeErrorTrace(const char*,idBool,const char*,unsigned int,const char*,char*)
    Caller[4] 000000010001FDAC      => .ideLogError        
    Caller[5] 00000001007AAF50      => .sdnbBTree::findTargetKeyForDupKey(sdrMtx*,sdnbHeader*,sdnbStatistic*,sdnbKeyInfo*,sdpPhyPageHdr**,short*)
    ...중략...
    
    index TSID : 47, get page ID : 0
    IDE_ASSERT( 0 ), [sdnbModule.cpp:17227], errno=[16]
    errno=[16]
    ```

    This bug can be made less likely by reorganizing the index or doing ALTER INDEX index_name AGING. The index in question can be identified as mIndexID in altibase_error.log.
    
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

### BUG-49739 A session that performed a CREATE AS SELECT statement using MERGE JOIN is not forced to close with SESSION CLOSE.

-   **module** : qp

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixes a phenomenon in which a session that executes a CREATE AS SELECT statement using MERGE JOIN is not forcibly terminated with SESSION CLOSE.
    
-   **How to reproduce this bug**

    -   **Reproduction conditions**

        -   Session A

            ```sql
            CREATE TABLE T1 AS
            SELECT LEVEL AS C1, CAST('AAAAA' AS VARCHAR(10)) AS T1_CD
              FROM DUAL CONNECT BY LEVEL <= 7335;
              
             CREATE TABLE T2 AS 
            SELECT LEVEL AS C1, CAST('AAAAA' AS VARCHAR(10)) AS T2_CD
              FROM DUAL CONNECT BY LEVEL <= 10000;
              
             CREATE TABLE T3 AS 
            SELECT /*+ USE_MERGE (B A) */ A.*, B.T2_CD
              FROM T1 A INNER JOIN T2 B ON A.T1_CD = B.T2_CD
               AND B.T2_CD = 'AAAAA';
            ```

        - Session B 

          ```sql
          ALTER DATABASE database_name SESSION CLOSE session_id;
          ```

    -   **Actual Results**

            End the session after completing the table creation.

    -   **Expected Results**

            [ERR-01043 : The session has been closed by the server]

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

<br/>

Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    7.1.0.7.6     |          6.5.1          |    8.10.1    |        7.1.7        |            7.4.7             |

> You can check the module version change history in [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.1/Altibase_7_1_Version_Histories.md).

#### Compatibility

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
