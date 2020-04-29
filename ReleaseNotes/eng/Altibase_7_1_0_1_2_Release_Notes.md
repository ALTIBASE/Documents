<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Altibase 7.1.0.1.2 Release Notes](#altibase-71012-release-notes)
  - [System Requirements](#system-requirements)
    - [Minimum Hardware Requirements](#minimum-hardware-requirements)
    - [Operating Systems and Platforms](#operating-systems-and-platforms)
  - [Release Notes](#release-notes)
    - [New Features](#new-features)
    - [Changes](#changes)
    - [Packages](#packages)
    - [Download](#download)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Altibase 7.1.0.1.2 Release Notes

The final version of the Altibase 7.1 release is 7.1.0.1.2, and maintenance starts from 7.1.0.1.2.



## System Requirements

### Minimum Hardware Requirements

* 1GB RAM (Recommended: 2GB) 
* 1 CPU (Recommended: 2 CPUs) 
* 4 GB free hard disk space (Recommended: 12 GB)

### Operating Systems and Platforms

Altibase 7.1.0.1.2 can be run on the operating systems and platforms listed in the table below.

| OS    | CPU                                         | Version               | Bit (Server) | Bit (Client) |
| ----- | ------------------------------------------- | --------------------- | ------------ | ------------ |
| AIX   | PowerPC                                     | 6.1 tl03 and higher   | 64-bit       | 64-bit       |
| HP-UX | IA64                                        | 11.31 and higher      | 64-bit       | 64-bit       |
| LINUX | X86-64, PowerPC (GNU glibc 2.12 and higher) | redhat 6.0 and higher | 64-bit       | 64-bit       |
| LINUX | PowerPC8(LE) (GNU glib 2.17)                | redhat 7.2            | 64-bit       | 64-bit       |

> Java version: Altibase 7.1 is compatiable with JDK 1.5 or higher.
>
> Starting with Altibase 7.1, Window Server and Client are not supported. Also, 32-bit clients are no longer supported.
>
> The Linux PowerPC8_LE (little endian) platform was added.



## Release Notes

### New Features

#### Altibase Sharding 2.0

As of Altibase 7.1, Altibase Sharding is provided. Altibase Sharding introduces sharding technology to Altibase, improving stroage capacity and throughput per hour, and enabling distributed processing of large databases.

Altibase Sharding is a hybrid sharding, and anlyzes existing SQL to automatically analyze whether to perform client-side sharding or server-side sharding to optimize the path.

Altibase Sharding supports various distributed methods, distributed objects, and utilities, and can be applied to various tasks. Altibase Sharding can be easily applied by replacing only the shard-only library without modifying the existing SQL.

In addition, the server-side sharding can be applied without modifying any existing applications. 

####  Meta Downgrade

##### SQL Extension

Previously, to roll back a patch when the meta version was different, the user had to manually reconfigure the version with the meta of the version the user wants to roll back to, and then roll back the patch. As of ALtibase 7.1.0.1.2, a meta downgrade command is provided so that patch rollback can be performed even when the meta version is different.

'''
% server downgrade
'''

###### Parition Exchange DDL Support

Parition CONJOIN and partition DISJOIN statements are provided to enable partition exchange between normal partitions (non-partitioned tables) and partitioned tables as well as partitions of partitioned tables.

* **CONJOIN**: This statement converts a non-partitioned table to a table partition. List and range partitions are supported, and hash partitions are not supported. All data in the target table is moved to the created partition.
* **DISJOIN**: This statement converts a partition of a partitioned table to a non-partitioned table. Hash partitioning is not supported, and non-partitioned tables retain the attributes of existing partitions.

###### Changing Tablespace for Table

By using the ALTER TABLE statement, the function to change the tablespace of a table to another tablespace is supported.

The user can move the tablespace storage space of the table. At this time, the index and LOB column are also moved. However, since a partitioned table can only move records of one partition, DDL must be executed several times to move records of all partitions.

###### Hybrid Partitioned Table Support

By supporting hybrid partitioned tables, partitioned tables can move data from disk tablespaces to memory/volatile tablespaces from memory/volatile tablespaces to disk tablespaces.

> Constraint:
>
> Global index is not supported.

###### COMPACT, AGING Statement Extension

COMPACT and AGING statements can be performed on a partitioned table in units of partitions.

###### NOWAIT, WAIT Support

NOWAIT and WAIT options are supported for INSERT, FOR UPDATE, and DEQUEUE statements.

###### User-defined Column Support When Creating a Queue

When creating a queue, the user can define columns.

###### Table Function Support

TABLE FUNCTION converts the associative array type or record type value returned by the user-defined function into a table type and outputs it.

###### Added Aggregate and Window Functions 

Altibase supports percentage ranking, ratio analysis function, cumulative distribution of groups, sorting function, correlation coefficient, sample covariance, and pore variance that can be used in aggregate and window functions.

* PERCENT_RANK
* CUME_DIST
* RATIO_TO_REPORT
* NTILE
* CORR
* COVAR_SAMP
* COVAR_POP

###### Added User Lock Funcitons

Functions that allow the user to request or release a user lock in a session are supported.

* USER_LOCK_REQUEST
* USER_LOCK_RELEASE

###### Other Functions

A function that returns the context information connected to the current session is supported.

* SYS_CONTEXT

The following functions are supported for encoding or decoding VARBYTE type strings.

* BASE64_DECODE
* BASE64_ENCODE

The following functions are supported for decoding or envoding a VARBYTE type string converted to Quoted printable type and returning it as a VARBYTE type string.

* QUOTE_PRINTABLE_DECODE
* QUOTE_PRINTABLE_ENCODE

Altibase PIPE funciton, which is not belonging to a specific schema and managed at the entire database level, has been added. The added functions are as follow:

* MSG_CREATE_QUEUE
* MSG_DROP_QUEUE
* MSG_SND_QUEUE
* MSG_RCV_QUEUE

###### LOCK TABLE supports 'UNTIL NEXT DDL' Statement

If a DDL is executed on a table when the session is in the NON-AUTOCOMMIT mode, the commit is automatically performed immediately before the DDL is executed.

However, if EXCLUSIVE mode is specified in lock_mode, commit is not automatically executed immediately before DDL is executed.

###### ENABLE, DISABLE Support When Creating Trigger

When creating a trigger, the user can set the enable state and the disable state. After that, the user can change the ENABLE/DISABLE state with the ALTER TRIGGER statement.

###### FIRST, LAST Aggregate Functions

For data sorted by Order by, a function that aggregates the FIRST or LAST was added. Functions that can be used together are MIN, MAX, SUM, AVG, COUNT, VARIANCE, and STDDEV.

* KEEP (DENSE_RANK FIRST ORDER BY)
* KEEP (DENSE_RANK LAST ORDER BY)

###### Date Data Format Support

The following date data types are supported by date funcitons such as ROUND (date) and TRUNC (date).

* SCC, CC, SYYYY, YYYY, YYY, YY, Y, Q, MON, MM, RM, WW, DDD, DD, J, HH, HH12, HH24, MI

###### Spatial Functions REVERS and MAKEENVELOPE

* REVERSE(GEOMETRY): Changes the point of the entered spatial object in reverse order.
* MAKEENVELOPE(X1, Y1, X2, Y2): Returns LINESTRING (X1 Y1, X2 Y2) corresponding to 4 input double variables as POLYGON (X1 Y1, X2 Y1, X2 Y2, X1 Y2, X1 Y1), which is the result of ENVELOPE.

###### Numeric Function

* NUMAND
* NUMOR
* NUMSHIFT
* NUMXOR

##### Replication Improvement

###### Replication Constraint Improvement

Replication is supported even if the column type, primary key, and NOT NULL constraints of the tables to be replicated on both servers are not the same.

###### SQL APLLY MODE

If the table schema information of the local server and the remote server is different, it provides a function to convert and reflect XLog to SQL on the remote server.

REPLICATION_SQL_APPLY_ENABLE was added, and it can be used by setting the REPLICATION_SQL_APPLY_ENABLE property value to 1.

> Constraint:
>
> It operates in SQL reflection mode only in LAZY mode. If a security column exists in the table, it does not operate in SQL reflection mode.

###### Added Executale DDL statements to the Table to be Replicated

By adding the REPLICATION_DDL_EN_ABLE_LEVEL property, DDL statement execution is allowed according to REPLICATION_DDL_ENABLE_LEVEL.

> Constraints:
>
> DDL statements cannot be executed on a tabler where the replication recovery option is specified.
>
> Also, DDL statement cannot be executed when replication is running in EAGER mode

##### DBLink Two-Phase Commit (2PC) Level Support and Function Improvement

To guarantee the consistency of global transactions executed between Altibase and heterogeneous database systems, DB LINK provides a 2PC protocol.

If the DBLINK_GLOBAL_TRANSACTION_LEVEL property is set to Two-Phase Commit Level and then commit is executed, ALTIBASE HDB and remote database systems exchange and receive messages using 2PC protocol.

The following properties are added and modified in relation to ensuring the consistency of distributed transactions.

* DBLINK_RECOVERY_MAX_LOGFILE
* DBLINK_GLOBAL_TRANSACTION_LEVEL

The added and modified performance views related to the consistency of distributed transactions are as follows.

* V$DBLINK_NOTIFIER_TRANSACTION_INFO
* V$DBLINK_LINKER_DATA_SESSION_INFO
* V$DBLINK_GLOBAL_TRANSACTION_INFO
* V$DBLINK_REMOTE_STATEMENT_INFO
* V$DBLINK_REMOTE_TRANSACTION_INFO
* V$SESSION

###### REMOTE Function Supporting Batch Processing in DBLink

Altibase has added a remote function and related functions that can be batch processed by Altibase DB Link. The added function can be used only within the stored procedure.

* IS_ARRAY_BOUND
* IS_FIRST_ARRAY_BOUND
* IS_LAST_ARRAY_BOUND
* REMOTE_ADD_BATCH
* REMOTE_ALLOC_STATEMENT_BATCH
* REMOTE_BIND_VARIABLE_BATCH
* REMOTE_EXECUTE_BATCH
* REMOTE_FREE_STATEMENT_BATCH
* REMOTE_GET_RESULT_COUNT_BATCH
* REMOTE_GET_RESULT_BATCH

##### Application Development Interface Extension and Improvements

###### PDO Driver Support

Altibase PDO driver has been added to work with. ALTIBASE in PHP applications.

###### FETCH Statement Supported in FOR clause in Embedded SQL

When using a host array in an embedded SQL statement, the FETCH statement can be used in the FOR clause.

##### Built-in Packages and Functions

###### AUTHID Support in Stored Procedures

The users can specify the permission to execute a procedure, funciton, or package in a stored procedure. It can be specified by adding the following clause in the CREATE PROCEDURE, CREATE FUNCTION, and CREATE PACKAGE statements.

* AUTHID CURRENT_USER: Specifies to execute with user authority
* AUTHID DEFINER: Specifies to execute with the creator's authority

###### STANDARD System Package

The STANDARD package was added to support the SYS_REFCURSOR type.

###### UTL_COPYSWAP System Package

The UTL_COPYSWAP package provides interfaces such as table schema copy, data replication, and table exchange. Refer to the table below for the procedures and functions that make up the UTL_COPYSWAP package.

| Procedure and Function Package | Description                                                  |
| ------------------------------ | ------------------------------------------------------------ |
| CHECK_PRECONDITION             | Checks permissions, session properties, system properties, and replication constraints |
| COPY_TABLE_SCHEMA              | Copies the table schema.                                     |
| REPLICATE_TABLE                | Replicates data                                              |
| SWAP_TABLE                     | Exchanges tables                                             |
| SWAP_TABLE_PARTITION           | Exchanges table partitions (To be provided in 7.1.0.1.3)     |
| FINISH                         | Cleans up what was created in COPY_TABLE_SCHEMA and REPLICATION_TABLE |

###### UTL_SMPT Package Support

The UTL_SMTP storage package that performs the SMTP protocol has been added so that EMAIL can be used. Refer to the table below for the procedures and functions that make up the UTL_SMTP package.

| Procedure and Function Package | Description                                                  |
| ------------------------------ | ------------------------------------------------------------ |
| OPEN_CONNECTION                | Creates a TCP socket and connect to the SMTP server          |
| HELO                           | Sends the HELO domain command, which is the initialization of the SMTP protocol |
| MAIL                           | Sends the MAIL FROM: \<reverse-path> command, which is the sender setting of the MTP protocol |
| RCPT                           | Sends the RCPT TO: \<forward-path> command, which is the recipient setting of the SMTP protocol |
| OPEN_DATA                      | Sends the DATA command, which is the start of data transmission of the SMPT protocol |
| WRITE_DATA                     | Sends data using the SMTP protocol                           |
| WRITE_RAW_DATA                 | Sends RAW data using the SMTP protocol                       |
| CLOSE_DATA                     | Sends \<CRLF> \<CRLF>, which is the end of data transmission of SMTP protocol |
| QUIT                           | Terminates the connection with the QUIT command of the SMTP protocol |

###### Other System-defined Save Packages

Other system-defined storage packges added by Altibase are as follows.

DBMS_ALERT: Informs other users of events occurring in the database as an interface.

DBMS_APPLICATION_INFO: Sets performance view values to manage client application information

DBMS_CONCURRENT_EXEC: procedure can be executed simulatneously

DBMS_LOCK: Provides an interface for a user to. request or release a lock

DBMS_OUTPUT: Outputs the string stored in the buffer to the client

DBMS_RANDOM: Generates random numbers

DBMS_SQL: Provides procedures and functions that use dynamic SQL

DBMS_STATS: Provides a subprogram that cna use various database statistics information

DBMS_RECYCLEBIN: It is possible to completely purge a table managed in the recycle bin by dropping it

DBMS_UTILITY: Provides subprograms of various utilities

UTL_FILE: The user can read and write by accessing text files managed by the operating system

UTL_RAW: The user can convert or manipulate RAW (VARBYTE) type data into other data types

UTL_TCP: Stored procedures control TCP connections

###### Static SQL Support when Using Cursors

In the OPEN FOR statement, the user can use static SQL as well as dynamic SQL.

> Static SQL cannot be used with the USING clause.

###### BULK COLLECTION INTO support in FETCH Cursor Statement

BULK COLLECTION INTO function is supported in FETCH statement. In addition, by supporting the limit functio, the number of rows returned in the BULK COLLECT clause can be adjusted.

###### NOCOPY Option Support

NOCOPY Option is supported for parameters and local variables used in stored procedures and stored functions. This option is a method of assigning an argument using a reference value.

> The NOCOPY option supports ASSOCIATIVE ARRAY type only.

###### Package Subprogram Overloading Support

Subprograms can be overloaded in a storage package. That is, the name of the subprogram is the same, but the argument name and data type can be defined differently.

###### Determining PSM Character Data Size

A property has been added to determine the size of charater data types used in stored procedures and functions.

* PSM_CHAR_DEFAULT_PRECISION
* PSM_NCHAR_UTF8_DEFAULT_PRECISION
* PSM_NCHAR_UTF16_DEFAULT_PRECISION
* PSM_NVARCHAR_UTF8_DEFAULT_PRECISION
* PSM_NVARCHAR_UTF16_DEFAULT_PRECISION
* PSM_PARAM_AND_RETURN_WITHOUT_PRECISION_ENABLE
* PSM_VARCHAR_DEFAULT_PRECISION

The following properties that set the default size of character data types have been removed.

* CHAR_DEFAULT_PRECISION
* NCHAR_DEFAULT_PRECISION
* NVARCHAR_DEFAULT_PRECISION
* VARCHAR_DEFAULT_PRECISION

###### PRAGMA AUTONOMOUS_TRANS ACTION, PRAGMA EXCEPTION_INIT Statement Support

The PRAGMA statement is supported in the stored procedure, funciton, and stored package creation statement.

* PRAGMA AUTONOMOUS_TRANSACTION: Autonomous transaction pragma. The user can change the way PSM objects operate within a transaciton.

* PRAGMA EXCEPTION_INT: The exception initialization pragma. it is a function that allows the user to initialize the exception variable with the error code of Altibase.

##### Client Tools

###### JDBC Adapter Support

JDBC Adapter is a utility that applies data changed in the Altibase database to other (third-party) databases that support JDBC. This is a structure that replicates the changed data to the target database using Altibase Log Analysis API (ALA) and Java Database Connectivity (JDBC) provided by Altibase.

> Currently, it can only be used in the Linux operating system, and works with JRE 7 or higher.

###### SQuirreL SQL Client Integration

The SQuirreL SQL client, an open source product for DB object browsing and SQL execution, can be used in conjunction with Altibase.

###### Shard Manage Support

Shard Manager is a tool to help organize and manage Altibase Sharding data nodes and shard objects. Altibase Sharding consists of multiple databases, so managing each database and object can be expensive. In this environment, the user can use Shard Manager to improve work efficiency.

###### altimon.sh Improvement

altimon.sh has been mainly improved to  monitors OS information and DB information, and in order to collect OS information, it is possible in an operating system that can use the PICL library.

###### Change of INPUT/OUTPUT Type Related Behavior in iSQL Host Variable Declaration

When declaring a host variable for use in executing a procedure or function, if INPUT/OUTPUT is not specified, the default value is set to the type received from the client.

> In Altibase 6.5.1.4.1 and below, if INPUT/OUTPUT is not specified, the default is INPUT.

###### iSQL Commands

In iSQL, a command to set the display format for the column of the SELECT result has been added.

SET NUMF[ORMAT]: Sets the display format of numeric data type

COLUMN: Sets the column display format of character type or numeric type

CL[EAR] COL[UMNS]: Unsets all columns set with COLUMN command

###### iLoader -prefetch_rows Support

It supports -prefetch_rows option, which can be used in iLoader out mode. When executing a select query, the user can specify the number of records fetched from the database at one time.

###### Display Partition Information

When viewing the table structure using the DESC command, information about the partition is also displayed.

###### dataCompJ

When replicating data from an Altibase database to a heterogeneous database, dataCompJ was added as a tool to verify data consistency and resolve data inconsistencies.

###### Asynchronous Prefetch Attribute

Asynchronous prefetch-related functions have been added to iLoader performance options and aexport property.

* ASYNC_PREFETCH = OFF|ON|AUTO (default: OFF): Use with OUT command
* ILOADER_ASYNC_PREFETCH = ON|AUTO (default: ON)

###### aexport Properties

The properties of the aexport utility have been added as follows.

* ILOADER_ARRAY
* ILOADER_COMMIT
* ILOADER_ERRORS
* ILOADER_PARALLEL

#### Efficiency

##### Server Performance Improvement

###### Improved Performance of Disk Buffer Manager

To prevent frequently used pages from being selected as a Victim in the buffer pool, change the flush order for recently used pages to speed up the disk buffer manager.

DELAYED_FLUSH_LIST_PCT: Specifies the maximum rate of the delayed flush list. (%)

DELAYED_FLUSH_PROTECTION_TIME_MSEC: This is a reference time for considering as the recently used page. If the last used time is less than the set value, it is considered as the recently used page. (Millisecond)

###### Memory Fetch Performance Improvement 

Memory full scan and index can performance has been improved.

###### Result Cache Support

The user can use the Result Cache to store the intermediate or final result of the first query executed on the server, and reuse the result when the same query is executed again.

###### Automatic Statistic Information Collection

Statistical information that can be used by the optimizer can be collected automatically.

###### Hints

Hints for normalization type, join method, join order, table access method, and parallel query processing have been added.

* INDEX_ASC
* INDEX_DESC
* LEADING
* NO_EXPAND
* NO_INDEX
* NO_PARALLEL
* NO_USE_HASH
* NO_USE_MERGE
* NO_USE_NL
* NO_USE_SORT
* USE_CONCAT

###### Delay Function of Execution Plan

Altibase provides a function to delay the hierarchy execution of sorting, windowing, grouping, set, and distinction based on the graph of the execution plan to be executed in the fetch. The user can find out that the DELAY plan has been added under the parent PROJECTION in the execution plan.

###### IPCDA Protocol Support

IPCDA (Inter Process Communication Direct Attach) is a protocol provided by Altibase and, like IPC, uses shared memory to exchange data between the client and the database server.

IPCDA improves performance by simplifying data reading and writing, and reducing idle time between clients and servers than IPCDA.

> Constraints:
>
> Like IPC, CLI and ODBC are supported, but JDBC is not. Also, LOB data cannot be used when using IPCDA. Currently only available on Linux operating systems.

###### ACCESS LIST Management Extension

The ACCESS_LIST_FILE property was added to allow access and blocking of IP packets described in external files.

##### Resource Efficiency

###### Mempool Memory Usage Improvement

Memory allocation and fraqmentation are reduced by allocating only the necessary amount when index memory is allocated.

###### Thread Reuse

The MAX_THREAD_COUNT property used for Altibase resource restriction has been removed, and the THREAD_REUSE_ENABLE property for setting thread reuse has been added.

* THREAD_REUSE_ENABLE = 1

  It is not returned immediately at the end of the thread, but remains idle and reused. When reused, calls to the system call funciton that creates threads can be reduced, so improved performance can be expected when not reused.

* THREAD_REUSE_ENABLE = 0

  Since the thread is not reused, it is returned immediately when the thread ends. (means using the system call funciton)

###### CPU Utilization During Startup Index Rebuild

Improved CPU utilization when rebuilding the internal algorithm of job threads and queues.

Also, the default number of threads used for index building has been changed.

* INDEX_BUILD_THREAD_COUNT

###### Memory Index Reorganization Support

Altibase has reorganized the index space by consolidating the leaf nodes of the memory index. When the range of the index is larger than that of the data, space efficiency is improved when it is used when fragmentation occurs in a specifiec index.

* ALTER INDEX ... REORGANIZATION statement support

> Only memory B-tree index can be used.

#### High Availability

##### Stability of Query Execution Improvement

Altibase improved the stability of Query Execution.

#### Other

##### Other Changes

###### Method 4 of Dynamic SQL

Altibase added method 4 to dynamic SQL. This method allows the user to enter the value of parameter marker during program execution. BIND VARIABLES, SELECT LIST, and ARRAY SIZE SET functions were added, and OPEN, FETCH, and EXECUTE functions were improved.

###### Interworking Support with Hibernate

Altibase supports Hibernate's dialect class so that Altibase can provide non-standard SQL.

> Since the Hibernate offical library does not include Altibase.Dialect.class, the user needs to compile and port the AltibaseDialect.java file to use it.

###### Load Balancer Logging Function

A function to record the log of the main operation of the load balancer has been added. The log level is set through the LB_MSGLOG_FLAG property, and a related message is recorded in \$ALTIBASE_HOME/trc/altibase_lb.log.

In addition, "LB" has been added to module_name in the V\$tracelog to be searchable.

The following properties have been added for the message log of Service Thread.

* LB_MSGLOG_FLAG
* LB_MSGLOG_COUNT
* LB_MSGLOG_FILE
* LB_MSGLOG_SIZE

###### Autoextend size change of tablespace in autoextend mode ON

In order to change the autoextend size of the tablespace when autoextend mode is ON, it had to be changed after autoextend off, but it can also be changed in autoextend on mode.

###### JRE 1.5 Support

JDK, JRE 1.5 or above is supported, and JDK 1.4 and JRE 1.4 are no longer supported.

###### Windows Platform Discontinued

Starting with Altibase 7.1, Window Server and Clien are not supported.

###### DataPort Function Removed

Altibase does not support the DataPort function and utility (convdp) that can transfer data.

###### Diaster Recovery Funciton Removed

###### Shared Memory Function Not Supported

Starting with Altibase 7.1, shared memory mode is not supported. 'shmutil' management tool and properties that support shared memory are removed.

### Changes

The functions added, changed, and removed that DBAs and developers need to understand are described below: 

#### Database Version

Version by Database Component

| Altibase Version | Database Binary Version | Communication Protocol Version | Meta Version | Replication Protocol Version | Sharding Version |
| ---------------- | ----------------------- | ------------------------------ | ------------ | ---------------------------- | ---------------- |
| 6.5.1            | 6.3.1                   | 7.1.3                          | 8.1.1        | 7.4.2                        | -                |
| 7.1.0.1.2        | 6.5.1                   | 7.1.6                          | 8.5.1        | 7.4.2                        | 2.0.0            |

#### Compatibility

##### Database Binary Version

The database binary version indciates the compatibility of the database image file and log file. Since the format of the database image and log file has changed, the existing database must be migrated when upgrading the database.

| Altibase Version | Database Binary Version |
| ---------------- | ----------------------- |
| 6.5.1            | 6.3.1                   |
| 7.1.0.1.2        | 6.5.1                   |

##### Communication Protocol Version

The communication protocol version has been changed. The patch version (third digit version) has been changed, so client applications built to work with 6.5.1 are compatible with Altibase 7.1.0.1.2. In other words, there is no need to rebuild.

| Altibase Version | Communication Protocol Version |
| ---------------- | ------------------------------ |
| 6.5.1            | 7.1.3                          |
| 7.1.0.1.2        | 7.1.6                          |

##### Meta Version

The meta version has been changed. When upgrading from Altibase 6.5.1 or earlier to Altibase 7.1.0.1.2, a meta upgrade is executed automatically. However, if the user wants to roll back the upgrade, the user will have to rebuild the meta.

| Altibase Version | Meta Version |
| ---------------- | ------------ |
| 6.5.1            | 8.1.1        |
| 7.1.0.1.2        | 8.5.1        |

##### Replication Protocol Version

The replication protocol version has not been changed. Therefore, replication between Altibase 6.5.1 and 7.1.0.1.2 is possible.

| Altibase Version | Replication Protocol Version |
| ---------------- | ---------------------------- |
| 6.5.1            | 7.4.2                        |
| 7.1.0.1.2        | 7.4.2                        |

##### Sharding Version

Starting with the Altibase 7.1, sharding is provided.

> Precautions:
>
> Altibase sharding protocol and meta do not guarantee high and low compatibility. In other words, if the sharding version is different, it must be reconstructed.

| Altibase Version | Sharding Version |
| ---------------- | ---------------- |
| 7.1.0.1.2        | 2.0.0            |

#### Properties

The following properties have been added, changed, and deleted in Altibase 7.1.0.1.2. For more information on each property, please refer to the *General Reference*.

###### New Properties

* ACCESS_LIST_FILE
* DBLINK_RECOVERY_MAX_LOGFILE
* DELAYED_FLUSH_LIST_PCT
* DELAYED_FLUSH_PROTECTION_TIME_MSEC
* ILOADER_ARRAY
* ILOADER_COMMIT
* ILOADER_ERRORS
* ILOADER_PARALLEL
* IPCDA_CHANNEL_COUNT
* IPCDA_DATABLOCK_SIZE
* IPCDA_FILEPATH
* LB_MSGLOG_FLAG
* LB_MSGLOG_COUNT
* LB_MSGLOG_FILE
* LB_MSGLOG_SIZE
* LOCK_MGR_CACHE_NODE
* LOCK_MGR_DETECTDEADLOCK_INTERVAL
* LOCK_MGR_MAX_SLEEP
* LOCK_MGR_MIN_SLEEP
* LOCK_MGR_SPIN_COUNT
* LOCK_MGR_TYPE
* LOCK_NODE_CACHE_COUNT
* LOG_CREATE_METHOD
* MEM_INDEX_KEY_REDISTRIBUTION
* MEM_INDEX_KEY_REDISTRIBUTION_STANDARD_RATE
* MSG_QUEUE_PERMISSION
* OPTIMIZER_AUTO_STATS
* OPTIMIZER_DELAYED_EXECUTION
* OPTIMIZER_PERFORMANCE_VIEW
* PSM_CURSOR_OPEN_LIMIT
* PSM_CHAR_DEFAULT_PRECISION
* PSM_NCHAR_UTF8_DEFAULT_PRECISION
* PSM_NCHAR_UTF16_DEFAULT_PRECISION
* PSM_NVARCHAR_UTF8_DEFAULT_PRECISION
* PSM_NVARCHAR_UTF16_DEFAULT_PRECISION
* PSM_PARAM_AND_RETURN_WITHOUT_PRECISION_ENABLE
* PSM_VARCHAR_DEFAULT_PRECISION
* REPLICATION_DDL_ENABLE_LEVEL
* REPLICATION_SQL_APPLY_ENABLE
* REPLICATION_IB_PORT_NO
* RESULT_CACHE_ENABLE
* RESULT_CACHE_MEMORY_MAXIMUM
* TOP_RESULT_CACHE_MODE
* TABLE_LOCK_MODE
* THREAD_REUSE_ENABLE
* USER_LOCK_POOL_INIT_SIZE
* USER_LOCK_REQUEST_CHECK_INTERVAL
* USER_LOCK_REQUEST_LIMIT
* USER_LOCK_REQUEST_TIMEOUT

###### Changed Properties

* CM_DISPATCHER_SOCKET_POLL_TYPE

  EPOOL type(3) was added as a property to select the system call for socket detection in the dispatcher of the Altibase server.

  > EPOLL supports only linux, so the default value for Linux has been changed from 1(SELECT) to 3(EPOLL).

* DEFAULT_THREAD_STACK_SIZE

  Default, minimum, and maximum values have been changed.

  The default value has been changed from 3145728 (Byte) to 10485760.

  The minimum value was changed from 65536 (Bytes) to 1048576, and the maximum value was changed from 10485760 to 134217728.

* DBLINK_GLOBAL_TRANSACTION_LEVEL

  MAX value changed from 1 to 2. Previously, only 0 and 1 were supported, but 2 was added.

  * - 2:Two-Phase Commit (2PC) Level.

* EXECUTOR_FAST_SIMPLE_QUERY

  The default has been changed from 0 to 1.

* INDEX_BUILD_THREAD_COUNT

  The default number of threads used for index building has been changed. Previously, the number of CPUs in the system (the number of logical cores) was changed to the nubmer of physical cores.

* NORMALFORM_MAXIMUM

  The default value changed from 128 to 2048 (pcs).

* OPTIMIZER_AUTO_STATS

  The default value has been changed from 2 to 0 (no statistical information collected).

* REPLICATION_SYNC_TUPLE_COUNT

  In the case of replication sync, the number of processing was changed from 50,000 to 500,000.

* REPLICATION_LOG_BUFER_SIZE

  The default value has changed from 30 to 0.

* REPLICATION_PREFETCH_LOGFILE_COUNT

  The default value has changed from 0 to 3.

* REPLICATION_ACK_XLOG_COUNT

  Changed from read-only yo writable attribute.

* REPLICATION_TRANSACTION_POOL_SIZE

  The default value has changed from 1 to 2.

* XA_INDOUBT_TX_TIME

  The default value has changed from 20 to 60.

###### Removed Properties

- CHAR_DEFAULT_PRECISION
- NCHAR_DEFAULT_PRECISION
- VARCHAR_DEFAULT_PRECISION
- NVARCHAR_DEFAULT_PRECISION
- DATAPORT_FILE_DIRECTORY
- DATAPORT_IMPORT_COMMIT_UNIT
- DATAPORT_IMPORT_STATEMENT_UNIT
- DR_ENABLE
- DR_RM_PORT_NO
- DR_PORT_NO
- DR_CONNECT_TIMEOUT
- DR_RECEIVE_TIMEOUT
- DR_SENDER_SLEEP_TIME
- DR_SENDER_NEXT_CONNECTION_TIMEOUT
- DR_HBT_DETECT_TIME
- DR_HBT_DETECT_HIGHWATER_MARK
- DR_CONNECT_RECEIVE_TIMEOUT
- DR PREFETCH_LOGFILE_COUNT
- DR_KEEP_ALIVE_CNT
- DR_MAX_LOGFILE
- DR_STANDBY_WAIT_TIMEOUT
- IPC_PORT_NO
- MAX_THREAD_COUNT
- SHM_DB_KEY
- SHM_PAGE_COUNT_PER_KEY
- SHM_POLICY
- SHM_MAX_SIZE
- SHM_STARTUP_SIZE
- SHM_CHUNK_SIZE
- SHM_CHUNK_ALIGN_SIZE
- STARTUP_SHM_CHUNK_SIZE

#### Meta Table

The meta table below has been deleted.

* SYS_DATA_PORTS_

#### Performance View

The following performance views have been added.

For more informaiton on each performance view, please refer to the *General Reference*.

##### New Performance Views

- V\$ACCESS_LIST

  Performance view showing whether to allow or restrict access to specific IP packets accessing ALTIBASE.

- V$DBLINK_NOTIFIER_TRANSACTION_INFO

  Performance view showing the information of the distributed transaction with the fault that AltiLinker is processing.

- V$RESERVED_WORDS

  Performance view for querying reserved words

- V$SNAPSHOT

  Performance view showing the setting status of SNAPSHOT and the usage of memory and disk undo tablespace.

##### Modified Performance View

* V$DBLINK_LINKER_DATA_SESSION_INFO

| Column Name          | Changed History                                              |
| -------------------- | ------------------------------------------------------------ |
| LOCAL_TRANSACITON_ID | Added (INTERGER)<br />Identifier of the local transaction being performed in the current session |

* V$DBLINK_REMOTE_STATMENT_INFO

| Column Name           | Changed History                                              |
| --------------------- | ------------------------------------------------------------ |
| GLOBAL_TRANSACITON_ID | Added (INTEGER)<br />Identifier of the global transaction using the database link |

* V$DBLINK_REMOTE_TRANSACTION_INFO

| Column Name           | Changed History                                              |
| --------------------- | ------------------------------------------------------------ |
| XID                   | Added (VARCHAR(256))<br />Transaction branch identifier      |
| GLOBAL_TRANSACITON_ID | Added (INTEGER)<br />Identifier of the global transaction using the database link |

* V$DBLINK_GLOBAL_TRANSACTION_INFO

| Column Name           | Changed History                                              |
| --------------------- | ------------------------------------------------------------ |
| GLOBAL_TRANSACTION_ID | Added (INTEGER)<br />Identifier of the global transaciton using the database link |

* V$MUTEX

| Column name | Changed History                                           |
| ----------- | --------------------------------------------------------- |
| THREAD_ID   | Added (VARCHAR(64))<br />Thread ID currently holding LOCK |

* V$REPGAP

  The meaning of the column below changes in V\$REPGAP, and the value of REP_GAP becomes very large. This is because it means byte unit value.

| Column Name | Changed History                                              |
| ----------- | ------------------------------------------------------------ |
| REP_LAST_SN | Serial number of last log record -> Identificaiton number of last log record |
| REP_SN      | Serial number of the log record currently being transmitted -> Identification number of the log record currently being transmitted |

* FAILBACK EAGER, FAILBACK FLUSH, and IDLE status values have been added V\$REPSENDER's STATUS (the current status of the replication transmission thread of the local server).

| Column Name | Changed History                                              |
| ----------- | ------------------------------------------------------------ |
| STATUS      | The following status values have been added.<br />7: FAILBACK EAGER<br />8. FAILBACK FLUSH<br />9. IDLE |

* FAILBACK EAGER, FAILBACK FLUSH, AND IDLE status values have been added to V\$REPSENDER_PARALLEL's Status (the current status of the replicaiton sending thread of the local server).

| Column Name | Changed History                                              |
| ----------- | ------------------------------------------------------------ |
| STATUS      | The following status values have been added.<br />7. FAILBACK EAGER<br />8. FAILBACK FLUSH<br />9: IDLE |

* V\$SESSION

| Column name             | Changed History              |
| ----------------------- | ---------------------------- |
| ID                      | INTEGER -> BIGINT            |
| FAILOVER_SOURCE         | VARCHAR(255) -> VARCHAR(256) |
| SSL_CIPHER              | VARCHAR(257) ->VARCHAR(256)  |
| SSL_CERTIFICATE_SUBJECT | VARCHAR(257) ->VARCHAR(256)  |
| SSL_CERTIFICATE_ISSUER  | VARCHAR(257) ->VARCHAR(256)  |

* V$TRANSACTION

| Column Name     | Changed History                                              |
| --------------- | ------------------------------------------------------------ |
| ISOLATION_LEVEL | Added (INTEGER)<br />Transaction isolation level<br />0: READ COMMITED<br />1: REPEATABLE READ<br />2.SERIALIZABLE |

### Packages

| OS    | CPU                       | Archive Name                                                 |
| ----- | ------------------------- | ------------------------------------------------------------ |
| AIX   | PowerPC                   | altibase- server-7.1.0.1.2-AIX-POWERPC-64bit-release.run     |
|       |                           | altibase- client-7.1.0.1.2-AIX-POWERPC-64bit-release.run     |
| HP-UX | IA64                      | altibase- server-7.1.0.1.2-HPUX-IA64-64bit-release.run       |
|       |                           | altibase- client -7.1.0.1.2-HPUX-IA64-64bit-release.run      |
| LINUX | X86                       | altibase- server-7.1.0.1.2-LINUX-X86-64bit-release.run       |
|       |                           | altibase- client-7.1.0.1.2-LINUX-X86-64bit-release.run       |
|       | PowerPC                   | altibase- server-7.1.0.1.2-LINUX-POWERPC-64bit-release.run   |
|       |                           | altibase- client-7.1.0.1.2-LINUX-POWERPC-64bit-release.run   |
|       | PowerPCLE (Little Endian) | altibase- server-7.1.0.1.2-LINUX-POWERPCLE-64bit-release.run |
|       |                           | altibase- client-7.1.0.1.2-LINUX-POWERPCLE-64bit-release.run |

### Download

#### Package

http://support.altibase.com/en/

#### Manual

https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/eng/

#### Installation

https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/eng/Installation.md

