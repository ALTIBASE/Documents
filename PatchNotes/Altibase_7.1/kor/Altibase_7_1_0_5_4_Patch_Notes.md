**Table of Contents**  

- [Altibase 7.1.0.5.4 Patch Notes](#altibase-71054-patch-notes)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-48746 ALTER REPLICATION ~ SYNC 수행 시 altibase_rp_conflict.log 에 ERR-11089(errno=62) Invalid column size 에러가 발생하며 Altibase 서버가 비정상 종료합니다.](#bug-48746alter-replication--sync-%EC%88%98%ED%96%89-%EC%8B%9C-altibase_rp_conflictlog-%EC%97%90-err-11089errno62-invalid-column-size-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%98%EB%A9%B0-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-48761 온라인 로그파일 open() 실패 시 Altibase 서버가 비정상 종료합니다.](#bug-48761%EC%98%A8%EB%9D%BC%EC%9D%B8-%EB%A1%9C%EA%B7%B8%ED%8C%8C%EC%9D%BC-open-%EC%8B%A4%ED%8C%A8-%EC%8B%9C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-48792 SELECT DISTINCT 와 GROUP BY CUBE 절이 뷰에서 사용될 경우 결과 오류가 발생합니다.](#bug-48792select-distinct-%EC%99%80-group-by-cube-%EC%A0%88%EC%9D%B4-%EB%B7%B0%EC%97%90%EC%84%9C-%EC%82%AC%EC%9A%A9%EB%90%A0-%EA%B2%BD%EC%9A%B0-%EA%B2%B0%EA%B3%BC-%EC%98%A4%EB%A5%98%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-48800 FORM 절에 파티션을 지정하고 WHERE 절에서 파티션 키 범위가 아닌 조건을 사용한 SELECT 문에서 결과 오류가 발생할 수 있습니다.](#bug-48800form-%EC%A0%88%EC%97%90-%ED%8C%8C%ED%8B%B0%EC%85%98%EC%9D%84-%EC%A7%80%EC%A0%95%ED%95%98%EA%B3%A0-where-%EC%A0%88%EC%97%90%EC%84%9C-%ED%8C%8C%ED%8B%B0%EC%85%98-%ED%82%A4-%EB%B2%94%EC%9C%84%EA%B0%80-%EC%95%84%EB%8B%8C-%EC%A1%B0%EA%B1%B4%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%9C-select-%EB%AC%B8%EC%97%90%EC%84%9C-%EA%B2%B0%EA%B3%BC-%EC%98%A4%EB%A5%98%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)



Altibase 7.1.0.5.4 Patch Notes
==============================

Fixed Bugs
----------

### BUG-48746 ALTER REPLICATION ~ SYNC 수행 시 altibase_rp_conflict.log 에 ERR-11089(errno=62) Invalid column size 에러가 발생하며 Altibase 서버가 비정상 종료합니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** :

- **재현 방법**

  - **재현 절차**

    ```
    아래 조건을 모두 만족하는 경우 발생할 수 있습니다. 
    
    1) Altibase 7.1.0.1.2 이상
    2) 메모리 테이블
    3) VARIABLE 컬럼을 포함한 이중화 대상 테이블
    4) ALTER REPLICATION ~ SYNC 수행 
    ```

  - **수행 결과**

    ```
    Altibase 서버 비정상 종료
    ```

  - **예상 결과**

    ```
    ALTER REPLICATION ~ SYNC 정상 수행
    ```

- **Workaround**

  ```
  VARIABLE 컬럼을 FIXED 로 변경
  ```

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48761 온라인 로그파일 open() 실패 시 Altibase 서버가 비정상 종료합니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Rare

-   **설명** : 온라인 로그파일을 open() 할 때 파일시스템 용량 부족 또는 open file 수 제한으로 실패할 경우 트레이스 로그 파일에 기록후 성공할 때까지 재시도 하도록 수정하였습니다. 그 외의 이유로 open() 이 실패할 경우 기존처럼 동작합니다.
    
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

### BUG-48792 SELECT DISTINCT 와 GROUP BY CUBE 절이 뷰에서 사용될 경우 결과 오류가 발생합니다.

-   **module** : qp-dml-execute

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : SELECT DISTINCT 와 GROUP BY CUBE 절이 뷰에서 사용될 경우 결과 오류가 발생하는 현상을 개선하였습니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    DROP TABLE T1;
    CREATE TABLE T1( I1 INTEGER, I2 INTEGER, I3 INTEGER, I4 INTEGER );
    INSERT INTO T1 VALUES (1,1,1,1);
    INSERT INTO T1 VALUES (1,1,1,2);
    INSERT INTO T1 VALUES (1,1,2,3);
    INSERT INTO T1 VALUES (1,2,2,4);
    INSERT INTO T1 VALUES (2,2,3,5);
    INSERT INTO T1 VALUES (2,2,3,6);
    INSERT INTO T1 VALUES (2,3,4,7);
    INSERT INTO T1 VALUES (2,3,4,8);
    INSERT INTO T1 VALUES (3,1,1,1);
    INSERT INTO T1 VALUES (3,1,1,2);
    SELECT * FROM ( SELECT /*+*/ DISTINCT I1, COUNT( I2) FROM T1 GROUP BY CUBE(I1) ) ;
    ```

  - **수행 결과**

    ```sql
    I1          COUNT( I2)
    ------------------------------------
    3           10
    3           4
    3           4
    3           2
    4 rows selected.
    ```

  -   **예상 결과**

      ```sql
      I1          COUNT( I2)
      ------------------------------------            
                  10
      1           4
      2           4
      3           24
      rows selected.
      ```

- **Workaround**

  ```sql
  GROUP BY GROUPING SETS 사용
  ```

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48800 FORM 절에 파티션을 지정하고 WHERE 절에서 파티션 키 범위가 아닌 조건을 사용한 SELECT 문에서 결과 오류가 발생할 수 있습니다.

-   **module** : qp-dml-pvo

-   **Category** : Functional Error

-   **재현 빈도** : Frequence

-   **설명** : FORM 절에 파티션을 지정하고 WHERE 절에서 파티션 키 범위가 아닌 조건을 사용한 SELECT 문에서 결과 오류가 발생할 수 있습니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    DROP TABLE T1;
    CREATE TABLE T1 (I1 INT, I2 INT)
         PARTITION BY RANGE(I1)
         (
             PARTITION P1 VALUES LESS THAN (100),
             PARTITION P2 VALUES LESS THAN (200),
             PARTITION P3 VALUES DEFAULT
         );
    INSERT INTO T1 VALUES ( 130, 100 );
    SELECT /*+ NO_EXEC_FAST */ * FROM T1 PARTITION(P1) WHERE I1 = 130;
    ALTER TABLE T1 MERGE PARTITIONS P1, P2 INTO PARTITION P1;
    SELECT /*+ NO_EXEC_FAST */ * FROM T1 PARTITION(P1) WHERE I1 = 130;
    ```

  - **수행 결과**

    ```sql
    -- 첫 select 쿼리
    T1.I1       T1.I2
    ---------------------------
    No rows selected.
    ------------------------------------------------------------
    PROJECT ( COLUMN_COUNT: 2, TUPLE_SIZE: 8, COST: BLOCKED )
     PARTITION-COORDINATOR ( TABLE: SYS.T1, PARTITION: 0/3, FULL SCAN, ACCESS: 0, COST: BLOCKED )
    ------------------------------------------------------------
    
    -- merge 후 두 번째 select 쿼리
    T1.I1       T1.I2
    ---------------------------
    No rows selected.
    ------------------------------------------------------------
    PROJECT ( COLUMN_COUNT: 2, TUPLE_SIZE: 8, COST: BLOCKED )
     PARTITION-COORDINATOR ( TABLE: SYS.T1, PARTITION: 0/3, FULL SCAN, ACCESS: 0, COST: BLOCKED )
    ------------------------------------------------------------
    ```

  -   **예상 결과**

      ```sql
      -- 첫 select 쿼리
      T1.I1       T1.I2
      ---------------------------
      No rows selected.
      ------------------------------------------------------------
      PROJECT ( COLUMN_COUNT: 2, TUPLE_SIZE: 8, COST: BLOCKED )
       PARTITION-COORDINATOR ( TABLE: SYS.T1, PARTITION: 0/3, FULL SCAN, ACCESS: 0, COST: BLOCKED )
      ------------------------------------------------------------
      
      -- merge 후 두 번째 select 쿼리
      T1.I1       T1.I2
      ---------------------------
      130         100
      1 row selected.
      ------------------------------------------------------------
      PROJECT ( COLUMN_COUNT: 2, TUPLE_SIZE: 8, COST: BLOCKED )
       PARTITION-COORDINATOR ( TABLE: SYS.T1, PARTITION: 1/2, FULL SCAN, ACCESS: 1, COST: BLOCKED )
        SCAN ( PARTITION: P1, FULL SCAN, ACCESS: 1, COST: BLOCKED )
      ------------------------------------------------------------
      ```

- **Workaround**

  ```sql
  NO_PLAN_CACHE 힌트 사용.
  
  iSQL> SELECT /*+ NO_EXEC_FAST NO_PLAN_CACHE */ * FROM T1 PARTITION(P1) WHERE I1 = 130;
  I1          I2          
  ---------------------------
  130         100         
  1 row selected.
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
|    7.1.0.5.4     |          6.5.1          |    8.9.1     |        7.1.7        |            7.4.6             |

> Altibase 7.1 패치 버전별 히스토리는 [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.1/Altibase_7_1_Version_Histories.md)에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

#### Meta Version

메타 버전은 변경되지 않았다.

#### CM protocol Version

통신 프로토콜 버전은 변경되지 않았다.

#### Replication protocol Version

Replication 프로토콜 버전은 변경되지 않았다.

### 프로퍼티

#### 추가된 프로퍼티

#### 변경된 프로퍼티

#### 삭제된 프로퍼티

### 성능 뷰

#### 추가된 성능 뷰

#### 변경된 성능 뷰

#### 삭제된 성능 뷰
