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
| Altibase 4.3.9 or higher<br />CUBRID 8.4.1 ~ 9.3.5 (ISO-8859-1, UTF-8 charset) <br/>Informix 11.50 <br />Microsoft SQL Server 2005 ~ 2012<br />Oracle Database 9i ~ 19c <br />Oracle MySQL 5.0 ~ 5.7 <br />Oracle TimesTen 7.0, 11.2 <br />Tibero 4 SP1 ~ 7.2.2<br/>PostgreSQL 9.5.3 | Altibase 6.5.1 or higher |

<br/>

# 2. Release Information

This section summarizes new features, fixed bugs, and changes in Migration Center 7.15.

## 2.1 New Features

### Support Oracle 12c, 18c and 19c as Source Database
Oracle 12c, 18c and 19c have been added to the list of supported source databases.

### Support Tibero 7(~7.2.2) as Source Database
Tibero 7(~7.2.2) has been added to the list of supported source databases.

### Provide an Option to Set whether to Migrate an Invisible Column
Since Altibase does not support Oracle’s invisible column feature, invisible columns are converted into regular columns during migration. If the 'Invisible Column Migration' option is set to Yes, these columns are migrated as general columns in Altibase; if set to No (the default), they are excluded from the migration.

### Provide an Option to Set whether String Data Type VARCHAR Type to CLOB Conversion
In the DB to DB migration option, the 'Convert Oversized String VARCHAR To CLOB' option was added to set whether to convert the CLOB type for columns whose column size exceeds 32,000 Bytes, which is the maximum size of Altibase's VARCHAR type. If the option value is Yes, it is converted and migrated to the CLOB type, and if the option value is No, it is converted to the VARCHAR type with a column size of 32,000 and migrated.

### Support for Oracle's Identity Column Migration
Altibase does not support Oracle’s identity column feature. Accordingly, during migration, a sequence is automatically created to replace the identity column. The column’s default value is then set to the .nextval of the generated sequence to replicate the original behavior.

### Supports Oracle's DEFAULT ON NULL column default migration
During migration from Oracle to Altibase, the DEFAULT ON NULL clause—supported in Oracle—is not retained, as Altibase does not support this feature. Instead, the specified default value is assigned as the column’s default, and a NOT NULL constraint is added to preserve the original semantics.

### Support for Migration of External Table and Hybrid Partitioned Table provided Oracle
Altibase does not support external tables and hybrid partitioned tables as Oracle does. These types of tables are converted into regular or partitioned tables during migration. Since they are typically large in size, they are automatically assigned to disk tablespaces. During the Reconcile phase, users can adjust the tablespaces where each table will be stored.

<br/>

## 2.2 Bug-Fixes

### BUG-51219 Modify PSM Transducer Rule: RULE-31001 Change the Cursor Definition Method to Resolve the Reference Scope Issue that Occurs when all Implicit Cursors are Converted to Explicit Cursors.
Since Altibase does not support implicit cursors, all implicit cursors are converted to explicit cursors. Previously, explicit cursors were defined in the declaration section. However, in this case, reference scope issues may occur, so the cursor is defined directly above each FOR LOOP statement.

### BUG-51220 Add PSM converter rules: Add rule for converting unsupported SQLERRM(SQLCODE) functions.
Altibase does not support SQLERRM(SQLCODE) functions. PSM converter rule RULE-40023 was added for SQLERRM(SQLCODE) function conversion that is not supported.

### BUG-51311 Add PSM converter rule: Add rule to remove unsupported EDITONABLE/NONEDITONABLE keyword.
Altibase does not support the EDITIONABLE/NONEDITIONABLE keyword. PSM converter rule RULE-17003 was added to remove the unsupported EDITIONABLE/NONEDITIONABLE keyword.

### BUG-51319: Fixes Incorrect Object Type Display for Columns in the "Unacceptable Name" Step During the Reconcile Phase
In the Reconcile phase, the "Unacceptable Name" step identifies objects that violate the target database’s naming rules and allows for renaming. Previously, when the target object was a column, an error caused it to be incorrectly displayed as a Primary key. This issue has been resolved.

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
