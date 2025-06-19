Altibase 7.1.0.10.4 Patch Notes
=================================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-51484 jdbcAdapter에서 Update 구문 Batch 처리가 가능하도록 개선](#bug-51484)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-51477 CREATE REPLICATION 이후 특정 트리거의 동작이 멈춥니다.](#bug-51477)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# New Features

### BUG-51484<a name=bug-51484></a> jdbcAdapter에서 Update 구문 Batch 처리가 가능하도록 개선

-   **module** : rp-jdbcAdapter

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : jdbcAdapter에서 Update 구문 Batch 처리가 가능하도록 개선합니다.

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

### BUG-51477<a name=bug-51477></a> 특정한 상황에서 Update 트리거의 동작이 멈추는 문제를 수정합니다.

-   **module** : qp-psm-trigger-execute

-   **Category** : Functional Error

-   **재현 빈도** : Rare

-   **설명** : 특정한 상황에서 Update 트리거의 동작이 멈추는 문제를 수정합니다. 이 버그는 아래의 조건을 모두 만족할때 발생합니다.
    
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

  -   **재현 절차**

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
      
  -   **수행 결과**
  
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
      
  -   **예상 결과**

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

Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 7.1.0.10.4       | 6.5.1                   | 8.12.1       | 7.1.7               | 7.4.7                        |

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

추가/변경/삭제된 프로퍼티 없음.

### 성능 뷰

추가/변경/삭제된 성능뷰 없음.
