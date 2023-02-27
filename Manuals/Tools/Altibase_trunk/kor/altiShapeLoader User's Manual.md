altiShapeLoader User's Manual
================

#### Release 1.0

Altibase® Tools & Utilities

<br><br><br><br><br><br><!-- PDF 변환을 위한 여백입니다. --> 







































<!-- PDF 변환을 위한 여백입니다. --> 

<div align="left">
    <img src="media/common/e5cfb3761673686d093a3b00c062fe7a.png">
</div>
<br><br><!-- PDF 변환을 위한 여백입니다. --> 











































<!-- PDF 변환을 위한 여백입니다. -->

<pre>
Altibase Tools & Utilities altiShapeLoader User's Manual
Release 1.0
Copyright ⓒ 2001~2023 Altibase Corp. All Rights Reserved.<br>
본 문서의 저작권은 ㈜알티베이스에 있습니다. 이 문서에 대하여 당사의 동의없이 무단으로 복제 또는 전용할 수 없습니다.<br>
<b>㈜알티베이스</b>
08378 서울시 구로구 디지털로 306 대륭포스트타워Ⅱ 10층
전화 : 02-2082-1114
팩스 : 02-2082-1099
고객서비스포털 : <a href='http://support.altibase.com'>http://support.altibase.com</a>
홈페이지      : <a href='http://www.altibase.com/'>http://www.altibase.com</a></pre>



<br>

# 목차

