

- [General Reference](#general-reference)
  - [3. The Data Dictionary](#3%EB%8D%B0%EC%9D%B4%ED%84%B0-%EB%94%95%EC%85%94%EB%84%88%EB%A6%AC)
    - [Meta Tables](#%EB%A9%94%ED%83%80-%ED%85%8C%EC%9D%B4%EB%B8%94)
    - [SYS_AUDIT\_](#sys_audit_)
    - [SYS_AUDIT_OPTS\_](#sys_audit_opts_)
    - [SYS_COLUMNS\_](#sys_columns_)
    - [SYS_COMMENTS\_](#sys_comments_)
    - [SYS_COMPRESSION_TABLES\_](#sys_compression_tables_)
    - [SYS_CONSTRAINTS\_](#sys_constraints_)
    - [SYS_CONSTRAINT_COLUMNS\_](#sys_constraint_columns_)
    - [SYS_CONSTRAINT_RELATED\_](#sys_constraint_related_)
    - [SYS_DATABASE\_](#sys_database_)
    - [SYS_DATABASE_LINKS\_](#sys_database_links_)
    - [SYS_DIRECTORIES\_](#sys_directories_)
    - [SYS_ENCRYPTED_COLUMNS\_](#sys_encrypted_columns_)
    - [SYS_GRANT_OBJECT\_](#sys_grant_object_)
    - [SYS_GRANT_SYSTEM\_](#sys_grant_system_)
    - [SYS_INDEX_COLUMNS\_](#sys_index_columns_)
    - [SYS_INDEX_PARTITIONS\_](#sys_index_partitions_)
    - [SYS_INDEX_RELATED\_](#sys_index_related_)
    - [SYS_INDICES\_](#sys_indices_)
    - [SYS_JOBS\_](#sys_jobs_)
    - [SYS_LIBRARIES\_](#sys_libraries_)
    - [SYS_LOBS\_](#sys_lobs_)
    - [SYS_MATERIALIZED_VIEWS\_](#sys_materialized_views_)
    - [SYS_PACKAGES\_](#sys_packages_)
    - [SYS_PACKAGE_PARAS\_](#sys_package_paras_)
    - [SYS_PACKAGE_PARSE\_](#sys_package_parse_)
    - [SYS_PACKAGE_RELATED\_](#sys_package_related_)
    - [SYS_PART_INDICES\_](#sys_part_indices_)
    - [SYS_PART_KEY_COLUMNS\_](#sys_part_key_columns_)
    - [SYS_PART_LOBS\_](#sys_part_lobs_)
    - [SYS_PART_TABLES\_](#sys_part_tables_)
    - [SYS_PASSWORD_HISTORY\_](#sys_password_history_)
    - [SYS_PASSWORD_LIMITS\_](#sys_password_limits_)
    - [SYS_PRIVILEGES\_](#sys_privileges_)
    - [SYS_PROCEDURES\_](#sys_procedures_)
    - [SYS_PROC_PARAS\_](#sys_proc_paras_)
    - [SYS_PROC_PARSE\_](#sys_proc_parse_)
    - [SYS_PROC_RELATED\_](#sys_proc_related_)
    - [SYS_RECYCLEBIN\_](#sys_recyclebin_)
    - [SYS_REPLICATIONS\_](#sys_replications_)
    - [SYS_REPL_HOSTS\_](#sys_repl_hosts_)
    - [SYS_REPL_ITEMS\_](#sys_repl_items_)
    - [SYS_REPL_OFFLINE_DIR\_](#sys_repl_offline_dir_)
    - [SYS_REPL_OLD_COLUMNS\_](#sys_repl_old_columns_)
    - [SYS_REPL_OLD_INDEX_COLUMNS\_](#sys_repl_old_index_columns_)
    - [SYS_REPL_OLD_INDICES\_](#sys_repl_old_indices_)
    - [SYS_REPL_OLD_ITEMS\_](#sys_repl_old_items_)
    - [SYS_REPL_RECOVERY_INFOS\_](#sys_repl_recovery_infos_)
    - [SYS_SECURITY\_](#sys_security_)
    - [SYS_SYNONYMS\_](#sys_synonyms_)
    - [SYS_TABLES\_](#sys_tables_)
    - [SYS_TABLE_PARTITIONS\_](#sys_table_partitions_)
    - [SYS_TABLE_SIZE\_](#sys_table_size_)
    - [SYS_TBS_USERS\_](#sys_tbs_users_)
    - [SYS_TRIGGERS\_](#sys_triggers_)
    - [SYS_TRIGGER_DML_TABLES\_](#sys_trigger_dml_tables_)
    - [SYS_TRIGGER_STRINGS\_](#sys_trigger_strings_)
    - [SYS_TRIGGER_UPDATE_COLUMNS\_](#sys_trigger_update_columns_)
    - [SYS_USERS\_](#sys_users_)
    - [DBA_USERS\_](#dba_users_)
    - [SYS_USER_ROLES\_](#sys_user_roles_)
    - [SYS_VIEWS\_](#sys_views_)
    - [SYS_VIEW_PARSE\_](#sys_view_parse_)
    - [SYS_VIEW_RELATED\_](#sys_view_related_)
    - [SYS_XA_HEURISTIC_TRANS\_](#sys_xa_heuristic_trans_)
    - [Performance View](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)
    - [V\$ACCESS_LIST](#vaccess_list)
    - [V\$ALLCOLUMN](#vallcolumn)
    - [V\$ARCHIVE](#varchive)
    - [V\$BACKUP_INFO](#vbackup_info)
    - [V\$BUFFPAGEINFO](#vbuffpageinfo)
    - [V\$BUFFPOOL_STAT](#vbuffpool_stat)
    - [V\$CATALOG](#vcatalog)
    - [V\$DATABASE](#vdatabase)
    - [V\$DATAFILES](#vdatafiles)
    - [V\$DATATYPE](#vdatatype)
    - [V\$DBA_2PC_PENDING](#vdba_2pc_pending)
    - [V\$DBLINK_ALTILINKER_STATUS](#vdblink_altilinker_status)
    - [V\$DBLINK_DATABASE_LINK_INFO](#vdblink_database_link_info)
    - [V\$DBLINK_GLOBAL_TRANSACTION_INFO](#vdblink_global_transaction_info)
    - [V\$DBLINK_LINKER_CONTROL_SESSION_INFO](#vdblink_linker_control_session_info)
    - [V\$DBLINK_LINKER_DATA_SESSION_INFO](#vdblink_linker_data_session_info)
    - [V\$DBLINK_LINKER_SESSION_INFO](#vdblink_linker_session_info)
    - [V\$DBLINK_NOTIFIER_TRANSACTION_INFO](#vdblink_notifier_transaction_info)
    - [V\$DBLINK_REMOTE_STATEMENT_INFO](#vdblink_remote_statement_info)
    - [V\$DBLINK_REMOTE_TRANSACTION_INFO](#vdblink_remote_transaction_info)
    - [V\$DBMS_STATS](#vdbms_stats)
    - [V\$DB_FREEPAGELISTS](#vdb_freepagelists)
    - [V\$DB_PROTOCOL](#vdb_protocol)
    - [V\$DIRECT_PATH_INSERT](#vdirect_path_insert)
    - [V\$DISKTBL_INFO](#vdisktbl_info)
    - [V\$DISK_BTREE_HEADER](#vdisk_btree_header)
    - [V\$DISK_TEMP_INFO](#vdisk_temp_info)
    - [V\$DISK_TEMP_STAT](#vdisk_temp_stat)
    - [V\$DISK_UNDO_USAGE](#vdisk_undo_usage)
    - [V\$EVENT_NAME](#vevent_name)
    - [V\$EXTPROC_AGENT](#vextproc_agent)
    - [V\$FILESTAT](#vfilestat)
    - [V\$FLUSHER](#vflusher)
    - [V\$FLUSHINFO](#vflushinfo)
    - [V\$INDEX](#vindex)
    - [V\$INSTANCE](#vinstance)
    - [V\$INTERNAL_SESSION](#vinternal_session)



Altibase® Administration

# General Reference

![](media/GeneralReference/e5cfb3761673686d093a3b00c062fe7a.png)

Altibase Administration General Reference

Release 7.1

Copyright ⓒ 2001\~2021 Altibase Corp. All Rights Reserved.

This manual contains proprietary information of Altibase Corporation; it is provided under a license agreement containing restrictions on use and disclosure and is also protected by copyright patent and other intellectual property law. Reverse engineering of the software is prohibited. All trademarks, registered or otherwise, are the property of their respective owners.

**Altibase Corp**

10F, Daerung PostTower II, 306, Digital-ro, Guro-gu, Seoul 08378, Korea Telephone: +82-2-2082-1000 Fax: 82-2-2082-1099

Customer Service Portal: http://support.altibase.com/en/

Homepage: [http://www.altibase.com]

## 3. The Data Dictionary

The data dictionary of Altibase consists of meta tables, in which information about objects is stored, and process tables, in which information about processes is stored. Process tables comprise fixed tables and performance views. 

This chapter describes the Altibase data dictionary, which is the basis of all database objects and all Altibase system information.

### Meta Tables

Meta tables are system-defined tables that contain all information about database objects. 

This section describes the types of meta tables and their structure, and explains how to read and update the information in meta tables.

#### Structure and Function

Meta tables are defined by the system for the purpose of managing database objects. They use the same data types and store records in the same way as user-defined tables. When Altibase starts up, it loads information about database objects. When DDL statements are executed, meta tables are used to read, store, and update this information. The owner of meta tables is the system user (user name: SYSTEM_), so normal users have limited access to meta tables. 

#### Retrieving Information from Meta Tables

When a database object is created, deleted or modified using a DDL statement, the system creates, deletes, or updates records in one or more meta tables. 

After a DDL statement is executed, the resultant changes to database objects can be confirmed by checking meta tables. This is accomplished using a SELECT statement, just as with a regular database table. 

#### Modifying Data in Meta Tables

It is possible to use DML statements to explicitly make changes to the data in meta tables. However, the system-defined system user (SYSTEM_) can only make such changes to meta tables. Additionally, when the information in meta tables is changed, the system may become impossible to start, information about database objects may be lost, or the system may be critically damaged. Therefore, users must avoid making changes to meta tables whenever possible. When it is inevitable that a user must change meta table information, it is imperative that the database first be backed up, and it must be understood that the user is completely responsible for any damage resulting from making direct changes to meta table information.

#### Modifying Meta Table Schema

The meta table schema may be modified when a new kind of DDL statement is introduced, or when the functionality of an existing statement is changed. Depending on the characteristics of the changes to meta table schema, one of two cases may arise: either the database might need to be migrated, or the meta table schema will simply be automatically modified when Altibase is restarted. This should be kept in mind when upgrading Altibase to a newer version.

#### The types of Meta Tables

This table shows the list of meta tables. Their names start with SYS_.

| Meta Table Name              | Description                                                  |
| ---------------------------- | ------------------------------------------------------------ |
| SYS_AUDIT\_                  | This table stores information about the operation status of the audit. |
| SYS_AUDIT_OPTS\_             | This view stores auditing conditions. SYS_AUDIT_ALL_OPTS_ is the base table of this view. |
| SYS_COLUMNS\_                | This table contains information about columns.               |
| SYS_COMMENTS\_               | This table contains information about explanatory comments.  |
| SYS_COMPRESSION_TABLES\_     | This table contains information about compressed columns.    |
| SYS_CONSTRAINTS\_            | This table contains information about constraints.           |
| SYS_CONSTRAINT_COLUMNS\_     | This table contains information about columns having constraints. |
| SYS_CONSTRAINT_RELATED\_     | This table contains information about the stored functions referenced by the constraints. |
| SYS_DATABASE\_               | This table contains information about the name and version of the database. |
| SYS_DATABASE_LINKS\_         | This table contains information about the database links.    |
| SYS_DIRECTORIES\_            | This table contains information about directories used by stored procedures for managing files. |
| SYS_DN_USERS\_               | This table is reserved for future use.                       |
| SYS_DUMMY\_                  | This table is for internal use only.                         |
| SYS_ENCRYPTED_COLUMNS\_      | This table contains additional security information for individual columns. |
| SYS_GRANT_OBJECT\_           | This table contains information about object privileges.     |
| SYS_GRANT_SYSTEM\_           | This table contains information about system privileges.     |
| SYS_INDEX_COLUMNS\_          | This table contains information about index key columns.     |
| SYS_INDEX_PARTITIONS\_       | This table contains information about index partitions.      |
| SYS_INDEX_RELATED\_          | This table contains information about the stored functions on which the function-based indexes are based. |
| SYS_INDICES\_                | This table contains information about indexes.               |
| SYS_JOBS\_                   | This table contains information about jobs.                  |
| SYS_LIBRARIES\_              | This table contains information about external library objects. |
| SYS_LOBS\_                   | This table contains information about LOB columns.           |
| SYS_MATERIALIZED_VIEWS\_     | This table contains information about materialized view.     |
| SYS_PACKAGES\_               | This table contains information about packages.              |
| SYS_PACKAGE_PARAS\_          | This table contains information about subprogram(stored procedures and stored functions) parameters contained in packages. |
| SYS_PACKAGE_PARSE\_          | This table contains information about statement texts of user-defined packages. |
| SYS_PACKAGE_RELATED\_        | This table contains information about tables, sequences, stored procedures, stored functions, or views accessed by stored procedures and stored functions inside packages. |
| SYS_PART_INDICES\_           | This table contains information about partitioned indexes.   |
| SYS_PART_KEY_COLUMNS\_       | This table contains information about partitioning keys.     |
| SYS_PART_LOBS\_              | This table contains information about LOB columns for respective partitions. |
| SYS_PART_TABLES\_            | This table contains information about partitioned tables.    |
| SYS_PASSWORD_HISTORY\_       | This table contains information about alterations made to user passwords that have been assigned a password policy. |
| SYS_PASSWORD_LIMITS\_        | This meta table contains specified password management policies at user creation and account status quo. |
| SYS_PRIVILEGES\_             | This table contains information about privileges.            |
| SYS_PROCEDURES\_             | This table contains information about stored procedures and functions. |
| SYS_PROC_PARAS\_             | This table contains information about the parameters for stored procedures and functions. |
| SYS_PROC_PARSE\_             | This table contains the actual text of stored procedures and stored functions. |
| SYS_PROC_RELATED\_           | This table contains information about tables accessed by stored procedures and functions. |
| SYS_RECYCLEBIN\_             | The table contains information about tables in the recycle bin. |
| SYS_REPLICATIONS\_           | This table contains general information about replication.   |
| SYS_REPL_HOSTS\_             | This table contains information about replication hosts.     |
| SYS_REPL_ITEMS\_             | This table contains information about tables to be replicated |
| SYS_REPL_OFFLINE_DIR\_       | This table contains information about the log directory related to the replication offline option. |
| SYS_REPL_OLD_COLUMNS\_       | This table contains information about columns replicated by the replication sender thread. |
| SYS_REPL_OLD_INDEX_COLUMNS\_ | This table contains information about index columns replicated by the replication sender thread. |
| SYS_REPL_OLD_INDICES\_       | This table contains information about indexes replicated by the replication sender thread. |
| SYS_REPL_OLD_ITEMS\_         | This table contains information about the tables replicated by the replication sender thread. |
| SYS_REPL_RECOVERY_INFOS\_    | This table contains information about logs used by replication for recovery of a remote server. |
| SYS_SECURITY\_               | This table contains information about the state of the security module. |
| SYS_SYNONYMS\_               | This table contains information about synonyms.              |
| SYS_TABLES\_                 | This table contains information about all kinds of tables.   |
| SYS_TABLE_PARTITIONS\_       | This table contains information about table partitions.      |
| SYS_TABLE_SIZE\_             | This table contains information about the actual size of disk and memory tables in the system. |
| SYS_TBS_USERS\_              | This table contains information about users’ access to user-defined tablespaces. |
| SYS_TRIGGERS\_               | This table contains information about triggers.              |
| SYS_TRIGGER_DML_TABLES\_     | This table contains information about tables accessed by triggers. |
| SYS_TRIGGER_STRINGS\_        | This table contains the actual text of trigger commands.     |
| SYS_TRIGGER_UPDATE_COLUMNS\_ | This table contains information about columns that cause triggers to fire whenever their contents are changed. |
| SYS_USERS\_                  | This table contains information about users.                 |
| DBA_USERS\_                  | The DBA_USERS is a meta table which stores the user information. Only SYS can make an inquiry. |
| SYS_USER_ROLES\_             | This table stores information about the roles granted to the user. |
| SYS_VIEWS\_                  | This table contains information about views.                 |
| SYS_VIEW_PARSE\_             | This table contains the actual text of statements used to create views. |
| SYS_VIEW_RELATED\_           | This table contains information about objects accessed by views. |
| SYS_XA_HEAURISTIC_TRANS_     | This table contains information about global transactions.   |
| USER_SRS                     | Meta table that stores information about Spatial Reference System (SRS), with SPATIAL_REF_SYS as synonym |

##### Unsupported Meta Tables

Altibase provides the following GIS-related meta tables. Their names begin with STO_. They are currently unsupported. 		

 STO_COLUMNS\_		
 STO_DATUMS\_		
 STO_ELLIPSOIDS\_		
 STO_GEOCCS\_		
 STO_GEOGCS\_		
 STO_PRIMEMS\_		
 STO_PROJCS\_		
 STO_PROJECTIONS\_		
 STO_SRS\_		
 STO_USER_COLUMNS\_

### SYS_AUDIT\_

This meta table stores information about the operation status of the audit.

| Column name | Type    | Description                                                  |
| ----------- | ------- | ------------------------------------------------------------ |
| IS_STARTED  | INTEGER | Whether or not auditing is being executed                    |
| START_TIME  | DATE    | The time at which auditing started                           |
| STOP_TIME   | DATE    | The time at which auditing stopped                           |
| RELOAD_TIME | DATE    | The time at which the auditing conditions were applied to the server |

#### Column Information

##### IS_STARTED

Indicates whether or not auditing is currently being performed. 

0: Auditing is currently not being performed. 

1: Auditing is currently being performed.

##### START_TIME

Indicates the time at which auditing started.

##### STOP_TIME

Indicates the time at which auditing stopped.

##### RELOAD_TIME

Indicates the time at which altered auditing conditions were applied to the Altibase server. The value of this column is updated for the occasions below:

- When the DBA has started auditing, using the ALTER SYSTEM START AUDIT statement. 
- When the DBA has applied altered auditing conditions to auditing, using the ALTER SYSTEM RELOAD AUDIT statement.

### SYS_AUDIT_OPTS\_

This meta view stores auditing conditions. The base table of this view is the SYS_AUDIT_ALL_OPTS_ meta table.

<table>
    <tr>
        <th>Column name</th>
        <th>Type</th>
        <th>Description</th>
   </tr>
    <tr>
    	<td>USER_NAME</td>
        <td>VARCHAR(128)</td>
        <td>The user name</td>
    </tr>
     <tr>
    	<td>OBJECT_NAME</td>
        <td>VARCHAR(128)</td>
        <td>The object name</td>
    </tr>
     <tr>
    	<td>OBJECT_TYPE</td>
        <td>VARCHAR(40)</td>
        <td>The object type</td>
    </tr>
     <tr>
    	<td>SELECT_OP</td>
        <td>CHAR(3)</td>
        <td rowspan="18">The units in which logs are written for each
operation statement</td>
    </tr>
     <tr>
    	<td>INSERT_OP</td>
        <td>CHAR(3)</td>
    </tr>
     <tr>
    	<td>UPDATE_OP</td>
        <td>CHAR(3)</td>
    </tr>
     <tr>
    	<td>DELETE_OP</td>
        <td>CHAR(3)</td>
    </tr>
     <tr>
    	<td>MOVE_OP</td>
        <td>CHAR(3)</td>
    </tr>
     <tr>
    	<td>MERGE_OP</td>
        <td>CHAR(3)</td>
    </tr>
     <tr>
    	<td>ENQUEUE_OP</td>
        <td>CHAR(3)</td>
    </tr>
     <tr>
    	<td>DEQUEUE_OP</td>
        <td>CHAR(3)</td>
    </tr>
     <tr>
    	<td>LOCK_TABLE_OP</td>
        <td>CHAR(3)</td>
    </tr>
     <tr>
    	<td>EXECUTE_OP</td>
        <td>CHAR(3)</td>
    </tr>
     <tr>
    	<td>COMMIT_OP</td>
        <td>CHAR(3)</td>
    </tr>
     <tr>
    	<td>ROLLBACK_OP</td>
        <td>CHAR(3)</td>
    </tr>
     <tr>
    	<td>SAVEPOINT_OP</td>
        <td>CHAR(3)</td>
    </tr>
     <tr>
    	<td>CONNECT_OP</td>
        <td>CHAR(3)</td>
    </tr>
     <tr>
    	<td>DISCONNECT_OP</td>
        <td>CHAR(3)</td>
    </tr>
     <tr>
    	<td>ALTER_SESSION_OP</td>
        <td>CHAR(3)</td>
    </tr>
     <tr>
    	<td>ALTER_SYSTEM_OP</td>
        <td>CHAR(3)</td>
    </tr>
    <tr>
    	<td>DDL_OP</td>
        <td>CHAR(3)</td>
    </tr>
</table>

#### Column Information

##### USER_NAME

This is the user name of the owner of the auditing target object.

##### OBJECT_NAME

This is the name of the auditing target object.

##### OBJECT_TYPE

This is the type of the target object, which is one of the following:

- TABLE
- VIEW
- QUEUE
- SEQUENCE
- PROCEDURE
- FUNCTION

##### XXX_OP

This is the units for logs of operation statements. Before '/' is the unit for logs of successful executions, and after is the unit for logs of failed executions. 

The units for logs are as below:

- -: Logs are not written. 
- S: Logs are written in the unit of sessions. 
- A: Logs are written in the unit of accesses.

The following examples show values of the SYS_AUDIT_OPTS_ view after auditing conditions are enabled.

```
iSQL> AUDIT insert, select, update, delete on friends BY SESSION WHENEVER SUCCESSFUL;
Audit success.

iSQL> AUDIT insert, select, update, delete on friends BY ACCESS WHENEVER NOT SUCCESSFUL;
Audit success.

USER_NAME : SYS 
OBJECT_NAME : FRIENDS 
OBJECT_TYPE : TABLE 
SELECT_OP : S/A 
INSERT_OP : S/A 
UPDATE_OP : S/A 
DELETE_OP : S/A 
MOVE_OP : -/- 
MERGE_OP : -/- 
ENQUEUE_OP : -/- 
DEQUEUE_OP : -/- 
LOCK_TABLE_OP : -/- 
EXECUTE_OP : -/- 
COMMIT_OP : -/- 
ROLLBACK_OP : -/- 
SAVEPOINT_OP : -/- 
CONNECT_OP : -/- 
DISCONNECT_OP : -/- 
ALTER_SESSION_OP : -/- 
ALTER_SYSTEM_OP : -/- 
DDL_OP : -/-

iSQL> AUDIT DDL BY sys WHENEVER NOT SUCCESSFUL;
Audit success.


USER_NAME : SYS 
OBJECT_NAME : ALL 
OBJECT_TYPE : 
SELECT_OP : -/- 
INSERT_OP : -/- 
UPDATE_OP : -/- 
DELETE_OP : -/- 
MOVE_OP : -/- 
MERGE_OP : -/- 
ENQUEUE_OP : -/- 
DEQUEUE_OP : -/- 
LOCK_TABLE_OP : -/- 
EXECUTE_OP : -/- 
COMMIT_OP : -/- 
ROLLBACK_OP : -/- 
SAVEPOINT_OP : -/- 
CONNECT_OP : -/- 
DISCONNECT_OP : -/- 
ALTER_SESSION_OP : -/- 
ALTER_SYSTEM_OP : -/- 
DDL_OP : -/T
```

### SYS_COLUMNS\_

Information about columns defined in all tables, virtual columns in all views, and virtual columns in all sequences is stored in this meta table.

| Column name      | Type          | Description                                                  |
| ---------------- | ------------- | ------------------------------------------------------------ |
| COLUMN_ID        | INTEGER       | The column identifier                                        |
| DATA_TYPE        | INTEGER       | The data type                                                |
| LANG_ID          | INTEGER       | The language identifier                                      |
| OFFSET           | BIGINT        | The offset of the column within the record                   |
| SIZE             | BIGINT        | The physical length of the column within the record          |
| USER_ID          | INTEGER       | The user identifier                                          |
| TABLE_ID         | INTEGER       | The table identifier                                         |
| PRECISION        | INTEGER       | The specified precision of the column                        |
| SCALE            | INTEGER       | The specified scale of the column                            |
| COLUMN_ORDER     | INTEGER       | The position of the column in the table                      |
| COLUMN_NAME      | VARCHAR(128)  | The name of the column                                       |
| IS_NULLABLE      | CHAR(1)       | Whether NULL is permitted. T: can be NULL F: cannot be NULL  |
| DEFAULT_VAL      | VARCHAR(4000) | The default value or expression                              |
| STORE_TYPE       | CHAR(1)       | The column storage type V: variable type F: fixed type L: LOB column |
| IN_ROW_SIZE      | INTEGER       | The length of data that can be saved in a fixed area when data are saved in a variable-length column in a memory table |
| REPL_CONDITION   | INTEGER       | Deprecated                                                   |
| IS_HIDDEN        | CHAR(1)       | Whether the column is hidden or not T: hidden column F: public column |
| IS_KEY_PRESERVED | CHAR(1)       | Whether or not the column is modifiable T: Modifiable F: Unmodifiable |

#### Column Information

##### COLUMN_ID

This is the column identifier, which is assigned automatically by the system sequence.

##### DATA_TYPE

This is the data type identifier. The identifiers for each data type are as follows:

| Data Type | Value |
| --------- | ----- |
| CHAR      | 1     |
| VARCHAR   | 12    |
| NCHAR     | \-8   |
| NVARCHAR  | \-9   |
| NUMERIC   | 2     |
| DECIMAL   | 2     |
| FLOAT     | 6     |
| NUMBER    | 6     |
| DOUBLE    | 8     |
| REAL      | 7     |
| BIGINT    | \-5   |
| INTEGER   | 4     |
| SMALLINT  | 5     |
| DATE      | 9     |
| BLOB      | 30    |
| CLOB      | 40    |
| BYTE      | 20001 |
| NIBBLE    | 20002 |
| BIT       | \-7   |
| VARBIT    | \-100 |
| GEOMETRY  | 10003 |

For more information about data types, please refer to Chapter1: Data Types.

##### LANG_ID

A column that contains the language properties for character data types (CHAR, VARCHAR).

##### OFFSET

This indicates the physical starting point of a column within a record. The offset and size of a column are used to calculate the physical storage size of a record.

##### SIZE

This is the physical storage size of the column in a record, calculated by the system based on the column type, user-defined precision, etc.

##### USER_ID

This corresponds to a USER_ID value in the SYS_USERS_ meta table, and identifies the owner of the table to which the column belongs.

##### TABLE_ID

This corresponds to a TABLE_ID value in the SYS_TABLES_ meta table, and identifies the table to which the column belongs.

##### PRECISION

This is the precision of the data type, and is either defined by the user or corresponds to the default value for the system. In the case of a character data type, it corresponds to the length of the character data type set by the user.

##### SCALE

This is the scale of the data type, and is either defined by the user or corresponds to the default value for the system. This value is not used with some data types. 

##### COLUMN_ORDER

This is the order in which columns appear in a table. 

The order in which the columns are stated in a CREATE TABLE statement determines the order in which they are created, and thus their position in the table. If a column is added using an ALTER TABLE statement, the newly created column will be the last column in the table.

##### COLUMN_NAME

This is the name specified when a user creates a table or adds a column to the table.

##### IS_NULLABLE

Indicates whether NULL is allowed in the column.

When creating a column, the user can explicitly specify whether to allow NULL for the column. If not specified, NULL is allowed by default.

##### DEFAULT_VAL

The default value the user specified in the column is displayed.

If the column is a hidden column added automatically due to the creation of a function-based index, the formula used to create the function-based index is stored.

##### STORE_TYPE

When physically storing a column, it can either be written as part of a record, or it can be saved on another page, in which case only the location of the data is stored in the record. 

If the physical storage size of a column is too big, or if the size of the column varies frequently for individual records, the column can be stored on another page by using the VARIABLE option when defining the column. This option is generally used for VARCHAR types where the character strings in a column are long. 

This column indicates whether the VARIABLE option is used.

##### IN_ROW_SIZE

This is the default IN_ROW_SIZE when data are stored in variable-length columns in memory tables. When data are inserted into a variable-length column, if the length of the data is equal to or smaller than the value specified by IN_ROW_SIZE, the data are stored in the fixed space, whereas if the data are longer than this value, they are stored in a variable space. For disk tables, this value is always 0. 

For more information about variable-length columns and the IN ROW clause, please refer to Chapter1: Data Types.

##### IS_HIDDEN

This indicates whether the column has hidden properties or not. On the creation of function-based indexes, columns with hidden properties are automatically added to the table. One of the following two values is displayed in this column:

- T: Hidden column
- F: Public column

##### IS_KEY_PRESERVED

This indicates whether the column of the join view is modifiable with DML statements(INSERT, UPDATE, DELETE). For columns of regular tables, this value is specified as 'T'; for views, this value is specified as 'T' for modifiable columns, and 'F' for unmodifiable columns.

- T: Modifiable columns
- F: Unmodifiable columns

#### Reference Tables

```
SYS_USERS_
SYS_TABLES_
STO_USER_COLUMNS_
```

### SYS_COMMENTS\_

This meta table is for storing comments such as descriptions of user-defined tables, views and associated columns.

| Column name | Type          | Description            |
| ----------- | ------------- | ---------------------- |
| USER_NAME   | VARCHAR(128)  | The name of the user   |
| TABLE_NAME  | VARCHAR(128)  | The name of the table  |
| COLUMN_NAME | VARCHAR(128)  | The name of the column |
| COMMENTS    | VARCHAR(4000) | The actual comment     |

#### Column Information

##### USER_NAME

This is the name of the table owner. Its value corresponds to one of the USER_NAME values in the SYS_USERS_ meta table.

##### TABLE_NAME

This is the name of the table (or view). Its value is the same as one of the TABLE_NAME values appearing in SYS_TABLES_.

##### COLUMN_NAME

This is the name of a column in the table (or view). Its value is equal to a COLUMN_NAME value in the SYS_COLUMNS_ meta table.

However, if the comment pertains to an entire table (or view), the value for COLUMN_NAME will be NULL.

##### COMMENTS

This is the actual comment written by the user.

#### Reference Tables

```
SYS_USERS_
SYS_TABLES_
SYS_COLUMNS_
```

### SYS_COMPRESSION_TABLES\_

This meta table stores information about compressed columns.

| Column name  | Type    | Description                                                  |
| ------------ | ------- | ------------------------------------------------------------ |
| TABLE_ID     | INTEGER | The identifier of the table with the compressed column       |
| COLUMN_ID    | INTEGER | The identifier of the compressed column                      |
| DIC_TABLE_ID | INTEGER | The identifier of the dictionary table in which data of the compressed column is actually stored |
| MAXROWS      | BIGINT  | The maximum number of rows that can be inserted in the table where data of the compressed column is stored (0: unlimited) |

#### Column Information

##### TABLE_ID

This is the identifier of the table with the compressed column. This value corresponds to one TABLE_ID value of the SYS_TABLES_ meta table.

##### COLUMN_ID

This is the identifier of the compressed column. This value corresponds to one COLUMN_ID value of the SYS_COLUMNS_ meta table.

##### DIC_TABLE_ID

This is the identifier of the dictionary table in which data of the compressed column is actually stored.

##### MAXROWS

This is the maximum number of rows that can be inserted to the dictionary table where data of the compressed column is actually stored.

### SYS_CONSTRAINTS\_

This meta table contains information about table constraints.

| Column name         | Type          | Description                                                  |
| ------------------- | ------------- | ------------------------------------------------------------ |
| USER_ID             | INTEGER       | The user identifier                                          |
| TABLE_ID            | INTEGER       | The table identifier                                         |
| CONSTRAINT_ID       | INTEGER       | The constraint identifier                                    |
| CONSTRAINT_NAME     | VARCHAR(128)  | The name of the constraint                                   |
| CONSTRAINT_TYPE     | INTEGER       | The type of the constraint                                   |
| INDEX_ID            | INTEGER       | The identifier of the index used by the constraint           |
| COLUMN_CNT          | INTEGER       | The number of columns that are associated with the constraint |
| REFERENCED_TABLE_ID | INTEGER       | The identifier of a table referenced in a FOREIGN KEY constraint |
| REFERENCED_INDEX_ID | INTEGER       | The identifier of an index referenced in a FOREIGN KEY constraint |
| DELETE_RULE         | INTEGER       | Whether to perform cascade delete for a FOREIGN KEY constraint 0: Do not perform cascade delete 1: perform cascade delete 2: SET NULL, columns with dependent foreign key values are modified to NULL. |
| CHECK_CONDITION     | VARCHAR(4000) | The character string condition of the CHECK constraint       |
| VALIDATED           | CHAR(1)       | Whether all data conform to the constraint                   |

#### Column Information

##### USER_ID

This is the user identifier, and corresponds to a USER_ID in the SYS_USERS_ meta table.

##### TABLE_ID

This is the identifier for the table associated with the constraint, and will correspond to a TABLE_ID value in the SYS_TABLES_ meta table.

##### CONSTRAINT_ID

This is a constraint identifier. It is automatically assigned by the system sequence.

##### CONSTRAINT_NAME

This is the name of the constraint.

##### CONSTRAINT_TYPE

This indicates the type of the constraint. The possible types are as follows:

- 0: FOREIGN KEY
- 1: NOT NULL
- 2: UNIQUE
- 3: PRIMARY KEY
- 5: TIMESTAMP
- 6: LOCAL UNIQUE
- 7: CHECK

For additional information about each type of constraint, please refer to the description of column constraints in the explanation of the CREATE TABLE statement in the *SQL Reference.* 

##### INDEX_ID

If an index must be created in order to define constraints such as UNIQUE or PRIMARY KEY constraints, the system creates an index internally. This is the identifier of that index, and will correspond to an INDEX_ID in the SYS_INDICES_ meta table.

##### COLUMN_CNT

This is the number of columns associated with the constraint. For example, for a constraint such as UNIQUE (i1, i2, i3), this value would be 3.

##### REFERENCED_TABLE_ID

This is the identifier of a table referenced in a FOREIGN KEY constraint (not the table for which the constraint is defined). This identifier will correspond to a TABLE_ID value in the SYS_TABLES_ meta table.

##### REFERENCED_INDEX_ID

This indicates a UNIQUE or PRIMARY KEY constraint that must exist in a table referenced by a FOREIGN KEY constraint. The identifier of this constraint will be the same as a CONSTRAINT_ID value in the SYS_CONSTRAINTS_ meta table.

##### CHECK_CONDITION

This displays the Integrity Rule defined by the user at CHECK constraint specification. 

##### VALIDATED

This indicates whether all data conform to the constraint. 

#### Reference Tables

```
SYS_USERS_
SYS_TABLES_
SYS_INDICES_
```

### SYS_CONSTRAINT_COLUMNS\_

This meta table contains information about columns related to all constraints defined in user tables.

| Column name          | Type    | Description                                  |
| -------------------- | ------- | -------------------------------------------- |
| USER_ID              | INTEGER | The user identifier                          |
| TABLE_ID             | INTEGER | The table identifier                         |
| CONSTRAINT_ID        | INTEGER | The constraint identifier                    |
| CONSTRAINT_COL_ORDER | INTEGER | The position of the column in the constraint |
| COLUMN_ID            | INTEGER | The column Identifier                        |

#### Column Information

##### USER_ID

This is the user identifier, and corresponds to a USER_ID in the SYS_USERS_ meta table.

##### TABLE_ID

This is the identifier of the table in which the constraint is defined, and corresponds to a TABLE_ID value in the SYS_TABLES_ meta table.

##### CONSTRAINT_ID

This is the identifier of the constraint, and corresponds to a CONSTRAINT_ID value in the SYS_CONSTRAINTS_ meta table.

##### CONSTRAINT_COL_ORDER

This is the position of the column within the constraint. For example, when the constraint UNIQUE (i1,i2,i3) is created, three records are inserted into the SYS_CONSTRAINT_COLUMNS_ meta table. The position of column i1 is 1, column i2 is 2, and column i3 is 3.

##### COLUMN_ID

This is the identifier of the column for which the constraint is defined, and corresponds to a COLUMN_ID value in the SYS_COLUMNS_ meta table.

#### Reference Tables

```
SYS_USERS_
SYS_TABLES_
SYS_CONSTRAINTS_
SYS_COLUMNS_
```

### SYS_CONSTRAINT_RELATED\_

This meta table contains information about the stored functions referenced by the constraints.

| Column name       | Type         | Description                                                  |
| ----------------- | ------------ | ------------------------------------------------------------ |
| USER_ID           | INTEGER      | The user identifier                                          |
| TABLE_ID          | INTEGER      | The table identifier                                         |
| CONSTRAINT_ID     | INTEGER      | The constraint identifier                                    |
| RELATED_USER_ID   | INTEGER      | The identifier of the owner of the stored function referenced by the constraint |
| RELATED_PROC_NAME | VARCHAR(128) | The name of the stored function referenced by the constraint |

#### Column Information

##### USER_ID

This is the identifier of the owner of the constraint, and is identical to one USER_ID value in the SYS_USERS_ meta table. 

##### TABLE_ID

This is the identifier of the table which defines the constraint, and is identical to one TABLE_ID value in the SYS_TABLES_ meta table.

##### CONSTRAINT_ID

This is the identifier of the constraint, and is identical to one CONSTRAINT_ID value in the SYS_CONSTRAINTS_ meta table.

##### RELATED_USER_ID

This is the identifier of the owner of the stored function referenced by the constraint, and is identical to one USER_ID value in the SYS_USERS_ meta table.

##### RELATED_PROC_NAME

This is the name of the stored function referenced by the constraint, and is identical to one PROC_NAME value in the SYS_PROCEDURES_ meta table.

#### Reference Tables

```
SYS_USERS_
SYS_TABLES_
SYS_CONSTRAINTS_
SYS_PROCEDURES_
```

### SYS_DATABASE\_

This is the table that contains the database name and meta table version information.

| Column name    | Type          | Description                             |
| -------------- | ------------- | --------------------------------------- |
| DB_NAME        | VARCHAR(40)   | The database name                       |
| OWNER_DN       | VARCHAR(2048) | Reserved for future use                 |
| META_MAJOR_VER | INTEGER       | The database meta table version (Main)  |
| META_MINOR_VER | INTEGER       | The database meta table version (Sub)   |
| META_PATCH_VER | INTEGER       | The database meta table version (Patch) |

#### Column Information

##### DB_NAME

The database name specified when creating the database is saved.

##### META_MAJOR_VER

This value increases when a meta table is modified, added or removed. If the database version and the corresponding binary version of Altibase do not match, the database must be migrated.

##### META_MINOR_VER

This value increases when the contents of one or more meta tables is modified. If the version of the database does not correspond to the current version of Altibase, the system internally compares this value and automatically upgrades the meta tables to the newer version.

##### META_PATCH_VER

This indicates the meta table patch version. 

### SYS_DATABASE_LINKS\_

This meta table is for storing Database Link information.

| Column name     | Type         | Description                                                  |
| --------------- | ------------ | ------------------------------------------------------------ |
| USER_ID         | INTEGER      | The user identifier                                          |
| LINK_ID         | INTEGER      | The Database Link identifier                                 |
| LINK_OID        | BIGINT       | The Database Link object identifier                          |
| LINK_NAME       | VARCHAR(40)  | The Database Link name                                       |
| USER_MODE       | INTEGER      | The access method to the remote server                       |
| REMOTE_USER_ID  | VARCHAR(128) | The user account for a remote database                       |
| REMOTE_USER_PWD | BYTE(40)     | The user password for a remote database                      |
| LINK_TYPE       | INTEGER      | Indicates whether it is a Heterogeneous Link or a Homogeneous Link. |
| TARGET_NAME     | VARCHAR(40)  | The name of the remote server which the database link object is to access |
| CREATED         | DATE         | The date and time at which the database link object is created |
| LAST_DDL_TIME   | DATE         | The time at which the database link object was most recently changed using a DDL statement |

#### Column Information

##### USER_ID

This is the identifier of the user who owns the Database Link object.

##### LINK_ID

This is the Database Link identifier. 

##### LINK_OID

This is the Database Link object identifier.

##### LINK_NAME

This is the name of the Database Link object, which is specified by the user when the Database Link object is created.

##### USER_MODE

This indicates the mode in which a remote server is accessed.

- 0: DEDICATE USER MODE
- 1: CURRENT USER MODE (reserved for future use)

##### REMOTE_USER_ID

This indicates a user account on a remote server, to be used when accessing a remote database server. 

##### REMOTE_USER_PWD

This is the password for the user account on the remote server, to be used when accessing a remote database server. The password is encrypted using an encryption algorithm before it is stored. 

##### LINK_TYPE

This indicates whether a heterogeneous link or a homogeneous link.

##### TARGET_NAME

This indicates the name of the remote server that the database link object will access.

##### CREATED

This indicates the date when the database link object was created.

##### LAST_DDL_TIME

This indicates the last time a DDL change occurred to a database link object.

### SYS_DIRECTORIES\_

This table contains information about directories that are used when files are managed using stored procedures

| Column name    | Type          | Description                                                  |
| -------------- | ------------- | ------------------------------------------------------------ |
| DIRECTORY_ID   | BIGINT        | The directory identifier                                     |
| USER_ID        | INTEGER       | The user identifier                                          |
| DIRECTORY_NAME | VARCHAR(128)  | The directory name                                           |
| DIRECTORY_PATH | VARCHAR(4000) | The absolute path of the directory on the system             |
| CREATED        | DATE          | The time at which the directory was created                  |
| LAST_DDL_TIME  | DATE          | The most recent time at which a DDL task was used to change the directory object |

#### Column Information

##### DIRECTORY_ID

This is a directory identifier. It is a unique value within the system.

##### USER_ID

This is the user identifier of the owner of the directory.

##### DIRECTORY_NAME

This is the name of the directory. It is a unique value within the system.

##### DIRECTORY_PATH

This is the absolute path where the directory is located. This value is explicitly set by the user when executing a CREATE DIRECTORY statement.

##### LAST_DDL_TIME

This is the most recent time at which a DDL task was used to change the directory object.

### SYS_ENCRYPTED_COLUMNS\_

This is the meta table for managing additional security information based on the security settings for individual columns.

| Column name       | Type         | Description                                                  |
| ----------------- | ------------ | ------------------------------------------------------------ |
| USER_ID           | INTEGER      | The identifier of the owner of the table to which the column belongs |
| TABLE_ID          | INTEGER      | The identifier of the table to which the column belongs      |
| COLUMN_ID         | INTEGER      | The identifier of the encrypted column                       |
| ENCRYPT_PRECISION | INTEGER      | The precision of the column encryption                       |
| POLICY_NAME       | VARCHAR(16)  | The name of the encryption policy                            |
| POLICY_CODE       | VARCHAR(128) | The verification code of the encryption policy               |

### SYS_GRANT_OBJECT\_

This contains information about object privileges granted to a user.

| Column name       | Type       | Description                                                  |
| ----------------- | ---------- | ------------------------------------------------------------ |
| GRANTOR_ID        | INTEGER    | The identifier of the user who granted the privileges        |
| GRANTEE_ID        | INTEGER    | The identifier of the user to whom the privileges were granted |
| PRIV_ID           | INTEGER    | The privilege identifier                                     |
| USER_ID           | INTEGER    | The identifier of the owner of the object                    |
| OBJ_ID            | BIGINT     | The identifier of the object                                 |
| OBJ_TYPE          | VARCHAR(1) | The type of object                                           |
| WITH_GRANT_OPTION | INTEGER    | Indicates whether the WITH_GRANT_OPTION is used when object access privileges are granted 0: Not used 1: Used |

#### Column Information

##### GRANTOR_ID

This is the identifier of the user who granted the privilege, and corresponds to a USER_ID in the SYS_USERS_ meta table.

##### GRANTEE_ID

This is the identifier of the user to whom the privilege has been granted, and corresponds to a USER_ID in the SYS_USERS_ meta table. If an object privilege is granted to PUBLIC, however, the USER_ID value "0"(which does not exist in the SYS_USERS_ meta table) is displayed in this column.

##### PRIV_ID

This is the identifier of the privilege. It corresponds to a PRIV_ID in the SYS_PRIVILEGES_ meta table.

##### USER_ID

This is the user ID of the owner of the object for which the privilege has been granted. This value will correspond to a USER_ID in the SYS_USERS_ meta table.

##### OBJ_ID

This is the ID of the object for which the privilege has been granted. It corresponds with one, and only one, target object ID saved in the appropriate meta table. 

If the target object is a table, view or sequence, it is mapped to a TABLE_ID in the SYS_TABLES_ meta table, whereas if it is a stored procedure or stored function, it is mapped to a PROC_OID in the SYS_PROCEDURES_ meta table.

##### OBJ_TYPE

This is the type of the object related to the privilege.

- A: Stored package
- D: Directory
- T: Table or View
- S: Sequence
- P: Stored procedure or function
- Y: Library

##### WITH_GRANT_OPTION

The WITH_GRANT_OPTION indicates whether the user to whom the privilege was granted is permitted to grant the privilege to other users.

#### Reference Tables

```
SYS_USERS_
SYS_PRIVILEGES_
SYS_TABLES_
SYS_PROCEDURES_
```

### SYS_GRANT_SYSTEM\_

This contains information about system privileges granted to users

| Column name | Type    | Description                                                  |
| ----------- | ------- | ------------------------------------------------------------ |
| GRANTOR_ID  | INTEGER | The identifier of the user who granted the privilege         |
| GRANTEE_ID  | INTEGER | The identifier of the user to whom the privilege was granted |
| PRIV_ID     | INTEGER | The identifier of the privilege                              |

#### Column Information

##### GRANTOR_ID

This is the identifier of the user who granted the privilege, and corresponds to a USER_ID in the SYS_USERS_ meta table.

##### GRANTEE_ID

This is the identifier of the user to whom the privilege was granted, and corresponds to a USER_ID in the SYS_USERS_ meta table.

##### PRIV_ID

This is the identifier of the privilege, and corresponds to a PRIV_ID found in the SYS_PRIVILEGES_ meta table.

#### Reference Tables

```
SYS_USERS_
SYS_PRIVILEGES_
```

### SYS_INDEX_COLUMNS\_

This is the meta table that contains information about all columns associated with indexes defined for all tables.

| Column name     | Type    | Description                             |
| --------------- | ------- | --------------------------------------- |
| USER_ID         | INTEGER | The identifier of the user              |
| INDEX_ID        | INTEGER | The identifier of the index             |
| COLUMN_ID       | INTEGER | The column identifier                   |
| INDEX_COL_ORDER | INTEGER | The position of the column in the index |
| SORT_ORDER      | CHAR(1) | The sort order                          |
| TABLE_ID        | INTEGER | The table identifier                    |

#### Column Information

##### USER_ID

This is the identifier of the owner of the index, and corresponds to a USER_ID in the SYS_USERS_ meta table.

##### INDEX_ID

This is the identifier of the index, and corresponds to an INDEX_ID in the SYS_INDICES_ meta table.

##### COLUMN_ID

This is the identifier of the column for which the index was created, and corresponds to a COLUMN_ID in the SYS_COLUMNS_ meta table.

##### INDEX_COL_ORDER

In the case of a composite index, because a single index spans multiple columns, this value indicates the position of the column in the index

##### SORT_ORDER

This indicates whether the index is arranged in ascending or descending order.

- A: Ascending order
- D: Descending order

##### TABLE_ID

This is the identifier of the table in which the index was created, and corresponds to a TABLE_ID value in the SYS_TABLES_ meta table.

#### Reference Tables

```
SYS_USERS_
SYS_TABLES_
SYS_COLUMNS_
SYS_INDICES_
```

### SYS_INDEX_PARTITIONS\_ 

This is the meta table for managing index partitions.

| Column name          | Type          | Description                                                  |
| -------------------- | ------------- | ------------------------------------------------------------ |
| USER_ID              | INTEGER       | The user identifier                                          |
| TABLE_ID             | INTEGER       | The tablespace identifier                                    |
| INDEX_ID             | INTEGER       | The index identifier                                         |
| TABLE_PARTITION_ID   | INTEGER       | The table partition identifier                               |
| INDEX_PARTITION_ID   | INTEGER       | The index partition identifier                               |
| INDEX_PARTITION_NAME | VARCHAR(128)  | The index partition name                                     |
| PARTITION_MIN_VALUE  | VARCHAR(4000) | Reserved for future use                                      |
| PARTITION_MAX_VALUE  | VARCHAR(4000) | Reserved for future use                                      |
| TBS_ID               | INTEGER       | The tablespace identifier                                    |
| CREATED              | DATE          | The date and time at which the index parition is created     |
| LAST_DDL_TIME        | DATE          | The time at which the index partition was most recently changed using a DDL statement |

#### Column Information

##### USER_ID

This is the user identifier of the owner of the index. It corresponds to a USER_ID in the SYS_USERS_ meta table.

##### TABLE_ID

This is the identifier of the table in which the index is created. It is the same as a TABLE_ID value in the SYS_TABLES_ meta table.

##### INDEX_ID

This is the index identifier, and corresponds to an INDEX_ID in the SYS_INDICES_ meta table.

##### TABLE_PARTITION_ID

This is the table partition identifier. 

##### INDEX_PARTITION_ID

This is the index partition identifier.

##### INDEX_PARTITION_NAME

This is the name of the index partition. It is specified by the user.

##### TBS_ID

This is the identifier of the tablespace in which the index is stored.

#### Reference Tables

```
SYS_USERS_
SYS_TABLES_
SYS_INDICES_
SYS_TABLE_PARTITIONS_
```

### SYS_INDEX_RELATED\_

This meta table contains information about the stored functions on which the function-based indexes are based. 

| Column name       | Type         | Description                                                  |
| ----------------- | ------------ | ------------------------------------------------------------ |
| USER_ID           | INTEGER      | The user identifier                                          |
| TABLE_ID          | INTEGER      | The table identifier                                         |
| INDEX_ID          | INTEGER      | The index identifier                                         |
| RELATED_USER_ID   | INTEGER      | The identifier of the owner of the stored function referenced by the index |
| RELATED_PROC_NAME | VARCHAR(128) | ) The name of the stored function referenced by the index    |

#### Column Infomation

##### USER_ID

This is the identifier of the owner of the index, and is identical to one USER_ID value in the SYS_USERS_ meta table.

##### TABLE_ID

This is the identifier of the table which defined the index, and is identical to one TABLE_ID value in the SYS_TABLES_ meta table.

##### INDEX_ID

This is the identifier of the index, and is identical to one INDEX_ID value in the SYS_INDICES_ meta table.

##### RELATED_USER_ID

This is the identifier of the owner of the stored function referenced by the index, and is identical to one USER_ID value in the SYS_USERS_ meta table.

##### RELATED_PROC_NAME

This is the name of the stored function referenced by the index, and is identical to one PROC_NAME value in the SYS_PROCEDURES_ meta table.

#### Reference Tables

```
SYS_USERS_
SYS_TABLES_
SYS_INDICES_
SYS_PROCEDURES_
```

### SYS_INDICES\_

This is the meta table that contains information about all indexes defined for all tables.

| Column name    | Type         | Description                                                  |
| -------------- | ------------ | ------------------------------------------------------------ |
| USER_ID        | INTEGER      | The user identifier                                          |
| TABLE_ID       | INTEGER      | The table identifier                                         |
| INDEX_ID       | INTEGER      | The index identifier                                         |
| INDEX_NAME     | VARCHAR(128) | The index name                                               |
| INDEX_TYPE     | INTEGER      | The index type                                               |
| IS_UNIQUE      | CHAR(1)      | Indicates whether the use of duplicate key values is allowed |
| COLUMN_CNT     | INTEGER      | The number of columns in the index                           |
| IS_RANGE       | CHAR(1)      | Indicates whether range scanning is possible using the index |
| IS_PERS        | CHAR(1)      | Indicates whether or not to permanently store the index      |
| IS_DIRECTKEY   | CHAR(1)      | Indicates whether the index is a direct key index            |
| TBS_ID         | INTEGER      | The tablespace identifier                                    |
| IS_PARTITIONED | CHAR(1)      | Indicates whether the index is partitioned                   |
| INDEX_TABLE_ID | INTEGER      | Indicates the identifier for tables created by non-partitioned index of the partitioned table |
| CREATED        | DATE         | Indicates when the index was created                         |
| LAST_DDL_TIME  | DATE         | The time at which the index was most recently changed using a DDL statement |

#### Column Information

##### USER_ID

This is the identifier of the owner of the index, and corresponds to a USER_ID value in the SYS_USERS_ meta table.

##### TABLE_ID

This is the identifier of the table in which the index was created, and corresponds to a TABLE_ID of the SYS_TABLES_ meta table.

##### INDEX_ID

This is an index identifier. It is automatically assigned by the system sequence.

##### INDEX_NAME

This is the name of the index.

##### INDEX_TYPE

This indicates the index type. A value of 1 indicates a B-TREE index, while a value of 2 indicates an R-TREE index. 

##### IS_UNIQUE

This is indicates whether range scanning is possible using the index.

- T: Range scanning is possible.
- F: Range scanning is not possible.

##### COLUMN_CNT

This is the number of columns with which the index is associated.

##### IS_RANGE

This is indicates whether range scanning is possible using the index.

- T: Range scanning is possible.
- F: Range scanning is not possible.

##### IS_DIRECTKEY

This indicates whether the index is a direct key index. 

- T: Direct key index
- F: Normal index

##### TBS_ID

This is the identifier of the tablespace in which the index was created.

##### IS_PARTITIONED

This indicates whether the index is partitioned. If it is ‘T’, the index is partitioned. If it is ‘F’, the index is not partitioned.

#### Reference Tables

```
SYS_USERS_
SYS_TABLES_
```

### SYS_JOBS\_

This meta table stores information about job objects.

| Column name    | Type          | Description                                                  |
| -------------- | ------------- | ------------------------------------------------------------ |
| JOB_ID         | INTEGER       | The job identifier                                           |
| JOB_NAME       | VARCHAR(128)  | The job name                                                 |
| EXEC_QUERY     | VARCHAR(1000) | The procedure registered for the job                         |
| START_TIME     | DATE          | The first time the job starts                                |
| END_TIME       | DATE          | The time the job ends                                        |
| INTERVAL       | INTEGER       | The interval after which the job is to run                   |
| INTERVAL_TYPE  | CHAR(2)       | The unit of the interval after which the job is to run(YY, MM, DD, HH, MI) |
| STATE          | INTEGER       | The status of the job currently executing. 0: Is not running 1: Is running |
| LAST_EXEC_TIME | DATE          | The last time the job was run                                |
| EXEC_COUNT     | INTEGER       | Execution frequency of the job                               |
| ERROR_CODE     | CHAR(7)       | An error code(NULL indicates success.)                       |
| IS_ENABLE      | CHAR(1)       | The status of job execution in the job scheduler. T: Possible to execute F: Impossible to execute |
| COMMENT        | VARCHAR(4000) | An additional description for the job                        |

#### Column Information

##### EXEC_QUERY

This indicates the procedure which is registered for the JOB and is executed.

##### INTERVAL_TYPE

This indicates the unit of time when an interval is set for the JOB. If a value exists in the INTERVAL column, this is the unit of the value.

- YY: Year
- MM: Mouth
- DD: Day
- HH: Hour
- MI: Minute

##### STATE

This indicates if a JOB is currently being executed or not.

- 0: Being executed
- 1: Not being executed

##### EXEC_COUNT

This indicates how many times a registered procedure has been executed since a JOB was created.

##### ERROR_CODE

This indicates the error code displaed if a procedure failed when the las JOB was executed. If succeeds, it is NULL.

##### IS_ENABLE

This indicates the possiblity of job execution in the job scheduler.

- T: Executable
- F: Not executable

##### COMMENT

This statement is used to describe a JOB. If the description is not delineated, NULL values are queried.

### SYS_LIBRARIES\_

This is the meta table that contains information about external library objects.

| Column name   | Type          | Description                                                  |
| ------------- | ------------- | ------------------------------------------------------------ |
| LIBRARY_ID    | BIGINT        | The library identifier                                       |
| USER_ID       | INTEGER       | The user identifier                                          |
| LIBRARY_NAME  | VARCHAR(128)  | The library name                                             |
| FILE_SPEC     | VARCHAR(4000) | The file path of the dynamic library                         |
| DYNAMIC       | VARCHAR(1)    | Reserved for future use                                      |
| STATUS        | VARCHAR(7)    | Reserved for future use                                      |
| CREATED       | DATE          | The time at which the library object was created             |
| LAST_DDL_TIME | DATE          | The time at which the library object was changed using a DDL statement for the last time. |

#### Column Information

##### LIBRARY_ID

This is the library identifier and has a unique value within the system.

##### USER_ID

This is the user identifier of the library owner.

##### LIBRARY_NAME

This is the name of the library object and it has a unique value within the system.

##### FILE_SPEC

This is the file path of the dynamic library which the library object points to and it is a relative path for the default file path of the library($ALTIBASE_HOME/lib). 

### SYS_LOBS\_

This is the meta table containing information about LOB columns defined in tables.

| Column name    | Type    | Description                                                  |
| -------------- | ------- | ------------------------------------------------------------ |
| USER_ID        | INTEGER | The user identifier                                          |
| TABLE_ID       | INTEGER | The table identifier                                         |
| COLUMN_ID      | INTEGER | The column identifier                                        |
| TBS_ID         | INTEGER | The tablespace identifier                                    |
| LOGGING        | CHAR(1) | This field is reserved for future use.                       |
| BUFFER         | CHAR(1) | This field is reserved for future use.                       |
| IS_DEFAULT_TBS | CHAR(1) | Indicates whether a tablespace is designated for LOB column storage T: Specify F: Not to specify |

#### Column Information

##### USER_ID

This is the identifier of the owner of the table to which the LOB column belongs, and corresponds to a USER_ID value in the SYS_USERS_ meta table.

##### TABLE_ID

This is the identifier of the table to which the LOB column belongs, and corresponds to a TABLE_ID value in the SYS_TABLES_ meta table.

##### COLUMN_ID

This is the LOB column identifier.

##### TBS_ID

This is the identifier of the tablespace to which the LOB column belongs. 

##### IS_DEFAULT_TBS

This indicates whether a tablespace for storing a LOB column was specified by the user when the LOB column was created. 

* T: Specify 
* F Not to specify

For more detailed information, please refer to CREATE TABLE > LOB_STORAGE_CLAUSE statement in the *SQL reference*.

#### Reference Tables

```
SYS_USERS_
SYS_TABLES_
SYS_COLUMNS_
```

### SYS_MATERIALIZED_VIEWS\_

This is a meta table that contains information about materialized views.

| Column name       | Type         | Description                                                  |
| ----------------- | ------------ | ------------------------------------------------------------ |
| USER_ID           | INTEGER      | The user identifier                                          |
| MVIEW_ID          | INTEGER      | The materialized view identifier                             |
| MVIEW_NAME        | VARCHAR(128) | The materialized view name                                   |
| TABLE_ID          | INTEGER      | The table identifier                                         |
| VIEW_ID           | INTEGER      | The view identifier                                          |
| REFRESH_TYPE      | CHAR(1)      | The refresh type                                             |
| REFRESH_TIME      | CHAR(1)      | The refresh time                                             |
| CREATED           | DATE         | The time at which the table was created                      |
| LAST_DDL_TIME     | DATE         | The time when DDL was most recently used to make changes to a stored procedure |
| LAST_REFRESH_TIME | DATE         | The last time the materialized view was refreshed            |

#### Column Information

##### USER_ID

This is the user identifier for the owner of the materialized view, it is identical to a USER_ID value of the SYS_USERS_ meta table.

##### MVIEW_ID

This is the materialized view identifier, automatically assigned by the database.

##### MVIEW_NAME

This is the name of the materialized view specified by the user.

##### TABLE_ID

This is the identifier for the table automatically created for the maintenance of the data of the materialized view. A table with the identical name of the materialized view can be checked by querying SYS_TABLES_ meta table with this identifier.

##### VIEW_ID

This is the identifier for the view automatically created for the maintenance of the data of the materialized view. This view can be looked up with this identifier at SYS_VIEWS_ meta table.

##### REFRESH_TYPE

This is the value taht indicates the refresh time of the materialized view.

- C: COMPLETE
- F: FAST
- R: FORCE

##### REFRESH_TIME

This is the value that indicates the refresh time of the materialized view.

- D: ON DEMAND
- C: ON COMMIT

##### CREATED

This is the date and time that the materialized view is created.

##### LAST_DDL_TIME

This is the date and time that the last alterations to the materialized view were made.

##### LAST_REFERESH_TIME

This is the date and time that the materialized view was refreshed lastly.

#### Reference Tables

```
SYS_USERS_
SYS_TABLES_
SYS_VIEWS_
SYS_VIEW_PARSE_
```

### SYS_PACKAGES\_

This meta table shows information about packages.

| Column name   | Type         | Description                                                  |
| ------------- | ------------ | ------------------------------------------------------------ |
| USER_ID       | INTEGER      | The user identifier of the package owner                     |
| PACKAGE_OID   | BIGINT       | The package identifier                                       |
| PACKAGE_NAME  | VARCHAR(128) | The package name                                             |
| PACKAGE_TYPE  | INTEGER      | The package type. Indicates whether it is the package specification or the package body. 6: Package specification 7: Package body |
| AUTHID        | INTEGER      | The authority to execute the package 0: The definer 1: The current user |
| STATUS        | INTEGER      | The package status. If INVALID, the package is non-executable. 0: VALID 1: INVALID |
| CREATED       | DATE         | The time at which the package was created                    |
| LAST_DDL_TIME | DATE         | The last time at which a DDL task was used to change the package |

#### Column Information

##### USER_ID

This is the user identifier of the package owner; this value corresponds to one of the USER_ID values in the SYS_USERS_ meta table.

##### PACKAGE_OID

This is the package identifier; this value is automatically assigned by the system.

##### PACKAGE_NAME

This is the package name.

##### PACKAGE_TYPE

This is the value which indicates whether it is the package specification or the package body.

- 6: Package specification
- 7: Package body

##### AUTHID

This is the value which indicates authority to execute the package.

- 0: The definer
- 1: The current user

##### STATUS

This is the value which indicates whether or not the package is executable. 0(VALID) indicates that the package is executable.

- 0: VALID
- 1: INVALID

##### CREATED

This is the value which indicates the time at which the package was created.

##### LAST_DDL_TIME

This is the value which indicates the last time at which a DDL task was used to change the package.

#### Reference Table

```
SYS_USERS_
```

### SYS_PACKAGE_PARAS\_

This meta table contains information about subprogram(stored procedures and stored functions) parameters contained in packages.

| Column name  | Type          | Description                                                  |
| ------------ | ------------- | ------------------------------------------------------------ |
| USER_ID      | INTEGER       | The user identifier of the package owner                     |
| OBJECT_NAME  | VARCHAR(128)  | The subprogram name                                          |
| PACKAGE_NAME | VARCHAR(128)  | The package name                                             |
| PACKAGE_OID  | BIGINT        | The package identifier                                       |
| SUB_ID       | INTEGER       | The subprogram identifier                                    |
| SUB_TYPE     | INTEGER       | The subprogram type 0: Procedure 1: Function                 |
| PARA_NAME    | VARCHAR(128)  | The name of the subprogram parameter                         |
| PARA_ORDER   | INTEGER       | The position of the parameter. The first parameter is assigned 1. |
| INOUT_TYPE   | INTEGER       | Whether the parameter is an Input, Output, or Input/Output parameter |
| DATA_TYPE    | INTEGER       | The parameter data type                                      |
| LANG_ID      | INTEGER       | The language identifier of the parameter type                |
| SIZE         | INTEGER       | The size of the parameter type                               |
| PRECISION    | INTEGER       | The precision of the parameter type                          |
| SCALE        | INTEGER       | The scale of the parameter type                              |
| DEFAULT_VAL  | VARCHAR(4000) | The default value of the parameter                           |

#### Column Information

##### USER_ID

This is the user identifier of the stored procedure or stored function owner; this value corresponds to one of the USER_ID values in the SYS_USERS_ meta table.

##### OBJECT_NAME

This is the subprogram name.

##### PACKAGE_NAME

This is the package name.

##### PACKAGE_OID

This is the package identifier and is identical to one of the values of PACKAGE_OID, which is the package specification in the SYS_PACKAGES_ meta table. This is the package identifier; this value corresponds to one of the PACKAGE_OID values in the package specification of the SYS_ PACKAGES _ meta table.

##### SUB_ID

This is the subprogram identifier. Inside a package, subprogram identifiers start from 1 and are assigned numbers in the order in which they are written. 

##### SUB_TYPE

This is the value which indicates whether the subprogram is a stored procedure or a stored function

- 0: Procedure
- 1: Function

##### PARA_NAME

This is the name of the subprogram parameter.

##### PARA_ORDER

This is the value which indicates the nth order in which the given parameter was defined among other parameters.

##### INOUT_TYPE

This is the value which indicates whether the parameter of the stored procedure or stored function is an INPUT, OUTPUT or INPUT/OUTPUT parameter.

- 0: IN
- 1: OUT
- 2: IN OUT

##### DATA_TYPE

This is the identifier of the parameter data type. Please refer to the description of the DATA_TYPE column in the SYS_COLUMNS_ meta table for the value of the data type identifier. 

For more detailed information about data types, please refer to Chapter 1.

##### LANG_ID

This is the column which displays information about the language properties of the character data types (CHAR, VARCHAR).

##### SIZE

This is the physical size of the data type.

##### PRECISION

This is the precision of the parameter data type, and is either specified by the user or assigned a default value by the system. For character data types, this value is the user-specified length of the character data type. 

##### SCALE

This is the scale of the parameter data type, and is either specified by the user or assigned a default value by the system. Depending on the data type, the use of this value can be unnecessary. 

For more detailed information about the scale and precision of data types, please refer to Chapter 1.

##### DEFAULT_VAL

This is the default parameter value specified by the user at the definition of a parameter.

#### Reference Tables

```
SYS_USERS_
SYS_PACKAGES_
```

### SYS_PACKAGE_PARSE\_

This meta table contains the statement text of user-defined packages.

| Column name  | Type         | Description                                                  |
| ------------ | ------------ | ------------------------------------------------------------ |
| USER_ID      | INTEGER      | The user identifier of the package owner                     |
| PACKAGE_OID  | BIGINT       | The package identifier                                       |
| PACKAGE_TYPE | INTEGER      | The package type. Indicates whether it is the package specification or the package body. 6: Package specification 7: Package body |
| SEQ_NO       | INTEGER      | The position of the record among multiple records of split and saved statements |
| PARSE        | VARCHAR(100) | The statement which was split and saved                      |

#### Column Information

##### USER_ID

This is the user identifier of the package owner; this value corresponds to one of the USER_ID values in the SYS_USERS_ meta table.

##### PACKAGE_OID

This is the package identifier; this value corresponds to one of the PACKAGE_OID values in the SYS_ PACKAGES_ meta table.

##### PACKAGE_TYPE

This is the value which indicates whether it is the package specification or the package body.

- 6: Package specification
- 7: Package body

##### SEQ_NO

This is the value which indicates the nth order of each record among multiple records of split and saved package statements in SYS_PACKAGE_PARSE_.

##### PARSE

This is the string piece of the package statement. A CREATE PACKAGE statement can be made by searching for records with one PACKAGE_OID value and adding the PARSE values in the SEQ_NO order.

#### Reference Tables

```
SYS_USERS_
SYS_PACKAGES_
```

### SYS_PACKAGE_RELATED\_

This meta table contains information about tables, sequences, stored procedures, stored functions or views that are accessed by stored procedures and stored functions inside the package.

| Column name         | Type         | Description                                                  |
| ------------------- | ------------ | ------------------------------------------------------------ |
| USER_ID             | INTEGER      | The user identifier of the package owner                     |
| PACKAGE_OID         | BIGINT       | The package identifier                                       |
| RELATED_USER_ID     | INTEGER      | The owner identifier of the object referenced inside the package |
| RELATED_OBJECT_NAME | VARCHAR(128) | The object name referenced inside the package                |
| RELATED_OBJECT_TYPE | INTEGER      | The object type referenced inside the package                |

#### Column Information

##### USER_ID

This is the user identifier of the package owner; this value corresponds to one of the USER_ID values in the SYS_USERS_ meta table.

##### PACKAGE_OID

This is the package identifier; this value corresponds to the one of the PACKAGE_OID values in the SYS_ PACKAGES_ meta table.

##### RELATED_USER_ID

This is the user identifier of the owner of the object accessed by the stored procedure; this value corresponds to one of the USER_ID values in the SYS_USERS_ meta table.

##### RELATED_OBJECT_TYPE

This is the value which indicates the type of the object accessed by the stored procedure.

- 0: Stored procedure
- 1: Stored function
- 2: Table, sequence, view
- 3: Type set
- 4: Database link

#### Reference Tables

```
SYS_USERS_
SYS_PACKAGES_  
SYS_TABLES_
```

### SYS_PART_INDICES\_ 

This is the meta table for managing partitioned indexes. It contains information about partitioned indexes for which IS_PARTITIONED in SYS_INDICES_ is set to ‘Y’.

| Column name     | Type    | Description                                        |
| --------------- | ------- | -------------------------------------------------- |
| USER_ID         | INTEGER | The user identifier                                |
| TABLE_ID        | INTEGER | The table identifier                               |
| INDEX_ID        | INTEGER | The index identifier                               |
| PARTITION_TYPE  | INTEGER | The partition type                                 |
| IS_LOCAL_UNIQUE | CHAR(1) | Indicates whether an index is a local unique index |

#### Column Information

##### USER_ID

This is the user identifier of the owner of the index, and corresponds to a USER_ID in the SYS_USERS_ meta table.

##### TABLE_ID

This is the identifier of the table for which the index was created, and corresponds to a TABLE_ID value in the SYS_TABLES_ meta table.

##### INDEX_ID

This is the index identifier. It corresponds to an INDEX_ID value in the SYS_INDICES_ meta table.

##### PARTITION_TYPE

This indicates whether the partition type is LOCAL or GLOBAL. However, because the GLOBAL partition type is not supported at present, it is always 0.

- 0: LOCAL
- 1: GLOBAL

##### IS_LOCAL_UNIQUE

This indicates whether an index is a local unique index, and can be ‘T’ or ‘F’. 

- T: A local unique index
- F: Not a local unique index

#### Reference Tables

```
SYS_USERS_
SYS_TABLES_
SYS_INDICES_
```

### SYS_PART_KEY_COLUMNS\_ 

This meta table shows information about the partitioning key columns for the partitioned objects

| Column name      | Type    | Description                                                  |
| ---------------- | ------- | ------------------------------------------------------------ |
| USER_ID          | INTEGER | The user identifier                                          |
| PARTITION_OBJ_ID | INTEGER | The partitioned object identifier                            |
| COLUMN_ID        | INTEGER | The column identifier                                        |
| OBJECT_TYPE      | INTEGER | The object type                                              |
| PART_COL_ORDER   | INTEGER | The position of the column in the partitioning key (starting with 0) |

#### Column Information

##### USER_ID

This is the identifier of the owner of the partitioned table or index. It corresponds to a USER_ID value in the SYS_USERS_ meta table.

##### PARTITION_OBJ_ID

This is the identifier of a partitioned object, and corresponds to a TABLE_ID value in the SYS_PART_TABLES_ meta table or INDEX_ID value in the SYS_PART_INDICES_ meta table.

##### COLUMN_ID

This is the identifier of the column in the partitioning key, and corresponds to a COLUMN_ID value in the SYS_COLUMNS_ meta table. 

##### OBJECT_TYPE

This identifies the type of the object.

- 0: TABLE
- 1: INDEX

##### PART_COL_ORDER

This is the position of the column in the partitioning key (starting with 0).

#### Reference Tables

```
SYS_PART_INDICES_
SYS_TABLE_PARTITIONS_
SYS_COLUMNS_
```

### SYS_PART_LOBS\_

This is a meta table for managing LOB columns for respective partitions.

| Column name  | Type    | Description                            |
| ------------ | ------- | -------------------------------------- |
| USER_ID      | INTEGER | The user identifier                    |
| TABLE_ID     | INTEGER | The table identifier                   |
| PARTITION_ID | INTEGER | The partition identifier               |
| COLUMN_ID    | INTEGER | The column identifier                  |
| TBS_ID       | INTEGER | The tablespace identifier              |
| LOGGING      | CHAR(1) | This field is reserved for future use. |
| BUFFER       | CHAR(1) | This field is reserved for future use. |

#### Column Information

##### USER_ID

This is the identifier of the owner of the table to which the LOB column belongs, and corresponds to a USER_ID value in the SYS_USERS_ meta table.

##### TABLE_ID

This is the identifier of the table to which the LOB column belongs, and corresponds to a TABLE_ID value in the SYS_TABLES_ meta table.

##### PARTITION_ID

This is the identifier of the partition in which the LOB column is stored.

##### COLUMN_ID

This is the LOB column identifier.

##### TBS_ID

This is the identifier of the tablespace to which the LOB column belongs. 

#### Reference Tables

```
SYS_USERS_
SYS_TABLES_
SYS_PART_TABLES_
SYS_COLUMNS_
```

### SYS_PART_TABLES\_ 

This is the meta table for the management of partitioned tables. The table information in SYS_PART_TABLES_ is information about partitioned tables for which IS_PARTITIONED in SYS_TABLES_ is set to 'Y'.

| Column name         | Type    | Description                                                  |
| ------------------- | ------- | ------------------------------------------------------------ |
| USER_ID             | INTEGER | The user identifier                                          |
| TABLE_ID            | INTEGER | The table identifier                                         |
| PARTITION_METHOD    | INTEGER | The partitioning method                                      |
| PARTITION_KEY_COUNT | INTEGER | The number of partition key columns                          |
| ROW_MOVEMENT        | CHAR(1) | Indicates whether updated records can be moved between partitions |

#### Column Information

##### USER_ID

This is the identifier of the owner of the index, and corresponds to a USER_ID value in the SYS_USERS_ meta table.

##### TABLE_ID

This is the identifier of the table in which the index was created, and corresponds to a TABLE_ID value in the SYS_TABLES_ meta table.

##### PARTITION_METHOD

This indicates the partitioning method.

- 0: RANGE
- 1: HASH
- 2: LIST

##### ROW_MOVEMENT

This indicates whether it is permissible for records that have been updated to be moved to other partitions when the value of a partition key column is updated. 

- T: Movement of updated records between partition is permitted
- F: Movement of updated records between partition is forbidden

#### Reference Tables

```
SYS_USERS_
SYS_TABLES_
```

### SYS_PASSWORD_HISTORY\_

This meta table stores alterations made to user passwords that have been assigned a password policy.

| Column name   | Type         | Description                                                  |
| ------------- | ------------ | ------------------------------------------------------------ |
| USER_ID       | INTEGER      | The user identifier                                          |
| PASSWORD      | VARCHAR(256) | The user password                                            |
| PASSWORD_DATE | DATE         | The date one which alterations are made to the user password |

### SYS_PASSWORD_LIMITS\_

This meta table stores specified password management policies at user creation and account status quo.

| Column name              | Type         | Description                                                  |
| ------------------------ | ------------ | ------------------------------------------------------------ |
| USER_ID                  | INTEGER      | The user identifier                                          |
| USER_NAME                | VARCHAR(128) | The user name                                                |
| ACCOUNT_STATUS           | VARCHAR(30)  | Indicates account status quo: EXPIRED EXPIRED(GRACE) LOCKED(TIMED) LOCKED EXPIRED & LOCKED(TIMED) EXPIRED(GRACE) & LOCKED(TIMED) EXPIRED & LOCKED EXPIRED(GRACE) & LOCKED |
| REMAIN_GRACE_DAY         | VARCHAR(10)  | The grace period remaining after password expiry date        |
| FAILED_LOGIN_ATTEMPTS    | VARCHAR(10)  | The maximum number of times login failure is permitted       |
| PASSWORD_LOCK_TIME       | VARCHAR(10)  | The amount of time needed to elapse for a locked account to become unlocked |
| PASSWORD_LIFE_TIME       | VARCHAR(10)  | The password validity period                                 |
| PASSWORD_GRACE_TIME      | VARCHAR(10)  | The grace period following password expiry date              |
| PASSWORD_REUSE_TIME      | VARCHAR(10)  | The amount of time needed to elapse for identical passwords to be available for reuse |
| PASSWORD_REUSE_MAX       | VARCHAR(10)  | The number of times identical passwords are available for reuse |
| PASSWORD_VERIFY_FUNCTION | VARCHAR(128) | The CALLBACK function for verifying passwords                |

### SYS_PRIVILEGES\_

This meta table contains information about the kinds of privileges supported by Altibase. For more detailed information, please refer to the descriptions of database privileges and of the GRANT statement in the Reference

| Column name | Type         | Description              |
| ----------- | ------------ | ------------------------ |
| PRIV_ID     | INTEGER      | The privilege identifier |
| PRIV_TYPE   | INTEGER      | The privilege type       |
| PRIV_NAME   | VARCHAR(128) | The privilege name       |

#### Column Information

##### PRIV_ID

This is the privilege identifier. It is defined internally by the system.

##### PRIV_TYPE

This indicates the type of privilege.

- 1: Indicates an object privilege
- 2: Indicates a system privilege

##### PRIV_NAME

This is the name of the privilege.

### SYS_PROCEDURES\_

This table is for storing information about stored procedures and stored functions, such as the stored procedure name, return type, number of parameters, whether it can be executed, etc.

| Column name      | Type         | Description                                                  |
| ---------------- | ------------ | ------------------------------------------------------------ |
| USER_ID          | INTEGER      | The identifier of the owner of the stored procedure          |
| PROC_OID         | BIGINT       | The identifier of the stored procedure                       |
| PROC_NAME        | VARCHAR(128) | The name of the stored procedure                             |
| OBJECT_TYPE      | INTEGER      | Indicates whether the object is a stored procedure, stored function, or type set |
| STATUS           | INTEGER      | Indicates the status of the object. The object cannot be executed if it is INVALID. 0: VALID 1: INVALID |
| AUTHID           | INTEGER      | The authority to execute the package 0: The definer 1: The current user |
| PARA_NUM         | INTEGER      | The number of parameters for the stored procedure            |
| RETURN_DATA_TYPE | INTEGER      | The return data type for the stored function                 |
| RETURN_LANG_ID   | INTEGER      | The return type language identifier                          |
| RETURN_SIZE      | INTEGER      | The size of the stored function return data type             |
| RETURN_PRECISION | INTEGER      | The precision of the stored function return data type        |
| RETURN_SCALE     | INTEGER      | The size of the stored function return data type             |
| PARSE_NO         | INTEGER      | The number of records containing statement fragments stored in SYS_PROC_PARSE_ for the procedure |
| PARSE_LEN        | INTEGER      | The total length of the procedure statement stored in SYS_PROC_PARSE_ |
| CREATED          | DATE         | The date on which the object was created                     |
| LAST_DDL_TIME    | DATE         | The time when DDL was most recently used to make changes to a stored procedure |

#### Column Information

##### USER_ID

This is the identifier of the owner of the stored procedure or stored function, and corresponds to a USER_ID value in the SYS_USERS_ meta table.

##### PROC_OID

This is the identifier of the stored procedure or stored function, and is automatically assigned by the system.

##### PROC_NAME

This is the name of the stored procedure or stored function.

##### OBJECT_TYPE

This value allows stored procedures to be distinguished from stored functions. Stored functions differ from stored procedures in that they return a value.

- 0: Stored procedure
- 1: Stored function
- 3: Type set

##### STATUS

This value indicates whether a stored procedure or function may be executed. A value of 0 (VALID) indicates that it can be executed.

If a DDL statement is executed on an object that is accessed by a stored procedure or stored function, the stored procedure or stored function will become invalid. For example, if a new column is added to a table that is accessed by a stored procedure, the stored procedure will need to be re-compiled before it can be deemed VALID and executed. The status values are as follows:

- 0: VALID
- 1: INVALID

##### AUTHID

This is the value which indicates the authority to execute the procedure or function.

- 0: DEFINER
- 1: CURRENT_USER

##### PARA_NUM

This indicates the number of parameters defined for a stored procedure or stored function.

##### RETURN_DATA_TYPE

This is the data type identifier for the return value of a stored function. Information about data type identifiers can be found in the DATA_TYPE column of the SYS_COLUMNS_ meta table. 

For more information about data types, please refer to Chapter1: Data Types.

##### RETURN_LANG_ID

This column contains information about the language properties of the character data types (CHAR, VARCHAR).

##### RETURN_SIZE

This is the physical size of the return data type.

##### RETURN_PRECISION

This is the precision of the return data type, which is either defined by the user or set based on the system default. For character types, it is the length of the user-defined character type.

##### RETURN_SCALE

This is the scale of the return data type, which is either defined by the user or set as the system default. Depending on the type, this value may not be used. 

For more information about data type precision and scale, please refer to Chapter1: Data Types.

##### PARSE_NO

Stored procedure and stored function statements are divided into multiple records containing text fragments and stored in the SYS_PROC_PARSE_ meta table. This value indicates the number of records used to store a stored procedure or function.

##### PARSE_LEN

Stored procedure and stored function statements are divided into multiple records containing text fragments and stored in the SYS_PROC_PARSE_ meta table. This value indicates the overall length of the statement.

##### LAST_DDL_TIME

This is the most recent time at which a DDL statement was used to make changes to a stored procedure.

#### Reference Table

```
SYS_USERS_
```

### SYS_PROC_PARAS\_

This meta table contains information about the parameters of stored procedures and stored functions.

| Column name | Type          | Description                                                  |
| ----------- | ------------- | ------------------------------------------------------------ |
| USER_ID     | INTEGER       | The identifier of the owner of the stored procedure          |
| PROC_OID    | BIGINT        | The identifier of the stored procedure                       |
| PARA_NAME   | VARCHAR(128)  | The parameter name                                           |
| PARA_ORDER  | INTEGER       | The parameter order. The first parameter is assigned the number 1. |
| INOUT_TYPE  | INTEGER       | Whether the parameter is an Input, Output, or Input/Output parameter |
| DATA_TYPE   | INTEGER       | The data type of the parameter                               |
| LANG_ID     | INTEGER       | The language identifier for the parameter type               |
| SIZE        | INTEGER       | The size of the parameter type                               |
| PRECISION   | INTEGER       | The precision of the parameter type                          |
| SCALE       | INTEGER       | The scale of the parameter type                              |
| DEFAULT_VAL | VARCHAR(4000) | The default value for the parameter                          |

#### Column Information

##### USER_ID

This is the identifier of the user who is the owner of the stored procedure or the stored function, and corresponds to a USER_ID in the SYS_USERS_ meta table.

##### PROC_OID

This is the identifier of the stored procedure or stored function, and corresponds to a PROC_ID in the SYS_PROCEDURES_ meta table

##### PARA_NAME

This is the parameter name.

##### PARA_ORDER

When there are multiple parameters, this value indicates the position of the parameter in the defined parameter order.

##### INOUT_TYPE

This value indicates whether the parameter for the stored procedure or stored function is an input, output, or input/output parameter.

- 0: IN
- 1: OUT
- 2: IN OUT

##### DATA_TYPE

This is the data type identifier for the parameter. The DATA_TYPE column in the SYS_COLUMNS_ meta table contains information about data type identifiers. 

For more information about data types, please refer to Chapter1: Data Types.

##### LANG_ID

This column displays the language properties for character type parameters (CHAR and VARCHAR).

##### SIZE

This is the physical size of the data type.

##### PRECISION

This is the precision of the parameter, which is either determined by the user or set based on the system default. The precision (length) of character data types is defined by the user.

##### SCALE

This is the scale of the parameter, which is either determined by the user or set to the system default. Depending on the data type, this value may not be used. 

For more information about the scale and precision of data types, please refer to Chapter1: Data Types.

##### DEFAULT_VAL

When a parameter is defined, this is the user-defined default parameter value.

#### Reference Tables

```
SYS_USERS_
SYS_PROCEDURES_
```

### SYS_PROC_PARSE\_

This meta table contains the text constituting user-defined stored procedures and stored functions.

| Column name | Type         | Description                                                  |
| ----------- | ------------ | ------------------------------------------------------------ |
| USER_ID     | INTEGER      | The identifier of the owner of the stored procedure or stored function |
| PROC_OID    | BIGINT       | The object identifier of the stored procedure                |
| SEQ_NO      | INTEGER      | The position of the record among multiple records for a statement that was split and then saved |
| PARSE       | VARCHAR(100) | A fragment of the text of the stored procedure or stored function |

#### Column Information

##### USER_ID

This is the identifier of the owner of the stored procedure or stored function, and corresponds to a USER_ID in the SYS_USERS_ meta table.

##### PROC_OID

This is the identifier of the stored procedure or the stored function, and corresponds to a PROC_ID in the SYS_PROCEDURES_ meta table.

##### SEQ_NO

When the information for a statement for one stored procedure is saved across multiple records in SYS_PROC_PARSE_, this is the sequential position of an individual record.

##### PARSE

This is a line of text belonging to the stored procedure or stored function. An entire statement of a stored procedure can be re-created by retrieving all records that correspond to a single PROC_OID value and combining the PARSE values in order according to the SEQ_NO values.

#### Reference Tables

```
SYS_USERS_
SYS_PROCEDURES_
```

### SYS_PROC_RELATED\_

This table contains information about tables, sequences, stored procedures, stored functions, and views accessed by a stored procedure or stored function

| Column name         | Type         | Description                                                  |
| ------------------- | ------------ | ------------------------------------------------------------ |
| USER_ID             | INTEGER      | The identifier of the owner of the stored procedure          |
| PROC_OID            | BIGINT       | The identifier of the stored procedure                       |
| RELATED_USER_ID     | INTEGER      | The identifier of the owner of an object referenced within a stored procedure |
| RELATED_OBJECT_NAME | VARCHAR(128) | The name of an object referenced within a stored procedure   |
| RELATED_OBJECT_TYPE | INTEGER      | The type of an object referenced within a stored procedure   |

In the case where stored procedure PROC1 performs an INSERT on table t1, the identifiers for the owner of the stored procedure PROC1 and for the stored procedure itself would be stored in USER_ID and PROC_OID respectively, the identifiers for the owner of table t1 and for the table itself would be stored in RELATED_USER_ID and RELATED_OBJECT_NAME respectively, and the number 2 (signifying a table) would be stored in RELATED_OBJECT_TYPE.

#### Column Information

##### USER_ID

This is the identifier of the owner of the stored procedure or the stored function, and corresponds to a USER_ID in the SYS_USERS_ meta table.

##### PROC_OID

This is the identifier of the stored procedure or the stored function, and corresponds to a PROC_ID in the SYS_PROCEDURES_ meta table.

##### RELATED_USER_ID

This is the identifier of the owner of the object accessed by the stored procedure, and corresponds to a USER_ID in the SYS_USERS_ meta table.

##### RELATED_OBJECT_NAME

This is the name of the object accessed by the stored procedure.

##### RELATED_OBJECT_TYPE

This is the type of the object accessed by the stored procedure. The possible values are as follows:

- 0: Stored procedure
- 1: Stored function
- 2: Table, Sequence, View
- 3: Type set
- 4: Database link

#### Reference Tables

```
SYS_USERS_
SYS_PROCEDURES_
SYS_TABLES_
```

### SYS_RECYCLEBIN\_

This table contains information about tables in the recycle bin. If the value for the RECYCLEBIN_ENABLE property is set to 1, this table contains information about tables moved to the recycle bin using the DROP statement.

| Column name         | Type         | Description                                                  |
| ------------------- | ------------ | ------------------------------------------------------------ |
| USER_NAME           | VARCHAR(128) | The table owner                                              |
| TABLE_NAME          | VARCHAR(128) | The table name generated by the system so that the table can be managed in the recycle bin when it is dropped. A table with the same name can be dropped multiple times; different names are generated so that tables can be managed in the recycle bin. |
| ORIGINAL_TABLE_NAME | VARCHAR(128) | The table name before it was dropped.                        |
| TBS_NAME            | VARCHAR(128) | The tablespace name in which the table is saved.             |
| MEMORY_SIZE         | BIGINT       | The total memory space occupied by the memory table that was dropped. |
| DISK_SIZE           | BIGINT       | The total disk space occupied by the disk table that was dropped. |
| DROPPED             | DATE         | The date at which the table was dropped.                     |

#### Column Information

##### TABLE_NAME

This is the table name generated by the system when it is moved to the recycle bin. If tables with the same name (ORIGINAL_TABLE_NAME) are dropped multiple times, new names are generated for the tables in the recycle bin.

### SYS_REPLICATIONS\_

This meta table contains information related to replication.

| Column name              | Type        | Description                                                  |
| ------------------------ | ----------- | ------------------------------------------------------------ |
| LAST_USED_HOST_NO        | INTEGER     | The most recently used remote server                         |
| HOST_COUNT               | INTEGER     | The number of remote servers                                 |
| IS_STARTED               | INTEGER     | Whether replication is active                                |
| XSN                      | BIGINT      | The Restart SN (Sequence Number), i.e. the SN from which the Sender will resume transmission of XLogs<sup>13</sup> |
| ITEM_COUNT               | INTEGER     | The number of replication target tables                      |
| CONFLICT_RESOLUTION      | INTEGER     | The replication conflict resolution method                   |
| REPL_MODE                | INTEGER     | The default replication mode                                 |
| ROLE                     | INTEGER     | The role of the sender thread                                |
| OPTIONS                  | INTEGER     | A flag for additional replication features                   |
| INVALID_RECOVERY         | INTEGER     | Whether replication recovery is possible                     |
| REMOTE_FAULT_DETECT_TIME | DATE        | The time at which a fault was detected on a remote server    |
| GIVE_UP_TIME             | DATE        | The time at which replication was most recently abandoned    |
| REPLICATION_NAME         | VARCHAR(40) | The name of the replication object                           |
| GIVE_UP_XSN              | BIGINT      | The XSN at which replication was most recently abandoned     |
| PARALLEL_APPLIER_COUNT   | INTEGER     | The number of appliers                                       |
| REMOTE_XSN               | BIGINT      | The most recently processed SN on the remote server.         |
| APPLIER_INIT_BUFFER_SIZE | BIGINT      | Initial size of applier buffer                               |

[<sup>13</sup>] SN: The identification number of the log record

#### Column Information

##### REPLICATION_NAME

This is the name of the replication object, and is set by the user when the replication object is created.

##### LAST_USED_HOST_NO

This is the number of the most recently used remote server, and corresponds to a HOST_NO in the SYS_REPL_HOSTS_ meta table.

##### HOST_COUNT

This is the number of remote servers involved in replication, and is equal to the number of IP addresses stored in SYS_REPL_HOSTS_.

##### IS_STARTED

Indicates whether replication is active.

- 0: suspended
- 1: replication active

##### XSN

This indicates the SN from which the Sender thread must begin sending logs when replication is started.

##### ITEM_COUNT

This is the number of replication target tables. This number corresponds to the number of records in the SYS_REPL_ITEMS_ meta table for this replication object, with one record corresponding to each of these tables.

##### CONFLICT_RESOLUTION

This describes the replication conflict resolution method.

- 0: Default
- 1: Act as the Master server
- 2: Act as the Slave server

Please refer to the *Replication Manual* for more detailed information about replication conflict resolution methods.

##### REPL_MODE

This is the default replication mode, which is set when the replication object is created.

- 0: LAZY MODE (Default)
- 2: EAGER MODE

The default replication mode is used if the ALTER SESSION SET REPLICATION statement is not used to set the replication mode for a session.

For more detailed information about the default replication mode, please refer to the *Replication Manual*, and for detailed information about the ALTER SESSION SET REPLICATION statement, please refer to the Reference.

##### ROLE

This indicates the role of the Sender thread.

- 0: Replication
- 1: Log Analyzer
- 2: Propagable Logging (Replication propagable logs)
- 3: Propagation (Send propagable logs)

For more detailed information, please refer to the *Log Analyzer User's Manual*.

##### OPTIONS

This flag indicates whether to use the recovery and offline options, which are extra replication features. The replication option types are as in the following. Each option is controlled by binary number and expressed as a decimal number. If more than two options are used, the sum of the binary numbers of each option is returned as decimal numbers.

- 0(00000): Do not use the recovery or offline option
- 1(00001): Use the recovery option 
- 2(00010): Use the offline option 
- 4(00100): Use the gapless option 
- 8(01000): Use the parallel applier option 
- 16(10000): Use the replication transaction grouping option

##### INVALID_RECOVERY

This value indicates whether recovery using replication is possible.

- 0: replication-based recovery is possible. 
- 1: replication-based recovery is not possible.

##### REMOTE_FAULT_DETECT_TIME

This is the time at which a fault was detected on a remote server while replication was running.

##### GIVE_UP_TIME

This is the time at which replication was most recently abandoned, i.e. the time at which the replication Sender most recently gave up on replication.

##### GIVE_UP_XSN

This is the XSN at which replication was most recently abandoned.

##### PARALLEL_APPLIER_COUNT

This is the number of parallel applier.

##### REMOTE_XSN

This is the most recently processed SN on the remote server. When the Sender is restarted, the log with the SN smaller than the corresponding REMOTE_XSN is not sent but skipped.

##### APPLIER_INIT_BUFFER_SIZE

This property specifies the initial buffer size of the parallel applier when replication is performed with the receiver applier option enabled. The number of queues in the parallel applier is set to the value divided by XLog Size.

```
( applier queue size = applier_init_buffer_size / xlog size )
```

If the number of parallel applier queues is less than the value of the property REPLICATION_RECEIVER_APPLIER_QUEUE_SIZE, then the number of parallel applier queues is set to the value specified in the property REPLICATION_RECEIVER_APPLIER_QUEUE_SIZE.

#### Example

\<Example\> The following is an example of returning values when using the replication gapless option and parallel applier option together on a created replication rep1.

```
iSQL> alter replication rep1 set gapless enable;
Alter success.
iSQL> alter replication rep1 set parallel 4;
Alter success.
iSQL> select options from system_.sys_replications_;
OPTIONS     
--------------
12           
1 row selected.
```

### SYS_REPL_HOSTS\_ 

This meta table contains information related to remote servers defined in replication objects.

| Column name      | Type        | Description                                      |
| ---------------- | ----------- | ------------------------------------------------ |
| HOST_NO          | INTEGER     | The host identifier                              |
| REPLICATION_NAME | VARCHAR(40) | The replication name                             |
| HOST_IP          | VARCHAR(64) | The IP address of the remote server              |
| PORT_NO          | INTEGER     | The replication port number on the remote server |
| CONN_TYPE        | VARCHAR(20) | The remote server connection method              |
| IB_LATENCY       | VARCHAR(10) | The RDMA_LATENCY option value for rsocket.       |

#### Column Information

##### HOST_NO

This is the serial number of the remote server, which is automatically assigned by the system sequence.

##### REPLICATION_NAME

This is the name of the replication object set by the user, and corresponds to a REPLICATION_NAME in the SYS_REPLICATIONS_ meta table.

##### HOST_IP

This is the IP address of the remote server.

##### PORT_NO

This is the replication port number on the remote server.

##### CONN_TYPE

This shows the remote server connection method.

- TCP
- Unix Domain
- InfiniBand(IB)

##### IB_LATENCY

This is the value of the RDMA_LATENCY option of rsocket when using InfiniBand, This value is N/A when CONN_TYPE is not IB.

#### Reference Table

```
SYS_REPLICATIONS_
```

### SYS_REPL_ITEMS\_

This meta table contains information about replication target tables.

| Column name           | Type          | Description                                                  |
| --------------------- | ------------- | ------------------------------------------------------------ |
| REPLICATION_NAME      | VARCHAR(40)   | The replication name                                         |
| TABLE_OID             | BIGINT        | The table object identifier                                  |
| LOCAL_USER_NAME       | VARCHAR(128)  | The name of a user owning a target table on the local server |
| LOCAL_TABLE_NAME      | VARCHAR(128)  | The name of a target table on the local server               |
| LOCAL_PARTITION_NAME  | VARCHAR(128)  | The name of a partition on the local server                  |
| REMOTE_USER_NAME      | VARCHAR(128)  | The name of a user owning a target table on the remote server |
| REMOTE_TABLE_NAME     | VARCHAR(128)  | The name of a target table on the remote server              |
| REMOTE_PARTITION_NAME | VARCHAR(128)  | The name of a partition on the remote server                 |
| IS_PARTITION          | CHAR(1)       | Whether or not a table is partitioned                        |
| INVALID_MAX_SN        | BIGINT        | The highest log SN to skip                                   |
| CONDITION             | VARCHAR(1000) | Deprecated                                                   |
| REPLICATION_UNIT      | CHAR(1)       | The replication unit                                         |
| IS_CONDITION_SYNCED   | INTEGER       | Whether or not a replication is conditional synced           |

One replication object can pertain to more than one table, and SYS_REPL_ITEMS_ has a record for each of these tables. For example, if a replication pertains to 10 tables, this meta table will contain 10 records pertaining to this replication.

#### Column Information

##### REPLICATION_NAME

This is the name of the replication object, which is defined by the user, and corresponds to a REPLICATION_NAME in the SYS_REPLICATIONS_ meta table

##### TABLE_OID

This is the identifier of the replication target table or partition, and corresponds to a TABLE_OID value in the SYS_TABLES_ meta table or a PARTITION_OID value in the SYS_TABLES_PARTITIONS meta table.

##### LOCAL_USER_NAME

This is the user name of the owner of the replication target table in the local system, and corresponds to a USER_NAME in the SYS_USERS_ meta table.

##### LOCAL_TABLE_NAME

This is the name of the replication target table in the local system, and corresponds to a TABLE_NAME in the SYS_TABLES_ meta table.

##### LOCAL_PARTITION_NAME

This is the name of the replication target partition on the local server.

##### REMOTE_USER_NAME

This is the user name of the owner of the replication target table in the remote system, and corresponds to a USER_NAME in the SYS_USERS_ meta table.

##### REMOTE_TABLE_NAME

This is the name of the replication target table in the remote system, and corresponds to a TABLE_NAME in the SYS_TABLES_ meta table.

##### REMOTE_PARTITION_NAME

This is the name of the replication target partition on the remote server.

##### IS_PARTITION

This is an identifier indicating whether a table is partitioned. If it is ‘Y’, the table is partitioned. If it is ‘N’, the table is not partitioned. 

##### INVALID_MAX_SN

If DDL statements or Sync operations are executed on replication target tables, the most recently recorded SN is saved here. Table logs up to this SN are skipped when the table is replicated. 

##### REPLICATION_UNIT

This is the unit of the replication target item. One of the following two values is indicated in this column.

- T: The replication target item is a table.
- P: The replication target item is a partition.

##### IS_CONDITION_SYNCED
Whether or not a replication is conditional synced           |


#### Reference Tables

```
SYS_REPLICATIONS_
SYS_USERS_
SYS_TABLES_
```

### SYS_REPL_OFFLINE_DIR\_

This meta table stores log directory information related to the offline replication option. 

| Column name      | Type         | Description                          |
| ---------------- | ------------ | ------------------------------------ |
| REPLICATION_NAME | VARCHAR(40)  | The replication name                 |
| LFG_ID           | INTEGER      | The identifier of the log file group |
| PATH             | VARCHAR(512) | The offline log path                 |

#### Column Information

##### REPLICATION_NAME

This is the user-defined replication name. It corresponds to a REPLICATION_NAME in the SYS_REPLICATIONS_ meta table.

##### LFG_ID

This is the identifier for the LFG which defalut value is ‘0’.

##### PATH

This is the absolute path in the system where the log file is saved. 

### SYS_REPL_OLD_COLUMNS\_

This meta table is for storing information about columns that are currently replicated by the replication Sender thread.

| Column name          | Type          | Description                                                  |
| -------------------- | ------------- | ------------------------------------------------------------ |
| REPLICATION_NAME     | VARCHAR(40)   | The name of the replication object                           |
| TABLE_OID            | BIGINT        | The object identifier of the table                           |
| COLUMN_NAME          | VARCHAR(128)  | The column name                                              |
| MT_DATATYPE_ID       | INTEGER       | The data type identifier                                     |
| MT_LANGUAGE_ID       | INTEGER       | The language identifier                                      |
| MT_FLAG              | INTEGER       | An internal flag                                             |
| MT_PRECISION         | INTEGER       | The number of digits                                         |
| MT_SCALE             | INTEGER       | The number of digits to the right of the decimal point       |
| MT_ENCRYPT_PRECISION | INTEGER       | The number of digits in an encrypted column                  |
| MT_POLICY_NAME       | VARCHAR(16)   | The name of the policy used for an encrypted column          |
| SM_ID                | INTEGER       | The column identifier                                        |
| SM_FLAG              | INTEGER       | An internal flag                                             |
| SM_OFFSET            | INTEGER       | The internal offset                                          |
| SM_VARORDER          | INTEGER       | Indicates the order of stored columns by variables method in a table. Exceptionally, VARORDER is not given to the geometry data type. (Default : 0) |
| SM_SIZE              | INTEGER       | The internal size                                            |
| SM_DIC_TABLE_OID     | BIGINT        | For a compressed column, the OID of the dictionary table     |
| SM_COL_SPACE         | INTEGER       | The tablespace identifier                                    |
| QP_FLAG              | INTEGER       | The internal flag                                            |
| DEFAULT_VAL          | VARCHAR(4000) | The default value of the column                              |

#### Column Information

##### REPLICATION_NAME

This is the replication name, which is specified by the user. It corresponds to a REPLICATION_NAME in the SYS_REPLICATIONS_ meta table.

##### TABLE_OID

This is the identifier for a replication target table currently being used by the replication Sender thread. Its value may not correspond to any TABLE_OID value in SYS_TABLES_.

##### COLUMN_NAME

This is the name of a column currently being replicated by the replication Sender thread. 

##### MT_DATATYPE_ID

This is the data type identifier, and is an internal value. 

##### MT_LANGUAGE_ID

This is the language identifier, and is an internal value.

##### MT_FLAG

This is an internal flag used by Altibase server.

##### MT_PRECISION

For a numeric type column, this is the number of digits in the column.

##### MT_SCALE

For a numeric type column, this is the number of digits to the right of the decimal point in the column.

##### MT_ENCRYPT_PRECISION

For an encrypted numeric type column, this is the number of digits in the column. 

##### MT_POLICY_NAME

For an encrypted column, this is the name of the policy used for the column. 

##### SM_ID

This is the column identifier. Column identifiers start with 0.

##### SM_FLAG

This is a flag internally used by Altibase.

##### SM_OFFSET

This is an offset value internally used by Altibase.

##### SM_VARORDER

This indicates the order of a column among the columns stored with the variable method within a table. Exceptionally, VARORDER is not given to the geometry data type (Default value:0).

##### SM_SIZE

This is a size value internally used by Altibase server. 

##### SM_DIC_TABLE_OID

For a compressed column, this is the OID of the dictionary table in which data of the compressed column is actually saved.

##### SM_COL_SPACE

This is the identifier of the tablespace in which the column data is saved.

##### QP_FLAG

This is the flag used internally by the Altibase server.

##### DEFAULT_VAL

The default value of the column is saved as a string and is used internally by the Altibase server.

#### Reference Tables

```
SYS_REPL_OLD_ITEMS_
SYS_REPL_OLD_INDICES_
SYS_REPL_OLD_INDEX_COLUMNS_
```

### SYS_REPL_OLD_INDEX_COLUMNS\_

This meta table is for storing information about columns currently being replicated by the replication Sender thread.

| Column name      | Type        | Description                                            |
| ---------------- | ----------- | ------------------------------------------------------ |
| REPLICATION_NAME | VARCHAR(40) | The replication name                                   |
| TABLE_OID        | BIGINT      | The table object identifier                            |
| INDEX_ID         | INTEGER     | The index identifier                                   |
| KEY_COLUMN_ID    | INTEGER     | The column identifier                                  |
| KEY_COLUMN_FLAG  | INTEGER     | An internal flag                                       |
| COMPOSITE_ORDER  | INTEGER     | The position of the column on which the index is based |

#### Column Information

##### REPLICATION_NAME

This value corresponds to a REPLICATION_NAME in the SYS_REPLICATIONS_ meta table, and is the user-defined replication name. 

##### TABLE_OID

This is the identifier of a table currently being replicated by the replication Sender thread. Its value may not correspond to any TABLE_OID value in SYS_TABLES_.

##### INDEX_ID

This is the identifier of an index currently being replicated by the replication Sender thread. 

##### KEY_COLUMN_ID

This is the identifier of the column on which the index is based. 

##### KEY_COLUMN_FLAG

This is an internal flag for the column on which the index is based. 

##### COMPOSITE_ORDER

This is the position of the column on which the index is based. 

#### Reference Tables

```
SYS_REPL_OLD_ITEMS_
SYS_REPL_OLD_COLUMNS_
SYS_REPL_OLD_INDICES_
```

### SYS_REPL_OLD_INDICES\_

This meta table contains information about indexes currently being replicated by the replication Sender thread. 

| Column name      | Type         | Description                                                  |
| ---------------- | ------------ | ------------------------------------------------------------ |
| REPLICATION_NAME | VARCHAR(40)  | The replication name                                         |
| TABLE_OID        | BIGINT       | The object identifier of the table                           |
| INDEX_ID         | INTEGER      | The index identifier                                         |
| INDEX_NAME       | VARCHAR(128) | The index name                                               |
| TYPE_ID          | INTEGER      | The index type identifier                                    |
| IS_UNIQUE        | CHAR(1)      | Indicates whether or not the index is globally unique        |
| IS_LOCAL_UNIQUE  | CHAR(1)      | Indicates whether or not the index is locally unique         |
| IS_RANGE         | CHAR(1)      | Indicates whether or not range scanning is possible using the index |

#### Column Information

##### REPLICATION_NAME

This is the user-defined replication name. Its value corresponds to a REPLICATION_NAME value in the SYS_REPLICATIONS_ meta table.

##### TABLE_OID

This is the identifier of a table currently being replicated by the replication Sender thread. Its value may be different from that of TABLE_OID in the SYS_TABLES_ meta table.

##### INDEX_ID

This is the identifier of an index currently being replicated by the replication Sender thread. 

##### INDEX_NAME

This is the name of an index currently being replicated by the replication Sender thread. 

##### TYPE_ID

This is an index type identifier, and is an internal value.

##### IS_UNIQUE

This indicates whether or not the index is globally unique. 'Y' signifies that the index is globally unique, and 'N' signifies that it is not globally unique. 

##### IS_LOCAL_UNIQUE

This indicates whether or not the index is locally unique. 'Y' signifies that it is locally unique, and 'N' means that it is not locally unique.

##### IS_RANGE

This indicates whether or not the index is locally unique. 'Y' signifies that it is locally unique, and 'N' means that it is not locally unique.

#### Reference Tables

```
SYS_REPL_OLD_ITEMS_
SYS_REPL_OLD_COLUMNS_
SYS_REPL_OLD_INDEX_COLUMNS_
```

### SYS_REPL_OLD_ITEMS\_

This meta table contains information about tables currently being replicated by the replication Sender thread. 

| Column name          | Type         | Description                             |
| -------------------- | ------------ | --------------------------------------- |
| REPLICATION_NAME     | VARCHAR(40)  | The partition name                      |
| TABLE_OID            | BIGINT       | The table object identifier             |
| USER_NAME            | VARCHAR(128) | The user name                           |
| TABLE_NAME           | VARCHAR(128) | The table name                          |
| PARTITION_NAME       | VARCHAR(128) | The name of the replication             |
| PRIMARY_KEY_INDEX_ID | INTEGER      | The index identifier of the primary key |

#### Column Information

##### REPLICATION_NAME

This value corresponds to a REPLICATION_NAME in the SYS_REPLICATIONS_ meta table, and is the user-defined replication name.

##### TABLE_OID

This is the identifier of a table currently being replicated by the replication Sender thread. Its value may be different from the value of TABLE_OID in the SYS_TABLES_ meta table.

##### USER_NAME

This is the user name of the owner of the table being replicated on the local server. Its value corresponds to a USER_NAME in the SYS_USERS_ meta table.

##### TABLE_NAME

This is the name of the table being replicated on the local server. Its value corresponds to a TABLE_NAME value in the SYS_TABLES_ meta table.

##### PARTITION_NAME

This is the name of the partition containing the table being replicated on the local server.

##### PRIMARY_KEY_INDEX_ID

This is the identifier of a primary key index. 

#### Reference Tables

```
SYS_REPL_OLD_COLUMNS_
SYS_REPL_OLD_INDICES_
SYS_REPL_OLD_INDEX_COLUMNS_
```

### SYS_REPL_RECOVERY_INFOS\_

This is the meta table in which log information is written for use in recovery of the remote server.

| Column name          | Type        | Description                                          |
| -------------------- | ----------- | ---------------------------------------------------- |
| REPLICATION_NAME     | VARCHAR(40) | The name of the replication                          |
| MASTER_BEGIN_SN      | BIGINT      | The starting log number of a master transaction      |
| MASTER_COMMIT_SN     | BIGINT      | The final log number of the master transaction       |
| REPLICATED_BEGIN_SN  | BIGINT      | The starting log number of a replication transaction |
| REPLICATED_COMMIT_SN | BIGINT      | The final log number of the replication transaction  |

#### Column Information

##### REPLICATION_NAME

This is the replication object name defined by the user, and corresponds to a REPLICATION_NAME in the SYS_REPLICATIONS_ meta table.

##### MASTER_BEGIN_SN

The starting log number of a master transaction occurring on a remote server.

##### MASTER_COMMIT_SN

The final log number of a master transaction occurring on a remote server.

##### REPLICATED_BEGIN_SN

The starting log number of a replication transaction occurring on the local server.

##### REPLICATED_COMMIT_SN

The final log number of a replication transaction occurring on the local server.

#### Reference Table

```
SYS_REPLICATIONS_
```

### SYS_SECURITY\_

This table contains information about the state of the security module.

| Column name     | Type        | Description                             |
| --------------- | ----------- | --------------------------------------- |
| MODULE_NAME     | VARCHAR(24) | The name of the security module         |
| MODULE_VERSION  | VARCHAR(40) | The version of the security module      |
| ECC_POLICY_NAME | VARCHAR(16) | The name of the ECC policy              |
| ECC_POLICY_CODE | VARCHAR(64) | The verification code of the ECC policy |

This table shows whether a security module authored by a third party is being used.

In the case where a security module authored by a third party is in use, the SYS_SECURITY_ meta table contains information about the properties of the security module, whereas if no such security module is in use, the SYS_SECURITY_ meta table will contain no records.

### SYS_SYNONYMS\_

This is the table for storing information about synonyms, which provide alias functions for database objects.

| Column name       | Type         | Description                                                  |
| ----------------- | ------------ | ------------------------------------------------------------ |
| SYNONYM_OWNER_ID  | INTEGER      | The user identifier                                          |
| SYNONYM_NAME      | VARCHAR(128) | The synonym name                                             |
| OBJECT_OWNER_NAME | VARCHAR(128) | The name of the object owner                                 |
| OBJECT_NAME       | VARCHAR(128) | The name of the synonym target object                        |
| CREATED           | DATE         | The time at which the synonym was created                    |
| LAST_DDL_TIME     | DATE         | The most recent time at which a DDL statement was used to make changes to a synonym |

#### Column Information

##### SYNONYM_OWNER_ID

This is the identifier of the owner of the synonym, and corresponds to a USER_ID in the SYS_USERS_ meta table.

##### SYNONYM_NAME

This is the synonym name, which is defined by the user.

##### OBJECT_OWNER_NAME

This is the name of the owner of the schema containing the object that is the target of the user-defined synonym.

##### OBJECT_NAME

This is the name of the object targeted by the user-defined synonym.

##### CREATED

This is the time at which the synonym was created.

##### LAST_DDL_TIME

This is the most recent time at which a DDL statement was used to create or make changes to the synonym.

#### Reference Table

```
SYS_USERS_
```

### SYS_TABLES\_

This table contains information about meta tables, user-defined tables, sequences and views.

| Column name                | Type         | Description                                                  |
| -------------------------- | ------------ | ------------------------------------------------------------ |
| USER_ID                    | INTEGER      | The user identifier                                          |
| TABLE_ID                   | INTEGER      | The table identifier                                         |
| TABLE_OID                  | BIGINT       | The table object identifier                                  |
| COLUMN_COUNT               | INTEGER      | The number of columns in the table                           |
| TABLE_NAME                 | VARCHAR(128) | The name of the table                                        |
| TABLE_TYPE                 | CHAR(1)      | The object type                                              |
| REPLICATION_COUNT          | INTEGER      | The number of replications related to the table              |
| REPLICATION_RECOVERY_COUNT | INTEGER      | The number of replications that use the recovery option and are related to the table |
| MAXROW                     | BIGINT       | The maximum number of records that can be entered (0: no limit) |
| TBS_ID                     | INTEGER      | The tablespace identifier                                    |
| TBS_NAME                   | VARCHAR(128) | The name of the tablespace in which the table is stored      |
| PCTFREE                    | INTEGER      | See below                                                    |
| PCTUSED                    | INTEGER      | See below                                                    |
| INIT_TRANS                 | INTEGER      | The initial number of transactions that can be simultaneously used for update in a page |
| MAX_TRANS                  | INTEGER      | The maximum number of transactions that can be simultaneously used for update in a page |
| INITEXTENTS                | BIGINT       | The initial number of extents when a table is created        |
| NEXTEXTENTS                | BIGINT       | The number of extents that are added when a table is expanded |
| MINEXTENTS                 | BIGINT       | The minimum number of extents in a table                     |
| MAXEXTENTS                 | BIGINT       | The maximum number of extents in a table                     |
| IS_PARTITIONED             | CHAR(1)      | Indicates whether a table is partitioned                     |
| TEMPORARY                  | CHAR(1)      | Whether or not the table is a temporary table D: Is a transaction-specific temporary table P: Is a session-specific temporary table N: Is not a temporary table |
| HIDDEN                     | CHAR(1)      | Indicates whether the table has hidden properties            |
| ACCESS                     | CHAR(1)      | The data access mode for the table                           |
| PARALLEL_DEGREE            | INTEGER      | The number of threads which execute parallel queries         |
| CREATED                    | DATE         | The time at which the table was created                      |
| LAST_DDL_TIME              | DATE         | The time at which the table was most recently changed using a DDL statement |

#### Column Information

##### USER_ID

This is the identifier of the owner of the table, and corresponds to a USER_ID in the SYS_USERS_ meta table

##### TABLE_ID

This is the table identifier, which is automatically assigned by the system sequence.

##### TABLE_OID

This is the table object identifier, which is automatically and internally assigned by the system. Unlike TABLE_ID, which is used when the user reads meta tables, this value is used only for internal operations.

##### COLUMN_COUNT

This is the number of columns defined in the table.

##### TABLE_NAME

This is the table name, which is defined by the user.

##### TABLE_TYPE

Information not only about tables, but also about sequences, views, etc. is saved in the SYS_TABLES_ meta table. This type identifier is used to distinguish them, and consists of the following types:

- T: A table
- S: A sequence
- V: A view
- W: A sequence for queue use only
- Q: A queue
- M: A table automatically created for the maintenance of the data of the materialized view
- A: A view automatically created for the maintenance of the data of the materialized view
- G: An internal table for global index of
- D: A dictionary table internally used for actually storing compressed column data

##### REPLICATION_COUNT

This is the number of replication objects associated with the table.

##### REPLICATION_RECOVERY_COUNT

This is the number of replication objects that use the recovery option and are associated with the table.

##### MAXROW

This is the maximum number of records that can be inserted into the table.

##### TBS_ID

This is the identifier of the tablespace in which the table is saved.

##### PCTFREE

This is the minimum percentage of free space that must exist in order for it to be possible to update a page. Usually, an amount of space equal to the percentage specified in PCTFREE is kept free so that existing rows saved in a page can be updated. For example, if PCTFREE is set to 20, 20% of the space in the page is set aside for update operations, so data can be inserted only into 80% of the space in the page.

The user can set PCTFREE between 0 and 99 when executing the CREATE TABLE statement. 

##### PCTUSED

This is a threshold below which the amount of used space in a page must decrease in order for the page to return to the state in which records can be inserted from the state in which only update operations are possible. If the amount of free space falls below the percentage specified in PCTFREE, it will become impossible to insert new records into the page, and it will only be possible to update and delete rows. If subsequent update or delete operations reduce the percentage of used space below the threshold specified by PCTUSED, it will become possible to insert new rows into the page again.

The user can set PCTUSED between 0 and 99 when the CREATE TABLE statement is executed.

> \* For more detailed explanations of PCTFREE and PCTUSED, please refer to the description of the CREATE TABLE statement in the *SQL Reference*.

##### INIT_TRANS

This is the initial number of update transactions that can be simultaneously executed, and is set when a page is created. The actual number of transactions can increase to the number specified in MAX_TRANS, as long as sufficient page space is available.

##### MAX_TRANS

This is the maximum number of update transactions that can be simultaneously executed for a single page.

##### INITEXTENTS

This denotes the number of extents that are available to be allocated when a table is created.

##### NEXTEXTENTS

This denotes the number of additional extents that are available to be allocated when the size of a table is increased.

##### MINEXTENTS

This denotes the minimum number of available extents for a table.

##### MAXEXTENTS

This denotes the maximum number of available extents for a table. 

##### IS_PARTITIONED

This is an identifier that indicates whether a table is partitioned. If it is ‘Y’, the table is partitioned. If it is ‘F’, the table is not partitioned. 

##### TEMPORARY

This indicates whether or not the table is a temporary table. 

- D: A transaction-specific temporary table
- P: A session-specific temporary table
- N: Not a temporary table

##### HIDDEN

This indicates whether the table is hidden or not.

- Y: The table is hidden from the user
- N: the table is open to the user (normal table)

##### PARALLEL_DEGREE

This indicates the number of threads which execute parallel queries when scanning the partitioned table. 

##### ACCESS

This is the data access mode for the table. The default mode is W which allows Read/Write.

- R: Read-Only mode
- W: Read/Write mode (default mode)
- A: Read/Add mode. This mode disallows the alteration/deletion of data.

#### Reference Table

```
SYS_USERS_
```

### SYS_TABLE_PARTITIONS\_ 

This is a meta table for the management of table partitions. 

| Column name                | Type          | Description                                                  |
| -------------------------- | ------------- | ------------------------------------------------------------ |
| USER_ID                    | INTEGER       | The user identifier                                          |
| TABLE_ID                   | INTEGER       | The table identifier                                         |
| PARTITION_OID              | BIGINT        | The partition object identifier                              |
| PARTITION_ID               | INTEGER       | The partition identifier                                     |
| PARTITION_NAME             | VARCHAR(128)  | The partition name                                           |
| PARTITION_MIN_VALUE        | VARCHAR(4000) | The minimum reference value for a partition (NULL in the case of a hash partition) |
| PARTITION_MAX_VALUE        | VARCHAR(4000) | The maximum reference value for a partition (NULL in the case of a hash partition) |
| PARTITION_ORDER            | INTEGER       | The position of the partition (required for hash partitions) |
| TBS_ID                     | INTEGER       | The identifier of a tablespace                               |
| PARTITION_ACCESS           | CHAR(1)       | The data access mode for the partition                       |
| REPLICATION_COUNT          | INTEGER       | The number of replication objects related to this partition  |
| REPLICATION_RECOVERY_COUNT | INTEGER       | The number of replication objects which have enabled the recovery option for this partition |
| CREATED                    | DATE          | The date and time at which the parition is created           |
| LAST_DDL_TIME              | DATE          | The time at which the partition was most recently changed using a DDL statement |

#### Column Information

##### USER_ID

This is the identifier of the table owner, and corresponds to a USER_ID in the SYS_USERS_ meta table.

##### TABLE_ID

This is the table identifier. It is assigned automatically by the system sequence.

##### PARTITION_OID

This is the partition object identifier. It is assigned automatically by the system. Unlike PARTITION_ID, which is used when viewing meta tables, it is used only internally by the system.

##### PARTITION_ID

This is the partition identifier. 

##### PARTITION_NAME

This is the user-defined partition name.

##### PARTITION_MIN_VALUE

This is a string that gives the minimum reference value for a partition. It is NULL for hash partitions. 

##### PARTITION_MAX_VALUE

This is a string that gives the maximum reference value for a partition. It is NULL for hash partitions.

##### PARTITION_ORDER

This is the position of the partition among the partitions. It is required for hash partitions.

##### TBS_ID

This is the identifier of the tablespace in which the table is stored.

##### PARTITION_ACCESS

This is the data access mode for the partition. The default mode is W which allows Read/Write.

- R: Read-Only mode
- W: Read/Write mode (default mode)
- A: Read/Append mode. This mode disallows the alteration/deletion of data.

##### REPLICATION_COUNT

This is the number of replication objects related to this partition.

##### REPLICATION_RECOVERY_COUNT

This is the number of replication objects which have enabled the recovery option for this partition.

#### Reference Tables

```
SYS_USERS_
SYS_TABLES_
SYS_PART_TABLES_
```

### SYS_TABLE_SIZE\_

This table stores information about the actual size of disk and memory tables in the system.

| Column name | Type         | Description                                            |
| ----------- | ------------ | ------------------------------------------------------ |
| USER_NAME   | VARCHAR(128) | The table owner                                        |
| TABLE_NAME  | VARCHAR(128) | The table name                                         |
| TBS_NAME    | VARCHAR(128) | The name of the tablespace in which the table is saved |
| MEMORY_SIZE | BIGINT       | The memory table size                                  |
| DISK_SIZE   | BIGINT       | The disk table size                                    |

### SYS_TBS_USERS\_

This meta table contains information about the relationship between users and user-defined tablespaces.

| Column name | Type    | Description                                          |
| ----------- | ------- | ---------------------------------------------------- |
| TBS_ID      | INTEGER | The tablespace identifier                            |
| USER_ID     | INTEGER | The user identifier                                  |
| IS_ACCESS   | INTEGER | Whether the user is allowed to access the tablespace |

#### Column Information

##### TBS_ID

This is the tablespace identifier.

##### USER_ID

This is the identifier of a particular user. It corresponds to a USER_ID in the SYS_USERS_ meta table.

##### IS_ACCESS

This indicates whether the user is permitted to access the tablespace.

- 0: access not permitted
- 1: access permitted.

#### Reference Table

```
SYS_USERS_
```

### SYS_TRIGGERS\_ 

This meta table contains default information about triggers.

| Column name       | Type         | Description                                                  |
| ----------------- | ------------ | ------------------------------------------------------------ |
| USER_ID           | INTEGER      | The user identifier                                          |
| USER_NAME         | VARCHAR(128) | The user name                                                |
| TRIGGER_OID       | BIGINT       | The trigger identifier                                       |
| TRIGGER_NAME      | VARCHAR(128) | The trigger name                                             |
| TABLE_ID          | INTEGER      | The table identifier                                         |
| IS_ENABLE         | INTEGER      | Indicates whether the trigger is enabled                     |
| EVENT_TIME        | INTEGER      | Indicates when the trigger fires                             |
| EVENT_TYPE        | INTEGER      | The trigger event type                                       |
| UPDATE_COLUMN_CNT | INTEGER      | The number of columns that can cause a trigger to fire if updated |
| GRANULARITY       | INTEGER      | The units in which the trigger is executed                   |
| REF_ROW_CNT       | INTEGER      | The number of ALIASes for a REFERENCING statement            |
| SUBSTRING_CNT     | INTEGER      | The number of records in which the trigger statement is saved |
| STRING_LENGTH     | INTEGER      | The total length of the trigger statement character string   |
| CREATED           | DATE         | The time at which the trigger was created                    |
| LAST_DDL_TIME     | DATE         | The most recent time at which a DDL statement was used to make changes to the trigger |

#### Column Information

##### USER_ID

This is the identifier of the user who owns the trigger, and corresponds to a USER_ID in the SYS_USERS_ meta table.

##### USER_NAME

This is the user name, and corresponds to a USER_NAME in the SYS_USERS_ meta table.

##### TRIGGER_OID

This is the trigger identifier. It is automatically assigned by the system.

##### TRIGGER_NAME

This is the user-defined trigger name.

##### TABLE_ID

This is the identifier of the table on which the trigger is defined, and corresponds to a TABLE_ID in the SYS_TABLES_ meta table.

##### IS_ENABLE

This value indicates whether or not the trigger is enabled. It can be modified using the ALTER TRIGGER statement.

- 0: DISABLED
- 1: ENABLED

##### EVENT_TIME

This displays the time point that the trigger fires.

- 1: BEFORE
- 2: AFTER
- 3: INSTEAD OF

##### EVENT_TYPE

This is the type of the event that causes the trigger to fire.

- 1: INSERT
- 2: DELETE
- 4: UPDATE

##### UPDATE_COLUMN_CNT

This is the number of columns that cause a trigger to fire when updated. This value is equal to the number of records related to the trigger in the SYS_TRIGGER_UPDATE_COLUMNS_ meta table.

##### GRANULARITY

This value indicates how often the trigger fires:

- 1: FOR EACH ROW
- 2: FOR EACH STATEMENT

##### REF_ROW_CNT

This is the number of ALIASes defined in a REFERENCING statement.

##### SUBSTRING_CNT

One trigger statement is divided into several records and stored in the SYS_TRIGGER_STRINGS_ meta table. This value indicates the number of records used to store the statement.

##### STRING_LENGTH

This is the total length of the trigger statement character string.

#### Reference Tables

```
SYS_USERS_
SYS_TABLES_
```

### SYS_TRIGGER_DML_TABLES\_

This meta table contains information about tables referenced by triggers.

| Column name  | Type    | Description                             |
| ------------ | ------- | --------------------------------------- |
| TABLE_ID     | INTEGER | The table identifier                    |
| TRIGGER_OID  | BIGINT  | The trigger identifier                  |
| DML_TABLE_ID | INTEGER | The table identifier within the trigger |
| STMT_TYPE    | INTEGER | The type of executable statement        |

#### Column Information

##### TABLE_ID

This is the identifier of the table on which the trigger is defined, and corresponds to a TABLE_ID in the SYS_TABLES_ meta table.

##### TRIGGER_OID

This is the trigger identifier, and corresponds to a TRIGGER_OID in the SYS_TRIGGERS_ meta table.

##### DML_TABLE_ID

This is the identifier of the table that is accessed using the DML statements within the trigger, and corresponds to a TABLE_ID in the SYS_TABLES_ meta table

##### STMT_TYPE

This is the type of statement executed on a table.

- 8: DELETE
- 19: INSERT
- 33: UPDATE

#### Reference Tables

```
SYS_TABLES_
SYS_TRIGGERS_
```

### SYS_TRIGGER_STRINGS\_

This is the meta table in which the trigger statements are saved.

| Column name | Type         | Description                                                 |
| ----------- | ------------ | ----------------------------------------------------------- |
| TABLE_ID    | INTEGER      | The table identifier                                        |
| TRIGGER_OID | BIGINT       | The trigger identifier                                      |
| SEQNO       | INTEGER      | The position of this text fragment in the trigger statement |
| SUBSTRING   | VARCHAR(100) | A fragment of trigger statement text                        |

#### Column Information

##### TABLE_ID

This is the table identifier, and corresponds to a TABLE_ID in the SYS_TABLES_ meta table.

##### TRIGGER_OID

This is the trigger identifier, and corresponds to a TRIGGER_OID in the SYS_TRIGGERS_ meta table.

##### SEQNO

When information about a single trigger statement is saved as several records in SYS_TRIGGER_STRINGS, this is the position of this record among the records.

##### SUBSTRING

This is a fragment of the trigger statement text. When records are searched for using a single TRIGGER_OID and their SUBSTRING values are concatenated in the order described in SEQNO, the complete trigger command can be reconstructed.

#### Reference Tables

```
SYS_TABLES_
SYS_TRIGGERS_
```

### SYS_TRIGGER_UPDATE_COLUMNS\_

This meta table contains information about columns that cause triggers to fire when updated.

| Column name | Type    | Description            |
| ----------- | ------- | ---------------------- |
| TABLE_ID    | INTEGER | The table identifier   |
| TRIGGER_OID | BIGINT  | The trigger identifier |
| COLUMN_ID   | INTEGER | The column identifier  |

#### Column Information

##### TABLE_ID

This is the table identifier, and corresponds to a TABLE_ID in the SYS_TABLES_ meta table.

##### TRIGGER_OID

This is the trigger identifier, and corresponds to a TRIGGER_OID in the SYS_TRIGGERS_ meta table.

##### COLUMN_ID

This is the column ID, and corresponds to a COLUMN_ID in the SYS_COLUMNS_ meta table.

#### Reference Tables

```
SYS_TABLES_
SYS_TRIGGERS_
```

### SYS_USERS\_

This meta table contains information about database users. 

| Column name              | Type         | Description                                                  |
| ------------------------ | ------------ | ------------------------------------------------------------ |
| USER_ID                  | INTEGER      | The user identifier                                          |
| USER_NAME                | VARCHAR(128) | The user name                                                |
| PASSWORD                 | VARCHAR(256) | The user password                                            |
| DEFAULT_TBS_ID           | INTEGER      | The default tablespace identifier                            |
| TEMP_TBS_ID              | INTEGER      | The temporary tablespace identifier                          |
| ACCOUNT_LOCK             | CHAR(1)      | Whether the account is locked/unlocked N: UNLOCKED L: LOCKED |
| ACCOUNT_LOCK_DATE        | DATE         | The date on which the account was locked                     |
| PASSWORD_LIMIT_FLAG      | CHAR(1)      | Indicates the use of password management policies T: used F: not used |
| FAILED_LOGIN_ATTEMPTS    | INTEGER      | The maximum number of times login failure is permitted       |
| FAILED_LOGIN_COUNT       | INTEGER      | The number of times login fails                              |
| PASSWORD_LOCK_TIME       | INTEGER      | The amount of time needed to elapse for a locked account to become unlocked |
| PASSWORD_EXPIRY_DATE     | DATE         | The password expiry date                                     |
| PASSWORD_LIFE_TIME       | INTEGER      | The password validity period                                 |
| PASSWORD_GRACE_TIME      | INTEGER      | The password grace period following expiration               |
| PASSWORD_REUSE_DATE      | DATE         | The date on which identical passwords are available for reuse |
| PASSWORD_REUSE_TIME      | INTEGER      | Not used                                                     |
| PASSWORD_REUSE_MAX       | INTEGER      | The number of times identical passwords are available for reuse |
| PASSWORD_REUSE_COUNT     | INTEGER      | Not used                                                     |
| PASSWORD_VERIFY_FUNCTION | VARCHAR(128) | The CALLBACK function for verifying passwords                |
| USER_TYPE                | CHAR(1)      | Indicates the user type U: User R: Role                      |
| DISABLE_TCP              | CHAR(1)      | Availability of TCP connection T: TCP connection is disabled; SSL or IPC is enabled. F: TCP connection is enabled. |
| CREATED                  | DATE         | The time at which the database user was created              |
| LAST_DDL_TIME            | DATE         | The most recent time at which a DDL statement was used to make changes to the user |

#### Column Information

##### USER_ID

This is the user identifier. It is automatically assigned by the system sequence.

##### USER_NAME

This is the user-defined user name.

##### PASSWORD

This is the encrypted user password.

##### DEFAULT_TBS_ID

This is the identifier of the default tablespace, which is used when the user creates an object without explicitly specifying a tablespace.

##### TEMP_TBS_ID

This is the identifier for the user temporary tablespace.

##### DISABLE_TCP

Displays the availability of TCP connection.

#### Reference Table

```
DBA_USERS_
```

### DBA_USERS\_

This is a meta table which records the information of database user and it can only be viewed by the SYS user. Note that the information of tables and columns is identical with the SYS_USERS_.

| Column name              | Type         | Description                                                  |
| ------------------------ | ------------ | ------------------------------------------------------------ |
| USER_ID                  | INTEGER      | The user identifier                                          |
| USER_NAME                | VARCHAR(128) | The user name                                                |
| PASSWORD                 | VARCHAR(256) | The user password                                            |
| DEFAULT_TBS_ID           | INTEGER      | The default tablespace identifier                            |
| TEMP_TBS_ID              | INTEGER      | The temporary tablespace identifier                          |
| ACCOUNT_LOCK             | CHAR(1)      | Indicates whether account is locked N: UNLOCKED L: LOCKED    |
| ACCOUNT_LOCK_DATE        | DATE         | The data the account was locked                              |
| PASSWORD_LIMIT_FLAG      | CHAR(1)      | Indicates whether password management policy is used. T: Enable password management policy F: Disable password management policy |
| FAILED_LOGIN_ATTEMPTS    | INTEGER      | The maximum number of failed login attempts                  |
| FAILED_LOGIN_COUNT       | INTEGER      | The login failed count                                       |
| PASSWORD_LOCK_TIME       | INTEGER      | The amount of time taht must elapse after an account is locked once and then released again |
| PASSWORD_EXPIRY_DATE     | DATE         | The password expiration date                                 |
| PASSWORD_LIFE_TIME       | INTEGER      | The passwrod expiration time                                 |
| PASSWORD_GRACE_TIME      | INTEGER      | The grace time after password expiration                     |
| PASSWORD_REUSE_DATE      | DATE         | The date when the same password will be reused               |
| PASSWORD_REUSE_TIME      | INTEGER      | Not used                                                     |
| PASSWORD_REUSE_MAX       | INTEGER      | The number of reuse of the same password                     |
| PASSWORD_REUSE_COUNT     | INTEGER      | Not used                                                     |
| PASSWORD_VERIFY_FUNCTION | VARCHAR(128) | The Callback function to verify password                     |
| USER_TYPE                | CHAR(1)      | The user type display U: User R: Role                        |
| DISABLE_TCP              | CHAR(1)      | Indicates whether or not TCP connection is in use. T: Failed TCP connection, communication only with SSL or IPC F: Allow TCP connection |
| CREATED                  | DATE         | The time when the database user was created                  |
| LAST_DDL_TIME            | DATE         | The time when the last DDL change occurred for a user        |

#### Column Information

##### USER_ID

This is the user identifier, automatically assigned by a sequence in the system.

##### USER_NAME

This is the name of the user specified by the user.

##### PASSWORD

This is encrypted with the user's password.

##### DEFAULT_TBS_ID

This is the default tablespace identifier, used when the user does not explicitly specify a tablespace when creating an object.

##### TEMP_TBS_ID

This is the user's temporary tablespace identifier.

##### DISABLE_TCP

This indicates to allow or restrict the user's TCP connection.

### SYS_USER_ROLES\_

This meta table stores information about the roles granted to the user.

| Column name | Type    | Description                                            |
| ----------- | ------- | ------------------------------------------------------ |
| GRANTOR_ID  | INTEGER | The identifier of the user to whom the role is granted |
| GRANTEE_ID  | INTEGER | The identifier of the user who granted the role        |
| ROLE_ID     | INTEGER | The role identifier                                    |

#### Column Information

##### GRANTOR_ID

This is the identifier of the user who granted the role, and corresponds to a USER_ID value in the SYS_USERS_ meta table.

##### GRANTEE_ID

This is the identifier of the user to whom the role is granted, and corresponds to a USER_ID value in the SYS_USERS_ meta table. 

##### ROLE_ID

This is the role identifier, and corresponds to a USER_ID value in the SYS_USERS_ meta table.

#### Reference Table

```
SYS_USERS_
SYS_TABLES_
```

### SYS_VIEWS\_

Basic information about views is stored in the SYS_TABLES_ meta table. This meta table contains additional information about views.

| Column name | Type    | Description                                   |
| ----------- | ------- | --------------------------------------------- |
| USER_ID     | INTEGER | The identifier of the owner of the view       |
| VIEW_ID     | INTEGER | The view identifier                           |
| STATUS      | INTEGER | The view status                               |
| READ_ONLY   | CHAR(1) | Displays whether the view is a read-only view |

#### Column Information

##### USER_ID

This is the identifier of the view owner, and corresponds to a USER_ID in the SYS_USERS_ meta table.

##### VIEW_ID

This is the view identifier, and corresponds to a TABLE_ID in the SYS_TABLES_ meta table.

##### STATUS

This value indicates the status of the view:

- 0: VALID
- 1: INVALID

#### Reference Tables

```
SYS_USERS_
SYS_TABLES_
```

### SYS_VIEW_PARSE\_

This meta table contains the text of view creation statements.

| Column name | Type         | Description                                                  |
| ----------- | ------------ | ------------------------------------------------------------ |
| USER_ID     | INTEGER      | The identifier of the owner of the view                      |
| VIEW_ID     | INTEGER      | The identifier of the view                                   |
| SEQ_NO      | INTEGER      | When a view creation statement text is split and the text is saved as multiple text fragments in SYS_VIEW_PARSE_, this is the position of the record among the records. |
| PARSE       | VARCHAR(100) | A text fragment of the view creation statement               |

#### Column Information

##### USER_ID

This is the identifier of the view owner, and corresponds to a USER_ID in the SYS_USERS_ meta table.

##### VIEW_ID

This is the view identifier, and corresponds to a TABLE_ID in the SYS_TABLES_ meta table.

##### SEQ_NO

When a single statement corresponding to one view is saved as multiple records in SYS_VIEW_PARSE_, this is the position of the record among the records.

##### PARSE

When records are searched for using a single VIEW_ID and their PARSE values are concatenated in the order described in SEQ_NO, the complete view statement can be reconstructed.

#### Reference Tables

```
SYS_USERS_
SYS_TABLES_
```

### SYS_VIEW_RELATED\_

This meta table contains information about objects accessed by user-defined views.

| Column name         | Type         | Description                                                  |
| ------------------- | ------------ | ------------------------------------------------------------ |
| USER_ID             | INTEGER      | The identifier of the owner of the view                      |
| VIEW_ID             | INTEGER      | The view identifier                                          |
| RELATED_USER_ID     | INTEGER      | The identifier of the owner of the object that the view accesses |
| RELATED_OBJECT_NAME | VARCHAR(128) | The name of the object accessed by the view                  |
| RELATED_OBJECT_TYPE | INTEGER      | The type of the object accessed by the view                  |

#### Column Information

##### USER_ID

This is the identifier of the view owner, and corresponds to a USER_ID in the SYS_USERS_ meta table.

##### VIEW_ID

This is the identifier of the view, and corresponds to a TABLE_ID in the SYS_TABLES_ meta table.

##### RELATED_USER_ID

This is the identifier of the owner of the object accessed by the view, and corresponds to a USER_ID in the SYS_USERS_ meta table.

##### RELATED_OBJECT_NAME

This is the name of the object accessed by the view.

##### RELATED_OBJECT_TYPE

This identifies the type of object accessed by the view. Views can access stored functions, tables, sequences, other views, Database Link objects, and synonyms. The identifiers are as follows:

- 1: Stored function
- 2: Table, Sequence, View
- 4: Database link
- 5: Synonym

#### Reference Tables

```
SYS_USERS_
SYS_TABLES_
SYS_PROCEDURES_
```

### SYS_XA_HEURISTIC_TRANS\_

This is a meta table that contains identifiers and information about the status of the database’s global transactions.

| Column name      | Type         | Description                                            |
| ---------------- | ------------ | ------------------------------------------------------ |
| FORMAT_ID        | BIGINT       | The identifier of the format of the global transaction |
| GLOBAL_TX_ID     | VARCHAR(128) | The identifier of the global transaction               |
| BRANCH_QUALIFIER | VARCHAR(128) | The branch qualifier of the global transaction         |
| STATUS           | INTEGER      | The status of the global transaction                   |
| OCCUR_TIME       | DATE         | The time XA transaction occurred.                      |

#### Column Information

##### FORMAT_ID

This is the identifier of the format of the global transaction. 

##### GLOBAL_TX_ID

This is the identifier of the global transaction.

##### BRANCH_QUALIFIER

This is the branch qualifier of the global transaction.

##### STATUS

This is the status of the global transaction. 

### Performance Views

Performance views are structures that exist in memory but have the form of regular tables, and allow users to monitor internal information about an Altibase system, such as system memory, process status, sessions, buffers, threads, etc. 

Performance views allow Altibase users to easily obtain information about memory objects (e.g. session information, log information, thread information) using SQL statements while Altibase is running, in the same way that they would use SQL to search for data saved in regular tables. 

This section describes the kinds of performance views provided with Altibase, their structure and function, how to access them, and the information that each view provides.

#### Structures and Features

Inside Altibase there is not only information about user-created objects such as tables; there is also a variety of information required for the operation of the DBMS itself. Because Altibase has a hybrid structure, in which tables can be created and queried not only in memory space but also in disk space, monitoring Altibase is particularly critical. 

Performance views provide information about most of the internal memory structures used by Altibase processes in the form of views. Because the data is dynamically created in real time when a view is queried, users can always obtain up-to-date information about internal processes. 

Performance views are always read-only. If a user attempts to modify the data in a performance view, Altibase returns an error and rolls back the transaction. 

#### How to Use Performance Views

The entire list of performance views can be retrieved in iSQL as follows: 

```
iSQL> SELECT * FROM V$TAB;
```

Performance view schemas can be checked from iSQL using the DESC command, just as with regular tables, and SELECT statements can also be used to query data in the same way that they would be used to query regular tables

#### V$Views

Performance views are identified by the prefix V$. The following table lists all performance views.

| Name                                  | Description                                                  |
| ------------------------------------- | ------------------------------------------------------------ |
| V\$ACCESS_LIST                        | Information about access or block on specific IP packets     |
| V\$ALLCOLUMN                          | Information about the columns that make up a performance view |
| V\$ARCHIVE                            | Archive and backup- related information                      |
| V\$BACKUP_INFO                        | Information about incremental backups performed until now    |
| V\$BUFFPAGEINFO                       | Statistics on the buffer frame of the buffer manager         |
| V\$BUFFPOOL_STAT                      | Buffer pool related statistics, including the buffer pool hit ratio |
| V\$CATALOG                            | Information about the structure of tables                    |
| V\$DATABASE                           | Internal information about memory database space             |
| V\$DATAFILES                          | Information about data files which are related to tablespaces |
| V\$DATATYPE                           | Information about data types supported by Altibase           |
| V\$DBA_2PC_PENDING                    | A list of distributed transactions whose status is “in-doubt” |
| V\$DBLINK_ALTILINKER_STATUS           | Status information about the AltiLinker process for the database link |
| V\$DBLINK_DATABASE_LINK_INFO          | Information about the database link object existing in the database |
| V\$DBLINK_GLOBAL_TRANSACTION_INFO     | Information about the transactions using the database link   |
| V\$DBLINK_LINKER_CONTROL_SESSION_INFO | Status information about the Linker Control Session          |
| V\$DBLINK_LINKER_DATA_SESSION_INFO    | Status information about the Linker Data Sessions            |
| V\$DBLINK_LINKER_SESSION_INFO         | Information about the number of Linker Control Session and Linker Data Sessions. |
| V\$DBLINK_NOTIFIER_TRANSACTION_INFO   | Information about distributed transaction (on which a failure occurred) AltiLinker processes. |
| V\$DBLINK_REMOTE_STATEMENT_INFO       | Information about statements that are executed on the remote server when using Database Link |
| V\$DBLINK_REMOTE_TRANSACTION_INFO     | Information about transactions that occur on the remote server when using Database Link |
| V\$DBMS_STATS                         | Statistical information about the whole database             |
| V\$DB_FREEPAGELISTS                   | Information about all usable page lists                      |
| V\$DB_PROTOCOL                        | Information about database protocols input into the server   |
| V\$DIRECT_PATH_INSERT                 | Information about historical statistics on direct-path uploads |
| V\$DISKTBL_INFO                       | Information about disk tables                                |
| V\$DISK_BTREE_HEADER                  | Information about headers of disk BTREE indexes              |
| V\$DISK_RTREE_HEADER                  | Information about headers of disk RTREE indexes              |
| V\$DISK_TEMP_INFO                     | Information about the minimum value of memory to line up the disk temporary tables |
| V\$DISK_TEMP_STAT                     | Information on each disk temporary table                     |
| V\$DISK_UNDO_USAGE                    | Information about the amount of undo tablespace on disk that is currently being used |
| V\$EVENT_NAME                         | Information about Altibase server wait events                |
| V\$EXTPROC_AGENT                      | Information about the Agent Process created for the execution of external procedures |
| V\$FILESTAT                           | Statistical information about disk data file I/O             |
| V\$FLUSHER                            | Information about the flusher which flushes the buffers      |
| V\$FLUSHINFO                          | Buffer flush information                                     |
| V\$INDEX                              | Information about table indexes                              |
| V\$INSTANCE                           | Information about the current startup phase                  |
| V\$INTERNAL_SESSION                   | Information about a session created in the DBMS_CONCURRENT_EXEC package |
| V\$LATCH                              | Information about the Buffer Control Block (BCB) latch of the buffer pool and statistical information about read/write latch attempts made on data pages |
| V\$LFG                                | Information about LFG and statistical information related to GROUP COMMIT |
| V\$LOCK                               | Information about all table level lock nodes in the database at the current point in time |
| V\$LOCK_STATEMENT                     | Information about locks and statements, shown together       |
| V\$LOCK_WAIT                          | Information about the status of transactions waiting to obtain locks |
| V\$LOG                                | Information about log anchor files                           |
| V\$MEMGC                              | Information about garbage collection (memory space recovery) |
| V\$MEMSTAT                            | Statistical information about memory use by Altibase processes |
| V\$MEMTBL_INFO                        | Information about memory tables                              |
| V\$MEM_BTREE_HEADER                   | Information about headers of memory BTREE indexes            |
| V\$MEM_BTREE_NODEPOOL                 | Information about node pools for memory BTREE Indices        |
| V\$MEM_RTREE_HEADER                   | Information about headers of memory RTREE indexes            |
| V\$MEM_RTREE_NODEPOOL                 | Information about node pools for memory RTREE indexes        |
| V\$MEM_TABLESPACES                    | Information about tablespaces created in memory              |
| V\$MEM_TABLESPACE_CHECKPOINT_PATHS    | Information about the location of DB files in which to record checkpointing details during checkpointing |
| V\$MEM_TABLESPACE_STATUS_DESC         | Internal information about the status of memory tablespaces  |
| V\$MUTEX                              | Statistical information about mutexes, used by Altibase for concurrency control |
| V\$NLS_PARAMETERS                     | Information about parameters related to NLS                  |
| V\$NLS_TERRITORY                      | Information about the names of territories available to be set for the database or the current session |
| V\$OBSOLETE_BACKUP_INFO               | Backup information no longer required to be retained         |
| V\$PKGTEXT                            | Information about strings of the packages executed on the system |
| V\$PLANTEXT                           | Information about SQL execution plan text                    |
| V\$PROCTEXT                           | Information about stored procedure text                      |
| V\$PROPERTY                           | Information about internally set Altibase properties         |
| V\$REPEXEC                            | Information about the replication manager                    |
| V\$REPGAP                             | Information about the difference between the log record currently being processed by the replication Sender and the most recently created log record |
| V\$REPGAP_PARALLEL                    | Information about the difference between the sequence number of the log record currently being processed by replication sender threads working in parallel and the sequence number of the most recently created log record |
| V\$REPLOGBUFFER                       | Information about the log buffer used for replication        |
| V\$REPOFFLINE_STATUS                  | Information about the status of offline replication execution |
| V\$REPRECEIVER                        | Information about the replication Receiver                   |
| V\$REPRECEIVER_COLUMN                 | Information about target columns for the replication Receiver |
| V\$ REPRECEIVER_PARALLEL              | Information about replication Receiver threads working in parallel |
| V\$REPRECEIVER_PARALLEL_APPLY         | Information about replication applier threads                |
| V\$REPRECEIVER_STATISTICS             | Statistical information about the execution time per task of the replication receive thread |
| V\$REPRECEIVER_TRANSTBL               | Transaction table information for replication receivers      |
| V\$REPRECEIVER_TRANSTBL_PARALLEL      | information about transaction tables used by multiple replication Receiver threads working in parallel. |
| V\$REPRECOVERY                        | Recovery information used in replication                     |
| V\$REPSENDER                          | Information about the replication Sender                     |
| V\$REPSENDER_PARALLEL                 | Information about replication Sender threads working in parallel |
| V\$REPSENDER_SENT_LOG_COUNT           | Information about the number of logs sent by the replication Sender for each DML type |
| V\$REPSENDER_SENT_LOG_COUNT_PARALLEL  | Information about the number of logs sent by each Sender thread for each DML type in parallel replication in EAGER mode |
| V\$REPSENDER_STATISTICS               | Statistical information about the execution time for each task of the replication send thread |
| V\$REPSENDER_TRANSTBL                 | Information about transaction tables used by the replication Sender |
| V\$REPSENDER_TRANSTBL_PARALLEL        | Information about transaction tables used by replication Sender threads working in parallel |
| V\$REPSYNC                            | Information about tables that are synchronized using replication |
| V\$SBUFFER_STAT                       | Statistical information about secondary buffers              |
| V\$SEGMENT                            | Information about segments, which constitute tables and indexes |
| V\$SEQ                                | Sequence-related information                                 |
| V\$SERVICE_THREAD                     | Information about service threads related to multiplexing    |
| V\$SERVICE_THREAD_MGR                 | Dynamic Service threads status information related to multiplexing. |
| V\$SESSION                            | Information about sessions created internally in Altibase    |
| V\$SESSION_EVENT                      | Statistical information about all wait events for all currently connected sessions |
| V\$SESSION_WAIT                       | Information about wait events for all currently connected sessions |
| V\$SESSION_WAIT_CLASS                 | Cumulative wait statistic information classified by session, wait event and wait class for all currently connected sessions |
| V\$SESSIONMGR                         | Statistical information about Altibase sessions              |
| V\$SESSTAT                            | Information about the status of currently connected sessions |
| V\$SFLUSHER                           | Information about tasks flushing secondary buffer pages to disk |
| V\$SFLUSHINFO                         | Flushing information about secondary buffers                 |
| V\$SNAPSHOT                           | The information of SNAPSHOT settings, memory, and disk undo tablespace |
| V\$SQLTEXT                            | Information about the text of all SQL statements executed in the system |
| V\$SQL_PLAN_CACHE                     | Information about the current status and statistical information about the SQL Plan Cache |
| V\$SQL_PLAN_CACHE_PCO                 | Information about Plan Cache objects registered in the SQL Plan Cache |
| V\$SQL_PLAN_CACHE_SQLTEXT             | Information about SQL statements registered in the SQL Plan Cach |
| V\$STABLE_MEM_DATAFILES               | Information about the paths of data file(s)                  |
| V\$STATEMENT                          | Information about statements for all current Altibase sessions |
| V\$STATNAME                           | Information about the name and status of the system and sessions |
| V\$ST_ANGULAR_UNIT                    | Reserved for future use                                      |
| V\$ST_AREA_UNIT                       | Reserved for future use                                      |
| V\$ST_LINEAR_UNIT                     | Reserved for future use                                      |
| V\$SYSSTAT                            | Information about the status of the system                   |
| V\$SYSTEM_CONFLICT_PAGE               | Information about latch contention according to page type    |
| V\$SYSTEM_EVENT                       | Cumulative statistical information about waits from startup to the current time, classified according to wait event |
| V\$SYSTEM_WAIT_CLASS                  | Cumulative statistical information about waits from startup to the current time, classified according to wait class |
| V\$TABLE                              | Information about records and columns for all performance views |
| V\$TABLESPACES                        | Information about tablespaces                                |
| V\$TIME_ZONE_NAMES                    | Region names, abbreviations and UTC offset values available to be set for the TIME_ZONE property |
| V\$TRACELOG                           | Information about trace logging                              |
| V\$TRANSACTION                        | Information about transaction objects                        |
| V\$TRANSACTION_MGR                    | R Information about the transaction manager of Altibase      |
| V\$TSSEGS                             | Information about all TSS segments                           |
| V\$TXSEGS                             | Information about bound transaction segments                 |
| V\$UDSEGS                             | Information about all undo segments                          |
| V\$UNDO_BUFF_STAT                     | Statistical Information about the undo tablespace buffer pool |
| V\$USAGE                              | Statistical information about the amount of space used by tables and indexes |
| V\$VERSION                            | Altibase product version information                         |
| V\$VOL_TABLESPACES                    | Information about volatile tablespaces                       |
| V\$WAIT_CLASS_NAME                    | Information for grouping wait events into classes            |
| V\$XID                                | List of XIDs, which are branches of distributed transactions, that currently exist in the DBMS |

### V\$ACCESS_LIST

This view displays access permission or deny information on specific IP packets accessing to Altibase.

| Column name | Type        | Description                                    |
| ----------- | ----------- | ---------------------------------------------- |
| ID          | INTEGER     | ACCESS LIST Identifier                         |
| ADDRESS     | VARCHAR(40) | IP address                                     |
| OPERATION   | VARCHAR(6)  | Access permit or deny status of IP address     |
| MASK        | VARCHAR(16) | Subnet Mask (IPv4) or prefix big length (IPv6) |

#### **Column Information**

##### ID

ID describes an identifier for permit or deny list of IP packets.

##### ADDRESS

ADDRESS describes the IP packet address.

##### OPERATION

OPERATION displays the status of permit or deny of the IP packet address.

- PERMIT : Access permit
- DENY: Access deny

##### MASK

If the specified address is in IPv4 address notation, subnet mask is described whereas the length of prefix bit is described if the specified address is in IPv6 address notation. Refer to the description delineated in the ACCESS_LIST property.

### V\$ALLCOLUMN

This view displays information about the columns in all performance views.

| Column name | Type        | Description                                    |
| ----------- | ----------- | ---------------------------------------------- |
| TABLENAME   | VARCHAR(39) | The name of the performance view               |
| COLNAME     | VARCHAR(39) | The name of the column in the performance view |

#### Column Information

##### TABLENAME

This is the name of the performance view.

##### COLNAME

This is the name of the column in the performance view.

### V\$ARCHIVE 

This view displays the information related to archiving and backups.

| Column name           | Type          | Description                                                 |
| --------------------- | ------------- | ----------------------------------------------------------- |
| LFG_ID                | INTEGER       | The log file group identifier                               |
| ARCHIVE_MODE          | BIGINT        | Archive log mode 0: no archive log mode 1: archive log mode |
| ARCHIVE_THR_RUNNING   | BIGINT        | Information about the execution of the archivelog thread    |
| ARCHIVE_DEST          | VARCHAR(1024) | The directory in which logs are to be archived              |
| NEXTLOGFILE_TO_ARCH   | INTEGER       | The number of the next log file to be archived              |
| OLDEST_ACTIVE_LOGFILE | INTEGER       | The number of the oldest of the online log files            |
| CURRENT_LOGFILE       | INTEGER       | The number of the current online log file                   |

#### Column Information

##### LFG_ID

This is the identifier of the LFG which default value is ‘0’.

##### ARCHIVE_MODE

This indicates the archive log mode of the database.

0: No archive log mode

1: Archive log mode

### V\$BACKUP_INFO

This view displays information about all incremenetal backups performed until now.

| Column name                    | Type      | Description                       |
| ------------------------------ | --------- | --------------------------------- |
| BEGIN_BACKUP_TIME              | CHAR(24)  | The start time of the backup      |
| END_BACKUP_TIME                | CHAR(24)  | The completion time of the backup |
| INCREMENTAL_BACKUP_CHUNK_COUNT | INTEGER   | The incremental chunk size        |
| BACKUP_TARGET                  | INTEGER   | The backup target                 |
| BACKUP_LEVEL                   | INTEGER   | The backup level                  |
| BACKUP_TYPE                    | INTEGER   | The backup type                   |
| TABLESPACE_ID                  | INTEGER   | The backup target tablespace ID   |
| FILE_ID                        | INTEGER   | The backup target datafile ID     |
| BACKUP_TAG                     | CHAR(128) | The backup tag name               |
| BACKUP_FILE                    | CHAR(512) | The backup file                   |

#### Column Information

##### BEGIN_BACKUP_TIME

This indicates the point in time at which backup started and is expressed in the 'YYYY-MM-DD HH:MM:SS' format.

##### END_BACKUP_TIME

This indicates the point in time at which backup completed and is expressed in the 'YYYY-MM-DD HH:MM:SS' format.

##### INCREMENTAL_BACKUP_CHUNK_COUNT

0 is always displayed for level 0 incremental backups. The size of an incremental chunk is displayed for level 1 incremental backups.

For more detailed information about incremental chunks, please refer to the INCREMENTAL_BACKUP_CHUNK_SIZE property.

##### BACKUP_TARGET

This indicates the backup target.

1: Database

2: Tablespace

##### BACKUP_LEVEL

This indicates the backup level.

1: Level 0

2: Level 1

##### BACKUP_TYPE

This indicates the backup type.

1: Full backup

2: Differential incremental backup

4: Cumulative incremental backup

##### TABLESPACE_ID

This indicates the ID of the tablespace to which the backed up datafile belongs.

##### FILE_ID

This indicates the ID of the backed up datafile.

##### BACKUP_TAG

This indicates the backup tag name used for the incremental backup.

##### BACKUP_FILE

This indicates the full path, including the backup file name.

### V\$BUFFPAGEINFO 

This view shows statistics about the main operations managed by the buffer manager for each type of page in the buffer frame.

| Column name       | Type        | Description                                                  |
| ----------------- | ----------- | ------------------------------------------------------------ |
| PAGE_TYPE         | VARCHAR(21) | The type of page                                             |
| READ_PAGE_COUNT   | BIGINT      | The number of times that disk I/O (READ) was initiated       |
| GET_PAGE_COUNT    | BIGINT      | The number of times that buffer frames have been requested   |
| FIX_PAGE_COUNT    | BIGINT      | The number of times that buffer frames have been fixed       |
| CREATE_PAGE_COUNT | BIGINT      | The number of times that new buffer frames have been requested |
| HIT_RATIO         | DOUBLE      | The buffer frame hit ratio                                   |

#### Column Information

##### PAGE_TYPE

PAGE_TYPE indicates the type of buffer page. The possible values are as follows: 

| PAGE_TYPE             | Description                                                  |
| --------------------- | ------------------------------------------------------------ |
| PAGE UNFORMAT         | An unformatted page                                          |
| PAGE FORMAT           | A formatted page                                             |
| PAGE INDEX META BTREE | A page in which meta information about a B-Tree index is written |
| PAGE INDEX META RTREE | A page in which meta information about an R-Tree index is written |
| PAGE INDEX BTREE      | A page in which a B-Tree index node is written               |
| PAGE INDEX RTREE      | A page in which an R-Tree index node is written              |
| PAGE TABLE            | A page in which table records are written                    |
| PAGE TEMP TABLE META  | A page in which meta information about a single temporary table is written |
| PAGE TEMP TABLE DATA  | A page in which the records stored in a temporary table are written |
| PAGE TSS              | A page in which information about the status of a transaction is written. Multiple transaction status slots (TSS) can be written to a single page. |
| PAGE UNDO             | A page in which UNDO information is written. A single page can contain multiple UNDO records. |
| PAGE LOB DATA         | A page in which LOB type data are written. A single page cannot contain more than one LOB column. Moreover, a single LOB column can span multiple pages. |
| PAGE LOB INODE        | A page in which an index node, which pertains to LOB data that exceed a certain size, is written |
| PAGE FMS SEGHDR       | A page in which a single FMS header is written               |
| PAGE FMS EXTDIR       | a pages in which a FMS extent directory is written           |
| PAGE TMS SEGHDR       | A page in which a single TMS header is written               |
| PAGE TMS LFBMP        | A page in which a single TMS leaf bitmap node is written     |
| PAGE TMS ITBMP        | A page in which a single TMS internal bitmap node is written |
| PAGE TMS RTBMP        | A page in which a single TMS root bitmap node is written     |
| PAGE TMS EXTDIR       | A page in which a single TMS extent directory is written     |
| PAGE CMS SEGHDR       | A page in which a single CMS header is written               |
| PAGE CMS EXTDIR       | A page in which a single CMS extent directory is written     |
| PAGE FEBT FSB         | A page in which a single datafile header is written          |
| PAGE FEBT EGHA        | A page in which meta information about a LOB data column is written |
| PAGE LOB META         | A page in which meta information about a LOB data column is written |
| PAGE HV TEMP NODE     | A page in which a node of a Hash Value-Based Temp Index is written |

##### READ_PAGE_COUNT

This is the total number of disk I/O (read) requests that have been made for buffer frames related to this PAGE_TYPE since the server was started. The value can be 0 or greater

##### GET_PAGE_COUNT

Shows the total number of read or write requests that have been made to the buffer manager for buffer frames related to this PAGE_TYPE since the server was started. The value can be 0 or greater.

##### FIX_PAGE_COUNT

This shows the total number of fixes for buffer frames related to PAGE_TYPE received by the buffer manager for reading or writing data since the server was started. The value can be 0 or greater.

##### CREATE_PAGE_COUNT

This shows the number of requests for new buffer frames for this PAGE_TYPE made to the buffer manager since the server was started. The value can be 0 or greater.

##### HIT_RATIO

This shows the hit ratio for this buffer since the server was started. Its value can be calculated as follows: (GET_PAGE_COUNT + FIX_PAGE_COUNT - READ_PAGE_COUNT) / (GET_PAGE_COUNT + FIX_PAGE_COUNT)

#### Example

After the server starts, check the cumulative value of major operations for each page type managed in the buffer.

```
iSQL> select * from v$buffpageinfo;
PAGE_TYPE            READ_PAGE_COUNT      GET_PAGE_COUNT       
---------------------------------------------------------------------
FIX_PAGE_COUNT       CREATE_PAGE_COUNT    HIT_RATIO       
---------------------------------------------------------------------
PAGE UNFORMAT          0                    0                
0                    0                    0                      
PAGE FORMAT            0                    0                 
0                    0                    0                      
PAGE INDEX META BTREE  4                    0                 
4                    0                    0                      
PAGE INDEX META RTREE  0                    0                 
0                    0                    0                      
PAGE INDEX BTREE       12                   0                 
12                   0                    0                      
PAGE INDEX RTREE       0                    0                 
0                    0                    0                      
PAGE TABLE             0                    0                   
0                    0                    0                      
PAGE TEMP TABLE META   0                    0                 
0                    0                    0                      
PAGE TEMP TABLE DATA   0                    0                 
0                    0                    0                      
PAGE TSS               0                    0                   
0                    0                    0                      
PAGE UNDO              0                    0                 
0                    0                    0                      
PAGE LOB DATA          0                    0                 
0                    0                    0                      
PAGE LOB INODE         0                    0                  
0                    0                    0                      
PAGE FMS SEGHDR        0                    0                 
0                    0                    0                      
PAGE FMS EXTDIR        0                    0                 
0                    0                    0                      
PAGE TMS SEGHDR        5                    19               
4                    0                    73.6842105263158       
PAGE TMS LFBMP         0                    0                 
0                    0                    0                      
PAGE TMS ITBMP         0                    0                   
0                    0                    0                      
PAGE TMS RTBMP         0                    0                 
0                    0                    0                      
PAGE TMS EXTDIR        0                    0                 
0                    0                    0                      
PAGE CMS SEGHDR        0                    1536             
0                    512                  100                    
PAGE CMS EXTDIR        0                    0                 
0                    0                    0                      
PAGE FEBT FSB          2                    1024               
515                  2                    99.8046875             
PAGE FEBT EGH          0                    512               
0                    4                    100                    
PAGE LOB META          0                    0                 
0                    0                    0                      
PAGE HV TEMP NODE      0                    0                 
0                    0                    0                      
26 rows selected.
```

### V\$BUFFPOOL_STAT

This view displays statistics including the buffer pool hit ratio and the buffer control block (BCB) count of the buffer pool.

| Column name            | Type    | Description                                                  |
| ---------------------- | ------- | ------------------------------------------------------------ |
| ID                     | INTEGER | The identifier of the buffer pool                            |
| POOL_SIZE              | INTEGER | The number of pages in the buffer pool                       |
| PAGE_SIZE              | INTEGER | The size of a page (in bytes)                                |
| HASH_BUCKET_COUNT      | INTEGER | The number of hash table buckets                             |
| HASH_CHAIN_LATCH_COUNT | INTEGER | The number of chain latches used in the hash table of the buffer pool |
| LRU_LIST_COUNT         | INTEGER | The number of LRU lists                                      |
| PREPARE_LIST_COUNT     | INTEGER | The number of prepare lists in the buffer pool               |
| FLUSH_LIST_COUNT       | INTEGER | The number of flush lists in the buffer pool                 |
| CHECKPOINT_LIST_COUNT  | INTEGER | The number of checkpoint lists in the buffer pool            |
| VICTIM_SEARCH_COUNT    | INTEGER | The number of victim searches in an LRU List                 |
| HASH_PAGES             | INTEGER | The number of pages inserted into the hash table at present  |
| HOT_LIST_PAGES         | INTEGER | The number of pages in LRU hot lists at present              |
| COLD_LIST_PAGES        | INTEGER | The number of pages in LRU cold lists at present             |
| PREPARE_LIST_PAGES     | INTEGER | The number of prepare lists in the buffer pool               |
| FLUSH_LIST_PAGES       | INTEGER | The number of pages in all flush lists at present            |
| CHECKPOINT_LIST_PAGES  | INTEGER | The number of pages in all checkpoint lists at present       |
| FIX_PAGES              | BIGINT  | The accumulated number of page fix requests without latches  |
| GET_PAGES              | BIGINT  | The accumulated number of page requests for which latches were obtained |
| READ_PAGES             | BIGINT  | The accumulated number of page reads from disk               |
| CREATE_PAGES           | BIGINT  | The accumulated number of new page creation tasks            |
| HIT_RATIO              | DOUBLE  | The cumulative hit ratio from the buffer pool since the system was started |
| HOT_HITS               | BIGINT  | The accumulated number of accesses to an LRU hot list        |
| COLD_HITS              | BIGINT  | The accumulated number of accesses to an LRU cold list       |
| PREPARE_HITS           | BIGINT  | The accumulated number of accesses to a prepare list         |
| FLUSH_HITS             | BIGINT  | The accumulated number of accesses to a prepare list         |
| OTHER_HITS             | BIGINT  | The accumulated number of accesses to buffers not included on any list |
| PREPARE_VICTIMS        | BIGINT  | The accumulated number of searches for replacement targets on a prepare list |
| LRU_VICTIMS            | BIGINT  | The accumulated number of searches for replacement targets on an LRU list |
| VICTIM_FAILS           | BIGINT  | The number of failures to find a replacement target          |
| PREPARE_AGAIN_VICTIMS  | BIGINT  | The cumulative number of searches for a replacement target buffer on a prepare list after failing to find a replacement target on an LRU list |
| VICTIM_SEARCH_WARP     | BIGINT  | The number of searches that continued to subsequent prepare lists after failing to find replacement targets on prepare lists or LRU lists |
| LRU_SEARCHS            | BIGINT  | The accumulated number of searched buffers on an LRU list    |
| LRU_SEARCHS_AVG        | INTEGER | The average number of buffers searched for a replacement target |
| LRU_TO_HOTS            | BIGINT  | The accumulated number of times that a Buffer Control Block (BCB) has moved into a hot area in an LRU list |
| LRU_TO_COLDS           | BIGINT  | The accumulated number of times that a BCB has moved into a cold area in an LRU list |
| LRU_TO_FLUSHS          | BIGINT  | The accumulated number of times that a BCB has moved from an LRU list to a flush list |
| HOT_INSERTIONS         | BIGINT  | The accumulated number of insertions into LRU hot lists      |
| COLD_INSERTIONS        | BIGINT  | The accumulated number of insertions into LRU cold lists     |
| DB_SINGLE_READ_PERF    | DOUBLE  | The average number of bytes that are read from disk per second when one data page is read from a disk data file |
| DB_MULTI_READ_PERF     | DOUBLE  | The average number of bytes that are read per second when multiple data pages are read from a disk data file at the same time |

#### Column Information

##### ID

This is a unique buffer pool number. Its value is 0 because multiple buffer pools are not currently supported. 

##### POOL_SIZE

This is the number of pages in the buffer pool. POOL_SIZE * PAGE_SIZE is equal to the size specified by the BUFFER_AREA_SIZE property.

##### PAGE_SIZE

This is the size of the pages used in the buffer pool at present. Only the fixed value 8192 is possible, because multiple buffer pools are not currently supported. 

##### HASH_BUCKET_COUNT

This is the number of hash table buckets. It is determined by the BUFFER_HASH_BUCKET_DENSITY property. This value cannot be changed while the server is running. The greater this value is, the less expensive it is to search the hash bucket list.

##### HASH_CHAIN_LATCH_COUNT

This is the number of chain latches used in the hash table. The greater this value is, the less competition there is for latches, which can occur when searching the hash table.

##### LRU_LIST_COUNT

This is the number of LRU lists in the buffer pool. 

##### PREPARE_LIST_COUNT

This is the number of prepare lists in the buffer pool.

##### FLUSH_LIST_COUNT

This is the number of flush lists in the buffer pool.

##### CHECKPOINT_LIST_COUNT

This is the number of flush lists in the buffer pool.

##### VICTIM_SEARCH_COUNT

This is the maximum number of BCBs that are searched when searching for replacement targets in LRU lists. If the search for replacement targets reaches the specified value and no replacement target is found, Buffer Manager waits until the flusher adds a clean buffer to the prepare list.

##### HASH_PAGES

This is the number of buffers that have been inserted into the hash table. lts value indicates the number of buffers currently in use. 

##### HOT_LIST_PAGES

This is the number of buffers that exist on the LRU hot list. 

##### COLD_LIST_PAGES

This is the number of buffers that exist on the LRU cold list.

##### PREPARE_LIST_PAGES

This is the number of buffers that exist on the prepare list. If the value is 0, the LRU list is searched in order to obtain replacement targets.

##### FLUSH_LIST_PAGES

This is the number of buffers that exist on the flush list. A high value means that there are many buffers to be flushed. 

##### CHECKPOINT_LIST_PAGES

This is the number of buffers that exist on the checkpoint list. It also indicates the number of pages that have been renewed. 

##### FIX_PAGES

This is the cumulative number of pages that have been requested without obtaining latches since the system was started.

##### GET_PAGES

This is the cumulative number of page latches that have been have been requested and obtained since the system was started.

##### READ_PAGES

This is the cumulative number of pages that have been read from disk when requesting a page. It also indicates the number of buffer misses.

##### CREATE_PAGES

This is the cumulative number of page assignments for the insertion of data into new pages. Page creation isn't actually accompanied by disk I/O.

##### HIT_RATIO

This is the cumulative hit ratio in the buffer pool. It can be calculated thus: (GET_PAGES + FIX_PAGES - READ_PAGES)/(GET_PAGES + FIX_PAGES). If this value is low, it means that many pages have been read from disk instead of from the cache. In other words, if the value is low, the system will not be able to process queries quickly.

##### HOT_HITS

This is the cumulative number of hits on the LRU hot list. If a requested page is already in the buffer, a hit doesn't cause a page to be read.

##### COLD_HITS

This is the cumulative number of hits on the LRU cold list.

##### PREPARE_HITS

This is the cumulative number of hits on the prepare list. 

##### FLUSH_HITS

This is the cumulative number of hits on the flush list.

##### OTHER_HITS

This is the number of hits on a buffer that was not on any list at that moment. A hit buffer need not always be on a list.

##### PREPARE_VICTIMS

This is the cumulative number of searches for replacement buffers on a prepare list. 

##### LRU_VICTIMS

This is the cumulative number of searches for replacement buffers on an LRU list.

##### VICTIM_FAILS

This is the cumulative number of failures to find a replacement target buffer. This value can be calculated thus: PREPARE_AGAIN_VICTIMS + VICTIM_SEARCH_WARP. 

Summing PREPARE_VICTIMS + LRU_VICTIMS + VICTIM_FAILS gives the total number of replacements in the buffer pool.

##### PREPARE_AGAIN_VICTIMS

After failing to find replacement target buffers, it is necessary to wait for the insertion of buffers on a prepare list. While waiting, this is the number of clean buffers that have been received and selected as replacement targets.

##### VICTIM_SEARCH_WARP

This is the cumulative number of searches for replacement target buffers that failed after the specified period of time and thus passed to the next prepare list.

##### LRU_SEARCHS

This is the cumulative number of buffers for which searches for replacement target buffers have been made in the LRU list.

##### LRU_SEARCHS_AVG

This is the average number of buffers that are searched when searching for a replacement target.

##### LRU_TO_HOTS

This is the cumulative number of times that buffers have moved into hot areas in LRU lists.

##### LRU_TO_COLDS

This is the cumulative number of times that buffers have moved into cold areas in LRU lists.

##### LRU_TO_FLUSHS

This is the cumulative number of times that buffers have moved from LRU lists to flush lists. 

##### HOT_INSERTIONS

This is the cumulative number of insertions into LRU hot lists.

##### COLD_INSERTIONS

This is the cumulative number of insertions into LRU cold lists. 

##### DB_SINGLE_READ_PERF

When FETCH, INSERT, UPDATE and DELETE operations are performed on disk tables, one data page is read from a data file on disk and stored in a memory buffer. This is the average number of bytes that are read from disk per second (in kB/sec) in the course of such tasks.

##### DB_MULTI_READ_PERF

When a so-called "full scan" is performed, i.e. when an entire disk table is scanned, multiple data pages are simultaneously read from a data file on disk and stored in a memory buffer. This is the average number of bytes that are read from disk per second (in kB/sec) in the course of this task.

### V\$CATALOG

This view displays information about the structure of the tables that exist in the database.

| Column name         | Type    | Description                                                  |
| ------------------- | ------- | ------------------------------------------------------------ |
| TABLE_OID           | BIGINT  | The object identifier of the table                           |
| COLUMN_CNT          | INTEGER | The number of columns in the table                           |
| COLUMN_VAR_SLOT_CNT | INTEGER | The number of variable slots, which are used to store information about columns |
| INDEX_CNT           | INTEGER | The number of indexes in the table                           |
| INDEX_VAR_SLOT_CNT  | INTEGER | The number of variable slots, which are used to store information about indexes |

#### Column Information

##### TABLE_OID

This is the physical location of the header, which contains information about the table.

##### COLUMN_CNT

This is the number of columns in the table.

##### COLUMN_VAR_SLOT_CNT

This is the number of variable slots, which are used to store information about the columns in the table.

##### INDEX_CNT

This is the number of indexes in the table. 

##### INDEX_VAR_SLOT_CNT

This is the number of variable slots, which are used to store information about the indexes in the table.

### V\$DATABASE

V$DATABASE displays internal information about the memory database.

| Column name          | Type         | Description                                                  |
| -------------------- | ------------ | ------------------------------------------------------------ |
| DB_NAME              | VARCHAR(128) | The database name                                            |
| PRODUCT_SIGNATURE    | VARCHAR(512) | A string describing the product binary and build environment |
| DB_SIGNATURE         | VARCHAR(512) | A unique database identification string                      |
| VERSION_ID           | INTEGER      | The version of the database                                  |
| COMPILE_BIT          | INTEGER      | Whether the product was compiled for 32 bits or 64 bits      |
| ENDIAN               | BIGINT       | Endian information                                           |
| LOGFILE_SIZE         | BIGINT       | The log file size                                            |
| TX_TBL_SIZE          | INTEGER      | The transaction table size                                   |
| LAST_SYSTEM_SCN      | VARCHAR(29)  | For internal usage only                                      |
| INIT_SYSTEM_SCN      | VARCHAR(29)  | For internal usage only                                      |
| DURABLE_SYSTEM_SCN   | VARCHAR(29)  | The saved system SCN value                                   |
| MEM_MAX_DB_SIZE      | VARCHAR(256) | The maximum size of the memory database                      |
| MEM_ALLOC_PAGE_COUNT | BIGINT       | The total number of allocated pages                          |
| MEM_FREE_PAGE_COUNT  | BIGINT       | The total number of available pages                          |
| MAX_ACCESS_FILE_SIZ  | VARCHAR(12)  | The maximum file size that can be created in the database    |

#### Column Information

##### DB_NAME

This is the name of the memory database.

##### PRODUCT_SIGNATURE

This is unique product information about Altibase.

##### DB_SIGNATURE

A unique database identification string.

##### VERSION_ID

This is a unique version number managed by the storage manager of Altibase.

##### COMPILE_BIT

This indicates whether the database was compiled as a 32-bit or 64-bit application.

##### ENDIAN

This is the Endian of the database.

- 0: little endian
- 1: big endian

##### LOGFILE_SIZE

This is the size, in bytes, of the log files used by the database.

##### TX_TBL_SIZE

This is the size of the transaction table.

##### MEM_MAX_DB_SIZE

This is the maximum size to which the memory database can expand. 

##### MEM_ALLOC_PAGE_COUNT

This is the total number of pages currently allocated to the memory database. This only indicates the current size of memory database space, not the maximum size to which it can expand. The current size of memory database space can be calculated by multiplying the sum of MEM_ALLOC_PAGE_COUNT and MEM_FREE_PAGE_COUNT by the page size (32kB).

##### MEM_FREE_PAGE_COUNT

This is the number of pages available to be allocated to memory database space, not including the number of pages that are currently allocated. This only pertains to the current size of memory database space, not the maximum size to which it can expand. The current size of memory database space can be calculated by multiplying the sum of MEM_ALLOC_PAGE_COUNT and MEM_FREE_PAGE_COUNT by the page size (32kB).

##### DURABLE_SYSTEM_SCN

This is the system SCN value saved in database.

### V\$DATAFILES

This view displays information about the data files used in tablespaces.

| Column name       | Type         | Description                                                  |
| ----------------- | ------------ | ------------------------------------------------------------ |
| ID                | INTEGER      | The data file identifier                                     |
| NAME              | VARCHAR(256) | Data file name                                               |
| SPACEID           | INTEGER      | The tablespace identifier                                    |
| OLDEST_LSN_LFGID  | INTEGER      | Not used (0)                                                 |
| OLDEST_LSN_FILENO | INTEGER      | See below                                                    |
| OLDEST_LSN_OFFSET | INTEGER      | See below                                                    |
| CREATE_LSN_LFGID  | INTEGER      | Not used (0)                                                 |
| CREATE_LSN_FILENO | INTEGER      | See below                                                    |
| CREATE_LSN_OFFSET | INTEGER      | See below                                                    |
| SM_VERSION        | INTEGER      | Version information                                          |
| NEXTSIZE          | BIGINT       | The size at the next increase                                |
| MAXSIZE           | BIGINT       | The maximum size                                             |
| INITSIZE          | BIGINT       | The initial size                                             |
| CURRSIZE          | BIGINT       | The current size                                             |
| AUTOEXTEND        | INTEGER      | An auto-extension flag                                       |
| IOCOUNT           | INTEGER      | The number of I/O operations currently underway              |
| OPENED            | INTEGER      | Indicates whether or not the file is currently in use        |
| MODIFIED          | INTEGER      | Indicates whether or not the file is currently being modified |
| STATE             | INTEGER      | The status of the file                                       |
| MAX_OPEN_FD_COUNT | INTEGER      | The maximum number of FDs that can be opened                 |
| CUR_OPEN_FD_COUNT | INTEGER      | The number of open FDs                                       |

#### Column Information

##### ID

This is the identifier of the data file. In order to avoid duplicate identifiers, identifiers are assigned sequentially in the order in which data files are created.

##### NAME

This is the physical path and name of the data file.

##### SPACEID

This is the identifier of the tablespace containing the data file.

##### OLDEST_LSN_FILENO

This is the file number portion of the LSN value of the oldest of the pages that were loaded into the buffer and changed at the time of the last checkpoint, when pages in the data file were flushed to disk.

##### OLDEST_LSN_OFFSET

This is the offset value portion of the LSN value of the oldest of the pages that were loaded into the buffer and changed at the time of the last checkpoint, when pages in the data file were flushed to disk.

##### CREATE_LSN_FILENO

This is the file number portion of the LSN that was current at the time at which the data file was created.

##### CREATE_LSN_OFFSET

This is the offset value portion of the LSN that was current at the time at which the data file was created.

##### SM_VERSION

This is the version of the binary from which the data file was created. 

##### NEXTSIZE

If the data file’s autoextend property is set to “on”, this is the size by which the data file will be increased when there is insufficient space. (1 page = 8kB)

##### MAXSIZE

If the data file’s autoextend property is set to “on”, this is the maximum size to which the data file can be increased when there is insufficient space. (1 page = 8kB)

##### INITSIZE

This is the initial size of the data file at the time of its creation
(1 page = 8kB).

##### CURRSIZE

This is the current size of the data file.  (1 page =
8kB).

##### AUTOEXTEND

This indicates whether the size of the data file will be increased automatically when there is insufficient space.

- 0: No automatic increase
- 1: Automatic increase

##### IOCOUNT

This is the number of I/O operations currently underway on the data file. If no data I/O is in progress on the data file, the next data file can be opened.

##### OPENED

This indicates whether the data file is currently open.

- 0: Closed
- 1: Opened

##### MODIFIED

This indicates whether the data file has been modified. If any pages have been flushed to the data file without subsequent synchronization, this value is 1. if synchronization has been executed on the data file since pages were last flushed to it, this value is 0.

##### STATE

This is the status of the data file.

- 1: Offline
- 2: Online
- 6: Backup is in progress
- 128: Dropped

##### MAX_OPEN_FD_COUNT

This is the maximum number of FDs (File Descriptors) that can be opened when performing I/O on the current disk data file.

##### CUR_OPEN_FD_COUNT

This is the number of open FDs (File Descriptors) for the current disk data file. 

### V\$DATATYPE

This table shows information about the data types that are supported by Altibase.<sup>14</sup>

[<sup>14</sup>] The value stored in this performance view is the value retrieved by the ODBCSQLQGettypeInfo () function.

For more detailed information, please refer to the *ODBC* *Reference*.

| Column name        | Type        | Description                                                  |
| ------------------ | ----------- | ------------------------------------------------------------ |
| TYPE_NAME          | VARCHAR(40) | The name of a data type that is supported in the DBMS        |
| DATA_TYPE          | SMALLINT    | An internally defined value indicating a data type that is supported in the DBMS |
| ODBC_DATA_TYPE     | SMALLINT    | The identifier of an ODBC SQL data type corresponding to the data type |
| COLUMN_SIZE        | INTEGER     | The maximum column size for the data type                    |
| LITERAL_PREFIX     | VARCHAR(4)  | Characters recognized as the prefix of the data type literal |
| LITERAL_SUFFIX     | VARCHAR(4)  | Characters recognized as the suffix of the data type literal |
| CREATE_PARAM       | VARCHAR(20) | When using SQL to define a data type, a parameter keyword list enclosed in parentheses |
| NULLABLE           | SMALLINT    | Indicates whether NULL values are allowed for the data type  |
| CASE_SENSITIVE     | SMALLINT    | Indicates whether the data type is case-sensitive            |
| SEARCHABLE         | SMALLINT    | Indicates how the data type is used in a WHERE clause        |
| UNSIGNED_ATTRIBUTE | SMALLINT    | For a numeric data type, indicates whether the data type is a signed data type |
| FIXED_PREC_SCALE   | SMALLINT    | Indicates whether the data type is a fixed type              |
| AUTO_UNIQUE_VALUE  | SMALLINT    | Reserved for future use                                      |
| LOCAL_TYPE_NAME    | VARCHAR(40) | The name of the data type in the local language              |
| MINIMUM_SCALE      | SMALLINT    | The minimum allowable number of digits to the right of the decimal point |
| MAXIMUM_SCALE      | SMALLINT    | The maximum allowable number of digits to the right of the decimal point |
| SQL_DATA_TYPE      | SMALLINT    | A defined value of a SQL data type that is provided by SQL_DESC_TYPE in ODBC |
| SQL_DATETIME_SUB   | SMALLINT    | A type subcode for a datetime or interval data type          |
| NUM_PREC_RADIX     | INTEGER     | The number of bits that are needed to perform operations on the maximum number of digits that a column can hold |
| INTERVAL_PRECISION | SMALLINT    | When the DATA_TYPE is interval, the maximum number of digits needed to express the data |

#### Column Information

##### ODBC_DATA_TYPE

This is the data type identifier for the ODBC SQL data type corresponding to the data type. For more information, please refer to the appendix pertaining to data types in the *ODBC Reference*. 

##### COLUMN_SIZE

This is the maximum column size for the data type. 

For numeric data types, this is the precision value, which was specified when the type was defined. For string data types, this is the length value, which was specified when the type was defined. For datetime data types, this is the total number of characters that are needed to display a value when it is converted to characters. 

##### LITERAL_PREFIX

This specifies the characters that signify the prefix of a literal for the data type. For data types to which literal prefixes do not apply, it is NULL.

##### LITERAL_SUFFIX

This specifies the characters that signify the suffix of a literal for the data type. For data types to which literal suffixes do not apply, it is NULL.

##### CREATE_PARAM

When using SQL to define a data type, this is a comma-separated list of parameter keywords enclosed in parentheses. For example, to express a NUMBER as NUMBER(precision,scale), the content within the parentheses, that is, “precision, scale”, is the list. ”Precision” and “scale” are thus both keywords in the list. For data types that do not need parameters, this is set to NULL. 

##### NULLABLE

This indicates whether NULL values are allowed for a data type. 

- 1: NULL is allowed.
- 0: NULL is not allowed. 

##### CASE_SENSITIVE

For character data types, indicates whether to distinguish between uppercase and lowercase letters when sorting data of the data type. 

- 1: Case-sensitive. 
- 0: Not case-sensitive.

##### SEARCHABLE

Indicates how a data type can be used in a WHERE clause.

- 0: It cannot be used in a WHERE clause (SQL_PRED_NONE). 
- 1: It can be used in a WHERE clause, but must be used with LIKE (SQL_PRED_CHAR). 
- 2: It can be used in a WHERE clause with any comparison operator except LIKE (SQL_PRED_BASIC). 
- 3: It can be used in a WHERE clause with any comparison operator (SQL_SEARCHABLE).

##### UNSIGNED_ATTRIBUTE

Indicates whether a data type is signed.

- 1: The data type is an unsigned data type.
- 0: The data type is a signed data type.
- NULL: The data type is not numeric, therefore this attribute is not applicable.

##### FIXED_PREC_SCALE

Indicates whether a data type is fixed. If a data type is a fixed numeric type and always has the same precision and scale, this value is 1 (SQL_TRUE). Otherwise, it is 0 (SQL_FALSE). 

##### LOCAL_TYPE_NAME

Indicates a localized (region-specific) name for a data type. If there is no localized name, this value is NULL. 

##### MINIMUM_SCALE

For numeric data types, this is the minimum allowable number of digits to the right of the decimal. This value exists for fixed scale types; it is set to NULL for types to which scale does not pertain

##### MAXIMUM_SCALE

For numeric data types, this is the maximum allowable number of digits to the right of the decimal. It is specified when the data type is defined. It is set to NULL for types to which scale does not pertain. 

##### SQL_DATA_TYPE

This is a SQL data type that is provided by SQL_DESC_TYPE in ODBC. For data types other than INTERVAL or DATETIME, this value is the same as that of ODBC_DATA_TYPE. 

##### SQL_DATETIME_SUB

If the SQL_DATA_TYPE value is SQL_DATETIME or SQL_INTERVAL, this is the type sub code for the DATETIME or INTERVAL data type. If the data type is not DATETIME or INTERVAL, it is set to NULL.

##### NUM_PREC_RADIX

This is the number of bits or digits that are needed to perform mathematical operations on the highest number that a column can hold

##### INTERVAL_PRECISION

This is the maximum number of digits that a DATA_TYPE of type INTERVAL can hold. 

### V\$DBA_2PC_PENDING

This view shows a list of XIDs (transaction IDs) for distributed transactions that exist in the DBMS and whose status is in doubt. The status of a distributed transaction is said to be "in-doubt" when a branch thereof is ready to be committed, but has not yet been committed or rolled back.

| Column name   | Type         | Description                                                  |
| ------------- | ------------ | ------------------------------------------------------------ |
| LOCAL_TRAN_ID | BIGINT       | An internal Altibase transaction identifier that is associated with the GLOBAL_TX_ID |
| GLOBAL_TX_ID  | VARCHAR(256) | Globally unique transaction identifier                       |

#### Column Information

##### LOCAL_TRAN_ID

This is an internal Altibase transaction identifier that is associated with a global transaction identifier.

##### GLOBAL_TX_ID

This is the globally unique transaction identifier. The GLOBAL_TX_ID contains a format identifier, two length fields and a data field. The data field consists of at most two contiguous components: a global transaction identifier and a branch qualifier.

### V\$DBLINK_ALTILINKER_STATUS 

This view shows status information about the AltiLinker process for the database link.

| Column name              | Type         | Description                                                  |
| ------------------------ | ------------ | ------------------------------------------------------------ |
| STATUS                   | INTEGER      | Status of the AltiLinker process 1: AltiLinker is in a normal state 0: AltiLinker is in an abnormal state, or is not available |
| SESSION_COUNT            | INTEGER      | The number of linker sessions, the sessions between Altibase and the Altilinker process. |
| REMOTE_SESSION_COUNT     | INTEGER      | The number of sessions between the Altilinker process and the remote servers |
| JVM_MEMORY_POOL_MAX_SIZE | INTEGER      | The maximum size of the memory pool allocated for the AltiLinker on the JVM |
| JVM_MEMORY_USAGE         | BIGINT       | The amount of memory used for the AltiLinker process on the JVM |
| START_TIME               | VARCHAR(128) | The date and time at which the Altilinker process started    |

#### Column Information

##### STATUS

This is the status of the Altilinker. A value of 1 indicates that the Altilinker is in a normal state, while a value of 0 indicates that the Altilinker is in an abnormal state, or is not available.

### V\$DBLINK_DATABASE_LINK_INFO

This view displays information about the database link object existing in the database.

| Column name     | Type    | Description                                          |
| --------------- | ------- | ---------------------------------------------------- |
| ID              | INTEGER | The database link object identifier                  |
| STATUS          | INTEGER | The status of the database link object               |
| REFERENCE_COUNT | INTEGER | The number of references of the database link object |

#### Column Information

##### STATUS

Displays the status of the database link object.

- 1(CREATED): Creation of the database link object is complete. 
- 2(META): Registration of the database link object information in the meta table. 
- 3(READY): The database link object is ready for use.

##### REFERENCE_COUNT

Displays the number of times the database link is currently being referenced.

### V\$DBLINK_GLOBAL_TRANSACTION_INFO 

This view displays information about global transactions being executed through the current database link.

| Column name              | Type    | Description                                                  |
| ------------------------ | ------- | ------------------------------------------------------------ |
| TRANSACTION_ID           | INTEGER | The identifier of the global transaction that is currently using the database link |
| STATUS                   | INTEGER | The current status of the global transaction                 |
| SESSION_ID               | INTEGER | The ID of the Linker Data Session executing the global transaction |
| REMOTE_TRANSACTION_COUNT | INTEGER | The number of remote transactions currently being executed within the global transaction |
| TRANSACTION_LEVEL        | INTEGER | The execution level of the global transaction                |
| GLOBAL_TRANSACTION_ID    | INTEGER | The global transaction identifier using the database link    |

#### Column Information

##### STATUS

Displays the current state of the global transaction.

- 0(NONE): No transaction exists.
- 1(BEGIN): The global transaction has started.
- 2(PREPARE_READY): The global tranaction has started, however, no remote transaction under execution exists.
- 3(PREPARE_REQUEST): The AltiLinker process has been requested to PREPARE at the Simple Transaction Commit level.
- 4(PREPARE_WAIT): The global transaction is waiting for all remote transactions to complete PREPARE at the Simple Transaction Commit level.
- 5(PREPARED): All remote transactions have completed PREPARE.
- 6(COMMIT_REQUEST): COMMIT has been requested via the AltiLinker process
- 7(COMMIT_WAIT): Waiting for a response on COMMIT from the AltiLinker process.
- 8(COMMITTED): The global transaction is committed
- 9(ROLLBACK_REQUEST):  ROLLBACK has been requested to the AltiLinker process.
- 10(ROLLBACK_WAIT): AWaiting for a response on ROLLBACK from the AltiLinker process.
- 11(ROLLBACKED): The global transaction is rolled back.

##### TRANSACTION_LEVEL

Displayed as 0, 1, or 2. For further information about each value, please refer to the DBLINK_GLOBAL_TRANSACTION_LEVEL property.

### V\$DBLINK_LINKER_CONTROL_SESSION_INFO

This view displays status information about the Linker Control Session which is singularly created for the control operations between the Altibase server and the AltiLinker process.

| Column name     | Type    | Description                                                  |
| --------------- | ------- | ------------------------------------------------------------ |
| STATUS          | INTEGER | The status of the Linker Control Session                     |
| REFERENCE_COUNT | INTEGER | The number of times the Linker Control Session is currently being referenced |

#### Column Information

##### STATUS

Displays the current status of the Linker Control Session.

- 0(NONE): No Linker Control Session exists. 
- 1(CREATED): Creation of a Linker Control Session is complete.
- 2(CONNECTED): The AltiLinker process and the Linker Control Session are connected. 
- 3(DISCONNECTED): The AltiLinker process and the Linker Control Session are disconnected.
- 5(LOCKED): The Linker Control Session is locked.
- 6(UNLOCKED): The Linker Control Session is unlocked.

### V\$DBLINK_LINKER_DATA_SESSION_INFO

This view displays the status information about Linker Data Sessions created for the execution of data operations between the Altibase server and the AltiLinker process

| Column name           | Type    | Description                                                  |
| --------------------- | ------- | ------------------------------------------------------------ |
| ID                    | INTEGER | The Linker Data Session identifier                           |
| STATUS                | INTEGER | The status of the Linker Data Session                        |
| LOCAL_TRANSACTION_ID  | INTEGER | The local transaction identifier executing in the current session |
| GLOBAL_TRANSACTION_ID | INTEGER | The global transaction identifier executing in the current session |

#### Column Information

##### STATUS

Displays the current status of the Linker Data Session.

- 0(NONE): No Linker Data Session exists. 
- 1(CREATED): Creation of the Linker Data Session is complete. 
- 2(CONNECTED): The Linker Data Session and the AltiLinker process are connected. 
- 3(DISCONNECTED): The Linker Data Session and the AltiLinker process are disconnected. 
- 4(DESTROYED): The Linker Data Session has been removed.
- 5(LOCKED): The Linker Control Session has been locked
- 6(UNLOCKED): The Linker Control Session is unlocked.

### V\$DBLINK_LINKER_SESSION_INFO

This view displays how many Linker Control Sessions and Linker Data Sessions exist between the Altibase server and the AltiLinker process.

| Column name  | Type       | Description                                                  |
| ------------ | ---------- | ------------------------------------------------------------ |
| SESSION_ID   | INTEGER    | The linker session identifier                                |
| STATUS       | INTEGER    | The status of the linker session                             |
| SESSION_TYPE | VARCHAR(7) | Indicates whether it is a Linker Control Session or a Linker Data Session |

#### Column Information

##### STATUS

Indicates the current status of the Linker Session. For the status value, please refer to the STATUS of the performance views, V\$DBLINK_LINKER_CONTROL_SESSION_INFO and V$DBLINK_LINKER_DATA_SESSION_INFO. 

##### SESSION_TYPE

Indicates whether the linker session is a Linker Control Session or a Linker Data Session.

- CONTROL: Linker Control Session
- DATA: Linker Data Session

### V\$DBLINK_NOTIFIER_TRANSACTION_INFO

This view displays information on hte distributed transaction AltiLinker is processing.

| Column name           | Type        | Description                                                  |
| --------------------- | ----------- | ------------------------------------------------------------ |
| GLOBAL_TRANSACTION_ID | INTEGER     | The transaction identifier using the database link.          |
| TRANSACTION_ID        | INTEGER     | The local transaction identifier                             |
| XID                   | VARCHAR(12) | The transaction branch identifier                            |
| TRANSACTION_RESULT    | VARCHAR(10) | The result of transaction process(COMMIT/ROLLBACK).          |
| TARGET_INFO           | VARCHAR(40) | The name of remote server that an object of the database link will be accessing. |

#### Column Information

##### GLOBAL_TRANSACTION_ID

This is the identifier of the global transaction which uses the database link.

##### TRANSACTION_ID

This is the inner transaction identifier when Altibase performs the local transaction in case of processing the global transaction.

##### XID

This is the transaction ID allocated to the transaction branch. The value displays the format identifier, global transaction identifier, or branch qualifier

##### TRANSACTION_RESULT

This information indicates the result of a processed transaction.

- COMMIT: The transaction is processed by COMMIT. 
- ROLLBACK: P The transaction is processed by ROLLBACK.TARGET_INFO

This shows the name of the remote server that the database link object will access.

### V\$DBLINK_REMOTE_STATEMENT_INFO

This view displays information about information of the query occurred in the remote server when using the database link.

| Column name           | Type           | Description                                                  |
| --------------------- | -------------- | ------------------------------------------------------------ |
| TRANSACTION_ID        | INTEGER        | The transaction identifier of using the database link.       |
| REMOTE_TRANSACTION_ID | INTEGER        | The transaction identifier occurred in the remote server.    |
| STATEMENT_ID          | BIGINT         | The statement identifier occurred in the remote server.      |
| QUERY                 | VARCHAR(32000) | The query contents executed in the statement.                |
| GLOBAL_TRANSACTION_ID | INTEGER        | The global transaction identifier which is using the database link. |

#### Column Information

##### REMOTE_TRANSACTION_ID

This is the identifier of the transaction which occurred on the remote server. This identifier is not the transaction identifier which was actually created on the remote server, but is an identifier autonomously granted by AltiLinker while executing a transaction through a remote server. Since this identifier is created for managemenet purposes, the value is of little significance.

##### STATEMENT_ID

This is the statement identifier that occurred on the remote server. This identifier is not a statement identifier actually generated at the remote server, but an identifier that AltiLinker assigns itself when generating a sentence at the remote server.

### V\$DBLINK_REMOTE_TRANSACTION_INFO

This view displays information about all remote transactions being executed on the remote node through the database link.

| Column name           | Type        | Description                                                  |
| --------------------- | ----------- | ------------------------------------------------------------ |
| TRANSACTION_ID        | INTEGER     | The identifier of the transaction which is using the database link |
| REMOTE_TRANSACTION_ID | INTEGER     | The identifier of the transaction which occurred on the remote server |
| TARGET_INFO           | VARCHAR(40) | The remote server name                                       |
| STATUS                | INTEGER     | The current status of the global transaction                 |
| XID                   | VARCHAR(12) | The identifier of the transaction branch                     |
| GLOBAL_TRANSACTION_ID | INTEGER     | The global transaction identifier which is using the database link. |

#### Column Information

##### REMOTE_TRANSACTION_ID

This is the identifier of the transaction which occurred on the remote server. This identifier is not the transaction identifier which was actually created on the remote server, but is an identifier autonomously granted by AltiLinker while executing a transaction through a remote server. Since this identifier is created for management purposes, the value is of little significance.

##### STATUS

Displays the current status of the global transaction.

- 0(NONE): No transaction exists
- 1(BEGIN): A transaction has started.
- 2(PREPARE_READY): A transaction has started, however, no remote transaction under execution exists.
- 3(PREPARE_WAIT): The global transaction is waiting for a response on PREPARE from the AltiLinker process at the Simple Transaction Commit Level.
- 4(PREPARED): PREPARE is complete.
- 5(COMMIT_WAIT): Waiting for a response on COMMIT from the AltiLinker process.
- 6(COMMITTED): The global transaction is committed.
- 7(ROLLBACK_WAIT): Waiting for a response on ROLLBACK from the AltiLinker process.
- 8(ROLLBACKED): The global transaction is rolled back.

### V\$DBMS_STATS

This view displays statistical information about the whole database.

| Column name       | Type     | Description                                                  |
| ----------------- | -------- | ------------------------------------------------------------ |
| DATE              | CHAR(48) | The time at which statistical information was collected for the last time |
| SAMPLE_SIZE       | DOUBLE   | The sample size                                              |
| NUM_ROW_CHANGE    | BIGINT   | The change in the number of rows after statistical information was collected for the last time |
| TYPE              | CHAR(1)  | The type of the statistics target: S: System T: Table I: Index C: Column |
| SREAD_TIME        | DOUBLE   | The amount of time spent on reading one page                 |
| MREAD_TIME        | DOUBLE   | The amount of time spent on reading multiple pages at a time |
| MREAD_PAGE_COUNT  | BIGINT   | The number of pages read when multiple pages are read at a time |
| HASH_TIME         | DOUBLE   | The average execution time for hashing                       |
| COMPARE_TIME      | DOUBLE   | The average execution time for comparing                     |
| STORE_TIME        | DOUBLE   | The average execution time for storing memory temporary tables |
| TARGET_ID         | BIGINT   | The OID of the statistics target table or the ID of the statistics target index |
| COLUMN_ID         | INTEGER  | The ID of the statistics target column                       |
| NUM_ROW           | BIGINT   | The number of rows                                           |
| NUM_PAGE          | BIGINT   | The number of pages                                          |
| NUM_DIST          | BIGINT   | The number of distinct rows                                  |
| NUM_NULL          | BIGINT   | The number of NULLs                                          |
| AVG_LEN           | BIGINT   | The average length of rows or column data                    |
| ONE_ROW_READ_TIME | DOUBLE   | The average time spent on reading one row                    |
| AVG_SLOT_COUNT    | BIGINT   | The average number of slots per leaf node                    |
| INDEX_HEIGHT      | BIGINT   | The depth from the root node to the leaf node in the index   |
| CLUSTERING_FACTOR | BIGINT   | The degree to which data is sorted according to the index    |
| MIN               | CHAR(48) | The minimum value                                            |
| MAX               | CHAR(48) | The maximum value                                            |
| META_SPACE        | BIGINT   | The amount of space used for data management                 |
| USED_SPACE        | BIGINT   | The amount of space used for data storage                    |
| AGEABLE_SPACE     | BIGINT   | The amount of space available for reuse due to aging in the future |
| FREE_SPACE        | BIGINT   | The amount of space available for use                        |

#### Column Information

##### DATE

This is the time at which statistical information was collected for the last time.

##### SAMPLE_SIZE

This is the sample size chosen for the collection of statistical information.

##### NUM_ROW_CHANGE

This is the change in the number of rows after statistical information was collected for the last time.

##### TYPE

This is the type of statistics target for collection, and takes one of the following values:

S: System

T: Table

I: Index

C: Column

##### SREAD_TIME

This is the average time spent on reading one page.

##### MREAD_TIME

This is the average time spent on reading multiple pages at a time.

##### MREAD_PAGE_COUNT

This is the number of pages specified to be read for reading multiple pages at a time.

##### HASH_TIME

This is the average execution time spent on hashing.

##### COMPARE_TIME

This is the average execution time spent on comparing.

##### STORE_TIME

This is the average time spent on storing to a memory temporary table.

##### TARGET_ID

This is the OID of the statistics target table for collection or the ID of the statistics target index for collection.

##### COLUMN_ID

This is the statistics target column ID for collection.

##### NUM_ROW

This is the number of rows of the statistics target for collection (a tables or an index).

##### NUM_PAGE

This is the number of pages of the statistics target for collection (a table or an index).

##### NUM_DIST

This is the number of distinct values of the index or the column.

##### NUM_NULL

This is the number of NULL values of the column.

##### AVG_LEN

This is the average length of row data, if the statistics target for collection is a table. This is the average length of column data, if the statistics target for collection is a column.

##### ONE_ROW_READ_TIME

This is the average time spent on reading one row.

##### AVG_SLOT_COUNT

This is the average number of slots per leaf node.

##### INDEX_HEIGHT

This is the depth from the root node to the lead node in the index.

##### CLUSTERING_FACTOR

This is the degree to which data is sorted according to the index.

##### MIN

This is the minimum value of the index or the column.

##### MAX

This is the maximum value of the index or the column.

##### META_SPACE

This is the amount of space used for data management.

##### USED_SPACE

This is the amount of space used for data storage.

##### AGEABLE_SPACE

This is the amount of space available for reuse due to aging in the future.

##### FREE_SPACE

This is the amount of space available for use among the space allocated to the table or the index.

### V\$DB_FREEPAGELISTS

This view displays information about lists of pages that can be used, that is, free pages, in a database.

| Column name        | Type    | Description                                                  |
| ------------------ | ------- | ------------------------------------------------------------ |
| SPACE_ID           | INTEGER | The identifier of the tablespace to which the free pages belong |
| RESOURCE_GROUP_ID  | INTEGER | The identifier of the resource group                         |
| FIRST_FREE_PAGE_ID | INTEGER | The identifier of the first free page in the list            |
| FREE_PAGE_COUNT    | BIGINT  | The total number of free pages in the list                   |

#### Column Information

##### RESOURCE_GROUP_ID

This is a unique number that is used to identify the list.

##### FIRST_FREE_PAGE_ID

This is the identifier of the first free page in the list.

##### FREE_PAGE_COUNT

This is the number of free pages on the list.

### V\$DB_PROTOCOL

This view shows information about Altibase communication protocols of all incoming packets.

| Column name | Type        | Description                                                 |
| ----------- | ----------- | ----------------------------------------------------------- |
| OP_NAME     | VARCHAR(50) | The protocol name                                           |
| OP_ID       | INTEGER     | The unique identifier of the protocol                       |
| COUNT       | BIGINT      | The cumulative number of incoming packets for this protocol |

### V\$DIRECT_PATH_INSERT

This view displays historical statistics on direct-path uploads.

| Column name                  | Type   | Description                                                  |
| ---------------------------- | ------ | ------------------------------------------------------------ |
| COMMIT_TX_COUNT              | BIGINT | The total number of transactions that were successfully committed using the direct-path option |
| ABORT_TX_COUNT               | BIGINT | The total number of transactions that were rolled back while data were being uploaded using the direct-path option |
| INSERT_ROW_COUNT             | BIGINT | The total number of rows that were inserted by iLoader using the direct-path option |
| ALLOC_BUFFER_PAGE_TRY_COUNT  | BIGINT | The total number of times that page allocation was requested |
| ALLOC_BUFFER_PAGE_FAIL_COUNT | BIGINT | The total number of times that a page allocation request failed |

#### Column Information

##### COMMIT_TX_COUNT

This is the total number of transactions which were committed by iLoader using the direct-path option, accumulated over past executions.

##### ABORT_TX_COUNT

This is the total number of transactions which were rolled back due to errors while data were being uploaded using the direct-path option, accumulated over past executions.

##### INSERT_ROW_COUNT

This is the total number of rows which were inserted by iLoader using the direct-path option, accumulated over past executions.

##### ALLOC_BUFFER_PAGE_TRY_COUNT

This is the total number of times that page allocation was requested for uploading data using the direct-path option, accumulated over past executions.

##### ALLOC_BUFFER_PAGE_FAIL_COUNT

This is the total number of times that a page allocation request for uploading data using the direct-path option failed due to insufficient memory, accumulated over past executions.

### V\$DISKTBL_INFO

The view displays information about disk tables.

| Column name         | Type     | Description                                                  |
| ------------------- | -------- | ------------------------------------------------------------ |
| TABLESPACE_ID       | SMALLINT | The tablespace identifier                                    |
| TABLE_OID           | BIGINT   | The table object identifier                                  |
| DISK_TOTAL_PAGE_CNT | BIGINT   | The total number of pages in a table                         |
| DISK_PAGE_CNT       | BIGINT   | The number of pages containing data in a table               |
| SEG_PID             | INTEGER  | The page identifier of a segment of a table                  |
| META_PAGE           | INTEGER  | This column has been deprecated                              |
| FST_EXTRID          | BIGINT   | The RID of the first extent in a table                       |
| LST_EXTRID          | BIGINT   | The RID of the last extent in a table                        |
| PCTFREE             | SMALLINT | See SYS_TABLES_                                              |
| PCTUSED             | SMALLINT | See SYS_TABLES_                                              |
| INITRANS            | SMALLINT | The initial number of transactions that can be simultaneously processed in one page |
| MAXTRANS            | SMALLINT | The maximum number of transactions that can be simultaneously processed in one page |
| INITEXTENTS         | INTEGER  | The initial number of extents when a table is created        |
| NEXTEXTENTS         | INTEGER  | The number of extents that can be allocated when a table is expanded |
| MINEXTENTS          | INTEGER  | The minimum number of extents in a table                     |
| MAXEXTENTS          | INTEGER  | The maximum number of extents in a table                     |
| COMPRESSED_LOGGING  | INTEGER  | Whether to compress a log for a table                        |
| IS_CONSISTENT       | INTEGER  | Whether an index is consistent                               |

To display a view together with the name of the table on which it is based, use a query to join the performance view with a meta table as follows:

```
SELECT A.TABLE_NAME,
	B.DISK_PAGE_CNT,
	B.PCTFREE,
 	B.PCTUSED
FROM SYSTEM_.SYS_TABLES_ A, V$DISKTBL_INFO B 
WHERE A.TABLE_OID = B.TABLE_OID;
```

#### Column Information

##### PCTFREE

Please refer to the description of the corresponding column in the SYS_TABLES_ description.

##### PCTUSED

Please refer to the description of the corresponding column in the SYS_TABLES_ description.

##### INITRANS

This is the initial number of transactions that can be processed simultaneously in one table page. 

##### MAXTRANS

This is the maximum number of transactions that can be processed simultaneously in one table page.

##### INITEXTENTS

This is the initial number of extents when a table segment is created.

##### NEXTEXTENTS

This is the number of additional extents that will be allocated when the size of a table segment is increased.

##### MINEXTENTS

This is the minimum number of extents in a table segment. 

##### MAXEXTENTS

This is the maximum number of extents in a table segment. 

### V\$DISK_BTREE_HEADER

This view displays information about the header of a disk BTREE index.

| Column name                | Type      | Description                                                  |
| -------------------------- | --------- | ------------------------------------------------------------ |
| INDEX_NAME                 | CHAR(128) | The index name                                               |
| INDEX_ID                   | INTEGER   | The index identifier                                         |
| INDEX_TBS_ID               | INTEGER   | The tablespace in which the index is saved                   |
| TABLE_TBS_ID               | INTEGER   | The tablespace in which the table is saved                   |
| IS_UNIQUE                  | CHAR(1)   | Whether an index is a unique key index                       |
| COLLENINFO_LIST            | CHAR(64)  | A list of the sizes of the values in the index               |
| IS_CONSISTENT              | CHAR(1)   | Whether an index is consistent                               |
| IS_CREATED_WITH_LOGGING    | CHAR(1)   | Whether the LOGGING option was specified at the time the index was created |
| IS_CREATED_WITH_FORCE      | CHAR(1)   | Whether the NOLOGGING FORCE or NOLOGGING NOFORCE option was specified at the time the index was created |
| COMPLETION_LSN_LFG_ID      | INTEGER   | The log group identifier when the index was created          |
| COMPLETION_LSN_FILE_NO     | INTEGER   | The log file number when the index was created               |
| COMPLETION_LSN_FILE_OFFSET | INTEGER   | The log file offset when the index was created               |
| INIT_TRANS                 | SMALLINT  | The initial number of transactions that can be simultaneously processed in a single index node |
| MAX_TRANS                  | SMALLINT  | The maximum number of transactions that can be simultaneously processed in a single index node |
| FREE_NODE_HEAD             | INTEGER   | The ID of the first page in a free node                      |
| FREE_NODE_CNT              | BIGINT    | The number of pages in a free node list                      |
| INITEXTENTS                | INTEGER   | The initial number of extents when the index was created.    |
| NEXTEXTENTS                | INTEGER   | The number of extents to be allocated when the index is increased in size |
| MINEXTENTS                 | INTEGER   | The minimum number of extents in the index segment           |
| MAXEXTENTS                 | INTEGER   | The maximum number of extents in the index segment           |

#### Column Information

##### INDEX_NAME

This is the name of the index.

##### INDEX_ID

This displays the identifier, unique in the system, of the index. 

##### INDEX_TBS_ID

This is the identifier of the tablespace in which the index is saved. 

##### TABLE_TBS_ID

This is the identifier of the tablespace containing the table that is connected to the corresponding index.

##### IS_UNIQUE

This indicates whether the index is a unique key index. It is set to ‘T’ for a unique key index, and to ‘F’ for a duplicate key index.

* T: Unique key index
* F: Duplicate key index

##### COLLENINFO_LIST

This is a list of the sizes of the values in the index. The list is expressed as a comma-delimited string. The size of a variable length column is expressed as ‘?’. The size of a key can be inferred based on this list.

```
iSQL> CREATE TABLE D3(I1 SMALLINT, I2 INTEGER, I3 VARCHAR(10), I4 DATE) TABLESPACE SYS_TBS_DISK_DATA;
Create success.
iSQL> CREATE INDEX D3X ON D3(I4,I3,I2,I1);
Create success.
iSQL> SELECT COLLENINFO_LIST FROM V$DISK_BTREE_HEADER WHERE INDEX_NAME='D3X';
COLLENINFO_LIST
--------------------------------------------------------------------
8,?,4,2
1 row selected.
```

##### IS_CONSISTENT

This indicates whether the index is consistent. It is usually set to ‘T’. It may be set to ‘F' when an index is created with NOLOGGING or NOFORCE.

* T: Normal
* F: Abnormal

##### IS_CREATED_WITH_LOGGING

This indicates whether the LOGGING option was specified at the time that the index was created.

##### IS_CREATED_WITH_FORCE

This value indicates whether the NOLOGGING FORCE or NOLOGGING NOFORCE option was specified at the time that the index was created.

##### COMPLETION_LSN_FILE_NO

This is the log file number that was current at the time that the index was created.

##### COMPLETION_LSN_FILE_OFFSET

This is the log file offset that was current at the time that the index was created.

##### INIT_TRANS

This is the initial number of transactions that can simultaneously access a single index node (page) for an INSERT, UPDATE or DELETE operation.

##### MAX_TRANS

This is the maximum number of transactions that can simultaneously access a single index node (page) for an INSERT, UPDATE or DELETE operation.

##### FREE_NODE_HEAD

A FREE_NODE_HEAD shows the first page of a free node list within an index, a FREE NODE being a node in which a delete mark has been set for all keys therein. 

##### FREE_NODE_CNT

This is the total number of FREE NODEs in an index. 

##### INITEXTENTS

This is the initial number of extents, which is specified at the time that an index segment is created. 

##### NEXTEXTENTS

This is the number of extents to be allocated when the size of an index segment is increased. 

##### MINEXTENTS

This is the minimum number of extents in an index segment. 

##### MAXEXTENTS

This is the maximum number of extents in an index segment. 

### V\$DISK_TEMP_INFO

This performance view shows the usage information of the entire disk temporary table.

| Column name | Type     | Description                       |
| ----------- | -------- | --------------------------------- |
| NAME        | CHAR(32) | The minimum value name for memory |
| VALUE       | CHAR(32) | The memory minimum value          |
| UNIT        | CHAR(32) | The unit                          |

#### Column Information

##### VALUE

Indicates the minimum amount of memory required to sort memory required to sort disk temporary tables in memory since the server was started.

### V\$DISK_TEMP_STAT

This view indicates the current memory usage of each disk temporary table. The statistics is collected if the value set is greater than the value specified in TEMP_STATS_WATCH_TIME property.

| Column name      | Type    | Description                                                 |
| ---------------- | ------- | ----------------------------------------------------------- |
| TBS_ID           | INTEGER | The identifier of the tablespace                            |
| TRANSACTION_ID   | INTEGER | The transaction identifier                                  |
| CONSUME_TIME     | INTEGER | The execution time of disk temporary table                  |
| READ_COUNT       | BIGINT  | The number of IOs that reads data                           |
| WRITE_COUNT      | BIGINT  | The number of IOs that stores data.                         |
| WRITE_PAGE_COUNT | BIGINT  | The total number of pages stored to disk                    |
| ALLOC_WAIT_COUNT | BIGINT  | The total number of times waiting to allocate memory space. |
| WRITE_WAIT_COUNT | BIGINT  | The total number of times waiting to store to disk.         |
| QUEUE_WAIT_COUNT | BIGINT  | The number of times to wait for a queue entry.              |
| WORK_AREA_SIZE   | BIGINT  | The memory size that disk temporary tables use.             |
| DISK_USAGE       | BIGINT  | The size of data space stored in disk.                      |

#### Column Information

##### TBS_ID

This is the identifier of tablespace using disk temporary tables.

##### TRANSACTION_ID

This is the identifier of a transaction using disk temporary tables.

##### CONSUME_TIME

This shows the execution time if the execution time of a disk temporary table exceeds the time specified in TEMP_STATS_WATCH_TIME property.

##### READ_COUNT

This is the number of READ IO occurrences in order to read data on disk.

##### WRITE_COUNT

This is the number of WRITE IO occurrences in order to store data on disk.

##### WRITE_PAGE_COUNT

This is the total number of pages that disk temporary tables are stored into disk.

##### ALLOC_WAIT_COUNT

This is the number of times waiting to allocate memory space for hash sorting.

##### WRITE_WAIT_COUNT

This is the number of times waiting to store data on disk.

##### QUEUE_WAIT_COUNT

This is the number of times waiting to be queued to store data on disk.

##### WORK_AREA_SIZE

This is the space used for hash sorting in memory.

##### DISK_USAGE

This is the size of space that the disk temporary tables are stored to disk.

### V\$DISK_UNDO_USAGE

This view displays the amount of undo tablespace on disk that is currently being used.

| Column name         | Type   | Description                                                  |
| ------------------- | ------ | ------------------------------------------------------------ |
| TX_EXT_CNT          | BIGINT | The number of extents in all transaction segments            |
| USED_EXT_CNT        | BIGINT | The number of extents currently being used in undo segments  |
| UNSTEALABLE_EXT_CNT | BIGINT | The number of extents that cannot be stolen by other undo segments (when a segment does not have enough extents, it can take extents from other undo segments) |
| REUSABLE_EXT_CNT    | BIGINT | The number of extents that can be reused                     |
| TOTAL_EXT_CNT       | BIGINT | The total number of extents in the undo tablespace           |

#### Column Information

##### TX_EXT_CNT

This is the number of extents in all transaction segments. These extents cannot be used in undo segments.

##### USED_EXT_CNT

This is the number of extents currently used in undo segments. Because these extents are currently being used, they cannot be reused by subseqent tasks.

##### REUSABLE_EXT_CNT

This is the number of extents that can be reused because they contain undo records that are no longer necessary

### V\$DR_CONNECTION_INFO

This view displays information about the servers currently deployed in the DR environment.

| Column name | Type        | Description                                      |
| ----------- | ----------- | ------------------------------------------------ |
| SERVER_NAME | VARCHAR(40) | The server name                                  |
| SERVER_IP   | VARCHAR(64) | The server IP address                            |
| SERVER_PORT | INTEGER     | The listening port number of the server listener |

#### Column Information

##### SERVER_NAME

This is the name given to the server deployed in the DR environment.

##### SERVER_IP

This is the IP address of the server deployed in the DR environment.

##### SERVER_PORT

This is the listening port number of the server listener.

### V\$DR_GAP

This view displays information about the synchronization delays between servers currently deployed in the DR environment.

| Column name  | Type        | Description                                                  |
| ------------ | ----------- | ------------------------------------------------------------ |
| SERVER_NAME  | VARCHAR(40) | The server name                                              |
| CURRENT_SN   | BIGINT      | Active server: The serial number(SN) of the log record currently being transmitted. <br/>Standby server: The serial number(SN) of the log record currently being applied. |
| SYNCED_SN    | BIGINT      | Active server: Always 0. A meaningless value. <br/>Standby server: The serial number of the log record most recently received by the standby server. |
| SN_GAP       | BIGINT      | Active server: Always 0. A meaningless value. <br/>Standby server: The gap between CURRENT_SN of the corresponding active server and SYNCED_SN of the standby server. |
| APPLY_SN_GAP | BIGINT      | Active server: Always 0. A meaningless value. <br/>Standby server: The gap between CURRENT_SN and SYNCED_SN. |

#### Column Information

##### SERVER_NAME

This is the name given to the server deployed in the DR environment.

##### CURRENT_SN

On the active server, the serial number(SN) of the log record currently being transmitted is displayed. 

On the standby server, the serial number(SN) of the log record currently being applied to the database is displayed

##### SYNCED_SN

On the active server, 0 is always displayed. 

On the standby server, the serial number(SN) of the most recently recieved log record is displayed

##### SN_GAP

On the active server, 0 is always displayed. 

On the standby server, the gap between CURRENT_SN of the corresponding active server and SYNCED_SN of the standby server is displayed.

##### APPLY_SN_GAP

On the active server, 0 is always displayed. 

On the standbyserver, the gap between CURRENT_SN and SYNCED_SN is displayed.

### V\$DR_SERVERS

This view displays information about the servers configured for the DR environment.

| Column name | Type        | Description                                      |
| ----------- | ----------- | ------------------------------------------------ |
| SERVER_NAME | VARCHAR(40) | The server name                                  |
| SERVER_IP   | VARCHAR(64) | The server IP address                            |
| SERVER_PORT | INTEGER     | The listening port number of the server listener |

#### Column Information

##### SERVER_NAME

This is the name given to the server deployed in the DR environment.

##### SERVER_IP

This is the IP address of the server configured for the DR environment.

##### SERVER_PORT

This is the listening port number of the server listener.

### V\$DR_STATUS

This view displays information of the current status of the servers deployed in the DR environment.

| Column name    | Type        | Description                              |
| -------------- | ----------- | ---------------------------------------- |
| SERVER_NAME    | VARCHAR(40) | The server name                          |
| CURRENT_MODE   | VARCHAR(7)  | The synchronization mode                 |
| SERVER_ROLE    | VARCHAR(7)  | The server role                          |
| SERVER_MODE    | VARCHAR(7)  | The synchronization mode set by the user |
| SERVER_STATUS  | VARCHAR(8)  | The server status                        |
| FAILOVER_SN    | BIGINT      | The SN at the time point of failover     |
| FAILOVER_COUNT | BIGINT      | The number of failovers                  |

#### Column Information

##### SERVER_NAME

This is the name given to the server deployed in the DR environment.

##### CURRENT_MODE

This is the synchronization mode currently being executed and is displayed as either 'async' or 'sync'. 

All standby servers conform to the synchronization mode of the active server.

##### SERVER_ROLE

This is the role of the server and is displayed as either 'active' or 'standby'.

##### SERVER_MODE

This is the synchronization mode set by the user and is displayed as either 'async' or 'sync'.

##### SERVER_STATUS

This is the current execution mode of the server and is displayed as either 'run', 'stop' or 'Failure Server Repair'.

##### FAILOVER_SN

This is the SN at the time point on which a failover has occurred.

##### FAILOVER_COUNT

This is the SN at the time point on which a failover has occurred.

### V\$EVENT_NAME

This displays information about various wait events for which an Altibase server is waiting.

| Column name   | Type         | Description                    |
| ------------- | ------------ | ------------------------------ |
| EVENT_ID      | INTEGER      | The identifier of a wait event |
| NAME          | VARCHAR(128) | The name of the wait event     |
| WAIT_CLASS_ID | INTEGER      | The identifier of a wait class |
| WAIT_CLASS    | VARCHAR(128) | The name of the wait class     |

#### Column Information

##### EVENT_ID

This is the identifier of the wait event. 

##### NAME

This is the name of the wait event. The identifiers, names and corresponding descriptions are given in the following table.

| EVENT_ID | NAME                                                | Description                                                  |
| -------- | --------------------------------------------------- | ------------------------------------------------------------ |
| 0        | latch: buffer busy waits                            | A wait to access a block being changed by another session    |
| 1        | latch: drdb B-tree index SMO                        | A wait caused by a session that is executing a Structure Modification Operation (SMO) of a B-tree index |
| 2        | latch: drdb B-tree index SMO by other session       | A wait until the completion of an SMO of a B-tree index by another session |
| 3        | latch: drdb R-tree index SMO                        | A wait caused by a session that is executing an SMO of an R-tree index |
| 4        | db file multi page read                             | A wait caused by a session that is waiting for the completion of a request to read multiple pages |
| 5        | db file single page read                            | A wait caused by a session that is waiting for the completion of a request to read a single page |
| 6        | db file single page write                           | A wait until a free BCB is obtained before an LRU flush can be executed |
| 7        | enq: TX – row lock contention, data row             | A wait to place a lock on a row so that it can be updated    |
| 8        | enq: TX – allocate TXSEG entry                      | A wait to assign a transaction segment entry                 |
| 9        | latch free: drdb file i/o                           | A wait to obtain a file latch in order to perform read/write I/O on a disk file |
| 10       | latch free: drdb tbs list                           | A wait to obtain a hash latch on a tablespace being used by another thread |
| 11       | latch free: drdb tbs creation                       | A wait caused by a session that is attempting to create a file when a tablespace is created |
| 12       | latch free: disk page list entry                    | A wait to obtain a latch on a disk page list being used by another thread |
| 13       | latch free: drdb transaction segment freelist       | A wait for a transaction segment free list                   |
| 14       | latch free: drdb LRU list                           | A wait for an LRU list in the buffer pool                    |
| 15       | latch free: drdb prepare list                       | A wait for a prepare list in the buffer pool                 |
| 16       | latch free: drdb prepare list wait                  | A wait until a BCB has been added to a prepare list in the buffer pool |
| 17       | latch free: drdb flush list                         | A wait for a flush list in the buffer pool                   |
| 18       | latch free: drdb checkpoint list                    | A wait for a checkpoint list in the buffer pool              |
| 19       | latch free: drdb buffer flusher min recovery LSN    | A wait for a latch for concurrency control of a Recovery LSN of the buffer pool flusher |
| 20       | latch free: drdb buffer flush manager req job       | A wait for a latch for concurrency control of a flush job of the buffer pool |
| 21       | latch free: drdb buffer bcb mutex                   | A wait for a latch for concurrency control of a BCB of the buffer pool |
| 22       | latch free: drdb buffer bcb read io mutex           | A wait for a latch on a BCB of the buffer pool for page loading |
| 23       | latch free: drdb buffer buffer manager expand mutex | A wait for expansion of the buffer pool                      |
| 24       | latch free: drdb buffer hash mutex                  | A wait for a buffer pool hash                                |
| 25       | latch free: plan cache LRU List mutex               | A wait to obtain a latch on an LRU list in a plan cache when adding, moving, or removing a plan from the list. |
| 26       | latch free: statement list mutex                    | A wait to obtain a latch on a statement list when adding, moving, or removing a statement from the list. |
| 27       | latch free: others                                  | A wait to obtain a latch on anything being used by another thread that was not mentioned above |
| 28       | replication before commit                           | In EAGER mode, this is the local server waiting to commit a transaction until all of the XLogs corresponding to statements that preceded the COMMIT statement have been replayed on the remote server. (Please refer to the description of EAGER mode in the Altibase *Replication Manual*.) |
| 29       | replication after commit                            | In EAGER mode, this is the local server waiting to commit a transaction until the XLog corresponding to the COMMIT statement has been sent to the remote server. (Please refer to the description of EAGER mode in the *Replication Manual*.) |
| 30       | no wait event                                       | No wait event exists                                         |

##### WAIT_CLASS_ID

Wait events are conceptually grouped into broadly defined wait classes. For more detailed information about these wait classes, please refer to V$WAIT_CLASS_NAME. 

##### WAIT_CLASS

This is the identifier of the class of a wait event. For more detailed information about wait class identifiers, please refer to V$WAIT_CLASS_NAME. 

### V\$EXTPROC_AGENT

This is the meta table that contains information about the Agent Process created for the execution of external procedures.

| Column name | Type        | Description                                                  |
| ----------- | ----------- | ------------------------------------------------------------ |
| SID         | INTEGER     | The identifier of the session which created the Agent Process |
| PID         | INTEGER     | The Pid of the Agent Process                                 |
| SOCK_FILE   | VARCHAR(64) | The socket path for communication between processes          |
| CREATED     | INTEGER     | The date and time at which the Agent Process was created     |
| LAST_SEND   | INTEGER     | The data and time at which the Agent Process returned the result for the last time |
| LAST_RECV   | INTEGER     | The date and time at which the Agent Process received the call message for the last time |
| STATE       | VARCHAR(11) | The status of the Agent Process                              |

#### Column Information

##### SID

This is the identifier of the session which created the Agent Process. The Agent Process is subordinate to the session

##### PID

This is the process ID of the Agent Process.

##### SOCK_FILE

This is the path of a socket used for communicaiton between processes.

##### CREATED

This is the date and time at which the Agent Process was created.

##### LAST_SEND

This is the date and time at which the Agent Process returned a result to the server session that called an external procedure for the last time

##### LAST_RECV

This is the date and time at which the Agent Process received a call message from the server session for the last time.

##### STATE

This is the status of the Agent Process and it takes one of the following values.

- INITIALIZED: Is newly created and waiting for a call. 
- RUNNING: The external procedure is being executed. 
- STOPPED: Execution of the external procedure is complete. 
- FAILED: Has been either terminated abnormally, or the Agent Process has been terminated already.

### V\$FILESTAT 

This view displays cumulative statistical information about I/O on individual disk files since the system was started. These statistics can be used to determine which data files are hot spots. 

| Column name    | Type    | Description                                                  |
| -------------- | ------- | ------------------------------------------------------------ |
| SPACEID        | INTEGER | The tablespace identifier                                    |
| FILEID         | INTEGER | The data file identifier                                     |
| PHYRDS         | BIGINT  | The number of physical read I/O operations that have been conducted |
| PHYWRTS        | BIGINT  | The number of physical write I/O operations that have occurred |
| PHYBLKRD       | BIGINT  | The number of physical read I/O operations that have been conducted |
| PHYBLKWRT      | BIGINT  | The number of pages that have been physically written to disk |
| SINGLEBLKRDS   | BIGINT  | The number of read operations that have taken place on single pages |
| READTIM        | DOUBLE  | The total time (in milliseconds) spent on read I/O operations |
| WRITETIM       | DOUBLE  | The total time (in milliseconds) spent on write operations   |
| SINGLEBLKRDTIM | DOUBLE  | The total time taken to read a single page (in milliseconds) |
| AVGIOTIM       | DOUBLE  | The average time (in milliseconds) per I/O operation         |
| LSTIOTIM       | DOUBLE  | The time (in milliseconds) spent performing the most recent I/O operation |
| MINIOTIM       | DOUBLE  | The shortest time (in milliseconds) spent on a single I/O operation |
| MAXIORTM       | DOUBLE  | The longest time (in milliseconds) spent performing a single read operation |
| MAXIOWTM       | DOUBLE  | The longest time (in milliseconds) spent performing a single write operation |

#### Column Information

##### SPACEID

This is the identifier of the tablespace. 

##### FILEID

This is the identifier of the data file. 

##### PHYRDS

This is the total number of physical read I/O operations that have been performed. 

##### PHYWRTS

This is the total number of physical write operations that have been performed. 

##### PHYBLKRD

This is the total number of pages that have been opened for physical reading. 

##### PHYBLKWRT

This is the total number of pages that have been physically written to disk. 

##### SINGLEBLKRDS

This is the total number of read I/O operations that have been performed on single pages. 

##### READTIM

This is the total time (in milliseconds) spent performing read I/O operations. 

##### WRITETIM

This is the total time (in milliseconds) spent performing write I/O operations. 

##### SINGLEBLKRDTIM

This is the total amount of time (in milliseconds) spent performing read I/O operations on single pages.

##### AVGIOTIM

This is the average time (in milliseconds) spent performing a single I/O operation. 

##### LSTIOTIM

This is the time (in milliseconds) spent performing the most recent I/O operation. 

##### MINIOTIM

This is the minimum time (in milliseconds) spent performing a single I/O operation. 

##### MAXIORTM

This is the maximum time (in milliseconds) spent performing a single read I/O operation. 

##### MAXIOWTM

This is the maximum time (in milliseconds) spent performing a single write I/O operation. 

### V\$FLUSHER 

This view displays information about flushing tasks.

| Column name              | Type    | Description                                                  |
| ------------------------ | ------- | ------------------------------------------------------------ |
| ID                       | INTEGER | This is the identifier of the flusher                        |
| ALIVE                    | INTEGER | This indicates whether the flusher is currently active.      |
| CURRENT_JOB              | INTEGER | Current job 1: replacement flushing is underway 2: checkpoint flushing is underway 3: an object is being flushed |
| DOING_IO                 | INTEGER | This indicates whether the flusher is performing disk I/O.   |
| INIOB_COUNT              | INTEGER | This is the number of times that an internal buffer has been directly accessed in order to save contents to be flushed therein. |
| REPLACE_FLUSH_JOBS       | BIGINT  | This is the cumulative number of replacement flushing tasks that have been completed |
| REPLACE_FLUSH_PAGES      | BIGINT  | This is the cumulative number of pages that have been written to disk by replacement flushing. |
| REPLACE_SKIP_PAGES       | BIGINT  | This is the cumulative number of pages for which flushing was canceled during replacement flushing. |
| CHECKPOINT_FLUSH_JOBS    | BIGINT  | This is the cumulative number of checkpoint flushing tasks that have been completed. |
| CHECKPOINT_FLUSH_PAGES   | BIGINT  | This is the cumulative number of pages that have been written to disk by checkpoint flushing. |
| CHECKPOINT_SKIP_PAGES    | BIGINT  | This is the cumulative number of pages for which flushing was canceled during checkpoint flushing. |
| OBJECT_FLUSH_JOBS        | BIGINT  | This is the cumulative number of times that object flushing has been performed. |
| OBJECT_FLUSH_PAGES       | BIGINT  | This is the cumulative number of pages that have been written to disk by object flushing. |
| OBJECT_SKIP_PAGES        | BIGINT  | This is the cumulative number of pages for which flushing was canceled during object flushing. |
| LAST_SLEEP_SEC           | INTEGER | This is the length of time that the flusher has slept after having completed all of its tasks. |
| TIMEOUT                  | BIGINT  | This is the number of times that a sleeping flusher has woken up in order to check whether it has any tasks |
| SIGNALED                 | BIGINT  | This is the number of times that the flusher has been woken up by a signal from Altibase. |
| TOTAL_SLEEP_SEC          | BIGINT  | This is the total length of time that the flusher has slept. |
| TOTAL_FLUSH_PAGES        | BIGINT  | The cumulative number of pages that have been flushed        |
| TOTAL_LOG_SYNC_USEC      | BIGINT  | The cumulative amount of time taken to write buffer-resident redo logs to disk |
| TOTAL_DW_USEC            | BIGINT  | The cumulative amount of time to taken write the contents of doublewrite buffers to disk |
| TOTAL_WRITE_USEC         | BIGINT  | The cumulative amount of time to taken to write data pages to data files |
| TOTAL_SYNC_USEC          | BIGINT  | The cumulative amount of time to taken to forcibly flush data pages to disk |
| TOTAL_FLUSH_TEMP_PAGES   | BIGINT  | The cumulative number of temporary pages that have been flushed |
| TOTAL_TEMP_WRITE_USEC    | BIGINT  | The cumulative amount of time to taken to write temporary pages to temporary files |
| TOTAL_CALC_CHECKSUM_USEC | BIGINT  | The cumulative amount of time to taken to perform checksum calculations |
| DB_WRITE_PERF            | DOUBLE  | The average number of bytes that are written per second when writing data pages to data files |
| TEMP_WRITE_PERF          | DOUBLE  | The average number of bytes that are written per second when writing temporary pages to temporary files |

#### Column Information

##### ID

This is the identifier of the flusher. A newly created identifier cannot be a duplicate of an existing identifier.

##### ALIVE

This indicates whether the flusher is currently active. Individual flushers can be started or stopped using DCL statements.

##### CURRENT_JOB

This indicates the type of job that the flusher is currently performing.

- A value of 1 indicates that the flusher is performing replacement flushing. The purpose of replacement flushing is to flush buffers that have not been accessed for a long time so that they can be replaced. 
- A value of 2 indicates that the flusher is performing checkpoint flushing. The purpose of checkpoint flushing is to flush the buffer that has not been flushed for the longest time in order to reduce the amount of time required to perform checkpointing. 
- A value of 3 indicates that the flusher is performing object flushing on a particular object, such as an index, table, segment, etc

##### DOING_IO

This indicates whether the flusher is currently performing disk I/O in order to fulfill its current task. 

##### INIOB_COUNT

In order to save pages to disk, their contents are saved in an internal buffer (IOB). This value indicates the number of times that this internal buffer has been directly accessed in order to save contents to be flushed therein. 

##### REPLACE_FLUSH_JOBS

This is the cumulative number of replacement flush opeartions performed.

##### REPLACE_FLUSH_PAGES

This is the cumulative number of pages that have been written to disk in the course of performing replacement flushing tasks.

##### REPLACE_SKIP_PAGES

This is the cumulative number of pages for which a flushing task was canceled during replacement flushing. Such cancellation can occur either according to some policy or in the interests of efficiency.

##### CHECKPOINT_FLUSH_JOBS

This the cumulative number of checkpoint flush operations.

##### CHECKPOINT_FLUSH_PAGES

This is the cumulative number of pages that have been written to disk in the course of performing checkpoint flushing tasks.

##### CHECKPOINT_SKIP_PAGES

This is the cumulative number of pages for which a flushing task was canceled during checkpoint flushing. Such cancellation can occur either according to some policy or in the interests of efficiency.

##### OBJECT_FLUSH_JOBS

The is the cumulative number of times that an object was flushed.

##### OBJECT_FLUSH_PAGES

This is the cumulative number of pages that have been written to disk in the course of performing object flushing tasks.

##### OBJECT_SKIP_PAGES

This is the cumulative number of pages for which a flushing task was canceled during object flushing. Such cancellation can occur either according to some policy or in the interests of efficiency.

##### LAST_SLEEP_SEC

This is the length of time the flusher has most recently slept after having completed all of its tasks.

##### TIMEOUT

Flushers that have no tasks and thus go to sleep are required to wake up at regular intervals to check whether they have work to do. This is the number of times that this has occurred.

##### SIGNALED

In order to improve the performance with which some task is performed, Altibase can signal a sleeping flusher and wake it up. This value is the number of times that the flusher has been woken up by such a signal.

##### TOTAL_SLEEP_SEC

This is the total length of time that the flusher has slept because the flusher did not have any work to do.

##### TOTAL_FLUSH_PAGES

This is the cumulative number of pages that have been flushed in the course of checkpoint flushing or replacement flushing.

##### TOTAL_LOG_SYNC_USEC

When data pages are flushed, redo logs must first be written to disk using the WAL (Write Ahead Logging) method. This is the cumulative amount of time taken to write redo logs to disk.

##### TOTAL_DW_USEC

This is the cumulative amount of time taken to write the contents of doublewrite buffers to disk. In so-called “doublewrite”, pages are first written to DW (“doublewrite”) files, i.e. the disk-resident doublewrite buffer. Once this process is complete, the pages are then written to data files in the usual location. If the operating system crashes during the process of writing pages to data files, or if these data files become corrupted, it will be possible to perform data recovery using the uncorrupted copies of the pages in the doublewrite buffer.

##### TOTAL_WRITE_USEC

This is the cumulative amount of time taken to write data pages to data files. This value does not include the amount of time spent flushing data to disk.

##### TOTAL_SYNC_USEC

This is the cumulative amount of time spent forcibly flushing data to disk.

##### TOTAL_FLUSH_TEMP_PAGES

This is the cumulative number of temporary pages that have been flushed. (Temporary pages are used for storing temporary tables, which are used for sort operations and hash joins.)

##### TOTAL_TEMP_WRITE_USEC

This is the amount of time spent writing temporary pages to temporary files.

##### TOTAL_CALC_CHECKSUM_USEC

This is the amount of time taken to calculate checksums, which are used to determine whether pages are corrupt.

##### DB_WRITE_PERF

This is the average number of bytes that are written per second (in kB/sec) when data pages are written to data files.

##### TEMP_WRITE_PERF

This is the average number of bytes that are written per second (kB/sec) when temporary pages are written to temporary files.

### V\$FLUSHINFO

This view displays buffer flush information.

| Column name               | Type    | Description                                                  |
| ------------------------- | ------- | ------------------------------------------------------------ |
| LOW_FLUSH_LENGTH          | INTEGER | The minimum length of the flush list above which replacement flushing can occur |
| HIGH_FLUSH_LENGTH         | INTEGER | The flush list length at which the flusher ignores REPLACE_FLUSH_COUNT and flushes all the buffers in the flush list. |
| LOW_PREPARE_LENGTH        | INTEGER | The threshold length of the prepare list that can cause replacement flushing. Replacement flushing occurs when the prepare list is shorter than this length. |
| CHECKPOINT_FLUSH_COUNT    | BIGINT  | The number of buffers to be flushed when checkpoint flushing occurs. |
| FAST_START_IO_TARGET      | BIGINT  | The number of dirty pages that will not be flushed when checkpoint flushing occurs |
| FAST_START_LOGFILE_TARGET | INTEGER | The number of log files that will not be flushed when checkpoint flushing occurs |
| REQ_JOB_COUNT             | INTEGER | The number of tasks currently registered for the flush manager |

#### Column Information

##### LOW_FLUSH_LENGTH

This is the minimum length of the flush list above which replacement flushing can occur.

##### HIGH_FLUSH_LENGTH

This is the flush list length at which the flusher ignores REPLACE_FLUSH_COUNT and flushes all the buffers in the flush list.

##### LOW_PREPARE_LENGTH

This is the threshold length of the prepare list. Replacement flushing occurs if the length of a prepare list drops below this length.

##### CHECKPOINT_FLUSH_COUNT

This is the number of buffers that will be flushed when checkpoint flushing is performed.

##### FAST_START_IO_TARGET

This is the number of dirty pages that are not flushed when checkpoint flushing occurs.

##### FAST_START_LOGFILE_TARGET

This is the number of log files that are not flushed when checkpoint flushing occurs. These are the most recently created log files.

##### REQ_JOB_COUNT

This is the number of jobs registered in the flush manager.

### V\$INDEX

This view shows information about the indexes that currently exist in the database: 

| Column name   | Type       | Description                                                  |
| ------------- | ---------- | ------------------------------------------------------------ |
| TABLE_OID     | BIGINT     | The object identifier of the table header                    |
| INDEX_SEG_PID | INTEGER    | The page identifier of a segment header in the case of a disk index |
| INDEX_ID      | INTEGER    | The identifier of the index                                  |
| INDEXTYPE     | VARCHAR(7) | An indicator that identifies whether the index is a primary key or a standard index |

#### Column Information

##### TABLE_OID

This is the object identifier of the table for which the index was created, and stores the physical location of the header, which contains the table information.

##### INDEXTYPE

This indicates whether the index is used as a primary key or as a normal index.

- PRIMARY: The index is used as primary key.
- NORMAL: The index is used as normal one

### V\$INSTANCE

This view displays information about an Altibase database, the amount of time it took to start up, and the amount of time that has elapsed since startup. 

| Column name      | Type        | Description                                                  |
| ---------------- | ----------- | ------------------------------------------------------------ |
| STARTUP_PHASE    | VARCHAR(13) | The current startup phase                                    |
| STARTUP_TIME_SEC | BIGINT      | The system time at which the system was started (in seconds). |
| WORKING_TIME_SEC | BIGINT      | The amount of time that has elapsed from startup to the present |

### V\$INTERNAL_SESSION

This view displays information about a session created in the DBMS_CONCURRENT_EXEC package. For further information, please refer to V$SESSION.

| Column name            | Type         | Description                                                  |
| ---------------------- | ------------ | ------------------------------------------------------------ |
| ID                     | BIGINT       | The session ID                                               |
| TRANS_ID               | BIGINT       | The ID of the transaction that is currently being executed in the session |
| QUERY_TIME_LIMIT       | BIGINT       | The amount of time by which a query running in the session exceeded the specified time limit |
| DDL_TIME_LIMIT         | BIGINT       | The amount of time by which a DDL statement running in the session exceeded the specified time limit |
| FETCH_TIME_LIMIT       | BIGINT       | The amount of time by which a fetch operation running in the session exceeded the specified time limit |
| UTRANS_TIME_LIMIT      | BIGINT       | The amount of time by which an update transaction running in the session exceeded the specified time limit |
| IDLE_TIME_LIMIT        | BIGINT       | The amount of time by which the current session exceeded the specified idle time limit |
| IDLE_START_TIME        | INTEGER      | The time at which the session becomes inactive (idle)        |
| ACTIVE_FLAG            | INTEGER      | The active transaction flag                                  |
| OPENED_STMT_COUNT      | INTEGER      | The number of statements being executed in the session       |
| DB_USERNAME            | VARCHAR(128) | The database user name                                       |
| DB_USERID              | INTEGER      | The database user ID                                         |
| DEFAULT_TBSID          | BIGINT       | The ID of the user’s default tablespace                      |
| DEFAULT_TEMP_TBSID     | BIGINT       | The ID of the user’s default temporary tablespace            |
| SYSDBA_FLAG            | INTEGER      | Whether the session is connected as SYSDBA                   |
| AUTOCOMMIT_FLAG        | INTEGER      | The autocommit flag                                          |
| SESSION_STATE          | VARCHAR(13)  | The session state                                            |
| ISOLATION_LEVEL        | INTEGER      | The session isolation level                                  |
| REPLICATION_MODE       | INTEGER      | The replication mode                                         |
| TRANSACTION_MODE       | INTEGER      | The transaction mode                                         |
| COMMIT_WRITE_WAIT_MODE | INTEGER      | See below                                                    |
| OPTIMIZER_MODE         | INTEGER      | The optimizer mode                                           |
| HEADER_DISPLAY_MODE    | INTEGER      | Indicates whether only the column names are output, or whether the table names are output along with the column names when the results of a SELECT query are output. 0: The table names are displayed along with the column names. 1: Only the column names are output. |
| CURRENT_STMT_ID        | INTEGER      | The ID of the statement that is currently being executed     |
| STACK_SIZE             | INTEGER      | The size of the stack for query processing (Unit: bytes)     |
| DEFAULT_DATE_FORMAT    | VARCHAR(64)  | The default date format (e.g. DD-MON-RRRR)                   |
| TRX_UPDATE_MAX_LOGSIZE | BIGINT       | The maximum size of the DML log (Unit: bytes)                |
| PARALLE_DML_MODE       | INTEGER      | Deprecated                                                   |
| LOGIN_TIME             | INTEGER      | The time at which the client was logged in                   |
| FAILOVER_SOURCE        | VARCHAR(256) | Information about the connection when a failover occurred    |
| NLS_TERRITORY          | VARCHAR(40)  | The territory name of the session                            |
| NLS_ISO_CURRENCY       | VARCHAR(40)  | The ISO currency code of the session                         |
| NLS_CURRENCY           | VARCHAR(10)  | The local currency symbol of the session                     |
| NLS_NUMERIC_CHARACTERS | VARCHAR(2)   | The group separator and decimal character of the session     |
| TIME_ZONE              | VARCHAR(40)  | The territory name/abbreviation or UTC_OFFSET of the specified time zone for the session |
| LOB_CACHE_THRESHOLD    | INTEGER      | The value specified for the LOB_CACHE_THRESHOLD property     |
| QUERY_REWRITE_ENABLE   | VARCHAR(7)   | The value specified for the QUERY_REWRITE_ENABLE property    |

#### Column Information

##### TRANS_ID

Indicates the transaction identifier currently running in the session. If no transaction is currently running, this value is -1.

##### ACTIVE_FLAG

If the session is executing a statement, the value is 1. If the session is merely connected or has committed/rolled back a transaction, the value is 0. 

##### SYSDBA_FLAG

Indicates whether the connected session is in sysdba mode or not.

- 1: sysdba mode

##### AUTOCOMMIT_FLAG

Indicates whether or not the session is in AUTOCOMMIT mode. 

* 0: NON-AUTOCOMMIT 
* 1: AUTOCOMMIT 

##### SESSION_STATE

| STATE         | Description                                                  |
| ------------- | ------------------------------------------------------------ |
| INIT          | Waiting for the client to request                            |
| AUTH          | Finished user authentication                                 |
| SERVICE READY | Ready for service. (Unable to start a transaction. Only an XA session can have this state.) |
| SERVICE       | Servicing                                                    |
| END           | Terminated normally (If a transaction exists, it has been committed successfully.) |
| ROLLBACK      | Terminated abnormally (If a transaction exists, it has been rolled back.) This state occurs if the client was disconnected or the server forcefully killed the session. |
| UNKNOWN       | N/A                                                          |

##### REPLICATION_MODE

The replicaiton mode.

- 0: DEFAULT
- 16: NONE

##### TRANSACTION_MODE

The transaction mode.

- 0: READ/WRITE
- 4: READ ONLY

##### COMMIT_WRITE_WAIT_MODE

- 0: when commiting, do not wait for the log to be written to disk
- 1: when commiting, wait for the log to be written to disk

##### OPTIMIZER_MODE

Indicates the optimization mode set for the session.

- 1: Rule based
- 0: Cost based

##### QUERY_REWRITE_ENABLE

Indicates the value set for the QUERY_REWRITE_ENABLE property in the session. Please refer to Chapter 2 for the QUERY_REWRITE_ENABLE property.

- FALSE: Disable function-based indexes when converting queries on the Altibase server
- TRUE: Enable function-based indexes when converting queries on the Altibase server.
