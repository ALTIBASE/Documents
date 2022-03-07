**Table of Contents**

- [Altibase 7.2.0.0.1 Release Notes](#altibase-7.2.0.0.1-release-notes)
  - [System Requirements](#system-requirements)
    - [Minimum Hardware Requirements](#minimum-hardware-requirements)
    - [Operating Systems and Platforms](#operating-systems-and-platforms)
  - [Release Notes](#release-notes)
    - [New Features](#new-features)
    - [Changes and Compatibility Issues](#changes-and-compatibility-issues)
    - [Package](#package)
    - [Download](#download)

# Altibase 7.2.0.0.1 Release Notes

## System Requirements

### Minimum Hardware Requirements

- 1GB RAM (Recommended: 2GB)
- 1 CPU (Recommended: 2 CPUs)
- 4 GB free hard disk space (Recommended: 12 GB)

### Operating Systems and Platforms

Altibase 7.2.0.0.1 can be run on the operating systems and platforms listed in the table below.

|                                                              | Altibase Server | Altibase client | System Requirement          |
| ------------------------------------------------------------ | --------------- | --------------- | --------------------------- |
| **Linux x86-64**                                             |                 |                 |                             |
| Red Hat Enterprise Linux 6 Red Hat Enterprise Linux 7 Red Hat Enterprise Linux 8 | ●               | ●               | - GNU glibc 2.12 and higher |
| **Linux on Power**                                           |                 |                 |                             |
| Red Hat Enterprise Linux 6                                   | ●               | ●               | - GNU glibc 2.12 and higher |
| **Linux on Power** **(Little Endian)**                       |                 |                 |                             |
| Red Hat Enterprise Linux 7                                   | ●               | ●               | - GNU glibc 2.17 and higher |
| **HP-UX Itanium (IA-64)**                                    |                 |                 |                             |
| HP-UX 11.31                                                  | ●               | ●               |                             |
| **Microsoft Windows (x64)**                                  |                 |                 |                             |
| Microsoft Windows 2008                                       | -               | ●               |                             |

> Both Altibase Server/Client support 64-bit only.
>
> Microsoft Windows supports Altibase Client only.
>
> Compatible with Red Hat Enterprise Linux 6, 7, 8 minor release.

## Release Notes

### New Features

#### SQL Extension

##### DELETE clause added to CREATE QUEUE and ALTER QUEUE statements

DELETE clause specifying whether to allow DELETE statement in QUEUE table is added.

If DELETE statement is not allowed by DELETE OFF clause, DEQUEUE parallel execution performance is enhanced compared to when it is allowed. Please refer to [Altibase 7.2 SQL Reference Manual](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.2/eng/SQL%20Reference.md#create-queue) for more detailed information about how to use the statement. In relation to this, [V$QUEUE_DELETE_OFF](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.2/eng/General Reference-2.The Data Dictionary.md#vqueue_delete_off) performance view was added.

##### ADD PARTITION supported on range-partitioned object

ADD PARTITION statement on range-partitioned table is supported. Due to this new feature, range-partitioned table without default partition can be created.

###### Restrictions on creating range partitioned table in Altibase 7.2

- Can create range-partitioned table without default partition.

  If this kind of range-partitioned table is created, partition without PARTITION_NAME is created in SYS_TABLE_PARTITIONS_.

- ADD PARTITION on range-partitioned object can only be executed on range-partitioned table without default partition.

- Range-partitioned tables without default partition cannot perform an execution adding default partitions.

- Range-partitioned tables with default partition cannot perform an execution deleting default partitions.

- Range-partitioned tables without default partition cannot execute CONJOIN/DISJOIN statement.

- In case range-partitioned table is replication target table, it cannot perform an execution adding partitions.

##### Application Development Interface Extension and Improvements

##### JDBC API Specification 4.2 partial support (PROJ-2707)

Altibase 7.2 supports JDBC API Specification 4.2 partially.

Altibase 7.2 JDBC Driver can be run on JRE 1.8 and higher. JDBC 4.2 APIs supported by Altibase 7.2 JDBC Driver can be found on [Altibase 7.2 JDBC User's Manual](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.2/eng/JDBC%20User's%20Manual.md#6jdbc-42-api-references). Changes or compatibility issues can be found on [changes and compatibility issues regarding Altibase JDBC 4.2](#changes-and-compatibility-issues-regarding-altibase-jdbc-42).

- **Auto-loading of JDBC driver class**

  Instead of loading the Class.forName() class manually, META-INF/services/java.sql.Driver file can automatically load the driver.

- **Wrapper Pattern Support**

  JDBC 4.0 standard interface that gets reference to the implementing object from proxy is supported. JDBC object can be obtained from a proxy object created such as in connection pool.

  ```sql
  try (Connection sWrappedCon = dbPool.getConnection()) {
      if (sWrappedCon.isWrapperFor(AltibaseConnection.class)) {
          AltibaseConnection connection = sWrappedCon.unwrap(AltibaseConnection.class);
          ...
          ...
  }
  ```

- **National Character Set Support**

  Standard multilingual interface, one of the specifications of JDBC 4.0, is supported.

- **Aborting Connections**

  Aborting the connection with database asynchronously, Connection.abort() interface, is supported.

- **Standard Socket Network Timeout API Support**

  Standard interface specifying socket timeout from the database server, Connection.setNetworkTimeout(), is supported.

- **Connection Management Enhancements**

  Executing the validation check on Connection object without Validation Query, Connection.isValid(), is supported.

- **Large Update Counts Support**

  For large record update, executeLargeUpdate() and executeLargeBatch() are supported.

- **Set Client Information Support**

  Specifying the name of client application using Connection.setClientInfo() is supported.

- **java.sql.SQLType interface Support**

  AltibaseJDBCType which implemented JDBC 4.2 standrd interface java.sql.SQLType is supported.

Most of the features enhanced at JDK level can also be used in Altibase JDBC 7.2.

- Release JDBC resources automatically using Try-with-resources statement

  ```sql
  try (Statement stmt = con.createStatement()) {
        ResultSet rs = stmt.executeQuery(query);
        while (rs.next()) {
          String coffeeName = rs.getString("aaa");
          int supplierID = rs.getInt("bbb");
        }
      }
  }
  ```

- Use Enhanced for-each loop in SQLException

  ```sql
  catch(SQLException ex) {
       for(Throwable e : ex ) {
          LOG.error("Error occurred: " + e);
       }
  }
  ```

- Obtain JDBC object from proxy object created such as in connection pool

  ```sql
  try (Connection sWrappedCon = dbPool.getConnection()) {
      if (sWrappedCon.isWrapperFor(AltibaseConnection.class)) {
          AltibaseConnection connection = sWrappedCon.unwrap(AltibaseConnection.class);
          ...
          ...
  }
  ```

#### Utilities

##### Specify altiComp commit count

COUNT_TO_COMMIT, a property enabling to specify the commit count, is added. Please refer to [Altibase 7.2 Utilities Manual](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.2/eng/Utilities%20Manual.md#count_to_commit) for more detailed information.

#### Altibase Server Performance and Stability Improvement

##### OLTP Scalability improvement (TASK-7073)

- Performance degradation of reading transaction in Linux x86-64 24-core CPU improved
- Logging structure improved for performance enhancement of DELETE transaction of memory DB
- In-place MVCC operating mechanism improved for performance enhancement of UPDATE transaction of disk DB
- Bottleneck of TABLE LOCK improved
- Removed unnecessary records of transaction logs when executing INSERT/UPDATE transaction
- Bottleneck of memory allocation/freeing improved when compressing transaction log file
  - See related [influences](#increased-usage-of-altibase-server-default-memory)
- Transaction performance of volatile memory DB improved
- Bottleneck of commit and garbage collection thread improved
  - Bottleneck of updating table information after transaction commit improved
- Transaction performance of memory DB enhanced
  - Removed bottleneck of the function invoking disk reading
  - Added Group Commit Log function

##### Transaction log recoding performance improvement (TASK-6983)

Changed the log compressing algorithm to LZ4 which has faster compressing speed.

##### Volatile/Involatile memory DB transaction performance improvement

Improved volatile/involatile memory DB transaction performance by simplifying the process of tracking memory table object identifier.

##### Stability of reusing undo tablespace enhancement

Removed the risk factor for occurring bugs by removing the unnecessary relationship between undo tablespace and disk index. Default value and maximum value of the related properties have changed due to improved disk page space efficiency.

- Maximum value of INDEX_INITTRANS has changed from 30 to 50
- Default value and maximum value of INDEX_MAXTRANS has changed from 30 to 50

##### LIMIT FOR UPDATE for PARTITIONED TABLE improvement

Improved performance by removing the unnecessary range reading operation when LIMIT is executed on partitioned table.

Performance is enhanced when all of the following conditions are met.

- START VALUE of the LIMIT clause is 1

  ```sql
  -- Example) START VALUE is 1
  SELECT * FROM T1 LIMIT 1;      -- internally limit start 1, count 1
  SELECT * FROM T1 LIMIT 100     -- internally limit start 1, count 100
  SELECT * FROM T1 LIMIT 1, 30   -- internally limit start 1, count 30
  ```

- Subnode of PROJECT is a node that manages scanning for each partition of the partition table (PARTITION-COORDINATOR) and

- every node of PARTITION-COORDINATOR node is SCAN

The form of an execution plan that meets all of the conditions is as below:

```sql
------------------------------------------------------------
PROJECT ( COLUMN_COUNT: 2, TUPLE_SIZE: 8, COST: 467.05 )
 PARTITION-COORDINATOR ( TABLE: SYS.T1, PARTITION: 4/4, FULL SCAN, ACCESS: 1, COST: 467.05 )
  SCAN ( PARTITION: P4, FULL SCAN, ACCESS: 0, COST: 116.76 )
  SCAN ( PARTITION: P3, FULL SCAN, ACCESS: 0, COST: 116.76 )
  SCAN ( PARTITION: P2, FULL SCAN, ACCESS: 0, COST: 116.76 )
  SCAN ( PARTITION: P1, FULL SCAN, ACCESS: 1, COST: 116.76 )
------------------------------------------------------------
```

##### SQL Performance improvement when using ORDER BY clause in inline view of a subquery

Improved performance by applying OBYE(Order By Elimination, removing unnecessary ORDER BY) query transformation when ORDER BY clause exists in inline view of subquery used in conditional clause(WHERE, HAVING clause).

- SQL example

  ```sql
  SELECT *
    FROM T1
   WHERE I1 IN (SELECT /*+ NO_UNNEST */I1
                  FROM (SELECT *
                          FROM T2
                         ORDER BY I2, I3));
  ```

  > Execution plan of SQL which is affected by this changes. SORT plan node in SUBQUERY FILTER is removed.

##### Scalar subquery performance improvement

Improved performance by removing the overhead occurring when checking whether the result of scalar subquery is a single record.



#### Altibase replication performance improvement

##### Replication sender performance enhancement

- New feature decompressing logs required for replication among compressed logs only added
- Changed the xLog compressing algorithm fron LZO to LZ4

### Changes and compatibility issues

The functions added, changed, and removed that DBAs and developers need to understand are described below.

#### Changes and compatibility issues regarding Altibase JDBC 4.2

Altibase JDBC 4.2 supports backward compatibility for Altibase JDBC 3.0, however, for some interfaces the operation has changed according to JDBC API Specification 4.2. 

##### Exception handling class changed for features not supported

Exception handling class for the following interfaces has changed from SQLException to SQLFeatureNotSupportedException. Since SQLFeatureNotSupportedException is a subclass of SQLException, current user programs can be operated without modification.

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

##### New column added to the result of some interfaces of DatabaseMetaData

SPECIFIC_NAME column is added to the result of getProcedures(), getProcedureColumns(), getFunctions() and getFunctionColumns() interfaces.

Altibase JDBC 7.2 has implemented SPECIFIC_NAME as below.

```sql
ProcName(FuncName) + '_' + ouid
```

##### Connection property default value has changed

- [reuse_resultset](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.2/eng/JDBC%20User's%20Manual.md#reuse_resultset)
  - Specifies whether to reuse the ResultSet object
  - Default value for Altibase 7.2 is true and reuses the ResultSet object whereas default value for Altibase 7.1 is false and does not reuse the ResultSet object.
- [lob_null_select](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.2/eng/JDBC%20User's%20Manual.md#lob_null_select)
  - Indicates whether getBlob(), getClob() should return the LOB object when the value of the the LOB column is NULL
  - Default value for Altibase 7.2 is off and does not return the LOB object whereas default value for Altibase 7.1 is on and returns the LOB object.

##### New connection property for Altibase JDBC 4.2 only

- [getprocedures_return_functions](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.2/eng/JDBC%20User's%20Manual.md#getprocedures_return_functions)
  - Specifies whether to add the result of the function to the result of DatabaseMetaData.getProcedures() and getProcedureColumns(). JDBC API Specification 4.2 standard excludes the function information, however, for client backward compatibility, Altibase JDBC 4.2 keeps it the same as subversion. To exclude the function information following the standard, the value of the property is set to false.

##### Changed CLIENT_TYPE

CLIENT_TYPE of Altibase 7.2 JDBC session is NEW_JDBC42. In case Altibase 7.2 JDBC Driver was used to compile or run, the CLIENT_TYPE value of V$SESSION has to be searched as NEW_JDBC42.



#### Altibase replication compatibility

##### Restrictions on bilateral replication between Altibase 7.1 and Altibase 7.2

Altibase 7.1 and Altibase 7.2 are not able to perform DDL duplication and offline replication.

DDL duplication can be executed when all three digits of replication protocol version are identical, therefore it does not support backward compatibility.

Offline replication is a add-on feature of replication and it can be executed when all three digits of binary db version are identical, therefore it does not support backward compatibility.

##### Restrictions on bilateral replication between Altibase 6.5.1 and Altibase 7.2

Since Altibase replication supports backward compatibility, both unilateral and bilateral LAZY mode replication between Altibase 6.5.1 and Altibase 7.2 are possible. However, if spatial data type column exists in replication target table, data with SRID value cannot be synchronized to Altibase 6.5.1 when executing replication from Altibase 7.2 to Altibase 6.5.1.



#### SQL result and execution plan modification

- SQL performance enhanced when using ORDER BY clause in the inline view of a subquery

  Execution plan of SQL that is affected by this has changed. SORT plan node in SUBQUERY FILTER is removed.

- Optimize the operation mechanism of duplicated LEFT OUTER JOIN

  Execution plan and result of SQL that is affected by this can be changed. 

- New and updated features related to Subquery Unnesting

  Execution plan of SQL that is affected by this can be changed.

  

#### Increased usage of Altibase server default memory

Default memory usage of Altibase server increases due to the improvement of bottleneck of memory allocation/freeing when compressing transaction log file. Previous version and increment can be found by Storage_Memory_Recovery in V$MEMSTAT. Meomry increment is affected by TRANSACTION_TABLE_SIZE. When TRANSACTION_TABLE_SIZE is set to its default value 1024, 32MB increases and when it is set to its maximum value 16384, 500MB increases.

#### New Error Message

The error message appearing when disk tablespace is chosen when creating a QUEUE has changed from ERR-311E5 : The table is not a memory or volatile table. to as belows.

```sql
iSQL> CREATE QUEUE Q1 ( 7 ) TABLESPACE SYS_TBS_DISK_DATA;
[ERR-314AA : Failed to create queue table in disk tablespace.]
```

#### Database Version

Version by Database Component

| Altibase Version | Database Binary Version | Meta Version | Communication Protocol Version | Replication Protocol Version |
| :--------------: | :---------------------: | :----------: | :----------------------------: | :--------------------------: |
|    7.1.0.5.8     |          6.5.1          |    8.9.1     |             7.1.7              |            7.4.6             |
|    7.2.0.0.1     |          7.2.0          |    8.9.1     |             7.1.7              |            7.4.8             |

#### Compatibility

##### Database Binary Version

This indicates the compatibility of the database image file and log file. 

Database binary version has changed due to the improvement of log file logging structure. Migration is required when upgrading the Altibase version because this is not compatible with databases lower than Altibase 7.2.

##### Communication Protocol Version

This indicates the compatibility of the communication protocol between Altibase server and client. Client backward compatibility can be found here.

The top two digits of the communication protocol version are the same and the patch version has changed. When major version and minor version are the same, client backward compatibility is supported.

> Client backward compatibility supports user application program(Altibase Client) which was compiled by lower version of Altibase library to operate normally on higer version of Altibase.

##### Replication protocol version

This indicates the Altibase replication backward compatibility or the compatibility with replication add-ons.

Since there are no major version and minor version changes, LAZY mode replication supports Altibase replication backward compatibility. However, due to patch version change replication add-ons are not compatible.

> ###### Altibase replication backward compatibility
>
> Altibase replication backward compatibility means replication can be executed from lower replication protocol version to higher version and it is supported when the top two digits(major and minor version) of replication protocol version are the same. Altibase replication backward compatibility is only supported in LAZY mode replication.
>
> EAGER mode replication does not support replication backward compatibility. DDL duplication does not support backward compatibility since all three digits of replication protocol version has to be the same. Replication add-ons including offline replication does not support backward compatibility.

#### Altibase Server Property

Altibase server properties that are added, updated or removed in Altibase 7.2.0.0.1 are as belows. For more detailed information about each properties, please refer to [General Reference-1.Data Types & Altibase Properties](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.2/eng/General%20Reference-1.Data%20Types%20%26%20Altibase%20Properties.md).

##### New property

- [DBLINK_GLOBAL_TRANSACTION_LEVEL](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.2/eng/General%20Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#dblink_global_transaction_level)

##### Updated properties

- [EXECUTE_STMT_MEMORY_MAXIMUM](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.2/eng/General%20Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#execute_stmt_memory_maximum)

  The default value has changed from 1073741824 to 2147483648.

- [INDEX_MAXTRANS](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.2/eng/General%20Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#index_maxtrans-unit-count)

  The default value and MAX value have changed from 30 to 50.

- [INDEX_INITRANS](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.2/eng/General%20Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#index_initrans-unit-count)

  The MAX value has changed from 30 to 50.

- [LOCK_MGR_TYPE](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.2/eng/General%20Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#lock_mgr_type)

  The default value has changed from 0 to 2.

- [PSM_CHAR_DEFAULT_PRECISION](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.2/eng/General%20Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#psm_char_default_precision)

  The default value has changed from 32767 to 32000.

- [PSM_NCHAR_UTF16_DEFAULT_PRECISION](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.2/eng/General%20Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#psm_nchar_utf16_default_precision)

  The default value has changed from 16383 to 16000.

- [PSM_NCHAR_UTF8_DEFAULT_PRECISION](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.2/eng/General%20Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#psm_nchar_utf8_default_precision)

  The default value has changed from 10921 to 10666.

- [PSM_NVARCHAR_UTF16_DEFAULT_PRECISION](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.2/eng/General%20Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#psm_nvarchar_utf16_default_precision)

  The default value has changed from 16383 to 16000.

- [PSM_NVARCHAR_UTF8_DEFAULT_PRECISION](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.2/eng/General%20Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#psm_nvarchar_utf8_default_precision)

  The default value has changed from 10921 to 10666.

- [PSM_VARCHAR_DEFAULT_PRECISION](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.2/eng/General%20Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#psm_varchar_default_precision)

  The default value has changed from 32767 to 32000.

##### Removed property

- GLOBAL_TRANSACTION_LEVEL

#### Meta Table

##### New meta table

- [SYS_REPL_TABLE_OID_IN_USE_](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.2/eng/General%20Reference-2.The%20Data%20Dictionary.md#sys_repl_table_oid_in_use_)

#### Performance View

New performance views as belows are added. For more detailed information about each performance view, please refer to [General Reference-2.The Data Dictionary](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.2/eng/General%20Reference-2.The%20Data%20Dictionary.md).

##### New performance views

- [V$REPL_REMOTE_META_INDEX_COLUMNS](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.2/eng/General%20Reference-2.The%20Data%20Dictionary.md#vrepl_remote_meta_index_columns)
- [V$QUEUE_DELETE_OFF](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.2/eng/General%20Reference-2.The%20Data%20Dictionary.md#vqueue_delete_off)

### Package

| OS    | CPU    | Server/Client   | Package Installer Name                                |
| ----- | ------ | --------------- | ----------------------------------------------------- |
| LINUX | x86-64 | Altibase Server | altibase-server-7.2.0.0.1-LINUX-X86-64bit-release.run |
|       |        | Altibase Client | altibase-client-7.2.0.0.1-LINUX-X86-64bit-release.run |

### Download

#### Package

[http://support.altibase.com](http://support.altibase.com/)

#### Manual

[Altibase 7.2 Manuals](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.2/eng/README.md)

#### Installation

[Altibase 7.2 Installation Guide](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.2/eng/Installation%20Guide.md)