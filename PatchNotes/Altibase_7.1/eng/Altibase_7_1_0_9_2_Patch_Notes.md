# Altibase 7.1.0.9.2 Patch Notes





# Table of Contents

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-50703 Improve that the trigger which includes the Row Referencing clause does not copy unused columns internally.](#bug-50703)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-50527 The Altibase server is terminated abnormally when applying operational expression on index columns as parameters of NVL\_EQUAL or NVL\_NOT\_EQUAL function.](#bug-50527) 
    - [BUG-50542 The Altibase server is terminated abnormally when multiple update statement is executed on the table, which is a hybrid partitioned table, contains GEOMETRY or LOB columns, and invokes an update trigger event.](#bug-50542)
    - [BUG-50660 The Altibase server is terminated abnormally when a trigger using the REFERENCING NEW ROW clause is executed after changing the tablespace of the referenced table.](#bug-50660)
    - [BUG-50686 The UTC_OFFSET value for America/Porto_Velho timezone in V\$TIME\_ZONE\_NAMES is incorrect.](#bug-50686)
    - [BUG-50697 A memory leak occurs when using a ping query with PreparedStatement in JDBC.](#bug-50697)
    - [BUG-50700 Invalid memory access error may occur during checking column constraints in a hybrid partitioned table because of incorrect row offset information.](#bug-50700)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [Compatibility](#Compatibility)
    - [Altibase Server Properties](#Altibase-Server-Properties)
    - [Performance Views](#Performance-Views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# New Features

### BUG-50703<a name=bug-50703 ></a> Improve that the trigger which includes the Row Referencing clause does not copy unused columns internally.

- **module** : qp-psm-trigger-execute

- **Category** : Enhancement

- **Reproducibility** : Always

- **Description** : Previously, when a trigger with the Row Referencing clause was executed, it internally copied the referenced records to specific variables. During this process, unnecessary columns were also copied. However, it has been improved to copy only the columns that are actually used.

  With this update, Altibase fixed the issue where a trigger using the Referencing clause would result in an  [ERR-21031: Unable to convert the data type.] error when the trigger does not use the LOB column.

  Additionally, the performance of the DML operation that activates the trigger has been improved.

  > Notice: This patch does not address the following issues.
  >
  > * In triggers using Row Referencing clauses on tables with LOB data exceeding 100MB, an [ERR-21031 : Unable to convert the data type.] error may occur when referencing the LOB columns.

- **How to reproduce this bug**

  -   **Reproduction conditions**
  -   **Actual Results**
  -   **Expected Results**

- **Workaround**

- **Changes**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

Fixed Bugs
==========

### BUG-50527<a name=bug-50527 ></a> The Altibase server is terminated abnormally when applying operational expression on index columns as parameters of NVL\_EQUAL or NVL\_NOT\_EQUAL function.

-   **module** : mt

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : The issue causing abnormal server termination when applying operational expression on index columns as parameters of the NVL_EQUAL() and NVL_NOT_EQUAL() functions has been resolved in this patch.

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

### BUG-50542<a name=bug-50542 ></a> The Altibase server is terminated abnormally when multiple update statement is executed on the table, which is a hybrid partitioned table, contains GEOMETRY or LOB columns and invokes an update trigger event.

-   **module** : sm

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : The issue causing abnormal termination during the execution of multiple update statements under specific conditions has been addressed.
    
    - The table is a hybrid partitioned table and contains a GEOMETRY or LOB column.
    - An update trigger event is configured.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    DROP TABLE T1;
    DROP TABLE T2;
    
    CREATE TABLE T1 ( I1 INTEGER, I2 FLOAT, I3 GEOMETRY  ) 
     PARTITION BY RANGE(I1) 
     ( PARTITION P1 VALUES DEFAULT TABLESPACE SYS_TBS_disk_DATA )
     TABLESPACE SYS_TBS_mem_DATA;
    
    CREATE TABLE T2 (I1 INTEGER, I2 VARCHAR(1000) );
     
    CREATE TRIGGER AFTER_UPDATE AFTER UPDATE ON T1
    REFERENCING 
    OLD AS OLDROW
    NEW AS NEWROW 
    FOR EACH ROW 
    AS 
    BEGIN 
    INSERT INTO T2 VALUES (7777, 'AFTER UPDATE'); 
    END;
    /
     
    INSERT INTO T1(I2) VALUES (178);
    UPDATE T1 LEFT OUTER JOIN T2 ON T1.I1 = T2.I1 SET T1.I1 = T1.I1 + 5, T2.I1 = T2.I1 + 10;
    ```

  - **Actual Results**

    ```sql
    [ERR-91015 : Communication failure.]
    ```

  -   **Expected Results**

      ```sql
      [ERR-1105F : No more than one update cursor can be used on a table.at "SYS.AFTER_UPDATE", line 8]
      ```

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50660<a name=bug-50660 ></a> The Altibase server is terminated abnormally when a trigger using the REFERENCING NEW ROW clause is executed after changing the tablespace of the referenced table.

-   **module** : qp-ddl-dcl-execute

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : The issue causing abnormal termination when a trigger, using the REFERENCING NEW ROW clause, is executed under the following conditions has been resolved:

    1. The trigger with the REFERENCING NEW ROW clause references a table.
    2. The table's tablespace is altered according to the following conditions:

    * If it was a memory tablespace, change it to a disk tablespace.

    * If it was a disk tablespace, change it to a memory tablespace.
    
    3. The trigger executes and DML statements defined in trigger_event are performed.
    
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

### BUG-50686<a name=bug-50686 ></a> The UTC_OFFSET value for America/Porto_Velho timezone in V\$TIME\_ZONE\_NAMES is incorrect.

-   **module** : mt

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : The UTC_OFFSET value for the America/Porto_Velho timezone in V$TIME_ZONE_NAMES is incorrectly displayed. This will be corrected to show the accurate value of "-04:00".
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    select * from v$time_zone_names where name='America/Porto_Velho';
    ```

  - **Actual Results**

    ```sql
    NAME                                      UTC_OFFSET
    ---------------------------------------------------------
    America/Porto_Velho                       04:00
    ```

  -   **Expected Results**

      ```sql
      NAME                                      UTC_OFFSET
      ---------------------------------------------------------
      America/Porto_Velho                       -04:00
      ```

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50697<a name=bug-50697 ></a> A memory leak occurs when using a ping query with PreparedStatement in JDBC.

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Altibase has fixed a memory leak issue when useing a ping query with PreparedStatement in JDBC. Users need to patch JDBC Driver to apply this fix.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```java
    Connection sConn = getConnection("20300");
    PreparedStatement sStmt = sConn.prepareStatement("/* PING */ SELECT 1 ");
    ResultSet sRs = sStmt.executeQuery();
    if (sRs.next())
    {
        sRs.close();
    }
    sStmt.executeQuery();
    sStmt.executeQuery();
    sStmt.executeQuery();
    sStmt.close();
    sConn.close();
    ```

  -   **Actual Results**

          Memory Usage is consistently increasing.

  -   **Expected Results**

          Memory usage is not consistently increasing.

-   **Workaround**

        Using 'select 1 from dual' instead of a ping query

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50700<a name=bug-50700 ></a> Invalid memory access error may occur during checking column constraints in a hybrid partitioned table because of incorrect row offset information.

-   **module** : qp

-   **Category** : Memory Error

-   **Reproducibility** : Always

-   **Description** : Altibase has fixed the issue of invalid memory access due to incorrect row offset information in the logic that checks column constraints in a hybrid partitioned table.
    
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
| 7.1.0.9.2        | 6.5.1                   | 8.11.1       | 7.1.7               | 7.4.7                        |

 > You can check the module version change history in [Version_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.1/Altibase_7_1_Version_Histories.md).

### Compatibility

#### Database binary version

The database binary version has not changed.

> The database binary version indicates the compatibility of database image files and log files. If this version needs to be patched to a different version, the database must be reorganized.

#### Meta Version

The meta version has not changed.

> If you want to roll back the patch after patching to a version with a changed meta version, see [Meta Downgrade](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/eng/Installation_Guide.md#meta-downgrade).

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
