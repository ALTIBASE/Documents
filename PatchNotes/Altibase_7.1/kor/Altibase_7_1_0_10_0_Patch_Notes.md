Altibase 7.1.0.10.0 Patch Notes
================================

New Features
============

### BUG-48885 통계 잠금 기능 추가

-   **module** : sm

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : 테이블의 통계를 잠글 수 있는 기능이 추가되었습니다.
    DBMS\_STATS 패키지에 LOCK\_TABLE\_STATS, UNLOCK\_TABLE\_STATS
    프로시저가 추가되었습니다. 이 프로시저를 이용하여 테이블의 통계를
    잠그거나 잠금을 해제할 수 있습니다.

    만약, 통계 잠금 기능일 설정된 테이블에 대해 GATHER\_TABLE\_STATS 로
    통계 자료 수집을 요청할 경우, **[ERR-111C9 Table statistic(s) are
    locked.]**를 확인할 수 있다.

-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    - Performance view
    
      -   V$LOCK_TABLE_STATS 추가
    
          - 설명: 테이블 통계 잠금 상태를 보여주는 뷰
    
          - 칼럼 정보
    
            | Column name | Type       | Description                                                  |
            | ----------- | ---------- | ------------------------------------------------------------ |
            | TABLE_OID   | BIGINT     | 테이블 객체 식별자                                           |
            | STAT_LOCKED | VARCHAR(6) | 테이블 통계 잠금 여부 -NONE: 통계 잠금 해제 상태 -LOCKED: 통계 잠금 상태 |
    
    - Property
    
    - Compile Option
    
    - Error Code
    
      -   추가
          - **[ERR-111C9 Table statistic(s) are locked.]**
          - **Cause**: Table statistic(s) have been locked.
          - **Action**: Find the table whose statistic(s) are locked and then unlock the table using the UNLOCK_TABLE_STATS procedure.

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

-   **설명** : glibc 3.34 이상의 환경에서 발생하던 호환성 문제가 해결되었습니다. 이제 Red Hat Linux 9 에서도 Altibase를 사용할 수 있습니다.  

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

### BUG-50650 체크포인트 수행 중 내부적으로 Memory recovery LSN이 갱신되지 않은 상태에서 서버가 종료된 경우, 서버 재시작에 실패할 수 있습니다.

-   **module** : sm-mem-recovery

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : 체크포인트 수행 중에 더티 페이지가 체크포인트 이미지
    파일에 기록된 후 Memory recovery LSN이 갱신되기 전에 서버가
    종료되면, 서버 재구동 시 복구에 실패하여 재시작이 실패하는 문제가
    있었습니다. 이를 수정하여 Memory recovery LSN이 갱신되기 전에
    서버가 종료되더라도, 서버 재 구동 시 정상적으로 복구가 진행되도록
    개선하였습니다.

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

    -   **수행 결과**
    
    -   **예상 결과**
    
-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50867 테이블스페이스를 오프라인으로 변경하는 로직의 오류를 수정합니다.

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

### BUG-51012 SQLColumns함수에서 SchemaName(스키마 이름) 인자에 NULL이 전달될 경우, 잘못된 데이터가 반환됩니다.

-   **module** : mm-cli

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : SQLColumns함수에서 SchemaName(스키마 이름) 인자에 NULL이 전달될 경우, 잘못된 데이터가 반환되는 문제를 수정합니다.
    
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

### BUG-51013 ODBC 드라이버를 이용하여 다이너셋(dynaset) 테스트를 수행할 때, Altibase 데이터베이스에 연결이 성공했으나 다이너셋을 지원하지 않는다는 오류가 발생합니다.

