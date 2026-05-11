Altibase 7.1.0.10.8 Patch Notes
=================================

New Features
============

### BUG-51888 The maximum allowed length for encrypted PASSWORD used in dblink, aku, and Adapter has been extended to 256 characters.

-   **module** : rp
-   **Category** : Enhancement
-   **Reproducibility** : Always
-   **Description** : The maximum allowed length of the encrypted PASSWORD used in dblink, aku, and Adapter has been changed to 256 characters. Note that altiEncrypt supports password input of up to 128 characters in length, and generates an encrypted PASSWORD of up to 256 characters.

### BUG-52014 Enhanced diagnostic information for Protocol header error and Invalid protocol sequence error

-   **module** : cm
-   **Category** : Functionality
-   **Reproducibility** : Rare
-   **Description** : Improved diagnostics by additionally logging session information and client PID when Protocol header error or Invalid protocol sequence error occurs.

### BUG-52066 Added feature to print the last executed query on abnormal termination

-   **module** : mm
-   **Category** : Enhancement
-   **Reproducibility** : Rare
-   **Description** : Added a feature to print the last executed query from the signal handler when the server terminates abnormally.
     This feature can be enabled using the internal property `__QUERY_BUCKET_FLAG`, and the output can be found in `dumptrc` or `altibase_error.log`. 

### BUG-52295 Improved handling of abnormal protocol by terminating session instead of assert and enhanced client logging

-   **module** : mm
-   **Category** : Assert
-   **Reproducibility** : Rare
-   **Description** : During abnormal protocol processing, the behavior has been changed to forcibly terminate the connection with the client session instead of triggering an assert. Additionally, client information is now additionally logged to assist in problem analysis.

Fixed Bugs
==========

### BUG-48937 Fixed a failure in deleting backup files when user-created directories exist in the incremental

-   **module** : sm

-   **Category** : Message Error

-   **Reproducibility** : Always

- **Description** : Fixed an issue where the statement `ALTER DATABASE DELETE OBSOLETE BACKUP FILES;` failed with `[ERR-41082: Internal server error]` if the incremental backup directory contained user-created subdirectories. Now, the statement executes successfully even if user-created directories exist; those directories are preserved.

  Additionally, information about directories that could not be deleted is recorded in the `altibase_sm.log` file under the `trc` directory.

  - Example log message in `altibase_sm.log`:

  ```bash
   [BackupInfoMgr] Unable to delete <backup_path> (errno=39)
  ```

### BUG-49298 Fixed unnecessary log output during replication conflict (Not Support Data Type)

-   **module** : rp

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where unnecessary logs were generated in `$ALTIBASE_HOME/trc/altibase_rp.log` during replication conflicts when columns of type BLOB, CLOB, GEOMETRY, or JSON exist.
    
    ```bash
    ERR-61069(errno=62) Internal server error in replication module (Not Support Data Type( id : 40 )).
    ```
    
    Also improved logging in `altibase_rp_conflict.log` to include the data type ID, e.g.:

    ```
    <None printable data( id : 30 )>
    ```

### BUG-50643 Fixed issue where last LOB column value becomes NULL during SYNC conflict

- **module** : rp

- **Category** : Functional Error

- **Reproducibility** : Always

- **Description** : Fixed an issue where the last LOB column value of the previously inserted record becomes NULL when a conflict occurs during SYNC on tables with LOB columns.

  This issue only occurred when the conflict happened on the second or subsequent records, not the first record.
   It no longer occurs after applying this patch.

### BUG-50976 Incorrect value is entered when executing a MERGE INTO statement on a CLOB column.

-   **module** : qp-dml-pvo

-   **Category** : Functionality

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where an incorrect value was entered when executing a `MERGE INTO` statement on a CLOB column.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

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

  - **Actual Results**

    ```sql
    I1
    -----------------------------------------------------------------------------------
    1
    
    2 rows selected.
    ```

  -   **Expected Results**

      ```sql
      	I1
      -----------------------------------------------------------------------------------
      1
      22
      2 rows selected.
      ```

- **Workaround**

  None

### BUG-51324 Fixed performance degradation when collecting disk index statistics in parallel.

-   **module** : sm
-   **Category** : Other
-   **Reproducibility** : Always
-   **Description** : Fixed an issue where more time was consumed when collecting disk index statistics in parallel.

