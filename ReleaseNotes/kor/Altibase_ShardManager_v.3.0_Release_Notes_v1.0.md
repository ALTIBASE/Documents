

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Altibase Shard Manager Release Notes](#altibase-shard-manager-release-notes)
  - [1. Abstract](#1-abstract)
    - [1.1 System Requirements](#11-system-requirements)
    - [1.2 Supported Operating Systems and Platforms](#12-supported-operating-systems-and-platforms)
  - [2. Release Information](#2-release-information)
    - [2.1 Altibase Shard Manager](#21-altibase-shard-manager)
    - [2.2 Changes](#22-changes)
    - [2.3 Open Source Libraries /Royalty-Free Images Used](#23-open-source-libraries-royalty-free-images-used)
    - [2.4 Packages](#24-packages)
    - [2.5 Downloads](#25-downloads)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

<br/>

<br/>

<br/>

Altibase Shard Manager Release Notes
===============================

**(Jan. 10, 2020)**

## 1. Abstract

### 1.1 System Requirements

#### Minimum Hardware

* Computer processor: 800MHz Pentium III or better
* Computer memory: 512 MB or more
* Computer disk : 120MB or more free space
* Screen resolution : 1024 * 768 pixels or higher

### 1.2 Supported Operating Systems and Platforms

| OS     | CPU    | Windows System | Bit (Client) | JRE              |
| ------ | ------ | -------------- | ------------ | ---------------- |
| LINUX  | x86_64 | GTK            | 64bit        | Java 6 or higher |
| WINDOW | x86    | Win32          | 32bit        | Java 6 or higher |

## 2. Release Information

### 2.1 Altibase Shard Manager

Shard Manager is a graphical tool which enables users to manage multiple databases and shard objects for Altibase Sharding. Typically, the task of manually administrating them are complicated, time-consuming, and prone to human error. In order to relieve such burden, Shard Manager can be utilized providing qualified help for users to efficiently perform their work with only a few mouse clicks while visualizing all of them on the same screen.

#### 	2.1.1 New Features

- Supports shard table resharding
- Provides report file: shard node configuration, shard object schema and shard table record count
- Provides Command Line Interface (CLI) including Graphical User Interface (GUI)

#### 2.1.2  Bug-Fixes

| PK        | SYNOPSIS                                    |
| :---------: | :-------------------------------------------- |
| BUG-47116 | In order to enhance count query performance, need to use shard view |
| BUG-47114 | Need to check that the same DB is not already registered when registering a new node |
| BUG-47138 | Need to provide a way to input replication address separately from DB address |
| BUG-47146 | Add new node continues to fail due to previous add node fail |
| BUG-47153 | Need to provide a way to set the Sync parallel option to enhance resharding performance |
| BUG-47147 | Resharding must be parallel |
| BUG-47156 | "Test" button is not be activated even if the input values are filled in the specific order on the Add Node screen |
| BUG-47179 | RpIp is applied incorrectly when configuring Shard Manager by reading ShardDatabase.xml |
| BUG-47181 | Need to remove alternate DB from node when alternate DB shutdown unexpectedly |
| BUG-47189 | Clone table resharding should be managed by Shard Manager instead of shard procedure |
| BUG-47191 | NEXT button may not be activated after shard database creation |
| BUG-47184 | Shard manager needs logic to avoid distributed deadlock |
| BUG-47185 | Need to make sure database has the properties for sharding when connecting to it |
| BUG-47103 | Incorrect local_meta_info_ is allocated when adding a new node. |
| BUG-47304 | To improve usability, need to remove the dependency on external procedures such as utl_shard_online_rebuild.sql |
| BUG-47317 | Need to provide wizard for "Create Hash Table" |
| BUG-47417 | When adding a new node or Alternate DB, need to copy shard object schema from old node |
| BUG-47418 | Need to check the shard database has the dbms_meta package when connecting to it |
| BUG-47353 | Need to provide a report on the shard object and its configuration |
| BUG-47157 | Need to test alternate DB connection if required |
| BUG-47440 | Need to unset multiple shard objects at once |
| BUG-47444 | [CLI] When resharding, need to enter partition name only instead of partition name and partition max |
| BUG-47462 | [CLI] Requires resharding functionality for Clone, Solo table |
| BUG-47463 | [CLI] Requires provide Add/remove node functionality |
| BUG-47464 | [CLI] Requires Set / unset shard object functionality |
| BUG-47465 | [CLI] Requires shard report functionality |
| BUG-47467 | [CLI] Requires Create/Load/Remove ShardDb functionality |
| BUG-47610 | When removing a shard database, need to drop the DB object registered as a shard object |

### 2.2 Changes

Listed below are added/updated/deleted functions and their explanations for Shard Manager.

#### 2.2.1 Version Updates

Shard Manager Version

| Altibase Shard Manager Version |
| :----------------------------: |
|              2.0               |



#### 2.2.2 Database Compatibility

##### Altibase Compatibility

- Altibase database: Altibase 7.1.0.2.3 (Altibase Sharding 2.2.1)

#### 2.2.3 Properties

NONE

#### 2.2.4 Error Messages

NONE

### 2.3 Open Source Libraries /Royalty-Free Images Used

Shard Manager is based on the following Open Source Libraries and Royalty-Free Images. The licenses are distributed in a text file format along with Shard Manager.

| Library              | Open Source License                                          |
| -------------------- | ------------------------------------------------------------ |
| Eclipse              | Homepage: http://www.eclipse.org <br/>License: Eclipse Public License (http://www.eclipse.org/legal/epl-v10.html) |
| Apache Commons Codec | Homepage: http://commons.apache.org/codec/<br/>License: Apache License 2.0<br/>(http://www.apache.org/licenses/LICENSE-2.0.txt) |
| Apache Commons Lang  | Homepage: http://commons.apache.org/proper/commons-lang/<br/>License: Apache License 2.0<br/>(http://www.apache.org/licenses/LICENSE-2.0.txt) |
| Apache Commons IO    | Homepage: http://commons.apache.org/proper/commons-io/<br/>License: Apache License 2.0<br/>(http://www.apache.org/licenses/LICENSE-2.0.txt) |
| Apache Commons CLI   | Homepage: https://commons.apache.org/proper/commons-cli/<br/>License: Apache License 2.0<br/>(http://www.apache.org/licenses/LICENSE-2.0.txt) |
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
