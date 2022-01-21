<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents** 

- [Altibase 7.1.0.5.5 Patch Notes](#altibase-71055-patch-notes)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-48436 잘못 작성된 WRAPPED 구문 사용 시 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-48436%C2%A0%EC%9E%98%EB%AA%BB-%EC%9E%91%EC%84%B1%EB%90%9C-wrapped-%EA%B5%AC%EB%AC%B8-%EC%82%AC%EC%9A%A9-%EC%8B%9C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-48747 AltibaseDatabaseMetaData.getTables() 매개변수에 지원하지 않는 table type이 포함된 경우 Invalid argument 에러가 발생합니다.](#bug-48747%C2%A0altibasedatabasemetadatagettables-%EB%A7%A4%EA%B0%9C%EB%B3%80%EC%88%98%EC%97%90-%EC%A7%80%EC%9B%90%ED%95%98%EC%A7%80-%EC%95%8A%EB%8A%94-table-type%EC%9D%B4-%ED%8F%AC%ED%95%A8%EB%90%9C-%EA%B2%BD%EC%9A%B0-invalid-argument-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-48782 CREATE AS SELECT 으로 해시 파티션 테이블을 생성한 경우 데이터가 파티션 키와 다른 파티션으로 삽입됩니다.](#bug-48782%C2%A0create-as-select-%EC%9C%BC%EB%A1%9C-%ED%95%B4%EC%8B%9C-%ED%8C%8C%ED%8B%B0%EC%85%98-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%9D%84-%EC%83%9D%EC%84%B1%ED%95%9C-%EA%B2%BD%EC%9A%B0-%EB%8D%B0%EC%9D%B4%ED%84%B0%EA%B0%80-%ED%8C%8C%ED%8B%B0%EC%85%98-%ED%82%A4%EC%99%80-%EB%8B%A4%EB%A5%B8-%ED%8C%8C%ED%8B%B0%EC%85%98%EC%9C%BC%EB%A1%9C-%EC%82%BD%EC%9E%85%EB%90%A9%EB%8B%88%EB%8B%A4)
    - [BUG-48850 레코드가 0 건인 테이블에 그룹 함수 LISTAGG 사용 시 Altibase 서버 비정상 종료합니다.](#bug-48850%C2%A0%EB%A0%88%EC%BD%94%EB%93%9C%EA%B0%80-0-%EA%B1%B4%EC%9D%B8-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90-%EA%B7%B8%EB%A3%B9-%ED%95%A8%EC%88%98-listagg-%EC%82%AC%EC%9A%A9-%EC%8B%9C-altibase-%EC%84%9C%EB%B2%84-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-48883 인라인 뷰 SELECT 절에 사용한 컬럼 수가 QUERY\_STACK\_SIZE를 초과한 경우 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-48883%EC%9D%B8%EB%9D%BC%EC%9D%B8-%EB%B7%B0-select-%EC%A0%88%EC%97%90-%EC%82%AC%EC%9A%A9%ED%95%9C-%EC%BB%AC%EB%9F%BC-%EC%88%98%EA%B0%80-query%5C_stack%5C_size%EB%A5%BC-%EC%B4%88%EA%B3%BC%ED%95%9C-%EA%B2%BD%EC%9A%B0-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Altibase 7.1.0.5.5 Patch Notes
==============================



Fixed Bugs
----------

### BUG-48436 잘못 작성된 WRAPPED 구문 사용 시 Altibase 서버가 비정상 종료할 수 있습니다.

-   **module** : qp-psm-trigger-pvo

-   **Category** : Fatal

-   **재현 빈도** : Frequence

-   **설명** : 잘못 작성된 WRAPPED 구문 사용 시 Altibase 서버가 비정상 종료하는 현상을 수정했습니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    CREATE OR REPLACE PACKAGE PKG1 WRAPPED 'NTQNJAAZ';
    CREATE OR REPLACE PACKAGE PKG2 WRAPPED 'MTUZMTZ';
    CREATE OR REPLACE PROCEDURE PROC1 WRAPPED 'MJZ ';
    ```

  -   **수행 결과**

          Altibase 서버 비정상 종료

  -   **예상 결과**

      ```sql
      ERR-010D4 : Malformed or corrupted wrapped unit.
      ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48747 AltibaseDatabaseMetaData.getTables() 매개변수에 지원하지 않는 table type이 포함된 경우 Invalid argument 에러가 발생합니다.

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : AltibaseDatabaseMetaData.getTables() 매개변수에 지원하지 않는 table type이 포함된 경우 Invalid argument 에러가 발생하는 현상을 수정하였습니다.
    
- **재현 방법**

  - **재현 절차**

    ```java
    Connection sConn = getConnection("20300");
    DatabaseMetaData sMeta = sConn.getMetaData();
    ResultSet sRs = sMeta.getTables(null,null,null, new String[] { "TABLE", "ALIAS" });
    int sCnt = 0;
    while (sRs.next())
    {    sCnt++;}
    System.out.println("Count =>" + sCnt);
    ```

  - **수행 결과**

    ```java
    Exception in thread "main" java.sql.SQLException: Invalid argument: Table type: TABLE | SYSTEM TABLE | VIEW | SYSTEM VIEW | MATERIALIZED VIEW | QUEUE | SYNONYM | SEQUENCE expected, but ALIAS   at Altibase.jdbc.driver.ex.Error.throwSQLExceptionInternal(Error.java:189)  at Altibase.jdbc.driver.ex.Error.throwSQLException(Error.java:182)  at Altibase.jdbc.driver.AltibaseDatabaseMetaData.checkTableTypes(AltibaseDatabaseMetaData.java:843) at Altibase.jdbc.driver.AltibaseDatabaseMetaData.getTables(AltibaseDatabaseMetaData.java:872)   at GetTablesTest.doTest(GetTablesTest.java:32)  at GetTablesTest.main(GetTablesTest.java:25)
    ```

  -   **예상 결과**

      ```java
      No Errors.
      ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48782 CREATE AS SELECT 으로 해시 파티션 테이블을 생성한 경우 데이터가 파티션 키와 다른 파티션으로 삽입됩니다.

-   **module** : qp-select-execute

-   **Category** : Reliability

-   **재현 빈도** : Always

-   **설명** : CREATE AS SELECT 으로 해시 파티션 테이블을 생성한 경우 데이터가 파티션 키와 다른 파티션으로 삽입되는 문제를 수정했습니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    DROP TABLE T2;
    DROP TABLE B;
    
    CREATE TABLE T2 ( I1 INTEGER, I2 INTEGER, I3 INTEGER )
    PARTITION BY HASH(I1)
    ( PARTITION P1,
      PARTITION P2,
      PARTITION PD ) TABLESPACE SYS_TBS_DISK_DATA
    ;
    
    INSERT INTO T2 VALUES( 2, 2, 2 );
    
    CREATE TABLE B
    PARTITION BY HASH(I1) 
    ( PARTITION P1,
      PARTITION P2,
      PARTITION PD ) TABLESPACE SYS_TBS_DISK_DATA
    AS SELECT * FROM T2;
    
    SELECT * FROM B WHERE I1 = 2;
    ```

  - **수행 결과**

    ```sql
    SELECT * FROM B WHERE I1 = 2;
    B.I1        B.I2        B.I3
    ----------------------------------------
    No rows selected.
    ```

  -   **예상 결과**

      ```sql
      SELECT * FROM B WHERE I1 = 2;
      B.I1        B.I2        B.I3
      ----------------------------------------
      2           2           2
      1 row selected.
      ```

-   **Workaround**

        N/A

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48850 레코드가 0 건인 테이블에 그룹 함수 LISTAGG 사용 시 Altibase 서버 비정상 종료합니다.

-   **module** : qp

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : 레코드가 0 건인 테이블에 그룹 함수 LISTAGG 사용 시 Altibase 서버가 비정상 종료하는 현상을 수정합니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    DROP TABLE BUG_48850;
    
    CREATE TABLE BUG_48850 ( C1 INT PRIMARY KEY, C2 INT, C3 INT ) ;
    INSERT INTO BUG_48850 VALUES(1, 1, 1);
    
    SELECT LISTAGG( C3 ) WITHIN GROUP(ORDER BY C1 ) OVER ( PARTITION BY C2 ORDER BY C1 )
      FROM BUG_48850;
    ```

  - **수행 결과**

    ```sql
    ERR-91015 : Communication failure.
    Altibase 서버 비정상 종료
    ```

  - **예상 결과**

    ```sql
    ISTAGG(C3)WITHINGROUP(ORDERBYC1)OVER(PART  
    ----------------------------------------------
    No rows selected.
    ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property

    -   Compile Option

    -   Error Code

### BUG-48883 인라인 뷰 SELECT 절에 사용한 컬럼 수가 QUERY\_STACK\_SIZE를 초과한 경우 Altibase 서버가 비정상 종료할 수 있습니다.

-   **module** : qp-dml-execute

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : 아래 조건을 만족하는 상황에서 Altibase 서버가 비정상 종료하는 현상을 예외 처리하여 ERR-21013 : Calculation stack overflow 에러가 발생하도록 수정했습니다.
    
    - 인라인 뷰 SELECT 절에 사용한 컬럼 수가 STACK SIZE를 초과하고 

    - 메인 쿼리 SELECT 절에서 사용한 컬럼 수가 인라인 뷰 SELECT 절에서 사용한 컬럼 수보다 적은 경우

- **재현 방법**

  - **재현 절차**

    ```sql
    ALTER SESSION SET STACK SIZE = 8;
    SELECT NAME, VALUE1, MIN, MAX FROM V$PROPERTY WHERE NAME = 'QUERY_STACK_SIZE';
    ```

  - **수행 결과**

    ```sql
    ERR-91015 : Communication failure.
    ```

  -   **예상 결과**

      ```sql
      ERR-21013 : Calculation stack overflow
      ```

- **Workaround**

  ```sql
  ALTER SESSION SET STACK SIZE = 128;
  또는
  ALTER SYSTEM SET __OPTIMIZER_VIEW_TARGET_ENABLE = 0;
  ```

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
|    7.1.0.5.5     |          6.5.1          |    8.9.1     |        7.1.7        |            7.4.6             |

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
