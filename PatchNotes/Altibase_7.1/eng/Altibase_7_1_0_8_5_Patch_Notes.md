# Altibase 7.1.0.8.5 Patch Notes

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [New Features](#new-features)
    - [BUG-49970 Provided TOTAL_CPU(Total CPU usage of OS),PROC_CPU(Total CPU usage of Altibase process)](#bug-49970-provided-total_cputotal-cpu-usage-of-osproc_cputotal-cpu-usage-of-altibase-process)
    - [BUG-50109 RECEIVE_ONLY option in replication.](#bug-50109%C2%A0receive_only-option-in-replication)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-47430 Add `CHECK` to `V$RESERVED_WORDS` and correct reserved words with incorrect RESERVED_TYPE.](#bug-47430%C2%A0add-check-to-vreserved_words-and-correct-reserved-words-with-incorrect-reserved_type)
    - [BUG-47989 The error message [ERR-3134F: Invalid use of sequence] has been modified to include the syntax that triggered the error.](#bug-47989%C2%A0the-error-message-err-3134f-invalid-use-of-sequence-has-been-modified-to-include-the-syntax-that-triggered-the-error)
    - [BUG-49399 Fixed an issue with concurrency control between the statements executed in the transaction and the checkpoint operation.](#bug-49399%C2%A0fixed-an-issue-with-concurrency-control-between-the-statements-executed-in-the-transaction-and-the-checkpoint-operation)
    - [BUG-49765 Change the error message of ERR-2106B in an environment with `REGEXP_MODE=1` (PCRE2 compatibility mode).](#bug-49765%C2%A0change-the-error-message-of-err-2106b-in-an-environment-with-regexp_mode1-pcre2-compatibility-mode)
    - [BUG-49936  Fixed issue with incorrect behavior after deleting PK on partitioned table.](#bug-49936%C2%A0-fixed-issue-with-incorrect-behavior-after-deleting-pk-on-partitioned-table)
    - [BUG-50210 Fixed an error that occurs when a table in the USING clause of the MERGE statement contains a LOB column, and that LOB column is used in the ON clause or MATCHED ... UPDATE clause.](#bug-50210%C2%A0fixed-an-error-that-occurs-when-a-table-in-the-using-clause-of-the-merge-statement-contains-a-lob-column-and-that-lob-column-is-used-in-the-on-clause-or-matched--update-clause)
    - [BUG-50232 Fixed an issue where using _PROWID in a JOIN predicate could reference incorrect memory.](#bug-50232%C2%A0fixed-an-issue-where-using-_prowid-in-a-join-predicate-could-reference-incorrect-memory)
    - [BUG-50248 When the alias of a function used in the target clause of a hierarchical query is the same as a column name used in the ORDER SIBLINGS BY clause, it may cause server to shut down abnormally.](#bug-50248%C2%A0when-the-alias-of-a-function-used-in-the-target-clause-of-a-hierarchical-query-is-the-same-as-a-column-name-used-in-the-order-siblings-by-clause-it-may-cause-server-to-shut-down-abnormally)
    - [BUG-50256 Fixed an issue where, after creating a Primary Key (PK) with a column that has a NOT NULL constraint and a column without a NOT NULL constraint, and then dropping the PK, the NOT NULL constraint on the affected column is not removed.](#bug-50256%C2%A0fixed-an-issue-where-after-creating-a-primary-key-pk-with-a-column-that-has-a-not-null-constraint-and-a-column-without-a-not-null-constraint-and-then-dropping-the-pk-the-not-null-constraint-on-the-affected-column-is-not-removed)
    - [BUG-50257 Enhance exception handling for disk index page allocation failure.](#bug-50257-enhance-exception-handling-for-disk-index-page-allocation-failure)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [Compatibility](#compatibility)
    - [Altibase Server Properties](#altibase-server-properties)
    - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-49970 Provided TOTAL_CPU(Total CPU usage of OS),PROC_CPU(Total CPU usage of Altibase process)

-   **module** : ux-altiMon

-   **Category** : Functionality

-   **Reproducibility** : Always

-   **Description** : Provided TOTAL_CPU(Total CPU usage of OS),PROC_CPU(Total CPU usage of Altibase process) in altimon.

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

### BUG-50109 RECEIVE_ONLY option in replication.

-   **module** : rp-control

-   **Category** : Enhancement

-   **Reproducibility** : Always

-   **Description** : A RECEIVE_ONLY option (Receive-Only option) has been added as a replication feature. The metaverse version has changed from 8.10.1 to 8.11.1 in this bug fix. If a rollback is needed after the patch, see [Meta Downgrade](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/eng/Installation Guide.md#meta-downgrade).

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

### BUG-47430 Add `CHECK` to `V$RESERVED_WORDS` and correct reserved words with incorrect RESERVED_TYPE.

-   **module** : qp-meta

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Add the reserved word CHECK to `V$RESERVED_WORDS` and correct reserved words with incorrect RESERVED_TYPE. This fix does not affect user systems.

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

### BUG-47989 The error message [ERR-3134F: Invalid use of sequence] has been modified to include the syntax that triggered the error.

-   **module** : qp-dml-execute

-   **Category** : Message Error

-   **Reproducibility** : Always

-   **Description** : Previously, only the error message **[ERR-3134F: Invalid use of sequence]** was displayed, making it difficult to locate the source of the error. With this fix, the syntax that triggered the error will also be displayed, making it easier to identify the location of the error.
    변경

- **How to reproduce this bug**

  - **Reproduction conditions**

        CREATE TABLE T1 (C1 INTEGER);
        CREATE SEQUENCE S1;
        VAR VAR INTEGER;
        PREPARE INSERT INTO T1 VALUES(1) RETURN S1.NEXTVAL INTO :VAR;
        SELECT C1 FROM T1 LIMIT S1.NEXTVAL;
        SELECT C1 FROM T1 LOOP S1.NEXTVAL;

  - **Actual Results**

        iSQL> PREPARE INSERT INTO T1 VALUES(1) RETURN S1.NEXTVAL INTO :VAR;
        [ERR-3134F : Invalid use of sequence]
        iSQL> SELECT C1 FROM T1 LIMIT S1.NEXTVAL;
        [ERR-3134F : Invalid use of sequence]
        iSQL> SELECT C1 FROM T1 LOOP S1.NEXTVAL;
        [ERR-3134F : Invalid use of sequence]

  -   **Expected Results**

          iSQL> prepare insert into t1 values(1) return s1.nextval into :var;
          [ERR-3134F : Invalid use of sequence
          0001 : insert into T1 values(1) return S1.NEXTVAL into :var
                                                ^         ^
          ]
          iSQL> select c1 from t1 limit s1.nextval;
          [ERR-3134F : Invalid use of sequence
          0001 : select C1 from T1 limit S1.NEXTVAL
                                        ^         ^
          ]
          iSQL> select c1 from t1 loop s1.nextval;
          [ERR-3134F : Invalid use of sequence
          0001 : select C1 from T1 loop S1.NEXTVAL
                                       ^         ^
          ]

-   **Workaround**

-   **Changes**

    - Performance view

    - Property

    - Compile Option

    - Error Code

      - Before : [ERR-3134F : Invalid use of sequence]

      - After : [ERR-3134F : Invalid use of sequence
0001 : insert into T1 values(1) return S1.NEXTVAL into :var
                                      ^         ^
]



### BUG-49399 Fixed an issue with concurrency control between the statements executed in the transaction and the checkpoint operation.

-   **module** : sm-mem-recovery

-   **Category** : Reliability

-   **Reproducibility** : Always

-   **Description** : Fixed an issue with concurrency control between the statements executed in the transaction and the checkpoint operation.

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

### BUG-49765 Change the error message of ERR-2106B in an environment with `REGEXP_MODE=1` (PCRE2 compatibility mode).

-   **module** : qp

-   **Category** : Functional Error

-   **Reproducibility** : Always

- **Description** : Modify the error message occurred when using a fixed table column as an argument in a regular expression function with `REGEXP_MODE=1` (PCRE2 compatibility mode) in a UTF8 character set environment:

  -   Before: ERR-2106B : Unsupported character set by PCRE2 library0001 

  -   After: ERR-2106B : Unable to execute this operation because of the database server character set.

- **How to reproduce this bug**

  - **Reproduction conditions**

        ALTER SESSION SET REGEXP_MODE=1;
        SELECT REGEXP_COUNT(DUMMY, '/') FROM DUAL;

  - **Actual Results**

    - in Altibase 7.1.0.8.4

      ```
      [ERR-2106B : Unable to execute this operation because of the database server character set.
      0001 : SELECT REGEXP_COUNT(DUMMY, '/') FROM DUAL
                   ^                       ^
      ]
      ```

    - in earlier version of Altibase 7.1.0.8.3

      ```
      [ERR-2106B : Unsupported character set by PCRE2 library0001 : SELECT REGEXP_COUNT(DUMMY, '/') FROM DUAL             ^                       ^]
      ```

  - **Expected Results**

        REGEXP_COUNT(DUMMY, '/')
        ---------------------------
        0
        1 row selected.

- **Workaround**

      ALTER SESSION SET REGEXP_MODE=1;
      SELECT REGEXP_COUNT(CONVERT(DUMMY, 'UTF8'), '/') FROM DUAL;

- **Changes**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

### BUG-49936  Fixed issue with incorrect behavior after deleting PK on partitioned table.

-   **module** : qp-ddl-dcl-execute

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : An issue was identified where, after creating a non-partitioned index on a partitioned table with a Primary Key (PK), deleting the PK and inserting NULL data into the column that was previously the PK could lead to incorrect behavior. This issue has been fixed to ensure proper handling of such operations.

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

### BUG-50210 Fixed an error that occurs when a table in the USING clause of the MERGE statement contains a LOB column, and that LOB column is used in the ON clause or MATCHED ... UPDATE clause.

-   **module** : qp

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : An issue was identified where, in the MERGE statement, when the table in the USING clause contains a LOB column, and that LOB column is used in the ON clause or the "MATCHED .. UPDATE" clause, an ERR-2100C: Conversion not applicable error occurs. This issue has been fixed.

- **How to reproduce this bug**

  - **Reproduction conditions**

        DROP TABLE T1 ;
        DROP TABLE T2 ;
        CREATE TABLE T1 ( I1 INT, I2 CLOB, i3 int );
        INSERT INTO T1 VALUES ( 1,1,1);
        INSERT INTO T1 VALUES ( 2,2,2);
    
        CREATE TABLE T2 ( I1 INT, I2 CLOB, i3 int );
        INSERT INTO T2 VALUES ( 1,10,10);
        INSERT INTO T2 VALUES ( 2,20,20);
    
        MERGE INTO T1 A USING T2 B ON A.I1 = B.I1
        WHEN MATCHED THEN
        UPDATE SET A.I2 = B.I2
        DELETE WHERE A.I1=3;

  -   **Actual Results**

          [ERR-2100C : Conversion not applicable.]

  -   **Expected Results**

          2 row merged.

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50232 Fixed an issue where using _PROWID in a JOIN predicate could reference incorrect memory.

-   **module** : qp

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where using _PROWID in a JOIN predicate could reference incorrect memory.

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

### BUG-50248 When the alias of a function used in the target clause of a hierarchical query is the same as a column name used in the ORDER SIBLINGS BY clause, it may cause server to shut down abnormally.

-   **module** : qp-select-execute

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where using the alias of a function in the target clause of a hierarchical query the same as a column name used in the ORDER SIBLINGS BY clause could cause an abnormal termination.

- **How to reproduce this bug**

  - **Reproduction conditions**

        DROP TABLE T1;
        CREATE TABLE T1
        (
            STM    VARCHAR(10) NOT NULL,
            STC    VARCHAR(10) NOT NULL,
            USCI    VARCHAR(10),
            SCIS    NUMERIC(10)
        );
        INSERT INTO T1 VALUES( 'S1041360', '1', '2', '1' );
        INSERT INTO T1 VALUES( 'S1041360', '2', '3', '1' );
        INSERT INTO T1 VALUES( 'S1041360', '3', '4', '1' );
    
        SELECT X.STM
        FROM (
        SELECT
            STM
           ,NVL(USCI,STC) AS USCI
          , SCIS AS SCIS
            FROM (
                     SELECT Y2.STM, Y2.USCI, Y2.STC, Y2.SCIS
                     FROM T1 Y2
                    )
            CONNECT BY PRIOR  STC = USCI
            ORDER SIBLINGS BY  USCI,STC
            ) X
        ;

  -   **Actual Results**

          [ERR-91015 : Communication failure.]

  -   **Expected Results**

          STM
          --------------
          S1041360
          S1041360
          S1041360
          S1041360
          S1041360
          S1041360
          6 rows selected.

- **Workaround**

      SELECT X.STM
      FROM (
      SELECT
          STM
         ,NVL(USCI,STC) AS USCI2
        , SCIS AS SCIS
          FROM (
                   SELECT Y2.STM, Y2.USCI, Y2.STC, Y2.SCIS
                   from t1 Y2
                  )
          CONNECT BY PRIOR  STC = USCI
          ORDER SIBLINGS BY  USCI,STC
          ) X
      ;

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50256 Fixed an issue where, after creating a Primary Key (PK) with a column that has a NOT NULL constraint and a column without a NOT NULL constraint, and then dropping the PK, the NOT NULL constraint on the affected column is not removed.

-   **module** : qp-ddl-dcl-execute

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where, after creating a Primary Key (PK) with a column that has a NOT NULL constraint and a column without a NOT NULL constraint, and then dropping the PK, the NOT NULL constraint on the affected column is not removed. This issue could lead to incorrect behavior.

-   **How to reproduce this bug**

    -   **Reproduction conditions**

            DROP TABLE T1;
            CREATE TABLE T1(
                    I1 INTEGER,
                    I2 INTEGER,
                    I3 INTEGER
                );
            ALTER TABLE T1 ALTER COLUMN ( I2 NOT NULL );
            ALTER TABLE T1 ADD CONSTRAINT T1_PK PRIMARY KEY ( I1, I2 );
            SELECT
                  CAST( TABLE_NAME  AS CHAR( 12 ) ) TABTABLE_NAME,
                  CAST( COLUMN_NAME AS CHAR( 12 ) ) COLUMN_NAME,
                  CAST( IS_NULLABLE AS CHAR( 12 ) ) IS_NULLABLE
                FROM (
                  SELECT *
                  FROM
                    SYSTEM_.SYS_TABLES_ T,
                    SYSTEM_.SYS_COLUMNS_ C
                  WHERE
                    T.TABLE_NAME = 'T1' AND
                    T.TABLE_ID = C.TABLE_ID );
            ALTER TABLE T1 DROP CONSTRAINT T1_PK;    // PK 삭제
            SELECT
                  CAST( TABLE_NAME  AS CHAR( 12 ) ) TABTABLE_NAME,
                  CAST( COLUMN_NAME AS CHAR( 12 ) ) COLUMN_NAME,
                  CAST( IS_NULLABLE AS CHAR( 12 ) ) IS_NULLABLE
                FROM (
                  SELECT *
                  FROM
                    SYSTEM_.SYS_TABLES_ T,
                    SYSTEM_.SYS_COLUMNS_ C
                  WHERE
                    T.TABLE_NAME = 'T1' AND
                    T.TABLE_ID = C.TABLE_ID );

    -   **Actual Results**

            ###### PK 삭제 전
            TABTABLE_NAME  COLUMN_NAME   IS_NULLABLE   
            -----------------------------------------------
            T1            I1            F             
            T1            I2            F             
            T1            I3            T             
            3 rows selected.
    
            ##### PK 삭제 후
            TABTABLE_NAME  COLUMN_NAME   IS_NULLABLE   
            -----------------------------------------------
            T1            I1            F             
            T1            I2            F             
            T1            I3            T             
            3 rows selected.

    -   **Expected Results**

            ##### PK 삭제 후
            TABTABLE_NAME  COLUMN_NAME   IS_NULLABLE   
            -----------------------------------------------
            T1            I1            T             
            T1            I2            F             
            T1            I3            T             
            3 rows selected.

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50257 Enhance exception handling for disk index page allocation failure.

-   **module** : sm-disk-index

-   **Category** : Fatal

-   **Reproducibility** : Impossible

-   **Description** : Modified exception handling to address the issue of server abnormal termination during disk index page allocation failure, and added debugging information when an error occurs. This bug fix does not impact the system.

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
| 7.1.0.8.5        | 6.5.1                   | 8.11.1       | 7.1.7               | 7.4.7                        |

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
