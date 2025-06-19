Altibase 7.1.0.4.6 Patch Notes
==============================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [New Features](#new-features)
  - [BUG-48161 Added a property to adjust the maximum bucket count.](#bug-48161-added-a-property-to-adjust-the-maximum-bucket-count)
- [Fixed Bugs](#fixed-bugs)
  - [BUG-48111  Fixed an issue where the CYCLE option was not properly displayed in V$SEQ when using the ENABLE SYNC TABLE option during Sequence creation.](#bug-48111%C2%A0-fixed-an-issue-where-the-cycle-option-was-not-properly-displayed-in-vseq-when-using-the-enable-sync-table-option-during-sequence-creation)
  - [BUG-48145 Fixed an issue where clients (CLI) version 7.1.0.3.0 or higher could not connect to servers version 7.1.0.2.9 or lower due to the GLOBAL_TRANSACTION_LEVEL property.](#bug-48145%C2%A0fixed-an-issue-where-clients-cli-version-71030-or-higher-could-not-connect-to-servers-version-71029-or-lower-due-to-the-global_transaction_level-property)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [Compatibility](#compatibility)
  - [Altibase Server Properties](#altibase-server-properties)
  - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
------------

### BUG-48161 Added a property to adjust the maximum bucket count.

-   **module** : qp-select-pvo

-   **Category** : Enhancement

-   **Reproducibility** : Always

-   **Description** : Added a property to adjust the maximum bucket count.

-   #### How to reproduce this bug

    -   **Reproduction conditions**

    -   **Actual Results**

    -   **Expected Results**

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
        -   New
            -   __OPTIMIZER_BUCKET_COUNT_MAX (hidden property)
                -   Description: adjust the maximum bucket count
                -   Default: 102400000
                -   Range: 1024 ~102400000
    -   Compile Option
    -   Error Code

Fixed Bugs
----------

### BUG-48111  Fixed an issue where the CYCLE option was not properly displayed in V$SEQ when using the ENABLE SYNC TABLE option during Sequence creation.

-   **module** : qp-meta

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where the CYCLE option was not displayed in V$SEQ when using the ENABLE SYNC TABLE option during Sequence creation.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    CREATE SEQUENCE S1 MINVALUE 1 MAXVALUE 5 CACHE 2 CYCLE ENABLE SYNC TABLE;
    select a.table_name, b.is_cycle from system_.sys_tables_ a, v$seq b where a.table_oid = b.seq_oid and a.table_name = 'S1';
    select * from seq;
    ```

  -   **Actual Results**

          iSQL> select a.table_name, b.is_cycle from system_.sys_tables_ a, v$seq b where a.table_oid = b.seq_oid and a.table_name = 'S1';
          TABLE_NAME                      IS_CYCLE
          -------------------------------------------------------------------
          S1                              UNKNOWN
          1 row selected.
          iSQL> select * from seq;
          USER_NAME                       SEQUENCE_NAME                   CURRENT_VALUE        INCREMENT_BY         MIN_VALUE            MAX_VALUE            CYCLE                           CACHE_SIZE
          ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
          SYS                             S1                                                   1                    1                    5                                                    2
          1 row selected.

  -   **Expected Results**

          iSQL> select a.table_name, b.is_cycle from system_.sys_tables_ a, v$seq b where a.table_oid = b.seq_oid and a.table_name = 'S1';
          TABLE_NAME                      IS_CYCLE
          -------------------------------------------------------------------
          S1                              YES
          1 row selected.
          iSQL> select * from seq;
          USER_NAME                       SEQUENCE_NAME                   CURRENT_VALUE        INCREMENT_BY         MIN_VALUE            MAX_VALUE            CYCLE                           CACHE_SIZE
          ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
          SYS                             S1                                                   1                    1                    5                    YES                             2
          1 row selected.

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48145 Fixed an issue where clients (CLI) version 7.1.0.3.0 or higher could not connect to servers version 7.1.0.2.9 or lower due to the GLOBAL_TRANSACTION_LEVEL property.

-   **module** : sharding

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where clients (CLI) version 7.1.0.3.0 or higher could not connect to servers version 7.1.0.2.9 or lower due to the GLOBAL_TRANSACTION_LEVEL property.
    
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
-------

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 7.1.0.4.6        | 6.5.1                   | 8.9.1        | 7.1.7               | 7.4.6                        |

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
