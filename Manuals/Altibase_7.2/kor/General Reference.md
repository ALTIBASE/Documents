<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [General Reference](#general-reference)
  - [서문](#%EC%84%9C%EB%AC%B8)
    - [이 매뉴얼에 대하여](#%EC%9D%B4-%EB%A7%A4%EB%89%B4%EC%96%BC%EC%97%90-%EB%8C%80%ED%95%98%EC%97%AC)
  - [1.자료형](#1%EC%9E%90%EB%A3%8C%ED%98%95)
    - [자료형의 개요](#%EC%9E%90%EB%A3%8C%ED%98%95%EC%9D%98-%EA%B0%9C%EC%9A%94)
    - [문자형 데이터 타입](#%EB%AC%B8%EC%9E%90%ED%98%95-%EB%8D%B0%EC%9D%B4%ED%84%B0-%ED%83%80%EC%9E%85)
    - [숫자형 데이터 타입](#%EC%88%AB%EC%9E%90%ED%98%95-%EB%8D%B0%EC%9D%B4%ED%84%B0-%ED%83%80%EC%9E%85)
    - [날짜형 데이타 타입](#%EB%82%A0%EC%A7%9C%ED%98%95-%EB%8D%B0%EC%9D%B4%ED%83%80-%ED%83%80%EC%9E%85)
    - [이진 데이터 타입](#%EC%9D%B4%EC%A7%84-%EB%8D%B0%EC%9D%B4%ED%84%B0-%ED%83%80%EC%9E%85)
    - [LOB 데이타 타입](#lob-%EB%8D%B0%EC%9D%B4%ED%83%80-%ED%83%80%EC%9E%85)
    - [공간 데이터 타입](#%EA%B3%B5%EA%B0%84-%EB%8D%B0%EC%9D%B4%ED%84%B0-%ED%83%80%EC%9E%85)
  - [2.Altibase 프로퍼티](#2altibase-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [환경 설정 방법](#%ED%99%98%EA%B2%BD-%EC%84%A4%EC%A0%95-%EB%B0%A9%EB%B2%95)
    - [프로퍼티 요약](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0-%EC%9A%94%EC%95%BD)
    - [데이터베이스 초기화 프로퍼티](#%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4-%EC%B4%88%EA%B8%B0%ED%99%94-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 관련 프로퍼티](#%EC%84%B1%EB%8A%A5-%EA%B4%80%EB%A0%A8-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Altibase® Administration

# General Reference

[![img](https://github.com/haeinnmin/Documents/raw/master/Manuals/Altibase_7.2/kor/media/GeneralReference/e5cfb3761673686d093a3b00c062fe7a.png)](https://github.com/haeinnmin/Documents/blob/master/Manuals/Altibase_7.2/kor/media/GeneralReference/e5cfb3761673686d093a3b00c062fe7a.png)

Altibase Administration General Reference

Release 7.2

Copyright ⓒ 2001~2021 Altibase Corp. All Rights Reserved.

본 문서의 저작권은 ㈜알티베이스에 있습니다. 이 문서에 대하여 당사의 동의 없이 무단으로 복제 또는 전용할 수 없습니다.

**㈜알티베이스**

08378 서울시 구로구 디지털로 306 대륭포스트타워Ⅱ 10층

전화: 02-2082-1114 팩스: 02-2082-1099

고객서비스포털: [http://support.altibase.com](http://support.altibase.com/)

homepage: [http://www.altibase.com](http://www.altibase.com/)

## 서문

### 이 매뉴얼에 대하여

이 매뉴얼은 Altibase의 기능, 제품 구성요소, 그리고 사용법에 대해 설명한다.

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

#### 소프트웨어 환경

이 매뉴얼은 데이터베이스 서버로 Altibase 버전 7.2를 사용한다는 가정 하에 작성되었다.

#### 이 매뉴얼의 구성

이 매뉴얼은 다음과 같이 구성되어 있다.

- 제 1장 자료형
  이 장은 Altibase에서 지원하는 데이터 타입에 대해 설명한다.
- 제 2장 Altibase 프로퍼티
  이 장은 Altibase 프로퍼티에 대해 설명한다.
- 제 3장 데이터베이스 객체 및 권한 관리
  이 장은 Altibase 데이터 딕셔너리에 대해 설명한다. Altibase의 데이터 딕셔너리는 데이터베이스 객체 정보를 저장하는 메타 테이블과 시스템 프로세스 정보를 저장하는 프로세스 테이블로 나뉘어진다.
- 제 4장 샘플 스키마
  이 장은 샘플로 제공되는 테이블 정보와 ER 다이어그램을 제공한다.

#### 문서화 규칙

이 절에서는 이 매뉴얼에서 사용하는 규칙에 대해 설명한다. 이 규칙을 이해하면 이 매뉴얼과 설명서 세트의 다른 매뉴얼에서 정보를 쉽게 찾을 수 있다.

여기서 설명하는 규칙은 다음과 같다.

- 구문 다이어그램
- 샘플 코드 규칙

##### 구문 다이어그램

이 매뉴얼에서는 다음 구성 요소로 구축된 다이어그램을 사용하여, 명령문의 구문을 설명한다.

| 구성 요소                                                    | 의미                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [![img](https://github.com/haeinnmin/Documents/raw/master/Manuals/Altibase_7.2/kor/media/GeneralReference/image004.gif)](https://github.com/haeinnmin/Documents/blob/master/Manuals/Altibase_7.2/kor/media/GeneralReference/image004.gif) | 명령문이 시작한다. 완전한 명령문이 아닌 구문 요소는 화살표로 시작한다. |
| [![img](https://github.com/haeinnmin/Documents/raw/master/Manuals/Altibase_7.2/kor/media/GeneralReference/image006.gif)](https://github.com/haeinnmin/Documents/blob/master/Manuals/Altibase_7.2/kor/media/GeneralReference/image006.gif) | 명령문이 다음 라인에 계속된다. 완전한 명령문이 아닌 구문 요소는 이 기호로 종료한다. |
| [![img](https://github.com/haeinnmin/Documents/raw/master/Manuals/Altibase_7.2/kor/media/GeneralReference/image008.gif)](https://github.com/haeinnmin/Documents/blob/master/Manuals/Altibase_7.2/kor/media/GeneralReference/image008.gif) | 명령문이 이전 라인으로부터 계속된다. 완전한 명령문이 아닌 구문 요소는 이 기호로 시작한다. |
| [![img](https://github.com/haeinnmin/Documents/raw/master/Manuals/Altibase_7.2/kor/media/GeneralReference/image010.gif)](https://github.com/haeinnmin/Documents/blob/master/Manuals/Altibase_7.2/kor/media/GeneralReference/image010.gif) | 명령문이 종료한다.                                           |
| [![img](https://github.com/haeinnmin/Documents/raw/master/Manuals/Altibase_7.2/kor/media/GeneralReference/image012.gif)](https://github.com/haeinnmin/Documents/blob/master/Manuals/Altibase_7.2/kor/media/GeneralReference/image012.gif) | 필수 항목                                                    |
| [![img](https://github.com/haeinnmin/Documents/raw/master/Manuals/Altibase_7.2/kor/media/GeneralReference/image014.gif)](https://github.com/haeinnmin/Documents/blob/master/Manuals/Altibase_7.2/kor/media/GeneralReference/image014.gif) | 선택적 항목                                                  |
| [![img](https://github.com/haeinnmin/Documents/raw/master/Manuals/Altibase_7.2/kor/media/GeneralReference/image016.gif)](https://github.com/haeinnmin/Documents/blob/master/Manuals/Altibase_7.2/kor/media/GeneralReference/image016.gif) | 선택사항이 있는 필수 항목. 한 항목만 제공해야 한다.          |
| [![img](https://github.com/haeinnmin/Documents/raw/master/Manuals/Altibase_7.2/kor/media/GeneralReference/image018.gif)](https://github.com/haeinnmin/Documents/blob/master/Manuals/Altibase_7.2/kor/media/GeneralReference/image018.gif) | 선택사항이 있는 선택적 항목.                                 |
| [![img](https://github.com/haeinnmin/Documents/raw/master/Manuals/Altibase_7.2/kor/media/GeneralReference/image020.gif)](https://github.com/haeinnmin/Documents/blob/master/Manuals/Altibase_7.2/kor/media/GeneralReference/image020.gif) | 선택적 항목. 여러 항목이 허용된다. 각 반복 앞부분에 콤마가 와야 한다. |

##### 샘플 코드 규칙

코드 예제는 SQL, Stored Procedure, iSQL, 또는 다른 명령 라인 구문들을 예를 들어 설명한다.

아래 테이블은 코드 예제에서 사용된 인쇄 규칙에 대해 설명한다.

| 규칙         | 의미                                                         | 예제                                                         |
| ------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ ]          | 선택 항목을 표시                                             | VARCHAR [(*size*)][[FIXED \|] VARIABLE]                      |
| { }          | 필수 항목 표시. 반드시 하나 이상을 선택해야 되는 표시        | { ENABLE \| DISABLE \| COMPILE }                             |
| \|           | 선택 또는 필수 항목 표시의 인자 구분 표시                    | { ENABLE \| DISABLE \| COMPILE } [ ENABLE \| DISABLE \| COMPILE ] |
| . . .        | 그 이전 인자의 반복 표시 예제 코드들의 생략되는 것을 표시    | SQL> SELECT ename FROM employee; ENAME ------------------------ SWNO HJNO HSCHOI . . . 20 rows selected. |
| 그 밖에 기호 | 위에서 보여진 기호 이 외에 기호들                            | EXEC :p1 := 1; acc NUMBER(11,2);                             |
| 기울임 꼴    | 구문 요소에서 사용자가 지정해야 하는 변수, 특수한 값을 제공해야만 하는 위치 | SELECT * FROM *table_name*; CONNECT *userID*/*password*;     |
| 소문자       | 사용자가 제공하는 프로그램의 요소들, 예를 들어 테이블 이름, 칼럼 이름, 파일 이름 등 | SELECT ename FROM employee;                                  |
| 대문자       | 시스템에서 제공하는 요소들 또는 구문에 나타나는 키워드       | DESC SYSTEM_.SYS_INDICES_;                                   |

#### 관련 자료

자세한 정보를 위하여 다음 문서 목록을 참조한다.

- Installation Guide
- Getting Started Guide
- Administrator’s Manual
- Replication Manual

#### Altibase는 여러분의 의견을 환영합니다.

이 매뉴얼에 대한 여러분의 의견을 보내주시기 바랍니다. 사용자의 의견은 다음 버전의 매뉴얼을 작성하는데 많은 도움이 됩니다. 보내실 때에는 아래 내용과 함께 고객서비스포털( http://support.altibase.com/kr/ )로 보내주시기 바랍니다.

- 사용 중인 매뉴얼의 이름과 버전
- 매뉴얼에 대한 의견
- 사용자의 성함, 주소, 전화번호

이 외에도 Altibase 기술지원 설명서의 오류와 누락된 부분 및 기타 기술적인 문제들에 대해서 이 주소로 보내주시면 정성껏 처리하겠습니다. 또한, 기술적인 부분과 관련하여 즉각적인 도움이 필요한 경우에도 고객서비스포털을 통해 서비스를 요청하시기 바랍니다.

여러분의 의견에 항상 감사드립니다.

## 1.자료형

SQL을 사용하여 데이타베이스에 데이타를 저장, 변경하고 질의하기 위해서는 데이타베이스의 자료형에 대한 이해가 선행되어야 한다. 이 장에서는 Altibase가 지원하는 데이타형에 대해서 자세히 설명한다.

### 자료형의 개요

#### 데이타형의 종류

Altibase에서 지원하는 데이타형은 다음과 같다.

##### 문자형 데이타형

| M: 정의된 칼럼 길이 L: 입력 문자열의 길이 |                              |                                                              |
| ----------------------------------------- | ---------------------------- | ------------------------------------------------------------ |
| 타 입                                     | Length                       | Size                                                         |
| CHAR(M)                                   | 1 ~ 32000                    | M + 2                                                        |
| VARCHAR(M)                                | 1 ~ 32000                    | length + 2, 여기서 입력 값이 가변영역에 저장되면, length = L 입력 값이 고정영역에 저장되면, length = M |
| NCHAR(M)                                  | 1~16000(UTF16) 1~10666(UTF8) | M*2 + 2(UTF16) M*3 + 2(UTF8)                                 |
| NVARCHAR(M)                               | 1~16000(UTF16) 1~10666(UTF8) | length*2 + 2(UTF16) length*3 + 2(UTF8) 여기서: 입력 값이 가변영역에 저장되면, length = L 입력 값이 고정영역에 저장되면, length = M |

NCHAR와 NVARCHAR는 유니코드 문자형 타입이다. UTF16으로 인코딩된 문자열의 최대 길이는 UTF8로 인코딩된 문자열의 최대 길이와 다르다.

##### 숫자형 데이타형

| Non-native   | 타 입               | Precision   | Scale               | Size (bytes)                                                 | 비 고 |
| ------------ | ------------------- | ----------- | ------------------- | ------------------------------------------------------------ | ----- |
| NUMERIC      | 38                  | 0           | 3+((precision)+2)/2 | *고정 소수점 숫자 *DECIMAL은 NUMERIC과 동일한 데이터 타입이다. |       |
| NUMERIC(p)   | 1 ~ 38              | 0           |                     |                                                              |       |
| NUMERIC(p,s) | 1 ~ 38              | -84 ~ 128   |                     |                                                              |       |
| DECIMAL      | 38                  | 0           |                     |                                                              |       |
| DECIMAL(p)   | 1 ~ 38              | 0           |                     |                                                              |       |
| DECIMAL(p,s) | 1 ~ 38              | -84 ~ 128   |                     |                                                              |       |
| NUMBER(p)    | 1 ~ 38              | 0           |                     |                                                              |       |
| NUMBER(p,s)  | 1 ~ 38              | -84 ~ 128   |                     |                                                              |       |
| NUMBER       | 38                  | X           | 3+((precision)+2)/2 | *부동 소수점 숫자                                            |       |
| FLOAT        | 38                  | X           |                     |                                                              |       |
| FLOAT(p)     | 1 ~ 38              | X           |                     |                                                              |       |
| Native       | 타입                | 호환 C Type | Size(bytes)         | 비고                                                         |       |
| DOUBLE       | double              | 8           | *부동 소수점 숫자   |                                                              |       |
| REAL         | float               | 4           |                     |                                                              |       |
| BIGINT       | long 또는 long long | 8           | *정수형             |                                                              |       |
| INTEGER      | int                 | 4           |                     |                                                              |       |
| SMALLINT     | short               | 2           |                     |                                                              |       |

###### 예제

예제1. 고정 소수점 숫자 크기 계산 : ( 3 + ( ( p ) + 2 ) / 2 )

```
- NUMERIC  
  NUMERIC(38, 0): 크기 = 3 + 40/2 = 23 bytes

- NUMERIC(p) / NUMERIC(p, 0)  
  NUMERIC(10): 크기 = 3 + 12/2 = 9 bytes

- NUMERIC(p, s)  
  NUMERIC(10, 9): 크기 = 3 + 12/2 = 9 bytes
  
- DECIMAL: NUMERIC과 동일

- DECIMAL(p): NUMERIC(p)과 동일

- DECIMAL(p,s): NUMERIC(p,s)과 동일

- NUMBER(p): NUMERIC(p)과 동일

- NUMBER(p,s): NUMERIC(p,s)과 동일
```

예제2. 부동 소수점 숫자 크기 계산: ( 3 + ( ( p ) + 2 ) / 2 )

```
- FLOAT  
  FLOAT(38): 크기 = 3 + 40/2 = 23 bytes
  
- FLOAT(p)  
  FLOAT(20): 크기 = 3 + 22/2 = 14 bytes
  
- NUMBER: FLOAT과 동일
```

**날짜 데이타형**

| 타 입 | Size (byte) |
| :---: | :---------: |
| DATE  |      8      |

**이진 데이타형**

<table>
    <tr>
    	<td colspan="3">M: 정의된 칼럼 길이<br/>L: 입력 문자열의 길이
</td>
    </tr>
    <tr>
    	<th>타 입</th>
        <th>Length</th>
        <th>Size</th>
    </tr>
    <tr>
    	<td>BLOB/CLOB</td>
        <td></td>
        <td>1~4294967295</td>
    </tr>
    <tr>
    	<td>BYTE</td>
        <td>1~32000</td>
        <td>M + 2</td>
    </tr>
     <tr>
    	<td>NIBBLE</td>
        <td>1~254</td>
        <td>M/2 + 1</td>
    </tr>
     <tr>
    	<td>BIT</td>
        <td>1~64000</td>
        <td>M/8 + 4</td>
    </tr>
    <tr>
    	<td>VARBIT</td>
        <td>1~64000</td>
        <td>length/8 + 4, 여기서
입력 값이 가변영역에 저장되면, length = L
입력 값이 고정영역에 저장되면, length = M
</td>
    </tr>
    </table>

**공간 데이타형**

|  타 입   |   Length    | Size (byte) |
| :------: | :---------: | :---------: |
| GEOMETRY | 8~104857600 | length + 40 |

실제 레코드의 크기는 위에 각 데이터형 별로 명시된 크기(bytes)에서 헤더 정보 크기 만큼 추가된다. 헤더 정보는 운영체제에 따라 다를 수 있다.

#### NULL

행을 테이블에 삽입할 때 열의 값을 모르거나 값이 아직 결정되지 않은 경우, 즉 값이 존재 하지 않는 것을 나타내는 경우에 널(NULL)이 사용된다. 널(NULL)은 0 또는 공백과는 다르며, 비교연산이나 저장시 특별하게 취급된다.

NVL() 함수, IS NULL 조건, IS NOT NULL 조건을 제외한 수식 연산에 널이 포함되면, 최종 연산의 결과는 널이 된다. 즉, 수식에 널이 포함되면 비교 또는 연산이 의미가 없어지게 된다.

테이블 생성시 NOT NULL 또는 PRIMARY KEY로 정의되지 않은 모든 데이타 유형의 칼럼에는 널을 입력할 수 있다.

#### 묵시적 데이터 타입 변환

서로 다른 데이터 타입에 대한 연산을 수행할 때 정확한 연산을 위해 데이터 타입이 변환되어 수행된다. 변환 방법은 묵시적인 방법과 명시적인 방법이 있다.

묵시적 변환이란, 타입이 다른 데이터를 연산할 때에는 내부적으로 데이터 타입을 변환하지만 데이터 타입의 속성은 유지되는 것을 의미한다. 같은 데이터 타입의 두 값을 비교 연산할 때, 어떤 변환 없이 직접 그 값에 대해 비교 연산이 수행된다. 그러나 비교되는 두 값의 데이타 타입이 다른 경우 한 쪽 값을 다른 값의 데이터 타입으로 변환한 후 비교 연산이 수행된다.

다음의 테이블은 묵시적 데이터 타입의 변환 가능한 행렬을 나타낸다 (O: 데이터 타입이 변환되어도 속성이 유지되는 것에 표시). 기존 테이블의 데이터 타입을 MODIFY 구문으로 변환하는 방법은 SQL Reference의 *modify_column_clause* 구문을 참조한다.

| 변환후 변환전 | char | var char | nchar | nvarchar | clob | big int | deci mal | dou ble | float | int eger | num ber | num eric | real | small int | date | blob | byte | varbyte | nibble | bit  | varbit | geometry |
| ------------- | :--: | :------: | :---: | :------: | :--: | :-----: | :------: | :-----: | :---: | :------: | :-----: | :------: | :--: | :-------: | :--: | :--: | :--: | :-----: | :----: | :--: | :----: | :------: |
| char          |  o   |    o     |   o   |    o     |      |    o    |    o     |    o    |   o   |    o     |    o    |    o     |  o   |     o     |  o   |      |      |         |        |      |        |          |
| varchar       |  o   |    o     |   o   |    o     |  o   |    o    |    o     |    o    |   o   |    o     |    o    |    o     |  o   |     o     |  o   |      |      |         |        |      |        |          |
| nchar         |  o   |    o     |   o   |    o     |      |    o    |    o     |    o    |   o   |    o     |    o    |    o     |  o   |     o     |  o   |      |      |         |        |      |        |          |
| nvarchar      |  o   |    o     |   o   |    o     |  o   |    o    |    o     |    o    |   o   |    o     |    o    |    o     |  o   |     o     |  o   |      |      |         |        |      |        |          |
| clob          |      |          |       |          |  o   |         |          |         |       |          |         |          |      |           |      |      |      |         |        |      |        |          |
| bigint        |  o   |    o     |   o   |    o     |      |    o    |    o     |    o    |   o   |    o     |    o    |    o     |  o   |     o     |      |      |      |         |        |      |        |          |
| decimal       |  o   |    o     |   o   |    o     |      |    o    |    o     |    o    |   o   |    o     |    o    |    o     |  o   |     o     |      |      |      |         |        |      |        |          |
| double        |  o   |    o     |   o   |    o     |      |    o    |    o     |    o    |   o   |    o     |    o    |    o     |  o   |     o     |      |      |      |         |        |      |        |          |
| float         |  o   |    o     |   o   |    o     |      |    o    |    o     |    o    |   o   |    o     |    o    |    o     |  o   |     o     |      |      |      |         |        |      |        |          |
| integer       |  o   |    o     |   o   |    o     |      |    o    |    o     |    o    |   o   |    o     |    o    |    o     |  o   |     o     |      |      |      |         |        |      |        |          |
| number        |  o   |    o     |   o   |    o     |      |    o    |    o     |    o    |   o   |    o     |    o    |    o     |  o   |     o     |      |      |      |         |        |      |        |          |
| numeric       |  o   |    o     |   o   |    o     |      |    o    |    o     |    o    |   o   |    o     |    o    |    o     |  o   |     o     |      |      |      |         |        |      |        |          |
| real          |  o   |    o     |   o   |    o     |      |    o    |    o     |    o    |   o   |    o     |    o    |    o     |  o   |     o     |      |      |      |         |        |      |        |          |
| smallint      |  o   |    o     |   o   |    o     |      |    o    |    o     |    o    |   o   |    o     |    o    |    o     |  o   |     o     |      |      |      |         |        |      |        |          |
| date          |  o   |    o     |   o   |    o     |      |         |          |         |       |          |         |          |      |           |  o   |      |      |         |        |      |        |          |
| blob          |      |          |       |          |      |         |          |         |       |          |         |          |      |           |      |  o   |      |         |        |      |        |          |
| byte          |      |          |       |          |      |         |          |         |       |          |         |          |      |           |      |  o   |  o   |    o    |        |      |        |          |
| varbyte       |      |          |       |          |      |         |          |         |       |          |         |          |      |           |      |  o   |  o   |    o    |        |      |        |          |
| nibble        |      |          |       |          |      |         |          |         |       |          |         |          |      |           |      |      |      |         |   o    |      |        |          |
| bit           |      |          |       |          |      |         |          |         |       |          |         |          |      |           |      |      |      |         |        |  o   |   o    |          |
| varbit        |      |    o     |       |          |      |         |          |         |       |          |         |          |      |           |      |      |      |         |        |  o   |   o    |          |
| geometry      |      |          |       |          |      |         |          |         |       |          |         |          |      |           |      |      |      |         |        |      |        |    o     |

##### 묵시적 데이터 타입 변환 규칙

테이블 t10 테이블에 bit 타입의 '1000'을 입력하면 integer '1000'으로 변환은 성공하지만, 데이터 타입의 속성이 달라지기 때문에 묵시적인 데이터 타입 변환이라고 볼 수 없다.

```
iSQL> create table t10 (i1 integer);
Create success.
iSQL> insert into t10 values (bit'1000');
1 row inserted.
iSQL> select * from t10;
I1
--------------
1000
1 row selected.
```

따라서 묵시적 데이터 타입의 변환은 아래와 같은 규칙을 따른다.

- 숫자형 데이터 타입과 문자형 데이터 타입의 비교 연산 또는 사칙 연산시, 문자형 데이터 타입을 숫자형 데이터 타입으로 변환하여 수행한다.
- 날짜형 데이터 타입과 문자형 데이터 타입의 비교 연산시, 문자형 데이터 타입을 날짜형 데이터 타입으로 변환하여 비교 연산을 수행한다.
- 테이터 타입의 변환이 불가능한 연산은 무효화 된다.
- 함수에서 사용되는 인자는 함수에서 정의된 인자의 데이터 타입으로 변환한다.
- 문자형 데이터 타입이나 십진 정밀도(decimal precision)를 사용하는 수치형 데이터 타입을 이진 정밀도(binary precision)를 사용하는 부동소수점 수치형 데이터 타입으로 변환하면 값이 손실될 수 있다.
- INSERT, UPDATE 실행시 INSERT, UPDATE 되는 칼럼의 데이터 타입으로 데이터형이 변환된다.

##### 예제

<질의> 숫자형 테이터 타입과 문자형 테이터 타입의 비교 연산시 문자형 데이터 타입 '10'은 숫자형 데이터로 변환된다.

```
iSQL> create table emp (empno integer, name varchar(10), hire_date date);
insert into emp values (10,'altibase', '10-nov-2015');

iSQL> select name from emp where empno = '10';
NAME
--------------
altibase
1 row selected.
```

<질의> 숫자형 데이터 타입과 문자형 데이터 타입 간 사칙연산시 문자형 데이터 타입 '10'은 숫자형 데이터 타입으로 변환된다.

```
iSQL> select empno + '10' from emp;
EMPNO+'10'
-------------------------
20
1 row selected.
```

<질의> 날짜형 데이터 타입과 문자형 데이터 타입의 비교 연산시 문자형 데이터 타입 '10-nov-2015'은 날짜형 데이터 타입으로 변환된다.

```
iSQL> select hire_date from emp where hire_date = '10-nov-2015';
HIRE_DATE
---------------
10-NOV-2015
1 row selected.
```

<질의> 숫자형 데이터 타입과 문자형 데이터 타입 간 사칙연산시 이진 데이터 타입은 숫자형 데이터 타입으로 변환할 수 없어 연산이 무효화된다.

```
iSQL> select empno + cast(12345 as nibble(6)) from emp;
[ERR-2100C : Conversion not applicable.
0001 : select EMPNO + CAST(12345 as NIBBLE(6)) from EMP
             ^                               ^
]
```

<질의> 함수 SUM에 문자형 데이터 타입 '10'을 인자로 받는 경우 숫자형 데이터로 변환된다.

```
iSQL> select sum('10') from dual;
SUM('10')
--------------
10
1 row selected.
```

<질의> 문자형 데이터 타입 '12.123456789'을 부동소수점 숫자형 데이터 타입인 float으로 변환하면, 유효 자릿수는 float(11)로 되어 값의 손실이 발생한다.

```
iSQL> select float'12.123456789' from dual;
FLOAT'12.123456789'
----------------------
12.1234568
1 row selected.
```

<질의> INSERT 되는 숫자형 데이터의 값은 INSERT 되는 칼럼의 데이터 유형에 맞게 변환되어 값이 INSERT 된다.

```
iSQL>  create table t1 ( i1 char(10), i2 integer, i3 double);
Create success.
iSQL>  insert into t1 values (integer'1020', char'1928', float'123.1234');
1 row inserted.
iSQL>     select * from t1;
I1          I2          I3
---------------------------------------------------
1020        1928        123.1234
1 row selected.
```

#### 명시적 데이터 타입 변환

명시적 데이터 타입 변환은 SQL 변환 함수 또는 아래와 같이 타입 캐스팅을 사용해서 명시적으로 수행될 수 있다. 데이터 타입을 변환하는 SQL 함수는 SQL Reference에서 설명한다.

##### 구문

```
datatype '문자 또는 상수 literal '
```

##### 예제

어떤 데이터 타입의 상수 테이터를 명시적으로 다른 데이터 타입으로 변환한다. 다음은 157.27의 숫자 값을 '157.27'의 문자열로 변환하는 예제이다.

```
CHAR '157.27'
```

#### 문자열 표기

SQL쿼리에서 문자열을 표기할 시에는 홀 따옴표(‘)로 문자열을 묶어서 사용한다. 홀 따옴표를 문자열로 표기할 시에는 홀 따옴표가 escape문자가 되므로 앞에 홀 따옴표를 붙여줘야 한다.

##### 예제

```
SELECT * FROM EMPLOYEE WHERE NAME = ’KIM’;
INSERT INTO EMPLOYEE VALUES (‘GILDONG’’’);//GILDONG’ 값을 삽입
SELECT * FROM REMOTE_TABLE(link1, ‘SELECT * FROM EMPLOYEE WHERE NAME=‘’KIM‘’’; //''는 쌍 따옴표가 아니라 홀 따옴표 두 개임
```

#### FIXED/VARIABLE 옵션

FIXED와 VARIABLE은 칼럼의 데이터가 어느 영역에 저장될 지를 지정하는 키워드이다.

한 레코드 전체가 연속된 공간에 저장될 때, 이 공간을 고정(FIXED) 영역이라고 한다. 칼럼들 중의 하나가 그 레코드의 나머지 연속된 고정 영역이 아닌 다른 분리된 공간에 저장될 때, 이 칼럼은 가변(VARIABLE) 영역에 저장된다고 말한다.

한 칼럼이 가변 영역에 저장될 때, 데이터 길이와 실제 데이터가 저장된 위치를 가리키는 포인터 같은 그 칼럼의 헤더 정보는 고정 영역에 저장된다. 반면 칼럼의 데이터는 가변 영역에 저장된다.

디스크 테이블스페이스에 테이블 생성시, 사용자가 FIXED 또는 VARIABLE을 지정하더라도 이는 무시되고 테이블의 모든 칼럼은 FIXED로 처리된다. 그러나 메모리 테이블스페이스에 테이블을 생성할 때는 사용자가 명시한 옵션이 그대로 사용된다.

그러나, 모든 LOB 데이터 타입 칼럼의 데이터는 항상 VARIABLE로 처리되고, 그 데이터는 IN ROW 절에 지정된 값에 따라서 고정 또는 가변 영역에 저장될 수 있다.

다음의 데이터 타입에 대해 VARIABLE을 지정할 수 있다.
: CHAR, VARCHAR, NCHAR, NVARCHAR, BYTE, VARBATE, NIBBLE, BIT, VARBIT, BLOB, 및 CLOB

#### IN ROW 절

이 절은 가변 영역에 저장되는 칼럼 데이터에만 관련이 있다. 테이블 생성시 FIXED와 IN ROW 절이 모두 명시되면, IN ROW 절은 무시된다. VARIABLE로 지정된 칼럼에 데이터가 입력될 때, 데이터의 길이가 IN ROW 절에 명시된 값 이하이면 데이터는 고정 영역에 저장될 것이다. 반면 데이터의 길이가 IN ROW 절에 명시된 값보다 크면, 데이터는 가변 영역에 저장될 것이다.

여기서 “데이터의 길이”는 입력된 데이터의 길이가 아니고, 메모리 또는 디스크에 실제로 저장될 데이터의 길이를 의미하는데, 이는 입력 데이터의 길이보다 다소 크다. 예를 들어, 칼럼이 ‘VARCHAR(400) IN ROW 200’으로 정의 되었다면, 입력 데이터의 길이가 198 (데이터 저장시 2바이트가 추가로 더 필요하다) 이하일 때 데이터는 고정 영역에 저장될 것이다.

고정 영역에 저장되는 LOB 데이터의 기본 크기는 메모리 테이블을 위한 MEMORY_LOB_COLUMN_IN_ROW_SIZE 프로퍼티와 디스크 테이블을 위한 DISK_LOB_COLUMN_IN_ROW_SIZE 프로퍼티를 사용해서 지정할 수 있다. 또한, VARIABLE 옵션이 지정된 다른 데이터 타입의 칼럼을 위한 기본 크기는 MEMORY_VARIABLE_COLUMN_IN_ROW_SIZE 프로퍼티를 사용해서 명시할 수 있다. 이들 프로퍼티를 지정하면 테이블 생성시 각 칼럼에 반복적으로 IN ROW 절을 사용할 필요가 없다.

이들 프로퍼티에 대한 상세한 설명은 2장을 참고하기 바란다.

### 문자형 데이터 타입

문자 데이터 타입은 데이터베이스 문자 집합 또는 국가 문자 집합의 문자 데이터를 저장하는데 사용된다.

Altibase는 아래의 타입을 지원한다.

- CHAR
- VARCHAR
- NCHAR
- NVARCHAR

#### CHAR

##### 흐름도

[![img](https://github.com/haeinnmin/Documents/raw/master/Manuals/Altibase_7.2/kor/media/GeneralReference/242f2c3edb0f197d371a4ec74f665ba8.jpg)](https://github.com/haeinnmin/Documents/blob/master/Manuals/Altibase_7.2/kor/media/GeneralReference/242f2c3edb0f197d371a4ec74f665ba8.jpg)

##### 구문

```
CHAR [(size)] [ FIXED | VARIABLE [IN ROW size] ]
```

##### 설명

명시된 크기(size)만큼 고정 길이를 가지는 문자형 데이터 타입이다. 명시된 전체 크기에 비해 입력 값의 길이가 작을 경우 뒷부분은 공백으로 채워진다.

CHAR 칼럼의 기본 크기는 1 바이트이며 최대 길이는 32000바이트이다.

FIXED 와 VARIABLE 절에 대한 자세한 설명은 앞서 기술한 "FIXED/VARIABLE 옵션"과 "IN ROW 절"을 참고한다.

#### VARCHAR

##### 흐름도

[![img](https://github.com/haeinnmin/Documents/raw/master/Manuals/Altibase_7.2/kor/media/GeneralReference/f7552045fb1b327e02cba948bbafeb3f.jpg)](https://github.com/haeinnmin/Documents/blob/master/Manuals/Altibase_7.2/kor/media/GeneralReference/f7552045fb1b327e02cba948bbafeb3f.jpg)

##### 구문

```
VARCHAR [(size)] [ FIXED | VARIABLE [IN ROW size] ]
```

##### 설명

명시된 크기 내에서 가변 길이를 가지는 문자형 데이터 타입이다.

VARCHAR 칼럼의 기본 크기는 1 바이트이며 최대 길이는 32000바이트이다.

VARCHAR는 가변 길이 데이터 타입이다. 즉, 입력 데이터의 길이가 정의된 칼럼의 크기보다 작을 경우, 실제로 입력된 데이터만 저장된다. 반면, CHAR 데이터 타입의 경우 입력 데이터의 길이가 칼럼 크기보다 작으면 그 칼럼의 남는 공간은 공백으로 채워진다. 예를 들어, CHAR(10)으로 정의된 칼럼에 단어 "magic"이 입력되면, 이 데이터는 "magic_____"으로 저장될 것이다. 여기서 "_"은 공백을 나타낸다.

FIXED 와 VARIABLE 절에 대한 자세한 설명은 앞서 기술한 "FIXED/VARIABLE 옵션"과 "IN ROW 절"을 참고한다.

#### NCHAR

##### 흐름도

[![img](https://github.com/haeinnmin/Documents/raw/master/Manuals/Altibase_7.2/kor/media/GeneralReference/479310aaf34bada9e78bf3bb9c18eb8c.jpg)](https://github.com/haeinnmin/Documents/blob/master/Manuals/Altibase_7.2/kor/media/GeneralReference/479310aaf34bada9e78bf3bb9c18eb8c.jpg)

##### 구문

```
NCHAR [(size)] [ FIXED | VARIABLE [IN ROW size] ]
```

##### 설명

명시된 길이만큼 고정 길이를 가지는 문자형 데이타 타입이다. 정의된 칼럼 크기에 비해 입력 값의 길이가 작을 경우, 남는 공간은 공백으로 채워진다.

NCHAR 칼럼의 문자 하나당 크기는 국가 문자 집합(national character set)이 UTF16인 경우에는 고정길이 2바이트이고(가변길이 없음), UTF8인 경우에는 가변길이 3바이트(고정길이 없음)이다. UFT16은 한 문자에 대해 고정 2바이트를 사용하는 반면, UTF8은 1~3바이트까지 가변으로 사용하기 때문이다.

국가 문자 집합이 UTF16이면 최대 크기는 16000 bytes이다.

FIXED 와 VARIABLE 절에 대한 자세한 설명은 앞서 기술한 "FIXED/VARIABLE 옵션"과 "IN ROW 절"을 참고한다.

#### NVARCHAR

##### 흐름도

[![img](https://github.com/haeinnmin/Documents/raw/master/Manuals/Altibase_7.2/kor/media/GeneralReference/bdc39809efd5cc54b1ee2b06d2dd638b.jpg)](https://github.com/haeinnmin/Documents/blob/master/Manuals/Altibase_7.2/kor/media/GeneralReference/bdc39809efd5cc54b1ee2b06d2dd638b.jpg)

##### 구문

```
NVARCHAR [(size)] [ FIXED | VARIABLE [IN ROW size] ]
```

##### 설명

명시된 길이 내에서 가변 길이를 가지는 유니코드 문자형 데이타 타입이다.

NVARCHAR 칼럼의 문자 하나당 크기는 국가 문자 집합(national character set)이 UTF16인 경우에는 고정길이 2바이트이고(가변길이 없음), UTF8인 경우에는 가변길이 3바이트(고정길이 없음)이다. UFT16은 한 문자에 대해 고정 2바이트를 사용하는 반면, UTF8은 1~3바이트까지 가변으로 사용하기 때문이다.

나머지 속성은 VARCHAR와 동일하므로, 더 상세한 설명은 VARCHAR 타입을 참조한다.

FIXED 와 VARIABLE 절에 대한 자세한 설명은 앞서 기술한 "FIXED/VARIABLE 옵션"과 "IN ROW 절"을 참고한다.

### 숫자형 데이터 타입

Altibase는 다음의 숫자형 데이터 타입을 지원한다.

- BIGINT
- DECIMAL
- DOUBLE
- FLOAT
- INTEGER
- NUMBER
- NUMERIC
- REAL
- SMALLINT

#### BIGINT

##### 흐름도

[![img](https://github.com/haeinnmin/Documents/raw/master/Manuals/Altibase_7.2/kor/media/GeneralReference/bigint1.png)](https://github.com/haeinnmin/Documents/blob/master/Manuals/Altibase_7.2/kor/media/GeneralReference/bigint1.png)

##### 구문

```
BIGINT
```

##### 설명

8 바이트 정수형 데이터 타입이다.

C언어의 long(64 bit 시스템에서) 또는 long long(32 bit 시스템에서)과 동일하다.

범위: -263 + 1(-9223372036854775807) ~ 263 – 1(9223372036854775807)

#### DECIMAL

##### 흐름도

[![img](https://github.com/haeinnmin/Documents/raw/master/Manuals/Altibase_7.2/kor/media/GeneralReference/decimal1.png)](https://github.com/haeinnmin/Documents/blob/master/Manuals/Altibase_7.2/kor/media/GeneralReference/decimal1.png)

##### 구문

```
DECIMAL [(precision[, scale])]
```

##### 설명

DECIMAL은 NUMERIC 데이터 타입과 동일하다.

#### DOUBLE

##### 흐름도

[![img](https://github.com/haeinnmin/Documents/raw/master/Manuals/Altibase_7.2/kor/media/GeneralReference/double1.png)](https://github.com/haeinnmin/Documents/blob/master/Manuals/Altibase_7.2/kor/media/GeneralReference/double1.png)

##### 구문

```
DOUBLE
```

##### 설명

8 바이트 부동 소수점 숫자형 데이터 타입이다.

C언어의 double과 동일한 데이터 타입이다.

#### FLOAT

##### 흐름도

[![img](https://github.com/haeinnmin/Documents/raw/master/Manuals/Altibase_7.2/kor/media/GeneralReference/float1.png)](https://github.com/haeinnmin/Documents/blob/master/Manuals/Altibase_7.2/kor/media/GeneralReference/float1.png)

##### 구문

```
FLOAT [(precision)]
```

##### 설명

-1E+120에서 1E+120까지 내의 부동 소수점 숫자 데이터 타입이다.

*Precision*은 정밀도 표시하기 위해 부동 소수점 숫자의 가수를 유효숫자 표기법으로 저장하는 데 사용되는 유효숫자의 자릿수이다.

*Precision*의 범위는 1에서 38까지이며, 39번째 자릿수에서 값이 반올림된다. *Precision*이 생략되면 기본값으로 38이 설정된다.

#### INTEGER

##### 흐름도

[![img](https://github.com/haeinnmin/Documents/raw/master/Manuals/Altibase_7.2/kor/media/GeneralReference/integer1.png)](https://github.com/haeinnmin/Documents/blob/master/Manuals/Altibase_7.2/kor/media/GeneralReference/integer1.png)

##### 구문

```
INTEGER
```

##### 설명

4 바이트 크기의 정수형 데이터 타입이다.

C언어의 int와 동일한 데이터 타입이다.

-2,147,483,647에서 2,147,483,647까지의 정수값을 가질 수 있다.

#### NUMBER

##### 흐름도

[![img](https://github.com/haeinnmin/Documents/raw/master/Manuals/Altibase_7.2/kor/media/GeneralReference/number1.png)](https://github.com/haeinnmin/Documents/blob/master/Manuals/Altibase_7.2/kor/media/GeneralReference/number1.png)

##### 구문

```
NUMBER [(precision, scale)]
```

##### 설명

NUMERIC 데이터 타입의 alias이다. 단, *precision*과 *scale*이 명시되지 않으면 FLOAT데이터 타입과 동일하게 취급된다. FLOAT 데이터 타입은 39번째 자릿수에서 값이 반올림된다.

#### NUMERIC

##### 흐름도

[![img](https://github.com/haeinnmin/Documents/raw/master/Manuals/Altibase_7.2/kor/media/GeneralReference/numberic1.png)](https://github.com/haeinnmin/Documents/blob/master/Manuals/Altibase_7.2/kor/media/GeneralReference/numberic1.png)

##### 구문

```
NUMERIC [(precision, scale)]
```

##### 설명

NUMERIC은 Precision과 scale을 가지는 숫자형 데이터 타입으로 precision 만큼의 유효 숫자와 scale 만큼의 소수점 이하 정밀도를 가지는 고정 소수점형이다. FLOAT 데이터 타입이 실수를 표현하는 형식인 부동 소수점 형식인 반면 NUMERIC 데이터 타입은 precision과 scale이 모두 생략되면 precision은 38, scale은 0인 정수를 표현하는 고정 소수점형으로 사용된다.

- Precision은 1부터 38까지의 값을 명시할 수 있다.
- Scale은 -84에서 128까지의 값을 명시할 수 있다.
- Precision이 생략되면 기본값으로 38이 설정된다.
- Scale이 생략되면 기본값으로 0이 설정된다.

다음은 각각 정의된 NUMERIC 타입의 칼럼에 입력 값이 1234567.89일때의 변환된 값을 보여준다.

- NUMERIC => 1234568
- NUMERIC(9) => 1234568
- NUMERIC(9, 2) => 1234567.89
- NUMERIC(9, 1) => 1234567.9
- NUMERIC(6) => precision 초과
- NUMERIC(7, -2) => 1234500
- NUMERIC(7, 2) => precision 초과

#### REAL

##### 흐름도

[![img](https://github.com/haeinnmin/Documents/raw/master/Manuals/Altibase_7.2/kor/media/GeneralReference/real1.png)](https://github.com/haeinnmin/Documents/blob/master/Manuals/Altibase_7.2/kor/media/GeneralReference/real1.png)

##### 구문

```
REAL
```

##### 설명

4 바이트 크기의 부동 소수점형이다.

C언어의 float과 동일한 데이터 타입이다.

#### SMALLINT

##### 흐름도

[![img](https://github.com/haeinnmin/Documents/raw/master/Manuals/Altibase_7.2/kor/media/GeneralReference/smallint1.png)](https://github.com/haeinnmin/Documents/blob/master/Manuals/Altibase_7.2/kor/media/GeneralReference/smallint1.png)

##### 구문

```
SMALLINT
```

##### 설명

2 바이트 크기의 정수형 데이터 타입이다.

C언어의 short와 동일한 데이터 타입이다.

-215 + 1(-32,767)에서 215 - 1(32,767) 까지의 정수값을 가질 수 있다.

#### 숫자형 데이타 형식

TO_CHAR 나 TO_NUMBER 등의 타입 변환 함수를 사용할 때 숫자형 데이타에 대하여 다음과 같이 형식을 지정할 수 있다. 숫자 데이타 형식은 하나 이상의 숫자를 표시하는 요소로 구성된다. 이장에서는 각각의 요소와 관련된 데이타 형식의 예를 설명한다.

##### , (쉼표)

###### 설명

지정한 위치에 쉼표를 출력한다. 쉼표는 여러 번 사용할 수 있다.

###### 제한사항

쉼표는 숫자의 끝, 마침표의 오른쪽, 또는 숫자의 맨 앞자리에 올 수 없다.

###### 예제

```
iSQL> SELECT TO_CHAR (1234, '99,99') FROM dual;
TO_CHAR (1234, '99,99')  
---------------------------
 12,34           
1 row selected.

iSQL> SELECT TO_NUMBER ( '12,34', '99,99') FROM dual;
TO_NUMBER ( '12,34', '99,99') 
--------------------------------
1234        
1 row selected.
```

##### . (마침표)

###### 설명

지정한 위치에 마침표를 추가로 반환한다.

###### 제한사항

한 숫자 내에서 마침표는 한번만 사용할 수 있다.

###### 예제

```
iSQL> SELECT TO_CHAR (1.234, '99.999') FROM dual;
TO_CHAR (1.234, '99.999')  
-----------------------------
  1.234          
1 row selected.

iSQL> SELECT TO_NUMBER ( '1.234', '99.999') FROM dual;
TO_NUMBER ( '1.234', '99.999') 
---------------------------------
1.234       
1 row selected.
```

##### $

###### 설명

숫자 앞에 $ 기호를 붙인다.

###### 예제

```
iSQL> SELECT TO_CHAR (123, '$9999') FROM dual;
TO_CHAR (123, '$9999')  
--------------------------
  $123           
1 row selected.

iSQL> SELECT TO_NUMBER ( '$0123', '09$99') FROM dual;
TO_NUMBER ( '$0123', '09$99') 
--------------------------------
123         
1 row selected.
```

##### 0(숫자 0)

###### 설명

정수 부분의 유효 자리수가 실제 숫자의 자리수 보다 많을 경우 실제 숫자 앞에 0을 채워서 반환한다. 그 외의 특성은 9와 같다.

###### 예제

```
iSQL> SELECT TO_CHAR (123, '0999') FROM dual;
TO_CHAR (123, '0999')  
-------------------------
 0123
```

##### 9(숫자 9)

###### 설명

출력할 숫자의 자릿수를 숫자 9를 이용해서 표시한다. 실제 숫자의 자릿수 보다 9의 개수가 더 많으면 앞에 공백문자를 출력하여 길이를 맞추고, 정수 부분의 9의 개수가 실제 숫자보다 더 적으면 숫자의 길이만큼 #를 출력한다. #의 개수는 사용자가 지정한 형식에 쓰인 문자의 개수 + 1(부호문자)이다.

9사이에 오는 마침표는 숫자의 정수 부분과 소수 부분을 구분하여 출력하게 한다.

첫 번째 인자에 소수가 있는데 사용자가 지정한 형식에 소수를 표현하는 부분이 없거나, 더 적으면 반올림해서 사용자가 지정한 형식의 소수 부분의 길이에 맞춘다.

###### 예제

```
iSQL> SELECT TO_CHAR (123, '99999') FROM dual;
TO_CHAR (123, '99999')  
--------------------------
   123

iSQL> SELECT TO_CHAR (123.55, '999') FROM dual;
TO_CHAR (123.55, '999')  
---------------------------
 124             
1 row selected.

iSQL> SELECT TO_CHAR (123.4567, '999999') FROM dual;
TO_CHAR (123.4567, '999999')  
--------------------------------
    123          
1 row selected.

iSQL> SELECT TO_CHAR (1234.578, '9999.99') FROM dual;
TO_CHAR (1234.578, '9999.99')  
---------------------------------
 1234.58         
1 row selected.

iSQL> SELECT TO_CHAR (1234.578, '999.99999') FROM dual;
TO_CHAR (1234.578, '999.99999')  
-----------------------------------
##########       
1 row selected.

iSQL> SELECT TO_NUMBER ( '123', '99999') FROM dual;
TO_NUMBER ( '123', '99999') 
------------------------------
123         
1 row selected.
iSQL> SELECT TO_NUMBER ( '1234.58', '9999.99') FROM dual;
TO_NUMBER ( '1234.58', '9999.99') 
------------------------------------
1234.58     
1 row selected.
```

##### FM

###### 설명

출력 문자열의 왼쪽 부분의 공백이나 0을 제거합니다.

###### 예제

```
iSQL> select to_char(00123.100,'99999.999') from dual;
TO_CHAR(00123.100,'99999.999')
----------------------------------
   123.100
1 row selected.
iSQL> select to_char(00123.100,'FM99999.999') from dual;
TO_CHAR(00123.100,'FM99999.999')
------------------------------------
123.100
1 row selected.
```

##### B

###### 설명

결과값이 0일 경우, 0을 공백(Blank)으로 반환한다.

###### 예제

```
iSQL> SELECT TO_CHAR (0.4, 'B9') FROM T1;
TO_CHAR (0.4, 'B9')  
-----------------------
                 
1 row selected.
```

##### C

###### 설명

ISO 통화 기호(NLS_ISO_CURRENCY 프로퍼티에 설정된 값)를 지정한 위치에 반환한다.

###### 예제

```
iSQL> SELECT TO_CHAR (4000, 'C9999') FROM dual;
TO_CHAR (4000, 'C9999')
---------------------------
 KRW4000
1 row selected.
```

##### D

###### 설명

소수점 문자(NLS_NUMERIC_CHARACTER 프로퍼티에 설정된 값)를 지정한 위치에 반환한다. 기본값은 마침표(.)이다.

제약사항: 숫자 형식을 명시할 때 한 개의 소수점 문자만 포함할 수 있다.

###### 예제

```
iSQL> SELECT TO_CHAR (24.06, '99D99') FROM dual;
TO_CHAR (24.06, '99D99')
----------------------------
 24.06
1 row selected.
iSQL> SELECT TO_CHAR (206, '999D99') FROM dual;
TO_CHAR (206, '999D99')
---------------------------
 206.00
1 row selected.
```

##### EEEE

###### 설명

입력 받은 숫자를 지수 표기법을 이용하여 표기한다.

###### 제한사항

EEEE는 항상 오른쪽 끝에 와야 한다. 단 S, PR, MI보다는 왼쪽에 오는 것이 가능하다. 쉼표와 같이 사용할 수 없다.
TO_NUMBER 함수에서 사용할 수 없다.

###### 예제

```
iSQL> SELECT TO_CHAR (1234, '9.9EEEE') FROM dual;
TO_CHAR (1234, '9.9EEEE')  
-----------------------------
  1.2E+03        
1 row selected.
```

##### G

###### 설명

그룹 구분자(NLS_NUMERIC_CHARACTER 프로퍼티에 설정된 값)를 지정한 위치에 반환한다. 하나의 숫자형 데이터 형식에 그룹 구분자를 여러 번 지정할 수 있다.

###### 제약사항

그룹 구분자는 하나의 숫자형 데이터 형식에서 소수점 문자 또는 마침표의 오른쪽에 올 수 없다.

###### 예제

```
iSQL> SELECT TO_CHAR (2534.3, '999G999D99') FROM dual;
TO_CHAR (2534.3, '999G999D99')
----------------------------------
   2,534.30
1 row selected.
```

##### L

###### 설명

지역 통화 기호(NLS_CURRENCY 프로퍼티에 설정된 값)를 지정한 위치에 반환한다.

###### 예제

```
iSQL> SELECT TO_CHAR (4000, 'L9999') FROM dual;
TO_CHAR (4000, 'L9999')
---------------------------
 ?4000
1 row selected.
```

##### MI

###### 설명

MI를 숫자 표현 형식의 오른쪽 끝에 사용하면 입력 받은 수가 음수일 경우 마이너스(-) 기호를 숫자 끝에 붙여서 반환한다. 양수일 경우에는 공백문자가 들어간다.

###### 제한사항

MI는 항상 숫자 형식 표현의 오른쪽 끝에 와야 한다. S, PR과 같이 사용할 수 없다.

###### 예제

```
iSQL> SELECT TO_CHAR (-123, '999MI') FROM dual;
TO_CHAR (-123, '999MI')  
---------------------------
123-             
1 row selected.

iSQL> SELECT TO_NUMBER ( '123-', '999MI') FROM dual;
TO_NUMBER ( '123-', '999MI') 
-------------------------------
-123        
1 row selected.
```

##### PR

###### 설명

PR를 숫자 표현 형식의 오른쪽 끝에 사용하면 입력 받은 수가 음수일 경우 마이너스 기호(-) 대신 <숫자> 형태로 출력된다.

###### 제한사항

PR은 항상 숫자 표현 형식의 오른쪽 끝에 와야 한다.
S, MI와 같이 사용할 수 없다.

###### 예제

```
iSQL> SELECT TO_CHAR (-123, '999PR') FROM dual;
TO_CHAR (-123, '999PR')  
---------------------------
<123>            
1 row selected.

iSQL> SELECT TO_NUMBER ( '<123>', '999PR') FROM dual;
TO_NUMBER ( '<123>', '999PR') 
--------------------------------
-123        
1 row selected.
```

##### RN

###### 설명

입력 받은 수를 로마 숫자로 변환한다. 입력할 수 있는 수는 1부터 3999까지이다. 숫자 표현 형식을 소문자 rn으로 사용하면 로마 숫자가 소문자로 출력된다.

###### 제한사항

다른 숫자 형식과 같이 사용할 수 없다. TO_NUMBER 함수에서 사용할 수 없다.

###### 예제

```
iSQL> SELECT TO_CHAR (14, 'RN') FROM dual;
TO_CHAR (14, 'RN')  
----------------------
XIV              
1 row selected.
```

##### S

###### 설명

숫자 표현 형식의 처음이나 끝에 와서 입력 받은 수의 기호에 따라서 마이너스(-) 또는 플러스(+) 기호를 붙인다.

###### 제한사항

S는 숫자 표현 형식의 맨 앞이나 맨 뒤에만 올 수 있다.MI, PR과 같이 사용할 수 없다.

###### 예제

```
iSQL> SELECT TO_CHAR (123, 'S999.99') FROM dual;
TO_CHAR (123, 'S999.99')  
----------------------------
+123.00          
1 row selected.

iSQL> SELECT TO_CHAR (-123, '999.99S') FROM dual;
TO_CHAR (-123, '999.99S')  
-----------------------------
123.00-          
1 row selected.

iSQL> SELECT TO_NUMBER ( '+123', 'S999.99') FROM dual;
TO_NUMBER ( '+123', 'S999.99') 
---------------------------------
123         
1 row selected.

iSQL> SELECT TO_NUMBER ( '123.00-', '999.99S') FROM dual;
TO_NUMBER ( '123.00-', '999.99S') 
------------------------------------
-123        
1 row selected.
```

##### V

###### 설명

V 다음에 있는 9의 개수와 10을 곱하고 그 값을 인자로 받은 숫자와 곱한다. V 앞의 9의 개수는 첫 번째 인자의 유효숫자의 개수를 의미한다.

###### 제한사항

마침표와 같이 사용할 수 없다. TO_NUMBER 함수에서 사용할 수 없다.

###### 예제

```
iSQL> SELECT TO_CHAR (12, '99V99') FROM dual;
TO_CHAR (12, '99V99')  
-------------------------
 1200            
1 row selected.

iSQL> SELECT TO_CHAR (1200, '99V99') FROM dual;
TO_CHAR (1200, '99V99')  
---------------------------
######           
1 row selected.

iSQL> SELECT TO_CHAR (-123.456, '999V999EEEEMI') from dual;
TO_CHAR (-123.456, '999V999EEEEMI')  
---------------------------------------
 1235E+02-        
1 row selected.
```

##### XXXX

###### 설명

입력 받은 수를 16진수로 변환한다. 만약 정수가 아니라면 반올림하여 16진수로 변환한다. xxxx는 16진수 중 문자를 소문자로 반환한다.

###### 제한사항

다른 숫자 표현 형식과 같이 사용할 수 없다. 변환할 수는 0 이상이어야 한다.

###### 예제

```
iSQL> SELECT TO_CHAR (123, 'XXXX') FROM dual;
TO_CHAR (123, 'XXXX')  
-------------------------
7B               
1 row selected.

iSQL> SELECT TO_NUMBER ('ABC', 'XXXX') FROM dual;
TO_NUMBER ('ABC', 'XXXX') 
----------------------------
2748        
1 row selected.
```

### 날짜형 데이타 타입

날짜형 타입은 날짜와 시간 데이터를 저장하는데 사용된다.

#### DATE

**흐름도**

[![img](https://github.com/haeinnmin/Documents/raw/master/Manuals/Altibase_7.2/kor/media/GeneralReference/date1.png)](https://github.com/haeinnmin/Documents/blob/master/Manuals/Altibase_7.2/kor/media/GeneralReference/date1.png)

**구문**

```
DATE
```

**설명**

8바이트 크기의 날짜 값을 저장하는 데이터 타입이다.

저장할 수 있는 날짜의 범위는 시스템에 따라 다르다. 일반적으로 1년 1월 1일부터 9999년 12월 31일의 범위 내에서 사용 가능하다.

날짜 값은 날짜형 데이터 형식을 사용해서 다양한 포맷으로 출력할 수 있다.

#### 날짜형 데이터 형식

날짜형 데이터 타입의 데이터는 데이타베이스 내부적으로는 숫자형 데이터로 관리하지만 사용자는 TO_CHAR또는 TO_DATE 변환 함수 등을 사용해서 문자열로 표시할 수 있다. 변환 함수를 사용할 때 사용자는 보고자 하는 형식에 맞게 날짜형 데이터 형식 문자열을 지정해 주어야 한다.

날짜형 데이터 형식은 다음과 같은 기본요소들로 구성된다.

- AM, PM
- SCC, CC
- D, DD, DDD, DAY,DY
- HH, HH12, HH24
- MM, MON, MONTH
- MI
- Q
- SS, SSSSS, SSSSSS, SSSSSSSS, FF[1..6]
- WW, WW2, W, IW
- Y,YYY
- SYYYY, YYYY, YYY, YY, Y, RR, RRRR
- IYYY, IYY, IY, I

위의 기본 요소들과 함께 다음의 다음의 구두점과 특수 문자들도 날짜형 데이터 형식을 구성하는 요소이다.

- 하이픈(-)
- 슬래시(/)
- 쉼표(,)
- 마침표(.)
- 콜론(:)
- 홑따옴표(‘)

각각의 기본 요소들이 의미하는 바와 활용 예를 다음에서 살펴보자.

##### AM, PM

###### 설명

정오를 기준으로 오전/오후를 구분한다. (‘AM’ 또는 ‘PM’)

###### 예제

```
iSQL> SELECT TO_CHAR ( TO_DATE( '13', 'HH' ), 'AM' ) FROM dual;
TO_CHAR ( TO_DATE( '13', 'HH' ), 'AM' )  
-------------------------------------------
PM      
1 row selected.

iSQL> SELECT TO_DATE('1980-12-28 PM', 'YYYY-MM-DD AM') FROM dual;
TO_DATE('1980-12-28 PM', 'YYYY-MM-DD AM' 
-------------------------------------------
1980/12/28 12:00:00  
1 row selected.
```

##### SCC

###### 설명

세기를 표시한다.

- 4자리 년도 중 뒤의 2자리 값이 01~99이면, 4자리 년도 중 앞의 두 자리의 값에 1을 더해서 반환한다.
- 4자리 년도 중 뒤의 2자리 값이 00이면, 4자리 년도 중 앞의 두 자리 값을 그대로 반환한다.

기원전은 년도 앞에 '-'가 표시된다.

- 년도가 0000인 경우 기원전 1년이며, -0001인 경우 기원전 2년이다.
- 0000~ -0099는 -1세기이며, -01로 표시된다.

TO_DATE 함수에서는 인자로 사용할 수 없다.

###### 예제

```
iSQL> SELECT TO_CHAR ( '28-DEC-1980', 'SCC' ) FROM dual;
TO_CHAR ( '28-DEC-1980', 'SCC' )  
------------------------------------
 20 
1 row selected.

iSQL> SELECT TO_CHAR ( DATE'01-JAN-0001' - 1, 'SCC' ) FROM dual;
TO_CHAR ( DATE'01-JAN-0001' - 1, 'SCC' )  
--------------------------------------------
-01 
1 row selected.
```

##### CC

###### 설명

세기를 표시한다.

- 4자리 년도 중 뒤의 2자리 값이 01~99이면, 4자리 년도 중 앞의 두 자리의 값에 1을 더해서 반환한다.
- 4자리 년도 중 뒤의 2자리 값이 00이면, 4자리 년도 중 앞의 두 자리 값을 그대로 반환한다.

TO_DATE 함수에서는 인자로 사용할 수 없다.

###### 예제

```
iSQL> SELECT TO_CHAR ( '28-DEC-1980', 'CC' ) FROM dual;
TO_CHAR ( '28-DEC-1980', 'CC' )  
-----------------------------------
20      
1 row selected.
```

##### D

###### 설명

일주일 중 몇 번째 날인지를 나타내는 1 ~ 7까지의 숫자이다. 일요일부터 1로 시작한다.

TO_DATE 함수에서 인자로 사용할 수 없다.

###### 예제

```
iSQL> SELECT TO_CHAR ( '28-DEC-1980', 'D' ) FROM dual;
TO_CHAR ( '28-DEC-1980', 'D' )  
----------------------------------
1    
1 row selected.
```

##### DAY

###### 설명

요일의 영문이름을 나타낸다. (SUNDAY, MONDAY,…)

TO_DATE 함수에서 사용할 수 없다.

###### 예제

```
iSQL> SELECT TO_CHAR ( '28-DEC-1980', 'DAY' ) FROM dual;
TO_CHAR ( '28-DEC-1980', 'DAY' )  
------------------------------------
SUNDAY     
1 row selected.
```

##### DD

###### 설명

한달 중 몇 번째 날인지를 나타낸다. (1 ~ 31)

###### 예제

```
iSQL> SELECT TO_CHAR ( '28-DEC-1980', 'DD' ) FROM dual;
TO_CHAR ( '28-DEC-1980', 'DD' )  
-----------------------------------
28      
1 row selected.

iSQL> SELECT TO_DATE( '1980-12-28', 'YYYY-MM-DD') FROM dual;
TO_DATE( '1980-12-28', 'YYYY-MM-DD') 
---------------------------------------
1980/12/28 00:00:00  
1 row selected.
```

##### DDD

###### 설명

일 년 중 몇 번째 날인지를 나타낸다. (1 ~ 366)

TO_DATE 함수에서 사용할 수 없다.

###### 예제

```
iSQL> SELECT TO_CHAR ( '28-DEC-1980', 'DDD' ) FROM dual;
TO_CHAR ( '28-DEC-1980', 'DDD' )  
------------------------------------
363        
1 row selected.
```

##### DY

###### 설명

요일의 이름을 약자로 나타낸다. (SUN, MON, TUE, …)

TO_DATE 함수에서 사용할 수 없다.

###### 예제

```
iSQL> SELECT TO_CHAR ( '28-DEC-1980', 'DY' ) FROM dual;
TO_CHAR ( '28-DEC-1980', 'DY' )  
-----------------------------------
SUN     
1 row selected.
```

##### FF [1..6]

###### 설명

FF다음의 1 ~ 6까지의 숫자를 이용하여 마이크로 초의 자리 수를 나타낸다. (0 ~ 999999). FF 형식은 FF6과 같은 같은 결과를 반환한다.

TO_DATE 함수에서 사용할 수 없다.

###### 예제

```
iSQL> SELECT TO_CHAR ( SYSDATE, 'FF5' ) FROM dual;
TO_CHAR ( SYSDATE, 'FF5' )  
------------------------------
34528      
1 row selected.
```

##### HH, HH24

###### 설명

시간을 24시간 단위로 나타낸다.(0 ~ 23)

###### 예제

```
iSQL> SELECT TO_CHAR ( TO_DATE( '2008-12-28 17:30:29', 'YYYY-MM-DD HH:MI:SS' ), 'HH' ) FROM dual;
TO_CHAR ( TO_DATE( '2008-12-28 17:30:29'  
--------------------------------------------
17      
1 row selected.

iSQL> SELECT TO_CHAR ( TO_DATE( '2008-12-28 17:30:29', 'YYYY-MM-DD HH24:MI:SS' ), 'YYYY-MM-DD HH24:MI:SS' ) FROM dual;
TO_CHAR ( TO_DATE( '2008-12-28 17:30:29',
------------------------------------------
2008-12-28 17:30:29
1 row selected.
```

##### HH12

###### 설명

시간을 12시간 단위로 나타낸다.(1 ~ 12)

###### 예제

```
iSQL> SELECT TO_CHAR ( TO_DATE( '2008-12-28 17:30:29', 'YYYY-MM-DD HH:MI:SS' ), 'HH12' ) FROM dual;
TO_CHAR ( TO_DATE( '2008-12-28 17:30:29',
---------------------------------------------
05
1 row selected.

iSQL> SELECT TO_CHAR( TO_DATE ( '08-12-28 05:30:29', 'RR-MM-DD HH12:MI:SS' ), 'RR-MM-DD HH12:MI:SS') FROM dual;
TO_CHAR( TO_DATE ( '08-12-28 05:30:29', 'R
--------------------------------------------
08-12-28 05:30:29
1 row selected.
```

##### MI

###### 설명

분 (0 ~ 59)

###### 예제

```
iSQL> SELECT TO_CHAR ( TO_DATE( '1980-12-28 17:30:29', 'YYYY-MM-DD HH:MI:SS' ), 'HH' ) FROM dual;
TO_CHAR ( TO_DATE( '1980-12-28 17:30:29'  
--------------------------------------------
17      
1 row selected.

iSQL> SELECT TO_DATE ( '05-12-28 14:30:29', 'RR-MM-DD HH:MI:SS' ) FROM dual;
TO_DATE ( '05-12-28 14:30:29', 'RR-MM-DD 
-------------------------------------------
2005/12/28 14:30:29  
1 row selected.
```

##### MM

###### 설명

월 (01 ~ 12)

###### 예제

```
iSQL> SELECT TO_CHAR ( TO_DATE( '1980-12-28 17:30:29', 'YYYY-MM-DD HH:MI:SS' ), 'HH' ) FROM dual;
TO_CHAR ( TO_DATE( '1980-12-28 17:30:29'  
--------------------------------------------
17      
1 row selected.

iSQL> SELECT TO_DATE ( '05-12-28 14:30:29', 'RR-MM-DD HH:MI:SS' ) FROM dual;
TO_DATE ( '05-12-28 14:30:29', 'RR-MM-DD 
-------------------------------------------
2005/12/28 14:30:29  
1 row selected.
```

##### MON

###### 설명

월의 이름을 약자로 표시한다.( JAN, FEB, MAR, … )

###### 예제

```
SQL> SELECT TO_CHAR (TO_DATE ('1995-12-05', 'YYYY-MM-DD'), 'MON') FROM dual;
TO_
---
DEC
```

##### MONTH

###### 설명

월의 이름을 표시한다. (JANUARY, FEBRUARY, … )

###### 예제

```
iSQL> SELECT TO_CHAR ( '28-DEC-1980', 'Month' ) FROM dual;
TO_CHAR ( '28-DEC-1980', 'Month' )  
--------------------------------------
December         
1 row selected.

iSQL> SELECT TO_DATE ( '05-APRIL-28 14:30:29', 'RR-MONTH-DD HH:MI:SS' ) FROM dual;
TO_DATE ( '05-APRIL-28 14:30:29', 'RR-MO 
-------------------------------------------
2005/04/28 14:30:29  
1 row selected.
```

##### Q

###### 설명

분기를 표시한다. (1 ~ 4)

TO_DATE 함수에서 사용할 수 없다.

###### 예제

```
iSQL> SELECT TO_CHAR ( '28-DEC-1980', 'Q' ) FROM dual;
TO_CHAR ( '28-DEC-1980', 'Q' )  
----------------------------------
4    
1 row selected.
```

##### RM

###### 설명

로마 숫자로 월을 나타낸다. (I, II, III, IV,... )

###### 예제

```
iSQL> SELECT TO_CHAR ( '28-DEC-1980', 'RM' ) FROM dual;
TO_CHAR ( '28-DEC-1980', 'RM' )  
-----------------------------------
XII     
1 row selected.

iSQL> SELECT TO_DATE ('28-V-1980', 'DD-RM-YYYY') FROM dual;
TO_DATE ('28-V-1980', 'DD-RM-YYYY') 
--------------------------------------
1980/05/28 00:00:00  
1 row selected.
```

##### RR

###### 설명

년도를 두자리 정수로 표시한다. 날짜를 표기할 때, 두 자리만 표기한 경우 50미만인 경우에만 21세기라고 가정하여 2000을 더하고, 50 경우에는 1900을 더해서 연도를 표시한다. 따라서 표시 가능한 년도는 1950 ~ 2049까지 이다.

###### 예제

```
iSQL> SELECT TO_CHAR ( '28-DEC-80', 'RR' ) FROM dual;
TO_CHAR ( '28-DEC-80', 'RR' )  
---------------------------------
80      
1 row selected.

iSQL> SELECT TO_DATE ( '28-DEC-80', 'DD-MON-RR' ) FROM dual;
TO_DATE ( '28-DEC-80', 'DD-MON-RR' ) 
---------------------------------------
1980/12/28 00:00:00  
1 row selected.
```

##### RRRR

###### 설명

연도 (0 ~ 9999)

네자리, 두자리의 년도를 모두 입력으로 받아서, 숫자가 50미만인 경우 2000을 더하고, 50이상 100 미만인 경우 1900을 더해서 연도를 나타낸다. 4자리의 숫자인 경우 그대로가 년도로 표시된다.

###### 예제

```
iSQL> SELECT TO_CHAR ( '28-DEC-1980', 'RRRR' ) FROM dual;
TO_CHAR ( '28-DEC-1980', 'RRRR' )  
-------------------------------------
1980          
1 row selected.

iSQL> SELECT TO_CHAR ( '28-DEC-1980', 'DD-MON-RRRR' ) FROM dual;
TO_CHAR ( '28-DEC-1980', 'DD-MON-RRRR' )  
--------------------------------------------
28-DEC-1980                        
1 row selected.
```

##### SS

###### 설명

초 (0 ~ 59)

###### 예제

```
iSQL> SELECT TO_CHAR ( TO_DATE( '1980-12-28 17:30:29', 'YYYY-MM-DD HH:MI:SS' ), 'HH' ) FROM dual;
TO_CHAR ( TO_DATE( '1980-12-28 17:30:29'  
--------------------------------------------
17      
1 row selected.

iSQL> SELECT TO_DATE ( '05-12-28 14:30:29', 'RR-MM-DD HH:MI:SS' ) FROM dual;
TO_DATE ( '05-12-28 14:30:29', 'RR-MM-DD 
-------------------------------------------
2005/12/28 14:30:29  
1 row selected.
```

##### SSSSS

###### 설명

지난 부터 몇 초가 경과 되었는지 나타낸다. (0 ~ 86399)

###### 예제

```
iSQL> SELECT TO_CHAR ( TO_DATE( '1980-12-28 17:30:29', 'YYYY-MM-DD HH24:MI:SS' ), 'SSSSS' ) FROM dual;
TO_CHAR ( TO_DATE( '1980-12-28 17:30:29'  
--------------------------------------------
62940            
1 row selected.

iSQL> SELECT TO_DATE('1980-12-28 12345', 'YYYY-MM-DD SSSSS') FROM dual;
TO_DATE('1980-12-28 12345', 'YYYY-MM-DD  
-------------------------------------------
1980/12/28 03:25:45  
1 row selected.
```

##### SSSSSS

###### 설명

날짜 데이터 타입의 값의 마이크로 초를 표시한다.(0 ~ 999999)

###### 예제

```
iSQL> SELECT TO_CHAR (SYSDATE, 'SSSSSS') FROM dual;
TO_CHAR (SYSDATE, 'SSSSSS')  
-------------------------------
490927              
1 row selected.  

iSQL> SELECT TO_CHAR ( TO_DATE('1980-12-28 123456', 'YYYY-MM-DD SSSSSS'), 'SSSSSS' ) FROM dual;
TO_CHAR ( TO_DATE('1980-12-28 123456', '  
--------------------------------------------
123456              
1 row selected.
```

##### SSSSSSSS

###### 설명

초 + 마이크로 초를 나타낸다. 앞의 2개의 숫자는 초를 나타내고, 나머지 6개의 숫자가 마이크로 초를 나타낸다. (0 ~ 59999999)

###### 예제

```
iSQL> SELECT TO_CHAR (SYSDATE, 'SSSSSSSS') FROM dual;
TO_CHAR (SYSDATE, 'SSSSSSSS')  
---------------------------------
48987403                  
1 row selected.  

iSQL> SELECT TO_DATE ( '12.345678', 'SS.SSSSSS') FROM dual;
TO_DATE ( '12.345678', 'SS.SSSSSS') 
--------------------------------------
2005/12/01 00:00:12  
1 row selected.

iSQL> SELECT TO_CHAR( TO_DATE( '12.345678', 'SS.SSSSSS'), 'SSSSSS') FROM dual;
TO_CHAR( TO_DATE( '12.345678', 'SS.SSSSS  
--------------------------------------------
345678              
1 row selected.
```

##### WW

###### 설명

일 년 중 몇 번째 주인지를 나타낸다. 1월 1일부터 그 주의 토요일까지가 그 해의 첫 번째 주이다. (1 ~ 54)

TO_DATE 함수에서 사용할 수 없다.

###### 예제

```
iSQL> SELECT TO_CHAR ( '28-DEC-1980', 'WW' ) FROM dual;
TO_CHAR ( '28-DEC-1980', 'WW' )  
-----------------------------------
53      
1 row selected.
```

##### WW2

###### 설명

요일과 상관없이 일 년 중 몇 번째 주인지를 나타낸다. 첫 번째 주는 1월 1일부터 시작하며, 7일 단위로 구분한다. (1~53주)

TO_DATE 함수에서 사용할 수 없다.

###### 예제

```
iSQL> SELECT TO_CHAR ( '28-DEC-1980', 'WW2' ) FROM dual;
TO_CHAR ( '28-DEC-1980', 'WW2' )  
-----------------------------------
52      
1 row selected.
```

##### W

###### 설명

한 달 중 몇 번째 주인지를 나타낸다. 1일부터 그 주의 토요일까지가 그 달의 첫 번째 주이다. (1 ~ 6)

TO_DATE 함수에서 사용할 수 없다.

###### 예제

```
iSQL> SELECT TO_CHAR ( '28-DEC-1980', 'W' ) FROM dual;
TO_CHAR ( '28-DEC-1980', 'W' )  
----------------------------------
5    
1 row selected.
```

##### IW

###### 설명

ISO 8601에 따라 일 년 중 몇 번째 주인지를 나타낸다(1~52 또는 1~53). 주의 시작은 월요일이며, 첫 번째 주는 해당 연도의 첫 번째 목요일(1월 4일)을 포함한다.

TO_DATE 함수에서 사용할 수 없다.

- 2012.12.31(월) ~ 2013.01.06(일) : 2013년 01주
- 2014.12.29(월) ~ 2015.01.04(일) : 2015년 01주
- 2015.12.28(월) ~ 2016.01.03(일) : 2015년 53주
- 2016.12.26(월) ~ 2017.01.01(일) : 2016년 52주

###### 예제

```
iSQL> SELECT TO_CHAR ( '28-DEC-1980', 'IW' ) FROM dual;
TO_CHAR ( '28-DEC-1980', 'IW' )  
-----------------------------------
52       
1 row selected.
```

##### Y,YYY

###### 설명

연도를 나타내는 숫자 중 임의의 위치에 ,(comma)를 삽입할 수 있다. 맨 앞이나 뒤에 와도 상관 없다.

TO_DATE 함수에서 사용할 수 없다.

###### 예제

```
iSQL> SELECT TO_CHAR ( '28-DEC-1980', 'Y,YYY' ) FROM dual;
TO_CHAR ( '28-DEC-1980', 'Y,YYY' )  
--------------------------------------
1,980            
1 row selected.
```

##### SYYYY

###### 설명

네 자리 숫자를 그대로 연도로 간주한다. 기원전은 '-'가 표시된다 (-9999 ~ 9999).

년도가 0000인 경우 기원전 1년, -0001은 기원전 2년을 나타낸다.

###### 예제

```
iSQL> SELECT TO_CHAR ( '28-DEC-1980', 'SYYYY' ) FROM dual;
TO_CHAR ( '28-DEC-1980', 'SYYYY' )  
--------------------------------------
 1980     
1 row selected.

iSQL> SELECT TO_CHAR ( DATE'01-JAN-0000' - 1, 'SYYYY-MM-DD' ) FROM dual;
TO_CHAR ( DATE'01-JAN-0000' - 1, 'SYYYY-MM  
----------------------------------------------
-0001-12-31 
1 row selected.
```

##### YYYY

###### 설명

네 자리 숫자를 그대로 연도로 간주한다. (0 ~ 9999)

###### 예제

```
iSQL> SELECT TO_CHAR ( '28-DEC-1980', 'YYYY' ) FROM dual;
TO_CHAR ( '28-DEC-1980', 'YYYY' )  
-------------------------------------
1980          
1 row selected.

iSQL> SELECT TO_DATE ( '28-DEC-1980', 'DD-MON-YYYY' ) FROM dual;
TO_DATE ( '28-DEC-1980', 'DD-MON-YYYY' ) 
-------------------------------------------
1980/12/28 00:00:00  
1 row selected.
```

##### YY

###### 설명

연도의 마지막 숫자 2자리를 반환한다. 21세기라고 가정하고 2000을 더한 값을 연도로 간주한다. (2000 ~ 2099)

###### 예제1

```
iSQL> SELECT TO_CHAR ( '28-DEC-1980', 'YY' ) FROM dual;
TO_CHAR ( '28-DEC-1980', 'YY' )  
-----------------------------------
80      
1 row selected.

iSQL> SELECT TO_DATE ( '28-DEC-80', 'DD-MON-YY' ) FROM dual;
TO_DATE ( '28-DEC-80', 'DD-MON-YY' ) 
---------------------------------------
2080/12/28 00:00:00  
1 row selected.
```

###### 예제2

```
iSQL> CREATE TABLE timetbl(i1 INTEGER, t1 DATE, etc VARCHAR(10));
Create success.

iSQL> INSERT INTO timetbl VALUES (1, SYSDATE, 'Start');
1 row inserted.

iSQL> INSERT INTO timetbl VALUES (2, TO_DATE('2003-02-20 12:15:50', 'YYYY-MM-DD HH:MI:SS'), 'The end');
1 row inserted.

iSQL> SELECT TO_CHAR(T1, 'YYYY YY MM MON Mon mon DD HH MI SS SSSSSS D DDD') Date_format FROM timetbl WHERE I1 = 2;
DATE_FORMAT                                         
------------------------------------------------
2003 03 02 FEB Feb feb 20 12 15 50 000000 5 051     
1 row selected.
```

##### RR, RRRR, YY, YYYY 비교

각 형식 요소에 대한 설명을 참고한다.

- [YYYY]: 숫자를 그대로 연도로 간주

‘23-FEB-5’ : 0005년 2월 23일

‘23-FEB-05’ : 0005년 2월 23일

‘23-FEB-2005’:

‘23-FEB-95’ : 0095년 2월 23일

- [YY]: 2000 + YY

‘23-FEB-5’ :

‘23-FEB-05’ :

‘23-FEB-2005’: 에러

‘23-FEB-95’ :

‘23-FEB-05’ :

‘23-FEB-2005’: 에러

‘23-FEB-95’ :

- [RRRR]: 4자리 숫자를 그대로 연도로 간주, 숫자가 50 미만인 경우 2000을, 50 이상 100 미만인 경우 1900을 더한다.

‘23-FEB-5’ :

‘23-FEB-05’ :

‘23-FEB-2005’:

‘23-FEB-95’ :

‘23-FEB-100’: 0100년 2월 23일

‘23-FEB-0005’: 0005년 2월 23일

- [RR]: 숫자가 50 미만인 경우 2000을, 50 이상 100 미만인 경우 1900을 더한다.

‘23-FEB-5’ :

‘23-FEB-05’ :

‘23-FEB-2005’: 에러

‘23-FEB-95’ : 1995년 2월 23일

##### YYY

###### 설명

연도의 마지막 숫자 3자리를 반환한다. 21세기라고 가정하고 2000을 더한 값을 연도로 간주한다. (2000 ~ 2099)

##### Y

###### 설명

연도의 마지막 숫자를 반환한다. 21세기라고 가정하고 2000을 더한 값을 연도로 간주한다. (2000 ~ 2099)

##### IYYY, IYY, IY, I

###### 설명

ISO 8601 표준에 따른 연도를 나타낸다. 주의 시작은 월요일이며, 첫 번째 주는 해당 연도의 첫 번째 목요일을 포함한다.

IYYY는 ISO 표준 연도를 반환한다. IYY는 ISO 표준 연도의 마지막 3자리를 반환한다. IY는 ISO 표준 연도의 마지막 2자리를 반환한다. I는 ISO 표준 연도의 마지막 1자리를 반환한다.

TO_DATE 함수에서 사용할 수 없다.

- 2012.12.31(월) ~ 2013.01.06(일) : 2013년
- 2014.12.29(월) ~ 2015.01.04(일) : 2015년
- 2015.12.28(월) ~ 2016.01.03(일) : 2015년
- 2016.12.26(월) ~ 2017.01.01(일) : 2016년

###### 예제

```
iSQL> SELECT TO_CHAR ( '1-JAN-2017', 'IYYY IYY IY I' ) FROM dual;
TO_CHAR('1-JAN-2017','IYYY IYY IY I')        
--------------------------------------------
2016 016 16 6                             
1 row selected
```

### 이진 데이터 타입

텍스트, 비디오, 및 공간 데이터 같은 비정형 데이터를 저장하는데 사용된다. Altibase는 다음의 이진 데이터 타입을 지원한다.

- BYTE
- VARBYTE
- NIBBLE
- BIT
- VARBIT

#### BYTE

##### 흐름도

[![img](https://github.com/haeinnmin/Documents/raw/master/Manuals/Altibase_7.2/kor/media/GeneralReference/byte1.png)](https://github.com/haeinnmin/Documents/blob/master/Manuals/Altibase_7.2/kor/media/GeneralReference/byte1.png)

##### 구문

```
BYTE [(size)] [[FIXED |] VARIABLE ( IN ROW size ) ]
```

##### 설명

명시된 크기만큼 고정된 길이를 가지는 이진 데이터 타입이다. 정의된 크기보다 짧은 길이의 문자열을 입력하면 입력된 데이터의 오른쪽이 '0'으로 채워진다.

BYTE 칼럼의 기본 크기는 1 바이트이다. 최대 길이는 32000 바이트이다. 데이터는 ‘0FAE13’과 같이 알파벳과 숫자 문자의 조합을 사용해서 16진수 형식으로 표현 가능하다. 이 때 사용 가능한 문자는 0에서 9까지, A에서 F까지의 문자이다.

BYTE 칼럼에 입력 또는 검색 시 반드시 정의한 크기에 맞추어야 한다. 1바이트에 2개의 문자를 입력할 수 있다. 예를 들어 BYTE(3) 이라고 정의 하였으면 ‘000000’ 부터 ‘FFFFFF’ 까지의 값을 입력할 수 있다.

소문자 ‘a’부터 ‘f’를 입력할 경우 대문자로 변환되어 저장된다.

FIXED 와 VARIABLE 절에 대한 자세한 설명은 앞서 기술한 “FIXED/VARIABLE 옵션”과 “IN ROW 절”을 참고한다.

##### 예제

```
iSQL> CREATE TABLE T1 (I1 BYTE(1), I2 BYTE(5));
Create success.
iSQL> INSERT INTO T1 VALUES (BYTE'11', BYTE'0011');
1 row inserted.
iSQL> SELECT TO_CHAR(I1), TO_CHAR(I2) FROM T1;
TO_CHAR(I1)  TO_CHAR(I2)  
-----------------------------
11  0011000000  
1 row selected.
```

#### VARBYTE

##### 흐름도

[![img](https://github.com/haeinnmin/Documents/raw/master/Manuals/Altibase_7.2/kor/media/GeneralReference/varbyte1.png)](https://github.com/haeinnmin/Documents/blob/master/Manuals/Altibase_7.2/kor/media/GeneralReference/varbyte1.png)

##### 구문

```
VARBYTE [(size)] [[FIXED |] VARIABLE ( IN ROW size ) ]
```

##### 설명

가변 길이를 갖는 이진 데이타 타입이다. VARBYTE 칼럼의 기본 크기는 1바이트이며, 최대 길이는 32000바이트이다.

데이터는 ‘0FAE13’과 같이 알파벳과 숫자 문자의 조합을 사용해서 16진수 형식으로 표현 가능하다. 이 때 사용 가능한 문자는 0에서 9까지, A에서 F까지의 문자이다.

BYTE 칼럼에 입력 또는 검색 시 반드시 정의한 크기에 맞추어야 한다. 1바이트에 2개의 문자를 입력할 수 있다. 예를 들어 BYTE(3) 이라고 정의 하였으면 ‘000000’ 부터 ‘FFFFFF’ 까지의 값을 입력할 수 있다.

소문자 ‘a’부터 ‘f’를 입력할 경우 대문자로 변환되어 저장된다.

FIXED 와 VARIABLE 절에 대한 자세한 설명은 앞서 기술한 “FIXED/VARIABLE 옵션”과 “IN ROW 절”을 참고한다.

##### 예제

```
iSQL> CREATE TABLE T1 (I1 VARBYTE(1), I2 VARBYTE(5) );
Create success.
iSQL> INSERT INTO T1 VALUES (VARBYTE'11', VARBYTE'0011');
1 row inserted.
iSQL> SELECT TO_CHAR(I1), TO_CHAR(I2) FROM T1;
TO_CHAR(I1)  TO_CHAR(I2)  
-----------------------------
11  0011        
1 row selected.
```

#### NIBBLE

##### 흐름도

[![img](https://github.com/haeinnmin/Documents/raw/master/Manuals/Altibase_7.2/kor/media/GeneralReference/nibble1.png)](https://github.com/haeinnmin/Documents/blob/master/Manuals/Altibase_7.2/kor/media/GeneralReference/nibble1.png)

##### 구문

```
NIBBLE [(size)] [[FIXED |] VARIABLE ( IN ROW size ) ]
```

##### 설명

명시된 크기만큼 가변 길이를 가지는 이진 데이타 타입이다.

NIBBLE 칼럼의 기본 크기는 한 개의 문자 크기이며, 최대 254nibbles까지 허용된다.

데이터는 알파벳과 숫자 문자의 조합을 사용해서 16진수 형식으로 표현 가능하다. 이 때 사용 가능한 문자는 0에서 9까지, A에서 F까지의 문자이다. BYTE와 달리 한 nibble에 한 개의 문자만을 입력할 수 있다.

예를 들어 NIBBLE(6) 이라고 정의 하였으면 ‘000000’ 부터 ‘FFFFFF’ 까지 입력할 수 있다.

소문자 ‘a’부터 ‘f’를 입력할 경우 대문자로 변환되어 저장된다.

FIXED 와 VARIABLE 절에 대한 자세한 설명은 앞서 기술한 “FIXED/VARIABLE 옵션”과 “IN ROW 절”을 참고한다.

#### BIT

##### 흐름도

[![img](https://github.com/haeinnmin/Documents/raw/master/Manuals/Altibase_7.2/kor/media/GeneralReference/bit1.png)](https://github.com/haeinnmin/Documents/blob/master/Manuals/Altibase_7.2/kor/media/GeneralReference/bit1.png)

##### 구문

```
BIT [(size)] [[FIXED |] VARIABLE ( IN ROW size ) ]
```

##### 설명

고정 길이를 갖는 이진 데이타 타입으로, 데이터는 0과 1로만 이루어진다.

BIT 칼럼의 기본 크기는 1 비트이며, 최대 크기는 64000 비트이다.

정의된 크기보다 긴 문자열을 입력할 경우 'Invalid data type

length' 에러가 발생한다. 정의된 크기보다 짧은 길이의 문자열을 입력하면 입력 데이터의 오른쪽이 0으로 채워진다. 0과 1이외의 값이 입력될 경우 ‘Invalid literal’ 에러가 발생한다.

FIXED 와 VARIABLE 절에 대한 자세한 설명은 앞서 기술한 “FIXED/VARIABLE 옵션”과 “IN ROW 절”을 참고한다.

##### 예제

```
iSQL> CREATE TABLE T1 ( I1 BIT(1), I2 BIT(5) );
Create success.
iSQL> INSERT INTO T1 VALUES ( BIT'1', BIT'011' );
1 row inserted.
iSQL> SELECT TO_CHAR(I1), TO_CHAR(I2) FROM T1;
TO_CHAR(I1)  TO_CHAR(I2)
-----------------------------
1  01100
1 row selected.
iSQL> INSERT INTO T1 VALUES ( BIT'1111', BIT'011' );
[ERR-2100D : Invalid data type length]
iSQL> INSERT INTO T1 VALUES ( BIT'1', BIT'1234' );
[ERR-21011 : Invalid literal]
```

#### VARBIT

##### 흐름도

[![img](https://github.com/haeinnmin/Documents/raw/master/Manuals/Altibase_7.2/kor/media/GeneralReference/varbit1.png)](https://github.com/haeinnmin/Documents/blob/master/Manuals/Altibase_7.2/kor/media/GeneralReference/varbit1.png)

##### 구문

```
VARBIT [(size)] [[FIXED |] VARIABLE ( IN ROW size ) ]
```

##### 설명

가변 길이를 갖는 이진 데이타 타입으로, 데이터는 0과 1로만 이루어진다.

BIT 칼럼의 기본 크기는 1Bit이며, 최대 크기는 64000비트이다. 정의된 크기보다 긴 문자열을 입력할 경우 ‘Invalid data type length’ 에러가 발생한다.

FIXED 와 VARIABLE 절에 대한 자세한 설명은 앞서 기술한 “FIXED/VARIABLE 옵션”과 “IN ROW 절”을 참고한다.

##### 예제

```
iSQL> CREATE TABLE T1 ( I1 VARBIT(1), I2 VARBIT(5) );
Create success.
iSQL> INSERT INTO T1 VALUES ( VARBIT'1', VARBIT'011' );
1 row inserted.
iSQL> SELECT TO_CHAR(I1), TO_CHAR(I2) FROM T1;
TO_CHAR(I1)  TO_CHAR(I2)
-----------------------------
1  011
1 row selected.
iSQL> INSERT INTO T1 VALUES ( VARBIT'1111', VARBIT'011' );
[ERR-2100D : Invalid data type length]
iSQL> INSERT INTO T1 VALUES ( VARBIT'1', VARBIT'1234' );
[ERR-21011 : Invalid literal]
```

### LOB 데이타 타입

#### 개요

LOB(Large Object) 데이터 타입은 대용량 데이타를 저장할 수 있는 데이타 타입이다. 하나의 LOB칼럼에 저장 가능한 데이타의 크기는 최대 2G이다. 테이블을 생성할 때 다른 타입들과 달리 사용자가 LOB 칼럼의 크기를 명시할 필요가 없다. 그리고 하나의 테이블에 하나 이상의 LOB 타입 칼럼을 정의할 수 있다.

LOB 데이타 타입은 이미지, 동영상 파일들과 같은 이진 데이타를 저장하는 BLOB(Binary Large Object)과 문자열 데이타를 저장하는 CLOB(Character Large Object)으로 구분된다.

#### LOB의 특징

Altibase가 제공하는 LOB은 다음과 같은 특징이 있다.

- 데이타 저장 기능
- 부분 읽기(Partial Read)
- 디스크 LOB 파티셔닝

##### 데이타 저장 기능

ODBC의 SQLPutLob 함수 또는 JDBC의 setBlob 또는 setClob 메쏘드를 이용하여 CLOB, BLOB 데이타를 저장할 수 있다.

##### 부분 읽기(Partial Read)

LOB 데이타의 특정 구간에 대한 데이타 조각을 읽는 기능이다. Altibase ODBC의 SQLGetLob 함수를 이용하여 특정 오프셋의 크기를 읽는다.

##### 디스크 LOB의 파티셔닝

디스크 LOB 데이타는 테이블이 속한 테이블스페이스가 아닌 다른 디스크 테이블스페이스로 저장이 가능하다. 이는 테이블 파티셔닝 방법과 유사하다.

#### LOB 칼럼의 저장

LOB 데이타는 대부분의 경우 레코드 영역 밖의 가변 영역에 저장된다. 또한 LOB 칼럼의 크기가 크지 않을 때에는 in row 옵션을 사용하여 레코드 영역(고정 영역) 안에 저장하기도 한다. 그러나 디스크 테이블의 LOB 데이터는 크기와 상관없이 항상 가변 영역에 저장된다.

가변 영역에 저장되는 LOB 칼럼의 데이타는 크기가 매우 크기 때문에, 레코드의 나머지가 속하는 테이블스페이스에 같이 저장되는 것은 공간 사용 측면에서 효율성이 떨어진다.

디스크 테이블의 경우 LOB 칼럼 데이타를 LOB 칼럼이 속한 테이블과 별도의 테이블스페이스에 저장할 수 있다. 그러나 메모리 테이블의 경우에는 LOB 칼럼 데이터를 별도로 저장할 수 없고 테이블과 동일한 테이블스페이스에만 저장할 수 있다.

#### BLOB

##### 흐름도

[![img](https://github.com/haeinnmin/Documents/raw/master/Manuals/Altibase_7.2/kor/media/GeneralReference/blob1.png)](https://github.com/haeinnmin/Documents/blob/master/Manuals/Altibase_7.2/kor/media/GeneralReference/blob1.png)

##### 구문

```
BLOB [ VARIABLE ( IN ROW size ) ]
```

##### 설명

BLOB은 이진형 대용량 데이타를 저장하기 위한 이진형 데이터 타입으로, 4GB-1bye 크기까지 저장 가능하다.

FIXED 와 VARIABLE 절에 대한 자세한 설명은 앞서 기술한 “FIXED/VARIABLE 옵션”과 “IN ROW 절”을 참고한다.

#### CLOB

##### 흐름도

[![img](https://github.com/haeinnmin/Documents/raw/master/Manuals/Altibase_7.2/kor/media/GeneralReference/clob1.png)](https://github.com/haeinnmin/Documents/blob/master/Manuals/Altibase_7.2/kor/media/GeneralReference/clob1.png)

##### 구문

```
CLOB [ VARIABLE ( IN ROW size ) ]
```

##### 설명

CLOB은 문자형 대용량 데이타를 저장하기 위한 문자형 데이타 타입으로, 4GB-1bye 크기 크기까지 저장 가능하다.

FIXED 와 VARIABLE 절에 대한 자세한 설명은 앞서 기술한 “FIXED/VARIABLE 옵션”과 “IN ROW 절”을 참고한다.

#### 제한 사항

- 커서에서 LOB 타입 칼럼을 사용할 수 없다.
- 휘발성 테이블 또는 디스크 임시 테이블스페이스에서는 LOB 타입 칼럼을 사용할 수 없다.
- 디스카드된 테이블스페이스에 속한 테이블의 LOB 칼럼은 접근이 불가능하다.
- 파티션 키 컬럼은 대소 비교가 가능해야 하기 때문에 LOB 타입 칼럼은 파티션 키 컬럼으로 사용될 수 없다.
- LOB 칼럼에는 인덱스를 생성할 수 없다.
- LOB 칼럼에 NOT NULL 제약조건을 정의하는 것은 가능하다. 그러나 이 칼럼에 데이터 입력시 Altibase 서버 내부적으로 이 데이터를 처리중에 제약조건을 위배한다는 에러가 발생할 것이다. 그러므로, LOB 칼럼에는 NOT NULL 제약조건을 정의하지 않는 것이 바람직하다.

### 공간 데이터 타입

Altibase에서 SQL로 사용할 수 있도록 지원하는 공간 데이터 타입은 Geomerty 한가지 뿐이다. 이 Geometry 타입은 내부적으로 다음 7개의 하위 데이터 타입으로 이루어진다:

- Point
- LineString
- Polygon
- GeomCollection
- MultiPolygon
- MultiLineString
- MultiPoint

공간 데이터 타입에 관한 자세한 내용은 *Spatial SQL Reference* 를 참조한다

## 2.Altibase 프로퍼티

사용자는 Altibase 서버를 다양한 모드로 운영할 수 있다. Altibase 서버의 환경 설정은 Altibase 프로퍼티 파일을 이용하는 것이다. 프로퍼티 파일은 Altibase 서버의 운용 방식과 튜닝에 관한 모든 구성 요소를 포함하고 있다.

이 장에서는 Altibase를 사용자 업무에 적합한 데이터베이스로 구성하고 운영하기 위해서 설정하고 관리해야 하는 Altibase 프로퍼티들에 대해서 설명한다.

### 환경 설정 방법

Altibase 서버와 관련된 환경을 설정하기 위한 방법은 세 가지가 있다.

첫째, Altibase 프로퍼티 파일, $ALTIBASE_HOME/conf/altibase.properties를 변경하는 방식이다. 이 방식은 Altibase 서버가 실행되지 않은 상태에서 할 수 있는 정적인 환경 설정 방법으로, 프로퍼티 파일에서 해당 구성 요소를 특정 값으로 설정한 후 Altibase 서버를 재구동해야 수정된 값이 Altibase 서버에 반영된다.

둘째, Altibase 서버가 운영 중이더라도 Altibase 관련 환경 설정을 변경할 수 있는 동적인 방식이다. Altibase 서버를 내리지 않고도 변경할 수 있다는 장점이 있으나, 모든 프로퍼티에 가능하지는 않는다. 프로퍼티 속성의 동적 변경이 가능한 경우, ALTER SYSTEM 문 혹은 ALTER SESSION 문을 이용하여 변경할 수 있으며 Altibase 서버 전체 혹은 세션 별로 환경 설정 값이 적용된다.

셋째, 운영체제의 환경변수를 이용하여 설정할 수 있다. 이는 프로퍼티 파일과 마찬가지로 정적인 방법이다. 프로퍼티 속성이 읽기 전용, 단일 값일 경우 환경변수로 값을 설정할 수 있다. 환경변수의 이름은 ALTIBASE_프로퍼티명 형식이며, 설정 후 데이터베이스 서버를 재구동하여야 수정된 값이 서버에 반영된다.

예를 들면 다음과 같다.

```
$ export ALTIBASE_DEFAULT_DATE_FORMAT=YYYY/MM/DD
```

프로퍼티 설정 방법에 따른 우선순위는 다음과 같다.

1. 환경변수로 설정
2. Altibase 프로퍼티 파일에서 설정
3. 시스템의 기본값 사용

다음과 같이 환경변수와 프로퍼티가 설정되었을 경우 환경변수의 우선순위가 높으므로, Altibase 프로퍼티 파일의 DEFAULT_DATE_FORMAT의 값은 무시되고 환경변수의 값이 사용된다.

```
$ export ALTIBASE_DEFAULT_DATE_FORMAT=YYYY-MM-DD
DEFAULT_DATE_FORMAT=YYYY-MM-DD (altibase.properties)
```

다음 예에서도 프로퍼티와 환경변수가 다르게 설정된 경우, 프로퍼티 파일의 NLS_USE 값은 무시되고, 환경변수의 UTF-8 이 우선 설정된다.

```
$ export ALTIBASE_NLS_USE=UTF8
NLS_USE=KO16KSC5601 (altibase.properties)
```

### 프로퍼티 요약

Altibase 서버의 환경 설정에 관한 프로퍼티 파일은 ALTIBASE_HOME의 conf 디렉토리 밑에 있는 altibase.properties이며, 프로퍼티의 내용은 크게 다음과 같이 분류할 수 있다.

- 데이터베이스 초기화 관련 프로퍼티
- 성능 관련 프로퍼티
- 세션 관련 프로퍼티
- 트랜잭션 관련 프로퍼티
- 백업 및 복구 관련 프로퍼티
- 이중화 관련 프로퍼티
- 네트워크 및 보안 관련 프로퍼티
- 메시지 로그 관련 프로퍼티
- 데이터베이스 링크 관련 프로퍼티
- 감사(Auditing) 관련 프로퍼티
- C/C++ 외부 프로시저용 에이전트 관련 프로퍼티
- 사용자 계정 보안 관련 프로퍼티
- 기타 프로퍼티

다음의 표는 위 분류기준에 의해서 Altibase 프로퍼티를 정리한 표이다. 참고로 표의 각 분류는 다음과 같은 의미를 지닌다.

- D: 데이터베이스 초기화
- P: 성능
- S: 세션
- T: 트랜잭션
- B: 백업 및 복구
- R: 이중화
- NM: 네트워크 관리 및 보안(Network Management)
- M: 메시지 로그
- L: 데이터베이스 링크
- U: 감사(Auditing)
- A: 에이전트(Agent)
- AS: 사용자 계정 보안(Account Security)
- E: 기타

"변경 레벨" 열은 다음의 의미를 지닌다.

- SESSION : ALTER SESSION 문을 이용하여 프로퍼티 값 변경 가능

- SYSTEM : ALTER SYSTEM 문을 이용하여 프로퍼티 값 변경 가능

- BOTH : ALTER SESSION, ALTER SYSTEM 문을 이용하여 프로퍼티 값 변경 가능

- NONE: 동적 변경 불가능

  <table>
      <tr>
      	<th>분류</th>
          <th>소분류</th>
          <th>프로퍼티</th>
          <th>변경 레벨</th>
      </tr>
      <tr>
      	<td rowspan="90">D</td>
          <td rowspan="90"></td>
          <td>BUFFER_AREA_CHUNK_SIZE</td>
          <td></td>
      </tr>
      <tr>
          <td>BUFFER_AREA_SIZE</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>BUFFER_CHECKPOINT_LIST_CNT</td>
          <td rowspan="9"></td>
      </tr>
      <tr>
      	<td>BUFFER_FLUSHER_CNT </td>
      </tr>
      <tr>
      	<td>BUFFER_FLUSH_LIST_CNT</td>
      </tr>
      <tr>
      	<td>BUFFER_HASH_BUCKET_DENSITY</td>
      </tr>
      <tr>
      	<td>BUFFER_HASH_CHAIN_LATCH_DENSITY</td>
      </tr>
      <tr>
      	<td>BUFFER_LRU_LIST_CNT</td>
      </tr>
      <tr>
      	<td>BUFFER_PREPARE_LIST_CNT</td>
      </tr>
      <tr>
      	<td>COMPRESSION_RESOURCE_GC_SECOND</td>
      </tr>
      <tr>
      	<td>DB_NAME</td>
      </tr>
      <tr>
      	<td>DDL_SUPPLEMENTAL_LOG_ENABLE</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>DEFAULT_DISK_DB_DIR</td>
          <td rowspan="7"></td>
      </tr>
      <tr>
      	<td>DEFAULT_MEM_DB_FILE_SIZE</td>
      </tr>
      <tr>
      	<td>DEFAULT_SEGMENT_MANAGEMENT_TYPE</td>
      </tr>
      <tr>
      	<td>DEFAULT_SEGMENT_STORAGE_INITEXTENTS</td>
      </tr>
      <tr>
      	<td>DEFAULT_SEGMENT_STORAGE_MAXEXTENTS</td>
      </tr>
      <tr>
      	<td>DEFAULT_SEGMENT_STORAGE_MINEXTENTS</td>
      </tr>
      <tr>
      	<td>DEFAULT_SEGMENT_STORAGE_NEXTEXTENTS</td>
      </tr>
      <tr>
      	<td>DIRECT_PATH_BUFFER_PAGE_COUNT</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>DISK_INDEX_UNBALANCED_SPLIT_RATE</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>DISK_LOB_COLUMN_IN_ROW_SIZE</td>
          <td rowspan="4"></td>
      </tr>
      <tr>
      	<td>DISK_MAX_DB_SIZE</td>
      </tr>
      <tr>
      	<td>DOUBLE_WRITE_DIRECTORY</td>
      </tr>
      <tr>
      	<td>DOUBLE_WRITE_DIRECTORY_COUNT</td>
      </tr>
      <tr>
      	<td>DRDB_FD_MAX_COUNT_PER_DATAFILE</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>EXPAND_CHUNK_PAGE_COUNT</td>
          <td rowspan="3"></td>
      </tr>
      <tr>
      	<td>LOB_OBJECT_BUFFER_SIZE</td>
      </tr>
      <tr>
      	<td>LOCK_MGR_CACHE_NODE</td>
      </tr>
      <tr>
      	<td>LOCK_MGR_DETECTDEADLOCK_INTERVAL</td>
          <td>SYSTEM</td>
      </tr>   
      <tr>
      	<td>LOCK_MGR_MAX_SLEEP</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>LOCK_MGR_MIN_SLEEP</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>LOCK_MGR_SPIN_COUNT</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>LOCK_MGR_TYPE</td>
          <td rowspan="8"></td>
      </tr>
      <tr>
      	<td>LOCK_NODE_CACHE_COUNT</td>
      </tr>
      <tr>
      	<td>LOGANCHOR_DIR</td>
      </tr>
      <tr>
      	<td>LOG_DIR</td>
      </tr>
      <tr>
      	<td>LOG_FILE_SIZE</td>
      </tr>
      <tr>
      	<td>MAX_CLIENT</td>
      </tr>
      <tr>
      	<td>MEM_DB_DIR</td>
      </tr>
      <tr>
      	<td>MEM_MAX_DB_SIZE</td>
      </tr>
      <tr>
      	<td>MEMORY_INDEX_BUILD_RUN_SIZE</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>MEMORY_INDEX_BUILD_VALUE_LENGTH_THRESHOLD</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>MEMORY_INDEX_UNBALANCED_SPLIT_RATE</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>MEMORY_LOB_COLUMN_IN_ROW_SIZE</td>
          <td rowspan="4"></td>
      </tr>
      <tr>
      	<td>MEMORY_VARIABLE_COLUMN_IN_ROW_SIZE</td>
      </tr>
      <tr>
      	<td>MEM_SIZE_CLASS_COUNT</td>
      </tr>
      <tr>
      	<td>MIN_COMPRESSION_RESOURCE_COUNT</td>
      </tr>
      <tr>
      	<td>MIN_LOG_RECORD_SIZE_FOR_COMPRESS</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>MIN_PAGES_ON_DB_FREE_LIST</td>
          <td></td>
      </tr>
      <tr>
      	<td>MIN_PAGES_ON_TABLE_FREE_LIST</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>MIN_TASK_COUNT_FOR_THREAD_LIVE</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>PCTFREE</td>
          <td rowspan="3"></td>
      </tr>
      <tr>
      	<td>PCTUSED</td>
      </tr>
      <tr>
      	<td>QP_MEMORY_CHUNK_SIZE</td>
      </tr>
      <tr>
      	<td>RECYCLEBIN_DISK_MAX_SIZE</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>RECYCLEBIN_ENABLE</td>
          <td>SESSION</td>
      </tr>
      <tr>
      	<td>RECYCLEBIN_MEM_MAX_SIZE</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>REDUCE_TEMP_MEMORY_ENABLE</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>SECURITY_ECC_POLICY_NAME</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>SECURITY_MODULE_LIBRARY</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>SECURITY_MODULE_NAME</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>SERVICE_THREAD_INITIAL_LIFESPAN</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>SMALL_TABLE_THRESHOLD</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>ST_OBJECT_BUFFER_SIZE</td>
          <td>BOTH</td>
      </tr>
      <tr>
      	<td>SYS_DATA_FILE_INIT_SIZE</td>
          <td rowspan="13"></td>
      </tr>
      <tr>
      	<td>SYS_DATA_FILE_MAX_SIZE</td>       
      </tr>
      <tr>
      	<td>SYS_DATA_FILE_NEXT_SIZE</td>
      </tr>
      <tr>
      	<td>SYS_DATA_TBS_EXTENT_SIZE</td>
      </tr>
      <tr>
      	<td>SYS_TEMP_FILE_INIT_SIZE</td>
      </tr>
      <tr>
      	<td>SYS_TEMP_FILE_MAX_SIZE</td>
      </tr>
      <tr>
      	<td>SYS_TEMP_FILE_NEXT_SIZE</td>
      </tr>
      <tr>
      	<td>SYS_TEMP_TBS_EXTENT_SIZE</td>
      </tr>
      <tr>
      	<td>SYS_UNDO_FILE_INIT_SIZE</td>
      </tr>
      <tr>
      	<td>SYS_UNDO_FILE_MAX_SIZE</td>
      </tr>
      <tr>
      	<td>SYS_UNDO_FILE_NEXT_SIZE</td>
      </tr>
      <tr>
      	<td>SYS_UNDO_TBS_EXTENT_SIZE</td>
      </tr>
      <tr>
      	<td>TABLE_BACKUP_FILE_BUFFER_SIZE</td>
      </tr>
      <tr>
      	<td>TABLE_COMPACT_AT_SHUTDOW</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>TEMP_HASH_BUCKET_DENSITY</td>
          <td rowspan="11"></td>
      </tr>  
      <tr>
        	<td>TEMP_PAGE_CHUNK_COUNT</td>
      </tr>
      <tr>
      	<td>USER_DATA_FILE_INIT_SIZE</td>
      </tr>
      <tr>
      	<td>USER_DATA_FILE_MAX_SIZE</td>
      </tr>
      <tr>
      	<td>USER_DATA_FILE_NEXT_SIZE</td>
      </tr>
      <tr>
      	<td>USER_DATA_TBS_EXTENT_SIZE</td>
      </tr>
      <tr>
      	<td>USER_TEMP_FILE_INIT_SIZE</td>
      </tr>
      <tr>
      	<td>USER_TEMP_FILE_MAX_SIZE</td>
      </tr>
      <tr>
      	<td>USER_TEMP_FILE_NEXT_SIZE</td>
      </tr>
      <tr>
      	<td>USER_TEMP_TBS_EXTENT_SIZE</td>
      </tr>
      <tr>
      	<td>VOLATILE_MAX_DB_SIZE</td>
      </tr>
      <tr>
      	<td rowspan="101">P</td>
          <td rowspan="101"></td>
          <td>AGER_WAIT_MAXIMUM</td>
          <td rowspan="2"></td>
      </tr>
       <tr>
      	<td>AGER_WAIT_MINIMUM</td>
      </tr>
      <tr>
      	<td>BUFFER_VICTIM_SEARCH_INTERVAL</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>BUFFER_VICTIM_SEARCH_PCT</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>BULKIO_PAGE_COUNT_FOR_DIRECT_PATH_INSERT</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
          <td>CHECKPOINT_BULK_SYNC_PAGE_COUNT</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>CHECKPOINT_BULK_WRITE_PAGE_COUNT</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>CHECKPOINT_BULK_WRITE_SLEEP_SEC</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>CHECKPOINT_BULK_WRITE_SLEEP_USEC</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>CHECKPOINT_FLUSH_COUNT</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>CHECKPOINT_FLUSH_MAX_GAP</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>CHECKPOINT_FLUSH_MAX_WAIT_SEC</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>CM_BUFFER_MAX_PENDING_LIST</td>
          <td rowspan="3"></td>
      </tr>
      <tr>
      	<td>CM_DISPATCHER_SOCK_POLL_TYPE</td>
      </tr>
      <tr>
      	<td>DATABASE_IO_TYPE</td>
      </tr>
      <tr>
      	<td>DATAFILE_WRITE_UNIT_SIZE</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>DB_FILE_MULTIPAGE_READ_COUNT</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>DEDICATED_THREAD_CHECK_INTERVAL</td>
          <td rowspan="4"></td>
      </tr>
      <tr>
      	<td>DEDICATED_THREAD_INIT_COUNT</td>
      </tr>
      <tr>
      	<td>DEDICATED_THREAD_MAX_COUNT</td>
      </tr>
      <tr>
      	<td>DEDICATED_THREAD_MODE</td>
      </tr>
      <tr>
      	<td>DEFAULT_FLUSHER_WAIT_SEC</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>DELAYED_FLUSH_LIST_PCT</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>DELAYED_FLUSH_PROTECTION_TIME_MSEC</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>DIRECT_IO_ENABLED</td>
          <td></td>
      </tr>
      <tr>
      	<td>DISK_INDEX_BUILD_MERGE_PAGE_COUNT</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>EXECUTE_STMT_MEMORY_MAXIMUM</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>EXECUTOR_FAST_SIMPLE_QUERY</td>
          <td></td>
      </tr>
      <tr>
      	<td>FAST_START_IO_TARGET</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>FAST_START_LOGFILE_TARGET</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>FAST_UNLOCK_LOG_ALLOC_MUTEX</td>
          <td></td>
      </tr>
      <tr>
      	<td>HASH_AREA_SIZE</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>HASH_JOIN_MEM_TEMP_AUTO_BUCKET_COUNT_DISABLE</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>HASH_JOIN_MEM_TEMP_PARTITIONING_DISABLE</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>HIGH_FLUSH_PCT</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>HOT_LIST_PCT</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>HOT_TOUCH_CNT</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>INDEX_BUILD_THREAD_COUNT</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>INDEX_INITRANS</td>
          <td rowspan="5"></td>
      </tr>
      <tr>
      	<td>INDEX_MAXTRANS</td>
      </tr>
      <tr>
      	<td>LFG_GROUP_COMMIT_INTERVAL_USEC</td>
      </tr>
      <tr>
      	<td>LFG_GROUP_COMMIT_RETRY_USEC</td>
      </tr>
      <tr>
      	<td>LFG_GROUP_COMMIT_UPDATE_TX_COUNT</td>
      </tr>
      <tr>
      	<td>LOB_CACHE_THRESHOLD</td>
          <td>BOTH</td>
      </tr>
      <tr>
      	<td>LOCK_ESCALATION_MEMORY_SIZE</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
          <td>LOG_CREATE_METHOD</td>
      	<td rowspan="2"></td>
      </tr>
      <tr>
      	<td>LOG_IO_TYPE</td>
      </tr>
      <tr>
      	<td>LOW_FLUSH_PCT</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>LOW_PREPARE_PCT</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>MATHEMATICS_TEMP_MEMORY_MAXIMUM</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>MAX_FLUSHER_WAIT_SEC</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>MEM_INDEX_KEY_REDISTRIBUTION</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>MEM_INDEX_KEY_REDISTRIBUTION_STANDARD_RATE</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>MULTIPLEXING_CHECK_INTERVAL</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>MULTIPLEXING_MAX_THREAD_COUNT</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>MULTIPLEXING_THREAD_COUNT</td>
          <td></td>
      </tr>
      <tr>
      	<td>NORMALFORM_MAXIMUM</td>
          <td>BOTH</td>
      </tr>
      <tr>
      	<td>OPTIMIZER_AUTO_STATS</td>
          <td>BOTH</td>
      </tr>
      <tr>
      	<td>OPTIMIZER_DELAYED_EXECUTION</td>
          <td>SESSION</td>
      </tr>
      <tr>
      	<td>OPTIMIZER_FEATURE_ENABLE</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>OPTIMIZER_MODE</td>
          <td>BOTH</td>
      </tr>
      <tr>
      	<td>OPTIMIZER_PERFORMANCE_VIEW</td>
          <td></td>
      </tr>
      <tr>
      	<td>OPTIMIZER_UNNEST_AGGREGATION_SUBQUERY</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>OPTIMIZER_UNNEST_COMPLEX_SUBQUERY</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>OPTIMIZER_UNNEST_SUBQUERY</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>OUTER_JOIN_OPERATOR_TRANSFORM_ENABLE</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>PARALLEL_LOAD_FACTOR</td>
          <td></td>
      </tr>
      <tr>
      	<td>PARALLEL_QUERY_THREAD_MAX</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>PARALLEL_QUERY_QUEUE_SIZE</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>PREPARE_STMT_MEMORY_MAXIMUM</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>QUERY_REWRITE_ENABLE</td>
          <td>BOTH</td>
      </tr>
      <tr>
      	<td>REFINE_PAGE_COUNT</td>
      	<td></td>
      </tr>
      <tr>
      	<td>RESULT_CACHE_ENABLE</td>
          <td>BOTH</td>
      </tr>
      <tr>
      	<td>RESULT_CACHE_MEMORY_MAXIMUM</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>SECONDARY_BUFFER_ENABLE</td>
          <td rowspan="5"></td>
      </tr>
      <tr>
      	<td>SECONDARY_BUFFER_FILE_DIRECTORY</td>
      </tr>
      <tr>
      	<td>SECONDARY_BUFFER_FLUSHER_CNT</td>
      </tr>
      <tr>
      	<td>SECONDARY_BUFFER_SIZE</td>
      </tr>
      <tr>
      	<td>SECONDARY_BUFFER_TYPE</td>
      </tr>
      <tr>
      	<td>SORT_AREA_SIZE</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>SQL_PLAN_CACHE_BUCKET_CNT</td>
          <td></td>
      </tr>
      <tr>
      	<td>SQL_PLAN_CACHE_HOT_REGION_LRU_RATIO</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>SQL_PLAN_CACHE_PREPARED_EXECUTION_CONTEXT_CNT</td>
          <td>SYSTEM</td>     
      </tr>
      <tr>
          <td>SQL_PLAN_CACHE_SIZE</td>
      	<td>SYSTEM</td>
      </tr>
      <tr>
      	<td>STATEMENT_LIST_PARTIAL_SCAN_COUNT</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>TABLE_INITRANS</td>
          <td></td>
      </tr>
      <tr>
      	<td>TABLE_LOCK_ENABLE</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
          <td>TABLE_LOCK_MODE</td>
          <td rowspan="2"></td>
      </tr>
      <tr>
      	<td>TABLE_MAXTRANS</td>
      </tr>
      <tr>
      	<td>TABLESPACE_LOCK_ENABLE</td>
          <td>BOTH</td>
      </tr>
      <tr>
      	<td>TEMP_STATS_WATCH_TIME</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>THREAD_CPU_AFFINITY</td>
          <td rowspan="2"></td>
      </tr>
      <tr>
      	<td>THREAD_REUSE_ENABLE</td>
      </tr>
      <tr>
          <td>TIMED_STATISTICS</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>TIMER_RUNNING_LEVEL</td>
          <td></td>
      </tr>
      <tr>
      	<td>TIMER_THREAD_RESOLUTION</td>
          <td>SYSTEM</td>
      </tr>
       <tr>
      	<td>TOP_RESULT_CACHE_MODE</td>
          <td>BOTH</td>
      </tr>
       <tr>
      	<td>TOTAL_WA_SIZE</td>
          <td>SYSTEM</td>
      </tr>
       <tr>
        <td>INIT_TOTAL_WA_SIZE</td>
          <td>SYSTEM</td>
      </tr>
       <tr>
      	<td>TOUCH_TIME_INTERVAL</td>
          <td>SYSTEM</td>
      </tr>
       <tr>
      	<td>TRANSACTION_SEGMENT_COUNT</td>
          <td>SYSTEM</td>
      </tr>
       <tr>
      	<td>TRX_UPDATE_MAX_LOGSIZE</td>
          <td>BOTH</td>
      </tr>
      <tr>
          <td rowspan="42">S</td>
          <td rowspan="31">일반</td>
          <td>CM_DISCONN_DETECT_TIME</td>
          <td></td>
      </tr>
       <tr>
      	<td>CONCURRENT_EXEC_DEGREE_DEFAULT</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>CONCURRENT_EXEC_DEGREE_MAX </td>
          <td></td>
      </tr>
      <tr>
      	<td>CONCURRENT_EXEC_WAIT_INTERVAL</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>DEFAULT_THREAD_STACK_SIZE</td>
          <td rowspan="4"></td>
      </tr>
      <tr>
      	<td>IPC_CHANNEL_COUNT</td>
      </tr>
      <tr>
      	<td>IPC_FILEPATH</td>
      </tr>
      <tr>
      	<td>IPCDA_CHANNEL_COUNT</td>
      </tr>
      <tr>
      	<td>IPCDA_DATABLOCK_SIZE</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>IPCDA_FILEPATH</td>
          <td rowspan="2"></td>
      </tr>
      <tr>
      	<td>MAX_LISTEN</td>
      </tr>
      <tr>
          <td>MAX_STATEMENTS_PER_SESSION</td>
          <td>BOTH</td>
      </tr>
      <tr>
      	<td>NET_CONN_IP_STACK</td>
          <td rowspan="2"></td>
      </tr>
      <tr>
      	<td>NLS_COMP</td>
      </tr>
      <tr>
      	<td>NLS_CURRENCY</td>
      	<td>SESSION</td>
      </tr>
      <tr>
      	<td>NLS_ISO_CURRENCY</td>
          <td>SESSION</td>
      </tr>
      <tr>
      	<td>NLS_NCHAR_CONV_EXCP</td>
          <td>SESSION</td>
      </tr>
      <tr>
      	<td>NLS_NCHAR_LITERAL_REPLACE</td>
          <td>SESSION</td>
      </tr>
      <tr>
      	<td>NLS_NUMERIC_CHARACTERS</td>
          <td>SESSION</td>
      </tr>
      <tr>
      	<td>NLS_TERRITORY</td>
          <td>SESSION</td>
      </tr>
      <tr>
      	<td>PORT_NO</td>
          <td></td>
      </tr>
      <tr>
      	<td>PSM_CURSOR_OPEN_LIMIT</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>PSM_FILE_OPEN_LIMIT</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>TIME_ZONE</td>
          <td>SESSION</td>
      </tr>
      <tr>
      	<td>UNIXDOMAIN_FILEPATH</td>
          <td rowspan="2"></td>
      </tr>
      <tr>
      	<td>USE_MEMORY_POOL</td>
      </tr>
      <tr>
      	<td>USER_LOCK_POOL_INIT_SIZE</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>USER_LOCK_REQUEST_CHECK_INTERVAL</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>USER_LOCK_REQUEST_LIMIT</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>USER_LOCK_REQUEST_TIMEOUT</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>XA_HEURISTIC_COMPLETE</td>
          <td></td>
      </tr>
      <tr>
      	<td rowspan="11">타임아웃</td>
          <td>BLOCK_ALL_TX_TIME_OUT</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>DDL_LOCK_TIMEOUT</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>DDL_TIMEOUT</td>
          <td>BOTH</td>
      </tr>
      <tr>
      	<td>FETCH_TIMEOUT</td>
          <td>BOTH</td>
      </tr>
      <tr>
      	<td>IDLE_TIMEOUT</td>
          <td>BOTH</td>
      </tr>
      <tr>
      	<td>LOGIN_TIMEOUT</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>MULTIPLEXING_POLL_TIMEOUT</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>QUERY_TIMEOUT</td>
          <td>BOTH</td>
      </tr>
      <tr>
      	<td>SHUTDOWN_IMMEDIATE_TIMEOUT</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>UTRANS_TIMEOUT</td>
          <td>BOTH</td>
      </tr>
      <tr>
      	<td>XA_INDOUBT_TX_TIMEOUT</td>
          <td></td>
      </tr>
      <tr>
      	<td rowspan="3">T</td>
          <td rowspan="3"></td>
          <td>AUTO_COMMIT</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>ISOLATION_LEVEL</td>
          <td rowspan="2"></td>
      </tr>
      <tr>
      	<td>TRANSACTION_TABLE_SIZE</td>
      </tr>
      <tr>
      	<td rowspan="17">B</td>
          <td rowspan="17"></td>
          <td>ARCHIVE_DIR</td>
          <td rowspan="6"></td>
      </tr>
      <tr>
      	<td>ARCHIVE_FULL_ACTION</td>
      </tr>
      <tr>
      	<td>ARCHIVE_MULTIPLEX_COUNT</td>
      </tr>
      <tr>
      	<td>ARCHIVE_MULTIPLEX_DIR</td>
      </tr>
      <tr>
      	<td>ARCHIVE_THREAD_AUTOSTART</td>
      </tr>
      <tr>
      	<td>CHECKPOINT_ENABLED</td>
      </tr>
      <tr>
      	<td>CHECKPOINT_INTERVAL_IN_LOG</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>CHECKPOINT_INTERVAL_IN_SEC</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>COMMIT_WRITE_WAIT_MODE</td>
          <td>BOTH</td>
      </tr>
      <tr>
      	<td>INCREMENTAL_BACKUP_CHUNK_SIZE</td>
          <td rowspan="6"></td>
      </tr>
      <tr>
      	<td>INCREMENTAL_BACKUP_INFO_RETENTION_PERIOD</td>
      </tr>
      <tr>
      	<td>LOG_BUFFER_TYPE</td>
      </tr>
      <tr>
      	<td>LOG_MULTIPLEX_COUNT</td>
      </tr>
      <tr>
      	<td>LOG_MULTIPLEX_DIR</td>
      </tr>
      <tr>
      	<td>PREPARE_LOG_FILE_COUNT</td>
      </tr>
      <tr>
      	<td>SNAPSHOT_MEM_THRESHOLD</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>SNAPSHOT_DISK_UNDO_THRESHOLD</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td rowspan="53">R</td>
          <td rowspan="53"></td>
          <td>REPLICATION_ACK_XLOG_COUNT</td>
          <td></td>
      </tr>
      <tr>
      	<td>REPLICATION_ALLOW_DUPLICATE_HOSTS</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>REPLICATION_BEFORE_IMAGE_LOG_ENABLE</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>REPLICATION_COMMIT_WRITE_WAIT_MODE</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>REPLICATION_CONNECT_RECEIVE_TIMEOUT</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>REPLICATION_CONNECT_TIMEOUT</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>REPLICATION_DDL_ENABLE</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>REPLICATION_DDL_ENABLE_LEVEL</td>
          <td rowspan="2"></td>
      </tr>
      <tr>
      	<td>REPLICATION_EAGER_PARALLEL_FACTOR</td>
      </tr>
      <tr>
      	<td>REPLICATION_EAGER_RECEIVER_MAX_ERROR_COUNT</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>REPLICATION_FAILBACK_INCREMENTAL_SYNC</td>
          <td></td>
      </tr>
      <tr>
      	<td>REPLICATION_GAP_UNIT</td>
          <td></td>
      </tr>
      <tr>
      	<td>REPLICATION_GAPLESS_ALLOW_TIME</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>REPLICATION_GAPLESS_MAX_WAIT_TIME</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>REPLICATION_GROUPING_AHEAD_READ_NEXT_LOG_FILE</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>REPLICATION_GROUPING_TRANSACTION_MAX_COUNT</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>REPLICATION_HBT_CONNECT_WAIT_TIME</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>REPLICATION_HBT_DETECT_HIGHWATER_MARK</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>REPLICATION_HBT_DETECT_TIME</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>REPLICATION_IB_LATENCY</td>
          <td rowspan="2"></td>
      </tr>
      <tr>
      	<td>REPLICATION_IB_PORT_NO</td>
      </tr>
      <tr>
      	<td>REPLICATION_INSERT_REPLACE</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
          <td>REPLICATION_KEEP_ALIVE_CNT</td>
          <td></td>
      </tr>
      <tr>
      	<td>REPLICATION_LOCK_TIMEOUT</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>REPLICATION_LOG_BUFFER_SIZE</td>
          <td rowspan="3"></td>
      </tr>
      <tr>
      	<td>REPLICATION_MAX_COUNT</td>
      </tr>
      <tr>
      	<td>REPLICATION_MAX_LISTEN</td>
      </tr>
      <tr>
      	<td>REPLICATION_MAX_LOGFILE</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>REPLICATION_POOL_ELEMENT_COUNT</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>REPLICATION_POOL_ELEMENT_SIZE</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>REPLICATION_PORT_NO</td>
          <td></td>
      </tr>
      <tr>
      	<td>REPLICATION_RECEIVE_TIMEOUT</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>REPLICATION_RECEIVER_APPLIER_ASSIGN_MODE</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>REPLICATION_RECEIVER_APPLIER_QUEUE_SIZE</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>REPLICATION_PREFETCH_LOGFILE_COUNT</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>REPLICATION_RECOVERY_MAX_LOGFILE</td>
          <td rowspan="3"></td>
      </tr>
      <tr>
      	<td>REPLICATION_RECOVERY_MAX_TIME</td>
      </tr>
      <tr>
      	<td>REPLICATION_SENDER_AUTO_START</td>
      </tr>
      <tr>
      	<td>REPLICATION_SENDER_COMPRESS_XLOG</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>REPLICATION_SENDER_ENCRYPT_XLOG</td>
          <td></td>
      </tr>
      <tr>
      	<td>REPLICATION_SENDER_SEND_TIMEOUT</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>REPLICATION_SENDER_SLEEP_TIME</td>
          <td></td>
      </tr>
      <tr>
      	<td>REPLICATION_SENDER_SLEEP_TIMEOUT</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>REPLICATION_SENDER_START_AFTER_GIVING_UP</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>REPLICATION_SERVER_FAILBACK_MAX_TIME</td>
          <td rowspan="2"></td>
      </tr>
      <tr>
      	<td>REPLICATION_SQL_APPLY_ENABLE</td>
      </tr>
      <tr>
      	<td>REPLICATION_SYNC_APPLY_METHOD</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>REPLICATION_SYNC_LOCK_TIMEOUT</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>REPLICATION_SYNC_LOG</td>
          <td></td>
      </tr>
      <tr>
      	<td>REPLICATION_SYNC_TUPLE_COUNT</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>REPLICATION_TIMESTAMP_RESOLUTION</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>REPLICATION_TRANSACTION_POOL_SIZE</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
           <td>REPLICATION_UPDATE_REPLACE</td>
           <td>SYSTEM</td>
      </tr>
      <tr>
          <td rowspan="26">NM</td>
          <td rowspan="26"></td>
          <td>IB_CONCHKSPIN</td>
          <td rowspan="5"></td>
      </tr>
      <tr>
          <td>IB_ENABLE</td>
      </tr>
      <tr>
      	<td>IB_LATENCY</td>
      </tr>
      <tr>
      	<td>IB_LISTEN_DISABLE</td>
      </tr>
      <tr>
      	<td>IB_MAX_LISTEN</td>
      </tr>
      <tr>
      	<td>IB_PORT_NO</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>SNMP_ALARM_QUERY_TIMEOUT</td>
          <td rowspan="5"></td>
      </tr>
      <tr>
      	<td>SNMP_ALARM_FETCH_TIMEOUT</td>
      </tr>
      <tr>
      	<td>SNMP_ALARM_UTRANS_TIMEOUT</td>
      </tr>
       <tr>
      	<td>SNMP_ALARM_SESSION_FAILURE_COUNT</td>
      </tr>
       <tr>
      	<td>SNMP_ENABLE</td>
      </tr>
      <tr>
      	<td>SNMP_MSGLOG_FLAG</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>SNMP_PORT_NO</td>
          <td rowspan="12"></td>
      </tr>
      <tr>
      	<td>SNMP_TRAP_PORT_NO</td>
      </tr>
      <tr>
      	<td>SNMP_RECV_TIMEOUT</td>
      </tr>
      <tr>
      	<td>SNMP_SEND_TIMEOUT</td>
      </tr>
      <tr>
      	<td>SSL_CA</td>
      </tr>
      <tr>
      	<td>SSL_CAPATH</td>
      </tr>
      <tr>
      	<td>SSL_CERT</td>
      </tr>
      <tr>
      	<td>SSL_CIPHER_LIST</td>
      </tr>
      <tr>
      	<td>SSL_CLIENT_AUTHENTICATION</td>
      </tr>
      <tr>
      	<td>SSL_ENABLE</td>
      </tr>
      <tr>
      	<td>SSL_KEY</td>
      </tr>
      <tr>
      	<td>SSL_MAX_LISTEN</td>
      </tr>
      <tr>
      	<td>SSL_PORT_NO</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>TCP_ENABLE</td>
          <td></td>
      </tr>
      <tr>
      	<td rowspan="60">M</td>
          <td rowspan="60"></td>
          <td>ALL_MSGLOG_FLUSH</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>COLLECT_DUMP_INFO</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>DK_MSGLOG_COUNT</td>
          <td rowspan="2"></td>
      </tr>
      <tr>
      	<td>DK_MSGLOG_FILE</td>
      </tr>
      <tr>
      	<td>DK_MSGLOG_FLAG</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>DK_MSGLOG_RESERVE_SIZE</td>
          <td rowspan="17"></td>
      </tr>
      <tr>
      	<td>DK_MSGLOG_SIZE</td>
      </tr>
      <tr>
      	<td>DUMP_MSGLOG_COUNT</td>
      </tr>
      <tr>
      	<td>DUMP_MSGLOG_SIZE</td>
      </tr>
      <tr>
      	<td>DUMP_MSGLOG_RESERVE_SIZE</td>
      </tr>
      <tr>
      	<td>ERROR_MSGLOG_COUNT</td>
      </tr>
      <tr>
      	<td>ERROR_MSGLOG_FILE</td>
      </tr>
      <tr>
      	<td>ERROR_MSGLOG_SIZE</td>
      </tr>
      <tr>
      	<td>ERROR_MSGLOG_RESERVE_SIZE</td>
      </tr>
      <tr>
      	<td>LB_MSGLOG_COUNT</td>
      </tr>
      <tr>
      	<td>LB_MSGLOG_FILE</td>
      </tr>
      <tr>
      	<td>LB_MSGLOG_FLAG</td>
      </tr>
      <tr>
      	<td>LB_MSGLOG_SIZE</td>
      </tr>
      <tr>
      	<td>MM_MSGLOG_COUNT</td>
      </tr>
      <tr>
      	<td>MM_MSGLOG_FILE</td>
      </tr>
      <tr>
      	<td>MM_MSGLOG_RESERVE_SIZE</td>
      </tr>
      <tr>
      	<td>MM_MSGLOG_SIZE</td>
      </tr>
      <tr>
      	<td>MM_SESSION_LOGGING</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>NETWORK_ERROR_LOG</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>QP_MSGLOG_COUNT</td>
          <td rowspan="2"></td>
      </tr>
      <tr>
      	<td>QP_MSGLOG_FILE</td>
      </tr>
      <tr>
      	<td>QP_MSGLOG_FLAG</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>QP_MSGLOG_RESERVE_SIZE</td>
          <td rowspan="2"></td>
      </tr>
      <tr>
      	<td>QP_MSGLOG_SIZE</td>
      </tr>
      <tr>
      	<td>QUERY_PROF_FLAG</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>QUERY_PROF_LOG_DIR</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>RP_CONFLICT_MSGLOG_COUNT</td>
          <td rowspan="4"></td>
      </tr>
      <tr>
      	<td>RP_CONFLICT_MSGLOG_DIR</td>
      </tr>
       <tr>
      	<td>RP_CONFLICT_MSGLOG_ENABLE</td>
      </tr>
       <tr>
      	<td>RP_CONFLICT_MSGLOG_FILE</td>
      </tr>
      <tr>
      	<td>RP_CONFLICT_MSGLOG_FLAG</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>RP_CONFLICT_MSGLOG_SIZE</td>
          <td rowspan="3"></td>
      </tr>
      <tr>
      	<td>RP_MSGLOG_COUNT</td>
      </tr>
      <tr>
      	<td>RP_MSGLOG_FILE</td>
      </tr>
      <tr>
      	<td>RP_MSGLOG_FLAG</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>RP_MSGLOG_RESERVE_SIZE</td>
          <td rowspan="5"></td>
      </tr>
      <tr>
      	<td>RP_MSGLOG_SIZE</td>
      </tr>
      <tr>
      	<td>SERVER_MSGLOG_COUNT</td>
      </tr>
      <tr>
      	<td>SERVER_MSGLOG_DIR</td>
      </tr>
      <tr>
      	<td>ERVER_MSGLOG_FILE</td>
      </tr>
      <tr>
      	<td>SERVER_MSGLOG_FLAG</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>SERVER_MSGLOG_RESERVE_SIZE</td>
          <td rowspan="4"></td>
      </tr>
      <tr>
      	<td>SERVER_MSGLOG_SIZE</td>
      </tr>
      <tr>
      	<td>SM_MSGLOG_COUNT</td>
      </tr>
      <tr>
      	<td>SM_MSGLOG_FILE</td>
      </tr>
      <tr>
      	<td>SM_MSGLOG_FLAG</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>SM_MSGLOG_RESERVE_SIZE</td>
          <td rowspan="3"></td>
      </tr>
      <tr>
      	<td>SM_MSGLOG_SIZE</td>
      </tr>
      <tr>
      	<td>TRC_MSGLOG_RESERVE_SIZE</td>
      </tr>
      <tr>
      	<td>TRCLOG_DETAIL_PREDICATE</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>XA_MSGLOG_COUNT</td>
          <td rowspan="2"></td>
      </tr>
      <tr>
      	<td>XA_MSGLOG_FILE</td>
      </tr>
      <tr>
      	<td>XA_MSGLOG_FLAG</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>XA_MSGLOG_RESERVE_SIZE</td>
          <td rowspan="2"></td>
      </tr>
      <tr>
      	<td>XA_MSGLOG_SIZE</td>
      </tr>
      <tr>
      	<td rowspan="9">L</td>
          <td rowspan="9"></td>
          <td>DBLINK_ALTILINKER_CONNECT_TIMEOUT</td>
          <td rowspan="6"></td>
      </tr>
      <tr>
      	<td>DBLINK_DATA_BUFFER_ALLOC_RATIO</td>
      </tr>
      <tr>
      	<td>DBLINK_DATA_BUFFER_BLOCK_COUNT</td>
      </tr>
      <tr>
      	<td>DBLINK_DATA_BUFFER_BLOCK_SIZE</td>
      </tr>
      <tr>
      	<td>DBLINK_ENABLE</td>
      </tr>
      <tr>
      	<td>DBLINK_GLOBAL_TRANSACTION_LEVEL</td>
      </tr>
      <tr>
      	<td>DBLINK_RECOVERY_MAX_LOGFILE</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>DBLINK_REMOTE_STATEMENT_AUTOCOMMIT</td>
          <td>BOTH</td>
      </tr>
      <tr>
          <td>DBLINK_REMOTE_TABLE_BUFFER_SIZE</td>
          <td></td>
      </tr>
      <tr>
      	<td rowspan="4">U</td>
          <td rowspan="4"></td>
          <td>AUDIT_FILE_SIZE</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>AUDIT_LOG_DIR</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>AUDIT_OUTPUT_METHOD</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>AUDIT_TAG_NAME_IN_SYSLOG</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td rowspan="4">A</td>
          <td rowspan="4"></td>
          <td>EXTPROC_AGENT_CONNECT_TIMEOUT</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>EXTPROC_AGENT_CALL_RETRY_COUNT</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>EXTPROC_AGENT_IDLE_TIMEOUT</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>EXTPROC_AGENT_SOCKET_FILEPATH</td>
          <td></td>
      </tr>
      <tr>
      	<td rowspan="8">AS</td>
          <td rowspan="8"></td>
          <td>CASE_SENSITIVE_PASSWORD</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>FAILED_LOGIN_ATTEMPTS</td>
          <td rowspan="7"></td>
      </tr>
      <tr>
          <td>PASSWORD_LOCK_TIME</td>
      </tr>
      <tr>
          <td>PASSWORD_LIFE_TIME</td>
      </tr>
      <tr>
      	<td>PASSWORD_GRACE_TIME</td>
      </tr>
      <tr>
      	<td>PASSWORD_REUSE_TIME</td>
      </tr>
      <tr>
      	<td>PASSWORD_REUSE_MAX</td>
      </tr>
      <tr>
      	<td>PASSWORD_VERIFY_FUNCTION</td>
      </tr>
      <tr>
          <td rowspan="27">E</td>
          <td rowspan="27"></td>
          <td>ACCESS_LIST</td>
          <td rowspan="2"></td>
      </tr>
  	<tr>
      	<td>ACCESS_LIST_FILE</td>     
      </tr>
      <tr>
      	<td>ADMIN_MODE</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>ARITHMETIC_OPERATION_MODE</td>
          <td>SESSION</td>
      </tr>
      <tr>
      	<td>CHECK_MUTEX_DURATION_TIME_ENABLE</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>COERCE_HOST_VAR_IN_SELECT_LIST_TO_VARCHAR</td>
          <td rowspan="2"></td>
      </tr>
      <tr>
      	<td>DEFAULT_DATE_FORMAT</td>
      </tr>
      <tr>
      	<td>EXEC_DDL_DISABLE</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>GROUP_CONCAT_PRECISION</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>JOB_SCHEDULER_ENABLE</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>JOB_THREAD_COUNT</td>
          <td rowspan="4"></td>
      </tr>
      <tr>
      	<td>JOB_THREAD_QUEUE_SIZE</td>
      </tr>
      <tr>
      	<td>MSG_QUEUE_PERMISSION</td>
      </tr>
      <tr>
      	<td>PSM_CHAR_DEFAULT_PRECISION</td>
      </tr>
      <tr>
      	<td>PSM_IGNORE_NO_DATA_FOUND_ERROR</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>PSM_NCHAR_UTF16_DEFAULT_PRECISION</td>
          <td rowspan="6"></td>
      </tr>
      <tr>
      	<td>PSM_NCHAR_UTF8_DEFAULT_PRECISION</td>
      </tr>
      <tr>
      	<td>PSM_NVARCHAR_UTF16_DEFAULT_PRECISION</td>
      </tr>
      <tr>
      	<td>PSM_NVARCHAR_UTF8_DEFAULT_PRECISION</td>
      </tr>
      <tr>
      	<td>PSM_PARAM_AND_RETURN_WITHOUT_PRECISION_ENABLE</td>
      </tr>
      <tr>
      	<td>PSM_VARCHAR_DEFAULT_PRECISION</td>
      </tr>
      <tr>
      	<td>QUERY_STACK_SIZE</td>
          <td>BOTH</td>
      </tr>
      <tr>
      	<td>RECURSION_LEVEL_MAXIMUM</td>
          <td>SESSION</td>
      </tr>
      <tr>
      	<td>REMOTE_SYSDBA_ENABLE</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>SELECT_HEADER_DISPLAY</td>
          <td>BOTH</td>
      </tr>
      <tr>
      	<td>SYS_CONNECT_BY_PATH_PRECISION</td>
          <td>SYSTEM</td>
      </tr>
      <tr>
      	<td>SERIAL_EXECUTE_MODE</td>
          <td>BOTH</td>
      </tr>
  </table>

이 장에서는 각 프로퍼티를 다음과 같은 형식으로 설명하고 있다.

- 프로퍼티 이름
- 데이터 타입
- 기본값
- 속성 (읽기 전용/변경 가능, 단일 값/다중 값 허용)
- 값의 범위 (최대, 최소값)
- 설명

### 데이터베이스 초기화 프로퍼티

#### BUFFER_AREA_CHUNK_SIZE (단위: 바이트)

##### 데이터 타입

Unsigned Long

##### 기본값

33554432 (32M)

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[8192, 264-1]

##### 설명

버퍼 영역의 크기가 늘어나는 단위를 명시한다. 버퍼 크기를 늘리면 이 크기의 배수로 늘어난다. 서버 운영중에는 변경할 수 없다.

#### BUFFER_AREA_SIZE (단위: 바이트)

##### 데이터 타입

Unsigned Long

##### 기본값

134217728 (128M)

##### 속성

변경 가능, 단일 값

##### 값의 범위

[8192, 264-1]

##### 설명

Altibase 버퍼 풀이 사용하는 총 메모리 크기를 명시한다. 설정되는 크기는 BUFFER_AREA_CHUNK_SIZE 값의 배수 중 사용자가 명시한 값과 가장 가까운 값이다. 버퍼 풀의 크기는 하나의 트랜잭션이 사용할 수 있는 페이지의 크기와 동시 진행되는 트랜잭션의 개수에 영향을 받는다. 따라서 DISK_INDEX_BUILD_MERGE_PAGE_COUNT 프로퍼티 등의 페이지 개수와 관련된 프로퍼티를 변경할 때 BUFFER_AREA_SIZE의 값이 작지않도록 해야한다.

#### BUFFER_CHECKPOINT_LIST_CNT

##### 데이터 타입

Unsigned Integer

##### 기본값

4

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 64]

##### 설명

체크포인트 리스트의 개수를 명시한다. 이 개수가 많을수록 트랜잭션 간의 체크포인트 리스트에 대한 록(LOCK) 경합이 줄어든다.

#### BUFFER_FLUSH_LIST_CNT

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 64]

##### 설명

플러시 리스트의 개수를 명시한다. 이 개수가 많을수록 트랜잭션 간의 플러시 리스트 관련 록(LOCK) 경합이 준다.

#### BUFFER_FLUSHER_CNT

##### 데이터 타입

Unsigned Integer

##### 기본값

2

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 16]

##### 설명

버퍼 플러셔의 개수를 결정한다. 서버 운영중에는 변경할 수 없다.

#### BUFFER_HASH_BUCKET_DENSITY

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 100]

##### 설명

한 버킷 안에 들어갈 수 있는 BCBs (Buffer Control Blocks) 개수의 백분율을 명시한다. 예를 들어 BCBs의 개수가 100일 때, 이 값이 1이면 버킷의 개수는 버퍼 풀의 버퍼 프레임 개수와 같아지기 때문에 록(LOCK) 경합은 최소화된다. 이 값이 2이면 버킷의 개수는 프레임 개수의 절반이 되며, 100이면 버킷은 하나가 된다. 이 값이 커질수록 메모리는 적게 사용하지만, 한 버킷당 관리해야 할 버퍼 프레임의 수가 증가하기 때문에 연산 비용이 증가한다.

#### BUFFER_HASH_CHAIN_LATCH_DENSITY

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 100]

##### 설명

한 해쉬 테이블 내에서 한 개의 래치가 담당해야할 버킷의 백분율을 명시한다. 예를 들어 버킷이 1000개일 때, 이 값이 1이면 버킷 10개당 한 개의 래치를 두며, 2이면 버킷 20 개가 하나의 래치를 공유한다. 그리고 100이면 해쉬 테이블 전체에 걸쳐 한 개의 래치가 존재한다.

이 프로퍼티는 해쉬 테이블에 BCB가 삽입, 삭제될 때 동시성을 제어하기 위해 사용된다. 래치 수가 많을 수록 해쉬 체인 래치의 경합이 줄어든다.

#### BUFFER_LRU_LIST_CNT

##### 데이터 타입

Unsigned Integer

##### 기본값

7

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 64]

##### 설명

LRU 리스트의 개수를 명시한다. 이 개수가 많을수록 트랜잭션 간의 LRU 리스트 관련 록(LOCK) 경합이 줄어든다.

#### BUFFER_PREPARE_LIST_CNT

##### 데이터 타입

Unsigned Integer

##### 기본값

7

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 64]

##### 설명

Prepare 리스트의 개수를 명시한다. 이 개수가 많을수록 트랜잭션 간의 Prepare 리스트 관련 록(LOCK) 경합이 줄어든다.

#### BULKIO_PAGE_COUNT_FOR_DIRECT_PATH_INSERT (단위 : 개수)

##### 데이터 타입

Unsigned Integer

##### 기본값

128

##### 속성

변경 가능, 단일 값

##### 값의 범위

[128, 12800]

##### 설명

Direct-Path INSERT 방식으로 데이터를 입력할 때 한 번에 몇 개의 페이지를 디스크에 기록할 것인지 결정한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### COMPRESSION_RESOURCE_GC_SECOND (단위 : 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

3600

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, (264-1)/1000000]

##### 설명

로그 압축 리소스 풀에서 리소스가 몇 초 이상 사용되지 않을 경우 가비지 콜렉션(Garbase Collection)할 것인지를 결정한다.

#### DB_NAME

##### 데이터 타입

String

##### 기본값

mydb

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

데이터베이스 이름을 명시한다. 데이터베이스 생성시 데이터베이스 이름은 이 프로퍼티에 명시한 것과 같은 이름을 사용해야 한다. 만약 데이터베이스 이름을 변경하려면, 데이터베이스를 다시 생성해야 한다.

#### DDL_SUPPLEMENTAL_LOG_ENABLE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

DDL 연산시 로그를 추가적으로 남길 것인지 여부를 설정한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

0: Disabled (로그를 남기지 않음)

1: Enabled (로그를 남김)

#### DEFAULT_DISK_DB_DIR

##### 데이터 타입

String

##### 기본값

$ALTIBASE_HOME/dbs

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

디스크 데이터베이스 파일을 저장할 디렉토리 경로를 지정한다. 디스크 기능을 사용하지 않더라도 반드시 지정해야 한다. 이 경로의 기본값은 $ALTIBASE_HOME/dbs이다.

#### DEFAULT_MEM_DB_FILE_SIZE (단위 : 바이트)

##### 데이터 타입

Unsigned Long

##### 기본값

1073741824 bytes (1G)

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[4194304 (4M), 264-1]

##### 설명

메모리 테이블스페이스를 위한 체크포인트 이미지 파일의 기본 크기를 나타낸다.

#### DEFAULT_SEGMENT_MANAGEMENT_TYPE

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

디스크 테이블스페이스를 생성할 때 세그먼트 관리 방법을 결정한다.

0: MANUAL – 사용자가 테이블스페이스의 가용 공간 관리 방식을 프리 리스트(Freelist) 기반으로 하는 세그먼트 생성

1: AUTO – 사용자가 테이블스페이스의 가용 공간 관리 방식을 비트맵(Bitmap) 인덱스 기반으로 하는 세그먼트 생성

#### DEFAULT_SEGMENT_STORAGE_INITEXTENTS (단위: 개수)

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 232-1]

##### 설명

기본 세그먼트의 초기 익스텐트(extent) 개수를 명시한다.

#### DEFAULT_SEGMENT_STORAGE_MAXEXTENTS (단위 : 개수)

##### 데이터 타입

Unsigned Integer

##### 기본값

232-1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 232-1]

##### 설명

기본 세그먼트의 최대 익스텐트 개수를 명시한다.

#### DEFAULT_SEGMENT_STORAGE_MINEXTENTS (단위 : 개수)

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 232-1]

##### 설명

기본 세그먼트의 최소한의 익스텐트 개수를 명시한다.

#### DEFAULT_SEGMENT_STORAGE_NEXTEXTENTS (단위 : 개수)

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 232-1]

##### 설명

기본 세그먼트의 확장할 수 있는 익스텐트 개수를 명시한다.

#### DIRECT_PATH_BUFFER_PAGE_COUNT (단위 : 개수)

##### 데이터 타입

Unsigned Integer

##### 기본값

1024

##### 속성

변경 가능, 단일 값

##### 값의 범위

[1024, 232-1]

##### 설명

Direct=Path INSERT 버퍼의 페이지 개수를 나타낸다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### DISK_INDEX_UNBALANCED_SPLIT_RATE (단위 : 백분율)

##### 데이터 타입

Unsigned Integer

##### 기본값

90

##### 속성

변경 가능, 단일 값

##### 값의 범위

[50, 99]

##### 설명

디스크 B+ tree인덱스에서 최하위 리프 노드의 마지막 차일드 노드(child node)가 분할될 때, 분할을 발생시키는 노드와 생성되는 노드 사이에 키를 분배하는 비율을 명시할 수 있다. 이 값을 기본값인 90으로 지정할 경우, 두 노드 사이에 키의 비율은 90:10으로 배분된다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### DISK_LOB_COLUMN_IN_ROW_SIZE (단위 : 바이트)

##### 데이터 타입

Unsigned Long

##### 기본값

4000

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0,4000]

##### 설명

디스크 테이블에 사용된 LOB 타입 데이터의 기본 in row 크기를 지정한다. in row 크기는 LOB 데이터 타입의 칼럼에 데이터가 들어갈 때 데이터 길이가 이 값보다 작거나 같으면 고정(fixed) 영역에 저장하고, 이 보다 긴 경우에는 가변(variable) 영역에 들어가도록 지정하는 속성이다. 디스크 테이블에만 해당하는 것으로 메모리 테이블은 이 프로퍼티를 참조하지 않는다.

in row 크기나 LOB 타입에 대한 자세한 사항은 1장의 데이터 타입 부분을 참조한다.

#### DISK_MAX_DB_SIZE (단위 : 바이트)

##### 데이터 타입

Unsigned Long

##### 기본값

264-1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

64비트: [2097152, 264]

##### 설명

Altibase에서 디스크 데이터베이스를 설정할 수 있는 최대 크기이다.

DISK_MAX_DB_SIZE를 초과해서 데이터베이스 크기가 확장될 경우 그 트랜잭션은 오류 처리되며, 이후 수행되는 SELECT 문을 제외한 모든 SQL 문은 오류 처리된다.

#### DOUBLE_WRITE_DIRECTORY

##### 데이터 타입

String

##### 기본값

없음

##### 속성

읽기 전용, 다중 값

##### 값의 범위

없음

##### 설명

더블 라이트 파일이 저장될 디렉토리를 지정한다. 이 프로퍼티는 DOUBLE_WRITE_DIRECTORY_COUNT에 의해 복수로 명시할 수 있다.

#### DOUBLE_WRITE_DIRECTORY_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

2

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 16]

##### 설명

더블 라이트 파일이 저장되는 디렉토리의 개수를 지정한다. 더블 라이트 파일들은 각각 다른 디스크에 저장될 수 있다. 플러셔(Flusher)마다 별도의 더블 라이트 파일을 사용하기 때문에 서로 다른 디스크로 디렉토리를 지정하면, 플러시 성능을 높일 수 있다.

#### DRDB_FD_MAX_COUNT_PER_DATAFILE

##### 데이터 타입

Unsigned Integer

##### 기본값

8

##### 속성

변경 가능, 단일 값

##### 값의 범위

[1, 1024]

##### 설명

하나의 디스크 데이터 파일에서 I/O가 발생할 때 열 수 있는 최대 FD(File Descriptors) 개수다. FD가 프로퍼티에서 설정한 최대 숫자까지 열려있다면, 다른 I/O가 완료될 때까지 대기한다.

#### EXPAND_CHUNK_PAGE_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

128

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[64, 232-1]

##### 설명

메모리 데이터베이스의 Expand Chunk가 가질 수 있는 페이지의 개수를 나타낸다. Expand Chunk는 메모리 데이터베이스에서 페이지를 확장할 수 있는 단위이다. 데이터베이스를 생성할 때 설정할 수 있으며, 만약 페이지 개수를 변경하려면 데이터베이스를 다시 생성해야 한다.

#### LOB_OBJECT_BUFFER_SIZE (단위: 바이트)

##### 데이터 타입

Unsigned Integer

##### 기본값

32000

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[32000, 104857600]

##### 설명

파라미터, 내부 변수 또는 반환값의 타입이 LOB으로 선언된 저장 프로시저/함수 또는 트리거를 동작하는 중에, 이러한 LOB 값 처리를 위해 Altibase 서버에서 내부적으로 사용하는 LOB 데이터의 최대 크기를 지정하는 프로퍼티이다.

#### LOCK_MGR_CACHE_NODE

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2]

##### 설명

테이블 록(lock) 노드의 캐시 타입을 명시한다. 서버 운영중에는 변경할 수 없다.

0: 캐시하지 않는다.

1: 링크드 리스트(Linked List)로 캐시한다.

2: 배열로 캐시하고, 64개로 고정된다.

#### LOCK_MGR_DETECTDEADLOCK_INTERVAL (단위 : 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

3

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 10]

##### 설명

Spin 모드에서 데드락을 검출하는 간격을 명시한다.

(Spin 모드가 deprecated 되어 7.1.0.3.2 부터는 값이 무시된다.)

#### LOCK_MGR_MAX_SLEEP (단위 : 마이크로 초)

데이터 타입

Unsigned Integer

##### 기본값

1000

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1000000]

##### 설명

Spin 모드에서 재시도 회수만큼 시도했음에도 불구하고 Lock 획득에 실패한 경우에 sleep하는 최대 시간을 명시한다.

(Spin 모드가 deprecated 되어 7.1.0.3.2 부터는 값이 무시된다.)

#### LOCK_MGR_MIN_SLEEP (단위 : 마이크로 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

50

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1000000]

##### 설명

Spin 모드에서 재시도 회수만큼 시도했음에도 불구하고 Lock 획득에 실패한 경우에 sleep하는 시간을 명시한다.

(Spin 모드가 deprecated 되어 7.1.0.3.2 부터는 값이 무시된다.)

#### LOCK_MGR_SPIN_COUNT (단위: 회수)

##### 데이터 타입

Unsigned Integer

##### 기본값

1000

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 3000]

##### 설명

Spin 모드에서 Lock 획득에 실패했을 경우 재시도 회수를 명시한다.

(Spin 모드가 deprecated 되어 7.1.0.3.2 부터는 값이 무시된다.)

#### LOCK_MGR_TYPE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2]

##### 설명

테이블 록(Table Lock) 관리자 타입을 선택한다. 서버 운영중에는 변경할 수 없다.

0: Mutex 모드

1: Spin lock 모드 (deprecated, 7.1.0.3.2)

2: light Mutex (added, 7.1.0.3.2)

#### LOCK_NODE_CACHE_COUNT (단위 : 개수)

##### 데이터 타입

Unsigned Integer

##### 기본값

2

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1024]

##### 설명

LOCK_MGR_CACHE_NODE=1일 경우 캐시할 테이블 락 노드의 개수를 명시한다. 서버 운영중에는 변경할 수 없다.

#### LOGANCHOR_DIR

##### 데이터 타입

String

##### 기본값

$ALTIBASE_HOME/logs

##### 속성

읽기 전용, 다중 값

##### 값의 범위

없음

##### 설명

로그앵커 파일이 존재할 경로를 지정한다. 반드시 3개가 지정되어야 하며, 기본으로 3개가 동일하게 기본값으로 지정된다.

#### LOG_DIR

##### 데이터 타입

String

##### 기본값

$ALTIBASE_HOME/logs

##### 속성

읽기 전용, 다중 값

##### 값의 범위

없음

##### 설명

로그 파일이 존재할 경로를 지정한다.

#### LOG_FILE_SIZE (단위: 바이트)

##### 데이터 타입

Unsigned long

##### 기본값

10 * 1024 * 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1024 * 1024, 264-1]

##### 설명

로그 파일의 크기를 지정한다. 지정된 로그 파일의 크기 만큼 차게 되면 새로운 로그 파일에 기록한다. 데이터베이스 생성 시에 설정할 수 있으며, 생성 후에는 변경할 수 없다. 만약 사용자가 로그 파일 크기를 변경하려면, 데이터베이스를 다시 생성해야 한다.

> \* 제약사항
>
> - 오프라인 이중화를 사용하기 위해서는 지역 서버(Active)와 원격 서버(Standby)의 이 프로퍼티의 값이 반드시 동일해야 한다.

#### MAX_CLIENT

##### 데이터 타입

Unsigned Integer

##### 기본값

1000

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 65535]

단, JOB_THREAD_COUNT프로퍼티가 0보다 큰 값으로 설정된 경우에 최댓값은 65535에서 JOB_THREAD_COUNT값을 뺀 값이다.

##### 설명

Altibase에 접속할 수 있는 클라이언트의 최대 개수를 명시한다.

#### MEM_DB_DIR

##### 데이터 타입

String

##### 기본값

$ALTIBASE_HOME/dbs

##### 속성

읽기 전용, 다중 값

##### 값의 범위

없음

##### 설명

메모리 데이터베이스 파일이 존재할 경로를 지정한다.

최소 1개, 최대 8개 경로 지정이 가능하다. 여러 개의 경로가 지정될 경우, 데이타베이스 파일은 각 경로에 분산되어 저장된다. 이 프로퍼티로 지정되는 모든 경로는 실제 존재하는 경로여야 한다. 경로의 기본 개수는 2개, 각 경로의 기본값은 $ALTIBASE_HOME/dbs로 동일하게 지정되어 있다.

#### MEM_MAX_DB_SIZE (단위 : 바이트)

##### 데이터 타입

Unsigned Long

##### 기본값

231

##### 속성

읽기 전용, 단일 값

##### 값의 범위

32비트: [2097152, 232+1]

64비트: [2097152, 264]

##### 설명

서비스 과정 중에 동적으로 늘어날 수 있는 모든 메모리 데이터베이스 크기의 합에 대한 최대값을 명시한다. 32비트와 64비트 모드에 관계없이 기본 값은 2G이다.

MEM_MAX_DB_SIZE를 초과해서 데이터베이스 크기가 확장될 경우 그 트랜잭션은 오류 처리되며, 이후 수행되는 SELECT 문을 제외한 모든 SQL 문은 오류 처리된다.

#### MEMORY_INDEX_BUILD_RUN_SIZE (단위 : 바이트)

##### 데이터 타입

Unsigned Long

##### 기본값

131072

##### 속성

변경 가능, 단일 값

##### 값의 범위

[1024, 264-1]

##### 설명

메모리 인덱스를 구축할 때 in-memory sorting 영역의 크기를 지정할 수 있다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### MEMORY_INDEX_BUILD_VALUE_LENGTH_THRESHOLD (단위 : 바이트)

##### 데이터 타입

Unsigned Long

##### 기본값

64

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 264-1]

##### 설명

메모리 인덱스 구축시, 중간 정렬을 위해 사용가능한 키 값의 최대 길이를 설정한다.

키 값의 길이가 이 프로퍼티보다 작으면 중간 정렬시 키 값을 사용하지만, 이 프로퍼티의 값이 0이면 레코드에 대한 포인터를 사용한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### MEMORY_INDEX_UNBALANCED_SPLIT_RATE (단위 : 백분율)

##### 데이터 타입

Unsigned Integer

##### 기본값

90

##### 속성

변경 가능, 단일 값

##### 값의 범위

[50, 99]

##### 설명

메모리 B+ tree인덱스에서 최하위 리프 노드의 마지막 차일드 노드(child node)가 분할될 때, 분할을 발생시키는 노드와 생성되는 노드 사이에 키를 분배하는 비율을 명시할 수 있다. 이 값을 기본값인 50으로 지정할 경우, 두 노드 사이에 키의 비율은 50:50으로 배분된다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### MEMORY_LOB_COLUMN_IN_ROW_SIZE (단위 : 바이트)

##### 데이터 타입

Unsigned Long

##### 기본값

64

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0,4000]

##### 설명

메모리 테이블에 사용된 LOB 타입 데이터의 기본 in row 크기를 지정한다. in row 크기는 LOB 데이터 타입의 칼럼에 데이터가 들어갈 때 데이터 길이가 이 값보다 작거나 같으면 고정(fixed) 영역에 저장하고, 이 보다 긴 경우에는 가변(variable) 영역에 들어가도록 지정하는 속성이다. 메모리 테이블에만 해당하는 것으로 디스크 테이블은 이 프로퍼티를 참조하지 않는다.

in row 크기나 LOB 타입에 대한 자세한 사항은 1장의 데이터 타입 부분을 참조한다.

#### MEMORY_VARIABLE_COLUMN_IN_ROW_SIZE(단위: 바이트)

##### 데이터 타입

Unsigned Long

##### 기본값

32

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0,4000]

##### 설명

메모리 테이블에 사용된 가변 크기 타입 데이터의 기본 in row 크기를 지정한다. in row 크기는 가변 크기 타입의 칼럼에 데이터가 들어갈 때 데이터 길이가 이 값보다 작거나 같으면 고정(fixed) 영역에 저장한다. 이보다 긴 경우에는 가변(variable) 영역에 들어가도록 지정하는 속성이다. 메모리 테이블에만 해당하는 것으로 디스크 테이블은 이 프로퍼티를 참조하지 않는다.

in row 절에 대한 자세한 사항은 1장의 데이터 타입 부분을 참조한다.

#### MEM_SIZE_CLASS_COUNT (단위 : 개수)

##### 데이터 타입

Unsigned Integer

##### 기본값

4

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 4]

##### 설명

메모리 페이지의 빈 공간(free space)을 몇 개의 클래스로 구분한 것인지를 나타낸다.

#### MIN_COMPRESSION_RESOURCE_COUNT (단위 : 개수)

##### 데이터 타입

unsigned integer

##### 기본값

16

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 16384]

##### 설명

로그 관리자가 로그를 압축하기 위해 사용하는 버퍼 청크(buffer chunk)의 최소한의 개수를 나타낸다 (한 개의 압축 버퍼 청크는 약 16KB이다).

#### MIN_LOG_RECORD_SIZE_FOR_COMPRESS (단위 : 바이트)

##### 데이터 타입

Unsigned Integer

##### 기본 값

512

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

로그 압축을 수행의 기준이 되는 로그의 크기를 설정할 수 있다. 이 값이 0으로 설정된 경우 로그 압축을 수행하지 않으며, 로그 크기가 설정된 값보다 큰 경우 로그 압축을 수행한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### MIN_PAGES_ON_DB_FREE_LIST

##### 데이터 타입

Unsigned Integer

##### 기본값

16

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 232-1]

##### 설명

데이타베이스의 다중화된 사용가능한 페이지 리스트에서 페이지를 분배할 때 각 페이지 리스트에 남겨 놓아야할 최소 페이지 개수이다.

#### MIN_PAGES_ON_TABLE_FREE_LIST

##### 데이타 타입

Unsigned Integer

##### 기본값

1

##### 속성

변경가능, 단일 값

##### 값의 범위

[ 1, 232-1]

##### 설명

테이블에서 데이타베이스로 빈 페이지를 반납하거나, 다중화된 사용 가능한 페이지 리스트에서 페이지를 분배할 때 각 페이지 리스트에 남겨 놓아야 할 최소 페이지 개수이다.

#### MIN_TASK_COUNT_FOR_THREAD_LIVE

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

변경 가능, 단일 값

##### 값의 범위

[1, 1024]

##### 설명

이 프로퍼티는 서비스 쓰레드가 해제되지 않기 위해 할당 받아야 하는 최소한의 클라이언트 수를 설정한다. 만약 서비스 쓰레드가 할당 받은 클라이언트의 수가 이 프로퍼티의 값보다 적으면, 곧바로 해제되는 것이 아니라 일정 기간 대기 상태로 놓인다. 대기중인 서비스 쓰레드가 SERVICE_THREAD_INITIAL_LIFESPAN에 설정된 주기동안 이 프로퍼티의 개수 이상 클라이언트를 할당 받지 못하면 해제된다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### PCTFREE (단위: 백분율)

##### 데이터 타입

Unsigned Integer

##### 기본값

10

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 99]

##### 설명

이 프로퍼티는 테이블스페이스의 각 페이지에서 삽입 가능한 상태를 유지하기 위한 여유 공간의 최소 비율을 나타낸다. 이 여유 공간은 기존 레코드들을 갱신하기 위해 필요하다.

만약 테이블스페이스의 전체 크기가 100MB인 경우 PCTFREE가 10이라면, 90%의 공간인 90MB까지만 삽입 연산이 가능하다.

디스크 테이블 생성 시 CREATE TABLE 구문에서 PCTFREE 값이 지정되지 않은 경우 기본값이 사용된다.

#### PCTUSED (단위: 백분율)

##### 데이터 타입

Unsigned Integer

##### 기본값

40

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 99]

##### 설명

이 프로퍼티는 테이블스페이스의 페이지가 갱신 연산만 가능한 상태에서 다시 삽입 연산이 가능한 상태로 가기 위한 페이지의 사용 공간 비율을 나타낸다.

페이지의 사용 공간은 PCTFREE에서 지정한 값까지 입력할 경우 갱신 연산만이 가능한 상태로 된다. 이 때 갱신과 삭제로 빈 공간이 다시 확보되어 PCTUSED에서 정한 값보다 낮아지면, 새로운 행을 삽입할 수 있는 상태가 된다.

디스크 테이블 생성시 CREATE TABLE 구문에서 PCTUSED 값이 지정되지 않은 경우 기본값으로 사용된다.

#### QP_MEMORY_CHUNK_SIZE (단위 : 바이트)

##### 데이터 타입

Unsigned long

##### 기본값

65536

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1024, 264-1]

##### 설명

질의 처리기에서 필요한 메모리를 시스템에서 가져올 때 확장 단위를 정한다.

#### RECYCLEBIN_DISK_MAX_SIZE (단위: 바이트)

##### 데이터 타입

Unsigned Long

##### 기본값

264-1

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 264-1]

##### 설명

디스크 테이블이 버려지는(drop) 휴지통의 사이즈를 명시할 수 있다.

Altibase 운영 중 ALTER SYSTEM문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### RECYCLEBIN_ENABLE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

테이블이 DROP 구문으로 삭제된 경우 휴지통으로 버려지거나, 데이터베이스 시스템에서 바로 삭제할 것인지를 설정할 수 있다. 기본값은 DROP 구문을 수행하면 시스템에서 테이블이 제거된다.

휴지통으로 버려진 테이블은 이름이 변경되어 저장된다. 그리고 테이블 타입이 ‘R’ 타입으로 변경 되어 일체 다른 DDL 및 INSERT/UPDATE/DELETE 등을 수행 할 수 없다. 단 SELECT는 가능하다.

휴지통에 테이블이 존재한다면 프로퍼티의 값을 0으로 변경하더라도 휴지통의 테이블을 조회하거나 FLASHBACK 또는 PURGE 구문을 사용하여 복구 및 제거할 수 있다.

Altibase 운영 중 ALTER SESSION문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

0 : Disable(기본값)-테이블이 데이터베이스에서 삭제된다.

1 : Enable - 테이블이 휴지통으로 버려진다.

#### RECYCLEBIN_MEM_MAX_SIZE (단위: 바이트)

##### 데이터 타입

Unsigned Long

##### 기본값

4 GB

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 264-1]

##### 설명

메모리 테이블이 버려지는(drop) 휴지통의 사이즈를 명시할 수 있다.

Altibase 운영 중 ALTER SYSTEM문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REDUCE_TEMP_MEMORY_ENABLE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

가변 길이 칼럼의 데이터가 메모리 테이블스페이스에 임시로 저장될 때 차지하는 공간을 줄일 수 있는 프로퍼티이다.

Altibase 서버가 디스크 테이블이나 뷰에 대한 질의를 처리할 때 중간 결과를 임시로 저장하는 공간은 기본적으로 디스크 임시 테이블스페이스이다. 그러나 성능 향상을 목적으로 TEMP_TBS_MEMORY 힌트(*Administrator's Manual, Performance Tuning Guide* 참고)를 사용하여 중간 결과가 메모리 테이블스페이스에 저장되도록 할 수 있다.

기본값인 0은 가변 길이 칼럼의 데이터도 고정 길이 칼럼처럼 고정된 길이의 임시 저장 공간을 사용하여, 불필요한 공간을 차지할 수 있다. 이러한 공간 낭비를 줄이기 위해 이 프로퍼티를 1로 설정하면 가변 길이 칼럼의 실제 데이터만큼 공간을 사용한다. 그러나, 메모리 사용량은 줄어들지만 질의 처리 속도가 떨어질 수 있다.

0: 가변 길이 칼럼이 정의된 길이만큼 임시 저장 공간을 사용

1: 가변 길이 칼럼이 실제 데이터만큼 임시 저장 공간을 사용

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### SECURITY_ECC_POLICY_NAME

##### 데이터 타입

String

##### 기본값

없음

##### 속성

변경 가능, 단일 값

##### 값의 범위

없음

##### 설명

암호화 칼럼을 위한 보안 모듈을 수행할 때 사용하는 ECC (Encrypted Comparison Code) 알고리듬의 이름을 지정한다.

#### SECURITY_MODULE_LIBRARY

##### 데이터 타입

String

##### 기본값

없음

##### 속성

변경 가능, 단일 값

##### 값의 범위

없음

##### 설명

보안 모듈의 라이브러리 파일 이름을 지정한다. 보안 모듈을 수행할 때 이 파일이 사용된다.

#### SECURITY_MODULE_NAME

##### 데이터 타입

String

##### 기본값

없음

##### 속성

변경 가능, 단일 값

##### 값의 범위

없음

##### 설명

보안 모듈을 수행할 때 명시하는 보안 모듈의 이름을 지정한다.

#### SERVICE_THREAD_INITIAL_LIFESPAN

##### 데이터 타입

Unsigned Integer

##### 기본값

6000

##### 속성

변경 가능, 단일 값

##### 값의 범위

[30, 232-1]

##### 설명

서비스 쓰레드의 해제 주기를 설정한다. 해제 주기란, 쓰레드를 해제하기 위해 쓰레드 매니저가 대기중인 서비스 쓰레드들의 상태를 확인해야 하는 횟수이다. 대기중인 서비스 쓰레드는 쓰레드 매니저가 이 프로퍼티에 설정된 확인 횟수동안 클라이언트를 할당 받지 못하면 해제된다.

대기하는 서비스 쓰레드는 MIN_TASK_COUNT_FOR_THREAD_LIVE 프로퍼티에 설정한 값보다 적은 클라이언트를 할당 받을 때 정해진다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### SMALL_TABLE_THRESHOLD

##### 데이터 타입

Unsigned Integer

##### 기본값

128

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

디스크 테이블에 FULL SCAN 이 수행될 때, 그 테이블의 페이지 개수가 이 프로퍼티에 지정된 페이지 개수보다 작거나 같으면 “다중 페이지 읽기”로 디스크에서 버퍼로 읽혀온 페이지가 full scan이 끝난 후에 그대로 버퍼에 남겨진다. 테이블의 페이지 개수가 이 프로퍼티에 지정된 페이지 개수보다 크면 페이지는 버퍼에 남겨지지 않는다.

이 값을 0으로 지정한 경우, 테이블의 페이지 개수에 상관없이 읽혀온 페이지는 버퍼에 남겨지지 않는다.

이 값이 최대값인 232-1로 지정된 경우, 테이블의 페이지 개수에 상관없이 읽혀온 페이지는 무조건 버퍼에 남겨진다.

#### ST_OBJECT_BUFFER_SIZE (단위: 바이트)

##### 데이터 타입

Unsigned long

##### 기본값

32000 (32KByte)

##### 속성

변경 가능, 단일 값

##### 값의 범위

[32000, 104857600]

##### 설명

단일 공간 객체(Geometry Object)의 최대 크기를 지정할 수 있다.

#### SYS_DATA_FILE_INIT_SIZE (단위: 바이트)

##### 데이터 타입

Unsigned long

##### 기본값

100M (100 * 1024 * 1024)

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[8*8K, 32GB]

##### 설명

SYS_TBS_DISK_DATA (시스템 디스크 테이블스페이스) 생성시 데이터 파일(system001.dbf)의 기본 크기를 명시한다. 또한 SYS_TBS_DISK_DATA에 데이터 파일(system001.dbf를 제외한 사용자가 명시한 데이터 파일)을 추가할 때 초기 크기를 지정하지 않은 경우 기본값으로 사용된다.

#### SYS_DATA_FILE_MAX_SIZE (단위: 바이트)

##### 데이터 타입

Unsigned long

##### 기본값

2 * 1024 * 1024 * 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[8 * 8K, 32GB]

##### 설명

SYS_TBS_DISK_DATA (시스템 디스크 데이터 테이블스페이스) 생성 시 할당될 데이터 파일의 최대 크기를 명시한다. 최소 SYS_DATA_FILE_INIT_SIZE 이상의 크기를 가져야 하며, 최소값은 64K이다.

또한 SYS_TBS_DISK_DATA 테이블스페이스에 데이터 파일을 추가할 때 최대 크기를 지정하지 않았을 경우 이 값을 기본값으로 사용한다.

#### SYS_DATA_FILE_NEXT_SIZE (단위: 바이트)

##### 데이터 타입

Unsigned long

##### 기본값

1 * 1024 * 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[8 * 8K, 32GB]

##### 설명

시스템 디스크 데이터 테이블스페이스 (SYS_TBS_DISK_DATA)의 속성이 “autoextend on”으로 설정되어 있는 경우, 데이터량의 증가에 따라서 명시된 값만큼 데이터 파일의 크기가 자동으로 확장된다.

데이터 파일의 크기가 SYS_DATA_FILE_MAX_SIZE에 도달한 상태에서 다른 데이터 파일에도 SYS_DATA_FILE_NEXT_SIZE에 설정한 만큼의 유효 공간이 없다면 테이블스페이스 공간 부족 오류가 발생한다.

#### SYS_DATA_TBS_EXTENT_SIZE (단위: 바이트)

##### 데이터 타입

Unsigned long

##### 기본값

512 * 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[40K, 32G]

##### 설명

SYS_TBS_DISK_DATA (시스템 디스크 데이터 테이블스페이스 1) 생성 시 익스텐트의 크기2를 명시한다. 최소 5개 이상의 페이지를 갖도록 설정해야 하고 최소값은 40kB (5*8kB)이다.

[1] 시스템 디스크 데이터 테이블스페이스 (System Disk Data Tablespace):

데이터베이스 생성 시 기본적으로 생성되는 디스크 데이터 테이블스페이스이다. 데이터베이스 객체 중 디스크 테이블과 디스크 인덱스만 저장된다.

[2] 하나의 테이블스페이스의 EXTENT의 크기(SIZE)는 생성 시 지정하면 이후

변경할 수 없다. 명시하지 않을 경우 기본값은 32개의 페이지 크기로 고정되어 있다.

#### SYS_TEMP_FILE_INIT_SIZE (단위: 바이트)

##### 데이터 타입

Unsigned long

##### 기본값

100M (100 * 1024 * 1024)

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[ 8 * 8kB, 32GB]

##### 설명

SYS_TBS_DISK_TEMP 생성 시 임시 데이터 파일(temp001.dbf)의 초기 크기를 명시한다. 또한 SYS_TBS_DISK_TEMP에 임시 데이터 파일을 추가할 때 초기 크기를 지정하지 않았을 경우, 이 값이 기본값으로 사용된다.

#### SYS_TEMP_FILE_MAX_SIZE (단위: 바이트)

##### 데이터 타입

Unsigned long

##### 기본값

2 * 1024 * 1024 * 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[8 * 8K, 32GB]

##### 설명

SYS_TBS_DISK_TEMP 생성 시 할당될 데이터 파일(temp001.dbf)의 최대 크기를 명시한다.

최소 SYS_TEMP_FILE_INIT_SIZE 이상의 크기를 가져야 하며, 가능한 최소값은 64kB이다. 또한, SYS_TBS_DISK_TEMP 테이블스페이스에 임시 데이터 파일을 추가할 때 최대 크기를 지정하지 않았을 경우, 여기에 명시한 값이 기본 최대 크기가 된다.

#### SYS_TEMP_FILE_NEXT_SIZE (단위: 바이트)

##### 데이터 타입

Unsigned long

##### 기본값

1 * 1024 * 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[8 * 8kB, 32GB]

##### 설명

SYS_TBS_DISK_TEMP 테이블스페이스에 데이터 파일의 공간이 부족한 경우 명시된 값만큼 데이터 파일의 크기를 확장한다.

#### SYS_TEMP_TBS_EXTENT_SIZE (단위: 바이트)

##### 데이터 타입

Unsigned long

##### 기본값

256 * 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[40kB, 32GB]

##### 설명

시스템 디스크 임시 테이블스페이스3 SYS_TBS_DISK_TEMP 생성 시 익스텐트의 크기를 명시한다.

[3] 시스템 디스크 임시 테이블스페이스 (System disk temporary tablespace):

데이터베이스 생성 시 기본적으로 생성되며, 데이터베이스 각종 연산의 임시 저장소로 사용되는 테이블스페이스이다. 모든 사용자의 디스크 객체를 위한 기본(DEFAULT) 임시 테이블스페이스로 지정된다. 데이터베이스 객체 중 디스크 테이블과 디스크 인덱스만 저장된다.

최소 5개 페이지(40kB = 5 * 8K) 이상의 크기를 가져야 한다.

#### SYS_UNDO_FILE_INIT_SIZE (단위: 바이트)

##### 데이터 타입

Unsigned long

##### 기본값

100 * 1024 * 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[32 * 8kB, 32GB]

##### 설명

SYS_TBS_DISK_UNDO 테이블스페이스 생성 시 데이터 파일(undo001.dbf)의 기본 크기를 명시한다. 또한 SYS_TBS_DISK_UNDO에 데이터 파일을 추가할 때 초기 크기를 지정하지 않았을 경우 기본값으로 사용된다.

#### SYS_UNDO_FILE_MAX_SIZE (단위: 바이트)

##### 데이터 타입

Unsigned long

##### 기본값

2 * 1024 * 1024 * 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[32 * 8kB, 32GB]

##### 설명

SYS_TBS_DISK_UNDO 테이블스페이스 생성 시 할당될 데이터 파일(undo001.dbf)의 최대 크기를 명시한다. 최소 SYS_UNDO_FILE_INIT_SIZE 이상의 크기를 가져야 한다. 가능한 최소값은 256K이다. SYS_TBS_DISK_UNDO 테이블스페이스에 데이터 파일을 추가할 때 최대 크기를 지정하지 않았을 경우, 기본 최대 크기로 사용된다.

#### SYS_UNDO_FILE_NEXT_SIZE (단위: 바이트)

##### 데이터 타입

Unsigned long

##### 기본값

1 * 1024 * 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[8 * 8kB, 32GB]

##### 설명

SYS_TBS_DISK_UNDO테이블스페이스의 데이터 파일에 공간이 부족한 경우 명시된 값만큼 데이터 파일의 크기를 확장한다.

#### SYS_UNDO_TBS_EXTENT_SIZE (단위: 바이트)

##### 데이터 타입

Unsigned long

##### 기본값

256 * 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[40kB, 32GB]

##### 설명

시스템 디스크 언두 테이블스페이스4 SYS_TBS_DISK_UNDO 생성 시 익스텐트의 크기를 명시한다.

[4] 시스템 디스크 언두 테이블스페이스 (System disk undo tablespace):

데이터베이스 생성 시 기본적으로 생성되며 언두(undo) 정보를 저장하기 위해 유일하게 사용되는 특수한 테이블스페이스이다. 사용자는 디스크 언두 테이블스페이스 내에 테이블이나 인덱스 등을 생성할 수 없다. 데이터베이스 내에 오직 하나만 존재 하며, 사용자가 생성하거나 삭제할 수 없다.

#### TABLE_BACKUP_FILE_BUFFER_SIZE (단위 : 바이트)

##### 데이터 타입

Unsigned Integer

##### 기본값

1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1048576]

##### 설명

메모리 테이블의 칼럼을 추가하거나 삭제할 경우 사용되는 테이블 백업 파일의 I/O 버퍼 크기를 나타낸다.

#### TABLE_COMPACT_AT_SHUTDOWN

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

데이터베이스 종료 시 테이블을 컴팩트할지 여부를 나타낸다. 데이터베이스 재시작시 테이블을 위한 메모리 낭비를 줄이기 위해 1로 설정하기를 권장한다.

#### TEMP_HASH_BUCKET_DENSITY

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 50]

##### 설명

해쉬 버킷 하나가 관리해야 하는 임시 테이블의 페이지 프레임 개수를 백분율로 명시한다. 이 값이 커질수록 필요한 해쉬 버킷의 개수가 줄어들어 메모리는 적게 사용되지만, 한 버킷당 관리해야 할 임시 페이지 프레임의 수가 증가하기 때문에 연산 비용이 커진다.

예를 들어 임시 페이지 프레임의 개수가 100일 때, 이 값이 1이면 버킷의 개수는 프레임의 개수와 같아진다. 이 값이 2이면 버킷의 개수는 프레임 개수의 절반인 50이 된다.

#### TEMP_PAGE_CHUNK_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

128

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 232-1]

##### 설명

임시 데이터 페이지를 한번에 할당하는 개수이다.

#### USER_DATA_FILE_INIT_SIZE (단위: 바이트)

##### 데이터 타입

Unsigned long

##### 기본값

100 * 1024 * 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[8 * 8kB, 32GB]

##### 설명

사용자 디스크 데이터 테이블스페이스에 사용자 정의 데이터 파일을 생성하거나 추가할 때 데이터 파일의 초기 크기를 명시한다. 데이터 파일을 생성하거나 추가할 때 초기 크기를 명시하지 않은 경우 기본값으로 사용된다.

#### USER_DATA_FILE_MAX_SIZE (단위: 바이트)

##### 데이터 타입

Unsigned long

##### 기본값

2 * 1024 * 1024 * 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[8 * 8kB, 32GB]

##### 설명

사용자 디스크 데이터 테이블스페이스에 사용자 정의 데이터 파일을 생성하거나 추가할 때 데이터 파일의 최대 크기를 명시한다.

최소 USER_DATA_FILE_INIT_SIZE 이상의 크기를 가져야 하며, 가능한 최소값은 64K이다. 테이블 스페이스 생성시 최대 크기를 명시하지 않은 경우 기본 최대 크기를 의미한다.

#### USER_DATA_FILE_NEXT_SIZE (단위: 바이트)

##### 데이터 타입

Unsigned long

##### 기본값

1 * 1024 * 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[8 * 8kB, 32GB]

##### 설명

사용자 디스크 데이터 테이블스페이스의 사용자 정의 데이터 파일에 데이터 파일 공간이 부족한 경우, 명시된 값만큼 데이터 파일의 크기를 확장한다.

#### USER_DATA_TBS_EXTENT_SIZE (단위: 바이트)

##### 데이터 타입

Unsigned long

##### 기본값

512 * 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[2 * 8kB, 264-1]

##### 설명

사용자 디스크 데이터 테이블스페이스5 생성 시 익스텐트의 크기를 명시한다.

[5] 사용자 디스크 데이터 테이블스페이스 (User disk data tablespace):

사용자의 객체를 저장하기 위한 테이블스페이스이다. 데이터베이스 객체 중 디스크 테이블과 디스크 인덱스만 저장된다.

#### USER_TEMP_FILE_INIT_SIZE (단위: 바이트)

##### 데이터 타입

Unsigned long

##### 기본값

100 * 1024 * 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[8 * 8kB, 32GB]

##### 설명

사용자 임시 테이블스페이스에 사용자 정의 임시 데이터 파일을 생성하거나 추가할 때 데이터 파일의 초기 크기를 명시한다. 임시 데이터 파일을 생성하거나 추가할 때 초기 크기를 명시하지 않은 경우 기본 크기로 사용된다.

#### USER_TEMP_FILE_MAX_SIZE (단위: 바이트)

##### 데이터 타입

Unsigned long

##### 기본값

2 * 1024 * 1024 * 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[8 * 8kB, 32GB]

##### 설명

사용자 임시 테이블스페이스에 사용자 정의 임시 데이터 파일을 생성하거나 추가할 때 할당 될 데이터파일의 최대 크기를 명시한다.

최소 USER_DATA_FILE_INIT_SIZE 이상의 크기를 가져야 하며, 가능한 최소값은 64kB이다. 임시 데이터 파일을 생성하거나 추가할 때 최대 크기를 지정하지 않은 경우 이 프로퍼티가 최대 크기로 사용된다.

#### USER_TEMP_FILE_NEXT_SIZE (단위: 바이트)

##### 데이터 타입

Unsigned long

##### 기본값

1 * 1024 * 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[8 * 8kB, 32GB]

##### 설명

사용자 임시 테이블스페이스에 사용자 정의 임시 데이터 파일에 데이터 파일의 공간이 부족한 경우 명시된 값만큼 데이터 파일의 크기를 확장한다.

#### USER_TEMP_TBS_EXTENT_SIZE (단위: 바이트)

##### 데이터 타입

Unsigned long

##### 기본값

256 * 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[2 * 8kB, 264-1]

##### 설명

사용자 임시 테이블스페이스(User temporary tablespace) 생성 시 익스텐트의 크기를 명시한다. 최소 2개 페이지(16kB = 2*8kB) 이상의 크기를 가져야 한다.

#### VOLATILE_MAX_DB_SIZE (단위 : 바이트)

##### 데이터 타입

Unsigned long

##### 기본값

232+1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

32비트: [2097152, 232+1]

64비트: [2097152, 264]

##### 설명

모든 휘발성 테이블스페이스 크기의 합에 대한 최대값을 설정한다. 운영 체제에서 제공하는 메모리 공간의 크기를 초과할 수 없다.

### 성능 관련 프로퍼티

#### AGER_WAIT_MAXIMUM (단위: 마이크로 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

1000000

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

가비지 콜렉터(garbage collector, 혹은 Ager) 관련 쓰레드들이 가비지 콜렉터 sleep 시, 시스템 호출인 sleep의 과도한 사용으로 인하여 (특히, HP 시스템) 발생하는 서버의 성능 저하를 막기 위한 것이다. 이 값들을 이용하여 서버 운영 중에 가비지 콜렉터 sleep time을 적절히 조절할 수 있도록 한다.

#### AGER_WAIT_MINIMUM (단위: 마이크로 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

200000

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

가비지 콜렉터(garbage collector, 혹은 Ager) 관련 쓰레드들이 가비지 콜렉터 sleep 시 시스템 호출인 sleep의 과도한 사용으로 인하여 (특히, HP 시스템) 발생하는 서버의 성능 저하를 막기 위한 것이다. 이 값들을 이용하여 서버 운영 중에 가비지 콜렉터 sleep time을 적절히 조절할 수 있도록 한다.

#### BUFFER_VICTIM_SEARCH_INTERVAL (단위: 밀리초)

##### 데이터 타입

Unsigned Integer

##### 기본값

3000

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 86400000]

##### 설명

이 프로퍼티는 버퍼 교체 대상 검색이 실패한 후 플러셔가 플러시 작업을 할 것을 기다리는 시간을 명시한다. 이 시간을 대기하여도 교체 대상 버퍼를 찾지 못하면, V$BUFFPOOL_STAT 성능 뷰의 VICTIM_SEARCH_WARP의 값이 증가한다.

#### BUFFER_VICTIM_SEARCH_PCT(단위 : 백분율)

##### 데이터 타입

Unsigned Integer

##### 기본값

5

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 100]

##### 설명

버퍼 교체 대상을 LRU 리스트에서 검색할 때 얼마나 탐색할 것인지를 명시한다. 이 프로퍼티는 하나의 LRU 리스트 전체를 100이라고 할 때, LRU Cold last를 기준으로 명시한 값의 퍼센트만큼 검색하는 것을 나타낸다.

#### CHECKPOINT_BULK_SYNC_PAGE_COUNT (단위: 페이지 개수)

##### 데이터 타입

Unsigned Integer

##### 기본값

3200

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

체크포인트를 할 때 메모리와 디스크의 데이터를 일치시키기 위해 한 번에 몇 개의 페이지 단위로 내용을 일치시킬 것인지를 나타낸다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### CHECKPOINT_BULK_WRITE_PAGE_COUNT (단위 : 개수)

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

체크포인트시 메모리의 더티 페이지들을 여러 번에 나눠서 디스크로 저장할 수 있다. 이 때 이 프로퍼티를 사용해서 한 번에 저장할 수 있는 더티 페이지의 개수를 설정할 수 있다. 이 값이 0일 때는 한 번에 모든 더티 페이지가 디스크 데이터베이스로 저장될 것이다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### CHECKPOINT_BULK_WRITE_SLEEP_SEC (단위 : 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 2592000]

##### 설명

CHECKPOINT_BULK_WRITE_PAGE_COUNT의 값이 0이 아닐 때 더티 페이지들을 디스크로 저장 후 대기하는 시간(초)을 나타낸다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### CHECKPOINT_BULK_WRITE_SLEEP_USEC (단위 : 마이크로초)

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 60000000]

##### 설명

CHECKPOINT_BULK_WRITE_PAGE_COUNT의 값이 0이 아닐 때 더티 페이지들을 디스크로 저장 후 대기하는 시간(마이크로 초)을 나타낸다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### CHECKPOINT_FLUSH_COUNT (단위: 프레임 개수)

##### 데이터 타입

Unsigned Integer

##### 기본값

64

##### 속성

변경 가능, 단일 값

##### 값의 범위

[1, 264-1]

##### 설명

플러셔가 한 번의 주기에서 체크포인트 플러시를 할 때 플러시 할 수 있는 버퍼 페이지(프레임)의 개수를 명시한다.

#### CHECKPOINT_FLUSH_MAX_GAP (단위: 로그 파일 개수)

##### 데이터 타입

Unsigned Integer

##### 기본값

10

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

체크포인트 플러시를 발생시키는 조건 중의 하나가 된다. 체크포인트 리스트에 있는 갱신된 버퍼들 중에 갱신 LSN(recovery LSN)이 가장 작은 값과 현재 로그 LSN과의 차이가 이 프로퍼티에서 지정한 값이 되면 체크포인트 플러시를 수행한다.

이 값은 서버 재구동시의 복구 시간을 결정한다. 이 값이 클수록 체크포인트 플러시가 적게 발생하며, 서버의 재구동시 복구 시간은 길어진다. 서버 운영 중에도 변경이 가능하다.

#### CHECKPOINT_FLUSH_MAX_WAIT_SEC (단위: 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

10

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

체크포인트 플러시를 발생시키는 조건 중의 하나이다. 마지막 플러시 작업이 끝난 이후 이 프로퍼티에서 지정한 시간이 지나면 체크포인트 플러시가 발생한다.

#### CM_BUFFER_MAX_PENDING_LIST

##### 데이터 타입

Unsigned Integer

##### 기본값

512

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 512]

##### 설명

메모리가 급격하게 증가하는 것을 방지하기 위해, 이 프로퍼티를 사용해서 한 세션에서 할당받을 수 있는 최대 통신 버퍼 블록의 수를 제한할 수 있다.

#### CM_DISPATCHER_SOCK_POLL_TYPE

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 2, 3]

##### 설명

Altibase 서버의 디스패처(Dispatcher)에서 소켓 감지를 위한 시스템 콜을 선택하는 프로퍼티이다. 클라이언트의 동시 접속이 1,000개 이상일 때 POLL() 시스템 콜이 사용되면 성능 향상에 도움이 된다.

- 1: SELECT() 시스템 콜
- 2: POLL() 시스템 콜; 지원되는 운영시스템에서만 사용이 가능함
- 3: EPOLL() 시스템 콜; 지원되는 운영시스템에서만 사용이 가능함

#### DATABASE_IO_TYPE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

데이터파일과 관련하여 디스크 I/O가 수행될 때, Direct I/O와 Buffered I/O 두 가지 방법이 사용될 수 있다. Direct I/O를 사용하기 위해서는 이 프로퍼티의 값을 1로 설정하며 Buffered I/O 를 사용하려면 0으로 설정한다.

Direct I/O는 디스크 I/O가 발생하는 동안 CPU 점유율을 줄인다는 장점이 있다. Buffered I/O는 read-ahead, asynchronous write 기법을 사용하므로 디스크 I/O 요구가 있을 때마다 실제로 디스크에 접근하지 않을 수도 있으므로 응용 프로그램 수준에서 볼 때 디스크 I/O가 훨씬 빠르다는 장점이 있다.

#### DATAFILE_WRITE_UNIT_SIZE (단위 : 개수)

##### 데이터 타입

Unsigned Long

##### 기본값

1024

##### 속성

변경 가능, 단일 값

##### 값의 범위

[1, 1024]

##### 설명

데이터 파일을 생성할 때 데이터의 기본 단위를 설정한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### DB_FILE_MULTIPAGE_READ_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

8

##### 속성

변경 가능, 단일 값

##### 값의 범위

[1, 128]

##### 설명

디스크 테이블을 풀 스캔(Full Scan)할 때 이 값에 정해진 페이지 개수 단위로 IO를 수행한다.

이 때 디스크 테이블의 익스텐트 사이즈 즉 익스텐트 내의 페이지 개수가 여기에 명시한 값의 배수이면서 이 값보다 크면 MPR(Multi Page Read)을 한다.

그러나 여기에 명시한 값의 배수가 아니고, 이 값보다 작으면 SPR(Single Page Read)로 수행한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### DEDICATED_THREAD_CHECK_INTERVAL (단위: 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

3600

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 264-1]

##### 설명

전용 쓰레드(Dedicated thread) 모드에서 서비스 쓰레드가 정리되는 시간 간격을 설정하는 프로퍼티이다. 이 프로퍼티는 DEDICATED_THREAD_MODE 프로퍼티가 1일 때에만 유효하다.

이 프로퍼티에 설정한 주기로 작업이 없는 서비스 쓰레드가 해제된다. 단, DEDICATED_THREAD_INIT_COUNT에 설정된 개수만큼의 서비스 쓰레드는 유지된다.

이 프로퍼티의 값이 0인 경우, 서비스 쓰레드가 정리되지 않는다.

#### DEDICATED_THREAD_INIT_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 65535]

##### 설명

전용 쓰레드(Dedicated thread) 모드에서 초기에 생성할 서비스 쓰레드의 개수를 지정하는 프로퍼티이다. 이 프로퍼티는 DEDICATED_THREAD_MODE 프로퍼티가 1일 때에만 유효하다.

DEDICATED_THREAD_INIT_COUNT 값은 DEDICATED_THREAD_MAX_COUNT 프로퍼티에 설정한 값보다 작아야 한다.

#### DEDICATED_THREAD_MAX_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 65535]

##### 설명

전용 쓰레드(Dedicated thread) 모드에서 최대로 생성할 수 있는 서비스 쓰레드의 개수를 지정하는 프로퍼티이다. 이 프로퍼티는 DEDICATED_THREAD_MODE 프로퍼티가 1일 때에만 유효하다.

초기에 생성된 서비스 쓰레드가 전부 클라이언트에 할당된 경우, 서비스 쓰레드의 개수는 DEDICATED_THREAD_MAX_COUNT까지 증가하게 된다.

DEDICATED_THREAD_MAX_COUNT 값은 MAX_CLIENT 프로퍼티에 설정한 값보다 작아야 한다.

#### DEDICATED_THREAD_MODE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

서비스 쓰레드가 클라이언트에 대해 전용 쓰레드(Dedicated thread) 모드로 동작할지 여부를 설정하는 프로퍼티이다.

1인 경우 전용 쓰레드 모드로 동작하고, 0인 경우 멀티플렉싱 쓰레드(Multiplexing thread) 모드로 동작한다.

#### DEFAULT_FLUSHER_WAIT_SEC (단위: 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

변경 가능, 단일 값

##### 값의 범위

[1, 232-1]

##### 설명

플러셔의 최소 대기 시간을 명시한다. 플러셔는 특정 조건을 제외하고, 항상 이 시간만큼 대기 후 플러시 작업을 수행한다. 플러셔가 대기에서 풀려나 아무런 플러시를 하지 않는다면, 대기 시간은 1초씩 계속 늘어난다.

#### DELAYED_FLUSH_LIST_PCT (단위: 백분율)

##### 데이터 타입

Unsigned Integer

##### 기본값

30

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 100]

##### 설명

지연된 플러시 목록의 최대 비율을 명시한다. Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### DELAYED_FLUSH_PROTECTION_TIME_MSEC (단위: 밀리초)

##### 데이터 타입

Unsigned Integer

##### 기본값

100

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 100000]

##### 설명

최근에 사용된 Page로 판단하기 위한 기준 시간이다. 마지막으로 사용된 시간이 설정 값 이하라면 최근에 사용된 Page로 판단한다. Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### DIRECT_IO_ENABLED

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

데이터베이스를 디스크로 직접 입출력할 것인지 여부를 나타낸다.

0 : disable (직접 입출력하지 않음)

1 : enable (직접 입출력함)

#### DISK_INDEX_BUILD_MERGE_PAGE_COUNT (단위: 페이지 수)

##### 데이터 타입

Unsigned Integer

##### 기본값

128

##### 속성

변경 가능, 단일 값

##### 값의 범위

[2, 232-1]

##### 설명

디스크 인덱스를 생성할 때 데이터에서 추출된 키들을 메모리에서 한번에 정렬할 수 없을 경우, 외부 정렬에 사용될 페이지의 수를 나타낸다. 운영 중 ALTER SYSTEM 문을 이용해 프로퍼티의 값을 변경할 수 있다.

#### EXECUTE_STMT_MEMORY_MAXIMUM (단위 : 바이트)

##### 데이터 타입

Unsigned Long

##### 기본값

1G

##### 속성

변경 가능, 단일 값

##### 값의 범위

[1024*1024, 264-1]

##### 설명

하나의 질의문(statement)이 사용할 수 있는 execute 메모리의 양을 제한한다. 이 프로퍼티는 가동중에 TER SYSTEM 구문으로 변경 가능하다.

#### EXECUTOR_FAST_SIMPLE_QUERY

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 2]

##### 설명

이 프로퍼티는 단순한 DML 구문을 최적화하거나 Nested Loop Join을 사용하는 구문의 실행 계획을 최적화하여 성능을 향상시킬 수 있다. DA 모드에서 사용할 때 성능을 기대할 수 있으며, SIMPLE QUERY PLAN으로 실행되면 PLAN TREE에서 확인할 수 있다. 단 SIMPLE QUERY 최적화를 사용할 때에는 이전 동작과 같은 동작을 보장할 수 없으므로, 주의를 기울여야 한다.

0: SIMPLE QUERY PLAN을 사용하지 않는다.

1: SIMPLE QUERY PLAN을 MEMORY TABLE에 사용한다.

2: SIMPLE QUERY PLAN을 MEMORY PARTITION TABLE에 사용한다.

#### FAST_START_IO_TARGET (단위: 페이지 개수)

##### 데이터 타입

Unsigned Long

##### 기본값

10000

##### 속성

변경 가능, 단일 값

##### 값의 범위

[1, 264-1]

##### 설명

서버를 재구동 단계에서 복구할 때 읽을 리두(Redo) 페이지의 개수를 명시한다.

운영중에 플러셔가 체크포인트 플러시를 할 때 버퍼에 남은 더티 페이지가 이 프로퍼티에서 지정한 페이지보다 많다면, 그 차이만큼 오래된 더티 페이지부터 디스크에 반영한다.

이 값은 서버 재구동시에 복구 시간을 결정해준다. 이 값이 작을수록 플러시할 페이지 수가 많아지기 때문에 서버를 재구동할 때 소요되는 복구 시간을 줄일 수 있다.

서버 운영중에 ALTER SYSTEM 문을 이용해 프로퍼티의 값을 변경할 수 있다.

#### FAST_START_LOGFILE_TARGET (단위: 로그 파일 개수)

##### 데이터 타입

Unsigned Integer

##### 기본값

100

##### 속성

변경 가능, 단일 값

##### 값의 범위

[1, 232-1]

##### 설명

서버를 재구동하여 복구할 때 읽을 로그 파일의 개수를 명시한다.

운영중에 플러셔가 체크포인트 플러시를 할 때, 체크포인트 리스트에 있는 더티 페이지 중 페이지 LSN의 LogFileNo와 현재 로그 LSN의 LogFileNo와의 차이가 이 프로퍼티에서 지정한 값보다 크면 페이지를 플러시한다.

이 값은 서버를 재구동할 때 복구 시간을 결정한다. 이 값이 작을수록 플러시 할 페이지 수는 많아지기 때문에 서버를 재구동할 때 소요되는 복구 시간을 줄일 수 있다.

서버 운영중에 ALTER SYSTEM 문을 이용해 프로퍼티의 값을 변경할 수 있다.

#### FAST_UNLOCK_LOG_ALLOC_MUTEX

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

서버의 여러 쓰레드가 로그 버퍼에 동시에 접근할 수 있는지를 설정하는 프로퍼티이다. 이 프로퍼티의 값을 0으로 설정하면, 서버의 여러 쓰레드가 로그 버퍼에 순차적으로 접근할 수 있다. 그리고 이 값을 1로 설정하면, 서버의 쓰레드들이 로그 버퍼로 동시에 접근할 수 있다.

0: 동시 접근 불가능

1: 동시 접근 가능

#### HASH_AREA_SIZE (단위: 바이트)

##### 데이터 타입

Unsigned Long

##### 기본값

4MB

##### 속성

변경 가능, 단일 값

##### 값의 범위

[3M, 264-1]

##### 설명

서버가 해싱(hashing) 작업을 위해 사용하는 임시 테이블 하나의 메모리 크기를 지정한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### HASH_JOIN_MEM_TEMP_AUTO_BUCKET_COUNT_DISABLE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

해쉬 조인(Hash Join)에 사용되는 메모리 해쉬 임시 테이블의 필요한 버킷(Bucket) 개수를 설정한다.

0 : 해쉬 테이블에 삽입된 실제 레코드 개수 ( DISTINCT 해싱방식에 의해 처리 되는 경우 /*+ HASH BUCKET COUNT () */ HINT로 HSDS 노드의 해시 버킷 수 지정 가능)

1 : 쿼리 옵티마이저가 예측한 버킷 개수 또는 힌트 /*+ HASH BUCKET COUNT () */로 지정된 버킷 개수

HASH_JOIN_MEM_TEMP_PARTITIONING_DISABLE프로퍼티의 값이 0(파티셔닝 방식)이면, 실제 레코드 개수에 기반하여 버킷 개수만큼 구역을 나누는 것이 효과적이다.

HASH_JOIN_MEM_TEMP_PARTITIONING_DISABLE프로퍼티의 값이 1(버킷 방식)이면, 이 프로퍼티의 값과 관계 없이 쿼리 옵티마이저가 예측하거나 힌트로 지정한 버킷 개수를 사용한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### HASH_JOIN_MEM_TEMP_PARTITIONING_DISABLE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

해쉬 조인(Hash Join)에 사용되는 메모리 해쉬 임시 테이블의 레코드를 어떠한 방식으로 삽입하고 탐색할 것인지를 설정할 수 있다.

0 : 파티셔닝 방식

1 : 버킷 방식

파티셔닝 방식은 임시 공간에 삽입된 레코드의 개수를 기반으로 파티션 개수를 자동 설정하여 레코드를 파티션 단위로 탐색한다. 버킷 방식은 레코드를 버킷에 리스트 형태로 저장하여 버킷 단위로 레코드를 탐색하는 방식이다. 파티셔닝 방식을 사용할 경우 추가적인 메모리를 요구하지만, 대용량 데이터베이스를 사용할 때에는 버킷 방식보다 삽입 및 탐색 속도가 효과적이다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### HIGH_FLUSH_PCT (단위: 백분율)

##### 데이터 타입

Unsigned Integer

##### 기본값

5

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 100]

##### 설명

플러셔가 대기 상태에서 풀렸을 때 플러시 리스트의 길이가 전체 버퍼 크기에서 명시된 값 이상이 되면 교체 플러시를 수행한다. 이 때 해당되는 플러시 리스트의 모든 갱신된 버퍼들이 대기없이 연속적으로 플러시된다. 이 프로퍼티는 서버 운영중에 변경이 가능하다.

#### HOT_LIST_PCT (단위: 백분율)

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 100]

##### 설명

LRU 리스트 내에서 hot 영역의 비중을 명시한다. 이 프로퍼티는 서버 운영중에 변경이 가능하다.

#### HOT_TOUCH_CNT

##### 데이터 타입

Unsigned Integer

##### 기본값

2

##### 속성

변경 가능, 단일 값

##### 값의 범위

[1, 232-1]

##### 설명

버퍼가 hot하다고 판단하는 접근 횟수의 기준을 명시한다. 이 속성에서 명시한 값 이상으로 버퍼에 접근되면 그 버퍼는 hot이라고 판단되며, hot 버퍼는 교체 대상 검색시 hot 리스트로 이동한다.

#### INDEX_BUILD_THREAD_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

물리 코어의 개수

##### 속성

변경 가능, 단일 값

##### 값의 범위

[1, 512]

##### 설명

실행시간(runtime)에 인덱스를 재구축(rebuilding)하는 과정에서 생성되는 인덱스를 구축(index build)하는 쓰레드의 개수를 조절한다.

주석으로 처리할 경우 기본값으로 시스템의 물리적 코어의 개수(N) 만큼 병렬 작업 쓰레드가 생성된다.

#### INDEX_INITRANS (단위 : 개수)

##### 데이터 타입

Unsigned Integer

##### 기본값

8

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 30]

##### 설명

인덱스 페이지에 유지될 TTS(Touched Transaction Slots)의 초기 개수를 나타낸다.

#### INDEX_MAXTRANS (단위 : 개수)

##### 데이터 타입

Unsigned Integer

##### 기본값

30

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 30]

##### 설명

인덱스 페이지에 유지될 수 있는 TTS(Touched Transaction Slots)의 최대 개수를 나타낸다.

#### LFG_GROUP_COMMIT_INTERVAL_USEC (단위: 마이크로 초)

##### 데이타 타입

Unsigned Integer

##### 기본값

1000

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

본 프로퍼티는 그룹 커밋 관련 프로퍼티이다.

트랜잭션 커밋을 위해 로그를 디스크에 기록하는 디스크 I/O를 수행한 마지막 시각을 가지고 있다. 이 시각을 기준으로 이 프로퍼티가 지정한 시간이 지난 후에 로그를 디스크에 기록하는 디스크 I/O가 수행된다.

이를 통해, 여러 트랜잭션이 동시 다발적으로 커밋하면서 요청하는 디스크 I/O가 한꺼번에 수행된다.

#### LFG_GROUP_COMMIT_RETRY_USEC (단위: 마이크로 초)

##### 데이타 타입

Unsigned Integer

##### 기본값

100

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 60000000]

##### 설명

본 프로퍼티는 그룹커밋 관련 프로퍼티이다.

마지막으로 로그 기록을 위한 디스크 I/O를 수행한 시각 이후로 LFG_GROUP_COMMIT_INTERVAL_USEC 만큼의 시간이 지나지 않은 경우, 커밋을 하려는 트랜잭션은 사용자가 이 프로퍼티에 지정한 값 만큼 기다린 후 디스크 I/O를 수행할 수 있는 충분한 시간이 지났는지를 다시 체크한다.

#### LFG_GROUP_COMMIT_UPDATE_TX_COUNT

##### 데이타 타입

Unsigned Integer

##### 기본값

80

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

본 프로퍼티는 그룹커밋 관련 프로퍼티이다.

데이터베이스에 변경(UPDATE)을 가한 트랜잭션의 수(V$LFG의 UPDATE_TX_COUNT 칼럼에서 조회 가능)가 이 값보다 크거나 같은 값이 되면 그룹 커밋이 활성화된다. 만약 이 프로퍼티가 0으로 설정되면 그룹커밋은 작동하지 않는다.

#### LOB_CACHE_THRESHOLD (단위: bytes)

##### 데이터 타입

Unsigned Integer

##### 기본값

8192

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 524288]

##### 설명

클라이언트 LOB 캐시에 저장될 수 있는 LOB 데이터의 최대 크기를 지정하는 프로퍼티이다. 이 프로퍼티에 0보다 큰 값을 지정하면, 설정한 크기 이하의 LOB 데이터는 클라이언트에 임시로 저장된다. 0으로 설정하면 클라이언트에 LOB 데이터가 임시 저장되지 않는다.

이 프로퍼티를 이용해서 임계치를 적절히 조절하면, LOB 데이터가 클라이언트 LOB 캐시에 저장되어 Bulk-select 속도가 향상된다.

Altibase 운영 중 ALTER SYSTEM 또는 ALTER SESSION 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### LOCK_ESCALATION_MEMORY_SIZE(단위 : 바이트)

##### 데이타 타입

Unsigned Integer

##### 기본값

100M

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1000MB]

##### 설명

메모리 테이블에 대해 다량의 변경(UPDATE) 배치 작업을 할 때, 버전(versioning)으로 인해 메모리 사용량이 크게 증가하는 것을 방지하기 위한 프로퍼티이다. 어떤 DML에 의해 생성되는 로그의 크기가 이 프로퍼티에 설정된 값보다 커지면 버전을 만들지 않고 "inplace update6"를 하여 메모리 사용량이 증가하는 것을 막는다.

[6] inplace update란 변경 대상이 되는 원래 레코드에 대해 버전(version)을

만들지 않고 해당 칼럼의 값이 바로 수정되는 것을 의미한다.

변경시 버전 기법을 사용하면, 레코드 레벨의 X 잠금(lock)을 획득하고 테이블 레벨의 IX 잠금을 획득한다. 그러나 inplace update시에는 테이블 레벨에도 X 잠금 즉, 배타적 잠금을 획득한다. 따라서, 이 값을 너무 작게 설정하면 해당 테이블에 대한 확장성(scalability)이 떨어질 수 있으므로 유의해야 한다.

Altibase 운영 중 ALTER SYSTEM 문으로 이 프로퍼티의 값을 변경할 수 있다.

#### LOG_IO_TYPE

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

로그를 기록할 때의 I/O 모드를 나타낸다.

0: buffered I/O

1: direct I/O

#### LOG_CREATE_METHOD

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

로그 파일을 생성할 때 사용되는 시스템 콜을 선택하는 프로퍼티이다. awrite 유틸리티로 출력되는 값을 참고하여 선택적으로 사용하면 성능 향상에 도움이 된다. awrite 유틸리티에 대한 자세한 내용은 Utilities Manual을 참고한다.

0 : write() 시스템 콜

1: fallocate() 시스템 콜 ; 지원되는 운영 시스템에서만 사용이 가능함

#### LOW_FLUSH_PCT(단위 : 백분율)

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 100]

##### 설명

플러시 리스트의 길이가 전체 버퍼 크기에서 명시된 값 이상이 되면 교체 플러시를 수행한다. 이 때 해당 플러시 리스트의 모든 갱신 버퍼들은 플러시한다.

#### LOW_PREPARE_PCT (단위 : 백분율)

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 100]

##### 설명

플러셔가 대기에서 깨어났을 때 Prepare 리스트의 길이가 전체 버퍼에서 명시한 값 이하가 되면 교체 플러시를 수행한다. 이 때 해당 플러시 리스트의 모든 갱신 버퍼들은 플러시한다.

#### MATHEMATICS_TEMP_MEMORY_MAXIMUM (단위 : 바이트)

##### 데이터 타입

Unsigned Long

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 264-1]

##### 설명

시스템 전체에서 분석 함수가 사용하는 MATHEMATICS TEMP의 메모리 양을 제한한다. ( 분석 함수 : listagg, percentile_cont, percentile_disc, ... ) 사용한 메모리 양이 MATHEMATICS_TEMP_MEMORY_MAXIMUM과 같거나 크다면 에러가 발생한다. 속성 값이 0 인 경우에 메모리 사용량을 검사하지 않는다.

#### MAX_FLUSHER_WAIT_SEC (단위: 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

10

##### 속성

변경 가능, 단일 값

##### 값의 범위

[1, 232-1]

##### 설명

플러셔의 최대 대기 시간을 명시한다. 플러셔의 대기 시간은 작업 빈도에 따라 계속 늘어날 수 있지만, 이 값을 넘어가지는 못한다.

#### MEM_INDEX_KEY_REDISTRIBUTION

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

메모리 인덱스의 키를 재분배하는 프로퍼티이다.

이 프로퍼티는 역순의 인덱스 키가 다수 삽입될 때, 리프 노드의 분열이 많이 발생할 때, 데이터에 비해 인덱스 범위가 클 때 사용하면 효과적이다.

0: 메모리 인덱스의 키를 재분배하지 않는다.

1: 메모리 인덱스의 키를 재분배한다. (기본값)

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### MEM_INDEX_KEY_REDISTRIBUTION_STANDARD_RATE

##### 데이터 타입

Unsigned Integer

##### 기본값

50

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[10, 90]

##### 설명

메모리 인덱스의 키를 재분배하기 위해 이웃 노드의 미사용 공간 비율의 최소값을 설정한다. 예를 들어 이 프로퍼티 값이 30이면 리프 노드의 빈 공간이 최소 30%이상이 있을 때 메모리 인덱스의 키를 재분배한다.

MEM_INDEX_KEY_REDISTRIBUTION프로퍼티가 0이면 이 프로퍼티는 동작하지 않는다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### MULTIPLEXING_CHECK_INTERVAL(단위 : 마이크로 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

200000

##### 속성

변경 가능, 단일 값

##### 값의 범위

[100000, 10000000]

##### 설명

쓰레드 매니저가 서비스 쓰레드 분산을 위해 세션을 확인하는 주기를 나타낸다. 시간 단위는 마이크로초이다.

쓰레드 매니저는 주기적으로 세션의 상태를 확인하여 세션의 통계 정보를 갱신하며, 서비스 쓰레드를 추가 또는 삭제한다.

#### MULTIPLEXING_MAX_THREAD_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

1024

##### 속성

변경 가능, 단일 값

##### 값의 범위

[1, 1024]

##### 설명

멀티플렉싱을 하는 쓰레드의 최대 개수다.

기존에 존재하는 쓰레드들의 부하가 증가하면 쓰레드가 자동으로 증가한다. 그러나 쓰레드들이 계속 증가하게 되면 오히려 성능이 저하될수 있으므로 적절한 값을 설정해야 한다.

단 큐(QUEUE)를 사용하는 경우에는 이 프로퍼티에서 설정한 값보다 더 많은 쓰레드가 생성될수 있다.

#### MULTIPLEXING_THREAD_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

호스트 장비의 CPU 개수

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 1024]

##### 설명

Altibase가 유지하는 서비스 쓰레드의 최소 개수이다. 기본값은 장비의 CPU 개수이다.

이 값은 서버가 구동된 후에는 변경할 수 없다.

#### NORMALFORM_MAXIMUM

##### 데이터 타입

Unsigned Integer

##### 기본값

2048

##### 속성

변경 가능, 단일 값

##### 값의 범위

[1, 232-1]

##### 설명

조건절을 정규화할 때 정규화 형(Normal Form) 노드의 최대 개수를 지정할 수 있는 프로퍼티이다.

SELECT 질의문의 WHERE절에 존재하는 predicate들이 논리 연산자(AND, OR)로 복잡하게 연결되어 있을 때, Altibase는 테이블을 더 빠르게 탐색하기 위하여 predicate을 정규화시킨다.

정규화 방법으로 CNF(Conjunctive Normal Form)와 DNF(Disjunctive Normal Form)가 있으며, 이 프로퍼티에 명시한 노드 개수를 초과하면 해당 정규화 형으로 더 이상 정규화를 시도하지 않는다.

만약 두 가지 정규화 형이 명시한 노드 개수를 초과하면, 조건절을 정규화하지 않고 NNF(Not Normal Form)를 수행한다. NNF를 사용하면 조건절이 정규화되지 않아서 인덱스를 사용할 수 없다.

그러나 조건절을 지나치게 복잡하게 작성한 경우 NNF를 피하고자 이 프로퍼티의 값을 지나치게 크게 설정하면, 복잡한 조건절 처리를 위해 정규화 비용과 메모리 사용량이 증가한다.

따라서 조건절 작성시에 논리연산자를 지나친 사용을 자제하고 정규화 형태로 조건절을 작성하는 것이 중요하다.

이 규칙은 ON 조건 조인의 ON predicate에도 동일하게 적용된다.

#### OPTIMIZER_AUTO_STATS

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 10]

##### 설명

옵티마이저가 사용할 수 있는 통계 정보가 없을 때 자동으로 통계 정보를 수집하는 프로퍼티이다. 수집할 수 있는 Page개수는 1~10까지의 값에 따라 아래의 표와 같다. 0으로 설정하면 통계 정보를 자동으로 수집할 수 없다.

Altibase 운영 중 ALTER SESSION, SYSTEM 문을 이용하여 변경할 수 있다.

| 값        | PAGE 개수    | 통계 정보 수집 여부 |
| --------- | ------------ | :-----------------: |
| 0(기본값) | 0            |         OFF         |
| 1         | 32           |         ON          |
| 2         | 64           |         ON          |
| 3         | 128          |         ON          |
| 4         | 256          |         ON          |
| 5         | 512          |         ON          |
| 6         | 1024         |         ON          |
| 7         | 4096 (32M)   |         ON          |
| 8         | 16384 (128M) |         ON          |
| 9         | 65536 (512M) |         ON          |
| 10        | ALL          |         ON          |

#### OPTIMIZER_DELAYED_EXECUTION

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

실행 계획의 그래프를 기준으로 hierarchy, sorting, windowing, grouping, set, distinction의 실행(execute)을 패치(fetch)에서 수행시킨다. 사용자는 실행 계획에서 상위 PROJECTION 아래에 DELAY 플랜이 추가된 것을 확인할 수 있다.

이 프로퍼티는 쿼리 수행 시 실행(execute)을 지연시켜 첫 번째 패치(fetch)에서 수행하도록 하여, 실행 시간을 줄이고 첫 번째 패치 시간을 늘린다. 첫 번째 패치 이 후의 수행 시간은 동일하다. 관련된 수행 시간은 v$statement 성능 뷰로 확인 가능하다.

0 : disable (비활성화, 기본값)

1 : enable (활성화)

Altibase 운영 중 ALTER SESSION문을 이용하여 변경할 수 있다.

#### OPTIMIZER_FEATURE_ENABLE

##### 데이터 타입

String

##### 기본값

Altibase 서버 버전

##### 속성

변경 가능, 단일 값

##### 값의 범위

[6.1.1.0.6 | 6.1.1.0.7 | 6.3.1.0.1 | 6.5.1.0.0| 7.1.0.0.0]

##### 설명

쿼리 옵티마이저와 관련된 프로퍼티들을 일괄적으로 제어하는 프로퍼티이다.

이 프로퍼티는 값의 범위에 속하는 버전에 한해 ALTER SYSTEM문으로 변경할 수 있다.

```
e.g) ALTER SYSTEM SET optimizer_feature_enable = '6.1.1.0.6';
```

아래는 이 프로퍼티의 설정에 따라 쿼리 옵티마이저와 관련된 프로퍼티들이 어떤 값으로 설정되는지를 나타낸 표이다.

| OPTIMIZER_FEATURE_ENABLE              | 6.1.1.0.6 | 6.1.1.0.7 | 6.3.1.0.1 | 6.5.1.0.0 | 7.1.0.0.0 |
| ------------------------------------- | :-------: | :-------: | :-------: | :-------: | :-------: |
| QUERY_REWRITE_ENABLE                  |  0 (off)  |  0 (off)  |  0 (off)  |  0 (off)  |  0 (off)  |
| OPTIMIZER_UNNEST_SUBQUERY             |  0 (off)  |  0 (off)  |  1 (on)   |  1 (on)   |  1 (on)   |
| OPTIMIZER_UNNEST_COMPLEX_SUBQUERY     |  0 (off)  |  0 (off)  |  1 (on)   |  1 (on)   |  1 (on)   |
| OPTIMIZER_UNNEST_AGGREGATION_SUBQUERY |  0 (off)  |  0 (off)  |  0 (off)  |  1 (on)   |  1 (on)   |
| RESULT_CACHE_ENABLE                   |  0 (off)  |  0 (off)  |  0 (off)  |  0 (off)  |  0 (off)  |
| TOP_RESULT_CACHE_MODE                 |  0 (off)  |  0 (off)  |  0 (off)  |  0 (off)  |  0 (off)  |
| OPTIMIZER_AUTO_STATS                  |  0 (off)  |  0 (off)  |  0 (off)  |  0 (off)  |  0 (off)  |
| OPTIMIZER_PERFORMANCE_VIEW            |  0 (off)  |  0 (off)  |  0 (off)  |  0 (off)  |  1 (on)   |

#### OPTIMIZER_MODE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

이 프로퍼티 값이 0으로 설정되면 질의문을 최적화하기 위하여 비용 기반 최적화(cost-based optimization)가 사용되고, 1이면 규칙 기반 최적화(rule-based optimization)가 사용된다.

Altibase 운영 중 ALTER SYSTEM 문 또는 ALTER SESSION 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### OPTIMIZER_PERFORMANCE_VIEW

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

성능 뷰를 최적화하기 위하여 메모리 제약 여부를 설정하는 프로퍼티이다. Altibase 시스템 정보를 모니터링 할 때 내부적인 효율성 향상을 기대할 수 있다.

0: 적용 안함 - 메모리 제약이 없다.

1: 적용(기본값) - 메모리 제약이 있다. EXECUTE_STMT_MEMORY_MAXIMUM 프로퍼티의 값을 초과하면 쿼리 실행이 실패한다.

#### OPTIMIZER_UNNEST_AGGREGATION_SUBQUERY

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

SELECT 구문에 "GROUP BY절 없이 집계 함수만 사용한 중첩된 부질의(Nested Subquery)7"가 포함되어 있을 때, 쿼리 옵티마이저가 중첩 풀기(unnesting)를 할 것인지 여부를 지시하는 프로퍼티이다.

[7] 중첩된 부질의 (Nested Subquery): WHERE절에 포함된 부질의이다. 결과 집합을

한정하기 위해, 주로 메인 쿼리(Main Query, 외부 질의)에 있는 칼럼을 참조하는 형태를 가진다. 이렇게 중첩된 부질의가 포함된 쿼리를 중첩되지 않은 조인 형태의 쿼리로 변환하는 것을 "Subquery Unnesting"이라고 한다.

Altibase 운영 중 ALTER SYSTEM문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

0: unnesting을 시도하지 않는다.

1: unnesting을 시도한다.

#### OPTIMIZER_UNNEST_COMPLEX_SUBQUERY

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

SELECT 구문에 복잡한 형태의 중첩된 부질의(Nested Subquery)가 포함되어 있을 때, 쿼리 옵티마이저가 중첩 풀기(unnesting)를 할 것인지 여부를 지시하는 프로퍼티이다. 복잡한 형태란 FROM절에 뷰 또는 두 개 이상의 테이블이 있거나, 또는 SELECT, FROM, WHERE절 이외의 다른 절이 포함된 것을 말한다.

Altibase 운영 중 ALTER SYSTEM문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

0: unnesting을 시도하지 않는다.

1: unnesting을 시도한다.

#### OPTIMIZER_UNNEST_SUBQUERY

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

SELECT 구문에 "중첩된 부질의(Nested Subquery)"가 포함되어 있을 때, 쿼리 옵티마이저가 중첩 풀기(unnesting)를 할 것인지 여부를 지시하는 프로퍼티이다.

Altibase 운영 중 ALTER SYSTEM문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

0: unnesting을 시도하지 않는다.

1: unnesting을 시도한다.

#### OUTER_JOIN_OPERATOR_TRANSFORM_ENABLE

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

최적화된 쿼리의 실행 계획이 수행되도록, 사용자가 직접 ANSI/ISO SQL 표준 기법으로 Outer Join 연산을 수행하도록 설정할 수 있다.

이 값을 0으로 설정하면, ANSI/ISO SQL 표준 기법의 Outer Join 연산을 수행하며, 쿼리문에 Oracle Outer Join Operator (+)이 사용되었다면 에러가 발생한다. 기본값은 1이며, Oracle Outer Join Operator(+)를 사용한다.

0 : Disable

1 : Enable (기본값, Oracle Outer Join Operator 사용)

알티베이스 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### PARALLEL_LOAD_FACTOR

##### 데이터 타입

Unsigned Integer

##### 기본값

2N (N:논리 코어 개수)

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 512]

##### 설명

Altibase 서버 재가동 시 데이터베이스 정제 과정(database refining) 또는 인덱스 재구축(index rebuilding) 과정에서 생성되는 데이터베이스 정제 쓰레드/인덱스 구축 쓰레드 개수를 조절하는 프로퍼티이다.

주석으로 처리할 경우 기본값으로 시스템의 논리 코어 개수(N)의 두 배(2N)만큼 병렬 작업 쓰레드가 생성된다.

#### PARALLEL_QUERY_THREAD_MAX

##### 데이터 타입

Unsigned Integer

##### 기본값

CPU 개수

##### 속성

변경 가능, 단일 값

##### 값의 범위

[1, 1024]

##### 설명

Altibase 서버가 병렬 질의를 처리하기 위해 생성할 수 있는 최대한의 작업 쓰레드 개수를 명시한다. 이 프로퍼티를 명시하지 않을 경우 기본값은 시스템의 CPU 개수(N)로 설정된다.

Altibase 운영 중 ALTER SYSTEM문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### PARALLEL_QUERY_QUEUE_SIZE

##### 데이터 타입

Unsigned Integer

##### 기본값

1024

##### 속성

변경 가능 전용, 단일 값

##### 값의 범위

[4, 1048576]

##### 설명

Altibase 서버가 병렬 질의를 처리할 때, PARALLEL-QUEUE(PRLQ) 노드에서 데이터를 임시로 저장할 큐의 크기를 지정하는 프로퍼티이다.

Altibase 운영 중 ALTER SYSTEM문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### PREPARE_STMT_MEMORY_MAXIMUM(단위 : 바이트)

##### 데이터 타입

Unsigned Long

##### 기본값

100M

##### 속성

변경 가능, 단일 값

##### 값의 범위

[1024*1024, 264-1]

##### 설명

하나의 질의문(statement)이 사용할 수 있는 prepare 메모리의 양을 제한한다.

Altibase 운영 중 ALTER SYSTEM문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### QUERY_REWRITE_ENABLE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

Altibase 서버에서 쿼리 변환 시에 함수 기반 인덱스를 적용할지 여부를 지정하는 프로퍼티이다.

0: disable (미적용)

1: enable (적용)

#### REFINE_PAGE_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

50

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

Altibase 서버 가동 시 수행하는 단계 중 데이터베이스 정제(database refining) 단계가 있다. Altibase 서버가 이전 종료할 당시, 트랜잭션들이 생성한 버전 레코드(versioning record)들이 가비지 콜렉터에 의해 처리되지 못해서 불필요한 레코드들이 데이터베이스에 존재하고 있을 수 있으며 또한 서버 가동시의 회복 과정에서 생성된 버전 레코드들이 존재할 수 있다. 이들 레코드들을 재사용 가능하도록 처리하는 것이 데이터베이스 정제 단계이다.

데이터베이스 정제 대상이 되는 레코드들이 많을 경우 시간을 많이 소모할 수 있기 때문에 이 작업을 여러 쓰레드에 의해 병렬로 수행할 수 있다. 이 때 각 쓰레드가 처리하는 페이지 양을 지정한다.

#### RESULT_CACHE_ENABLE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

Result Cache를 사용하여 중간 결과의 실행계획을 저장할 지 여부를 설정한다.

0: Disabled (기본값) – 캐시기능을 사용하지 않는다.

1: Enabled – 캐시기능을 사용한다.

Altibase 운영 중 ALTER SYSTEM 또는 ALTER SESSION 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### RESULT_CACHE_MEMORY_MAXIMUM (단위:바이트)

##### 데이터 타입

Unsigned Long

##### 기본값

10M

##### 속성

변경 가능, 단일 값

##### 값의 범위

[4096, ULONG MAX]

##### 설명

Result Cache및 Top Result Cache를 사용할 때, 저장하는 메모리 크기를 제한한다. 만약 이 크기를 넘으면 메모리에 저장되지 않고 해제된다. 이 프로퍼티는 쿼리 1개에 대한 제약이며 시스템 전체에 대한 제약은 제공하지 않는다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### SECONDARY_BUFFER_ENABLE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

보조 버퍼(Secondary Buffer) 기능을 사용하려면, 이 프로퍼티의 값을 설정한 후 반드시 SECONDARY_BUFFER_FILE_DIRECTORY, SECONDARY_BUFFER_SIZE를 설정해야 서버가 구동된다.

보조 버퍼 기능을 사용하면 메모리 버퍼의 데이터 페이지를 디스크에 바로 플러시하지 않고 SSD(Solid-state Drive)의 보조 버퍼에 먼저 플러시한다. 그리고 Altibase 서버 내의 별도의 쓰레드가 보조 버퍼의 데이터 페이지를 디스크로 플러시한다.

0: 보조 버퍼 기능 비활성화

1: 보조 버퍼 기능 활성화

#### SECONDARY_BUFFER_FILE_DIRECTORY

##### 데이터 타입

String

##### 기본값

""

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

보조 버퍼 파일이 존재할 디렉토리의 경로를 지정한다. 파일 이름은 sbuffer.sbf로 고정되며, 변경할 수 없다. 이 프로퍼티를 설정하지 않으면 SECONDARY_BUFFER_ENABLE 프로퍼티가 1이더라도 보조 버퍼 기능이 비활성화된다.

보조 버퍼 기능에 대한 설명은 SECONDARY_BUFFER_ENABLE 프로퍼티의 설명을 참고하도록 한다.

#### SECONDARY_BUFFER_FLUSHER_CNT

##### 데이터 타입

Unsigned Integer

##### 기본값

2

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 16]

##### 설명

보조 버퍼의 데이터 페이지를 하드 디스크로 플러시하는 쓰레드(flusher)의 개수를 지정한다.

보조 버퍼 기능에 대한 설명은 SECONDARY_BUFFER_ENABLE 프로퍼티의 설명을 참고하도록 한다.

#### SECONDARY_BUFFER_SIZE (단위: 바이트)

##### 데이터 타입

Unsigned Long

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 32GB]

##### 설명

보조 버퍼 파일의 크기를 명시한다. 이 값이 0이면 SECONDARY_BUFFER_ENABLE 프로퍼티가 1이더라도 보조 버퍼 기능이 비활성화된다.

보조 버퍼 기능에 대한 설명은 SECONDARY_BUFFER_ENABLE 프로퍼티의 설명을 참고하도록 한다.

#### SECONDARY_BUFFER_TYPE

##### 데이터 타입

Unsigned Integer

##### 기본값

2

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2]

##### 설명

보조 버퍼에 저장할 데이터 페이지의 타입을 지정한다. 아래의 값 중 하나를 지정할 수 있다.

0: 모든 타입의 페이지

1: Dirty 페이지

2: Clean 페이지

보조 버퍼 기능에 대한 설명은 SECONDARY_BUFFER_ENABLE 프로퍼티의 설명을 참고하도록 한다.

#### SORT_AREA_SIZE(단위: 바이트)

##### 데이터 타입

Unsigned long

##### 기본값

1048576

##### 속성

변경 가능, 단일 값

##### 값의 범위

[512, 264-1]

##### 설명

서버가 정렬 작업을 위해 사용하는 임시 테이블 하나의 메모리 크기를 지정한다. 시스템 운영 중에는 ALTER SYSTEM 문을 이용해 프로퍼티의 값을 변경할 수 있다.

#### SQL_PLAN_CACHE_BUCKET_CNT

##### 데이터 타입

Unsigned Integer

##### 기본값

127

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[5, 4096]

##### 설명

SQL 플랜 캐시에서 해쉬 테이블의 버킷 개수를 나타낸다.

#### SQL_PLAN_CACHE_HOT_REGION_LRU_RATIO(단위 : 백분율)

##### 데이터 타입

Unsigned Integer

##### 기본값

50

##### 속성

변경 가능, 단일 값

##### 값의 범위

[10, 100]

##### 설명

SQL 플랜 캐시에 있는 LRU 리스트의 HOT 영역 비율을 나타낸다. HOT 영역 LRU 리스트는 SQL 플랜 캐시에 있는 LRU 리스트에서 빈번하게 참조되는 플랜들을 별도의 HOT 영역으로 저장한 것이다. 시스템 운영 중 ALTER SYSTEM 문을 이용해 프로퍼티의 값을 변경할 수 있다.

#### SQL_PLAN_CACHE_PREPARED_EXECUTION_CONTEXT_CNT

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1024]

##### 설명

플랜을 생성할 때 초기에 생성하는 execution context의 개수를 나타낸다.

플랜을 생성하기 전에 execution context의 개수를 지정하지만, 이는 초기에 생성하는 개수만을 결정할 뿐이다. 그리고 execution context는 실행 시간에 필요한 만큼 자동으로 증가되거나 감소된다.

그러나 하나의 플랜을 동시에 execute하는 경우 이 값을 증가시키는 것은 성능에 도움이 되지만, 그렇지 않은 경우에는 플랜의 크기만 증가시킬 뿐 성능 향상에 도움이 되지 않는다.

#### SQL_PLAN_CACHE_SIZE (단위: 바이트)

##### 데이터 타입

Unsigned long

##### 기본값

64 M

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 264-1]

##### 설명

SQL 플랜 캐시의 최대 크기를 나타낸다. 그러나 0으로 설정되면 캐시를 사용할 수 없게 된다. V$SQL_PLAN_CACHE의 MAX_CACHE_SIZE로 확인할 수 있다.

시스템 운영 중에는 ALTER SYSTEM 문을 이용해 프로퍼티의 값을 변경할 수 있다.

#### STATEMENT_LIST_PARTIAL_SCAN_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

V$STATEMENT, V$SQLTEXT, 또는 V$PLANTEXT 성능 뷰에 대한 SELECT 쿼리 결과로서 클라이언트에 반환할 statement의 최대 개수를 지정한다. 이 값이 0이면, 모든 statement에 대한 모든 레코드를 반환한다.

시스템 운영 중에는 ALTER SYSTEM 문을 이용해 프로퍼티의 값을 변경할 수 있다.

#### TABLE_INITRANS

##### 데이터 타입

Unsigned Integer

##### 기본값

2

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 120]

##### 설명

테이블 페이지에 유지될 TTS(Touched Transaction Slots)의 초기 개수를 나타낸다.

#### TABLE_LOCK_ENABLE

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

잠금(Lock) 수준을 제어하는 프로퍼티이다.

0: 테이블 잠금을 지원하지 않으며 레코드 잠금을 지원한다. 단순DML사용시에 성능이 향상된다.

1: 테이블 잠금과 레코드 잠금을 지원한다.

이 프로퍼티 값을 0으로 설정하면 다음과 같은 제약이 따른다.

- DDL문을 수행할 수 없다.
- CREATE DATABASE질의문을 수행할 수 없다.
- 이중화로 사용할 시에병렬 동기화 (parallel SYNC)를 사용할 수 없다.

이 프로퍼티는 ALTER SYSTEM 문으로 변경이 가능하다.

#### TABLE_LOCK_MODE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

테이블 파티션의 잠금(Lock) 수준을 설정하는 프로퍼티이다. TABLE_LOCK_ENABLE프로퍼티가 1인 경우에만 이 프로퍼티를 사용할 수 있다.

0: 테이블 파티션 단위의 잠금을 지원한다. 파티션 단위의 잠금을 사용하므로 ALTER TABLE…TRUNCATE PARTITION와 같이 파티션 단위로 수행되는 질의문 사용 시에 동시성이 향상된다.

1: 테이블 파티션의 잠금을 지원하지 않으며 파티션드 테이블의 논 파티션드 테이블 잠금과 동일하다. 잠금 횟수가 줄어들어 DML 성능이 향상된다.

#### TABLE_MAXTRANS

##### 데이터 타입

Unsigned Integer

##### 기본값

120

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 120]

##### 설명

테이블 페이지에 유지될 수 있는 TTS(Touched Transaction Slots)의 최대 개수를 나타낸다.

#### TABLESPACE_LOCK_ENABLE

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

테이블스페이스 잠금(lock) 레벨을 지정하는 프로퍼티이다.

1: 테이블스페이스 잠금을 지원한다.

0: 테이블스페이스 잠금을 지원하지 않는다. 이 경우 단순 DML 수행 시 처리 속도 향상의 이점이 있지만, 다음과 같은 제약이 있다.

- DDL문을 수행할 수 없다.
- CREATE DATABASE 구문을 수행할 수 없다.
- 이중화 시 병렬 동기화(Parallel Synchronization)를 허용하지 않는다.

Altibase 운영 중 ALTER SYSTEM 또는 ALTER SESSION문을 이용하여 이 프로퍼티의 값을 변경할 수 있다. 단, 활성화된 트랜잭션이 없을 경우에만 변경할 수 있다.

#### TEMP_STATS_WATCH_TIME

##### 데이터 타입

Unsigned Int

##### 기본값

10

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

통계 정보에 등록되는 기준 시간을 지정한다. 임시 테이블을 사용하는 연산 중 이 프로퍼티의 설정된 시간보다 오래 걸리는 연산은 통계정보로 등록된다. 임시 테이블에

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### THREAD_CPU_AFFINITY

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

서비스 쓰레드를 CPU와 연계할지 여부를 설정하는 프로퍼티이다. CPU 연계 기능을 활성화하면 하나의 서비스 쓰레드는 동일한 CPU 코어에만 할당될 것이다. 또한, 한 CPU 코어에서 다른 CPU 코어로 쓰레드 정보를 이동하는 비용이 줄어들 것이다.

- 0: CPU 연계 기능을 사용하지 않는다.
- 1: CPU 연계 기능을 사용한다.

하지만 HP-UX IA64 플랫폼에서는 CPU 연계 기능을 사용하는 경우에 로깅 병목이 발생할 수 있다. 따라서 HP-UX IA64 플랫폼에서는 이 프로퍼티의 값을 1로 설정(altibase.properties 파일에서)하여도 Altibase 서버는 CPU 연계 기능을 활성화하지 않는다.

#### THREAD_REUSE_ENABLE

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

Altibase 내부에서 사용하는 쓰레드를 재사용할 것인지 여부를 설정한다.

0: 쓰레드 재사용 불가

1: 쓰레드 재사용 가능(기본값)

쓰레드를 재사용하면, 메모리에 대기중인 쓰레드를 사용할 수 있어 쓰레드를 생성하는 비용을 줄일 수 있다.

#### TIMED_STATISTICS

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

Wait 발생시 대기 시간과 SQL 연산의 소요 시간을 측정할 것인지 여부를 설정한다. 이 프로퍼티를 측정하는 것으로 설정할 경우 성능이 떨어질 수 있다.

0: 측정하지 않음

1: 측정함

#### TIMER_RUNNING_LEVEL

##### 데이터 타입

Unsigned Integer

##### 기본값

플랫폼 별로 기본값이 아래와 같이 상이하다.

1 : 하위에 기술되지 않은 모든 플랫폼
2 : IBM-AIX
3 : x86-linux, Amd64-linux

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 3]

##### 설명

Wait event를 대기하는 시간과 SQL 연산에 소요되는 시간을 측정하는 방법을 설정한다.

1: 시간을 측정하는 쓰레드가 TIMER_THREAD_RESOLUTION에서 지정한 규칙적인 간격으로 시간을 측정한다.

2: 플랫폼 별로 지원하는 라이브러리 함수를 이용하여 측정한다.

3: 1번과 비슷하지만 시스템 시계(clock)를 이용하여 측정한다. 따라서 다른 방법에 비해 성능 저하가 낮다.

LINUX, PA-RISC-HP-64 이외의 장비에서 이 값을 3으로 설정할 경우, 시간을 제대로 측정하지 못하여 Altibase 서버가 기동이 안 될 수도 있다. 이 경우 Altibase는 altibase_boot.log에 경고 메시지를 남기고, 자동으로 이 프로퍼티의 값을 기본값으로 변경한 후 기동한다. 기본값이 1인 장비에서는 아래와 같은 메시지가 altibase_boot.log에 기록될 것이다.

[Warning] Because a TIMER_RUNNING_LEVEL of 3 is not supported on this platform, it has been set to the default(=1) for this platform.

#### TIMER_THREAD_RESOLUTION (단위: 마이크로초)

##### 데이터 타입

Unsigned Integer

##### 기본값

1000

##### 속성

변경 가능, 단일 값

##### 값의 범위

[50, 10000000]

##### 설명

TIMER_RUNNING_LEVEL을 1로 설정한 경우 이 프로퍼티는 시간을 측정하는 주기를 의미한다.

#### TOP_RESULT_CACHE_MODE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 3]

##### 설명

Top Result Cache를 사용하여 최종 결과의 실행계획을 저장할 지 여부를 설정한다.

0: Disabled (기본값) – Top Result Cache기능을 사용하지 않는다.

1: MEMORY - 메모리 테이블만 사용한 쿼리의 최종결과를 캐시한다

2: DISK – 디스크 테이블만 사용한 쿼리의 최종결과를 캐시한다

3: ALL – 테이블 타입과 상관없이 최종 결과를 캐시한다.

Altibase 운영 중 ALTER SYSTEM 또는 ALTER SESSION 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### TOTAL_WA_SIZE (단위: 바이트)

##### 데이터 타입

Unsigned Long

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 264-1]

##### 설명

정렬 또는 해싱 작업을 위해 할당할 수 있는 메모리의 최대 크기를 지정한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### INIT_TOTAL_WA_SIZE (단위: 바이트)

##### 데이터 타입

Unsigned Long

##### 기본값

264-1

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 264-1]

##### 설명

정렬 또는 해싱 작업을 위해 미리 할당 할 메모리의 크기를 지정한다.

TOTAL_WA_SIZE 보다 더 클 경우 TOTAL_WA_SIZE 까지만 생성한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### TOUCH_TIME_INTERVAL (단위: 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

3

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 100]

##### 설명

버퍼의 접근 횟수를 증가시키기 위한 최소 시간 간격을 의미한다. 버퍼에 대해 마지막으로 접근한 이후 이 프로퍼티에서 명시한 시간이 지나면, 접근 횟수가 증가한다.

이 값이 기본값 3으로 명시되면, 특정 버퍼의 마지막 접근 이후 3초 이내의 접근에 대해서는 접근 횟수를 갱신하지 않는다.

#### TRANSACTION_SEGMENT_COUNT (단위 : 개수)

##### 데이터 타입

Unsigned Integer

##### 기본값

256

##### 속성

변경 가능, 단일 값

##### 값의 범위

[1, 512]

##### 설명

서버 구동시 생성되는 트랜잭션 세그먼트(언두 세그먼트와 TSS 세그먼트)의 개수를 나타낸다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### TRX_UPDATE_MAX_LOGSIZE (단위 : 바이트)

##### 데이타 타입

Unsigned Integer

##### 기본값

10 MB

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 264-1]

##### 설명

하나의 DML에 의해 생성되는 로그의 누적 크기가 이 프로퍼티에 설정된 값보다 커지면 해당 트랜잭션을 중단하고 오류를 반환한다.

사용자의 부주의로 대용량 배치 작업이 실행되어 시스템에 부하가 발생하는 것을 방지하기 위해 사용하는 프로퍼티이다.

해당 프로퍼티의 값을 0으로 설정하면 로그 크기에 대한 제한이 없어지기 때문에, 트랜잭션을 갱신할 때 발생하는 로그를 무한대로 사용할 수 있다. Altibase 운영 중 ALTER SYSTEM 문 또는 ALTER SESSION 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### SERIAL_EXECUTE_MODE

##### 데이타 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

이 프로퍼티는 SCAN PLAN내 FILTER를 최적하화여 FILTER 수행 성능을 향상시킨다. 이때 단순한 FILTER에 한하여 최적화하며, 최적화 여부는 PLAN TREE에서 확인할 수 있다.

0: 최적화지 않음

1: 최적화함

<details class="details-reset details-overlay details-overlay-dark" id="jumpto-line-details-dialog" style="box-sizing: border-box; display: block;"><summary data-hotkey="l" aria-label="Jump to line" role="button" style="box-sizing: border-box; display: list-item; cursor: pointer; list-style: none;"></summary></details>

## 2.Altibase 프로퍼티

### 세션 관련 프로퍼티

Altibase는 클라이언트-서버 구조로 사용 가능하며 세션 연결 프로퍼티는 클라이언트와 서버의 통신에 관한 프로퍼티를 규정하는 것이다. 다음과 같은 프로퍼티들이 있다.

#### CM_DISCONN_DETECT_TIME (단위: 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

3

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 232-1]

##### 설명

세션 관리 쓰레드의 동작 주기를 설정하기 위한 프로퍼티이다. Altibase 서버에는 클라이언트와 서버의 연결이 단절되었는지 검사하기 위해 세션 관리 쓰레드가 존재한다.

일반적으로 클라이언트 프로세스가 비정상 종료하면 그 클라이언트와 연결된 세션은 곧바로 그 상태를 감지할 수 있다.

그러나 세션에서 수행 중인 작업이 세션 작업과는 무관한 Altibase 서버 내부의 작업이면서 오랜 시간을 요구하는 작업이라면, 해당 세션은 클라이언트 비정상 종료 여부를 확인할 수 없다. 즉 클라이언트와 연결이 종료되었는지를 해당 세션에서는 확인할 수 없기 때문에 클라이언트가 비정상 종료되었음에도 불구하고 Altibase 서버는 그 작업을 계속 진행하게 된다.

위와 같은 경우 그러한 세션을 감지하여 해당 트랜잭션들을 롤백시킬 필요가 있으며 이를 위해 세션 관리 쓰레드가 주기적으로 세션들의 상태를 검사하게 된다.

#### CONCURRENT_EXEC_DEGREE_DEFAULT

##### 데이터 타입

Unsigned Integer

##### 기본값

4

##### 속성

변경 가능, 단일 값

##### 값의 범위

[2, 1024]

##### 설명

각 세션에서 DBMS_CONCURRENT_EXEC 패키지를 이용하여 동시에 실행시킬 수 있는 프로시저 개수를 설정한다. 만약 사용자가 저장 패키지의 INITIALIZE 함수로 병렬 처리할 프로시저의 개수를 지정하지 않으면, 이 프로퍼티의 값이 적용된다.

그러나 Altibase서버에서 저장 패키지를 이용하여 수행될 수 있는 프로시저의 개수는 CONCURRENT_EXEC_DEGREE_MAX 프로퍼티의 값보다 클 수 없다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### CONCURRENT_EXEC_DEGREE_MAX

##### 데이터 타입

Unsigned Integer

##### 기본값

CPU 개수

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1024]

##### 설명

Altibase서버에서 DBMS_CONCURRENT_EXEC 패키지를 이용하여 실행시킬 수 있는 병렬 프로시저의 최대 개수를 설정한다.

이 프로퍼티의 값을 0으로 설정한 경우 DBMS_CONCURRENT_EXEC 패키지가 동작하지 않는다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 없다.

#### CONCURRENT_EXEC_WAIT_INTERVAL

##### 데이터 타입

Unsigned Integer

##### 기본값

100

##### 속성

변경 가능, 단일 값

##### 값의 범위

[10, 1000000]

##### 설명

DBMS_CONCURRENT_EXEC 패키지에서 요청한 프로시저가 정상적으로 동작하는지 여부를 검사하는 간격을 설정한다.

이 프로퍼티의 값은 DBMS_CONCURRENT_EXEC 패키지에서 REQUEST 함수와 WAIT_REQ 함수에 영향을 준다. 이 함수들은 패키지를 이용하여 요청된 프로시저의 작업이 완료될 때까지 기다리기 때문이다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### DEFAULT_THREAD_STACK_SIZE(단위 : 바이트)

##### 데이터 타입

Unsigned Integer

##### 기본값

10485760 (10MB)

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1048576, 134217728]

##### 설명

모든 쓰레드의 스택 사이즈를 지정한다.

#### IPC_CHANNEL_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 65535]

##### 설명

클라이언트와 서버 사이에 IPC 통신을 하기 위하여 반드시 설정되어야 하는 프로퍼티이다. IPC를 이용한 클라이언트와 서버 통신 채널의 최대 개수를 지정한다. 각 채널 수에 비례해서 공유 메모리와 세마포어를 할당받기 때문에 서버에 동시에 연결할 수 있는 최대 IPC 연결 개수를 설정하는 것은 중요하다.

#### IPC_FILEPATH

##### 데이터 타입

String

##### 기본값

$ALTIBASE_HOME/trc/cm-ipc

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

Altibase 서버가 유닉스 환경에서 IPC 방식으로 클라이언트와 연결하기 위해 생성하는 소켓 파일이다.

서버를 구동하면 $ALTIBASE_HOME/trc 디렉토리 아래에 cm-ipc로 소켓 파일이 생성되며, 이 파일은 삭제되지 않도록 주의해야 한다.

#### IPCDA_CHANNEL_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 65535]

##### 설명

클라이언트와 서버 사이에 IPCDA 통신을 하기 위하여 반드시 설정되어야 하는 프로퍼티이다.

IPCDA를 이용한 클라이언트와 서버간 통신 채널의 최대 개수를 지정한다. 채널 개수에 비례하여 공유 메모리와 세마포어를 할당받기 때문에 서버에 동시에 연결할 수 있는 최대 IPCDA 연결 개수를 설정하는 것이 중요하다. IPCDA의 채널 개수는 CPU 코어 개수의 1/2 값이 최적화된 값이다.

#### IPCDA_DATABLOCK_SIZE (단위: 킬로 바이트)

##### 데이터 타입

Unsigned Integer

##### 기본값

20480

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[32, 102400]

##### 설명

IPCDA를 이용하는 통신 채널 한 개의 공유 메모리의 크기를 설정하는 프로퍼티이다. 이 값을 1000으로 하고, IPCDA_CHANNEL_COUNT를 24로 하는 경우 서버에서 통신 채널로 사용되는 전체 메모리의 크기(IPCDA_CHANNEL_COUNT * IPCDA_DATABLOCK_SIZE)는 1000KB * 24 = 24000KB가 된다.

이 값은 시스템 메모리의 크기에 따라 공유 메모리를 사용하는 다른 프로그램의 운영에 장애가 되지 않도록 적절한 값을 설정해야 한다. 예를 들어 사용자의 시스템 메모리가 4GB인 시스템에서는 IPCDA_CHANNEL_COUNT를 24로 할 경우, IPCDA_DATABLOCK_SIZE는 최댓값으로 하여도, 실제 사용 메모리는 2457600KB를 사용하기 때문에 최댓값으로 설정할 수 있다.

#### IPCDA_FILEPATH

##### 데이터 타입

String

##### 기본값

$ALTIBASE_HOME/trc/cm-ipcda

##### 속성

읽기 전용, 다중 값

##### 값의 범위

없음

##### 설명

Altibase 서버가 유닉스 환경에서 IPCDA 방식으로 클라이언트와 연결하기 위해 생성하는 소켓 파일이다.

서버를 구동하면 $ALTIBASE_HOME/trc 디렉토리 아래에 cm-ipcda로 소켓 파일이 생성되며, 이 파일은 삭제되지 않도록 주의해야 한다.

#### MAX_LISTEN

##### 데이터 타입

Unsigned Integer

##### 기본값

128

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 16384]

##### 설명

클라이언트와 Altibase 간의 통신 시 TCP/IP 또는 UNIX DOMAIN 소켓을 사용하는 경우 대기 큐(listen queue)의 크기를 지정하는 값이다.

#### MAX_STATEMENTS_PER_SESSION

##### 데이터 타입

Unsigned Integer

##### 기본값

1024

##### 속성

변경 가능, 단일 값

##### 값의 범위

[1, 65535]

##### 설명

한 세션에서 실행 가능한 statement의 최대 개수를 지정한다.

Altibase 운영 중 ALTER SYSTEM 또는 ALTER SESSION 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### NET_CONN_IP_STACK

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1, 2]

##### 설명

클라이언트 서버간의 TCP/IP통신을 위해서 서버 측에 소켓을 생성할 때 사용하는 인터넷 프로토콜 스택을 지정한다.

0: IPv4만을 지원하는 인터넷 프로토콜 스택을 사용하게 된다.

1: 듀얼 스택 (IPv4와 IPv6 모두 지원하는 인터넷 프로토콜 스택)이 사용된다.

2: IPv6만을 지원하는 인터넷 프로토콜 스택을 사용하게 된다.

#### NLS_COMP

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

데이터베이스 생성시 지정된 캐릭터셋(character set)의 캐릭터들의 순서는 해당 국가에서 사용되는 사전과 그 이진 값의 순서가 동일하다고 보장할 수 없다.

이 프로퍼티의 값이 1로 설정되면, 각 캐릭터셋을 해당 언어의 사전 순서대로 비교한다. 현재 한국어에 대해서만 지원하기 때문에, 데이터베이스 캐릭터셋이 한글(KSC5601 완성형 또는 MS확장 완성형)로 설정됐을 때에만 지원한다.

#### NLS_CURRENCY

##### 데이터 타입

String

##### 기본값

NLS_TERRITORY의 값을 따른다.

##### 속성

변경 가능, 단일 값

##### 값의 범위

최대 10바이트 길이의 문자

##### 설명

지역 통화 기호를 지정하는 프로퍼티이다. 숫자형 데이터 형식 L을 통해 지역 통화 기호를 표시할 때 이 프로퍼티의 값이 사용된다. 이 프로퍼티의 값은 +, -, <, > 기호로 시작할 수 없다.

Altibase 운영 중 아래와 같이 ALTER SESSION문을 이용하여 이 프로퍼티의 값을 변경할 수 있다:

```
ALTER SESSION SET NLS_CURRENCY = '$';
```

> 주의: 아랍권의 통화 기호가 정확히 표시되려면 클라이언트 응용 프로그램(또는 쉘이나 에디터)이 아랍 문자의 표시를 지원해야 한다.

#### NLS_ISO_CURRENCY

##### 데이터 타입

String

##### 기본값

NLS_TERRITORY의 값을 따른다.

##### 속성

변경 가능, 단일 값

##### 값의 범위

V$NLS_TERRITORY 성능 뷰에 존재하는 값

##### 설명

ISO 통화 기호를 지정하는 프로퍼티이다. 숫자형 데이터 형식 C를 통해 국제 통화 기호를 표시할 때 이 프로퍼티의 값이 사용된다. 이 프로퍼티에 지정할 수 있는 값은 V$NLS_TERRITORY 성능 뷰에 존재하는 값(지역)에 한정된다.

Altibase 운영 중 아래와 같이 ALTER SESSION문을 이용하여 이 프로퍼티의 값을 변경할 수 있다:

```
ALTER SESSION SET NLS_ISO_CURRENCY = America;
```

#### NLS_NCHAR_CONV_EXCP

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

NCHAR 데이터 타입의 데이터를 다른 캐릭터셋으로 변환 시, 데이터 손실이 발생할 수 있다. 이 때 에러를 발생시킬 것인지 아니면 데이터 손실이 발생한 채로 변환을 할 것인지를 결정하는 프로퍼티이다.

이 프로퍼티는 서버에서 NCHAR타입 데이터를 다른 캐릭터셋으로 변환할 때에만 에러를 발생시킨다.

Altibase 운영 중 ALTER SESSION 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

0: FALSE (에러를 발생시키지 않는다.)

1: TRUE

#### NLS_NCHAR_LITERAL_REPLACE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

기본적으로 클라이언트는 쿼리 문 전체를 데이터베이스 문자 셋으로 변환하여 전송한다. 그러나, 특정 리터럴에 대해 이런 동작을 막으려면, 이 프로퍼티의 값을 1로 설정하고 그 리터럴 앞에 "N" 문자를 덧붙이면 된다. 즉, NCHAR 리터럴로 만드는 것이다.

이 프로퍼티의 값이 1일 때, 클라이언트는 쿼리 문 내의 모든 리터럴 앞에 "N" 문자가 있는지 찾는다. 만약 찾게 되면 클라이언트는 그 리터럴을 데이터베이스 문자 셋으로 변환하지 않고 그대로 전송하며 서버가 직접 내셔널 문자 셋으로 변환한다. 이것은 데이터베이스 문자 셋과는 다른 인코딩이 필요한 NCHAR 타입 데이터를 사용하고자 할 때 유용하다.

Altibase 운영 중 ALTER SESSION 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

0: "N" 문자가 있는지 검사하지 않고 쿼리 문 전체를 데이터베이스 문자 셋으로 변환한다.

1: "N" 문자가 붙어있는 NCHAR 리터럴은 데이터베이스 문자 셋으로 변환하지 않는다.

> 주의: 이 값을 1로 설정하는 것은 클라이언트의 비용이 크게 발생하므로, 사용시 주의가 필요하다.

#### NLS_NUMERIC_CHARACTERS

##### 데이터 타입

String

##### 기본값

NLS_TERRITORY의 값을 따른다.

##### 속성

변경 가능, 단일 값

##### 값의 범위

없음

##### 설명

소수점 문자와 그룹 구분자를 지정하는 프로퍼티이다. 그룹 구분자는 숫자에서 천단위로 구분해서 표기할 때 사용되며 일반적으로 쉼표(,)가 사용된다. 소수점 문자는 일반적으로 마침표(.)가 사용된다. 이 프로퍼티는 +, -, <, > 기호로 시작할 수 없다.

이 프로퍼티에 지정한 문자열에서 처음 두 개의 문자만 각각 소수점 문자와 그룹 구분자로 설정되고 나머지 문자는 무시된다.

Altibase 운영 중 아래와 같이 ALTER SESSION문을 이용하여 이 프로퍼티의 값을 변경할 수 있다:

```
ALTER SESSION SET NLS_NUMERIC_CHARACTERS='.,';
```

#### NLS_TERRITORY

##### 데이터 타입

String

##### 기본값

KOREA

##### 속성

변경 가능, 단일 값

##### 값의 범위

V$NLS_TERRITORY 성능 뷰에 존재하는 값

##### 설명

지역의 이름을 지정하는 프로퍼티이다. 이 프로퍼티에 지정한 지역에 따라 NLS_NUMERIC_CHARACTER, NLS_CURRENCY, 및 NLS_ISO_CURRENCY 프로퍼티의 값이 자동으로 변경된다. V$NLS_TERRITORY 성능 뷰를 조회해서 이 프로퍼티에 지정 가능한 지역의 이름을 확인할 수 있다.

Altibase 운영 중 아래와 같이 ALTER SESSION문을 이용하여 이 프로퍼티의 값을 변경할 수 있다. 지역의 이름은 대소문자를 구분하지 않으며, 작은 따옴표(')를 사용할 수 있다.

```
ALTER SESSION SET NLS_TERRITORY = America;
or
ALTER SESSION SET NLS_TERRITORY = 'America';
```

#### PORT_NO

##### 데이터 타입

Unsigned Integer

##### 기본값

20300

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1024, 65535]

##### 설명

TCP/IP로 클라이언트와 서버가 통신할 때 사용하는 포트 번호이다. 사용자는 루트 영역(일반적으로 1023번까지)을 제외한 나머지 영역(최대 65535)에 대해 다른 프로그램에서 사용하지 않는 번호면 임의로 지정할 수 있다. Altibase 응용 프로그램은 이 포트 번호를 사용하여 서버와 연결할 수 있다.

#### PSM_CURSOR_OPEN_LIMIT

##### 데이터 타입

Unsigned Integer

##### 기본값

32

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1,1024]

##### 설명

세션에서 DBMS_SQL 패키지를 사용하여 열 수 있는 커서의 개수를 지정한다.

#### PSM_FILE_OPEN_LIMIT

##### 데이터 타입

Unsigned Integer

##### 기본값

16

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0,128]

##### 설명

세션당 최대로 열 수 있는 저장 프로시저 파일 핸들의 개수를 지정한다.

#### TIME_ZONE

##### 데이터 타입

String

##### 기본값

OS_TZ

##### 속성

변경 가능, 단일 값

##### 값의 범위

V$TIME_ZONE_NAMES 성능 뷰에 존재하는 값

##### 설명

타임 존을 설정하는 프로퍼티이다. 해당되는 지역 이름이나 약어 또는 UTC 오프셋(예. +09:00)과 같은 문자열로 지정할 수 있다.

Altibase 운영 중 ALTER SESSION 문을 이용하여 해당 세션의 타임 존을 변경할 수 있다.

#### UNIXDOMAIN_FILEPATH

##### 데이터 타입

String

##### 기본값

$ALTIBASE_HOME/trc/cm-unix

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

Altibase 서버가 유닉스 도메인 방식으로 클라이언트와 연결하기 위해 생성하는 소켓 파일이다.

서버를 구동하면 $ALTIBASE_HOME/trc 디렉토리 아래에 cm-unix로 기본 소켓 파일이 생성되며, 이 파일은 삭제되지 않도록 주의해야 한다.

#### USE_MEMORY_POOL

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0,1]

##### 설명

메모리 풀링 기능의 사용 유무를 지정한다. 메모리 풀링이란 서버에서 메모리를 미리 할당하여 사용하는 기능이다.

이 기능을 사용하면, 메모리를 미리 할당하기 때문에 메모리 사용량이 많아진다.

0: 사용하지 않음

1: 사용

#### USER_LOCK_POOL_INIT_SIZE(단위 : 개수)

##### 데이터 타입

Unsigned Integer

##### 기본값

128

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[128, 10000]

##### 설명

데이터베이스에서 사용자 잠금(User Lock)을 사용할 수 있는 개수를 설정할 수 있다.

이 프로퍼티의 값을 초과하여 사용자 잠금의 개수를 사용할 수 있으나, 성능 저하가 발생할 수 있다. 또한 한 번 생성된 사용자 잠금을 해제하여도 제거되는 것은 아니므로, 해제된 사용자 잠금을 재사용하는 것이 효과적이다.

#### USER_LOCK_REQUEST_CHECK_INTERVAL(단위 : 마이크로 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

10000

##### 속성

변경 가능, 단일 값

##### 값의 범위

[10, 999999]

##### 설명

다른 세션이 사용자 잠금(User Lock)을 획득할 수 있는지 검사하는 주기를 설정한다. 다른 세션에서 현재 사용중인 사용자 잠금을 요청하면, 사용자 잠금이 해제되기 전까지 세션이 대기한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### USER_LOCK_REQUEST_LIMIT(단위 : 개수)

##### 데이터 타입

Unsigned Integer

##### 기본값

10

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 10000]

##### 설명

하나의 세션이 요청할 수 있는 사용자 잠금(User Lock)의 개수를 설정한다. Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### USER_LOCK_REQUEST_TIMEOUT(단위 : 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

10

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

세션에서 사용자 잠금(User Lock)을 요청한 후 획득할 때까지 대기하는 최대 시간을 설정한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### XA_HEURISTIC_COMPLETE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2]

##### 설명

PREPARE 상태(IN_DOUBT 상태)인 전역 트랜잭션을 일정 시간이 지나면 임의로 종료시킬 수 있는 프로퍼티이다. 이 때 COMMIT으로 종료시킬 것인지, ROLLBACK으로 종료시킬 것인지를 선택할 수 있으며, 트랜잭션을 종료시킬 때 명령을 기다리는 시간은 XA_INDOUBT_TX_TIMEOUT 프로퍼티에 정의된 값을 사용한다.

0: 종료하지 않음.

1: 트랜잭션 커밋

2: 트랜잭션 롤백

분산 트랜잭션 환경에서는 2 단계 커밋 프로토콜(2 Phase Commit Protocol, XA)을 사용하여 트랜잭션을 수행한다. 트랜잭션을 수행중에 전역(global) 트랜잭션 관리자(Coordinator)로부터 PREPARE 명령을 받은 후 COMMIT이나 ROLLBACK 명령을 받지 못한 상태가 오래 지속될 경우, 데이터베이스 성능에 영향을 줄 수 있다.

### 타임아웃 관련 프로퍼티

#### BLOCK_ALL_TX_TIME_OUT (단위: 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

3

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

버퍼 매니저가 해쉬 테이블의 크기를 조정할 때 트랜잭션의 접근을 제한할 수 있다. 이 프로퍼티의 최소값 0은 대기하지 않고 즉시 오류 처리됨을 의미한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### DDL_LOCK_TIMEOUT (단위 : 초)

##### 데이터 타입

Short integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[-1, 65535]

##### 설명

DDL 문을 수행할 때 해당 테이블에 이미 다른 트랜잭션에 의해 잠금(Lock)이 획득되어 있는 경우 잠금을 대기하는 옵션을 설정하는 것이다. 잠금을 요구하여 곧바로 획득되지 않을 경우 이 프로퍼티의 값이 –1로 설정되어 있으면 무한정 대기하고 양수로 설정되어 있으면 지정된 값 만큼 대기하고 다시 시도한다.

기본값은 0으로, DDL 수행시 잠금을 요구한 시점에서 잠금을 획득할 수 없는 경우 해당 DDL은 즉시 오류 처리된다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### DDL_TIMEOUT(단위 : 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

DDL 문의 실행 시간이 이 프로퍼티에 설정한 시간(초)을 초과하면, 그 구문의 실행은 취소된다. 기본 설정 값은 0으로, Altibase는 DDL 구문 수행이 끝날 때까지 무한 대기한다.

이 프로퍼티의 값은 Altibase 실행 중에 ALTER SYSTEM 또는 ALTER SESSION 구문으로 변경 가능하다.

> Note: Altibase 버전 5.5.1 까지는, DDL구문의 실행 시간도 UTRANS_TIMEOUT 과 QUERY_TIMEOUT 프로퍼티의 영향을 받았다. DML과 DCL구문의 실행시간은 여전히 UTRANS_TIMEOUT 과 QUERY_TIMEOUT 프로퍼티의 영향을 받는다.

#### FETCH_TIMEOUT(단위 : 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

60

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

응용 프로그램에서 SELECT 문을 수행하는 시간이 길어짐에 따라 데이터베이스 메모리가 비정상적으로 증가하는 것을 막기 위하여 이 값을 설정한다. 질의 수행 시간이 프로퍼티 파일에 설정된 값보다 커지면 세션 연결을 해제하고 현재 트랜잭션을 철회한다.

Altibase 운영 중 ALTER SYSTEM 문 또는 ALTER SESSION 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### IDLE_TIMEOUT (단위 : 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

서버에 접속된 클라이언트가 비정상적으로 오랜 시간 연결을 맺고 있고, 만약 이러한 클라이언트의 수가 점차적으로 많아진다면 결국에는 서비스를 할 수 있는 연결 개수가 현저히 작아져, 나중에는 서비스가 불가능한 상황이 될 수 있다.

이러한 현상을 미리 방지하기 위해 이 값을 설정한다. 한 세션의 유휴 시간이 프로퍼티 파일에 설정된 값보다 커지면 세션 연결을 해제하고 현재 트랜잭션을 철회한다.

Altibase 운영 중 ALTER SYSTEM 문 또는 ALTER SESSION 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### LOGIN_TIMEOUT(단위 : 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

Altibase의 포트로 접속이 이루어진 후 인증 절차가 완료될 때까지 허용된 시간이다. 이 시간 안에 인증이 이루어지지 않으면 서버는 접속을 끊는다.

#### MULTIPLEXING_POLL_TIMEOUT(단위 : 마이크로 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

10000

##### 속성

변경 가능, 단일 값

##### 값의 범위

[1000, 1000000]

##### 설명

멀티플렉싱을 하는 서비스 쓰레드가 세션을 감지하는 주기를 나타낸다.

#### QUERY_TIMEOUT (단위 : 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

600

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

특정 질의들(정렬 혹은 긴 조인 등)의 수행 시간이 길어짐에 따라 데이터베이스 메모리가 비정상적으로 증가하는 것을 막기 위하여 이 값을 설정한다. 질의 수행 시간이 프로퍼티 파일에 설정된 값보다 커지면 현재 트랜잭션 연산을 부분 철회한다.

Altibase 운영 중 ALTER SYSTEM 문 또는 ALTER SESSION 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### SHUTDOWN_IMMEDIATE_TIMEOUT

##### 데이터 타입

Unsigned Integer

##### 기본값

60

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

IMMEDIATE 옵션으로 Altibase 서버를 종료할 때, 끝나지 않은 트랜잭션들은 롤백 처리된다. 이 프로퍼티는 트랜잭션을 롤백하기 위해 대기하는 시간을 지정한다. 이 시간을 초과하게 되면, 종료되지 않은 트랜잭션이 롤백되지 않은 채로 서버는 강제 종료된다. 이 값이 0이면, 모든 트랜잭션이 롤백될 때까지 대기한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### UTRANS_TIMEOUT (단위 : 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

3600

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

변경 연산(UPDATE, INSERT, DELETE)을 수행하는 트랜잭션의 수행 시간이 길어짐에 따라 로그 파일의 개수가 비정상적으로 증가하는 것을 막기 위하여 이 값을 설정한다. 수행 시간이 프로퍼티 파일에 설정된 값보다 커지면 세션 연결을 해제하고 현재 트랜잭션을 철회한다.

Altibase 운영 중 ALTER SYSTEM 문 또는 ALTER SESSION 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### XA_INDOUBT_TX_TIMEOUT (단위: 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

60

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

2 단계 커밋 프로토콜에서 IN-DOUBT 상태의 오래 실행되는 전역 트랜잭션을 임의로 종료시키는 시간 기준에 대한 프로퍼티이다.

### 트랜잭션 관련 프로퍼티

#### AUTO_COMMIT

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

세션에서 SQL 문을 수행할 때 하나의 SQL 문을 하나의 트랜잭션으로 처리하여 커밋할 것인지를 결정하는 프로퍼티이다. 이 값이 1 이면 auto-commit 모드이고 0 이면 non-autocommit 모드이다. non-autocommit 모드인 경우 응용 프로그램에서 트랜잭션의 시작과 끝을 명시적으로 알려주어야 한다.

세션 단위로 이를 설정할 수 있는데, 서버 구동 시 AUTO_COMMIT의 값이 1일지라도 세션 별로 이 모드를 변경할 수 있다. 예를 들어, 클라이언트에서 ALTER SESSION SET AUTOCOMMIT = FALSE (non-autocommit)를 실행하면 이 세션은 이 후에 발생하는 트랜잭션을 반영할 것인지 또는 롤백할 것인지를 사용자가 명시해 주어야 한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### ISOLATION_LEVEL

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2]

##### 설명

트랜잭션의 고립화 수준(isolation level)을 지정한다. 고립화 수준에 따라 하나의 트랜잭션이 여러 번 같은 테이블에 대한 검색을 수행할 때의 결과가 다르다.

트랜잭션의 고립화 수준에 대한 자세한 설명은 *Administrator’s Manual*을 참고하기 바란다.

| 고립화 수준         | 특징                                                         |
| ------------------- | ------------------------------------------------------------ |
| 0 (Committed Read)  | Altibase의 기본 모드이다. 검색 트랜잭션이 읽은 데이터는 완료된 다른 트랜잭션에 의해 변경된 데이터임을 보장한다. 검색 트랜잭션이 한번 읽고 다시 읽을 때 다른 트랜잭션이 동시에 INSERT 혹은 DELETE를 수행하고 커밋했다면 그것이 반영되어 새로운 행(row)이 보이거나 혹은 보였던 행이 보이지 않게 될 수 있다. |
| 1 (Repeatable Read) | 한 트랜잭션 수행 동안 동일 레코드를 여러 번 반복해서 읽는 경우 항상 동일한 레코드의 내용을 검색하게 됨을 보장한다. 한번 읽을 때 읽은 행(row)에 잠금(lock)이 걸린다. 그래서 다시 읽을 때 이전에 보였던 행이 안 보이는 경우는 없으나, 그 사이에 새로 삽입된 행은 보일 수 있다. |
| 2 (No Phantom)      | 여러 번 반복해서 읽어도 모두 동일한 결과가 보이는 것을 보장한다. |

#### TRANSACTION_TABLE_SIZE(단위 : 트랜잭션 개수)

##### 데이터 타입

Unsigned Integer

##### 기본값

1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[16,16384]

##### 설명

Altibase 서비스 중에 동시에 생성될 수 있는 트랜잭션 개수를 데이터베이스를 생성할 때 설정할 수 있으며, 이에 대해 메모리가 미리 할당된다.

이 프로퍼티는 2n 크기만큼 값을 증감시켜야 하며, 감소시킬 때에는 반드시 데이터베이스를 다시 생성해야 한다.

### 백업 및 복구 관련 프로퍼티

데이터베이스가 변경될 때 변경 로그를 유지하는데, 이에 관한 처리를 어떻게 할 것인지를 정하는 프로퍼티들이 있다.

#### ARCHIVE_DIR

##### 데이터 타입

String

##### 기본값

$ALTIBASE_HOME/arch_logs

##### 속성

읽기 전용, 다중 값

##### 값의 범위

없음

##### 설명

데이터베이스를 아카이브 로그(Archivelog) 모드로 운영하는 경우 아카이브 로그파일들이 백업될 디렉토리를 설정하는 프로퍼티이다. 사용자가 명시적으로 이 값을 지정하지 않으면 기본으로 Altibase가 설치된 디렉토리 밑의 arch_logs 디렉토리에 아카이브 로그파일들이 백업된다. 이 프로퍼티의 개수는 LOG_DIR 프로퍼티 개수와 정확히 일치해야 한다.

사용자가 이 값을 명시적으로 지정할 수 있으나 지정된 디렉토리는 미리 생성되어 있어야 하며, 그렇지 않은 경우 오류 메시지를 출력함과 동시에 Altibase 서버가 구동되지 않는다.

#### ARCHIVE_FULL_ACTION

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

ARCHIVE_DIR에 설정된 디렉토리가 속한 파일 시스템에 충분한 디스크 공간이 없는 경우 아카이브 로그 백업(archive log backup)을 수행하는 아카이브로그 쓰레드의 동작을 제어하는 프로퍼티이다.

값이 0인 경우 아카이브로그 쓰레드는 오류 메시지를 출력한 후, 아카이브 로그파일을 백업하는 작업을 중지하게 된다. 이후 충분한 디스크 공간이 확보된 후에라도 사용자가 명시적으로 아카이브 로그 백업을 활성화하는 명령을 입력하지 않는 한 아카이브 로그 백업은 재개되지 않는다. 이 경우 체크포인트가 발생하면 아카이브 로그파일이 백업되지 않았더라도 불필요한 로그 파일들은 삭제되기 때문에 운영시 주의가 필요하다.

값이 1인 경우 아카이브로그 쓰레드는 충분한 디스크 공간이 확보되어 아카이브 로그파일을 백업할 수 있을 때까지 기다린다. 이 기간 동안은 체크포인트가 발생하더라도 아카이브 로그파일을 백업할 수 없기 때문에 로그 파일들은 삭제되지 않는다.

#### ARCHIVE_MULTIPLEX_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 10]

##### 설명

Altibase 서버가 아카이브 로그 파일의 복사본9을 몇 개 유지할 것인지를 지정한다. 프로퍼티 설정 이후에 새로이 아카이브 되는 로그 파일부터 복사본이 유지된다.

[9] 아카이브 로그 파일 다중화(Multiplexing Archive Logfiles): 아카이브 로그

파일을 별도의 디스크에 복사해 두어, 아카이브 로그 파일 원본의 손상에 대비하는 기능이다.

ARCHIVE_MULTIPLEX_COUNT와 ARCHIVE_MULTIPLEX_DIR 프로퍼티는 서버가 중지(shutdown)된 상태에서 설정할 수 있다.

#### ARCHIVE_MULTIPLEX_DIR

##### 데이터 타입

String

##### 기본값

""

##### 속성

읽기 전용, 다중 값

##### 값의 범위

없음

##### 설명

아카이브 로그 파일의 복사본이 위치할 경로를 지정한다. ARCHIVE_MULTIPLEX_DIR 프로퍼티는 ARCHIVE_MULTIPLEX_COUNT에 명시한 아카이브 로그 파일의 개수만큼 설정해야 한다. 이 때 각각의 경로는 서로 다른 디스크에 둘 것을 권장한다.

#### ARCHIVE_THREAD_AUTOSTART

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

아카이브 로그파일을 주기적으로 백업하는 쓰레드인 아카이브로그 쓰레드를 알티베이스 구동시 자동으로 활성화시킬 것인지를 지정하는 프로퍼티이다. 이 값을 1로 하는 경우 아카이브 쓰레드가 자동으로 활성화된다.

이 프로퍼티는 디렉토리에 아카이브 로그파일 백업을 위한 충분한 디스크 공간이 없어서 아카이브로그 쓰레드가 비활성화되면, 이후에 디스크 공간을 확보하여 아카이브로그 쓰레드를 다시 활성화하고자 할 때 사용할 수 있다.

#### CHECKPOINT_ENABLED

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

체크포인트를 ON 또는 OFF 시키는 프로퍼티이다.

0: OFF

1: ON

이 값을 0(OFF)으로 지정하면 체크포인트 쓰레드가 동작하지 않으며, CHECKPOINT_INTERVAL_IN_SEC와 CHECKPOINT_INTERVAL_IN_LOG 프로퍼티에서 지정한 주기로 동작할 수 없다. 그러나 사용자가 명시적으로 체크포인트를 수행하면 수행할 수 있다.

#### CHECKPOINT_INTERVAL_IN_LOG

##### 데이터 타입

Unsigned Integer

##### 기본값

100

##### 속성

변경 가능, 단일 값

##### 값의 범위

[1, 232-1]

##### 설명

체크포인트 주기를 설정하는 프로퍼티이다. 즉, 이 프로퍼티에 설정된 값만큼 로그 파일이 생성되면, 다음 체크포인트가 발생한다.

그러나 이 프로퍼티 값에 의해 체크포인트 수행이 요구될 때, 이미 체크포인트가 진행 중이거나 기타 다른 이유로 인하여 체크포인트가 수행되지 못하는 경우가 발생할 수 있다. 이 경우 이미 진행 중인 체크포인트가 끝난 후 바로 체크포인트를 수행하는 것이 아니라 현재의 체크포인트 요구는 바로 취소된다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### CHECKPOINT_INTERVAL_IN_SEC(단위 : 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

6000

##### 속성

변경 가능, 단일 값

##### 값의 범위

[3, 2592000]

##### 설명

체크포인트의 주기를 초 단위 시간으로 정하는 것이다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### COMMIT_WRITE_WAIT_MODE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

트랜잭션을 커밋할 때 로그가 로그 파일에 반영될 때까지 기다릴 것인지 여부를 설정하는 프로퍼티이다. Altibase는 기본으로 성능을 위해 기다리지 않는 값으로 설정된다.

이 프로퍼티는 시스템 전체에 대해서 혹은 사용자의 세션 단위로 설정할 수 있으며, Altibase 운영 중 ALTER SYSTEM 또는 ALTER SESSION 구문으로 변경할 수 있다.

0: Do Not Wait

1: Wait

#### INCREMENTAL_BACKUP_CHUNK_SIZE

##### 데이터 타입

Unsigned Integer

##### 기본값

4

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

데이터의 페이지가 변경되는 것을 페이지 단위로 추적하기 위해 설정하는 프로퍼티이다. 예를 들어 이 프로퍼티의 값이 4로 설정되면, 4개의 페이지 단위로 변경 추적 정보를 기록하기 때문에, 한 묶음에 속하는 4개의 페이지 중 하나라도 변경된다면 그 묶음의 모든 페이지가 백업된다.

이 프로퍼티를 변경하려면 아래의 단계를 거쳐서 changeTracking 파일을 다시 생성해야 한다.

1. 서버 종료 후 프로퍼티 파일에서 값 변경
2. 서버 구동
3. 변경 추적 기능 비활성화 후 다시 활성화

#### INCREMENTAL_BACKUP_INFO_RETENTION_PERIOD

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

backupInfo 파일에 저장되는 백업 정보가 유지되는 기간(단위: 일)을 지정하는 프로퍼티이다.

ALTER DATABASE DELETE OBSOLETE BACKUP FILES 구문으로 삭제되는 백업 정보는 유효 기간이 지난 가장 오래된 레벨 0 백업부터 유효 기간이 지나지 않은 가장 오래된 레벨 0 바로 이전의 레벨 1 백업까지이다.

> 참고: 증분 백업에 대한 복구에는 레벨 0로 백업된 백업 파일이 반드시 필요하다. 따라서 이 프로퍼티에 지정한 유지 기간이 지난 백업 정보와 거기에 대응하는 백업 파일이 있더라도, 레벨 0 백업이 유일하다면, 삭제 명령을 실행하더라도 유지 기간이 지난 백업 정보와 백업 파일이 삭제되지 않는다.

#### LOG_BUFFER_TYPE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

로그 버퍼 타입을 결정하는 프로퍼티이다.

0: 운영체제 커널의 로그 버퍼를 사용

1: 프로세스 메모리의 로그 버퍼를 사용

이 프로퍼티는 시스템 운영 중에 변경할 수 없다.

#### LOG_MULTIPLEX_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 10]

##### 설명

Altibase 서버가 로그 파일의 복사본10을 몇 개 유지할 것인지를 지정한다. 원본 로그 파일이 생성되거나 삭제될 때 로그 파일의 복사본도 동시에 생성되거나 삭제된다.

[10] 로그 파일 다중화(Multiplexing Log Files): 데이터베이스의 모든 변경 사항이

기록되는 로그 파일을 별도의 디스크에 복사해 두어, 로그 파일 원본의 손상에 대비하는 기능이다.

LOG_MULTIPLEX_COUNT와 LOG_MULTIPLEX_DIR 프로퍼티는 서버가 중지(shutdown)된 상태에서 설정할 수 있다.

#### LOG_MULTIPLEX_DIR

##### 데이터 타입

String

##### 기본값

""

##### 속성

읽기 전용, 다중 값

##### 값의 범위

없음

##### 설명

로그 파일의 복사본이 위치할 경로를 지정한다. LOG_MULTIPLEX_COUNT에 명시한 개수만큼 LOG_MULTIPLEX_DIR 프로퍼티를 설정해야 한다. 또한, 각 경로를 서로 다른 디스크에 둘 것을 권장한다.

#### PREPARE_LOG_FILE_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

5

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

로그 생성시 해당 로그파일에 충분한 공간이 없으면 새로운 로그 파일을 생성하며, 이 경우 트랜잭션의 응답 시간은 늦어지게 된다. 이처럼 로그파일 생성으로 인해 트랜잭션의 수행이 늦어지는 것을 막기 위해 Altibase는 여분의 로그파일을 미리 생성해 둔다. 이 여분의 로그파일의 개수를 지정하는 것이 이 프로퍼티이다.

**SNAPSHOT_MEM_THRESHOLD(단위: 백분율)**

##### 데이터 타입

Unsigned Integer

##### 기본값

80

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 100]

##### 설명

스냅샷 설정(BEGIN SNAPSHOT) 이후 메모리 데이터베이스에서 사용할 수 있는 임계치(Threshod)를 설정하는 프로퍼티이다.

현재 사용되는 메모리의 크기는 프로퍼티 MEM_MAX_DB_SIZE의 몇 퍼센트를 사용하고 있는지 확인하고, 설정한 임계치를 초과하면 스냅샷(shapshot)은 자동으로 중지된다.

**SNAPSHOT_DISK_UNDO_THRESHOLD(단위: 백분율)**

##### 데이터 타입

Unsigned Integer

##### 기본값

80

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 100]

##### 설명

스냅샷 설정(BEGIN SNAPSHOT) 이후 디스크에서 사용할 수 있는 임계치(Threshold)를 설정하는 프로퍼티이다.

현재까지 사용된 디스크 언두 테이블스페이스의 크기는 프로퍼티 SYS_UNDO_FILE_MAX_SIZE 에서 몇 퍼센트를 사용하는지 확인하고, 설정한 임계치를 초과하면 스냅샷(shapshot)은 자동으로 중지된다.

### 이중화 프로퍼티

다음 속성값들은 데이터베이스의 이중화 기능을 위한 값들이다. 데이터베이스 이중화에 대한 자세한 내용은 *Getting Started Guide*의 데이터베이스 이중화 장과 *Replication Manual*을 참조하기 바란다.

#### REPLICATION_ACK_XLOG_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

100

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

수신 쓰레드가 송신 쓰레드에게 ACK를 보내는 주기를 나타낸다.

수신 쓰레드는 XLog를 받아서 하나씩 반영하는 작업을 하는데, 반영한 XLog의 개수가 REPLICATION_ACK_XLOG_COUNT를 넘게 되면 송신 쓰레드에게 ACK를 전송한다.

이 값이 너무 작으면 송신 쓰레드에 ACK를 자주 보내게 되어 성능 저하를 가져올 수 있다.

너무 큰 경우에는 송신 쓰레드가 ACK를 받기 위해 대기하는 시간을 초과하여 네트워크 장애로 판단할 수 있다. 또한, 오랜 시간 ACK를 받지 못하는 경우 이중화 재시작 SN이 갱신되지 않아, 체크포인트시 송신 쓰레드가 가장 최근의 로그 레코드부터 다시 시작되며, 이중화하지 못한 로그 파일이 삭제되는 현상이 발생할 수 있다.

#### REPLICATION_ALLOW_DUPLICATE_HOSTS

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

이중화 객체들의 원격 서버 IP 주소와 포트 번호를 서로 동일하게 설정하는 것을 허용할 것인지 지정한다.

0: 허용하지 않는다.

1: 허용한다.

#### REPLICATION_BEFORE_IMAGE_LOG_ENABLE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

이중화 수신자의 "이전 이미지(before image)"가 송신자로부터 받은 XLog의 이전 이미지와 다르면 데이터 충돌이 발생할 수 있다.

사용자가 충돌이 발생한 데이터를 확인할 수 있도록, 이 프로퍼티를 설정하여 트레이스 로그에 이중화 수신자의 이전 이미지를 기록할 수 있다.

0: 기록하지 않음

1: 기록함

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_COMMIT_WRITE_WAIT_MODE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

이중화 수신자가 수신한 XLOG를 복제 트랜잭션으로 수행 완료한 후에 디스크에 반영될 때까지 기다릴지 여부를 지정한다. 이 값이 0이면 기다리지 않으며, 1이면 디스크에 반영될 때까지 기다린다.

#### REPLICATION_CONNECT_RECEIVE_TIMEOUT (단위: 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

60

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

이중화 시작시 대상 호스트에 접속을 시도한 후, 대기하는 시간이다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_CONNECT_TIMEOUT (단위: 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

10

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

이중화를 수행하기 위해 대상 호스트에 대한 연결 수행 시, 이 프로퍼티에 설정된 시간 값 이상 응답이 없을 경우 연결을 더 이상 시도하지 않는다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_DDL_ENABLE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

이중화 대상 테이블에 DDL 구문을 허용할 것인지를 나타낸다. 1로 설정한 경우 이중화 대상 테이블에 DDL을 실행할 수 있다.

DDL을 수행하기 전에 현재 세션에서 수행하는 트랜잭션의 이중화 프로퍼티를 NONE 이외의 값으로 설정해야 송신 쓰레드에서 DDL 실행을 알 수 있다. 이중화에서 허용하는 DDL 목록과 제약사항은 *Replication Manual*을 참조한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_DDL_ENABLE_LEVEL

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

이중화 대상 테이블에 사용할 수 있는 DDL 구문의 범위를 결정한다. 이 프로퍼티를 사용하려면 먼저 REPLICATION_DDL_ENABLE 프로퍼티의 값을 1로 설정해야 한다. REPLICATION_DDL_ENABLE_LEVEL 값에 따라 허용되는 DDL 구문은 *Replication Manual*을 참조한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_DDL_SYNC

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

이중화중 DDL 복제 여부를 나타낸다.

0 : 이중화중 DDL 복제를 허용하지 않음. DDL 수행 시 이중화 지역 서버 ( Local Server ) 에서만 수행된다.

1 : 이중화중 DDL 복제를 허용함. DDL 수행 시 이중화 원격 서버 ( Remote Server )에 DDL 이 복제된다.

Altibase 운영 중 ALTER SYSTEM 문 또는 ALTER SESSION 문을 이용하여 이 프로퍼티 값을 변경할 수 있다.

#### REPLICATION_DDL_SYNC_TIMEOUT ( 단위 : 초 )

##### 데이터 타입

Unsigned Integer

##### 기본값

7200

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

DDL 복제의 실행 시간이 이 프로퍼티에 설정한 시간(초)을 초과하면, 그 구문의 실행은 이중화 지역, 원격 서버 모두 취소된다. DDL 복제를 수행하는 이중화 지역서버를 기준으로 Timeout 값이 측정된다. Altibase 운영 중 ALTER SYSTEM 문 또는 ALTER SESSION 문을 이용하여 이 프로퍼티 값을 변경할 수 있다.

#### REPLICATION_EAGER_PARALLEL_FACTOR

##### 데이터 타입

Unsigned Integer

##### 기본값

'CPU개수/2'와 '512' 중 작은 값

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 512]

##### 설명

EAGER모드로 이중화 수행시 여러 개의 송신 쓰레드가 병렬로 작업을 하게 된다. 이 프로퍼티는 병렬 작업할 송신 쓰레드의 개수를 지정한다. 이중화 송신 쓰레드의 개수를 늘리면 이중화 성능이 향상될 수 있다.

그러나, 이 프로퍼티를 사용하여 송신 쓰레드 개수를 늘릴 경우, 송신 쓰레드가 보내는 트랜잭션의 순서가 보장되지 않는다는 점을 주의해야 한다. 이에 대한 자세한 내용은 *Replication Manual*을 참고한다.

이 프로퍼티를 설정하지 않으면 기본값은 CPU개수와 512중 더 작은 값이 된다.

#### REPLICATION_EAGER_RECEIVER_MAX_ERROR_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

5

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

Eager 모드로 이중화를 진행할 때, 이중화 수신자가 데이터 복제를 재시도하는 횟수를 설정할 수 있는 프로퍼티이다.

만약 이 값이 5로 설정되었을 때, Xlog 복제에 오류가 발생하면 이중화 수신자는 최대 5회까지 복제를 재시도한다. 재시도에서도 성공하지 못하면 Altibase 서버를 강제로 종료한다. 이 값을 0으로 설정하면, 이중화 수신자가 Xlog 복제에 실패할 경우 성공할 때까지 복제를 재시도하며, 서버를 강제 종료하지 않는다.

Eager 모드의 이중화는 이중화 수신자와 송신자간의 데이터 일치가 중요한 환경에서 주로 사용된다. 따라서 사전에 데이터 불일치를 예방하기 위해 데이터 복제를 중단하고 서버를 종료하는 것이다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_FAILBACK_INCREMENTAL_SYNC

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

이 프로퍼티는 증분 동기화(Incremental Sync) 수행 여부를 설정한다. 증분 동기화란 EAGER 모드의 이중화 작업 중 한 쪽 서버의 장애로 인해 데이터 불일치가 발생한 경우, 이 후 장애 서버가 다시 구동되는 중에 서버가 불일치 데이터를 동기화하는 것을 말한다.

- 0: 증분 동기화를 비활성화시킨다.
- 1: 증분 동기화를 활성화시킨다.

이중화에 참가하는 양쪽 Altibase 서버 모두 이 프로퍼티를 같은 값으로 설정해야 한다. 증분 동기화 및 Eager 이중화 장애 복구에 대한 자세한 내용은 *Replication Manual*을 참고한다.

#### REPLICATION_GAP_UNIT (단위: 바이트)

##### 데이터 타입

Unsigned Long

##### 기본값

1048576 (1MB)

##### 속성

변경 가능, 단일 값

##### 값의 범위

[1, 264-1]

##### 설명

이중화 갭의 크기를 조회하는 REP_GAP의 값을 표현하는 단위를 설정한다.

REP_GAP의 값은 REP_GAP_SIZE의 값을 이 프로퍼티로 나눈 결과값이며, 나머지는 올림한다.

기본값이면 V$REPGAP의 REP_GAP_SIZE는 바이트 단위로, REP_GAP은 메가바이트 단위로 조회된다.

#### REPLICATION_GAPLESS_ALLOW_TIME (단위: 마이크로 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

2000

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

갭 해소 옵션이 설정된 이중화 송신자는 이 프로퍼티에 설정한 시간만큼 이중화 격차(Replication Gap)를 허용한다. 이중화 송신자는 이 프로퍼티에 설정된 시간 안에 이중화 격차를 해소할 수 없다고 판단하면 서비스 트랜잭션의 커밋을 지연시키는 기능이 동작한다.

예를 들어 이 프로퍼티가 5이고, 송신자가 초당 처리하는 로그가 1,000건이라면 이중화 격차를 허용할 수 있는 로그의 개수는 5,000건이다. 만약 현재의 이중화 격차가 10,000건이라면, 허용하는 로그의 개수보다 5,000건을 초과하였으므로, 이중화 격차가 허용하는 로그 개수에 만족하기 위해서 트랜잭션이 5초간 지연되어야 한다는 것을 의미한다.

이 값이 0이면 이중화 격차를 허용하지 않는다는 의미이므로, 트랜잭션이 커밋되기 전에 이중화 격차를 해소시키고 커밋을 수행한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_GAPLESS_MAX_WAIT_TIME (단위: 마이크로 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

10*,*000*,*000

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

이중화 갭 해소(Gapless) 옵션이 설정된 이중화 송신자가 이중화 격차를 해소하기 위하여 트랜잭션 커밋을 지연시킬 수 있는 최대 시간을 의미한다.

이 값이 0이면 이중화 격차를 해소할 때까지 트랜잭션의 커밋을 지연시킨다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_GROUPING_TRANSACTION_MAX_COUNT (단위 : 개)

##### 데이터 타입

Unsigned Integer

##### 기본값

5

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 1000]

##### 설명

Ahead Analyzer 쓰레드가 복수의 트랜잭션을 한 번에 최대 몇 개까지 그룹화하여 수신자에 전송할 것인지 정하는 프로퍼티이다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_GROUPING_AHEAD_READ_NEXT_LOG_FILE (단위 : 개)

##### 데이터 타입

Unsigned Integer

##### 기본값

2

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 232-1]

##### 설명

선행 분석(Ahead Analyzer) 쓰레드가 분석을 시작할 때, 송신자(Sender)가 현재 읽는 로그 파일 번호보다 얼마나 큰 번호의 로그 파일을 읽을 것인지 설정한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_HBT_DETECT_HIGHWATER_MARK

##### 데이터 타입

Unsigned Integer

##### 기본값

5

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

연결(Connection) 응답을 하지 않는 경우 몇 회 이후에 장애로 판단할 것인지 결정한다. 따라서, 임의의 호스트의 장애를 판단하는 최대 시간은 REPLICATION_HBT_DETECT_TIME * REPLICATION_HBT_DETECT_HIGHWATER_MARK 이다.

즉, HeartBeat 쓰레드는 기본값인 30초 (5회 시도* 6초) 동안 연결이 되지 않을 경우 장애로 판단한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_HBT_DETECT_TIME(단위 : 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

6

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 2592000]

##### 설명

HeartBeat 쓰레드12의 검사 주기를 설정한다. 기본값인 6초 마다 HeartBeat 쓰레드는 해당 호스트에 대한 장애를 검사한다.

[12] HeartBeat 쓰레드: Altibase의 리플리케이션은 송신 쓰레드와 수신 쓰레드

간에 데이터 통신 수행 시 물리적인 장애가 발생했을 때, 신속하게 장애를 검출하기 위하여 HeartBeat 쓰레드를 만들어서 상대 호스트의 상태를 주기적으로 검사하는 기법을 도입했다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_IB_LATENCY

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

rsocket의 RDMA_LATENCY 옵션 값이다.

이 값이1이면 CPU 자원을 소모하더라도, 적은 대기 시간을 사용한다.

#### REPLICATION_IB_PORT_NO

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 65535]

##### 설명

이중화로 연결할 때 인피니밴드(InfiniBand)를 이용하여 접속할 경우 지역 서버의 이중화 포트 번호를 나타낸다.

인피니밴드를 이용하기 위해 IB_ENABLE 프로퍼티의 값이 1이어야 한다. 이 값이 0인 경우에는 인피니밴드로 이중화를 연결할 수 없다.

#### REPLICATION_INSERT_REPLACE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

이 프로퍼티는 이중화 중 INSERT 충돌이 발생했을 때 삽입된 내용을 유지할 지를 결정한다. 이 값이 0이면, INSERT는 커밋되지 않고 데이터 충돌은 에러 처리 된다. 반면에 이 값이 1이면 데이터 충돌은 무시되고 INSERT는 커밋된다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_KEEP_ALIVE_CNT

##### 데이터 타입

Unsigned Integer

##### 기본값

600

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

송신 쓰레드가 패킷을 전송하지 않고 (REPLICATION_SENDER_SLEEP_TIME * REPLICATION_KEEP_ALIVE_CNT) 시간 동안 Sleep하면, KEEP_ALIVE신호를 전송한다.

#### REPLICATION_LOCK_TIMEOUT (단위: 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

5

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 3600]

##### 설명

이중화 데드락이 발생하는 경우 수신 쓰레드 쪽에서는 무한정 잠금을 기다리게 되어 서비스가 중단될 수 있다. 이러한 경우를 방지하기 위해 수신 쓰레드는 해당 작업의 수행에 대해 잠금을 요구할 때, 최대 이 프로퍼티에 설정된 시간만큼만 잠금을 획득하기 위해 기다린다.

명시된 시간 내에 잠금을 획득하지 못하는 경우 해당 작업은 철회된다.

#### REPLICATION_LOG_BUFFER_SIZE (단위 : MB)

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 212-1]

##### 설명

이중화 전용 로그 버퍼를 사용함으로써 이중화 성능을 개선하는 프로퍼티이다. 이중화 전용 로그 버퍼에는 이중화에 필요한 로그만 필터링하여 저장하기 때문에 더 많은 로그가 버퍼에 존재한다.

송신 쓰레드는 로그를 읽기 위해서 로그 버퍼 또는 디스크에서 로그를 읽는다. 그러나 디스크에서 로그를 읽는 경우 송신 쓰레드의 처리 속도가 현저히 떨어질 수 있다. 더욱이 이중화를 실행하면 필요하지 않은 로그까지 읽어야 하는 부담이 발생한다. 이중화 전용 로그 버퍼는 이러한 부담을 완화시켜준다.

다수의 이중화 송신 쓰레드가 수행중일 때는 이중화 성능과 서비스 성능이 저하될 수 있다. 이중화 로그 버퍼가 하나이므로 다수의 송신 쓰레드가 접근한다면 동기화 오버헤드가 발생할 확률이 높아지기 때문이다.

이중화 로그 버퍼에서 읽은 로그는 REPLICATION_SYNC_LOG 값을 1로 하여도 디스크에 기록되지 않은 상태에서 수신 쓰레드로 전송될 수 있다.

REPLICATION_LOG_BUFFER_SIZE를 너무 작게 설정하면, 사용하지 않는 것(0)보다 더 좋지 못한 성능을 낼 수 있다.

#### REPLICATION_MAX_COUNT (단위 : 개)

##### 데이터 타입

Unsigned Integer

##### 기본값

32

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 10240]

##### 설명

Altibase에 생성할 수 있는 이중화 객체의 최대 개수를 지정한다.

기본값은 32이며, 한 서버에서 최대 32개의 원격 서버와 이중화로 연결할 수 있음을 의미한다.

#### REPLICATION_MAX_LISTEN

##### 데이터 타입

Unsigned Integer

##### 기본값

32

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 512]

##### 설명

이중화 송신 쓰레드와 수신 쓰레드를 관리하는 Altibase 서버간의 통신 시 TCP/IP 소켓을 사용하는 경우 대기 큐(listen queue)의 크기를 지정하는 값이다. .

#### REPLICATION_MAX_LOGFILE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 65535]

##### 설명

이중화를 위하여 재시작 리두 시점(Restart Redo Point)을 기준으로 삭제하지 않을 최대 로그파일의 개수이다.

이중화 시작 후, 지역 서버와 원격 서버간의 네트워크 속도 등의 문제로 지역 서버의 변경내용이 아직 원격 서버에 반영되지 않았을 경우, 체크포인트가 발생해도 서버는 로그 파일을 삭제할 수 없다. 이러한 문제가 발생하면, 지역서버의 로그파일 개수가 계속 증가하게 되고 결국 디스크가 가득 차버릴 수 있다(Disk Full).

따라서 체크포인트가 발생하였을 때, 재시작 리두 시점 (Restart Redo Point) 이전 로그 파일들의 개수가 이 프로퍼티로 정해 놓은 값보다 클 경우 이중화는 잠시 중단되며, Altibase는 중단된 시점의 일시 (날짜, 시각)와 “재시작 SN”을 SYS_REPLICATION_ 메타 테이블의 GIVE_UP_TIME과 GIVE_UP_XSN 컬럼에 각각 저장한다. 그리고 재시작 리두 시점 이전 로그파일들을 삭제한다. 현재 로그파일의 마지막(가장 큰) SN값이 새로운 이중화 “재시작 SN” 이 되며, 이 값도 SYS_REPLICATION_ 메타 테이블의 XSN 컬럼에 저장된다. 이중화는 이 새로운 “재시작SN”부터 다시 수행될 것이다. 이런 디폴트 작업 방식을 변경하고 싶다면, REPLICATION_SENDER_START_AFTER_GIVING_UP 프로퍼티 값을 변경하면 된다. 또, SYS_REPLICATION_ 메타 테이블에서 특정 replication과 관련된 모든 정보들을 초기화하고 싶다면, “ALTER REPLICATION replication_name RESET” 을 실행해라.

0으로 설정한 경우에는 이 기능을 적용하지 않는다. 참고로 체크포인트를 수행할 때 로그파일을 지우기 때문에, CHECKPOINT_INTERVAL_IN_SEC와 CHECKPOINT_IN_LOG의 값을 함께 고려해야 한다.

#### REPLICATION_POOL_ELEMENT_COUNT(단위 : 개)

##### 데이터 타입

Unsigned Integer

##### 기본값

10

##### 속성

변경 가능, 단일 값

##### 값의 범위

[1, 1024]

##### 설명

송신 쓰레드가 로그를 분석하여 칼럼 값을 복사할 때 사용하는 메모리의 개수이다. 이 때 메모리는 메모리 풀에서 미리 할당하며, 메모리 크기는 REPLICATION_POOL_ELEMENT_SIZE에서 지정한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_POOL_ELEMENT_SIZE(단위 : Byte)

##### 데이터 타입

Unsigned Integer

##### 기본값

256

##### 속성

변경 가능, 단일 값

##### 값의 범위

[128, 65536]

##### 설명

송신 쓰레드가 로그를 분석하여 각각의 칼럼 값을 복사할 때 사용하는 메모리의 크기이다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_PORT_NO

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 65535]

##### 설명

이중화 연결을 할 때 지역 서버의 이중화 포트 번호이다. 이중화를 사용하지 않으려면 이 프로퍼티를 0으로 설정한다.

#### REPLICATION_PREFETCH_LOGFILE_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

3

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1024]

##### 설명

각각의 로그 파일 그룹에 대해서 미리 읽을 로그 파일의 수를 나타낸다. 로그 파일을 미리 읽어 둠으로써 송신 쓰레드가 파일에서 로그 레코드를 읽는 시간을 줄인다.

#### REPLICATION_RECEIVE_TIMEOUT(단위 : 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

7200

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

송신 쓰레드와 수신 쓰레드에서 공통적으로 사용하는 프로퍼티로 송신/수신 쓰레드로부터 어떤 메시지를 기다리는 최대 시간을 지정하는 프로퍼티이다.

송신 쓰레드에서는 상대편 수신 쓰레드로부터 응답을 기다리는 최대 시간이며 명시된 시간이 경과하게 되면 REPLICATION_SENDER_SLEEP_TIMEOUT에서 지정된 시간만큼 sleep한 후 다시 상대편 수신 쓰레드와의 접속을 시도한다. 이 경우 기존 사용하던 소켓은 닫고 새로운 소켓을 생성하여 재연결을 시도한다.

수신 쓰레드에서는 상대편 송신 쓰레드로부터 어떤 메시지를 기다리는 최대 시간이다. 명시된 시간이 경과하게 되면 수신 쓰레드는 자동 종료되며 이후 상대편 송신 쓰레드가 어떤 메시지를 다시 보내게 되는 경우 다시 생성된다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_RECEIVER_APPLIER_ASSIGN_MODE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

이중화 수신자가 적용자(Applier)에게 XLog를 할당할 때 어떤 모드로 적용자에게 분배할 것인지를 선택하는 프로퍼티이다.

0: XLog Count Mode

1: Transaction Count Mode

이 값이 0이면 수신자는 XLog 개수가 가장 적게 할당된 적용자에게 XLog를 할당한다. 1인 경우에는 할당된 트랜잭션이 가장 적은 적용자에게 XLog를 할당한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_RECEIVER_APPLIER_QUEUE_SIZE

##### 데이터 타입

Unsigned Integer

##### 기본값

20

##### 속성

변경 가능, 단일 값

##### 값의 범위

[2, 232-1]

##### 설명

수신자가 적용자 쓰레드들의 대기 큐에 전달할 수 있는 최대 XLog의 개수이다.

이 값이 클수록 적용자(Applier)에 전달하는 XLog의 개수가 많아질 수 있으나, 대기 큐에 XLog 들이 쌓이므로 메모리를 보다 많이 사용하게 된다. 이 값은 적용자 숫자의 2배 가량으로 설정하는 것을 권고한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_RECEIVER_APPLIER_YIELD_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

20000

##### 속성

변경 가능, 단일 값

##### 값의 범위

[2, 232-1]

##### 설명

Applier 가 다른 Applier 의 Transaction 반영 대기시 시스템 함수인 yield 를 이용하여 대기 하는 횟수.

yield 함수를 사용시 CPU 사용을 하기 때문에 이 횟수 이상 호출 이후에는 CPU자원을 사용안하는 timed_wait 함수를 호출 한다.

#### REPLICATION_RECOVERY_MAX_LOGFILE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 232–1]

##### 설명

이중화를 이용한 데이터 복구를 위하여 재시작 리두 시점(Restart Redo Point)을 기준으로 삭제하지 않을 최대 로그 파일의 개수를 의미한다.

이중화를 이용한 데이터 복구를 하기 위하여 원격 서버에서 디스크에 반영(flush)되지 않은 로그에 해당하는 지역 서버의 로그를 삭제하지 않고 유지한다. 이 때 체크포인트가 발생해도 로그 파일을 삭제할 수 없어 지역 서버의 로그파일 개수가 계속 증가하게 되면 결국 디스크 풀이 발생할 수 있다.

따라서 체크포인트가 발생하였을 때 복구 옵션을 위한 로그 파일 개수의 최대 값을 넘는 경우, 이중화를 이용한 복구를 포기하고, 로그 파일들을 삭제한다. 그리고 이중화를 다시 시작한다.

0으로 설정한 경우, 이 기능을 적용하지 않는다.

체크포인트를 수행할 때 로그 파일을 지우기 때문에, CHECKPOINT_INTERVAL_IN_SEC와 CHECKPOINT_IN_LOG의 값을 함께 고려해야 한다.

#### REPLICATION_RECOVERY_MAX_TIME (단위 : 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

232–1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 232–1]

##### 설명

이중화 모듈이 복구를 진행하는 중에 최대 시간이 지나면, 복구를 중단하고 지금까지 복구된 상태로 서비스를 진행할 수 있도록 한다.

이 값을 0으로 설정하는 경우, 이중화를 이용한 복구 과정을 진행하지 않는다.

Altibase는 이중화를 이용한 데이터 복구가 완료하기 전에 서비스 단계로 진행할 수 없어, 서비스 지연을 가져올 수 있다.

#### REPLICATION_SENDER_AUTO_START

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

Altibase가 서버 종료시 stop 시키지 않은 이중화 객체가 있었다면, 서버 재구동 시 이러한 이중화 객체들이 자동으로 시작되는 것이 기본 동작이다. 이 값을 0으로 설정하면, 서버 구동 시 이중화 객체가 자동으로 시작되는 것을 막을 수 있다.

#### REPLICATION_SENDER_COMPRESS_XLOG

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

이 프로퍼티는 이중화를 위해 데이터가 네트워크 상에서 전송될 때, 전송하는 패킷의 압축 여부를 지정한다.

0: 전송할 데이터를 압축하지 않음

1: 전송할 데이터를 압축함

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_SENDER_ENCRYPT_XLOG

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

이 프로퍼티는 이중화를 수행할 때 송신 쓰레드의 로그를 암호화하여 전송할 것인지 여부를 지정할 수 있다.

0: 전송 로그를 비암호화

1: 전송 로그를 암호화

#### REPLICATION_SENDER_SEND_TIMEOUT (단위: 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

7200

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

송신 쓰레드가 원격 서버로 패킷을 전송할 때 대기하는 최대 시간을 지정하는 프로퍼티이다.

이 값은 REPLICATION_RECEIVE_TIMEOUT(기본값:7200초) 프로퍼티의 값과 동일한 값을 설정할 것을 권고한다. 이 값을 0으로 설정하면 송신 쓰레드가 블로킹 소켓(blocking socket)을 사용한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_SENDER_SLEEP_TIME (단위: 마이크로 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

10000

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

이 프로퍼티는 송신 쓰레드가 더 이상 읽을 로그가 없을 때, Sleep하는 시간을 지정한다. 특정 플랫폼에서는 짧은 시간의 Sleep이 무시되므로, 적당한 값을 지정해야 한다. REPLICATION_KEEP_ALIVE_CNT와 함께 KEEP_ALIVE를 전송하는 데 사용된다.

#### REPLICATION_SENDER_SLEEP_TIMEOUT(단위: 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

60

##### 속성

변경가능, 단일 값

##### 값의 범위

[0, 2592000]

##### 설명

이중화 송신 쓰레드가 오류 상황에서 sleep을 해야 할 때 얼마나 할 것인지를 결정한다.

Altibase 운영 중에 ALTER SYSTEM 구문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_SENDER_START_AFTER_GIVING_UP

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

이 프로퍼티는 재시작 리두 시점 (Restart Redo Point) 이전 로그 파일들의 개수가 REPLICATION_MAX_LOGFILE 프로퍼티로 설정된 값을 초과하여 이중화가 잠시 중단된 이후, 다시 시작하는 방식을 결정한다.

0으로 설정된 경우에는, 이중화 "재시작 SN" (즉 SYS_REPLICATIONS_ 메타 테이블의 XSN 컬럼의 값)이 -1로 초기화되며, 이중화는 중지된다. 그리고, SYS_REPLICATIONS_ 메타 테이블의 IS_STARTED 컬럼의 값이 0으로 바뀐다.

1로 설정된 경우, 이중화 "재시작 SN" 값은 현재 로그 파일의 마지막 (가장 큰) SN으로 변경되고, 이중화는 이 "재시작 SN" 부터 다시 수행된다.

#### REPLICATION_SERVER_FAILBACK_MAX_TIME

##### 데이터 타입

Unsigned Integer

##### 기본값

232-1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

EAGER 모드 이중화에서, 비정상 종료된 서버가 재구동 될 때, 다른 쪽(즉, 원격) 서버의 데이터와 동기화된 후에야 서비스가 재개된다. 이 때, 다른 서버의 로그를 비정상 종료했던 서버에 반영하는 과정이 이 프로퍼티에 설정된 시간(초)보다 오래 걸린다면, 비정상 종료했던 서버는 동기화가 완료되는 것을 포기하게 된다.

#### REPLICATION_SQL_APPLY_ENABLE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

Lazy 모드로 이중화 수행 과정에서 Active 서버와 Standby 서버의 이중화 테이블 메타 정보가 다른 경우, 아래의 조건에 따라 XLog가 SQL 문으로 변환되어 반영된다.

- 0: XLog를 이용하여 이중화가 동작한다. 이때, 메타 정보가 다르면 Handshaking 에러가 발생한다.
- 1: 아래의 조건에서 이중화를 수행하면, XLog가 SQL 문으로 변환이 되어 이중화 테이블에 반영한다.
- 컬럼 정보
  데이타 타입이 다를 경우
  size, precision, scale 이 다를 경우
- 제약 조건
  check 제약 조건이 다를 경우
  Not Null 제약 조건이 다를 경우
  다른 메타 정보 중 LOB 컬럼이 포함된 경우
- 인덱스
  유니크 인덱스나 Function-based 인덱스가 이중화 대상 컬럼과 이중화 대상이 아닌 컬럼으로 구성되어 있을 경우
  유니크 인덱스의 구성 정보가 다를 경우
  Function-based 인덱스의 구성 정보가 다를 경우

#### REPLICATION_SYNC_APPLY_METHOD

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

이중화 수행 중에 지역 서버와 원격 서버간의 불일치한 데이터를 어떤 방식으로 동기화 할 것인지 설정한다.

- 0: Normal Insert
- 1: Direct-Path Insert

이중화 SYNC 과정에서 Direct-Path Insert 방식을 이용할 경우, 데이터 동기화 이후 Index를 재생성한다. 따라서, 이중화 SYNC 과정이 도중에 실패할 경우, Index inconsistent 가 발생할 수 있다.

Direct-Path Insert에 대한 자세한 설명은 *Administrator’s Manual*을 참조하기 바란다. Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_SYNC_LOCK_TIMEOUT (단위: 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

30

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

이중화 송신 쓰레드가 동기화 대상 테이블의 잠금(lock)을 획득하기 위해 대기하는 시간을 정하는 프로퍼티이다. ALTER REPLICATION .. SYNC 구문으로 이중화 동기화를 실행하면, 이중화 송신 쓰레드는 데이터 동기화를 수행한 후 계속해서 이중화를 시작할 로그 위치를 결정한다. 이 때 동기화 대상 테이블이 다른 트랜잭션에 의해 데이터가 변경되지 않도록 송신 쓰레드는 공유 잠금(S Lock)을 획득한다. 그러나 이미 다른 트랜잭션에 의해 잠금이 되었다면, 이 프로퍼티에 지정한 시간만큼 대기한다.

예를 들어 이 프로퍼티의 값이 30인 경우, 30초 동안 잠금을 획득할 수 없으면 동기화 시도는 오류 처리된다. 만약 이 값을 0으로 설정하면 이중화 대상 테이블에 대한 잠금은 획득하지 않지만, 데이터의 충돌이 발생할 수 있다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_SYNC_LOG

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

이중화 수행 시 송신 쓰레드가 보내는 로그는 디스크에 내려갔는지의 여부에 관계없이 메모리 상의 로그를 보내기 때문에, 시스템 또는 매체 장애(media failure)와 같은 상황에서 데이터 불일치 등의 문제가 발생할 소지가 있다.

이러한 문제를 해결하기 위해서 이 값을 1로 설정하면, 송신 쓰레드는 디스크에 내려간 로그만 보내게 된다.

#### REPLICATION_SYNC_TUPLE_COUNT

##### 데이터 타입

Unsigned long

##### 기본값

50000

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 264-1]

##### 설명

병렬 동기화시 송신 쓰레드가 한번에 읽어서 처리할 수 있는 레코드의 최대 개수를 지정한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_TIMESTAMP_RESOLUTION

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

Active-Active 이중화 환경에서 데이터 충돌이 발생하였을 때 이 프로퍼티의 값에 따라 해결방식이 다르게 적용된다.

이 프로퍼티의 값이 1로 설정되고, 이중화 대상 테이블에 TIMESTAMP 컬럼이 있는 경우에 Timestamp-based Scheme 방식으로 충돌이 해결된다.

그러나 이중화 대상 테이블에 TIMESTAMP 컬럼이 있어도, 이 프로퍼티의 값이 0이면 이미 설정되어 있는 Conflict Resolution Scheme 방식이 사용된다.

데이터 충돌에 대한 자세한 설명은 *Replication Manual*을 참고한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_TRANSACTION_POOL_SIZE

##### 데이터 타입

Unsigned Integer

##### 기본값

2

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

이 프로퍼티는 트랜잭션 풀에 미리 생성해 두는 트랜잭션의 개수를 지정한다. 이중화 수신자는 데이터를 복제할 때 트랜잭션을 사용한다. 그리고 성능 향상을 위해 이중화 수신자 별로 트랜잭션 풀(pool)을 만들고, 이 곳에 트랜잭션들을 미리 생성해 두고 사용할 수 있다.

만약 풀에 존재하는 트랜잭션의 수가 부족하다면, 이중화 수신자는 새로운 트랜잭션을 생성하여 이를 사용할 것이다. 그리고 사용이 끝난 트랜잭션은 풀에 반환되는데, 이 때 존재하는 트랜잭션의 개수가 이 프로퍼티에 지정된 값보다 크면, 풀에 반환되지 않고 바로 해제된다.

이 값을 너무 크게 지정하면, 일반 트랜잭션의 개수에 제한을 줄 수 있으므로 적절한 값으로 설정해야 한다. 이 프로퍼티에 허용된 최대값은 232-1이지만, 실제 최대값은 TRANSACTION_TABLE_SIZE 프로퍼티에 지정한 값과 같다. 만약 사용자가 이 값을 TRANSACTION_TABLE_SIZE의 값보다 크게 지정하면, 내부적으로 이 프로퍼티의 값이 TRANSACTION_TABLE_SIZE의 값으로 설정된다.

Altibase 구동 중에 이 프로퍼티의 값을 변경할 수 있다. 하지만 이중화 수신 쓰레드 생성시 트랜잭션 풀이 초기화되므로, 이중화를 재시작해야 변경된 프로퍼티의 값이 적용된다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_UPDATE_REPLACE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

이중화 작업중 변경작업 충돌(update conflict) 시 변경된 내용의 반영을 결정한다. 값이 0 이면 충돌이 있을 경우 반영하지 않고 오류 처리하며, 1 일 경우 충돌을 무시하고 반영한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_META_ITEM_COUNT_DIFF_ENABLE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

Lazy 모드로 이중화 수행 과정에서 SPLIT PARTITION과 MERGE PARTITION, DROP PARTITION을 수행하여 Active 서버와 Standby 서버의 이중화 테이블 파티션 메타 아이템 개수가 다른 경우에 이중화를 START 할 수 있는 프로퍼티이다. 이 값을 1로 설정하면 이중화 테이블 파티션 메타 아이템 개수가 다른 경우에도 이중화를 START 할 수 있다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

### 네트워크 관련 프로퍼티

#### IB_CONCHKSPIN

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2147483]

##### 설명

rsocket의 RDMA_CONCHKSPIN 옵션 값을 설정한다. 인피니밴드의 연결 확인을 어느 주기로 할 것인지 설정하는 값이다. 이 값이 0이면 rsocket의 기본값을 사용한다.

이 프로퍼티는 Altibase rdma-core ( https://github.com/ALTIBASE/rdma-core )를 사용할 때에만 사용할 수 있다.

#### IB_ENABLE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

Altibase에서 인피니밴드(InfiniBand, IB)의 사용 여부를 설정한다. 이 기능은 Linux에서만 사용할 수 있다.

0 : IB사용하지 않음 (기본값)

1: IB사용

#### IB_LATENCY

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

rsocket의 RDMA_LATENCY 옵션 값을 설정한다.

이 프로퍼티의 값이 1이면 CPU 자원을 더 소모하더라도, 대기 시간을 줄이기 위하여 튜닝 코드를 사용한다.

이 프로퍼티는 Altibase rdma-core ( https://github.com/ALTIBASE/rdma-core )를 사용할 때에만 사용할 수 있다.

#### IB_LISTENER_DISABLE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

Altibase를 시작할 때 인피니밴드 리스너(InfiniBand Listener)의 시작 여부를 설정할 수 있다.

0: 인피니밴드 리스너 시작(기본값)

1: 인피니밴드 리스너 시작하지 않음

#### IB_MAX_LISTEN

##### 데이터 타입

Unsigned Integer

##### 기본값

128

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1024]

##### 설명

인피니밴드(InfiniBand, IB)로 접속하여 동시에 Altibase를 사용할 수 있는 클라이언트의 최대 숫자이다.

#### IB_PORT_NO

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1024, 65535]

##### 설명

인피니밴드(InfiniBand, IB)를 이용하여 통신하기 위해 사용하는 포트 번호이다.

#### SNMP_ALARM_QUERY_TIMEOUT

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

세션에서 쿼리 타임아웃이 발생했을 때 트랩을 보낼지 여부를 결정한다. 디폴트 값은 1이며 트랩을 보낸다. 자세한 내용은 SNMP Agent Guide의 altiPropertyAlarmQueryTimeout를 참고하기 바란다.

#### SNMP_ALARM_FETCH_TIMEOUT

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

FETCH TIMEOUT이 발생했을 때 트랩을 보낼지 여부를 결정한다. 기본값은 1이며 트랩을 보낸다. 자세한 내용은 SNMP Agent Guide의 altiPropertyAlarmFetchTimeout를 참고하기 바란다.

#### SNMP_ALARM_UTRANS_TIMEOUT

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

UTRANS TIMEOUT이 발생했을 때 트랩을 보낼지 여부를 결정한다.

0: 트랩을 발생시키지 않는다.

1: 트랩을 발생시킨다.

자세한 내용은 SNMP Agent Guide의 altiPropertyAlarmUtransTimeout를 참고하기 바란다.

#### SNMP_ALARM_SESSION_FAILURE_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

3

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

세션에서 연속으로 프로퍼티에 설정한 횟수만큼 오류가 발생했을 때 트랩을 보낸다. 기본값은 3이고, 0이면 트랩을 보내지 않는다. 자세한 내용은 SNMP Agent Guide의 altiPropertyAlarmSessionFailureCount를 참고하기 바란다.

#### SNMP_ENABLE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

SNMP 서비스를 사용하기 위해서는 1 (Enable)로 설정해야 한다. 기본값은 0 (Disable)이다.

0 : SNMP 사용

1: SNMP 사용하지 않음

#### SNMP_MSGLOG_FLAG

##### 데이터 타입

Unsigned Integer

##### 기본값

3

##### 속성

변경 가능, 단일 값

##### 값의 범위

[3, 12]

##### 설명

로그 출력의 레벨(Level)을 설정한다. 레벨은 '1', '2', '4', '8' 4가지가 있으며 각각의 합으로 설정된다. 기본값은 3(1 + 2)이며, 레벨이 Level1, Level3가 되면 관련된 로그가 출력된다.

#### SNMP_PORT_NO

##### 데이터 타입

Unsigned Integer

##### 기본값

20400

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1024, 65535]

##### 설명

Altibase와 altisnmpd(Altibase sub agent)간에 통신을 하기 위해 사용되는 UDP 포트이다.

#### SNMP_TRAP_PORT_NO

##### 데이터 타입

Unsigned Integer

##### 기본값

20400

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1024, 65535]

##### 설명

Altibase와 altisnmpd(Altibase sub agent)간에 트랩을 보내기 위해 통신을 하는 UDP 포트이다.

#### SNMP_RECV_TIMEOUT (단위 : 밀리세크초)

##### 데이터 타입

Unsigned Integer

##### 기본값

1000

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 232-1]

##### 설명

통신을 사용하기 위한 타임아웃 값이다.

Altibase와 altisnmpd(Altibase sub agent)간에 통신을 할 때 이 프로퍼티에 설정한 값만큼 대기한다.

#### SNMP_SEND_TIMEOUT (단위 : 밀리세크초)

##### 데이터 타입

Unsigned Integer

##### 기본값

100

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 232-1]

##### 설명

통신을 사용하기 위한 타임아웃 값이다.

Altibase와 altisnmpd(Altibase sub agent)간에 통신을 할 때 이 프로퍼티에 설정한 값만큼 대기한다.

#### SSL_CA

##### 데이터 타입

String

##### 기본값

없음

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

CA 인증서의 소유권을 인정받기 위해서 CA 인증서를 저장하는 파일의 경로를 지정할 수 있다. CA 인증서 파일은 사용자 지정 경로나 X.509 형식의 디렉토리에 위치한다. 예를 들어 $ALTIBASE_HOME/cert/ ca-cert.pem으로 할 수 있다.

#### SSL_CAPATH

##### 데이터 타입

String

##### 기본값

없음

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

CA 디렉토리 형식의 CAPATH를 지정할 수 있다. 예를 들어서, 지정할 경우 $ALTIBASE_HOME/etc/ssl/certs로 할 수 있다.

#### SSL_CERT

##### 데이터 타입

String

##### 기본값

없음

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

Altibase 서버의 인증서 파일 경로를 지정한다. 예를 들어 $ALTIBASE_HOME/cert/server-cert.pem으로 지정할 수 있다.

#### SSL_CIPHER_LIST

##### 데이터 타입

String

##### 기본값

없음

##### 속성

읽기 전용, 단일 값

##### 값의 범위

255

##### 설명

이 프로퍼티는 Altibase가 클라이언트와 협의하여 사용할 수 있는 암호 알고리즘의 이름 후보들이다. 암호 알고리즘은 사용자의 보안 정책에 따라 하나 또는 그 이상의 암호를 사용할 수 있다. 두 개 이상의 암호를 사용할 경우 콜론(:)으로 구분한다. 사용자가 사용할 수 있는 암호 목록은 OpenSSL( [http://www.openssl.org](http://www.openssl.org/)/ )에서 확인하거나 아래처럼 명령어를 사용하여 확인할 수 있다.

```
$ openssl ciphers
```

#### SSL_CLIENT_AUTHENTICATION

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

서버와 클라이언트가 SSL로 통신을 할 때 클라이언트에게 인증서를 요청할 것인지를 설정할 수 있다. 기본값이 0일 때에는 클라이언트가 서버만 인증서를 통해 확인하다. 이 값을 1로 하면, 서버는 SSL 핸드쉐이크중에 클라이언트에게 인증서를 요청한다.

0: 서버만 인증(기본값)

1: 서버와 클라이언트 동시 인증

#### SSL_ENABLE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

Altibase가 SSL/TLS를 이용할지 여부를 설정할 수 있다. 기본값은 0 (Disable)이다.

0 : SSL/TLS 사용하지 않음

1: SSL/TLS 사용

#### SSL_KEY

##### 데이터 타입

String

##### 기본값

없음

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

Altibase 서버의 개인 키(private key)가 저장된 파일 경로를 지정한다.

예를 들어 $ALTIBASE_HOME/cert/server-key.pem으로 지정할 수 있다.

#### SSL_MAX_LISTEN

##### 데이터 타입

Unsigned Integer

##### 기본값

128

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 16384]

##### 설명

SSL/TLS로 접속하여 동시에 Altibase를 사용할 수 있는 대기 큐(listen queue)의 최대 크기를 지정한다. 이 값이 클수록 Altibase에 더 많은 메모리가 필요하다.

#### SSL_PORT_NO

##### 데이터 타입

Unsigned Integer

##### 기본값

20443

##### 속성

변경 가능, 단일 값

##### 값의 범위

[1024, 65535]

##### 설명

서버와 클라이언트가 SSL/TLS를 이용하여 통신하기 위해 사용되는 포트번호를 설정한다.

#### TCP_ENABLE

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

Altibase 서버가 통신 프로토콜로 TCP/IP를 선택하여 통신할 것인지를 설정할 수 있다.

0 : TCP/IP 사용하지 않음

1: TCP/IP 사용

### 메시지 로그 관련 프로퍼티

#### ALL_MSGLOG_FLUSH

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

이 값이 1인 경우 데이터베이스의 모든 메시지가 기록 즉시 디스크에 반영되고 0인 경우에는 일정 주기에 한 번씩 디스크에 반영된다. 과도한 로깅으로 인한 성능저하를 예방하기 위해서는 0으로 설정하는 것이 적절하고, 데이터베이스 문제 진단 시에는 1로 설정하고 작업한다.

#### COLLECT_DUMP_INFO

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

서버가 비정상 종료할 때 메시지 파일과 로그 파일 등의 정보를 수집할 것인지 여부를 지정한다.

0: 메시지 파일과 로그 파일의 정보를 수집하지 않음

1: 메시지 파일과 로그 파일의 정보를 수집함

#### DK_MSGLOG_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

10

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

데이터베이스 링크를 할 때 연결 프로세스에 지정할 수 있는 메시지 파일의 최대 개수를 설정한다.

#### DK_MSGLOG_FILE

##### 데이터 타입

String

##### 기본값

altibase_lk.log

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

데이터베이스 링크가 연결 프로세스 처리 과정에서 발생하는 메시지를 기록되는 파일이다.

#### DK_MSGLOG_FLAG

##### 데이터 타입

Unsigned Integer

##### 기본값

6

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

데이터베이스 링크의 연결 프로세스 모듈에서 발생하는 경고 메시지나 추적 메시지를 LK_MSGLOG_FILE에 기록할 것인지 여부를 나타내는 플래그 값이다.

0이면 기록하지 않고, 0보다 큰값이면 기록한다.

#### DK_MSGLOG_SIZE

##### 데이터 타입

Unsigned Integer

##### 기본값

10 * 1024 * 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

데이터베이스 링크에서 연결 프로세스의 메시지 파일 최대 크기를 지정한다.

#### DUMP_MSGLOG_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

10

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

서버 오류에 대한 디버깅 정보가 기록되는 메시지 파일의 최대 개수를 지정한다.

#### DUMP_MSGLOG_FILE

##### 데이터 타입

String

##### 기본값

altibase_dump.log

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

서버 오류에 대한 디버깅 정보가 기록되는 메시지 파일명을 지정한다.

#### DUMP_MSGLOG_SIZE (단위 : 바이트)

##### 데이터 타입

Unsigned Integer

##### 기본값

10 * 1024 * 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

디버깅 정보가 기록되는 메시지 파일의 최대 크기를 지정한다.

#### ERROR_MSGLOG_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

10

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

서버 오류 메시지 파일의 최대 개수를 지정한다.

#### ERROR_MSGLOG_FILE

##### 데이터 타입

String

##### 기본값

altibase_error.log

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

서버에서 발생하는 오류 메시지를 기록할 파일명을 지정한다. Altibase 서버 비정상 종료시 프로세스의 콜 스택도 이 파일에 기록된다.

#### ERROR_MSGLOG_SIZE (단위 : 바이트)

##### 데이터 타입

Unsigned Integer

##### 기본값

10 * 1024 * 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

서버 오류 메시지가 저장되는 파일의 최대 크기를 지정한다.

#### LB_MSGLOG_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

10

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

서비스 쓰레드 관련 메시지 파일의 최대 개수를 설정한다.

#### LB_MSGLOG_FILE

##### 데이터 타입

String

##### 기본값

altibase_lb.log

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

서비스 쓰레드 관련 메시지를 기록하는 파일이다.

#### LB_MSGLOG_FLAG

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

LB_MSGLOG_FILE에 기록될 서비스 쓰레드 관련 메시지 항목을 지정한다.

0: 기록하지 않음

1: 서비스 쓰레드의 생성 및 해제

2: Task 이동에 대한 로그

3: 서비스 쓰레드의 생성 및 해제, Task 이동에 대한 로그

#### LB_MSGLOG_SIZE

##### 데이터 타입

Unsigned Integer

기본값

10 * 1024 * 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

서비스 쓰레드 관련 메시지가 기록되는 파일의 최대 크기를 지정한다.

#### MM_MSGLOG_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

10

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

메인 모듈을 위한 메시지 파일의 최대 개수를 지정한다.

#### MM_MSGLOG_FILE

##### 데이터 타입

String

##### 기본값

altibase_mm.log

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

메일 모듈 처리 시에 발생하는 메시지가 기록되는 파일이다.

#### MM_MSGLOG_SIZE(단위 : 바이트)

##### 데이터 타입

Unsigned Integer

##### 기본값

10 * 1024 * 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

메인 모듈의 메시지 파일의 최대 크기를 지정한다.

#### MM_SESSION_LOGGING

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

데이터베이스 서버에 대한 모든 로그온, 로그오프 이벤트를 발생시키는 세션 정보를 MM_MSGLOG_FILE에 기록할 지 여부를 지정한다. 세션 정보는 세션 ID, 사용자 이름, 클라이언트 IP 주소, 클라이언트 프로그램의 PID, 그리고 클라이언트 프로그램에 대한 세부 정보를 포함한다.

#### NETWORK_ERROR_LOG

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

서버 메시지 파일에 네트워크 관련 에러 메시지의 출력 여부를 지정한다.

네트워크 환경이 불안정하여 에러 메시지의 출력이 많을 때 0으로 설정하면, 네트워크 관련 에러 메시지의 출력을 막을수 있다.

#### QP_MSGLOG_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

10

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

질의 처리기 메시지 파일의 최대 개수를 지정한다.

#### QP_MSGLOG_FILE

##### 데이터 타입

String

##### 기본값

altibase_qp.log

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

질의 연산 (Query Processing) 처리 시에 발생하는 메시지가 기록되는 파일이다.

#### QP_MSGLOG_FLAG

##### 데이터 타입

Unsigned Integer

##### 기본값

2

##### 속성

변경가능, 단일 값

##### 값의 범위

[0, 232 –1]

##### 설명

쿼리 프로세싱 모듈에서 발생하는 경고 메시지나 트레이스 메시지를 QP_MSGLOG_FILE에 기록 할지 여부를 나타내는 플래그 값이다.

0이면 기록하지 않고, 0 보다 큰값이면 기록한다.

#### QP_MSGLOG_SIZE(단위 : 바이트)

##### 데이터 타입

Unsigned Integer

##### 기본값

10 * 1024 * 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

질의 처리기 메시지 파일의 최대 크기를 지정한다.

#### QUERY_PROF_FLAG

##### 데이터 타입

Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 26-1]

##### 설명

서버 내에서 수행되는 작업과 서버의 상태 정보를 파일로 기록하여 분석할 수 있도록 한다. 사용자는 값을 조합하여 원하는 정보를 기록하도록 설정할 수 있으며, 값에 따라서 기록되는 정보는 다음과 같다.

- 0 : 기록하지 않음
- 1 : SQL 문이 실행될 때마다 실행된 SQL문, 실행시간, 실행정보, 색인 및 디스크 접근 정보 출력. 단, 실행시간이 제대로 출력되게 하려면 TIMED_STATISTICS 프로퍼티를 1로 설정해야 한다.
- 2 : SQL 문이 실행될 때마다 BIND 파라미터 출력
- 4 : SQL 문이 실행될 때마다 실행계획 출력
- 8 : 3초마다 세션 정보 출력 (V$SESSTAT 의 데이터)
- 16 : 3초마다 시스템 정보 출력 (V$SYSSTAT 의 데이터)
- 32 : 3초마다 메모리 정보 출력 (V$MEMSTAT 의 데이터)

예를 들어 프로퍼티를 1+4+32=37로 설정하면, SQL 문이 실행될 때마다 SQL 문의 실행 정보와 실행계획을 출력하고 3초마다 메모리 정보를 출력한다.

파일에 대한 분석은 altiProfile 유틸리티로 가능하며, 자세한 설명은 *Utilities Manual의 유틸리티*를 참조한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### QUERY_PROF_LOG_DIR

##### 데이터 타입

String

##### 기본값

$ALTIBASE_HOME/trc

##### 속성

변경 가능, 단일 값

##### 값의 범위

[1, 1024 ]

##### 설명

Altibase에서 수행된 작업과 서버의 상태 정보가 기록되는 파일이 위치할 디렉토리 경로를 지정한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### RP_CONFLICT_MSGLOG_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

10

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

이중화 충돌시 트레이스 로그가 기록되는 파일의 최대 개수를 지정한다.

#### RP_CONFLICT_MSGLOG_DIR

##### 데이터 타입

String

##### 기본값

$ALTIBASE_HOME/trc

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

이중화 충돌이 발생할 때 트레이스 로그가 기록되는 파일이 위치할 디렉토리를 지정한다.

#### RP_CONFLICT_MSGLOG_ENABLE

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

이중화 충돌에 대한 트레이스 로그를 기록할 것인지 여부를 지정한다.

#### RP_CONFLICT_MSGLOG_FILE

##### 데이터 타입

String

##### 기본값

altibase_rp_conflict.log

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

이중화 충돌에 대한 트레이스 로그가 기록되는 파일이다.

#### RP_CONFLICT_MSGLOG_FLAG

##### 데이터 타입

Unsigned Integer

##### 기본값

6

##### 속성

변경가능, 단일 값

##### 값의 범위

[0, 232 –1]

##### 설명

이중화 충돌과 관련된 트레이스 로그의 로깅 레벨을 지정한다.

설정 가능한 값은 아래와 같다:

2: 충돌 메시지 기록

4: 충돌을 유발한 SQL문 기록

6: 충돌 메시지와 충돌을 유발한 SQL문을 모두 기록

#### RP_CONFLICT_MSGLOG_SIZE(단위 : 바이트)

##### 데이터 타입

Unsigned Integer

##### 기본값

10 * 1024 * 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

이중화 충돌에 대한 트레이스 로그 파일의 최대 크기를 지정한다.

#### RP_MSGLOG_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

10

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

이중화 메시지 파일의 최대 개수를 지정한다.

#### RP_MSGLOG_FILE

##### 데이터 타입

String

##### 기본값

altibase_rp.log

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

복제 관리자 (Replication) 처리 과정에서 발생하는 메시지가 기록되는 파일이다.

#### RP_MSGLOG_FLAG

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경가능, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

복제 관리자(Replication Manager) 모듈에서 발생하는 경고 메시지나 트레이스 메시지를 RP_MSGLOG_FILE에 기록 할지 여부를 나타내는 플래그 값이다.

0이면 기록하지 않고, 0보다 큰 값이면 기록한다.

#### RP_MSGLOG_SIZE (단위 : 바이트)

##### 데이터 타입

Unsigned Integer

##### 기본값

10 * 1024 * 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

이중화 메시지 파일의 최대 크기를 지정한다.

#### SERVER_MSGLOG_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

10

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

서버 메시지 파일의 최대 개수를 지정한다.

#### SERVER_MSGLOG_DIR

##### 데이터 타입

String

##### 기본값

$ALTIBASE_HOME/trc

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

서버 구동 및 종료 등에 대한 시스템 정보가 기록되어 있는 서버 모듈의 메시지 파일인 SERVER_MSGLOG_FILE과 서버 관리 프로그램에서 사용하는 내부 파일인 altibase.lock이 위치할 경로이다.

또한, SM_MSGLOG_FILE, QP_MSGLOG_FILE, RP_MSGLOG_FILE 등과 같은 서버 모듈의 메시지 파일을 위한 기본 경로로 사용된다.

#### SERVER_MSGLOG_FILE

##### 데이터 타입

String

##### 기본값

altibase_boot.log

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

서버 모듈에 대한 메시지를 남기는 파일명을 지정한다.

Altibase의 구동 및 경고, 비정상 종료 시에 출력되는 메시지를 기록하는 파일이다.

#### SERVER_MSGLOG_FLAG

##### 데이터 타입

Unsigned Integer

##### 기본값

7

##### 속성

변경가능, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

서버 모듈에서 발생하는 경고 메시지나 트레이스 메시지를 SERVER_MSGLOG_FILE에 기록 할지 여부를 나타내는 플래그 값이다.

0이면 기록하지 않고, 0 보다 큰 값이면 기록한다.

#### SERVER_MSGLOG_SIZE(단위 : 바이트)

##### 데이터 타입

Unsigned Integer

##### 기본값

10 * 1024 * 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

서버 메시지 파일의 최대 크기를 지정한다.

#### SM_MSGLOG_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

10

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

저장 관리자 메시지 파일의 최대 개수를 지정한다.

#### SM_MSGLOG_FILE

##### 데이터 타입

String

##### 기본값

altibase_sm.log

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

저장 관리자(Storage Manager) 처리 과정에서 발생하는 메시지가 기록되는 파일이다.

#### SM_MSGLOG_FLAG

##### 데이터 타입

Unsigned Integer

##### 기본값

2147483647

##### 속성

변경가능, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

저장 관리자(Storage Manager)모듈에서 발생하는 경고 메시지나 트레이스 메시지를 SM_MSGLOG_FILE에 기록 할지 여부를 나타내는 플래그 값이다. 0이면 기록하지 않고, 0보다 큰값이면 기록한다.

#### SM_MSGLOG_SIZE(단위 : 바이트)

##### 데이터 타입

Unsigned Integer

##### 기본값

10 * 1024 * 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

저장 관리자 메시지 파일의 최대 크기를 지정한다.

#### TRCLOG_DETAIL_PREDICATE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

Isql에서 Explain plan 기능 사용 시 where 절의 predicate 분류 상태를 나타낸다. 이 trace log를 사용하기 위해 1을 설정한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### XA_MSGLOG_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

10

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 232–1]

##### 설명

서버용 XA 메시지 파일의 최대 개수를 지정한다.

#### XA_MSGLOG_FILE

##### 데이터 타입

String

##### 기본값

altibase_xa.log

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

서버용 XA 메시지 로그가 기록되는 파일이다.

#### XA_MSGLOG_FLAG

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경가능, 단일 값

##### 값의 범위

[0, 3]

##### 설명

서버용 XA 메시지 로그의 기록 단계를 설정하는 속성으로 설정값은 다음과 같다.

0: XA 관련 최소 필수 메시지만 기록

1: XA 연산 호출을 기록

2: XID 할당, 해제 등을 기록함

3: XA 관련 모든 메시지 로그를 기록함

#### XA_MSGLOG_SIZE

##### 데이터 타입

Unsigned Integer

##### 기본값

10 * 1024 * 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 232–1]

##### 설명

서버용 XA 메시지 파일의 최대 크기를 지정한다.

### 데이터베이스 링크 관련 프로퍼티

#### DBLINK_ALTILINKER_CONNECT_TIMEOUT(단위: 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

100

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

Altibase 서버에서 AltiLinker로 접속할 때, 접속 대기 최대 시간을 지정한다.

#### DBLINK_DATA_BUFFER_ALLOC_RATIO

##### 데이터 타입

Unsigned Integer

##### 기본값

50

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

데이터베이스 링크로 원격 서버에서 수행한 질의의 결과 집합을 로컬 서버가 가져와서 저장하는 공간을 데이터베이스 링크 전용 데이터 버퍼라고 한다. 이 프로퍼티는 데이터베이스 링크 전용 데이터 버퍼의 남은 공간에서 원격 질의별로 할당 받을 record buffer의 비율을 지정한다.

#### DBLINK_DATA_BUFFER_BLOCK_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

128

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 212-1]

##### 설명

데이터베이스 링크를 위해 원격 서버에서 수행한 질의의 결과 집합을 로컬 서버에서 받아와서 저장하는 공간을 데이터 버퍼라고 한다. 이 프로퍼티는 데이터 버퍼를 구성하는 메모리 블럭(record buffer block)의 초기 할당 개수를 지정한다. 데이터 버퍼의 크기는 DBLINK_DATA_BUFFER_BLOCK_COUNT * DBLINK_DATA_BUFFER_BLOCK_SIZE가 될 것이다..

#### DBLINK_DATA_BUFFER_BLOCK_SIZE (단위: 바이트)

##### 데이터 타입

Unsigned Integer

##### 기본값

2 MBytes

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 29]

##### 설명

데이터베이스 링크를 위해 원격 서버에서 수행한 질의의 결과 집합을 로컬 서버에서 받아와서 저장하는 공간을 데이터 버퍼라고 한다. 이 프로퍼티는 데이터 버퍼를 구성하는 메모리 블럭(record buffer block)의 크기를 지정한다.

#### DBLINK_ENABLE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

데이터베이스 링크 사용 여부를 결정한다. 데이터베이스 링크를 사용하고자 할 때는 이 값을 1로 설정한다. 값이 0이면 데이터베이스 링크를 사용할 수 없다.

#### DBLINK_GLOBAL_TRANSACTION_LEVEL

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 2]

##### 설명

글로벌 트랜잭션 수행 레벨을 지정한다. 이 프로퍼티를 0으로 설정할 경우, DBLINK_REMOTE_STATEMENT_AUTOCOMMIT 프로퍼티를 원격 데이터베이스의 AUTOCOMMIT 모드와 동일하게 지정해야 한다.

0: remote statement execution level. 이 레벨에서는 하나의 글로벌 트랜잭션에 참여하는 서버들(로컬 및 원격 서버)의 각 트랜잭션이 별개의 트랜잭션으로 인식되므로, 글로벌 트랜잭션을 커밋하기 위해서는 각 서버의 트랜잭션을 별도로 commit해 주어야 한다. 즉, 이 레벨에서는 글로벌 트랜잭션이라 하더라도 로컬 서버에서 수행하는 commit이 원격 서버에 영향을 미치지 않는다.

1: simple transaction commit level. 이 레벨에서는 하나의 글로벌 트랜잭션에 참여하는 서버들(로컬 및 원격 서버)의 모든 트랜잭션이 하나의 트랜잭션으로 인식된다. 즉, 로컬 서버에서 글로벌 트랜잭션을 커밋하면 해당 트랜잭션에 참여하는 모든 트랜잭션들이 커밋된다.

2:Two-Phase Commit (2PC) Level. 이 레벨에서는 하나의 글로벌 트랜잭션에 참여하는 데이터베이스 시스템의 트랜잭션 정합성을 보장하기 위해 2PC 프로토콜을 지원한다. 글로벌 트랜잭션이 시작되면 트랜잭션이 종료할 때까지 이 프로퍼티 값을 변경 할 수 없다.

#### DBLINK_RECOVERY_MAX_LOGFILE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[1, 232-1]

##### 설명

이 프로퍼티는 트랜잭션 수행 중에 이기종 데이터베이스 시스템에 장애가 발생할 경우, 알티베이스가 분산 트랜잭션 복구를 위해 유지하는 로그 파일의 최대 개수이다. 이 프로퍼티 값이 0이면 분산 트랜잭션 복구를 위한 로그를 삭제하지 않아 정합성이 보장된다. 그러나 프로퍼티 값을 1보다 큰 값으로 설정하면, 로그 파일의 개수가 초과할 경우에 분산 트랜잭션이 완료되지 않더라도 체크포인트에 의해 로그가 삭제되므로 정합성을 보장할 수 없다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### DBLINK_REMOTE_STATEMENT_AUTOCOMMIT

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

원격 데이터베이스의 AUTOCOMMIT 모드를 지정한다.

DBLINKE_GLOBAL_TRANSACTION_LEVEL을 0으로 설정한 경우에만 이 프로퍼티가 적용된다.

0: autocommit-off

1: autocommit-on

#### DBLINK_REMOTE_TABLE_BUFFER_SIZE (단위 : MB)

##### 데이터 타입

Unsigned Integer

##### 기본값

50

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

REMOTE_TABLE 키워드를 사용하여 원격 서버에서 질의를 수행하면, 질의 결과를 임시로 저장할 수 있는 메모리 버퍼이다.

저장된 질의 결과는 질의 처리기에 전달된 후 삭제된다. 그러나 결과 집합중의 하나의 레코드가 이 프로퍼티에 지정한 크기보다 크면 저장할 수 없으므로, 프로퍼티의 값을 조정해야 한다.

### 감사 관련 프로퍼티

#### AUDIT_FILE_SIZE (단위: 바이트)

##### 데이터 타입

Unsigned Int

##### 기본값

100M

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

감사된 구문의 정보가 기록되는 바이너리 파일의 크기를 바이트 단위로 지정한다. 이 프로퍼티는 AUDIT_OUTPUT_METHOD 프로퍼티의 값이 0일 때 적용된다.

Altibase 운영 중에는 아래와 같이 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

```
ALTER SYSTEM SET AUDIT_FILE_SIZE=10000;
```

단, 서버가 auditing을 수행 중이라면 다음 생성되는 파일부터 변경된 크기가 적용된다. 만약 프로퍼티의 변경을 바로 적용하려면 ALTER SYSTEM STOP AUDIT과 ALTER SYSTEM START AUDIT 구문으로 auditing을 재시작하라.

#### AUDIT_LOG_DIR

##### 데이터 타입

String

##### 기본값

$ALTIBASE_HOME/trc

##### 속성

변경 가능, 다중값

##### 값의 범위

없음

##### 설명

감사된 구문 정보가 기록되는 바이너리 파일이 생성될 디렉토리를 지정한다. 이 프로퍼티는 AUDIT_OUTPUT_METHOD 프로퍼티의 값이 0일 때 적용된다.

Altibase 운영 중에는 아래와 같이 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

```
ALTER SYSTEM SET AUDIT_LOG_DIR='/tmp';
```

단, 서버가 auditing을 수행 중이라면 다음 생성되는 파일부터 변경된 디렉토리가 적용된다. 만약 프로퍼티의 변경을 바로 적용하려면 ALTER SYSTEM STOP AUDIT과 ALTER SYSTEM START AUDIT 구문으로 auditing을 재시작하라.

#### AUDIT_OUTPUT_METHOD

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 불가, 단일값

##### 값의 범위

[0, 9]

##### 설명

감사된 구문 정보가 기록되는 파일의 형태를 지정한다. Altibase는 감사 정보를 바이너리 또는 시스로그(syslog)로 저장할 수 있다. 단 syslog는 리눅스 운영체제에서만 지원한다.

기본값을 설정한 경우 감사된 정보가 바이너리 형태로 AUDIT_LOG_DIR 프로퍼티에서 지정한 디렉토리에 저장된다. 1~9의 값을 설정한 경우, syslog를 사용해서 syslog.conf(또는 rsyslog.conf)에 로그가 쌓이게 된다. syslog의 순서는 syslog.conf 파일의 LOG_INFO를 사용한다.

0: 바이너리 파일로 AUDIT_LOG_DIR 프로퍼티에서 지정한 디렉토리에 저장

1: user 퍼실리티를 /var/log/messages에 저장. 파일명은 시스템 설정시 변경 가능.

2: 사용자 정의에 따라 local0 facility에 저장

3: 사용자 정의에 따라 local1 facility에 저장

4: 사용자 정의에 따라 local2 facility에 저장

5: 사용자 정의에 따라 local3 facility에 저장

6: 사용자 정의에 따라 local4 facility에 저장

7: 사용자 정의에 따라 local5 facility에 저장

8: 사용자 정의에 따라 local6 facility에 저장

9: 사용자 정의에 따라 local7 facility에 저장

#### AUDIT_TAG_NAME_IN_SYSLOG

##### 데이터 타입

String

##### 기본값

AUDIT

##### 속성

변경 불가, 단일값

##### 값의 범위

없음

##### 설명

시스로그(syslog)를 사용해서 감사된 구문의 정보를 기록할 때 구분자로 "AUDIT" 태그가 사용된다.

### 에이전트 관련 프로퍼티

#### EXTPROC_AGENT_CONNECT_TIMEOUT

##### 데이터 타입

Unsigned Integer

##### 기본값

60 초

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[5, 232-1]

##### 설명

사용자가 외부 프로시저를 호출할 때, Altibase가 외부 프로시저용 에이전트에 연결을 시도하는 최대 시간을 초 단위로 설정한다. 이 프로퍼티에 설정한 시간 동안 연결을 할 수 없다면 외부 프로시저 호출은 연결을 실패했다는 오류 메시지와 함께 종료된다. 연결이 맺어진 후의 외부 프로시저 호출은 이 프로퍼티 값의 영향을 받지 않는다.

#### EXTPROC_AGENT_CALL_RETRY_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

변경 가능, 단일 값

##### 값의 범위

[1, 10]

##### 설명

사용자가 외부 프로시저를 호출할 때, Altibase가 외부 프로시저용 에이전트 연결을 재시도하는 횟수를 설정한다.

Altibase는 에이전트 프로세스에 외부 에이전트가 있는지 확인한 후 사용할 수 있다. 그러나 사용하려는 외부 에이전트가 EXTPROC_AGENT_CONNECT_TIMEOUT 프로퍼티 값에 의해 타임아웃 되어 종료될 수 있다. 그러면 이 프로퍼티에서 설정한 횟수만큼 외부 에이전트에 연결을 재시도한다.

Altibase 운영 중에 ALTER SYSTEM 구문으로 이 프로퍼티 값을 변경할 수 있다.

#### EXTPROC_AGENT_IDLE_TIMEOUT

##### 데이터 타입

Unsigned Integer

##### 기본값

300 초

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[5, 232-1]

##### 설명

외부 프로시저용 에이전트 프로세스가 idle 상태로 대기하는 최대 시간을 초 단위로 설정한다. 사용자가 외부 프로시저를 호출했을 때 에이전트 프로세스가 idle 상태로 대기 중이라면, 에이전트 프로세스로의 연결 과정 없이 프로시저를 수행할 수 있어 응답 시간이 적게 걸릴 것이다. 그러나, 사용자의 외부 프로시저 호출이 없는데도 에이전트 프로세스가 종료하지 않고 대기하는 것은 자원 낭비가 될 수 있으므로 외부 프로시저의 호출 빈도가 높은 경우에만 대기 시간을 늘릴 것을 권장한다.

#### EXTPROC_AGENT_SOCKET_FILEPATH

##### 데이터 타입

String

##### 기본값

$ALTIBASE_HOME/trc

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

Altibase 서버가 외부 프로시저 에이전트(external procedure agent)와 통신하기 위해 생성하는 소켓 파일의 경로이다.

외부 프로시저를 사용하면, 세션이 외부 프로시저 에이전트를 생성하면서 socket_sessionID로 소켓 파일을 생성한다. 임의로 이 파일을 삭제하지 않도록 주의해야 한다.

생성된 소켓 파일은 세션이 정상적으로 종료할 때 자동으로 삭제된다.

### 사용자 계정 보안 관련 프로퍼티

#### CASE_SENSITIVE_PASSWORD

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

데이터베이스에서 사용자 암호의 대소문자를 구분할지 여부를 결정한다. 기본값은 대소문자를 구분하지 않는 0이며, 데이터베이스 내에서 사용자 암호가 대문자로 다뤄진다.

- 0: 대소문자 구분을 하지 않는다.
- 1: 대소문자 구분을 한다. 단, 사용자 생성 구문에서 암호를 큰따옴표(")로 묶은 경우에만 대소문자가 구분된다. 큰따옴표를 쓰지않은 암호는 대문자로 인식된다.

알티베이스 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### FAILED_LOGIN_ATTEMPTS

##### 데이터 타입

Unsigned Int

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1000]

##### 설명

로그인을 시도할 때 이 프로퍼티에 설정된 횟수 이상 실패하면, 해당 계정은 로그인이 불가능하다.

#### PASSWORD_LOCK_TIME

##### 데이터 타입

Unsigned Int

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 3650]

##### 설명

계정이 한 번 잠긴 후 다시 풀리기 위해 경과되어야 하는 날짜(단위: 일)를 지정한다.

#### PASSWORD_LIFE_TIME

##### 데이터 타입

Unsigned Int

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 3650]

##### 설명

계정의 패스워드가 유효한 기간(단위: 일)을 지정한다.

#### PASSWORD_GRACE_TIME

##### 데이터 타입

Unsigned Int

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 3650]

##### 설명

계정의 패스워드가 만료되는 시점 이후의 유예 기간(단위: 일)을 지정한다.

#### PASSWORD_REUSE_TIME

##### 데이터 타입

Unsigned Int

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 3650]

##### 설명

동일한 패스워드를 재사용하기 위해 경과해야 하는 기간(단위:일)을 지정한다. 즉, 여기에 설정한 기간이 지난 후에 동일한 패스워드를 재사용할 수 있다.

#### PASSWORD_REUSE_MAX

##### 데이터 타입

Unsigned Int

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1000]

##### 설명

동일한 패스워드를 재사용하기 위한 패스워드 변경 횟수를 지정한다. 즉, 여기에 설정한 횟수만큼 패스워드를 변경한 후에 동일한 패스워드를 재사용할 수 있다.

#### PASSWORD_VERIFY_FUNCTION

##### 데이터 타입

String

##### 기본값

""

##### 속성

읽기 전용, 단일 값

##### 값의 범위

최대 길이 40바이트

##### 설명

패스워드를 검증할 사용자 정의 콜백 함수(CALLBACK function)를 지정한다.

### 기타 프로퍼티

#### ACCESS_LIST

##### 형식

ACCESS_LIST = operation, address, mask, [limit]

##### 값의 범위

- operation ::= [PERMIT|DENY]
  검사 규칙과 일치하는 IP 패킷의 접근을 허용할 것인지 제한할 것인지 기술한다.

- address
  검사할 패킷의 IP 주소를 기술한다.

- mask
  명시한 주소값이 IPv4 주소 형식이면, 이것은 서브넷 마스크로, 패킷의 IP 주소 중, 특정 부분만 검사하도록 설정한다.
  명시한 주소값이 IPv6 주소 형식이면, 이것은 등록된 IPv6 주소들과 비교할 prefix비트의 길이를 나타낸다. 즉, 등록된 주소의 마스크 비트 길이에 해당하는 값이 접근하는 패킷의 IP 주소의 마스크 비트 길이에 해당하는 값과 일치한다면 접근이 허용된다.

- limit

  선택 입력 항목으로 ACCESS_LIST에 명시된 접속 가능한 IP 주소 영역에서 허용되는 최대 접속 세션 개수를 지정한다.

  limit 값을 입력하면 모든 접속 요청에 대해 limit 조건 검사를 수행한다. 따라서, 허용된 IP의 접속 요청도 limit 개수를 초과하면 접속을 허용하지 않는다. 값을 입력하지 않으면 limit 조건을 검사하지 않는다.

  운영 중 RELOAD ACCESS LIST로 ACCESS_LIST를 추가하면, 기존에 연결된 세션은 영향을 받지 않으며, 변경 이후 새로운 연결 요청에 대해서만 ACCESS_LIST 조건이 적용된다. 예를 들어 ACCESS_LIST에 limit값을 설정 후 RELOAD ACCESS LIST 수행하면, 적용 이후 새로운 연결에 대해서만 limit 값이 적용된다. 이런 경우, V$ACCESS_LIST 조회시 Limit 값보다 CONNECTED 값이 더 클 수도 있다.

##### 검사 규칙

```
IF 
BITXOR(BITAND(IP_패킷,mask), BITAND(address,mask)) = 0
THEN  일치
ELSE  불일치
```

##### 설명

Altibase에 접근하고자 하는 IP 패킷을 주소에 따라 접근을 제한하거나 허용할 수 있다. IP 패킷의 주소를 검사 규칙에 따라 검사하여, 일치하면 operation에 기술된 대로 허용 또는 제한하며 불일치하면 무시하고 다음 리스트를 검사한다.

IP 패킷의 주소를 여러 개가 지정될 경우 기술된 순서대로 검사한다. 일치하는 조건이 없을 경우, 접근이 허용된다.

만약 ACCESS_LIST_FILE 프로퍼티에 값을 기술하면 ACCESS_LIST 프로퍼티에 정의된 목록 대신 외부 파일의 목록을 사용할 수 있다. 외부 파일은 최대 1024개의 항목까지 사용할 수 있으며, 'ACCESS_LIST='는 생략하고 내용만 작성해야 한다.

##### 예제

IP 주소가 192.168.1.55인 패킷만 접근을 제한하고 나머지는 허용한다.

```
ACCESS_LIST = deny, 192.168.1.55, 255.255.255.255
```

192.168.3.*과 219.211.253.* 주소들은 접근을 허용하고 나머지는 모두 제한한다.

```
ACCESS_LIST = permit, 192.168.3.0, 255.255.255.0
ACCESS_LIST = permit, 219.211.253.0, 255.255.255.0
ACCESS_LIST = deny ,0.0.0.0, 0.0.0.0
```

로컬 호스트를 제외한 모든 IPv4, IPv6 주소들의 접근을 제한한다.

```
ACCESS_LIST = deny, 0.0.0.0, 0.0.0.0
ACCESS_LIST = deny, ::1, 1
ACCESS_LIST = deny, fe80::, 1
```

외부 파일에 검사할 IP 주소를 기술한다. 192.168.3.*과 fe80으로 시작하는 IPv6 주소를 제외한 모든 IP 주소의 접근을 제한한다.

```
permit, 192.168.3.0, 255.255.255.0
permit, fe80::, 16
deny, 0.0.0.0, 0.0.0.0
deny, ::1, 1
deny, fe80::, 1
```

192.168.3.17 주소의 세션 접근 허용 개수를 5개로 제한한다.

```
ACCESS_LIST = permit, 192.168.3.17, 255.255.255.255, 5
```

**ACCESS_LIST_FILE**

##### 데이터 타입

String

##### 기본값

없음

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

ACCESS_LIST가 외부 파일 경로를 참조할 때 설정한다. 파일명과 경로를 정확히 설정하지 않은 경우 서버를 구동할 수 없다. 외부 파일 경로는 절대경로를 지정해야 한다. 파일에 ACCESS_LIST를 기술할 때의 형식은 ACCESS_LIST 프로퍼티의 설명을 참조한다.

이 프로퍼티를 사용하지 않을 때에는 ACCESS_LIST 프로퍼티에 기술된 목록을 사용한다.

#### ADMIN_MODE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

이 프로퍼티는 관리자 모드로 접근하는 것만 허용한다.

0: OFF

1: ON

이 값을 1로 설정하면 관리자 모드로 활성화되어 SYS 또는 SYSTEM_ 사용자가 SYSDBA 옵션으로 서버와 연결을 맺어 작업을 할 수 있고 그 외 일반 사용자들은 연결 자체가 실패한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### ARITHMETIC_OPERATION_MODE

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

Altibase 서버의 산술 연산 모드를 설정하는 프로퍼티이다.

0: 서버가 정밀도 우선 산술 연산 모드로 동작한다. 이 모드에서는 서버가 FLOAT 또는 NUMERIC 타입을 주로 사용하여 산술 연산의 오차를 줄인다. 단, "성능 우선 산술 연산 모드"에 비해 처리 속도가 떨어질 수 있다.

1: 서버가 성능 우선 산술 연산 모드로 동작한다. 이 모드에서는 서버가 산술 연산 시 DOUBLE 타입을 주로 사용하여 성능을 높이지만, 상대적으로 오차가 발생할 수 있다.

#### CHECK_MUTEX_DURATION_TIME_ENABLE

##### 데이터 타입

Unsigned Integer

##### 기본 값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

MUTEX_DURATION_TIME을 확인할 것인지 여부를 설정한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

0: check disable

1: check enable

#### COERCE_HOST_VAR_IN_SELECT_LIST_TO_VARCHAR

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 32000]

##### 설명

이 프로퍼티는 select target list 절에 CAST 연산자 없이 호스트 변수를 사용할 수 있도록 해 준다.

이 프로퍼티를 1 이상의 값으로 설정하면, CAST 연산자 없이 사용된 호스트 변수에 대해서 Altibase 서버가 임의로 VARCHAR 타입으로 처리한다. 또한 설정된 값이 VARCHAR 타입의 크기(precision)가 된다.

이 프로퍼티의 값을 0으로 설정하면, CAST 연산자 없이 호스트 변수를 사용할 경우 에러가 발생한다.

#### DEFAULT_DATE_FORMAT

##### 데이터 타입

String

##### 기본값

DD-MON-RRRR

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

테이블의 칼럼 도메인 중 DATE 타입 데이터의 기본 형식을 지정한다. 이 타입은 날짜, 시간을 저장할 수 있는 형식으로 제공되어야 한다. 형식은 “DD MON RRRR” 과 같이 따옴표 내에 공백도 사용할 수 있다.

```
DEFAULT_DATE_FORMAT = YYYY/MM/DD
iSQL> select sysdate from dual;
SYSDATE
--------------
2008/06/16
1 row selected.
```

#### EXEC_DDL_DISABLE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

일반적으로 초기 데이터베이스를 구축한 이후에는 DML구문을 훨씬 더 빈번하게 수행하며 DDL 구문의 수행은 기존 데이터베이스 스키마를 변경시키는 작업이므로 상당한 주의를 요한다.

따라서 Altibase 운영 중 DDL구문을 수행하지 못하도록 운영자가 설정할 수 있으며 이 프로퍼티의 값을 1로 설정하면 Altibase 운영 중 DDL구문을 수행할 수 없으며 0인 경우 DDL구문을 수행할 수 있다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### GROUP_CONCAT_PRECISION

##### 데이터 타입

Unsigned Integer

##### 기본값

4000

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 32000]

##### 설명

이 프로퍼티는 GROUP_CONCAT 함수가 반환하는 VARCHAR 타입의 크기를 지정한다.

Altibase 운영 중에 ALTER SYSTEM 구문으로 이 프로퍼티의 값을 변경할 수 있다.

#### JOB_SCHEDULER_ENABLE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

작업 스케줄러의 동작을 제어한다. 이 프로퍼티의 값을 1로 설정하여도 JOB_THREAD_COUNT 프로퍼티가 0이면 작업 스케줄러가 동작하지 않는다.

0: JOB스케줄러가 JOB 실행을 종료한다.

1: JOB스케줄러가 JOB 실행을 시작한다.

Altibase 운영 중에 ALTER SYSTEM 구문으로 이 프로퍼티의 값을 변경할 수 있다.

#### JOB_THREAD_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 128]

##### 설명

이 프로퍼티는 JOB을 실행하기 위한 쓰레드를 서버 구동 시 몇 개 생성할 것인지를 지정한다. 이 값이 0일 경우 작업 스케줄러(JOB Scheduler)를 위한 쓰레드가 생성되지 않는다.

#### JOB_THREAD_QUEUE_SIZE

##### 데이터 타입

Unsigned Integer

##### 기본값

64

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[64, 1024]

##### 설명

이 프로퍼티는 JOB을 실행하기 위한 큐(Queue)를 서버 구동 시에 얼마나 생성할 것인지를 지정한다. 이 값이 크면, 동일 시간에 더 많은 JOB을 실행할 수 있다.

#### MSG_QUEUE_PERMISSION

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

메시지 큐의 접근 권한(permission type)을 설정한다. Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

0: (rw-rw-rw 0666) - 모든 사용자는 읽기와 쓰기만 할 수 있으며 실행하기는 할 수 없다.

1: (rw-r-r 0644) - 소유자는 읽기와 쓰기만 할 수 있으며, 그 외의 사용자는 읽기만 할 수 있다.

#### PSM_CHAR_DEFAULT_PRECISION

##### 데이터 타입

Unsigned Integer

##### 기본값

32767

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 65534]

##### 설명

아래와 같은 경우에 CHAR 타입의 크기를 명시하지 않으면 Altibase는 PSM_CHAR_DEFAULT_PRECISION 프로퍼티에 설정된 값을 CHAR크기로 결정한다.

- 저장 프로시저 생성시 데이터 타입이 CHAR인 파라미터의 크기를 명시하지 않을 때
- 저장 함수 생성시 데이터 타입이 CHAR인 파라미터 또는 반환 값의 크기를 명시하지 않을 때

#### PSM_IGNORE_NO_DATA_FOUND_ERROR

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

Altibase의 PSM에서 제공하는 시스템-정의 예외 중 NO_DATA_FOUND가 있다. 이 예외는 PSM(저장 프로시저 및 함수, 트리거) 내에 포함된 "SELECT ~ INTO" 구문이 실행될 때 결과 집합이 없으면 발생한다. PSM_IGNORE_NO_DATA_FOUND_ERROR 프로퍼티를 사용하면 저장 함수에 대해서는 NO_DATA_FOUND 예외가 발생하지 않도록 할 수 있다.

- 0: 결과 집합이 없는 경우에 NO_DATA_FOUND 예외가 발생한다.
- 1: 결과 집합이 없는 경우에 NO_DATA_FOUND 예외가 발생하지 않는다.

Altibase 운영 중에 ALTER SYSTEM 구문으로 이 프로퍼티의 값을 변경할 수 있다.

#### PSM_NCHAR_UTF16_DEFAULT_PRECISION

##### 데이터 타입

Unsigned Integer

##### 기본값

16383

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 32766]

##### 설명

Altibase 캐릭터 셋(character set)이 UTF16이고 아래와 같은 경우에 NCHAR타입의 크기를 명시하지 않으면 Altibase는 PSM_NCHAR_UTF16_DEFAULT_PRECISION 프로퍼티에 설정된 값을 NCHAR크기로 결정한다.

- 저장 프로시저 생성시 데이터 타입이 NCHAR인 파라미터의 크기를 명시하지 않을 때
- 저장 함수 생성시 데이터 타입이 NCHAR인 파라미터 또는 반환 값의 크기를 명시하지 않을 때

#### PSM_NCHAR_UTF8_DEFAULT_PRECISION

##### 데이터 타입

Unsigned Integer

##### 기본값

10921

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 21843]

##### 설명

Altibase 캐릭터 셋(character set)이 UTF8이고 아래와 같은 경우에 NCHAR타입의 크기를 명시하지 않으면 Altibase는 PSM_NCHAR_UTF8_DEFAULT_PRECISION 프로퍼티에 설정된 값을 NCHAR크기로 결정한다.

- 저장 프로시저 생성시 데이터 타입이 NCHAR인 파라미터의 크기를 명시하지 않을 때
- 저장 함수 생성시 데이터 타입이 NCHAR인 파라미터 또는 반환 값의 크기를 명시하지 않을 때

#### PSM_NVARCHAR_UTF16_DEFAULT_PRECISION

##### 데이터 타입

Unsigned Integer

##### 기본값

16383

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 32766]

##### 설명

Altibase 캐릭터 셋(character set)이 UTF16이고 아래와 같은 경우에 NVARCHAR타입의 크기를 명시하지 않으면 Altibase는 PSM_NVARCHAR_UTF16_DEFAULT_PRECISION 프로퍼티에 설정된 값을 NVARCHAR크기로 결정한다.

- 저장 프로시저 생성시 데이터 타입이 NVARCHAR인 파라미터의 크기를 명시하지 않을 때
- 저장 함수 생성시 데이터 타입이 NVARCHAR인 파라미터 또는 반환 값의 크기를 명시하지 않을 때

#### PSM_NVARCHAR_UTF8_DEFAULT_PRECISION

##### 데이터 타입

Unsigned Integer

##### 기본값

10921

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 21843]

##### 설명

Altibase 캐릭터 셋(character set)이 UTF8이고 아래와 같은 경우에 NVARCHAR타입의 크기를 명시하지 않으면 Altibase는 PSM_NVARCHAR_UTF8_DEFAULT_PRECISION 프로퍼티에 설정된 값을 NVARCHAR크기로 결정한다.

- 저장 프로시저 생성시 데이터 타입이 NVARCHAR인 파라미터의 크기를 명시하지 않을 때
- 저장 함수 생성시 데이터 타입이 NVARCHAR인 파라미터 또는 반환 값의 크기를 명시하지 않을 때

#### PSM_PARAM_AND_RETURN_WITHOUT_PRECISION_ENABLE

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0,1]

##### 설명

저장 프로시저를 생성할 때 파라미터의 크기를 정의하지 않았거나 저장 함수를 생성할 때 파라미터 및 반환 값의 데이터 크기를 정의하지 않았다면, 이 프로퍼티 값에 따라 사용할 수 있는 데이터 크기가 달라진다.

파라미터 또는 반환 값의 타입이 CHAR, NCHAR, NVARCHAR, VARCHAR 이고 이 프로퍼티의 값이 1이면, 데이터 타입의 크기는 아래의 프로퍼티에 설정한 값으로 결정된다. 그러나 이 값이 0으로 설정하면 데이터 타입의 크기는 1이다.

- PSM_CHAR_DEFAULT_PRECISION
- PSM_NCHAR_UTF8_DEFAULT_PRECISION
- PSM_NCHAR_UTF16_DEFAULT_PRECISION
- PSM_NVARCHAR_UTF8_DEFAULT_PRECISION
- PSM_NVARCHAR_UTF16_DEFAULT_PRECISION
- PSM_PARAM_AND_RETURN_WITHOUT_PRECISION_ENABLE
- PSM_VARCHAR_DEFAULT_PRECISION

#### PSM_VARCHAR_DEFAULT_PRECISION

##### 데이터 타입

Unsigned Integer

##### 기본값

32767

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 65534]

##### 설명

아래와 같은 경우에 VARCHAR 타입의 크기를 명시하지 않으면 Altibase는 PSM_VARCHAR_DEFAULT_PRECISION 프로퍼티에 설정된 값을 VARCHAR의 크기로 결정한다.

- 저장 프로시저 생성시 데이터 타입이 VARCHAR인 파라미터의 크기를 명시하지 않을 때
- 저장 함수 생성시 데이터 타입이 VARCHAR인 파라미터 또는 반환 값의 크기를 명시하지 않을 때

#### QUERY_STACK_SIZE (단위 : 개)

##### 데이터 타입

Unsigned Integer

##### 기본값

1024

##### 속성

변경 가능, 단일 값

##### 값의 범위

[8, 65536]

##### 설명

질의 수행 시 연산 및 비교 등의 연산자를 처리하기 위해 시스템 내부적으로 사용하는 스택의 크기를 설정하는 시스템 프로퍼티이다.

복잡한 연산식 또는 저장프로시저와 같이 많은 구문이 사용될 경우 stack overflow 오류가 날 수 있고 이 때 프로퍼티 값을 큰 값으로 변경해야 한다. 응용 프로그램 환경에 따라 적절한 값을 설정해야 하며 필요 이상 큰 값으로 설정할 경우 불필요한 메모리 공간 낭비가 될 수 있으므로 유의해야 한다.

이 프로퍼티는 altibase.properties 파일내에 명시할 수 있으며 ALTER SYSTEM 또는 ALTER SESSION 명령문으로 변경할 수 있다.

ALTER SESSION문으로 변경하는 경우 다음과 같이 값을 변경할 수 있다.

ALTER SESSION SET STACK SIZE = *n*;

#### RECURSION_LEVEL_MAXIMUM

##### 데이터 타입

Unsigned Integer

##### 기본값

1000

##### 속성

변경 가능, 단일 값

##### 값의 범위

[5, 232-1]

##### 설명

이 프로퍼티에 설정한 횟수(level) 만큼 재귀 질의를 반복하여 수행한다.

Altibase 운영 중 ALTER SESSION 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REMOTE_SYSDBA_ENABLE

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

SYS 사용자가 원격에서 SYSDBA 모드로 접속할 수 있는지 여부를 설정한다. ALTER SYSTEM 명령문으로 값을 변경할 수 있다.

0: 원격에서 SYSDBA 모드로 접속 불가

1: 원격에서 SYSDBA 모드로 접속 가능 (기본값)

#### SELECT_HEADER_DISPLAY

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

SELECT 쿼리의 결과 출력 시 iSQL 상에 칼럼 이름만 출력할 것인지, 테이블 이름과 함께 칼럼 이름을 출력할 것인지를 설정하는 시스템 프로퍼티이다.

이 프로퍼티는 altibase.properties 파일에 명시할 수 있으며 ALTER SYSTEM 또는 ALTER SESSION 명령문으로 변경할 수 있다. 값이 0인 경우 iSQL 상에서 결과 출력 시 테이블 이름과 칼럼 이름이 함께 출력된다.

#### SYS_CONNECT_BY_PATH_PRECISION

##### 데이터 타입

Unsigned Integer

##### 기본값

4000

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 32000]

##### 설명

이 프로퍼티는 SYS_CONNECT_BY_PATH_PRECISION 함수가 반환하는 VARCHAR 타입의 크기를 지정한다.

Altibase 운영 중에 ALTER SYSTEM 구문으로 이 프로퍼티의 값을 변경할 수 있다.

## 3.데이터 딕셔너리

Altibase의 데이터 딕셔너리는 데이터베이스 객체 정보를 저장하는 메타 테이블과 시스템 프로세스 정보를 저장하는 프로세스 테이블로 나뉘어진다. 프로세스 테이블은 다시 고정 테이블 (Fixed Table)과 성능 뷰 (Performance View)로 나뉘어진다.

본 장은 데이터베이스 객체 및 Altibase 시스템 정보를 제공하는 데이터 딕셔너리에 대해 설명한다.

### 메타 테이블

메타 테이블이란 데이터베이스에 생성된 객체에 대한 모든 정보를 저장하고 있는 시스템 정의 테이블이다.

이 절에서는 메타 테이블의 종류 및 그 구조, 그리고 메타 테이블의 조회 및 변경에 대하여 설명한다.

#### 구조 및 기능

메타 테이블은 데이터베이스 객체를 관리하기 위해 시스템에 의해 정의된 테이블이다. 메타 테이블의 데이터 타입 및 레코드 저장 형태는 사용자가 생성하는 일반 테이블과 동일하다.

Altibase는 구동시 데이터베이스 객체 정보를 로딩하고, DDL 문을 수행할 때 데이터베이스 객체 정보를 조회, 저장 및 변경하기 위해 메타 테이블을 사용한다.

메타 테이블의 소유자는 시스템 사용자 (SYSTEM_)로 일반 사용자는 메타 테이블에 대한 접근이 제한된다.

#### 메타 테이블 조회

DDL 문으로 데이터베이스 객체를 생성, 삭제 및 변경 시 메타 테이블의 레코드가 시스템에 의해 생성, 삭제 또는 변경된다.

DDL 문 수행 후, 변경된 데이터베이스 객체 정보는 메타 테이블을 조회함으로써 확인할 수 있다. 메타 테이블의 레코드는 일반 테이블과 같이 SELECT 문으로 조회가 가능하다.

#### 메타 테이블 데이터 변경

사용자는 시스템에서 정의된 시스템 사용자(SYSTEM_ ) 계정으로 DML문을 사용하여 메타 테이블의 데이터를 명시적으로 변경할 수 있다. 그러나 메타 테이블 정보가 변경되면 시스템 구동이 실패하거나, 데이터베이스 객체 정보를 상실하여 시스템에 치명적인 손상이 발생할 수 있다. 따라서 가급적 메타 테이블 데이터에 대한 사용자의 명시적인 변경은 피해야 한다. 불가피한 사정으로 메타 테이블 데이터 변경 시에는 변경 전에 반드시 데이터베이스 백업을 해야 하며, 사용자의 명시적인 메타 테이블 데이터 변경으로 인해 발생하는 데이터베이스의 손상은 전적으로 사용자 책임이다.

#### 메타 테이블 스키마 변경

새로운 종류의 DDL문이 제공되거나 기존 구문의 기능 변경 시 메타 테이블 스키마가 변경될 수 있다. 메타 테이블 스키마의 변경 특성에 따라 데이터베이스 마이그레이션이 필요한 경우와 Altibase 구동 시 자동으로 메타 테이블 스키마를 변경하는 두 가지 경우로 구분된다.

Altibase 하위 버전에서 상위 버전으로 업그레이드 시 이를 고려해야 한다.

#### 메타 테이블 종류

다음 표는 메타 테이블의 목록이다. 메타 테이블의 이름은 SYS_로 시작한다.

| 메타 테이블 이름            | 설명                                                         |
| --------------------------- | ------------------------------------------------------------ |
| SYS_AUDIT_                  | 감사의 동작 상태가 저장되는 메타 테이블                      |
| SYS_AUDIT_OPTS_             | 감사 조건이 저장되는 메타 뷰. SYS_AUDIT_ALL_OPTS_가 이 뷰의 베이스 메타 테이블이다. |
| SYS_COLUMNS_                | 칼럼에 대한 정보를 저장하는 메타 테이블                      |
| SYS_COMMENTS_               | 설명을 달기 위한 주석 메타 테이블                            |
| SYS_COMPRESSION_TABLES_     | 압축 칼럼에 대한 정보가 저장되는 메타 테이블                 |
| SYS_CONSTRAINTS_            | 제약 조건에 대한 정보를 저장하는 메타 테이블                 |
| SYS_CONSTRAINT_COLUMNS_     | 제약 조건을 가지는 칼럼에 대한 정보를 저장하는 메타 테이블   |
| SYS_CONSTRAINT_RELATED_     | 제약조건(constraints)이 참조하는 저장 함수에 대한 정보를 저장하는 메타 테이블 |
| SYS_DATABASE_               | 데이터베이스 이름과 버전에 대한 정보를 저장하는 메타 테이블  |
| SYS_DATABASE_LINKS_         | 데이터베이스 링크에 대한 정보를 저장하는 메타 테이블         |
| SYS_DIRECTORIES_            | 저장프로시저 내 파일 제어용 디렉터리에 대한 정보를 저장하는 메타 테이블 |
| SYS_DN_USERS_               | 향후 확장 예정                                               |
| SYS_DUMMY_                  | 내부 용도                                                    |
| SYS_ENCRYPTED_COLUMNS_      | 보안 설정에 기반한 부가적인 보안 정보를 암호화된 칼럼별로 저장하는 메타 테이블 |
| SYS_GRANT_OBJECT_           | 객체 권한에 대한 정보를 저장하는 메타 테이블                 |
| SYS_GRANT_SYSTEM_           | 시스템 권한에 대한 정보를 저장하는 메타 테이블               |
| SYS_INDEX_COLUMNS_          | 인덱스 키 칼럼에 대한 정보를 저장하는 메타 테이블            |
| SYS_INDEX_PARTITIONS_       | 인덱스 파티션에 대한 정보를 저장하는 메타 테이블             |
| SYS_INDEX_RELATED_          | 함수 기반 인덱스가 기반하는 저장 함수에 대한 정보를 저장하는 메타 테이블 |
| SYS_INDICES_                | 인덱스에 대한 정보를 저장하는 메타 테이블                    |
| SYS_JOBS_                   | JOB에 대한 정보를 저장하는 메타 테이블                       |
| SYS_LIBRARIES_              | 외부 라이브러리 객체에 대한 정보를 저장하는 메타 테이블      |
| SYS_LOBS_                   | LOB 칼럼에 대한 정보를 저장하는 메타 테이블                  |
| SYS_MATERIALIZED_VIEWS_     | Materialized view에 대한 정보가 기록되어 있는 메타 테이블    |
| SYS_PACKAGES_               | 패키지에 대한 정보가 저장되는 메타 테이블                    |
| SYS_PACKAGE_PARAS_          | 패키지에 포함된 서브프로그램(저장 프로시저와 저장 함수)들의 인자 (parameter)들에 대한 정보가 저장되는 메타 테이블 |
| SYS_PACKAGE_PARSE_          | 사용자가 정의한 패키지의 구문 텍스트가 저장되는 메타 테이블  |
| SYS_PACKAGE_RELATED_        | 패키지 내에 포함된 저장 프로시저와 저장 함수들이 참조하는 테이블, 시퀀스, 저장 프로시저, 저장 함수, 또는 뷰들에 대한 정보가 저장되는 메타 테이블 |
| SYS_PART_INDICES_           | 파티션드 인덱스에 대한 정보를 저장하는 메타 테이블           |
| SYS_PART_KEY_COLUMNS_       | 파티셔닝 키에 대한 정보를 저장하는 메타 테이블               |
| SYS_PART_LOBS_              | 파티션별 LOB 칼럼에 대한 정보를 저장하는 메타 테이블         |
| SYS_PART_TABLES_            | 파티션드 테이블에 대한 정보를 저장하는 메타 테이블           |
| SYS_PASSWORD_HISTORY_       | 패스워드 관리 정책을 설정한 사용자의 패스워드 변경 내역을 저장하는 메타 테이블 |
| SYS_PASSWORD_LIMITS_        | 사용자 생성 시 계정에 대해 지정한 패스워드 관리 정책과 계정의 현재 상태를 저장하는 메타 뷰 |
| SYS_PRIVILEGES_             | 권한에 대한 정보를 저장하는 메타 테이블                      |
| SYS_PROCEDURES_             | 저장 프로시저 및 함수에 대한 정보를 저장하는 메타 테이블     |
| SYS_PROC_PARAS_             | 저장 프로시저 및 함수의 파라미터에 대한 정보를 저장하는 메타 테이블 |
| SYS_PROC_PARSE_             | 저장 프로시저 및 함수의 구문에 대한 정보를 저장하는 메타 테이블 |
| SYS_PROC_RELATED_           | 저장 프로시저 및 함수가 접근하는 테이블에 대한 정보를 저장하는 메타 테이블 |
| SYS_RECYCLEBIN_             | 휴지통에 있는 테이블의 정보를 저장하는 메타 테이블           |
| SYS_REPLICATIONS_           | 이중화에 대한 정보를 저장하는 메타 테이블                    |
| SYS_REPL_HOSTS_             | 이중화 호스트에 대한 정보를 저장하는 메타 테이블             |
| SYS_REPL_ITEMS_             | 이중화 테이블에 대한 정보를 저장하는 메타 테이블             |
| SYS_REPL_OFFLINE_DIR_       | 이중화 오프라인 옵션 관련 로그 디렉터리에 대한 정보를 저장하는 메타 테이블 |
| SYS_REPL_OLD_COLUMNS_       | 이중화 송신 쓰레드가 이중화하는 칼럼에 대한 정보를 저장하는 메타 테이블 |
| SYS_REPL_OLD_INDEX_COLUMNS_ | 이중화 송신 쓰레드가 이중화하는 인덱스 칼럼에 대한 정보를 저장하는 메타 테이블 |
| SYS_REPL_OLD_INDICES_       | 이중화 송신 쓰레드가 이중화하는 인덱스에 대한 정보를 저장하는 메타 테이블 |
| SYS_REPL_OLD_ITEMS_         | 이중화 송신 쓰레드가 이중화하는 테이블에 대한 정보를 저장하는 메타 테이블 |
| SYS_REPL_RECOVERY_INFOS_    | 원격 서버의 복구를 위한 로그 정보를 저장하는 메타 테이블     |
| SYS_SECURITY_               | 보안 모듈에 대한 정보를 저장하는 메타 테이블                 |
| SYS_SYNONYMS_               | 시노님에 대한 정보를 저장하는 메타 테이블                    |
| SYS_TABLES_                 | 테이블에 대한 정보를 저장하는 메타 테이블                    |
| SYS_TABLE_PARTITIONS_       | 테이블의 파티션에 대한 정보를 저장하는 메타 테이블           |
| SYS_TABLE_SIZE_             | 시스템에 있는 디스크 테이블과 메모리 테이블의 실제 크기 정보를 저장하는 메타 테이블 |
| SYS_TBS_USERS_              | 사용자 정의 테이블스페이스에 대한 사용자 접근 정보를 저장하는 메타 테이블 |
| SYS_TRIGGERS_               | 트리거에 대한 정보를 저장하는 메타 테이블                    |
| SYS_TRIGGER_DML_TABLES_     | 트리거가 접근하는 테이블에 대한 정보를 저장하는 메타 테이블  |
| SYS_TRIGGER_STRINGS_        | 트리거 구문을 저장하는 메타 테이블                           |
| SYS_TRIGGER_UPDATE_COLUMNS_ | 그 값이 변경될 때마다 트리거를 시작시키는 칼럼들에 대한 정보를 저장하는 메타 테이블 |
| SYS_USERS_                  | 사용자에 대한 정보를 저장하는 메타 테이블                    |
| DBA_USERS_                  | 사용자에 대한 정보를 저장하는 메타 테이블. SYS 사용자만 조회 가능. |
| SYS_USER_ROLES_             | 사용자에게 부여된 롤(Role)에 대한 정보를 저장하는 메타 테이블 |
| SYS_VIEWS_                  | 뷰에 대한 정보를 저장하는 메타 테이블                        |
| SYS_VIEW_PARSE_             | 뷰 구문을 저장하는 메타 테이블                               |
| SYS_VIEW_RELATED_           | 뷰가 접근하는 테이블에 대한 정보를 저장하는 메타 테이블      |
| SYS_XA_HEURISTIC_TRANS_     | 글로벌 (global) 트랜잭션에 대한 정보를 저장하는 메타 테이블  |
| SYS_GEOMETRIES_             | GEOMETRY 칼럼을 보유한 테이블의 정보를 저장하는 메타 테이블  |
| SYS_GEOMETRY_COLUMNS_       | GEOMETRY 칼럼에 대한 정보를 저장하는 메타 테이블; Synonym으로 GEOMETRY_COLUMNS가 있음 |
| USER_SRS                    | 공간 참조 시스템(SRS, Spatial Reference System)에 관한 정보를 저장하는 메타 테이블, Synonym으로 SPATIAL_REF_SYS가 있음 |

### SYS_AUDIT_

감사(Auditing)의 동작 상태가 기록되는 메타 테이블이다.

| Column name | Type    | Description                    |
| ----------- | ------- | ------------------------------ |
| IS_STARTED  | INTEGER | 감사가 실행 중인지 여부        |
| START_TIME  | DATE    | 감사 시작 일시                 |
| STOP_TIME   | DATE    | 감사 종료 일시                 |
| RELOAD_TIME | DATE    | 감사 조건이 서버에 적용된 일시 |

#### 칼럼 정보

##### IS_STARTED

현재 감사가 실행 중인지를 나타낸다.

0: 현재 감사가 실행 중이 아님

1: 현재 감사가 실행 중임

##### START_TIME

감사가 시작된 일시를 나타낸다.

##### STOP_TIME

감사가 종료된 일시를 나타낸다.

##### RELOAD_TIME

변경된 감사 조건을 Altibase 서버에 적용한 시각을 나타낸다. 아래의 경우에 이 칼럼의 값이 업데이트 된다.

- 데이터베이스 관리자가 ALTER SYSTEM START AUDIT문을 사용해서 감사를 시작한 경우
- 데이터베이스 관리자가 ALTER SYSTEM RELOAD AUDIT문을 사용해서 변경된 감사 조건이 감사 수행에 적용되도록 한 경우

### SYS_AUDIT_OPTS_

감사 조건이 저장되어 있는 뷰이다. 이 뷰의 베이스 테이블은 SYS_AUDIT_ALL_OPTS_ 메타 테이블이다.

| Column name      | Type         | Description                                    |
| ---------------- | ------------ | ---------------------------------------------- |
| USER_NAME        | VARCHAR(128) | 사용자 이름                                    |
| OBJECT_NAME      | VARCHAR(128) | 객체 이름                                      |
| OBJECT_TYPE      | VARCHAR(40)  | 객체 타입                                      |
| SELECT_OP        | CHAR(3)      | 각 작업 구문에 대한 로그 기록 단위를 나타낸다. |
| INSERT_OP        | CHAR(3)      |                                                |
| UPDATE_OP        | CHAR(3)      |                                                |
| DELETE_OP        | CHAR(3)      |                                                |
| MOVE_OP          | CHAR(3)      |                                                |
| MERGE_OP         | CHAR(3)      |                                                |
| ENQUEUE_OP       | CHAR(3)      |                                                |
| DEQUEUE_OP       | CHAR(3)      |                                                |
| LOCK_TABLE_OP    | CHAR(3)      |                                                |
| EXECUTE_OP       | CHAR(3)      |                                                |
| COMMIT_OP        | CHAR(3)      |                                                |
| ROLLBACK_OP      | CHAR(3)      |                                                |
| SAVEPOINT_OP     | CHAR(3)      |                                                |
| CONNECT_OP       | CHAR(3)      |                                                |
| DISCONNECT_OP    | CHAR(3)      |                                                |
| ALTER_SESSION_OP | CHAR(3)      |                                                |
| ALTER_SYSTEM_OP  | CHAR(3)      |                                                |
| DDL_OP           | CHAR(3)      |                                                |

#### 칼럼 정보

##### USER_NAME

감사 대상 객체의 소유자의 사용자 이름이다.

##### OBJECT_NAME

감사 대상 객체의 이름을 나타낸다.

##### OBJECT_TYPE

대상 객체의 타입을 나타낸다. 아래 타입들 중 하나일 것이다.

- TABLE
- VIEW
- QUEUE
- SEQUENCE
- PROCEDURE
- FUNCTION

##### XXX_OP

각 작업 구문에 대한 로그를 기록하는 단위를 나타낸다. '/' 앞 쪽은 수행 성공에 대한 로그 기록 단위이고, 뒤 쪽은 수행 실패에 대한 로그 기록 단위이다.

표시되는 로그가 기록되는 단위는 아래와 같다.

- -: 로그가 기록되지 않음
- S: 세션 단위 로그가 기록됨
- A: 액세스 단위 로그가 기록됨

아래는 감사 조건 설정 후의 SYS_AUDIT_OPTS_ 뷰의 값을 보여준다.

```
iSQL> AUDIT insert, select, update, delete on friends BY SESSION WHENEVER SUCCESSFUL;
Audit success.

iSQL> AUDIT insert, select, update, delete on friends BY ACCESS WHENEVER NOT SUCCESSFUL;
Audit success.

USER_NAME : SYS 
OBJECT_NAME : FRIENDS 
OBJECT_TYPE : TABLE 
SELECT_OP : S/A 
INSERT_OP : S/A 
UPDATE_OP : S/A 
DELETE_OP : S/A 
MOVE_OP : -/- 
MERGE_OP : -/- 
ENQUEUE_OP : -/- 
DEQUEUE_OP : -/- 
LOCK_TABLE_OP : -/- 
EXECUTE_OP : -/- 
COMMIT_OP : -/- 
ROLLBACK_OP : -/- 
SAVEPOINT_OP : -/- 
CONNECT_OP : -/- 
DISCONNECT_OP : -/- 
ALTER_SESSION_OP : -/- 
ALTER_SYSTEM_OP : -/- 
DDL_OP : -/-

iSQL> AUDIT DDL BY sys WHENEVER NOT SUCCESSFUL;
Audit success.


USER_NAME : SYS 
OBJECT_NAME : ALL 
OBJECT_TYPE : 
SELECT_OP : -/- 
INSERT_OP : -/- 
UPDATE_OP : -/- 
DELETE_OP : -/- 
MOVE_OP : -/- 
MERGE_OP : -/- 
ENQUEUE_OP : -/- 
DEQUEUE_OP : -/- 
LOCK_TABLE_OP : -/- 
EXECUTE_OP : -/- 
COMMIT_OP : -/- 
ROLLBACK_OP : -/- 
SAVEPOINT_OP : -/- 
CONNECT_OP : -/- 
DISCONNECT_OP : -/- 
ALTER_SESSION_OP : -/- 
ALTER_SYSTEM_OP : -/- 
DDL_OP : -/T
```

### SYS_COLUMNS_

모든 테이블에 정의된 칼럼들의 정보, 뷰의 가상 칼럼 정보, 그리고 시퀀스의 가상 칼럼 정보를 저장하는 메타 테이블이다.

| Column name      | Type          | Description                                                  |
| ---------------- | ------------- | ------------------------------------------------------------ |
| COLUMN_ID        | INTEGER       | 칼럼 식별자                                                  |
| DATA_TYPE        | INTEGER       | 데이터 타입                                                  |
| LANG_ID          | INTEGER       | 언어 식별자                                                  |
| OFFSET           | BIGINT        | 레코드 내 칼럼의 오프셋                                      |
| SIZE             | BIGINT        | 레코드 내 칼럼의 물리적 길이                                 |
| USER_ID          | INTEGER       | 사용자 식별자                                                |
| TABLE_ID         | INTEGER       | 테이블 식별자                                                |
| PRECISION        | INTEGER       | 칼럼에 지정한 정밀도 (precision)                             |
| SCALE            | INTEGER       | 칼럼에 지정한 스케일 (scale)                                 |
| COLUMN_ORDER     | INTEGER       | 테이블에서 칼럼의 위치                                       |
| COLUMN_NAME      | VARCHAR(128)  | 칼럼 이름                                                    |
| IS_NULLABLE      | CHAR(1)       | 널 (NULL) 허용 여부 T: NULL 허용 F: NULL 불허                |
| DEFAULT_VAL      | VARCHAR(4000) | 기본 값 또는 수식                                            |
| STORE_TYPE       | CHAR(1)       | 칼럼의 저장 타입 V: 가변 (Variable) 방식 F: 고정 (Fixed) 방식 L: LOB 칼럼 |
| IN_ROW_SIZE      | INTEGER       | 메모리 테이블의 가변 길이 컬럼에 데이터가 입력될 때, 고정 영역(fixed area)에 저장될 수 있는 데이터의 최대 길이 |
| REPL_CONDITION   | INTEGER       | Deprecated                                                   |
| IS_HIDDEN        | CHAR(1)       | Hidden 칼럼인지 여부 T: 숨기는 칼럼 F: 공개된 칼럼           |
| IS_KEY_PRESERVED | CHAR(1)       | 데이터 변경이 가능한 칼럼인지 여부 T: 변경 가능 F: 변경 불가능 |

#### 칼럼 정보

##### COLUMN_ID

칼럼 식별자로 시스템 시퀀스에 의해 자동으로 부여된다.

##### DATA_TYPE

데이터 타입 식별자이다. 각 데이터 타입별 식별자 값은 다음과 같다.

| Data Type | 값    |
| --------- | ----- |
| CHAR      | 1     |
| VARCHAR   | 12    |
| NCHAR     | -8    |
| NVARCHAR  | -9    |
| NUMERIC   | 2     |
| DECIMAL   | 2     |
| FLOAT     | 6     |
| NUMBER    | 6     |
| DOUBLE    | 8     |
| REAL      | 7     |
| BIGINT    | -5    |
| INTEGER   | 4     |
| SMALLINT  | 5     |
| DATE      | 9     |
| BLOB      | 30    |
| CLOB      | 40    |
| BYTE      | 20001 |
| NIBBLE    | 20002 |
| BIT       | -7    |
| VARBIT    | -100  |
| GEOMETRY  | 10003 |

데이터 타입에 대한 자세한 내용은 1장을 참조한다.

##### LANG_ID

데이터 타입 (CHAR, VARCHAR)의 언어 속성 정보를 나타내는 칼럼이다.

##### OFFSET

레코드 내에서 칼럼의 물리적 시작 위치이다. 레코드의 물리적 저장 크기를 계산할 때 칼럼의 오프셋과 사이즈 값이 이용된다.

##### SIZE

레코드 내의 칼럼의 물리적 저장 사이즈로, 칼럼의 타입 및 사용자가 지정하는 정밀도 (precision) 등을 기준으로 시스템에 의해 계산된다.

##### USER_ID

칼럼이 속한 테이블 소유자의 식별자로, SYS_USERS_ 메타 테이블의 한 USER_ID 값과 일치한다.

##### TABLE_ID

칼럼이 속한 테이블의 식별자로, SYS_TABLES_ 메타 테이블의 한 TABLE_ID 값과 일치한다.

##### PRECISION

데이터 타입의 정밀도 (precision)로, 사용자가 지정하거나 시스템의 의해 기본값이 부여된다. 데이터 타입의 경우 사용자가 정의한 데이터 타입의 길이와 일치한다.

##### SCALE

데이터 타입의 스케일로, 사용자가 지정하거나 시스템이 기본값으로 부여한다. 타입에 따라 이 값은 사용되지 않는다.

##### COLUMN_ORDER

한 테이블 내에서 해당 칼럼이 보여지는 순서이다.

CREATE TABLE문에서 기술한 칼럼의 순서대로 칼럼이 생성되고, 테이블 내에서의 위치가 된다. ALTER TABLE문으로 칼럼을 추가한 경우 이 칼럼은 그 테이블의 마지막 칼럼으로 생성된다.

##### COLUMN_NAME

사용자가 테이블 생성 또는 칼럼 추가 시 명시한 칼럼의 이름이다.

##### IS_NULLABLE

칼럼에 NULL을 허용할 지 여부를 나타낸다.

칼럼 생성 시 사용자가 명시적으로 칼럼의 NULL 허용 여부를 명시할 수 있으며, 명시하지 않을 경우 기본으로 NULL을 허용한다.

##### DEFAULT_VAL

사용자가 해당 칼럼에 지정한 기본값이 표시된다.

해당 칼럼이 함수 기반 인덱스 생성으로 인해 자동으로 추가된 hidden 칼럼일 경우 함수 기반 인덱스 생성에 사용된 수식이 저장된다.

##### STORE_TYPE

칼럼을 물리적으로 저장할 때 레코드의 한 부분으로 기록할 수도 있고, 레코드 내에는 칼럼의 저장 위치 정보만을 저장하고 실제 칼럼 값은 다른 페이지에 기록할 수도 있다.

한 칼럼의 물리적 저장 크기가 크거나 레코드별로 칼럼의 저장 크기의 변동이 잦은 경우, 칼럼 정의 시 VARIABLE 옵션을 사용하면 레코드와 물리적으로 다른 페이지에 해당 칼럼을 저장할 수 있다. 일반적으로 VARCHAR 타입의 경우 문자열 길이가 긴 칼럼의 경우 이 옵션을 사용한다.

이 칼럼은 이러한 VARIABLE 옵션 지정 여부를 나타낸다.

##### IN_ROW_SIZE

메모리 테이블의 가변(VARIABLE) 길이 칼럼에 데이터가 입력될 때의 기본 in row size를 나타낸다. 가변 길이 칼럼에 데이터가 삽입될 때 데이터 길이가 이 값보다 작거나 같으면 고정 (fixed) 영역에 저장되고, 이 보다 긴 경우에는 가변 (variable) 영역에 들어가게 된다. 디스크 테이블의 경우 이 값은 항상 0이다.

IN ROW 절이나 VARIABLE 옵션(가변 길이 칼럼)에 대한 자세한 사항은 1장의 데이터 타입 부분을 참조한다.

##### IS_HIDDEN

해당 칼럼이 hidden 속성을 갖는지 여부를 나타낸다. 함수 기반 인덱스 생성 시, 테이블에 hidden 속성의 칼럼이 자동으로 추가된다. 이 칼럼에는 아래 두개의 값 중에서 하나가 표시된다.

- T: 숨기는 칼럼
- F: 공개된 칼럼

##### IS_KEY_PRESERVED

조인 뷰의 칼럼이 DML문으로 변경(INSERT, UPDATE, DELETE) 가능한 칼럼인지를 나타낸다. 일반 테이블의 칼럼일 경우 이 값이 'T'로 표시될 것이다. 뷰의 경우 변경 가능한 칼럼은 'T'로 표시되고 변경이 불가능한 칼럼은 'F'로 표시될 것이다.

- T: 변경 가능한 칼럼
- F: 변경 불가능한 칼럼

#### 참조 테이블

```
SYS_USERS_
SYS_TABLES_
SYS_GEOMETRIES_
```

### SYS_COMMENTS_

사용자가 정의한 테이블, 뷰 및 그에 소속된 칼럼에 대한 설명, 즉 주석을 기록하는 메타 테이블이다.

| Column name | Type          | Description |
| ----------- | ------------- | ----------- |
| USER_NAME   | VARCHAR(128)  | 사용자 이름 |
| TABLE_NAME  | VARCHAR(128)  | 테이블 이름 |
| COLUMN_NAME | VARCHAR(128)  | 칼럼 이름   |
| COMMENTS    | VARCHAR(4000) | 주석 내용   |

#### 칼럼 정보

##### USER_NAME

테이블 소유자 이름으로, 이 값은 SYS_USERS_ 메타 테이블의 한 USER_NAME 값과 일치한다.

##### TABLE_NAME

테이블 (또는 뷰)의 이름으로, 이 값은 SYS_TABLES_ 메타 테이블의 한 TABLE_NAME 값과 동일하다.

##### COLUMN_NAME

테이블 (또는 뷰)에 속한 칼럼의 이름으로, 이 값은 SYS_COLUMNS_ 메타 테이블의 한 COLUMN_NAME 값과 동일하다.

단, 주석이 테이블 (또는 뷰)에 대한 설명일 경우에는 COLUMN_NAME의 값은 NULL 일 것이다.

##### COMMENTS

사용자가 기록한 주석 내용이다.

#### 참조 테이블

```
SYS_USERS_
SYS_TABLES_
SYS_COLUMNS_
```

### SYS_COMPRESSION_TABLES_

압축 칼럼에 대한 정보가 저장되는 메타 테이블이다.

| Column name  | Type    | Description                                                  |
| ------------ | ------- | ------------------------------------------------------------ |
| TABLE_ID     | INTEGER | 압축 칼럼을 포함하는 테이블의 식별자                         |
| COLUMN_ID    | INTEGER | 압축 칼럼의 식별자                                           |
| DIC_TABLE_ID | INTEGER | 압축 칼럼의 데이터가 저장되어 있는 딕셔너리 테이블의 식별자  |
| MAXROWS      | BIGINT  | 압축 칼럼의 데이터가 저장되어 있는 테이블에 입력할 수 있는 행의 최대 개수(0: 제한 없음) |

#### 칼럼 정보

##### TABLE_ID

압축 칼럼이 속한 테이블의 식별자를 나타낸다. 이 값은 SYS_TABLES_ 메타 테이블의 한 TABLE_ID 값과 일치한다.

##### COLUMN_ID

압축 칼럼의 식별자로, SYS_COLUMNS_ 메타 테이블의 한 COLUMN_ID 값과 일치한다.

##### DIC_TABLE_ID

압축 칼럼의 데이터가 실제로 저장되어 있는 딕셔너리 테이블의 식별자를 나타낸다.

##### MAXROWS

압축 칼럼의 데이터가 실제로 저장되어 있는 딕셔너리 테이블에 입력할 수 있는 행의 최대 개수를 나타낸다.

### SYS_CONSTRAINTS_

테이블의 제약 조건에 관한 정보를 포함하는 메타 테이블이다.

| Column name         | Type          | Description                                                  |
| ------------------- | ------------- | ------------------------------------------------------------ |
| USER_ID             | INTEGER       | 사용자 식별자                                                |
| TABLE_ID            | INTEGER       | 테이블 식별자                                                |
| CONSTRAINT_ID       | INTEGER       | 제약조건 식별자                                              |
| CONSTRAINT_NAME     | VARCHAR(128)  | 제약조건 이름                                                |
| CONSTRAINT_TYPE     | INTEGER       | 제약조건 타입                                                |
| INDEX_ID            | INTEGER       | 제약조건의 인덱스 식별자                                     |
| COLUMN_CNT          | INTEGER       | 제약조건에 관련된 칼럼 개수                                  |
| REFERENCED_TABLE_ID | INTEGER       | FOREIGN KEY 제약조건으로 참조하는 테이블의 식별자            |
| REFERENCED_INDEX_ID | INTEGER       | FOREIGN KEY 제약조건으로 참조하는 인덱스의 식별자            |
| DELETE_RULE         | INTEGER       | FOREIGN KEY 제약조건을 위한 삭제 규칙 0: 종속적으로 삭제하지 않음 1: 종속적으로 삭제 2: SET NULL, 외래 키 관계에 의해 종속되는 칼럼 값을 NULL로 변경 |
| CHECK_CONDITION     | VARCHAR(4000) | Check 제약조건의 조건 문자열                                 |
| VALIDATED           | CHAR(1)       | 모든 데이터가 제약조건을 따르는지 여부                       |

#### 칼럼 정보

##### USER_ID

사용자 식별자로 SYS_USERS_ 메타 테이블의 한 USER_ID 값과 동일하다.

##### TABLE_ID

제약 조건을 정의한 테이블 식별자로 SYS_TABLES_ 메타 테이블의 TABLE_ID 중 한 값과 동일하다.

##### CONSTRAINT_ID

제약 조건 식별자로 시스템 시퀀스에 의해 자동으로 부여된다.

##### CONSTRAINT_NAME

제약 조건의 이름을 나타낸다.

##### CONSTRAINT_TYPE

제약 조건의 타입을 나타내는 값으로 종류는 다음과 같다.

- 0: FOREIGN KEY
- 1: NOT NULL
- 2: UNIQUE
- 3: PRIMARY KEY
- 5: TIMESTAMP
- 6: LOCAL UNIQUE
- 7: CHECK

각 제약 조건의 기능에 대한 설명은 *SQL Reference*의 CREATE TABLE문에 있는 column constraint 설명을 참조한다.

##### INDEX_ID

UNIQUE 또는 PRIMARY KEY 제약 조건과 같이 제약조건을 정의하기 위해서 인덱스를 생성해야 할 때, 시스템은 내부적으로 인덱스를 생성한다. 이것은 이때 생성한 인덱스의 식별자로 SYS_INDICES_ 메타 테이블의 한 INDEX_ID 값과 동일하다.

##### COLUMN_CNT

제약 조건에 관련된 칼럼들의 개수를 나타낸다. 예를 들어 UNIQUE (i1, i2, i3) 과 같은 제약 조건을 생성하였다면 이 값은 3일 것이다.

##### REFERENCED_TABLE_ID

참조 제약조건 (Foreign key constraint)으로 참조하는 테이블의 식별자이다 (제약 조건이 정의된 테이블이 아니다). 이 식별자는 SYS_TABLES_ 메타 테이블의 한 TABLE_ID 값과 일치할 것이다.

##### REFERENCED_INDEX_ID

참조 제약조건 (Foreign key constraint)으로 참조하는 테이블에 존재해야 하는 UNIQUE 또는 PRIMARY KEY 제약조건의 식별자이다. 이 제약조건의 식별자 값은 SYS_CONSTRAINTS_ 메타 테이블의 한 CONSTRAINT_ID 값과 동일할 것이다.

##### CHECK_CONDITION

사용자가 Check 제약조건을 지정할 때 정의한 무결성 규칙(Integrity Rule)을 나타낸다.

##### VALIDATED

모든 데이터가 제약조건을 따르는지 여부를 나타낸다.

#### 참조 테이블

```
SYS_USERS_
SYS_TABLES_
SYS_INDICES_
```

### SYS_CONSTRAINT_COLUMNS_

사용자 테이블에 정의된 모든 제한조건에 관련된 칼럼의 정보를 기록하고 있는 메타 테이블이다.

| Column name          | Type    | Description                |
| -------------------- | ------- | -------------------------- |
| USER_ID              | INTEGER | 사용자 식별자              |
| TABLE_ID             | INTEGER | 테이블 식별자              |
| CONSTRAINT_ID        | INTEGER | 제약조건 식별자            |
| CONSTRAINT_COL_ORDER | INTEGER | 제약조건내에서 칼럼의 순서 |
| COLUMN_ID            | INTEGER | 칼럼 식별자                |

#### 칼럼 정보

##### USER_ID

테이블의 소유자 식별자로, SYS_USERS_ 메타 테이블의 한 USER_ID 값과 동일하다.

##### TABLE_ID

제약조건을 정의한 테이블의 식별자로, SYS_TABLES_ 메타 테이블의 한 TABLE_ID 값과 동일하다.

##### CONSTRAINT_ID

제약조건의 식별자로, SYS_CONSTRAINTS_ 메타 테이블의 어떤 CONSTRAINT_ID 값과 동일하다.

##### CONSTRAINT_COL_ORDER

제약조건 내에 정의된 칼럼의 위치이다. 예를 들어 UNIQUE (i1, i2, i3)과 같은 제약조건을 생성할 경우 SYS_CONSTRAINT_COLUMNS_ 메타 테이블에는 3개의 레코드가 삽입된다. 이 때 i1의 위치는 1, i2 의 위치는 2, i3 의 위치는 3이 각각 기록된다.

##### COLUMN_ID

제약조건에 정의된 칼럼의 식별자로, SYS_COLUMNS_ 메타 테이블의 한 COLUMN_ID 값과 동일하다.

#### 참조 테이블

```
SYS_USERS_
SYS_TABLES_
SYS_CONSTRAINTS_
SYS_COLUMNS_
```

### SYS_CONSTRAINT_RELATED_

제약조건(constraint)이 참조하고 있는 저장 함수에 대한 정보가 기록되어 있는 메타 테이블이다.

| Column name       | Type         | Description                                   |
| ----------------- | ------------ | --------------------------------------------- |
| USER_ID           | INTEGER      | 사용자 식별자                                 |
| TABLE_ID          | INTEGER      | 테이블 식별자                                 |
| CONSTRAINT_ID     | INTEGER      | 제약조건 식별자                               |
| RELATED_USER_ID   | INTEGER      | 제약조건이 참조하는 저장 함수의 소유자 식별자 |
| RELATED_PROC_NAME | VARCHAR(128) | 제약조건이 참조하는 저장 함수의 이름          |

#### 칼럼 정보

##### USER_ID

제약조건 소유자의 식별자로, SYS_USERS_ 메타 테이블의 한 USER_ID 값과 동일하다.

##### TABLE_ID

제약조건을 정의한 테이블의 식별자로, SYS_TABLES_ 메타 테이블의 한 TABLE_ID 값과 동일하다.

##### CONSTRAINT_ID

제약조건의 식별자로, SYS_CONSTRAINTS_ 메타 테이블의 한 CONSTRAINT_ID 값과 동일하다.

##### RELATED_USER_ID

제약조건이 참조하는 저장 함수 소유자의 식별자로, SYS_USERS_ 메타 테이블의 한 USER_ID 값과 동일하다.

##### RELATED_PROC_NAME

제약조건이 참조하는 저장 함수의 이름으로, SYS_PROCEDURES_ 메타 테이블의 한 PROC_NAME 값과 동일하다.

#### 참조 테이블

```
SYS_USERS_
SYS_TABLES_
SYS_CONSTRAINTS_
SYS_PROCEDURES_
```

### SYS_DATABASE_

데이터베이스 이름과 메타 테이블 버전 정보를 기록하는 테이블이다.

| Column name    | Type          | Description                              |
| -------------- | ------------- | ---------------------------------------- |
| DB_NAME        | VARCHAR(40)   | 데이터베이스 이름                        |
| OWNER_DN       | VARCHAR(2048) | 향후 확장 예정                           |
| META_MAJOR_VER | INTEGER       | 데이터베이스 메타 테이블 버전(주 버전)   |
| META_MINOR_VER | INTEGER       | 데이터베이스 메타 테이블 버전(부 버전)   |
| META_PATCH_VER | INTEGER       | 데이터베이스 메타 테이블 버전(패치 버전) |

#### 칼럼 정보

##### DB_NAME

데이터베이스 생성시 지정한 데이터베이스 이름이 저장된다.

##### META_MAJOR_VER

메타 테이블의 주 버전을 나타낸다. 주 버전은 메타 테이블의 정의가 변경되거나 메타 테이블이 추가 또는 삭제 될 경우 증가한다. 데이터베이스의 이 버전과 Altibase 바이너리의 해당 버전이 일치하지 않은 경우 데이터베이스 마이그레이션 작업을 요한다.

##### META_MINOR_VER

메타 테이블의 부 버전을 나타낸다. 부 버전은 메타 테이블의 일부 스키마 또는 레코드 값이 변경될 경우 증가한다. 데이터베이스의 이 버전과 Altibase 바이너리의 해당 버전이 다른 경우, 내부적으로 값을 비교해 상위 버전으로 메타 테이블의 자동 업그레이드를 수행한다.

##### META_PATCH_VER

메타 테이블 패치 버전을 나타낸다.

### SYS_DATABASE_LINKS_

데이터베이스 링크 정보를 기록하는 메타 테이블이다

| Column name     | Type         | Description                                                  |
| --------------- | ------------ | ------------------------------------------------------------ |
| USER_ID         | INTEGER      | 사용자 식별자                                                |
| LINK_ID         | INTEGER      | 데이터베이스 링크 식별자                                     |
| LINK_OID        | BIGINT       | 데이터베이스 링크 객체 식별자                                |
| LINK_NAME       | VARCHAR(40)  | 데이터베이스 링크 이름                                       |
| USER_MODE       | INTEGER      | 원격 서버로의 접근 방법                                      |
| REMOTE_USER_ID  | VARCHAR(128) | 원격 데이타베이스의 사용자 계정                              |
| REMOTE_USER_PWD | BYTE(40)     | 원격 데이타베이스의 사용자 비밀번호                          |
| LINK_TYPE       | INTEGER      | Heterogeneous Link인지 Homogeneous Link인지를 나타냄.        |
| TARGET_NAME     | VARCHAR(40)  | 데이터베이스 링크 객체가 접근할 원격서버의 이름              |
| CREATED         | DATE         | 데이터베이스 링크 객체가 생성된 일시                         |
| LAST_DDL_TIME   | DATE         | 데이터베이스 링크 객체에 마지막으로 DDL 변경 작업이 일어난 일시 |

#### 칼럼 정보

##### USER_ID

데이터베이스 링크 소유자의 식별자이다.

##### LINK_ID

데이터베이스 링크 식별자이다.

##### LINK_OID

데이터베이스 링크의 객체 식별자이다.

##### LINK_NAME

사용자가 데이터베이스 링크 생성 시에 명시한 데이터베이스 링크 이름을 나타낸다.

##### USER_MODE

원격 서버로의 접근 방법을 나타낸다.

- 0: DEDICATE USER MODE
- 1: CURRENT USER MODE (향후 사용을 위해 예약됨)

##### REMOTE_USER_ID

원격 데이터베이스 서버에 접근할 때 사용하는 원격 서버 사용자 계정을 나타낸다.

##### REMOTE_USER_PWD

원격 데이터베이스 서버에 접근할 때 사용하는 원격 서버 사용자 비밀번호를 나타낸다. 비밀번호는 복호화가 가능한 암호화 알고리즘으로 암호화하여 저장한다.

##### LINK_TYPE

Heterogeneous Link인지 Homogeneous Link인지를 나타낸다.

##### TARGET_NAME

데이터베이스 링크 객체가 접근할 원격서버의 이름을 나타낸다.

##### CREATED

데이터베이스 링크 객체가 생성된 일시를 나타낸다.

##### LAST_DDL_TIME

데이터베이스 링크 객체에 마지막으로 DDL 변경 작업이 일어난 일시를 나타낸다.

### SYS_DIRECTORIES_

저장프로시저 내에서 파일 제어를 하기 위해 사용하는 디렉터리에 대한 정보를 기록하는 테이블이다.

| Column name    | Type          | Description                                                  |
| -------------- | ------------- | ------------------------------------------------------------ |
| DIRECTORY_ID   | BIGINT        | 디렉터리 식별자                                              |
| USER_ID        | INTEGER       | 사용자 식별자                                                |
| DIRECTORY_NAME | VARCHAR(128)  | 디렉터리 이름                                                |
| DIRECTORY_PATH | VARCHAR(4000) | 시스템에서 디렉터리의 절대 경로                              |
| CREATED        | DATE          | 디렉터리가 생성된 시간                                       |
| LAST_DDL_TIME  | DATE          | 디렉터리에 대해 가장 최근에 DDL 변경작업이 마지막으로 일어난 시간 |

#### 칼럼 정보

##### DIRECTORY_ID

디렉터리 식별자로 시스템 내에서 유일값을 가진다.

##### USER_ID

디렉터리 소유자의 사용자 식별자를 나타낸다.

##### DIRECTORY_NAME

디렉터리 이름으로 시스템 내 유일값을 가진다.

##### DIRECTORY_PATH

디렉터리가 위치하는 시스템 내 절대 경로로, CREATE DIRECTORY문 수행 시 사용자가 명시적으로 지정한다.

##### LAST_DDL_TIME

디렉터리 객체에 마지막으로 DDL 변경 작업이 일어난 시간을 나타낸다.

### SYS_ENCRYPTED_COLUMNS_

보안 설정에 기반한 부가적인 보안 정보를 암호화된 칼럼별로 관리하기 위한 메타 테이블이다.

| Column name       | Type         | Description                      |
| ----------------- | ------------ | -------------------------------- |
| USER_ID           | INTEGER      | 보안 칼럼이 속한 테이블의 소유자 |
| TABLE_ID          | INTEGER      | 보안 칼럼이 속한 테이블의 식별자 |
| COLUMN_ID         | INTEGER      | 보안 대상 칼럼의 식별자          |
| ENCRYPT_PRECISION | INTEGER      | 보안 칼럼의 precision            |
| POLICY_NAME       | VARCHAR(16)  | 보안 정책의 이름                 |
| POLICY_CODE       | VARCHAR(128) | 보안 정책에 대한 검증 코드       |

### SYS_GRANT_OBJECT_

사용자에게 부여된 객체 권한 정보를 저장한다.

| Column name       | Type       | Description                                                  |
| ----------------- | ---------- | ------------------------------------------------------------ |
| GRANTOR_ID        | INTEGER    | 권한을 부여한 사용자의 식별자                                |
| GRANTEE_ID        | INTEGER    | 권한이 부여된 사용자의 식별자                                |
| PRIV_ID           | INTEGER    | 권한 식별자                                                  |
| USER_ID           | INTEGER    | 객체 소유자의 식별자                                         |
| OBJ_ID            | BIGINT     | 객체 식별자                                                  |
| OBJ_TYPE          | VARCHAR(1) | 객체 타입                                                    |
| WITH_GRANT_OPTION | INTEGER    | 객체 접근 권한 부여시 WITH GRANT OPTION의 사용 유무 0: 사용 안 함 1: 사용함 |

#### 칼럼 정보

##### GRANTOR_ID

권한을 부여한 사용자의 식별자로, SYS_USERS_ 메타 테이블의 한 USER_ID 값과 동일하다.

##### GRANTEE_ID

권한을 부여받은 사용자의 식별자로, SYS_USERS_ 메타 테이블의 한 USER_IeovytD 값과 동일하다. 단, 객체 권한을 public에게 부여한 경우, SYS_USERS_ 메타 테이블에 존재하지 않는 USER_ID 값인 "0"이 이 칼럼에 나타난다.

##### PRIV_ID

권한 식별자로 SYS_PRIVILEGES_ 메타 테이블의 한 PRIV_ID 값과 동일하다.

##### USER_ID

해당 권한과 관련된 객체 소유자의 사용자 식별자로, SYS_USERS_ 메타 테이블의 한 USER_ID 값과 동일하다.

##### OBJ_ID

해당 권한과 관련된 객체의 식별자로, 메타 테이블에 저장된 대상 객체의 식별자와 1:1 관계이다.

대상 객체가 테이블, 뷰 또는 시퀀스인 경우에는 SYS_TABLES_메타 테이블의 한 TABLE_ID와 매핑되고, 대상 객체가 저장 프로시저이거나 저장 함수일 경우에는 SYS_PROCEDURES_ 메타 테이블의 한 PROC_OID와 매핑된다.

##### OBJ_TYPE

해당 권한과 관련된 객체의 종류를 나타낸다.

- A: 저장 패키지
- D: 디렉토리
- T: 테이블 또는 뷰
- S: 시퀀스
- P: 저장 프로시저 또는 저장 함수
- Y: 라이브러리

##### WITH_GRANT_OPTION

권한을 부여받은 사용자가 다른 사용자에게 해당 권한을 부여할 수 있는 권한이 있는지 여부를 나타낸다.

#### 참조 테이블

```
SYS_USERS_
SYS_PRIVILEGES_
SYS_TABLES_
SYS_PROCEDURES_
```

### SYS_GRANT_SYSTEM_

사용자에게 부여된 시스템 권한 정보를 포함한다.

| Column name | Type    | Description                   |
| ----------- | ------- | ----------------------------- |
| GRANTOR_ID  | INTEGER | 권한을 부여한 사용자의 식별자 |
| GRANTEE_ID  | INTEGER | 권한이 부여된 사용자의 식별자 |
| PRIV_ID     | INTEGER | 권한 식별자                   |

#### 칼럼 정보

##### GRANTOR_ID

권한을 부여한 사용자의 사용자 식별자로, SYS_USERS_ 메타 테이블의 한 USER_ID 값과 동일하다.

##### GRANTEE_ID

권한을 부여받은 사용자의 사용자 식별자로, SYS_USERS_ 메타 테이블의 한 USER_ID 값과 동일하다.

##### PRIV_ID

권한 식별자로 SYS_PRIVILEGES_ 메타 테이블의 한 PRIV_ID 값과 동일하다.

#### 참조 테이블

```
SYS_USERS_
SYS_PRIVILEGES_
```

### SYS_INDEX_COLUMNS_

모든 테이블에 정의된 인덱스에 연관된 칼럼의 정보를 기록하고 있는 메타 테이블이다.

| Column name     | Type    | Description               |
| --------------- | ------- | ------------------------- |
| USER_ID         | INTEGER | 사용자 식별자             |
| INDEX_ID        | INTEGER | 인덱스 식별자             |
| COLUMN_ID       | INTEGER | 칼럼의 식별자             |
| INDEX_COL_ORDER | INTEGER | 인덱스 내에서 칼럼의 위치 |
| SORT_ORDER      | CHAR(1) | 정렬 순서                 |
| TABLE_ID        | INTEGER | 테이블 식별자             |

#### 칼럼 정보

##### USER_ID

인덱스 소유자의 사용자 식별자로, SYS_USERS_ 메타 테이블의 한 USER_ID 값과 동일하다.

##### INDEX_ID

인덱스 식별자로, SYS_INDICES_ 메타 테이블의 한 INDEX_ID 값과 동일하다.

##### COLUMN_ID

인덱스를 생성한 칼럼의 식별자로, SYS_COLUMNS_ 메타 테이블의 한 COLUMN_ID 값과 동일하다.

##### INDEX_COL_ORDER

복합 인덱스 (composite index)의 경우 여러 개의 칼럼에 한 인덱스를 생성하므로, 이 때 해당 칼럼이 인덱스에서 몇 번째 위치하는지를 나타내는 값이다.

##### SORT_ORDER

인덱스가 오름차순 또는 내림차순으로 정렬되었는지를 나타낸다.

- A: 오름차순
- D: 내림차순

##### TABLE_ID

인덱스를 생성한 테이블의 식별자로, SYS_TABLES_ 메타 테이블의 한 TABLE_ID 값과 동일하다.

#### 참조 테이블

```
SYS_USERS_
SYS_TABLES_
SYS_COLUMNS_
SYS_INDICES_
```

### SYS_INDEX_PARTITIONS_

인덱스 파티션을 관리하는 메타 테이블이다.

| Column name          | Type          | Description                                     |
| -------------------- | ------------- | ----------------------------------------------- |
| USER_ID              | INTEGER       | 사용자 식별자                                   |
| TABLE_ID             | INTEGER       | 테이블 식별자                                   |
| INDEX_ID             | INTEGER       | 인덱스 식별자                                   |
| TABLE_PARTITION_ID   | INTEGER       | 테이블 파티션 식별자                            |
| INDEX_PARTITION_ID   | INTEGER       | 인덱스 파티션 식별자                            |
| INDEX_PARTITION_NAME | VARCHAR(128)  | 인덱스 파티션 이름                              |
| PARTITION_MIN_VALUE  | VARCHAR(4000) | 사용되지 않음                                   |
| PARTITION_MAX_VALUE  | VARCHAR(4000) | 사용되지 않음                                   |
| TBS_ID               | INTEGER       | 테이블스페이스 식별자                           |
| CREATED              | DATE          | 인덱스 파티션이 생성된 시간                     |
| LAST_DDL_TIME        | DATE          | 인덱스 파티션을 마지막으로 DDL 변경 작업한 시간 |

#### 칼럼 정보

##### USER_ID

인덱스 소유자의 사용자 식별자로, SYS_USERS_ 메타 테이블의 한 USER_ID 값과 동일하다.

##### TABLE_ID

인덱스를 생성한 테이블의 테이블 식별자로, SYS_TABLES_ 메타 테이블의 한 TABLE_ID 값과 동일하다.

##### INDEX_ID

인덱스 식별자로, SYS_INDICES_ 메타 테이블의 한 INDEX_ID 값과 동일하다.

##### TABLE_PARTITION_ID

테이블 파티션의 식별자이다.

##### INDEX_PARTITION_ID

인덱스 파티션의 식별자이다.

##### INDEX_PARTITION_NAME

인덱스 파티션의 이름으로, 사용자가 명시한 값이다.

##### TBS_ID

인덱스가 저장되는 테이블스페이스의 식별자이다.

#### 참조 테이블

```
SYS_USERS_
SYS_TABLES_
SYS_INDICES_
SYS_TABLE_PARTITIONS_
```

### SYS_INDEX_RELATED_

함수 기반 인덱스(Function-based Index)가 기반하고 있는 저장 함수들에 대한 정보가 기록되어 있는 메타 테이블이다.

| Column name       | Type         | Description                                 |
| ----------------- | ------------ | ------------------------------------------- |
| USER_ID           | INTEGER      | 사용자 식별자                               |
| TABLE_ID          | INTEGER      | 테이블 식별자                               |
| INDEX_ID          | INTEGER      | 인덱스 식별자                               |
| RELATED_USER_ID   | INTEGER      | 인덱스가 참조하는 저장 함수의 소유자 식별자 |
| RELATED_PROC_NAME | VARCHAR(128) | 인덱스가 참조하는 저장 함수의 이름          |

#### 칼럼 정보

##### USER_ID

인덱스 소유자의 식별자이다. SYS_USERS_ 메타 테이블의 한 USER_ID 값과 동일하다.

##### TABLE_ID

인덱스가 정의된 테이블의 식별자로, SYS_TABLES_ 메타 테이블의 한 TABLE_ID 값과 동일하다.

##### INDEX_ID

인덱스 식별자로, SYS_INDICES_ 메타 테이블의 한 INDEX_ID 값과 동일하다.

##### RELATED_USER_ID

인덱스가 참조하는 저장 함수 소유자의 식별자로, SYS_USERS_ 메타 테이블의 한 USER_ID 값과 동일하다.

##### RELATED_PROC_NAME

인덱스가 참조하는 저장 함수의 이름으로, SYS_PROCEDURES_ 메타 테이블의 한 PROC_NAME 값과 동일하다.

#### 참조 테이블

```
SYS_USERS_
SYS_TABLES_
SYS_INDICES_
SYS_PROCEDURES_
```

### SYS_INDICES_

모든 테이블에 정의된 모든 인덱스 정보를 기록하고 있는 메타 테이블이다.

| Column name    | Type         | Description                                                  |
| -------------- | ------------ | ------------------------------------------------------------ |
| USER_ID        | INTEGER      | 사용자 식별자                                                |
| TABLE_ID       | INTEGER      | 테이블 식별자                                                |
| INDEX_ID       | INTEGER      | 인덱스 식별자                                                |
| INDEX_NAME     | VARCHAR(128) | 인덱스 이름                                                  |
| INDEX_TYPE     | INTEGER      | 인덱스 타입                                                  |
| IS_UNIQUE      | CHAR(1)      | 중복 키 값 허용 여부                                         |
| COLUMN_CNT     | INTEGER      | 인덱스 칼럼 개수                                             |
| IS_RANGE       | CHAR(1)      | 범위 검색 가능 여부                                          |
| IS_PERS        | CHAR(1)      | 인덱스 영구 저장 여부                                        |
| IS_DIRECTKEY   | CHAR(1)      | 다이렉트 키 인덱스 여부                                      |
| TBS_ID         | INTEGER      | 테이블스페이스 식별자                                        |
| IS_PARTITIONED | CHAR(1)      | 파티션드 인덱스인지 여부                                     |
| INDEX_TABLE_ID | INTEGER      | 파티션드 테이블의 넌파티션드 인덱스가 보조적으로 생성한 테이블 식별자 |
| CREATED        | DATE         | 인덱스가 생성된 시간                                         |
| LAST_DDL_TIME  | DATE         | DDL 구문을 사용해서 인덱스에 대해 마지막으로 변경 작업이 일어난 시간 |

#### 칼럼 정보

##### USER_ID

인덱스 소유자의 사용자 식별자로, SYS_USERS_ 메타 테이블의 한 USER_ID 값과 동일하다.

##### TABLE_ID

인덱스를 생성한 테이블의 테이블 식별자로, SYS_TABLES_ 메타 테이블의 한 TABLE_ID 값과 동일하다.

##### INDEX_ID

인덱스 식별자로, 시스템 시퀀스에 의해 자동으로 부여된다.

##### INDEX_NAME

인덱스의 이름이다.

##### INDEX_TYPE

인덱스 타입을 나타낸다. 1이면 B-TREE 인덱스이고, 2이면 R-TREE 인덱스이다.

##### IS_UNIQUE

중복 키 값 허용여부를 나타낸다.

- T: 중복 키 값을 허용하지 않는다.
- F: 중복 키 값을 허용한다.

##### COLUMN_CNT

인덱스를 구성하는 칼럼의 개수를 나타낸다.

##### IS_RANGE

범위 검색 가능 여부를 나타낸다.

- T: 범위 검색 가능
- F: 범위 검색 불가능

##### IS_DIRECTKEY

다이렉트 키(Direct Key) 인덱스의 사용 여부를 나타낸다.

- T: 다이렉트 키 인덱스
- F: 일반 인덱스

##### TBS_ID

인덱스가 저장되는 테이블스페이스의 식별자이다.

##### IS_PARTITIONED

파티션드 인덱스인지 여부를 나타내는 식별자이다. 'T'는 파티션드 인덱스, 'F'는 파티션드 인덱스가 아니다.

#### 참조 테이블

```
SYS_USERS_
SYS_TABLES_
```

### SYS_JOBS_

JOB에 대한 정보가 기록되는 메타 테이블이다.

| Column name    | Type          | Description                                                 |
| -------------- | ------------- | ----------------------------------------------------------- |
| JOB_ID         | INTEGER       | JOB의 식별자                                                |
| JOB_NAME       | VARCHAR(128)  | JOB의 이름                                                  |
| EXEC_QUERY     | VARCHAR(1000) | JOB에 등록한 프로시저                                       |
| START_TIME     | DATE          | JOB이 처음으로 시작하는 시간                                |
| END_TIME       | DATE          | JOB이 끝나는 시간                                           |
| INTERVAL       | INTEGER       | 실행 주기                                                   |
| INTERVAL_TYPE  | CHAR(2)       | 실행 주기의 단위(YY, MM, DD, HH, MI)                        |
| STATE          | INTEGER       | 현재 실행중인 JOB의 상태 0: 실행되지 않음 1: 실행되고 있음  |
| LAST_EXEC_TIME | DATE          | 마지막으로 JOB을 실행한 시간                                |
| EXEC_COUNT     | INTEGER       | JOB의 실행 횟수                                             |
| ERROR_CODE     | CHAR(7)       | 에러 코드(NULL은 성공을 의미함)                             |
| IS_ENABLE      | CHAR(1)       | 작업 스케줄러에서 JOB 실행 여부 T: 실행 가능 F: 실행 불가능 |
| COMMENT        | VARCHAR(4000) | JOB에 대한 부가 설명                                        |

#### 칼럼 정보

##### EXEC_QUERY

JOB에 등록되어 실행되는 프로시저를 나타낸다.

##### INTERVAL_TYPE

JOB의 실행 주기가 설정되어 있는 경우, 시간의 단위를 나타낸다. 즉, INTERVAL 칼럼에 값이 있을 경우 그 값의 단위이다.

- YY: 년
- MM: 월
- DD: 일
- HH: 시
- MI: 분

##### STATE

JOB이 현재 실행되고 있는지 여부를 나타낸다.

- 0: 실행되지 않음
- 1: 실행되고 있음

##### EXEC_COUNT

JOB이 생성된 이후 등록된 프로시저가 몇 번 실행되었는지 총 횟수를 나타낸다.

##### ERROR_CODE

마지막으로 JOB이 실행되었을 때의 프로시저 수행이 실패하였을 때 에러 코드를 나타낸다. 성공하였을 때는 NULL이다.

##### IS_ENABLE

작업 스케줄러에서 JOB을 실행할 수 있는지 여부를 나타낸다.

- T: 실행 가능
- F: 실행 불가능

##### COMMENT

JOB에 대하여 설명을 나타낸다. 설명이 기술되지 않으면 NULL 값이 조회된다.

### SYS_LIBRARIES_

외부 라이브러리 객체에 대한 정보를 기록하는 메타 테이블이다.

| Column name   | Type          | Description                                              |
| ------------- | ------------- | -------------------------------------------------------- |
| LIBRARY_ID    | BIGINT        | 라이브러리 식별자                                        |
| USER_ID       | INTEGER       | 사용자 식별자                                            |
| LIBRARY_NAME  | VARCHAR(128)  | 라이브러리 이름                                          |
| FILE_SPEC     | VARCHAR(4000) | 동적 라이브러리 파일의 경로                              |
| DYNAMIC       | VARCHAR(1)    | 향후 사용 예약                                           |
| STATUS        | VARCHAR(7)    | 향후 사용 예약                                           |
| CREATED       | DATE          | 라이브러리 객체가 생성된 시간                            |
| LAST_DDL_TIME | DATE          | 라이브러리 객체에 마지막으로 DDL 변경 작업이 일어난 시간 |

#### 칼럼 정보

##### LIBRARY_ID

라이브러리 식별자로써 시스템 내에서 유일값을 가진다.

##### USER_ID

라이브러리 소유자의 사용자 식별자를 나타낸다.

##### LIBRARY_NAME

라이브러리 객체의 이름으로 시스템 내에서 유일값을 가진다.

##### FILE_SPEC

라이브러리 객체가 가리키는 동적 라이브러리 파일의 경로를 나타낸다. 라이브러리 파일이 위치하는 기본 경로 ($ALTIBASE_HOME/lib)에 대한 상대 경로로 표시된다.

### SYS_LOBS_

테이블에 정의된 LOB 칼럼의 정보를 기록하는 메타 테이블이다.

| Column name    | Type    | Description                                                  |
| -------------- | ------- | ------------------------------------------------------------ |
| USER_ID        | INTEGER | 사용자 식별자                                                |
| TABLE_ID       | INTEGER | 테이블 식별자                                                |
| COLUMN_ID      | INTEGER | 칼럼 식별자                                                  |
| TBS_ID         | INTEGER | 테이블스페이스 식별자                                        |
| LOGGING        | CHAR(1) | 향후 확장 예정                                               |
| BUFFER         | CHAR(1) | 향후 확장 예정                                               |
| IS_DEFAULT_TBS | CHAR(1) | LOB 칼럼 저장용 테이블스페이스 여부 T: 지정함 F: 지정하지 않음 |

#### 칼럼 정보

##### USER_ID

LOB 칼럼이 속한 테이블 소유자의 식별자로, SYS_USERS_ 메타 테이블의 한 USER_ID 값과 동일하다.

##### TABLE_ID

LOB 칼럼이 속한 테이블의 식별자로, SYS_TABLES_ 메타 테이블의 한 TABLE_ID 값과 동일하다.

##### COLUMN_ID

LOB 칼럼의 식별자이다.

##### TBS_ID

LOB 칼럼이 저장되는 테이블스페이스의 식별자이다.

##### IS_DEFAULT_TBS

LOB 칼럼 생성 시, 사용자가 LOB 칼럼이 저장될 테이블스페이스를 지정했는지를 나타낸다.

- T: 지정함
- F: 지정하지 않음

자세한 설명은 *SQL Reference*의 CREATE TABLE > LOB_STORAGE_CLAUSE 구문을 참조한다.

#### 참조 테이블

```
SYS_USERS_
SYS_TABLES_
SYS_COLUMNS_
```

### SYS_MATERIALIZED_VIEWS_

Materialized view에 대한 정보가 기록된 메타 테이블이다.

| Column name       | Type         | Description                                                  |
| ----------------- | ------------ | ------------------------------------------------------------ |
| USER_ID           | INTEGER      | 사용자 식별자                                                |
| MVIEW_ID          | INTEGER      | Materialized view의 식별자                                   |
| MVIEW_NAME        | VARCHAR(128) | Materialized view의 이름                                     |
| TABLE_ID          | INTEGER      | 테이블 식별자                                                |
| VIEW_ID           | INTEGER      | 뷰 식별자                                                    |
| REFRESH_TYPE      | CHAR(1)      | Refresh 타입                                                 |
| REFRESH_TIME      | CHAR(1)      | Refresh 시기                                                 |
| CREATED           | DATE         | Materialized view가 생성된 시간                              |
| LAST_DDL_TIME     | DATE         | Materialized view에 대해 마지막으로 DDL 변경 작업이 일어난 시간 |
| LAST_REFRESH_TIME | DATE         | Materialized view를 마지막으로 refresh한 시각                |

#### 칼럼 정보

##### USER_ID

Materialized view 소유자의 사용자 식별자로, SYS_USERS_ 메타 테이블의 한 USER_ID 값과 동일하다.

##### MVIEW_ID

Materialized view 식별자로, 데이터베이스가 자동으로 부여한다.

##### MVIEW_NAME

사용자가 명시한 materialized view의 이름이다.

##### TABLE_ID

Materialized view의 데이터 유지를 위해 자동으로 생성되는 테이블의 식별자이다. SYS_TABLES_ 메타 테이블에서 이 식별자로 조회해 보면 해당 materialized view의 이름과 동일한 이름의 테이블이 존재하는 것을 확인할 수 있다.

##### VIEW_ID

Materialized view의 데이터 유지를 위해 자동으로 생성되는 뷰의 식별자이다. SYS_VIEWS_ 메타 테이블에서 이 식별자로 해당 뷰를 조회할 수 있다.

##### REFRESH_TYPE

Materialized view의 리프레쉬 방법을 나타내는 값이다.

- C: COMPLETE
- F: FAST
- R: FORCE

##### REFRESH_TIME

Materialized view의 리프레쉬 시기를 나타내는 값이다.

- D: ON DEMAND
- C: ON COMMIT

##### CREATED

Materialized view가 생성된 일시를 나타낸다.

##### LAST_DDL_TIME

Materialized view에 대해 DDL 변경 작업이 마지막으로 일어난 일시를 나타낸다.

##### LAST_REFERESH_TIME

Materialized view를 마지막으로 리프레쉬한 일시를 나타낸다.

#### 참조 테이블

```
SYS_USERS_
SYS_TABLES_
SYS_VIEWS_
SYS_VIEW_PARSE_
```

### SYS_PACKAGES_

패키지에 대한 정보가 기록된 메타 테이블이다.

| Column name   | Type         | Description                                                  |
| ------------- | ------------ | ------------------------------------------------------------ |
| USER_ID       | INTEGER      | 패키지 소유자 식별자                                         |
| PACKAGE_OID   | BIGINT       | 패키지 식별자                                                |
| PACKAGE_NAME  | VARCHAR(128) | 패키지 이름                                                  |
| PACKAGE_TYPE  | INTEGER      | 패키지 유형. 패키지 스펙인지 패키지 바디인지를 나타낸다. 6: 패키지 스펙 7: 패키지 바디 |
| AUTHID        | INTEGER      | 패키지의 실행자 권한 0: 생성자 권한(DEFINER) 1: 사용자 권한(CURRENT_USER) |
| STATUS        | INTEGER      | 패키지의 상태를 나타낸다. INVALID이면 실행 불가능 상태이다. 0: VALID 1: INVALID |
| CREATED       | DATE         | 패키지를 생성한 일시                                         |
| LAST_DDL_TIME | DATE         | 패키지에 DDL 변경 작업이 마지막으로 일어난 일시              |

#### 칼럼 정보

##### USER_ID

패키지 소유자의 사용자 식별자로, SYS_USERS_ 메타 테이블의 한 USER_ID 값과 동일하다.

##### PACKAGE_OID

패키지의 식별자로, 시스템에 의해 자동으로 부여된다.

##### PACKAGE_NAME

패키지의 이름이다.

##### PACKAGE_TYPE

패키지 스펙인지 패키지 바디인지를 나타내는 값이다.

- 6: 패키지 스펙
- 7: 패키지 바디

##### AUTHID

패키지를 실행하는 권한을 나타내는 값이다.

- 0: 생성자 권한(DEFINER)
- 1: 사용자 권한(CURRENT_USER)

##### STATUS

패키지의 실행 가능 여부를 나타내는 값이다. 0 (VALID) 은 실행 가능함을 나타낸다.

- 0: VALID
- 1: INVALID

##### CREATED

패키지가 생성된 일시를 나타낸다.

##### LAST_DDL_TIME

패키지에 DDL 변경 작업이 마지막으로 일어난 일시를 나타낸다.

#### 참조 테이블

```
SYS_USERS_
```

### SYS_PACKAGE_PARAS_

패키지에 포함된 서브프로그램(저장 프로시저와 저장 함수)들의 인자 (parameter)들에 대한 정보가 기록된 메타 테이블이다.

| Column name  | Type          | Description                                       |
| ------------ | ------------- | ------------------------------------------------- |
| USER_ID      | INTEGER       | 패키지 소유자 식별자                              |
| OBJECT_NAME  | VARCHAR(128)  | 서브프로그램 이름                                 |
| PACKAGE_NAME | VARCHAR(128)  | 패키지 이름                                       |
| PACKAGE_OID  | BIGINT        | 패키지 식별자                                     |
| SUB_ID       | INTEGER       | 서브프로그램 식별자                               |
| SUB_TPYE     | INTEGER       | 서브프로그램 유형. 0: 프로시저 1: 함수            |
| PARA_NAME    | VARCHAR(128)  | 서브프로그램의 파라미터 이름                      |
| PARA_ORDER   | INTEGER       | 파라미터의 순서. 첫번째 파라미터의 경우 1을 가짐. |
| INOUT_TYPE   | INTEGER       | 파라미터의 입력, 출력, 입출력 여부                |
| DATA_TYPE    | INTEGER       | 파라미터의 데이터 타입                            |
| LANG_ID      | INTEGER       | 파라미터 타입 언어 식별자                         |
| SIZE         | INTEGER       | 파라미터 타입의 크기                              |
| PRECISION    | INTEGER       | 파라미터 타입의 precision                         |
| SCALE        | INTEGER       | 파라미터 타입의 scale                             |
| DEFAULT_VAL  | VARCHAR(4000) | 파라미터의 기본값                                 |

#### 칼럼 정보

##### USER_ID

저장 프로시저 또는 저장 함수 소유자의 사용자 식별자로, SYS_USERS_ 메타 테이블의 한 USER_ID 값과 동일하다.

##### OBJECT_NAME

서브프로그램의 이름이다.

##### PACKAGE_NAME

패키지의 이름이다.

##### PACKAGE_OID

패키지의 식별자로, SYS_PACKAGES_ 메타 테이블에서 패키지 스펙에 해당하는 PACKAGE_OID 값들 중 하나와 동일하다.

##### SUB_ID

서브프로그램의 식별자이다. 패키지 내에서 서브프로그램들의 식별자는 1부터 시작되며 작성한 순서대로 번호가 부여된다.

##### SUB_TYPE

서브프로그램이 저장 프로시저인지 또는 저장 함수인지를 나타낸다.

- 0: 프로시저
- 1: 함수

##### PARA_NAME

서브프로그램의 파라미터 이름이다.

##### PARA_ORDER

여러 파라미터들 중 해당 파라미터가 몇번째 정의된 파라미터인지를 나타내는 값이다.

##### INOUT_TYPE

저장 프로시저 또는 저장 함수의 파라미터가 입력인자, 출력인자, 또는 입출력인자인지를 나타낸다.

- 0: IN
- 1: OUT
- 2: IN OUT

##### DATA_TYPE

파라미터의 데이터 타입 식별자이다. 데이터 타입 식별자 값은 SYS_COLUMNS_ 메타 테이블의 DATA_TYPE 칼럼 설명을 참조한다.

데이터 타입에 대한 자세한 내용은 1장을 참조한다.

##### LANG_ID

타입 (CHAR, VARCHAR)의 언어 속성 정보를 나타내는 칼럼이다.

##### SIZE

데이터 타입의 물리적 크기이다.

##### PRECISION

인자 데이터 타입의 정밀도 (precision)으로, 사용자가 지정하거나 또는 시스템이 기본 값으로 부여한다. 타입의 경우 사용자가 정의한 타입의 길이이다.

##### SCALE

인자 데이터 타입의 scale로, 사용자가 지정하거나 또는 시스템이 기본 값으로 부여한다. 타입에 따라 이 값은 사용하지 않을 수 있다.

데이터 타입의 precision 과 scale에 대한 상세한 내용은 1장을 참조한다.

##### DEFAULT_VAL

파라미터 정의 시 사용자가 지정하는 파라미터 기본 값이다.

#### 참조 테이블

```
SYS_USERS_
SYS_PACKAGES_
```

### SYS_PACKAGE_PARSE_

사용자가 정의한 패키지의 구문 텍스트를 기록하는 메타 테이블이다.

| Column name  | Type         | Description                                                  |
| ------------ | ------------ | ------------------------------------------------------------ |
| USER_ID      | INTEGER      | 패키지 소유자 식별자                                         |
| PACKAGE_OID  | BIGINT       | 패키지 식별자                                                |
| PACKAGE_TYPE | INTEGER      | 패키지 유형. 패키지 스펙인지 패키지 바디인지를 나타낸다. 6: 패키지 스펙 7: 패키지 바디 |
| SEQ_NO       | INTEGER      | 나뉘어 여러 레코드로 저장된 구문들 중 레코드의 순서          |
| PARSE        | VARCHAR(100) | 나뉘어 저장된 구문                                           |

#### 칼럼 정보

##### USER_ID

패키지 소유자의 사용자 식별자로, SYS_USERS_ 메타 테이블의 한 USER_ID 값과 동일하다.

##### PACKAGE_OID

패키지의 식별자로, SYS_PACKAGES_ 메타 테이블의 한 PACKAGE_OID 값과 동일하다.

##### PACKAGE_TYPE

패키지 스펙인지 패키지 바디인지를 나타내는 값이다.

- 6: 패키지 스펙
- 7: 패키지 바디

##### SEQ_NO

패키지의 구문 정보를 나누어서 SYS_PACKAGE_PARSE_에 여러 개의 레코드로 저장할 때, 각 레코드의 순서를 나타낸다.

##### PARSE

패키지 구문의 문자열의 조각이다. 한 PACKAGE_OID 값으로 레코드들을 검색하여 SEQ_NO 순서대로 PARSE 값을 합치면 패키지 생성 구문이 된다.

#### 참조 테이블

```
SYS_USERS_
SYS_PACKAGES_
```

### SYS_PACKAGE_RELATED_

패키지 내에 포함된 저장 프로시저와 저장 함수들이 참조하는 테이블, 시퀀스, 저장 프로시저, 저장 함수, 또는 뷰들에 대한 정보가 기록된 메타 테이블이다.

| Column name         | Type         | Description                                 |
| ------------------- | ------------ | ------------------------------------------- |
| USER_ID             | INTEGER      | 패키지 소유자 식별자                        |
| PACKAGE_OID         | BIGINT       | 패키지 식별자                               |
| RELATED_USER_ID     | INTEGER      | 패키지 내에서 참조하는 객체의 소유자 식별자 |
| RELATED_OBJECT_NAME | VARCHAR(128) | 패키지 내에서 참조하는 객체의 이름          |
| RELATED_OBJECT_TYPE | INTEGER      | 패키지 내에서 참조하는 객체의 타입          |

#### 칼럼 정보

##### USER_ID

패키지 소유자의 사용자 식별자로, SYS_USERS_ 메타 테이블의 한 USER_ID 값과 동일하다.

##### PACKAGE_OID

패키지의 식별자로, SYS_PACKAGES_ 메타 테이블의 한 PACKAGE_OID 값과 동일하다.

##### RELATED_USER_ID

저장 프로시저가 접근하는 객체 소유자의 사용자 식별자로, SYS_USERS_ 메타 테이블의 한 USER_ID 값과 동일하다.

##### RELATED_OBJECT_NAME

저장 프로시저가 접근하는 객체의 이름이다.

##### RELATED_OBJECT_TYPE

저장 프로시저가 접근하는 객체의 타입을 나타낸다. 가능한 값은 다음과 같다.

- 0: 저장 프로시저
- 1: 저장 함수
- 2: 테이블, 시퀀스, 뷰
- 3: 타입세트
- 4: 데이터베이스 링크

#### 참조 테이블

```
SYS_USERS_
SYS_PACKAGES_  
SYS_TABLES_
```

### SYS_PART_INDICES_

파티션드 인덱스를 관리하기 위한 메타 테이블이다. SYS_INDICES_의 IS_PARTITIONED가 ‘Y’로 되어 있는 파티션드 인덱스에 대한 정보이다.

| Column name     | Type    | Description                 |
| --------------- | ------- | --------------------------- |
| USER_ID         | INTEGER | 사용자 식별자               |
| TABLE_ID        | INTEGER | 테이블 식별자               |
| INDEX_ID        | INTEGER | 인덱스 식별자               |
| PARTITION_TYPE  | INTEGER | 파티션 타입                 |
| IS_LOCAL_UNIQUE | CHAR(1) | 로컬 유니크 인덱스인지 여부 |

#### 칼럼 정보

##### USER_ID

인덱스 소유자의 사용자 식별자로, SYS_USERS_ 메타 테이블의 한 USER_ID 값과 동일하다.

##### TABLE_ID

인덱스를 생성한 테이블의 테이블 식별자로, SYS_TABLES_ 메타 테이블의 한 TABLE_ID 값과 동일하다.

##### INDEX_ID

인덱스 식별자로, SYS_INDICES_ 메타 테이블의 한 INDEX_ID 값과 동일하다.

##### PARTITION_TYPE

파티션 타입이 지역 (LOCAL)인지 글로벌 (GLOBAL)인지를 나타낸다. 그러나 현재 글로벌 파티션 타입을 지원하지 않으므로, 이 값은 항상 0이다.

- 0: LOCAL
- 1: GLOBAL

##### IS_LOCAL_UNIQUE

인덱스가 로컬 유니크 인덱스인지 여부를 가리키는 것으로, 'T' 또는 'F'이다.

- T: 로컬 유니크 인덱스이다.
- F: 로컬 유니크 인덱스가 아니다.

#### 참조 테이블

```
SYS_USERS_
SYS_TABLES_
SYS_INDICES_
```

### SYS_PART_KEY_COLUMNS_

파티션드 객체의 파티셔닝 키 칼럼에 대한 정보를 저장하는 메타 테이블이다.

| Column name      | Type    | Description                                 |
| ---------------- | ------- | ------------------------------------------- |
| USER_ID          | INTEGER | 사용자 식별자                               |
| PARTITION_OBJ_ID | INTEGER | 파티션드 객체 식별자                        |
| COLUMN_ID        | INTEGER | 칼럼 식별자                                 |
| OBJECT_TYPE      | INTEGER | 객체 타입                                   |
| PART_COL_ORDER   | INTEGER | 파티셔닝 키 내에서 칼럼의 위치 (0부터 시작) |

#### 칼럼 정보

##### USER_ID

인덱스 소유자의 사용자 식별자로, SYS_PART_INDICES_ 메타 테이블의 한 USER_ID 값과 동일하다.

##### PARTITION_OBJ_ID

파티션드 객체 식별자로, SYS_PART_TABLES_ 메타 테이블의 한 TABLE_ID 값 또는 SYS_PART_INDICES_메타 테이블의 한 INDEX_ID값과 동일하다.

##### COLUMN_ID

인덱스를 생성한 테이블의 테이블 식별자로, SYS_COLUMNS_

메타 테이블의 한 COLUMN_ID 값과 동일하다.

##### OBJECT_TYPE

객체 타입을 나타내는 식별자이다.

- 0: 테이블 (TABLE)
- 1: 인덱스 (INDEX)

##### PART_COL_ORDER

파티셔닝 키 내에서 칼럼의 위치를 나타낸다 (0부터 시작).

#### 참조 테이블

```
SYS_PART_INDICES_
SYS_TABLE_PARTITIONS_
SYS_COLUMNS_
```

### SYS_PART_LOBS_

파티션별로 LOB 칼럼을 관리하기 위한 메타 테이블이다.

| Column name  | Type    | Description           |
| ------------ | ------- | --------------------- |
| USER_ID      | INTEGER | 사용자 식별자         |
| TABLE_ID     | INTEGER | 테이블 식별자         |
| PARTITION_ID | INTEGER | 파티션 식별자         |
| COLUMN_ID    | INTEGER | 칼럼 식별자           |
| TBS_ID       | INTEGER | 테이블스페이스 식별자 |
| LOGGING      | CHAR(1) | 향후 확장 예정        |
| BUFFER       | CHAR(1) | 향후 확장 예정        |

#### 칼럼 정보

##### USER_ID

LOB 칼럼이 속한 테이블 소유자의 사용자 식별자로, SYS_USERS_ 메타 테이블의 한 USER_ID 값과 동일하다.

##### TABLE_ID

LOB 칼럼이 속한 테이블의 식별자, SYS_TABLES_ 메타 테이블의 한 TABLE_ID 값과 동일하다.

##### PARTITION_ID

LOB 칼럼이 저장되는 파티션의 식별자이다.

##### COLUMN_ID

LOB 칼럼의 식별자이다.

##### TBS_ID

LOB 칼럼이 저장되는 테이블스페이스의 식별자이다.

#### 참조 테이블

```
SYS_USERS_
SYS_TABLES_
SYS_PART_TABLES_
SYS_COLUMNS_
```

### SYS_PART_TABLES_

파티션드 테이블을 관리하기 위한 메타 테이블이다. SYS_PART_TABLE_에 들어가는 테이블 정보는 SYS_TABLES_에서 IS_PARTITIONED가 ‘Y’로 되어 있는 파티션드 테이블에 대한 정보이다.

| Column name         | Type    | Description                                |
| ------------------- | ------- | ------------------------------------------ |
| USER_ID             | INTEGER | 사용자 식별자                              |
| TABLE_ID            | INTEGER | 테이블 식별자                              |
| PARTITION_METHOD    | INTEGER | 파티셔닝 메소드                            |
| PARTITION_KEY_COUNT | INTEGER | 파티션 키 칼럼의 개수                      |
| ROW_MOVEMENT        | CHAR(1) | 갱신된 레코드에 대한 파티션 이동 허용 여부 |

#### 칼럼 정보

##### USER_ID

인덱스 소유자의 사용자 식별자로, SYS_USERS_ 메타 테이블의 한 USER_ID 값과 동일하다.

##### TABLE_ID

인덱스를 생성한 테이블의 테이블 식별자로, SYS_TABLES_ 메타 테이블의 한 TABLE_ID 값과 동일하다.

##### PARTITION_METHOD

파티셔닝 메소드를 나타낸다.

- 0: 범위 (RANGE)
- 1: 해쉬 (HASH)
- 2: 리스트 (LIST)

##### ROW_MOVEMENT

파티션 키 칼럼의 값이 갱신 (UPDATE)될 때, 갱신된 레코드를 다른 파티션으로 이동할 것인지에 대한 허가 여부를 결정하는 것이다.

- T: 이동 허가
- F: 이동 불허가

#### 참조 테이블

```
SYS_USERS_
SYS_TABLES_
```

### SYS_PASSWORD_HISTORY_

패스워드 관리 정책을 설정한 사용자의 패스워드 변경 내역을 기록하는 메타 테이블이다.

| Column name   | Type         | Description            |
| ------------- | ------------ | ---------------------- |
| USER_ID       | INTEGER      | 사용자 식별자          |
| PASSWORD      | VARCHAR(256) | 사용자 패스워드        |
| PASSWORD_DATE | DATE         | 사용자 패스워드 변경일 |

### SYS_PASSWORD_LIMITS_

사용자 생성 시 계정에 대해 지정한 패스워드 관리 정책과 계정의 현재 상태를 기록하는 메타 테이블이다.

| Column name              | Type         | Description                                                  |
| ------------------------ | ------------ | ------------------------------------------------------------ |
| USER_ID                  | INTEGER      | 사용자 식별자                                                |
| USER_NAME                | VARCHAR(128) | 사용자 이름                                                  |
| ACCOUNT_STATUS           | VARCHAR(30)  | 계정의 현재 상태를 표시 EXPIRED EXPIRED(GRACE) LOCKED(TIMED) LOCKED EXPIRED & LOCKED(TIMED) EXPIRED(GRACE) & LOCKED(TIMED) EXPIRED & LOCKED EXPIRED(GRACE) & LOCKED |
| REMAIN_GRACE_DAY         | VARCHAR(10)  | 패스워드 만료 후 남은 유예기간                               |
| FAILED_LOGIN_ATTEMPTS    | VARCHAR(10)  | 로그인 실패 허용 최대 횟수                                   |
| PASSWORD_LOCK_TIME       | VARCHAR(10)  | 계정이 한 번 잠긴 후 다시 풀리기 위해 경과되어야 하는 기간   |
| PASSWORD_LIFE_TIME       | VARCHAR(10)  | 패스워드 유효기간                                            |
| PASSWORD_GRACE_TIME      | VARCHAR(10)  | 패스워드 만료 후 유예기간                                    |
| PASSWORD_REUSE_TIME      | VARCHAR(10)  | 동일한 패스워드가 재사용 가능해지기 위해 경과해야 하는 기간  |
| PASSWORD_REUSE_MAX       | VARCHAR(10)  | 동일한 패스워드의 재사용 가능 횟수                           |
| PASSWORD_VERIFY_FUNCTION | VARCHAR(128) | 패스워드를 검증할 콜백 함수(Callback Function)               |

### SYS_PRIVILEGES_

Altibase가 지원하는 권한의 종류 정보를 기록하는 메타 테이블이다. 권한에 대한 자세한 설명은 데이터베이스 권한 관리 또는 *SQL Reference*의 GRANT문 설명을 참조한다.

| Column name | Type         | Description |
| ----------- | ------------ | ----------- |
| PRIV_ID     | INTEGER      | 권한 식별자 |
| PRIV_TYPE   | INTEGER      | 권한 타입   |
| PRIV_NAME   | VARCHAR(128) | 권한 이름   |

#### 칼럼 정보

##### PRIV_ID

권한 식별자로 시스템이 내부적으로 정의한 값이다.

##### PRIV_TYPE

권한의 타입을 나타낸다.

- 1: 객체 권한
- 2: 시스템 권한

##### PRIV_NAME

권한의 이름이다.

### SYS_PROCEDURES_

저장 프로시저와 저장 함수들에 대한 정보로 저장 프로시저 이름, 리턴 타입, 파라미터 개수, 실행 가능 여부 등을 기록하는 테이블이다.

| Column name      | Type         | Description                                                  |
| ---------------- | ------------ | ------------------------------------------------------------ |
| USER_ID          | INTEGER      | 저장 프로시저 소유자 식별자                                  |
| PROC_OID         | BIGINT       | 저장 프로시저 식별자                                         |
| PROC_NAME        | VARCHAR(128) | 저장 프로시저 이름                                           |
| OBJECT_TYPE      | INTEGER      | 저장 프로시저, 저장 함수 또는 타입세트 인지를 나타냄         |
| STATUS           | INTEGER      | 객체의 상태를 나타낸다. INVALID이면 실행 불가능 상태이다. 0: VALID 1: INVALID |
| AUTHID           | INTEGER      | 프,로시저 또는 함수의 실행자 권한 0: 생성자 권한(DEFINER) 1: 사용자 권한(CURRENT_USER) |
| PARA_NUM         | INTEGER      | 저장 프로시저 파라미터 개수                                  |
| RETURN_DATA_TYPE | INTEGER      | 저장 함수의 리턴 데이터 타입                                 |
| RETURN_LANG_ID   | INTEGER      | 리턴 타입 언어 식별자                                        |
| RETURN_SIZE      | INTEGER      | 저장 함수의 리턴 데이터 타입의 크기                          |
| RETURN_PRECISION | INTEGER      | 저장 함수의 리턴 데이터 타입의 precision                     |
| RETURN_SCALE     | INTEGER      | 저장 함수의 리턴 데이터 타입의 scale                         |
| PARSE_NO         | INTEGER      | SYS_PROC_PARSE_에 구문의 조각들을 저장하고 있는 레코드의 개수 |
| PARSE_LEN        | INTEGER      | SYS_PROC_PARSE_에 저장된 구문의 전체 길이                    |
| CREATED          | DATE         | 저장 프로시저를 생성한 날짜                                  |
| LAST_DDL_TIME    | DATE         | 저장 프로시저에 DDL 변경 작업이 마지막으로 일어난 시간       |

#### 칼럼 정보

##### USER_ID

저장 프로시저 또는 저장 함수 소유자의 사용자 식별자로, SYS_USERS_ 메타 테이블의 한 USER_ID 값과 동일하다.

##### PROC_OID

저장 프로시저 또는 저장 함수의 식별자로, 시스템에 의해 자동으로 부여된다.

##### PROC_NAME

저장 프로시저 또는 저장 함수의 이름이다.

##### OBJECT_TYPE

저장 프로시저와 저장 함수를 구별하는 값이다. 저장 함수는 저장 프로시저와 달리 하나의 리턴 값을 가진다.

- 0: 저장 프로시저
- 1: 저장 함수
- 3: 타입 세트

##### STATUS

저장프로시저 또는 함수의 실행 가능 여부를 나타내는 값이다. 0 (VALID) 은 실행가능함을 나타낸다.

저장 프로시저 또는 저장 함수가 접근하는 객체에 DDL문을 수행하면, 관련 저장 프로시저 또는 저장 함수는 무효한 상태가 된다. 예를 들어 저장 프로시저가 접근하는 테이블에 새로운 칼럼이 추가되면 관련 저장 프로시저는 재 컴파일 후 VALID 상태가 되면 실행할 수 있다.

- 0: VALID
- 1: INVALID

##### AUTHID

프로시저 또는 함수를 실행하는 권한을 나타내는 값이다.

- 0: 생성자 권한(DEFINER)
- 1: 사용자 권한(CURRENT_USER)

##### PARA_NUM

저장 프로시저 또는 저장 함수에 정의된 파라미터 개수를 나타낸다.

##### RETURN_DATA_TYPE

저장 함수의 리턴값에 대한 데이터 타입의 식별자이다. 데이터 타입 식별자 값은 SYS_COLUMNS_ 메타 테이블의 DATA_TYPE 칼럼 설명을 참조한다.

데이터 타입에 대한 자세한 내용은 1장을 참조한다.

##### RETURN_LANG_ID

타입 (CHAR, VARCHAR)의 언어 속성 정보를 나타내는 칼럼이다.

##### RETURN_SIZE

리턴 데이터 타입의 물리적 크기이다.

##### RETURN_PRECISION

리턴 데이터 타입의 정밀도 (precision)로, 사용자가 지정하거나 또는 시스템이 기본 값으로 부여한다. 타입의 경우 사용자가 정의한 타입의 길이이다.

##### RETURN_SCALE

리턴 데이터 타입의 scale로, 사용자가 지정하거나 또는 시스템이 기본 값으로 부여한다. 타입에 따라 이 값은 사용하지 않을 수 있다.

데이터 타입의 precision 과 scale에 대한 상세한 내용은 1장을 참조한다.

##### PARSE_NO

저장 프로시저 또는 저장 함수 구문은 SYS_PROC_PARSE_ 메타 테이블에 나눠져 여러 레코드로 저장되는데, 이 값은 저장하는 레코드의 수를 나타낸다.

##### PARSE_LEN

저장 프로시저 또는 저장 함수 구문은 SYS_PROC_PARSE_ 메타 테이블에 나눠져 여러 레코드로 저장되는데 저장하는 전체 구문의 문자열 길이이다.

##### LAST_DDL_TIME

저장 프로시저에 DDL 변경 작업이 마지막으로 일어난 시간을 나타낸다.

#### 참조 테이블

```
SYS_USERS_
```

### SYS_PROC_PARAS_

저장 프로시저와 저장 함수들의 인자 (parameter)들에 대한 정보를 기록하는 테이블이다.

| Column name | Type          | Description                                       |
| ----------- | ------------- | ------------------------------------------------- |
| USER_ID     | INTEGER       | 저장 프로시저 소유자 식별자                       |
| PROC_OID    | BIGINT        | 저장 프로시저 식별자                              |
| PARA_NAME   | VARCHAR(128)  | 파라미터 이름                                     |
| PARA_ORDER  | INTEGER       | 파라미터의 순서. 첫번째 파라미터의 경우 1을 가짐. |
| INOUT_TYPE  | INTEGER       | 파라미터의 입력, 출력, 입출력 여부                |
| DATA_TYPE   | INTEGER       | 파라미터의 데이터 타입                            |
| LANG_ID     | INTEGER       | 파라미터 타입 언어 식별자                         |
| SIZE        | INTEGER       | 파라미터 타입의 크기                              |
| PRECISION   | INTEGER       | 파라미터 타입의 precision                         |
| SCALE       | INTEGER       | 파라미터 타입의 scale                             |
| DEFAULT_VAL | VARCHAR(4000) | 파라미터의 기본 값                                |

#### 칼럼 정보

##### USER_ID

저장 프로시저 또는 저장 함수 소유자의 사용자 식별자로, SYS_USERS_ 메타 테이블의 한 USER_ID 값과 동일하다.

##### PROC_OID

저장 프로시저 또는 저장 함수의 식별자로, SYS_PROCEDURES_ 메타 테이블의 한 PROC_OID 값과 동일하다.

##### PARA_NAME

파라미터의 이름이다.

##### PARA_ORDER

여러 파라미터들 중 해당 파라미터가 몇번째 정의된 파라미터인지를 나타내는 값이다.

##### INOUT_TYPE

저장 프로시저 또는 저장 함수의 파라미터가 입력인자, 출력인자, 또는 입출력인자인지를 나타낸다.

- 0: IN
- 1: OUT
- 2: IN OUT

##### DATA_TYPE

파라미터의 데이터 타입 식별자이다. 데이터 타입 식별자 값은 SYS_COLUMNS_ 메타 테이블의 DATA_TYPE 칼럼 설명을 참조한다.

데이터 타입에 대한 자세한 내용은 1장을 참조한다.

##### LANG_ID

타입 (CHAR, VARCHAR)의 언어 속성 정보를 나타내는 칼럼이다.

##### SIZE

데이터 타입의 물리적 크기이다.

##### PRECISION

인자 데이터 타입의 정밀도 (precision)으로, 사용자가 지정하거나 또는 시스템이 기본 값으로 부여한다. 타입의 경우 사용자가 정의한 타입의 길이이다.

##### SCALE

인자 데이터 타입의 scale로, 사용자가 지정하거나 또는 시스템이 기본 값으로 부여한다. 타입에 따라 이 값은 사용하지 않을 수 있다.

데이터 타입의 precision 과 scale에 대한 상세한 내용은 1장을 참조한다.

##### DEFAULT_VAL

파라미터 정의 시 사용자가 지정하는 파라미터 기본 값이다.

#### 참조 테이블

```
SYS_USERS_
SYS_PROCEDURES_
```

### SYS_PROC_PARSE_

사용자가 정의한 저장 프로시저와 저장 함수들의 구문 텍스트를 기록하는 테이블이다.

| Column name | Type         | Description                                         |
| ----------- | ------------ | --------------------------------------------------- |
| USER_ID     | INTEGER      | 저장 프로시저 또는 저장 함수의 소유자 식별자        |
| PROC_OID    | BIGINT       | 저장 프로시저 객체 식별자                           |
| SEQ_NO      | INTEGER      | 나뉘어 여러 레코드로 저장된 구문들 중 레코드의 순서 |
| PARSE       | VARCHAR(100) | 나뉘어진 저장 프로시저 또는 저장 함수의 구문        |

#### 칼럼 정보

##### USER_ID

저장 프로시저 소유자의 사용자 식별자로, SYS_USERS_ 메타 테이블의 한 USER_ID 값과 동일하다.

##### PROC_OID

저장 프로시저 또는 저장 함수의 식별자로, SYS_PROCEDURES_ 메타 테이블의 한 PROC_OID 값과 동일하다.

##### SEQ_NO

한 저장 프로시저의 구문 정보를 나누어서 SYS_PROC_PARSE_에 여러 개의 레코드로 저장할 때, 각 레코드의 순서를 나타낸다.

##### PARSE

저장 프로시저 또는 저장 함수 구문의 문자열의 조각이다. 한 PROC_OID 값으로 레코드들을 검색하여 SEQ_NO 순서대로 PARSE 값을 합치면 저장 프로시저 전체 구문을 생성할 수 있다.

#### 참조 테이블

```
SYS_USERS_
SYS_PROCEDURES_
```

### SYS_PROC_RELATED_

저장 프로시저와 저장 함수들이 접근하는 테이블, 시퀀스, 저장 프로시저, 저장 함수, 또는 뷰들에 대한 정보를 기록하는 테이블이다.

| Column name         | Type         | Description                                        |
| ------------------- | ------------ | -------------------------------------------------- |
| USER_ID             | INTEGER      | 저장 프로시저 소유자 식별자                        |
| PROC_OID            | BIGINT       | 저장 프로시저 식별자                               |
| RELATED_USER_ID     | INTEGER      | 저장 프로시저 내에서 참조하는 객체의 소유자 식별자 |
| RELATED_OBJECT_NAME | VARCHAR(128) | 저장 프로시저 내에서 참조하는 객체의 이름          |
| RELATED_OBJECT_TYPE | INTEGER      | 저장 프로시저 내에서 참조하는 객체의 타입          |

저장 프로시저 PROC1이 테이블 t1에 INSERT 작업을 수행하는 경우, PROC1의 소유자 식별자와 저장 프로시저 식별자가 각각 USER_ID와 PROC_OID에 저장되고, 테이블 t1의 소유자 ID와 테이블 이름은 각각 RELATED_USER_ID, RELATED_OBJECT_NAME에 저장되며, RELATED_OBJECT_TYPE에는 2 (TABLE을 나타냄)가 저장된다.

#### 칼럼 정보

##### USER_ID

저장 프로시저 또는 저장 함수 소유자의 사용자 식별자로, SYS_USERS_ 메타 테이블의 한 USER_ID 값과 동일하다.

##### PROC_OID

저장 프로시저 또는 저장 함수의 식별자로, SYS_PROCEDURES_ 메타 테이블의 한 PROC_OID 값과 동일하다.

##### RELATED_USER_ID

저장 프로시저가 접근하는 객체 소유자의 사용자 식별자로, SYS_USERS_ 메타 테이블의 한 USER_ID 값과 동일하다.

##### RELATED_OBJECT_NAME

저장 프로시저가 접근하는 객체의 이름이다.

##### RELATED_OBJECT_TYPE

저장 프로시저가 접근하는 객체의 타입을 나타낸다. 가능한 값은 다음과 같다.

- 0: 저장 프로시저
- 1: 저장 함수
- 2: 테이블, 시퀀스, 뷰
- 3: 타입세트
- 4: 데이터베이스 링크

#### 참조 테이블

```
SYS_USERS_
SYS_PROCEDURES_
SYS_TABLES_
```

### SYS_RECYCLEBIN_

휴지통에서 관리하는 테이블의 정보를 저장하는 메타 테이블이다. RECYCLEBIN_ENABLE 프로퍼티의 값이 1로 설정된 경우 DROP 구문으로 휴지통으로 이동하는 테이블이 저장된다.

| Column name         | Type         | Description                                                  |
| ------------------- | ------------ | ------------------------------------------------------------ |
| USER_NAME           | VARCHAR(128) | 테이블 소유자                                                |
| TABLE_NAME          | VARCHAR(128) | 삭제될 때 휴지통에서 관리하기 위해 시스템에서 생성되는 테이블 이름. 동일한 이름의 테이블이 여러 번 삭제될 수 있으며, 휴지통에서 이를 관리하기 위해 테이블 이름을 별도로 생성한다. |
| ORIGINAL_TABLE_NAME | VARCHAR(128) | 삭제되기 전의 테이블의 이름.                                 |
| TBS_NAME            | VARCHAR(128) | 테이블이 저장된 테이블스페이스 이름                          |
| MEMORY_SIZE         | BIGINT       | 삭제된 메모리 테이블이 메모리에서 차지하는 전체 크기         |
| DISK_SIZE           | BIGINT       | 삭제된 디스크 테이블이 디스크에서 차지하는 전체 크기         |
| DROPPED             | DATE         | 테이블이 삭제(Drop)된 시간                                   |

#### 칼럼 정보

##### TABLE_NAME

테이블이 DROP 될 때 휴지통에서 관리하기 위해 시스템에서 생성하는 테이블 이름이다. 동일한 이름의 테이블(ORIGINAL_TABLE_NAME)이 여러 번 삭제될 경우 휴지통에서 테이블을 관리하기 위해서 새로운 이름이 생성된다.

### SYS_REPLICATIONS_

이중화 관련 정보를 기록하고 있는 메타 테이블이다.

| Column name              | Type        | Description                                             |
| ------------------------ | ----------- | ------------------------------------------------------- |
| LAST_USED_HOST_NO        | INTEGER     | 가장 최근에 사용한 원격 서버                            |
| HOST_COUNT               | INTEGER     | 원격 서버 개수                                          |
| IS_STARTED               | INTEGER     | 이중화 시작 여부                                        |
| XSN                      | BIGINT      | 송신자가 XLog 전송을 재개할 재시작 SN(Seqence Number)13 |
| ITEM_COUNT               | INTEGER     | 이중화 대상 테이블 개수                                 |
| CONFLICT_RESOLUTION      | INTEGER     | 이중화 충돌 해결 방법                                   |
| REPL_MODE                | INTEGER     | 기본 이중화 모드                                        |
| ROLE                     | INTEGER     | 송신 쓰레드의 역할                                      |
| OPTIONS                  | INTEGER     | 부가적인 이중화 기능을 위한 플래그                      |
| INVALID_RECOVERY         | INTEGER     | 이중화 복구 가능 여부                                   |
| REMOTE_FAULT_DETECT_TIME | DATE        | 원격 서버의 장애 감지 시각                              |
| GIVE_UP_TIME             | DATE        | 가장 최근에 이중화를 포기한 일시                        |
| REPLICATION_NAME         | VARCHAR(40) | 이중화 이름                                             |
| GIVE_UP_XSN              | BIGINT      | 가장 최근에 이중화를 포기했을 시점의 XSN                |
| PARALLEL_APPLIER_COUNT   | INTEGER     | 병렬 적용자(Applier)의 수                               |
| REMOTE_XSN               | BIGINT      | 원격 서버에서 가장 최근에 처리한 SN                     |
| APPLIER_INIT_BUFFER_SIZE | BIGINT      | applier buffer 의 초기 사이즈                           |
| PEER_REPLICATION_NAME    | VARCHAR(40) | 로컬 이중화한 원격 이중화 이름                          |
| REMOTE_LAST_DDL_XSN      | BIGINT      | 원격 서버에서 가장 최근에 처리한 DDL SN                 |

[13] SN(Sequence Number): 로그 레코드의 식별 번호

#### 칼럼 정보

##### REPLICATION_NAME

이중화 이름으로, 이중화 생성 시 사용자가 명시한다.

##### LAST_USED_HOST_NO

가장 최근에 사용한 원격 서버의 번호로, SYS_REPL_HOSTS_ 메타 테이블의 한 HOST_NO 값과 동일하다.

##### HOST_COUNT

이중화에 참여하는 원격 서버의 개수로, SYS_REPL_HOSTS_ 에 저장된 IP의 개수와 동일하다.

##### IS_STARTED

이중화 동작 여부를 나타낸다.

- 0: 중지
- 1: 이중화 수행 중

##### XSN

이중화가 시작될 때, 송신 쓰레드에서 로그 전송을 시작해야 할 SN을 나타낸다.

##### ITEM_COUNT

이중화 대상 테이블의 개수이다. 해당 이중화에 대해 SYS_REPL_ITEMS_ 메타 테이블에 이 수만큼 레코드들이 존재한다.

##### CONFLICT_RESOLUTION

이중화 충돌 해결 방법을 기록한다.

- 0: 기본 값
- 1: Master Server로 동작
- 2: Slave Server로 동작

이중화 충돌 해결 방법에 대한 자세한 설명은 *Replication Manual*을 참조한다.

##### REPL_MODE

이중화 생성시에 지정한 기본 이중화 모드이다.

- 0: LAZY MODE (기본 값)
- 2: EAGER MODE

기본 이중화 모드는 ALTER SESSION SET REPLICATION 구문으로 세션의 이중화 모드를 설정하지 않았을 때 사용된다.

기본 이중화 모드에 관한 자세한 내용은 *Replication Manual*을 참조하며, ALTER SESSION SET REPLICATION 구문에 관한 내용은 *SQL Reference*을 참조한다.

##### ROLE

송신 쓰레드의 역할을 나타낸다.

- 0: 이중화
- 1: Log Analyzer
- 2: Propagable Logging(이중화 로그 복제)
- 3: Propagation(복제 로그 전송)

자세한 내용은 Log Analyzer User's Manual을 참고한다.

##### OPTIONS

이중화 부가 기능을 나타내는 플래그이다. 이중화 옵션의 종류는 아래와 같으며, 각 옵션을 설정시 이진수로 제어되며, 십진수로 변환되어 표시된다. 두 개 이상의 옵션을 사용할 경우 각각의 옵션에 해당하는 이진수 합이 십진수로 반환된다.

- 0(00000000): 이중화 옵션을 사용하지 않음
- 1(00000001): 복구 옵션 사용
- 2(00000010): 오프라인 옵션 사용
- 4(00000100): 이중화 갭 해소 옵션 사용
- 8(00001000): 병렬 적용자 옵션 사용
- 16(00010000):이중화 트랜잭션 그룹 옵션 사용
- 32(00100000):로컬 이중화 옵션 사용
- 64(01000000):메타 로깅 옵션 사용

##### INVALID_RECOVERY

이중화를 이용하여 복구가 가능한지 여부를 나타낸다.

- 0: 복구 가능 상태
- 1: 복구 불가능 상태

##### REMOTE_FAULT_DETECT_TIME

이중화 동작 중에 원격 서버의 장애를 감지한 시점을 기록한다.

##### GIVE_UP_TIME

이 값은 가장 최근에 이중화를 포기했을 시점의 일시이다. 즉, 이중화 송신 쓰레드가 이중화 전송을 포기한 시점이다.

##### GIVE_UP_XSN

이 값은 가장 최근에 이중화를 포기했을 시점의 XSN이다.

##### PARALLEL_APPLIER_COUNT

병렬 적용자의 수를 나타낸다.

##### REMOTE_XSN

원격 서버에서 가장 최근에 처리한 SN 이다. Sender 재시작 시 해당 REMOTE_XSN보다 SN이 작은 로그는 보내지 않고 Skip한다..

##### APPLIER_INIT_BUFFER_SIZE

병렬 적용자 옵션(receiver applier option)을 설정하여 이중화를 수행할 경우, 병렬 적용자의 초기 버퍼 크기이다. 병렬 적용자의 큐(queue) 개수는 해당 값을 XLog Size 로 나눈 값으로 설정된다.

```
( applier queue size = applier_init_buffer_size / xlog size )
```

만약 병렬 적용자 큐의 수가 프로퍼티 REPLICATION_RECEIVER_APPLIER_QUEUE_SIZE 값보다 작다면 병렬 적용자 큐의 수는 프로퍼티 REPLICATION_RECEIVER_APPLIER_QUEUE_SIZE에 지정된 값으로 설정된다.

##### PEER_REPLICATION_NAME

로컬 이중화 옵션을 사용했을 때 원격 이중화의 이름이다.

##### REMOTE_LAST_DDL_XSN

원격 서버에서 가장 최근에 처리한 DDL의 SN 이다.

#### 예제

<예제> 다음은 생성된 이중화 rep1에 이중화 갭 해소 옵션과 병렬 적용자 옵션을 함께 사용할 때의 값을 반환한다.

```
iSQL> alter replication rep1 set gapless enable;
Alter success.
iSQL> alter replication rep1 set parallel 4;
Alter success.
iSQL> select options from system_.sys_replications_;
OPTIONS     
--------------
12           
1 row selected.
```

### SYS_REPL_HOSTS_

원격 서버에 관련된 정보를 가진 메타 테이블이다

| Column name      | Type        | Description                    |
| ---------------- | ----------- | ------------------------------ |
| HOST_NO          | INTEGER     | 호스트 식별자                  |
| REPLICATION_NAME | VARCHAR(40) | 이중화 이름                    |
| HOST_IP          | VARCHAR(64) | 원격 서버 IP 주소              |
| PORT_NO          | INTEGER     | 원격 서버 이중화 포트 번호     |
| CONN_TYPE        | VARCHAR(20) | 원격 서버 접속 방법            |
| IB_LATENCY       | VARCHAR(10) | rsocket의 RDMA_LATENCY 옵션 값 |

#### 칼럼 정보

##### HOST_NO

원격 서버의 일련 번호로, 시스템 시퀀스에 의해 자동으로 부여된다.

##### REPLICATION_NAME

사용자가 명시한 이중화 이름으로, SYS_REPLICATIONS_ 메타 테이블의 한 REPLICATION_NAME 값과 동일하다.

##### HOST_IP

원격 서버의 IP 주소이다.

##### PORT_NO

원격 서버의 이중화 포트 번호를 기록한다.

##### CONN_TYPE

원격 서버의 접속 방법을 나타낸다.

- TCP
- Unix Domain
- InfiniBand(IB)

##### IB_LATENCY

인피니밴드를 사용할 경우 rsocket의 RDMA_LATENCY 옵션 값을 나타낸다. CONN_TYPE이 IB가 아닌 경우에 이 값은 N/A이다.

#### 참조 테이블

```
SYS_REPLICATIONS_
```

### SYS_REPL_ITEMS_

이중화 대상 테이블에 관련된 정보를 가진 메타 테이블이다.

| Column name           | Type          | Description                         |
| --------------------- | ------------- | ----------------------------------- |
| REPLICATION_NAME      | VARCHAR(40)   | 이중화 이름                         |
| TABLE_OID             | BIGINT        | 테이블 객체 식별자                  |
| LOCAL_USER_NAME       | VARCHAR(128)  | 지역 서버의 대상 테이블 소유자 이름 |
| LOCAL_TABLE_NAME      | VARCHAR(128)  | 지역 서버의 대상 테이블 이름        |
| LOCAL_PARTITION_NAME  | VARCHAR(128)  | 지역 서버의 파티션 이름             |
| REMOTE_USER_NAME      | VARCHAR(128)  | 원격 서버의 대상 테이블 소유자 이름 |
| REMOTE_TABLE_NAME     | VARCHAR(128)  | 원격 서버의 대상 테이블 이름        |
| REMOTE_PARTITION_NAME | VARCHAR(128)  | 원격 서버의 파티션 이름             |
| IS_PARTITION          | CHAR(1)       | 파티션드 테이블인지 여부            |
| INVALID_MAX_SN        | BIGINT        | 건너 뛸 로그의 최대 SN              |
| CONDITION             | VARCHAR(1000) | Deprecated                          |
| REPLICATION_UNIT      | CHAR(1)       | 이중화 단위                         |

하나의 이중화 객체는 한 개 이상의 테이블들을 포함할 수 있으며, 이들 테이블 각각에 대해 SYS_REPL_ITEMS_에 레코드가 존재한다. 예를 들어 한 이중화가 10개의 테이블을 가지고 있다면, 이 이중화에 대한 총 10개의 레코드가 이 메타 테이블에 기록된다.

#### 칼럼 정보

##### REPLICATION_NAME

사용자가 명시한 이중화 이름으로, SYS_REPLICATIONS_ 메타 테이블의 한 REPLICATION_NAME 값과 동일하다.

##### TABLE_OID

이중화 대상 테이블 또는 파티션의 식별자로, SYS_TABLES_ 메타 테이블의 한 TABLE_OID 값 또는 SYS_TABLES_PARTITIONS_의 한 PARTITION_OID 값과 동일하다.

##### LOCAL_USER_NAME

지역 서버의 이중화 대상 테이블 소유자의 사용자 이름으로, SYS_USERS_ 메타 테이블의 한 USER_NAME 값과 동일하다.

##### LOCAL_TABLE_NAME

지역 서버의 이중화 대상 테이블의 이름으로, SYS_TABLES_ 메타 테이블의 한 TABLE_NAME 값과 동일하다.

##### LOCAL_PARTITION_NAME

지역 서버의 이중화 대상 파티션의 이름이다.

##### REMOTE_USER_NAME

원격 서버의 이중화 대상 테이블 소유자의 사용자 이름으로, 원격 서버의 SYS_USERS_ 메타 테이블의 한 USER_NAME 값과 동일하다.

##### REMOTE_TABLE_NAME

원격 서버의 이중화 대상 테이블의 이름으로, 원격 서버의 SYS_TABLES_ 메타 테이블의 한 TABLE_NAME 값과 동일하다.

##### REMOTE_PARTITION_NAME

원격 서버의 이중화 대상 파티션의 이름이다.

##### IS_PARTITION

테이블이 파티션드 테이블인지를 나타낸다. ‘Y’는 파티션드 테이블이고, ‘N’은 파티션드 테이블이 아니다.

##### INVALID_MAX_SN

이중화 대상 테이블에 DDL구문 또는 동기화 작업이 수행되는 시점에서 가장 최근에 기록된 SN이 저장된다. 해당 SN까지의 테이블 로그를 이중화에서 건너뛴다.

##### REPLICATION_UNIT

이중화 대상 아이템이 무엇인지를 나타낸다. 이 칼럼에는 아래 두 개의 값 중에서 하나가 표시된다.

- T: 이중화 대상 아이템이 테이블임을 나타낸다.
- P: 이중화 대상 아이템이 파티션임을 나타낸다.

#### 참조 테이블

```
SYS_REPLICATIONS_
SYS_USERS_
SYS_TABLES_
```

### SYS_REPL_OFFLINE_DIR_

이중화 오프라인 옵션과 관련된 로그 디렉터리 정보를 가지는 메타 테이블이다.

| Column name      | Type         | Description             |
| ---------------- | ------------ | ----------------------- |
| REPLICATION_NAME | VARCHAR(40)  | 이중화 이름             |
| LFG_ID           | INTEGER      | 로그 파일 그룹의 식별자 |
| PATH             | VARCHAR(512) | 오프라인 로그 경로      |

#### 칼럼 정보

##### REPLICATION_NAME

사용자가 명시한 이중화 이름이다. SYS_REPLICATIONS_ 메타 테이블의 한 REPLICATION_NAME 값과 동일하다.

##### LFG_ID

이는 0의 값을 가진 로그파일 그룹 고유번호이다.

##### PATH

로그 파일이 저장되는 시스템 내의 절대 경로를 나타낸다.

### SYS_REPL_OLD_COLUMNS_

이중화 송신 쓰레드가 현재 복제중인 이중화 대상 칼럼의 정보를 가진 메타 테이블이다.

| Column name          | Type          | Description                                                  |
| -------------------- | ------------- | ------------------------------------------------------------ |
| REPLICATION_NAME     | VARCHAR(40)   | 이중화 이름                                                  |
| TABLE_OID            | BIGINT        | 테이블 객체 식별자                                           |
| COLUMN_NAME          | VARCHAR(128)  | 칼럼 이름                                                    |
| MT_DATATYPE_ID       | INTEGER       | 데이터 타입 식별자                                           |
| MT_LANGUAGE_ID       | INTEGER       | 언어 식별자                                                  |
| MT_FLAG              | INTEGER       | 내부 플래그                                                  |
| MT_PRECISION         | INTEGER       | 정밀도                                                       |
| MT_SCALE             | INTEGER       | 소수 자릿수                                                  |
| MT_ENCRYPT_PRECISION | INTEGER       | 암호화 칼럼 정밀도                                           |
| MT_POLICY_NAME       | VARCHAR(16)   | 암호화 칼럼에 사용된 정책의 이름                             |
| SM_ID                | INTEGER       | 칼럼 식별자                                                  |
| SM_FLAG              | INTEGER       | 내부 플래그                                                  |
| SM_OFFSET            | INTEGER       | 내부 오프셋                                                  |
| SM_VARORDER          | INTEGER       | 한 테이블 내에서 가변(Variable) 방식으로 저장된 칼럼의 저장 순서. 예외적으로 공간 데이타형은 VARORDER가 부여되지 않는다 (기본값 0). |
| SM_SIZE              | INTEGER       | 내부 크기                                                    |
| SM_DIC_TABLE_OID     | BIGINT        | 압축 칼럼의 경우 딕셔너리 테이블의 OID                       |
| SM_COL_SPACE         | INTEGER       | 테이블스페이스 식별자                                        |
| QP_FLAG              | INTEGER       | 내부 플래그                                                  |
| DEFAULT_VAL          | VARCHAR(4000) | 칼럼의 기본 값                                               |
| MT_SRID              | INTEGER       | GEOMETRY 칼럼에 적용된 SRID                                  |

#### 칼럼 정보

##### REPLICATION_NAME

사용자가 명시한 이중화 이름이다. SYS_REPLICATIONS_ 메타 테이블의 한 REPLICATION_NAME 값과 동일하다.

##### TABLE_OID

이중화 송신 쓰레드가 현재 사용중인 이중화 대상 테이블의 식별자이다. SYS_TABLES_ 메타 테이블의 어떤 TABLE_OID 값과도 일치하지 않을 수 있다.

##### COLUMN_NAME

이중화 송신 쓰레드가 현재 복제중인 이중화 대상 칼럼의 이름이다.

##### MT_DATATYPE_ID

데이터 타입 식별자로, 내부 값이다.

##### MT_LANGUAGE_ID

언어 식별자로, 내부 값이다.

##### MT_FLAG

Altibase 서버가 사용하는 내부 플래그이다.

##### MT_PRECISION

숫자 타입의 경우, 칼럼의 정밀도 (숫자 자리수)를 나타낸다. 타입의 경우, 문자형 데이터 타입의 길이를 나타낸다.

##### MT_SCALE

숫자 타입의 경우, 칼럼의 소수점 이하 자릿수를 나타낸다.

##### MT_ENCRYPT_PRECISION

암호화된 칼럼의 정밀도 (크기)를 나타낸다.

##### MT_POLICY_NAME

암호화된 칼럼의 경우, 칼럼에 적용된 보안 정책의 이름을 나타낸다.

##### MT_SRID

GEOMETRY 칼럼의 경우, 칼럼에 적용된 SRID를 나타낸다.

##### SM_ID

칼럼 식별자이다. 0부터 시작한다.

##### SM_FLAG

Altibase 서버가 사용하는 내부 플래그이다.

##### SM_OFFSET

Altibase 서버가 사용하는 내부 오프셋이다.

##### SM_VARORDER

한 테이블 내에서 가변(Variable) 방식으로 저장된 칼럼들 중 해당 칼럼이 저장되는 순서를 나타낸다. 예외적으로 공간 데이타형(GEOMETRY)은 VARORDER가 부여되지 않는다(기본값 0).

##### SM_SIZE

Altibase 서버가 사용하는 내부 크기이다.

##### SM_DIC_TABLE_OID

해당 칼럼이 압축 칼럼일 경우 압축 칼럼의 데이터가 실제로 저장되어 있는 딕셔너리 테이블의 OID를 나타낸다.

##### SM_COL_SPACE

해당 칼럼의 데이터가 저장되는 테이블스페이스의 식별자이다.

##### QP_FLAG

Altibase 서버가 내부적으로 사용하는 플래그이다.

##### DEFAULT_VAL

칼럼의 기본값이 문자열로 저장된다. Altibase 서버가 내부적으로 사용한다.

#### 참조 테이블

```
SYS_REPL_OLD_ITEMS_
SYS_REPL_OLD_INDICES_
SYS_REPL_OLD_INDEX_COLUMNS_
```

### SYS_REPL_OLD_INDEX_COLUMNS_

이중화 송신 쓰레드가 현재 사용 중인 이중화 대상 인덱스 칼럼의 정보를 가진 메타 테이블이다.

| Column name      | Type        | Description              |
| ---------------- | ----------- | ------------------------ |
| REPLICATION_NAME | VARCHAR(40) | 이중화 이름              |
| TABLE_OID        | BIGINT      | 테이블 객체 식별자       |
| INDEX_ID         | INTEGER     | 인덱스 식별자            |
| KEY_COLUMN_ID    | INTEGER     | 칼럼 식별자              |
| KEY_COLUMN_FLAG  | INTEGER     | 내부 플래그              |
| COMPOSITE_ORDER  | INTEGER     | 인덱스에서의 칼럼의 위치 |

#### 칼럼 정보

##### REPLICATION_NAME

사용자가 명시한 이중화 이름으로, SYS_REPLICATIONS_ 메타 테이블의 한 REPLICATION_NAME 값과 동일하다.

##### TABLE_OID

이중화 송신 쓰레드가 현재 복제중인 이중화 대상 테이블의 식별자이다. SYS_TABLES_ 메타 테이블의 어떤 TABLE_OID 값과도 일치하지 않을 수 있다.

##### INDEX_ID

이중화 송신 쓰레드가 현재 복제 중인 이중화 대상 인덱스의 식별자이다.

##### KEY_COLUMN_ID

인덱스를 구성하는 칼럼의 식별자이다.

##### KEY_COLUMN_FLAG

인덱스를 구성하는 칼럼의 내부 플래그이다.

##### COMPOSITE_ORDER

인덱스를 구성하는 칼럼의 순서이다.

#### 참조 테이블

```
SYS_REPL_OLD_ITEMS_
SYS_REPL_OLD_COLUMNS_
SYS_REPL_OLD_INDICES_
```

### SYS_REPL_OLD_INDICES_

이중화 송신 쓰레드가 현재 복제 중인 이중화 대상 인덱스의 정보를 가진 메타 테이블이다.

| Column name      | Type         | Description               |
| ---------------- | ------------ | ------------------------- |
| REPLICATION_NAME | VARCHAR(40)  | 이중화 이름               |
| TABLE_OID        | BIGINT       | 테이블 객체 식별자        |
| INDEX_ID         | INTEGER      | 인덱스 식별자             |
| INDEX_NAME       | VARCHAR(128) | 인덱스 이름               |
| TYPE_ID          | INTEGER      | 인덱스 타입 식별자        |
| IS_UNIQUE        | CHAR(1)      | 글로벌 유니크 인덱스 여부 |
| IS_LOCAL_UNIQUE  | CHAR(1)      | 로컬 유니크 인덱스 여부   |
| IS_RANGE         | CHAR(1)      | 범위 검색 가능 여부       |

#### 칼럼 정보

##### REPLICATION_NAME

사용자가 명시한 이중화 이름으로, SYS_REPLICATIONS_ 메타 테이블의 한 REPLICATION_NAME과 동일하다.

##### TABLE_OID

이중화 송신 쓰레드가 현재 복제 중인 이중화 대상 테이블의 식별자이다. SYS_TABLES_ 메타 테이블의 어떤 TABLE_OID 값과도 일치하지 않을 수 있다.

##### INDEX_ID

이중화 송신 쓰레드가 현재 복제중인 이중화 대상 인덱스의 식별자이다.

##### INDEX_NAME

이중화 송신 쓰레드가 현재 복제 중인 이중화 대상 인덱스의 이름이다.

##### TYPE_ID

인덱스 유형 식별자로, 내부 값이다.

##### IS_UNIQUE

글로벌 유니크 인덱스인지 여부를 나타낸다. 'Y'는 글로벌 유니크를 나타내고, 'N'은 글로벌 유니크가 아님을 나타낸다.

##### IS_LOCAL_UNIQUE

로컬 유니크 인덱스인지 여부를 나타낸다. 'Y'는 로컬 유니크를 나타내고, 'N'은 로컬 유니크가 아님을 나타낸다.

##### IS_RANGE

범위 검색 가능 여부를 나타낸다. 'Y'는 범위 검색이 가능한 인덱스이고, 'N'은 범위 검색이 불가능한 인덱스임을 나타낸다.

#### 참조 테이블

```
SYS_REPL_OLD_ITEMS_
SYS_REPL_OLD_COLUMNS_
SYS_REPL_OLD_INDEX_COLUMNS_
```

### SYS_REPL_OLD_ITEMS_

이중화 송신 쓰레드가 현재 복제중인 이중화 대상 테이블의 정보를 가진 메타 테이블이다.

| Column name           | Type          | Description                                    |
| --------------------- | ------------- | ---------------------------------------------- |
| REPLICATION_NAME      | VARCHAR(40)   | 이중화 이름                                    |
| TABLE_OID             | BIGINT        | 테이블 객체 식별자                             |
| USER_NAME             | VARCHAR(128)  | 사용자 이름                                    |
| TABLE_NAME            | VARCHAR(128)  | 테이블 이름                                    |
| PARTITION_NAME        | VARCHAR(128)  | 파티션 이름                                    |
| PRIMARY_KEY_INDEX_ID  | INTEGER       | 프라이머리 키의 인덱스 식별자                  |
| REMOTE_USER_NAME      | VARCHAR(128)  | 원격 서버의 대상 테이블 소유자 이름            |
| REMOTE_TABLE_NAME     | VARCHAR(128)  | 원격 서버의 대상 테이블 이름                   |
| REMOTE_PARTITION_NAME | VARCHAR(128)  | 원격 서버의 파티션 이름                        |
| PARTITION_ORDER       | INTEGER       | 파티션 순서(해쉬 파티션일 경우 필요)           |
| PARTITION_MIN_VALUE   | VARCHAR(4000) | 파티션의 최소 기준값 (해쉬 파티션의 경우 NULL) |
| PARTITION_MAX_VALUE   | VARCHAR(4000) | 파티션의 최대 기준값 (해쉬 파티션의 경우 NULL) |
| INVALID_MAX_SN        | BIGINT        | 건너 뛸 로그의 최대 SN                         |

#### 칼럼 정보

##### REPLICATION_NAME

사용자가 명시한 이중화 이름으로, SYS_REPLICATIONS_ 메타 테이블의 한 REPLICATION_NAME 값과 동일하다.

##### TABLE_OID

이중화 송신 쓰레드가 현재 복제중인 이중화 대상 테이블의 식별자이다. SYS_TABLES_ 메타 테이블의 어떤 TABLE_OID 값과도 일치하지 않을 수 있다.

##### USER_NAME

지역 서버의 이중화 대상 테이블인 소유자의 이름이다. SYS_USERS_ 메타 테이블의 USER_NAME 값과 동일하다.

##### TABLE_NAME

지역 서버의 이중화 대상 테이블의 이름이다. SYS_TABLES_ 메타 테이블의 한 TABLE_NAME 값과 동일하다.

##### PARTITION_NAME

지역 서버의 이중화 대상 테이블이 속해 있는 파티션의 이름이다.

##### PRIMARY_KEY_INDEX_ID

프라이머리 키 (Primary Key)의 인덱스 식별자이다.

##### REMOTE_USER_NAME

원격 서버의 이중화 대상 테이블인 소유자의 이름이다.

##### REMOTE_TABLE_NAME

원격 서버의 이중화 대상 테이블의 이름이다.

##### REMOTE_PARTITION_NAME

원격 서버의 이중화 대상 테이블이 속해 있는 파티션의 이름이다.

##### PARTITION_ORDER

파티션들 중에서 이 파티션의 순서를 나타낸다. 해쉬 (HASH) 파티션인 경우에 필요하다.

##### PARTITION_MIN_VALUE

파티션의 최소 기준값을 문자열로 보여준다. 해쉬 (HASH) 파티션인 경우에는 널(NULL)이다.

##### PARTITION_MAX_VALUE

파티션의 최대 기준값을 문자열로 보여준다. 해쉬 (HASH) 파티션인 경우에는 널(NULL)이다.

##### INVALID_MAX_SN

이중화 대상 테이블에 DDL구문 또는 동기화 작업이 수행되는 시점에서 가장 최근에 기록된 SN이 저장된다. 해당 SN까지의 테이블 로그를 이중화에서 건너뛴다.

#### 참조 테이블

```
SYS_REPL_OLD_COLUMNS_
SYS_REPL_OLD_INDICES_
SYS_REPL_OLD_INDEX_COLUMNS_
```

### SYS_REPL_TABLE_OID_IN_USE_

이중화가 아직 처리하지 않은 DDL 로그에 포함된 테이블의 테이블 객체 식별자(TABLE OID) 정보를 관리하는 메타 테이블이다.

| Column name      | Type         | Description                    |
| ---------------- | ------------ | ------------------------------ |
| REPLICATION_NAME | VARCHAR(40)  | 이중화 이름                    |
| OLD_TABLE_OID    | BIGINTBIGINT | DDL 수행 전 테이블 객체 식별자 |
| TABLE_OID        | BIGINTBIGINT | 현재 테이블 객체 식별자        |

#### 칼럼 정보

##### REPLICATION_NAME

사용자가 명시한 이중화 이름으로, SYS_REPLICATIONS_ 메타 테이블의 한 REPLICATION_NAME 값과 동일하다.

##### OLD_TABLE_OID

이중화가 아직 처리하지 않은 DDL 로그에 포함된 테이블의 이전 테이블 객체 식별자이다.

##### TABLE_OID

이중화가 아직 처리하지 않은 DDL 로그에 포함된 테이블의 현재 테이블 객체 식별자이다. 이 값은 SYS_REPL_ITEMS_ 메타 테이블의 한 TABLE_OID 값과 동일하다.

### SYS_REPL_RECOVERY_INFOS_

원격 서버의 복구에 사용하기 위해 로그 정보를 기록하는 메타 테이블이다.

| Column name          | Type        | Description                    |
| -------------------- | ----------- | ------------------------------ |
| REPLICATION_NAME     | VARCHAR(40) | 이중화 이름                    |
| MASTER_BEGIN_SN      | BIGINT      | 주 트랜잭션의 시작 로그 번호   |
| MASTER_COMMIT_SN     | BIGINT      | 주 트랜잭션의 완료 로그 번호   |
| REPLICATED_BEGIN_SN  | BIGINT      | 복제 트랜잭션의 시작 로그 번호 |
| REPLICATED_COMMIT_SN | BIGINT      | 복제 트랜잭션의 완료 로그 번호 |

#### 칼럼 정보

##### REPLICATION_NAME

사용자가 명시한 이중화 이름으로, SYS_REPLICATIONS_ 메타 테이블의 한 REPLICATION_NAME 값과 동일하다.

##### MASTER_BEGIN_SN

원격 서버에서 발생한 주 트랜잭션의 시작 로그 번호이다.

##### MASTER_COMMIT_SN

원격 서버에서 발생한 주 트랜잭션의 완료 로그 번호이다.

##### REPLICATED_BEGIN_SN

지역 서버에서 발생한 복제 트랜잭션의 시작 로그 번호이다.

##### REPLICATED_COMMIT_SN

지역 서버에서 발생한 복제 트랜잭션의 완료 로그 번호이다.

#### 참조 테이블

```
SYS_REPLICATIONS_
```

### SYS_SECURITY_

보안 모듈의 상태 정보를 관리한다.

| Column name     | Type        | Description               |
| --------------- | ----------- | ------------------------- |
| MODULE_NAME     | VARCHAR(24) | 보안 모듈의 이름          |
| MODULE_VERSION  | VARCHAR(40) | 보안 모듈의 버전          |
| ECC_POLICY_NAME | VARCHAR(16) | ECC 정책의 이름           |
| ECC_POLICY_CODE | VARCHAR(64) | ECC 정책에 대한 검증 코드 |

이 테이블은 써드 파티에서 제공한 보안 모듈의 연동 여부를 보여준다.

써드 파티에서 제공한 보안 모듈이 정상적으로 연동되어 있는 경우, SYS_SECURITY_ 메타 테이블은 보안 모듈 프로퍼티들에 대한 정보를 저장한다. 반면, 보안 모듈이 연동되어 있지 않은 경우에는 SYS_SECURITY_ 메타 테이블에는 어떤 레코드도 존재하지 않는다.

### SYS_SYNONYMS_

데이터베이스 객체에 대한 별칭 기능을 하는 시노님에 대한 정보를 기록하는 테이블이다.

| Column name       | Type         | Description                                          |
| ----------------- | ------------ | ---------------------------------------------------- |
| SYNONYM_OWNER_ID  | INTEGER      | 사용자 식별자                                        |
| SYNONYM_NAME      | VARCHAR(128) | 시노님 이름                                          |
| OBJECT_OWNER_NAME | VARCHAR(128) | 객체 소유자 이름                                     |
| OBJECT_NAME       | VARCHAR(128) | 시노님 대상 객체 이름                                |
| CREATED           | DATE         | 시노님이 생성된 시간                                 |
| LAST_DDL_TIME     | DATE         | 시노님에 대해 마지막으로 DDL 변경 작업이 일어난 시간 |

#### 칼럼 정보

##### SYNONYM_OWNER_ID

시노님 소유자의 사용자 식별자로, SYS_USERS_ 메타 테이블의 한 USER_ID 값과 동일하다.

##### SYNONYM_NAME

사용자가 명시한 시노님 이름이다.

##### OBJECT_OWNER_NAME

시노님 대상 객체가 소속된 스키마 소유자의 이름이다.

##### OBJECT_NAME

사용자가 명시한 시노님 대상 객체의 이름이다.

##### CREATED

시노님이 생성된 시간을 나타낸다.

##### LAST_DDL_TIME

시노님에 대해 DDL 변경 작업이 마지막으로 일어난 시간을 나타낸다.

#### 참조 테이블

```
SYS_USERS_
```

### SYS_TABLES_

메타 테이블들과 사용자가 정의한 테이블, 시퀀스 그리고 뷰에 대한 정보를 기록하는 테이블이다.

| Column name                | Type         | Description                                                  |
| -------------------------- | ------------ | ------------------------------------------------------------ |
| USER_ID                    | INTEGER      | 사용자 식별자                                                |
| TABLE_ID                   | INTEGER      | 테이블 식별자                                                |
| TABLE_OID                  | BIGINT       | 테이블 객체 식별자                                           |
| COLUMN_COUNT               | INTEGER      | 테이블 칼럼의 개수                                           |
| TABLE_NAME                 | VARCHAR(128) | 테이블 이름                                                  |
| TABLE_TYPE                 | CHAR(1)      | 객체 타입                                                    |
| REPLICATION_COUNT          | INTEGER      | 테이블과 관련된 이중화 개수                                  |
| REPLICATION_RECOVERY_COUNT | INTEGER      | 테이블과 관련된 복구 옵션을 사용하는 이중화 개수             |
| MAXROW                     | BIGINT       | 입력할 수 있는 최대 레코드 개수(0: 제한 없음)                |
| TBS_ID                     | INTEGER      | 테이블스페이스 식별자                                        |
| TBS_NAME                   | VARCHAR(128) | 테이블이 저장된 테이블스페이스 이름                          |
| PCTFREE                    | INTEGER      | 아래 설명 참조                                               |
| PCTUSED                    | INTEGER      | 아래 설명 참조                                               |
| INIT_TRANS                 | INTEGER      | 한 페이지에서 동시에 갱신 가능한 트랜잭션의 초기 개수        |
| MAX_TRANS                  | INTEGER      | 한 페이지에서 동시에 갱신 가능한 트랜잭션의 최대 개수        |
| INITEXTENTS                | BIGINT       | 테이블 생성시 초기 익스텐트 개수                             |
| NEXTEXTENTS                | BIGINT       | 테이블 확장시 추가될 익스텐트 개수                           |
| MINEXTENTS                 | BIGINT       | 테이블의 최소 익스텐트 개수                                  |
| MAXEXTENTS                 | BIGINT       | 테이블의 최대 익스텐트 개수                                  |
| IS_PARTITIONED             | CHAR(1)      | 파티션드 테이블 여부                                         |
| TEMPORARY                  | CHAR(1)      | 임시 테이블 여부 D: 트랜잭션에 한정되는 임시 테이블 P: 세션에 한정되는 임시 테이블 N: 임시 테이블이 아님 |
| HIDDEN                     | CHAR(1)      | 숨김 속성을 갖는 테이블인지 여부                             |
| ACCESS                     | CHAR(1)      | 테이블 접근 모드                                             |
| PARALLEL_DEGREE            | INTEGER      | 병렬 질의를 처리하는 쓰레드의 개수                           |
| CREATED                    | DATE         | 테이블이 생성된 시간                                         |
| LAST_DDL_TIME              | DATE         | 테이블에 대해 마지막으로 DDL 변경 작업이 일어난 시간         |

#### 칼럼 정보

##### USER_ID

테이블 소유자의 사용자 식별자로, SYS_USERS_ 메타 테이블의 한 USER_ID 값과 동일하다.

##### TABLE_ID

테이블 식별자로, 시스템 시퀀스에 의해 자동으로 부여된다.

##### TABLE_OID

시스템 내부에서 자동으로 부여되는 테이블 객체 식별자이다. 사용자가 메타 테이블 조회 시 사용하는 TABLE_ID와는 달리 시스템 내부 동작 시에만 사용된다.

##### COLUMN_COUNT

테이블에 정의된 칼럼의 개수이다.

##### TABLE_NAME

사용자가 명시한 테이블 이름이다.

##### TABLE_TYPE

SYS_TABLES_ 메타 테이블에는 테이블 외에 시퀀스, 뷰 정보 등도 함께 저장된다. 타입 식별자는 이들 객체를 구별하며, 아래의 타입 식별자로 표시된다.

- T: 테이블
- S: 시퀀스
- V: 뷰
- W: 큐(Queue) 전용 시퀀스
- Q: 큐
- M: Materialized view의 데이터 유지를 위해 자동으로 생성되는 테이블
- A: Materialized view의 데이터 유지를 위해 자동으로 생성되는 뷰
- G: 글로벌 인덱스를 위해 내부적으로 사용되는 테이블
- D: 압축 칼럼의 데이터를 실제로 저장하기 위해 내부적으로 사용되는 딕셔너리 테이블
- R: 삭제(Drop)되어 휴지통에서 관리되고 있는 테이블

##### REPLICATION_COUNT

해당 테이블과 관련된 이중화 객체의 개수이다.

##### REPLICATION_RECOVERY_COUNT

해당 테이블에 대해 복구 옵션을 사용하는 이중화 객체의 개수이다.

##### MAXROW

테이블에 삽입가능한 최대 레코드 수이다.

##### TBS_ID

테이블이 저장되는 테이블스페이스의 식별자이다.

##### PCTFREE

한 페이지가 갱신 가능하기 위해 유지해야 하는 여유 공간의 최소 비율이다. 기존에 페이지에 저장된 행들을 갱신하기 위해 PCTFREE에서 명시한 비율만큼의 여유 공간을 페이지에서 유지하고 있다. 예를 들어 PCTFREE 값이 20이면, 한 페이지의 20%의 공간은 갱신 연산을 위해 남겨두고, 80%의 공간에 대해서만 데이터 삽입이 가능하다.

PCTFREE는 CREATE TABLE문 정의시 0에서 99사이의 값으로 사용자가 명시할 수 있다.

##### PCTUSED

한 페이지가 갱신만 가능한 상태에서 다시 삽입이 가능한 상태로 가기 위한 페이지 사용 공간의 최소 비율을 의미한다. 페이지의 여유 공간이 PCTFREE에 명시한 비율에 도달하면 더 이상 삽입 연산은 안되며, 갱신만 가능해진다. 이후 갱신과 삭제 등으로 페이지 사용 공간의 비율이 PCTUSED에서 정한 값보다 낮아지면 새로운 행을 삽입할 수 있게 된다.

CREATE TABLE문 정의시 0에서 99사이의 값으로 사용자가 명시할 수 있다.

> \* PCTFREE와 PCTUSED에 대한 자세한 설명은 *SQL Reference*의 CREATE TABLE문 설명을 참조한다.

##### INIT_TRANS

한 페이지에 동시에 갱신 연산을 수행할 수 있는 트랜잭션의 개수로, 페이지를 생성할 때 설정된다. 실제 트랜잭션의 개수는 페이지 내의 가용 공간이 허용하는 한 MAX_TRANS에 설정된 개수까지 증가할 수 있다.

##### MAX_TRANS

한 페이지에서 동시에 갱신 연산을 수행할 수 있는 트랜잭션의 최대 개수이다.

##### INITEXTENTS

테이블을 생성할 때 할당하는 가용 익스텐트 개수를 나타낸다.

##### NEXTEXTENTS

테이블의 공간을 확장할 때 할당할 수 있는 추가 익스텐트 개수를 나타낸다.

##### MINEXTENTS

테이블의 최소 가용 익스텐트 개수를 나타낸다.

##### MAXEXTENTS

테이블의 최대 가용 익스텐트 개수를 나타낸다.

##### IS_PARTITIONED

테이블이 파티션드 테이블인지 여부를 나타내는 식별자이다. ‘Y’는 파티션드 테이블이고, ‘N’은 파티션드 테이블이 아니다.

##### TEMPORARY

해당 테이블이 임시 테이블인지 여부를 나타낸다.

- D: 트랜잭션에 한정되는 임시 테이블임
- P: 세션에 한정되는 임시 테이블임
- N: 임시 테이블이 아님

##### HIDDEN

해당 테이블이 숨기는 테이블인지 여부를 나타낸다.

- Y: 사용자에게 숨기는 테이블임
- N: 사용자에게 공개된 테이블임 (일반 테이블)

##### PARALLEL_DEGREE

파티션드 테이블을 스캔할 때 병렬 질의를 처리하는 쓰레드의 개수를 나타낸다.

##### ACCESS

테이블의 데이터에 대한 접근 모드를 나타낸다. 기본 모드는 읽기/쓰기가 가능한 W이다.

- R: 데이터 읽기 전용 모드
- W: 데이터 읽기/쓰기 모드 (기본 모드)
- A: 데이터 읽기/추가 모드. 이 모드에서는 데이터 변경/삭제가 허용되지 않는다.

#### 참조 테이블

```
SYS_USERS_
```

### SYS_TABLE_PARTITIONS_

테이블의 파티션을 관리하는 메타 테이블이다.

| Column name                | Type          | Description                                         |
| -------------------------- | ------------- | --------------------------------------------------- |
| USER_ID                    | INTEGER       | 사용자 식별자                                       |
| TABLE_ID                   | INTEGER       | 테이블 식별자                                       |
| PARTITION_OID              | BIGINT        | 파티션 객체 식별자                                  |
| PARTITION_ID               | INTEGER       | 파티션 식별자                                       |
| PARTITION_NAME             | VARCHAR(128)  | 파티션 이름                                         |
| PARTITION_MIN_VALUE        | VARCHAR(4000) | 파티션의 최소 기준값 (해쉬 파티션의 경우 NULL)      |
| PARTITION_MAX_VALUE        | VARCHAR(4000) | 파티션의 최대 기준값 (해쉬 파티션의 경우 NULL)      |
| PARTITION_ORDER            | INTEGER       | 파티션 순서 (해쉬 파티션일 경우 필요)               |
| TBS_ID                     | INTEGER       | 테이블스페이스 식별자                               |
| PARTITION_ACCESS           | CHAR(1)       | 파티션 접근 모드                                    |
| REPLICATION_COUNT          | INTEGER       | 파티션에 관련된 이중화 객체의 개수                  |
| REPLICATION_RECOVERY_COUNT | INTEGER       | 파티션에 대해 복구 옵션을 설정한 이중화 객체의 개수 |
| CREATED                    | DATE          | 파티션이 생성된 시간                                |
| LAST_DDL_TIME              | DATE          | 파티션을 마지막으로 DDL 변경 작업한 시간            |

#### 칼럼 정보

##### USER_ID

테이블 소유자의 사용자 식별자로, SYS_USERS_ 메타 테이블의 한 USER_ID 값과 동일하다.

##### TABLE_ID

테이블 식별자로, 시스템 시퀀스에 의해 자동으로 부여된다.

##### PARTITION_OID

시스템 내부에서 자동으로 부여되는 파티션 객체 식별자이다. 메타 테이블 조회 시 사용하는 PARTITION_ID와 달리 시스템 내부 동작 시에만 사용된다.

##### PARTITION_ID

파티션 식별자이다.

##### PARTITION_NAME

사용자가 명시한 파티션 이름이다.

##### PARTITION_MIN_VALUE

파티션의 최소 기준값을 문자열로 보여준다. 해쉬 (HASH) 파티션인 경우에는 널(NULL)이다.

##### PARTITION_MAX_VALUE

파티션의 최대 기준값을 문자열로 보여준다. 해쉬 (HASH) 파티션인 경우에는 널(NULL)이다.

##### PARTITION_ORDER

파티션들 중에서 이 파티션의 순서를 나타낸다. 해쉬 (HASH) 파티션인 경우에 필요하다.

##### TBS_ID

테이블이 저장되는 테이블스페이스의 식별자이다.

##### PARTITION_ACCESS

파티션의 데이터에 대한 접근 모드를 나타낸다. 기본 모드는 읽기/쓰기가 가능한 W이다.

- R: 데이터 읽기 전용 모드
- W: 데이터 읽기/쓰기 모드(기본 모드)
- A: 데이터 읽기/추가 모드. 이 모드에서는 데이터 변경/삭제가 허용되지 않는다.

##### REPLICATION_COUNT

이 파티션에 관련된 이중화 객체의 개수를 나타낸다.

##### REPLICATION_RECOVERY_COUNT

이 파티션에 대해 복구 옵션을 설정한 이중화 객체의 개수를 나타낸다.

#### 참조 테이블

```
SYS_USERS_
SYS_TABLES_
SYS_PART_TABLES_
```

### SYS_TABLE_SIZE_

시스템에 있는 디스크 테이블과 메모리 테이블의 실제 크기 정보를 저장하는 메타 테이블이다.

| Column name | Type         | Description                         |
| ----------- | ------------ | ----------------------------------- |
| USER_NAME   | VARCHAR(128) | 테이블 소유자                       |
| TABLE_NAME  | VARCHAR(128) | 테이블 이름                         |
| TBS_NAME    | VARCHAR(128) | 테이블이 저장된 테이블스페이스 이름 |
| MEMORY_SIZE | BIGINT       | 메모리 테이블의 크기                |
| DISK_SIZE   | BIGINT       | 디스크 테이블의 크기                |

### SYS_TBS_USERS_

사용자와 사용자 정의 테이블스페이스간의 관계에 대한 정보가 저장된 테이블이다.

| Column name | Type    | Description                   |
| ----------- | ------- | ----------------------------- |
| TBS_ID      | INTEGER | 테이블스페이스 식별자         |
| USER_ID     | INTEGER | 사용자 식별자                 |
| IS_ACCESS   | INTEGER | 테이블스페이스 접근 허용 여부 |

#### 칼럼 정보

##### TBS_ID

테이블스페이스 식별자이다.

##### USER_ID

사용자 식별자로, SYS_USERS_ 메타 테이블의 한 USER_ID 값과 동일하다.

##### IS_ACCESS

사용자가 해당 테이블스페이스에 접근 가능한지를 나타낸다.

- 0: 접근불가
- 1: 접근가능

#### 참조 테이블

```
SYS_USERS_
```

### SYS_TRIGGERS_

트리거의 기본 정보를 저장하는 메타 테이블이다.

| Column name       | Type         | Description                                          |
| ----------------- | ------------ | ---------------------------------------------------- |
| USER_ID           | INTEGER      | 사용자 식별자                                        |
| USER_NAME         | VARCHAR(128) | 사용자 이름                                          |
| TRIGGER_OID       | BIGINT       | 트리거 식별자                                        |
| TRIGGER_NAME      | VARCHAR(128) | 트리거 이름                                          |
| TABLE_ID          | INTEGER      | 테이블 식별자                                        |
| IS_ENABLE         | INTEGER      | 트리거 수행 여부                                     |
| EVENT_TIME        | INTEGER      | 트리거 수행 시점                                     |
| EVENT_TYPE        | INTEGER      | 트리거 이벤트 타입                                   |
| UPDATE_COLUMN_CNT | INTEGER      | UPDATE 시 트리거를 발생시키는 칼럼 개수              |
| GRANULARITY       | INTEGER      | 트리거 수행 단위 구분                                |
| REF_ROW_CNT       | INTEGER      | REFERENCING 구문의 ALIAS 개수                        |
| SUBSTRING_CNT     | INTEGER      | 트리거 구문을 저장하고 있는 레코드 수                |
| STRING_LENGTH     | INTEGER      | 트리거 구문의 전체 문자열 길이                       |
| CREATED           | DATE         | 트리거가 생성된 시간                                 |
| LAST_DDL_TIME     | DATE         | 트리거에 대해 마지막으로 DDL 변경 작업이 일어난 시간 |

#### 칼럼 정보

##### USER_ID

사용자 식별자로, SYS_USERS_ 메타 테이블의 한 USER_ID 값과 동일하다.

##### USER_NAME

사용자 이름으로, SYS_USERS_ 메타 테이블의 한 USER_NAME 값과 동일하다.

##### TRIGGER_OID

트리거 식별자로, 시스템에 의해 자동으로 부여된다.

##### TRIGGER_NAME

사용자가 명시한 트리거 이름이다.

##### TABLE_ID

트리거가 정의된 테이블의 식별자로, SYS_TABLES_ 메타 테이블의 한 TABLE_ID 값과 동일하다.

##### IS_ENABLE

트리거를 발생시킬지 여부를 나타내는 값으로, ALTER TRIGGER문을 사용해서 변경할 수 있다.

- 0: 발생시키지 않음
- 1: 발생시킴

##### EVENT_TIME

트리거를 발생시킬 시점을 나타낸다.

- 1: BEFORE
- 2: AFTER
- 3: INSTEAD OF

##### EVENT_TYPE

트리거를 발생시키는 이벤트의 타입을 나타낸다.

- 1: INSERT
- 2: DELETE
- 4: UPDATE

##### UPDATE_COLUMN_CNT

갱신 시 트리거를 발생시키는 칼럼 수를 나타낸다. 이 값은 SYS_TRIGGER_UPDATE_COLUMNS_ 메타 테이블의 해당 트리거와 관련된 레코드의 개수와 동일하다.

##### GRANULARITY

트리거를 발생시키는 단위를 나타낸다.

- 1: FOR EACH ROW
- 2: FOR EACH STATEMENT

##### REF_ROW_CNT

REFERENCING 구문에 정의된 ALIAS의 개수이다.

##### SUBSTRING_CNT

한 트리거 구문은 나뉘어져서 SYS_TRIGGER_STRINGS_ 메타 테이블에 여러 레코드로 저장된다. 이 값은 그 구문을 저장하는 레코드의 수를 나타낸다.

##### STRING_LENGTH

트리거 구문의 전체 문자열 길이이다.

#### 참조 테이블

```
SYS_USERS_
SYS_TABLES_
```

### SYS_TRIGGER_DML_TABLES_

트리거가 참조하고 접근하는 테이블의 정보를 저장하는 메타 테이블이다.

| Column name  | Type    | Description               |
| ------------ | ------- | ------------------------- |
| TABLE_ID     | INTEGER | 테이블 식별자             |
| TRIGGER_OID  | BIGINT  | 트리거 식별자             |
| DML_TABLE_ID | INTEGER | 트리거 내의 테이블 식별자 |
| STMT_TYPE    | INTEGER | 실행 구문 종류            |

#### 칼럼 정보

##### TABLE_ID

트리거의 기반 테이블의 식별자로, SYS_TABLES_ 메타 테이블의 한 TABLE_ID 값과 동일하다.

##### TRIGGER_OID

트리거 식별자로, SYS_TRIGGERS_ 메타 테이블의 한 TRIGGER_OID 값과 동일하다.

##### DML_TABLE_ID

트리거 내에서 DML문으로 접근하는 테이블의 식별자로, SYS_TABLES_ 메타 테이블의 한 TABLE_ID 값과 동일하다.

##### STMT_TYPE

테이블에 수행하는 DML 구문의 종류를 나타낸다.

- 8: DELETE
- 19: INSERT
- 33: UPDATE

#### 참조 테이블

```
SYS_TABLES_
SYS_TRIGGERS_
```

### SYS_TRIGGER_STRINGS_

트리거 구문을 저장하는 메타 테이블이다.

| Column name | Type         | Description                                        |
| ----------- | ------------ | -------------------------------------------------- |
| TABLE_ID    | INTEGER      | 테이블 식별자                                      |
| TRIGGER_OID | BIGINT       | 트리거 식별자                                      |
| SEQNO       | INTEGER      | 나뉘어 저장된 구문 조각의 트리거 구문내에서의 위치 |
| SUBSTRING   | VARCHAR(100) | 나뉘어진 트리거 구문                               |

#### 칼럼 정보

##### TABLE_ID

테이블 식별자로, SYS_TABLES_ 메타 테이블의 한 TABLE_ID 값과 동일하다.

##### TRIGGER_OID

트리거 식별자로, SYS_TRIGGERS_ 메타 테이블의 한 TRIGGER_OID 값과 동일하다.

##### SEQNO

한 트리거의 전체 구문을 여러 레코드로 SYS_TRIGGER_STRINGS_에 저장할 때, 이들 레코드 중에서 이 레코드의 위치를 나타낸다.

##### SUBSTRING

트리거 구문의 문자열 조각이다. 한 TRIGGER_OID 값으로 레코드들을 검색하여 SEQNO 순서대로 SUBSTRING 값을 합치면 트리거 전체 구문을 생성할 수 있다.

#### 참조 테이블

```
SYS_TABLES_
SYS_TRIGGERS_
```

### SYS_TRIGGER_UPDATE_COLUMNS_

갱신시 트리거를 발생시키는 칼럼 정보를 저장하는 메타 테이블이다.

| Column name | Type    | Description   |
| ----------- | ------- | ------------- |
| TABLE_ID    | INTEGER | 테이블 식별자 |
| TRIGGER_OID | BIGINT  | 트리거 식별자 |
| COLUMN_ID   | INTEGER | 칼럼 식별자   |

#### 칼럼 정보

##### TABLE_ID

테이블 식별자로, SYS_TABLES_ 메타 테이블의 한 TABLE_ID 값과 동일하다.

##### TRIGGER_OID

트리거 식별자로, SYS_TRIGGERS_ 메타 테이블의 한 TRIGGER_OID 값과 동일하다.

##### COLUMN_ID

칼럼 식별자로, SYS_COLUMNS_ 메타 테이블의 한 COLUMN_ID 값과 동일하다.

#### 참조 테이블

```
SYS_TABLES_
SYS_TRIGGERS_
```

### SYS_USERS_

데이터베이스 사용자에 대한 정보를 기록하는 테이블이다.

| Column name              | Type         | Description                                                  |
| ------------------------ | ------------ | ------------------------------------------------------------ |
| USER_ID                  | INTEGER      | 사용자 식별자                                                |
| USER_NAME                | VARCHAR(128) | 사용자 이름                                                  |
| PASSWORD                 | VARCHAR(256) | 사용자 패스워드                                              |
| DEFAULT_TBS_ID           | INTEGER      | 기본 테이블스페이스 식별자                                   |
| TEMP_TBS_ID              | INTEGER      | 임시 테이블스페이스 식별자                                   |
| ACCOUNT_LOCK             | CHAR(1)      | 계정의 잠김 여부 표시 N: UNLOCKED L: LOCKED                  |
| ACCOUNT_LOCK_DATE        | DATE         | 계정이 잠기게 된 날짜                                        |
| PASSWORD_LIMIT_FLAG      | CHAR(1)      | 패스워드 관리 정책의 사용 여부 표시 T: 패스워드 관리 정책 사용 F: 패스워드 관리 정책 미사용 |
| FAILED_LOGIN_ATTEMPTS    | INTEGER      | 로그인 실패 허용 최대 횟수                                   |
| FAILED_LOGIN_COUNT       | INTEGER      | 로그인 실패 횟수                                             |
| PASSWORD_LOCK_TIME       | INTEGER      | 계정이 한 번 잠긴 후 다시 풀리기 위해 경과되어야 하는 기간   |
| PASSWORD_EXPIRY_DATE     | DATE         | 패스워드 만료일                                              |
| PASSWORD_LIFE_TIME       | INTEGER      | 패스워드 유효기간                                            |
| PASSWORD_GRACE_TIME      | INTEGER      | 패스워드 만료 후 유예기간                                    |
| PASSWORD_REUSE_DATE      | DATE         | 동일한 패스워드가 재사용 가능해지는 날짜                     |
| PASSWORD_REUSE_TIME      | INTEGER      | 미사용                                                       |
| PASSWORD_REUSE_MAX       | INTEGER      | 동일한 패스워드의 재사용 가능 횟수                           |
| PASSWORD_REUSE_COUNT     | INTEGER      | 미사용                                                       |
| PASSWORD_VERIFY_FUNCTION | VARCHAR(128) | 패스워드를 검증할 콜백 함수(Callback Function)               |
| USER_TYPE                | CHAR(1)      | 사용자 타입 표시 U: 사용자(User) R: 롤(Role)                 |
| DISABLE_TCP              | CHAR(1)      | 사용중인 TCP 접속의 제한 여부 표시 T : TCP 접속을 못하고, SSL이나 IPC로만 통신 F : TCP 접속 허용 |
| CREATED                  | DATE         | 데이터베이스 사용자가 생성된 시간                            |
| LAST_DDL_TIME            | DATE         | 사용자에 대해 마지막으로 DDL 변경 작업이 일어난 시간         |

#### 칼럼 정보

##### USER_ID

사용자 식별자로, 시스템의 시퀀스에 의해 자동으로 부여된다.

##### USER_NAME

사용자가 명시한 사용자의 이름이다.

##### PASSWORD

사용자의 패스워드로 암호화 되어 있다.

##### DEFAULT_TBS_ID

기본 테이블스페이스 식별자로, 사용자가 객체 생성 시 테이블스페이스를 명시적으로 기술하지 않을 경우 사용된다.

##### TEMP_TBS_ID

사용자의 임시 테이블스페이스 식별자이다.

##### DISABLE_TCP

사용자의 TCP 접속을 허용하거나 제한하는 것을 나타낸다.

#### 참조 테이블

```
DBA_USERS_
```

### DBA_USERS_

데이터베이스 사용자에 대한 정보를 기록하는 테이블이다. SYS 사용자만이 조회할 수 있다.

| Column name              | Type         | Description                                                  |
| ------------------------ | ------------ | ------------------------------------------------------------ |
| USER_ID                  | INTEGER      | 사용자 식별자                                                |
| USER_NAME                | VARCHAR(128) | 사용자 이름                                                  |
| PASSWORD                 | VARCHAR(256) | 사용자 패스워드                                              |
| DEFAULT_TBS_ID           | INTEGER      | 기본 테이블스페이스 식별자                                   |
| TEMP_TBS_ID              | INTEGER      | 임시 테이블스페이스 식별자                                   |
| ACCOUNT_LOCK             | CHAR(1)      | 계정의 잠김 여부 표시 N: UNLOCKED L: LOCKED                  |
| ACCOUNT_LOCK_DATE        | DATE         | 계정이 잠기게 된 날짜                                        |
| PASSWORD_LIMIT_FLAG      | CHAR(1)      | 패스워드 관리 정책의 사용 여부 표시 T: 패스워드 관리 정책 사용 F: 패스워드 관리 정책 미사용 |
| FAILED_LOGIN_ATTEMPTS    | INTEGER      | 로그인 실패 허용 최대 횟수                                   |
| FAILED_LOGIN_COUNT       | INTEGER      | 로그인 실패 횟수                                             |
| PASSWORD_LOCK_TIME       | INTEGER      | 계정이 한 번 잠긴 후 다시 풀리기 위해 경과되어야 하는 기간   |
| PASSWORD_EXPIRY_DATE     | DATE         | 패스워드 만료일                                              |
| PASSWORD_LIFE_TIME       | INTEGER      | 패스워드 유효기간                                            |
| PASSWORD_GRACE_TIME      | INTEGER      | 패스워드 만료 후 유예기간                                    |
| PASSWORD_REUSE_DATE      | DATE         | 동일한 패스워드가 재사용 가능해지는 날짜                     |
| PASSWORD_REUSE_TIME      | INTEGER      | 미사용                                                       |
| PASSWORD_REUSE_MAX       | INTEGER      | 동일한 패스워드의 재사용 가능 횟수                           |
| PASSWORD_REUSE_COUNT     | INTEGER      | 미사용                                                       |
| PASSWORD_VERIFY_FUNCTION | VARCHAR(128) | 패스워드를 검증할 콜백 함수(Callback Function)               |
| USER_TYPE                | CHAR(1)      | 사용자 타입 표시 U: 사용자(User) R: 롤(Role)                 |
| DISABLE_TCP              | CHAR(1)      | 사용중인 TCP 접속의 제한 여부 표시 T : TCP 접속을 못하고, SSL이나 IPC로만 통신 F : TCP 접속 허용 |
| CREATED                  | DATE         | 데이터베이스 사용자가 생성된 시간                            |
| LAST_DDL_TIME            | DATE         | 사용자에 대해 마지막으로 DDL 변경 작업이 일어난 시간         |

#### 칼럼 정보

##### USER_ID

사용자 식별자로, 시스템의 시퀀스에 의해 자동으로 부여된다.

##### USER_NAME

사용자가 명시한 사용자의 이름이다.

##### PASSWORD

사용자의 패스워드로 암호화 되어 있다.

##### DEFAULT_TBS_ID

기본 테이블스페이스 식별자로, 사용자가 객체 생성 시 테이블스페이스를 명시적으로 기술하지 않을 경우 사용된다.

##### TEMP_TBS_ID

사용자의 임시 테이블스페이스 식별자이다.

##### DISABLE_TCP

사용자의 TCP 접속을 허용하거나 제한하는 것을 나타낸다.

### SYS_USER_ROLES_

사용자에게 부여된 롤(Role) 정보가 기록되는 메타 테이블이다.

| Column name | Type    | Description                 |
| ----------- | ------- | --------------------------- |
| GRANTOR_ID  | INTEGER | 롤을 부여한 사용자의 식별자 |
| GRANTEE_ID  | INTEGER | 롤이 부여된 사용자의 식별자 |
| ROLE_ID     | INTEGER | 롤 식별자                   |

#### 칼럼 정보

##### GRANTOR_ID

롤을 부여한 사용자의 식별자로, SYS_USERS_ 메타 테이블의 한 USER_ID 값과 동일하다.

##### GRANTEE_ID

롤이 부여된 사용자의 식별자로, SYS_USERS_ 메타 테이블의 한 USER_ID 값과 동일하다.

##### ROLE_ID

롤의 식별자로, SYS_USERS_ 메타 테이블의 한 USER_ID 값과 동일하다.

#### 참조 테이블

```
SYS_USERS_
SYS_TABLES_
```

### SYS_VIEWS_

뷰에 대한 기본 정보는 SYS_TABLES_ 메타 테이블에 기록된다. 이 메타 테이블은 그 외의 뷰에 대한 부가 정보를 저장한다.

| Column name | Type    | Description          |
| ----------- | ------- | -------------------- |
| USER_ID     | INTEGER | 뷰의 소유자 식별자   |
| VIEW_ID     | INTEGER | 뷰 식별자            |
| STATUS      | INTEGER | 뷰의 상태            |
| READ_ONLY   | CHAR(1) | 읽기전용 뷰인지 여부 |

#### 칼럼 정보

##### USER_ID

뷰 소유자의 사용자 식별자로, SYS_USERS_ 메타 테이블의 한 USER_ID 값과 동일하다.

##### VIEW_ID

뷰 식별자로, SYS_TABLES_ 메타 테이블의 한 TABLE_ID 값과 동일하다.

##### STATUS

뷰 상태를 나타내는 값이다.

- 0: VALID
- 1: INVALID

#### 참조 테이블

```
SYS_USERS_
SYS_TABLES_
```

### SYS_VIEW_PARSE_

사용자가 정의한 뷰의 구문 텍스트를 기록하는 테이블이다.

| Column name | Type         | Description                                                  |
| ----------- | ------------ | ------------------------------------------------------------ |
| USER_ID     | INTEGER      | 뷰의 소유자 식별자                                           |
| VIEW_ID     | INTEGER      | 뷰 식별자                                                    |
| SEQ_NO      | INTEGER      | 뷰 생성문 텍스트를 여러 개의 텍스트 조각으로 SYS_VIEW_PARSE_에 저장할 때, 여러 레코드 중에서 이 레코드의 위치이다. |
| PARSE       | VARCHAR(100) | 뷰 생성문 텍스트 조각                                        |

#### 칼럼 정보

##### USER_ID

뷰 소유자의 사용자 식별자로, SYS_USERS_ 메타 테이블의 한 USER_ID 값과 동일하다.

##### VIEW_ID

뷰 식별자로, SYS_TABLES_ 메타 테이블의 한 TABLE_ID 값과 동일하다.

##### SEQ_NO

한 뷰의 생성 구문 텍스트를 SYS_VIEW_PARSE_에 여러 개의 레코드로 저장할 때, 이들 레코드 중에서 해당 레코드의 위치를 나타낸다.

##### PARSE

뷰 구문의 조각난 문자열이다. 한 VIEW_ID 값으로 레코드들을 검색하여 SEQ_NO 순서대로 PARSE 값을 합치면 뷰 전체 구문을 생성할 수 있다.

#### 참조 테이블

```
SYS_USERS_
SYS_TABLES_
```

### SYS_VIEW_RELATED_

사용자가 정의한 뷰들이 접근하는 객체에 대한 정보를 기록하는 테이블이다.

| Column name         | Type         | Description                        |
| ------------------- | ------------ | ---------------------------------- |
| USER_ID             | INTEGER      | 뷰의 소유자 식별자                 |
| VIEW_ID             | INTEGER      | 뷰 식별자                          |
| RELATED_USER_ID     | INTEGER      | 뷰가 접근하는 객체의 소유자 식별자 |
| RELATED_OBJECT_NAME | VARCHAR(128) | 뷰가 접근하는 객체의 이름          |
| RELATED_OBJECT_TYPE | INTEGER      | 뷰가 접근하는 객체의 타입          |

#### 칼럼 정보

##### USER_ID

뷰 소유자의 사용자 식별자로, SYS_USERS_ 메타 테이블의 한 USER_ID 값과 동일하다.

##### VIEW_ID

뷰 식별자로, SYS_TABLES_ 메타 테이블의 한 TABLE_ID 값과 동일하다.

##### RELATED_USER_ID

뷰가 접근하는 객체 소유자의 사용자 식별자로, SYS_USERS_ 메타 테이블의 한 USER_ID 값과 동일하다.

##### RELATED_OBJECT_NAME

뷰가 접근하는 객체의 이름이다.

##### RELATED_OBJECT_TYPE

뷰가 접근하는 객체의 타입이다. 뷰는 저장 함수, 테이블, 시퀀스, 다른 뷰, 데이터베이스 링크, 또는 시노님에 접근할 수 있다. 각 객체의 타입 식별자는 다음과 같다.

- 1: 저장 함수
- 2: 테이블, 시퀀스, 뷰
- 4: 데이터베이스 링크
- 5: 시노님

#### 참조 테이블

```
SYS_USERS_
SYS_TABLES_
SYS_PROCEDURES_
```

### SYS_XA_HEURISTIC_TRANS_

데이터베이스가 가지고 있는 글로벌(Global) 트랜잭션 식별자들과 그 상태를 가지고 있는 메타 테이블이다.

| Column name      | Type         | Description                                  |
| ---------------- | ------------ | -------------------------------------------- |
| FORMAT_ID        | BIGINT       | 전역 (Global) 트랜잭션의 형식(Format) 식별자 |
| GLOBAL_TX_ID     | VARCHAR(128) | 전역 트랜잭션 식별자                         |
| BRANCH_QUALIFIER | VARCHAR(128) | 전역 트랜잭션의 branch qualifier             |
| STATUS           | INTEGER      | 전역 트랜잭션 상태                           |
| OCCUR_TIME       | DATE         | XA 트랜잭션이 발생한 시간                    |

#### 칼럼 정보

##### FORMAT_ID

글로벌 트랜잭션의 형식(Format) 식별자

##### GLOBAL_TX_ID

글로벌 트랜잭션 식별자

##### BRANCH_QUALIFIER

글로벌 트랜잭션의 브랜치(Branch) qualifier

##### STATUS

글로벌 트랜잭션의 상태

### SYS_GEOMETRIES_

GEOMETRY 칼럼을 보유한 테이블에 대한 정보를 저장하고 있는 메타 테이블이다.

| Column name     | Type     | Description                            |
| --------------- | -------- | -------------------------------------- |
| USER_ID         | INTERGER | 테이블의 소유자                        |
| TABLE_ID        | INTERGER | 테이블의 식별자                        |
| COLUMN_ID       | INTERGER | 컬럼의 식별자                          |
| COORD_DIMENSION | INTERGER | GEOMETRY 객체의 차원                   |
| SRID            | INTERGER | 데이터베이스 내에서의 공간 참조 식별자 |

### SYS_GEOMETRY_COLUMNS_

GEOMETRY 칼럼에 공간 참조 식별자(SRID, Spatial Reference ID)를 지정, 관리하기 위해 사용한다.

이 메타 테이블의 synonym은 GEOMETRY_COLUMNS_이다.

| Column name       | Type         | Description                            |
| ----------------- | ------------ | -------------------------------------- |
| F_TABLE_SCHEMA    | VARCHAR(128) | 테이블 소유자 이름                     |
| F_TABLE_NAME      | VARCHAR(128) | 테이블 이름                            |
| F_GEOMETRY_COLUMN | VARCHAR(128) | 컬럼의 이름                            |
| COORD_DIMENSION   | INTERGER     | GEOMETRY 객체의 차원                   |
| SRID              | INTERGER     | 데이터베이스 내에서의 공간 참조 식별자 |

### USER_SRS_

공간 참조 식별자(SRID, Spatial Reference IDentifier)와 이에 대응하는 공간 참조 시스템(SRS, Spatial Reference System)에 관한 정보를 관리하기 위해 사용한다.

이 메타 테이블의 synonym은 SPATIAL_REF_SYS 이다.

SPATIAL_REF_SYS 테이블에 Spatial Reference System 메타 데이터를 등록 및 삭제하기 위해서는 SYS_SPATIAL 패키지의 ADD_SPATIAL_REF_SYS, DELETE_SPATIAL_REF_SYS 프로시저를 사용해야한다. 메타 데이터를 등록할 때 SRID와 AUTH_SRID를 동일한 값으로 사용하는것을 권장합니다. 자세한 내용은 *Spatial Manual*을 참조한다.

| Column name | Type          | Description                                           |
| ----------- | ------------- | ----------------------------------------------------- |
| SRID        | INTEGER       | 데이터베이스 내에서의 공간 참조 식별자                |
| AUTH_NAME   | VARCHAR(256)  | 표준 이름                                             |
| AUTH_SRID   | INTEGER       | 표준 식별자                                           |
| SRTEXT      | VARCHAR(2048) | OGC-WKT 형태로 표현 되는 공간 참조 시스템에 대한 설명 |
| PROJ4TEXT   | VARCHAR(2048) | PROJ4에서 사용되는 정보                               |

### 성능 뷰

성능 뷰 (performance view)란 메모리에 존재하는 구조이지만 일반 테이블 형태로 제공되어 시스템 메모리, 프로세스 상태, 세션, 버퍼, 쓰레드 등에 대한 Altibase 시스템 내부 정보를 사용자가 모니터링 할 수 있다.

사용자가 테이블에 저장된 데이터를 검색하기 위하여 SQL을 사용하는 것처럼, Altibase 운용 시 사용되는 메모리 객체 (예. 세션 정보, 로그 정보)에 관한 정보를 SQL문을 이용하여 성능 뷰로부터 쉽게 검색할 수 있다.

이 절에서는 Altibase가 지원하는 성능 뷰의 종류, 구조 및 기능, 조회 방법, 그리고 각 뷰에서 제공하는 정보에 대해 설명한다.

#### 구조 및 기능

Altibase 내부에는 사용자가 생성한 객체 (테이블 같은)뿐만 아니라 DBMS 자체 운용에 필요한 다수의 정보를 저장하고 있다.

특히 Altibase의 경우 메모리 공간 외에도 디스크 공간에도 테이블 생성 및 조회가 가능한 하이브리드 형태이기 때문에, Altibase 자체에 대한 모니터링 기능이 필수적이라고 할 수 있다.

성능 뷰는 Altibase 운용과정에서 사용되는 대부분의 내부 메모리 구조체를 뷰 형태로 제공한 것이다. 해당 테이블에 대해 조회를 하는 순간에 그 데이터가 실시간으로 생성되기 때문에 언제나 Altibase 프로세스 내부의 최신 정보를 얻을 수 있다.

성능 뷰는 항상 읽기 전용 속성을 가진다. 만일 이 테이블에 대해 변경 연산을 시도한다면, Altibase는 에러를 내고, 해당 트랜잭션에 대한 부분 철회 (rollback)를 수행할 것이다.

#### 성능 뷰의 조회 방법

성능 뷰의 전체 목록은 iSQL에서 다음과 같이 조회할 수 있다.

```
iSQL> SELECT * FROM V$TAB;
```

성능 뷰의 스키마는 일반 테이블과 마찬가지로 iSQL 에서 DESC 명령어를 통해 확인할 수 있고, 데이터는 일반 테이블과 동일하게 SELECT문을 이용하여 검색할 수 있다.

#### 성능 뷰의 종류

성능 뷰의 이름은 V$로 시작한다. 아래 표는 전체 성능 뷰의 목록이다.

| 이름                                 | 설명                                                         |
| ------------------------------------ | ------------------------------------------------------------ |
| V$ACCESS_LIST                        | 서버에 접근하는 특정 IP 패킷의 접근 허용 및 제한 정보        |
| V$ALLCOLUMN                          | 성능 뷰를 구성하는 칼럼 정보                                 |
| V$ARCHIVE                            | 아카이브와 백업 관련 정보                                    |
| V$BACKUP_INFO                        | 현재까지 수행된 증분 백업에 대한 정보                        |
| V$BUFFPAGEINFO                       | 버퍼 메니저의 버퍼 프레임 통계 정보                          |
| V$BUFFPOOL_STAT                      | 버퍼 풀 적중 비율 (hit ratio)를 포함한 버퍼 풀 관련 통계 정보 |
| V$CATALOG                            | 테이블의 구조 정보                                           |
| V$DATABASE                           | 메모리 데이터베이스의 내부 정보                              |
| V$DATAFILES                          | 테이블스페이스에서 사용하는 데이터 파일의 정보               |
| V$DATATYPE                           | Altibase가 지원하는 데이터 타입의 정보                       |
| V$DBA_2PC_PENDING                    | in-doubt 상태의 분산 트랜잭션 목록                           |
| V$DBLINK_ALTILINKER_STATUS           | 데이터베이스 링크를 위한 AltiLinker 프로세스의 상태 정보     |
| V$DBLINK_DATABASE_LINK_INFO          | 데이터베이스에 존재하는 데이터베이스 링크 객체 정보          |
| V$DBLINK_GLOBAL_TRANSACTION_INFO     | 데이터베이스 링크를 사용하는 트랜잭션 정보                   |
| V$DBLINK_LINKER_CONTROL_SESSION_INFO | 링커 제어 세션의 상태 정보                                   |
| V$DBLINK_LINKER_DATA_SESSION_INFO    | 링커 데이터 세션들의 상태 정보                               |
| V$DBLINK_LINKER_SESSION_INFO         | 링커 제어 세션과 링커 데이터 세션의 개수 정보                |
| V$DBLINK_NOTIFIER_TRANSACTION_INFO   | AltiLinker가 처리중인 (장애가 발생한) 분산 트랜잭션의 정보   |
| V$DBLINK_REMOTE_STATEMENT_INFO       | 데이터베이스 링크 사용시 원격 서버에서 수행한 구문 (statement) 정보 |
| V$DBLINK_REMOTE_TRANSACTION_INFO     | 데이터베이스 링크 사용시 원격 서버에서 발생한 트랜잭션 정보  |
| V$DBMS_STATS                         | 데이터베이스 전체의 통계 정보                                |
| V$DB_FREEPAGELISTS                   | 사용가능한 페이지 리스트 정보                                |
| V$DB_PROTOCOL                        | 서버로 유입되는 데이터베이스 프로토콜의 정보                 |
| V$DIRECT_PATH_INSERT                 | Direct-path 업로드 관련 통계 정보                            |
| V$DISKTBL_INFO                       | 디스크 테이블 정보                                           |
| V$DISK_BTREE_HEADER                  | 디스크 BTREE 인덱스들의 헤더 정보                            |
| V$DISK_RTREE_HEADER                  | 디스크 RTREE 인덱스들의 헤더 정보                            |
| V$DISK_TEMP_INFO                     | 전체 디스크 임시 테이블의 메모리 사용 정보                   |
| V$DISK_TEMP_STAT                     | 현재 사용중인 각각의 디스크 임시 테이블 정보                 |
| V$DISK_UNDO_USAGE                    | 디스크상에서 현재 사용중인 언두 테이블스페이스의 양에 대한 정보 |
| V$EVENT_NAME                         | Altibase 서버의 대기 이벤트 정보                             |
| V$EXTPROC_AGENT                      | 외부 프로시저 실행을 위해 생성된 에이전트 프로세스(agent process)의 정보 |
| V$FILESTAT                           | 디스크의 데이터 파일별 I/O 통계 정보                         |
| V$FLUSHER                            | 버퍼를 플러쉬하는 플러셔에 대한 정보                         |
| V$FLUSHINFO                          | 버퍼 플러쉬 정보                                             |
| V$INDEX                              | 테이블의 인덱스 정보                                         |
| V$INSTANCE                           | Altibase의 현재 구동 단계 정보                               |
| V$INTERNAL_SESSION                   | DBMS_CONCURRENT_EXEC 패키지에서 생성된 세션의 정보           |
| V$LATCH                              | 버퍼 풀의 버퍼 제어 블록 (BCB) 래치 (latch) 정보와 읽기 또는 쓰기가 시도된 페이지에 대한 read/write latch에 대한 통계 정보 |
| V$LFG                                | LFG에 대한 정보와 그룹커밋 관련 통계값                       |
| V$LOCK                               | 현재 시점에서 데이터베이스의 모든 테이블 레벨 lock 노드 정보 |
| V$LOCK_STATEMENT                     | Lock과 statement 에 대한 정보                                |
| V$LOCK_WAIT                          | 트랜잭션의 락 획득을 위한 대기 상태 정보                     |
| V$LOG                                | 로그 앵커 정보                                               |
| V$MEMGC                              | 메모리 공간 회수를 위한 garbage collection에 대한 정보       |
| V$MEMSTAT                            | Altibase 프로세스가 사용하는 메모리 통계 정보                |
| V$MEMTBL_INFO                        | 메모리 테이블 정보                                           |
| V$MEM_BTREE_HEADER                   | 메모리 BTREE 인덱스의 헤더 정보                              |
| V$MEM_BTREE_NODEPOOL                 | 메모리 BTREE 인덱스를 위한 노드 풀 정보                      |
| V$MEM_RTREE_HEADER                   | 메모리 RTREE 인덱스의 헤더 정보                              |
| V$MEM_RTREE_NODEPOOL                 | 메모리 RTREE 인덱스를 위한 노드 풀 정보                      |
| V$MEM_TABLESPACES                    | 메모리에 생성된 테이블스페이스 정보                          |
| V$MEM_TABLESPACE_CHECKPOINT_PATHS    | 체크포인트 발생시 반영되는 DB 파일의 위치 정보               |
| V$MEM_TABLESPACE_STATUS_DESC         | 메모리 테이블스페이스의 상태 정보                            |
| V$MUTEX                              | 동시성 제어를 위해서 Altibase 프로세스에서 사용되고 있는 뮤텍스(mutex) 통계 정보 |
| V$NLS_PARAMETERS                     | NLS 관련 파라미터 정보                                       |
| V$NLS_TERRITORY                      | 설정 가능한 지역의 이름 정보                                 |
| V$OBSOLETE_BACKUP_INFO               | 더 이상 유지할 필요가 없는 백업 정보                         |
| V$PKGTEXT                            | 시스템에서 수행되는 패키지의 문자열 정보                     |
| V$PLANTEXT                           | SQL의 실행 계획 텍스트 정보                                  |
| V$PROCTEXT                           | 저장 프로시저의 텍스트 정보                                  |
| V$PROPERTY                           | Altibase에 설정된 프로퍼티 정보                              |
| V$REPEXEC                            | 이중화 관리자 정보                                           |
| V$REPGAP                             | 이중화 송신자의 작업 로그 레코드와 현재 생성된 최근 로그 레코드간의 차이 정보 |
| V$REPGAP_PARALLEL                    | 병렬 수행중인 이중화 송신 쓰레드의 작업 로그 레코드와 현재 생성된 최근 로그 레코드간의 차이 정보 |
| V$REPLOGBUFFER                       | 이중화 전용 로그 버퍼의 정보                                 |
| V$REPOFFLINE_STATUS                  | 오프라인 이중화의 수행 상태 정보                             |
| V$REPRECEIVER                        | 이중화 수신자 정보                                           |
| V$REPRECEIVER_COLUMN                 | 이중화 수신자의 이중화 대상 칼럼 정보                        |
| V$ REPRECEIVER_PARALLEL              | 병렬 수행중인 이중화 수신 쓰레드에 대한 정보                 |
| V$REPRECEIVER_PARALLEL_APPLY         | 이중화 적용자 쓰레드에 대한 정보                             |
| V$REPRECEIVER_STATISTICS             | 이중화 수신 쓰레드의 작업별 수행시간에 대한 통계 정보        |
| V$REPRECEIVER_TRANSTBL               | 이중화 수신자의 트랜잭션 테이블 정보                         |
| V$REPRECEIVER_TRANSTBL_PARALLEL      | 병렬 수행중인 이중화 수신 쓰레드가 사용하는 트랜잭션 테이블 정보 |
| V$REPRECOVERY                        | 이중화를 이용한 복구 정보                                    |
| V$REPSENDER                          | 이중화 송신자 정보                                           |
| V$REPSENDER_PARALLEL                 | 병렬 수행중인 이중화 송신 쓰레드에 대한 정보                 |
| V$REPSENDER_SENT_LOG_COUNT           | 이중화 송신자가 전송한 로그의 DML 타입별 개수 정보           |
| V$REPSENDER_SENT_LOG_COUNT_PARALLEL  | Eager 모드의 병렬 이중화에서 각 송신 쓰레드가 전송한 로그의 DML 타입별 개수 정보 |
| V$REPSENDER_STATISTICS               | 이중화 송신 쓰레드의 작업 별 수행시간에 대한 통계 정보       |
| V$REPSENDER_TRANSTBL                 | 이중화 송신자의 트랜잭션 테이블 정보                         |
| V$REPSENDER_TRANSTBL_PARALLEL        | 병렬 수행중인 이중화 송신 쓰레드가 사용하는 트랜잭션 테이블 정보 |
| V$REPSYNC                            | 이중화로 동기화 중인 테이블의 정보                           |
| V$SBUFFER_STAT                       | 보조 버퍼(Secondary Buffer)에 대한 통계 정보                 |
| V$SEGMENT                            | 테이블과 색인을 구성하는 세그먼트 정보                       |
| V$SEQ                                | 시퀀스 관련 정보                                             |
| V$SERVICE_THREAD                     | Multiplexing 관련 서비스 쓰레드 정보                         |
| V$SERVICE_THREAD_MGR                 | 멀티플렉싱 (Multiplexing)과 관련하여 서비스 쓰레드가 생성되거나 삭제된 정보 |
| V$SESSION                            | 클라이언트에 대응하는 Altibase 내부에 생성된 세션 정보       |
| V$SESSION_EVENT                      | 구동 후부터 현재까지 접속한 세션의 모든 대기 이벤트 통계 정보 |
| V$SESSION_WAIT                       | 현재 접속한 상태에 있는 모든 세션의 대기 이벤트 정보         |
| V$SESSION_WAIT_CLASS                 | 현재 접속한 상태에 있는 모든 세션에 대해 대기 이벤트, 대기 클래스별로 누적된 대기 통계 정보 |
| V$SESSIONMGR                         | Altibase의 세션 통계 정보                                    |
| V$SESSTAT                            | 현재 접속된 세션의 상태 정보                                 |
| V$SFLUSHER                           | 보조 버퍼(Secondary Buffer)의 페이지를 디스크에 플러시 하는 작업에 대한 정보 |
| V$SFLUSHINFO                         | 보조 버퍼(Secondary Buffer)의 플러시 정보                    |
| V$SNAPSHOT                           | 스냅샷(SNAPSHOT)의 설정 상태와 메모리, 디스크 언두 테이블스페이스의 사용 정보 |
| V$SQLTEXT                            | 시스템에서 수행되는 SQL문의 텍스트 정보                      |
| V$SQL_PLAN_CACHE                     | SQL Plan Cache의 현재 상태 및 통계 정보                      |
| V$SQL_PLAN_CACHE_PCO                 | SQL Plan Cache에 등록된 Plan Cache 객체에 대한 정보          |
| V$SQL_PLAN_CACHE_SQLTEXT             | SQL Plan Cache에 등록된 SQL 문 정보                          |
| V$STABLE_MEM_DATAFILES               | 데이터 파일의 전체 경로 정보                                 |
| V$STATEMENT                          | 현재 Altibase에 생성된 모든 세션의 구문 정보                 |
| V$STATNAME                           | 시스템 및 세션 상태와 이름 정보                              |
| V$ST_ANGULAR_UNIT                    | 향후 확장 예정                                               |
| V$ST_AREA_UNIT                       | 향후 확장 예정                                               |
| V$ST_LINEAR_UNIT                     | 향후 확장 예정                                               |
| V$SYSSTAT                            | 시스템 상태 정보                                             |
| V$SYSTEM_CONFLICT_PAGE               | 페이지 타입 별 래치 경합 정보                                |
| V$SYSTEM_EVENT                       | 구동부터 현재까지의 대기 이벤트별 누적된 대기 통계 정보      |
| V$SYSTEM_WAIT_CLASS                  | 구동부터 현재까지의 대기 클래스별 누적된대기 통계 정보       |
| V$TABLE                              | 모든 성능 뷰의 레코드 및 칼럼 정보                           |
| V$TABLESPACES                        | 테이블스페이스 정보                                          |
| V$TIME_ZONE_NAMES                    | TIME_ZONE 프로퍼티에 설정할 수 있는 지역 이름과 약어 및 UTC 오프셋 값의 정보 |
| V$TRACELOG                           | 트레이스 로깅 정보                                           |
| V$TRANSACTION                        | 트랜잭션 객체 정보                                           |
| V$TRANSACTION_MGR                    | Altibase 트랜잭션 관리자 정보                                |
| V$TSSEGS                             | 모든 TSS 세그먼트들의 정보                                   |
| V$TXSEGS                             | 바인딩된 트랜잭션 세그먼트들의 정보                          |
| V$UDSEGS                             | 모든 언두 세그먼트들의 정보                                  |
| V$UNDO_BUFF_STAT                     | Undo 테이블스페이스의 버퍼 풀 관련 통계 정보                 |
| V$USAGE                              | 데이터베이스에 존재하는 테이블과 인덱스가 사용하는 공간량에 대한 정보 |
| V$VERSION                            | Altibase 버전 정보                                           |
| V$VOL_TABLESPACES                    | 휘발성 테이블스페이스에 대한 정보                            |
| V$WAIT_CLASS_NAME                    | Altibase 서버상의 대기 이벤트들을 클래스로 그룹화기 위한 정보 |
| V$XID                                | DBMS에 현재 존재하는 분산 트랜잭션 브랜치인 XID의 목록       |

### V$ACCESS_LIST

Altibase에 접근하는 특정 IP 패킷의 접근 허용 및 제한 정보를 보여준다.

| Column name | Type        | Description                                     |
| ----------- | ----------- | ----------------------------------------------- |
| ID          | INTEGER     | ACCESS LIST 식별자                              |
| ADDRESS     | VARCHAR(40) | IP 주소                                         |
| OPERATION   | VARCHAR(6)  | IP 주소 접근 허용 및 제한 여부                  |
| MASK        | VARCHAR(16) | 서브넷 마스크(IPv4) 또는 prefix 비트 길이(IPv6) |
| LIMIT       | INTEGER     | 세션 최대 허용 개수                             |
| CONNECTED   | INTEGER     | 현재 세션 접속 개수                             |

#### **칼럼 정보**

##### ID

IP 패킷의 접근 허용 및 제한 목록의 식별자를 기술한다.

##### ADDRESS

IP 패킷 주소를 기술한다

##### OPERATION

IP 패킷 주소의 접근 허용 및 제한 여부를 보여준다.

- PERMIT : 접근 허용
- DENY: 접근 제한

##### MASK

IPv4 주소일 경우 서브넷 마스크를 기술하고, IPv6 주소인 경우에는 prefix 비트의 길이를 기술한다. 자세한 내용은 ACCESS_LIST 프로퍼티의 설명을 참조한다

**LIMIT**

ACCESS_LIST에 명시된 접속 가능한 IP 주소 영역에서 허용되는 최대 접속 세션 개수.

운영 중 RELOAD ACCESS LIST로 ACCESS_LIST를 추가하면, 기존에 연결된 세션은 영향을 받지 않으며, 변경 이후 새로운 연결 요청에 대해서만 ACCESS_LIST 조건이 적용된다. 예를 들어 ACCESS_LIST에 limit값을 설정 후 RELOAD ACCESS LIST 수행하면, 적용 이후 새로운 연결에 대해서만 limit 값이 적용된다. 이런 경우, V$ACCESS_LIST 조회시 Limit 값보다 CONNECTED 값이 더 클 수도 있다.

**CONNECTED**

ACCESS_LIST에 해당하는 현재 접속된 세션 개수

### V$ALLCOLUMN

모든 성능 뷰의 칼럼 정보를 나타낸다.

| Column name | Type        | Description         |
| ----------- | ----------- | ------------------- |
| TABLENAME   | VARCHAR(39) | 성능 뷰 이름        |
| COLNAME     | VARCHAR(39) | 성능 뷰의 칼럼 이름 |

#### 칼럼 정보

##### TABLENAME

성능 뷰의 이름을 나타낸다.

##### COLNAME

성능 뷰의 칼럼 이름을 나타낸다.

### V$ARCHIVE

아카이브와 백업 관련 정보를 보여준다.

| Column name           | Type          | Description                                                  |
| --------------------- | ------------- | ------------------------------------------------------------ |
| LFG_ID                | INTEGER       | 로그 파일의 그룹 식별자                                      |
| ARCHIVE_MODE          | BIGINT        | 아카이브 로그 모드 0: no archive log 모드 1: archive log 모드 |
| ARCHIVE_THR_RUNNING   | BIGINT        | 아카이브로그 쓰레드 수행 여부                                |
| ARCHIVE_DEST          | VARCHAR(1024) | 로그를 아카이브 하여 저장하는 디렉터리                       |
| NEXTLOGFILE_TO_ARCH   | INTEGER       | 다음 번에 아카이브 할 로그 파일 번호                         |
| OLDEST_ACTIVE_LOGFILE | INTEGER       | 온라인로그 파일 중 가장 오래된 로그 파일 번호                |
| CURRENT_LOGFILE       | INTEGER       | 현재 온라인로그 파일 번호                                    |

#### 칼럼 정보

##### LFG_ID

이는 0의 값을 가진 로그파일 그룹 고유번호이다.

##### ARCHIVE_MODE

데이터베이스의 아카이브 로그 모드를 나타낸다.

0: 노(No) 아카이브 로그 모드

1: 아카이브 로그 모드

### V$BACKUP_INFO

현재까지 수행된 모든 증분 백업에 대한 정보를 보여준다.

| Column name                    | Type      | Description                 |
| ------------------------------ | --------- | --------------------------- |
| BEGIN_BACKUP_TIME              | CHAR(24)  | 백업 시작 일시              |
| END_BACKUP_TIME                | CHAR(24)  | 백업 완료 일시              |
| INCREMENTAL_BACKUP_CHUNK_COUNT | INTEGER   | Incremental chunk의 크기    |
| BACKUP_TARGET                  | INTEGER   | 백업 대상                   |
| BACKUP_LEVEL                   | INTEGER   | 백업 레벨                   |
| BACKUP_TYPE                    | INTEGER   | 백업 유형                   |
| TABLESPACE_ID                  | INTEGER   | 백업 대상 테이블스페이스 ID |
| FILE_ID                        | INTEGER   | 백업 대상 데이터파일 ID     |
| BACKUP_TAG                     | CHAR(128) | 백업 태그 이름              |
| BACKUP_FILE                    | CHAR(512) | 백업 파일                   |

#### 칼럼 정보

##### BEGIN_BACKUP_TIME

백업이 시작된 일시를 나타낸다. 'YYYY-MM-DD HH:MM:SS'의 형식으로 표시된다.

##### END_BACKUP_TIME

백업이 완료된 일시를 나타낸다. 'YYYY-MM-DD HH:MM:SS'의 형식으로 표시된다.

##### INCREMENTAL_BACKUP_CHUNK_COUNT

레벨 0 증분 백업의 경우, 항상 0으로 표시된다.

레벨 1 증분 백업의 경우, incremental chunk의 크기를 나타낸다.

incremental chunk에 대해서는 INCREMENTAL_BACKUP_CHUNK_SIZE 프로퍼티의 설명을 참고하라.

##### BACKUP_TARGET

백업 대상을 나타낸다.

1: 데이터베이스

2: 테이블스페이스

##### BACKUP_LEVEL

백업 레벨을 나타낸다.

1: 레벨 0

2: 레벨 1

##### BACKUP_TYPE

백업 유형을 나타낸다.

1: 전체 백업

2: 차등 증분 백업

4: 누적 증분 백업

##### TABLESPACE_ID

백업된 데이터파일이 속한 테이블스페이스의 ID를 나타낸다.

##### FILE_ID

백업된 데이터파일의 ID를 나타낸다.

##### BACKUP_TAG

증분 백업 수행시 사용된 백업 태그 이름을 나타낸다.

##### BACKUP_FILE

백업 파일 이름을 포함한 전제 경로를 나타낸다.

### V$BUFFPAGEINFO

버퍼 관리자가 관리하는 버퍼 프레임의 페이지 타입별 주요 연산들에 대한 통계치를 보여준다.

| Column name       | Type        | Description                      |
| ----------------- | ----------- | -------------------------------- |
| PAGE_TYPE         | VARCHAR(21) | 페이지 타입                      |
| READ_PAGE_COUNT   | BIGINT      | DISK I/O (READ)를 유발한 횟수    |
| GET_PAGE_COUNT    | BIGINT      | 버퍼 프레임을 요구한 횟수        |
| FIX_PAGE_COUNT    | BIGINT      | 버퍼 프레임에 고정(fix)한 횟수   |
| CREATE_PAGE_COUNT | BIGINT      | 새로운 버퍼 프레임을 요구한 횟수 |
| HIT_RATIO         | DOUBLE      | 버퍼 프레임 적중률 (hit ratio)   |

#### 칼럼 정보

##### PAGE_TYPE

버퍼 페이지 타입을 나타내며, 다음과 같은 페이지 타입이 있다.

| PAGE_TYPE             | Description                                                  |
| --------------------- | ------------------------------------------------------------ |
| PAGE UNFORMAT         | 포맷되지 않은 페이지                                         |
| PAGE FORMAT           | 포맷된 페이지                                                |
| PAGE INDEX META BTREE | B-트리 인덱스에 대한 메타 정보가 쓰여진 페이지               |
| PAGE INDEX META RTREE | R-트리 인덱스에 대한 메타 정보가 쓰여진 페이지               |
| PAGE INDEX BTREE      | B-트리 인덱스 노드가 쓰여진 페이지                           |
| PAGE INDEX RTREE      | R-트리 인덱스 노드가 쓰여진 페이지                           |
| PAGE TABLE            | 테이블 레코드가 저장된 페이지                                |
| PAGE TEMP TABLE META  | 한 임시 테이블에 대한 메타 정보가 저장된 페이지              |
| PAGE TEMP TABLE DATA  | 임시 테이블에 저장된 레코드가 쓰여진 페이지                  |
| PAGE TSS              | 트랜잭션의 상태에 대한 정보가 쓰여진 페이지. 여러 트랜잭션 상태 슬롯 (Transaction Status Slots, TSS)이 한 페이지에 저장될 수 있다. |
| PAGE UNDO             | 언두 정보가 저장된 페이지. 한 페이지에 여러 언두 레코드가 저장될 수 있다. |
| PAGE LOB DATA         | LOB 타입 데이터가 저장된 페이지. 한 페이지는 한 개의 LOB칼럼만 담을 수 있다. 한 개의 LOB칼럼은 여러 페이지에 걸쳐서 저장될 수 있다. |
| PAGE LOB INODE        | 특정 크기를 초과하는 LOB 데이터와 관련된 인덱스 노드가 저장된 페이지 |
| PAGE FMS SEGHDR       | 한 개의 FMS 헤더가 저장된 페이지                             |
| PAGE FMS EXTDIR       | 한 개의 FMS extent directory 가 저장된 페이지                |
| PAGE TMS SEGHDR       | 한 개의 TMS 헤더가 저장된 페이지                             |
| PAGE TMS LFBMP        | 한 개의 TMS 리프 (leaf) 비트맵 노드가 저장된 페이지          |
| PAGE TMS ITBMP        | 한 개의 TMS 중간 비트맵 노드가 저장된 페이지                 |
| PAGE TMS RTBMP        | 한 개의 TMS 루트 비트맵 노드가 저장된 페이지                 |
| PAGE TMS EXTDIR       | 한 개의 TMS extent directory 가 저장된 페이지                |
| PAGE CMS SEGHDR       | 한 개의 CMS 헤더가 저장된 페이지                             |
| PAGE CMS EXTDIR       | 한 개의 CMS extent directory 가 저장된 페이지                |
| PAGE FEBT FSB         | 한 개의 데이터파일 헤더가 저장된 페이지                      |
| PAGE FEBT EGH         | 데이터파일 내의 확장 그룹 헤더가 저장된 페이지. 한 페이지는 하나의 헤더만 저장할 수 있다. |
| PAGE LOB META         | LOB 데이터 칼럼에 대한 메타 정보가 쓰여진 페이지             |
| PAGE HV TEMP NODE     | 해쉬 값 기반의 임시 인덱스 노드가 저장된 페이지              |

##### READ_PAGE_COUNT

서버 구동 이후부터 현재까지 PAGE_TYPE에 해당하는 버퍼 프레임들에 DISK I/O (READ)를 유발시킨 총 횟수를 나타낸다. 0 이상의 값을 갖는다.

##### GET_PAGE_COUNT

서버 구동 이후부터 현재까지 버퍼 관리자에게 데이터 쓰기나 읽기 목적으로 PAGE_TYPE에 해당하는 버퍼 프레임들을 요구한 총 횟수를 나타낸다. 0 이상의 값을 갖는다.

##### FIX_PAGE_COUNT

서버 구동 이후부터 현재까지 버퍼 관리자에게 데이터 쓰기나 읽기를 목적으로 PAGE_TYPE에 해당하는 버퍼 프레임들을 고정(Fix)한 총 횟수를 나타낸다. 0 이상의 값을 갖는다.

##### CREATE_PAGE_COUNT

서버 구동 이후부터 현재까지 버퍼 관리자에게 PAGE_TYPE에 해당하는 새로운 버퍼 프레임들을 요구한 총 횟수를 나타낸다. 0 이상의 값을 갖는다.

##### HIT_RATIO

서버 구동 이후부터 현재까지 이 버퍼에 대한 적중률 (hit ratio)을 나타낸다. 이 값은 (GET_PAGE_COUNT + FIX_PAGE_COUNT - READ_PAGE_COUNT) / (GET_PAGE_COUNT + FIX_PAGE_COUNT)로 구해진다.

#### 예제

서버 구동 이후 버퍼에서 관리된 페이지 타입별 주요 연산들의 누적치를 확인한다.

```
iSQL> select * from v$buffpageinfo;
PAGE_TYPE            READ_PAGE_COUNT      GET_PAGE_COUNT       
---------------------------------------------------------------------
FIX_PAGE_COUNT       CREATE_PAGE_COUNT    HIT_RATIO       
---------------------------------------------------------------------
PAGE UNFORMAT          0                    0                
0                    0                    0                      
PAGE FORMAT            0                    0                 
0                    0                    0                      
PAGE INDEX META BTREE  4                    0                 
4                    0                    0                      
PAGE INDEX META RTREE  0                    0                 
0                    0                    0                      
PAGE INDEX BTREE       12                   0                 
12                   0                    0                      
PAGE INDEX RTREE       0                    0                 
0                    0                    0                      
PAGE TABLE             0                    0                   
0                    0                    0                      
PAGE TEMP TABLE META   0                    0                 
0                    0                    0                      
PAGE TEMP TABLE DATA   0                    0                 
0                    0                    0                      
PAGE TSS               0                    0                   
0                    0                    0                      
PAGE UNDO              0                    0                 
0                    0                    0                      
PAGE LOB DATA          0                    0                 
0                    0                    0                      
PAGE LOB INODE         0                    0                  
0                    0                    0                      
PAGE FMS SEGHDR        0                    0                 
0                    0                    0                      
PAGE FMS EXTDIR        0                    0                 
0                    0                    0                      
PAGE TMS SEGHDR        5                    19               
4                    0                    73.6842105263158       
PAGE TMS LFBMP         0                    0                 
0                    0                    0                      
PAGE TMS ITBMP         0                    0                   
0                    0                    0                      
PAGE TMS RTBMP         0                    0                 
0                    0                    0                      
PAGE TMS EXTDIR        0                    0                 
0                    0                    0                      
PAGE CMS SEGHDR        0                    1536             
0                    512                  100                    
PAGE CMS EXTDIR        0                    0                 
0                    0                    0                      
PAGE FEBT FSB          2                    1024               
515                  2                    99.8046875             
PAGE FEBT EGH          0                    512               
0                    4                    100                    
PAGE LOB META          0                    0                 
0                    0                    0                      
PAGE HV TEMP NODE      0                    0                 
0                    0                    0                      
26 rows selected.
```

### V$BUFFPOOL_STAT

버퍼 풀 적중률과 버퍼 풀 내의 버퍼 제어 블록 (Buffer Control Block, BCB) 개수를 포함하여, 버퍼 풀 관련 통계 정보를 보여준다.

| Column name            | Type    | Description                                                  |
| ---------------------- | ------- | ------------------------------------------------------------ |
| ID                     | INTEGER | 버퍼 풀 식별자                                               |
| POOL_SIZE              | INTEGER | 버퍼 풀 내의 페이지 개수                                     |
| PAGE_SIZE              | INTEGER | 페이지 크기 (bytes)                                          |
| HASH_BUCKET_COUNT      | INTEGER | 해쉬 테이블의 버킷 개수                                      |
| HASH_CHAIN_LATCH_COUNT | INTEGER | 해쉬 테이블에 사용되는 체인 래치 개수                        |
| LRU_LIST_COUNT         | INTEGER | LRU 리스트 개수                                              |
| PREPARE_LIST_COUNT     | INTEGER | 버퍼 풀의 Prepare 리스트 개수                                |
| FLUSH_LIST_COUNT       | INTEGER | 버퍼 풀의 플러시 리스트 개수                                 |
| CHECKPOINT_LIST_COUNT  | INTEGER | 버퍼 풀의 체크포인트 리스트 개수                             |
| VICTIM_SEARCH_COUNT    | INTEGER | LRU 리스트에서 victim 검색 개수                              |
| HASH_PAGES             | INTEGER | 현재 해쉬 테이블에 삽입된 페이지 개수                        |
| HOT_LIST_PAGES         | INTEGER | 현재 LRU hot 리스트에 있는 페이지 개수                       |
| COLD_LIST_PAGES        | INTEGER | 현재 LRU cold 리스트에 있는 페이지 개수                      |
| PREPARE_LIST_PAGES     | INTEGER | 현재 Prepare 리스트에 있는 페이지 개수                       |
| FLUSH_LIST_PAGES       | INTEGER | 현재 플러시 리스트에 있는 페이지 개수                        |
| CHECKPOINT_LIST_PAGES  | INTEGER | 현재 체크포인트 리스트에 있는 페이지 개수                    |
| FIX_PAGES              | BIGINT  | 래치 없이 페이지 고정을 요청한 누적 횟수                     |
| GET_PAGES              | BIGINT  | 래치를 획득하면서 페이지를 요청한 누적 횟수                  |
| READ_PAGES             | BIGINT  | 페이지 요청시 디스크에서 페이지를 읽은 누적 횟수             |
| CREATE_PAGES           | BIGINT  | 새로운 페이지를 생성한 누적 횟수                             |
| HIT_RATIO              | DOUBLE  | 시스템 구동 후부터 버퍼 풀에서 누적 적중률                   |
| HOT_HITS               | BIGINT  | LRU hot 리스트에 접근된 누적 횟수                            |
| COLD_HITS              | BIGINT  | LRU cold 리스트에 접근된 누적 횟수                           |
| PREPARE_HITS           | BIGINT  | Prepare 리스트에 접근된 누적 횟수                            |
| FLUSH_HITS             | BIGINT  | 플러시 리스트에 접근된 누적 횟수                             |
| OTHER_HITS             | BIGINT  | 어떤 리스트에도 속하지 않은 버퍼에 접근된 누적 횟수          |
| PREPARE_VICTIMS        | BIGINT  | Prepare 리스트에서 교체 대상을 찾은 누적 횟수                |
| LRU_VICTIMS            | BIGINT  | LRU 리스트에서 교체 대상을 찾은 누적 횟수                    |
| VICTIM_FAILS           | BIGINT  | 교체 대상 검색에 실패한 횟수                                 |
| PREPARE_AGAIN_VICTIMS  | BIGINT  | LRU 리스트에서 교체 대상 찾기를 실패한 후, 다시 prepare 리스트에서 교체 대상 버퍼를 찾은 누적 횟수 |
| VICTIM_SEARCH_WARP     | BIGINT  | Prepare 리스트와 LRU 리스트에서 교체 대상 찾기를 실패한 후 다음 Prepare 리스트로 검색 대상을 옮긴 횟수 |
| LRU_SEARCHS            | BIGINT  | LRU 리스트에서 검색한 버퍼의 누적 개수                       |
| LRU_SEARCHS_AVG        | INTEGER | 교체 대상을 검색한 평균 버퍼 수                              |
| LRU_TO_HOTS            | BIGINT  | LRU 리스트에서 hot 영역으로 버퍼 제어 블록 (BCB)을 옮긴 누적 횟수 |
| LRU_TO_COLDS           | BIGINT  | LRU 리스트에서 cold 영역으로 BCB를 옮긴 누적 횟수            |
| LRU_TO_FLUSHS          | BIGINT  | LRU 리스트에서 플러시 리스트로 BCB를 옮긴 누적 횟수          |
| HOT_INSERTIONS         | BIGINT  | LRU hot 리스트에 삽입된 누적 횟수                            |
| COLD_INSERTIONS        | BIGINT  | LRU cold 리스트에 삽입된 누적 횟수                           |
| DB_SINGLE_READ_PERF    | DOUBLE  | 한 개의 데이터 페이지 요청 시, 초당 디스크로부터 읽은 평균 바이트 수 |
| DB_MULTI_READ_PERF     | DOUBLE  | 여러 데이터 페이지가 동시에 디스크의 데이터파일에서 읽혀질 때, 초당 읽은 평균 바이트 수 |

#### 칼럼 정보

##### ID

버퍼 풀 고유 번호를 나타낸다. 현재 다중 버퍼 풀을 지원하지 않기 때문에 이 값은 항상 0이다.

##### POOL_SIZE

버퍼 풀의 페이지 개수이다. POOL_SIZE * PAGE_SIZE는 프로퍼티 BUFFER_AREA_SIZE의 크기와 같다.

##### PAGE_SIZE

현재 버퍼 풀에서 사용되는 페이지의 크기를 나타낸다. 현재는 다중 버퍼 풀을 지원하지 않기 때문에 8192바이트로 고정되어 있다.

##### HASH_BUCKET_COUNT

해쉬 테이블의 버킷 개수를 나타낸다. 프로퍼티 BUFFER_HASH_BUCKET_DENSITY에 의해 결정된다. 서버 구동 중에는 변경할 수 없다. 이 값이 클수록 해쉬 버킷 리스트의 탐색 비용이 감소된다.

##### HASH_CHAIN_LATCH_COUNT

해쉬 테이블에 사용되는 체인 래치의 개수를 나타낸다. 이 값이 클수록 해쉬 탐색시 발생할 수 있는 래치 경합이 줄어든다.

##### LRU_LIST_COUNT

버퍼 풀의 LRU 리스트 개수를 나타낸다.

##### PREPARE_LIST_COUNT

버퍼 풀의 prepare 리스트 개수를 나타낸다.

##### FLUSH_LIST_COUNT

버퍼 풀의 플러시 리스트 개수이다. 버퍼에 올라와 있는 페이지 중 수정되어 디스크에 반영해야 할 페이지가 플러시 리스트에 삽입된다.

##### CHECKPOINT_LIST_COUNT

버퍼 풀의 체크포인트 리스트 개수를 나타낸다.

##### VICTIM_SEARCH_COUNT

LRU 리스트에서 교체 대상을 검색할 때 몇 개까지 검색할지를 나타낸다. 명시된 값만큼 검색해도 교체 대상을 찾지 못하면 플러셔가 prepare 리스트에 clean 버퍼가 삽입될 때까지 대기한다.

##### HASH_PAGES

해쉬 테이블에 삽입된 버퍼 수를 나타낸다. 이 값은 현재 사용중인 버퍼의 수를 의미한다.

##### HOT_LIST_PAGES

LRU hot 리스트에 존재하는 버퍼 수를 나타낸다.

##### COLD_LIST_PAGES

LRU cold 리스트에 존재하는 버퍼 수를 나타낸다.

##### PREPARE_LIST_PAGES

prepare 리스트에 존재하는 버퍼 수를 나타낸다. 이 값이 0이면 교체 대상을 얻기 위해 LRU 리스트를 조회한다.

##### FLUSH_LIST_PAGES

플러시 리스트에 존재하는 버퍼 수를 나타낸다. 값이 크면 플러시할 버퍼가 많다는 의미이다.

##### CHECKPOINT_LIST_PAGES

체크포인트 리스트에 존재하는 버퍼 수를 나타낸다. 이 값은 갱신된 페이지의 수를 의미한다.

##### FIX_PAGES

래치 획득없이 페이지를 요청한 횟수이다. 시스템 구동 후부터 누적된 횟수이다.

##### GET_PAGES

페이지 래치 획득과 함께 요청된 횟수를 나타낸다.

##### READ_PAGES

페이지 요청 시 디스크에서 페이지를 읽은 누적 횟수이다. 버퍼 miss 횟수와 동일한 의미이다.

##### CREATE_PAGES

새로운 페이지에 데이터를 삽입하기 위해 페이지를 할당한 누적 횟수이다. 페이지 생성은 실제로 디스크 I/O를 수반하지는 않는다.

##### HIT_RATIO

버퍼 풀의 누적 적중률 (hit ratio)을 나타낸다. 이 값은 (GET_PAGES + FIX_PAGES - READ_PAGES)/(GET_PAGES + FIX_PAGES) 으로 계산할 수 있다. 이 값이 작으면 메모리 버퍼 대신에 디스크로부터 읽기(read page) 횟수가 많다는 것이다. 즉 이 값이 작으면, 시스템이 빠른 질의 처리를 못하고 있다는 것을 보여준다.

##### HOT_HITS

LRU hot 리스트에서 hit가 발생한 누적 횟수를 나타낸다. Hit란 페이지 요청시 해당 페이지가 이미 버퍼에 있어서 디스크로부터 읽기를 유발시키지 않음을 의미한다.

##### COLD_HITS

LRU cold 리스트에서 hit가 발생한 누적 횟수를 나타낸다.

##### PREPARE_HITS

prepare 리스트에서 hit가 발생한 누적 횟수를 나타낸다.

##### FLUSH_HITS

플러시 리스트에서 hit가 발생한 누적 횟수를 나타낸다.

##### OTHER_HITS

순간적으로 어떤 리스트에도 속하지 않은 버퍼에 hit 발생한 횟수를 나타낸다. hit가 발생한 버퍼는 항상 어떤 리스트에 존재해야 하는 것은 아니다.

##### PREPARE_VICTIMS

prepare 리스트에서 교체 대상 버퍼를 찾은 누적 횟수를 나타낸다.

##### LRU_VICTIMS

LRU 리스트에서 교체 대상 버퍼를 찾은 누적 횟수를 나타낸다.

##### VICTIM_FAILS

교체 대상 버퍼 찾기에 실패한 누적 횟수를 나타낸다. 이 값은 PREPARE_AGAIN_VICTIMS

- VICTIM_SEARCH_WARP로 계산할 수 있다. PREPARE_VICTIMS + LRU_VICTIMS + VICTIM_FAILS는 버퍼 풀에서 발생한 총 교체 횟수이다.

##### PREPARE_AGAIN_VICTIMS

교체 대상 버퍼 찾기에 실패한 후 prepare 리스트에 버퍼가 삽입되기를 대기한다. 이 때 대기 중에 clean 버퍼가 삽입되어 이를 교체 대상으로 선정하게 된 횟수를 나타낸다.

##### VICTIM_SEARCH_WARP

prepare 리스트에 일정 시간 대기한 후에도 교체 대상 버퍼를 선정하지 못한 경우 다음 prepare 리스트로 넘어가서 교체 대상 버퍼를 찾는 누적 횟수를 나타낸다.

##### LRU_SEARCHS

LRU 리스트에서 교체 대상 버퍼를 검색한 누적 버퍼 개수를 나타낸다.

##### LRU_SEARCHS_AVG

교체 대상 검색시 탐색 버퍼의 평균 개수를 나타낸다.

##### LRU_TO_HOTS

LRU 리스트에서 hot영역으로 옮겨진 버퍼의 누적 개수를 나타낸다.

##### LRU_TO_COLDS

LRU 리스트에서 cold영역으로 옮겨진 버퍼의 누적 개수를 나타낸다.

##### LRU_TO_FLUSHS

LRU 리스트에서 플러시 리스트로 옮겨진 버퍼의 누적 개수를 나타낸다.

##### HOT_INSERTIONS

LRU hot 리스트에 삽입된 누적 버퍼 개수를 나타낸다.

##### COLD_INSERTIONS

LRU cold 리스트에 삽입된 누적 버퍼 개수를 나타낸다.

##### DB_SINGLE_READ_PERF

디스크 테이블에 대해 FETCH, INSERT, UPDATE 및 DELETE 수행 시, Altibase는 하나의 데이터 페이지를 데이터 파일에서 읽어서 메모리 버퍼에 저장한다. 이 값은 이런 작업 과정 중 초당 디스크에서 읽은 평균 바이트 수이다. (단위: kB/sec)

##### DB_MULTI_READ_PERF

일명 “full 스캔”이라 불리는 작업 즉, 한 디스크 테이블 전체를 스캔하는 작업 수행 시, Altibase는 여러 데이터 페이지를 동시에 디스크에서 읽어서 메모리 버퍼에 저장한다. 이 값은 이 작업 과정 중 초당 디스크에서 읽은 평균 바이트 수이다. (단위: kB/sec)

### V$CATALOG

데이타베이스에 존재하는 테이블의 구조 정보를 보여준다.

| Column name         | Type    | Description                                             |
| ------------------- | ------- | ------------------------------------------------------- |
| TABLE_OID           | BIGINT  | 테이블의 객체 식별자                                    |
| COLUMN_CNT          | INTEGER | 테이블의 칼럼 개수                                      |
| COLUMN_VAR_SLOT_CNT | INTEGER | 칼럼 정보를 저장하기 위해 사용된 Variable Slot의 개수   |
| INDEX_CNT           | INTEGER | 테이블의 인덱스 개수                                    |
| INDEX_VAR_SLOT_CNT  | INTEGER | 인덱스 정보를 저장하기 위해 사용된 Variable Slot의 개수 |

#### 칼럼 정보

##### TABLE_OID

테이블의 정보를 가지는 헤더 (Header)의 물리적인 위치를 나타낸다.

##### COLUMN_CNT

테이블의 정보를 가지는 헤더 (Header)의 물리적인 위치를 나타낸다.

##### COLUMN_VAR_SLOT_CNT

테이블의 칼럼 정보를 저장하기 위해 사용된 Variable Slot의 개수.

##### INDEX_CNT

테이블의 인덱스 개수이다.

##### INDEX_VAR_SLOT_CNT

인덱스에 대한 정보를 저장하기 위해 사용된 Variable Slot의 개수이다.

### V$DATABASE

메모리 데이터베이스에 대한 내부 정보를 보여준다.

| Column name          | Type         | Description                                           |
| -------------------- | ------------ | ----------------------------------------------------- |
| DB_NAME              | VARCHAR(128) | 데이터베이스 이름                                     |
| PRODUCT_SIGNATURE    | VARCHAR(512) | 제품 바이너리와 빌드 환경을 나타내는 제품 고유 스트링 |
| DB_SIGNATURE         | VARCHAR(512) | 고유한 데이터베이스 식별 스트링                       |
| VERSION_ID           | INTEGER      | 데이터베이스 버전                                     |
| COMPILE_BIT          | INTEGER      | 제품이 32 또는 64비트로 컴파일 되었는지 나타냄        |
| ENDIAN               | BIGINT       | Endian 정보                                           |
| LOGFILE_SIZE         | BIGINT       | 로그파일 크기                                         |
| TX_TBL_SIZE          | INTEGER      | 트랜잭션 테이블 크기                                  |
| LAST_SYSTEM_SCN      | VARCHAR(29)  | 내부 용도                                             |
| INIT_SYSTEM_SCN      | VARCHAR(29)  | 내부 용도                                             |
| DURABLE_SYSTEM_SCN   | VARCHAR(29)  | 저장된 시스템 SCN 값                                  |
| MEM_MAX_DB_SIZE      | VARCHAR(256) | 메모리 데이터베이스의 최대 크기                       |
| MEM_ALLOC_PAGE_COUNT | BIGINT       | 할당된 페이지 총 개수                                 |
| MEM_FREE_PAGE_COUNT  | BIGINT       | 사용 가능한 페이지 총 개수                            |
| MAX_ACCESS_FILE_SIZ  | VARCHAR(12)  | 데이터베이스에 생성가능한 최대 파일 크기              |

#### 칼럼 정보

##### DB_NAME

메모리 데이터베이스의 이름을 나타낸다.

##### PRODUCT_SIGNATURE

Altibase 제품이 가지는 고유한 제품 정보를 나타낸다.

##### DB_SIGNATURE

고유한 데이터베이스 식별 스트링이다.

##### VERSION_ID

Altibase 저장관리자가 유지하는 고유 버전번호를 나타낸다.

##### COMPILE_BIT

현재 생성된 데이터베이스가 32비트인지 혹은 64비트인지 표현한다.

##### ENDIAN

현재 생성된 데이터베이스의 Endian을 나타낸다.

- 0: little endian
- 1: big endian

##### LOGFILE_SIZE

현재 생성된 데이터베이스에서 사용하는 로그 파일의 크기를 바이트 단위로 나타낸다.

##### TX_TBL_SIZE

트랜잭션 테이블의 크기를 나타낸다.

##### MEM_MAX_DB_SIZE

메모리 데이터베이스 공간의 확장가능한 최대 크기를 바이트 단위로 나타낸다.

##### MEM_ALLOC_PAGE_COUNT

현재 메모리 데이터베이스에 할당된 총 페이지 개수를 나타낸다. 이는 확장가능한 최대 크기까지 고려하지 않으며, 현재 메모리 데이타베이스 공간 크기에 대해서만 고려한다. 그러므로, 현재 메모리 데이타베이스 공간의 크기는 MEM_ALLOC_PAGE_COUNT와 MEM_FREE_PAGE_COUNT의 합에 페이지 크기 (메모리 데이터베이스의 페이지 크기는 32KB)를 곱하여 계산할 수 있다.

##### MEM_FREE_PAGE_COUNT

현재 메모리 데이타베이스 공간에서 할당가능한 페이지 개수를 나타낸다. 현재 할당된 페이지는 포함되지 않는다. 이는 확장가능한 최대 크기까지 고려하지 않으며, 현재 메모리 데이타베이스 공간 크기에 대해서만 고려한다. 그러므로, 현재 메모리 데이타베이스 공간의 크기는 MEM_ALLOC_PAGE_COUNT와 MEM_FREE_PAGE_COUNT의 합에 페이지 크기 (32KB)를 곱하여 표현할 수 있다.

##### DURABLE_SYSTEM_SCN

데이터베이스 공간에 저장된 시스템 SCN의 값을 나타낸다.

### V$DATAFILES

테이블스페이스에서 사용하는 데이터 파일의 정보를 보여준다.

| Column name       | Type         | Description                     |
| ----------------- | ------------ | ------------------------------- |
| ID                | INTEGER      | 데이터 파일 식별자              |
| NAME              | VARCHAR(256) | 데이터 파일 이름                |
| SPACEID           | INTEGER      | 테이블스페이스 식별자           |
| OLDEST_LSN_LFGID  | INTEGER      | 사용하지 않음(0)                |
| OLDEST_LSN_FILENO | INTEGER      | 아래 참조                       |
| OLDEST_LSN_OFFSET | INTEGER      | 아래 참조                       |
| CREATE_LSN_LFGID  | INTEGER      | 사용하지 않음(0)                |
| CREATE_LSN_FILENO | INTEGER      | 아래 참조                       |
| CREATE_LSN_OFFSET | INTEGER      | 아래 참조                       |
| SM_VERSION        | INTEGER      | 버전 정보                       |
| NEXTSIZE          | BIGINT       | 데이터 파일 확장 시 증가할 크기 |
| MAXSIZE           | BIGINT       | 최대 크기                       |
| INITSIZE          | BIGINT       | 초기 크기                       |
| CURRSIZE          | BIGINT       | 현재 크기                       |
| AUTOEXTEND        | INTEGER      | 자동 확장 플래그                |
| IOCOUNT           | INTEGER      | 현재 진행 중인 I/O 작업의 개수  |
| OPENED            | INTEGER      | 현재 사용 중인지 여부           |
| MODIFIED          | INTEGER      | 데이터 파일 수정 여부           |
| STATE             | INTEGER      | 파일의 상태                     |
| MAX_OPEN_FD_COUNT | INTEGER      | 열 수 있는 최대 FD 개수         |
| CUR_OPEN_FD_COUNT | INTEGER      | 열린 FD 개수                    |

#### 칼럼 정보

##### ID

데이터 파일의 식별자를 나타낸다. 아이디는 파일이 생성된 순서대로 순차적으로 부여되어 같은 아이디가 중복되는 일은 없다.

##### NAME

데이터 파일의 물리적 경로와 이름을 나타낸다.

##### SPACEID

데이터 파일이 속한 테이블스페이스의 식별자를 나타낸다.

##### OLDEST_LSN_FILENO

데이터 파일에 페이지를 플러시한 마지막 체크포인트 시점에 버퍼에 올라와 수정되었던 페이지 중 가장 오래된 페이지의 LSN 값의 파일 번호 부분을 나타낸다.

##### OLDEST_LSN_OFFSET

데이터 파일에 페이지를 플러시한 마지막 체크포인트 시점에 버퍼에 올라와 수정되었던 페이지 중 가장 오래된 페이지의 LSN값의 offset부분을 나타낸다.

##### CREATE_LSN_FILENO

데이터 파일이 생성된 시점의 LSN 값의 파일 번호 부분을 나타낸다.

##### CREATE_LSN_OFFSET

데이터 파일이 생성된 시점의 LSN 값의 offset부분을 나타낸다.

##### SM_VERSION

데이터 파일을 생성한 바이너리의 버전을 나타낸다.

##### NEXTSIZE

데이터 파일의 autoextend 속성이 on인 경우, 공간 부족 시 데이터 파일은 이 크기만큼 확장된다. 표시되는 값은 페이지 개수이다 (1페이지 = 8kB).

##### MAXSIZE

데이터 파일의 autoextend 속성이 on인 경우, 공간 부족 시 데이터 파일이 확장될 수 있는 최대 크기를 나타낸다. 표시되는 값은 페이지 개수이다 (1페이지 = 8kB).

##### INITSIZE

데이터 파일이 최초에 생성된 크기를 나타낸다. 표시되는 값은 페이지 개수이다 (1페이지 = 8kB).

##### CURRSIZE

데이터 파일의 현재 크기를 나타낸다. 표시되는 값은 페이지 개수이다 (1페이지 = 8kB).

##### AUTOEXTEND

데이터 파일의 공간이 부족할 때 자동 확장될 지 여부를 나타낸다.

- 0: 자동 확장 안함.
- 1: 자동 확장

##### IOCOUNT

데이터 파일에 현재 진행 중인 I/O작업의 개수를 나타낸다. 데이터 파일에 I/O가 진행 중이 아니라면, 다음 데이터 파일이 오픈될 수 있다.

##### OPENED

데이터 파일이 현재 오픈되었는지 나타낸다.

- 0: 닫혀 있음
- 1: 열려 있음

##### MODIFIED

데이터 파일이 수정되었는지 나타낸다. 데이터 파일에 페이지를 플러시하고 동기화 (synchronization)하지 않으면 이 값이 1이 된다. 플러시 후에 데이터 파일에 동기화를 수행하면 이 값이 0이 된다.

##### STATE

데이터 파일의 상태를 나타낸다.

- 1: 오프라인 (offline)
- 2: 온라인 (online)
- 6: 백업 중
- 128: 삭제 (dropped)

##### MAX_OPEN_FD_COUNT

현재 디스크 데이터 파일에서 I/O가 발생할 때 열 수 있는 최대 FD (File Descriptor) 개수

##### CUR_OPEN_FD_COUNT

현재 디스크 데이터 파일에서 열린 FD (File Descriptor) 개수

### V$DATATYPE

Altibase에서 지원하는 데이터 타입의 정보를 보여준다.14

[14] 이 성능 뷰에 저장된 값은 ODBC SQLGettypeInfo() 함수에서 조회하는 값이다.

자세한 내용은 *ODBC Reference*을 참고한다.

| Column name        | Type        | Description                                                  |
| ------------------ | ----------- | ------------------------------------------------------------ |
| TYPE_NAME          | VARCHAR(40) | DBMS에서 지원하는 데이터 타입 이름                           |
| DATA_TYPE          | SMALLINT    | DBMS에서 지원하는 데이터 타입의 내부 정의 값                 |
| ODBC_DATA_TYPE     | SMALLINT    | 데이터 타입에 대응하는 ODBC SQL 데이타 타입 식별자           |
| COLUMN_SIZE        | INTEGER     | 해당 타입에 대한 최대 칼럼 크기.                             |
| LITERAL_PREFIX     | VARCHAR(4)  | 해당 데이터 타입의 리터럴에 대한 접두부로 인식하는 문자      |
| LITERAL_SUFFIX     | VARCHAR(4)  | 해당 데이터 타입의 리터럴에 대한 접미부로 인식하는 문자.     |
| CREATE_PARAM       | VARCHAR(20) | SQL에서 데이터 타입 정의시 괄호로 표현되는 매개변수 키워드 목록 |
| NULLABLE           | SMALLINT    | 데이터 타입의 NULL 값 허용 여부                              |
| CASE_SENSITIVE     | SMALLINT    | 대/소문자 구분 여부                                          |
| SEARCHABLE         | SMALLINT    | WHERE절에서 데이터 타입 사용 방법                            |
| UNSIGNED_ATTRIBUTE | SMALLINT    | 데이터 타입의 부호 여부                                      |
| FIXED_PREC_SCALE   | SMALLINT    | 데이터 타입이 고정형인지 나타낸다                            |
| AUTO_UNIQUE_VALUE  | SMALLINT    | 향후 확장 예정                                               |
| LOCAL_TYPE_NAME    | VARCHAR(40) | 데이터 타입에 대한 로컬화된 (자국어) 이름                    |
| MINIMUM_SCALE      | SMALLINT    | 허용가능한 최소 소수 자릿수                                  |
| MAXIMUM_SCALE      | SMALLINT    | 허용가능한 최대 소수 자릿수                                  |
| SQL_DATA_TYPE      | SMALLINT    | SQL_DESC_TYPE에서 지원하는 SQL 데이터 타입 정의 값           |
| SQL_DATETIME_SUB   | SMALLINT    | datetime 또는 interval 타입의 하위 코드                      |
| NUM_PREC_RADIX     | INTEGER     | 한 칼럼이 보유할수 있는 숫자의 최대 자리수를 계산하기 위해 필요한 비트수 |
| INTERVAL_PRECISION | SMALLINT    | DATA_TYPE이 interval인 경우에 해당 데이터 타입에 표현할 수 있는 숫자의 최대 자리수 |

#### 칼럼 정보

##### ODBC_DATA_TYPE

해당하는 데이터 타입에 대응하는 ODBC SQL 데이타 타입 식별자이다. 이에 대한 자세한 내용은 *ODBC Reference*의 부록 데이터 형을 참고한다.

##### COLUMN_SIZE

해당 타입에 대한 최대 칼럼 크기이다.

숫자형 타입의 경우 이 값은 타입 정의시에 주어진 Precision 값이다. 문자형 타입의 경우에 이 값은 타입 정의시에 주어진 길이 값이다. 날짜형 타입의 경우 이 값은 문자로 변환될 때 값을 표시하기 위해 필요한 총 문자 수이다.

##### LITERAL_PREFIX

해당 데이터 타입의 리터럴에 대한 접두부로 인식하는 문자이다. 리터럴 접두부를 적용할 수 없는 데이터 타입인 경우 이 값은 NULL이다.

##### LITERAL_SUFFIX

해당 데이터 타입의 리터럴에 대한 접미부로 인식하는 문자이다. 리터럴 접두부를 적용할 수 없는 데이터 타입인 경우 이 값은 NULL이다.

##### CREATE_PARAM

SQL에서 데이터 타입 정의시 괄호내에 표현되는 매개변수 키워드 목록으로 쉼표로 구분된다. 예를 들어 NUMBER(precision, scale) 표현되는 NUMBER 의 경우, 괄호 안의 “precision, scale”이 이에 해당된다. 목록에서 키워드는 precision와 scale이다. 매개변수가 필요 없는 데이터 타입의 경우, 이 값은 NULL이다.

##### NULLABLE

데이터 타입이 NULL 값을 허용하는지를 나타낸다.

- 1: NULL 값을 허용한다.
- 0: NULL 값을 허용하지 않는다.

##### CASE_SENSITIVE

문자형 데이터 타입의 경우, 이 데이터 타입의 데이터를 정렬할 때 대/소문자를 구분하는지 나타낸다.

- 1: 대/소문자를 구분한다.
- 0: 대/소문자를 구분하지 않는다.

##### SEARCHABLE

WHERE 절에서 이 데이터 타입을 사용하는 방법을 나타낸다.

- 0: WHERE절에서 사용될 수 없다 (SQL_PRED_NONE).
- 1: WHERE절에서 사용될 수 있으나, LIKE와 함께 사용되어야 한다 (SQL_PRED_CHAR).
- 2: WHERE절에서 LIKE를 제외한 모든 비교 연산자들과 사용될 수 있다 (SQL_PRED_BASIC).
- 3: WHERE절에서 모든 비교 연산자들과 사용될 수 있다 (SQL_SEARCHABLE).

##### UNSIGNED_ATTRIBUTE

데이터 타입의 부호 여부를 나타한다.

- 1: 해당 타입이 부호없는 (unsigned) 데이타 타입이다.
- 0: 해당 타입이 부호를 가지는 (signed) 데이타 타입이다.
- NULL: 해당 타입이 숫자형이 아니어서, 이 속성이 적용되지 않는다.

##### FIXED_PREC_SCALE

데이터 타입이 고정형인지 나타낸다. 해당 데이터 타입이 고정형 숫자 타입이고 항상 같은 정밀도 (precision)와 소수 자릿수 (scale)를 가지면 1 (SQL_TRUE), 그렇지 않은 경우 0 (SQL_FALSE)이다.

##### LOCAL_TYPE_NAME

데이터 타입에 대한 로컬화된 (자국어) 이름을 나타낸다. 로컬화된 이름이 없는 경우 NULL이다.

##### MINIMUM_SCALE

숫자형 데이터 타입의 경우, 허용가능한 최소 소수 자릿수이다. 고정 scale 타입일 경우 이 값이 존재하며, scale이 적용되지 않는 타입에 대해서는 이 값이 NULL이다.

##### MAXIMUM_SCALE

숫자형 데이터 타입의 경우, 허용가능한 최대 소수 자릿수이다. scale이 적용되지 않는 타입의 경우, 이 값은 NULL이다.

##### SQL_DATA_TYPE

ODBC의 SQL_DESC_TYPE에서 지원하는 SQL 데이터 타입이다. interval, datetime 데이터 타입을 제외한 다른 타입의 경우, ODBC_DATA_TYPE 값과 같다.

##### SQL_DATETIME_SUB

SQL_DATA_TYPE 값이 SQL_DATETIME 또는 SQL_INTERVAL인 경우 이 값은 datetime 또는 interval의 하위 코드이다. 데이터 타입이 datetime 또는 interval이 아닌 경우 이 값은 NULL이다.

##### NUM_PREC_RADIX

한 칼럼이 보유할 수 있는 최대 수를 계산하는데 필요한 비트수 또는 자릿수입니다.

##### INTERVAL_PRECISION

DATA_TYPE이 interval인 경우에 해당 데이터 타입에 표현할 수 있는 숫자의 최대 자릿수이다.

### V$DBA_2PC_PENDING

DBMS에 존재하는 분산 트랜잭션 중에서 현재 in-doubt 상태인 트랜잭션의 XID의 목록을 보여준다. 분산 트랜잭션에서 in-doubt 상태란 커밋할 준비가 된 상태에서 커밋 또는 롤백 명령을 받기 전까지의 트랜잭션 브랜치의 상태를 의미한다.

| Column name   | Type         | Description                                                  |
| ------------- | ------------ | ------------------------------------------------------------ |
| LOCAL_TRAN_ID | BIGINT       | 글로벌 트랜잭션 아이디 (GLOBAL_TX_ID)와 연계되어 있는 Altibase 내부의 트랜잭션 아이디 |
| GLOBAL_TX_ID  | VARCHAR(256) | 글로벌 트랜잭션 아이디                                       |

#### 칼럼 정보

##### LOCAL_TRAN_ID

Altibase 내부의 트랜잭션 아이디로써 글로벌 트랜잭션 아이디와 연계된다.

##### GLOBAL_TX_ID

트랜잭션 브랜치에 할당한 고유한 트랜잭션 아이디이다. 이 값은 포맷 식별자(format identifier), 글로벌 트랜잭션 식별자 (global transaction identifier) 및 브랜치 수식자(branch qualifier)를 포함한 문자열로 표시된다.

### V$DBLINK_ALTILINKER_STATUS

데이터베이스 링크를 위한 AltiLinker 프로세스의 상태 정보를 보여준다.

| Column name              | Type         | Description                                                  |
| ------------------------ | ------------ | ------------------------------------------------------------ |
| STATUS                   | INTEGER      | AltiLinker의 상태 1: AltiLinker가 정상적으로 수행 중인 상태 0: AltiLinker가 실행되어 있지 않거나 정상적인 수행이 불가능한 상태 |
| SESSION_COUNT            | INTEGER      | Altibase와 AltiLinker 프로세스 사이의 세션인 링커 세션의 개수 |
| REMOTE_SESSION_COUNT     | INTEGER      | AltiLinker 프로세스와 원격 서버들 사이의 세션의 개수         |
| JVM_MEMORY_POOL_MAX_SIZE | INTEGER      | JVM 상에서 AltiLinker를 위해 할당하는 메모리 풀의 최대 크기  |
| JVM_MEMORY_USAGE         | BIGINT       | JVM 상에서 AltiLinker 프로세스의 메모리 사용량               |
| START_TIME               | VARCHAR(128) | AltiLinker 프로세스가 시작된 일시                            |

#### 칼럼 정보

##### STATUS

AltiLinker의 상태를 나타낸다. 값이 1이면 AltiLinker가 정상적으로 수행 중인 상태이다. 그러나 값이 0이면, AltiLinker가 실행되어 있지 않거나 정상적인 수행이 불가능한 상태이다.

### V$DBLINK_DATABASE_LINK_INFO

데이터베이스에 존재하는 데이터베이스 링크 객체에 대한 정보를 보여준다.

| Column name     | Type    | Description                       |
| --------------- | ------- | --------------------------------- |
| ID              | INTEGER | 데이터베이스 링크 객체 식별자     |
| STATUS          | INTEGER | 이 데이터베이스 링크 객체의 상태  |
| REFERENCE_COUNT | INTEGER | 이 데이터베이스 링크 객체 참조 수 |

#### 칼럼 정보

##### STATUS

데이터베이스 링크 객체의 상태를 나타낸다.

- 1(CREATED): 메모리에 데이터베이스 링크 객체 생성이 완료
- 2(META): 메타 테이블에 데이터베이스 링크 객체 정보 등록
- 3(READY): 데이터베이스 링크 객체의 사용이 가능

##### REFERENCE_COUNT

이 데이터베이스 링크가 현재 참조되고 있는 횟수를 나타낸다.

### V$DBLINK_GLOBAL_TRANSACTION_INFO

현재 데이터베이스 링크를 통해 수행중인 글로벌 트랜잭션에 대한 정보를 나타낸다.

| Column name              | Type    | Description                                                |
| ------------------------ | ------- | ---------------------------------------------------------- |
| TRANSACTION_ID           | INTEGER | 현재 데이터베이스 링크를 사용하는 글로벌 트랜잭션의 식별자 |
| STATUS                   | INTEGER | 글로벌 트랜잭션의 현재 상태                                |
| SESSION_ID               | INTEGER | 글로벌 트랜잭션을 수행하고 있는 링커 데이터 세션의 ID      |
| REMOTE_TRANSACTION_COUNT | INTEGER | 글로벌 트랜잭션 내에서 현재 수행중인 원격 트랜잭션의 개수  |
| TRANSACTION_LEVEL        | INTEGER | 글로벌 트랜잭션의 실행 레벨                                |
| GLOBAL_TRANSACTION_ID    | INTEGER | 데이터베이스 링크를 사용하고 있는 글로벌 트랜잭션의 식별자 |

#### 칼럼 정보

##### STATUS

글로벌 트랜잭션의 현재 상태를 나타낸다.

- 0(NONE): 트랜잭션이 존재하지 않음
- 1(BEGIN): 트랜잭션이 시작됨
- 2(PREPARE_READY): 트랜잭션이 시작되었으나 현재 수행중인 원격 트랜잭션은 존재하지 않음
- 3(PREPARE_REQUEST): Simple transaction commit level 에서 AltiLinker 프로세스에 prepare를 요청한 상태
- 4(PREPARE_WAIT): Simple transaction commit level에서 모든 원격 트랜잭션에 대해 prepare 완료여부를 기다리는 상태
- 5(PREPARED): 모든 원격 트랜잭션의 prepare 완료
- 6(COMMIT_REQUEST): AltiLinker 프로세스로 commit 을 요청한 상태
- 7(COMMIT_WAIT): AltiLinker 프로세스로부터 commit 에 대한 응답을 기다리는 상태
- 8(COMMITTED): 트랜잭션 commit 완료
- 9(ROLLBACK_REQUEST): AltiLinker 프로세스로 rollback 을 요청한 상태
- 10(ROLLBACK_WAIT): AltiLinker 프로세스로부터 rollback 에 대한 응답을 기다리는 상태
- 11(ROLLBACKED): 트랜잭션 rollback 완료

##### TRANSACTION_LEVEL

0 ,1,2로 표시된다. 각 값에 대한 상세한 설명은 DBLINK_GLOBAL_TRANSACTION_LEVEL 프로퍼티의 내용을 참고하도록 한다.

### V$DBLINK_LINKER_CONTROL_SESSION_INFO

Altibase 서버와 AltiLinker 프로세스 사이의 제어 작업을 위해 유일하게 생성되는 링커 제어 세션의 상태 정보를 보여준다.

| Column name     | Type    | Description                              |
| --------------- | ------- | ---------------------------------------- |
| STATUS          | INTEGER | 링커 제어 세션의 상태                    |
| REFERENCE_COUNT | INTEGER | 링커 제어 세션이 현재 참조되고 있는 횟수 |

#### 칼럼 정보

##### STATUS

이 링커 제어 세션의 현재 상태를 나타낸다.

- 0(NONE): 링커 제어 세션이 존재하지 않는 상태
- 1(CREATED): 링커 제어 세션이 생성 완료된 상태
- 2(CONNECTED): AltiLinker 프로세스와 링커 제어 세션이 연결된 상태
- 3(DISCONNECTED): AltiLinker 프로세스와 링커 제어 세션의 연결이 끊어진 상태
- 4(DESTROYED): 링커 제어 세션이 제거된 상태
- 5(LOCKED): 링커 제어 세션이 잠긴 상태
- 6(UNLOCKED): 링커 제어 세션의 잠금이 풀린 상태

### V$DBLINK_LINKER_DATA_SESSION_INFO

Altibase 서버와 AltiLinker 프로세스 사이의 데이터 작업을 수행하기 위해 생성되는 링커 데이터 세션들의 상태 정보를 보여준다.

| Column name           | Type    | Description                                      |
| --------------------- | ------- | ------------------------------------------------ |
| ID                    | INTEGER | 링커 데이터 세션 식별자                          |
| STATUS                | INTEGER | 링커 데이터 세션의 상태                          |
| LOCAL_TRANSACTION_ID  | INTEGER | 현재 세션에서 수행 중인 로컬 트랜잭션의 식별자   |
| GLOBAL_TRANSACTION_ID | INTEGER | 현재 세션에서 수행 중인 글로벌 트랜잭션의 식별자 |

#### 칼럼 정보

##### STATUS

이 링커 데이터 세션의 현재 상태를 나타낸다.

- 0(NONE): 링커 데이터 세션이 존재하지 않는 상태
- 1(CREATED): 링커 데이터 세션의 생성이 완료된 상태
- 2(CONNECTED): 링커 데이터 세션이 AltiLinker 프로세스와 연결된 상태
- 3(DISCONNECTED): 링커 데이터 세션과 AltiLinker 프로세스와의 연결이 끊어진 상태
- 4(DESTROYED): 링커 데이터 세션이 제거된 상태

### V$DBLINK_LINKER_SESSION_INFO

Altibase 서버와 AltiLinker 프로세스 간에 생성되는 링커 제어 세션(Linker Control Session)과 링커 데이터 세션(Linker Data Session)들이 얼마나 존재하는지 보여준다.

| Column name  | Type       | Description                                      |
| ------------ | ---------- | ------------------------------------------------ |
| SESSION_ID   | INTEGER    | 링커 세션 식별자                                 |
| STATUS       | INTEGER    | 링커 세션의 상태                                 |
| SESSION_TYPE | VARCHAR(7) | 링커 제어 세션인지 링커 데이터 세션인지를 나타냄 |

#### 칼럼 정보

##### STATUS

이 링커 세션의 현재 상태를 나타낸다. 상태 값은 V$DBLINK_LINKER_CONTROL_SESSION_INFO 성능와 V$DBLINK_LINKER_DATA_SESSION_INFO 성능 뷰의 STATUS를 참고하도록 한다.

##### SESSION_TYPE

이 링커 세션이 링커 제어 세션인지 링커 데이터 세션인지를 나타낸다.

- CONTROL: 링커 제어 세션
- DATA: 링커 데이터 세션

### V$DBLINK_NOTIFIER_TRANSACTION_INFO

AltiLinker가 처리 중인 분산 트랜잭션의 정보를 보여준다.

| Column name           | Type        | Description                                     |
| --------------------- | ----------- | ----------------------------------------------- |
| GLOBAL_TRANSACTION_ID | INTEGER     | 데이터베이스 링크를 사용하는 트랜잭션의 식별자  |
| TRANSACTION_ID        | INTEGER     | 로컬 트랜잭션 식별자                            |
| XID                   | VARCHAR(12) | 트랜잭션 브랜치 식별자                          |
| TRANSACTION_RESULT    | VARCHAR(10) | 해당 트랜잭션을 처리한 결과(COMMIT/ROLLBACK)    |
| TARGET_INFO           | VARCHAR(40) | 데이터베이스 링크 객체가 접근할 원격서버의 이름 |

#### 칼럼 정보

##### GLOBAL_TRANSACTION_ID

데이터베이스 링크를 사용하는 글로벌 트랜잭션의 식별자이다.

##### TRANSACTION_ID

글로벌 트랜잭션을 처리할 경우에 알티베이스가 로컬 트랜잭션을 수행할 때 사용하는 내부 트랜잭션의 식별자이다.

##### XID

트랜잭션 브랜치에 할당한 고유한 트랜잭션 아이디이다. 이 값은 포맷 식별자(format identifier), 글로벌 트랜잭션 식별자 (global transaction identifier), 브랜치 수식자(branch qualifier)를 문자열로 표시한다.

##### TRANSACTION_RESULT

해당 트랜잭션을 처리한 결과를 나타낸다.

- COMMIT: 트랜잭션을 COMMIT으로 처리한 경우
- ROLLBACK: 트랜잭션을 ROLLBACK으로 처리한 경우

##### TARGET_INFO

데이터베이스 링크 객체가 접근할 원격서버의 이름을 보여준다.

### V$DBLINK_REMOTE_STATEMENT_INFO

데이터베이스 링크를 사용했을 때, 원격 서버에 파생되어 발생한 질의문 정보를 보여준다

| Column name           | Type           | Description                                                |
| --------------------- | -------------- | ---------------------------------------------------------- |
| TRANSACTION_ID        | INTEGER        | 데이터베이스 링크를 사용하고 있는 트랜잭션의 식별자        |
| REMOTE_TRANSACTION_ID | INTEGER        | 원격 서버에 발생한 트랜잭션 식별자                         |
| STATEMENT_ID          | BIGINT         | 원격 서버에 발생한 구문(statement) 식별자                  |
| QUERY                 | VARCHAR(32000) | 구문 (statement)에서 실행한 질의 내용                      |
| GLOBAL_TRANSACTION_ID | INTEGER        | 데이터베이스 링크를 사용하고 있는 글로벌 트랜잭션의 식별자 |

#### 칼럼 정보

##### REMOTE_TRANSACTION_ID

원격 서버에 발생한 트랜잭션 식별자이다. 이 식별자는 실제 원격 서버 상의 트랜잭션 식별자가 아니라, 원격 서버에 트랜잭션을 생성할 때 AltiLinker가 자체적으로 부여한 식별자이다. 이 식별자는 관리 목적으로 생성된 것이므로, 그 값 자체에 의미를 둘 필요는 없다.

##### STATEMENT_ID

원격 서버에 발생한 구문 (statement) 식별자이다. 이 식별자는 실제 원격 서버에서 생성된 구문 식별자가 아니라, 원격 서버에 문장을 생성할 때 AltiLinker가 자체적으로 부여한 식별자이다. 이 식별자는 관리 목적으로 생성된 것이므로, 그 값 자체에 의미를 둘 필요가 없다.

### V$DBLINK_REMOTE_TRANSACTION_INFO

데이터베이스 링크를 통해 원격 노드에서 수행중인 모든 원격 트랜잭션의 정보를 보여준다.

| Column name           | Type        | Description                                                |
| --------------------- | ----------- | ---------------------------------------------------------- |
| TRANSACTION_ID        | INTEGER     | 데이터베이스 링크를 사용한 트랜잭션 식별자                 |
| REMOTE_TRANSACTION_ID | INTEGER     | 원격 서버에 발생한 트랜잭션 식별자                         |
| TARGET_INFO           | VARCHAR(40) | 데이터베이스 링크 객체가 접근할 원격 서버의 이름           |
| STATUS                | INTEGER     | 이 글로벌 트랜잭션의 현재 상태                             |
| XID                   | VARCHAR(12) | 트랜잭션 브랜치 식별자                                     |
| GLOBAL_TRANSACTION_ID | INTEGER     | 데이터베이스 링크를 사용하고 있는 글로벌 트랜잭션의 식별자 |

#### 칼럼 정보

##### REMOTE_TRANSACTION_ID

원격 서버에 발생한 트랜잭션 식별자이다. 이 식별자는 실제 원격 서버에서 생성된 트랜잭션 식별자가 아니라, 원격 서버에 트랜잭션을 생성할 때 AltiLinker가 자체적으로 부여한 식별자이다. 이 식별자는 관리 목적으로 생성된 것이므로, 그 값 자체에 의미를 둘 필요가 없다.

##### STATUS

이 글로벌 트랜잭션의 현재 상태를 나타낸다.

- 0(NONE): 트랜잭션이 존재하지 않음
- 1(BEGIN): 트랜잭션이 시작됨
- 2(PREPARE_READY): 트랜잭션이 시작되었으나 현재 수행중인 원격 트랜잭션은 존재하지 않음
- 3(PREPARE_WAIT): Simple transaction commit level에서 AltiLinker 프로세스로부터 prepare 에 대한 응답을 기다리는 상태
- 4(PREPARED): prepare 완료
- 5(COMMIT_WAIT): AltiLinker 프로세스로부터 commit 에 대한 응답을 기다리는 상태
- 6(COMMITTED): 트랜잭션 commit 완료
- 7(ROLLBACK_WAIT): AltiLinker 프로세스로부터 rollback 에 대한 응답을 기다리는 상태
- 8(ROLLBACKED): 트랜잭션 rollback 완료

### V$DBMS_STATS

데이터베이스 전체의 통계 정보를 보여준다.

| Column name       | Type     | Description                                          |
| ----------------- | -------- | ---------------------------------------------------- |
| DATE              | CHAR(48) | 마지막으로 통계 정보를 수집한 일시                   |
| SAMPLE_SIZE       | DOUBLE   | 샘플의 크기                                          |
| NUM_ROW_CHANGE    | BIGINT   | 마지막 통계 정보 수집 후 행 개수의 변화량            |
| TYPE              | CHAR(1)  | 통계 대상 유형 S: 시스템 T: 테이블 I: 인덱스 C: 칼럼 |
| SREAD_TIME        | DOUBLE   | 하나의 페이지를 읽는 데 소요된 시간                  |
| MREAD_TIME        | DOUBLE   | 여러 페이지를 한 번에 읽는 데 소요된 시간            |
| MREAD_PAGE_COUNT  | BIGINT   | 여러 페이지를 한 번에 읽을 때 읽어 온 페이지 개수    |
| HASH_TIME         | DOUBLE   | 평균 해쉬 수행 시간                                  |
| COMPARE_TIME      | DOUBLE   | 평균 비교 수행 시간                                  |
| STORE_TIME        | DOUBLE   | 평균 메모리 임시 테이블 저장 수행 시간               |
| TARGET_ID         | BIGINT   | 통계 대상 테이블의 OID 또는 인덱스의 ID              |
| COLUMN_ID         | INTEGER  | 통계 대상 칼럼의 ID                                  |
| NUM_ROW           | BIGINT   | 행의 개수                                            |
| NUM_PAGE          | BIGINT   | 페이지의 개수                                        |
| NUM_DIST          | BIGINT   | 유일한 행의 개수                                     |
| NUM_NULL          | BIGINT   | NULL 개수                                            |
| AVG_LEN           | BIGINT   | 행 또는 칼럼 데이터의 평균 길이                      |
| ONE_ROW_READ_TIME | DOUBLE   | 행 하나를 읽는 평균 시간                             |
| AVG_SLOT_COUNT    | BIGINT   | Leaf 노드 당 슬롯의 평균 개수                        |
| INDEX_HEIGHT      | BIGINT   | 인덱스의 루트에서 leaf 노드까지의 깊이               |
| CLUSTERING_FACTOR | BIGINT   | 인덱스에 부합하게 데이터가 정렬되어 있는 정도        |
| MIN               | CHAR(48) | 최소 값                                              |
| MAX               | CHAR(48) | 최대 값                                              |
| META_SPACE        | BIGINT   | 데이터 관리를 위해 사용된 공간의 크기                |
| USED_SPACE        | BIGINT   | 데이터를 저장하기 위해 사용된 공간의 크기            |
| AGEABLE_SPACE     | BIGINT   | 나중에 aging 되어 재활용 가능한 공간의 크기          |
| FREE_SPACE        | BIGINT   | 사용 가능한 공간의 크기                              |

#### 칼럼 정보

##### DATE

서버가 마지막으로 통계 정보를 수집한 일시를 나타낸다.

##### SAMPLE_SIZE

통계 정보 수집을 위해 선택된 샘플의 크기를 나타낸다.

##### NUM_ROW_CHANGE

마지막 통계 정보 수집 이후 행 개수의 변경된 양을 나타낸다.

##### TYPE

통계 수집 대상의 유형을 나타낸다. 아래의 값들 중 하나가 표시된다.

S: 시스템

T: 테이블

I: 인덱스

C: 칼럼

##### SREAD_TIME

하나의 페이지를 읽는 데 소요된 평균 시간을 나타낸다.

##### MREAD_TIME

여러 페이지를 한 번에 읽는 데 소요된 평균 시간을 나타낸다.

##### MREAD_PAGE_COUNT

여러 페이지를 한 번에 읽을 때 읽어 오도록 설정된 페이지의 개수를 나타낸다.

##### HASH_TIME

해쉬 수행에 소요된 평균 시간을 나타낸다.

##### COMPARE_TIME

비교 수행에 소요된 평균 시간을 나타낸다.

##### STORE_TIME

메모리 임시 테이블에 저장하는 데 소요된 평균 시간을 나타낸다.

##### TARGET_ID

통계 수집의 대상이 된 테이블의 OID 또는 인덱스의 ID 나타낸다.

##### COLUMN_ID

통계 수집의 대상이 된 칼럼의 ID를 나타낸다.

##### NUM_ROW

통계 수집 대상(테이블 또는 인덱스)의 행의 개수를 나타낸다.

##### NUM_PAGE

통계 수집 대상(테이블 또는 인덱스)의 페이지 개수를 나타낸다.

##### NUM_DIST

인덱스 또는 칼럼에서 중복되지 않은 유일한 값의 개수를 나타낸다.

##### NUM_NULL

칼럼에서 NULL의 개수를 나타낸다.

##### AVG_LEN

행 또는 칼럼의 평균 길이를 나타낸다.

##### ONE_ROW_READ_TIME

행 하나를 읽는 데 소요된 평균 시간을 나타낸다.

##### AVG_SLOT_COUNT

Leaf 노드 당 슬롯의 평균 개수를 나타낸다.

##### INDEX_HEIGHT

인덱스의 루트에서 leaf 노드까지의 깊이를 나타낸다.

##### CLUSTERING_FACTOR

인덱스에 부합하게 데이터가 정렬되어 있는 정도를 나타낸다.

##### MIN

인덱스 또는 칼럼의 최소 값을 나타낸다.

##### MAX

인덱스 또는 칼럼의 최대 값을 나타낸다.

##### META_SPACE

데이터 관리를 위해 사용된 공간의 크기를 나타낸다.

##### USED_SPACE

데이터를 저장하기 위해 사용된 공간의 크기를 나타낸다.

##### AGEABLE_SPACE

나중에 aging 되어 재활용할 수 있는 공간의 크기를 나타낸다.

##### FREE_SPACE

테이블 또는 인덱스에 할당된 영역 중에서 사용 가능한 공간의 크기를 나타낸다.

### V$DB_FREEPAGELISTS

데이터베이스에서 사용가능한 페이지 리스트 즉, free 페이지들의 정보를 보여준다.

| Column name        | Type    | Description                                      |
| ------------------ | ------- | ------------------------------------------------ |
| SPACE_ID           | INTEGER | 사용가능한 페이지들이 속한 테이블스페이스 식별자 |
| RESOURCE_GROUP_ID  | INTEGER | 자원 그룹 식별자                                 |
| FIRST_FREE_PAGE_ID | INTEGER | 리스트 내에서 첫번째 사용가능한 페이지 식별자    |
| FREE_PAGE_COUNT    | BIGINT  | 리스트 내의 사용가능한 페이지 개수               |

#### 칼럼 정보

##### RESOURCE_GROUP_ID

다중화된 리스트들을 식별하기 위한 고유 번호이다.

##### FIRST_FREE_PAGE_ID

해당 리스트의 사용가능한 첫 번째 페이지 식별자이다.

##### FREE_PAGE_COUNT

해당 리스트 내에서 사용가능한 페이지 개수이다.

### V$DB_PROTOCOL

서버로 유입되는 모든 패킷들의 Altibase 통신 프로토콜 정보를 보여준다.

| Column name | Type        | Description                        |
| ----------- | ----------- | ---------------------------------- |
| OP_NAME     | VARCHAR(50) | 프로토콜 이름                      |
| OP_ID       | INTEGER     | 프로토콜의 고유 식별자             |
| COUNT       | BIGINT      | 이 프로토콜로 유입된 패킷의 누적치 |

### V$DIRECT_PATH_INSERT

Direct-path 업로드 관련 통계 정보를 보여준다.

| Column name                  | Type   | Description                                                  |
| ---------------------------- | ------ | ------------------------------------------------------------ |
| COMMIT_TX_COUNT              | BIGINT | Direct-path 옵션을 사용하여 커밋에 성공한 트랜잭션의 총 개수 |
| ABORT_TX_COUNT               | BIGINT | Direct-path 옵션을 사용하여 데이터 업로드 중에 철회한 트랜잭션의 총 개수 |
| INSERT_ROW_COUNT             | BIGINT | iLoader에서 direct-path 옵션을 사용하여 삽입한 행의 총 개수  |
| ALLOC_BUFFER_PAGE_TRY_COUNT  | BIGINT | 페이지 할당 요청 총 횟수                                     |
| ALLOC_BUFFER_PAGE_FAIL_COUNT | BIGINT | 페이지 할당 요청이 실패한 총 횟수                            |

#### 칼럼 정보

##### COMMIT_TX_COUNT

이 값은 iLoader에서 direct-path 옵션을 사용하여 커밋한 트랜잭션의 총 개수로, 누적된다.

##### ABORT_TX_COUNT

이 값은 direct-path 옵션을 사용하여 데이터 업로드 중에 오류로 인해서 롤백된 트랜잭션의 총 개수로, 누적된다.

##### INSERT_ROW_COUNT

iLoader에서 direct-path 옵션을 사용하여 삽입한 행의 총 개수로, 누적된다.

##### ALLOC_BUFFER_PAGE_TRY_COUNT

이 값은 direct-path 옵션을 사용한 데이터 업로드를 위해 페이지 할당이 요청된 총 횟수로, 누적된다.

##### ALLOC_BUFFER_PAGE_FAIL_COUNT

이 값은 direct-path 옵션을 사용한 데이터 업로드를 위해 페이지 할당이 요청되었으나 메모리 부족 등의 이유로 인해 실패한 총 횟수로, 누적된다.

### V$DISKTBL_INFO

디스크 테이블의 정보를 보여준다.

| Column name         | Type     | Description                                          |
| ------------------- | -------- | ---------------------------------------------------- |
| TABLESPACE_ID       | SMALLINT | 테이블스페이스 식별자                                |
| TABLE_OID           | BIGINT   | 테이블 객체 식별자                                   |
| DISK_TOTAL_PAGE_CNT | BIGINT   | 테이블이 가지고 있는 전체 페이지 개수                |
| DISK_PAGE_CNT       | BIGINT   | 테이블에서 데이터를 갖고 있는 페이지 개수            |
| SEG_PID             | INTEGER  | 테이블 세그먼트의 페이지 식별자                      |
| META_PAGE           | INTEGER  | Deprecated                                           |
| FST_EXTRID          | BIGINT   | 테이블의 첫번째 익스텐트의 RID                       |
| LST_EXTRID          | BIGINT   | 테이블의 마지막 익스텐트의 RID                       |
| PCTFREE             | SMALLINT | SYS_TABLES_의 설명 참조                              |
| PCTUSED             | SMALLINT | SYS_TABLES_의 설명 참조                              |
| INITRANS            | SMALLINT | 한 페이지 내에서 동시 처리 가능한 초기 트랜잭션 개수 |
| MAXTRANS            | SMALLINT | 한 페이지 내에서 동시 처리 가능한 최대 트랜잭션 개수 |
| INITEXTENTS         | INTEGER  | 테이블 생성시 초기 익스텐트 개수                     |
| NEXTEXTENTS         | INTEGER  | 테이블 확장시 할당할 익스텐트 개수                   |
| MINEXTENTS          | INTEGER  | 테이블의 최소 익스텐트 개수                          |
| MAXEXTENTS          | INTEGER  | 테이블의 최대 익스텐트 개수                          |
| COMPRESSED_LOGGING  | INTEGER  | 테이블을 위한 로그 압축 여부                         |
| IS_CONSISTENT       | INTEGER  | 테이블의 일관성 여부                                 |

테이블 이름을 포함하여 보려면 다음과 같이 메타 테이블과 조인하여 질의를 하여야 한다.

```
SELECT A.TABLE_NAME,
	B.DISK_PAGE_CNT,
	B.PCTFREE,
 	B.PCTUSED
FROM SYSTEM_.SYS_TABLES_ A, V$DISKTBL_INFO B 
WHERE A.TABLE_OID = B.TABLE_OID;
```

#### 칼럼 정보

##### PCTFREE

SYS_TABLES_ 설명의 해당하는 칼럼 정보를 참조한다.

##### PCTUSED

SYS_TABLES_ 설명의 해당하는 칼럼 정보를 참조한다.

##### INITRANS

하나의 테이블 페이지 내에서 동시에 처리할 수 있는 트랜잭션의 초기 개수를 나타낸다.

##### MAXTRANS

하나의 테이블 페이지 내에서 동시에 처리할 수 있는 트랜잭션의 최대 개수를 나타낸다.

##### INITEXTENTS

테이블 세그먼트 생성시 초기 익스텐트 개수를 나타낸다.

##### NEXTEXTENTS

테이블 세그먼트 확장시 할당할 익스텐트 개수를 나타낸다.

##### MINEXTENTS

테이블 세그먼트의 최소 익스텐트 개수를 나타낸다.

##### MAXEXTENTS

테이블 세그먼트의 최대 익스텐트 개수를 나타낸다.

### V$DISK_BTREE_HEADER

디스크 BTREE 인덱스의 헤더 정보를 보여준다.

| Column name                | Type      | Description                                                  |
| -------------------------- | --------- | ------------------------------------------------------------ |
| INDEX_NAME                 | CHAR(128) | 인덱스 이름                                                  |
| INDEX_ID                   | INTEGER   | 인덱스 식별자                                                |
| INDEX_TBS_ID               | INTEGER   | 인덱스가 저장되어 있는 테이블스페이스 식별자                 |
| TABLE_TBS_ID               | INTEGER   | 테이블이 저장되어 있는 테이블스페이스 식별자                 |
| IS_UNIQUE                  | CHAR(1)   | 유일 키 인덱스인지 여부                                      |
| COLLENINFO_LIST            | CHAR(64)  | 인덱스 값들의 사이즈 목록                                    |
| IS_CONSISTENT              | CHAR(1)   | 인덱스의 일관성 여부                                         |
| IS_CREATED_WITH_LOGGING    | CHAR(1)   | 인덱스 생성시 LOGGING 옵션 지정 여부                         |
| IS_CREATED_WITH_FORCE      | CHAR(1)   | 인덱스 생성시 NOLOGGING FORCE또는 NOLOGGING NOFORCE 옵션 지정 여부 |
| COMPLETION_LSN_LFG_ID      | INTEGER   | 사용하지 않음(0)                                             |
| COMPLETION_LSN_FILE_NO     | INTEGER   | 인덱스 생성 시점의 로그 파일 번호                            |
| COMPLETION_LSN_FILE_OFFSET | INTEGER   | 인덱스 생성 시점의 로그 파일 오프셋                          |
| INIT_TRANS                 | SMALLINT  | 하나의 인덱스 노드에서 동시 처리 가능한 초기 트랜잭션 개수   |
| MAX_TRANS                  | SMALLINT  | 하나의 인덱스 노드에서 동시 처리 가능한 최대 트랜잭션 개수   |
| FREE_NODE_HEAD             | INTEGER   | 프리 노드의 첫번째 페이지의 ID                               |
| FREE_NODE_CNT              | BIGINT    | 프리 노드 리스트 내의 페이지 개수                            |
| INITEXTENTS                | INTEGER   | 인덱스 생성시 초기 익스텐트 개수                             |
| NEXTEXTENTS                | INTEGER   | 인덱스 사이즈 확장시 할당할 익스텐트 개수                    |
| MINEXTENTS                 | INTEGER   | 인덱스 세그먼트의 최소 익스텐트 개수                         |
| MAXEXTENTS                 | INTEGER   | 인덱스 세그먼트의 최대 익스텐트 개수                         |

#### 칼럼 정보

##### INDEX_NAME

인덱스의 이름이다.

##### INDEX_ID

해당 인덱스가 갖는 시스템 내에서 고유한 식별자이다.

##### INDEX_TBS_ID

인덱스가 저장되어 있는 테이블스페이스 식별자이다.

##### TABLE_TBS_ID

해당 인덱스가 기반하고 있는 테이블이 저장되어 있는 테이블스페이스 식별자이다.

##### IS_UNIQUE

유일키 인덱스인지 여부를 나타낸다. 유일키 인덱스는 ‘T’, 중복키 인덱스의 경우는 ‘F’이다.

##### COLLENINFO_LIST

인덱스를 구성하는 값들의 사이즈 리스트이다. 이 리스트는 쉼표로 구분된 스트링으로 표현된다. 가변 길이 칼럼에 해당하는 사이즈는 ‘?’로 표시된다. 인덱스 키의 크기는 이 리스트에 기반하여 추정 가능하다.

```
iSQL> CREATE TABLE D3(I1 SMALLINT, I2 INTEGER, I3 VARCHAR(10), I4 DATE) TABLESPACE SYS_TBS_DISK_DATA;
Create success.
iSQL> CREATE INDEX D3X ON D3(I4,I3,I2,I1);
Create success.
iSQL> SELECT COLLENINFO_LIST FROM V$DISK_BTREE_HEADER WHERE INDEX_NAME='D3X';
COLLENINFO_LIST
--------------------------------------------------------------------
8,?,4,2
1 row selected.
```

##### IS_CONSISTENT

인덱스의 일관성 여부를 나타낸다. 일반적인 경우에는 ‘T’를 가지며, 인덱스가 비정상적으로 구성되어 있는 경우는 ‘F’를 갖는다. NOLOGGING이나 NOFORCE를 이용하여 인덱스를 생성한 경우에는 ‘F’를 가질 수 있다.

##### IS_CREATED_WITH_LOGGING

인덱스 생성 시 LOGGING옵션이 지정되었는지 여부를 나타낸다.

##### IS_CREATED_WITH_FORCE

인덱스 생성 시 강제적 디스크 저장 옵션 (NOLOGGING FORCE 또는 NOLOGGING NOFORCE옵션) 지정 여부를 나타낸다.

##### COMPLETION_LSN_FILE_NO

인덱스가 생성된 시점에서의 로그 파일 번호를 나타낸다.

##### COMPLETION_LSN_FILE_OFFSET

인덱스가 생성된 시점에서의 로그 파일 오프셋 (Offset)을 나타낸다.

##### INIT_TRANS

삽입, 갱신 또는 삭제를 하기 위해 하나의 인덱스 노드(페이지)에 동시에 접근할 수 있는 트랜잭션의 초기 개수를 나타낸다.

##### MAX_TRANS

삽입, 갱신 또는 삭제를 하기 위해 하나의 인덱스 노드(페이지)에 동시에 접근할 수 있는 트랜잭션의 최대 개수를 나타낸다.

##### FREE_NODE_HEAD

FREE_NODE_HEAD는 인덱스 내 FREE NODE들의 첫번째 페이지를 나타낸다. FREE NODE는 노드 내의 모든 키에 삭제 마크가 설정되어 있는 상태의 노드이다.

##### FREE_NODE_CNT

인덱스 내 FREE NODE의 전체 개수이다.

##### INITEXTENTS

인덱스 세그먼트 생성시 초기 익스텐트 개수이다.

##### NEXTEXTENTS

인덱스 세그먼트 확장시 할당할 익스텐트 개수이다.

##### MINEXTENTS

인덱스 세그먼트의 최소 익스텐트 개수이다.

##### MAXEXTENTS

인덱스 세그먼트의 최대 익스텐트 개수이다.

### V$DISK_TEMP_INFO

전체 디스크 임시 테이블이 사용한 메모리의 사용 정보를 보여준다.

| Column name | Type     | Description          |
| ----------- | -------- | -------------------- |
| NAME        | CHAR(32) | 메모리의 최소값 이름 |
| VALUE       | CHAR(32) | 메모리 최소값        |
| UNIT        | CHAR(32) | 단위                 |

#### 칼럼 정보

##### VALUE

서버가 시작한 이후부터 현재까지 동작한 디스크 임시 테이블을 메모리에서 정렬하기 위하여 필요한 메모리의 최솟값을 나타낸다.

### V$DISK_TEMP_STAT

현재 사용중인 각각의 디스크 임시 테이블이 메모리를 사용하는 정보를 보여준다. 이 정보는 [TEMP_STATS_WATCH_TIME](https://github.com/haeinnmin/Documents/blob/master/Manuals/Altibase_7.2/kor/General Reference 3.md#temp_stats_watch_time) 프로퍼티에 설정된 값 이상일 때 통계 정보가 수집된다.

| Column name      | Type    | Description                               |
| ---------------- | ------- | ----------------------------------------- |
| TBS_ID           | INTEGER | 테이블스페이스 식별자                     |
| TRANSACTION_ID   | INTEGER | 트랜잭션 식별자                           |
| CONSUME_TIME     | INTEGER | 디스크 임시 테이블의 수행 시간            |
| READ_COUNT       | BIGINT  | 데이터를 읽어오는 IO가 발생한 횟수        |
| WRITE_COUNT      | BIGINT  | 데이터를 저장하는 IO가 발생한 횟수        |
| WRITE_PAGE_COUNT | BIGINT  | 페이지가 디스크로 저장된 총 개수          |
| ALLOC_WAIT_COUNT | BIGINT  | 메모리 공간 할당을 위해 대기한 총 횟수    |
| WRITE_WAIT_COUNT | BIGINT  | 디스크로 저장하기 위해 대기한 총 횟수     |
| QUEUE_WAIT_COUNT | BIGINT  | 큐에 입력되기를 기다리는 횟수             |
| WORK_AREA_SIZE   | BIGINT  | 디스크 임시 테이블이 사용하는 메모리 크기 |
| DISK_USAGE       | BIGINT  | 디스크에 저장된 데이터 공간의 크기        |

#### 칼럼 정보

##### TBS_ID

디스크 임시 테이블을 사용하는 테이블스페이스 식별자이다.

##### TRANSACTION_ID

디스크 임시 테이블을 사용하는 트랜잭션의 식별자이다.

##### CONSUME_TIME

디스크 임시 테이블이 [TEMP_STATS_WATCH_TIME](https://github.com/haeinnmin/Documents/blob/master/Manuals/Altibase_7.2/kor/General Reference 3.md#temp_stats_watch_time) 프로퍼티에 설정된 시간을 초과하여 수행된 경우, 수행되는 시간을 보여준다.

##### READ_COUNT

디스크 상에 있는 데이터를 읽어오기 위해 READ IO가 발생한 횟수

##### WRITE_COUNT

디스크 상에 데이터를 저장하기 위해 WRITE IO가 발생한 횟수

##### WRITE_PAGE_COUNT

디스크 임시 테이블이 디스크로 저장되는 페이지의 총 개수

##### ALLOC_WAIT_COUNT

해쉬(hash) 정렬을 하기 위해 메모리의 공간 할당을 대기하는 횟수

##### WRITE_WAIT_COUNT

디스크에 데이터를 저장하기 위해 대기하는 횟수

##### QUEUE_WAIT_COUNT

디스크 상에 데이터를 저장하기 위해 큐에 입력되기까지 대기하는 횟수

##### WORK_AREA_SIZE

해쉬(hash) 정렬을 하기 위해 메모리에서 사용된 공간

##### DISK_USAGE

디스크 임시 테이블이 디스크로 저장된 공간의 크기

### V$DISK_UNDO_USAGE

디스크상에서 현재 사용중인 언두 테이블스페이스의 양에 대한 정보를 보여준다.

| Column name         | Type   | Description                                         |
| ------------------- | ------ | --------------------------------------------------- |
| TX_EXT_CNT          | BIGINT | 트랜잭션 세그먼트용 익스텐트의 개수                 |
| USED_EXT_CNT        | BIGINT | 언두 세그먼트에서 현재 사용중인 익스텐트의 개수     |
| UNSTEALABLE_EXT_CNT | BIGINT | 다른 언두 세그먼트가 가져갈 수 없는 익스텐트의 개수 |
| REUSABLE_EXT_CNT    | BIGINT | 재사용 가능한 익스텐트의 개수                       |
| TOTAL_EXT_CNT       | BIGINT | 언두 테이블스페이스의 총 익스텐트 개수              |

#### 칼럼 정보

##### TX_EXT_CNT

모든 트랜잭션 세그먼트의 익스텐트 개수이다. 이 익스텐트들은 언두 세그먼트용으로는 사용되지 않는다.

##### USED_EXT_CNT

언두 세그먼트에서 현재 사용중인 익스텐트의 개수이다. 현재 사용중인 익스텐트들은 후속 작업에서 재사용되지 않는다.

##### REUSABLE_EXT_CNT

더 이상 필요하지 않은 언두 레코드만 가지고 있어 재사용이 가능한 익스텐트의 개수이다.

### V$DR_CONNECTION_INFO

DR 환경에 현재 참여하고 있는 서버들의 정보를 보여준다.

| Column name | Type        | Description                  |
| ----------- | ----------- | ---------------------------- |
| SERVER_NAME | VARCHAR(40) | 서버 이름                    |
| SERVER_IP   | VARCHAR(64) | 서버의 IP 주소               |
| SERVER_PORT | INTEGER     | 서버 청취자의 청취 포트 번호 |

#### 칼럼 정보

##### SERVER_NAME

DR 환경을 구성하는 서버에 주어진 이름이다.

##### SERVER_IP

DR 환경을 구성하는 서버의 IP 주소이다.

##### SERVER_PORT

서버의 청취자가 청취하는 포트 번호이다.

### V$DR_GAP

DR 환경에 현재 참여하고 있는 서버들 간의 동기화 격차를 보여준다.

| Column name  | Type        | Description                                                  |
| ------------ | ----------- | ------------------------------------------------------------ |
| SERVER_NAME  | VARCHAR(40) | 서버 이름                                                    |
| CURRENT_SN   | BIGINT      | Active 서버: 현재 전송중인 로그 레코드의 식별 번호. Standby 서버: 현재 적용중인 로그 레코드의 식별 번호. |
| SYNCED_SN    | BIGINT      | Active 서버 : 항상 0. 의미 없는 값. Standby 서버에서 마지막으로 전송받은 로그 레코드의 식별 번호 |
| SN_GAP       | BIGINT      | Active 서버: 항상 0. 의미 없는 값. Standby 서버: 대응하는 Active 서버의 CURRENT_SN과 해당 Standby 서버의 SYNCED_SN의 차이. |
| APPLY_SN_GAP | BIGINT      | Active 서버 : 항상 0. 의미 없는 값. Standby 서버 : SYNCED_SN과 CURRENT_SN 의 차이. |

#### 칼럼 정보

##### SERVER_NAME

DR 환경을 구성하는 서버의 이름이다.

##### CURRENT_SN

Active 서버에서는 현재 전송중인 로그 레코드의 식별 번호가 표시된다.

Standby 서버에서는 현재 데이터베이스에 적용중인 로그 레코드의 식별 번호가 표시된다.

##### SYNCED_SN

Active 서버에서는 항상 0이 표시된다.

Standby 서버에서는 마지막으로 전송받은 로그 레코드의 식별 번호가 표시된다.

##### SN_GAP

Active 서버에서는 항상 0이 표시된다.

Standby 서버에서는 현재 Active 서버의 CURRENT_SN과 해당 Standby 서버의 SYNCED_SN의 차이가 표시된다.

##### APPLY_SN_GAP

Active 서버에서는 항상 0이 표시된다.

Standby 서버에서는 SYNCED_SN과 CURRENT_SN의 차이가 표시된다.

### V$DR_SERVERS

DR 환경을 구성하는 서버들의 정보를 보여준다.

| Column name | Type        | Description                  |
| ----------- | ----------- | ---------------------------- |
| SERVER_NAME | VARCHAR(40) | 서버 이름                    |
| SERVER_IP   | VARCHAR(64) | 서버의 IP 주소               |
| SERVER_PORT | INTEGER     | 서버 청취자의 청취 포트 번호 |

#### 칼럼 정보

##### SERVER_NAME

DR 환경을 구성하는 서버에 주어진 이름이다.

##### SERVER_IP

DR 환경을 구성하는 서버의 IP 주소이다.

##### SERVER_PORT

서버의 청취자가 청취하는 포트 번호이다.

### V$DR_STATUS

DR 환경에 참여하고 있는 서버들의 현재 상태를 보여준다.

| Column name    | Type        | Description                 |
| -------------- | ----------- | --------------------------- |
| SERVER_NAME    | VARCHAR(40) | 서버 이름                   |
| CURRENT_MODE   | VARCHAR(7)  | 동기화 모드                 |
| SERVER_ROLE    | VARCHAR(7)  | 서버의 역할                 |
| SERVER_MODE    | VARCHAR(7)  | 사용자가 설정한 동기화 모드 |
| SERVER_STATUS  | VARCHAR(8)  | 서버 상태                   |
| FAILOVER_SN    | BIGINT      | Fail-Over 시점의 SN         |
| FAILOVER_COUNT | BIGINT      | Fail-Over 횟수              |

#### 칼럼 정보

##### SERVER_NAME

DR 환경을 구성하는 서버의 이름이다.

##### CURRENT_MODE

현재 동작중인 동기화 모드로, async 또는 sync로 표시된다.

모든 Standby 서버들은 Active 서버의 동기화 모드를 그대로 따른다.

##### SERVER_ROLE

서버의 역할을 나타낸다. active 또는 standby로 표시된다.

##### SERVER_MODE

사용자가 설정한 동기화 모드로, async 또는 sync로 표시된다.

##### SERVER_STATUS

현재 서버의 동작 상태를 나타낸다. run, stop, 또는 Failure Server Repair로 표시된다.

##### FAILOVER_SN

Fail-Over가 발생한 시점의 SN이다.

##### FAILOVER_COUNT

Fail-Over가 발생한 누적 횟수이다.

### V$EVENT_NAME

Altibase 서버에서 대기하고 있는 다양한 대기 이벤트들의 정보를 보여준다.

| Column name   | Type         | Description        |
| ------------- | ------------ | ------------------ |
| EVENT_ID      | INTEGER      | 대기 이벤트 식별자 |
| NAME          | VARCHAR(128) | 대기 이벤트의 이름 |
| WAIT_CLASS_ID | INTEGER      | 대기 클래스 식별자 |
| WAIT_CLASS    | VARCHAR(128) | 대기 클래스의 이름 |

#### 칼럼 정보

##### EVENT_ID

대기하고 있는 이벤트의 식별자이다.

##### NAME

대기하고 있는 이벤트의 이름이다. 다음 표는 식별자, 이름 및 그에 대한 설명을 보여준다.

| EVENT_ID | 이름                                                | 설명                                                         |
| -------- | --------------------------------------------------- | ------------------------------------------------------------ |
| 0        | latch: buffer busy waits                            | 다른 세션이 변경하고 있는 블록에 접근하기 위한 대기          |
| 1        | latch: drdb B-tree index SMO                        | B-tree 인덱스의 SMO (Structure Modification Operation)를 수행하는 세션에 의해 발생하는 대기 |
| 2        | latch: drdb B-tree index SMO by other session       | 다른 세션에 의해 수행되는 B-tree 인덱스의 SMO 연산이 완료될 때까지 대기 |
| 3        | latch: drdb R-tree index SMO                        | R-tree 인덱스의 SMO 연산을 하고 있는 세션에 의해 발생하는 대기 |
| 4        | db file multi page read                             | 다중 페이지 읽기 요청이 완료되기를 대기하는 세션에 의해 발생 |
| 5        | db file single page read                            | 단일 페이지 읽기 요청이 완료되기를 대기하는 세션에 의해 발생 |
| 6        | db file single page write                           | LRU flush를 수행하기 전에 free BCB가 확보될 때까지 대기      |
| 7        | enq: TX – row lock contention, data row             | 갱신을 위해 로우(row)에 잠금을 하기 위한 대기                |
| 8        | enq: TX – allocate TXSEG entry                      | 트랜잭션 세그먼트 엔트리를 할당하기 위한 대기                |
| 9        | latch free: drdb file i/o                           | 디스크 파일에 read/write I/O를 수행하기 위해서 파일 래치를 획득하기를 대기 |
| 10       | latch free: drdb tbs list                           | 다른 쓰레드에 의해 사용되고 있는 테이블스페이스의 해쉬 래치를 얻기 위해 대기 |
| 11       | latch free: drdb tbs creation                       | 테이블스페이스 생성시 파일을 생성 하려는 세션에 의해 발생하는 대기 |
| 12       | latch free: disk page list entry                    | 다른 쓰레드에 의해 사용되고 있는 디스크 페이지 리스트 엔트리의 래치를 획득하기를 대기 |
| 13       | latch free: drdb transaction segment freelist       | 트랜잭션 세그먼트 프리 리스트에 대한 대기                    |
| 14       | latch free: drdb LRU list                           | 버퍼 풀의 LRU 리스트들에 대한 대기                           |
| 15       | latch free: drdb prepare list                       | 버퍼 풀의 prepare 리스트들에 대한 대기                       |
| 16       | latch free: drdb prepare list wait                  | 버퍼 풀의 prepare 리스트에 BCB가 추가될 때까지 대기          |
| 17       | latch free: drdb flush list                         | 버퍼 풀의 flush 리스트들에 대한 대기                         |
| 18       | latch free: drdb checkpoint list                    | 버퍼 풀의 checkpoint 리스트들에 대한 대기                    |
| 19       | latch free: drdb buffer flusher min recovery LSN    | 버퍼 풀 flusher의 Recovery LSN 동시성 제어를 위한 래치에 대기 |
| 20       | latch free: drdb buffer flush manager req job       | 버퍼 풀의 플러시 작업의 동시성 제어를 위한 래치에 대기       |
| 21       | latch free: drdb buffer bcb mutex                   | 버퍼 풀의 BCB 동시성 제어를 위한 래치에 대기                 |
| 22       | latch free: drdb buffer bcb read io mutex           | 버퍼 풀의 BCB로 페이지를 적재하기 위한 래치에 대기           |
| 23       | latch free: drdb buffer buffer manager expand mutex | 버퍼 풀의 확장에 대한 대기                                   |
| 24       | latch free: drdb buffer hash mutex                  | 버퍼 풀의 해쉬에 대한 대기                                   |
| 25       | latch free: plan cache LRU List mutex               | 리스트에 plan을 추가, 이동 또는 제거시, Plan cache내 LRU 리스트의 래치를 획득하기 위한 대기 |
| 26       | latch free: statement list mutex                    | 리스트에 statement를 추가, 이동 또는 삭제시, Statement 리스트의 래치를 획득하기 위한 대기 |
| 27       | latch free: others                                  | 다른 쓰레드에 의해 사용되고 있는 위에서 언급되지 않은 모든 래치에 대해서 획득하기를 대기 |
| 28       | replication before commit                           | EAGER 모드에서, COMMIT 이전의 구문들에 대응하는 모든 XLog들을 원격 서버에서 재현할 때까지 로컬 서버가 트랜잭션 커밋을 대기 (*Replication Manual*의 EAGER 모드 설명 참조) |
| 29       | replication after commit                            | EAGER 모드에서, COMMIT 구문에 대응하는 XLog를 원격 서버에 송신할 때까지 로컬 서버가 트랜잭션 커밋을 대기 (*Replication Manual*의 EAGER 모드 설명 참조) |
| 30       | no wait event                                       | 대기 이벤트가 존재하지 않음                                  |

##### WAIT_CLASS_ID

대기 이벤트의 클래스 식별자이다. 클래스 식별자에 대한 자세한 정보는 V$WAIT_CLASS_NAME를 참조하기 바란다.

##### WAIT_CLASS

대기 이벤트는 상위 개념의 대기 클래스로 그룹화된다. 대기 클래스에 대한 자세한 정보는 V$WAIT_CLASS_NAME를 참조하기 바란다.

### V$EXTPROC_AGENT

외부 프로시저 실행을 위해 생성된 에이전트 프로세스(agent process)의 정보를 보여준다.

| Column name | Type        | Description                                            |
| ----------- | ----------- | ------------------------------------------------------ |
| SID         | INTEGER     | 에이전트 프로세스를 생성한 세션의 식별자               |
| PID         | INTEGER     | 에이전트 프로세스의 pid                                |
| SOCK_FILE   | VARCHAR(64) | 프로세스 간 통신을 위한 소켓의 경로                    |
| CREATED     | INTEGER     | 에이전트 프로세스가 생성된 일시                        |
| LAST_SEND   | INTEGER     | 에이전트 프로세스가 마지막으로 결과를 반환한 일시      |
| LAST_RECV   | INTEGER     | 에이전트 프로세스가 마지막으로 호출 메시지를 받은 일시 |
| STATE       | VARCHAR(11) | 에이전트 프로세스의 상태                               |

#### 칼럼 정보

##### SID

에이전트 프로세스를 생성한 세션의 식별자를 나타낸다. 에이전트 프로세스는 세션에 종속적이다.

##### PID

에이전트 프로세스의 프로세스 ID를 나타낸다.

##### SOCK_FILE

프로세스 간의 통신에 사용되는 소켓의 경로를 나타낸다.

##### CREATED

에이전트 프로세스가 생성된 일시를 나타낸다.

##### LAST_SEND

에이전트 프로세스가 외부 프로시저를 호출한 서버 세션으로 가장 최근에 결과를 반환한 일시를 나타낸다.

##### LAST_RECV

에이전트 프로세스가 서버 세션으로부터 가장 최근에 호출 메시지를 받은 일시를 나타낸다.

##### LAST_RECV

에이전트 프로세스의 상태를 나타낸다. 아래의 값 중 하나로 표시된다.

- INITIALIZED : 최초로 생성되어 호출을 기다림
- RUNNING : 외부 프로시저(External Procedure) 실행 중
- STOPPED : 외부 프로시저(External Procedure) 실행 완료
- FAILED : 비정상 종료 됨. 에이전트 프로세스가 이미 종료되었을 수도 있음

### V$FILESTAT

Altibase 구동 이후 각 디스크에 있는 데이터 파일별 I/O 통계 정보를 보여준다. 통계 정보를 통해 핫스팟(hotspot) 데이터 파일을 알 수 있다.

| Column name    | Type    | Description                                        |
| -------------- | ------- | -------------------------------------------------- |
| SPACEID        | INTEGER | 테이블스페이스 식별자                              |
| FILEID         | INTEGER | 데이터 파일 식별자                                 |
| PHYRDS         | BIGINT  | 물리적 Read I/O 발생 횟수                          |
| PHYWRTS        | BIGINT  | 물리적 Write I/O 발생 횟수                         |
| PHYBLKRD       | BIGINT  | 물리적인 읽기로 판독한 페이지 개수                 |
| PHYBLKWRT      | BIGINT  | 물리적인 쓰기로 기록한 페이지 개수                 |
| SINGLEBLKRDS   | BIGINT  | 단일 페이지에 대한 읽기 작업 횟수                  |
| READTIM        | DOUBLE  | Read I/O 작업 시간 (milliseconds)                  |
| WRITETIM       | DOUBLE  | Write I/O 작업 시간 (milliseconds)                 |
| SINGLEBLKRDTIM | DOUBLE  | 단일 페이지에 대한 읽기에 걸린 시간 (milliseconds) |
| AVGIOTIM       | DOUBLE  | 평균 I/O 작업 시간 (milliseconds)                  |
| LSTIOTIM       | DOUBLE  | 마지막 I/O 작업 시간 (milliseconds)                |
| MINIOTIM       | DOUBLE  | 최소 I/O 작업 시간 (milliseconds)                  |
| MAXIORTM       | DOUBLE  | 최대 Read I/O 작업 시간 (milliseconds)             |
| MAXIOWTM       | DOUBLE  | 최대 Write I/O 작업 시간 (milliseconds)            |

#### 칼럼 정보

##### SPACEID

테이블스페이스의 식별자이다.

##### FILEID

데이터 파일의 식별자이다.

##### PHYRDS

물리적 Read I/O가 발생한 횟수다.

##### PHYWRTS

물리적 Write I/O가 발생한 횟수다.

##### PHYBLKRD

물리적인 Read로 판독한 페이지 개수이다.

##### PHYBLKWRT

물리적인 Write로 기록한 페이지 개수이다.

##### SINGLEBLKRDS

단일 페이지에 대한 Read 작업 횟수이다.

##### READTIM

Read I/O 작업에 걸린 시간이다. (단위: milliseconds)

##### WRITETIM

Write I/O 작업에 걸린 시간이다. (단위: milliseconds)

##### SINGLEBLKRDTIM

단일 페이지에 대하여 Read 작업에 걸린 시간이다. (단위: milliseconds)

##### AVGIOTIM

I/O 작업에 걸린 평균 시간이다. (단위: milliseconds)

##### LSTIOTIM

마지막 I/O 작업에 걸린 시간이다. (단위: milliseconds)

##### MINIOTIM

I/O 작업에 걸린 최소 시간이다. (단위: milliseconds)

##### MAXIORTM

Read I/O 작업에 걸린 최대 시간이다. (단위: milliseconds)

##### MAXIOWTM

Write I/O 작업에 걸린 최대 시간이다. (단위: milliseconds)

### V$FLUSHER

플러시 작업에 대한 정보를 보여준다.

| Column name              | Type    | Description                                                  |
| ------------------------ | ------- | ------------------------------------------------------------ |
| ID                       | INTEGER | Flusher 식별자                                               |
| ALIVE                    | INTEGER | Flusher 가 현재 활동 중인지 여부                             |
| CURRENT_JOB              | INTEGER | 현재 작업 1: 교체 플러시 중 2: 체크포인트 플러시 중 3: 객체 플러시 중 |
| DOING_IO                 | INTEGER | Flusher가 디스크 I/O 수행중인지 여부                         |
| INIOB_COUNT              | INTEGER | 플러시되는 내용을 그 안에 저장하기 위해 내부 버퍼에 직접 접근한 횟수 |
| REPLACE_FLUSH_JOBS       | BIGINT  | 완료된 교체 플러시 작업의 누적 횟수                          |
| REPLACE_FLUSH_PAGES      | BIGINT  | 교체 플러시로 디스크에 쓰여진 페이지의 누적 개수             |
| REPLACE_SKIP_PAGES       | BIGINT  | Replacement 플러시 중에 플러시가 취소된 페이지의 누적 개수   |
| CHECKPOINT_FLUSH_JOBS    | BIGINT  | 완료된 체크포인트 플러시 작업의 누적 횟수                    |
| CHECKPOINT_FLUSH_PAGES   | BIGINT  | 체크포인트 플러시로 디스크에 쓰여진 페이지의 누적 개수       |
| CHECKPOINT_SKIP_PAGES    | BIGINT  | 체크포인트 플러시 중에 플러시가 취소된 페이지의 누적 개수    |
| OBJECT_FLUSH_JOBS        | BIGINT  | 객체 플러시가 수행된 누적 횟수                               |
| OBJECT_FLUSH_PAGES       | BIGINT  | 객체 플러시로 디스크에 쓰여진 페이지의 누적 개수             |
| OBJECT_SKIP_PAGES        | BIGINT  | 객체 플러시 중에 플러시가 취소된 페이지의 누적 개수          |
| LAST_SLEEP_SEC           | INTEGER | 작업이 모두 완료된 후 Flusher가 잠들어 있던 시간의 길이      |
| TIMEOUT                  | BIGINT  | 작업 유무를 확인하기 위해서 잠든 Flusher가 깨어난 횟수       |
| SIGNALED                 | BIGINT  | Altibase로부터의 시그널에 의해 Flusher가 깨어난 횟수         |
| TOTAL_SLEEP_SEC          | BIGINT  | Flusher가 잠들어 있던 시간의 총 길이                         |
| TOTAL_FLUSH_PAGES        | BIGINT  | 플러시된 페이지의 누적 개수                                  |
| TOTAL_LOG_SYNC_USEC      | BIGINT  | 버퍼에 있는 리두 로그를 디스크로 쓰는 데 걸린 시간의 누적 양 |
| TOTAL_DW_USEC            | BIGINT  | DoubleWrite 버퍼의 내용을 디스크로 쓰는데 걸린 시간의 누적 양 |
| TOTAL_WRITE_USEC         | BIGINT  | 데이터 페이지를 데이터 파일에 쓰는데 걸린 시간의 누적 양     |
| TOTAL_SYNC_USEC          | BIGINT  | 데이터 페이지를 디스크로 강제 플러시하는데 걸린 시간의 누적 양 |
| TOTAL_FLUSH_TEMP_PAGES   | BIGINT  | 플러시된 임시 페이지의 누적 개수                             |
| TOTAL_TEMP_WRITE_USEC    | BIGINT  | 임시 페이지를 임시 파일에 쓰는데 걸린 시간의 누적 양         |
| TOTAL_CALC_CHECKSUM_USEC | BIGINT  | 체크섬(checksum) 계산에 걸린 시간의 누적 양                  |
| DB_WRITE_PERF            | DOUBLE  | 데이터 페이지를 데이터 파일에 쓸 때 초당 기록한 평균 바이트 수 |
| TEMP_WRITE_PERF          | DOUBLE  | 임시 페이지를 임시 파일에 쓸 때 초당 기록한 평균 바이트 수   |

#### 칼럼 정보

##### ID

Flusher 식별자이다. 식별자는 중복되지 않는다.

##### ALIVE

Flusher 가 현재 동작 중인지 여부를 나타낸다. 각 Flusher는 DCL구문으로 시작하거나 중지할 수 있다.

##### CURRENT_JOB

Flusher가 현재 수행중인 작업의 유형을 나타낸다.

- 1: 교체 플러시 수행 중임을 가리킨다. 교체 플러시의 목적은 오랜 시간 접근되지 않은 버퍼를 플러시하여 교체 가능하도록 하는 데 있다.
- 2: 체크포인트 플러시 수행 중임을 가리킨다. 체크포인트 플러시의 목적은 가장 오래 전에 갱신된 버퍼를 플러시하여 체크포인트 시간을 줄이는 데 있다.
- 3: 인덱스, 테이블, 세그먼트 등의 특정 객체를 플러시하고 있음을 가리킨다.

##### DOING_IO

Flusher가 현재 자신의 업무 수행을 위해서 디스크 I/O 작업 중인지 여부를 나타낸다.

##### INIOB_COUNT

Flusher는 페이지를 디스크에 기록하기 위해서, 그 내용을 내부 버퍼 (IOB)에 저장한다. 이 값은 그 내부 버퍼에 플러시할 내용을 저장하기 위해 접근한 횟수를 가리킨다.

##### REPLACE_FLUSH_JOBS

교체 플러시 작업을 수행한 횟수이다.

##### REPLACE_FLUSH_PAGES

교체 플러시 작업에 의해 디스크에 쓰여진 페이지의 누적 개수이다.

##### REPLACE_SKIP_PAGES

교체 플러시 중에 정책 또는 효율의 이유로 인해서 플러시 작업이 취소된 페이지의 누적 개수이다.

##### CHECKPOINT_FLUSH_JOBS

체크포인트 플러시 작업을 수행한 누적 횟수이다.

##### CHECKPOINT_FLUSH_PAGES

체크포인트 플러시 작업에 의해 디스크에 쓰여진 페이지의 누적 개수이다.

##### CHECKPOINT_SKIP_PAGES

체크포인트 플러시 중에 정책 또는 효율의 이유로 인해서 플러시가 취소된 페이지의 누적 개수이다.

##### OBJECT_FLUSH_JOBS

객체 플러시 작업을 수행한 누적 횟수이다.

##### OBJECT_FLUSH_PAGES

객체 플러시 작업에 의해 디스크에 쓰여진 페이지의 누적 개수이다.

##### OBJECT_SKIP_PAGES

객체 플러시 중에 정책 또는 효율의 이유로 인해서 플러시가 취소된 페이지의 누적 개수이다.

##### LAST_SLEEP_SEC

가장 최근에 모든 작업을 완료한 Flusher가 더 이상 작업이 없어서 잠들어 있던 시간의 길이이다.

##### TIMEOUT

작업이 없어서 잠들어 있던 Flusher가 작업 유무를 확인하기 위해서 일정 간격으로 깨어나야 할 필요가 있다. 이 값은 깨어난 누적 횟수다.

##### SIGNALED

어떤 작업의 빠른 처리를 위해서 Altibase는 잠든 Flusher에게 시그널을 주어서 깨울 수 있다. 이 값은 그 시그널에 의해 Flusher가 깨어난 횟수이다.

##### TOTAL_SLEEP_SEC

Flusher가 처리할 작업이 없어서 잠든 상태로 대기하고 있었던 시간의 총 합이다.

##### TOTAL_FLUSH_PAGES

체크포인트 플러시 또는 교체 플러시 중에 플러시된 페이지의 누적 개수이다

##### TOTAL_LOG_SYNC_USEC

데이터 페이지가 플러시될 때, WAL (Write Ahead Logging) 기법을 따라서 리두 로그가 먼저 디스크에 기록되어야 한다. 이 값은 리두 로그가 디스크에 기록되는데 소요된 시간의 누적 양이다.

##### TOTAL_DW_USEC

이 값은 doublewrite 버퍼의 내용을 디스크로 쓰는 데 걸린 시간의 누적 값이다. Doublewrite란 페이지들을 데이터 파일에 쓰기 전에, doublewrite buffer라 불리는 DW 파일에 먼저 기록하는 것을 말한다. Doublewrite buffer에 일단 기록된 후에, 그 페이지들은 데이터 파일의 올바른 위치에 다시 기록된다. 페이지를 데이터 파일에 기록하는 중에 운영 체제가 멈추거나 이들 데이터 파일이 손상된다면, 이 doublewrite 버퍼의 손상되지 않은 페이지를 이용해서 복구가 가능하다.

##### TOTAL_WRITE_USEC

데이터 페이지를 데이터 파일에 쓰는데 걸린 시간의 누적값이다. 이 값은 디스크에 플러시하는데 걸린 시간은 포함하지 않는다.

##### TOTAL_SYNC_USEC

데이터 페이지를 데이터 파일에 강제로 플러시 하는데 소요된 시간의 누적값이다.

##### TOTAL_FLUSH_TEMP_PAGES

플러시된 임시 페이지들의 누적 개수이다. (임시 페이지는 Sort 연산과 hash join을 할 때 사용되는 임시 테이블을 저장하는 데이터 페이지이다.)

##### TOTAL_TEMP_WRITE_USEC

임시 페이지들을 임시 파일에 기록하는데 걸린 시간의 누적값이다.

##### TOTAL_CALC_CHECKSUM_USEC

페이지에 오류가 있는지를 판단하기 위해 사용되는Checksum을 계산하는 데 걸린 시간의 누적 값이다.

##### DB_WRITE_PERF

데이터 페이지를 데이터 파일에 쓸 때 초당 기록된 bytes 수의 평균값으로 단위는 KB/Sec이다.

##### TEMP_WRITE_PERF

임시 페이지를 임시 파일에 쓸 때 초당 기록된 bytes 수의 평균값으로 단위는 KB/Sec이다.

### V$FLUSHINFO

버퍼 플러시 정보를 보여준다.

| Column name               | Type    | Description                                                  |
| ------------------------- | ------- | ------------------------------------------------------------ |
| LOW_FLUSH_LENGTH          | INTEGER | 교체 플러시(replacement flush)를 유발시킬 수 있는 최소한의 플러시 리스트 길이 |
| HIGH_FLUSH_LENGTH         | INTEGER | 플러셔가 REPLACE_FLUSH_COUNT 값을 무시하고 플러시 리스트의 모든 버퍼를 플러시하는 플러시 리스트 길이 |
| LOW_PREPARE_LENGTH        | INTEGER | 교체 플러시를 유발시킬 수 있는 최소한의 prepare 리스트 길이. 이 길이 이하가 되면 교체 플러시가 발생한다. |
| CHECKPOINT_FLUSH_COUNT    | BIGINT  | 체크포인트 플러시 수행시 플러시 할 버퍼의 개수               |
| FAST_START_IO_TARGET      | BIGINT  | 체크포인트 플러시 수행시 플러시 하지 않을 더티 페이지의 개수 |
| FAST_START_LOGFILE_TARGET | INTEGER | 체크포인트 플러시 수행시 플러시 하지 않을 로그 파일의 개수   |
| REQ_JOB_COUNT             | INTEGER | 현재 플러시 관리자에 등록된 작업의 개수                      |

#### 칼럼 정보

##### LOW_FLUSH_LENGTH

이는 교체 플러시(replacement flush)를 유발시킬 수 있는 최소한의 플러시 리스트 길이이다.

##### HIGH_FLUSH_LENGTH

이는 플러셔가 REPLACE_FLUSH_COUNT 값을 무시하고 플러시 리스트의 모든 버퍼를 플러시하는 플러시 리스트 길이이다.

##### LOW_PREPARE_LENGTH

이는 교체 플러시를 유발시킬 수 있는 최소한의 prepare 리스트 길이이다. 이 길이 이하가 되면 교체 플러시가 발생한다.

##### CHECKPOINT_FLUSH_COUNT

이는 체크포인트 플러시 수행시 플러시 할 버퍼의 개수이다.

##### FAST_START_IO_TARGET

이는 체크포인트 플러시 수행시 플러시 하지 않을 더티 페이지의 개수이다.

##### FAST_START_LOGFILE_TARGET

이는 체크포인트 플러시 수행시 플러시 하지 않을 로그 파일의 개수이다. 이들은 가장 최근에 생성된 로그 파일들이다.

##### REQ_JOB_COUNT

이는 플러시 관리자에 등록된 작업의 개수이다.

### V$INDEX

현재 데이터베이스에 존재하는 인덱스 정보를 보여준다.

| Column name   | Type       | Description                                                  |
| ------------- | ---------- | ------------------------------------------------------------ |
| TABLE_OID     | BIGINT     | 테이블 헤더의 객체 식별자                                    |
| INDEX_SEG_PID | INTEGER    | 디스크 인덱스의 경우 인덱스 세그먼트 헤더 (header)의 페이지 식별자 |
| INDEX_ID      | INTEGER    | 인덱스 식별자                                                |
| INDEXTYPE     | VARCHAR(7) | 해당 인덱스가 주 키 (primary key)로 사용되는지 일반 인덱스인지 식별하기 위한 구분자 |

#### 칼럼 정보

##### TABLE_OID

이는 인덱스가 생성된 테이블의 객체 식별자로, 테이블 정보를 갖고 있는 헤더의 물리적인 위치를 저장한다.

##### INDEXTYPE

이 값은 해당 인덱스가 주 키 (primary key)로서 사용되는지 또는 일반 인덱스인지를 나타낸다.

- PRIMARY: 주 키로 사용되는 인덱스
- NORMAL: 일반 인덱스

### V$INSTANCE

현재 Altibase의 구동 단계, 구동된 시간, 구동 후 경과된 시간에 관한 정보를 보여준다.

| Column name      | Type        | Description                                                  |
| ---------------- | ----------- | ------------------------------------------------------------ |
| STARTUP_PHASE    | VARCHAR(13) | 현재 구동 단계                                               |
| STARTUP_TIME_SEC | BIGINT      | Altibase가 구동된 시각을 시스템 시간으로 나타낸다 (단위: seconds) |
| WORKING_TIME_SEC | BIGINT      | 구동하여 지금까지 경과한 시간                                |

### V$INTERNAL_SESSION

Altibase의 DBMS_CONCURRENT_EXEC 패키지에서 생성된 세션에 대한 정보를 보여준다. 더 자세한 칼럼에 대한 정보는 V$SESSION의 칼럼 정보를 참조한다.

| Column name            | Type         | Description                                                  |
| ---------------------- | ------------ | ------------------------------------------------------------ |
| ID                     | BIGINT       | 세션 식별자                                                  |
| TRANS_ID               | BIGINT       | 세션에서 현재 수행중인 트랜잭션의 식별자                     |
| QUERY_TIME_LIMIT       | BIGINT       | 세션의 쿼리 시간 초과                                        |
| DDL_TIME_LIMIT         | BIGINT       | 세션의 DDL문 수행 시간 초과                                  |
| FETCH_TIME_LIMIT       | BIGINT       | 현재 세션의 Fetch 시간 초과                                  |
| UTRANS_TIME_LIMIT      | BIGINT       | 현재 세션의 갱신(update) 트랜잭션 시간 초과                  |
| IDLE_TIME_LIMIT        | BIGINT       | 현재 세션의 Idle 시간 초과                                   |
| IDLE_START_TIME        | INTEGER      | 세션의 Idle상태로 진입한 시각                                |
| ACTIVE_FLAG            | INTEGER      | 트랜잭션 활성 플래그                                         |
| OPENED_STMT_COUNT      | INTEGER      | 사용 중인 구문 개수                                          |
| DB_USERNAME            | VARCHAR(128) | 데이터베이스 사용자 이름                                     |
| DB_USERID              | INTEGER      | 데이터베이스 사용자 식별자                                   |
| DEFAULT_TBSID          | BIGINT       | 사용자의 디폴트 테이블스페이스 식별자                        |
| DEFAULT_TEMP_TBSID     | BIGINT       | 사용자의 디폴트 임시(temp) 테이블스페이스 식별자             |
| SYSDBA_FLAG            | INTEGER      | sysdba 로 접속했는지 여부                                    |
| AUTOCOMMIT_FLAG        | INTEGER      | Autocommit 플래그                                            |
| SESSION_STATE          | VARCHAR(13)  | 세션의 상태                                                  |
| ISOLATION_LEVEL        | INTEGER      | 세션의 고립 수준(isolation level)                            |
| REPLICATION_MODE       | INTEGER      | 이중화 모드                                                  |
| TRANSACTION_MODE       | INTEGER      | 트랜잭션 모드                                                |
| COMMIT_WRITE_WAIT_MODE | INTEGER      | 아래 참조                                                    |
| OPTIMIZER_MODE         | INTEGER      | 최적화 모드                                                  |
| HEADER_DISPLAY_MODE    | INTEGER      | SELECT 질의의 결과 출력시, 칼럼 이름만 출력할 것인지 테이블 이름도 함께 출력할 것인지 여부 0: 칼럼 이름과 함께 테이블 이름도 출력 1: 칼럼 이름만 출력 |
| CURRENT_STMT_ID        | INTEGER      | 사용 중인 구문 식별자                                        |
| STACK_SIZE             | INTEGER      | 질의 처리를 위한 스택의 크기(단위: bytes)                    |
| DEFAULT_DATE_FORMAT    | VARCHAR(64)  | 디폴트 날짜 형식 예) DD-MON-RRRR                             |
| TRX_UPDATE_MAX_LOGSIZE | BIGINT       | DML 로그의 최대 크기(단위: bytes)                            |
| PARALLE_DML_MODE       | INTEGER      | Deprecated                                                   |
| LOGIN_TIME             | INTEGER      | 클라이언트 접속 시간                                         |
| FAILOVER_SOURCE        | VARCHAR(256) | FailOver가 일어났을 때의 접속 정보                           |
| NLS_TERRITORY          | VARCHAR(40)  | 세션의 지역 이름                                             |
| NLS_ISO_CURRENCY       | VARCHAR(40)  | 세션의 ISO 통화 기호                                         |
| NLS_CURRENCY           | VARCHAR(10)  | 세션의 지역 통화 기호                                        |
| NLS_NUMERIC_CHARACTERS | VARCHAR(2)   | 세션의 소수점 문자와 그룹 구분자                             |
| TIME_ZONE              | VARCHAR(40)  | 세션에 설정된 타임 존의 지역 이름, 약어 또는 UTC_OFFSET      |
| LOB_CACHE_THRESHOLD    | INTEGER      | LOB_CACHE_THRESHOLD 프로퍼티에 설정된 값                     |
| QUERY_REWRITE_ENABLE   | VARCHAR(7)   | QUERY_REWRITE_ENABLE 프로퍼티에 설정된 값                    |

#### 칼럼 정보

##### TRANS_ID

세션에서 현재 수행하고 있는 트랜잭션 식별자를 나타낸다. 현재 수행중인 트랜잭션이 없으면 이 값은 -1이 된다.

##### ACTIVE_FLAG

세션이 어떤 구문을 수행하고 있을 경우 1로 나타난다. 그러나 단지 연결만 되어있거나, 트랜잭션을 커밋 또는 롤백한 후에는 0으로 표시된다.

##### SYSDBA_FLAG

접속된 세션이 sysdba 모드인지 아닌지를 나타낸다.

- 1: sysdba 모드

##### AUTOCOMMIT_FLAG

접속된 세션이 autocommit 모드인지를 나타낸다.

- 0: non-autocommit
- 1: autocommit

##### SESSION_STATE

| STATE         | Description                                                  |
| ------------- | ------------------------------------------------------------ |
| INIT          | 클라이언트로부터 요청이 들어오기를 기다리고 있는 상태        |
| AUTH          | 사용자 인증을 마친 상태                                      |
| SERVICE READY | 서비스 준비상태 (트랜잭션을 만들 수 없는 상태로 XA 세션의 경우에만 이 상태로 올 수 있다.) |
| SERVICE       | 서비스 상태                                                  |
| END           | 정상 종료 (트랜잭션이 있을 경우 커밋) 하고 있는 상태         |
| ROLLBACK      | 비정상 종료 (트랜잭션이 있을 경우 ROLLBACK)하고 있는 상태. 클라이언트가 끊기거나 서버에서 세션을 강제로 끊을 때 발생한다. |
| UNKNOWN       | 알 수 없는 상태                                              |

##### REPLICATION_MODE

세션의 이중화 모드를 나타낸다.

- 0: DEFAULT
- 16: NONE

##### TRANSACTION_MODE

트랜잭션 모드를 나타낸다.

- 0: READ/WRITE
- 4: READ ONLY

##### COMMIT_WRITE_WAIT_MODE

- 0: commit 시, 로그를 디스크에 기록할 때까지 기다리지 않는다.
- 1: commit 시, 로그를 디스크에 기록할 때까지 기다린다.

##### OPTIMIZER_MODE

해당 세션에 설정된 최적화 모드를 나타낸다.

- 1: 규칙 기반 (rule based)
- 0: 비용 기반 (cost based)

##### QUERY_REWRITE_ENABLE

세션에서 QUERY_REWRITE_ENABLE 프로퍼티에 설정된 값을 표시한다. QUERY_REWRITE_ENABLE 프로퍼티에 대해서는 2장을 참고하라.

- FALSE: Altibase 서버에서 쿼리 변환 시에 함수 기반 인덱스 미적용(disable)
- TRUE: Altibase 서버에서 쿼리 변환 시에 함수 기반 인덱스 적용(enable)
