# Altibase 6.5.1.11.0 Patch Notes

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-52066 비정상 종료 시 직전에 수행된 쿼리 출력 기능 추가](#bug-52066)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-51909 서버 비정상 종료시 콜스택에 클라이언트 PID, COMMIT MODE, COMM_NAME, statement 정보 등을 추가로 출력해야 합니다.](#bug-51909)
    - [BUG-51977 SQLDriverConnectW()에서 접속이 실패했는데 SQL_SUCCESS_WITH_INFO를 리턴하는 오류 수정](#bug-51977)
    - [BUG-52086 IPC 접속 환경에서 ServiceThread가 유효하지 않은 메모리를 참조할 수 있는 문제를 수정하였습니다.](#bug-52086)
    - [BUG-52128 테이블스페이스 DDL 추출 시 aexport 에서 Segmentation fault 오류 발생 문제 수정](#bug-52128)
    - [BUG-52140 `VIEW_FORCE=ON` 환경에서 View DDL이 100바이트를 초과할 경우 오류(Core Dump) 수정](#bug-52140)
    - [BUG-52188 비정상 종료 시 진단 덤프 정보 수집 안정성 개선](#bug-52188)
    - [BUG-52262 구버전 클라이언트(6.1.1 이하) 연결 중 잘못된 프로토콜 헤더가 수신될 경우 서버가 비정상 종료되는 문제 수정](#bug-52262)
    - [BUG-52316 Disconnect Audit 처리 중 서버 비정상 종료 문제 수정](#bug-52316)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# New Features

### BUG-52066<a name=bug-52066></a> 비정상 종료 시 직전에 수행된 쿼리 출력 기능 추가

-   **module** : mm

-   **Category** : Enhancement

-   **재현 빈도** : Rare

-   **설명** : 서버 비정상 종료 시 시그널 핸들러에서 직전에 수행된 쿼리를 출력하는 기능을 추가하였습니다. 해당 기능은 `__QUERY_BUCKET_FLAG` 비공개 프로퍼티로 활성화할 수 있으며, 출력된 쿼리는 `dumptrc` 또는 `altibase_error.log` 파일에서 확인할 수 있습니다.

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

### BUG-51909<a name=bug-51909></a> 서버 비정상 종료시 콜스택에 클라이언트 PID, COMMIT MODE, COMM_NAME, statement 정보 등을 추가로 출력해야 합니다.

-   **module** : mm

-   **Category** : Other

-   **재현 빈도** : Rare

-   **설명** : 서버 비정상 종료시 분석에 도움이 되도록 클라이언트 PID, COMMIT MODE, COMM_NAME, statement 정보등을 altibase_error.log에 출력하도록 추가하였습니다. 기존 콜스택 정보 밑에 추가로 출력됩니다.

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

### BUG-51977<a name=bug-51977></a> SQLDriverConnectW()에서 접속이 실패했는데 SQL_SUCCESS_WITH_INFO를 리턴하는 오류 수정

-   **module** : mm-cli

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : SQLDriverConnectW()함수를 호출할 때 InConnectionString 인자에 유효하지 않은 IP 주소가 포함되어 있고, BufferLength 인자에 16과 같이 작은 값을 전달할 경우, 접속이 실패해야 하는데 `SQL_SUCCESS_WITH_INFO`가 반환되는 문제를 수정합니다.

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

### BUG-52086<a name=bug-52086></a> IPC 접속 환경에서 ServiceThread가 유효하지 않은 메모리를 참조할 수 있는 문제를 수정하였습니다.

-   **module** : mm

-   **Category** : Memory Error

-   **재현 빈도** : Rare

-   **설명** : IPC 접속 환경에서 ServiceThread가 유효하지 않은 메모리를 참조할 수 있는 문제를 수정하였습니다.

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

### BUG-52128<a name=bug-52128></a> 테이블스페이스 DDL 추출 시 aexport 에서 Segmentation fault 오류 발생 문제 수정

-   **module** : ux-aexport

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** :  테이블스페이스 DDL의 크기가 64KB를 초과할 경우, aexport 수행 중 Segmentation fault 오류가 발생하는 문제를 수정하였습니다.
    
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

### BUG-52140<a name=bug-52140></a> `VIEW_FORCE=ON` 환경에서 View DDL이 100바이트를 초과할 경우 오류(Core Dump) 수정

-   **module** : ux-aexport

-   **Category** : Functional Error

-   **재현 빈도** : Unknown

-   **설명** : `VIEW_FORCE=ON` 환경에서 View DDL이 100바이트를 초과할 경우, aexport 수행 중 core 파일이 생성되며 추출이 중단되던 문제를 수정했습니다.
    
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

### BUG-52188<a name=bug-52188></a> 비정상 종료 시 진단 덤프 정보 수집 안정성 개선

-   **module** : mm

-   **Category** : Reliability

-   **재현 빈도** : Rare

-   **설명** : 비정상 종료 시 특정 상황에서 세션 및 태스크 진단 정보가 누락되던 오류를 수정했습니다. 또한 장애 분석에 도움이 되도록 통신 읽기 버퍼와 서비스 스레드 Statement ID 정보도 함께 덤프하도록 개선하였다.
    
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

Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 6.5.1.11.0       | 6.3.1                   | 8.1.1        | 7.1.3               | 7.4.5                        |

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

추가/변경/삭제된 프로퍼티 없음.

### 성능 뷰

추가/변경/삭제된 성능뷰 없음.
