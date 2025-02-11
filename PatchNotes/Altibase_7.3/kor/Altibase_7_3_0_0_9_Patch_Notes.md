Altibase 7.3.0.0.9 Patch Notes
================================

New Features
------------

### BUG-51057 Updateable Dynaset 지원

-   **module** : mm-win-odbc

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : Updateable Dynaset 지원을 위해 ODBC 드라이버가 개선되었습니다.

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

### BUG-51068 KEYSET DRIVEN 커서의 읽기 성능 개선

-   **module** : mm-cli

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : SQL_CURSOR_KEYSET_DRIVEN 커서로 select를 수행할 때 서버-클라이언트간 통신 횟수(fetch 프로토콜)를 줄여 성능을 개선했습니다.
    
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

### BUG-51199 Red Hat Linux 9 지원

-   **module** : id

-   **Category** : Portability

-   **재현 빈도** : Unknown

-   **설명** :  glibc 2.34 이상의 환경에서 발생하던 호환성 문제가
    해결되었습니다. 이제 Red Hat Linux 9 에서도 Altibase를 사용할 수
    있습니다.

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

### BUG-51204 이중화 DDL 동작 개선

-   **module** : rp
-   **Category** : Other
-   **재현 빈도** : Always
-   **설명** : 
    -   이중화 대상 테이블에 ADD TABLE 시 오류 수정
        -   이중화 갭이 존재하는 상태에서 이중화 대상 테이블에 ADD TABLE을 수행할 때, **[ERR-11058 : The row already exists in a unique index.]** 에러로 실패하는 문제가 해결되었습니다.

    -   이중화 대상 테이블에 SPLIP/MERGE PARTITION 후 사용자가 신규로 생성된 파티션을 DROP하는 경우의 오동작을 수정합니다.
    -   이중화 대상 테이블에 SPLIT/MERGE/DROP PARTITION 의 DDL을 수행할때 동작 변경
        -   LOCK TABLE ... IN EXCLUSIVE MODE UNTIL NEXT DDL 구문을 사용하지 않아도 이중화 대상인 테이블에 SPLIT/MERGE/DROP PARTITION이 수행 가능하게 수정 되었습니다. 

        -   이중화 테이블에 DROP PARTITION을 수행할 때, 기존에는 삭제할 PARTITION의 값을 이중화한 후 DROP PARTITION이 수행되었는데, 이제 DROP PARTITION의 값은 이중화를 포기하도록 수정되었습니다.
    -   이중화의 부가옵션으로 META LOGGING 기능 추가
        -   기존에는 ALA(Altibase Log Analyzer)에서만 사용가능하던 META LOGGING 옵션이, 이제 일반 이중화에서도 사용하도록 개선되었습니다. 이 기능의 추가됨에 따라 dbms_metadata 패키지의 업데이트가 필요합니다. 
    
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

### BUG-50178 증분 백업을 사용할 때 데드락 상황을 방지하도록 개선되었습니다.

-   **module** : sm\_resource

-   **Category** : Hang

-   **재현 빈도** : Always

-   **설명** : 증분 백업을 사용할 때 데드락 상황을 방지하도록 개선되었습니다.

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

### BUG-50757 증분 백업에서 extend 와 change tracking 이 동시에 수행되는 경우 서버가 비정상 종료할 수 있습니다.

-   **module** : sm\_resource

-   **Category** : Fatal

-   **재현 빈도** : Frequence

-   **설명** : 증분 백업에서 extend 와 change tracking 이 동시에 수행되는 경우 서버가 비정상 종료하는 문제를 수정했습니다.

-   **재현 방법**

    -   **재현 절차**

            insert into t0 values (...)
            alter database backup incremental level 0 database with tag '1';

    -   **수행 결과**

            insert into t0 values (...)
            success.
            alter database backup incremental level 1 database with tag '1';
            [ERR-50032 : Client unable to establish connection. (Failed to invoke the connect() system function, errno=111)]

    -   **예상 결과**

            insert into t0 values (...)
            success.
            alter database backup incremental level 0 database with tag '1';
            Alter success.

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50867 테이블스페이스를 오프라인으로 변경하는 로직에 오류가 있습니다.

-   **module** : sm\_collection

-   **Category** : Fatal

-   **재현 빈도** : Rare

