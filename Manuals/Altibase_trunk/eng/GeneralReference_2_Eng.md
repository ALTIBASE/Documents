<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [General Reference](#general-reference)
  - [2. Altibase Properties](#2altibase-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [Session Properties](#%EC%84%B8%EC%85%98-%EA%B4%80%EB%A0%A8-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [Time-out Properties](#%ED%83%80%EC%9E%84%EC%95%84%EC%9B%83-%EA%B4%80%EB%A0%A8-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [Transaction Properties](#%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98-%EA%B4%80%EB%A0%A8-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [Backup and Recovery Properties](#%EB%B0%B1%EC%97%85-%EB%B0%8F-%EB%B3%B5%EA%B5%AC-%EA%B4%80%EB%A0%A8-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [Replication Properties](#%EC%9D%B4%EC%A4%91%ED%99%94-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [Network and Security Properties](#%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC-%EA%B4%80%EB%A0%A8-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [Message Logging Properties](#%EB%A9%94%EC%8B%9C%EC%A7%80-%EB%A1%9C%EA%B7%B8-%EA%B4%80%EB%A0%A8-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [Database Link Properties](#%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4-%EB%A7%81%ED%81%AC-%EA%B4%80%EB%A0%A8-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [Auditing Properties](#%EA%B0%90%EC%82%AC-%EA%B4%80%EB%A0%A8-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [C/C++ External Procedure Agent Properties](#%EC%97%90%EC%9D%B4%EC%A0%84%ED%8A%B8-%EA%B4%80%EB%A0%A8-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [Account Security Properties](#%EC%82%AC%EC%9A%A9%EC%9E%90-%EA%B3%84%EC%A0%95-%EB%B3%B4%EC%95%88-%EA%B4%80%EB%A0%A8-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [Altibase Sharding Properties](#altibase-sharding-%EA%B4%80%EB%A0%A8-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [Other Properties](#%EA%B8%B0%ED%83%80-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Altibase® Administration

# General Reference

![](media/GeneralReference/e5cfb3761673686d093a3b00c062fe7a.png)

Altibase Administration General Reference

Release 7.1

Copyright ⓒ 2001\~2020 Altibase Corp. All Rights Reserved.

This manual contains proprietary information of Altibase Corporation; it is provided under a license agreement containing restrictions on use and disclosure and is also protected by copyright patent and other intellectual property law. Reverse engineering of the software is prohibited. All trademarks, registered or otherwise, are the property of their respective owners.

**Altibase Corp**

10F, Daerung PostTower II, 306, Digital-ro, Guro-gu, Seoul 08378, Korea Telephone: +82-2-2082-1000 Fax: 82-2-2082-1099

Customer Service Portal: http://support.altibase.com/en/

Homepage: [http://www.altibase.com](http://www.altibase.com/)

## 2. Altibase Properties

### Session Properties

Session-related properties define the rules for communication between clients and the database server when Altibase is run in a client-server configuration. They are as follows:

#### CM_DISCONN_DETECT_TIME (Unit: second)

##### Data Type

Unsigned Integer

##### Default Value

3

##### Attributes

Read-Only, Single Value

##### Range

[1, 2<sup>32</sup>-1]

##### Description

Altibase server provides a session management thread for checking whether the connection between a client and a server has been interrupted. This property specifies the interval, in seconds, at which the session management thread operates. 

Usually, when a client process is abnormally terminated, the server to which the client is connected can immediately detect this

However, when a session has an unfinished task, and furthermore if the task is an internal Altibase server operation that is not directly related to the client session, and it is taking a long time, the server cannot check whether the client has terminated abnormally. That is to say, because the server cannot check whether the connection with the client has ended abnormally, such abnormal termination would be disregarded and Altibase would continue to process the task.

Such sessions must be detected, and the corresponding transactions must be rolled back. For this purpose, the session management thread regularly checks the status of all sessions.

#### CONCURRENT_EXEC_DEGREE_DEFAULT

##### Data Type

Unsigned Integer

##### Default Value

4

##### Attributes

Read-Write, Single Value

##### Range

[2, 1024]

##### Description

CONCURRENT_EXEC_DEGREE_DEFAULT specifies for each session, the number of procedures in the DBMS_CONCURRENT_EXEC package that are allowed to execute in parallel concurrently. If the number of procedures to be executed in parallel is omitted, the CONCURRENT_EXEC_DEGREE_DEFAULT value is applied. 

Altibase does not allow a stored package to execute more procedures than the value set for the CONCURRENT_EXEC_DEGREE_MAX property.

The value of this property can be changed with the ALTER SYSTEM statement while Altibase is running. 

#### CONCURRENT_EXEC_DEGREE_MAX

##### Data Type

Unsigned Integer

##### Default Value

The number of CPUs

##### Attributes

Read-Only, Single Value

##### Range

[0, 1024]

##### Description

CONCURRENT_EXEC_DEGREE_MAX specifies the maximum number of procedures in the DBMS_CONCURRENT_EXEC package that are allowed to execute in parallel

If this value is set to 0, the DBMS_CONCURRENT_EXEC package cannot be executed.

The value of this property can be changed with the ALTER SYSTEM statement while Altibase is running. 

#### CONCURRENT_EXEC_WAIT_INTERVAL

##### Data Type

Unsigned Integer

##### Default Value

100

##### Attributes

Read-Write, Single Value

##### Range

[10, 1000000]

##### Description

CONCURRENT_EXEC_WAIT_INTERVAL specifies the interval to wait before checking whether a procedure in the DBMS_CONCURRENT_EXEC package has executed successfully.

The value of this property affects the REQUEST and WAIT_REQ functions. These functions wait for the procedure to finish execution. 

The value of this property can be changed with the ALTER SYSTEM statement while Altibase is running. 

#### DEFAULT_THREAD_STACK_SIZE (Unit: byte)

##### Data Type

Unsigned Integer

##### Default

10485760 (10MB)

##### Attributes

Read-Only, Single Value

##### Range

[1048576, 134217728]

##### Description

This property specifies the stack size, in bytes, for all system threads other than service threads. 

#### IPC_CHANNEL_COUNT

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Only, Single Value

##### Range

[0, 65535]

##### Description

This property, which specifies the maximum number of IPC communication channels between a client and an Altibase server, must be set. Because shared memory and semaphore(s) are allocated in proportion to the channel count, it is important to set the maximum number of IPC connections that can be simultaneously established with the server.

#### IPC_FILEPATH

##### Data Type

String

##### Default Value

\$ALTIBASE_HOME/trc/cm-ipc

##### Attributes

Read-Only, Single Value

##### Range

None

##### Description

This is a socket file created for Altibase server to connect with the client through IPC in the UNIX environment. 

If the server starts, a socket file is created under $ALTIBASE_HOME/trc/cm-ipc directory, and be careful not to delete this file. 

#### IPCDA_CHANNEL_COUNT

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Only, Single Value

##### Range

[0, 65535]

##### Description

The maximum number of communication channels using IPCDA between the client and server is specified with this property. 

This property specifies the maximum number of IPCDA which can concurrently connect to the server plays an important role since shared memory and semaphores are proportionally allocated to the number of IPCDA channels. The optimized number of IPCDA channels should be half value of the number of CPU cores.

#### IPCDA_DATABLOCK_SIZE (Unit: KB)

##### Data Type

Unsigned Integer

##### Default Value

20480

##### Attributes

Read-Only, Single Value

##### Range

[32, 102400]

##### Description

This is a property specifying the size of shared memory in a communication channel using IPCDA. If the value is 1000, and IPCDA_CHANNEL_COUNT is 24, the entire memory size (IPCDA_CHANNEL_COUNT * IPCDA_DATABLOCK_SIZE) used for the communication channel in server is 1000KB * 24 = 24000KB. 

The value should be properly specified in order not to interrupt the operation of other programs using shared memory depending on the system size. For example, If IPCDA_CHANNEL_COUNT is 24 in 4GB system memory, the maximum value of IPCDA_DATABLOCK_SIZE cannot be used because the actual memory to use is 2457600KB. 

#### IPCDA_FILEPATH

##### Data Type

String

##### DEfault Value

\$ALTIBASE_HOME/trc/cm-ipcda

##### Attributes

Read-Only, Multiple Value

##### Range

None

##### Description

This is a socket file created for Altibase server to connect with the client through IPCDA in the UNIX environment. 

If the server starts, a socket file is created under $ALTIBASE_HOME/trc/cm-ipcda directory, and be careful not to delete this file. 

#### MAX_LISTEN

##### Data Type

Unsigned Integer

##### Default Value

128

##### Attributes

Read-Only, Single Value

##### Range

[0, 16384]

##### Description

This property specifies the maximum size of the “listen queue” when TCP/IP or UNIX domain protocol is used for communication between a client and Altibase.

#### MAX_STATEMENTS_PER_SESSION

##### Data Type

Unsigned Integer

##### Default

1024

##### Attributes

Read-Write, Single Value

##### Range

[1, 65535]

##### Description

This property specifies the maximum number of statements that can be executed in a session. 

This property value can be modified with the ALTER SESSION or ALTER SYSTEM statement while Altibase is running.

#### NET_CONN_IP_STACK

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Only, Single Value

##### Range

[0, 1, 2]

##### Description

This property specifies the Internet Protocol Stack to be used when creating sockets on the
server side for communication between the client and the server via TCP/IP.

0: An Internet Protocol Stack supporting only IPv4 will be used.

1: A dual stack (Internet Protocol Stack supporting both IPv4 and IPv6) will be used.

2: An Internet Protocol Stack supporting only IPv6 will be used.

#### NLS_COMP

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Only, Single Value

##### Range

[0, 1]

##### Description

When a database is created, it cannot be guaranteed that the sequence of characters in the character set specified by NLS_USE is the same as in a dictionary for the language of the country in question.

If this property is set to 1, character comparisons are performed based on the order in which the words in that language appear in a dictionary. If this property is set to 0, character comparisons are performed based on the binary values of the characters.

This is supported only when the database character set is set to Korean (KSC-5601 complete and MS extended complete) because the system currently supports Korean only.

#### NLS_CURRENCY

##### Data Type

String

##### Default Value

Determined by the value of NLS_TERRITORY

##### Attributes

Read-Write, Single Value

##### Range

Character string, maximum10 bytes 

##### Description

This property specifies the currency symbol. The value for this property is used to display the local currency symbol with the L number format. This property value cannot begin with +, -, <, > signs.

While Altibase is running, this property value can be modified with the ALTER SESSION statement as below:

```
ALTER SESSION SET NLS_CURRENCY = '$';
```

> Note: In order to display the Arabic currency symbol properly, the client application program(or shell/editor) must support the display of Arabic characters.

#### NLS_ISO_CURRENCY

##### Data Type

String

##### Default Value

Determined by the value of NLS_TERRITORY.

##### Attributes

Read-Write, Single Value

##### Range

Value that exists in the V$NLS_TERRITORY performance view. 

##### Description

This property specifies the ISO currency symbol. The value of this property is used with the C number format to display the international currency symbol. The value of this property is limited to the value(territory) that exists in the V$NLS_TERRITORY performance view.

While Altibase is running, this property value can be modified with the ALTER SESSION statement as below:

```
ALTER SESSION SET NLS_ISO_CURRENCY = America;
```

#### NLS_NCHAR_CONV_EXCP

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Write, Single Value

##### Range

[0, 1]

##### Description

When NCHAR type data are converted to another character set, data loss can occur. In such cases, this property determines whether to raise an error or to continue converting the data despite the possibility of data loss.

This property raises an error only when data conversion is performed on the server; it doesn’t apply to conversion performed on clients. 

This property can be changed using the ALTER SESSION statement while Altibase is running.

0: FALSE (Do not raise an error.)

1: TRUE

#### NLS_NCHAR_LITERAL_REPLACE

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Write, Single Value

##### Range

[0, 1]

##### Description

By default, clients convert an entire query string to the database character set before sending the data to the database. This behavior can be prevented for a given string literal by setting this property to 1 and placing the "N" character in front of the string literal.

A property setting of 1 instructs the client to search for the "N" character in front of every string literal. If the "N" character is found, the client sends the string to the database without converting it to the database character set. This is useful when it is desired to use NCHAR type data that are encoded differently from the database character set.

This property can be changed using the ALTER SESSION statement while Altibase is running.

0: convert all strings to the database character set without checking for the "N" character

1: do not convert strings that are preceded by the "N" character to the database character set

> Note: Setting this property to 1 can be expensive in terms of usage of client resources.

#### NLS_NUMERIC_CHARACTERS

##### Data Type

String

##### Default Value

Determined by the value of NLS_TERRITORY.

##### Attributes

Read-Write, Single Value

##### Range	

None

##### Description

This property specifies the decimal character and the group separator. The group separator is used to display numbers in thousands and generally uses a comma(,). The decimal character generally uses a period(.).This property value cannot begin with +, -, <, > signs.

Of a character string specified for this property, only the first two characters are set as decimal characters; the group separator and the rest are ignored. 

While Altibase is running, this property value can be modified with the ALTER SESSION statement as below:

```
ALTER SESSION SET NLS_NUMERIC_CHARACTERS='.,';
```

#### NLS_TERRITORY

##### Data Type

String

##### Default Value

KOREA

##### Attributes

Read-Write, Single Value

##### Range

Value that exists in the V$NLS_TERRITORY performance view

##### Description

This property specifies the name of the territory. Values of the NLS_NUMERIC_CHARACTER, NLS_CURRENCY, NLS_ISO_CURRENCY properties are automatically modified according to the territory set for this property. Territory names available for specification of this property can be checked by querying the V$NLS_TERRITORY performance view. 

While Altibase is running, this property value can be modified with the ALTER SESSION statement as below. Territory names do not distinguish upper or lower class, and apostrophes(‘) can be used. 

```
ALTER SESSION SET NLS_TERRITORY = America;
or
ALTER SESSION SET NLS_TERRITORY = 'America';
```

#### PORT_NO

##### Data Type

Unsigned Integer

##### Default Value

20300

##### Attributes

읽기 전용, 단일 값

##### Range

[1024, 65535]

##### Description

This property specifies the port number for communication between the client and the server via TCP/IP. The user can set this port number to any number not being used by another application within the range of port numbers (up to number 65535) excluding the so-called “well-known TCP port numbers” (from 1 to 1023). Application programs of Altibase can connect to the server via this port number

#### PSM_CURSOR_OPEN_LIMIT

##### Data Type

Unsigned Integer

##### Default Value

32

##### Attributes

Read-Only, Single Value

##### Range

[1,1024]

##### Description

The PMS_CURSOR_OPEN_LIMIT specifies the cursor which can be open by using DBMS_SQL in the session.

#### PSM_FILE_OPEN_LIMIT

##### Data Type

Unsigned Integer

##### Default Value

16

##### Attributes

Read-Write, Single Value

##### Range

[0,128]

##### Description

This property specifies the maximum number of stored procedure file handles that can be opened for a session.

#### TIME_ZONE

##### Data Type

String

##### Default Value

OS_TZ

##### Attributes

Read-Write, Single Value

##### Range

The vlue that exists in the V\$TIME_ZONE_NAMES performance view.

##### Description

This property sets the time zone. Region names, abbreviations or character strings such as the UTC offset value(e.g., +09:00) can be used for specification.

This property can be modified using the ALTER SESSION statement while Altibase is running.

#### UNIXDOMAIN_FILEPATH

##### Data Type

String

##### Default Value

\$ALTIBASE_HOME/trc/cm-unix

##### Attributes

Read-Only, Single Value

##### Range

None

##### Description

This property is a socket file created for Altibase server to connect with a client through the Unix domain. 

If the server is driven, the basic socket file is created under $ALTIBASE_HOME/trc directory, and it should be ensured that the file is not deleted.

#### USE_MEMORY_POOL

##### Data Type

Unsigned Integer

##### Default Value

1

##### Attributes

Read-Only, Single Value

##### Range

[0,1]

##### Description

This property specifies whether memory pooling is used. “Memory pooling” means assigning server memory in advance.

When this function is used, because server memory is allocated in advance, memory use is increased.

0: Do not use memory pooling 

1: Use memory pooling

#### USER_LOCK_POOL_INIT_SIZE (Unit: count)

##### Data Type

Unsigned Integer

##### Default Value

128

##### Attributes

Read-Only, Single Value

##### Range

[128, 10000]

##### Description

The number of times for user lock in the database can be specified through the USER_LOCK_POOL_INIT_SIZE property. 

By exceeding the property values, the user lock can be used for maximum number of times; however, in that case, performance degradation might be occurred due to overutilization. Moreover, once the user lock is created the user lock cannot be eliminated even though it is released; thus, it can be said that re-using the user unlock that has been once released is rather efficient.

#### USER_LOCK_REQUEST_CHECK_INTERVAL (Unit: microsecond)

##### Data Type

Unsigned Integer

##### Default Value

10000

##### Attributes

Read-Write, Single Value

##### Range

[10, 999999]

##### Description

The USER_LOCK_REQUEST_CHECK_INTERVAL configures a cycle for examining whether the user lock is available for use or not. If a user, who is currently using in a different session, requests the user lock, the session would be waiting until the user lock is released.

The property value can be modified by using the ALTER SYSTEM statement during the operation of Altibase.

#### USER_LOCK_REQUEST_LIMIT (Unit: count)

##### Data Type

Unsigned Integer

##### Default Value

10

##### Attributes

Read-Write, Single Value

##### Attributes

[0, 10000]

##### Default Value

The USER_LOCK_REQUEST_LIMIT sets number of times the user lock that one session can request. The value of this property can be modified through the ALTER SYSTEM statement during the operation of Altibase..

#### USER_LOCK_REQUEST_TIMEOUT (Unit: second)

##### Data Type

Unsigned Integer

##### Default value

10

##### Attributes

Read-Write, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

The USER_LOCK_REQUEST_TIMEOUT establishes the maximum waiting time until the user lock is obtained in a session.

The value of this property can be modified through the ALTER SYSTEM statement during the operation of Altibase.

#### XA_HEURISTIC_COMPLETE

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Only, Single Value

##### Range

[0, 2]

##### Description

In a distributed transaction environment, Two-Phase Commit Protocol (XA) is used. While a transaction is underway, after a Prepare command has been received from the global transaction coordinator, if for some reason a COMMIT or ROLLBACK command does not arrive for a long time, Altibase will keep the transaction active for a long time, which will negatively affect database performance.

To prevent this, Altibase terminates the entire transaction if it has been in a PREPARE (or IN_DOUBT) state beyond a certain period of time. In such cases, this property determines whether to use COMMIT or ROLLBACK to terminate the transaction.

Altibase waits for the amount of time specified with the XA_INDOUBT_TX_TIMEOUT property before cancelling a transaction in this way. If the value of XA_HEURISTIC_COMPLETE is 0, which is the default, nothing will be done; if it is 1, the transaction will be committed, and if it is 2, the transaction will be rolled back. 

### Time-out Properties

#### BLOCK_ALL_TX_TIME_OUT (Unit: second)

##### Data Type

Unsigned Integer

##### Default Value

3

##### Attributes

Read-Write, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This property restricts transactions’ access to the hash table when the buffer manager resizes the hash table. The minimum value of 0 specifies that error handling is to be performed without any wait time. 

This property can be changed using the ALTER SYSTEM statement while Altibase is running.

#### DDL_LOCK_TIMEOUT (Unit: second)

##### Data Type

Short integer

##### Default Value

0

##### Attributes

Read-Write, Single Value

##### Range

[-1, 65535]

##### Description

When DDL query statements are executed, this property sets how long to wait to establish a lock when the target table has already been locked by another transaction. In cases where a transaction cannot immediately gain write access to the table, If this parameter is set to -1, the transaction will wait indefinitely, whereas if this parameter is set to a positive value, the transaction will wait for that number of seconds before trying again.

The default value of this parameter is 0, which tells Altibase to return an error code if it cannot obtain a lock immediately at the time of executing a DDL statement. 

This property can be changed using the ALTER SYSTEM statement while Altibase is running.

#### DDL_TIMEOUT (Unit: second)

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Write, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

If the execution time of a DDL statement exceeds the number of seconds specified here, execution of that statement is canceled. The default value of this property is 0, in which case Altibase waits indefinitely for DDL operations to finish. 

This property can be changed using the ALTER SYSTEM or ALTER SESSION statement while Altibase is running.

> Note: In Altibase versions up to 5.5.1, the execution time of DDL statements was governed by the UTRANS_TIMEOUT and QUERY_TIMEOUT properties, which still govern the execution time of DML and DCL statements

#### FETCH_TIMEOUT (Unit: second)

##### Data Type

Unsigned Integer

##### Default Value

60

##### Attributes

Read-Write, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This property prevents abnormal increases in database memory consumption when SELECT statements executed by client applications take an excessive amount of time. In cases where the query execution time exceeds the number of seconds specified using this property, the session will be disconnected and the transaction will be rolled back. 

This property can be changed using the ALTER SYSTEM or ALTER SESSION statement while Altibase is running.

#### IDLE_TIMEOUT (Unit: second)

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Write, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

If a large number of clients are connected to a server for an excessive period of time due to some abnormality, the number of available connections will significantly decrease, ultimately leading to failure to provide service.

This property functions to preemptively prevent this situation. If the number of seconds that a session is idle exceeds this value, the session will be disconnected and any associated transactions will be rolled back. 

The value of this property can be changed using the ALTER SYSTEM or ALTER SESSION statement while Altibase is running.

#### LOGIN_TIMEOUT (Unit: second)

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Write, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This property specifies the permitted amount of time, in seconds, to wait for authorization to be completed after a connection has been made to an Altibase port. If authorization is not completed within this time, the server disconnects.

#### MULTIPLEXING_POLL_TIMEOUT (Unit: microsecond)

##### Data Type

Unsigned Integer

##### Default Value

10000

##### Attributes

Read-Write, Single Value

##### Range

[1000, 1000000]

##### Description

This property specifies the interval at which the multiplexed thread running service detects sessions.

#### QUERY_TIMEOUT (Unit: second)

##### Data Type

Unsigned Integer

##### Default Value

600

##### Attributes

Read-Write, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This property is set to prevent abnormal increases in database memory consumption when particular kinds of queries (especially those involving sort operations or joins) are executed. If the query execution time exceeds the number of seconds specified here, the transaction is partially rolled back. 

This property can be changed using the ALTER SYSTEM or ALTER SESSION statement while Altibase is running.

#### SHUTDOWN_IMMEDIATE_TIMEOUT

##### Data Type

Unsigned Integer

##### Default Value

60

##### Attributes

Read-Write, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

When shutting down Altibase with the IMMEDIATE option, Altibase is shut down after uncommitted transactions are rolled back. This property specifies the amount of time, in seconds, to wait for the transactions to be rolled back. If the elapsed time exceeds the specified value, Altibase is shut down forcibly and uncommitted transactions are not rolled back. If this property is set to 0, Altibase waits until all transactions are rolled back. 

This property can be changed using the ALTER SYSTEM statement while Altibase is running.

#### UTRANS_TIMEOUT (Unit: second)

##### Data Type

Unsigned Integer

##### Default value

3600

##### Attributes

Read-Write, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This property is set to prevent the number of log files from abnormally increasing when write operations (UPDATE, DELETE, INSERT) take a long time. If such a transaction takes longer than the number of seconds specified here, the session will be disconnected and the transaction in question will be rolled back. 

This property can be changed using the ALTER SYSTEM or ALTER SESSION statement while Altibase is running.

#### XA_INDOUBT_TX_TIMEOUT (Unit: second)

##### Data Type

Unsigned Integer

##### Default Value

60

##### Attributes

Read-Only, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

When using the Two-Phase Commit Protocol, this property specifies the number of seconds to wait before terminating an entire transaction that has taken a long time and is thus in IN_DOUBT state.

### Tranaction Properties

#### AUTO_COMMIT

##### Data Type

Unsigned Integer

##### Default Value

1

##### Attributes

Read-Write, Single Value

##### Range

[0, 1]

##### Description

This property determines whether to handle each individual SQL statement as a separate transaction and commit it when SQL statements are executed in a session. A value of 1 indicates auto-commit mode, while a value of 0 indicates non-autocommit mode. When using non-autocommit mode, the client application must explicitly indicate the beginning and end of a transaction. 

Even if this value is set to 1, indicating auto-commit, when the server is started, this property can be changed for individual sessions. For example, if ALTER SESSION SET AUTOCOMMIT = FALSE (non-autocommit) is executed from a client, the user must explicitly specify whether to commit or rollback any transactions that occur for the remainder of the session. 

This property can be changed using the ALTER SYSTEM statement while Altibase is running.

#### ISOLATION_LEVEL

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Only, Single Value

##### Range

[0, 3]

##### Description 

This property specifies the transaction isolation level. When a single transaction searches the same table multiple times, the result varies depending on the isolation level. 

For more information about transaction isolation levels, please refer to the *Altibase Administrator’s Manual*.

| Isolation Level     | Characteristics                                              |
| ------------------- | ------------------------------------------------------------ |
| 0 (Committed Read)  | This is the default mode of Altibase. This isolation level guarantees that previously read data that have been modified by another transaction will reflect the changes of that other transaction. When a SELECT transaction reads data one time and then reads the data again, if another transaction simultaneously executes and commits an INSERT or DELETE statement, due to this change, it is possible for a new row to be found, or for a previously found row to have disappeared. |
| 1 (Repeatable Read) | This isolation level guarantees that the contents of a row will be the same upon repeated reads by the same transaction.This isolation level places a lock on a row once it has been read. Therefore, when the table is subsequently read, previously read rows will not change or disappear, but it is possible for new rows to appear. |
| 2 (No Phantom)      | This isolation level guarantees identical results for repeated reads. |

#### TRANSACTION_TABLE_SIZE (Unit: Transaction count)

##### Data Type

Unsigned Integer

##### Default Value

1024

##### Attributes

Read-Only, Single Value

##### Range

[16,16384]

##### Description

The number of transactions which can be simultaneously created during the Altibase service is specifiable when creating a database, and memory for such process is allocated in advance. 

This property should increase or decrease the value by 2n and the database must be created again when decreasing the value.

#### SHARED_TRANS_HASH_BUCKET_COUNT(단위 : 해시 저장소 개수)

##### Data Type

Unsigned Integer

##### Default value

1024

##### Attributes

Read-Only, Single value

##### Range

[16,16384]

##### Description

Sets the hash storage size of the data structure for managing shared transactions created during the Altibase sharding.

### Backup and Recovery Properties

These properties are related to the management of change logs, which are maintained in response to database changes.

#### ARCHIVE_DIR

##### Data Type

String

##### Default Value

\$ALTIBASE_HOME/arch_logs

##### Attributes

Read-Only, Multiple Values

##### Range

None

##### Description

This property specifies the directory or directories in which to store archive log files when performing an archive log backup. If this value is not expressly specified by the user, the default location is $ALTIBASE_HOME/arch_logs. 

The number of directories specified in this property must be the same as the number specified in the LOG_DIR property. 

The user can explicitly specify the value(s), but the specified directories must be created first. If not, an error message will be output, and Altibase will not start.

#### ARCHIVE_FULL_ACTION

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Only, Single Value

##### Range

[0, 1]

##### Description

This property controls the action of the archivelog thread, which conducts archive log backup, when there is not enough disk space in the archive log destination (specified using ARCHIVE_DIR).

If this parameter is set to 0, the archivelog thread will output an error message and stop the archive log file backup. Even if enough disk space can subsequently be secured, archive log backup will not resume until the user explicitly issues a command to do so. If checkpointing takes place in such cases, unnecessary log files will be deleted, even if no archive log file backup has been conducted. Therefore care must be taken when using this mode

If this parameter is set to 1, the archivelog thread waits until enough disk space can be secured to perform the archive log file backup. Because the archive log files have not been backed up, care must be taken to prevent the log files from being deleted if checkpointing takes place during this waiting period.

#### ARCHIVE_MULTIPLEX_COUNT

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Only, Single Value

##### Range

[0, 10]

##### Description 

This property specifies how many copies of the archive log file<sup>9</sup> are to be kept by the Altibase server. After this property has been specified, copies of newly archived log files are kept.

[<sup>9</sup>] Multiplexing archive log files

This feature copies the archive log files to a separate disk to prepare for the event of damage to the original archive log files.

The ARCHIVE_MULTIPLEX_COUNT and ARCHIVE_MULTIPLEX_DIR properties can be specified while the server is shutdown.

#### ARCHIVE_MULTIPLEX_DIR

##### Data Type

String

##### Default Value

""

##### Attributes

Read-Only, Multiple Value

##### Range

None

##### Description

This property specifies the path for copies of the archive log file. The number of values specified in the ARCHIVE_MULTIPLEX_DIR properties must be equal to the value specified in the ARCHIVE_MULTIPLEX_COUNT property. It is recommended to set each path to a separate disk.

#### ARCHIVE_THREAD_AUTOSTART

##### Data Type

Unsigned Integer

##### Default Value

1

##### Attributes

Read-Only, Single Value

##### Range

[0, 1]

##### Description

This property specifies whether to activate the archivelog thread, which periodically performs archive log file backups. If this property is 1, the archivelog thread is activated.

After the archivelog thread has been suspended due to insufficient disk space in the backup directory, this property is used to restart the thread automatically after sufficient disk space is secured.

#### CHECKPOINT_ENABLED

##### Data Type

Unsigned Integer

##### Default Value

1

##### Attributes

Read-Only, Single Value

##### Range

[0, 1]

##### Description

This property specifies whether checkpointing is enabled (“ON”) or disabled (“OFF”).

0: OFF

1: ON

When this value is 0 (“OFF”), the checkpoint thread cannot be started, and additionally it cannot operate the checkpoint interval specified by CHECKPOINT_INTERVAL_IN_SEC and CHECKPOINT_INTERVAL_IN_LOG. However, the user can perform checkpointing manually.

#### CHECKPOINT_INTERVAL_IN_LOG

##### Data Type

Unsigned Integer

##### Default Value

100

##### Attributes

Read-Write, Single Value

##### Range

[1, 2<sup>32</sup>-1]

##### Description

This property defines the checkpoint interval based on the log file creation count. In other words, after the log files have been replaced the number of times specified using this property, checkpointing will be automatically executed. When checkpointing is requested based on this property, it may be impossible to execute, either because checkpointing is already underway, or for some other reason.

In such cases, checkpointing is not initiated immediately again after the checkpointing that is already underway has finished; instead, the current checkpointing request is canceled. Therefore, the next checkpointing request will occur when the number of log files reaches the value set in this property. 

This property can be changed using the ALTER SYSTEM statement while Altibase is running.

#### CHECKPOINT_INTERVAL_IN_SEC (Unit: second)

##### Data Type

Unsigned Integer

##### Default Value

6000

##### Attributes

Read-Write, Single Value

##### Range

[3, 2592000]

##### Description

This property specifies the checkpoint interval in seconds. 

This property can be changed using the ALTER SYSTEM statement while Altibase is running.

#### COMMIT_WRITE_WAIT_MODE 

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Write, Single Value

##### Range

[0, 1]

##### Description

This property specifies whether to wait until logs have been written to log files when committing transactions. In Altibase, the default is not to wait, in the interests of better performance.

This property can be set for the entire system or for individual user sessions, and thus this property can be changed using either the ALTER SYSTEM or ALTER SESSION statement while Altibase is running.

0: Do Not Wait

1: Wait

#### INCREMENTAL_BACKUP_CHUNK_SIZE

##### Data Type

Unsigned Integer

##### Default Value

4

##### Attributes

Read-Only, Multiple Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This property is specified to track the changes made to pages of data(unit: pages). For example, if the value of this property is set to 4, change tracking information is recorded for every 4 pages and all of the 4 pages are backed up if one of the 4 pages is changed.

To alter the value of this property, the changeTracking file must be recreated in the following steps:

1. Shut down the server and then alter the value in the properties file.
2. Start up the server.
3. Disable change tracking and then reactivate it.

#### INCREMENTAL_BACKUP_INFO_RETENTION_PERIOD

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Only, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This property specifies the period of time(unit: days) during which backup information stored in the backupInfo file is retained

Backup information deleted with the ALTER DATABASE DELETE OBSOLETE BACKUP FILES statement ranges from the oldest expired level 0 backup to the level 1 backup immediately prior to the oldest unexpired level 0 backup.

> Note: Backup files backed up at level 0 are a prerequisite for incremental backups. Regardless of the existence of backup information which has expired the maintenance period specified for this property and the corresponding backup files, if only a level 0 backup has been performed, expired backup information and backup files are not deleted, even if the “ALTER DATABASE DELETE OBSOLETE ...” statement is executed.

#### LOG_BUFFER_TYPE 

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Only, Single Value

##### Range

[0, 1]

##### Description

This property determines the log buffer type. If it is set to 0, the OS kernel log buffer is used. If it is set to 1, the process memory log buffer is used.

This property cannot be changed while the system is running

#### LOG_MULTIPLEX_COUNT

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Only, Single Value

##### Range

[0, 10]

##### Description

This property specifies how many copies of the log file<sup>10</sup> are to be kept by the Altibase server. Whenever original log files are created or dropped, the copies of log files are also simultaneously created or dropped. 

[<sup>10</sup>] Multiplexing Log Files

This feature copies the log files to which all changes of the database have been written, to a separate disk to prepare for the event of damage to the original log files.

The LOG_MULTIPLEX_COUNT and LOG_MULTIPLEX_DIR properties can be specified while the server is shutdown.

#### LOG_MULTIPLEX_DIR

##### Data Type

String

##### Default Value

""

##### Attributes

Read-Only, Single Value

##### Range

None

##### Description

This property specifies the path for copies of the log file. The number of values specified in the LOG_MULTIPLEX_DIR properties must be equal to the value of the LOG_MULTIPLEX_COUNT property. It is recommended to set each path to a separate disk

#### PREPARE_LOG_FILE_COUNT

##### Data Type

Unsigned Integer

##### Default Value

5

##### Attributes

Read-Only, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

If there is not enough space in the log file when logs are written, a new log file is created, which can increase the transaction response time. To prevent such delays in transaction execution caused by the creation of log files, Altibase creates extra log files (“prepare log files”) in advance. This parameter specifies the number of such log files.

**SNAPSHOT_MEM_THRESHOLD (Unit: percentage)**

##### Data Type

Unsigned Integer

##### Default Value

80

##### Attributes

Read-Write, Single Value

##### Range

[0, 100]

##### Description

This is a property which sets up available thresholds for use in memory database after the snapshot settings (BEGIN SNAPSHOT). 

The percentage of the MEM_MAX_DB_SIZE property which is currently being used by memory is verified, and if it exceeds the specified threshold, the snapshot is automatically stopped.

**SNAPSHOT_DISK_UNDO_THRESHOLD (Unit: percentage)**

##### Data Type

Unsigned Integer

##### Default Value

80

##### Attributes

Read-Write, Single Value

##### Range

[0, 100]

##### Description

This property specifies thresholds usable in disk after the snapshot settings (BEGING SNAPSHOT).

It verifies what percentage of the SYS_UNDO_FILE_MAX_SIZE property has been used by the disk undo tablespace up to now, and if it exceeds specified threshold, the snapshot is automatically stopped.

### Replication Properties

The following parameters pertain to database replication. For more information about database replication, please refer to the *Getting Started Guide* and to the R*eplication User's Manual.*

#### REPLICATION_ACK_XLOG_COUNT

##### Data Type

Unsigned Integer

##### Default Value

100

##### Attributes

Read-Write, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This property indicates the frequency with which the Receiver thread sends ACK to the Sender thread.

The Receiver thread receives XLogs and replays them one by one. When the number of replayed XLogs exceeds the value specified here, the Receiver thread sends ACK to the Sender thread.

If this value is set too low, the Receiver thread sends ACK too often, leading to reduced performance.

If it is set too high, the amount of time that the Sender thread waits for ACK can increase excessively, and may be treated as a network fault. In addition, if the Sender thread does not receive ACK for an extended time, the replication restart SN is not updated, and thus the Sender thread will start over from the most recent log record if checkpointing occurs, resulting in the deletion of unreplicated logs.

#### REPLICATION_ALLOW_DUPLICATE_HOSTS 

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Write, Single Value

##### Range

[0, 1]

##### Description

This property specifies whether or not to allow replication objects to set duplicate values for the IP address and port number of the remote server

0: Disallowed

1: Allowed

#### REPLICATION_BEFORE_IMAGE_LOG_ENABLE

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Write, Single Value

##### Range

[0, 1]

##### Description

If the "before image" of the replication Receiver differs from the "before image" of the XLog received from the Sender, it is possible for data conflict to occur.

With this property, the "before image" of the replication receiver can be stored in the trace log to enable the user to check which data conflicted. 

0: Disables trace logging

1: Enables trace logging

This property can be changed using the ALTER SYSTEM statement while Altibase is running.

#### REPLICATION_COMMIT_WRITE_WAIT_MODE

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Write, Single Value

##### Range

[0, 1]

##### Description

This property determines whether the replication Receiver checks whether XLOGs have been applied to disk after the replication Receiver has completed executing all of the transactions that are necessary in order to apply the contents of XLOGs to disk. If this property is set to 0, the replication Receiver doesn't wait to ensure that the contents of XLOGs have been applied to disk. If the value of this property is set to 1, the replication Receiver ensures that the contents of XLOGs have been applied to disk.

#### REPLICATION_CONNECT_RECEIVE_TIMEOUT (Unit: second)

##### Data Type

Unsigned Integer

##### Default Value

60

##### Attributes

Read-Write, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This property specifies the amount of time, in seconds, to wait after attempting to connect to the target host at the start of replication.

This property can be changed using the ALTER SYSTEM statement while Altibase is running.

#### REPLICATION_CONNECT_TIMEOUT (Unit: second)

##### Data Type

Unsigned Integer

##### Default Value

10

##### Attributes

Read-Write, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

When attempting to connect to a target host to perform replication, if there is no response within the number of seconds specified in this property, no further connection attempts are made. 

This property can be changed using the ALTER SYSTEM statement while Altibase is running.

#### REPLICATION_DDL_ENABLE 

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Write, Single Value

##### Range

[0, 1]

##### Description

This property specifies whether to allow DDL statements to be executed on replication target tables. If this property is set to 1, DDL statements can be executed on replication target tables.

Before executing DDL statements, if the replication property of a transaction in the current session is set to a value other than NONE, the Sender thread can be made aware of the execution of DDL statements.

For a list of DDL statements permitted during replication and other restrictions, please refer to the *Replication Manual*.

This property can be changed using the ALTER SYSTEM statement while Altibase is running.

#### REPLICATION_DDL_ENABLE_LEVEL

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Write, Single Value

##### Range

[0, 1]

##### Description

This property determines the range of DDL statements that can be used for the replication target table. To use this property, the value of the REPLICATION_DDL_ENABLE has to be set to 1. The following DDL statement is allowed according to the REPLICATION_DDL_ENABLE_LEVEL value.

- REPLICATION_DDL_ENABLE_LEVEL = 0

ALTER TABLE table_name ADD COLUMN ( column_name DATA_TYPE );

ALTER TABLE table_name DROP COLUMN column_name;

ALTER TABLE table_name ALTER COLUMN column_name SET DEFAULT

ALTER TABLE table_name ALTER COLUMN column_name DROP DEFAULT

ALTER TABLE table_name TRUNCATE PARTITION

TRUNCATE TABLE table_name;

CREATE INDEX index_name ON table_name ( column_name );

DROP INDEX index_name; -- for Normal Index

- REPLICATION_DDL_ENABLE_LEVEL = 1

ALTER TABLE table_name ADD COLUMN ( column_name DATA_TYPE NOT NULL );

ALTER TABLE table_name ADD COLUMN ( column_name DATA_TYPE UNIQUE );

ALTER TABLE table_name ALTER COLUMN ( column_name NOT NULL );

ALTER TABLE table_name ALTER COLUMN ( column_name NULL );

ALTER TABLE table_name MODIFY COLUMN ( column_name DATA_TYPE );

ALTER TABLE table_name MODIFY COLUMN ( column_name NULL );

ALTER TABLE table_name MODIFY COLUMN ( column_name NOT NULL );

ALTER TABLE table_name DROP COLUMN column_name; ( NOT NULL, NULL, Unique,
function-base index can also be deleted. )

ALTER TABLE table_name ADD CONSTRAINT constraint_name UNIQUE ( column_name );

ALTER TABLE table_name ADD CONSTRAINT constraint_name UNIQUE ( column_name )
LOCAL;

ALTER TABLE table_name DROP CONSTRAINT constraint_name; ( Unique, Local Unique )

CREATE UNIQUE INDEX index_name ON table_name ( column_name );

CREATE INDEX index_name ON table_name ( expression );

DROP INDEX index_name; ( unique, function-base indexes can be deleted. )

#### REPLICATION_DDL_SYNC

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Write, Single Value

##### Range

[0, 1]

##### Description

This property indicates whether DDL is replicated during replication.

0 : Do not allow DDL replication during replication. When executing DDL, it is executed only in the replicaiton local server.

1 : Allow DDL replication during replication. When executing DDL, DDL is replicated to the replicaiton remote server.

This property can be changed using the ALTER SYSTEM or ALTER SESSION statement while Altibase is running.

#### REPLICATION_DDL_SYNC_TIMEOUT (Unit: second)

##### Data Type

Unsigned Integer

##### Default Value

7200

##### Attributes

Read-Write, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

If the execution time of DDL copy exceeds the number of seconds set in this property, the execution of that statement is canceled for both the replicaiton local and remote servers.

Timeout value is measured based on the replication local server that performs DDL replication.

This property can be changed using the ALTER SYSTEM or ALTER SESSION statemenet while Altibase is running.

#### REPLICATION_EAGER_PARALLEL_FACTOR

##### Data Type

Unsigned Integer

##### Default Value

The smaller value among 'number of CPUs/2' and '512'

##### Attributes

Read-Only, Single Value

##### Range

[1, 512]

##### Description

When replication is executed on EAGER mode, multiple Sender threads are operated in parallel. This property specifies the number of Sender threads to be operated in parallel; an increase in the number of Sender threads leads to an improvement in replication performance. 

When increasing the number of Sender threads with this property, however, the user must note that the order in which the Sender threads send transactions are not guaranteed. For further information about this matter, please refer to the *Replication Manual*.

If this property is not set, the default value is the smaller value among the number of CPUs/2 and 512.

#### REPLICATION_EAGER_RECEIVER_MAX_ERROR_COUNT

##### Data Type

Unsigned Integer

##### Default Value

5

##### Attributes

Read-Write, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

When replication is performed in eager mode, this property can set the number of times the replication Receiver is to attempt data replication.

If this value is set to 5 and an Xlog replication error occurs, the replication Receiver attempts replication up to 5 times, and forcefully terminates the Altibase server if the last attempt fails.

When this value is set to 0, if an Xlog replication error occurs, the replication Receiver attempts replication until it succeeds and does not forcefully terminate the server. 

Replication in eager mode is mainly used in environments where data concurrency between the replication Receiver and the Sender are important. Therefore, data replication is stopped and the server is terminated to prevent data conflicts.

 The value of this property can be changed using the ALTER SYSTEM statement while Altibase is running.

#### REPLICATION_FAILBACK_INCREMENTAL_SYNC

##### Data Type

Unsigned Integer

##### Default Value

1

##### Attributes

Read-Only, Single Value

##### Range

[0, 1]

##### Description

This property sets the execution of incremental sync on or off. If one of the servers during replication in EAGER mode fails and data inconsistency occurs, Incremental Sync performs data synchronization on the inconsistent data upon restart of the failure server. 

- 0: Deactivates Incremental Sync
- 1: Activates Incremental Sync

The value of this property for both Altibase servers participating in replication must be identical. For more detailed information about incremental synchronization and EAGER replication failure recovery, refer to *Replication Manual.*

#### REPLICATION_GAP_UNIT (Unit: byte)

##### Data Type

Unsigned Long

##### Default Value

1048576 (1MB)

##### Attributes

Read-Write, Single Value

##### Range

[1, 2<sup>64</sup>-1]

##### Description 

This property sets the unit that represents the value of REP_GAP for querying the size of the replication gap.

The value of REP_GAP is the result of dividing the value of REP_GAP_SIZE by this property, and rounding up the rest.

By default, REP_GAP_SIZE of V$REPGAP is retrieved in bytes, and REP_GAP is retrieved in megabytes (MB).



#### REPLICATION_GAPLESS_ALLOW_TIME (Unit: microsecond)

##### Data Type

Unsigned Integer

##### Default Value

2000

##### Attributes

Read-Write, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

If the GAPLESS option is enabled, the replication sender allows a replication gap for as long as the value (unit: microseconds) set for the REPLICATION_GAPLESS_ALLOW_TIME property. The replication sender delays transaction commits if it anticipates the replication gap to still exist after the amount of time set for this property. 

For example, if the REPLICATION_GAPLESS_ALLOW_TIME property is set to 5 and the sender sends 1,000 XLogs per second, a replication gap of 5,000 XLogs is allowed. If the current replication gap consists of 10,000 XLogs, this means that transaction commits must be delayed for five microseconds, since 5,000 XLogs have exceeded the limit. 

If the REPLICATION_GAPLESS_ALLOW_TIME property is set to 0, this means that no replication gaps are allowed; transactions will be committed only after replication gaps are dissolved.

The value of this property can be altered using the ALTER SYSTEM statement while Altibase is running. 

#### REPLICATION_GAPLESS_MAX_WAIT_TIME (Unit: microsecond)

##### Data Type

Unsigned Integer

##### Default Value

10*,*000*,*000

##### Attributes

Read-Write, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

When the GAPLESS option is enabled, the REPLICATION_GAPLESS_MAX_WAIT_TIME property sets the maximum amount of time (unit: microseconds) that the replication sender can delay transaction commits to dissolve replication gaps. 

If the REPLICATION_GAPLESS_MAX_WAIT_TIME property is set to 0, transactions will be committed only after replication gaps are dissolved.

The value of this property can be altered using the ALTER SYSTEM statement while Altibase is running. 

#### REPLICATION_GROUPING_TRANSACTION_MAX_COUNT (Unit: count)

##### Data Type

Unsigned Integer

##### Default Value

5

##### Attributes

Read-Only, Single Value

##### Range

[1, 1000]

##### Description

The REPLICATION_GROUPING_TRANSACTION_MAX_COUNT property sets the maximum number of transactions that are allowed to be accumulated into a single transaction group. 

The value of this property can be altered using the ALTER SYSTEM statement while Altibase is running. 

#### REPLICATION_GROUPING_AHEAD_READ_NEXT_LOG_FILE (Unit: count)

##### Data Type

Unsigned Integer

##### Default Value

2

##### Attributes

Read-Only, Single Value

##### Range

[1, 2<sup>32</sup>-1]

##### Description

The REPLICATION_GROUPING_AHEAD_READ_NEXT_LOG_FILE property sets the value to be incremented to the current file being read by the sender; the Ahead Analyzer will start analyzing an XLog that increments (starting from the value of the current file) by as much as this value. 

The value of this property can be altered using the ALTER SYSTEM statement while Altibase is running. 

#### REPLICATION_HBT_DETECT_HIGHWATER_MARK

##### Data Type

Unsigned Integer

##### Default Value

5

##### Attribute

Read-Write, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This property specifies the number of failed connection attempts to make before determining that a failure has occurred in a replication environment. Thus, the maximum time that can pass before it is determined that a host has failed can be calculated by multiplying REPLICATION_HBT_DETECT_TIME * REPLICATION_HBT_DETECT_HIGHWATER_MARK.

In other words, if the HeartBeat thread (see below) fails to connect for 30 seconds (i.e. 5 attempts * 6 seconds, the default values for each of the above properties), it will be handled as a failure.

This property can be changed using the ALTER SYSTEM statement while Altibase is running.

#### REPLICATION_HBT_DETECT_TIME (Unit: second)

##### Data Type

Unsigned Integer

##### Default Value

6

##### Attributes

Read-Write, Single Value

##### Range

[0, 2592000]

##### Description

This property specifies the interval, in seconds, at which to check the HeartBeat thread<sup>12</sup>. The HeartBeat thread checks the host for a fault every 6 seconds (the default value). This property can be changed using the ALTER SYSTEM statement while Altibase is running

[<sup>12</sup>] HeartBeat thread

In an Altibase replication environment, in order to allow physical faults to be detected as quickly as possible while data are being exchanged between a Sender thread and a Receiver thread, a HeartBeat Thread is used to allow each host to regularly check the condition of the other host.

This property can be changed using the ALTER SYSTEM statement while Altibase is running.

#### REPLICATION_IB_LATENCY

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Only, Single Value

##### Range

[0, 1]

##### Description

This property is the RDMA_LATENCY option value of rsocket.

If this value is 1, it uses latency even if it consumes CPU resources.

#### REPLICATION_IB_PORT_NO

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Only, Single Value

##### Range

[0, 65535]

##### Description

When connecting with replication, this property displays the connection port number of the local server when connecting using the InfiniBand.

To use the InfiniBand, the value of the IB_ENABLE property must be 1. If this value is 0, replication cannot be connected with the InfiniBand.

#### REPLICATION_INSERT_REPLACE

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Write, Single Value

##### Range

[0, 1]

##### Description

This property specifies whether to keep inserted contents if an insert conflict occurs during replication. If this value has been set to 0, the insert will not be committed, and the data conflict will be handled as an error, whereas if this value has been set to 1, the data conflict will be ignored and the insert will be committed. 

This property can be changed using the ALTER SYSTEM statement while Altibase is running.

#### REPLICATION_KEEP_ALIVE_CNT 

##### Data Type

Unsigned Integer

##### Default Value

600

##### Attributes

Read-Only, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

A KEEP_ALIVE signal is sent when a Sender thread has not sent a packet and has slept for REPLICATION_SENDER_SLEEP_TIME * REPLICATION_KEEP_ALIVE_CNT.

#### REPLICATION_LOCK_TIMEOUT (Unit: second)

##### Data Type

Unsigned Integer

##### Default Value

5

##### Attributes

Read-Write, Single Value

##### Description

[0, 3600]

##### Description

When a replication deadlock occurs, the Receiver thread will wait indefinitely to establish a lock, which may result in a service interruption. To prevent this, when the Receiver thread requests a lock to perform this kind of operation, it will only wait for the number of seconds specified using this property.

If a lock cannot be acquired within the given time, the corresponding operation will be rolled back.

#### REPLICATION_LOG_BUFFER_SIZE (단위 : MB)

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read Only, Single Value

##### Range

[0, 2<sup>12</sup>-1]

##### Description

This property is set in order to improve replication performance using a dedicated replication log buffer. The dedicated replication log buffer filters and stores only replication logs. The Sender thread can read logs from the log buffer or from disk. However, when reading logs from disk, the processing speed of the Sender thread may be greatly reduced. Furthermore, the additional burden of reading unnecessary logs is imposed. The dedicated replication log buffer mitigates this burden. 

When multiple replication Sender threads are working, replication and overall service performance can suffer. This is because there is only one replication log buffer, so if it is accessed by more than one Sender thread, synchronization overhead is more likely to occur. When the REPLICATION_SYNC_LOG value is set to 1, this property must be set to 0. Otherwise, the Altibase server will fail to start. If the value of this property is set too small, it may lead to worse performance than when it is not used at all (i.e. when it is set to 0).

#### REPLICATION_MAX_COUNT (Unit: count)

##### Data Type

Unsigned Integer

##### Default Value

32

##### Attributes

Read-Only, Single Value

##### Range

[0, 10240]

##### Description

This property specifies the maximum number of replication objects which can be created in Altibase. 

The default value is 32, which means that one server can connect to a maximum number of 32 remote servers by replication.

#### REPLICATION_MAX_LISTEN

##### Data Type

Unsigned Integer

##### Default Value

32

##### Attributes

Read-Only, Single Value

##### Range

[0, 512]

##### Description

This property specifies the maximum size of the “listen queue” when TCP/IP is used for communication between a Sender thread and an Altibase server that maintains a Receiver thread.

#### REPLICATION_MAX_LOGFILE

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Write, Single Value

##### Range

[0, 65535]

##### Description

This property specifies the maximum number of log files preceding the Restart Redo Point that are to be prevented from being deleted, for use in replication. If, after replication starts, changes to a local server are not also made on a remote server for some reason, such as reduced network speed between the local and remote servers, replication will prevent log files from being deleted, even after checkpointing has taken place. Under such circumstances, the number of log files on the local server will continue to increase, which can ultimately lead to a disk full error. 

Therefore, when checkpointing occurs, if the number of accumulated log files preceding the Restart Redo Point exceeds the number specified using this property, replication is temporarily suspended, and the time and XSN at which replication was suspended are stored in the GIVE_UP_TIME and GIVE_UP_XSN columns in the SYS_REPLICATIONS_ meta table. Additionally, all of the log files preceding the Restart Redo Point are deleted. The replication restart SN is set to the highest SN in the current log file, and this value is stored in the XSN column in the SYS_REPLICATIONS_ meta table. Replication will be performed starting from this new restart SN. If it is desired to change this default behavior, change the value of the REPLICATION_SENDER_START_AFTER_GIVING_UP property. Additionally, in order to reinitialize all of the information pertaining to a particular replication object in the SYS_REPLICATIONS_ meta table, execute “ALTER REPLICATION replication_name RESET”. 

If the REPLICATION_MAX_LOGFILE property is set to 0, or if replication is running in EAGER mode, this function is disabled. Please note that because log files are erased when checkpointing is carried out, the values of the CHECKPOINT_INTERVAL_IN_SEC and CHECKPOINT_IN_LOG properties should be considered when setting the value of this property.

#### REPLICATION_POOL_ELEMENT_COUNT (Unit: count)

##### Data Type

Unsigned Integer

##### Default Value

10

##### Attributes

Read-Write, Single Value

##### Range

[1, 1024]

##### Description

This is the amount of memory (number of elements) used when a Sender thread analyzes a log and copies column values. Memory elements are pre-allocated from the memory pool, and their size is specified by REPLICATION_POOL_ELEMENT_SIZE. 

The value of this property can be changed using the ALTER SYSTEM statement while Altibase is running.

#### REPLICATION_POOL_ELEMENT_SIZE (Unit : Byte)

##### Data Type

Unsigned Integer

##### Default value

256

##### Attributes

Read-Write, Single Value

##### Range

[128, 65536]

##### Description

This is the size of a memory element, in bytes, that is used when the sender thread analyzes a log and copies column values. 

This property can be changed using the ALTER SYSTEM statement while Altibase is running. 

#### REPLICATION_PORT_NO

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Only, Single Value

##### Range

[0, 65535]

##### Description

This property specifies the replication port number on the local server, to be used when a replication connection is established. Set this property to 0 to disable replication.

#### REPLICATION_PREFETCH_LOGFILE_COUNT

##### Data Type

Unsigned Integer

##### Default Value

3

##### Attributes

Read-Write, Single Value

##### Range

[0, 1024]

##### Description

This property specifies the number of prefetch log files, that is, the number of log files in each log file group that are read in advance. Pre-reading and caching log files allows the Sender thread to read logs from log files more quickly

#### REPLICATION_RECEIVE_TIMEOUT (Unit: second)

##### Data Type

Unsigned Integer

##### Default Value

7200

##### Attributes

Read-Write, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This property, which is used by both the Sender thread and the Receiver thread, specifies the maximum amount of time, in seconds, to wait for a message from the Receiver or Sender thread, respectively.

In the case where the Sender thread has waited for a response from the Receiver thread for the maximum amount of time specified here, the Sender thread will enter into sleep mode for the amount of time specified using the REPLICATION_SENDER_SLEEP_TIMEOUT property before again attempting to connect to the Receiver thread. In this case, the existing socket is closed and a new socket is created for the new connection attempt.

This property also specifies the maximum time that the Receiver thread waits for a message from a Sender thread. If the specified amount of time has passed, the Receiver thread is automatically terminated, and a new Receiver thread will be created when the Sender thread sends a message. 

This property can be changed using the ALTER SYSTEM statement while Altibase is running.

#### REPLICATION_RECEIVER_APPLIER_ASSIGN_MODE

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

REPLICATION_RECEIVER_APPLIER_ASSIGN_MODE

##### Range

[0, 1]

##### Description

The REPLICATION_RECEIVER_APPLIER_ASSIGN_MODE property sets the mode in which the replication sender is to assign XLogs to the applier. 

0: XLog Count Mode

1: Transaction Count Mode

If the REPLICATION_RECEIVER_APPLIER_ASSIGN_MODE property is set to 0, XLogs are assigned to the applier with the least amount of XLogs. 

If the REPLICATION_RECEIVER_APPLIER_ASSIGN_MODE property is set to 1, XLogs are assigned to the applier with the least number of transactions. 

The value of this property can be altered using the ALTER SYSTEM statement while Altibase is running. 

#### REPLICATION_RECEIVER_APPLIER_QUEUE_SIZE

##### Data Type

Unsigned Integer

##### Default Value

20

##### Attributes

Read-Write, Single Value

##### Range

[2, 2<sup>32</sup>-1]

##### Description

The REPLICATION_RECEIVER_APPLIER_QUEUE_SIZE sets the maximum number of XLogs that the sender is allowed to be passed to the queue for applier threads. 

Although a large value for the REPLICATION_RECEIVER_APPLIER_QUEUE_SIZE property means that a large number of XLogs will be passed to the applier, memory usage increases because XLogs are queued. The user is recommended to set the REPLICATION_RECEIVER_APPLIER_QUEUE_SIZE property to twice as much as the number of appliers. 

The value of this property can be altered using the ALTER SYSTEM statement while Altibase is running. 

#### REPLICATION_RECOVERY_MAX_LOGFILE

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Write, Single Value

##### Range

[0, 2<sup>32</sup>–1]

##### Description

This property specifies the maximum number of log files that are not deleted, based on a Restart Redo Point, for data recovery using replication. 

In order to recover data at the time of replication, the local server does not delete logs that have not been flushed to disk on remote servers. Even if checkpointing takes place at this time, because the log files cannot be deleted, the number of log files on the local server will continue to increase and this can ultimately lead to a disk full error. 

Thus, if the maximum log file count in the recovery options is exceeded when checkpointing occurs, replication-based recovery is aborted and the log files are deleted. Then, replication starts over. 

If this property is set to 0 or replication runs in eager mode, this function is not used. Because log files are deleted when checkpointing occurs, the values of CHECKPOINT_INTERVAL_IN_SEC and CHECKPOINT_IN_LOG should be considered together.

#### REPLICATION_RECOVERY_MAX_TIME (Unit: second)

##### Data Type

Unsigned Integer

##### Default Value

2<sup>32</sup>–1

##### Attributes

Read-Only, Single Value

##### Range

[0, 2<sup>32</sup>–1]

##### Description

If the number of seconds specified using this property is exceeded while the replication module is performing recovery, recovery is stopped and service is provided in the state in which recovery has been performed up to that point. 

If this property is set to 0, replication-based recovery is not performed. 

Before replication-based data recovery is completed, Altibase will not be able to proceed to the service stage, and service may be delayed.

#### REPLICATION_SENDER_AUTO_START

##### Data Type

Unsigned Integer

##### Default Value

1

##### Attributes

Read-Only, Single Value

##### Range

[0, 1]

##### Description

If a replication object which has not been stopped at the termination of the previous Altibase server exists, this replication object is automatically started by default when the server restarts. 

If this value is set to 0, a replication object can be prevented from automatically starting.

#### REPLICATION_SENDER_COMPRESS_XLOG

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Write, Single Value

##### Range

[0, 1]

##### Description

This property specifies whether or not a packet is to be compressed, when data is transmitted via network for replication purposes.

0: Compression is disabled for transmissive data

1: Compression is enabled for transmissive data

This property can be changed using the ALTER SYSTEM statement while Altibase is running.

#### REPLICATION_SENDER_ENCRYPT_XLOG

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Write, Single Value

##### Range

[0, 1]

##### Description

The REPLICATION_SENDER_ENCRYPT_XLOG property sets whether or not to encrypt XLogs that the sender thread sends during replication. 

0: Does not encrypt XLogs.

1: Encrypts XLogs.

#### REPLICATION_SENDER_SEND_TIMEOUT (Unit: second)

##### Data Type

Unsigned Integer

##### Default Value

7200

##### Attributes

Read-Write, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This property specifies the maximum amount of time that the sending thread will wait when sending a packet to a remote server.

It is recommended that this value be the same as the value of the REPLICATION_RECEIVER_TIMEOUT (default 7200 seconds) property. If the value is set to 0, the sender thread uses a blocking socket.

The value of this property can be changed using the ALTER SYSTEM statement while Altibase is running.

#### REPLICATION_SENDER_SLEEP_TIME (Unit: microsecond)

##### Data Type

Unsigned Integer

##### Default Value

10000

##### Attributes

Read-Write, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This property indicates the sleep time, in microseconds, when there are no more logs to be read by the Sender thread. Because certain platforms ignore short Sleep time values, a suitable value must be specified. The value specified here is used in conjunction with REPLICATION_KEEP_ALIVE_CNT to determine when to send KEEP_ALIVE.

#### REPLICATION_SENDER_SLEEP_TIMEOUT (Unit: second)

##### Data Type

Unsigned Integer

##### Default Value

60

##### Attributes

Read-Write, Single Value

##### Range

[0, 2592000]

##### Description

This property specifies the number of microseconds that a replication Sender thread that is in an error state must sleep before trying again. 

This property can be changed using the ALTER SYSTEM statement while Altibase is running.

#### REPLICATION_SENDER_START_AFTER_GIVING_UP

##### Data Type

Unsigned Integer

##### Default Value

1

##### Attributes

Read-Write, Single Value

##### Range

[0, 1]

##### Description

This property determines how replication proceeds after replication has been suspended due to the number of accumulated log files preceding the Restart Redo Point exceeding the value of the REPLICATION_MAX_LOGFILE property.

If this value is set to 0, the replication restart SN (which is stored in the XSN column in the SYS_REPLICATIONS_ meta table) is reinitialized (set to -1), and replication is suspended. Additionally, the value of the IS_STARTED column in the SYS_REPLICATIONS_ meta table is set to 0.

If this value is set to 1, the replication restart SN is set to the last generated sequence number in the current log file, and replication is performed starting from this new restart SN.

#### REPLICATION_SERVER_FAILBACK_MAX_TIME

##### Data Type

Unsigned Integer

##### Default Value

2<sup>32</sup>-1

##### Attributes

Read-Only, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

In EAGER mode replication, when a server that was terminated abnormally is restarted, it resumes providing service only after it has synchronized its data with the data on another (i.e. the remote) server. At this time, if the process of applying the logs from the other server on the server that experienced the fault takes longer than the number of seconds specified using this property, the server that experienced the fault gives up waiting for synchronization to complete.

#### REPLICATION_SQL_APPLY_ENABLE

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Only, Single Value

##### Range

[0, 1]

##### Description

This property configures how to synchronize inconsistent data between the local and remote servers during the replication. 

- 0: Replication works using XLog. At this time, if the meta information is different, a Handshaking error occurs.

- 1: If replication is performed under the following conditions, XLog is converted into a SQL statement and reflected in the replicated table.

- Column information  
  If the data types are different  
  If sizes, precisions, and scales are different
  
- Constraints  
  If the check constraints are different
  
  If Not Null constraints are different
  
  If any of the other meta information contains a LOB column
  
- Indexes  
  If a unique index or function-based index consists of columns to be replicated and not to be replicated  
  If the configuration information for the unique index is different  
  If the configuration information for the function-based index is different

#### REPLICATION_SYNC_APPLY_METHOD

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Only, Single Value

##### Range

[0, 1]

##### Description

This property configures how to synchronize inconsistent data between the local and remote servers during the replication. 

- 0: Normal Insert
- 1: Direct-Path Insert

Please refer to *Administrator’s Manual* for in-depth description on Direct-Path Insert. 

The value of this property can be modified through ALTER SYSTEM statement during the Altibase operation.

#### REPLICATION_SYNC_LOCK_TIMEOUT (Unit: second)

##### Data Type

Unsigned Integer

##### Default Value

30

##### Attributes

Read-Write, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

When replication synchronization is performed, the Replication Sender Thread determines the current position in the log at which replication will start after synchronization. In order to prevent another transaction from changing the data in the table on which synchronization is to be performed right at the time of this determination, the Replication Sender Thread obtains an S Lock on the table on which synchronization is to be performed for a short time before synchronization. This property specifies the amount of time, in seconds, to wait to establish a lock when a table to be synchronized has been locked by another transaction. If a lock is requested but cannot be obtained immediately, the replication process will wait for the amount of time specified here. If a lock cannot be obtained within the amount of time specified here, the synchronization attempt will be handled as an error. If this value is specified as 0, a lock is not established on the replication target table; however, data conflict can occur

This property can be changed using the ALTER SYSTEM statement while Altibase is running.

#### REPLICATION_SYNC_LOG

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Only, Single Value

##### Range

[0, 1]

##### Description

When performing replication, because the Sender thread sends logs that are in memory regardless of whether they have been committed to disk, data inconsistency or other problems may occur in the event of system or media failure.

To prevent this problem, setting this value to 1 ensures that the Sender thread only sends logs that have already been committed to disk.

#### REPLICATION_SYNC_TUPLE_COUNT

##### Data Type

Unsigned long

##### Default Value

50000

##### Attributes

Read-Write, Single Value

##### Range

[0, 2<sup>64</sup>-1]

##### Description

This property specifies the maximum number of records that each Sender thread can read and handle during parallel synchronization.

This property can be changed using the ALTER SYSTEM statement while Altibase is running.

#### REPLICATION_TIMESTAMP_RESOLUTION

##### Data Type

Unsigned Integer

##### Default Value

1

##### Attributes

Read-Write, Single Value 값

##### Range

[0, 1]

##### Description

In an Active-Active replication environment, if this property is set to 1 and a TIMESTAMP column exists in a given replication target table, then the TIMESTAMP-based resolution scheme is used to resolve any data conflicts that occur in that table. 

However, even if a TIMESTAMP column exists in a replication target table, if this value has been set to 0, some other conflict resolution scheme is used. 

For more detailed information about TIMESTAMP-based resolution and data conflicts, please refer to the *Altibase Replication Manual*. 

This property can be changed using the ALTER SYSTEM statement while Altibase is running.

#### REPLICATION_TRANSACTION_POOL_SIZE

##### Data Type

Unsigned Integer

##### Default Value

1

##### Attributes

Read-Write, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

Replication receivers use transactions when copying data and create respective transaction pools - wherein transactions can be created in advance for use - for performance improvement. This property specifies the number of transactions that are to be created in advance in transaction pools.

If the number of transactions existing in pools falls short, the replication receiver will create new transactions and use them. The transactions thus created are returned to pools after use; if the number of transactions existing at that time is larger than the value specified in this property, the transactions are immediately freed, instead of being returned. 

If set to an excessively large value, it can constrain the number of normal transactions; therefore, an appropriate number of transactions must be specified. This property permits the maximum value of 232 -1; however, the actual maximum value is identical to the value specified in the property of TRANSACTION_TABLE_SIZE. If the user specifies this value to be larger than the value of TRANSACTION_TABLE_SIZE, the value of this property will be internally set as the value of the TRANSACTION_TABLE_SIZE. 

This property value can be changed while Altibase is running; however, transaction pools are initialized at the creation of replication receiver threads and replication must be restarted for the modified property values to be applied. 

This property value can be changed using the ALTER SYSTEM statement while Altibase is running.

#### REPLICATION_UPDATE_REPLACE

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Write, Single Value

##### Range

[0, 1]

##### Description

This property specifies whether to keep updated contents if an update conflict occurs during replication. If this value has been set to 0, the update will not be committed, and the data conflict will be handled as an error, whereas if this value has been set to 1, the data conflict will be ignored and the update will be committed. 

This property can be changed using the ALTER SYSTEM statement while Altibase is running.

### Network and Security Properties

#### IB_CONCHKSPIN

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Only, Single Value

##### Range

[0, 2147483]

##### Description

This property sets the value of the RDMA_CONCHKSPIN option of rsocket. This is the value to set which period to check the connection of InfiniBand. If this value is 0, the default value of rsocket is used.

This property is only available when using the Altibase rdma-core. ( <https://github.com/ALTIBASE/rdma-core> )

#### IB_ENABLE

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read Only, Single Value

##### Range

[0, 1]

##### Description

This property is an option to use InfiniBand in Altibase. This feature is only available on Linux.

0 : IB is not used (default value)

1: IB is used

#### IB_LATENCY 

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Only, Single Value

##### Range

[0, 1]

##### Description

This property sets the value of the RDMA_LATENCY option of rsocket. 

If the value of this property is 1, tuning code is used to reduce latency even though it consumes more CPU resources.

This property is only available when using the Altibase rdma-core. ( <https://github.com/ALTIBASE/rdma-core> )

#### IB_LISTENER_DISABLE

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Only, Single Value

##### Range

[0, 1]

##### Description

This property can set whether to start the InfiniBand listener when starting Altibase.

0: InfiniBand listener is started (default).

1: InfiniBand listener is not started.

#### IB_MAX_LISTEN 

##### Data Type

Unsigned Integer

##### Default Value

128

##### Attributes

Read-Only, Single Value

##### Range

[0, 1024]

##### Description

This property specifies the maximum number of clients that can connect to InfiniBand and use Altibase at the same time.

#### IB_PORT_NO

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Only, Single Value

##### Range

[1024, 65535]

##### Description

This property specifies the port number used for communication using the InfiniBand.

#### SNMP_ALARM_QUERY_TIMEOUT

##### Data Type

Unsigned Integer

##### Default Value

1

##### Attributes

Read-Only, Single Value

##### Range

[0, 1]

##### Description

Sets whether or not to send a trap when a query timeout occurs in a session. The default value is 1 and sends a trap. For more detailed information, please refer to altiPropertyAlarmQueryTimeout in the SNMP Agent Guide.

#### SNMP_ALARM_FETCH_TIMEOUT

##### Data Type

Unsigned Integer

##### Default Value

1

##### Attributes

Read-Only, Single Value

##### Range

[0, 1]

##### Description

Sets whether or not to send a trap when a fetch timeout occurs. The default value is 1 and sends a trap. For more detailed information, please refer to altiPropertyAlarmFetchTimeout in the SNMP Agent Guide. 

#### SNMP_ALARM_UTRANS_TIMEOUT

##### Data Type

Unsigned Integer

##### Default Value

1

##### Attributes

Read-Only, Single Value

##### Range

[0, 1]

##### Description

Sets whether or not to send a trap when a utrans timeout occurs. 

0: Does not raise a trap.

1: Raises a trap.

For more detailed information, please refer to altiPropertyAlarmUtransTimeout in the SNMP Agent Guide.

#### SNMP_ALARM_SESSION_FAILURE_COUNT

##### Data Type

Unsigned Integer

##### Default Value

3

##### Attributes

Read-Only, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

Sets the number of times an error is allowed to continuously occur before a trap is sent. The default value is 3. If the value is 0, a trap is not sent. For more detailed information, please refer to altiPropertyAlarmSessionFailureCount in the SNMP Agent Guide.

#### SNMP_ENABLE 

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read Only, Single Value

##### Range

[0, 1]

##### Description

To use SNMP, this property must be set to 1(Enable). The default value is 0(Disable). 

0 : Use SNMP

1: Do not use SNMP 

#### SNMP_MSGLOG_FLAG 

##### Data Type

Unsigned Integer

##### Default Value

3

##### Attributes

Read-Write, Single Value

##### Range

[3, 12]

##### Description

Sets the log output level. Four levels (‘1’, ‘2’, ‘4’, ‘8’) are available and the sum of these can comprise a level. The default value is 3(1+2) and logs are output for Level1 and Level3. 

#### SNMP_PORT_NO 

##### Data Type

Unsigned Integer

##### Default Value

20400

##### Attributes

Read-Only, Single Value

##### Range

[1024, 65535]

##### Description

This is the UDP port for communication between Altibase and altisnmpd (Altibase SNMP subagent).

#### SNMP_TRAP_PORT_NO 

##### Data Type

Unsigned Integer

##### Default Value

20400

##### Attributes

Read-Only, Single Value

##### Range

[1024, 65535]

##### Description

This is the UDP port for sending traps between Altibase and altisnmpd (Altibase SNMP subagent).

#### SNMP_RECV_TIMEOUT (Unit: millisecond)

##### Data Type

Unsigned Integer

##### Default Value

1000

##### Attributes

Read-Only, Single Value

##### Range

[1, 2<sup>32</sup>-1]

##### Description

This is the communication timeout value.

When Altibase and altisnmpd(Altibase SNMP subagent) communicate, the application waits for as many milliseconds as specified for this property.

#### SNMP_SEND_TIMEOUT (Unit: millisecond)

##### Data Type

Unsigned Integer

##### Default Value

100

##### Attributes

Read-Only, Single Value

##### Range

[1, 2<sup>32</sup>-1]

##### Description

This is the communication timeout value.

When Altibase and altisnmpd (Altibase SNMP subagent) communicate, the application waits for as many milliseconds as specified for this property. 

#### SSL_CA

##### Data Type

String

##### Default Value

None

##### Attributes 

Read-Only, Single Value

##### Range

None

##### Description

Specifies the file path to store CA certificates to certify the ownership of received certificates. CA certificates can exist in a user-specific file path or a X.509 structured directory. An example of this value could be $ALTIBASE_HOME/cert/ ca-cert.pem.

#### SSL_CAPATH

##### Data Type

String

##### Default Value

None

##### Attributes

Read-Only, Single Value

##### Range

None

##### Description

Specifies CAPATH in a CA directory format. An example of this value could be $ALTIBASE_HOME/etc/ssl/certs.

#### SSL_CERT

##### Data Type

String

##### Default Value

None

##### Attributes

Read-Only, Single Value

##### Range

None

##### Description

Sets the Altibase certificate path. An example of this value could be $ALTIBASE_HOME/cert.pem.

#### SSL_CIPHER_LIST 

##### Data Type

String

##### Default Value

None

##### Attributes

Read-Only, Single Value

##### Range

255

##### Description

A list of cipher algorithms available for the server and client to use and negotiate with. Depending on your security policy, you can specify one or more cipher names and separate them by colons. You can check the list at OpenSSL (http://www.openssl.org/) or execute the following command in the shell environment.

```
$ openssl ciphers
```

#### SSL_CLIENT_AUTHENTICATION

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read Only, Single Value

##### Range

[0, 1]

##### Description

Sets whether or not to request a certificate from the client when the server and client communicate over SSL. If the value is 0 (default), the client requests a certificate from the server. If the value is 1, the server requests a certificate from the client during the SSL handshake.

0: Authenticates the server only (default) 

1: Authenticates the server and client concurrently

#### SSL_ENABLE 

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Only, Single Value

##### Range

[0, 1]

##### Description

Switches the SSL/TLS feature on or off within Altibase. The default value is 0 (Disable). 

0: Disables SSL/TLS 

1: Enables SSL/TLS

#### SSL_KEY

##### Data Type

String

##### Default Value

None

##### Attribute

Read-Only, Single Value

##### Range

None

##### Description

Sets the server private (secret) key path. 

An example of this value could be $ALTIBASE_HOME/cert/server- key.pem.

#### SSL_MAX_LISTEN

##### Data Type

Unsigned Integer

##### Default Value

128

##### Attributes

Read-Only, Single Value

##### Range

[0, 16384]

##### Description

Sets the listen queue maximum size for concurrent SSL/TLS connections. Note that more listeners require more memory.

#### SSL_PORT_NO 

##### Data Type

Unsigned Integer

##### Default Value

20443

##### Attributes

Read-Only, Single Value

##### Range

[1024, 65535]

##### Description

Specifies the listening port number for SSL connections. 

#### TCP_ENABLE

##### Data Type

Unsigned Integer

##### Default Value

1

##### Attributes

Read-Only, Single Value

##### Range

[0, 1]

##### Description

Altibase server can configure whether or not to communicate with TCP/IP as a communication protocol.

0: Using TCP/IP 

1: Not using TCP/IP

### Message Logging Properties

#### ALL_MSGLOG_FLUSH

##### Data Type

Unsigned Integer

##### Default Value

1

##### Attributes

Read-Write, Single Value

##### Range

[0, 1]

##### Description

If this property is set to 1, all database messages are written immediately to disk, whereas if it is set to 0, Altibase writes the messages all at once at regularly scheduled intervals In order to prevent reduced performance attributable to excessive logging, it is recommended that this value be set to 0 for normal operations, and that it be set to 1 when troubleshooting.

#### COLLECT_DUMP_INFO

##### Data Type

Unsigned Integer

##### Default Value

1

##### Attributes

Read-Write, Single Value

##### Range

[0, 1]

##### Description

This property specifies whether or not information about message files and log files are to be collected when the server terminates abnormally. 

0: Information about message files and log files are not collected. 

1: Information about message files and log files are collected.

#### DK_MSGLOG_COUNT

##### Data Type

Unsigned Integer

##### Default Value

10

##### Attributes

Read-Only, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This property specifies the maximum number of message files that in the connection process when linking a database.

#### DK_MSGLOG_FILE

##### Data Type

String

##### Default Value

altibase_lk.log

##### Attributes

Read-Only, Single Value

##### Range

None

##### Description

This is property specifies a database link file that records message that occur during the connection process.

#### DK_MSGLOG_FLAG

##### Data Type

Unsigned Integer

##### Default Value

6

##### Attributes

Read-Write, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

Flag value indicating whether warning messages or trace messages generated by the connection process module of the database link are logged to LK_MSGLOG_FILE.

If it is 0, it is not written. If it is greater than 0, it is written.

#### DK_MSGLOG_SIZE

##### Data Type

Unsigned Integer

##### Default Value

10 \* 1024 \* 1024

##### Attributes

Read-Only, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

THis property specifies the maximum size of the message file of the connect process in the database link.

#### DUMP_MSGLOG_COUNT

##### Data Type

Unsigned Integer

##### Default Value

10

##### Attributes

Read-Only, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This property specifies the maximum number of message files to which debugging information for server errors are written.

#### DUMP_MSGLOG_FILE

##### Data Type

String

##### Default Value

altibase_dump.log

##### Attributes

Read-Only, Single Value

##### Range

None

##### Description

This property specifies the name of the message file to which debugging information for server errors is written.

#### DUMP_MSGLOG_SIZE (Unit: byte)

##### Data Type

Unsigned Integer

##### Default Value

10 \* 1024 \* 1024

##### Attributes

Read-Only, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This property specifies the name of the message file to which debugging information for server errors is written

#### DUMP_MSGLOG_RESERVE_SIZE (Unit : byte)

##### Data type

Unsigned Integer

##### Default Value

10 \* 1024 \* 1024

##### Attributes

Read-only, Single value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This property specifies the amount of space to secure in advance on the disk to store the message file in which debugging information is recorded.

#### ERROR_MSGLOG_COUNT

##### Data Type

Unsigned Integer

##### Default Value

10

##### Attributes

Read-Only, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This property specifies the maximum number of message files for server errors.

#### ERROR_MSGLOG_FILE

##### Data Type

String

##### Default Value

altibase_error.log

##### Attributes

Read-Only, Single Value

##### Range

None

##### Description

This property specifies the name of the file to which errors raised on the server are written. Also, the process call stack is recorded in this file when Altibase shuts down abnormally.

#### ERROR_MSGLOG_SIZE (Unit: byte)

##### Data Type

Unsigned Integer

##### Default Value

10 \* 1024 \* 1024

##### Attributes

Read-Only, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This property specifies the maximum size, in bytes, of the file to which server error messages are stored.

#### ERROR_MSGLOG_RESERVE_SIZE (Unit : byte)

##### Data type

Unsigned Integer

##### Default value

10 \* 1024 \* 1024

##### Attributes

Read-Only, Single value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This property specifies the amount of space to be reserved in advance for the file where the server error message is stored.

#### LB_MSGLOG_COUNT 

##### Data Type

Unsigned Integer

##### Default Value

10

##### Attributes

Read-Only, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This property specifies the maximum number of message files about service thread.

#### LB_MSGLOG_FILE 

##### Data Type

String

##### Default Value

altibase_lb.log

##### Attributes

Read-Only, Single Value

##### Range

None

##### Description

This property is the file to which service thread-related message are written.

#### LB_MSGLOG_FLAG 

##### Data Type

Unsigned Integer

##### Default Value

1

##### Attributes

Read-Write, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This property specifies the message of service thread to be written to LB_MSGLOG_FILE as follows.

0: not record 

1: Creation and release of the service thread 

2: Log for the service thread moved to task 

3: (1+2) Creation and release of the service thread, log for the service thread moved to task 

#### LB_MSGLOG_SIZE

##### Data Type

Unsigned Integer

##### Default Value

10 \* 1024 \* 1024

##### Attributes

Read-Only, Single Value 

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This property specifies the maximum size of the file to which service thread are written.

#### MM_MSGLOG_COUNT

##### Data Type

Unsigned Integer

##### Default Value

10

##### Attributes

Read-Only, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This sets the maximum number of message files for the Main module.

#### MM_MSGLOG_FILE

##### Data Type

String

##### Default Value

altibase_mm.log

##### Attributes

Read Only, Single Value

##### Range

None

##### Description

This property specifies the file in which to write messages that arise during Main module processing. 

#### MM_MSGLOG_RESERVE_SIZE (Unit : byte)

##### Data type

Unsigned Integer

##### Default value

10 \* 1024 \* 1024

##### Attributes

Read-Only, Single value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This property specifies the amount of space to reserve on the disk in advance to store the message file for the main module.

#### MM_MSGLOG_SIZE (Unit: byte)

##### Data Type

Unsigned Integer

##### Default Value

10 \* 1024 \* 1024

##### Attributes

Read-Only, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This property sets the maximum size of the Main module message files.

#### MM_SESSION_LOGGING

##### Data Type

Unsigned Integer

##### Default

0

##### Attributes

Read-Write, Single Value

##### Range

[0, 1]

##### Description

This is a flag value that indicates whether to write session information regarding all database logon and logoff events to MM_MSGLOG_FILE. Session information includes session ID, user name, IP address, client program PID and other details about the client program. 

If this property is set to 0, no messages are written, whereas if it is set to 1, the messages are written.

#### NETWORK_ERROR_LOG 

##### Data Type

Unsigned Integer

##### Default Value

1

##### Attributes

Read-Write, Single Value

##### Range

[0, 1]

##### Description

This property specifies whether to write network-related error messages in the server message file. 

In an unstable network environment, in which error messages are frequently output, setting this value to 0 prevents network-related error messages from being output.

#### QP_MSGLOG_COUNT

##### Data Type

Unsigned Integer

#####  Default Value

10

##### Attributes

Read-Only, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This property sets the maximum number of message log files for the Query Processor.

#### QP_MSGLOG_FILE

##### Data Type

String

##### Default Value

altibase_qp.log

##### Attributes

Read-Only, Single Value

##### Range

None

##### Description

This property specifies the name of the file in which to write messages when processing queries.

#### QP_MSGLOG_FLAG

##### Data Type

Unsigned Integer

##### Default Value

2

##### Attributes

Read-Write, Single Value

##### Range

[0, 2<sup>32</sup> –1]

##### Description

This is a flag value that indicates whether to write trace messages generated by the Query Processor in QP_MSGLOG_FILE.

If this property is set to 0, the messages are not written, whereas if it is set to a value greater than 0, the messages are written.

#### QP_MSGLOG_RESERVE_SIZE (Unit : byte)

##### Data type

Unsigned Integer

##### Default value

10 \* 1024 \* 1024

##### Attributes

Read-Only, Single value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This property specifies the amount of space to be reseroved on disk to store the message file of the query processor.

#### QP_MSGLOG_SIZE (Unit: byte)

##### Data Type

Unsigned Integer

##### Default Value

10 \* 1024 \* 1024

##### Attributes

Read-Only, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This property specifies the maximum size, in bytes, of the Query Processor message log files.

#### QUERY_PROF_FLAG

##### Data Type

Integer

##### Default Value

0

##### Attributes

Read-Write, Single Value

##### Range

[0, 2<sup>6</sup>-1]

##### Description

This property enables information about the work being conducted by a server and the overall state of the server to be written to a file for later analysis. The user can specify that information is written as desired by suitably combining the following values:

- 0 : Write nothing
- 1: Every time a SQL statement is executed, write the executed SQL statement, execution time, execution information, and information about index and disk access. The value for the TIMED_STATISTICS property must be set to 1 to print the proper execution time. 
- 2: Every time a SQL statement is executed, write the BIND parameter(s). 
- 4: Every time a SQL statement is executed, write the execution plan. 
- 8: Write session information (i.e. the data in V\$SESSTAT) every 3 seconds. 
- 16: Write system information (i.e. the data in V$SYSSTAT) every 3 seconds.
- 32: Write information about memory (i.e. the data in V\$SYSSTAT) every 3 seconds.

For example, if this property is set to 1+4+32=37, then whenever a SQL statement is executed, the execution information and execution plan for the SQL statement is written, and additionally, information about memory is written every 3 seconds.

This file can be converted to a form suitable for analysis using the altiprofile utility. For more information, please refer to the portion of the *Altibase Utilities Manual* pertaining to the altiprofile utility. 

This property can be changed using the ALTER SYSTEM statement while Altibase is running.

#### QUERY_PROF_LOG_DIR

##### Data Type

String

##### Default Value

\$ALTIBASE_HOME/trc

##### Attributes

Read-Write, Single Value

##### Range

[1, 1024 ]

##### Description

This property specifies the directory path in which files to which status information of the Altibase server and operations executed on it are written are to be saved. 

The value of this property can be changed using the ALTER SYSTEM statement while Altibase is running. 

#### RP_CONFLICT_MSGLOG_COUNT

##### Data Type

Unsigned Integer

##### Default

10

##### Attributes

Read-Only, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This property specifies the maximum number of files to which the trace log is written in the event of a replication conflict.

#### RP_CONFLICT_MSGLOG_DIR

##### Data Type

String

##### Default

\$ALTIBASE_HOME/trc

##### Attributes

Read-Only, Single Value

##### Range

None

##### Description

This property specifies the directory for the file to which the trace log is written in the event of a replication conflict.

#### RP_CONFLICT_MSGLOG_ENABLE

##### Data Type

Unsigned Integer

##### Default Value

1

##### Attributes

Read-Only, Single Value

##### Range

[0, 1]

##### Description

This property specifies whether or not the trace log of a replication conflict is to be written.

#### RP_CONFLICT_MSGLOG_FILE

##### Data Type

String

##### Default Value

altibase_rp_conflict.log

##### Attributes

Read-Only, Single Value

##### Range

None

##### Description

This property specifies the file to which the trace log of a replication conflict is written.

#### RP_CONFLICT_MSGLOG_FLAG

##### Data Type

Unsigned Integer

##### Default Value

6

##### Attributes

Read-Write, Single Value

##### Range

[0, 2<sup>32</sup> –1]

##### Description

This property specifies the logging level of the trace log of a replication conflict. 

The following values are available for specification:

2: Writes conflict messages 

4: Writes SQL statements that cause conflict 

6: Write both conflict messages and SQL statements that cause conflict

#### RP_CONFLICT_MSGLOG_RESERVE_SIZE (Unit : byte)

##### Data type

Unsigned Integer

##### Default Value

10 \* 1024 \* 1024

##### Attributes

Read-Only, Single value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This property specifies the amount of space to be reserved on disk for storing the trace log file for a replication collison.

#### RP_CONFLICT_MSGLOG_SIZE (Unit: bytes)

##### Data Type

Unsigned Integer

##### Default Value

10 \* 1024 \* 1024

##### Attributes

Read-Only, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This property specifies the maximum size, in bytes, of replication conflict trace logs.

#### RP_MSGLOG_COUNT

##### Data Type

Unsigned Integer

#####  Default Value

10

##### Attributes

Read Only, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This property specifies the maximum number of replication message log files.

#### RP_MSGLOG_FILE

##### Data Type

String

##### Default Value

altibase_rp.log

##### Attributes

Read-Only, Single Value

##### Range

None

##### Description

This property specifies the name of the file in which to write messages output from the Replication Manager.

#### RP_MSGLOG_FLAG

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Write, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This is a flag value that indicates whether to write trace messages generated by the Replication Manager module in RP_MSGLOG_FILE.

If this property is set to 0, no messages are written, whereas if it is set to a value greater than 0, the messages are written.

#### RP_MSGLOG_RESERVER_SIZE (Unit: byte)

##### Data Type

Unsigned Integer

##### Default Value

10 * 1024 * 1024

##### Attributes

Read-Write, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This property specifies the amount of space to be reserved on the disk for storage of the replicaiton message file.

#### RP_MSGLOG_SIZE (Unit: byte)

##### Data Type

Unsigned Integer

##### Default Value

10 \* 1024 \* 1024

##### Attributes

Read-Only, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This property specifies the maximum size, in bytes, of the replication message log file.

#### SERVER_MSGLOG_COUNT

##### Data Type

Unsigned Integer

##### Default Value

10

##### Attributes

Read Only, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This property specifies the maximum number of server message log files.

#### SERVER_MSGLOG_DIR

##### Data Type

String

##### Default Value

\$ALTIBASE_HOME/trc

##### Attributes

Read-Only, Single Value

##### Range

None

##### Description

This property specifies the path in which altibase.lock, which is an internally used server maintenance file, and SERVER_MSGLOG_FILE, which is the server module message file in which information about the server startup, shutdown etc. is written, are located. 

This directory can also serve as the default directory for individual server modules’ message files, such as SM_MSGLOG_FILE, QP_MSGLOG_FILE, RP_MSGLOG_FILE and the like.

#### SERVER_MSGLOG_FILE

##### Data Type

String

##### Default Value

altibase_boot.log

##### Attributes

Read-Only, Single Value

##### Range

None

##### Description

This property specifies the file name for messages left by the server module. 

Messages pertaining to Altibase startup, warnings, and abnormal termination are written to the server message log file.

#### SERVER_MSGLOG_FLAG

##### Data Type

Unsigned Integer

##### Default Value

7

##### Attributes

Read-Write, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This is a flag value that indicates whether to write trace messages generated by the server module in SERVER_MSGLOG_FILE. 

If this property is set to 0, no messages are written, whereas if it is set to a value greater than 0, the messages are written.

#### SERVER_MSGLOG_RESERVE_SIZE (Unit : byte)

##### Data type

Unsigned Integer

##### Default Value

10 \* 1024 \* 1024

##### Attributes

읽기 전용, 단일 값

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This property specifies the amount of space to be reserved on the disk for storage of the server message file.

#### SERVER_MSGLOG_SIZE (Unit: byte)

##### Data Type

Unsigned Integer

##### Default Value

10 \* 1024 \* 1024

##### Attributes

Read-Only, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This property specifies the maximum size, in bytes, of server message log files.

#### SM_MSGLOG_COUNT

##### Data Type

Unsigned Integer

##### Default Value

10

##### Attributes

Read-Only, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This property specifies the maximum number of Storage Manager message log files.

#### SM_MSGLOG_FILE

##### Data Type

String

##### Default Value

altibase_sm.log

##### Attributes

Read Only, Single Value

##### Range

None

##### Description

This property specifies the prefix of the name of the message file(s) in which the Storage Manager writes messages.

#### SM_MSGLOG_FLAG

##### Data Type

Unsigned Integer

##### Default Value

2147483647

##### Attributes

Read-Write, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This is a flag value that indicates whether to write trace messages generated by the Storage Manager module in the file(s) specified in SM_MSGLOG_FILE. 

If this property is set to 0, no messages are written, whereas if it is set to a value greater than 0, the messages are written.

#### SM_MSGLOG_RESERVE_SIZE (Unit : byte)

##### Data Type

Unsigned Integer

##### Default Value

10 \* 1024 \* 1024

##### Attributes

Read-Only, Single value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This property specifies the amount of space to be reserved on the disk to store the message file of the storage manager.

#### SM_MSGLOG_SIZE (Unit: byte)

##### Data Type

Unsigned Integer

##### Default Value

10 \* 1024 \* 1024

##### Attributes

Read-Only, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This property specifies the maximum size, in bytes, of the Storage Manager message log files.

#### TRC_MSGLOG_RESERVE_SIZE (Unit : byte)

##### Data Type

Unsigned Integer

##### Default Value

10 \* 1024 \* 1024

##### Attributes

Read-Only, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This property specifies the size in advance to secure the space of the trace log file on the disk where warning messsages, etc., gneerated when starting the server can be recorded.

#### TRCLOG_DETAIL_PREDICATE

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Write, Single Value

##### Range

[0, 1]

##### Description

When Explain Plan mode is being used in iSQL, this property specifies whether to display the status of a predicate portion of a WHERE clause. To use this trace log, set this parameter to 1.

This property can be changed using the ALTER SYSTEM statement while Altibase is running.

#### XA_MSGLOG_COUNT

##### Data Type

Unsigned Integer

##### Default Value

10

##### Attributes

Read Only, Single Value

##### Range

[0, 2<sup>32</sup>–1]

##### Description

This property specifies the maximum number of XA message files used by the server.

#### XA_MSGLOG_FILE

##### Data Type

String

##### Default Value

altibase_xa.log

##### Attributes

Read-Only, Single Value

##### Range

None

##### Description

This property specifies the prefix of the name of the file(s) in which XA message logs from the server are written.

#### XA_MSGLOG_FLAG

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Write, Single Value

##### Range

[0, 3]

##### Description

This property determines which of the server XA messages to write to disk. The possible values are as follows: 

0: Write only critical XA-related messages 

1: Write messages pertaining to XA calls 

2: Write messages when XIDs are allocated, freed, etc. 

3: Write all message logs related to XA

#### XA_MSGLOG_RESERVE_SIZE (Unit : byte)

##### Data Type

Unsigned Integer

##### Default Value

10 \* 1024 \* 1024

##### Attributes

Read-Only, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This property specifies the amount to space to be reserved in advance for storage of the XA message file for the server.

#### XA_MSGLOG_SIZE 

##### Data Type

Unsigned Integer

##### Default Value

10 \* 1024 \* 1024

##### Attributes

Read Only, Single Value

##### Range

[0, 2<sup>32</sup>–1]

##### Description

This property specifies the maximum size of XA message files used by the server.

### Database Link Properties

#### DBLINK_ALTILINKER_CONNECT_TIMEOUT (Unit: second)

##### Data Type

Unsigned Integer

##### Default Value

100

##### Attributes

Read-Only, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This property specifies the connection timeout, in seconds, when the Altibase server attempts to establish a connection to AltiLinker.

#### DBLINK_DATA_BUFFER_ALLOC_RATIO

##### Data Type

Unsigned Integer

##### Default Value

50

##### Attributes

Read-Only, Single Value

##### Range

[0, 1]

##### Description

This is the space in which the local server retrieves and stores the result sets of a query executed on a remote server through a database link. This is called the database link-exclusive data buffer. This property specifies the ratio of the record buffer to be allocated per query for the remaining space in the database link-exclusive data buffer. 

#### DBLINK_DATA_BUFFER_BLOCK_COUNT

##### Data Type

Unsigned Integer

##### Default Value

128

##### Attributes

Read-Only, Single Value

##### Range

[0, 2<sup>12</sup>-1]

##### Description

This is the space in which the local server retrieves and stores the result sets of a query executed on a remote server through a database link. This is called the database link-exclusive data buffer. This property specifies the initial number of allocations for record buffer blocks that compose the data buffer. The size of the data buffer is DBLINK_DATA_BUFFER_BLOCK_COUNT * DBLINK_DATA_BUFFER_BLOCK_SIZE.

#### DBLINK_DATA_BUFFER_BLOCK_SIZE (Unit: byte)

##### Data Type

Unsigned Integer

##### Default Value

2 MBytes

##### Attributes

Read-Only, Single Value

##### Range

[0, 29]

##### Description

This is the space in which the local server retrieves and stores the result sets of a query executed on a remote server through a database link. This is called the database link-exclusive data buffer. This property specifies the size, in bytes, of the record buffer block which composes the data buffer.

#### DBLINK_ENABLE

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Write, Single Value

##### Range

[0, 1]

##### Description

This property specifies the AUTOCOMMIT mode of the remote database. This property is only applied when the DBLINK_GLOBAL_TRANSACTION_LEVEL is set to 0. 

0: Autocommit-Off 

1: Autocommit-On

#### DBLINK_GLOBAL_TRANSACTION_LEVEL

##### Data Type

Unsigned Integer

##### Default Value

1

##### Attributes

Read-Only, Single Value

##### Range

[0, 2]

##### Description

This property specifies the execution level of the global transaction. When this property is set to 0, the DBLINK_REMOTE_STATEMENT_AUTOCOMMIT property must be set to correspond to the AUTOCOMMIT mode of the remote database. 

* 0: Remote Statement Execution Level. 

  This level perceives each transaction on servers(local and remote servers) participating in one global transaction as separate transactions, so the transactions must be respectively committed at the local and remote servers in order to commit the global transaction. Even if a global transaction is in this level, a COMMIT performed on the local server does not affect the remote server. 

* 1: Simple Transaction Commit Level.

  This level perceives all transactions on servers(local and remote servers) participating in one global transaction as one transaction. Therefore, if a global transaction is committed on a local server, all transactions participating in the global transaction are committed..

* 2:Two-Phase Commit (2PC) Level. 

  At this level, the 2PC protocol is supported to ensure ttransaction consistency of database systems that participating in one global transaction. If a global transaction begines, this property cannot be changed until the end of the transaction.

#### DBLINK_RECOVERY_MAX_LOGFILE

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Write, Single Value

##### Range

[1, 2<sup>32</sup>-1]

##### Description

This property specifies the maximum number of log files that Altibase HDB maintains or distributed transaction recovery when a heterogeneous database system fails during a transaction.

If this property value is 0, consistency is guaranteed because the log for distributed transaction recovery is not deleted.

However, if the property value is set to a value greater than 1, consistency cannot be guaranteed because the log is deleted by a checkpoint even if the distributed transaction is not completed when the number of log files is exceeded.

The value of this property can be changed using the ALTER SYSTEM statement while Altibase is running.

#### DBLINK_REMOTE_STATEMENT_AUTOCOMMIT

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Write, Single Value

##### Range

[0, 1]

##### Description

This property specifies the AUTOCOMMIT mode of the remote database. This property is only applied when the DBLINK_GLOBAL_TRANSACTION_LEVEL is set to 0. 

0: Autocommit-Off 

1: Autocommit-On

#### DBLINK_REMOTE_TABLE_BUFFER_SIZE (Unit: MB)

##### Data Type

Unsigned Integer

##### Default Value

50

##### Attributes

Read-Write, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This is a memory buffer which can temporarily store query results if a query is executed through REMOTE_TABLE keyword in the remote server.

The stored query results are deleted after being delivered to a query processor. However, the property value should be adjusted since it cannot be specified if one of records of the result set is larger than the specified size.

### Auditing Properties

#### AUDIT_FILE_SIZE (Unit: byte)

##### Data Type

Unsigned Int

##### Default Value

100M

##### Attributes

Read-Write, Single Value

##### Range

[0, 2<sup>32</sup>-1]

##### Description

This property specifies the size of the binary audit log file in bytes. This property is used when AUDIT_OUTPUT_METHOD is 0. 

The value of this property can be changed using the ALTER SYSTEM statement, as shown below, while Altibase is running.

```
ALTER SYSTEM SET AUDIT_FILE_SIZE=10000;
```

However, if the server is in the process of auditing, the changed size applies to files that are created thereafter. For the immediate application of the changed value of this property, restart auditing with the ALTER SYSTEM STOP AUDIT and ALTER SYSTEM START AUDIT statement.

#### AUDIT_LOG_DIR

##### Data Type

String

##### Default Value

\$ALTIBASE_HOME/trc

##### Attributes

Read-Write, Multiple Value

##### Range

None

##### Description

This property specifies the directory in which the binary audit log file is created. This property is used when AUDIT_OUTPUT_METHOD is 0. 

The value of this property can be changed using the ALTER SYSTEM statement, as shown below, while Altibase is running.

```
ALTER SYSTEM SET AUDIT_LOG_DIR='/tmp';
```

However, if the server is in the process of auditing, the changed size applies to files that are created thereafter. For the immediate application of the changed value of this property, restart auditing with the ALTER SYSTEM STOP AUDIT and ALTER SYSTEM START AUDIT statement.

#### AUDIT_OUTPUT_METHOD

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Only, Single Value

##### Range

[0, 9]

##### Description

This property sets the file format for the audit log file. Altibase can store audit information in binary or syslog (syslog is only supported on Linux). 

If this property is set to the default value, audit logs are saved in the directory specified for AUDIT_LOG_DIR in binary format. If this property is set to a value between 1~9, logs are stacked in syslog.conf (or rsyslog.conf) using syslog. The syslog message order uses LOG_INFO priority from the syslog.conf file.

0: Stores binary files in the directory specified for AUDIT_LOG_DIR. 

1: Stores user facility in /var/log/messages. The file name can be edited at system configuration. 

2: Stores to local0 facility, according to user definition. 

3: Stores to local1 facility, according to user definition. 

4: Stores to local2 facility, according to user definition. 

5: Stores to local3 facility, according to user definition. 

6: Stores to local4 facility, according to user definition. 

7: Stores to local5 facility, according to user definition. 

8: Stores to local6 facility, according to user definition. 

9: stores to local7 facility, according to user definition.

#### AUDIT_TAG_NAME_IN_SYSLOG

##### Data Type

String

##### Default Value

AUDIT

##### Attributes

Read-Only, Single Value

##### Range

None

##### Description

This property uses the “AUDIT” tag as a delimiter for saving audit logs using syslog. 

### C/C++ External Procedure Agent Properties

#### EXTPROC_AGENT_CONNECT_TIMEOUT

##### Data Type

Unsigned Integer

##### Default Value

60 Seconds

##### Attributes

Read-Only, Single Value

##### Range

[5, 2<sup>32</sup>-1]

##### Description

This property specifies the maximum length of time in seconds during which Altibase attempts to connect to the external procedure agent when the user calls an external procedure. If the connection does not succeed within the time specified in this property, the call is terminated with the error message displaying that the external procedure call failed. Once a connection is made, external procedure calls are not affected by the value of this property.

#### EXTPROC_AGENT_CALL_RETRY_COUNT

##### Data Type

Unsigned Integer

##### Default Value

1

##### Attributes

Read-Write, Single Value

##### Range

[1, 10]

##### Description

When the user calls an external procedure, EXTPROC_AGENT_CALL_RETRY_COUNT specifies the number of times Altibase tries to reconnect to the external procedure agent. 

Altibase first needs to check whether the external procedure agent exists. The external procedure agent may have been timed out and terminated due to the value specified for the EXTPROC_AGENT_CONNECT_TIMEOUT property. In this case, EXTPROC_AGENT_CALL_RETRY_COUNT specifies the number of times Altibase tries to reconnect to the external procedure agent. 

The value of this property can be altered with the ALTER SYSTEM statement while Altibase is running.

#### EXTPROC_AGENT_IDLE_TIMEOUT

##### Data Type

Unsigned Integer

##### Default Value

300 Seconds

##### Attributes

Read-Only, Multiple Value

##### Range

[5, 2<sup>32</sup>-1]

##### Description

This property specifies the maximum length of time, in seconds, in which the external procedure agent process is to stand by in an idle state. If an external procedure call is made when the external procedure agent process is standing by in an idle state, response time is optimized, as the procedure is executed without connecting to the agent process. However, standby of the agent process in the absence of an external procedure call is a waste of resources; the extension of standby time is recommended only when external procedure calls are highly frequent.

#### EXTPROC_AGENT_SOCKET_FILEPATH

##### Data Type

String

##### Default Value

\$ALTIBASE_HOME/trc

##### Attributes

Read-Only, Single Value

##### Range

None

##### Description

This is a socket file's path created for Altibase server to connect with the external procedure agent. If the external procedure uses, the session creates a socket file with socket_sessionID when creating an external procedure agent. The socket file is automatically deleted when the session is colsed normally. And, be careful not to delete this file

### Account Security Properties

#### CASE_SENSITIVE_PASSWORD

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Write, Single Value

##### Range

[0, 1]

##### Description

This specifies whether or not the database is to distinguish between uppercase and lowercase letters in user passwords. The default value for this property is 0 (case-insensitive), which means that the database treats user passwords as uppercase letters.

- 0: Does not distinguish between uppercase and lowercase letters (case-insensitive).
- 1: Distinguishes between uppercase and lowercase letters (case sensitive); however, only if passwords are enclosed in quotation marks (") in the CREATE USER statement. Passwords which are not enclosed in quotation marks are treated as uppercase letters.

The value of this property can be changed using the ALTER SYSTEM statement while Altibase is running.

#### FAILED_LOGIN_ATTEMPTS

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Only, Single Value

##### Range

[0, 1000]

##### Description

If an attempt to log in fails more than number of times set in this property, the account cannot be logged in.

#### PASSWORD_LOCK_TIME

##### Data Type

Unsigned Int

##### Default Value

0

##### Attributes

Read-Only, Single Value

##### Range

[0, 3650]

##### Description

This specifies the date(unit: days) required to elapse for a locked account to become unlocked.

#### PASSWORD_LIFE_TIME

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Only, Single Value

##### Range

[0, 3650]

##### Description

This specifies the period of validity(unit: days) for the account password.

#### PASSWORD_GRACE_TIME

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Only, Single Value

##### Range

[0, 3650]

##### Description

This property specifies the grace period (unit: days) after the expiry date of the account password.

#### PASSWORD_REUSE_TIME

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Only, Single Value

##### Range

[0, 3650]

##### Description

This specifies the period of time(unit: days) needed to elapse for the reuse of identical passwords. Thus, identical passwords can be reused after the period of time specified for this option elapses.

#### PASSWORD_REUSE_MAX

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Only, Single Value

##### Range

[0, 1000]

##### Description

This specifies the number of times passwords can be altered for the reuse of identical passwords. Thus, identical passwords can be reused after they have been altered for the number of times specified by this option. 

#### PASSWORD_VERIFY_FUNCTION

##### Data Type

String

##### Default Value

""

##### Attributes

Read-Only, Single Value

##### Range

Maximum length : 40 bytes

##### Description

This specifies a user-defined CALLBACK function for verifying passwords.

### Altibase Sharding Properties

#### SHARD_ENABLE 

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Only, Single Value

##### Range

[0, 1]

##### Description

Set to shard node of Altibase sharding:

0: Disabled

1: Enabled

For other sharding properties, please refer to the *Sharding Manual*.

### Other Properties

#### ACCESS_LIST

##### Format

ACCESS_LIST = operation, address, mask

##### Range

- operation ::= [PERMIT\|DENY]  
  Indicates whether to allow or deny access by an IP packet that matches a validation rule.
  
- address  
  Indicates the IP address of the packet to validate. It can be in IPv4 or IPv6 address notation.
  
- mask  
  If the specified address is in IPv4 address notation, mask specifies that only part of the IP address of a packet, the subnet mask, is to be validated. 
  
  If the specified address is in IPv6 address notation, mask gives the length of prefix bits to be compared. An IPv6 address is matched if the specified mask bits of the specified address are equal to the specified mask bits of the originating address of an incoming IP packet.

##### Validation Rule

```
IF 
BITXOR(BITAND(IP_패킷,mask), BITAND(address,mask)) = 0
THEN  valid
ELSE  invalid
```

##### Description

This property can grant or deny an IP packet attempting to access to Altibase in accordance with an address. By inspecting the IP packet address based upon the specified inspection rules, it can be decided whether or not to allow access. If the IP packet address is corresponding as described in the operation, the access is permitted, but if not, the IP packet is neglected and the next list will be inspected. 

If multiple IP packet addresses are specified, the inspection is executed in the order delineated. If there is no address to be matched, the access is allowed. 

If the property value of ACCESS_LIST_FILE is described, an external file list defined in the ACCESS_LIST property can be used. The external file can use maximum 1024 lists, but 'ACCESS_LIST=' should be omitted and only the contents should be written out.

##### Example

Block packets with the IP address 192.168.1.55 and allow all other packets.

```
ACCESS_LIST = deny, 192.168.1.55, 255.255.255.255
```

Allow access to packets from the addresses 192.168.3.* and 219.211.253.*, and block all other packets.

```
ACCESS_LIST = permit, 192.168.3.0, 255.255.255.0
ACCESS_LIST = permit, 219.211.253.0, 255.255.255.0
ACCESS_LIST = deny ,0.0.0.0, 0.0.0.0
```

Block all Ipv4 and IPv6 address except for localhost.

```
ACCESS_LIST = deny, 0.0.0.0, 0.0.0.0
ACCESS_LIST = deny, ::1, 1
ACCESS_LIST = deny, fe80::, 1
```

Describe the IP address which will be inspected in the external file. Block all IP address except for IPv6 address starting with 192.168.3.* and fe80.

```
permit, 192.168.3.0, 255.255.255.0
permit, fe80::, 16
deny, 0.0.0.0, 0.0.0.0
deny, ::1, 1
deny, fe80::, 1
```

**ACCESS_LIST_FILE**

##### Data Type

String

##### Default Value

None

##### Attributes

Read-Only, Single Value

##### Range

None

##### Description

This property configures the file path when ACCESS_LIST references an external file path. If the file name and path is not precisely configured, the server will not drive. The absolute path should be specified for an external file path. Refer to the description section of the ACCESS_LIST property for the ACCESS_LIST format.

The list described in ACCESS_LIST property is used if this property is not used.

#### ADMIN_MODE

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Write, Single Value

##### Range

[0, 1]

##### Description

ADMIN_MODE limits the database connection to administrators only.

0: OFF

1: ON

When this property is set to 1, administrator mode is activated, and only the SYS and SYSTEM_ users can connect to the server using the SYSDBA option, and other users will be unable to establish a connection. 

This property can be changed using the ALTER SYSTEM statement while Altibase is running.

#### ARITHMETIC_OPERATION_MODE

##### Data Type

Unsigned Integer

##### Default Value

1

##### Attributes

Read-Write, Single Value

##### Range

[0, 1]

##### Description

This property sets the Altibase server to arithmetic operation mode. 

0: The server runs in arithmetic operation mode with precision as its priority. The server mainly uses FLOAT or NUMERIC data types to reduce errors from arithmetic operations. The processing speed can be slower than arithmetic operation mode with performance as its priority. 

1: The server runs in arithmetic operation mode with performance as its priority. The server mainly uses DOUBLE data types for arithmetic operations to enhance performance; the occurrence of errors is relatively higher

#### CHECK_MUTEX_DURATION_TIME_ENABLE

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

변경 가능, 단일 값

##### Range

[0, 1]

##### Description

This property specifies whether to check MUTEX_DURATION_TIME. 

This property can be changed using the ALTER SYSTEM statement while Altibase is running.

0: check disable

1: check enable

#### COERCE_HOST_VAR_IN_SELECT_LIST_TO_VARCHAR

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Only, Single Value

##### Range

[0, 32000]

##### Description

This property enables host variables to be used in the select target list without CAST operators. 

If this property is 1 or greater, the server treats host variables without CAST operators as VARCHAR data types, and the specified value in this property is used as the size (precision) of the VARCHAR data type. 

If this property is set to 0, using host variables without CAST operators will cause an error.

#### DEFAULT_DATE_FORMAT

##### Data Type

String

##### Default Value

DD-MON-RRRR

##### Attributes

Read-Only, Single Value

##### Range

None

##### Description

This property sets the default format of DATE type data table columns. If not specified otherwise when SQL statements are executed, DATE type data are input or output according to this setting. This type must specify the formats in which both dates and times are saved. It is also possible to use blanks within double quotation marks, such as "DD MON RRRR".

```
DEFAULT_DATE_FORMAT = YYYY/MM/DD
iSQL> select sysdate from dual;
SYSDATE
--------------
2008/06/16
1 row selected.
```

#### EXEC_DDL_DISABLE

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Write, Single Value

##### Range

[0, 1]

##### Description

Generally, after a database is initially created, DML statements are executed much more frequently than DDL statements. Because DDL statements change existing database schema, they must be executed with caution. 

The administrator can thus use this property to prevent the execution of DDL statements. When this property is set to 1, DDL statements cannot be executed while Altibase is running, whereas if it is set to 0, DDL statements can be executed. 

This property can be changed using the ALTER SYSTEM statement while Altibase is running

#### GROUP_CONCAT_PRECISION

##### Data Type

Unsigned Integer

##### Default Value

4000

##### Attributes

Read-Write, Single Value

##### Range

[0, 32000]

##### Description

This property specifies the size of the VARCHAR type that the GROUP_CONCAT function returns. 

This property can be modified using the ALTER SYSTEM statement while Altibase is running.

#### JOB_SCHEDULER_ENABLE 

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Write, Single Value

##### Range

[0, 1]

##### Description

This controls the operation of the job scheduler. The job scheduler does not operate if the value of the JOB_THREAD_COUNT property is set to 0, even if the value of this property is set to 1.

0: The job scheduler terminates the job

1: The job scheduler starts the job the run

The value of this property can be changed using the ALTER SYSTEM statement while Altibase is running.

#### JOB_THREAD_COUNT 

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Only, Single Value

##### Range

[0, 128]

##### Description

This property specifies the number of threads to be created at server startup for a JOB to run. If the value of this property is 0, threads are not created for the job scheduler.

#### JOB_THREAD_QUEUE_SIZE 

##### Data Type

Unsigned Integer

##### Default Value

64

##### Attributes

Read-Only, Single Value

##### Range

[64, 1024]

##### Description

This property specifies the number of queues to be created at server startup for a JOB to run. If the value of this property is large, a larger number of jobs can run in a given amount of time.

#### MSG_QUEUE_PERMISSION

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Only, Single Value

##### Range

[0, 1]

##### Description

This property sets the permission type of a message queue. The value of this property can be modified by the ALTER SYSTEM statement during ALTIBASE HDB operation

0: (rw-rw-rw 0666) - All users are allowed to read and write, but cannot perform an execution.

1: (rw-r-r 0644) - Only the system owner can read and write, but other users are only allowed to read.

#### PSM_CHAR_DEFAULT_PRECISION

##### Data Type

Unsigned Integer

##### Default Value

32767

##### Attributes

Read-Only, Single Value

##### Range

[1, 65534]

##### Description

In case that the size of CHAR type is unspecified in the stored procedures or functions, Altibase determines the specified values in the PSM_CHAR_DEFAULT_PRECISION property as the size of CHAR. 

#### PSM_IGNORE_NO_DATA_FOUND_ERROR

##### Data Type

Unsigned Integer

##### Default Value

0

##### Attributes

Read-Write, Single Value

##### Range

[0, 1]

##### Description

The NO_DATA_FOUND exception is one of the system defined exceptions provided by Altibase's PSM. This exception is raised when the "SELECT ~INTO" statement contained in PSM(stored procedures, functions, triggers) returns no result sets. With the PSM_IGNORE_NO_DATA_FOUND_ERROR property, the user can guard against this exception. 

* 0: When no result set is returned, the NO_DATA_FOUND exception is raised. 

* 1: When no result set is returned, the NO_DATA_FOUND exception is not raised. 

  This property can be changed using the ALTER SYSTEM statement while Altibase is running.

#### PSM_NCHAR_UTF16_DEFAULT_PRECISION

##### Data Type

Unsigned Integer

##### Default Value

16383

##### Attributes

Read-Only, Single Value

##### Range

[1, 32766]

##### Description

Altibase determines the values specified in the PSM_NCHAR_UTF16_DEFAULT_PRECISION property as the size of NCHAR in the case Altibase character set is UTF16, and the size of NCHAR type is unspecified in parameters or return values when creating stored procedures and functions.

#### PSM_NCHAR_UTF8_DEFAULT_PRECISION

##### Data Type

Unsigned Integer

##### Default Value

10921

##### Attributes

Read-Only, Single Value

##### Range

[1, 21843]

##### Description

In the case the Altibase character set is UTF8, and the NCHAR type size is unspecified in parameters or return values when creating the stored procedures or functions, Altibase determines the specified values in the PSM_CHAR_DEFAULT_PRECISION property as the size of NCHAR.

#### PSM_NVARCHAR_UTF16_DEFAULT_PRECISION

##### Data Type

Unsigned Integer

##### Default

16383

##### Attributes

Read-Only, Single Value

##### Range

[1, 32766]

##### Description

Altibase determines the specified values in the PSM_NCHAR_UTF16_DEFAULT_PRECISION property as the size of NVARCHAR in the case that Altibase character set is UTF16, and the size of NVARCHAR type is not specified in parameters or return values when creating the stored procedures and stored functions.

#### PSM_NVARCHAR_UTF8_DEFAULT_PRECISION

##### Data Type

Unsigned Integer

##### Default Value

10921

##### Attributes

Read-Only, Single Value

##### Range

[1, 21843]

##### Description

In the case the Altibase character set is UTF8 and the NCHAR type size is unspecified in parameters or return values when creating the stored procedures or functions, Altibase determines the specified values in the PSM_NVARCHAR_UTF8_DEFAULT_PRECISION property as the size of NVARCHAR.

#### PSM_PARAM_AND_RETURN_WITHOUT_PRECISION_ENABLE

##### Data Type

Unsigned Integer

#####  Default Value

1

##### Attributes

Read-Only, Single Value

##### Range

[0,1]

##### Description

The size of usable data varies depending on the value of this property if the scale of parameter is unspecified when creating the stored procedures or if the data size of parameters and return values is not specified in case of creating stored functions.

If the type of parameter or return values is CHAR, NCHAR, NVARCHAR or VARCHAR, and the property value is 1, the size of data type is determined by the values specified in the following properties; however, if the value is set to 0, the size of data type would be 1.

- PSM_CHAR_DEFAULT_PRECISION
- PSM_NCHAR_UTF8_DEFAULT_PRECISION
- PSM_NCHAR_UTF16_DEFAULT_PRECISION
- PSM_NVARCHAR_UTF8_DEFAULT_PRECISION
- PSM_NVARCHAR_UTF16_DEFAULT_PRECISION
- PSM_PARAM_AND_RETURN_WITHOUT_PRECISION_ENABLE
- PSM_VARCHAR_DEFAULT_PRECISION

#### PSM_VARCHAR_DEFAULT_PRECISION

##### Data Type

Unsigned Integer

##### Default Value

32767

##### Attributes

Read-Only, Single Value

##### Range

[1, 65534]

##### Description

In case that the size of VARCHAR type is unspecified in the stored procedures or functions, Altibase determines the specified values in the PSM_VARCHAR_DEFAULT_PRECISION property as the size of VARCHAR.

#### QUERY_STACK_SIZE (Unit: count)

##### Data Type

Unsigned Integer

##### Default Value

1024

##### Range

Read-Write, Single Value

##### Range

[8, 65536]

##### Description

This property specifies the size of the stack internally used in the system to process query operations such as comparisons and other operations. 

When complicated calculations or stored procedures are used, a stack overflow error may occur. In such cases, the property must be changed to a bigger value. 

This parameter must be set according to the application environment. If it is set to a value higher than necessary, memory space will be wasted, so this parameter must be set carefully. 

This property can be set in the altibase.properties file, and can be changed using the ALTER SYSTEM or ALTER SESSION statements. 

This property can be changed using the ALTER SESSION statement as follows: ALTER SESSION SET STACK SIZE = n;

#### RECURSION_LEVEL_MAXIMUM

##### Data Type

Unsigned Integer

##### Default Value

1000

##### Attributes

Read-Write, Single Value

##### Range

[5, 2<sup>32</sup>-1]

##### Description

This property repeatedly executes recursive queries for specified number of times(level). 

The value of this property can be modified through ALTHER SESSION statement during the Altibase operation.

#### REMOTE_SYSDBA_ENABLE

##### Data Type

Unsigned Integer

##### Default Value

1

##### Attributes

Read-Write, Single Value

##### Range

[0, 1]

##### Description

This property specifies whether the SYS user can access the database with SYSDBA privileges from a remote location. Its value can be changed using the ALTER SYSTEM statement.

0: Deny remote database access with SYSDBA privileges

1: Allow remote database access with SYSDBA privileges (default)

#### SELECT_HEADER_DISPLAY

##### Data Type

Unsigned Integer

##### Default Value

1

##### Attributes

Read-Write, Single Value

##### Range

[0, 1]

##### Description

When the results of a SELECT query are output over iSQL, this system property determines whether only the column names are output, or whether the table names are output along with the column names. 

This property can be set in the altibase.properties file, and can be changed using the ALTER SYSTEM or ALTER SESSION statements. 

If this parameter is set to 0, the table names are displayed along with the column names when the results of SQL statements are output using iSQL

#### SYS_CONNECT_BY_PATH_PRECISION

##### Data Type

Unsigned Integer

##### Default Value

4000

##### Attributes

Read-Write, Single Value

##### Range

[0, 32000]

##### Description

This property specifies the size of the VARCHAR type that the SYS_CONNECT_BY_PATH function returns.

This property can be modified using the ALTER SYSTEM statement while Altibase is running.

