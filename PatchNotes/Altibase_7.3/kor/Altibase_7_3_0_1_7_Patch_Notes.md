Altibase 7.3.0.1.7 Patch Notes
================================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-52066 비정상 종료 시 직전에 수행된 쿼리 출력 기능 추가](#bug-52066)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-52087 ROW_NUMBER() 함수가 사용된 View에서 UNION ALL 사용 시 발생할 수 있는 오류 수정](#bug-52087)
    - [BUG-52091 이중화 환경에서 메타데이터 처리 중 동시성 문제 수정](#bug-52091)
    - [BUG-52111 abm -h 명령의 도움말 출력 개선](#bug-52111)
    - [BUG-52141 테이블스페이스 DDL 추출 시 64KB 초과 시 발생하던 문제 수정](#bug-52141)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# New Features

### BUG-52066<a name=bug-52066></a> 비정상 종료 시 직전에 수행된 쿼리 출력 기능 추가

-   **module** : mm
-   **Category** : Other
-   **재현 빈도** : Rare
-   **설명** : 서버 비정상 종료 시 시그널 핸들러에서 직전에 수행된 쿼리를 출력하는 기능을 추가하였습니다.
     해당 기능은 `__QUERY_BUCKET_FLAG` 프로퍼티로 활성화할 수 있으며, 출력된 쿼리는 `dumptrc` 또는 `altibase_error.log` 파일에서 확인할 수 있습니다.                                    
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

# Fixed Bugs

### BUG-52087<a name=bug-52087></a> ROW_NUMBER() 함수가 사용된 View에서 UNION ALL 사용 시 발생할 수 있는 오류 수정

-   **module** : qp

-   **Category** : Fatal

-   **재현 빈도** : Rare

-   **설명** : `ROW_NUMBER()` 함수가 사용된 View에서 `UNION ALL`이 포함된 쿼리를 수행할 때, 특정 상황에서 오류가 발생할 수 있는 문제를 수정하였습니다.

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

### BUG-52091<a name=bug-52091></a> 이중화 환경에서 메타데이터 처리 중 동시성 문제 수정

-   **module** : rp

-   **Category** : Fatal

-   **재현 빈도** : Rare

-   **설명** : 이중화 환경에서 메타 데이터 처리 중 발생할 수 있는 동시성 문제를 수정하였습니다.
    
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

### BUG-52111<a name=bug-52111></a> abm -h 명령의 도움말 출력 개선

-   **module** : ux-abm

-   **Category** : Other

-   **재현 빈도** : Always

-   **설명** : abm -h 명령의 도움말 출력에 불필요한 내용이 포함되어 있던 부분을 개선하였습니다.

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

### BUG-52141<a name=bug-52141></a> 테이블스페이스 DDL 추출 시 64KB 초과 시 발생하던 문제 수정

-   **module** : ux-aexport

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 테이블스페이스 DDL의 크기가 64KB를 초과할 경우, DBMS\_METADATA 의 VARCHAR 크기 제한으로 인해 DDL추출이 정상적으로 수행되지 않던 문제를 수정하였습니다.
    
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
| 7.3.0.1.7        | 7.3.0                   | 9.4.1        | 7.1.8               | 7.4.9                        |

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
