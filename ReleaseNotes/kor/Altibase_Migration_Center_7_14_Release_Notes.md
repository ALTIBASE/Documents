# Altibase Migration Center 7.14 Release Notes

#### Release 7.14 (November 1, 2024)

Altibase® Tool & Utilities

<br><br><br><br><br><br><!-- PDF 변환을 위한 여백입니다. --> 





































<!-- PDF 변환을 위한 여백입니다. --> 

<div align="left">
    <img src="media/common/e5cfb3761673686d093a3b00c062fe7a.png">
</div>
<br><br><!-- PDF 변환을 위한 여백입니다. --> 











































<!-- PDF 변환을 위한 여백입니다. --> 

<pre>
Altibase Release Notes Migration Center 
Release 7.14
Copyright ⓒ 2001~2024 Altibase Corp. All Rights Reserved.<br>
본 문서의 저작권은 ㈜알티베이스에 있습니다. 이 문서에 대하여 당사의 동의없이 무단으로 복제 또는 전용할 수 없습니다.<br>
<b>㈜알티베이스</b>
08378 서울시 구로구 디지털로 306 대륭포스트타워Ⅱ 10층
전화 : 02-2082-1114
팩스 : 02-2082-1099
고객서비스포털 : <a href='http://support.altibase.com'>http://support.altibase.com</a>
홈페이지      : <a href='http://www.altibase.com/'>http://www.altibase.com</a></pre>

<br>

<div style="page-break-after: always; visibility: hidden"> \pagebreak </div>

# 목차

