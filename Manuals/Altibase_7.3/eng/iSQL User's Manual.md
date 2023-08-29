iSQL User’s Manual
==================

#### Altibase 7.3

Altibase® Tools & Utilities

<br><br><br><br><br><br>
<!-- PDF 변환을 위한 여백입니다. --> 







































<!-- PDF 변환을 위한 여백입니다. --> 

<div align="left">
    <img src="media/common/e5cfb3761673686d093a3b00c062fe7a.png">
</div>

<br><br><!-- PDF 변환을 위한 여백입니다. --> 





























<!-- PDF 변환을 위한 여백입니다. --> 

<pre>
Altibase Tools & Utilities iSQL User's Manual
Release 7.3
Copyright ⓒ 2001~2023 Altibase Corp. All Rights Reserved.<br>
This manual contains proprietary information of Altibase® Corporation; it is provided under a license agreement containing restrictions on use and disclosure and is also protected by copyright patent and other intellectual property law. Reverse engineering of the
software is prohibited.<br>
All trademarks, registered or otherwise, are the property of their respective owners.<br>
<b>Altibase Corp</b>
10F, Daerung PostTower II,
306, Digital-ro, Guro-gu, Seoul 08378, Korea
Telephone : +82-2-2082-1000 
Fax       : +82-2-2082-1099
Customer Service Portal : <a href='http://support.altibase.com/en/'>http://support.altibase.com/en/</a>
Homepage                : <a href='http://www.altibase.com'>http://www.altibase.com</a></pre>


<br>

# Table Of Contents

