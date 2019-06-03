<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Altibase 7.1.0.2.1 Patch Notes](#altibase-71021-patch-notes)
  - [New Features](#new-features)
    - [BUG-46702  with rollup 구문 지원](#bug-46702-with-rollup-%EA%B5%AC%EB%AC%B8-%EC%A7%80%EC%9B%90)
    - [BUG-46806  INSERT 구문에 alias 지원](#bug-46806-insert-%EA%B5%AC%EB%AC%B8%EC%97%90-alias-%EC%A7%80%EC%9B%90)
    - [BUG-46703  limit clause에 simple expression 지원.](#bug-46703-limit-clause%EC%97%90-simple-expression-%EC%A7%80%EC%9B%90)
    - [BUG-46719  SYSDATETIME 지원](#bug-46719-sysdatetime-%EC%A7%80%EC%9B%90)
    - [BUG-46727  ISO 표준 기준 년 IYYY format 지원](#bug-46727-iso-%ED%91%9C%EC%A4%80-%EA%B8%B0%EC%A4%80-%EB%85%84-iyyy-format-%EC%A7%80%EC%9B%90)
    - [BUG-46755  호스트 네임으로 발급된 라이선스 적용](#bug-46755-%ED%98%B8%EC%8A%A4%ED%8A%B8-%EB%84%A4%EC%9E%84%EC%9C%BC%EB%A1%9C-%EB%B0%9C%EA%B8%89%EB%90%9C-%EB%9D%BC%EC%9D%B4%EC%84%A0%EC%8A%A4-%EC%A0%81%EC%9A%A9)
    - [BUG-46826  DDL PVO 안정성 개선](#bug-46826-ddl-pvo-%EC%95%88%EC%A0%95%EC%84%B1-%EA%B0%9C%EC%84%A0)
    - [BUG-46781  이중화 DDL 안전성 개선](#bug-46781-%EC%9D%B4%EC%A4%91%ED%99%94-ddl-%EC%95%88%EC%A0%84%EC%84%B1-%EA%B0%9C%EC%84%A0)
    - [BUG-46825  OTHER_DATABASE_SKIP_ERROR 와 ORACLE_SKIP_ERROR 정책변경](#bug-46825-other_database_skip_error-%EC%99%80-oracle_skip_error-%EC%A0%95%EC%B1%85%EB%B3%80%EA%B2%BD)
    - [BUG-46832  memory partition table 의 simple query 최적화](#bug-46832-memory-partition-table-%EC%9D%98-simple-query-%EC%B5%9C%EC%A0%81%ED%99%94)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-46208  REPLICATION\_SENDER\_AUTO\_START 값이 설정되어 있는 상태에서 서버 시작를 못할수 있습니다.](#bug-46208-replication%5C_sender%5C_auto%5C_start-%EA%B0%92%EC%9D%B4-%EC%84%A4%EC%A0%95%EB%90%98%EC%96%B4-%EC%9E%88%EB%8A%94-%EC%83%81%ED%83%9C%EC%97%90%EC%84%9C-%EC%84%9C%EB%B2%84-%EC%8B%9C%EC%9E%91%EB%A5%BC-%EB%AA%BB%ED%95%A0%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-46670  temp flusher에서 이미 free된 temp table header에 접근 할 수 있습니다.](#bug-46670-temp-flusher%EC%97%90%EC%84%9C-%EC%9D%B4%EB%AF%B8-free%EB%90%9C-temp-table-header%EC%97%90-%EC%A0%91%EA%B7%BC-%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-46680  INSERT\_REPLACE가 1로 되어 있을때 CLOB이 포함된 Table에 Replcation SYNC를 두번 수행하면 lock timeout이 발생합니다.](#bug-46680-insert%5C_replace%EA%B0%80-1%EB%A1%9C-%EB%90%98%EC%96%B4-%EC%9E%88%EC%9D%84%EB%95%8C-clob%EC%9D%B4-%ED%8F%AC%ED%95%A8%EB%90%9C-table%EC%97%90-replcation-sync%EB%A5%BC-%EB%91%90%EB%B2%88-%EC%88%98%ED%96%89%ED%95%98%EB%A9%B4-lock-timeout%EC%9D%B4-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-46697  hash partition 이중화 시 이중화 재시작을 하면 partition 갯수를 찾지 못해 handshake 가 되지 않습니다.](#bug-46697-hash-partition-%EC%9D%B4%EC%A4%91%ED%99%94-%EC%8B%9C-%EC%9D%B4%EC%A4%91%ED%99%94-%EC%9E%AC%EC%8B%9C%EC%9E%91%EC%9D%84-%ED%95%98%EB%A9%B4-partition-%EA%B0%AF%EC%88%98%EB%A5%BC-%EC%B0%BE%EC%A7%80-%EB%AA%BB%ED%95%B4-handshake-%EA%B0%80-%EB%90%98%EC%A7%80-%EC%95%8A%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-46700  메모리 테이블의 LOB컬럼 UPDATE시 메모리 테이블 사이즈가 계속 증가할 수 있는 문제 수정](#bug-46700-%EB%A9%94%EB%AA%A8%EB%A6%AC-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%9D%98-lob%EC%BB%AC%EB%9F%BC-update%EC%8B%9C-%EB%A9%94%EB%AA%A8%EB%A6%AC-%ED%85%8C%EC%9D%B4%EB%B8%94-%EC%82%AC%EC%9D%B4%EC%A6%88%EA%B0%80-%EA%B3%84%EC%86%8D-%EC%A6%9D%EA%B0%80%ED%95%A0-%EC%88%98-%EC%9E%88%EB%8A%94-%EB%AC%B8%EC%A0%9C-%EC%88%98%EC%A0%95)
    - [BUG-46708  윈도우 OS에서는 altilinker 실행시 java파일이 아니라 java.exe파일을 찾도록 수정해야 합니다.](#bug-46708-%EC%9C%88%EB%8F%84%EC%9A%B0-os%EC%97%90%EC%84%9C%EB%8A%94-altilinker-%EC%8B%A4%ED%96%89%EC%8B%9C-java%ED%8C%8C%EC%9D%BC%EC%9D%B4-%EC%95%84%EB%8B%88%EB%9D%BC-javaexe%ED%8C%8C%EC%9D%BC%EC%9D%84-%EC%B0%BE%EB%8F%84%EB%A1%9D-%EC%88%98%EC%A0%95%ED%95%B4%EC%95%BC-%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-46728  order by 절에 사용된 host 변수를 target과 같은 varchar로 지정하도록 수정](#bug-46728-order-by-%EC%A0%88%EC%97%90-%EC%82%AC%EC%9A%A9%EB%90%9C-host-%EB%B3%80%EC%88%98%EB%A5%BC-target%EA%B3%BC-%EA%B0%99%EC%9D%80-varchar%EB%A1%9C-%EC%A7%80%EC%A0%95%ED%95%98%EB%8F%84%EB%A1%9D-%EC%88%98%EC%A0%95)
    - [BUG-46731  simple query를 사용하는 insert문에도 nowait에 대한 고려가 필요합니다.](#bug-46731-simple-query%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94-insert%EB%AC%B8%EC%97%90%EB%8F%84-nowait%EC%97%90-%EB%8C%80%ED%95%9C-%EA%B3%A0%EB%A0%A4%EA%B0%80-%ED%95%84%EC%9A%94%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-46754  server restart 시 logfile0 이 없어서 서버가 시작 하지 못 합니다.](#bug-46754-server-restart-%EC%8B%9C-logfile0-%EC%9D%B4-%EC%97%86%EC%96%B4%EC%84%9C-%EC%84%9C%EB%B2%84%EA%B0%80-%EC%8B%9C%EC%9E%91-%ED%95%98%EC%A7%80-%EB%AA%BB-%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-46757  V$DB_PROTOCOL 조회시 이상한 문자가 출력됩니다.](#bug-46757-vdb_protocol-%EC%A1%B0%ED%9A%8C%EC%8B%9C-%EC%9D%B4%EC%83%81%ED%95%9C-%EB%AC%B8%EC%9E%90%EA%B0%80-%EC%B6%9C%EB%A0%A5%EB%90%A9%EB%8B%88%EB%8B%A4)
    - [BUG-46782  Begin transaction 디버깅 정보 추가.](#bug-46782-begin-transaction-%EB%94%94%EB%B2%84%EA%B9%85-%EC%A0%95%EB%B3%B4-%EC%B6%94%EA%B0%80)
    - [BUG-46800  ANTI JOIN시 INVERSE HASH로 PLAN생성 시 CONSTANT FILTER 처리](#bug-46800-anti-join%EC%8B%9C-inverse-hash%EB%A1%9C-plan%EC%83%9D%EC%84%B1-%EC%8B%9C-constant-filter-%EC%B2%98%EB%A6%AC)
    - [BUG-46805  target에 index를 타는 subquery 2개가 where문을 제외한 다른 부분이 같을 경우 결과 오류](#bug-46805-target%EC%97%90-index%EB%A5%BC-%ED%83%80%EB%8A%94-subquery-2%EA%B0%9C%EA%B0%80-where%EB%AC%B8%EC%9D%84-%EC%A0%9C%EC%99%B8%ED%95%9C-%EB%8B%A4%EB%A5%B8-%EB%B6%80%EB%B6%84%EC%9D%B4-%EA%B0%99%EC%9D%84-%EA%B2%BD%EC%9A%B0-%EA%B2%B0%EA%B3%BC-%EC%98%A4%EB%A5%98)
    - [BUG-46816  table name과 username이 128자 이상일 경우 메모리 침범이 발생합니다.](#bug-46816-table-name%EA%B3%BC-username%EC%9D%B4-128%EC%9E%90-%EC%9D%B4%EC%83%81%EC%9D%BC-%EA%B2%BD%EC%9A%B0-%EB%A9%94%EB%AA%A8%EB%A6%AC-%EC%B9%A8%EB%B2%94%EC%9D%B4-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-46836  simple query 최적화를 사용하는 환경에서 select for update 시에 nowait option 적용되지 않는 문제가 있습니다.](#bug-46836-simple-query-%EC%B5%9C%EC%A0%81%ED%99%94%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94-%ED%99%98%EA%B2%BD%EC%97%90%EC%84%9C-select-for-update-%EC%8B%9C%EC%97%90-nowait-option-%EC%A0%81%EC%9A%A9%EB%90%98%EC%A7%80-%EC%95%8A%EB%8A%94-%EB%AC%B8%EC%A0%9C%EA%B0%80-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Altibase 7.1.0.2.1 Patch Notes
==============================

New Features
------------

### BUG-46702  with rollup 구문 지원

- **module** : qp-dml-execute

- **Category** : Other

- **재현 빈도** : Always

- **증상** : with rollup 구문을 지원합니다.

- **재현 방법**
  - **재현 절차**

    ```
    drop table t1;
    create table t1 (i1 int,i2 int, i3 int, i4 int);
    insert into t1 values (1 , 2 , 3 , 0);
    insert into t1 values (1 , 2 , 3 , 0);
    insert into t1 values (1 , 2 , 5 , 0);
    insert into t1 values (1 , 3 , 7 , 0);
    insert into t1 values (2 , 3 , 9 , 0);
    select i1, i2, count( i4 ) from t1 group by i1,i2 with rollup  order by i2;
    ```

  - **수행 결과**

    ```

    iSQL> select i1, i2, count( i4 ) from t1 group by i1,i2 with rollup  order by i2;
    [ERR-31001 : SQL syntax error

    line 1: missing or invalid syntax
    select I1, I2, COUNT( I4 ) from T1 group by I1,I2 with rollup  order by i2
                                                           ^    ^

    ]
    ```

  - **예상 결과**

    ```
    iSQL> select i1, i2, count( i4 ) from t1 group by i1,i2 with rollup  order by i2;
    I1          I2          COUNT( I4 )
    -------------------------------------------------
    1           2           3
    1           3           1
    2           3           1
    1                       4
    2                       1
                            5
    6 rows selected.
    ```

- **Workaround**

  ```
  iSQL> select i1, i2, count( i4 ) from t1 group by rollup(i1,i2)  order by i2;
  I1          I2          COUNT( I4 )
  -------------------------------------------------
  1           2           3
  1           3           1
  2           3           1
  1                       4
  2                       1
                          5
  6 rows selected.
  ```

- **변경사항**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

### BUG-46806  INSERT 구문에 alias 지원

- **module** : qp-dml-execute

- **Category** : Other

- **재현 빈도** : Always

- **증상** : INSERT 구문에 alias를 사용할 수 있도록 수정하였습니다.

- **재현 방법**

  - **재현 절차**

    ```
    iSQL> insert into t1 a (a.i1) values (1);
    [ERR-31001 : SQL syntax error
    line 1: parse error
    insert into T1 A (A.I1) values (1)
                                   ^
    ]
    ```

  - **수행 결과**

  - **예상 결과**

    ```
    iSQL> insert into t1 a (a.i1) values (1);
    1 row inserted.
    ```

- **Workaround**

- **변경사항**

  - Performance view
  - Property
  - Compile Option
  - Error Code

### BUG-46703  limit clause에 simple expression 지원.

- **module** : qp-dml-pvo

- **Category** : Functionality

- **재현 빈도** : Always

- **증상** : Limit clause에 연산, function 호출, package 변수
  접근 등이 가능하도록 개선합니다.

- **재현 방법**

  - **재현 절차**

        drop table t1;
        create table t1 (i1 int,i2 int);
        insert into t1 values (1,1);
        insert into t1 values (2,2);
        select * from t1 limit 1+1;

  - **수행 결과**

    ```
    iSQL> select * from t1 limit 1+1;
    [ERR-31001 : SQL syntax error
    line 1: parse error
    select * from T1 limit 1+1
    ```

  - **예상 결과**

        iSQL> select * from t1 limit 1+1;
        I1          I2
        ---------------------------
        1           1
        2           2
        2 rows selected.

- **Workaround**

- **변경사항**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

### BUG-46719  SYSDATETIME 지원

-   **module** : qp

-   **Category** : Other

-   **재현 빈도** : Always

-   **증상** : SYSDATETIME을 지원합니다.

    altibase의 SYSDATE와 동일하며, 운영중인 시스템의 현재시간 날짜
    출력합니다.

- **재현 방법**

  - **재현 절차**

        iSQL> select sysdatetime from dual;
        [ERR-31058 : Column not found
        0001 : select SYSDATETIME from DUAL
                     ^^
        ]

  -   **수행 결과**

  - **예상 결과**

        iSQL> select sysdatetime from dual;
        SYSDATETIME
        ---------------
        21-JAN-2019
        1 row selected.

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-46727  ISO 표준 기준 년 IYYY format 지원

-   **module** : mt-function

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **증상** : DATE를 문자열로 표현할 때, IYYY IYY IY I 형식을
    추가합니다.

    ​1. SQL (TO\_CHAR FUNCTION)

        SELECT TO\_CHAR( date, 'IYYY' ) FROM T1 ORDER BY I1;

    ​2. SQL (DATE -\> CHAR ENCODE)

        ALTER SESSION SET DEFAULT\_DATE\_FORMAT = 'IYYY';

        SELECT date FROM T1 ORDER BY I1;

    ​3. CLI (DATE -\> CHAR CONVERT)

        (1) SQLDriverConnect   : DATE\_FORMAT=IYYY

        (2) Query              : SELECT date FROM T1 ORDER BY I1

        (3) SQLBindCol & Fetch : SQL\_C\_CHAR

- **재현 방법**

  - **재현 절차**

        iSQL> SELECT TO_CHAR(TO_DATE('2018-12-31','YYYY-MM-DD'), 'IYYY-IW') FROM DUAL;
        [ERR-21039 : The date format ( IYYY-IW ) was not recognized.
        0001 : SELECT TO_CHAR(TO_DATE('2018-12-31','YYYY-MM-DD'), 'IYYY-IW') FROM DUAL
                     ^                                                     ^
        ]

  - **수행 결과**

        [ERR-21039 : The date format ( IYYY-IW ) was not recognized.
        0001 : SELECT TO_CHAR(TO_DATE('2018-12-31','YYYY-MM-DD'), 'IYYY-IW') FROM DUAL
                     ^                                                     ^

  - **예상 결과**

        iSQL> SELECT TO_CHAR(TO_DATE('2018-12-31','YYYY-MM-DD'), 'IYYY-IW') FROM DUAL;
        TO_CHAR(TO_DATE('2018-12-31','YYYY-MM-DD')
        ----------------------------------------------
        2019-01
        1 row selected.

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-46755  호스트 네임으로 발급된 라이선스 적용

- **module** : id

- **Category** : Other

- **재현 빈도** : Always

- **증상** : 라이선스정책 변경(hostname으로도 License 발급가능)으로
  변경된 라이선스가 적용되도록 수정하였습니다. 기존에 MAC Address 를
  기반으로 발급하였는데,

  MAC Address 또는 HOST Name 을 이용해서 라이선스를 발급할 수 있도록
  변경되었습니다.

- **재현 방법**

  -   **재현 절차**

  -   **수행 결과**

  -   **예상 결과**

- **Workaround**

- **변경사항**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

### BUG-46826  DDL PVO 안정성 개선

- **module** : qp-ddl-dcl-pvo
- **Category** : Functionality
- **재현 빈도** : Always
- **증상** : DDL PVO 수행 중 내부적인 요인에 의한 FATAL이 발생는 경우,
  비정상종료하지 않도록 개선되었습니다.
- **재현 방법**
  - **재현 절차**
  - **수행 결과**
  - **예상 결과**
- **Workaround**
- **변경사항**
  - Performance view
  - Property
  - Compile Option
  - Error Code

### BUG-46781  이중화 DDL 안전성 개선

-   **module** : rp

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **증상** : 이중화 DDL 안전성 향상을 위한 개선사항을 적용합니다.

-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**
    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code
        -   399,rpERR\_ABORT\_FAULT\_TOLERATED = Failed to work because
            an internal exception occurred from an OS.[Contact
            Altibase's Support Center]</br>
             \# \*Cause: An internal exception occurred from an OS.</br>
             \# \*Action: Check the error number from the trace log for
            more detailed information. And contact Altibase's Support
            Center (http://support.altibase.com).

### BUG-46825  OTHER_DATABASE_SKIP_ERROR 와 ORACLE_SKIP_ERROR 정책변경

-   **module** : rp-jdbcAdapter

-   **Category** : Other

-   **재현 빈도** : Always

- **증상** : OTHER_DATABASE_SKIP_ERROR = 0 , ORACLE_SKIP_ERROR=0 인 경우, 기본적으로 에러를 스킵하지않되, 스킵해야하는 에러코드들을 dbms_skip_error_include.list 에
  기록할수 있도록 했습니다.

  OTHER_DATABASE_SKIP_ERROR = 1 , ORACLE_SKIP_ERROR=1 인 경우, 기본적으로 에러를 스킵하되, 스킵하면 안되는 에러코드들을 dbms_skip_error_exclude.list 에 기록할수
  있도록 했습니다.

-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-46832  memory partition table 의 simple query 최적화

- **module** : qp

- **Category** : Enhancement

- **재현 빈도** : Always

- **증상** : 기존에는 memory table에 대해서만 simple query 최적화를
  지원하였으나, memory partition table 의 경우도 지원하도록
  수정하였습니다.

  프로퍼티 EXECUTOR\_FAST\_SIMPLE\_QUERY =2 인경우에 사용가능합니다

- **재현 방법**

  -   **재현 절차**

  -   **수행 결과**

  -   **예상 결과**

- **Workaround**

- **변경사항**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

Fixed Bugs
----------

### BUG-46208  REPLICATION\_SENDER\_AUTO\_START 값이 설정되어 있는 상태에서 서버 시작를 못할수 있습니다.

-   **module** : rp

-   **Category** : Functional Error

-   **재현 빈도** : Rare

-   **증상** : 이중화 start시에 lock timeout을 0으로 해서 table lock을
    바로 획득하지 못하면 실패하도록 되어있습니다.

    Server start시 REPLICATION\_SENDER\_AUTO\_START가 설정되어 있으면
    이중화를 자동으로 start 시키는데

    receiver에서 table에 data를 execute 하기위해 lock을 잡고
    있면 sender가 start중 lock을 획득하지 못해 실패하게되고

    이로인해 server start도 실패 하게 됩니다.

    server start중에 이중화 sender를 start 시키는 경우에는 lock
    timeout을 무한대로 설정하여 receiver가 lock을 반환 할때 까지
    대기해서 server start가 실패하지 않도록 수정하였습니다.

-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-46670  temp flusher에서 이미 free된 temp table header에 접근 할 수 있습니다.

-   **module** : sm-disk-resource

-   **Category** : Fatal

-   **재현 빈도** : Unknown

-   **증상** : disk temp table에서 stress test 중에 통계정보 이슈로 temp
    table header 를 해제하고 나서 접근하는 문제가 있어서 해결
    하였습니다.

-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-46680  INSERT\_REPLACE가 1로 되어 있을때 CLOB이 포함된 Table에 Replcation SYNC를 두번 수행하면 lock timeout이 발생합니다.

-   **module** : dm

-   **Category** : Other

-   **재현 빈도** : Always

-   **증상** : INSERT\_REPLACE가 1로 되어 있을때 LOB이 포함된 Table에서
    Replcation SYNC를 두 번 수행하면 lock timeout이 발생하는 문제가
    있어, 이를 수정하였습니다.

-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-46697  hash partition 이중화 시 이중화 재시작을 하면 partition 갯수를 찾지 못해 handshake 가 되지 않습니다.

-   **module** : rp

-   **Category** : Testcase Fail

-   **재현 빈도** : Always

-   **증상** : 해시 파티션 이중화시 이중화를 중지했다가 재시작 하면 해시 파티션 갯수를 잘못 계산하여
    이중화가 되지 않는 문제가 있습니다. 이중화 재 시작시에 해시파티션 갯수를 바르게 찾아 이중화가 진행되도록 수정하였습니다.

-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-46700  메모리 테이블의 LOB컬럼 UPDATE시 메모리 테이블 사이즈가 계속 증가할 수 있는 문제 수정

-   **module** : sm

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : 메모리 테이블의 LOB컬럼 UPDATE시

    메모리 테이블 사이즈가 계속 증가할 수 있는 문제가 있어서
    수정하였습니다.

-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-46708  윈도우 OS에서는 altilinker 실행시 java파일이 아니라 java.exe파일을 찾도록 수정해야 합니다.

-   **module** : dblink

-   **Category** : Other

-   **재현 빈도** : Always

- **증상** : 윈도우 OS에서는 java파일이 아니라 java.exe 파일이 존재하여 dblink 실행시 java파일이 없는 것으로 판단하여 에러가 발생하였습니다.

  윈도우 OS에서는 java 파일이 아니라 java.exe 파일로 java 유무를 판단하도록 수정하였습니다.

-   **재현 방법**

    -   **재현 절차**

            dblink enable 후 server start

    -   **수행 결과**

            java 파일을 찾지 못하여 에러 발생

    -   **예상 결과**

            서버와 altilinker 정상적으로 구동

-   **Workaround**

        java.exe 파일을 복사하여 java파일을 만든다.

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-46728  order by 절에 사용된 host 변수를 target과 같은 varchar로 지정하도록 수정

-   **module** : qp-dml-execute

-   **Category** : Other

-   **재현 빈도** : Always

-   **증상** : order by 절에 사용된 host 변수를 target과 같은 varchar로
     지정하도록 수정

- **재현 방법**

  - **재현 절차**

        iSQL> VAR V1 VARCHAR(100);
        iSQL> EXEC :V1 := 'KO';
        Execute success.
        iSQL> print var;
        [ HOST VARIABLE ]
        -------------------------------------------------------
        NAME                 TYPE                 VALUE
        -------------------------------------------------------
        V1                   VARCHAR(100)         KO
        iSQL> PREPARE SELECT CASE WHEN :v1 ='KO' THEN 1 ELSE 2 END FROM DUAL;
        CASEWHEN:V1='KO'THEN1ELSE2END
        --------------------------------
        1           
        1 row selected.
        iSQL> PREPARE SELECT CASE WHEN :v1 ='KO' THEN 1 ELSE 2 END FROM DUAL ORDER BY (CASE WHEN :v1 ='KO' THEN 1 ELSE 2 END);
        [ERR-3123B : Invalid use of host variables
        0001 : SELECT CASE WHEN :v1 ='KO' THEN 1 ELSE 2 END FROM DUAL ORDER BY (CASE WHEN :v1 ='KO' THEN 1 ELSE 2 END)

  -   **수행 결과**

  - **예상 결과**

        iSQL> VAR V1 VARCHAR(100);
        iSQL> EXEC :V1 := 'KO';
        Execute success.
        iSQL> print var;
        [ HOST VARIABLE ]
        -------------------------------------------------------
        NAME                 TYPE                 VALUE
        -------------------------------------------------------
        V1                   VARCHAR(100)         KO
        iSQL> PREPARE SELECT CASE WHEN :v1 ='KO' THEN 1 ELSE 2 END FROM DUAL;
        CASEWHEN:V1='KO'THEN1ELSE2END
        --------------------------------
        1           
        1 row selected.
        iSQL> PREPARE SELECT CASE WHEN :v1 ='KO' THEN 1 ELSE 2 END FROM DUAL ORDER BY (CASE WHEN :v1 ='KO' THEN 1 ELSE 2 END);
        CASEWHEN:V1='KO'THEN1ELSE2END
        --------------------------------
        1           
        1 row selected.

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-46731  simple query를 사용하는 insert문에도 nowait에 대한 고려가 필요합니다.

-   **module** : qp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : simple query를 사용하는 insert문에서 nowait이 적용되지
    않는 문제를 수정하였습니다.

-   **재현 방법**
    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**
    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-46754  server restart 시 logfile0 이 없어서 서버가 시작 하지 못 합니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Rare

-   **증상** : 리커버리 시작위치에 고려해야하는
    요소가 추가되었으나 불필요한 로그파일 제거 루틴에서는 추가된 요소에 대한 처리가 누락되었습니다. 해당 요소를 고려하도록 수정합니다.

-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-46757  V$DB_PROTOCOL 조회시 이상한 문자가 출력됩니다.

-   **module** : cm

-   **Category** : Functional Error

-   **재현 빈도** : Always

- **증상** : V\$DB\_PROTOCOL 조회시 추가된 프로토콜에 대한 정의가 코드에서 빠져 있어

  이상한 문자열이 출력 되는 문제가 존재 하였습니다.

  추가된 프로토콜에 대하여 정의를 코드에 추가 하여 수정하였습니다.

- **재현 방법**

  -   **재현 절차**

          select * from v$db_protocol;

  - **수행 결과**

        CMP_OP_DB_ShardNodeGetListResult                    92        
        0                    
        CMP_OP_DB_ShardHandshake                            93        
        0                    
        CMP_OP_DB_ShardHandshakeResult                      94        
        0                    
        CMP_OP_DB_MAX                                       95        
        0                    
        UH‰�Hƒ�0H‰}�H‹E�Hƒ�H‰E�H‹E�H‰험�                  96  
        0                    
        UH‰�Hƒ�0H‰}�H‹E�Hƒ�H‰E�H‹E�HƒH‰험h�      97          
        0                    
        UH‰�H‰}片                                           98       
        0                    
        UH‰�Hƒ�0H‰}�H‹E�Hƒ�H‰E�H‹E�HƒH‰험곁              99    
        0                    
        UH‰�Hƒ�@H‰}�H‹E�Hƒ�H‰E�H‹E�H‰험晦                  100
        0                    
        101 rows selected.

  - **예상 결과**

        CMP_OP_DB_ShardNodeGetListResult                    92
        0
        CMP_OP_DB_ShardHandshake                            93
        0
        CMP_OP_DB_ShardHandshakeResult                      94
        0
        CMP_OP_DB_ShardTransaction                          95
        0
        CMP_OP_DB_ShardTransactionResult                    96
        0
        CMP_OP_DB_ShardPrepare                              97
        0
        CMP_OP_DB_ShardPrepareResult                        98
        0
        CMP_OP_DB_ShardEndPendingTx                         99
        0
        CMP_OP_DB_ShardEndPendingTxResult                   100
        0
        101 rows selected.

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-46782  Begin transaction 디버깅 정보 추가.

- **module** : sm\_transaction

- **Category** : Fatal

- **재현 빈도** : Rare

- **증상** : altibase\_error.log 로그에 Invalid statement processing
  request 오류가 발생할 수 있어서, 디버깅 정보를 추가하였습니다.

  smxTrans::begin()에서 문제 발생 시 디버깅 정보를 기록하여,

  ​1. begin된 transaction을 정리하지 않고 재활용 한 것인지,

  ​2. free된 transaction을 잘못 건드린 것인지,

  3. smiTrans에서 transaction Pool에서 최초 할당 받았는데, 문제가 있는 것인지,

  4. 혹은 smiTrans에서 기존 transaction을 정리 없이 재활용 한 것인지 등등

  비정상 종료 시 출력한 디버깅 정보를 기준으로 찾을 수 있도록 합니다.

- **재현 방법**

  -   **재현 절차**

  -   **수행 결과**

  -   **예상 결과**

- **Workaround**

- **변경사항**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

### BUG-46800  ANTI JOIN시 INVERSE HASH로 PLAN생성 시 CONSTANT FILTER 처리

-   **module** : qp-dml-pvo

-   **Category** : Other

-   **재현 빈도** : Always

-   **증상** : INVERSE HASH로 PLAN생성 시 CONSTANT FILTER 가 잘못
    처리되는 현상 수정

- **재현 방법**

  -   **재현 절차**

          drop table t1;
          drop table t2;
          create table t1(i1 integer , i2 integer);
          create index t1_i2_idx on t1(i2);
          create table t2(i1 integer, i2 integer);
          create index t2_i2_idx on t2(i2);
          insert into t1 select level, mod(level, 10)+1 from dual connect by level <= 100;
          insert into t1 values (999, 999);
          insert into t1 values (1000, null);
          insert into t2 select level, level+1 from dual connect by level <= 20;
          insert into t2 values (99, 99);
          insert into t2 values (100, null);
          iSQL> SELECT t1.*
              2   FROM t1
              3  WHERE 'N' = 'Y' AND NOT EXISTS (SELECT  /*+ INVERSE_JOIN */  1
              4                      FROM t2
              5                     WHERE t2.i1 = t1.i2);
              I1          I2
          ---------------------------
          ...
          102 rows selected.

  -   **수행 결과**

  - **예상 결과**

        iSQL> SELECT t1.*
            2   FROM t1
            3  WHERE 'N' = 'Y' AND NOT EXISTS (SELECT  /*+ INVERSE_JOIN */  1
            4                      FROM t2
            5                     WHERE t2.i1 = t1.i2);
        I1          I2
        ---------------------------
        No rows selected.

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-46805  target에 index를 타는 subquery 2개가 where문을 제외한 다른 부분이 같을 경우 결과 오류

-   **module** : qp-dml-execute

-   **Category** : Other

-   **재현 빈도** : Always

-   **증상** : taget에 index를 타는 subquery 2개가 where문을 제외한 다른
    부분이 같을 경우 결과 오류 수정

- **재현 방법**

  -   **재현 절차**

          drop table t1 cascade;
          create table t1(i1 integer , i2 integer);
          alter table t1 add constraint t1_pk primary key(i1);
          insert into t1 select level, 10 from dual connect by level <= 10;
          SELECT
              MAX( ( SELECT COUNT(AA.I1) FROM T1 AA WHERE AA.I2=1 ))  as C1,
              MAX( ( SELECT COUNT(AA.I1) FROM T1 AA WHERE AA.I2=10 ))  as C2
          FROM DUAL;

  - **수행 결과**

        iSQL> SELECT
             MAX( ( SELECT COUNT(AA.I1) FROM T1 AA WHERE AA.I2=1 )) as C1,
             MAX( ( SELECT COUNT(AA.I1) FROM T1 AA WHERE AA.I2=10 )) as C2
             FROM DUAL;
        C1                   C2
        ---------------------------------------------
        0                    0
        1 row selected.

  - **예상 결과**

        iSQL> SELECT
        	MAX( ( SELECT COUNT(AA.I1) FROM T1 AA WHERE AA.I2=1 ))  as C1,
            MAX( ( SELECT COUNT(AA.I1) FROM T1 AA WHERE AA.I2=10 ))  as C2
        FROM DUAL;
        C1                   C2
        ---------------------------------------------
        0                    10
        1 row selected.

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-46816  table name과 username이 128자 이상일 경우 메모리 침범이 발생합니다.

- **module** : dm

- **Category** : Other

- **재현 빈도** : Always

- **증상** : table name과 username의 메모리 할당 사이즈를 작게
  할당하여 128자 이상일 경우 메모리 침범이 발생하였습니다.

  메모리 할당 사이즈를 늘여 주어 메모리 침범이 발생하지 않도록
  수정하였습니다.

- **재현 방법**

  -   **재현 절차**

  -   **수행 결과**

  -   **예상 결과**

- **Workaround**

- **변경사항**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

### BUG-46836  simple query 최적화를 사용하는 환경에서 select for update 시에 nowait option 적용되지 않는 문제가 있습니다.

-   **module** : qp-select-execute

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : simple query 최적화를 사용하는 환경에서 select for update
    시에 nowait option 이 적용되지 않고, timeout 까지 대기하는 문제가
    있습니다. 이를 수정하였습니다.

- **재현 방법**

  - **재현 절차**

        ALTER SYSTEM SET EXECUTOR_FAST_SIMPLE_QUERY = 1;
        drop table t1;
        create table t1 (c1 int primary key, c2 char(200) );
        insert into t1 values (1,'1');
        autocommit off;
        update t1 set c2 = '0' where c1 = 1;

        다른 세션으로 접속
        select * from t1 where c1 =1 for update nowait;

  -   **수행 결과**

           타임아웃때까지 대기

  - **예상 결과**

        대기없이 실패

-   **Workaround**

        ALTER SYSTEM SET EXECUTOR_FAST_SIMPLE_QUERY = 0;

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

Changes
-------

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version | sharding version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- | ---------------- |
| 7.1.0.2.1        | 6.5.1                   | 8.7.1        | 7.1.6               | 7.4.4                        | 2.2.1            |

> Altibase 7.1 패치 버전별 히스토리는
> [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7_1_Version_Histories.md)
> 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의
> 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는
> 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

> 패치를 롤백하려는 경우,
> [메타다운그레이드](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Installation.md#%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9Cmeta-downgrade)를
> 참고한다.

#### CM protocol Version

통신 프로토콜 버전은 변경되지 않았다.

#### Replication protocol Version

Replication 프로토콜 버전은 변경되지 않았다.

#### Sharding Version

샤딩 버전은 변경 되지 않았다.

> 알티베이스 샤딩 프로토콜 및 메타는 상위, 하위 호환성을 보장하지
> 않는다. 즉, 샤딩 버전이 다른 경우, 재구성해야 한다. 샤딩 설정은 [Altibase Sharding 설치와 설정](<https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Sharding.md#2altibase-sharding-%EC%84%A4%EC%B9%98%EC%99%80-%EC%84%A4%EC%A0%95>)을 참고한다.

### 프로퍼티

#### 변경된 프로퍼티

* [EXECUTOR_FAST_SIMPLE_QUERY](<https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_1.md#executor_fast_simple_query>)

### 성능 뷰

추가/변경/삭제된 성능뷰 없음
