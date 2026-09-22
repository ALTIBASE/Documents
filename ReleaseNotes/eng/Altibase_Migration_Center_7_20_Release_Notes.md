Altibase Migration Center 7.20 Release Notes
================

#### Release 7.20 (June 19, 2026)

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
Release 7.20
Copyright ⓒ 2001~2026 Altibase Corp. All Rights Reserved.<br>
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

This section introduces the DBMSs and versions that can be migrated using Migration Center 7.20.

| Source DBMS                                                  | Target DBMS                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Altibase 4.3.9 or higher<br />Altibase Windows 2026 (Altibase 2.6.0)<br />CUBRID 8.4 ~ 11.4 (ISO-8859-1, UTF-8 charset) <br />Microsoft SQL Server 2005 ~ 2012<br />Oracle Database 10gR2 ~ 21c <br />Oracle MySQL 5.0 ~ 5.7 <br />Oracle TimesTen 11.2 <br />Tibero 4 SP1 ~ 7.2.2<br/>PostgreSQL 9.5 ~ 18 | Altibase 6.5.1 or higher<br />Altibase Windows 2026 (Altibase 2.6.0) |

<br/>

# 2. Release Information

This section summarizes new features, fixed bugs, and changes in Migration Center 7.20.

## 2.1 New Features

### Expanded Support for CUBRID 8.4 - 11.4 as Source Database

CUBRID versions 8.4 - 11.4 are now supported as source databases.

### Added 'No Logging' Migration Option

A new **No Logging** option has been added to improve migration performance and optimize disk usage by preventing log generation during table and index migration. The default value is **Yes**. The No Logging feature is applied only in supported environments, and Migration Center automatically determines whether it can be used by checking the target database environment.

- For **tables**, this option prevents log generation in the target Altibase database during data migration. This feature is supported only on **Altibase 7.3 or later**.
- For **indexes**, the **NOLOGGING FORCE** clause is added to the index creation statement, preventing log generation during index creation. This feature applies only to **Disk B+Tree indexes**.

### Added 'Defer Index Creation' Migration Option

A new **Defer Index Creation** option has been added to improve migration performance by postponing index creation during migration and allowing users to create indexes manually after the migration is completed. The default value is **No**.

When this option is enabled, the migration project directory contains the `DbIndex_Create.sql` file for index creation and the `DbIndex_Drop.sql` file for index removal.

Regardless of this option, Function-Based Indexes are automatically created before data insertion.

### Added 'Global to Local Partition Index' Migration Option

A new **Global to Local Partition Index** option has been added to optimize performance and reduce log usage by converting Global Non-Partitioned Indexes on partitioned tables in the source database to Local Prefixed Partitioned Indexes. The conversion is performed only when the table partition key and the index key match exactly.

The default value is **Yes**, and this option is applied only when **Keep Partitioned Table** is set to **Yes**.

## 2.2 Bug-Fixes

### BUG-52287 Fixed an Issue Where Converted Object Names Exceeded the Altibase Object Name Length Limit

Fixed an issue where migration could fail when a converted object name exceeded the Altibase object name length limit. This occurred when Migration Center generated a new object name based on an existing object name that exceeded a certain length.

### BUG-52333 Fixed Incorrect Default Tablespace Assignment for Users with ALL PRIVILEGES

Fixed an issue where the default tablespace of the SYS user was incorrectly used when generating default tablespace information for users granted the ALL PRIVILEGES privilege in Altibase. As a result, the target database user could be assigned an incorrect default tablespace.

### BUG-52375 Fixed Incorrect Detection of Function-Based Indexes in Altibase

Fixed an issue where Migration Center could incorrectly determine whether an index was a Function-Based Index when Altibase was used as the source database.

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

- MigrationCenter7.20.zip

- MigrationCenter7.20.tar.gz

<br/>

# 5. Download

#### Package

<http://support.altibase.com/en/product>

#### Manual

[Migration Center User's Manual](https://manual.altibase.com/8.1/en/external-tools/migration-center/copyright/)

#### Installation

Please refer to the Migration Center User's Manual.
