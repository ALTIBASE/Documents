- [Altibase Replication Manager 1.3 Release Notes](#altibase-replication-manager-13-release-notes)
  - [1. Abstract](#1-abstract)
    - [1.1 System Requirements](#11-system-requirements)
    - [1.2 Supported Operating Systems and Platforms](#12-supported-operating-systems-and-platforms)
  - [2. Release Information](#2-release-information)
    - [2.1 Altibase Replication Manager 1.3](#21-altibase-replication-manager-13)
    - [2.2 Changes](#22-changes)
    - [2.3 Open Source Libraries](#23-open-source-libraries)
    - [2.4 Packages](#24-packages)
    - [2.5 Downloads](#25-downloads)



Altibase Replication Manager 1.3 Release Notes
===============================

**(April 6, 2022)**

## 1. Abstract

### 1.1 System Requirements

#### Minimum Hardware

* CPU: 800 MHz Pentium III or better
* Main memory: 512 MB or more
* Disk : 50 MB or free space(Except JRE)
* Screen resolution : 1024 * 768 pixels or higher

### 1.2 Supported Operating Systems and Platforms

| OS      | CPU  | Windows System | Bit (Client) | JRE              |
| ------- | ---- | -------------- | ------------ | ---------------- |
| Windows | x86  | Win32          | 32 bit       | Java 6 or higher |
| LINUX   | x86  | GTK            | 32 bit       | Java 6 or higher |

## 2. Release Information

### 2.1 Altibase Replication Manager 1.3

Replication Manager is a graphical tool for managing replication on Altibase more easily and quickly. 

#### 2.1.1 New Features

|    PK     |                          SYNOPSIS                           |
| ------- | --------------------------------------------------------- |
| BUG-47926 | Need to provide a function to create full-mesh replications. |
| BUG-47927 | Need to easily add a newly added DB to the full-mesh replication object. |
| BUG-49483 | Need to replace Embedded help with github manual link |

#### 2.1.2  Bug-Fixes

| PK        | SYNOPSIS                                                     |
| --------- | ------------------------------------------------------------ |
| BUG-46876 | A partitioned table represented as the number of partitions. |
| BUG-49500 | Logging system has been replaced from log4j to JUL (java.util.logging) <br />due to CVE-2021-44832 security issue |

### 2.2 Changes

#### 2.2.1 Version Update

Replication Manager Version

| Altibase Replication Manager Version |
| :----------------------------------: |
|                 1.3                  |

#### 2.2.2 Compatibility

##### Altibase Compatibility

- Replication Manager : Altibase 4.3.9 or higher

#### 2.2.3 Properties

NONE

#### 2.2.4 Error Messages

NONE

### 2.3 Open Source Libraries

Replication Manager is based on the following Open Source Libraries and Royalty-Free Images. 

- Open Source Libraries

| Library           | Open Source License                                          |
| ----------------- | ------------------------------------------------------------ |
| balcosqlformatter | Homepage: http://www.igapyon.jp/blanco/blancosqlformatter.html </br>License: LGPL (http://www.gnu.org/licenses/lgpl-3.0.txt) |
| Eclipse           | Homepage: http://www.eclipse.org <br/>License: Eclipse Public License (http://www.eclipse.org/legal/epl-v10.html) |
| JDOM              | Homepage: http://www.jfree.org/jfreechart/) <br/>License: LGPL (http://www.gnu.org/licenses/lgpl-3.0.txt) |
| JFreeChart        | Homepage: http://www.jfree.org/jfreechart/) <br/>License: LGPL (http://www.gnu.org/licenses/lgpl-3.0.txt) |
| SLF4J             | Homepage: https://www.slf4j.org/<br/>License: MIT license (https://www.slf4j.org/license.html) |

- Royalty-Free Images

| Library                   | Royalty-Free Images                        |
| ------------------------- | ------------------------------------------ |
| asp.net_commercial_free2  | Homepage: www.asp.net                      |
| www.famfamfam.com         | Homepage: www.famfamfam.com                |
| fatcow-hosting-icons-2400 | Homepage: http://www.fatcow.com/free-icons |

### 2.4 Packages

| OS      | Archive Name                           |
| ------- | -------------------------------------- |
| Windows | ReplicationManager-win32.win32.x86.zip |
| Linux   | ReplicationManager-linux.gtk.x86.zip   |

### 2.5 Downloads

#### 2.5.1 Packages

<http://support.altibase.com>

#### 2.5.2 Manual

[Replication Manager User's Manual.md](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Tools/eng/Replication%20Manager%20User's%20Manual.md)

#### 2.5.3 Installation

Please refer to the Replication Manager User's Manual.