-   **module** : mm-cli

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : ODBC 드라이버를 이용하여 다이너셋 테스트를 수행할 때, Altibase 데이터베이스에 연결이 성공했으나 다이너셋을 지원하지 않는다는 오류가 발생하는 문제를 해결했습니다.
    
    SQLGetInfo 함수에서 SCROLL_OPTIONS, SCROLL_CONCURRENCY 의 매개변수가 전달될 때, 내부 로직에서 누락된 값이 있어 올바르게 동작하도록 수정했습니다.
    
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
-   **설명** : V$DISK_UNDO_USAGE와 같은 모니터링 쿼리에 대한 조회가 장시간 수행되는 경우 세션 확인 기능이 추가되었습니다. 이제 Session Timeout이 발생하거나 session close 명령으로 세션이 종료되도록 개선되었습니다. 그외 아래의 성능뷰에도 동일하게 적용하였습니다. 
    -   V$DATABASE
    -   V$DATAFILES
    -   V$LOCK_WAIT
    -   V$MEMTBL_INFO
    -   V$TABLESPACES
    -   V$TSSEGS

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

### BUG-51041  디스크 테이블에서 DML 을 수행하는 중에 내부적으로테이블 정보를 기록하는 페이지가 깨진 경우, 서버가 비정상 종료되는 문제가 있습니다.

-   **module** : sm

-   **Category** : Enhancement

-   **재현 빈도** : Unknown

-   **설명** : 디스크 테이블에서 DML을 수행하는 중에 내부적으로 테이블
    정보를 기록하는 페이지가 깨진 경우, 페이지 덤프와 같이 분석 가능한
    정보를 기록하고 예외가 발생하도록 수정되었습니다.

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
            -   **ERR-51229 Failed to add the PROWID to the hash table.**
            -   **Cause**: Failed to add the PROWID to the hash table due to an internal error.
            -   **Action**: Contact Altibase's Support Center ([http://support.altibase.com](http://support.altibase.com/)).

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

### BUG-51063 메모리 인덱스가 존재하는 테이블에서 inplace update 수행시  오류를 수정합니다.

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

### BUG-51138 iloader 에서 1개 파일이 2,147,483,647 건을 초과하는 데이터를 export/import 수행시 오류메시지를 출력하도록 개선되었습니다.

-   **module** : ux-iloader

-   **Category** : Functional Error

-   **재현 빈도** : Always

- **설명** : iloader로 2,147,483,647 건을 초과하는 데이터를 export 수행시 오류없이 종료되는 문제가 있었습니다. 또한 2,147,483,647 건을 초과하는 데이터를 import 수행시  2,147,483,647 건만 import되고, 오류없이 종료되는 문제가 있었습니다. 

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
            -   **[ERR-9114A : The datafile (data.txt) exceeded the maximum**
                **record limit (2,147,483,647), causing iLoader to terminate.]**
            -   **Cause** : The datafile contains more records than the allowed limit (2,147,483,647).
            -   **Action** : Split the datafile into smaller files and retry.

### BUG-51144 COLLECT_DBMS_STATS를 ON으로 설정한 후 aexport를 수행할 때, ERR-31014 : Index not found 오류가 발생하는 경우가 있습니다.

-   **module** : ux-aexport

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : COLLECT_DBMS_STATS를 ON으로 설정한 상태에서 aexport를 수행할 때 발생하던 문제를 수정했습니다. 테이블 소유자와 인덱스 소유자가 다른 경우, 인덱스 통계 정보를 추출하는 과정에서 **[ERR-31014: Index not found]** 오류가 발생했습니다. 이로 인해 aexport가 비정상적으로 종료되는 문제가 있었으며, 이를 개선하여 정상적으로 처리되도록 수정했습니다.
    
- **재현 방법**

  -   **재현 절차**

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

### BUG-51158 Prepared Statement 의 batchUpdate를 사용하여 CLOB 칼럼 처리 중 **[ERR-110C5: LobCursor already closed]** 오류가 발생하는 문제를 수정합니다.

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : Prepared Statement의 batchUpdate를 사용하여 CLOB 컬럼에 대해 `executeUpdate()`를 수행하는 과정에서 Primary Key 중복으로 인한 오류 메시지를 확인한 후, 동일한 `executeUpdate()`를 다시 호출하면 **[ERR-110C5: LobCursor already closed]** 오류가 발생하던 문제를 수정했습니다. 이제 중복된 레코드에 대해서는 올바르게 **ERR-11058: The row already exists in a unique index.** 오류가 발생하도록 수정되었습니다.

