- [dataCompJ Release Notes](#datacompj-release-notes)
  - [1. Overview](#1-overview)
    - [1.1 Hardware Requirements](#11-hardware-requirements)
    - [1.2 Supported Operating Systems and Platforms](#12-supported-operating-systems-and-platforms)
  - [2. Release Information](#2-release-information)
    - [2.1 Version](#21-version)
    - [2.2 New Features](#22-new-features)
    - [2.3 Bug Fixed](#23-bug-fixed)
    - [2.4 Database Compatibility](#24-database-compatibility)
    - [2.5 Properties](#25-properties)
    - [2.6 Error Messages](#26-error-messages)
  - [3. Open Source Libraries Used](#3-open-source-libraries-used)
  - [4. Packages](#4-packages)
  - [5. Downloads](#5-downloads)
    - [5.1 Packages](#51-packages)

# dataCompJ Release Notes

**(Feb. 17, 2022)**

## 1. Overview

 Altibase dataCompJ is a utility designed to guarantee data consistency between two heterogeneous databases and resolve data inconsistency if any. The main target data for comparing in dataCompJ is replicated data from Altibase to another heterogeneous database using Altibase Adapter for Oracle (oraAdapter) or JDBC Adapter provided by Altibase. dataCompJ compares Altibase with another heterogeneous database on a table-by-table basis, and outputs information on any inconsistency it detects.
Also, it offers an efficient feature for synchronizing two databases in the event of data inconsistency. A proper use of Altibase dataCompJ would be a cornerstone of effective data management with advantageous usability along with its advanced technical performance.  

### 1.1 Hardware Requirements

- Main memory: Minimum 512MB, 4GB or more recommended
- Disk: More than 500MB of free space for installation

### 1.2 Supported Operating Systems and Platforms

| Mode | JRE                                                         |
| ---- | ----------------------------------------------------------- |
| CLI  | Oracle, OpenJDK or IBM Java Runtime Environment 8 or higher |

dataCompJ is a pure Java-based client application relying on the JAVA Runtime Environment (JRE) instead of the client's hardware or an operating system.

## 2. Release Information

### 2.1 Version

- 7.2

### 2.2 New Features

- N/A

### 2.3 Bug Fixed

| PK        | Synopsis                                                     |
| --------- | ------------------------------------------------------------ |
| BUG-45222 | Requires handling of user-entered object names enclosed in double quotation marks. |
| BUG-46675 | Error message for the unsupported DB JDBC URL should be provided more clearly. |
| BUG-46689 | Need to modify the DB type check routine using the JDBC URL string. |
| BUG-49501 | dataCompJ log4j upgraded to version 2.17.1 due to security issues. |

### 2.4 Database Compatibility

#### Master Database

- Altibase: Altibase 5.3.3 or higher

#### Slave Database

- Oracle: Oracle 9i or higher
- MariaDB: MariaDB 5.5.x or higher

### 2.5 Properties

### 2.6 Error Messages

## 3. Open Source Libraries Used

dataCompJ is based on the following open-source libraries. The licenses are distributed in a text file format
along with dataCompJ.

| Library             | Open Source License                                          |
| ------------------- | ------------------------------------------------------------ |
| Apache Commons CLI  | http://commons.apache.org/proper/commons-cli/<br/>License: Apache License 2.0 (http://www.apache.org/licenses/LICENSE-2.0.txt) |
| Apache Commons Lang | http://commons.apache.org/proper/commons-lang/ <br/>License: Apache License 2.0 (http://www.apache.org/licenses/LICENSE-2.0.txt) |
| Apache Commons IO   | http://commons.apache.org/proper/commons-io/ <br>License: Apache License 2.0 (http://www.apache.org/licenses/LICENSE-2.0.txt) |
| JDOM                | http://www.jdom.org/ <br/>License: Apache-style Open Source License (http://www.jdom.org/docs/faq.html#a0030) |
| Log4j               | http://logging.apache.org/index.html <br/>License: Apache License 2.0 (http://www.apache.org/licenses/LICENSE-2.0.txt) |
| Oracle JDBC Driver  | http://www.oracle.com <br>License: Oracle Free Use Terms and Conditions (https://www.oracle.com/downloads/licenses/oracle-free-license.html) |

## 4. Packages

| Archive Name                             |
| ---------------------------------------- |
| dataCompJ7.2.zip<br/>dataCompJ7.2.tar.gz |

## 5. Downloads

### 5.1 Packages

http://support.altibase.com/kr/product
