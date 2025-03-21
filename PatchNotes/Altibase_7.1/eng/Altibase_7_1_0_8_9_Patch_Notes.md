# Altibase 7.1.0.8.9 Patch Notes

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-50412  Log level improvement related to the unsupported property warning message in altibase_mm.log.

### Modification of MM_MSGLOG_FLAG related to warning message in altibase_mm.log.

-   **module** : mm

-   **Category** : Usability

-   **Reproducibility** : Always

-   **Description** : The default value of MM_MSGLOG_FLAG was changed to 1 from 0, in order to  control the unsupported property warning message in altibase_mm.log.
    
-   #### How to reproduce this bug

    -   **Reproduction conditions**

    -   **Actual Results**

    -   **Expected Results**

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
        -   change of MM\_MSGLOG\_FLAG
            -   default value: 0-> 1
        
    -   Compile Option
    -   Error Code

Fixed Bugs
==========

### BUG-49999 Fixed an issue where a transaction waits when DELETE and DEQUEUE are performed on the same record of the queue table simultaneously.

-   **module** : sm

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixes the issue where the queue waits for a record lock. This issue was reproducible in Altibase 7.1.0.6.0 and later versions. After applying this patch, the issue will no longer occur.
    
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

### BUG-50391 Removing 'PUBLIC ROLE' is not allowed.

-   **module** : qp
-   **Category** : Functional Error
-   **Reproducibility** : Always
-   **Description** : Fixes the issue where the PUBLIC ROLE could be removed using the `DROP ROLE PUBLIC;` statement. Now, if a user attempts to remove it by mistake, an error message will be displayed indicating that the removal is not allowed.
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
        -   New
            - [ERR-314B6 : It is forbidden to drop the PUBLIC role.]
              - Cause: You cannot drop the PUBLIC role.
              - Action: Don't try dropping the PUBLIC role.

### BUG-50402 Fixed an installation issue that occurs when using the installer if the shell is not bash.

-   **module** : installer

-   **Category** : Maintainability

-   **Reproducibility** : Rare

-   **Description** : Fixed an installation issue that occurs when using the installer in an environment that is not a bash shell.

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

### BUG-50406  There is an issue where altimon fails to run on HP-UX and AIX

-   **module** : ux-altiMon

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where altimon fails to run on HP-UX and AIX due to BUG-50009. This issue started occurring from version 7.1.0.8.6, and will not occur in the 7.1.0.8.9 patch that includes the fix for this bug.

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

### BUG-50422 Fixed the typo in the AKU_SYS_PASSWORD property within the aku.conf.

-   **module** :

-   **Category** : Maintainability

-   **Reproducibility** : Always

-   **Description** : Fixed the typo in the properties within the aku.conf file.

     Before : AKU\_SYS\_**PASW**WORD

     After : AKU\_SYS\_**PASS**WORD

-   #### How to reproduce this bug

    -   **Reproduction conditions**

    -   **Actual Results**

    -   **Expected Results**

-   **Workaround**

-   #### Changes

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code
    

### BUG-50451  The server shut down abnormal when an alias used in the ORDER BY clause and in the ROW_NUMBER function in the SELECT clause.

-   **module** : qp

-   **Category** : Fatal

-   **Reproducibility** : Always

- **Description** :  Fixed an abnormal termination when executing a query that satisfies all of the following conditions:

  -   When the column used for PARTITION BY or ORDER BY in the OVER clause was used for GROUP BY.

  -   When the column used for PARTITION BY or ORDER BY in the OVER clause is used as an argument of the function in the TARGET clause.

  -   The column used as an argument to a function in the TARGET clause is specified as an ALIAS of that function (if the argument and ALIAS of the function in the TARGET clause are the same).

  -   If the alias of the function in the TARGET clause is used in ORDER BY.

- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    DROP TABLE T1;
    CREATE TABLE T1 ( I1 VARCHAR(30),I2 VARCHAR(30), I3 VARCHAR(30) );
    CREATE FUNCTION FUNC1( V1 INTEGER )
       RETURN INTEGER
       AS
       BEGIN
         RETURN V1;
       END;
       /
    
    SELECT ROW_NUMBER() OVER(PARTITION BY I1 ORDER BY I2 ASC) AS AA
                ,FUNC1(I1) AS I1
                ,FUNC1(I2) AS I2
                FROM T1
                GROUP BY I1, I2
                ORDER BY AA;
    ```
    
  - **Actual Results**

    ```sql
    [ERR-31455 : Failed to work because an internal exception occurred
     from an OS.[Contact Altibase's Support Center]]
    ```

  -   **Expected Results**

      ```sql
      No rows selected.
      ```

- **Workaround**

  This issue can be avoided by changing the alias of the function in the target clause as shown below.

  ```sql
  SELECT ROW_NUMBER() OVER(PARTITION BY I1 ORDER BY I2 ASC) AS AA
              ,FUNC1(I1) AS I1a
              ,FUNC1(I2) AS I2b
              FROM T1
              GROUP BY I1, I2
              ORDER BY AA;
  ```

- **Changes**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

### BUG-50453 Fixed an issue in the LB trace log message.

-   **module** : mm

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an issue in the LB trace log message where the number of newly created service threads was displayed instead of the number of currently active service threads when indicating that the service thread count exceeds MULTIPLEXING_MAX_THREAD_COUNT.

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

Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 7.1.0.8.9        | 6.5.1                   | 8.11.1       | 7.1.7               | 7.4.7                        |

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
