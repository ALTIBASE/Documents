

- [Altibase Migration Center 7.10 Release Notes](#altibase-migration-center-710-release-notes)
  - [1. 개요](#1-%EA%B0%9C%EC%9A%94)
    - [1.1 시스템 요구사항](#11-%EC%8B%9C%EC%8A%A4%ED%85%9C-%EC%9A%94%EA%B5%AC%EC%82%AC%ED%95%AD)
    - [1.2 지원하는 OS 및 플랫폼](#12-%EC%A7%80%EC%9B%90%ED%95%98%EB%8A%94-os-%EB%B0%8F-%ED%94%8C%EB%9E%AB%ED%8F%BC)
  - [2. 릴리즈 정보](#2-%EB%A6%B4%EB%A6%AC%EC%A6%88-%EC%A0%95%EB%B3%B4)
    - [2.1 Altibase Migration Center 7.10](#21-altibase-migration-center-710)
    - [2.2 변경사항](#22-%EB%B3%80%EA%B2%BD%EC%82%AC%ED%95%AD)
    - [2.3 사용된 오픈소스 라이브러리 / 로열티 프리 이미지](#23-%EC%82%AC%EC%9A%A9%EB%90%9C-%EC%98%A4%ED%94%88%EC%86%8C%EC%8A%A4-%EB%9D%BC%EC%9D%B4%EB%B8%8C%EB%9F%AC%EB%A6%AC--%EB%A1%9C%EC%97%B4%ED%8B%B0-%ED%94%84%EB%A6%AC-%EC%9D%B4%EB%AF%B8%EC%A7%80)
    - [2.4 패키지](#24-%ED%8C%A8%ED%82%A4%EC%A7%80)
    - [2.5 다운로드](#25-%EB%8B%A4%EC%9A%B4%EB%A1%9C%EB%93%9C)

# Altibase Migration Center 7.10 Release Notes

**(Sep. 19, 2022)**

## 1. 개요

### 1.1 시스템 요구사항

#### 하드웨어 최소 사양

|             |        GUI 모드         | CLI 모드 |
| ----------- | :---------------------: | :------: |
| 프로세서    | 800MHz Pentium III 이상 |   좌동   |
| 메모리      |       512 MB 이상       |   좌동   |
| 디스크      |   150MB 이상 여유공간   |   좌동   |
| 화면 해상도 |  1024 * 768 픽셀 이상   |    -     |

### 1.2 지원하는 OS 및 플랫폼

| Mode | JRE                      | OS Graphic Library |
| ---- | ------------------------ | ------------------ |
| GUI  | Sun 또는 IBM Java 8 이상 | 필수               |
| CLI  | Sun 또는 IBM Java 8 이상 | 필수 아님          |

Migration Center는 순수 Java 기반 클라이언트 애플리케이션으로, 클라이언트의 하드웨어나 OS보다 JAVA Runtime Environment (JRE)에 의존한다. 단, Migration Center를 GUI 모드로 실행하기 위해 운영 체제의 그래픽 라이브러리에 대한 추가 지원이 필요하다.

## 2. 릴리즈 정보

### 2.1 Altibase Migration Center 7.10

Migration Center는 데이터베이스 마이그레이션을 위한 도구로서, 사용자가 편리하게 써드파티 데이터베이스를 알티베이스 데이터베이스 또는 외부 파일로 이관하거나 알티베이스 데이터베이스를 오라클 데이터베이스로 이관하도록 한다. 보통 데이터베이스 마이그레이션은 수동으로 진행할 경우 복잡하고 시간이 많이 소요되며 휴먼 에러가 발생하는 불편함이 있다. 이를 효율화하기 위해 Migration Center는 GUI 모드에서 마우스 클릭 몇 번만으로 데이터베이스 마이그레이션을 가능하게 한다. 이에 더하여, 자원 사용을 최적화하기 위해 CLI 모드도 지원한다.

#### 2.1.1 새로운 기능

- 원본 데이터베이스로 MySQL 5.6, 5.7 지원
- OpenJDK18 지원

#### 2.1.2 수정된 버그

| PK        | SYNOPSIS                                                  |
| --------- | --------------------------------------------------------- |
| BUG-49579 | MySQL bit 타입 default 값 변환이 부정확합니다.            |
| BUG-49595 | Support MySQL 5.6, 5.7 to Altibase migration              |
| BUG-49731 | LOB 데이터도 배치 처리 가능하도록 옵션을 제공해야 합니다. |


### 2.2 변경사항

Migration Center에 추가, 삭제 또는 변경된 기능들은 다음과 같다.

- N/A

#### 2.2.1 버전 업데이트

Migration Center 버전

| Altibase Migration Center 버전 |
| ------------------------------ |
| 7.10                           |

#### 2.2.2 데이터베이스 호환성

##### 대상 데이터베이스: Altibase

- 원본 데이터베이스
  - Altibase : Altibase 4.3.9 이상 버전
  - ORACLE : Oracle 9i ~ 11g
  - MS-SQL : MS-SQL 2005 ~ 2012
  - MySQL : MySQL 5.0 ~ 5.7
  - Informix : Informix 11.50
  - TimesTen : TimesTen 7.0, TimesTen 11.2
  - CUBRID : CUBRID 8.4.1 ~ 9.3.5 (ISO-8859-1, UTF-8 charset)
  - Tibero : Tibero 4 sp1, 5 ~ 6
- 대상 데이터베이스
  - Altibase : Altibase 6.5.1 이상 버전

##### 대상 데이터베이스: Oracle

- 원본 데이터베이스
  - Altibase : Altibase 4.3.9 이상 버전

- 대상 데이터베이스
  - ORACLE : Oracle 10g ~ 11g

#### 2.2.3 프로퍼티

없음

#### 2.2.4 에러 메시지

없음

### 2.3 사용된 오픈소스 라이브러리 / 로열티 프리 이미지

Migration Center는 아래의 오픈소스 라이브러리에 기반한다. 라이선스는 텍스트 파일 형식으로 Migration Center와 함께 제공된다.

- 오픈소스 라이브러리

| Library                    | Open Source License                                          |
| -------------------------- | ------------------------------------------------------------ |
| Apache Commons Codec       | Homepage: http://commons.apache.org/codec/ <br>License: Apache License 2.0(http://www.apache.org/licenses/LICENSE-2.0.txt) |
| Apache Commons Lang        | Homepage: http://commons.apache.org/proper/commons-lang/ <br>License: Apache License 2.0(http://www.apache.org/licenses/LICENSE-2.0.txt) |
| Apache Commons Mathematics | Homepage: http://commons.apache.org/math/  <br>License: Apache License 2.0(http://www.apache.org/licenses/LICENSE-2.0.txt) |
| Apache Commons IO          | Homepage: http://commons.apache.org/proper/commons-io/ <br>License: Apache License 2.0(http://www.apache.org/licenses/LICENSE-2.0.txt) |
| Java Help System           | Homepage: http://javahelp.java.net/ <br>License: GPL linking exception(http://en.wikipedia.org/wiki/GPL_linking_exception) |
| JDOM                       | Homepage: http://www.jdom.org/ <br>License: Apache-style Open Source License(http://www.jdom.org/docs/faq.html#a0030) |
| JUniversalChardet          | Homepage: http://wwwarchive.mozilla.org/projects/intl/UniversalCharsetDetection.html <br>License: Mozilla Public License Version 1.1(http://www.mozilla.org/MPL/1.1/) |
| JGraphT                    | Homepage: http://jgrapht.org/ <br>License: GNU Lesser General Public License(http://jgrapht.org/LGPL.html) |
| Log4J                      | Homepage: http://logging.apache.org/index.html <br>License: Apache License 2.0(http://www.apache.org/licenses/LICENSE-2.0.txt) |
| OpenCSV                    | Homepage: http://opencsv.sourceforge.net/ <br>License: Apache License 2.0(http://www.apache.org/licenses/LICENSE-2.0.txt) |
| Oracle JDBC Driver         | Homepage: [http://www.oracle.com](http://www.oracle.com/) <br>License: OTN(http://www.oracle.com/technetwork/licenses/distribution-license152002.html) |

- 로열티 프리 이미지

| Library                  | Royalty-Free Images                                      |
| ------------------------ | -------------------------------------------------------- |
| org.eclipse.datatools    | Homepage: [www.eclipse.org](http://www.eclipse.org/)     |
| asp.net_commercial_free2 | Homepage: [www.asp.net](http://www.asp.net/)             |
| fugue-icons-3.2.3-src    | Homepage: http://code.google.com/p/fugue-icons-src/      |
| Silk Icons 1.3           | Homepage: [www.famfamfam.com](http://www.famfamfam.com/) |

### 2.4 패키지

| JRE                      | Archive Name                                       |
| ------------------------ | -------------------------------------------------- |
| Sun 또는 IBM Java 8 이상 | MigrationCenter7.10.zip MigrationCenter7.10.tar.gz |

### 2.5 다운로드

#### 2.5.1 패키지

[http://support.altibase.com](http://support.altibase.com/)

#### 2.5.2 매뉴얼

[Migration Center User's Manual](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Tools/kor/Migration%20Center%20User's%20Manual.md)

#### 2.5.3 설치

Migration Center User's Manual을 참고한다.

