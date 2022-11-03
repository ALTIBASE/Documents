Altibase 7.1.0.8.0 Patch Notes
==============================

<br/>

<br/>

# Table Of Contents

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
  - [BUG-49904 이중화 송신자에게 고정 IP 주소를 할당하는 기능을 추가합니다.](#bug-49904%EC%9D%B4%EC%A4%91%ED%99%94-%EC%86%A1%EC%8B%A0%EC%9E%90%EC%97%90%EA%B2%8C-%EA%B3%A0%EC%A0%95-ip-%EC%A3%BC%EC%86%8C%EB%A5%BC-%ED%95%A0%EB%8B%B9%ED%95%98%EB%8A%94-%EA%B8%B0%EB%8A%A5%EC%9D%84-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
- [Fixed Bugs](#fixed-bugs)
  - [BUG-48624 ​타입 세트 재생성과 PSM 간 동시성 문제로 발생하는 안정성 문제를 개선합니다.](#bug-48624%E2%80%8B%ED%83%80%EC%9E%85-%EC%84%B8%ED%8A%B8-%EC%9E%AC%EC%83%9D%EC%84%B1%EA%B3%BC-psm-%EA%B0%84-%EB%8F%99%EC%8B%9C%EC%84%B1-%EB%AC%B8%EC%A0%9C%EB%A1%9C-%EB%B0%9C%EC%83%9D%ED%95%98%EB%8A%94-%EC%95%88%EC%A0%95%EC%84%B1-%EB%AC%B8%EC%A0%9C%EB%A5%BC-%EA%B0%9C%EC%84%A0%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49094 뷰 머징이 발생한 뷰의 컬럼을 HAVING 절의 CONNECT BY 절에서 사용할 때 발생하는 안정성 문제를 개선합니다.](#bug-49094%EB%B7%B0-%EB%A8%B8%EC%A7%95%EC%9D%B4-%EB%B0%9C%EC%83%9D%ED%95%9C-%EB%B7%B0%EC%9D%98-%EC%BB%AC%EB%9F%BC%EC%9D%84-having-%EC%A0%88%EC%9D%98-connect-by-%EC%A0%88%EC%97%90%EC%84%9C-%EC%82%AC%EC%9A%A9%ED%95%A0-%EB%95%8C-%EB%B0%9C%EC%83%9D%ED%95%98%EB%8A%94-%EC%95%88%EC%A0%95%EC%84%B1-%EB%AC%B8%EC%A0%9C%EB%A5%BC-%EA%B0%9C%EC%84%A0%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49712 기본 파티션 테이블을 포함한 이중화 객체에서 특정 파티션 테이블을 이중화 테이블에서 삭제하면 이중화 송신자가 중단됩니다.](#bug-49712EA%B8%B0%EB%B3%B8-%ED%8C%8C%ED%8B%B0%EC%85%98-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%9D%84-%ED%8F%AC%ED%95%A8%ED%95%9C-%EC%9D%B4%EC%A4%91%ED%99%94-%EA%B0%9D%EC%B2%B4%EC%97%90%EC%84%9C-%ED%8A%B9%EC%A0%95-%ED%8C%8C%ED%8B%B0%EC%85%98-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%9D%84-%EC%9D%B4%EC%A4%91%ED%99%94-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90%EC%84%9C-%EC%82%AD%EC%A0%9C%ED%95%98%EB%A9%B4-%EC%9D%B4%EC%A4%91%ED%99%94-%EC%86%A1%EC%8B%A0%EC%9E%90%EA%B0%80-%EC%A4%91%EB%8B%A8%EB%90%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49737 Veracode에서 검출된 JDBC 드라이버의 보안 취약점을 수정합니다.](#bug-49737veracode%EC%97%90%EC%84%9C-%EA%B2%80%EC%B6%9C%EB%90%9C-jdbc-%EB%93%9C%EB%9D%BC%EC%9D%B4%EB%B2%84%EC%9D%98-%EB%B3%B4%EC%95%88-%EC%B7%A8%EC%95%BD%EC%A0%90%EC%9D%84-%EC%88%98%EC%A0%95%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49774 REGEXP\_MODE 프로퍼티 값이 1일 때 정규 표현식 함수에서 성능 뷰를 참조하면 결과 오류가 발생합니다.](#bug-49774regexp_mode-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0-%EA%B0%92%EC%9D%B4-1%EC%9D%BC-%EB%95%8C-%EC%A0%95%EA%B7%9C-%ED%91%9C%ED%98%84%EC%8B%9D-%ED%95%A8%EC%88%98%EC%97%90%EC%84%9C-%EC%84%B1%EB%8A%A5-%EB%B7%B0%EB%A5%BC-%EC%B0%B8%EC%A1%B0%ED%95%98%EB%A9%B4-%EA%B2%B0%EA%B3%BC-%EC%98%A4%EB%A5%98%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49825 NORMALFORM\_MAXIMUM 프로퍼티가 0 일 때, PARALLEL을 지정한 테이블과 서브쿼리가 있는 질의문 수행 시 발생하는 안정성 문제를 개선합니다.](#bug-49825normalform_maximum-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0%EA%B0%80-0-%EC%9D%BC-%EB%95%8C-parallel%EC%9D%84-%EC%A7%80%EC%A0%95%ED%95%9C-%ED%85%8C%EC%9D%B4%EB%B8%94%EA%B3%BC-%EC%84%9C%EB%B8%8C%EC%BF%BC%EB%A6%AC%EA%B0%80-%EC%9E%88%EB%8A%94-%EC%A7%88%EC%9D%98%EB%AC%B8-%EC%88%98%ED%96%89-%EC%8B%9C-%EB%B0%9C%EC%83%9D%ED%95%98%EB%8A%94-%EC%95%88%EC%A0%95%EC%84%B1-%EB%AC%B8%EC%A0%9C%EB%A5%BC-%EA%B0%9C%EC%84%A0%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49834 저장 프로시저(또는 저장 함수 및 패키지)에서 접근하는 시노님의 정의가 변경될 때 저장 프로시저(또는 저장 함수 및 패키지)에 반영되지 않습니다.](#bug-49834%EC%A0%80%EC%9E%A5-%ED%94%84%EB%A1%9C%EC%8B%9C%EC%A0%80%EB%98%90%EB%8A%94-%EC%A0%80%EC%9E%A5-%ED%95%A8%EC%88%98-%EB%B0%8F-%ED%8C%A8%ED%82%A4%EC%A7%80%EC%97%90%EC%84%9C-%EC%A0%91%EA%B7%BC%ED%95%98%EB%8A%94-%EC%8B%9C%EB%85%B8%EB%8B%98%EC%9D%98-%EC%A0%95%EC%9D%98%EA%B0%80-%EB%B3%80%EA%B2%BD%EB%90%A0-%EB%95%8C-%EC%A0%80%EC%9E%A5-%ED%94%84%EB%A1%9C%EC%8B%9C%EC%A0%80%EB%98%90%EB%8A%94-%EC%A0%80%EC%9E%A5-%ED%95%A8%EC%88%98-%EB%B0%8F-%ED%8C%A8%ED%82%A4%EC%A7%80%EC%97%90-%EB%B0%98%EC%98%81%EB%90%98%EC%A7%80-%EC%95%8A%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-49845 휘발성 테이블스페이스를 대상으로 BEGIN BACKUP 수행 시 ERR-0109E : Internal server error. 에러가 발생합니다.](#bug-49845%ED%9C%98%EB%B0%9C%EC%84%B1-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%8A%A4%ED%8E%98%EC%9D%B4%EC%8A%A4%EB%A5%BC-%EB%8C%80%EC%83%81%EC%9C%BC%EB%A1%9C-begin-backup-%EC%88%98%ED%96%89-%EC%8B%9C-err-0109e--internal-server-error-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49846 패키지의 시노님을 사용한 질의문을 반복 수행 시 하드 파싱이 발생합니다.](#bug-49846%ED%8C%A8%ED%82%A4%EC%A7%80%EC%9D%98-%EC%8B%9C%EB%85%B8%EB%8B%98%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%9C-%EC%A7%88%EC%9D%98%EB%AC%B8%EC%9D%84-%EB%B0%98%EB%B3%B5-%EC%88%98%ED%96%89-%EC%8B%9C-%ED%95%98%EB%93%9C-%ED%8C%8C%EC%8B%B1%EC%9D%B4-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49849 Non autocommit 환경에서 PSM 수행 중 명시적 또는 묵시적 커밋이 발생한 후 PSM 수행이 실패하면 Altibase 서버가 비정상 종료합니다.](#bug-49849non-autocommit-%ED%99%98%EA%B2%BD%EC%97%90%EC%84%9C-psm-%EC%88%98%ED%96%89-%EC%A4%91-%EB%AA%85%EC%8B%9C%EC%A0%81-%EB%98%90%EB%8A%94-%EB%AC%B5%EC%8B%9C%EC%A0%81-%EC%BB%A4%EB%B0%8B%EC%9D%B4-%EB%B0%9C%EC%83%9D%ED%95%9C-%ED%9B%84-psm-%EC%88%98%ED%96%89%EC%9D%B4-%EC%8B%A4%ED%8C%A8%ED%95%98%EB%A9%B4-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49850 패키지 스펙의 변수를 기본값으로 하는 인자를 사용한 서브 프로그램을 다른 저장 프로시저 또는 저장 함수에서 호출할 때 ERR-31455 에러가 발생합니다.](#bug-49850%ED%8C%A8%ED%82%A4%EC%A7%80-%EC%8A%A4%ED%8E%99%EC%9D%98-%EB%B3%80%EC%88%98%EB%A5%BC-%EA%B8%B0%EB%B3%B8%EA%B0%92%EC%9C%BC%EB%A1%9C-%ED%95%98%EB%8A%94-%EC%9D%B8%EC%9E%90%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%9C-%EC%84%9C%EB%B8%8C-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%A8%EC%9D%84-%EB%8B%A4%EB%A5%B8-%EC%A0%80%EC%9E%A5-%ED%94%84%EB%A1%9C%EC%8B%9C%EC%A0%80-%EB%98%90%EB%8A%94-%EC%A0%80%EC%9E%A5-%ED%95%A8%EC%88%98%EC%97%90%EC%84%9C-%ED%98%B8%EC%B6%9C%ED%95%A0-%EB%95%8C-err-31455-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49857 altibase.properties에서 TRANSACTION\_SEGMENT\_COUNT 프로퍼티의 최대값을 16384로 수정합니다.](#bug-49857altibaseproperties%EC%97%90%EC%84%9C-transaction_segment_count-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0%EC%9D%98-%EC%B5%9C%EB%8C%80%EA%B0%92%EC%9D%84-16384%EB%A1%9C-%EC%88%98%EC%A0%95%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49867 디스크 인덱스 생성 시 altibase_sm.log에 [IDX_CRE] 2. Merge 메시지가 출력된 후 무한 대기하는 현상이 발생합니다.](#bug-49867%EB%94%94%EC%8A%A4%ED%81%AC-%EC%9D%B8%EB%8D%B1%EC%8A%A4-%EC%83%9D%EC%84%B1-%EC%8B%9C-altibase_smlog%EC%97%90-idx_cre-2-merge-%EB%A9%94%EC%8B%9C%EC%A7%80%EA%B0%80-%EC%B6%9C%EB%A0%A5%EB%90%9C-%ED%9B%84-%EB%AC%B4%ED%95%9C-%EB%8C%80%EA%B8%B0%ED%95%98%EB%8A%94-%ED%98%84%EC%83%81%EC%9D%B4-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49868 EXECUTE\_STMT\_MEMORY\_MAXIMUM 초과로 재컴파일이 실패한 뷰 사용 시 발생하는 안정성 문제를 개선합니다.](#bug-49868execute_stmt_memory_maximum-%EC%B4%88%EA%B3%BC%EB%A1%9C-%EC%9E%AC%EC%BB%B4%ED%8C%8C%EC%9D%BC%EC%9D%B4-%EC%8B%A4%ED%8C%A8%ED%95%9C-%EB%B7%B0-%EC%82%AC%EC%9A%A9-%EC%8B%9C-%EB%B0%9C%EC%83%9D%ED%95%98%EB%8A%94-%EC%95%88%EC%A0%95%EC%84%B1-%EB%AC%B8%EC%A0%9C%EB%A5%BC-%EA%B0%9C%EC%84%A0%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49894 aexport 수행 시 TYPESET 객체가 추출되지 않습니다.](#bug-49894aexport-%EC%88%98%ED%96%89-%EC%8B%9C-typeset-%EA%B0%9D%EC%B2%B4%EA%B0%80-%EC%B6%94%EC%B6%9C%EB%90%98%EC%A7%80-%EC%95%8A%EC%8A%B5%EB%8B%88%EB%8B%A4)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
  - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
  - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-49904 이중화 송신자에게 고정 IP 주소를 할당하는 기능을 추가합니다.

#### module
`rp-sender`

#### Category
`Functionality`

#### 재현 빈도
`Always`

#### 설명
이중화 송신자에게 고정 IP 주소를 할당하는 기능을 추가합니다.

이 기능을 사용하려면 Altibase 서버 프로퍼티 REPLICATION\_SENDER\_IP를 설정해야 합니다.  프로퍼티 설명 및 사용 방법은 매뉴얼을 참고하시기 바랍니다.

- [Altibase 7.1 General Reference-1.Data Types & Altibase Properties](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase\_7.1/kor/General%20Reference-1.Data%20Types%20%26%20Altibase%20Properties.md\#replication\_sender\_ip)
- [Altibase 7.1 Replication Manual](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase\_7.1/kor/Replication%20Manual.md\#%EC%86%A1%EC%8B%A0%EC%9E%90-ip-%EC%A3%BC%EC%86%8C-%EC%84%A4%EC%A0%95)

#### 변경사항

-   Performance view
-   Property
    -   `REPLICATION_SENDER_IP`

        이중화 송신자의 IP 주소를 설정하는 프로퍼티이다. 값으로 ANY나 IP 주소를 입력할 수 있다.

        기본값 ANY는 이중화 객체를 생성하는 지역 서버의 모든 IP 주소가 이중화 통신에 사용될 수 있으며 OS에서 할당한 IP 주소가 송신자 IP 주소로 사용된다. IP 주소를 값으로 설정하면 원격 서버(수신자)와 통신할 때 설정한 IP 주소만 사용된다. REPLICATION_SENDER_IP = *value*를 추가하여 여러 개의 IP 주소를 설정할 수 있으며 순서대로 송신자 IP 주소로 사용된다. IP 주소는 IPv4, IPv6, IPv6 확장 주소 형태로 입력할 수 있다. 이 프로퍼티는 Altibase 7.1.0.8.0부터 지원하며 이중화 통신 방법이 TCP일 때 적용된다.

-   Compile Option
-   Error Code

Fixed Bugs
==========

### BUG-48624 ​타입 세트 재생성과 PSM 간 동시성 문제로 발생하는 안정성 문제를 개선합니다.

#### module
`qp-trigger-execute`

#### Category
`Fatal`

#### 재현 빈도
`Rare`

#### 설명
PSM에서 타입 세트 또는 패키지 스펙을 참조할 때, 한 세션에서 해당 타입 세트 또는 패키지 스펙을 재생성하고 또 다른 세션에서 PSM을 반복 수행했을 때 Altibase 서버가 비정상 종료하는 현상을 수정합니다.

#### 재현 방법

-   재현 절차
-   수행 결과
-   예상 결과

#### Workaround

`없음`

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-49094 뷰 머징이 발생한 뷰의 컬럼을 HAVING 절의 CONNECT BY 절에서 사용할 때 발생하는 안정성 문제를 개선합니다.

#### module
`qp-dml-pvo`

#### Category
`Assert`

#### 재현 빈도
`Always`

#### 설명
뷰 머징이 발생한 뷰의 컬럼을 HAVING 절의 CONNECT BY 절에서 사용할 때 Altibase 서버가 비정상 종료하는 현상을 개선합니다.

#### 재현 방법

- 재현 절차

  ```sql
  CREATE TABLE T1 ( I1 INT, I2 INT);
  SELECT I1
    FROM (SELECT * FROM T1 ) AS V1
   GROUP BY I1
  HAVING I1 IN (SELECT I1 FROM T1 START WITH I1 = V1.I1 CONNECT BY PRIOR I1 = I2);
  ```

- 수행 결과

  아래와 같은 메시지가 발생하며 Altibase 서버가 비정상 종료합니다.

  ```sql
  [ERR-31455 : Failed to work because an internal exception occurred from an OS.[Contact Altibase's Support Center]]
  ```

- 예상 결과

  ```sql
  I1          
  --------------
  No rows selected.
  ```

#### Workaround

NO_MERGE 힌트를 사용합니다.

```sql
SELECT /*+ NO_MERGE(V1) */ I1
  FROM (SELECT * FROM T1 ) AS V1
 GROUP BY I1
HAVING I1 IN (SELECT I1 FROM T1 START WITH I1 = V1.I1 CONNECT BY PRIOR I1 = I2);
```

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-49712 기본 파티션 테이블을 포함한 이중화 객체에서 특정 파티션 테이블을 이중화 테이블에서 삭제하면 이중화 송신자가 중단됩니다.

#### module
`rp-control`

#### Category
`Functional Error`

#### 재현 빈도
`Frequence`

#### 설명
기본 파티션 테이블을 포함한 이중화 객체에서 특정 파티션 테이블을 이중화 테이블에서 삭제하면  이중화 송신자가 중단되는 현상을 수정합니다.

#### 재현 방법

-   재현 절차
-   수행 결과
-   예상 결과

#### Workaround

`없음`

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-49737 Veracode에서 검출된 JDBC 드라이버의 보안 취약점을 수정합니다.

#### module
`mm-jdbc`

#### Category
`Functional Error`

#### 재현 빈도
`Always`

#### 설명
보안 취약점 검사 툴인 베라코드(Veracode)에서 검출된 JDBC 드라이버의 보안 취약점을 수정합니다.

#### 재현 방법

-   재현 절차
-   수행 결과
-   예상 결과

#### Workaround

`없음`

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-49774 REGEXP\_MODE 프로퍼티 값이 1일 때 정규 표현식 함수에서 성능 뷰를 참조하면 결과 오류가 발생합니다.

#### module
`qp`

#### Category
`Functional Error`

#### 재현 빈도
`Always`

#### 설명
REGEXP\_MODE 프로퍼티 값이 1일 때 정규 표현식 함수에서 성능 뷰를 참조하면 결과 오류가 발생합니다.

#### 재현 방법

- 재현 절차

  ```sql
  ALTER SESSION SET REGEXP_MODE=1;
  SELECT * FROM V$NLS_TERRITORY WHERE REGEXP_LIKE(CONVERT(NAME, 'UTF8'), 'C');
  ```

- 수행 결과

  ~~~sql
  NAME
  --------------------------------------------
  No rows selected.
  ~~~

- 예상 결과

  ~~~sql
  NAME
  --------------------------------------------
  AMERICA
  CANADA
  CATALONIA
  CHILE
  CHINA
  CIS
  COLOMBIA
  COSTA RICA
  CROATIA
  CYPRUS
  CZECH REPUBLIC
  CZECHOSLOVAKIA
  ECUADOR
  FRANCE
  FYR MACEDONIA
  GREECE
  ICELAND
  MACEDONIA
  MEXICO
  MOROCCO
  NICARAGUA
  PUERTO RICO
  SOUTH AFRICA
  23 rows selected.
  ~~~


#### Workaround


~~~sql
ALTER SESSONI SET REGEXP_MODE = 0;
~~~

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-49825 NORMALFORM\_MAXIMUM 프로퍼티가 0 일 때, PARALLEL을 지정한 테이블과 서브쿼리가 있는 질의문 수행 시 발생하는 안정성 문제를 개선합니다.

#### module
`qp`

#### Category
`Fatal`

#### 재현 빈도
`Always`

#### 설명
NORMALFORM\_MAXIMUM 프로퍼티가 0 일 때, PARALLEL을 지정한 테이블과 서브쿼리가 있는 질의문 수행 시 Altibase 서버가 비정상 종료하는 현상을 수정합니다.

이 버그는 다음의 조건을 모두 만족하는 질의문 수행 시 간헐적으로 발생합니다.
- NORMALFORM\_MAXIMUM 프로퍼티 0 으로 설정

- PARALLEL을 지정하여 테이블 생성

- FROM 절에 PARALLEL을 지정하여 생성한 테이블 사용

- WHERE 절에 서브 쿼리 사용

- 서브 쿼리에 USE\_FULL\_STORE\_NL 힌트 사용 또는 USE\_FULL\_STORE\_NL 힌트와 RESULT\_CACHE 힌트를 함께 사용

- 서브 쿼리의 WHERE 절에 조인 조건 외에 FROM 절의 2번째 테이블의 컬럼이 사용된 또다른 조건 사용

#### 재현 방법

-   재현 절차
-   수행 결과
-   예상 결과

#### Workaround

`없음`

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-49834 저장 프로시저(또는 저장 함수 및 패키지)에서 접근하는 시노님의 정의가 변경될 때 저장 프로시저(또는 저장 함수 및 패키지)에 반영되지 않습니다.

#### module
`qp-ddl-dcl-execute`

#### Category
`Functional Error`

#### 재현 빈도
`Always`

#### 설명
저장 프로시저나 저장 함수의 별칭으로 생성한 시노님을 또 다른 저장 프로시저(또는 저장 함수 및 패키지)에서 사용할 때 해당 시노님을 연관된 객체로 저장하지 않는 문제를 수정합니다.

이 버그는 아래 조건을 모두 만족하는 저장 프로시저(또는 저장 함수 및 패키지)를 수행할 때 발생합니다.

- 저장 프로시저나 저장 함수의 별칭으로 생성한 시노님

- 저장 프로시저나 저장 함수의 별칭으로 생성한 시노님을 또 다른 저장 프로시저(또는 저장 함수 및 패키지)에서 사용

- 저장 프로시저나 저장 함수의 별칭으로 생성한 시노님의 정의를 변경하여 재생성

***패치 영향도***

버그 조건을 만족하는 시노님, 저장 프로시저(또는 저장 함수 및 패키지)가 있을 때 패치 전/후 저장 프로시저(또는 저장 함수 및 패키지)의 수행 결과가 달라집니다.

#### 재현 방법

-   재현 절차

    ```sql
    DROP TABLE T1;
    DROP TABLE T2;
    DROP SYNONYM TABLE_SYM;
    DROP PROCEDURE PROC1;
    DROP PROCEDURE PROC2;
    DROP PROCEDURE PROC3;
    DROP SYNONYM PROC_SYM;
    
    CREATE TABLE T1 (C1 VARCHAR(10));
    CREATE TABLE T2 (C1 VARCHAR(10));
    CREATE SYNONYM TABLE_SYM FOR T1;
    
    INSERT INTO T1 VALUES('T1');
    INSERT INTO T2 VALUES('T2');
    
    CREATE OR REPLACE PROCEDURE PROC1 AS
    BEGIN
      PRINTLN('PROC1');
    END;
    /
    
    CREATE OR REPLACE PROCEDURE PROC2 AS
    BEGIN
      PRINTLN('PROC2');
    END;
    /
    
    CREATE SYNONYM PROC_SYM FOR PROC1;
    
    CREATE OR REPLACE PROCEDURE PROC3 AS
    VAR1 VARCHAR(10);
    BEGIN
      SELECT C1 INTO VAR1 FROM TABLE_SYM;
      PRINTLN(VAR1);
      PROC_SYM;
    END;
    /
    
    EXEC PROC3;
    CREATE OR REPLACE SYNONYM TABLE_SYM FOR T2;
    
    EXEC PROC3;
    CREATE OR REPLACE SYNONYM PROC_SYM FOR PROC2;
    
    EXEC PROC3;
    ```

-   수행 결과

    ```sql
    iSQL> EXEC PROC3;
    T2
    PROC1
    Execute success.
    ```

-   예상 결과

    ```sql
    iSQL> EXEC PROC3;
    T2
    PROC2
    Execute success.
    ```

#### Workaround

`없음`

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-49845 휘발성 테이블스페이스를 대상으로 BEGIN BACKUP 수행 시 ERR-0109E : Internal server error. 에러가 발생합니다.

#### module
`sm`

#### Category
`Assert`

#### 재현 빈도
`Always`

#### 설명
휘발성 테이블스페이스를 대상으로 ALTER TABLESPACE ... BEGIN BACKUP 수행 시 ERR-0109E : Internal server error. 에러가 발생하는 현상을 수정합니다. 휘발성 테이블스페이스는 데이터베이스 백업 대상이 아니므로 ERR-11101 : Unable to back up a vilatile tablespace. 에러가 발생하도록 변경합니다.

#### 재현 방법

-   재현 절차
-   수행 결과
-   예상 결과

#### Workaround

`없음`

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-49846 패키지의 시노님을 사용한 질의문을 반복 수행 시 하드 파싱이 발생합니다.

#### module
`qp-select-pvo`

#### Category
`Functional Error`

#### 재현 빈도
`Always`

#### 설명
패키지의 시노님을 사용한 질의문을 반복 수행 시 하드 파싱이 발생하는 문제를 수정합니다. 

질의 처리 과정에서 패키지의 시노님의 정당성 검사(Validation) 누락으로 SQL Plan Cache에 등록된 실행 계획을 공유하지 않아 하드 파싱이 발생합니다.

이 버그 반영 후에는 패키지의 시노님을 사용한 질의문을 반복 수행 시 실행 계획 생성 이후 패키지가 변경되지 않았다면 소프트 파싱합니다.

#### 재현 방법

-   재현 절차

        CREATE OR REPLACE PACKAGE PKG1 AS
        FUNCTION FUNC1 RETURN INTEGER;
        END;
        /
        CREATE OR REPLACE PACKAGE BODY PKG1 AS
        FUNCTION FUNC1 RETURN INTEGER AS
        BEGIN
          RETURN 1;
        END;
        END;
        /
        CREATE SYNONYM SYN2 FOR SYS.PKG1;
        SELECT * FROM V$SQL_PLAN_CACHE_SQLTEXT WHERE SQL_TEXT LIKE 'SELECT%SYN2%DUAL';
        SELECT SYN2.FUNC1 FROM DUAL;
        SELECT * FROM V$SQL_PLAN_CACHE_SQLTEXT WHERE SQL_TEXT LIKE 'SELECT%SYN2%DUAL';
        SELECT SYN2.FUNC1 FROM DUAL;
        SELECT * FROM V$SQL_PLAN_CACHE_SQLTEXT WHERE SQL_TEXT LIKE 'SELECT%SYN2%DUAL';

-   수행 결과

        iSQL> SELECT * FROM V$SQL_PLAN_CACHE_SQLTEXT WHERE SQL_TEXT LIKE 'SELECT%SYN2%DUAL';
        No rows selected.
        iSQL> SELECT SYN2.FUNC1 FROM DUAL;
        SYN2.FUNC1 : 1 
        1 row selected.
        iSQL> SELECT * FROM V$SQL_PLAN_CACHE_SQLTEXT WHERE SQL_TEXT LIKE 'SELECT%SYN2%DUAL';
        SQL_TEXT_ID            : 00500  
        SQL_TEXT               : SELECT SYN2.FUNC1 FROM DUAL  
        CHILD_PCO_COUNT        : 1 
        CHILD_PCO_CREATE_COUNT : 1 
        PLAN_CACHE_KEEP        : UNKEEP  
        1 row selected.
        iSQL> SELECT SYN2.FUNC1 FROM DUAL;
        SYN2.FUNC1 : 1 
        1 row selected.
        iSQL> SELECT * FROM V$SQL_PLAN_CACHE_SQLTEXT WHERE SQL_TEXT LIKE 'SELECT%SYN2%DUAL';
        SQL_TEXT_ID            : 00500  
        SQL_TEXT               : SELECT SYN2.FUNC1 FROM DUAL  
        CHILD_PCO_COUNT        : 2 
        CHILD_PCO_CREATE_COUNT : 2 
        PLAN_CACHE_KEEP        : UNKEEP 

-   예상 결과

        iSQL> SELECT * FROM V$SQL_PLAN_CACHE_SQLTEXT WHERE SQL_TEXT LIKE 'SELECT%SYN2%DUAL';
        No rows selected.
        iSQL> SELECT SYN2.FUNC1 FROM DUAL;
        SYN2.FUNC1 : 1 
        1 row selected.
        iSQL> SELECT * FROM V$SQL_PLAN_CACHE_SQLTEXT WHERE SQL_TEXT LIKE 'SELECT%SYN2%DUAL';
        SQL_TEXT_ID            : 00500  
        SQL_TEXT               : SELECT SYN2.FUNC1 FROM DUAL  
        CHILD_PCO_COUNT        : 1 
        CHILD_PCO_CREATE_COUNT : 1 
        PLAN_CACHE_KEEP        : UNKEEP  
        1 row selected.
        iSQL> SELECT SYN2.FUNC1 FROM DUAL;
        SYN2.FUNC1 : 1 
        1 row selected.
        iSQL> SELECT * FROM V$SQL_PLAN_CACHE_SQLTEXT WHERE SQL_TEXT LIKE 'SELECT%SYN2%DUAL';
        SQL_TEXT_ID            : 00500  
        SQL_TEXT               : SELECT SYN2.FUNC1 FROM DUAL  
        CHILD_PCO_COUNT        : 1 
        CHILD_PCO_CREATE_COUNT : 1 
        PLAN_CACHE_KEEP        : UNKEEP  
        1 row selected.

#### Workaround

`없음`

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-49849 Non autocommit 환경에서 PSM 수행 중 명시적 또는 묵시적 커밋이 발생한 후 PSM 수행이 실패하면 Altibase 서버가 비정상 종료합니다.

#### module
`sm`

#### Category
`Fatal`

#### 재현 빈도
`Always`

#### 설명
Non autocommit 환경에서 PSM 수행이 실패할 때 Altibase 서버가 비정상 종료하는 현상을 수정합니다.

Altibase 서버는 하나의 트랜잭션에서 PSM이 시작할 때, PSM 수행이 실패하면 롤백할 지점인 PSM savepoint를 설정합니다. 이 버그는 PSM 수행 중 PSM savepoint가 초기화되는 문제로, PSM 수행이 실패하면 메모리 참조 오류로 Altibase 서버가 비정상 종료합니다.

이 버그가 발생하는 조건은 아래와 같습니다.

- Altibase 클라이언트 버전 5.3.3 \~ 6.1.1

- Altibase 서버 버전 6.5.1, 7.1 

- non autocommit 모드

- 하나의 트랜잭션 내에서 아래와 같은 순서로 수행

  - PSM 수행

  - 명시적 또는 묵시적 커밋 발생

  - PSM 수행 중 에러 발생

Altibase 서버가 비정상 종료할 때 트레이스 로그에 아래와 같은 메시지가 기록됩니다.

*altibase_sm.log*

~~~bash
[2022/08/03 17:18:36 14C7F79][PID:7667][Thread-139792713553664][LWP-7670]
Invalid PSMSavepoint
~~~

*altibase\_error.log*

~~~bash
[2022/08/03 17:18:36 14C7F7A][PID:7667][Thread-139792713553664][LWP-7670]
IDE_Assert( 0 ), [smxSavepointMgr.cpp:664], errno=[11]
~~~

#### 재현 방법

-   재현 절차
-   수행 결과
-   예상 결과

#### Workaround

`없음`

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-49850 패키지 스펙의 변수를 기본값으로 하는 인자를 사용한 서브 프로그램을 다른 저장 프로시저 또는 저장 함수에서 호출할 때 ERR-31455 에러가 발생합니다.

#### module
`qp-PSM-trigger-pvo`

#### Category
`Memory Error`

#### 재현 빈도
`Always`

#### 설명
패키지 스펙의 변수를 기본값으로 하는 인자를 사용한 서브 프로그램을 다른 저장 프로시저 또는 저장 함수에서 호출할 때 ERR-31455 : Failed to work because an internal exception occurred from an OS.[Contact Altibase's Support Center] 에러가 발생하는 현상을 수정합니다.

#### 재현 방법

-   재현 절차

    ```sql
    DROP PACKAGE PGK1;
    DROP PROCEDURE PROC1;
    
    CREATE OR REPLACE PACKAGE PKG1 AS
    V2 INTEGER := 1;
    PROCEDURE SUB1( P1 IN INTEGER DEFAULT V2);
    END;
    /
    
    CREATE OR REPLACE PROCEDURE PROC1 AS
    BEGIN
    PKG1.SUB1;
    END;
    /
    ```

-   수행 결과

    ```sql
    [ERR-31455 : Failed to work because an internal exception occurred from an OS.[Contact Altibase's Support Center]]
    ```

-   예상 결과

    ```sql
    Create success.
    ```

#### Workaround

`없음`

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-49857 altibase.properties에서 TRANSACTION\_SEGMENT\_COUNT 프로퍼티의 최대값을 16384로 수정합니다.

#### module
`sm`

#### Category
`Other`

#### 재현 빈도
`Always`

#### 설명
altibase.properties에서 TRANSACTION\_SEGMENT\_COUNT 프로퍼티의 최대값을 16384로 수정합니다. TRANSACTION\_SEGMENT\_COUNT 프로퍼티의 최대값은 Altibase 7.1.0.7.3 부터 16384로 변경되었습니다. (관련 버그 : [BUG-49668](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.1/kor/Altibase_7_1_0_7_3_Patch_Notes.md#bug-49668%EB%8F%99%EC%8B%9C%EC%97%90-%EC%88%98%ED%96%89%ED%95%A0-%EC%88%98-%EC%9E%88%EB%8A%94-%EB%94%94%EC%8A%A4%ED%81%AC-%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98%EC%9D%98-%EC%B5%9C%EB%8C%80-%EC%88%98transaction_segment_count-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0%EC%9D%98-%EC%B5%9C%EB%8C%80%EA%B0%92%EB%A5%BC-512%EC%97%90%EC%84%9C-16384%EB%A1%9C-%EC%A6%9D%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4))

*Altibase 7.1.0.7.9 이하*

```bash
$ grep TRANSACTION_SEGMENT_COUNT $ALTIBASE_HOME/conf/altibase.properties
TRANSACTION_SEGMENT_COUNT = 256 # ( 1 ~ 512 )
```

*Altibase 7.1.0.8.0 이상*

```bash
$ grep TRANSACTION_SEGMENT_COUNT $ALTIBASE_HOME/conf/altibase.properties
TRANSACTION_SEGMENT_COUNT = 256 # ( 1 ~ 16384 )
```

### BUG-49867 디스크 인덱스 생성 시 altibase_sm.log에 [IDX_CRE] 2. Merge 메시지가 출력된 후 무한 대기하는 현상이 발생합니다.

#### module
`sm-disk-page`

#### Category
`Hang`

#### 재현 빈도
`Always`

#### 설명
디스크 인덱스 생성 시 디스크 버퍼 풀의 가용 공간을 사용하지 못하고 무한 대기하는 현상을 수정합니다. 지연된 플러시 리스트(delayed flush list)의 더티 페이지(Dirty Page)가 디스크에 반영되는 조건을 개선하였습니다. 

#### 재현 방법

-   재현 절차
-   수행 결과
-   예상 결과

#### Workaround

`없음`

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-49868 EXECUTE\_STMT\_MEMORY\_MAXIMUM 초과로 재컴파일이 실패한 뷰 사용 시 발생하는 안정성 문제를 개선합니다.

#### module
`qp-ddl-dcl-execute`

#### Category
`Fatal`

#### 재현 빈도
`Always`

#### 설명

뷰의 부질의에 사용된 객체에 DDL이 수행될 때 EXECUTE\_STMT\_MEMORY\_MAXIMUM 초과로 뷰의 재컴파일이 실패하면, 뷰의 상태가 비정상적인 상태로 남아 해당 뷰 사용 시 Altibase 서버의 비정상 종료를 유발하는 문제를 수정합니다.

메모리 제약으로 뷰의 재컴파일이 실패하면 DDL을 실패 처리하여 Altibase 서버가 비정상 종료하는 현상이 발생하지 않도록 개선하였습니다.

이 버그의 반영 전/후 변경 사항은 아래와 같습니다.

*버그 반영 전*

- 메모리 제약으로 뷰의 재컴파일이 실패하더라도 DDL 수행은 성공합니다. 

- 뷰는 재컴파일을 완료하지 않은 비정상적인 상태로 남습니다.

*버그 반영 후*

- 메모리 제약으로 뷰의 재컴파일이 실패하면 DDL을 실패 처리합니다. 

- 사용자는 EXECUTE\_STMT\_MEMORY\_MAXIMUM 프로퍼티를 조정 후 DDL을 다시 수행해야 합니다.

#### 재현 방법

-   재현 절차

    ```sql
    ALTER SYSTEM SET EXECUTE_STMT_MEMORY_MAXIMUM = 1048576;
    
    CREATE TABLE T1 
    ( I1 INTEGER,
      I2 INTEGER 
    ) 
    PARTITION BY RANGE(I1) 
    ( 
      PARTITION P1 VALUES DEFAULT
    );
      
    CREATE VIEW V1 AS SELECT * FROM T1;
    
    DROP TABLE T1;
    
    CREATE TABLE T1 
    ( I1 INTEGER, 
      I2 INTEGER, 
      I3 INTEGER 
    ) 
    PARTITION BY RANGE(I1) 
    ( 
      PARTITION P1 VALUES DEFAULT
    );
    
    SELECT * FROM V1;
    ```

-   수행 결과

    ```sql
    iSQL> CREATE TABLE T1 
    ( I1 INTEGER, 
      I2 INTEGER, 
      I3 INTEGER 
    ) 
    PARTITION BY RANGE(I1) 
    ( 
      PARTITION P1 VALUES DEFAULT
    );
    Create success.
    
    iSQL> SELECT * FROM V1;
    [ERR-31455 : Failed to work because an internal exception occurred from an OS.[Contact Altibase's Support Center]]
    ```

-   예상 결과

    ```sql
    iSQL> CREATE TABLE T1 
    ( I1 INTEGER, 
      I2 INTEGER, 
      I3 INTEGER 
    ) 
    PARTITION BY RANGE(I1) 
    ( 
      PARTITION P1 VALUES DEFAULT
    );
    [ERR-01067 : The memory size allocated for the statement has exceeded the maximum limit ( Name : Query_Execute, Wanted Memory Size : 1114112, Max size : 1048576 ).]
    
    iSQL> ALTER SYSTEM SET EXECUTE_STMT_MEMORY_MAXIMUM = 10485760;
    Alter success.
    
    iSQL> CREATE TABLE T1 ( I1 INTEGER, I2 INTEGER, I3 INTEGER ) PARTITION BY RANGE(I1) ( PARTITION P1 VALUES DEFAULT  );
    Create success.
    
    iSQL> SELECT * FROM V1;
    I1          I2          I3          
    ----------------------------------------
    No rows selected.
    ```

#### Workaround

`없음`

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-49894 aexport 수행 시 TYPESET 객체가 추출되지 않습니다.

#### module
`ux-aexport`

#### Category
`Functional Error`

#### 재현 빈도
`Always`

#### 설명
aexport 수행 시 TYPESET 객체가 추출되지 않는 문제를 수정합니다.

#### 재현 방법

-   재현 절차

    ```sql
    CREATE TYPESET type1
    AS
      TYPE rec1 IS RECORD (c1 INTEGER, c2 INTEGER);
      TYPE arr1 IS TABLE OF rec1 INDEX BY INTEGER;
    END;
    /
    CREATE FUNCTION func1(i1 INTEGER)
    RETURN type1.arr1
    AS
      v1 type1.arr1;
    BEGIN
      for i in 1 .. i1 loop
        v1[i].c1 := i;
        v1[i].c2 := i * i;
      END LOOP;
      RETURN v1;
    END;
    /
    ```

    ```bash
    $ aexport -u sys -p manager -s localhost
    $ grep TYPE1 *.sql
    ```

-   수행 결과

    ```bash
    $ grep TYPE1 *.sql
    ALL_OBJECT.sql:RETURN TYPE1.ARR1
    ALL_OBJECT.sql:  V1 TYPE1.ARR1;
    ```

-   예상 결과

    ```bash
    $ grep TYPE1 *.sql
    ALL_CRT_VIEW_PROC.sql:CREATE TYPESET TYPE1
    ALL_CRT_VIEW_PROC.sql:RETURN TYPE1.ARR1
    ALL_CRT_VIEW_PROC.sql:  V1 TYPE1.ARR1;
    ```

#### Workaround

`없음`

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    7.1.0.8.0     |          6.5.1          |    8.10.1    |        7.1.7        |            7.4.7             |

> Altibase 7.1 패치 버전별 히스토리는 [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.1/Altibase_7_1_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

> 패치를 롤백하려는 경우, [메타다운그레이드](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Installation.md#%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9Cmeta-downgrade)를 참고한다.

#### CM protocol Version

통신 프로토콜 버전은 변경되지 않았다.

#### Replication protocol Version

Replication 프로토콜 버전은 변경되지 않았다.

### 프로퍼티

#### 추가된 프로퍼티

- [REPLICATION\_SENDER\_IP](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase\_7.1/kor/General%20Reference-1.Data%20Types%20%26%20Altibase%20Properties.md\#replication\_sender\_ip)

#### 변경된 프로퍼티

#### 삭제된 프로퍼티

### 성능 뷰

#### 추가된 성능 뷰

#### 변경된 성능 뷰

#### 삭제된 성능 뷰
