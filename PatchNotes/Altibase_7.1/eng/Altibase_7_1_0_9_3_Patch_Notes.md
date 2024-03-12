# Altibase 7.1.0.9.3 Patch Notes

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-50713 Improve that the error message includes the header information when the Protocol header error occurs because of an incorrect packet receiving.](#bug-50713)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-48041 Fix an issue where triggers using %ROWTYPE or %TYPE did not automatically recompile when the table definition changed.](#bug-48041)
    - [BUG-50694 Resolve a problem where the server would abnormally terminate when a group by column in a subquery within a disk table was referenced in the main query.](#bug-50694)
    - [BUG-50710 Fix an issue where the server could abnormally terminate when creating a package that calls an external procedure.](#bug-50710)
    - [BUG-50714  Fix a problem that Altibase does not work properly when directly modifying a variable with the constant or nocopy option within a package.](#bug-50714)
    - [BUG-50729 Address an issue where the stack size of terminated threads continued to be output in V$MEMSTAT.](#bug-50729)
    - [BUG-50758 Fix an escape processing omission for double quote characters in APRE.](#bug-50758)
    - [BUG-50778 Add exception handling to the getColumnCount function.](#bug-50778)
    - [BUG-50783 Resolve an issue where an "Invalid use of host variables" error occurred during DDL on a table while executing a procedure.](#bug-50783)
    - [BUG-50789 Fix a problem where media recovery failed when additional checkpoint image files were added during the process.](#bug-50789)
    - [BUG-50792 Fix a logic error in calculating the maximum value of undo tablespace during snapshot specification.](#bug-50792)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [Compatibility](#Compatibility)
    - [Altibase Server Properties](#Altibase-Server-Properties)
    - [Performance Views](#Performance-Views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-50713<a name=bug-50713></a> Improve that the error message includes the header information when the Protocol header error occurs because of an incorrect packet receiving.

-   **module** : cm
-   **Category** : Functionality
-   **Reproducibility** : Rare
-   **Description** : When the Protocol header error occurs due to malformed packets, the error message now displays the header information to assist in problem analysis.
    - Before : ERR-7101d(errno=0) Protocol header error.(TCP 127.0.0.1:41462)
    - After : ERR-710cc(errno=0) Protocol header error.(TCP 127.0.0.1:41462, 0, 3132333435363738393031323334353637383930)
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
        -   Before : ERR-7101d(errno=0) Protocol header error.(TCP 127.0.0.1:41462)
        -   After : ERR-710cc(errno=0) Protocol header error.(TCP 127.0.0.1:41462, 0, 3132333435363738393031323334353637383930)

Fixed Bugs
==========

### BUG-48041<a name=bug-48041></a> Fix an issue where triggers using %ROWTYPE or %TYPE did not automatically recompile when the table definition changed.

-   **module** : qp-ddl-dcl-execute

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Altibase fixed an issue where triggers using %ROWTYPE or %TYPE do not automatically recompile when the table definition was changed.
    
- **How to reproduce this bug**

  -   **Reproduction conditions**

      ```sql
      CREATE TABLE T1(C1 INT, C2 INT);
      CREATE TABLE T2(C1 INT);
      CREATE TABLE T3(C1 INT, C2 INT);
      CREATE OR REPLACE TRIGGER TRIG_ON_T1
           BEFORE INSERT ON T1
           REFERENCING NEW AS NEW_ROW
           FOR EACH ROW
           BEGIN
           DECLARE
           VAR1 T3%ROWTYPE;
           BEGIN
             VAR1.C2 := NEW_ROW.C1;
             INSERT INTO T2 VALUES(VAR1.C2);
           END;
           END;
           /
      
      INSERT INTO T1 VALUES(1,1);
      SELECT * FROM T1;
      SELECT * FROM T2;
      ALTER TABLE T3 DROP C2;
      INSERT INTO T1 VALUES(1,2);
      ```
      
  -   **Actual Results**
  
      ```sql
      iSQL> INSERT INTO T1 VALUES(1,2);
      1 row inserted.
      ```
      
  -   **Expected Results**
  
      ```sql
      iSQL> INSERT INTO T1 VALUES(1,2);
      [ERR-311F9 : The attempt to recompile the trigger SYS.TRIG_ON_T1 was aborted because the creation statement was invalid. :
      
       Column not found
      
      In trigger SYS.TRIG_ON_T1
      0009 :        VAR1.C2 := NEW_ROW.C1;
                        ^ ^
      ]
      ```
  
-   **Workaround**

        Recompile after modifying the trigger

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50694<a name=bug-50694></a> Resolve a problem where the server would abnormally terminate when a group by column in a subquery within a disk table was referenced in the main query.

- **module** : qp

- **Category** : Fatal

- **Reproducibility** : Always

- **Description** : This bug is reproduced in the disk table only. Altibase resolved a problem where the server would abnormally terminate when a group by column in a subquery is referenced in the main query.

- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    CREATE TABLE T1( I1 INTEGER, I2 INTEGER, I3 INTEGER ) TABLESPACE SYS_TBS_DISK_DATA;
    INSERT INTO T1 VALUES (2, NULL, NULL);
    SELECT * FROM T1 WHERE I1 > ALL ( SELECT MIN(I2) FROM DUAL WHERE I1 = '1' GROUP BY I1);
    ```

  - **Actual Results**

    ```sql
    [ERR-91015 : Communication failure.]
    ```

  - **Expected Results**

    ```sql
    iSQL> SELECT * FROM T1 WHERE I1 > ALL ( SELECT MIN(I2) FROM DUAL WHERE I1 = '1' GROUP BY I1);
    I1          I2          I3
    ----------------------------------------
    2
    1 row selected.
    ```

- **Workaround**

- **Changes**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

### BUG-50710<a name=bug-50710></a> Fix an issue where the server could abnormally terminate when creating a package that calls an external procedure.

-   **module** : qp
-   **Category** : Fatal
-   **Reproducibility** : Always
-   **Description** : Altibase fixed an issue where the server could abnormally terminate when creating a package that calls an external procedure.
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

### BUG-50714<a name=bug-50714></a> Fix a problem that Altibase does not work properly when directly modifying a variable with the constant or nocopy option within a package.

-   **module** : qp-psm-trigger-execute

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Altibase fixed a problem when directly modifying a variable with the constant or nocopy option within a package.
    
    1. In the case of directly modifying the value of a variable with the constant option within a package, there should be an error, but there was an issue that the value was changed. Now, when attempting to change the value of a variable with the constant option, an error message will be displayed, preventing the modification of the value.
    2. In the case of directly modifying the value of a variable with the nocopy option, the issue, which "ERR-31439 : An array (element) is not initialized" occurs, has been fixed.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    CREATE OR REPLACE PACKAGE PKG1 AS
    VAR1 CONSTANT INTEGER := 1;
    end;
    /
    EXEC PKG1.VAR1 := 100;
    EXEC PRINTLN(PKG1.VAR1);
    
    CREATE OR REPLACE PACKAGE PKG2 AS
    TYPE ARR_TYPE IS TABLE OF CHAR(32000) INDEX BY INTEGER;
    VAR1 NOCOPY ARR_TYPE;
    VAR2 ARR_TYPE;
    RET INTEGER;
    END;
    /
    BEGIN
      FOR I IN 1 .. 10000 LOOP
        PKG2.VAR2(I) := I;
      END LOOP;
    END;
    /
    EXEC PKG2.VAR1 := PKG2.VAR2;
    ```

  - **Actual Results**

    ```sql
    iSQL> EXEC PKG1.VAR1 := 100;
    Execute success.
    iSQL> EXEC PRINTLN(PKG1.VAR1);
    100
    Execute success.
    iSQL> EXEC PKG2.VAR1 := PKG2.VAR2;
    [ERR-31439 : An array (element) is not initialized.
    at line 1]
    ```

  -   **Expected Results**

      ```sql
      iSQL> EXEC PKG1.VAR1 := 100;
      [ERR-3113F : The L-value of the ASSIGN statement is either a CONSTANT variable or an IN parameter.
      0001 : EXEC PKG1.VAR1 := 100
                 ^        ^
      ]
      iSQL> EXEC PRINTLN(PKG1.VAR1);
      1
      Execute success.
      iSQL> EXEC PKG2.VAR1 := PKG2.VAR2;
      Execute success.
      ```

- **Workaround**

  ```sql
  BEGIN
    PKG1.VAR1 := 100;
  END;
  /
  BEGIN
    PKG2.VAR1 := PKG2.VAR2;
  END;
  /
  ```

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50729<a name=bug-50729></a> Address an issue where the stack size of terminated threads continued to be output in V$MEMSTAT.

-   **module** : id

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Altibase addressed an issue where the stack size of terminated threads continued to be ouptut in V$MEMSTAT. Through this patch, the issue where more memory usage was being reported than the actual memory usage has been resolved.

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

### BUG-50758<a name=bug-50758></a> Fix an escape processing omission for double quote characters in APRE.

-   **module** : mm-apre

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Escape character is automatically added to .c and .cpp files generated after apre precompile when EXEC SQL statements include "(double quote) character.
    
    Example)

    .sc File : EXEC SQL SELECT ' " ' FROM DUAL;

    ==\>

    .c File : ulpSqlstmt.stmt = (char \*)"SELECT ' \\" ' FROM DUAL";

- **How to reproduce this bug**

  - **Reproduction conditions**

    ```c
    int main()
    {
        EXEC SQL SELECT ' " ' FROM DUAL;
    }
    ```

  - **Actual Results**

    It is converted as follows in the .c file.

    ```c
    int main()
    {
        /*  SELECT ' " ' FROM DUAL; */
    {
        struct ulpSqlstmt ulpSqlstmt;
        memset(&ulpSqlstmt, 0, sizeof(ulpSqlstmt));
        ulpSqlstmt.stmttype = 4;
        ulpSqlstmt.stmtname = NULL;
        ulpSqlstmt.ismt = 0;
        ulpSqlstmt.numofhostvar = 0;
        ulpSqlstmt.statusptr = NULL;
        ulpSqlstmt.errcodeptr = NULL;
        ulpSqlstmt.isatomic = 0;
        ulpSqlstmt.stmt = (char *)"SELECT ' " ' FROM DUAL";
     ...
    }
    }
    ```

  -   **Expected Results**

      In the .c file, users can find \ is added before " as follows.
      
      ```c
      int main()
      {
          /*  SELECT ' " ' FROM DUAL; */
      {
          struct ulpSqlstmt ulpSqlstmt;
          memset(&ulpSqlstmt, 0, sizeof(ulpSqlstmt));
          ulpSqlstmt.stmttype = 4;
          ulpSqlstmt.stmtname = NULL;
          ulpSqlstmt.ismt = 0;
          ulpSqlstmt.numofhostvar = 0;
          ulpSqlstmt.statusptr = NULL;
          ulpSqlstmt.errcodeptr = NULL;
          ulpSqlstmt.isatomic = 0;
          ulpSqlstmt.stmt = (char *)"SELECT ' \" ' FROM DUAL";
      ...
      }
      }
      ```

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50778<a name=bug-50778></a> Add exception handling to the getColumnCount function.

-   **module** : qp
-   **Category** : Fatal
-   **Reproducibility** : Rare
-   **Description** : Altibase internally invokes the getColumnCount function to request column information during the Prepare process. There was an issue that the server was abnormally terminated because of incorrect data structure access in an exceptional situation. Altibase added exception handling to this situation.
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

### BUG-50783<a name=bug-50783></a> Resolve an issue where an "Invalid use of host variables" error occurred during DDL on a table while executing a procedure.

-   **module** : qp

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Altibase resolved an issue where an  "ERR-3123B : Invalid use of host variables" error occurred during DDL on a table while executing a procedure.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    -- session 1
    CREATE TABLE T1 (I1 INTEGER);
    INSERT INTO T1 VALUES(1);
    CREATE OR REPLACE PROCEDURE PROC1 AS
    VAR1 INTEGER;
    VAR2 INTEGER;
    BEGIN
      VAR1 := 1;
      FOR I IN 1 .. 10 LOOP
      SELECT VAR1 INTO VAR2 FROM T1;
      PRINTLN(VAR2);
      SLEEP(2);
      VAR1 := VAR1 + 1;
      END LOOP;
    END;
    /
    EXEC PROC1;
    
    -- session 2
    ALTER TABLE T1 ADD (I2 INTEGER);
    ```

  - **Actual Results**

    ```sql
    iSQL> EXEC PROC1;
    1
    2
    3
    4
    [ERR-3123B : Invalid use of host variables
    0001 : select :B0 from T1;
                 ^  ^
    
    at "SYS.PROC1", line 7]
    ```

  -   **Expected Results**

      ```sql
      iSQL> EXEC PROC1;
      1
      2
      3
      4
      5
      6
      7
      8
      9
      10
      Execute success.
      ```

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50789<a name=bug-50789></a> Fix a problem where media recovery failed when additional checkpoint image files were added during the process.

-   **module** : sm
-   **Category** : Fatal
-   **Reproducibility** : Always
-   **Description** : When additional checkpoint image files were added during the MEDIA RECOVERY process, the media recovery failed because it was not able to find LSNs of the added checkpoint image files. To resolve this, now Altibase records CreateLSN of the added file during the MEDIA RECOVERY process on its header.
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

### BUG-50792<a name=bug-50792></a> Fix a logic error in calculating the maximum value of undo tablespace during snapshot specification.

-   **module** : sm

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Altibase fixed a logic error in calculating the maximum value of undo tablespace during snapshot specification.
    
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
| 7.1.0.9.3        | 6.5.1                   | 8.11.1       | 7.1.7               | 7.4.7                        |

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
