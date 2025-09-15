Altibase Migration Center 7.16 Release Notes
================

#### Release 7.16 (September 12, 2025)

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
Release 7.16
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

Migration Center is a database migration tool that either directly or indirectly copies generally compatible database objects and data. Generally, manual database migration is complicated, time-consuming, and error-prone. Migration Center helps users migrate databases with only a few mouse clicks in Graphic User Interface (GUI) mode, and offers Command Line Interface (CLI) mode as well.

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

This section introduces the DBMSs and versions that can be migrated using Migration Center 7.16.

| Source DBMS                                                  | Target DBMS              |
| ------------------------------------------------------------ | ------------------------ |
| Altibase 4.3.9 or higher<br />CUBRID 8.4.1 ~ 9.3.5 (ISO-8859-1, UTF-8 charset) <br />Microsoft SQL Server 2005 ~ 2012<br />Oracle Database 10gR2 ~ 21c <br />Oracle MySQL 5.0 ~ 5.7 <br />Oracle TimesTen 11.2 <br />Tibero 4 SP1 ~ 7.2.2<br/>PostgreSQL 9.5.3 | Altibase 6.5.1 or higher |

> [!NOTE]
>
> **Unsupported Versions**
>
> The following database versions are no longer supported in Migration Center starting from version 7.16:
>
> - **Oracle**: 9i, 10g Release 1 (10gR1)
> - **TimesTen**: 7
> - **Informix**: 11.50

<br/>

# 2. Release Information

This section summarizes new features, fixed bugs, and changes in Migration Center 7.16.

## 2.1 New Features

### Support Oracle 21c as Source Database
Oracle 21c has been added to the list of supported source databases.

### Support for JSON Data Type
The JSON data type has been added to the list of supported data types. During migration, it will be mapped to the JSON type if the target database (Altibase) supports it. If the target database doesn't support JSON, it will be mapped to the CLOB type instead.

### Provide an Option to Specify the Correction Factor for Character Type Conversion
The 'Correction Factor for Character Type Conversion' option has been added to the DB to DB Migration Options. This option specifies a correction factor for the automatic length conversion of character data types (CHAR, VARCHAR) when the source and target databases use different character sets. The default value is automatically calculated, and it cannot be set to less than 1. Note that this correction factor does not apply to columns that have a column-specific character set defined.

### Validation Added for Migration Option Values in the Migration Option Window
A new pop-up window has been added to the migration option window. This window displays a list of options with invalid values and their reasons when an invalid option value is entered. Invalid option values will not be applied unless they are corrected to a valid value within the option window.

### Oracle Internationalization Support Library (orai18n.jar) Added to Migration Center package

To support Oracle’s multilingual character sets, the **orai18n.jar** has been added to the Migration Center package.

<br/>

## 2.2 Bug-Fixes

### BUG-51321 Fixes an Issue where the "Use double-quoted identifier" Option was not Applied to Columns in the "Unacceptable Name" Step During the Reconcile Phase
In the Reconcile phase, the "Unacceptable Name" step identifies objects that violate the target database’s naming rules and allows for renaming. Previously, when the target object was a column, the "Use double-quoted identifier" option was not applied due to an error. This issue has been resolved.

### BUG-51472 Add PSM converter rules: Add rule to remove unsupported DEFAULT COLLATION clause
Altibase does not support the DEFAULT COLLATION clause. PSM converter rules RULE-11009, RULE-12018, RULE-13016, RULE-14011, and RULE-16003 have been added to remove the unsupported DEFAULT COLLATION clause.

### BUG-51650 Apply automatic adjustment of character column length between heterogeneous character sets when the source database uses a single-byte character set
The automatic adjustment of character column length between heterogeneous character sets is now applied even when the source database uses a single-byte character set.

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

- MigrationCenter7.16.zip

- MigrationCenter7.16.tar.gz

<br/>

# 5. Download

#### Package

<http://support.altibase.com/en/product>

#### Manual

[Migration Center User's Manual](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Tools/Altibase_release/eng/Migration%20Center%20User's%20Manual.md)

#### Installation

Please refer to the Migration Center User's Manual.
