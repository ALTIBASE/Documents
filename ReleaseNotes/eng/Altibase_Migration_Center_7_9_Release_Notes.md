

- [Altibase Migration Center 7.9 Release Notes](#altibase-migration-center-79-release-notes)
  - [1. Abstract](#1-abstract)
    - [1.1 System Requirements](#11-system-requirements)
    - [1.2 Supported Operating Systems and Platforms](#12-supported-operating-systems-and-platforms)
  - [2. Release Information](#2-release-information)
    - [2.1 Altibase Migration Center 7.9](#21-altibase-migration-center-79)
    - [2.2 Changes](#22-changes)
    - [2.3 Open Source Libraries / Royalty-Free Images Used](#23-open-source-libraries--royalty-free-images-used)
    - [2.4 Packages](#24-packages)
    - [2.5 Downloads](#25-downloads)

Altibase Migration Center 7.9 Release Notes
===============================

**(Dec. 31, 2021)**

## 1. Abstract

### 1.1 System Requirements

#### Minimum Hardware

|                    |           GUI mode           | CLI mode |
| ------------------ | :--------------------------: | :------: |
| Computer processor | 800MHz Pentium III or better |  Ditto   |
| Computer memory    |        512 MB or more        |  Ditto   |
| Computer disk      |   150MB or more free space   |  Ditto   |
| Screen resolution  | 1024 * 768 pixels or higher  |    -     |

### 1.2 Supported Operating Systems and Platforms

| Mode | JRE                         | OS Graphic Library |
| ---- | --------------------------- | ------------------ |
| GUI  | Sun or IBM Java 8 or higher | Required           |
| CLI  | Sun or IBM Java 8 or higher | Not required       |

Migration Center is a pure Java-based client application relying on the JAVA Runtime Environment (JRE) instead of the client's hardware or an operating system. In order to execute Migration Center in the GUI mode, however, additional support for the graphic library of operating system is required.

## 2. Release Information

### 2.1 Altibase Migration Center 7.9

Migration Center is a database migration tool which enables users to migrate a third-party database to Altibase database and external files or Altibase database to Oracle database in a convenient manner. Typically, the tasks of manual database migration are complicated, time-consuming, and prone to human error. In order to relieve such burden, Migration Center can be utilized providing qualified help for users to efficiently perform database migration with only a few mouse clicks in the Graphic User Interface (GUI) mode. Moreover, it also supports the migration at a Command Line Interface (CLI) mode for optimized resource consumption.

#### 2.1.1 New Features

* Support Tibero 4 sp1 as source database
* Support OpenJDK12

#### 2.1.2  Bug-Fixes

| PK        | SYNOPSIS                                                     |
| :-------- | :----------------------------------------------------------- |
| BUG-47352 | Changes in "Partitioned Table Conversion" during the reconcile phase are not kept when returning after next or previous step |
| BUG-47372 | Need to improve type conversion method for local variables in PSM |
| BUG-47376 | Support source DDL with dbms_metadata since Altibase 7       |
| BUG-47381 | If the object referenced by a synonym is not a build target, hang occurs in the reconcile stage. |
| BUG-47402 | Support TimesTen direct connection                           |
| BUG-47408 | Reserved words allowed as column names must be excluded from _poc autoconversion. |
| BUG-47409 | Composite index including a PK column in the source DB is excluded from the migration target with an error in the build phase. |
| BUG-48340 | If the table name includes underscore, the table column with a similar name is also included. |
| BUG-48672 | As of Altibase 7.2, the warning window should not appear even if there is no default partition in the range partition table. |
| BUG-49467 | Support TimesTen 11.2.1.9.10 to Altibase migration           |
| BUG-49499 | Upgrade log4j version to 2.17.0 due to its security issue    |

### 2.2 Changes

Features that have been added, deleted or updated in Migration Center are listed and explained below.

* Due to security issues, log4j has been updated to the latest version, and the minimum JRE version for running Migration Center is changed from 1.5 to 8.
* Bundled JRE version in Migration Center is updated from 7 to 8 in order to support Altibase 7.2 JDBC that requires JRE 8 or higher.

#### 2.2.1 Version Updates

Migration Center Version

| Altibase Migration Center Version |
|:---------------------------------:|
| 7.9                               |

#### 2.2.2 Database Compatibility

##### Destination Database: Altibase

* Source Database
  
  * Altibase : Altibase 4.3.9 or higher
  * ORACLE : Oracle 9i ~ 11g
  * MS-SQL :  MS-SQL 2005 ~ 2012
  * MySQL : MySQL 5.0 ~ 5.5
  * Informix : Informix 11.50
  * TimesTen : TimesTen 7.0, TimesTen 11.2
  * CUBRID : CUBRID 8.4.1 ~ 9.3.5 (ISO-8859-1, UTF-8 charset)
  * Tibero : Tibero 4 sp1, 5 ~ 6

* Destination Database
  
  * Altibase : Altibase 6.5.1 or higher

##### Destination Database: Oracle

- Source Database
  
  - Altibase : Altibase 4.3.9 or higher
* Destination Database
  
  * ORACLE : Oracle 10g ~ 11g

#### 2.2.3 Properties

NONE

#### 2.2.4 Error Messages

NONE

### 2.3 Open Source Libraries / Royalty-Free Images Used

Migration Center is based on the following open-source libraries. The licenses are distributed in a text file format along with Migration Center.

* Open Source Library

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

* Royalty-Free Images</br>

| Library                  | Royalty-Free Images                                 |
| ------------------------ | --------------------------------------------------- |
| org.eclipse.datatools    | Homepage: www.eclipse.org                           |
| asp.net_commercial_free2 | Homepage: www.asp.net                               |
| fugue-icons-3.2.3-src    | Homepage: http://code.google.com/p/fugue-icons-src/ |
| Silk Icons 1.3           | Homepage: www.famfamfam.com                         |

### 2.4 Packages

| JRE                         | Archive Name                                         |
| --------------------------- | ---------------------------------------------------- |
| Sun or IBM Java 8 or higher | MigrationCenter7.9.zip<br/>MigrationCenter7.9.tar.gz |

### 2.5 Downloads

#### 2.5.1 Packages

<http://support.altibase.com>

#### 2.5.2 Manual

[Migration Center User's Manual](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Tools/eng/Migration%20Center%20User's%20Manual.md)

#### 2.5.3 Installation

Please refer to the Migration Center User's Manual.
