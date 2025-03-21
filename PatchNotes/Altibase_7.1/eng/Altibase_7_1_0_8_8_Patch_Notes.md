# Altibase 7.1.0.8.8 Patch Notes

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Fixed Bugs
==========

### BUG-46720  Fixed the page allocation failure during LOB index creation when insert LOB data larger than 100MB into a disk table.

-   **module** : sm

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixed an issue that caused page allocation to fail during the LOB INDEX creation process when trying to INSERT more than 100MB of LOB type data into a disk table.

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

### BUG-49885 Modified the remarks column of DatabaseMetaData.getTables() and getColumns() methods to return table and column comments.

-   **module** : mm-jdbc

-   **Category** : Functionality

-   **Reproducibility** : Always

-   **Description** : Modified the remarks column of DatabaseMetaData.getTables() and getColumns() methods to return table and column comments.

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

### BUG-49944 Fixed the issue where DatabaseMetaData.getImportedKeys() and getExportedKeys() returned incorrect DELETE_RULE values.

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed the issue where DatabaseMetaData.getImportedKeys() and getExportedKeys() returned incorrect DELETE_RULE values.
    
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

### BUG-50363 Performance improvement for AltibaseDatabaseMetaData.getProcedureColumns() and getFunctionColumns().

-   **module** : mm-jdbc

-   **Category** : Efficiency

-   **Reproducibility** : Always

-   **Description** : Performance improvement for AltibaseDatabaseMetaData.getProcedureColumns() and getFunctionColumns().

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

### BUG-50187 In an environment where autocommit mode is off, an incorrect query is recorded as the Last Query in the error log when a UTRANS TIMEOUT occurs.

-   **module** : mm

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : In an environment where autocommit mode is off, an incorrect query is recorded as the Last Query in the error log when a UTRANS TIMEOUT occurs.

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

### BUG-50307 Fixed an issue where the server would shut down abnormally when using a record type in the NVL function in PSM.

-   **module** : qp-psm-trigger-pvo

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where the server would shut down abnormally when using a record type in the NVL function in PSM.

- **How to reproduce this bug**

  - **Reproduction conditions**

        CREATE OR REPLACE PROCEDURE PROC1 AS
        TYPE REC_TYPE IS RECORD(C1 INTEGER, C2 INTEGER);
        VAR1 REC_TYPE;
        BEGIN
          VAR1 := NVL(VAR1, VAR1);
        END;
        /
        EXEC PROC1;

  -   **Actual Results**

          [ERR-91015 : Communication failure.]

  -   **Expected Results**

          [ERR-21017 : The argument is not applicable.
        
          In procedure SYS.PROC1
          0005 :   VAR1 := NVL(VAR1, VAR1);
                          ^              ^
          ]

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50312 Improved to log the query in the dump stack after a prepare error occurs and the server shuts down abnormally.

-   **module** : mm

-   **Category** : Functionality

-   **Reproducibility** : Rare

-   **Description** : Fixes an issue where the dump stack is missing query information when a segment fault occurs due to an internally incorrect memory access during prepareProtocol processing.

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

### BUG-50325 Fixes the typo in the error message related to the RECEIVE_ONLY option in replication.

-   **module** : rp

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixes the typo in the error message related to the RECEIVE_ONLY option in replication.

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

### BUG-50343 The server may shut down abnormally  when attempting to delete an invalid page during internal disk index page recycling.

-   **module** : sm-disk-index

-   **Category** : Fatal

-   **Reproducibility** : Rare

-   **Description** : An issue was discovered where an invalid page could be deleted during internal disk index page recycling, and it has been addressed.

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

### BUG-50354 Data inconsistency may occur when running 'aku -p start' on the 3rd or 4th pod.

-   **module** :

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** :  Fixed the data inconsistency issue when running 'aku -p start' on the 3rd or 4th pod.

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

### BUG-50356 Fixed the issue where REP_GAP_SIZE in v$repgap shows incorrect values.

-   **module** : rp

-   **Category** : Functional Error

-   **Reproducibility** : Rare

-   **Description** : Fixed the issue where REP_GAP_SIZE in v$repgap shows incorrect values.

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

### BUG-50381 Fixed the issue where the server crashes when an uninitialized variable is used as an argument for the HASH function in PSM..

-   **module** : qp-dml-execute

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixed the issue where the server crashes when an uninitialized variable is used as an argument for the HASH function in PSM.

- **How to reproduce this bug**

  - **Reproduction conditions**

        CREATE OR REPLACE PROCEDURE proc1
        AS
          v1 integer;
          v2 integer;
        BEGIN
          v2 := HASH(v1);
        END;
        /
        EXEC proc1;

  -   **Actual Results**

          [ERR-91015 : Communication failure.]

  -   **Expected Results**

          [ERR-21010 : Value overflow
          at "SYS.PROC1", line 6]

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
| 7.1.0.8.8        | 6.5.1                   | 8.11.1       | 7.1.7               | 7.4.7                        |

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
