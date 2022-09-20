# Altibase Migration Center 7.10 Release Notes

**(Sept. 19, 2022)**



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

|                    |           GUI mode           | CLI mode |
| ------------------ | :--------------------------: | :------: |
| Computer processor | 800MHz Pentium III or better |  Ditto   |
| Computer memory    |        512 MB or more        |  Ditto   |
| Computer disk      |   150MB or more free space   |  Ditto   |
| Screen resolution  | 1024 * 768 pixels or higher  |    -     |

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

| Source DBMS                                                  | Target DBMS               |
| ------------------------------------------------------------ | ------------------------- |
| Altibase: 4.3.9 or higher<br />CUBRID: 8.4.1 ~ 9.3.5 (ISO-8859-1, UTF-8 charset) <br/>Informix: 11.50 <br />Microsoft SQL Server: 2005 ~ 2012<br />Oracle Database: 9i ~ 11g <br />Oracle MySQL: 5.0 ~ 5.7 <br />Oracle TimesTen: 7.0, 11.2 <br />Tibero: 4sp1~6 | Altibase 6.5.1 or higher  |
| Altibase 4.3.9 or higher                                     | Oracle Database 10g ~ 11g |

<br/>

# 2. Release Information

This section summarizes new features, fixed bugs, and changes in Migration Center.

## 2.1 New Features

### Support MySQL 5.6 and 5.7 as source database

It is possible to migrate database objects and data from MySQL 5.6, 5.7 to Altibase DBMS using Migration Center. Supported version of the source database MySQL has been changed from MySQL 5.0 to **5.5** to MySQL 5.0 to **5.7**. (BUG-49595)

### Support batch processing of LOB data type during data migration

[`Batch LOB type`](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Tools/Altibase_release/kor/Migration%20Center%20User's%20Manual.md#db-to-db-%EB%A7%88%EC%9D%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EC%85%98-%EC%98%B5%EC%85%98) has been added to DB to DB migration options whether or not to batch processing of LOB data type. This option can be used to improve the data migration performance for LOB data type. (BUG-49731)

### Support OpenJDK18

Migration Center 7.10 compatibility verification has been completed in OpenJDK18. 

## 2.2 Bug-Fixes

### BUG-47352 Fix incorrect MySQL bit data type default value conversion

The default value of MySQL BIT data type written with bit-value literals in the form of b'val' had been incorrectly converted to 'b''val' and caused *ERR-2100C : Conversion not applicable* during schema migration. MySQL's bit-value literals default value *`b'val'`* is to be converted into Altibase *`VARBIT'val'`*.

<br/>

# 3. Open Source Libraries / Royalty-Free Images Used

- Open Source Library

Migration Center is based on the following open-source libraries. The licenses are distributed in a text file format along with Migration Center.

| Library                    | Open Source License                                                                                                                                                   |
| -------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Apache Commons Codec       | Homepage: http://commons.apache.org/codec/<br/>License: Apache License 2.0(http://www.apache.org/licenses/LICENSE-2.0.txt)                                            |
| Apache Commons Lang        | Homepage: http://commons.apache.org/proper/commons-lang/<br/>License: Apache License 2.0(http://www.apache.org/licenses/LICENSE-2.0.txt)                              |
| Apache Commons Mathematics | Homepage: http://commons.apache.org/math/ </br><br/>License: Apache License 2.0(http://www.apache.org/licenses/LICENSE-2.0.txt)                                       |
| Apache Commons IO          | Homepage: http://commons.apache.org/proper/commons-io/<br/>License: Apache License 2.0(http://www.apache.org/licenses/LICENSE-2.0.txt)                                |
| Java Help System           | Homepage: http://javahelp.java.net/<br/>License: GPL linking exception(http://en.wikipedia.org/wiki/GPL_linking_exception)                                            |
| JDOM                       | Homepage: http://www.jdom.org/<br/>License: Apache-style Open Source License(http://www.jdom.org/docs/faq.html#a0030)                                                 |
| JUniversalChardet          | Homepage: http://wwwarchive.mozilla.org/projects/intl/UniversalCharsetDetection.html<br/>License: Mozilla Public License Version 1.1(http://www.mozilla.org/MPL/1.1/) |
| JGraphT                    | Homepage: http://jgrapht.org/<br/>License: GNU Lesser General Public License(http://jgrapht.org/LGPL.html)                                                            |
| Log4J                      | Homepage: http://logging.apache.org/index.html<br/>License: Apache License 2.0(http://www.apache.org/licenses/LICENSE-2.0.txt)                                        |
| OpenCSV                    | Homepage: http://opencsv.sourceforge.net/<br/>License: Apache License 2.0(http://www.apache.org/licenses/LICENSE-2.0.txt)                                             |
| Oracle JDBC Driver         | Homepage: http://www.oracle.com<br/>License: OTN(http://www.oracle.com/technetwork/licenses/distribution-license152002.html)                                          |

- Royalty-Free Images

| Library                  | Royalty-Free Images                                 |
| ------------------------ | --------------------------------------------------- |
| org.eclipse.datatools    | Homepage: www.eclipse.org                           |
| asp.net_commercial_free2 | Homepage: www.asp.net                               |
| fugue-icons-3.2.3-src    | Homepage: http://code.google.com/p/fugue-icons-src/ |
| Silk Icons 1.3           | Homepage: www.famfamfam.com                         |

<br/>

# 4. Packages

The Migration Center installation package is provided in two types (.zip, .gz) files.

- MigrationCenter7.10.zip

- MigrationCenter7.10.tar.gz

<br/>

# 5. Download

- Package

<http://support.altibase.com>

- Manual

[Migration Center User's Manual](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Tools/eng/Migration%20Center%20User's%20Manual.md)

- Installation

Please refer to the Migration Center User's Manual.
