# Altibase 7.1.0.6.5 Patch Notes

<br/>

<br/>

# **Table of Contents**  

- [Altibase 7.1.0.6.5 Patch Notes](#altibase-71065-patch-notes)
  - [New Features](#new-features)
    - [BUG-49330 집합 연산자를 포함한 WITH 절 또는 VIEW 의 실행 계획을 개선합니다.](#bug-49330%EC%A7%91%ED%95%A9-%EC%97%B0%EC%82%B0%EC%9E%90%EB%A5%BC-%ED%8F%AC%ED%95%A8%ED%95%9C-with-%EC%A0%88-%EB%98%90%EB%8A%94-view-%EC%9D%98-%EC%8B%A4%ED%96%89-%EA%B3%84%ED%9A%8D%EC%9D%84-%EA%B0%9C%EC%84%A0%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-49398 DDL 복제 실행 시 테이블 잠금 획득 실패 또는 교착 상태(deadlock)를 사유로 일시적으로 DDL 수행이 실패하는 경우 재시도하는 기능을 추가합니다.](#bug-49398ddl-%EB%B3%B5%EC%A0%9C-%EC%8B%A4%ED%96%89-%EC%8B%9C-%ED%85%8C%EC%9D%B4%EB%B8%94-%EC%9E%A0%EA%B8%88-%ED%9A%8D%EB%93%9D-%EC%8B%A4%ED%8C%A8-%EB%98%90%EB%8A%94-%EA%B5%90%EC%B0%A9-%EC%83%81%ED%83%9Cdeadlock%EB%A5%BC-%EC%82%AC%EC%9C%A0%EB%A1%9C-%EC%9D%BC%EC%8B%9C%EC%A0%81%EC%9C%BC%EB%A1%9C-ddl-%EC%88%98%ED%96%89%EC%9D%B4-%EC%8B%A4%ED%8C%A8%ED%95%98%EB%8A%94-%EA%B2%BD%EC%9A%B0-%EC%9E%AC%EC%8B%9C%EB%8F%84%ED%95%98%EB%8A%94-%EA%B8%B0%EB%8A%A5%EC%9D%84-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-48756 AUTOCOMMIT OFF 모드에서 메타 테이블을 조회하는 SQL 문 수행 후 일반 테이블을 접근하는 SQL 문 수행 시 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-48756autocommit-off-%EB%AA%A8%EB%93%9C%EC%97%90%EC%84%9C-%EB%A9%94%ED%83%80-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%9D%84-%EC%A1%B0%ED%9A%8C%ED%95%98%EB%8A%94-sql-%EB%AC%B8-%EC%88%98%ED%96%89-%ED%9B%84-%EC%9D%BC%EB%B0%98-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%9D%84-%EC%A0%91%EA%B7%BC%ED%95%98%EB%8A%94-sql-%EB%AC%B8-%EC%88%98%ED%96%89-%EC%8B%9C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-49141 이중화 객체 관련한 DDL문 유효성 검사에서 사용하는 메모리 관리자를 올바르게 변경합니다.](#bug-49141%EC%9D%B4%EC%A4%91%ED%99%94-%EA%B0%9D%EC%B2%B4-%EA%B4%80%EB%A0%A8%ED%95%9C-ddl%EB%AC%B8-%EC%9C%A0%ED%9A%A8%EC%84%B1-%EA%B2%80%EC%82%AC%EC%97%90%EC%84%9C-%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94-%EB%A9%94%EB%AA%A8%EB%A6%AC-%EA%B4%80%EB%A6%AC%EC%9E%90%EB%A5%BC-%EC%98%AC%EB%B0%94%EB%A5%B4%EA%B2%8C-%EB%B3%80%EA%B2%BD%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-49418 날짜시간 함수 DATEDIFF 동작을 매뉴얼 설명에 맞춰 date_field_name가 SECOND 일 때 결과가 2144448000초를 초과하는 경우 에러가 발생하도록 변경합니다.](#bug-49418-날짜시간-함수-datediff-동작을-매뉴얼-설명에-맞춰-date_field_name가-second-일-때-결과가-2144448000초를-초과하는-경우-에러가-발생하도록-변경합니다)
    - [BUG-49424 지역 서버와 원격 서버 간 이중화 대상 테이블의 컬럼 수가 다른 경우 원격 서버에서 복제 트랜잭션 수행 시 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-49424%EC%A7%80%EC%97%AD-%EC%84%9C%EB%B2%84%EC%99%80-%EC%9B%90%EA%B2%A9-%EC%84%9C%EB%B2%84-%EA%B0%84-%EC%9D%B4%EC%A4%91%ED%99%94-%EB%8C%80%EC%83%81-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%9D%98-%EC%BB%AC%EB%9F%BC-%EC%88%98%EA%B0%80-%EB%8B%A4%EB%A5%B8-%EA%B2%BD%EC%9A%B0-%EC%9B%90%EA%B2%A9-%EC%84%9C%EB%B2%84%EC%97%90%EC%84%9C-%EB%B3%B5%EC%A0%9C-%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98-%EC%88%98%ED%96%89-%EC%8B%9C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->



New Features
============

### BUG-49330 집합 연산자를 포함한 WITH 절 또는 VIEW 의 실행 계획을 개선합니다.

-   **module** : qp-select

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : WITH 절 또는 VIEW 에서 집합 연산자 사용 시 불필요한 실행 노드를 제거하여 실행 계획을 개선하였습니다. 불필요한 PROJECT 노드와 VIEW 노드를 생성하지 않습니다. 집합 연산자 중 UNION 을 제외한 UNION ALL, INTERSECT, MINUS 3가지만 해당합니다.  LIMIT, LOOP 절이 사용된 경우 이 버그가 적용되지 않을 수 있습니다. 
    
    이 버그는 Altibase 7.1 이상에 반영합니다. 히든 프로퍼티 \_\_OPTIMIZER\_SET 으로 이 기능 사용을 제어할 수 있으며 Altibase 버전에 따라 기본값이 다릅니다.

    _\_OPTIMIZER\_SET 히든 프로퍼티가 추가되었습니다.
    
    - 설명
    
      WITH 절 또는 VIEW 에서 집합 연산자 사용 시 개선한 실행 계획 적용 여부를 설정합니다.
    
      1 : 적용
    
      0 : 미적용
    
    - 기본값
    
      0
    
    - 속성

      비공개

- **재현 방법**

  - **재현 절차**

    ```sql
    DROP TABLE T1;
    CREATE TABLE T1 ( I1 INTEGER , I2 INTEGER, I3 INTEGER );
    INSERT INTO T1 VALUES ( 1, 11, 21);
    INSERT INTO T1 VALUES ( 2, 12, 22);
    INSERT INTO T1 VALUES ( 3, 13, 33);
    ALTER SESSION SET EXPLAIN PLAN = ON;
    WITH W1 AS 
    (
      SELECT I1 FROM T1
      UNION ALL
      SELECT I2 FROM T1
      UNION ALL
      SELECT I3 FROM T1 
    )
    SELECT * FROM W1;
    ```

  - **수행 결과**

    ```sql
    iSQL> WITH W1 AS 
        2 (
        3   SELECT I1 FROM T1
        4   UNION ALL
        5   SELECT I2 FROM T1
        6   UNION ALL
        7   SELECT I3 FROM T1 
        8 )
        9 SELECT * FROM W1;
    I1          
    --------------
    1           
    2           
    3           
    11          
    12          
    13          
    21          
    22          
    33          
    9 rows selected.
    ------------------------------------------------------------
    PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: 712.44 )
     VIEW ( W1, ACCESS: 9, COST: 708.49 )
      PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: 358.20 )
       VIEW ( ACCESS: 9, COST: 354.24 )
        BAG-UNION
         PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: 118.08 )
          SCAN ( TABLE: SYS.T1, FULL SCAN, ACCESS: 3, COST: 116.76 )
         PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: 118.08 )
          SCAN ( TABLE: SYS.T1, FULL SCAN, ACCESS: 3, COST: 116.76 )
         PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: 118.08 )
          SCAN ( TABLE: SYS.T1, FULL SCAN, ACCESS: 3, COST: 116.76 )
    ------------------------------------------------------------
    ```

  -   **예상 결과**

      ```sql
      iSQL> WITH W1 AS 
          2 (
          3   SELECT I1 FROM T1
          4   UNION ALL
          5   SELECT I2 FROM T1
          6   UNION ALL
          7   SELECT I3 FROM T1 
          8 )
          9 SELECT * FROM W1;
      W1.I1
      --------------
      1
      2
      3
      11
      12
      13
      21
      22
      33
      9 rows selected.
      ------------------------------------------------------------
      PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: BLOCKED )
       VIEW ( W1, ACCESS: 9, COST: BLOCKED )
          BAG-UNION
           PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: BLOCKED )
            SCAN ( TABLE: SYS.T1, FULL SCAN, ACCESS: 3, COST: BLOCKED )
           PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: BLOCKED )
            SCAN ( TABLE: SYS.T1, FULL SCAN, ACCESS: 3, COST: BLOCKED )
           PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: BLOCKED )
            SCAN ( TABLE: SYS.T1, FULL SCAN, ACCESS: 3, COST: BLOCKED )
      ------------------------------------------------------------
      ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49398 DDL 복제 실행 시 테이블 잠금 획득 실패 또는 교착 상태(deadlock)를 사유로 일시적으로 DDL 수행이 실패하는 경우 재시도하는 기능을 추가합니다.

-   **module** : rp

-   **Category** : Other

-   **재현 빈도** : Always

-   **설명** : DDL 복제 실행 시 테이블 잠금 획득 실패 또는 교착 상태(deadlock)를 사유로 일시적으로 DDL 수행이 실패하는 경우, 재시도하는 기능을 추가합니다. 일시적인 DDL 실패 상황 발생 시 REPLICATION\_DDL\_SYNC\_TIMEOUT 프로퍼티 시간 동안 DDL 복제 실행을 재시도합니다.
    
    이 기능 추가로 이중화 프로토콜 버전의 패치 버전이 7.4.6 에서 7.4.7 로 변경되었습니다. 따라서, DDL 복제 기능 사용하는 경우 이중화 프로토콜 버전 세 자리가 모두 일치해야하므로 이 버그는 모든 이중화 대상 서버에 모두 적용해야 합니다.
    
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

### BUG-48756 AUTOCOMMIT OFF 모드에서 메타 테이블을 조회하는 SQL 문 수행 후 일반 테이블을 접근하는 SQL 문 수행 시 Altibase 서버가 비정상 종료할 수 있습니다.

-   **module** : qp

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : AUTOCOMMIT OFF 모드에서 메타 테이블을 조회하는 SQL 문 수행 후 일반 테이블을 접근하는 SQL 문 수행 시 Altibase 서버가 비정상 종료합니다. 트랜잭션 재사용 과정에서 발생하는 문제를 수정하였습니다.
    
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

### BUG-49141 이중화 객체 관련한 DDL문 유효성 검사에서 사용하는 메모리 관리자를 올바르게 변경합니다.

-   **module** : rp
-   **Category** : Memory Error
-   **재현 빈도** : Always
-   **설명** : 이중화 객체 관련한 DDL문 유효성 검사에서 사용하는 메모리 관리자를 올바르게 변경합니다. 아래의 DDL문 수행 시 메모리 사용량 표시가 V\$MEMSTAT의 Query\_Execute에서 Query\_Prepare로 변경됩니다.
    - CREATE REPLICATION 
    - ALTER REPLICATION *replication\_name* ADD TABLE
    - ALTER REPLICATION *replication\_name* DROP TABLE
    - ALTER REPLICATION *replication\_name* SYNC
    - DROP REPLICATION
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

### BUG-49418 날짜시간 함수 DATEDIFF 동작을 매뉴얼 설명에 맞춰 date_field_name가 SECOND 일 때 결과가 2144448000초를 초과하는 경우 에러가 발생하도록 변경합니다.

-   **module** : qp

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : DATEDIFF함수의 세 번째 인자 *date_field_name*가 SECOND 인 경우, enddate와 startdate의 차가 평년(365일)을 기준으로 68년인 2144448000초를 초과하면 에러가 발생하도록 변경되었습니다. 

    > 참고 : [Altibase 7.1 SQL Reference - DATEDIFF](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/SQL%20Reference.md#datediff)

-   **재현 방법**

    -   **재현 절차**

        ```sql
        SELECT DATEDIFF('27-SEP-2005', '30-DEC-2074', 'SECOND') FROM DUAL;
        ```

    -   **수행 결과**

        ```sql
        DATEDIFF('27-SEP-2005','30-DEC-2074','SECO 
        ---------------------------------------------
        2185574400           
        1 row selected.
        ```

    -   **예상 결과**

        ```sql
        [ERR-2102D : The interval between startdate and enddate exceeded 68 years. 
        0001 : SELECT DATEDIFF('27-SEP-2005', '30-DEC-2074', 'SECOND') FROM DUAL
                     ^                                               ^
        ]
        ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49424 지역 서버와 원격 서버 간 이중화 대상 테이블의 컬럼 수가 다른 경우 원격 서버에서 복제 트랜잭션 수행 시 Altibase 서버가 비정상 종료할 수 있습니다.

-   **module** : rp

-   **Category** : Fatal

-   **재현 빈도** : Rare

-   **설명** : 지역 서버와 원격 서버 간 이중화 대상 테이블의 컬럼 수가 다른 경우 원격 서버에서 복제 트랜잭션 수행 시 Altibase 서버가 비정상 종료할 수 있습니다. 수신자(Receiver)의 컬럼 분석 오류를 수정하였습니다.
    
    이 버그는 "BUG-47458 SQL Apply에서 Lob을 지원 하지 않습니다. Lob을 지원하도록 수정해야 합니다." 를 반영한 버전에서 발생합니다. Altibase 버전 별 본 버그 노출 패치 버전은 아래와 같습니다. 
    
    - Altibase 7.1.0.3.1 \~ 7.1.0.6.4
    
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
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    7.1.0.6.5     |          6.5.1          |    8.10.1    |        7.1.7        |         ***7.4.7***          |

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