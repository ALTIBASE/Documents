# Altibase 7.1.0.8.6 Patch Notes

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [New Features](#new-features)
    - [BUG-50009 Improved logging in altimon.log when an exception occurs in PICL library. (Linux)](#bug-50009%C2%A0improved-logging-in-altimonlog-when-an-exception-occurs-in-picl-library-linux)
    - [BUG-50259  Modify `aku -p start` to Connect to Altibase in Admin Mode](#bug-50259%C2%A0-modify-aku--p-start-to-connect-to-altibase-in-admin-mode)
    - [BUG-50293 New property to change the error message to 'Invalid User ID or Password' when attempting to connect with an incorrect user ID or password in iSQL.](#bug-50293%C2%A0new-property-to-change-the-error-message-to-invalid-user-id-or-password-when-attempting-to-connect-with-an-incorrect-user-id-or-password-in-isql)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-47333 Fixed an issue where an external procedure could not be executed after a library loading failure.](#bug-47333%C2%A0fixed-an-issue-where-an-external-procedure-could-not-be-executed-after-a-library-loading-failure)
    - [BUG-47812 Fixed a concurrency issue occurring in `ALTER TRIGGER` and `DROP TRIGGER` DDL.](#bug-47812%C2%A0fixed-a-concurrency-issue-occurring-in-alter-trigger-and-drop-trigger-ddl)
    - [BUG-48193 Fixed an issue where the results of `GROUP BY ROLLUP` were incorrect.](#bug-48193%C2%A0fixed-an-issue-where-the-results-of-group-by-rollup-were-incorrect)
    - [BUG-50072 Fixed Potential Issue of Missing Statistics in Memory Management Logic for v$memstat.](#bug-50072%C2%A0fixed-potential-issue-of-missing-statistics-in-memory-management-logic-for-vmemstat)
    - [BUG-50165 Fixed Issue with Reconnection After STF (Session Time Failover) When Loadbalancing is ON.](#bug-50165%C2%A0fixed-issue-with-reconnection-after-stf-session-time-failover-when-loadbalancing-is-on)
    - [BUG-50241 In APRE, if a host variable is placed before the INTO clause, it cannot be bound using a structure array (row-wise binding).](#bug-50241%C2%A0in-apre-if-a-host-variable-is-placed-before-the-into-clause-it-cannot-be-bound-using-a-structure-array-row-wise-binding)
    - [BUG-50264  Fixed an issue where a delay in updating the base time managed by the session manager during server load caused a UTRANS_TIMEOUT.](#bug-50264%C2%A0-fixed-an-issue-where-a-delay-in-updating-the-base-time-managed-by-the-session-manager-during-server-load-caused-a-utrans_timeout)
    - [BUG-50279 Fixed an issue where the server could shut down abnorally when using User Defined Types (UDT) as arguments in the `NULLIF`, `COALESCE`, and `CASE2` functions.](#bug-50279-fixed-an-issue-where-the-server-could-shut-down-abnorally-when-using-user-defined-types-udt-as-arguments-in-the-nullif-coalesce-and-case2-functions)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [Compatibility](#compatibility)
    - [Altibase Server Properties](#altibase-server-properties)
    - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-50009 Improved logging in altimon.log when an exception occurs in PICL library. (Linux)

-   **module** : ux-altiMon

-   **Category** : Usability

-   **Reproducibility** : Always

-   **Description** : Improved logging in altimon.log when an exception occurs in PICL library. This feature is supported only on Linux.
    
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

### BUG-50259  Modify `aku -p start` to Connect to Altibase in Admin Mode

-   **module** :

-   **Category** : Enhancement

-   **Reproducibility** : Always

- **Description** : Admin mode has been added for executing `aku`. Additionally, in the master pod, the logic for performing `truncate`, receiving replication sync from the slave, and resetting replication has been removed.

  - about Admin Mode

    - If `ADMIN_MODE` is set to `0`  in Altibase Server when running `aku -p start`, an error message will be displayed, and the process will terminate.
    - During `aku -p start`, the process will connect to Altibase Server in admin mode to perform `aku` tasks.
    - Upon successful completion of `aku -p start`, `ADMIN_MODE` will be set back to `0` before termination.
    
   - Guide for the Master Pod (`pod-0`)    
  
     * when executing `aku -p start`
  
       In the master pod, the logic for performing `truncate` and receiving replication sync from the slave has been removed.
       
     * when executing `aku -p end`
     
       In the master pod, the replication reset logic has been removed.
     
       Performing a replication reset prevents further data exchange in the replication setup. Previously, after executing `aku -p end` and then `aku -p start`, it was necessary to truncate existing tables and receive replication sync to synchronize data.
     
       However, if the master pod does not perform a replication reset during `aku -p end`, it will continue synchronizing data through replication, eliminating the need for truncation and replication sync.
     
   - Caution
  
     - You must start the Altibase DB after setting ADMIN_MODE = 1 and REMOTE_SYSDBA_ENABLE = 1 in the altibase.properties file.
     - In the event of a master node failure, the user must manually perform truncate and receive replication sync from another pod based on their judgment. (For pods other than the master pod, aku automatically performs truncate and replication sync.)

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

### BUG-50293 New property to change the error message to 'Invalid User ID or Password' when attempting to connect with an incorrect user ID or password in iSQL.

-   **module** : ux-isql

-   **Category** : Functionality

-   **Reproducibility** : Always

- **Description** : In iSQL, when attempting to connect with an incorrect user ID or password, detailed error messages like [ERR-31010 : User not found] or [ERR-4102E : Invalid password] are displayed. However, you can change the error message to [ERR-91149 : Invalid UserID or Password] by configuring with **ISQL_SECURE_LOGIN_MSG**. 

  If the [ISQL_SECURE_LOGIN_MSG](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/iSQL User's Manual.md#isql_secure_login_msg) property is set to 1, when the user ID or password is incorrect, the error message **[ERR-91149 : Invalid UserID or Password]** will be shown.

-   **How to reproduce this bug**
    
    -   **Reproduction conditions**
    
    -   **Actual Results**
    
    -   **Expected Results**
    
-   **Workaround**

-   **Changes**
    -   Performance view
    -   Property
        -   NEW
            -   ISQL_SECURE_LOGIN_MSG
                -   0: Display the detailed error messages like **[ERR-31010 : User not found]** or **[ERR-4102E : Invalid password]** are displayed (Default value)
                -   1: Display the error message **[ERR-91149 : Invalid UserID or Password]** 
    -   Compile Option
    -   Error Code

Fixed Bugs
==========

### BUG-47333 Fixed an issue where an external procedure could not be executed after a library loading failure.

-   **module** : qp-psm-trigger-execute

-   **Category** : Functional Error

-   **Reproducibility** : Always

- **Description** : Fixed an issue where an external procedure could not be executed after a library loading failure, even if the cause of the failure was resolved.

  Previously, if this issue occurred, the problem could be resolved by reconnecting the client. With this patch, the issue can now be resolved without requiring a client reconnection.

- **How to reproduce this bug**

  -   **Reproduction conditions**

          CREATE LIBRARY LIB1 AS 'andy_upper.so';
          CREATE PROCEDURE PROC1 ( istr in varchar(100), ostr out varchar(100) ) AS
          LANGUAGE C
          LIBRARY LIB1 NAME "andy_upper";
          /
          VAR VAR1 VARCHAR(100);
          VAR VAR2 VARCHAR(100);
          EXEC :VAR1 := 'aaaa';
          EXEC PROC1(:VAR1, :VAR2);
          CREATE OR REPLACE LIBRARY LIB1 AS 'invalid_library_name.so';
          EXEC PROC1(:VAR1, :VAR2);
          CREATE OR REPLACE LIBRARY LIB1 AS 'andy_upper.so';
          EXEC PROC1(:VAR1, :VAR2);

  - **Actual Results**

        iSQL> CREATE OR REPLACE LIBRARY LIB1 AS 'invalid_library_name.so'; //오류를 발생시키는 라이브러리로 변경
        Create success.
        iSQL> EXEC PROC1(:VAR1, :VAR2);
        [ERR-0109F : Library file for external procedure/function not found : ......./lib/invalid_library_name.so]
        
        iSQL> CREATE OR REPLACE LIBRARY LIB1 AS 'andy_upper.so'; //오류를 제거하여 정상동작하도록 수정
        Create success.
        iSQL> EXEC PROC1(:VAR1, :VAR2);
        [ERR-010A0 : Function for external procedure/function not found]

  -   **Expected Results**

          iSQL> CREATE OR REPLACE LIBRARY LIB1 AS 'invalid_library_name.so';//오류를 발생시키는 라이브러리로 변경
          Create success.
          iSQL> EXEC PROC1(:VAR1, :VAR2);
          [ERR-0109F : Library file for external procedure/function not found : ......./lib/invalid_library_name.so]
            
          iSQL> CREATE OR REPLACE LIBRARY LIB1 AS 'andy_upper.so'; //오류를 제거하여 정상동작하도록 수정
          Create success.
          iSQL> EXEC PROC1(:VAR1, :VAR2);
          Execute success.

-   **Workaround**

        Client 접속을 해제하고, 다시 접속한다.

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47812 Fixed a concurrency issue occurring in `ALTER TRIGGER` and `DROP TRIGGER` DDL.

-   **module** : qp-psm-trigger-execute

-   **Category** : Fatal

-   **Reproducibility** : Frequence

-   **Description** : Fixed a concurrency issue occurring in `ALTER TRIGGER` and `DROP TRIGGER` DDL.
    
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

### BUG-48193 Fixed an issue where the results of `GROUP BY ROLLUP` were incorrect.

-   **module** : qp-select-pvo

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where the results of `GROUP BY ROLLUP` were incorrect.

- **How to reproduce this bug**

  -   **Reproduction conditions**

          DROP TABLE T1;
          DROP TABLE T2;
          CREATE TABLE T1 (I1 INT, I2 INT, I3 INT, I4 INT);
          CREATE TABLE T2 ( I1 INT);
          INSERT INTO T1 VALUES( 1,1,1,3);
          INSERT INTO T1 VALUES( 2,2,2,4);
          INSERT INTO T2 VALUES(1);
          SELECT I1, MAX(I4), (SELECT MIN(I1) FROM T2 WHERE I1 = T1.I1) AS SUB FROM T1 GROUP BY ROLLUP(I1);

  - **Actual Results**

        I1          MAX(I4)     SUB
        ----------------------------------------
        1           3           1
        2           4           1
                    4           1
        3 rows selected.

  -   **Expected Results**

          I1          MAX(I4)     SUB
          ----------------------------------------
          1           3           1
          2           4
                      4
          3 rows selected.

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50072 Fixed Potential Issue of Missing Statistics in Memory Management Logic for v$memstat.

-   **module** : id

-   **Category** : Maintainability

-   **Reproducibility** : Unknown

- **Description** : An issue was identified in the memory management logic related to `v$memstat`, where some statistical information could be missing due to a potential flaw in the code. This has been fixed to prevent such missing statistics.

  Additionally, if any statistics are still missing, a log will now be recorded in the `altibase_boot.log` file to assist with troubleshooting.

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

### BUG-50165 Fixed Issue with Reconnection After STF (Session Time Failover) When Loadbalancing is ON.

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : An issue was identified where, when Loadbalancing is ON and STF (Session Time Failover) occurs, the system attempts to reconnect to the default server instead of the server accessed before the STF event. This issue has been resolved, and the behavior has been modified as follows:

    -   When Loadbalancing is ON, the server that is initially connected to is randomly selected between the default server and the alternate server. In the event of STF, the system will first attempt to reconnect to the previously accessed server. If this fails, it will then attempt a random server connection.

    -   When Loadbalancing is OFF, the system will first attempt to connect to the default server. If the connection fails, it will attempt to connect sequentially to the servers specified as AlternateServers. In the event of STF, the system will first try to reconnect to the previously accessed server. If this fails, it will then attempt the connection sequentially.

- **How to reproduce this bug**

  - **Reproduction conditions**

        loadbalance=on, sessionfailover=on
        Primary Server - A
        AlternateServers  - ( B, C, D )
        1. Connect ==> C is selected randomly.
        2. Prepare ==> STF occurs on server C.

  -   **Actual Results**

          Attempt to connect to server A -> Then attempt to connect to the remaining servers randomly.

  -   **Expected Results**

          Attempt to connect to server C -> Then attempt to connect to the remaining servers randomly.

- **Workaround**

- **Changes**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

### BUG-50241 In APRE, if a host variable is placed before the INTO clause, it cannot be bound using a structure array (row-wise binding).

-   **module** : mm-apre

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where row-wise binding did not work correctly when a structure array host variable was not the first host variable in the SQL statement.
    
- **How to reproduce this bug**

  -   **Reproduction conditions**

  - **Actual Results**
  
  -   **Expected Results**
  
-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50264  Fixed an issue where a delay in updating the base time managed by the session manager during server load caused a UTRANS_TIMEOUT.

기준시간을 관리하는 세션 관리자에서

-   **module** : mm
-   **Category** : Functional Error
-   **Reproducibility** : Frequence
-   **Description** : Fixed an issue where a delay in updating the base time managed by the session manager during server load caused a UTRANS_TIMEOUT.
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

### BUG-50279 Fixed an issue where the server could shut down abnorally when using User Defined Types (UDT) as arguments in the `NULLIF`, `COALESCE`, and `CASE2` functions.

-   **module** : mt-function

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where the server could shut down abnorally when using User Defined Types (UDT) as arguments in the `NULLIF`, `COALESCE`, and `CASE2` functions.

- **How to reproduce this bug**

  -   **Reproduction conditions**

          create or replace procedure proc1
          as
           type aa_type is table of integer;
           var1 aa_type;
           var2 varchar(128);
          begin
            var1 := nullif(var1, var1);
          end;
          /
          exec proc1;

  - **Actual Results**

        [ERR-91015 : Communication failure.]

  -   **Expected Results**

          [ERR-2100C : Conversion not applicable.
          In PROC1
          0007 :   var1 := nullif(var1, var1);
                          ^            ^
          ]

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
| 7.1.0.8.6        | 6.5.1                   | 8.11.1       | 7.1.7               | 7.4.7                        |

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