### BUG-51792 불완전 복구시에 TBS Update 로그를 만날경우 redo 시점을 조정하지 않도록 수정합니다.

-   **module** : sm
-   **Category** : Fatal
-   **Reproducibility** : Always
-   **Description** : 불완전 복구시에 TBS Update 로그를 만나면 Redo 시점을 조정하지 않도록 합니다.

### BUG-51905 adapter에서 LOB 컬럼이 포함된 디스크 테이블 이중화 오류 수정

-   **module** : rp-jdbcAdapter
-   **Category** : Functional Error
-   **Reproducibility** : Always
-   **Description** : adapter에서 LOB 컬럼이 포함된 디스크 테이블 이중화 오류를 수정하였습니다.

### BUG-51920 ORDER BY절에 LOB 타입을 사용시 비정상 종료 문제 수정

-   **module** : qp-dml-execute
-   **Category** : Fatal
-   **Reproducibility** : Always
-   **Description** : ORDER BY절에서는 LOB 타입을 사용할 수 없는데, LOB 컬럼을 사용한경우 비정상 종료하는 문제를 수정했습니다. 이제 ORDER BY절에서 LOB 타입을 사용하면 [ERR-31246 : Incomparable data types (GEOMETRY,LOB) cannot be used in ORDER BY, GROUP BY, HAVING and CONNECT BY clauses.] 오류가 정상적으로 반환됩니다.

### BUG-51953 메모리 테이블스페이스 자원 부족 시 이중화 리시버를 중지하도록 동작 개선

-   **module** : rp
-   **Category** : Enhancement
-   **Reproducibility** : Always
-   **Description** : 이중화 반영 과정에서 아래와 같은 메모리 테이블스페이스 자원 부족으로 인해 반영에 실패하는 경우, 기존에는 해당 오류가 충돌로 처리되었으나, 개선 후에는 이중화 리시버를 중지하도록 동작이 변경되었습니다.
    - 메모리 테이블스페이스의 자동 확장 기능이 꺼져있는 경우 (smERR_ABORT_UNABLE_TO_EXTEND_CHUNK_WHEN_AUTO_EXTEND_OFF)
    - 메모리 테이블스페이스의 크기가 MEM_MAX_TBS_SIZE 를 초과한 경우 (smERR_ABORT_UNABLE_TO_EXTEND_CHUNK_MORE_THAN_MEM_MAX_DB_SIZE)
    - 메모리 테이블스페이스의 최대 크기를 초과한 경우 (smERR_ABORT_UNABLE_TO_EXTEND_CHUNK_MORE_THAN_TBS_MAXSIZE )

### BUG-51977 SQLDriverConnectW()에서 접속이 실패했는데 SQL_SUCCESS_WITH_INFO를 리턴하는 오류를 수정해야 합니다.

-   **module** : mm-cli
-   **Category** : Functional Error
-   **Reproducibility** : Always
-   **Description** : SQLDriverConnectW()함수를 호출할 때 InConnectionString 인자에 유효하지 않은 IP 주소가 포함되어 있고, BufferLength 인자에 16과 같이 작은 값을 전달할 경우, 접속이 실패해야 하는데 `SQL_SUCCESS_WITH_INFO`가 반환되는 문제를 수정합니다.

### BUG-51989 디스크 테이블에 인덱스가 존재하는 환경에서 Multiple Table Update 를 수행할 경우, 일부 행이 갱신되지 않는 문제를 수정하였습니다.

-   **module** : sm\_index

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : 디스크 테이블에 인덱스가 존재하는 환경에서 Multiple Table Update 를 수행할 경우, 일부 행이 갱신되지 않는 문제를 수정하였습니다.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

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

  -   **Actual Results**

          3 rows updated.

  -   **Expected Results**

          4 rows updated.

-   **Workaround**

        NO INDEX

### BUG-51994 중첩된 Left Outer Join 구문 수행 시 일부 결과가 누락되는 결과 오류를 수정하였습니다.

-   **module** : qp

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : 중첩된 Left Outer Join 구문 수행 시 Join predicate 처리 오류로 인해, 일부 결과가 누락될 수 있는 문제를 수정하였습니다.