-   **설명** : 테이블스페이스를 오프라인으로 변경하는 로직의 오류를 수정합니다.

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

### BUG-50978 트리거 생성시 권한 검사 로직의 오류를 수정합니다.

-   **module** : qp-ddl-dcl-execute

-   **Category** : Reliability

-   **재현 빈도** : Always

-   **설명** : 트리거 생성시 권한 검사 로직의 오류를 수정합니다.

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

### BUG-51048 SQL_CURSOR_KEYSET_DRIVEN 커서로 SQLExecute, SQLFetch를 반복 수행하는 경우, 맨 처음 레코드만 반환됩니다.

-   **module** : mm-cli

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : SQL_CURSOR_KEYSET_DRIVEN 커서로 SQLExectue, SQLFetch를 반복 수행하는 경우, 내부 오류로 인해 잘못된 데이터가 반환되는 문제를 수정하였습니다.
    
    또한 Fetch 과정에서 에러가 발생해도 사용자에게 성공을 반환하는 오류도 함께 수정하였습니다.
    
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
        -   추가
            - **ERR-51229 Failed to add the PROWID to the hash table.**
            - **Cause**: Failed to add the PROWID to the hash table due to an internal error.
            - **Action**: Contact Altibase's Support Center ([http://support.altibase.com](http://support.altibase.com/)).

### BUG-51050 트리거가 설정된 테이블에서 다중 테이블 갱신(Multiple Table Update)을 수행하는 경우, 잘못된 메모리에 접근할 수 있습니다.

-   **module** : qp

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : 트리거가 설정된 테이블에 다중 테이블 갱신을 수행하는 경우 잘못된 메모리에 접근할 수 있는 문제가 해결되었습니다.

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

### BUG-51056 Volatile 테이블에서 inplace update 수행 로직의 오류를 수정합니다.

-   **module** : sm\_page

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : Volatile 테이블에서 inplace update 수행 로직의 오류를 수정합니다.

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

### BUG-51063 메모리 인덱스가 존재하는 테이블에서 inplace update 수행시 오류를 수정합니다.

-   **module** : sm-mem-index

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : 메모리 인덱스가 존재하는 테이블에서 inplace update 수행시, 일부 레코드가 갱신되지 않거나 잘못된 레코드가 갱신되는 오류를 수정합니다.

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

### BUG-51065 이중화 SQL 반영 모드일때, 파티션 SPLIT 전 수행한 DELETE 문이 이중화되지 않습니다.

-   **module** : rp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 이중화 SQL 반영 모드에서 이중화 대상 테이블의 특정 행(row)을 삭제한 후 해당 파티션을 SPLIT하는 경우, 특정 행 삭제 명령이 이중화되지 않아 데이터 정합성 문제가 발생하는 현상을 수정하였습니다.
    
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

### BUG-51118 서버 설치시 지정한 Transaction log directory경로(LOG\_DIR)가 altibase.properties 파일에 반영되지 않습니다.

-   **module** : installer

-   **Category** : Usability

-   **재현 빈도** : Always

-   **설명** : 서버 설치시 지정한 Transaction log
    directory경로(LOG\_DIR)가 altibase.properties 파일에 반영되지 않는
    문제를 수정합니다.

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

### BUG-51133 SQL의 Prepare 단계에서 생성된 메모리를 해제하는 과정에서 잘못된 메모리 참조의 오류로 서버가 비정상 종료 할 수 있습니다.

-   **module** : qp-select

-   **Category** : Enhancement

-   **재현 빈도** : Impossible

-   **설명** : SQL의 Prepare 단계에서 생성된 메모리를 해제하는 과정에서 잘못된 메모리 참조의 오류가 발생할 경우, 오류를 출력하도록 수정하였습니다.
    
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

### BUG-51138 iloader 에서 1개 파일이 2,147,483,647 건을 초과하는 데이터를 export/import 수행할 경우 발생하는 오동작문제를 개선합니다.

-   **module** : ux-iloader

-   **Category** : Functional Error

-   **재현 빈도** : Always

