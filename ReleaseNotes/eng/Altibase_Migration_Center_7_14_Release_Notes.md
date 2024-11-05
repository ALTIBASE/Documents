Altibase Migration Center 7.14 Release Notes
================

#### Release 7.14 (Novenber 1, 2024)

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
Release 7.14
Copyright ⓒ 2001~2024 Altibase Corp. All Rights Reserved.<br>
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

This section introduces the DBMSs and versions that can be migrated using Migration Center 7.14.

| Source DBMS                                                  | Target DBMS              |
| ------------------------------------------------------------ | ------------------------ |
| Altibase 4.3.9 or higher<br />CUBRID 8.4.1 ~ 9.3.5 (ISO-8859-1, UTF-8 charset) <br/>Informix 11.50 <br />Microsoft SQL Server 2005 ~ 2012<br />Oracle Database 9i ~ 11g <br />Oracle MySQL 5.0 ~ 5.7 <br />Oracle TimesTen 7.0, 11.2 <br />Tibero 4 SP1 ~ 6<br/>PostgreSQL 9.5.3 | Altibase 6.5.1 or higher |

<br/>

# 2. Release Information

This section summarizes new features, fixed bugs, and changes in Migration Center.

## 2.1 New Features

### BUG-50652	Allow User to Modify Select Condition Entered in Reconcile Step Before Executing in Run Step

When extracting data from the source database, a function that allows only data that meets a specific condition to be selectively extracted and migrated has been added. The Select condition can be modified in "Select Editing" during the Reconcile step, or edited directly by the user in the TableCondition.properties file after completing the Reconcile step.

<br/>

## 2.2 Bug-Fixes

### BUG-50263	Data type mapping update: BINARY_DOUBLE of Oracle, TimesTen, and Tibero is now mapped to Altibase DOUBLE, replacing the previous VARCHAR mapping

The BINARY_DOUBLE types of Oracle, TimesTen, and Tibero are compatible with the Altibase DOUBLE type, so the default data mapping type need to be changed. However, Oracle, TimesTen, and Tibero support special values of NaN(Not a Number) and INF(Infinity), while Altibase does not. For these values, data loss can occur.

### BUG-50821	Oracle has been removed from destination databases in Migration Center

Remove the Altibase to Oracle data migration feature supported by Migration Center.

### BUG-50827 	Data type mapping update: The TimesTen BINARY type is now mapped to Altibase BYTE, replacing the previous BLOB mapping

Change the default data mapping type of TimesTen Binary type from Altibase BLOB type to Altibase BYTE type.

### BUG-51034	Provide Empty String Data Conversion Function for Migration to Altibase

When performing from a specific DBMS to Altibase migration, the Empty String value may not operate normally and may be removed. The function of converting Empty String data into data suitable for Altibase is added to the migration option.

### BUG-51035	Provide Conversion Function for Not Null & Default ''(Empty String) Columns During Migration to Altibase

When performing from a specific DBMS to Altibase migration, Not Null & Default ''(Empty String) column does not work normally and is removed. When converting Not Null & Default '' columns for migration, add the option to configure DDL suitable for Altibase.

### BUG-51075	Migration Center UI Enhancement: Add Scrollbar and Adjust Height for Improved Usability in Option Window

As options are continuously added to the Migration Center, the length of the existing Option window is too long, which may cause inconvenience to use. Add a scrollbar to the Option window and modify the height of the Option window to be small.

### BUG-51076	Migration Center UI Enhancement: Allow User-Adjustable Separation Bar in the Main Window

In some cases, the Project Tree and DB Properties window on the left side of the Migration Center main window may not be visible at certain resolutions. In the left window, the user cannot use the Migration Center normally in this case because the user cannot arbitrarily adjust the size. Modify the Project Tree and DB Properties window on the left side of the main window to allow the user to adjust the size.

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

- MigrationCenter7.14.zip

- MigrationCenter7.14.tar.gz

<br/>

# 5. Download

#### Package

<http://support.altibase.com>

#### Manual

[Migration Center User's Manual](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Tools/Altibase_release/eng/Migration%20Center%20User's%20Manual.md)

#### Installation

Please refer to the Migration Center User's Manual.