- **How to reproduce this bug**

  - **Reproduction conditions**

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

  -   **Actual Results**

      ```sql
      C1          C2          C3          C1          C2          C3
      -------------------------------------------------------------------------------
      C1          C2          C3
      ----------------------------------------
      1           1           24
      1 row selected.
      ```
      
  -   **Expected Results**

      ```sql
      C1          C2          C3          C1          C2          C3
      -------------------------------------------------------------------------------
      C1          C2          C3
      ----------------------------------------
      1           1           24
      1           1           24
      1 row selected.
      ```

- **Workaround**

  없음

### BUG-52002 SQL\_APPLY 모드로 SYNC 수행 중 충돌 발생 시, 레코드 갱신 처리 중 비정상 종료가 발생합니다.

-   **module** : rp
-   **Category** : Fatal
-   **Reproducibility** : Always
-   **Description** : SQL_APPLY 모드로 SYNC 수행 중 충돌 발생 시, 충돌 해결 정책에 따라 레코드 갱신이 이루어질 경우, 서버가 비정상적으로 종료되는 현상을 수정했습니다.

### BUG-52046 레코드 1건의 길이가 2.5MB 이상일 때 디스크 해시 템프 테이블 삽입 중 오류가 발생할 수 있는 문제를 수정하였습니다.

-   **module** : sm
-   **Category** : Functional Error
-   **Reproducibility** : Always
-   **Description** : 레코드 1건의 길이가 2.5MB 이상일 때 디스크 해시 템프 테이블 삽입 중 오류가 발생할 수 있는 문제를 수정하였습니다.

### BUG-52062 altiEncrypt 바이너리가 패키지에 포함되지 않은 문제 수정

-   **module** : rp-jdbcAdapter
-   **Category** : Other
-   **Reproducibility** : Always
-   **Description** : 패키지 구성 과정에서 altiEncrypt 바이너리가 포함되지 않아 해당 기능을 사용할 수 없는 문제를 수정하였습니다.

### BUG-52086 IPC 접속 환경에서 ServiceThread가 유효하지 않은 메모리를 참조할 수 있는 문제를 수정하였습니다.

-   **module** : mm
-   **Category** : Memory Error
-   **Reproducibility** : Rare
-   **Description** : IPC 접속 환경에서 ServiceThread가 유효하지 않은 메모리를 참조할 수 있는 문제를 수정하였습니다.

### BUG-52087 ROW_NUMBER() 함수가 사용된 View에서 UNION ALL 사용 시 발생할 수 있는 오류 수정

-   **module** : qp
-   **Category** : Fatal
-   **Reproducibility** : Frequence
-   **Description** : ROW_NUMBER() 함수가 사용된 View에서 UNION ALL이 포함된 쿼리를 수행할 때, 특정 상황에서 오류가 발생할 수 있는 문제를 수정하였습니다.

### BUG-52091 이중화 환경에서 메타데이터 처리 중 동시성 문제 수정

-   **module** : rp
-   **Category** : Fatal
-   **Reproducibility** : Rare
-   **Description** : 이중화 환경에서 메타 데이터 처리 중 발생할 수 있는 동시성 문제를 수정하였습니다.

### BUG-52168 BUFFER AREA SIZE 확장 후 디스크 테이블 DML 성능 미반영 문제 수정

-   **module** : sm
-   **Category** : Functional Error
-   **Reproducibility** : Always
-   **Description** : 서비스 중 DISK BUFFER AREA SIZE를 확장하더라도 디스크 테이블의 DML 성능이 향상되지 않던 문제를 수정하였습니다.

### BUG-52171 SQL 함수를 사용하는 트리거가 있는 테이블의 이름을 변경할 때 서버 비정상 종료 문제 수정

-   **module** : qp-psm-trigger-execute

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : SQL 함수를 사용하는 트리거가 있는 테이블의 이름을 변경할 때 서버가 비정상 종료할 수 있는 문제를 수정했습니다.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

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

  -   **Actual Results**

          [ERR-91015 : Communication failure.]

  -   **Expected Results**

          Rename success.

-   **Workaround**

        트리거를 제거(Drop)하고, 테이블의 이름을 변경한 다음 다시 트리거를 생성한다.

### BUG-52188 비정상 종료 시 진단 덤프 정보 수집 안정성 개선

