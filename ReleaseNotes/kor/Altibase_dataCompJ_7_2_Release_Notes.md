dataCompJ Release Notes
================

#### Release 7.2 (Feb. 17, 2022)

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
Altibase Release Notes dataCompJ
Release 7.2
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

<br>

# 1. 개요

dataCompJ는 Altibase에서 이기종 데이터베이스로 복제한 데이터를 대상으로 데이터 정합성 확인과 데이터 불일치를 해소하기 위한 도구이다. 테이블 단위로 데이터를 비교하고 데이터 불일치가 있는 경우 이에 관한 정보를 파일로 출력한다. 불일치 데이터를 Slave 데이터베이스에 직접 적용하여 데이터를 일치시키는 기능도 제공한다.<br>
dataCompJ가 관리하는 데이터는 데이터 복제 도구로 Altibase에서 제공하는 Adapter for Oracle 또는 Adapter for JDBC를 사용하여 복제한 데이터를 전제로 한다. <br>
dataCompJ는 편리한 사용성과 빠른 성능으로, 효율적인 이기종 데이터베이스 간 데이터 관리 방법을 제공한다.

### 1.1 하드웨어 요구사항

- 메인 메모리: 최소 512MB, 4GB 이상 권장
- 디스크: 최소 500MB 이상의 여유 공간 필요

### 1.2 지원하는 OS 및 플랫폼

| Mode | JRE                                                      |
| ---- | -------------------------------------------------------- |
| CLI  | Oracle, OpenJDK 또는 IBM Java Runtime Environment 8 이상 |

dataCompJ는 순수 Java 기반 클라이언트 애플리케이션으로, 하드웨어나 OS보다 JAVA Runtime Environment (JRE)에 의존한다.

<br>

# 2. 릴리즈 정보

### 2.1 버전

- 7.2

### 2.2 새로운 기능

### 2.3 수정된 버그

| 버그 번호 | 제목                                                         |
| --------- | ------------------------------------------------------------ |
| BUG-45222 | 따옴표로 묶인 사용자 입력 개체 이름을 처리해야 한다.         |
| BUG-46675 | 미지원 DB JDBC URL에 대한 에러메시지를 더욱 명확하게 제공해야 한다. |
| BUG-46689 | JDBC URL 문자열을 이용한 DB 타입 검사 루틴을 수정해야 한다.  |
| BUG-49501 | dataCompJ log4j 보안 문제로 2.17.1 버전으로 업그레이드 한다. |

### 2.4 데이터베이스 호환성

#### Master 데이터베이스

- Altibase: Altibase 5.3.3 이상

#### Slave 데이터베이스

- Oracle: Oracle 9i 이상
- MariaDB: MariaDB 5.5.x 이상

### 2.5 프로퍼티

### 2.6 에러 메시지

<br>

# 3. 사용된 오픈소스 라이브러리

dataCompJ는 아래의 오픈소스 라이브러리에 기반한다. 라이선스는 텍스트 파일 형식으로 dataCompJ와 함께 제공된다.

| 라이브러리          | 오픈소스 라이선스                                            |
| ------------------- | ------------------------------------------------------------ |
| Apache Commons CLI  | http://commons.apache.org/proper/commons-cli/<br/>License: Apache License 2.0 (http://www.apache.org/licenses/LICENSE-2.0.txt) |
| Apache Commons Lang | http://commons.apache.org/proper/commons-lang/ <br/>License: Apache License 2.0 (http://www.apache.org/licenses/LICENSE-2.0.txt) |
| Apache Commons IO   | http://commons.apache.org/proper/commons-io/ <br>License: Apache License 2.0 (http://www.apache.org/licenses/LICENSE-2.0.txt) |
| JDOM                | http://www.jdom.org/ <br/>License: Apache-style Open Source License (http://www.jdom.org/docs/faq.html#a0030) |
| Log4j               | http://logging.apache.org/index.html <br/>License: Apache License 2.0 (http://www.apache.org/licenses/LICENSE-2.0.txt) |
| Oracle JDBC Driver  | http://www.oracle.com <br>License: Oracle Free Use Terms and Conditions (https://www.oracle.com/downloads/licenses/oracle-free-license.html) |

<br>

# 4. 패키지

2가지 종류의 압축 파일을 제공한다. 
- dataCompJ7.2.zip
- dataCompJ7.2.tar.gz 

<br>

# 5. 다운로드

### 5.1 패키지

http://support.altibase.com/kr/product
