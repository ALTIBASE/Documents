Altibase 7.1.0.10.4 Patch Notes
=================================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-51484 Improved jdbcAdapter to support batch execution of UPDATE queries.](#bug-51484)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-51477 Fixed an issue where UPDATE triggers stop working under certain conditions.](#bug-51477)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [Compatibility](#compatibility)
    - [Altibase Server Properties](#altibase-server-properties)
    - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# New Features

### BUG-51484<a name=bug-51484></a> Improved jdbcAdapter to support batch execution of UPDATE queries.

-   **module** : rp-jdbcAdapter

-   **Category** : Enhancement

-   **Reproducibility** : Always

-   **Description** : Improved jdbcAdapter to support batch execution of UPDATE queries.

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

### BUG-51477<a name=bug-51477></a> Fixed an issue where UPDATE triggers stop working under certain conditions.

-   **module** : qp-psm-trigger-execute

-   **Category** : Functional Error

-   **Reproducibility** : Rare

-   **Description** : Fixed an issue where an `UPDATE` trigger may stop working under certain conditions.
    
    The issue occurred only when **all** of the following conditions were met:
    
    - An `UPDATE` trigger **with explicitly specified column names** exists, and
    - One of the following DDL operations is performed on the trigger's target table:
      - Executing `CREATE REPLICATION`, `DROP REPLICATION` statement on the target table.
      - Creating or altering the `UPDATE` trigger.
      - Executing a `TRUNCATE TABLE` statement on the target table.
      - Executing a `CREATE INDEX` statement on the target table.
    
    > **This issue does not occur in the following cases:**
    >
    > - The `UPDATE` trigger does **not** specify column names.
    > - Executing DDLs such as `ADD`, `DROP`, `RENAME`, or `MODIFY` column on the target table.
    
- **How to reproduce this bug**

  -   Reproduction conditions

      ```sql
      DROP TABLE t1;
      DROP TABLE t2;
      CREATE TABLE t1 (c1 INTEGER PRIMARY KEY, c2 INTEGER);
      CREATE TABLE t2 (c1 INTEGER);
       
      INSERT INTO t1 VALUES(1, 2);
       
      CREATE OR REPLACE TRIGGER trig_on_t1
      BEFORE UPDATE OF c2 ON t1
      REFERENCING NEW AS new_row
      FOR EACH ROW
      BEGIN
        INSERT INTO t2 VALUES( new_row.c2 );
      END;
      /
      SELECT * FROM t1;
      SELECT * FROM t2;
      -- Normal operation
      UPDATE t1 SET c2 = c2 + 1;
      
      -- CREATE REPLICATION
      CREATE REPLICATION repl1 WITH '127.0.0.1', 21113 FROM sys.t1 TO sys.t1;
      
      -- Abnormal behavior
      UPDATE t1 SET c2 = c2 + 1;
      SELECT * FROM t1;
      SELECT * FROM t2;
      ```
      
  -   **Actual Results**
  
      ```sql
      iSQL> select * from t1;
      C1          C2
      ---------------------------
      1           4
      1 row selected.
      iSQL> select * from t2;
      C1
      --------------
      3
      1 row selected.
      ```
      
  -   **Expected Results**

      ```sql
      iSQL> select * from t1;
      C1          C2
      ---------------------------
      1           4
      1 row selected.
      iSQL> select * from t2;
      C1
      --------------
      4
      1 row selected.
      ```
  
- **Workaround**

      When a trigger stops working, the issue can be resolved using one of the following methods:
      1. Recreate all UPDATE triggers that specify column names on the target table.
      2. Recompile the affected trigger using the ALTER TRIGGER trigger_name COMPILE statement.

- Changes

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 7.1.0.10.4       | 6.5.1                   | 8.12.1       | 7.1.7               | 7.4.7                        |

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

No properties added/changed/deleted.

### Performance Views

No performance views added/changed/deleted.
