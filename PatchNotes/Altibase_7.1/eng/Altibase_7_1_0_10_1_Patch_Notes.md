# Altibase 7.1.0.10.1 Patch Notes

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Fixed Bugs](#fixed-bugs)
    - [BUG-51170 Improved handling of spurious wakeups in condition wait in SM modules](#bug-51170)
    - [BUG-51366 Fixed a concurrency issue with reading currentSN](#bug-51366)
    - [BUG-51372 Fixed LOB transaction log handling error during replication restart](#bug-51372)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [Compatibility](#compatibility)
    - [Altibase Server Properties](#altibase-server-properties)
    - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Fixed Bugs
==========

### BUG-51170<a name=bug-51170></a> Improved handling of spurious wakeups in condition wait in SM modules

-   **module** : sm\_resource

-   **Category** : Fatal

-   **Reproducibility** : Rare

-   **Description** : Fix spurious wakup response code in pthread_cond_wait, pthread_cond_timewait to prevent them from performing unintended behavior.

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

### BUG-51297<a name=bug-51170></a> Fixed the issue where a compile error occurs when using the altibase_home/install/altibase_env.mk file to compile the application on HP and AIX due to the '-Wno-narrowing' option.

- **module** : installer

- **Category** : Functional Error

- **Reproducibility** : Rare

- **Description** : Fixed the issue where a compile error occurs when using the altibase_home/install/altibase_env.mk file to compile the application on HP and AIX due to the '-Wno-narrowing' option.

- #### How to reproduce this bug

  -   **Reproduction conditions**

  -   **Actual Results**

  -   **Expected Results**

- **Workaround**

- **Changes**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

### BUG-51366<a name=bug-51366></a> Fixed a concurrency issue with reading currentSN

-   **module** : sm
-   **Category** : Functional Error
-   **Reproducibility** : Rare
-   **Description** : When the sender reads the currentSN, a concurrency issue may cause a partial read, leading to incorrect values being read and potentially causing replication to stop abnormally. To prevent this, the concurrency issue has been fixed to ensure that partial reads no longer occur.
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

### BUG-51372<a name=bug-51372></a> Fixed LOB transaction log handling error during replication restart

-   **module** : rp-sender

-   **Category** : Functional Error

-   **Reproducibility** : Rare

-   **Description** : During replication restart, the sender failed to exclude already processed LOB transaction logs, causing some logs that should not have been transmitted to be sent incorrectly. This resulted in a **"Transaction has not begun."** error on the receiver. The issue has been resolved by improving the logic to prevent unnecessary LOB transaction logs from being transmitted.
    
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
| 7.1.0.10.1       | 6.5.1                   | 8.12.1       | 7.1.7               | 7.4.7                        |

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
