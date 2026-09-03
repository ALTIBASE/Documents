Altibase 7.3.0.2.4 Patch Notes
================================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Fixed Bugs](#fixed-bugs)
  - [BUG-52444 iloader에서 `-lightmode` 옵션 제거](#bug-52444)
  - [BUG-52456 iloader에서 `-direct` 옵션 제거](#bug-52456)
  - [BUG-52499 AUDIT 사용 시 메모리 오류로 비정상 종료가 발생할 수 있는 문제 수정](#bug-52499)
  - [BUG-52502 Level 1 증분 백업 실패 문제 수정](#bug-52502)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
  - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
  - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Fixed Bugs
==========

### BUG-52444<a name=bug-52444></a> iloader에서 `-lightmode` 옵션 제거

-   **module** : ux-iloader

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : iloader 에서 `-lightmode` 옵션을 제거했습니다. 해당 옵션은 더 이상 사용할 수 없습니다.

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

### BUG-52456<a name=bug-52456></a> iloader에서 `-direct` 옵션 제거

-   **module** : ux-iloader

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : iloader에서  `-direct` 옵션을 제거했습니다. 해당 옵션은 더 이상 사용할 수 없습니다.
    
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

### BUG-52499<a name=bug-52499></a> AUDIT 사용 시 메모리 오류로 비정상 종료가 발생할 수 있는 문제 수정

-   **module** : mm-statement

-   **Category** : Memory Error

-   **재현 빈도** : Rare

-   **설명** : AUDIT 을 사용하는 환경에서 Direct Execute 방식으로 Statement를 수행할 경우, Statement가 정리되는 과정에서 메모리 오류가 발생하여 비정상 종료할 수 있는 문제가 있었습니다. 해당 문제를 수정했습니다.

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

### BUG-52502<a name=bug-52502></a> Level 1 증분 백업 실패 문제 수정

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : 여러 세션에서 동시에 데이터 변경이 발생하는 상황에서 Level 1 증분 백업을 수행할 경우, Change Tracking 과정의 동시성 문제로 인해 `ERR-42000` 오류가 발생하고 백업이 실패할 수 있었습니다. 이 문제를 수정하여 동시에 데이터 변경이 발생하는 환경에서도 Level 1 백업이 정상적으로 수행되도록 개선했습니다.

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
| 7.3.0.2.4        | 7.3.0                   | 9.4.1        | 7.1.8               | 7.4.9                        |

> Altibase 7.3 패치 버전별 히스토리는 [Version_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.3/Altibase_7_3_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의
> 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는
> 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

> 패치를 롤백하려는 경우, [메타다운그레이드](https://manual.altibase.com/7.3/start-here/install/3.-Uninstalling-Altibase-and-Meta-Downgrade/#%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9Cmeta-downgrade)를 참고한다.

#### CM protocol Version

통신 프로토콜 버전은 변경되지 않았다.

#### Replication protocol Version

Replication 프로토콜 버전은 변경되지 않았다.

### 프로퍼티

추가/변경/삭제된 프로퍼티 없음.

### 성능 뷰

추가/변경/삭제된 성능뷰 없음.
