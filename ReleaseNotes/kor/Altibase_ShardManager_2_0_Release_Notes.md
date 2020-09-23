

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Altibase Shard Manager 2.0 Release Notes](#altibase-shard-manager-20-release-notes)
  - [1. Abstract](#1-abstract)
    - [1.1 System Requirements](#11-system-requirements)
    - [1.2 Supported Operating Systems and Platforms](#12-supported-operating-systems-and-platforms)
  - [2. Release Information](#2-release-information)
    - [2.1 Altibase Shard Manager 2.0](#21-altibase-shard-manager-20)
    - [2.2 Changes](#22-changes)
    - [2.3 Open Source Libraries](#23-open-source-libraries-royalty-free-images-used)
    - [2.4 Packages](#24-packages)
    - [2.5 Downloads](#25-downloads)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

</br>

</br>

</br>

Altibase Shard Manager 2.0 Release Notes
===============================

**(April 9, 2018)**

## 1. Abstract

### 1.1 System Requirements

#### Minimum Hardware

* Computer processor: 800MHz Pentium III or better
* Computer memory: 512 MB or more
* Computer disk : 90MB or more free space
* Screen resolution : 1024 * 768 pixels or higher

### 1.2 Supported Operating Systems and Platforms

| OS     | CPU    | Windows System | Bit (Client) | JRE              |
| ------ | ------ | -------------- | ------------ | ---------------- |
| LINUX  | x86_64 | GTK            | 64bit        | Java 5 or higher |
| WINDOW | x86    | Win32          | 32bit        | Java 5 or higher |

## 2. Release Information

### 2.1 Altibase Shard Manager 2.0

Shard Manager is a graphical tool which enables users to manage multiple databases and shard objects for Altibase Sharding. Typically, the task of manually administrating them are complicated, time-consuming, and prone to human error. In order to relieve such burden, Shard Manager can be utilized providing qualified help for users to efficiently perform their work with only a few mouse clicks while visualizing all of them on the same screen.

#### 	2.1.1 New Features

**NONE**

#### 2.1.2  Bug-Fixes

| PK        | SYNOPSIS                                    |
| :---------: | :-------------------------------------------- |
| BUG-45116 | Need to support the Linux platform |
| BUG-45129 | Failed to parse a single line comment in the Query View. |
| BUG-45130 | Need to support specifying properties for database connection. |
| BUG-45234 | Failed to execute truncating a shard table. |
| BUG-45329 | Failed to register a table as a shard object when it has Timestamp constraint. |
| BUG-34342 | Need to display the output from PSM execution using JDBC callback. |
| BUG-45780 | Need to update querying record count of shard table according to the changes of shard 2.0. |
| BUG-45831 | Need to support the shard keyword 'NODE'. |
| BUG-45839 | Need to support shard table data rebuild. |
| BUG-45855 | Need to ship the JDBC driver file in the package. |
| BUG-45908 | Need to support executing the selected statement in Query View. |

### 2.2 Changes

Listed below are added/updated/deleted functions and their explanations for Shard Manager.

#### 2.2.1 Version Updates

Shard Manager Version

| Altibase Shard Manager Version |
| :----------------------------: |
|              2.0               |



#### 2.2.2 Database Compatibility

##### Altibase Compatibility

- Altibase database: Altibase 7.1.0.1.2 (Altibase Sharding 2.0)

- JDBC driver version: Altibase 7.1.0.1.2

  that comes with Shard Manager

#### 2.2.3 Properties

NONE

#### 2.2.4 Error Messages

NONE

### 2.3 Open Source Libraries /Royalty-Free Images Used

Shard Manager is based on the following Open Source Libraries and Royalty-Free Images. The
licenses are distributed in a text file format along with Shard Manager.

| Library              | Open Source License                                          |
| -------------------- | ------------------------------------------------------------ |
| Eclipse              | Homepage: http://www.eclipse.org <br/>License: Eclipse Public License (http://www.eclipse.org/legal/epl-v10.html) |
| Apache Commons Codec | Homepage: http://commons.apache.org/codec/<br/>License: Apache License 2.0<br/>(http://www.apache.org/licenses/LICENSE-2.0.txt) |
| Apache Commons Lang  | Homepage: http://commons.apache.org/proper/commons-lang/<br/>License: Apache License 2.0<br/>(http://www.apache.org/licenses/LICENSE-2.0.txt) |
| Apache Common IO     | Homepage: http://commons.apache.org/proper/commons-io/<br/>License: Apache License 2.0<br/>(http://www.apache.org/licenses/LICENSE-2.0.txt) |
| Log4j                | Homepage: http://logging.apache.org/index.html<br/>License: Apache License 2.0<br/>(http://www.apache.org/licenses/LICENSE-2.0.txt) |
| JDOM                 | Homepage: http://www.jdom.org/<br/>License: Apache-style Open Source License<br/>(http://www.jdom.org/docs/faq.html#a0030) |

| Library                      | Royalty-Free Images                                 |
| ---------------------------- | --------------------------------------------------- |
| 16x16 Free Application Icons | Homepage: http://www.aha-soft.com                   |
| asp.net_commercial_free2     | Homepage: www.asp.net                               |
| Eclipse                      | Homepage: www.eclipse.org                           |
| www.famfamfam.com            | Homepage: www.famfamfam.com                         |
| fatcow-hosting-icons-2400    | Homepage: http://www.fatcow.com/free-icons          |
| fugue-icons-3.2.3-src        | Homepage: http://code.google.com/p/fugue-icons-src/ |
| SqlExplorer                  | Homepage: http://eclipsesql.sourceforge.net/        |

### 2.4 Packages

| OS      | CPU    | Archive Name                      |
| ------- | ------ | --------------------------------- |
| Linux   | x86_64 | ShardManager-linux.gtk.x86_64.zip |
| Windows | x86    | ShardManager-win32.win32.x86.zip  |

### 2.5 Downloads

#### 2.5.1 Packages

<http://support.altibase.com/kr/product>

#### 2.5.2 Manual

https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Sharding.md#7-shard-manager

#### 2.5.3 Installation

Please refer to the Altibase Sharding Manual.
