Replication Manager Release Notes
===============================

#### Release 1.4 (August 31, 2023)

Alitbase® Tools & Utilities

<br><br><br><br><br><br>
<!-- PDF 변환을 위한 여백입니다. --> 





































<!-- PDF 변환을 위한 여백입니다. --> 

<div align="left">
    <img src="media/common/e5cfb3761673686d093a3b00c062fe7a.png">
</div>
<br><br><!-- PDF 변환을 위한 여백입니다. --> 









































<!-- PDF 변환을 위한 여백입니다. --> 

<pre>
Altibase Release Notes Replication Manager
Release 1.3
Copyright ⓒ 2001~2023 Altibase Corp. All Rights Reserved.<br>
본 문서의 저작권은 ㈜알티베이스에 있습니다. 이 문서에 대하여 당사의 동의없이 무단으로 복제 또는 전용할 수 없습니다.<br>
<b>㈜알티베이스</b>
08378 서울시 구로구 디지털로 306 대륭포스트타워Ⅱ 10층
전화 : 02-2082-1114
팩스 : 02-2082-1099
고객서비스포털 : <a href='http://support.altibase.com'>http://support.altibase.com</a>
홈페이지      : <a href='http://www.altibase.com/'>http://www.altibase.com</a></pre>




<br>

# 목차

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

<br>



# 1. 개요
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

<br>

# 2. 릴리즈 정보

### 2.1 버전

- 1.3

### 2.2 새로운 기능

### 2.3  수정된 버그

| PK        | SYNOPSIS                                               |
| --------- | ------------------------------------------------------ |
| BUG-50573 | Replication Manager에 패키징된 JRE를 6 -> 8로 업데이트 |

### 2.4 프로퍼티

### 2.5 에러 메시지

<br>

# 3. 오픈소스 라이브러리 / 로열티 프리 이미지

Replication Manager는 아래의 오픈소스 라이브러리와 로열티 프리 이미지에 기반한다. 

- 오픈소스 라이브러리

| Library           | Open Source License                                          |
| ----------------- | ------------------------------------------------------------ |
| balcosqlformatter | Homepage: http://www.igapyon.jp/blanco/blancosqlformatter.html <br/>License: LGPL (http://www.gnu.org/licenses/lgpl-3.0.txt) |
| Eclipse           | Homepage: http://www.eclipse.org <br/>License: Eclipse Public License (http://www.eclipse.org/legal/epl-v10.html) |
| JDOM              | Homepage: http://www.jdom.org/<br/>License: an Apache-style open source license, with the acknowledgment clause removed (http://www.jdom.org/docs/faq.html#a0030) |
| JFreeChart        | Homepage: http://www.jfree.org/jfreechart/ <br/>License: LGPL (http://www.gnu.org/licenses/lgpl-3.0.txt) |
| SLF4J             | Homepage: https://www.slf4j.org/<br/>License: MIT license (https://www.slf4j.org/license.html) |

- 로열티 프리 이미지


| Library                   | Royalty-Free Images                        |
| ------------------------- | ------------------------------------------ |
| asp.net_commercial_free2  | Homepage: www.asp.net                      |
| www.famfamfam.com         | Homepage: www.famfamfam.com                |
| fatcow-hosting-icons-2400 | Homepage: http://www.fatcow.com/free-icons |

<br>

# 4. 패키지

| OS      | Archive Name                                 |
| ------- | -------------------------------------------- |
| Windows | ReplicationManager_1.4.0-win32.win32.x86.zip |
| Linux   | ReplicationManager_1.4.0-linux.gtk.x86.zip   |

<br>

# 5. 다운로드

### 5.1 패키지

<http://support.altibase.com>

### 5.2 매뉴얼

[Replication Manager User's Manual.md](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Tools/eng/Replication%20Manager%20User's%20Manual.md)

### 5.3 설치

[Replication Manager User's Manual.md](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Tools/eng/Replication%20Manager%20User's%20Manual.md)을 참고한다.