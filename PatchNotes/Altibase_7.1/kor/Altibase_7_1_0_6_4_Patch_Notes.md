<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  

- [Altibase 7.1.0.6.4 Patch Notes](#altibase-71064-patch-notes)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-49331 이중화 대상 테이블에 DDL문 수행 시 SYS\_REPL\_TABLE\_OID\_IN\_USE 메타 테이블 갱신 시 발생하는 경합으로 이중화 송신자(Sender)가 종료합니다.](#bug-49331%EC%9D%B4%EC%A4%91%ED%99%94-%EB%8C%80%EC%83%81-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90-ddl%EB%AC%B8-%EC%88%98%ED%96%89-%EC%8B%9C-sys_repl_table_oid_in_use-%EB%A9%94%ED%83%80-%ED%85%8C%EC%9D%B4%EB%B8%94-%EA%B0%B1%EC%8B%A0-%EC%8B%9C-%EB%B0%9C%EC%83%9D%ED%95%98%EB%8A%94-%EA%B2%BD%ED%95%A9%EC%9C%BC%EB%A1%9C-%EC%9D%B4%EC%A4%91%ED%99%94-%EC%86%A1%EC%8B%A0%EC%9E%90sender%EA%B0%80-%EC%A2%85%EB%A3%8C%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-49356 인덱스 소유자가 테이블 소유자와 다른 경우, 전체 DB 모드로 aexport 수행 시 해당 인덱스 생성 스크립트를 추출하지 않습니다.](#bug-49356%EC%9D%B8%EB%8D%B1%EC%8A%A4-%EC%86%8C%EC%9C%A0%EC%9E%90%EA%B0%80-%ED%85%8C%EC%9D%B4%EB%B8%94-%EC%86%8C%EC%9C%A0%EC%9E%90%EC%99%80-%EB%8B%A4%EB%A5%B8-%EA%B2%BD%EC%9A%B0-%EC%A0%84%EC%B2%B4-db-%EB%AA%A8%EB%93%9C%EB%A1%9C-aexport-%EC%88%98%ED%96%89-%EC%8B%9C-%ED%95%B4%EB%8B%B9-%EC%9D%B8%EB%8D%B1%EC%8A%A4-%EC%83%9D%EC%84%B1-%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%EB%A5%BC-%EC%B6%94%EC%B6%9C%ED%95%98%EC%A7%80-%EC%95%8A%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-49376 DBLink 사용 시 2단계 커밋 레벨 (Two-Phase Commit Level)에서 특정 노드에서 보류된 트랜잭션이 발생한 경우 처리하지 못하는 문제가 있습니다.](#bug-49376dblink-%EC%82%AC%EC%9A%A9-%EC%8B%9C-2%EB%8B%A8%EA%B3%84-%EC%BB%A4%EB%B0%8B-%EB%A0%88%EB%B2%A8-two-phase-commit-level%EC%97%90%EC%84%9C-%ED%8A%B9%EC%A0%95-%EB%85%B8%EB%93%9C%EC%97%90%EC%84%9C-%EB%B3%B4%EB%A5%98%EB%90%9C-%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98%EC%9D%B4-%EB%B0%9C%EC%83%9D%ED%95%9C-%EA%B2%BD%EC%9A%B0-%EC%B2%98%EB%A6%AC%ED%95%98%EC%A7%80-%EB%AA%BB%ED%95%98%EB%8A%94-%EB%AC%B8%EC%A0%9C%EA%B0%80-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-49378 DISK TEMP TABLE에서 해시(HASH) 연산 중 Altibase 서버가 비정상 종료하는 현상을 회피하고 원인 분석을 위한 로그를 추가합니다.](#bug-49378disk-temp-table%EC%97%90%EC%84%9C-%ED%95%B4%EC%8B%9Chash-%EC%97%B0%EC%82%B0-%EC%A4%91-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%98%EB%8A%94-%ED%98%84%EC%83%81%EC%9D%84-%ED%9A%8C%ED%94%BC%ED%95%98%EA%B3%A0-%EC%9B%90%EC%9D%B8-%EB%B6%84%EC%84%9D%EC%9D%84-%EC%9C%84%ED%95%9C-%EB%A1%9C%EA%B7%B8%EB%A5%BC-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-49402 삼중화 이상의 이중화 환경에서 DDL문 수행 시 ERR-11041 : A deadlock situation has been detected. 에러가 발생할 수 있습니다.](#bug-49402%EC%82%BC%EC%A4%91%ED%99%94-%EC%9D%B4%EC%83%81%EC%9D%98-%EC%9D%B4%EC%A4%91%ED%99%94-%ED%99%98%EA%B2%BD%EC%97%90%EC%84%9C-ddl%EB%AC%B8-%EC%88%98%ED%96%89-%EC%8B%9C-err-11041--a-deadlock-situation-has-been-detected-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-49408 DDL 복제 기능을 사용하는 이중화 환경에서 지역 서버에서 DDL문이 롤백되는 경우 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-49408ddl-%EB%B3%B5%EC%A0%9C-%EA%B8%B0%EB%8A%A5%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94-%EC%9D%B4%EC%A4%91%ED%99%94-%ED%99%98%EA%B2%BD%EC%97%90%EC%84%9C-%EC%A7%80%EC%97%AD-%EC%84%9C%EB%B2%84%EC%97%90%EC%84%9C-ddl%EB%AC%B8%EC%9D%B4-%EB%A1%A4%EB%B0%B1%EB%90%98%EB%8A%94-%EA%B2%BD%EC%9A%B0-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-49412 "PROJ-2751 호스트 변수 최대 갯수 제약 완화" 반영합니다.](#bug-49412proj-2751-%ED%98%B8%EC%8A%A4%ED%8A%B8-%EB%B3%80%EC%88%98-%EC%B5%9C%EB%8C%80-%EA%B0%AF%EC%88%98-%EC%A0%9C%EC%95%BD-%EC%99%84%ED%99%94-%EB%B0%98%EC%98%81%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-49420 DDL문 수행 시 ERR-11058 : The row already exists in a unique index. 에러가 발생합니다.](#bug-49420ddl%EB%AC%B8-%EC%88%98%ED%96%89-%EC%8B%9C-err-11058--the-row-already-exists-in-a-unique-index-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Altibase 7.1.0.6.4 Patch Notes
==============================

Fixed Bugs
----------

### BUG-49331 이중화 대상 테이블에 DDL문 수행 시 SYS\_REPL\_TABLE\_OID\_IN\_USE 메타 테이블 갱신 시 발생하는 경합으로 이중화 송신자(Sender)가 종료합니다.

-   **module** : rp-control

-   **Category** : Testcase Fail

-   **재현 빈도** : Frequence

-   **설명** : 이중화 대상 테이블에 DDL문 수행 시
    SYS\_REPL\_TABLE\_OID\_IN\_USE 메타 테이블 갱신 시 발생하는 경합으로 이중화 송신자가 종료하는 현상을 수정합니다.
    
    하나의 테이블이 여러 이중화 객체에 포함된 경우나 이중화 대상 테이블에 DDL문 수행 시 경합이 발생하며, 이 때 \$ALTIBASE\_HOME/trc/altibase\_rp.log에 아래와 같은 메세지를 출력합니다.
    
    \[2021/10/12 14:31:14 79E\]\[PID:193728\]\[Thread-140046648854272][LWP-194294]
    
    ERR-1304c(errno=16) A record has already been updated.

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

### BUG-49356 인덱스 소유자가 테이블 소유자와 다른 경우, 전체 DB 모드로 aexport 수행 시 해당 인덱스 생성 스크립트를 추출하지 않습니다.

-   **module** : ux-aexport

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 인덱스 소유자가 테이블 소유자와 다른 경우, 전체 DB 모드로 aexport 수행 시 해당 인덱스 생성 스크립트를 추출하지 않는 문제를 수정하였습니다.
    
- **재현 방법**

  -   **재현 절차**

          CREATE USER alti IDENTIFIED BY test;
          CONNECT alti/test
          DROP TABLE t1;
          CREATE TABLE t1 (c1 INTEGER, c2 CHAR(10), c3 CHAR(10));
          CREATE INDEX t1_idx1 ON t1 (c1);
          CONNECT sys/manager
          CREATE INDEX alti.t1_idx2 ON alti.t1 (c2);
          CREATE INDEX t1_idx3 ON alti.t1 (c3);

  - **수행 결과**

        $ aexport -s 127.0.0.1 -u sys -p manager...
        $ grep T1_IDX3 *
        $

  -   **예상 결과**

          $ grep T1_IDX3 *ALL_CRT_INDEX.sql:create index "T1_IDX3" on "ALTI"."T1"("C3") tablespace "SYS_TBS_MEM_DATA";

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49376 DBLink 사용 시 2단계 커밋 레벨 (Two-Phase Commit Level)에서 특정 노드에서 보류된 트랜잭션이 발생한 경우 처리하지 못하는 문제가 있습니다.

-   **module** : dblink

-   **Category** : Functional Error

-   **재현 빈도** : Frequence

-   **설명** : DBLink 사용 시 2단계 커밋 레벨 (Two-Phase Commit Level)(DBLINK\_GLOBAL\_TRANSACTION\_LEVEL = 2)에서 다수의 노드에 트랜잭션이 수행 중일 때, 특정 노드가 완료(commit/rollback) 과정에서 비정상 종료한 경우 해당 노드에서 수행된 트랜잭션이 보류 상태로 남는 문제를 수정하였습니다.
    
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

### BUG-49378 DISK TEMP TABLE에서 해시(HASH) 연산 중 Altibase 서버가 비정상 종료하는 현상을 회피하고 원인 분석을 위한 로그를 추가합니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Impossible

-   **설명** : DISK TEMP TABLE에서 해시(HASH) 연산 중 Altibase 서버가 비정상 종료하는 현상을 회피하고 원인 분석을 위한 로그를 추가합니다. 이 버그 반영 후 문제 상황 발생 시 \$ALTIBASE\_HOME/trc/altibase\_dump.log 에 아래와 같은 로그가 남습니다. (단, \_\_TEMPDUMP\_LEVEL = 1 설정 필요)
    
    ```
    DUMP HASH WASEGMENT:
    WASegPtr              : 0x7fb19e2031d8
    SpaceID               : 4
    Type                  : 1 HASH
    HashSlotCount         : 65536
    InMemory              : OutMemory
    Unique                : 0
    OpenCursorType        : 0
    EndWPID               : 384
    InsertGroup BeginWPID : 128
    InsertGroup EndWPID   : 320
    InsertGroup ReuseWPID : 131
    FetchGroup BeginWPID  : 384
    FetchGroup EndWPID    : 384
    FetchGroup ReuseWPID  : 384
    SubHashGroup BeginWPID : 320
    SubHashGroup EndWPID   : 384
    SubHashGroup ReuseWPID : 352
    WAExtentListCount     : 8
    MaxWAExtentCount      : 6
    AllocWAPageCount      : 384
    NPageHashBucketCnt    : 384
    NPageCount            : 386
    SubHashPageCount      : 64
    SubHashBuildCount     : 3
    HashSlotPageCount     : 128
    ```
    
    
    
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

### BUG-49402 삼중화 이상의 이중화 환경에서 DDL문 수행 시 ERR-11041 : A deadlock situation has been detected. 에러가 발생할 수 있습니다.

-   **module** : rp-control

-   **Category** : Functional Error

-   **재현 빈도** : Rare

-   **설명** : 삼중화 이상의 이중화 환경에서 DDL문 수행 시 ERR-11041 : A deadlock situation has been detected. 에러가 발생하는 현상을 수정합니다.
    
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

### BUG-49408 DDL 복제 기능을 사용하는 이중화 환경에서 지역 서버에서 DDL문이 롤백되는 경우 Altibase 서버가 비정상 종료할 수 있습니다.

-   **module** : rp

-   **Category** : Fatal

-   **재현 빈도** : Frequence

-   **설명** : 아래 조건을 만족하는 이중화 환경에서 지역 서버에서 수행한 DDL문이 원격 서버 문제로 지역 서버에서 롤백되는 경우 메모리 오류로 인해 발생하는 Altibase 서버 비정상 종료 현상을 수정하였습니다.
    
    1. 이중화 대상 테이블을 포함한 뷰(View), 트리거(Trigger), 저장 프로시저(Stored Procedure), 패키지(Package) 객체 중 하나라도 존재

    2. DDL 복제 기능 사용 (Altibase 서버 프로퍼티 REPLICATION\_DDL\_ENABLE 설정값 1)
    
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

### BUG-49412 "PROJ-2751 호스트 변수 최대 갯수 제약 완화" 반영합니다.

-   **module** : qp

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : 호스트 변수 사용 갯수가 1024를 초과하는 경우 The number of host variables exceed the maximum limit (1024). 에러 발생하는 현상을 수정하였습니다.
    
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

### BUG-49420 DDL문 수행 시 ERR-11058 : The row already exists in a unique index. 에러가 발생합니다.

-   **module** : rp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 이중화 환경에서 아래 조건을 모두 만족하는 경우 DDL문 수행 시 ERR-11058 : The row already exists in a unique index. 에러가 발생하는 현상을 수정하였습니다.
    
    1. 이중화를 한번이라도 시작

    2. 이중화 대상 테이블에 DDL문 수행

    3. 이중화 송신자(Sender)가 이전에 수행한 DDL 로그를 읽기 전에 DDL문 재수행 

    4. 재수행한 DDL문이 최초 DDL문을 수행하기 전의 테이블 객체 식별자(TABLE OID)를 재사용
    
- **재현 방법**

  - **재현 절차**

        이중화 gap 생성
        이중화 테이블에 DDL 구문 수행(truncate 등)

  - **수행 결과**

        다음 에러메세지로 DDL 구문 실패
        [ERR-11058 : The row already exists in a unique index.] 

  -   **예상 결과**

          DDL 구문 성공

- **Workaround**

      DDL문을 수행하기 전 이중화 FLUSH 구문을 수행하여 이중화 갭(gap)을 제거
      또는
      DDL문을 수행하기 전 V$REPGAP을 확인하여 이중화 갭(gap)이 없음을 확인 후 DDL문 수행

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

Changes
-------

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    7.1.0.6.4     |          6.5.1          |    8.10.1    |        7.1.7        |            7.4.6             |

> Altibase 7.1 패치 버전별 히스토리는 [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.1/Altibase_7_1_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

> 패치를 롤백하려는 경우, [메타다운그레이드](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Installation%20Guide.md#%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9Cmeta-downgrade)를 참고한다.

#### CM protocol Version

통신 프로토콜 버전은 변경되지 않았다.

#### Replication protocol Version

Replication 프로토콜 버전은 변경되지 않았다..

### 프로퍼티

#### 추가된 프로퍼티

#### 변경된 프로퍼티

#### 삭제된 프로퍼티

### 성능 뷰

#### 추가된 성능 뷰

#### 변경된 성능 뷰

#### 삭제된 성능 뷰
