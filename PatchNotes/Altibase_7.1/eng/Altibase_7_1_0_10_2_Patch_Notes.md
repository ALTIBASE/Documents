Altibase 7.1.0.10.2 Patch Notes
===============================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-51299 Change the maximum value of the MEMORY_INDEX_BUILD_RUN_SIZE property to 4,294,967,295.](#bug-51299)
    - [BUG-51443 Improved memory usage issue during disk DB media recovery](#bug-51443)
    - [BUG-51455 Modified the previous behavior where the umask value was set to 0 during environment handle allocation using SQLAllocHandle().](#bug-51455)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-51357 When a query using a WITH clause assigns the same alias to the RANK() OVER(...) function in both the inner and outer queries, the server may shut down abnormally.](#bug-51357)
    - [BUG-51374 Fixed an issue in which a buffer latch was not released, causing an exception during server shutdown.](#bug-51374)
    - [BUG-51399 Fixed an issue in which ERR-42000 was logged in altibase\_boot.log when an exception occurred during the state transition phase of database startup.](#bug-51399)
    - [BUG-51403 Fixed an issue where large LOB inserts into memory tables caused performance degradation.](#bug-51403)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [Compatibility](#compatibility)
    - [Altibase Server Properties](#altibase-server-properties)
    - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# New Features

### BUG-51299<a name=bug-51299></a> Change the maximum value of the MEMORY_INDEX_BUILD_RUN_SIZE property to 4,294,967,295.

-   **module** : sm-mem-index

-   **Category** : Other

-   **Reproducibility** : Always

-   **Description** : Change the maximum value of the MEMORY_INDEX_BUILD_RUN_SIZE property.
    -   Before : 18,446,744,073,709,551,615 (2<sup>64</sup>-1)
    -   After : 4,294,967,295 (2<sup>32</sup>-1)
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

### BUG-51443<a name=bug-51443></a> Improved memory usage issue during disk DB media recovery

-   **module** : sm

-   **Category** : Enhancement

-   **Reproducibility** : Always

-   **Description** : Improved the issue of high memory usage during incomplete recovery on disk DB.

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

### BUG-51455<a name=bug-51455></a> Modified the previous behavior where the umask value was set to 0 during environment handle allocation using SQLAllocHandle().

-   **module** : core

-   **Category** : Enhancement

-   **Reproducibility** : Always

-   **Description** : Fixed the issue where the umask value was being set to 0 when allocating an environment handle using SQLAllocHandle().

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
==========

### BUG-51357<a name=bug-51357></a> When a query using a WITH clause assigns the same alias to the RANK() OVER(...) function in both the inner and outer queries, the server may shut down abnormally.

-   **module** : qp-select

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where the server would shut down abnormally if both the inner and outer queries used the same alias for the RANK() OVER(...) function in a query that used a WITH clause.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    create table t1 ( i1 varchar(10) , i2 varchar(10) );
    ALTER SESSION SET STACK SIZE= 65536;
    WITH BASE AS (
    SELECT /*+ */A.i1 ,A.i2 ,RANK() OVER(ORDER BY i2) RNK
    FROM t1 A
    )
    SELECT ROW_RNK ,RANK() OVER(PARTITION BY i1 ORDER BY RNK DESC) RNK ,i1 ,i2
    FROM (
    SELECT A.i1 ,A.i2 ,A.RNK ROW_RNK ,RANK() OVER(PARTITION BY A.i1 ORDER BY A.i1 DESC) RNK
    FROM BASE A
    )
    ORDER BY ROW_RNK, RNK DESC;
    ```

  -   **Actual Results**

          [ERR-31455 : Failed to work because an internal exception occurred from an OS.[Contact Altibase's Support Center]]

  -   **Expected Results**

          no rows

- **Workaround**

  ```sql
  ALTER SESSION SET STACK SIZE= 65536;
  WITH BASE AS (
  SELECT /*+ */A.i1 ,A.i2 ,RANK() OVER(ORDER BY i2) RNK
  FROM t1 A
  )
  SELECT ROW_RNK ,RANK() OVER(PARTITION BY i1 ORDER BY RNK DESC) RNK2 ,i1 ,i2
  FROM (
  SELECT A.i1 ,A.i2 ,A.RNK ROW_RNK ,RANK() OVER(PARTITION BY A.i1 ORDER BY A.i1 DESC) RNK
  FROM BASE A
  )
  ORDER BY ROW_RNK, RNK2 DESC;
  ```

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-51374<a name=bug-51374></a> Fixed an issue in which a buffer latch was not released, causing an exception during server shutdown.

-   **module** : sm

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixed an issue in which a buffer latch was not released, causing an exception during server shutdown.

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

### BUG-51399<a name=bug-51399></a> Fixed an issue in which ERR-42000 was logged in altibase\_boot.log when an exception occurred during the state transition phase of database startup.

-   **module** : mm

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an issue in which ERR-42000 was logged in altibase\_boot.log when an exception occurred during the state transition phase of database startup.
    
    - Before : Only ERR-42000 was displayed without an error message
    
      [2025/03/19 15:35:04 82C] [PID:40062] [Thread-140190385456896] [LWP-40066]
      ERR-42000(errno=0)
    
    - After : The error code and message are displayed together.
    
      [2025/03/19 15:35:49 58E] [PID:60907] [Thread-140158181746432] [LWP-60920]
      ERR-4107a(errno=0) Unable to start up in the specified phase in the current state.
    
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

### BUG-51403<a name=bug-51403></a> Fixed an issue where large LOB inserts into memory tables caused performance degradation.

-   **module** : sm

-   **Category** : Other

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where large LOB inserts into memory tables caused performance degradation.
    
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
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 7.1.0.10.2       | 6.5.1                   | 8.12.1       | 7.1.7               | 7.4.7                        |

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

No properties added/changed/deleted.

### Performance Views

No performance views added/changed/deleted.
