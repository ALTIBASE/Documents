# Altibase Migration Center 7.16 Release Notes

#### Release 7.16 (September 12, 2025)

Altibase® Tools & Utilities

<br><br><br><br><br><br><!-- PDF 변환을 위한 여백입니다. --> 





































<!-- PDF 변환을 위한 여백입니다. --> 

<div align="left">
    <img src="media/common/e5cfb3761673686d093a3b00c062fe7a.png">
</div>
<br><br><!-- PDF 변환을 위한 여백입니다. --> 











































<!-- PDF 변환을 위한 여백입니다. --> 

<pre>
Altibase Release Notes Migration Center 
Release 7.16
Copyright ⓒ 2001~2025 Altibase Corp. All Rights Reserved.<br>
본 문서의 저작권은 ㈜알티베이스에 있습니다. 이 문서에 대하여 당사의 동의없이 무단으로 복제 또는 전용할 수 없습니다.<br>
<b>㈜알티베이스</b>
08378 서울시 구로구 디지털로 306 대륭포스트타워Ⅱ 10층
전화 : 02-2082-1114
팩스 : 02-2082-1099
고객서비스포털 : <a href='http://support.altibase.com'>http://support.altibase.com</a>
홈페이지      : <a href='http://www.altibase.com/'>http://www.altibase.com</a></pre>

<br>

