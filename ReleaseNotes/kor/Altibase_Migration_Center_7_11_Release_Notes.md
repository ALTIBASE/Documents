# Altibase Migration Center 7.11 Release Notes

**(Oct. 21, 2022)**



# **Table of Contents** 

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

Migration Center는 데이터베이스 마이그레이션을 위한 도구로서, 사용자가 편리하게 써드파티 데이터베이스를 알티베이스 데이터베이스 또는 외부 파일로 이관하거나 알티베이스 데이터베이스를 오라클 데이터베이스로 이관하도록 한다. 보통 데이터베이스 마이그레이션은 수동으로 진행할 경우 복잡하고 시간이 많이 소요되며 휴먼 에러가 발생하는 불편함이 있다. 이를 효율화하기 위해 Migration Center는 GUI 모드에서 마우스 클릭 몇 번만으로 데이터베이스 마이그레이션을 가능하게 한다. 이에 더하여, 자원 사용을 최적화하기 위해 CLI 모드도 지원한다.

<br/>

## 1.2 시스템 요구사항

### 하드웨어 최소 사양

Migration Center센터를 실행하기 위한 하드웨어의 최소 사양은 아래와 같다. 

|                 |        GUI 모드         | CLI 모드 |
| --------------- | :---------------------: | :------: |
| **프로세서**    | 800MHz Pentium III 이상 |   좌동   |
| **메모리**      |       512 MB 이상       |   좌동   |
| **디스크**      |   150MB 이상 여유공간   |   좌동   |
| **화면 해상도** |  1024 * 768 픽셀 이상   |    -     |

### 지원 OS

Migration Center는 소프트웨어 최소 사양을 만족하면 OS 무관하게 실행할 수 있다. 

### 소프트웨어 최소 사양

Migration Center는 순수 Java 기반 클라이언트 애플리케이션으로, JAVA Runtime Environment (JRE)에 의존한다. 또한  Migration Center를 GUI 모드로 실행하기 위해 운영 체제의 그래픽 라이브러리에 대한 추가 지원이 필요하다.

| Mode | JRE                      | OS Graphic Library |
| ---- | ------------------------ | :----------------: |
| GUI  | Sun 또는 IBM Java 8 이상 |        필수        |
| CLI  | Sun 또는 IBM Java 8 이상 |     필수 아님      |

<br/>

## 1.3 호환 가능한 데이터베이스 시스템

Migration Center 7.11 으로 마이그레이션 할 수 있는 데이터베이스 시스템 종류와 버전을 소개한다.

#### 대상 데이터베이스가 Altibase 일 때

| **원본 데이터베이스 종류 및 버전**                           | **대상 데이터베이스 버전** |
| :----------------------------------------------------------- | :------------------------- |
| Altibase 4.3.9 이상<br />CUBRID 8.4.1 ~ 9.3.5 (ISO-8859-1, UTF-8 charset) <br/>Informix 11.50 <br />Microsoft SQL Server 2005 ~ 2012<br />Oracle Database 9i ~ 11g <br />Oracle MySQL 5.0 ~ 5.7 <br />Oracle TimesTen 7.0, 11.2 <br />Tibero 4 SP1 ~ 6 | Altibase 6.5.1 이상        |

#### 대상 데이터베이스가 Oracle 일 때

| **원본 데이터베이스 종류 및 버전** | **대상 데이터베이스 버전** |
| :--------------------------------- | :------------------------- |
| Altibase 4.3.9 이상                | Oracle Database 10g ~ 11g  |

<br/>

# 2. 릴리즈 정보

Migration Center 7.11 의 새로운 기능과 수정된 버그 및 변경 사항에 관한 내용이다.

## 2.1 새로운 기능

<br/>

## 2.2 수정된 버그

### BUG-49950 Migration Center에서 지원하지 않는 데이터베이스 객체의 생성 문장을 확인할 수 없습니다.

Migration Center에서 지원하지 않는 원본 데이터베이스의 객체는 사용자가 직접 수동으로 변환해야 한다. Migration Center 7.11부터 구축(Build) 단계에서 객체 생성 구문을 아래 두 파일에 기록하고 있으므로 사용자는 이 파일들을 변환 작업에 참고할 수 있다.

- SrcDbObj_Create.sql
- BuildReport4Unsupported.html

### BUG-49951 MySQL의 Unicode  문자집합 CHAR/VARCHAR 테이블 컬럼이 Altibase로 변환 시 NVARCHAR(10666)으로 변환됩니다.

MySQL의 CHAR 데이터 타입이 Altibase로 변환 시 NVARCHAR(10666)으로 변환되는 현상을 수정한다. MySQL에서 CHAR/VARCHAR 컬럼의 문자 집합이 유니코드일 때 Altibase의 문자 집합에 따라 변환되는 데이터 타입이 결정된다.

|                      MySQL의 CHAR/VARCHAR | Altibase의 문자 집합이 유니코드일 때 | Altibase의 문자 집합이 유니코드가 아닐 때 |
| ----------------------------------------: | :----------------------------------: | :---------------------------------------: |
|      **컬럼의 문자 집합이 유니코드일 때** |             CHAR/VARCHAR             |              NCHAR/NVARCHAR               |
| **컬럼의 문자 집합이 유니코드가 아닐 때** |             CHAR/VARCHAR             |               CHAR/VARCHAR                |

또한, 원본 데이터베이스의  CHAR 또는 VARCHAR 타입의 테이블 컬럼 크기를 대상 데이터베이스의 컬럼 크기 표현단위 (바이트 또는 문자갯수)와 문자집합을 고려해 변환한다. 만약 변환된 크기가 대상 데이터베이스의 CHAR 또는 VARCHAR의 최대 크기를 초과하면 해당 테이블 컬럼의 데이터 타입을 CLOB으로 변경하도록 수정하였다. 이는 원본, 대상 데이터베이스 간의 데이터 타입 최대 크기 차이로 데이터 마이그레이션 시 데이터 손실을 방지하기 위해서이다. 

관련 내용은 [Migration Center User's Manual-C.부록: 데이터 타입 맵핑-기본 데이터 타입 맵핑 테이블](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Tools/Altibase_release/kor/Migration%20Center%20User's%20Manual.md#%EA%B8%B0%EB%B3%B8-%EB%8D%B0%EC%9D%B4%ED%84%B0-%ED%83%80%EC%9E%85-%EB%A7%B5%ED%95%91-%ED%85%8C%EC%9D%B4%EB%B8%94)에서도 확인할 수 있다. 

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

- MigrationCenter7.11.zip

- MigrationCenter7.11.tar.gz

<br/>

# 5. 다운로드

#### 패키지

[http://support.altibase.com](http://support.altibase.com/)

#### 매뉴얼

[Migration Center User's Manual](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Tools/kor/Migration%20Center%20User's%20Manual.md)

#### 설치

Migration Center User's Manual을 참고한다.