- [서문](#%EC%84%9C%EB%AC%B8)
  - [이 매뉴얼에 대하여](#%EC%9D%B4-%EB%A7%A4%EB%89%B4%EC%96%BC%EC%97%90-%EB%8C%80%ED%95%98%EC%97%AC)
- [1. altiShapeLoader 소개](#1-altishapeloader-%EC%86%8C%EA%B0%9C)
  - [altiShapeLoader 버전](#altishapeloader-%EB%B2%84%EC%A0%84)
  - [개요](#%EA%B0%9C%EC%9A%94)
  - [시스템 요구 사항](#%EC%8B%9C%EC%8A%A4%ED%85%9C-%EC%9A%94%EA%B5%AC-%EC%82%AC%ED%95%AD)
  - [설치 및 제거](#%EC%84%A4%EC%B9%98-%EB%B0%8F-%EC%A0%9C%EA%B1%B0)
- [2. altiShapeLoader 사용하기](#2-altishapeloader-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0)
  - [알티베이스 선행조건 - SRID 등록](#%EC%95%8C%ED%8B%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4-%EC%84%A0%ED%96%89%EC%A1%B0%EA%B1%B4---srid-%EB%93%B1%EB%A1%9D)
  - [실행 옵션](#%EC%8B%A4%ED%96%89-%EC%98%B5%EC%85%98)
  - [필수 옵션](#%ED%95%84%EC%88%98-%EC%98%B5%EC%85%98)
  - [선택 옵션](#%EC%84%A0%ED%83%9D-%EC%98%B5%EC%85%98)
  - [성능 옵션](#%EC%84%B1%EB%8A%A5-%EC%98%B5%EC%85%98)
  - [특수 옵션](#%ED%8A%B9%EC%88%98-%EC%98%B5%EC%85%98)
  - [쉐이프 파일 가져오기(Import)](#%EC%89%90%EC%9D%B4%ED%94%84-%ED%8C%8C%EC%9D%BC-%EA%B0%80%EC%A0%B8%EC%98%A4%EA%B8%B0import)
  - [쉐이프 파일 내보내기(Export)](#%EC%89%90%EC%9D%B4%ED%94%84-%ED%8C%8C%EC%9D%BC-%EB%82%B4%EB%B3%B4%EB%82%B4%EA%B8%B0export)
  - [SRID 가져오기 및 내보내기](#srid-%EA%B0%80%EC%A0%B8%EC%98%A4%EA%B8%B0-%EB%B0%8F-%EB%82%B4%EB%B3%B4%EB%82%B4%EA%B8%B0)
- [3. 주의사항](#3-%EC%A3%BC%EC%9D%98%EC%82%AC%ED%95%AD)
  - [쉐이프 파일(Shapefile) 제약점](#%EC%89%90%EC%9D%B4%ED%94%84-%ED%8C%8C%EC%9D%BCshapefile-%EC%A0%9C%EC%95%BD%EC%A0%90)
  - [GeoTools 제약점](#geotools-%EC%A0%9C%EC%95%BD%EC%A0%90)
- [4. 데이터 타입 변환](#4-%EB%8D%B0%EC%9D%B4%ED%84%B0-%ED%83%80%EC%9E%85-%EB%B3%80%ED%99%98)
  - [가져오기 데이터 타입 변환](#%EA%B0%80%EC%A0%B8%EC%98%A4%EA%B8%B0-%EB%8D%B0%EC%9D%B4%ED%84%B0-%ED%83%80%EC%9E%85-%EB%B3%80%ED%99%98)
  - [내보내기 데이터 타입 변환](#%EB%82%B4%EB%B3%B4%EB%82%B4%EA%B8%B0-%EB%8D%B0%EC%9D%B4%ED%84%B0-%ED%83%80%EC%9E%85-%EB%B3%80%ED%99%98)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

<br>

# 서문

### 이 매뉴얼에 대하여

이 매뉴얼은 지리정보시스템(GIS) 분야의 표준 파일인 쉐이프 파일(Shapefile)<sup>[1](#shapefile)</sup> 을 분석하여 공간 데이터 정보를 쉐이프 파일에서 Altibase 서버로 가져오거나 Altibase 서버에서 쉐이프 파일로 내보내기 기능을 제공하는 유틸리티 altiShapeLoader에 관한 문서이다.

#### 대상 사용

이 매뉴얼은 다음과 같은 Altibase 사용자를 대상으로 작성되었다.

- 데이터베이스 관리자

- 성능 관리자

- 데이터베이스 사용자

- 응용 프로그램 개발자

- 기술지원부

다음과 같은 배경 지식을 가지고 이 매뉴얼을 읽는 것이 좋다.

- 컴퓨터, 운영 체제 및 운영 체제 유틸리티 운용에 필요한 기본 지식

- 관계형 데이터베이스 사용 경험 또는 데이터베이스 개념에 대한 이해

- 컴퓨터 프로그래밍 경험

- 데이터베이스 서버 관리, 운영 체제 관리 또는 네트워크 관리 경험

#### 이 매뉴얼의 구성

이 매뉴얼은 다음과 같이 구성되어 있다.

- 제 1장 altiShapeLoader 소개  
  이 장은 altiShapeLoader를 사용하고자 하는 사용자들을 위해 기능과 설치 방법을 소개한다.

- 제 2장 altiShapeLoader  시작하기  
  이 장은 altiShapeLoader  효율적으로 원활하게 실행하는 데 도움이 되는 기본 개념을 소개하고, 명령어 인터페이스(CLI) 모드 사용법을 간단하게 설명한다.

#### 문서화 규칙

이 절에서는 이 매뉴얼에서 사용하는 규칙에 대해 설명한다. 이 규칙을 이해하면 이 매뉴얼과 설명서 세트의 다른 매뉴얼에서 정보를 쉽게 찾을 수 있다.

여기서 설명하는 규칙은 다음과 같다.

- 구문 다이어그램

- 샘플 코드 규칙

##### 구문 다이어그램

이 매뉴얼에서는 다음 구성 요소로 구축된 다이어그램을 사용하여, 명령문의 구문을 설명한다.

| 구성 요소                                       | 의미                                                  |
| ------------------------------------------- | --------------------------------------------------- |
| ![image1](media/altiShapeLoader/image1.gif) | 명령문이 시작한다. 완전한 명령문이 아닌 구문 요소는 화살표로 시작한다.            |
| ![image2](media/altiShapeLoader/image2.gif) | 명령문이 다음 라인에 계속된다. 완전한 명령문이 아닌 구문 요소는 이 기호로 종료한다.    |
| ![image3](media/altiShapeLoader/image3.gif) | 명령문이 이전 라인으로부터 계속된다. 완전한 명령문이 아닌 구문 요소는 이 기호로 시작한다. |
| ![image4](media/altiShapeLoader/image4.gif) | 명령문이 종료한다.                                          |
| ![](media/altiShapeLoader/image5.gif)       | 필수 항목                                               |
| ![](media/altiShapeLoader/image6.gif)       | 선택적 항목                                              |
| ![](media/altiShapeLoader/image7.gif)       | 선택사항이 있는 필수 항목. 한 항목만 제공해야 한다.                      |
| ![](media/altiShapeLoader/image8.gif)       | 선택사항이 있는 선택적 항목                                     |
| ![](media/altiShapeLoader/image9.gif)       | 선택적 항목. 여러 항목이 허용된다. 각 반복 앞부분에 콤마가 와야 한다.           |

##### 샘플 코드 규칙

코드 예제는 SQL, Stored Procedure, iSQL 또는 다른 명령 라인 구문들을 예를 들어 설명한다.

아래 테이블은 코드 예제에서 사용된 인쇄 규칙에 대해 설명한다.

| 규칙      | 의미                                                | 예제                                                                                                                                                     |
| ------- | ------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [ ]     | 선택 항목을 표시                                         | VARCHAR [(*size*)] [[FIXED \|] VARIABLE]                                                                                                               |
| { }     | 필수 항목 표시. 반드시 하나 이상을 선택해야 되는 표시                   | { ENABLE \| DISABLE \| COMPILE }                                                                                                                       |
| \|      | 선택 또는 필수 항목 표시의 인자 구분 표시                          | { ENABLE \| DISABLE \| COMPILE } <br />[ ENABLE \| DISABLE \| COMPILE ]                                                                                |
| . . .   | 그 이전 인자의 반복 표시 예제 코드들의 생략되는 것을 표시                 | SQL\> SELECT ename FROM employee; <br />ENAME  <br />----------------------- <br />SWNO  <br />HJNO  <br />HSCHOI  <br />. . . <br />20 rows selected. |
| 그 밖에 기호 | 위에서 보여진 기호 이 외에 기호들                               | EXEC :p1 := 1; <br />acc NUMBER(11,2);                                                                                                                 |
| 기울임 꼴   | 구문 요소에서 사용자가 지정해야 하는 변수, 특수한 값을 제공해야만 하는 위치       | SELECT \* FROM *table_name*; <br />CONNECT *userID*/*password*;                                                                                        |
| 소문자     | 사용자가 제공하는 프로그램의 요소들, 예를 들어 테이블 이름, 칼럼 이름, 파일 이름 등 | SELECT ename FROM employee;                                                                                                                            |
| 대문자     | 시스템에서 제공하는 요소들 또는 구문에 나타나는 키워드                    | DESC SYSTEM_.SYS_INDICES_;                                                                                                                             |

#### 관련 자료

자세한 정보를 위하여 Altibase의 다음 문서 목록을 참조한다.

- Installation Guide

- Getting Started Guide

- Administrator’s Manual

- Replication Manual

- Precompiler User’s Manual

- API User’s Manual

- Altibase C Interface Manual

- iSQL User’s Manual

- Utilities Manual

- General Reference

- Error Message Reference

#### Altibase는 여러분의 의견을 환영합니다.

이 매뉴얼에 대한 여러분의 의견을 보내주시기 바랍니다. 사용자의 의견은 다음 버전의 매뉴얼을 작성하는데 많은 도움이 됩니다. 보내실 때에는 아래 내용과 함께 고객서비스포털(http://support.altibase.com/kr/ )로 보내주시기 바랍니다.

- 사용 중인 매뉴얼의 이름과 버전

- 매뉴얼에 대한 의견

- 사용자의 성함, 주소, 전화번호

이 외에도 Altibase 기술지원 설명서의 오류와 누락된 부분 및 기타 기술적인 문제들에 대해서 이 주소로 보내주시면 정성껏 처리하겠습니다. 또한, 기술적인 부분과 관련하여 즉각적인 도움이 필요한 경우에도 고객서비스포털을 통해 서비스를 요청하시기 바랍니다.

여러분의 의견에 항상 감사드립니다.

</br>

# 1. altiShapeLoader 소개

이 장은 altiShapeLoader 사용을 위한 시스템 요구 사항과 설치 및 환경 설정에 관해 소개한다. 

### 개요

altiShapeLoader는 쉐이프 파일(Shapefile)<sup>[1](#shapefile)</sup> 가져오기 및 내보내기를 수행하는 도구로, 자바 기반의 오픈 소스 GeoTools를 기반으로 작성되었다. 

쉐이프 파일 가져오기(Import)는 쉐이프 파일에서 좌표 정보, 속성 정보 등 공간 데이터 정보를 Altibase 데이터베이스 테이블에 입력하는 것을 의미하고 쉐이프 파일 내보내기(Export)는 Altibase 데이터베이스 테이블에 저장된 공간 데이터 정보로 쉐이프 파일로 생성하는 것을 의미한다. 

### altiShapeLoader 버전

altiShapeLoader 버전은 1.0 이다. 버전 정보는 설치 디렉터리에 있는 version.info 파일에서 확인할 수 있다. 

### 시스템 요구 사항

altiShapeLoader 설치 및 실행에 필요한 시스템 사양과 altiShapeLoader와 호환하는 Altibase 서버 버전은 다음과 같다.

#### 하드웨어 요구 사항

- 메인 메모리 : 최소 512MB 이상, 4GB 이상 권고
- 디스크 : 20MB 이상의 설치 여유 공간

#### 소프트웨어 요구 사항

- Java : Oracle, OpenJDK 또는 IBM Java Runtime Environment 8 이상
- OS : Java 설치 및 구동 가능한 64bit OS

#### 호환되는 Altibase 서버 버전

- Altibase 7.1 이상

### 설치 및 제거

#### altiShapeLoader 설치

http://support.altibase.com/kr/product 에서 altiShapeLoader-1.0.zip 파일을 다운로드한다. altiShapeLoader를 실행할 곳에서 압축 파일을 해제하고 altiShapeLoader 디렉터리를 확인한다. 

altiShapeLoader 디렉터리 내 파일 구성은 아래와 같다.

```bash
[altibase@ /data/altibase/altiShapeLoader]$ ls -l
-rw-rw-r-- 1 altibase altibase 27438 2021-10-08 13:19 Altibase_altiShapeLoader_1_0_Release_Notes.pdf
-rw-r--r-- 1 altibase altibase  1318 2021-10-08 11:27 altiShapeLoader.bat
-rw-r--r-- 1 altibase altibase  1177 2021-10-08 11:27 altiShapeLoader.properties.release
-rw-rw-r-- 1 altibase altibase   867 2021-10-08 11:27 altiShapeLoader.sh
-rw-r--r-- 1 altibase altibase   798 2021-10-08 11:27 epsg.properties
drwxr-xr-x 2 altibase altibase  4096 2021-10-08 11:27 lib
drwxr-xr-x 2 altibase altibase  4096 2021-10-08 11:27 license
-rw-r--r-- 1 altibase altibase   560 2021-10-08 11:27 log4j2.xml
```

##### 실행 파일

altiShapeLoader를 실행하는 서버가 Windows 환경인 경우 altiShapeLoader.bat 을 이용하고 Unix/Linux 환경인 경우 altiShapeLoader.sh를 이용한다.

#### altiShapeLoader 환경 설정

##### JAVA_HOME 환경 변수

altiShapeLoader는 자바로 작성된 프로그램으로 JAVA_HOME 환경 변수를 설정해야 한다. altiShapeLoader 실행에 필요한 자바 버전은 [소프트웨어 요구 사항](#소프트웨어-요구-사항)을 참고한다. 

```bash
$ export JAVA_HOME=/usr/java/1.8
$ $JAVA_HOME/bin/java -version
java version "1.8.0_101"
Java(TM) SE Runtime Environment (build 1.8.0_101-b13)
Java HotSpot(TM) 64-Bit Server VM (build 25.101-b13, mixed mode)
```

##### altiShapeLoader 설정 파일(altiShapeLoader.properties)

altiShapeLoader 실행 시 altiShapeLoader 설정 파일(altiShapeLoader.properties)이 필요하다. altiShapeLoader 디렉터리 아래의 altiShapeLoader.properties.release 파일을 복사하여 생성하고 필요에 따라 편집해서 사용한다.

```bash
$ cd altiShapeLoader
$ cp -p altiShapeLoader.properties.release altiShapeLoader.properties
```

#### altiShapeLoader 제거

altiShapeLoader 디렉터리를 삭제한다.

```bash
$ rm -fr altiShapeLoader
```

</br>

# 2. altiShapeLoader 사용하기

이 장에서는 altiShapeLoader를 사용하는 방법에 관해 설명한다.

### 알티베이스 선행조건 - SRID 등록

Spatial Reference Identifier (SRID)는 공간 정보 객체의 위치를 나타내는 좌표계 시스템을 표현하는 고유한 값이다. Altibase 서버에서 SRID는 SYSTEM_.USER_SRS\_ 메타 테이블(이하 시노님 SPATIAL_REF_SYS)에 저장한다.

쉐이프 파일 가져오기 할 때 적절한 좌표 정보를 제공하기 위해 SRID가 필요하다. 쉐이프 파일 구성 요소 중 SRID 정보를 가지고 있는 파일은 .prj 파일이며, 이 SRID는 가져오기 수행하기 전 SPATIAL_REF_SYS 테이블에 미리 입력해야 한다. 

##### Altibase 서버에 등록된 SRID 확인 방법

Altibase 서버에 등록된 SRID는 아래 문장으로 확인할 수 있다. 

```sql
SELECT * FROM SPATIAL_REF_SYS;
```

##### Altibase 서버에 SRID를 등록하는 방법

.prj 파일이 가지고 있는 SRID가 Altibase 서버에 등록되어 있지 않은 경우 SYS_SPATIAL.ADD_SPATIAL_REF_SYS 프로시저를 이용해 등록한다.

- SYS_SPATIAL.ADD_SPATIAL_REF_SYS 프로시저는 Altibase 저장 패키지 SYS_SPATIAL을 생성해야 사용할 수 있다. Altibase 저장 패키지는 SYS 사용자 소유로 생성해야 한다. SYS_SPATIAL.ADD_SPATIAL_REF_SYS 프로시저가 없는 경우 altiShapeLoader 수행 시 아래와 같은 에러가 발생한다. 
  
  ```bash
  [Preparing & analyzing metadata]
  com.altibase.gis.lib.util.AltiException: Failed to ensure condtitions to insert a new SRID into database
  - Unable to find target package [SYS_SPATIAL]
  ```

- altiShapeLoader를 실행하는 데이터베이스 사용자가 ADD_SPATIAL_REF_SYS 프로시저를 수행하고자 할 경우 EXECUTE ANY PROCEDURE 권한이 필요하다. 
  
  ```sql
  -- 데이터베이스 사용자가 altitest 인 경우
  iSQL> GRANT EXECUTE ANY PROCEDURE TO altitest;
  ```

SYS_SPATIAL.ADD_SPATIAL_REF_SYS 사용 방법은 Spatial SQL Reference 매뉴얼을 참고한다.

- [Altibase 7.2 Spatial SQL Reference](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.2/kor/Spatial%20SQL%20Reference.md#add_spatial_ref_sys)
- [Altibase 7.1 Spatial SQL Reference](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Spatial%20SQL%20Reference.md#add_spatial_ref_sys)

### 실행 옵션

altiShapeLoader 수행하려면 Altibase 서버 접속 정보와 작업 종류, 테이블 이름, 쉐이프 파일 경로 등의 실행 옵션을 입력해야 한다. 실행 옵션 입력은 2가지 방법을 제공한다.

#### 실행 옵션 입력 방법

- **명령 줄 인터페이스(Command Line Interface, CLI)  방식**
  
  명령 줄 인터페이스에서 altiShapeLoader 실행 옵션을 입력하는 일괄식 (Batch mode) 방식으로 쉐이프 파일마다 다른 입력 옵션이 필요한 경우 사용한다. 실행 후 필요한 정보를 차례로 입력하는 대화식(Interactive mode) 방식은 지원하지 않는다. 

- **altiShapeLoader 설정 파일 방식**
  
  altiShapeLoader 설정 파일인 altiShapeLoader.properties 파일을 읽어 실행 옵션 값을 적용한다. 이 파일은 altiShapeLoader.properties.release 파일을 altiShapeLoader.properties 이름으로 복사해서 생성하며altiShapeLoader 실행 파일(altiShapeLoader.sh 또는 altiShapeLoader.bat)과 같은 디렉터리에 있어야 한다.
  
  Altibase 서버 접속 정보 및 공통 옵션들은 altiShapeLoader 설정 파일을 이용한다.

#### 실행 옵션 입력 우선 순위

실행 옵션 값은 아래 순서로 적용한다. 

1) 명령 줄 인터페이스
2) altiShapeLoader 설정 파일
3) 정의된 기본값 순으로 적용한다. 

예를 들어 쉐이프 파일 가져오기에서 테이블 이름을 명령 줄 옵션에 T1을 입력하고 altiShapeLoader 설정 파일에서 T2로 입력한 경우 우선순위가 높은 명령 줄 옵션값인 T1 테이블을 작업 대상으로 선택한다. 앞 두 가지 입력 방법에서 입력하지 않은 경우 altiShapeLoader에 정의된 기본값인 .shp 파일 이름을 테이블 이름으로 적용한다.

아래는 Altibase 서버 접속 정보를 포함한 공통적인 가져오기 옵션은 altiShapeLoader 설정 파일에 입력하고 작업 종류, 테이블 이름, 개별 쉐이프 파일 경로는 명령 줄 인터페이스에서 입력한 예제이다.

```bash
% cat ./altiShapeLoader.properties.release
###############################################
# DB connection arguments 
###############################################
DB_IP         = 127.0.0.1
DB_PORT        = 20300
DB_NAME        = mydb
DB_USER     = SYS
DB_PASSWORD    = MANAGER
JDBC_PATH     = ${ALTIBASE_HOME}/lib/Altibase.jar

###############################################
# General options
###############################################
# CREATE_TABLE      = T
# TABLE_TBS         = SYS_TBS_DISK_DATA
# CREATE_INDEX      = F
# INDEX_TBS         = SYS_TBS_DISK_DATA
# DBF_CHAR          = EUC-KR
# ENDIAN            = B
# CASE_SENSIITIVE   = F
# CREATE_BAD        = F

###############################################
# Performance options
###############################################
# PARALLEL         = 4
# COMMIT        = 1000

###############################################
# Mandatory arguments
###############################################
# OPERATION     = import 
### Use / instead of \ when specifying Windows file path.
# SHAPE_FILE    = ./sample.shp
# TABLE_NAME    = T1

###############################################
# Special options
###############################################
#GEO_COL_SIZE   = 103809024
#SRID           = 2097

% cp altiShapeLoader.properties.release altiShapeLoader.properties

% ./altiShapeLoader.sh -o import -f subway_station.shp -T subway_station
-----------------------------------------------------------------
        altiShapeLoader Release 1.0
        Shapefile import/export utility for Altibase datatbase
        Copyright(c) 2000, ALTIBASE Corporation or its subsidiaries.
        All Rights Reserved.
-----------------------------------------------------------------
...
```

### 필수 옵션

필수 옵션은 명령 줄 인터페이스와 altiShapeLoader 설정 파일, 둘 중 한 곳에 반드시 입력해야 하는 정보이다. 입력하지 않으면 오류를 출력하고 작업을 중단한다. "명령줄 옵션"은 명령 줄 인터페이스에서 *-option_name* 형식으로, ''altiShapeLoader 설정 파일 옵션''은 altiShapeLoader 설정 파일에서 *OPTION_NAME=value* 형식으로 입력한다. 

아래 두 가지 옵션은 일반적으로 쉐이프 파일마다 다른 값을 가지므로 명령 줄 인터페이스에서 직접 입력하는 것을 권장한다.

| 명령줄 옵션 | altiShapeLoader 설정 파일 옵션 | 의미                                                                                                                                                                                                                                                                                                                                                                                                                            |
|:------ |:------------------------ |:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| -o     | OPERATION                | altiShapeLoader 작업 종류를 입력한다. import 또는 export를 입력할 수 있다.<br />import는 쉐이프 파일에서 공간 데이터 정보를 테이블로 입력한다. import는 세 가지 방법으로 이용할 수 있으며 보다 자세한 내용은 [쉐이프 파일 가져오기(Import)](#쉐이프-파일-가져오기import)절을 참고한다.<br />    - 하나의 쉐이프 파일을 하나의 테이블에 입력<br />    - 디렉터리 내 여러 쉐이프 파일을 하나의 테이블에 입력<br />    - 디렉터리 내 여러 쉐이프 파일을 각각의 개별 테이블에 입력<br />export는 테이블에 저장된 공간 데이터를 쉐이프 파일에 저장한다. 보다 자세한 설명은 [쉐이프 파일 내보내기(Export)](#쉐이프-파일-내보내기export)를 참고한다. |
| -f     | SHAPE_FILE               | 쉐이프 파일이 위치한 경로 또는 경로를 포함한 .shp 파일을 지정한다. <br />- 경로를 포함한 .shp 파일을 지정 예 : -f subway_station.shp<br />- 쉐이프 파일이 위치한 경로 지정 예 : -f multi2single                                                                                                                                                                                                                                                                                   |

Altibase 서버 접속 정보는 필수 옵션이다. 반복적으로 사용한다면 altiShapeLoader 설정 파일에 추가한다.

| 명령줄 옵션 | altiShapeLoader 설정 파일 옵션 | 의미                                                         |
|:------ |:------------------------ |:---------------------------------------------------------- |
| -s     | DB_IP                    | Altibase 서버를 설치한 OS의 호스트 이름(hostname) 또는 IP 주소             |
| -port  | DB_PORT                  | Altibase 서버의 서비스 포트 번호                                     |
| -d     | DB_NAME                  | 데이터베이스 이름 (예, mydb)                                        |
| -u     | DB_USER                  | 데이터베이스 사용자 ID                                              |
| -p     | DB_PASSWORD              | 사용자 ID와 일치하는 암호                                            |
| -j     | JDBC_PATH                | 접속에 사용할 Altibase JDBC 드라이버 파일 경로 <br />(예, ./Altibase.jar) |

### 선택 옵션

선택 옵션은 작업 종류에 따라 사용자가 선택적으로 입력하는 정보이다. 명령 줄 인터페이스이나 altiShapeLoader 설정 파일 어느 곳에도 입력하지 않으면 정의된 기본값을 사용한다. 

| 명령줄 옵션          | altiShapeLoader 설정 파일 옵션 | 의미                                                                                                                                                                                                                                                                                | 기본값         |
|:--------------- |:------------------------ |:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |:-----------:|
| -t              | TABLE_NAME               | 테이블 이름을 지정한다.<br />-o 옵션이 import 경우 공간 데이터를 입력할 테이블을 의미한다. -create_table 옵션이 T 이면서 이 옵션을 생략하면  테이블 이름은 .shp 파일 이름을 사용한다. 예를 들어 .shp 파일 이름이 test.shp이면 테이블 이름은 test이다. 대소문자 구분은 case_sensitive 옵션 설정에 따른다.<br />-o 옵션이 export 경우 공간 데이터가 저장된 테이블을 의미한다.                            | 쉐이프 파일 이름   |
| -create_table   | CREATE_TABLE             | -o 옵션이 import 경우 테이블 생성 여부를 설정한다.<br />T 또는 F를 입력할 수 있다.<br />T는 FID(Feature ID)를 첫 번째 컬럼으로 가진 테이블을 생성한다. 또한 레코드마다 고유한 FID 값 입력을 위해 시퀀스(SEQ\_*table_name*\_FID) 객체를 생성한다. 같은 이름의 시퀀스 객체가 데이터베이스에 존재하면 생성하지 않는다.<br />F는 테이블을 생성하지 않는다.                                            | T           |
| -table_tbs      | TABLE_TBS                | 테이블이 생성될 테이블스페이스 이름을 입력한다. 이 옵션을 생략하면 데이터베이스 사용자의 기본 테이블스페이스에 생성한다. -create_table 옵션이 T일 때만 적용한다.                                                                                                                                                                                 | 기본 테이블스페이스  |
| -create_index   | CREATE_INDEX             | 공간 데이터 타입 컬럼에 인덱스 생성 여부를 설정한다.<br />T 또는 F를 입력할 수 있다.<br />T는 인덱스를 생성하고 F는 생성하지 않는다. -create_table 옵션이 T일 때만 적용한다.                                                                                                                                                                | F           |
| -index_tbs      | INDEX_TBS                | 인덱스가 생성될 테이블스페이스 이름을 입력한다. 이 옵션을 생략하면 데이터베이스 사용자의 기본 테이블스페이스에 생성한다. -create_index 옵션이 T일 때만 적용한다.                                                                                                                                                                                 | 기본 테이블스페이스  |
| -dbf_char       | DBF_CHAR                 | 쉐이프 파일 가져오기 및 내보내기에서 .dbf 파일을 읽을 때 인코딩할 캐릭터셋(character-Set)을 설정한다. altiShapeLoader 설정 파일과 컬럼 이름 매핑 파일(-col_map_file 옵션 참고)을 읽을 때도 같은 캐릭터셋을 적용한다.                                                                                                                                  | EUC-KR      |
| -endian         | ENDIAN                   | 쉐이프 파일의 endian 종류.<br />B 또는 L 을 입력할 수 있다. B는 Big Endian이고 L은 Little Endian이다. <br />-o 옵션이 import 인 경우 적용한다.                                                                                                                                                                     | B           |
| -case_sensitive | CASE_SENSITIVE           | 테이블/컬럼 이름 대소문자 구분 여부를 설정한다.<br />T 또는 F 를 입력할 수 있다. <br />T는 사용자 입력값을 그대로 데이터베이스에 입력하고 F는 대문자로 변경하여 입력한다.                                                                                                                                                                         | F           |
| -col_map_file   | COL_MAP_FILE             | 컬럼 이름 매핑 파일 경로를 설정한다.<br />컬럼 이름 매핑 파일은 쉐이프 파일에서 정의한 컬럼 이름과 다르게 테이블의 컬럼 이름을 생성할 때, 사용자가 Key=value 형식으로 작성하는 텍스트 파일이다. <br />shpColName=dbColName 형식으로 작성하며 값이 없으면 쉐이프 파일에서 정의한 컬럼 이름으로 테이블을 생성한다.  대소문자를 구분은 -case_sensitive 옵션 설정에 따른다.                                          | 쉐이프 파일 컬럼이름 |
| -create_bad     | CREATE_BAD               | 가져오기 또는 내보내기가 실패한 레코드를 기록하기 위한 bad 파일 생성 여부를 설정한다. T 또는 F 를 입력할 수 있다.<br />T는 가져오기 또는 내보내기가 실패한 레코드를 지정한 파일에 기록한다. bad 파일 이름은 *쉐이프 파일 이름*.bad 형태이며 -o 옵션이 import 경우 parallel 옵션 값만큼 bad 파일이 생성될 수 있다. 실패한 레코드가 한 건도 없다면 bad 파일은 생성되지 않는다. F는 가져오기 또는 내보내기가 실패해도 bad 파일을 생성하지 않는다. | F           |

### 성능 옵션

altiShapeLoader의 가져오기 수행 성능을 조정하기 위한 옵션이다. 최대 성능을 위해 altiShapeLoader를 설치한 시스템의 CPU와 메모리 사양에 따라 적절한 조정이 필요하다. 

| 명령줄 옵션    | altiShapeLoader 설정 파일 옵션 | 의미                                                                                                                                                                                                                                                                                     | 기본값  |
|:--------- |:------------------------ |:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |:----:|
| -parallel | PARALLEL                 | 데이터 입력 작업 쓰레드 수. <br />가져오기 수행 성능 조정을 위한 옵션이다. altiShapeLoader는 생산자-소비자 패턴(Producer Consumer Pattern)의 멀티 쓰레드 구조로, 쉐이프 파일을 읽어 큐에 넣는 1개의 쓰레드(생산자)와 큐에서 데이터를 읽어 데이터베이스에 입력하는 N개의 쓰레드(소비자)로 구성된다. 여기서 parallel 옵션은 N개의 소비자 쓰레드를 의미한다. 최소값은 1이고 최대값에 제한이 없다. 이 옵션을 사용하지 않은 경우 기본값 4를 적용한다. | 4    |
| -commit   | COMMIT                   | 데이터 입력 시 커밋 단위. <br />가져오기 수행 성능 조정을 위한 옵션이다. 데이터 입력 작업 쓰레드가 몇 개 레코드 단위로 커밋할 것인지를 결정한다. 최소값은 1이고 최대값에 제한이 없다. 이 옵션을 사용하지 않은 경우 기본값 1000을 적용한다.                                                                                                                                         | 1000 |

### 특수 옵션

특수 옵션은 특별 목적을 위해 제공하는 옵션들로 일반적인 경우에는 사용하지 않기를 권장한다.

| 명령줄 옵션        | altiShapeLoader 설정 파일 옵션 | 의미                                                                                                                                       | 기본값                |
|:------------- |:------------------------ |:---------------------------------------------------------------------------------------------------------------------------------------- |:------------------:|
| -srid         | SRID                     | 사용자 강제 지정 SRID 값. <br />altiShapeLoader가 .prj 파일을 처리하지 못하는 경우 강제로 지정할 SRID를 설정한다. 상세 방법은 [SRID 가져오기 및 내보내기](#SRID-가져오기-및-내보내기) 부분을 참고한다. | N/A                |
| -geo_col_size | GEO_COL_SIZE             | 테이블 생성시 공간(geometry) 데이터 컬럼의 precision 지정한다. 단위는 byte 이다. 기본값보다 큰 컬럼이 필요할 때만 사용한다.                                                       | 103,809,024 (99MB) |

### 쉐이프 파일 가져오기(Import)

가져오기는 쉐이프 파일 구성 요소 중 .shp 파일의 공간 정보와 .dbf 파일의 속성 정보를 데이터베이스에 입력하는 작업이다. 가져오기는 쉐이프 파일을 구성하는 .shp, .shx, .dbf, .prj 등의 파일을 필요로 한다. 가져오기 수행 전 SRID가 Altibase 서버에 등록되어 있어야 한다. 이에 관한 설명은 [알티베이스 선행조건 - SRID 등록](#알티베이스-선행조건---SRID-등록)를 참고한다. 

가져오기는 크게 세 가지로 구분할 수 있다.

1. 하나의 쉐이프 파일을 하나의 테이블로 가져오기 (Single shapefile into single table)
2. 여러 쉐이프 파일을 하나의 테이블로 가져오기 (Multiple shapefiles into single table)
3. 여러 쉐이프 파일을 각각의 개별 테이블로 가져오기 (Multiple shapefiles into each tables)

각 작업 별 필수 실행 옵션은 아래와 같다. (O : 필수, △ : 선택, X : 입력 불가)

| 명령줄 옵션 | altiShapeLoader 설정 파일 옵션 | 하나의 쉐이프 파일을 하나의 테이블로 가져오기 | 여러 쉐이프 파일을 하나의 테이블로 가져오기 | 여러 쉐이프 파일을 각각의 개별 테이블로 가져오기 |
|:------ |:------------------------ |:-------------------------:|:------------------------:|:---------------------------:|
| -o     | OPERATION                | O                         | O                        | O                           |
| -f     | SHAPE_FILE               | O                         | O                        | O                           |
| -t     | TABLE_NAME               | △                         | O                        | X                           |

#### 하나의 쉐이프 파일을 하나의 테이블로 가져오기 (Single shapefile into single table)

가장 일반적인 경우로 .shp, .shx, .dbf 등으로 구성된 하나의 쉐이프 파일을 하나의 테이블로 가져오기를 수행한다. OPERATION(-o)과 SHAPE_FILE(-f)는 필수 옵션으로 SHAPE_FILE(-f) 옵션에 .shp 확장자 파일을 입력한다. TABLE_NAME (-t)은 선택 옵션이다.

아래는 subway_station.shb, subway_station.shx, subway_station.dbf 로 구성된 하나의 쉐이프 파일을 하나의 테이블로 가져오기를 수행한 예제이다. 

```bash
$ ls -l data/subway_station.*
-rw-r--r-- 1 altibase altibase 287186 Apr 28  2021 data/subway_station.dbf
-rw-r--r-- 1 altibase altibase    758 Apr 28  2021 data/subway_station.prj
-rw-r--r-- 1 altibase altibase    758 Apr 28  2021 data/subway_station.prj.bak
-rw-r--r-- 1 altibase altibase   3052 Apr 28  2021 data/subway_station.sbn
-rw-r--r-- 1 altibase altibase   7716 Apr 28  2021 data/subway_station.shp
-rw-r--r-- 1 altibase altibase   2276 Apr 28  2021 data/subway_station.shx

$ ./altiShapeLoader.sh -o import -f data/subway_station.shp
-----------------------------------------------------------------
        altiShapeLoader Release 1.0
        Shapefile import/export utility for Altibase datatbase
        Copyright(c) 2000, ALTIBASE Corporation or its subsidiaries.
        All Rights Reserved.
-----------------------------------------------------------------
Importing shp requested: /home/altiShapeLoader/data/subway_station.shp
[Preparing & analyzing metadata]
[CREATE SEQUENCE] CREATE SEQUENCE "ALTITEST"."SEQ_SUBWAY_STATION_FID" START WITH 1 INCREMENT BY 1 MINVALUE 1 CYCLE
[CREATE SEQUENCE] Success
[CREATE TABLE] CREATE TABLE "ALTITEST"."SUBWAY_STATION" ( FID BIGINT DEFAULT "SEQ_SUBWAY_STATION_FID".NEXTVAL PRIMARY KEY, "THE_GEOM" GEOMETRY(103809024) SRID 2097, "XCOORD" DOUBLE, "YCOORD" DOUBLE, "GUBUN" VARCHAR(254), "GUBUN2" VARCHAR(254), "NAM" VARCHAR(254), "NAM2" VARCHAR(254) )
[CREATE TABLE] Success
[Importing data started] A single dot (.) means 1,000 records processed.
.
[Importing data done]
<summary>
[File  ] /home/altiShapeLoader/data/subway_station.shp 
[Status] [Read] Success, [Write] Success 
[Read  ] Total:272, Success:272, Fail:0 
[Write ] Total:272, Success:272, Fail:0 
[Time  ] 0:00:00.138 (HH:MM:SS.sss)
```

-t 옵션으로 테이블 이름을 명시하지 않았지만 altiShapeLoader 설정 파일(altiShapeLoader.properties)에 CREATE_TABLE=T 이 기본 설정으로 포함되어 있어 SEQ_SUBWAY_STATION_FID 시퀀스와 SUBWAY_STATION 테이블을 생성하고 SUBWAY_STATION 테이블에 공간 데이터를 입력한다. 

[DATA IMPORT start]와 [DATA IMPORT done] 사이의 점(dot)은 레코드 1,000개 단위로 출력한다. 본 예제의 레코드 수는 32개로 1개가 출력되었다. 

수행 결과는 \<summary>에 출력한다.

- [Status] [Read] Success, [Write] Success
  - 쉐이프 파일 읽기 및 테이블 입력이 모두 성공하였음을 의미한다.
- [Read  ] Total:272, Success:272, Fail:0 
  - 272개의 데이터를 성공적으로 읽었음을 의미한다.
- [Write ] Total:272, Success:272, Fail:0 
  - 읽은 272개의 데이터를 오류없이 테이블에 입력하였음을 의미한다. 
- [Time  ] 0:00:00.124 
  - 쉐이프 파일 읽기 및 테이블 입력 소요 시간으로  hh:mm:ss.sss 형식으로 출력한다.

#### 여러 쉐이프 파일을 하나의 테이블로 가져오기 (Multiple shapefiles into single table)

여러 쉐이프 파일을 하나의 테이블로 입력한다. 쉐이프 파일들은 같은 디렉터리 내에 있어야 하며 모두 같은 스키마를 가져야 한다. 필수 옵션은 OPERATION(-o), SHAPE_FILE(-f),TABLE_NAME (-t) 이다. SHAPE_FILE(-f) 옵션에 디렉터리 경로를 입력한다. 

아래 예제는 multi2single 디렉터리에 있는 3개의 쉐이프 파일을 MULTI2SINGLE 테이블에 가져오기를 수행하는 과정이다. altiShapeLoader 설정 파일에 CREATE_TABLE=T 이 기본 설정으로 포함되어 있어 SEQ_MULTI2SINGLE_FID 시퀀스와 MULTI2SINGLE 테이블을 생성하고 MULTI2SINGLE 테이블에 가져오기를 수행한다.

```bash
$ ls -l data/multi2single
합계 100
-rw-r--r-- 1 altibase altibase   426 2021-04-28 09:07 river.dbf
-rw-r--r-- 1 altibase altibase   758 2021-05-14 09:33 river.prj
-rw-r--r-- 1 altibase altibase 20648 2021-04-28 09:07 river.shp
-rw-r--r-- 1 altibase altibase   340 2021-04-28 09:07 river.shx
-rw-r--r-- 1 altibase altibase   645 2021-04-28 09:07 river2.dbf
-rw-r--r-- 1 altibase altibase   758 2021-05-14 09:34 river2.prj
-rw-r--r-- 1 altibase altibase 20080 2021-04-28 09:07 river2.shp
-rw-r--r-- 1 altibase altibase   332 2021-04-28 09:07 river2.shx
-rw-r--r-- 1 altibase altibase   645 2021-04-28 09:07 river3.dbf
-rw-r--r-- 1 altibase altibase   758 2021-05-14 09:34 river3.prj
-rw-r--r-- 1 altibase altibase 20080 2021-04-28 09:07 river3.shp
-rw-r--r-- 1 altibase altibase   332 2021-04-28 09:07 river3.shx

$ ./altiShapeLoader.sh -o import -f data/multi2single -t MULTI2SINGLE
-----------------------------------------------------------------
        altiShapeLoader Release 1.0
        Shapefile import/export utility for Altibase datatbase
        Copyright(c) 2000, ALTIBASE Corporation or its subsidiaries.
        All Rights Reserved.
-----------------------------------------------------------------
Importing shp requested: /home/altiShapeLoader/data/multi2single/river.shp
[Preparing & analyzing metadata]
[CREATE SEQUENCE] CREATE SEQUENCE "ALTITEST"."SEQ_MULTI2SINGLE_FID" START WITH 1 INCREMENT BY 1 MINVALUE 1 CYCLE
[CREATE SEQUENCE] Success
[CREATE TABLE] CREATE TABLE "ALTITEST"."MULTI2SINGLE" ( FID BIGINT DEFAULT "SEQ_MULTI2SINGLE_FID".NEXTVAL PRIMARY KEY, "THE_GEOM" GEOMETRY(103809024) SRID 2097, "ID" BIGINT )
[CREATE TABLE] Success
[Importing data started] A single dot (.) means 1,000 records processed.
.
[Importing data done]
<summary>
[File  ] /home/altiShapeLoader/data/multi2single/river.shp 
[Status] [Read] Success, [Write] Success 
[Read  ] Total:30, Success:30, Fail:0 
[Write ] Total:30, Success:30, Fail:0 
[Time  ] 0:00:00.071 (HH:MM:SS.sss)

Importing shp requested: /home/altiShapeLoader/data/multi2single/river2.shp
[Preparing & analyzing metadata]
[Importing data started] A single dot (.) means 1,000 records processed.
.
[Importing data done]
<summary>
[File  ] /home/altiShapeLoader/data/multi2single/river2.shp 
[Status] [Read] Success, [Write] Success 
[Read  ] Total:29, Success:29, Fail:0 
[Write ] Total:29, Success:29, Fail:0 
[Time  ] 0:00:00.029 (HH:MM:SS.sss)

Importing shp requested: /home/altiShapeLoader/data/multi2single/river3.shp
[Preparing & analyzing metadata]
[Importing data started] A single dot (.) means 1,000 records processed.
.
[Importing data done]
<summary>
[File  ] /home/altiShapeLoader/data/multi2single/river3.shp 
[Status] [Read] Success, [Write] Success 
[Read  ] Total:29, Success:29, Fail:0 
[Write ] Total:29, Success:29, Fail:0 
[Time  ] 0:00:00.053 (HH:MM:SS.sss)
```

#### 여러 쉐이프 파일을 각각의 개별 테이블로 가져오기 (Multiple shapefiles into each tables)

.shp, .shx, .dbf 등으로 구성된 여러 쉐이프 파일을 각각의 테이블로 입력할 수 있다. 쉐이프 파일들은 같은 디렉터리 내에 있어야 하며 모두 같은 스키마를 가져야 한다. 필수 옵션은 OPERATION(-o), SHAPE_FILE(-f) 이고 SHAPE_FILE(-f) 옵션에 디렉터리 경로를 입력한다. 이 경우 파일 이름을 테이블 이름으로 사용하기 때문에 TABLE_NAME (-t)은 사용하지 않는다. 이 옵션을 사용할 경우 '여러 쉐이프 파일을 하나의 테이블로 가져오기'를 수행한다. 

다음은 multi2multi 디렉터리에 있는 네 개의 쉐이프 파일들을 각각 4개의 테이블에 가져오기를 수행하는 예제이다. altiShapeLoader 설정 파일에 CREATE_TABLE=T 이 기본 설정으로 포함되어 있어 시퀀스 4개와 BUILDING, FIRESTATION, HEALTHCENTER, POLICESTATION 테이블을 생성하고 가져오기를 수행한다.

```bash
$ ls -l data/multi2multi
합계 16064
-rw-r--r-- 1 altibase altibase 10877274 2021-04-28 09:07 building.dbf
-rw-r--r-- 1 altibase altibase      758 2021-04-28 09:07 building.prj
-rw-r--r-- 1 altibase altibase  5234704 2021-04-28 09:07 building.shp
-rw-r--r-- 1 altibase altibase   204356 2021-04-28 09:07 building.shx
-rw-r--r-- 1 altibase altibase     6538 2021-04-28 09:07 firestation.dbf
-rw-r--r-- 1 altibase altibase      758 2021-04-28 09:07 firestation.prj
-rw-r--r-- 1 altibase altibase      328 2021-04-28 09:07 firestation.qix
-rw-r--r-- 1 altibase altibase      332 2021-04-28 09:07 firestation.sbn
-rw-r--r-- 1 altibase altibase      124 2021-04-28 09:07 firestation.sbx
-rw-r--r-- 1 altibase altibase      744 2021-04-28 09:07 firestation.shp
-rw-r--r-- 1 altibase altibase      284 2021-04-28 09:07 firestation.shx
-rw-r--r-- 1 altibase altibase     6818 2021-04-28 09:07 healthcenter.dbf
-rw-r--r-- 1 altibase altibase      758 2021-04-28 09:07 healthcenter.prj
-rw-r--r-- 1 altibase altibase      332 2021-04-28 09:07 healthcenter.qix
-rw-r--r-- 1 altibase altibase      340 2021-04-28 09:07 healthcenter.sbn
-rw-r--r-- 1 altibase altibase      124 2021-04-28 09:07 healthcenter.sbx
-rw-r--r-- 1 altibase altibase      772 2021-04-28 09:07 healthcenter.shp
-rw-r--r-- 1 altibase altibase      292 2021-04-28 09:07 healthcenter.shx
-rw-r--r-- 1 altibase altibase    11202 2021-04-28 09:07 policestation.dbf
-rw-r--r-- 1 altibase altibase      758 2021-04-28 09:07 policestation.prj
-rw-r--r-- 1 altibase altibase      364 2021-04-28 09:07 policestation.qix
-rw-r--r-- 1 altibase altibase      468 2021-04-28 09:07 policestation.sbn
-rw-r--r-- 1 altibase altibase      156 2021-04-28 09:07 policestation.sbx
-rw-r--r-- 1 altibase altibase      996 2021-04-28 09:07 policestation.shp
-rw-r--r-- 1 altibase altibase      356 2021-04-28 09:07 policestation.shx

$ ./altiShapeLoader.sh -o import -f data/multi2multi
-----------------------------------------------------------------
        altiShapeLoader Release 1.0
        Shapefile import/export utility for Altibase datatbase
        Copyright(c) 2000, ALTIBASE Corporation or its subsidiaries.
        All Rights Reserved.
-----------------------------------------------------------------
Importing shp requested: /home/altiShapeLoader/data/multi2multi/building.shp
[Preparing & analyzing metadata]
[CREATE SEQUENCE] CREATE SEQUENCE "ALTITEST"."SEQ_BUILDING_FID" START WITH 1 INCREMENT BY 1 MINVALUE 1 CYCLE
[CREATE SEQUENCE] Success
[CREATE TABLE] CREATE TABLE "ALTITEST"."BUILDING" ( FID BIGINT DEFAULT "SEQ_BUILDING_FID".NEXTVAL PRIMARY KEY, "THE_GEOM" GEOMETRY(103809024) SRID 2097, "UFID" VARCHAR(28), "BLD_NM" VARCHAR(100), "DONG_NM" VARCHAR(100), "GRND_FLR" INTEGER, "UGRND_FLR" INTEGER, "PNU" VARCHAR(19), "ARCHAREA" DOUBLE, "TOTALAREA" DOUBLE, "PLATAREA" DOUBLE, "HEIGHT" DOUBLE, "STRCT_CD" VARCHAR(2), "USABILITY" VARCHAR(5), "BC_RAT" DOUBLE, "VL_RAT" DOUBLE, "BLDRGST_PK" VARCHAR(28), "USEAPR_DAY" VARCHAR(8), "REGIST_DAY" VARCHAR(8), "GB_CD" VARCHAR(2), "VIOL_BD_YN" VARCHAR(1) )
[CREATE TABLE] Success
[Importing data started] A single dot (.) means 1,000 records processed.
..........................
[Importing data done]
<summary>
[File  ] /home/altiShapeLoader/data/multi2multi/building.shp 
[Status] [Read] Success, [Write] Success 
[Read  ] Total:25,532, Success:25,532, Fail:0 
[Write ] Total:25,532, Success:25,532, Fail:0 
[Time  ] 0:00:00.951 (HH:MM:SS.sss)

Importing shp requested: /home/altiShapeLoader/data/multi2multi/firestation.shp
[Preparing & analyzing metadata]
[CREATE SEQUENCE] CREATE SEQUENCE "ALTITEST"."SEQ_FIRESTATION_FID" START WITH 1 INCREMENT BY 1 MINVALUE 1 CYCLE
[CREATE SEQUENCE] Success
[CREATE TABLE] CREATE TABLE "ALTITEST"."FIRESTATION" ( FID BIGINT DEFAULT "SEQ_FIRESTATION_FID".NEXTVAL PRIMARY KEY, "THE_GEOM" GEOMETRY(103809024) SRID 2097, "NAM" VARCHAR(25), "ADDR" VARCHAR(254) )
[CREATE TABLE] Success
[Importing data started] A single dot (.) means 1,000 records processed.
.
[Importing data done]
<summary>
[File  ] /home/altiShapeLoader/data/multi2multi/firestation.shp 
[Status] [Read] Success, [Write] Success 
[Read  ] Total:23, Success:23, Fail:0 
[Write ] Total:23, Success:23, Fail:0 
[Time  ] 0:00:00.053 (HH:MM:SS.sss)

Importing shp requested: /home/altiShapeLoader/data/multi2multi/healthcenter.shp
[Preparing & analyzing metadata]
[CREATE SEQUENCE] CREATE SEQUENCE "ALTITEST"."SEQ_HEALTHCENTER_FID" START WITH 1 INCREMENT BY 1 MINVALUE 1 CYCLE
[CREATE SEQUENCE] Success
[CREATE TABLE] CREATE TABLE "ALTITEST"."HEALTHCENTER" ( FID BIGINT DEFAULT "SEQ_HEALTHCENTER_FID".NEXTVAL PRIMARY KEY, "THE_GEOM" GEOMETRY(103809024) SRID 2097, "NAM" VARCHAR(25), "ADDR" VARCHAR(254) )
[CREATE TABLE] Success
[Importing data started] A single dot (.) means 1,000 records processed.
.
[Importing data done]
<summary>
[File  ] /home/altiShapeLoader/data/multi2multi/healthcenter.shp 
[Status] [Read] Success, [Write] Success 
[Read  ] Total:24, Success:24, Fail:0 
[Write ] Total:24, Success:24, Fail:0 
[Time  ] 0:00:00.051 (HH:MM:SS.sss)

Importing shp requested: /home/altiShapeLoader/data/multi2multi/policestation.shp
[Preparing & analyzing metadata]
[CREATE SEQUENCE] CREATE SEQUENCE "ALTITEST"."SEQ_POLICESTATION_FID" START WITH 1 INCREMENT BY 1 MINVALUE 1 CYCLE
[CREATE SEQUENCE] Success
[CREATE TABLE] CREATE TABLE "ALTITEST"."POLICESTATION" ( FID BIGINT DEFAULT "SEQ_POLICESTATION_FID".NEXTVAL PRIMARY KEY, "THE_GEOM" GEOMETRY(103809024) SRID 2097, "NAM" VARCHAR(50), "ADDR" VARCHAR(254), "TEL" VARCHAR(20), "FAX" VARCHAR(20) )
[CREATE TABLE] Success
[Importing data started] A single dot (.) means 1,000 records processed.
.
[Importing data done]
<summary>
[File  ] /home/altiShapeLoader/data/multi2multi/policestation.shp 
[Status] [Read] Success, [Write] Success 
[Read  ] Total:32, Success:32, Fail:0 
[Write ] Total:32, Success:32, Fail:0 
[Time  ] 0:00:00.048 (HH:MM:SS.sss)
```

### 쉐이프 파일 내보내기(Export)

내보내기는 테이블에 저장된 공간 데이터 정보를 쉐이프 파일로 저장하는 기능이다. 내보내기를 수행하면 쉐이프 파일을 구성하는 .shp, .shx, .dbf 등의 파일들을 생성한다. altiShapeLoader는 테이블에 저장된 공간 객체의 SRID와 SPATIAL_REF_SYS 메타 테이블을 참조하여 GeoTools 라이브러리를 통해 .prj 파일을 생성한다. 테이블의 FID 컬럼은 내보내기 대상이 아니므로 쉐이프 파일에 저장하지 않는다. 

필수 옵션은 OPERATION(-o)과 SHAPE_FILE(-f) 이며 SHAPE_FILE(-f)  옵션에 .shp 확장자 파일을 입력한다. 선택 옵션인 TABLE_NAME (-t)을 생략하면 테이블 이름을 쉐이프 파일 이름으로 사용한다. 

#### 내보내기 예제

다음은 POLICESTATION 테이블에 저장된 공간 데이터 정보를 policestation2.shp 파일에 내보내기를 수행하는 예제이다. 

```bash
$ ls -l policestation2*
ls: cannot access policestation2*: No such file or directory

$ ./altiShapeLoader.sh -o export -t POLICESTATION -f ./policestation2.shp
-----------------------------------------------------------------
        altiShapeLoader Release 1.0
        Shapefile import/export utility for Altibase datatbase
        Copyright(c) 2000, ALTIBASE Corporation or its subsidiaries.
        All Rights Reserved.
-----------------------------------------------------------------
Exporting requested: ./policestation2.shp
[Preparing files & analyzing metadata]
[Exporting data started] A single dot (.) means 1,000 records processed.
.
[Exporting data done]
<summary>
[File  ] ./policestation2.shp 
[Status] [Read] Success, [Write] Success 
[Read  ] Total:32, Success:32, Fail:0 
[Write ] Total:32, Success:32, Fail:0 
[Time  ] 0:00:00.342 (HH:MM:SS.sss)
```

\<commit started>와 \<finished> 사이의 점(dot)은 레코드 1,000개 단위로 출력한다. 이 예제의 데이터는 32개 레코드로 1개가 출력되었다.

수행 결과는 \<summary>에 출력한다. 

- [Status] [Read] Success, [Write] Success
  - 테이블 조회 및 파일 기록 모두 성공적으로 수행하였음을 의미한다.
- [Read  ] Total:32, Success:32, Fail:0
  - 테이블 조회에서 32개 데이터를 성공적으로 읽었음을 의미한다. 
- [Write ] Total:32, Success:32, Fail:0
  - 테이블에서 조회한 32개 데이터를 쉐이프 파일에 오류없이 기록하였음을 의미한다.
- [Time  ] 0:00:01.287
  - 테이블 조회 및 파일 기록 소요 시간으로 hh:mm:ss.sss 형식으로 출력한다. 

export 수행 후 쉐이프 파일 생성 결과는 아래와 같다.

```bash
$ ls -l policestation2*
-rw-rw-rw- 1 altibase altibase 11201 Nov 21 21:38 policestation2.dbf
-rw-rw-rw- 1 altibase altibase   397 Nov 21 21:38 policestation2.fix
-rw-rw-rw- 1 altibase altibase   737 Nov 21 21:38 policestation2.prj
-rw-rw-rw- 1 altibase altibase   996 Nov 21 21:38 policestation2.shp
-rw-rw-rw- 1 altibase altibase   356 Nov 21 21:38 policestation2.shx

$ file policestation2*
policestation2.dbf: DBase 3 data file (32 records)
policestation2.fix: data
policestation2.prj: ASCII text, with very long lines, with no line terminators
policestation2.shp: ESRI Shapefile version 1000 length 498 type Point
policestation2.shx: ESRI Shapefile version 1000 length 178 type Point
```

### SRID 가져오기 및 내보내기

#### SRID 가져오기

쉐이프 파일 가져오기 수행 시 적절한 좌표 정보를 함께 제공하기 위해 SRID 정보가 필요하다. 아래 2가지 조건이 준비되어 있다면 altiShapeLoader가 .prj 파일을 읽고 분석하여 SRID 정보와 함께 공간 데이터를 입력하므로 사용자가 SRID 정보 입력을 위해 따로 해야 할 작업은 없다.

- .prj 파일
  
  SRID는 쉐이프 파일 구성 요소 중 하나인 .prj 파일에 기록된다. 쉐이프 파일 가져오기를 할 때 이 파일이 있어야 SRID 정보를 올바르게 입력할 수 있다.  

- SPATIAL_REF_SYS 테이블
  
  .prj 파일에 저장된 SRID가 SPATIAL_REF_SYS 테이블에 입력되어 있어야 한다. 

하지만 아래 두 가지 경우 사용자는 사용자 정의 파일(epsg.properties)이나 -srid 옵션을 사용하여 SRID 정보를 입력해야 한다. 

- .prj 파일이 없는 경우 
  
  SPATIAL_REF_SYS 테이블에 SRID가 있지만 .prj 파일이 없는 경우로 쉐이프 파일 가져오기 수행 시 [Preparing & analyzing metadata] 단계 로그에 아래와 같은 에러 메시지가 발생한다. 
  
  ```bash
  Unable to find the target prj file: /home/altiShapeLoader/data/subway_station.prj
  Unable to parse the given prj file and no user input SRID
  ```

- .prj 파일 분석이 실패하는 경우
  
  .prj 파일이 존재하고 SPATIAL_REF_SYS 테이블에 SRID가 있지만 altiShapeLoader에서 SRID를 분석할 수 없는 경우이다. altiShapeLoader는 GeoTools에서 제공하는 라이브러리(gt-epsg-hsql-xx.jar)와 사용자 정의 파일(epsg.properties)을 참조하여 SRID를 분석하는데 이 참조 파일에 .prj 파일의 SRID가 없는 것을 의미한다. 쉐이프 파일 가져오기 수행 시 [Preparing & analyzing metadata] 단계 로그에 아래와 같은 에러 메시지가 발생한다. 
  
  ```bash
  [SRID] Failed to parse or find EPSG code: /home/altiShapeLoader/data/bld.prj
  Unable to parse the given prj file and no user input SRID
  ```

다음은 EPSG 코드에 없는 GRS80 타원체 좌표 SR-ORG:7846를 SRID로 가진 쉐이프 파일 bld를 가져오기 수행하는  예제이다. SRID 7846은 SPATIAL_REF_SYS 테이블에 입력되어 있어야 한다. 

- 사전 준비 : 메타 테이블 SPATIAL_REF_SYS에 SRID 입력
  
  ```sql
  -- 메타 테이블 SPATIAL_REF_SYS에 SRID를 입력한다.
  -- SRID와 AUTH_SRID는 같게 입력해야 한다. 
  
  iSQL> EXEC SYS_SPATIAL.ADD_SPATIAL_REF_SYS ( 7846, 'SR-ORG', 7846, 'PROJCS["PCS_ITRF2000_TM",GEOGCS["GCS_ITRF_2000",DATUM["D_ITRF_2000",SPHEROID["GRS_1980",6378137.0,298.257222101]],PRIMEM["Greenwich",0.0],UNIT["Degree",0.0174532925199433]],PROJECTION["Transverse_Mercator"],PARAMETER["False_Easting",1000000.0],PARAMETER["False_Northing",2000000.0],PARAMETER["Central_Meridian",127.5],PARAMETER["Scale_Factor",0.9996],PARAMETER["Latitude_Of_Origin",38.0],UNIT["Meter",1.0]]', 'Proj4js.defs["SR-ORG:7846"] = "+proj=tmerc +lat_0=38 +lon_0=127 +k=1 +x_0=200000 +y_0=0 +ellps=GRS80 +towgs84=0,0,0,0,0,0,0 +units=m +no_defs";' );
  Execute success.
  
  iSQL> SELECT SRID, AUTH_NAME, AUTH_SRID FROM SPATIAL_REF_SYS WHERE AUTH_SRID = '7846';
  SRID        AUTH_NAME   AUTH_SRID   
  ----------------------------------------
  7846        SR-ORG      7846        
  1 row selected.
  ```

- **사용자 정의 파일(epsg.properties)을 이용**
  
  epsg.properties 파일에 SRID=WKT 형식으로 SRID를 추가한다. 이 파일은 altiShapeLoader 디렉터리에 있어야 한다. 
  
  ```bash
  $ cat epsg.properties
  7846=PROJCS["PCS_ITRF2000_TM",GEOGCS["GCS_ITRF_2000",DATUM["D_ITRF_2000",SPHEROID["GRS_1980",6378137.0,298.257222101]],PRIMEM["Greenwich",0.0],UNIT["Degree",0.0174532925199433]],PROJECTION["Transverse_Mercator"],PARAMETER["False_Easting",1000000.0],PARAMETER["False_Northing",2000000.0],PARAMETER["Central_Meridian",127.5],PARAMETER["Scale_Factor",0.9996],PARAMETER["Latitude_Of_Origin",38.0],UNIT["Meter",1.0]]
  
  $ altiShapeLoader.sh -o import -f data/bld.shp
  ```

- **-srid 옵션 사용**
  
  altiShapeLoader 가져오기 실행 시 실행 옵션에 -srid를 추가한다.
  
  ```bash
  $ altiShapeLoader.sh -o import -f data/bld.shp -srid 7846
  ```

#### SRID 내보내기

쉐이프 파일 내보내기 작업을 수행하면 .shp 파일과 함께 SRID 정보를 담고 있는 .prj 파일을 함께 생성한다. altiShapeLoader는 테이블에 저장된 AUTH_SRID를 참조하여 GeoTools 라이브러리를 통해 .prj 파일 내용을 작성한다.

<br />

# 3. 주의사항

altiShapeLoader는 자바 기반의 오픈 소스 GeoTools를 기반으로 작성되어 쉐이프 파일 및 GeoTools의 제약 사항을 그대로 따른다. 

### 쉐이프 파일(Shapefile) 제약점

쉐이프 파일(Shapefile)은 다음과 같은 주요 제약점이 있다.

- 쉐이프 파일은 한 개의 공간 데이터(geometry) 컬럼만 가질 수 있고 한 가지 공간 데이터 타입만 가질 수 있다 (Polygon과 line 등 여러 타입을 섞어서 저장할 수 없다).
- 쉐이프 파일의 각 구성 요소는 최대 2GB 크기까지 지원한다.
- 속성 필드 이름은 최대 10자를 넘을 수 없다.
- 속성 필드 최대 개수는 255개이고 최대 수를 초과한 속성 필드는 무시한다.
- 정해진 데이터 타입 4가지만 지원한다 : NUMBER, FLOAT, CHARACTER(255), DATE

위 제약 사항은 https://desktop.arcgis.com/en/arcmap/latest/manage-data/shapefiles/geoprocessing-considerations-for-shapefile-output.htm 에서도 확인할 수 있다.

### GeoTools 제약점

GeoTools 제약점은 아래 링크를 참조한다.

- https://docs.geotools.org/stable/userguide/library/data/shape.html

<br/>

# 4. 데이터 타입 변환

Altibase와 쉐이프 파일 간 데이터 타입 변환표이다. 쉐이프 파일에서 데이터 타입 정보는 dBASE 파일 형식인 .dbf 파일이 가지고 있다. 쉐이프 파일 버전에 따라 지원하는 데이터 타입이나 precision이 달라질 수 있으므로 주의해야 한다.

### 가져오기 데이터 타입 변환

| Data Type | dBASE field      | Altibase                | Note                                                                                                                                              |
| --------- | ---------------- | ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| 숫자형       | NUMBER           | INTEGER, BIGINT, DOUBLE | dBASE 필드(field)의 precision과 scale 여부에 따라 알티베이스 데이터 타입을 결정한다. scale이 있으면 DOUBLE 형으로, scale이 없으면 precision 1~9까지 INTEGER 형, 10 이상은 BIGINT 형으로 변환한다. |
| 문자형       | CHARACTER        | VARCHAR                 | -                                                                                                                                                 |
| 날짜형       | DATE             | DATE                    | dBASE에서 TIME 타입 미지원                                                                                                                               |
| 불리언       | BOOLEAN(Logical) | VARCHAR(1)              | 알티베이스는 Boolean 데이터 타입을 지원하지 않는다. dbf 파일에서 T 값은 "T"로 F 값은 "F"로 가져오기를 수행하고 나머지 값(1/0/null)은 널(NULL)로 처리한다.                                          |

### 내보내기 데이터 타입 변환

| Data Type | Altibase                                               | dBASE field (precision) | Note                                                |
|:---------:|:------------------------------------------------------ |:-----------------------:|:--------------------------------------------------- |
| 숫자형       | SMALLINT, INTEGER, BIGINT                              | NUMBER                  | Altibase 데이터 타입에 따라 적절한 precision을 설정하며 scale은 0이다. |
| 숫자형       | REAL, NUMBER, NUMERIC, DOUBLE, FLOAT                   | NUMBER                  | Altibase 데이터 타입에 따라 적절한 precision과 scale을 설정한다.     |
| 문자형       | CHAR, VARCHAR                                          | CHARACTER               | dBASE  문자형 최대값은 255 이다.                             |
| 문자형       | NCHAR, NVARCHAR                                        | 미지원                     | -                                                   |
| 날짜형       | DATE                                                   | DATE                    | Altibase 는 TIME을 지원한다.<br />dBASE 는 TIME을 지원하지 않는다. |
| 이진        | BINARY, BIT, VARBIT, BYTE, VARBYTE, NIBBLE, CLOB, BLOB | 미지원                     | -                                                   |

<br/>

------

<a name="shapefile">1</a> 쉐이프 파일(Shapefile) : 지리정보시스템 소프트웨어 개발사 ESRI에서 개발한 파일 형식으로 지리정보시스템(GIS) 분야에서 표준 파일이다. 쉐이프 파일은 아래 3가지 파일들이 필수로 구성되어 있다.

- shp : 벡터 형식으로 점, 선, 도형을 표현한 공간 데이터 정보를 가지고 있다.
- shx : 인덱스 파일. shp 파일에 담겨있는 도형 정보의 위치를 담고 있다.
- dbf : shp 파일의 도형 정보에 대한 속성 정보를 담은 dBASE 테이블 파일이다. 

참고 : [Geoprocessing considerations for shapefile output](https://desktop.arcgis.com/en/arcmap/latest/manage-data/shapefiles/geoprocessing-considerations-for-shapefile-output.htm)
