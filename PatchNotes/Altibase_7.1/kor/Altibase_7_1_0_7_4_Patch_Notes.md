# Altibase 7.1.0.7.4 Patch Notes

<br/>

<br/>

# **Table of Contents** 

- [New Features](#new-features)
  - [BUG-49184 파티션드 테이블에 MIN, MAX 함수를 사용한 SQL 문의 수행 성능 향상을 위해 테이블 스캔 방식을 개선하였습니다.](#bug-49184%ED%8C%8C%ED%8B%B0%EC%85%98%EB%93%9C-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90-min-max-%ED%95%A8%EC%88%98%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%9C-sql-%EB%AC%B8%EC%9D%98-%EC%88%98%ED%96%89-%EC%84%B1%EB%8A%A5-%ED%96%A5%EC%83%81%EC%9D%84-%EC%9C%84%ED%95%B4-%ED%85%8C%EC%9D%B4%EB%B8%94-%EC%8A%A4%EC%BA%94-%EB%B0%A9%EC%8B%9D%EC%9D%84-%EA%B0%9C%EC%84%A0%ED%95%98%EC%98%80%EC%8A%B5%EB%8B%88%EB%8B%A4)
- [Fixed Bugs](#fixed-bugs)
  - [BUG-46674 메모리 풀링 기능을 사용하지 않는 경우(USE\_MEMORY\_POOL = 0) 정렬되지 않은 메모리 할당 문제를 개선합니다.](#bug-46674%EB%A9%94%EB%AA%A8%EB%A6%AC-%ED%92%80%EB%A7%81-%EA%B8%B0%EB%8A%A5%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%98%EC%A7%80-%EC%95%8A%EB%8A%94-%EA%B2%BD%EC%9A%B0use_memory_pool--0-%EC%A0%95%EB%A0%AC%EB%90%98%EC%A7%80-%EC%95%8A%EC%9D%80-%EB%A9%94%EB%AA%A8%EB%A6%AC-%ED%95%A0%EB%8B%B9-%EB%AC%B8%EC%A0%9C%EB%A5%BC-%EA%B0%9C%EC%84%A0%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49614 THREAD\_REUSE\_ENABLE=0 설정하고 Altibase 서버 운영 시 V\$MEMSTAT에 부정확한 메모리 통계 정보가 출력되는 현상을 개선합니다.](#bug-49614thread_reuse_enable0-%EC%84%A4%EC%A0%95%ED%95%98%EA%B3%A0-altibase-%EC%84%9C%EB%B2%84-%EC%9A%B4%EC%98%81-%EC%8B%9C-vmemstat%EC%97%90-%EB%B6%80%EC%A0%95%ED%99%95%ED%95%9C-%EB%A9%94%EB%AA%A8%EB%A6%AC-%ED%86%B5%EA%B3%84-%EC%A0%95%EB%B3%B4%EA%B0%80-%EC%B6%9C%EB%A0%A5%EB%90%98%EB%8A%94-%ED%98%84%EC%83%81%EC%9D%84-%EA%B0%9C%EC%84%A0%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49646 뷰 객체에 사용된 조인 테이블 중 한 개를 삭제하고 기본키를 갖는 파티션드 테이블로 재생성할 때 발생하는 오류를 개선합니다.](#bug-49646%EB%B7%B0-%EA%B0%9D%EC%B2%B4%EC%97%90-%EC%82%AC%EC%9A%A9%EB%90%9C-%EC%A1%B0%EC%9D%B8-%ED%85%8C%EC%9D%B4%EB%B8%94-%EC%A4%91-%ED%95%9C-%EA%B0%9C%EB%A5%BC-%EC%82%AD%EC%A0%9C%ED%95%98%EA%B3%A0-%EA%B8%B0%EB%B3%B8%ED%82%A4%EB%A5%BC-%EA%B0%96%EB%8A%94-%ED%8C%8C%ED%8B%B0%EC%85%98%EB%93%9C-%ED%85%8C%EC%9D%B4%EB%B8%94%EB%A1%9C-%EC%9E%AC%EC%83%9D%EC%84%B1%ED%95%A0-%EB%95%8C-%EB%B0%9C%EC%83%9D%ED%95%98%EB%8A%94-%EC%98%A4%EB%A5%98%EB%A5%BC-%EA%B0%9C%EC%84%A0%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49681 디스크 테이블스페이스에 접근하는 트랜잭션 처리 중 버퍼 풀(Buffer Pool) 부족으로 버퍼 교체 발생 시 동시성 문제로 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-49681%EB%94%94%EC%8A%A4%ED%81%AC-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%8A%A4%ED%8E%98%EC%9D%B4%EC%8A%A4%EC%97%90-%EC%A0%91%EA%B7%BC%ED%95%98%EB%8A%94-%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98-%EC%B2%98%EB%A6%AC-%EC%A4%91-%EB%B2%84%ED%8D%BC-%ED%92%80buffer-pool-%EB%B6%80%EC%A1%B1%EC%9C%BC%EB%A1%9C-%EB%B2%84%ED%8D%BC-%EA%B5%90%EC%B2%B4-%EB%B0%9C%EC%83%9D-%EC%8B%9C-%EB%8F%99%EC%8B%9C%EC%84%B1-%EB%AC%B8%EC%A0%9C%EB%A1%9C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
  - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
  - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)



New Features
============

### BUG-49184 파티션드 테이블에 MIN, MAX 함수를 사용한 SQL 문의 수행 성능 향상을 위해 테이블 스캔 방식을 개선하였습니다.

-   **module** : qp

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : 파티션드 테이블에 MIN, MAX 함수를 사용한 SQL 문의 수행 성능 향상을 위해 테이블 스캔 방식을 개선하였습니다.
    
    이 버그의 영향을 받는 SQL 문의 실행 계획에서 SCAN 노드의 FULL SCAN이 INDEX로 변경됩니다. 실행 계획 변경으로, 이전 버전과의 호환성을고려하여 사용자 환경에 따라 본 버그를 선택 적용할 수 있도록 프로퍼티를 제공합니다.
    
    - 이름
    
      \_\_PARTITION\_INDEXABLE\_MINMAX

    - 설명

      파티션드 테이블에 MIN, MAX 함수를 사용한 SQL 문 수행 시 인덱스 사용 여부를 선택합니다. 값 0은 인덱스를 사용하지 않으며 1은 인덱스를 사용합니다.

    - 기본값

      0 
    
    - 속성

      변경 가능, **비공개**

    위 프로퍼티는 비공개 프로퍼티로 매뉴얼에 설명을 추가하지 않습니다.

    Altibase 7.1.0.7.3 이상에서 이 버그 적용을 원하면 프로퍼티 값을 1로 변경해야 합니다. 이 프로퍼티는 Altibase 서버 구동 중 ALTER
    SYSTEM으로 변경할 수 있으며 영구적으로 적용하기를 원하면 altibase.properties 파일에 \_\_PARTITION\_INDEXABLE\_MINMAX = 1을 추가하고 Altibase 서버를 재시작해야 합니다.
    
-   **재현 방법**

    -   **재현 절차**

            DROP TABLE T2;
            CREATE TABLE T2 ( I1 INT, I2 INT , I3 INT, I4 INT) 
            PARTITION BY HASH ( I1 )
            (
              PARTITION P1,
              PARTITION P2,
              PARTITION P3 
            ) TABLESPACE SYS_TBS_DISK_DATA;
            INSERT INTO T2 VALUES ( 1, 1, 1, 1 );
            INSERT INTO T2 VALUES ( 1, 1, 1, 2 );
            INSERT INTO T2 VALUES ( 1, 1, 2, 3 );
            INSERT INTO T2 VALUES ( 1, 1, 3, 4 );
            INSERT INTO T2 VALUES ( 1, 1, 4, 1 );
            INSERT INTO T2 VALUES ( 2, 1, 1, 1 );
            INSERT INTO T2 VALUES ( 2, 1, 1, 2 );
            INSERT INTO T2 VALUES ( 2, 1, 2, 3 );
            INSERT INTO T2 VALUES ( 2, 1, 3, 4 );
            INSERT INTO T2 VALUES ( 2, 1, 4, 1 );
            DROP INDEX IDX2;
            CREATE INDEX IDX2 ON T2 ( I3 ) LOCAL;
            ALTER SESSION SET EXPLAIN PLAN = ON;
            SELECT MAX(I3) FROM T2;

    -   **수행 결과**

            iSQL> SELECT MAX(I3) FROM T2;
            MAX(I3)     
            --------------
            4           
            1 row selected.
            ------------------------------------------------------------
            PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: 369.36 )
             GROUP-AGGREGATION ( ITEM_SIZE: 24, GROUP_COUNT: 1, BUCKET_COUNT: 1, ACCESS: 1, COST: 369.36 )
              PARTITION-COORDINATOR ( TABLE: SYS.T2, PARTITION: 3/3, FULL SCAN, ACCESS: 10, COST: 356.19 )
               SCAN ( PARTITION: P3, FULL SCAN, ACCESS: 5, DISK_PAGE_COUNT: 64, COST: 118.73 )
               SCAN ( PARTITION: P2, FULL SCAN, ACCESS: 5, DISK_PAGE_COUNT: 64, COST: 118.73 )
               SCAN ( PARTITION: P1, FULL SCAN, ACCESS: 0, DISK_PAGE_COUNT: 64, COST: 118.73 )
            ------------------------------------------------------------

    -   **예상 결과**

            iSQL> SELECT MAX(I3) FROM T2;
            MAX(I3)     
            --------------
            4           
            1 row selected.
            ------------------------------------------------------------
            PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: 369.36 )
             GROUP-AGGREGATION ( ITEM_SIZE: 24, GROUP_COUNT: 1, BUCKET_COUNT: 1, ACCESS: 1, COST: 369.36 )
              PARTITION-COORDINATOR ( TABLE: SYS.T2, PARTITION: 3/3, FULL SCAN, ACCESS: 2, COST: 356.19 )
               SCAN ( PARTITION: P3, INDEX: SYS.IDX2, RANGE SCAN DESC, ACCESS: 1, DISK_PAGE_COUNT: 64, COST: 118.73 )
               SCAN ( PARTITION: P2, INDEX: SYS.IDX2, RANGE SCAN DESC, ACCESS: 1, DISK_PAGE_COUNT: 64, COST: 118.73 )
               SCAN ( PARTITION: P1, INDEX: SYS.IDX2, RANGE SCAN DESC, ACCESS: 0, DISK_PAGE_COUNT: 64, COST: 118.73 )
            ------------------------------------------------------------

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

Fixed Bugs
==========

### BUG-46674 메모리 풀링 기능을 사용하지 않는 경우(USE\_MEMORY\_POOL = 0) 정렬되지 않은 메모리 할당 문제를 개선합니다.

-   **module** : id

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : Altibase 서버 프로퍼티 USE\_MEMORY\_POOL을 0으로 설정하여 메모리 풀링 기능을 사용하지 않을 때, 정렬된 주솟값이 요구되는 메모리 할당 시 정렬되지 않은 주솟값이 할당되어 Altibase 서버가 비정상 종료하는 현상을 수정합니다.
    
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

### BUG-49614 THREAD\_REUSE\_ENABLE=0 설정하고 Altibase 서버 운영 시 V\$MEMSTAT에 부정확한 메모리 통계 정보가 출력되는 현상을 개선합니다.

-   **module** : id

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : Altibase 서버 프로퍼트 THREAD\_REUSE\_ENABLE=0 설정하여 쓰레드 재사용 기능을 사용하지 않을 때 V\$MEMSTAT의 ALLOC\_SIZE에 부정확한 메모리 통계 정보가 출력되는 현상을 개선합니다.
    
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

### BUG-49646 뷰 객체에 사용된 조인 테이블 중 한 개를 삭제하고 기본키를 갖는 파티션드 테이블로 재생성할 때 발생하는 오류를 개선합니다.

-   **module** : qp-ddl-dcl-pvo

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : 뷰 객체에 사용된 조인 테이블 중 한 개를 삭제하고 기본키를 갖는 파티션드 테이블로 재생성할 때 Altibase 서버가 비정상 종료하는 현상을 수정합니다.        
    
    이 버그는 아래의 절차로 수행 시 발생합니다.
    
    1. 뷰 객체 생성 시 조인과 USE\_INDEX\_NL 힌트 사용 
    2. 뷰에서 접근하는 베이스 테이블 삭제
    3. 삭제한 베이스 테이블과 같은 이름으로 기본키 또는 유일키를 갖는 파티션드 테이블 생성

-   **재현 방법**

    -   **재현 절차**

            DROP TABLE T1;
            DROP VIEW  V1;
            CREATE TABLE T1 ( I1 INTEGER );
            CREATE TABLE T2 ( I1 INTEGER );
            CREATE VIEW V1 AS
            SELECT /*+ USE_INDEX_NL(T1, T2) */ T1.I1 I1
                 , T2.I1 I2
              FROM T1 T1
                 , T1 T2
             WHERE T1.I1 = T2.I1;
            DROP TABLE T1;
            CREATE TABLE T1
            (
              I1 INTEGER PRIMARY KEY
            )
            PARTITION BY RANGE( I1 )
            (
              PARTITION P1 VALUES LESS THAN ( 100 ),
              PARTITION P2 VALUES DEFAULT
            );

    -   **수행 결과**

            Altibase 서버 비정상 종료

    -   **예상 결과**

            Create success.

-   **Workaround**

        USE_INDEX_NL 제거

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49681 디스크 테이블스페이스에 접근하는 트랜잭션 처리 중 버퍼 풀(Buffer Pool) 부족으로 버퍼 교체 발생 시 동시성 문제로 Altibase 서버가 비정상 종료할 수 있습니다.

-   **module** : sm-disk-page

-   **Category** : Assert

-   **재현 빈도** : Rare

-   **설명** :

    디스크 테이블스페이스에 접근하는 트랜잭션 처리 중 버퍼 풀(Buffer Pool) 부족으로 버퍼 교체 발생 시 동시성 문제로 Altibase 서버가 비정상 종료하는 현상을 수정합니다.

    이 버그로 Altibase 서버가 비정상 종료하는 경우 altibase\_error.log에 아래와 같은 형태의 로그를 출력합니다.

    ```
    BCB Info..
    mID 7922
    mState 2
    mFrame 7fc8d69a4000
    mSpaceID 6
    ...중략...
    
    IDE_ASSERT( 0 ), [sdbBufferPool.cpp:852], errno=[16]
    errno=[16]
    
    [ASSERT] ERROR LINE => [sdbBufferPool.cpp:852]
    ERR-0109e(errno=16) Internal server error.
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

Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    7.1.0.7.4     |          6.5.1          |    8.10.1    |        7.1.7        |            7.4.7             |

> Altibase 7.1 패치 버전별 히스토리는 [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7_1_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

> 패치를 롤백하려는 경우, [메타다운그레이드](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Installation.md#%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9Cmeta-downgrade)를 참고한다.

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
