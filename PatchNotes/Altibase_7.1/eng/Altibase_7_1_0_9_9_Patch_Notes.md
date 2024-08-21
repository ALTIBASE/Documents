Altibase 7.1.0.9.9 Patch Notes
================================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-47423 Improve APRE to support RETURNING INTO clause.](#bug-47423)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-50949 When a comment in the aku configuration file has no text after '#', an error occurs.](#bug-50949)
    - [BUG-50997  A results error can occur under certain conditions when using an aggregate function in a subquery that references an outer query](#bug-50997)
    - [BUG-51004 A "Function sequence error" may occur if the type or pointer of the variable bound to altibase_stmt_bind_param changes.](#bug-51004)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [Compatibility](#Compatibility)
    - [Altibase Server Properties](#Altibase-Server-Properties)
    - [Performance Views](#Performance-Views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-47423<a name=bug-47423></a> Improve APRE to support RETURNING INTO clause.

-   **module** : mm-apre

-   **Category** : Functionality

-   **Reproducibility** : Always

-   **Description** : Altibase improved APRE to support RETURNING INTO clause.

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

### BUG-50949<a name=bug-50949></a> When a comment in the aku configuration file has no text after '#', an error occurs.

-   **module** : aku
-   **Category** : Enhancement
-   **Reproducibility** : Always
-   **Description** : Altibase resolved the issue where an error occurred when a comment in the aku configuration file (aku.conf) had no text after the '#'.
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

### BUG-50997<a name=bug-50997></a> A results error can occur under certain conditions when using an aggregate function in a subquery that references an outer query.

-   **module** : qp

-   **Category** : Functional Error

-   **Reproducibility** : Always

- **Description** : Altibase fixed an issue where a results error occurred under specific conditions when using an aggregate function in a subquery that references an outer query.

  This bug only occurred when all of the following conditions were met:

  1.  An `OR` operator is used within the conditions of an `AND` operation.
  2. The condition in the `OR` operator contains a subquery that references the outer query.
  3. The subquery mentioned in 2. uses an aggregate function.

- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    drop table T1;
    drop table T2; 
    
    create table T1
    (
     REV integer,
     REVTYPE smallint,
     id integer
    );
    
    insert into T1 values(7,              7,           0);
    insert into T1 values(6,              5,           2);
    insert into T1 values(5,              6,           1);
    
    create table T2
    (
     REV integer ,
     REVTYPE smallint,
     id integer
    );
    
    insert into T2 values(15,          3,      2);           
    insert into T2 values(17,          1,      0);           
    insert into T2 values(10,          3,      1);           
    
    select A.id 
    from T1 A, T2 B
    where 
       A.id = B.id
      and 
    (
        (B.REV = (select min(BB.REV) from T2 BB where BB.REV < 23 and B.id = BB.id )
          and 
         A.REV = (select (AA.REV) from T1 AA where AA.REV < 23 and A.id = AA.id)
        )
      or  (
        A.REVTYPE = 2
         and B.REVTYPE <= 2
           )
    );
    ```

  - **Actual Results**

    ```
    ID
    --------------
    1
    1 row selected.
    ```

  - **Expected Results**

    ```
    ID
    --------------
    0
    2
    1
    3 rows selected.
    ```

- **Workaround**

- **Changes**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

### BUG-51004<a name=bug-51004></a> A "Function sequence error" may occur if the type or pointer of the variable bound to altibase_stmt_bind_param() changes.

-   **module** : ux-cdbc

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Altibase fixed the issue to prevent a "Function sequence error" when the type or pointer of the variable bound to altibase_stmt_bind_param changes.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

        altibase_stmt_prepare (select ... )
        altibase_stmt_bind_param(sStmt, sBind1)
        altibase_stmt_execute
        altibase_stmt_free_result
        altibase_stmt_bind_param(sStmt, sBind2)
        altibase_stmt_execute

  - **Actual Results**

        altibase_stmt_prepare (select ... )
        altibase_stmt_bind_param(sStmt, sBind1)
        altibase_stmt_execute
        altibase_stmt_free_result
        altibase_stmt_bind_param(sStmt, sBind2)  -> Function sequence error
        altibase_stmt_execute

  -   **Expected Results**

          altibase_stmt_prepare (select ... )
          altibase_stmt_bind_param(sStmt, sBind1)
          altibase_stmt_execute
          altibase_stmt_free_result
          altibase_stmt_bind_param(sStmt, sBind2)  -> Success
          altibase_stmt_execute

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
|    7.1.0.9.9     |          6.5.1          |    8.11.1    |        7.1.7        |            7.4.7             |

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
