<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Precompiler User’s Manual](#precompiler-users-manual)
  - [Preface](#preface)
    - [About This Manual](#about-this-manual)
  - [1. The C/C++ Precompiler](#1-the-cc-precompiler)
    - [Introduction and Concepts](#introduction-and-concepts)
    - [Command-Line Options](#command-line-options)
    - [Programming using Embedded SQL Statements](#programming-using-embedded-sql-statements)
  - [2. Host Variables and Indicator Variables](#2-host-variables-and-indicator-variables)
    - [Host Variables](#host-variables)
    - [Classifying Host Variables](#classifying-host-variables)
    - [Indicator Variables](#indicator-variables)
    - [Classifying Indicator Variables](#classifying-indicator-variables)
    - [Meaning of Indicator Variables](#meaning-of-indicator-variables)
    - [Sample Programs](#sample-programs)
  - [3. Host Variable Declaration Section](#3-host-variable-declaration-section)
    - [Host Variable Declaration Section](#host-variable-declaration-section)
    - [Data Type Definition](#data-type-definition)
    - [Function Argument Declaration Section](#function-argument-declaration-section)
  - [4. C Preprocessor](#4-c-preprocessor)
    - [C Preprocessor Overview](#c-preprocessor-overview)
    - [C Preprocessor Directives](#c-preprocessor-directives)
    - [Limitations on the Use of the Preprocessor](#limitations-on-the-use-of-the-preprocessor)
    - [Preprocessor Example](#preprocessor-example)
    - [The ALTIBASE_APRE Macro](#the-altibase_apre-macro)
  - [5. Host Variable Data Types](#5-host-variable-data-types)
    - [Overview](#overview)
    - [Fundamental C/C++ Data Types](#fundamental-cc-data-types)
    - [Extended APRE Data Types](#extended-apre-data-types)
    - [Column and Host Variable Type Conversion](#column-and-host-variable-type-conversion)
  - [6. Embedded SQL Statements](#6-embedded-sql-statements)
    - [Overview](#overview-1)
    - [Connection related SQL statements](#connection-related-sql-statements)
    - [Using DDL and DML in Embedded SQL Statements](#using-ddl-and-dml-in-embedded-sql-statements)
    - [Using Other Embedded SQL Statements](#using-other-embedded-sql-statements)
    - [OPTION Statements](#option-statements)
  - [7. Handling Runtime Errors](#7-handling-runtime-errors)
    - [Overview](#overview-2)
    - [sqlca](#sqlca)
    - [SQLCODE](#sqlcode)
    - [SQLSTATE](#sqlstate)
    - [WHENEVER Statement](#whenever-statement)
    - [Sample Programs](#sample-programs-1)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Altibase® Application Development

Precompiler User’s Manual
=========================

![](media/Precompiler/e5cfb3761673686d093a3b00c062fe7a.png)

Altibase Application Development Precompiler User’s Manual

Release 7.1

Copyright ⓒ 2001\~2020 Altibase Corp. All Rights Reserved.

This manual contains proprietary information of Altibase Corporation; it is provided under a license agreement containing restrictions on use and disclosure and is also protected by copyright patent and other intellectual property law. Reverse engineering of the software is prohibited. All trademarks, registered or otherwise, are the property of their respective owners.

**Altibase Corp**

10F, Daerung PostTower II, 306, Digital-ro, Guro-gu, Seoul 08378, Korea Telephone: +82-2-2082-1000 Fax: 82-2-2082-1099

Customer Service Portal: http://support.altibase.com/en/

Homepage: [[http://www.altibase.com](http://www.altibase.com/)]

Preface
----

### About This Manual

This manual explains how to use the embedded SQL statement of Altibase and C/C++ precompiler. The user can create an application using the embedded SQL statement of Altibase and precompile the created program

#### Audience

This manual has been prepared for the following Altibase users:

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

#### Organization

This manual is organized as follows: 

-   Chapter 1: The C/C++ Precompiler  
    This chapter presents an introduction to the C/C++ precompiler and how to use it, and gives a detailed description of the procedure for writing applications that contain embedded SQL statements.
    
-   Chapter 2: Host Variables and Indicator Variables  
    This chapter describes both host variables and indicator variables, and explains how to interpret the meaning of indicator variables
    
-   Chapter 3: Host Variable Declaration Section  
    This chapter explains both the host variable declaration section and the function argument declaration section

-   Chapter 4: C Preprocessor

-   Chapter 5: Host Variable Data Types  
    This chapter describes the data types that are used for host variables.
    
-   Chapter 6: Embedded SQL Statements  
    This chapter explains how to use embedded SQL statements, including those for managing database connections and executing DDL and DML statements.
    
-   Chapter 7: Handling Runtime Errors  
    This chapter explains how to use the standard variables for handling runtime errors.

-   Chapter 8: Using Cursors  
    This chapter explains the statements used to manage cursors.

-   Chapter 9: Using Arrays in Embedded SQL Statements  
    This chapter covers how to use array-type host variables and discusses arrays of structures and the limitations on their use.

-   Chapter 10: Dynamic SQL Statements  
    This chapter explains dynamic SQL statements.

-   Chapter 11: Using Stored Procedures in C/C++  
    This chapter describes how to use stored functions and stored procedures.

-   Chapter 12: Application with Multiple Database Connections  
    This chapter covers how to write applications that use multiple database connections.

-   Chapter 13: Multithreaded Applications  
    This chapter discusses how to write multithreaded applications.

-   Chapter 14: Error Codes and Messages  
    This chapter explains the APRE error codes and messages.

-   Appendix A. Using Files and LOBs  
    This chapter describes how to use the file system to input or output BLOB and CLOB data.
    
-   Appendix B. Porting ProC Applications to APRE  
    This chapter discusses how to convert applications written with Oracle ProC(C++) to APRE.
    
-   Appendix C. The Method 4 of Dynamic SQL  
    This appendix should be thoroughly comprehended and referred especially when utilizing the method 4 of dynamic SQL since it can insert a value for parameter marker at a time of executing a program.
    
-   Appendix D. Sample Applications  
    This chapter explains the location of the sample applications.
    
-   Appendix E. FAQ  
    This chapter lists frequently asked questions about how to use APRE and embedded SQL statements.

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
| [ ]              | Indicates an optional item                                   | VARCHAR [(*size*)][[FIXED \|] VARIABLE]                      |
| { }              | Indicates a mandatory field for which one or more items must be selected. | { ENABLE \| DISABLE \| COMPILE }                             |
| \|               | A delimiter between optional or mandatory arguments.         | { ENABLE \| DISABLE \| COMPILE } [ ENABLE \| DISABLE \| COMPILE ] |
| . . .            | Indicates that the previous argument is repeated, or that sample code has been omitted. | SQL> SELECT ename FROM employee; ENAME ----------------------- SWNO HJNO HSCHOI . . . 20 rows selected. |
| Other Symbols    | Symbols other than those shown above are part of the actual code.Other Symbols | EXEC :p1 := 1; acc NUMBER(11,2);Symbols other than those shown above are part of the actual code. |
| Italics          | Statement elements in italics indicate variables and special values specified by the user. | SELECT * FROM *table_name*; CONNECT *userID*/*password*;     |
| Lower case words | Indicate program elements set by the user, such as table names, column names, file names, etc. | SELECT ename FROM employee;                                  |
| Upper case words | Keywords and all elements provided by the system appear in upper case. | DESC SYSTEM_.SYS_INDICES_;                                   |

#### Related Documentations

For more detailed information, please refer to the following documents.

-   Installation Guide

-   Administrator’s Manual

-   CLI User's Manual

-   SQL Reference

-   Stored Procedures Manual

-   iSQL User’s Manual

-   Error Message Reference

#### Altibase Welcomes Your Comments and Feedbacks

Please let us know what you like or dislike about our manuals. To help us with better future versions of our manuals, please tell us if there is any corrections or classifications that you would find useful.

Include the following information:

- The name and version of the manual that you are using
- Any comments about the manual
- Your name, address, and phone number

If you need immediate assistance regarding any errors, omissions, and other technical issues, please contact Altibase's Support Portal (http://altibase.com/support-center/en/).

Thank you. We always welcome your feedbacks and suggestions.

## 1. The C/C++ Precompiler

-------------------

### Introduction and Concepts

#### Introduction

APRE (the Altibase C/C++ Precompiler) is a programming tool that accepts source code containing embedded SQL as input, translates the embedded SQL statements into standard runtime library calls, and generates a modified source program that can be compiled in the host language and executed. 

APRE makes it easy for users to write and precompile applications that contain embedded SQL statements.

By embedding SQL statements into applications, users can create applications that have all of the functionality that is available when creating a program using the ODBC API, and can do so much more easily.

#### Precompiler Environment Settings

The following environment settings are required in order to compile and link a file that is output by APRE:

##### Required Header File

-   The ulpLibInterface.h header file is necessary. It is located in the $ALTIBASE_HOME/include directory.
  
-   In order to compile an application that was precompiled with APRE, it will be necessary to use the following option in your C/C++ compiler: -I $ALTIBASE_HOME/include

##### Required Library Files

-   The library files libapre.a and libodbccli.a (or apre.lib and odbccli.lib in Windows) are also necessary. They are located in the $ALTIBASE_HOME/lib directory.
-   In order to link a compiled application program with these libraries, it is necessary to use all of the following options:

```
–L $ALTIBASE_HOME/lib –lapre, –lodbccli, -lpthread
```

> #### Notes:
>
> The Altibase client library is not safe for system signal generation.
>
> Therefore, when the network connection is terminated due to an external cause, an application in progress may be forcibly terminated by receiving a SIGPIPE signal. To prevent this forced termination, the SIGPIPE signal must be handled by the user application. However, a function is called in the Altibase client library while processing SIGPIP signals, it should not call it because the program may stopped.
> 
> However, after signal processing, it is possible to call functions from the Altibase client library.

#### The Precompilation Process

APRE is used to precompile a program that was written in C or C++ and includes embedded SQL statements. It outputs a C or C++ program in which the embedded SQL has been converted into a form that is understandable by the C or C++ compiler. The input file is a text file containing C or C++ source code, and must have the .sc extension. The file output by APRE can have either the .c or .cpp extension. The user can choose the desired filename extension using the -t command-line argument. If this is omitted, the default extension is .c.

##### Executing the Precompile Command

```
apre [ <apre-options> ] <filename>
```

##### APRE Command-Line Options

-   \<*filename*\> : This is a text file that contains C or C++ source code, including embedded SQL statements. The filename extension must be .sc. It is possible to specify more than one file, in which case all of them will be preprocessed individually. When specifying multiple files, the asterisk (“*”) wildcard character is useful.

[Example 1] Precompile a program that was written in C. The precompilation operation creates the sample1.c file.

```
$ apre sample1.sc
```

[Example 2] Precompile multiple programs that were written in C. Note the use of the asterisk (“*”) wildcard character in the second example.

```
$ apre sample1.sc sample2.sc 
$ apre *.sc
```

-   \<*apre-options*\> : APRE*C/C++ command-line options are specified here, before the name of the file(s) to precompile. For details, please refer to the next section,Command-Line Options.

##### Precompile Messages

The screen that is displayed when APRE is executed is shown below.

```
$ apre sample1.sc
--------------------------------------------------------
  APRE C/C++ Precompiler.
  Release Version 7.1.0.0.0
  Copyright 2000, Altibase Corporation or its subsidiaries.
  All rights reserved.
--------------------------------------------------------
```

### Command-Line Options

The following command-line options can be used when precompiling applications. This section explains each of the command-line options in detail.

##### Run option

```
-h
```

When this option is used, the precompile operation is not performed, and APRE help information is displayed. The following screen will be shown:

```
$ apre -h
===========================================================
APRE (Altibase Precompiler) C/C++ Precompiler HELP Screen
===========================================================
Usage  :  apre [<options>] <filename>

-h               : Display this help information.
-t <c|cpp>       : Specify the file extension for the output file.
                   c   - File extension is '.c' (default)
                   cpp - File extension is '.cpp'
-o <output_path> : Specify the directory path for the output file.
                   (default : current directory)
-mt              : When precompiling a multithreaded application,
                   this option must be specified.
-I<include_path> : Specify the directory paths for files included using APRE C/C++.
                   (default : current directory)
-parse <none|partial|full>
                 : Control which non-SQL code is parsed.
-D<define_name>  : Use to define a preprocessor symbol.
-v               : Output the version of APRE.
-n               : Specify when CHAR variables are not null-padded.
-unsafe_null     : Specify to suppress errors when NULL values are fetched
                   and indicator variables are not used.
-align           : Specify when using alignment in AIX.
-spill <values>  : Specify the register allocation spill area size.
-keyword         : Display all reserved keywords.
-debug <macro|symbol>
                 : Use for debugging.
                   macro   - Display macro table.
                   symbol  - Display symbol table.
-nchar_var <variable_name_list>
                 : Process the specified variables using
                   the Altibase national character set.
-nchar_utf16     : Set client nchar encoding to UTF-16.
-lines           : Add #line directives to the generated code.
-silent          : No display Copyright.
================================================
```

#### \-t \<c\|cpp\>

This is used to choose the filename extension of the file created as a result of the APRE precompiling operation. When this option is set to “c”, the filename extension will be “.c”, whereas when this option is set to “cpp”, the filename extension will be “.cpp”. If neither extension is specified, the filename extension will be “.c”.

##### Example

Use the -t option to precompile a program written in C++. After APRE has executed the command, a file named “sample1.cpp” will be created.

```
$ apre –t cpp sample1.sc
```

#### \-o \<output_path\>

This is used to specify the location of the file(s) created by APRE. If this option is omitted, the resultant file(s) will be created in the current directory. Only one path can be specified. That is, when precompiling and creating multiple files, the resultant files must all be created in the same directory. 

#### \-mt

전처리할 파일이 멀티쓰레드 프로그램일 경우, 반드시 이 옵션을 지정하여야 한다. 이
옵션은 각각의 소스 파일(.sc)에 적용할 수 없으므로, 두 개 이상의 소스 파일을
전처리하여 실행 프로그램을 만드는 경우에는 모든 소스 파일에 이 옵션을 적용해야
한다.

```
EXEC SQL OPTION(THREADS=TRUE);
```

This can be replaced with the embedded SQL statement. That is, if the embedded SQL statement is declared within the file which will be precompiled, this option can be omitted. However, in the case of precompiling multiple files, this options is preferentially applied than the embedded SQL. Thus, if this option is selected, the precompiling files are applied all as well. 

Refer refer to Chapter6: Embedded SQL Statements on in-depth information on the OPTION statement.

#### \-I\<include_path\>

This option is used to specify the location(s) of the header file(s) to be used in the precompiling operation. Both absolute and relative paths can be specified. APRE will always look for the header file in the current directory first, followed by the directories specified here. 

In order to specify multiple locations, the -I option can be specified multiple times.

##### Example

Use the -I option to specify the location of header files to be used for precompiling. When this option is specified as shown, APRE will look for the header file in the current directory first, and will then look in the /include directory. 

```
$ apre –I. -I/include sample1.sc
```

#### \-parse \<none\|partial\|full\>

This option is used to specify the range within the source file(s), which are specified within the source code using the #include directive, that is parsed by the precompiler. When this option is not specified, it defaults to partial.

##### none

If this option is set to none, the precompiler processes only the macro commands and host variable declarations that are found within the EXEC SQL BEGIN/END DECLARE SECTION block, and ignores any macro commands and host variable declarations that are not found within that block. However, all embedded SQL statements found within the source file(s) are processed.

##### partial

If this option is set to partial, the precompiler processes all macro commands, but processes only the host variable declarations that are found within the EXEC SQL BEGIN/END DECLARE SECTION block. Additionally, the macro commands that are found in the header files that are included using the #include directive are processed, whereas the host variables found within these files are not. However, as with the none option, all embedded SQL statements found within the source file(s) are processed.

##### full

If this option is set to full, the precompiler executes an internal C parser and processes all host variables, regardless of whether they were declared inside or outside the EXEC SQL BEGIN/END DECLARE SECTION block, and all macro commands. Furthermore, not only all macro commands but also all host variables found within the header files included using the #include directive are also processed. Finally, all embedded SQL statements are then precompiled.

However, since performance loss can occur - regardless of this option being specified - the ALTIBASE precompiler does not parse the system header files that are included using the #include directive. Thus, an error is raised when types defined in the system header files are used as host variables. To avoid this, the user must define the desired type in the $ALTIBASE_HOME/include/aprePredefinedTypes.h file which is provided by Altibase.

In the “*.sc” source file, however, the system header files must be included using the #include directive, instead of the aprePredefinedTypes.h file. This is because the aprePredefinedTypes.h file is automatically referenced at APRE precompilation; at compilation, however, the system header files must be referenced.

> ##### Note:
>
> Because APRE's internal C parser is activated when the -parse option is set to full, an error will be raised if any C++ source code is encountered during the precompile operation. Therefore, when precompiling C++ source code, either avoid the use of the -parse option, or set it to partial or none.

##### Example

```
$ apre -parse none –t cpp sample1.sc
$ apre -parse partial –t cpp sample1.sc
$ apre -parse full –t cpp sample1.sc
```

#### \-D\<define_name\>

This option is used to specify the name of a macro during the precompile operation. This command has the same function as using the #define preprocessor directive in your code.

##### Example

Set the command-line option as shown below to define a macro named ALTIBASE when precompiling sample1.sc.

```
$ apre -DAltibase –t cpp sample1.sc
```

#### \-v

This displays the version of APRE.

##### Example

Check the version of the APRE C/C++ precompiler:

```
$ apre –v
Altibase Precompiler2(APRE) Ver. 7.1.0.0.1 XEON_LINUX_redhat_Enterprise_AS4-64bit-7.1.0.0.1-release-GCC3.4.6 (xeon-redhat-linux-gnu) Oct 23 2013 09:28:30
```

#### \-n

This option is used to indicate that any host variables of type CHAR are not null-padded. This option should be applied into all the necessary source files when creating an execution program through precompiling multiple source files(.sc) The length of a CHAR type input host variable must be the same as or shorter than that of the column in the database.

#### \-unsafe_null

This option is used to prevent an error from being raised even when a NULL value is fetched. This option should be applied to all the necessary source files when creating an executing program with precompiling multiple source files(.sc). 

An error occurs if the value of a column on which a SELECT or FETCH operation is executed is NULL in case that an indicator variable is not specified.

#### \-spill \<values\>

This option is specified only when precompiling in an AIX environment. This is the same as using the #pragma directive, as shown below:

```
#pragma options spill=<values>
```

#### \-keyword

The -keyword displays the list of reserved words in relation to embedded SQL.

##### Example

```
$ apre -keyword

:: Keywords for C code ::
:: Keywords for C code ::
ALTIBASE_APRE APRE_BINARY APRE_BINARY2 APRE_BIT APRE_BLOB APRE_BLOB_LOCATOR APRE_BYTES APRE_CLOB APRE_CLOB_LOCATOR APRE_DUPKEY_ERR APRE_INTEGER APRE_NIBBLE APRE_NUMERIC APRE_VARBYTES MAX_CHAR_PTR SESC_DECLARE SESC_INCLUDE SES_BINARY SES_BIT SES_BLOB SES_BLOB_LOCATOR SES_BYTES SES_CLOB SES_CLOB_LOCATOR SES_DUPKEY_ERR SES_INTEGER SES_NIBBLE SES_NUMERIC SES_VARBYTES SQLFailOverCallback SQLLEN SQL_DATE_STRUCT SQL_TIMESTAMP_STRUCT SQL_TIME_STRUCT SQL_NUMERIC_STRUCT VARCHAR

:: Keywords for Embedded SQL statement ::
ABSOLUTE ADD AFTER AGER ALL ALLOCATE ALTER AND ANY ARCHIVE ARCHIVELOG AS ASC ASENSITIVE AT AUTOCOMMIT BACKUP BATCH BEFORE BEGIN BETWEEN BLOB_FILE BREAK BY CASCADE CASE CAST CLEAR_RECPTRS CLOB_FILE CLOSE COALESCE COLUMN COMMIT COMPILE CONNECT CONSTANT CONSTRAINT CONSTRAINTS CONTINUE CREATE CUBE CURSOR CYCLE DATABASE DEALLOCATE DECLARE DEFAULT DELETE DEQUEUE DESC DESCRIPTOR DIRECTORY DISABLE DISABLE_RECPTR DISCONNECT DISTINCT DO DROP EACH ELSE ELSEIF ELSIF ENABLE ENABLEALL_RECPTRS ENABLE_RECPTR END ENQUEUE ESCAPE EXCEPTION EXEC EXECUTE EXISTS EXIT EXTENTSIZE FALSE FETCH FIFO FIRST FIXED FLUSH FOR FOREIGN FOUND FREE FROM FULL FUNCTION GOTO GRANT GROUP GROUPING HAVING HOLD IDENTIFIED IF IMMEDIATE IN INDEX INDICATOR INNER INSENSITIVE INSERT INTERSECT INTO IS ISOLATION JOIN KEY LAST LEFT LESS LEVEL LIFO LIKE LIMIT LOB LOCAL LOCK LOGANCHOR LOOP MAXROWS MERGE MINUS MODE MOVE MOVEMENT NEW NEXT NOARCHIVELOG NOCYCLE NOPARALLEL NOT NULL OF OFF OFFLINE OLD ON ONERR ONLINE ONLY OPEN OPTION OR ORDER OTHERS OUT OUTER PARALLEL PARTITION PARTITIONS PREPARE PRIMARY PRIOR PRIVILEGES PROCEDURE PUBLIC QUEUE RAISE READ REBUILD RECOVER REFERENCES REFERENCING RELATIVE RELEASE RENAME REPLACE REPLICATION RESTRICT RETURN REVERSE REVOKE RIGHT ROLLBACK ROLLUP ROW ROWCOUNT ROWTYPE SAVEPOINT SCROLL SELECT SENSITIVE SEQUENCE SESSION SET SETS SOME SPLIT SQLCODE SQLERRM SQLERROR SQLLEN START STATEMENT STEP STORE SYNONYM TABLE TABLESPACE TEMPORARY THAN THEN THREADS TO TRIGGER TRUE TRUNCATE TYPE TYPESET UNION UNIQUE UNTIL UPDATE USER USING VALUES VARCHAR VARIABLE VIEW VOLATILE WAIT WAKEUP_RECPTR WHEN WHENEVER WHERE WHILE WITH WORK WRITE
```

#### \-debug \<macro\|symbol\>

When this option is used, a symbol table containing the names of macros or declared variables in the source code is output. This option is provided for use in debugging source code.

##### macro

If -debug macro is specified, a macro list containing the names of all defined macros is output.

##### symbol

If -debug symbol is specified, a list of information about declared variables is output.

##### Example

Create the sample1.c file and output a macro list containing the names of all defined macros.

```
$ apre –debug macro sample1.sc
```

Create the sample1.c file and output a list of information about declared variables.

```
$ apre –debug symbol sample1.sc
```

Print both macros and variables.

```
$ apre –debug macro symbol sample1.sc
```

#### \-lines

The contents of the source file '* .sc' can be compared through specifying #line to be inserted into .c or .cpp file created by preprocessing

##### Example

It can be verified that there is #line after creating sample.sc file with preprocessing.

```
$ apre –debug macro symbol sample1.sc
```

#### \-nchar_utf16

When this option is used, national character type data are encoded as UTF-16 during the precompile operation. Since this option cannot be applied into each source file(.sc), this option should be applied into all the source files in the case of creating an execution program with precompiling two or more source files. The national character type data are encoded in the format specified by the ALTIBASE_NLS_USE property. 

However, when using the encoding method specified in the ALTIBASE_NLS_USE property, the potential data loss might be occurred since the Unicode values stored in the database cannot be accurately expressed when executing a query expression.

##### Example

Preprocess the program with UTF-16.

```
$ apre -nchar_utf16 -t cpp sample.sc
```

#### \-nchar_var \<variable_name_list\>

When this option is used, APRE processes the specified variables using the national character set of Altibase. Blanks between variable names are not allowed. Additionally, variables within structures cannot be specified.

#### -silent

This is an option to turn on silent mode. Turning on silent mode will not show additional description such as Copryright.

### Programming using Embedded SQL Statements

In this section, a brief explanation of the general flow of applications containing embedded SQL statements is provided, as well as a description of how to approach writing such applications. 

Generally, the order in which an application is authored should mirror the general flow of execution of the application, which is as follows:

#### Declaring Host Variables

When writing a program, it is first necessary to declare the host variables and indicator variables that will be used. Host variables must be declared in the host variable declaration section if the -partial precompiler option is not set to “full”.

For more information about host variables and indicator variables, please refer to Chapter 2: Host Variables and Indicator Variables.

##### Considerations when Declaring Host Variables

-   Nested structures cannot be used as host variables. In other words, a structure cannot be an element of another structure. 
-   When declaring array-type host variables, macros can be used only to specify the number of array elements. Macro definitions cannot be used, for example, to specify the location at which the value of a host variable is to be substituted in an embedded SQL statement. 
-   When declaring a character-type (i.e. char or varchar) output host variable, the length of the host variable must be defined so that it is at least one byte longer than the size of the corresponding column. Otherwise, when a SELECT or FETCH statement is executed, the value in the column will be truncated. In this case, the value returned in sqlca.sqlcode will be SQL_SUCCESS_WITH_INFO.

##### Special Considerations when Declaring Array-Type Host Variables

For complete information about using arrays with embedded SQL statements, please refer to Chapter 9: Using Arrays in Embedded SQL Statements.

-   Array-type host variables can only be one-dimensional arrays. The exception is that two-dimensional char and varchar type arrays are allowed.
-   An indicator variable cannot be used with a host variable that is an array of structures. 
-   When an array of structures is used as an output host variable in the INTO clause of a SELECT or FETCH statement, only one output host variable can be used. In other words, the array of structures cannot be used with other output host variables. Therefore, if the output host variable to be used in the INTO clause is an array of structures, the number of elements in the structure must be the same as the number of columns in the select list. 
-   When an array of structures is used as an insert host variable in the VALUES clause of an INSERT statement, only one input host variable can be used. In other words, the array of structures cannot be used with other input host variables. Therefore, if the input host variable to be used in the VALUES clause is an array of structures, the number of elements in the structure must be the same as the number of columns in the INSERT statement. 
-   Internally, the varchar type is handled as a kind of structure, so it is subject to the above limitations. 
-   Array-type host variables must not be used together with non-array type host variables in INSERT, UPDATE or DELETE statements. 
-   If an array-type output host variable is used when a SELECT or FETCH statement is executed, and the number of returned records is smaller than the array size, the value of sqlca.sqlcode will be SQL_SUCCESS. 
-   Array-type input host variables cannot be used with SELECT statements or cursor-related statements. 
-   The FOR clause can be used with array-type input host variables to execute an embedded INSERT, UPDATE, DELETE statements, but can be used with array-type output host variables to execute an embedded FETCH statement. 
-   When working with array-type host variables in AUTOCOMMIT mode, a “transaction” is not the totality of operations performed using the entire array. Rather, the operations corresponding to each element are individual transactions, and thus they are committed separately from one another. 
-   Arrays of pointers cannot be declared or used as host variables.

##### Considerations When Declaring Indicator Variables

-   The data type of indicator variables must be int. 
-   When using the varchar type as an input host variable without a separately defined indicator variable, it is necessary to specify the value of len, which is one of the elements of the varchar structure. If the value of the varchar array is not NULL, set the value of len to the length of the arr element. If the varchar array is NULL, set len to -1. 
-   For numeric type host variables, indicator variable values other than -1 are meaningless. 
-   Indicator variables must be used when working with binary type host variables.

##### Host Variable Declaration Section

For complete information about the host variable declaration section, please refer to Chapter 3: Host Variable Declaration Section.

-   Definitions of data types (typedef) to be used as host variable data types must be made in the host variable declaration section.

##### Example

The following is an example of a host variable declaration section:

< Sample program: insert.sc >

```
/* declare host variables */
EXEC SQL BEGIN DECLARE SECTION;
char usr[10];
char pwd[10];
char    s_gno[10+1];
char    s_gname[20+1];
char    s_goods_location[9+1];
int     s_stock;
double  s_price;
EXEC SQL END DECLARE SECTION;
```

#### Connecting to a Database Server

After the host variables have been declared, it is necessary to connect to a database server before any SQL statements can be executed. 

After a connection with a database server has been successfully established, it will then be possible to execute all embedded SQL statements. 

For detailed instructions on how to connect to database servers, please refer to Chapter 6: Embedded SQL Statements.

##### About Connections, Multiple Connections, and Sessions

-   To establish a new connection using the same name as an existing connection, it is first necessary to execute the FREE or DISCONNECT statement to terminate the existing connection. If the database server is online, execute the DISCONNECT statement, whereas if the database server is offline, execute the FREE statement. 
  
-   If the connection method (CONNTYPE) is set to 2 or 3 in the connection string in a USING clause, the DSN and PORT_NO options will be ignored even if they are set, and an attempt will be made to connect with the local database server.  When two sets of connection options are specified and a connection is successfully established using the first set of options, the value returned in sqlca.sqlcode is SQL_SUCCESS. If the connection attempt using the first set of options fails, but a connection is then successfully established using the second set of options, the value returned in sqlca.sqlcode is SQL_SUCCES_WITH_INFO. If a connection cannot be established using either set of options, the value returned in sqlca.sqlcode is SQL_ERROR. 
  
-   A maximum of 1024 embedded SQL statements can be executed per connection. 
  
-   In a session in which AUTOCOMMIT is set to OFF, if an application is shut down in the state in which uncommitted transactions exist, all transactions that were not committed at the time that the application is shut down will be rolled back. However, if the DISCONNECT statement is executed before the application is shut down, all pending transactions will be committed. 
  
-   The AT clause cannot be used in the following types of embedded SQL:
  
    INCLUDE statement: EXEC SQL INCLUDE …  
    OPTION statement: EXEC SQL OPTION …  
WHENEVER statement: EXEC SQL WHENEVER …

##### Example

The following example shows how to connect to a database server:

\< Sample Program : connect1.sc \>

```
/* declare host variables */
EXEC SQL BEGIN DECLARE SECTION;
char usr[10];
char pwd[10];
EXEC SQL END DECLARE SECTION;

/* set username */
strcpy(usr, "SYS");
/* set password */
strcpy(pwd, "MANAGER");

EXEC SQL CONNECT :usr IDENTIFIED BY :pwd;  
if (sqlca.sqlcode == SQL_SUCCESS) /* check sqlca.sqlcode */
{
    printf("Success connection to altibase server\n\n");
}
else
{
    printf("Error : [%d] %s\n\n", SQLCODE, sqlca.sqlerrm.sqlerrmc);
    exit(1);
}
```

#### Executing Embedded SQL Statements

After a connection with a database server has been successfully established, it is possible to execute embedded SQL statements. The term “embedded SQL statements” encompasses DML statements such as the SELECT and INSERT statements, DDL statements such as object creation statements, system control statements, cursor-related SQL statements, dynamic SQL statements, and all other SQL statements of Altibase. 

For more information about using each of the various kinds of embedded SQL statements, please refer to Chapters 6 , 8 , 9 , 10 , and 11.

##### Examples

What follows are examples of the use of various kinds of embedded SQL statements.

[Example 1] The following is an example of an UPDATE statement:

\< Sample Program : update.sc \>

```
/* declare host variables */
EXEC SQL BEGIN DECLARE SECTION;
int      s_eno;
short    s_dno;
varchar  s_emp_job[15+1];
EXEC SQL END DECLARE SECTION;

s_eno = 2;
s_dno = 1001;
strcpy(s_emp_job.arr, "ENGINEER");
s_emp_job.len = strlen(s_emp_job.arr);

EXEC SQL UPDATE EMPLOYEES 
SET DNO     = :s_dno,
                EMP_JOB = :s_emp_job
            WHERE ENO = :s_eno;
```

[Example 2] The following is an example of the use of cursor control statements:

\< Sample Program : hostvar.h \>

```
EXEC SQL BEGIN DECLARE SECTION;
typedef struct department
{
    short dno; 
    char  dname[30+1];
    char  dep_location[9+1];
    int   mgr_no;
} department;

typedef struct dept_ind
{
    int dno; 
    int dname;
    int dep_location;
    int mgr_no;
} dept_ind;
EXEC SQL END DECLARE SECTION;
```

\< Sample Program : cursor1.sc \>

```
/* specify path of header file */
EXEC SQL OPTION (INCLUDE=./include);
/* include header file for precompile */
EXEC SQL INCLUDE hostvar.h;

/* declare host variables */
EXEC SQL BEGIN DECLARE SECTION;
/* structure host variables */
department s_department;
/* structure indicator variables */
dept_ind s_dept_ind;
EXEC SQL END DECLARE SECTION;

/* declare cursor */
EXEC SQL DECLARE DEPT_CUR CURSOR FOR 
             SELECT *
             FROM DEPARTMENTS; 
    
/* open cursor */
EXEC SQL OPEN DEPT_CUR;
    
/* fetch cursor in loop */
while(1)
{
    /* use indicator variables to check null value */
    EXEC SQL FETCH DEPT_CUR INTO :s_department :s_dept_ind;
    if (sqlca.sqlcode == SQL_SUCCESS) /* check sqlca.sqlcode */
    {
    printf("%d     %s %s          %d\n", 
              s_department.dno, s_department.dname, 
              s_department.dep_location, 
s_department.mgr_no);
}
else if (sqlca.sqlcode == SQL_NO_DATA)
{
    break;
}
else 
{
    printf("Error : [%d] %s\n", SQLCODE, sqlca.sqlerrm.sqlerrmc);
    break;
}
}

/* close cursor */
EXEC SQL CLOSE DEPT_CUR;
```

#### Handling Runtime Errors

-   After every embedded SQL statement has been executed, it is necessary to check the result of execution. The result of execution of embedded SQL statements is stored in the variable sqlca.sqlcode, and, depending on the value of sqlca.sqlcode, the variables SQLSTATE, SQLCODE, etc. can be checked to obtain more information about the result of execution.

For detailed information about all of the variables that can be checked to determine the result of execution of an embedded SQL statement, please refer to Chapter 7: Handling Runtime Errors.

##### Considerations when Handling Runtime Errors

The following are some considerations to keep in mind when using SQLCA, SQLCODE, SQLSTATE and WHENEVER to handle run-time errors.

-   Every time an embedded SQL statement is executed, be sure to check the value of sqlca.sqlcode so that any errors that occurred will be processed appropriately. 
-   When a SELECT statement is executed, if the size of an output host variable is smaller than the size of the corresponding character-type column, the data will be truncated so that they can be saved in the host variable. When this happens, the value of sqlca.sqlcode will be SQL_SUCCESS_WITH_INFO. 
-   If no records are affected by an UPDATE or DELETE operation, the value of sqlca.sqlcode will be SQL_NO_DATA. To determine the number of records that were affected by an UPDATE or DELETE operation, check the value of sqlca.sqlerrd[2]. If no records were affected, this value will be 0. 
-   The SQLCODE error code values are negative decimal integers. However, the error codes in the Error Message Reference are positive hexadecimal values. Therefore, when referring to the Error Message Reference, convert the absolute values of SQLCODE error codes into hexadecimal values. 
-   The scope of applicability of a WHENEVER statement is not the same as the overall program flow. In particular, a WHENEVER statement applies only to the file in which it is found. 
-   The WHENEVER statement must precede any embedded SQL statements to which it is intended to apply. 
-   WHENEVER statements are connection-independent. In other words, a WHENEVER statement in an application with more than one connection affects all embedded SQL statements within its scope of applicability, regardless of the connection to which the embedded SQL statements pertain.

##### Example

In this example, the variables in the sqlca structure are checked to determine the result of execution of an embedded SQL statement.

\< Sample Program : delete.sc \>

```
/* declare host variables */
EXEC SQL BEGIN DECLARE SECTION;
int      s_eno;
short    s_dno;
EXEC SQL END DECLARE SECTION;

s_eno = 5;
s_dno = 1000;

EXEC SQL DELETE FROM EMPLOYEES 
WHERE ENO > :s_eno AND 
DNO > :s_dno AND 
EMP_JOB LIKE 'P%';

/* check sqlca.sqlcode */
if (sqlca.sqlcode == SQL_SUCCESS) 
{
    /* sqlca.sqlerrd[2] holds the 
rows-processed(deleted) count */
    printf("%d rows deleted\n\n", sqlca.sqlerrd[2]);
}
else 
{
    printf("Error : [%d] %s\n\n", 
SQLCODE, sqlca.sqlerrm.sqlerrmc);
}
```

#### Disconnecting from the Database Server

After all embedded SQL statements have been executed, it will be necessary to disconnect from the database server before shutting down the application. Disconnecting from the database server frees all resources that were allocated for the connection. After disconnecting from the database server, it is of course impossible to execute any more embedded SQL statements. 

For detailed information about how to connect to and disconnect from database servers, please refer to Chapter6: Embedded SQL Statements.

##### Example

The following example shows how to disconnect from a database server:

\< Sample Program : connect1.sc \>

```
EXEC SQL DISCONNECT;
```

#### The Precompile Operation

This is how to execute the precompiling operation using the APRE precompiler:

```
apre [<apre – option>] <filename>
```

##### Example

In the following example, the connect1.sc file is precompiled:

```
$ apre connect1.sc
```

## 2. Host Variables and Indicator Variables

-------------------------

### Host Variables 

#### Overview

Host variables are responsible for data exchange between an application written in a host language and a database server. In other words, host variables store data that have been read from table columns, data that are to be inserted into table columns, etc. 

#### Declaring Host Variables

The host variable declaration method is as follows:

-   If an attempt is made to use a variable in an embedded SQL statement, and the variable was not first declared in either the host variable declaration section or the function argument declaration section, an error saying “The host variable [variable_name] is unknown.” will be raised during the precompile operation.  
    For more information about the host variable declaration section and the function argument declaration section, please refer to Chapter3: Host Variable Declaration Section.
    
-   The syntax for declaring host variables is as follows  
    datatype variable_name;  
    This is the same as when declaring variables in a C or C++ program. For detailed information about the data types that host variables can have, please refer to Chapter 5: Host Variable Data Types.
    
-   Host variables can also be declared as arrays. For the CHAR and VARCHAR types, it is possible to declare one- or two-dimensional arrays, whereas for the other types, it is only possible to declare one-dimensional arrays. For more information about using arrays with embedded SQL statements, please refer to Chapter9 : Using Arrays in Embedded SQL Statements.
  
-   APRE can use the CHAR and VARCHAR type host variables to process text data in any of the national character sets supported by Altibase. When handling data in the national character set, use the reserved word shown below:  
    character set [is] nchar_cs  
    Note that if the -nchar_var command-line option is used when precompiling the source code, it is not necessary to use the reserved word shown above.
    
-   The names of host variables must start with an alphabetic character (a ~ z, A ~ Z), the underscore character (‘_’), or a dollar sign (“$”), and must not be longer than 50 bytes.

#### Using Host Variables in Embedded SQL Statements

A host variable can be used anywhere in an embedded SQL statement where the use of a scalar expression would be allowed.

Host variables must be distinguished from the other elements in embedded SQL statements. This is accomplished by prepending the colon (“:”) character to the names of host variables whenever they appear in embedded SQL statements.

#### Example

In the following example, the host variables s_dno, s_dname, and s_dep_location are declared:

\< Sample Program : select.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
short      s_dno;
char       s_dname[30+1];
char       s_dep_location[9+1];
EXEC SQL END DECLARE SECTION;

EXEC SQL SELECT DNAME, DEP_LOCATION
INTO :s_dname, :s_dep_location
FROM DEPARTMENTS
WHERE DNO = :s_dno;
```

### Classifying Host Variables

Host variables are classified as either input host variables or output host variables depending on whether they are used to input data into a database server or extract data from a database server

#### Output Host Variables 

An output host variable is used in an INTO clause of a SELECT or FETCH statement to store query results. An output host variable thus plays the same role as a variable used in the ODBC SQLBindCol() function.

##### Example

The following is an example of the use of output host variables.

In this example, s_dname and s_dep_location are host variables. The values in the DNAME and DEP_LOCATION columns for the records that satisfy the condition in the WHERE clause are stored in the host variables s_dname and s_dep_location, respectively.

\< Sample Program : select.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
short      s_dno;
char       s_dname[30+1];
char       s_dep_location[9+1];
EXEC SQL END DECLARE SECTION;

s_dno = 1001;
EXEC SQL SELECT DNAME, DEP_LOCATION
INTO :s_dname, :s_dep_location
FROM DEPARTMENTS
WHERE DNO = :s_dno;
```

#### Input Host Variables 

Input host variables are used wherever output host variables are not used. Their primary role is to specify data to be used in SQL statements. For example, an input host variable can be used in the WHERE clause of a SELECT statement to specify a value that is part of a condition, or in the VALUES clause of an INSERT statement to specify a value to be inserted into a particular column of a record.

An input variable can be used anywhere in an embedded SQL statement where the use of a scalar expression would be allowed. Note however that in order to use a host variable in the select list or the GROUP BY or ORDER BY clause of a SELECT statement, its type must be specified using the CAST operator in the SQL statement. If the CAST operator is used in the GROUP BY clause to specify the host variable type, this expression cannot be used in the TARGET clause.

An input host variable can be used in a WHERE clause. However, be aware that when using a host variable in a join predicate in a WHERE clause, the query optimizer will be unaware of its data type, and thus can only use the NL join method when creating an execution plan. To overcome this limitation and allow the optimizer to choose a more efficient joining method, use the CAST operator in the SQL statement to let the optimizer know the type of the host variable.

##### Examples

The following examples illustrate the use of input host variables in various ways. 

[Example 1] The following example shows the use of the input host variables s_gno, s_gname, s_goods_location, s_stock, and s_price in an INSERT statement. The values stored in the input host variables are inserted into respective table columns.

\< Sample Program: insert.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
char    s_gno[10+1];
char    s_gname[20+1];
char    s_goods_location[9+1];
int     s_stock;
double  s_price;
EXEC SQL END DECLARE SECTION;

strcpy(s_gno, "F111100002");
strcpy(s_gname, "XX-101");
strcpy(s_goods_location, "FD0003");
s_stock = 5000;
s_price = 9980.21;

EXEC SQL INSERT INTO GOODS 
VALUES (:s_gno, :s_gname, :s_goods_location, 
:s_stock, :s_price);
```

[Example 2] The following example shows the use of the input host variables s_dno, s_emp_job, and s_eno in an UPDATE statement. The values in the DNO and EMP_JOB columns of the records that satisfy the condition in the WHERE clause are updated with the values of s_dno and s_emp_job, respectively.

\< Sample Program : update.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
int      s_eno;
short    s_dno;
varchar  s_emp_job[15+1];
EXEC SQL END DECLARE SECTION;

s_eno = 2;
s_dno = 1001;
strcpy(s_emp_job.arr, "ENGINEER");
s_emp_job.len = strlen(s_emp_job.arr);

EXEC SQL UPDATE EMPLOYEES 
SET DNO = :s_dno,
                          EMP_JOB = :s_emp_job
            WHERE ENO = :s_eno;
```

[Example 3] The following example shows the use of the input host variables s_eno and s_dno in a DELETE statement. The values of the host variables are used in the WHERE clause to determine which records are to be deleted.

\< Sample Program : delete.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
int      s_eno;
short    s_dno;
EXEC SQL END DECLARE SECTION;

s_eno = 5;
s_dno = 1000;

EXEC SQL DELETE FROM EMPLOYEES 
WHERE ENO > :s_eno AND 
DNO > :s_dno AND 
EMP_JOB LIKE 'P%';
```

[Example 4] The following example shows the use of the input host variable s_dno in a SELECT statement. The value of s_dno is used in the WHERE clause to determine which records to retrieve.

\< Sample Program : select.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
short      s_dno;
char       s_dname[30+1];
char       s_dep_location[9+1];
EXEC SQL END DECLARE SECTION;

s_dno = 1001;
EXEC SQL SELECT DNAME, DEP_LOCATION
INTO :s_dname, :s_dep_location
FROM DEPARTMENTS
WHERE DNO = :s_dno;
```

[Example 5] The following example shows the use of the input host variable s_call in the select list of a SELECT statement.

\< Sample Program : host_target.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
double s_call;
EXEC SQL END DECLARE SECTION;

s_call = 0.045;

EXEC SQL SELECT principal sum * ( 1 – CAST( :s_call AS DOUBLE ) ) FROM 계좌;
```

[Example 6] The following example shows the use of the input host variable s_period in the GROUP BY clause of a SELECT statement.

\< Sample Program : host_group.sc \>

```
int s_period;
EXEC SQL END DECLARE SECTION;

s_period = 1;    /* 1(month), 3(quarter year), 6(half year) */

EXEC SQL SELECT SUM(sale) FROM sales 
                 GROUP BY FLOOR( month / CAST( :s_period AS INTEGER ) );
```

[Example 7] The following example shows the use of the input host variable s_diff in the join predicate of a WHERE clause. 

< Sample Program : host_join.sc >

```
EXEC SQL BEGIN DECLARE SECTION;
int s_diff;
EXEC SQL END DECLARE SECTION;

s_diff = 1;

EXEC SQL SELECT * FROM t1, t2
                 WHERE t1.i1 = t2.i1 + CAST( :s_diff AS INTEGER );
```

### Indicator Variables 

#### Overview

Because NULL table column values cannot be expressed in the host language, a method of handling them separately is required. 

To enable APRE to process NULL values, the use of so-called “indicator variables” is supported. 

Indicator variables are used alongside host variables in embedded SQL statements to process NULL values. 

#### Why use indicator variables?

##### 		For Handling Null Values

-   Indicator variables can be used to provide information on the basis of which a programmer can judge whether or not a column value is NULL.   
    If an input indicator variable is set to -1 (SQL_NULL_DATA), the corresponding host variable will be processed as NULL. If the value of an output indicator variable is -1 (SQL_NULL_DATA), For example, an indicator variable can be used to indicate whether the value of a host variable to be used in an INSERT statement is NULL, or whether a column value returned by a SELECT statement is NULL. 
    
    ##### For Managing the Length of Data
    
- Indicator variables can also be used to specify the length of an input value or store the length of a column value returned by a SELECT statement. Indicator variables can be used to manage data length only for character or binary type host variables. To specify the length of an input value, an input indicator variable would be used, whereas an output indicator variable would be used to store the length of a returned column value. If a host variable is a character type variable, and the value to be input or the returned column value is terminated with a null terminator (“\0”) and is known not to be NULL, there is no need to use an indicator variable. When dealing with a binary type host variable, it is essential to use an indicator variable, even when the input value or the returned column value is known not to be NULL. This is because the binary type is not terminated with a NULL character, and the database needs a way of knowing the length of the input value, while the application needs a way of knowing the length of the returned column.) For more information about the use of binary type host variables, please refer to Chapter 5: Host Variable Data Types.

#### Declaring Indicator Variables

Indicator variables are declared as follows:

-   Indicator variables are declared in the host variable declaration section or the function argument declaration section. If an attempt is made to use an indicator variable in an embedded SQL statement, and the indicator variable was not previously declared in the host variable declaration section or the function argument declaration section, an error saying “The host variable [variable_name] is unknown.” will be raised during the precompile operation. For more information about the host variable declaration section and the function argument declaration section, please refer to Chapter 3: Host Variable Declaration Section. 

The syntax for declaring indicator variables is as follows:  

* datatype indicator_variable_name;  
  The data type of an indicator variable must be int or SQLLEN (a predefined type in ODBC). It can also be a data structure, as long as it consists of only the int and SQLLEN types. 

-   The names of indicator variables must start with an alphabetic character (a ~ z, A ~ Z), the underscore character (“_”), or a dollar sign (“$”), and must not be longer than 50 bytes.

#### Syntax

The syntax for using indicator variables within embedded SQL statements is as follows:

```
<:host_variable> [INDICATOR] <:indicator_variable>
```

The keyword “INDICATOR” can be omitted.

If the host variable is not a structure, the indicator variable must not be a structure either. However, if the host variable is a structure, the indicator variable must be a structure too.

#### When is it necessary to use indicator variables?

Indicator variables must be used in the following cases:

-   When an input value is NULL  
    When inputting a NULL value, an indicator variable must be used, and its value must be set to -1 (SQL_NULL_DATA). 

-   When querying a column that does not have a NOT NULL constraint  
    If the value of a selected or fetched column is NULL and an indicator variable is not being used, the result of execution of the embedded SQL statement (sqlca.sqlcode) will be SQL_SUCCESS_WITH_INFO, and a warning message will be returned in the variable sqlca.sqlerrm.sqlerrmc. 
    
-   When the type of an input or output host variable is APRE_BINARY, APRE_BLOB or APRE_BYTES  
    Because binary types are not NULL-terminated, the database needs a way of knowing the length of an input value. Therefore, the length of the input data must be specified using the indicator variable. In the same way, when dealing with output host variables, the length of returned column values must be stored in indicator variables. For more information about the APRE_BINARY, APRE_BLOB and APRE_BYTES data types, please refer to Chapter 5: Host Variable Data Types. 
    
-   When using an APRE_NIBBLE type output host variable  
    An indicator variable must be used when entering a NULL value in a NIBBLE type column or reading a NULL value from a NIBBLE type column. For more information about the use of the APRE_NIBBLE data type, please refer to Chapter 5: Host Variable Data Types

#### Considerations

-   When a host variable is a structure, the corresponding indicator variable must also be a structure. The two structures must have the same number of elements

```
Example) EXEC SQL BEGIN DECLARE SECTION;
struct tag1 { int i1; int i2; } var1;
struct tag2 { int i1_ind; int i2_ind; } var1_ind1;
struct tag3 { int i1_ind; int i2_ind; 
int i3_ind; } var1_ind2; 
EXEC SQL END DECLARE SECTION;

EXEC SQL INSERT INTO T1(I1, I2) 
VALUES (:var1 :var1_ind1);	(O)
EXEC SQL INSERT INTO T1(I1, I2) 
VALUES (:var1 :var1_ind2);	(X)
```

-   An indicator variable cannot be used with a host variable that is an array of structures.

```
Example) EXEC SQL BEGIN DECLARE SECTION;
struct tag1 { int i1; int i2; char i3[11]; } var1[10];
struct tag2 { int i1_ind; int i2_ind; int i3_ind; } var1_ind1[10];
EXEC SQL END DECLARE SECTION;

EXEC SQL INSERT INTO T1(I1, I2, I3) 
VALUES (:var1 :var1_ind1);	(X)
```

-   When dealing with a VARCHAR type host variable, if an indicator variable is specified for use with the host variable, it will be used as the indicator variable, whereas if no indicator variable is specified, the len variable, which is an element of the VARCHAR type, will automatically be used as the indicator variable. In this case it is acceptable to use the value of len as the indicator variable. 

```
Example) EXEC SQL BEGIN DECLARE SECTION;
varchar var1;
int var1_ind;
EXEC SQL END DECLARE SECTION;

/* Inserting 'TEST' in column I1 of table T1
when var1.len is used as an indicator variable  */
strcpy(var1.arr, “TEST”);
var1.len = strlen(var1.arr);
EXEC SQL INSERT INTO T1(I1) 
VALUES (:var1);

/*  Inserting NULL in column I1 of table T1
when var1.len is used as an indicator variable */
var1.len = -1;
EXEC SQL INSERT INTO T1(I1) 
VALUES (:var1);

/*  Inserting 'TEST' in column I1 of table T1
when var1_ind is used as an indicator variable */
strcpy(var1.arr, “TEST”);
var1_ind = strlen(var1.arr);
EXEC SQL INSERT INTO T1(I1) 
VALUES (:var1 :var1_ind);	
```

#### Examples

In the following example, s_goods_location_ind is used as the indicator variable for the s_goods_location host variable, and s_price_ind is used as the indicator variable for the s_price host variable. Because the value of both indicator variables is SQL_NULL_DATA, NULL will be inserted in the corresponding columns, even though the values of the s_goods_location and s_price host variables are not NULL.

\< Sample Program : indicator.sc \>

```
/* declare host variables */
EXEC SQL BEGIN DECLARE SECTION;
char    s_gno[10+1];
char    s_gname[20+1];
char    s_goods_location[9+1];
int     s_stock;
double  s_price;

/* declare indicator variables */
int      s_goods_location_ind;
int      s_price_ind;
EXEC SQL END DECLARE SECTION;

/* set host variables */
strcpy(s_gno, "X111100002");
strcpy(s_gname, "XX-101");
strcpy(s_goods_location, "FD0003");
s_stock = 5000;
s_price = 9980.21;

/* set indicator variables */
s_goods_location_ind = SQL_NULL_DATA;
s_price_ind          = SQL_NULL_DATA;

EXEC SQL INSERT INTO GOODS 
VALUES (:s_gno, 
:s_gname,
:s_goods_location :s_goods_location_ind,
:s_stock,
:s_price :s_price_ind);
```

### Classifying Indicator Variables

Indicator variables are classified as either input indicator variables or output indicator variables depending on whether they are used with output host variables or input host variables.

#### Output Indicator Variables

If the column corresponding to an output host variable does not have a NOT NULL constraint, it is essential that an indicator variable be used for the host variable. The reason for this is that when the value of a selected or fetched column is NULL and an indicator variable is not being used, the result of execution of the embedded SQL statement (sqlca.sqlcode) will be SQL_SUCCESS_WITH_INFO and a warning message will be returned in the variable sqlca.sqlerrm.sqlerrmc.

If the value of the indicator variable is -1 (SQL_NULL_DATA), this means that NULL will be returned from the column. Therefore, the value of the output host variable is not meaningful (i.e. a garbage value). If the value of the indicator variable is not -1 (SQL_NULL_DATA), this means that the value in the corresponding column is not NULL, and will be saved in the output host variable. For more detailed information about the value of the indicator variable in such cases, please refer to the next section "Meaning of Indicator Variables".

##### Examples

The following is an example of the use of an output indicator variable. 

In this example, the variable s_good_ind is used as an indicator variable for the variable s_goods. Because s_goods is a structure, s_good_ind must also be declared as a structure. The two structures will have the same number of components. After the SELECT statement is executed, each of the members of s_good_ind will be checked to determine if the value is -1. 

\< Sample Program : hostvar.h \>

```
EXEC SQL BEGIN DECLARE SECTION;
typedef struct goods
{
    char   gno[10+1];
    char   gname[20+1];
    char   goods_location[9+1];
    int    stock;
    double price;
} goods;

typedef struct good_ind
{
    int gno;
    int gname;
    int goods_location;
    int stock;
    int price;
} good_ind;
EXEC SQL END DECLARE SECTION;
```

\< Sample Program : indicator.sc \>

```
/* specify path of header file */
EXEC SQL OPTION (INCLUDE=./include);
/* include header file for precompile */
EXEC SQL INCLUDE hostvar.h;

EXEC SQL BEGIN DECLARE SECTION;
goods     s_goods;
good_ind s_good_ind;
EXEC SQL END DECLARE SECTION;

EXEC SQL SELECT * 
INTO :s_goods :s_good_ind 
FROM GOODS 
WHERE GNO = :s_gno;

/* Because the GNO and GNAME columns have the NOT NULL constraint, their indicator variables do not have to
be checked. */ 
if (sqlca.sqlcode == SQL_SUCCESS) 
{
        if (s_good_ind.goods_location == SQL_NULL_DATA)
        {
            strcpy(s_goods.goods_location, "NULL");
        }
        if (s_good_ind.stock == SQL_NULL_DATA)
        {
            s_goods.stock = -1;
        }
        if (s_good_ind.price == SQL_NULL_DATA)
        {
            s_goods.price = -1;
        }
}
```

#### Input Indicator Variables

To specify NULL as an input value, it is necessary to use an input indicator variable. In such cases, the value of the indicator variable must be set to -1.

When specifying a non-NULL input value, there is no need to use the corresponding indicator variable, but when using the indicator variable, care must be taken to ensure that there is no possibility that a NULL value will be entered. The meaning of the value of the indicator variable differs depending on the type of the input host variable. For more information, please refer to the next section "Meaning of Indicator Variables".

##### Example

The following is an example of the use of an input indicator variable. 

In this example, the variable s_goods_location_ind is used as an indicator variable for the variable s_goods_location, and the variable s_price_ind is used as an indicator variable for the variable s_price. The values of s_goods_location_ind and s_price_ind are set to SQL_NULL_DATA (-1) to insert NULL into the GOODS_LOCATION and PRICE columns, respectively. 

\< Sample Program : indicator.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
/* declare host variables */
char    s_gno[10+1];
char    s_gname[20+1];
char    s_goods_location[9+1];
int     s_stock;
double  s_price;

/* declare indicator variables */
int      s_goods_location_ind;
int      s_price_ind;
EXEC SQL END DECLARE SECTION;

/* set host variables */
strcpy(s_gno, "X111100002");
strcpy(s_gname, "XX-101");
strcpy(s_goods_location, "FD0003");
s_stock = 5000;
s_price = 9980.21;

/* set indicator variables */
s_goods_location_ind = SQL_NULL_DATA;
s_price_ind            = SQL_NULL_DATA;

EXEC SQL INSERT INTO GOODS 
VALUES (:s_gno, 
                   :s_gname, 
                   :s_goods_location :s_goods_location_ind, 
                   :s_stock, 
:s_price :s_price_ind);
```

### Meaning of Indicator Variables

The following table describes the meanings of indicator variable values depending on the type of the host variable and on whether the indicator variable is an input indicator variable or an output indicator variable. 

An indicator variable value of -1 always signifies a NULL host variable value. The meaning of indicator variable values other than -1, however, differs depending on the type of the host variable and on whether the indicator variable is an input indicator variable or an output indicator variable. Therefore, it is important to understand the information in the following table, and to refer back to it when using indicator variables. 

It is particularly important that the value of input indicator variables be set correctly, because these values are used internally by the precompiler and the database server

<table>
    <tr>
    	<th>Host Variable
Type
</th>
		<th colspan="2">Value of Input Indicator Variables</th>
		<th colspan="2">Value of Output Indicator Variables</th>	
    </tr>
    <tr>
    	<td>Host variable type / Indicator variable value</td>
    	<td>-1</td>
    	<td>-1 Values other than -1 </td>
    	<td>-1</td>
    	<td>Values other than -1</td>
    </tr>
    <tr>
    	<td>Numeric types</td>
    	<td rowspan="8">Means the input value is NULL</td>
    	<td>Not internally used. Not
meaningful.</td>
    	<td rowspan="8">Means the
returned
value is
NULL.
The actual value
of the
host variable does
not mean
anything.
(Garbage
value)
</td>
		<td>Contains the size of the host variable (sizeof).</td>
    </tr>
    <tr>
    	<td>Character types</td>
    	<td>Used to indicate the
length of the input value
(strlen). Must be set.</td>
    	<td>Contains the length of the returned
value (strlen).</td>   	
    </tr>
    <tr>
    	<td>Date type</td>
    	<td>Not internally used. Not
meaningful.</td>
    	<td>Contains the size of the host variable (sizeof).</td>
    </tr>
    <tr>
    	<td>APRE_BINARY</td>
    	<td>Used to indicate the
length, in bytes, of the
input value. Must be set.</td>
    	<td>Contains the length, in bytes, of the
returned value.</td>
    </tr>
    <tr>
    	<td>APRE_BINARY2</td>
    	<td>Must specifies the length in bytes of the input.</td>
    	<td>The length (bytes) of the returned value is stored.</td>
    </tr>
    <tr>
    	<td>APRE_BLOB</td>
    	<td>Used to indicate the
length, in bytes, of the
input value. Must be set.</td>
    	<td>Contains the length, in bytes, of the
returned value.</td>
    </tr>
    <tr>
    	<td>APRE_CLOB</td>
    	<td>Used to indicate the
length, in bytes, of the
input value. Must be set.</td>
    	<td>The length (bytes) of the returned value is stored.</td>
    </tr>
    <tr>
    	<td>APRE_BYTES</td>
    	<td>Must specify the length in bytes of the input.</td>
    	<td>
The length (bytes) of the returned value is stored.</td>
    </tr>
    <tr>
    	<td>APRE_NIBBLE</td>
    	<td>Not internally used. Not
meaningful.</td>
    	<td>The length, in bytes, of the returned
value is stored</td>
    </tr>
<table>


Indicator variables are usually used for handling NULL values. However, as shown in the above table, input indicator variable values other than -1 can be meaningful, and are checked and used within the system. Therefore, when using an input indicator variable, it is important to set its value accurately, even when the value of the corresponding host variable is not NULL.

When the value of an input indicator variable that corresponds to a CHAR or BINARY type host variable is not -1, the database server will take the value of the indicator variable as the length of the input value, and process the value accordingly

### Sample Programs

##### indicator.sc 

This example can be found at $ALTIBASE_HOME/sample/APRE/indicator.sc

##### Result of Execution

```
$ is –f schema/schema.sql
$ make indicator
$ ./indicator
<INDICATOR VARIABLES>
-----------------------------------------------------------
[Scalar Indicator Variables]                                      
-----------------------------------------------------------
Success insert

-----------------------------------------------------------
[Structure Indicator Variables]                                   
-----------------------------------------------------------
GNO        GNAME                GOODS_LOCATION  STOCK  PRICE      
-----------------------------------------------------------
X111100002 XX-101               NULL            5000   -1.00

-----------------------------------------------------------
 [Scalar Array Indicator Variables]                                
-----------------------------------------------------------
3 rows updated
3 times update success

-----------------------------------------------------------
 [Arrays In Structure]                                             
-----------------------------------------------------------
3 rows inserted
3 times inserte success

-----------------------------------------------------------
 [Indicator Variable(.len) of VARCHAR With Output Host Variables]  
-----------------------------------------------------------
v_address.arr = [Pusan University]
v_address.len = 16

-----------------------------------------------------------
 [Indicator Variable(.len) of VARCHAR With Input Host Variables]   
-----------------------------------------------------------
Success update

-----------------------------------------------------------
 [Indicator Variable of DATE Type With Input Host Variables]       
-----------------------------------------------------------
Success update

-----------------------------------------------------------
 [Indicator Variable of DATE Type With Output Host Variables]      
-----------------------------------------------------------
d_arrival_date2 = NULL
```



## 3. Host Variable Declaration Section

------------------

### Host Variable Declaration Section

The name, type, and length of host variables are critical information during the precompiling operation. Therefore, the host variables to be used must be defined in a form such that the C/C++ precompiler can be aware of them. This is accomplished in the host variable declaration section

In the host variable declaration secion, a host variable is declared to use in the program.

#### Syntax

The syntax shown below is supported for the host variable declaration section:

```
EXEC SQL BEGIN DECLARE SECTION;
/* variable_declarations */
EXEC SQL END DECLARE SECTION;
```

The host variable declaration section begins with the EXEC SQL BEGIN DECLARE SECTION statement and ends with the EXEC SQL END DECLARE SECTION statement. Host variables to be used in the program must be declared between these two statements.

A host variable declaration section can be present both in the file (.sc) to be precompiled and in any header files (.h) that are included in the precompile operation. 

Note however that when including a header file using the #include preprocessor directive, a host variable should be declared without host variable declaration section in the header file. Then it requires the -parse option set to full during the precompile operation. If the header file is included within EXEC SQL INCLUDE section, then a host variable should be declared in the host variable declaration section of the header file.

The reason for this is that a header file (.h) that is included using the #include preprocessor directive is referred to not only by the file to be precompiled (.sc), but may also be referred to by C (.c) or C++ (.cpp) source files that do not contain any embedded SQL, so errors may be raised during the compile operation. Please refer to Chapter 4: #include for more detail.

#### Scope of Host Variables

Host variables can be global or local in scope, depending on the location of the host variable declaration section. The method of determining the scope of declared variables is similar to that of C/C++. If a global host variable and a local host variable have the same name, the local variable (i.e. the variable having the narrower scope) will take precedence over the global variable (i.e. the variable having the broader scope).

The precompiler is capable of handling 50 levels of overlapping variables.

##### Example

The following example shows how the preprocessor handles multiple variables that have the same name but are declared such that they have different scopes. The locally declared variable name (indicated by #2) takes priority over the global variable name (indicated by #1) within the myfunc() function. Therefore, when reference is made to a variable called name within the function (at #3), this is handled as a reference to the local variable.

```
EXEC SQL BEGIN DECLARE SECTION;	
char name[20];			<- #1
EXEC SQL END DECLARE SECTION;	

int myfunc(void)
{
EXEC SQL BEGIN DECLARE SECTION;	
char name[20];			<- #2
EXEC SQL END DECLARE SECTION;	

EXEC SQL INSERT INTO T1 VALUES (:name);		<- #3
}
```

#### Example

The following example shows how to declare various kinds of host variables:

```
EXEC SQL BEGIN DECLARE SECTION;	<- #1
int x, y, z;	<- #2
char c1[50], c2[100]; 		<- #3
varchar v1[50]; 		<- #4
struct tag1 
{	
int  x;
char  y[50];
varchar  z[50];
} st1;            		<- #5
struct tag1 st2; 		<- #6
EXEC SQL END DECLARE SECTION; 	<- #7
```

\#1: Indicates the beginning of the host variable declaration section

\#2: Declares the variables x, y, and z as int type host variables. 

\#3: Declares the variables c1 and c2 as char type variables that are 50 and 100 bytes long, respectively. 

\#4: Declares the variable v1 as a varchar type variable 50 bytes long. 

\#5: Defines a structure type called tag1, and declares the variable st1, which is of type tag1. 

\#6: Declares the variable st2, which is also of type tag1.

\#7: Indicates the end of the host variable declaration section. 

### Data Type Definition 

In addition to the data types that are supported for use in embedded SQL statements, it is also possible to use host variables based on user-defined types in embedded SQL statements. Such user-defined types are defined using the typedef statement.

#### Description

Definitions of data types intended for use as host variable data types must be indicated in a way such that the preprocessor can recognize them. The data type definition (i.e. the typedef statement) can only be located in the host variable declaration section. Newly defined data types can be used as host variables, just like other data types.

#### Examples

Various examples of data type definitions are shown below.

[Example 1] The following example shows the use of the typedef keyword:

```
EXEC SQL BEGIN DECLARE SECTION;	
typdef unsigned int UINT;
typdef unsigned char UCHAR;
EXEC SQL END DECLARE SECTION; 
```

[Example 2] The following examples illustrate various ways to define data types and structures.

(1) This example shows a data type definition that follows the definition of the structure on which it is based:

```
EXEC SQL BEGIN DECLARE SECTION;	
struct department
{
    short dno;
    char  dname[30+1];
    char  dep_location[9+1];
    int   mgr_no;
};
typedef struct department department;
EXEC SQL END DECLARE SECTION; 
```

(2) This example shows how to define a structure and the corresponding data type at the same time:

```
EXEC SQL BEGIN DECLARE SECTION;	
typedef struct department
{
    short dno;
    char  dname[30+1];
    char  dep_location[9+1];
    int   mgr_no;
} department;
EXEC SQL END DECLARE SECTION; 	
```

(3) This example shows a data type definition that precedes the definition of the structure on which it is based:

```
EXEC SQL BEGIN DECLARE SECTION;	
typedef struct department department;
struct department
{
    short dno;
    char  dname[30+1];
    char  dep_location[9+1];
    int   mgr_no;
};
EXEC SQL END DECLARE SECTION; 	
```

### Function Argument Declaration Section

When using a function argument as a host variable, it is necessary to have a way to provide information about the function arguments to the C/C++ precompiler. The function argument declaration section plays the role of providing information about function arguments to the C/C++ precompiler.

#### Syntax

The syntax of the function argument declaration section is as follows: 

```
EXEC SQL BEGIN ARGUMENT SECTION;
/* Declare function arguments to be used as host variables */
EXEC SQL END ARGUMENT SECTION;
```

The function argument declaration section begins with the EXEC SQL BEGIN ARGUMENT SECTION statement and ends with the EXEC SQL END ARGUMENT SECTION statement. Function arguments to be used as host variables must be declared between these two statements. 

The function arguments that are declared within the function argument declaration section must be exactly the same as the function arguments declared in the function header.

#### Description

The function argument declaration section can be located only inside functions that are found inside the file to be precompiled (i.e. the file with the .sc extension). Additionally, the limitations that apply to the host variable declaration section also apply to the function argument declaration section.

####  Sample Program

##### argument.sc

The sample program can be found at $ALTIBASE_HOME/sample/APRE/argument.sc

##### Result of Execution

```
$ is –f schema/schema.sql
$ make argument
$ ./argument
         <ARGUMENT> 
```



## 4. C Preprocessor

--------------

### C Preprocessor Overview

The purpose of the APRE C/C++ preprocessor is to process C preprocessor directives. The APRE C/C++ preprocessor can handle most directives, including the #include directive for specifying source files to include, the #define directive for defining macros, and the #if directive for conditionally including source code.

#### How the C Preprocessor Works

The APRE C/C++ preprocessor recognizes most C preprocessor commands, and efficiently performs macro substitutions. It also includes files as required, and includes or excludes source text on the basis of conditions. The APRE C/C++ preprocessor uses the macro values obtained in the preprocessing step to modify the source text, and then generates an output file.

##### Example

The following example illustrates how the APRE C/C++ preprocessor handles preprocessor directives:

```
#include “my_header.h”
...
#if A
char name[10];
#endif
...
```

Assume that the file my_header.h is in the current directory and contains the following directive:

```
#define A 1
```

In the above example, the APRE C/C++ preprocessor first reads my_header.h and remembers the definition of the value A. Therefore, when it subsequently processes the #if condition, it substitutes 1 for A. Because the #if condition is thus true, the declaration of the name array is included in the source file (i.e. the output text). If the #if condition had evaluated to false, the name array declaration would have been excluded from the source file.

### C Preprocessor Directives

The C preprocessor directives that the APRE*C/C++ preprocessor recognizes are #define, #undef, #include, #if, #ifdef, #ifndef, #else, #elif and #endif.

#### \#define, \#undef

\#define defines the name of a macro to be used by the APRE C/C++ preprocessor, while #undef deletes a previously defined macro.

##### Example

```
...
#define A
#define func()
...
#undef A
#undef func
```

In the above example, the APRE C/C++ preprocessor handles the #define command and stores the names A and func() in a symbol table, and then performs the required macro substitutions whenever the names A and func() subsequently appear. Finally, when the APRE C/C++ preprocessor encounters the #undef command, it deletes the stored names from the symbol table.

#### \#include

This directive instructs the APRE C/C++ preprocessor to read the specified external source file and incorporate any #define macros and variables found in the external source file. 

The portion of the files referenced using #include directives that is actually incorporated in the source text varies depending on how the -parse option is set. 

#### \#if

When the APRE C/C++ preprocessor encounters the #if directive, it evaluates the given condition and uses the result of the evaluation as the basis on which to determine whether to include the source text between the #if and #endif directives in the precompile operation.

##### Example

```
#define A 1 + 1
#define B A - 2
...
#if B
int var;
#endif
...
#if defined(A)
int var2;
#endif
```

In the above example, the APRE C/C++ preprocessor substitutes A-2 for B, and then 1+1 for A, when evaluating the first #if condition. This results in the expression 1+1-2, which evaluates to 0, or false. Therefore, the source text between the first #if and #endif commands is not included in the output.

The second condition, #if defined, is handled in the same way as an #ifdef condition.

#### \#ifdef

When the APRE C/C++ preprocessor encounters the #ifdef condition, it determines whether to include the source text between the #ifdef and #endif directives based on whether the name that follows the #ifdef keyword is a defined name.

##### Example

```
#define A
#ifdef A
int var;
#endif
...
```

In the above example, the text “int var;” is included in the output of the precompile operation because A has been defined.

#### \#ifndef

If there is a reverse of \#ifdef and there is no defined name, the next source code is preprocessed.

##### Example

```
#define A
#ifndef A
int var;
#endif
...
```

In this example, the text “int var;“ is excluded from the output of the precompile operation because A has been defined.

#### \#else

If all \ #if, \ #ifdef and \ #ifndef conditional clauses are false, the source code following the last \#else is preprocessed.

##### Example

```
...
#define A 0
#if A
int var1;
#else
int var2;
#endif
...
```

In the above example, the source text between the #else and #endif directives will be included in the output of the precompile operation because the #if condition evaluates to false.

#### \#elif

If this directive is provided between an #if, #ifdef or #ifndef condition and the corresponding #endif directive, and the first condition evaluates to false, then the #elif condition is evaluated, and the source text between the #elif and #endif directives is included in the output of the precompile operation if the #elif condition evaluates to true.

##### Example

```
...
#define A 0
#define B 1
#if A
int var1;
#elif B
int var2;
#else
int var3;
#endif
...
```

In the above example, the source text between the #elif and #else directives is included in the output of the precompile operation, because the #if condition is not satisfied and the #elif condition is satisfied.

#### \#endif

This indicates the end of a block of text that is included or excluded based on the result of evaluation of an #if, #ifdef or #ifndef condition. 

### Limitations on the Use of the Preprocessor

This section covers a few limitations of the APRE C/C++ Preprocessor, including some directives that it ignores.

#### Ignored Directives

The APRE C/C++ preprocessor ignores some C preprocessor directives, because they are not necessary for the precompile operation. One example is the #pragma directive, which does not need to be processed by the precompiler because it is used only by the C compiler. 

The commands that are ignored by the APRE C/C++ preprocessor during the precompile operation are as follows:

##### \#

This directive converts a preprocessor macro parameter to a string constant.

##### \#\#

This directive merges two preprocessor tokens in a macro definition.

##### \#error

This directive is used to output a compile-time error message. 

##### \#pragma

The #pragma directive is used to pass implementation-dependent information to the C compiler.

##### \#line

This directive is used to provide line number information to the C compiler. 

#### Limitations on the Use of #define

The use of the #define directive with the APRE C/C++ precompiler is limited in one important way: names defined using the #define directive cannot be used within embedded SQL statements.

##### Example

```
#define RESEARCH_DEPT   40
...
EXEC SQL SELECT empno, sal
    INTO :emp_number, :salary /* host arrays */
    FROM emp
    WHERE deptno = RESEARCH_DEPT;  /* INVALID! */
```

In the above example, the embedded SQL statement would result in an error, because 40 will not be substituted for RESEARCH_DEPT in the WHERE clause.

#### Limitations on the Use of #if

When a user-defined macro function is used in an #if condition, the condition may not evaluate as expected, so it is recommended that #if conditions not contain user-defined macro functions.

##### Example

```
#define fun(X,Y) X-Y
...
#if fun(1,1)
int var;
#else
int var2;
#endif
...
```

#### Limitations on the Use of #include 

The APRE C/C++ Preprocessor raises an error if a header file that is included using the #include directive contains embedded SQL statements. Additionally, header files included in this way must not include declarations of VARCHAR type variables. If you need to include a header file that contains embedded SQL statements or VARCHAR declarations, you must use the EXEC SQL INCLUDE statement to include the header file.

When EXEC SQL INCLUDE is used to include a header file, the APRE C/C++ Preprocessor includes the entire contents of the header file in the output source file (i.e. the resultant output file with the .c or .cpp filename extension.). Therefore, it is acceptable for header files included in this way to contain embedded SQL statements and VARCHAR declarations. In contrast, when the #include directive is used to include a header file, APRE only processes the header file's macro commands and C variable declarations.

### Preprocessor Example

The following simple example illustrates how the #define and #ifdef directives can be used to conditionally input data into a database. Because a macro called ALTIBASE is defined, the host variable s_goods_alti is declared. If it were not defined, the host variable s_goods_ora would be declared.

##### Example

< Sample Program : macro.sc > 

```
/*********************************************************

 * SAMPLE : MACRO

 *          1. Using #define, #if, #ifdef 

 *********************************************************/



/* specify path of header file */

EXEC SQL OPTION (INCLUDE=./include);

/* include header file for precompile */

EXEC SQL INCLUDE hostvar.h;



/* define Altibase */

#define Altibase



int main()

{

    /* declare host variables */

    char usr[10];

    char pwd[10];

    char conn_opt[1024];



    /* structure type */

#ifdef Altibase

    goods   s_goods_alti;

#else

    goods   s_goods_ora;

#endif



    int i;



    printf("<INSERT>\n");



    /* set username */

    strcpy(usr, "SYS");

    /* set password */

    strcpy(pwd, "MANAGER");

    /* set various options */

    strcpy(conn_opt, "DSN=127.0.0.1;CONNTYPE=1"); /* PORT_NO=20300 */



    /* connect to altibase server */

    EXEC SQL CONNECT :usr IDENTIFIED BY :pwd USING :conn_opt;  

    /* check sqlca.sqlcode */

    if (sqlca.sqlcode != SQL_SUCCESS) 

    {

        printf("Error : [%d] %s\n\n", SQLCODE, sqlca.sqlerrm.sqlerrmc);

        exit(1);

    }



    /* use structure host variables */



#ifdef Altibase

    strcpy(s_goods_alti.gno, "F111100010");

    strcpy(s_goods_alti.gname, "Altibase");

    strcpy(s_goods_alti.goods_location, "AD0010");

    s_goods_alti.stock = 9999;

    s_goods_alti.price = 99999.99;

#else

    strcpy(s_goods_ora.gno, "F111100011");

    strcpy(s_goods_ora.gname, "ORACLE");

    strcpy(s_goods_ora.goods_location, "AD0011");

    s_goods_ora.stock = 0001;

    s_goods_ora.price = 00000.01;

#endif



    /* the select insertion useing #ifdef. */



EXEC SQL INSERT INTO GOODS VALUES (

#ifdef Altibase

:s_goods_alti

#else

:s_goods_ora

#endif

);



    printf("------------------------------------------------------------------\n");

    printf("[Structure Host Variables]                                        \n");

    printf("------------------------------------------------------------------\n");



    /* check sqlca.sqlcode */

    if (sqlca.sqlcode == SQL_SUCCESS) 

    {

        /* sqlca.sqlerrd[2] holds the rows-processed(inserted) count */

        printf("%d rows inserted\n\n", sqlca.sqlerrd[2]);

    }

    else 

    {

        printf("Error : [%d] %s\n\n", SQLCODE, sqlca.sqlerrm.sqlerrmc);

    }



    /* disconnect */

    EXEC SQL DISCONNECT;

    /* check sqlca.sqlcode */

    if(sqlca.sqlcode != SQL_SUCCESS) 

    {

        printf("Error : [%d] %s\n\n", SQLCODE, sqlca.sqlerrm.sqlerrmc);

    }

}
```

### The ALTIBASE_APRE Macro

The APRE C/C++ preprocessor contains a predefined macro called ALTIBASE_APRE, which is used when determining whether to precompile certain portions of source code. The ALTIBASE_APRE macro is particularly useful when preprocessing source code that contains large and unnecessary header files that are not necessary for the precompile operation.

The following example illustrates the use of the ALTIBASE_APRE macro to avoid precompiling the header.h file.

##### Example

```
#ifndef ALTIBASE_APRE
#include <header.h>
#endif
```

In the above example, the header.h file will not be read while the APRE C/C++ preprocessor precompiles the source code, because the ALTIBASE_APRE macro is defined within APRE, and thus APRE evaluates the #ifndef condition as false. However, the ALTIBASE_APRE macro is not defined within a separate C or C++ compiler, and thus the compiler will evaluate the #ifndef condition as true, and include the header.h file in the compile operation.

The ALTIBASE_APRE macro is intended for use with the #ifdef and #ifndef preprocessor directives.

> ### Consideration
>
> This section explains some considerations to keep in mind when using the APRE C/C++ Preprocessor.
>

#### Defining Macros

If a macro is defined using a command-line option when executing the C compiler, then in most cases the same macro must also be defined using the -D command-line option when using the APRE C/C++ precompiler. For example, if a C compiler is executed from the command line as shown below:

```
cc -DDEBUG ...
```

Then the DEBUG macro should also be defined when executing the APRE C/C++ precompiler, before executing the C compiler. This is shown below:

```
apre -DDEBUG ...
```

#### include Path

All locations for include files used during preprocessing must be specified with the -I option. For example, if the header file located at /home/project/include needs to be refered, the include path must be specified as follow when  APRE\*C/C++ preprocessing and C compilation.

```
apre -I/home/project/include test.sc
cc -I/home/project/include ... test.c
```



## 5. Host Variable Data Types

-----------------------

### Overview

Host variables differ from variables in C or C++ applications in how they are used, in their functionality, and in how they are declared. It follows that host variable data types are different from C data types. The following data types can be used as host variables:

-   Data type that can be used as data type of host variable

-   Extended data types provided by embedded SQL statements

-   Relationship between column type and host variable type

#### Term Description

This section describes some of the terms that will be used in this chapter

##### Host Variables

Host variables are variables declared in host variable declaration and used in embedded SQL statements.

##### Fundamental Variables

All variables declared and used in a C or C++ program. 

##### Host Variable Types (Host Variable Data Types)

Host variable types are data types of host variables, including most data types used in C or C ++ and extended data types provided by embedded SQL statements.

##### Fundamental Variable Types (Fundamental Variable Data Types)

Fundamental variable types are data types used in C or C ++ programs. In this chapter, they are used to compare with host variable types to help developers understand.

##### Column Types

The column type is a data type of a column defined in a table of a database server. When determining the data type of a host variable, a compatible data type should be used in consideration of the corresponding column type.

#### Host Variable Data Type

The following are the data types that can be used as data types of host variables.

-   Most data types used in C or C++
-   Extended data types provided by embedded SQL statements
-   Data type declated in host variable declaration.

### Fundamental C/C++ Data Types

Most of the fundamental data types supported for use as C and C++ data types can also be used for host variables. The fundamental C/C++ types that can be used for host variables are set forth below.

#### Numeric Types

The following numeric types can be used as host variable data types:

##### Integer Types

int, short int, long int, short, long, long long, unsigned int, unsigned short
int, unsigned long int, unsigned short, unsigned long, unsigned long long

##### Real Number Types

float, double

##### Unavailable Numeric Type

The long double type is not supported for use as a host variable data type.

####  Character Types

The following character types can be used as host variable data types:

##### Character types

char, unsigned char

> ##### Precautions
>
> An output host variable corresponding to a CHAR type database column must be declared so that its length is one (1) byte longer than the length of the database column. The reason for this is that the length of the data stored in a CHAR type column is fixed, so the length of the data that are returned will always be the same as the length of the column, and the host variable requires one additional byte to store the NULL terminating character at the end. If a host variable is not declared so that it is at least one byte longer than the database column to which it corresponds, then when a SELECT or FETCH statement is executed, the value returned inthe sqlca.sqlcode variable will be SQL_SUCCESS_WITH_INFO rather than SQL_SUCCESS.
> 
> When declaring a host variable for use with a database column, it is common to declare and use a single “input/output” host variable, that is, a host variable that is used as both an input and output variable for the column, rather than declaring separate input and output host variables. Therefore, for the above reason pertaining to output host variables, when declaring an input/output variable of this type for use with a CHAR type database column, it must be declared such that its length is one byte greater than the length of the column.

#### Pointer Types

All host variable types that are available in APRE can be used as base types for pointers.

##### char\*

A Pointer to a character string can be used as a host variable. 

The char* type is convenient for use when using a function argument as a host variable. For more information about using a function argument as a host variable, please refer to Chapter 3: Host Variable Declaration Section.

##### MAX_CHAR_PTR

When using a pointer to a character string as a host variable, the precompiler assumes that the maximum size of the string to which the host variable points is 65000 bytes, which is predefined in the internally provided MAX_CHAR_PTR macro. This is because the precompiler cannot know the actual allocated size. Therefore, when a smaller amount of memory than the value of the MAX_CHAR_PTR macro is allocated to a char* type output host variable, care must be taken because a character string that is longer than the allocated memory size and smaller than the value of the MAX_CHAR_PTR macro can be stored in the host variable. In this case, memory corruption will occur.

It may become necessary to declare a pointer to a string that is more than 65000 bytes long. In such cases, before declaring the char* type host variable, use the MAX_CHAR_PTR macro to redefine the maximum size of a string to which a char* type host variable can point.

Redefine the MAX_CHAR_PTR macro as follows: 

```
#define MAX_CHAR_PTR 90000
```

After the MAX_CHAR_PTR macro has been redefined, it becomes possible to allocate an amount of memory equal to the value of the MAX_CHAR_PTR macro, and to declare a char* type host variable that points to a string that occupies this much memory.

##### Structure Pointers

A pointer to a structure can be used as a host variable data type. A pointer to a structure is convenient to use when using a function argument as a host variable. For more information about using a function argument as a host variable, please refer to Chapter 3: Host Variable Declaration Section. 

After a pointer to a structure has been declared, be sure to allocate an appropriate amount of space in memory. This is critical, because the precompiler has no way of checking whether or not enough space for the structure has been allocated.

##### Pointer to an Array

The number of array elements should be specified with the FOR clause when replacing pointer type variables to a 1 dimensional array as input host variable within the INSEART statement. 

However, unwanted outcome could be caused when using a 2 dimensional pointer array as a host variable or using 1 dimensional array which indicates the point in the INSERT statement or FOR clause. 

char, varchar, APRE_BINARY, APRE_BINARY2, APRE_BYTES, APRE_NIBBLE,
APRE_NUMERIC, APRE_BLOB, APRE_CLOB, APRE_BIT, APRE_VARBYTES

To use a pointer to an array of integer values as an input host variable in an INSERT statement, use the FOR clause, as shown in the following example:

```
int sInt[10];
int *sIntptr;
sIntptr = sInt;

EXEC SQL FOR 10 INSERT INTO T2 VALUES ( :sIntptr );
```

For more information about the use of the FOR clause, please refer to Chapter 9: Using Arrays in Embedded SQL Statements. 

Also, it does not work properly when using a 2-dimensional pointer array as a host variable as follows:

```
int sInt[2][10];
int (*sIntptr)[10];
sIntptr = sInt;
EXEC SQL FOR 10 INSERT INTO T2 VALUES ( :sIntptr );
```

##### Example

[Example 1] This example demonstrates the use of the v_ename char* type input host variable.

\< Sample Program : argument.sc \>

```
void ins_employee(int v_eno, char* v_ename, short v_dno)
{
EXEC SQL BEGIN ARGUMENT SECTION;
    int    v_eno;
    char*  v_ename;
    short  v_dno;
    EXEC SQL END ARGUMENT SECTION;

    EXEC SQL INSERT INTO TODAY_EMPLOYEE 
VALUES (:v_eno, :v_ename, :v_dno);
}
```

[Example 2] The following example demonstrates how to define the MAX_CHAR_PTR macro.

```
#define MAX_CHAR_PTR 90000
EXEC SQL BEGIN DECLARE SECTION;
char* var1;
EXEC SQL END DECLARE SECTION;

Or

EXEC SQL BEGIN DECLARE SECTION;
#define MAX_CHAR_PTR 90000
char* var1;
EXEC SQL END DECLARE SECTION;
```

[Example 3] The followhing shows various example of defining structure pointers

(1) Declare a structure and a pointer to the structure in the same statement.

```
struct tag1 
{ 
    int a; 
} *A; 
A = (struct tag1*)(malloc(sizeof(struct tag1))); 
INSERT INTO T1 VALUES ( :A ); or INSERT INTO T1 VALUES (:A->a); 
```

(2) First declare the structure, and then declare a pointer to the structure in a separate statement.

```
struct tag1 
{ 
    int a; 
}; 
struct tag1 *A; 
A = (struct tag1*)(malloc(sizeof(struct tag1))); 
SELECT I1 INTO :A FROM T1; or SELECT I1 INTO :A->a FROM T1; 
```

(3) First declare a structure and define a type based on the structure in the same statement, and then declare a pointer to the type in a separate statement.

```
typedef struct tag1 
{ 
    int a; 
}tag1; 
tag1 *A; 
A = (tag1*)(malloc(sizeof(tag1))); 
SELECT I1 INTO :A FROM T1; or SELECT I1 INTO :A->a FROM T1; 
```

In the following example, vDataT2 is a pointer to a structure, and is used as an input host variable.

\< Sample Program : pointer.sc \>

```
EXEC SQL BEGIN DECLARE SECTION; 
typedef struct tag 
{    
    char n1[11]; 
    int  n2; 
}tag; 
     
tag *dataT2; 
EXEC SQL END DECLARE SECTION; 

 void ins_t2(tag* vDataT2) 
{ 
    EXEC SQL BEGIN ARGUMENT SECTION; 
    tag *vDataT2; 
    EXEC SQL END ARGUMENT SECTION; 

    EXEC SQL INSERT INTO T2 VALUES (:vDataT2->n1, :vDataT2->n2); 
}
```

#### Structure Types

##### struct

Structures (struct) can be used as host variable data types. 

Using the structure type obviates the need to list multiple host variables one by one in an embedded SQL statement when retrieving data from or inserting data into multiple columns in a table. Instead, it is possible to use a single host variable, which makes the development process much more convenient. For example, a structure-type host variable can be used in the VALUES clause of an INSERT statement, or in the INTO clause of a SELECT statement. 

Even arrays of structures and structures containing arrays are valid data types for use as host variables. For more information about the use of arrays, please refer to Chapter 9: Using Arrays in Embedded SQL Statements.

##### Limitations

-   When a host variable is a structure, the corresponding indicator variable must also be a structure, and must have the same number of elements as the host variable.

```
Example) EXEC SQL BEGIN DECLARE SECTION;
struct tag1 { int i1; int i2; } var1;
struct tag2 { int i1_ind; int i2_ind; } var1_ind1;
struct tag3 { int i1_ind; int i2_ind; int i3_ind; } var1_ind2; 
EXEC SQL END DECLARE SECTION;

EXEC SQL INSERT INTO T1(I1, I2) 
VALUES (:var1 :var1_ind1);	(O)
EXEC SQL INSERT INTO T1(I1, I2) 
VALUES (:var1 :var1_ind2);	(X)
```

-   Nested structures cannot be used as host variables. In other words, a structure cannot have another structure as one of its constituent elements.

```
Example) EXEC SQL BEGIN DECLARE SECTION;
struct tag1 
{ 	
int i1; 
struct tag2 
{ 
int i2; 
int i3; 
} sub_var; 
} var1; 		(X)
EXEC SQL END DECLARE SECTION;
```

-   It is impossible to use an indicator variable with a host variable that is an array of structures. This means that it is necessary to guarantee that no NULL column values are returned when using an array of structures as an output host variable. If a NULL column value is returned, the value stored in the sqlca.sqlcode variable will be SQL_SUCCESS_WITH_INFO.

```
Example) EXEC SQL BEGIN DECLARE SECTION;
struct tag1 {int i1; int i2; char i3[11]; } var1[10];
struct tag2 {int i1_ind; int i2_ind; int i3_ind; } var1_ind[10];
EXEC SQL END DECLARE SECTION;

EXEC SQL INSERT INTO T1(I1, i2, i3) 
VALUES (:var1 :var1_ind);	(X)
```

-   When using an array of structures as a host variable in the INTO clause of a SELECT or FETCH statement, only one output host variable can be used. In other words, such an output host variable cannot be used with other host variables. Therefore, when using an array of structures as an output host variable in the INTO clause, the underlying structure will need the same number of constituent elements as the number of columns in the select list.  
    Similarly, when using an array of structures as a host variable in the VALUES clause of an INSERT statement, only one input host variable can be used. In other words, such an input host variable  Host Variable Data Types cannot be used with other host variables. Therefore, when using an array of structures as an input host variable in the VALUES clause, the underlying structure will need the same number of constituent elements as the number of columns in the INSERT statement.

```
Example) EXEC SQL BEGIN DECLARE SECTION;
struct tag1 { int i1; int i2; } var1[10];
int var2[10];
EXEC SQL END DECLARE SECTION;

EXEC SQL INSERT INTO T1(I1, I2, i3) 
VALUES (:var1, :var2);		(X)
```

-   The last two limitations are due to the internal rule that requires all host variables to be included in the structure when the host variable is a structure array.

##### Examples

The following example demonstrates the use of the structure type. 

In this example, a structure type called goods is defined, and the host variable s_goods, which is of the goods type, is declared. The s_goods variable is then used as an input host variable in an INSERT statement. 

\< Sample Program : hostvar.h \>

```
EXEC SQL BEGIN DECLARE SECTION;
typedef struct goods
{
    char   gno[10+1];
    char   gname[20+1];
    char   goods_location[9+1];
    int    stock;
    double price;
} goods;
EXEC SQL END DECLARE SECTION;
```

\< Sample Program : insert.sc \>

```
/* specify path of header file */
EXEC SQL OPTION (INCLUDE=./include);
/* include header file for precompile */
EXEC SQL INCLUDE hostvar.h;

EXEC SQL BEGIN DECLARE SECTION;
goods   s_goods;
EXEC SQL END DECLARE SECTION;

strcpy(s_goods.gno, "F111100003");
strcpy(s_goods.gname, "XX-102");
strcpy(s_goods.goods_location, "AD0003");
s_goods.stock = 6000;
s_goods.price = 10200.96;

EXEC SQL INSERT INTO GOODS VALUES (:s_goods);
```

### Extended APRE Data Types

Beyond the fundamental C/C++ data types, APRE provides additional data types for use as host variables and in embedded SQL statements. These extended data types are described below, along with how to use them.

#### VARCHAR

##### varchar

The varchar type may be declared in either lower case or upper case, that is, as either varchar or VARCHAR. Internally, it is a kind of structure. For example, if a varchar type variable is declared as follows:

```
varchar a[10];
```

The underlying structure would appear thus:

```
struct { int len; char arr[10] ;}a;
```

The constituent elements of the varchar type variable can thus be referred to using the period (“.”) operator in this way: a.rr

The varchar type has its own built-in indicator variable. This role is played by the first constituent element, namely len. Therefore, when it is necessary to use an indicator variable with a varchar type host variable, there is no need to declare a separate indicator variable, thus making the use of the varchar type very convenient.

Although the varchar type comes with its own indicator variable, it is still possible to declare and use a separate indicator variable. This is useful when the varchar type is just one element inside another structure type host variable and a structure type indicator variable is declared for use with the structure type host variable, so that a separate indicator variable corresponding to the varchar type element can be provided inside the structure type indicator variable.

##### Advantage

Because the varchar type has its own internal indicator variable, there is no need for the user to specify a separate indicator variable. This makes it convenient to use the varchar type when it is necessary to use an indicator variable.

##### Considerations

-   Unless a separate indicator variable is specified for use with a varchar type host variable, len, one of its constituent elements, will function as the indicator variable. Therefore, when using a varchar type variable as an input host variable, it is necessary to expressly specify the value of len when not using a separate indicator variable. If it is desired to input NULL data, then set the value of len to -1. When entering non-NULL data, set the value of len to the actual length of the arr element, excluding the trailing NULL character.

```
Example) EXEC SQL BEGIN DECLARE SECTION;
varchar var1;
EXEC SQL END DECLARE SECTION;

strcpy(var1.arr, “ABC”);
var1.len = strlen(var1.arr);
EXEC SQL INSERT INTO T1(I1) 
VALUES (:var1);		(O)
```

-   When using the varchar type as an output host variable that will receive a value from a CHAR type column, be sure to declare the length of the host variable so that it is one (1) byte longer than the size of the corresponding CHAR type column. The reason for this is that the length of the data stored in a CHAR type column is fixed, so the length of the data that are returned will always be the same as the length of the column, and the host variable requires one additional byte to store the NULL terminating character at the end. If a host variable is not declared so that it is at least one character longer than the database column to which it corresponds, then when a SELECT or FETCH statement is executed, the value returned in the sqlca.sqlcode variable will be SQL_SUCCESS_WITH_INFO.
  
-   When using a two-dimensional varchar array as a host variable in the INTO clause of a SELECT or FETCH statement, only one output host variable can be used. In other words, such an output host variable cannot be used with other output host variables. Therefore, when using a two-dimensional varchar array as an output host variable in an INTO clause, the corresponding select list can contain only one column.  
    Similarly, when using a two-dimensional varchar array as a host variable in the VALUES clause of an INSERT statement, only one input host variable can be used. In other words, such an input host variable cannot be used with other input host variables. Therefore, when using a two-dimensional varchar array as an input host variable in the VALUES clause of an INSERT statement, the VALUES clause can contain only one column value.  
    The reason for this is that the varchar type is a structure, and thus the limitation on the use of structures also applies to the varchar type.

```
Example) EXEC SQL BEGIN DECLARE SECTION;
varchar var1[10][10+1];
int var2[10];
EXEC SQL END DECLARE SECTION;

EXEC SQL INSERT INTO T1(I1, I2) 
VALUES (:var1, :var2);		(X)
```

##### Example

The following example shows the use of the varchar type. 

In this example, both the input host variable and the output host variable are varchar type host variables. The variable s_cus_job is the input host variable, while the variable s_address is the output host variable. The programmer is responsible for checking the length of s_cus_job.arr and specifying it in s_cus_job.len. Although not shown in the example, after the SELECT statement is executed, it will be necessary to check whether the value of s_address.len is -1, which would indicate that a NULL value was returned.

\< Sample Program : varchar.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
char    s_cname[20+1];
varchar s_cus_job[20+1];
varchar s_address[60+1];
EXEC SQL END DECLARE SECTION;

strcpy(s_cus_job.arr, "WEBMASTER");
s_cus_job.len = strlen(s_cus_job.arr);

EXEC SQL SELECT CNAME, ADDRESS 
INTO :s_cname, :s_address 
FROM CUSTOMERS 
            WHERE CNO = BIGINT'7' 
AND CUS_JOB = :s_cus_job;
```

#### Date Types

APRE date types can be used only with DATE type database columns.

Three date types are provided for use within APRE. The developer can choose the date type that is most appropriate for the task at hand.

##### SQL_DATE_STRUCT 

This type consists of year, month, and date elements. Its structure is shown below:

```
typedef struct tagDATE_STRUCT {
SQLSMALLINT  year;
SQLSMALLINT month;
SQLSMALLINT day;
} DATE_STRUCT;
```

##### Example

The following example shows the use of the SQL_DATE_STRUCT type.

In this example, s_date is used as both an input and output host variable. 

\< Sample Program : date.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
SQL_DATE_STRUCT s_date;
int s_ind;
EXEC SQL END DECLARE SECTION;

EXEC SQL SELECT JOIN_DATE 
INTO :s_date :s_ind 
FROM EMPLOYEES 
WHERE ENO = 3;

s_date.year  = 2003;
s_date.month = 5;
s_date.day   = 9;

EXEC SQL UPDATE EMPLOYEES 
SET JOIN_DATE = :s_date 
WHERE ENO = 3;
```

##### SQL_TIME_STRUCT 

This type consists of hour, minute, and second elements. Its structure is shown below:

```
typedef struct tagTIME_STRUCT {
SQLSMALLINT hour;
SQLSMALLINT minute;
SQLSMALLINT second;
} TIME_STRUCT;
```

##### Example

The following example shows the use of the SQL_TIME_STRUCT type. 

In this example, s_time is used as both an input and output host variable. 

\< Sample Program : date.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
SQL_TIME_STRUCT s_time;
int s_ind;
EXEC SQL END DECLARE SECTION;

EXEC SQL SELECT JOIN_DATE 
INTO :s_time :s_ind 
FROM EMPLOYEES 
WHERE ENO = 3;

s_time.hour   = 12;
s_time.minute = 12;
s_time.second = 12;

EXEC SQL UPDATE EMPLOYEES 
SET JOIN_DATE = :s_time 
WHERE ENO = 4;
```

##### SQL_TIMESTAMP_STRUCT 

This type consists of year, month, date, hour, minute, second, and nanosecond elements. Its structure is shown below. The fraction element is the element in which the nanoseconds (i.e. billionths of a second) are stored.

```
typedef struct tagTIMESTAMP_STRUCT {
SQLSMALLINT  year;
SQLSMALLINT month;
SQLSMALLINT day;
SQLSMALLINT hour;
SQLSMALLINT minute;
SQLSMALLINT second;
SQLINTEGER  fraction;
} TIMESTAMP_STRUCT;
```

##### Example

The following example shows the use of the SQL_TIMESTAMP_STRUCT type.

In this example, s_timestamp is used as both an input and output host variable. 

\< Sample Program : date.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
SQL_TIMESTAMP_STRUCT s_timestamp;
int s_ind;
EXEC SQL END DECLARE SECTION;

EXEC SQL SELECT JOIN_DATE 
INTO :s_timestamp :s_ind 
FROM EMPLOYEES 
WHERE ENO = 3;

s_timestamp.year     = 2003;
s_timestamp.month    = 5;
s_timestamp.day      = 9;
s_timestamp.hour     = 4;
s_timestamp.minute   = 0;
s_timestamp.second   = 15;
s_timestamp.fraction = 100000;

EXEC SQL UPDATE EMPLOYEES 
SET JOIN_DATE = :s_timestamp 
WHERE ENO = 5;    
```

##### SQL_NUMERIC_STRUCT 

When using this type, NUMERIC data can be passed

The structure of this type is:

```
typedef struct tagSQL_NUMERIC_STRUCT
{
	SQLCHAR		precision;
	SQLSCHAR	scale;
	SQLCHAR		sign;	/* 1=pos 0=neg */
	SQLCHAR		val[SQL_MAX_NUMERIC_LEN];
} SQL_NUMERIC_STRUCT;
```

##### Example

The following is an example of using the SQL_NUMERIC_STRUCT type

This example uses s_price as an input or output host variable.

\< Sample Program : date.sc \>

```
/* declare host variables */
EXEC SQL BEGIN DECLARE SECTION;
char                 s_gno[10+1];
char                 s_gname[20+1];
char                 s_goods_location[9+1];
int                  s_stock;
SQL_NUMERIC_STRUCT   s_price;
EXEC SQL END DECLARE SECTION;

int s_price_val = 0;

/* use scalar host variables */
strcpy(s_gno, "F111100002");
strcpy(s_gname, "XX-101");
strcpy(s_goods_location, "FD0003");
s_stock = 5000;

/* set value 123.4 on SQL_NUMERIC_STRUCT */
memset(&s_price, 0, sizeof(s_price));
s_price.precision = 4;
s_price.scale = 1;
s_price.sign = 1;
s_price_val = 1234;
memcpy(&s_price.val, &s_price_val, sizeof(int));

printf("------------------------------------------------------------------\n");
printf("[SQL_NUMERIC_STRUCT Insert]\n");
printf("------------------------------------------------------------------\n");

EXEC SQL INSERT INTO GOODS VALUES (:s_gno, :s_gname, :s_goods_location, :s_stock, :s_price);

memset(s_gname, 0, sizeof(s_gname));
memset(s_goods_location, 0, sizeof(s_goods_location));
s_stock = 0;
memset(&s_price, 0, sizeof(s_price));

printf("------------------------------------------------------------------\n");
printf("[SQL_NUMERIC_STRUCT Select]\n");
printf("------------------------------------------------------------------\n");

EXEC SQL SELECT GNAME, GOODS_LOCATION, STOCK, PRICE INTO :s_gname, :s_goods_location, :s_stock, :s_price FROM GOODS WHERE GNO = :s_gno;
/* check sqlca.sqlcode */
if (sqlca.sqlcode == SQL_SUCCESS)
{
    /* sqlca.sqlerrd[2] holds the rows-processed(inserted) count */
    printf("%d rows select s_gno=%s, s_gname=%s, s_goods_location=%s, s_stock=%d, s_price=%.15G \n\n", 
            sqlca.sqlerrd[2], s_gno, s_gname, s_goods_location, s_stock, APRE_NUMERIC_TO_DOUBLE(s_price));
}
else
{
    printf("Error : [%d] %s\n\n", SQLCODE, sqlca.sqlerrm.sqlerrmc);
}   
```

#### Binary Types

The binary type can be used as a host variable type when a column type is blob, BYTE, or NIBBLE. 

The binary type is internally defined as following:

```
typedef char APRE_CLOB;
typedef char APRE_BLOB;
typedef char APRE_BINARY;
typedef char APRE_BINARY2;
typedef char APRE_BYTES;
typedef char APRE_NIBBLE;
typedef char APRE_VARBYTES;
```

Each of the type is described in detail as follows.

##### APRE_CLOB

This type can be used only with CLOB type database columns. It is essential that an indicator variable be declared and used with this type. 

When using the APRE_CLOB type as an input host variable, set the value of the corresponding indicator variable to -1 to indicate that the value of the host variable is NULL. When the value of the host variable is any other value (i.e. a non-NULL value), set the value of the indicator variable to the length of the data saved in the host variable. 

When using this type as an output host variable, NULL is returned when the indicator variable is -1, and if it is greater than 0, the length of the value stored in the host variable is stored in the indicator variable.

##### Example

The following example demonstrates the use of the APRE_CLOB type.

In this example, ins_clob is an input host variable, and ins_clob_ind is the corresponding input indicator variable. The value of ins_clob_ind is set to the length of the value stored in ins_clob. Meanwhile, sel_clob is an output host variable, and sel_clob_ind is its output indicator variable. After the execution of the SELECT statement, a sel_clob_ind value of -1 means that sel_clob is NULL, whereas a sel_clob_ind value greater than 0 indicates the length of the value stored in sel_clob.

\< Sample Program : binary.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
APRE_CLOB ins_clob[10+1];
APRE_CLOB sel_clob[10+1];
SQLLEN ins_clob_ind;  
SQLLEN sel_clob_ind; 
EXEC SQL END DECLARE SECTION;

memset(ins_clob, 0x41, 10);
ins_clob_ind = 10; /* set length of ins_clob value to indicator variable */

EXEC SQL INSERT INTO T_CLOB
VALUES (:ins_clob :ins_clob_ind);

EXEC SQL SELECT *
INTO :sel_clob :sel_clob_ind
FROM T_CLOB;
```

##### APRE_BLOB

This type can be used only with BLOB type database columns.

It is essential that an indicator variable be declared and used with this type.

When using the APRE_BLOB type as an input host variable, set the value of the corresponding indicator variable to -1 to indicate that the value of the host variable is NULL. When the value of the host variable is any other value (i.e. a non-NULL value), set the value of the indicator variable to the length of the data saved in the host variable. 

When using this type as an output host variable, a value of -1 in the corresponding indicator variable indicates that a NULL value was returned to the host variable, whereas an indicator variable value greater than 0 indicates that a non-NULL value was returned to the host variable, and furthermore indicates the length of the data saved in the host variable.

##### Example

The following example demonstrates the use of the APRE_BLOB type.

In this example, ins_blob is an input host variable, and ins_blob_ind is the corresponding input indicator variable. The value of ins_blob_ind is set to the length of the value stored in ins_blob. Meanwhile, sel_blob is an output host variable, and sel_blob_ind is its output indicator variable. After the execution of the SELECT statement, a sel_blob_ind value of -1 means that sel_blob is NULL, whereas a sel_blob_ind value greater than 0 indicates the length of the value stored in sel_blob

\< Sample Program : binary.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
APRE_BLOB ins_blob[10+1];
APRE_BLOB sel_blob[10+1];
SQLLEN ins_blob_ind; 
SQLLEN sel_blob_ind;
EXEC SQL END DECLARE SECTION;

memset(ins_blob, 0x21, 10);
ins_blob_ind = 10; /* set length of ins_blob value to indicator variable */

EXEC SQL INSERT INTO T_BLOB
VALUES (:ins_blob :ins_blob_ind);

EXEC SQL SELECT *
INTO :sel_blob :sel_blob_ind
FROM T_BLOB;
```

##### APRE_BINARY

This type is identical to the APRE_BLOB type. 

##### Example

The following example illustrates the use of the APRE_BINARY type.

Use ins_blob as the input host variable and ins_blob_ind as the input indicator variable. ins_blob_ind stores the length of ins_blob. Output sel_blob as output host variable Use the indicator variable sel_blob_ind. After executing the SELECT statement, sel_blob_ind stores –1 if the sel_blob value is NULL, otherwise the length of sel_blob is stored.

\< Sample Program : binary.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
APRE_BINARY ins_blob[10+1]; 
APRE_BINARY sel_blob[10+1];
int ins_blob_ind;   
int sel_blob_ind;  
EXEC SQL END DECLARE SECTION;

memset(ins_blob, 0x21, 10);
ins_blob_ind = 10; /* set length of ins_blob value to indicator variable */

EXEC SQL INSERT INTO T_BLOB 
VALUES (:ins_blob :ins_blob_ind);

EXEC SQL SELECT * 
INTO :sel_blob :sel_blob_ind 
FROM T_BLOB;
```

##### APRE_BINARY2

It has the same characteristics as APRE_BLOB and APRE_BINARY. However, when the data size of the input host variable is less than 128KB, the performance is improved, and the maximum data size is 100MB. When the data size exceeds 128KB, the use of the APRE_BLOB and APRE_BINARY types is recommended to improve performance and save memory.

##### Example

The following example shows how to use the APRE_BINARY2 type.

Use ins_blob as the input host variable and ins_blob_ind as the input indicator variable. ins_blob_ind stores the length of ins_blob. 

Output sel_blob as output host variable Use sel_blob_ind as an indicator variable. 

After executing the SELECT statement, sel_blob_ind stores –1 if the sel_blob value is NULL, otherwise the length of sel_blob is stored.

\< Sample Program : binary.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
APRE_BINARY2 ins_blob[10+1];
APRE_BINARY2 sel_blob[10+1];
int ins_blob_ind;
int sel_blob_ind;
EXEC SQL END DECLARE SECTION;

memset(ins_blob, 0x21, 10);
ins_blob_ind = 10; /* set length of ins_blob value to indicator variable */

EXEC SQL INSERT INTO T_BLOB
VALUES (:ins_blob :ins_blob_ind);

EXEC SQL SELECT *
INTO :sel_blob :sel_blob_ind 
FROM T_BLOB;
```

##### APRE_BYTES

The APRE_BYTES type can be used only with BYTE type database columns. In all other respects, it is identical to the APRE_BLOB type.

##### Example

The following example illustrates the use of the APRE_BYTES type.

In this example, ins_bytes is an input host variable, and ins_bytes_ind is the corresponding input indicator variable. The value of ins_bytes_ind is set to the length of the value stored in ins_bytes. 

Meanwhile, sel_bytes is an output host variable, and sel_bytes_ind is its output indicator variable. After the execution of the SELECT statement, a sel_bytes_ind value of -1 means that sel_bytes is NULL, whereas a sel_bytes_ind value greater than 0 indicates the length of the value stored in sel_bytes.

\< Sample Program : binary.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
APRE_BYTES ins_bytes[5+1]; 
APRE_BYTES sel_bytes[5+1];
int ins_bytes_ind;   
int sel_bytes_ind;  
EXEC SQL END DECLARE SECTION;

memset(ins_bytes, 0x21, 5);
ins_bytes_ind = 5; /* set length of ins_bytes value to indicator variable */

EXEC SQL INSERT INTO T_BYTES 
VALUES (:ins_bytes :ins_bytes_ind);

EXEC SQL SELECT * 
INTO :sel_bytes :sel_bytes_ind 
FROM T_BYTES;
```

##### APRE_NIBBLE

The APRE_NIBBLE type can be used only with NIBBLE type database columns. 

When using the APRE_NIBBLE type as an input host variable, use an indicator variable to indicate that the value of the host variable is NULL, but use the first byte of the host variable to indicate the length of the host variable when the value of the host value is any other value (i.e. a non-NULL value). Note that the indicator variable will take precedence over the first byte of the host variable. That is, the value of the indicator variable is first checked, and if it is found to be -1, the host variable is handled as having a NULL value. If the value of the indicator variable is anything other than -1, the first byte of the host variable is taken as the length of the input data. Therefore, to input NULL data, the indicator variable must be set to -1, whereas to input other (non-NULL) values, the length of the input data must be specified in the first byte of the host variable.

Because the length of the input data is stored in the first byte, the actual data will be stored starting in the second byte of the host variable. Therefore, the length of the input data, that is, the nibble count, will be counted from the second byte of the host variable. One nibble is 4 bits.

When using the APRE_NIBBLE type as an output host variable, a value of -1 in the corresponding indicator variable indicates that a NULL value was returned to the host variable. An indicator variable value greater than 0 indicates the total length, in bytes, of the data saved in the host variable. 

Meanwhile, as mentioned above, the length of the actual output data, in nibbles, (one nibble = 4 bits) is stored in the first byte of the host variable, and the actual data are stored starting in the second byte.

Therefore, when non-NULL data are returned, the data length is indicated by both the indicator variable and the first byte of the host variable. The relationship between the two data length values is as follows:

(indicator variable) = ((first byte of host variable + 1)/2 + 1)

##### Example

The following example illustrates the use of the APRE_NIBBLE type. 

In this example, ins_nibble is an input host variable. Because the value to be input is not NULL, the length of the actual data stored in ins_nibble is set in the first byte of ins_nibble. 

Meanwhile, sel_nibble is an output host variable, and sel_nibble_ind is its output indicator variable. After the execution of the SELECT statement, a sel_nibble_ind value of -1 means that sel_nibble is NULL, whereas a sel_nibble_ind value greater than 0 indicates the total length, in bytes, of the value stored in sel_nibble. Additionally, the first byte in sel_nibble (i.e. sel_nibble[0]) contains the total length, in nibbles, of the actual data, which are stored starting from the second byte of sel_nibble (i.e. sel_nibble[1]).

\< Sample Program : binary.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
APRE_NIBBLE ins_nibble[5+2]; 
APRE_NIBBLE sel_nibble[5+2];
int sel_nibble_ind;  
EXEC SQL END DECLARE SECTION;

memset(ins_nibble+1, 0x21, 5);
ins_nibble[0] = 10; /* set length of ins_nibble value to ins_nibble[0] */

EXEC SQL INSERT INTO T_NIBBLE 
VALUES (:ins_nibble);

EXEC SQL SELECT * 
INTO :sel_nibble :sel_nibble_ind 
FROM T_NIBBLE;
```

##### APRE_VARBYTES 

This is availble to use when a column type is VARBYTE; otherwise, other features are identicl to that of the APRE_BLOB.

#### Sample Program

##### varchar.sc 

This sample program can be found at $ALTIBASE_HOME/sample/APRE/varchar.sc.

##### Result of Execution

```
$ is –f schema/schema.sql
$ make varchar
$ ./varchar
<VARCHAR TYPE>
-----------------------------------------------------------
[Scalar VARCHAR]                                                  
-----------------------------------------------------------
s_cname       = [DKHAN               ]
s_address.arr = [YeongdeungpoGu Seoul]
s_address.len = [20]

-----------------------------------------------------------
[Array of VARCHAR]                                                
-----------------------------------------------------------
CUS_JOB                                                           
-----------------------------------------------------------
ENGINEER
DOCTOR
DESIGNER
ENGINEER
WEBMASTER
WEBPD
PLANER
PD
DESIGNER
NULL
MANAGER
BANKER
ENGINEER
BANKER
MANAGER
PLANER
NULL
ENGINEER
NULL
WEBMASTER

-----------------------------------------------------------
[Structure Included VARCHAR]                                      
-----------------------------------------------------------
Success insert

-----------------------------------------------------------
[Array of Structure Included VARCHAR]                             
-----------------------------------------------------------
3 rows inserted
3 times insert success
```

##### date.sc 

This sample program can be found at $ALTIBASE_HOME/sample/APRE/date.sc.

##### Result of Execution

```
$ is –f schema/schema.sql
$ make date
$ ./date
<DATE TYPE>
------------------------------------------------------
[SQL_DATE_STRUCT]                                                 
------------------------------------------------------
JOIN_DATE of ENO is 3 : 2000/1/11

------------------------------------------------------
[SQL_TIME_STRUCT]                                                 
------------------------------------------------------
JOIN_DATE of ENO is 3 : 0:0:0

------------------------------------------------------
[SQL_TIMESTAMP_STRUCT]                                            
------------------------------------------------------
JOIN_DATE of ENO is 3 : 2000/1/11 0:0:0:0

------------------------------------------------------
[SQL_DATE_STRUCT]                                                 
------------------------------------------------------
Success update with SQL_DATE_STRUCT
1 rows updated

------------------------------------------------------
[SQL_TIME_STRUCT]                                                 
------------------------------------------------------
Success update with SQL_TIME_STRUCT
1 rows updated

------------------------------------------------------
[SQL_TIMESTAMP_STRUCT]                                            
------------------------------------------------------
Success update with SQL_TIMESTAMP_STRUCT
1 rows updated

------------------------------------------------------
[Array of Structure Included Date Type]                           
------------------------------------------------------
Success insert
3 rows inserted
3 times insert success
```

##### binary.sc 

This sample program can be found at $ALTIBASE_HOME/sample/APRE/binary.sc.

##### Result of Execution

```
$ is –f schema/schema.sql
$ make binary
$ ./binary
<BINARY TYPE>
------------------------------------------------------
[APRE_CLOB]                                                     
------------------------------------------------------
Success insert with APRE_CLOB
sel_clob     = AAAAAAAAAA
sel_clob_ind = 10

------------------------------------------------------
 [APRE_BLOB]                                                     
------------------------------------------------------
Success insert with APRE_BLOB
sel_blob     = !!!!!!!!!!
sel_blob_ind = 10
------------------------------------------------------
[APRE_BINARY]                                                      
------------------------------------------------------
Success insert with APRE_BINARY
sel_blob     = !!!!!!!!!!
sel_blob_ind = 10

------------------------------------------------------
[APREBYTES]                                                       
------------------------------------------------------
Success insert with APRE_BYTES
sel_bytes     = !!!!!
sel_bytes_ind = 5

------------------------------------------------------
[APRE_NIBBLE]                                                      
------------------------------------------------------
Success insert with APRE_NIBBLE
sel_nibble     = !!!!!
sel_nibble_ind = 6
sel_nibble[0]  = 10
```

### Column and Host Variable Type Conversion

Various host variable types can be used with each database column type. The following tables set forth the type conversions that are possible between host variable types and column types.

#### Input Host Variables

The following table lists the available input host variable types by column type. In addition, Host Variable Type with Minimum Conversion Cost' is the recommended type and you can expect performance improvement when using this type.
<table>
	<tr>
		<th colspan="2">Column Type</th>
		<th>Host variable types that can be
converted into the column type
</th>
		<th>Host variable types that incur
the minimum conversion
expense
</th>
	</tr>
	<tr>
		<td rowspan="2">Character type</td>
		<td>CHAR</td>
		<td>char, varchar, 
short, int, long, long long,
double, float,
SQL_DATE_STRUCT,
SQL_TIME_STRUCT,
SQL_TIMESTAMP_STRUCT,
</td>
		<td>char, varchar</td>
	</tr>
	<tr>
		<td>VARCHAR</td>
		<td>char, varchar, 
short, int, long, long long,
double, float,
SQL_DATE_STRUCT,
SQL_TIME_STRUCT,
SQL_TIMESTAMP_STRUCT,
</td>
		<td>char, varchar</td>
	</tr>
	<tr>
		<td rowspan="3">Integer type</td>
		<td>SMALLINT</td>
		<td>char, varchar, 
short, int, long, long long,
double, float
</td>
		<td>short</td>
	</tr>
	<tr>
		<td>INTEGER</td>
		<td>char, varchar, 
short, int, long, long long,
double, float
</td>
		<td>int</td>
	</tr>
	<tr>
		<td>BIGINT</td>
		<td>char, varchar, 
short, int, long, long long,
double, float
</td>
		<td>long, long long</td>		
	</tr>
	<tr>
		<td rowspan="4">Real number
type</td>
		<td>NUMERIC
NUMBER
DECIMAL
</td>
		<td>char, varchar, 
short, int, long, long long,
double, float, SQL_NUMERIC_STRUCT
</td>
		<td>char,
long, long long,
float, double
</td>
	</tr>
    <tr>
    	<td>FLOAT</td>
    	<td>char, varchar, 
short, int, long, long long,
double, float
</td>
    	<td>float</td>
    </tr>
    <tr>
    	<td>REAL</td>
    	<td>char, varchar, 
short, int, long, long long,
double, float
</td>
    	<td>double</td>
    </tr>
    <tr>
    	<td>DOUBLE</td>
    	<td>char, varchar, 
short, int, long, long long,
double, float
</td>
    	<td>double</td>
    </tr>
    <tr>
    	<td>Date Type</td>
    	<td>DATE</td>
    	<td>char, 
SQL_DATE_STRUCT,
SQL_TIME_STRUCT,
SQL_TIMESTAMP_STRUCT
</td>
    	<td>char, 
SQL_DATE_STRUCT,
SQL_TIME_STRUCT, 
SQL_TIMESTAMP_STRUCT
</td>
    </tr>
    <tr>
    	<td rowspan="6">Binary Type</td>
    	<td>CLOB</td>
    	<td>APRE_CLOB</td>
    	<td>APRE_CLOB</td>
    </tr>
    <tr>
    	<td>BLOB</td>
    	<td>APRE_BLOB,
APRE_BINARY,
APRE_BINARY2</td>
    	<td>APRE_BLOB,
APRE_BINARY,
APRE_BINARY2</td>
    </tr>
    <tr>
    	<td>BYTE</td>
    	<td>APRE_BYTES, APRE_VARBYTES</td>
    	<td>APRE_BYTES, APRE_VARBYTES</td>
    </tr>
    <tr>
    	<td>NIBBLE</td>
    	<td>APRE_NIBFBLE</td>
    	<td>APRE_NIBBLE</td>
    </tr>
    <tr>
    	<td>VARBYTE</td>
    	<td>APRE_BYTES, APRE_VARBYTES</td>
    	<td>APRE_BYTES, APRE_VARBYTES</td>
    </tr>
</table>


#### Output Host Variables

This table sets forth the output host variable types into which each database column type can be converted.  In addition, 'Host variable type with minimum conversion cost' is the recommended type and can expect performance improvement when using this type.
<table>
	<tr>
		<th colspan="2">Column Type</th>
		<th>Host variable types into which the
column type can be converted
</th>
		<th>Host variable types that incur
the minimum conversion
expense
</th>
	</tr>
	<tr>
		<td rowspan="2">Character
Type</td>
		<td>CHAR</td>
		<td>char, varchar, 
APRE_BINARY, APRE_BINARY2
</td>
		<td>char, varchar</td>
	</tr>
	<tr>
		<td>VARCHAR</td>
		<td>char, varchar, 
APRE_BINARY, APRE_BINARY2
</td>
		<td>char, varchar</td>
	</tr>
	<tr>
		<td rowspan="3">Integer Type</td>
		<td>SMALLINT</td>
		<td>char, varchar, 
short, int, long, long long,
double, float,
APRE_BINARY, APRE_BINARY2
</td>
		<td>short</td>
	</tr>
	<tr>
		<td>INTEGER</td>
		<td>char, varchar, 
short, int, long, long long,
double, float,
APRE_BINARY, APRE_BINARY2
</td>
		<td>int</td>
	</tr>
	<tr>
		<td>BIGINT</td>
		<td>char, varchar, 
short, int, long, long long,
double, float,
APRE_BINARY, APRE_BINARY2
</td>
		<td>long, long long</td>		
	</tr>
	<tr>
		<td rowspan="4">Real Number
Type</td>
		<td>NUMERIC
NUMBER
DECIMAL
</td>
		<td>char, varchar, 
short, int, long, long long,
double, float,
APRE_BINARY, APRE_BINARY2, SQL_NUMERIC_STRUCT
</td>
		<td>char,
long, long long,
float, double
</td>
	</tr>
    <tr>
    	<td>FLOAT</td>
    	<td>char, varchar, 
short, int, long, long long,
double, float,
APRE_BINARY, APRE_BINARY2
</td>
    	<td>float</td>
    </tr>
    <tr>
    	<td>REAL</td>
    	<td>char, varchar, 
short, int, long, long long,
double, float,
APRE_BINARY, APRE_BINARY2
</td>
    	<td>double</td>
    </tr>
    <tr>
    	<td>DOUBLE</td>
    	<td>char, varchar, 
short, int, long, long long,
double, float,
APRE_BINARY, APRE_BINARY2
</td>
    	<td>double</td>
    </tr>
    <tr>
    	<td>Data Type</td>
    	<td>DATE</td>
    	<td>char, 
SQL_DATE_STRUCT,
SQL_TIME_STRUCT,
SQL_TIMESTAMP_STRUCT,
APRE_BINARY, APRE_BINARY2
</td>
    	<td>char, 
SQL_DATE_STRUCT,
SQL_TIME_STRUCT, 
SQL_TIMESTAMP_STRUCT
</td>
    </tr>
    <tr>
    	<td rowspan="6">Binary Type</td>
    	<td>CLOB</td>
    	<td>APRE_CLOB</td>
    	<td>APRE_CLOB</td>
    </tr>
    <tr>
    	<td>BLOB</td>
    	<td>APRE_BLOB,
APRE_BINARY,
APRE_BINARY2</td>
    	<td>APRE_BLOB,
APRE_BINARY,
APRE_BINARY2</td>
    </tr>
     <tr>
    	<td>BYTE</td>
    	<td>APRE_BYTES, APRE_VARBYTES,
APRE_BINARY, APRE_BINARY2
</td>
    	<td>APRE_BYTES, APRE_VARBYTES</td>
    </tr>
     <tr>
    	<td>NIBBLE</td>
    	<td>APRE_NIBBLE,
APRE_BINARY, APRE_BINARY2
</td>
    	<td>APRE_NIBBLE</td>
    </tr>
     <tr>
    	<td>VARBYTE</td>
    	<td>APRE_BYTES, APRE_VARBYTES, APRE_BINARY, APRE_BINARY2</td>
    	<td>APRE_BYTES, APRE_VARBYTES</td>
    </tr>
</table>

The APRE_BINARY type can be used as an output host variable for all column types. The APRE_BINARY type does not involve any type conversion, because assigning a value to this type merely invokes the memcpy() function to store the contents that were retrieved from the database in the host variable without change. It is thus necessary to understand how each column type stores data in memory and to be able to interpret the contents of memory in order to use the APRE_BINARY type as a host variable. 

Therefore, although the lack of type conversion means that performance will likely improve when the APRE_BINARY type is used as a host variable, the requirement to understand how data are stored in memory complicates development tasks. Therefore, in most cases it is recommended that the APRE_BINARY type be used only with BLOB type columns.



## 6. Embedded SQL Statements

----------

### Overview

The term “embedded SQL statement” refers to a SQL statement that resides within an application.

#### Syntax

```
EXEC SQL … ;
```

An embedded SQL statement begins with the words “EXEC SQL” and ends with a semicolon (“;”). 

Between the EXEC SQL keyword and the semicolon, various kinds of SQL statements can be used, including DML statements, such as SELECT and UPDATE statements, and DDL statements, such as CREATE and DROP statements.

##### Limitation

The maximum possible length of a SQL statement is 32KB (kilobytes).

##### Example

The following is an example of embedded SQL statement.

< SELECT statement : select.sc >

```
EXEC SQL BEGIN DECLARE SECTION;
short      s_dno;
char       s_dname[30+1];
char       s_dep_location[9+1];
EXEC SQL END DECLARE SECTION;

EXEC SQL SELECT DNAME, DEP_LOCATION 
INTO :s_dname, :s_dep_location
           FROM DEPARTMENTS 
WHERE DNO = :s_dno;
```

< INSERT statement : insert.sc >

```
EXEC SQL BEGIN DECLARE SECTION;
char    s_gno[10+1];
char    s_gname[20+1];
char    s_goods_location[9+1];
int     s_stock;
double  s_price;
EXEC SQL END DECLARE SECTION;

EXEC SQL INSERT INTO GOODS 
VALUES (:s_gno, :s_gname, 
:s_goods_location, 
:s_stock, :s_price);
```

More detailed information about the syntax of each embedded SQL statement will be provided later in this chapter.

#### Static Versus Dynamic SQL Statements

Embedded SQL statements can be broadly classified as either static SQL statements or dynamic SQL statements, depending on whether the contents of the SQL statement are determined when the application is written, or at runtime. This chapter describes only static SQL statements. For more information about dynamic SQL statements, please refer to the Chapter 10.

Embedded SQL statements can also classified into the following categories based on how they handle data and the role that they play.

##### Host Variable Declaration Section

These statements are used to delimit a block of code for declaring host variables for use in other embedded SQL statements. For more detailed information, please refer to Chapter 3: Host Variable Declaration Section.

##### Function Argument Declaration Section

These statements are used to delimit a block of code for declaring function arguments for use in other embedded SQL statements. For more detailed information, please refer to Chapter 3: Host Variable Declaration Section.

##### Connection-Related SQL Statements

These statements are used to connect to and disconnect from a database.

##### Basic Embedded SQL Statements

These statements include DML statements, such as SELECT, UPDATE, INSERT, and DELETE statements, as well as DDL statements, such as CREATE, DROP, and ALTER statements.

##### Cursor Control SQL Statements

These statements are used together with cursors to process data, and include statements for defining cursors, opening cursors, using cursors to retrieve data, and closing cursors. For more detailed information, please refer to Chapter 8: Using Cursors. 

##### SQL Statements for Controlling Stored Procedures and Functions

These statements are used for handling stored procedures and stored functions, and include statements for creating, recompiling, executing, and deleting stored procedures and functions. For more detailed information, please refer to Chapter 11: Using Stored Procedures in C/C++

##### Other Embedded SQL Statements

This category includes all SQL statements supported in Altibase that do not fall into one of the above categories. These statements include task control statements and DCL statements for controlling the system and individual transactions.

##### OPTION Statements

These statements are used to set various options provided by the APRE C/C++precompiler.

### Connection related SQL statements

Connection-related SQL statements are those that are used to manage a connection with a database server, including the CONNECT and DISCONNECT statements.

#### CONNECT

This statement is used to connect to the database server.

##### Syntax

```
EXEC SQL CONNECT <:user> IDENTIFIED BY <:passwd>
[ USING <:conn_opt1> [ , <:conn_opt2> ] ];
```

##### Arguments

-   \<:*user*\>: This is the name of the user with which to connect to the database server.

-   \<:*passwd*\>: This is the password corresponding to the user with which a connection is established to the database server.

-   \<:*conn_opt1*\>: This is used to specify various options related to the database server connection.

    -   DSN: This is the IP address of the database server with which to establish a connection.

    -   CONNTYPE: This is used to specify the protocol with which to communicate with the database server.

        -   1: TCP/IP

        -   2: UNIX DOMAIN

        -   3: IPC

    -   PORT_NO: This is used to specify the port number via which to communicate with the database server.

    -   NLS_USE: This is used to set the character set to use during the session.

        -   KO16KSC5601: Korean

        -   US7ASCII: English

        -   MS949

        -   BIG5

        -   GB231280

        -   MS936

        -   UTF8

        -   SHIFTJIS

        -   MS932

        -   EUCJP

    -   BATCH: This is used to specify the batch processing mode for the session.

        -   ON: Batch Processing Mode

        -   OFF: Non Batch Processing Mode

-   \<:*conn_opt2*\>: This is used to specify the same database server connection options that are specified using *conn_opt1*. If an attempt to connect with a database server using the options specified in *conn_opt1* fails, another connection attempt will automatically be made using the options specified in *conn_opt2.*

##### Description

One application is permitted to establish one or more connections to a database using embedded SQL statements. When multiple connections to a database are established within a single application, there can be only one connection that does not have a connection name. This chapter only describes the connection that does not have a connection name.

For more information about establishing multiple connections within a single application, please refer to Chapter 12: Applications with Multiple Database Connections. For more information about multi-threaded applications, please refer to Chapter 13: Multithreaded Applications.

> \* Note: If PORT_NO and NLS_USE are not specified in the connection string, then the environment variables shown below must exist, and must have the same values that are set in the corresponding properties in the altibase.properties file

```
export ALTIBASE_PORT_NO=20300
export ALTIBASE_NLS_USE=US7ASCII 
```

##### Specifying Two Sets of Connection Options

**SQL_SUCCESS**: This is returned when a connection is successfully established using the first set of options.

**SQL_SUCCESS_WITH_INFO**: This is returned when the connection attempt using the first set of options fails, but a connection is then successfully established using the second set of options. The error message related to the failure of the first connection attempt is stored in sqlca.sqlerrm.sqlerrmc.

**SQL_ERROR**: This is returned when both connection attempts fail. The error messages related to the failure of both connection attempts are consecutively stored in sqlca.sqlerrm.sqlerrmc. 

> ##### Considerations
>
> If an attempt to establish a connection is made when a connection already exists, an error message indicating that a connection has already been established will be displayed. Therefore, if it is desired to establish a connection while a connection exists, it is first necessary to execute FREE or DISCONNECT to terminate the existing connection. If the database server is running, the DISCONNECT statement must be executed, whereas if the database server is not running, the FREE statement must be executed.
> 
> If the connection method (CONNTYPE) is set to 2 or 3 in the connection string, the DSN and PORT_NO options will be ignored even if they are set, and an attempt will be made to connect with the local database server.

##### Example

Various database server connection examples are shown below.

[Example 1] This example shows how to connect to the database server by specifying only the user name and the user password. In this case, the other information that is necessary in order to establish a connection with the database server will be read from the environment variables.

\< Sample Program: connect1.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
char usr[10];
char pwd[10];
EXEC SQL END DECLARE SECTION;

strcpy(usr, "SYS");
strcpy(pwd, "MANAGER"); 

EXEC SQL CONNECT :usr IDENTIFIED BY :pwd; 
```

[Example 2] This example shows how to connect to the database server by specifying the connection method in the USING clause. In this case, the connection to the database server will be established using the user name and the user password stored in the usr and pwd host variables and the connection information stored in the conn_opt3 host variable. Any information that is necessary in order to establish a connection with the database server but could not be found in the conn_opt3 host variable will be read from the environment variables.

\< Sample Program : connect1.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
char usr[10];
char pwd[10];
char conn_opt3[100];
EXEC SQL END DECLARE SECTION;

strcpy(usr, "SYS");
strcpy(pwd, "MANAGER"); 
strcpy(conn_opt3, "DSN=192.168.11.12;CONNTYPE=1;PORT_NO=53000"); 

EXEC SQL CONNECT :usr IDENTIFIED BY :pwd USING :conn_opt3;  
```

[Example 3] This example shows how to connect to the database server by specifying two different sets of connection options in the USING clause. In this case, an attempt will be made to connect to the database server using the user name and the user password stored in the usr and pwd host variables and the connection information stored in the conn_opt1 host variable. If this attempt fails, another attempt will be made to connect to the database server using the same user name and user password, but this time with the connection information stored in the conn_opt2 host variable.

\< Sample Program: connect2.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
char usr[10];
char pwd[10];
char conn_opt1[100];
char conn_opt2[100];
EXEC SQL END DECLARE SECTION;

strcpy(usr, "SYS");
strcpy(pwd, "MANAGER"); 
strcpy(conn_opt1, "DSN=192.168.11.12;CONNTYPE=1;PORT_NO=53000"); 
strcpy(conn_opt2, "DSN=192.168.11.22;CONNTYPE=1;PORT_NO=53000");

EXEC SQL CONNECT :usr IDENTIFIED BY :pwd USING :conn_opt1, :conn_opt2;  
if (sqlca.sqlcode == SQL_SUCCESS) /* check sqlca.sqlcode */
{
    printf("Success connection to altibase server with first option\n\n");
}
else if (sqlca.sqlcode == SQL_SUCCESS_WITH_INFO)
{
    /* fail connection with first option and then success connection with second option */
    printf("Success connection to altibase server with second option\n");
    printf("First connection error : [%d] %s\n\n", SQLCODE, sqlca.sqlerrm.sqlerrmc);
}
else
{
    printf("Fail connection to altibase server both first option and second option\n");
    printf("Error : [%d]\n", SQLCODE);
    printf("%s\n\n", sqlca.sqlerrm.sqlerrmc);
    exit(1);
}
```

#### DISCONNECT

This statement is used to disconnect from the database server.

##### Syntax

```
EXEC SQL DISCONNECT;
```

##### Argument

None

##### Description

This statement disconnects from the database server and releases all resources that were allocated to the connection.

##### Example

The following example shows the use of the DISCONNECT statement.

\< Sample Program : connect1.sc \>

```
EXEC SQL DISCONNECT;
```

#### Sample Programs

##### connect1.sc 

This sample program can be found at $ALTIBASE_HOME/sample/APRE/connect1.sc.

##### Result of Execution

```
$ is –f schema/schema.sql
$ make connect1
$ connect1
<CONNECT 1>
------------------------------------------------------
[Connect]
------------------------------------------------------
Success connection to altibase server

------------------------------------------------------
[Disconnect]
------------------------------------------------------
Success disconnection from altibase server
```

##### connect2.sc 

This sample program can be found at $ALTIBASE_HOME/sample/APRE/connect2.sc.

##### Result of Execution

```
$ is –f schema/schema.sql
$ make connect2
$ connect2
<CONNECT 2>
------------------------------------------------------
[Connect With Two ConnOpt]
------------------------------------------------------
Fail connection to altibase server both first option and second option
Error : [-327730]
Failed first connection : Client unable to establish connection
Failed second connection : Client unable to establish connection
```

### Using DDL and DML in Embedded SQL Statements

The notional category “basic embedded SQL statements” essentially refers to those embedded SQL statements in which DML statements, such as SELECT, UPDATE, INSERT, and DELETE, and DDL statements, such as CREATE, DROP, and ALTER, are executed.

#### SELECT

This statement is used to search one or more database tables for records that meet the specified conditions and store the returned data in host variables. The basic syntax is the same as the general SELECT statement supported in Altibase SQL, however, in order to be able to use host variables, an additional INTO clause is needed.

##### Syntax

```
EXEC SQL SELECT [ ALL | DISTINCT ] <target_list>
INTO <host_var_list> 
FROM <table_expression> [ WHERE … ]; 
```

##### Argument

-   \<target_list\> : Please refer to the SQL Reference.

-   \<*host_var_list*\> : This is a list of output host variables and output indicator variables.

-   \<table_expression\> :  Please refer to the SQL Reference.

##### Description

Unless the host variable is an array, only one record must be returned. If more than one record is returned, the value returned in the sqlca.sqlcode variable will be SQL_ERROR, and the value returned in the sqlca.sqlerrm.sqlerrmc variable will be an error message indicating that too many rows were returned. When it is expected that more than one record is to be returned, it is necessary to use an array or a cursor.

If the host variable is an array, the number of returned records must be the same as or less than the size of the array. If the number of returned records is greater than the array size, the value returned in the sqlca.sqlcode variable will be SQL_ERROR and the value returned in the sqlca.sqlerrm.sqlerrmc variable will be an error message indicating that too many rows were returned. In such cases, it is necessary either to increase the size of the array, or use a cursor.

##### Result

<table>
	<tr>
		<th colspan="2">When the host variable is not an array</th>
		<th colspan="2">When the host variable is an array</th>	
	</tr>
	<tr>
		<td>Number of
returned records</td>
		<td>Result of Execution</td>
		<td>Number of returned
records</td>
		<td>Result of Execution</td>
	</tr>
	<tr>
		<td>0</td>
		<td>SQL_NO_DATA</td>
		<td>0</td>
		<td>SQL_NO_DATA</td>
	</tr>
	<tr>
		<td rowspan="2">1</td>
		<td rowspan="2">SQL_SUCCESS</td>
		<td>Fewer than the size of
the array</td>
		<td>SQL_SUCCESS</td>
	</tr>
	<tr>
		<td>The same number as the
size of the array</td>
		<td>SQL_SUCCESS</td>
	</tr>
	<tr>
		<td>More than 1 </td>
		<td>SQL_ERROR</td>
		<td>More than the size of the
array</td>
		<td>SQL_ERROR</td>
	</tr>
</table>


An sqlca.sqlcode value of SQL_NO_DATA means that zero (0) records were returned. In this case, the contents of the host variable will not have any meaning (i.e. will be a garbage value).

##### Limitations

-   An input host variable cannot be an array.

```
Example) EXEC SQL BEGIN DECLARE SECTION;
int var1;
int var2[10];
int var3[10];
EXEC SQL END DECLARE SECTION;

EXEC SQL SELECT * INTO :var1 
FROM T1 WHERE i1 = :var3;	(X)
          or
EXEC SQL SELECT * INTO :var2 
FROM T1 WHERE i1 = :var3;	(X)
```

-   If the CAST operator is used in the GROUP BY clause to specify the host variable type, this expression cannot be used in the TARGET clause.

```
Example) 
prepare select trunc(QTY - cast(:jstm as integer)) / cast(:unit as integer) from orders;		(O)

prepare SELECT trunc(QTY - cast(:jstm as integer)) from orders GROUP BY trunc(QTY - cast(:jstm as integer));	(X)
```

-   If the output host variable in the INTO clause is an array of structures, only one output host variable can be used. For more information, please refer to Chapter 5: Host Variable Data Types.
  
-   When the output host variable in an INTO clause is a varchar array, it cannot be used with any other output host variables. For more information, please refer to Chapter 5: Host Variable Data Types.
  
-   An input indicator variable cannot be used in the LIMIT clause of a SELECT statement; only an input host variable can be used for this purpose. Additionally, the only input host variable data type that is supported for use with the LIMIT clause is int.

##### Example

Various SELECT statement examples are shown below.

[Example 1] ] In the following example, the departments table is searched for records whose DNO column value matches the value of the s_dno host variable, and the values in the DNAME and DEP_LOCATION columns are loaded into the s_dname and s_dep_location host variables, respectively.

\< Sample Program : select.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
short s_dno;
char  s_dname[30+1];
char  s_dep_location[9+1];
EXEC SQL END DECLARE SECTION;

s_dno = 1001;
EXEC SQL SELECT DNAME, DEP_LOCATION 
INTO :s_dname, :s_dep_location
FROM DEPARTMENTS 
WHERE DNO = :s_dno;
```

[Example 2] The following example shows the use of a structure type host variable. In this example, the departments table is searched for records whose DNO column value matches the value of the s_dno input host variable, and the column values are stored in the corresponding elements of the s_department structure.

\< Sample Program : hostvar.h \>

```
EXEC SQL BEGIN DECLARE SECTION;
typedef struct department
{
    short dno; 
    char  dname[30+1];
    char  dep_location[9+1];
    int   mgr_no;
} department;
EXEC SQL END DECLARE SECTION;
```

< Sample Program : select.sc >

```
/* specify path of header file */
EXEC SQL OPTION (INCLUDE=./include);
/* include header file for precompile */
EXEC SQL INCLUDE hostvar.h;

EXEC SQL BEGIN DECLARE SECTION;
short s_dno;
department s_department;
EXEC SQL END DECLARE SECTION;

s_dno = 1002;
EXEC SQL SELECT * 
INTO :s_department
FROM DEPARTMENTS 
WHERE DNO = :s_dno;
```

[Example 3] The following is an example of retrieving the T_LOB table and storing the INTEGER column in the sI1 host variable and the CLOB column in the file sI2FName created with the APRE_FILE_CREATE option.

\< Sample Program : clobSample.sc\>

```
EXEC SQL BEGIN DECLARE SECTION;
int          sI1;
char         sI2FName[33];
unsigned int sI2FOpt;
SQLLEN       sI2Ind;
EXEC SQL END DECLARE SECTION;

strcpy(sI2FName, aOutFileName);
sI2FOpt = APRE_FILE_CREATE;
 
EXEC SQL SELECT * INTO :sI1, CLOB_FILE :sI2FName OPTION :sI2FOpt INDICATOR :sI2Ind FROM T_LOB;
```

> \* Refer to Appendix A for an example of retrieving data of BLOB and CLOB type columns and saving them to a file.

#### INSERT

This statement is used to insert new records into a table.

##### Syntax

```
Please refer to the SQL Reference.
```

##### Argument

None

##### Description

Host variables and indicator variables can both be used in the VALUES clause.

##### Example

Various INSERT statement examples are shown below. 

[Example 1] In the following example, new records are inserted into the GOODS table.

\< Sample Program: insert.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
char    s_gno[10+1];
char    s_gname[20+1];
char    s_goods_location[9+1];
int     s_stock;
double  s_price;
EXEC SQL END DECLARE SECTION;

strcpy(s_gno, "F111100002");
strcpy(s_gname, "XX-101");
strcpy(s_goods_location, "FD0003");
s_stock = 5000;
s_price = 9980.21;

EXEC SQL INSERT INTO GOODS 
VALUES (:s_gno, :s_gname, :s_goods_location, 
:s_stock, :s_price);
```

[Example 2] In the following example, a structure-type host variable is used to insert new records into the GOODS table.

\< Sample Program : hostvar.h \>

```
EXEC SQL BEGIN DECLARE SECTION;
typedef struct goods
{
    char   gno[10+1];
    char   gname[20+1];
    char   goods_location[9+1];
    int    stock;
    double price;
} goods;
EXEC SQL END DECLARE SECTION;
```

\< Sample Program : insert.sc \>

```
/* specify path of header file */
EXEC SQL OPTION (INCLUDE=./include);
/* include header file for precompile */
EXEC SQL INCLUDE hostvar.h;

EXEC SQL BEGIN DECLARE SECTION;
goods   s_goods;
EXEC SQL END DECLARE SECTION;

strcpy(s_goods.gno, "F111100003");
strcpy(s_goods.gname, "XX-102");
strcpy(s_goods.goods_location, "AD0003");
s_goods.stock = 6000;
s_goods.price = 10200.96;

EXEC SQL INSERT INTO GOODS VALUES (:s_goods);
```

> \* For an example of the use of an INSERT statement to insert data from a file into a BLOB or CLOB column, please refer to Appendix A.

#### UPDATE

This statement is used to find records that meet specified conditions and change the values in certain columns of those records.

##### Syntax

```
Please refer to the SQL Reference 
```

##### Arguments

None

##### Description

Both host variables and indicator variables can be used in both the SET and WHERE clauses.

##### Limitations

-   Arrays must not be used together with non-array type variables. For example, if the host variable used in the SET clause is an array, the host variable used in the WHERE clause must also be an array.

```
예) EXEC SQL BEGIN DECLARE SECTION;
int var1[10]; 
int var2[10];
int var3;
EXEC SQL END DECLARE SECTION;

EXEC SQL UPDATE T1 
SET I1 = :var1, I2 = :var2 
WHERE I1 = :var3;       	    (X)
```

##### Example

Various UPDATE statement examples are shown below.

[Example 1] In this example, records for which the value in the ENO column matches the value of the s_eno host variable are found, and the values in the DNO and EMP_JOB columns for those records are updated with the values of the s_dno and s_emp_job.arr host variables, respectively.

\< Sample Program : update.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
int      s_eno;
short    s_dno;
varchar  s_emp_job[15+1];
EXEC SQL END DECLARE SECTION;

s_eno = 2;
s_dno = 1001;
strcpy(s_emp_job.arr, "ENGINEER");
s_emp_job.len = strlen(s_emp_job.arr);

EXEC SQL UPDATE EMPLOYEES 
SET DNO      = :s_dno,
     EMP_JOB = :s_emp_job
WHERE ENO = :s_eno;
```

[Example 2] This example illustrates the use of a structure-type host variable in an UPDATE statement. Records for which the value in the ENO column matches the value of the s_eno host variable are found, and the values in the DNO, EMP_JOB, and JOIN_DATE columns for those records are updated with the values of s_employee.s_dno, s_employee.s_emp_job.arr, and SYSDATE, respectively.

\< Sample Program : hostvar.h \>

```
EXEC SQL BEGIN DECLARE SECTION;
typedef struct employee
{
      int        eno;
      char      ename[20+1];
      varchar   emp_job[15+1];
      char      emp_tel[15+1];
      short     dno;
      double    salary;
      char      sex;
      char      birth[4+1];
      char      join_date[19+1];
      char      status[1+1];
} employee;
EXEC SQL END DECLARE SECTION;
```

\< Sample Program : update.sc \>

```
/* specify path of header file */
EXEC SQL OPTION (INCLUDE=./include);
/* include header file for precompile */
EXEC SQL INCLUDE hostvar.h;

EXEC SQL BEGIN DECLARE SECTION;
employee s_employee;
EXEC SQL END DECLARE SECTION;

s_eno = 20;
s_employee.dno = 2001;
strcpy(s_employee.emp_job.arr, "TESTER");
s_employee.emp_job.len = strlen(s_employee.emp_job.arr);

EXEC SQL UPDATE EMPLOYEES 
SET DNO        = :s_employee.dno,
     EMP_JOB   = :s_employee.emp_job,
               JOIN_DATE = SYSDATE
           WHERE ENO = :s_eno;
```

#### DELETE

This statement is used to delete the records that satisfy the specified conditions from the corresponding table. 

##### Syntax

```
Please refer to the SQL Reference
```

##### Argument

None

##### Description

Both host variables and indicator variables can be used in the WHERE clause.

##### Example

The following example shows how to delete records that satisfy the specified conditions from the employees table.

\< Sample Program : delete.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
int      s_eno;
short    s_dno;
EXEC SQL END DECLARE SECTION;

s_eno = 5;
s_dno = 1000;

EXEC SQL DELETE FROM EMPLOYEES 
           WHERE ENO > :s_eno AND 
DNO > :s_dno AND 
EMP_JOB LIKE 'P%';
```

#### Sample Programs

##### select.sc

This sample program can be found at $ALTIBASE_HOME/sample/APRE/select.sc.

##### Result of Execution

```
$ is –f schema/schema.sql
$ make select
$ ./select
<SELECT>
------------------------------------------------------
[Scalar Host Variables]                                           
------------------------------------------------------
DNO      DNAME                          DEP_LOCATION              
------------------------------------------------------
1001     RESEARCH DEVELOPMENT DEPT 1    New York 

------------------------------------------------------
[Structure Host Variables]                                        
------------------------------------------------------------------
DNO      DNAME                          DEP_LOCATION       MGR_NO 
------------------------------------------------------------------
1002     RESEARCH DEVELOPMENT DEPT 2    Sydney             13

------------------------------------------------------
[Error Case : Scalar Host Variables]                              
------------------------------------------------------
Error : [-594092] Returns too many rows
```

##### insert.sc 

This sample program can be found at $ALTIBASE_HOME/sample/APRE/insert.sc.

##### Result of Execution

```
$ is –f schema/schema.sql
$ make insert
$ ./insert
<INSERT>
------------------------------------------------------
[Scalar Host Variables]                                           
------------------------------------------------------
1 rows inserted

------------------------------------------------------
[Structure Host Variables]                                        
------------------------------------------------------
1 rows inserted
```

##### update.sc 

This sample program can be found at $ALTIBASE_HOME/sample/APRE/update.sc.

##### Result of Execution

```
$ is –f schema/schema.sql
$ make update
$ ./update
<UPDATE>
------------------------------------------------------
[Scalar Host Variables]                                           
------------------------------------------------------
1 rows updated

------------------------------------------------------
[Structure Host Variables]                                        
------------------------------------------------------
1 rows updated
```

##### delete.sc 

This sample program can be found at $ALTIBASE_HOME/sample/APRE/delete.sc.

##### Result of Execution

```
$ is –f schema/schema.sql
$ make delete
$ ./delete
<DELETE>
------------------------------------------------------
[Scalar Host Variables]                                           
------------------------------------------------------
7 rows deleted
```

### Using Other Embedded SQL Statements

This category includes task control statements, DCL statements for controlling the system and individual transactions, and the INCLUDE OPTION and THREAD OPTION statements. 

#### AUTOCOMMIT

##### Syntax

```
EXEC SQL AUTOCOMMIT { ON | OFF };
```

##### Argument

None

##### Description

This statement is used to change the AUTOCOMMIT mode for the current session.

##### Example

The following examples illustrate how to change the AUTOCOMMIT mode. 

```
EXEC SQL AUTOCOMMIT ON; -- To change to AUTOCOMMIT mode
EXEC SQL AUTOCOMMIT OFF; -- To change to Non-AUTOCOMMIT mode
```

#### COMMIT

##### Syntax

```
EXEC SQL COMMIT;
```

##### Argument

None

##### Description

This statement is used to indicate that the current transaction was successful and terminate it. The changes effected by the transaction will be stored in the database permanently.

> Note that an error is never raised when this statement is executed, even when the autocommit mode of the current session is AUTOCOMMIT.
>

##### Example

The following example shows how to use the COMMIT statement in an embedded SQL statement:

```
EXEC SQL COMMIT;
```

#### SAVEPOINT 

##### Syntax

```
EXEC SQL SAVEPOINT <savepoint_name>;
```

##### Argument

<savepoint_name>: This is the name to be given to the savepoint.

##### Description

A savepoint is a defined point in time at which the changes made by a transaction that has not finished executing are temporarily stored. The SAVEPOINT embedded SQL statement is used to define an explicit savepoint, to which the transaction can be rolled back if necessary

> Note that an error is never raised when this statement is executed, even when the autocommit mode of the current session is AUTOCOMMIT.
>

##### Example

The following example shows how to use the SAVEPOINT statement in an embedded SQL statement:

```
EXEC SQL SAVEPOINT sp;
```

#### ROLLBACK

##### Syntax

```
EXEC SQL ROLLBACK [ TO SAVEPOINT <savepoint_name> ];
```

##### Arguments

\<savepoint_name\> :  This is the name of a savepoint to which to return.

##### Description

This statement is used to restore the database to the state that existed prior to the commencement of execution of the current transaction, or to the state that existed when a specified savepoint was defined. That is, this statement undoes all or some of the operations that have been performed by the current transaction.

If a previously defined savepoint is specified in this statement, the current transaction will be only partially rolled back. That is, the operations performed since the savepoint was defined will be undone.

> Note that an error is never raised when this statement is executed, even when the autocommit mode of the current session is AUTOCOMMIT.
>

##### Example

The following example shows how to use the ROLLBACK statement in an embedded SQL statement:

```
EXEC SQL ROLLBACK;
or
EXEC SQL ROLLBACK TO SAVEPOINT sp;
```

#### BATCH

This statement is used to change a connection property so as to activate or deactivate batch processing.

##### Syntax

```
EXEC SQL BATCH { ON | OFF };
```

##### Argument

None

##### Description

When batch processing mode is active, the execution (i.e. transmission to the server) of embedded SQL statements is delayed until the transaction is committed or a SELECT statement is subsequently executed. Batch processing is possible because the result of uncommitted INSERT, UPDATE, and DELETE statements can only be read from within the same transaction.

Batch processing can improve performance in environments in which INSERT, UPDATE, and DELETE statements are frequently executed.

##### Example

The following examples show how to use the BATCH statement in an embedded SQL statement to change the batch mode. 

```
EXEC SQL BATCH ON;	- To activate batch processing mode
EXEC SQL BATCH OFF; 	- To deactivate batch processing mode
```

#### FREE

This statement is used to release all resources that were allocated when the connection with the database server was established and embedded SQL statements were executed. 

##### Syntax

```
EXEC SQL FREE;
```

##### Arguments

None

##### Description

If the connection with the server is lost while embedded SQL statements are being executed, it is necessary to execute the FREE statement before attempting to re-establish the connection. 

The database server must not be running when the FREE statement is executed. If the database server is running, use the DISCONNECT statement instead of the FREE statement.

##### Example

The following example shows the use of the FREE statement:

\< Sample Program : free.sc \>

```
EXEC SQL FREE;
```

#### INCLUDE

This statement is used to specify a header file that is to be included in a precompile operation. 

##### Syntax

```
EXEC SQL INCLUDE <filename>;
```

##### Argument

-   \<*filename*\> : This is the name of the header file to be included in the precompile operation.

##### Description

The definitions of host variables and host variable data types are important information that APRE needs to know in order to perform the precompile operation. Therefore, header files that contain host variable type definitions or host variable declarations to be used in the application must be included using the INCLUDE statement if the -parse precompiler option will not be set to “full”. 

The EXEC SQL INCLUDE command can be used both in the main source file to be precompiled (i.e. the file with the .sc extension) and in any header files (.h) that are also included using the EXEC SQL INCLUDE command. Note however that this command cannot be used within header files that are included using the #include command.

##### Limitation

Recursive header file inclusions are not allowed. In other words, if myheader2.h is included in myheader1.h, then myheader1.h must not also be included in myheader2.h

Example) <myheader1.h>

```
EXEC SQL INCLUDE myheader2.h;
…

<myheader2.h>
EXEC SQL INCLUDE myheader1.h;	(X)
…
```

##### Example

The following example shows how to use the INSERT statement to specify the header file hostvar.h for inclusion in a precompile operation.

\< Sample Program : insert.sc \>

```
EXEC SQL INCLUDE hostvar.h;
```

#### Sample Programs

##### free.sc 

This sample program can be found at $ALTIBASE_HOME/sample/APRE/free.sc.

##### Result of Execution

```
$ is –f schema/schema.sql
$ make free
$ ./free
<FREE>
------------------------------------------------------
[Connect]
------------------------------------------------------
Success connection to altibase server

------------------------------------------------------
[Free]
------------------------------------------------------
Error : [-331796] Function sequence error

------------------------------------------------------
[Reconnect]
------------------------------------------------------
Error : [-589826] Already connected
```

### OPTION Statements

Result of Execution

#### INCLUDE

APRE provides various methods of using embedded SQL statements to specify the location of the header files to be included in a precompile operation. One of them is the INCLUDE OPTION statement.

##### Syntax

```
EXEC SQL OPTION (INCLUDE = <pathname>);
```

##### Argument

-   \<*pathname*\> : This is the location of the header files to be included in the precompile operation. 

##### Description

This command is used to specify one or more locations in which to look for the header files to be included in the precompile operation. The current directory does not need to be specified. When specifying multiple locations, they must be separated by commas (“,”). The INCLUDE OPTION statement must precede all INCLUDE statements. 

##### Example

In the following example, the INCLUDE OPTION statement is used to specify the location in which to look for hostvar.h (namely, the ./include directory), after which the hostvar.h file is included using the INCLUDE statement.

\< Sample Program : insert.sc \>

```
EXEC SQL OPTION (INCLUDE=./include);
EXEC SQL INCLUDE hostvar.h;
```

#### THREADS

APRE supports the use of embedded SQL statements in multi-threaded applications. The THREADS OPTION statement provides a basis on which the precompiler can determine whether or not the file to be precompiled is a multi-threaded program. 

##### Syntax

```
EXEC SQL OPTION (THREADS = { TRUE | FALSE });
```

##### Argument

None

##### Description

The THREADS OPTION statement can have either of the following two values:

-   TRUE : When the file to be precompiled is a multi-threaded program

-   FALSE : When the file to be precompiled is not a multi-threaded program

If the THREADS OPTION statement is not specified, APRE assumes that the file to be precompiled is not a multi-threaded program. Therefore, if the file to be precompiled is a multi-threaded program, then the THREADS OPTION must specified, and must be set to TRUE. If the -mt option is used on the command line when precompiling a multi-threaded program, the THREADS OPTION statement can be omitted.

##### Example

The following example shows how to set the THREADS OPTION to TRUE using the OPTION statement when the file to be precompiled is a multi-threaded program.

\< Sample Program : mt1.sc \>

```
EXEC SQL OPTION (THREADS=TRUE); 
```

## 7. Handling Runtime Errors 

--------------------

### Overview

Applications must be able to handle internal runtime errors. APRE provides the programmer with numerous methods for handling runtime errors, including variables such as SQLCODE and SQLSTATE and the WHENEVER statement.

#### Return Values 

After an embedded SQL statement is executed, the result of execution is stored in **sqlca.sqlcode**. This variable can have the following values:

-   **SQL_SUCCESS**  
    This value indicates that the embedded SQL statement was executed successfully.

-   **SQL_SUCCESS_WITH_INFO**  
    This value indicates that the embedded SQL statement was executed but that a warning was detected.

-   **SQL_NO_DATA**  
    This value indicates that no records were returned by an executed SELECT or FETCH statement.

-   **SQL_ERROR**  
    This value indicates that an error occurred during execution of the embedded SQL statement.

### sqlca

sqlca is an instance of the ulpSqlca structure that is declared during the precompile operation. ulpSqlca is an internal structure that is used to store the results of execution of an embedded SQL statement, and is defined in the ulpLibInterface.h file. Developers can use the sqlca variable in their applications to check the result of execution of embedded SQL statements. 

#### ulpSqlca Data Structure Definition

```
typedef struct ulpSqlca
{
    char sqlcaid[8];  /* not used */
    int  sqlcabc;     /* not used */
    int  sqlcode;
    struct
    {
        short sqlerrml;
        char sqlerrmc[2048];
    }sqlerrm;
    char sqlerrp[8];  /* not used */
    int  sqlerrd[6];
    char sqlwarn[8]; /* not used */
    char sqlext[8];  /* not used */
} ulpSqlca;
```

#### sqlca Elements

The ulpSqlca structure consists of numerous constituent elements. Some of these elements are reserved for future use, and are thus not described here. 

The meaning of each element is as follows:

##### sqlcode

This element is used to store the result of execution of an embedded SQL statement. The value stored herein will be one of the following, which were described above:

-   SQL_SUCCESS

-   SQL_SUCCESS_WITH_INFO

-   SQL_NO_DATA

-   SQL_ERROR

##### sqlerrm.sqlerrmc 

This element is used to store error messages. The maximum error message length that can be saved herein is 2048 bytes.

##### sqlerrm.sqlerrml 

This element is used to store the length of the returned error message.

##### sqlerrd[2] 

This element is used to store the number of records that were affected by the execution of an INSERT, UPDATE, or DELETE statement.

When a SELECT or FETCH statement is executed and the output host variable is an array, this element is used to store the number of records that were returned. This is only the number of records that were returned by the most recently executed SELECT or FETCH statement, not a cumulative number of records returned by multiple statements. Therefore, this value will not be larger than the array size.

##### sqlerrd[3] 

The value of this variable can be checked after an array-type input host variable is used to execute an embedded SQL statement. This value indicates the number of elements of the array-type host variable for which the operation was successfully performed. Therefore, this value cannot be larger than the array size. 

For example, if an array-type input host variable whose size is 3 is used to execute an UPDATE statement, and the respective update operations are successful for the 0th array element, unsuccessful for the 1st array element, and successful for the 2nd array element, a value of 2 will be stored in this variable. Meanwhile, the number of records that were actually updated will be stored in sqlca.sqlerrd[2], which means that a value higher than 2 might be stored in sqlca.sqlerrd[2].

> #### Precautions
>
> -   In order to ensure that errors are reliably detected and handled, it is necessary to check sqlca.sqlcode every time an embedded SQL statement is executed.
>   
>-   When a SELECT statement is used to retrieve a value from a character type column, and the size of the corresponding output variable is smaller than (the size of the column + 1), the character column data will be truncated to the length of the host variable - 1 so that it can be stored therein. At this time, the contents of sqlca.sqlcode will be SQL_SUCCESS_WITH_INFO.
>   
> -   If no records are affected by an UPDATE or DELETE operation, the contents of sqlca.sqlcode will be SQL_NO_DATA. To check the number of records that were affected by an UPDATE or DELETE operation, check the value of sqlca.sqlerrd[2].
> 

### SQLCODE

If the result of execution of an embedded SQL statement is SQL_ERROR, the error code will be stored in SQLCODE. 

#### Data Structure Definition

```
int SQLCODE;
```

#### SQLCODE Return Values

0: This is returned upon successful execution of an embedded SQL statement. At this time, the value of sqlca.sqlcode will be SQL_SUCCESS.

1: This is returned when the embedded SQL statement was executed but a warning was detected. At this time, the value of sqlca.sqlcode will be SQL_SUCCESS_WITH_INFO.

100: This is returned when no records were returned by an executed SELECT or FETCH statement. At this time, the value of sqlca.sqlcode will be SQL_NO_DATA.

\-1: This is returned when an error occurred during execution of the embedded SQL statement, but there is no error code corresponding to the error that occurred. At this time, the value of sqlca.sqlcode will be SQL_ERROR

\-Other negative values indicate that an error occurred during execution of the embedded SQL statement. In this case, the return value is the actual error code.

#### Error Codes

Depending on the origin of the error, the error code that is returned when an error occurs during the execution of an embedded SQL statement will be either an APRE error code or a database server error code. 

##### Embedded SQL Statement Error Codes

Errors that are raised by embedded SQL statements at runtime will return APRE error codes. These include the following. (For information on errors other than the following, please refer to *Error Message Reference*.)

-   589826: This code is returned when a connection with the same name already exists. 
-   -589841: This code is returned when the name of the connection exceeds 50 bytes. 
-   -589857: This code is returned when an attempt is made to execute a SQL statement for handling a cursor, and the name of the cursor has not been declared. 
-   -589858: This code is returned when an attempt is made to execute a dynamic SQL statement using an identifier for a SQL statement that has not been prepared.

#####  Database Server Error Codes

When an error that occurs during the execution of a SQL statement originates in the database server, a database server error code will be returned. For complete information about all Altibase error codes, please refer to the Altibase Error Message Reference.

> #### Precaution
>
> The error codes returned by SQLCODE are negative decimal numbers. However, the error codes in the Error Message Reference are positive decimal and hexadecimal numbers. Therefore, when referring to the *Error Message Reference*, use the absolute value of the error code returned by SQLCODE, or convert this absolute value into a hexadecimal number.

### SQLSTATE

SQLSTATE is used to store a status code. This status code can be used to determine the error that occurred, or the warning that was raised. Checking the value of SQLSTATE is useful when the result of execution of an embedded SQL statement is SQL_ERROR or SQL_SUCCESS_WITH_INFO. 

#### Definition of Data Structure

```
char SQLSTATE[6];
```

#### Status Codes

-   00000 - This code is returned upon successful execution of an embedded SQL statement. 
-   01004 - This code is returned when the size of a character type output host variable is the same as or smaller than the corresponding column size. At this time, the returned data are truncated so that they can be stored in the host variable. 
-   07006 – This code is returned when the host variable type is not compatible with the corresponding column type. 
-   07009 – This code is returned when the number of the columns is greater than the number of corresponding host variables. 
-   08001 – This code is returned when the database server is not running. 
-   08S01 – This code is returned when the connection with the database server is interrupted. 
-   21S01 – This code is returned when the number of columns is not same as the number of corresponding input host variables for an INSERT statement. 
-   22002 – This code is returned when NULL data are returned and no indicator variable is being used to detect NULL data. 
-   HY000 – This code indicates a general error. 
-   HY001 – This code is returned when a memory allocation error occurs. 
-   HY009 – This code is returned when the host variable and the indicator variable are both NULL pointers. 
-   HY010 – This code is returned when an attempt is made to fetch records using a cursor that has not been opened.
-   HY090 – This code is returned when the value of the indicator variable is invalid.

### WHENEVER Statement

APRE provides the WHENEVER statement for use in handling runtime errors.

#### Syntax

```
EXEC SQL WHENEVER <condition> <action>;
```

##### Arguments

-   \<*condition*\> : This is the result of execution of an embedded SQL statement.

-   \<*action*\> : This is the action to take in response to the result of execution of the embedded SQL statement.

#### Conditions

The following conditions can be set in a WHENEVER statement:

##### SQLERROR

This condition is used to detect the occurrence of an error, meaning a sqlca.sqlcode value of SQL_ERROR, during the execution of an embedded SQL statement.

##### NOT FOUND

This condition is used to detect the state in which no records are returned in response to the execution of a SELECT or FETCH statement, at which time the value of sqlca.sqlcode is SQL_NO_DATA.

#### Actions

If the result of execution of an embedded SQL statement matches the condition specified in the WHENEVER statement, the action specified here will be taken. 

The following actions can be specified in the WHENEVER statement:

##### CONTINUE

This specifies that the condition is to be ignored and execution is to continue.

##### DO BREAK

This specifies that the current loop construct is to be exited, and that execution is to continue. This has the same effect as using the 'do break'; command in a loop construct. This action can only be specified within a loop construct, and a WHENEVER statement specifying the action will only have an effect within the loop. 

##### DO CONTINUE

This specifies that control is to be passed to the next iteration of the current loop construct, and that execution is to 'continue'. This has the same effect as using the continue; command in a loop construct. This action can only be specified within a loop construct, and a WHENEVER statement specifying the action will only have an effect within the loop.

##### DO *function_name*

This calls the function specified using *function_name.*

##### GOTO label_name

This specifies that control is to be passed to the statement immediately following *label_name*, and that execution is to continue. 

##### STOP

This specifies that the connection with the database server is to be closed, and that the application is to be shut down.

#### Description

The scope of applicability of a WHENEVER statement is not determined by the flow of execution of the application. A WHENEVER statement is valid only within the current file. 

The WHENEVER statement must precede any embedded SQL statements to which it is intended to apply. That is, all embedded SQL statements that follow a WHENEVER statement in the source file will be tested. 

A WHENEVER statement tests the results of execution of all embedded SQL statement in the routine in which it is declared and all routines within that routine). Therefore, whenever the result of execution of any embedded SQL statement in this scope matches the condition in the WHENEVER statement,
the corresponding action will be taken. 

A WHENEVER statement that checks for the SQLERROR condition and a WHENEVER statement that checks for the NOT FOUND condition can coexist without having any effect on each other.

When execution control moves out of the routine in which a WHENEVER statement was declared, the WHENEVER statement has no further effect. From that point onward, embedded SQL statements will be affected by WHENEVER statements located in the current routine or higher routines. 

If two WHENEVER statements that listen for the same condition are present within the same routine, the WHENEVER statement that appeared first will have no effect, and the more recent WHENEVER statement will apply. 

If two WHENEVER statements that check for the same condition exist, but have different scopes of applicability, the WHENEVER statement having the broader scope (i.e. the statement declared in an outer routine) will have no effect, and the WHENEVER statement having the narrower scope (i.e. the statement declared in an inner routine) will apply. 

WHENEVER statements are connection-independent. In other words, a WHENEVER statement in an application with more than one connection affects all embedded SQL statements within its scope of applicability, regardless of the connection to which the embedded SQL statements pertain. 

A WHENEVER statement that has a global scope will affect all embedded SQL statements in the file in which it appears.

### Sample Programs

##### runtime_error_check.sc

This example can be found at $ALTIBASE_HOME/sample/APRE/runtime_error_check.sc

##### Result of Execution

```
$ is –f schema/schema.sql
$ make runtime_error_check
$ ./runtime_error_check
<RUNTIME ERROR CHECK>
------------------------------------------------------
[SQL_SUCCESS]                                                     
------------------------------------------------------
sqlca.sqlcode = 0

-----------------------------------------------------------
 [SQL_SUCCESS_WITH_INFO With SQLSTATE=01004]                      
-----------------------------------------------------------
sqlca.sqlcode          = 1
sqlca.sqlerrm.sqlerrmc = String data right truncated.
SQLSTATE               = 01004
SQLCODE                = 1

-----------------------------------------------------------
[SQL_ERROR With SQLSTATE=22002]                      
-----------------------------------------------------------
sqlca.sqlcode          = -1
sqlca.sqlerrm.sqlerrmc = Indicator variable required but not supplied.
SQLSTATE               = 22002
SQLCODE                = -331841

-----------------------------------------------------------
[SQL_NO_DATA With SELECT]                                        
-----------------------------------------------------------
sqlca.sqlcode          = 100
sqlca.sqlerrm.sqlerrmc = Not found data
SQLSTATE               = 02000
SQLCODE                = 100

-----------------------------------------------------------
[SQL_NO_DATA With FETCH]                                         
-----------------------------------------------------------
sqlca.sqlcode          = 100
sqlca.sqlerrm.sqlerrmc = Not found data
SQLSTATE               = 02000
SQLCODE                = 100
2 rows fetched

-----------------------------------------------------------
[SQL_ERROR]                                                      
-----------------------------------------------------------
sqlca.sqlcode          = -1
sqlca.sqlerrm.sqlerrmc = The row already exists in a unique index.
SQLSTATE               = 23000
SQLCODE                = -69720

-----------------------------------------------------------
[SQL_ERROR With SQLSTATE=HY010]                                  
-----------------------------------------------------------
sqlca.sqlcode          = -1
sqlca.sqlerrm.sqlerrmc = Function sequence error.
SQLSTATE               = HY010
SQLCODE                = -331796

-----------------------------------------------------------
[sqlca.sqlerrd[2]]                                               
-----------------------------------------------------------
sqlca.sqlcode    = 0
sqlca.sqlerrd[2] = 12

-----------------------------------------------------------
sqlca.sqlerrd[3] With Array In-Binding]                          
-----------------------------------------------------------
sqlca.sqlcode    = 0
sqlca.sqlerrd[2] = 12
sqlca.sqlerrd[3] = 3
```

##### whenever1.sc 

This example can be found at $ALTIBASE_HOME/sample/APRE/whenever1.sc

##### whenever2.sc 

This example can be found at $ALTIBASE_HOME/sample/APRE/whenever2.sc

##### Result of Execution

```
$ is –f schema/schema.sql
$ make whenever
$ ./whenever
<WHENEVER>
Success connection

------------------------------------------------------------------
DNO      DNAME                          DEP_LOCATION       MGR_NO 
------------------------------------------------------------------
1001     PAPER TEAM                     New York           16
1002     RESEARCH DEVELOPMENT DEPT 2    Sydney             13
1003     SOLUTION DEVELOPMENT DEPT      Japan              14
2001     QUALITY ASSURANCE DEPT         Seoul              17
3001     CUSTOMER SUPPORT DEPT          London             4
3002     PRESALES DEPT                  Peking             5
4001     MARKETING DEPT                 Seoul              8
4002     BUSINESS DEPT                  LA                 7 
```

