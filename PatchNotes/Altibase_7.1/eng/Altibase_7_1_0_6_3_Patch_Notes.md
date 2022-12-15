Altibase 7.1.0.6.3 Patch Notes
==============================

<br/>

<br/>

# Table Of Contents

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [New Features](#new-features)
    - [BUG-49274 Adds a property to altiComp that allows the user to adjust the commit count.](#bug-49274adds-a-property-to-alticomp-that-allows-the-user-to-adjust-the-commit-count)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-49324 Exception handling is added to avoid the possibility of abnormal termination of Altibase while the statement object remains.](#bug-49324exception-handling-is-added-to-avoid-the-possibility-of-abnormal-termination-of-altibase-while-the-statement-object-remains)
    - [BUG-49326 An 'error while loading shared libraries' error occurs when running the Altibase server in RHEL 8.](#bug-49326-an-error-while-loading-shared-libraries-error-occurs-when-running-the-altibase-server-in-rhel-8)
    - [BUG-49350 When extracting the queue (QUEUE) object schema from aexport, an error [ERR-00000:] occurs.](#bug-49350when-extracting-the-queue-queue-object-schema-from-aexport-an-error-err-00000-occurs)
    - [BUG-49354 Remove V$QUEUE added in BUG-49063 and add V$QUEUE_DELETE_OFF.](#bug-49354remove-vqueue-added-in-bug-49063-and-add-vqueue_delete_off)
    - [BUG-49364 If null padding occurs on the lowest LEFT OUTER JOIN and no null padding occurs on the middle LEFT OUTER JOIN, the SQL results in an error.](#bug-49364if-null-padding-occurs-on-the-lowest-left-outer-join-and-no-null-padding-occurs-on-the-middle-left-outer-join-the-sql-results-in-an-error)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [Altibase Server Properties](#altibase-server-properties)
    - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->



New Features
============

### BUG-49274 Adds a property to altiComp that allows the user to adjust the commit count.

-   **module** : ux-audit(altiComp)
-   **Category** : Functionality
-   **Reproducibility** : Always
-   **Description** : Adds a property [COUNT\_TO\_COMMIT](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/eng/Utilities%20Manual.md#count_to_commit) to altiComp that allows the user to set the commit count.
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

### BUG-49324 Exception handling is added to avoid the possibility of abnormal termination of Altibase while the statement object remains.

-   **module** : qp-meta

-   **Category** : Memory Error

-   **Reproducibility** : Always

-   **Description** : Exception handling is added to avoid the possibility of abnormal termination of Altibase while the statement object remains.

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

### BUG-49326 An 'error while loading shared libraries' error occurs when running the Altibase server in RHEL 8.

-   **module** : installer

-   **Category** : Portability

-   **Reproducibility** : Always

-   **Description** : In RHEL 8, the ncurses (including tinfo) library version has been changed to 6.1. Since Altibase requires ncurses 5 version, errors may occur when running Altibase server in RHEL 8.
    The ncurses library guarantees source-level compatibility (API) and binary compatibility (ABI) at the same time from ncurses 5 to ncurses 6.2. If the files libncurses.so.5 and libtinfo.so.5 do not exist, the Altibase server package installer creates symbolic links under $ALTIBASE_HOME/lib.

    You can also check the related content in the [Installation Guide](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/eng/Installation%20Guide.md#red-hat-enterprise-linux-8) manual.

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

### BUG-49350 When extracting the queue (QUEUE) object schema from aexport, an error [ERR-00000:] occurs.

-   **module** : ux-aexport

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed a bug where an error [ERR-00000:] occurred when extracting the queue (QUEUE) object schema from aexport. 

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

### BUG-49354 Remove V$QUEUE added in BUG-49063 and add V$QUEUE_DELETE_OFF.

-   **module** : sm

-   **Category** : Usability

-   **Reproducibility** : Always

-   **Description** : Remove V$QUEUE added in BUG-49063 and add V$QUEUE_DELETE_OFF.
    
-   **How to reproduce this bug**

    -   **Reproduction conditions**

    -   **Actual Results**

    -   **Expected Results**

-   **Workaround**

-   **Changes**

    -   Performance view
        -   Delete the V$QUEUE

        - Add V\$QUEUE\_DELETE\_OFF
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49364 If null padding occurs on the lowest LEFT OUTER JOIN and no null padding occurs on the middle LEFT OUTER JOIN, the SQL results in an error.

-   **module** : qp-select

-   **Category** : Reliability

-   **Reproducibility** : Always

-   **Description** : If null padding occurs on the lowest LEFT OUTER JOIN and no null padding occurs on the middle LEFT OUTER JOIN, the SQL results in an error. This bug occurs when right read skip function is enabled on nested LEFT OUTER JOINs.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    DROP TABLE AA CASCADE;
    DROP TABLE BB CASCADE;
    DROP TABLE CC CASCADE;
    DROP TABLE DD CASCADE;
    
    CREATE TABLE AA (KEY INT, VAL INT ) TABLESPACE SYS_TBS_DISK_DATA;
    CREATE TABLE BB (KEY INT, VAL INT ) TABLESPACE SYS_TBS_DISK_DATA;
    CREATE TABLE CC (KEY INT, VAL INT ) TABLESPACE SYS_TBS_DISK_DATA;
    CREATE TABLE DD (KEY INT, VAL INT ) TABLESPACE SYS_TBS_DISK_DATA;
    
    ALTER TABLE AA ADD CONSTRAINT AA_PK PRIMARY KEY (KEY);
    ALTER TABLE BB ADD CONSTRAINT BB_PK PRIMARY KEY (KEY);
    ALTER TABLE CC ADD CONSTRAINT CC_PK PRIMARY KEY (KEY);
    ALTER TABLE DD ADD CONSTRAINT DD_PK PRIMARY KEY (KEY);
    
    INSERT INTO AA VALUES(1, 1);
    INSERT INTO BB VALUES(1, 1);
    INSERT INTO CC VALUES(2, 2);
    INSERT INTO DD VALUES(1, 1);
    
    ALTER SYSTEM SET __LEFT_OUTER_SKIP_RIGHT_ENABLE = 1;
    
    SELECT
           /*+ no_plan_cache LEADING(A) USE_NL(A B C D) */
           A.KEY
         , K.VAL
      FROM AA A
           LEFT OUTER JOIN CC C ON C.KEY = A.KEY AND C.KEY = 2
           LEFT OUTER JOIN DD D ON D.KEY = A.KEY
           LEFT OUTER JOIN BB K ON K.KEY = D.KEY;
    ```
    
  - **Actual Results**
  
    ```sql
    KEY         VAL
    ---------------------------
    1           
    1 row selected.
    ```
  
  -   **Expected Results**
  
      ```sql
      KEY         VAL
      ---------------------------
      1           1
      1 row selected.
      ```
  
- **Workaround**

  ```sql
  ALTER SYSTEM SET __LEFT_OUTER_SKIP_RIGHT_ENABLE = 0;
  ```

- **Changes**

  -   Performance view

  -   Property
  -   Compile Option
  -   Error Code

Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    7.1.0.6.3     |          6.5.1          |    8.10.1    |        7.1.7        |            7.4.6             |

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

- V\$QUEUE\_DELETE\_OFF

#### Changed Performance Views

#### Deleted Performance Views

- V\$QUEUE