# 목차
- [1. 개요](#1-개요)
  - [1.1 Altibase Migration Center](#11-altibase-migration-center)
  - [1.2 시스템 요구사항](#12-시스템-요구사항)
    - [하드웨어 최소 사양](#하드웨어-최소-사양)
    - [지원 OS](#지원-os)
    - [소프트웨어 최소 사양](#소프트웨어-최소-사양)
  - [1.3 호환 가능한 데이터베이스 시스템](#13-호환-가능한-데이터베이스-시스템)
- [2. 릴리즈 정보](#2-릴리즈-정보)
  - [2.1 새로운 기능](#21-새로운-기능)
  - [2.2 수정된 버그](#22-수정된-버그)
- [3. 사용된 오픈소스 라이브러리 / 로열티 프리 이미지](#3-사용된-오픈소스-라이브러리--로열티-프리-이미지)
      - [오픈소스 라이브러리](#오픈소스-라이브러리)
      - [로열티 프리 이미지](#로열티-프리-이미지)
- [4. 패키지](#4-패키지)
- [5. 다운로드](#5-다운로드)
      - [패키지](#패키지)
      - [매뉴얼](#매뉴얼)
      - [설치](#설치)

<br/>

# 1. 개요

## 1.1 Altibase Migration Center

Migration Center는 데이터베이스 사이에 일반적으로 호환되는 데이터베이스 객체와 데이터를 직접 또는 간접적으로 복사하는 데이터베이스 마이그레이션(migration) 도구이다. 대부분의 데이터베이스는 국제 표준을 준수하지만, 어떤 데이터베이스라도 수동 데이터베이스 마이그레이션이 불가피한 경우가 있다. 일반적으로 데이터베이스 마이그레이션 작업을 수동으로 직접 하는 것은 복잡하고 시간이 많이 소모되며, 사람이 하는 일이기에 실수가 잦을 수 있다. Migration Center는 사용자가 그래픽 사용자 인터페이스(GUI) 모드에서 몇 번의 마우스 클릭만으로도 데이터베이스 마이그레이션 작업을 수행할 수 있게 도와준다. 또한, 명령어 인터페이스(CLI) 모드도 지원한다.

<br/>

## 1.2 시스템 요구사항

### 하드웨어 최소 사양

Migration Center를 실행하기 위한 하드웨어의 최소 사양은 아래와 같다. 

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

Migration Center 7.16 으로 마이그레이션 할 수 있는 데이터베이스 시스템 종류와 버전을 소개한다.

| **원본 데이터베이스 종류 및 버전**                           | **대상 데이터베이스 버전** |
| :----------------------------------------------------------- | :------------------------- |
| Altibase 4.3.9 이상<br />CUBRID 8.4.1 ~ 9.3.5 (ISO-8859-1, UTF-8 charset) <br />Microsoft SQL Server 2005 ~ 2012<br />Oracle Database 10gR2 ~ 21c <br />Oracle MySQL 5.0 ~ 5.7 <br />Oracle TimesTen 11.2 <br />Tibero 4 SP1 ~ 7.2.2<br/>PostgreSQL 9.5.3 | Altibase 6.5.1 이상        |

> [!NOTE]
>
> **지원 중단 데이터베이스 종류 및 버전**
>
> Migration Center7. 16부터는 다음 데이터베이스의 버전은 더 이상 지원되지 않습니다.
>
> - **Oracle**: 9i, 10g Release 1 (10gR1)
> - **TimesTen**: 7
> - **Informix**: 11.50

<br/>

# 2. 릴리즈 정보

Migration Center 7.16 의 새로운 기능과 수정된 버그 및 변경 사항에 관한 내용이다.

## 2.1 새로운 기능

### 원본 데이터베이스로 Oracle 21c 지원
Migration Center의 원본 데이터베이스 Oracle 지원 버전에 Oracle 21c가 추가되었다.

### 데이터 타입으로 JSON 타입 지원
데이터 타입 지원 목록에 JSON 타입이 추가되었다. 대상 데이터베이스인 Altibase가 JSON을 지원하는 버전에서는 JSON으로, 지원하지 않는 경우에는 CLOB 타입으로 매핑되어 마이그레이션된다.

### 이종 문자 집합을 고려한 문자형 칼럼 길이의 보정 계수 옵션 추가
DB to DB 마이그레이션 옵션에 이종 문자 집합을 고려한 문자형 칼럼 길이 보정 계수(Correction Factor)를 지정하는 'Correction Factor for Character Type Conversion' 옵션이 추가되었다. 원본과 대상 데이터베이스의 문자 집합이 서로 다른 경우, 문자형 데이터 타입(CHAR, VARCAHR) 칼럼 길이를 변환하는데 사용되는 보정 계수(Correction Factor)를 지정하는 옵션이다. 기본 값은 자동으로 계산된 값이며 1보다 작은 값으로 지정할 수 없다. 칼럼 단위로 문자 집합이 지정된 경우에는 이 옵션으로 설정한 보정 계수는 적용되지 않는다.

### 마이그레이션 옵션 창에 옵션 값 유효성 검증 추가
마이그레이션 옵션 창에 유효하지 않은 옵션 값 입력 시 해당 옵션 목록과 오류 원인을 알려주는 팝업 창이 추가되었다. 유효하지 않은 옵션 값은 옵션 창에서 유효한 값으로 수정하지 않으면 입력한 옵션 값이 적용되지 않는다.

<br/>

## 2.2 수정된 버그

### BUG-51321 조정 단계 중 "Unacceptable Name" 단계에서 대상이 칼럼인 경우 Use double-quoted identifier 옵션이 적용되지 않는 오류를 수정합니다.
조정 단계 중 "Unacceptable Name" 단계는 대상 데이터베이스의 인용 부호 없는 객체 이름 규칙에 어긋나는 객체를 표시하고 객체 이름을 조정하는 단계이다. 대상 객체가 칼럼인 경우 Use double-quoted identifier 옵션이 적용되지 않는 오류가 있어 이를 수정하였다.

### BUG-51472 PSM 변환기 규칙 추가: 지원하지 않는 DEFAULT COLLATION 절을 제거하기 위한 규칙을 추가합니다.
Altibase는 DDL에서 DEFAULT COLLATION 절을 지원하지 않는다. 지원하지 않는 DEFAULT COLLATION 절 제거를 위해 PSM 변환기 규칙 RULE-11009, RULE-12018, RULE-13016, RULE-14011, RULE-16003을 추가하였다.

### BUG-51650 원본 데이터베이스의 문자 집합이 한 문자 당 바이트 수가 1일 경우 이종 문자 집합 간 문자형 칼럼 길이 자동 보정이 적용되도록 수정합니다.
원본 데이터베이스의 문자 집합이 한 문자 당 바이트 수가 1일 경우에도 이종 문자 집합 간 문자형 칼럼 길이 자동 보정이 적용되도록 수정하였다.

### BUG-51657 Oracle이 지원하는 다국어 문자 집합 지원을 위해 Migration Center 패키지에 Oracle 국제화 지원 보조 라이브러리 orai18n.jar 파일을 추가합니다.
Migration Center에서 Oracle이 지원하는 다국어 문자 집합 지원을 위해 Migration Center 패키지에 Oracle 국제화 지원 보조 라이브러리인 orai18n.jar 파일을 추가하였다.

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

- MigrationCenter7.16.zip

- MigrationCenter7.16.tar.gz

<br/>

# 5. 다운로드

#### 패키지

http://support.altibase.com/kr/product

#### 매뉴얼

[Migration Center User's Manual](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Tools/Altibase_release/kor/Migration%20Center%20User's%20Manual.md)

#### 설치

Migration Center User's Manual을 참고한다.

