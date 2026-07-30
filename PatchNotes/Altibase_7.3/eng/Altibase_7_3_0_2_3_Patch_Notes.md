Altibase 7.3.0.2.3 Patch Notes
==============================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
  - [BUG-52430 Added a feature to enable or disable Sender IP verification during the ALA handshake process](#bug-52430)
- [Fixed Bugs](#fixed-bugs)
  - [BUG-51279 Fixed an issue where patching from version 7.3.0.x.x to 7.3.1.x.x was not possible](#bug-51279)
  - [BUG-51719 Fixed an issue where the Replication name was not displayed correctly in the receiver initialization error message](#bug-51719)
  - [BUG-52325 Improved stability of Supplemental Log processing in replication environments](#bug-52325)
  - [BUG-52381 Fixed LOB data insertion errors when using the iLoader -lightmode option](#bug-52381)
  - [BUG-52384 Fixed an issue where trigger Statement objects were not reused when repeatedly executing the same Prepared Statement with different bind values](#bug-52384)
  - [BUG-52466 Fixed incorrect results during index access after recreating a Primary Key constraint on a Temporary Table in a Volatile Tablespace](#bug-52466)
  - [BUG-52484 Fixed a server crash that could occur while printing diagnostic information after receiving an invalid protocol header](#bug-52484)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [Compatibility](#compatibility)
  - [Altibase Server Properties](#altibase-server-properties)
  - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-52430<a name=bug-52430></a> Added a feature to enable or disable Sender IP verification during the ALA handshake process

-   **module** : rp-kafkaConnector

-   **Category** : Functionality

-   **Reproducibility** : Always

-   **Description** : Added a feature that allows you to choose whether to verify the Sender IP during the ALA handshake process. The newly added `ALA_SetVerifySenderIP()` function can be used to enable or disable Sender IP verification. The default is Verify (`ALA_TRUE`).
    
    In addition, properties for configuring the same functionality have been added to oraAdapter, jdbcAdapter, and Altibase Source Connector for Kafka.
    
    - `ALA_VERIFY_SENDER_IP` (0: Do not verify, 1: Verify)
    - `ala.verify.sender.ip` (false: Do not verify, true: Verify)
    
-   **How to Reproduce**

    -   **Reproduction Steps**

    -   **Actual Result**

    -   **Expected Result**

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
        -   ALA\_VERIFY\_SENDER\_IP (ALA Properties)
            -   Value range: 0, 1
                -   1: (default) Verify
                -   0: Do not verify
        -   ala.verify.sender.ip (커넥터 Properties)
            -   Type: boolean
                -   true: (default) Verify
                -   false: Do not verify
    -   Compile Option
    -   Error Code

Fixed Bugs
==========

### BUG-51279<a name=bug-51279></a> Fixed an issue where patching from version 7.3.0.x.x to 7.3.1.x.x was not possible

- **module** : installer

- **Category** : Portability

- **Reproducibility** : Always

- **Description** : Previously, some 7.3.0.x.x versions could not be patched to 7.3.1.x.x. This issue has been fixed, and starting from 7.3.0.2.3, patching to 7.3.1.x.x works correctly. 

-   **How to Reproduce**
    -   **Reproduction Steps**
    
    -   **Actual Result**
    
    -   **Expected Result**
    
- **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-51719<a name=bug-51719></a> Fixed an issue where the Replication name was not displayed correctly in the receiver initialization error message

-   **module** : rp
-   **Category** : Message Error
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where the Replication name was not displayed correctly in the `rpERR_ABORT_RP_RECEIVER_INITIALIZE_FAIL` error message when receiver initialization failed.
    -   Before: **The receiver(%s) has not started, because the replication meta information has been changed.**
    -   After: **The receiver(<0%s>) has not started, because the replication meta information has been changed.**
    
-   **How to Reproduce**

    -   **Reproduction Steps**

    -   **Actual Result**

    -   **Expected Result**
-   **Workaround**
-   **Changes**
    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-52325<a name=bug-52325></a> Improved stability of Supplemental Log processing in replication environments

-   **module** : sm\_interface

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixed a server crash that could occur when executing UPDATE operations on disk tables with Supplemental Log enabled in a replication environment.

-   **How to Reproduce**

    -   **Reproduction Steps**

    -   **Actual Result**

    -   **Expected Result**

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-52381<a name=bug-52381></a> Fixed LOB data insertion errors when using the iLoader -lightmode option

-   **module** : sm

-   **Category** : Functional Error

-   **Reproducibility** : Always

- **Description** : Fixed an issue where LOB data was not inserted correctly when loading data with the iLoader `-lightmode` option.

  In addition, when a failure occurs during data loading with the `-lightmode` option and the table consistency cannot be guaranteed, DML operations on the affected table now return the following error:

  **[ERR-11120 : The table is inconsistent.]**

  If this error occurs, the affected table must be dropped and recreated.

-   **How to Reproduce**

    -   **Reproduction Steps**

    -   **Actual Result**

    -   **Expected Result**

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-52384<a name=bug-52384></a> Fixed an issue where trigger Statement objects were not reused when repeatedly executing the same Prepared Statement with different bind values

-   **module** : qp-psm-trigger-execute

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : When repeatedly executing the same Prepared Statement while changing only the bind values, trigger  Statement objects were not reused and new Statement objects were allocated for each execution. As a result, the number of Statement objects in the session could continue to increase, potentially causing the `There are too many statements in the session` error. After the fix, previously allocated trigger Statement objects are properly released, preventing unnecessary growth in the number of Statement objects during repeated execution.
    
-   **How to Reproduce**
    -   **Reproduction Steps**
    
    -   **Actual Result**
    
    -   **Expected Result**
    
-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-52466<a name=bug-52466></a> Fixed incorrect results during index access after recreating a Primary Key constraint on a Temporary Table in a Volatile Tablespace

-   **module** : qp-dml-pvo

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an issue that could cause incorrect results during index access after recreating a Primary Key constraint on a Temporary Table in a Volatile Tablespace.
    
-   **How to Reproduce**

    -   **Reproduction Steps**

    -   **Actual Result**

    -   **Expected Result**

-   **Workaround**

-   **Changes**
    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-52484<a name=bug-52484></a> Fixed a server crash that could occur while printing diagnostic information after receiving an invalid protocol header

-   **module** : mm
-   **Category** : Fatal
-   **Reproducibility** : Rare
-   **Description** : Fixed a server crash that could occur while printing diagnostic information after receiving an invalid protocol header. This issue could occur when a client version 6.1.1 or earlier sent an incorrect value instead of the A5 protocol header signature value (0x06). The server has been improved so that it no longer terminates abnormally when an invalid header is received.
-   **How to Reproduce**
-   **Reproduction Steps**
    
-   **Actual Result**
    
-   **Expected Result**
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
| 7.3.0.2.3        | 7.3.0                   | 9.4.1        | 7.1.8               | 7.4.9                        |

> You can check the module version change history in [Version_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.3/Altibase_7_3_Version_Histories.md).

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
