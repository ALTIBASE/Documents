<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Altibase 8.1.0.0.1 Release Notes](#altibase-81001-release-notes)
  - [1. System Requirements](#1-system-requirements)
    - [Minimum Hardware Requirements](#minimum-hardware-requirements)
    - [Operating Systems and Platforms](#operating-systems-and-platforms)
  - [2. Release Notes](#2-release-notes)
    - [2.1 New Features](#21-new-features)
    - [2.2 Changes](#22-changes)
    - [2.3 Packages](#23-packages)
    - [2.4 Download](#24-download)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

</br>

</br>

</br>

Altibase 8.1.0.0.1 Release Notes
===============================

**(2026.02)** </br>



## 1. System Requirements

### Minimum Hardware Requirements

* 1GB RAM (Recommended: 2GB)
* 1 CPU (Recommended: 2 CPUs)
* 4 GB free hard disk space (Recommended: 12 GB)



### Operating Systems and Platforms

Altibase 8.1.0.0.1 can be run on the operating systems and platforms listed in the table below.


|                                                           | Altibase Server | Altibase Client | Software requirements   |
| --------------------------------------------------------- | :-------------: | :-------------: | :---------------------- |
| **AIX on IBM Power Systems**                              |                 |                 |                         |
| AIX 7.2                                                   |        ●        |        ●        |                         |
| **Linux x86-64**                                          |                 |                 |                         |
| Red Hat Enterprise Linux 9                                |        ●        |        ●        | - GNU glibc 2.34        |
| Red Hat Enterprise Linux 7<br/>Red Hat Enterprise Linux 8 |        ●        |        ●        | - GNU glibc 2.12 ~ 2.33 |
| **Microsoft Windows (x64)**                               |                 |                 |                         |
| Microsoft Windows 2008                                    |      **x**      |        ●        |                         |
| Microsoft Windows 10                                      |      **x**      |        ●        |                         |

> Altibase 8.1 server and client both support 64-bit only.
>
> Altibase 8.1 is compatible with minor versions of Red Hat Enterprise Linux 7,8 and 9.
>
> Altibase 8.1 is compatible with JDK 1.8 and higher.

<br/><br/>

## 2. Release Notes

### 2.1 New Features

#### 2.1.1 Support for JSON Data Type

Starting with Altibase 8.1, a **Native JSON data type** is supported in compliance with the **IETF RFC 8259** standard. The JSON data type in Altibase can store up to **2 GB**, enabling the efficient handling of large-scale JSON datasets.

In addition, it supports **JSON path expressions** following the **ISO/IEC 19075-6:2021** standard, allowing for standard-based JSON querying and data extraction. To facilitate JSON data processing, the following key JSON functions are provided:

* JSON_ARRAY
* JSON_OBJECT
* JSON_EXISTS
* JSON_QUERY
* JSON_VALUE
* JSON_VALID

These features enable the integrated processing of relational and JSON data, supporting the development of standard-based applications.

#### 2.1.2 Support for Temporary LOB Data Type

Temporary LOBs are supported to efficiently process large text and binary data.
A Temporary LOB is a transient LOB created in memory at execution time and exists within a specific session or transaction. It is automatically removed when the corresponding session or transaction terminates. 

In Altibase, Temporary LOBs are classified into Session Temporary LOBs and Transaction Temporary LOBs, depending on how they are used.

* Session Temporary LOB: When LOB data types are used as **ASSOCIATIVE ARRAY, VARRAY, or PACKAGE variables** within PSM, they are handled as Session Temporary LOBs.
* Transaction Temporary LOB: The following cases are handled as Transaction Temporary LOBs:
  * When calling the `TO_CLOB` or `TO_BLOB` functions
  * When processing functions such as `SUBSTR` or `CONCAT` that accept a CLOB argument
  * When handling LOB-type variables within PSM execution

Information about currently used Temporary LOBs can be queried through the `V$TEMPORARY_LOBS` view.

#### 2.1.3 KADA (Key-optimized Altibase Document Access) API

Altibase 8.1 provides the **KADA (Key-optimized Altibase Document Access)** API to enable more efficient handling of JSON-based document data.
 KADA supports key-based document access and is available in both **Java API** and **REST API** forms.

* KADA for Java API

  * NoSQL-style CRUD operations: Provides an intuitive API that allows applications to create, read, update, and delete JSON documents using a unique key, without writing SQL statements.

  * Flexible application development: Supports query operators and syntax similar to MongoDB.

  * Manual transaction control

  * Ensures safe resource release through the `AutoCloseable` interface.

* KADA for REST API

  Provides REST APIs that enable management of JSON documents in the Altibase database over HTTP.

  * Supports JWT-based authentication
  * Supports multi-tenant isolation
  * Provides ACL-based collection sharing

#### 2.1.4 Altibase Connectors(Source & Sink)

Altibase 8.1 provides dedicated connectors for real-time data integration and synchronization between Altibase and Apache Kafka. These connectors enable users to easily build low-latency real-time data pipelines and event-driven architectures.

* Altibase Source Connector: Detects change data in Altibase and publishes it to Kafka topics.
* Altibase Sink Connector: Consumes messages from Kafka topics and applies them to Altibase tables. 

#### 2.1.5 ABM(Altibase Backup Manager)

`abm` is a utility that supports physical backup of the Altibase database. It is provided to efficiently perform backup operations and securely manage backup files.
Through an intuitive interface, users can easily perform backup operations as well as backup file compression, encryption, and decryption. 

#### 2.1.6 SSL/TLS Support for Replication Communication

Altibase 8.1 supports the SSL/TLS encryption protocol for replication communication. This enhances security by encrypting data transmitted during replication. 

SSL/TLS communication can be configured using the `USING SSL` clause when creating replication.
 In addition, the `REPLICATION_SSL_PORT_NO` property has been added to configure SSL-based replication communication.

#### 2.1.7 Utilities and Features Added for Enhanced Security

* **altiEncrypt Utility**

  `altiEncrypt` is a utility for password encryption. By configuring encrypted passwords generated using `altiEncrypt`, exposure of plaintext passwords can be prevented.
   Encrypted passwords created by `altiEncrypt` can be used in the configuration files of AKU, dblink, and adapters.

* **Encrypted Password File Generation Satement Added**

  A new statement has been added to generate encrypted password files from user passwords.
  The generated encrypted password file can be used when logging in to iSQL, iLoader, aexport, and abm using the -pf option.
  This prevents storing passwords in plaintext and enhances security.

#### 2.1.8 Performance Improvements

* **Support for Checkpoint Scale Single Mode**

  To improve the management of memory database checkpoint image files, support for the single checkpoint scale mode is provided. When the checkpoint scale is set to single mode, a single checkpoint image file is created when generating a memory tablespace. Then, when a checkpoint is performed, it internally operates using the ping-pong checkpoint method, but ultimately leaves only one stable checkpoint image file. This enhances disk usage efficiency.

* **Improved Performance of Memory Index Build During Server Startup**

* **Improved Performance During Server Shutdown and Memory Index Removal**

* **Performance Improvements to the Log File Prepare Thread**

  * The default value of `LOG_FILE_SIZE` has been changed from 10MB to 100MB.
  * he default value of `LOG_CREATE_METHOD` has been updated.

* **Improved Performance for Bulk LOB Insert Operations** 

* **Improved Page Cache Handling During Memory Database Startup**

#### 2.1.9 Enhancements and Feature Support for External Integration

* **Altibase Handler Officially Supported in MindsDB**

Altibase has developed the **Altibase Handler** for integration with **MindsDB**, an open-source AI data platform, and it has been officially included starting from MindsDB v24.5.4.
 This enables Altibase to be directly connected as a data source in the MindsDB environment, allowing Altibase data to be used for machine learning model training and prediction workflows.

* **Support for .NET 8 Environment**

Altibase ADO.NET 드라이버 및 Altibase EF(Entity Framework) Core가 .NET 8.0 환경에서 동작할 수 있도록 개선되었다.

* **Support for Node.js Driver (node-odbc-altibase)**

The `node-odbc-altibase` driver is provided to enable access to Altibase servers from Node.js environments, supporting integration with JavaScript-based applications.

#### 2.1.10 Interface Enhancements for Empty LOB Handling

To enhance flexibility in LOB data processing, functionality supporting empty LOBs (LOB data with length 0) has been added and improved across multiple interfaces.

* CLI
  * New functions SQLEmptyLob() and SQLGetLobLength2() have been added.
* iLoader
  * iLoader behavior has been improved to support empty LOB processing.
    (Supported only when the -lob -use_lob_file=yes option is specified.)
* JDBC
  * JDBC behavior has been improved to support empty LOB processing.

* JDBC Adapter, OraAdapter
  * Empty LOB processing is now supported.


#### 2.1.11 ODBC Driver Enhancements

* **Support for Updatable Dynaset**

* **Improved Read Performance of Keyset-Driven Cursor**

  When executing a SELECT statement using the `SQL_CURSOR_KEYSET_DRIVEN` cursor, read performance has been improved by reducing the number of server-client communications (fetch protocol).

#### 2.1.12 AKU(Altibase Kubernetes Utility) Enhancements

* Scale-up support for up to six nodes
* Support for multiple replications : Multiple replication configurations can be defined in the REPLICATIONS setting of the aku.conf file using comma-separated values. For more details, refer to the AKU manual.
* Performance improvement through multi-thread–based parallel processing
* The maximum length limit for table names and user names in replication targets has been increased from 40 characters to 128 characters.

#### 2.1.13 Thai Character Set Support

Official support for the Thai character set has been added.
Thai collation based on the ISO/IEC 14651 standard is supported in UTF-8 environments, enabling accurate and consistent processing of Thai data. This enhancement improves data reliability for localization services and global environments.

* To use Thai collation, NLS_COMP must be set to 1.

#### 2.1.14 Other Enhancements

* **Support for Table Statistics Locking**

  The `LOCK_TABLE_STATS` and `UNLOCK_TABLE_STATS` procedures have been added to the `DBMS_STATS` package to allow locking and unlocking of table statistics.

* **Support for JSON-formatted execution plans**

  Support has been added for outputting execution plans in JSON format. This feature generates structured execution plan information as JSON objects, enabling more efficient integration with external tools, visualization, and performance analysis.

* **Statement Caching Support in JDBC**

  The JDBC driver now supports statement caching for `PreparedStatement` and `CallableStatement`.
   This improves performance when executing identical SQL statements repeatedly. The feature can be enabled through the connection property `stmt_cache_enable` and can be applied without modifying existing application code.
  
* **Expanded META LOGGING Support for Replication**

  The META LOGGING option, previously available only in JDBC Adapter and OraAdapter, is now supported in general replication environments.

</br>



### 2.2 Changes

The following describes the features that DBAs and developers need to be aware of, which include additions, modifications, and removals.

#### 2.2.1 Database Version

Version by Database Component

| Altibase Server/Client Version | Database Binary Version | Meta Version | Communication Protocol Version | Replication Protocol Version |
| :----------------------------: | :---------------------: | :----------: | :----------------------------: | :--------------------------: |
|           8.1.0.0.1            |          8.1.0          |    10.1.1    |             7.1.9              |            7.4.9             |
|           7.3.0.1.5            |          7.3.0          |    9.4.1     |             7.1.8              |            7.4.9             |
|           7.3.0.0.1            |          7.3.0          |    9.3.1     |             7.1.8              |            7.4.9             |

#### 2.2.2 Compatibility

##### Database Binary Version

The database binary version indicates the compatibility between database image files and log files.

The database binary version has changed due to improvements in the log file logging structure. **It is not compatible with Altibase databases prior to version 8.1, so migration is required when upgrading the Altibase version.**

##### Meta Version

Since the META MAJOR VERSION has been changed, **metadata must be rebuilt when upgrading from versions prior to Altibase 8.1 to Altibase 8.1.**

##### Communication Protocol Version

It represents the communication protocol compatibility between the Altibase server and client, and indicates client backward compatibility.

Since only the patch version of the communication protocol has been changed, backward compatibility is preserved.

> Client backward compatibility ensures that user applications developed using an older version of the Altibase library work well when connected to a newer version of Altibase.

##### Replication Protocol Version

The replication protocol version indicates the compatibility of replication.

No changes have been made to the replication protocol.

> ###### Altibase Replication Backward Compatibility
>
> Only LAZY mode replication guarantees backward compatibility.
> 
>EAGER mode replication does not guarantee backward compatibility.
> 
> Replication optional features, including offline replication, do not guarantee backward compatibility.
>
> DDL replication guarantees backward compatibility only when all three digits of the replication protocol version are identical.

</br>

#### 2.2.3 Others

##### iLoader API Build Environment Change(Addition of libaltiutil.a)

To enable login using encrypted password files in applications that use the iLoader API, the `libaltiutil.a` library must be included during iLoader API compilation.

##### aexport Property Changes

| Property Name      | Before | After   |
| ------------------ | ------ | ------- |
| ILOADER_FIELD_TERM | ^      | ^C_c^   |
| ILOADER_ROW_TERM   | %n     | ^R_r^%n |

##### Altibase Stored Package Changes

The DBMS_METADATA package needs to be updated.

#### 2.2.4 Properties

The following properties have been added, changed, or deleted in Altibase 8.1.0.0.1. For more information on each property, please refer to **[General Reference-Altibase Properties](https://manual.altibase.com/8.1/en/ref/general/2.-Altibase-Properties/2.-Altibase-Properties/)**.

##### New Properties

-   CHECKPOINT_SCALE_SINGLE_DW_BUFFER_SIZE
-   MEMORY_TEMPLOB_MAX_ALLOC_SIZE
-   MEMORY_TEMPLOB_PIECE_SIZE
-   REPLICATION_SSL_PORT_NO
-   PSM_CASE_SENSITIVE_MODE
-   TEMPORARY_LOB_ENABLE
-   TRCLOG_EXPLAIN_TYPE
-   TRCLOG_JSON_PLAN_INDENT_DEPTH

##### Modified Properties

- CHECKPOINT_INTERVAL_IN_LOG
  - The default value has been changed from 100 to 10

- FAST_START_LOGFILE_TARGET
  - The default value has been changed from 100 to 10

- LOG_CREATE_METHOD
  - The default value has been changed from 0 to 1.

- LOG_FILE_SIZE
  - The default value has been changed from 10,485,760 to 104,857,600.
  - The maximum value has been changed from 18,446,744,073,709,551,615 to 4,294,967,295.

- MEMORY_INDEX_BUILD_RUN_SIZE
  - The maximum value has been changed from 18,446,744,073,709,551,615 to 4,294,967,295.

- MEMORY_INDEX_BUILD_VALUE_LENGTH_THRESHOLD
  - The maximum value has been changed from 18,446,744,073,709,551,615 to 4,294,967,295.

- OPTIMIZER_FEATURE_ENABLE
  - The default value has been changed from 7.3.0.0.1 to 8.1.0.0.1.

##### Removed Properties

-   INSPECTION_LARGE_HEAP_THRESHOLD

#### 2.2.5 Meta Tables

No meta tables are added, deleted, or changed.

#### 2.2.6 Performance Views

The following performance views have been added.

For more information on each performance view, please refer to the [**General Reference-Performance View**](https://manual.altibase.com/8.1/en/ref/general/3.-The-Data-Dictionary/Performance-Views/).

##### New Performance Views

-   V$LOCK_TABLE_STATS
-   V$MEM_STABLE
-   V$TEMPORARY_LOBS

</br>

### 2.3 Packages

| OS    | CPU     | Server/Client   | File Names                                               |
| ----- | ------- | --------------- | -------------------------------------------------------- |
| AIX   | PowerPC | Altibase Server | altibase- server-8.1.0.0.1-AIX-POWERPC-64bit-release.run |
|       |         | Altibase Client | altibase- client-8.1.0.0.1-AIX-POWERPC-64bit-release.run |
| LINUX | x86-64  | Altibase Server | altibase-server-8.1.0.0.1-LINUX-X86-64bit-release.run    |
|       |         | Altibase Client | altibase-client-8.1.0.0.1-LINUX-X86-64bit-release.run    |

</br>

### 2.4 Download

#### Package

http://support.altibase.com

#### Manual

https://manual.altibase.com/8.1/

