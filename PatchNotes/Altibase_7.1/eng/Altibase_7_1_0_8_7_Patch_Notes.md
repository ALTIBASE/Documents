# Altibase 7.1.0.8.7 Patch Notes

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-48520 Network-related error messages can now be logged in altibase_cm.log

-   **module** : mm

-   **Category** : Functionality

-   **Reproducibility** : Always

-   **Description** : The **NETWORK_ERROR_LOG_FILE** property allows configuring the log file where network-related error messages are recorded. By default, these messages are logged in **altibase_boot.log**. If the property is set to **1**, the messages will be logged in **altibase_cm.log** instead.

-   **How to reproduce this bug**
    -   **Reproduction conditions**
    
    -   **Actual Results**
    
    -   **Expected Results**
    
-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
        -   New
            -   NETWORK\_ERROR\_LOG\_FILE
                -   0: Logs network-related error messages in **altibase_boot.log**
                -   1: Logs network-related error messages in **altibase_cm.log**

    -   Compile Option
    -   Error Code

### BUG-50287 Added a function to wait for a specified time during the execution of `aku -p start`.

-   **module** :

-   **Category** : Enhancement

-   **Reproducibility** : Always

-   **Description** : Added a function for a slave pod to wait for a specified time before changing ADMIN_MODE to 0 after replication, start during the execution of the `aku -p start` command. The wait time can be configured using **AKU_DELAY_START_COMPLETE_TIME**.

-   **How to reproduce this bug**
    -   **Reproduction conditions**
    
    -   **Actual Results**
    
    -   **Expected Results**
    
-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
        -   New
            -   **AKU_DELAY_START_COMPLETE_TIME**
                -   Default value: 0
                -   Description: This property specifies a waiting time (in seconds) during `aku -p start` process on the slave pod, specifically after the data synchronization is completed internally and before changing the Altibase property ADMIN_MODE to 0.
    -   Compile Option
    -   Error Code

### BUG-50293 New property to change the error message to 'Invalid User ID or Password' when attempting to connect with an incorrect user ID or password in iSQL.

-   **module** : ux-isql

-   **Category** : Functionality

-   **Reproducibility** : Always

-   **Description** : In iSQL, when attempting to connect with an incorrect user ID or password, detailed error messages like [ERR-31010 : User not found] or [ERR-4102E : Invalid password] are displayed. However, you can change the error message to [ERR-91149 : Invalid UserID or Password] by configuring with **ISQL_SECURE_LOGIN_MSG**.

    If the [ISQL_SECURE_LOGIN_MSG](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/iSQL User's Manual.md#isql_secure_login_msg) property is set to 1, when the user ID or password is incorrect, the error message **[ERR-91149 : Invalid UserID or Password]** will be shown.

    ```
    export ISQL_SECURE_LOGIN_MSG=1
    ```
    
-   **How to reproduce this bug**

    -   **Reproduction conditions**

    -   **Actual Results**

    -   **Expected Results**

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
        -   New
            -   [ISQL_SECURE_LOGIN_MSG](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/iSQL%20User's%20Manual.md#isql_secure_login_msg)
                -   0 : Display the detailed error messages like **[ERR-31010 : User not found]** or **[ERR-4102E : Invalid password]** are displayed (Default value)
                -   1: Display the error message **[ERR-91149 : Invalid UserID or Password]** 
    -   Compile Option
    -   Error Code

### BUG-50341 Logging queries that cause errors during preparation.

- **module** : qp

- **Category** : Enhancement

- **Reproducibility** : Always

- **Description** : The feature to log queries that result in an error during preparation has been added. When the **QP_MSGLOG_FLAG property** is set to 66, logging will begin

  ```
  alter system set QP_MSGLOG_FLAG = 66;
  ```

-   **How to reproduce this bug**

    -   **Reproduction conditions**

    -   **Actual Results**

    -   **Expected Results**

- **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

Fixed Bugs
==========

### BUG-48092 Fixed Incorrect sequence values after changing CYCLE option and restarting server with negative minvalue or maxvalue.

-   **module** : sm

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where incorrect sequence values are returned after modifying the cycle option and restarting the server when the sequence's minvalue and maxvalue are negative.

- **How to reproduce this bug**

  -   **Reproduction conditions**

          create sequence s2 minvalue -20 maxvalue -1;
          select s2.nextval;
          select s2.nextval;
          alter sequence s2 cycle;
          alter sequence s2 nocycle;
          -- server restart
          select s2.nextval;

  - **Actual Results**

        NEXTVAL
        -----------------------
        -19
        1 row selected.

  -   **Expected Results**

          [ERR-11044 : Sequence upper bound exceeded]

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50069 The message '[ERR-910FB : Connected to idle instance]' is changed to '[Connected to idle instance]' when connecting with isql -sysdba while the server is not running.

-   **module** : ux-isql

-   **Category** : Usability

-   **Reproducibility** : Always

-   **Description** : The message **[ERR-910FB : Connected to idle instance]** is changed to **[Connected to idle instance]** when connecting with isql -sysdba while the server is not running.

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

### BUG-50097  Improved exception handling for using incorrect values with the iloader -direct option.

-   **module** : ux-iloader

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Improved exception handling for using incorrect values with the iloader -direct option. The error message '[ERR-9103B : Invalid option]' will be displayed when an incorrect value is used.

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

### BUG-50304  Fixed an issue where the packet sequence could increase to its maximum value if a session was not terminated for a long time.

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** :  Fixed an issue where the packet sequence could increase to its maximum value if a session was not terminated for a long time, leading to an 'Invalid packet sequence number' error.

    To apply this fix, the Altibase JDBC driver must be patched.

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

### BUG-50309  Modify the max value so that the SORT_AREA_SIZE per build thread does not exceed Unsigned INT MAX.

-   **module** : sm-disk-index

-   **Category** : Other

-   **Reproducibility** : Always

-   **Description** : During disk index build, if the SORT AREA SIZE per build thread exceeds Unsigned INT MAX (4G-1 bytes), the index build will fail.

    Modify the max value to ensure that the SORT AREA SIZE per build thread does not exceed the maximum Unsigned INT MAX.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    alter system set SORT_AREA_SIZE = 21474836480;
    alter system set INDEX_BUILD_THREAD_COUNT = 1;
    create table t (id int) tablespace sys_tbs_disk_data;
    insert into t values (1);
    create index i on t ( id);
    ```

  -   **Actual Results**

          [ERR-41082 : Internal server error (mmcStatement::execute code=0x42000000 )]

  -   **Expected Results**

          Create success.

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
| 7.1.0.8.7        | 6.5.1                   | 8.11.1       | 7.1.7               | 7.4.7                        |

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
