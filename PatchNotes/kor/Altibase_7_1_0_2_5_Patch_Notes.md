<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Altibase 7.1.0.2.5 Patch Notes](#altibase-71025-patch-notes)
  - [New Features](#new-features)
    - [BUG-46790  shardjdbc에서 failover 지원](#bug-46790-shardjdbc%EC%97%90%EC%84%9C-failover-%EC%A7%80%EC%9B%90)
    - [BUG-46878  java version 9 이상을 사용할 경우 DBLink 시작 실패](#bug-46878-java-version-9-%EC%9D%B4%EC%83%81%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%A0-%EA%B2%BD%EC%9A%B0-dblink-%EC%8B%9C%EC%9E%91-%EC%8B%A4%ED%8C%A8)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-46938  Mathematics function data 전체를 재사용하기 위해 getStatus, setStatus 추가 시 성능이슈 수정](#bug-46938-mathematics-function-data-%EC%A0%84%EC%B2%B4%EB%A5%BC-%EC%9E%AC%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0-%EC%9C%84%ED%95%B4-getstatus-setstatus-%EC%B6%94%EA%B0%80-%EC%8B%9C-%EC%84%B1%EB%8A%A5%EC%9D%B4%EC%8A%88-%EC%88%98%EC%A0%95)
    - [BUG-46957  Invalid operation 에러의 Cause와 Action을 보강해야 합니다.](#bug-46957-invalid-operation-%EC%97%90%EB%9F%AC%EC%9D%98-cause%EC%99%80-action%EC%9D%84-%EB%B3%B4%EA%B0%95%ED%95%B4%EC%95%BC-%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-46977  Anonymous block의 select into 구문에서 ?로도 bind가 가능해야 합니다.](#bug-46977-anonymous-block%EC%9D%98-select-into-%EA%B5%AC%EB%AC%B8%EC%97%90%EC%84%9C-%EB%A1%9C%EB%8F%84-bind%EA%B0%80-%EA%B0%80%EB%8A%A5%ED%95%B4%EC%95%BC-%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-47043  checkpoint 하다가 server kill 후 server start 실패](#bug-47043-checkpoint-%ED%95%98%EB%8B%A4%EA%B0%80-server-kill-%ED%9B%84-server-start-%EC%8B%A4%ED%8C%A8)
    - [BUG-47048  aexport로 수행 후 생성된 스크립트에 QUEUE의 테이블스페이스 지정절이 누락됩니다.](#bug-47048-aexport%EB%A1%9C-%EC%88%98%ED%96%89-%ED%9B%84-%EC%83%9D%EC%84%B1%EB%90%9C-%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%EC%97%90-queue%EC%9D%98-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%8A%A4%ED%8E%98%EC%9D%B4%EC%8A%A4-%EC%A7%80%EC%A0%95%EC%A0%88%EC%9D%B4-%EB%88%84%EB%9D%BD%EB%90%A9%EB%8B%88%EB%8B%A4)
    - [BUG-47051  set explainplan on/only 후 프로시저를 실행하면 Function sequence error](#bug-47051-set-explainplan-ononly-%ED%9B%84-%ED%94%84%EB%A1%9C%EC%8B%9C%EC%A0%80%EB%A5%BC-%EC%8B%A4%ED%96%89%ED%95%98%EB%A9%B4-function-sequence-error)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Altibase 7.1.0.2.5 Patch Notes
==============================

New Features
------------

### BUG-46790  shardjdbc에서 failover 지원

-   **module** : mm-jdbc

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **증상** : shardjdbc에 failover 를 지원합니다.

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

### BUG-46878  java version 9 이상을 사용할 경우 DBLink 시작 실패

-   **module** : dblink

-   **Category** : Functional Error

-   **재현 빈도** : Always

- **증상** : java version 9이상에서  dblink start가 실패하는 문제가 있어, 수정하였습니다.

  Java version 9이상에서 dblink start 하면, altibase\_error.log 에
  아래의 에러가 기록될 수 있으나, 무시해도 됩니다.  java version 9
  이상에서 –d64 옵션이 제거되어 발생하는 에러로, 내부적으로 해당
  옵션을 제거하고 다시 dblink start 시도하기 때문입니다.

  Unrecognized option: -d64

  Error: Could not create the Java Virtual Machine.

  Error: A fatal exception has occurred. Program will exit. 

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

### BUG-46938  Mathematics function data 전체를 재사용하기 위해 getStatus, setStatus 추가 시 성능이슈 수정

-   **module** : mt-function

-   **Category** : Maintainability

-   **재현 빈도** : Always

-   **증상** : Mathematics function data 전체를 재사용하기 위해 getStatus, setStatus 추가 시 성능 하락이 있어, 수정하였습니다.

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

### BUG-46957  Invalid operation 에러의 Cause와 Action을 보강해야 합니다.

-   **module** : doc

-   **Category** : Manual

-   **재현 빈도** : Always

-   **증상** : CAUSE, ACTION을 사용자 관점에서 보강하였습니다.

    4, cmERR\_ABORT\_INVALID\_OPERATION = Invalid operation

    \# \*Cause: Client version is higher than Server version or internal
    error occurs while interpreting protocol.

    \# \*Action: Make sure Client version is same or lower than Server
    version, or contact Altibase's Support
    Center(http://support.altibase.com).

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

### BUG-46977  Anonymous block의 select into 구문에서 ?로도 bind가 가능해야 합니다.

-   **module** : qp-psm-trigger-pvo

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** :

- **재현 방법**

  - **재현 절차**

        BEGIN
          SELECT 1 INTO ? FROM DUAL;
        END;
        /

  -   **수행 결과**

          $ java SimpleSQL
          ERROR CODE    : 200705
          ERROR MESSAGE : SQL syntax error
          line 1: parse error
          BEGIN SELECT 1 INTO ? FROM DUAL; END;
                              ^
          java.sql.SQLException: SQL syntax error
          line 1: parse error
          BEGIN SELECT 1 INTO? FROM DUAL; END;
                             ^
                  at Altibase.jdbc.driver.ex.Error.processServerError(Error.java:369)
                  at Altibase.jdbc.driver.AltibasePreparedStatement.(AltibasePreparedStatement.java:125)
                  at Altibase.jdbc.driver.AltibaseCallableStatement.(AltibaseCallableStatement.java:46)
                  at Altibase.jdbc.driver.AltibaseConnection.prepareCall(AltibaseConnection.java:1183)
                  at SimpleSQL.main(SimpleSQL.java:45)

  -   **예상 결과**

          $ java SimpleSQL1

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47043  checkpoint 하다가 server kill 후 server start 실패

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **증상** : Checkpoint Image 생성 도중에 서버가 비정상 종료되면 재구동에 실패하는 문제가 있어, 수정하였습니다.

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

### BUG-47048  aexport로 수행 후 생성된 스크립트에 QUEUE의 테이블스페이스 지정절이 누락됩니다.

-   **module** : ux-aexport

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : DISK\_SYSTEM\_DATA 테이블스페이스에 생성한 Queue를 aexport 로 수행후 생성된 스크립트에 QUEUE의 테이블 스페이스 지정절이 누락되는 문제가 있어, 수정하였습니다.

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

### BUG-47051  set explainplan on/only 후 프로시저를 실행하면 Function sequence error

-   **module** : ux-isql

-   **Category** : Functionality

-   **재현 빈도** : Always

- **증상** : set explainplan on/only 상태에서 ResultSet을 반환하는 프로시저를 실행하면, Function sequence error 또는 Invalid statement processing request 에러 발생하는 문제를 수정하였습니다.

- **재현 방법**

  - **재현 절차**

        CREATE OR REPLACE PACKAGE STANDARD AS TYPE SYS_REFCURSOR IS REF CURSOR;
        END;
        /
        DROP TABLE t1;
        CREATE TABLE t1 (id INT, val VARCHAR(10));
        CREATE OR REPLACE PROCEDURE proc1 (oc OUT SYS_REFCURSOR)
        AS
        BEGIN
            OPEN oc FOR 'SELECT * FROM t1';
        END;
        /
        set explainplan on;
        EXEC proc1();
        set explainplan only;
        EXEC proc1();
        set explainplan off;
        EXEC proc1();

  -   **수행 결과**

          iSQL> set explainplan on;
          iSQL> EXEC proc1();
          ID          VAL
          ---------------------------
          No rows selected.
          [ERR-4103A : Invalid statement processing request]
          iSQL> set explainplan only;
          iSQL> EXEC proc1();
          ID          VAL
          ---------------------------
          No rows selected.
          [ERR-4103A : Invalid statement processing request]
          iSQL> set explainplan off;
          iSQL> EXEC proc1();
          ID          VAL
          ---------------------------
          No rows selected.
          Execute success.

  - **예상 결과**

        iSQL> set explainplan on;
        iSQL> EXEC proc1();
        EXEC proc1();
        ID          VAL
        ---------------------------
        No rows selected.
        ------------------------------------------------------------
                               NO PLAN
        ------------------------------------------------------------
        Execute success.
        iSQL> set explainplan only;
        iSQL> EXEC proc1();
        set explainplan off;
        ID          VAL
        ---------------------------
        No rows selected.
        ------------------------------------------------------------
                               NO PLAN
        ------------------------------------------------------------
        Execute success.
        iSQL> set explainplan off;
        iSQL> EXEC proc1();
        ID          VAL
        ---------------------------
        No rows selected.
        Execute success.

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

Changes
-------

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version | sharding version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- | ---------------- |
| 7.1.0.2.5        | 6.5.1                   | 8.7.1        | 7.1.7               | 7.4.5                        | 2.2.1            |

> Altibase 7.1 패치 버전별 히스토리는 [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7_1_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의
> 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는
> 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

> 패치를 롤백하려는 경우, [메타다운그레이드](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Installation.md#%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9Cmeta-downgrade)를 참고한다.

#### CM protocol Version

통신 프로토콜 버전은 변경되지 않았다.

#### Replication protocol Version

Replication 프로토콜 버전은 변경되지 않았다.

#### Sharding Version

샤딩 버전은 변경 되지 않았다.

> 알티베이스 샤딩 프로토콜 및 메타는 상위, 하위 호환성을 보장하지
> 않는다. 즉, 샤딩 버전이 다른 경우, 재구성해야 한다. 샤딩 설정은 [Altibase Sharding 설치와 설정](<https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Sharding.md#2altibase-sharding-%EC%84%A4%EC%B9%98%EC%99%80-%EC%84%A4%EC%A0%95>)을 참고한다.

### 프로퍼티

추가/변경/삭제된 프로퍼티 없음

### 성능 뷰

추가/변경/삭제된 성능뷰 없음