Altibase® Tools & Utilities

dataCompJ User's Manual
==============================

![](media/dataCompJ/e5cfb3761673686d093a3b00c062fe7a.png)

Altibase Tools & Utilities dataCompJ User's Manual

Release 7.2

Copyright ⓒ 2001\~2021 Altibase Corp. All Rights Reserved.

본 문서의 저작권은 ㈜알티베이스에 있습니다. 이 문서에 대하여 당사의 동의 없이
무단으로 복제 또는 전용할 수 없습니다.

**㈜알티베이스**

08378 서울시 구로구 디지털로 306 대륭포스트타워Ⅱ 10층

전화: 02-2082-1114 팩스: 02-2082-1099

고객서비스포털: <http://support.altibase.com>

homepage: [http://www.altibase.com](http://www.altibase.com/)

서문
----

### 이 매뉴얼에 대하여

이 매뉴얼은 Altibase 데이터베이스에서 이기종 데이터베이스로 데이터를 복제한 이후의 데이터 정합성 확인과 데이터 불일치를 해소하기 위한 도구인 dataCompJ를 사용하는 방법을 기술한다.

#### 대상 사용자

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

- 제 1장 dataCompJ 소개  
  이 장은 dataCompJ를 사용하고자 하는 사용자들을 위해 그 기능과 용어를 소개한다.
- 제 2장 dataCompJ 시작하기  
  이 장은 dataCompJ를 효율적으로 원활하게 실행하는 데 도움이 되는 기본 개념을 소개하고, 사용법을 간단하게 설명한다.
- 제 3장 기능
  이 장은 dataCompJ의 비교(DIFF) 기능과 일치(SYNC) 기능을 예제와 함께 설명한다.
- A. 부록: 이기종간 데이터 타입 호환 테이블

#### 문서화 규칙

이 절에서는 이 매뉴얼에서 사용하는 규칙에 대해 설명한다. 이 규칙을 이해하면 이 매뉴얼과 설명서 세트의 다른 매뉴얼에서 정보를 쉽게 찾을 수 있다.

여기서 설명하는 규칙은 다음과 같다.

- 구문 다이어그램

- 샘플 코드 규칙

##### 구문 다이어그램

이 매뉴얼에서는 다음 구성 요소로 구축된 다이어그램을 사용하여, 명령문의 구문을 설명한다.

| 구성 요소                             | 의미                                                         |
| ------------------------------------- | ------------------------------------------------------------ |
| ![image1](media/dataCompJ/image1.gif) | 명령문이 시작한다. 완전한 명령문이 아닌 구문 요소는 화살표로 시작한다. |
| ![image2](media/dataCompJ/image2.gif) | 명령문이 다음 라인에 계속된다. 완전한 명령문이 아닌 구문 요소는 이 기호로 종료한다. |
| ![image3](media/dataCompJ/image3.gif) | 명령문이 이전 라인으로부터 계속된다. 완전한 명령문이 아닌 구문 요소는 이 기호로 시작한다. |
| ![image4](media/dataCompJ/image4.gif) | 명령문이 종료한다.                                           |
| ![](media/dataCompJ/image5.gif)       | 필수 항목                                                    |
| ![](media/dataCompJ/image6.gif)       | 선택적 항목                                                  |
| ![](media/dataCompJ/image7.gif)       | 선택사항이 있는 필수 항목. 한 항목만 제공해야 한다.          |
| ![](media/dataCompJ/image8.gif)       | 선택사항이 있는 선택적 항목                                  |
| ![](media/dataCompJ/image9.gif)       | 선택적 항목. 여러 항목이 허용된다. 각 반복 앞부분에 콤마가 와야 한다. |

##### 샘플 코드 규칙

코드 예제는 SQL, Stored Procedure, iSQL 또는 다른 명령 라인 구문들을 예를 들어 설명한다.

아래 테이블은 코드 예제에서 사용된 인쇄 규칙에 대해 설명한다.

| 규칙         | 의미                                                         | 예제                                                         |
| ------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ ]          | 선택 항목을 표시                                             | VARCHAR [(*size*)] [[FIXED \|] VARIABLE]                     |
| { }          | 필수 항목 표시. 반드시 하나 이상을 선택해야 되는 표시        | { ENABLE \| DISABLE \| COMPILE }                             |
| \|           | 선택 또는 필수 항목 표시의 인자 구분 표시                    | { ENABLE \| DISABLE \| COMPILE } <br />[ ENABLE \| DISABLE \| COMPILE ] |
| . . .        | 그 이전 인자의 반복 표시 예제 코드들의 생략되는 것을 표시    | SQL\> SELECT ename FROM employee; <br />ENAME  <br />----------------------- <br />SWNO  <br />HJNO  <br />HSCHOI  <br />. . . <br />20 rows selected. |
| 그 밖에 기호 | 위에서 보여진 기호 이 외에 기호들                            | EXEC :p1 := 1; <br />acc NUMBER(11,2);                       |
| 기울임 꼴    | 구문 요소에서 사용자가 지정해야 하는 변수, 특수한 값을 제공해야만 하는 위치 | SELECT \* FROM *table_name*; <br />CONNECT *userID*/*password*; |
| 소문자       | 사용자가 제공하는 프로그램의 요소들, 예를 들어 테이블 이름, 컬럼 이름, 파일 이름 등 | SELECT ename FROM employee;                                  |
| 대문자       | 시스템에서 제공하는 요소들 또는 구문에 나타나는 키워드       | DESC SYSTEM_.SYS_INDICES_;                                   |

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

1.dataCompJ 소개
---------------------

이 장은 dataCompJ의 특징을 이해하고자 하는 사용자에게 이 도구를 소개하고 설치하는 방법을 설명한다. 이 장은 다음의 절로 구성된다.

- 개요
- 시스템 요구 사항
- 용어
- 불일치 레코드
- 일치 정책

### 개요

dataCompJ는 Altibase에서 이기종 데이터베이스로 복제한 데이터를 대상으로 데이터 정합성 확인과 데이터 불일치를 해소하기 위한 도구이다. 테이블 단위로 데이터를 비교하고 데이터 불일치가 있는 경우 이에 관한 정보를 파일로 출력한다. 불일치 데이터를 Slave 데이터베이스에 직접 적용하여 데이터를 일치시키는 기능도 제공한다.
dataCompJ가 관리하는 데이터는 데이터 복제 도구로 Altibase에서 제공하는 Adapter for Oracle 또는 Adapter for JDBC를 사용하여 복제한 데이터를 전제로 한다.

dataCompJ는 편리한 사용성과 빠른 성능으로, 효율적인 이기종 데이터베이스 간 데이터 관리 방법을 제공한다.

### 시스템 요구 사항

이 절은 dataCompJ를 설치하고 실행하기 위해 필요한 시스템 사양에 대해
설명하고, dataCompJ와 호환되는 데이터베이스 관리 시스템을 열거한다.

- 하드웨어 요구 사항
- 소프트웨어 요구 사항
- 호환되는 데이터베이스 시스템

#### 하드웨어 요구 사항

- 확인받아야 하는 부분@@@@@@@@@@@@@@@#$%^&*(*&^%$!@#$%^&*()*&^%$#@)

#### 소프트웨어 요구 사항

- Oracle, OpenJDK 또는 IBM Java 8 이상의 JRE

dataCompJ는 순수 Java 기반 클라이언트 애플리케이션으로 하드웨어 및 운영체제에 상관없이 독립적으로 실행되나, 자바 런타임 환경(JRE)에 의존적이므로 환경에 맞는 JRE를 설치해야 한다. 또한 설치된 Java의 경로를 가리키는 JAVA_HOME 환경변수가 설정되어 있어야 한다.

#### 호환되는 데이터베이스 관리 시스템

##### Master 데이터베이스

- Altibase: Altibase 5.3.3 이상

##### Slave 데이터베이스

- Oracle: Oracle 9i 이상
- MariaDB: MariaDB 5.5.x 이상

Master/Slave DB의 의미는 ['용어](#용어)'절을 참조한다.

dataCompJ는 Altibase 및 이기종 데이터베이스들과 함께 사용할 수 있다. 데이터베이스 접속을 위해 JDBC 드라이버를 사용하므로, 원본 데이터베이스와 대상 데이터베이스에 호환되는 JDBC 드라이버를 준비하는 것이 중요하다. 사용자 편의를 위해 지원되는 데이터베이스에 적합한 몇 가지 JDBC 드라이버를 dataCompJ와 함께 제공한다.

### 용어

##### Master DB

비교 대상인 두 이기종 데이터베이스 중 원본 데이터를 가진 Altibase
데이터베이스이다.

##### Slave DB

비교 대상인 두 이기종 데이터베이스 중 복제된 데이터가 적용되는 다른 벤더의 데이터베이스이다.

##### TablePair

사용자가 지정하는 dataCompJ의 비교 대상을 의미하며 테이블 단위이다. Master DB에 있는 하나의 테이블(Master table)과 Slave DB에 있는 하나의 테이블(Slave table)이 쌍을 이룬다.

##### Master 테이블

TablePair 중 사용자가 지정한 Master DB의 비교 대상 테이블이다.

##### Slave 테이블

TablePair 중 사용자가 지정한 Slave DB의 비교 대상 테이블이다.

### 불일치 레코드(Inconsistent record)

##### 불일치 레코드 

Master 테이블과 Slave 테이블의 주요 키(Primary Key)를 기준으로 컬럼 값이 일치하지 않는 레코드들을 의미한다. 불일치 레코드 종류는 다음과 같이 세 가지 타입이 있다.

##### MOSO 불일치

동일한 주요 키 컬럼들(Primary key columns) 값을 가진 특정 레코드가 Master 테이블과 Slave 테이블에 모두 존재하지만, 주요 키가 아닌 컬럼들(Non primary key columns)의 값이 서로 다른 경우

##### MOSX 불일치

특정 주요 키 컬럼들(Primary key columns) 값을 가진 레코드가 Master 테이블에만 존재하고 Slave 테이블에는 존재하지 않는 경우

##### MXSO 불일치

특정 주요 키 컬럼들(Primary key columns) 값을 가진 레코드가 Master 테이블에는 존재하지 않고 Slave 테이블에만 존재하는 경우

##### 불일치 레코드 처리

dataCompJ는 불일치 레코드 발견 시 dataCompJ 환경 파일에 기술된 사용자의 선택에 따라 다음의 두 가지 기능을 제공한다.

1.  DIFF: Master 테이블과 Slave 테이블 간의 불일치 레코드를 식별하여 CSV 형식의 파일에 기록한다.
2.  SYNC: Master 테이블과 Slave 테이블 간의 불일치 레코드를 식별하여 dataCompJ 환경 파일에 기술된 일치 정책에 따라 불일치를 해소한다.

### 일치 정책 (Synchronization policy)

일치 정책은 dataCompJ가 불일치 레코드를 발견하였을 때, Master 테이블의 레코드를 기준으로 Slave 테이블의 레코드를 어떻게 일치시킬지 명시하는 정책이다. 일치 정책으로 다음과 같은 세 가지 방법을 제공한다.

##### MOSO 불일치

UPDATE_TO_SLAVE 정책이다. Master 테이블의 레코드를 기준으로 동일한 주요 키를 가진 Slave 테이블의 레코드를 변경(update)한다.

##### MOSX 불일치

INSERT_TO_SLAVE 정책이다. Master 테이블에만 존재하고 Slave
테이블에는 존재하지 않는 레코드를 Slave 테이블에 삽입(insert)한다.

##### MXSO 불일치

DELETE_FROM_SLAVE 정책이다. Master 테이블에는 존재하지 않고 Slave 테이블에만 존재하는 레코드를 Slave 테이블에서 삭제(delete)한다.