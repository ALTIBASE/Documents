Altibase 7.1.0.10.8 Patch Notes
=================================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-51888 The maximum allowed length for encrypted PASSWORD used in dblink, aku, and Adapter has been extended to 256 characters.](#bug-51888)
    - [BUG-52014 Enhanced diagnostic information for Protocol header error and Invalid protocol sequence error](#bug-52014)
    - [BUG-52066 Added feature to print the last executed query on abnormal termination](#bug-52066)
    - [BUG-52295 Improved handling of abnormal protocol by terminating session instead of assert and enhanced client logging](#bug-52295)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-48937 Fixed a failure in deleting backup files when user-created directories exist in the incremental](#bug-48937)
    - [BUG-49298 Fixed unnecessary log output during replication conflict (Not Support Data Type)](#bug-49298)
    - [BUG-50643 Fixed issue where last LOB column value becomes NULL during SYNC conflict](#bug-50643)
    - [BUG-50976 Incorrect value is entered when executing a MERGE INTO statement on a CLOB column.](#bug-50976)
    - [BUG-51324 Fixed performance degradation when collecting disk index statistics in parallel.](#bug-51324)
    - [BUG-51792 Fixed to not adjust the redo point when encountering a TBS Update log during Incomplete Recovery.](#bug-51792)
    - [BUG-51905 Fixed replication issue for disk tables with LOB columns in adapter](#bug-51905)
    - [BUG-51920 Fixed abnormal termination when using LOB type in ORDER BY clause](#bug-51920)
    - [BUG-51953 Improved behavior to stop the replication receiver if memory tablespace resources are insufficient](#bug-51953)
    - [BUG-51977 Fixed an issue where SQLDriverConnectW() returns SQL_SUCCESS_WITH_INFO even when the connection fails.](#bug-51977)
    - [BUG-51989 Fixed an issue where some rows are not updated when performing Multiple Table Update on a disk table with indexes.](#bug-51989)
    - [BUG-51994 Fixed a result error where some results were missing when executing nested Left Outer Join statements](#bug-51994)
    - [BUG-52002 Fixed abnormal termination during record update processing when a conflict occurs during SYNC in SQL_APPLY mode.](#bug-52002)
    - [BUG-52046 Fixed an issue where an error may occur during disk hash temp table insertion when a single record length is 2.5MB or more.](#bug-52046)
    - [BUG-52062 Fixed an issue where the altiEncrypt binary was not included in the package.](#bug-52062)
    - [BUG-52086 Fixed an issue where ServiceThread may reference invalid memory in an IPC connection environment.](#bug-52086)
    - [BUG-52087 Fixed an error that could occur when using UNION ALL in a View that uses the ROW_NUMBER() function.](#bug-52087)
    - [BUG-52091 Fixed a concurrency issue that could occur during metadata processing in a replication environment.](#bug-52091)
    - [BUG-52168 Fixed performance issue for disk table DML after expanding BUFFER AREA SIZE](#bug-52168)
    - [BUG-52171 Fixed a server crash when renaming a table that has a trigger using SQL functions.](#bug-52171)
    - [BUG-52188 Improved stability of diagnostic dump information collection on server crash](#bug-52188)
    - [BUG-52190 Fixed for Abnormal Lock Release Depending on SELECT Execution Order in Non-AutoCommit Mode](#bug-52190)
    - [BUG-52219 Fixed incorrect variable column padding when generating Supplemental Logs](#bug-52219)
    - [BUG-52220 Fixed server crash when executing DROP COLUMN on replicated disk tables with LOB and Supplemental Log](#bug-52220)
    - [BUG-52226 Fixed standby server crash during DELETE log processing in SQL_APPLY mode](#bug-52226)
    - [BUG-52230 Fixed "Meta table crashed" error when SYS revokes Role privileges granted by another user](#bug-52230)
    - [BUG-52262 Fixed abnormal server termination when an invalid protocol header is received during connection from an older client (6.1.1 or earlier).](#bug-52262)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [Compatibility](#compatibility)
    - [Altibase Server Properties](#altibase-server-properties)
    - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-51888<a name=bug-51888></a> The maximum allowed length for encrypted PASSWORD used in dblink, aku, and Adapter has been extended to 256 characters.

-   **module** : rp
-   **Category** : Enhancement
-   **Reproducibility** : Always
-   **Description** : The maximum allowed length of the encrypted PASSWORD used in dblink, aku, and Adapter has been changed to 256 characters. Note that altiEncrypt supports password input of up to 128 characters in length, and generates an encrypted PASSWORD of up to 256 characters.

### BUG-52014<a name=bug-52014></a> Enhanced diagnostic information for Protocol header error and Invalid protocol sequence error

-   **module** : cm
-   **Category** : Functionality
-   **Reproducibility** : Rare
-   **Description** : Improved diagnostics by additionally logging session information and client PID when Protocol header error or Invalid protocol sequence error occurs.

### BUG-52066<a name=bug-52066></a> Added feature to print the last executed query on abnormal termination

-   **module** : mm
-   **Category** : Enhancement
-   **Reproducibility** : Rare
-   **Description** : Added a feature to print the last executed query from the signal handler when the server terminates abnormally.
     This feature can be enabled using the internal property `__QUERY_BUCKET_FLAG`, and the output can be found in `dumptrc` or `altibase_error.log`. 

### BUG-52295<a name=bug-52295></a> Improved handling of abnormal protocol by terminating session instead of assert and enhanced client logging

-   **module** : mm
-   **Category** : Assert
-   **Reproducibility** : Rare
-   **Description** : During abnormal protocol processing, the behavior has been changed to forcibly terminate the connection with the client session instead of triggering an assert. Additionally, client information is now additionally logged to assist in problem analysis.

Fixed Bugs
==========

### BUG-48937<a name=bug-48937></a> Fixed a failure in deleting backup files when user-created directories exist in the incremental

-   **module** : sm

-   **Category** : Message Error

-   **Reproducibility** : Always

- **Description** : Fixed an issue where the statement `ALTER DATABASE DELETE OBSOLETE BACKUP FILES;` failed with `[ERR-41082: Internal server error]` if the incremental backup directory contained user-created subdirectories. Now, the statement executes successfully even if user-created directories exist; those directories are preserved.

  Additionally, information about directories that could not be deleted is recorded in the `altibase_sm.log` file under the `trc` directory.

  - Example log message in `altibase_sm.log`:

  ```bash
   [BackupInfoMgr] Unable to delete <backup_path> (errno=39)
  ```

### BUG-49298<a name=bug-49298></a> Fixed unnecessary log output during replication conflict (Not Support Data Type)

-   **module** : rp

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where unnecessary logs were generated in `$ALTIBASE_HOME/trc/altibase_rp.log` during replication conflicts when columns of type BLOB, CLOB, GEOMETRY, or JSON exist.
    
    ```bash
    ERR-61069(errno=62) Internal server error in replication module (Not Support Data Type( id : 40 )).
    ```
    
    Also improved logging in `altibase_rp_conflict.log` to include the data type ID, e.g.:

    ```
    <None printable data( id : 30 )>
    ```

### BUG-50643<a name=bug-50643></a> Fixed issue where last LOB column value becomes NULL during SYNC conflict

- **module** : rp

- **Category** : Functional Error

- **Reproducibility** : Always

- **Description** : Fixed an issue where the last LOB column value of the previously inserted record becomes NULL when a conflict occurs during SYNC on tables with LOB columns.

  This issue only occurred when the conflict happened on the second or subsequent records, not the first record.
   It no longer occurs after applying this patch.

### BUG-50976<a name=bug-50976></a> Incorrect value is entered when executing a MERGE INTO statement on a CLOB column.

-   **module** : qp-dml-pvo

-   **Category** : Functionality

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where an incorrect value was entered when executing a `MERGE INTO` statement on a CLOB column.
    
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

  -   **Expected Results**

      ```sql
      	I1
      -----------------------------------------------------------------------------------
      1
      22
      2 rows selected.
      ```

- **Workaround**

  None

### BUG-51324<a name=bug-51324></a> Fixed performance degradation when collecting disk index statistics in parallel.

-   **module** : sm
-   **Category** : Other
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where more time was consumed when collecting disk index statistics in parallel.

### BUG-51792<a name=bug-51792></a> Fixed to not adjust the redo point when encountering a TBS Update log during Incomplete Recovery.

-   **module** : sm
-   **Category** : Fatal
-   **Reproducibility** : Always
-   **Description** : Fixed so that the Redo point is not adjusted when a TBS Update log is encountered during Incomplete Recovery.

### BUG-51905<a name=bug-51905></a> Fixed replication issue for disk tables with LOB columns in adapter

-   **module** : rp-jdbcAdapter
-   **Category** : Functional Error
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where replication failed for disk tables containing LOB columns in the adapter.

### BUG-51920<a name=bug-51920></a> Fixed abnormal termination when using LOB type in ORDER BY clause

- **module** : qp-dml-execute

- **Category** : Fatal

- **Reproducibility** : Always

- **Description** : Fixed an issue where using LOB types in ORDER BY caused abnormal termination.
   Now, the following error is correctly returned:

  ```
  [ERR-31246 : Incomparable data types (GEOMETRY,LOB) cannot be used in ORDER BY, GROUP BY, HAVING and CONNECT BY clauses.] 
  ```

### BUG-51953<a name=bug-51953></a> Improved behavior to stop the replication receiver if memory tablespace resources are insufficient

- **module** : rp

- **Category** : Enhancement

- **Reproducibility** : Always

-   **Description** : When the replication fails due to insufficient memory tablespace resources, the behavior has been changed.
    
    Previously, such errors were treated as conflicts. After the fix, the replication receiver is stopped instead.
    
    This applies to the following cases:
    
    - Auto-extension of the memory tablespace is disabled (smERR_ABORT_UNABLE_TO_EXTEND_CHUNK_WHEN_AUTO_EXTEND_OFF)
    - The memory tablespace size exceeds MEM_MAX_TBS_SIZE (smERR_ABORT_UNABLE_TO_EXTEND_CHUNK_MORE_THAN_MEM_MAX_DB_SIZE)
    - The memory tablespace exceeds its maximum size (smERR_ABORT_UNABLE_TO_EXTEND_CHUNK_MORE_THAN_TBS_MAXSIZE )

### BUG-51977<a name=bug-51977></a> Fixed an issue where SQLDriverConnectW() returns SQL_SUCCESS_WITH_INFO even when the connection fails.

-   **module** : mm-cli
-   **Category** : Functional Error
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where `SQLDriverConnectW()` returned `SQL_SUCCESS_WITH_INFO` even when connection failed due to invalid IP address and small buffer size.

### BUG-51989<a name=bug-51989></a> Fixed an issue where some rows are not updated when performing Multiple Table Update on a disk table with indexes.

-   **module** : sm\_index

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where some rows were not updated when performing Multiple Table Update on a disk table that has indexes.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    drop table t1;
    drop table t2;
    create table t1 ( i1 varchar(40), i2 varchar(10), SBI_ORDER_ID varchar(10) ) tablespace sys_tbs_disk_data;
    create index idx1 on t1 ( SBI_ORDER_ID );
    create table t2 ( i1 varchar(40), SBI_ORDER_ID varchar(10) ) tablespace sys_tbs_disk_data;
    create index idx2 on t2 ( SBI_ORDER_ID );
    
    insert into t1 select level, 10, '6000000077' from dual connect by level < 3;
    insert into t2 select level, '6000000077' from dual connect by level < 3;
    
    update t1 a, t2 b set a.i1 = 'AA', b.i1 = 'BB' where A.SBI_ORDER_ID = B.SBI_ORDER_ID and a.SBI_ORDER_ID = '6000000077';
    ```

  -   **Actual Results**

          3 rows updated.

  -   **Expected Results**

          4 rows updated.

-   **Workaround**

        NO INDEX

### BUG-51994<a name=bug-51994></a> Fixed a result error where some results were missing when executing nested Left Outer Join statements

-   **module** : qp

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where some results could be missing due to a Join predicate processing error when executing nested Left Outer Join statements.

- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    drop table t1;
    drop table t2;
    drop table t3;
    drop table t4;
    
    create table t1 (c1 integer primary key, c2 char(10), c3 char(10));
    create table t2 (c1 integer primary key, c2 char(10), c3 char(10));
    create table t3 (c1 integer primary key, c2 char(10), c3 char(10));
    create table t4 (c1 integer primary key, c2 char(10), c3 char(10));
    insert into t1 values (1,1,null);
    insert into t2 values (1,1,24);
    insert into t4 values (1,1,24);
    
    select t2.*, t3.*, t4.* from t1
              left outer join  t2 on t1.c1 = t2.c1
              left outer join  t3 on t1.c1 = t3.c1
              left outer join  t4 on
              (t4.c2=t3.c2 and t4.c3 = t3.c3)
              or
              (t4.c2=t2.c2 and t4.c3 = t2.c3)
              ;
    ```

  -   **Actual Results**

      ```sql
      C1          C2          C3          C1          C2          C3
      -------------------------------------------------------------------------------
      C1          C2          C3
      ----------------------------------------
      1           1           24
      1 row selected.
      ```
      
  -   **Expected Results**

      ```sql
      C1          C2          C3          C1          C2          C3
      -------------------------------------------------------------------------------
      C1          C2          C3
      ----------------------------------------
      1           1           24
      1           1           24
      1 row selected.
      ```

- **Workaround**

  None

### BUG-52002<a name=bug-52002></a> Fixed abnormal termination during record update processing when a conflict occurs during SYNC in SQL_APPLY mode.

-   **module** : rp
-   **Category** : Fatal
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where the server terminated abnormally when a record update occurred according to the conflict resolution policy during SYNC execution in SQL_APPLY mode when a conflict was detected.

### BUG-52046<a name=bug-52046></a> Fixed an issue where an error may occur during disk hash temp table insertion when a single record length is 2.5MB or more.

-   **module** : sm
-   **Category** : Functional Error
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where an error could occur during disk hash temp table insertion when a single record's length was 2.5MB or more.

### BUG-52062<a name=bug-52062></a> Fixed an issue where the altiEncrypt binary was not included in the package.

-   **module** : rp-jdbcAdapter
-   **Category** : Other
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where the altiEncrypt binary was not included during the package build process, making the feature unavailable.

### BUG-52086<a name=bug-52086></a> Fixed an issue where ServiceThread may reference invalid memory in an IPC connection environment.

-   **module** : mm
-   **Category** : Memory Error
-   **Reproducibility** : Rare
-   **Description** : Fixed an issue where ServiceThread could reference invalid memory in an IPC connection environment..

### BUG-52087<a name=bug-52087></a> Fixed an error that could occur when using UNION ALL in a View that uses the ROW_NUMBER() function.

-   **module** : qp
-   **Category** : Fatal
-   **Reproducibility** : Frequence
-   **Description** : Fixed an issue where an error could occur in certain situations when executing a query containing UNION ALL in a View that uses the ROW_NUMBER() function.

### BUG-52091<a name=bug-52091></a> Fixed a concurrency issue that could occur during metadata processing in a replication environment.

-   **module** : rp
-   **Category** : Fatal
-   **Reproducibility** : Rare
-   **Description** : Fixed a concurrency issue that could occur during metadata processing in a replication environment.

### BUG-52168<a name=bug-52168></a> Fixed performance issue for disk table DML after expanding BUFFER AREA SIZE

-   **module** : sm
-   **Category** : Functional Error
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where DML performance on disk tables did not improve after expanding the DISK BUFFER AREA SIZE during service.

### BUG-52171<a name=bug-52171></a> Fixed a server crash when renaming a table that has a trigger using SQL functions.

-   **module** : qp-psm-trigger-execute

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where the server could crash when renaming a table that has a trigger using SQL functions.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    create table t1 (c1 integer);
    create or replace trigger trig_on_t1
    before insert on t1
    referencing new as new_row
    for each row
    as
    var1 varchar(10);
    begin
      var1 := nvl('a', 'a');
    end;
    /
    rename t1 to tx;
    ```

  -   **Actual Results**

          [ERR-91015 : Communication failure.]

  -   **Expected Results**

          Rename success.

-   **Workaround**

        Drop the trigger, rename the table, and then recreate the trigger.

### BUG-52188<a name=bug-52188></a> Improved stability of diagnostic dump information collection on server crash

-   **module** : mm
-   **Category** : Reliability
-   **Reproducibility** : Rare
-   **Description** : Fixed an error where session and task diagnostic information were missing in certain situations upon abnormal termination. Also improved the dump to include communication read buffers and service thread Statement ID to assist in failure analysis.

### BUG-52190<a name=bug-52190></a> Fixed for Abnormal Lock Release Depending on SELECT Execution Order in Non-AutoCommit Mode

-   **module** : sm
-   **Category** : Fatal
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where IS_LOCK was released abnormally depending on the execution order of SELECT statements within a single transaction in Non-AutoCommit mode.

### BUG-52219<a name=bug-52219></a> Fixed incorrect variable column padding when generating Supplemental Logs

-   **module** : sm
-   **Category** : Functional Error
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where `UPDATE` statements failed due to incorrect handling of variable column padding during the generation of Supplemental Logs.

### BUG-52220<a name=bug-52220></a> Fixed server crash when executing DROP COLUMN on replicated disk tables with LOB and Supplemental Log

-   **module** : sm
-   **Category** : Fatal
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where the server could crash when executing a DROP COLUMN statement on a disk table containing LOB columns and Supplemental Log, when the table is included in replication.

### BUG-52226<a name=bug-52226></a> Fixed standby server crash during DELETE log processing in SQL_APPLY mode

-   **module** : rp-receiver
-   **Category** : Fatal
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where the standby server could crash during DELETE log processing when operating in SQL_APPLY mode in a replication environment with Supplemental Log enabled on the table.

### BUG-52230<a name=bug-52230></a> Fixed "Meta table crashed" error when SYS revokes Role privileges granted by another user

-   **module** : qp-ddl-dcl-execute

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where `[ERR-31015: The meta table crashed.]` occurred when the `SYS` account attempted to revoke object privileges from a Role that were originally granted by the Role owner (another user).
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    ## Create userA user , role 
    create user userA identified by userA;
    create role r_userA;
    
    ## connect by userA and create userA.T1
    connect userA/userA;
    create table T1(c1 integer primary key, c2 varchar(10), c3 varchar(10));
    
    ## userA user grants the privileges to r_userA
    grant delete, insert, select, update on userA.T1 to r_userA; 
    
    ## sys user try to revoke the privileges from r_userA
    connect sys/manager;
    revoke delete, insert, select, update on userA.T1 from r_userA;
    ```

  - **Actual Results**

    ```sql
    [ERR-31015 : The meta table crashed.
    0001 : revoke delete, insert, select, update on userA.T1 from R_userA
    ^ ^
    ]
    ```

  - **Expected Results**

    

-   **Workaround**

        Grant and revoke privileges using the SYS user.

### BUG-52262<a name=bug-52262></a> Fixed abnormal server termination when an invalid protocol header is received during connection from an older client (6.1.1 or earlier).

-   **module** : cm
-   **Category** : Fatal
-   **Reproducibility** : Rare
-   **Description** : Fixed an issue where the server could terminate abnormally in certain situations when an invalid protocol header value was received during a connection from an older client (version 6.1.1 or earlier).

Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 7.1.0.10.8       | 6.5.1                   | 8.12.1       | 7.1.7               | 7.4.7                        |

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

No properties added/changed/deleted.

### Performance Views

No performance views added/changed/deleted.
