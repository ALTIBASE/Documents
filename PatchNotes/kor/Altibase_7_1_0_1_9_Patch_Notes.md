<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Altibase 7.1.0.1.9 Patch Notes](#altibase-71019-patch-notes)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-45623 HBT에서 연결확인작업시 허용된 갯수 이상의 소켓을 사용하는 문제로 인해 에러가 발생합니다.(HP-UX)](#bug-45623hbt에서-연결확인작업시-허용된-갯수-이상의-소켓을-사용하는-문제로-인해-에러가-발생합니다hp-ux)
    - [BUG-46296 OTHER\_DATABASE\_SKIP\_ERROR 가 1일때 connection error가 발생하면 skip하지 않도록 수정](#bug-46296other_database_skip_error-가-1일때-connection-error가-발생하면-skip하지-않도록-수정)
    - [BUG-46453 STF(Service Time Failover) 수행시 AlternateServers가 설정되어 있지 않으면 ASSERT 에러가 발생합니다.](#bug-46453stfservice-time-failover-수행시-alternateservers가-설정되어-있지-않으면-assert-에러가-발생합니다)
    - [BUG-46593 PSM 호출시 host variable의 array size의 동일 여부를 확인하는 로직 추가](#bug-46593%C2%A0psm-%ED%98%B8%EC%B6%9C%EC%8B%9C-host-variable%EC%9D%98-array-size%EC%9D%98-%EB%8F%99%EC%9D%BC-%EC%97%AC%EB%B6%80%EB%A5%BC-%ED%99%95%EC%9D%B8%ED%95%98%EB%8A%94-%EB%A1%9C%EC%A7%81-%EC%B6%94%EA%B0%80)
    - [BUG-46596  data file open 시 실패했을 경우에 대비한 코드를 만들어야 합니다.](#bug-46596%C2%A0-data-file-open-%EC%8B%9C-%EC%8B%A4%ED%8C%A8%ED%96%88%EC%9D%84-%EA%B2%BD%EC%9A%B0%EC%97%90-%EB%8C%80%EB%B9%84%ED%95%9C-%EC%BD%94%EB%93%9C%EB%A5%BC-%EB%A7%8C%EB%93%A4%EC%96%B4%EC%95%BC-%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-46607 지원하지 않는 OS 에서 altiMon을 구동하려는 경우, PICL(platform information collection library) library file does not exist. 오류 발생](#bug-46607%C2%A0%EC%A7%80%EC%9B%90%ED%95%98%EC%A7%80-%EC%95%8A%EB%8A%94-os-%EC%97%90%EC%84%9C-altimon%EC%9D%84-%EA%B5%AC%EB%8F%99%ED%95%98%EB%A0%A4%EB%8A%94-%EA%B2%BD%EC%9A%B0-piclplatform-information-collection-library-library-file-does-not-exist-%EC%98%A4%EB%A5%98-%EB%B0%9C%EC%83%9D)
    - [BUG-46608 이중화 중 HBT error가 발생한 후 receiver쪽에Invalid protocol sequence error 가 발생합니다.](#bug-46608%C2%A0%EC%9D%B4%EC%A4%91%ED%99%94-%EC%A4%91-hbt-error%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%9C-%ED%9B%84-receiver%EC%AA%BD%EC%97%90invalid-protocol-sequence-error-%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-46620 AIX 7에서 altiMon 지원](#bug-46620%C2%A0aix-7%EC%97%90%EC%84%9C-altimon-%EC%A7%80%EC%9B%90)
    - [BUG-46625 IPCDA에서 host 변수에 matching 되는 컬럼이 없을 경우 비정상 종료하는 문제 수정](#bug-46625%C2%A0ipcda%EC%97%90%EC%84%9C-host-%EB%B3%80%EC%88%98%EC%97%90-matching-%EB%90%98%EB%8A%94-%EC%BB%AC%EB%9F%BC%EC%9D%B4-%EC%97%86%EC%9D%84-%EA%B2%BD%EC%9A%B0-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%98%EB%8A%94-%EB%AC%B8%EC%A0%9C-%EC%88%98%EC%A0%95)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Altibase 7.1.0.1.9 Patch Notes
==================

Fixed Bugs
----------

### BUG-45623 HBT에서 연결확인작업시 허용된 갯수 이상의 소켓을 사용하는 문제로 인해 에러가 발생합니다.(HP-UX)

-   **module** : pd

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **증상** : HBT가 이중화네트워크를 체크할때 altibase에서 사용 가능한
    소켓갯수 이상으로 소켓을 open하는 문제로 인해 에러가 발생하는 것을
    해결합니다.

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

### BUG-46296 OTHER\_DATABASE\_SKIP\_ERROR 가 1일때 connection error가 발생하면 skip하지 않도록 수정

-   **module** : rp-jdbcAdapter

-   **Category** : Other

-   **재현 빈도** : Always

-   **증상** : JDBC Adapter 에서 OTHER\_DATABASE\_SKIP\_ERROR 프로퍼티를
    1로 설정하면 모든 에러를 skip 하는데, connection error가 발생해도
    skip 하는 문제가 있습니다.

    또한, OraAdapter의 ORACLE\_SKIP\_ERROR 프로퍼티를 1로 설정하는 경우
    동일한 문제가 있습니다.

    이에, 아래의 에러가 발생한 경우만 skip 하고, 그외의 에러(연결이
    끊기거나 비정상 동작)에 대해서는 각 Adapter를 종료하도록
    수정하였습니다.

    "01B00":  Batch update exception occurred

    "23000": The row already exists in a unique index

    "HYT00": Client's query exceeded the execution time limit

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

### BUG-46453 STF(Service Time Failover) 수행시 AlternateServers가 설정되어 있지 않으면 ASSERT 에러가 발생합니다.

-   **module** : ul-odbc

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **증상** : SessionFailOver=on, AlternateServers를 설정하지 않은
    상태에서 STF(Service Time Failover) 수행시 assert 에러가 발생하는
    문제를 수정하였습니다.

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

### BUG-46593 PSM 호출시 host variable의 array size의 동일 여부를 확인하는 로직 추가

-   **module** : mm-apre

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : PSM(procedure, function) 호출시 array host variable는
    모두 같은 size로 호출되어야 합니다. 기존에는 동일한 size인지
    확인하는 로직이 누락되어 있어, 이를 수정하였습니다.

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

### BUG-46596  data file open 시 실패했을 경우에 대비한 코드를 만들어야 합니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Unknown

-   **증상** : 데이타파일을 오픈할때 실패해서 에러를 반환할 경우, 오픈
    실패의 이유가 디스크 공간 부족, 디스크립터 부족 등이면 성공할 때까지
    재시도하도록 수정합니다.

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

### BUG-46607 지원하지 않는 OS 에서 altiMon을 구동하려는 경우, PICL(platform information collection library) library file does not exist. 오류 발생

-   **module** : ux-altiMon

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **증상** : 지원하지 않는 OS 에서 altiMon을 구동하려는 경우, 지원하지
    않는 플랫폼이라는 에러메시지가 출력되도록 수정되었습니다.

     "PICL does not support this platform."

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

### BUG-46608 이중화 중 HBT error가 발생한 후 receiver쪽에Invalid protocol sequence error 가 발생합니다.

-   **module** : rp

-   **Category** : Other

-   **재현 빈도** : Rare

-   **증상** : 이중화 중 Sender에서 HBT에러로 인해 network 장애로 잘못
    판단 할 경우 Receiver에 Invalid protocol sequence 에러 발생하는 문제
    수정

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

### BUG-46620 AIX 7에서 altiMon 지원

-   **module** : ux-altiMon

-   **Category** : Portability

-   **재현 빈도** : Always

-   **증상** : AIX 7에서 altiMon 지원

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

### BUG-46625 IPCDA에서 host 변수에 matching 되는 컬럼이 없을 경우 비정상 종료하는 문제 수정

-   **module** : qp

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **증상** : IPCDA에서 host 변수에 matching 되는 컬럼이 없을 경우
    비정상 종료 하는 경우가 있어, 이를 수정하였습니다.

- **재현 방법**

  - **재현 절차**

        환경변수 설정
        export ISQL_CONNECTION=IPCDA
        export ALTIBASE_IPCDA_CHANNEL_COUNT=10
        export ALTIBASE_EXECUTOR_FAST_SIMPLE_QUERY=1
        
        drop table t1;
        CREATE TABLE T1(I1 INTEGER) ;
        INSERT INTO T1 VALUES(1);
        INSERT INTO T1 VALUES(2);
        INSERT INTO T1 VALUES(3);
         UPDATE T1 SET I1 = ?;

  -   **수행 결과**

          서버 비정상 종료

  - **예상 결과**

        iSQL>  UPDATE T1 SET I1 = ?;
         [ERR-31248 : Mismatched bind column count]

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
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: | :--------------: |
|    7.1.0.1.9     |          6.5.1          |    8.7.1     |        7.1.6        |            7.4.4             |      2.1.0       |

> Altibase 7.1 패치 버전별 히스토리는
> [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7_1_Version_Histories.md)
> 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의
> 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는
> 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

> 패치를 롤백하려는 경우,
> [메타다운그레이드](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Installation.md#%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9Cmeta-downgrade)를
> 참고한다.

#### CM protocol Version

통신 프로토콜 버전은 변경되지 않았다.

#### Replication protocol Version

Replication 프로토콜 버전은 변경되지 않았다..

#### Sharding Version

샤딩 버전은 변경 되지 않았다.

> 알티베이스 샤딩 프로토콜 및 메타는 상위, 하위 호환성을 보장하지
> 않는다. 즉, 샤딩 버전이 다른 경우, 재구성해야 한다.

### 프로퍼티

추가/변경/삭제된 프로퍼티 없음

### 성능 뷰

추가/변경/삭제된 성능뷰 없음
