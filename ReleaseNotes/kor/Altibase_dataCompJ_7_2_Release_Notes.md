- [dataCompJ Release Notes](#datacompj-release-notes)
  - [1. 개요](#1-개요)
    - [1.1 하드웨어 요구사항](#11-하드웨어-요구사항)
    - [1.2 지원하는 OS 및 플랫폼](#12-지원하는-os-및-플랫폼)
  - [2. 릴리즈 정보](#2-릴리즈-정보)
    - [2.1 버전](#21-버전)
    - [2.2 새로운 기능](#22-새로운-기능)
    - [2.3 수정된 버그](#23-수정된-버그)
    - [2.4 데이터베이스 호환성](#24-데이터베이스-호환성)
    - [2.5 프로퍼티](#25-프로퍼티)
    - [2.6 에러 메시지](#26-에러-메시지)
  - [3. 사용된 오픈소스 라이브러리](#3-사용된-오픈소스-라이브러리)
  - [4. 패키지](#4-패키지)
  - [5. 다운로드](#5-다운로드)
    - [5.1 패키지](#51-패키지)

# dataCompJ Release Notes

**(Feb. 17, 2022)**

## 1. 개요

Altibase dataCompJ는 Altibase 데이터베이스에서 이기종 데이터베이스로 데이터를 복제한 이후, 데이터 정합성 확인과 데이터 불일치를 해소하기 위한 도구이다. dataCompJ는 비교하는 메인 대상 데이터를 Altibase에서 제공하는 Altibase Adapter for Oracle(oraAdapter) 또는 JDBC Adapter를 사용하여 Altibase에서 다른 이기종 데이터베이스로 복제한다. dataCompJ는 Altibase와 다른 이기종 데이터베이스를 테이블 단위로 비교하고 데이터 불일치가 있는 경우 이에 관한 정보를 파일로 출력한다. Altibase dataCompJ의 올바른 사용은 뛰어난 기술적 성능을 통해 효과적인 데이터베이스 관리를 가능하게 한다.

### 1.1 하드웨어 요구사항

- 메인 메모리: 최소 512MB, 4GB 이상 권장
- 디스크: 최소 500MB 이상의 여유 공간 필요

### 1.2 지원하는 OS 및 플랫폼

| Mode | JRE                                                      |
| ---- | -------------------------------------------------------- |
| CLI  | Oracle, OpenJDK 또는 IBM Java Runtime Environment 8 이상 |

dataCompJ는 순수 Java 기반 클라이언트 애플리케이션으로, 하드웨어나 OS보다 JAVA Runtime Environment (JRE)에 의존한다.

## 2. 릴리즈 정보

### 2.1 버전

- 7.2

### 2.2 새로운 기능

- N/A

### 2.3 수정된 버그

| PK        | Synopsis                                                     |
| --------- | ------------------------------------------------------------ |
| BUG-45222 | 따옴표로 묶인 사용자 입력 개체 이름을 처리해야 한다.         |
| BUG-46675 | 미지원 DB JDBC URL에 대한 에러메시지를 더욱 명확하게 제공해야 한다. |
| BUG-46689 | JDBC URL 문자열을 이용한 DB 타입 검사 루틴을 수정해야 한다.  |
| BUG-49501 | dataCompJ log4j 보안 문제로 2.17.1 버전으로 업그레이드 한다. |

### 2.4 데이터베이스 호환성

#### Master 데이터베이스

- Altibase: Altibase 5.3.3 이상 버전

#### Slave 데이터베이스

- Oracle: Oracle 9i 이상
- MariaDB: MariaDB 5.5.x 이상

### 2.5 프로퍼티

### 2.6 에러 메시지

## 3. 사용된 오픈소스 라이브러리

dataCompJ는 아래의 오픈소스 라이브러리에 기반한다. 라이선스는 텍스트 파일 형식으로 dataCompJ와 함께 제공된다.

| Library             | Open Source License                                          |
| ------------------- | ------------------------------------------------------------ |
| Apache Commons CLI  | http://commons.apache.org/proper/commons-cli/<br/>License: Apache License 2.0 (http://www.apache.org/licenses/LICENSE-2.0.txt) |
| Apache Commons Lang | http://commons.apache.org/proper/commons-lang/ <br/>License: Apache License 2.0 (http://www.apache.org/licenses/LICENSE-2.0.txt) |
| Apache Commons IO   | http://commons.apache.org/proper/commons-io/ <br>License: Apache License 2.0 (http://www.apache.org/licenses/LICENSE-2.0.txt) |
| JDOM                | http://www.jdom.org/ <br/>License: Apache-style Open Source License (http://www.jdom.org/docs/faq.html#a0030) |
| Log4j               | http://logging.apache.org/index.html <br/>License: Apache License 2.0 (http://www.apache.org/licenses/LICENSE-2.0.txt) |
| Oracle JDBC Driver  | http://www.oracle.com <br>License: Oracle Free Use Terms and Conditions (https://www.oracle.com/downloads/licenses/oracle-free-license.html) |

## 4. 패키지

| Archive Name                             |
| ---------------------------------------- |
| dataCompJ7.2.zip<br/>dataCompJ7.2.tar.gz |

## 5. 다운로드

### 5.1 패키지

http://support.altibase.com/kr/product
