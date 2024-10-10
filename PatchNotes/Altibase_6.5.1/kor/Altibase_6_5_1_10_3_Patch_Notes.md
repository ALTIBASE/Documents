# Altibase 6.5.1.10.3 Patch Notes

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-51057 Updateable Dynaset 지원](#bug-51057)
    - [BUG-51068 키 집합(KEYSET DRIVEN) 커서의 읽기 성능 개선](#bug-51068)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-51048 SQL_CURSOR_KEYSET_DRIVEN 커서로 SQLExecute, SQLFetch를 반복 수행하는 경우, 맨 처음 레코드만 반환됩니다.](#bug-51048)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-51057<a name=bug-51057></a> Updateable Dynaset 지원

-   **module** : mm-win-odbc

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : Updateable Dynaset 지원을 위해 ODBC 드라이버가 개선되었습니다.

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

### BUG-51068<a name=bug-51068></a> 키 집합(KEYSET DRIVEN) 커서의 읽기 성능 개선

-   **module** : mm-cli

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : SQL_CURSOR_KEYSET_DRIVEN 커서로 select를 수행할 때 서버-클라이언트간 통신 횟수(fetch 프로토콜)를 줄여 성능을 개선했습니다.
    
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

### BUG-51048<a name=bug-51048></a> SQL_CURSOR_KEYSET_DRIVEN 커서로 SQLExecute, SQLFetch를 반복 수행하는 경우, 맨 처음 레코드만 반환됩니다.

-   **module** : mm-cli

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : SQL_CURSOR_KEYSET_DRIVEN 커서로 SQLExectue, SQLFetch를 반복 수행하는 경우, 내부 오류로 인해 잘못된 데이터가 반환되는 문제를 수정하였습니다.
    
    또한 Fetch 과정에서 에러가 발생해도 사용자에게 성공을 반환하는
    오류도 함께 수정하였습니다.
    
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
        -   추가
            -   **ERR-51229 Failed to add the PROWID to the hash table.**
            -   **Cause**: Failed to add the PROWID to the hash table due to an internal error.
            -   **Action**: Contact Altibase's Support Center (http://support.altibase.com).

Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 6.5.1.10.3       | 6.3.1                   | 8.1.1        | 7.1.3               | 7.4.5                        |

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

#### 추가된 프로퍼티

#### 변경된 프로퍼티

#### 삭제된 프로퍼티

### 성능 뷰

#### 추가된 성능 뷰

#### 변경된 성능 뷰

#### 삭제된 성능 뷰
