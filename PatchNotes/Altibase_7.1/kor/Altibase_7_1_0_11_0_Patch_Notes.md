Altibase 7.1.0.11.0 Patch Notes
===============================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-52430 ALA에서 Handshake 과정 중 Sender IP 확인 여부를 선택할 수 있는 기능을 추가](#bug-52430)
    - [BUG-52456 iloader에서 `-direct` 옵션 제거](#bug-52456)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-51901 ALA REPLICATION SYNC로 큰 용량의 LOB 이중화 시 HANG 문제 수정](#bug-51901)
    - [BUG-52360 집계 함수가 포함된 서브쿼리를 Unnesting할 때의 결과 오류 수정](#bug-52360)
    - [BUG-52378 특정 조건에서 WITH 구문에서 집계 함수 사용 시 서버 비정상 종료 문제 수정](#bug-52378)
    - [BUG-52382 임시 테이블스페이스에서 빈 페이지(Free Page) 부족 시 오류 처리 개선](#bug-52382)
    - [BUG-52384 동일한 Prepared Statement에서 바인드 값만 변경하며 반복 실행하는 경우, 트리거 내부 statement 가 재사용되지 않는 문제 수정](#bug-52384)
    - [BUG-52395 글로벌 인덱스를 사용하는 파티션 테이블의 이중화 환경에서 GATHER_TABLE_STATS 를 원격 서버에서 수행한 경우, 이후부터 INSERT 실패 문제 수정](#bug-52395)
    - [BUG-52397 UTF8 캐릭터셋 환경에서 NCHAR, NVARCHAR 타입의 데이터 처리 시 메모리 오류로 인한 서버 비정상 종료 문제 수정](#bug-52397)
    - [BUG-52466 Volatile Tablespace 내 Temporary Table의 Primary Key 제약조건 재생성 후 인덱스 접근 시 발생하는 결과 오류 수정](#bug-52466)
    - [BUG-52484 잘못된 프로토콜 헤더 수신 시 진단 정보 출력 과정에서 서버가 비정상 종료되는 문제 수정](#bug-52484)
    - [BUG-52499 AUDIT 사용 시 메모리 오류로 비정상 종료가 발생할 수 있는 문제 수정](#bug-52499)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-52430<a name=bug-52430></a> ALA에서 Handshake 과정 중 Sender IP 확인 여부를 선택할 수 있는 기능을 추가

-   **module** : rp-ala

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : ALA에서 Handshake 수행 시 Sender IP를 검증할지 여부를 선택할 수 있는 기능을 추가했습니다.
    
    새로 추가된 `ALA_SetVerifySenderIP()` 함수를 사용하여 Sender IP 검증을 활성화하거나 비활성화할 수 있으며, 기본값은 검증 수행(`ALA_TRUE`)입니다.
    
    또한 oraAdapter, jdbcAdapter에도 동일한 기능을 설정할 수 있는 프로퍼티를 추가했습니다.
    
    - `ALA_VERIFY_SENDER_IP` (0: 검증 안 함, 1: 검증 수행)
    
-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
        -   ALA\_VERIFY\_SENDER\_IP (ALA 프로퍼티)
            -   값 범위: 0, 1
                -   1: (기본값) Sender IP 를 확인
                -   0: Sender IP 를 확인하지 않음
    -   Compile Option
    -   Error Code

### BUG-52456<a name=bug-52456></a> iloader에서 `-direct` 옵션 제거

-   **module** : ux-iloader

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : iloader에서  `-direct` 옵션을 제거했습니다. 해당 옵션은 더 이상 사용할 수 없습니다.
    
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

### BUG-51901<a name=bug-51901></a> ALA REPLICATION SYNC로 큰 용량의 LOB 이중화 시 HANG 문제 수정

-   **module** : rp-jdbcAdapter

-   **Category** : Hang

-   **재현 빈도** : Always

-   **설명** : ALA REPLICATION SYNC로 큰 용량의 LOB 데이터를 이중화할 때 HANG이 발생할 수 있는 문제를 수정하였습니다.
    
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

### BUG-52360<a name=bug-52360></a> 집계 함수가 포함된 서브쿼리를 Unnesting할 때의 결과 오류 수정

-   **module** : qp-select-pvo

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 집계 함수(Aggregation)가 포함된 Subquery에서 외부 참조 테이블이 2개 이상인 경우, Unnesting 과정의 오류로 인해 SQL 실행 결과가 올바르게 반환되지 않는 문제를 수정하였습니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    DROP TABLE t1;
    DROP TABLE t2;
    
    CREATE TABLE T1 (
        ID          VARCHAR(16),
        C1  VARCHAR(16),
        C2        VARCHAR(14),
        C3        VARCHAR(20),
        C4    VARCHAR(20),
        C5    VARCHAR(100),
        C6          CHAR(1),
        C7    VARCHAR(10)
    );
    CREATE UNIQUE INDEX T1_PK
        ON T1 (
            ID ASC,
            C2 ASC
        );
    CREATE INDEX T1_IX01
        ON T1 (
            C3 ASC
        );
    CREATE INDEX T1_IX02
        ON T1 (
            C7 ASC
        );
    CREATE INDEX T1_IX03
        ON T1 (
            C2 ASC
        );
    
    CREATE TABLE T2 (
        C1  VARCHAR(16),
        C2        VARCHAR(14)
    );
    CREATE UNIQUE INDEX T2_PK
        ON T2 (
            C1 ASC,
            C2 ASC
        );
    CREATE INDEX T2_IX03
        ON T2 (
            C2 ASC
        );
    INSERT INTO T1 VALUES (
        'G1',
        'P_NEW',
        '20260527072107',
        'WA',
        'WC',
        'C1',
        'N',
        '1000062151'
    );
    INSERT INTO T1 VALUES (
        'G1',
        'P_OLD',
        '20260527072000',
        'WC',
        'WB',
        'C1',
        'N',
        '1000062150'
    );
    INSERT INTO T2 VALUES ('P_NEW', '20260527071728');
    INSERT INTO T2 VALUES ('P_OLD', '20260518065820');
    INSERT INTO T2 VALUES ('P_OLD', '20260518070054');
    INSERT INTO T2 VALUES ('P_OLD', '20260519020748');
    
    SELECT A.C7
      FROM T1 A
           JOIN T2 B
             ON A.C1 = B.C1
           JOIN T1 C
             ON A.ID = C.ID
            AND A.C4 = C.C3
           JOIN T2 D
             ON C.C1 = D.C1
            AND D.C2 = (SELECT MAX(C2)
                                FROM T2
                               WHERE C1 = C.C1
                                 AND C2 <= A.C2)
     WHERE A.C7 = '1000062151'
       AND A.C5 LIKE '%C1%'
       AND A.C6 = 'N';
    ```

  - **수행 결과**

    ```sql
    C7
    ----------------
    1000062151
    1000062151
    1000062151
    3 rows selected.
    ```

  -   **예상 결과**

      ```sql
      C7
      ----------------
      1000062151
      1 row selected.
      ```

-   **Workaround**

        /*+ no_unnest */ 힌트 사용

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-52378<a name=bug-52378></a> 특정 조건에서 WITH 구문에서 집계 함수 사용 시 서버 비정상 종료 문제 수정

-   **module** : qp-select-pvo

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : WITH 구문을 사용하는 SQL에서 UNION ALL, GROUP BY 및 여러 개의 집계 함수(예: MAX, COUNT)를 함께 사용하는 특정 조건의 질의를 수행할 때 서버가 비정상 종료되는 문제를 수정하였습니다.
    
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

### BUG-52382<a name=bug-52382></a> 임시 테이블스페이스에서 빈 페이지(Free Page) 부족 시 오류 처리 개선

-   **module** : sm-disk-resource

-   **Category** : Hang

-   **재현 빈도** : Always

-   **설명** : 디스크 테이블에서 내부적으로 사용하는 임시 테이블스페이스(Temporary Tablespace)의 빈 페이지(Free Page)가 부족한 경우, 질의 수행이 종료되지 않고 HANG이 발생하는 문제를 수정하였습니다.

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

### BUG-52384<a name=bug-52384></a> 동일한 Prepared Statement에서 바인드 값만 변경하며 반복 실행하는 경우, 트리거 내부 statement 가 재사용되지 않는 문제 수정

-   **module** : qp-psm-trigger-execute

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 동일한 Prepared Statement에서 바인드 값만 변경하며 반복 실행하는 경우, 트리거 내부의 Statement가 재사용되지 않고 매번 새로 할당되는 문제가 있었습니다. 이로 인해 세션 내 Statement 수가 계속 증가하여 `There are too many statements in the session` 오류가 발생할 수 있었습니다. 수정 이후에는 이전에 할당된 트리거 Statement가 정상적으로 정리되어, 반복 실행 시에도 Statement가 불필요하게 증가하지 않습니다.
    
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

### BUG-52395<a name=bug-52395></a> 글로벌 인덱스를 사용하는 파티션 테이블의 이중화 환경에서 GATHER_TABLE_STATS 를 원격 서버에서 수행한 경우, 이후부터 INSERT 실패 문제 수정

-   **module** : rp-receiver
-   **Category** : Functional Error
-   **재현 빈도** : Always
-   **설명** : 글로벌 인덱스를 사용하는 파티션 테이블을 이중화 하는 환경에서, 원격 서버에서 GATHER_TABLE_STATS를 수행한 후 이중화가 정상적으로 수행되지 않아 INSERT가 실패하는 문제를 수정하였습니다.
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

### BUG-52397<a name=bug-52397></a> UTF8 캐릭터셋 환경에서 NCHAR, NVARCHAR 타입의 데이터 처리 시 메모리 오류로 인한 서버 비정상 종료 문제 수정

-   **module** : qp-ddl-dcl-execute

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : UTF8 캐릭터셋 환경에서 NCHAR 또는 NVARCHAR 타입의 데이터 처리 시 메모리 침범(memory corruption) 오류로 인한 서버 비정상 종료 문제를 수정합니다.
    
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

### BUG-52466<a name=bug-52466></a> Volatile Tablespace 내 Temporary Table의 Primary Key 제약조건 재생성 후 인덱스 접근 시 발생하는 결과 오류 수정

-   **module** : qp-dml-pvo

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : Volatile Tablespace 내 Temporary Table의 Primary Key 제약조건 재생성 후 인덱스 접근 시 발생하는 오류를 수정합니다.
    
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

### BUG-52484<a name=bug-52484></a> 잘못된 프로토콜 헤더 수신 시 진단 정보 출력 과정에서 서버가 비정상 종료되는 문제 수정

-   **module** : mm
-   **Category** : Fatal
-   **재현 빈도** : Rare
-   **설명** : 잘못된 프로토콜 헤더를 수신했을때 진단정보 출력과정에서
    서버가 비정상 종료하는 문제를 수정하였습니다. 이 문제는 6.1.1 이하 클라이언트가 A5 프로토콜의 헤더 사인 값(0x06) 대신 잘못된 값을 전송하는 경우 발생할 수 있습니다. 이제 잘못된 헤더를 수신하더라도 서버가 비정상 종료되지 않도록 개선되었습니다.
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

### BUG-52499<a name=bug-52499></a> AUDIT 사용 시 메모리 오류로 비정상 종료가 발생할 수 있는 문제 수정

-   **module** : mm-statement

-   **Category** : Memory Error

-   **재현 빈도** : Rare

-   **설명** : AUDIT 을 사용하는 환경에서 Direct Execute 방식으로 Statement를 수행할 경우, Statement가 정리되는 과정에서 메모리 오류가 발생하여 비정상 종료할 수 있는 문제가 있었습니다. 해당 문제를 수정했습니다.

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
| 7.1.0.11.0       | 6.5.1                   | 8.12.1       | 7.1.7               | 7.4.7                        |

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

### 프로퍼티

#### 추가된 프로퍼티

-   ALA\_VERIFY\_SENDER\_IP (ALA 프로퍼티)
    -   값 범위: 0, 1
        -   1: (기본값) Sender IP 를 확인
        -   0: Sender IP 를 확인하지 않음

#### 변경된 프로퍼티

변경된 프로퍼티 없음.

#### 삭제된 프로퍼티

삭제된 프로퍼티 없음.

### 성능 뷰

추가/변경/삭제된 성능뷰 없음.
