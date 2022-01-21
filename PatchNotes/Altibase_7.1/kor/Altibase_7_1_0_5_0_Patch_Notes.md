<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Altibase 7.1.0.5.0 Patch Notes](#altibase-71050-patch-notes)
  - [New Features](#new-features)
    - [BUG-48336 서브쿼리 Unnesting 대상 조건에서 제외하기 위한 기능을 추가합니다.](#bug-48336%EC%84%9C%EB%B8%8C%EC%BF%BC%EB%A6%AC-unnesting-%EB%8C%80%EC%83%81-%EC%A1%B0%EA%B1%B4%EC%97%90%EC%84%9C-%EC%A0%9C%EC%99%B8%ED%95%98%EA%B8%B0-%EC%9C%84%ED%95%9C-%EA%B8%B0%EB%8A%A5%EC%9D%84-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-48358 aexport 수행 시 run_il_out.sh 파일에 -geom WKB 를 추가하기 위한 옵션을 제공합니다.](#bug-48358aexport-%EC%88%98%ED%96%89-%EC%8B%9C-run_il_outsh-%ED%8C%8C%EC%9D%BC%EC%97%90--geom-wkb-%EB%A5%BC-%EC%B6%94%EA%B0%80%ED%95%98%EA%B8%B0-%EC%9C%84%ED%95%9C-%EC%98%B5%EC%85%98%EC%9D%84-%EC%A0%9C%EA%B3%B5%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-48381 집합 연산자를 포함한 서브쿼리가 쿼리 변환 과정에서 DNF로 풀릴 경우 ERR-31455 : Failed to work because an internal exception occurred from an OS.[Contact Altibase's Support Center] 에러가 발생합니다.](#bug-48381%EC%A7%91%ED%95%A9-%EC%97%B0%EC%82%B0%EC%9E%90%EB%A5%BC-%ED%8F%AC%ED%95%A8%ED%95%9C-%EC%84%9C%EB%B8%8C%EC%BF%BC%EB%A6%AC%EA%B0%80-%EC%BF%BC%EB%A6%AC-%EB%B3%80%ED%99%98-%EA%B3%BC%EC%A0%95%EC%97%90%EC%84%9C-dnf%EB%A1%9C-%ED%92%80%EB%A6%B4-%EA%B2%BD%EC%9A%B0-err-31455--failed-to-work-because-an-internal-exception-occurred-from-an-oscontact-altibases-support-center-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-48405 OPTIMIZER_ANSI_JOIN_ORDERING = 1 이고 LEFT OUTER JOIN 과 다른 JOIN 이 함께 사용된 경우 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-48405optimizer_ansi_join_ordering--1-%EC%9D%B4%EA%B3%A0-left-outer-join-%EA%B3%BC-%EB%8B%A4%EB%A5%B8-join-%EC%9D%B4-%ED%95%A8%EA%BB%98-%EC%82%AC%EC%9A%A9%EB%90%9C-%EA%B2%BD%EC%9A%B0-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-48419 서브쿼리 Unnesting 제외 조건에 해당하지만, 뷰 머징(View Merging) 이 발생한 경우 서브쿼리 Unnesting 이 발생합니다.](#bug-48419%EC%84%9C%EB%B8%8C%EC%BF%BC%EB%A6%AC-unnesting-%EC%A0%9C%EC%99%B8-%EC%A1%B0%EA%B1%B4%EC%97%90-%ED%95%B4%EB%8B%B9%ED%95%98%EC%A7%80%EB%A7%8C-%EB%B7%B0-%EB%A8%B8%EC%A7%95view-merging-%EC%9D%B4-%EB%B0%9C%EC%83%9D%ED%95%9C-%EA%B2%BD%EC%9A%B0-%EC%84%9C%EB%B8%8C%EC%BF%BC%EB%A6%AC-unnesting-%EC%9D%B4-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-48429 세션 타임아웃 조건에서도 세션이 종료되지 않는 현상 분석을 위한 디버깅 정보를 추가합니다.](#bug-48429%EC%84%B8%EC%85%98-%ED%83%80%EC%9E%84%EC%95%84%EC%9B%83-%EC%A1%B0%EA%B1%B4%EC%97%90%EC%84%9C%EB%8F%84-%EC%84%B8%EC%85%98%EC%9D%B4-%EC%A2%85%EB%A3%8C%EB%90%98%EC%A7%80-%EC%95%8A%EB%8A%94-%ED%98%84%EC%83%81-%EB%B6%84%EC%84%9D%EC%9D%84-%EC%9C%84%ED%95%9C-%EB%94%94%EB%B2%84%EA%B9%85-%EC%A0%95%EB%B3%B4%EB%A5%BC-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Altibase 7.1.0.5.0 Patch Notes
==============================

New Features
------------

### BUG-48336 서브쿼리 Unnesting 대상 조건에서 제외하기 위한 기능을 추가합니다.

-   **module** : qp-dml-pvo

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **증상** : 특정 상황에서 서브쿼리 Unnesting 성능이 느린 경우
    unnesting 하지 않도록 서브쿼리 Unnesting 대상 조건에서 제외하는 기능을 추가합니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    DROP TABLE T1;   
    CREATE TABLE T1 ( I1 INT, I2 INT, I3 INT, I4 INT) ;
    INSERT INTO T1 (SELECT LEVEL, LEVEL, MOD(LEVEL,10), LEVEL FROM DUAL CONNECT BY LEVEL <= 100000);
    ALTER SESSION SET EXPLAIN PLAN = ON;
    ALTER SYSTEM SET __OPTIMIZER_UNNEST_COMPATIBILITY = 0;
    SELECT COUNT(*)
     FROM T1 A LEFT OUTER JOIN T1 B ON A.I1 = B.I1
          LEFT OUTER JOIN T1 C ON B.I1 = C.I1 LEFT OUTER JOIN T1 D ON C.I1 = D.I1 LEFT OUTER JOIN T1 E ON D.I1 = E.I1
     WHERE A.I2 IN (SELECT /*+ NO_INVERSE_JOIN */ I2
                      FROM T1 F
                     WHERE I3 = 0);
    ```

  - **수행 결과**

    ```sql
    10000 rows selected.
    ------------------------------------------------------------
    PROJECT ( COLUMN_COUNT: 20, TUPLE_SIZE: 80, COST: 562517886347943.06 )
     SEMI-JOIN ( METHOD: HASH, COST: 559615345990377.81 )
      LEFT-OUTER-JOIN INVERSE ( METHOD: HASH, COST: 43964924059972.31 )
       SCAN ( TABLE: SYS.T1 E, FULL SCAN, ACCESS: 100000, COST: 116.76 )
       HASH ( ITEM_SIZE: 48, ITEM_COUNT: 100000, BUCKET_COUNT: 16384, ACCESS: 100000, COST: 43964924059972.31 )
        LEFT-OUTER-JOIN INVERSE ( METHOD: HASH, COST: 42930304986.08 )
         SCAN ( TABLE: SYS.T1 D, FULL SCAN, ACCESS: 100000, COST: 116.76 )
         HASH ( ITEM_SIZE: 40, ITEM_COUNT: 100000, BUCKET_COUNT: 16384, ACCESS: 100000, COST: 42930304986.08 )
    LEFT-OUTER-JOIN INVERSE ( METHOD: HASH, COST: 41920810.10 )
    SCAN ( TABLE: SYS.T1 C, FULL SCAN, ACCESS: 100000, COST: 116.76 )
    HASH ( ITEM_SIZE: 32, ITEM_COUNT: 100000, BUCKET_COUNT: 16384, ACCESS: 100000, COST: 41920810.10 )
    LEFT-OUTER-JOIN ( METHOD: HASH, COST: 41243.85 )
    SCAN ( TABLE: SYS.T1 A, FULL SCAN, ACCESS: 100000, COST: 116.76 )
    HASH ( ITEM_SIZE: 24, ITEM_COUNT: 100000, BUCKET_COUNT: 16384, ACCESS: 100000, COST: 41243.85 )
    SCAN ( TABLE: SYS.T1 B, FULL SCAN, ACCESS: 100000, COST: 116.76 )
      HASH ( ITEM_SIZE: 24, ITEM_COUNT: 10000, BUCKET_COUNT: 1024, ACCESS: 10000, COST: 559615345990377.81 )
       SCAN ( TABLE: SYS.T1 $$1_$$VIEW1_$F, FULL SCAN, ACCESS: 100000, COST: 120.72 )
    ------------------------------------------------------------
    ```

  -   **예상 결과**

      ```sql
      10000 rows selected.
      ------------------------------------------------------------
      PROJECT ( COLUMN_COUNT: 20, TUPLE_SIZE: 80, COST: 24330109213100.52 )
       LEFT-OUTER-JOIN INVERSE ( METHOD: HASH, COST: 14654974687883.07 )
        SCAN ( TABLE: SYS.T1 E, FULL SCAN, ACCESS: 100000, COST: 116.76 )
        HASH ( ITEM_SIZE: 48, ITEM_COUNT: 10000, BUCKET_COUNT: 1024, ACCESS: 10000, COST: 14654974687883.07 )
         LEFT-OUTER-JOIN INVERSE ( METHOD: HASH, COST: 14310102575.13 )
          SCAN ( TABLE: SYS.T1 D, FULL SCAN, ACCESS: 100000, COST: 116.76 )
          HASH ( ITEM_SIZE: 40, ITEM_COUNT: 10000, BUCKET_COUNT: 1024, ACCESS: 10000, COST: 14310102575.13 )
           LEFT-OUTER-JOIN INVERSE ( METHOD: HASH, COST: 13974203.94 )
      SCAN ( TABLE: SYS.T1 C, FULL SCAN, ACCESS: 100000, COST: 116.76 )
      HASH ( ITEM_SIZE: 32, ITEM_COUNT: 10000, BUCKET_COUNT: 1024, ACCESS: 10000, COST: 13974203.94 )
      LEFT-OUTER-JOIN ( METHOD: HASH, COST: 14035.99 )
      SCAN ( TABLE: SYS.T1 A, FULL SCAN, ACCESS: 100000, COST: 242.89 )
      ::SUB-QUERY BEGIN
      PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: 120.85 )
      HASH ( ITEM_SIZE: 24, ITEM_COUNT: 10000, BUCKET_COUNT: 16384, ACCESS: 10000, COST: 0.00 )
      VIEW ( ACCESS: 10000, COST: 0.00 )
      PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: 120.85 )
      SCAN ( TABLE: SYS.T1 F, FULL SCAN, ACCESS: 100000, COST: 120.72 )
      ::SUB-QUERY END
      HASH ( ITEM_SIZE: 24, ITEM_COUNT: 100000, BUCKET_COUNT: 16384, ACCESS: 10000, COST: 14035.99 )
      SCAN ( TABLE: SYS.T1 B, FULL SCAN, ACCESS: 100000, COST: 116.76 )
      ------------------------------------------------------------
      ```

- **Workaround**

  ```sql
  NO_UNNEST 힌트를 사용합니다. 
  
  SELECT COUNT(*)
   FROM T1 A LEFT OUTER JOIN T1 B ON A.I1 = B.I1
        LEFT OUTER JOIN T1 C ON B.I1 = C.I1 LEFT OUTER JOIN T1 D ON C.I1 = D.I1 LEFT OUTER JOIN T1 E ON D.I1 = E.I1
   WHERE A.I2 IN (SELECT /*+ NO_INVERSE_JOIN NO_UNNEST */ I2
                    FROM T1 F
                   WHERE I3 = 0);
  ```

- **변경사항**

  - Performance view

  - Property

    - __OPTIMIZER_UNNEST_COMPATIBILITY 

      - 속성 설명 : Subquery unnest에 대한 하위호환성 프로퍼티

      - 변경/추가/삭제 : 모드 2가 추가되었습니다.
        __OPTIMIZER_UNNEST_COMPATIBILITY =2 를 사용하면 기존과 동일하게 unnest 플랜으로 동작합니다.

      - 공개/비공개 : 비공개

      - 최소값, 최대값, 기본값 : 0, 3, 3

        기본값이 1에서 3으로 변경되었지만, 기본값의 동작에는 영향없습니다. 

  - Compile Option

  -   Error Code

### BUG-48358 aexport 수행 시 run_il_out.sh 파일에 -geom WKB 를 추가하기 위한 옵션을 제공합니다.

-   **module** : ux-aexport

-   **Category** : Enhancement

-   **재현 빈도** : Always

- **증상** : aexport 프로퍼티 ILOADER_GEOM_FORMAT 이 추가되었습니다.

  aexport.properties 파일에 ILOADER_GEOM_FORMAT = WKB 옵션을 사용한 경우 run_il_out.sh 파일에 -geom WKB 옵션이 추가된 iloader 명령문이 저장됩니다.

  Altibase 7.1.0.4.0 이상에서 EWKT(Extended Well-Known Text) 형식으로 공간 데이터가 입력된 경우 사용합니다.

  ```sql
  CREATE TABLE TB3(ID INTEGER PRIMARY KEY, OBJ GEOMETRY);
      
  // ID 121, 123 데이터는 WKT 형식으로 입력, 122, 124 데이터는 EWKT 형식으로 입력
  INSERT INTO TB3 VALUES (121, ST_POLYGONFROMTEXT('POLYGON((10 10, 10 20, 20 20, 20 15, 10 10))'));
  INSERT INTO TB3 VALUES (122, ST_POLYGONFROMTEXT('POLYGON((10 10, 10 20, 20 20, 20 15, 10 10))', 100));
  INSERT INTO TB3 VALUES (123, ST_POLYGONFROMTEXT('MULTILINESTRING((10 10, 20 20), (15 15, 30 15))'));
  INSERT INTO TB3 VALUES (124, ST_POLYGONFROMTEXT('SRID=100;POLYGON((10 10, 10 20, 20 20, 20 15, 10 10))'));
  ```

  - ILOADER_GEOM_FORMAT 프로퍼티 사용 없이 aexport 수행한 경우

    - run_il_out.sh 결과

      ```bash
      iloader -s localhost -u SYS -p manager out -f SYS_TB3.fmt -d SYS_TB3.dat -log SYS_TB3.log -NLS_USE UTF8
      ```

    - EWKT형식을 지원하지 않는  Altibase 7.1.0.4.0 이전 버전으로 iloader in 수행 시 ERR-A1018 에러가 발생합니다.

      ```bash
      Load Count  : 2(TB3)
      Error Count : 2
      
      cat SYS_TB3.log
      Record 2 : 122,[GEOMETRY]
      [ERR-A1018 : The specified object type is not currently supported.]
      Record 4 : 124,[GEOMETRY]
      [ERR-A1018 : The specified object type is not currently supported.]
      ```

  - aexport.properties 파일에 ILOADER_GEOM_FORMAT 프로퍼티 추가 후 aexport 수행한 경우

    - run_il_out.sh 결과

      ```bash
      iloader -s localhost -u SYS -p manager out -f SYS_TB3.fmt -d SYS_TB3.dat -log SYS_TB3.log -NLS_USE UTF8 -geom WKB
      ```

    - EWKT형식을 지원하지 않는 Altibase 7.1.0.4.0 이전 버전으로 iloader in 수행 결과   

      ```bash
      Load Count  : 4(TB3) 
      ```

- **재현 방법**
  - *재현 절차**
  - **수행 결과**
  - **예상 결과**

-   **Workaround**

- **변경사항**

  -   Performance view

  -   Property
      -   aexport 프로퍼티 ILOADER_GEOM_FORMAT 이 추가되었습니다. 

  -   Compile Option

  -   Error Code

Fixed Bugs
----------

### BUG-48381 집합 연산자를 포함한 서브쿼리가 쿼리 변환 과정에서 DNF로 풀릴 경우 ERR-31455 : Failed to work because an internal exception occurred from an OS.[Contact Altibase's Support Center] 에러가 발생합니다.

-   **module** : qp-select-pvo

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **증상** : 집합 연산자를 포함한 서브쿼리가 쿼리 변환 과정에서 DNF로 풀릴 경우 ERR-31455 : Failed to work because an internal exception occurred from an OS.[Contact Altibase's Support Center] 에러 발생 현상을 개선하였습니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    DROP TABLE t1;
    DROP TABLE t2;
    CREATE TABLE t1 (i1 INT, i2 INT, i3 INT, i4 INT);
    CREATE TABLE t2 (i1 INT, i2 INT, i3 INT);
    
    ALTER TABLE t1 ADD PRIMARY KEY (i1, i2, i3);
    
    SELECT *
      FROM t1
     WHERE i1 = :A
       AND i2 = (SELECT i2 FROM t1 WHERE i1 = 1
                  UNION ALL
                 SELECT i2 FROM t2 WHERE i1 < 0)
       AND i3 IN (1,2,3,4,5,6,7,8,9,10);
    ```

  - **수행 결과**

    ```sql
    [ERR-31455 : Failed to work because an internal exception occurred from an OS.[Contact Altibase's Support Center]]
    ```

  -   **예상 결과**

          에러가 발생하지 않음.

-   **Workaround**

        /*+ full scan(t1) */ 힌트 사용또는CSE를 비활성화(__OPTIMIZER_ELIMINATE_COMMON_SUBEXPRESSION = 0)합니다. 

- **변경사항**

  -   Performance view

  -   Property

  -   Compile Option

  -   Error Code

### BUG-48405 OPTIMIZER_ANSI_JOIN_ORDERING = 1 이고 LEFT OUTER JOIN 과 다른 JOIN 이 함께 사용된 경우 Altibase 서버가 비정상 종료할 수 있습니다.

-   **module** : qp-select-pvo

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **증상** : OPTIMIZER_ANSI_JOIN_ORDERING = 1 에서 Altibase 서버가 비정상 종료하거나 결과 오류가 발생하는 현상을 수정했습니다.
    

아래 조건을 모두 만족하는 경우 발생할 수 있습니다.
    
- OPTIMIZER_ANSI_JOIN_ORDERING = 1
  
- LEFT OUTER JOIN 이 2개 이상 사용되고 다른 JOIN 함께 사용된 경우
  
- **재현 방법**

  - **재현 절차**

    ```sql
    DROP TABLE t1;
    CREATE TABLE t1 (i1 INT, i2 INT, i3 INT);
    
    INSERT INTO t1 VALUES (1, 1, 1);
    
    ALTER SYSTEM SET OPTIMIZER_ANSI_JOIN_ORDERING = 1;
    
    SELECT /*+ USE_HASH(D C) */ *
      FROM t1 a LEFT OUTER JOIN t1 b ON a.i1 = b.i1 INNER JOIN t1 c ON a.i1 = c.i1     LEFT OUTER JOIN t1 d ON d.i1 = a.i1
       AND d.i2 <= c.i2
       AND d.i3 >= c.i3;
    ```

  -   **수행 결과**

          Altibase 서버가 비정상 종료합니다. 

  -   **예상 결과**

      ```sql
      I1          I2          I3          I1          I2          I3          I1          I2          I3          I1          I2          I3          
      -------------------------------------------------------------------------------------------------------------------------------------------------------------
      1           1           1           1           1           1           1           1           1           1           1           1           
      1 row selected.
      ```

-   **Workaround**

        ALTER SYSTEM SET OPTIMIZER_ANSI_JOIN_ORDERING = 0;
        재현 케이스의 경우 힌트를 사용하여 조인 순서를 변경합니다. 
        /*+ USE_HASH(C D) */

- **변경사항**

  -   Performance view

  -   Property

  -   Compile Option

  -   Error Code

### BUG-48419 서브쿼리 Unnesting 제외 조건에 해당하지만, 뷰 머징(View Merging) 이 발생한 경우 서브쿼리 Unnesting 이 발생합니다.

-   **module** : qp-select-pvo

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : 서브쿼리 Unnesting 제외 조건에 해당하지만, 뷰 머징(View Merging) 이 발생한 경우 서브쿼리 Unnesting 이 발생하는 문제를 수정했습니다. 

- **재현 방법**

  - **재현 절차**

    ```sql
    CREATE TABLE T1 (I1 INT, I2 INT, I3 INT);
    CREATE TABLE T2 (I1 INT, I2 INT, I3 INT);
    
    ALTER SYSTEM SET __OPTIMIZER_UNNEST_COMPATIBILITY = 0;
    ALTER SESSION SET EXPLAIN PLAN = ONLY;
    
    WITH TMP_HDD
    AS
    (SELECT *
       FROM T1 A LEFT OUTER JOIN T1 B ON A.I2 = B.I2
      WHERE A.I1 IN (SELECT I1 FROM T2) )
    SELECT /*+ NO_PLAN_CACHE */ *
    FROM TMP_HDD ;
    ```

  - **수행 결과**

    ```sql
    ------------------------------------------------------------
    PROJECT ( COLUMN_COUNT: 6, TUPLE_SIZE: 24, COST: BLOCKED )
     SEMI-JOIN INVERSE ( METHOD: HASH, COST: BLOCKED )
      SCAN ( TABLE: SYS.T2 $$1_$$VIEW1_$T2, FULL SCAN, ACCESS: 0, COST: BLOCKED )
      HASH ( ITEM_SIZE: BLOCKED, ITEM_COUNT: 0, BUCKET_COUNT: 5243392, ACCESS: 0, COST: BLOCKED )
       LEFT-OUTER-JOIN ( METHOD: HASH, COST: BLOCKED )
        SCAN ( TABLE: SYS.T1 A, FULL SCAN, ACCESS: 0, COST: BLOCKED )
        HASH ( ITEM_SIZE: 0, ITEM_COUNT: 0, BUCKET_COUNT: 5120, ACCESS: 0, COST: BLOCKED )
         SCAN ( TABLE: SYS.T1 B, FULL SCAN, ACCESS: 0, COST: BLOCKED )
    ------------------------------------------------------------
    ```

  -   **예상 결과**

      ```sql
      ------------------------------------------------------------
      PROJECT ( COLUMN_COUNT: 6, TUPLE_SIZE: 24, COST: BLOCKED )
       VIEW ( TMP_HDD, ACCESS: 0, COST: BLOCKED )
        PROJECT ( COLUMN_COUNT: 6, TUPLE_SIZE: 24, COST: BLOCKED )
         LEFT-OUTER-JOIN ( METHOD: HASH, COST: BLOCKED )
          SCAN ( TABLE: SYS.T1 A, FULL SCAN, ACCESS: 0, COST: BLOCKED )
           ::SUB-QUERY BEGIN
           PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: BLOCKED )
            HASH ( ITEM_SIZE: 0, ITEM_COUNT: 0, BUCKET_COUNT: 1024, ACCESS: 0, COST: BLOCKED )
             VIEW ( ACCESS: 0, COST: BLOCKED )
              PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: BLOCKED )
               SCAN ( TABLE: SYS.T2, FULL SCAN, ACCESS: 0, COST: BLOCKED )
           ::SUB-QUERY END
          HASH ( ITEM_SIZE: 0, ITEM_COUNT: 0, BUCKET_COUNT: 5120, ACCESS: 0, COST: BLOCKED )
           SCAN ( TABLE: SYS.T1 B, FULL SCAN, ACCESS: 0, COST: BLOCKED )
      ------------------------------------------------------------
      ```

- **Workaround**

  ```sql
  NO_MERGE 힌트를 사용합니다.
  WITH TMP_HDD
  AS
  (SELECT /*+ NO_MERGE */ *
     FROM T1 A LEFT OUTER JOIN T1 B ON A.I2 = B.I2
    WHERE A.I1 IN (SELECT I1 FROM T2) )
  SELECT /*+ NO_PLAN_CACHE */ *
  FROM TMP_HDD ;
  ```

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48429 세션 타임아웃 조건에서도 세션이 종료되지 않는 현상 분석을 위한 디버깅 정보를 추가합니다.

-   **module** : sm-disk-index

-   **Category** : Hang

-   **재현 빈도** : Rare

-   **증상** : 세션 타임아웃 조건에서도 세션이 종료되지 않는 현상 분석을 위한 디버깅 정보를 추가합니다.
    
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
-------

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 7.1.0.5.0        | 6.5.1                   | 8.9.1        | 7.1.7               | 7.4.6                        |

> Altibase 7.1 패치 버전별 히스토리는 [Version_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.1/Altibase_7_1_Version_Histories.md)에서 확인할 수 있다.

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

Replication 프로토콜 버전은 변경되지 않았다.

### 프로퍼티

#### 추가된 프로퍼티

ILOADER_GEOM_FORMAT

#### 변경된 프로퍼티

__OPTIMIZER_UNNEST_COMPATIBILITY

### 성능 뷰

추가/변경/삭제된 성능뷰 없음

