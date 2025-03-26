# Altibase 7.1.0.10.0 Patch Notes

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [New Features](#new-features)
    - [BUG-48885 Statistics Locking feature Added](#bug-48885)
    - [BUG-51057 Support for Updatable Dynaset](#bug-51057)
    - [BUG-51068 Improved read performance of KEYSET DRIVEN cursors](#bug-51068)
    - [BUG-51199 Support for Red Hat Linux 9](#bug-51199)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-50650 Server Restart Failure Due to Unupdated Memory Recovery LSN During Checkpoint](#bug-50650)
    - [BUG-50757 In incremental backup, if both extend and change tracking are performed simultaneously, the server may shut down abnormally.](#bug-50757)
    - [BUG-50867 Fixed Logic Issue for Changing Tablespace to Offline](#bug-50867)
    - [BUG-50978 Fixed an issue with Authorization Check Logic During Trigger Creation](#bug-50978)
    - [BUG-51012 Fixed an issue where passing NULL as the SchemaName argument in the SQLColumns function resulted in incorrect data being returned.](#bug-51012)
    - [BUG-51013 Fixed Issue with Dynaset Testing Using ODBC Driver](#bug-51013)
    - [BUG-51203 Improve Handling of Long-Running Queries on Performance Views like V$DISK_UNDO_USAGE](#bug-51203)
    - [BUG-51041 Provide page dump and debugging code enhancement for handling corrupted disk pages.](#bug-51041)
    - [BUG-51048 Fix for Incorrect Data Returned with Repeated SQLExecute and SQLFetch Using SQL_CURSOR_KEYSET_DRIVEN Cursor](#bug-51048)
    - [BUG-51050 Fix invalid memory access issue during a Multiple Table Update on a table with a trigger set.](#bug-51050)
    - [BUG-51056 Fixes an error in the logic of performing an inplace update on a volatile table.](#bug-51056)
    - [BUG-51063 Fixes an error when performing an INPLACE UPDATE on a table where a memory index exists.](#bug-51063)
    - [BUG-51065 In replication SQL mode, DELETE statements executed before a partition SPLIT are not replicated.](#bug-51065)
    - [BUG-51133 Fixed Server Crash Due to Invalid Memory Reference During Memory Deallocation in SQL Prepare Phase](#bug-51133)
    - [BUG-51138 Improved to output an error message when exporting/importing data with more than 2,147,483,647 occurrences in a single file in the iloader.](#bug-51138)
    - [BUG-51144 Fixed an error [ERR-31014 : Index not found] during aexport when table owner and index owner were different with COLLECT_DBMS_STATS ON.](#bug-51144)
    - [BUG-51158 Fixes an issue where **[ERR-110C5: LobCursor already closed]** error occurs while processing a CLOB column using batchUpdate in a Prepared Statement.](#bug-51158)
    - [BUG-51160 Improved error handling when executing executeBatch() while inserting data into Oracle using JDBCadapter.](#bug-51160)
    - [BUG-51163 Fixed replication failure for tables with TableOID exceeding 2,147,483,647.](#bug-51163)
    - [BUG-51165 Improves behavior when updatedRowCount is 0 during CLOB column processing using batchUpdate in Prepared Statement.](#bug-51165)
    - [BUG-51189 Changes in DDL replication behavior.](#bug-51189)
    - [BUG-51214 Fixed an issue where an error occurred when granting permissions on individual objects using the SYS account.](#bug-51214)
    - [BUG-51216 Improved to display an error message if the Extent List traversal does not complete during internal processing.](#bug-51216)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [Compatibility](#compatibility)
    - [Altibase Server Properties](#altibase-server-properties)
    - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-48885<a name=bug-48885></a> Statistics Locking feature Added

-   **module** : sm

-   **Category** : Enhancement

-   **Reproducibility** : Always

-   **Description** : A feature to lock table statistics has been added. The `DBMS_STATS` package now includes the `LOCK_TABLE_STATS` and `UNLOCK_TABLE_STATS` procedures, which allow you to lock or unlock table statistics.
    
    If you attempt to gather statistics using GATHER\_TABLE\_STATS on a table with statistics locking enabled, you will encounter the error **[ERR-111C9 Table statistic(s) are
    locked.]**

-   **How to reproduce this bug**

    - **Reproduction conditions**
    - **Actual Results**
    - **Expected Results**
- **Workaround**

- **Changes**

    - Performance view

      -   V$LOCK_TABLE_STATS

          - Added columns

            | Column name | Type       | Description                                                  |
            | ----------- | ---------- | ------------------------------------------------------------ |
            | TABLE_OID   | BIGINT     | The table object identifier                                  |
            | STAT_LOCKED | VARCHAR(6) | Table statistics lock status</br> -NONE: Statistics are unlocked</br> -LOCKED: Statistics are locked |
      
    - Property

    - Compile Option

    - Error Code

      -   added message
          - **[ERR-111C9 Table statistic(s) are locked.]**
          - **Cause**: Table statistic(s) have been locked.
          - **Action**: Find the table whose statistic(s) are locked and then unlock the table using the UNLOCK_TABLE_STATS procedure.

### BUG-51057<a name=bug-51057></a> Support for Updatable Dynaset

-   **module** : mm-win-odbc

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : The ODBC driver has been improved to support Updatable Dynasets.

-   **How to reproduce this bug**
    - **Reproduction conditions**
    - **Actual Results**
    - **Expected Results**
    
-   **Workaround**

-   **Changes**
    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-51068<a name=bug-51068></a> Improved read performance of KEYSET DRIVEN cursors

-   **module** : mm-cli
-   **Category** : Enhancement
-   **Reproducibility** : Always
-   **Description** : The performance has been improved by reducing the number of server-client communications (fetch protocol) when performing a SELECT with the SQL_CURSOR_KEYSET_DRIVEN cursor.
-   **How to reproduce this bug**
- **Reproduction conditions**
    - **Actual Results**
- **Expected Results**
-   **Workaround**
-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-51199<a name=bug-51199></a> Support for Red Hat Linux 9

-   **module** : id

-   **Category** : Portability

-   **Reproducibility** : Unknown

-   **Description** : Compatibility issues that occurred in environments with glibc 2.34 or higher have been resolved. Altibase can now also be used on Red Hat Linux 9.  

-   **How to reproduce this bug**
    - **Reproduction conditions**
    - **Actual Results**
    - **Expected Results**
    
-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

Fixed Bugs
==========

### BUG-50650<a name=bug-50650></a> Server Restart Failure Due to Unupdated Memory Recovery LSN During Checkpoint

-   **module** : sm-mem-recovery

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : An issue was identified where, if the server was shut down after dirty pages were written to the checkpoint image file but before the Memory Recovery LSN was updated, the server would fail to restart due to recovery failure. 
    
    Now this issue has been fixed. Even if the server is shut down before the Memory Recovery LSN is updated, recovery will proceed normally during server restart.
    
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

### BUG-50757<a name=bug-50757></a> In incremental backup, if both extend and change tracking are performed simultaneously, the server may shut down abnormally.

-   **module** : sm\_resource

-   **Category** : Fatal

-   **Reproducibility** : Frequence

-   **Description** : An issue was identified where the server could shut down abnormally when both extend and change tracking were performed simultaneously during incremental backup. Now this issue has been fixed to prevent abnormal server shutdowns when both operations are executed concurrently.

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

### BUG-50867<a name=bug-50867></a> Fixed Logic Issue for Changing Tablespace to Offline

-   **module** : sm\_collection

-   **Category** : Fatal

-   **Reproducibility** : Rare

-   **Description** : The issue in the logic for changing the tablespace to offline has been fixed.

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

### BUG-50978<a name=bug-50978></a> Fixed an issue with Authorization Check Logic During Trigger Creation 

-   **module** : qp-ddl-dcl-execute

-   **Category** : Reliability

-   **Reproducibility** : Always

-   **Description** : The issue in the authorization check logic during trigger creation has been fixed.

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

### BUG-51012<a name=bug-51012></a> Fixed an issue where passing NULL as the SchemaName argument in the SQLColumns function resulted in incorrect data being returned.

-   **module** : mm-cli

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where passing NULL as the SchemaName argument in the SQLColumns function resulted in incorrect data being returned.
    
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

### BUG-51013<a name=bug-51013></a> Fixed Issue with Dynaset Testing Using ODBC Driver

-   **module** : mm-cli
-   **Category** : Functional Error
-   **Reproducibility** : Always
-   **Description** : An issue where the connection to the Altibase database was successful during a dynaset test using the ODBC driver, but an error occurred stating that dynasets were not supported, has been fixed. 
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

### BUG-51203<a name=bug-51203></a> Improve Handling of Long-Running Queries on Performance Views like V$DISK_UNDO_USAGE

-   **module** : sm-disk-collection
-   **Category** : Enhancement
-   **Reproducibility** : Rare
-   **Description** : A session check feature has been added for long-running queries on performance views like V$DISK_UNDO_USAGE. Now, if a session times out or is terminated with the session close command, it will be properly handled. This improvement has been applied to the following performance views as well.
    -   V$DATABASE
    -   V$DATAFILES
    -   V$LOCK_WAIT
    -   V$MEMTBL_INFO
    -   V$TABLESPACES
    -   V$TSSEGS

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

### BUG-51041<a name=bug-51041></a> Provide page dump and debugging code enhancement for handling corrupted disk pages.

-   **module** : sm

-   **Category** : Enhancement

-   **Reproducibility** : Unknown

-   **Description** : Page dump and debugging code enhancements have been implemented to better handle corrupted disk pages. These improvements ensure that when disk pages become corrupted, diagnostic information is captured, and the issue can be properly analyzed.
    
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

### BUG-51048<a name=bug-51048></a> Fix for Incorrect Data Returned with Repeated SQLExecute and SQLFetch Using SQL_CURSOR_KEYSET_DRIVEN Cursor

-   **module** : mm-cli

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where incorrect data was returned due to an internal error when repeatedly executing SQLExectue and SQLFetch with the SQL_CURSOR_KEYSET_DRIVEN cursor.
    
    We also fixed an error that returned success to the user even if an error occurred during the fetch process.
    
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
        -   추가
            -   **ERR-51229 Failed to add the PROWID to the hash table.**
            -   **Cause**: Failed to add the PROWID to the hash table due to an internal error.
            -   **Action**: Contact Altibase's Support Center ([http://support.altibase.com](http://support.altibase.com/)).

### BUG-51050<a name=bug-51050></a> Fix invalid memory access issue during a Multiple Table Update on a table with a trigger set.

-   **module** : qp

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixed the invalid memory access issue that occured during a Multiple Table Update on a table with a trigger set.

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

### BUG-51056<a name=bug-51056></a> Fixes an error in the logic of performing an inplace update on a volatile table.

-   **module** : sm\_page

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixes an error in the logic of performing an inplace update on a volatile table.

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

### BUG-51063<a name=bug-51063></a> Fixes an error when performing an INPLACE UPDATE on a table where a memory index exists.

-   **module** : sm-mem-index

-   **Category** : Functionality

-   **Reproducibility** : Always

-   **Description** : Fixes an error that caused some records not to be updated or incorrect records to be updated when performing an inplace update on a table with a memory index.

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

### BUG-51065<a name=bug-51065></a> In replication SQL mode, DELETE statements executed before a partition SPLIT are not replicated.

-   **module** : rp

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : In replication SQL mode, when a specific row in a replication target table is deleted and the partition is subsequently SPLIT, the deletion command for the specific row was not replicated, causing a data consistency issue. This issue has been fixed.
    
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

### BUG-51133<a name=bug-51133></a> Fixed Server Crash Due to Invalid Memory Reference During Memory Deallocation in SQL Prepare Phase

-   **module** : qp-select

-   **Category** : Enhancement

-   **Reproducibility** : Impossible

-   **Description** : Fixed an issue where an invalid memory reference during the memory release process in the SQL Prepare phase would cause a server crash, now outputting an error instead.
    
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

### BUG-51138<a name=bug-51138></a> Improved to output an error message when exporting/importing data with more than 2,147,483,647 occurrences in a single file in the iloader.

-   **module** : ux-iloader

-   **Category** : Functional Error

-   **Reproducibility** : Always

- **Description** : When exporting more than 2,147,483,647 data with the ILOADER, it was terminated without error. Also, when importing more than 2,147,483,647 data, only 2,147,483,647 data were imported, and it was terminated without error. 

  The number of data that can be processed when exporting/importing with the iloader is 2,147,483,647, and the following error message is now displayed when exporting/importing data that exceeds this limit.

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
        -   추가
            -   **[ERR-9114A : The datafile (data.txt) exceeded the maximum**
                **record limit (2,147,483,647), causing iLoader to terminate.]**
            -   **Cause** : The datafile contains more records than the allowed limit (2,147,483,647).
            -   **Action** : Split the datafile into smaller files and retry.

### BUG-51144<a name=bug-51144></a> Fixed an error [ERR-31014 : Index not found] during aexport when table owner and index owner were different with COLLECT_DBMS_STATS ON.

-   **module** : ux-aexport

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an issue that occurred when executing aexport with COLLECT_DBMS_STATS set to ON. When the table owner and index owner were different, an error **[ERR-31014: Index not found]** occurred while extracting index statistics information. This was causing aexport to terminate abnormally, and we have fixed it so that it is handled correctly.
    
- **How to reproduce this bug**

  -   **Reproduction conditions**

          CREATE USER alti IDENTIFIED BY test;
          CONNECT alti/test
          DROP TABLE t1;
          CREATE TABLE t1 (c1 INTEGER, c2 CHAR(10), c3 CHAR(10));
          CREATE INDEX t1_idx1 ON t1 (c1);
          
          CONNECT sys/manager
          CREATE INDEX alti.t1_idx2 ON alti.t1 (c2);
          CREATE INDEX t1_idx3 ON alti.t1 (c3);
          exec gather_database_stats(0.1,10,false);
          
          // Set COLLECT_DBMS_STATS = ON in the aexport.properties file
          
          $ aexport -u sys -p manager -s localhost
      
  - ****Actual Results****

        ##### TBS #####
        
        ##### USER  #####
        ** input user ALTI's password(default - same with USER_NAME):
        
        ##### SYNONYM #####
        
        ##### DIRECTORY #####
        
        ##### TABLE #####
        ** "ALTI"."T1"
        ... query[EXEC GET_INDEX_STATS('"ALTI"', '"T1_IDX1"', NULL, ?, ?, ?, ?, ?, ?,                          ?)]
        ... query[EXEC GET_INDEX_STATS('"ALTI"', '"T1_IDX2"', NULL, ?, ?, ?, ?, ?, ?,                          ?)]
        ... query[EXEC GET_INDEX_STATS('"ALTI"', '"T1_IDX3"', NULL, ?, ?, ?, ?, ?, ?,                          ?)]
        [ERR-31014 : Index not found]

  -   **Expected Results**

          without errors

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-51158<a name=bug-51158></a> Fixes an issue where **[ERR-110C5: LobCursor already closed]** error occurs while processing a CLOB column using batchUpdate in a Prepared Statement.

-   **module** : mm-jdbc
-   **Category** : Functional Error
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where, when executing `executeUpdate()` on a CLOB column using a Prepared Statement, encountering a Primary Key duplication error and then re-executing `executeUpdate()` would result in **[ERR-110C5: LobCursor already closed]**.
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

### BUG-51160<a name=bug-51160></a> Improved error handling when executing executeBatch() while inserting data into Oracle using JDBCadapter.

-   **module** : rp-jdbcAdapter

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : When an error occurs while performing Batch DMLs, improve to log the DMLs that failed and the DMLs that were not processed. Also, improve to not log an error if the value returned by the BatchUpdateException.getUpdateCounts() method is SUCCESS_NO_INFO.
    
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

### BUG-51163<a name=bug-51163></a> Fixed replication failure for tables with TableOID exceeding 2,147,483,647.

-   **module** : rp

-   **Category** : Functional Error

-   **Reproducibility** : Rare

-   **Description** : Fixed an issue where adding a table with a TableOID value greater than 2,147,483,647 to a replication target table would fail with the error **[ERR-21010 Value overflow]**.
    
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

### BUG-51165<a name=bug-51165></a> Improves behavior when updatedRowCount is 0 during CLOB column processing using batchUpdate in Prepared Statement.

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Improves behavior when updatedRowCount is 0 during CLOB column processing using batchUpdate in Prepared Statement.

-   **How to reproduce this bug**

    - **Reproduction conditions**

      **Actual Results**

      **Expected Results**

-   **Workaround**

-   **Changes**

    -   Performance view
        
    -   Property
    -   Compile Option
    -   Error Code

### BUG-51189<a name=bug-51189></a> Changes in DDL replication behavior.

-   **module** : rp

-   **Category** : Other

-   **Reproducibility** : Always

-   **Description** : SPLIT/MERGE/DROP PARTITION can be executed on the replication target table without using the LOCK TABLE ... IN EXCLUSIVE MODE UNTIL NEXT DDL syntax. 
    
    Additionally, the behavior of `DROP PARTITON` on a replication table  has been changed. Previously, when executing `DROP PARTITION` on a replication table, the data of the partition to be dropped was first replicated before the `DROP PARTITION` operation was performed. Now, the data of the dropped partition is no longer replicated.
    
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

### BUG-51214<a name=bug-51214></a> Fixed an issue where an error occurred when granting permissions on individual objects using the SYS account.

-   **module** : qp-ddl-dcl-pvo

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where an error occurred when granting permissions on individual objects using the SYS account.
    
-   **How to reproduce this bug**

    -   **Reproduction conditions**

            connect sys/manager;
            Create user ccj identified by ccj;
            create user alti identified by alti;
            
            connect ccj/ccj;
            create table t1 (c1 int primary key,c2 int);
            
            connect sys/manager;
            grant select on ccj.t1 to alti;
        
    -   **Actual Results**
    
            [ERR-313D8 : The user has insufficient privileges.]
    
    -   **Expected Results**
    
            Success
    
-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-51216<a name=bug-51216></a> Improved to display an error message if the Extent List traversal does not complete during internal processing.

-   **module** : sm-disk-collection

-   **Category** : Enhancement

-   **Reproducibility** : Rare

-   **Description** : Improved to display an error message if the Extent List traversal does not complete during internal processing.

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
        -   new
            -    **Failed to traverse the extent directory list of segment.**
            -   **Cause** : Concurrency conflict may occur when retrieving and updating the Extent Directory Page List simultaneously.
            -   **Action**: Retry the operation. If the error persists, please contact Altibase support.

Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 7.1.0.10.0       | 6.5.1                   | 8.12.1       | 7.1.7               | 7.4.7                        |

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
