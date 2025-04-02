<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Altibase 7.1.0.5.5 Patch Notes](#altibase-71055-patch-notes)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-48436 Fixed an issue where the Altibase server would shut down abnormally when using an incorrectly written WRAPPED statement.](#bug-48436%C2%A0fixed-an-issue-where-the-altibase-server-would-shut-down-abnormally-when-using-an-incorrectly-written-wrapped-statement)
    - [BUG-48747 An "Invalid argument" error occurs when an unsupported table type is included in the parameters of `AltibaseDatabaseMetaData.getTables()`.](#bug-48747%C2%A0an-invalid-argument-error-occurs-when-an-unsupported-table-type-is-included-in-the-parameters-of-altibasedatabasemetadatagettables)
    - [BUG-48782 When a hash-partitioned table is created using `CREATE AS SELECT`, the data may be inserted into a partition different from the one corresponding to the partition key.](#bug-48782%C2%A0when-a-hash-partitioned-table-is-created-using-create-as-select-the-data-may-be-inserted-into-a-partition-different-from-the-one-corresponding-to-the-partition-key)
    - [BUG-48850 Fixed an issue where the Altibase server abnormally shut down when using the LISTAGG aggregate function on a table with zero records.](#bug-48850%C2%A0fixed-an-issue-where-the-altibase-server-abnormally-shut-down-when-using-the-listagg-aggregate-function-on-a-table-with-zero-records)
    - [BUG-48883 Fixed an issue where the Altibase server could abnormally shut down when the number of columns used in the SELECT clause of an inline view exceeded QUERY_STACK_SIZE.](#bug-48883%C2%A0fixed-an-issue-where-the-altibase-server-could-abnormally-shut-down-when-the-number-of-columns-used-in-the-select-clause-of-an-inline-view-exceeded-query_stack_size)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [Compatibility](#compatibility)
    - [Altibase Server Properties](#altibase-server-properties)
    - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Altibase 7.1.0.5.5 Patch Notes
==============================



Fixed Bugs
----------

### BUG-48436 Fixed an issue where the Altibase server would shut down abnormally when using an incorrectly written WRAPPED statement.

-   **module** : qp-psm-trigger-pvo

-   **Category** : Fatal

-   **Reproducibility** : Frequence

-   **Description** : Fixed an issue where the Altibase server would shut down abnormally when using an incorrectly written WRAPPED statement.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    CREATE OR REPLACE PACKAGE PKG1 WRAPPED 'NTQNJAAZ';
    CREATE OR REPLACE PACKAGE PKG2 WRAPPED 'MTUZMTZ';
    CREATE OR REPLACE PROCEDURE PROC1 WRAPPED 'MJZ ';
    ```

  -   **Actual Results**

          ERR-91015 : Communication failure.

  -   **Expected Results**

      ```sql
      ERR-010D4 : Malformed or corrupted wrapped unit.
      ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48747 An "Invalid argument" error occurs when an unsupported table type is included in the parameters of `AltibaseDatabaseMetaData.getTables()`.

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : An "Invalid argument" error occurs when an unsupported table type is included in the parameters of `AltibaseDatabaseMetaData.getTables()`.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```java
    Connection sConn = getConnection("20300");
    DatabaseMetaData sMeta = sConn.getMetaData();
    ResultSet sRs = sMeta.getTables(null,null,null, new String[] { "TABLE", "ALIAS" });
    int sCnt = 0;
    while (sRs.next())
    {    sCnt++;}
    System.out.println("Count =>" + sCnt);
    ```

  - **Actual Results**

    ```java
    Exception in thread "main" java.sql.SQLException: Invalid argument: Table type: TABLE | SYSTEM TABLE | VIEW | SYSTEM VIEW | MATERIALIZED VIEW | QUEUE | SYNONYM | SEQUENCE expected, but ALIAS   at Altibase.jdbc.driver.ex.Error.throwSQLExceptionInternal(Error.java:189)  at Altibase.jdbc.driver.ex.Error.throwSQLException(Error.java:182)  at Altibase.jdbc.driver.AltibaseDatabaseMetaData.checkTableTypes(AltibaseDatabaseMetaData.java:843) at Altibase.jdbc.driver.AltibaseDatabaseMetaData.getTables(AltibaseDatabaseMetaData.java:872)   at GetTablesTest.doTest(GetTablesTest.java:32)  at GetTablesTest.main(GetTablesTest.java:25)
    ```

  -   **Expected Results**

      ```java
      No Errors.
      ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48782 When a hash-partitioned table is created using `CREATE AS SELECT`, the data may be inserted into a partition different from the one corresponding to the partition key.

-   **module** : qp-select-execute

-   **Category** : Reliability

-   **Reproducibility** : Always

-   **Description** : When a hash-partitioned table is created using `CREATE AS SELECT`, the data may be inserted into a partition different from the one corresponding to the partition key
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    DROP TABLE T2;
    DROP TABLE B;
    
    CREATE TABLE T2 ( I1 INTEGER, I2 INTEGER, I3 INTEGER )
    PARTITION BY HASH(I1)
    ( PARTITION P1,
      PARTITION P2,
      PARTITION PD ) TABLESPACE SYS_TBS_DISK_DATA
    ;
    
    INSERT INTO T2 VALUES( 2, 2, 2 );
    
    CREATE TABLE B
    PARTITION BY HASH(I1) 
    ( PARTITION P1,
      PARTITION P2,
      PARTITION PD ) TABLESPACE SYS_TBS_DISK_DATA
    AS SELECT * FROM T2;
    
    SELECT * FROM B WHERE I1 = 2;
    ```

  - **Actual Results**

    ```sql
    SELECT * FROM B WHERE I1 = 2;
    B.I1        B.I2        B.I3
    ----------------------------------------
    No rows selected.
    ```

  -   **Expected Results**

      ```sql
      SELECT * FROM B WHERE I1 = 2;
      B.I1        B.I2        B.I3
      ----------------------------------------
      2           2           2
      1 row selected.
      ```

-   **Workaround**

        N/A

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48850 Fixed an issue where the Altibase server abnormally shut down when using the LISTAGG aggregate function on a table with zero records.

-   **module** : qp

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where the Altibase server abnormally shut down when using the LISTAGG aggregate function on a table with zero records.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    DROP TABLE BUG_48850;
    
    CREATE TABLE BUG_48850 ( C1 INT PRIMARY KEY, C2 INT, C3 INT ) ;
    INSERT INTO BUG_48850 VALUES(1, 1, 1);
    
    SELECT LISTAGG( C3 ) WITHIN GROUP(ORDER BY C1 ) OVER ( PARTITION BY C2 ORDER BY C1 )
      FROM BUG_48850;
    ```

  - **Actual Results**

    ```sql
    ERR-91015 : Communication failure.
    ```
    
  - **Expected Results**
  
    ```sql
    ISTAGG(C3)WITHINGROUP(ORDERBYC1)OVER(PART  
    ----------------------------------------------
    No rows selected.
    ```
  
-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property

    -   Compile Option

    -   Error Code

### BUG-48883 Fixed an issue where the Altibase server could abnormally shut down when the number of columns used in the SELECT clause of an inline view exceeded QUERY_STACK_SIZE.

-   **module** : qp-dml-execute

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Handled exceptions to prevent the Altibase server from abnormally shutting down under the following conditions. Instead, an ERR-21013: Calculation stack overflow error is now returned.
    
    - The number of columns used in the SELECT clause of an inline view exceeds the stack size.
    - The number of columns used in the SELECT clause of the main query is smaller than the number of columns used in the SELECT clause of the inline view.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    ALTER SESSION SET STACK SIZE = 8;
    SELECT NAME, VALUE1, MIN, MAX FROM V$PROPERTY WHERE NAME = 'QUERY_STACK_SIZE';
    ```

  - **Actual Results**

    ```sql
    ERR-91015 : Communication failure.
    ```

  -   **Expected Results**

      ```sql
      ERR-21013 : Calculation stack overflow
      ```

- **Workaround**

  ```sql
  ALTER SESSION SET STACK SIZE = 128;
  ```
  
-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

Changes
-------

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    7.1.0.5.5     |          6.5.1          |    8.9.1     |        7.1.7        |            7.4.6             |

> You can check the module version change history in [Version_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.1/Altibase_7_1_Version_Histories.md).

### Compatibility

#### Database binary version

The database binary version has not changed.

> The database binary version indicates the compatibility of database image files and log files. If this version needs to be patched to a different version, the database must be reorganized.

#### Meta Version

The meta version has not changed.

> If you want to roll back the patch after patching to a version with a changed meta version, see [Meta Downgrade](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/eng/Installation Guide.md#meta-downgrade).

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
