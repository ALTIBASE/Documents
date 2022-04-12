- [Replication Manager Release Notes](#replication-manager-release-notes)
  - [1. 개요](#1-%EA%B0%9C%EC%9A%94)
    - [1.1 시스템 요구사항](#11-%EC%8B%9C%EC%8A%A4%ED%85%9C-%EC%9A%94%EA%B5%AC%EC%82%AC%ED%95%AD)
  - [2. 릴리즈 정보](#2-%EB%A6%B4%EB%A6%AC%EC%A6%88-%EC%A0%95%EB%B3%B4)
    - [2.1 버전](#21-%EB%B2%84%EC%A0%84)
    - [2.2 새로운 기능](#22-%EC%83%88%EB%A1%9C%EC%9A%B4-%EA%B8%B0%EB%8A%A5)
    - [2.3  수정된 버그](#23--%EC%88%98%EC%A0%95%EB%90%9C-%EB%B2%84%EA%B7%B8)
    - [2.4 프로퍼티](#24-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [2.5 에러 메시지](#25-%EC%97%90%EB%9F%AC-%EB%A9%94%EC%8B%9C%EC%A7%80)
  - [3. 오픈소스 라이브러리 / 로열티 프리 이미지](#3-%EC%98%A4%ED%94%88%EC%86%8C%EC%8A%A4-%EB%9D%BC%EC%9D%B4%EB%B8%8C%EB%9F%AC%EB%A6%AC--%EB%A1%9C%EC%97%B4%ED%8B%B0-%ED%94%84%EB%A6%AC-%EC%9D%B4%EB%AF%B8%EC%A7%80)
  - [4. 패키지](#4-%ED%8C%A8%ED%82%A4%EC%A7%80)
  - [5. 다운로드](#5-%EB%8B%A4%EC%9A%B4%EB%A1%9C%EB%93%9C)
    - [5.1 패키지](#51-%ED%8C%A8%ED%82%A4%EC%A7%80)
    - [5.2 매뉴얼](#52-%EB%A7%A4%EB%89%B4%EC%96%BC)
    - [5.3 설치](#53-%EC%84%A4%EC%B9%98)



Replication Manager Release Notes
===============================

**(April 6, 2022)**

## 1. 개요
Replication Manager는 Altibase의 이중화 객체를 편리하게 관리하기 위한 GUI 툴이다.

### 1.1 시스템 요구사항

#### 하드웨어 최소 사양

* 프로세스: 800 MHz Pentium III 이상
* 메모리: 512 MB 이상
* 디스크: 50 MB 이상 여유공간 (JRE 제외)
* 화면 해상도 : 1024 * 768 픽셀 이상

#### 소프트웨어 요구사항

- Java Development Kit (JDK) 또는 Java Runtime Environment (JRE) 6 이상

#### 지원하는 OS 및 플랫폼

| OS      | CPU  | Windows System | Bit (Client) | JRE         |
| :------ | :----: | :-------------: | :------------: | :-----------: |
| Windows | x86  | Win32          | 32 bit       | Java 6 이상 |
| LINUX   | x86  | GTK            | 32 bit       | Java 6 이상 |

#### 호환 가능한 알티베이스 버전

- Altibase 4.3.9 이상 버전


## 2. 릴리즈 정보

### 2.1 버전

- 1.3

### 2.2 새로운 기능

|    PK     |                          SYNOPSIS                           |
| ------- | --------------------------------------------------------- |
| BUG-47926 | Create full-mesh replications를 쉽게 할 수 있는 기능을 제공해야 합니다. |
| BUG-47927 | 새로 추가되는 DB를 full-mesh 이중화 객체에 손쉽게 추가할 수 있어야 합니다. |
| BUG-49483 | ReplicationManager Embedded help를 github 링크로 대체 |

### 2.3  수정된 버그

| PK        | SYNOPSIS                                                     |
| --------- | ------------------------------------------------------------ |
| BUG-46876 | 하나의 파티션 테이블이 여러 개로 표현됩니다.                 |
| BUG-49500 | log4j CVE-2021-44832 보안 이슈로 로깅시스템을 JUL (java.util.logging)로 변경 |

### 2.4 프로퍼티

### 2.5 에러 메시지

## 3. 오픈소스 라이브러리 / 로열티 프리 이미지

Replication Manager는 아래의 오픈소스 라이브러리와 로열티 프리 이미지에 기반한다. 

- 오픈소스 라이브러리

| Library           | Open Source License                                          |
| ----------------- | ------------------------------------------------------------ |
| balcosqlformatter | Homepage: http://www.igapyon.jp/blanco/blancosqlformatter.html <br/>License: LGPL (http://www.gnu.org/licenses/lgpl-3.0.txt) |
| Eclipse           | Homepage: http://www.eclipse.org <br/>License: Eclipse Public License (http://www.eclipse.org/legal/epl-v10.html) |
| JDOM              | Homepage: http://www.jfree.org/jfreechart/) <br/>License: LGPL (http://www.gnu.org/licenses/lgpl-3.0.txt) |
| JFreeChart        | Homepage: http://www.jfree.org/jfreechart/) <br/>License: LGPL (http://www.gnu.org/licenses/lgpl-3.0.txt) |
| SLF4J             | Homepage: https://www.slf4j.org/<br/>License: MIT license (https://www.slf4j.org/license.html) |

- 로열티 프리 이미지


| Library                   | Royalty-Free Images                        |
| ------------------------- | ------------------------------------------ |
| asp.net_commercial_free2  | Homepage: www.asp.net                      |
| www.famfamfam.com         | Homepage: www.famfamfam.com                |
| fatcow-hosting-icons-2400 | Homepage: http://www.fatcow.com/free-icons |

## 4. 패키지

| OS      | Archive Name                           |
| ------- | -------------------------------------- |
| Windows | ReplicationManager-win32.win32.x86.zip |
| Linux   | ReplicationManager-linux.gtk.x86.zip   |

## 5. 다운로드

### 5.1 패키지

<http://support.altibase.com>

### 5.2 매뉴얼

[Replication Manager User's Manual.md](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Tools/eng/Replication%20Manager%20User's%20Manual.md)

### 5.3 설치

[Replication Manager User's Manual.md](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Tools/eng/Replication%20Manager%20User's%20Manual.md)을 참고한다.