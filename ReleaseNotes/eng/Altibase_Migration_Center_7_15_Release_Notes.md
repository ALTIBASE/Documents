Altibase Migration Center 7.15 Release Notes
================

#### Release 7.15 (April 25, 2025)

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
Altibase Release Notes Migration Center 
Release 7.15
Copyright ⓒ 2001~2025 Altibase Corp. All Rights Reserved.<br>
This manual contains proprietary information of Altibase® Corporation; it is provided under a license agreement containing restrictions on use and disclosure and is also protected by copyright patent and other intellectual property law. Reverse engineering of the software is prohibited.<br>
All trademarks, registered or otherwise, are the property of their respective owners.<br>
<b>Altibase Corp</b>
10F, Daerung PostTower II,
306, Digital-ro, Guro-gu, Seoul 08378, Korea
Telephone : +82-2-2082-1000 
Fax       : +82-2-2082-1099
Customer Service Portal : <a href='http://support.altibase.com/en/'>http://support.altibase.com/en/</a>
Homepage                : <a href='http://www.altibase.com'>http://www.altibase.com</a></pre>



<br>

# **Table of Contents** 

- [1. Abstract](#1-abstract)
  - [1.1 Altibase Migration Center](#11-altibase-migration-center)
  - [1.2 System Requirements](#12-system-requirements)
  - [1.3 Compatible DBMS](#13-compatible-dbms)
- [2. Release Information](#2-release-information)
  - [2.1 New Features](#21-new-features)
  - [2.2 Bug-Fixes](#22-bug-fixes)
- [3. Open Source Libraries / Royalty-Free Images Used](#3-open-source-libraries--royalty-free-images-used)
- [4. Packages](#4-packages)
- [5. Download](#5-download)

<br/>

# 1. Abstract

## 1.1 Altibase Migration Center

Migration Center is a database migration tool that either directly or indirectly copies generally compatible database objects and data. Most databases comply with international standards, but no database is exempt from manual database migration. Generally, manual database migration is complicated, time-consuming, and error-prone. Migration Center helps users migrate databases with only a few mouse clicks in Graphic User Interface (GUI) mode, and offers Command Line Interface (CLI) mode as well.

<br/>

## 1.2 System Requirements

### Minimum Hardware

The minimum specifications of hardware for running Migration Center are as follows.

|                        |           GUI mode           | CLI mode |
| ---------------------- | :--------------------------: | :------: |
| **Computer processor** | 800MHz Pentium III or better |  Ditto   |
| **Computer memory**    |        512 MB or more        |  Ditto   |
| **Computer disk**      |   150MB or more free space   |  Ditto   |
| **Screen resolution**  | 1024 * 800 pixels or higher  |    -     |

### Supported Operating Systems

Migration Center can be run regardless of OS if it meets the minimum software specifications.

### Minimum Software

Migration Center is a pure Java application that uses Swing for GUI mode. It runs regardless of the user’s hardware and operating system, but relies on the JRE. The user is recommended to install Oracle, or IBM Java 8 or later. To run Migration Center in GUI mode, the user’s environment must support Java Swing.

| Mode | JRE                         | OS Graphic Library |
| ---- | --------------------------- | ------------------ |
| GUI  | Sun or IBM Java 8 or higher | Required           |
| CLI  | Sun or IBM Java 8 or higher | Not required       |

<br/>

## 1.3 Compatible DBMS

This section introduces the DBMSs and versions that can be migrated using Migration Center 7.15.

| Source DBMS                                                  | Target DBMS              |
| ------------------------------------------------------------ | ------------------------ |
| Altibase 4.3.9 or higher<br />CUBRID 8.4.1 ~ 9.3.5 (ISO-8859-1, UTF-8 charset) <br/>Informix 11.50 <br />Microsoft SQL Server 2005 ~ 2012<br />Oracle Database 9i ~ 19c <br />Oracle MySQL 5.0 ~ 5.7 <br />Oracle TimesTen 7.0, 11.2 <br />Tibero 4 SP1 ~ 7<br/>PostgreSQL 9.5.3 | Altibase 6.5.1 or higher |

<br/>

# 2. Release Information

This section summarizes new features, fixed bugs, and changes in Migration Center 7.15.

## 2.1 New Features

### Support Oracle 12c, 18c and 19c as Source Database
It is possible to migrate database objects and data from Oracle 12c, 18c and 19c to Altibase DBMS using Migration Center. Supported version of the source database Oracle has been changed from Oracle 9i to **11g** to Oracle 9i to **19c**.

### Support Tibero 7 as Source Database
It is possible to migrate database objects and data from Tibero 7 to Altibase DBMS using Migration Center. Supported version of the source database Tibero has been changed from Tibero 4 to **6** to Tibero 4 to **7**.

### Provide an Option to Set whether to Migrate an Invisible Column
To the DB to DB migration option, the option of 'Invisible Column Migration' was added to set whether to migrate the Invisible column. Because Altibase does not provide Invisible column functionality, the Invisible column migrates to the general column. If the option value is Yes, the Invisible column is converted and migrated to the Altibase general column, and if the option value is No, the Invisible column is excluded from the migration.

### Provide an Option to Set whether String Data Type VARCHAR Type to CLOB Conversion
In the DB to DB migration option, the 'Convert Oversized String VARCHAR To CLOB' option was added to set whether to convert the CLOB type for columns whose column size exceeds 32,000 Bytes, which is the maximum size of Altibase's VARCHAR type. If the option value is Yes, it is converted and migrated to the CLOB type, and if the option value is No, it is converted to the VARCHAR type with a column size of 32,000 and migrated.

### Sequence .nextval Column Supports Default Migration
Altibase provides the function to use sequence .nextval for the default values of a column. Migration Center supports migration of the default values of the sequence .nextval column.

### Support for Identity Column Migration
Altibase does not support identity column functionality. Therefore, instead of the identity column, it automatically generates a sequence for use in that column and sets the default value of the column to .nextval of the generated sequence.

### Supports DEFAULT ON NULL column default migration
Altibase does not support the DEFAULT ON NULL function in the default value of the column. Therefore, instead of DEFAULT ON NULL, the default value specified in the DEFAULT ON NULL statement of the column is set to the default value of the Altibase column, and the NOT NULL constraint is added.

### Support for Migration of External Table and Hybrid Partitioned Table provided Oracle
Altibase does not provide external and hybrid partitioned table functions provided by Oracle. These tables are converted to general tables or partitioned tables and migrated. In addition, these tables are expected to be large in capacity and are automatically assigned to the disk table space.

<br/>

## 2.2 Bug-Fixes

### BUG-51319 Corrects the Object Type Display Error if the Target is a Column in the "Unacceptable Name" Step During the Reconcile phase
During the Reconcile phase, the "Unacceptable Name" is a step of displaying objects that violate the object name rule of the target database and adjusting the object name. If the target object is a column, there is an error in which the object type is incorrectly displayed, so it was corrected.

<br/>

# 3. Open Source Libraries / Royalty-Free Images Used

#### Open Source Library

Migration Center is based on the following open-source libraries. The licenses are distributed in a text file format along with Migration Center.

| Library                                                      | Open Source License                                          |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [Apache Commons Codec](http://commons.apache.org/codec/ )    | [Apache License 2.0](http://www.apache.org/licenses/LICENSE-2.0.txt) |
| [Apache Commons Lang](http://commons.apache.org/proper/commons-lang/) | [Apache License 2.0](http://www.apache.org/licenses/LICENSE-2.0.txt) |
| [Apache Commons Mathematics](http://commons.apache.org/math/) | [Apache License 2.0](http://www.apache.org/licenses/LICENSE-2.0.txt) |
| [Apache Commons IO](http://commons.apache.org/proper/commons-io/) | [Apache License 2.0](http://www.apache.org/licenses/LICENSE-2.0.txt) |
| [Java Help System](http://javahelp.java.net/)                | [GPL linking exception](http://en.wikipedia.org/wiki/GPL_linking_exception) |
| [JDOM](http://www.jdom.org/)                                 | [Apache-style Open Source License](http://www.jdom.org/docs/faq.html#a0030) |
| [JUniversalChardet](http://wwwarchive.mozilla.org/projects/intl/UniversalCharsetDetection.html ) | [Mozilla Public License Version 1.1](http://www.mozilla.org/MPL/1.1/) |
| [JGraphT](http://jgrapht.org/)                               | [GNU Lesser General Public License](http://jgrapht.org/LGPL.html) |
| [Log4J](http://logging.apache.org/index.html)                | [Apache License 2.0](http://www.apache.org/licenses/LICENSE-2.0.txt) |
| [OpenCSV](http://opencsv.sourceforge.net/)                   | [Apache License 2.0](http://www.apache.org/licenses/LICENSE-2.0.txt) |
| [Oracle JDBC Driver](http://www.oracle.com/)                 | [OTN](http://www.oracle.com/technetwork/licenses/distribution-license152002.html) |

#### Royalty-Free Images

| Library                  | Royalty-Free Images                            |
| ------------------------ | ---------------------------------------------- |
| org.eclipse.datatools    | [www.eclipse.org](http://www.eclipse.org/)     |
| asp.net_commercial_free2 | [www.asp.net](http://www.asp.net/)             |
| fugue-icons-3.2.3-src    | http://code.google.com/p/fugue-icons-src/      |
| Silk Icons 1.3           | [www.famfamfam.com](http://www.famfamfam.com/) |

<br/>

# 4. Packages

The Migration Center installation package is provided in two types (.zip, .gz) files.

- MigrationCenter7.15.zip

- MigrationCenter7.15.tar.gz

<br/>

# 5. Download

#### Package

<http://support.altibase.com/en/product>

#### Manual

[Migration Center User's Manual](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Tools/Altibase_release/eng/Migration%20Center%20User's%20Manual.md)

#### Installation

Please refer to the Migration Center User's Manual.