-   **module** : mm
-   **Category** : Reliability
-   **Reproducibility** : Rare
-   **Description** : 비정상 종료 시 특정 상황에서 세션 및 태스크 진단 정보가 누락되던 오류를 수정했습니다.
    또한 장애 분석에 도움이 되도록 통신 읽기 버퍼와 서비스 스레드 Statement ID 정보도 함께 덤프하도록 개선하였다.

### BUG-52190 Non-AutoCommit 환경에서 SELECT 문 실행 순서에 따른 Lock 비정상 해제 문제 수정

-   **module** : sm
-   **Category** : Fatal
-   **Reproducibility** : Always
-   **Description** : Non-AutoCommit 모드에서 하나의 트랜잭션 내 여러 SELECT 문을 수행할 때, SELECT 문 실행 순서에 따라 IS_LOCK이 비정상적으로 해제되던 문제를 수정합니다.

### BUG-52219 SUPPLEMENTAL LOG 를 생성할 때 VARIABLE COLUMN 패딩을 고려해야 합니다.

-   **module** : sm
-   **Category** : Functional Error
-   **Reproducibility** : Always
-   **Description** : SUPPLEMENTAL LOG 를 생성할 때 VARIABLE COLUMN의 패딩 처리가 올바르게 처리되지 않아, UPDATE문 수행시 실패하던 문제를 수정하였습니다.

### BUG-52220 이중화 환경에서 LOB 컬럼과 SUPPLEMENTAL LOG가 설정된 디스크 테이블에 DROP COLUMN 구문 수행 시 서버 비정상 종료 문제 수정

-   **module** : sm
-   **Category** : Fatal
-   **Reproducibility** : Always
-   **Description** : LOB 컬럼과 SUPPLEMENTAL LOG가 설정된 디스크 테이블이 이중화(Replication)에 포함된 경우, DROP COLUMN 구문 수행 시 서버가 비정상 종료되던 문제를 수정하였습니다.

### BUG-52226 SQL_APPLY 모드에서 DELETE 로그 처리 시 standby 서버 비정상 종료 문제 수정

-   **module** : rp-receiver
-   **Category** : Fatal
-   **Reproducibility** : Always
-   **Description** : Supplemental Log가 설정된 테이블의 이중화 환경에서 standby 서버가 SQL_APPLY 모드로 동작할 때, DELETE 로그 처리 중 비정상 종료되는 문제를 수정합니다.

### BUG-52230 다른 사용자가 부여한 Role 권한을 SYS 계정에서 회수시에 The meta table crashed. 에러가 발생

-   **module** : qp-ddl-dcl-execute

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : 사용자 계정에서 생성한 Role에 객체 권한을 부여한 후, SYS 계정에서 해당 권한을 회수할 경우 [ERR-31015 : The meta table crashed.] 오류가 발생하던 문제를 수정합니다.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

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

  - **Actual Results**

    ```sql
    [ERR-31015 : The meta table crashed.
    0001 : revoke delete, insert, select, update on userA.T1 from R_userA
    ^ ^
    ]
    ```

  -   **Expected Results**

-   **Workaround**

        sys user가 권한을 주고 회수

### BUG-52262 구버전 클라이언트(6.1.1 이하) 연결 중 잘못된 프로토콜 헤더가 수신될 경우 서버가 비정상 종료되는 문제 수정

-   **module** : cm
-   **Category** : Fatal
-   **Reproducibility** : Rare
-   **Description** : 구버전 클라이언트(6.1.1 이하) 연결 중 잘못된 프로토콜 헤더 값이 수신되는 특정 상황에서 서버가 비정상 종료될 수 있는 문제를 수정하였습니다.

Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 7.1.0.10.8       | 6.5.1                   | 8.12.1       | 7.1.7               | 7.4.7                        |

> You can check the module version change history in [Version_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.1/Altibase_7_1_Version_Histories.md).

### Compatibility

#### Database binary version

The database binary version has not changed.

> The database binary version indicates the compatibility of database image files and log files. If this version needs to be patched to a different version, the database must be reorganized.

#### Meta Version

The meta version has not changed.

> If you want to roll back the patch after patching to a version with a changed meta version, see [Meta Downgrade](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/eng/Installation%20Guide.md#meta-downgrade).

#### CM protocol Version

The cm protocol version has not changed.

#### Replication protocol Version

The replication protocol version has not changed.

### Altibase Server Properties

No properties added/changed/deleted.

### Performance Views

No performance views added/changed/deleted.