- **설명** : iloader로 2,147,483,647 건을 초과하는 데이터를 export 수행시 오류없이 종료되는 문제가 있었습니다. 또한 2,147,483,647 건을 초과하는 데이터를 import 수행시 2,147,483,647 건만 import되고, 오류없이 종료되는 문제가 있었습니다.

  iloader로 export/import 할때 처리가능한 데이터 건수는 2,147,483,647 건으로, 이를 초과하는 데이터를 export/import 수행할 경우 아래의 에러메시지를 출력하도록 개선되었습니다.

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
        -   추가
            - **[ERR-9114A : The datafile (data.txt) exceeded the maximum** **record limit (2,147,483,647), causing iLoader to terminate.]**
            - **Cause** : The datafile contains more records than the allowed limit (2,147,483,647).
            - **Action** : Split the datafile into smaller files and retry.

### BUG-51144 COLLECT_DBMS_STATS를 ON으로 설정한 후 aexport를 수행할 때, ERR-31014 : Index not found 오류가 발생하는 경우가 있습니다.

-   **module** : ux-aexport

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : COLLECT_DBMS_STATS를 ON으로 설정한 상태에서 aexport를 수행할 때 발생하던 문제를 수정했습니다. 테이블 소유자와 인덱스 소유자가 다른 경우, 인덱스 통계 정보를 추출하는 과정에서 **[ERR-31014: Index not found]** 오류가 발생했습니다. 이로 인해 aexport가 비정상적으로 종료되는 문제가 있었으며, 이를 개선하여 정상적으로 처리되도록 수정했습니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    CREATE USER alti IDENTIFIED BY test;
    CONNECT alti/test
    DROP TABLE t1;
    CREATE TABLE t1 (c1 INTEGER, c2 CHAR(10), c3 CHAR(10));
    CREATE INDEX t1_idx1 ON t1 (c1);
    
    CONNECT sys/manager
    CREATE INDEX alti.t1_idx2 ON alti.t1 (c2);
    CREATE INDEX t1_idx3 ON alti.t1 (c3);
    exec gather_database_stats(0.1,10,false);
    
    // aexport.properties 파일에서 COLLECT_DBMS_STATS = ON 설정
    
    $ aexport -u sys -p manager -s localhost
    ```

  - **수행 결과**

        ##### TBS #####
        
        ##### USER  #####
        ** input user ALTI's password(default - same with USER_NAME):
        
        ##### SYNONYM #####
        
        ##### DIRECTORY #####
        
        ##### TABLE #####
        ** "ALTI"."T1"
        ... query[EXEC GET_INDEX_STATS('"ALTI"', '"T1_IDX1"', NULL, ?, ?, ?, ?, ?, ?,                          ?)]
        ... query[EXEC GET_INDEX_STATS('"ALTI"', '"T1_IDX2"', NULL, ?, ?, ?, ?, ?, ?,                          ?)]
        ... query[EXEC GET_INDEX_STATS('"ALTI"', '"T1_IDX3"', NULL, ?, ?, ?, ?, ?, ?,                          ?)]
        [ERR-31014 : Index not found]

  -   **예상 결과**

          오류없이 정상동작

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-51154 특정 상황에서 FULL OUTER JOIN 사용시 DB Hang 문제 수정

-   **module** : qp-select-pvo

-   **Category** : Hang

-   **재현 빈도** : Always

-   **설명** : 특정 상황에서 FULL OUTER JOIN을 사용하는 쿼리에서 DB HANG 문제가 발생하여, 수정하였습니다.

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

### BUG-51158 Prepared Statement 의 batchUpdate를 사용하여 CLOB 칼럼 처리 중 **[ERR-110C5: LobCursor already closed]** 오류가 발생하는 문제를 수정합니다.

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : Prepared Statement를 사용하여 CLOB 컬럼에 대해 executeUpdate()를 연속으로 수행하는 과정에서 Primary Key 중복으로 인한 오류 등의 서버 에러가 발생하면, 그 다음 executeUpdate()에서 **[ERR-110C5: LobCursor already closed]** 오류가 발생하던 문제를 수정했습니다.

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

### BUG-51160 jdbcAdapter 를 이용하여 Oracle 에 데이터 입력할 때, executeBatch() 함수를 수행하는 과정에서 오류가 발생했을 때의 동작 개선

-   **module** : rp-jdbcAdapter

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : Batch DML 수행 중 오류가 발생했을 때, 오류가 발생한 DML과 처리되지 않은 DML을 로그에 출력하도록 개선합니다. 또한, BatchUpdateException.getUpdateCounts() 메소드를 통해 가져온 배열의 값이 SUCCESS_NO_INFO 일 경우 오류 로그를 출력하지 않도록 개선합니다.
    
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

### BUG-51163 2,147,483,647 보다 큰 TableOID 값을 가지는 테이블을 ALTER REPLICATION ... ADD TABLE 구문으로 이중화 대상 테이블에 추가할 때, ERR-21010 Value overflow 오류가 발생합니다.

-   **module** : rp
-   **Category** : Functional Error
-   **재현 빈도** : Rare
-   **설명** : 2,147,483,647 보다 큰 TableOID 값을 가지는 테이블을 이중화 대상 테이블에 추가할 때, **[ERR-21010 Value overflow]** 오류로 실패하는 문제를 수정하였습니다.
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

### BUG-51165 Prepared Statement 의 batchUpdate를 사용하여 CLOB 칼럼 처리 중, updatedRowCount가 0인 파라미터 세트가 포함될 경우의 동작을 개선합니다.

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : Prepared Statement 의 batchUpdate를 사용하여 CLOB 칼럼 처리 중, updatedRowCount가 0인 파라미터 세트가 포함될 경우의 동작을 개선합니다.

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

### BUG-51203 V$DISK_UNDO_USAGE와 같은 모니터링 쿼리에 대한 조회가 장시간 수행되는 경우의 동작을 개선합니다.

-   **module** : sm-disk-collection

-   **Category** : Enhancement

-   **재현 빈도** : Rare

-   **설명** :  V\$DISK\_UNDO\_USAGE와 같은 모니터링 쿼리에 대한 조회가
    장시간 수행되는 경우 세션 확인 기능이 추가되었습니다. 이제 Session
    Timeout이 발생하거나 session close 명령으로 세션이 종료되도록
    개선되었습니다. 그외 아래의 성능뷰에도 동일하게 적용하였습니다.

    -   V\$DATABASE
    -   V\$DATAFILES
    -   V\$LOCK\_WAIT
    -   V\$MEMTBL\_INFO
    -   V\$TABLESPACES
    -   V\$TSSEGS

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

### BUG-51214 SYS 계정으로 개별 오브젝트에 대한 권한 부여시 에러가 발생합니다.

-   **module** : qp-ddl-dcl-pvo

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : SYS 계정으로 개별 오브젝트에 대한 권한 부여시 에러가 발생하는 문제를 수정합니다.
    수정

- **재현 방법**

  - **재현 절차**

    ```sql
    connect sys/manager;
    Create user ccj identified by ccj;
    create user alti identified by alti;
    
    connect ccj/ccj;
    create table t1 (c1 int primary key,c2 int);
    
    connect sys/manager;
    grant select on ccj.t1 to alti;
    ```

  -   **수행 결과**

          [ERR-313D8 : The user has insufficient privileges.]

  -   **예상 결과**

          Success

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-51216 내부적으로 익스텐트 리스트 탐색 시 리스트 순회가 종료되지 않을 수 있는 현상에 대한 수정

-   **module** : sm-disk-collection

-   **Category** : Enhancement

-   **재현 빈도** : Rare

-   **설명** : 내부적으로 익스텐트 리스트 탐색 시 리스트 순회가 종료되지
    않을 경우, 에러메시지를 출력하도록 개선되었습니다.

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
        -   추가
            - **Failed to traverse the extent directory list of segment.**
            - **Cause** : Concurrency conflict may occur when retrieving and updating the Extent Directory Page List simultaneously.
            - **Action**: Retry the operation. If the error persists, please contact Altibase support.

### BUG-51281 DBMS\_METADATA 패키지에 META\_LOGGING에 관한 구문을 추가해야 합니다.

-   **module** :

-   **Category** : Other

-   **재현 빈도** : Always

-   **설명** :

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
| 7.3.0.0.9        | 7.3.0                   | 9.4.1        | 7.1.8               | 7.4.9                        |

> Altibase 7.3 패치 버전별 히스토리는 [Version_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.3/Altibase_7_3_Version_Histories.md) 에서 확인할 수 있다.

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

#### 추가된 프로퍼티

#### 변경된 프로퍼티

#### 삭제된 프로퍼티

### 성능 뷰

#### 추가된 성능 뷰

#### 변경된 성능 뷰

#### 삭제된 성능 뷰