-   **재현 방법**
    -   **재현 절차**
    
    -   **수행 결과**
    
    -   **예상 결과**
    
-   **Workaround**

-   **변경사항**

    -   Performance view
        -   PreparedStatement의 setXXX 메서드(setNull, setObject 등)에서
            targetSqlType을 java.sql.Types.CLOB 또는
            java.sql.Types.BLOB으로 지정하고 executeUpdate를 연속으로
            수행하는 경우, 첫 번째 executeUpdate에서 서버 에러가
            발생하면 두 번째 executeUpdate에서 (내부적으로 동일한 LOB
            업데이트가 두 번 수행되면서 정상적으로 업데이트는
            되었지만) "LobCursor  already closed" 에러가 발생함.

    -   Property
    -   Compile Option
    -   Error Code

### BUG-51160 jdbcAdapter 를 이용하여 Oracle 에 데이터 입력할 때, executeBatch() 함수를 수행하는 과정에서 오류가 발생했을 때의 동작 개선

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

### BUG-51165 Prepared Statement 의 batchUpdate를 사용하여 CLOB 칼럼 처리 중, updatedRowCount가 0인 파라미터 세트가 포함되면 잘못된 동작이 발생합니다.

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : Prepared Statement 의 batchUpdate를 사용하여 CLOB 칼럼 처리 중, updatedRowCount가 0인 파라미터 세트가 포함될 경우의 동작을 개선합니다.

-   **재현 방법**

    - **재현 절차**

      **수행 결과**

      **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
        
    -   Property
    -   Compile Option
    -   Error Code

### BUG-51189 이중화 DDL 의 동작 변경

-   **module** : rp

-   **Category** : Other

-   **재현 빈도** : Always

-   **설명** : LOCK TABLE ... IN EXCLUSIVE MODE UNTIL NEXT DDL 구문을 사용하지 않아도 이중화 대상인 테이블에 SPLIT/MERGE/DROP PARTTION이 수행 가능하게 수정 되었습니다. 또한, 이중화 테이블에 DROP PARTITION을 수행할 때, 기존에는 삭제할 PARTITION의 값을 이중화한 후 DROP PARTITION이 수행되었는데, 이제 DROP PARTITION의 값은 이중화를 포기하도록 수정되었습니다.
    
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
    
-   **재현 방법**

    -   **재현 절차**

            connect sys/manager;
            Create user ccj identified by ccj;
            create user alti identified by alti;
            
            connect ccj/ccj;
            create table t1 (c1 int primary key,c2 int);
            
            connect sys/manager;
            grant select on ccj.t1 to alti;
        
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

-   **설명** : 내부적으로 익스텐트 리스트 탐색 시 리스트 순회가 종료되지 않을 경우, 에러메시지를 출력하도록 개선되었습니다.

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
            -    **Failed to traverse the extent directory list of segment.**
            -   **Cause** : Concurrency conflict may occur when retrieving and updating the Extent Directory Page List simultaneously.
            -   **Action**: Retry the operation. If the error persists, please contact Altibase support.

Changes
-------

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 7.1.0.10.0       | 6.5.1                   | 8.12.1       | 7.1.7               | 7.4.7                        |

> Altibase 7.1 패치 버전별 히스토리는 [Version_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.1/Altibase_7_1_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의
> 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는
> 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전이 8.11.1 에서 8.12.1로 변경되었습니다.

> 패치를 롤백하려는 경우, [메타다운그레이드](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Installation%20Guide.md#%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9Cmeta-downgrade)를 참고한다.

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
