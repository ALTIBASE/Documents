# Altibase 7.1.0.5.8 Patch Notes

<br/>

<br/>



# Table of Contents 

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [New Features](#new-features)
    - [BUG-47815 Fixes incorrect setting of trace logging level related to query processing (QP) module and adds logging level related to task scheduler execution.](#bug-47815fixes-incorrect-setting-of-trace-logging-level-related-to-query-processing-qp-module-and-adds-logging-level-related-to-task-scheduler-execution)
    - [BUG-49108 Add altibase_job.log for job scheduler execution record.](#bug-49108add-altibase_joblog-for-job-scheduler-execution-record)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-49122 If the PUBLIC role is deleted, a segmentaion failure error occurs when aexport is executed.](#bug-49122if-the-public-role-is-deleted-a-segmentaion-failure-error-occurs-when-aexport-is-executed)
    - [BUG-49136 Altibase server abnormally terminates when executing an INSERT statement for a view created using UNION ALL.](#bug-49136altibase-server-abnormally-terminates-when-executing-an-insert-statement-for-a-view-created-using-union-all)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [Compatibility](#compatibility)
    - [Altibase Server Properties](#altibase-server-properties)
    - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-47815 Fixes incorrect setting of trace logging level related to query processing (QP) module and adds logging level related to task scheduler execution.

-   **module** : qp-psm-trigger-execute

-   **Category** : Maintainability

-   **Reproducibility** : Always

-   **Description** : Fixes incorrect setting of trace logging level related to query processing (QP) module and adds logging level related to task scheduler execution. The added logging level can be found in V$TRACELOG.
    
-   **How to reproduce this bug**

    -   **Reproduction conditions**

    -   **Actual Results**

    -   **Expected Results**

-   **Workaround**

-   **Changes**

    -   Performance view
        -   V\$TRACELOG

            Add TRCLEVEL 3 Job Scheduler Trace Log and TRCLEVEL 4 DCL Trace Log related to query processing.

            ```sql
            iSQL> SELECT MODULE_NAME, TRCLEVEL, FLAG, POWLEVEL, DESCRIPTION FROM V$TRACELOG WHERE MODULE_NAME = 'QP';
            MODULE_NAME                TRCLEVEL    FLAG                       POWLEVEL             DESCRIPTION                
            ------------------------------------------------------------------------------------------------------------------------
            QP                         1           X                          1                    PSM Error Line Trace Log   
            QP                         2           O                          2                    DDL Trace Log              
            QP                         3           X                          4                    Job Scheduler Trace Log    
            QP                         4           X                          8                    DCL Trace Log              
            QP                         5           X                          16                   ---                        
            QP                         6           X                          32                   ---                        
            ...
            QP                         31          X                          1073741824           ---                        
            QP                         32          X                          2147483648           Debug                      
            QP                         99          SUM                        2                    Total Sum of Trace Log Va  
                                                                                                   lues                       
            33 rows selected.
            ```
        
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49108 Add altibase_job.log for job scheduler execution record.

-   **module** : qp

-   **Category** : Enhancement

-   **Reproducibility** : Always

-   **Description** : Add altibase_job.log for job scheduler execution record.
    
    The creation location is $ALTIBASE_HOME/trc (default setting of SERVER_MSGLOG_DIR property). The following properties have been added to separate trace logs related to the task scheduler.
    
    - JOB\_MSGLOG\_FILE

    - JOB\_MSGLOG\_SIZE
    
    - JOB\_MSGLOG\_COUNT
    
    - JOB\_MSGLOG\_FLAG
    
    For the description of the property, please refer to the property section.
    
-   **How to reproduce this bug**

    -   **Reproduction conditions**

    -   **Actual Results**

    -   **Expected Results**

-   **Workaround**

-   **Changes**

    -   Performance view
        -   V\$TRACELOG

            Add task scheduler related log level.

            ```sql
            iSQL> SELECT MODULE_NAME, TRCLEVEL, FLAG, POWLEVEL, DESCRIPTION FROM V$TRACELOG WHERE MODULE_NAME = 'JOB';
            MODULE_NAME                TRCLEVEL    FLAG                       POWLEVEL             DESCRIPTION                
            ------------------------------------------------------------------------------------------------------------------------
            JOB                        1           O                          1                    JOB Trace Log              
            JOB                        2           X                          2                    ---                        
            JOB                        3           X                          4                    ---                        
            ...
            JOB                        31          X                          1073741824           ---                        
            JOB                        32          X                          2147483648           Debug                      
            JOB                        99          SUM                        1                    Total Sum of Trace Log Va  
                                                                                                   lues                       
            33 rows selected.
            ```
            
        
    -   Property
        -   **Add JOB_MSGLOG_FILE **
            
            - Description
            
              This is a file that records job scheduler execution logs.
            
            - Default Value
            
              altibase\_job.log
            
            - Attributes
            
              Read-Only, Single Value
            
        - **Add JOB\_MSGLOG\_SIZE **
          
          - Description
          
            Specifies the maximum size of the job scheduler trace log file. The range of values is [0, 2<sup>32</sup>-1].
          
          - Default Value
            
            10 \* 1024 \* 1024
            
          - Attributes
          
            Read-Only, Single Value
          
        - **Add  JOB\_MSGLOG\_COUNT**
        
          - Description
        
            Specifies the maximum number of Task Scheduler trace log files. The range of values is [0, 2<sup>32</sup>-1].
        
          - Default Value
            
            10
            
          - Attributes
        
            Read-Only, Single Value
        
        - **Add JOB\_MSGLOG\_FLAG**
        
          - Description
            
            Set Job Scheduler execution record settings and log level. The value of this property is a combination of V$TRACELOG and POWLEVEL. In the example below, TRCLEVEL 1 JOB Trace Log is set. Whether or not it is set can be checked with the FLAG value. Other than TRCLEVEL 1 JOB Trace Log and TRCLEVEL 32 Debug, other TRCLEVELs are undefined.
            
            ```sql
            iSQL> SELECT MODULE_NAME, TRCLEVEL, FLAG, POWLEVEL, DESCRIPTION FROM V$TRACELOG WHERE MODULE_NAME = 'JOB';
            MODULE_NAME                TRCLEVEL    FLAG                       POWLEVEL             DESCRIPTION                
            ------------------------------------------------------------------------------------------------------------------------
            JOB                        1           O                          1                    JOB Trace Log              
            JOB                        2           X                          2                    ---                        
            JOB                        3           X                          4                    ---                        
            ...중략...
            JOB                        31          X                          1073741824           ---                        
            JOB                        32          X                          2147483648           Debug                      
            JOB                        99          SUM                        1                    Total Sum of Trace Log Va  
                                                                                                   lues                       
            33 rows selected.
            ```
            
          - Default Value
            
            1
            
          - Attributes
          
            Read-Write, Single Value
        
    -   Compile Option
    
    -   Error Code

Fixed Bugs
==========

### BUG-49122 If the PUBLIC role is deleted, a segmentaion failure error occurs when aexport is executed.

-   **module** : ux-aexport

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixed a bug where a segmentaion fault error occurs when performing aexport when the PUBLIC role is deleted.
    
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

### BUG-49136 Altibase server abnormally terminates when executing an INSERT statement for a view created using UNION ALL.

-   **module** : qp

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixed a bug where the Altibase server abnormally terminated when an INSERT statement was executed for a view created using UNION ALL.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    CREATE TABLE T2 (I1 INTEGER PRIMARY KEY);
    CREATE VIEW V2 AS SELECT * FROM T2 UNION ALL SELECT * FROM T2;
    INSERT INTO V2(I1,I2) VALUES (12, 12);
    ```

  -   **Actual Results**

          ERR-31455 : Failed to work because an internal exception occurred from an OS.[Contact Altibase's Support Center] error occurred or the Altibase server abnormally terminated.

  -   **Expected Results**

          [ERR-313A4 : Cannot modify a column for a non key-preserved table]

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
|    7.1.0.5.8     |          6.5.1          |    8.9.1     |        7.1.7        |            7.4.6             |

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

- JOB_MSGLOG_FILE
- JOB_MSGLOG_SIZE
- JOB_MSGLOG_COUNT
- JOB_MSGLOG_FLAG

#### Changed properties

#### Deleted properties

### Performance Views

#### Added performance views

#### Changed performance views

- [V$TRACELOG](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/eng/General%20Reference-2.The%20Data%20Dictionary.md#vtracelog)

#### Deleted performance views
