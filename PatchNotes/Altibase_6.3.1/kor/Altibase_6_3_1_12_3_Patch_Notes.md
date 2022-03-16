Altibase 6.3.1.12.3 Patch Notes
===============================

<br/>

<br/>

# Table of Contents

- [Fixed Bugs](#fixed-bugs)
  - [BUG-49423 SQL PLAN CACHE 처리 시 statement 객체가 정리되지 않은 경우 Altibase 서버가 비정상 종료하거나 CPU 사용률이 증가할 수 있습니다.](#bug-49423sql-plan-cache-%EC%B2%98%EB%A6%AC-%EC%8B%9C-statement-%EA%B0%9D%EC%B2%B4%EA%B0%80-%EC%A0%95%EB%A6%AC%EB%90%98%EC%A7%80-%EC%95%8A%EC%9D%80-%EA%B2%BD%EC%9A%B0-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%98%EA%B1%B0%EB%82%98-cpu-%EC%82%AC%EC%9A%A9%EB%A5%A0%EC%9D%B4-%EC%A6%9D%EA%B0%80%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-49439 AUDIT disconnect 설정 환경에서 데이터베이스 세션 종료 시 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-49439audit-disconnect-%EC%84%A4%EC%A0%95-%ED%99%98%EA%B2%BD%EC%97%90%EC%84%9C-%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4-%EC%84%B8%EC%85%98-%EC%A2%85%EB%A3%8C-%EC%8B%9C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-49532 LEFT OUTER JOIN 왼쪽이 집합 연산을 포함한 인라인 뷰이고 ON 절의 AND 조건에 SUBQUERY가 포함된 경우 Altibase 서버가 비정상 종료합니다.](#bug-49532-left-outer-join-%EC%99%BC%EC%AA%BD%EC%9D%B4-%EC%A7%91%ED%95%A9-%EC%97%B0%EC%82%B0%EC%9D%84-%ED%8F%AC%ED%95%A8%ED%95%9C-%EC%9D%B8%EB%9D%BC%EC%9D%B8-%EB%B7%B0%EC%9D%B4%EA%B3%A0-on-%EC%A0%88%EC%9D%98-and-%EC%A1%B0%EA%B1%B4%EC%97%90-subquery%EA%B0%80-%ED%8F%AC%ED%95%A8%EB%90%9C-%EA%B2%BD%EC%9A%B0-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49554 Java 9 이상에서 DB Link 구동이 실패합니다.](#bug-49554-java-9-%EC%9D%B4%EC%83%81%EC%97%90%EC%84%9C-db-link-%EA%B5%AC%EB%8F%99%EC%9D%B4-%EC%8B%A4%ED%8C%A8%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49619 디스크 인덱스에서 언두 테이블스페이스를 사용하는 경우 다른 트랜젝션에 의해 언두 영역이 재사용되어 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-49619%EB%94%94%EC%8A%A4%ED%81%AC-%EC%9D%B8%EB%8D%B1%EC%8A%A4%EC%97%90%EC%84%9C-%EC%96%B8%EB%91%90-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%8A%A4%ED%8E%98%EC%9D%B4%EC%8A%A4%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94-%EA%B2%BD%EC%9A%B0-%EB%8B%A4%EB%A5%B8-%ED%8A%B8%EB%9E%9C%EC%A0%9D%EC%85%98%EC%97%90-%EC%9D%98%ED%95%B4-%EC%96%B8%EB%91%90-%EC%98%81%EC%97%AD%EC%9D%B4-%EC%9E%AC%EC%82%AC%EC%9A%A9%EB%90%98%EC%96%B4-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
  - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
  - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)



Fixed Bugs
==========

### BUG-49423 SQL PLAN CACHE 처리 시 statement 객체가 정리되지 않은 경우 Altibase 서버가 비정상 종료하거나 CPU 사용률이 증가할 수 있습니다.

-   **module** : mm-plancache

-   **Category** : Maintainability

-   **재현 빈도** : Frequence

-   **설명** : SQL PLAN CACHE 처리 시 statement 객체가 정리되지 않은 경우 Altibase 서버가 비정상 종료하거나 CPU 사용률이 증가하는 현상을 수정합니다. 
    
    본 버그로 인한 Altibase 서버 비정상 종료 현상 발생 시 altibase\_error.log 에 아래와 같은 로그가 남습니다. 

    ```bash
    IDE_ASSERT( aTrans->mStatus == SMX_TX_END ), [smxTransMgr.h:272], errno=[2]
    [[ASSERT] ERROR LINE => [smxTransMgr.h:272]
    ```
    
    또한 수행 중인 SQL문이 없거나 적음에도 CPU 사용률이 증가하는 현상을 나타날 수 있습니다.
    
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

### BUG-49439 AUDIT disconnect 설정 환경에서 데이터베이스 세션 종료 시 Altibase 서버가 비정상 종료할 수 있습니다.

-   **module** : mm-altiaudit

-   **Category** : Maintainability

-   **재현 빈도** : Rare

-   **설명** : AUDIT disconnect 설정 환경에서 데이터베이스 세션 종료 시 Altibase 서버가 비정상 종료하는 현상을 수정합니다. 
    
-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

        altibase_error.log 에 아래와 같은 콜스택을 남기며 Altibase 서버가 비정상 종료합니다. 

        ```bash
        BEGIN-STACK [CRASH] =============================
        Caller[0] 0000000000417208      => mmmSignalHandler
        Caller[1] 00007F004DB5D5E0      => not found
        Caller[2] 0000000000442C3F      => mmtAuditManager::auditBySession(mmcStatement*)
        Caller[3] 000000000046925F      => mmcStatement::finalize()
        Caller[4] 0000000000470E6B      => mmcStatementManager::freeStatement(mmcStatement*)
        Caller[5] 0000000000462669      => mmcSession::finalize()
        Caller[6] 000000000041D62F      => mmtSessionManager::freeSession(mmcTask*)
        Caller[7] 0000000000413558      => mmcTask::finalize()
        Caller[8] 000000000041C9ED      => mmtSessionManager::freeTask(mmcTask*)
        Caller[9] 000000000042A485      => mmtServiceThread::terminateTask(mmcTask*)
        Caller[10] 000000000042AD82     => mmtServiceThread::executeTask()
        Caller[11] 000000000042B75C     => mmtServiceThread::run()
        Caller[12] 0000000000EA4A1B     => idtContainer::staticRunner(void*)
        Caller[13] 00007F004DB55E25     => not found
        Caller[14] 00007F004CC2434D     => not found
        END-STACK =======================================
        ```

    -   **예상 결과**

-   **Workaround**

    AUDIT disconnect 설정을 비활성화합니다.

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49532 LEFT OUTER JOIN 왼쪽이 집합 연산을 포함한 인라인 뷰이고 ON 절의 AND 조건에 SUBQUERY가 포함된 경우 Altibase 서버가 비정상 종료합니다.

-   **module** : qp-dml-pvo

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : LEFT OUTER JOIN 왼쪽이 집합 연산을 포함한 인라인 뷰이고 ON 절의 AND 조건에 SUBQUERY가 포함된 경우 Altibase 서버가 비정상 종료하는 현상을 수정합니다.

-   **재현 방법**

    -   **재현 절차**

        ```sql
        DROP TABLE T1;
        DROP TABLE T2;
        DROP TABLE T3;
        
        CREATE TABLE T1 ( I1 VARCHAR(10), I2 VARCHAR(10));
        CREATE TABLE T2 ( I1 VARCHAR(10), I2 VARCHAR(10));
        CREATE TABLE T3 ( I1 VARCHAR(10), I2 VARCHAR(10), I3 VARCHAR(10));
        
        SELECT A.I1
          FROM T1 A 
          LEFT OUTER JOIN (SELECT I1 , SUM(I2) AS TOT_GWASE_PYOJUN_PRC
                             FROM T2 TA
                            GROUP BY I1 ) C 
          ON A.I1 = C.I1 
          AND C.TOT_GWASE_PYOJUN_PRC >= (SELECT I1 FROM T3 ) ;
        ```

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

    ```sql
    SELECT A.i1
      FROM t1 A 
      LEFT OUTER JOIN (SELECT i1 , SUM(i2) AS TOT_GWASE_PYOJUN_PRC
                         FROM t2 TA
                     GROUP BY i1 ) C 
      ON A.i1 = C.i1
     WHERE C.TOT_GWASE_PYOJUN_PRC >= (SELECT i1 FROM t3 ) ;
    ```

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49554 Java 9 이상에서 DB Link 구동이 실패합니다. 

-   **module** : dblink

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : Java 9 이상에서 DB Link 구동 실패 시 -d64 옵션 삭제 후 재구동하도록 수정하였습니다. 이 과정에서 altibase_error.log에 아래의 에러 메시지가 기록될 수 있습니다. 

    ```
    Unrecognized option: -d64
    Error: Could not create the Java Virtual Machine.
    Error: A fatal exception has occurred. Program will exit. 
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

### BUG-49619 디스크 인덱스에서 언두 테이블스페이스를 사용하는 경우 다른 트랜젝션에 의해 언두 영역이 재사용되어 Altibase 서버가 비정상 종료할 수 있습니다.

-   **module** : sm-disk-index

-   **Category** : Fatal

-   **재현 빈도** : Rare

-   **설명** : 디스크 인덱스에서 언두 테이블스페이스를 사용하는 경우 다른 트랜젝션에 의해 언두 영역이 재사용되어 Altibase 서버가 비정상 종료하는 현상을 수정합니다.
    
    본 버그로 인한 Altibase 서버 비정상 종료 발생 시 트레이스 로그에 아래와 같은 로그가 기록됩니다.

    - altibase\_error.log
    
       ```
       [ASSERT] ERROR LINE => [sdnIndexCTL.cpp:2208]
       ```
    
    - altibase\_boot.log 에 아래와 같은 형태의 인덱스 및 언두 페이지 정보 기록
    
        ```
    [2022/02/09 16:42:10] [Thread-28749] [Level-0]
        Undo PageID               : 56023
    Undo Slot Number          : 91
        UndoRec Hdr Type          : 2
    Chained CTS's Commit SCN  : 61801506952
        Min DskView SCN           : 61801348159
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
|    6.3.1.12.3    |          6.2.1          |    6.3.1     |        7.1.1        |            7.4.1             |

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
