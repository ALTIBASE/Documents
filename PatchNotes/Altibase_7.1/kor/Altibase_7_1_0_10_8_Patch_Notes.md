# Altibase 7.1.0.10.8 Patch Notes

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-51873 Altibase Connector for Kafka에 자동 재시작 기능이 추가되었습니다.](#bug-51873)
    - [BUG-51888 dblink, aku, Adapter에서 사용하는 암호화된 PASSWORD의 최대 허용 길이를 256자로 확장하였습니다.](#bug-51888)
    - [BUG-52014 Protocol header error 및 Invalid protocol sequence error 발생 시 진단 정보 출력 보강](#bug-52014)
    - [BUG-52066 비정상 종료 시 직전에 수행된 쿼리 출력 기능 추가](#bug-52066)
    - [BUG-52295 비정상 프로토콜 처리 시 assert 대신 세션 종료 및 클라이언트 정보 로깅 기능 개선](#bug-52295)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-48937 증분 백업 디렉토리 경로에 사용자가 생성한 디렉토리가 존재하는 경우, 백업 파일의 삭제가 실패하는 문제를 수정](#bug-48937)
    - [BUG-49298 이중화 Conflict시 정상 상황에서 불필요한 로그가 출력됩니다(Not Support Data Type).](#bug-49298)
    - [BUG-50643 컬럼이 포함된 테이블의 SYNC 작업 중 특정 레코드에서 충돌(Conflict)이 발생 할 경우, 직전에 입력된 레코드의 마지막 LOB 컬럼값이 NULL로 변경되는 문제를 수정했습니다.](#bug-50643)
    - [BUG-50976 CLOB 컬럼을 포함한 MERGE 문 수행 시 NULL 값이 포함된 행이 예상과 다르게 INSERT되는 문제 수정](#bug-50976)
    - [BUG-51324 디스크 인덱스 통계정보 병렬 수집 시 성능 저하 문제 수정](#bug-51324)
    - [BUG-51529 adapter 실행 중 간헐적으로 발생하던 통신 오류(Protocol header error) 문제를 수정하였습니다.](#bug-51529)
    - [BUG-51792 불완전 복구시에 TBS Update 로그를 만날경우 redo 시점을 조정하지 않도록 수정합니다.](#bug-51792)
    - [BUG-51905 adapter에서 LOB 컬럼이 포함된 디스크 테이블 이중화 오류 수정](#bug-51905)
    - [BUG-51920 ORDER BY절에 LOB 타입을 사용시 비정상 종료 문제 수정](#bug-51920)
    - [BUG-51953 메모리 테이블스페이스 자원 부족 시 이중화 리시버를 중지하도록 동작 개선](#bug-51953)
    - [BUG-51977 SQLDriverConnectW()에서 접속이 실패했는데 SQL_SUCCESS_WITH_INFO를 리턴하는 오류 수정](#bug-51977)
    - [BUG-51989 디스크 테이블에 인덱스가 존재하는 환경에서 Multiple Table Update 를 수행할 경우, 일부 행이 갱신되지 않는 문제를 수정하였습니다.](#bug-51989)
    - [BUG-51994 중첩된 Left Outer Join 구문 수행 시 일부 결과가 누락되는 결과 오류를 수정하였습니다.](#bug-51994)
    - [BUG-52002 SQL\_APPLY 모드로 SYNC 수행 중 충돌 발생 시, 레코드 갱신 처리 중 비정상 종료가 발생합니다.](#bug-52002)
    - [BUG-52046 레코드 1건의 길이가 2.5MB 이상일 때 디스크 해시 템프 테이블 삽입 중 오류가 발생할 수 있는 문제를 수정하였습니다.](#bug-52046)
    - [BUG-52062 altiEncrypt 바이너리가 패키지에 포함되지 않은 문제 수정](#bug-52062)
    - [BUG-52086 IPC 접속 환경에서 ServiceThread가 유효하지 않은 메모리를 참조할 수 있는 문제를 수정하였습니다.](#bug-52086)
    - [BUG-52087 ROW_NUMBER() 함수가 사용된 View에서 UNION ALL 사용 시 발생할 수 있는 오류 수정](#bug-52087)
    - [BUG-52091 이중화 환경에서 메타데이터 처리 중 동시성 문제 수정](#bug-52091)
    - [BUG-52168 BUFFER AREA SIZE 확장 후 디스크 테이블 DML 성능 미반영 문제 수정](#bug-52168)
    - [BUG-52171 SQL 함수를 사용하는 트리거가 있는 테이블의 이름을 변경할 때 서버 비정상 종료 문제 수정](#bug-52171)
    - [BUG-52188 비정상 종료 시 진단 덤프 정보 수집 안정성 개선](#bug-52188)
    - [BUG-52190 Non-AutoCommit 환경에서 SELECT 문 실행 순서에 따른 Lock 비정상 해제 문제 수정](#bug-52190)
    - [BUG-52219 SUPPLEMENTAL LOG 를 생성할 때 VARIABLE COLUMN 패딩을 고려해야 합니다.](#bug-52219)
    - [BUG-52220 이중화 환경에서 LOB 컬럼과 SUPPLEMENTAL LOG가 설정된 디스크 테이블에 DROP COLUMN 구문 수행 시 서버 비정상 종료 문제 수정](#bug-52220)
    - [BUG-52226 SQL_APPLY 모드에서 DELETE 로그 처리 시 standby 서버 비정상 종료 문제 수정](#bug-52226)
    - [BUG-52230 다른 사용자가 부여한 Role 권한을 SYS 계정에서 회수시에 The meta table crashed. 에러가 발생](#bug-52230)
    - [BUG-52262 구버전 클라이언트(6.1.1 이하) 연결 중 잘못된 프로토콜 헤더가 수신될 경우 서버가 비정상 종료되는 문제 수정](#bug-52262)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-51873<a name=bug-51873></a> Altibase Connector for Kafka에 자동 재시작 기능이 추가되었습니다.

-   **module** :

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : Altibase source connector for Kafka에 DDL 메시지 수신 시
    자동 재시작 기능이 추가되었습니다. 이 기능을 사용하려면 `restart.ddl` 프로퍼티의 값을 true로 설정해야 합니다.(기본값은 false)

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

### BUG-51888<a name=bug-51888></a> dblink, aku, Adapter에서 사용하는 암호화된 PASSWORD의 최대 허용 길이를 256자로 확장하였습니다.

-   **module** : rp

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** :  dblink, aku, Adapter에서 사용하는 암호화 PASSWORD의 최대 허용 길이를 256자로 변경합니다. 참고로, altiEncryt는 최대 128자 길이의 암호 입력을 지원하며, 이를 256자 길이의 암호화 PASSWORD로 생성합니다.
    
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

### BUG-52014<a name=bug-52014></a> Protocol header error 및 Invalid protocol sequence error 발생 시 진단 정보 출력 보강

-   **module** : cm

-   **Category** : Functionality

-   **재현 빈도** : Rare

-   **설명** : Protocol header error 및 Invalid protocol sequence error 발생 시 문제 분석에 도움이 되도록 세션 정보와 Client PID를 추가로 출력하도록 개선하였습니다.
    
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

### BUG-52066<a name=bug-52066></a> 비정상 종료 시 직전에 수행된 쿼리 출력 기능 추가

-   **module** : mm

-   **Category** : Enhancement

-   **재현 빈도** : Rare

-   **설명** : 서버 비정상 종료 시 시그널 핸들러에서 직전에 수행된 쿼리를 출력하는 기능을 추가하였습니다. 해당 기능은 `__QUERY_BUCKET_FLAG` 비공개 프로퍼티로 활성화할 수 있으며, 출력된 쿼리는 `dumptrc` 또는 `altibase_error.log` 파일에서 확인할 수 있습니다.
    
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

### BUG-52295<a name=bug-52295></a> 비정상 프로토콜 처리 시 assert 대신 세션 종료 및 클라이언트 정보 로깅 기능 개선

-   **module** : mm

-   **Category** : Assert

-   **재현 빈도** : Rare

- **설명** : 비정상 프로토콜 처리 과정에서 assert 대신 해당 클라이언트 세션과의 연결을 강제 종료하도록 수정하였습니다.

  또한, 문제 분석에 도움이 되도록 클라이언트 정보를 추가로 로깅하도록 개선하였습니다.

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

### BUG-48937<a name=bug-48937></a> 증분 백업 디렉토리 경로에 사용자가 생성한 디렉토리가 존재하는 경우, 백업 파일의 삭제가 실패하는 문제를 수정

-   **module** : sm

-   **Category** : Message Error

-   **재현 빈도** : Always

- **설명** : 증분 백업 디렉토리 경로에 사용자가 생성한 디렉토리가 존재하는 경우, "ALTER DATABASE DELETE OBSOLETE BACKUP FILES;" 구문 수행 시 [ERR-41082 : Internal server error]로 실패하던 문제를 수정하였습니다. 이제 증분 백업 디렉토리 내에 사용자 생성 디렉토리가 있더라도 해당 구문이 정상적으로 수행되며, 사용자가 생성한 디렉토리는 삭제되지 않습니다. 또한, 삭제할 수 없는 디렉토리에 대한 정보는 trc의 `altibase_sm.log` 파일에 기록됩니다.

  - 예:  `altibase_sm.log` 파일에 아래와 같은 메시지를 확인할 수 있습니다.

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

### BUG-49298<a name=bug-49298></a> 이중화 Conflict시 정상 상황에서 불필요한 로그가 출력됩니다(Not Support Data Type).

-   **module** : rp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 이중화 Conflict 시 BLOB, CLOB, GEOMETRY, JSON 타입의 컬럼이 존재하면 $ALTIBASE_HOME/trc/altibase_rp.log 파일에 아래와 같이 불필요한 로그가 출력되는 현상을 수정했습니다.
    
    ```bash
    ERR-61069(errno=62) Internal server error in replication module (Not Support Data Type( id : 40 )).
    ```
    
    또한, `altibase_rp_conflict.log` 파일에 BLOB, CLOB, GEOMETY, JSON 타입은 데이터 타입과 상관 없이 "\<None printable data>"와 같이 출력되는 것을 "<None printable data( id : 30 )>"처럼 해당 컬럼의 데이터 타입의 ID도 함께 출력하도록 수정했습니다.

-   **재현 방법**

    -   ***재현 절차***

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50643<a name=bug-50643></a> 컬럼이 포함된 테이블의 SYNC 작업 중 특정 레코드에서 충돌(Conflict)이 발생 할 경우, 직전에 입력된 레코드의 마지막 LOB 컬럼값이 NULL로 변경되는 문제를 수정했습니다.

-   **module** : rp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : LOB 컬럼이 포함된 테이블의 SYNC 작업 중 특정 레코드에서 충돌(Conflict)이 발생 할 경우, 직전에 입력된 레코드의 마지막 LOB 컬럼값이 NULL로 변경되는 문제를 수정했습니다. 이 현상은 첫 번째 레코드에서 충돌이 발생한 경우에는 발생하지 않으며, 두 번째 이후의 레코드에서 충돌이 발생할 경우에만 재현되었으며, 이번 패치 적용으로 더이상 발생하지 않습니다.
    
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

### BUG-50976<a name=bug-50976></a> CLOB 컬럼을 포함한 MERGE 문 수행 시 NULL 값이 포함된 행이 예상과 다르게 INSERT되는 문제 수정

-   **module** : qp-dml-pvo

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : CLOB 타입 컬럼을 포함한 테이블에서 MERGE 문 수행 시, `WHEN NOT MATCHED THEN INSERT` 절의 대상 행에 NULL 값이 포함된 경우 일부 컬럼 값이 NULL로 INSERT될 수 있는 문제를 수정하였습니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    drop table t1;
    drop table t2;
    create table t1( i1 clob, i2 clob );
    create table t2( i1 clob, i2 clob );
    insert into t1 values( '1', '1' );
    insert into t2 values( '1', '1' );
    insert into t2 values( '22', null);
    merge into t1 using t2 on (length(t1.i1) = length(t2.i1))
    when matched then
    update set t1.i2 = t1.i2 || t2.i2
    when not matched then
    insert (i1,i2) values (t2.i1, t2.i2);
    select i1 from t1;
    ```

  - **수행 결과**

    ```sql
    I1
    -----------------------------------------------------------------------------------
    1
    
    2 rows selected.
    ```

  -   **예상 결과**

      ```sql
      	I1
      -----------------------------------------------------------------------------------
      1
      22
      2 rows selected.
      ```

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

### BUG-51529<a name=bug-51529></a> adapter 실행 중 간헐적으로 발생하던 통신 오류(Protocol header error) 문제를 수정하였습니다.

-   **module** : rp-jdbcAdapter

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : adapter 실행 중 간헐적으로 발생하던 통신 오류(Protocol header error) 문제를 수정하였습니다.

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

### BUG-51792<a name=bug-51792></a> 불완전 복구시에 TBS Update 로그를 만날경우 redo 시점을 조정하지 않도록 수정합니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : 불완전 복구시에 TBS Update 로그를 만나면 Redo 시점을 조정하지 않도록 합니다.
    
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

### BUG-51905<a name=bug-51905></a> adapter에서 LOB 컬럼이 포함된 디스크 테이블 이중화 오류 수정

-   **module** : rp-jdbcAdapter

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : adapter에서 LOB 컬럼이 포함된 디스크 테이블 이중화 오류를 수정하였습니다.
    
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

### BUG-51920<a name=bug-51920></a> ORDER BY절에 LOB 타입을 사용시 비정상 종료 문제 수정

-   **module** : qp-dml-execute

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : ORDER BY절에서는 LOB 타입을 사용할 수 없는데, LOB 컬럼을 사용한경우 비정상 종료하는 문제를 수정했습니다. 이제 ORDER BY절에서 LOB 타입을 사용하면 [ERR-31246 : Incomparable data types (GEOMETRY,LOB) cannot be used in ORDER BY, GROUP BY, HAVING and CONNECT BY clauses.] 오류가 정상적으로 반환됩니다.

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

### BUG-51977<a name=bug-51977></a> SQLDriverConnectW()에서 접속이 실패했는데 SQL_SUCCESS_WITH_INFO를 리턴하는 오류 수정

-   **module** : mm-cli

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : SQLDriverConnectW()함수를 호출할 때 InConnectionString 인자에 유효하지 않은 IP 주소가 포함되어 있고, BufferLength 인자에 16과 같이 작은 값을 전달할 경우, 접속이 실패해야 하는데 `SQL_SUCCESS_WITH_INFO`가 반환되는 문제를 수정합니다.
    
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

### BUG-51989<a name=bug-51989></a> 디스크 테이블에 인덱스가 존재하는 환경에서 Multiple Table Update 를 수행할 경우, 일부 행이 갱신되지 않는 문제를 수정하였습니다.

-   **module** : sm\_index

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 디스크 테이블에 인덱스가 존재하는 환경에서 Multiple Table Update 를 수행할 경우, 일부 행이 갱신되지 않는 문제를 수정하였습니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    drop table t1;
    drop table t2;
    create table t1 ( i1 varchar(40), i2 varchar(10), SBI_ORDER_ID varchar(10) ) tablespace sys_tbs_disk_data;
    create index idx1 on t1 ( SBI_ORDER_ID );
    create table t2 ( i1 varchar(40), SBI_ORDER_ID varchar(10) ) tablespace sys_tbs_disk_data;
    create index idx2 on t2 ( SBI_ORDER_ID );
    
    insert into t1 select level, 10, '6000000077' from dual connect by level < 3;
    insert into t2 select level, '6000000077' from dual connect by level < 3;
    
    update t1 a, t2 b set a.i1 = 'AA', b.i1 = 'BB' where A.SBI_ORDER_ID = B.SBI_ORDER_ID and a.SBI_ORDER_ID = '6000000077';
    ```

  -   **수행 결과**

          3 rows updated.

  -   **예상 결과**

          4 rows updated.

-   **Workaround**

        NO INDEX

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-51994<a name=bug-51994></a> 중첩된 Left Outer Join 구문 수행 시 일부 결과가 누락되는 결과 오류를 수정하였습니다.

-   **module** : qp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 중첩된 Left Outer Join 구문 수행 시 Join predicate 처리 오류로 인해, 일부 결과가 누락될 수 있는 문제를 수정하였습니다.

- **재현 방법**

  - **재현 절차**

    ```sql
    drop table t1;
    drop table t2;
    drop table t3;
    drop table t4;
    
    create table t1 (c1 integer primary key, c2 char(10), c3 char(10));
    create table t2 (c1 integer primary key, c2 char(10), c3 char(10));
    create table t3 (c1 integer primary key, c2 char(10), c3 char(10));
    create table t4 (c1 integer primary key, c2 char(10), c3 char(10));
    insert into t1 values (1,1,null);
    insert into t2 values (1,1,24);
    insert into t4 values (1,1,24);
    
    select t2.*, t3.*, t4.* from t1
              left outer join  t2 on t1.c1 = t2.c1
              left outer join  t3 on t1.c1 = t3.c1
              left outer join  t4 on
              (t4.c2=t3.c2 and t4.c3 = t3.c3)
              or
              (t4.c2=t2.c2 and t4.c3 = t2.c3)
              ;
    ```

  -   **수행 결과**

      ```sql
      C1          C2          C3          C1          C2          C3
      -------------------------------------------------------------------------------
      C1          C2          C3
      ----------------------------------------
      1           1           24
      1 row selected.
      ```
      
  -   **예상 결과**

      ```sql
      C1          C2          C3          C1          C2          C3
      -------------------------------------------------------------------------------
      C1          C2          C3
      ----------------------------------------
      1           1           24
      1           1           24
      1 row selected.
      ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-52002<a name=bug-52002></a> SQL\_APPLY 모드로 SYNC 수행 중 충돌 발생 시, 레코드 갱신 처리 중 비정상 종료가 발생합니다.

-   **module** : rp

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : SQL_APPLY 모드로 SYNC 수행 중 충돌 발생 시, 충돌 해결 정책에 따라 레코드 갱신이 이루어질 경우, 서버가 비정상적으로 종료되는 현상을 수정했습니다.
    
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

### BUG-52046<a name=bug-52046></a> 레코드 1건의 길이가 2.5MB 이상일 때 디스크 해시 템프 테이블 삽입 중 오류가 발생할 수 있는 문제를 수정하였습니다.

-   **module** : sm

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 레코드 1건의 길이가 2.5MB 이상일 때 디스크 해시 템프 테이블 삽입 중 오류가 발생할 수 있는 문제를 수정하였습니다.

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

### BUG-52062<a name=bug-52062></a> altiEncrypt 바이너리가 패키지에 포함되지 않은 문제 수정

-   **module** : rp-jdbcAdapter

-   **Category** : Other

-   **재현 빈도** : Always

-   **설명** : 패키지 구성 과정에서 altiEncrypt 바이너리가 포함되지 않아 해당 기능을 사용할 수 없는 문제를 수정하였습니다.

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

### BUG-52086<a name=bug-52086></a> IPC 접속 환경에서 ServiceThread가 유효하지 않은 메모리를 참조할 수 있는 문제를 수정하였습니다.

-   **module** : mm

-   **Category** : Memory Error

-   **재현 빈도** : Rare

-   **설명** : IPC 접속 환경에서 ServiceThread가 유효하지 않은 메모리를 참조할 수 있는 문제를 수정하였습니다.

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

### BUG-52087<a name=bug-52087></a> ROW_NUMBER() 함수가 사용된 View에서 UNION ALL 사용 시 발생할 수 있는 오류 수정

-   **module** : qp

-   **Category** : Fatal

-   **재현 빈도** : Frequence

-   **설명** : ROW_NUMBER() 함수가 사용된 View에서 UNION ALL이 포함된 쿼리를 수행할 때, 특정 상황에서 오류가 발생할 수 있는 문제를 수정하였습니다.
    
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

### BUG-52091<a name=bug-52091></a> 이중화 환경에서 메타데이터 처리 중 동시성 문제 수정

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

        트리거를 제거(Drop)하고, 테이블의 이름을 변경한 다음 다시 트리거를 생성한다.

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-52188<a name=bug-52188></a> 비정상 종료 시 진단 덤프 정보 수집 안정성 개선

-   **module** : mm

-   **Category** : Reliability

-   **재현 빈도** : Rare

-   **설명** : 비정상 종료 시 특정 상황에서 세션 및 태스크 진단 정보가 누락되던 오류를 수정했습니다.
    또한 장애 분석에 도움이 되도록 통신 읽기 버퍼와 서비스 스레드 Statement ID 정보도 함께 덤프하도록 개선하였다.

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
    ]
    ```

  -   **예상 결과**

-   **Workaround**

        sys user가 권한을 주고 회수

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

Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 7.1.0.10.8       | 6.5.1                   | 8.12.1       | 7.1.7               | 7.4.7                        |

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

### 프로퍼티

추가/변경/삭제된 프로퍼티 없음.

### 성능 뷰

추가/변경/삭제된 성능뷰 없음.
