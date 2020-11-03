<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Altibase 7.1.0.4.7 Patch Notes](#altibase-71047-patch-notes)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-48201  assert()가 AIX 7.2에서 동작하지 않습니다.](#bug-48201-assert%EA%B0%80-aix-72%EC%97%90%EC%84%9C-%EB%8F%99%EC%9E%91%ED%95%98%EC%A7%80-%EC%95%8A%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-48210  logging이 없는 commit 의 예외처리가 잘못된 부분이 있어 비정상 종료할 수 있습니다.](#bug-48210-logging%EC%9D%B4-%EC%97%86%EB%8A%94-commit-%EC%9D%98-%EC%98%88%EC%99%B8%EC%B2%98%EB%A6%AC%EA%B0%80-%EC%9E%98%EB%AA%BB%EB%90%9C-%EB%B6%80%EB%B6%84%EC%9D%B4-%EC%9E%88%EC%96%B4-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-48212  Lob Read할 때, Session Timeout 체크 추가](#bug-48212-lob-read%ED%95%A0-%EB%95%8C-session-timeout-%EC%B2%B4%ED%81%AC-%EC%B6%94%EA%B0%80)
    - [BUG-48224  v$plantext를 select 할때 graph 정보가 출력되면 비정상 종료 할 수 있습니다.](#bug-48224-vplantext%EB%A5%BC-select-%ED%95%A0%EB%95%8C-graph-%EC%A0%95%EB%B3%B4%EA%B0%80-%EC%B6%9C%EB%A0%A5%EB%90%98%EB%A9%B4-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C-%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-48226  Disk temp table merge sort 중에 Internal server error 발생](#bug-48226-disk-temp-table-merge-sort-%EC%A4%91%EC%97%90-internal-server-error-%EB%B0%9C%EC%83%9D)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Altibase 7.1.0.4.7 Patch Notes
==============================

Fixed Bugs
----------

### BUG-48201  assert()가 AIX 7.2에서 동작하지 않습니다.

-   **module** : id

-   **Category** : Hang

-   **재현 빈도** : Always

-   **증상** : AIX 7.2에서 시그널핸들러가 올바른 인자를 받지 못하여
    비정상종료가 되어야 하는 상황에서 HANG이 발생하는 문제를 해결합니다.

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

### BUG-48210  logging이 없는 commit 의 예외처리가 잘못된 부분이 있어 비정상 종료할 수 있습니다.

-   **module** : sm\_transaction

-   **Category** : Fatal

-   **재현 빈도** : Rare

-   **증상** : commit 실패에 대한 예외처리중 잘못된 곳이 있어서 수정합니다.

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

### BUG-48212  Lob Read할 때, Session Timeout 체크 추가

-   **module** : sm

-   **Category** : Hang

-   **재현 빈도** : Frequence

-   **증상** : Lob 탐색할 때, 세션이 타임아웃될 수 있도록 체크하는 코드를 추가

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

### BUG-48224  v$plantext를 select 할때 graph 정보가 출력되면 비정상 종료 할 수 있습니다.

-   **module** : qp-select

-   **Category** : Fatal

-   **재현 빈도** : Rare

-   **증상** : v\$plantext를  select 할때  graph 정보가 출력되면 비정상 종료 할 수 있는 문제를 수정하였습니다.

-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

        TRCLOG_EXPLAIN_GRAPH = 0

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48226  Disk temp table merge sort 중에 Internal server error 발생

-   **module** : sm-disk-collection

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : disk temp merge sort 에서 row size계산이 잘못되는 부분이 있어서 발생한 문제입니다.

- **재현 방법**

  -   **재현 절차**

          CREATE TABLE T1 ( I1 CHAR(495) ) tablespace sys_tbs_disk_data;
          CREATE TABLE T2 ( I1 CHAR(495) ) tablespace sys_tbs_disk_data;

          INSERT /*+APPEND*/ INTO T1 SELECT ROWNUM/5 FROM DUAL CONNECT BY LEVEL <= 1500;
          INSERT /*+APPEND*/ INTO T2 SELECT ROWNUM/5+1 FROM DUAL CONNECT BY LEVEL <= 1500;
          SELECT COUNT(*) FROM (SELECT /*+ USE_SORT(T1,T2)  */ T1.I1 FROM T1 JOIN T2 ON T1.I1=T2.I1 );
          DROP TABLE T1;
          DROP TABLE T2;

  - **수행 결과**

        iSQL> SELECT COUNT(*) FROM (SELECT /*+ USE_SORT(T1,T2)  */ T1.I1 FROM T1 JOIN T2 ON T1.I1=T2.I1 );
        [ERR-11069 : Internal server error in the storage manager ([FAILURE] ERR-0109E(error=16) Internal server error.)]

  -   **예상 결과**

          iSQL> SELECT COUNT(*) FROM (SELECT /*+ USE_SORT(T1,T2)  */ T1.I1 FROM T1 JOIN T2 ON T1.I1=T2.I1 );
          COUNT(*)
          -----------------------
          1495
          1 row selected.

-   **Workaround**

        1.
        TEMP_MAX_KEY_SIZE property를 문제가 발생하지 않는 값으로 변경한다.
        예를 들어 default 값인 512의 경우, temp value size 495 ~510 에서 문제가 발생한다.
        2. memory temp를 사용한다.

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
| 7.1.0.4.7        | 6.5.1                   | 8.9.1        | 7.1.7               | 7.4.6                        | 2.2.1            |

> Altibase 7.1 패치 버전별 히스토리는 [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7_1_Version_Histories.md)에서 확인할 수 있다.

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
> 않는다. 즉, 샤딩 버전이 다른 경우, 재구성해야 한다.

### 프로퍼티

추가/변경/삭제된 프로퍼티 없음

### 성능 뷰

추가/변경/삭제된 성능뷰 없음
