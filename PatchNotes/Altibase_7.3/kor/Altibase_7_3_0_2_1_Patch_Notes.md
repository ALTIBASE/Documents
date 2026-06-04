# Altibase 7.3.0.2.1 Patch Notes

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-52165 비정상 종료 발생 시 진단 정보 보강](#bug-52165)
    - [BUG-52321 Altibase 소스 커넥터에서 debezium 형식의 kafka 메시지 출력 지원](#bug-52321)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-52244 서버 재시작 시 통계 정보 수집 과정에서 META TABLE에 대한 불필요한 Lock 획득 문제 수정](#bug-52244)
    - [BUG-52257 UTransTimeout 발생시 boot 로그에 출력되는 Last Query 개선](#bug-52257)
    - [BUG-52261 oraAdapter에서 EMPTY_CLOB() 또는 EMPTY_BLOB()을 포함한 UPDATE 문을 동시 수행 시 timeout 발생 문제 수정](#bug-52261)
    - [BUG-52262 구버전 클라이언트(6.1.1 이하) 연결 중 잘못된 프로토콜 헤더가 수신될 경우 서버가 비정상 종료되는 문제 수정](#bug-52262)
    - [BUG-52284 모든 public synonym 제거 시 aexport에서 DBMS_METADATA 수행 실패 문제 수정](#bug-52284)
    - [BUG-52314 External Procedure 수행 중 ERR-010A3 : Failed to start an agent process 에러 발생 시 altibase_qp.log에 진단용 메시지 추가](#bug-52314)
    - [BUG-52316 Disconnect Adit 처리 중 서버 비정상 종료 문제 수정](#bug-52316)
    - [BUG-52318 SSL 통신 중 간헐적인 이중화 Sync 실패 문제 수정](#bug-52318)
    - [BUG-52320 이중화 테이블 Sync 중 데드락 발생 시 즉시 실패하도록 개선](#bug-52320)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-52165<a name=bug-52165></a> 비정상 종료 발생 시 진단 정보 보강

-   **module** : id

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : SIGSEGV 등 signal에 의한 비정상 종료 발생 시 원인 분석에 필요한 statement 의 시간 정보, 커서 정보 및 transaction lock 정보를 trc 파일에 출력하도록 개선되었습니다.

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

### BUG-52321<a name=bug-52321></a> Altibase 소스 커넥터에서 debezium 형식의 메시지 출력 지원

-   **module** : rp-kafkaConnector

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : 히든 프로퍼티를 통해 Altibase 소스 커넥터에서 메시지를 Debezium 형식으로 출력할 수 있는 옵션을 추가했습니다. 기본값은 기존 Confluent JDBC Connector 형식이며, 별도 설정이 없는 경우 기존 동작에는 영향을 주지 않습니다.

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

### BUG-52244<a name=bug-52244></a> 서버 재시작 시 통계 정보 수집 과정에서 META TABLE에 대한 불필요한 Lock 획득 문제 수정

-   **module** : sm

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 서버 재시작 시 통계 정보를 수집하는 과정에서 META TABLE에 대해서도 Lock을 획득하는 문제를 수정했습니다. META TABLE은 Lock 획득이 불필요하므로, 이제 META TABLE인 경우 Lock을 획득하지 않도록 개선했습니다.

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

### BUG-52257<a name=bug-52257></a> UTransTimeout 발생시 boot 로그에 출력되는 Last Query 개선

-   **module** : mm

-   **Category** : Enhancement

-   **재현 빈도** : Rare

-   **설명** : UTrans Timeout 발생 시 마지막으로 수행된 Statement가 해제된 경우 Last Query 정보가 "(null)"로 출력될 수 있는 문제를 개선했습니다. 이제 UTrans Timeout 발생 시 마지막으로 수행된 SQL 문을 Last Query로 출력하도록 개선했습니다.

- **재현 방법**

  - **재현 절차**

        (1) 트랜잭션 A 시작
        (2) 질의문 할당: SQLAllocHandle(SQL_HANDLE_STMT, dbc, &stmt);
        (3) 질의문 준비: SQLPrepare(stmt, "DELETE FROM DEMO_EX5 WHERE id = ?", SQL_NTS);
        (4) 질의문 수행: SQLExecute(stmt);
        (5) 질의문 해제: SQLFreeStmt(stmt, SQL_DROP);
        (6) Commit/Rollback 없이 트랜잭션 유지
        (7) UTrans Timeout 발생

  - **수행 결과**

        [2026/03/25 19:33:58 A9C][PID:103887][Thread-139717591328832][LWP-103881]
        [Notify : UTrans Timeout] Session Closed by Server : Session ID = 5
        CLIENT_INFO => TCP 127.0.0.1:57064(PID : 426111)
        Time Limit => 3600
        Running Time => 3601
        Last Query => (null)
        Caused by Transaction => 41896

  -   **예상 결과**

          [2026/03/25 19:33:58 A9C][PID:103887][Thread-139717591328832][LWP-103881]
          [Notify : UTrans Timeout] Session Closed by Server : Session ID = 5
          CLIENT_INFO => TCP 127.0.0.1:57064(PID : 426111)
          Time Limit => 3600
          Running Time => 3601
          Last Query => (SELECT .... )
          Caused by Transaction => 41896

-   **Workaround**

-   **변경사항**

    -   Performance view
        
    -   Property
        
    -   Compile Option
    -   Error Code

### BUG-52261<a name=bug-52261></a> oraAdapter에서 EMPTY_CLOB() 또는 EMPTY_BLOB()을 포함한 UPDATE 문을 동시 수행 시 timeout 발생 문제 수정

-   **module** : rp-oraAdapter

-   **Category** : Testcase Fail

-   **재현 빈도** : Frequence

-   **설명** : oraAdapter에서 EMPTY_CLOB() 및 EMPTY_BLOB()을 포함한 UPDATE 문을 동시에 수행할 경우, timeout이 발생하는 문제를 수정했습니다.

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

### BUG-52262<a name=bug-52262></a> 구버전 클라이언트(6.1.1 이하) 연결 중 잘못된 프로토콜 헤더가 수신될 경우 서버가 비정상 종료되는 문제 수정

-   **module** : cm

-   **Category** : Fatal

-   **재현 빈도** : Rare

-   **설명** : 구버전 클라이언트(6.1.1 이하) 연결 중 잘못된 프로토콜 헤더 값이 수신되는 특정 상황에서 서버가 비정상 종료될 수 있는 문제를 수정하였습니다.
    
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

### BUG-52284<a name=bug-52284></a> 모든 public synonym 제거 시 aexport에서 DBMS_METADATA 수행 실패 문제 수정

-   **module** : ux-dbms_metadata

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 모든 public synonym이 제거된 상태에서 aexport 수행 시, DBMS_METADATA 관련 작업이 실패하는 문제를 수정했습니다.
    
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

### BUG-52314<a name=bug-52314></a> External Procedure 수행 중 ERR-010A3 : Failed to start an agent process 에러 발생 시 altibase_qp.log에 진단용 메시지 추가

-   **module** : qp-select
-   **Category** : Functional Error
-   **재현 빈도** : Always
-   **설명** : External Procedure 수행 중 ERR-010A3 : Failed to start an agent process 에러 발생 시, 원인 분석을 위해 altibase_qp.log에 진단용 메시지를 추가했습니다. Agent 프로세스 기동 실패의 원인에 따라 `Failed to open agent path.`, `Failed to fork process.`, `Invalid Agent Process.` 메시지를 기록하며, Linux 환경에서는 errno 정보도 함께 출력합니다.
    -   Failed to open agent path. : 에이전트 프로세스 파일(extprocAgent)이 없거나 실행권한 등이 부족한 경우

    -   Failed to fork process. : 에이전트 프로세스를 fork하는 작업이 실패한 경우
    
    -   Invalid Agent Process : 에이전트 프로세스가 존재하지 않는 등 비정상 상황
    
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

### BUG-52316<a name=bug-52316></a> Disconnect Audit 처리 중 서버 비정상 종료 문제 수정

-   **module** : mm
-   **Category** : Functional Error
-   **재현 빈도** : Rare
-   **설명** : Disconnect audit 처리 과정에서 Session이 NULL인 경우, 서버가 비정상 종료하는 문제를 수정하였습니다.
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

### BUG-52318<a name=bug-52318></a> SSL 통신 중 간헐적인 이중화 Sync 실패 문제 수정

-   **module** : rp
-   **Category** : Functional Error
-   **재현 빈도** : Rare
-   **설명** : SSL 통신 환경에서 간헐적으로 발생하는 일시적인 통신 오류로 인해 이중화 Sync가 실패할 수 있는 문제를 수정했습니다.
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

### BUG-52320<a name=bug-52320></a> 이중화 테이블 Sync 중 데드락 발생 시 즉시 실패하도록 개선

-   **module** : rp
-   **Category** : Functional Error
-   **재현 빈도** : Rare
-   **설명** : INSERT가 수행 중인 이중화 대상 테이블에 대해 Sync를 수행할 때 특정 상황에서 데드락이 발생하면, `REPLICATION_SYNC_LOCK_TIMEOUT` 만큼 대기 후 Sync가 실패하는 문제를 개선했습니다. 이제 Sync 수행 중 필요한 Table IS Lock을 획득하지 못하는 경우 즉시 실패하도록 개선했습니다.
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
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 7.3.0.2.1        | 7.3.0                   | 9.4.1        | 7.1.8               | 7.4.9                        |

> Altibase 7.3 패치 버전별 히스토리는 [Version_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.3/Altibase_7_3_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의
> 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는
> 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

> 패치를 롤백하려는 경우,
> [메타다운그레이드](https://manual.altibase.com/7.3/start-here/install/3.-Uninstalling-Altibase-and-Meta-Downgrade/#%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9Cmeta-downgrade)를
> 참고한다.

#### CM protocol Version

통신 프로토콜 버전은 변경되지 않았다.

#### Replication protocol Version

Replication 프로토콜 버전은 변경되지 않았다.

### 프로퍼티

추가/변경/삭제된 프로퍼티 없음.

### 성능 뷰

추가/변경/삭제된 성능뷰 없음.
