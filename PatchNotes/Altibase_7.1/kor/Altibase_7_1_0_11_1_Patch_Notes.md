Altibase 7.1.0.11.1 Patch Notes
===============================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [New Features](#new-features)
    - [BUG-52383 임시 테이블스페이스의 Extent 크기 설정에 따른 동작 개선](#bug-52383)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-52533 DDL Sync 중 TableOID가 변경되어도 이중화 메타를 다시 빌드하지 않는 문제 수정](#bug-52533)
    - [BUG-52548 JDBC 드라이버의 CallableStatement 이름 기반 파라미터 API 호출 시 NullPointerException이 발생하는 문제 수정](#bug-52548)
    - [BUG-52553 DDL 수행 중 Commit 실패로 서버가 비정상 종료되는 문제 수정](#bug-52553)
    - [BUG-52575 이중화에서 잘못된 Update Log 처리 시 Sender가 비정상 종료되는 문제 수정](#bug-52575)
    - [BUG-52589 Disk Hash Temp Table 사용 시 잘못된 결과가 반환되는 문제 수정](#bug-52589)
    - [BUG-52617 FAST SIMPLE QUERY 처리 과정에서 읽기 전용 파티션에 UPDATE가 수행되는 문제 수정](#bug-52617)
    - [BUG-52620 서버 패키지에서 altiMon 분리](#bug-52620)
    - [BUG-52629 파티션 테이블에서 CLOB 컬럼 조건으로 SELECT FOR UPDATE 수행 시 잘못된 결과가 반환되는 문제 수정](#bug-52629)
    - [BUG-52639 LIMIT 절의 정수 오버플로 문제 수정](#bug-52639)
    - [BUG-52644 파티션 테이블 조회 시 ERR-31455 (Failed to work because an internal exception occurred from an OS) 오류가 발생하는 문제 수정](#bug-52644)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-52383<a name=bug-52383></a> 임시 테이블스페이스의 Extent 크기 설정에 따른 동작 개선

-   **module** : sm-disk-resource

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : 임시 테이블스페이스와 임시 테이블의 Extent 크기가 서로 다르게 설정된 경우에도 임시 테이블 전체 스캔이 정상적으로 수행되도록 개선했습니다. 기존에는 전체 스캔 시 임시 테이블스페이스의 Extent 크기만큼 한 번에 Fetch했으나, 이제 최대 64 Page 단위로 Fetch합니다.

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

### BUG-52533<a name=bug-52533></a> DDL Sync 중 TableOID가 변경되어도 이중화 메타를 다시 빌드하지 않는 문제 수정

-   **module** : rp

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : DDL Sync 수행 중 TableOID가 변경되었음에도 이중화 메타를 다시 빌드하지 않아 문제가 발생할 수 있었습니다. DDL Sync 중 TableOID가 변경되면 이중화 메타를 다시 빌드하도록 예외 처리를 개선했습니다.

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

### BUG-52548<a name=bug-52548></a> JDBC 드라이버의 CallableStatement 이름 기반 파라미터 API 호출 시 NullPointerException이 발생하는 문제 수정

-   **module** : mm-jdbc

-   **Category** : Functionality

-   **재현 빈도** : Always

- **설명** : Altibase JDBC 드라이버는 CallableStatement의 이름 기반 파라미터 바인딩을 지원하지 않습니다.

  기존에는 이름 기반 파라미터 API 호출 시 `NullPointerException`이 발생했으나, 이제 다음과 같은 예외가 발생하도록 수정했습니다.

  * Altibase.jar: `SQLException(Unsupported feature)` 발생
  * Altibase42.jar: `SQLFeatureNotSupportedException` 발생

- **재현 방법**

  - **재현 절차**

    ```java
    CallableStatement sStmt =
        conn.prepareCall("EXEC PROC1(:I1_IN, :I2_OUT, :I3_OUT)");
    sStmt.setInt(1, 1);
    sStmt.registerOutParameter(2, Types.VARCHAR);
    sStmt.registerOutParameter(3, Types.VARCHAR);
    sStmt.execute();
    sStmt.getCharacterStream("I3_OUT");
    ```

  -   **수행 결과**

          `java.lang.NullPointerException`이 발생한다.

  -   **예상 결과**

          `SQLException(Unsupported feature)` 또는 `SQLFeatureNotSupportedException`이 발생한다.

-   **Workaround**

        이름 기반 API 대신 `sStmt.getCharacterStream(3)`과 같은 인덱스 기반 API를 사용한다.

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-52553<a name=bug-52553></a> DDL 수행 중 Commit 실패로 서버가 비정상 종료되는 문제 수정

-   **module** : qp-ddl-dcl-execute

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : DDL 수행 과정에서 Commit이 실패할 경우 서버가 비정상 종료될 수 있는 문제를 수정했습니다.

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

### BUG-52575<a name=bug-52575></a> 이중화에서 잘못된 Update Log 처리 시 Sender가 비정상 종료되는 문제 수정

-   **module** : rp

-   **Category** : Fatal

-   **재현 빈도** : Impossible

-   **설명** : 이중화에서 잘못된 Update Log를 읽을 경우 서버가 비정상 종료되는 문제를 수정했습니다. 잘못된 Update Log가 감지되면 오류 로그를 기록하고 Sender를 종료하도록 변경했습니다.

    사용자는 아래와 같은 에러가 `altibase_rp.log`에 남을 경우 이중화를 drop한 후 재생성해야 합니다.

    ```text
    ERR-11069(errno=62) Internal server error in the storage manager (... Column Count is 0(zero) ...)
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

### BUG-52589<a name=bug-52589></a> 디스크 해시 임시 테이블(Disk Hash Temp Table) 사용 시 잘못된 결과가 반환되는 문제 수정

-   **module** : sm-disk-resource

-   **Category** : Reliability

-   **재현 빈도** : Always

-   **설명** : 특정 조건에서 GROUP BY 수행 중 디스크 해시 임시 테이블을 사용할 경우 잘못된 결과가 반환될 수 있는 문제를 수정했습니다.

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

### BUG-52617<a name=bug-52617></a> FAST SIMPLE QUERY 처리 과정에서 읽기 전용 파티션에 UPDATE가 수행되는 문제 수정

-   **module** : qp-dml-execute

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : `EXECUTOR_FAST_SIMPLE_QUERY` 프로퍼티가 `2`로 설정된 환경에서, FAST SIMPLE QUERY 처리 과정 중 읽기 전용으로 설정된 파티션에 UPDATE가 수행되는 문제를 수정했습니다.

- **재현 방법**

  - **재현 절차**

    ```sql
    CREATE TABLE T0 ( ID INTEGER, K INTEGER )
    PARTITION BY RANGE ( ID )
    (
      PARTITION P1 VALUES LESS THAN (100),
      PARTITION P2 VALUES LESS THAN (200),
      PARTITION P9 VALUES DEFAULT
    );
    INSERT INTO T0(ID, K) SELECT LEVEL, LEVEL FROM DUAL CONNECT BY LEVEL <= 10;
    INSERT INTO T0(ID, K) SELECT LEVEL + 100, LEVEL + 100 FROM DUAL CONNECT BY LEVEL <= 10;
    COMMIT;
    ALTER TABLE T0 ACCESS PARTITION P1 READ APPEND;
    UPDATE T0 SET K = K + 1 WHERE 1 = 1;
    UPDATE T0 SET K = K + 1;
    ```

  - **수행 결과**

    ```sql
    iSQL> UPDATE T0 SET K = K + 1 WHERE 1 = 1;
    [ERR-313D6 : Unable to update table or partition P1]
    iSQL> UPDATE T0 SET K = K + 1;
    20 rows updated.
    ```

  -   **예상 결과**

      ```sql
      iSQL> UPDATE T0 SET K = K + 1 WHERE 1 = 1;
      [ERR-313D6 : Unable to update table or partition P1]
      iSQL> UPDATE T0 SET K = K + 1;
      [ERR-313D6 : Unable to update table or partition P1]
      ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-52620<a name=bug-52620></a> 서버 패키지에서 altiMon 분리

-   **module** : ux-altiMon

-   **Category** : Maintainability

-   **재현 빈도** : Always

-   **설명** : 서버 패키지에 포함되어 있던 altiMon 바이너리를 분리하여 서버 패키지에 포함되지 않도록 변경했습니다.

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

### BUG-52629<a name=bug-52629></a> 파티션 테이블에서 CLOB 컬럼 조건으로 SELECT FOR UPDATE 수행 시 잘못된 결과가 반환되는 문제 수정

-   **module** : qp-dml-pvo

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : 파티션 테이블에서 CLOB 컬럼에 대한 `IS NOT NULL` 조건을 사용하여 SELECT FOR UPDATE를 수행할 때, 해당 컬럼의 값이 NULL인 행까지 조회되는 문제를 수정했습니다.

-   **재현 방법**

    -   **재현 절차**

        ```sql
        CREATE TABLE T0 ( ID INTEGER, C CLOB )
        PARTITION BY RANGE ( ID )
        (
          PARTITION P1 VALUES LESS THAN ( 10 ),
          PARTITION P2 VALUES DEFAULT
        ) TABLESPACE SYS_TBS_MEM_DATA;
        INSERT INTO T0 VALUES ( 1, 'x' );
        INSERT INTO T0 VALUES ( 2, NULL );
        INSERT INTO T0 VALUES ( 11, 'x' );
        INSERT INTO T0 VALUES ( 12, NULL );

        SELECT ID FROM T0 WHERE C IS NOT NULL ORDER BY ID;
        SELECT ID FROM T0 WHERE C IS NOT NULL ORDER BY ID FOR UPDATE;
        ```

    -   **수행 결과**

        ```sql
        iSQL> SELECT ID FROM T0 WHERE C IS NOT NULL ORDER BY ID;
        ID
        -------------
        1
        11
        2 rows selected.
        iSQL> SELECT ID FROM T0 WHERE C IS NOT NULL ORDER BY ID FOR UPDATE;
        ID
        -------------
        1
        2
        11
        12
        4 rows selected.
        ```

    -   **예상 결과**

        ```sql
        iSQL> SELECT ID FROM T0 WHERE C IS NOT NULL ORDER BY ID FOR UPDATE;
        ID
        -------------
        1
        11
        2 rows selected.
        ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-52639<a name=bug-52639></a> LIMIT 절의 정수 오버플로 문제 수정

-   **module** : qp-select-pvo

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : LIMIT 절에 32비트 정수 범위를 초과하는 값을 지정할 경우, 정수 오버플로가 발생하는 문제를 수정했습니다.

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

### BUG-52644<a name=bug-52644></a> 파티션 테이블 조회 시 ERR-31455 (Failed to work because an internal exception occurred from an OS) 오류가 발생하는 문제 수정

-   **module** : qp-select-pvo

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : 파티션 테이블에서 Local Index에 대한 INDEX 힌트와 FULL SCAN 힌트를 함께 지정하고 ORDER BY 및 LIMIT 절을 사용하여 조회할 때 `ERR-31455` 오류가 발생하는 문제를 수정했습니다.

-   **재현 방법**

    -   **재현 절차**

        ```sql
        CREATE TABLE T0 ( ID INTEGER, V INTEGER )
        PARTITION BY RANGE ( ID )
        (
          PARTITION P1 VALUES LESS THAN ( 100 ),
          PARTITION P2 VALUES DEFAULT
        ) TABLESPACE SYS_TBS_MEM_DATA;
        INSERT INTO T0 SELECT LEVEL, LEVEL FROM DUAL CONNECT BY LEVEL <= 300;
        CREATE INDEX IDX0 ON T0 ( V ) LOCAL ( PARTITION IDX0_P1 ON P1, PARTITION IDX0_P2 ON P2 );

        SELECT /*+ INDEX(T0, IDX0) FULL SCAN(T0) */ V FROM T0 ORDER BY V LIMIT 1;
        ```

    -   **수행 결과**

        ```sql
        [ERR-31455 : Failed to work because an internal exception occurred from an OS.[Contact Altibase's Support Center]]
        ```

    -   **예상 결과**

            `ERR-31455` 오류가 발생하지 않고 조회 결과가 정상적으로 반환된다.

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
| 7.1.0.11.1       | 6.5.1                   | 8.12.1       | 7.1.7               | 7.4.7                        |

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
