- Altibase Migration Center 7.9 Release Notes
  - [1\. 개요](#1-개요)
    - [1.1 시스템 요구사항](#11-시스템-요구사항)
    - [1.2 지원하는 OS 및 플랫폼](#12-지원하는-os-및-플랫폼)
  - [2\. 릴리즈 정보](#2-릴리즈-정보)
    - [2.1 Altibase Migration Center 7.9](#21-altibase-migration-center-79)
    - [2.2 변경사항](#22-변경사항)
    - [2.3 사용된 오픈소스 라이브러리 / 로열티 프리 이미지](#23-사용된-오픈소스-라이브러리--로열티-프리-이미지)
    - [2.4 패키지](#24-패키지)
    - [2.5 다운로드](#25-다운로드)

# Altibase Migration Center 7.9 Release Notes

**(Nov. 11, 2021)**

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
| GUI  | Sun 또는 IBM Java 5 이상 | 필수               |
| CLI  | Sun 또는 IBM Java 5 이상 | 필수 아님          |

Migration Center는 순수 Java 기반 클라이언트 애플리케이션으로, 클라이언트의 하드웨어나 OS보다 JAVA Runtime Environment (JRE)에 의존한다. 단, Migration Center를 GUI 모드로 실행하기 위해 운영 체제의 그래픽 라이브러리에 대한 추가 지원이 필요하다.

## 2. 릴리즈 정보

### 2.1 Altibase Migration Center 7.9

Migration Center는 데이터베이스 마이그레이션을 위한 도구로서, 사용자가 편리하게 써드파티 데이터베이스를 알티베이스 데이터베이스 또는 외부 파일로 이관하거나 알티베이스 데이터베이스를 오라클 데이터베이스로 이관하도록 한다. 보통 데이터베이스 마이그레이션은 수동으로 진행할 경우 복잡하고 시간이 많이 소요되며 휴먼 에러가 발생하는 불편함이 있다. 이를 효율화하기 위해 Migration Center는 GUI 모드에서 마우스 클릭 몇 번만으로 데이터베이스 마이그레이션을 가능하게 한다. 이에 더하여, 자원 사용을 최적화하기 위해 CLI 모드도 지원한다.

#### 2.1.1 새로운 기능

- 원본 데이터베이스로 Tibero 4 sp1 지원
- OpenJDK12 지원

#### 2.1.2 수정된 버그

| PK        | SYNOPSIS                                                     |
| --------- | ------------------------------------------------------------ |
| BUG-47352 | Reconcile 중 파티션드 테이블 변환 단계에서 변경사항 일부가 Next 또는 Back 후에 돌아오면 유지되지 않는다. |
| BUG-47372 | PSM 내부 지역 변수의 타입 변환 방식을 개선해야 한다.         |
| BUG-47376 | 원본 데이터베이스가 Altibase 7 이상일 경우 dbms_metadata 패키지를 이용해서 원본 DDL을 지원한다. |
| BUG-47381 | Synonym 참조 대상 객체가 빌드 대상이 아닐 시 Reconcile 단계에서 hang이 발생한다. |
| BUG-47402 | TimesTen의 direct connection을 지원한다.                     |
| BUG-47408 | 컬럼 이름으로 허용되는 예약어는 _poc 자동변환에서 제외해야 한다. |
| BUG-47409 | 원본 데이터베이스의 인덱스에 PK 컬럼이 있을 경우 빌드 시에 에러와 함께 마이그레이션 대상에서 제외된다. |
| BUG-48340 | 테이블 이름에 밑줄(_)이 포함된 경우 유사한 이름을 가진 테이블 컬럼도 포함된다. |
| BUG-48672 | Altibase 7.2부터 범위 파티션드 테이블에 기본 파티션이 없더라도 경고창이 나타나지 않는다. |
| BUG-49467 | TimesTen 11.2.1.9.10으로부터 알티베이스로의 마이그레이션을 지원한다. |
| BUG-49499 | [CVE-2021-44228](https://github.com/advisories/GHSA-jfh8-c2jp-5v3q) 보안 문제로 log4j를 2.15.0 버전으로 업그레이드해야 한다. |

### 2.2 변경사항

Migration Center에 추가, 삭제 또는 변경된 기능들은 다음과 같다.

- JRE 8 이상을 요구하는 Altibase 7.2 JDBC를 지원하기 위해 Migration Center에 포함된 JRE 버전이 7에서 8로 업데이트되었다.

#### 2.2.1 버전 업데이트

Migration Center 버전

| Altibase Migration Center 버전 |
| ------------------------------ |
| 7.9                            |

#### 2.2.2 데이터베이스 호환성

##### 대상 데이터베이스: Altibase

- 원본 데이터베이스
  - Altibase : Altibase 4.3.9 이상 버전
  - ORACLE : Oracle 9i ~ 11g
  - MS-SQL : MS-SQL 2005-2012
  - MySQL : MySQL 5.0 ~ 5.5
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

| JRE                      | Archive Name                                     |
| ------------------------ | ------------------------------------------------ |
| Sun 또는 IBM Java 5 이상 | MigrationCenter7.9.zip MigrationCenter7.9.tar.gz |

### 2.5 다운로드

#### 2.5.1 패키지

[http://support.altibase.com](http://support.altibase.com/)

#### 2.5.2 매뉴얼

[Migration Center User's Manual](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Tools/kor/Migration%20Center%20User's%20Manual.md)

#### 2.5.3 설치

Migration Center User's Manual을 참고한다.