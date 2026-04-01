Altibase 7.3.0.1.9 Patch Notes
================================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-52215 abm 로그(abm.log) 경로 지정 기능 추가](#bug-5221)
    - [BUG-52224 이중화 Give-up 관련 로그 메시지 추가](#bug-52224)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-48937 증분 백업 디렉토리 경로에 사용자가 생성한 디렉토리가 존재하는 경우, 백업 파일의 삭제가 실패하는 문제를 수정](#bug-48937)
    - [BUG-51953 메모리 테이블스페이스 자원 부족 시 이중화 리시버를 중지하도록 동작 개선](#bug-51953)
    - [BUG-52181 REPLICATION_MAX_LOGFILE 설정 환경에서 이중화 반영 중 Give-up 실패 문제 수정](#bug-52181)
    - [BUG-52213 통계 정보에 누적 시간이 잘못 기록되지 않도록 개선](#bug-52213)
    - [BUG-52190 Non-AutoCommit 환경에서 SELECT 문 실행 순서에 따른 Lock 비정상 해제 문제 수정](#bug-52190)
    - [BUG-52219 SUPPLEMENTAL LOG 를 생성할 때 VARIABLE COLUMN 패딩을 고려해야 합니다.](#bug-52219)
    - [BUG-52230 다른 사용자가 부여한 Role 권한을 SYS 계정에서 회수시에 The meta table crashed. 에러가 발생](#bug-52230)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-52215<a name=bug-52215></a> abm 로그(abm.log) 경로 지정 기능 추가

-   **module** :

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : abm.log 파일의 생성 경로를 지정할 수 있도록 `-log_path` 옵션이 추가되었다. `-log_path`를 지정하지 않으면, abm이 실행되는 현재 디렉터리에 abm.log 파일이 생성된다.
    
    또한 abm.properties 파일이 추가되었으며, 이 파일의 `LOG_PATH` 프로퍼티를 통해서도 abm.log 파일의 생성 경로를 지정할 수 있다.
    
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

### BUG-52224<a name=bug-52224></a> 이중화 Give-up 관련 로그 메시지 추가

- **module** : rp-sender

- **Category** : Enhancement

- **재현 빈도** : Always

- **설명** : `REPLICATION_MAX_LOGFILE` 프로퍼티 값을 1 이상으로 설정한 이후, Give-up이 발생했을 때 확인할 수 있는 로그 메시지와 Give-up
  이후 이중화 SENDER가 재시작되었을 때 확인할 수 있는 로그 메시지가 추가 되었습니다.

  로그 메시지는 아래와 같이 추가되었습니다.

  -   Give-up 시작 시: **[Manager] Replication {replication_name} Sender Give-up Start.**
  -   Give-up 종료 시: **[Manager] Replication {replication_name} Sender Give-up End.**
  -   Give-up 수행 중 Sender 스레드 재시작 시: **[Manager] Replication {replication_name} Restarts Sender After Give-up.**

- **재현 방법**

  -   **재현 절차**

  -   **수행 결과**

  -   **예상 결과**

- **Workaround**

- **변경사항**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

Fixed Bugs
==========

### BUG-48937<a name=bug-48937></a> 증분 백업 디렉토리 경로에 사용자가 생성한 디렉토리가 존재하는 경우, 백업 파일의 삭제가 실패하는 문제를 수정

- **module** : sm

- **Category** : Message Error

- **재현 빈도** : Always

- **설명** : 증분 백업 디렉토리 경로에 사용자가 생성한 디렉토리가 존재하는 경우, "ALTER DATABASE DELETE OBSOLETE BACKUP FILES;" 구문 수행 시 [ERR-41082 : Internal server error]로 실패하던 문제를 수정하였습니다. 이제 증분 백업 디렉토리 내에 사용자 생성 디렉토리가 있더라도 해당 구문이 정상적으로 수행되며, 사용자가 생성한 디렉토리는 삭제되지 않습니다. 또한, 삭제할 수 없는 디렉토리에 대한 정보는 trc의 altibase_sm.log 파일에 기록됩니다. 

  - 예-altibase_sm.log 파일에 아래와 같은 메시지를 확인할 수 있습니다.

    [BackupInfoMgr] Unable to delete <backup_path> (errno=39)

- **재현 방법**

  -   **재현 절차**

  -   **수행 결과**

  -   **예상 결과**

- **Workaround**

- **변경사항**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

### BUG-51953<a name=bug-51953></a> 메모리 테이블스페이스 자원 부족 시 이중화 리시버를 중지하도록 동작 개선

-   **module** : rp

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : 이중화 반영 과정에서 아래와 같은 메모리 테이블스페이스 자원 부족으로 인해 반영에 실패하는 경우, 기존에는 해당 오류가 충돌로 처리되었으나, 개선 후에는 이중화 리시버를 중지하도록 동작이 변경되었습니다.
    -   메모리 테이블스페이스의 자동 확장 기능이 꺼져있는 경우
        (smERR_ABORT_UNABLE_TO_EXTEND_CHUNK_WHEN_AUTO_EXTEND_OFF)
    -   메모리 테이블스페이스의 크기가 MEM_MAX_TBS_SIZE 를 초과한 경우
        (smERR_ABORT_UNABLE_TO_EXTEND_CHUNK_MORE_THAN_MEM_MAX_DB_SIZE)
    -   메모리 테이블스페이스의 최대 크기를 초과한 경우
        (smERR_ABORT_UNABLE_TO_EXTEND_CHUNK_MORE_THAN_TBS_MAXSIZE )
    
- **재현 방법**

  -   **재현 절차**

  -   **수행 결과**

  -   **예상 결과**

- **Workaround**

- **변경사항**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

### BUG-52181<a name=bug-52181></a> REPLICATION_MAX_LOGFILE 설정 환경에서 이중화 반영 중 Give-up 실패 문제 수정

-   **module** : rp-sender
-   **Category** : Functional Error
-   **재현 빈도** : Frequence
-   **설명** : `REPLICATION_MAX_LOGFILE` 프로퍼티가 1 이상으로 설정된 환경에서, 이중화가 실행되어 레코드가 Standby 서버에 반영되고 있는 중일 경우 Give-up이 실패할 수 있는 문제를 수정하였습니다.

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

### BUG-52213<a name=bug-52213></a> 통계 정보에 누적 시간이 잘못 기록되지 않도록 개선

-   **module** : id

-   **Category** : Enhancement

-   **재현 빈도** : Unknown

-   **설명** : 통계 정보에 누적 시간이 잘못 기록되지 않도록 개선하였습니다.

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

### BUG-52190<a name=bug-52190></a> Non-AutoCommit 환경에서 SELECT 문 실행 순서에 따른 Lock 비정상 해제 문제 수정

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : Non-AutoCommit 모드에서 하나의 트랜잭션 내 여러 SELECT 문을 수행할 때, SELECT 문 실행 순서에 따라 IS_LOCK이 비정상적으로 해제되던 문제를 수정합니다.

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

### BUG-52219<a name=bug-52219></a> SUPPLEMENTAL LOG 를 생성할 때 VARIABLE COLUMN 패딩을 고려해야 합니다.

-   **module** : sm

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : SUPPLEMENTAL LOG 를 생성할 때 VARIABLE COLUMN의 패딩 처리가 올바르게 처리되지 않아, UPDATE문 수행시 실패하던 문제를 수정하였습니다.

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

### BUG-52230<a name=bug-52230></a> 다른 사용자가 부여한 Role 권한을 SYS 계정에서 회수시에 The meta table crashed. 에러가 발생

-   **module** : qp-ddl-dcl-execute

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 사용자 계정에서 생성한 Role에 객체 권한을 부여한 후, SYS 계정에서 해당 권한을 회수할 경우  [ERR-31015 : The meta table crashed.] 오류가 발생하던 문제를 수정합니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    ## userA user 생성, role 생성
    create user userA identified by userA;
    create role r_userA;
    
    ## userA 으로 접속하여 userA.T1 테이블 생성
    connect userA/userA;
    create table T1(c1 integer primary key, c2 varchar(10), c3 varchar(10));
    
    ## userA user(소유자)가 r_userA role에 객체 권한 부여
    grant delete, insert, select, update on userA.T1 to r_userA; 
    
    ## sys user가 r_userA role에게서 객체권한 회수 시도
    connect sys/manager;
    revoke delete, insert, select, update on userA.T1 from r_userA;
    ```

  - **수행 결과**

        [ERR-31015 : The meta table crashed.
        0001 : revoke delete, insert, select, update on userA.T1 from R_userA
        ^ ^
        ]

  - **예상 결과**

    ```
    Revoke success.
    ```

-   **Workaround**

        sys user가 권한을 주고 회수

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
| 7.3.0.1.9        | 7.3.0                   | 9.4.1        | 7.1.8               | 7.4.9                        |

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
