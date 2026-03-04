Altibase 7.1.0.10.7 Patch Notes
===============================

# New Features

### BUG-51902 The new CLI function SQLRowCount2 has been added.

- **module** : ul-odbc
- **Category** : Functional Error
- **Reproducibility** : Always
- **Description** : The new CLI function [SQLRowCount2](https://manual.altibase.com/7.1/en/dev/cli/2.-Altibase-CLI-Functions/SQLRowCount/#sqlrowcount2) has been added to return the number of rows affected by UPDATE, INSERT, or DELETE statements with support for 64-bit row counts.
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

### BUG-51467 Improved to record client information, in addition to the call stack, in `altibase_error.log` when the server terminates abnormally.

-   **module** : mm

-   **Category** : Functionality

-   **Reproducibility** : Always

-   **Description** : Improved to record client information, in addition to the call stack, in `altibase_error.log` when the server terminates abnormally.
    
    - CliPkgVer: Client Version
    
    - CliProtoVer: Client Communication Protocol Version
    
    - CliType: Client Type
    
    - AppInfo: Application Information
    
      ```
      The following information is additionally recorded below the existing call stack information.
      
      BEGIN-DUMP Diagnostic Information ===============
          Statement: 00007F75D24A9808                  
          Session: 000000000A22F148                    
              CliPkgVer: 7.1.0.10.7                     
              CliProtoVer: 7.1.7                       
              CliType: CLI-64LE                        
              AppInfo: isql                                
          Task: 000000000A16EF00                       
          Link: 00007F74E0000990                       
              ConnType: 1                              
      END-DUMP Diagnostic Information =================
      ```
    
-   **How to reproduce this bug**

    -   **Reproduction conditions**

    -   **Actual Results**

    -   **Expected Results**

- **Workaround**

- **Changes**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

### BUG-51540 Fixed Issue in Memory Index Aging

-   **module** : sm

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : An issue where memory index aging could fail under certain conditions when a memory index includes a VARIABLE column has been fixed.

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

### BUG-51864 Altibase Connector for Kafka Provided

-   **module** : rp-kafkaConnector

-   **Category** : Other

-   **Reproducibility** : Always

-   **Description** : The Altibase Connector for Kafka (hereafter Altibase Connector), compatible with the Confluent JDBC connector protocol, has been developed. Using the Altibase Connector, change data from Altibase can be replicated to other databases via Kafka, and change data from other databases can be replicated to Altibase. The Altibase Connector consists of the following two types of connectors:
- **Altibase Source Connector**: Streams Altibase's changed data to Kafka for replication to other databases.
    - **Altibase Sink Connector**: Applies change data received via Kafka from other databases to Altibase and other supported sink databases.

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

### BUG-51880 Internal Logic Improvement for Query Stability (Change in Column Count Management Structure)

-   **module** : qp

-   **Category** : Fatal

-   **Reproducibility** : Unknown

-   **Description** : The column count management structure has been changed to prevent invalid memory references and improve stability.
    
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

# Fixed Bugs

### BUG-51899 The index header address may not be updated when an index is added or dropped.

-   **module** : sm

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : The index header address may not be updated when an index is added or dropped.

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

### BUG-51909 When the server terminates abnormally, client information such as PID, COMMIT MODE, COMM_NAME, and statement details should be additionally recorded in the call stack.

-   **module** : mm

-   **Category** : Other

-   **Reproducibility** : Rare

-   **Description** : To aid in analysis when the server terminates abnormally, client information such as PID, COMMIT MODE, COMM_NAME, and statement details has been added to `altibase_error.log`. This information is recorded below the existing call stack.
    
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
| 7.1.0.10.7       | 6.5.1                   | 8.12.1       | 7.1.7               | 7.4.7                        |

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

No properties added/changed/deleted.

### Performance Views

No performance views added/changed/deleted.
