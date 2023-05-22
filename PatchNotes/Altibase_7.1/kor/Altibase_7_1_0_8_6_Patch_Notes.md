# Altibase 7.1.0.8.6 Patch Notes

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-50009  PICL 라이브러리에 예외상황 발생시 로그에 남기는 기능을 추가합니다. (Linux)](#bug-50009-picl-%EB%9D%BC%EC%9D%B4%EB%B8%8C%EB%9F%AC%EB%A6%AC%EC%97%90-%EC%98%88%EC%99%B8%EC%83%81%ED%99%A9-%EB%B0%9C%EC%83%9D%EC%8B%9C-%EB%A1%9C%EA%B7%B8%EC%97%90-%EB%82%A8%EA%B8%B0%EB%8A%94-%EA%B8%B0%EB%8A%A5%EC%9D%84-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4-linux)
    - [BUG-50259  aku -p start시 altibase에 admin mode로 접속하도록 수정합니다.](#bug-50259-aku--p-start%EC%8B%9C-altibase%EC%97%90-admin-mode%EB%A1%9C-%EC%A0%91%EC%86%8D%ED%95%98%EB%8F%84%EB%A1%9D-%EC%88%98%EC%A0%95%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50293  iSQL에 잘못된 사용자 아이디 또는 암호로 접속을 시도할때, "Invalid UserID or Password" 를 출력하도록 설정할 수 있습니다.](#bug-50293-isql%EC%97%90-%EC%9E%98%EB%AA%BB%EB%90%9C-%EC%82%AC%EC%9A%A9%EC%9E%90-%EC%95%84%EC%9D%B4%EB%94%94-%EB%98%90%EB%8A%94-%EC%95%94%ED%98%B8%EB%A1%9C-%EC%A0%91%EC%86%8D%EC%9D%84-%EC%8B%9C%EB%8F%84%ED%95%A0%EB%95%8C-invalid-userid-or-password-%EB%A5%BC-%EC%B6%9C%EB%A0%A5%ED%95%98%EB%8F%84%EB%A1%9D-%EC%84%A4%EC%A0%95%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-47333  외부프로시저에서 라이브러리 로딩에 실패한 다음, 실패의 원인을 해결해도 외부 프로시저 실행에 실패하는 문제가 있습니다.](#bug-47333-%EC%99%B8%EB%B6%80%ED%94%84%EB%A1%9C%EC%8B%9C%EC%A0%80%EC%97%90%EC%84%9C-%EB%9D%BC%EC%9D%B4%EB%B8%8C%EB%9F%AC%EB%A6%AC-%EB%A1%9C%EB%94%A9%EC%97%90-%EC%8B%A4%ED%8C%A8%ED%95%9C-%EB%8B%A4%EC%9D%8C-%EC%8B%A4%ED%8C%A8%EC%9D%98-%EC%9B%90%EC%9D%B8%EC%9D%84-%ED%95%B4%EA%B2%B0%ED%95%B4%EB%8F%84-%EC%99%B8%EB%B6%80-%ED%94%84%EB%A1%9C%EC%8B%9C%EC%A0%80-%EC%8B%A4%ED%96%89%EC%97%90-%EC%8B%A4%ED%8C%A8%ED%95%98%EB%8A%94-%EB%AC%B8%EC%A0%9C%EA%B0%80-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-47812  TRIGGER DDL간 동시성 문제로 비정상종료합니다.](#bug-47812-trigger-ddl%EA%B0%84-%EB%8F%99%EC%8B%9C%EC%84%B1-%EB%AC%B8%EC%A0%9C%EB%A1%9C-%EB%B9%84%EC%A0%95%EC%83%81%EC%A2%85%EB%A3%8C%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-48193  group by rollup 결과값이 다릅니다.](#bug-48193-group-by-rollup-%EA%B2%B0%EA%B3%BC%EA%B0%92%EC%9D%B4-%EB%8B%A4%EB%A6%85%EB%8B%88%EB%8B%A4)
    - [BUG-50072  메모리사용 통계정보 누락 가능성이 있습니다.](#bug-50072-%EB%A9%94%EB%AA%A8%EB%A6%AC%EC%82%AC%EC%9A%A9-%ED%86%B5%EA%B3%84%EC%A0%95%EB%B3%B4-%EB%88%84%EB%9D%BD-%EA%B0%80%EB%8A%A5%EC%84%B1%EC%9D%B4-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-50165  Loadbalance 가 ON일때 STF(Session Time Failover) 발생시, STF가 발생하기 전에 접속했던 서버로 재 접속 시도를 하지 않는 문제가 있습니다.](#bug-50165-loadbalance-%EA%B0%80-on%EC%9D%BC%EB%95%8C-stfsession-time-failover-%EB%B0%9C%EC%83%9D%EC%8B%9C-stf%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%98%EA%B8%B0-%EC%A0%84%EC%97%90-%EC%A0%91%EC%86%8D%ED%96%88%EB%8D%98-%EC%84%9C%EB%B2%84%EB%A1%9C-%EC%9E%AC-%EC%A0%91%EC%86%8D-%EC%8B%9C%EB%8F%84%EB%A5%BC-%ED%95%98%EC%A7%80-%EC%95%8A%EB%8A%94-%EB%AC%B8%EC%A0%9C%EA%B0%80-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-50241  APRE에서 INTO 구문 앞에 호스트 변수가 있는 경우 구조체 배열(row-wise binding)로 바인딩을 하지 못합니다.](#bug-50241-apre%EC%97%90%EC%84%9C-into-%EA%B5%AC%EB%AC%B8-%EC%95%9E%EC%97%90-%ED%98%B8%EC%8A%A4%ED%8A%B8-%EB%B3%80%EC%88%98%EA%B0%80-%EC%9E%88%EB%8A%94-%EA%B2%BD%EC%9A%B0-%EA%B5%AC%EC%A1%B0%EC%B2%B4-%EB%B0%B0%EC%97%B4row-wise-binding%EB%A1%9C-%EB%B0%94%EC%9D%B8%EB%94%A9%EC%9D%84-%ED%95%98%EC%A7%80-%EB%AA%BB%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50264  서버 부하 시 세션 관리자에서 동반 수행되는 특정 시스템 호출 지연으로, 기준 시간 갱신이 지연되어 UTRANS_TIMEOUT 이 발생합니다.](#bug-50264-%EC%84%9C%EB%B2%84-%EB%B6%80%ED%95%98-%EC%8B%9C-%EC%84%B8%EC%85%98-%EA%B4%80%EB%A6%AC%EC%9E%90%EC%97%90%EC%84%9C-%EB%8F%99%EB%B0%98-%EC%88%98%ED%96%89%EB%90%98%EB%8A%94-%ED%8A%B9%EC%A0%95-%EC%8B%9C%EC%8A%A4%ED%85%9C-%ED%98%B8%EC%B6%9C-%EC%A7%80%EC%97%B0%EC%9C%BC%EB%A1%9C-%EA%B8%B0%EC%A4%80-%EC%8B%9C%EA%B0%84-%EA%B0%B1%EC%8B%A0%EC%9D%B4-%EC%A7%80%EC%97%B0%EB%90%98%EC%96%B4-utrans_timeout-%EC%9D%B4-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50279  NULLIF, COALESCE, CASE2 함수의 인자로 사용자 정의 타입(User Defined Type)을 사용하는 경우, 서버가 비정상 종료할 수 있습니다.](#bug-50279-nullif-coalesce-case2-%ED%95%A8%EC%88%98%EC%9D%98-%EC%9D%B8%EC%9E%90%EB%A1%9C-%EC%82%AC%EC%9A%A9%EC%9E%90-%EC%A0%95%EC%9D%98-%ED%83%80%EC%9E%85user-defined-type%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94-%EA%B2%BD%EC%9A%B0-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-50009  PICL 라이브러리에 예외상황 발생시 로그에 남기는 기능을 추가합니다. (Linux)

-   **module** : ux-altiMon

-   **Category** : Usability

-   **재현 빈도** : Always

-   **설명** : OS를 모니터링하는 PICL 라이브러리에서 예외상황 발생시, 원인 파악을
    위해 예외 처리를 추가하고 altimon.log에 로그를 남기는 기능을
    추가했습니다. 이 기능은 리눅스만 지원합니다.

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

### BUG-50259  aku -p start시 altibase에 admin mode로 접속하도록 수정합니다.

-   **module** :

-   **Category** : Enhancement

-   **재현 빈도** : Always

- **설명** : aku 실행을 위해 ADMIN MODE가 추가되었습니다. 또한 마스터 파드의 경우 truncate 수행과 rep sync 받는 로직 및 rep reset 로직이 제거되었습니다.

  - DB admin mode 관련 aku 구현 내용

  -   aku -p start 시 altibase DB가 ADMIN\_MODE가 0으로 설정되어
    있으면 에러 출력 후 종료
  -   aku -p start 과정에 altibase DB에 admin mode로 접속하여 aku
      작업 수행
  -   aku -p start 정상 종료시 altibase DB를 ADMIN\_MODE 를 0으로
      설정 후 종료

   - 마스터 파드(pod-0)에서의 aku 처리 및 사용 가이드     

  * aku -p start 수행시

    마스터 파드인 경우, truncate 수행과 slave로부터 rep
    sync 받는 로직을 제거합니다.

  * aku -p end 수행시

    마스터 파드인 경우, 이중화 reset 로직을 제거합니다.

    이중화 reset을 수행하면, 더 이상 이중화 데이터를 주고받지 못하기 때문에,
       aku -p end에서 이중화 reset 수행 후 aku -p start 수행시에 기존 테이블을 truncate하고 rep sync 받아 와서 데이터를 동기화하는 과정이 필요했었습니다.
       그런데, aku -p end시 마스터 파드인 경우 이중화 reset을 하지 않으면,
       마스터 파드가 계속 이중화를 통해 데이터를 동기화하기 때문에, truncate 및 rep sync가 필요없습니다.

  * 마스터 파드가 아닌 일반 slave 파드인 경우, aku -p start와 aku
    -p end 의 수정 사항이 없어, 이전과 동일하게 동작합니다.

  > 주의사항

     1) altibase.properties의 ADMIN\_MODE = 1
  과 REMOTE\_SYSDBA\_ENABLE = 1 을 설정한 후, altibase DB를 구동해야
  합니다.

        2) 마스터 노드 장애시 사용자가 판단해서 수동으로 truncate, 다른
    파드로부터 rep sync 받기를 사용자가 직접 수행해야 합니다. (마스터 파드 이외의 파드에서는 aku 에서 자동으로 truncate 및 rep sync 받기를 수행합니다.)

  **수동 복구(sync) 후 에는 반드시 마스터 파드에서 등록된 이중화 중 임의의 한 이중화를 시작한 후(아래 예 참조)에 aku -p start를 수행해야 aku가 정상 동작합니다.**

  ```
  ALTER REPLICATION AKU_REP_01 START;
  ```

  위 과정 없이 aku -p start 시 다음 에러로 실패할 수 있습니다.

  ```
  [ERROR] The master pod is detected to have failed. Check and
  perform a manual recovery.
  ```

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

### BUG-50293  iSQL에 잘못된 사용자 아이디 또는 암호로 접속을 시도할때, "Invalid UserID or Password" 를 출력하도록 설정할 수 있습니다.

-   **module** : ux-isql

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : 보안을 강화하기 위해 iSQL에 잘못된 사용자 아이디 또는 암호로 접속을 시도할때, 상세한 접속 실패 이유를 표시하지 않도록 설정할 수 있습니다. ISQL_SECURE_LOGIN_MSG 프로퍼티를 1로 설정하면 사용자 아이디 또는 암호가 틀린경우, "Invalid UserID or Password" 라는 에러메시지가 출력됩니다. 이 프로퍼티를 0으로 설정하거나 환경변수를 설정하지 않으면, 기존과 동일하게 명확한 접속 실패 이유가 출력됩니다.

-   **재현 방법**
    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**
    -   Performance view
    -   Property
        -   ISQL_SECURE_LOGIN_MSG
            -   0: 명확한 접속 실패 이유를 출력.(기본값)
            -   1: 사용자 아이디 또는 암호가 틀린경우, "Invalid UserID or Password" 라는 에러메시지 출력.
    -   Compile Option
    -   Error Code

Fixed Bugs
==========

### BUG-47333  외부프로시저에서 라이브러리 로딩에 실패한 다음, 실패의 원인을 해결해도 외부 프로시저 실행에 실패하는 문제가 있습니다.

-   **module** : qp-psm-trigger-execute

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 외부 프로시저에서 라이브러리 로딩에 실패한 다음, 실패의 원인을 해결하더라도 외부 프로시저를 실행할 수 없는 문제를 수정합니다. 이 문제가 발생하면, 이 패치의 적용전의 경우 클라이언트를 재 접속하는 것으로 문제를 해결할 수 있었습니다. 이 패치의 적용으로 클라이언트의 재접속을 하지 않고도 문제를 해결할 수 있습니다.

- **재현 방법**

  -   **재현 절차**

          CREATE LIBRARY LIB1 AS 'andy_upper.so';
          CREATE PROCEDURE PROC1 ( istr in varchar(100), ostr out varchar(100) ) AS
          LANGUAGE C
          LIBRARY LIB1 NAME "andy_upper";
          /
          VAR VAR1 VARCHAR(100);
          VAR VAR2 VARCHAR(100);
          EXEC :VAR1 := 'aaaa';
          EXEC PROC1(:VAR1, :VAR2);
          CREATE OR REPLACE LIBRARY LIB1 AS 'invalid_library_name.so';
          EXEC PROC1(:VAR1, :VAR2);
          CREATE OR REPLACE LIBRARY LIB1 AS 'andy_upper.so';
          EXEC PROC1(:VAR1, :VAR2);

  - **수행 결과**

        iSQL> CREATE OR REPLACE LIBRARY LIB1 AS 'invalid_library_name.so'; //오류를 발생시키는 라이브러리로 변경
        Create success.
        iSQL> EXEC PROC1(:VAR1, :VAR2);
        [ERR-0109F : Library file for external procedure/function not found : ......./lib/invalid_library_name.so]

        iSQL> CREATE OR REPLACE LIBRARY LIB1 AS 'andy_upper.so'; //오류를 제거하여 정상동작하도록 수정
        Create success.
        iSQL> EXEC PROC1(:VAR1, :VAR2);
        [ERR-010A0 : Function for external procedure/function not found]

  -   **예상 결과**

          iSQL> CREATE OR REPLACE LIBRARY LIB1 AS 'invalid_library_name.so';//오류를 발생시키는 라이브러리로 변경
          Create success.
          iSQL> EXEC PROC1(:VAR1, :VAR2);
          [ERR-0109F : Library file for external procedure/function not found : ......./lib/invalid_library_name.so]

          iSQL> CREATE OR REPLACE LIBRARY LIB1 AS 'andy_upper.so'; //오류를 제거하여 정상동작하도록 수정
          Create success.
          iSQL> EXEC PROC1(:VAR1, :VAR2);
          Execute success.

-   **Workaround**

        Client 접속을 해제하고, 다시 접속한다.

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47812  TRIGGER DDL간 동시성 문제로 비정상종료합니다.

-   **module** : qp-psm-trigger-execute

-   **Category** : Fatal

-   **재현 빈도** : Frequence

-   **설명** : ALTER TRIGGER DDL과 DROP TRIGGER DDL에서 발생하는 동시성
    문제로 비정상종료합니다.

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

### BUG-48193  group by rollup 결과값이 다릅니다.

-   **module** : qp-select-pvo

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : group by rollup 결과값이 다른 문제를 수정합니다.

- **재현 방법**

  -   **재현 절차**

          drop table t1;
          drop table t2;
          create table t1 (i1 int, i2 int, i3 int, i4 int);
          create table t2 ( i1 int);
          insert into t1 values( 1,1,1,3);
          insert into t1 values( 2,2,2,4);
          insert into t2 values(1);
          select i1, max(i4), (select min(i1) from t2 where i1 = t1.i1) as sub from t1 group by rollup(i1);

  - **수행 결과**

        I1          MAX(I4)     SUB
        ----------------------------------------
        1           3           1
        2           4           1
                    4           1
        3 rows selected.

  -   **예상 결과**

          I1          MAX(I4)     SUB
          ----------------------------------------
          1           3           1
          2           4
                      4
          3 rows selected.

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50072  메모리사용 통계정보 누락 가능성이 있습니다.

-   **module** : id

-   **Category** : Maintainability

-   **재현 빈도** : Unknown

-   **설명** : v$memstat에 관련된 메모리관리의 통계정보를 관리하는 로직에 통계값의 누락이 발생할 가능성이 있는 코드가 있어서 그에 대해 수정합니다. 통계정보 누락이 발생하면 altibase_boot.log에 로그를 남기도록 개선하였습니다.

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

### BUG-50165  Loadbalance 가 ON일때 STF(Session Time Failover) 발생시, STF가 발생하기 전에 접속했던 서버로 재 접속 시도를 하지 않는 문제가 있습니다.

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : Loadbalance 가 ON일때 STF(Session Time Failover) 발생시, STF가 발생하기 전에 접속했던 서버로 재 접속을 하지 않고, 기본 서버로 접속하는 문제가 있습니다. 이 문제를 해결하면서 다음과 같이 동작이 변경되었습니다.

    -   Loadbalance 가 ON이면, 최초로 접속을 시도할 서버는 기본 서버와 AlternateServer 중에서 랜덤으로 선택하여 접속한다. session time failover 발생 시엔 기존 접속했던 서버에 다시 접속을 시도해보고 실패할 경우 랜덤하게 접속을 시도한다.

    -   Loadbalance가 OFF이면, 최초 접속 시에는 기본 서버에 접속을 시도하고, 접속에 실패하면 AlternateServer로 지정된 서버에 순서대로 접속을 시도한다. session time failover 발생 시엔 기존 접속했던 서버에 다시 접속을 시도해보고 실패할 경우 순서대로 접속을 시도한다.

- **재현 방법**

  - **재현 절차**

        loadbalance=on, sessionfailover=on
        Primary Server - A
        AlternateServers  - ( B, C, D )
        1. Connect ==> C가 랜덤하게 선택됨
        2. Prepare ==> C서버에서 STF발생

  -   **수행 결과**

          A 서버로 접속 시도 -> 나머지 서버 랜덤으로 시도

  -   **예상 결과**

          C 서버로 접속 시도 -> 나머지 서버 랜덤으로 시도

- **Workaround**

- **변경사항**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

### BUG-50241  APRE에서 INTO 구문 앞에 호스트 변수가 있는 경우 구조체 배열(row-wise binding)로 바인딩을 하지 못합니다.

-   **module** : mm-apre

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 구조체 배열 호스트 변수가 SQL 구문 내 첫번째 호스트
    변수가 아닐때 row-wise 바인딩을 제대로 못하는 문제를 수정하였습니다.

- **재현 방법**

  -   **재현 절차**

          $ALTIBASE_HOME/sample/APRE/arrays2.sc
              /* use structure array host variables : row wise */    
              s_dno = 2000;                                          
              EXEC SQL SELECT * INTO :a_department                   
                       FROM DEPARTMENTS WHERE DNO < :s_dno;          
              ==> 쿼리를 변경
              EXEC SQL WITH NEWDEPARTMENT AS                       
                  (                                                
                      SELECT * FROM DEPARTMENTS WHERE DNO < :s_dno
                  )                                                
                  SELECT * INTO :a_department FROM NEWDEPARTMENT;

  - **수행 결과**

        ------------------------------------------------------------------
        [Structure Array Host Variables With Select]
        ------------------------------------------------------------------
        DNO      DNAME                          DEP_LOCATION       MGR_NO
        ------------------------------------------------------------------
            544826734CH DEVELOPMENT DEPT 1    RESEARCH DEVELOPSydney
        13               32596
        1      �~�T    0

  -   **예상 결과**

          ------------------------------------------------------------------
          [Structure Array Host Variables With Select]
          ------------------------------------------------------------------
          DNO      DNAME                          DEP_LOCATION       MGR_NO
          ------------------------------------------------------------------
          1001     RESEARCH DEVELOPMENT DEPT 1    New York           16
          1002     RESEARCH DEVELOPMENT DEPT 2    Sydney             13
          1003     SOLUTION DEVELOPMENT DEPT      Osaka              14
          3 rows selected

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50264  서버 부하 시 세션 관리자에서 동반 수행되는 특정 시스템 호출 지연으로, 기준 시간 갱신이 지연되어 UTRANS_TIMEOUT 이 발생합니다.

기준시간을 관리하는 세션 관리자에서

-   **module** : mm
-   **Category** : Functional Error
-   **재현 빈도** : Frequence
-   **설명** : 서버 부하 시 세션 관리자에서 관리하는 기준 시간(base time) 갱신이 지연되는 문제가 있어, UTRANS_TIMEOUT이 발생합니다. 세션 관리자에서 지연을 유발하는 시스템 호출을 별도의 쓰레드로 분리하여 기준 시간 갱신이 지연되지 않도록 수정합니다.
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

### BUG-50279  NULLIF, COALESCE, CASE2 함수의 인자로 사용자 정의 타입(User Defined Type)을 사용하는 경우, 서버가 비정상 종료할 수 있습니다.

-   **module** : mt-function

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : NULLIF, COALESCE, CASE2 함수의 인자로 사용자 정의 타입(User Defined Type)을 사용하는 경우, 서버가 비정상 종료하는 문제를 수정합니다.

- **재현 방법**

  -   **재현 절차**

          create or replace procedure proc1
          as
           type aa_type is table of integer;
           var1 aa_type;
           var2 varchar(128);
          begin
            var1 := nullif(var1, var1);
          end;
          /
          exec proc1;

  - **수행 결과**

        [ERR-91015 : Communication failure.]

  -   **예상 결과**

          [ERR-2100C : Conversion not applicable.
          In PROC1
          0007 :   var1 := nullif(var1, var1);
                          ^            ^
          ]

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
| 7.1.0.8.6        | 6.5.1                   | 8.11.1       | 7.1.7               | 7.4.7                        |

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

> 알티베이스 샤딩 프로토콜 및 메타는 상위, 하위 호환성을 보장하지
> 않는다. 즉, 샤딩 버전이 다른 경우, 재구성해야 한다.

### 프로퍼티

#### 추가된 프로퍼티

#### 변경된 프로퍼티

#### 삭제된 프로퍼티

### 성능 뷰

#### 추가된 성능 뷰

#### 변경된 성능 뷰

#### 삭제된 성능 뷰
