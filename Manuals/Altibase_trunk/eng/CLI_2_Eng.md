<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [CLI User's Manaul](#cli-users-manaul)
  - [2. Altibase CLI Functions](#2-altibase-cli-functions)
    - [SQLGetInfo](#sqlgetinfo)
    - [SQLGetPlan](#sqlgetplan)
    - [SQLGetStmtAttr](#sqlgetstmtattr)
    - [SQLGetTypeInfo](#sqlgettypeinfo)
    - [SQLMoreResults](#sqlmoreresults)
    - [SQLNativeSql](#sqlnativesql)
    - [SQLNumParams](#sqlnumparams)
    - [SQLNumResultCols](#sqlnumresultcols)
    - [SQLParamData](#sqlparamdata)
    - [SQLPrepare](#sqlprepare)
    - [SQLPrimaryKeys](#sqlprimarykeys)
    - [SQLProcedureColumns](#sqlprocedurecolumns)
    - [SQLProcedures](#sqlprocedures)
    - [SQLPutData](#sqlputdata)
    - [SQLRowCount](#sqlrowcount)
    - [SQLSetConnectAttr](#sqlsetconnectattr)
    - [SQLSetDescField](#sqlsetdescfield)
    - [SQLSetEnvAttr](#sqlsetenvattr)
    - [SQLSetPos](#sqlsetpos)
    - [SQLSetStmtAttr](#sqlsetstmtattr)
    - [SQLSpecialColumns](#sqlspecialcolumns)
    - [SQLStatistics](#sqlstatistics)
    - [SQLTablePrivileges](#sqltableprivileges)
    - [SQLTables](#sqltables)
    - [SQLTransact](#sqltransact)
  - [3. LOB Interface](#3-lob-interface)
    - [LOB data types](#lob-data-types)
    - [LOB Function Overview](#lob-function-overview)
    - [SQLBindFileToCol](#sqlbindfiletocol)
    - [SQLindFileToParam](#sqlindfiletoparam)
    - [SQLGetLobLength](#sqlgetloblength)
    - [SQLGetLob](#sqlgetlob)
    - [SQLPutLob](#sqlputlob)
    - [SQLTrimLob](#sqltrimlob)
    - [SQLFreeLob](#sqlfreelob)
  - [4. Using Cursors](#4-using-cursors)
    - [Cursor Characteristics](#cursor-characteristics)
    - [Implicit Cursor Conversionse](#implicit-cursor-conversionse)
    - [Scrolling and Fetching Rows](#scrolling-and-fetching-rows)
    - [Restrictions](#restrictions)
  - [Appendix A. Sample Codes](#appendix-a-sample-codes)
    - [Programing Considerations](#programing-considerations)
    - [Sample of Simple Basic Program](#sample-of-simple-basic-program)
    - [Sample of Using Metadata](#sample-of-using-metadata)
    - [Example of Procedure Test Program](#example-of-procedure-test-program)
  - [Appendix B. Data Types](#appendix-b-data-types)
    - [SQL Data Types](#sql-data-types)
    - [C Data Types](#c-data-types)
    - [Converting SQL Data into C Data Types](#converting-sql-data-into-c-data-types)
    - [Converting C Data into SQL Data types](#converting-c-data-into-sql-data-types)
  - [Appendix C. Error Codes](#appendix-c-error-codes)
    - [SQLSTATE](#sqlstate)
    - [Statement State Transition-related Errors](#statement-state-transition-related-errors)
    - [State Transition Table](#state-transition-table)
  - [Appendix D. Upgrade](#appendix-d-upgrade)
    - [Data Type](#data-type)
    - [Other Changes](#other-changes)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Altibase® Application Development

# CLI User's Manaul

![](/media/CLI/e5cfb3761673686d093a3b00c062fe7a.png)

Release 7.1

Copyright ⓒ 2001\~2020 Altibase Corp. All Rights Reserved.

This manual contains proprietary information of Altibase Corporation; it is provided under a license agreement containing restrictions on use and disclosure and is also protected by copyright patent and other intellectual property law. Reverse engineering of the software is prohibited. All trademarks, registered or otherwise, are the property of their respective owners.

**Altibase Corp**

10F, Daerung PostTower II, 306, Digital-ro, Guro-gu, Seoul 08378, Korea Telephone: +82-2-2082-1000 Fax: 82-2-2082-1099

Customer Service Portal: http://support.altibase.com/en/

Homepage: [[http://www.altibase.com](http://www.altibase.com/)]

## 2. Altibase CLI Functions

### SQLGetInfo

This indicates to return general information of DBMS accessed to application. 

SQLGetInfoW() as a Unicode string supports same execution as SQLGetInfo()

#### Syntax

```
SQLRETURN SQLGetInfo(
	SQLHANDLE    ConnectionHandle,
	SQLUSMALLINT InfoType,
	SQLPOINTER   InfoValuePtr,
	SQLSMALLINT  BufferLength,
	SQLSMALLINT  *StringLengthPtr );
```

#### Arguments

| Data Type      | Argument         | In/Output | Description                                                  |
| -------------- | ---------------- | --------- | ------------------------------------------------------------ |
| SQLHANDLE      | ConnectionHandle | Input     | Database connection handle                                   |
| SQLUSMALLINT   | InfoType         | Input     | Type of information which you want to search. The following values are available in addition to the values provided by the ODBC standard. ALTIBASE_PROTO_VER: A character string that indicates the protocol version of the Altibase connected by the Altibase CLI driver. |
| SQLPOINTER     | InfoValuePtr     | Output    | 5 kinds of data are outputted according to data types of buffer pointer which makes data returned: <br/>16 bit integer value <br/>32 bit integer value <br/>32 bit binary value <br/>32 bit mask <br/>Null-terminated Character String |
| SQLSMALLINT    | BufferLength     | Input     | The byte size of buffer which InfoValuePtr indicates         |
| SQLSMALLINT \* | StringLengthPtr  | Output    | The byte length of result values which InfoValuePtr indicates |

#### Return Values

```
SQL_SUCCESS
SQL_SUCCESS_WITH_INFO
SQL_ERROR
SQL_INVALID_HANDLE
```

#### Description

SQLGetInfo() is used to get general information of DBMS. You can get relevant information of each type according to InfoType with this function, and Altibase follows the standard of ODBC.

#### Diagnosis		

| SQLSTATE | Description                                                 | Comments                                                     |
| -------- | ----------------------------------------------------------- | ------------------------------------------------------------ |
| 01004    | String data, right truncated                                | The size of returned values is bigger than that of the given buffer. |
| 08003    | Disconnection                                               | Disconnection Status                                         |
| 08S01    | Communication channel error(Data Sending/Recieving Failure) | Communication channel error before the function processing is completed between the Altibase CLI driver and the database. |
| HY000    | General error                                               |                                                              |
| HY090    | Invalid arguments used                                      | One value among name length arguments must be under 0 or not be equal to SQL_NTS. |
| HY096    | Out of InfoType range                                       | IThe values specified in InfoType are invalid in the version which ODBC provides. |

### SQLGetPlan

This is nonstandard function returning execution information.

#### Syntax

```
SQLRETURN SQLGetPlan (
    SQLHSTMT	stmt,
    SQLCHAR**	aPlan);
```

#### Arguments

| Data Type   | Argument | In/Output | Description                                   |
| ----------- | -------- | --------- | --------------------------------------------- |
| SQLHSTMT    | stmt     | Input     | Input statement handle                        |
| SQLCHAR\*\* | aPlan    | Output    | Pointer to store output execution information |

#### Returned Values

```
SQL_SUCCESS
SQL_ERROR
```

#### Description

SQLGetPlan is nonstandard function, but you can use it when retrieving information of execution plan. 

At this time, you shouldn't modify information returned by aPlan.

#### Related Function

```
SQLSetConnectAttr
```

#### Example

< Refer to: $ALTIBASE_HOME/sample/SQLCLI/demo_plan.cpp >

```
if( SQLSetConnectAttr( dbc, ALTIBASE_EXPLAIN_PLAN,
                           (SQLPOINTER) 1, 0) != SQL_SUCCESS)
.
.
.
    if ( SQLGetPlan(stmt, (SQLCHAR**)&plan) != SQL_SUCCESS )
```

### SQLGetStmtAttr

SQLGetStmtAttr retrieves the attributes related to the current statement handle. 

SQLGetStmtAttrW() as a Unicode string supports same execution as SQLGetStmtAttr().

#### Syntax

```
SQLRETURN  SQLGetStmtAttr (
	SQLHSTMT 		stmt,
	SQLINTEGER		Attribute,
	SQLPOINTER		param,
	SQLINTEGER  	StringLength
	SQLINTEGER *	StringLengthPtr );
```

#### Arguments

| Data Type     | Argument        | In/Output | Description                                                  |
| ------------- | --------------- | --------- | ------------------------------------------------------------ |
| SQLHSTMT      | stmt            | Input     | Statement handle                                             |
| SQLINTEGER    | Attribute       | Input     | Attribute to set. Refer to SQLSetStmtAttr.                   |
| SQLPOINTER    | param           | Output    | Pointer of the value related to the attributeDepending on the Attribute, the param will be a 32-bit integer, the pointer of the Null-terminator, the binary pointer, or the value defined in the ODBC. If Attribute is the unique value of the ODBC, *param* is the integral number with a sign. |
| SQLINTEGER    | StringLength    | Input     | If the Attribute has been defined in the ODBC and if the param indicates the character string or binary buffer, this argument must be the length of *param. If the Attribute is defined in the ODBC and param is an integer, this Arguments will be ignored. |
| SQLINTEGER \* | StringLengthPtr | Output    | Returns the length (excluding the NULLterminatior) of the value returned to *ValuePtr.* |

#### Return Values

```
SQL_SUCCESS
SQL_SUCCESS_WITH_INFO
SQL_ERROR
SQL_INVALID_HANDLE
```

#### Description

SQLGetStmtAttr () returns the attribute related to the statement handle. For the statement attribute or more information, refer to SQLSetStmtAttr ().

#### Diagnosis

| SQLSTATE | Descriptionb                    | Comments                                                     |
| -------- | ------------------------------- | ------------------------------------------------------------ |
| HY090    | Invalid string or buffer length | StringLength is smaller than 0.                              |
| HY092    | Invalid attribute or option     | The value specified in the attribute argument is not supported by this driver. |
| HYC00    | Option not implemented          | The value specified in the attribute argument of ODBC is valid but not supported by this driver. |

#### Related Functions

```
SQLGetConnectAttr
SQLSetConnectAttr
SQLSetStmtAttr
```

### SQLGetTypeInfo

SQLGetTypeInfo returns information related to the data types that the database supports. The Altibase CLI driver returns the information in the form of a SQL result set. The data type is used in the DDL statement.

#### Syntax

```
SQLRETURN  SQLGetTypeInfo (
	SQLHSTMT 		stmt,
	SQLSMALLINT		type );
```

#### Arguments

| Data Type   | Argument | In/Output | Description      |
| ----------- | -------- | --------- | ---------------- |
| SQLHSTMT    | stmt     | Input     | Statement handle |
| SQLSMALLINT | type     | Input     | SQL data type    |

#### Return Values

```
SQL_SUCCESS
SQL_SUCCESS_WITH_INFO
SQL_INVALID_HANDLE
SQL_ERROR
```

#### Description

SQLGetTypeInfo () converts data type information that Altibase provides into the standard result set type. The current result set is sorted by TYPE_NAME in ascending orders to be returned.

#### Diagnosis

| SQLSTATE | Description                 | Comments                                                     |
| -------- | --------------------------- | ------------------------------------------------------------ |
| 08S01    | Communication channel error | Communication channel failure before the function processing between the Altibase CLI driver and the database is completed |
| HY000    | General error               |                                                              |
| HY001    | Memory allocation error     | Cannot allocate the requested memory for the Altibase CLI driver to execute the function and complete execution |

#### Related Functions

```
SQLBindCol
SQLColAttribute
SQLFetch
```

#### Example

< Refer to: $ALTIBASE_HOME/sample/SQLCLI/demo_info1.cpp >

```
if (SQLGetTypeInfo(stmt, SQL_ALL_TYPES) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, "SQLGetTypeInfo");
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR; 
}

while ( (rc = SQLFetch(stmt)) != SQL_NO_DATA)
{
    if ( rc == SQL_ERROR )
    {
        execute_err(dbc, stmt, "SQLGetTypeInfo:SQLFetch");
        break;
    }
    SQLGetData(stmt, 1, SQL_C_CHAR, szTypeName, STR_LEN, &cbTypeName);
    SQLGetData(stmt, 2, SQL_C_SSHORT, &DataType, 0, &cbDataType);
      SQLGetData(stmt, 3, SQL_C_SLONG, &ColumnSize, 0, &cbColumnSize);
      SQLGetData(stmt, 9, SQL_C_SSHORT, &Searchable, 0, NULL);
      SQLGetData(stmt, 14, SQL_C_SSHORT, &MinScale, 0, &cbMinScale);
      SQLGetData(stmt, 15, SQL_C_SSHORT, &MaxScale, 0, &cbMaxScale);
      SQLGetData(stmt, 16, SQL_C_SSHORT, &SQLDataType, 0, &cbSQLDataType);
      SQLGetData(stmt, 18, SQL_C_SLONG, &NumPrecRadix, 0, &cbNumPrecRadix);

      printf("%-20s%10d%10d%10d\t",
szTypeName, DataType, ColumnSize, SQLDataType);
      if ( Searchable == SQL_PRED_NONE )
      {
          printf("SQL_PRED_NONE\n");
      }
      else if ( Searchable == SQL_PRED_CHAR )
      {
          printf("SQL_PRED_CHAR\n");
      }
      else if ( Searchable == SQL_PRED_BASIC )
      {   
          printf("SQL_PRED_BASIC\n");
      }
      else if ( Searchable == SQL_SEARCHABLE )
      {   
          printf("SQL_SEARCHABLE\n");
      }
}
```

### SQLMoreResults

SQLMoreResults returns whether there is more result.

#### Syntax

```
SQLRETURN SQLMoreResults (
	SQLHSTMT 		stmt);
```

#### Argument

| Data Type | Argument | In/Output | Description        |
| --------- | -------- | --------- | ------------------ |
| SQLHSTMT  | stmt     | Input     | Instruction handle |

#### Result Values

```
SQL_SUCCESS
SQL_NO_DATA
```

#### Description

When a statement is fetched to obtain its result, the corresponding cursor is located at the first record of the result set. Depending on an application, when its result set is used, a further check is performed to see if there is more result left. If there are more result values left, SQL_SUCCESS is returned, and if not, SQL_NO_DATA_FOUND is returned.

If the result set is fetched, the cursor is located at the first result set. Depending on an application, when its result set is used, a further check is performed to see if there is more result left. If there are more result values left, SQL_SUCCESS is returned, and if not, SQL_NO_DATA_FOUND is returned.

#### Related Function

```
SQLFetch
```

### SQLNativeSql

This coverts SQL statements to statements supported by Altibase CLI driver. 

Unicode SQLNativeSqlW() supports same execution as SQLNativeSql().

#### Syntax

```
SQLRETURN SQLNativeSql (
		SQLHDBC dbc,
		SQLCHAR *InstatementText,
		SQLINTEGER textLength,
		SQLCHAR *OutStstementText,
		SQLINTEGER bufferLength,
		SQLINTEGER textLength);
```

#### Argument

| Data Type  | Argument         | In/Output | Description                                                  |
| ---------- | ---------------- | --------- | ------------------------------------------------------------ |
| SQLHDBC    | dbc              | Input     | Connection handle                                            |
| SQLCHAR \* | InstatementText  | Input     | SQL statements to convert                                    |
| SQLINTEGER | textLength       | Input     | The length, in bytes, of the contents of the InstatementText argument |
| SQLCHAR \* | OutStstementText | Output    | Buffer Pointer recieving the converted SQL statements        |
| SQLINTEGER | bufferLength     | Input     | Size of OutStstementText                                     |
| SQLINTEGER | textLength       | Output    | Size specified in OutStstementText                           |

#### Return Values

```
SQL_SUCCESS
SQL_SUCCESS_WITH_INFO
SQL_INVALID_HANDLE
SQL_ERROR
```

#### Description 

This converts SQL statements to statements supported by Altibase CLI driver.

Altibase supports the following syntaxes:

-   {d, '1981-09-27'} → TO_DATE('1981-09-27', 'YYYY-MM-DD')

-   {t, '07:23:56'} → TO_DATE('07:23:56', 'HH:MI:SS')

-   {ts, '1981-09-27 07:23:56'} → TO_DATE('1981-09-27 07:23:56', 'YYYY-MM-DD
    HH:MI:SS')

-   {? = call PROC1(a, ?, c)} → EXECUTE ? := PROC1(a, ? ,c)

#### Diagnosis

| SQLSTATE | Description             | Comments                                                     |
| -------- | ----------------------- | ------------------------------------------------------------ |
| HY000    | General error           | No error occurs explicitly.                                  |
| HY001    | Memory allocation error | This denotes to fail to allocate memory for handle.          |
| 01004    | Data is cut off         | Buffer size of OutStstementText is lesser than the size of returned data. |

#### Example

```
SQLNativeSql(  dbc, 
               (SQLCHAR*)"INSERT INTO T1 VALUES( {d '1981-09-27'} )",
               SQL_NTS,
               outText,
               100,
               &outTextLen);
outText에 INSERT INTO T1 VALUES( TO_DATE('1981-09-27', 'YYYY-MM-DD'))가 저장된다.
```

### SQLNumParams

SQLNumParams returns the number of parameters in a SQL statement.

#### Syntax

```
SQLRETURN  SQLNumParams (
	SQLHSTMT 		    stmt,
	SQLSMALLINT * 		parameterCounterPtr );
```

#### Arguments

| Data Type      | Argument          | In/Out | Description                             |
| -------------- | ----------------- | ------ | --------------------------------------- |
| SQLHSTMT       | stmt              | Input  | Statement handle                        |
| SQLSMALLINT \* | parameterCountPtr | Output | Pointer of the number of the parameters |

#### Return Values

```
SQL_SUCCESS
```

#### Description

This function can be called only after SQLPrepare () is called. 

If the stmt does not include parameters, SQLNumParams () will set 0 in **parameterCountPtr*.

#### Diagnosis	

| SQLSTATE | Description   | Comments |
| -------- | ------------- | -------- |
| HY000    | General error |          |

#### Related Functions 

```
SQLBindParameter
SQLDescribeParam	
```

#### Example

< Refer to: $ALTIBASE_HOME/sample/SQLCLI/demo_info2.cpp >

```
SQLPrepare(hstmt, Statement, SQL_NTS);

// Check to see if there are any parameters. If so, process them.
SQLNumParams(hstmt, &NumParams);
if (NumParams) {
   // Allocate memory for three arrays. The first holds pointers to buffers in which
   // each parameter value will be stored in character form. The second contains the
   // length of each buffer. The third contains the length/indicator value for each
   // parameter.
   PtrArray = (SQLPOINTER *) malloc(NumParams * sizeof(SQLPOINTER));
   BufferLenArray = (SQLINTEGER *) malloc(NumParams * sizeof(SQLINTEGER));
   LenOrIndArray = (SQLINTEGER *) malloc(NumParams * sizeof(SQLINTEGER));

   for (i = 0; i < NumParams; i++) {
   // Describe the parameter.
   SQLDescribeParam(hstmt, i + 1, &DataType, &ParamSize, &DecimalDigits, &Nullable);

   // Call a helper function to allocate a buffer in which to store the parameter
   // value in character form. The function determines the size of the buffer from
   // the SQL data type and parameter size returned by SQLDescribeParam and returns
   // a pointer to the buffer and the length of the buffer.
   PtrArray[i] = (char*)malloc(ParamSize);
   BufferLenArray[i] = SQL_NTS;


   // Bind the memory to the parameter. Assume that we only have input parameters.
   SQLBindParameter(hstmt, i + 1, SQL_PARAM_INPUT, SQL_C_CHAR, DataType, ParamSize,
         DecimalDigits, PtrArray[i], BufferLenArray[i],
         &LenOrIndArray[i]);

   // Prompt the user for the value of the parameter and store it in the memory
   // allocated earlier. For simplicity, this function does not check the value
   // against the information returned by SQLDescribeParam. Instead, the driver does
   // this when the statement is executed.
   strcpy((char*)PtrArray[i], "AAAAAAA");
   BufferLenArray[i] = 7;
   }
}
```

### SQLNumResultCols

SQLNumResultCols returns the number of columns in a result set.

#### Syntax

```
SQLRETURN  SQLNumResultCols (
	SQLHSTMT 		    stmt,
	SQLSMALLINT * 		col );
```

#### Arguments	

| Data Type      | Argument | In/Output | Description                                            |
| -------------- | -------- | --------- | ------------------------------------------------------ |
| SQLHSTMT       | stmt     | Input     | Statement handle                                       |
| SQLSMALLINT \* | col      | Output    | Pointer to save the number of columns in a result set. |

#### Return Values

```
SQL_SUCCESS
SQL_SUCCESS_WITH_INFO
SQL_INVALID_HANDLE
SQL_ERROR
```

#### Description

If the commands related to stmt do not return columns, SQLNumResultCols () will set 0 in *col. 

This function can be called only after SQLPrepare () or SQLExecDirect () is called. After this function is called, SQLDescribeCol (), SQLColAttribute (), SQLBindCol () or SQLGetData () can be called. 

When the command is in ready, executed, or defined status, SQLNumResultCols () can be successfully called.

#### Diagnosis

| SQLSTATE | Description                 | Comments                                                     |
| -------- | --------------------------- | ------------------------------------------------------------ |
| 08S01    | Communication channel error | Communication channel failure before the function processing is completed between the Altibase CLI driver and the database |
| HY000    | General error               |                                                              |

If SQLNumResultCols () is called after SQLPrepare () and before SQLExecute (), no SQLSTATE returned by these two functions can be returned.

#### Related Functions

```
SQLBindCol
SQLColAttribute
SQLDescribeCol	
SQLExecDirect
SQLExecute
SQLFetch
SQLGetData
SQLPrepare
SQLSetStmtAttr
```

#### Example

< Refer to: $ALTIBASE_HOME/sample/SQLCLI/demo_ex1.cpp >

```
sprintf(query,"SELECT * FROM DEMO_EX1");
if (SQLExecDirect(stmt,query, SQL_NTS) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, query);
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}           
SQLNumResultCols(stmt, &columnCount);
```

### SQLParamData

You can use this when inserting data while running command.

#### Syntax

```
SQLRETURN SQLParamData (
		SQLHSTMT   stmt,
		SQLPOINTER *value);
```

#### Arguments	

| Data Type     | Argument | In/Output | Description                                           |
| ------------- | -------- | --------- | ----------------------------------------------------- |
| SQLHSTMT      | stmt     | Input     | Command handle                                        |
| SQLPOINTER \* | value    | Out       | Pointer to save address specified in SQLBindParameter |

#### Return Values

```
SQL_SUCCESS
SQL_SUCCESS_WITH_INFO
SQL_NEED_DATA
SQL_NO_DATA
SQL_INVALID_HANDLE
SQL_ERROR
```

#### Description

This puts data while the statement is executing.

Use with SQLPutData.

#### Diagnosis

| SQLSTATE | Description               | Comments                                            |
| -------- | ------------------------- | --------------------------------------------------- |
| HY000    | General error             | No error occurs explicitly                          |
| HY001    | Memory allocation error   | This denotes to fail to allocate memory for handle. |
| HY010    | Continuous function error |                                                     |

#### Related Functions

```
SQLBindParameter
SQLExecDirect
SQLExecute
SQLPutData
```

### SQLPrepare

This prepares a SQL string for execution. 

SQLPrepareW() as a Unicode string supports same execution as SQLPrepare().

#### Syntax

```
SQLRETURN  SQLPrepare (
	SQLHSTMT 		stmt,
	SQLCHAR *		sql,
	SQLSMALLINT 		sqlLength );
```

#### Arguments

| Data Type   | Argument  | In/Out | Description                                                 |
| ----------- | --------- | ------ | ----------------------------------------------------------- |
| SQLHSTMT    | stmt      | Input  | Statement handle                                            |
| SQLCHAR \*  | sql       | Input  | SQL text string column                                      |
| SQLSMALLINT | sqlLength | Input  | The length, in bytes, of the contents of the *sql* argument |

#### Return Values

```
SQL_SUCCESS
SQL_SUCCESS_WITH_INFO
SQL_INVALID_HANDLE
SQL_ERROR
```

#### Description

An application calls SQLPrepare () to send a SQL statement to the database. The application may include more than one parameter markers (?) in the SQL statement. To include the parameter marker, an application inserts the parameter marker in the SQL character string at a proper position.

Once the statement is ready, an application calls the function. To refer to the statement, use the statement handle. The statements related to the statement handle can be executed again when an application calls SQLFreeStmt () using SQL_DROP option to release the statement or when the statement handle is used again to call SQLPrepare (), SQLExecDirect (), or catalog function such like SQLColumns (), SQLTables (). Once an application prepares the statement, an application an request information about the result set format. Calling SQLDescribeCol () after SQLPrepare () may not be as effective as calling it after SQLExecute () or SQLExecDirect ().

The ODBC data type will be inspected when the command is executed (in case not all parameters are bound.) For maximum inter-operation, an application must unbound all parameters applied to the previous SQL statement before the same command prepares a new SQL statement. This prevents errors that occur due to pervious parameters applied to new information.

#### Diagnosis

| SQLSTATE | Description                           | Comments                                                     |
| -------- | ------------------------------------- | ------------------------------------------------------------ |
| 08003    |                                       | When *stmt* is not connected or the connection is released   |
| 08S01    | Communication channel error           | Communication channel failure before the function processing is completed between the Altibase CLI driver and the database |
| HY000    | General error                         |                                                              |
| HY001    | Memory allocation error               | Cannot allocate the requested memory for the Altibase CLI driver to execute the function and complete execution. |
| HY009    | Use an invalid pointer (null pointer) | sql is a NULL pointer                                        |

#### Related Functions

```
SQLAllocHandle
SQLBindCol
SQLBindParameter
SQLEndTran
SQLExecDirect
SQLExecute
SQLRowCount
```

#### Example

< Refer to: $ALTIBASE_HOME/sample/SQLCLI/demo_ex2.cpp >

```
sprintf(query,"INSERT INTO DEMO_EX2 VALUES( ?, ?, ?, ?, ?, ? )");

/*  Prepare for a statement and bind the variable.  */
if (SQLPrepare(stmt, query, SQL_NTS) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, query);
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}
```

### SQLPrimaryKeys

SQLPrimaryKeys returns the column names that make up the primary key for a table. The driver returns the information as a result set. This function does not support returning primary keys from multiple tables in a single call.

SQLPrimarykeysW() as a Unicode string supports same execution as SQLPrimarykey().

#### Syntax

```
SQLRETURN SQLPrimaryKeys (
		SQLHSTMT	stmt,
		SQLCHAR *	cName,
		SQLSMALLINT 	cNameLength,
		SQLCHAR *	sName,
		SQLSMALLINT 	sNameLength,
		SQLCHAR *	tName,
		SQLSMALLINT 	tNameLength );
```

#### Arguments

| Data Type   | Argument      | In/Output | Description                                                  |
| ----------- | ------------- | --------- | ------------------------------------------------------------ |
| SQLHSTMT    | *stmt*        | Input     | Statement handle                                             |
| SQLCHAR \*  | *cName*       | Input     | Catalog name                                                 |
| SQLSMALLINT | *cNameLength* | Input     | The length, in bytes, of **cName*                            |
| SQLCHAR \*  | *sName*       | Input     | Schema name                                                  |
| SQLSMALLINT | *sNameLength* | Input     | The length, in bytes, of **sName*                            |
| SQLCHAR \*  | *tName*       | Input     | The table name. Cannot be a NULL pointer. tName cannot contain a string search pattern. |
| SQLSMALLINT | *tNameLength* | Input     | The length, in bytes, of **tName*                            |

#### Return Values

```
SQL_SUCCESS
SQL_SUCCESS_WITH_INFO
SQL_INVALID_HANDLE
SQL_ERROR
```

#### Description

SQLPrimaryKeys () returns the results in the format of standard result set which is sorted in order byTABLE_CAT, TABLE_SCHEM, TABLE_NAME, and KEY_SEQ. 

The search type cannot be used to define the schema-defining arguments or the table name. In many cases, calling of SQLPrimaryKeys () is mapped on the search that is complex and cost a lot. 

Therefore, the stored result set must be used instead of repeating the calling.

The following table lists the columns of the result set.

| No.  | Name        | Data Type           | Description                                            |
| ---- | ----------- | ------------------- | ------------------------------------------------------ |
| 1    | TABLE_CAT   | VARCHAR             | Null will be always returned                           |
| 2    | TABLE_SCHEM | VARCHAR             | Primary key table schema name                          |
| 3    | TABLE_NAME  | VARCHAR (NOT NULL)  | Primary key table name                                 |
| 4    | COLUMN_NAME | VARCHAR (NOT NULL)  | First primary key column name                          |
| 5    | KEY_SEQ     | SMALLINT (NOT NULL) | Column orders of the first primary key starting with 1 |
| 6    | PK_NAME     | VARCHAR             | First primary key name                                 |

[Table 2‑2] Columns Returned by SQLPrimaryKeys ()

#### Diagnosis

| SQLSTATE | Desctipiton                           | Comments                                                     |
| -------- | ------------------------------------- | ------------------------------------------------------------ |
| 08S01    | Communication channel error           | Communication channel failure before the function processing is completed between the Altibase CLI driver and the database |
| HY000    | General error                         |                                                              |
| HY009    | Invalid arguments used (null pointer) | tNameTransfer NULL pointer                                   |

#### Related Functions

```
SQLBindCol
SQLFetch
SQLStatistics
```

#### Example

< Refer to: $ALTIBASE_HOME/sample/SQLCLI/demo_meta3.cpp >

```
if (SQLPrimaryKeys(stmt,
                   NULL, 0,
                   NULL, 0,
                   (char*)"DEMO_META3", SQL_NTS) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, "SQLPrimaryKeys");
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}

SQLBindCol(stmt, 1, SQL_C_CHAR, szCatalog, STR_LEN,&cbCatalog);
SQLBindCol(stmt, 2, SQL_C_CHAR, szSchema, STR_LEN, &cbSchema);
SQLBindCol(stmt, 3, SQL_C_CHAR, szTableName, STR_LEN,&cbTableName);
SQLBindCol(stmt, 4, SQL_C_CHAR, szColumnName, STR_LEN, &cbColumnName);
SQLBindCol(stmt, 5, SQL_C_SSHORT, &KeySeq, 0, &cbKeySeq);
SQLBindCol(stmt, 6, SQL_C_CHAR, szPkName, STR_LEN, &cbPkName);
while ( (rc = SQLFetch(stmt)) != SQL_NO_DATA)
{
    if ( rc == SQL_ERROR )
    {
        execute_err(dbc, stmt, "SQLPrimaryKeys:SQLFetch");
        break;
    }
    printf("%-20s%-20s%-3d%-20s\n", szTableName,
                szColumnName, KeySeq, szPkName);
}
```

### SQLProcedureColumns

SQLProcedureColumns returns the list of input and output parameters, as well as the columns that make up the result set for the specified procedures. The driver returns the information as a result set on the specified statement. 

SQLProcedureColumnsW() as a Unicode string supports same execution as SQLProcedureColumns().

#### Syntax

```
SQLRETURN  SQLProcedureColumns (
	SQLHSTMT		stmt,
	SQLCHAR *		cName,
	SQLSMALLINT 	cNameLength,
	SQLCHAR *		sName,
	SQLSMALLINT 	sNameLength,
	SQLCHAR *		pName,
	SQLSMALLINT 	pNameLength,
	SQLCHAR * 		colName,
	SQLSMALLINT	    colNameLength );
```

#### Arguments

| Data Type   | Argument      | In/Output | Description                                                  |
| ----------- | ------------- | --------- | ------------------------------------------------------------ |
| SQLHSTMT    | stmt          | Input     | Statement handle                                             |
| SQLCHAR \*  | cName         | Input     | Procedure catalog name                                       |
| SQLSMALLINT | cNameLength   | Input     | The length, in bytes, of **cName*                            |
| SQLCHAR \*  | sName         | Input     | Procedure schema name                                        |
| SQLSMALLINT | sNameLength   | Input     | The length, in bytes, of **sName*                            |
| SQLCHAR \*  | pName         | Input     | Procedure name. Cannot be a NULL pointer. *pName* must not include the character string search pattern. |
| SQLSMALLINT | pNameLength   | Input     | The length, in bytes, of **pName*                            |
| SQLCHAR \*  | colName       | Input     | Column name                                                  |
| SQLSMALLINT | colNameLength | Input     | The length, in bytes, of **colName*                          |

#### Return Values

```
SQL_SUCCESS
SQL_SUCCESS_WITH_INFO
SQL_INVALID_HANDLE
SQL_ERROR
```

#### Description

This function is used before a statement is executed to retrieve the procedure parameters and the columns that form the result sets returned by the procedure.

SQLProcedureColumns () returns the results in the standard result set sorted in order by PROCEDURE_CAT, PROCEDURE_SCHEM, PROCEDURE_NAME, and COLUMN_TYPE.

The column names will be returned for each procedure in the following order: 

-   Name of returned value
-   Each parameter names to call the procedures (or calling order)
-   Column names of the result set returned by the procedure (or column order)

The columns returned by SQLProcedureColumns () are shown in [Table 2-3].

| Name              | No.  | Data Type           | Description                                                  |
| ----------------- | ---- | ------------------- | ------------------------------------------------------------ |
| PROCEDURE_CAT     | 1    | VARCHAR             | Always returns NULL                                          |
| PROCEDURE \_SCHEM | 2    | VARCHAR             | Procedure schema name; NULL if not applicable to the database |
| PROCEDURE \_NAME  | 3    | VARCHAR (NOT NULL)  | Procedure name                                               |
| COLUMN_NAME       | 4    | VARCHAR (NOT NULL)  | Procedure column name. The driver returns an empty string for a procedure column that does not have a name. |
| COLUMN_TYPE       | 5    | SMALLINT (NOT NULL) | Defines the procedure column as a parameter or a result set column: SQL_PARAM_INPUT: The procedure column is the input parameter. SQL_PARAM_INPUT_OUTPUT: The procedure column is the input/output parameters. SQL_PARAM_OUTPUT: The procedure column is the output parameter. |
| DATA_TYPE         | 6    | SMALLINT (NOT NULL) | SQL data type                                                |
| TYPE_NAME         | 7    | VARCHAR (NOT NULL)  | Name of the data type corresponding to the database          |
| COLUMN_SIZE       | 8    | INTEGER             | Column Size. NULL will be returned when the column size is not proper. |
| BUFFER_LENGTH     | 9    | INTEGER             | The maximum byte storing the data                            |
| DECIMAL_DIGITS    | 10   | SMALLINT            | The NULL will return the data type that cannot apply the decimal points of the string and the decimal points. |
| NUM_PREC_RADIX    | 11   | SMALLINT            | In case of the numeric data type 10: For COLUMN_SIZE and DECIMAL_DIGIT, decimal digits allowable in this string is be given. For example, DECIMAL(12,5) string can return NUM_PREC_RADIX 10, COLUMN_SIZE 12, and DECIMAL_DIGITS 5. |
| NULLABLE          | 12   | SMALLINT (NOT NULL) | SQL_NO_NullS when the procedure column does not allow NULL value, or SQL_Nullable when NULL is allowed. |
| REMARKS           | 13   | VARCHAR             | Description of the procedure column                          |
| COLUMN_DEF        | 14   | VARCHAR             | The default value of the column. If NULL was specified as the default value, this column is the word NULL, not enclosed in quotation marks. If the default value cannot be represented without truncation, this column contains TRUNCATED, with no enclosing single quotation marks. If no default value was specified, this column is NULL. The value of COLUMN_DEF can be used in generating a new column definition, except when it contains the value TRUNCATED. |
| SQL_DATA_TYPE     | 15   | SMALLINT (NOT NULL) | SQL data type                                                |
| SQL_DATETIME_SUB  | 16   | SMALLINT            | Subtype code for the Date data type. ∅ is returned for any other data type |
| CHAR_OCTET_LENGTH | 17   | INTEGER             | Maximum digits of the character string or binary data-type string. |
| ORDINAL_POSITION  | 18   | INTEGER (NOT NULL)  | Location of the order of the parameters in the procedure definition (starting with 1) |
| IS_NULLABLE       | 19   | VARCHAR             | NO : When the string does not contain the NULL <br/>YES : When the string contain the NULL |

[Table 2‑3] Columns Returned by SQLProcedureColumns ()

#### Diagnosis

| SQLSTATE | Description                           | Comments                  |
| -------- | ------------------------------------- | ------------------------- |
| HY000    | General error                         |                           |
| HY009    | Invalid arguments used (null pointer) | *CName* is a NULL pointer |

#### Related Functions

```
SQLBindCol
SQLFetch
SQLProcedures
```

#### Example

< Refer to: $ALTIBASE_HOME/sample/SQLCLI/demo_meta6.cpp >

```
if (SQLProcedureColumns(stmt,
                        NULL, 0,
                        NULL, 0,
                        "DEMO_META6_PROC", SQL_NTS,
                        NULL, 0) != SQL_SUCCESS)
{                       
    execute_err(dbc, stmt, "SQLProcedureColumns");
      SQLFreeStmt(stmt, SQL_DROP);
      return SQL_ERROR;
}

SQLBindCol(stmt, 1, SQL_C_CHAR, szCatalog, STR_LEN,&cbCatalog);
  SQLBindCol(stmt, 2, SQL_C_CHAR, szSchema, STR_LEN, &cbSchema);
  SQLBindCol(stmt, 3, SQL_C_CHAR, szProcName, STR_LEN,&cbProcName);
  SQLBindCol(stmt, 4, SQL_C_CHAR, szColumnName, STR_LEN, &cbColumnName);
  SQLBindCol(stmt, 5, SQL_C_SSHORT, &ColumnType, 0, &cbColumnType);
  SQLBindCol(stmt, 7, SQL_C_CHAR, szTypeName, STR_LEN, &cbTypeName);
  SQLBindCol(stmt, 8, SQL_C_SLONG, &ColumnSize, 0, &cbColumnSize);
  SQLBindCol(stmt, 10, SQL_C_SSHORT, &DecimalDigits, 0, &cbDecimalDigits);
  SQLBindCol(stmt, 11, SQL_C_SSHORT, &NumPrecRadix, 0, &cbNumPrecRadix);
  SQLBindCol(stmt, 18, SQL_C_SLONG, &OrdinalPosition, 0, &cbOrdinalPosition);
```

### SQLProcedures

SQLProcedures returns the list of procedure names stored in a specific database. Procedure is a generic term used to describe an executable object, or a named entity that can be invoked using input and output parameters. 

SQLProceduresW() as a Unicode string supports same execution as SQLProcedures().

#### Syntax

```
SQLRETURN  SQLProcedures (
	SQLHSTMT		stmt,
	SQLCHAR *		cName,
	SQLSMALLINT 	cNameLength,
	SQLCHAR *		sName ,
	SQLSMALLINT 	sNameLength,
	SQLCHAR *		pName,
	SQLSMALLINT 	pNameLength );
```

#### Arguments

| Data Type   | Argument    | In/Out | Description                                                  |
| ----------- | ----------- | ------ | ------------------------------------------------------------ |
| SQLHSTMT    | stmt        | Input  | Statement handle                                             |
| SQLCHAR \*  | cName       | Input  | Procedure catalog name                                       |
| SQLSMALLINT | cNameLength | Input  | The length, in bytes, of **cName*                            |
| SQLCHAR \*  | sName       | Input  | Procedure schema name                                        |
| SQLSMALLINT | sNameLength | Input  | The length, in bytes, of **sName*                            |
| SQLCHAR \*  | pName       | Input  | Procedure name. Cannot be a NULL pointer. pName must not contain the string search-patterns. |
| SQLSMALLINT | pNameLength | Input  | The length, in bytes, of **pName*                            |

#### Return Values

```
SQL_SUCCESS
SQL_SUCCESS_WITH_INFO
SQL_INVALID_HANDLE
SQL_ERROR
```

#### Description

SQLProcedures () displays the list of all procedures in the required range. A user may have or have not a privilege to use and execute these procedures. 

SQLProcedures () returns the results in the format of the standard result set format sorted in order by PROCEDURE_CAT, PROCEDURE_SCHEM, and PROCEDURE_NAME.

> Note:  SQLProcedures () may not return all procedures. An application can use the valid procedures whether the procedure is returned by SQLProcedures () or not.

| Name              | No.  | Data Type          | Description                                                  |
| ----------------- | ---- | ------------------ | ------------------------------------------------------------ |
| PROCEDURE_CAT     | 1    | VARCHAR            | Procedure catalog identifier; NULL if not applicable to the database |
| PROCEDURE \_SCHEM | 2    | VARCHAR            | Procedure schema identifier; NULL if not applicable to the database |
| PROCEDURE \_NAME  | 3    | VARCHAR (NOT NULL) | Procedure identifier                                         |
| NUM_INPUT_PARAMS  | 4    | N/A                | Reserved for future use. An application must not apply any returned data to this result string. |
| NUM_OUTPUT_PARAMS | 5    | N/A                | Reserved for future use. An application must not apply any returned data to this result string. |
| NUM_RESULT_SETS   | 6    | N/A                | Reserved for future use. An application must not apply any returned data to this result string. |
| REMARKS           | 7    | VARCHAR            | Procedure description                                        |
| PROCEDURE_TYPE    | 8    | SMALLINT           | Definition of the procedure type SQL_PT_UNKNOWN: It cannot be determined whether the procedure returns a value. SQL_PT_PROCEDURE: The returned object is a procedure; that is, it does not have a return value. SQL_PT_FUNCTION: The returned object is a function; that is, it has a return value. |

[Table 2‑4] The Column Returned by SQLProcedures ()

#### Diagnosis

| SQLSTATE | Description                           | Comments                                                     |
| -------- | ------------------------------------- | ------------------------------------------------------------ |
| 08S01    | Communication channel error           | Communication channel failure before the function processing is completed between the Altibase CLI driver and the database |
| HY000    | General error                         |                                                              |
| HY009    | Invalid arguments used (null pointer) | *CName* is a NULL pointer *sNme, pName* are NULL pointer     |

#### Related Functions

```
SQLBindCol
SQLFetch
SQLProcedureColumns
```

#### Example

< Refer to: $ALTIBASE_HOME/sample/SQLCLI/demo_meta5.cpp >

```
if (SQLProcedures(stmt,
                  NULL, 0,
                  NULL, 0,
                  NULL, 0) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, "SQLProcedures");
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}
```

### SQLPutData

The user can use this when inserting data while running command.

#### Syntax

```
SQLRETURN SQLPutData (
		SQLHSTMT 	stmt,
		SQLPOINTER 	data,
		SQLLEN 	    strLength);
```

#### Arguments

| Data Type  | Argument    | In/Output | Description            |
| ---------- | ----------- | --------- | ---------------------- |
| SQLHSTMT   | *stmt*      | Input     | Command handle         |
| SQLPOINTER | *data*      | Input     | Pointer of data buffer |
| SQLLEN     | *strLength* | Input     | Data size              |

#### Return Values

```
SQL_SUCCESS
SQL_SUCCESS_WITH_INFO
SQL_INVALID_HANDLE
SQL_ERROR
```

#### Description

This inserts data while executing a statement. This is used with SQLParamData.

#### Diagnosis

| SQLSTATE | Description               | Comments                                           |
| -------- | ------------------------- | -------------------------------------------------- |
| HY000    | General error             | No error occurs explicitly                         |
| HY001    | Memory allocation error   | This denotes to fail to allocate memory for handle |
| HY010    | Continuous function error |                                                    |

#### Related Functions

```
SQLBindParameter
SQLExecDirect
SQLExecute
SQLParamData
```

### SQLRowCount

SQLRowCount returns the number of rows affected by an UPDATE, DELETE,or INSERT statement.

#### Syntax

```
SQLRETURN  SQLRowCount (
	SQLHSTMT		stmt,
	SQLLEN *		row );
```

#### Arguments

| Data Type | Argument | In/Output | Description                       |
| --------- | -------- | --------- | --------------------------------- |
| SQLHSTMT  | stmt     | Input     | Statement handle                  |
| SQLLEN \* | row      | Output    | Pointer to save the number of row |

#### Return Values

```
SQL_SUCCESS
SQL_SUCCESS_WITH_INFO
SQL_INVALID_HANDLE
SQL_ERROR
```

#### Description

This function returns the number of rows affected by an UPDATE, INSERT or DELETE statement. For SQL statements which alter rows, such as MOVE, ENQUEUE and MERGE, the number of affected rows is returned in **row*; if no rows are affected, 0 is returned. 

If the SQL statement which was most recently executed by the input statement handle is not one listed above, or it failed to execute successfully, this function returns -1 in **row*. 

The rows in the tables affected by the SQL statement such as cascading delete operationare not included.

Before this funciton is called, SQLExecute () or SQLExecDirect () must be called.

#### Diagnosis

| SQLSTATE | Description   | Comments |
| -------- | ------------- | -------- |
| HY000    | General error |          |

#### Related Functions 

```
SQLExecDirect
SQLExecute
```

#### Example

< Refer to: $ALTIBASE_HOME/sample/SQLCLI/demo_exa5.cpp >

```
if (SQLExecute(stmt) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, query);
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}
SQLRowCount(stmt, &row_count);
```

### SQLSetConnectAttr	

SQLSetConnectAttr() sets attributes that govern aspects of connections.

SQLSetConnectAttrW() as a Unicode string supports same execution as SQLSetConnectAttr().

#### Syntax

```
SQLRETURN  SQLSetConnectAttr (
	SQLHDBC 	dbc,
	SQLINTEGER 	Attribute,
	SQLPOINTER	ValuePtr,
	SQLINTEGER 	StringLength );
```

#### Arguments

| Data Type  | Argument     | In/Output | Description                                                  |
| ---------- | ------------ | --------- | ------------------------------------------------------------ |
| SQLHDBC    | dbc          | Input     | Connection handle                                            |
| SQLINTEGER | Attribute    | Input     | Attribute to set                                             |
| SQLPOINTER | ValuePtr     | Input     | Pointer of value contaied attribute. Depending on the Attribute value, the ValuePtr will be either a 32-bit unsigned integer or a pointer indicating the Nullterminator string. <br/>SQL_ATTR_AUTOCOMMIT <br/>SQL_ATTR_CONNECTION_TIMEOUT <br/>SQL_ATTR_PORT <br/>SQL_ATTR_TXN_ISOLATION <br/>ALTIBASE_APP_INFO <br/>ALTIBASE_DATE_FORMAT |
| SQLINTEGER | StringLength | Input     | When *ValuePtr* is the character string, *StringLength* is the length of the character string or SQL_NTS. If *ValuePtr* is 32-bit integer, this argument is ignored. |

#### Return Values

```
SQL_SUCCESS
SQL_SUCCESS_WITH_INFO
SQL_INVALID_HANDLE
SQL_ERROR
```

#### Description

An application can call SQLSetConnectAttr () at any point whether the connection is allocated or released. All connections successfully set by an application and statement attribute are stored until SQLFreeHandle () is called in the current connection

| Attribute                         | Contents                                                     |
| --------------------------------- | ------------------------------------------------------------ |
| SQL_ATTR_AUTOCOMMIT               | 32-bit value to set the commit mode. SQL_AUTOCOMMIT_ON: Each SQL statement is automatically committed SQL_AUTOCOMMIT_OFF: Not automatically committed. |
| SQL_ATTR_CONNECTION_TIMEOUT       | Set timeout value to prevent blocking that may occur in select() or poll() in an unstable network |
| SQL_ATTR_PORT                     | Server port setting (32-bit Integer)                         |
| SQL_ATTR_TXN_ISOLATION            | 32-bit value that sets the transaction isolation level for the current connection referred to by dbc. |
| SQL_ATTR_ENLIST_IN_DTC            | Participate in a distributed transaction initiated by a Distributed Transaction Coordinator (DTC). To participate in a distributed transaction, set the distributed transaction's object (ITransaction \ *) as an attribute value or set SQL_DTC_DONE. SQL_DTC_DONE: If the value is set, it will be executed as a local transaction after completing participation in distributed transaction. |
| ALTIBASE_APP_INFO                 | Specify an identifier for an Altibase CLI application to obtain more detailed information on the user's session. |
| ALTIBASE_DATE_FORMAT              | Sets the date format. Supports YYYY/MM/DD HH:MI:SS as the default. |
| ALTIBASE_CONN_ATTR_IPC_FILEPATH   | If ALTIBASE_HOME is different when server and client are connected by IPC in Unix environment, the socket path of Unix domain does not match. At this time, if ALTIBASE_HOME / trc / cm-ipc file is used, Unix domain communication is possible and information of shared memory can be obtained. |
| ALTIBASE_SOCK_RCVBUF_BLOCK_RATIO  | Sets the size of the socket receive buffer in 32K increments. If the value of this property is set to 2, the size of the socket receive buffer is 64K. The default value is 0. If the maximum socket receive buffer size among the TCP kernel parameters is set to less than the socket receive buffer size set by this property value, this property may be ignored or an error may be generated depending on the OS. (For Linux OS, it corresponds to 'net.core.rmem_max' TCP kernel parameter.) |
| ALTIBASE_MESSAGE_CALLBACK         | Registers a callback function to receive a message from the server. The user can handle the received message with a callback function. For details, refer to the sample below: <$ ALTIBASE_HOME / sample / SQLCLI / demo_message.cpp> |
| ALTIBASE_GLOBAL_TRANSACTION_LEVEL | The user can specify the level of the transaction to run when using Sharding. For more information about transaction level, refer to Shard Transaction in *Sharding Manual.* |

#### Diagnosis	

| SQLSTATE | Description                                                  | Comments                                                     |
| -------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 08S01    | Communication channel error                                  | Communication channel failure before the function processing is completed between the Altibase CLI driver and the database |
| 25000    | Operation is not possible because local transaction is running | Fails when attempting to join a distributed transaction with the SQL_ATTR_ENLIST_IN_DTC attribute in NON-AUTOCOMMIT mode |
| HY000    | General error                                                |                                                              |

In case of the statement attribute, SQLSetConnectAttr () can return any SQL state returned by SQLSetStmtAttr ().

#### Related Function

```
SQLAllocHandle
```

#### Example 

< Refer to: $ALTIBASE_HOME/sample/SQLCLI/demo_tran1.cpp >

```
if (SQLSetConnectAttr(dbc, SQL_ATTR_AUTOCOMMIT,
                    (void*)SQL_AUTOCOMMIT_OFF, 0) != SQL_SUCCESS)
{              
    execute_err(dbc, SQL_NULL_HSTMT, "Autocommit OFF");
    return SQL_ERROR;
}
```

### SQLSetDescField

This specifies an attribute of descriptor. Unicode SQLSetDescFieldW() supports same execution as SQLSetDescField().

#### Syntax

```
SQLRETURN SQLSetDescField (
		SQLHDESC 	desc,
		SQLSMALLINT 	recNumber,
		SQLSMALLINT 	fieldIdentifier,
		SQLPOINTER	value,
		SQLINTEGER 	bufferLength);
```

#### Arguments

| Data Type   | Argument          | In/Out | Description                                         |
| ----------- | ----------------- | ------ | --------------------------------------------------- |
| SQLHDESC    | *desc*            | Input  | Descriptor hanlde                                   |
| SQLSMALLINT | *renNumber*       | Input  | This starts from 1 of column number.                |
| SQLSMALLINT | *fieldIdentifier* | Input  | This specifies the attribute of column to retrieve. |
| SQLPOINTER  | *value*           | Input  | Buffer pointer specifying attributes                |
| SQLINTEGER  | *bufferLength*    | Input  | Value size                                          |

#### Return Values

```
SQL_SUCCESS
SQL_SUCCESS_WITH_INFO
SQL_INVALID_HANDLE
SQL_ERROR
```

#### Description	

This specifies an attribute of descriptor. 

#### Diagnosis

| SQLSTATE | Description                     | Comments                                            |
| -------- | ------------------------------- | --------------------------------------------------- |
| HY000    | General error                   | No error occurs explicitly.                         |
| HY001    | Memory allocation error         | This denotes to fail to allocate memory for handle. |
| HY010    | Order error of calling function |                                                     |
| 07009    | Invalid descriptor index        | The value of recNumber is incorrect.                |

#### Related Functions

```
SQLBindCol
SQLBindParameter
SQLGetDescField
SQLGetDescRec
```

### SQLSetEnvAttr

SQLSetEnvAttr() sets the environment attribute for the current environment.

#### Syntax

```
SQLRETURN  SQLSetEnvAttr (
	SQLHENV 	env,
	SQLINTEGER	Attribute,
	SQLPOINTER	Value,
	SQLINTEGER	StringLength );
```

#### Argument

| Data Type  | Argument     | In/Output | Description                                                  |
| ---------- | ------------ | --------- | ------------------------------------------------------------ |
| SQLHENV    | env          | Input     | Environment handle                                           |
| SQLINTEGER | Attribute    | Input     | Environment attribute to set                                 |
| SQLPOINTER | Value        | Input     | Pointer of the value related to the Attribute. Depending on the Attribute, the Value will be either a 32-bit unsigned integer or a pointer indicating the Nullterminator string |
| SQLINTEGER | StringLength | Input     | In case the attribute is the character, it is the length of *Value. |

#### Return Values

```
SQL_SUCCESS
SQL_SUCCESS_WITH_INFO
SQL_INVALID_HANDLE
SQL_ERROR
```

#### Description

An application can call SQLSetEnvAttr () only when no connection handle is allocated in the current environment. All environment attribute successfully set in an application are stored till SQLFreeHandle () is called in the current environment.

#### Environment Attributes			

| Attribute             | Descirption                                           |
| --------------------- | ----------------------------------------------------- |
| SQL_ATTR_ODBC_VERSION | (Applied only in Win32.) SQL_OV_ODBC3 or SQL_OV_ODBC2 |

#### Diagnosis

| SQLSTATE | Description   | Comments |
| -------- | ------------- | -------- |
| HY000    | General error |          |

#### Related Function

```
SQLAllocHandle
```

### SQLSetPos

This function specifies the cursor position in a rowset.

#### Syntax

```
SQLRETURN  SQLSetPos (
	SQLHSTMT 	stmt,
	SQLSETPOSIROW 	rowNumber,
	SQLUSMALLINT 	operation,
	SQLUSMALLINT 	lockType);
```

#### Arguments

| Data Type     | Argument  | In/Output | Description                                                  |
| ------------- | --------- | --------- | ------------------------------------------------------------ |
| SQLHSTMT      | stmt      | Input     | Statement handle                                             |
| SQLSETPOSIROW | rowNumber | Input     | Position of the row in the rowset on which the operation specified by the operation argument is to be performed. Starts from 1. For 0, the operation applies to every row of the rowset. |
| SQLUSMALLINT  | operation | Input     | Operation to be performed. One of the following can be used: <br/>SQL_POSITION <br/>SQL_REFRESH <br/>SQL_UPDATE <br/>SQL_DELETE |
| SQLUSMALLINT  | lockType  | Input     | Lock type. Currently not supported                           |

#### Return Values

```
SQL_SUCCESS
SQL_SUCCESS_WITH_INFO
SQL_NEED_DATA
SQL_STILL_EXECUTING
SQL_INVALID_HANDLE
SQL_ERROR 
```

#### Description

SQLSetPos specifies the cursor position in the rowset, and enables an application to refresh, update or delete data of that position. *rowNumber* specifies the number of the row in the rowset on which the operation is to be performed. If *rowNumber* is 1, the operation is performed on the first row in the rowset; if rowNumber is 0, the operation is performed on every row in the rowset. If *operation* is SQL_POSITION, however, *rowNumber* cannot be 0.

A cursor position is required for the following operations:

-   Calls to SQLGetData 
-   Calls to SQLSetPos with the SQL_DELETE, SQL_REFRESH, or SQL_UPDATE option

For the initial fetch after executing a SELECT statement, the cursor position in the rowset is 1. 

The following options are provided for the operation argument of the SQLSetPos function:

| Option       | Description                                                  |
| ------------ | ------------------------------------------------------------ |
| SQL_POSITION | The driver positions the cursor on the row specified by *rowNumber.* |
| SQL_REFRESH  | The driver positions the cursor on the row specified by *rowNumber*, and refreshes data in the rowset buffer for that row. If 0 is specified for *rowNumber*, data of every row in the rowset is refreshed. If the driver detects a HOLE, SQL_ROW_DELETED is returned as the row status value. For SENSITIVE type cursors, the latest data from the database is retrieved; for non-SENSITIVE type cursors, existing data from the cache is retrieved. |
| SQL_UPDATE   | The driver positions the cursor on the row specified by *rowNumber*, and updates data of the database with the data of that row in the rowset buffer. If 0 is specified for rowNumber, the database is updated with all of the data in the rowset. If the length/indicator argument of SQLBindCol is set to SQL_COLUMN_IGNORE, the column is not updated. If a row which is specified as SQL_ROW_IGNORE for the SQL_ATTR_ROW_OPERATION_PTR statement attribute exists in the row operation array, that row is ignored and operations are performed on the next row. |
| SQL_DELETE   | The driver positions the cursor on the row specified by *rowNumber*, and deletes the row. If *rowNumber* is set to 0, every row in the rowset is deleted. If a row which is specified as SQL_ROW_IGNORE for the SQL_ATTR_ROW_OPERATION_PTR statement attribute exists in the row operation array, that row is ignored and operations are performed on the next row. |

##### Using SQLSetPos 

When calling SQLSetPos, write the program in the following order:

1. Call SQLBindCol to bind buffers

2. Execute a SELECT query statement with SQLExecDirect, etc. 

3. To call SQLSetPos with the SQL_UPDATE option, 

   A. Change the data of the bound buffer to the desired value. 

   B. To ignore a certain column, call SQLBindCol again with the length/indicator set to SQL_COLUMN_IGNORE. 

   C. To exclude a certain row from the operation, set the SQL_ATTR_ROW_OPERATION statement attribute and its corresponding array element to SQL_ROW_IGNORE

4. Call SQLSetPos 

   A. If the SQL_ATTR_ROW_STATUS_PTR statement attribute is set to a status array, the operational result of each row (whether or not it is SQL_ROW_DELETED) can be checked.

#### Diagnosis

| SQLSTATE | Description                                                  | Comments                                                     |
| -------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| HY000    | General error                                                |                                                              |
| HY001    | Memory allocation error                                      | Memory required for Altibase CLI driver to process and complete the function cannot be allocated. |
| 08S01    | Communication channel error(data transmission failure)       | Communication channel error occurred before function process between Altibase CLI driver and DB completed. |
| 08003    |                                                              | *stmt* was released or connection was not in a connected state. |
| HY010    | Function sequence error                                      | Given *stmt* cannot process the function. Asynchronous operations are unsupported. |
| 24519    | Hole detected but no indicator variable provided             |                                                              |
| 01S01    | Error(s) in row(s)                                           | The *rowNumber* value was 0, and an error occurred in one or more rows during operation. |
| HY107    | Row value out of range                                       | The value specified for rowNumber is larger than the number of rows in the rowset. |
| HY109    | Invalid cursor position                                      |                                                              |
| 01001    | Cursor operation conflict                                    |                                                              |
| HY024    | Invalid array size                                           |                                                              |
| 21S02    | Type and number of column in derived table does not match column list |                                                              |
| HY092    | Invalid attribute/option                                     |                                                              |
| 24000    | Invalid cursor state                                         |                                                              |

#### Related Functions

```
SQLBindCol
SQLBulkOperations
SQLCancel
SQLFetchScroll
SQLGetDescField
SQLGetDescRec
SQLSetDescField
SQLSetDescRec
SQLSetStmtAttr
```

### SQLSetStmtAttr

SQLSetStmtAttr() sets the attribute related to the statement handle. 

SQLSetStmtAttrW() as a Unicode string supports same execution as SQLSetStmtAttr().

#### Syntax

```
SQLRETURN  SQLSetStmtAttr (
	SQLHSTMT 	stmt,
	SQLINTEGER	Attribute,
	SQLPOINTER	param,
	SQLINTEGER	StringLength );
```

#### Arguments

| Data Type  | Argument     | In/Output | Description                                                  |
| ---------- | ------------ | --------- | ------------------------------------------------------------ |
| SQLHENV    | stmt         | Input     | Statement handle                                             |
| SQLINTEGER | Attribute    | Input     | Attribute to set, Supported attribute value: SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_SCROLLABLE, SQL_ATTR_CURSOR_SENSITIVITY, SQL_ATTR_CURSOR_TYPE, SQL_ATTR_PARAM_BIND_TYPE, SQL_ATTR_PARAM_STATUS_PTR, SQL_ATTR_PARAMS_PROCESSED_PTR, SQL_ATTR_PARAMS_ROW_COUNTS_P TR, SQL_ATTR_PARAMS_SET_ROW_COUN TS, SQL_ATTR_PARAMSET_SIZE, SQL_ATTR_PREFETCH_ROWS, SQL_ATTR_ROW_ARRAY_SIZE, SQL_ATTR_ROW_BIND_TYPE, SQL_ATTR_ROW_STATUS_PTR, SQL_ATTR_ROWS_FETCHED_PTR ALTIBASE_STMT_ATTR_ATOMIC_ARR AY, SQL_ATTR_FETCH_BOOKMARK_PTR, SQL_ATTR_ROW_OPERATION_PTR, SQL_ATTR_USE_BOOKMARKS, SQL_ATTR_CURSOR_HOLD ALTIBASE_PREPARE_WITH_DESCRIBE PARAM Attribute value which is not currently being supported: SQL_ATTR_APP_PARAM_DESC, SQL_ATTR_APP_ROW_DESC, SQL_ATTR_ASYNC_ENABLE, SQL_ATTR_ENABLE_AUTO_IPD, SQL_ATTR_IMP_PARAM_DESC, SQL_ATTR_IMP_ROW_DESC, SQL_ATTR_KEYSET_SIZE, SQL_ATTR_MAX_LENGTH, SQL_ATTR_METADATA_ID, SQL_ATTR_NOSCAN, SQL_ATTR_PARAM_BIND_OFFSET_PTR , SQL_ATTR_PARAM_OPERATION_PTR, SQL_ATTR_QUERY_TIMEOUT, SQL_ATTR_RETRIEVE_DATA, SQL_ATTR_ROW_BIND_OFFSET_PTR, SQL_ATTR_ROW_NUMBER, SQL_ATTR_SIMULATE_CURSOR |
| SQLPOINTER | param        | Input     | Pointer of the value related to the Attribute Depending on the pointer, Attribute, the param will be a 32-bit integer, the pointer of the Null-terminator, the character string’s pointer, the binary pointer, or the value defined in the ODBC. If Attribute is the unique value of the ODBC, param is the integer number with a sign. |
| SQLINTEGER | StringLength | Input     | If Attribute has been defined in the ODBC and param indicates the character string or binary buffer, this argument must be the byte length of *param. If Attribute has been defined in the ODBC and param is an integer, this argument is ignored. |

#### Return Values

```
SQL_SUCCESS	
SQL_SUCCESS_WITH_INFO
SQL_INVALID_HANDLE	
SQL_ERROR
```

#### Description

The command option for stmt is valid until the option is changed by calling of SQLSetStmtAttr () or till stmt is removed by calling of SQLFreeHandle (). Handle release method: Calling SQL_CLOSE, SQL_UNBIND, or SQL_RESET_PARAMS with SQLFreeStmt () does not reset the statement attribute. 

To use a column-wise binding, set SQL_ATTR_PARAM_BIND_TYPE in Arguments Attribute of an application function SQLSetStmtAttr() and set SQL_PARAM_BIND_BY_COLUMN in param. ARRAY_SIZE changes only PARAM_SIZE at every execution moment. PARAM_STATUS_PTR is the vaule to return if each column will be executed, and specifies SQLSMALLINT array. If succeeds, SQL_SUCCESS, SQL_SUCCESS_WITH_INFO will be returned, and if fails, then SQL_PARAM_UNUSED will be returned respectively. 

For Macro values: SQL_PARAM_SUCCESS is 0SQL_PARAM_ERROR is 5, SQL_PARAM_SUCCESS_WITH_INFO is 6SQL_PARAM_UNUSED is 7

```
SQLSetStmtAttr(stmt, SQL_ATTR_PARAM_BIND_TYPE, SQL_PARAM_BIND_BY_COLUMN);
SQLSetStmtAttr(stmt, SQL_ATTR_PARAMSET_SIZE, ARRAY_SIZE, 0);
SQLSetStmtAttr(stmt, SQL_ATTR_PARAM_STATUS_PTR, ParamStatusArray, 0);
```

Designates the pointer of the variables to store the number of columns processed by PARAMS_PROCESSED_PTR. The pointer type of SQLINTEGER. Then, execute SQLBindParameter () like before.

```
SQLSetStmtAttr(stmt, SQL_ATTR_PARAMS_PROCESSED_PTR, &ParamsProcessed, 0);
```

Then, executing SQLBINDParameter().

When using the row-wise binding, define the size of the structure in PARAM_Bind_Type, unlike in the column-wise binding.

```
SQLSetStmtAttr(stmt, SQL_ATTR_PARAM_BIND_TYPE, sizeof(struct…));
SQLSetStmtAttr(stmt, SQL_ATTR_PARAMSET_SIZE, ARRAY_SIZE, 0);
SQLSetStmtAttr(stmt, SQL_ATTR_PARAM_STATUS_PTR, ParamStatusArray, 0);
SQLSetStmtAttr(stmt, SQL_ATTR_PARAMS_PROCESSED_PTR, &ParamsProcessed, 0);
```

Then, executing SQLBINDParameter().

**Statement Attributes**

| Attribute                           | Contents                                                     |
| ----------------------------------- | ------------------------------------------------------------ |
| SQL_ATTR_CONCURRENCY                | SQLUINTEGER value specifying the temporary processing of the cursor: SQL_CONCUR_READ_ONLY: The cursor supports readonly. Updating is not allowed. SQL_CONCUR_ROWVER: The concurrency is controlled with row versions. SQL_CONCUR_LOCK and SQL_CONCUR_VALUES are not supported. |
| SQL_ATTR_CURSOR_SCROLLABLE          | The 32-bit integer value which specifies whether or not the open cursor associated with the statement handle is scrollable. |
| SQL_ATTR_CURSOR_SENSITIVITY         | The 32-bit integer value which specifies whether or not data modified by another cursor is visible to the open cursor associated with the statement handle. SQL_INSENSITIVE or SQL_SENSITIVE is supported; SQL_UNSPECIFIED is not supported. |
| SQL_ATTR_CURSOR_TYPE                | SQLUINTEGER indicating the cursor type. SQL_CURSOR_FORWARD_ONLY: The cursor only proceeds forward. SQL_CURSOR_STATIC: The data located in the result set are static. SQL_CURSOR_KEYSET_DRIVEN: The membership and order of rows included in the cursor are fixed. The Altibase CLI driver supports pure keyset-driven cursors. The SQL_KEYSET_SIZE statement attribute is ignored. |
| SQL_ATTR_PARAM_BIND_TYPE            | Setting value which is necessary for array binding To retrieve the data by the column-wise binding, SQL_PARAM_BIND_BY_COLUMN (default) is set in this field. To retrieve the data by the row-wise binding, the length of the structure or the length of the buffer to which the dynamic parameter will be bound will be set. This length must include the bound parameter space. |
| SQL_ATTR_PARAM_STATUS_PTR           | This field is requested only when PARAMSET_SIZE is higher than 1. Status values are as follows:<br/>SQL_PARAM_SUCCESS: A SQL statement has been successfully executed. The macro value is 0.<br/>SQL_PARAM_SUCCESS_WITH_INFO: A SQL statement has been successfully executed.: however, the warning data can be viewed from the diagnosis data structure. The macro value is 5. <br/> SQL_PARAM_ERROR: Error occurs during the execution of parameters. additional error information can be viewed on the diagnosis data structure. The macro value is 6. <br/>SQL_PARAM_UNUSED: This parameter set is not used partly because an error has occurred preventing the previous parameter from further proceeding. The macro value is 7. |
| SQL_ATTR_PARAMS_PROCESSED_PTR       | (Necessary for array binding) Indicates the buffer that return the number of parameters including the errors. In case of the NULL pointer, no data will be returned. If SQL_SUCCESS or SQL_SUCCESS_WITH_INFO is not returned upon calling of SQLExecDirect () or SQLExecute (), the contents of the buffer will not be defined. |
| SQL_ATTR_PARAMS_ROW_COUNTS_PTR      | (Necessary for array binding) Sets the buffer that returns the following values as the result of SQLExecute to array binding. SQL_SUCCESS: When a SQL statement was successfully executed for all array elements SQL_ERROR When even one array element fails to execute SQL statement SQL_NO_DATA: When no array element was changed (inputted or deleted) |
| SQL_ATTR_PARAMS_SET_ROW_COUNTS      | (Necessary for array binding) SQL_ROW_COUNTS_ON: Returns the number of records changed by each array element. In other words, if there are changed records, the number of records will be returned. If there is no record changed, 0 will be returned. In case an error occurs, SQL_USHRT_MAX (65534) will be returned. SQL_ROW_COUNTS_OFF: Existing behaviors of attribute SQL_ATTR_PARAM_STATUS_PTR will be maintained. |
| SQL_ATTR_PARAMSET_SIZE              | (Necessary for array binding) SQLUINTEGER value that indicates the number of values for each parameter. |
| SQL_ATTR_PREFETCH_ROWS              | Specifies the number of rows to fetch from the server in one fetch operation. If this attribute is set to 0, the CLI driver fetches the maximum size of data that can be contained in one network packet from the server. A value between 0 and 2147483647 can be specified for this attribute. |
| SQL_ATTR_ROW_ARRAY_SIZE             | (Necessary setting value at the time of the array fetch in the SELECT statement) SQLUINTEGER that indicates the number of rows returned by calling each SQLFetch (). |
| SQL_ATTR_ROW_BIND_TYPE              | (Necessary setting value at the time of the array fetch in the SELECT statement) SQLUINTEGER that sets the direction of the binding to be used upon calling of SQLFetch (). The column-wise binding is searched by setting SQL_BIND_BY_COLUMN. The row-wise binding searches the data by setting the length of the structure or the length of the buffer to which the results columns will be bound. In case the length is specified, the space for the columns to be bound must be included. |
| SQL_ATTR_ROW_STATUS_PTR             | (Necessary setting value at the time of the array fetch in the SELECT statement) The size of the array is same as the number of rows of the row set. In this attribute, the NULL pointer can be set. In this case, the Altibase CLI driver does not return the column status value. |
| SQL_ATTR_ROWS_FETCHED_PTR           | (Necessary setting value at the time of the array fetch in the SELECT statement) SQLUINTEGER* value indicating the buffer that returns the number of fetched rows after SQLFetch () is called |
| ALTIBASE_STMT_ATTR_ATOMIC_ARRAY     | This is Altibase only attribute indicating to execute Atomic Array Insert. Array Insert can execute the entire statements respectively, whereas Atomic Array Insert can execute several statements at one execution and this results in them executed as a single statement in other words. You may specify ALTIBASE_STMT_ATTR_ATOMIC_ARRAY in Attribute and SQL_TRUE/SQL_FALSE in the param argument. If you choose SQL_TRUE, you can execute Atomic Array Insert. However, you must specify Array Size in order that Atomic Array Insert has better performance than the existing Array Insert does.(SQL_ATTR_PARAMSET_SIZE) And you can save result values with using the following attributes. SQL_ATTR_PARAM_STATUS_PRT : Real result values are saved only in the first row and the rest is successfully processed. SQL_ATTR_PARAMS_PROCESSED_PTR : Real result values are saved only in the first row and the rest of them are ignored. |
| SQL_ATTR_FETCH_BOOKMARK_PTR         | The pointer which points to a buffer which stores a binary bookmark value. When SQLFetchScroll is called with SQL_FETCH_BOOKMARK, the driver scrolls the row using the bookmark value set for this attribute. The default value of this attribute is the null pointer. The bookmark value set for this attribute is not used for delete, update or fetch by bookmark operations using SQLBulkOperations; SQLBulkOperations uses bookmarks cached in rowset buffers. |
| SQL_ATTR_ROW_OPERATION_PTR          | The pointer which points to the array of SQLUSMALLINT values in order to specify which row to ignore or operate on during bulk operations using SQLSetPos. SQL_ROW_IGNORE: Row to be excluded from bulk operations. SQL_ROW_PROCEED: Row to be included in bulk operations. The value of this array is not applied during SQLBulkOperations. |
| SQL_ATTR_USE_BOOKMARKS              | The SQLULEN value that specifies whether or not to use bookmarks. SQL_UB_OFF: The default value SQL_UB_ON or SQL_UB_FIXED: Bookmarks with a fixed length of 4 bytes are used. SQL_UB_VARIABLE: Bookmarks of variable length are used. |
| SQL_ATTR_CURSOR_HOLD                | The SQLULEN value which controls the effect of transaction completion on the open cursor. SQL_CURSOR_HOLD_ON: The cursor is not closed when the transaction is committed SQL_CURSOR_HOLD_OFF: The cursor is closed when the transaction is committed. The default value is SQL_CURSOR_HOLD_OFF. |
| ALTIBASE_PREFETCH_ASYNC             | Improving fetch performance by performing prefetch asynchronously. Only available for TCP and SSL connections. ALTIBASE_PREFETCH_ASYNC_OFF: Performs a prefetch synchronously (default). ALTIBASE_PREFETCH_ASYNC_PREFERRED: Performs a prefetch asynchronously. Asynchronous prefetch can be set for each statement, but only one statement per connection is performed asynchronously. |
| ALTIBASE_PREFETCH_AUTO_TUNING       | If a prefetch is performed asynchronously, specify whether to auto-tuning according to the network status. Auto-tuning is a function that automatically adjusts the number of prefetch rows according to network conditions. This feature is only available on Linux. ALTIBASE_PREFETCH_AUTO_TUNING_OFF: Do not use auto-tuning (default on non-Linux OS) ALTIBASE_PREFETCH_AUTO_TUNING_ON: Use auto-tuning. (Default on Linux) |
| ALTIBASE_PREPARE_WITH_DESCRIBEPARAM | This property is to reduce network I / O cost by requesting parameter information when preparing. If you need parameter information, you can use it to improve performance. ALTIBASE_PREPARE_WITH_DESCRIBEPARAM_OFF: Do not request parameter information when preparing. (Default) ALTIBASE_PREPARE_WITH_DESCRIBEPARAM_ON: Request parameter information when preparing together. |

#### Diagonsis

| SQLSTATE | Description                                                 | Comments                                                     |
| -------- | ----------------------------------------------------------- | ------------------------------------------------------------ |
| HY000    | General error                                               |                                                              |
| 24000    | Invalid cursor state                                        |                                                              |
| HY010    | Funciton sequence error                                     |                                                              |
| HY011    | Attribute cannot be set now                                 |                                                              |
| HY013    | Memory management error                                     |                                                              |
| HYC00    | Use of unsupported attribute                                | The value specified for the argument *Attribute* is not supported by the driver. |
| HY009    | Invalid use of null pointer                                 |                                                              |
| HY017    | Invalid use of an automatically allocated descriptor handle |                                                              |
| 01S02    | Option value changed                                        |                                                              |
| HY024    | Invalid attribute value                                     | The value specified for the given *Attribute* is invalid.    |
| HY024    | Invalid array size                                          |                                                              |

#### Example

< Refer to: $ALTIBASE_HOME/sample/SQLCLI/demo_ex4.cpp >

```
SQLSetStmtAttr(stmt, SQL_ATTR_PARAM_BIND_TYPE, (void*)sizeof(demo_ex4_data), 0);
SQLSetStmtAttr(stmt, SQL_ATTR_PARAMSET_SIZE, (void*)10, 0);
SQLSetStmtAttr(stmt, SQL_ATTR_PARAMS_PROCESSED_PTR,(void*) &processed_ptr, 0);
SQLSetStmtAttr(stmt, SQL_ATTR_PARAM_STATUS_PTR, (void*)status, 0);
You may use Automic Array Insert.
SQLSetStmtAttr(stmt, SQL_ATTR_PARAMSET_SIZE, (SQLPOINTER) array_size, 0); // Specify Array Size.
SQLSetStmtAttr(stmt, ALTIBASE_STMT_ATTR_ATOMIC_ARRAY, (SQLPOINTER) SQL_TRUE, 0); // Specify Atomic attribute.
The following is an example code which specifies the cursor type.
SQLAllocStmt(sDbc, &sStmt);
SQLSetStmtAttr(sStmt, SQL_ATTR_CURSOR_TYPE, (SQLPOINTER) SQL_CURSOR_KEYSET_DRIVEN, NULL);
SQLSetStmtAttr(sStmt, SQL_ATTR_ROW_STATUS_PTR, (SQLPOINTER) sRowStatus, NULL);

/* ... */

SQLExecDirect(sStmt, (SQLCHAR *)"SELECT t1.* FROM t1", SQL_NTS);
while (1)
{
	sRC = SQLFetch(sStmt);
	if (! SQL_SUCCEEDED(sRC))
	{
	break;
	}
	if (sRowStatus == SQL_ROW_DELETED)
	{
	/* hole */
	}
	else
	{
	/* todo */
	}
}
...
```

### SQLSpecialColumns

SQLSpecialColumns retrieves the following information about columns within a specified table: 

-   The optimal set of columns that uniquely identifies a row in the table. 
-   Columns that are automatically updated when any value in the row is updated by a transaction.

SQLSpecialColumnsW() as a Unicode string supports same execution as SQLSpecialColumns().

#### Syntax

```
SQLRETURN  SQLSpecialColumns (
	SQLHSTMT 		stmt,
	SQLSMALLINT		fColType,
	SQLCHAR *		szTableQual,
	SQLSMALLINT		cbTableQual,
	SQLCHAR *		szTableOwner,
	SQLSMALLINT     cbTableOwner,
	SQLCHAR *		szTableName,
	SQLSMALLINT		cbTableName,
	SQLSMALLINT		fScope,
	SQLSMALLINT 	fNullable );
```

#### Arguments

| Data Type   | Argument     | In/Output | Description                                                  |
| ----------- | ------------ | --------- | ------------------------------------------------------------ |
| SQLHSTMT    | stmt         | Input     | Statement handle                                             |
| SQLSMALLINT | fColType     | Input     | Type of the column to be returned SQL_BEST_ROWID: Returns the optimal column that uniquely identify the rows in the table by searching column value(s). |
| SQLCHAR \*  | szTableQual  | Input     | Null will be always returned.                                |
| SQLSMALLINT | cbTableQual  | Input     | The length, in bytes, of *szTableQual                        |
| SQLCHAR \*  | szTableOwner | Input     | Schema name                                                  |
| SQLSMALLINT | cbTableOwner | Input     | The length, in bytes, of *szTableOwner                       |
| SQLCHAR \*  | szTableName  | Input     | The table name. Cannot be a NULL pointer.                    |
| SQLSMALLINT | cbTableName  | Input     | The length, in bytes, of *szTableName                        |
| SQLSMALLINT | fScope       | Input     | Not used                                                     |
| SQLSMALLINT | fNullable    | Input     | Not used (Does not allow NULL data because the corresponding columns are returned to the primary keys.) |

#### Return Values

```
SQL_SUCCESS
SQL_SUCCESS_WITH_INFO
SQL_INVALID_HANDLE
SQL_ERROR
```

#### Description

When *fColType* is SQL_BEST_ROWID, SQLSpecialColumns () returns column(s) that uniquely identify each row in the table. These columns can be used in select-list or Where clause.

SQLSpecialColumns () is used to return these columns because SQLColumns () does not return the columns that are automatically updated when columns or rows are updated by the transaction. 

If there are no columns that uniquely identifies each row in the table, SQLSpecialColumns () will return the row set without rows. To subsequently call SQLFetch () on the command syntax, return SQL_NO_DATA. 

When the fact that the database does not support *fColType, fScope*, and *fNullable* arguments is stated, SQLSpecialColumns () will return the empty result set.

| Name           | No.  | Data Type           | Description                                                  |
| -------------- | ---- | ------------------- | ------------------------------------------------------------ |
| SCOPE          | 1    | SMALLINT            | SQL_SCOPE_SESSION value is fixed to 2.                       |
| COLUMN_NAME    | 2    | VARCHAR (NOT NULL)  | Column Name.As for the unnamed string, Altibase CLI driver returns the empty character string. |
| DATA_TYPE      | 3    | SMALLINT (NOT NULL) | SQL data type                                                |
| TYPE_NAME      | 4    | VARCHAR (NOT NULL)  | Character string representing the name of the data type corresponding to DATA_TYPE. |
| COLUMN_SIZE    | 5    | INTEGER             | Column Size. NULL will be returned when the string size is not proper. |
| BUFFER_LENGTH  | 6    | INTEGER             | The maximum byte storing the data                            |
| DECIMAL_DIGITS | 7    | SMALLINT            | The NULL will return the data type that cannot apply the decimal points of the column and the decimal points. |
| PSEUDO_COLUMN  | 8    | SMALLINT            | Maximum digits of the character of binary datatype string. For other data types, NULL will be returned. |

#### Diagnosis

| SQLSTATE | Description                           | Comments                                                     |
| -------- | ------------------------------------- | ------------------------------------------------------------ |
| 08S01    | Communication line failure            | Communication channel failure before the function processing is completed between the Altibase CLI driver and the database |
| HY009    | Use an invalid pointer (null pointer) | *szTableName* is a NULL pointer.                             |

#### Related Functions

```
SQLBindCol
SQLColumns
SQLFetch
SQLPrimaryKeys
```

#### Example

< Refer to: $ALTIBASE_HOME/sample/SQLCLI/demo_meta7.cpp >

```
if (SQLSpecialColumns(stmt, 0,
                          NULL, 0,
                          NULL, 0,
                          "DEMO_META7", SQL_NTS,
                          NULL, 0) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, "SQLColumns");
      SQLFreeStmt(stmt, SQL_DROP);
      return SQL_ERROR;
}

  SQLBindCol(stmt, 2, SQL_C_CHAR, szColumnName, STR_LEN, &cbColumnName);
  SQLBindCol(stmt, 3, SQL_C_SSHORT, &DataType, 0, &cbDataType);
  SQLBindCol(stmt, 4, SQL_C_CHAR, szTypeName, STR_LEN, &cbTypeName);
  SQLBindCol(stmt, 5, SQL_C_SLONG, &ColumnSize, 0, &cbColumnSize);
  SQLBindCol(stmt, 6, SQL_C_SLONG, &BufferLength, 0, &cbBufferLength);
  SQLBindCol(stmt, 7, SQL_C_SSHORT, &DecimalDigits, 0, &cbDecimalDigits);
```

### SQLStatistics

SQLStatistics retrieves a list of statistics about a single table and the indexes associated with the table. The driver returns the information as a result set. 

SQLStatisticsW() as a Unicode string supports same execution as SQLStatistics().

#### Syntax

```
SQLRETURN  SQLStatistics (
	SQLHSTMT 		stmt,
	SQLCHAR *		cName,
	SQLSMALLINT		cNameLength,
	SQLCHAR *		sName,
	SQLSMALLINT 	sNameLength,
	SQLCHAR *		tName,
	SQLSMALLINT		tNameLength,
	SQLSMALLINT		unique,
	SQLSMALLINT 	reserved );
```

#### Arguments

| Data Type   | Argument    | In/Ouput | Description                                  |
| ----------- | ----------- | -------- | -------------------------------------------- |
| SQLHSTMT    | stmt        | Input    | Statement handle                             |
| SQLCHAR \*  | cName       | Input    | Catalog name                                 |
| SQLSMALLINT | cNameLength | Input    | The length, in bytes, of **cName*            |
| SQLCHAR \*  | sName       | Input    | Schema nam                                   |
| SQLSMALLINT | sNameLength | Input    | The length, in bytes, of **sName*            |
| SQLCHAR \*  | tName       | Input    | The table name. Cannot be a NULL pointer.    |
| SQLSMALLINT | tNameLength | Input    | The length, in bytes, of **tName*            |
| SQLSMALLINT | unique      | Input    | index type:SQL_INDEX_UNIQUE or SQL_INDEX_ALL |
| SQLSMALLINT | reserved    | Input    | Not used                                     |

#### Return Values

```
SQL_SUCCESS
SQL_SUCCESS_WITH_INFO
SQL_INVALID_HANDLE
SQL_ERROR
```

#### Description

returns information about a single table as a standard result set, ordered by NON_UNIQUE, TYPE, INDEX_QUALIFIER, INDEX_NAME, and ORDINAL_POSITION. The result set combines the statistical information of the table and the data for index.

| Column Name      | No.  | Data Type           | Description                                                  |
| ---------------- | ---- | ------------------- | ------------------------------------------------------------ |
| TABLE_CAT        | 1    | VARCHAR             | Null will be always returned.                                |
| TABLE_SCHEM      | 2    | VARCHAR             | Schema name including TABLE_NAME                             |
| TABLE_NAME       | 3    | VARCHAR (NOT NULL)  | Table name of the table to which the statistic or index applies. |
| NON_UNIQUE       | 4    | SMALLINT            | Indicates whether the index prohibits duplicate values: SQL_TRUE if the index values can be nonunique. SQL_FALSE if the index values must be unique. NULL is returned if TYPE is SQL_TABLE_STAT. |
| INDEX_QUALIFIER  | 5    | VARCHAR             | An empty character string is returned.                       |
| INDEX_NAME       | 6    | VARCHAR             | Index name; NULL data will be returned when the TYPE is SQL_TABLE_STAT. |
| TYPE             | 7    | SMALLINT (NOT NULL) | TYPE of the returned data SQL_TABLE_STAT: Indicates whether the statistical data for the table are displayed SQL_INDEX_BTREE: Indicates B-Tree index. SQL_INDEX_HASHED: Indicates the hashed index. SQL_INDEX_OTHER : Indicates other index types. (T-Tree) |
| ORDINAL_POSITION | 8    | SMALLINT            | Position of the columns in order in the index. (Starting with 1) NULL data will be returned when the TYPE is SQL_TABLE_STAT |
| COLUMN_NAME      | 9    | VARCHAR             | Column name. If the column is expression (e.g. SALARY + BENEFITS), the expression will be returned. If the expression cannot be determined, the empty character string will be returned. Null data will be returned when the TYPE is SQL_TABLE_STAT. |
| ASC_OR_DESC      | 10   | CHAR(1)             | Column sorting order. A: In ascending orders, D In descending orders, If the database does not support the sorting orders and the TYPE is SQL_TABLE_STAT, NULL data will be returned |
| CARDINALITY      | 11   | INTEGER             | Table or index order. When the TYPE is SQL_TABLE_STAT, the row number will be returned. If the TYPE is not SQL_TABLE_STAT, the unique number of the index will be returned. If the database does not support the TYPE, NULL data will be returned. |
| PAGES            | 12   | INTEGER             | Page number used to store data in the index or table. If the TYPE is SQL_TABLE_STAT, this column will include the number of pages used to define the table. If the TYPE is not SQL_TABLE_STAT, this column contains the number of pages used to store the index. If the database does not support the TYPE, NULL data returns. |
| FILTER_CONDITION | 13   | VARCHAR             | In case of the filtered index, this column will have the filtering conditions. 30000; filter" conditions cannot be decided, this column is an empty character string. Null In case the filter has not been faltered. When it is not possible to decide whether the index has been filtered or the TYPE is SQL_TABLE_STAT. |

[Table 2‑5] Column returned by SQLStatistics ()

#### Diagnosis	

| SQLSTATE | Description                           | Comments                                                     |
| -------- | ------------------------------------- | ------------------------------------------------------------ |
| 08S01    | Communication channel error           | Communication channel failure before the function processing is completed between the Altibase CLI driver and the database |
| HY000    | General error                         |                                                              |
| HY009    | Use an invalid pointer (null pointer) | tName is a NULL pointer <br/>cName is a NULL pointer<br/>sName is a NULL pointer |

#### Related Functions

```
SQLBindCol
SQLFetch
SQLPrimaryKeys
```

#### Example

< Refer to:  $ALTIBASE_HOME/sample/SQLCLI/demo_meta4.cpp >

```
if (SQLStatistics(stmt,NULL, 0,
                      NULL, 0,
                      "DEMO_META4", SQL_NTS,
                      SQL_INDEX_ALL, 0) != SQL_SUCCESS)
    {
        execute_err(dbc, stmt, "SQLStatistics");
        SQLFreeStmt(stmt, SQL_DROP);
        return SQL_ERROR;
    }

    SQLBindCol(stmt, 2, SQL_C_CHAR, szSchema, STR_LEN, &cbSchema);
    SQLBindCol(stmt, 3, SQL_C_CHAR, szTableName, STR_LEN,&cbTableName);
    SQLBindCol(stmt, 4, SQL_C_SSHORT, &NonUnique, 0, &cbNonUnique);
    SQLBindCol(stmt, 6, SQL_C_CHAR, szIndexName, STR_LEN, &cbIndexName);
    SQLBindCol(stmt, 8, SQL_C_SSHORT, &OrdinalPosition, 0, &cbOrdinalPosition);
    SQLBindCol(stmt, 9, SQL_C_CHAR, szColumnName, STR_LEN, &cbColumnName);
    SQLBindCol(stmt, 10, SQL_C_CHAR, szAscDesc, 2, &cbAscDesc);
```

### SQLTablePrivileges

SQLTablePrivileges returns a list of tables and the privileges associated with each table. The driver returns the information as a result set on the specified statement.

SQLTablePrivilegesW() as a Unicode string supports same execution as SQLTablePrivileges().

#### Syntax

```
SQLRETURN  SQLTablePrivileges(
	SQLHSTMT		stmt,	
	SQLCHAR *		cName,	
	SQLSMALLINT		cNaneLength, 		
	SQLCHAR *		sName, 		
	SQLSMALLINT		sNameLength, 		
	SQLCHAR *		tName, 
	SQLSMALLINT		tNameLength);
```

#### Arguments

| Data Type   | Argument    | In/Out | Description                       |
| ----------- | ----------- | ------ | --------------------------------- |
| SQLHSTMT    | stmt        | Input  | Statement handle                  |
| SQLCHAR\*   | cName       | Input  | Catalog nam                       |
| SQLSMALLINT | cNameLength | Input  | The length, in bytes, of **cName* |
| SQLCHAR \*  | sName       | Input  | Name of the schema to retrieve    |
| SQLSMALLINT | sNameLength | Input  | The length, in bytes, of **sName* |
| SQLCHAR \*  | tName       | Input  | Table name to retrieve            |
| SQLSMALLINT | tNameLength | Input  | The length, in bytes, of **tName* |

#### Result Values

```
SQL_SUCCESS
SQL_SUCCESS_WITH_INFO
SQL_INVALID_HANDLE
SQL_ERROR
```

#### Description

SQLTablePrivileges () returns the data in the standard result set format sorted by TABLE_CAT, TABLE_SCHEM, TABLE_NAME, PRIVILEGE, and GRANTEE.

| Column Name  | No.  | Data Type          | Description                                                  |
| ------------ | ---- | ------------------ | ------------------------------------------------------------ |
| TABLE_CAT    | 1    | VARCHAR            | Always NULL Return                                           |
| TABLE_SCHEM  | 2    | VARCHAR            | Schema name; NULL if not applicable to the database.         |
| TABLE_NAME   | 3    | VARCHAR (NOT NULL) | Table name                                                   |
| GRANTOR      | 4    | VARCHAR            | Name of the user who granted the privilege; NULL if not applicable to the database. |
| GRANTEE      | 5    | VARCHAR (NOT NULL) | Name of the user to whom the privilege was granted.          |
| PRIVILEGE    | 6    | VARCHAR (NOT NULL) | Table privilege. One of the following privileges: Alter: The grantee can change the definition of the table. Delete: The grantee can dele the rows in the table. Index: The grantee can perform index operations (such as create or alter) for the table. INSERT: The grantee can insert new rows to the table. REFERENCES: The grantee can refer to the columns of the table with the limited conditions. SELECT: The grantee can search one or multiple columns in the table. UPDATE: The grantee can modify one or more data for the table. |
| IS_GRANTABLE | 7    | VARCHAR            | Indicates whether the grantee can give privilege to other users. Yes. No. Or NULL if unknown or not applicable to the database. |

[Table 2‑6] Columns Returned by SQLTablePrivileges ()

#### Diagnosis	

| SQLSTATE | Description                               | Comments                                                     |
| -------- | ----------------------------------------- | ------------------------------------------------------------ |
| 08S01    | Communication channel error               | Communication channel failure before the function processing is completed between the Altibase CLI driver and the database |
| HY009    | Invalid Arguments used (null pointer).    | Argument *cName* is a NULL pointer.                          |
| HY090    | Invalid character string or buffer length | One of the name length Arguments is smaller than 0 or is not equal to SQL_NTS. |

#### Related Functions

```
SQLBindCol
SQLCancel
SQLColumns
SQLFetch
SQLPrimaryKeys
SQLStatistics
SQLTables
```

#### Example

< Refer to: $ALTIBASE_HOME/sample/SQLCLI/demo_meta10.cpp >

```
if (SQLTablePrivileges(stmt,
                       NULL, 0,
                       "SYS", SQL_NTS,
                       "DEMO_META10", SQL_NTS) != SQL_SUCCESS)
    {
        execute_err(dbc, stmt, "SQLTablePrivileges");
        SQLFreeStmt(stmt, SQL_DROP);
        return SQL_ERROR;
    }

    SQLBindCol(stmt, 2, SQL_C_CHAR, szSchema, NAME_LEN, &cbSchema);
    SQLBindCol(stmt, 3, SQL_C_CHAR, szTableName, NAME_LEN,&cbTableName);
    SQLBindCol(stmt, 4, SQL_C_CHAR, szGrantor, NAME_LEN, &cbGrantor);
    SQLBindCol(stmt, 5, SQL_C_CHAR, szGrantee, NAME_LEN, &cbGrantee);
    SQLBindCol(stmt, 6, SQL_C_CHAR, szPrivilege, NAME_LEN,&cbPrivilege);
    SQLBindCol(stmt, 7, SQL_C_CHAR, szGrantable, 5, &cbGrantable);
```

### SQLTables

SQLTables returns the list of table, catalog, or schema names, and table types, stored in a specific data source. The driver returns the information as a result set. 

SQLTablesW() as a Unicode string supports same execution as SQLTables().

#### Syntax

```
SQLRETURN  SQLTables (
	SQLHSTMT 		stmt,
	SQLCHAR *		cName,
	SQLSMALLINT 	cNameLength,
	SQLCHAR *		sName,
	SQLSMALLINT 	sNameLength,
	SQLCHAR *		tName,
	SQLSMALLINT 	tNameLength,
	SQLCHAR *		tableType,
	SQLSMALLINT 	tableTypeLength);
```

#### Argument

| Data Type   | Argument        | In/Output | Description                              |
| ----------- | --------------- | --------- | ---------------------------------------- |
| SQLHSTMT    | stmt            | Input     | Statement handle for the searched result |
| SQLCHAR \*  | cName           | Input     | Catalog Name                             |
| SQLSMALLINT | cNameLength     | Input     | The length, in bytes, of **cName*        |
| SQLCHAR \*  | sName           | Input     | Schema Name                              |
| SQLSMALLINT | sNameLength     | Input     | The length, in bytes, of **sName*        |
| SQLCHAR \*  | tName           | Input     | Table name                               |
| SQLSMALLINT | tNameLength     | Input     | The length, in bytes, of **tName*        |
| SQLCHAR \*  | tableType       | Input     | Table type list to compare               |
| SQLSMALLINT | tableTypeLength | Input     | The length, in bytes, of **tableType*    |

#### Return Values

```
SQL_SUCCESS
SQL_SUCCESS_WITH_INFO
SQL_INVALID_HANDLE
SQL_ERROR
```

#### Description

SQLTables () displays all table information within the required range. Some users may or may not have the SELECT privilege to any of these tables. 

The application must be able to handle a situation where the user selects a table for which SELECT privileges are not granted. 

The following special syntaxes are defined for cName, sName, tName, and tableType of SQLTables () to support the catalogs, schema, and the list of table types: 

If sName is SQL_ALL_SCHEMAS and cName and tName are empty character strings, the result set will include the schema list valid for the database. (All columns expect that TABLE_SCHEM columns will include NULL data.) 

If tableType is SQL_ALL_TABLE_TYPES and cName, sName, and tName are empty character strings, the result set will include the list of table types valid for the database. (All columns except TABLE_TYPE column will include the NULL data.) 

An application must alwas specify the tableType in capital letters. One of the following can be specified: SQL_ALL_TABLE_TYPES, "SYSTEM TABLE", "TABLE", "VIEW", "QUEUE", "SYNONYM", "MATERIALIZED VIEW". 

SQLTables () returns the data in the standard result set format sorted by TABLE_TYPE, TABLE_CAT, TABLE_SCHEM, and TABLE_NAME.

The following table lists the columns in the result set.

| Column Name | No.  | Data Type          | Description                                                  |
| ----------- | ---- | ------------------ | ------------------------------------------------------------ |
| TABLE_CAT   | 1    | VARCHAR            | Null will be always returned.                                |
| TABLE_SCHEM | 2    | VARCHAR            | Schema name including TABLE_Name; NULL if not applicable to the database |
| TABLE_NAME  | 3    | VARCHAR (NOT NULL) | Table Name                                                   |
| TABLE_TYPE  | 4    | VARCHAR            | Table type name. One of the following types are returned: SQL_ALL_TABLE_TYPES 'SYSTEM TABLE' 'TABLE' 'VIEW' 'QUEUE' 'SYNONYM' 'MATERIALIZED VIEW' |
| REMARKS     | 5    | VARCHAR            | Not used                                                     |

[Table 2‑7] Columns Returned by SQLTables ()

#### Diagnosis

| SQLSTATE | Description                 | Comments                                                     |
| -------- | --------------------------- | ------------------------------------------------------------ |
| 08S01    | Communication channel error | Communication channel failure before the function processing is completed between the Altibase CLI driver and the database |
| HY000    | General erro                |                                                              |

#### Related Functions

```
SQLBindCol
SQLColumns
SQLFetch
SQLStatistics
```

#### Example

< Refer to: $ALTIBASE_HOME/sample/SQLCLI/demo_meta1.cpp >

```
if (SQLTables(stmt,
                  NULL, 0,
                  NULL, 0,
                  NULL, 0,
                  NULL, 0) != SQL_SUCCESS)
    {             
        execute_err(dbc, stmt, "SQLTables");
        SQLFreeStmt(stmt, SQL_DROP);
        return SQL_ERROR; 
    }

    if (SQLBindCol(stmt, 2, SQL_C_CHAR,
                   schem, sizeof(schem), &schem_ind) != SQL_SUCCESS)
    {
        execute_err(dbc, stmt, "SQLBindCol");
        SQLFreeStmt(stmt, SQL_DROP);
        return SQL_ERROR;
    }

    if (SQLBindCol(stmt, 3, SQL_C_CHAR,
                   name, sizeof(name), &name_ind) != SQL_SUCCESS)
    {
        execute_err(dbc, stmt, "SQLBindCol");
        SQLFreeStmt(stmt, SQL_DROP);
        return SQL_ERROR;
    }

    if (SQLBindCol(stmt, 4, SQL_C_CHAR,
                   type, sizeof(type), &type_ind) != SQL_SUCCESS)
    {
        execute_err(dbc, stmt, "SQLBindCol");
        SQLFreeStmt(stmt, SQL_DROP);
        return SQL_ERROR;
    }
while ( (rc = SQLFetch(stmt)) != SQL_NO_DATA)
    {
        if ( rc == SQL_ERROR )
        {
            execute_err(dbc, stmt, "SQLFetch");
            break;
        }
        printf("%-40s%-40s%s\n", schem, name, type);
    }

```

### SQLTransact

SQLTransact requests a commit or rollback operation for all active operations on all statements associated with a connection. 

Normally terminates or cancels all changed in the database made after the connection or before calling of SQLTransact (). 

If the transaction is in use in the connection status, an application must call SQLTransact () before disconnecting the database. 

SQLTransact () has been replaced by SQLEndTran ().

#### Syntax

```
SQLRETURN  SQLTransact (
	SQLHENV 		env,
	SQLHDBC 		dbc,
	SQLSMALLINT 	type );
```

#### Arguments

| Data Type   | Argument | In/Output | Description                                               |
| ----------- | -------- | --------- | --------------------------------------------------------- |
| SQLHENV     | env      | Input     | Environment handle                                        |
| SQLHDBC     | dbc      | Input     | Connection handle                                         |
| SQLSMALLINT | type     | Input     | One of the following two values. SQL_COMMIT, SQL_ROLLBACK |

#### Return Values

```
SQL_SUCCESS
SQL_INVALID_HANDLE
SQL_ERROR
```

#### Description

Completing the transaction with SQL_COMMIT or SQL_ROLLBACK will have the following effects: 

Even after SQLTransact () is called, the statement handle remains valid. 

The bound parameter and the column binding remain alive longer than the transaction. 

Discarding incompleted result sets.

Calling SQLTransact () when there is not transaction is currently used will return SQL_SUCCESS without any affecting the database server. 

SQLTransact() may fail while Commit or Rollback is executed due to loss of connection. In this case, an application cannot judge whether commit or rollback was made.In this case the database administrator handles it manually.

#### Example

< Refer to: $ALTIBASE_HOME/sample/SQLCLI/demo_tran1.cpp >

```
SQLTransact(SQL_NULL_HENV, dbc, SQL_COMMIT);
```

## 3. LOB Interface

This chapter describes functions and data types that can be used for handling LOB data.

### LOB data types

The following table shows SQL data type identifiers that support LOB:

| SQL Type Identifier | Data Type | Description                                           |
| ------------------- | --------- | ----------------------------------------------------- |
| SQL_BLOB            | BLOB      | BLOB is a binary data type with a variable length.    |
| SQL_CLOB            | CLOB      | CLOB is a character data type with a variable length. |

[Table 3‑1] Identifier of the SQL data type

The following table shows C data type identifiers that support LOB. It lists C data type of ODBC for each identifier and their definition.

| C Type Identifier  | ODBC C Type | C Type Definition |
| ------------------ | ----------- | ----------------- |
| SQL_C_BLOB_LOCATOR | SQLUBIGINT  | unsigned \_int64  |
| SQL_C_CLOB_LOCATOR | SQLUBIGINT  | unsigned \_int64  |

[Table 3‑2] Identifier for LOB-supported C data types

The name of a 64-bit integer type may vary depending on platform. The _int64 shown in the above table is the name of a 64-bit integer that is used in several platforms. 

Use SQL_C_CHAR for CLOB data and SQL_C_BINARY for BLOB data to bind user variables. 

To obtain a LOB locator, bind SQL_C_CLOB_LOCATOR or SQL_C_BLOB_LOCATOR appropriately based on the LOB column type. A LOB locator in this context, – a LOB location input scheme – is a handle that is used during LOB data operation like a file pointer in an operating system. 

The LOB location input scheme for Read can be obtained after SELECT LOB column name FROM table where… and select are executed. The LOB location input scheme for Write can be obtained after SELECT LOB column name FROM table where… FOR UPDATE are executed. 

Since a LOB location input scheme refers to LOB data at a certain point in relation to MVCC, it has the same life cycle with the transaction that has created itself. Therefore, to perform LOB operation with a LOB location input scheme, a connection should be always established in Non-Autocommit Mode. 

Care must be taken as there is no LOB type of a user variable such as SQL_C_BLOB or SQL_C_CLOB. 

### LOB Function Overview

The functions that are available for manipulating LOB data are as follows:

1.  SQLBindFileToCol()  (Non-standard)  
    Full Retrieve

2.  SQLBindFileToParam()  (Non-standard)  
    Full Insert, Full Update

3.  SQLGetLobLength()  (Non-standard)  
    Get the length of LOB data.

4.  SQLGetLob()  (Non-standard)  
    Partial Retrieve

5.  SQLPutLob()  (Non-standard)  
    Partial Insert, Partial Update, Partial Delete

6.  SQLFreeLob() (Non-standard)  
    Release the LOB locator being used.

7.  SQLGetData(), SQLPutData() (Non-standard)  
    Full Retrieve/Update

8.  Other ODBC standard functions

Among the above functions, the functions #1 through #6 are special functions that are provided by Altibase for LOB manipulation, and they are not ODBC standard functions.

ODBC standard functions such as #7 and #8 can be used to access LOB data whether the database column type is LOB or not. However, when only a standard function is used, the functions for partial update and partial retrieve are not available. If a user wants to do programming with ODBC Driver Manager, he should add the following entry to the odbc.ini file:

```
LongDataCompat = yes
or
LongDataCompat = on
```

If the above entry is added, the types such as SQL_BLOB and SQL_CLOB are converted to SQL_LONGVARBINARY and SQL_LONGVARCHAR types respectively before they are passed to the user. Therefore, if ODBC Driver Manager is used, transparent manipulation of LOB data can be ensured.

### SQLBindFileToCol

SQLBindFileToCol binds a file or files to the columns in the result set for BLOB or CLOB data type

#### Syntax

```
SQLRETURN SQLBindFileToCol(
    SQLHSTMT      	  stmt,
    SQLSMALLINT  	  col,
    SQLCHAR *    	  fileName,
    SQLLEN *    	  fileNameLength,
    SQLUINTEGER * 	  fileOptions,
    SQLLEN   		  fileNameBufferSize,
    SQLLEN *      	  valueLength);
```

#### Arguments

| Data Type      | Argument           | In/Output       | Description                                                  |
| -------------- | ------------------ | --------------- | ------------------------------------------------------------ |
| SQLHSTMT       | stmt               | Input           | An instruction handle for the found results.                 |
| SQLSMALLINT    | col                | Input           | Begins from #1 in the order of columns in the result set to bind. |
| SQLCHAR \*     | filename           | Input (Pending) | A pointer to the buffer that holds a filename or an array of filenames. It cannot be NULL.Upon SQLFetch(), there should be a filename stored in this buffer, and SQLFetch() returns data to the file(s).Either of an absolute path (recommended) and a relative path is allowed. |
| SQLLEN \*      | fileNameLength     | Input (Pending) | A pointer to the buffer that holds a filename length or an array of filename lengths.Upon SQLFetch(), there should be a filename length stored in this buffer.If this argument is NULL, a filename is regarded as a null-terminated string. That is, it has the same effect as if SQL_NTS were stored in the memory pointed by this argument.The max. length of a filename is 255 characters. |
| SQLUINTEGER \* | fileOptions        | Input (Pending) | A pointer to the buffer that holds a file option or an array of file options. Upon SQLFetch(), there should a file option stored in this buffer. The following options are available: SQL_FILE_CREATE creates one if there is no file, and returns SQL_ERROR if there is a file. SQL_FILE_OVERWRITE creates one if there is no file, and overwrites it if there is a file. SQL_FILE_APPEND creates one if there is no file, and appends to it if there is a file.Only one of the above options can be selected and there is no default option. This argument cannot be NULL. |
| SQLLEN         | fileNameBufferSize | Input           | Sets the length of the fileName buffer.                      |
| SQLLEN \*      | valueLength        | Output(Pending) | A pointer to the buffer that holds an indicator variable or an array of indicator variables. It cannot be NULL. It is used to return the length of the data stored in a file or to indicate that LOB is NULL. SQLFetch() can return the following values to the buffer pointed by this pointer: 1. Data length, 2. SQL_NULL_DATA. |

#### Return Values

```
SQL_SUCCESS
SQL_SUCCESS_WITH_INFO
SQL_INVALID_HANDLE
SQL_ERROR
```

#### Description

SQLBindFileToCol() binds LOB data in the result set to a file, and SQLBindCol() binds it to an application variable (memory buffer).

If SQLFetch() is called after SQLBindFileToCol() is called, LOB data from DBMS is stored in a file, and the length (byte) of the data stored in the file is stored in the buffer pointed by the valueLength pointer. If LOB is NULL, SQL_NULL_DATA is stored in the buffer pointed by the valueLength pointer. The values of fileName, fileNameLength and fileOptions arguments are referred to upon SQLFetch(), and any error in these arguments is also reported during fetching.

To transfer more than one LOB to a file at once upon fetching, all of the fileName, fileNameLength, fileOptions and valueLength arguments should be arrays. 

#### Diagnosis	

| SQLSTATE | Description                                          | Comments                                                     |
| -------- | ---------------------------------------------------- | ------------------------------------------------------------ |
| 08S01    | Communication line fault (Data transmission failure) | Communication line fails before function processing is complete between Altibase CLI driver and DB. |
| HY000    | General error                                        |                                                              |

#### Related Functions

```
SQLBindCol
SQLBindFileToParam
SQLDescribeCol
SQLFetch
```

#### Examples

It is assumed that a table has been created with the following DDL.

```
CREATE TABLE T1 (i1 INTEGER PRIMARY KEY, i2 BLOB);
```

##### Write one LOB to a file.

```
SQLCHAR fileName[16];
SQLLEN fileNameLength = 15;
SQLUINTEGER fileOptions = SQL_FILE_CREATE;
SQLLEN valueLength;
.
strcpy(query, "SELECT i2 FROM T1 WHERE i1=1");
if (SQLPrepare(stmt, query, SQL_NTS) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, “SQLPrepare : ”);
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}

/* Specify a file to put the result values of Select. */
strcpy(fileName, "Terminator2.avi");
if (SQLBindFileToCol(stmt, 1, fileName, &fileNameLength, &fileOptions, 16, &valueLength) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, “SQLBindFileToCol : “);
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}

if (SQLExecute(stmt) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, "SQLExecute : ");
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}

if (SQLFetch(stmt) == SQL_SUCCESS)
{
    printf("SQLFetch success!!!\n");
}
else
{
    execute_err(dbc, stmt, “SQLFetch : “);
}
```

##### Write three LOB’s to a file

```
SQLCHAR fileName[3][10];
SQLLEN fileNameLength[3];
SQLUINTEGER fileOptions[3];
SQLLEN valueLength[3];
.
.
.
if (SQLSetStmtAttr(stmt, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER) 3, 0) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, "SQLSetStmtAttr : ");
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}

if (SQLSetStmtAttr(stmt, SQL_ATTR_ROW_BIND_TYPE, SQL_BIND_BY_COLUMN, 0) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, "SQLSetStmtAttr : ");
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}

strcpy(query, "SELECT i2 FROM T1 WHERE i1 >= 1 AND i1 <= 3");

if (SQLExecDirect(stmt, query, SQL_NTS) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, "SQLExecDirect : ");
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}

/* Specify a file to put the result values of Select. */
strcpy(fileName[0], "Cube.avi");
strcpy(fileName[1], "Movie.avi");
strcpy(fileName[2], "Term.avi");

for (i = 0; i < 3; i++)
{
    fileNameLength[i] = strlen(fileName[i]);
    fileOptions[i] = SQL_FILE_CREATE;
}

if (SQLBindFileToCol(stmt, 1, (SQLCHAR *) fileName, fileNameLength, fileOptions, 10, valueLength) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, “SQLBindFileToCol : “);
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}

if (SQLFetch(stmt) == SQL_SUCCESS)
{
    printf("SQLFetch success!!!\n");
}
else
{
    execute_err(dbc, stmt, “SQLFetch : “);
```

##### Write n LOB’s to a file

```
SQLCHAR fileName[11];
SQLLEN fileNameLength = 10;
SQLUINTEGER fileOptions = SQL_FILE_OVERWRITE;
SQLLEN valueLength;
.
strcpy(query, "SELECT i2 FROM T1");

if (SQLExecDirect(stmt, query, SQL_NTS) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, "SQLExecDirect : ");
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}

if (SQLBindFileToCol(stmt, 1, fileName, &fileNameLength, &fileOptions, 11, &valueLength) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, "SQLBindFileToCol : “);
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}

for (i = 0; ; i++)
{
    sprintf(fileName, "Term%02d.avi", i + 1);

    rc = SQLFetch(stmt);
    if (rc == SQL_SUCCESS)
    {
        printf("SQLFetch of file[%02] success!!!\n", i + 1);
    }
    else if (rc == SQL_NO_DATA)
    {
        break;
    }
    else
    {
        execute_err(dbc, stmt, "SQLFetch : ");
        break;
    }
}
```

### SQLindFileToParam

SQLBindFileToParam binds the parameter market ‘?’ used for LOB data type to a file or files. When SQLExecute() or SQLExecDirect() is called, data is transferred from the file(s) to the database management system.

#### Syntax

```
SQLRETURN SQLBindFileToParam(
    SQLHSTMT         stmt,
    SQLSMALLINT      par,
    SQLSMALLINT      sqlType,
    SQLCHAR *        fileName,
    SQLLEN *         fileNameLength,
    SQLUINTEGER *    fileOptions,
    SQLLEN           maxFileNameLength,
    SQLLEN *         ind);
```

#### Arguments

| Data Type      | Argument           | In/Output       | Description                                                  |
| -------------- | ------------------ | --------------- | ------------------------------------------------------------ |
| SQLHSTMT       | stmt               | Input           | A handle for the found results.                              |
| SQLSMALLINT    | Par                | Input           | The order of parameters. Begins at 1.                        |
| SQLSMALLINT    | sqlType            | Input           | The SQL data type of a parameter.The following options are available: SQL_BLOB SQL_CLOB |
| SQLCHAR \*     | fileName           | Input(Pending ) | A pointer to the buffer that holds a filename or an array of filenames. Upon SQLExecute() or SQLExecDirect(), there should be a filename stored in this buffer. Either of an absolute path (recommended) and a relative path is allowed. This argument cannot be NULL. |
| SQLLEN \*      | fileNameLength     | Input(Pending)  | A pointer to the buffer that holds a filename length or an array of filename lengths.Upon SQLExecute() or SQLExecDirect(), there should be a filename length stored in this buffer.If this argument is NULL, a filename is regarded as a null-terminated string. That is, it has the same effect as if SQL_NTS were stored in the memory pointed by this argument.The max. length of a filename is 255 characters. |
| SQLUINTEGER \* | fileOptions        | Input(Pending)  | A pointer to the buffer that holds a file option or an array of file options. Upon SQLExecute() or SQLExecDirect(), there should a file option stored in this buffer.The following option is available: SQL_FILE_READ. |
| SQLLEN         | fileNameBufferSize | Input           | The length of the filename buffer.                           |
| SQLLEN \*      | Ind                | Input(Pending ) | A pointer to the buffer that holds an indicator variable or an array of indicator variables. It cannot be NULL.It is used to determine if LOB is NULL.The following values can be set for the buffer pointed by this pointer: 0, SQL_NULL_DATA. |

#### Result Values

```
SQL_SUCCESS
SQL_SUCCESS_WITH_INFO
SQL_INVALID_HANDLE
SQL_ERROR
```

#### Description

SQLBindFileToParam() binds a LOB parameter marker to a file. SQLBindParameter() can be used to bind a parameter marker to an application variable (memory buffer). For SQLBindFileToParam() and SQLBindParameter(), only the binding by the most recently called bind function is valid.

Because the values of fileName, fileNameLength, fileOptions and ind arguments are referred to upon SQLExecute() or SQLExecDirect(), they should be set before SQLExecute() or SQLExecDirect() is called. When SQLExecute() or SQLExecDirect() is called, data is transferred from the file being bound to DBMS.

If LOB is NULL, the buffer pointed by the ind pointer should be set to SQL_NULL_DATA, and then SQLExecute() or SQLExecDirect() should be called. If LOB is not NULL, the buffer pointed by the ind pointer should be set to 0. The ind argument cannot be a NULL pointer. 

To bind an array of files to a parameter marker, all of the fileName, fileNameLength, fileOptions and ind arguments should be arrays.

#### Diagnosis

| SQLSTATE | Description                                          | Comments                                                     |
| -------- | ---------------------------------------------------- | ------------------------------------------------------------ |
| 08S01    | Communication link fault (Data transmission failure) | Communication link failed before function processing is complete between Altibase CLI driver and DB |
| HY000    | General error                                        |                                                              |

#### Related Functions

```
SQLBindCol
SQLBindFileToCol
SQLExecute
SQLExecDirect
SQLDescribeParam
```

#### Examples

```
It is assumed that a table has been created with the following DDL.
CREATE TABLE T1 (i1 INTEGER PRIMARY KEY, i2 BLOB);
```

##### Input one LOB to a table

```
SQLCHAR fileName[16];
SQLLEN fileNameLength = 15;
SQLUINTEGER fileOptions = SQL_FILE_READ;
SQLLEN ind = 0;
.
strcpy(query, "INSERT INTO T1 VALUES (1, ?)");

/* Prepare a statement and bind a file */
if (SQLPrepare(stmt, query, SQL_NTS) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, “SQLPrepare : ”);
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}

strcpy(fileName, "Terminator2.avi");
if (SQLBindFileToParam(stmt, 1, SQL_BLOB, fileName, &fileNameLength, &fileOptions, 16, &ind) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, “SQLBindFileToParam : “);
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}

if (SQLExecute(stmt) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, "SQLExecute : ");
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}
```

##### Input three LOB’s to a table

```
SQLINTEGER i1[3];
SQLCHAR fileName[3][10];
SQLLEN fileNameLength[3];
SQLUINTEGER fileOptions[3];
SQLLEN ind[3];
.
if (SQLSetStmtAttr(stmt, SQL_ATTR_PARAMSET_SIZE, (SQLPOINTER) 3, 0) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, "SQLSetStmtAttr : ");
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}

if (SQLSetStmtAttr(stmt, SQL_ATTR_PARAM_BIND_TYPE, SQL_PARAM_BIND_BY_COLUMN, 0) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, "SQLSetStmtAttr : ");
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}

strcpy(query, "INSERT INTO T1 VALUES (?, ?)");

/* Prepare a statement and bind a file. */
if (SQLPrepare(stmt, query, SQL_NTS) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, “SQLPrepare : ”);
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}

if (SQLBindParameter(stmt, 1, SQL_PARAM_INPUT, SQL_C_INTEGER, SQL_INTEGER, 0, 0, (SQLPOINTER) i1, 0, NULL) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, “SQLBindParameter : “);
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}

if (SQLBindFileToParam(stmt, 2, SQL_BLOB, (SQLCHAR *) fileName, fileNameLength, fileOptions, 10, ind) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, “SQLBindFileToParam : “);
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}

/* Specify a file to insert data. */
strcpy(fileName[0], "Cube.avi");
strcpy(fileName[1], "Movie.avi");
strcpy(fileName[2], "Term.avi");

for (i = 0; i < 3; i++)
{
    i1[i] = i + 1;
    fileNameLength[i] = strlen(fileName[i]);
    fileOptions[i] = SQL_FILE_READ;
    ind[i] = 0;
}

if (SQLExecute(stmt) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, "SQLExecute : ");
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}
```

##### Update one LOB in a table

```
SQLCHAR fileName[16];
SQLLEN fileNameLength = 15;
SQLUINTEGER fileOptions = SQL_FILE_READ;
SQLLEN ind = 0;
.
strcpy(query, "UPDATE T1 SET i2=? WHERE i1=1");

/* Prepare a statement and bind a file. */
if (SQLPrepare(stmt, query, SQL_NTS) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, “SQLPrepare : ”);
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}

strcpy(fileName, "Terminator2_fix.avi");
if (SQLBindFileToParam(stmt, 1, SQL_BLOB, fileName, &fileNameLength, &fileOptions, 16, &ind) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, “SQLBindFileToParam : “);
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}

if (SQLExecute(stmt) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, "SQLExecute : ");
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}
```

### SQLGetLobLength

SQLGetLobLength gets the length of the LOB pointed by the LOB locator obtained during the current transaction.

#### Syntax

```
SQLRETURN SQLGetLobLength(
    SQLHSTMT         stmt,
    SQLUBIGINT       locator,
    SQLSMALLINT      locatorCType,
    SQLUINTEGER *    valueLength);
```

#### Arguments

| Data Type      | Argument     | In/Output | Description                                                  |
| -------------- | ------------ | --------- | ------------------------------------------------------------ |
| SQLHSTMT       | stmt         | Input     | A handle for the found results.                              |
| SQLUBIGINT     | locator      | Input     | LOB Locator                                                  |
| SQLSMALLINT    | locatorCType | Input     | The C data type of A LOB locator. It can have the following values: SQL_C_BLOB_LOCATOR SQL_C_CLOB_LOCATOR |
| SQLUINTEGER \* | valueLength  | Output    | It stores the length of a LOB. The buffer pointed to by the pointer returns the data length. |

#### Return Values

```
SQL_SUCCESS
SQL_SUCCESS_WITH_INFO
SQL_INVALID_HANDLE
SQL_ERROR
```

#### Description

A function that is used to get the length of the LOB pointed by a LOB locator. 

A LOB locator has the value that directly points LOB in a database (not offset in LOB). A LOB locator can be obtained in two ways: 

It can be obtained from the LOB column in the result set of the SELECT SQL statement with SQLBindCol() or SQLGetData() function. 

In this case, the application buffer type bound by the user should be SQL_C_CLOB_LOCATOR or SQL_C_BLOB_LOCATOR. 

It can be obtained from the output parameter of SQLBindParameter(). 

In this case, the application buffer type bound by the user should be SQL_C_CLOB_LOCATOR or SQL_C_BLOB_LOCATOR. 

If a LOB locator has not been obtained during the current transaction, it cannot be used as an argument for this function. This is because a LOB locator becomes invalid if a transaction is terminated. If an invalid LOB locator is used as an argument, this function will return SQL_ERROR, and the buffer pointed by the valueLength argument will not be changed. 

The length of LOB is returned via the valueLength argument. However, If a LOB locator points NULL LOB, SQL_NULL_DATA is returned to the buffer pointed by the valueLength argument. If a LOB locator points NULL LOB, this function will not return an error.

#### Diagnosis

| SQLSTATE | Description                                          | Note                                                         |
| -------- | ---------------------------------------------------- | ------------------------------------------------------------ |
| 08S01    | Communication link fault (Data transmission failure) | Communication link failed before function processing is complete between Altibase CLI driver and DB. |
| HY000    | General error                                        |                                                              |

#### Related Functions

```
SQLBindCol
SQLBindParameter
SQLFetch
SQLExecute
SQLGetLob
SQLPutLob
```

#### Example

It is assumed that a table has been created with the following DDL.

```
CREATE TABLE T1 (i1 INTEGER PRIMARY KEY, i2 BLOB);
```

##### Retrieve the length of LOB data

```
SQLINTEGER valueLength;
SQLUBIGINT lobLoc;
.
.
.
strcpy(query, "SELECT i2 FROM T1 WHERE i1=1");
if (SQLExecDirect(stmt, query, SQL_NTS) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, “SQLExecDirect : ”);
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}

if (SQLBindCol(stmt, 1, SQL_C_BLOB_LOCATOR, &lobLoc, 0, NULL) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, “SQLBindCol : ”);
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}

if (SQLFetch(stmt) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, “SQLFetch : ”);
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}

if (SQLGetLobLength(stmt, lobLoc, SQL_C_BLOB_LOCATOR, &valueLength) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, “SQLGetLobLength : ”);
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}

printf("SQLGetLobLength success!!!\n");

if (SQLFreeLob(stmt, lobLoc) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, “SQLFreeLob : ”);
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}
```

### SQLGetLob

SQLGetLob gets a part of data in the LOB pointed by the LOB locator obtained during the current transaction to an application data buffer.

#### Syntax

```
SQLRETURN SQLGetLob(
    SQLHSTMT        stmt,
    SQLSMALLINT     locatorCType,
    SQLUBIGINT      sourceLocator,
    SQLUINTEGER     fromPosition,
    SQLUINTEGER     forLength,
    SQLSMALLINT     targetCType,
    SQLPOINTER      value,
    SQLUINTEGER     bufferSize,
    SQLUINTEGER *   valueLength);
```

#### Arguments

| Data Type     | Argument      | In/Output | Description                                                  |
| ------------- | ------------- | --------- | ------------------------------------------------------------ |
| SQLHSTMT      | stmt          | Input     | Handle for the found results.                                |
| SQLSMALLINT   | locatorCType  | Input     | The C data type identifier of a LOB locator. It can have the following values: SQL_C_BLOB_LOCATOR SQL_C_CLOB_LOCATOR |
| SQLUBIGINT    | sourceLocator | Input     | Source LOB Locator                                           |
| SQLUINTEGER   | fromPosition  | Input     | The start point of data to transfer from LOB (byte). It begins at 1. |
| SQLUINTEGER   | forLength     | Input     | The length of data to transfer from LOB (byte).              |
| SQLSMALLINT   | targetCType   | Input     | The C data type identifier of the value buffer. It can have the following values: SQL_C_BINARY SQL_C_CHAR If the user reads BLOB data into the SQL_C_CHAR buffer, BINARY is converted to CHAR, and the result value is stored in an application buffer. |
| SQLPOINTER    | value         | Output    | A pointer to the buffer that holds data.                     |
| SQLUINTEGER   | bufferSize    | Input     | The size of the value buffer (byte).                         |
| SQLUINTEGER\* | valueLength   | Output    | A pointer to the buffer to which the length of data stored in the value buffer is returned. This argument cannot be NULL. |

#### Result Values

```
SQL_SUCCESS
SQL_SUCCESS_WITH_INFO
SQL_INVALID_HANDLE
SQL_ERROR
```

#### Description

Gets a part of data in the LOB pointed by the source locator to an application data buffer. It is used to get LOB data in parts. The total length of LOB can be obtained by calling SQLGetLobLength(). 

If a source locator is not the LOB locator obtained during the current transaction, it cannot be used as an argument for this function. This is because a LOB locator becomes invalid if a transaction is terminated. If a source LOB locator is not valid, the SQLGetLob() function will return SQL_ERROR, and the buffer pointed by the value and valueLength arguments will not be changed. 

If a source locator points NULL LOB, the SQLGetLob() function works in the same way as when a LOB locator points LOB with length 0.

If the size of data that will be returned by calling SQLGetLob() exceeds the size of bufferSize, the SQLGetLob() will return SQL_SUCCESS_WITH_INFO (SQLSTATE=01004), and the data will be truncated to fit the buffer size before it is returned to the buffer.

#### Diagnosis	

| SQLSTATE | Description                                          | Comments                                                     |
| -------- | ---------------------------------------------------- | ------------------------------------------------------------ |
| 08S01    | Communication link fault (Data transmission failure) | Communication link failed before function processing is complete between Altibase CLI driver and DB. |
| HY000    | General error                                        |                                                              |

#### Related Functions

```
SQLGetLobLength
SQLPutLob
```

#### Example

It is assumed that a table has been created with the following DDL.

```
CREATE TABLE T1 (i1 INTEGER PRIMARY KEY, i2 CLOB);
```

##### Retrieve LOB data to an application buffer by using the SQLGetLob() function

```
SQLCHAR buf[1024];
SQLINTEGER valueLength, accumLength, forLength, procLength;
SQLUBIGINT lobLoc;
.
.
strcpy(query, "SELECT i2 FROM T1 WHERE i1=1");
if (SQLExecDirect(stmt, query, SQL_NTS) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, “SQLExecDirect : ”);
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}

if (SQLBindCol(stmt, 1, SQL_C_CLOB_LOCATOR, &lobLoc, 0, NULL) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, “SQLBindCol : ”);
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}

if (SQLFetch(stmt) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, “SQLFetch : ”);
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}

if (SQLGetLobLength(stmt, lobLoc, SQL_C_CLOB_LOCATOR, &valueLength) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, “SQLGetLobLength : ”);
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}

for (accumLength = 0; accumLength < valueLength; accumLength += procLength)
{
    if (valueLength - accumLength > 256)
    {
        forLength = 256;
    }
    else
    {
        forLength = valueLength - accumLength;
    }

    if (SQLGetLob(stmt, SQL_C_CLOB_LOCATOR, lobLoc, accumLength, forLength, SQL_C_CHAR, buf, 256, &procLength) != SQL_SUCCESS)
    {
        execute_err(dbc, stmt, “SQLGetLob : ”);
        SQLFreeStmt(stmt, SQL_DROP);
        return SQL_ERROR;
    }

    printf("%s", buf);
}

if (SQLFreeLob(stmt, lobLoc) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, “SQLFreeLob : ”);
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}
```

### SQLPutLob

All operations of this function are performed as internal updates. Insertion is the operation of updating existing LOB data of 0 length value into another value. Depending on the argument value, update either overwrites existing data with another value, starting at a specified position, or appends another value at the end of existing data.

#### Syntax

```
SQLRETURN SQLPutLob(
    SQLHSTMT        stmt,
    SQLSMALLINT     locatorCType,
    SQLUBIGINT      targetLocator,
    SQLUINTEGER     fromPosition,
    SQLUINTEGER     forLength,
    SQLSMALLINT     sourceCType,
    SQLPOINTER      value,
    SQLUINTEGER     valueLength);
```

#### Arguments

| Data Type   | Argument      | In/Output | Description                                                  |
| ----------- | ------------- | --------- | ------------------------------------------------------------ |
| SQLHSTMT    | stmt          | Input     | Handle for the found results.                                |
| SQLSMALLINT | locatorCType  | Input     | The C data type of a target LOB locator. SQL_C_BLOB_LOCATOR SQL_C_CLOB_LOCATOR |
| SQLUBIGINT  | targetLocator | Input     | Target LOB Locator                                           |
| SQLUINTEGER | fromPosition  | Input     | The start point to update data in LOB (byte). It begins at 1. |
| SQLUINTEGER | forLength     | Input     | Not used.                                                    |
| SQLSMALLINT | sourceCType   | Input     | The C data type identifier of the value buffer. SQL_C_BINARY (for BLOB), SQL_C_CHAR (for CLOB) |
| SQLPOINTER  | value         | Input     | The pointer that points to the buffer storing input data.    |
| SQLUINTEGER | valueLength   | Input     | The length of data input in the value buffer (unit: bytes). A value larger than 0 must be set; SQL_NULL_DATA is not accepted. |

#### Return Values

```
SQL_SUCCESS
SQL_SUCCESS_WITH_INFO
SQL_INVALID_HANDLE
SQL_ERROR
```

#### Description

This function inserts or updates data stored in the application data buffer into the LOB which the target LOB locator points to. 

When this function is operated, the server overwrites data of the target LOB, starting at the position of fromPosition, for the length of valueLength of the value buffer. If valueLength is larger than (LOBSize - fromPosition), the length of the target LOB of the database is extended; if fromPosition points to the end position of the target LOB value, data of the length of valueLength of the value buffer is appended to the end of the existing value. 

If the LOB locator is not one which is opened in the current session, it is not accepted as an argument for this function, since the LOB locator becomes invalid when the transaction terminates. If the target LOB locator is invalid, the SQLPutLob() function returns SQL_ERROR. 

If the target LOB locator points to a LOB with the value of NULL, the SQLPutLob() function operates equivalent to the LOB locator pointing to a LOB with the length of 0. 

The fromPosition argument must not be larger than the length of the target LOB at the time point of calling. If the value of the fromPosition argument is larger than the length of the target LOB, the SQLPutLob() function returns SQL_ERROR.

#### Diagnosis

| SQLSTATE | Description                                          | Comments                                                     |
| -------- | ---------------------------------------------------- | ------------------------------------------------------------ |
| 08S01    | Communication link fault (Data transmission failure) | Communication link failed before function processing is complete between Altibase CLI driver and DB. |
| HY000    | 일반 오류                                            |                                                              |

#### Related Functions

```
SQLGetLobLength
SQLGetLob
```

#### Examples

It is assumed that a table has been created with the following DDL.

```
CREATE TABLE T1 (i1 INTEGER PRIMARY KEY, i2 CLOB);
```

##### After inserting a record with the CLOB column value being ‘Ver.Beta’, replace ‘Beta’ with ‘Gamma’

```
SQLCHAR buf[5];
SQLUBIGINT lobLoc;
.
strcpy(query, "INSERT INTO T1 VALUES (1, 'Ver.Beta')");
if (SQLExecDirect(stmt, query, SQL_NTS) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, “SQLExecDirect : ”);
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}

.
strcpy(query, "SELECT i2 FROM T1 WHERE i1=1 FOR UPDATE");
if (SQLExecDirect(stmt, query, SQL_NTS) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, “SQLExecDirect : ”);
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}

if (SQLBindCol(stmt, 1, SQL_C_CLOB_LOCATOR, &lobLoc, 0, NULL) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, “SQLBindCol : ”);
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}

if (SQLFetch(stmt) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, “SQLFetch : ”);
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}

memcpy(buf, "Gamma", 5);
if (SQLPutLob(stmt, SQL_C_CLOB_LOCATOR, lobLoc, 4, 4, SQL_C_CHAR, buf, 5) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, “SQLPutLob : ”);
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}

if (SQLFreeLob(stmt, lobLoc) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, “SQLFreeLob : ”);
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}
```

##### Insert a record with the CLOB column value being ‘Ver.0.9a’

```
SQLCHAR buf[8];
SQLINTEGER lobInd;
SQLUBIGINT lobLoc;
.
.
.
strcpy(query, "INSERT INTO T1 VALUES (5, ?)");
if (SQLPrepare(stmt, query, SQL_NTS) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, “SQLPrepare : ”);
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}

if (SQLBindParameter(stmt, 1, SQL_PARAM_OUTPUT, SQL_C_CLOB_LOCATOR, SQL_CLOB_LOCATOR, 0, 0, &lobLoc, 0, &lobInd) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, “SQLBindParameter : ”);
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}

if (SQLExecute(stmt) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, “SQLExecute : ”);
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}

memcpy(buf, "Ver.0.9a", 8);
if (SQLPutLob(stmt, SQL_C_CLOB_LOCATOR, lobLoc, 0, 0, SQL_C_CHAR, buf, 7) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, “SQLPutLob : ”);
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}

/*  In ‘Ver.0.9a’, replace ‘0.9’ with ‘1’. */
memcpy(buf, "1", 1);
if (SQLPutLob(stmt, SQL_C_CLOB_LOCATOR, lobLoc, 4, 3, SQL_C_CHAR, buf, 1) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, “SQLPutLob : ”);
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}

if (SQLFreeLob(stmt, lobLoc) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, “SQLFreeLob : ”);
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}
```

##### Change the CLOB of multiple records to ‘Retail’ at once

```
SQLCHAR buf[6];
SQLINTEGER lobInd;
SQLUBIGINT lobLoc;
.
.
.
strcpy(query, "UPDATE T1 SET i2=? WHERE i1>=1 AND i1<=100");
if (SQLPrepare(stmt, query, SQL_NTS) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, “SQLPrepare : ”);
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}

/*  If an UPDATE query is executed after a LOB locator parameter is being outbound, LOB columns to be updated will be truncated to null automatically.  */
if (SQLBindParameter(stmt, 1, SQL_PARAM_OUTPUT, SQL_C_CLOB_LOCATOR, SQL_CLOB_LOCATOR, 0, 0, &lobLoc, 0, &lobInd) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, “SQLBindParameter : ”);
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}

if (SQLExecute(stmt) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, “SQLExecute : ”);
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}

memcpy(buf, “Retail”, 6);
if (SQLPutLob(stmt, SQL_C_CLOB_LOCATOR, lobLoc, 0, 0, SQL_C_CHAR, buf, 6) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, “SQLPutLob : ”);
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}

if (SQLFreeLob(stmt, lobLoc) != SQL_SUCCESS)
{
    execute_err(dbc, stmt, “SQLFreeLob : ”);
    SQLFreeStmt(stmt, SQL_DROP);
    return SQL_ERROR;
}
```

### SQLTrimLob

This function deletes the latter portion of data from a specified position, of the LOB value that the LOB locater points to.

#### Syntax

```
SQLRETURN SQLTrimLob(
    SQLHSTMT         stmt,
    SQLSMALLINT      locatorCType,
    SQLUBIGINT       targetLocator,
    SQLLEN           fromPosition);
```

#### Arguments

| Data Type   | Argument      | In/Output | Description                                                  |
| ----------- | ------------- | --------- | ------------------------------------------------------------ |
| SQLHSTMT    | stmt          | Input     | The handle for the found results.                            |
| SQLSMALLINT | locatorCType  | Input     | The C data type identifier of the target LOB locator. SQL_C_BLOB_LOCATOR SQL_C_CLOB_LOCATOR |
| SQLUBIGINT  | targetLocator | Input     | Target LOB Locator                                           |
| SQLLEN      | fromPosition  | Input     | The position at which to start deleting LOB data (unit:bytes). Begins at 0. |

#### Result Values

```
SQL_SUCCESS
SQL_INVALID_HANDLE
SQL_ERROR
```

#### Description

This function deletes the latter portion of data from a specified position, of the LOB value that the LOB locater points to. After deletion, the length of the target LOB is shortened.

If the LOB locator is not one which is opened in the current session, it is not accepted as an argument for this function, since the LOB locator becomes invalid when the transaction terminates. If the target LOB locator is invalid, the SQLTrimLob() function returns SQL_ERROR.

#### Diagnosis

| SQLSTATE | Description                                          | Comments                                                     |
| -------- | ---------------------------------------------------- | ------------------------------------------------------------ |
| 08S01    | Communication link fault (Data transmission failure) | A communication link failed before function processing is complete between Altibase CLI driver and DB. |
| HY000    | General error                                        |                                                              |

#### Related Functions

```
SQLGetLobLength
SQLGetLob
```

#### Examples

It is assumed that a table is created with the following DDL.

```
CREATE TABLE T1 (i1 INTEGER PRIMARY KEY, i2 CLOB);
```

##### After inserting a record with the CLOB column value ‘Ver.Beta’, delete ‘Beta’

```
SQLCHAR buf[5];
SQLUBIGINT lobLoc;
 
strcpy(query, "INSERT INTO T1 VALUES (1, 'Ver.Beta')");
if (SQLExecDirect(stmt, query, SQL_NTS) != SQL_SUCCESS)
{
     execute_err(dbc, stmt, “SQLExecDirect : ”);
     SQLFreeStmt(stmt, SQL_DROP);
     return SQL_ERROR;
}
 
strcpy(query, "SELECT i2 FROM T1 WHERE i1=1 FOR UPDATE");
if (SQLExecDirect(stmt, query, SQL_NTS) != SQL_SUCCESS)
{
     execute_err(dbc, stmt, “SQLExecDirect : ”);
     SQLFreeStmt(stmt, SQL_DROP);
     return SQL_ERROR;
}
if (SQLBindCol(stmt, 1, SQL_C_CLOB_LOCATOR, &lobLoc, 0, NULL) != SQL_SUCCESS)
{
     execute_err(dbc, stmt, “SQLBindCol : ”);
     SQLFreeStmt(stmt, SQL_DROP);
 
     return SQL_ERROR;
}
if (SQLFetch(stmt) != SQL_SUCCESS)
{
     execute_err(dbc, stmt, “SQLFetch : ”);
     SQLFreeStmt(stmt, SQL_DROP);
     return SQL_ERROR;
}
 
if (SQLTrimLob(stmt, SQL_C_CLOB_LOCATOR, lobLoc, 4) != SQL_SUCCESS)
{
     execute_err(dbc, stmt, “SQLTrimLob : ”);
     SQLFreeStmt(stmt, SQL_DROP);
     return SQL_ERROR;
}
if (SQLFreeLob(stmt, lobLoc) != SQL_SUCCESS)
{
     execute_err(dbc, stmt, “SQLFreeLob : ”);
     SQLFreeStmt(stmt, SQL_DROP);
     return SQL_ERROR;
}
```

### SQLFreeLob

SQLFreeLob releases resources that are related to a LOB locator opened during the current transaction.

#### Syntax

```
SQLRETURN SQLFreeLob (
    SQLHSTMT        stmt,
    SQLUBIGINT      locator);
```

#### Arguments

| Data Type  | Argument | In/Out | Description                  |
| ---------- | -------- | ------ | ---------------------------- |
| SQLHSTMT   | stmt     | Input  | Handle for the found results |
| SQLUBIGINT | locator  | Input  | LOB Locator                  |

#### Return Values

```
SQL_SUCCESS
SQL_INVALID_HANDLE
SQL_ERROR
```

#### Description

Reports that operation of LOB pointed by a LOB locator is complete. This will release the LOB locator assigned by a server and other related resources in the server.

This function does not commit or rollback changes to LOB pointed by a LOB locator.

If a transaction is terminated with SQLEndTran(), a LOB locator is automatically released and this function does have to be called.

#### Diagnosis

| SQLSTATE | Description                                          | Comments                                                     |
| -------- | ---------------------------------------------------- | ------------------------------------------------------------ |
| 08S01    | Communication link fault (Data transmission failure) | Communication link failed before function processing is complete between Altibase CLI driver and DB. |
| HY000    | General error                                        |                                                              |

#### Related Functions

```
SQLGetLobLength
SQLGetLob
SQLPutLob
```

#### Example

Please see the examples of SQLGetLobLength(), SQLGetLob() and SQLPutLob().

## 4. Using Cursors

This chapter explains how to use cursors provided by the Altibase CLI driver.

### Cursor Characteristics

The Altibase CLI driver supports the following cursors:

-   Diverse types of cursors 
-   Scrolling and positioning within cursors 
-   Multiple concurrency options 
-   Positioned updates

Cursor characteristics are controlled by statement attributes set with SQLSetStmtAttr before executing SQL statements. Altibase CLI API functions for processing result sets support all-inall cursor functionality, such as fetch, scroll and positioned update. 

#### Setting Cursor Attributes

An application can control cursor behavior by setting one or more cursor attributes before executing a SQL statement. There are two ways of specifying cursor characteristics in the ODBC Standard:

-   Cursor Type  
    Cursor types can be set using the SQL_ATTR_CURSOR_TYPE attribute of SQLSetStmtAttr. The Altibase CLI driver supports forward-only, static, and keyset-driven cursor types. 
    
-   Cursor Behavior  
    Cursor behavior can be set using the SQL_ATTR_CURSOR_SCROLLABLE, SQL_ATTR_CURSOR_SENSITIVITY, and SQL_ATTR_CONCURRENCY attributes of SQLSetStmtAttr.

Cursor types are ODBC-style and cursor behavior is SQL-92/ISO style. 

#### Cursor Types

The Altibase CLI driver supports the following three cursor types:

-   Forward-only cursors: Scrolling is not supported; fetching rows are only supported from the start to the end of the cursor.
  
-   Static cursor: Displays the result set as it was when the cursor was opened, and is readonly.

-   Keyset-driven cursors: Row order is fixed when the cursor is opened. Data modifications made to nonkey columns are visible through the cursor.

#### Cursor Behavior

Cursor scrollability, sensitivity and concurrency can be specified using the SQL_ATTR_CURSOR_SCROLLABLE, SQL_ATTR_CURSOR_SENSITIVITY, and SQL_ATTR_CONCURRENCY attributes of SQLSetStmtAttr.

-   Scrollability  
    If SQL_ATTR_CURSOR_SCROLLABLE is set to SQL_SCROLLABLE, the cursor supports scrolling in various directions; if SQL_ATTR_CURSOR_SCROLLABLE is set to SQL_NONSCROLLABLE, the cursor supports scrolling only in the SQL_FETCH_NEXT direction.
    
-   Sensitivity  
    If SQL_ATTR_CURSOR_SENSITIVITY is set to SQL_SENSITIVE, the cursor reflects data modifications of the database, and retrieves the latest data from the database upon a repeated request of a rowset; If SQL_ATTR_CURSOR_SENSITIVITY is set to SQL_INSENSITIVE, the cursor does not reflect data modifications, and retrieves cached data upon a repeated request of a rowset.
    
-   Concurrency  
    Cursor concurrency is set using the SQL_ATTR_CONCURRENCY attribute of SQLSetStmtAttr. the Altibase CLI driver supports the following two types of cursor concurrency: 
    -   SQL_CONCUR_READONLY: Read-only
    
    -   SQL_CONCUR_ROWVER: Concurrency control with row versions.

### Implicit Cursor Conversionse

Instead of specifying the cursor type, an application can specify each characteristic related to cursor behavior separately, by setting the SQL_ATTR_CURSOR_SCROLLABLE, SQL_ATTR_CURSOR_SENSITIVITY, and SQL_ATTR_CONCURRENCY statement attributes before opening a cursor associated with the statement handle. The Altibase CLI driver then selects the cursor type which most efficiently provides the characteristic requested by the application. 

Whenever an application sets either of the SQL_ATTR_CURSOR_SCROLLABLE, SQL_ATTR_CURSOR_SENSITIVITY, SQL_ATTR_CONCURRENCY, or SQL_ATTR_CURSOR_TYPE statement attributes, the driver converts another attribute value for the four attribute values to be compatible. If an application specifies an attribute related to cursor behavior, the driver can convert an attribute which defines the cursor type, on the basis of implicit selection; if an application specifies the cursor type, the driver can convert other attributes to ensure compatibility among attribute values and characteristics of the selected cursor type. 

Caution is required as there is a possibility of begetting a cursor of unintentional characteristics if an application specifies both the cursor type and cursor behavior. 

The following table shows basic cursor behaviors according to cursor types. 

| Cursor Type   | Sensitivity | Scrollability  | Concurrency |
| ------------- | ----------- | -------------- | ----------- |
| Forward-only  | insensitive | non-scrollable | read-only   |
| Static        | insensitive | scrollable     | read-only   |
| Keyset-driven | sensitive   | scrollable     | updatable   |
| Dynamic       | \-          | \-             | \-          |

The Altibase CLI driver does not support dynamic cursors. For forward-only and static cursors, any other behavior combination apart from that of the table above is not supported. For keyset-driven cursors, apart from the combinations of the table above, the (SENSITIVE, SCROLLABLE, READ-ONLY) combination is supported. 

Cursor conversion rules are as follows:

-   If the user-specified cursor attribute is not compatible with the cursor type, the driver converts the cursor type in the following order:
  
    -   dynamic → keyset-driven → static → foward-only
  
-   If an application specifies the cursor type, the driver converts the remaining attributes in the following order, until they are compatible with the characteristics of the selected type:
  
    -   sensitive → insensitive
  
    -   scrollable → non-scrollable
  
    -   updatable → read-only

### Scrolling and Fetching Rows

To use scrollable cursors, the following must be executed in Altibase CLI applications:

-   The cursor attributes must be set using SQLSetStmtAttr. 
-   The cursor must be opened using SQLExecute or SQLExecDirect. 
-   Rows must be scrolled and fetched using SQLFetch or SQLFetchScroll.

ODBC cursors do not limit one fetch to one row. Multiple rows can be fetched whenever SQLFetch or SQLFetchScroll is called. For client/server model database operations like ODBC application programs, it is efficient to fetch multiple rows at one time. The number of rows returned from a fetch is said to be the size of the rowset, and this can be specified using SQL_ATTR_ROW_ARRAY_SIZE of SQLSetStmtAttr. 

Cursors with a rowset size larger than 1 are called block cursors, and data can be queried from block cursors by binding arrays. 

For more detailed information, refer to the SQLFetch function in Chapter 2: SQLFetch can be used only for forward-only cursors and SQLFetchScroll can scroll cursors in various directions. 

#### Setting Bookmarks For Rowsets

A bookmark is a value used to identify a row of data. In Altibase CLI applications, bookmarks for certain rows are requested, stored, and then passed to the cursor to return to the row. 

When fetching rows with SQLFetchScroll, an application can select the starting row, using a bookmark as a basis. This bookmark takes the form of an absolute address, since it does not refer to the current cursor position. An application can scroll a bookmarked row by calling SQLFetchScroll, using SQL_FETCH_BOOKMARK. This operation uses the bookmark specified in the SQL_ATTR_FETCH_BOOKMARK_PTR statement attribute; rowsets are returned, starting from the row identified by the bookmark. An application can take an offset as an argument when calling SQLFetchScroll. When the offset is specified, the first row of the returned rowset is determined by adding the number of offsets to the row identified by the bookmark. The Altibase CLI driver only supports bookmarks on static and keyset-driven cursors. If bookmarks are set on and a dynamic cursor is requested, a keyset-driven cursor is opened instead. 

### Restrictions

In order to use Altibase CLI driver cursors, the SELECT statement which retrieves the result set is restricted in the following manner:

-   Only one table can be specified in the FROM clause. 
-   The column name must be specified in the ORDER BY clause.

In order to execute positioned updates in a cursor, the following restrictions apply additionally: 

-   Only regular tables can be specified in the FROM clause. 
-   Only pure columns can be specified in the SELECT list; neither expressions, nor functions can be included. Columns that have a NOT NULL constraint, but do not have a DEFAULT value must be included in the SELECT list.

## Appendix A. Sample Codes

The following describes notes on programming the client using the Altibase CLI and frequent errors:

### Programing Considerations

The following describes notes on programming the client using the Altibase CLI and frequent errors:

#### Binding Parameters

Note on using the last argument, valueLength (indicator), upon calling SQLBindCol () and SQLBindParameter (). 

In case the value fetched by the output argument in SQLBindCol () is NULL, SQL_NULL_DATA will be returned to the indicator argument. 

The valueLength of SQLBindParameter () is used to indicate the length of the buffer when the data type of the argument bound to the input buffer is the variable type. (When the parameter inout type is SQL_PARAM_INOUT)

For example, the user can specify the following values for * valueLength *:

-   SQL_NTS: A string in which the buffer ends with NULL ( '' )
-   SQL_NULL_DATA: Binding the NULL value
-   Result of the SQL_DATA_AT_EXEC or SQL_LEN_DATA_AT_EXEC () macro: This means that data will be inserted using a combination of SQLPutData () and SQLParamData (). SQLExecute () returns SQL_NEED_DATA when executed.

When SQLBindParameter () specifies the input / output type in SQL_PARAM_OUTPUT *valueLength* is equivalent to *valueLength* of the SQLBindCol () function used when executing a SELECT statement. Play the same role.

#### Transaction Commit Mode

All transactions that are not committed when an application program is terminated in an autocommit off session are rolled back by the Altibase server. However, the Altibase server commits the transactions which were not committed if the application program is terminated after SQLDisconnect() was called.

#### Using SQLFreeStmt() function

If the second argument is SQL_DROP in SQLFreeStmt (), the status of the handle will be changed into the previous status before the handle was allocated. however, when SQL_CLOSE argument is used, the handle status after SQLAllocStmt () is executed will be selected and can be used for other queries. In case the command executes SQLPrepare (), the status will be changed into the preparation status after SQLFreeStmt () is called by SQL_CLOSE. 

In case SELECT statement is executed by SQLPrepare (). Execution result of SELECT statement upon changing from SQLExecute () to SQLFetch (). When SQLExecute () is called again by binding other hosts variables without fetching untill the last record of the result set, "invalid cursor state" may occur. To prevent this, the user must call SQLFreeStmt ( .. , SQL_CLOSE ) and SQLExecute ().However, if SQLFetch () was executed until the last record in the execution result of SELECT statement, SQLFreeStmt () of SQL_CLOSE does not need to be called for normal operation.

### Sample of Simple Basic Program

```
/***********************************************
**  File name = demo_ex1.cpp
***********************************************/
#include <sqlcli.h>
#include <stdio.h>
#include <stdlib.h>


#define SQL_LEN 1000
#define MSG_LEN 1024

SQLHENV  env;  // Environment Handle
SQLHDBC  dbc;  // Connection Handle
int      conn_flag;

SQLRETURN alloc_handle();
SQLRETURN db_connect();
void free_handle();

SQLRETURN execute_select();
void execute_err(SQLHDBC aCon, SQLHSTMT aStmt, char* q);

int main()
{
    SQLRETURN    rc;

    env = SQL_NULL_HENV;
    dbc = SQL_NULL_HDBC;
    conn_flag = 0;

    /* allocate handle */
    rc = alloc_handle();
    if ( rc != SQL_SUCCESS )
    {
        free_handle();
        exit(1);
    }

    /* Connect to Altibase Server */
    rc = db_connect();
    if ( rc != SQL_SUCCESS )
    {
        free_handle();
        exit(1);
    }

    rc = execute_select();
    if ( rc != SQL_SUCCESS )
    {
        free_handle();
        exit(1);
    }

    free_handle();
}


static void print_diagnostic(SQLSMALLINT aHandleType, SQLHANDLE aHandle)
{
    SQLRETURN   rc;
    SQLSMALLINT sRecordNo;
    SQLCHAR     sSQLSTATE[6];
    SQLCHAR     sMessage[2048];
    SQLSMALLINT sMessageLength;
    SQLINTEGER  sNativeError;

    sRecordNo = 1;

    while ((rc = SQLGetDiagRec(aHandleType,
                               aHandle,
                               sRecordNo,
                               sSQLSTATE,
                               &sNativeError,
                               sMessage,
                               sizeof(sMessage),
                               &sMessageLength)) != SQL_NO_DATA)
    {
        printf("Diagnostic Record %d\n", sRecordNo);
        printf("     SQLSTATE     : %s\n", sSQLSTATE);
        printf("     Message text : %s\n", sMessage);
        printf("     Message len  : %d\n", sMessageLength);
        printf("     Native error : 0x%X\n", sNativeError);

        if (rc != SQL_SUCCESS && rc != SQL_SUCCESS_WITH_INFO)
        {
            break;
        }

        sRecordNo++;
    }
}

void execute_err(SQLHDBC aCon, SQLHSTMT aStmt, char* q)
{
    printf("Error : %s\n",q);

    if (aStmt == SQL_NULL_HSTMT)
    {
        if (aCon != SQL_NULL_HDBC)
        {
            print_diagnostic(SQL_HANDLE_DBC, aCon);
        }
    }
    else
    {
        print_diagnostic(SQL_HANDLE_STMT, aStmt);
    }
}

SQLRETURN alloc_handle()
{
    /* allocate Environment handle */
    if (SQLAllocEnv(&env) != SQL_SUCCESS)
    {
        printf("SQLAllocEnv error!!\n");
        return SQL_ERROR;
    }

    /* allocate Connection handle */
    if (SQLAllocConnect(env, &dbc) != SQL_SUCCESS)
    {
        printf("SQLAllocConnect error!!\n");
        return SQL_ERROR;
    }
    return SQL_SUCCESS;
}

void free_handle()
{
    if ( conn_flag == 1 )
    {
        /* close connection */
        SQLDisconnect( dbc );
    }
    /* free connection handle */
    if ( dbc != NULL )
    {
        SQLFreeConnect( dbc );
    }
    if ( env != NULL )
    {
        SQLFreeEnv( env );
    }
}

SQLRETURN db_connect()
{
    char    *USERNAME = "SYS";        // user name
    char    *PASSWD   = "MANAGER";    // user password
    char    *NLS      = "US7ASCII";   // NLS_USE ( KO16KSC5601, US7ASCII )
    char     connStr[1024];

    sprintf(connStr,
            "DSN=127.0.0.1;UID=%s;PWD=%s;CONNTYPE=%d;NLS_USE=%s", /* ;PORT_NO=20300", */
            USERNAME, PASSWD, 1, NLS);

    /* establish connection */
    if (SQLDriverConnect( dbc, NULL, (SQLCHAR *)connStr, SQL_NTS,
                          NULL, 0, NULL,
                          SQL_DRIVER_NOPROMPT ) != SQL_SUCCESS)
    {
        execute_err(dbc, SQL_NULL_HSTMT, "SQLDriverConnect");
        return SQL_ERROR;
    }

    conn_flag = 1;

    return SQL_SUCCESS;
}

SQLRETURN execute_select()
{
    SQLHSTMT     stmt = SQL_NULL_HSTMT;
    SQLRETURN    rc;
    int          i;
    char         query[SQL_LEN];

    SQLSMALLINT  columnCount;
    char         columnName[50];
    SQLSMALLINT  columnNameLength;
    SQLSMALLINT  dataType;
    SQLSMALLINT  scale;
    SQLSMALLINT  nullable;
    SQLULEN      columnSize;

    void       **columnPtr;
    SQLLEN      *columnInd;

    /* allocate Statement handle */
    if (SQL_ERROR == SQLAllocStmt(dbc, &stmt))
    {
        printf("SQLAllocStmt error!!\n");
        return SQL_ERROR;
    }

    sprintf(query,"SELECT * FROM DEMO_EX1");
    if (SQLExecDirect(stmt, (SQLCHAR *)query, SQL_NTS) != SQL_SUCCESS)
    {
        execute_err(dbc, stmt, query);
        SQLFreeStmt(stmt, SQL_DROP);
        return SQL_ERROR;
    }

    SQLNumResultCols(stmt, &columnCount);
    columnPtr = (void**) malloc( sizeof(void*) * columnCount );
    columnInd = (SQLLEN*) malloc( sizeof(SQLLEN) * columnCount );
    if ( columnPtr == NULL )
    {
        return SQL_ERROR;
    }

    for ( i=0; i<columnCount; i++ )
    {
        SQLDescribeCol(stmt, i+1,
                       (SQLCHAR *)columnName, sizeof(columnName), &columnNameLength,
                       &dataType, &columnSize, &scale, &nullable);
        printf("columnName = %s, nullable = %d\n", columnName, nullable);
        switch (dataType)
        {
        case SQL_CHAR:
            printf("%s : CHAR(%d)\n", columnName, columnSize);
            columnPtr[i] = (char*) malloc( columnSize + 1 );
            SQLBindCol(stmt, i+1, SQL_C_CHAR, columnPtr[i], columnSize+1, &columnInd[i]);
            break;
        case SQL_VARCHAR:
            printf("%s : VARCHAR(%d)\n", columnName, columnSize);
            columnPtr[i] = (char*) malloc( columnSize + 1 );
            SQLBindCol(stmt, i+1, SQL_C_CHAR, columnPtr[i], columnSize+1, &columnInd[i]);
            break;
        case SQL_INTEGER:
            printf("%s : INTEGER\n", columnName);
            columnPtr[i] = (int*) malloc( sizeof(int) );
            SQLBindCol(stmt, i+1, SQL_C_SLONG, columnPtr[i], 0, &columnInd[i]);
            break;
        case SQL_SMALLINT:
            printf("%s : SMALLINT\n", columnName);
            columnPtr[i] = (short*) malloc( sizeof(short) );
            SQLBindCol(stmt, i+1, SQL_C_SSHORT, columnPtr[i], 0, &columnInd[i]);
            break;
        case SQL_NUMERIC:
            printf("%s : NUMERIC(%d,%d)\n", columnName, columnSize, scale);
            columnPtr[i] = (double*) malloc( sizeof(double) );
            SQLBindCol(stmt, i+1, SQL_C_DOUBLE, columnPtr[i], 0, &columnInd[i]);
            break;
        case SQL_TYPE_TIMESTAMP:
            printf("%s : DATE\n", columnName);
            columnPtr[i] = (SQL_TIMESTAMP_STRUCT*) malloc( sizeof(SQL_TIMESTAMP_STRUCT) );
            SQLBindCol(stmt, i+1, SQL_C_TYPE_TIMESTAMP, columnPtr[i], 0, &columnInd[i]);
            break;
        }
    }

    /* fetches next rowset of data from the result set and print to stdout */
    printf("==========================================================================\n");
    while ( (rc = SQLFetch(stmt)) != SQL_NO_DATA)
    {
        if ( rc != SQL_SUCCESS )
        {
            execute_err(dbc, stmt, query);
            break;
        }
        for ( i=0; i<columnCount; i++ )
        {
            SQLDescribeCol(stmt, i+1,
                           NULL, 0, NULL,
                           &dataType, NULL, NULL, NULL);
            if ( columnInd[i] == SQL_NULL_DATA )
            {
                printf("NULL\t");
                continue;
            }
            switch (dataType)
            {
            case SQL_CHAR:
            case SQL_VARCHAR:
                printf("%s\t", columnPtr[i]);
                break;
            case SQL_INTEGER:
                printf("%d\t", *(int*)columnPtr[i]);
                break;
            case SQL_SMALLINT:
                printf("%d\t", *(short*)columnPtr[i]);
                break;
            case SQL_NUMERIC:
                printf("%10.3f\t", *(double*)columnPtr[i]);
                break;
            case SQL_TYPE_TIMESTAMP:
                printf("%4d/%02d/%02d %02d:%02d:%02d\t",
                        ((SQL_TIMESTAMP_STRUCT*)columnPtr[i])->year,
                        ((SQL_TIMESTAMP_STRUCT*)columnPtr[i])->month,
                        ((SQL_TIMESTAMP_STRUCT*)columnPtr[i])->day,
                        ((SQL_TIMESTAMP_STRUCT*)columnPtr[i])->hour,
                        ((SQL_TIMESTAMP_STRUCT*)columnPtr[i])->minute,
                        ((SQL_TIMESTAMP_STRUCT*)columnPtr[i])->second);
                break;
            }
        }
        printf("\n");
    }

    SQLFreeStmt(stmt, SQL_DROP);

    for ( i=0; i<columnCount; i++ )
    {
        free( columnPtr[i] );
    }
    free( columnPtr );
    free( columnInd );

    return SQL_SUCCESS;
}
```

### Sample of Using Metadata

```
/***********************************************
**  File name = demo_meta1.cpp
**  Meta data search program example
************************************************/
#include <sqlcli.h>
#include <stdio.h>
#include <stdlib.h>

#define SQL_LEN 1000
#define MSG_LEN 1024

SQLHENV  env;  // Environment Handle
SQLHDBC  dbc;  // Connection Handle
int      conn_flag;

SQLRETURN alloc_handle();
SQLRETURN db_connect();
void free_handle();

SQLRETURN get_tables();
void execute_err(SQLHDBC aCon, SQLHSTMT aStmt, char* q);

int main()
{
    SQLRETURN    rc;

    env = SQL_NULL_HENV;
    dbc = SQL_NULL_HDBC;
    conn_flag = 0;

    /* allocate handle */
    rc = alloc_handle();
    if ( rc != SQL_SUCCESS )
    {
        free_handle();
        exit(1);
    }

    /* Connect to Altibase Server */
    rc = db_connect();
    if ( rc != SQL_SUCCESS )
    {
        free_handle();
        exit(1);
    }

    rc = get_tables();
    if ( rc != SQL_SUCCESS )
    {
        free_handle();
        exit(1);
    }

    free_handle();
}


static void print_diagnostic(SQLSMALLINT aHandleType, SQLHANDLE aHandle)
{
    SQLRETURN   rc;
    SQLSMALLINT sRecordNo;
    SQLCHAR     sSQLSTATE[6];
    SQLCHAR     sMessage[2048];
    SQLSMALLINT sMessageLength;
    SQLINTEGER  sNativeError;

    sRecordNo = 1;

    while ((rc = SQLGetDiagRec(aHandleType,
                               aHandle,
                               sRecordNo,
                               sSQLSTATE,
                               &sNativeError,
                               sMessage,
                               sizeof(sMessage),
                               &sMessageLength)) != SQL_NO_DATA)
    {
        printf("Diagnostic Record %d\n", sRecordNo);
        printf("     SQLSTATE     : %s\n", sSQLSTATE);
        printf("     Message text : %s\n", sMessage);
        printf("     Message len  : %d\n", sMessageLength);
        printf("     Native error : 0x%X\n", sNativeError);

        if (rc != SQL_SUCCESS && rc != SQL_SUCCESS_WITH_INFO)
        {
            break;
        }

        sRecordNo++;
    }
}

void execute_err(SQLHDBC aCon, SQLHSTMT aStmt, char* q)
{
    printf("Error : %s\n",q);

    if (aStmt == SQL_NULL_HSTMT)
    {
        if (aCon != SQL_NULL_HDBC)
        {
            print_diagnostic(SQL_HANDLE_DBC, aCon);
        }
    }
    else
    {
        print_diagnostic(SQL_HANDLE_STMT, aStmt);
    }
}


SQLRETURN alloc_handle()
{
    /* allocate Environment handle */
    if (SQLAllocEnv(&env) != SQL_SUCCESS)
    {
        printf("SQLAllocEnv error!!\n");
        return SQL_ERROR;
    }

    /* allocate Connection handle */
    if (SQLAllocConnect(env, &dbc) != SQL_SUCCESS)
    {
        printf("SQLAllocConnect error!!\n");
        return SQL_ERROR;
    }
    return SQL_SUCCESS;
}

void free_handle()
{
    if ( conn_flag == 1 )
    {
        /* close connection */
        SQLDisconnect( dbc );
    }
    /* free connection handle */
    if ( dbc != NULL )
    {
        SQLFreeConnect( dbc );
    }
    if ( env != NULL )
    {
        SQLFreeEnv( env );
    }
}

SQLRETURN db_connect()
{
    char    *USERNAME = "SYS";        // user name
    char    *PASSWD   = "MANAGER";    // user password
    char    *NLS      = "US7ASCII";   // NLS_USE ( KO16KSC5601, US7ASCII )
    char     connStr[1024];

    sprintf(connStr,
            "DSN=127.0.0.1;UID=%s;PWD=%s;CONNTYPE=%d;NLS_USE=%s", /* ;PORT_NO=20300", */
            USERNAME, PASSWD, 1, NLS);

    /* establish connection */
    if (SQLDriverConnect( dbc, NULL, (SQLCHAR *) connStr, SQL_NTS,
                          NULL, 0, NULL,
                          SQL_DRIVER_NOPROMPT ) != SQL_SUCCESS)
    {
        execute_err(dbc, SQL_NULL_HSTMT, "SQLDriverConnect");
        return SQL_ERROR;
    }

    conn_flag = 1;

    return SQL_SUCCESS;
}

SQLRETURN get_tables()
{
    SQLHSTMT     stmt = SQL_NULL_HSTMT;
    SQLRETURN    rc;

    char         schem[50+1] = {0};
    char         name[50+1] = {0};
    char         type[50+1] = {0};
    SQLLEN       schem_ind;
    SQLLEN       name_ind;
    SQLLEN       type_ind;

    /* allocate Statement handle */
    if (SQL_ERROR == SQLAllocHandle(SQL_HANDLE_STMT, dbc, &stmt))
    {
        printf("SQLAllocHandle error!!\n");
        return SQL_ERROR;
    }

    if (SQLTables(stmt,
                  NULL, 0,
                  NULL, 0,
                  NULL, 0,
                  NULL, 0) != SQL_SUCCESS)
    {
        execute_err(dbc, stmt, "SQLTables");
        SQLFreeStmt(stmt, SQL_DROP);
        return SQL_ERROR;
    }

    if (SQLBindCol(stmt, 2, SQL_C_CHAR,
                   schem, sizeof(schem), &schem_ind) != SQL_SUCCESS)
    {
        execute_err(dbc, stmt, "SQLBindCol");
        SQLFreeStmt(stmt, SQL_DROP);
        return SQL_ERROR;
    }

    if (SQLBindCol(stmt, 3, SQL_C_CHAR,
                   name, sizeof(name), &name_ind) != SQL_SUCCESS)
    {
        execute_err(dbc, stmt, "SQLBindCol");
        SQLFreeStmt(stmt, SQL_DROP);
        return SQL_ERROR;
    }

    if (SQLBindCol(stmt, 4, SQL_C_CHAR,
                   type, sizeof(type), &type_ind) != SQL_SUCCESS)
    {
        execute_err(dbc, stmt, "SQLBindCol");
        SQLFreeStmt(stmt, SQL_DROP);
        return SQL_ERROR;
    }

    /* fetches the next rowset of data from the result set and print to stdout */
    printf("TABLE_SCHEM\t\tTABLE_NAME\t\tTABLE_TYPE\n");
    printf("=============================================================\n");
    while ( (rc = SQLFetch(stmt)) != SQL_NO_DATA)
    {
        if ( rc == SQL_ERROR )
        {
            execute_err(dbc, stmt, "SQLFetch");
            break;
        }
        printf("%-40s%-40s%s\n", schem, name, type);
    }

    SQLFreeHandle(SQL_HANDLE_STMT, stmt);/* == SQLFreeStmt(stmt, SQL_DROP); */

    return SQL_SUCCESS;
}
```

### Example of Procedure Test Program

```
/***********************************************
**   File name = demo_ex6.cpp
** Example of procedure test program
************************************************/
#include <sqlcli.h>
#include <stdio.h>
#include <stdlib.h>


#define SQL_LEN 1000
#define MSG_LEN 1024

SQLHENV  env;  // Environment Handle
SQLHDBC  dbc;  // Connection Handle
int      conn_flag;

SQLRETURN alloc_handle();
SQLRETURN db_connect();
void free_handle();

SQLRETURN execute_proc();
SQLRETURN execute_select();

void execute_err(SQLHDBC aCon, SQLHSTMT aStmt, char* q);

int main()
{
    SQLRETURN    rc;

    env = SQL_NULL_HENV;
    dbc = SQL_NULL_HDBC;
    conn_flag = 0;

    /* allocate handle */
    rc = alloc_handle();
    if ( rc != SQL_SUCCESS )
    {
        free_handle();
        exit(1);
    }

    /* Connect to Altibase Server */
    rc = db_connect();
    if ( rc != SQL_SUCCESS )
    {
        free_handle();
        exit(1);
    }

    /* select data */
    rc = execute_select();
    if ( rc != SQL_SUCCESS )
    {
        free_handle();
        exit(1);
    }

    /* procedure execution */
    rc = execute_proc();
    if ( rc != SQL_SUCCESS )
    {
        free_handle();
        exit(1);
    }

    /* select data */
    rc = execute_select();
    if ( rc != SQL_SUCCESS )
    {
        free_handle();
        exit(1);
    }

    /* disconnect, free handles */
    free_handle();
}

void execute_err(SQLHDBC aCon, SQLHSTMT aStmt, char* q)
{
    SQLINTEGER errNo;
    SQLSMALLINT msgLength;
    SQLCHAR errMsg[MSG_LEN];

    printf("Error : %s\n",q);

    if (SQLError ( SQL_NULL_HENV, aCon, aStmt,
                   NULL, &errNo,
                   errMsg, MSG_LEN, &msgLength ) == SQL_SUCCESS)
    {
        printf(" Error : # %ld, %s\n", errNo, errMsg);
    }
}

SQLRETURN alloc_handle()
{
    /* allocate Environment handle */
    if (SQLAllocEnv(&env) != SQL_SUCCESS)
    {
        printf("SQLAllocEnv error!!\n");
        return SQL_ERROR;
    }

    /* allocate Connection handle */
    if (SQLAllocConnect(env, &dbc) != SQL_SUCCESS)
    {
        printf("SQLAllocConnect error!!\n");
        return SQL_ERROR;
    }
    return SQL_SUCCESS;
}

void free_handle()
{
    if ( conn_flag == 1 )
    {
        /* close connection */
        SQLDisconnect( dbc );
    }
    /* free connection handle */
    if ( dbc != NULL )
    {
        SQLFreeConnect( dbc );
    }
    if ( env != NULL )
    {
        SQLFreeEnv( env );
    }
}

SQLRETURN db_connect()
{
    char    *USERNAME = "SYS";        // user name
    char    *PASSWD   = "MANAGER";    // user password
    char    *NLS      = "US7ASCII";   // NLS_USE ( KO16KSC5601, US7ASCII )
    char     connStr[1024];

    sprintf(connStr,
            "DSN=127.0.0.1;UID=%s;PWD=%s;CONNTYPE=%d;NLS_USE=%s", /* ;PORT_NO=20300", */
            USERNAME, PASSWD, 1, NLS);

    /* establish connection */
    if (SQLDriverConnect( dbc, NULL, (SQLCHAR *) connStr, SQL_NTS,
                          NULL, 0, NULL,
                          SQL_DRIVER_NOPROMPT ) != SQL_SUCCESS)
    {
        execute_err(dbc, SQL_NULL_HSTMT, "SQLDriverConnect");
        return SQL_ERROR;
    }

    conn_flag = 1;

    return SQL_SUCCESS;
}

SQLRETURN execute_select()
{
    SQLHSTMT     stmt = SQL_NULL_HSTMT;
    SQLRETURN    rc;
    char         query[SQL_LEN];

    SQLINTEGER           id;
    char                 name[20+1];
    SQL_TIMESTAMP_STRUCT birth;

    /* allocate Statement handle */
    if (SQL_ERROR == SQLAllocStmt(dbc, &stmt))
    {
        printf("SQLAllocStmt error!!\n");
        return SQL_ERROR;
    }

    sprintf(query,"SELECT * FROM DEMO_EX6");
    if (SQLPrepare(stmt, (SQLCHAR *)query, SQL_NTS) != SQL_SUCCESS)
    {
        execute_err(dbc, stmt, query);
        SQLFreeStmt(stmt, SQL_DROP);
        return SQL_ERROR;
    }

    /* binds application data buffers to columns in the result set */
    if (SQLBindCol(stmt, 1, SQL_C_SLONG,
                   &id, 0, NULL) != SQL_SUCCESS)
    {
        printf("SQLBindCol error!!!\n");
        execute_err(dbc, stmt, query);
        SQLFreeStmt(stmt, SQL_DROP);
        return SQL_ERROR;
    }
    if (SQLBindCol(stmt, 2, SQL_C_CHAR,
                   name, sizeof(name), NULL) != SQL_SUCCESS)
    {
        printf("SQLBindCol error!!!\n");
        execute_err(dbc, stmt, query);
        SQLFreeStmt(stmt, SQL_DROP);
        return SQL_ERROR;
    }
    if (SQLBindCol(stmt, 3, SQL_C_TYPE_TIMESTAMP,
                   &birth, 0, NULL) != SQL_SUCCESS)
    {
        printf("SQLBindCol error!!!\n");
        execute_err(dbc, stmt, query);
        SQLFreeStmt(stmt, SQL_DROP);
        return SQL_ERROR;
    }

    /* fetches the next rowset of data from the result set and print to stdout */
    printf("id\t        Name\tbirth\n");
    printf("=====================================================================\n");
    if ( SQLExecute(stmt) != SQL_SUCCESS )
    {
        execute_err(dbc, stmt, "SQLExecute : ");
        SQLFreeStmt(stmt, SQL_DROP);
        return SQL_ERROR;
    }

    while ( (rc = SQLFetch(stmt)) != SQL_NO_DATA )
    {
        if ( rc != SQL_SUCCESS )
        {
            execute_err(dbc, stmt, query);
            break;
        }
        printf("%d%20s\t%4d/%02d/%02d %02d:%02d:%02d\n",
                id, name, birth.year, birth.month, birth.day,
                birth.hour, birth.minute, birth.second);
    }

    SQLFreeStmt(stmt, SQL_DROP);

    return SQL_SUCCESS;
}

SQLRETURN execute_proc()
{
    SQLHSTMT     stmt = SQL_NULL_HSTMT;
    char         query[SQL_LEN];

    SQLINTEGER           id;
    char                 name[20+1];
    SQL_TIMESTAMP_STRUCT birth;
    SQLINTEGER           ret = 0;

    SQLLEN               name_ind = SQL_NTS;

    /* allocate Statement handle */
    if (SQL_ERROR == SQLAllocStmt(dbc, &stmt))
    {
        printf("SQLAllocStmt error!!\n");
        return SQL_ERROR;
    }

    sprintf(query,"EXEC DEMO_PROC6( ?, ?, ?, ? )");

    /* prepares an SQL string for execution */
    if (SQLPrepare(stmt, (SQLCHAR *) query, SQL_NTS) != SQL_SUCCESS)
    {
        execute_err(dbc, stmt, query);
        SQLFreeStmt(stmt, SQL_DROP);
        return SQL_ERROR;
    }

    if (SQLBindParameter(stmt,
                         1, /* Parameter number, starting at 1 */
                         SQL_PARAM_INPUT, /* in, out, inout */
                         SQL_C_SLONG, /* C data type of the parameter */
                         SQL_INTEGER, /* SQL data type of the parameter : char(8)*/
                         0,          /* size of the column or expression, precision */
                         0,          /* The decimal digits, scale */
                         &id,        /* A pointer to a buffer for the parameter’s data */
                         0,          /* Length of the ParameterValuePtr buffer in bytes */
                         NULL        /* indicator */
                         ) != SQL_SUCCESS)
    {
        execute_err(dbc, stmt, query);
        SQLFreeStmt(stmt, SQL_DROP);
        return SQL_ERROR;
    }
    if (SQLBindParameter(stmt, 2, SQL_PARAM_INPUT,
                         SQL_C_CHAR, SQL_VARCHAR,
                         20,  /* varchar(20) */
                         0,
                         name, sizeof(name), &name_ind) != SQL_SUCCESS)
    {
        execute_err(dbc, stmt, query);
        SQLFreeStmt(stmt, SQL_DROP);
        return SQL_ERROR;
    }
    if (SQLBindParameter(stmt, 3, SQL_PARAM_INPUT,
                         SQL_C_TYPE_TIMESTAMP, SQL_DATE,
                         0, 0, &birth, 0, NULL) != SQL_SUCCESS)
    {
        execute_err(dbc, stmt, query);
        SQLFreeStmt(stmt, SQL_DROP);
        return SQL_ERROR;
    }
    if (SQLBindParameter(stmt, 4, SQL_PARAM_OUTPUT,
                         SQL_C_SLONG, SQL_INTEGER,
                         0, 0, &ret,
                         0,/* For all fixed size C data type, this argument is ignored */
                         NULL) != SQL_SUCCESS)
    {
        execute_err(dbc, stmt, query);
        SQLFreeStmt(stmt, SQL_DROP);
        return SQL_ERROR;
    }

    /* executes a prepared statement */

    id = 5;
    sprintf(name, "name5");
    birth.year=2004;birth.month=5;birth.day=14;
    birth.hour=15;birth.minute=17;birth.second=20;
    birth.fraction=0;
    name_ind = 5;            /* name => length=5 */
    if (SQLExecute(stmt) != SQL_SUCCESS)
    {
        execute_err(dbc, stmt, query);
        SQLFreeStmt(stmt, SQL_DROP);
        return SQL_ERROR;
    }
    else
    {
        printf("\n======= Result of exec procedure ======\n");
        printf("ret => %d\n\n", ret);
    }

    SQLFreeStmt(stmt, SQL_DROP);

    return SQL_SUCCESS;
}
```

## Appendix B. Data Types

This appendix describes the data types of Altibase SQL data types, C data types, and the data conversion.

### SQL Data Types

To find which data types the Altibase CLI supports, call SQLGetTypeInfo (). 

THe user can find out what data types the ODBC driver and Altibase CLI support by calling SQLGetTypeInfo ().

The following table shows the list of the Altibase SQL data types and the standard SQL type identifier.

| SQL Type Identifier | Data Types of Altibase | Comments                                                     |
| ------------------- | ---------------------- | ------------------------------------------------------------ |
| SQL_CHAR            | CHAR(n)                | Character string of fixed string length n.                   |
| SQL_VARCHAR         | VARCHAR(n)             | Variable-length character string with a maximum string length n. |
| SQL_WCHAR           | NCHAR(n)               | Unicode character data type with fixed length(n)N means the number of characters. |
| SQL_WVARCHAR        | NVARCHAR(n)            | Unicode character data type with variable length: If declared as fixed, SQL_WVARCHAR has a fixed length. If declared as variable, SQL_WVARCHAR has a variable length.N means the number of characters. |
| SQL_DECIMAL         | DECIMAL(p, s)          | Same data type as the NUMERIC data type                      |
| SQL_NUMERIC         | NUMERIC(p, s)          | Signed, exact, numeric value with a precision p and scale s (1<=p<=38, -84<=s<=126) |
| SQL_SMALLINT        | SMALLINT               | 2-byte integer data type(-2^15+1 ~ 2^15-1)                   |
| SQL_INTEGER         | INTEGER                | 4-byte integer data type(-2^31+1 ~ 2^31-1)                   |
| SQL_BIGINT          | BIGINT                 | 8-byte integer data type(-2^63+1 ~2^63-1)                    |
| SQL_REAL            | REAL                   | The same data type as Float of C                             |
| SQL_FLOAT           | FLOAT(p)               | Fixed decimal numeric type data from -1E+120 to 1E+120 (1<=p<=38) |
| SQL_DOUBLE          | DOUBLE                 | The same data type with DOUBLE of C                          |
| SQL_BLOB            | BLOB                   | Variable-length binary data type with up to 4 Giga Bytes length |
| SQL_CLOB            | CLOB                   | Variable-length character data type with up to 4 Giga Bytes length |
| SQL_TYPE_DATE       | DATE                   | Year, month, and day fields, conforming to the rules of the Gregorian calendar. |
| SQL_TYPE_TIME       | DATE                   | Hour, minute, and second fields, with valid values for hours of 00 to 23, valid values for minutes of 00 to 59, and valid values for seconds of 00 to 61. |
| SQL_TYPE_TIMESTAMP  | DATE                   | Year, month, day, hour, minute, and second fields, with valid values as defined for the DATE and TIME data types. |
| SQL_INTERVAL        | \-                     | The result type of the DATE – DATE                           |
| SQL_BYTES           | BYTE(n)                | Binary data type with the fixed length as long as the specified size (1 byte<=n<=32000 bytes) |
| SQL_NIBBLE          | NIBBLE(n)              | Binary data type with the fixed length as long as the changeable size (n) (1 byte<=n<=255 bytes) |
| SQL_GEOMETRY        | GEOMETRY               | Internally, it implies properties of seven data types (Point, LineString, Polygon, GeometryCollection, MultiLineString, MultiPolygon, MultiPoint), and these implied properties can be distinguished as functions supported by each type: Fixed when declared as FIXED Use a storage of length and a variable length of storage if declared as VARIABLE |

### C Data Types

C data types refer to the data type of C buffer used to store the data in an application. 

C data type is specified with the type argument in SQLBindCol () and SQLGetData (), and in SQLBindParameter () with cType. 

The following table is the list of valid type identifiers for C data type. Also, the table lists the definitions of C data type of the ODBC Standard and the data types corresponding to each identifier.

| C Type Identifier    | ODBC C typedef       | C type                                                       |
| -------------------- | -------------------- | ------------------------------------------------------------ |
| SQL_C_CHAR           | SQLSCHAR \*          | char \*                                                      |
| SQL_C_WCHAR          | SQLWCHAR \*          | short \*                                                     |
| SQL_C_STINYINT       | SQLSCHAR             | signed char                                                  |
| SQL_C_UTINYINT       | SQLCHAR              | unsigned char                                                |
| SQL_C_SBIGINT        | SQLBIGINT            | \_int64                                                      |
| SQL_C_UBIGINT        | SQLUBIGINT           | unsigned \_int64                                             |
| SQL_C_SSHORT         | SQLSMALLINT          | short int                                                    |
| SQL_C_USHORT         | SQLUSMALLINT         | unsigned short int                                           |
| SQL_C_SLONG          | SQLINTEGER           | int                                                          |
| SQL_C_ULONG          | SQLUINTEGER          | unsigned int                                                 |
| SQL_C_FLOAT          | SQLREAL              | float                                                        |
| SQL_C_DOUBLE         | SQLDOUBLE            | double                                                       |
| SQL_C_BINARY         | SQLCHAR \*           | unsigned char \*                                             |
| C Type 식별자        | ODBC C typedef       | C type                                                       |
| SQL_C_TYPE_DATE      | SQL_DATE_STRUCT      | struct tagDATE_STRUCT { SQLSMALLINT year; SQLSMALLINT month; SQLSMALLINT day; } DATE_STRUCT |
| SQL_C_TYPE_TIME      | SQL_TIME_STRUCT      | struct tagTIME_STRUCT { SQLSMALLINT hour; SQLSMALLINT minute; SQLSMALLINT second; } TIME_STRUCT |
| SQL_C_TYPE_TIMESTAMP | SQL_TIMESTAMP_STRUCT | struct tagTIMESTAMP_STRUCT {SQLSMALLINT year; SQLSMALLINT month; SQLSMALLINT day; SQLSMALLINT hour; SQLSMALLINT minute; SQLSMALLINT second; SQLINTEGER fraction; **}** TIMESTAMP_STRUCT; |
| SQL_C_NIBBLE         | SQL_NIBBLE_STRUCT    | struct tagNIBBLE_STRUCT { SQLCHAR length; SQLCHAR value[1]; } NIBBLE_STRUCT |

### Converting SQL Data into C Data Types

![](media/CLI/CLI.1.94.1.jpg)



|                      | SQL_C_CHAR | SQL_C_WCHAR | SQL_C_BIT | SQL_C_STINYINT | SQL_C_UTINYINT | SQL_C_SBIGINT | SQL_C_UBIGINT | SQL_C_SSHORT | SQL_C_USHORT | SQL_C_SLONG | SQL_C_ULONG | SQL_C_FLOAT | SQL_C_DOUBLE | SQL_C_BINARY | SQL_C_TYPE_DATE | SQL_C_TYPE_TIME | SQL_C_TYPE_TIMESTAMP | SQL_C_BYTES | SQL_C_NIBBLE |
|----------------------|------------|-------------|-----------|----------------|----------------|---------------|---------------|--------------|--------------|-------------|-------------|-------------|--------------|--------------|-----------------|-----------------|----------------------|-------------|--------------|
| SQL_CHAR             | \#         |             | ○         | ○              | ○              |               |               |              |              |             |             |             |              | ○            |                 |                 |                      |             |              |
| SQL_VARCHAR          | \#         |             | ○         | ○              | ○              |               |               |              |              |             |             |             |              | ○            |                 |                 |                      |             |              |
| SQL_WCHAR            |            | \#          | ○         | ○              | ○              |               |               |              |              |             |             |             |              | ○            |                 |                 |                      |             |              |
| SQL_WVARCHAR         |            | \#          | ○         | ○              | ○              |               |               |              |              |             |             |             |              | ○            |                 |                 |                      |             |              |
| SQL_DECIMAL          | \#         |             | ○         | ○              | ○              | ○             | ○             | ○            | ○            | ○           | ○           | \#          | ○            | ○            |                 |                 |                      |             |              |
| SQL_NUMERIC          | \#         |             | ○         | ○              | ○              | ○             | ○             | ○            | ○            | ○           | ○           | \#          | ○            | ○            |                 |                 |                      |             |              |
| SQL_SMALLINT         | ○          |             | ○         | ○              | ○              | ○             | ○             | \#           | ○            | ○           | ○           | ○           | ○            | ○            |                 |                 |                      |             |              |
| (signed)             |            |             |           |                |                |               |               |              |              |             |             |             |              |              |                 |                 |                      |             |              |
| SQL_INTEGER          | ○          |             | ○         | ○              | ○              | ○             | ○             | ○            | ○            | \#          | ○           | ○           | ○            | ○            |                 |                 |                      |             |              |
| (signed)             |            |             |           |                |                |               |               |              |              |             |             |             |              |              |                 |                 |                      |             |              |
| SQL_BIGINT           | ○          |             | ○         | ○              | ○              | \#            | ○             | ○            | ○            | ○           | ○           | ○           | ○            | ○            |                 |                 |                      |             |              |
| (signed)             |            |             |           |                |                |               |               |              |              |             |             |             |              |              |                 |                 |                      |             |              |
| SQL_REAL             | ○          |             | ○         | ○              | ○              | ○             | ○             | ○            | ○            | ○           | ○           | \#          | ○            | ○            |                 |                 |                      |             |              |
| SQL_FLOAT            | \#         |             | ○         | ○              | ○              | ○             | ○             | ○            | ○            | ○           | ○           | \#          | ○            | ○            |                 |                 |                      |             |              |
| SQL_DOUBLE           | ○          |             | ○         | ○              | ○              | ○             | ○             | ○            | ○            | ○           | ○           | ○           | \#           | ○            |                 |                 |                      |             |              |
| SQL_BINARY           | ○          |             |           |                |                |               |               |              |              |             |             |             |              | \#           |                 |                 |                      |             |              |
| SQL_TYPE_DATE        | ○          |             |           |                |                |               |               |              |              |             |             |             |              | ○            | \#              |                 | ○                    |             |              |
| SQL_TYPE_TIME        | ○          |             |           |                |                |               |               |              |              |             |             |             |              | ○            |                 | \#              | ○                    |             |              |
| SQL_TYPE_TIMESTAMP   | ○          |             |           |                |                |               |               |              |              |             |             |             |              | ○            | ○               | ○               | \#                   |             |              |
| SQL_INTERVAL         | ○          |             |           |                |                |               |               |              |              |             |             | ○           | \#           | ○            |                 |                 |                      |             |              |
| SQL_BYTES            | ○          |             |           |                |                |               |               |              |              |             |             |             |              | ○            |                 |                 |                      | \#          |              |
| SQL_NIBBLE           | ○          |             |           |                |                |               |               |              |              |             |             |             |              | ○            |                 |                 |                      |             | \#           |
| SQL_GEOMETRY         |            |             |           |                |                |               |               |              |              |             |             |             |              | \#           |                 |                 |                      |             |              |

\# : Default conversion

○ : Supported conversion

### Converting C Data into SQL Data types

![](media/CLI/CLI.1.95.1.jpg)



|                      | SQL_CHAR | SQL_VARCHAR | SQL_WCHAR | SQL_WVARCHAR | SQL_DECIMAL | SQL_NUMERIC | SQL_SMALLINT(signed) | SQL_INTEGER(signed) | SQL_BIGINT(signed) | SQL_REAL | SQL_FLOAT | SQL_DOUBLE | SQL_BINARY | SQL_DATE | SQL_INTERVAL | SQL_BYTES | SQL_NIBBLE | SQL_GEOMETRY |
|----------------------|----------|-------------|-----------|--------------|-------------|-------------|----------------------|---------------------|--------------------|----------|-----------|------------|------------|----------|--------------|-----------|------------|--------------|
| SQL_C_CHAR           | \#       | \#          |           |              | \#          | \#          | ○                    | ○                   | ○                  | ○        | ○         | ○          | ○          | ○        |              | ○         | ○          |              |
| SQL_C_WCHAR          |          |             | \#        | \#           |             |             |                      |                     |                    |          |           |            |            |          |              |           |            |              |
| SQL_C_BIT            | ○        | ○           | ○         | ○            | ○           | ○           | ○                    | ○                   | ○                  | ○        | ○         | ○          |            |          |              |           |            |              |
| SQL_C_STINYINT       | ○        | ○           | ○         | ○            | ○           | ○           | ○                    | ○                   | ○                  | ○        | ○         | ○          |            |          |              |           |            |              |
| SQL_C_UTINYINT       | ○        | ○           | ○         | ○            | ○           | ○           | ○                    | ○                   | ○                  | ○        | ○         | ○          |            |          |              |           |            |              |
| SQL_C_SBIGINT        | ○        | ○           | ○         | ○            | ○           | ○           | ○                    | ○                   | \#                 | ○        | ○         | ○          |            |          |              |           |            |              |
| SQL_C_UBIGINT        | ○        | ○           | ○         | ○            | ○           | ○           | ○                    | ○                   | ○                  | ○        | ○         | ○          |            |          |              |           |            |              |
| SQL_C_SSHORT         | ○        | ○           | ○         | ○            | ○           | ○           | \#                   | ○                   | ○                  | ○        | ○         | ○          |            |          |              |           |            |              |
| SQL_C_USHORT         | ○        | ○           | ○         | ○            | ○           | ○           | ○                    | ○                   | ○                  | ○        | ○         | ○          |            |          |              |           |            |              |
| SQL_C_SLONG          | ○        | ○           | ○         | ○            | ○           | ○           | ○                    | \#                  | ○                  | ○        | ○         | ○          |            |          |              |           |            |              |
| SQL_C_ULONG          | ○        | ○           | ○         | ○            | ○           | ○           | ○                    | ○                   | ○                  | ○        | ○         | ○          |            |          |              |           |            |              |
| SQL_C_FLOAT          | ○        | ○           | ○         | ○            | ○           | ○           | ○                    | ○                   | ○                  | \#       | ○         | ○          |            |          |              |           |            |              |
| SQL_C_DOUBLE         | ○        | ○           | ○         | ○            | ○           | ○           | ○                    | ○                   | ○                  | ○        | \#        | \#         |            |          |              |           |            |              |
| SQL_C_BINARY         | ○        | ○           | ○         | ○            |             |             |                      |                     |                    |          |           |            | \#         |          |              |           |            | ○            |
| SQL_C_TYPE_DATE      |          |             |           |              |             |             |                      |                     |                    |          |           |            |            |          |              |           |            |              |
| SQL_C_TYPE_TIME      |          |             |           |              |             |             |                      |                     |                    |          |           |            |            | ○        |              |           |            |              |
| SQL_C_TYPE_TIMESTAMP |          |             |           |              |             |             |                      |                     |                    |          |           |            |            | ○        |              |           |            |              |
| SQL_C_BYTES          |          |             |           |              |             |             |                      |                     |                    |          |           |            |            | ○        |              | \#        |            |              |
| SQL_C_NIBBLE         |          |             |           |              |             |             |                      |                     |                    |          |           |            |            |          |              |           | \#         |              |

\# : Default conversion

○ : Supported conversion

## Appendix C. Error Codes

SQLError returns SQLSTATE values as defined in the X/Open and SQL Access Group SQL CAE specification (1992), and ODBC specifications. SQLSTATE is a five-byte alphanumeric string. This Appendix describes SQLSTATE values for Altibase CLI and ODBC.

### SQLSTATE

The following table displays SQLSTATE values that can be returned by SQLError of the Altibase CLI driver.

| SQLSTATE | Error                                                        | Can be returned from                                         |
| -------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 01004    | Data truncation (if the size of the value to be returned is larger than the size of the buffer) | SQLDescribeCol SQLFetch SQLGetData                           |
| 07006    | Restricted data type attribute violation                     | SQLBindParameter SQLExecute SQLFetch                         |
| 07009    | Invalid descriptor index                                     | SQLBindCol SQLBindParameter SQLColAttribute SQLDescribeCol SQLDescribeParam SQLGetData |

> \* For SQLSTATE 08001, 08002, 08003, and 08S01, refer to the next table.
>

| SQLSTATE | Error                                                        | Can be returned from                                         |
| -------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| HY000    | General error                                                | SQLAllocStmt SQLAllocConnect SQLBindCol SQLBindParameter SQLColAttribute SQLColumns SQLConnect SQLDescribeCol SQLDisconnect SQLDriverConnect SQLEndTran SQLExecDirect SQLExecute SQLFetch SQLFreeHandle SQLFreeStmt SQLGetData SQLNumParams SQLNumResultCols SQLPrepare SQLPrimaryKeys SQLProcedureColumns SQLProcedures SQLRowCount SQLSetAttribute SQLSetConnectAttr SQLSetEnvAttr SQLStatistics SQLTables |
| HY001    | Memory allocation error (Cannot allocate the requested memory for the ODBC driver to execute and complete the function.) | SQLAllocConnect SQLAllocStmt SQLBindCol SQLBindParameter SQLConnect SQLDriverConnect SQLExecDirect SQLGetTypeInfo SQLPrepare |
| HY003    | Invalid application buffer type (the cType argument value is not a valid C data type.) | SQLBindCol SQLBindParameter                                  |
| HY009    | Invalid argument (null pointer)                              | SQLAllocConnect SQLAllocStmt SQLBindParameter SQLExecDirect SQLForeignKeys SQLPrimaryKeys SQLProcedureColumns SQLProcedures SQLSpecialColumns SQLStatistics SQLTablePrivileges |
| HY010    | Function sequence error                                      | SQLAllocStmt SQLDescribeParam SQLGetData                     |
| HY090    | Invalid character string or buffer length                    | SQLBindParameter SQLDescribeCol SQLExecute SQLForeignKeys SQLGetData SQLGetStmtAttr SQLTablePrivileges |
| HY092    | Invalid attribute or option                                  | SQLGetStmtAttr                                               |
| HY105    | Invalid parameter type                                       | SQLBindParameter                                             |
| HYC00    | Unsupported attribute                                        | SQLGetConnectAttr SQLGetStmtAttr                             |

#### Database Connection-related Error Codes			

| SQLSTATE | Code    | Error                                                        | Can be returned from        |
| -------- | ------- | ------------------------------------------------------------ | --------------------------- |
| HY000    | 0x51001 | The character set does not exist.                            | SQLConnect SQLDriverConnect |
|          | 0x5003b | The communication buffer is insufficient. (It exceeded the length of the communication buffer.) | SQLExecute                  |
| HY001    | 0x5104A | Memory allocation error (Cannot allocate the memory requested for the driver to execute the function and complete execution) | SQLConnect SQLDriverConnect |
| 08001    | 0x50032 | The driver cannot set the connection to the database.        | SQLConnect SQLDriverConnect |

#### Network-related Error Codes

| SQLSTATE | Code    | Error                                                        | Can be returned from                                         |
| -------- | ------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 08002    | 0x51035 | The *dbc* is already connected to the database.              | SQLConnect SQLDriverConnect                                  |
| 08003    | 0x51036 | *stmt* is unconnected or disconnected.                       | SQLExecDirect SQLExecute SQLPrepare                          |
| 08S01    | 0x51043 | Communication channel error (Communication channel failure occurred before the execution of the function was complete between the ODBC driver and the database.) | SQLColumns SQLConnect SQLDriverConnect SQLExecDirect SQLExecute SQLFetch SQLForeignKeys SQLGetConnectAttr SQLPrepare SQLPrimaryKeys SQLProcedureColumns SQLProcedures SQLSetConnectAttr SQLSpecialColumns SQLStatistics SQLTablePrivileges SQLTables |

### Statement State Transition-related Errors

The following tables show how each state changes when an Altibase CLI function that uses an environment, connection or statement handle is called in a statement state. 

Altibase CLI statements have the following states.

| State | Description                                                                 |
|-------|-----------------------------------------------------------------------------|
| S0    | Unallocated statement. (The connection state must be connected connection.) |
| S1    | Allocated statement.                                                        |
| S2    | Prepared statement. (A (possibly empty) result set will be created.)        |
| S6    | Cursor positioned with SQLFetch.                                            |

The entry values in the transition table are as follows:

-   \-- : When the state remains the same after the function is executed

-   Sn : When the statement state is transitioned to a specified state

-   (IH) : Invalid Handle

-   (HY010) : Function sequence error

-   (24000) :

> Note*
>
> -   S : Success. In this case, the function returns one of the following values: SQL_SUCCESS_WITH_INFO or SQL_SUCCESS.
>   
>-   E : Error. In this case, the function returns SQL_ERROR.
> 
>-   R : Results. There is a result set when the statement is executed. (There is a possibility that the result set is an empty set.)
>   
> -   NR : No Results. There is no result set when the statement is executed.
>
> -   NF : No Data Found. The function returns SQL_NO_DATA.
>
> -   RD : Receive Done
>
> -   P : Prepared. The statement was prepared
>
> -   NP : Not Prepared. The statement was not prepared.
>

The following example shows how to view a statement state transition table for the SQLPrepare function.

<table>
   <tr>
      <th>S0 Unallocated</th>
      <th>S1Allocated</th>
      <th>S2 Prepared</th>
      <th>S6 Infetch</th>
   </tr>
   <tr>
      <td rowspan="2">(IH)</td>
       <td rowspan="2">S => S1</td>
       <td>S => S2 </td>
       <td rowspan="2">(24000)</td>
   </tr>  
   <tr> 
      <td>E => S1</td>
   </tr>
</table>
If the SQLPrepare function is called when the handle type is SQL_HANDLE_STMT and the statement state is S0, SQL_INVALID_Handle (IH) is returned. If SQLPrepare is called and successfully executed when the handle type is SQL_HANDLE_STMT and the state is S1, this state is retained. If SQLPrepare is called and successfully executed when the handle type is SQL_HANDLE_STMT and the state is S2, the statement state is transitioned to S2; if unsuccessful, the statement state remains S1 as before. If the function is called while the handle type is SQL_HANDLE_STMT and the state is S6, SQL_ERROR and SQLSTATE 24000 (Invalid Cursor State) are always returned.

**SQLAllocHandle**
<table>
   <tr>
      <th>S0 Unallocated</th>
      <th>S1Allocated</th>
      <th>S2 Prepared</th>
      <th>S6 Infetch</th>
   </tr>
   <tr>
      <td>--</td>
      <td rowspan="2">--</td>
       <td rowspan="2">--</td>  
       <td rowspan="2">--</td>
   </tr>  
   <tr> 
      <td>S1*</td>
   </tr>
</table>


>  \* When HandleType is SQL_HANDLE_STMT
>

**SQLBindCol**

| S0 Unallocated | S1 Allocated | S2 Prepared | S6 Infetch |
|----------------|--------------|-------------|------------|
| (IH)           | \--          | \--         | \--        |

**SQLBindParameter**

| S0 Unallocated | S1 Allocated | S2 Prepared | S6 Infetch |
|----------------|--------------|-------------|------------|
| (IH)           | \--          | \--         | \--        |

**SQLColumns, SQLGetTypeInfo, SQLPrimaryKeys, SQLProcedureColumns,
SQLProcedures, SQLStatistics, SQLTables**

<table>
   <tr>
      <th>S0 Unallocated</th>
      <th>S1Allocated</th>
      <th>S2 Prepared</th>
      <th>S6 Infetch</th>
   </tr>
   <tr>
      <td rowspan="2">(IH)</td>
      <td rowspan="2"> S => S6</td>
       <td >E => S1</td>  
       <td rowspan="2">(24000) </td>
   </tr>  
   <tr> 
      <td>S => S6 </td>
   </tr>
</table>


**SQLConnect**

| S0 Unallocated | S1 Allocated | S2 Prepared | S6 Infetch |
|----------------|--------------|-------------|------------|
| (Error)        | (Error)      | (Error)     | (Error)    |

**SQLDisconnect**

| S0 Unallocated | S1 Allocated | S2 Prepared | S6 Infetch |
|----------------|--------------|-------------|------------|
| \--            | \* =\> S0    | \* =\> S0   | \* =\> S0  |

> \* *When the SQLDisconnect function is called, all statements related to the connection handle are terminated. This function moves a connection from a connection state to an allocated connection state; the connection state is C4 (connected connection) before the statement state becomes S0.

**SQLDriverConnect**

Please refer to SQLConnect.

**SQLExecDirect**
<table>
   <tr>
      <th>S0 Unallocated</th>
      <th>S1Allocated</th>
      <th>S2 Prepared</th>
      <th>S6 Infetch</th>
   </tr>
   <tr>
      <td rowspan="3">(IH)</td>
      <td> S, NR => --</td>
      <td >S, NR => S1</td>  
      <td rowspan="3">(24000) </td>
   </tr>  
   <tr> 
   	  <td  rowspan="2">S, R => S6 </td>
      <td> S, R => S6  </td>
   </tr>
   <tr> 
      <td> E => S1 </td>
   </tr>
</table>


**SQLExecute**

<table>
   <tr>
      <th>S0 Unallocated</th>
      <th>S1Allocated</th>
      <th>S2 Prepared</th>
      <th>S6 Infetch</th>
   </tr>
   <tr>
      <td rowspan="3">(IH)</td>
      <td rowspan="3"> (HY010) </td>
      <td >S, NR => --</td>  
      <td rowspan="3">(24000) </td>
   </tr>  
   <tr> 
      <td> S, R => S6 </td>
   </tr>
   <tr> 
      <td> E => --  </td>
   </tr>
</table>

**SQLFetch**

<table>
   <tr>
      <th>S0 Unallocated</th>
      <th>S1Allocated</th>
      <th>S2 Prepared</th>
      <th>S6 Infetch</th>
   </tr>
   <tr>
      <td rowspan="2">(IH)</td>
      <td rowspan="2"> (HY010) </td>      
      <td rowspan="2">(HY010) </td>
      <td >S => --</td>  
   </tr>  
   <tr> 
      <td> RD || NF || E =>
(if NP => S1,
if P => S2)
</td>
   </tr>
</table>


**SQLFreeHandle**

| S0 Unallocated | S1 Allocated | S2 Prepared | S6 Infetch |
|----------------|--------------|-------------|------------|
| \--            | (HY010)      | (HY010)     | (HY010)    |
| (IH)           | S0           | S0          | S0         |

(1) When the handleType of the first row is SQL_HANDLE_ENV or SQL_HANDLE_DBC 

(2) When the handleType of the second row is SQL_HANDLE_STMT

**SQLFreeStmt**
<table>
   <tr>
      <th>S0 Unallocated</th>
      <th>S1Allocated</th>
      <th>S2 Prepared</th>
      <th>S6 Infetch</th>
   </tr>
   <tr>
      <td rowspan="2">(IH)</td>
      <td rowspan="2"> -- </td>      
      <td rowspan="2">--</td>
      <td >NP = > S1</td>  
   </tr>  
   <tr>
       <td> P => S2</td>
   </tr>
   <tr> 
      <td> (IH)</td>
      <td>S0</td>
      <td>S0</td>
      <td>S0</td>
   </tr>
</table>
(1) When *fOption* of the first row is SQL_CLOSE 

(2) When *fOption* of the second row is SQL_DROP

**SQLGetData**

| S0 Unallocated | S1 Allocated | S2 Prepared | S6 Infetch       |
|----------------|--------------|-------------|------------------|
| (IH)           | (HY010)      | (HY010)     | S \|\| NF =\> -- |


**SQLGetTypeInfo**

Please refer to SQLColumns.

**SQLNumResultCols**

| S0 Unallocated | S1 Allocated | S2 Prepared | S6 Infetch |
|----------------|--------------|-------------|------------|
| (IH)           | (HY010)      | S =\> --    | S =\> --   |

**SQLPrepare**
<table>
   <tr>
      <th>S0 Unallocated</th>
      <th>S1Allocated</th>
      <th>S2 Prepared</th>
      <th>S6 Infetch</th>
   </tr>
   <tr>
      <td rowspan="2">(IH)</td>
      <td rowspan="2">S => -- </td>      
      <td> S => --</td>
      <td rowspan="2">(24000) </td>  
   </tr>  
   <tr>
       <td> E => S1 </td>
   </tr>
</table>

**SQLPrimaryKeys**

Please refer to SQLColumns.

**SQLProcedureColumns**

Please refer to SQLColumns.

**SQLProcedures**

Please refer to SQLColumns.

**SQLSetConnectAttr**

| S0 Unallocated | S1 Allocated | S2 Prepared | S6 Infetch |
|----------------|--------------|-------------|------------|
| \--\*          | \--          | \--         | (24000)    |

> \* When the set Attribute is a connection attribute; please refer to SQLSetStmtAttr if the set Attribute is a statement attribute.

**SQLSetEnvAttr**

| S0 Unallocated | S1 Allocated | S2 Prepared | S6 Infetch |
|----------------|--------------|-------------|------------|
| (Error)        | (Error)      | (Error)     | (Error)    |

**SQLSetStmtAttr**
<table>
   <tr>
      <th>S0 Unallocated</th>
      <th>S1Allocated</th>
      <th>S2 Prepared</th>
      <th>S6 Infetch</th>
   </tr>
   <tr>
      <td rowspan="2">(IH)</td>
      <td rowspan="2">-- </td>      
      <td> (1) => -- </td>
      <td>(1) => --  </td>  
   </tr>  
   <tr>
       <td> (2) => (Error) </td>
       <td>(2) => (24000)  </td>
   </tr>
</table>

(1) When the Attribute argument is neither SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_TYPE, SQL_ATTR_SIMULATE_CURSOR, SQL_ATTR_USE_BOOKMARKS, SQL_ATTR_CURSOR_SCROLLABLE, nor SQL_ATTR_CURSOR_SENSITIVITY

(2) When the Attribute argument is either SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_TYPE, SQL_ATTR_SIMULATE_CURSOR, SQL_ATTR_USE_BOOKMARKS, SQL_ATTR_CURSOR_SCROLLABLE, or SQL_ATTR_CURSOR_SENSITIVITY

**SQLStatistics**

Please refer to SQLColumns.

**SQLTables**

Please refer to SQLColumns.

### State Transition Table

The following table lists the major functions that affect state transition:
<table>
  <tr>
    <th><img src="media/CLI/diagonal.png"/></th>
    <th>S0
UNALLOCATED
</th>
    <th>S1
ALLOCATED
</th>
    <th>S2
PREPARED
</th>
    <th>S6
INFETCH
</th>
  </tr>
  <tr>
        <td rowspan="2">Prepare</td>
        <td rowspan="2">(IH)</td>
        <td rowspan="2">S => S1</td>
        <td>S => S2</td>
        <td rowspan="2">(24000)</td>
  </tr>
  <tr>
   		<td>E => S1</td>
   </tr>
   <tr>
        <td rowspan="3">ExecDirect</td>
        <td rowspan="3">(IH)</td>
        <td>S,NR => S1</td>
        <td>S => S2</td>
        <td rowspan="3">(24000)</td>
    </tr>
    <tr>
        <td rowspan="2">S,R => S6</td>
        <td>S,R => S6</td>
    </tr>
    <tr>
    	<td>E => S1</td>
    </tr>
    <tr>
        <td rowspan="3">Execute</td>
        <td rowspan="3">(IH)</td>
        <td rowspan="3">(HY010)</td>
        <td>S,NR => S2</td>
        <td rowspan="3">(24000)</td>
    </tr>
    <tr>
        <td>S,R => S6</td>
    </tr>
    <tr>
    	<td>E => S2</td>
    </tr>
     <tr>
        <td rowspan="2">Fetch</td>
        <td rowspan="2">(IH)</td>
        <td rowspan="2">(HY010)</td>
        <td rowspan="2">(HY010)</td>
        <td>S => S6</td>        
    </tr>
    <tr>
        <td>RD || NF || E =>
(if NP => S1,
if P => S2 )
</td>
    </tr>
    <tr>
        <td rowspan="2">FreeStmt
(CLOSE)
</td>
        <td rowspan="2">(IH)</td>
        <td rowspan="2">S1</td>
        <td rowspan="2">S2</td>
        <td>NP => S1</td>        
    </tr>
    <tr>
        <td>P => S2</td>
    </tr>
    <tr>
    	<td>FreeStmt
(DROP)
</td>
    	<td>(IH)</td>
        <td>S0</td>
        <td>S0</td>
        <td>S0</td>
    </tr>
</table>

Cf )

\- (IH) : Invalid Handle (HY010) : Function Sequence Error

\- (24000) : Invalid Cursor State

\- S : Success E : Error except Network Error

\- R : Results NR : No Results NF : No data Found RD: Receive Done

\- P : Prepared NP : Not Prepared

## Appendix D. Upgrade

This appendix describes the requirements to make ODBC or Altibase CLI applications for Altibase 4 available for Altibase 5 as follows. 

The level of CLI interface has been improved since the upgrade to Altibase 5. Especially it has high compatibility with user applications and general purpose applications to follow the standard of X/Open CLI or ODBC specification to the highest degree.

This appendix explains data types newly added or defined, and other changes.

-   Data Types
-   Other Changes

### Data Type

This section describes data types newly added to Altibase 5. 

The user can resolve the problems derived from compiling the existing applications to firmly keep the standard compared to previous version.

#### SQLCHAR, SQLSCHAR

The previous CLI applications have used SQLCHAR and char together. However, standardoriented SQLCHAR is defined newly as follows.

```
typedef unsigned char SQLCHAR;
typedef signed char SQLSCHAR;
```

Therefore, errors occur when you compile the existing applications with the following statements.

```
char *query = “....”;
SQLPrepare(stmt, query, SQL_NTS);
```

The user only have to modify type casting as follows to solve this problem.

```
char *query = “....”;
SQLPrepare(stmt, (SQLCHAR *)query, SQL_NTS);
```

#### SQL_BIT, SQL_VARBIT

Subsequent releases, starting with version 5, support BIT type as standard SQL92 and VARBIT type for your convenience. Refer to *SQL Reference* for details about them.

##### BIT to C type

The following indicates conversion table related to BIT.	
<table>
   <tr>
      <th>C type id</th>
      <th>Test</th>
      <th>*TargetValuePtr</th>
      <th>*StrLen_or_IndPtr</th>
      <th>SQLSTATE</th>
   </tr>
   <tr>
      <td rowspan="2">SQL_C_CHAR</td>
      <td>BufferLength > 1</td>      
      <td>Data (‘0’ or ‘1’) </td>
      <td>1 </td>  
      <td>n/a</td>
   </tr>  
   <tr>
      <td>BufferLength <= 1</td>      
      <td>Undefined</td>
      <td>Undefined </td>  
      <td>22003</td>
   </tr>  
   <tr>
       <td> SQL_C_STINYINT
SQL_C_UTINYINT
SQL_C_SBIGINT
SQL_C_UBIGINT
SQL_C_SSHORT
SQL_C_USHORT
SQL_C_SLONG
SQL_C_ULONG
SQL_C_FLOAT
SQL_C_DOUBLE
SQL_C_NUMERIC
</td>
       <td>None(The values of
BufferLength have
the fixed type like
this, and they are
ignored in case of
coversion.)
  </td>
  <td>Data (0 or 1) </td>
  <td>Size of C type</td>
  <td>n/a</td> 
   </tr>
   <tr>
       <td>SQL_C_BIT</td>
       <td>None</td>
       <td>Data (0 or 1)</td>
       <td>1</td>
       <td>n/a</td>
   </tr>
    <tr>
       <td>SQL_C_BINARY</td>
       <td>None</td>
       <td>Data 
Data (See below
for formats)
</td>
       <td>Data length to be
written in the
memory the user
binds</td>
       <td>n/a</td>
   </tr>
</table>



##### VARBIT to C type

The following indicates conversion table related to VARBIT.
<table>
   <tr>
      <th>C type id</th>
      <th>Test</th>
      <th>*TargetValuePtr</th>
      <th>*StrLen_or_IndPtr</th>
      <th>SQLSTATE</th>
   </tr>
   <tr>
      <td rowspan="2">SQL_C_CHAR</td>
      <td>BufferLength > 1</td>      
      <td>Data</td>
      <td>Precision of varbit n </td>  
      <td>n/a</td>
   </tr>  
   <tr>
      <td>BufferLength <= 1</td>      
      <td>Undefined</td>
      <td>Undefined </td>  
      <td>22003</td>
   </tr>  
   <tr>
       <td> SQL_C_BIT</td>
       <td>None  </td>
       <td>Data (0 or 1)</td>
       <td>1</td>
       <td>n/a</td> 
   </tr>
   <tr>
       <td>SQL_C_BINARY</td>
       <td></td>
       <td>Data 
(Data (Its format
is same as that
of BIT)
</td>
       <td>Data length to be
written in the
memory the user
binds</td>
       <td>n/a</td>
   </tr>
</table>


##### C type to BIT/VARBIT

No type is converted to BIT currently.

##### Binary Format
<table>
    <tr>
      <td>0 7</td>      
      <td>8 15</td>
      <td>16 23 </td>  
      <td>24 31</td>
      <td>32 39</td>
      <td>...</td>
      <td>8n 8n+7</td>
   </tr>  
   <tr>
      <td colspan="4">Precision</td>
      <td colspan="3">Data ....</td>      
   </tr>  
</table>

where n= (Precision+7)/8 + 3

Precision : Length of BIT data

Data : BIT Data

##### Data Type Conversion Example

###### BIT/VARBIT SQL_C_BINARY

Data themselves are sent from server to user when you bind and fetch BIT to SQL_C_BINARY. Data formats sotred in user buffer are as mentioned above. 

The user can access to the server conveniently if specifying struct bit_t as the following examples and using it.

```
CREATE TABLE T1(I1 BIT(17), I2 VARBIT(37));
INSERT INTO T1 VALUES(BIT'11111011010011011', 
VARBIT'0010010010101110001010100010010011011');
INSERT INTO T1 VALUES(BIT'110011011',
VARBIT'001110001010100010010011011');

----------------------

void dump(unsigned char *Buffer, SQLINTEGER Length)
{
for (SQLINTEGER i = 0; i < Length; i++) 
{
printf(“%02X “, *(Buffer + i));
}
}

typedef struct bit_t
{
SQLUINTEGER mPrecision;
unsigned char mData[1];
} bit_t;

bit_t *Bit;
bit_t *Varbit;
SQLLEN Length;
SQLRETURN rc;

Bit = (bit_t *)malloc(BUFFER_SIZE);
Varbit = (bit_t *)malloc(BUFFER_SIZE);

SQLBindCol( stmt, 1, 
SQL_C_BINARY, 
(SQLPOINTER)Bit, 
BUFFER_SIZE, 
&LengthBit);

SQLBindCol( stmt, 2, 
SQL_C_BINARY, 
(SQLPOINTER)Varbit, 
BUFFER_SIZE, 
&LengthVarbit);
do
{
memset(Buffer, 0, BUFFER_SIZE);
rc = SQLFetch(stmt);

printf(“-----\n”);

printf(“>> Bit\n”);
printf(“Length : %d\n”, LengthBit);
printf(“Precision : %d\n”, Bit->mPrecision);
dump(Bit->mData, LengthBit – sizeof(SQLUINTEGER));

printf(“>> Varbit\n”);
printf(“Length : %d\n”, LengthVarbit);
printf(“Precision : %d\n”, Varbit->mPrecision);
dump(Varbit->mData, LengthVarbit – sizeof(SQLUINTEGER));
} while (rc != SQL_NO_DATA);
When the above program is executed, the following output is displayed.
------
>> Bit
Length : 7
Precision : 17
FB 4D 80 (1111 1011 0100 1101 1)
>> Varbit
Length : 9
Precision : 37
24 AE 2A 24 D8 (0010 0100 1010 1110 0010 1010 0010 0100 1101 1)
------
>> Bit
Length : 7
Precision : 17 -> Precision indicates 17 because “0” bit is appended.
CD 80 00 (1100 1101 1000 0000)
>> Varbit
Length : 8
Precision : 27 ->  Precision indicates 27 because VARBIT doesn’t perform padding.
38 A8 93 60 (0011 1000 1010 1000 1001 0011 011)
```

If BUFFER_SIZE is less than required, SQLFetch() returns SQL_SUCCESS_WITH_INFO, and wirtes its data in the memory bound as BUFFER_SIZE.

###### BIT/VARBIT to SQL_C_BIT

SQL_C_BIT of ODBC requires special care because it is the unsigned 8bit integer whose value is 0 or 1. In other words, bound variables don’t have 0x64 but 0x01 even though BIT ‘011001’ is stored on the table of server when you bind them with SQL_C_BIT and fetch them.

###### BIT to SQL_C_CHAR

If you bind BIT column with SQL_C_CHAR when fetching it, the result always has 0 or 1 following ODBC type conversion rules.

```
CREATE TABLE T1 (I1 BIT(12));
INSERT INTO T1 VALUES(BIT’110011000010’);
INSERT INTO T1 VALUES(BIT’010011000010’);

SQLCHAR sData[128];
SQLLEN sLength;

sQuery = (SQLCHAR *)”SELECT I1 FROM T1”;

SQLBindCol(stmt, 1, SQL_C_CHAR, sData, sizeof(sData), sLength);

SQLExecDirect(stmt, sQuery, SQL_NTS);

while (SQLFetch(stmt) != SQL_NO_DATA)
{
printf(“bit value = %s, ”, sData);
printf(“sLength = %d\n”, sLength);
}
When the above program is executed, the following output is displayed.
1, sLength = 1
0, sLength = 1
```

###### VARBIT to SQL_C_CHAR

Since there is no VARBIT type in the ODBC standard, so the conversion tool is built on its own, when fetching a VARBIT column, all the data in that column is fetched.

```
CREATE TABLE T1 (I1 VARBIT(12));
INSERT INTO T1 VALUES(VARBIT’110011000010’);
INSERT INTO T1 VALUES(VARBIT’01011010’);

SQLCHAR sData[128];
SQLLEN sLength;
sQuery = (SQLCHAR *)”SELECT I1 FROM T1”;
SQLBindCol(stmt, 1, SQL_C_CHAR, sData, sizeof(sData), &sLength);
SQLExecDirect(stmt, sQuery, SQL_NTS);
while (SQLFetch(stmt) != SQL_NO_DATA)
{
printf(“bit value = %s, ”, sData);
printf(“sLength = %d\n”, sLength);
}
When the above program is executed, the following output is displayed.
110011000010, sLength = 12
01011010, sLength = 8
```

#### SQL_NIBBLE

SQL_C_NIBBLE supported in Altibase 4 is not available to Altibase 5. However, you can fetch data with SQL_C_BINARY.

##### NIBBLE to C type

Conversion is available only to SQL_C_CHAR and SQL_C_BINARY.
<table>
   <tr>
      <th>C type id</th>
      <th>Test</th>
      <th>*TargetValuePtr</th>
      <th>*StrLen_or_IndPtr</th>
      <th>SQLSTATE</th>
   </tr>
   <tr>
      <td rowspan="2">SQL_C_CHAR</td>
      <td>BufferLength > 1</td>      
      <td>Data (‘0’ or ‘1’) </td>
      <td>Data length to be
written in the
memory the user
binds (Except null
and termination
character) </td>  
      <td>n/a</td>
   </tr>  
   <tr>
      <td>BufferLength <= 1</td>      
      <td>Undefined</td>
      <td>Undefined </td>  
      <td>22003</td>
   </tr>  
   <tr>
       <td> SQL_C_BINARY</td>
       <td>None  </td>
       <td>Data (See below
for formats)
</td>
       <td>Data length to be
written in the
memory the user
binds</td>
       <td>n/a</td> 
   </tr>
</table>

NIBBLE is fetched in binary format in the same way as BIT, but binary format of NIBBLE is different from that of BIT because its precision field has 1 byte integer.

##### Binary Format

<table>
    <tr>
      <td>0 7</td>      
      <td>8 15</td>
      <td>...</td>
      <td>8n 8n+7</td>
   </tr>  
   <tr>
      <td colspan="2">Precision</td>
      <td colspan="2">Data ....</td>      
   </tr>  
</table>
Where n = (Precision+1)/2

Precision : Length of NIBBLE data

Data : Nibble Data

##### Data Type Conversion Example

###### NIBBLE to SQL_C_BINARY

Data themselves are sent from server to user when you bind and fetch NIBBLE to SQL_C_BINARY. Data types stored in user buffer are as metioned above.

The user can access to the server conveniently if specifying nibble_t as the results are as follows.

```
CREATE TABLE T1(I1 NIBBLE, I2 NIBBLE(10), I3 NIBBLE(21) NOT NULL);
INSERT INTO T1 VALUES(NIBBLE'A', NIBBLE'0123456789', NIBBLE'0123456789ABCDEF00121');
INSERT INTO T1 VALUES(NIBBLE'B', NIBBLE'789', NIBBLE'ABCD1234');

-------------------

void dump(unsigned char *Buffer, int Length)
{
for (int i = 0; i < Length; i++) printf(“%02X “, *(Buffer + i));
}

typedef struct nibble_t
{
unsigned char mPrecision;
unsigned char mData[1];
} nibble_t;

nibble_t *Buffer;
SQLLEN Length;
SQLRETURN rc;

Buffer = (nibble_t *)malloc(BUFFER_SIZE);

SQLBindCol(stmt, 2, SQL_C_BINARY, (SQLPOINTER)Buffer, BUFFER_SIZE, &Length);
do
{
memset(Buffer, 0, BUFFER_SIZE);
rc = SQLFetch(stmt);

printf(“----\n”);
printf(“Length : %d\n”, Length);
printf(“Precision : %d\n”, Buffer->mPrecision);
dump(Buffer->mData, Length – sizeof(SQLUINTEGER));
} while (rc != SQL_NO_DATA);
When the above program is executed, the following output is displayed.
Length : 6
Precision : 10
01 23 45 67 89
----
Length : 3
Precision : 3
78 90
```

###### NIBBLE to SQL_C_CHAR

Examples and results are omitted cause of no unusual events in this case.

#### SQL_BYTE

This is bound to SQL_C_BINARY instead of SQL_C_BYTE in Altibase 4 and then is executed in the same way as this is in Altibase 4

##### BYTE to C types

Conversion to other types is not available except SQL_C_CHAR and SQL_C_BINARY. However, original data requires special care that its 1 byte is expressed as ASCII 2 characters when you convert binary data to SQL_C_CHAR.
<table>
   <tr>
      <th>C type id</th>
      <th>Test</th>
      <th>*TargetValuePtr</th>
      <th>*StrLen_or_IndPtr</th>
      <th>SQLSTATE</th>
   </tr>
   <tr>
      <td rowspan="2">SQL_C_CHAR</td>
      <td>(Byte length of data) * 2 < BufferLength </td>      
      <td>Data</td>
      <td>Length of data in bytes</td>  
      <td>n/a</td>
   </tr>  
   <tr>
      <td>(Byte length of data) * 2 >= BufferLength</td>      
      <td>Truncated data</td>
      <td>Length of data in bytes </td>  
      <td>01004</td>
   </tr>  
   <tr>
       <td rowspan="2"> SQL_C_BINARY</td>
       <td>Byte length of data <= BufferLength  </td>
       <td>Data </td>
       <td>Length of data in bytes</td>
       <td>n/a</td> 
   </tr>
   <tr>
       <td>Byte length of data > BufferLength</td>
       <td>Truncated data</td>
       <td>Length of data in bytes</td>
       <td>01004</td>
   </tr>
</table>
Each byte of binary data is always converted to a pair of hex characters when the Altibase CLI converts them to SQL_C_CHAR. Therefore, if buffer size of bound SQL_C_CHAR indicates the even, NULL termination character is printed not in the last byte of it but in ahead of that.

<table>
   <tr>
      <th>Source binary data
(hex characters)
</th>
      <th>Size of bound buffer
(bytes)
</th>
      <th>Contents of the buffer bound as SQL_C_CHAR</th>
      <th>*StrLen_or_IndPtr</th>
      <th>SQLSTATE</th>
   </tr>
   <tr>
      <td rowspan="2">AA BB 11 12</td>
      <td>8 </td>      
      <td>hex : 41 41 42 42 31 31 00 ??<sup>1</sup> 
string : “AABB11”
</td>
      <td>8</td>  
      <td>01004</td>
   </tr>  
     <tr>
      <td>9 </td>      
      <td>hex : 41 41 42 42 31 31 31 32 00
string : “AABB1112”
</td>
      <td>8</td>  
      <td>n/a</td>
   </tr>  
</table>

[<sup>1</sup>] The part marked with ?? is not defined.

##### Binary Format	

Byte type doesn't have special format like NIBBLE or BIT, but is the conjuction of binary data.

##### Data Type Conversion Example

###### BYTE to SQL_C_CHAR

```
CREATE TABLE T1(I1 BYTE(30));
INSERT INTO T1 VALUES(BYTE’56789ABC’);

-------------------
SQLLEN Length;
SQLRETURN rc;

// execution query : SELECT * FROM T1;

Buffer = (nibble_t *)malloc(BUFFER_SIZE);

SQLBindCol(stmt, 1, SQL_C_CHAR, (SQLPOINTER)Buffer, BUFFER_SIZE, &Length);
do
{
memset(Buffer, 0, BUFFER_SIZE);
rc = SQLFetch(stmt);
printf(“Length : %d\n”, Length);
printf(“Data : %s\n”, Length);
} while (rc != SQL_NO_DATA);
When the above program is executed, the following output is displayed.
Execution Query 1 : BUFFER_SIZE >= 9
Length : 8
Data : 56789ABC

Execution Query 2 : BUFFER_SIZE == 8
Length : 8
Data : 56789A -> 8 This is bound in byte buffer, and then only 6 characters are expressed.

Execution Query 3 : BUFFER_SIZE == 7
Length : 8
Data : 56789A -> same as BUFFER_SIZE == 8

Execution Query 4 : BUFFER_SIZE == 6
Length : 8
Data : 5678

SQLFetch() returns SQL_SUCCESS_WITH_INFO for execution results except 1. SQLSTATE
indicates 01004.
```

###### BYTE to SQL_C_BINARY

No unusual events for binding to binary in this case.

#### DATE : SQL_TYPE_TIMESTAMP

SQL_TYPE_TIMESTAMP is retuned when Altibase 5 inserts data as SQL Type into DATE column with using SQLDescribeCol() or SQLColAttribute(). SQL_TYPE_TIMESTAMP is similar to Altibase DATE type of ODBC standard, and consists of year, month, day, hour and second.

However, if you call SQLColAttribute() or SQLDescribeCol(), SQL_DATE is returned as SQL type because DATE type in Altibase 4 consists of basic elements such as day and hour, and much data such as special characters separating basic elements. 

Therefore, when you use the Altibase CLI of Altibase 5, SQL_TYPE_DATE, SQL_TYPE_TIME and SQL_TYPE_TIMESTAMP as constant numbers for ODBC 3.0 are recommended.

#### LOB

##### Data Type

In Altibase 4, length of LOB type is limited to page size. However, it consists of BLOB and CLOB supporting maximum 2GB.

###### Altibase 4 DDL

```
CREATE TABLE T1 (I1 BLOB(3));
```

###### Altibase 5 DDL

```
CREATE TABLE T1 (I1 BLOB); ---> This precision in brackets disappears.
```

##### Using LOB Functions

Altibase CLI application supports private functions to use LOB. Refer to Chapter3: LOB Interface for details about special functions for LOB. 

You can use functions available to general binary and character type except functions for LOB. You can store and search LOB data with standard ODBC in ODBC application cause of these features. 

You can’t update and retrieve data partially in ODBC application, whereas you can in Altibase CLI application with SQLGetLob and SQLPutLob.

```
CREATE TABLE T1 (I1 BLOB, I2 CLOB);  // Turn off the AUTOCOMMIT mode of the connection.

SQLCHAR sBlobData[128];
SQLCHAR sClobData[128];
SQLLEN sBlobLength;
SQLLEN sClobLength;

SQLCHAR *sQuery = (SQLCHAR *)”INSERT INTO T1 VALUES(?, ?)”;
SQLPrepare(stmt, sQuery, SQL_NTS);

SQLBindParameter(stmt, 1, SQL_C_BINARY, SQL_BLOB,0, 0, sBlobData, sizeof(sBlobData), sBlobLength);
SQLBindParameter(stmt, 2, SQL_C_CHAR, SQL_CLOB,0, 0, sClobData, sizeof(sClobData), &sClobLength);
sBlobLength = create_blob_data(sBlobData);
sprintf((char *)sClobData, “this is clob data”);
sClobLength = SQL_NTS;

SQLExecute(stmt);
```

##### Using LOB in ODBC application

If you want to fetch LOB column in ODBC application and store data in LOB column, call SQLDescribeCol, SQLColAttribute or SQLDescribeParam. 

If you execute these functions in LOB column, they are returned as data types of SQL_BLOB and SQL_CLOB. However, ODBC application doesn’t recognize data types such as SQL_BLOB or SQL_CLOB. 

Therefore, you may return them as data type which ODBC application recognizes.You can solve this problem by setting LongDataCompat = on in odbc.ini. If you call SQLColAttribute() in LOB column for this option, ODBC returns SQL_LONGVINARYto SQL_BLOB and SQL_LONGVARCHAR to SQL_CLOB relatively

##### Use Examples in PHP Program

The following is an example of using LOB in a PHP application. 

Before running the program, you should check two properties in php.ini:

```
odbc.defaultlrl = 4096 (This value must be specified as greater than 1)
odbc.defaultbinmode = 0 (You must specify this as 0 for using LOB because this can be executed
without allocating additional memory.)
~/.odbc.ini  is as follows.
[Altibase]
Driver = AltibaseODBCDriver
Description = Altibase DSN
ServerType = Altibase
UserName = SYS
Password = MANAGER
Server = 127.0.0.1
Port = 20073
LongDataCompat = on
NLS_USE = US7ASCII
php program
<?
/*
* =================================================
* Connection Trial
* =================================================
*/

$Connection = @odbc_connect("Altibase", "SYS", "MANAGER");
if (!$Connection)
{
echo "ConnectFail!!!\n";
exit;
}

/*
* =================================================
* Table Creation
* =================================================
*/

@odbc_exec($Connection, "DROP TABLE T2 ");
if (!@odbc_exec($Connection, 
"CREATE TABLE T2 (I1 INTEGER, B2 BLOB, C3 CLOB) TABLESPACE SYS_TBS_DATA"))
{
echo "create test table Fail!!!\n";
exit;
}

/*
* =================================================
*  autocommit off for using LOB
* =================================================
*/

odbc_autocommit($Connection, FALSE);

/*
* =================================================
* Data Insertion
* =================================================
*/

$query = "INSERT INTO T2 VALUES (?, ?, ?)";
$Result1 = @odbc_prepare($Connection, $query);
if (!$Result1)
{
$msg = odbc_errormsg($Connection);
echo "prepare insert: $msg\n";
exit;
}

for ($i = 0; $i < 10; $i++)
{

/*
* ----------------------
* Reading in File
* ----------------------
*/

$fileno2 = $i + 1;
$filename2 = "a$fileno2.txt";
print("filename = $filename2\n");
$fp = fopen($filename2, "r");
$blob = fread($fp, 1000000);
fclose($fp);

$fileno3 = 10 - $i;
$filename3 = "a$fileno3.txt";
print("filename = $filename3\n");
$fp = fopen($filename3, "r");
$clob = fread($fp, 1000000);
fclose($fp);

/*
* ----------------------
* INSERT
* ----------------------
*/
	
$Result2 = @odbc_execute($Result1, array($i, $blob, $clob));
	
print("inserting $i ,$filename2 and $filename3 into T2 ......... ");
	
if (!$Result2)
{
print("FAIL\n");
$msg = odbc_errormsg($Connection);
echo "execute insert: $msg \n";
exit;
}

print("OK\n");
}

/*
* =================================================
* COMMIT
* =================================================
*/

odbc_commit($Connection);

/*
* =================================================
* Check inserted data
* =================================================
*/
print "\n\n";
print "==========================================\n";
print "Selecting from table\n";
print "==========================================\n";

$query = "select * from t2";
$Result1 = @odbc_exec($Connection, $query);
if (!$Result1)
{
$msg = odbc_errormsg($Connection);
echo "ERROR select: $msg\n";
exit;
}

$rownumber = 0;
while (odbc_fetch_row($Result1))
{
$data1 = odbc_result($Result1, 1);
$data2 = odbc_result($Result1, 2);
$data3 = odbc_result($Result1, 3);
$len2 = strlen($data2); 
$len3 = strlen($data3); 
	
print "\n==========================================\n";
print "Row $rownumber....\n";
$rownumber++;
print "data1 = ".$data1."\n";
print "-------\n";
print "data2 = \n";
// print $data2; //  Output is omitted because this is binary data.
print "\n";
print "dataLen2 = [$len2]\n";
print "-------\n";
print "data3 = \n";
print $data3;
print "\n";
print "dataLen3 = [$len3]\n";
}

odbc_commit($Connection);

@odbc_close($Connection);
?>
```

### Other Changes

This section describes changes except data types.

#### SQLCloseCursor

Since there is no ODBC state machine in Altibase 4, the Altibase CLI library calls the functions in the following order.

```
SQLHSTMT stmt;
SQLAllocHandle(SQL_HANDLE_STMT, dbc, &stmt);
SQLPrepare(stmt, (SQLCHAR *)”SELECT I1 FROM T1”, SQL_NTS);

SQLExecute(stmt);
SQLFetch(stmt);
SQLExecute(stmt);
```

However, if you execute codes above with the Altibase CLI driver in Altibase 5, function sequence error occurs in SQLExecute(stmt). 

Because stmt performing SQLExecute() first indicates to generate result set. Therefore, ODBC cursor becomes open and state of stmt indicates S5. (Refer to MSDN ODBC specification.). However, error occurs in this state cause of no performing SQLExecute().

If you want to perform SQLExecute() again, call SQLCloseCursor() clearly as follows and then make stmt have S1 or S3 state.

```
SQLExecute(stmt);
SQLFetch(stmt);
SQLCloseCursor(stmt); 

SQLExecute(stmt);
```

#### SQLBindParameter – ColumnSize Argument

ColumnSize of SQLBindParameter() as the 6th parameter in Altibase 5 is different from that of previous one. If you insert 0 into this argument for previous version, no problem. However, if you insert maximum length of data transmitted to server in Altibase 5, its performance has problem because it checks their information whenever executed. 

#### SQLBindParameter – StrLen_or_IndPtr Argument

CLI library in Altibase 4 references data only if they, which StrLen_or_IndPtr argument indicates, have variable length. However, Altibase 5 references the values in the memory StrLen_or_IndPtr argument indicates whenever performing SQLExecute() or SQLExecDirect() because Altibase 5 can implement SQLPutData() and SQLParamData(). 

Therefore, you need special care in perfectly initializing memory the pointer indicates if sending StrLen_or_Ind as the last argument of SQLBindParameter() to not Null pointer but valid pointer variables. 

If SQL_DATA_AT_EXEC is -2 as constant number or SQL_LEN_DATA_AT_EXEC() is less than - 100 without initializing memory completely, CLI library judges user intends to send the argument with SQLPutData(). And CLI library returns SQL_NEED_DATA when you call SQLExecute(). 

If SQLExecDirect() returns the unintended value(SQL_NEED_DATA) cause of no initialized value above, this influences on functions called next. So you need special care that function sequence errors in all functions called next cause to return SQL_ERROR.

#### SQLPutData(), SQLParamData()

The Altibase CLI in Altibase 5 supports SQLPutData() and SQLParamData() provided not in previous version. Refer to MSDN for details about each function. 

The following is the example program with using functions and StrLen_or_IndPtr mentioned above.

```
Table Schema : 
CREATE TABLE T2_CHAR (I1 INTEGER, I2 CHAR(50));

void putdata_test(void)
{
SQLRETURN sRetCode;
SQLHANDLE sStmt;

SQLINTEGER i1;
SQLLEN i1ind;

SQLCHAR *i2[10] =
{
(unsigned char *)"0000000000000.",
(unsigned char *)"1111111111111. test has been done.",
(unsigned char *)"2222222222222. Abra ca dabra",
(unsigned char *)"3333333333333. Short accounts make long friends.",
(unsigned char *)"4444444444444. Whar the hell are you doing man!",
(unsigned char *)"5555555555555. Oops! I missed this row. What an idiot!",
(unsigned char *)"6666666666666. SQLPutData test is well under way.",
(unsigned char *)"7777777777777. The length of this line is well over 50 characters.",
(unsigned char *)"8888888888888. Hehehe",
(unsigned char *)"9999999999999. Can you see this?",
};

SQLLEN i2ind;

SQLINTEGER i;

SQLINTEGER sMarker = 0;

i1ind = SQL_DATA_AT_EXEC;
i2ind = SQL_DATA_AT_EXEC;

sRetCode = SQLAllocHandle(SQL_HANDLE_STMT, gHdbc, &sStmt);
check_error(SQL_HANDLE_DBC, gHdbc, "STMT handle allocation", sRetCode);

sRetCode = SQLBindParameter(sStmt, 1, SQL_PARAM_INPUT, 
SQL_C_SLONG, SQL_INTEGER, 
0, 0, (SQLPOINTER *)1, 0, &i1ind);

sRetCode = SQLBindParameter(sStmt, 2, SQL_PARAM_INPUT, 
SQL_C_CHAR, SQL_CHAR, 
60, 0, (SQLPOINTER *)2, 0, &i2ind);

sRetCode = SQLPrepare(sStmt, 
(SQLCHAR *)"insert into t2_char values (?, ?)", SQL_NTS);

for(i = 0; i < 10; i++)
{
i1 = i + 1000;

printf("\n");
printf(">>>>>>>> row %d : inserting %d, \"%s\"\n", i, i1, i2[i]);
sRetCode = SQLExecute(sStmt);

if(sRetCode == SQL_NEED_DATA)
{
sRetCode = SQLParamData(sStmt, (void **)&sMarker);

while(sRetCode == SQL_NEED_DATA)
{
printf("SQLParamData gave : %d\n", sMarker);

if(sMarker == 1)
{
sRetCode = SQLPutData(sStmt, &i1, 0);
}
else if(sMarker == 2)
{
int unitsize = 20;
int size;
int pos;
int len;

len = strlen((char *)(i2[i]));
for(pos = 0; pos < len;)
{
size = len - pos;
if(unitsize < size)
{
size = unitsize;
}
sRetCode = SQLPutData(sStmt, i2[i] + pos, size);

pos += size;
}
}
else
{
printf("bbbbbbbbbbbbbbbbbbbbbbbbbbbbb!!! unknown marker value\n");
exit(1);
}

sRetCode = SQLParamData(sStmt, (void **)&sMarker);
}
}
}

sRetCode = SQLFreeHandle(SQL_HANDLE_STMT, sStmt);
check_error(SQL_HANDLE_DBC, gHdbc, "STMT free", sRetCode);
}
```

#### Limitation on ALTER SESSION statements

Altibase 4 specifies AUTOCOMMIT MODE and DEFAULT_DATE_FORMAT as session properties as follows

```
SQLExecDirect(stmt, 
“ALTER SESSION SET AUTOCOMMIT=FALSE”, 
SQL_NTS);

SQLExecDirect(stmt,
“ALTER SESSION SET DEFAULT_DATE_FORMAT='YYYY/MM/DD'",
SQL_NTS); 
```

The Altibase CLI driver must have information on two session-related properties above because they definitely affect conversion of Altibase CLI and operation of functions related to transactions. 

However, the Altibase CLI driver cannot know property changes if transmitting SQL syntaxes to server directly with using SQLExecDirect(). The Altibase CLI driver can get information from server to know the values of property, but this causes to have worse performance. 

In Altibase 5 the property is modified with SQLSetConnectAttr() to solve this problem. Altibase 5 always makes the property in the Altibase CLI driver same as that in server. 

You can write as follows when using the Altibase CLI.

```
SQLSetConnectAttr(conn,
SQL_ATTR_AUTOCOMMIT,
(SQLPOINTER)SQL_AUTOCOMMIT_OFF,
0);
SQLSetConnectAttr(conn,
ALTIBASE_DATE_FORMAT,
(SQLPOINTER)"YYYY/MM/DD",
SQL_NTS); 
```

#### SQLRowCount(), SQLMoreResults() functions

There are two results of the Altibase CLI.

-   Number of affected rows

-   Result set

The Altibase CLI considers multiple results in Altibase 5. In other words, you can get them by one execution. Therefore, returned results of SQLRoewCount() are different from those of Altibase 4 when you use array binding.

-   SQLRowCount() : gets affected row count in “current” result.

-   SQLMoreResults() : moves to “next” result and returns SQL_NO_DATA if current result is last.

##### Example

```
CREATE TABLE T1 (I1 INTEGER);
INSERT INTO T1 VALUES(1);
INSERT INTO T1 VALUES(2); ........ repeat 1000 times
SELECT * FROM T1;
T1
----- 
1 
2 
3 
. 
. 
. 
1000 
-----

SQLINTEGER p1[3];
SQLINTEGER p2[3];
SQLLEN rowcount = 0L;
SQLLEN totalRowcount = 0L;

p1[0] = 10; p2[0] = 20;
p1[1] = 100; p2[1] = 200;
p1[2] = 11; p2[2] = 14;

SQLSetStmtAttr(stmt, SQL_ATTR_PARAMSET_SIZE, 3); // <--- array binding

SQLBindParameter(stmt, 1, p1 ..);
SQLBindParameter(stmt, 2, p2 ..);

SQLExecDirect(stmt, 
(SQLCHAR *)"DELETE FROM T1 WHERE I1>? AND I1<?”, 
SQL_NTS);

do {
SQLRowCount(stmt, &rowcount);
printf("%d\n", rowcount);
totalRowcount += rowcount;
rc = SQLMoreResults(stmt);
} while (rc != SQL_NO_DATA);

printf(“totalRowcount = %d\n”, totalRowCount);
Execution Results
9 => This is affected row count of DELETE FROM T1 WHERE I1>10 AND I1<20
199 => This is affected row count of DELETE FROM T1 WHERE I1>100 AND I1<200
0 => This is affected row count of DELETE FROM T1 WHERE I1>11 AND I1<14
 (No record exists because it is deleted by the first execution.)
208 => This is the total of affected row counts
```

Each execution result of syntax the argument indicates is created, and then sent to the Altibase CLI driver. When multiple results are created like this, each data can move for next result with SQLMoreResults() and have its result with SQLRowCount().

In Altibase 4, when all three results are summed together, SQLRowCount () is 208 Return the result. 

If you want to get the same result as Altibase 4 in Altibase 5, SQLMoreResults () The function must be repeated until it returns SQL_NO_DATA and added to the result obtained by SQLRowCount ().

#### Unlimited Array Execute, Array Fetch

Altibase does not have restrictions on Array Execute and Array Fetch as buffer size.

Therefore, you can bind array in the allocated memory and can use CM_BUFF_SIZE no more.

#### Unavailable Properties

##### Batch Processing Mode

The placement keyword of the connection string is no longer supported. 

In addition, the connection attribute SQL_ATTR_BATCH is no longer supported.

##### SQL_ATTR_MAX_ROWS

This indicates to specify the number of prefetched row for better performance in Altibase 4. 

However, this property is similar to LIMIT of SELECT statement following ODBC. This option is not available for the Altibase CLI of Altibase. Therefore, if you specify property above as SQLSetStmtAttr(), this asks your attention because error occurs like ‘Optional feature not implemented’.
