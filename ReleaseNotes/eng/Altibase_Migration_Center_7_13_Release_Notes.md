Altibase Migration Center 7.13 Release Notes
================

#### Release 7.13 (March 20, 2023)

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
Release 7.13
Copyright ⓒ 2001~2023 Altibase Corp. All Rights Reserved.<br>
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

Migration Center is a database migration tool which enables users to migrate a third-party database to Altibase database and external files or Altibase database to Oracle database in a convenient manner. Typically, the tasks of manual database migration are complicated, time-consuming, and prone to human error. In order to relieve such burden, Migration Center can be utilized providing qualified help for users to efficiently perform database migration with only a few mouse clicks in the Graphic User Interface (GUI) mode. Moreover, it also supports the migration at a Command Line Interface (CLI) mode for optimized resource consumption.

<br/>

## 1.2 System Requirements

### Minimum Hardware

|                        |           GUI mode           | CLI mode |
| ---------------------- | :--------------------------: | :------: |
| **Computer processor** | 800MHz Pentium III or better |  Ditto   |
| **Computer memory**    |        512 MB or more        |  Ditto   |
| **Computer disk**      |   150MB or more free space   |  Ditto   |
| **Screen resolution**  | 1024 * 768 pixels or higher  |    -     |

### Supported Operating Systems

Migration Center can be run regardless of OS if it meets the minimum software specifications.

### Minimum Software

Migration Center is a pure Java-based client application relying on the JAVA Runtime Environment (JRE) instead of the client's hardware or an operating system. In order to execute Migration Center in the GUI mode, however, additional support for the graphic library of operating system is required.

| Mode | JRE                         | OS Graphic Library |
| ---- | --------------------------- | ------------------ |
| GUI  | Sun or IBM Java 8 or higher | Required           |
| CLI  | Sun or IBM Java 8 or higher | Not required       |

<br/>

## 1.3 Compatible DBMS

This section introduces the DBMSs and versions that can be migrated using Migration Center 7.13.

#### The target DBMS is Altibase

| Source DBMS                                                  | Target DBMS              |
| ------------------------------------------------------------ | ------------------------ |
| Altibase 4.3.9 or higher<br />CUBRID 8.4.1 ~ 9.3.5 (ISO-8859-1, UTF-8 charset) <br/>Informix 11.50 <br />Microsoft SQL Server 2005 ~ 2012<br />Oracle Database 9i ~ 11g <br />Oracle MySQL 5.0 ~ 5.7 <br />Oracle TimesTen 7.0, 11.2 <br />Tibero 4 SP1 ~ 6<br/>PostgreSQL 9.5.3 | Altibase 6.5.1 or higher |

#### The target DBMS is Oracle

| Source DBMS | Target DBMS               |
| ------------------------------------------------------------ | ------------------------- |
| Altibase 4.3.9 or higher                                     | Oracle Database 10g ~ 11g |

<br/>

# 2. Release Information

This section summarizes new features, fixed bugs, and changes in Migration Center.

## 2.1 New Features

<br/>

## 2.2 Bug-Fixes

### BUG-50180 When performing PostgreSQL to Altibase migration, creating a child table that inherits the Serial data type of the parent table fails

PostgreSQL supports inheritance relationship tables. Among the inheritance tables, child tables inheriting the serial data type column belonging to the parent table fail to create the table during migration due to an incorrect sequence reference in the default value of the corresponding column. Modify the inherited serial data type column to create an accurate default value.

### BUG-50173	During PostgreSQL constraint migration, a NullPointer exception occurs in a type that is not supported by Altibase.

During PostgreSQL constraint migration, a NullPointer exception may occur while processing a type that is not supported by Altibase. Ignore constarint types that are not supported and modify them to pass.

### BUG-50160	Incorrect sequence 'start with' value when migrated from PostgreSQL

For sequences that have been used even once in PostgreSQL, the start with value of the migrated sequence may be set incorrectly. Modify it so that it is migrated accurately regardless of whether it is used or not.

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

- MigrationCenter7.13.zip

- MigrationCenter7.13.tar.gz

<br/>

# 5. Download

#### Package

<http://support.altibase.com>

#### Manual

[Migration Center User's Manual](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Tools/Altibase_release/eng/Migration%20Center%20User's%20Manual.md)

#### Installation

Please refer to the Migration Center User's Manual.
