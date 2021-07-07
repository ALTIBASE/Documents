<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Altibase 7.1.0.2.6 Patch Notes](#altibase-71026-patch-notes)
  - [New Features](#new-features)
    - [BUG-46824  APRE에 anonymous block을 지원해야 합니다.](#bug-46824-apre%EC%97%90-anonymous-block%EC%9D%84-%EC%A7%80%EC%9B%90%ED%95%B4%EC%95%BC-%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-46887  dbms_metadata 패키지 지원](#bug-46887-dbms_metadata-%ED%8C%A8%ED%82%A4%EC%A7%80-%EC%A7%80%EC%9B%90)
    - [BUG-46922  Percentile_Cont , Percentile_Disc 함수의 메모리 재사용 기능 향상](#bug-46922-percentile_cont--percentile_disc-%ED%95%A8%EC%88%98%EC%9D%98-%EB%A9%94%EB%AA%A8%EB%A6%AC-%EC%9E%AC%EC%82%AC%EC%9A%A9-%EA%B8%B0%EB%8A%A5-%ED%96%A5%EC%83%81)
    - [BUG-47082  메모리 인덱스 VALUE BASE BOTTOM-UP 빌드 성능 향상](#bug-47082-%EB%A9%94%EB%AA%A8%EB%A6%AC-%EC%9D%B8%EB%8D%B1%EC%8A%A4-value-base-bottom-up-%EB%B9%8C%EB%93%9C-%EC%84%B1%EB%8A%A5-%ED%96%A5%EC%83%81)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-46409  Alter replication set 구문 중 meta 초기화가 안된 구문이 있습니다.](#bug-46409-alter-replication-set-%EA%B5%AC%EB%AC%B8-%EC%A4%91-meta-%EC%B4%88%EA%B8%B0%ED%99%94%EA%B0%80-%EC%95%88%EB%90%9C-%EA%B5%AC%EB%AC%B8%EC%9D%B4-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-46783  이중화 중 DDL 수행 시 receiver 가 종료할 경우 이미 free 된 이중화 이름을 복사 할 수 있습니다.](#bug-46783-%EC%9D%B4%EC%A4%91%ED%99%94-%EC%A4%91-ddl-%EC%88%98%ED%96%89-%EC%8B%9C-receiver-%EA%B0%80-%EC%A2%85%EB%A3%8C%ED%95%A0-%EA%B2%BD%EC%9A%B0-%EC%9D%B4%EB%AF%B8-free-%EB%90%9C-%EC%9D%B4%EC%A4%91%ED%99%94-%EC%9D%B4%EB%A6%84%EC%9D%84-%EB%B3%B5%EC%82%AC-%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-46879  OpenJDK11 에서 jdbcAdapter 구동 실패 수정](#bug-46879-openjdk11-%EC%97%90%EC%84%9C-jdbcadapter-%EA%B5%AC%EB%8F%99-%EC%8B%A4%ED%8C%A8-%EC%88%98%EC%A0%95)
    - [BUG-47090  AIX, HP 장비에서 sysdba로 remote 접속을 막는 기능이 제대로 동작하지 않습니다.](#bug-47090-aix-hp-%EC%9E%A5%EB%B9%84%EC%97%90%EC%84%9C-sysdba%EB%A1%9C-remote-%EC%A0%91%EC%86%8D%EC%9D%84-%EB%A7%89%EB%8A%94-%EA%B8%B0%EB%8A%A5%EC%9D%B4-%EC%A0%9C%EB%8C%80%EB%A1%9C-%EB%8F%99%EC%9E%91%ED%95%98%EC%A7%80-%EC%95%8A%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-47095  partition simple query 수행 시, 메모리 초기화 누락](#bug-47095-partition-simple-query-%EC%88%98%ED%96%89-%EC%8B%9C-%EB%A9%94%EB%AA%A8%EB%A6%AC-%EC%B4%88%EA%B8%B0%ED%99%94-%EB%88%84%EB%9D%BD)
    - [BUG-47105  cpu 정보를 가져올 때 on-line 인지 off-line 인지 체크하지 않아, 서버가 boot 과정에서 실패할 수 있습니다.](#bug-47105-cpu-%EC%A0%95%EB%B3%B4%EB%A5%BC-%EA%B0%80%EC%A0%B8%EC%98%AC-%EB%95%8C-on-line-%EC%9D%B8%EC%A7%80-off-line-%EC%9D%B8%EC%A7%80-%EC%B2%B4%ED%81%AC%ED%95%98%EC%A7%80-%EC%95%8A%EC%95%84-%EC%84%9C%EB%B2%84%EA%B0%80-boot-%EA%B3%BC%EC%A0%95%EC%97%90%EC%84%9C-%EC%8B%A4%ED%8C%A8%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-47115  OpenJDK11 환경에서 jdbcAdapter 테스트 수행시, StackOverflowError가 발생하는 문제 수정](#bug-47115-openjdk11-%ED%99%98%EA%B2%BD%EC%97%90%EC%84%9C-jdbcadapter-%ED%85%8C%EC%8A%A4%ED%8A%B8-%EC%88%98%ED%96%89%EC%8B%9C-stackoverflowerror%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%98%EB%8A%94-%EB%AC%B8%EC%A0%9C-%EC%88%98%EC%A0%95)
    - [BUG-47119  이중화 접속시 sendHandshakeAck 를 보낼 때 패킷 계산이 잘못되어 메모리를 긁을 수 있습니다.](#bug-47119-%EC%9D%B4%EC%A4%91%ED%99%94-%EC%A0%91%EC%86%8D%EC%8B%9C-sendhandshakeack-%EB%A5%BC-%EB%B3%B4%EB%82%BC-%EB%95%8C-%ED%8C%A8%ED%82%B7-%EA%B3%84%EC%82%B0%EC%9D%B4-%EC%9E%98%EB%AA%BB%EB%90%98%EC%96%B4-%EB%A9%94%EB%AA%A8%EB%A6%AC%EB%A5%BC-%EA%B8%81%EC%9D%84-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-47121  jdbcAdapter conf 파일에 OTHER\_DATABASE\_JDBC\_MAX\_HEAP\_SIZE 가 설정이 되지 않는 문제가 있습니다.](#bug-47121-jdbcadapter-conf-%ED%8C%8C%EC%9D%BC%EC%97%90-other%5C_database%5C_jdbc%5C_max%5C_heap%5C_size-%EA%B0%80-%EC%84%A4%EC%A0%95%EC%9D%B4-%EB%90%98%EC%A7%80-%EC%95%8A%EB%8A%94-%EB%AC%B8%EC%A0%9C%EA%B0%80-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-47126  호스트 변수에 길이가 긴 값을 할당하면 segment fault 발생합니다](#bug-47126-%ED%98%B8%EC%8A%A4%ED%8A%B8-%EB%B3%80%EC%88%98%EC%97%90-%EA%B8%B8%EC%9D%B4%EA%B0%80-%EA%B8%B4-%EA%B0%92%EC%9D%84-%ED%95%A0%EB%8B%B9%ED%95%98%EB%A9%B4-segment-fault-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-47128  Query rebuild시 query\_binding memory가 지속적으로 증가할 수 있습니다.](#bug-47128-query-rebuild%EC%8B%9C-query%5C_binding-memory%EA%B0%80-%EC%A7%80%EC%86%8D%EC%A0%81%EC%9C%BC%EB%A1%9C-%EC%A6%9D%EA%B0%80%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-47135  OpenJDK에서 실행시 jvm 생성이 안 됩니다](#bug-47135-openjdk%EC%97%90%EC%84%9C-%EC%8B%A4%ED%96%89%EC%8B%9C-jvm-%EC%83%9D%EC%84%B1%EC%9D%B4-%EC%95%88-%EB%90%A9%EB%8B%88%EB%8B%A4)
    - [BUG-47136  alter tablespace swap시, 테이블 스페이스 사용량를 계산하는 로직 오류 수정](#bug-47136-alter-tablespace-swap%EC%8B%9C-%ED%85%8C%EC%9D%B4%EB%B8%94-%EC%8A%A4%ED%8E%98%EC%9D%B4%EC%8A%A4-%EC%82%AC%EC%9A%A9%EB%9F%89%EB%A5%BC-%EA%B3%84%EC%82%B0%ED%95%98%EB%8A%94-%EB%A1%9C%EC%A7%81-%EC%98%A4%EB%A5%98-%EC%88%98%EC%A0%95)
    - [BUG-47140  하위버전과 이중화시 해시 파티션드 테이블의 파티션 개수가 같은 경우에도 이중화 실패가 발생할수 있습니다.](#bug-47140-%ED%95%98%EC%9C%84%EB%B2%84%EC%A0%84%EA%B3%BC-%EC%9D%B4%EC%A4%91%ED%99%94%EC%8B%9C-%ED%95%B4%EC%8B%9C-%ED%8C%8C%ED%8B%B0%EC%85%98%EB%93%9C-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%9D%98-%ED%8C%8C%ED%8B%B0%EC%85%98-%EA%B0%9C%EC%88%98%EA%B0%80-%EA%B0%99%EC%9D%80-%EA%B2%BD%EC%9A%B0%EC%97%90%EB%8F%84-%EC%9D%B4%EC%A4%91%ED%99%94-%EC%8B%A4%ED%8C%A8%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A0%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-47142  BLOB컬럼과 DECIMAL 컬럼을 포함한 테이블에서 첫번째 컬럼의 타입이 BLOB 이고, HASH 조인을 할 경우 에러가 발생합니다.](#bug-47142-blob%EC%BB%AC%EB%9F%BC%EA%B3%BC-decimal-%EC%BB%AC%EB%9F%BC%EC%9D%84-%ED%8F%AC%ED%95%A8%ED%95%9C-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90%EC%84%9C-%EC%B2%AB%EB%B2%88%EC%A7%B8-%EC%BB%AC%EB%9F%BC%EC%9D%98-%ED%83%80%EC%9E%85%EC%9D%B4-blob-%EC%9D%B4%EA%B3%A0-hash-%EC%A1%B0%EC%9D%B8%EC%9D%84-%ED%95%A0-%EA%B2%BD%EC%9A%B0-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-47173  host variable precision이 컬럼 size보다 큰 경우 simple query 수행 시 에러처리 되는 것을 개선해야합니다.](#bug-47173-host-variable-precision%EC%9D%B4-%EC%BB%AC%EB%9F%BC-size%EB%B3%B4%EB%8B%A4-%ED%81%B0-%EA%B2%BD%EC%9A%B0-simple-query-%EC%88%98%ED%96%89-%EC%8B%9C-%EC%97%90%EB%9F%AC%EC%B2%98%EB%A6%AC-%EB%90%98%EB%8A%94-%EA%B2%83%EC%9D%84-%EA%B0%9C%EC%84%A0%ED%95%B4%EC%95%BC%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-47195  PARTITION SWAP 후 비정상종료시 재구동 실패.](#bug-47195-partition-swap-%ED%9B%84-%EB%B9%84%EC%A0%95%EC%83%81%EC%A2%85%EB%A3%8C%EC%8B%9C-%EC%9E%AC%EA%B5%AC%EB%8F%99-%EC%8B%A4%ED%8C%A8)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Altibase 7.1.0.2.6 Patch Notes
==============================

New Features
------------

### BUG-46824  APRE에 anonymous block을 지원해야 합니다.

-   **module** : mm-apre

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **증상** : APRE에서 anonymous block 을 지원하도록 개선되었습니다.

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

### BUG-46887  dbms_metadata 패키지 지원

-   **module** : ut

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **증상** : [DBMS\_METADATA](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/StoredProcedure2.md#dbms_metadata) 패키지 지원으로, 서버에서 DB객체의 DDL을 조회할 수 있는 기능을 제공합니다. $ALTIBASE_HOME/packages 아래에 dbms_metadata.sql, dbms_metadata.plb로 제공합니다.

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

### BUG-46922  Percentile_Cont , Percentile_Disc 함수의 메모리 재사용 기능 향상

-   **module** : mt-function

-   **Category** : Efficiency

-   **재현 빈도** : Always

-   **증상** : Percentile_Cont , Percentile_Disc 함수의 메모리 재사용 기능이 향상되었습니다.

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

### BUG-47082  메모리 인덱스 VALUE BASE BOTTOM-UP 빌드 성능 향상

- **module** : sm-mem-index

- **Category** : Enhancement

- **재현 빈도** : Always

- **증상** : 메모리 인덱스의 VALUE BASE BOTTOM-UP 빌드 속도를 향상시켰습니다.

  이로 인해 STARTUP시 VALUE BASE 인덱스 생성속도도 향상되었으며, VALUE BASE 인덱스 생성 중 추가로 요구되는 메모리 사이즈가 절반으로 줄었습니다.

- **재현 방법**

  -   **재현 절차**

  -   **수행 결과**

  -   **예상 결과**

- **Workaround**

- **변경사항**

  -   Performance view
  -   Property
      -   변경
          -   [MEMORY_INDEX_BUILD_RUN_SIZE](<https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_1.md#memory_index_build_run_size-%EB%8B%A8%EC%9C%84--%EB%B0%94%EC%9D%B4%ED%8A%B8>)의 디폴트값을 변경합니다.
              -   32768 -> 131072

  -   Compile Option
  -   Error Code

Fixed Bugs
----------

### BUG-46409  Alter replication set 구문 중 meta 초기화가 안된 구문이 있습니다.

-   **module** : rp

-   **Category** : Other

-   **재현 빈도** : Always

-   **증상** : 내부적으로 Alter replication set 구문을 처리하는 로직에서 meta 초기화가 누락된 부분이 있어, 수정하였습니다.

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

### BUG-46783  이중화 중 DDL 수행 시 receiver 가 종료할 경우 이미 free 된 이중화 이름을 복사 할 수 있습니다.

-   **module** : rp-control

-   **Category** : Memory Error

-   **재현 빈도** : Frequence

-   **증상** : 이중화 중 DDL 수행 시 receiver 가 종료할 경우 이미 free 된 이중화 이름을 복사 할 수 있어 수정합니다.

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

### BUG-46879  OpenJDK11 에서 jdbcAdapter 구동 실패 수정

- **module** : rp-jdbcAdapter

- **Category** : Functional Error

- **재현 빈도** : Always

- **증상** : OpenJDK11에서 jdbcAdapter 구동이 되지 않는 문제를 수정하였습니다.

  또한, jdbcAdapter 실행시 jvm생성시 stderr가 발생하면 ALA socket으로 error가 전송되는 문제가 있었는데, $ALTIBASE_HOME/trc/stderr.log에 쓰도록 로그파일이 추가되었습니다.

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

### BUG-47090  AIX, HP 장비에서 sysdba로 remote 접속을 막는 기능이 제대로 동작하지 않습니다.

-   **module** : cm

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : AIX, HP 장비에서 sysdba로 remote 접속을 막는 기능이 제대로 동작하지 않아 수정하였습니다.

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

### BUG-47095  partition simple query 수행 시, 메모리 초기화 누락

-   **module** : qp-dml-execute

-   **Category** : Memory Error

-   **재현 빈도** : Always

-   **증상** : partition simple query 수행시, 내부적으로 초기화하지 않은 변수를 사용하는 문제가 있어 수정하였습니다.

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

### BUG-47105  cpu 정보를 가져올 때 on-line 인지 off-line 인지 체크하지 않아, 서버가 boot 과정에서 실패할 수 있습니다.

- **module** : id

- **Category** : Functional Error

- **재현 빈도** : Always

- **증상** : 리눅스플래폼에서 cpu중 일부만 활성화한 상태에서 altibase 서버구동시 실패하는 문제를 해결합니다.

- **재현 방법**

  -   **재현 절차**

          cpu의 상태를 off-line으로 변경

  -   **수행 결과**

  -   **예상 결과**

- **Workaround**

- **변경사항**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

### BUG-47115  OpenJDK11 환경에서 jdbcAdapter 테스트 수행시, StackOverflowError가 발생하는 문제 수정

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : OpenJDK11환경에서 JdbcAdapter 테스트 수행시
    StackOverflowError가 발생하는 문제 수정.

-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

        use JRE 1.7

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47119  이중화 접속시 sendHandshakeAck 를 보낼 때 패킷 계산이 잘못되어 메모리를 긁을 수 있습니다.

-   **module** : rp

-   **Category** : Other

-   **재현 빈도** : Always

-   **증상** : 이중화 접속시 sendHandshakeAck 를 보낼 때 패킷 계산이
    잘못되어 메모리를 긁을 수 있어 수정합니다.

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

### BUG-47121  jdbcAdapter conf 파일에 OTHER\_DATABASE\_JDBC\_MAX\_HEAP\_SIZE 가 설정이 되지 않는 문제가 있습니다.

- **module** : rp-jdbcAdapter

- **Category** : Other

- **재현 빈도** : Always

- **증상** : 매뉴얼에는 OTHER\_DATABASE\_JDBC\_MAX\_HEAP\_SIZE 로 되어
  있으나 소스상에서는 OTHER\_DATABASE\_JDBC\_JVM\_MAX\_HEAP\_SIZE 로
  되어 있어서 프로퍼티가 설정되지 않는 문제가 있었습니다.

  소스에도 매뉴얼과 동일하게 OTHER\_DATABASE\_JDBC\_MAX\_HEAP\_SIZE 를
  사용하도록 하여 문제 수정하였습니다.

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

### BUG-47126  호스트 변수에 길이가 긴 값을 할당하면 segment fault 발생합니다

-   **module** : ux-isql

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : 호스트 변수에 할당한 스트링 값을 저장하는 변수가 256 길이로 고정되어 있어서 발생하는 문제로, 동적할당으로 변경하였습니다.

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

### BUG-47128  Query rebuild시 query\_binding memory가 지속적으로 증가할 수 있습니다.

-   **module** : qp-dml-execute

-   **Category** : Memory Error

-   **재현 빈도** : Always

-   **증상** : Query rebuild 발생시 이전에 bind data를 저장하기 위한
    memory를 해제하지 않는 문제를 수정합니다.

    Bind가 있는 query를 prepare 한 뒤 반복해서 execute 할 때, rebuild가
    발생하면 해당 문제가 발생합니다.

    Statement를 닫거나 session을 종료하면 bind를 위해 할당한 memory를
    memory manager에서 일괄 반납하므로 이전에 해제하지
    못한 memory도 모두 해제합니다.

-   **재현 방법**

    -   **재현 절차**

            session 1
            loop
            {
              update with binding
            }
            session 2
            loop
            {
              truncate table
            }

    -   **수행 결과**

            query_binding size is continually increased.

    -   **예상 결과**

            query_binding size is fixed.

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47135  OpenJDK에서 실행시 jvm 생성이 안 됩니다

- **module** : ux-altiMon

- **Category** : Portability

- **재현 빈도** : Always

- **증상** : OpenJDK에서 altimon.sh 실행시 아래 에러 메시지를 출력하고 jvm 생성이 안 되는 문제를 수정하였습니다.
  

% cat altimon\_stderr.log

Error: Could not create the Java Virtual Machine.

Error: A fatal exception has occurred. Program will exit.

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

### BUG-47136  alter tablespace swap시, 테이블 스페이스 사용량를 계산하는 로직 오류 수정

-   **module** : qp

-   **Category** : Other

-   **재현 빈도** : Always

-   **증상** : alter tablespace swap시, 테이블 스페이스 사용량를 계산하는 로직의 오류로 [ERR-3144E : Need more free space of tablespace.] 에러가 발생하는 경우가 있어 수정하였습니다.

-   **재현 방법**

    -   **재현 절차**

            DROP TABLESPACE DISK_TBS_0 INCLUDING CONTENTS AND DATAFILES;
            DROP TABLESPACE MEM__TBS_0 INCLUDING CONTENTS AND DATAFILES;
            CREATE DISK     TABLESPACE DISK_TBS_0 DATAFILE 'disk_tbs_0' SIZE 4M AUTOEXTEND ON MAXSIZE 40M;
            CREATE MEMORY   TABLESPACE MEM__TBS_0                       SIZE 4M AUTOEXTEND ON MAXSIZE 40M;
            create table t1
                 (
                     c1 integer,
                     c2 char(100),
                     c3  integer,
                     c4  char(100),
                     c5  char(100),
                     c6  char(100),
                     c7  char(100),
                     c8  char(100),
                     c9  integer,
                     c10 date
                   ) TABLESPACE MEM__TBS_0;
            alter table t1 add primary key(c3,c1) ;
            insert into t1 
             select level, level, 3, level, level, level, level, level, level, sysdate
             from dual connect by level <=  50000;
            alter table t1 alter tablespace DISK_TBS_0;
        
    - **수행 결과**
    
      ```
  iSQL> alter table t1 alter tablespace DISK_TBS_0;
      [ERR-3144E : Need more free space of tablespace. Tablespace Name: DISK_TBS_0, Progress : 1%, Threshold : 80%, Estimated Page Count : 400.]
    ```
  
-   **예상 결과**
    
            iSQL> alter table t1 alter tablespace DISK_TBS_0;
            Alter success.
    
-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47140  하위버전과 이중화시 해시 파티션드 테이블의 파티션 개수가 같은 경우에도 이중화 실패가 발생할수 있습니다.

-   **module** : rp

-   **Category** : Other

-   **재현 빈도** : Always

-   **증상** :  이중화시 해시 파티션드 테이블의 파티션 개수를 체크하도록
    프로토콜을 추가하였는데 하위버전과 이중화시  해시 파티션드 테이블을
    사용하면 파티션 개수를 잘못 체크하여 이중화 start 시 에러가 발생하는
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

### BUG-47142  BLOB컬럼과 DECIMAL 컬럼을 포함한 테이블에서 첫번째 컬럼의 타입이 BLOB 이고, HASH 조인을 할 경우 에러가 발생합니다.

-   **module** : qp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : BLOB컬럼과 DECIMAL 컬럼을 포함한 테이블에서 HASH 조인을
    할 경우, 과도한 메모리 할당을 요구하는 문제가 있어, 수정하였습니다.

-   **재현 방법**

    -   **재현 절차**

            drop table t1;
            drop table t2;                    
            CREATE TABLE t1 ( COL   blob,
                                             COL_DECIMAL     DECIMAL );
            CREATE TABLE T2( COL   blob,
                                              COL_DECIMAL     DECIMAL );
            select * from  t1 left outer join t2 on t1.col_decimal = t2.col_decimal;
        
    -   **수행 결과**

            iSQL> select * from  t1 left outer join t2 on t1.col_decimal = t2.col_decimal;
            [ERR-31318 : Unexpected errors may have occurred: qtc::fixAfterValidation: tuple row size is larger than 4GB]
        
    -   **예상 결과**
    
            iSQL> select * from  t1 left outer join t2 on t1.col_decimal = t2.col_decimal;
            [ERR-91022 : LOB and GEOMETRY type data cannot be displayed]
    
-   **Workaround**

        drop table t1;
        drop table t2;                    
        CREATE TABLE t1 ( COL_DECIMAL     DECIMAL ,
                                        COL_int1   blob);
        CREATE TABLE T2( COL_DECIMAL     DECIMAL,
                                          COL_int1   blob );
        select * from  t1 left outer join t2 on t1.col_decimal = t2.col_decimal;
    
-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47173  host variable precision이 컬럼 size보다 큰 경우 simple query 수행 시 에러처리 되는 것을 개선해야합니다.

-   **module** : qp-dml-execute

-   **Category** : Other

-   **재현 빈도** : Always

-   **증상** :  fast simple query에서 index생성 시 bind되는 varchar,
    char type precision이 테이블의 varchar, char precision보다 큰 경우
    에러 처리되는 부분을 개선함

-   **재현 방법**

    -   **재현 절차**

            VAR A CHAR(9);
                EXEC :A := 'ABCDEFGHI';
                CREATE TABLE T1 (I1 CHAR(5) PRIMARY KEY, I2 CHAR(5));
                VAR A CHAR(9);
                EXEC :A := 'ABCDEFGHI';
                PREPARE SELECT * FROM T1 WHERE I1 = :A;
                [ERR-2100D : Invalid data type length]

    -   **수행 결과**

    -   **예상 결과**

            VAR A CHAR(9);
                EXEC :A := 'ABCDEFGHI';
                CREATE TABLE T1 (I1 CHAR(5) PRIMARY KEY, I2 CHAR(5));
                VAR A CHAR(9);
                EXEC :A := 'ABCDEFGHI';
                PREPARE SELECT * FROM T1 WHERE I1 = :A;
            I1     I2     
            -----------------
            No rows selected.

-   **Workaround**

            VAR A CHAR(9);
            EXEC :A := 'ABCDEFGHI';
            CREATE TABLE T1 (I1 CHAR(5) PRIMARY KEY, I2 CHAR(5));
            VAR A CHAR(9);
            EXEC :A := 'ABCDEFGHI';
            PREPARE SELECT  /*+ NO_EXEC_FAST*/  * FROM T1 WHERE I1 = :A;
        I1     I2     
        -----------------
        No rows selected.

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47195  PARTITION SWAP 후 비정상종료시 재구동 실패.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **증상** : PARTITON SWAP 후 비정상종료 된경우 서버 구동 실패하는 버그를 수정하였습니다.

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
-------

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 7.1.0.2.6        | 6.5.1                   | 8.7.1        | 7.1.7               | 7.4.5                        |

> Altibase 7.1 패치 버전별 히스토리는 [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7_1_Version_Histories.md)
> 에서 확인할 수 있다.

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

### 프로퍼티

#### 변경된 프로퍼티

[MEMORY_INDEX_BUILD_RUN_SIZE](<https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_1.md#memory_index_build_run_size-%EB%8B%A8%EC%9C%84--%EB%B0%94%EC%9D%B4%ED%8A%B8>)

### 성능 뷰

추가/변경/삭제된 성능뷰 없음
