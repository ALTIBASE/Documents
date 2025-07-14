# Altibase 7.3.0.1.1 Patch Notes

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-51509 UTF-8 문자셋에서 태국어 정렬 기능 지원](#bug-51509)
    - [BUG-51484 jdbcAdapter에서 Update 구문 Batch 처리가 가능하도록 개선](#bug-51484)
    - [BUG-51443 디스크 DB 미디어 복구 중 메모리를 많이 사용하는 문제 개선](#bug-51443)
    - [BUG-51446 서버 비정상 종료 시(SIGSEGV 등) altibase_error.log에 콜스택 외 추가 진단 정보를 출력하도록 개선](#bug-51446)
    - [BUG-51452 불완전 복구에서 로그 앵커 백업 파일과 데이터 백업 파일의 익스텐드(Extend) 범위의 불일치 경우에 대한 보완](#bug-51452)
    - [BUG-51455 SQLAllocHandle()을 이용하여 환경 핸들을 할당할 때, umask 값을 0으로 설정하던 기존 동작을 변경합니다.](#bug-51455)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-51457 MEM\_DB\_DIR 로 지정된 경로가 없는 경우, 잘못된 에러가 출력됩니다.](#bug-51457)
    - [BUG-51471 BUFFER_AREA_SIZE를 820G 이상으로 설정할 경우, DB 생성이 실패하는 문제를 수정합니다.](#bug-51471)
    - [BUG-51475 aexport 수행시 생성되는 이중화 객체의 생성 DDL에 `AS MASTER/SLAVE`절이 누락되는 문제를 수정합니다.](#bug-51475)
    - [BUG-51476 DBMS_METADATA패키지를 이용하여 이중화 생성 DDL을 추출할 때, `AS MASTER/SALVE`절이 누락되는 문제를 수정합니다.](#bug-51476)
    - [BUG-51477  특정한 상황에서 Update 트리거의 동작이 멈추는 문제를 수정합니다.](#bug-51477)
    - [BUG-51480 altibase가 생성하는 파일에 대해 다른 사용자(other)에게 쓰기(w) 권한이 부여되지 않도록 수정합니다.](#bug-51480)
    - [BUG-51491 Temporary table 여부를 검사하는 로직의 오류로 인해 서버가 비정상 종료될 수 있는 문제를 수정합니다.](#bug-51491)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-51509<a name=bug-51509></a> UTF-8 문자셋에서 태국어 정렬 기능 지원

-   **module** : qp

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : UTF-8 문자셋에서 ISO/IEC 14651 기반의 태국어 정렬을 지원합니다.

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

### BUG-51484<a name=bug-51484></a> jdbcAdapter에서 Update 구문 Batch 처리가 가능하도록 개선

-   **module** : rp-jdbcAdapter

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : jdbcAdapter에서 Update 구문 Batch 처리가 가능하도록 개선합니다.
    
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

### BUG-51443<a name=bug-51443></a> 디스크 DB 미디어 복구 중 메모리를 많이 사용하는 문제 개선

-   **module** : sm

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : 디스크 DB 불완전 복구시 메모리를 많이 사용하는 문제를 개선했습니다.

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

### BUG-51446<a name=bug-51446></a> 서버 비정상 종료 시(SIGSEGV 등) altibase_error.log에 콜스택 외 추가 진단 정보를 출력하도록 개선

-   **module** : mm

-   **Category** : Maintainability

-   **재현 빈도** : Rare

-   **설명** : 서버 비정상 종료 시(SIGSEGV 등) altibase_error.log에 콜스택 외 추가 진단 정보를 출력하도록 개선합니다.

-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
        -   비정상 종료(SIGSEGV 등) 시 altibase\_error.log에 콜스택 외
            추가 진단 정보 출력 기능 추가.

    -   Property
    -   Compile Option
    -   Error Code

### BUG-51452<a name=bug-51452></a> 불완전 복구에서 로그 앵커 백업 파일과 데이터 백업 파일의 익스텐드(Extend) 범위의 불일치 경우에 대한 보완

-   **module** : sm

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : 로그 앵커 백업 파일과 데이터 백업 파일의 익스텐드 범위가 일치하지 않을 경우, 불완전 복구 과정에서 페이지 상태가 유효하지 않아 서버가 비정상 종료될 수 있습니다. 이번 패치에서 두 파일의 익스텐드 범위가 일치하지 않더라도 불완전 복구가 수행될 수 있도록 개선하였습니다.

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

### BUG-51455<a name=bug-51455></a> SQLAllocHandle()을 이용하여 환경 핸들을 할당할 때, umask 값을 0으로 설정하던 기존 동작을 변경합니다.

-   **module** : core
-   **Category** : Enhancement
-   **재현 빈도** : Always
-   **설명** : SQLAllocHandle()을 이용하여 환경 핸들을 할당할 때 umask 값이 0으로 변경되지 않도록 수정하였습니다.
-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**
-   **Workaround**
-   **변경사항**

    -   Performance view
        -   SQLAllocHandle 으로 environment 핸들을 할당한 후에 umask
            값이 0으로 변경되던 것을 변경하지 않도록 수정함

    -   Property
    -   Compile Option
    -   Error Code

# Fixed Bugs

### BUG-51457<a name=bug-51457></a> MEM\_DB\_DIR 로 지정된 경로가 없는 경우, 잘못된 에러가 출력됩니다.

-   **module** : sm

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : MEM\_DB\_DIR 로 지정된 경로가 없는 경우, 잘못된 에러가 출력되는 문제를 수정합니다.

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

### BUG-51471<a name=bug-51471></a> BUFFER_AREA_SIZE를 820G 이상으로 설정할 경우, DB 생성이 실패하는 문제를 수정합니다.

-   **module** : sm
-   **Category** : Functional Error
-   **재현 빈도** : Always
-   **설명** : BUFFER_AREA_SIZE를 820G 이상으로 설정할 경우, DB 생성이 실패하는 문제를 수정합니다.
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

### BUG-51475<a name=bug-51475></a> aexport 수행시 생성되는 이중화 객체의 생성 DDL에 `AS MASTER/SLAVE`절이 누락되는 문제를 수정합니다.

- **module** : ux-aexport

- **Category** : Functional Error

- **재현 빈도** : Always

- **설명** : aexport 수행시 생성되는 이중화 객체의 생성 DDL에 `AS MASTER/SLAVE`절이 누락되는 문제를 수정합니다.

- **재현 방법**

  - **재현 절차**

    ```sql
    DROP TABLE t1;
    CREATE TABLE t1 (c1 INT PRIMARY KEY, c2 INT);
    CREATE REPLICATION rep1 AS MASTER WITH 'localhost', 31136 FROM sys.t1 TO sys.t1;
    
    $aexport -s localhost -u sys -p manager
    ```

  - **수행 결과**

    ```sql
    $cat ALL_CRT_REP.sql
    
    DROP REPLICATION "REP1";
    CREATE REPLICATION "REP1" WITH 'localhost', 31136
    FROM "SYS"."T1" TO "SYS"."T1";
    ```

  - **예상 결과**

    ```sql
    $cat ALL_CRT_REP.sql
    
    DROP REPLICATION "REP1";
    CREATE REPLICATION "REP1" AS MASTER
    WITH 'localhost', 31136
    FROM "SYS"."T1" TO "SYS"."T1";
    ```

- **Workaround**

- **변경사항**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

### BUG-51476<a name=bug-51476></a> DBMS_METADATA패키지를 이용하여 이중화 생성 DDL을 추출할 때, `AS MASTER/SALVE`절이 누락되는 문제를 수정합니다.

-   **module** : ux-dbms_metadata

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : DBMS_METADATA패키지를 이용하여 이중화 생성 DDL을 추출할 때, `AS MASTER/SALVE`절이 누락되는 문제를 수정합니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    SET VERTICAL ON;
    DROP TABLE t1;
    CREATE TABLE t1 (c1 int primary key, c2 int);
    CREATE REPLICATION rep1 AS MASTER WITH 'localhost', 31136 FROM sys.t1 TO sys.t1;
    
    select to_char(dbms_metadata.get_ddl('REPLICATION','REP1',null)) AS ddl FROM DUAL;
    ```

  - **수행 결과**

    ```sql
    DDL : CREATE REPLICATION "REP1" WITH 'localhost', 31136
    FROM "SYS"."T1" TO "SYS"."T1"
    1 row selected.
    ```

  - **예상 결과**

    ```sql
    DDL : CREATE REPLICATION "REP1" AS MASTER
    WITH 'localhost', 31136
    FROM "SYS"."T1" TO "SYS"."T1"
    1 row selected.
    ```

- **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-51477<a name=bug-51477></a>  특정한 상황에서 Update 트리거의 동작이 멈추는 문제를 수정합니다.

- **module** : qp-psm-trigger-execute

- **Category** : Functional Error

- **재현 빈도** : Rare

- **설명** : 특정한 상황에서 Update 트리거의 동작이 멈추는 문제를 수정합니다. 이 버그는 아래의 조건을 모두 만족할때 발생합니다.

  -   컬럼 이름을 명시한 Update 트리거가 존재하고
  -   트리거 대상 테이블에 아래의 DDL을 수행한 경우
      -   트리거 대상 테이블에 이중화 생성 및 삭제 DDL을 수행한 경우
      -   Update 트리거의 생성 또는 수정 구문을 수행한 경우
      -   트리거 대상 테이블에 TRUNCATE TABLE 구문을 수행한 경우
      -   트리거 대상 테이블에 CREATE INDEX 구문을 수행한 경우


  > 아래의 경우는 문제가 없습니다.
  >
  > * Update 트리거에 컬럼 이름을 명시하지 않은 경우
  > * 트리거 대상 테이블에 ADD/DROP/RENAME/MODIFY 컬럼 DDL을 수행한 경우

- **재현 방법**

  - **재현 절차**

    ```sql
    DROP TABLE t1;
    DROP TABLE t2;
    CREATE TABLE t1 (c1 INTEGER PRIMARY KEY, c2 INTEGER);
    CREATE TABLE t2 (c1 INTEGER);
     
    INSERT INTO t1 VALUES(1, 2);
     
    CREATE OR REPLACE TRIGGER trig_on_t1
    BEFORE UPDATE OF c2 ON t1
    REFERENCING NEW AS new_row
    FOR EACH ROW
    BEGIN
      INSERT INTO t2 VALUES( new_row.c2 );
    END;
    /
    SELECT * FROM t1;
    SELECT * FROM t2;
    -- 정상 동작
    UPDATE t1 SET c2 = c2 + 1;
    -- CREATE REPLICATION
    CREATE REPLICATION repl1 WITH '127.0.0.1', 21113 FROM sys.t1 TO sys.t1;
    -- 비정상동작
    UPDATE t1 SET c2 = c2 + 1;
    SELECT * FROM t1;
    SELECT * FROM t2;
    ```

  - **수행 결과**

    ```sql
    iSQL> select * from t1;
    C1          C2
    ---------------------------
    1           4
    1 row selected.
    iSQL> select * from t2;
    C1
    --------------
    3
    1 row selected.
    ```

  - **예상 결과**

    ```sql
    iSQL> select * from t1;
    C1          C2
    ---------------------------
    1           4
    1 row selected.
    iSQL> select * from t2;
    C1
    --------------
    4
    1 row selected.
    ```

- **Workaround**

      트리거가 동작하지 않을 때 아래의 방법으로 문제를 해결할 수 있습니다.
      1. 대상 테이블에 생성된 컬럼 이름을 명시한 update 트리거를 모두 재생성한다.
      2. alter trigger trigger_name compile 구문으로 동작하지 않는 트리거를 컴파일 한다.

- **변경사항**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

### BUG-51480<a name=bug-51480></a> altibase가 생성하는 파일에 대해 다른 사용자(other)에게 쓰기(w) 권한이 부여되지 않도록 수정합니다.

-   **module** : id

-   **Category** : Other

-   **재현 빈도** : Frequence

-   **설명** : altibase가 생성하는 파일에 대해 다른 사용자(other)에게 쓰기(w) 권한이 부여되지 않도록 수정합니다.

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

### BUG-51491<a name=bug-51491></a> Temporary table 여부를 검사하는 로직의 오류로 인해 서버가 비정상 종료될 수 있는 문제를 수정합니다.

-   **module** : qp

-   **Category** : Fatal

-   **재현 빈도** : Unknown

-   **설명** : Temporary table 여부를 검사하는 로직의 오류로 인해 서버가 비정상 종료될 수 있는 문제를 수정합니다.
    
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
| 7.3.0.1.1        | 7.3.0                   | 9.4.1        | 7.1.8               | 7.4.9                        |

> Altibase 7.3 패치 버전별 히스토리는 [Version_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.3/Altibase_7_3_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의
> 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는
> 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

> 패치를 롤백하려는 경우,
> [메타다운그레이드](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/Installation%20Guide.md#%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9Cmeta-downgrade)를
> 참고한다.

#### CM protocol Version

통신 프로토콜 버전은 변경되지 않았다.

#### Replication protocol Version

Replication 프로토콜 버전은 변경되지 않았다.

### 프로퍼티

추가/변경/삭제된 프로퍼티 없음.

### 성능 뷰

추가/변경/삭제된 성능뷰 없음.
