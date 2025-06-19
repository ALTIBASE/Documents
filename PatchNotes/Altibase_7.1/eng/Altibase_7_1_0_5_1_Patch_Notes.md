Altibase 7.1.0.5.1 Patch Notes
==============================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [New Features](#new-features)
  - [BUG-48369 Disk temp table renewal](#bug-48369%C2%A0disk-temp-table-renewal)
  - [BUG-48409 Improved the method of creating online log files.](#bug-48409%C2%A0improved-the-method-of-creating-online-log-files)
  - [BUG-48425 Added the functionality to enable/disable logging for the three types of comparison (DIFF) results in the altiComp utility.](#bug-48425%C2%A0added-the-functionality-to-enabledisable-logging-for-the-three-types-of-comparison-diff-results-in-the-alticomp-utility)
- [Fixed Bugs](#fixed-bugs)
  - [BUG-48327 Fixed the issue where inefficient indexes were chosen in Semi Join and Anti Join.](#bug-48327%C2%A0fixed-the-issue-where-inefficient-indexes-were-chosen-in-semi-join-and-anti-join)
  - [BUG-48422 Fixed the issue where the Altibase server would crash due to errors between the Buffer Control Block (BCB) and buffer frames during the process of loading pages into the disk buffer.](#bug-48422%C2%A0fixed-the-issue-where-the-altibase-server-would-crash-due-to-errors-between-the-buffer-control-block-bcb-and-buffer-frames-during-the-process-of-loading-pages-into-the-disk-buffer)
  - [BUG-48477 Fixed the issue where the Altibase server would crash during the initialization process for reusing disk hash temp.](#bug-48477%C2%A0fixed-the-issue-where-the-altibase-server-would-crash-during-the-initialization-process-for-reusing-disk-hash-temp)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [Compatibility](#compatibility)
  - [Altibase Server Properties](#altibase-server-properties)
  - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
------------

### BUG-48369 Disk temp table renewal

-   **module** : sm-disk-resource

-   **Category** : Enhancement

-   **Reproducibility** : Always

-   **Description** : With the implementation of Disk temp table renewal, the behavior of Disk hash temp tables has changed.
    
    The result order of SELECT queries without an ORDER BY clause may vary.
    
    The performance of SQL using Disk temp tables has improved.
    
    SQL using Disk temp tables now use less memory compared to before.
    
    With the removal of the TEMP_MAX_PAGE_COUNT property, the entire disk temporary tablespace can be utilized without being constrained by the TEMP_MAX_PAGE_COUNT.    

- **How to reproduce this bug**
  
  -   **Reproduction conditions**
      
  -   **Actual Results**
      
  -   **Expected Results**
  
-   **Workaround**

- **Changes**

  -   Performance view
      
      -   The performance view V$DISK_TEMP_STAT has been updated with the addition of the columns OVER_ALLOC_COUNT, MAX_WORK_AREA_SIZE, and RUNTIME_MAP_SIZE.
  - Property
    -   Changed the range of **HASH_AREA_SIZE**
        -   Range : [512K, 2^64-1]  -\> [3M, 2^64-1]
    -   Delete
        -   **TEMP_MAX_PAGE_COUNT**
    -   Changed the decription of **TOTAL_WA_SIZE**
         - Description :
        This property specifies the maximum size of memory available for allocation for sorting or hashing operations. The value of this property can be changed using the ALTER SYSTEM statement while Altibase is running. 
    -   New property - **INIT_TOTAL_WA_SIZE**
    
       - Description : Specifies the amount of memory to be preallocated for sorting or hashing operations. If the specified value exceeds `TOTAL_WA_SIZE`, only up to `TOTAL_WA_SIZE` will be allocated. The value of this property can be changed using the ALTER SYSTEM statement while Altibase is running. 
    
       - Default value:  2<sub>64</sub>-1
       - Range : 0, 2^64-1, 2^64-1
  -   Compile Option
  -   Error Code

### BUG-48409 Improved the method of creating online log files.

-   **module** : sm\_recovery
-   **Category** : Enhancement
-   **Reproducibility** : Rare
-   **Description** : Improve the way online log files are generated to prevent online log file generation errors from creating incomplete online log files. 
    1. create a temporary file named logfile.tmp
    2. initialize the file and expand it by the size of LOG_FILE_SIZE
    3. rename the temporary file to logfile.*\#*
-   **How to reproduce this bug**

    -   **Reproduction conditions**

    -   **Actual Results**

    -   **Expected Results**
-   **Workaround**
-   **Changes**

    -   Performance view
    -   Property
        - New
        - **__USE_TEMP_FOR_PREPARE_LOGFILE** (hidden property)
          -   Default value: 1
          -   Range: [0,1]
          -   Description : Configure whether to create a temporary file when preparing an online log file. To maintain the existing behavior, set __USE_TEMP_FOR_PREPARE_LOGFILE to 0.   
              -   0 : The process of preparing an online log file has been improved to no longer use temporary files.
              -   1 : The process of preparing an online log file has been modified to use temporary files.
                   The **ZERO_SIZE_LOG_FILE_AUTO_DELETE** property setting is ignored.
                   At the time of Altibase server startup, the function to expand the size of an online log file is disabled if its size is between 1 and 9,999,999 bytes.
    -   Compile Option
    -   Error Code

### BUG-48425 Added the functionality to enable/disable logging for the three types of comparison (DIFF) results in the altiComp utility.

-   **module** : ux-audit(altiComp)

-   **Category** : Functionality

-   **Reproducibility** : Always

- **Description** : In the altiComp utility, the functionality to enable/disable logging for the following three types of comparison (DIFF) results has been added:

  -   LOG\_DF\_MOSO
  -   LOG\_MOSX
  -   LOG\_MXSO

  For example, to prevent the results of the DF_MOSO type from being logged in the execution result file, set LOG_DF_MOSO = OFF.

-   **How to reproduce this bug**

    -   **Reproduction conditions**

    -   **Actual Results**

    -   **Expected Results**

-   **Workaround**

- **Changes**

  - Performance view

  - Property
    -   altComp.cfg 파일에 프로퍼티 추가되었습니다.
        -   [LOG\_DF\_MOSO](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Utilities.md#log_df_moso)
        -   [LOG\_MOSX](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Utilities.md#log_mosx)
        -   [LOG\_MXSO](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Utilities.md#log_mxso)

  - Compile Option

  - Error Code

  

Fixed Bugs
----------

### BUG-48327 Fixed the issue where inefficient indexes were chosen in Semi Join and Anti Join.

-   **module** : qp-dml-pvo

-   **Category** : Efficiency

-   **Reproducibility** : Always

-   **Description** : Fixed the issue where inefficient indexes were chosen in Semi Join and Anti Join.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    DROP TABLE T1;
    CREATE TABLE T1 ( I1 INT, I2 INT, I3 INT, I4 INT, I5 INT) TABLESPACE SYS_TBS_MEM_DATA;
    ALTER TABLE T1 ADD PRIMARY KEY (I1, I2, I3);
    CREATE INDEX IDX1 ON T1(I1, I3); 
    ALTER SESSION SET EXPLAIN PLAN = ON;
    ALTER SESSION SET TRCLOG_DETAIL_PREDICATE=1;
    SELECT *
      FROM T1 A
     WHERE I1 IN (SELECT /*+ NL_SJ NO_INVERSE_JOIN */ I1
                    FROM T1 B
                   WHERE I3 > 0 AND I4 > 0);
    ```

  - **Actual Results**

    ```sql
    ------------------------------------------------------------
    PROJECT ( COLUMN_COUNT: 5, TUPLE_SIZE: 20, COST: 526.09 )
     SEMI-JOIN ( METHOD: INDEX_NL, COST: 525.43 )
      SCAN ( TABLE: SYS.T1 A, FULL SCAN, ACCESS: 0, COST: 116.76 )
      SCAN ( TABLE: SYS.T1 $$1_$$VIEW1_$B, INDEX: SYS.__SYS_IDX_ID_248, RANGE SCAN, ACCESS: 0, COST: 124.68 )
        [ VARIABLE KEY ]
       OR
        AND
         A.I1 = $$1_$$VIEW1_$B.I1
       [ VARIABLE KEY FILTER ]
       OR
        AND
         I3 > 0
       [ FILTER ]
       I4 > 0
    ------------------------------------------------------------
    ```

  -   **Expected Results**

          ------------------------------------------------------------
          PROJECT ( COLUMN_COUNT: 5, TUPLE_SIZE: 20, COST: 526.09 )
           SEMI-JOIN ( METHOD: INDEX_NL, COST: 525.43 )
            SCAN ( TABLE: SYS.T1 A, FULL SCAN, ACCESS: 0, COST: 116.76 )
            SCAN ( TABLE: SYS.T1 $$1_$$VIEW1_$B, INDEX: SYS.IDX1, RANGE SCAN, ACCESS: 0, COST: 7.93 )
             [ VARIABLE KEY ]
             OR
              AND
               A.I1 = $$1_$$VIEW1_$B.I1
               I3 > 0
             [ FILTER ]
             I4 > 0
          -----------------------------------------------------------

- **Workaround**

  ```sql
  -- Use "INDEX" hint
  SELECT *
    FROM T1 A
   WHERE I1 IN (SELECT /*+ NL_SJ NO_INVERSE_JOIN INDEX(B IDX1) */ I1
                  FROM T1 B
                 WHERE I3 > 0 AND I4 > 0);
  ```

- **Changes**

  - Performance view
  - Property

  - Compile Option
    
  - Error Code
  
    

### BUG-48422 Fixed the issue where the Altibase server would crash due to errors between the Buffer Control Block (BCB) and buffer frames during the process of loading pages into the disk buffer.

-   **module** : sm

-   **Category** : Assert

-   **Reproducibility** : Unknown

-   **Description** : Fixed the issue where the Altibase server would crash due to errors between the Buffer Control Block (BCB) and buffer frames during the process of loading pages into the disk buffer.
    
-   **How to reproduce this bug**

    -   **Reproduction conditions**

    -   **Actual Results**

    -   **Expected Results**

-   **Workaround**

- **Changes**

  - Performance view

  - Property

  - Compile Option

  - Error Code

    

### BUG-48477 Fixed the issue where the Altibase server would crash during the initialization process for reusing disk hash temp.

-   **module** : sm

-   **Category** : Fatal

-   **Reproducibility** : Rare

-   **Description** : Fixed the issue where the Altibase server would crash during the initialization process for reusing disk hash temp.
    
-   **How to reproduce this bug**

    -   **Reproduction conditions**

    -   **Actual Results**

    -   **Expected Results**

-   **Workaround**

- **Changes**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

  

Changes
-------

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 7.1.0.5.1        | 6.5.1                   | 8.9.1        | 7.1.7               | 7.4.6                        |

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
