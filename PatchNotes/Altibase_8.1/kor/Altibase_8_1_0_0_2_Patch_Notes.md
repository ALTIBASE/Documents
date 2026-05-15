Altibase 8.1.0.0.2 Patch Notes
================================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-52206 Log Analyzer(ALA) 및 Adapter에서 JSON 데이터 타입 지원 확대](#bug-52206)
    - [BUG-52215 abm 로그(abm.log) 경로 지정 기능 추가](#bug-52215)
    - [BUG-52233 abm에서 gzip 압축 레벨 설정 기능 추가](#bug-52233)
    - [BUG-52224 이중화 Give-up 관련 로그 메시지 추가](#bug-52224)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-48937 증분 백업 디렉토리 경로에 사용자가 생성한 디렉토리가 존재하는 경우, 백업 파일의 삭제가 실패하는 문제를 수정](#bug-48937)
    - [BUG-51201 이중화 대상 파티션이 PK를 기준으로 나뉘어있지 않은 경우, 파티션의 순서에 따라 XLog 반영 순서가 역전될 수 있습니다.](#bug-51201)
    - [BUG-51324 디스크 인덱스 통계정보 병렬 수집 시 성능 저하 문제 수정](#bug-51324)
    - [BUG-51953 메모리 테이블스페이스 자원 부족 시 이중화 리시버를 중지하도록 동작 개선](#bug-51953)
    - [BUG-52106 abm 에러 메시지 개선1](#bug-52106)
    - [BUG-52122 abm 에러 메시지 개선2](#bug-52122)
    - [BUG-52119 SUPPLEMENTAL LOG 활성화 상태에서 jdbcAdapter를 통해 이중화 대상 테이블에 반영하는 과정에서, UPDATE 실패 문제 수정](#bug-52119)
    - [BUG-52140 `VIEW_FORCE=ON` 환경에서 View DDL이 100바이트를 초과할 경우 오류(Core Dump) 수정](#bug-52140)
    - [BUG-52152 adapter에서 UPDATE, DELETE 수행 중 오류 발생 시 로그에 출력되는 쿼리 형식의 오류 수정](#bug-52152)
    - [BUG-52163 CLI 환경에서 Temporary LOB의 EMPTY_CLOB() 처리 오류 수정](#bug-52163)
    - [BUG-52168 BUFFER AREA SIZE 확장 후 디스크 테이블 DML 성능 미반영 문제 수정](#bug-52168)
    - [BUG-52171 SQL 함수를 사용하는 트리거가 있는 테이블의 이름을 변경할 때 서버 비정상 종료 문제 수정](#bug-52171)
    - [BUG-52181 REPLICATION_MAX_LOGFILE 설정 환경에서 이중화 반영 중 Give-up 실패 문제 수정](#bug-52181)
    - [BUG-52189 json 함수에서 EMPTY_CLOB() 입력 시 오류 발생 문제 수정](#bug-52189)
    - [BUG-52190 Non-AutoCommit 환경에서 SELECT 문 실행 순서에 따른 Lock 비정상 해제 문제 수정](#bug-52190)
    - [BUG-52192 파일 백업 과정에서 시스템 콜 호출 실패 시 오류 메시지 개선](#bug-52192)
    - [BUG-52213 통계 정보 누적 시간 값 오류 수정](#bug-52213)
    - [BUG-52219 SUPPLEMENTAL LOG 를 생성할 때 VARIABLE COLUMN 패딩을 고려해야 합니다.](#bug-52219)
    - [BUG-52220 이중화 환경에서 LOB 컬럼과 SUPPLEMENTAL LOG가 설정된 디스크 테이블에 DROP COLUMN 구문 수행 시 서버 비정상 종료 문제 수정](#bug-52220)
    - [BUG-52226 SQL_APPLY 모드에서 DELETE 로그 처리 시 standby 서버 비정상 종료 문제 수정](#bug-52226)
    - [BUG-52229 Temporary LOB의 Concat 연산시 [ERR-314B8 : Failed to seek a Session Temporary LOB.] 오류 수정](#bug-52229)
    - [BUG-52230 다른 사용자가 부여한 Role 권한을 SYS 계정에서 회수시에 The meta table crashed. 에러가 발생](#bug-52230)
    - [BUG-52236 하위 버전 클라이언트(6.1.1)에서 7.3 서버 접속 시 바인드 값이 없는 경우 ASSERT 발생 문제 수정](#bug-52236)
    - [BUG-52261 oraAdapter에서 EMPTY_CLOB() 또는 EMPTY_BLOB()을 포함한 UPDATE 문을 동시 수행 시 timeout 발생 문제 수정](#bug-52261)
    - [BUG-52262 구버전 클라이언트(6.1.1 이하) 연결 중 잘못된 프로토콜 헤더가 수신될 경우 서버가 비정상 종료되는 문제 수정](#bug-52262)
    - [BUG-52284 모든 public synonym 제거 시 aexport에서 DBMS_METADATA 수행 실패 문제 수정](#bug-52284)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# New Features

### BUG-52206<a name=bug-52206></a> Log Analyzer(ALA) 및 Adapter에서 JSON 데이터 타입 지원 확대

- **module** : rp

- **Category** : Other

- **재현 빈도** : Always

- **설명** : 이제 Altibase Log Analyzer(ALA)와 Adapter(oraAdapter, jdbcAdapter)를 이용한 이중화 환경에서도 JSON 데이터 타입을 지원합니다.

  ALA와 Adapter를 통한 이중화 시 JSON 타입 데이터는 CLOB 형태로 변환되어 로그로 전송되며, 이에 따라 JSON 데이터에 매핑되는 타겟 데이터베이스의 대상 컬럼은 CLOB 타입으로 설정해야 합니다.

- **재현 방법**

  -   **재현 절차**

  -   **수행 결과**

  -   **예상 결과**

- **Workaround**

- **변경사항**

  - Performance view

  - Property

    - [REPLICATION_JSON_MEMPOOL_ELEMENT_COUNT](https://manual.altibase.com/8.1/ref/general/2.-Altibase-Properties/Replication-Properties/#replication_json_mempool_element_count) 추가

      -   설명: Log Analyzer를 이용하여 JSON 컬럼을 포함한 테이블을 이중화하는 과정에서, JSON to CLOB 변환에 사용되는 mempool의 element(element의 크기: 64KB) 개수를 지정하는 프로퍼티이다.

      이 프로퍼티는 메모리 사용량과 시스템 콜 오버헤드 간의 trade-off를 고려하여 설정해야 한다. 이 값을 작게 설정하면, 메모리 낭비는 줄어들지만 대용량 데이터 처리 시 시스템 콜 오버헤드가 증가할 수 있다. 이 값을 크게 설정하면, 시스템 콜 오버헤드는 감소하지만 메모리 사용량이 증가할 수 있다.

      -   기본값: 1
      -   값의 범위: 1~2<sup>10</sup>

  - Compile Option

  - Error Code

### BUG-52215<a name=bug-52215></a> abm 로그(abm.log) 경로 지정 기능 추가

- **module** :

- **Category** : Functionality

- **재현 빈도** : Always

- **설명** : abm.log 파일의 생성 경로를 지정할 수 있도록 `-log_path` 옵션이 추가되었다. `-log_path`를 지정하지 않으면, abm이 실행되는 현재 디렉터리에 abm.log 파일이 생성된다.

  또한 abm.properties 파일이 추가되었으며, 이 파일의 `LOG_PATH` 프로퍼티를 통해서도 abm.log 파일의 생성 경로를 지정할 수 있다.

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

### BUG-52233<a name=bug-52233></a> abm에서 gzip 압축 레벨 설정 기능 추가

-   **module** : ux-abm
-   **Category** : Functionality
-   **재현 빈도** : Always
-   **설명** : abm에서 gzip 압축 레벨을 사용자가 직접 설정할 수 있도록 개선되었습니다. 이를 위해 `abm.properties` 파일에 ` GZIP_COMP_LEVEL`프로퍼티가 추가되었으며, 기본값은 6입니다.
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

### BUG-52224<a name=bug-52224></a> 이중화 Give-up 관련 로그 메시지 추가

- **module** : rp-sender

- **Category** : Enhancement

- **재현 빈도** : Always

- **설명** : `REPLICATION_MAX_LOGFILE` 프로퍼티 값을 1 이상으로 설정한 이후, Give-up이 발생했을 때 확인할 수 있는 로그 메시지와 Give-up 이후 이중화 SENDER가 재시작되었을 때 확인할 수 있는 로그 메시지가 추가 되었습니다.

  로그 메시지는 아래와 같이 추가되었습니다.

  - Give-up 시작 시: **[Manager] Replication {replication_name} Sender Give-up Start.**
  - Give-up 종료 시: **[Manager] Replication {replication_name} Sender Give-up End.**
  - Give-up 수행 중 Sender 스레드 재시작 시: **[Manager] Replication {replication_name} Restarts Sender After Give-up.**

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

Fixed Bugs
==========

### BUG-48937<a name=bug-48937></a> 증분 백업 디렉토리 경로에 사용자가 생성한 디렉토리가 존재하는 경우, 백업 파일의 삭제가 실패하는 문제를 수정

-   **module** : sm

-   **Category** : Message Error

-   **재현 빈도** : Always

- **설명** : 증분 백업 디렉토리 경로에 사용자가 생성한 디렉토리가 존재하는 경우, "ALTER DATABASE DELETE OBSOLETE BACKUP FILES;" 구문 수행 시 [ERR-41082 : Internal server error]로 실패하던 문제를 수정하였습니다. 이제 증분 백업 디렉토리 내에 사용자 생성 디렉토리가 있더라도 해당 구문이 정상적으로 수행되며, 사용자가 생성한 디렉토리는 삭제되지 않습니다. 또한, 삭제할 수 없는 디렉토리에 대한 정보는 trc의 `altibase_sm.log` 파일에 기록됩니다.

  - 예: `altibase_sm.log` 파일에 아래와 같은 메시지를 확인할 수 있습니다.

    ```bash
    [BackupInfoMgr] Unable to delete <backup_path> (errno=39)
    ```

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

### BUG-51201<a name=bug-51201></a> 이중화 대상 파티션이 PK를 기준으로 나뉘어있지 않은 경우, 파티션의 순서에 따라 XLog 반영 순서가 역전될 수 있습니다.

-   **module** : rp-jdbcAdapter

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : Active 서버의 이중화 대상 파티션이 PK를 기준으로 나뉘어있지 않은 경우, 파티션의 순서에 따라 어댑터에서 반영하는 XLog의 순서가 역전될 수 있는 것을 수정했습니다.
    
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

### BUG-51324<a name=bug-51324></a> 디스크 인덱스 통계정보 병렬 수집 시 성능 저하 문제 수정

-   **module** : sm

-   **Category** : Other

-   **재현 빈도** : Always

-   **설명** : 디스크 인덱스 통계정보 수집을 병렬로 수행할 때 수행시간이 더 소모되는 문제를 수정했습니다.
    
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

### BUG-51953<a name=bug-51953></a> 메모리 테이블스페이스 자원 부족 시 이중화 리시버를 중지하도록 동작 개선

-   **module** : rp
-   **Category** : Enhancement
-   **재현 빈도** : Always
-   **설명** : 이중화 반영 과정에서 아래와 같은 메모리 테이블스페이스 자원 부족으로 인해 반영에 실패하는 경우, 기존에는 해당 오류가 충돌로 처리되었으나, 개선 후에는 이중화 리시버를 중지하도록 동작이 변경되었습니다.
    - 메모리 테이블스페이스의 자동 확장 기능이 꺼져있는 경우 (smERR_ABORT_UNABLE_TO_EXTEND_CHUNK_WHEN_AUTO_EXTEND_OFF)
    - 메모리 테이블스페이스의 크기가 MEM_MAX_TBS_SIZE 를 초과한 경우 (smERR_ABORT_UNABLE_TO_EXTEND_CHUNK_MORE_THAN_MEM_MAX_DB_SIZE)
    - 메모리 테이블스페이스의 최대 크기를 초과한 경우 (smERR_ABORT_UNABLE_TO_EXTEND_CHUNK_MORE_THAN_TBS_MAXSIZE )
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

### BUG-52106<a name=bug-52106></a> abm 에러 메시지 개선1

-   **module** : ux-abm

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : BACKUP INCREMENTAL 수행 중 서버 에러 메세지가 누락되는 현상을 수정하였습니다.
    
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

### BUG-52122<a name=bug-52122></a> abm 에러 메시지 개선2

-   **module** : ux-abm

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : Change Tracking 비활성 상태에서 iSQL 전용 명령어 안내
    메시지 출력을 abm용으로 변경

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

### BUG-52119<a name=bug-52119></a> SUPPLEMENTAL LOG 활성화 상태에서 jdbcAdapter를 통해 이중화 대상 테이블에 반영하는 과정에서, UPDATE 실패 문제 수정

-   **module** : rp-jdbcAdapter

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : SUPPLEMENTAL LOG 활성화 상태에서 jdbcAdapter를 통해 이중화 대상 테이블에 반영하는 과정에서, UPDATE 문 수행이 실패하던 문제를 수정하였습니다.

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

### BUG-52140<a name=bug-52140></a> `VIEW_FORCE=ON` 환경에서 View DDL이 100바이트를 초과할 경우 오류(Core Dump) 수정

-   **module** : ux-aexport

-   **Category** : Functional Error

-   **재현 빈도** : Unknown

-   **설명** : `VIEW_FORCE=ON` 환경에서 View DDL이 100바이트를 초과할 경우, aexport 수행 중 core 파일이 생성되며 추출이 중단되던 문제를 수정했습니다.
    
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

### BUG-52152<a name=bug-52152></a> adapter에서 UPDATE, DELETE 수행 중 오류 발생 시 로그에 출력되는 쿼리 형식의 오류 수정

-   **module** : rp-jdbcAdapter

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : `ADAPTER_XLOG_WRITE_TYPE` 프로퍼티가 `1`인 상태에서 UPDATE/DELETE 수행 중 오류가 발생할 경우, 로그 파일에 기록되는 SQL에 공백이 잘못 처리되어 해당 SQL을 그대로 사용할 수 없는 문제를 수정했습니다.
    
    수정된 항목은 다음과 같습니다.

    - WHERE 절에 PK 조건이 두 개 이상 포함된 경우, `AND` 앞 공백이 누락되는 문제 해결
    - `NULL` 값 이후 불필요한 공백이 추가되는 문제 해결

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

### BUG-52163<a name=bug-52163></a> CLI 환경에서 Temporary LOB의 EMPTY_CLOB() 처리 오류 수정

-   **module** : qp-select-execute

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : CLI 환경에서 Temporary LOB에 대해 `EMPTY_CLOB()`을 처리하는 과정에서 오류가 발생하는 문제를 수정했습니다.
    
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

### BUG-52168<a name=bug-52168></a> BUFFER AREA SIZE 확장 후 디스크 테이블 DML 성능 미반영 문제 수정

-   **module** : sm

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 서비스 중 DISK BUFFER AREA SIZE를 확장하더라도 디스크 테이블의 DML 성능이 향상되지 않던 문제를 수정하였습니다.
    
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

### BUG-52171<a name=bug-52171></a> SQL 함수를 사용하는 트리거가 있는 테이블의 이름을 변경할 때 서버 비정상 종료 문제 수정

-   **module** : qp-psm-trigger-execute

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : SQL 함수를 사용하는 트리거가 있는 테이블의 이름을 변경할 때 서버가 비정상 종료할 수 있는 문제를 수정했습니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    create table t1 (c1 integer);
    create or replace trigger trig_on_t1
    before insert on t1
    referencing new as new_row
    for each row
    as
    var1 varchar(10);
    begin
      var1 := nvl('a', 'a');
    end;
    /
    rename t1 to tx;
    ```

  -   **수행 결과**

          [ERR-91015 : Communication failure.]

  -   **예상 결과**

          Rename success.

-   **Workaround**

        트리거를 제거(Drop)하고, 테이블의 이름을 변경(rename)한 다음 다시 트리거를 생성한다.

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-52181<a name=bug-52181></a> REPLICATION_MAX_LOGFILE 설정 환경에서 이중화 반영 중 Give-up 실패 문제 수정

-   **module** : rp-sender

-   **Category** : Functional Error

-   **재현 빈도** : Frequence

-   **설명** : REPLICATION_MAX_LOGFILE 프로퍼티가 1 이상으로 설정된 환경에서, 이중화가 실행되어 레코드가 Standby 서버에 반영되고 있는 중일 경우 Give-up이 실패할 수 있는 문제를 수정하였습니다.
    
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

### BUG-52189<a name=bug-52189></a> json 함수에서 EMPTY_CLOB() 입력 시 오류 발생 문제 수정

-   **module** : qp-dml-execute

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : json 함수에서 EMPTY_CLOB() 입력 시 발생하는 오류를 수정합니다.
    
- **재현 방법**

  -   **재현 절차**

          DROP TABLE BUG_XXXXX;
          CREATE TABLE BUG_XXXXX(C1 INTEGER, C2 CLOB);
          INSERT INTO BUG_XXXXX VALUES ( 1, 1 );
          INSERT INTO BUG_XXXXX VALUES ( 2, '' );
          INSERT INTO BUG_XXXXX VALUES ( 3, NULL );
          INSERT INTO BUG_XXXXX VALUES ( 4, EMPTY_CLOB() );
          SELECT JSON_ARRAY( C2 RETURNING CLOB ) FROM BUG_XXXXX;

  - **수행 결과**

        JSON_ARRAY(C2RETURNINGCLOB)
        -----------------------------------------------------------------------------------
        ["1"]
        [null]
        [null]
        [ERR-110D0 : The lob size is bigger than the maximum lob size]
        3 rows selected.

  -   **예상 결과**

          JSON_ARRAY(C2RETURNINGCLOB)
          -----------------------------------------------------------------------------------
          ["1"]
          [null]
          [null]
          [""]
          4 rows selected.

-   **Workaround**

        NONE

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-52190<a name=bug-52190></a> Non-AutoCommit 환경에서 SELECT 문 실행 순서에 따른 Lock 비정상 해제 문제 수정

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : Non-AutoCommit 모드에서 하나의 트랜잭션 내 여러 SELECT 문을 수행할 때, SELECT 문 실행 순서에 따라 IS_LOCK이 비정상적으로 해제되던 문제를 수정합니다.

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

### BUG-52192<a name=bug-52192></a> 파일 백업 과정에서 시스템 콜 호출 실패 시 오류 메시지 개선

-   **module** : sm

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : 기존에는 파일 백업 과정에서 시스템 콜 호출 실패가
    발생하더라도 로그에 상세 정보가 충분히 기록되지 않아 정확한 원인을
    파악하기 어려웠습니다. 이제는 오류 발생시 실패한 시스템 콜 호출
    정보를 포함한 보다 상세한 오류 메시지가 출력되도록 개선하였습니다.

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

### BUG-52213<a name=bug-52213></a> 통계 정보 누적 시간 값 오류 수정

-   **module** : id

-   **Category** : Enhancement

-   **재현 빈도** : Unknown

-   **설명** : 통계 정보에 누적 시간 값이 잘못 기록되던 문제를 수정하였습니다.
    
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

### BUG-52219<a name=bug-52219></a> SUPPLEMENTAL LOG 를 생성할 때 VARIABLE COLUMN 패딩을 고려해야 합니다.

-   **module** : sm

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : SUPPLEMENTAL LOG 를 생성할 때 VARIABLE COLUMN의 패딩 처리가 올바르게 처리되지 않아, UPDATE문 수행시 실패하던 문제를 수정하였습니다.

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

### BUG-52220<a name=bug-52220></a> 이중화 환경에서 LOB 컬럼과 SUPPLEMENTAL LOG가 설정된 디스크 테이블에 DROP COLUMN 구문 수행 시 서버 비정상 종료 문제 수정

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : LOB 컬럼과 SUPPLEMENTAL LOG가 설정된 디스크 테이블이 이중화(Replication)에 포함된 경우, DROP COLUMN 구문 수행 시 서버가 비정상 종료되던 문제를 수정하였습니다.
    
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

### BUG-52226<a name=bug-52226></a> SQL_APPLY 모드에서 DELETE 로그 처리 시 standby 서버 비정상 종료 문제 수정

-   **module** : rp-receiver

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : Supplemental Log가 설정된 테이블의 이중화 환경에서 standby 서버가 SQL_APPLY 모드로 동작할 때, DELETE 로그 처리 중 비정상 종료되는 문제를 수정합니다.

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

### BUG-52229<a name=bug-52229></a> Temporary LOB의 Concat 연산시 [ERR-314B8 : Failed to seek a Session Temporary LOB.] 오류 수정

-   **module** : qp-select-pvo
-   **Category** : Functional Error
-   **재현 빈도** : Always
-   **설명** : Temporary LOB에 대한 concat(`||`) 연산 수행 시 발생할 수 있는 오류를 수정했습니다.
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

### BUG-52230<a name=bug-52230></a> 다른 사용자가 부여한 Role 권한을 SYS 계정에서 회수시에 The meta table crashed. 에러가 발생

-   **module** : qp-ddl-dcl-execute

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 사용자 계정에서 생성한 Role에 객체 권한을 부여한 후, SYS 계정에서 해당 권한을 회수할 경우 [ERR-31015 : The meta table crashed.] 오류가 발생하던 문제를 수정합니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    ## userA user 생성, role 생성
    create user userA identified by userA;
    create role r_userA;
    
    ## userA 으로 접속하여 userA.T1 테이블 생성
    connect userA/userA;
    create table T1(c1 integer primary key, c2 varchar(10), c3 varchar(10));
    
    ## userA user(소유자)가 r_userA role에 객체 권한 부여
    grant delete, insert, select, update on userA.T1 to r_userA;
    
    ## sys user가 r_userA role에게서 객체권한 회수 시도
    connect sys/manager;
    revoke delete, insert, select, update on userA.T1 from r_userA;
    ```

  - **수행 결과**

    ```sql
    [ERR-31015 : The meta table crashed.
    0001 : revoke delete, insert, select, update on userA.T1 from R_userA
    ^ ^
    ]                                                    ^        ^]
    ```

  -   **예상 결과**

-   **Workaround**

        sys user가 권한을 주고 회수

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-52236<a name=bug-52236></a> 하위 버전 클라이언트(6.1.1)에서 7.3 서버 접속 시 바인드 값이 없는 경우 ASSERT 발생 문제 수정

-   **module** : qp

-   **Category** : Assert

-   **재현 빈도** : Always

-   **설명** : 하위 버전 클라이언트에서 7.3 서버에 접속하여 요청을 수행할 때, 바인드 값 없이 전달된 프로토콜을 처리하는 과정에서 ASSERT가 발생하여 서버가 비정상 종료되는 문제가 있었습니다. 이를 수정하여 정상 처리되도록 개선하였습니다.

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

### BUG-52261<a name=bug-52261></a> oraAdapter에서 EMPTY_CLOB() 또는 EMPTY_BLOB()을 포함한 UPDATE 문을 동시 수행 시 timeout 발생 문제 수정

-   **module** : rp-oraAdapter

-   **Category** : Testcase Fail

-   **재현 빈도** : Frequence

-   **설명** : oraAdapter에서 `EMPTY_CLOB()` 및 `EMPTY_BLOB()`을 포함한 UPDATE 문을 동시에 수행할 경우, timeout이 발생하는 문제를 수정했습니다.

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

### BUG-52262<a name=bug-52262></a> 구버전 클라이언트(6.1.1 이하) 연결 중 잘못된 프로토콜 헤더가 수신될 경우 서버가 비정상 종료되는 문제 수정

-   **module** : cm

-   **Category** : Fatal

-   **재현 빈도** : Rare

-   **설명** : 구버전 클라이언트(6.1.1 이하) 연결 중 잘못된 프로토콜 헤더 값이 수신되는 특정 상황에서 서버가 비정상 종료될 수 있는 문제를 수정하였습니다.
    
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

### BUG-52284<a name=bug-52284></a> 모든 public synonym 제거 시 aexport에서 DBMS_METADATA 수행 실패 문제 수정

-   **module** :

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 모든 public synonym이 제거된 상태에서 aexport 수행 시, DBMS_METADATA 관련 작업이 실패하는 문제를 수정했습니다.
    
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
| 8.1.0.0.2        | 8.1.0                   | 10.1.1       | 7.1.9               | 7.4.9                        |

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의
> 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는
> 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

> 패치를 롤백하려는 경우,
> [메타다운그레이드](https://manual.altibase.com/8.1/start-here/install/3.-Uninstalling-Altibase-and-Meta-Downgrade/#%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9Cmeta-downgrade)를
> 참고한다.

#### CM protocol Version

통신 프로토콜 버전은 변경되지 않았다.

#### Replication protocol Version

Replication 프로토콜 버전은 변경되지 않았다.

### 프로퍼티

추가/변경/삭제된 프로퍼티 없음.

### 성능 뷰

추가/변경/삭제된 성능뷰 없음.
