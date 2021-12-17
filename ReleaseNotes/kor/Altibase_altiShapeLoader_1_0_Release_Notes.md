- altiShapeLoader Release Notes
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

# altiShapeLoader Release Notes

**(Oct. 15, 2021)**

## 1. 개요

altiShapeLoader는 쉐이프 파일(Shapefile) 가져오기와 내보내기를 위한 도구로, Java 기반의 오픈소스 라이브러리 GeoTools를 사용하여 작성되었다.

쉐이프 파일 가져오기는 좌표 및 좌표 속상과 같은 공간 데이터 정보를 쉐이프 파일로부터 알티베이스 데이터베이스 테이블에 삽입하는 것을 의미한다. 쉐이프 파일 내보내기는 알티베이스 데이터베이스 테이블에 저장된 공간 데이터 정보를 사용하여 쉐이프 파일을 생성하는 것을 의미한다.

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

## 2. 릴리즈 정보

### 2.1 버전

- 1.0

### 2.2 새로운 기능

- 해당 릴리즈가 첫번째 릴리즈이다.

### 2.3 수정된 버그

### 2.4 프로퍼티

### 2.5 에러 메시지

## 3. 사용된 오픈소스 라이브러리

altiShapeLoader는 아래의 오픈소스 라이브러리에 기반한다. 라이선스는 텍스트 파일 형식으로 altiShapeLoader와 함께 제공된다.

| Library              | Version | Open Source License                                          |
| -------------------- | ------- | ------------------------------------------------------------ |
| GeoTools             | 25.1    | Homepage: https://geotools.org/ License: GNU Lesser General Public License(http://jgrapht.org/LGPL.html) |
| hsqldb               | 1.8.0.1 | Homepage: http://hsqldb.org/ License: Based on BSD(http://hsqldb.org/web/hsqlLicense.html) |
| Apache Commons IO    | 2.6     | Homepage: http://commons.apache.org/proper/commons-io/ License: Apache License 2.0(http://www.apache.org/licenses/LICENSE-2.0.txt) |
| Apache Commons CLI   | 1.3.1   | Homepage: [http://https://commons.apache.org/proper/commons-cli/](http://https//commons.apache.org/proper/commons-cli/) License: Apache License 2.0(http://www.apache.org/licenses/LICENSE-2.0.txt) |
| Apache Commons lang3 | 1.3.1   | Homepage: https://commons.apache.org/proper/commons-lang/ License: Apache License 2.0(http://www.apache.org/licenses/LICENSE-2.0.txt) |
| Apache log4j         | 2.15.0  | Homepage: https://logging.apache.org/log4j/ License: Apache License 2.0(http://www.apache.org/licenses/LICENSE-2.0.txt) |

## 4. 패키지

| Archive Name                                     |
| ------------------------------------------------ |
| altiShapeLoader1.0.zip altiShapeLoader1.0.tar.gz |

## 5. 다운로드

### 5.1 패키지

http://support.altibase.com/kr/product

### 5.2 매뉴얼

[https://github.com/ALTIBASE/Documents/blob/master/Manuals/Tools/kor/altiShapeLoader%20User's%20Manual.md](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Tools/kor/altiShapeLoader%20User's%20Manual.md)

### 5.3 설치

altiShapeLoader User's Manual를 참고한다.