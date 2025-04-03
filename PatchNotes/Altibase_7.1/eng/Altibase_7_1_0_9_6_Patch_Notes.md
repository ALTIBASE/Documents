# Altibase 7.1.0.9.6 Patch Notes

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [New Features](#new-features)
    - [BUG-50868 support for multiple replication in AKU](#bug-50868)
    - [BUG-50873 Improvement of the aku -p clean operation](#bug-50873)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-50864 Incorrect error message when the log file size is abnormally changed.](#bug-50864)
    - [BUG-50866 Fixed issue where 'Database media recovery successful' message was incorrectly displayed during recovery when MustRedo LSN log file did not exist from online backup.](#bug-50866)
    - [BUG-50869 Fixed Deadlock Issue Between Thread Manager and IPCDA Service Thread](#bug-50869)
    - [BUG-50881 Fixed an issue where an abnormal server shutdown occured if the client terminated during IPCDA connection.](#bug-50881)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [Compatibility](#compatibility)
    - [Altibase Server Properties](#altibase-server-properties)
    - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-50868<a name=bug-50868></a> support for multiple replication in AKU

- **module** : aku

- **Category** : Enhancement

- **Reproducibility** : Always

- **Description** : Previously, AKU only supported single replication, but it has now been improved to support multiple replications. It is now possible to configure multiple replications in the 'Replication Properties' section of the aku.conf file as follows:

  ```shell
  #=================================================================
  # Replication Properties
  #=================================================================
  REPLICATIONS = (
      REPLICATION_NAME_PREFIX = AKU_REP1
      SYNC_PARALLEL_COUNT     = 1
      (
          SYS.T1, SYS.T2, SYS.T3
      )
  ),
  (
      REPLICATION_NAME_PREFIX = AKU_REP2
      SYNC_PARALLEL_COUNT     = 1
      (
          SYS.T4, SYS.T5, SYS.T6
      )
  ),
  (
      REPLICATION_NAME_PREFIX = AKU_REP3
      SYNC_PARALLEL_COUNT     = 1
      (
          SYS.T7,
          SYS.T8,
          SYS.T9
      )
  )
  ```

  For more details, refer to [aku.conf](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/eng/Utilities%20Manual.md#akuconf) from Utilities Manual -3.aku. Additionally, the format "user_name.table_name" for specifying replication target tables has now been supported.

  * Original

    ```
    REPLICATIONS = (
        REPLICATION_NAME_PREFIX = "AKU_REP"
        SYNC_PARALLEL_COUNT     = 1
        (
            (
                USER_NAME      = "SYS"
                TABLE_NAME     = "T1"
            ),
            (
                USER_NAME      = "SYS"
                TABLE_NAME     = "T2"
            ),
            (
                USER_NAME      = "SYS"
                TABLE_NAME     = "T3"
            )
        )
    )
    ```

  * New (In addition to supporting the original configuration format, we also support the following additional format.)

    ```
    REPLICATIONS = (
        REPLICATION_NAME_PREFIX = AKU_REP1
        SYNC_PARALLEL_COUNT     = 1
        (
            SYS.T1, SYS.T2, SYS.T3
        )
    )
    ```

- Additional enhancements

  -   Improved the ability to use the same character set as the Altibase server's charset on the Altibase server using the ALTIBASE_NLS_USE environment variable.
  -   Improved to allow comments in the aku.conf file.
  - When running AKU, tasks that were executed sequentially on a single thread are now performed in parallel using multiple threads, reducing overall execution time.
  - Fixed AKU to return an error if REPLICATION_MAX_COUNT is exceeded when creating replication.
  - Retrying a query when it failed was now only retried once after a 1 second wait,
      AKU_QUERY_RETRY_COUNT and AKU_QUERY_RETRY_DELAY_MSEC
      properties, which can be set using the AKU_QUERY_RETRY_DELAY_MSEC
  - Added instructions to the manual for what to do if the `aku -p start` command fails due to a failure of the master pod, see Utilitis manual - 3.aku for details.
  
- #### How to reproduce this bug

  -   **Reproduction conditions**

  -   **Actual Results**

  -   **Expected Results**

- **Workaround**

- **Changes**

  -   Performance view
  -   Property
      -   AKU_QUERY_RETRY_COUNT
          -   number of retry attempts when the query fails during AKU
          -   default value : 5
          -   min : 0
          -   max : 2<sup>32</sup> - 1
      -   AKU_QUERY_RETRY_DELAY_MSEC
          -   Wait time before the next retry when a query fails during AKU execution and a retry is attempted ( msec )
          -   default value : 1000
          -   min : 0
          -   max : 2<sup>32</sup> - 1
  -   Compile Option
  -   Error Code

### BUG-50873<a name=bug-50873></a> Improvement of the aku -p clean operation

-   **module** : aku

-   **Category** : Functional Error

-   **Reproducibility** : Rare

-   **Description** : When performing `aku -p clean`, only the replication objects on the local pod were deleted. However, in this case, the replication on all pods related to the local pod was not stopped. Now, when the replication object of the local pod is deleted, the replication objects on all pods related to the deleted object will be stopped.
    
    For example, in an environment consisting of four pods, when `aku -p clean` is executed on the third pod:

    * **(Previous behavior)** 
    
      : Only the replication objects AKU_REP_03, AKU_REP_13, and AKU_REP_23 on the third pod were stopped and deleted.
    
    * **(Updated behavior)** 
    
      : The replication objects AKU_REP_03, AKU_REP_13, and AKU_REP_23 on the third pod will be stopped and deleted, and the replication objects AKU_REP_03, AKU_REP_13, and AKU_REP_23 on the master pod, pod 1, and pod 2 will also be stopped.
    
-   #### How to reproduce this bug

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
==========

### BUG-50864<a name=bug-50864></a> Incorrect error message when the log file size is abnormally changed.

-   **module** : sm

-   **Category** : Message Error

-   **Reproducibility** : Always

-   **Description** : Fixes the issue where an incorrect error message **[ERR-111AC: OS return Log file size is zero. (log file path and file)]** was displayed when the log file size was abnormally changed. Now, the error message **[ERR-111C1: The log file size has changed. : (current file size:, expected file size:)]** will be displayed.

-   #### How to reproduce this bug

    -   **Reproduction conditions**

    -   **Actual Results**

    -   **Expected Results**

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code
        -   **0x111C1 (  70081) smERR_ABORT_WrongLogFileSize** The log file size has changed. : <0%s> (current file size:<1%u>, expected file size:<2%u>)
            -   **Cause**: The log file size has changed abnormally, so that the file is invalid.
            -   **Action**: Check if the backed-up file for the log file exists and restore it. If it's not available, contact Altibase's Support Center (http://support.altibase.com).

### BUG-50866<a name=bug-50866></a> Fixed issue where 'Database media recovery successful' message was incorrectly displayed during recovery when MustRedo LSN log file did not exist from online backup.

-   **module** : sm
-   **Category** : Fatal
-   **Reproducibility** : Always
-   **Description** : When attempting recovery using an online backup file, if the MustRedo LSN is missing, the server will now return the error message **[ERR-91015 : Communication failure.]**. Additionally, the log file will display the message "Recovery failure, need more logfile ..." in the altibase_boot.log.
- #### How to reproduce this bug

  -   **Reproduction conditions**

  -   **Actual Results**

  -   **Expected Results**
-   **Workaround**
-   **Changes**
    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50869<a name=bug-50869></a> Fixed Deadlock Issue Between Thread Manager and IPCDA Service Thread

-   **module** : cm

-   **Category** : Hang

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where a deadlock situation occurred in the server. The Thread Manager waited for the IPCDA service thread, the IPCDA service thread waited for client requests, and the client waited for the Thread Manager's response, resulting in a deadlock.
    
-   #### How to reproduce this bug

    -   **Reproduction conditions**

    -   **Actual Results**

    -   **Expected Results**

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50881<a name=bug-50881></a>Fixed an issue where an abnormal server shutdown occured if the client terminated during IPCDA connection.

-   **module** : cm

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where an abnormal server shutdown occured if the client terminated during IPCDA connection.
    
-   #### How to reproduce this bug

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
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 7.1.0.9.6        | 6.5.1                   | 8.11.1       | 7.1.7               | 7.4.7                        |

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
