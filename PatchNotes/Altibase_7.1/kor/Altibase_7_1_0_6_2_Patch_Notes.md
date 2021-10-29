<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  

- [Altibase 7.1.0.6.2 Patch Notes](#altibase-71062-patch-notes)
  - [New Features](#new-features)
    - [BUG-49332 이중화 중 네트워크 패킷 변조로 xLog가 수정되었을 때 Altibase 서버 비정상 종료 발생 가능성을 방어합니다.](#bug-49332%EC%9D%B4%EC%A4%91%ED%99%94-%EC%A4%91-%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC-%ED%8C%A8%ED%82%B7-%EB%B3%80%EC%A1%B0%EB%A1%9C-xlog%EA%B0%80-%EC%88%98%EC%A0%95%EB%90%98%EC%97%88%EC%9D%84-%EB%95%8C-altibase-%EC%84%9C%EB%B2%84-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C-%EB%B0%9C%EC%83%9D-%EA%B0%80%EB%8A%A5%EC%84%B1%EC%9D%84-%EB%B0%A9%EC%96%B4%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-49266 트랜잭션 처리 함수에 존재하는 메모리 초기화 오류를 수정합니다.](#bug-49266%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98-%EC%B2%98%EB%A6%AC-%ED%95%A8%EC%88%98%EC%97%90-%EC%A1%B4%EC%9E%AC%ED%95%98%EB%8A%94-%EB%A9%94%EB%AA%A8%EB%A6%AC-%EC%B4%88%EA%B8%B0%ED%99%94-%EC%98%A4%EB%A5%98%EB%A5%BC-%EC%88%98%EC%A0%95%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-49273 뷰 머징(View Merging)이 발생한 뷰가 집합 연산자와 사용된 경우 결과값 오류가 발생할 수 있습니다.](#bug-49273%EB%B7%B0-%EB%A8%B8%EC%A7%95view-merging%EC%9D%B4-%EB%B0%9C%EC%83%9D%ED%95%9C-%EB%B7%B0%EA%B0%80-%EC%A7%91%ED%95%A9-%EC%97%B0%EC%82%B0%EC%9E%90%EC%99%80-%EC%82%AC%EC%9A%A9%EB%90%9C-%EA%B2%BD%EC%9A%B0-%EA%B2%B0%EA%B3%BC%EA%B0%92-%EC%98%A4%EB%A5%98%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-49287 원격 서버의 트랜잭션 세그먼트가 모두 사용 중인 상태에서 이중화 Receiver가 디스크 테이블에 변경 트랜잭션 반영 시 무한 대기하는 현상이 발생합니다.](#bug-49287%EC%9B%90%EA%B2%A9-%EC%84%9C%EB%B2%84%EC%9D%98-%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98-%EC%84%B8%EA%B7%B8%EB%A8%BC%ED%8A%B8%EA%B0%80-%EB%AA%A8%EB%91%90-%EC%82%AC%EC%9A%A9-%EC%A4%91%EC%9D%B8-%EC%83%81%ED%83%9C%EC%97%90%EC%84%9C-%EC%9D%B4%EC%A4%91%ED%99%94-receiver%EA%B0%80-%EB%94%94%EC%8A%A4%ED%81%AC-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90-%EB%B3%80%EA%B2%BD-%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98-%EB%B0%98%EC%98%81-%EC%8B%9C-%EB%AC%B4%ED%95%9C-%EB%8C%80%EA%B8%B0%ED%95%98%EB%8A%94-%ED%98%84%EC%83%81%EC%9D%B4-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-49320 ALTER INDEX \~ REORGANIZE 수행 중 인덱스 노드가 분할(SPLIT)된 경우 인덱스 구조가 손상되어 결과 오류가 발생할 수 있습니다.](#bug-49320alter-index--reorganize-%EC%88%98%ED%96%89-%EC%A4%91-%EC%9D%B8%EB%8D%B1%EC%8A%A4-%EB%85%B8%EB%93%9C%EA%B0%80-%EB%B6%84%ED%95%A0split%EB%90%9C-%EA%B2%BD%EC%9A%B0-%EC%9D%B8%EB%8D%B1%EC%8A%A4-%EA%B5%AC%EC%A1%B0%EA%B0%80-%EC%86%90%EC%83%81%EB%90%98%EC%96%B4-%EA%B2%B0%EA%B3%BC-%EC%98%A4%EB%A5%98%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-49322 COUNT(column\_name) KEEP 사용 시 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-49322countcolumn_name-keep-%EC%82%AC%EC%9A%A9-%EC%8B%9C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-49334 C/C++ External Procedures에서 메모리 참조 오류 발생 시 예외 처리 부족으로 Altibase 서버가 비정상 종료합니다.](#bug-49334cc-external-procedures%EC%97%90%EC%84%9C-%EB%A9%94%EB%AA%A8%EB%A6%AC-%EC%B0%B8%EC%A1%B0-%EC%98%A4%EB%A5%98-%EB%B0%9C%EC%83%9D-%EC%8B%9C-%EC%98%88%EC%99%B8-%EC%B2%98%EB%A6%AC-%EB%B6%80%EC%A1%B1%EC%9C%BC%EB%A1%9C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->



Altibase 7.1.0.6.2 Patch Notes
==============================

New Features
------------

### BUG-49332 이중화 중 네트워크 패킷 변조로 xLog가 수정되었을 때 Altibase 서버 비정상 종료 발생 가능성을 방어합니다.

-   **module** : rp-receiver

-   **Category** : Functional Error

-   **재현 빈도** : Unknown

-   **설명** : 이중화 중 네트워크 패킷 변조로 xLog가 수정되었을 때 altibase\_rp.log에 다음의 에러를 남기며 Altibase 서버가 비정상 종료하는 현상을 방어합니다. 
    
    ```bash
    [2021/09/28 18:08:58 F5FD][PID:187816][Thread-140133571839744][LWP-189001]
    transaction abort error [TID : 61783414]
    [2021/09/28 18:08:58 F5FE][PID:187816][Thread-140133571839744][LWP-189001]
    ERR-1104d(errno=62) An update statement already exists.
    ```

    이 현상은 네트워크 중간에 누군가 xlog를 조작하였을때만 발생하며, 일반적인 상황에서는 발생하지 않습니다. 이 버그를 반영하면 이중화 Receiver는 다음과 같은 에러를 남기며 종료한 후 이중화 Sender에 의해 재시작되어 다시 이중화를 시작합니다.
    
    ```bash
    [2021/10/01 19:51:32 59F][PID:30274][Thread-1417512704][LWP-30388]
    ERR-61069(errno=62) Internal server error in replication module
    ([rpsSmExecutor::convertValueToOID] Column not found [CID: 0] at [Remote SN: 8590708662, TID: 49988, TABLEID: 4461760]).
    [2021/10/01 19:51:32 5A0][PID:30274][Thread-1417512704][LWP-30388]
    UPDATE SYS.T1 SET I1 = '100' WHERE PK = 1; (TID : 49988)
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

Fixed Bugs
----------

### BUG-49266 트랜잭션 처리 함수에 존재하는 메모리 초기화 오류를 수정합니다.

-   **module** : sm

-   **Category** : Memory Error

-   **재현 빈도** : Always

-   **설명** : 트랜잭션 처리 함수에 존재하는 메모리 초기화 오류를 수정하여 Altibase 서버 비정상 종료 유발 가능성을 제거합니다.

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

### BUG-49273 뷰 머징(View Merging)이 발생한 뷰가 집합 연산자와 사용된 경우 결과값 오류가 발생할 수 있습니다.

-   **module** : qp-dml-pvo

-   **Category** : Functional Error

-   **재현 빈도** : Rare

-   **설명** : 뷰 머징(View Merging)이 발생한 뷰가 집합 연산자와 사용된 경우 결과값 오류가 발생하는 문제를 수정합니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    DROP TABLE T1;
    CREATE TABLE T1 ( C1 INT, C2 INT, C3 INT);
    
    INSERT INTO T1 VALUES( 1, 2, 3);
    INSERT INTO T1 VALUES( 2, 3, 4);
    
    WITH WITH_1 
    AS 
    (SELECT C1, C2
       FROM (SELECT /*+ no_merge */ A.C1, A.C2
               FROM T1 A) C 
    )
    SELECT c1
      FROM (SELECT NULL, C1
              FROM WITH_1
             UNION ALL
            SELECT NULL, C1
              FROM WITH_1 ) v1 
    ;
    ```

  - **수행 결과**

    ```sql
    C1
    --------------
    
    
    
    
    4 rows selected.
    ```

  -   **예상 결과**

      ```sql
      C1
      --------------
      1
      2
      1
      2
      4 rows selected.
      ```

- **Workaround**

  ```sql
  /*+ NO_MERGE(WITH_1) */
  ```

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49287 원격 서버의 트랜잭션 세그먼트가 모두 사용 중인 상태에서 이중화 Receiver가 디스크 테이블에 변경 트랜잭션 반영 시 무한 대기하는 현상이 발생합니다.

-   **module** : rp-receiver

-   **Category** : Hang

-   **재현 빈도** : Always

-   **설명** : 원격 서버의 트랜잭션 세그먼트가 모두 사용 중인 상태에서 이중화 Receiver가 디스크 테이블에 변경 트랜잭션 반영 시 무한 대기하는 현상을 수정합니다. 원격 서버의 트랜잭션 세그먼트가 모두 사용 중인 경우, \$ALTIBASE\_HOME/trc/altibase\_boot.log 에 아래와 같은 에러 메시지가 발생합니다.
    
    TRANSACTION\_SEGMENT\_COUNT is full !!

    Transaction (TID:169992) is waiting for TXSegs allocation.
    
    위 현상 발생 시 이중화 Receiver가 약 10초 대기 후 해당 작업을 취소하고 이중화 Receiver를 종료하도록 수정하였습니다.

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

### BUG-49320 ALTER INDEX \~ REORGANIZE 수행 중 인덱스 노드가 분할(SPLIT)된 경우 인덱스 구조가 손상되어 결과 오류가 발생할 수 있습니다.

-   **module** : sm-mem-index

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : ALTER INDEX \~ REORGANIZE 수행 중 인덱스 노드가 분할(SPLIT)된 경우 인덱스 구조가 손상되는 오류를 수정하였습니다.
    
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

### BUG-49322 COUNT(column\_name) KEEP 사용 시 Altibase 서버가 비정상 종료할 수 있습니다.

-   **module** : mt-function

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : COUNT(*column\_name*) KEEP 사용 시 Altibase 서버가 비정상 종료하는 현상을 수정합니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    DROP TABLE t1; 
    CREATE TABLE T1 ( I1 INTEGER PRIMARY KEY, I2 INTEGER );
    INSERT INTO T1 VALUES ( 5, 5 );
    INSERT INTO T1 VALUES( 3, 3 );
    SELECT COUNT(I1) KEEP ( DENSE_RANK LAST ORDER BY I2 DESC ) FROM T1;
    ```

  -   **수행 결과**

          Altibase 서버 비정상 종료

  -   **예상 결과**

      ```sql
      COUNT(I1)KEEP(DENSE_RANKLASTORDERBYI2DESC) 
      ---------------------------------------------
      1                    
      1 row selected.
      ```

-   **Workaround**

        OPTIMIZER_COUNT_COLUMN_TO_COUNT_ASTAR = 0

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49334 C/C++ External Procedures에서 메모리 참조 오류 발생 시 예외 처리 부족으로 Altibase 서버가 비정상 종료합니다.

-   **module** : qp-psm-trigger-execute

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : C/C++ External Procedures에서 메모리 참조 오류 발생 시 예외 처리 부족으로 Altibase 서버가 비정상 종료하는 현상을 수정합니다.
    
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
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    7.1.0.6.2     |          6.5.1          |    8.10.1    |        7.1.7        |            7.4.6             |

> Altibase 7.1 패치 버전별 히스토리는 [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7_1_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

> 메타 버전이 변경된 패치 버전을 롤백하려는 경우, [메타다운그레이드](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Installation.md#%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9Cmeta-downgrade)를 참고한다.

#### CM protocol Version

통신 프로토콜 버전은 변경되지 않았다.

#### Replication protocol Version

Replication 프로토콜 버전은 변경되지 않았다.

#### Sharding Version

샤딩 버전은 변경 되지 않았다.

> 알티베이스 샤딩 프로토콜 및 메타는 상위, 하위 호환성을 보장하지
> 않는다. 즉, 샤딩 버전이 다른 경우, 재구성해야 한다.

### 프로퍼티

#### 추가된 프로퍼티

#### 변경된 프로퍼티

#### 삭제된 프로퍼티

### 성능 뷰

#### 추가된 성능 뷰

#### 변경된 성능 뷰

#### 삭제된 성능 뷰
