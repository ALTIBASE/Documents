<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Altibase 7.1.0.2.3 Patch Notes](#altibase-71023-patch-notes)
  - [New Features](#new-features)
    - [BUG-46837  Replication이 Drop된 receiver 에 Sender가 접속을 시도하면 출력되는 에러메시지 개선](#bug-46837-replication%EC%9D%B4-drop%EB%90%9C-receiver-%EC%97%90-sender%EA%B0%80-%EC%A0%91%EC%86%8D%EC%9D%84-%EC%8B%9C%EB%8F%84%ED%95%98%EB%A9%B4-%EC%B6%9C%EB%A0%A5%EB%90%98%EB%8A%94-%EC%97%90%EB%9F%AC%EB%A9%94%EC%8B%9C%EC%A7%80-%EA%B0%9C%EC%84%A0)
    - [BUG-46866 쿼리 수행 성능 개선을 위한 기능 추가](#bug-46866-%EC%BF%BC%EB%A6%AC-%EC%88%98%ED%96%89-%EC%84%B1%EB%8A%A5-%EA%B0%9C%EC%84%A0%EC%9D%84-%EC%9C%84%ED%95%9C-%EA%B8%B0%EB%8A%A5-%EC%B6%94%EA%B0%80)
    - [BUG-46882 QUEUE생성 시 tablespace를 지정할 수 있어야합니다.](#bug-46882-queue%EC%83%9D%EC%84%B1-%EC%8B%9C-tablespace%EB%A5%BC-%EC%A7%80%EC%A0%95%ED%95%A0-%EC%88%98-%EC%9E%88%EC%96%B4%EC%95%BC%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-46883 anonymous block 지원](#bug-46883anonymous-block-%EC%A7%80%EC%9B%90)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-46529 REPLICATION\_DDL\_ENABLE 옵션에 따라 REPLICATION\_DDL\_ENABLE\_LEVEL 관련 에러 메세지가 틀리게 출력됩니다.](#bug-46529replication%5C_ddl%5C_enable-%EC%98%B5%EC%85%98%EC%97%90-%EB%94%B0%EB%9D%BC-replication%5C_ddl%5C_enable%5C_level-%EA%B4%80%EB%A0%A8-%EC%97%90%EB%9F%AC-%EB%A9%94%EC%84%B8%EC%A7%80%EA%B0%80-%ED%8B%80%EB%A6%AC%EA%B2%8C-%EC%B6%9C%EB%A0%A5%EB%90%A9%EB%8B%88%EB%8B%A4)
    - [BUG-46661 이중화 걸린 테이블에 Online DDL 수행 시 간헐적으로 Receiver data conflict 발생](#bug-46661%EC%9D%B4%EC%A4%91%ED%99%94-%EA%B1%B8%EB%A6%B0-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90-online-ddl-%EC%88%98%ED%96%89-%EC%8B%9C-%EA%B0%84%ED%97%90%EC%A0%81%EC%9C%BC%EB%A1%9C-receiver-data-conflict-%EB%B0%9C%EC%83%9D)
    - [BUG-46803 Hostname 으로 발급된 라이센스 사용 시 간헐적 서버 시작 실패](#bug-46803hostname-%EC%9C%BC%EB%A1%9C-%EB%B0%9C%EA%B8%89%EB%90%9C-%EB%9D%BC%EC%9D%B4%EC%84%BC%EC%8A%A4-%EC%82%AC%EC%9A%A9-%EC%8B%9C-%EA%B0%84%ED%97%90%EC%A0%81-%EC%84%9C%EB%B2%84-%EC%8B%9C%EC%9E%91-%EC%8B%A4%ED%8C%A8)
    - [BUG-46804 IPCDA simple query가 실행될 때 execute success 통계정보가 카운트 되지 않습니다.](#bug-46804ipcda-simple-query%EA%B0%80-%EC%8B%A4%ED%96%89%EB%90%A0-%EB%95%8C-execute-success-%ED%86%B5%EA%B3%84%EC%A0%95%EB%B3%B4%EA%B0%80-%EC%B9%B4%EC%9A%B4%ED%8A%B8-%EB%90%98%EC%A7%80-%EC%95%8A%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-46885 CLI 함수에 NULL handle이 전달되었을 때 Segmentation fault가 발생합니다.](#bug-46885cli-%ED%95%A8%EC%88%98%EC%97%90-null-handle%EC%9D%B4-%EC%A0%84%EB%8B%AC%EB%90%98%EC%97%88%EC%9D%84-%EB%95%8C-segmentation-fault%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-46889 SQLFetch() 전에 LOB 함수를 호출하면 Segmentation fault가 발생합니다.](#bug-46889sqlfetch-%EC%A0%84%EC%97%90-lob-%ED%95%A8%EC%88%98%EB%A5%BC-%ED%98%B8%EC%B6%9C%ED%95%98%EB%A9%B4-segmentation-fault%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-46890 legacy statement 생성 실패로 인한 assert 발생시 추가적인 정보를 남겨야 합니다](#bug-46890legacy-statement-%EC%83%9D%EC%84%B1-%EC%8B%A4%ED%8C%A8%EB%A1%9C-%EC%9D%B8%ED%95%9C-assert-%EB%B0%9C%EC%83%9D%EC%8B%9C-%EC%B6%94%EA%B0%80%EC%A0%81%EC%9D%B8-%EC%A0%95%EB%B3%B4%EB%A5%BC-%EB%82%A8%EA%B2%A8%EC%95%BC-%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-46891 replication sync중 conflict 발생으로 데이터가 불일치하는 경우에도 Success로 처리되는 문제가 있습니다.](#bug-46891replication-sync%EC%A4%91-conflict-%EB%B0%9C%EC%83%9D%EC%9C%BC%EB%A1%9C-%EB%8D%B0%EC%9D%B4%ED%84%B0%EA%B0%80-%EB%B6%88%EC%9D%BC%EC%B9%98%ED%95%98%EB%8A%94-%EA%B2%BD%EC%9A%B0%EC%97%90%EB%8F%84-success%EB%A1%9C-%EC%B2%98%EB%A6%AC%EB%90%98%EB%8A%94-%EB%AC%B8%EC%A0%9C%EA%B0%80-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-46893 aix용 PICL에서 SWAP\_FREE의 값이 kB 단위여야 합니다](#bug-46893aix%EC%9A%A9-picl%EC%97%90%EC%84%9C-swap%5C_free%EC%9D%98-%EA%B0%92%EC%9D%B4-kb-%EB%8B%A8%EC%9C%84%EC%97%AC%EC%95%BC-%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-46903 Administrator 매뉴얼 "매체복구 사례 4" 복구 절차 수정](#bug-46903administrator-%EB%A7%A4%EB%89%B4%EC%96%BC-%EB%A7%A4%EC%B2%B4%EB%B3%B5%EA%B5%AC-%EC%82%AC%EB%A1%80-4-%EB%B3%B5%EA%B5%AC-%EC%A0%88%EC%B0%A8-%EC%88%98%EC%A0%95)
    - [BUG-46910 replication Sync중 데이타가 추가되거나 삭제될 경우, 실제로는 Sync 성공하였는데도 실패로 처리되는 문제가 있습니다.](#bug-46910replication-sync%EC%A4%91-%EB%8D%B0%EC%9D%B4%ED%83%80%EA%B0%80-%EC%B6%94%EA%B0%80%EB%90%98%EA%B1%B0%EB%82%98-%EC%82%AD%EC%A0%9C%EB%90%A0-%EA%B2%BD%EC%9A%B0-%EC%8B%A4%EC%A0%9C%EB%A1%9C%EB%8A%94-sync-%EC%84%B1%EA%B3%B5%ED%95%98%EC%98%80%EB%8A%94%EB%8D%B0%EB%8F%84-%EC%8B%A4%ED%8C%A8%EB%A1%9C-%EC%B2%98%EB%A6%AC%EB%90%98%EB%8A%94-%EB%AC%B8%EC%A0%9C%EA%B0%80-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Altibase 7.1.0.2.3 Patch Notes
==============================

New Features
------------

### BUG-46837  Replication이 Drop된 receiver 에 Sender가 접속을 시도하면 출력되는 에러메시지 개선

- **module** : dm

- **Category** : Other

- **재현 빈도** : Always

- **증상** : 이중화를 drop시킨 receiver에 이중화 sender 접속을
  시도하면 정보가 표시 되지 않아 어디서 접속했는지 알수 없습니다.

  receiver initialize 실패시 접속을 시도한 sender의 ip, port,
  replication name을 표시하도록 수정하였습니다.

- **재현 방법**

  -   **재현 절차**

  -   **수행 결과**

  -   **예상 결과**

- **Workaround**

- **변경사항**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

### BUG-46866 쿼리 수행 성능 개선을 위한 기능 추가

- **module** : qp-select-execute

- **Category** : Enhancement

- **재현 빈도** : Always

- **증상** : serial filter 의 적용으로 쿼리 수행 성능을 개선할 수
  있습니다. SERIAL\_FILTER 힌트 및 SERIAL\_EXECUTE\_MODE 프로퍼티가
  추가되었습니다.

- **재현 방법**

  - **재현 절차**

        alter session set explain plan=on;
        alter session set trclog_detail_predicate=1;
        create table t1 (i1 int, i2 int, i3 int);
        insert into values(1,1,1);
        insert into t1 values(1,1,1);
        insert into t1 values(2,2,2);
        insert into t1 values(3,3,3);
        select i1 from t1 where i1=2;
        select /*+ SERIAL_FILTER */ i1 from t1 where i1=2;

  -   **수행 결과**

  - **예상 결과**

        iSQL> select /*+ SERIAL_FILTER */ i1 from t1 where i1=2;
        I1
        --------------
        2
        1 row selected.
        ------------------------------------------------------------
        PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: BLOCKED )
         SCAN ( TABLE: SYS.T1, FULL SCAN, ACCESS: 3, COST: BLOCKED )
          [ FILTER SERIAL EXECUTE ]
          I1 = 2
        ------------------------------------------------------------

- **Workaround**

- **변경사항**

  - Performance view

  - Property

    -  추가

      - [SERIAL_EXECUTE_MODE](<https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_1.md#serial_execute_mode>)

        - 데이터 타입: Unsigned Integer

        - 기본값: 0

        - 속성: 변경가능, 단일 값

        - 값의 범위: [0,1]

        - 설명:  이 프로퍼티는 SCAN PLAN내 FILTER를 최적화하여 FILTER 수행 성능을 향상시킨다. 최적화 여부는 PLAN TREE에서 확인할 수 있다.

          0: 최적화하지 않음

          1: 최적화 함.

  - Compile Option

  - Error Code

### BUG-46882 QUEUE생성 시 tablespace를 지정할 수 있어야합니다.

-   **module** : qp

-   **Category** : Other

-   **재현 빈도** : Always

-   **증상** : QUEUE 생성시 tablespace를 지정하는 구문이 추가되었습니다.

- **재현 방법**

  -   **재현 절차**

          create queue q1(40) maxrows 100 tablespace sys_tbs_disk_data;

  -   **수행 결과**

          iSQL> create queue q1(40) maxrows 100 tablespace sys_tbs_disk_data;
          [ERR-31001 : SQL syntax error
          line 1: missing or invalid syntax
          create queue Q1(40) maxrows 100 tablespace sys_tbs_disk_data
                                          ^        ^
          ]

  - **예상 결과**

        iSQL> create queue q1(40) maxrows 100 tablespace sys_tbs_disk_data;
        Create success.

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-46883 anonymous block 지원

-   **module** : qp-psm-trigger-execute

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **증상** : Anonymous block을 지원합니다.

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

### BUG-46529 REPLICATION\_DDL\_ENABLE 옵션에 따라 REPLICATION\_DDL\_ENABLE\_LEVEL 관련 에러 메세지가 틀리게 출력됩니다.

- **module** : dm

- **Category** : Functional Error

- **재현 빈도** : Always

- **증상** : REPLICATION\_DDL\_ENABLE\_LEVEL 관련 에러메세지에 설정된
  프로퍼티값이 올바르게 출력되도록 수정하였습니다.

- **재현 방법**

  - **재현 절차**

        $T1> CREATE TABLE T1( i1 varchar(10) primary key, i2 varchar(10) )
                PARTITION BY RANGE( I1 )
                (
                     PARTITION p1 VALUES LESS THAN ('300'),
                     PARTITION p2 VALUES LESS THAN ('700'),
                     PARTITION p0 VALUES DEFAULT
                );
        Create success.
        $T1> CREATE REPLICATION REP1 WITH '${HOST_IP@DB2}',${ALTIBASE_REPLICATION_PORT_NO@DB2}
                       FROM SYS.T1 TO SYS.T1;
        Create success.

  - **수행 결과**

        $T1> ALTER TABLE SYS.T1 SPLIT PARTITION P2 AT ('500') INTO (PARTITION P3, PARTITION P2);
        [ERR-6117F : Cannot execute this DDL on a replicated table when the system property REPLICATION_DDL_ENABLE_LEVEL is 1.]

  - **예상 결과**

        $T1> ALTER TABLE SYS.T1 SPLIT PARTITION P2 AT ('500') INTO (PARTITION P3, PARTITION P2);
        [ERR-6117F : Cannot execute this DDL on a replicated table when the system property REPLICATION_DDL_ENABLE_LEVEL is 0.]

- **Workaround**

- **변경사항**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

### BUG-46661 이중화 걸린 테이블에 Online DDL 수행 시 간헐적으로 Receiver data conflict 발생

-   **module** : dm

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : 현상

    =============================================================

    이중화 걸린 테이블에 Online DDL 수행 시 간헐적으로 Receiver data
    conflict 발생하여

    재시작 전까지 이중화 간 데이터 불일치 발생.

    원인분석

    =============================================================

    DDL 로 인해 이중화 대상 테이블의 oid 가 변경되었는데 receiver 는
    이전 oid 를 가지고 있어 update 해당 데이터를 찾지 못함.

    해결방안

    =========================================

    DDL 수행시 Meta 테이블에 Lock 을 잡아 다른 스레드에서 접근할 수
    없도록 합니다.

    DDL 이 끝나면 Lock 이 풀리고 Receiver 가 다시 올라와 정상 동작
    합니다.

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

### BUG-46803 Hostname 으로 발급된 라이센스 사용 시 간헐적 서버 시작 실패

-   **module** : id

-   **Category** : Functional Error

-   **재현 빈도** : Frequence

-   **증상** : Hostname 으로 발급된 라이센스 사용 시 간헐적으로 서버
    시작 실패하는 문제가 있어, 수정하였습니다.

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

### BUG-46804 IPCDA simple query가 실행될 때 execute success 통계정보가 카운트 되지 않습니다.

-   **module** : mm-statement

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **증상** : IPCDA fast simple query execute시 통계 정보 추가

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

### BUG-46885 CLI 함수에 NULL handle이 전달되었을 때 Segmentation fault가 발생합니다.

- **module** : mm-cli

- **Category** : Fatal

- **재현 빈도** : Always

- **증상** : CLI 함수에 NULL handle이 전달되었을 때 Segmentation
  fault가 발생합니다.

  핸들 유효성을 검사하기 전에 핸들에 접근하기 때문이며 해당 부분
  수정하였습니다.

  SQLProcedureColumns

  SQLProcedures

  SQLSpecialColumns

  SQLStatistics

  SQLTablePrivileges

  SQLBulkOperations

  SQLCancel

  SQLSetPos

- **재현 방법**

  -   **재현 절차**

  -   **수행 결과**

  -   **예상 결과**

- **Workaround**

- **변경사항**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

### BUG-46889 SQLFetch() 전에 LOB 함수를 호출하면 Segmentation fault가 발생합니다.

-   **module** : mm-cli

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **증상** : Select 쿼리 수행시 SQLFetch()를 수행하지 않고
    SQLGetLob(), SQLGetLobLength()를 호출했을 때

    Segmentation fault 에러가 발생하는 문제를 수정하였습니다.

- **재현 방법**

  - **재현 절차**

        SQLPrepare()
        SQLExecute()
        Do not call SQLFetch()
        SQLGetLobLength()

  -   **수행 결과**

          FATAL Error

  -   **예상 결과**

          Raise Errors

-   **Workaround**

        Call SQLFetch()

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-46890 legacy statement 생성 실패로 인한 assert 발생시 추가적인 정보를 남겨야 합니다

-   **module** : sm\_transaction

-   **Category** : Assert

-   **재현 빈도** : Rare

-   **증상** : Tx의 statement간 연결 이상으로 Legacy Statement 생성 중
    assert가 발생할 경우

    추가적인 디버그 메시지를 추가하여 차후 분석을 용이하게 하도록
    합니다.

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

### BUG-46891 replication sync중 conflict 발생으로 데이터가 불일치하는 경우에도 Success로 처리되는 문제가 있습니다.

-   **module** : dm

-   **Category** : Other

-   **재현 빈도** : Always

-   **증상** : replication sync때 bulk insert 중 conflict 발생으로
    데이터가 불일치하는 경우에도 Success로 처리되는 문제가 있습니다.

    conflict를 제외한 데이터가 insert 성공한 경우 SUCCESS, 그렇지 않은
    경우에는 FAIL로 처리하도록 수정하였습니다.

    즉, 데이터가 일치하는 경우에는 SUCCESS , 불일치 하는 경우에는 FAIL
    로 처리하도록 수정하였습니다.

-   **재현 방법**

    -   **재현 절차**

            replication sync중 conflict 발생

    -   **수행 결과**

            일부 데이터가 insert 되지 않으나 sync success 된

    -   **예상 결과**

            sync 실패 처리 되어야 함

-   **Workaround**

        sync tuple count를 1로 변경

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-46893 aix용 PICL에서 SWAP\_FREE의 값이 kB 단위여야 합니다

-   **module** : ux-altiMon

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : AIX 용 altiMon 에서 SWAP\_FREE의 값이 kB 단위가 아니라
    bytes 단위로 출력되는 문제를 수정하였습니다.

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

### BUG-46903 Administrator 매뉴얼 "매체복구 사례 4" 복구 절차 수정

- **module** : sm

- **Category** : Manual

- **재현 빈도** : Always

- **증상** : Administrator 매뉴얼 "매체복구 사례 4" 복구 절차에 잘못된
  부분을 수정하고, 올바르게 동작하도록 변경하였습니다.

  UNTIL TIME 구문으로 복구를 수행할 때 사용자의 실수로 필요한 파일을
  누락하면, 사용자에게 로그가 연속되지 않았다는 사실을 알리고 UNTIL
  TIME 을 실패 시켜 잘못된 복구를 방지 합니다.

- **재현 방법**

  -   **재현 절차**

  -   **수행 결과**

  -   **예상 결과**

- **Workaround**

- **변경사항**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code
      -   추가
          -   437, smERR\_ABORT\_ERR\_LOG\_CONSISTENCY = Incomplete media
              recovery aborted due to log consistency failure. ( \<0%s\>
              ).</br>
               \# \*Cause: A log file has been lost. If Incomplete media
              recovery continues, data may be lost.</br>
               \# \*Action: Copy a valid log file to [LOG\_DIR] or move
              log files that are not needed for recovery to another
              directory.

### BUG-46910 replication Sync중 데이타가 추가되거나 삭제될 경우, 실제로는 Sync 성공하였는데도 실패로 처리되는 문제가 있습니다.

- **module** : dm

- **Category** : Other

- **재현 빈도** : Rare

- **증상** : Sync를 시작하는 동시에 Service로 데이타가 들어 올 경우 
  Sync할 table row 갯수가 잘못 계산 되어 실제로는 Sync가 성공하였으나
  추가 검증단계에서 실패 처리 되는 문제가 있었습니다.

  Sync 중에 에러 발생시 에러를 확인 할수 있으므로 Sync 완료 후 추가
  검증단계 부분은 제거 하였습니다.

- **재현 방법**

  -   **재현 절차**

  -   **수행 결과**

  -   **예상 결과**

- **Workaround**

- **변경사항**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

Changes
-------

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version | sharding version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- | ---------------- |
| 7.1.0.2.3        | 6.5.1                   | 8.7.1        | 7.1.6               | 7.4.4                        | 2.2.1            |

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

#### 추가된 프로퍼티

* [SERIAL_EXECUTE_MODE](<https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_1.md#serial_execute_mode>)

### 성능 뷰

추가/변경/삭제된 성능 뷰 없음
