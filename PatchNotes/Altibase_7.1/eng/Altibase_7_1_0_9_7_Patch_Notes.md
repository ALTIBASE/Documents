Altibase 7.1.0.9.7 Patch Notes
==============================

<br/>

<br/>

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Fixed Bugs](#fixed-bugs)
  - [BUG-50005 Improvement in aku help](#bug-50005)
  - [BUG-50249 When collecting the operating system's resource state from the PICL library, any exceptions should be logged to altimon.log. (AIX, HP-UX)](#bug-50249)
  - [BUG-50849 Using uppercase letters in an ODBC escape sequence results in a parse error.](#bug-50849)
  - [BUG-50875 Fix for abnormal server shutdown when Logical Ager cannot find the index key to delete.](#bug-50875)
  - [BUG-50878 Changes of ILOADER_FIELD_TERM and ILOADER_ROW_TERM properties in aexport.properties file.](#bug-50878)
  - [BUG-50891 The unused INSPECTION_LARGE_HEAP_THRESHOLD property has been removed.](#bug-50891)
  - [BUG-50905 Fixed error when DSN attribute is missing in connection string.](#bug-50905)
  - [BUG-50907 Fixed result error when performing FULL Nested Loop join on hybrid partitioned tables with **SERIAL_EXECUTE_MODE** property set to 1.](#bug-50907)
  - [BUG-50914 Fixed "HY010 Function sequence error" when executing altibase_store_result() and altibase_next_result() sequentially.](#bug-50914)
  - [BUG-50919 Fixed "HY010 Function sequence error" when executing altibase_store_result() and altibase_next_result() sequentially.](#bug-50919)
  - [BUG-50920 Improved error logging for data upload failures](#bug-50920)
  - [BUG-50923 Fixed an issue where the `SQLPrepare` function in CLI did not return an error when executed with an empty SQL string.](#bug-50923)
  - [BUG-50938 Corrected the string length limit used in the aku utility.](#bug-50938)
  - [BUG-50950 Fixed an issue where AKU would not immediately shut down if the creation is failed for the first replication object when running aku -p start.](#bug-50950)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [Compatibility](#compatibility)
  - [Altibase Server Properties](#altibase-server-properties)
  - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Fixed Bugs
----------

### BUG-50005 Improvement in aku help

#### module

aku

#### Category 

Enhancement

#### Reproducibility 

Always


#### Description 

The behavior has been updated so that when no options are provided or incorrect options are entered during the execution of `aku`, an error message will no longer be displayed

#### How to reproduce this bug

-   **Reproduction conditions**

    ```bash
    $ aku
    ```

-   **Actual Results**

    ```bash
    Error while getting option.
    ===============================================================================
                  Altibase Kubernetes Utility Help Screen                          
    ===============================================================================
       Usage   : aku        [-h]                                                   
                            [--help]                                               
                            [-v ]                                                  
                            [--version ]                                           
                            [-i ]                                                  
                            [--info ]                                              
                            [-p pod_action ]                                       
                            [--pod pod_action]                                     
                 -h, --help    : this screen                                       
                 -v, --version : version information                               
                 -i, --info    : option information                                
                 -p, --pod     : [start | stop | clean] specify pod_action         
    ===============================================================================
    ```

-   **Expected Results**

    ```bash
    ===============================================================================
                  Altibase Kubernetes Utility Help Screen                          
    ===============================================================================
       Usage   : aku        [-h]                                                   
                            [--help]                                               
                            [-v ]                                                  
                            [--version ]                                           
                            [-i ]                                                  
                            [--info ]                                              
                            [-p pod_action ]                                       
                            [--pod pod_action]                                     
                 -h, --help    : this screen                                       
                 -v, --version : version information                               
                 -i, --info    : option information                                
                 -p, --pod     : [start | stop | clean] specify pod_action         
    ===============================================================================
    ```

#### Workaround

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50249 When collecting the operating system's resource state from the PICL library, any exceptions should be logged to altimon.log. (AIX, HP-UX)
#### module

ux-altiMon

#### Category

Functionality

#### Reproducibility

Rare

#### Description 

Modified altiMon's monitoring items to log to altimon.log when an exception occurs in the PICL library that collects the operating system's resource status. An exception occurs when a system function call that gets the following information fails.

- Altibase process information

- File system usage

- memory usage

- SWAP memory usage

- system time

This bug targets AIX and HP-UX. Linux is addressed in BUG-50009, which can be found in the [Altibase 7.1.0.8.6 Patch Notes](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.1/eng/Altibase_7_1_0_8_6_Patch_Notes.md).

#### How to reproduce this bug

-   **Reproduction conditions**

-   **Actual Results**

-   **Expected Results**

#### Workaround

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50849 Using uppercase letters in an ODBC escape sequence results in a parse error.
#### module

mm-cli

#### Category

Functional Error

#### Reproducibility

Always

#### Description 

Fixed a “parse error” error when using uppercase letters in an ODBC escape sequence in SQLCLI. ODBC escape sequences are now case insensitive. In previous versions, using uppercase letters would cause a “parse error” error, but with this bug fixed, no error occurs.

See the ODBC escape sequence topic on the [Microsoft ODBC page](https://learn.microsoft.com/ko-kr/sql/odbc/reference/appendixes/odbc-escape-sequences?view=sql-server-ver16).

The Altibase CLI driver (libodbccli.a) needs to be patched to reflect this bug.

#### How to reproduce this bug

-   **Reproduction conditions**

    ```c
    CREATE TABLE T1(i1 int, i2 int);
    CREATE OR REPLACE PROCEDURE proc1
    AS
      v1 constant INTEGER := 1;
      v2 constant t1.i1%TYPE := 1;
    BEGIN
      INSERT INTO t1 VALUES (v1, v2);
    END;
    rc = SQLExecDirect(stmt, (SQLCHAR *)"{ CALL proc1() }", SQL_NTS);
    if (!SQL_SUCCEEDED(rc))
    {
        PRINT_DIAGNOSTIC(SQL_HANDLE_STMT, stmt, "SQLExecDirect");
        goto EXIT_STMT;
    }
    printf("stored procedure call success\n");
    ```

-   **Actual Results**

    ```c
    Error : 158 : SQLExecDirect
      Diagnostic Record 1
        SQLSTATE     : 42000
        Message text : SQL syntax error
    line 1: parse error
    { CALL proc1() }
    ^
    ```

-   **Expected Results**

    Procedure call success

#### Workaround

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50875 Fix for abnormal server shutdown when Logical Ager cannot find the index key to delete.

#### module

sm-mem-index

#### Category

Fatal

#### Reproducibility

Unknown


#### Description

- Fixed an issue where the Altibase server would abnormally shut down when the Logical Ager could not find the index key to delete.


#### How to reproduce this bug

-   **Reproduction conditions**

-   **Actual Results**

-   **Expected Results**

#### Workaround

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50878 Changes of ILOADER_FIELD_TERM and ILOADER_ROW_TERM properties in aexport.properties file.
#### module

ux-aexport

#### Category

Usability

#### Reproducibility

Always

#### Description 

In the aexport.properties and aexport.properties.sample files, the values of the ILOADER_FIELD_TERM and ILOADER_ROW_TERM properties have been updated as follows:

* ILOADER\_FIELD\_TERM :`^`-> `^C_c^`
* ILOADER\_ROW\_TERM : `%n`->`^R_r^%n`

#### How to reproduce this bug

-   **Reproduction conditions**

-   **Actual Results**

-   **Expected Results**

#### Workaround

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50891 The unused INSPECTION_LARGE_HEAP_THRESHOLD property has been removed.
#### module

sm

#### Category

Maintainability

#### Reproducibility

Always

#### Description 


The unused **INSPECTION_LARGE_HEAP_THRESHOLD** property has been removed.

#### How to reproduce this bug

-   **Reproduction conditions**

-   **Actual Results**

-   **Expected Results**

#### Workaround

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50905 Fixed error when DSN attribute is missing in connection string.
#### module

ul-odbc

#### Category

Functional Error

#### Reproducibility

Always

#### Description 


An issue where the error **"Invalid attribute value."** occurred when the **DSN** attribute was not provided in the connection string has been fixed. Now, it is possible to connect using only Driver, Server, User, Password, and Port without specifying **DSN**.

To apply this fix, the Altibase ODBC driver must be patched:

- **32-bit ODBC driver**: `libaltibase_odbc-64bit-ul32.so`
- **64-bit ODBC driver**: `libaltibase_odbc-64bit-ul64.so`

#### How to reproduce this bug

-   **Reproduction conditions**

-   **Actual Results**

-   **Expected Results**

    연결 성공

#### Workaround

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50907 Fixed result error when performing FULL Nested Loop join on hybrid partitioned tables with **SERIAL_EXECUTE_MODE** property set to 1.
#### module

qp

#### Category

Reliability

#### Reproducibility

Always

#### Description 


An issue has been resolved where incorrect results could occur when performing Full Nested Loop join on hybrid partitioned tables with the **SERIAL_EXECUTE_MODE** property set to 1. This issue can be avoided by using the `USE_HASH` hint.

#### How to reproduce this bug

-   **Reproduction conditions**

    ```sql
    CREATE VOLATILE DATA TABLESPACE VOL_TBS SIZE 32M AUTOEXTEND ON;
    
    CREATE TABLE t1( i1 int, c1 clob )
    PARTITION BY RANGE(i1)
    (
        PARTITION p1 VALUES LESS THAN (1) TABLESPACE SYS_TBS_MEM_DATA,
        PARTITION p2 VALUES LESS THAN (2) TABLESPACE SYS_TBS_DISK_DATA,
        PARTITION p3 VALUES LESS THAN (3) TABLESPACE VOL_TBS,
        PARTITION pd VALUES DEFAULT TABLESPACE SYS_TBS_DISK_DATA
    ) TABLESPACE SYS_TBS_DISK_DATA UNCOMPRESSED LOGGING;
    
    CREATE TABLE t2( i1 int, c1 clob )
    PARTITION BY RANGE(i1)
    (
        PARTITION p1 VALUES LESS THAN (2) TABLESPACE SYS_TBS_DISK_DATA,
        PARTITION p2 VALUES LESS THAN (4) TABLESPACE SYS_TBS_MEM_DATA,
        PARTITION p3 VALUES LESS THAN (6) TABLESPACE SYS_TBS_DISK_DATA,
        PARTITION pd VALUES DEFAULT TABLESPACE VOL_TBS
    ) TABLESPACE SYS_TBS_DISK_DATA UNCOMPRESSED LOGGING;
    
    INSERT INTO t1 VALUES( 0, '0' );
    INSERT INTO t1 VALUES( 1, '1' );
    INSERT INTO t1 VALUES( 2, '2' );
    INSERT INTO t1 VALUES( 3, '3' );
    INSERT INTO t1 VALUES( 4, '4' );
    INSERT INTO t2 SELECT * FROM t1;
    
    CREATE VIEW v1 AS SELECT t1.i1 i1 FROM t1, t2 WHERE t1.i1 = t2.i1;
    
    SELECT i1 FROM v1;
    ```

-   **Actual Results**

    ```sql
    SELECT i1 FROM v1;
    I1
    --------------
    0
    1
    2
    4
    4 rows selected.
    ```

-   **Expected Results**

    ```sql
    I1
    --------------
    0
    1
    2
    3
    4
    5 rows selected.
    ```

#### Workaround

`USE_HASH` 힌트를 사용하여 문제 현상을 회피할 수 있습니다.

```sql
SELECT /*+ USE_HASH( t1, t2 ) */ i1 FROM v1;
```

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50914 Fixed "HY010 Function sequence error" when executing altibase_store_result() and altibase_next_result() sequentially.

#### module

ux-cdbc

#### Category

Functional Error

#### Reproducibility

Always

#### Description 

An issue where the "HY010 Function sequence error" occurred when retrieving the second result set by executing altibase_store_result() and altibase_next_result() sequentially has been fixed. 

To apply this fix, the ACI library (**libalticapi.a**) must be patched.

**How to reproduce this bug**

-   **Reproduction conditions**

        -- Schema
        CREATE TABLE RESULT1 (I1 INTEGER, I2 VARCHAR(10));
        INSERT INTO RESULT1 VALUES (11, '11_AAA');
        INSERT INTO RESULT1 VALUES (12, '12_BBB');
        INSERT INTO RESULT1 VALUES (13, '13_CCC');
        CREATE TABLE RESULT2 (I1 INTEGER, I2 VARCHAR(10), I3 VARCHAR(10));
        INSERT INTO RESULT2 VALUES (21, '21_AAA', '221_AAA');
        INSERT INTO RESULT2 VALUES (22, '22_BBB', '222_BBB');
        INSERT INTO RESULT2 VALUES (23, '23_CCC', '223_CCC');
        CREATE TABLE RESULT3 (I1 INTEGER, I2 VARCHAR(10));
        INSERT INTO RESULT3 VALUES (31, '31_AAA');
        INSERT INTO RESULT3 VALUES (32, '32_BBB');
        INSERT INTO RESULT3 VALUES (33, '33_CCC');
        CREATE TABLE RESULT4 (I1 INTEGER, I2 VARCHAR(10));
        INSERT INTO RESULT4 VALUES (41, NULL);
        INSERT INTO RESULT4 VALUES (NULL, '42_BBB');
        INSERT INTO RESULT4 VALUES (NULL, NULL);
        CREATE TYPESET MY_TYPE
        AS
           TYPE MY_CUR IS REF CURSOR;
        END;
        /
        CREATE OR REPLACE PROCEDURE PROC_RESULTSET
        (
           P1 OUT MY_TYPE.MY_CUR,
           P2 OUT MY_TYPE.MY_CUR,
           P3 OUT MY_TYPE.MY_CUR,
           P4 OUT MY_TYPE.MY_CUR
        )
        AS
            sSQL_STMT VARCHAR(200);
        BEGIN
            sSQL_STMT := 'SELECT * FROM RESULT1';
            OPEN P1 FOR sSQL_STMT;
            sSQL_STMT := 'SELECT * FROM RESULT2';
            OPEN P2 FOR sSQL_STMT;
            sSQL_STMT := 'SELECT * FROM RESULT3';
            OPEN P3 FOR sSQL_STMT;
            sSQL_STMT := 'SELECT * FROM RESULT4';
            OPEN P4 FOR sSQL_STMT;
        END;
        /
        --  ACI code example   
        sRC = altibase_query(sAB, "EXEC PROC_RESULTSET");
        while (1)
        {
            sRes = altibase_store_result(sAB);
            ...details omitted...
            while ((sRow = altibase_fetch_row(sRes)) != NULL)
            {
            ...details omitted...
            }
            ...details omitted...
            sRC = altibase_next_result(sAB);
            ...details omitted...
        }

-   **Actual Results**

        HY010 Function sequence error.

-   **Expected Results**

    ```
    no error
    ```

#### Workaround

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50919 Fixed "HY010 Function sequence error" when executing altibase_store_result() and altibase_next_result() sequentially.

#### module

ux-cdbc

#### Category

Functional Error

#### Reproducibility

Always

#### Description 

An issue where the "HY010 Function sequence error" occurred when retrieving the second result set by executing altibase_store_result() and altibase_next_result() sequentially has been fixed. 

To apply this fix, the ACI library (**libalticapi.a**) must be patched.

#### How to reproduce this bug

-   **Reproduction conditions**

        -- Schema
        CREATE TABLE fetch1 (id INTEGER, val VARCHAR(10));
        INSERT INTO fetch1 VALUES (1, 'a1');
        INSERT INTO fetch1 VALUES (2, 'b2');
        CREATE TABLE fetch2 (id INTEGER, val VARCHAR(10), etc VARCHAR(10));
        INSERT INTO fetch2 VALUES (4, 'd4', 'asd');
        INSERT INTO fetch2 VALUES (5, 'e5', 'qwe');
        INSERT INTO fetch2 VALUES (6, 'f6', 'zxc');
        CREATE TYPESET fetch_type
        AS
                TYPE fetch_cur IS REF CURSOR;
        END;
        /
        CREATE OR REPLACE PROCEDURE fetch_proc
        (
                p1 OUT fetch_type.fetch_cur,
                p2 OUT fetch_type.fetch_cur
        )
        AS
        BEGIN
                OPEN p1 FOR 'SELECT * FROM fetch1';
                OPEN p2 FOR 'SELECT * FROM fetch2';
        END;
        /
        -- ACI code example
        sRC = altibase_stmt_prepare(sStmt, "EXEC fetch_proc");
        ...details omitted...
        sRC = altibase_stmt_execute(sStmt);
        ...details omitted...  
        while (1)
        {
            ...details omitted...
            while ((sRC = altibase_stmt_fetch(sStmt)) != ALTIBASE_NO_DATA)
            {
            ...details omitted...
            }
            ...details omitted...
            sRC = altibase_stmt_next_result(sStmt);
            ...details omitted...
        }

-   **Actual Results**

        HY010 Function sequence error.

-   **Expected Results**

    ```
    no error
    ```


#### Workaround

#### Changes

-   Performance view
    
-   Property
-   Compile Option
-   Error Code

### BUG-50920 Improved error logging for data upload failures

#### module

ux-iloader

#### Category

Usability

#### Reproducibility

Always

#### Description 

A feature has been added to log column information in the logfile when an error occurs during data upload with iLoader. By using the `-verbose` option in iLoader, if an error occurs during data upload, the column's location in the affected table will be logged along with the error message in the `-log logfile` file.

**How to reproduce this bug**

-   **Reproduction conditions**

    ```
    -- 테이블 스키마
    CREATE TABLE BUG_50920 (c1 INT, c2 int);
    
    -- 테이블에 업로드 할 파일 내용
    cat BUG_50920.dat
    1,1
    2,2147483648
    2147483648, 3
    2147483648, 2147483648
    
    -- 데이터 업로드 수행
    iloader -s localhost -u SYS -p manager formout -f BUG_50920.fmt -T BUG_50920
    iloader -s localhost -u SYS -p manager in -f BUG_50920.fmt -d BUG_50920.dat -log BUG_50920.log -silent
    cat BUG_50920.log
    iloader -s localhost -u SYS -p manager in -f BUG_50920.fmt -d BUG_50920.dat -log BUG_50920.log -silent -verbose
    cat BUG_50920.log
    ```

-   **Actual Results**

    ```bash
    $ iloader -s localhost -u SYS -p manager in -f BUG_50920.fmt -d BUG_50920.dat -log BUG_50920.log -silent
    UPLOAD : 14.3730 msec
         Load Count  : 1(BUG_50920)
         Error Count : 3
         
    $ cat BUG_50920.log
    TableName : BUG_50920
    Start Time : Wed Jun 19 19:19:33 2024
    Record 2 : 2,2147483648
    [ERR-51072 : Numeric value out of range.]
    Record 3 : 2147483648,3
    [ERR-51072 : Numeric value out of range.]
    Record 4 : 2147483648,2147483648
    [ERR-51072 : Numeric value out of range.]
    End Time : Wed Jun 19 19:19:33 2024
    Total Row Count : 4
    Load Row Count  : 1
    Error Row Count : 3
    
    $ iloader -s localhost -u SYS -p manager in -f BUG_50920.fmt -d BUG_50920.dat -log BUG_50920.log -silent -verbose
    [ERR-9103B : Invalid option (-verbose)]
    ```

-   **Expected Results**

    ```bash
    $ iloader -s localhost -u SYS -p manager in -f BUG_50920.fmt -d BUG_50920.dat -log BUG_50920.log -silent
    UPLOAD : 15.8760 msec
         Load Count  : 1(BUG_50920)
         Error Count : 3
         
    $ cat BUG_50920.log
    TableName : BUG_50920
    Start Time : Wed Jun 19 19:20:50 2024
    Record 2 : 2,2147483648
    [ERR-51072 : Numeric value out of range.]
    Record 3 : 2147483648,3
    [ERR-51072 : Numeric value out of range.]
    Record 4 : 2147483648,2147483648
    [ERR-51072 : Numeric value out of range.]
    End Time : Wed Jun 19 19:20:50 2024
    Total Row Count : 4
    Load Row Count  : 1
    Error Row Count : 3
    
    $ iloader -s localhost -u SYS -p manager in -f BUG_50920.fmt -d BUG_50920.dat -log BUG_50920.log -silent -verbose
    UPLOAD : 15.4300 msec
         Load Count  : 1(BUG_50920)
         Error Count : 3
         
    $ cat BUG_50920.log
    TableName : BUG_50920
    Start Time : Wed Jun 19 19:21:20 2024
    Record 2 : 2,2147483648
    [ERR-51072 : Numeric value out of range. at Column [2]]
    Record 3 : 2147483648,3
    [ERR-51072 : Numeric value out of range. at Column [1]]
    Record 4 : 2147483648,2147483648
    [ERR-51072 : Numeric value out of range. at Column [1]]
    End Time : Wed Jun 19 19:21:20 2024
    Total Row Count : 4
    Load Row Count  : 1
    Error Row Count : 3
    ```

#### Workaround

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50923 Fixed an issue where the `SQLPrepare` function in CLI did not return an error when executed with an empty SQL string.

#### module

mm-cli

#### Category

Functional Error

#### Reproducibility

Always

#### Description 

Fixed an issue where the `SQLPrepare` function in CLI did not return an error when executed with an empty SQL string.

To apply this bug fix, the Altibase CLI driver (`libodbccli.a`) must be patched.

**How to reproduce this bug**

-   **Reproduction conditions**

    ```c
    rc = SQLPrepare(stmt, (SQLCHAR *)"", SQL_NTS);
    if (!SQL_SUCCEEDED(rc))
    {
        PRINT_DIAGNOSTIC(SQL_HANDLE_STMT, stmt, "SQLPrepare");
        goto EXIT_STMT;
    }
    rc = SQLExecute(stmt);
    if (!SQL_SUCCEEDED(rc))
    {
        PRINT_DIAGNOSTIC(SQL_HANDLE_STMT, stmt, "SQLExecute");
        goto EXIT_STMT;
    }
    ```

-   **Actual Results**

    An error does not occur in SQLPrepare but occurs in SQLExecute.

    ```bash
    Error : 236 : SQLExecute
      Diagnostic Record 1
        SQLSTATE     : HY000
        Message text : Failure to find statement
        Message len  : 25
        Native error : 0x41098
    ```

-   **Expected Results**

    An error occurs in SQLPrepare. 
    
    ```bash
    Error : 160 : SQLPrepare                                           
      Diagnostic Record 1                                              
        SQLSTATE     : HY000                                           
        Message text : SQL statement too short                         
        Message len  : 23                                              
        Native error : 0x41039
    ```

#### Workaround

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50938 Corrected the string length limit used in the aku utility.

#### module

aku

#### Category

Functional Error

#### Reproducibility

Always

#### Description

The length limits of the `AKU_STS_NAME` and `AKU_SVC_NAME` properties have been changed from 40 to 63 to comply with Kubernetes restrictions. Additionally, the maximum length for the replication target table’s user name and table name has been increased from 40 to 128.

#### How to reproduce this bug

-   **Reproduction conditions**

-   **Actual Results**

-   **Expected Results**

#### Workaround

#### Changes

-   Performance view
-   Property
    
-   Compile Option
-   Error Code

### BUG-50950 Fixed an issue where AKU would not immediately shut down if the creation is failed for the first replication object when running aku -p start.

#### module

aku

#### Category

Functional Error

#### Reproducibility

Always

#### Description 

Fixed a bug in `aku -p start` where if the creation of the first replication object failed, it would try to create a second replication object and then exit instead of exiting immediately. Changed it so that if the creation of a replication object failed, it would exit immediately without performing any other actions.

#### How to reproduce this bug

-   **Reproduction conditions**

-   **Actual Results**

-   **Expected Results**

#### Workaround

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code

Changes
-------

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    7.1.0.9.7     |          6.5.1          |    8.11.1    |        7.1.7        |            7.4.7             |

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
