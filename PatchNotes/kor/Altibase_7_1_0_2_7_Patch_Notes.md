<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Altibase 7.1.0.2.7 Patch Notes](#altibase-71027-patch-notes)
  - [New Features](#new-features)
    - [BUG-47159  dbms_metadata 패키지를 aexport에 적용](#bug-47159-dbms_metadata-%ED%8C%A8%ED%82%A4%EC%A7%80%EB%A5%BC-aexport%EC%97%90-%EC%A0%81%EC%9A%A9)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-45933  APRE에서 APRE_NUMERIC 타입 사용시 소수점값이 잘리는 문제 수정](#bug-45933-apre%EC%97%90%EC%84%9C-apre_numeric-%ED%83%80%EC%9E%85-%EC%82%AC%EC%9A%A9%EC%8B%9C-%EC%86%8C%EC%88%98%EC%A0%90%EA%B0%92%EC%9D%B4-%EC%9E%98%EB%A6%AC%EB%8A%94-%EB%AC%B8%EC%A0%9C-%EC%88%98%EC%A0%95)
    - [BUG-46019  프로시저에서 PRINT 구문 사용시 불필요한 데이터 전송을 제거해야 합니다.](#bug-46019-%ED%94%84%EB%A1%9C%EC%8B%9C%EC%A0%80%EC%97%90%EC%84%9C-print-%EA%B5%AC%EB%AC%B8-%EC%82%AC%EC%9A%A9%EC%8B%9C-%EB%B6%88%ED%95%84%EC%9A%94%ED%95%9C-%EB%8D%B0%EC%9D%B4%ED%84%B0-%EC%A0%84%EC%86%A1%EC%9D%84-%EC%A0%9C%EA%B1%B0%ED%95%B4%EC%95%BC-%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Altibase 7.1.0.2.7 Patch Notes
==============================

New Features
------------

### BUG-47159  dbms_metadata 패키지를 aexport에 적용

-   **module** : ux-aexport

-   **Category** : Maintainability

-   **재현 빈도** : Always

-   **증상** : dbms_metadata 패키지를 aexport에 적용

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
----------

### BUG-45933  APRE에서 APRE_NUMERIC 타입 사용시 소수점값이 잘리는 문제 수정

-   **module** : mm-apre

-   **Category** : Functional Error

-   **재현 빈도** : Always

- **증상** : APRE에서 APRE_NUMERIC 타입 사용시 소수점값이 잘리는 문제 수정하기 위해, SQL_NUMERIC_STRUCT 타입이 추가되었습니다.

  APRE에서 호스트변수로 SQL_NUMERIC_STRUCT 타입을 사용하기 위해서는 $ALTIBASE_HOME/sample/APRE 폴더내 numeric.sc 를 참고하시면됩니다.

- **재현 방법**

  - **재현 절차**

        CREATE TABLE T1 (C1 NUMERIC(10, 3));
        run numeric

  -   **수행 결과**

          111111

  -   **예상 결과**

          111111.11

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-46019  프로시저에서 PRINT 구문 사용시 불필요한 데이터 전송을 제거해야 합니다.

-   **module** : mm

-   **Category** : Efficiency

-   **재현 빈도** : Always

-   **증상** : 클라이언트에 메시지 콜백 함수가 등록되어 있는 경우에만
    서버 메시지를 클라이언트에 전송하도록 수정하였습니다.

    불필요한 메시지 전송으로 인한 성능 영향을 줄였습니다.

-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
        -   변경
            -   [V$SESSION](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_4.md#vsession)
                -   [MESSAGE_CALLBACK](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_4.md#message_callback) 컬럼 추가
                        \* REG : 클라이언트는 메시지콜백을 등록하였으며, 서버는
                    메시지를 클라이언트로 전송한다.
                        \* UNREG : 클라이언트는 메시지콜백을 등록하지 않았으며,
                    서버는 메시지를 클라이언트로 전송하지 않는다.
                        \* UNKNOWN : 클라이언트의 메시지콜백 등록 여부를 알 수
                    없으며, 서버는 메시지를 클라이언트로 전송한다.                                본 버그가 반영되지 않은 구버전 클라이언트가 접속한 경우 UNKNOWN 상태를 가진다.
        
    -   Property
    -   Compile Option
    -   Error Code

Changes
-------

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 7.1.0.2.7        | 6.5.1                   | 8.7.1        | 7.1.7               | 7.4.5                        |

> Altibase 7.1 패치 버전별 히스토리는 [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7_1_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의
> 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

> 패치를 롤백하려는 경우, [메타다운그레이드](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Installation.md#%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9Cmeta-downgrade)를 참고한다.

#### CM protocol Version

통신 프로토콜 버전은 변경되지 않았다.

#### Replication protocol Version

Replication 프로토콜 버전은 변경되지 않았다.

### 프로퍼티

추가/변경/삭제된 프로퍼티 없음

### 성능 뷰

#### 변경된 성능 뷰

[V$SESSION](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_4.md#vsession)
