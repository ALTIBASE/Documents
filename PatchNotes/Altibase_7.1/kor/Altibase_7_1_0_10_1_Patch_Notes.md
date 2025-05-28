Altibase 7.1.0.10.1 Patch Notes
===============================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Fixed Bugs](#fixed-bugs)
    - [BUG-51170 SM 모듈의 condition wait 의 Spurious wakeup 대응 코드 보완](#bug-51170)
    - [BUG-51366 송신자가 currentSN을 읽는 과정에서 동시성 문제로 인해 partial read가 발생 할 수 있습니다.](#bug-51366)
    - [BUG-51372 이중화 재 시작시 LOB 트랜잭션 로그 처리 오류 수정](#bug-51372)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Fixed Bugs
==========

### BUG-51170<a name=bug-51170></a> SM 모듈의 condition wait 의 Spurious wakeup 대응 코드 보완

-   **module** : sm\_resource

-   **Category** : Fatal

-   **재현 빈도** : Rare

-   **설명** : pthread_cond_wait, pthread_cond_timewait 에서 spurious wakup 대응 코드를 보완하여, 의도하지 않은 동작을 수행하지 않도록 수정합니다.

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

### BUG-51366<a name=bug-51366></a> 송신자가 currentSN을 읽는 과정에서 동시성 문제로 인해 partial read가 발생 할 수 있습니다.

-   **module** : sm
-   **Category** : Functional Error
-   **재현 빈도** : Rare
-   **설명** : 송신자가 currentSN을 읽는 과정에서 동시성 문제로 Partial Read가 발생하면 잘못된 값을 읽을 수 있으며, 이로 인해 이중화가 비정상적으로 중지될 수 있습니다. 이를 방지하기 위해 동시성 문제를 수정하여 Partial Read가 발생하지 않도록 개선하였습니다.
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

### BUG-51372<a name=bug-51372></a> 이중화 재 시작시 LOB 트랜잭션 로그 처리 오류 수정

-   **module** : rp-sender

-   **Category** : Functional Error

-   **재현 빈도** : Rare

-   **설명** : 이중화 재시작이 발생하는 시점에서 송신자가 LOB 트랜잭션 로그를 전송할 때, 이미 처리된 로그를 제외하는 로직에 문제가 있었습니다. 이로 인해 전송되지 않아야 할 일부 LOB 트랜잭션 로그가 잘못 전송되었으며, 그 결과 수신자에서 **"Transaction has not begun."** 오류가 발생하는 문제가 있었습니다. 이를 해결하기 위해 해당 로직을 개선하여, 불필요한 LOB 트랜잭션 로그가 전송되지 않도록 조치하였습니다.
    
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
| 7.1.0.10.1       | 6.5.1                   | 8.12.1       | 7.1.7               | 7.4.7                        |

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

#### 추가된 프로퍼티

#### 변경된 프로퍼티

#### 삭제된 프로퍼티

### 성능 뷰

#### 추가된 성능 뷰

#### 변경된 성능 뷰

#### 삭제된 성능 뷰
