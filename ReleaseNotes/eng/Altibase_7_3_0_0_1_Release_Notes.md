<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Altibase 7.3.0.0.1 Release Notes](#altibase-73001-release-notes)
  - [1. System Requirements](#1-system-requirements)
    - [Minimum Hardware Requirements](#minimum-hardware-requirements)
    - [Operating Systems and Platforms](#operating-systems-and-platforms)
  - [2. Release Notes](#2-release-notes)
    - [2.1 New Features](#21-new-features)
      - [2.1.1 AKU](#211-aku)
      - [2.1.2 AltiShapeLoader 1.0](#212-altishapeloader-10)
      - [2.1.3 Partial Support for JDBC 4.2](#213-partial-support-for-jdbc-42)
      - [2.1.4 OpenSSL 3.0.8 Support](#214-openssl-308-support)
      - [2.1.5 Functionality Improvement - SQL Extension](#215-functionality-improvement---sql-extension)
      - [2.1.6 Functionality Improvement - Spatial SQL](#216-functionality-improvement---spatial-sql)
      - [2.1.7 Functionality Improvement - Replication](#217-functionality-improvement---replication)
      - [2.1.8  Functionality Improvement - Application Development Interface](#218--functionality-improvement---application-development-interface)
      - [2.1.9 Functionality Improvement - Stored Procedures](#219-functionality-improvement---stored-procedures)
      - [2.1.10 Functionality Improvement - Utilities](#2110-functionality-improvement---utilities)
      - [2.1.11 Functionality Improvement - JDBC Adapter, oraAdpater](#2111-functionality-improvement---jdbc-adapter-oraadpater)
      - [2.1.12 Performance Improvement](#2112-performance-improvement)
      - [2.1.13 High Availability](#2113-high-availability)
      - [2.1.14 DBeaver Package](#2114-dbeaver-package)
    - [2.2 Changes](#22-changes)
      - [2.2.1 Database Version](#221-database-version)
      - [2.2.2 Compatibility](#222-compatibility)
      - [2.2.3 Others](#223-others)
      - [2.2.4 Properties](#224-properties)
      - [2.2.5 Meta Tables](#225-meta-tables)
      - [2.2.6 Performance Views](#226-performance-views)
    - [2.3 Packages](#23-packages)
    - [2.4 Download](#24-download)
      - [Package](#package)
      - [Manual](#manual)
      - [Installation](#installation)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

</br>

</br>

</br>

Altibase 7.3.0.0.1 Release Notes
===============================

**(2023.08)** </br>



## 1. System Requirements

### Minimum Hardware Requirements

* 1GB RAM (Recommended: 2GB)
* 1 CPU (Recommended: 2 CPUs)
* 4 GB free hard disk space (Recommended: 12 GB)



### Operating Systems and Platforms

Altibase 7.3.0.0.1 can be run on the operating systems and platforms listed in the table below.


|                                                              | Altibase Server | Altibase Client | Software requirements   |
| ------------------------------------------------------------ | :-------------: | :-------------: | :---------------------- |
| **AIX on IBM Power Systems**                                 |                 |                 |                         |
| AIX 6.1                                                      |        ●        |        ●        |                         |
| **Linux x86-64**                                             |                 |                 |                         |
| Red Hat Enterprise Linux 6<br/>Red Hat Enterprise Linux 7<br/>Red Hat Enterprise Linux 8 |        ●        |        ●        | - GNU glibc 2.12 ~ 2.33 |
| **Linux on Power**                                           |                 |                 |                         |
| Red Hat Enterprise Linux 6.5 and higher                      |        ●        |        ●        | - GNU glibc 2.12 ~ 2.33 |
| **Linux on Power** **(Little Endian)**                       |                 |                 |                         |
| Red Hat Enterprise Linux 7.3 and higher                      |        ●        |        ●        | - GNU glibc 2.17 ~ 2.33 |
| **HP-UX Itanium (IA-64)**                                    |                 |                 |                         |
| HP-UX 11.31                                                  |        ●        |        ●        |                         |

> Altibase 7.3 server and client both support 64-bit only.
>
> Altibase 7.3 is compatible with minor versions of Red Hat Enterprise Linux 6, 7, and 8.
>
> Altibase 7.3 is compatible with JDK 1.8 and higher.

<br/><br/>

## 2. Release Notes

### 2.1 New Features

#### 2.1.1 AKU

Altibase Kubernetes Utility(AKU) is a utility that helps with synchronizing data or resetting synchronization information when Pods start or terminate in a Statefulset in Kubernetes.

#### 2.1.2 AltiShapeLoader 1.0

altiShapeLoader is a tool used to import and export shapefile<sup id="shapefile1">[[1]](#shapefile)</sup>,  which is programmed based on GeoTools, an open-source library based on Java.

#### 2.1.3 Partial Support for JDBC 4.2

Altibase 7.3 provides partial support for JDBC API Specification 4.2. For more detailed information about the JDBC 4.2 API supported by the Altibase 7.3 JDBC driver, please refer to [**JDBC User's Manual** - JDBC 4.2 API References](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/JDBC%20User's%20Manual.md#6-jdbc-42-api-references). Additionally, for information on the changes and compatibility issues, please refer to [Changes and Compatibility Issues with Altibase 7.3 JDBC Driver]() section in this manual.

#### 2.1.4 OpenSSL 3.0.8 Support

To enhance security, Altibase 7.3 supports the latest version of OpenSSL 3.0.8, and no longer provides support for OpenSSL versions 1.0.x. Altibase now extends its protocol support to include TLS 1.3, in addition to TLS 1.0 and 1.2. If users want to specify particular cipher algorithms for TLS 1.3, please set them in the server property, SSL_CIPHER_SUITES. For more detailed information, please refer to [**Altibase SSL TLS User's Guide** - server properties to connect over ssl](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/Altibase%20SSL%20TLS%20User's%20Guide.md#step-2-set-server-properties-to-connect-over-ssl).

Additionally, Altibase supports the Federal Information Processing Standards(FIPS) module. To use the FIPS module with SSL, users must set the SSL_LOAD_CONFIG property to 1. Refer to [Altibase SSL TLS User's Guide - Step4. FIPS module with SSL]().

</br>

#### 2.1.5 Functionality Improvement - SQL Extension

##### VARRAY TYPE

Within stored procedures, the VARRAY type is now supported as a new user-defined type. The VARRAY type is capable of storing a sequence of data with the same data type. For more details, please refer to [Stored Procedures Manual - VARRAY]().

##### Anonymous Block 

An anonymous block is a form of a stored procedure composed of a body block without a header, declared with a structure like DECLARE...BEGIN...END;. Anonymous blocks do not create Persistent Stored Module(PSM) objects, are not stored in the database, and do not return a value in the RETURN clause. Unlike stored procedures, anonymous blocks allow the use of INPUT, OUTPUT, and INOUT bind variables.

##### Internal Mode in C/C++ External Procedure

The internal mode procedure operates faster compared to the external mode by directly loading dynamic libraries and invoking external procedures from the Altibase server without agent processes, resulting in improved efficiency. For more details, refer to [**External Procedures Manual**](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/External%20Procedures%20Manual.md).

##### Multiple Delete, Update

Provides support for multiple delete and multiple update statements. Refer to [**SQL Reference Manual** - multiple_delete](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/SQL%20Reference.md#multiple_delete), [multiple_update](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/SQL%20Reference.md#multiple_update).

##### Regular Expression for Korean Searching

To support searching a regular expression in Korean,  Altibase provides PCRE2 compatibility mode. The PCRE2 compatibility mode supports the regular expression syntax of the PCRE2 library. Please refer to [**SQL Reference Manual**](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/SQL%20Reference.md) for more information.

##### Fetch Across Rollback

To address the issue of 'Fetch out of sequence' error occurring during rollback using CURSOR HOLD ON, now Altibase provides the 'fetch across rollback' feature.

##### Improved Queue Functionality With Delete Statement Control

Queue functionality has been enhanced to allow the use of DELETE statements. Additionally, new 'DELETE ON' and 'DELETE OFF' clauses have been introduced to control the execution of DELETE statements within queues. Refer to [**SQL Reference Manual**](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/SQL%20Reference.md) for more information. Plus, Altibase 7.3 provides V$QUEUE_DELETE_OFF performance view.

##### Sequence Restart Statement

Altibase 7.3 supports the restart_clause with ALTER SEQUENCE statement. Refer to [**SQL Reference Manual** - restart_clause](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/SQL%20Reference.md#restart_clause).

</br>

#### 2.1.6 Functionality Improvement - Spatial SQL

##### SRID Interface

A Spatial Reference Identifier(SRID) is an identifier used to distinguish spatial objects, represented by an integer within a 4-byte range, and can be applied to GEOMETRY columns. Users can specify the SRID when creating a table and also alter the SRID using the ALTER TABLE statement.

New ways to represent GEOMETRY data types:

- Extended Well-Known Text (EWKT) format: It includes SRID information in the WKT format to represent spatial objects.
- Extended Well-Known Binary (EWKB) format: It includes SRID information in the WKB format to represent spatial objects.

##### Spatial Functions

New functions have been introduced as follows.

* ASEWKT
* ASEWKB
* GEOMFROMEWKT
* GEOMFROMEWKB
* SETSRID
* SRID
* ST_Collect
* ST_IsCollection
* ST_LinestringFromWKB
* ST_MakeEnvelope
* ST_MakeLine
* ST_MakePoint
* ST_Point
* ST_PolygonFromText
* ST_Transform

##### Spatial Object Creation Functions

A new function has been introduced as follows.

* ACSGetGeometrySRID

#### 2.1.7 Functionality Improvement - Replication

##### DDL Synchronization

DDL Synchronization is now possible through replication. To use this feature, users must set the REPLICATION_DDL_SYNC and REPLICATION_DDL_ENABLE properties on each node to 1. Also, the REPLICATION_DDL_ENABLE_LEVEL property of each node must be set the same.

To use DDL Synchronization, the following constraints must be verified:

- Replication must be operational on the nodes where DDL Synchronization is performed.
- The table names on both local and remote nodes for DDL Synchronization must match.
- The table partition names on both local and remote nodes for DDL Synchronization must match.
- The owner names of tables on both local and remote nodes for DDL Synchronization must match.
- Only one node can perform DDL Synchronization at a time.
- The values of the REPLICATION_DDL_ENABLE and REPLICATION_DDL_ENABLE_LEVEL properties must be identical for each node.
- The Altibase Server version(5 digits) must be the same.
- DDL Synchronization is not permitted when using the Propagation option.

#####  RECEIVE_ONLY Option

A new option, RECEIVE_ONLY, has been introduced to prevent the transmission of transaction logs for changing data to other nodes. If users create a replication with the RECEIVE_ONLY option on the remote server, the local server does not read the transaction logs of the remote server. Therefore, any replication issues such as network failures do not affect the local server system.

#### 2.1.8  Functionality Improvement - Application Development Interface

##### InfiniBand Support

Altibase 7.3 supports Infiniband, which is based on Remote Direct Memory Access (RDMA) communication for high-speed data communication.

##### New Features on JDBC Driver

- **Auto-Loading of JDBC Driver Class**

  Automatic driver loading using the META-INF/services/java.sql.Driver file without loading of the Class.forName() class explicitly.

- **Wrapper Pattern Support**

  Altibase 7.3 supports the JDBC 4.0 standard interface for obtaining references to implementation objects from proxies. This allows obtaining JDBC objects from proxy objects created in the Connection Pool, etc.

  ```java
  try (Connection sWrappedCon = dbPool.getConnection()) {
      if (sWrappedCon.isWrapperFor(AltibaseConnection.class)) {
          AltibaseConnection connection = sWrappedCon.unwrap(AltibaseConnection.class);
          ...
          ...
  }
  ```

- **National Character Set Support**

  Altibase 7.3 supports the standard multilingual processing interface in the JDBC 4.0 specification.

- **Aborting Connections**

  Altibase 7.3 supports the Connection.abort() interface for asynchronously terminating the physical connection to the database.

- **Standard Socket Network Timeout API Support**

  Altibase 7.3 supports the standard interface Connection.setNetworkTimeout() to set the socket response wait time from the database server.

- **Connection Management Enhancements**

  Altibase 7.3 supports Connection.isValid() to perform validation on Connection objects without a Validation Query

- **Large Update Counts Support**

  Altibase 7.3 supports executeLargeUpdate() and executeLargeBatch() for updating large numbers of records

- **Set Client Information Support**

  Altibase 7.3 supports configuring client application attributes (name) using Connection.setClientInfo()

- **java.sql.SQLType Interface Support**

  Altibase 7.3 supports AltibaseJDBCType, which implements the JDBC 4.2 standard interface java.sql.SQLType. 

- **Automatic JDBC Resource Release Using the Try-With-Resources Statement**

  ```java
  try (Statement stmt = con.createStatement()) {
        ResultSet rs = stmt.executeQuery(query);
        while (rs.next()) {
          String coffeeName = rs.getString("aaa");
          int supplierID = rs.getInt("bbb");
        }
      }
  }
  ```

- **Enhanced For-Each Loop With SQLException**

  ```java
  catch(SQLException ex) {
       for(Throwable e : ex ) {
          LOG.error("Error occurred: " + e);
       }
  }
  ```

</br>

#### 2.1.9 Functionality Improvement - Stored Procedures

##### DBMS_STANDARD Package

DBMS_STANDARD package offers a function for checking trigger events.

##### DBMS_METADATA Package

DBMS_METADATA package offers functions to export object creation DDL statements and GRANT statements from the database dictionary.

##### DBMS_SQL_PLAN_CACHE Package

DBMS_SQL_PLAN_CACHE package provides a stored procedure that functions to keep or delete a specific Execution Plan in the SQL Plan Cache.

##### Add print_enable/print_disable Procedures to DBMS_OUTPUT Package

DBMS_OUTPUT package now includes print_enable/print_disable procedures which offer the functionality to enable or disable the 'println' function within the PSM. These procedures are executed on a per-session basis.

##### Add sleep2 Procedure to the DBMS_LOCK Package

DBMS_LOCK package now includes the sleep2 procedure to support microsecond sleep.

##### SYS_SPATIAL Package

SYS_SPATIAL package provides the function to register and delete Spatial Reference System metadata in the SPATIAL_REF_SYS table.

</br>

#### 2.1.10 Functionality Improvement - Utilities

##### Added Platforms for Altimon: AIX 7 and Power Linux LE(Little Endian)

Now Altimon is available on AIX 7 and Power Linux LE(Little Endian).

##### Added AltiComp Commit Count Configuration Feature

The new property, COUNT_TO_COMMIT has been added to enable the configuration of commit counts. Refer to Utilities Manual.

</br>

#### 2.1.11 Functionality Improvement - JDBC Adapter, oraAdpater

##### Support for LOB Data Types

A new property, ADAPTER_LOB_TYPE_SUPPORT, has been introduced to enable LOB data type support. To enable LOB data type support feature, set the value of ADAPTER_LOB_TYPE_SUPPORT property to 1 and then restart the adapter.

##### Offline Option

Offline option is a feature used with adapters (JDBC Adapter, oraAdapter) to handle the event of a failure in the Altibase server when applying changes from Altibase to the target database. Refer to [**Adapter for JDBC User's Manual** - Offline Option](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_trunk/eng/Adapter%20for%20JDBC%20User's%20Manual.md) or [**Adapter for Oracle User's Manual** - Offline Option](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_trunk/eng/Adapter%20for%20Oracle%20User's%20Manual.md).

</br>

#### 2.1.12 Performance Improvement

##### Improvement in TABLE LOCK Bottlenecks

The LOCK_MGR_TYPE property, previously used for specifying the TABLE LOCK manager type, has been removed. In its place, a new TABLE LOCK mode called 'light mutex mode' has been introduced to enhance performance and address TABLE LOCK bottlenecks.

##### Improvement in Tablespace Manager Mutex Bottlenecks

Altibase 7.3 features an improved TABLESPACE MANAGER MUTEX, achieved by eliminating unnecessary LOCKs.

##### Improved Disk Temporary Table Performance

Altibase 7.3 improves the performance of SQLs using disk temporary tables, resulting in reduced memory usage.

##### Enhanced Transaction Log Recording Performance

In Altibase 7.3, the log compression algorithm has been changed to the LZ4 for faster compression speed.

##### OLTP Scalability

- Enhanced transaction performance on Linux x86-64 with 24+ CPU cores
- Improved logging structure for memory database deletion (DELETE) transactions
- Enhanced In-Place MVCC operation for disk database alterations
- Elimination of unnecessary transaction logging during INSERT/UPDATE transactions
- Improved memory allocation/deallocation bottlenecks during transaction log file compression
- Enhanced commit and garbage collection thread bottlenecks
- Improved transaction performance on memory databases
  - Eliminated bottlenecks in functions that trigger disk reads
  - Group Commit Log

##### Index Performance Improvement

* Reduced time and memory usage for POINTER BASE index creation during server startup.
* Reduced time and memory usage for VALUE BASE index creation during server startup.

##### Database Startup

Improved management of threads used for index building during server startup.

##### Improvement in Transaction Performance for Volatile and Non-Volatile Memory Table

Improved volatile/non-volatile memory table transaction performance by simplifying the memory table object identifier tracking steps.

##### DEQUEUE in Parallel

Eliminated bottlenecks that occur during parallel DEQUEUE operations.

##### Reduction in Prepare Time for CSE

Common Subexpression Elimination(CSE) is an optimization feature that identifies and removes redundant conditional expressions in query conditions. In Altibase 7.3, the CSE execution algorithm and performance of related queries have been improved.

##### Simple Query Optimization on Memory Partitioned Tables

Previously, simple query optimization was only supported for memory tables. But now it extends support to memory partitioned tables and enhanced DML performance of memory partitioned tables.

##### SERIAL FILTER EXECUTE

The performance of performing row filters has been improved by serializing the Filter operator and optimizing the function call structure. The SERIAL_FILTER hint and SERIAL_EXECUTE_MODE properties have been added to enable this feature. Users can see FILTER SERIAL EXECUTE in the execution plan. Through this value, users can confirm Serial Filter Enable.

##### Performance Enhancement for Scalar Subqueries

Altibase 7.3 supports improved optimization of the execution of scalar subqueries. 

##### Performance Enhancement in the FOR Loop Clause of PSM

##### Performance Enhancement in Replication Sender

- The functionality to decompress only logs required for replication in compressed logs has been added.
- The xLog compression algorithm has been changed from LZO to LZ4.

##### Performance Enhancement for Migration

The performance of data insertion for large data migrations has been improved. A new option, -lightmode, has been introduced of iloader. Refer to [**iLoader User's Manual**](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_trunk/eng/iLoader%20User's%20Manual.md).

##### JDBC Fetch Performance

To enhance JDBC fetch performance, ResultSet objects are now reused. When multiple ResultSet objects are created from the same PreparedStatement object, the first ResultSet object is reused. Users can set the reuse_resultset property of the JDBC connection attribute to false when they do not want to reuse ResultSet objects.

</br>

#### 2.1.13 High Availability

##### Enhanced DDL PVO Stability

Altibase 7.3 offers improved reliability by strengthening exception handling in the DDL PVO phase.

##### Improved Protocol Validation

Altibase 7.3 has been Improved to prevent abnormal server termination and behavior caused by the transmission of invalid packets(malformed packets). Packet validity is now checked during protocol processing, and in cases of abnormalities, the client's connection is terminated, and diagnostic logs are generated. To enable this feature, the default value of CM_MSGLOG_FLAG has been set to 3, and the default value of SERVER_MSGLOG_FLAG has been changed to 15.

##### Enhanced Transaction Stability - Multiple Rollback Segment

The maximum number of concurrent transactions for the disk table that can be executed simultaneously has been expanded from the previous 512 to 16,384

##### Improved Undo Tablespace Reusability

To enhance the stability of Undo tablespace reuse, unnecessary associations between the undo tablespace and disk indexes have been removed, thereby eliminating potential bug-related risks. Additionally, the default and maximum values of related properties have been changed to improve disk page space efficiency.

- INDEX_INITTRANS maximum value has been increased from 30 to 50.
- Default and maximum values for INDEX_MAXTRANS have been changed from 30 to 50.

#### 2.1.14 DBeaver Package

Altibase 7.3 provides a package for DBeaver on Windows.

</br>

### 2.2 Changes

The following describes the features that DBAs and developers need to be aware of, which include additions, modifications, and removals.

#### 2.2.1 Database Version

Version by Database Component

| Altibase Server/Client Version | Database Binary Version | Meta Version | Communication Protocol Version | Replication Protocol Version |
| :----------------------------: | :---------------------: | :----------: | :----------------------------: | :--------------------------: |
|           7.1.0.8.8            |          6.5.1          |    8.11.1    |             7.1.7              |            7.4.7             |
|           7.3.0.0.1            |          7.3.0          |    9.3.1     |             7.1.8              |            7.4.9             |

#### 2.2.2 Compatibility

##### Database Binary Version

The database binary version indicates the compatibility between database image files and log files.

The updated database binary version of Altibase 7.3 is not compatible with the lower version anymore because the logging structure of log files has changed. Therefore, **if users want to upgrade the existing Altibase version to Altibase 7.3, migration tasks are required.**

##### Meta Version

Given that the major version of Meta has changed, **it is necessary to reconfigure the metadata when upgrading from the earlier version to Altibase 7.3**.

##### Communication Protocol Version

The patch version of the communication protocol version has been changed. Altibase 7.3 ensures client backward compatibility only if the versions of major and minor are identical.

> Client backward compatibility ensures that user applications developed using an older version of the Altibase library work well when connected to a newer version of Altibase.

##### Replication Protocol Version

The replication protocol version indicates the compatibility of replication.

Altibase 7.3 guarantees replication backward compatibility in LAZY mode because there are no changes in the major and minor versions of the replication protocol. However, it does not guarantee compatibility with replication additional features including EAGER mode, because the patch version of the replication protocol has been changed.

> ###### Altibase Replication Backward Compatibility
>
> Only LAZY mode replication guarantees backward compatibility.
>
> EAGER mode replication, DDL synchronization and Offline Replication do not guarantee backward compatibility since they require the same replication protocol version.

</br>

#### 2.2.3 Others

##### aexport

To run Altibase 7.3 aexport, users must install the DBMS_METADATA package. Otherwise, the following error message will be displayed.

```
[ERR-91144 : DBMS_METADATA package does not exist.]
```

##### Changes and Compatibility Issues With Altibase 7.3 JDBC Driver

The Altibase 7.3 JDBC driver guarantees backward compatibility, but for some interfaces, the behavior has changed according to JDBC API Specification 4.2.

###### SQLFeatureNotSupportedException

The exception handling class for the following interfaces has been changed from SQLException to SQLFeatureNotSupportedException. SQLFeatureNotSupportedException is a subclass of SQLException, so existing user programs will continue to work without modification.

- Altibase.jdbc.driver.AltibaseConnection
  - setTypeMap(Map)
- Altibase.jdbc.driver.AltibaseStatement
  - setCursorName(String)
- Altibase.jdbc.driver.AltibasePreparedStatement
  - setArray(int, Array)
  - setRef(int, Ref)
  - setURL(int, URL)
  - setUnicodeStream(int, InputStream, int)
- Altibase.jdbc.driver.Blob
  - position(Blob, long)
  - position(byte[], long)
- Altibase.jdbc.driver.Clob
  - position(Clob, long)
  - position(String, long)
- Altibase.jdbc.driver.CallableStatement
  - getArray(int)
  - getObject(int, Map)
  - getRef(int)
  - getURL(int)
- Altibase.jdbc.driver.AltibaseDatabaseMetaData
  - getColumnPrivileges(String, String, String, String)
  - getUDTs(String, String, String, int[])
- Altibase.jdbc.driver.AltibaseResultSet
  - getCursorName()
  - getArray(int)
  - getObject(int, Map)
  - getRef(int)
  - getURL(int)
  - getUnicodeStream(int)
  - updateArray(int, Array)
  - updateRef(int, Ref)

###### DatabaseMetaData

SPECIFIC_NAME column has been added to the results of the getProcedures(), getProcedureColumns(), getFunctions(), and getFunctionColumns() interfaces.
In Altibase 7.3 JDBC, SPECIFIC_NAME is implemented as follows.

```java
ProcName(FuncName) + '_' + ouid
```

###### JDBC Connection Properties

- [reuse_resultset](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/JDBC%20User's%20Manual.md#reuse_resultset)
  - In Altibase 7.3, the default value is 'true', which means that ResultSet objects are reused. 
  - In Altibase 7.1, the default value is 'false', which means that ResultSet objects are not reused.
- [lob_null_select](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/JDBC%20User's%20Manual.md#lob_null_select)
  - When a LOB column's value is NULL, the JDBC connection property 'lob_null_select' has been introduced to control the behavior of getBlob() and getClob() functions. 
  - In Altibase 7.3, the default value is 'off', which means getBlob() and getClob() functions return 'NULL'.
  - In Altibase 7.1, the default value is 'on', which means these functions return LOB objects.

- [getprocedures_return_functions](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/JDBC%20User's%20Manual.md#getprocedures_return_functions)
  - Configuration for including function information in the results of DatabaseMetaData.getProcedures() and getProcedureColumns() is provided. While the JDBC API Specification 4.2 standard excludes function information, Altibase 7.3 JDBC Driver includes it for client backward compatibility. To exclude function information under the JDBC 4.2 standard, set this property value to false.

###### CLIENT_TYPE

The CLIENT_TYPE of an Altibase 7.3 JDBC session is NEW_JDBC42.

</br>

##### Changes in SQL Results and Execution Plans

- Improved SQL Performance When Using the ORDER BY Clause in Subquery Inline Views

  This change has an impact on the execution plan of SQLs that utilize it, with the SORT plan node being eliminated within the SUBQUERY FILTER.

- Optimization of Nested LEFT OUTER JOIN Operations

  This change can result in alterations to the execution plan and potential differences in the SQL execution results for SQLs affected by it.

- Modifications and Additions to Subquery Unnesting Functionality

  This change can lead to alterations in the execution plans of SQLs influenced by it.

</br>

##### Replication Restrictions

###### Replication Restrictions Between Altibase 7.1 and Altibase 7.3

DDL synchronization and Offline Replication are not supported between Altibase 7.1 and Altibase 7.3.

###### Replication Restrictions Between Altibase 6.5.1 and Altibase 7.3

Replication from Altibase 7.3 to Altibase 6.5.1 may fail when the target table contains data with SRID values.

</br>

#### 2.2.4 Properties

The following properties have been added, changed, or deleted in Altibase 7.3.0.0.1. For more information on each property, please refer to the *General Reference*.

##### New Properties

-   [DISK_INDEX_BUILD_SORT_AREA_SIZE](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#disk_index_build_merge_page_count-%EB%8B%A8%EC%9C%84-%ED%8E%98%EC%9D%B4%EC%A7%80-%EC%88%98)
-   [DBLINK_GLOBAL_TRANSACTION_LEVEL](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#dblink_global_transaction_level)
-   [IB_CONCHKSPIN](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#ib_conchkspin)
-   [IB_ENABLE](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#ib_enable)
-   [IB_LATENCY](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#ib_latency)
-   [IB_LISTENER_DISABLE](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#ib_listener_disable)
-   [IB_MAX_LISTEN](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#ib_max_listen)
-   [IB_PORT_NO](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#ib_port_no)
-   [INIT_TOTAL_WA_SIZE](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#init_total_wa_size-%EB%8B%A8%EC%9C%84-%EB%B0%94%EC%9D%B4%ED%8A%B8)
-   [IPCDA_SEM_KEY](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#ipcda_sem_key)
-   [IPCDA_SHM_KEY](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#ipcda_shm_key)
-   [IPC_SHM_KEY](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#ipc_shm_key)
-   [IPC_SEM_KEY](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#ipc_sem_key)
-   [JOB_MSGLOG_COUNT](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#job_msglog_count)
-   [JOB_MSGLOG_FILE](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#job_msglog_file)
-   [JOB_MSGLOG_FLAG](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#job_msglog_flag)
-   [JOB_MSGLOG_SIZE](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#job_msglog_size%EB%8B%A8%EC%9C%84--%EB%B0%94%EC%9D%B4%ED%8A%B8)
-   [LISTAGG_PRECISION](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#listagg_precision-%EB%8B%A8%EC%9C%84-%EB%B0%94%EC%9D%B4%ED%8A%B8)
-   [MATHEMATICS_TEMP_MEMORY_MAXIMUM](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#mathematics_temp_memory_maximum-%EB%8B%A8%EC%9C%84--%EB%B0%94%EC%9D%B4%ED%8A%B8)
-   [NETWORK_ERROR_LOG_FILE](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#network_error_log_file)
-   [PSM_MAX_DDL_REFERENCE_DEPTH](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#psm_max_ddl_reference_depth)
-   [REGEXP_MODE](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#regexp_mode)  
-   [REPLICATION_DDL_SYNC](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#replication_ddl_sync)
-   [REPLICATION_DDL_SYNC_TIMEOUT](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#replication_ddl_sync_timeout--%EB%8B%A8%EC%9C%84--%EC%B4%88-)
-   [REPLICATION_GAP_UNIT](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#replication_gap_unit-%EB%8B%A8%EC%9C%84-%EB%B0%94%EC%9D%B4%ED%8A%B8)
-   [REPLICATION_IB_LATENCY](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#replication_ib_latency)
-   [REPLICATION_IB_PORT_NO](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#replication_ib_port_no)
-   [REPLICATION_META_ITEM_COUNT_DIFF_ENABLE](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#replication_meta_item_count_diff_enable)
-   [REPLICATION_RECEIVER_APPLIER_YIELD_COUNT](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#replication_receiver_applier_yield_count)
-   [REPLICATION_SENDER_IP](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#replication_sender_ip)
-   [SERIAL_EXECUTE_MODE](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#serial_execute_mode)
-   [SERVICE_THREAD_RECV_TIMEOUT](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#service_thread_recv_timeout%EB%8B%A8%EC%9C%84--%EC%B4%88)
-   [SSL_CIPHER_SUITES](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#ssl_cipher_suites)
-   [SSL_LOAD_CONFIG](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#ssl_load_config)        
-   [ST_MSGLOG_COUNT](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#st_msglog_count)
-   [ST_MSGLOG_FILE](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#st_msglog_file)
-   [ST_MSGLOG_FLAG](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#st_msglog_flag)
-   [ST_MSGLOG_SIZE](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#st_msglog_size)
-   [VARRAY_MEMORY_MAXIMUM](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#varray_memory_maximum)

##### Modified Properties

- [ARCHIVE_FULL_ACTION](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#archive_full_action)

  The property has been changed from Read-Only to Read-Write. While there is no change in the default value, a new setting value 2 has been added.

- [CM_MSGLOG_FLAG](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#cm_msglog_flag)

  The default value has been changed to 3.

- [EXECUTE_STMT_MEMORY_MAXIMUM](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#execute_stmt_memory_maximum-%EB%8B%A8%EC%9C%84--%EB%B0%94%EC%9D%B4%ED%8A%B8)

  The default value has been changed from 1073741824 to 2147483648.

- [HASH_AREA_SIZE](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#hash_area_size-%EB%8B%A8%EC%9C%84-%EB%B0%94%EC%9D%B4%ED%8A%B8)

  The minimum value has been changed from 512K to 3M.

- [INDEX_INITRANS](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#index_initrans-%EB%8B%A8%EC%9C%84--%EA%B0%9C%EC%88%98)

  The maximum value has been changed from 30 to 50.

- [INDEX_MAXTRANS](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#index_maxtrans-%EB%8B%A8%EC%9C%84--%EA%B0%9C%EC%88%98)

  The default and maximum values have been changed from 30 to 50.

- [LOB_CACHE_THRESHOLD](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#lob_cache_threshold-%EB%8B%A8%EC%9C%84-bytes)

  The maximum value has been changed from 8192 to 524288.

- [MEMORY_INDEX_BUILD_RUN_SIZE](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#memory_index_build_run_size-%EB%8B%A8%EC%9C%84--%EB%B0%94%EC%9D%B4%ED%8A%B8)

  The default value has been changed from 32768 to 131072.

- [MM_MSGLOG_FILE](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#mm_msglog_file)

  The default value has been changed to 1.

- [PSM_CHAR_DEFAULT_PRECISION](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#psm_char_default_precision)

  The default value has been changed from 32767 to 32000.

- [PSM_NCHAR_UTF16_DEFAULT_PRECISION](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#psm_nchar_utf16_default_precision)

  The default value has been changed from 16383 to 16000.

- [PSM_NCHAR_UTF8_DEFAULT_PRECISION](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#psm_nchar_utf8_default_precision)

  The default value has been changed from 10921 to 10666.

- [PSM_NVARCHAR_UTF16_DEFAULT_PRECISION](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#psm_nvarchar_utf16_default_precision)

  The default value has been changed from 16383 to 16000.

- [PSM_NVARCHAR_UTF8_DEFAULT_PRECISION](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#psm_nvarchar_utf8_default_precision)

  The default value has been changed from 10921 to 10666.

- [PSM_VARCHAR_DEFAULT_PRECISION](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#psm_varchar_default_precision)

  The default value has been changed from 32767 to 32000.

- [REPLICATION_EAGER_PARALLEL_FACTOR](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#replication_eager_parallel_factor)

  The minimum value has been changed from 1 to 2.

- [SERVER_MSGLOG_FLAG](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#server_msglog_flag)

  The default value has been changed from 7 to 15.

- [TOTAL_WA_SIZE](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#total_wa_size-%EB%8B%A8%EC%9C%84-%EB%B0%94%EC%9D%B4%ED%8A%B8)

  The minimum value has been changed to 0.

- [TRANSACTION_SEGMENT_COUNT](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#transaction_segment_count-%EB%8B%A8%EC%9C%84--%EA%B0%9C%EC%88%98)

  The maximum value has been changed from 512 to 16384.

##### Removed Properties

-   GLOBAL_TRANSACTION_LEVEL
-   LOCK_MGR_TYPE
-   LOCK_MGR_SPIN_COUNT
-   LOCK_MGR_MIN_SLEEP
-   LOCK_MGR_MAX_SLEEP
-   LOCK_MGR_DETECTDEADLOCK_INTERVAL
-   TEMP_MAX_PAGE_COUNT
-   TRANSACTION_START_MODE

#### 2.2.5 Meta Tables

##### New Meta Tables

* [SYS_GEOMETRIES_](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-2.The%20Data%20Dictionary.md#sys_geometries_)
* [SYS_GEOMETRY_COLUMNS_](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-2.The%20Data%20Dictionary.md#sys_geometry_columns_)
* [SYS_REPL_RECEIVER_](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-2.The%20Data%20Dictionary.md#sys_repl_receiver_)
* [SYS_REPL_TABLE_OID_IN_USE_](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-2.The%20Data%20Dictionary.md#sys_repl_table_oid_in_use_)
* [USER_SRS_](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-2.The%20Data%20Dictionary.md#user_srs_)

##### Modified Meta Tables

* [SYS_REPLICATIONS_](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-2.The%20Data%20Dictionary.md#sys_repl_hosts_)
  
  A new column has been introduced below.
  
  * REMOTE_LAST_DDL_XSN
  
* [SYS_REPL_HOSTS_](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-2.The%20Data%20Dictionary.md#sys_repl_hosts_)
  
  New columns have been introduced below.
  
  * CONN_TYPE
  * IB_LATENCY
  
* [SYS_REPL_OLD_COLUMNS_](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-2.The%20Data%20Dictionary.md#sys_repl_old_columns_)
  
  A new column has been introduced below.
  
  * MT_SRID
  
* [SYS_REPL_OLD_ITEMS_](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-2.The%20Data%20Dictionary.md#sys_repl_old_items_)
  
  New columns have been introduced below.
  
  * REMOTE_USER_NAME 
  * REMOTE_TABLE_NAME
  * REMOTE_PARTITION_NAME
  * PARTITION_COUNT
  * PARTITION_METHOD
  * PARTITION_ORDER
  * PARTITION_MIN_VALUE
  * PARTITION_MAX_VALUE
  * INVALID_MAX_SN

##### Removed Meta Tables

The following meta tables have been removed.

-   STO_COLUMNS_
-   STO_DATUMS_
-   STO_ELLIPSOIDS_
-   STO_GEOCCS_
-   STO_GEOGCS_
-   STO_PRIMEMS_
-   STO_PROJCS_
-   STO_PROJECTIONS_
-   STO_SRS_
-   STO_USER_COLUMNS_

#### 2.2.6 Performance Views

The following performance views have been added.

For more information on each performance view, please refer to the [**General Reference-2.The Data Dictionary**](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-2.The%20Data%20Dictionary.md).

##### New Performance Views

-   [V$LIBRARY](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-2.The%20Data%20Dictionary.md#vlibrary)
-   [V$PROCINFO](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-2.The%20Data%20Dictionary.md#vprocinfo)
-   [V$QUEUE_DELETE_OFF](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-2.The%20Data%20Dictionary.md#vqueue_delete_off)
-   [V$REPL_REMOTE_META_CHECKS](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-2.The%20Data%20Dictionary.md#vrepl_remote_meta_checks)
-   [V$REPL_REMOTE_META_COLUMNS](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-2.The%20Data%20Dictionary.md#vrepl_remote_meta_columns)
-   [V$REPL_REMOTE_META_INDEX_COLUMNS](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-2.The%20Data%20Dictionary.md#vrepl_remote_meta_index_columns)
-   [V$REPL_REMOTE_META_INDICES](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-2.The%20Data%20Dictionary.md#vrepl_remote_meta_indices)
-   [V$REPL_REMOTE_META_ITEMS](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-2.The%20Data%20Dictionary.md#vrepl_remote_meta_indices)
-   [V$REPL_REMOTE_META_REPLICATIONS](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/General_Reference-2.The%20Data%20Dictionary.md#vrepl_remote_meta_replications)

##### Removed Performance Views

* V$ST_ANGULAR_UNIT
* V$ST_AREA_UNIT
* V$ST_LINEAR_UNIT

</br>

### 2.3 Packages

| OS    | CPU                       | Server/Client   | File Names                                                  |
| ----- | ------------------------- | --------------- | ----------------------------------------------------------- |
| AIX   | PowerPC                   | Altibase Server | altibase-server-7.3.0.0.1-AIX-POWERPC-64bit-release.run     |
|       |                           | Altibase Client | altibase-client-7.3.0.0.1-AIX-POWERPC-64bit-release.run     |
| HP-UX | IA64                      | Altibase Server | altibase-server-7.3.0.0.1-HPUX-IA64-64bit-release.run       |
|       |                           | Altibase Client | altibase-client-7.3.0.0.1-HPUX-IA64-64bit-release.run       |
| LINUX | x86-64                    | Altibase Server | altibase-server-7.3.0.0.1-LINUX-X86-64bit-release.run       |
|       |                           | Altibase Client | altibase-client-7.3.0.0.1-LINUX-X86-64bit-release.run       |
| LINUX | PowerPC                   | Altibase Server | altibase-server-7.3.0.0.1-LINUX-POWERPC-64bit-release.run   |
|       |                           | Altibase Client | altibase-client-7.3.0.0.1-LINUX-POWERPC-64bit-release.run   |
| LINUX | PowerPCLE (Little Endian) | Altibase Server | altibase-server-7.3.0.0.1-LINUX-POWERPCLE-64bit-release.run |
|       |                           | Altibase Client | altibase-client-7.3.0.0.1-LINUX-POWERPCLE-64bit-release.run |

</br>

### 2.4 Download

#### Package

http://support.altibase.com

#### Manual

https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/README.md

#### Installation

https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/Installation%20Guide.md

------

<a name="shapefile">[1]</a> Shapefile: A file format developed by ESRI, a software developer specializing in Geographic Information Systems (GIS). In the GIS field, the Shapefile is considered a standard file format and consists of the following three essential files.  [↩](#shapefile1)

- shp : contains spatial data information representing points, lines, and shapes in a vector format.
- shx : Index file, which contains the location of the shape information stored in the shp file.
- dbf : dBASE table file containing attribute information about the shape information in the shp file.

References : [Geoprocessing considerations for shapefile output](https://desktop.arcgis.com/en/arcmap/latest/manage-data/shapefiles/geoprocessing-considerations-for-shapefile-output.htm)

