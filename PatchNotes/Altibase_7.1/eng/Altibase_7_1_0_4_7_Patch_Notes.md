Altibase 7.1.0.4.7 Patch Notes
==============================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Fixed Bugs](#fixed-bugs)
  - [BUG-48201 Fixed an issue causing AIX 7.2 to hang](#bug-48201%C2%A0fixed-an-issue-causing-aix-72-to-hang)
  - [BUG-48210 Fixed an issue with incorrect exception handling during commit failures.](#bug-48210%C2%A0fixed-an-issue-with-incorrect-exception-handling-during-commit-failures)
  - [BUG-48212  Added code to check session timeout during reading LOB data.](#bug-48212%C2%A0-added-code-to-check-session-timeout-during-reading-lob-data)
  - [BUG-48224 Fixed an issue where the server could shut down abnormally when selecting from v$plantext with graph information being displayed.](#bug-48224%C2%A0fixed-an-issue-where-the-server-could-shut-down-abnormally-when-selecting-from-vplantext-with-graph-information-being-displayed)
  - [BUG-48226 Fixed an issue where an internal server error occurred during disk temp table merge sort.](#bug-48226-fixed-an-issue-where-an-internal-server-error-occurred-during-disk-temp-table-merge-sort)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [Compatibility](#compatibility)
  - [Altibase Server Properties](#altibase-server-properties)
  - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Fixed Bugs
----------

### BUG-48201 Fixed an issue causing AIX 7.2 to hang

-   **module** : id

-   **Category** : Hang

-   **Reproducibility** : Always

-   **Description** : Fixed an issue causing AIX 7.2 to hang.
    
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

### BUG-48210 Fixed an issue with incorrect exception handling during commit failures.

-   **module** : sm\_transaction

-   **Category** : Fatal

-   **Reproducibility** : Rare

-   **Description** : Fixed an issue with incorrect exception handling during commit failures.

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

### BUG-48212  Added code to check session timeout during reading LOB data.

-   **module** : sm

-   **Category** : Hang

-   **Reproducibility** : Frequence

-   **Description** : Added code to check session timeout during reading LOB data.

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

### BUG-48224 Fixed an issue where the server could shut down abnormally when selecting from v$plantext with graph information being displayed.

-   **module** : qp-select

-   **Category** : Fatal

-   **Reproducibility** : Rare

-   **Description** : Fixed an issue where the server could shut down abnormally when selecting from v$plantext with graph information being displayed.

-   **How to reproduce this bug**

    -   **Reproduction conditions**

    -   **Actual Results**

    -   **Expected Results**

-   **Workaround**

        TRCLOG_EXPLAIN_GRAPH = 0

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48226 Fixed an issue where an internal server error occurred during disk temp table merge sort.

-   **module** : sm-disk-collection

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where an internal server error occurred during disk temp table merge sort.

- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    CREATE TABLE T1 ( I1 CHAR(495) ) tablespace sys_tbs_disk_data;
    CREATE TABLE T2 ( I1 CHAR(495) ) tablespace sys_tbs_disk_data;
    
    INSERT /*+APPEND*/ INTO T1 SELECT ROWNUM/5 FROM DUAL CONNECT BY LEVEL <= 1500;
    INSERT /*+APPEND*/ INTO T2 SELECT ROWNUM/5+1 FROM DUAL CONNECT BY LEVEL <= 1500;
    SELECT COUNT(*) FROM (SELECT /*+ USE_SORT(T1,T2)  */ T1.I1 FROM T1 JOIN T2 ON T1.I1=T2.I1 );
    DROP TABLE T1;
    DROP TABLE T2;
    ```

  - **Actual Results**

    ```sql
    SELECT COUNT(*) FROM (SELECT /*+ USE_SORT(T1,T2)  */ T1.I1 FROM T1 JOIN T2 ON T1.I1=T2.I1 );
    [ERR-11069 : Internal server error in the storage manager ([FAILURE] ERR-0109E(error=16) Internal server error.)]
    ```

  -   **Expected Results**

      ```sql
      SELECT COUNT(*) FROM (SELECT /*+ USE_SORT(T1,T2)  */ T1.I1 FROM T1 JOIN T2 ON T1.I1=T2.I1 );
      COUNT(*)
      -----------------------
      1495
      1 row selected.
      ```

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
| 7.1.0.4.7        | 6.5.1                   | 8.9.1        | 7.1.7               | 7.4.6                        |

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
