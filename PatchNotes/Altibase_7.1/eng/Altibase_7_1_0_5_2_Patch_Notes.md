Altibase 7.1.0.5.2 Patch Notes
================================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [New Features](#new-features)
  - [BUG-48380 Improved performance of newJDBC fetch.](#bug-48380%C2%A0improved-performance-of-newjdbc-fetch)
  - [BUG-48510 Improved performance of MEMORY table INDEX SCAN and FULL SCAN.](#bug-48510%C2%A0improved-performance-of-memory-table-index-scan-and-full-scan)
- [Fixed Bugs](#fixed-bugs)
  - [BUG-42525 Fixed an issue where the database is not created when a non-alphabetic value is entered for DB_NAME in the Installer.](#bug-42525%C2%A0fixed-an-issue-where-the-database-is-not-created-when-a-non-alphabetic-value-is-entered-for-db_name-in-the-installer)
  - [BUG-48433 Improved the issue where the call stack and OS error messages are mixed in the altibase_error.log during dumptrc execution.](#bug-48433%C2%A0improved-the-issue-where-the-call-stack-and-os-error-messages-are-mixed-in-the-altibase_errorlog-during-dumptrc-execution)
  - [BUG-48523 Fixed the issue where the server shuts down if the statement object is not cleaned up during session termination.](#bug-48523%C2%A0fixed-the-issue-where-the-server-shuts-down-if-the-statement-object-is-not-cleaned-up-during-session-termination)
  - [BUG-48526 Fixed the issue where a result error occurs when an arbitrary index key is used more than once in the WHERE clause and a host variable is used in the OR condition.](#bug-48526%C2%A0fixed-the-issue-where-a-result-error-occurs-when-an-arbitrary-index-key-is-used-more-than-once-in-the-where-clause-and-a-host-variable-is-used-in-the-or-condition)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [Compatibility](#compatibility)
  - [Altibase Server Properties](#altibase-server-properties)
  - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
------------

### BUG-48380 Improved performance of newJDBC fetch.

- **module** : mm-jdbc

- **Category** : Enhancement

- **Reproducibility** : Always

- **Description** : Improved performance of newJDBC fetch. 
  To take advantage of this feature, you must patch your JDBC driver and add the connection property reuse_resultset=true.

- #### How to reproduce this bug

  -   **Reproduction conditions**

  -   **Actual Results**

  -   **Expected Results**

- **Workaround**

-   **Changes**

  - Performance view
  - Property
  
    - Add JDBC Connection Properties
       * reuse_resultset
           * Description : Specifies whether to reuse the ResultSet object when multiple ResultSet objects were created by executeQuery() method on the same PreparedStatement object. When it is set to true, it reuses the ResultSet object. When close() method is used on the first newly created ResultSet object, the resource is released and an error occurs when another ResultSet object is used. To prevent this, the next ResultSet object has to be created after the resource of the first ResultSet object is released. When it is set to false, ResultSet object will not be reused.
           * default value : false (Do not reuse ResultSet)
  - Compile Option
  - Error Code

### BUG-48510 Improved performance of MEMORY table INDEX SCAN and FULL SCAN.

-   **module** : sm-mem-index

-   **Category** : Enhancement

-   **Reproducibility** : Always

-   **Description** : Improved performance of MEMORY table INDEX SCAN and FULL SCAN.

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

Fixed Bugs
----------

### BUG-42525 Fixed an issue where the database is not created when a non-alphabetic value is entered for DB_NAME in the Installer.

-   **module** : installer

-   **Category** : Enhancement

-   **Reproducibility** : Rare

-   **Description** : Fixed an issue where an error occurs when creating a database using the Installer if characters other than alphabets and numbers are included in DB_NAME. The Installer is modified to follow Altibase object naming rules when creating DB_NAME.
    
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

### BUG-48433 Improved the issue where the call stack and OS error messages are mixed in the altibase_error.log during dumptrc execution.

-   **module** : id

-   **Category** : Fatal

-   **Reproducibility** : Unknown

-   **Description** : Improved the issue where the call stack and OS error messages are mixed in the altibase_error.log during dumptrc execution.
    
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

### BUG-48523 Fixed the issue where the server shuts down if the statement object is not cleaned up during session termination.

-   **module** : sm\_transaction

-   **Category** : Fatal

-   **Reproducibility** : Rare

-   **Description** : Fixed the issue where the server shuts down if the statement object is not cleaned up during session termination.
    
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

### BUG-48526 Fixed the issue where a result error occurs when an arbitrary index key is used more than once in the WHERE clause and a host variable is used in the OR condition.

-   **module** : qp-select

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed the issue where a result error occurs when an arbitrary index key is used more than once in the WHERE clause and a host variable is used in the OR condition.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    DROP TABLE  NECDEXTERN_M;
    CREATE TABLE NECDEXTERN_M 
    (
       RECV_NO      NUMERIC(4)  FIXED,
       RECV_NM      CHAR(40)    FIXED,
       COMP_CD      CHAR(3)     FIXED,
       RTIME        CHAR(6)     FIXED,
       ORD_CLS      CHAR(1)     FIXED,
       OK_GB        CHAR(1)     FIXED,
       RJCT_CD      CHAR(5)     FIXED,
       COMP_EMP_NM  CHAR(20)    FIXED,
       FIX_YN       CHAR(1)     FIXED
    );
    ALTER TABLE NECDEXTERN_M ADD CONSTRAINT PK_NECDEXTERN_M PRIMARY KEY ( RECV_NO );
    
    DROP INDEX IDX_NECDEXTERN_M_1;
    CREATE INDEX IDX_NECDEXTERN_M_1 ON NECDEXTERN_M ( OK_GB ASC, RECV_NO ASC );
    
    INSERT INTO NECDEXTERN_M VALUES(1, '', 'ABC', '', '', '1', '', '', '');
    INSERT INTO NECDEXTERN_M VALUES(2, '', 'ABC', '', '', '0', '', '', '');
    INSERT INTO NECDEXTERN_M VALUES(3, '', 'ABC', '', '', '0', '', '', '');
    INSERT INTO NECDEXTERN_M VALUES(4, '', 'ABC', '', '', '0', '', '', '');
    
    VAR s_dno CHAR(1);
    EXEC :s_dno := '0';
    
    ALTER SESSION SET EXPLAIN PLAN = ON;
    ALTER SESSION SET TRCLOG_DETAIL_PREDICATE = 1;
    ALTER SYSTEM SET __OPTIMIZER_OR_VALUE_INDEX = 1;
    
    PREPARE SELECT /*+ CNF */ A.RECV_NO, A.OK_GB
              FROM NECDEXTERN_M A
             WHERE ((:s_dno  = '0' AND A.OK_GB = '0') 
                OR (:s_dno  = '1' AND A.OK_GB IN ('1', '2') ))
             ORDER BY A.RECV_NO;
    ```

  - **Actual Results**

    ```sql
    RECV_NO     OK_GB  
    ----------------------
    1           1  
    2           0  
    3           0  
    4           0  
    4 rows selected.
    ```

  -   **Expected Results**

      ```sql
      RECV_NO     OK_GB
      ----------------------
      2           0
      3           0
      4           0
      3 rows selected.
      ```

- **Workaround**

  ```sql
  ALTER SYSTEM SET __OPTIMIZER_OR_VALUE_INDEX = 0;
  ```

- **Changes**

  -   Performance view

  -   Property

  -   Compile Option

  -   Error Code

Changes
-------

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    7.1.0.5.2     |          6.5.1          |    8.9.1     |        7.1.7        |            7.4.6             |

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
