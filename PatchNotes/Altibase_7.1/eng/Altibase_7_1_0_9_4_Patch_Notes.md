# Altibase 7.1.0.9.4 Patch Notes

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

# **Table of Contents**  

- [New Features](#new-features)
    - [Improve V\$DISK\_BTREE\_HEADER and V\$MEM\_BTREE\_HEADER performance views to include index status information.](#bug-50768)
    - [BUG-50812 cdbc (C API) support on Windows Clients.](#bug-50812)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-50433 Improve to avoid accessing corrupted pages during Disk Page Recovery or service.](#bug-50433)
    - [BUG-50781 Fix an issue where two clients controlling the semaphore on a single IPC channel caused data to be re-received, resulting in an Invalid protocol sequence error.](#bug-50781)
    - [BUG-50791 Fix an issue causing server abnormal termination when the TO_CHAR function was used as an alias in a condition clause, and  multiple condition clause pushdowns on views occurred.](#bug-50791)
    - [BUG-50799 Resolve the issue where the odbccli_sl.dll was missing from the Windows installation file.](#bug-50799)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [Compatibility](#Compatibility)
    - [Altibase Server Properties](#Altibase-Server-Properties)
    - [Performance Views](#Performance-Views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-50768<a name=bug-50768></a> Improve V\$DISK\_BTREE\_HEADER and V\$MEM\_BTREE\_HEADER performance views to include index status information.

-   **module** : sm

-   **Category** : Enhancement

-   **Reproducibility** : Always

-   **Description** : V\$DISK\_BTREE\_HEADER and V\$MEM\_BTREE\_HEADER performance views now include INDEX_STATUS column which has index status information.
    
    Plus, V\$MEM\_BTREE\_HEADER also now includes IS_CONSISTENT column to indicate the consistency of the index.
    
-   **How to reproduce this bug**

    -   **Reproduction conditions**

    -   **Actual Results**

    -   **Expected Results**

-   **Workaround**

-   **Changes**

    -   Performance view
        -   V\$DISK\_BTREE\_HEADER
            -   Added INDEX_STATUS column : Indicate the status of the index
        -   V\$MEM\_BTREE\_HEADER
            -   Added INDEX_STATUS column : Indicate the status of the index
            -   Added IS_CONSISTENT column : Indicate the consistency of the index.
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50812<a name=bug-50812></a> cdbc (C API) support on Windows Clients.

-   **module** : ux-cdbc

-   **Category** : Portability

-   **Reproducibility** : Always

-   **Description** :  Windows 7.1 clients now supports cdbc(C API).

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

### BUG-50433<a name=bug-50433></a> Improve to avoid accessing corrupted pages during Disk Page Recovery or Service operations.

-   **module** : sm

-   **Category** : Fatal

-   **Reproducibility** : Unknown

-   **Description** : 
    
    1. Altibase modified to prevent access to corrupted pages during Disk Page Recovery or service.
    
    2. If a corrupted Disk Index Page is detected during service, it will be marked with an inconsistent flag, and the index will be set as an inconsistent index.
    
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

### BUG-50781<a name=bug-50781></a> Fix an issue where two clients controlling the semaphore on a single IPC channel caused data to be re-received, resulting in an Invalid protocol sequence error.

-   **module** : cm-ipc
-   **Category** : Functional Error
-   **Reproducibility** : Rare
-   **Description** : Altibase resolved the problem where two clients in one IPC channel controlled the semaphore and the received data was re-received, causing an Invalid protocol sequence error.
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

### BUG-50791<a name=bug-50791></a> Fix an issue causing server abnormal termination when the TO_CHAR function was used as an alias in a condition clause, and  multiple condition clause pushdowns on views occurred.

-   **module** : qp

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Altibase fixed an issue causing server abnormal termination when the TO_CHAR function was used as an alias in a condition clause, and  multiple condition clause pushdowns on views occurred.
    
    This bug occurred where the following conditions are all met:
    
    1. The second argument of the TO_CHAR function is a numeric or date format.
    2. The first argument of the TO_CHAR function is not a `Numeric` type.
    3. The first argument column of the TO_CHAR function exists in a subquery view where view merging does not occur, but it is pushed down.
    4. The TO_CHAR function is used in the target clause of the subquery with an alias, and this alias is used in the condition clause of the main query, causing a pushdown to the view where TO_CHAR is used.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    select * from (
         select 
               (select c.USER_NAME from SYSTEM_.SYS_COMMENTS_ c where c.table_name = a.table_name and c.COLUMN_NAME is null limit 1) as usernm,
               a.table_name, 
               (select c.comments from SYSTEM_.SYS_COMMENTS_ c where c.table_name = a.table_name and c.COLUMN_NAME is null limit 1) as tablenm,
               to_char((b.fixed_alloc_mem+b.var_alloc_mem)/1024/1024,'999,999,999') || 'MB' as alloc,
               to_char((b.fixed_used_mem+b.var_used_mem)/1024/1024,'999,999,999') || 'MB' as used
          from system_.sys_tables_ a, v$memtbl_info b
         where a.table_oid = b.table_oid
           and a.user_id <> (select user_id from system_.sys_users_ where user_name = 'SYSTEM_')
           and a.table_type = 'T'
          order by (b.fixed_alloc_mem+b.var_alloc_mem) desc)
          where alloc != '0MB';
    ```

  - **Actual Results**

    ```sql
    [ERR-91015 : Communication failure.]
    ```

  -   **Expected Results**

          No rows selected.

- **Workaround**

  ```sql
  Use NO_PUSH_SELECT_VIEW hint
  
  select /*+ NO_PUSH_SELECT_VIEW(AA) */ * from (
       select /*+  */
             (select /*+   */c.USER_NAME from SYSTEM_.SYS_COMMENTS_ c where c.table_name = a.table_name and c.COLUMN_NAME is null limit 1) as usernm,
             a.table_name, 
             (select /*+  */c.comments from SYSTEM_.SYS_COMMENTS_ c where c.table_name = a.table_name and c.COLUMN_NAME is null limit 1) as tablenm,
             to_char((b.fixed_alloc_mem+b.var_alloc_mem)/1024/1024,'999,999,999') || 'MB' as alloc,
             to_char((b.fixed_used_mem+b.var_used_mem)/1024/1024,'999,999,999') || 'MB' as used
        from system_.sys_tables_ a, v$memtbl_info b
       where a.table_oid = b.table_oid
         and a.user_id <> (select /*+ */user_id from system_.sys_users_ where user_name = 'SYSTEM_')
         and a.table_type = 'T'
        order by (b.fixed_alloc_mem+b.var_alloc_mem) desc) AA
        where alloc != '0MB';
  ```

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50799<a name=bug-50799></a> Resolve the issue where the odbccli_sl.dll was missing from the Windows installation file.

-   **module** : pkg-map

-   **Category** : Portability

-   **Reproducibility** : Always

-   **Description** : Altibase fixed the issue that odbccli_sl.dll was missing form the Windows installation file.

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
| 7.1.0.9.4        | 6.5.1                   | 8.11.1       | 7.1.7               | 7.4.7                        |

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
