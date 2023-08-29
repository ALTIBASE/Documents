# Altibase 6.5.1.9.9 Patch Notes

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Fixed Bugs](#fixed-bugs)
    - [BUG-50427 RANGE PARTITION 에 대한 ORDER BY 에 대해 Preserved Order 지원](#bug-50427)
    - [BUG-50451 같은 query set내에 order by에 사용된 alias 가 target 절의 row_number 함수의 alias로 사용된 경우 서버가 비정상 종료 합니다.](#bug-50451)
    - [BUG-50533 Altibase 6.1.1 클라이언트로 Altibase 6.5.1 서버에 접속을 시도할 때, 연결 실패에 대한 audit 정보가 잘못 기록되는 문제를 수정합니다.](#bug-50533)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Fixed Bugs
==========

### BUG-50427 RANGE PARTITION 에 대한 ORDER BY 에 대해 Preserved Order 지원<b id="bug-50427"> </b>

-   **module** : qp

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : 범위 파티션 테이블에 로컬 인덱스가 존재하는 경우, Preserved Order를 지원하여 ORDER BY, GROUP BY, JOIN 에서 이를 활용할 수 있도록 기능을 제공합니다. 이 기능은 히든 프로퍼티 RANGE_PARTITION_USABLE_LOCAL_INDEX를 1로 설정하는 경우에 사용할 수 있습니다.

    이 기능을 설정하면 아래의 조건에 해당하는 파티션 테이블의 경우 실행계획이 변경됩니다.

    * 범위 파티션 테이블에서 WHERE 절의 조건이 파티션 키와 동일하고, ORDER BY(또는 GROUP BY)에 해당 컬럼이 사용된 경우

    단, 파티션키가 1개일 때만 사용가능하며 PARALLER QUERY 및 MERGE JOIN에서는 동작하지 않습니다.

- **재현 방법**

  - **재현 절차**

    ```sql
    DROP TABLE T1;
    CREATE TABLE T1 ( I1 INT, I2 INT, I3 INT )
    PARTITION BY RANGE ( I1 )
        (
         PARTITION P1 VALUES LESS THAN (10)
         , PARTITION P2 VALUES LESS THAN (20)
         , PARTITION P3 VALUES LESS THAN (30)
         , PARTITION P4 VALUES LESS THAN (40)
         , PARTITION P_MAX VALUES DEFAULT
        );

    INSERT INTO T1 SELECT LEVEL, LEVEL, LEVEL FROM DUAL CONNECT BY LEVEL < 50;

    DROP INDEX IDX1;
    CREATE UNIQUE INDEX IDX1 ON T1 ( I1 ) LOCAL;

     SELECT * FROM T1 WHERE I1 > 20 ORDER BY I1 DESC;
    ```

  - **수행 결과**

    ```sql
    PROJECT ( COLUMN_COUNT: 3, TUPLE_SIZE: 12, COST: 0.04 )
     SORT ( ITEM_SIZE: ??, ITEM_COUNT: ??, ACCESS: ??, COST: 0.04 )
      PARTITION-COORDINATOR ( TABLE: SYS.T1, PARTITION: 3/5, ACCESS: ??, COST: 0.03 )
       SCAN ( PARTITION: P_MAX, INDEX: SYS.IDX1, RANGE SCAN, ACCESS: ??, COST: 0.01 )
       SCAN ( PARTITION: P4, INDEX: SYS.IDX1, RANGE SCAN, ACCESS: ??, COST: 0.01 )
       SCAN ( PARTITION: P3, INDEX: SYS.IDX1, RANGE SCAN, ACCESS: ??, COST: 0.01 )
    ```

  -   **예상 결과**

      ```sql
      PROJECT ( COLUMN_COUNT: 3, TUPLE_SIZE: 12, COST: 0.04 )
        PARTITION-COORDINATOR ( TABLE: SYS.T1, PARTITION: 3/5, ACCESS: ??, COST: 0.03 )
         SCAN ( PARTITION: P_MAX, INDEX: SYS.IDX1, RANGE SCAN, ACCESS: ??, COST: 0.01 )
         SCAN ( PARTITION: P4, INDEX: SYS.IDX1, RANGE SCAN, ACCESS: ??, COST: 0.01 )
         SCAN ( PARTITION: P3, INDEX: SYS.IDX1, RANGE SCAN, ACCESS: ??, COST: 0.01 )
      ```

- **Workaround**

- **변경사항**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

### BUG-50451 같은 query set내에 order by에 사용된 alias 가 target 절의 row_number 함수의 alias로 사용된 경우 서버가 비정상 종료 합니다.<b id="bug-50451"> </b>

-   

-   **module** : qp

-   **Category** : Fatal

-   **재현 빈도** : Always

- **설명** : 아래 조건을 모두 만족하는 질의문 수행 시, 비정상 종료하는 문제를 수정하였습니다.

  - over 절의 partition by 나 order by에 사용된 컬럼을 group by에 사용한 경우
  - over 절의 partition by 나 order by에 사용된 컬럼을 target 절의 함수의 인자로 사용한 경우
  - target 절의 함수의 인자로 사용한 컬럼을 해당함수의 alias로 지정한 경우 (target 절의 함수의 인자와 alias가 동일한 경우)
  - target 절의 함수의 alias를 order by에 사용한 경우

-   **재현 방법**

    -   **재현 절차**

        ```sql
        DROP TABLE T1;
        CREATE TABLE T1 ( I1 VARCHAR(30),I2 VARCHAR(30), I3 VARCHAR(30) );
        CREATE FUNCTION FUNC1( V1 INTEGER )
           RETURN INTEGER
           AS
           BEGIN
             RETURN V1;
           END;
           /

        SELECT ROW_NUMBER() OVER(PARTITION BY I1 ORDER BY I2 ASC) AS AA
                    ,FUNC1(I1) AS I1
                    ,FUNC1(I2) AS I2
                    FROM T1
                    GROUP BY I1, I2
                    ORDER BY AA;
        ```

    -   **수행 결과**

        ```sql
        [ERR-31455 : Failed to work because an internal exception occurred from an OS.[Contact Altibase's Support Center]]
        ```

    -   **예상 결과**

        ```sql
        No rows selected.
        ```

- **Workaround**

  target 절의 함수의 인자와 alias가 같은 경우를 해소하면(아래와 같이 alias를 다르게 변경하면), 비정상 종료 하지 않습니다.

  ```sql
  SELECT ROW_NUMBER() OVER(PARTITION BY I1 ORDER BY I2 ASC) AS AA
              ,FUNC1(I1) AS I1a
              ,FUNC1(I2) AS I2b
              FROM T1
              GROUP BY I1, I2
              ORDER BY AA;
  ```

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50533 Altibase 6.1.1 클라이언트로 Altibase 6.5.1 서버에 접속을 시도할 때, 연결 실패에 대한 audit 정보가 잘못 기록되는 문제를 수정합니다.<b id="bug-50533"> </b>

-   **module** : mm-altiaudit

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : Altibase 6.1.1 클라이언트로 Altibase 6.5.1 서버에 접속을 시도할 때, 연결 실패에 대해서 CONNECT가 기록되어야 하는데 DISCONNECT로 기록되는 문제 수정합니다.

- **재현 방법**

  - **재현 절차**

    - 1. Altibase 6.5.1 서버의 isql에서 아래의 명령어 수행

         ```
         audit connect, disconnect;
         ALTER SYSTEM START AUDIT;
         ```

    - 2. Altibase 6.1.1 클라이언트에서 1의 6.5.1 서버로 접속을 시도 (잘못된 비밀번호로 접속을 시도한다)

    - 3. Altibase 6.5.1 서버의 isql에서 아래의 명령어 수행 후 $ALTIBASE_HOME/trc/ 에서 audit 로그 확인

         ```
         ALTER SYSTEM STOP AUDIT;
         ```

  - **수행 결과**

  - **예상 결과**

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
| 6.5.1.9.9        | 6.3.1                   | 8.1.1        | 7.1.3               | 7.4.5                        |

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

#### 추가된 프로퍼티

#### 변경된 프로퍼티

#### 삭제된 프로퍼티

### 성능 뷰

#### 추가된 성능 뷰

#### 변경된 성능 뷰

#### 삭제된 성능 뷰
