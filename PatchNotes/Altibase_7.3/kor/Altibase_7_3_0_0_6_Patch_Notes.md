# Altibase 7.3.0.0.6 Patch Notes

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-50855 BYTE, VARBYTE 데이터 타입에 대한 SIMPLE QUERY 최적화 지원](#bug-50855)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-50775 Multiple Statement 쿼리를 수행할 때 SQLExecute() 결과값이 SQL_NO_DATA일 경우, execute 처리가 중단되는 문제를 수정합니다.](#bug-50775)
    - [BUG-50798 매체 복구(MEDIA RECOVERY) 진행 중에 체크포인트 이미지 파일이 추가되 경우, 내부적으로 PCH(Page Control Header)를 할당하는 과정에서 오류가 있어서 수정합니다.](#bug-50798)
    - [BUG-50817 DISK TABLE, DISK INDEX AGING 수행 시, 테이블에 X Lock(Exclusive Lock) 잡던 것을 IX Lock(Intent Exclusive Lock)으로 변경합니다.](#bug-50817)
    - [BUG-50840 매체 복구(MEDIA RECOVERY) 진행 중에 체크포인트 이미지 파일이 추가되는 경우, 내부적으로 페이지가 할당되지 않는 경우가 있어서 수정합니다.](#bug-50840)
    - [BUG-50851 Active-Standby 상황에서 Standby쪽에 DDL 수행 후 Receiver가 재시작할 때, ERR-61075 : Timeout exceed 에러가 발생하는 문제를 수정합니다.](#bug-50851)
    - [BUG-50869 IPCDA 접속 과정에서 쓰레드 매니저가 행이 걸리는 현상이 발생합니다.](#bug-50869)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# New Features

### BUG-50855<a name=bug-50855></a> BYTE, VARBYTE 데이터 타입에 대한 SIMPLE QUERY 최적화 지원

-   **module** : qp

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : BYTE, VARBYTE 데이터 타입에 대해 SIMPLE QUERY 최적화를 지원합니다. SIMPLE QUERY 최적화를 위해서는 [EXECUTOR_FAST_SIMPLE_QUERY](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#executor_fast_simple_query) 프로퍼티를 참고합니다.

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

### BUG-50775<a name=bug-50775></a> Multiple Statement 쿼리를 수행할 때 SQLExecute() 결과값이 SQL_NO_DATA일 경우, execute 처리가 중단되는 문제를 수정합니다.

-   **module** : mm-cli

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : Multiple Statement 쿼리를 수행할 때 SQLExecute() 결과값이 SQL_NO_DATA일 경우, execute가 중단되지 않도록 수정하였습니다.
    
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

### BUG-50798<a name=bug-50798></a> 매체 복구(MEDIA RECOVERY) 진행 중에 체크포인트 이미지 파일이 추가되 경우, 내부적으로 PCH(Page Control Header)를 할당하는 과정에서 오류가 있어서 수정합니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : 매체 복구(MEDIA RECOVERY) 진행 중에 체크포인트 이미지 파일이 추가되는 경우, 내부적으로 PCH(Page Control Header)를 할당하는 과정에서 오류가 있어서 수정하였습니다.

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

### BUG-50817<a name=bug-50817></a> DISK TABLE, DISK INDEX AGING 수행 시, 테이블에 X Lock(Exclusive Lock) 잡던 것을 IX Lock(Intent Exclusive Lock)으로 변경합니다.

-   **module** : sm

-   **Category** : Other

-   **재현 빈도** : Always

-   **설명** : DISK TABLE, DISK INDEX AGING 구문 수행 시, 테이블에 X Lock(Exclusive
    Lock) 잡던 것을 IX Lock(Intent Exclusive Lock)으로 변경합니다. 페이지 정보를 갱신하기 위해 디스크 테이블 또는 디스크 인덱스에 AGING을 수행할 때, X Lock으로 인해 트랜잭션을 대기하다가 timeout이
    발생하는 문제가 해결되었습니다.
    
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

### BUG-50840<a name=bug-50840></a> 매체 복구(MEDIA RECOVERY) 진행 중에 체크포인트 이미지 파일이 추가되는 경우, 내부적으로 페이지가 할당되지 않는 경우가 있어서 수정합니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : 매체 복구(MEDIA RECOVERY) 진행 중에 체크포인트 이미지 파일이 추가되는 경우, 내부적으로 페이지가 할당되지 않는 경우가 있어서 수정하였습니다.

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

### BUG-50851<a name=bug-50851></a> Active-Standby 상황에서 Standby쪽에 DDL 수행 후 Receiver가 재시작할 때, ERR-61075 : Timeout exceed 에러가 발생하는 문제를 수정합니다.

-   **module** : rp-receiver
-   **Category** : Functional Error
-   **재현 빈도** : Frequence
-   **설명** : Standby 서버에서 DDL을 수행하기 위해 이중화 테이블에 LOCK을 잡은 상태에서 Active 서버의 Sender가 재시작하면, Standby 서버의 Receiver가 재시작되면서 테이블의 LOCK을 대기하는데, 이때  [DDL_LOCK_TIMEOUT](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#ddl_lock_timeout-%EB%8B%A8%EC%9C%84-%EC%B4%88)에 설정된 시간(기본값 0초)만큼 대기하고 ERR-61075 : Timeout exceed. 에러를 출력합니다. Receiver가 재시작할 때 테이블의 LOCK을 대기해야할 경우, [DDL_LOCK_TIMEOUT](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#ddl_lock_timeout-%EB%8B%A8%EC%9C%84-%EC%B4%88)이 아니라 [REPLICATION_CONNECT_TIMEOUT](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#replication_connect_timeout-%EB%8B%A8%EC%9C%84-%EC%B4%88)(기본값 10초)만큼 대기하도록 수정합니다.
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

### BUG-50869<a name=bug-50869></a> IPCDA 접속 과정에서 쓰레드 매니저가 행이 걸리는 현상이 발생합니다.

-   **module** : cm

-   **Category** : Hang

-   **재현 빈도** : Always

-   **설명** : IPCDA 쓰레드 매니저(Thread Manager)와 서비스 쓰레드(Service Thread) 간에 동기가 맞지
    않아 서버에서 행(HANG)이 발생하는 문제를 수정하였습니다.

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
| 7.3.0.0.6        | 7.3.0                   | 9.3.1        | 7.1.8               | 7.4.9                        |

> Altibase 7.3 패치 버전별 히스토리는 [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.3/Altibase_7_3_Version_Histories.md) 에서 확인할 수 있다.

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

#### 추가된 프로퍼티

#### 변경된 프로퍼티

#### 삭제된 프로퍼티

### 성능 뷰

#### 추가된 성능 뷰

#### 변경된 성능 뷰

#### 삭제된 성능 뷰
