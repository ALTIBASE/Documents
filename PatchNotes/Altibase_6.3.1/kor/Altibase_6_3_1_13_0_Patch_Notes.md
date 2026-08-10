Altibase 6.3.1.13.0 Patch Notes
===============================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Fixed Bugs](#fixed-bugs)
  - [BUG-46567 dumpStack의 동시성 문제 수정](#bug-46567)
  - [BUG-52140 `VIEW_FORCE=ON` 환경에서 View DDL이 100바이트를 초과할 경우 오류(Core Dump) 수정](#bug-52140)
  - [BUG-52316 Disconnect Audit 처리 중 서버 비정상 종료 문제 수정](#bug-52316)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
  - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
  - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Fixed Bugs
==========

### BUG-46567<a name=bug-46567></a> dumpStack의 동시성 문제 수정

- **module** : id

- **Category**:  Reliability

- **재현 빈도** : Rare

- **증상**: 여러 쓰레드간 dumpStack시 동시성 문제 발생가능성이 있어, 이를 수정하였습니다.

- **재현 방법**
  - **재현 절차** 

  - **수행 결과**

  - **예상 결과**

- **Workaround** 

- **변경사항** 
  - Performance view
  - Property
  - Compile Option
  - Error Code

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
| 6.3.1.13.0       | 6.2.1                   | 6.3.1        | 7.1.1               | 7.4.1                        |

> Altibase 6.3.1 패치 버전별 히스토리는 [Version_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_6.3.1/Altibase_6_3_1_Version_Histories.md) 에서 확인할 수 있다.

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

추가/변경/삭제된 프로퍼티

### 성능 뷰

추가/변경/삭제된 성능뷰
