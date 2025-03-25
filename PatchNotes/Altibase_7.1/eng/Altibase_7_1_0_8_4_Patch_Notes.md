# Altibase 7.1.0.8.4 Patch Notes

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [New Features](#new-features)
    - [BUG-50145 Add a feature to create the `aku_start_completed` file when `aku -p start` is successful.](#bug-50145%C2%A0add-a-feature-to-create-the-aku_start_completed-file-when-aku--p-start-is-successful)
    - [BUG-50206 Add a property `AKU_ADDRESS_CHECK_COUNT` to check the connectivity to the local address during `aku -p start`.](#bug-50206%C2%A0add-a-property-aku_address_check_count-to-check-the-connectivity-to-the-local-address-during-aku--p-start)
    - [BUG-50191 New threads have been added in altimon to measure CPU usage: one for measuring OS CPU usage and another for measuring Altibase CPU usage.](#bug-50191%C2%A0new-threads-have-been-added-in-altimon-to-measure-cpu-usage-one-for-measuring-os-cpu-usage-and-another-for-measuring-altibase-cpu-usage)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-49101 Fixed an issue where the page lock was not released when a page read failure occurred.](#bug-49101-fixed-an-issue-where-the-page-lock-was-not-released-when-a-page-read-failure-occurred)
    - [BUG-49584 When executing a DDL to change the tablespace of a memory-partitioned table that includes a LOB column, the tablespace of the LOB column is not changed.](#bug-49584-when-executing-a-ddl-to-change-the-tablespace-of-a-memory-partitioned-table-that-includes-a-lob-column-the-tablespace-of-the-lob-column-is-not-changed)
    - [BUG-49890 Changed the error message that occurs when attempting to set `ALTER SESSION SET REGEXP_MODE = 1` with an unsupported character set in the PCRE2 library.](#bug-49890%C2%A0changed-the-error-message-that-occurs-when-attempting-to-set-alter-session-set-regexp_mode--1-with-an-unsupported-character-set-in-the-pcre2-library)
    - [BUG-50010 A concurrency issue may occur if the same monitoring task is executed simultaneously due to delays in monitoring tasks under abnormally high server load.](#bug-50010-a-concurrency-issue-may-occur-if-the-same-monitoring-task-is-executed-simultaneously-due-to-delays-in-monitoring-tasks-under-abnormally-high-server-load)
    - [BUG-50024  In Altimon, when there is no result from the DB monitoring query, values are missing when outputting data to GroupMetrics.](#bug-50024-%C2%A0in-altimon-when-there-is-no-result-from-the-db-monitoring-query-values-are-missing-when-outputting-data-to-groupmetrics)
    - [BUG-50066 Prevents an issue where a "Freed Memory Read" error may occur due to memory released in concurrency control if a DDL statement fails during execution.](#bug-50066%C2%A0prevents-an-issue-where-a-freed-memory-read-error-may-occur-due-to-memory-released-in-concurrency-control-if-a-ddl-statement-fails-during-execution)
    - [BUG-50086 Fixed an issue where the number of physical cores was incorrectly estimated in a hyper-threading off environment.](#bug-50086%C2%A0fixed-an-issue-where-the-number-of-physical-cores-was-incorrectly-estimated-in-a-hyper-threading-off-environment)
    - [BUG-50130  Fixed an issue where an error occurred during the creation of the system stored package when applying a patch using the package installer.](#bug-50130%C2%A0-fixed-an-issue-where-an-error-occurred-during-the-creation-of-the-system-stored-package-when-applying-a-patch-using-the-package-installer)
    - [BUG-50164  Fixed an issue where the page lock was not released when the expansion failed due to space exhaustion in a volatile table.](#bug-50164%C2%A0-fixed-an-issue-where-the-page-lock-was-not-released-when-the-expansion-failed-due-to-space-exhaustion-in-a-volatile-table)
    - [BUG-50174  Removes unused properties -REPLICATION_SERVICE_WAIT_MAX_LIMIT from the altibase.properties.release file.](#bug-50174%C2%A0-removes-unused-properties--replication_service_wait_max_limit-from-the-altibasepropertiesrelease-file)
    - [BUG-50177 Fixed an issue where replication fails when an undo tablespace becomes full on a disk table that contains a LOB.](#bug-50177-fixed-an-issue-where-replication-fails-when-an-undo-tablespace-becomes-full-on-a-disk-table-that-contains-a-lob)
    - [BUG-50196 Fixed an issue where a sequence created with the NOCYCLE option behaves as CYCLE after executing the `ALTER SEQUENCE` statement and restarting the server.](#bug-50196-fixed-an-issue-where-a-sequence-created-with-the-nocycle-option-behaves-as-cycle-after-executing-the-alter-sequence-statement-and-restarting-the-server)
    - [BUG-50197 Improved the validation for specifying the LOB tablespace in the memory-partitioned table creation statement.](#bug-50197-improved-the-validation-for-specifying-the-lob-tablespace-in-the-memory-partitioned-table-creation-statement)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [Compatibility](#compatibility)
    - [Altibase Server Properties](#altibase-server-properties)
    - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-50145 Add a feature to create the `aku_start_completed` file when `aku -p start` is successful.

-   **module** : aku

-   **Category** : Enhancement

-   **Reproducibility** : Always

-   **Description** : Add a feature to create the `aku_start_completed` file in the `/tmp` directory when the `aku -p start` command completes successfully. This file will be deleted when `aku -p end` or `aku -p clean` is executed. If the `aku_start_completed` file already exists in `/tmp`, an error message will be displayed, and the `aku -p start` command will terminate.
    
    If an error occurs during the execution of `aku -p start`, the `aku_start_completed` file will not be created.
    
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

### BUG-50206 Add a property `AKU_ADDRESS_CHECK_COUNT` to check the connectivity to the local address during `aku -p start`.

-   **module** : aku

-   **Category** : Enhancement

-   **Reproducibility** : Always

-   **Description** : Add the `AKU_ADDRESS_CHECK_COUNT` property to the `aku.conf` configuration file. This property allows you to set the number of times to check if the local DNS is registered with the endpoint during `aku -p start`. The default value is 30.

-   **How to reproduce this bug**
    -   **Reproduction conditions**

    -   **Actual Results**

    -   **Expected Results**

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
        -   New
            -   AKU_ADDRESS_CHECK_COUNT
                -   Default value : 30
                -   Description: When `aku -p start` is executed, it attempts to connect to the local IP the number of times specified by the `AKU_ADDRESS_CHECK_COUNT`.
    -   Compile Option
    -   Error Code

### BUG-50191 New threads have been added in altimon to measure CPU usage: one for measuring OS CPU usage and another for measuring Altibase CPU usage.

-   **module** : ux-altiMon

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : New threads have been added in altimon to measure CPU usage: one for measuring OS CPU usage and another for measuring Altibase CPU usage.
    
    User can configure the execution interval of the CPU usage (%) measurement thread using the `CpuSamplingInterval` element in the `config.xml` file. The unit is in seconds, and the default value is 3 seconds.
    
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

### BUG-49101 Fixed an issue where the page lock was not released when a page read failure occurred.

-   **module** : sm

-   **Category** : Hang

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where the page lock was not released when a page read failure occurred.

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

### BUG-49584 When executing a DDL to change the tablespace of a memory-partitioned table that includes a LOB column, the tablespace of the LOB column is not changed.

-   **module** : qp-ddl-dcl-execute

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where the tablespace of a LOB column was not updated when changing the tablespace of a memory-partitioned table, which could cause an abnormal server shutdown when executing the `ALTER TABLE ... MODIFY COLUMN` statement.

- **How to reproduce this bug**

  - **Reproduction conditions**

        CREATE MEMORY TABLESPACE MEM_TEST_TBS_0 SIZE 32M AUTOEXTEND ON;
        CREATE TABLE T1 ( I1 INTEGER DEFAULT 1, I2 VARCHAR(4) , I3 CLOB )
        PARTITION BY RANGE ( I1 )
        ( PARTITION P1 VALUES LESS THAN( 10 ),
        PARTITION P2 VALUES DEFAULT
        ) ;
        ALTER TABLE T1 ALTER TABLESPACE MEM_TEST_TBS_0 ;
        INSERT INTO T1 VALUES (3, 1, 17);
        
        ALTER TABLE T1 MODIFY (I2 VARCHAR(1));

  -   **Actual Results**

          [ERR-91015 : Communication failure.]

  -   **Expected Results**

          Alter success.

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49890 Changed the error message that occurs when attempting to set `ALTER SESSION SET REGEXP_MODE = 1` with an unsupported character set in the PCRE2 library.

-   **module** : qp

-   **Category** : Usability

-   **Reproducibility** : Always

-   **Description** : Changed the error message that occurs when attempting to set `ALTER SESSION SET REGEXP_MODE = 1` with an unsupported character set in the PCRE2 library.
    
    - Before:
    
      ERR-2106B : Unsupported character set by PCRE2 library
    
    - After:
    
      ERR-2106B : Unable to execute this operation because of the database server character set.
    
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
      -   0x2106B ( 135275) mtERR_ABORT_PCRE2_NOT_SUPPORTED_ENCODING Unable to execute this operation because of the database server character set.
          -   Cause: The current database server character set is not supported in REGEXP_MODE=1 (i.e., PCRE2 compatibility mode).
          -   Action:
              -   Check the character sets supported by REGEXP_MODE = 1 in the SQL Reference.
              -   Check the Altibase server character set in v$nls_parameters.
              -   If the current regexp_mode property value is 0, change the database
              -   server character set to one supported by REGEXP_MODE = 1.
              -   If the current regexp_mode property value is 1, change it to 0 or change the database server character set to one supported by REGEXP_MODE = 1.
              -   To change the database server character set, you need to re-create the database.

### BUG-50010 A concurrency issue may occur if the same monitoring task is executed simultaneously due to delays in monitoring tasks under abnormally high server load.

-   **module** : ux-altiMon

-   **Category** : Functional Error

-   **Reproducibility** : Rare

-   **Description** : Fixed a concurrency issue that could occur when the same monitoring task was executed simultaneously due to delays in monitoring tasks under abnormally high server load.

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

### BUG-50024  In Altimon, when there is no result from the DB monitoring query, values are missing when outputting data to GroupMetrics.

-   **module** : ux-altiMon

-   **Category** : Usability

-   **Reproducibility** : Always

-   **Description** : Fixes an issue where output values were missing when data was output to GroupMetrics for a DB monitoring query result of 'no rows.'

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

### BUG-50066 Prevents an issue where a "Freed Memory Read" error may occur due to memory released in concurrency control if a DDL statement fails during execution.

-   **module** : qp

-   **Category** : Memory Error

-   **Reproducibility** : Frequence

-   **Description** : Prevents an issue where a "Freed Memory Read" error may occur due to memory released in concurrency control if a DDL statement fails during execution.
    
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

### BUG-50086 Fixed an issue where the number of physical cores was incorrectly estimated in a hyper-threading off environment.

-   **module** : id

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where the number of physical cores was incorrectly estimated in a hyper-threading off environment.
    
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

### BUG-50130  Fixed an issue where an error occurred during the creation of the system stored package when applying a patch using the package installer.

-   **module** : qp
-   **Category** : Functional Error
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where an error occurred during the creation of the system stored package when applying a patch using the package installer.
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

### BUG-50164  Fixed an issue where the page lock was not released when the expansion failed due to space exhaustion in a volatile table.

-   **module** : sm

-   **Category** : Hang

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where the page lock was not released when the expansion failed due to space exhaustion in a volatile table.
    
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

### BUG-50174  Removes unused properties -REPLICATION_SERVICE_WAIT_MAX_LIMIT from the altibase.properties.release file.

-   **module** : rp

-   **Category** : Maintainability

-   **Reproducibility** : Always

-   **Description** : Removes unused properties `REPLICATION_SERVICE_WAIT_MAX_LIMIT` from the altibase.properties.release file.
    
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

### BUG-50177 Fixed an issue where replication fails when an undo tablespace becomes full on a disk table that contains a LOB.

-   **module** : rp

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : LOB 로그 처리 중 undo tablespace full이 발생하더라도
    이중화가 정상적으로 동작하도록 수정 합니다.

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

### BUG-50196 Fixed an issue where a sequence created with the NOCYCLE option behaves as CYCLE after executing the `ALTER SEQUENCE` statement and restarting the server.

-   **module** : sm

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where a sequence created with the NOCYCLE option behaves as CYCLE after executing the `ALTER SEQUENCE` statement and restarting the server.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

        create sequence seq2 start with 8 cache 3 maxvalue 10 nocycle;
        SELECT seq2.NEXTVAL FROM dual;
        alter sequence seq2 increment by 3;
        
        server restart
        
        SELECT seq2.NEXTVAL FROM dual;

  -   **Actual Results**

          NEXTVAL
          -----------------------
          4
          1 row selected.

  -   **Expected Results**

          [ERR-11044 : Sequence upper bound exceeded]

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50197 Improved the validation for specifying the LOB tablespace in the memory-partitioned table creation statement.

-   **module** : qp-ddl-dcl-pvo

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Improved the validation for specifying the LOB tablespace in the memory-partitioned table creation statement.
    
-   **How to reproduce this bug**

    -   **Reproduction conditions**

            DROP TABLE T1;
            DROP TABLESPACE MEM_TEST_TBS_0  INCLUDING CONTENTS AND DATAFILES;
            DROP TABLESPACE MEM_TEST_TBS_1  INCLUDING CONTENTS AND DATAFILES;
            DROP TABLESPACE MEM_TEST_TBS_2  INCLUDING CONTENTS AND DATAFILES;
            CREATE MEMORY TABLESPACE MEM_TEST_TBS_0  SIZE 32M AUTOEXTEND ON;
            CREATE MEMORY TABLESPACE MEM_TEST_TBS_1  SIZE 32M AUTOEXTEND ON;
            CREATE MEMORY TABLESPACE MEM_TEST_TBS_2  SIZE 32M AUTOEXTEND ON;
            CREATE TABLE T1 ( I1 INTEGER DEFAULT 1, I2 VARCHAR(4), I3 CLOB )
            PARTITION BY HASH ( I1 )
            ( PARTITION P1 TABLESPACE MEM_TEST_TBS_0 LOB (I3) STORE AS ( TABLESPACE MEM_TEST_TBS_1 ),
              PARTITION P2 TABLESPACE MEM_TEST_TBS_2 LOB (I3) STORE AS ( TABLESPACE MEM_TEST_TBS_1 )
            ) TABLESPACE MEM_TEST_TBS_1;

    -   **Actual Results**

            Create success.

    -   **Expected Results**

            [ERR-31245 : Unable to create a LOB type column with the specified tablespace.]

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
| 7.1.0.8.4        | 6.5.1                   | 8.10.1       | 7.1.7               | 7.4.7                        |

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
