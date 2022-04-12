- [Replication Manager Release Notes](#replication-manager-release-notes)
  - [1. Abstract](#1-abstract)
    - [1.1 System Requirements](#11-system-requirements)
  - [2. Release Information](#2-release-information)
    - [2.1 Version](#21-version)
    - [2.2 New Features](#22-new-features)
    - [2.3 Bug Fixed](#23-bug-fixed)
    - [2.4 Properties](#24-properties)
    - [2.5 Error Messages](#25-error-messages)
  - [3. Open Source Libraries/Royalty-Free Images](#3-open-source-librariesroyalty-free-images)
  - [4. Packages](#4-packages)
  - [5. Downloads](#5-downloads)
    - [5.1 Packages](#51-packages)
    - [5.2 Manual](#52-manual)
    - [5.3 Installation](#53-installation)



Replication Manager Release Notes
===============================

**(April 6, 2022)**

## 1. Abstract

### 1.1 System Requirements

#### Hardware Requirements

* CPU: 800 MHz Pentium III or better
* Main memory: 512 MB or more
* Disk : 50 MB or free space(Except JRE)
* Screen resolution : 1024 * 768 pixels or higher

#### Software Requirements

- Java Development Kit (JDK) 또는 Java Runtime Environment (JRE) 6 or higher

#### Supported Operating Systems and Platforms

| OS      | CPU  | Windows System | Bit (Client) | JRE              |
| :------ | :----: | :-------------: | :------------: | :-----------: |
| Windows | x86  | Win32          | 32 bit       | Java 6 or higher |
| LINUX   | x86  | GTK            | 32 bit       | Java 6 or higher |

#### Compatible Altibase version

- Altibase 4.3.9 or higher

## 2. Release Information

### 2.1 Version

- 1.3

Replication Manager is a graphical tool for managing replication on Altibase more easily and quickly. 

### 2.2 New Features

|    PK     |                          SYNOPSIS                           |
| ------- | --------------------------------------------------------- |
| BUG-47926 | Need to provide a function to create full-mesh replications. |
| BUG-47927 | Need to easily add a newly added DB to the full-mesh replication object. |
| BUG-49483 | Need to replace Embedded help with github manual link |

### 2.3 Bug Fixed

| PK        | SYNOPSIS                                                     |
| --------- | ------------------------------------------------------------ |
| BUG-46876 | A partitioned table represented as the number of partitions. |
| BUG-49500 | Logging system has been replaced from log4j to JUL (java.util.logging) <br />due to CVE-2021-44832 security issue |

### 2.4 Properties

### 2.5 Error Messages

## 3. Open Source Libraries/Royalty-Free Images

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

## 4. Packages

| OS      | Archive Name                           |
| ------- | -------------------------------------- |
| Windows | ReplicationManager-win32.win32.x86.zip |
| Linux   | ReplicationManager-linux.gtk.x86.zip   |

## 5. Downloads

### 5.1 Packages

<http://support.altibase.com>

### 5.2 Manual

[Replication Manager User's Manual.md](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Tools/eng/Replication%20Manager%20User's%20Manual.md)

### 5.3 Installation

Please refer to the [Replication Manager User's Manual.md](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Tools/eng/Replication%20Manager%20User's%20Manual.md)

