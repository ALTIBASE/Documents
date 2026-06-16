Altibase 7.1.0.10.9 Patch Notes
===============================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-52165 비정상 종료 발생 시 진단 정보 보강](#bug-52165)
    - [BUG-52321 Altibase 소스 커넥터에서 debezium 형식의 메시지 출력 지원](#bug-52321)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-52314 External Procedure 수행 중 ERR-010A3 : Failed to start an agent process 에러 발생 시 altibase_qp.log에 진단용 메시지 추가](#bug-52314)
    - [BUG-52316 Disconnect Audit 처리 중 서버 비정상 종료 문제 수정](#bug-52316)
    - [BUG-52320 이중화 테이블 Sync 중 데드락 발생 시 즉시 실패하도록 개선](#bug-52320)
    - [BUG-52337 ERR-4203, ERR-71018, ERR-71019 발생 시 trc 로그에 클라이언트 정보 출력 개선](#bug-52337)
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

### BUG-52320<a name=bug-52320></a> 이중화 테이블 Sync 중 데드락 발생 시 즉시 실패하도록 개선

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

### BUG-52337<a name=bug-52337></a> ERR-4203, ERR-71018, ERR-71019 발생 시 trc 로그에 클라이언트 정보 출력 개선

-   **module** : mm

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : 클라이언트가 비정상 종료되어 ERR-4203, ERR-71018 또는 ERR-71019가 발생하는 경우, trc 로그에 세션 ID와 최소한의 연결 정보만 기록되던 문제를 개선하였습니다. 이제 클라이언트 강제 종료가 감지되면 세션 ID뿐만 아니라 접속 주소, 클라이언트 PID, 패키지 버전, 프로토콜 버전, 클라이언트 유형(Client Type), 애플리케이션 정보(AppInfo) 등 추가 클라이언트 정보를 trc 로그에 함께 출력합니다. 이를 통해 장애 분석 및 원인 추적이 보다 용이해졌습니다.

- **재현 방법**

  -   **재현 절차**

          kill -9 client_pid

  - **수행 결과**

        [2026/05/06 09:02:35 C5120E6] [PID:84561] (Thread-139985260955392] [LWP-86862]
        ERR-4203(errno=11) The session has been disconnected by the client
        Session ID : 2941
        Client Info : IPC

  -   **예상 결과**

          [2026/05/06 09:02:35 C5120E6] [PID:84561] (Thread-139985260955392] [LWP-86862]
          ERR-4203(errno=11) The session has been disconnected by the client
          Session ID : 2
          Client Info : TCP 127.0.0.1:44621
          Client PID : 3511
          Client Package : 8.2.0.0.0
          Client Protocol : 7.1.9
          Client Type : CLI-64LE
          Client AppInfo :

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
| 7.1.0.10.9       | 6.5.1                   | 8.12.1       | 7.1.7               | 7.4.7                        |

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
