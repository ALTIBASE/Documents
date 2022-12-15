# Altibase 7.1.0.7.5 Patch Notes

<br/>

<br/>

# Table of Contents

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Fixed Bugs](#fixed-bugs)
    - [BUG-48279 Fixes an issue with updating the sender meta information file when processing DDL logs in offline replication.](#bug-48279fixes-an-issue-with-updating-the-sender-meta-information-file-when-processing-ddl-logs-in-offline-replication)
    - [BUG-48349 The SET BUCKET COUNT hint does not apply to SQL statements that use INTERSECT or MINUS among the set operators.](#bug-48349the-set-bucket-count-hint-does-not-apply-to-sql-statements-that-use-intersect-or-minus-among-the-set-operators)
    - [BUG-49642 Restart recovery may fail if the Altibase server is abnormally terminated while deleting and creating a tablespace at the same time.](#bug-49642restart-recovery-may-fail-if-the-altibase-server-is-abnormally-terminated-while-deleting-and-creating-a-tablespace-at-the-same-time)
    - [BUG-49643 Adds exception handling when executing a BEFORE UPDATE trigger on a table containing a LOB column.](#bug-49643adds-exception-handling-when-executing-a-before-update-trigger-on-a-table-containing-a-lob-column)
    - [BUG-49670 Altibase server may abnormally terminate when performing hard parsing again while executing SQL statements registered in the SQL Plan cache.](#bug-49670altibase-server-may-abnormally-terminate-when-performing-hard-parsing-again-while-executing-sql-statements-registered-in-the-sql-plan-cache)
    - [BUG-49682 Change exception handling when data of a different data type than the index key is entered into a function-based index.](#bug-49682change-exception-handling-when-data-of-a-different-data-type-than-the-index-key-is-entered-into-a-function-based-index)
    - [BUG-49686 File read error occurs when ALTER REPLICAITOIN replication_name BUILD OFFLINE META is executed.](#bug-49686file-read-error-occurs-when-alter-replicaitoin-replication_name-build-offline-meta-is-executed)
    - [BUG-49690 ALTER REPLICATION replication_name BUILD OFFLINE META When executing the META statement, the error message returned when the sender metafile or Restart SN file is invalid is improved.](#bug-49690alter-replication-replication_name-build-offline-meta-when-executing-the-meta-statement-the-error-message-returned-when-the-sender-metafile-or-restart-sn-file-is-invalid-is-improved)
    - [BUG-49696 Adds the function of backing up and restoring the segment header information file (txSegEntry.hdr) of the undo tablespace in the incremental backup.](#bug-49696adds-the-function-of-backing-up-and-restoring-the-segment-header-information-file-txsegentryhdr-of-the-undo-tablespace-in-the-incremental-backup)
    - [BUG-49697 Improved sender metafile creation process in offline redundancy to avoid possible loss of sender metafile and Restart SN file.](#bug-49697improved-sender-metafile-creation-process-in-offline-redundancy-to-avoid-possible-loss-of-sender-metafile-and-restart-sn-file)
    - [BUG-49706 Optimize the CSV parser for improved iLoader in performance.](#bug-49706optimize-the-csv-parser-for-improved-iloader-in-performance)
    - [BUG-49708 When index reorganization of a disk table is required by ALTER TABLE, the status of index activation is checked.](#bug-49708when-index-reorganization-of-a-disk-table-is-required-by-alter-table-the-status-of-index-activation-is-checked)
    - [BUG-49721 The Altibase server may abnormally terminate when executing a DDL statement that regenerates a table internally to a replication target table.](#bug-49721the-altibase-server-may-abnormally-terminate-when-executing-a-ddl-statement-that-regenerates-a-table-internally-to-a-replication-target-table)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [Altibase Server Properties](#altibase-server-properties)
    - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Fixed Bugs
==========

### BUG-48279 Fixes an issue with updating the sender meta information file when processing DDL logs in offline replication.

-   **module** : rp

-   **Category** : Functional Error

-   **Reproducibility** : Unknown

-   **Description** : Fixes an issue with updating the sender meta information file when processing DDL logs in offline replication.
    
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

### BUG-48349 The SET BUCKET COUNT hint does not apply to SQL statements that use INTERSECT or MINUS among the set operators.

-   **module** : qp

-   **Category** : Functionality

-   **Reproducibility** : Always

-   **Description** : Fixes an issue where the SET BUCKET COUNT hint is not applied to SQL statements using INTERSECT or MINUS among set operators.
    
-   **How to reproduce this bug**

    -   **Reproduction conditions**

            DROP TABLE t1 CASCADE;
            DROP TABLE t2 CASCADE;
            CREATE TABLE t1(i1 INTEGER);
            CREATE TABLE t2(i1 INTEGER) ;
            ALTER SESSION SET EXPLAIN PLAN = ON;
            ALTER SESSION SET TRCLOG_DETAIL_PREDICATE = 1;
            # INTERSECT
            SELECT /*+ set bucket count (256) hash bucket count (512) */ i1 FROM t1 INTERSECT SELECT i1 FROM t2;
            # MINUS
            SELECT /*+ set bucket count (256) hash bucket count (512) */ i1 FROM t1 MINUS SELECT i1 FROM t2;

    -   **Actual Results**

        -   INTERSECT operator

            ```
            SELECT /*+ set bucket count (256) hash bucket count (512) */ i1 FROM t1 INTERSECT SELECT i1 FROM t2;
            ------------------------------------------------------------
            PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: 236.82 )
             VIEW ( ACCESS: 0, COST: 236.16 )
              SET-INTERSECT ( ITEM_SIZE: 24, ITEM_COUNT: 0, BUCKET_COUNT: 512, ACCESS: 0, COST: 236.16 )
               PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: 118.08 )
                SCAN ( TABLE: SYS.T1, FULL SCAN, ACCESS: 0, COST: 116.76 )
               PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: 118.08 )
                SCAN ( TABLE: SYS.T2, FULL SCAN, ACCESS: 0, COST: 116.76 )
            ------------------------------------------------------------
            ```

        -   MINUS operator

            ```
            SELECT /*+ set bucket count (256) hash bucket count (512) */ i1 FROM t1 MINUS SELECT i1 FROM t2;
            ------------------------------------------------------------
            PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: 236.82 )
             VIEW ( ACCESS: 0, COST: 236.16 )
              SET-DIFFERENCE ( ITEM_SIZE: 24, ITEM_COUNT: 0, BUCKET_COUNT: 512, ACCESS: 0, COST: 236.16 )
               PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: 118.08 )
                SCAN ( TABLE: SYS.T1, FULL SCAN, ACCESS: 0, COST: 116.76 )
               PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: 118.08 )
                SCAN ( TABLE: SYS.T2, FULL SCAN, ACCESS: 0, COST: 116.76 )
            -----------------------------------------------------------
            ```

    -   **Expected Results**

        -   INTERSECT operator

            ```
            SELECT /*+ set bucket count (256) hash bucket count (512) */ i1 FROM t1 INTERSECT SELECT i1 FROM t2;
            ------------------------------------------------------------
            PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: 236.82 )
             VIEW ( ACCESS: 0, COST: 236.16 )
              SET-INTERSECT ( ITEM_SIZE: 24, ITEM_COUNT: 0, BUCKET_COUNT: 256, ACCESS: 0, COST: 236.16 )
               PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: 118.08 )
                SCAN ( TABLE: SYS.T1, FULL SCAN, ACCESS: 0, COST: 116.76 )
               PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: 118.08 )
                SCAN ( TABLE: SYS.T2, FULL SCAN, ACCESS: 0, COST: 116.76 )
            ------------------------------------------------------------
            ```

        -   MINUS operator

            ```
            SELECT /*+ set bucket count (256) hash bucket count (512) */ i1 FROM t1 MINUS SELECT i1 FROM t2;
            ------------------------------------------------------------
            PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: BLOCKED )
             VIEW ( ACCESS: 0, COST: BLOCKED )
              SET-DIFFERENCE ( ITEM_SIZE: BLOCKED, ITEM_COUNT: 0, BUCKET_COUNT: 256, ACCESS: 0, COST: BLOCKED )
               PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: BLOCKED )
                SCAN ( TABLE: SYS.T1, FULL SCAN, ACCESS: 0, COST: BLOCKED )
               PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: BLOCKED )
                SCAN ( TABLE: SYS.T2, FULL SCAN, ACCESS: 0, COST: BLOCKED )
            ------------------------------------------------------------
            ```

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49642 Restart recovery may fail if the Altibase server is abnormally terminated while deleting and creating a tablespace at the same time.

-   **module** : sm

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixes a phenomenon in which restart recovery fails when the Altibase server is started if the Altibase server is abnormally terminated while deleting and creating tablespaces are being performed at the same time.
    
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

### BUG-49643 Adds exception handling when executing a BEFORE UPDATE trigger on a table containing a LOB column.

-   **module** : qp-psm-trigger-execute

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixes the abnormal termination of the Altibase server when executing a BEFORE UPDATE trigger on a table that includes a LOB column, and adds restrictions related to LOB columns to the BEFORE UPDATE trigger.
    
-   **How to reproduce this bug**

    -   **Reproduction conditions**

            DROP TABLE T1;
            DROP TABLE T2;
             
            CREATE TABLE T1( I1 INTEGER, I3 CLOB ) ;
            CREATE TABLE T2( I1 INTEGER, I2 VARCHAR(10) );
             
            CREATE OR REPLACE TRIGGER TRIG1 
            BEFORE 
            UPDATE ON T1  
            REFERENCING NEW AS NEW_ROW OLD AS OLD_ROW 
            FOR EACH ROW 
            BEGIN :NEW_ROW.I1 := 100; 
            INSERT INTO T2 VALUES( :OLD_ROW.I1, 'OLD' ); 
            INSERT INTO T2 VALUES( :NEW_ROW.I1, 'NEW' ); 
            END;
            /
             
            INSERT INTO T1 SELECT LEVEL, LEVEL FROM DUAL CONNECT BY LEVEL <= 1;
            UPDATE T1 SET I1=I1+1;

    -   **Actual Results**

            ERR-91015 : Communication failure. 

    -   **Expected Results**

            ERR-3112F : Unsupported data type for parameter, RETURN, or local variable. LOB columns are not supported.

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49670 Altibase server may abnormally terminate when performing hard parsing again while executing SQL statements registered in the SQL Plan cache.

-   **module** : qp

-   **Category** : Fatal

-   **Reproducibility** : Unknown

-   **Description** : Fixes a phenomenon in which the Altibase server abnormally terminates due to a memory concurrency error during the Check-In PCO process when performing hard parsing again due to a change in bind variables during the execution of SQL statements registered in the SQL Plan Cache.
    
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

### BUG-49682 Change exception handling when data of a different data type than the index key is entered into a function-based index.

-   **module** : qp-non\_select

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : If data of a different data type than the index key is entered into a function-based index, the Altibase server may abnormally terminate. Change exception handling to return an error message.
    
-   **How to reproduce this bug**

    -   **Reproduction conditions**

            DROP TABLE T3;
            CREATE TABLE T3( I1 INTEGER, I2 VARCHAR(10) ) TABLESPACE SYS_TBS_DISK_DATA;
            CREATE INDEX T3_IDX11 ON T3( I1+1, I2+1 ) ;
            ALTER SESSION SET ARITHMETIC_OPERATION_MODE = 0;
            INSERT INTO T3 VALUES ( 5, 3 );

    -   **Actual Results**

            [ERR-91015 : Communication failure.]

    -   **Expected Results**

            iSQL> INSERT INTO T3 VALUES ( 5, 3 );
            [ERR-314AD : An error occurred while applying a value with an unexpected data type to the function-based index.]

-   **Workaround**

        ALTER SESSION SET ARITHMETIC_OPERATION_MODE = 1;

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code
        
        Added error messages.
        
        ```
        0x314AD ( 201901) qpERR_ABORT_QMC_INVALID_FUNCTION_BASED_INDEX An error occurred while applying a value with an unexpected data type to the function-based index. 
        # *Cause: The specified value does not match the data type of the function-based index column.
        # *Action: Rebuild the function-based index and retry.
        ```
        
        

### BUG-49686 File read error occurs when ALTER REPLICAITOIN replication_name BUILD OFFLINE META is executed.

-   **module** : rp-jdbcAdapter

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : If the ala_replication_name_META_NEW.bin or ala_replication_name_SN_NEW.bin file is abnormal, ALTER Fixes a phenomenon in which File read error occurs when REPLICAITOIN replication_name BUILD OFFLINE META is executed. If the backup file named OLD is OK, then BUILD OFFLINE META is performed by reading the backup file.
    
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

### BUG-49690 ALTER REPLICATION replication_name BUILD OFFLINE META When executing the META statement, the error message returned when the sender metafile or Restart SN file is invalid is improved.

-   **module** : rp-oraAdapter

-   **Category** : Usability

-   **Reproducibility** : Always

-   **Description** : ALTER REPLICATION replication_name BUILD OFFLINE META When executing the META statement, the error message returned when the sender metafile or Restart SN file is invalid is improved.
    
    If both sender metafiles (replication_name_META_NEW.bin, replication_name_META_OLD.bin) are invalid [ERR-611B3 : Invalid sender meta files. (Replication name: replication_name, File name: replication_name_META_NEW.bin, replication_name_META_OLD.bin )] error, if all Restart SN files are invalid [ERR-611B4 : Invalid Restart SN files. (Replication name: replication_name, File name: replication_name_SN_NEW.bin, replication_name_SN_OLD.bin )] Fixed to return an error.
    
-   **How to reproduce this bug**

    -   **Reproduction conditions**

    -   **Actual Results**

        - When both sender metafiles (replication_name_META_NEW.bin, replication_name_META_OLD.bin) are invalid

          ```
          ERR-611B3 : There is no valid meta file.
          ```

        - Restart SN when all files are invalid

          ```
          ERR-611B4 : There is no valid sn file.
          ```

    -   **Expected Results**

        -   When both sender metafiles (replication_name_META_NEW.bin, replication_name_META_OLD.bin) are invalid
        
            ```
            ERR-611B3 : Invalid sender meta files. (Replication name: replication_name, File name: replication_name_META_NEW.bin, replication_name_META_OLD.bin )
            ```
        
        -   Restart SN when all files are invalid
        
            ```
            ERR-611B4 : Invalid Restart SN files. (Replication name: replication_name, File name: replication_name_SN_NEW.bin, replication_name_SN_OLD.bin )
            ```

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code
        -   Added error messages.

            ```
            0x611B3 ( 397747) rpERR_ABORT_ERR_NO_VALID_METAFILE Invalid sender meta files. (Replication name: <0%s>, File name: <1%s>_META_NEW.bin, <2%s>_META_OLD.bin ) 
            # *Cause:
            # - Sender meta files do not exist or are invalid.
            # *Action:
            # - 'BUILD OFFLINE META' failed. Verify the altibase_rp.log.
            
            0x611B4 ( 397748) rpERR_ABORT_ERR_NO_VALID_SNFILE Invalid Restart SN files. (Replication name: <0%s>, File name: <1%s>_SN_NEW.bin, <2%s>_SN_OLD.bin ) 
            # *Cause:
            # - Restart SN files do not exist or are invalid.
            # *Action:
            # - 'BUILD OFFLINE META' failed. Verify the altibase_rp.log.
            ```
            


### BUG-49696 Adds the function of backing up and restoring the segment header information file (txSegEntry.hdr) of the undo tablespace in the incremental backup.

-   **module** : sm-disk-page

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Adds the function of backing up and restoring the segment header information file (txSegEntry.hdr) of the undo tablespace in the incremental backup.
    
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

### BUG-49697 Improved sender metafile creation process in offline redundancy to avoid possible loss of sender metafile and Restart SN file.

-   **module** : rp-oraAdapter

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Improved sender metafile creation process in offline redundancy to avoid possible loss of sender metafile and Restart SN file.
    
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

### BUG-49706 Optimize the CSV parser for improved iLoader in performance.

-   **module** : ux-iloader

-   **Category** : Efficiency

-   **Reproducibility** : Always

-   **Description** : Optimize the CSV parser for improved iLoader in performance.
    
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

### BUG-49708 When index reorganization of a disk table is required by ALTER TABLE, the status of index activation is checked.

-   **module** : sm

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixes a bug in which the Altibase server abnormally terminates when an index in an inactive state is executed when ALTER TABLE is executed. This happens when the table's indexes need to be reorganized internally, such as ALTER TABLE ~ ADD COLUMN .
    
    This bug only occurs with disk tables.
    
-   **How to reproduce this bug**

    -   **Reproduction conditions**

            DROP TABLE T1;
            CREATE TABLE T1 ( I1 INTEGER, I2 INTEGER, I3 INTEGER ) TABLESPACE SYS_TBS_DISK_DATA;
            ALTER TABLE T1 ALL INDEX DISABLE;
            CREATE INDEX IDX5 ON T1(I2, I3);
            ALTER TABLE T1 ADD COLUMN ( C3 VARCHAR(10) FIXED, C4 VARCHAR(10) VARIABLE );

    -   **Actual Results**

    -   **Expected Results**

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49721 The Altibase server may abnormally terminate when executing a DDL statement that regenerates a table internally to a replication target table.

-   **module** : sm

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixes an issue where the Altibase server abnormally terminates when executing a DDL statement that regenerates a table internally to a replication target table.

    This bug can occur on the active server when REPLICATION_DDL_ENABLE = 1 is set and operated in a replication environment, and it can also occur on the node where replication transactions occur when using the DDL replication function.

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
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    7.1.0.7.5     |          6.5.1          |    8.10.1    |        7.1.7        |            7.4.7             |

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