- [Preface](#preface)
  - [About This Manual](#about-this-manual)
- [1. Using iSQL](#1-using-iSQL)
  - [iSQL Overview](#iSQL-overview)
  - [Setting up iSQL](#setting-up-iSQL)
  - [iSQL Command-Line Options](#iSQL-command-line-options)
  - [iSQL Commands](#iSQL-commands)
  - [iSQL Environment Variables](#iSQL-environment-variables)
  - [Personalizing iSQL](#personalizing-iSQL)
- [2. Examples of iSQL in Use](#2-examples-of-iSQL-in-use)
  - [Logging In to iSQL](#logging-in-to-iSQL)
  - [Starting Up and Shutting Down Altibase](#starting-up-and-shutting-down-altibase)
  - [Connecting and Disconnecting](#connecting-and-disconnecting)
  - [Retrieving Information Related to the Database and Database Objects](#retrieving-information-related-to-the-database-and-database-objects)
  - [Controlling Transactions](#controlling-transactions)
  - [File Management](#file-management)
  - [Formatting SELECT Query Results](#formatting-select-query-results)
  - [Setting Output Options](#setting-output-options)
  - [Viewing iSQL Display Settings](#viewing-iSQL-display-settings)
  - [Host Variables](#host-variables)
  - [Executing Prepared SQL Statements](#executing-prepared-sql-statements)
  - [Creating, Executing, and Dropping Stored Procedures](#creating-executing-and-dropping-stored-procedures)
  - [Creating, Executing ,and Dropping Functions](#creating-executing-and-dropping-functions)
  - [Convenient User Functions](#convenient-user-functions)
  - [Using National Character Sets](#using-national-character-sets)d



Preface
====

### About This Manual

This manual describes how to use iSQL, a tool for connecting to a database and viewing and controlling database and server information.

#### Audience

This manual has been prepared for the following users of Altibase:

-   Database administrators
-   Performance administrators
-   Database users
-   Application developers
-   Technical Supporters

It is recommended for those reading this manual possess the following background knowledge:

-   Basic knowledge in the use of computers, operating systems, and operating system utilities
-   Experience in using relational database and an understanding of database concepts
-   Computer programming experience
-   Experience in database server management, operating system management, or network administration
-   Knowledge related to the storage, management and processing of data in distributed environments

#### Organization

This manual is organized as follows:

-   Chapter 1: Using iSQL  
    This chapter provides an overview of iSQL and explains the commands and how to use iSQL.

-   Chapter 2: Examples of iSQL Usage  
    This chapter provides in-depth examples of each of the commands provided with iSQL.

#### Documentation Conventions

This section describes the conventions used in this manual. Understanding these conventions will make it easier to find information in this manual and in the other manuals in the series. 

There are two sets of conventions:

-   Syntax diagram convetions
-   Sample code conventions

##### Syntax Diagram Conventions

This manual describes command syntax using diagrams composed of the following elements:

| Elements                                                     | Meaning                                                      |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [![image1](https://github.com/ALTIBASE/Documents/raw/master/Manuals/Altibase_7.1/eng/media/SQL/image1.gif)](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/eng/media/SQL/image1.gif) | Indicates the start of a command. If a syntactic element starts with an arrow, it is not a complete command. |
| [![image2](https://github.com/ALTIBASE/Documents/raw/master/Manuals/Altibase_7.1/eng/media/SQL/image2.gif)](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/eng/media/SQL/image2.gif) | Indicates that the command continues to the next line. If a syntactic element ends with this symbol, it is not a complete command. |
| [![image3](https://github.com/ALTIBASE/Documents/raw/master/Manuals/Altibase_7.1/eng/media/SQL/image3.gif)](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/eng/media/SQL/image3.gif) | Indicates taht the command continues from the previous line. If a syntactic element starts witht his symbol, it is not a complete command. |
| [![image4](https://github.com/ALTIBASE/Documents/raw/master/Manuals/Altibase_7.1/eng/media/SQL/image4.gif)](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/eng/media/SQL/image4.gif) | Indicates the end of a statement.                            |
| [![image5](https://github.com/ALTIBASE/Documents/raw/master/Manuals/Altibase_7.1/eng/media/SQL/image5.gif)](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/eng/media/SQL/image5.gif) | Indicates a manatory element.                                |
| [![image6](https://github.com/ALTIBASE/Documents/raw/master/Manuals/Altibase_7.1/eng/media/SQL/image6.gif)](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/eng/media/SQL/image6.gif) | Indicates an optional element.                               |
| [![image7](https://github.com/ALTIBASE/Documents/raw/master/Manuals/Altibase_7.1/eng/media/SQL/image7.gif)](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/eng/media/SQL/image7.gif) | Indicates a mandatory element comprised of options. One, and only one, option must be specified. |
| [![image8](https://github.com/ALTIBASE/Documents/raw/master/Manuals/Altibase_7.1/eng/media/SQL/image8.gif)](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/eng/media/SQL/image8.gif) | Indicates an optional element comprised of options.          |
| [![image9](https://github.com/ALTIBASE/Documents/raw/master/Manuals/Altibase_7.1/eng/media/SQL/image9.gif)](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/eng/media/SQL/image9.gif) | Indicates an optional element in which multiple elements may be specified. A comman must precede all but the first element. |

##### Sample Code Conventions

The code examples explain SQL statements, stored procedures, iSQL statements, and other command line syntax.

The following table describes the printing conventions used in the code examples.

| Rules            | Meaning                                                      | Example                                                      |
| ---------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ ]              | Indicates an optional item                                   | VARCHAR [(*size*)] [[FIXED \|] VARIABLE]                     |
| { }              | Indicates a mandatory field for which one or more items must be selected. | { ENABLE \| DISABLE \| COMPILE }                             |
| \|               | A delimiter between optional or mandatory arguments.         | { ENABLE \| DISABLE \| COMPILE } [ ENABLE \| DISABLE \| COMPILE ] |
| . . .            | Indicates that the previous argument is repeated, or that sample code has been omitted. | SQL\> SELECT ename FROM employee;<br/> ENAME<br/>  -----------------------<br/> SWNO<br/>  HJNO<br/>  HSCHOI<br/>  .<br/> .<br/> .<br/> 20 rows selected. |
| Other Symbols    | Symbols other than those shown above are part of the actual code. | EXEC :p1 := 1; acc NUMBER(11,2)                              |
| Italics          | Statement elements in italics indicate variables and special values specified by the user. | SELECT \* FROM *table_name*; <br/>CONNECT *userID*/*password*; |
| Lower case words | Indicate program elements set by the user, such as table names, column names, file names, etc. | SELECT ename FROM employee;                                  |
| Upper case words | Keywords and all elements provided by the system appear in upper case. | DESC SYSTEM_.SYS_INDICES_;                                   |

#### Related Documentations

For more detailed information, please refer to the following documents.

-   Installation Guide

-   Getting Started Guide

-   Administrator’s Manual

-   Replication Manual

-   SQL Reference

-   Stored Procedures Manual

-   Error Message Reference

#### Altibase Welcomes Your Comments and Feedbacks

Please let us know what you like or dislike about our manuals. To help us with better future versions of our manuals, please tell us if there is any corrections or classifications that you would find useful.

Include the following information:

- The name and version of the manual that you are using
- Any comments about the manual
- Your name, address, and phone number

If you need immediate assistance regarding any errors, omissions, and other technical issues, please contact [Altibase's Support Portal](http://support.altibase.com/en/).

Thank you. We always welcome your feedbacks and suggestions.





# 1. Using iSQL

### iSQL Overview

iSQL is an user's tool for accessing an Altibase and retrieving and modifying stored data using SQL statements and a number of additional commands. 

#### iSQL Main Functionality

-   Altibase Startup and Shutdown  
    iSQL allows users to perform database management tasks, such as starting up and shutting down the server, and execute SQL statements using the same command prompt.
    
-   Database Connection & Disconnection   
    After Altibase starts up, users can use various user names to connect to and disconnect from the database.
    
-   Database Object Information Inquiry   
    iSQL allows users to use SQL statements to query all database object information, and supports convenient commands for inquiring about main objects.
    
-   Database Management via SQL Statements   
    Because iSQL can be used to execute any kind of SQL statement, users can control transactions and alter databases quickly and conveniently.
    
-   Functions to Improve User Convenience   
    The above tasks can be easily and conveniently accomplished using the file management and editing functions, the ability to execute shell commands over iSQL, and the HISTORY function.



### Setting up iSQL

In order for iSQL to access a server, the following information is necessary.

-   ALTIBASE_HOME  
    A path to a server or client installation

-   server_name  
    The name (or IP address) of a computer on which Altibase Server is running

-   port_no  
    The port number used when connecting via TCP, IPC, or IPCDA

-   user_id  
    A User ID registered in the database

-   password  
    The password corresponding to the User ID

-   NLS_USE  
    The character set with which to display retrieved data to the user

ALTIBASE_HOME can only be set using an environment variable, while the other settings may be made using command-line options. (For more information, please refer to iSQL Command-Line Options.) 

ALTIBASE_HOME environment variable must be set in order to use iSQL. Although it is automatically configured when the server is installed in general, but the user should directly configure since there might be a chance of conflict with the environment variables in the server. 

port_no and NLS_USE can be set using the environment variables or the server settings file (altibase.properties). If these settings are made via all three methods, they will take priority as follows, in descending order: 

1.  command-line options 
2.  environment variables (ALTIBASE_PORT_NO, ALTIBASE_NLS_USE) 
3.  server settings file (altibase.properties)

Therefore, when it is desired to connect using options other than those that have been previously set, the command-line options can be used, so that it is not necessary to change the settings in the server setting file or the environment variables.

If any options have not been set, when iSQL is executed for the first time, the user will be prompted to enter the corresponding variables. At this time, it is essential to enter values that are valid and follow the proper format, otherwise iSQL may not run properly. 

However, if the NLS_USE option in particular has not been set, no command prompt will appear at the time of execution. Instead, US7ASCII will be used, and a connection attempt will be made. In this case, if the character set of the database is not US7ASCII, the application will not execute properly, or some of the user’s data may become corrupted. Thus it is paramount that NLS_USE be set to a suitable value for the usage environment. 

In order to ensure stable iSQL operation, we recommend that the following environment variables be set: • ALTIBASE

-   ALTIBASE_HOME : the path to a server or client installation 
-   ALTIBASE_PORT_NO : the port number to use to connect to the server 
-   ALTIBASE_NLS_USE : the character set to use to display retrieved data to the user 
-   PATH : the path containing the executable file, which must equal $ALTIBASE_HOME/bin



### iSQL Command-Line Options

The Altibase server must be started before iSQL is executed. The following options are case-insensitive.

```
isql
[-H]
[-S server_name]
[-PORT port_no]
[-U user_id] [-P password] [/NOLOG]
[-SYSDBA]
[-UNIXDOMAIN-FILEPATH filepath]
[-IPC-FILEPATH filepath]
[-SILENT]
[-F infile_name [param1 [param2]...]] [-O outfile_name] [-NLS_USE nls_name]
[-NLS_NCHAR_LITERAL_REPLACE 0|1]
[-prefer_ipv6] [-TIME_ZONE timezone]
[-ssl_ca CA_file_path | -ssl_capath CA_dir_path]
[-ssl_cert certificate_file_path]
[-ssl_key key_file_path]
[-ssl_verify]
[-ssl_cipher cipher_list]
```



- -S *server_name*
  This option specifies the name (or IP address) of a computer on which Altibase Server is running. 
  
  If connection is attempted while the ISQL CONNECTION environment variable is set to IPC or UNIX, and the remote server is specified for this option, iSQL ignores the ISQL CONNECTION specification and connects to the remote server via TCP, and outputs a warning message that the ISQL CONNECTION specification has been ignored. It can be a host name, an IPv4 address, or an IPv6 address. An IPv6 address must be enclosed by a left square bracket([) and a right square bracket(]). For example, in the case of localhost (meaning this computer), localhost can be specified as the host name, 127.0.0.1 as the IPv4 address, or [::1] as the IPv6 address.
  
  For more information about the IPv6 address notation, please refer to the *Altibase Administrator's Manual.*
  
- -PORT *port_no*
  This option specifies the port number for connecting via TCP, IPC or IPCDA. However, when connecting in a Unix environment via IPC, this option must not be specified. 
  
  After a warning message is output, connection to the server is made. To connect via TCP, first set 'ISQL_CONNECTION=TCP' on the client and then enter the PORT_NO. If the environment variable ISQL_CONNECTION is not set to IPC and the -PORT option is omitted, ALTIBASE_PORT_NO and PORT_NO property is referred in sequence. However, the prompt for port number input is output if all is not specified.
  
- -U *user_id*
  This option specifies a user ID registered in the database.
  
- -P *password*
  This option specifies the password corresponding to the user ID.
  
- /NOLOG
  This executes iSQL without connecting to the database.
  
- -SYSDBA
  This allows the SYS user to execute iSQL in SYSDBA mode. If the server has not yet started, iSQL connects as an idle instance and allows the user to start the server. 
  
- -UNIXDOMAIN-FILEPATH *filepath*  
  When a server and client connect using a Unix domain socket in a Unix environment (ISQL_CONNECTION=UNIX), the connection will fail if the server and client have different values for ALTIBASE_HOME and also have different Unix domain socket paths. In this case, if the server and client use corresponding files (e.g. ALTIBASE_HOME/trc/cm-unix), Unix domain communication is possible.
  
- -IPC-FILEPATH *filepath*  
  When the client and the server connect via IPC(ISQL_CONNECTION=IPC) in a Unix environment, if ALTIBASE_HOME is set differently on them, they will not be able to connect because they have different socket paths. In this case, Unix domain communication can be achived using the ALTIBASE_HOME/trc/cm-ipc file, and then information about shared memory can be retrieved. However, this option can be omitted if ALTIBASE_IPC_FILEPATH is set.
  
- -IPCDA-FILEPATH *filepath*  
  If ALTIBASE_HOME is different from each other when attempting to connect the client and server via IPCDA (ISQL_CONNECTION=IPCDA), the connection cannot be made due to different socket paths Howeve, if ALTIBASE_HOME/trc/cm-ipcda file is used, the Unix domain communication is enabled to bring the information of shared memory. However, this option can be omitted if IPCDA_FILEPATH of environment variables is specified.
  
- -F infile_name [*param1 [param2]...*]  
  This command option specifies a script file to be executed immediately after iSQL is launched. Use double quotation marks if the file name contains special characters or spaces.  
  Ex) -F \\" file name\\"  
  This command also can specify a paramater value which will be substituted for a substitution variable in the script file. Refer to the 'Passing parameters through START command' for more information regarding the substitution variables.
  
- -O *outfile_name*
  This command option specifies a file in which to store the results of the excuted iSQL commands. This file will be created in the current directory. If the file already exists, it will be overwritten. 
  
  Use double quotation marks if the file name contains special characters or spaces.  
  Ex) -O \\" file name\\"
  
- -H
  This option outputs help information for iSQL execution.
  
- -SILENT s
  This option turns on silent mode. If silent mode is on, noncritical messages, such as the copyright notice, etc. will not be displayed.
  
- -NLS_USE Character set to display to user when searching data.
  This specifies the encoding of the terminal running iSQL. If omitted, the environment variable ALTIBASE_NLS_USE will be referred to, followed by altibase.properties. If not set, the default charset (US7ASCII) is used.
  
  - US7ASCII  
  - KO16KSC5601  
  - MS949  
  - BIG5  
  - GB231280  
  - MS936  
  - UTF8  
  - SHIFTJIS  
  - MS932  
  
- EUCJP-NLS_NCHAR_LITERAL_REPLACE  
  0 : convert all strings to the database character set without checking for the "N" character.  
  1 : do not convert strings that are preceded by the "N" character to the database character set
  
- -prefer_ipv6
  This option determines the IP address to be connected first when a host name is given for the -s option.  
  If this option is specified and a host name is given for the -s option, this means that resolving the host name to the IPv6 address is prefered. If this option is omitted, iSQL connects to the IPv4 address by default. If it fails to connect to the prefered IP version address, an attempt is made to connect using the other IP version address.  
  For example, when localhost is given for the -s option and this option is specified, iSQL first tries to connect to the [::1] IPv6 address. If this attempt fails, iSQL proceeds to connect to the 127.0.0.1 IPv4 address.
  
- -TIME_ZONE *timezone*  
  This option sets the time zone of the client. If DB_TZ is specified for this option, the time zone is defaulted to that of the database server. Time zone names like Asia/Seoul, abbreviations such as KST and UTC offset values as +09:00 are valid for specification.  
  If this option is omitted, the time zone set for the ALTIBASE_TIME_ZONE environment variable is defaulted to the time zone of the client; on omission of the environment variable, the time zone is defaulted to that of the database server.
  
- -ssl_ca *CA_file_path*  
  This specifies the location of the certification authority (CA) certificate in which the public key of the Altibase server to be connected to is incorporated.
  
- -ssl_capath *CA_dir_path*  
  This specifies the directory under which the certification authority (CA) certificate in which the public key of the Altibase server to be connected is incorporated.
  
- -ssl_cert *certificate_file_path*  
  This specifies the location of the client authentication file.
  
- -ssl_key *key_file_path*  
  This specifies the location of the client private key file.
  
- -ssl_verify
  This verifies the certificate the client receives from the server.
  
- -ssl_cipher *cipher_list*  
  This specifies a cipher list for SSL encryption. Please refer to the SSL_CIPHER_LIST property in the *General Reference.* 

If any of the -S, -U, or -P options are missing from the above command, the user will be prompted to input the option values.



### iSQL Commands

When iSQL is started, an iSQL command prompt will appear, and when iSQL commands are entered, the results of execution will be displayed. The iSQL commands are described individually in the following table.

<TABLE>
    <TR>
        <TH>Category</TH><TH>Type</TH><TH>Command</TH><TH>Description</TH>
    </TR>
    <TR>
        <TD rowspan="3">iSQL startup
and shutdown</TD><TD>Startup</TD> <TD>$ isql [option]</TD> <TD>If you execute this command in a shell,
iSQL will start up. For information on
the available options, please refer to the
iSQL Command-Line Options section.</TD>
    </TR>
     <TR>
        <TD>Prompt</TD> <TD>iSQL></TD> <TD>Type a command at the iSQL prompt
and press the ENTER key.</TD>
    </TR>
     <TR>
        <TD>Shutdown</TD> <TD>EXIT;<BR>QUIT;</TD> <TD>Used to shut down iSQL.</TD>
    </TR>
     <TR>
        <TD rowspan="2">Altibase
startup and
shutdown</TD><TD>Altibase
Startup</TD> <TD>STARTUP</TD> <TD>Use the PRE-PROCESS, PROCESS,
CONTROL, META, or SERVICE option to start Altibase up to the corresponding stage.</TD>
    </TR>
     <TR>
        <TD>Altibase
Shutdown</TD> <TD>SHUTDOWN</TD> <TD>Use one of the NORMAL, IMMEDIATE, or ABORT options to shut down
Altibase.</TD>
    </TR>
    <TR>
        <TD rowspan="2">Database
connection
and disconnection</TD><TD>Access the
server as another user</TD><TD>CONNECT [logon] [nls] [AS sysdba];<BR>
logon:user1/pass1 nls: NLS=character_set
</TD><TD>This command allows access to the database as user1 with password pass1
after having already accessed the database as another user in iSQL. If CONNECT is successful, the information
related to the previous session is
cleared.The AS clause allows the SYS
user to access the server in sysdba manager mode. Only one user is allowed to
connect as sysdba at a time.
The nls option specifies the character set.
For detailed information on character
sets, please refer to the iSQL Command-Line Options: -NLS_USE option.
</TD>
     </TR>
     <TR>
         <TD>Terminate a
connection</TD><TD>DISCONNECT;</TD><TD>Ends the current session and terminates
the connection with the server.</TD>
     </TR>
     <TR>
         <TD rowspan="4">Database object information inquiry</TD><TD>Display performance view
list </TD><TD>ELECT * FROM V$TAB;</TD><TD>Displays the list of all of the performance views provided by the system. This command is available only in
iSQL.</TD>
     </TR>
     <TR>
         <TD>Display table
list</TD><TD>SELECT * FROM TAB;</TD><TD>Displays the list of currently created tables. This command is only available in
iSQL.</TD>
     </TR>
     <TR>
         <TD>Display table
list</TD><TD>DESC samp;</TD><TD>Lists the column definitions for the table
samp</TD>
     </TR>
     <TR>
         <TD>Display sequence Information</TD><TD>SELECT * FROM SEQ;</TD><TD>If you accessed the server with the SYS
account, information on all sequences is
displayed.If you accessed the server as
another user, only the information on the
sequences generated by that user will be
displayed. This command is available
only in iSQL.</TD>
     </TR>
     <TR>
         <TD rowspan="11">File management</TD><TD rowspan="2">Saving results
to a file</TD><TD>SPOOL filename;</TD><TD>Starts writing the results of executed
command in iSQL to the file file_name. </TD>
     </TR>
     <TR>
        <TD>SPOOL OFF;</TD><TD>Stops spooling.</TD>
     </TR>
     <TR>
         <TD rowspan="3">SQL script
execution</TD><TD>START file_name;</TD><TD>Reads a script file and executes the SQL
statements in sequence.</TD>
     </TR>
     <TR>
         <TD>@ file_name;</TD><TD>Performs a function similar to that of
startup when executed via an iSQL
prompt.</TD>
     </TR>
     <TR>
         <TD>@@ file_name;</TD><TD>When used in a script, this command
executes the file file_name in the same
directory as the calling script. </TD>
     </TR>
     <TR>
         <TD>Save SQL statement to file</TD><TD>SAVE abc.sql;</TD><TD>Saves the last of the commands currently
in the iSQL buffer to a file.</TD>
     </TR>
     <TR>
         <TD>Load SQL
statement</TD><TD>LOAD abc.sql;</TD><TD>Loads the first of the commands saved in
a file at the end of the command buffer.</TD>
     </TR>
     <TR>
         <TD>Save DML
statements to
file</TD><TD>SET QUERYLOGGING ON;<BR>SET QUERYLOGGING OFF;
</TD><TD>This writes executed DML statements,
such as INSERT, UPDATE, DELETE
and MOVE, in
$ALTIBASE_HOME/trc/isql_query.log. </TD>
     </TR>
     <TR>
         <TD ROWSPAN="3">Edit query
statements </TD><TD>ED[IT]</TD><TD>This command edits the most recently
executed query.</TD>
     </TR>
     <TR>
         <TD>ED[IT] filename[.sql]</TD><TD>This command edits existing files or new
files.</TD>
     </TR>
     <TR>
         <TD>2ED[IT] or 2 ED[IT]</TD><TD>This edits the query statements with the
number 2 in the history list.</TD>
     </TR>
      <TR>
     <TD ROWSPAN="41">Control output
option</TD><TD ROWSPAN="11">Format SELECT result
column</TD><TD>SET LINESIZE 100;</TD><TD>Sets the length of a display line for outputting the result of a SELECT query.
Must be between 10 and 32767 inclusive.<BR>Default: 80</TD>
     </TR>
     <TR>
         <TD>SET LOBSIZE 10;</TD><TD>Sets the number of characters to display
when a CLOB column is output. <BR>Default: 80</TD>
     </TR>
     <TR>
         <TD>SET LOBOFFSET 3;</TD><TD>Sets the number of characters by which
to offset the display when a CLOB column is output. <BR>Default: 0
</TD>
     </TR>
     <TR>
         <TD>SET FEED[BACK] ON;<BR>SET FEED[BACK] OFF;<BR>SET FEED[BACK] n;</TD><TD>Determines whether to output the number of rows in a query result.</TD>
     </TR>
     <TR>
         <TD>SET PAGESIZE 10;</TD> <TD>Sets how many records of a SELECT
query result are output at one time.
When set to 0, all resultant records are
output.<BR>Default: 0</TD>
     </TR>
     <TR>
         <TD>SET HEADING ON;<BR>SET HEADING OFF;</TD> <TD>Sets whether to output the header of a
SELECT result<BR>Default: ON</TD>
     </TR>
     <TR>
         <TD>SET COLSIZE N;</TD> <TD>Sets the number of characters to output
when CHAR or VARCHAR type columns are output as a SELECT query
result.</TD>
     </TR>
     <TR>
         <TD>SET NUM[WIDTH] N;</TD> <TD>Sets the number of characters to output
when data of NUMERIC, DECIMAL,
NUMBER, FLOAT type columns are
output as a SELECT query result.<BR>Default: 11</TD>
     </TR>
     <TR>
         <TD>CL[EAR] COL[UMNS]</TD> <TD>This command releases the column format which has been specified with the
COLUMN.</TD>
     </TR>
     <TR>
         <TD>COL[UMN] [{column | expr} [option]]</TD> <TD>This command verifies and configures
the display format for a SELECT target
column.</TD>
     </TR>
     <TR>
         <TD>SET NUMF[ORMAT] format;</TD><TD>This command sets the display format of
SELECT results of NUMERIC, DECIMAL, NUMBER, and FLOAT type.</TD>
     </TR>
     <TR>
         <TD>Show SQL
statement execution time</TD><TD>SET TIMING ON;<BR>SET TIMING OFF;</TD><TD>Sets whether to output the amount of
time taken to execute a SQL command.<BR>Default: OFF</TD>
     </TR>
     <TR>
         <TD>Set the SQL
statement execution time
units for output</TD><TD>SET TIMESCALE SEC;<BR>SET TIMESCALE MILSEC;<BR>SET TIMESCALE MICSEC;<BR>SET TIMESCALE NANSEC;</TD><TD>Sets the unit of time for executing SQL
statements as seconds, milliseconds, microseconds or nanoseconds.</TD>
     </TR>
     <TR>
         <TD>Show/hide
CHECK constraint information</TD><TD>SET CHKCONSTRAINTS ON;<BR>Sets whether to output CHECK constraint output including information
when displaying the table structure(using
DESC).<BR>Default: OFF</TD>
     </TR>
     <TR>
         <TD>Show/hide
foreign key
information</TD><TD>SET FOREIGNKEYS ON;<BR>SET FOREIGNKEYS OFF;</TD><TD>Determines whether to include foreign
key information in the output when displaying the table structure (using DESC).<BR>Default: OFF</TD>
     </TR>
     <TR>
         <TD>Show/hide
partition information</TD><TD>SET PARTITIONS ON;<BR>SET PARTITIONS OFF;</TD><TD>Determines whether to include partition
information in the output when displaying the table structure (using DESC).<BR>Default: OFF</TD>
     </TR>
     <TR>
         <TD>Show/hide
script execution result</TD><TD>SET TERM ON;<BR>SET TERM OFF;</TD><TD>Determines whether to display the results
of execution of a script file on the screen.<BR>Default: ON</TD>
     </TR>
     <TR>
         <TD>Show/hide
script commands</TD><TD>SET ECHO ON;<BR>SET ECHO OFF;</TD><TD>Option to output the commands in the script file executed by @.<BR>Default : ON </TD>
     </TR>
     <TR>
         <TD>Replace Substitution Variable</TD><TD>SET DEFINE ON;<BR>SET DEFINE OFF;</TD><TD>This command specifies whether or not
to replace substitution variables with
parameter values inserted by a user when
executing a script file containing substitution variables.<BR>Default: OFF</TD>
     </TR>
     <TR>
         <TD>Display contents before/after replacing substitution variable</TD><TD>SET VERIFY ON;<BR>SET VERIFY OFF;</TD><TD>This command specifies whether or not
to display SQL statements before and
after the substitution variables are replaced with the parameter values
when executing a script file containing
substitution variables.<BR>Default: ON</TD>
     </TR>
     <TR>
         <TD>Output
executionplan
tree</TD><TD>ALTER SESSION SET EXPLAIN PLAN = ON;<BR>ALTER SESSION SET EXPLAIN PLAN = ONLY;<BR>ALTER SESSION SET EXPLAIN PLAN = OFF;</TD><TD>Determines whether to output an execution plan for a SELECT statement.<BR>Default: OFF</TD>
     </TR>
     <TR>
         <TD>SELECT result output
direction</TD><TD>SET VERTICAL ON;<BR>SET VERTICAL OFF;</TD><TD>Displays SELECT results vertically
when set to ON.<BR>Default: OFF</TD>
     </TR>
     <TR>
         <TD ROWSPAN="19">Show value of
iSQL display
settings </TD><TD>SHOW LINESIZE</TD><TD>Displays the current LINESIZE value.</TD>
     </TR>
     <TR>
         <TD>SHOW COLSIZE</TD><TD>Displays the current COLSIZE value.</TD>
     </TR>
     <TR>
         <TD>SHOW LOBOFFSET</TD><TD>Displays the current LOBOFFSET value.</TD>
     </TR>
     <TR>
         <TD>SHOW LOBSIZE</TD><TD>Displays the current LOBSIZE value.</TD>
     </TR>
     <TR>
         <TD>SHOW PAGESIZE</TD><TD>Displays the current PAGESIZE value.</TD>
     </TR>
     <TR>
         <TD>SHOW PLANCOMMIT</TD><TD>Shows whether PLANCOMMIT is ON
or OFF.</TD>
     </TR>
     <TR>
         <TD>SHOW QUERYLOGGING</TD><TD>DML Shows whether DML statements wil be
written to
ALTIBASE_HOME/trc/isql_query.log
when executed.</TD>
     </TR>
     <TR>
         <TD>SHOW FEEDBACK</TD><TD>Shows the current FEEDBACK value.</TD>
     </TR>
     <TR>
         <TD>SHOW HEADING</TD><TD>Shows the current HEADING setting.</TD>
     </TR>
     <TR>
         <TD>SHOW TERM</TD><TD>Shows the current TERM setting.</TD>
     </TR>
     <TR>
         <TD>SHOW ECHO</TD><TD>Shows the current ECHO setting.</TD>
     </TR>
     <TR>
         <TD>SHOW TIMING</TD><TD>Shows the current TIMING setting.</TD>
     </TR>
     <TR>
         <TD>SHOW TIMESCLAE	</TD><TD>This shows the current time units for the
execution of SQL statements.</TD>
     </TR>
     <TR>
         <TD>SHOW USER</TD><TD>Shows the current user.</TD>
     </TR>
     <TR>
         <TD>SHOW CHKCONSTRAINTS</TD><TD>Shows whether the current CHECK constraint is set or not.</TD>
     </TR>
     <TR>
         <TD>SHOW FOREIGNKEYS</TD><TD>Shows the current foreign key display
setting.</TD>
     </TR>
     <TR>
         <TD>SHOW PARTITIONS</TD><TD>Shows whether the current partition display is set or not.</TD>
     </TR>
     <TR>
         <TD>SHOW VERTICAL</TD><TD>Shows whether the results of a SELECT
query will be output vertically.</TD>
     </TR>
     <TR>
         <TD>SHOW ALL</TD><TD>Shows the set values of the display settings for the current session.</TD>
     </TR>
     <TR>
         <TD ROWSPAN="7">Variable and
Prepared SQL
statements</TD><TD ROWSPAN="2">Variable declaration</TD><TD>VAR p1 INTEGER;</TD><TD>Declares the variable p1 as integer type.</TD>
     </TR>    
     <TR>
         <TD>VARIABLE p2 CHAR(10);</TD><TD>Declares the variable p2 as CHAR type. </TD>
     </TR>
     <TR>
         <TD ROWSPAN="2">Assign values
to variables</TD><TD>EXECUTE :p1 := 100;</TD><TD>Assigns the value 100 to variable p1.</TD>
     </TR>
     <TR>
         <TD>EXEC :p2 := 'abc';</TD><TD>Assigns the text ‘abc’ to variable p2.</TD>
     </TR>
     <TR>
         <TD ROWSPAN="2">Variable display</TD><TD>PRINT VAR[IABLE];</TD><TD>Shows the currently declared variables.</TD>
     </TR>
     <TR>
         <TD>PRINT p1;</TD><TD>Shows the type and value of variable p1.</TD>
     </TR>
     <TR>
         <TD>Prepared SQL
statement execution</TD><TD>PREPARE SQL statement ;</TD><TD>Separates the processes of query optimization and execution, and executes the
query as a prepared SQL statement. In
iSQL, the default execution method for
executing SQL statements is the Direct
Execution method, in which optimization
and execution are performed at
once.There is no difference between the
two execution methods in iSQL in terms
of the results obtained, however, prepared SQL statements can be used to
bind variables to values and execute
SQL statements based thereon.</TD>
      </TR>
      <TR>
          <TD ROWSPAN="7">Functions for
user convenience</TD><TD>Historylist
display</TD><TD>HISTORY;<BR>H;
</TD><TD>Shows a list of the commands currently
saved in the iSQL buffer.</TD>
      </TR>
      <TR>
          <TD ROWSPAN="2">Repeat execution </TD><TD>/</TD><TD>Repeats execution of the command currently in the iSQL buffer. The most recently executed command will be executed again./TD>
      </TR>
      <TR>
          <TD>2/</TD><TD>Executes the second command in a list
output using the HISTORY command. </TD>
      </TR>
      <TR>
          <TD>Shell command execution</TD><TD>! shell command</TD><TD>A shell command that follows an exclamation point will be immediately executed from within iSQL.</TD>
      </TR>
      <TR>
          <TD>Command
prompt change</TD><TD>SET SQLP[ROMPT] {text}</TD><TD>This configures the iSQL command
prompt.</TD>
      </TR>
       <TR>
          <TD>Comment </TD> <TD>/* comment */<BR>-- comment</TD> <TD>Indicate a multiple-line comment and a
single-line comment, respectively.</TD>
       </TR>
       <TR>
          <TD>Help</TD> <TD>HELP;<BR>HELP INDEX;<BR>HELP EXIT;</TD> <TD>This provides information on how to use
help, outputs a list of commands, and
describes (e.g.) the EXIT command, respectively.</TD>
       </TR>          
</table>         





###  iSQL Environment Variables

#### ALTIBASE_HOME

ALTIBASE_HOME is the environment variable which must be configured in order to used iSQL.

Although it is automatically configured when the server is installed in general, but the user should directly configure since there might be a chance of conflict with the environment variables in the server. 

#### ALTIBASE_PORT_NO

This is the port number of the server to connect to. This can be specified either by using the -PORT option or in altibase.properties. 

If no designated port number can be found (in descending order of precedence) in the -PORT option, in the environment variable ALTIBASE_PORT_NO, or in altibase.properties, a prompt to enter the port number will appear.

#### ALTIBASE_SSL_PORT_NO

The port number of the server iSQL is to connect to on SSL/TLS. 

The -PORT option, environment variables, ALTIBASE_SSL_PORT_NO, the properties in the altibase.properties file take priority in this order as the port number in SSL. On omission, the command prompt asks the user to enter the port number. 

#### ALTIBASE_NLS_USE

This is the character set used to display retrieved results to the user. 

-   US7ASCII

-   KO16KSC5601

-   MS949

-   BIG5

-   GB231280

-   MS936

-   UTF8

-   SHIFTJIS

-   MS932

-   EUCJP

This can be set either using the -NLS_USE option or in altibase.properties. 

If NLS_USE is not specified using the -NLS_USE option, the environment variable ALTIBASE_NLS_USE, or altibase.properties (in descending order of precedence), US7ASCII is used as the default character set.

#### ALTIBASE_NLS_NCHAR_LITERAL_REPLACE

By default, iSQL converts an entire query string to the database character set before sending the data to the database. This behavior can be prevented for a given string literal by setting this property to 1 and placing the "N" character in front of the string literal. 

A property setting of 1 instructs iSQL to search for the "N" character in front of every string literal. If the "N" character is found, iSQL sends the string to the database without converting it to the database character set. This is useful when it is desired to use NCHAR type data that are encoded differently from the database character set.

-   0: convert all strings to the database character set without checking for the "N" character
  
-   1: do not convert strings that are preceded by the "N" character to the database character set

Note: Setting this variable to 1 can be expensive in terms of usage of client resources.

#### ISQL_CONNECTION

When Altibase is operated with a client-server arrangement, the user can select the client-server protocol that is suitable for the operating environment by setting environment variables. Altibase supports the TCP/IP, IPC, IPCDA, and Unix domain SSL socket protocols. The default protocol for communication with Altibase servers is TCP/IP. 

- TCP
- UNIX
- IPC
- IPCDA
- SSL
- IB

Note that when using the IPC or IPCDA protocol the value of Altibase properties related to the IPC channel (IPC_CHANNEL_COUNT or IPCDA_CHANNEL_COUNT) must be considered. 

The following example shows how to set the environment variable when using the IPC protocol:

```
CSH: setenv ISQL_CONNECTION IPC
SH: ISQL_CONNECTION=IPC; export ISQL_CONNECTION
```

Note: If the value set for the ISQL_CONNECTION environment variable is UNIX or IPC, and the remote server is specified for the -s option, a warning message that the setting for ISQL_CONNECTION has been ignored is output and iSQL connects to the remote server using TCP. 

#### ISQL_BUFFER_SIZE

The size of the buffer in which to store queries can be set using this environment variable. 

```
CSH: setenv ISQL_BUFFER_SIZE 128000
SH: ISQL_BUFFER_SIZE = 128000; export ISQL_BUFFER_SIZE
```



#### ALTIBASE_DATE_FORMAT

When retrieving Date type data using a SELECT statement, the environment variable ALTIBASE_DATE_FORMAT can be used to change the default date format, which is YYYY/MM/DD HH:MI:SS, to some other date format.

Ex) For Born, Korn, or Bash Shell

```
export ALTIBASE_DATE_FORMAT=’DD-MON-YYYY’
```



#### ISQL_EDITOR

This environment variable can be used to change the default editor (Ex: /bin/vi ). 

```
CSH: setenv ISQL_EDITOR /usr/bin/ed
SH: ISQL_EDITOR=/usr/bin/ed; export ISQL_EDITOR
```



#### ALTIBASE_IPC_FILEPATH

In a Unix environment, if a client and the server have different values for ALTIBASE_HOME, they will not be able to connect via IPC since they have different Unix domain socket paths. In this case, in order to be able to connect via IPC, it is necessary to set the ALTIBASE_IPC_FILEPATH environment variable or the -IPC-FILEPATH iSQL option to the $ALTIBASE_HOME/trc/cm-ipc file used by the server.

#### IPCDA_FILEPATH

In a Unix environment, if a client and the server have different values for ALTIBASE_HOME, they will not be able to connect via IPCDA since they have different Unix domain socket paths. In this case, if IPCDA_FILEPATH environment variables or –IPCDA -FILEPATH is specified as a file of $ALTIBASE_HOME/trc/cm-ipcda in the server connection via IPCDA is possible because the server and client can use the identical socket file.

#### ALTIBASE_TIME_ZONE

This environment variable sets the time zone of the client. If DB_TZ is specified for this option, the time zone is defaulted to that of the database server. 

This environment variable can be set with time zone names like Asia/Seoul, abbreviations such as KST and UTC offset values as +09:00 are valid for specification.



### Personalizing iSQL

iSQL users can customize their iSQL environment and use the same settings for each session. For example, using the OS file, the user can specify a desired output format so that each query result displays the current time whenever query results are output. These files can be categorized into the following two types.

#### glogin.sql

For initialization tasks that must be conducted when iSQL is started, iSQL supports the creation of a global script file, glogin.sql, by the DB administrator. iSQL executes this script whenever any user executes iSQL or attempts to connect to Altibase for the first time. The global file allows the DB administrator to make site-specific iSQL environment settings for all users. The global script file is located in $ALTIBASE_HOME/conf.

#### login.sql

iSQL also supports the login.sql file, which is executed after glogin.sql. If both the glogin.sql file and the login.sql file exist, login.sql is executed after glogin.sql during iSQL startup, so the commands in login.sql will take precedence. 

If several people share one Unix account, it will be impossible for them to personalize the glogin.sql file. In this case, individual users may add SQL commands, stored procedures, or iSQL commands to their respective login.sql files in their personal work directories. When a user starts up iSQL, iSQL automatically searches the current directory for the login.sql file and executes the commands in it. 

The login.sql file cannot modify initial iSQL settings or individual session actions.

#### Editing the LOGIN file

The user may change the LOGIN file, like any other script. The following is an example of user1 creating a LOGIN file that turns off autocommit mode and executes SQL statements:

```
$ vi glogin.sql
AUTOCOMMIT ON
SET HEADING OFF
SELECT sysdate FROM dual;

$ vi login.sql
AUTOCOMMIT OFF;
SET HEADING ON
DROP TABLE savept;
CREATE TABLE savept(num INTEGER);
INSERT INTO savept VALUES(1);
SAVEPOINT sp1;
INSERT INTO savept VALUES(2);
SELECT * FROM savept;
ROLLBACK TO SAVEPOINT sp1;
SELECT * FROM savept;
COMMIT;

$ isql
-------------------------------------------------------
     Altibase Client Query utility.
     Release Version 7.1.0.1
     Copyright 2000, Altibase Corporation or its subsidiaries.
     All Rights Reserved.
-------------------------------------------------------
Write Server Name (default:127.0.0.1) :
Write UserID : user1
Write Password :
ISQL_CONNECTION = TCP, SERVER = 127.0.0.1, PORT_NO = 20300
Set autocommit on success. -> Executing glogin.sql first
28-DEC-2004 -> heading off
1 row selected.
Set autocommit off success. -> Execute login.sql in the current work directory of the user after
glogin.sql is executed.
Drop success.
Create success.
1 row inserted.
Savepoint success. -> It is executable only when Autocommit mode is off
1 row inserted.
NUM -> heading on
--------------
1           
2           
2 rows selected.
Rollback success.
SAVEPT.NUM  
--------------
1           
1 row selected.
Commit success.
```



#### Notes

For security reasons, the CONNECT command which inputs both the user name and password cannot be used with the LOGIN file. If the CONNECT command is included in the LOGIN file, the following warning message is output and the command is not executed.

```
WARNING: CONNECT command in glogin.sql file ignored
```





# 2. Examples of iSQL in Use

This chapter describes several examples of the use of iSQL to manipulate databases.

### Logging In to iSQL

To use iSQL, users must first be logged in. Connection information may be input directly via a command line, or via the iSQL input prompt.

```
isql -U userID -P password [-SYSDBA]
or
isql [-SYSDBA]
```

Additional information necessary for connection with the server is the server name (-S), user ID (-U), and password (-P). The user ID and password are not case-sensitive. 

In order for the SYS user to use iSQL as an administrator, the SYSDBA option is used. The SYSDBA option can be used for remote access. 

-SYSDAB option should be used in order for the SYS user to use iSQL as an administrator. The SYSDBA option can be also used for remote access. Use double quotation marks if the user ID contains special characters or spaces.

```
$ isql -U \"user name\"
```



#### Login Restrictions

-   Only one user is permitted to connect in SYSDBA mode at one time. Two or more users cannot connect in SYSDBA mode at the same time. 
-   The user can access the database remotely in SYSDBA mode, but can't start up the database.

For detailed information on system privileges, please refer to the *Altibase SQL Reference.* 

For detailed information on errors that may arise during iSQL execution, please refer to the *Altibase Error Message Reference.*

```
$ isql -U sys -P manager [-SYSDBA]
```

```
$ isql [-sysdba]
-------------------------------------------------------
     Altibase Client Query utility.
     Release Version 7.1.0.1
     Copyright 2000, Altibase Corporation or its subsidiaries.
     All Rights Reserved.
-------------------------------------------------------
Write Server Name (default:127.0.0.1) :
Write UserID : sys
Write Password : manager             -> The password on the screen is not displayed.
ISQL_CONNECTION = TCP, SERVER = 127.0.0.1, PORT_NO = 20300
iSQL(sysdba)>	-> iSQL is connected to the server, and SQL, iSQL, and PSM commands
can be input and executed here.

```



### Starting Up and Shutting Down Altibase

iSQL can be used to start up and shut down Altibase.

#### Starting Up Altibase

To start up Altibase, iSQL must first be launched with the -sysdba option, in the same way as when a database is created.

>  Altibase startup commands can be executed only with the UNIX account with which Altibase (including iSQL) was installed.

The following is an example of the use of iSQL to start up Altibase. For more information on starting up Altibase, please refer to the *Altibase Administrators’ Manual Chapter 4: Startup and Shutdown.*

```
$ isql –s 127.0.0.1 –u sys –p manager –sysdba
-------------------------------------------------------
     Altibase Client Query utility.
     Release Version 7.1.0.1
     Copyright 2000, Altibase Corporation or its subsidiaries.
     All Rights Reserved.
-------------------------------------------------------
ISQL_CONNECTION = TCP, SERVER = 127.0.0.1, PORT_NO = 20300
[Connected to idle instance]
iSQL(sysdba)> startup service
Connecting to the DB server... Connected.

TRANSITION TO PHASE : PROCESS

TRANSITION TO PHASE : CONTROL

TRANSITION TO PHASE : META
  [SM] Recovery Phase - 1 : Preparing Database
                            : Dynamic Memory Version => Parallel Loading
  [SM] Recovery Phase - 2 : Loading Database
  [SM] Recovery Phase - 3 : Skipping Recovery & Starting Threads...
                              Refining Disk Table
  [SM] Refine Memory Table : ........................................................ [SUCCESS]
  [SM] Rebuilding Indices [Total Count:100] .................................. [SUCCESS]
TRANSITION TO PHASE : SERVICE
  [CM] Listener started : TCP on port 20300
  [CM] Listener started : UNIX
  [RP] Initialization : [PASS]
--- STARTUP Process SUCCESS ---
Command execute success.
```



#### Shutting Down Altibase

Use the SHUTDOWN command to shut down a running Altibase server. 

The following is an example of the use of iSQL to shut down Altibase. For more information on shutting down Altibase, please refer to the Altibase Administrators’ Manual Chapter 4: Startup and Shutdown.

```
iSQL(sysdba)> shutdown normal
Ok..Shutdown Proceeding....


TRANSITION TO PHASE : Shutdown Altibase
  [RP] Finalization : PASS
shutdown normal success.
```



### Connecting and Disconnecting

#### Connecting to a Database

The CONNECT command is used to connect to Altibase with a specified user ID. If the first connection attempt fails, the CONNECT command does not prompt again for the user ID or password.

```
CONNECT [logon][nls] [AS SYSDBA];  
logon: userID[/password]  
nls: NLS=character_set
```



- userID/password
  The user ID and password with which to establish a connection to Altibase.
- NLS=character_set
  The NLS option specifies the character set.

```
iSQL> CONNECT sys/manager NLS=US7ASCII
Connect success.
```

- AS SYSDBA
  The AS clause permits the SYS user to access the server in sysdba manager mode. 
  
  If CONNECT is successful, the current session is terminated, and a connection is established to the server using the specified user ID and password and the information in altibase.properties. Accordingly, the session information is cleared before connecting. 
  
  For instance, if AUTOCOMMIT mode is set to TRUE in altibase.properties and AUTOCOMMIT mode is changed to FALSE in iSQL, when the CONNECT statement is executed, AUTOCOMMIT mode will be changed to TRUE, because of the value in altibase.properties. 
  
  If CONNECT fails, the previous session is terminated and the connection with the server is closed. In other words, the result of all SQL statements executed thereafter will be a “Not connected”   message. Execute “CONNECT userID/password [AS SYSDBA]” to attempt to re-establish a connection with the server.

```
$ isql
-------------------------------------------------------
     Altibase Client Query utility.
     Release Version 7.1.0.1
     Copyright 2000, Altibase Corporation or its subsidiaries.
     All Rights Reserved.
-------------------------------------------------------
Write Server Name (default:127.0.0.1) :
Write UserID : SYS
Write Password :
ISQL_CONNECTION = TCP, SERVER = 127.0.0.1, PORT_NO = 20300
iSQL> SHOW USER;
User : SYS
iSQL> CREATE USER altiadmin IDENTIFIED BY altiadmin1234;
Create success.
iSQL> CONNECT altiadmin/altiadmin1234;
Connect success.
iSQL> SHOW USER;
User : ALTIADMIN
iSQL> CREATE TABLE altitbl(i1 INTEGER, i2 CHAR(5));
Create success.
iSQL> SELECT * FROM tab;
TABLE NAME                               TYPE
---------------------------------------------
ALTITBL                                  TABLE
.
.
.
33 row selected.
iSQL> CONNECT sys/manager;
Connect success.
iSQL> SHOW USER;
User : SYS
iSQL> CREATE TABLE systbl(i1 INTEGER, i2 CHAR(5));
Create success.
iSQL> SELECT * FROM tab;
USER NAME	TABLE NAME	TYPE
-----------------------------------------------
SYSTEM_	SYS_COLUMNS_	SYSTEM TABLE
SYSTEM_	SYS_CONSTRAINTS_	SYSTEM TABLE
.
.
.
ALTIADMIN	ALTITBL		TABLE.
SYS		SYSTBL		TABLE
.
.
.
93 rows selected.
```



> ##### Note
>
> Double quotation marks should be used if the name contains special characters or spaces.
> 
>```
> iSQL\> CONNECT "user name";
> ```

#### Connecting on SSL

##### Server-Exclusive Mode

When using a private certificate in server-exclusive mode (when the SSL_CLIENT_AUTHENTICATION property is set to 0), the location of the client certificate and private key file need not be specified, as the server does not authenticate the client. 

Enable the -ssl_verify option and specify the location of the CA certificate file in which the server public key is incorporated, to verify the certificate received from the server.

```
$ export ISQL_CONNECTION=SSL
$ isql -s localhost -u sys -p MANAGER
or
$ isql -s localhost -u sys -p MANAGER -ssl_verify -ssl_ca ~/cert/ca-cert.pem
```



##### Mutual Authentication Mode

When using a private certificate in mutual authentication mode (when the SSL_CLIENT_AUTHENTICATION property is set to 1), the location of the client certificate and private key file need to be specified, as the server performs client authentication. 

Enable the -ssl_verify option and specify the location of the CA certificate file in which the server public key is incorporated, to verify the certificate received from the server.

```
$ export ISQL_CONNECTION=SSL
$ isql -s localhost -u sys -p MANAGER \
-ssl_cert ~/cert/client-cert.pem \
-ssl_key ~/cert/client-key.pem
or
$ isql -s localhost -u sys -p MANAGER \
-ssl_verify -ssl_ca ~/cert/ca-cert.pem \
-ssl_cert ~/cert/client-cert.pem \
-ssl_key ~/cert/client-key.pem
```



#### Disconnecting from a Database

DISCONNECT is used to terminate the current session and disconnect from the server. The result of all subsequently executed SQL statements will be a “Not connected” message, and “CONNECT userID/password” must be executed in order to connect to the server again.

```
DISCONNECT;
iSQL> INSERT INTO systbl VALUES(1, 'A1');
1 row inserted.
iSQL> INSERT INTO systbl VALUES(2, 'A2');
1 row inserted.
iSQL> SELECT * FROM systbl;
SYSTBL.I1   SYSTBL.I2  
--------------------------
1           A1     
2           A2     
2 rows selected.
iSQL> DISCONNECT;
Disconnect success.
iSQL> INSERT INTO systbl VALUES(3, 'A3');
[ERR-91020 : No Connection State]
iSQL> SELECT * FROM systbl;
[ERR-91020 : No Connection State]
iSQL> CONNECT sys/manager;
Connect success.
```



#### Executing iSQL with the NOLOG Option

The /NOLOG option allows the user to execute iSQL without connecting to the database. The server IP address and port number must be specified to use this option. 

```
isql -s localhost -port 20300 /NOLOG
```

Once iSQL is running, enter the database user ID and password with the CONNECT command to connect to the database, and then execute a SQL statement. 



### Retrieving Information Related to the Database and Database Objects

#### Performance Views

A performance view is a type of data dictionary table capable of inquiring about the server status and database information. The following SELECT statement can be used to view the list of performance views provided by Altibase:

```
iSQL> SELECT * FROM V$TAB;
TABLE NAME                               TYPE
---------------------------------------------
V$ALLCOLUMN                              PERFORMANCE VIEW
V$ARCHIVE                                PERFORMANCE VIEW
V$BUFFPOOL_STAT                          PERFORMANCE VIEW
V$DATABASE                               PERFORMANCE VIEW
V$DATAFILES                              PERFORMANCE VIEW
V$DISKGC                                 PERFORMANCE VIEW
V$DISKTBL_INFO                           PERFORMANCE VIEW
V$FLUSHINFO                              PERFORMANCE VIEW
```

or the complete list of the performance views provided with Altibase and the meanings of the columns, please refer to the *Altibase General Reference Chapter 3: Data Dictionary.* 

Data in a particular performance view can be queried in the same way as an ordinary table using a SELECT statement, and using JOIN, etc., results can be output in various forms.

#### Viewing the List of Tables

Information on all of the tables that exist in the database can be retrieved using the following SELECT statement. The SYS_TABLES_ meta table is an internal system table that contains information about the database catalog provided by Altibase.

```
iSQL> SELECT * FROM system_.sys_tables_;
.
.
iSQL> SELECT * FROM tab;  -> This command is available in iSQL only. 
USER NAME	TABLE NAME	TYPE
-----------------------------------------------
.
..
```



#### Viewing a Table Structure

The following command is used to retrieve information on user-created tables: 

```
DESC table_name;

CREATE TABLE department (
DNO            SMALLINT     PRIMARY KEY,
DNAME          CHAR(30)     NOT NULL,
DEP_LOCATION   CHAR(9),
MGR_NO         INTEGER );

iSQL> DESC department; 	-> The name of a table whose information (table structure) you want to know.
[ TABLESPACE : SYS_TBS_MEM_DATA ]
[ ATTRIBUTE ]
-----------------------------------------------------------
NAME                  TYPE                        IS NULL
-----------------------------------------------------------
DNO                   SMALLINT        FIXED       NOT NULL
DNAME                 CHAR(30)        FIXED       NOT NULL
DEP_LOCATION          CHAR(9)         FIXED       
MGR_NO                INTEGER         FIXED       
[ INDEX ]
-----------------------------------------------------------
NAME                  TYPE     IS UNIQUE     COLUMN
-----------------------------------------------------------
__SYS_IDX_ID_122      BTREE    UNIQUE        DNO ASC
[ PRIMARY KEY ]
-----------------------------------------------------------
DNO
```

Use double quotation marks if the table name contains special characters or spaces.

```
iSQL> DESC "table name";
iSQL> DESC "user name"."table name";
```



#### Viewing Sequence Information

The following commands are used to obtain information on all sequences that exist in the database:

```
SELECT * FROM seq;

iSQL> CONNECT sys/manager;
Connect success.
iSQL> CREATE USER user1 IDENTIFIED BY user1;
Create success.
iSQL> CONNECT user1/user1;
Connect success.
iSQL> CREATE SEQUENCE seq1 MAXVALUE 100 CYCLE;
Create success.
iSQL> CREATE SEQUENCE seq2;
Create success.
iSQL> CONNECT sys/manager;
Connect success.
iSQL> CREATE SEQUENCE seq2 START WITH 20 INCREMENT BY 30;
Create success.
iSQL> CREATE SEQUENCE seq3 CACHE 40;
Create success.
iSQL> SELECT * FROM seq;
      ->When accessing the database using the SYS account, information of all sequences will be displayed.

USER_NAME                                 
--------------------------------------------
SEQUENCE_NAME                             CURRENT_VALUE   INCREMENT_BY    
------------------------------------------------
MIN_VALUE              MAX_VALUE              CYCLE           CACHE_SIZE      
------------------------------------------------
SYS                                       
SEQ2                                      20              30              
1                      9223372036854775806    NO              20              
SYS                                       
SEQ3                                      1               1               
1                      9223372036854775806    NO              40              
USER1                                     
SEQ1                                      1               1               
1                      100                    YES             20              
USER1                                     
SEQ2                                      1               1               
1                      9223372036854775806    NO              20           
4 rows selected.

iSQL> CONNECT user1/user1;
Connect success.

iSQL> SELECT * FROM seq;
	-> Information of all sequences created by User 1 will be displayed.
SEQUENCE_NAME                             CURRENT_VALUE   INCREMENT_BY    
------------------------------------------------
MIN_VALUE              MAX_VALUE              CYCLE           CACHE_SIZE      
------------------------------------------------
SEQ1                                      1               1               
1                      100                    YES             20              
SEQ2                                      1               1               
1                      9223372036854775806    NO              20           
2 rows selected.
```



### Controlling Transactions

#### Defining Transaction Modes

AUTOCOMMIT determines whether to automatically commit the results of a command at the time of execution.

```
iSQL> AUTOCOMMIT OFF; ->  Commands are not automatically committed before being manually committed by the user.
Set autocommit off success.

iSQL> AUTOCOMMIT ON; -> Commands are automatically committed at the time of execution.
Set autocommit on success.
```



#### PLANCOMMIT

```
SET PLANCOMMIT ON/OFF;
```

When EXPLAIN PLAN has been set to ON or ONLY, there is the possibility that the iSQL commands DESC; SELECT * FROM TAB; or SELECT * FROM SEQ; will be committed, even if AUTOCOMMIT has been set to OFF. This setting determines whether to commit them automatically.

> Note: This setting has been provided to overcome the misunderstanding where the user believes that such a command has not been prepared, but the system prepares the command in order to generate the execution plan. The command would then be committed, without the user knowing it, when a COMMIT command is executed later. When this value is OFF (which is the default) in a session for which EXPLAIN PLAN is ON (or ONLY) and AUTOCOMMIT is OFF, Altibase does not autocommit the above commands (DESC, SELECT * FROM tab; or SELECT * FROM seq;). When this value is ON, iSQL issues a special commit command to commit these commands.
>



### File Management

#### Saving Results

iSQL enables results returned through iSQL to be saved in a designated file. In the following example, results are stored in the designated file, book.txt, using the SPOOL command. 

To cancel this command, use the SPOOL OFF command.

```
iSQL> SPOOL book.txt	 
Spool start. [book.txt]	-> All subsequently executed commands and their results will be written to
book.txt. The file is created in the current directory.
iSQL> SPOOL OFF
Spool Stop		-> From this point on, no more commands or results will be saved in the file.
```



#### Running Scripts

##### @ Command

```
@file_name[.sql]
or
START file_name[.sql]
```

file_name[.sql]: The script file to be executed. If the filename extension is omitted, iSQL assumes the default command file extension (.sql). 

When this command is executed, , iSQL executes all of the commands in the specified script file in sequence. 

@command performs the same function as START.

-   An EXIT or QUIT command in the script file terminates iSQL. 
-   The script file may include general SQL statements, iSQL commands, references to stored procedures, etc.

The following is an example in which the schema.sql script, which can be found in the $ALTIBASE_HOME/sample/APRE/schema directory, which is the current directory, is executed.

```
iSQL> START schema.sql  	<- The SQL statements in the file are executed. 
or
iSQL> @schema.sql
```

When specifying a script file, you can use a question mark (“?”) to indicate the Altibase home directory (\$ALTIBASE_HOME) of the user account. The following is an example in which the schema.sql script, which can be found in the ​\$ALTIBASE_HOME/sample/APRE/schema directory, is executed regardless of which directory is the current directory.

```
iSQL> @?/sample/schema.sql
```

The question mark (“?”) can also be used with the following iSQL commands:

edit, save, load, spool, start

> The -- or /* */ characters can be used to insert comments in script files. -- means that everything that follows until the end of the line will be handled as a comment, whereas comments that span several lines are placed between /* and */.

##### @@ Command

```
@@file_name[.sql]
```

file_name[.sql]: This indicates the embedded script to be executed. If the extension is omitted, iSQL assumes the default command file extension(.sql). 

Executes the specified script. The functionality of the @@ command is similar to that of the @ command. 

This command searches for script files in the same path as the script currently being executed, and is thus useful for executing embedded scripts. 

The @@ command can be used for the following purposes:

-   If a script file that contains the text @@file_name.sql is executed, iSQL looks for the file specified by file_name.sql, and executes its contents in sequence. file_name.sql must be located in the same directory as the script file that called it. If no such file exists, iSQL raises an error.
  
-   If a user inputs @@file_name.sql at the iSQL prompt, the result will be the same as when using iSQL to execute @file_name.sql.
  
-   The script typically may include SQL statements, iSQL commands, or stored procedures.
  
-   An EXIT or QUIT command in the script terminates iSQL.

The following is an example of the execution of a.sql, in which schema.sql is referenced, from the \$ALTIBASE_HOME directory. In order for this example to be executed without error, a.sql must exist in the $ALTIBASE_HOME/sample/APRE/schema directory alongside schema.sql.

```
iSQL> @sample/APRE/schema/a.sql

$ cat a.sql
@@schema.sql
```

> Note: The following chapter provides examples of editing the results of a query in an iSQL environment based on the tables created by execution of the above script (see appendix Schema). 

##### Passing parameters through SART Command

```
START file_name[.sql] [param1 [param2] ...]
@file_name[.sql] [param1 [param2] ...]
@@file_name[.sql] [param1 [param2] ...]
```

[param1 [param2] ...] : The value to be transferred as a parameter to the script file.

The substitution variables are used if a user wants to specify every time execution is made and not fixating certain values of a SQL statement within the script file. The values to be replaced the substitution variable can be passed as a parameter if the script file is executed with START, @ or @@ command. 

The substitution variable within the script file is used with '&' and numbers, and the number signifies the sequence. However, this feature is performed only if the SET DEFINE ON option is specified. Refer to the SET DEFINE(hyperlink) for further information.

For instance, if substitution variables are used in emp.sql file as in the following :

```
SELECT ENO, E_LASTNAME FROM EMPLOYEES
WHERE EMP_JOB = '&1'
AND SALARY > &2;
```

If 'programmer' and '2000' are inserted as parameters when executing the START command, 'programmer' and '2000' are replaced into &1 and &2, respectively. Thus, employees whose job is 'programmer' and salary is '2000' are viewed. 

```
iSQL> SET DEFINE ON; -- Substitution values are replaced as parameters if it is set to ON.
iSQL> START emp.sql programmer 2000
old   2: WHERE EMP_JOB = '&1'
new   2: WHERE EMP_JOB = 'programmer'
old   3: AND SALARY > &2;
new   3: AND SALARY > 2000;

ENO         E_LASTNAME
-------------------------------------
10          Bae
```

iSQL outputs SQL commands before and after parameter values are replaced for the command-lines containing substitution variables. SQL commands after replacing values are not output if the SET VERIFY OFF option is specified. The substitution variable can be used for multiple times within a single script and it is not necessary to be used in sequence. 

The substitution value can also be replaced with parameters in the following manner.

```
START emp.sql
...
Enter value for 1: programmer
old   2: WHERE EMP_JOB = '&1'
new   2: WHERE EMP_JOB = 'programmer'
Enter value for 2: 2000
old   3: AND SALARY > &2;
new   3: AND SALARY > 2000;
```

In addition, in order to use specific characters by connecting immediately after the substitution value, a period(.) should be used for distinguishing the substitution value and characters.

```
SELECT E_LASTNAME FROM EMPLOYEES WHERE ENO='&1.0';
Enter value for 1: 2
old   1: SELECT E_LASTNAME FROM EMPLOYEES WHERE ENO='&1.0';
new   1: SELECT E_LASTNAME FROM EMPLOYEES WHERE ENO='20';
```



##### SET DEFINE {ON\|OFF}

This specifies whether or not to replace substitution variables with the parameter values inserted by a user when executing a script file containing the substitution variable through the START, @ or @@ command. 

The default value is set to OFF, and substitution variables are not replaced with parameter values. That is, this option should be set to ON when executing a script file containing substitution variables.

##### SET VERIFY {ON\|OFF}

This specifies whether or not to display SQL statements before and after replacing with the parameter value when executing a script file containing the substitution variable through the START, @ or @@ command. 

The default value is set to ON and before and after SQL statements are output.

```
$cat Param1.sql
SELECT * FROM T1 WHERE I1 = &1;

iSQL> SET DEFINE ON;
iSQL> SHOW VERIFY;
Verify : On
iSQL> START Param1.sql 5;
iSQL> SELECT * FROM T1
WHERE I1 = &1;
old   2: WHERE I1 = &1;
new   2: WHERE I1 = 5;
T1.I1       T1.I2
---------------------------
5           Hyacinth
1 row selected.

iSQL> SET VERIFY OFF;
iSQL> SHOW VERIFY;
Verify : Off
iSQL> START Param1.sql 5;
iSQL> SELECT * FROM T1
WHERE I1 = &1;
T1.I1       T1.I2
---------------------------
5           Hyacinth
1 row selected.
```



#### Saving SQL Statements

Of the commands currently in the iSQL buffer, the SAVE command saves the most recently executed one in a file. 

This file will be created in the current directory.

```
iSQL> SELECT * FROM book;
iSQL> SAVE book.sql; -> ‘SELECT * FROM book;’ is saved in the file book.sql.
Save completed.
```



#### Loading SQL Statements

This function loads the first command in the specified file to the last position in the iSQL buffer.

```
iSQL> LOAD book.sql
iSQL> SELECT * FROM book;
Load completed.
iSQL> /		 -> The results of execution of SELECT * FROM book; can be seen.
```



#### Saving DML Statements

Executed DML statements such as INSERT, UPDATE, DELETE and MOVE are saved in $ALTIBASE_HOME/trc/isql_query.log. 

Specify SET QUERYLOGGING ON to use this functionality and OFF to disable it.

```
iSQL> SET QUERYLOGGING ON;	-> From this point on, all executed DML statements will be
saved in $ALTIBASE_HOME/trc/isql_query.log. 
iSQL> CREATE TABLE T1 ( I1 INTEGER );
Create success.
iSQL> INSERT INTO T1 VALUES ( 1 );
1 row inserted.
iSQL> UPDATE  T1 SET I1 = 2;
1 row updated.
iSQL> SELECT * FROM T1;
I1  
--------------
2
1 row selected.
iSQL> DELETE FROM T1;
1 row deleted.
iSQL> DROP TABLE T1;
Drop success.
iSQL> EXIT

% cat $ALTIBASE_HOME/trc/isql_query.log	-> All queries executed since SET QUERYLOGGING ON
was executed can be observed.
[2009/09/16 10:36:14] [127.0.0.1:25310 SYS] INSERT INTO T1 VALUES ( 1 )
[2009/09/16 10:36:31] [127.0.0.1:25310 SYS] UPDATE T1 SET I1 = 2
[2009/09/16 10:36:37] [127.0.0.1:25310 SYS] DELETE FROM T1
```



#### Editing Query Statements

##### Editing the Most Recent Query Statement

The command edit is provided for creating and editing files in iSQL. 

If ed is executed without parameters, a temporary file named iSQL.buf containing the most recently executed query statements will be created, and the following screen will be visible. (To save space, only a few of the blank lines that would be displayed on the screen are shown here.)

```
iSQL> SELECT sysdate FROM dual;
SYSDATE      
---------------
01-JAN-2000  
1 row selected.

iSQL> ed
SELECT sysdate FROM dual;
~
~
~
"iSQL.buf" 1L, 26C
```



Editing Existing Files

If the user wants to edit an existing file, type the file name in iSQL as a parameter when launching the text editor using the “ed” command. When the screen is initialized, blank lines will be displayed as ~ (tilde) characters.

```
iSQL> ed myquery.sql
"myquery.sql"
INSERT INTO employee(ENO, E_FIRSTNAME, E_LASTNAME, SEX) VALUES(21, 'MSJUNG', 'F');
INSERT INTO employee(ENO, E_FIRSTNAME, E_LASTNAME, SEX, JOIN_DATE)
VALUES(22, 'Joshua', 'Baldwin', 'M', TO_DATE('2001-11-19 00:00:00', 'YYYY-MM-DD HH:MI:SS'));
~
~"myquery.sql"
```



##### Editing Query Statements in History Lists

The user can use the number in the history list to edit previously executed commands. In detail, the query statements are stored in the temporary file iSQL.buf in association with numbers, and can be edited with reference to them. The edited query will be stored again as the most recent record in the history list, and can be executed by entering the ‘/’ (re-execute) character.

```
iSQL> h
1  : SELECT * FROM customers;
2  : SELECT * FROM employees;
iSQL> 2ed
or
iSQL> 2 ed
SELECT * FROM employees;
~
~
"iSQL.buf"
```

> The command-line parameter 2, which is the name of the file to be edited (iSQL> ed 2), must be distinguished from the number indicating the line in the file to edit.
>

After editing (employees was replaced with orders)

```
iSQL> h 		<- The history list currently in the iSQL buffer 
1  : SELECT * FROM customers;
2  : SELECT * FROM employees;
 : SELECT * FROM orders;
	<- The query statement edited using the 2 ed command will be saved as the last command in the history list.

iSQL> /		<- The most recently executed command will be executed.
ORDERS.ONO            ORDERS.ORDER_DATE    ORDERS.ENO  ORDERS.CNO      
-----------------------------------------------
ORDERS.GNO  ORDERS.QTY  ORDERS.ARRIVAL_DATE  ORDERS.PROCESSING  
-----------------------------------------------
0011290007            2000/11/29 00:00:00  12          7111111431202  
A111100002  70          2000/12/02 00:00:00  C  
0011290011            2000/11/29 00:00:00  12          7610011000001  
E111100001  1000        2000/12/05 00:00:00  D
…
0012310012            2000/12/31 00:00:00  19          7308281201145  
C111100001  250         2001/01/03 00:00:00  O  
30 rows selected.
```



#### Note

Use double quotation marks if the file name contains special characters or spaces.

```
iSQL> SPOOL "file name.txt";
iSQL> START "file name.sql";
iSQL> EDIT "file name.sql";
```



### Formatting SELECT Query Results

The results of a SELECT query can be formatted as desired by the user.

#### SET LINESIZE

Sets the size (number of characters) of one line to be displayed when the results of a SELECT statement are output. It must be between 10 and 32767.

```
iSQL> SET LINESIZE 100; --> Set the display size of one line to 100.
```



#### SET LOBSIZE

This specifies the number of characters to display when a CLOB column is queried using a SELECT statement. 

In order to query CLOB column data using a SELECT statement, the transaction mode must first be set to AUTOCOMMIT OFF.

```
CREATE TABLE C1(I1 INTEGER, I2 CLOB);
INSERT INTO C1 VALUES(1, 'A123456789');
INSERT INTO C1 VALUES(2, 'A1234');
INSERT INTO C1 VALUES(3, 'A12345');
INSERT INTO C1 VALUES(4, 'A1234567890123');

iSQL> autocommit off; 	-> This sets the transaction mode to OFF so that a CLOB column can be queried.
Set autocommit off success.
iSQL> select * from c1;
C1.I1        C1.I2
---------------------------
1	A123456789
2 	A1234
3	A12345
4	A1234567890123
4 rows selected.

iSQL> set lobsize 10; 	-> This specifies the number of characters to display on the screen when querying a CLOB column using a SELECT statement
iSQL> select * from c1;
C1.I1       C1.I2
--------------------------
1           A123456789
2           A1234
3           A12345
4           A123456789
4 rows selected.
```



#### SET LOBOFFSET

This specifies the starting location from which to display CLOB data when a CLOB column is queried using a SELECT statement. 

In order to query CLOB column data using a SELECT statement, the transaction mode must first be set to AUTOCOMMIT OFF.

```
CREATE TABLE C1(I1 INTEGER, I2 CLOB);
INSERT INTO C1 VALUES(1, 'A123456789');
INSERT INTO C1 VALUES(2, 'A1234');
INSERT INTO C1 VALUES(3, 'A12345');
INSERT INTO C1 VALUES(4, 'A1234567890123');

iSQL> autocommit off;
Set autocommit off success.
iSQL> set loboffset 4; 	-> This specifies the starting location of data to be shown on the
screen number of characters to skip) when querying a CLOB column using a SELECT statement.
iSQL> select * from c1;
C1.I1       C1.I2
--------------------------
1           456789
2           4
3           45
4           4567890123
4 rows selected.
```



#### SET FEEDBACK

Outputs the number of records found when the results of a SELECT statement are output.

```
SET FEEDBACK ON\|OFF\|n
```

- ON: Output the number of resultant records after execution of a SELECT statement. 
- OFF: Do not output the number of resultant records after execution of a SELECT statement. 
- n: Output the number of resultant records when the number is n or greater.


```
iSQL> SET FEEDBACK ON;
iSQL> SELECT * FROM employees WHERE ENO < 3;
ENO         E_LASTNAME            E_FIRSTNAME           EMP_JOB          
------------------------------------------------------------------------------
EMP_TEL          DNO         SALARY      SEX  BIRTH   JOIN_DATE    STATUS  
-----------------------------------------------------------------------------------
1           Moon                  Chan-seung            CEO              
01195662365      3002                    M                       R  
2           Davenport             Susan                 designer         
0113654540                   1500        F  721219  18-NOV-2009  H  
2 rows selected.
```



#### SET PAGESIZE

Specifies the number of resultant rows to display at one time.

```
iSQL> SET PAGESIZE 2;	-> Show results in groups comprising two rows each
iSQL> SELECT * FROM employees;
ENO         E_LASTNAME            E_FIRSTNAME           EMP_JOB          
------------------------------------------------------------------------------
EMP_TEL          DNO         SALARY      SEX  BIRTH   JOIN_DATE    STATUS  
-----------------------------------------------------------------------------------
1           Moon                  Chan-seung            CEO              
01195662365      3002                    M                       R  
2           Davenport             Susan                 designer         
0113654540                   1500        F  721219  18-NOV-2009  H  
ENO         E_LASTNAME            E_FIRSTNAME           EMP_JOB          
------------------------------------------------------------------------------
EMP_TEL          DNO         SALARY      SEX  BIRTH   JOIN_DATE    STATUS  
-----------------------------------------------------------------------------------
3           Kobain                Ken                   engineer         
0162581369       1001        2000        M  650226  11-JAN-2010  H  
4           Foster                Aaron                 PL               
0182563984       3001        1800        M  820730               H  
ENO         E_LASTNAME            E_FIRSTNAME           EMP_JOB          
------------------------------------------------------------------------------
EMP_TEL          DNO         SALARY      SEX  BIRTH   JOIN_DATE    STATUS  
-----------------------------------------------------------------------------------
5           Ghorbani              Farhad                PL               
01145582310      3002        2500        M          20-DEC-2009  H  
6           Momoi                 Ryu                   programmer       
0197853222       1002        1700        M  790822  09-SEP-2010  H
.
.
.
20 rows selected.

iSQL> SET PAGESIZE 0;		-> Show all of the results on one page.
iSQL> SELECT * FROM employees;
ENO         E_LASTNAME            E_FIRSTNAME           EMP_JOB          
------------------------------------------------------------------------------
EMP_TEL          DNO         SALARY      SEX  BIRTH   JOIN_DATE    STATUS  
-----------------------------------------------------------------------------------
1           Moon                  Chan-seung            CEO              
01195662365      3002                    M                       R  
2           Davenport             Susan                 designer         
0113654540                   1500        F  721219  18-NOV-2009  H  
3           Kobain                Ken                   engineer         
0162581369       1001        2000        M  650226  11-JAN-2010  H
.
.
.
20 rows selected.
```



#### SET HEADING

Sets whether to output the header with a SELECT result.

```
iSQL> SET HEADING OFF;	  ->  Header is not displayed with the result.
iSQL> SELECT * FROM employees;


1           Moon                  Chan-seung            CEO              
01195662365      3002                    M                       R  
2           Davenport             Susan                 designer         
0113654540                   1500        F  721219  18-NOV-2009  H  
3           Kobain                Ken                   engineer         
0162581369       1001        2000        M  650226  11-JAN-2010  H
.
.
.
20 rows selected.

iSQL> SET HEADING ON;	-> Outputs header in result.
iSQL> SELECT * FROM employee;
ENO         E_LASTNAME            E_FIRSTNAME           EMP_JOB          
------------------------------------------------------------------------------
EMP_TEL          DNO         SALARY      SEX  BIRTH   JOIN_DATE    STATUS  
-----------------------------------------------------------------------------------
1           Moon                  Chan-seung            CEO              
01195662365      3002                    M                       R  
2           Davenport             Susan                 designer         
0113654540                   1500        F  721219  18-NOV-2009  H  
3           Kobain                Ken                   engineer         
0162581369       1001        2000        M  650226  11-JAN-2010  H
.
.
.
20 rows selected.
```



#### SET COLSIZE

When the results of a SELECT statement are output, sets the number of characters from a column of type CHAR or VARCHAR to display so that columns containing long lines of text can be easily viewed.

```
iSQL> CREATE TABLE LOCATION(
ID      INTEGER,
NAME    CHAR(20),
ADDRESS VARCHAR(500),
PHONE   CHAR(20));
Create success.
iSQL> INSERT INTO LOCATION VALUES(1, 'ALTIBASE', 'Inyoung Bldg, 5fl 44-11 Youido-dong Youngdungpo-qu seoul, 150-890. Korea', '82-2-769-7500');
1 row inserted.
```

In the following example, the number of characters of a column of type CHAR or VARCHAR is set to 7:

```
iSQL> SET COLSIZE 7;
iSQL> SELECT ID,NAME,ADDRESS,PHONE FROM LOCATION;
ID          NAME     ADDRESS  PHONE    
--------------------------------------------
1           ALTIBAS  10Fl.,   82-2-20  
            E        Daerung  82-1000  
                     post-to           
                     wer II,           
                      Guro-d           
                     ong, Gu           
                     ro-qu,            
                     Seoul 1           
                     52-790.           
                      Korea            
1 row selected.
```



#### SET NUM[WIDTH]

This command sets the number of characters to display for data of NUMERIC, DECIMAL, NUMBER, and FLOAT columns in SELECT result sets. Data with many significant digits can be made more legible by setting this value high. 

The following example sets NUMWIDTH to 30, and then queries NUMERIC, DECIMAL, NUMBER, and FLOAT columns.

```
iSQL> CREATE TABLE t1
(
c_numeric NUMERIC(38, 0),
c_decimal DECIMAL(38, 0),
c_number NUMBER(38, 0),
c_float FLOAT(38)
);
Create success.
iSQL> INSERT INTO t1 VALUES(12345678901234567890, 12345678901234567890, 12345678901234567890, 12345678901234567890);
1 row inserted.
iSQL> SET NUMWIDTH 30
iSQL> SELECT c_numeric, c_decimal, c_number, c_float FROM t1;
C_NUMERIC C_DECIMAL
-----------------------------------------------------------
C_NUMBER C_FLOAT
-----------------------------------------------------------
12345678901234567890 12345678901234567890
12345678901234567890 12345678901234567890
1 row selected.
```



#### SET NUMF[ORMAT]

##### Syntax

```
SET NUMF[ORMAT] format;
```

This command sets a format of NUMERIC, DECIMAL, NUMBER, and FLOAT type to display their SELECT results. It will take precedence over SET NUMWIDTH settings. 

Refer to the "*General Reference> Data Types > Numeric Data Types > Numeric*" in order to grasp on the formatting on format. 

The following is an example of viewing through an exponential form.

```
iSQL> create table t1(i1 float(30));
Create success.
iSQL> insert into t1 values (123456789012);
1 row inserted.
iSQL> SET NUMFORMAT 9.99EEEE
iSQL> select * from t1;
T1.I1
-------------
  1.23E+11
1 rows selected.
```



#### CL[EAR] COL[UMNMS]

This command releases the display format of all of the columns which have been specified by COLUMN commands. 

##### Syntax

```
CL[EAR] COL[UMNS]
```



#### COLUMN

This command verifies or sets the display format for a target column of SELECT. The setting is applied to the following cases only. 

-   The length of character data type. 
-   The display format of numeric data type.

##### Syntax

```
COL[UMN] [{column | expr} [option]]
```

column or expr should be indicating a target column or an expression, and it should be identical with the one used in the SELECT statement. Every specified column or the specified format can be confirmed by the COL[UMN] [{column | expr}] command. 

The followings can be used in option.

| Option          | Description                                                  |
| --------------- | ------------------------------------------------------------ |
| CLE[AR]         | This option releases a specified column.                     |
| FOR[MAT] format | This option sets the display format for the specified column <br/>The character data type column: This type can set the display length of the CHAR and VARCHAR type. It will take precedence over SET COLSIZE settings. <br />The numeric data type column: The display format of the NUMBER, DECIMAL, FLOAT, and NUMERIC type can be specified by this option.<br />Refer to "General Reference > Data Types > Numeric Data Types > Numeric " for the available format which can be applied into. It will take precedence over SET NUMFORMAT settings. |
| ON\|OFF         | This option confirms whether or not to apply the specified display.<br/>OFF: OFF leaves the column setting as it is, however; it is not applied to output <br />ON : The specified setting is applied. |

##### Description

The display format of a target column in the SELECT statement can be specified. If multiple display formats are selected, the last format will be applied. 

In order to release the display format, the user can use the CLEAR or OFF option. The differences between the CLEAR and OFF option is that the CLEAR option can completely remove the specified display setting whereas the OFF option executes the same except it is not applied to output

##### Example

The following example demonstrates displaying the length of an address column in VARCHAR(60) with 20.

```
iSQL> @schema.sql
iSQL> COLUMN address FORMAT A20
iSQL> select cno, address from customers;
CNO                  ADDRESS
----------------------------------------------
1                    2100 Exposition Boul
                     evard Los Angeles US
                     A
...
```

The following commands should be taken in order to delete the given setting.

```
iSQL> COLUMN address CLE
```



###  Setting Output Options

#### Getting the Elapsed Time

This function displays the time it took to execute the SQL statement.

```
iSQL> SET TIMING ON;	  -> Output the execution time in the last line after the command is executed.
iSQL> SELECT * FROM employees;
ENO         E_LASTNAME            E_FIRSTNAME           EMP_JOB          
------------------------------------------------------------------------------
EMP_TEL          DNO         SALARY      SEX  BIRTH   JOIN_DATE    STATUS  
-----------------------------------------------------------------------------------
1           Moon                  Chan-seung            CEO              
01195662365      3002                    M                       R  
2           Davenport             Susan                 designer         
0113654540                   1500        F  721219  18-NOV-2009  H
.
.
.
20 rows selected.
elapsed time : 0.01
iSQL> SET TIMING OFF;	-> Execution time is not displayed.
```



#### Setting Execution Time Units for Output

This function sets the units with which to output SQL statement execution time. Can be set to the following units:

-   Seconds 
-   Milliseconds 
-   Microseconds 
-   Nanoseconds

```
iSQL> SET TIMING ON
iSQL> SET TIMESCALE SEC;
iSQL> SELECT * FROM employees;
ENO         E_LASTNAME            E_FIRSTNAME           EMP_JOB          
------------------------------------------------------------------------------
EMP_TEL          DNO         SALARY      SEX  BIRTH   JOIN_DATE    STATUS  
-----------------------------------------------------------------------------------
1           Moon                  Chan-seung            CEO              
01195662365      3002                    M                       R
...
20 rows selected.
elapsed time : 0.00

iSQL> SET TIMESCALE MILSEC;
iSQL> SELECT * FROM employee;
ENO         E_LASTNAME            E_FIRSTNAME           EMP_JOB          
------------------------------------------------------------------------------
EMP_TEL          DNO         SALARY      SEX  BIRTH   JOIN_DATE    STATUS  
-----------------------------------------------------------------------------------
1           Moon                  Chan-seung            CEO              
01195662365      3002                    M                       R
...
...
20 rows selected.
elapsed time : 0.72

iSQL> SET TIMESCALE MICSEC;
iSQL> SELECT * FROM employee;
ENO         E_LASTNAME            E_FIRSTNAME           EMP_JOB          
------------------------------------------------------------------------------
EMP_TEL          DNO         SALARY      SEX  BIRTH   JOIN_DATE    STATUS  
-----------------------------------------------------------------------------------
1           Moon                  Chan-seung            CEO              
01195662365      3002                    M                       R
...
20 rows selected.
elapsed time : 966.00

iSQL> SET TIMESCALE NANSEC;
iSQL> SELECT * FROM employee;
NO         E_LASTNAME            E_FIRSTNAME           EMP_JOB          
------------------------------------------------------------------------------
EMP_TEL          DNO         SALARY      SEX  BIRTH   JOIN_DATE    STATUS  
-----------------------------------------------------------------------------------
1           Moon                  Chan-seung            CEO              
01195662365      3002                    M                       R
...
20 rows selected.
elapsed time : 681000.00
```



#### Describing Foreign Key Information

This function displays information on foreign keys when the DESC command is used to view the table structure.

```
iSQL> SET FOREIGNKEYS ON; 	-> The foreign key information will be output.
iSQL> DESC employees;
[ TABLESPACE : SYS_TBS_MEM_DATA ]
[ ATTRIBUTE ]                                                         
------------------------------------------------------------------------------
NAME                                     TYPE                        IS NULL
------------------------------------------------------------------------------
ENO                                      INTEGER         FIXED       NOT NULL
E_LASTNAME                               CHAR(20)        FIXED       NOT NULL
E_FIRSTNAME                              CHAR(20)        FIXED       NOT NULL
EMP_JOB                                  VARCHAR(15)     FIXED       
EMP_TEL                                  CHAR(15)        FIXED       
DNO                                      SMALLINT        FIXED       
SALARY                                   NUMERIC(10, 2)  FIXED       
SEX                                      CHAR(1)         FIXED       
BIRTH                                    CHAR(6)         FIXED       
JOIN_DATE                                DATE            FIXED       
STATUS                                   CHAR(1)         FIXED       
[ INDEX ]                                                       
------------------------------------------------------------------------------
NAME                                     TYPE     IS UNIQUE     COLUMN
------------------------------------------------------------------------------
__SYS_IDX_ID_238                         BTREE    UNIQUE        ENO ASC
EMP_IDX1                                 BTREE                  DNO ASC
[ PRIMARY KEY ]                                                 
------------------------------------------------------------------------------
ENO

[ FOREIGN KEYS ]                                         
----------------------------------------------------------------------

iSQL> SET FOREIGNKEYS OFF; 	-> The foreign key information will not be output.
iSQL> DESC employees;
[ ATTRIBUTE ]                                                         
------------------------------------------------------------------------------
NAME                                     TYPE                        IS NULL
------------------------------------------------------------------------------
ENO                                      INTEGER         FIXED       NOT NULL
E_LASTNAME                               CHAR(20)        FIXED       NOT NULL
E_FIRSTNAME                              CHAR(20)        FIXED       NOT NULL
EMP_JOB                                  VARCHAR(15)     FIXED       
EMP_TEL                                  CHAR(15)        FIXED       
DNO                                      SMALLINT        FIXED       
SALARY                                   NUMERIC(10, 2)  FIXED       
SEX                                      CHAR(1)         FIXED       
BIRTH                                    CHAR(6)         FIXED       
JOIN_DATE                                DATE            FIXED       
STATUS                                   CHAR(1)         FIXED       
[ INDEX ]                                                       
------------------------------------------------------------------------------
NAME                                     TYPE     IS UNIQUE     COLUMN
------------------------------------------------------------------------------
__SYS_IDX_ID_238                         BTREE    UNIQUE        ENO ASC
EMP_IDX1                                 BTREE                  DNO ASC
[ PRIMARY KEY ]                                                 
----------------------------------------------------------------------
ENO
```



#### Describing CHECK constraints Information

This function displays information on CHECK constraints when the DESC command is used to view the table structure.

```
iSQL> SET CHKCONSTRAINTS ON;        -> Check Constraint information is output. 
iSQL> DESC employees;
[ TABLESPACE : SYS_TBS_MEM_DATA ]
[ ATTRIBUTE ]
------------------------------------------------------------------------------
NAME                                     TYPE                        IS NULL
------------------------------------------------------------------------------
ENO                                      INTEGER         FIXED       NOT NULL
E_LASTNAME                               CHAR(20)        FIXED       NOT NULL
E_FIRSTNAME                              CHAR(20)        FIXED       NOT NULL
EMP_JOB                                  VARCHAR(15)     FIXED       
EMP_TEL                                  CHAR(15)        FIXED       
DNO                                      SMALLINT        FIXED       
SALARY                                   NUMERIC(10, 2)  FIXED       
SEX                                      CHAR(1)         FIXED       
BIRTH                                    CHAR(6)         FIXED       
JOIN_DATE                                DATE            FIXED       
STATUS                                   CHAR(1)         FIXED       
[ INDEX ]                                                       
------------------------------------------------------------------------------
NAME                                     TYPE     IS UNIQUE     COLUMN
------------------------------------------------------------------------------
__SYS_IDX_ID_238                         BTREE    UNIQUE        ENO ASC
EMP_IDX1                                 BTREE                  DNO ASC
[ PRIMARY KEY ]                                                 
------------------------------------------------------------------------------
ENO

[ CHECK CONSTRAINTS ]
------------------------------------------------------------------------------
NAME      : EMP_CHECK_SEX1
CONDITION : SEX in ('M', 'F')

iSQL> SET CHKCONSTRAINTS OFF;       ->  Check Constraint information is not output.
iSQL> DESC employees;
[ TABLESPACE : SYS_TBS_MEM_DATA ]
[ ATTRIBUTE ]
------------------------------------------------------------------------------
NAME                                     TYPE                        IS NULL
------------------------------------------------------------------------------
ENO                                      INTEGER         FIXED       NOT NULL
E_LASTNAME                               CHAR(20)        FIXED       NOT NULL
E_FIRSTNAME                              CHAR(20)        FIXED       NOT NULL
EMP_JOB                                  VARCHAR(15)     FIXED       
EMP_TEL                                  CHAR(15)        FIXED       
DNO                                      SMALLINT        FIXED       
SALARY                                   NUMERIC(10, 2)  FIXED       
SEX                                      CHAR(1)         FIXED       
BIRTH                                    CHAR(6)         FIXED       
JOIN_DATE                                DATE            FIXED       
STATUS                                   CHAR(1)         FIXED       
[ INDEX ]                                                       
------------------------------------------------------------------------------
NAME                                     TYPE     IS UNIQUE     COLUMN
------------------------------------------------------------------------------
__SYS_IDX_ID_238                         BTREE    UNIQUE        ENO ASC
EMP_IDX1                                 BTREE                  DNO ASC
[ PRIMARY KEY ]                                                 
------------------------------------------------------------------------------
ENO
```



#### Outputting the partition information

This function allows to view partition information when viewing the table structure with the DESC command.

```
iSQL> create table t1_range(
c1 integer,
c2 integer,
c3 varchar(4))
PARTITION BY RANGE(c3)
(
PARTITION P_2000 VALUES LESS THAN ('2001') TABLESPACE sys_tbs_disk_data,
PARTITION P_2001 VALUES LESS THAN ('2002') TABLESPACE sys_tbs_mem_data,
PARTITION P_DEFAULT VALUES DEFAULT
) tablespace SYS_TBS_DISK_DATA;

iSQL> SET PARTITIONS ON; -> This command outputs the partition information.
iSQL> DESC t1_range
[ TABLESPACE : SYS_TBS_DISK_DATA ]
[ ATTRIBUTE ]
----------------------------------------------------
NAME               TYPE              IS NULL               ----------------------------------------------------
C1                 INTEGER                                  
C2                 INTEGER                                  
C3                 VARCHAR(4)                               
T1_RANGE has no index                                     
T1_RANGE has no primary key                              
[ PARTITIONS ]
----------------------------------------------------
Method: Range                                               
Key column(s)                                                
----------------------------------------
NAME                                            
----------------------------------------
C3
Values
----------------------------------------------------
PARTITION NAME        MIN VALUE          MAX VALUE      
----------------------------------------------------
P_2000                                        '2001'
P_2001                  '2001'               '2002'
P_DEFAULT              '2002'                         
Tablespace
---------------------------------------------------
PARTITION NAME                    TABLESPACE NAME
---------------------------------------------------
P_2000                              SYS_TBS_DISK_DATA
P_2001                              SYS_TBS_MEM_DATA
P_DEFAULT                          SYS_TBS_DISK_DATA
iSQL> SET PARTITIONS OFF;       -> This command does not output the partition information.
iSQL> DESC t1_range
[ TABLESPACE : SYS_TBS_DISK_DATA ]
[ ATTRIBUTE ]
----------------------------------------------------
NAME                      TYPE               IS NULL      
----------------------------------------------------
C1                       INTEGER
C2                       INTEGER
C3                       VARCHAR(4)
T1_RANGE has no index
T1_RANGE has no primary key
```



####  Outputting the Execution Results and Commands of Script Files

The SET TERM and SET ECHO commands determine whether or not to output the execution results and commands of script files to the screen. 

Script execution results are output(TERM ON) by default. If the TERM option is set to OFF, the commands which are executed and the results that are generated when the script file is executed in iSQL are not output to the screen. Even if the TERM option is set to OFF, however, query results are output to the screen if queries are manually input(e.g., iSQL> select * from t1;). Only when script commands are used(e.g., iSQL> @t.sql ), are the results not output to the screen. 

Even if the TERM option is set to OFF, the commands executed in the script can be output by setting the ECHO command to ON. 

The following example outputs the execution results of a script file.

```
iSQL> SET TERM ON;       -> Outputs the script execution result.
iSQL> @schema.sql
iSQL> ALTER SESSION SET AUTOCOMMIT = TRUE;	  -> Beginning of the result.
Alter success.
iSQL> DROP TABLE ORDERS;
Drop success.
elapsed time : 0.00
iSQL> DROP TABLE EMPLOYEES;
Drop success.
elapsed time : 0.00
.
.
.
iSQL> CREATE INDEX ODR_IDX3 ON ORDERS (GNO ASC);
Create success.
elapsed time : 0.00	  -> End of the result.
```

The following example demonstrates how the commands in the script that is executed with @ can be output, although the TERM option is set to OFF, by setting the ECHO option to ON. 

```
iSQL> SET TERM OFF;          -> The script execution results are not output. 
iSQL> @schema.sql
iSQL> SELECT eno, e_firstname, e_lastname FROM employees;
	->  The result is output when the query is manually input.
ENO         E_FIRSTNAME           E_LASTNAME
------------------------------------------------------------
1           Chan-seung            Moon
2           Susan                 Davenport
3           Ken                   Kobain
4           Aaron                 Foster
5           Farhad                Ghorbani
.
.
.
iSQL> SET ECHO ON;	-> Only the commands in the script that is executed with @ are output.
iSQL> @schema.sql
ALTER SESSION SET AUTOCOMMIT = TRUE;
DROP TABLE ORDERS;
DROP TABLE EMPLOYEES;
.
.
.
iSQL> CREATE INDEX ODR_IDX3 ON ORDERS (GNO ASC);
Create success.
elapsed time : 0.00	  -> End of the result
```



#### Outputting an Execution Plan

In iSQL, an execution plan can be output to fine-tune SQL statements. Using an execution plan, DML statements such as SELECT, INSERT, UPDATE and DELETE can be checked. 

In order to accomplish this, the following command must be executed before a statement such as a SELECT statement is executed.

```
ALTER SESSION SET EXPLAIN PLAN = option;
```

This option can be set to ON, OFF, or ONLY. The default is OFF. 

-   ON: After the SELECT statement is executed, the execution plan information is displayed along with the resultant records. 

-   ONLY: The SELECT statement is prepared but not executed, and only the execution plan information is output.This can be used to check the execution plan for a SELECT statement that involves host variable binding, or to quickly check the execution plan for queries that take a long time to execute.
  
-   OFF: After the SELECT statement is executed, only the resultant records are displayed.

The following command is used to obtain detailed information about how conditions included in WHERE clauses written by the user will be execute:

```
ALTER SYSTEM SET TRCLOG_DETAIL_PREDICATE = 1;
```

If this property is set to 1, signifying “ON”, as in the above statement, the execution plan’s WHERE clause conditions, including FIXED KEY RANGE, VARIBALE KEY RANGE and FILTER, are classified and displayed in detail. Therefore, if the WHERE clause is complicated, the user can check which predicates will be executed by scanning the sorted indexes. However, this information may not be output if queries are changed to optimize them in some way.

The following example shows the output when the given SQL statement is executed:

-   When TRCLOG_DETAIL_PREDICATE has been set to 1 (=on), and EXPLAIN PLAN = ON, the following is output in addition to the results.

```
iSQL> alter system set trclog_detail_predicate = 1;
Alter success.
iSQL> alter session set explain plan = on;
Alter success.
iSQL> SELECT eno, e_lastname, e_firstname FROM employees WHERE eno = 1;
ENO         E_LASTNAME            E_FIRSTNAME
------------------------------------------------------------
1           Moon                  Chan-seung
1 row selected.
------------------------------------------------------------
PROJECT ( COLUMN_COUNT: 3, TUPLE_SIZE: 48 )
 SCAN ( TABLE: EMPLOYEES, INDEX: __SYS_IDX_ID_238, ACCESS: 1, SELF_ID: 2 )
  [ FIXED KEY ]
  AND
   OR
    ENO = 1
------------------------------------------------------------
```



-   When TRCLOG_DETAIL_PREDICATE is not set to 1, and EXPLAIN PLAN = ON, the following is output in addition to the results.

```
iSQL> ALTER SYSTEM SET TRCLOG_DETAIL_PREDICATE = 0;
Alter success.
iSQL> ALTER SESSION SET EXPLAIN PLAN = ON;
Alter success.
iSQL> SELECT eno, e_lastname, e_firstname FROM employees WHERE eno = 1;
ENO         E_LASTNAME            E_FIRSTNAME
------------------------------------------------------------
1           Moon                  Chan-seung
1 row selected.
------------------------------------------------------------
PROJECT ( COLUMN_COUNT: 3, TUPLE_SIZE: 48 )
 SCAN ( TABLE: EMPLOYEES, INDEX: __SYS_IDX_ID_238, ACCESS: 1, SELF_ID: 2 )
------------------------------------------------------------
```



-   When TRCLOG_DETAIL_PREDICATE is not set to 1, and EXPLAIN PLAN = ONLY, only the following is output.

```
iSQL> ALTER SYSTEM SET TRCLOG_DETAIL_PREDICATE = 0;
Alter success.
iSQL> ALTER SESSION SET EXPLAIN PLAN = ONLY;
Alter success.
iSQL> SELECT eno, e_lastname, e_firstname FROM employees WHERE eno = 1;
ENO         E_LASTNAME            E_FIRSTNAME
------------------------------------------------------------
No rows selected.
------------------------------------------------------------
PROJECT ( COLUMN_COUNT: 3, TUPLE_SIZE: 48 )
 SCAN ( TABLE: EMPLOYEES, INDEX: __SYS_IDX_ID_238, ACCESS: ??, SELF_ID: 2 )
------------------------------------------------------------
```

If EXPLAIN PLAN = ONLY, because only an execution plan is created and the query is not executed, values that would be determined after actual execution are indicated using question marks (“??”), like an ACCESS clause.

#### Setting Result Output Orientation

When querying data using a SELECT statement in iSQL, the results can be displayed either horizontally or vertically.

This function is suitable for outputting results that comprise a small number of rows and many columns. If such a result set is output horizontally, as is usually the case, it is difficult to compare columns and check the values. However, it is easy to see when output vertically.

```
iSQL>SET VERTICAL ON;         -> This sets the print direction vertically.
iSQL> SELECT * FROM employees WHERE eno = 2;
ENO         : 2
E_LASTNAME  : Davenport
E_FIRSTNAME : Susan
EMP_JOB     : designer
EMP_TEL     : 0113654540
DNO         :
SALARY      : 1500
SEX         : F
BIRTH       : 721219
JOIN_DATE   : 18-NOV-2009
STATUS      : H

1 row selected.
```



### Viewing iSQL Display Settings

The following is an example of viewing the values of the iSQL environment variables for the current session:

```
iSQL> SHOW USER	 -> This is the current user.
User : SYS
iSQL> SHOW COLSIZE
ColSize  : 0
iSQL> SHOW LOBOFFSET
LobOffset: 0
iSQL> SHOW LINESIZE
Linesize : 100
iSQL> SHOW LOBSIZE
LobSize  : 80
iSQL> SHOW NUMWIDTH
NumWidth : 11
iSQL> SHOW PAGESIZE
Pagesize : 0
iSQL> SHOW TIMESCALE
TimeScale : Second
iSQL> SHOW HEADING
Heading : On
iSQL> SHOW TIMING
Timing : Off
iSQL> SHOW VERTICAL
Vertical  : Off
iSQL> SHOW CHKCONSTRAINTS
ChkConstraints : Off
iSQL> SHOW FOREIGNKEYS
ForeignKeys : Off
iSQL> SHOW PLANCOMMIT
PlanCommit : Off
iSQL> SHOW QUERYLOGGING
QueryLogging : Off
iSQL> SHOW TERM
Term : On
iSQL> SHOW ECHO
Echo : OFF
iSQL> SHOW FEEDBACK
Feedback : 1
iSQL> SHOW ALL
User      : SYS
ColSize   : 0
LobOffset : 0
LineSize  : 80
LobSize   : 80
NumWidth : 11
PageSize  : 0
TimeScale : Second
Heading   : On
Timing    : Off
Vertical  : Off
ChkConstraints : Off
ForeignKeys : Off
Partitions : Off
PlanCommit : Off
QueryLogging : Off
Term : On
Echo : Off
Feedback : 1
Fullname : Off
Sqlprompt : "iSQL> "
Define : Off
```



### Host Variables

Host variables are first declared and then used. Host variables are useful when executing procedures or functions.

#### Declaring a Host Variable

##### Syntax

```
VAR[IABLE] var_name[INPUT|OUTPUT|INOUTPUT] var_type
```

The default value is automatically given unless INPUT, OUTPUT or INOUTPUT is specified.

##### Type

The following types can be used when declaring variables:

```
INTEGER, BYTE(n), NIBBLE(n),
NUMBER, NUMBER(n), NUMBER(n,m),
NUMERIC, NUMERIC(n), NUMERIC(n,m),
CHAR(n), VARCHAR(n), NCHAR(n), NVARCHAR(n), DATE
DECIMAL, DECIMAL(n), DECIMAL(n,m),
FLOAT, FLOAT(n), DOUBLE, REAL
BIGINT, SMALLINT
```



##### Example

The following examples demonstrate how to declare variables:

```
iSQL> VAR p1 INTEGER
iSQL> VAR p2 CHAR(10)
iSQL> VAR v_double DOUBLE
iSQL> VAR v_real REAL
```



#### Assigning a Value to a Host Variable

##### Syntax

```
EXEC[UTE] :var_name := value;
```



##### Example

The following example shows how to assign a value to a variable:

```
iSQL> EXECUTE :p1 := 100;
Execute success
iSQL> EXEC :p2 := ‘abc’;
Execute success
```



#### Viewing Host Variables

##### Syntax

```
PRINT VAR[IABLE]
```

Shows all declared variables.

```
PRINT var_name
```

Shows the type and value of the variable var_name.

##### Example

The following shows the values of all declared variable:

```
iSQL> PRINT VAR
[ HOST VARIABLE ]
-------------------------------------------------------
NAME                 TYPE                 VALUE
-------------------------------------------------------
P1                   INTEGER              100
P2                   CHAR(10)             abc
V_REAL               REAL                
V_DOUBLE             DOUBLE
iSQL> PRINT p2 	-> Outputs only variable p2 information.
NAME                TYPE                   VALUE
-------------------------------------------
P2                  CHAR ( 10 )            abc
```



### Executing Prepared SQL Statements

#### Prepared SQL versus Dynamic SQL Statements

SQL statements executed in iSQL are usually executed according to the so-called “Direct Execution” method. 

In Direct Execution, syntax analysis, validity testing, optimization and execution of a query are all performed at once. However, in Prepared Execution, only the syntax analysis, validity testing, and optimization of the query are performed to set up an execution plan for the query, which is then executed when requested by the client. When creating an application that uses ODBC, the Prepared Execution method is typically used, and is more advantageous in terms of speed when a SQL statement is to be repeatedly executed using host variable binding. 

In iSQL, the difference between these two methods lies only in whether variables are used or not; there is no advantage in terms of speed. However, when it is executed in Prepared Execution, the printed graph and the execution plan may contain different information. The graph shows the plan up until the optimization phase, whereas execution plan shows the plan once the actual value is applied to the variable.

#### Prepared SQL Statements

##### Syntax

```
PREPARE SQL_statement;
```



##### Example

The following is an example of the use of the PREPARE command to execute a SQL statement:

```
iSQL> VAR t1 INTEGER;
iSQL> EXEC :t1 := 1;
Execute success.
iSQL> PREPARE SELECT eno, e_firstname, e_lastname, sex
FROM employees WHERE eno=:t1;
ENO         E_FIRSTNAME           E_LASTNAME            SEX
------------------------------------------------------------------
1           Chan-seung            Moon                  M
1 row selected.
```



### Creating, Executing, and Dropping Stored Procedures

#### Creating Procedures

Support is provided for the creation and execution of stored procedures. A stored procedure must end with the following:

```
END;
/
```

Successful creation of the procedures can be confirmed by checking the sys_procedures_ meta table.

#### Executing Procedures

Procedures are executed in order to execute multiple queries at one time. If the procedure to be executed has parameters, as many variables as there are parameters must be declared before the procedure is executed.

##### Example 1

In the following example, a procedure named emp_proc, which executes an INSERT statement using IN parameters, is created:

```
iSQL> CREATE OR REPLACE PROCEDURE emp_proc(p1 IN INTEGER, p2 IN CHAR(20), p3 IN CHAR(20), p4 IN CHAR(1))
 AS
 BEGIN
 INSERT INTO employees(eno, e_firstname, e_lastname, sex)
 VALUES(p1, p2, p3, p4);
 END;
 /
Create success.
iSQL> SELECT * FROM system_.sys_procedures_ order by created desc limit 1;
USER_ID     PROC_OID
------------------------------------
PROC_NAME                                 OBJECT_TYPE STATUS
----------------------------------------------------------------------
PARA_NUM    RETURN_DATA_TYPE RETURN_LANG_ID RETURN_SIZE
-------------------------------------------------------------
RETURN_PRECISION RETURN_SCALE PARSE_NO    PARSE_LEN   CREATED
-------------------------------------------------------------------------
LAST_DDL_TIME
----------------
2           3208680
EMP_PROC                                  0           0
4
                        2           192         29-FEB-2012
29-FEB-2012
1 row selected.
```

emp_proc, which was created above, is executed:

```
iSQL> VAR eno INTEGER
iSQL> VAR first_name CHAR(20)
iSQL> VAR last_name CHAR(20)
iSQL> VAR sex CHAR(1)
iSQL> EXECUTE :eno := 21;
Execute success.
iSQL> EXECUTE :first_name := 'Joel';
Execute success.
iSQL> EXECUTE :last_name := 'Johnson';
Execute success.
iSQL> EXECUTE :sex := 'M';
Execute success.
iSQL> EXECUTE emp_proc(:eno, :first_name, :last_name, :sex);
Execute success.
iSQL> SELECT eno, e_firstname, e_lastname, sex FROM employees WHERE eno = 21;
ENO         E_FIRSTNAME           E_LASTNAME            SEX  
-----------------------------------------------------------------
21          Joel                  Johnson               M
1 row selected.
```



##### Example 2

In the following example, a procedure called outProc, which executes a SELECT statement, is created:

```
iSQL> CREATE TABLE outTbl(i1 INTEGER, i2 INTEGER);
Create success.
iSQL> INSERT INTO outTbl VALUES(1,1);
1 row inserted.
iSQL> /
1 row inserted.
iSQL> /
1 row inserted.
iSQL> /
1 row inserted.
iSQL> /
1 row inserted.
iSQL> SELECT * FROM outTbl;
OUTTBL.I1   OUTTBL.I2   
---------------------------
1           1           
1           1           
1           1           
1           1           
1           1           
5 rows selected.
iSQL> CREATE OR REPLACE PROCEDURE outProc(a1 OUT INTEGER, a2 IN OUT INTEGER)
AS
BEGIN
  SELECT COUNT(*) INTO a1 FROM outTbl WHERE i2 = a2;
END;
/
Create success.
```

In the following example, outProc is executed:

```
iSQL> VAR t3 INTEGER
iSQL> VAR t4 INTEGER
iSQL> EXEC :t4 := 1;
Execute success.
iSQL> EXEC outProc (:t3, :t4);
Execute success.
iSQL> PRINT t3;
NAME                 TYPE                 VALUE
-----------------------------------------------
T3                   INTEGER              5                  
```



##### Example 3

In the following example, the procedure outProc1 is created:

```
iSQL> CREATE OR REPLACE PROCEDURE outProc1( p1 INTEGER, p2 IN OUT INTEGER, p3 OUT INTEGER)
AS
BEGIN
  p2 := p1;
  p3 := p1 + 100;
END;
/
Create success.
iSQL> VAR v1 INTEGER
iSQL> VAR v2 INTEGER
iSQL> VAR v3 INTEGER
iSQL> EXEC :v1 := 3;
Execute success.
iSQL> EXEC outProc1(:v1, :v2, :v3);
Execute success.
iSQL> PRINT VAR;
[ HOST VARIABLE ]
-----------------------------------------------
NAME                 TYPE                 VALUE
-----------------------------------------------
..
V1                   INTEGER              3
V2                   INTEGER              3
V3                   INTEGER              103
..
```



##### Example 4

In the following example, a procedure called inoutProc1, which executes a SELECT statement, is created:

```
iSQL> CREATE TABLE inoutTbl(i1 INTEGER);
Create success.
iSQL> INSERT INTO inoutTbl VALUES(1);
1 row inserted.
iSQL> /
1 row inserted.
iSQL> /
1 row inserted.
iSQL> SELECT * FROM inoutTbl;
INOUTTBL.I1
--------------
1           
1           
1           
3 rows selected.
iSQL> CREATE OR REPLACE PROCEDURE inoutProc (a1 IN OUT INTEGER)
AS
BEGIN
  SELECT COUNT(*) INTO a1 FROM inoutTbl WHERE i1 = a1;
END;
/
Create success.
iSQL> VAR t3 INTEGER
iSQL> EXEC :t3 := 1;
Execute success.
iSQL> EXEC inoutProc(:t3);
Execute success.
iSQL> PRINT t3;
NAME                 TYPE                 VALUE
-----------------------------------------------
T3                   INTEGER              3
```



##### Example 5

In the following example, the procedure inoutProc1 is created:

```
iSQL> CREATE OR REPLACE PROCEDURE inoutProc1( p1 INTEGER, p2 IN OUT INTEGER, p3 OUT INTEGER)
AS
BEGIN
  p2 := p1 + p2;
  p3 := p1 + 100;
END;
/
Create success.
```

In the following example, the procedure inoutProc1 is executed:

```
iSQL> VAR v1 INTEGER
iSQL> VAR v2 INTEGER
iSQL> VAR v3 INTEGER
iSQL> EXEC :v1 := 3;
Execute success.
iSQL> EXEC :v2 := 5;
Execute success.
iSQL> EXEC inoutProc1(:v1, :v2, :v3);
Execute success.
iSQL> PRINT VAR;
[ HOST VARIABLE ]
-----------------------------------------------
NAME                 TYPE                 VALUE
-----------------------------------------------
..
V1                   INTEGER              3
V2                   INTEGER              8
V3                   INTEGER              103
..
```



#### Dropping Procedures

The DROP command is used to drop (delete) procedures. 

In the following example, the procedure emp_proc is deleted:

```
iSQL> DROP PROCEDURE emp_proc;
Drop success
```



### Creating, Executing ,and Dropping Functions

#### Creating Functions

A function is provided to create functions. When creating a function, you must end with the following syntax, and the return type must be defined.

```
END;
/
```

Successful creation of the function can be confirmed by checking the sys_procedures_ meta table. 

In the following example, the function emp_func, which executes an UPDATE statement and a SELECT statement, is created:

```
iSQL> CREATE OR REPLACE FUNCTION emp_func(f1 IN INTEGER)
RETURN NUMBER
AS
 f2 NUMBER;
BEGIN
 UPDATE employees SET salary = 1000000 WHERE eno = f1;
 SELECT salary INTO f2 FROM employees WHERE eno = f1;
 RETURN f2;
END;
/
Create success.

iSQL> SELECT * FROM system_.sys_procedures_;
USER_ID     PROC_OID             PROC_NAME                                 
-------------------------------------------------------------------------------
OBJECT_TYPE STATUS      PARA_NUM    RETURN_DATA_TYPE RETURN_LANG_ID
--------------------------------------------------------------------------
RETURN_SIZE RETURN_PRECISION RETURN_SCALE PARSE_NO    PARSE_LEN   
------------------------------------------------------------------------
CREATED      LAST_DDL_TIME
------------------------------
.
.
.
2           3300024              INOUTPROC1                                
0           0           3                                   
                                    2           132         
15-SEP-2010  15-SEP-2010  
2           3302344              EMP_FUNC                                  
1           0           1           6           30000       
23          38          0           3           209         
15-SEP-2010  15-SEP-2010  
36 rows selected.
```



#### Executing Functions

Functions can be executed to simultaneously execute multiple queries. If the function to be executed has parameters, as many variables as there are functions must be declared before the function is executed. Additionally, a variable for saving the result of the function must also be defined. 

The following is an example of executing the function emp_func:

```
iSQL> VAR eno INTEGER
iSQL> VAR ret NUMBER
iSQL> EXEC :eno := 11;
Execute success.
iSQL> EXEC :ret := emp_func(:eno);
Execute success.
iSQL> SELECT eno, salary FROM employees WHERE eno = 11;
ENO         SALARY      
---------------------------
11          1000000     
1 row selected.
```



#### Dropping Functions

The DROP FUNCTION statement is used to drop functions. 

In the following example, the function emp_func is deleted:

```
iSQL> DROP FUNCTION emp_func;
Drop success
```



### Convenient User Functions

#### History

A list of all previously executed commands can be displayed using the HISTORY command. The number corresponding to a previously executed command can be used to easily execute that command again.

```
iSQL> HISTORY;	-> View history list
```

or

```
iSQL> H;		
1 : SELECT * FROM tab;
2 : SELECT * FROM book;
3 : HISTORY;

iSQL> / -> Re-execute the most recent command(HISTORY;))
iSQL> 2/ -> Execute Command number 2 in history list(SELECT * FROM book;)
```

#### History Logging

It saves the commands executed in iSQL to a file when you exit iSQL. Enabling this function loads previous commands stored in the file when iSQL is restarted. Therefore, previous commands are accessible and executable by using the arrow keys on the keyboard.

To use the history logging function, ISQL_HIST_FILE environment variable should be set and iSQL has to be restarted.

```
$ export ISQL_HIST_FILE=~/.isql_history
```

To turn off the history logging function, delete the ISQL_HIST_FILE environment variable.

```
$ unset ISQL_HIST_FILE
```

##### Default Value

Not used

##### Constraints

- This function can only be used  when previous commands are accessible by using the arrow keys on command prompt or shell prompt.
- Maximum 100 commands can be stored.

File access control should be well taken care of when this function is used since every command the user entered is stored in the file, including sensitive information such as user passwords.

#### Shell Commands

The exclamation point (“!”) is a convenient function that allows direct execution of most shell commands from within iSQL.

```
iSQL> !ls -al
total 3417
-rw-r-----   1 wlgml337 section      1198 Nov  1 13:30 .aliases
-rw-------   1 wlgml337 section      5353 Oct 18 21:17 .bash_history
-rw-r-----   1 wlgml337 section      1436 Nov  2 15:42 .bashrc
-rw-r-----   1 wlgml337 section      1549 Dec 13 17:36 .profile
drwxr-x---   2 wlgml337 section       512 Nov  2 02:00 TEMP
drwxr-xr-x   2 root     root          512 Oct 16 11:29 TT_DB
-rw-------   	 1 wlgml337 section   	 3446548 Dec 18 13:19 core
drwxr-x---   2 wlgml337 section       512 Nov 11 16:33 cron
drwxr-x---   2 wlgml337 section       512 Nov 15 10:52 test
drwxr-xr-x   6 wlgml337 section       512 Nov 11 11:45 work
```



#### Command Prompt

The prompt can be modified by configuting other values instead of the fundamental command prompt 'iSQL>'. The SET SQLPROMPT dynamically replaces variables when including runtime variables, such as current accessed user, and current time.

```
SET SQLP[ROMPT] {text}
```

The followings are the substitution variables available for use.

| Variable             | Description                                                  |
| -------------------- | ------------------------------------------------------------ |
| \_CONNECT_IDENTIFIER | The connected server. It is expressed with " host:port_no ". |
| \_DATE               | The current time. It is expressed through a specified format in the DATE_FORMAT. |
| \_PRIVILEGE          | This variable displays the iSQL access privilege. If it is connected with sysdba, '(sysdba)' is replaced. |
| \_USER               | The user name currently being connected.                     |

##### Example

```
iSQL>SET SQLPROMPT "_CONNECT_IDENTIFIER> "

iSQL>SET SQLP "_USER> "

iSQL>SET SQLPROMPT "_USER'@'_CONNECT_IDENTIFIER > "

iSQL>SET SQLPROMPT "_USER on _DATE from _CONNECT_IDENTIFIER> "
```



#### Getting Help

Help is available for the commands provided with iSQL. The HELP command without parameters outputs information on how to use help. For help on specific commands, enter HELP followed by the name of the command for which help is desired.

```
iSQL> HELP;
Use 'help [command]'
Enter 'help index' for a list of command
iSQL> HELP INDEX;
/               EXIT            PARTITIONS
@               EXPLAINPLAN     QUERYLOGGING
ALTER           FEEDBACK        QUIT
AUTOCOMMIT      FOREIGNKEYS     ROLLBACK
CHKCONSTRAINTS  FULLNAME        SAVE
CL[EAR]         H[ISTORY]       SELECT
COL[UMN]        HEADING         SPOOL
COLSIZE         INSERT          SQLP[ROMPT]
COMMIT          LINESIZE        START
CREATE          LOAD            TERM
DEFINE          LOBOFFSET       TIMESCALE
DELETE          LOBSIZE         TIMING
DESC            MERGE           UPDATE
DROP            MOVE            USER
ECHO            NUM[WIDTH]      VAR[IABLE]
EDIT            NUMF[ORMAT]     VERTICAL
EXECUTE         PAGESIZE

iSQL> HELP EXIT;
exit;
or
quit; - exit iSQL
```



### Using National Character Sets

When using NCHAR and NVARCHAR type character constants, if the following environment variables settings are made, there will be no concerns over possible data loss.

The ALTIBASE_NLS_NCHAR_LITERAL_REPLACE environment variable must be set to1.

```
$ export ALTIBASE_NLS_NCHAR_LITERAL_REPLACE =1
```

In order to use NCHAR type data that are encoded differently from the database character set, enter the character “N” in front of the string.

```
iSQL> create table t1 (c1 nvarchar(10));
Create success.
iSQL> insert into t1 values (N'AB가나');
1 row inserted.
iSQL> select * from t1;
C1
------------------------
AB가나
1 row selected.
```
