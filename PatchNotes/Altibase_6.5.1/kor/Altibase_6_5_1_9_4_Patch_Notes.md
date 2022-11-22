Altibase 6.5.1.9.4 Patch Notes
==============================

<br/>

<br/>

# Table of Contents

- [New Features](#new-features)
  - [BUG-49904 이중화 송신자에게 고정 IP 주소를 할당하는 기능을 추가합니다.](#bug-49904%EC%9D%B4%EC%A4%91%ED%99%94-%EC%86%A1%EC%8B%A0%EC%9E%90%EC%97%90%EA%B2%8C-%EA%B3%A0%EC%A0%95-ip-%EC%A3%BC%EC%86%8C%EB%A5%BC-%ED%95%A0%EB%8B%B9%ED%95%98%EB%8A%94-%EA%B8%B0%EB%8A%A5%EC%9D%84-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
- [Fixed Bugs](#fixed-bugs)
  - [BUG-48624 ​타입 세트 재생성과 PSM 간 동시성 문제로 발생하는 안정성 문제를 개선합니다.](#bug-48624%E2%80%8B%ED%83%80%EC%9E%85-%EC%84%B8%ED%8A%B8-%EC%9E%AC%EC%83%9D%EC%84%B1%EA%B3%BC-psm-%EA%B0%84-%EB%8F%99%EC%8B%9C%EC%84%B1-%EB%AC%B8%EC%A0%9C%EB%A1%9C-%EB%B0%9C%EC%83%9D%ED%95%98%EB%8A%94-%EC%95%88%EC%A0%95%EC%84%B1-%EB%AC%B8%EC%A0%9C%EB%A5%BC-%EA%B0%9C%EC%84%A0%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49825 NORMALFORM\_MAXIMUM 프로퍼티가 0 일 때, PARALLEL을 지정한 테이블과 서브쿼리가 있는 질의문 수행 시 발생하는 안정성 문제를 개선합니다.](#bug-49825normalform_maximum-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0%EA%B0%80-0-%EC%9D%BC-%EB%95%8C-parallel%EC%9D%84-%EC%A7%80%EC%A0%95%ED%95%9C-%ED%85%8C%EC%9D%B4%EB%B8%94%EA%B3%BC-%EC%84%9C%EB%B8%8C%EC%BF%BC%EB%A6%AC%EA%B0%80-%EC%9E%88%EB%8A%94-%EC%A7%88%EC%9D%98%EB%AC%B8-%EC%88%98%ED%96%89-%EC%8B%9C-%EB%B0%9C%EC%83%9D%ED%95%98%EB%8A%94-%EC%95%88%EC%A0%95%EC%84%B1-%EB%AC%B8%EC%A0%9C%EB%A5%BC-%EA%B0%9C%EC%84%A0%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49846 패키지의 시노님을 사용한 질의문을 반복 수행 시 하드 파싱이 발생합니다.](#bug-49846%ED%8C%A8%ED%82%A4%EC%A7%80%EC%9D%98-%EC%8B%9C%EB%85%B8%EB%8B%98%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%9C-%EC%A7%88%EC%9D%98%EB%AC%B8%EC%9D%84-%EB%B0%98%EB%B3%B5-%EC%88%98%ED%96%89-%EC%8B%9C-%ED%95%98%EB%93%9C-%ED%8C%8C%EC%8B%B1%EC%9D%B4-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49851 SQLDriverConnect 함수에서 연결 속성 TIMEOUT의 값을 0으로 설정하면 Connection Timeout Error 에러가 발생할 수 있습니다.](#bug-49851sqldriverconnect-%ED%95%A8%EC%88%98%EC%97%90%EC%84%9C-%EC%97%B0%EA%B2%B0-%EC%86%8D%EC%84%B1-timeout%EC%9D%98-%EA%B0%92%EC%9D%84-0%EC%9C%BC%EB%A1%9C-%EC%84%A4%EC%A0%95%ED%95%98%EB%A9%B4-connection-timeout-error-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-49939 GROUP BY GROUPING SETS 절과 ORDER BY NULLS FIRST 절 또는 ORDER BY NULLS LAST 절을 같이 사용할 때 ERR-31001 : SQL syntax error 에러가 발생합니다.](#bug-49939group-by-grouping-sets-%EC%A0%88%EA%B3%BC-order-by-nulls-first-%EC%A0%88-%EB%98%90%EB%8A%94-order-by-nulls-last-%EC%A0%88%EC%9D%84-%EA%B0%99%EC%9D%B4-%EC%82%AC%EC%9A%A9%ED%95%A0-%EB%95%8C-err-31001--sql-syntax-error-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49942 디스크 트랜잭션의 롤백과 핑퐁 체크포인트의 동시성 문제로 Altibase 서버 구동이 실패할 수 있습니다.](#bug-49942%EB%94%94%EC%8A%A4%ED%81%AC-%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98%EC%9D%98-%EB%A1%A4%EB%B0%B1%EA%B3%BC-%ED%95%91%ED%90%81-%EC%B2%B4%ED%81%AC%ED%8F%AC%EC%9D%B8%ED%8A%B8%EC%9D%98-%EB%8F%99%EC%8B%9C%EC%84%B1-%EB%AC%B8%EC%A0%9C%EB%A1%9C-altibase-%EC%84%9C%EB%B2%84-%EA%B5%AC%EB%8F%99%EC%9D%B4-%EC%8B%A4%ED%8C%A8%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-49949 에러 코드 0x51098의 에러 메시지에 부정확한 사용자 입력 값이 출력될 수 있습니다.](#bug-49949%EC%97%90%EB%9F%AC-%EC%BD%94%EB%93%9C-0x51098%EC%9D%98-%EC%97%90%EB%9F%AC-%EB%A9%94%EC%8B%9C%EC%A7%80%EC%97%90-%EB%B6%80%EC%A0%95%ED%99%95%ED%95%9C-%EC%82%AC%EC%9A%A9%EC%9E%90-%EC%9E%85%EB%A0%A5-%EA%B0%92%EC%9D%B4-%EC%B6%9C%EB%A0%A5%EB%90%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-49973 DEQUEUE 병렬 수행 시 성능 저하 현상을 개선합니다.](#bug-49973DEQUEUE-병렬-수행-시-성능-저하-현상을-개선합니다)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
  - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
  - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)



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

이 기능을 사용하려면 Altibase 서버 프로퍼티 REPLICATION\_SENDER\_IP를 설정해야 합니다.

프로퍼티 설명 및 사용 방법은 Altibase 7.1 매뉴얼을 참고하시기 바랍니다.

- [Altibase 7.1 General Reference-1.Data Types & Altibase Properties](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase\_7.1/kor/General%20Reference-1.Data%20Types%20%26%20Altibase%20Properties.md\#replication\_sender\_ip)

- [Altibase 7.1 Replication Manual](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase\_7.1/kor/Replication%20Manual.md\#%EC%86%A1%EC%8B%A0%EC%9E%90-ip-%EC%A3%BC%EC%86%8C-%EC%84%A4%EC%A0%95)

#### 변경사항

-   Performance view
-   Property
    -   `REPLICATION_SENDER_IP`

        이중화 송신자의 IP 주소를 설정하는 프로퍼티이다. 값으로 ANY나 IP 주소를 입력할 수 있다.

        기본값 ANY는 이중화 객체를 생성하는 지역 서버의 모든 IP 주소가 이중화 통신에 사용될 수 있으며 OS에서 할당한 IP 주소가 송신자 IP 주소로 사용된다. IP 주소를 값으로 설정하면 원격 서버(수신자)와 통신할 때 설정한 IP 주소만 사용된다. REPLICATION_SENDER_IP = *value*를 추가하여 여러 개의 IP 주소를 설정할 수 있으며 순서대로 송신자 IP 주소로 사용된다. IP 주소는 IPv4, IPv6, IPv6 확장 주소 형태로 입력할 수 있다. 이 프로퍼티는 Altibase 6.5.1.9.4 부터 지원하며 이중화 통신 방법이 TCP일 때 적용된다.

-   Compile Option
-   Error Code

Fixed Bugs
==========

### BUG-48624 ​타입 세트 재생성과 PSM 간 동시성 문제로 발생하는 안정성 문제를 개선합니다.

#### module

`qp-psm-trigger-execute`

#### Category

`Fatal`

#### 재현 빈도

`Rare`

#### 설명

PSM에서 타입 세트 또는 패키지 스펙을 참조할 때, 한 세션에서 해당 타입 세트 또는 패키지 스펙을 재생성하고 또 다른 세션에서 PSM을 반복 수행했을 때 Altibase 서버가 비정상 종료하는 현상을 수정합니다.

#### 재현 방법

-   **재현 절차**

-   **수행 결과**

-   **예상 결과**

#### Workaround

`없음`

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

-   **재현 절차**

-   **수행 결과**

-   **예상 결과**

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

질의 처리 과정에서 패키지의 시노님의 정당성 검사(Validation) 누락으로 SQL Plan Cache에 등록된 실행 계획을 공유하지 않아 하드
파싱이 발생합니다.

이 버그 반영 후에는 패키지의 시노님을 사용한 질의문을 반복 수행 시 실행 계획 생성 이후 패키지가 변경되지 않았다면 소프트 파싱합니다.

#### 재현 방법

-   **재현 절차**

    ```sql
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
    ```

-   **수행 결과**

    ```sql
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
    ```

-   **예상 결과**

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

### BUG-49851 SQLDriverConnect 함수에서 연결 속성 TIMEOUT의 값을 0으로 설정하면 Connection Timeout Error 에러가 발생할 수 있습니다.

#### module

`mm-cli`

#### Category

`Functional Error`

#### 재현 빈도

`Always`

#### 설명

Altibase CLI의 SQLDriverConnect 함수에서 연결 속성 TIMEOUT의 값을 0으로 설정하면 Connection Timeout Error 에러가 발생하는 현상을 수정합니다. 이 버그는 OS와 무관하게 노출되어 있으나, 버그 현상은 Windows 환경에서 Altibase 서버로 원격 접속할 때 항상 발생합니다.

이 버그를 적용하려면 Altibase CLI 라이브러리를 패치해야 합니다.

- Linux/Unix 클라이언트 : libodbccli.a, libodbccli\_sl.so

- Windows 클라이언트 : altiodbc.dll


#### 재현 방법

-   **재현 절차**

    Windows 클라이언트에서 아래와 같이 접속 시 재현됩니다.

    ```c
    rc = SQLDriverConnect(dbc, NULL,
                              (SQLCHAR *)"Server=127.0.0.1;User=SYS;Password=MANAGER;TIMEOUT=0", SQL_NTS,
                              NULL, 0, NULL, SQL_DRIVER_NOPROMPT);
    ```

-   **수행 결과**

    ```c
    Connection Timeout Error
    ```

-   **예상 결과**

    ```c
    Connection success
    ```

#### Workaround

`없음`

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-49939 GROUP BY GROUPING SETS 절과 ORDER BY NULLS FIRST 절 또는 ORDER BY NULLS LAST 절을 같이 사용할 때 ERR-31001 : SQL syntax error 에러가 발생합니다.

#### module

`qp-select`

#### Category

`Functional Error`

#### 재현 빈도

`Always`

#### 설명

GROUP BY GROUPING SETS 절과 ORDER BY NULLS FIRST 절 또는 ORDER BY NULLS LAST 절을 같이 사용할 때 ERR-31001 : SQL syntax error 에러가 발생하는 현상을 수정합니다.

-   **재현 방법**

    -   **재현 절차**

        ```sql
        DROP TABLE BUG_49939;
        
        CREATE TABLE BUG_49939 ( C1 VARCHAR(10), C2 VARCHAR(10), C3 VARCHAR(10));
        
        INSERT INTO BUG_49939 VALUES(1,1,1);
        INSERT INTO BUG_49939 VALUES(1,2,1);
        INSERT INTO BUG_49939 VALUES(2,2,2);
        INSERT INTO BUG_49939 VALUES(1,3,2);
        INSERT INTO BUG_49939 VALUES(2,1,1);
        INSERT INTO BUG_49939 VALUES(2,3,2);
        
        SELECT A1.C1, A1.C2, A1.C3
          FROM BUG_49939 A1
         GROUP BY GROUPING SETS ((A1.C1, A1.C2, A1.C3), ())
         ORDER BY A1.C1 NULLS FIRST, A1.C3 NULLS FIRST;
        ```

    -   **수행 결과**

        ```sql
        [ERR-31001 : SQL syntax error 
        
        line 4: missing or invalid syntax
         ORDER BY A1.C1 NULLS FIRST, A1.C3 NULLS FIRST
                        ^   ^
        
        ]
        ```

    -   **예상 결과**

        ```sql
        C1                    C2                    C3                    
        ----------------------------------------------------------------------
                                                                          
        1                     1                     1                     
        1                     2                     1                     
        1                     3                     2                     
        2                     1                     1                     
        2                     2                     2                     
        2                     3                     2                     
        7 rows selected.
        ------------------------------------------------------------
        ```

-   **Workaround**

    아래와 같이 쿼리를 변환하여 버그를 회피할 수 있습니다.

    ```sql
    SELECT A1.C1, A1.C2, A1.C3
     FROM BUG_49939 A1
    GROUP BY A1.C1, A1.C2, A1.C3
    UNION ALL
    SELECT NULL C1, NULL C2, NULL C3
     FROM BUG_49939 A1
    GROUP BY NULL
    ORDER BY C1 NULLS FIRST, C3 NULLS FIRST;
    ```

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49942 디스크 트랜잭션의 롤백과 핑퐁 체크포인트의 동시성 문제로 Altibase 서버 구동이 실패할 수 있습니다.

#### module

`sm-mem-recovery`

#### Category

`Fatal`

#### 재현 빈도

`Always`

#### 설명

디스크 트랜잭션의 롤백과 핑퐁 체크포인트(ping-pong checkpoint)의 동시성 문제를 수정합니다. 
Altibase 서버 운용 중에 아래와 같은 상황이 발생하면 로그 앵커(Log Anchor) 파일에 안정적인(stable) 체크포인트 이미지 파일 정보가 변경되지 않습니다. 이에 따라 Altibase 서버 구동이 실패하거나 Altibase 서버 운용 중 예상할 수 없는 문제가 발생할 수 있습니다.

- 디스크 트랜잭션의 롤백과 메모리 DB의 핑퐁 체크포인트가 동시 수행
- 이후 Altibase 서버 중지

#### 재현 방법

-   **재현 절차**

-   **수행 결과**

-   **예상 결과**


#### Workaround

`없음`

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-49949 에러 코드 0x51098의 에러 메시지에 부정확한 사용자 입력 값이 출력될 수 있습니다.

#### module
`mm-cli`

#### Category
`Message Error`

#### 재현 빈도
`Always`

#### 설명

에러 코드 0x51098의 에러 메시지에 부정확한 사용자 입력 값이 출력되는 문제를 수정합니다.

#### 재현 방법

- **재현 절차**

-   **수행 결과**

-   **예상 결과**

#### Workaround
`없음`

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-49973 DEQUEUE 병렬 수행 시 성능 저하 현상을 개선합니다.

#### module
`sm`

#### Category
`Efficiency`

#### 재현 빈도
`Always`

#### 설명
8개 이상 클라이언트에서 DEQUEUE를 동시에 수행할 경우 성능이 하락하는 현상이 있습니다. 병렬로 DEQUEUE 수행 시 발생하는 병목을 제거하여 성능을 개선합니다. 

이 버그를 처리하면서 추가되거나 중단된 사항입니다.

- CREATE QUEUE 및 ALTER QUEUE 구문에 DELETE 절 추가

  - DELETE ON

    - 큐(QUEUE) 테이블에 DELETE 문을 허용합니다.

    - DELETE 문을 허용하지 않은 경우보다 DEQUEUE 병렬 수행 성능이 저하됩니다.


  - DELETE OFF
    - 큐 테이블에 DELETE 문을 수행할 수 없습니다.
      - DELETE 문을 허용한 경우보다 DEQUEUE 병렬 수행 성능이 향상됩니다. 

- V\$QUEUE\_DELETE\_OFF 성능 뷰 추가

  DELETE 문을 허용하지 않는 큐 테이블을 조회할 수 있습니다.

- 디스크 큐 테이블 지원하지 않습니다.

  CREATE QUEUE 구문에서 디스크 테이블스페이스 지정 시 ERR-314AA : Failed to create queue table in disk tablespace. 에러가 발생합니다.

관련 내용은 Altibase 7.1 매뉴얼을 참고하시기 바랍니다. 

- [Altibase 7.1 SQL Reference : CREATE QUEUE 구문](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/SQL%20Reference.md#create-queue)
- [Altibase 7.1 SQL Reference : ALTER QUEUE 구문](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/SQL%20Reference.md#alter-queue)
- [Altibase 7.1 General_Reference-2.The Data Dictionary](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/General%20Reference-2.The%20Data%20Dictionary.md#vqueue_delete_off)

#### 재현 방법

- **재현 절차**

-   **수행 결과**

-   **예상 결과**

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
|    6.5.1.9.4     |          6.3.1          |    8.1.1     |        7.1.3        |            7.4.5             |

> Altibase 6.5.1 패치 버전별 히스토리는 [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_6.5.1/Altibase_6_5_1_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

#### CM protocol Version

통신 프로토콜 버전은 변경되지 않았다.

#### Replication protocol Version

Replication 프로토콜 버전은 변경되지 않았다.

### 프로퍼티

#### 추가된 프로퍼티

- [REPLICATION_SENDER_IP](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/General%20Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#replication_sender_ip)

#### 변경된 프로퍼티

#### 삭제된 프로퍼티

### 성능 뷰

#### 추가된 성능 뷰

- [V\$QUEUE\_DELETE\_OFF](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/General%20Reference-2.The%20Data%20Dictionary.md#vqueue_delete_off)

#### 변경된 성능 뷰

#### 삭제된 성능 뷰
