<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  

- [altiShapeLoader User's Manual](#altishapeloader-users-manual)
  - [서문](#%EC%84%9C%EB%AC%B8)
    - [이 매뉴얼에 대하여](#%EC%9D%B4-%EB%A7%A4%EB%89%B4%EC%96%BC%EC%97%90-%EB%8C%80%ED%95%98%EC%97%AC)
- [1.altiShapeLoader 소개](#1altishapeloader-%EC%86%8C%EA%B0%9C)
    - [개요](#%EA%B0%9C%EC%9A%94)
    - [시스템 요구 사항](#%EC%8B%9C%EC%8A%A4%ED%85%9C-%EC%9A%94%EA%B5%AC-%EC%82%AC%ED%95%AD)
    - [설치 및 제거](#%EC%84%A4%EC%B9%98-%EB%B0%8F-%EC%A0%9C%EA%B1%B0)
- [2.altiShapeLoader 시작하기](#2altishapeloader-%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0)
    - [알티베이스 선행조건](#%EC%95%8C%ED%8B%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4-%EC%84%A0%ED%96%89%EC%A1%B0%EA%B1%B4)
    - [접속 정보 및 수행 옵션](#%EC%A0%91%EC%86%8D-%EC%A0%95%EB%B3%B4-%EB%B0%8F-%EC%88%98%ED%96%89-%EC%98%B5%EC%85%98)
    - [Import](#import)
    - [Export](#export)
    - [SRID](#srid)
- [3.주의사항](#3%EC%A3%BC%EC%9D%98%EC%82%AC%ED%95%AD)
  - [Shapefile 제약점](#shapefile-%EC%A0%9C%EC%95%BD%EC%A0%90)
  - [데이터 타입 제약점](#%EB%8D%B0%EC%9D%B4%ED%84%B0-%ED%83%80%EC%9E%85-%EC%A0%9C%EC%95%BD%EC%A0%90)
    - [Import 데이터 타입 변환](#import-%EB%8D%B0%EC%9D%B4%ED%84%B0-%ED%83%80%EC%9E%85-%EB%B3%80%ED%99%98)
    - [Export 데이터 타입 변환](#export-%EB%8D%B0%EC%9D%B4%ED%84%B0-%ED%83%80%EC%9E%85-%EB%B3%80%ED%99%98)
- [4.Open Source Libraries](#4open-source-libraries)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->


Altibase® Tools & Utilities

altiShapeLoader User's Manual
==============================

![](media/altiShapeLoader/e5cfb3761673686d093a3b00c062fe7a.png)



altiShapeLoader User's Manual

Release 7.2

Copyright ⓒ 2001\~2021 Altibase Corp. All Rights Reserved.

본 문서의 저작권은 ㈜알티베이스에 있습니다. 이 문서에 대하여 당사의 동의 없이 무단으로 복제 또는 전용할 수 없습니다.

**㈜알티베이스**

08378 서울시 구로구 디지털로 306 대륭포스트타워Ⅱ 10층

전화: 02-2082-1114 팩스: 02-2082-1099

고객서비스포털: <http://support.altibase.com>

homepage: [http://www.altibase.com](http://www.altibase.com/)



서문
----

### 이 매뉴얼에 대하여

이 매뉴얼은 알티베이스에 shp 파일을 import/export 기능을 제공하는 altiShapeLoader에 대해 기술한다.

#### 대상 사용자

이 매뉴얼은 다음과 같은 Altibase 사용자를 대상으로 작성되었다.

-   데이터베이스 관리자

-   성능 관리자

-   데이터베이스 사용자

-   응용 프로그램 개발자

-   기술지원부

다음과 같은 배경 지식을 가지고 이 매뉴얼을 읽는 것이 좋다.

-   컴퓨터, 운영 체제 및 운영 체제 유틸리티 운용에 필요한 기본 지식

-   관계형 데이터베이스 사용 경험 또는 데이터베이스 개념에 대한 이해

-   컴퓨터 프로그래밍 경험

-   데이터베이스 서버 관리, 운영 체제 관리 또는 네트워크 관리 경험

#### 이 매뉴얼의 구성

이 매뉴얼은 다음과 같이 구성되어 있다.

-   제 1장 altiShapeLoader 소개  
    이 장은altiShapeLoader를 사용하고자 하는 사용자들을 위해 기능과 설치 방법을 소개한다.
    
-   제 2장 altiShapeLoader  시작하기  
    이 장은 altiShapeLoader  효율적으로 원활하게 실행하는 데 도움이 되는 기본 개념을 소개하고,명령어 인터페이스(CLI) 모드 사용법을 간단하게 설명한다.


#### 문서화 규칙

이 절에서는 이 매뉴얼에서 사용하는 규칙에 대해 설명한다. 이 규칙을 이해하면 이 매뉴얼과 설명서 세트의 다른 매뉴얼에서 정보를 쉽게 찾을 수 있다.

여기서 설명하는 규칙은 다음과 같다.

-   구문 다이어그램

-   샘플 코드 규칙

##### 구문 다이어그램

이 매뉴얼에서는 다음 구성 요소로 구축된 다이어그램을 사용하여, 명령문의 구문을 설명한다.

| 구성 요소                                   | 의미                                                         |
| ------------------------------------------- | ------------------------------------------------------------ |
| ![image1](media/altiShapeLoader/image1.gif) | 명령문이 시작한다. 완전한 명령문이 아닌 구문 요소는 화살표로 시작한다. |
| ![image2](media/altiShapeLoader/image2.gif) | 명령문이 다음 라인에 계속된다. 완전한 명령문이 아닌 구문 요소는 이 기호로 종료한다. |
| ![image3](media/altiShapeLoader/image3.gif) | 명령문이 이전 라인으로부터 계속된다. 완전한 명령문이 아닌 구문 요소는 이 기호로 시작한다. |
| ![image4](media/altiShapeLoader/image4.gif) | 명령문이 종료한다.                                           |
| ![](media/altiShapeLoader/image5.gif)       | 필수 항목                                                    |
| ![](media/altiShapeLoader/image6.gif)       | 선택적 항목                                                  |
| ![](media/altiShapeLoader/image7.gif)       | 선택사항이 있는 필수 항목. 한 항목만 제공해야 한다.          |
| ![](media/altiShapeLoader/image8.gif)       | 선택사항이 있는 선택적 항목                                  |
| ![](media/altiShapeLoader/image9.gif)       | 선택적 항목. 여러 항목이 허용된다. 각 반복 앞부분에 콤마가 와야 한다. |

##### 샘플 코드 규칙

코드 예제는 SQL, Stored Procedure, iSQL 또는 다른 명령 라인 구문들을 예를 들어 설명한다.

아래 테이블은 코드 예제에서 사용된 인쇄 규칙에 대해 설명한다.

| 규칙         | 의미                                                                                | 예제                                                                                                         |
|--------------|-------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
| [ ]          | 선택 항목을 표시                                                                    | VARCHAR [(*size*)] [[FIXED \|] VARIABLE]                                                                     |
| { }          | 필수 항목 표시. 반드시 하나 이상을 선택해야 되는 표시                               | { ENABLE \| DISABLE \| COMPILE }                                                                             |
| \|           | 선택 또는 필수 항목 표시의 인자 구분 표시                                           | { ENABLE \| DISABLE \| COMPILE } [ ENABLE \| DISABLE \| COMPILE ]                                            |
| . . .        | 그 이전 인자의 반복 표시 예제 코드들의 생략되는 것을 표시                           | SQL\> SELECT ename FROM employee; ENAME  ----------------------- SWNO  HJNO  HSCHOI  . . . 20 rows selected. |
| 그 밖에 기호 | 위에서 보여진 기호 이 외에 기호들                                                   | EXEC :p1 := 1; acc NUMBER(11,2);                                                                             |
| 기울임 꼴    | 구문 요소에서 사용자가 지정해야 하는 변수, 특수한 값을 제공해야만 하는 위치         | SELECT \* FROM *table_name*; CONNECT *userID*/*password*;                                                    |
| 소문자       | 사용자가 제공하는 프로그램의 요소들, 예를 들어 테이블 이름, 칼럼 이름, 파일 이름 등 | SELECT ename FROM employee;                                                                                  |
| 대문자       | 시스템에서 제공하는 요소들 또는 구문에 나타나는 키워드                              | DESC SYSTEM_.SYS_INDICES_;                                                                                   |

#### 관련 자료

자세한 정보를 위하여 Altibase의 다음 문서 목록을 참조한다.

-   Installation Guide

-   Getting Started Guide

-   Administrator’s Manual

-   Replication Manual

-   Precompiler User’s Manual

-   API User’s Manual

-   Altibase C Interface Manual

-   iSQL User’s Manual

-   Utilities Manual

-   General Reference

-   Error Message Reference

#### Altibase는 여러분의 의견을 환영합니다.

이 매뉴얼에 대한 여러분의 의견을 보내주시기 바랍니다. 사용자의 의견은 다음 버전의 매뉴얼을 작성하는데 많은 도움이 됩니다. 보내실 때에는 아래 내용과 함께 고객서비스포털(http://support.altibase.com/kr/ )로 보내주시기 바랍니다.

-   사용 중인 매뉴얼의 이름과 버전

-   매뉴얼에 대한 의견

-   사용자의 성함, 주소, 전화번호

이 외에도 Altibase 기술지원 설명서의 오류와 누락된 부분 및 기타 기술적인 문제들에 대해서 이 주소로 보내주시면 정성껏 처리하겠습니다. 또한, 기술적인 부분과 관련하여 즉각적인 도움이 필요한 경우에도 고객서비스포털을 통해 서비스를 요청하시기 바랍니다.

여러분의 의견에 항상 감사드립니다.



# 1.altiShapeLoader 소개

이 장은 altiShapeLoader를 소개하고 설치하는 방법을 설명한다. 이 장은 다음의 절로 구성된다.

-   개요
-   시스템 요구 사항
-   설치 및 제거



### 개요

altiShapeLoader는 알티베이스를 대상으로 shp 파일을 import/export 하기 위한 도구로 오픈 소스인 GeoTools를 기반으로 작성되었다.

### 시스템 요구 사항

이 절은 altiShapeLoader를 설치하고 실행하기 위해 필요한 시스템 사양에 대해 설명하고, altiShapeLoader와 호환되는 알티베이스에 대해 설명한다.

-   하드웨어 요구 사항
-   소프트웨어 요구 사항
-   호환되는 알티베이스 버전

#### 하드웨어 요구 사항

-   메인 메모리: 최소 512MB 이상, 4GB 이상 권고
-   디스크: 20MB 이상의 설치 여유 공간

#### 소프트웨어 요구 사항

-   Java: Oracle, OpenJDK 또는 IBM Java Runtime Environment 8 또는 이상
-   OS: Java 설치 및 구동 가능한 64bit OS

#### 호환되는 알티베이스 버전

-   Altibase 7.1.0 또는 그 이상 버전

### 설치 및 제거

altiShapeLoader 설치는 제공되는 압축 파일을 풀면 실행에 필요한 파일들이 포함된 altiShapeLoader 디렉토리가 압축해제 되는 것으로 완료된다. altiShapeLoader는 자바로 작성된 프로그램으로 JAVA_HOME 환경 변수를 반드시 설정하고 구동하여야 한다.

```bash
$ export JAVA_HOME=/usr/java/1.8
$ $JAVA_HOME/bin/java -version
java version "1.8.0_101"
Java(TM) SE Runtime Environment (build 1.8.0_101-b13)
Java HotSpot(TM) 64-Bit Server VM (build 25.101-b13, mixed mode)
```

altiShapeLoader 환경변수 파일인 altiShapeLoader.properties는 altiShapeLoader.properties.release 파일을 복사 후 필요에 따라 편집해서 사용한다.

altiShapeLoader를 제거하려면, 설치된 altiShapeLoader 디렉토리를 삭제하면 완료된다.



# 2.altiShapeLoader 시작하기

이 장은 altiShapeLoader를 사용하기 위한 알티베이스 선행조건, 접속 정보 및 수행 옵션, import/export 예제, SRID를 간략하게 설명한다. 

-   알티베이스 선행조건
-   접속 정보 및 수행 옵션
-   Import/Export 예제
-   SRID

### 알티베이스 선행조건

altiShapeLoader로 import 작업을 수행할 때 알티베이스에 등록되지 않은 SRID를 가진 shp 파일을 있으면, SYS_SPATIAL.ADD_SPATIAL_REF_SYS 프로시저를 통해 등록작업을 수행한다.

1. 이를 위해서 SYS_SPATIAL.ADD_SPATIAL_REF_SYS 프로시저가 알티베이스에 미리 생성되어 있어야 한다.  SYS 사용자로 SYS_SPATIAL 패키지를 알티베이스에 설치해야 한다.
2. altiShapeLoader에서 사용하는 데이터베이스 사용자 계정은 EXECUTE ANY PROCEDURE 권한이 있어야 한다. SYS_SPATIAL.ADD_SPATIAL_REF_SYS 프로시저를 수행하기 위해 필요한 권한이다.

### 접속 정보 및 수행 옵션

#### 입력 방법

altiShapeLoader로 특정 shp 파일 대상으로 import/export를 수행하기 위해서는 접속할 대상 데이터베이스 정보, 수행할 작업 종류, 테이블이름, shp 파일 경로 등의 정보가 필요하다. 입력 방법은 **명령창(Command Line Interface)  입력 방법**과 **설정 파일 (altiShapeLoader.properties) 입력**하는 방법이 있다. 두가지 입력 방법을 각기 따로 또는 혼용하여 사용가능하다. shp 파일마다 다른 값이 필요한 옵션은 명령창으로 입력하고, 공통적으로 사용되는 DB 접속 정보 및 공통 옵션들은 설정 파일에 기입하는 방법을 권고한다. 

**명령창 입력 방법**은 명령창에 altiShapeLoader 구동 명령 뒤에 옵션을 입력 후 수행하는 일괄식 (Batch mode) 방식으로 동작한다. 구동 이후 필요한 정보를 차례로 입력하는 대화식(Interactive mode) 방식은 지원하지 않는다. **설정 파일 방식**은 altiShapeLoader가 구동될 때마다 altiShapeLoader.properties 파일을 읽어 값을 적용하는데, 파일은 altiShapeLoader.sh, altiShapeLoader.bat와 같은 디렉토리에 있어야 한다. altiShapeLoader.properties 파일 생성은 설치 시 제공되는 altiShapeLoader.properties.release 파일을 복사 후 필요에 따라 편집해 사용한다.

입력값 적용 우선 순위는 명령창 입력, 설정 파일, 그리고 미리 정의된 기본값 순으로 적용된다. 예를 들어 import 작업 대상 테이블 이름을 명령창에는 T1, altiShapeLoader.properties에는 T2로 입력하였으면, 우선순위가 높은 명령창 입력값인 T1 이름을 작업 대상으로 선택한다. 만약 두가지 입력 방법으로 모두 입력되지 않았으면, 미리 정의된 기본값인 파일 이름을 테이블 이름으로 적용한다.

아래는 DB 접속 정보와 공통적인 import 옵션은 설정 파일에 기록하고 작업 종류, 테이블 이름, 개별 shp 파일 경로은 명령창에서 입력하여 수행하는 예제이다.

```bash
% cat ./altiShapeLoader.properties.release
###############################################
# DB connection arguments 
###############################################
DB_IP	 	= 127.0.0.1
DB_PORT		= 20300
DB_NAME		= mydb
DB_USER 	= SYS
DB_PASSWORD	= MANAGER
JDBC_PATH 	= ${ALTIBASE_HOME}/lib/Altibase.jar

###############################################
# General options
###############################################
# CREATE_TABLE	= T
# TABLE_TBS		= SYS_TBS_DISK_DATA
# CREATE_INDEX 	= F
# INDEX_TBS		= SYS_TBS_DISK_DATA
# DBF_CHAR 		= EUC-KR
# ENDIAN 			= B
# CASE_SENSIITIVE = F
# CREATE_BAD		= F

###############################################
# Performance options
###############################################
# PARALLEL 		= 4
# COMMIT		= 1000

###############################################
# Mandatory arguments
###############################################
# OPERATION 	= import 
### Use / instead of \ when specifying Windows file path.
# SHAPE_FILE = ./sample.shp
# TABLE_NAME 	= T1

###############################################
# Special options
###############################################
#GEO_COL_SIZE   = 103809024
#SRID			= 2097

% cp altiShapeLoader.properties.release altiShapeLoader.properties

% ./altiShapeLoader.sh -o import -f ./subway_station.shp
-----------------------------------------------------------------
        altiShapeLoader Release 1.0
        Shapefile import/export utility for Altibase datatbase
        Copyright(c) 2000, ALTIBASE Corporation or its subsidiaries.
        All Rights Reserved.
-----------------------------------------------------------------
...
```

#### 필수 입력 정보

필수 입력 정보는 명령창과 설정파일, 둘 중 하나에 반드시 입력해야 하는 정보이다. 미입력시 오류가 발생하고 작업이 중단된다. ''명령창 옵션''은 명령창에서는 *-option_name* 형식으로, ''프로퍼티 파일''은 altiShapeLoader.properties 파일에는 *OPTION_NAME=value* 형식으로 입력가능하다.

아래 두 가지 옵션은 일반적으로 shp 파일마다 다른 값을 가지므로, 명령창에서 직접 입력하는 방법을 권장한다.

| 명령창 옵션 | 프로퍼티 파일 | 의미                                                         |
| ----------- | ------------- | ------------------------------------------------------------ |
| o           | OPERATION     | Operation 종류 { import \| export \}. import 수행시 FID attribute가 dbf 파일에 들어 있으면 FID 값은 import 대상에서 제외된다. |
| f           | SHAPE_FILE    | shape file path (OS에 따라 대소문자 구분).                   |

데이터베이스에 접속하기 위해 필요한  DB 접속 정보도 필수 입력정보이다. 반복적으로 사용된다면 altiShapeLoader.properties 파일에 기입하여 사용하기를 권장한다.

| 명령창 옵션 | 프로퍼티 파일 | 의미                                                    |
| ----------- | ------------- | ------------------------------------------------------- |
| s           | DB_IP         | 데이터베이스가 구동되는 장비의 호스트 이름 또는 IP 주소 |
| port        | DB_PORT       | 데이터베이스의 포트 번호                                |
| d           | DB_NAME       | 데이터베이스 이름 (e.g. mydb)                           |
| u           | DB_USER       | 데이터베이스 사용자 ID                                  |
| p           | DB_PASSWORD   | 사용자 ID와 일치하는 암호                               |
| j           | JDBC_PATH     | 접속에 사용할 JDBC 파일 경로 (e.g. ./Altibase.jar)      |

#### 선택 입력 정보

선택 입력 정보는 사용자가 선택적으로 입력 가능한 정보이다. 명령창과 설정파일 두 곳 모두 미입력시 미리 정의된 기본값이 사용되어 작업이 진행된다.

| 명령창 옵션    | 프로퍼티 파일  | 의미                                                         | 기본값                 |
| -------------- | -------------- | ------------------------------------------------------------ | ---------------------- |
| t              | TABLE_NAME     | 테이블 이름 ( case_sensitive 옵션이 'T'이면 대소문자 구분). 미입력시 확장자를 제외한 shp 파일 이름이 기본값으로 적용된다 (e.g. /home/user/shp/test.shp 이면 테이블 이름이 test) | shp 파일 이름          |
| create_table   | CREATE_TABLE   | 테이블 생성여부 [ T\|F ]. 'T'를 선택하면 테이블이 생성되며, 이때 테이블의 첫번째 컬럼에 Feature ID (FID)가 자동 추가된다. 테이블 생성시 시퀀스(SEQ\_*table_name*\_FID)도 함께 생성되어 레코드 입력마다 고유한 FID값을 시퀀스에서 자동 할당한다. 생성 대상 시퀀스 객체가 데이터베이스에 이미 존재하면 생성하지 않는다. | T                      |
| table_tbs      | TABLE_TBS      | 테이블이 생성될 테이블스페이스 이름을 기입한다. 입력하지 않으면 알티베이스 디폴트 테이블 스페이스에 생성된다. create_table 옵션값이 'T'일 때만 적용된다. | 디폴트 테이블 스페이스 |
| create_index   | CREATE_INDEX   | 테이블 생성시 공간 객체 컬럼 index 생성 여부                 | F                      |
| index_tbs      | INDEX_TBS      | 인덱스가 생성될 테이블스페이스 이름을 기입한다. 입력하지 않으면 알티베이스 디폴트 테이블 스페이스에 생성된다. create_index 옵션값이  'T'일 때만 적용된다. | 디폴트 테이블 스페이스 |
| dbf_char       | DBF_CHAR       | import/export 수행시 DBF 파일을 어떤 character set으로 읽거나 쓸지 결정한다. altiShapeLoader.properties와 column mapping properties 파일을 읽을 때도 동일한 character set이 적용된다. | EUC-KR                 |
| endian         | ENDIAN         | import 작업 수행시 읽는 shp 파일의 endian 종류 \[ B\|L \]    | B                      |
| case_sensitive | CASE_SENSITIVE | 테이블/컬럼 이름 대소문자 구분 여부. 'T'이면 사용자 입력값을 그대로 데이터베이스에 전달하므로 주의해야 한다. 'F'이면 대문자로 변경하여 사용한다. | F                      |
| col_map_file   | COL_MAP_FILE   | shp 파일 컬럼과 데이터베이스 컬럼 이름 매핑 파일의 경로. 이름을 다르게 적용할 컬럼을 대상 파일에 shpColName=dbColName 형식으로 입력하면 적용된다. 값이 없으면 shp 파일에서 제공하는 컬럼이름이 적용된다. case_sensitive 옵션값에 따라 대소문자 구분이 적용된다. | shp 컬럼이름           |
| create_bad     | CREATE_BAD     | import/export 수행시 처리 실패한 데이터를 저장하기 하기 위한 bad 파일 생성 여부 [ T\|F ]. 'T'를 선택하면 처리 실패한 데이터를 shp 파일과 같은 이름(-f 옵션값)에 'bad' 확장자를 가진 파일에 저장한다. 모든 데이터가 문제없이 처리되면 bad 파일은 생성되지 않는다. import는 parallel 옵션값 갯수만큼의 bad 파일이 생성될 수도 있다. | F                      |

#### 성능 옵션

altiShapeLoader의 성능을 조정하기 위한 옵션이다. 최대 성능을 위해서는 수행되는 장비의 CPU와 메모리에 따라 적절한 조정이 필요하다. 선택 입력 정보와 마찬가지로 명령창과 설정파일 두 곳 모두 미입력시 미리 정의된 기본값이 적용된다.

| 명령창 옵션 | 프로퍼티 파일 | 의미                                                         | 기본값 |
| ----------- | ------------- | ------------------------------------------------------------ | ------ |
| parallel    | PARALLEL      | DB insert thread 갯수. import 작업 수행시 데이터를 몇개의 thread로 insert 작업을 수행할 것인가를 결정한다. | 4      |
| commit      | COMMIT        | Batch insert commit 레코드 갯수. import 작업 수행시 insert thread가 레코드 몇개 단위로 커밋할 것인지를 결정한다. | 1,000  |

#### 특수 옵션

특수 옵션은 특별 목적을 위해 제공되는 옵션들로, 일반적인 경우에는 사용하지 않기를 권장한다.

| 명령창 옵션  | 프로퍼티 파일 | 의미                                                         | 기본값             |
| ------------ | ------------- | ------------------------------------------------------------ | ------------------ |
| srid         | SRID          | 사용자 강제 지정 SRID 값. altiShapeLoader가 주어진 prj 파일을 처리하지 못하는 경우 강제로 지정할 SRID. 상세 방법은 아래의 SRID 절을 참조한다. | N/A                |
| geo_col_size | GEO_COL_SIZE  | 테이블 생성시 geometry column precision 지정 (byte 단위). 기본값보다 큰 컬럼을 필요로 할때만 지정할 필요가 있다. | 103,809,024 (99MB) |

### Import

Import는 shp 파일의 공간 정보와 dbf 파일의 속성 정보를 데이터베이스로 복사하기 위한 기능이다. Import를 하기 위해서는 shp, shx, dbf, prj 등의 파일이 필요하다.

Import 사용자 케이스는 크게 세가지로 구분된다.

1. Single shp file to Single table: 한 개의 shp 파일을 하나의 테이블로 데이터를 import한다.
2. Multiple shp files to Single table: 특정 디렉토리내의 여러 개 shp 파일을 하나의 테이블로 데이터를 import한다.
3. Multiple shp files to Multiple tables : 특정 디렉토리내의 여러 개 shp 파일을 각기 개별 테이블로 데이터를 import한다.

3가지 사용자 케이스에서 필요한 옵션 값은 아래와 같다. (O: 필수, △: 선택, X: 입력 불가)

| 명령창 옵션 | 프로퍼티 파일 | Single shp file to Single table | Multiple shp files to Single table | Multiple shp files to Multiple tables |
| ----------- | ------------- | ------------------------------- | ---------------------------------- | ------------------------------------- |
| o           | OPERATION     | O                               | O                                  | O                                     |
| f           | SHAPE_FILE    | O                               | O                                  | O                                     |
| t           | TABLE_NAME    | △                               | O                                  | X                                     |

#### Single shp file to Single table

가장 일반적인 경우로 한 개의 shp 파일을 하나의 데이터베이스 테이블에 import 하는 케이스이다. 

OPERATION(-o)과 SHAPE_FILE(-f) 옵션은 반드시 입력해야 하며, TABLE_NAME (-t)은 사용자 선택 사항이다.

본 예제에서 altiShapeLoader.properties 파일에 CREATE_TABLE=T 이 설정되었기 때문에 시퀀스와 테이블이 생성되었다. 

```bash
% ./altiShapeLoader.sh -o import -f ./subway_station.shp
-----------------------------------------------------------------
        altiShapeLoader Release 1.0
        Shapefile import/export utility for Altibase datatbase
        Copyright(c) 2000, ALTIBASE Corporation or its subsidiaries.
        All Rights Reserved.
-----------------------------------------------------------------
Import requested: ./subway_station.shp
<started>
[CREATE SEQUENCE] CREATE SEQUENCE "SYS"."SEQ_SUBWAY_STATION_FID" START WITH 1 INCREMENT BY 1 MINVALUE 1 CYCLE
[CREATE SEQUENCE] Success
[CREATE TABLE] CREATE TABLE "SYS"."SUBWAY_STATION" (FID BIGINT DEFAULT "SEQ_SUBWAY_STATION_FID".NEXTVAL PRIMARY KEY,  "THE_GEOM" GEOMETRY(104857600) SRID 2097, "XCOORD" DOUBLE, "YCOORD" DOUBLE, "GUBUN" VARCHAR(254), "GUBUN2" VARCHAR(254), "NAM" VARCHAR(254), "NAM2" VARCHAR(254) )
[CREATE TABLE] Success
[DATA IMPORT start]
.
[DATA IMPORT done]
<finished>
<summary>
[File  ] ./subway_station.shp
[Status] [Read] Success, [Write] Success
[Read  ] Total:272, Success:272, Fail:0
[Write ] Total:272, Success:272, Fail:0
[Time  ] 0:00:00.124
```
위 예제는 subway_station.shp 파일을 import 하는 과정이다. 테이블 이름을 명시하지 않았기에 파일 이름과 동일한 SUBWAY_STATION 테이블이 대상이 된다.

[DATA IMPORT start]와 [DATA IMPORT done] 사이의 점(dot)은 레코드 1,000개 단위로 출력된다. 본 예제에서는 32개 레코드이기 때문에 1개가 출력되었다.

수행 결과는 \<summary>에 출력된다.
1. [Status] [Read] Success, [Write] Success: shp 파일 읽기 및 DB insert 모두 성공적으로 수행되었다.
2. [Read  ] Total:272, Success:272, Fail:0 272개의 데이터를 성공적으로 읽었다. 
3. [Write ] Total:272, Success:272, Fail:0 읽은 272개의 데이터를 오류없이 DB에 입력하였다. 
4. [Time  ] 0:00:00.124 shp 파일 읽기 와 DB insert에 소요된 시간으로  hh:mm:ss.sss 형식으로 출력된다.

#### Multiple shp files to Single table

특정 디렉토리에 들어있는 한개 이상의 shp 파일을 하나의 테이블로 import 하기 위한 케이스이다. 디렉토리 내의 shp 파일은 모두 동일한 스키마를 가져야 한다.

필수 입력인 OPERATION(-o), SHAPE_FILE(-f) 뿐 아니라, 대상 테이블 이름인 TABLE_NAME (-t) 옵션은 반드시 입력해야 한다. 그리고, SHAPE_FILE(-f) 은 개별 파일 경로가 아닌 디렉토리 경로를 입력하여야 한다. 

본 예제는 ./multi2single라는 디렉토리에 들어있는 3개의 shp 파일을 MULTI2SINGLE라는 테이블에 import하는 과정이다. altiShapeLoader.properties 파일에 CREATE_TABLE=T 를 설정해서 시퀀스와 테이블이 최초 1회 생성되었다.

```bash
% ls ./multi2single
river.dbf  river.prj  river.shp  river.shx  river2.dbf  river2.prj  river2.shp  river2.shx  river3.dbf  river3.prj  river3.shp  river3.shx
% ./altiShapeLoader.sh -o import -f ./multi2single -t MULTI2SINGLE
-----------------------------------------------------------------
        altiShapeLoader Release 1.0
        Shapefile import/export utility for Altibase datatbase
        Copyright(c) 2000, ALTIBASE Corporation or its subsidiaries.
        All Rights Reserved.
-----------------------------------------------------------------
Import requested: ./multi2single/river.shp
<started>
[CREATE SEQUENCE] CREATE SEQUENCE "SYS"."SEQ_MULTI2SINGLE_FID" START WITH 1 INCREMENT BY 1 MINVALUE 1 CYCLE
[CREATE SEQUENCE] Success
[CREATE TABLE] CREATE TABLE "SYS"."MULTI2SINGLE" (FID BIGINT DEFAULT "SEQ_MULTI2SINGLE_FID".NEXTVAL PRIMARY KEY,  "THE_GEOM" GEOMETRY(104857600) SRID 2097, "ID" BIGINT )
[CREATE TABLE] Success
[DATA IMPORT start]
.
[DATA IMPORT done]
<finished>
<summary>
[File  ] ./multi2single/river.shp
[Status] [Read] Success, [Write] Success
[Read  ] Total:30, Success:30, Fail:0
[Write ] Total:30, Success:30, Fail:0
[Time  ] 0:00:00.085

Import requested: ./multi2single/river2.shp
<started>
[DATA IMPORT start]
.
[DATA IMPORT done]
<finished>
<summary>
[File  ] ./multi2single/river2.shp
[Status] [Read] Success, [Write] Success
[Read  ] Total:29, Success:29, Fail:0
[Write ] Total:29, Success:29, Fail:0
[Time  ] 0:00:00.041

Import requested: ./multi2single/river3.shp
<started>
[DATA IMPORT start]
.
[DATA IMPORT done]
<finished>
<summary>
[File  ] ./multi2single/river3.shp
[Status] [Read] Success, [Write] Success
[Read  ] Total:29, Success:29, Fail:0
[Write ] Total:29, Success:29, Fail:0
[Time  ] 0:00:00.045
```

#### Multiple shp files to Multiple tables

특정 디렉토리의 여러 개의 shp 파일을 각각 개별 테이블로 import하는 케이스이다. 

OPERATION(-o)과 SHAPE_FILE(-f)옵션은 반드시 입력해야 하며, SHAPE_FILE(-f) 은 개별 파일 경로가 아닌 디렉토리 경로를 입력하여야 한다. 파일이름이 곧 테이블 이름으로 설정되기 때문에 TABLE_NAME (-t)은 입력하지 않아야 한다. 테이블 이름을 입력하면 Multiple shp files to Single table 케이스로 간주되어 하나의 테이블로 import 작업을 시도하게 된다.

본 예제는 ./multi2multi라는 디렉토리에 들어있는 네 개의 shp 파일들을 파일이름으로 설정된 테이블에 데이터를  import하는 과정이다. altiShapeLoader.properties 파일에 CREATE_TABLE=T를 설정해서 shp 파일별로 필요한 시퀀스와 테이블을 각각 생성한다.

```bash
% ls ./multi2multi/
building.dbf  firestation.dbf  firestation.sbx   healthcenter.prj  healthcenter.shp   policestation.qix  policestation.shx
building.prj  firestation.prj  firestation.shp   healthcenter.qix  healthcenter.shx   policestation.sbn
building.shp  firestation.qix  firestation.shx   healthcenter.sbn  policestation.dbf  policestation.sbx
building.shx  firestation.sbn  healthcenter.dbf  healthcenter.sbx  policestation.prj  policestation.shp

% ./altiShapeLoader.sh -o import -f ./multi2multi
-----------------------------------------------------------------
        altiShapeLoader Release 1.0
        Shapefile import/export utility for Altibase datatbase
        Copyright(c) 2000, ALTIBASE Corporation or its subsidiaries.
        All Rights Reserved.
-----------------------------------------------------------------
Import requested: ./multi2multi/building.shp
<started>
[CREATE SEQUENCE] CREATE SEQUENCE "SYS"."SEQ_BUILDING_FID" START WITH 1 INCREMENT BY 1 MINVALUE 1 CYCLE
[CREATE SEQUENCE] Success
[CREATE TABLE] CREATE TABLE "SYS"."BUILDING" (FID BIGINT DEFAULT "SEQ_BUILDING_FID".NEXTVAL PRIMARY KEY,  "THE_GEOM" GEOMETRY(104857600) SRID 2097, "UFID" VARCHAR(28), "BLD_NM" VARCHAR(100), "DONG_NM" VARCHAR(100), "GRND_FLR" INTEGER, "UGRND_FLR" INTEGER, "PNU" VARCHAR(19), "ARCHAREA" DOUBLE, "TOTALAREA" DOUBLE, "PLATAREA" DOUBLE, "HEIGHT" DOUBLE, "STRCT_CD" VARCHAR(2), "USABILITY" VARCHAR(5), "BC_RAT" DOUBLE, "VL_RAT" DOUBLE, "BLDRGST_PK" VARCHAR(28), "USEAPR_DAY" VARCHAR(8), "REGIST_DAY" VARCHAR(8), "GB_CD" VARCHAR(2), "VIOL_BD_YN" VARCHAR(1) )
[CREATE TABLE] Success
[DATA IMPORT start]
..........................
[DATA IMPORT done]
<finished>
<summary>
[File  ] ./multi2multi/building.shp
[Status] [Read] Success, [Write] Success
[Read  ] Total:25,532, Success:25,532, Fail:0
[Write ] Total:25,532, Success:25,532, Fail:0
[Time  ] 0:00:01.041

Import requested: ./multi2multi/firestation.shp
<started>
[CREATE SEQUENCE] CREATE SEQUENCE "SYS"."SEQ_FIRESTATION_FID" START WITH 1 INCREMENT BY 1 MINVALUE 1 CYCLE
[CREATE SEQUENCE] Success
[CREATE TABLE] CREATE TABLE "SYS"."FIRESTATION" (FID BIGINT DEFAULT "SEQ_FIRESTATION_FID".NEXTVAL PRIMARY KEY,  "THE_GEOM" GEOMETRY(104857600) SRID 2097, "NAM" VARCHAR(25), "ADDR" VARCHAR(254) )
[CREATE TABLE] Success
[DATA IMPORT start]
.
[DATA IMPORT done]
<finished>
<summary>
[File  ] ./multi2multi/firestation.shp
[Status] [Read] Success, [Write] Success
[Read  ] Total:23, Success:23, Fail:0
[Write ] Total:23, Success:23, Fail:0
[Time  ] 0:00:00.047

Import requested: ./multi2multi/healthcenter.shp
<started>
[CREATE SEQUENCE] CREATE SEQUENCE "SYS"."SEQ_HEALTHCENTER_FID" START WITH 1 INCREMENT BY 1 MINVALUE 1 CYCLE
[CREATE SEQUENCE] Success
[CREATE TABLE] CREATE TABLE "SYS"."HEALTHCENTER" (FID BIGINT DEFAULT "SEQ_HEALTHCENTER_FID".NEXTVAL PRIMARY KEY,  "THE_GEOM" GEOMETRY(104857600) SRID 2097, "NAM" VARCHAR(25), "ADDR" VARCHAR(254) )
[CREATE TABLE] Success
[DATA IMPORT start]
.
[DATA IMPORT done]
<finished>
<summary>
[File  ] ./multi2multi/healthcenter.shp
[Status] [Read] Success, [Write] Success
[Read  ] Total:24, Success:24, Fail:0
[Write ] Total:24, Success:24, Fail:0
[Time  ] 0:00:00.035

Import requested: ./multi2multi/policestation.shp
<started>
[CREATE SEQUENCE] CREATE SEQUENCE "SYS"."SEQ_POLICESTATION_FID" START WITH 1 INCREMENT BY 1 MINVALUE 1 CYCLE
[CREATE SEQUENCE] Success
[CREATE TABLE] CREATE TABLE "SYS"."POLICESTATION" (FID BIGINT DEFAULT "SEQ_POLICESTATION_FID".NEXTVAL PRIMARY KEY,  "THE_GEOM" GEOMETRY(104857600) SRID 2097, "NAM" VARCHAR(50), "ADDR" VARCHAR(254), "TEL" VARCHAR(20), "FAX" VARCHAR(20) )
[CREATE TABLE] Success
[DATA IMPORT start]
.
[DATA IMPORT done]
<finished>
<summary>
[File  ] ./multi2multi/policestation.shp
[Status] [Read] Success, [Write] Success
[Read  ] Total:32, Success:32, Fail:0
[Write ] Total:32, Success:32, Fail:0
[Time  ] 0:00:00.044
```

### Export

Export는 데이터베이스 테이블에 저장된 공간 정보를 shp 파일로 복사하기 위한 기능이다. 테이블의 FID 컬럼은 export 대상에서 제외되어 shp 파일에 저장되지 않는다.

OPERATION(-o)과 SHAPE_FILE(-f) 옵션은 반드시 입력해야 하며, TABLE_NAME (-t)을 생략하면 데이터베이스 테이블 이름으로 치환된다.

#### export 예제
```bash
% altiShapeLoader.sh -o export -t POLICESTATION -f ./policestation2.shp
-----------------------------------------------------------------
        altiShapeLoader Release 1.0
        Shapefile import/export utility for Altibase datatbase
        Copyright(c) 2000, ALTIBASE Corporation or its subsidiaries.
        All Rights Reserved.
-----------------------------------------------------------------
Export requested: ./policestation2.shp
<started>
<commit started>
.
<finished>
<summary>
[File  ]./policestation2.shp
[Status] [Read] Success, [Write] Success
[Read  ] Total:32, Success:32, Fail:0
[Write ] Total:32, Success:32, Fail:0
[Time  ] 0:00:01.287
```
위 예제는 127.0.0.1:20300에 설치된 알티베이스에 SYS계정으로 접속하여, POLICESTATION 테이블의 내용을 policestation2.shp파일로 export 하기 위한 명령이다.

\<commit started>와 \<finished> 사이의 점(dot)은 레코드 1,000개 단위로 출력된다. 본 예제에서는 32개 레코드이기 때문에 1개가 출력되었다.

수행 결과는 \<summary>에 출력된다.
1. [Status] [Read] Success, [Write] Success: DB fetch 및 파일기록 모두 성공적으로 수행되었다.
2. [Read  ] Total:32, Success:32, Fail:0 DB로부터 32개의 데이터를 성공적으로 읽었다. 
3. [Write ] Total:32, Success:32, Fail:0 읽은 32개의 데이터를 shp 파일에 오류없이 기록하였다. 
4. [Time  ] 0:00:01.287: 총 소요시간은 hh:mm:ss.sss 형식으로 출력된다.

### SRID

Spatial Reference Identifier (SRID)는 공간 정보 객체의 위치를 표현하기 위한 좌표계 시스템을 표현하는 고유한 값이다. SRID는 shp 파일셋 중 하나로 shp 파일명과 동일한 이름의 prj 파일에 내용이 기록된다. 여기서 언급하는 SRID는  European Petroleum Survey Group (EPSG)와 같은 기구에서 제공하는 공식적인 SRID로 SPATIAL_REF_SYS의 AUTH_SRID와 동일하다.

#### import

shp 파일의 공간 정보를 데이터베이스 테이블에 입력할 때 적절한 좌표 정보를 함께 제공하기 위해 SRID 정보가 필요하다. altiShapeLoader에서는 두가지 입력 방법을 제공하며 우선 순위별로 아래와 같다.

1. shp 파일과 함께 제공되는 prj 파일을 읽어 altiShapeLoader가 SRID를 분석 및 입력한다. altiShapeLoader는 GeoTools에서 제공하는 기본 라이브러리(gt-epsg-hsql-xx.jar)와 사용자가 직접 정의하는 파일(epsg.properties) 두 가지를 참조하여 SRID를 분석한다. 사용자가 추가하고자 하는 SRID는 epsg.properties 파일에 SRID=WKT 형식으로 추가하면 altiShapeLoader에서 분석 가능하다. 이때 주의할 점은 프로퍼티 파일 특성상 WKT 입력시 한줄로 입력해야 한다.
2. 사용자가 특정 SRID를 강제 지정한다. 특별한 경우 사용하기를 권고하며, 데이터베이스의 SPATIAL_REF_SYS에 대상 SRID 정보가 미리 입력되어 있어야 한다.

#### export

export 작업을 수행하면 shp 파일과 함께 SRID 정보를 담고 있는 prj 파일이 함께 생성된다. altiShapeLoader는 알티베이스에 저장된 대상 테이블의 AUTH_SRID를 참조하여 GeoTools 라이브러리를 통해 prj 파일 내용을 작성한다.

# 3.주의사항

altiShapeLoader는 shapefile import/export 기능을 GeoTools 라이브러리를 사용하여 구현하였다. 따라서, shapefile 및 GeoTools의 제약점이 적용된다.

## Shapefile 제약점

Shapefile은 다음과 같은 주요 제약점이 있다.

- shapefile은 한개의 geometry 컬럼만 가질 수 있고, 한가지 geometry type만 가질 수 있다 (Polygon과 line 등 여러 타입을 섞어서 저장할 수 없다).
- 최대 2GB 크기까지 지원된다.
- 필드 이름 크기는 최대 10자를 넘을 수 없다.
- 필드 최대 갯수는 255개이고, 초과해서 정의된 필드는 무시된다.
- 정해진 데이터 타입만 지원된다: Number, Float , Character (255), Date

GeoTools 라이브러리를 사용하여 제작되었기에, GeoTools의 제약점 또한 적용된다. 상세 내용은 아래 링크를 참조한다.

- https://docs.geotools.org/stable/userguide/library/data/shape.html

## 데이터 타입 제약점

알티베이스와 dbf 파일 간 변환되는 데이터 타입을 설명한다. 사용되는 dbf 버전에 따라 지원하는 데이터 타입 또는 precision 지원이 달라질 수 있수 있으므로 주의한다.

### Import 데이터 타입 변환

| Data Type | dBase field       | Altibase                | Note                                                         |
| --------- | ----------------- | ----------------------- | ------------------------------------------------------------ |
| 숫자형    | Number            | INTEGER, BIGINT, DOUBLE | dBase field의 precision과 scale 여부에 따라 데이터 타입이 결정된다. scale이 있으면 DOUBLE형으로 결정된다. scale이 없으면 precision 1~9까지는 INTEGER, 초과값은 BIGINT로 결정된다. |
| 문자형    | Character         | VARCHAR                 |                                                              |
| 날짜      | Date (Time 제외)  | DATE                    |                                                              |
| 불리언    | Boolean (Logical) | VARCHAR(1)              | 알티베이스에는 불리언 데이터 타입이 없다. dbf 파일의 T/F값만 "T"/"F" 값으로 import, 나머지 값(1/0/null)은 null로 처리된다. |

### Export 데이터 타입 변환

| Data Type | Altibase                                               | dBase field (precision) | Note                                                         |
| --------- | ------------------------------------------------------ | ----------------------- | ------------------------------------------------------------ |
| 숫자형    | SMALLINT, INTEGER, BIGINT                              | Number                  | Altibase 타입에 따라 적절한 precision이 설정된다. scale은 0. |
| 숫자형    | REAL, NUMBER, NUMERIC, DOUBLE, FLOAT                   | Number                  | Altibase 타입에 따라 적절한 precision과 scale이 설정된다.    |
| 문자형    | CHAR, VARCHAR                                          | Character (Max. 255)    |                                                              |
| 문자형    | NCHAR, NVARCHAR                                        | 미지원                  | N/A                                                          |
| 날짜      | DATE (Time 포함)                                       | Date (Time 제외)        | dBase Time 미지원                                            |
| 이진      | BINARY, BIT, VARBIT, BYTE, VARBYTE, NIBBLE, CLOB, BLOB | 미지원                  | N/A                                                          |



# 4.Open Source Libraries 

이 장은 altiShapeLoader 프로그램 작성에 사용된 오픈 소스 라이브러리와 라이선스에 대해 기술한다.

altiShapeLoader는 다음 표에 기술된 오픈 소스 라이브러리를 기반하여 작성되었다. 라이선스 파일들은 텍스트 형식으로 altiShapeLoader와 함께 배포된다.

| Library                                    | Version | Homepage                          | Open               |
| ------------------------------------------ | ------- | --------------------------------- | ------------------ |
| GeoTools                                   | 22.5    | https://geotools.org/             | LGPL               |
| EPSG Authority Service Using HSQL Database | 22.5    | http://hsqldb.org/                | LGPL               |
| Apache Commons IO                          | 2.6     | https://commons.apache.org/       | Apache License 2.0 |
| Apache Commons CLI                         | 1.3.1   | https://commons.apache.org/       | Apache License 2.0 |
| Apache log4j                               | 1.2.16  | https://logging.apache.org/log4j/ | Apache License 2.0 |

