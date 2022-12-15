Altibase 7.1.0.6.7 Patch Notes
==============================

<br/>

<br/>

# Table Of Contents

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Fixed Bugs](#fixed-bugs)
    - [BUG-49384 ERR-21017 : The argument is not applicable when binding null value in REMOTE_BIND_VARIABLE function. An error occurs.](#bug-49384err-21017--the-argument-is-not-applicable-when-binding-null-value-in-remote_bind_variable-function-an-error-occurs)
    - [BUG-49417 The Altibase server may abnormally terminate when a change transaction occurs on a disk table in a situation where disk index tablespace space is insufficient.](#bug-49417the-altibase-server-may-abnormally-terminate-when-a-change-transaction-occurs-on-a-disk-table-in-a-situation-where-disk-index-tablespace-space-is-insufficient)
    - [BUG-49429 If the extent size of the disk temporary tablespace is not 512K, the Altibase server abnormally terminates.](#bug-49429if-the-extent-size-of-the-disk-temporary-tablespace-is-not-512k-the-altibase-server-abnormally-terminates)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [Altibase Server Properties](#altibase-server-properties)
    - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->



Fixed Bugs
==========

### BUG-49384 ERR-21017 : The argument is not applicable when binding null value in REMOTE_BIND_VARIABLE function. An error occurs.

-   **module** : dblink

-   **Category** : Functionality

-   **Reproducibility** : Always

-   **Description** : Fixed a problem where [ERR-21017: The argument is not applicable.] error occurs when binding a null value in the REMOTE_BIND_VARIABLE function of Database Link (DBLink).
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    REMOTE_BIND_VARIABLE( 'link1', STATEMENT_ID, 1, NULL);
    ```

  - **Actual Results**

    ```sql
    [ERR-21017 : The argument is not applicable.
    In PROC1
    0013 :            RESULT := REMOTE_BIND_VARIABLE( 'link1', STATEMENT_ID, 1, NULL);
                     ^                                                                       ^
    ]
    ```

  -   **Expected Results**

          success

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49417 The Altibase server may abnormally terminate when a change transaction occurs on a disk table in a situation where disk index tablespace space is insufficient.

-   **module** : sm-disk-index

-   **Category** : Fatal

-   **Reproducibility** : Rare

-   **Description** : Fixes a bug in which the Altibase server abnormally terminates when a disk table change transaction occurs in a situation where disk index tablespace space is insufficient. When the Altibase server abnormally terminates due to this bug, the following log is left in altibase_error.log.
    
    ```bash
    IDE_ASSERT( sSegMgmtOp->mAllocNewPage( aStatistics, aMtx, aIndex->mIndexTSID, &(aIndex- >mSegmentDesc.mSegHandle),
    SDP_PAGE_INDEX_BTREE, (UChar **)aNewPage ) == IDE_SUCCESS ),
    [sdnbModule.cpp:23858], errno=[11]
    
    ERR-11123(errno=11) The tablespace does not have enough free space (
    TBS Name :tablespace_name ).
    ```
    
    You can avoid abnormal termination of the Altibase server by securing free space in the disk index tablespace.
    
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

### BUG-49429 If the extent size of the disk temporary tablespace is not 512K, the Altibase server abnormally terminates.

- **module** : sm

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixed the abnormal termination of the Altibase server when the extent size of the disk temporary tablespace is not 512K.
    
    - bug condition
      
      - When executing the CREATE TEMPORARY TABLESPACE statement 
        - Use a value other than 512K for the EXTENTSIZE clause, or 
        - When the Altibase server property SYS_TEMP_TBS_EXTENT_SIZE or USER_TEMP_TBS_EXTENT_SIZE value is set to a value other than 512K
      - This bug occurs in Altibase 7.1.0.5.1 or later with BUG-48369 reflected.
      
    - phenomenon
    
      When executing SQL using a disk temporary tablespace, the Altibase server abnormally terminates, and the following log is left in the trace log altibase_error.log.
    
      ```bash
      IDE_ASSERT( sExtDesc.mLength == SDT_WAEXTENT_PAGECOUNT )
      ```
    
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
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    7.1.0.6.7     |          6.5.1          |    8.10.1    |        7.1.7        |            7.4.7             |

> You can check the module version change history in [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.1/Altibase_7_1_Version_Histories.md).

#### Compatibility

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
