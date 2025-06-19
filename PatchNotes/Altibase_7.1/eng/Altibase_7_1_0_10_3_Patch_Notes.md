Altibase 7.1.0.10.3 Patch Notes
===============================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-51446 Improved altibase_error.log to include additional diagnostic information when the server shuts down abnormally (e.g., SIGSEGV)](#bug-51446)
    - [BUG-51452 Improved handling of mismatched extend ranges of the log anchor backup file and the data backup file during incomplete recovery.](#bug-5145284)
    - [BUG-51466 GUID datatype support in Altibase EF Core](#bug-51466)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-51471 Fixed an issue where DB creation fails when BUFFER_AREA_SIZE is set to more than 820GB.](#bug-51471)
    - [BUG-51475 Fixed an issue where the `AS MASTER/SLAVE` clause was missing from the DDL of replication objects generated when performing an aexport.](#bug-51475)
    - [BUG-51476 Fixed an issue where the `AS MASTER/SLAVE` clause was missing when extracting the replication creation DDL using the DBMS_METADATA package.](#bug-51476)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [Compatibility](#compatibility)
    - [Altibase Server Properties](#altibase-server-properties)
    - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-51446<a name=bug-51446></a> Improved altibase_error.log to include additional diagnostic information when the server shuts down abnormally (e.g., SIGSEGV)

-   **module** : mm

-   **Category** : Maintainability

-   **Reproducibility** : Frequence

-   **Description** : Enhance altibase_error.log to include additional diagnostic information when the server shuts down abnormally (e.g., SIGSEGV).

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

### BUG-51452<a name=bug-51452></a> Improved handling of mismatched extend ranges of the log anchor backup file and the data backup file during incomplete recovery.

-   **module** : sm

-   **Category** : Enhancement

-   **Reproducibility** : Always

-   **Description** : If the extend ranges of the log anchor backup file and the data backup file do not match, the server may shut down abnormally during incomplete recovery due to invalid page states. This patch improves the recovery process to allow incomplete recovery to proceed even when the extend ranges of the two files are inconsistent.

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

### BUG-51466<a name=bug-51466></a> GUID datatype support in Altibase EF Core

-   **module** : adonet
-   **Category** : Functionality
-   **Reproducibility** : Always
-   **Description** : Added the Guid data type to the data types in .NET Core that are supported in Altibase EF Core. 

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

### BUG-51471<a name=bug-51471></a> Fixed an issue where DB creation fails when BUFFER_AREA_SIZE is set to more than 820GB.

-   **module** : sm

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where DB creation fails when BUFFER_AREA_SIZE is set to more than 820 GB.

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

### BUG-51475<a name=bug-51475></a> Fixed an issue where the `AS MASTER/SLAVE` clause was missing from the DDL of replication objects generated when performing an aexport.

-   **module** : ux-aexport

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where the `AS MASTER/SLAVE` clause was missing from the DDL of replication objects generated when performing an aexport.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    DROP TABLE t1;
    CREATE TABLE t1 (c1 INT PRIMARY KEY, c2 INT);
    CREATE REPLICATION rep1 AS MASTER WITH 'localhost', 31136 FROM sys.t1 TO sys.t1;
    
    $aexport -s localhost -u sys -p manager
    ```

  - **Actual Results**

    ```sql
    $cat ALL_CRT_REP.sql
    
    DROP REPLICATION "REP1";
    CREATE REPLICATION "REP1" WITH 'localhost', 31136
    FROM "SYS"."T1" TO "SYS"."T1";
    ```

  -   **Expected Results**

      ```sql
      $cat ALL_CRT_REP.sql
      
      DROP REPLICATION "REP1";
      CREATE REPLICATION "REP1" AS MASTER
      WITH 'localhost', 31136
      FROM "SYS"."T1" TO "SYS"."T1";
      ```

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-51476<a name=bug-51476></a> Fixed an issue where the `AS MASTER/SLAVE` clause was missing when extracting the replication creation DDL using the DBMS_METADATA package.

-   **module** : ux-dbms_metadata

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where the `AS MASTER/SALVE` clause was missing when extracting the replication creation DDL using the DBMS_METADATA package.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    set vertical on;
    drop table t1;
    create table t1 (c1 int primary key, c2 int);
    create replication rep1 as master with 'localhost', 31136 from sys.t1 to sys.t1;
    
    select to_char(dbms_metadata.get_ddl('REPLICATION','REP1',null)) as ddl from dual;
    ```

  - **Actual Results**

    ```sql
    DDL : CREATE REPLICATION "REP1" WITH 'localhost', 31136
    FROM "SYS"."T1" TO "SYS"."T1"
    1 row selected.
    ```

  -   **Expected Results**

      ```sql
      DDL : CREATE REPLICATION "REP1" AS MASTER
      WITH 'localhost', 31136
      FROM "SYS"."T1" TO "SYS"."T1"
      1 row selected.
      ```

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
| 7.1.0.10.3       | 6.5.1                   | 8.12.1       | 7.1.7               | 7.4.7                        |

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
