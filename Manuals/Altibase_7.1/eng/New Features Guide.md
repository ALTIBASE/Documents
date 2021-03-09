<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features Guide](#new-features-guide)
  - [1.New Features of Altibase Version 7.1.0.1.2](#1new-features-of-altibase-version-71012)
    - [Others](#others)
  - [2.New Features of Altibase Version 7.1.0.1.1](#2new-features-of-altibase-version-71011)
    - [Improved Features](#improved-features)
    - [Others](#others-1)
  - [3.New Features of Altibase Version 7.1.0.1.0](#3new-features-of-altibase-version-71010)
    - [Others](#others-2)
  - [4.New Features of Altibase Version 7.1.0.0.9](#4new-features-of-altibase-version-71009)
    - [Improved Features](#improved-features-1)
    - [Others](#others-3)
  - [5.New Features of Altibase Version 7.1.0.0.7](#5new-features-of-altibase-version-71007)
    - [Improved Features](#improved-features-2)
    - [Others](#others-4)
  - [6.New Features of Altibase Version 7.1.0.0.6](#6new-features-of-altibase-version-71006)
    - [Improved Features](#improved-features-3)
  - [7.New Features of Altibase Version 7.1.0.0.5](#7new-features-of-altibase-version-71005)
    - [Others](#others-5)
  - [8.New Features of Altibase Version 7.1.0.0.4](#8new-features-of-altibase-version-71004)
    - [Other](#other)
  - [9.New Features of Altibase Version 7.1.0.0.0](#9new-features-of-altibase-version-71000)
    - [Improved Features](#improved-features-4)
    - [Efficiency](#efficiency)
    - [High Availability](#high-availability)
    - [Others](#others-6)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

- Altibase®

New Features Guide
==================

![](media/NewFeatures/e5cfb3761673686d093a3b00c062fe7a.png)



Altibase New Features Guide

Release 7.1

Copyright ⓒ 2001\~2020 Altibase Corp. All Rights Reserved.

This manual contains proprietary information of Altibase Corporation; it is provided under a license agreement containing restrictions on use and disclosure and is also protected by copyright patent and other intellectual property law. Reverse engineering of the software is prohibited. All trademarks, registered or otherwise, are the property of their respective owners.

**Altibase Corp**

10F, Daerung PostTower II, 306, Digital-ro, Guro-gu, Seoul 08378, Korea Telephone: +82-2-2082-1000 Fax: 82-2-2082-1099

Customer Service Portal: http://support.altibase.com/en/

Homepage: [[http://www.altibase.com](http://www.altibase.com/)]






1.New Features of Altibase Version 7.1.0.1.2
--------------------------------------------

This chapter introduces new features available for Altibase version 7.1.0.1.2. 

### Others

#### Properties

##### Removed Properties

-   AUTO_REMOTE_EXEC

2.New Features of Altibase Version 7.1.0.1.1
--------------------------------------------

This chapter introduces new features available for Altibase version 7.1.0.1.1. 

### Improved Features

#### Meta Downgrade

If the meta version is different when deleting or roll back the patch, the user must perform the patch deletion after reconfiguring the current version of the meta with the old version of the meta. This process is called "Meta downgrade" or "downgrade".

Meta downgrade can only downgrade to the meta of the patch that last upgraded the database.

Please refer to the manual below for more information.

-   *Installation Guide* > Chapter 3. *Uninstallation Altibase and Meta Downgrade* > *Meta Downgrade*

#### UTL_COPYSWAP System Package

The UTL_COPYSWAP package provides interfaces such as table schema copy, data replication, and table exchange.

-   CHECK_PRECONDITION

-   COPY_TABLE_SCHEMA

-   REPLICATE_TABLE

-   SWAP_TABLE

-   SWAP_TABLE_PARTITION

-   FINISH

Please refer to the manual below for more information.

-   *Stored Procedures Manual* \> *Chapter 13. Altibase Storage Package* \> *Types of system package*

#### PDO Callback Function Support

Altibase added a method to write FailOver related callback funciton in application using PDO.

Please refer to the manual below for more information.

-   *Replication Manual* \> *Chapter 4. Fail-Over*

#### awrite Utility 

This is a utility that outputs the response time of the system call write() and fallocate () used when creating a log file.

Please refer to the manual below for more information.

-   *Utilities Manual \> 5. Other Utilities \> awrite*

### Others

#### Properties 

##### New Properties

-   LOG_CREATE_METHOD

3.New Features of Altibase Version 7.1.0.1.0
--------------------------------------------

### Others

#### Properties

##### New Properties

-   THREAD_REUSE_ENABLE

##### Removed Properties

-   MAX_THREAD_COUNT



4.New Features of Altibase Version 7.1.0.0.9
--------------------------------------------

This chapter introduces new features available for Altibase version 7.1.0.0.9. 

### Improved Features

#### AUTHID Option

The user can specify the permission to execute a procedure, function, or package in a stored procedure. If omitted, it executes with constructor authority and refers to the object.

-   AUTHID CURRENT_USER : User authority

-   AUTHID DEFINER: Definer authority

Please refer to the manual below for more information.

-   *Stored Procedures Manual > Chapter 2. SQL Statements for Managing Stored Procedures > CREATE PROCEDURE, CREATE FUNCTION*
  
-   *Stored Procedures Manual > Chapter 11. Stored Package > CREATE PACKAGE*

-   *General Reference > Chapter 3. The Data Dictionary > SYS_PACKAGES_, SYS_PROCEDURES\_*

#### Character Function

The following character functions have been added:

-   REGEXP_REPLACE  
    : Finds the matching string and replace it with another character or remove it.

Please refer to the manual below for more information.

-   *SQL Reference> Chapter 7. SQL Functions> Character functions*

### Others

#### autoextend off

When changing the auto-extend size of a tablespace, the size can be changed without executing 'autoextend off'.

#### Properties

##### New Properties

-   LB_MSGLOG_COUNT

-   LB_MSGLOG_FILE

-   LB_MSGLOG_FLAG

-   LB_MSGLOG_SIZE

5.New Features of Altibase Version 7.1.0.0.7
--------------------------------------------

This chapter introduces new features avaiable for Altibase version 7.1.0.0.7.

### Improved Features

#### PDO Driver

Altibase PDO driver has been added to work with Altibase in PHP applicaiton.

Please refer to the manual below for more information.

-    *API User's Manual> Chapter 2. PDO Driver*

#### SQuirreL SQL Client 

SquirreL SQL client, an open source product for DB object browsing and SQL execution, can be used in conjuction with Altibase.

Please refer to the manual below for more information.

-   Altibase 3rd Party Connector Guide

#### UTL_SMTP Package

The UTL_SMTP storage package that performs the SMTP protocl has been added so that EMAIL can be used.

Please refer to the manual below for more information.

-   *Stored Procedures Manual \> Chapter 13. Altibase Storage Package*

### Others

#### Using a FOR clauses with FETCH in Embedded SQL Statements

FOR clauses can be used with "FETCH" when using host array in embedded SQL statements. 

Please refer to the manual below for more information.

-   *Precompiler User’s Manual > Chapter 9 Using Arrays in Embedded SQL Statements> FOR Clause*

#### Performance Properties

Performance related properties have been added as below.

-   DELAYED_FLUSH_LIST_PCT: Specifies the maximum rate of the Delayed flush list.

-   DELAYED_FLUSH_PROTECTION_TIME_MSEC: This is the reference time for determining the last used page. If the last used time is below the set value, it is judged to be the last used page.

Please refer to the manual below for more information.

-   *General Reference > Chapter 2. Altibase Properties> Performance Properties*

6.New Features of Altibase Version 7.1.0.0.6
--------------------------------------------

This chapter introduces new features available for Altibase version 7.1.0.0.6.

### Improved Features

#### Mitigation Replication Constraints and SQL Reflection Mode 

Replication is supported even if the column type, primary key, and NOT NULL constraint of the table to be replicated on both servers are not the same. 

SQL Reflection Moe : When meta information of local server and remote server is different, this mode is converted to SQL and reflected to the remote server that receives XLog. When the value of the REPLICATION_SQL_APPLY_ENABLE property of the receiver is 1, in the LAZY mode, a table without a security column can be used as the SQL reflection mode.

Please refer to the manual below for more information.

-   *Replication \> Chapter 3. Using Replicaiton \> Replication Constraint, SQL Reflection Mode*

-   *jdbcAdapter \> 3. Usage Instruction \> jdbcAdapter Constraints*

-   *oraAdapter \> 3. Usage Instruction \> oraAdapter Constraints*

7.New Features of Altibase Version 7.1.0.0.5
--------------------------------------------

This chapter introduces new features available for Altibase version 7.1.0.0.5. 

### Others

#### Properties

##### Changed Properties

The default values of these properties below have been changed:

-   DEFALUT_THREAD_STACK_SIZE  
    : 3145728 (Byte) --\>10485760

8.New Features of Altibase Version 7.1.0.0.4
--------------------------------------------

This chapter introduces new features available for Altibase version 7.1.0.0.4. 

### Other

#### Properties

##### Changed Properties

The following properties have been changed.

-   REPLICATION_ACK_XLOG_COUNT  
    :Read-Only --> Read-Write

9.New Features of Altibase Version 7.1.0.0.0
--------------------------------------------

This chapter introduces new features available for Altibase version 7.1.0.0.0. 

This chapter consists of the following sections:

-   Improved Features
-   Efficiency
-   High Availability
-   Others

### Improved Features

#### SQL Extension

##### Conversion of Non-Partitioned table and Partitioned table(Partition Exchange)

CONJOIN TABLE: This statement controls converting a non-partitioned table into a partition of a table. The list partition and range partition are supported, but the hash partitioned is not supported. All the data created in the target table is transferred to the created partition.

DISJOIN TABEL: The user can use this statement to convert a partition in a partitioned table into a non-partitioned table. The hash partition is not supported whereas the existing partition attributes of the non-partitioned table remain the same.

Please refer to the manual below for more information.

-   *SQL Reference > Chapter 3. Data Definition Language> CONJOIN TABLE, DISJOIN TABLE*


##### Modifying Tablespace of Table 

The tablespace storage of tables can transfer concurrently along with indexes and LOB columns. However, in a partitioned table, you can only move records from one partition, so you must perform multiple DDLs to move records across all partitions.

Please refer to the manual below for more information.

-   *SQL Reference > Chapter 3. Data Definition Lauguagae > ALTER TABLE* 
-   *Getting Started Guide > Chapter 6.Database Replication > Executing DDL Statements in a Replication Environment* 
-   *Replication Manual > Chapter.3 Deploying Replication > Executing DDL Statement on Replication Target Tables*

##### User-defined Columns in a Queue

The user can define a column when creating a queue.

Please refer to the manual below for more information.

-   *SQL Reference > Chapter 3. Data Definition Language > CREATE QUEUE*

##### Syntax extension of COMPACT and AGING 

COMPACT and AGING statements can be executed on a partitioned table by a partition unit.

Please refer to the manual below for more information.

-   *SQL Reference > Chapter 3. Data Definition Language > ALTER TABLE*

##### NOWAIT and WAIT Options 

NOWAIT and WAIT options has been supported in the INSERT, FOR UPDATE, and DEQUEUE statements. The time unit can be specified in the WAIT option is second(sec), millisecond(msec, 1/1000 sec), and microsecond (μsec, 1/1000000 sec).The second is applied unless otherwise specified.

Please refer to the manual below for more information.

-   SQL Reference > Chapter 3. Data Definition Language > INSERT, SELECT, DEQUEUE


##### NOCOPY option

The NOCOPY is provided as an option for parameters and local variables in stored procedure and stored function to use call by reference method. It is only supported for ASSOCIATIVE ARRAY type.

Please refer to the manual below for more information.

-   Stored Procedures Manual > Chapter 2. SQL Statements for Managing Stored Procedures

##### Overloading of Package Subprogram

Overloading of package subprogram is supported. In other words, package subprograms can be defined with the same name if their parameters or data types are different. 

Please refer to the manual below for more information.

-   *Stored Procedures Manual > Chapter 13. Altibase Stored Packates*

##### Supporting BULK COLLECTION in FETCH syntax

BULK COLLECT INTO function is supported in the FETCH statement in stored procedure and stored function.

Please refer to the manual below for more information.

-   *Stored Procedures Manual > Chapter 5. Using Cursors > FETCH* 

**Static SQL available for using Cursor**

In the OPEN FOR statement, the user can use static SQL as well as dynamic SQL. Static SQL cannot be used with the USING clause.

Please refer to the manual below for more information.

-   *Stored Procedures Manual > Chapter 8. Dynamic SQL > OPEN FOR* 

#####  Autonomous Transation and Exception Initializing Pragma

Autonomous Transaction(Autonomous_Transaction) pragma and Execption Initialization (Exception_Init Pragma) pragma are supported. 

Autonomous_Transaction pragma enables a stored module like stored procedure, stored function, stored package to independentaly operate within a transaction. Exception_Init pragma initializes exception variables in a stored module with an Altibase error code. 

Please refer to the manual below for more information.

-   *Stored Procedures Manual > Chapter 10. Pragma*

##### Aggregate functions and Windows functions

Various functions such as, the percentage rank, ratio analysis functions, cumulative distribution of a group, array functions, sort functions, coefficient of correlation, sample covariance, and population distribution are supported in the aggregate functions and window functions as below:

-   PERCENT_RANK

-   CUME_DIST

-   RATIO_TO_REPORT

-   NTILE

-   CORR

-   COVAR_SAMP

-   COVAR_POP

-   FIRST

-   LAST

Please refer to the manual below for more information.

-   *SQL Reference> Chapter 7. SQL Functions> Aggregate Functions, Analytic Functions*


##### User Lock functions

The following functions are supported in an attempt to request or release the user lock. 

-   USER_LOCK_REQUEST

-   USER_LOCK_RELEASE

The added properties are as follows.

-   USER_LOCK_POOL_INIT_SIZE

-   USER_LOCK_REQUEST_CHECK_INTERVAL

-   USER_LOCK_REQUEST_LIMIT

-   USER_LOCK_REQUEST_TIMEOUT

Please refer to the manual below for more information.

-   *SQL Reference> Chapter 7. SQL Functions> Other Functions* 

##### VARBYTE Data Type and Function Support

VARBYTE is supported to support binary data types with variable length. In addition, the following functions were added to convert various types of data types to VARBYTE data types or VARBYTE data types to other data types.

-   RAW_SIZEOF

-   TO_RAW

-   RAW_TO_NUMERIC

-   RAW_TO_FLOAT

-   RAW_TO_INTEGER

-   RAW_CONCAT

-   SUBRAW

-   RAW_TO_VARCHAR

Please refer to the manual below for more information.

-   *General Reference \> Chapter 1. Datatype \> Compatible with Binary Data Type, Data Type Conversion*

-   *SQL Reference\> Chapter 7. SQL Funcitons*

-   *Precompiler \> Chapter 5. Host Variable Data Type \> Extended Data Type*

-   *Precompiler \> Chapter 5. Host Variable Data Type \> Column Type and Host Variable Type*

##### Other functions

The following function returns the context information of the current database session.

-   SYS_CONTEXT

The functions returning the VARBYTE type character strings through encoding or decoding are supported as follows: 

-   BASE64_DECODE

-   BASE64_ENCODE

Altibase supports functions which can return VARBAYTE type character strings either by decoding or encoding the VARBYTE type character strings that were converted to Quoted printable format. The functions include as follows:

-   QUOTE_PRINTABLE_DECODE

-   QUOTE_PRINTABLE_ENCODE

The following functions are provided to support the database-level message queue functionality. These functions do not belong to a specific schema:

-   MSG_CREATE_QUEUE

-   MSG_DROP_QUEUE

-   MSG_SND_QUEUE

-   MSG_RCV_QUEUE

Please refer to the manual below for more information.

-   *SQL Reference\> Chapter 7. SQL Functions \> Other Functions*

##### 'UNTIL NEXT DDL' in LOCK TABLE 

With 'UNTIL NEXT DDL' specified in a NON-AUTOCOMMIT session, COMMIT will be automatically executed before DDL(Data Definition Language) execution. However, if EXCLUSIVE lock mode is specified in the session, COMMIT will not be executed automatically before the DDL execution.

Please refer to the manual below for more information.

-   *SQL Reference> Chapter 4. Data Manipulation Language> LOCK TABLE* 

##### ENABLE and DISABLE functions

The user can set ENABLE or DISABLE status when creating triggers. The use can change the status using ALTER TRIGGER. 

Please refer to the manual below for more information.

-   *SQL Reference> Chapter 3. Data Definition Language > CREATE TRIGGER* 

##### Extension of COMPACT clause

The maximum size of page compression can be specified when using a query statement with ALTER TABLE table_name COMPACT.

Please refer to the manual below for more information.

-   *SQL Reference> Chapter 3. Data Definition Language > ALTER TABLE* 

##### TOUCH Statement 

Using the TOUCH clause increases the SCN(System Commit Number) of the table, thereby forcing the optimizer to recreate the execution plan of the query containing the table

Please refer to the manual below for more information.

-   *SQL Reference> Chapter 3. Data Definition Language > ALTER TABLE* 

##### Session Close

The user name can be specified with ALTER DATABASE statement to terminate a session, and all sessions can be terminated at once with ALL statement.

Please refer to the manual below for more information.

-   *SQL Reference > Ch.3 Data Definition Language > ALTER DATABASE*

##### Newly Spatial Object Creation Functions 

Spatial object creation functions for spatial data was added. 

-   RECTFROMTEXT : Creates polygon objects by receiving RECTANGLE spatial objects in the form of WKT (Well-Known Text)
  
-   RECTFROMWKB : Creates polygon objects by receiving RECTANGLE spatial objects in the form of WKB (Well-Known Binary)

Please refer to the manual below for more information.

-   *Spatial SQL Reference > Ch.2 Spatial SQL > Spatial Object Creation Functions* 

##### CONNECT BY

When using an index in a CONNECT BY node used for hierarchical query, the output has been changed.

-   *CONNECT BY ( INDEX: index_name, ACCESS: acc_num, COST: cost )*

Please refer to the manual below for more information.

-   *TuningGuide \> 4. Using EXPLAIN PLAN \> Execution Node \> CONNECT BY*

#### Application Development Interface Extensions and Improvements

##### JDBC Logging

JDBC Logging indicates recording of all sorts of logs occurring in the Altibase JDBC driver, and the relevant logs can be stored by using java.util.logging package.

Please refer to the manual below for more information.

-   *JDBC User’s Manual > Chapter 3. Advanced Functions > JDBC Logging* 

#### Data Types

##### Support for Date format 

Altibase supports 'WW2' data format that returns which week of the year regardless of the date. It begins with the 1st of January and it is distinguished by 7 days unit. The last week is the 53th week.

In addition, date types for Julian calendar and BC dates are newly added as below.

-   SYYYY : Marks the BC years

-   SCC : Marks the BC centuries 

Please refer to the manual below for more information.

-   *General Reference> Chapter 1. Data Type> Date Date Types*

#### Built-in Function

##### DBMS Stats Functions

A built-in function has been added to copy partition statistics

-   COPY_TABLE_STATS

Please refer to the manual below for more information.

-   Stored Procedures Manual\> Chapter 12. Altibase Stored Procedures and Built-in Functions \> DBMS Stats

##### Other Functions

Stored procedures for setting V\$SESSION information has been added.

-   SET_CLIENT_INFO

-   SET_MODULE

Please refer to the manual below for more information.

-   *Stored Procedures Manual\> Chapter 12. Altibase Stored Procedures and Built-in Functions > Other Functions*

#### Client Tools

##### Improved altimon.sh

The altimon.sh has been enhanced in order to efficiently monitor the Altibase server and the host system in which the altiMon is installed. altiMon primarily monitors OS information and DB information. The operating system is required to have PICL library to gather the OS information.

In order to use altiMon, config.xml, Metrics.xml, and GroupMetrics.xml files located under the $ALTIBASE_HOME/altiMon/conf directory should be properly configured.

Please refer to the manual below for more information.

-   *Utilities Manual\> Chapter 4. Other Utilities \> altimon.sh*

##### Host Variable 

The default value of declared host variables has been modified. 

Please refer to the manual below for more information.

-   *iSQL User's Manual > Chapter 2. Examples of iSQL in Use > Host Variables > Declaring a Host Variables* 

##### Substitution variable when using iSQL

This tool helps parameters be input when executing a script file with the substitution variable by using START command in iSQL. SET DEFINE ON should be executed in order to use the substitution variables. 

Please refer to the manual below for more information.

-   *iSQL Users' Manual> Chapter 1 Using iSQL> iSQL Commands* 
-   *iSQL User's Manual> Chapter 2 Examples of iSQL in Use. > File management*

##### New iSQL command 

In iSQL, commands to set the display format of columns corresponding to the SELECT result have been added:

-   SET NUMF[ORMAT] : This command configures the display format of numeric data type. 
-   COLUMN : This command configures the display format for columns of character or numeric type. 
-   CL[EAR] COL[UMNS] : This removes all the columns configured by the COLUMN command. 
-   SET VERIFY: This command specifies whether or not to display SQL statements before and after replacing the substitution value with the parameter value inserted by a user when executing a script file containing substitution variables. The default value is set to ON and it signifies displaying SQL statements.

Please refer to the manual below for more information.

-   *iSQL User's Manual > Chapter 1. How to Use iSQL > iSQL Commands* 
-   *iSQL User's Manual > Chapter 2. iSQL Examples > Formatting SELECT Query Results* 

##### --prefetch_rows option of iLoader utility

iLoader utility newly supports -prefetch_rows option in the out mode. This specifies the number of records that can be fetched from the database at once. The default value is 0 which is the maximum size in which the network packet can be transferred.

Please refer to the manual below for more information.

-   *iLoader User's Manual > Chapter 2. Using iLoader > Command-line option* 
-   *iLoader User's Manual > Chapter 2. Using iLoader > General Option*

##### Partition Information Output

The DESC command allows to view partition information when viewing the table structure.

Please refer to the manual below for more information.

-   *iSQL User's Manual > Chapter 1. Using iSQL > iSQL Command-Line Option* 
-   *iSQL User's Manual > Chapter 2. Examples of iSQL in Use> Formatting SELECT query results*

##### aexport Property

The following properties of aexport utility have been added.

-   ILOADER_ARRAY: This property specifies the number of rows which will be executed all at once when uploading or downloading data with iLoader.
  
-   ILOADER_COMMIT: This property specifies the unit(number) to commit when uploading or downloading data with iLoader.

-   ILOADER_ERRORS: This property specifies the maximum number of allowable errors when uploading data with iLoader.
  
-   ILOADER_PARALLEL:  This property specifies the number of concurrent threads which will be executed parallelly when uploading or downloading data with iLoader.

Please refer to the manual below for more information.

-   *Utilities Manual > Chapter 1. How to Use aexport> aexport properties*

##### dataCompJ

When replicating data from the Altibase database to a heterogeneous database, dataCompJ has been added as a utility to verify the data consistency and resolve the data inconsistencies.

Please refer to the manual below for more information.

-   *Utilities Manual > Chapter 3. dataComJ*

##### Asynchronous Prefetch Attributes

Asynchronous prefetch attributes are newly added as below

-   async_prefetch off\| on\| auto (off default value) : Used with OUT command

-   ILOADER_ASYNC_PREFETCH = ON\| OFF\|AUTO

Please refer to the manual below for more information.

-   *iLoader User’s Manual \> 2. How to use iLoader*

-   *Utilities Manual\> 1. aexport \> How to use aexport*

### Efficiency

#### Enhanced Server Performance

##### Newly Added Packages

The system-defined stored packages newly added in Altibase are as follows:

-   DBMS_ALERT: The DBMS_ALERT package informs and provides an alert to other users with the support of an interface form in regards to various database events.
  
-   DBMS_APPLICATION_INFO  
     The DBMS_APPLICATION_INFO package configures the performance view in order to manage information of clients' application.

-   DBMS_CONCURRENT_EXEC  
    The procedure cannot be concurrently executed. 

-   DBMS_LOCK  
    The DBMS_LOCK package provides an interface for user to request lock/unlock. 

-   DBMS_OUTPUT  
    The DBMS_OUPUT allows a user to output a string stored in the buffer to clients.

-   DBMS_RANDOM  
    The DBMS_RANDOM package creates random numbers.

-   DBMS_SQL  
    The DBMS_SQL package provides procedures and functions to use dynamic SQL

-   DBMS_STATS  
    The DBMS_STATS package provides an Sub-programs to use various database statistical information. 

-   DBMS_RECYCLEBIN  
    The DBMS_RECYCLEBIN package can completely purge tables, which have been dropped and managed in the recycle bin, from the entire system.
    
-   DBMS_UTILITY  
    The DBMS_UTILITY package provides various utility functions and procedures.

-   STANDARD : The STANDARD package defines the types that can be used in the PSM without any additional declarations other than the basic data types.
  
-   UTL_FILE  
    The UTL_FILE package can access to text files, which are managed by the operating system, and read and write them.

-   UTL_RAW  
    The UTL_RAW package can convert or alter RAW(VARBYTE) type data into a different data type.

-   UTL_TCP  
    The UTL_TCP package controls TCP access in the stored procedure

For in-depth contents and information on the package procedures and functions, please refer to the following manual.

-   *Stored Procedures Manual > Chapter13. Altibase Stored Packages*

##### Result Cache

By using the Result Cache, the intermediate result or the final result of initially executed query can be stored so that the results can be reused when executing the same query. 

The following hints have been added for Result Cache:

-   RESULT_CACHE

-   TOP_RESULT_CACHE

The following properties in relation to the Result Cache have been added.

-   RESULT_CACHE_ENABLE

-   RESULT_CACHE_MEMORY_MAXIMUM

-   TOP_RESULT_CACHE_MODE

Please refer to the manual below for more information.

-   *General Reference > Chapter 2. Altibase Properties> Performance Properties* 
-   *SQL Reference > Chapter 2. Altibase SQL Basics> Hint List* 
-   *Performance Tuning Guide > Chapter 6. SQL Hints> Types of Hints* 
-   *Performance Tuning Guide > Chapter 7. SQL Plan Cache > Result Cache-related Properties*

##### Two-Phase Commit(2PC)Level of DBLink 

DB Link provides 2PC protocol to ensure interoperable compatibility of the global transaction conducted between other database system and the Altibase. 

Altibase and remote database system perform the two-phase commit exchanging messages following the 2PC protocol after the DBLINK_GLOBAL_TRANSACTION_LEVEL property is set to the two-phase commit level. 

The following properties are added and modified. in relation to ensuring the consistency of distributed transactions:

-   DBLINK_RECOVERY_MAX_LOGFILE

-   DBLINK_GLOBAL_TRANSACTION_LEVEL

The added and modified performance views related to the consistency of distributed transactions are as follows:

-   V\$DBLINK_NOTIFIER_TRANSACTION_INFO

-   V\$DBLINK_LINKER_DATA_SESSION_INFO

-   V\$DBLINK_GLOBAL_TRANSACTION_INFO

-   V\$DBLINK_REMOTE_STATEMENT_INFO

-   V\$DBLINK_REMOTE_TRANSACTION_INFO

-   V\$SESSION

Please refer to the manual below for more information.

-   *General Reference > Chapter 2. Altibase Properties > Performance Properties* 
-   *General Reference > Chapter 3. The Data Dictionary* 
-   *Database Link User’s Manual > Chapter 1. Introduction to Database Link* 
-   *Database Link User’s Manual > Chapter 3 Configuration of Database Link* 
-   *Database Link User’s Manual > Chapter 4. Database Link-Related SQL Statments* 

##### Automatic Database Statistics

Statistical information that can be used by the optimizer can be collected automatically.

The following properties are added in relation to automatic statistics collection:

-   OPTIMIZER_AUTO_STATS

Please refer to the manual below for more information.

-   General Reference > Chapter 2. Altibase Properties > Performance Properties 
-   Performance Tuning Guide > Chapter 5. The Optimizer and Statistics > Managing Statistics 

##### Additional Hints

In Altibase 7.1, various and advantageous hints, such as Normalization code, join methods, table access methods, and parallel query execution have been added. 

The following properties have been added:

-   INDEX_ASC

-   INDEX_DESC

-   LEADING

-   NO_EXPAND

-   NO_INDEX

-   NO_PARALLEL

-   NO_USE_HASH

-   NO_USE_MERGE

-   NO_USE_NL

-   NO_USE_SORT

-   USE_CONCAT

Please refer to the manual below for more information.

-    *Performance Tuning Guide > Chapter 6. SQL Hints > Types of Hints* 
-   *SQL Reference > Chapter 2. Altibase SQL Basics > Hint List* 

##### Delay on Execution Plans

Query execution can be delayed until the first fetch is performed for hierarchy, sorting, windowing, grouping, set, and distinction queries. The user can check the added DELAY plan under the top PROJECTION in the execution plan.

The following property is newly included with regards to query execution delay.

-   OPTIMIZER_DELAYED_EXECUTION

The property related to result cache property has been added as follows.

-   NO DELAY

-   DELAY

Please refer to the manual below for more information.

-   *General Reference > Chapter 2. Altibase Properties > Performance-related Properties* 
-   *Performance Tuning Guide > Chapter 6. SQL Hints > Type of Hints*
-   *SQL \> Chapter 2. Altibase SQL Basics \> Hint List*

##### IPCDA Protocol

IPCDA(Inter Process Communication Direct Attach) is a protocol provided by Altibase to exchange data between the server and client by using shared memory. IPCDA can produce much advanced performance by reducing idle time between the server and client as well as simplifying data reading and writing.

CLI and OBDB is supported, but JDBC is not supported. Besides, LOB data cannot be used when using IPCDA. IPCDA is only supported on Linux. The following properties should be configured to use IPCDA.

To communicate using IPCDA, the following IPCDA-related server properties must be set.

-   IPCDA_CHANNEL_COUNT

-   IPCDA_DATABLOCK_SIZE

-   IPCDA_FILEPATH

Please refer to the manual below for more information.

-   *Administration's Manual > Chapter 1. Introduction > Altibase Features* 
-   *Administration's Manual > Chapter 2. Altibase Components > trc Directory* 
-   *Administration's Manual >Chapter 12. Communication Layer > Communication Protocols* 
-   *General Reference > Chapter 2. Altibase Properties > Session Properties* 
-   *iSQL User's Manual > Chapter 1. Using iSQL > Setting Up iSQL* 
-   *iSQL User's Manual > Chapter 1. Using iSQL > iSQL Environment Variables*

##### ACCESS_LIST Management Extension

ACCESS_LIST_FILE property has been added to specify an external file to set access information for certain IP addresses. When it is specified, ACCESS_LIST in the altibase.properties file will be ignored. 

Up to 1024 items can be used, and the contents of 'ACCESS_LIST' are omitted and only the contents are written.

The added property is as follows.

-   ACCESS_LIST_FILE

The added performance views is as follows.

-   V\$ACCESS_LIST

Please refer to the manual below for more information.

-   *General Reference > Chapter 2. Altibase Properties > Other Properties* 
-   *General Reference > Chapter 3 Data Dictionary > V$ACCESS_LIST* 
-   *SQL Reference > Chapter 5. Data Control Language > ALTER SYSTEM*

##### Support Buffer for minimizing the data loss of replication  

Buffer is supported for minimizing the data loss of replication. When the network is shut down after saving a certain amount of xlog, apply the xlog stored in the buffer and terminated.

Please refer to the manual below for more information.

-   *Replication Manual > Chapter 3. Deploying Replication > Extra Features*

#### Resource Efficiency

**Reorganization of Memory Index **

The user can reorganizes the index space through integration of leaf nodes in memory index. This function ensures high space efficiency especially when the index range is relatively greater than that of the data, or there is an occurrence of index fragmentation on a particular index.

The following properties are newly added to this release:

-   MEM_INDEX_KEY_REDISTRIBUTION

-   MEM_INDEX_KEY_REDISTRIBUTION_STANDARD_RATE

Please refer to the manual below for more information.

-   *General Reference > Chapter 2. Altibase Properties > Performance-related Properties* 
-   *SQL Reference > Chapter 3. Data Definition Language > ALTER INDEX*

### High Availability

#### Hybrid Partitioned Table

Hybrid partitioned tables are supported in Altibase 7.1, and the partitioned table can transfer data from disk tablespace to memory/volatile tablespace, and vice versa; however, global indexes are not supported. 

Please refer to the manual below for more information.

-   *Administrator's Manual > Chapter 7. PartitionedObjects> Partitioned Objects, Partitioning Methods* 
-   *SQL Reference > Chapter 3. Data Definition Language > ALTER TABLE* 
-   *Replication Manual> Chapter 3. Deploying Replication> Executing DDL Statements on Replication Target Tables* 
-   *Getting Started Guide > Chapter 6. Database Replication > Executing DDL Statements in a Replication Environment* 

#### Specifying the size of PSM character data 

Properties that can determine the size of character data type used in the stored procedures and the stored functions have been added as indicated below:

-   PSM_CHAR_DEFAULT_PRECISION

-   PSM_NCHAR_UTF8_DEFAULT_PRECISION

-   PSM_NCHAR_UTF16_DEFAULT_PRECISION

-   PSM_NVARCHAR_UTF8_DEFAULT_PRECISION

-   PSM_NVARCHAR_UTF16_DEFAULT_PRECISION

-   PSM_PARAM_AND_RETURN_WITHOUT_PRECISION_ENABLE

-   PSM_VARCHAR_DEFAULT_PRECISION

The properties specifying the basic size of character type data have been removed as follows:

-   CHAR_DEFAULT_PRECISION

-   NCHAR_DEFAULT_PRECISION

-   NVARCHAR_DEFAULT_PRECISION

-   VARCHAR_DEFAULT_PRECISION

Please refer to the manual below for more information.

-   *General Reference> Chapter 1. Data Types> Character Data Types* 
-   *General Reference > Chapter 2. Altibase Properties > Other Properties*

#### REMOTE Functions for Batch Process

Remote function and the related functions have been added for the database links to execute batch queries. The functions can be used only within the stored procedures. 

-   IS_ARRAY_BOUND

-   IS_FIRST_ARRAY_BOUND

-   IS_LAST_ARRAY_BOUND

-   REMOTE_ADD_BATCH

-   REMOTE_ALLOC_STATEMENT_BATCH

-   REMOTE_BIND_VARIABLE_BATCH

-   REMOTE_EXECUTE_BATCH

-   REMOTE_FREE_STATEMENT_BATCH

-   REMOTE_GET_RESULT_COUNT_BATCH

-   REMOTE_GET_RESULT_BATCH

Please refer to the manual below for more information.

-   *Database Link User’s Manual > Chapter 4. Database Link-Related SQL Statements*

#### Snapshot Backup

The snapshot backup is configured based upon at the point of time when BEGING SNAPSOT is executed, and data can be exported with iLoader standing on the pertaining SCN.

Only the DBA with SYSDBA privilege can set up or disable the snapshot. 

The following properties have been newly added this time.

-   SNAPSHOT_DISK_UNDO_THRESHOLD

-   SNAPSHOT_MEM_THRESHOLD

The following performance view has been included.

-   V\$SNAPSHOT

Please refer to the manual below for more information.

-   *Admin > Chapter 10. Backup and Recovery > SNAPSHOT Backup* 
-   *SQL > Chapter 3. Data Definition Language > ALTER DATABASE* 
-   *General Reference > Chapter 2. Altibase Properties > Backup and Recovery Properties* 
-   *General Reference > Chapter 3. The Data Dictionary > Performance Views*

#### jdbcAdapter 

jdbcAdapter is a utility that can apply changed data in Altibase to other JDBC supported databases.

It can be used with Altibase 6.3.1 or later, or with other databases using JDBC 4.1 or earlier. jdbcAdapter only supports the Linux operating system.

Please refer to the manual below for more information.

-   *Adapter for JDBC User’s Manual* 

### Others

#### Other Changes

##### Table Function

The TABLE FUNCTION transforms associative array type or record type variables returning from user defined functions into a table format and output them;; however, this is not a function.

Please refer to the manual below for more information.

-   *SQL Reference > Chapter 4. Data Manipulation Language > SELECT*

##### Dynamic SQL Method 4 

Dynamic SQL Method 4 has been added in Altibase Precompiler. This method allows the user to set parameter markers at runtime when exeucting the program instead of when compiling it. Functions, such as BIND VARIABLES, SELECT LIST, and ARRAY SIZE SET have been added in 7.1 and OPEN, FETCH, and EXECUTE functions have been much improved.

Please refer to the manual below for more information.

-   *Precompiler User’s Manual > Chapter 10. Dynamic SQL Statments > Using Dynamic SQL Statements*

##### CLOSE Statement for Precompile Cursors

A cursor in the OPEN state can be re-opened without the CLOSE execution, which is identical to OPEN after executing CLOSE.

Please refer to the manual below for more information.

-   *Precompiler User’s Manual > Chapter 8. Using Cursors > Cursor-Related SQL Statements.*

##### Interworking Support with Hibernate

Hibernate dialect class is supported for Altibase to provide non-standard SQL. Since the official Hibernate library does not include AltibaseDialect.class, AltibaseDialect.java file should be compiled and ported in order to use.

Please refer to the following manual and Altibase Github website for in-depth information.

-   https://github.com/ALTIBASE/hibernate-orm/
-   *JDBC User’s Manual > Chapter 3. Advanced Functions > Hibernate*

##### Support for JRE 1.5

JDK and JRE 1.5 or above is supported.

##### Asynchronous Prefetch Properties

Asynchronous prefetch-related attributes have been added to the CLI function below.

-   SQLDriveConnect  
    : SOCK_RCVBUF_BLOCK_RATIO

-   SQLGetConnectAttr  
    : ALTIBASE_SOCK_RCVBUF_BLOCK_RATIO

-   SQLSetConnectAttr  
    : ALTIBASE_SOCK_RCVBUF_BLOCK_RATIO

-   SQLSetStmtAttr  
    : ALTIBASE_PREFETCH_ASYNC  
    : ALTIBASE_PREFETCH_AUTO_TUNING

Asynchronous prefetch-related properties have been added to the JDBC driver.

-   sock_rcvbuf_block_ratio

-   fetch_async

-   fetch_auto_tuning

Please refer to the manual below for more information.

-   *CLI User’s Manual > 2. Altibase CLI functions* 
-   *JDBC User’s Manual > 2. Altibase CLI functions*

##### DB Link Properties

A property which can specify JVM bit(32/64) in DB Link has been included as follows.

-   ALTILINKER_JVM_BIT_DATA_MODEL_VALUE

##### CLI Functions Properties

The ALTIBASE_PREPARE_WITH_DESCRIBEPARAM attribute has been added to the CLI function below to reduce network I / O cost.

Please refer to the manual below for more information.

-   *CLI Manual \> Chapter 2. Altibase CLI Functions \> SQLSetStmtAttr*

#### Dropped or Changed Properties

##### Windows platform discontinued

Starting with Altibase 7.1, Windows Server and Client are not supported.

##### Removed DataPort feature

Altibase does not support the DataPort function and utility (convdp) that can transfer data.

##### Shared Memory Function Not Supported

Shared memory mode is not supported since 7.1.

Delete the management tool 'shmutil' that supports shared memory and the following properties.

-   SHM_DB_KEY

-   SHM_PAGE_COUNT_PER_KEY

-   STARTUP_SHM_CHUNK_SIZE

##### Removed Failover Attributes

The following connection properties related to Failover have been removed:

-   LoadBalance

-   HealthCheckDuration

Please refer to the manual below for more information.

-   *Replication Manual \> Chapter 4. Fail-Over*

-   *JDBC User's Manual \> Chapter 1. Getting started with JDBC*

-   *JDBC User's Manual \> Chapter 3. Advanced Features*

#### Properties

##### Newly Added Properties

The following properties are newly added to this release.

-   ACCESS_LIST_FILE

-   DBLINK_RECOVERY_MAX_LOGFILE

-   EXTPROC_AGENT_SOCKET_FILEPATH

-   IPCDA_CHANNEL_COUNT

-   IPCDA_DATABLOCK_SIZE

-   IPCDA_FILEPATH

-   LOCK_MGR_CACHE_NODE

-   LOCK_MGR_DETECTDEADLOCK_INTERVAL

-   LOCK_MGR_MAX_SLEEP

-   LOCK_MGR_MIN_SLEEP

-   LOCK_MGR_SPIN_COUNT

-   LOCK_MGR_TYPE

-   LOCK_NODE_CACHE_COUNT

-   MEM_INDEX_KEY_REDISTRIBUTION

-   MEM_INDEX_KEY_REDISTRIBUTION_STANDARD_RATE

-   MSG_QUEUE_PERMISSION

-   OPTIMIZER_AUTO_STATS

-   OPTIMIZER_DELAYED_EXECUTION

-   OPTIMIZER_PERFORMANCE_VIEW

-   PSM_CURSOR_OPEN_LIMIT

-   PSM_CHAR_DEFAULT_PRECISION

-   PSM_NCHAR_UTF8_DEFAULT_PRECISION

-   PSM_NCHAR_UTF16_DEFAULT_PRECISION

-   PSM_NVARCHAR_UTF8_DEFAULT_PRECISION

-   PSM_NVARCHAR_UTF16_DEFAULT_PRECISION

-   PSM_PARAM_AND_RETURN_WITHOUT_PRECISION_ENABLE

-   PSM_VARCHAR_DEFAULT_PRECISION

-   RESULT_CACHE_ENABLE

-   RESULT_CACHE_MEMORY_MAXIMUM

-   REPLICATION_SENDER_SEND_TIMEOUT

-   SNAPSHOT_DISK_UNDO_THRESHOLD

-   SNAPSHOT_MEM_THRESHOLD

-   TABLE_LOCK_MODE

-   TOP_RESULT_CACHE_MODE

-   USER_LOCK_POOL_INIT_SIZE

-   USER_LOCK_REQUEST_CHECK_INTERVAL

-   USER_LOCK_REQUEST_LIMIT

-   USER_LOCK_REQUEST_TIMEOUT

##### Removed Properties

The following properties have been removed in this release.

-   AUTODETECT_UNIQ_INX

-   CHAR_DEFAULT_PRECISION

-   DATAPORT_FILE_DIRECTORY

-   DATAPORT_IMPORT_COMMIT_UNIT

-   DATAPORT_IMPORT_STATEMENT_UNIT

-   IPC_PORT_NO

-   NCHAR_DEFAULT_PRECISION

-   NVARCHAR_DEFAULT_PRECISION

-   SHM_DB_KEY

-   SHM_PAGE_COUNT_PER_KEY

-   STARTUP_SHM_CHUNK_SIZE

-   VARCHAR_DEFAULT_PRECISION

##### Changed Properties

The default values of the properties below have been changed.

-   DEFALUT_THREAD_STACK_SIZE  
    : 1048576 --\> 3145728 (Byte)

-   REPLICATION_LOG_BUFFER_SIZE  
    : 30 --\> 0(MB)

-   REPLICATION_PREFETCH_LOGFILE_COUNT  
    : 0 --\> 3

-   OPTIMIZER_AUTO_STATS  
    : 2--\>0 (Do not collect statistical information)

-   NORMALFORM_MAXIMUM  
    : 128 --\> 2048(Counts)

#### Meta Table

##### Removed Meta Table

The meta tables deleted in this release are as follows.

-   SYS_DATA_PORTS\_

#### Performance View 

The performance views added in this release are as follows.

-   V\$ACCESS_LIST

-   V\$DBLINK_NOTIFIER_TRANSACTION_INFO

-   V\$RESERVED_WORDS

-   V\$SHANPSHOT

The performance views modified in this release are as follows.

-   V\$DBLINK_LINKER_DATA_SESSION_INFO

-   V\$DBLINK_GLOBAL_TRANSACTION_INFO

-   V\$DBLINK_REMOTE_STATEMENT_INFO

-   V\$DBLINK_REMOTE_TRANSACTION_INFO

-   V\$MUTEX: THREAD_ID Added

-   V\$REPSENDER

-   V\$REPSENDER_PARALLEL

-   V\$SESSION

-   V\$TRANSACTION : ISOLATION_LEVEL to indicate transaction isolation level is added.


