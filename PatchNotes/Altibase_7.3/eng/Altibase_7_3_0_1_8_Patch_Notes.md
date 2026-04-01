Altibase 7.3.0.1.8 Patch Notes
================================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-52188 Improved stability of diagnostic dump information collection on server crash](#bug-52188)
    - [BUG-52192 Improved error messages when system call fails during file backup.](#bug-5219)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-51201 Fixed an issue where XLog application order could be reversed depending on partition order if replication target partitions are not divided by PK.](#bug-51201)
    - [BUG-51324  Fixed performance degradation when collecting disk index statistics in parallel.](#bug-51324)
    - [BUG-52171 Fixed a server crash when renaming a table that has a trigger using SQL functions.](#bug-52171)
    - 
    - [BUG-52205 Fixed a memory access error during meta information updates related to offline replication.](#bug-52205)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [Compatibility](#compatibility)
    - [Properties](#properties)
    - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-52188<a name=bug-52188></a> Improved stability of diagnostic dump information collection on server crash

-   **module** : mm
-   **Category** : Reliability
-   **Reproducibility** : Rare
-   **Description** : Fixed an error where session and task diagnostic information were missing in certain situations upon abnormal termination. Also improved the dump to include communication read buffers and service thread Statement ID to assist in failure analysis.

### BUG-52192<a name=bug-52192></a> Improved error messages when system call fails during file backup.

-   **module** : sm

-   **Category** : Enhancement

-   **Reproducibility** : Always

-   **Description** : Previously, when a system call failed during file backup, detailed information was not sufficiently recorded in the log, making it difficult to determine the exact cause. It has been improved to output more detailed error messages, including information about the failed system call.


Fixed Bugs
==========

### BUG-51201<a name=bug-51201></a> Fixed an issue where XLog application order could be reversed depending on partition order if replication target partitions are not divided by PK.

-   **module** : rp-jdbcAdapter
-   **Category** : Functional Error
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where XLogs could be applied in reverse order in the adapter. This could occur when the replication target partitions of the Active server were not partitioned by Primary Key (PK), depending on the partition order.

### BUG-51324<a name=bug-51324></a> Fixed performance degradation when collecting disk index statistics in parallel.

-   **module** : sm

-   **Category** : Other

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where more time was consumed when collecting disk index statistics in parallel.


### BUG-52171<a name=bug-5217></a> Fixed a server crash when renaming a table that has a trigger using SQL functions.

-   **module** : qp-psm-trigger-execute

-   **Category** : Fatal

- **Reproducibility** : Always

- **Description** : Fixed an issue where the server could crash when renaming a table that has a trigger using SQL functions.

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

- **Workaround** : Drop the trigger, rename the table, and then recreate the trigger.

### BUG-52119<a name=bug-52119></a> Fixed an issue where UPDATE operations failed while applying replicated data to the target table via the jdbcAdapter with SUPPLEMENTAL LOG enabled

-   **module** : rp-jdbcAdapter

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where UPDATE operations failed while applying replication data to the target table via the jdbcAdapter with SUPPLEMENTAL LOG enabled.

### BUG-52205<a name=bug-52205></a> Fixed a memory access error during meta information updates related to offline replication.

-   **module** : rp
-   **Category** : Memory Error
-   **Reproducibility** : Always
-   **Description** : Fixed a memory access error that occurred while updating meta information related to offline replication in a replication environment.

# Changes

### Version Info

| **Altibase Version** | **Database Binary Version** | **Meta Version** | **CM Protocol Version** | **Replication Protocol Version** |
| -------------------- | --------------------------- | ---------------- | ----------------------- | -------------------------------- |
| 7.3.0.1.8            | 7.3.0                       | 9.4.1            | 7.1.8                   | 7.4.9                            |

### Compatibility

#### Database binary version

The database binary version has not changed.

> The database binary version indicates the compatibility of database image files and log files. If this version needs to be patched to a different version, the database must be reorganized.

#### Meta Version

The meta version has not changed.

> If you want to roll back the patch after patching to a version with a changed meta version, see [Meta Downgrade](https://manual.altibase.com/7.3/en/start-here/install/3.-Uninstalling-Altibase-and-Meta-Downgrade/#meta-downgrade).

#### CM protocol Version

The cm protocol version has not changed.

#### Replication protocol Version

The replication protocol version has not changed.

### Properties

No properties added/changed/deleted.

### Performance Views

No performance views added/changed/deleted.