- [1. 개요](#1-개요)
  - [1.1 Altibase Migration Center](#11-altibase-migration-center)
  - [1.2 시스템 요구사항](#12-시스템-요구사항)
  - [1.3 호환 가능한 데이터베이스 시스템](#13-호환-가능한-데이터베이스-시스템)
- [2. 릴리즈 정보](#2-릴리즈-정보)
  - [2.1 새로운 기능](#21-새로운-기능)
  - [2.2 수정된 버그](#22-수정된-버그)
- [3. 사용된 오픈소스 라이브러리 / 로열티 프리 이미지](#3-사용된-오픈소스-라이브러리--로열티-프리-이미지)
- [4. 패키지](#4-패키지)
- [5. 다운로드](#5-다운로드)

<br/>

# 1. 개요

## 1.1 Altibase Migration Center

Migration Center는 데이터베이스 사이에 일반적으로 호환되는 데이터베이스 객체와 데이터를 직접 또는 간접적으로 복사하는 데이터베이스 마이그레이션(migration) 도구이다. 대부분의 데이터베이스는 국제 표준을 준수하지만, 어떤 데이터베이스라도 수동 데이터베이스 마이그레이션이 불가피한 경우가 있다. 일반적으로 데이터베이스 마이그레이션 작업을 수동으로 직접 하는 것은 복잡하고 시간이 많이 소모되며, 사람이 하는 일이기에 실수가 잦을 수 있다. Migration Center는 사용자가 그래픽 사용자 인터페이스(GUI) 모드에서 몇 번의 마우스 클릭만으로도 데이터베이스 마이그레이션 작업을 수행할 수 있게 도와준다. 또한, 명령어 인터페이스(CLI) 모드도 지원한다.

<br/>

## 1.2 시스템 요구사항

### 하드웨어 최소 사양

Migration Center센터를 실행하기 위한 하드웨어의 최소 사양은 아래와 같다. 

|                 |        GUI 모드         | CLI 모드 |
| --------------- | :---------------------: | :------: |
| **프로세서**    | 800MHz Pentium III 이상 |   좌동   |
| **메모리**      |       512 MB 이상       |   좌동   |
| **디스크**      |   150MB 이상 여유공간   |   좌동   |
| **화면 해상도** |  1024 * 800 픽셀 이상   |    -     |

### 지원 OS

Migration Center는 소프트웨어 최소 사양을 만족하면 OS 무관하게 실행할 수 있다. 

### 소프트웨어 최소 사양

Migration Center는 GUI 모드의 경우 스윙(Swing)을 사용하는 순수 자바 애플리케이션이다. 이는 사용자의 하드웨어 및 운영 체제에 상관없이 대부분 독립적으로 실행되지만, 오라클 자바 런타임 환경(JRE)에 의존적이다. 오라클 또는 IBM Java 8 이상의 JRE를 설치할 것을 권장한다. GUI 모드로 Migration Center를 실행하려면, 사용자의 환경이 자바 스윙을 지원해야 한다.

| Mode | JRE                      | OS Graphic Library |
| ---- | ------------------------ | :----------------: |
| GUI  | Sun 또는 IBM Java 8 이상 |        필수        |
| CLI  | Sun 또는 IBM Java 8 이상 |     필수 아님      |

<br/>

## 1.3 호환 가능한 데이터베이스 시스템

Migration Center 7.14 으로 마이그레이션 할 수 있는 데이터베이스 시스템 종류와 버전을 소개한다.

| **원본 데이터베이스 종류 및 버전**                           | **대상 데이터베이스 버전** |
| :----------------------------------------------------------- | :------------------------- |
| Altibase 4.3.9 이상<br />CUBRID 8.4.1 ~ 9.3.5 (ISO-8859-1, UTF-8 charset) <br/>Informix 11.50 <br />Microsoft SQL Server 2005 ~ 2012<br />Oracle Database 9i ~ 11g <br />Oracle MySQL 5.0 ~ 5.7 <br />Oracle TimesTen 7.0, 11.2 <br />Tibero 4 SP1 ~ 6<br/>PostgreSQL 9.5.3 | Altibase 6.5.1 이상        |

<br/>

# 2. 릴리즈 정보

Migration Center 7.14 의 새로운 기능과 수정된 버그 및 변경 사항에 관한 내용이다.

## 2.1 새로운 기능

### BUG-50652 Reconcile 단계에서 입력한 Select 조건을 Run 단계에서 편집할 수 있도록 허용합니다.

원본 데이터베이스에서 데이터를 추출할 때, 특정 조건에 맞는 데이터만 선택적으로 추출하여 마이그레이션 할 수 있는 기능이 추가되었다. Select 조건은 Reconcile 단계 중 "Select Editing"에서 수정하거나, Reconcile 단계 완료 후 사용자가 직접 TableCondition.properties 파일에서 편집할 수 있다.

<br/>

## 2.2 수정된 버그
### BUG-50263 데이터 매핑 타입 변경: Oracle, TimesTen, Tibero BINARY_DOUBLE 타입의 기본 데이터 매핑 타입을 Altibase VARCHAR 타입에서 DOUBLE 타입으로 변경합니다.

Oracle, TimesTen, Tibero의 BINARY_DOUBLE 타입은 Altibase DOUBLE 타입과 호환되므로 기본 데이터 매핑 타입을 변경한다. 다만 Oracle, TimesTen, Tibero은 특수한 값인 NaN(Not a Number)과 INF(Infinity)를 지원하는 반면, Altibase는 지원하지 않는다. 이 값의 경우 데이터 손실이 발생할 수 있다.

### BUG-50821 Migration Center 대상 데이터베이스에서 Oracle을 제거합니다.

Migration Center가 지원하는 Altibase to Oracle 데이터 마이그레이션 기능을 제거한다.

### BUG-50827 데이터 매핑 타입 변경: TimesTen Binary 타입의 기본 데이터 매핑 타입을 Altibase BLOB 타입에서 BYTE 타입으로 변경합니다.

TimesTen의 Binary 타입의 기본 데이터 매핑 타입을 Altibase BLOB 타입에서 BYTE 타입으로 변경한다.

### BUG-51034 Altibase 대상으로 마이그레이션 수행 시 Empty string 데이터 변환 기능 옵션을 제공합니다.

특정 DBMS에서 Altibase로 마이그레이션 할 때, Empty String 값이면 정상 동작 하지 않고 제거되는 경우가 있다. Empty String 데이터를 Altibase에 적합한 데이터로 변환하는 기능을 Migration Option에서 제공한다.

### BUG-51035 Altibase 대상으로 마이그레이션 수행 시 Not Null & Default '' 컬럼 변환 기능 옵션을 제공합니다.

특정 DBMS에서 Altibase로 마이그레이션 할 때, Default ''(Empty String) Not Null 컬럼일 경우 정상 동작하지 않고 제거된다. Not Null & Default '' 컬럼 변환 시 Altibase에 적합한 DDL을 구성할 수 있는 옵션을 제공한다.

### BUG-51075 Migration Center UI 개선: 사용성 향상을 위해 옵션 창에 스크롤바를 추가하고 창 높이를 조정합니다.

Migration Center에 지속적으로 옵션이 추가되면서 기존 Option 창이 너무 길어져 사용에 불편함을 줄 우려가 있다. Option 창에 스크롤바를 추가하고 Option 창 높이를 수정한다.

### BUG-51076 Migration Center UI 개선: 메인 창의 분리바를 사용자가 조정 가능하도록 변경합니다.

특정 해상도에서 Migration Center 메인 창 왼쪽 Project 트리와 DB Properties 창이 보이지 않는 경우가 있다. 왼쪽 창은 사용자가 임의로 크기 조절이 불가능하여 사용자가 이 경우에 Migration Center를 정상적으로 사용할 수 없다. 메인 창 왼쪽 Project 트리와 DB Properties 창을 사용자가 크기를 조정가능하도록 수정한다.

<br/>

# 3. 사용된 오픈소스 라이브러리 / 로열티 프리 이미지

#### 오픈소스 라이브러리

Migration Center는 아래의 오픈소스 라이브러리에 기반한다. 각 오픈소스 라이브러리의 라이선스는 doc/license 폴더 아래에 텍스트 파일 형식으로 제공한다. Java Help System은 GPL linking exception으로 라이선스 예외사항에 해당되어 라이선스 파일을 제공하지 않는다.

| Library                                                      | Open Source License                                          |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
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

#### 로열티 프리 이미지

| Library                  | Royalty-Free Images                            |
| :----------------------- | :--------------------------------------------- |
| org.eclipse.datatools    | [www.eclipse.org](http://www.eclipse.org/)     |
| asp.net_commercial_free2 | [www.asp.net](http://www.asp.net/)             |
| fugue-icons-3.2.3-src    | http://code.google.com/p/fugue-icons-src/      |
| Silk Icons 1.3           | [www.famfamfam.com](http://www.famfamfam.com/) |

<br/>

# 4. 패키지

Migration Center 설치 패키지는 두 가지 형태(.zip, .gz) 파일로 제공한다.

- MigrationCenter7.14.zip

- MigrationCenter7.14.tar.gz

<br/>

# 5. 다운로드

#### 패키지

[http://support.altibase.com](http://support.altibase.com/)

#### 매뉴얼

[Migration Center User's Manual](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Tools/kor/Migration%20Center%20User's%20Manual.md)

#### 설치

Migration Center User's Manual을 참고한다.
