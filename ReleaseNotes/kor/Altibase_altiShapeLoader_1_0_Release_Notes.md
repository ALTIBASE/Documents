altiShapeLoader Release Notes
================

#### Release 1.0 (Oct. 15, 2021)

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
Altibase Release Notes altiShapeLoader
Release 1.0
Copyright ⓒ 2001~2022 Altibase Corp. All Rights Reserved.<br>
본 문서의 저작권은 ㈜알티베이스에 있습니다. 이 문서에 대하여 당사의 동의없이 무단으로 복제 또는 전용할 수 없습니다.<br>
<b>㈜알티베이스</b>
08378 서울시 구로구 디지털로 306 대륭포스트타워Ⅱ 10층
전화 : 02-2082-1114
팩스 : 02-2082-1099
고객서비스포털 : <a href='http://support.altibase.com'>http://support.altibase.com</a>
홈페이지      : <a href='http://www.altibase.com/'>http://www.altibase.com</a></pre>

<br>

# 목차

- [1\. 개요](#1-개요)
  - [1.1 시스템 요구사항](#11-시스템-요구사항)
- [2. 릴리즈 정보](#2-릴리즈-정보)
  - [2.1 버전](#21-버전)
  - [2.2 새로운 기능](#22-새로운-기능)
  - [2.3 수정된 버그](#23-수정된-버그)
  - [2.4 프로퍼티](#24-프로퍼티)
  - [2.5 에러 메시지](#25-에러-메시지)
- [3. 사용된 오픈소스 라이브러리](#3-사용된-오픈소스-라이브러리)
- [4. 패키지](#4-패키지)
- [5\. 다운로드](#5-다운로드)
  - [5.1 패키지](#51-패키지)
  - [5.2 매뉴얼](#52-매뉴얼)
  - [5.3 설치](#53-설치)

<br>

# 1. 개요

altiShapeLoader는 쉐이프 파일(Shapefile) 가져오기와 내보내기를 위한 도구로, Java 기반의 오픈소스 라이브러리 GeoTools를 사용하여 작성되었다.

쉐이프 파일 가져오기는 좌표 및 좌표 속성과 같은 공간 데이터 정보를 쉐이프 파일로부터 알티베이스 데이터베이스 테이블에 삽입하는 것을 의미한다. 쉐이프 파일 내보내기는 알티베이스 데이터베이스 테이블에 저장된 공간 데이터 정보를 사용하여 쉐이프 파일을 생성하는 것을 의미한다.

### 1.1 시스템 요구사항

#### 하드웨어 요구사항

- 메인 메모리: 최소 512MB, 4GB 이상 권장
- 디스크: 설치를 위해 최소 20MB 이상의 여유 공간 필요

#### 소프트웨어 요구사항

- Java: Oracle, OpenJDK 또는 IBM Java Runtime Environment 8 이상 버전

#### 지원하는 플랫폼

- Java 설치 및 구동 가능한 64bit OS

#### 호환 가능한 알티베이스 버전

- Altibase 7.1 이상 버전

<br>

# 2. 릴리즈 정보

### 2.1 버전

- 1.0

### 2.2 새로운 기능

- 해당 릴리즈가 첫번째 릴리즈이다.

### 2.3 수정된 버그

### 2.4 프로퍼티

### 2.5 에러 메시지

<br>

# 3. 사용된 오픈소스 라이브러리

altiShapeLoader는 아래의 오픈소스 라이브러리에 기반한다. 라이선스는 텍스트 파일 형식으로 altiShapeLoader와 함께 제공된다.

| Library              | Version | Open Source License                                          |
| -------------------- | ------- | ------------------------------------------------------------ |
| GeoTools             | 25.1    | Homepage: https://geotools.org/ <br>License: GNU Lesser General Public License(http://jgrapht.org/LGPL.html) |
| hsqldb               | 1.8.0.1 | Homepage: http://hsqldb.org/ <br>License: Based on BSD(http://hsqldb.org/web/hsqlLicense.html) |
| Apache Commons IO    | 2.6     | Homepage: http://commons.apache.org/proper/commons-io/ <br>License: Apache License 2.0(http://www.apache.org/licenses/LICENSE-2.0.txt) |
| Apache Commons CLI   | 1.3.1   | Homepage: [http://https://commons.apache.org/proper/commons-cli/](http://https//commons.apache.org/proper/commons-cli/)<br>License: Apache License 2.0(http://www.apache.org/licenses/LICENSE-2.0.txt) |
| Apache Commons lang3 | 1.3.1   | Homepage: https://commons.apache.org/proper/commons-lang/ <br>License: Apache License 2.0(http://www.apache.org/licenses/LICENSE-2.0.txt) |
| Apache log4j         | 2.17.1  | Homepage: https://logging.apache.org/log4j/ <br>License: Apache License 2.0(http://www.apache.org/licenses/LICENSE-2.0.txt) |

<br>

# 4. 패키지

| Archive Name                                             |
| -------------------------------------------------------- |
| altiShapeLoader-1.0.zip <br/> altiShapeLoader-1.0.tar.gz |

<br>

# 5. 다운로드

### 5.1 패키지

http://support.altibase.com/kr/product

### 5.2 매뉴얼

[altiShapeLoader User's Manual](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Tools/Altibase_release/kor/altiShapeLoader%20User's%20Manual.md)

### 5.3 설치

[altiShapeLoader User's Manual](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Tools/Altibase_release/kor/altiShapeLoader%20User's%20Manual.md) 을 참고한다.

