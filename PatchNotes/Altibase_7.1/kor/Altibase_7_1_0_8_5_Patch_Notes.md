# Altibase 7.1.0.8.5 Patch Notes

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-49970  altimon에서 사용자 모드와 커널 모드 구분없이 단일 CPU 사용률 표시가 필요합니다.](#bug-49970-altimon%EC%97%90%EC%84%9C-%EC%82%AC%EC%9A%A9%EC%9E%90-%EB%AA%A8%EB%93%9C%EC%99%80-%EC%BB%A4%EB%84%90-%EB%AA%A8%EB%93%9C-%EA%B5%AC%EB%B6%84%EC%97%86%EC%9D%B4-%EB%8B%A8%EC%9D%BC-cpu-%EC%82%AC%EC%9A%A9%EB%A5%A0-%ED%91%9C%EC%8B%9C%EA%B0%80-%ED%95%84%EC%9A%94%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50109  이중화 부가기능으로 RECEIVE_ONLY 옵션 제공](#bug-50109-%EC%9D%B4%EC%A4%91%ED%99%94-%EB%B6%80%EA%B0%80%EA%B8%B0%EB%8A%A5%EC%9C%BC%EB%A1%9C-receive_only-%EC%98%B5%EC%85%98-%EC%A0%9C%EA%B3%B5)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-47430  V$RESERVED_WORDS 에서 누락된 예약어를 추가하고, 타입이 잘못된 예약어를 수정합니다.](#bug-47430-vreserved_words-%EC%97%90%EC%84%9C-%EB%88%84%EB%9D%BD%EB%90%9C-%EC%98%88%EC%95%BD%EC%96%B4%EB%A5%BC-%EC%B6%94%EA%B0%80%ED%95%98%EA%B3%A0-%ED%83%80%EC%9E%85%EC%9D%B4-%EC%9E%98%EB%AA%BB%EB%90%9C-%EC%98%88%EC%95%BD%EC%96%B4%EB%A5%BC-%EC%88%98%EC%A0%95%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-47989  ERR\-3134F : Invalid use of sequence 에러 메시지를 출력할 때, 에러를 발생시킨 문법도 함께 출력하도록 수정합니다.](#bug-47989-err%5C-3134f--invalid-use-of-sequence-%EC%97%90%EB%9F%AC-%EB%A9%94%EC%8B%9C%EC%A7%80%EB%A5%BC-%EC%B6%9C%EB%A0%A5%ED%95%A0-%EB%95%8C-%EC%97%90%EB%9F%AC%EB%A5%BC-%EB%B0%9C%EC%83%9D%EC%8B%9C%ED%82%A8-%EB%AC%B8%EB%B2%95%EB%8F%84-%ED%95%A8%EA%BB%98-%EC%B6%9C%EB%A0%A5%ED%95%98%EB%8F%84%EB%A1%9D-%EC%88%98%EC%A0%95%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-49399  트랜잭션에서 실행하는 구문과 체크포인트 동작의 동시성 제어에 오류가 있어서 수정합니다.](#bug-49399-%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98%EC%97%90%EC%84%9C-%EC%8B%A4%ED%96%89%ED%95%98%EB%8A%94-%EA%B5%AC%EB%AC%B8%EA%B3%BC-%EC%B2%B4%ED%81%AC%ED%8F%AC%EC%9D%B8%ED%8A%B8-%EB%8F%99%EC%9E%91%EC%9D%98-%EB%8F%99%EC%8B%9C%EC%84%B1-%EC%A0%9C%EC%96%B4%EC%97%90-%EC%98%A4%EB%A5%98%EA%B0%80-%EC%9E%88%EC%96%B4%EC%84%9C-%EC%88%98%EC%A0%95%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-49765  REGEXP_MODE=1로 설정된 환경(PCRE2 호환모드)에서 정규식 함수의 인자로 fixed table의 컬럼을 사용한 경우 ERR-2106B 오류가 발생합니다.](#bug-49765-regexp_mode1%EB%A1%9C-%EC%84%A4%EC%A0%95%EB%90%9C-%ED%99%98%EA%B2%BDpcre2-%ED%98%B8%ED%99%98%EB%AA%A8%EB%93%9C%EC%97%90%EC%84%9C-%EC%A0%95%EA%B7%9C%EC%8B%9D-%ED%95%A8%EC%88%98%EC%9D%98-%EC%9D%B8%EC%9E%90%EB%A1%9C-fixed-table%EC%9D%98-%EC%BB%AC%EB%9F%BC%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%9C-%EA%B2%BD%EC%9A%B0-err-2106b-%EC%98%A4%EB%A5%98%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-49936  PK(Primary Key)가 있는 파티션드 테이블에 논파티션드 인덱스를 생성한 후 PK를 삭제하면, PK였던 칼럼에 NULL데이터를 입력하면 잘못된 동작을 할 수 있습니다.](#bug-49936-pkprimary-key%EA%B0%80-%EC%9E%88%EB%8A%94-%ED%8C%8C%ED%8B%B0%EC%85%98%EB%93%9C-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90-%EB%85%BC%ED%8C%8C%ED%8B%B0%EC%85%98%EB%93%9C-%EC%9D%B8%EB%8D%B1%EC%8A%A4%EB%A5%BC-%EC%83%9D%EC%84%B1%ED%95%9C-%ED%9B%84-pk%EB%A5%BC-%EC%82%AD%EC%A0%9C%ED%95%98%EB%A9%B4-pk%EC%98%80%EB%8D%98-%EC%B9%BC%EB%9F%BC%EC%97%90-null%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%A5%BC-%EC%9E%85%EB%A0%A5%ED%95%98%EB%A9%B4-%EC%9E%98%EB%AA%BB%EB%90%9C-%EB%8F%99%EC%9E%91%EC%9D%84-%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-50210  MERGE 구문의 USING 절에서 조회한 테이블이 LOB칼럼을 포함하고, ON절 또는 MATCHED ... UPDATE 절 에서 그 LOB 칼럼을 사용하면, ERR-2100C : Conversion not applicable. 오류가 발생한다.](#bug-50210-merge-%EA%B5%AC%EB%AC%B8%EC%9D%98-using-%EC%A0%88%EC%97%90%EC%84%9C-%EC%A1%B0%ED%9A%8C%ED%95%9C-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%9D%B4-lob%EC%B9%BC%EB%9F%BC%EC%9D%84-%ED%8F%AC%ED%95%A8%ED%95%98%EA%B3%A0-on%EC%A0%88-%EB%98%90%EB%8A%94-matched--update-%EC%A0%88-%EC%97%90%EC%84%9C-%EA%B7%B8-lob-%EC%B9%BC%EB%9F%BC%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%98%EB%A9%B4-err-2100c--conversion-not-applicable-%EC%98%A4%EB%A5%98%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%9C%EB%8B%A4)
    - [BUG-50232  JOIN predicate 에 _PROWID 를 사용하는 경우, 잘못된 메모리를 참조할 수 있습니다.](#bug-50232-join-predicate-%EC%97%90-_prowid-%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94-%EA%B2%BD%EC%9A%B0-%EC%9E%98%EB%AA%BB%EB%90%9C-%EB%A9%94%EB%AA%A8%EB%A6%AC%EB%A5%BC-%EC%B0%B8%EC%A1%B0%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-50248  계층적 질의의 target 절에 사용한 함수의 별칭(alias) 을  ORDER SIBILINGS BY 절에서 사용한 칼럼 이름과 동일하게  사용한 경우, 비정상 종료 할 수 있습니다.](#bug-50248-%EA%B3%84%EC%B8%B5%EC%A0%81-%EC%A7%88%EC%9D%98%EC%9D%98-target-%EC%A0%88%EC%97%90-%EC%82%AC%EC%9A%A9%ED%95%9C-%ED%95%A8%EC%88%98%EC%9D%98-%EB%B3%84%EC%B9%ADalias-%EC%9D%84--order-sibilings-by-%EC%A0%88%EC%97%90%EC%84%9C-%EC%82%AC%EC%9A%A9%ED%95%9C-%EC%B9%BC%EB%9F%BC-%EC%9D%B4%EB%A6%84%EA%B3%BC-%EB%8F%99%EC%9D%BC%ED%95%98%EA%B2%8C--%EC%82%AC%EC%9A%A9%ED%95%9C-%EA%B2%BD%EC%9A%B0-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C-%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-50256  NOT NULL 제약조건인 칼럼과 NOT NULL 제약이 없는 칼럼으로 PK를 생성한 다음 PK를 제거(DROP) 하면, NOT NULL 제약이 삭제되지 않는 문제가 있습니다.](#bug-50256-not-null-%EC%A0%9C%EC%95%BD%EC%A1%B0%EA%B1%B4%EC%9D%B8-%EC%B9%BC%EB%9F%BC%EA%B3%BC-not-null-%EC%A0%9C%EC%95%BD%EC%9D%B4-%EC%97%86%EB%8A%94-%EC%B9%BC%EB%9F%BC%EC%9C%BC%EB%A1%9C-pk%EB%A5%BC-%EC%83%9D%EC%84%B1%ED%95%9C-%EB%8B%A4%EC%9D%8C-pk%EB%A5%BC-%EC%A0%9C%EA%B1%B0drop-%ED%95%98%EB%A9%B4-not-null-%EC%A0%9C%EC%95%BD%EC%9D%B4-%EC%82%AD%EC%A0%9C%EB%90%98%EC%A7%80-%EC%95%8A%EB%8A%94-%EB%AC%B8%EC%A0%9C%EA%B0%80-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-50257  디스크 인덱스 페이지 할당 실패시 예외처리를 보강합니다.](#bug-50257-%EB%94%94%EC%8A%A4%ED%81%AC-%EC%9D%B8%EB%8D%B1%EC%8A%A4-%ED%8E%98%EC%9D%B4%EC%A7%80-%ED%95%A0%EB%8B%B9-%EC%8B%A4%ED%8C%A8%EC%8B%9C-%EC%98%88%EC%99%B8%EC%B2%98%EB%A6%AC%EB%A5%BC-%EB%B3%B4%EA%B0%95%ED%95%A9%EB%8B%88%EB%8B%A4)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-49970  altimon에서 사용자 모드와 커널 모드 구분없이 단일 CPU 사용률 표시가 필요합니다.

-   **module** : ux-altiMon

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : USER/KERNEL 구분없는 TOTAL\_CPU(OS), PROC\_CPU (알티베이스 프로세스) 사용률을 제공합니다.

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

### BUG-50109  이중화 부가기능으로 RECEIVE_ONLY 옵션 제공

-   **module** : rp-control

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : 이중화 부가기능으로 RECEIVE\_ONLY 옵션(수신 전용 옵션)이 추가되었습니다. 이 버그에서 메타버전이 8.10.1에서 8.11.1로 변경되었습니다. 패치 후 롤백이 필요한 경우 [메타다운그레이드](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Installation%20Guide.md#%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9Cmeta-downgrade)를 수행해야 합니다.

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

Fixed Bugs
==========

### BUG-47430  V$RESERVED_WORDS 에서 누락된 예약어를 추가하고, 타입이 잘못된 예약어를 수정합니다.

-   **module** : qp-meta

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : V\$RESERVED\_WORDS 에서 누락된 예약어 CHECK를 추가합니다. 그리고 RESERVED\_TYPE이 잘못된 예약어가 있어서 수정합니다. 이 수정은 사용자 시스템에 영향을 주지 않습니다.

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

### BUG-47989  ERR\-3134F : Invalid use of sequence 에러 메시지를 출력할 때, 에러를 발생시킨 문법도 함께 출력하도록 수정합니다.

-   **module** : qp-dml-execute

-   **Category** : Message Error

-   **재현 빈도** : Always

-   **설명** : 기존에는 ERR-3134F : Invalid use of sequence 에러 메시지만 출력하여, 에러의 위치를 찾기가 어려웠습니다. 이 버그의 수정으로 에러가 발생한 위치를 알 수 있습니다.
    변경

- **재현 방법**

  - **재현 절차**

        CREATE TABLE T1 (C1 INTEGER);
        CREATE SEQUENCE S1;
        VAR VAR INTEGER;
        PREPARE INSERT INTO T1 VALUES(1) RETURN S1.NEXTVAL INTO :VAR;
        SELECT C1 FROM T1 LIMIT S1.NEXTVAL;
        SELECT C1 FROM T1 LOOP S1.NEXTVAL;

  - **수행 결과**

        iSQL> PREPARE INSERT INTO T1 VALUES(1) RETURN S1.NEXTVAL INTO :VAR;
        [ERR-3134F : Invalid use of sequence]
        iSQL> SELECT C1 FROM T1 LIMIT S1.NEXTVAL;
        [ERR-3134F : Invalid use of sequence]
        iSQL> SELECT C1 FROM T1 LOOP S1.NEXTVAL;
        [ERR-3134F : Invalid use of sequence]

  -   **예상 결과**

          iSQL> prepare insert into t1 values(1) return s1.nextval into :var;
          [ERR-3134F : Invalid use of sequence
          0001 : insert into T1 values(1) return S1.NEXTVAL into :var
                                                ^         ^
          ]
          iSQL> select c1 from t1 limit s1.nextval;
          [ERR-3134F : Invalid use of sequence
          0001 : select C1 from T1 limit S1.NEXTVAL
                                        ^         ^
          ]
          iSQL> select c1 from t1 loop s1.nextval;
          [ERR-3134F : Invalid use of sequence
          0001 : select C1 from T1 loop S1.NEXTVAL
                                       ^         ^
          ]

-   **Workaround**

-   **변경사항**

    - Performance view

    - Property

    - Compile Option

    - Error Code

      - 변경전 : [ERR-3134F : Invalid use of sequence]

      - 변경후 : [ERR-3134F : Invalid use of sequence
0001 : insert into T1 values(1) return S1.NEXTVAL into :var
                                      ^         ^
]



### BUG-49399  트랜잭션에서 실행하는 구문과 체크포인트 동작의 동시성 제어에 오류가 있어서 수정합니다.

-   **module** : sm-mem-recovery

-   **Category** : Reliability

-   **재현 빈도** : Always

-   **설명** : 트랜잭션에서 실행하는 구문과 체크포인트 동작의 동시성 제어에 오류가 있어서 수정합니다.

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

### BUG-49765  REGEXP_MODE=1로 설정된 환경(PCRE2 호환모드)에서 정규식 함수의 인자로 fixed table의 컬럼을 사용한 경우 ERR-2106B 오류가 발생합니다.

-   **module** : qp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : UTF8 캐릭터셋 환경에서 REGEXP_MODE=1로 설정(PCRE2 호환모드)하고 정규식 함수의 인자로 fixed table의 column을 사용한 경우, ERR-2106B : Unable to execute this operation because of the database server character set. 오류가 발생하는 문제를 수정합니다.

- **재현 방법**

  - **재현 절차**

        ALTER SESSION SET REGEXP_MODE=1;
        SELECT REGEXP_COUNT(DUMMY, '/') FROM DUAL;

  - **수행 결과**

    - 7.1.0.8.4 에서의 결과 (7.1.0.8.4부터 에러코드는 동일하나, 에러메시지가 변경되었습니다.)

      ```
      [ERR-2106B : Unable to execute this operation because of the database server character set.
      0001 : SELECT REGEXP_COUNT(DUMMY, '/') FROM DUAL
                   ^                       ^
      ]
      ```

    - 7.1.0.8.3 이하에서의 결과

      ```
      [ERR-2106B : Unsupported character set by PCRE2 library0001 : SELECT REGEXP_COUNT(DUMMY, '/') FROM DUAL             ^                       ^]
      ```

  - **예상 결과**

        REGEXP_COUNT(DUMMY, '/')
        ---------------------------
        0
        1 row selected.

- **Workaround**

      ALTER SESSION SET REGEXP_MODE=1;
      SELECT REGEXP_COUNT(CONVERT(DUMMY, 'UTF8'), '/') FROM DUAL;

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49936  PK(Primary Key)가 있는 파티션드 테이블에 논파티션드 인덱스를 생성한 후 PK를 삭제하면, PK였던 칼럼에 NULL데이터를 입력하면 잘못된 동작을 할 수 있습니다.

-   **module** : qp-ddl-dcl-execute

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : PK(Primary Key)가 있는 파티션드 테이블에 논파티션드 인덱스를 생성한 후 PK를 삭제하면, PK였던 칼럼에 NULL데이터를 입력하면 잘못된 동작을 할 수 있어서 수정합니다.

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

### BUG-50210  MERGE 구문의 USING 절에서 조회한 테이블이 LOB칼럼을 포함하고, ON절 또는 MATCHED ... UPDATE 절 에서 그 LOB 칼럼을 사용하면, ERR-2100C : Conversion not applicable. 오류가 발생한다.

-   **module** : qp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : MERGE 구문의 USING 절에서 조회한 테이블이 LOB칼럼을 포함하고, ON절 또는 MATCHED ... UPDATE 절 에서 그 LOB 칼럼을 사용하면, ERR-2100C : Conversion not applicable. 오류가 발생하는 문제를 수정합니다.

- **재현 방법**

  - **재현 절차**

        DROP TABLE T1 ;
        DROP TABLE T2 ;
        CREATE TABLE T1 ( I1 INT, I2 CLOB, i3 int );
        INSERT INTO T1 VALUES ( 1,1,1);
        INSERT INTO T1 VALUES ( 2,2,2);

        CREATE TABLE T2 ( I1 INT, I2 CLOB, i3 int );
        INSERT INTO T2 VALUES ( 1,10,10);
        INSERT INTO T2 VALUES ( 2,20,20);

        MERGE INTO T1 A USING T2 B ON A.I1 = B.I1
        WHEN MATCHED THEN
        UPDATE SET A.I2 = B.I2
        DELETE WHERE A.I1=3;

  -   **수행 결과**

          [ERR-2100C : Conversion not applicable.]

  -   **예상 결과**

          2 row merged.

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50232  JOIN predicate 에 _PROWID 를 사용하는 경우, 잘못된 메모리를 참조할 수 있습니다.

-   **module** : qp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : JOIN predicate에 _PROWID를 사용하는 경우, 잘못된 메모리를 참조 할 수 있어 수정합니다.

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

### BUG-50248  계층적 질의의 target 절에 사용한 함수의 별칭(alias) 을  ORDER SIBILINGS BY 절에서 사용한 칼럼 이름과 동일하게  사용한 경우, 비정상 종료 할 수 있습니다.

-   **module** : qp-select-execute

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : 계층적 질의의 target 절에 사용한 함수의 별칭(alias) 을 ORDER SIBILINGS BY 절에서 사용한 칼럼 이름과 동일하게 사용한 경우, 비정상 종료하는 문제를 수정합니다.

- **재현 방법**

  - **재현 절차**

        DROP TABLE T1;
        CREATE TABLE T1
        (
            STM    VARCHAR(10) NOT NULL,
            STC    VARCHAR(10) NOT NULL,
            USCI    VARCHAR(10),
            SCIS    NUMERIC(10)
        );
        INSERT INTO T1 VALUES( 'S1041360', '1', '2', '1' );
        INSERT INTO T1 VALUES( 'S1041360', '2', '3', '1' );
        INSERT INTO T1 VALUES( 'S1041360', '3', '4', '1' );

        SELECT X.STM
        FROM (
        SELECT
            STM
           ,NVL(USCI,STC) AS USCI
          , SCIS AS SCIS
            FROM (
                     SELECT Y2.STM, Y2.USCI, Y2.STC, Y2.SCIS
                     FROM T1 Y2
                    )
            CONNECT BY PRIOR  STC = USCI
            ORDER SIBLINGS BY  USCI,STC
            ) X
        ;

  -   **수행 결과**

          [ERR-91015 : Communication failure.]

  -   **예상 결과**

          STM
          --------------
          S1041360
          S1041360
          S1041360
          S1041360
          S1041360
          S1041360
          6 rows selected.

- **Workaround**

      SELECT X.STM
      FROM (
      SELECT
          STM
         ,NVL(USCI,STC) AS USCI2
        , SCIS AS SCIS
          FROM (
                   SELECT Y2.STM, Y2.USCI, Y2.STC, Y2.SCIS
                   from t1 Y2
                  )
          CONNECT BY PRIOR  STC = USCI
          ORDER SIBLINGS BY  USCI,STC
          ) X
      ;

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50256  NOT NULL 제약조건인 칼럼과 NOT NULL 제약이 없는 칼럼으로 PK를 생성한 다음 PK를 제거(DROP) 하면, NOT NULL 제약이 삭제되지 않는 문제가 있습니다.

-   **module** : qp-ddl-dcl-execute

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : NOT NULL 제약조건인 칼럼과 NOT NULL 제약이 없는 칼럼으로 PK를 생성한 다음 PK를 제거(DROP) 하면, PK로 인해 NOT NULL 제약이 생긴 칼럼에 NOT NULL 제약이 삭제되지 않는 문제가 있습니다. 이로 인해 잘못된 동작을 할 수가 있어 수정합니다.

-   **재현 방법**

    -   **재현 절차**

            DROP TABLE T1;
            CREATE TABLE T1(
                    I1 INTEGER,
                    I2 INTEGER,
                    I3 INTEGER
                );
            ALTER TABLE T1 ALTER COLUMN ( I2 NOT NULL );
            ALTER TABLE T1 ADD CONSTRAINT T1_PK PRIMARY KEY ( I1, I2 );
            SELECT
                  CAST( TABLE_NAME  AS CHAR( 12 ) ) TABTABLE_NAME,
                  CAST( COLUMN_NAME AS CHAR( 12 ) ) COLUMN_NAME,
                  CAST( IS_NULLABLE AS CHAR( 12 ) ) IS_NULLABLE
                FROM (
                  SELECT *
                  FROM
                    SYSTEM_.SYS_TABLES_ T,
                    SYSTEM_.SYS_COLUMNS_ C
                  WHERE
                    T.TABLE_NAME = 'T1' AND
                    T.TABLE_ID = C.TABLE_ID );
            ALTER TABLE T1 DROP CONSTRAINT T1_PK;    // PK 삭제
            SELECT
                  CAST( TABLE_NAME  AS CHAR( 12 ) ) TABTABLE_NAME,
                  CAST( COLUMN_NAME AS CHAR( 12 ) ) COLUMN_NAME,
                  CAST( IS_NULLABLE AS CHAR( 12 ) ) IS_NULLABLE
                FROM (
                  SELECT *
                  FROM
                    SYSTEM_.SYS_TABLES_ T,
                    SYSTEM_.SYS_COLUMNS_ C
                  WHERE
                    T.TABLE_NAME = 'T1' AND
                    T.TABLE_ID = C.TABLE_ID );

    -   **수행 결과**

            ###### PK 삭제 전
            TABTABLE_NAME  COLUMN_NAME   IS_NULLABLE   
            -----------------------------------------------
            T1            I1            F             
            T1            I2            F             
            T1            I3            T             
            3 rows selected.

            ##### PK 삭제 후
            TABTABLE_NAME  COLUMN_NAME   IS_NULLABLE   
            -----------------------------------------------
            T1            I1            F             
            T1            I2            F             
            T1            I3            T             
            3 rows selected.

    -   **예상 결과**

            ##### PK 삭제 후
            TABTABLE_NAME  COLUMN_NAME   IS_NULLABLE   
            -----------------------------------------------
            T1            I1            T             
            T1            I2            F             
            T1            I3            T             
            3 rows selected.

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50257  디스크 인덱스 페이지 할당 실패시 예외처리를 보강합니다.

-   **module** : sm-disk-index

-   **Category** : Fatal

-   **재현 빈도** : Impossible

-   **설명** : 디스크 인덱스 페이지 할당 실패시 서버가 비정상하는 문제를 처리하기 위해 예외처리를 변경하고, 오류 발생시 디버깅정보를 추가하였습니다. 이 버그 수정으로 시스템에 영향은 없습니다.

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

Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 7.1.0.8.5        | 6.5.1                   | 8.11.1       | 7.1.7               | 7.4.7                        |

> Altibase 7.1 패치 버전별 히스토리는 [Version_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.1/Altibase_7_1_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의
> 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는
> 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

> 패치를 롤백하려는 경우,
> [메타다운그레이드](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Installation%20Guide.md#%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9Cmeta-downgrade)를
> 참고한다.

#### CM protocol Version

통신 프로토콜 버전은 변경되지 않았다.

#### Replication protocol Version

Replication 프로토콜 버전은 변경되지 않았다.

> 알티베이스 샤딩 프로토콜 및 메타는 상위, 하위 호환성을 보장하지
> 않는다. 즉, 샤딩 버전이 다른 경우, 재구성해야 한다.

### 프로퍼티

#### 추가된 프로퍼티

#### 변경된 프로퍼티

#### 삭제된 프로퍼티

### 성능 뷰

#### 추가된 성능 뷰

#### 변경된 성능 뷰

#### 삭제된 성능 뷰
