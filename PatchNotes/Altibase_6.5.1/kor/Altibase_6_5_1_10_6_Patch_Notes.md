Altibase 6.5.1.10.6 Patch Notes
===============================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Fixed Bugs](#fixed-bugs)
    - [BUG-51475 aexport 수행시 생성되는 이중화 객체의 생성 DDL에 `AS MASTER/SLAVE`절이 누락되는 문제를 수정합니다.](#bug-51475)
    - [BUG-51477 특정한 상황에서 Update 트리거의 동작이 멈추는 문제를 수정합니다.](#bug-51477)
    - [BUG-51491 Temporary table 여부를 검사하는 로직의 오류로 인해 서버가 비정상 종료될 수 있는 문제를 수정합니다.](#bug-51491)
    - [BUG-51519 Lead 함수 3번째 인자 사용시 특정 경우에 FATAL](#bug-51519)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Fixed Bugs
==========

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

### BUG-51519<a name=bug-51519></a> Lead 함수 3번째 인자 사용시 특정 경우에 FATAL

-   **module** : qp-select-execute

-   **Category** : Fatal

-   **재현 빈도** : Rare

-   **설명** : Lead 함수의 3번째 인자 사용시 특정 조건에서 서버가 비정상 종료하는 문제를 수정하였습니다.

- **재현 방법**

  - **재현 절차**

    ```sql
    DROP TABLE t1;
    CREATE TABLE t1 ( i1 int , i2 int , i3 int);
    INSERT into t1 values ( 1, 49106157, 1);
    
    DROP TABLE t2;
    create table t2 ( i1 int, i2 int, i3 int, i4 int);
    select i1, change, i2 from (
    select lead( buy - sell, 1, 0) over ( partition by i2 order by i1  ) as change, i2, i1
    from
    (
    select nvl( case when i3 = 1 then i2
                     when i3 = 2 then i2
                     when i3 = 3 then i2
                     else 0 end, 0) as buy, numeric'0' as sell, i1, i2
    from t1
    union all
    select nvl( case when i3 = 1 then i2
                     when i3 = 2 then i2
                     when i3 = 3 then i2
                     else 0 end, 0) as sell, numeric'0' as buy, i1, i2
    from t2
    ) order by i1 desc, i2 desc
    );
    ```

  -   **수행 결과**

          [ERR-91015 : Communication failure.]

  -   **예상 결과**

          I1          CHANGE      I2
          ----------------------------------------
          1           0           49106157
          1 row selected.

- **Workaround**

  ```sql
  --lead함수의 3번째 인자를 사용하지 않고, NVL 함수로 감싸도록 수정.
  select i1, change, i2 from (
  select nvl(lead( buy - sell, 1) over ( partition by i2 order by i1  ), 0) as change, i2, i1
  from
  (
  select nvl( case when i3 = 1 then i2
                   when i3 = 2 then i2
                   when i3 = 3 then i2
                   else 0 end, 0) as buy, numeric'0' as sell, i1, i2
  from t1
  union all
  select nvl( case when i3 = 1 then i2
                   when i3 = 2 then i2
                   when i3 = 3 then i2
                   else 0 end, 0) as sell, numeric'0' as buy, i1, i2
  from t2
  ) order by i1 desc, i2 desc
  );
  ```

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
| 6.5.1.10.6       | 6.3.1                   | 8.1.1        | 7.1.3               | 7.4.5                        |

> Altibase 6.5.1 패치 버전별 히스토리는 [Version_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_6.5.1/Altibase_6_5_1_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의
> 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는
> 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

#### CM protocol Version

통신 프로토콜 버전은 변경되지 않았다.

#### Replication protocol Version

Replication 프로토콜 버전은 변경되지 않았다.

### 프로퍼티

추가/변경/삭제된 프로퍼티 없음.

### 성능 뷰

추가/변경/삭제된 성능뷰 없음.
