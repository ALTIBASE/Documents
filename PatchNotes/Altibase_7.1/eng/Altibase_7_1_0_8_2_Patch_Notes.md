# Altibase 7.1.0.8.2 Patch Notes

<br/>

<br>

# Table of Contents

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Fixed Bugs](#fixed-bugs)
    - [BUG-49607 Improves the stability issue that occurs when performing operations on objects that reference a PACKAGE SPEC or TYPESET in an INVALID state due to changes in the object.](#bug-49607%C2%A0improves-the-stability-issue-that-occurs-when-performing-operations-on-objects-that-reference-a-package-spec-or-typeset-in-an-invalid-state-due-to-changes-in-the-object)
    - [BUG-49851 Setting the connection property TIMEOUT to 0 in the SQLDriverConnect function may result in a Connection Timeout Error.](#bug-49851%C2%A0setting-the-connection-property-timeout-to-0-in-the-sqldriverconnect-function-may-result-in-a-connection-timeout-error)
    - [BUG-49913 Improved the stability issue caused when a partitioned table used with a LATERAL VIEW is processed by a parallel query.](#bug-49913%C2%A0improved-the-stability-issue-caused-when-a-partitioned-table-used-with-a-lateral-view-is-processed-by-a-parallel-query)
    - [BUG-49923 Improved exception handling when compiling PSM with deep recursion or a large number of references.](#bug-49923%C2%A0improved-exception-handling-when-compiling-psm-with-deep-recursion-or-a-large-number-of-references)
    - [BUG-49925 Improved the stability issue found when using a view based on a partitioned table in multiple update (or delete) operations, with triggers on the referenced table.](#bug-49925%C2%A0improved-the-stability-issue-found-when-using-a-view-based-on-a-partitioned-table-in-multiple-update-or-delete-operations-with-triggers-on-the-referenced-table)
    - [BUG-49930 In a multiple update statement that updates a view, the error [ERR-31058: Column not found] occurs because the trigger cannot find the modified columns added by the trigger.](#bug-49930%C2%A0in-a-multiple-update-statement-that-updates-a-view-the-error-err-31058-column-not-found-occurs-because-the-trigger-cannot-find-the-modified-columns-added-by-the-trigger)
    - [BUG-49931 Improved the consistency error found when updating a view based on a reference table of a **BEFORE UPDATE** trigger that changes values using **NEW ROW**.](#bug-49931%C2%A0improved-the-consistency-error-found-when-updating-a-view-based-on-a-reference-table-of-a-before-update-trigger-that-changes-values-using-new-row)
    - [BUG-49942 The Altibase server may fail to start due to a concurrency issue between disk transaction rollback and ping-pong checkpoint.](#bug-49942%C2%A0the-altibase-server-may-fail-to-start-due-to-a-concurrency-issue-between-disk-transaction-rollback-and-ping-pong-checkpoint)
    - [BUG-49987 Fixed stability issues that occur when using inline views in the FROM clause, string functions in the GROUP BY clause, and using keys from the GROUP BY clause in the SELECT and ORDER BY clauses with analytical functions.](#bug-49987%C2%A0fixed-stability-issues-that-occur-when-using-inline-views-in-the-from-clause-string-functions-in-the-group-by-clause-and-using-keys-from-the-group-by-clause-in-the-select-and-order-by-clauses-with-analytical-functions)
    - [BUG-49994 Fixed the result error issue that occurs when a window function is used and `NULLS LAST` is applied in the ORDER BY clause.](#bug-49994%C2%A0fixed-the-result-error-issue-that-occurs-when-a-window-function-is-used-and-nulls-last-is-applied-in-the-order-by-clause)
    - [BUG-49998 Fixed an issue where an error occurred when using the same column more than once in the SET clause of a MULTIPLE UPDATE statement.](#bug-49998%C2%A0fixed-an-issue-where-an-error-occurred-when-using-the-same-column-more-than-once-in-the-set-clause-of-a-multiple-update-statement)
    - [BUG-50002 Fixed a stability issue that occurs when a hash-partitioned table is processed using the USE_FULL_NL join method.](#bug-50002%C2%A0fixed-a-stability-issue-that-occurs-when-a-hash-partitioned-table-is-processed-using-the-use_full_nl-join-method)
    - [BUG-50004 Changes the default values of the AKU_QUERY_TIMEOUT and SYNC_PARALLEL_COUNT properties in the aku.conf.sample file.](#bug-50004%C2%A0changes-the-default-values-of-the-aku_query_timeout-and-sync_parallel_count-properties-in-the-akuconfsample-file)
    - [BUG-50017 Using the DELETE clause in the CREATE QUEUE statement in APRE results in a syntax error during compilation.](#bug-50017%C2%A0using-the-delete-clause-in-the-create-queue-statement-in-apre-results-in-a-syntax-error-during-compilation)
    - [BUG-50022 Improved stability when performing a multiple update on a target table with a TIMESTAMP column.](#bug-50022%C2%A0improved-stability-when-performing-a-multiple-update-on-a-target-table-with-a-timestamp-column)
    - [BUG-50032 Added the `force` option to the `oaUtility` utility.](#bug-50032%C2%A0added-the-force-option-to-the-oautility-utility)
    - [BUG-50038 Enhanced error messages for exception handling during the startup of `jdbcAdapter` and `oraAdapter`.](#bug-50038%C2%A0enhanced-error-messages-for-exception-handling-during-the-startup-of-jdbcadapter-and-oraadapter)
    - [BUG-50048 Added session access control functionality to aku.](#bug-50048%C2%A0added-session-access-control-functionality-to-aku)
    - [BUG-50050 Added functionality to remove conditions in views or inline views that do not affect the logical result of the query.](#bug-50050%C2%A0added-functionality-to-remove-conditions-in-views-or-inline-views-that-do-not-affect-the-logical-result-of-the-query)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [Compatibility](#compatibility)
    - [Altibase Server Properties](#altibase-server-properties)
    - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->



Fixed Bugs
==========

### BUG-49607 Improves the stability issue that occurs when performing operations on objects that reference a PACKAGE SPEC or TYPESET in an INVALID state due to changes in the object.

#### module

`qp-psm-trigger-pvo`

#### Category

`Fatal`

#### Reproducibility

`Always`

#### Description

Fixed the bug where the Altibase server shut down abnormally when executing objects that reference a PACKAGE SPEC or TYPESET that has been changed to an INVALID state.


#### How to reproduce this bug

-   **Reproduction conditions**

    ```sql
    CREATE TABLE T1 ( I1 INTEGER, I2 INTEGER ) ;
    
    CREATE OR REPLACE TYPESET TYPE1 
    AS 
    TYPE ARRI IS TABLE OF INTEGER INDEX BY INTEGER; 
    TYPE REC IS RECORD ( I1 T1.I1%TYPE); 
    END;
    /
    
    CREATE OR REPLACE PROCEDURE PROC1 
    AS VARRI TYPE1.ARRI; 
    R1 INTEGER; BEGIN VARRI(1) := 1; 
    SELECT VARRI(1) INTO R1 FROM DUAL ; 
    PRINTLN( R1 ); 
    END;
    /
    
    ALTER TABLE T1 RENAME COLUMN I2 TO TYPE;
    
    EXEC PROC1;
    ```

-   **Actual Results**

    ~~~sql
    [ERR-91015 : Communication failure.]
    ~~~

-   **Expected Results**

    ```sql
    1
    Execute success.
    ```

#### Workaround

```sql
CREATE TABLE T1 ( I1 INTEGER, I2 INTEGER, I3 INTEGER, I4 INTEGER, I5 INTEGER, CONSTRAINT T1_PK PRIMARY KEY (I2 DESC, I3 DESC), CONSTRAINT T1_UK UNIQUE (I4 DESC, I5 DESC) ) PARTITION BY HASH(I1) ( PARTITION P1, PARTITION P2, PARTITION P3 ) TABLESPACE SYS_TBS_DISK_DATA;
CREATE OR REPLACE TYPESET TYPE1 AS TYPE ARRI IS TABLE OF INTEGER INDEX BY INTEGER; TYPE ARRC IS TABLE OF INTEGER INDEX BY VARCHAR(10); TYPE REC IS RECORD ( I1 T1.I1%TYPE, I2 T1.I2%TYPE ); TYPE ARRI_REC IS TABLE OF REC INDEX BY INTEGER; TYPE ARRC_REC IS TABLE OF REC INDEX BY VARCHAR(10); END;
/
CREATE OR REPLACE PROCEDURE PROC1 AS VARRI TYPE1.ARRI; R1 INTEGER; BEGIN VARRI(1) := 1; SELECT VARRI(1) INTO R1 FROM DUAL ; PRINTLN( R1 ); END;
/
ALTER TABLE T1 RENAME COLUMN I4 TO TYPE;

ALTER TYPESET TYPE1 COMPILE;

EXEC PROC1;
```

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code



### BUG-49851 Setting the connection property TIMEOUT to 0 in the SQLDriverConnect function may result in a Connection Timeout Error.

#### module 

`mm-cli`

#### Category 

`Functional Error`

#### Reproducibility 

`Always`

#### Description

Fixed an issue where setting the connection property TIMEOUT to 0 in the SQLDriverConnect function of the Altibase CLI causes a Connection Timeout Error. This bug is exposed regardless of the operating system, but the issue consistently occurs when remotely connecting to the Altibase server from a Windows environment.

To apply this fix, the Altibase CLI library needs to be patched.

- for Linux/Unix : libodbccli.a, libodbccli\_sl.so

- for Windows : altiodbc.dll


#### How to reproduce this bug

-   **Reproduction conditions**

    ```c
    rc = SQLDriverConnect(dbc, NULL, (SQLCHAR *)"Server=127.0.0.1;User=SYS;Password=MANAGER;TIMEOUT=0", SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);
    ```
    
-   **Actual Results**

        Connection Timeout Error

-   **Expected Results**

        Connection success

#### Workaround

`없음`

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code



### BUG-49913 Improved the stability issue caused when a partitioned table used with a LATERAL VIEW is processed by a parallel query.

#### module 

`qp`

#### Category 

`Fatal`

#### Reproducibility 

`Always`

#### Description

Fixed an issue where the Altibase server shut down abnormally when a partitioned table used with a LATERAL VIEW is processed by a parallel query. Since LATERAL VIEW is not supported for parallel queries, this issue is addressed by ensuring that LATERAL VIEW is not processed in parallel.

This bug occurs under the following conditions:

- The PARALLEL clause is specified for a partitioned table or a PARALLEL hint is used.
- An inline view that uses the partitioned table is defined as a LATERAL VIEW (using the LATERAL or APPLY keyword).


#### How to reproduce this bug

-   **Reproduction conditions**

    ```sql
    CREATE TABLE T2( I1 INTEGER, I2 INTEGER ) 
    PARTITION BY HASH(I1) 
    ( PARTITION P1, 
      PARTITION P2 
    ) TABLESPACE SYS_TBS_MEM_DATA;
    
    ALTER TABLE T2 PARALLEL 4;
    
    CREATE TABLE T1 (I1 INTEGER, I2 INTEGER);
    INSERT INTO T2 VALUES( 4, 4 );
    
    SELECT * FROM T1 OUTER APPLY ( SELECT SUM(T1.I1) AS I1 FROM T2 INTERSECT SELECT COUNT(T1.I2) AS I1 FROM T2 );
    ```

-   **Actual Results**

    ```sql
    [ERR-91015 : Communication failure.]
    ```

-   **Expected Results**

    ```sql
    I1          I2          I1                   
    -------------------------------------------------
    No rows selected.
    ```

#### Workaround

You can work around this bug by using the /*+ NOPARALLEL */ hint.

```sql
SELECT * FROM T1 OUTER APPLY ( SELECT /*+ NOPARALLEL */ SUM(T1.I1) AS I1 FROM T2 INTERSECT SELECT /*+ NOPARALLEL */ COUNT(T1.I2) AS I1 FROM T2 );
```

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code



### BUG-49923 Improved exception handling when compiling PSM with deep recursion or a large number of references.

#### module 

`qp-psm-trigger-execute`

#### Category 

`Fatal`

#### Reproducibility 

`Always`

#### Description

Improved the bug where the Altibase server may shut down abnormally when compiling PSM with deep recursion or a large number of references. To prevent deep recursion or a large reference depth, a new Altibase server property is added.

In Altibase 7.1, the change for this bug is disabled. To apply this fix in Altibase 7.1.0.8.2 or later, you need to modify the value of the PSM_MAX_DDL_REFERENCE_DEPTH property. This property can be changed using the ALTER SYSTEM command. To permanently apply the change to the Altibase server, you must add the PSM_MAX_DDL_REFERENCE_DEPTH property to the altibase.properties file.

If the recursion or reference depth exceeds the PSM_MAX_DDL_REFERENCE_DEPTH value when compiling PSM, the following error message will be returned.

~~~sql
[ERR-31459 : The attempt to recompile the object was aborted. 

 The number of recursive calls or references depth exceeded 128 in the PSM. 
0003 : VAR1 PKG2_SYM.T1_REC;
      ^   ^
 
~~~


#### How to reproduce this bug

-   **Reproduction conditions**

    ```sql
    CREATE TABLE T1 (C1 INTEGER);
    CREATE TABLE T2 (C1 INTEGER);
    CREATE OR REPLACE PACKAGE PKG1 AS
    TYPE T1_REC IS RECORD(C1 T1.C1%TYPE);
    VAR1 NUMBER;
    PROCEDURE PROC1;
    END;
    /
    CREATE OR REPLACE PACKAGE BODY PKG1 AS
    PROCEDURE PROC1 AS
    BEGIN
      PRINTLN('PKG1');
    END;
    BEGIN
      VAR1 := 1;
    END;
    /
    CREATE SYNONYM PKG1_SYM FOR SYS.PKG1;
    CREATE OR REPLACE PACKAGE PKG2 AS
    TYPE T1_REC IS RECORD(C1 T2.C1%TYPE);
    VAR1 PKG1_SYM.T1_REC;
    PROCEDURE PROC1;
    END;
    /
    CREATE OR REPLACE PACKAGE BODY PKG2 AS
    PROCEDURE PROC1 AS
    BEGIN
      PRINTLN('PKG2');
      PKG1_SYM.PROC1;
    END;
    BEGIN
      VAR1.C1 := 1;
    END;
    /
    CREATE SYNONYM PKG2_SYM FOR SYS.PKG2;
    CREATE OR REPLACE PACKAGE PKG3 AS
    TYPE T1_REC IS RECORD(C1 T2.C1%TYPE);
    VAR1 PKG2_SYM.T1_REC;
    PROCEDURE PROC1;
    END;
    /
    CREATE OR REPLACE PACKAGE BODY PKG3 AS
    PROCEDURE PROC1 AS
    BEGIN
      PRINTLN('PKG3');
      PKG2_SYM.PROC1;
    END;
    BEGIN
      VAR1.C1 := 1;
    END;
    /
     
     
    DROP SYNONYM PKG1_SYM;
    CREATE SYNONYM PKG1_SYM FOR SYS.PKG3;
     
    EXEC PKG2.PROC1;
    ```

-   **Actual Results**

    ```sql
    [ERR-31455 : Failed to work because an internal exception occurred from an OS.[Contact Altibase's Support Center]]
    ```

-   **Expected Results**

    ```sql
    [ERR-31459 : The attempt to recompile the object was aborted. 
     The number of recursive calls or references depth exceeded 128 in the PSM. 
    0003 : VAR1 PKG2_SYM.T1_REC;
          ^   ^
    ]
    ```

#### Workaround

`없음`

#### Changes

-   Performance view

-   Property
    
    - PSM_MAX_DDL_REFERENCE_DEPTH
    
      - Data Type : Unsinged Integer
    
      - Default value : 4294967295 (기능 비활성화)
    
      - Attribute : Read-Write, Single Value
    
      - Range : [64, 232-1]
    
      - Description : Limits the recursion or reference depth when compiling PSM. If the recursion or reference depth exceeds the configured value, an error will occur.
    
-   Compile Option

-   Error Code



### BUG-49925 Improved the stability issue found when using a view based on a partitioned table in multiple update (or delete) operations, with triggers on the referenced table.

#### module 

`qp-dml-pvo`

#### Category 

`Fatal`

#### Reproducibility 

`Always`

#### Description
Improved the issue where the Altibase server shut down abnormally when using a view based on a partitioned table in multiple update (or delete) operations, and there are triggers on the referenced table.


#### How to reproduce this bug

-   **Reproduction conditions**

    ```sql
    CREATE TABLE T1( I1 INTEGER, I2 INTEGER, I3 INTEGER, I4 INTEGER ) PARTITION BY HASH(I4) ( PARTITION P1, PARTITION P2 ) ;
    
    CREATE VIEW V1 AS SELECT I1, I2 FROM T1 WHERE I1 < 5;
    CREATE SYNONYM V2 FOR V1;
    
    CREATE OR REPLACE TRIGGER TRIG1
    BEFORE UPDATE OF I1 ON T1
    REFERENCING NEW AS NEW_ROW
    FOR EACH ROW
    BEGIN
      NEW_ROW.I1 := NEW_ROW.I1 + 1;
      NEW_ROW.I2 := NEW_ROW.I2 + 1;
    END;
    /
    
    DELETE FROM V1,V2 USING V1 RIGHT OUTER JOIN V2 ON V1.I1 = V2.I1 WHERE V1.I1 = 5 OR V2.I1 = 6;
    ```

-   **Actual Results**

    ```sq
    [ERR-91015 : Communication failure.]
    ```

-   **Expected Results**

    ~~~sql
    No rows deleted.
    ~~~

#### Workaround

`없음`

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code



### BUG-49930 In a multiple update statement that updates a view, the error [ERR-31058: Column not found] occurs because the trigger cannot find the modified columns added by the trigger.

#### module 

`qp-dml-pvo`

#### Category 

`Functional Error`

#### Reproducibility 

`Always`

#### Description

Fixed the bug where the **[ERR-31058: Column not found]** error occurs in a multiple update statement updating a view, due to the trigger being unable to find the modified columns added by the trigger.


#### How to reproduce this bug

-   **Reproduction conditions**

    ```sql
    CREATE TABLE T1( I1 INTEGER, I2 INTEGER, I3 INTEGER, I4 INTEGER ) PARTITION BY HASH(I4) ( PARTITION P1, PARTITION P2 ) TABLESPACE SYS_TBS_DISK_DATA;
    
    CREATE VIEW V1 AS SELECT I1, I2 FROM T1 WHERE I1 < 5;
    CREATE SYNONYM V2 FOR V1;
    
    CREATE OR REPLACE TRIGGER TRIG1
    BEFORE UPDATE OF I1 ON T1
    REFERENCING NEW AS NEW_ROW
    FOR EACH ROW
    BEGIN
      NEW_ROW.I1 := NEW_ROW.I1 + 1;
      NEW_ROW.I2 := NEW_ROW.I2 + 1;
    END;
    /
    
    UPDATE V1 RIGHT OUTER JOIN V2 ON V1.I1 = V2.I1 SET V1.I1 = V1.I1 + 1 WHERE V1.I1 = 5 OR V2.I1 = 6;
    ```

-   **Actual Results**

    ```sq
    UPDATE V1 RIGHT OUTER JOIN V2 ON V1.I1 = V2.I1 SET V1.I1 = V1.I1 + 1 WHERE V1.I1 = 5 OR V2.I1 = 6;
    [ERR-31058 : Column not found
    0001 : UPDATE V1 RIGHT OUTER JOIN V2 ON V1.I1 = V2.I1 SET V1.I1 = V1.I1 + 1 WHERE V1.I1 = 5 OR V2.I1 = 6
          ^ ^
    ]
    ```

-   **Expected Results**

    ~~~sql
    No rows updated.
    ~~~

#### Workaround

`없음`

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code



### BUG-49931 Improved the consistency error found when updating a view based on a reference table of a **BEFORE UPDATE** trigger that changes values using **NEW ROW**.

#### module 

`qp-dml-pvo`

#### Category 

`Functional Error`

#### Reproducibility 

`Always`

#### Description

Fixed the result error bug found when updating a view based on a reference table of a **BEFORE UPDATE** trigger that changes values with **NEW ROW**.

The conditions for the occurrence of this bug are:

1. A **BEFORE UPDATE** trigger that modifies values using **NEW ROW**.
2. A view created based on the reference table of the trigger.
3. An **UPDATE** statement that attempts to update the view.


#### How to reproduce this bug

-   **Reproduction conditions**

    ```sql
    CREATE TABLE T1( I1 INTEGER, I2 INTEGER);
    CREATE VIEW V1 AS SELECT I1, I2 FROM T1 WHERE I1 < 5;
    CREATE OR REPLACE TRIGGER TRIG1
    BEFORE UPDATE OF I1 ON T1
    REFERENCING NEW AS NEW_ROW
    FOR EACH ROW
    BEGIN
      NEW_ROW.I1 := NEW_ROW.I1 + 1;
      NEW_ROW.I2 := NEW_ROW.I2 + 1;
    END;
    /
    INSERT INTO V1 VALUES(1,1);
    UPDATE V1 SET I1 = I1;
    SELECT * FROM V1;
    ```

-   **Actual Results**

    ```sql
    I1          I2
    ---------------------------
    2           1
    1 row selected.
    ```

-   **Expected Results**

    ```sql
    I1          I2
    ---------------------------
    2           2
    1 row selected.
    ```

#### Workaround

`없음`

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code



### BUG-49942 The Altibase server may fail to start due to a concurrency issue between disk transaction rollback and ping-pong checkpoint.

#### module

`sm-mem-recovery`

#### Category 

`Fatal`

#### Reproducibility 

`Always`

#### Description

Fixes the concurrency issue between disk transaction rollback and ping-pong checkpoint.

When the following situation occurs during the operation of the Altibase server, the stable checkpoint image file information in the Log Anchor file is not updated. This can lead to Altibase server startup failure or unexpected issues during server operation.

#### How to reproduce this bug

-   **Reproduction conditions**

-   **Actual Results**

-   **Expected Results**

#### Workaround

`없음`

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code



### BUG-49987 Fixed stability issues that occur when using inline views in the FROM clause, string functions in the GROUP BY clause, and using keys from the GROUP BY clause in the SELECT and ORDER BY clauses with analytical functions.

#### module 

`qp-select`

#### Category 

`Fatal`

#### Reproducibility 

`Always`

#### Description

Fixed an issue where the Altibase server shuts down unexpectedly when using inline views in the FROM clause, string functions in the GROUP BY clause, and keys from the GROUP BY clause in the SELECT and ORDER BY clauses with analytical functions.

#### How to reproduce this bug

-   **Reproduction conditions**

    ```sql
    CREATE TABLE T1 ( YYYYMM VARCHAR(6) );
    INSERT INTO T1 VALUES ('201901');
    CREATE TABLE T2 ( YYYYMM VARCHAR(6) );
    INSERT INTO T2 VALUES ('202001');
    SELECT SUBSTR(B1.YYYYMM,1,4) || 'A' AS ACT_YYYY              
         , ROW_NUMBER() OVER( ORDER BY SUBSTR(B1.YYYYMM,1,4)) AS PK_COL
      FROM T1 B2
         , (SELECT A2.YYYYMM AS YYYYMM FROM T2 A2) B1
      WHERE B2.YYYYMM (+)= B1.YYYYMM
      GROUP BY SUBSTR(B1.YYYYMM,1,4);
    ```

-   **Actual Results**

        [ERR-91015 : Communication failure.]

-   **Expected Results**

    ```sql
    ACT_YYYY  PK_COL               
    ----------------------------------
    2020A    1                    
    1 row selected.
    ```

#### Workaround

`없음`

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code



### BUG-49994 Fixed the result error issue that occurs when a window function is used and `NULLS LAST` is applied in the ORDER BY clause.

#### module 

`qp-select`

#### Category 

`Functional Error`

#### Reproducibility 

`Always`

#### Description

Fixed the result error issue that occurs when a window function is used and `NULLS LAST` is applied in the ORDER BY clause.


#### How to reproduce this bug

-   **Reproduction conditions**

    ```sql
    CREATE TABLE T1 ( I1 INTEGER, I2 INTEGER, I3 INTEGER );
    INSERT INTO T1 VALUES(   1,    1,    1);
    INSERT INTO T1 VALUES(   1,    1,    1);
    INSERT INTO T1 VALUES(   2,    1,    1);
    INSERT INTO T1 VALUES(   2,    2,    1);
    INSERT INTO T1 VALUES(   2,    1,    2);
    INSERT INTO T1 VALUES(   2,    1,    1);
    INSERT INTO T1 VALUES(   2,    3,    1);
    INSERT INTO T1 VALUES(   3,    3,    1);
    INSERT INTO T1 VALUES(   1,    1,    3);
    INSERT INTO T1 VALUES(   1,    2,    3);
    INSERT INTO T1 VALUES(NULL,    2,    3);
    INSERT INTO T1 VALUES(NULL, NULL,    3);
    INSERT INTO T1 VALUES(NULL, NULL, NULL);
    
    SELECT COUNT(I3) OVER (PARTITION BY I1
             ORDER BY I2 NULLS LAST ROWS UNBOUNDED PRECEDING) C1
         , COUNT(I3) OVER (PARTITION BY I1
             ORDER BY I2 NULLS LAST RANGE 1 PRECEDING) C7
      FROM T1
     GROUP BY I1,I2,I3
     ORDER BY C1,C7;
    ```

-   **Actual Results**

    ```sql
    C1                   C7                   
    ---------------------------------------------
    1                    1                    
    1                    1                    
    2                    1                    
    2                    1                    
    1                    2                    
    2                    2                    
    1                    2                    
    2                    2                    
    4                    2                    
    3                    3                    
    3                    3                    
    11 rows selected.
    ```

-   **Expected Results**

    ```sql
    C1                   C7                   
    ---------------------------------------------
    1                    1                    
    1                    1                    
    1                    2                    
    1                    2                    
    2                    1                    
    2                    1                    
    2                    2                    
    2                    2                    
    3                    3                    
    3                    3                    
    4                    2                    
    11 rows selected.
    ```

#### Workaround

```sql
SELECT *
  FROM (SELECT COUNT(I3) OVER (PARTITION BY I1
                 ORDER BY I2 NULLS LAST ROWS UNBOUNDED PRECEDING) C1
             , COUNT(I3) OVER (PARTITION BY I1
                 ORDER BY I2 NULLS LAST RANGE 1 PRECEDING) C7
          FROM T1
         GROUP BY I1,I2,I3 )
 ORDER BY C1,C7;
```

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code



### BUG-49998 Fixed an issue where an error occurred when using the same column more than once in the SET clause of a MULTIPLE UPDATE statement.

#### module 

`qp-dml-pvo`

#### Category 

`Functional Error`

#### Reproducibility 

`Always`

#### Description
The issue where an error occurred when using the same column more than once in the `SET` clause of a `MULTIPLE UPDATE` statement has been fixed.


#### How to reproduce this bug

-   **Reproduction conditions**

    ```sql
    CREATE SYNONYM V2 FOR V1;
    CREATE TABLE T1( I1 INTEGER, I2 INTEGER, I3 INTEGER, I4 INTEGER );
    CREATE VIEW V1 AS SELECT I1, I2 FROM T1 WHERE I1 < 5;
    INSERT INTO T1 SELECT ROWNUM, ROWNUM + 1, ROWNUM, ROWNUM + 1 FROM DUAL CONNECT BY LEVEL <= 20;
    
    UPDATE /*+ no_plan_cache */ V1 RIGHT OUTER JOIN V2 ON V1.I1 = V2.I1 SET V1.I1 = V1.I1 - 1, V1.I1 = V1.I1 + 1 WHERE V1.I1 = 3 OR V2.I1 = 4;
    
    SELECT * FROM T1 WHERE I1 <> I3 OR I2 <> I4;
    ```

-   **Actual Results**

    ```sql
    2 rows updated.
    ```

-   **Expected Results**

    ```sql
    [ERR-31072 : Duplicate columns specified in a SET clause.]
    ```

#### Workaround

`없음`

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code



### BUG-50002 Fixed a stability issue that occurs when a hash-partitioned table is processed using the USE_FULL_NL join method.

#### module 

`qp`

#### Category

`Fatal`

#### Reproducibility 

`Always`

#### Description
Fixed a stability issue that occurs when a hash-partitioned table is processed using the USE_FULL_NL join method.


#### How to reproduce this bug

-   **Reproduction conditions**

    ~~~sql
    CREATE TABLE T1 ( I1 INTEGER, I2 VARCHAR(256) ) 
    PARTITION BY RANGE_USING_HASH (I1) 
    ( PARTITION P1 VALUES LESS THAN (400), 
      PARTITION P3 VALUES DEFAULT
    );
    
    INSERT INTO T1 VALUES (1, 9);
    
    SELECT /*+ NO_PLAN_CACHE USE_FULL_NL(V1, V2) */*
      FROM T1 V1
         , T1 V2
     WHERE V1.I2 = V2.I1;
    ~~~

-   **Actual Results**

    ~~~sql
    [ERR-91015 : Communication failure.]
    ~~~

-   **Expected Results**

    ~~~sql
    I1          I2                    I1          I2                    
    -------------------------------------------------------------------------
    No rows selected.
    ~~~

#### Workaround

`없음`

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code



### BUG-50004 Changes the default values of the AKU_QUERY_TIMEOUT and SYNC_PARALLEL_COUNT properties in the aku.conf.sample file.

#### module 

`aku`

#### Category 

`Maintainability`

#### Reproducibility 

`Always`

#### Description

Changes the default values of the AKU_QUERY_TIMEOUT and SYNC_PARALLEL_COUNT properties in the aku.conf.sample file.

#### How to reproduce this bug

-   **Reproduction conditions**

-   **Actual Results**

-   **Expected Results**

#### Workaround

`없음`

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code



### BUG-50017 Using the DELETE clause in the CREATE QUEUE statement in APRE results in a syntax error during compilation.

#### module 

`ul-odbc`

#### Category 

`Functional Error`

#### Reproducibility 

`Always`

#### Description
Fixed an issue where using the DELETE clause in the CREATE QUEUE statement in APRE caused a syntax error during compilation.

`[ERR-000H : parse error, unexpected TR_DELETE, expecting TS_SEMICOLON]`

To apply this bug fix, you need to patch APRE.


#### How to reproduce this bug

-   **Reproduction conditions**

-   **Actual Results**

-   **Expected Results**

#### Workaround

`없음`

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code



### BUG-50022 Improved stability when performing a multiple update on a target table with a TIMESTAMP column.

#### module 

`qp-dml-pvo`

#### Category 

`Fatal`

#### Reproducibility 

`Always`

#### Description

Improved stability when performing a multiple update on a target table with a TIMESTAMP column.


#### How to reproduce this bug

-   **Reproduction conditions**

    ```sql
    CREATE TABLE T1 ( I1 INTEGER, I2 INTEGER ) ;
    CREATE TABLE T2 ( I1 VARCHAR(100) );
    ALTER TABLE T1 ADD COLUMN ( I3 TIMESTAMP VARIABLE );
    UPDATE T1 LEFT OUTER JOIN T2 ON T1.I1 = T2.I1 SET T1.I1 = 100, T1.I2 = 100 WHERE T2.I1 = 6;
    ```

-   **Actual Results**

    ```sql
    [ERR-91015 : Communication failure.] 발생하며 Altibase 서버 비정상 종료
    ```

-   **Expected Results**

    ```sql
    No rows updated.
    ```

#### Workaround

`없음`

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code



### BUG-50032 Added the `force` option to the `oaUtility` utility.

#### module 

`rp-oraAdapter`

#### Category 

`Functionality`

#### Reproducibility 

`Rare`

#### Description

Added the `force` option to the `oaUtility` utility. This option allows starting `oraAdapter` without checking for primary key constraints on the replication target table.

#### How to reproduce this bug

-   **Reproduction conditions**

-   **Actual Results**

-   **Expected Results**

#### Workaround

`없음`

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code



### BUG-50038 Enhanced error messages for exception handling during the startup of `jdbcAdapter` and `oraAdapter`.

#### module 

`rp-oraAdapter`, `rp-jdbcAdapter`

#### Category 

`Functional Error`

#### Reproducibility 

`Always`

#### Description

Improved error messages for the following exceptions during the startup of jdbcAdapter and oraAdapter:

- Initialization failure
- Memory allocation failure
- Failure in reading the adapter property file
- Failure in opening the adapter trace log file
- Failure in reading the adapter error message file


#### How to reproduce this bug

-   **Reproduction conditions**

-   **Actual Results**

-   **Expected Results**

#### Workaround

`없음`

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code



### BUG-50048 Added session access control functionality to aku.

#### module

`aku`

#### Category 

`Functionality`

#### Reproducibility

`Always`

#### Description

Added session access control functionality to the `aku -p start` operation on SLAVE AKU.

In this updated process, before requesting a replication SYNC from the MASTER AKU, the SLAVE AKU sets the administrator access mode on its pod and forcefully terminates any connected sessions. Once the replication SYNC is completed from MASTER AKU and the replication starts on SLAVE AKU, the administrator access mode is released.


#### How to reproduce this bug

-   **Reproduction conditions**

-   **Actual Results**

-   **Expected Results**

#### Workaround

`없음`

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code



### BUG-50050 Added functionality to remove conditions in views or inline views that do not affect the logical result of the query.

#### module 

`qp`

#### Category 

`Enhancement`

#### Reproducibility 

`Always`

#### Description

Added functionality to remove conditions in views or inline views that do not affect the logical result of the query.

In this enhancement, redundant conditions that do not impact the logical result of the query are removed from the following clauses in views or inline views:

- ON clause in the FROM clause
- WHERE clause (except when the Outer Join symbol (+) is present)
- HAVING clause

This feature may cause changes in the execution plan of the query.

To use this feature in Altibase 7.1, you must modify a private property value or use a private hint. If necessary, please contact Altibase Technical Support.


#### How to reproduce this bug

-   **Reproduction conditions**

    ```sql
    CREATE TABLE T1 (C1 INTEGER, C2 INTEGER, C3 CHAR(10), C4 CHAR(10));
    ALTER TABLE T1 ADD CONSTRAINT T1_PK PRIMARY KEY (C2,C1);
    
    CREATE TABLE T2 (C1 INTEGER, C2 INTEGER, C3 CHAR(10), C4 CHAR(10));
    ALTER TABLE T2 ADD CONSTRAINT T2_PK PRIMARY KEY (C1);
    
    CREATE INDEX T1_IDX_1 ON T1 ( C1,C2 );
    
    ALTER SESSION SET EXPLAIN PLAN = ON;
    
    SELECT *
      FROM (SELECT A.C1, A.C2, B.C3
              FROM T1 A, T2 B
             WHERE 0 IS NULL
                OR 0 = A.C1
               AND A.C1 = B.C1 ) ;
    ```
    
-   **Actual Results**

    ```sql
    C1          C2          C3          
    ----------------------------------------
    No rows selected.
    ------------------------------------------------------------
    PROJECT ( COLUMN_COUNT: 3, TUPLE_SIZE: 20, COST: 1290336.82 )
     JOIN ( METHOD: NL, COST: 1249804.63 )
      SCAN ( TABLE: SYS.T1 $$1_$NONAME_$A, FULL SCAN, ACCESS: 0, COST: 122.04 )
      SCAN ( TABLE: SYS.T2 $$2_$NONAME_$B, FULL SCAN, ACCESS: 0, COST: 116.76 )
    ------------------------------------------------------------
    ```

-   **Expected Results**

    ```sql
    C1          C2          C3
    ----------------------------------------
    No rows selected.
    ------------------------------------------------------------
    PROJECT ( COLUMN_COUNT: 3, TUPLE_SIZE: 20, COST: 487.20 )
     JOIN ( METHOD: INDEX_NL, COST: 81.88 )
      SCAN ( TABLE: SYS.T1 $$1_$NONAME_$A, INDEX: SYS.T1_IDX_1, RANGE SCAN, ACCESS: 0, COST: 0.01 )
      SCAN ( TABLE: SYS.T2 $$2_$NONAME_$B, INDEX: SYS.T2_PK, RANGE SCAN, ACCESS: 0, COST: 116.76 )
    ------------------------------------------------------------
    ```

#### Workaround

`없음`

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code



Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    7.1.0.8.2     |          6.5.1          |    8.10.1    |        7.1.7        |            7.4.7             |

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
