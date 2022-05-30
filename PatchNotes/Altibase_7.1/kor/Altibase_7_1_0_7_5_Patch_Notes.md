# Altibase 7.1.0.7.5 Patch Notes

<br/>

<br/>

# Table of Contents

- [Fixed Bugs](#fixed-bugs)
  - [BUG-48279 오프라인 이중화에서 DDL 로그를 처리할 때 송신자 메타 정보 파일을 업데이트하는 문제를 수정합니다.](#bug-48279%EC%98%A4%ED%94%84%EB%9D%BC%EC%9D%B8-%EC%9D%B4%EC%A4%91%ED%99%94%EC%97%90%EC%84%9C-ddl-%EB%A1%9C%EA%B7%B8%EB%A5%BC-%EC%B2%98%EB%A6%AC%ED%95%A0-%EB%95%8C-%EC%86%A1%EC%8B%A0%EC%9E%90-%EB%A9%94%ED%83%80-%EC%A0%95%EB%B3%B4-%ED%8C%8C%EC%9D%BC%EC%9D%84-%EC%97%85%EB%8D%B0%EC%9D%B4%ED%8A%B8%ED%95%98%EB%8A%94-%EB%AC%B8%EC%A0%9C%EB%A5%BC-%EC%88%98%EC%A0%95%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-48349 집합 연산자 중 INTERSECT 또는 MINUS를 사용한 SQL 문에 SET BUCKET COUNT 힌트가 적용되지 않습니다.](#bug-48349%EC%A7%91%ED%95%A9-%EC%97%B0%EC%82%B0%EC%9E%90-%EC%A4%91-intersect-%EB%98%90%EB%8A%94-minus%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%9C-sql-%EB%AC%B8%EC%97%90-set-bucket-count-%ED%9E%8C%ED%8A%B8%EA%B0%80-%EC%A0%81%EC%9A%A9%EB%90%98%EC%A7%80-%EC%95%8A%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-49642 테이블스페이스 삭제와 생성이 동시에 수행 중 Altibase 서버가 비정상 종료한 경우 재시작 복구(Restart Recovery)가 실패할 수 있습니다.](#bug-49642%ED%85%8C%EC%9D%B4%EB%B8%94%EC%8A%A4%ED%8E%98%EC%9D%B4%EC%8A%A4-%EC%82%AD%EC%A0%9C%EC%99%80-%EC%83%9D%EC%84%B1%EC%9D%B4-%EB%8F%99%EC%8B%9C%EC%97%90-%EC%88%98%ED%96%89-%EC%A4%91-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%9C-%EA%B2%BD%EC%9A%B0-%EC%9E%AC%EC%8B%9C%EC%9E%91-%EB%B3%B5%EA%B5%ACrestart-recovery%EA%B0%80-%EC%8B%A4%ED%8C%A8%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-49643 LOB 칼럼을 포함한 테이블에 BEFORE UPDATE 트리거 수행 시 예외 처리를 추가합니다.](#bug-49643lob-%EC%B9%BC%EB%9F%BC%EC%9D%84-%ED%8F%AC%ED%95%A8%ED%95%9C-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90-before-update-%ED%8A%B8%EB%A6%AC%EA%B1%B0-%EC%88%98%ED%96%89-%EC%8B%9C-%EC%98%88%EC%99%B8-%EC%B2%98%EB%A6%AC%EB%A5%BC-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49670 SQL Plan cache에 등록된 SQL 문 수행 중 Hard Parsing을 다시 진행할 때 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-49670sql-plan-cache%EC%97%90-%EB%93%B1%EB%A1%9D%EB%90%9C-sql-%EB%AC%B8-%EC%88%98%ED%96%89-%EC%A4%91-hard-parsing%EC%9D%84-%EB%8B%A4%EC%8B%9C-%EC%A7%84%ED%96%89%ED%95%A0-%EB%95%8C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-49682 함수 기반 인덱스(function-based index)에 인덱스 키와 다른 데이터 타입의 데이터가 입력되는 경우 예외 처리를 변경합니다.](#bug-49682%ED%95%A8%EC%88%98-%EA%B8%B0%EB%B0%98-%EC%9D%B8%EB%8D%B1%EC%8A%A4function-based-index%EC%97%90-%EC%9D%B8%EB%8D%B1%EC%8A%A4-%ED%82%A4%EC%99%80-%EB%8B%A4%EB%A5%B8-%EB%8D%B0%EC%9D%B4%ED%84%B0-%ED%83%80%EC%9E%85%EC%9D%98-%EB%8D%B0%EC%9D%B4%ED%84%B0%EA%B0%80-%EC%9E%85%EB%A0%A5%EB%90%98%EB%8A%94-%EA%B2%BD%EC%9A%B0-%EC%98%88%EC%99%B8-%EC%B2%98%EB%A6%AC%EB%A5%BC-%EB%B3%80%EA%B2%BD%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49686 ALTER REPLICAITOIN replication\_name BUILD OFFLINE META 수행 시 File read error 에러가 발생합니다.](#bug-49686alter-replicaitoin-replication_name-build-offline-meta-%EC%88%98%ED%96%89-%EC%8B%9C-file-read-error-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49690 ALTER REPLICATION replication\_name BUILD OFFLINE META 구문 수행 시 송신자 메타 파일 또는 Restart SN 파일이 유효하지 않을 경우 반환하는 에러 메시지를 개선합니다.](#bug-49690alter-replication-replication_name-build-offline-meta-%EA%B5%AC%EB%AC%B8-%EC%88%98%ED%96%89-%EC%8B%9C-%EC%86%A1%EC%8B%A0%EC%9E%90-%EB%A9%94%ED%83%80-%ED%8C%8C%EC%9D%BC-%EB%98%90%EB%8A%94-restart-sn-%ED%8C%8C%EC%9D%BC%EC%9D%B4-%EC%9C%A0%ED%9A%A8%ED%95%98%EC%A7%80-%EC%95%8A%EC%9D%84-%EA%B2%BD%EC%9A%B0-%EB%B0%98%ED%99%98%ED%95%98%EB%8A%94-%EC%97%90%EB%9F%AC-%EB%A9%94%EC%8B%9C%EC%A7%80%EB%A5%BC-%EA%B0%9C%EC%84%A0%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49696 증분 백업에서 언두 테이블스페이스의 세그먼트 헤더 정보 파일(txSegEntry.hdr) 백업 및 복원 기능을 추가합니다.](#bug-49696%EC%A6%9D%EB%B6%84-%EB%B0%B1%EC%97%85%EC%97%90%EC%84%9C-%EC%96%B8%EB%91%90-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%8A%A4%ED%8E%98%EC%9D%B4%EC%8A%A4%EC%9D%98-%EC%84%B8%EA%B7%B8%EB%A8%BC%ED%8A%B8-%ED%97%A4%EB%8D%94-%EC%A0%95%EB%B3%B4-%ED%8C%8C%EC%9D%BCtxsegentryhdr-%EB%B0%B1%EC%97%85-%EB%B0%8F-%EB%B3%B5%EC%9B%90-%EA%B8%B0%EB%8A%A5%EC%9D%84-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49697 오프라인 이중화에서 송신자 메타 파일 생성 과정을 개선하여 송신자 메타 파일 및 Restart SN 파일이 유실될 가능성을 방지합니다.](#bug-49697%EC%98%A4%ED%94%84%EB%9D%BC%EC%9D%B8-%EC%9D%B4%EC%A4%91%ED%99%94%EC%97%90%EC%84%9C-%EC%86%A1%EC%8B%A0%EC%9E%90-%EB%A9%94%ED%83%80-%ED%8C%8C%EC%9D%BC-%EC%83%9D%EC%84%B1-%EA%B3%BC%EC%A0%95%EC%9D%84-%EA%B0%9C%EC%84%A0%ED%95%98%EC%97%AC-%EC%86%A1%EC%8B%A0%EC%9E%90-%EB%A9%94%ED%83%80-%ED%8C%8C%EC%9D%BC-%EB%B0%8F-restart-sn-%ED%8C%8C%EC%9D%BC%EC%9D%B4-%EC%9C%A0%EC%8B%A4%EB%90%A0-%EA%B0%80%EB%8A%A5%EC%84%B1%EC%9D%84-%EB%B0%A9%EC%A7%80%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49706 iLoader in 성능 개선을 위해 CSV 파서를 최적화합니다.](#bug-49706iloader-in-%EC%84%B1%EB%8A%A5-%EA%B0%9C%EC%84%A0%EC%9D%84-%EC%9C%84%ED%95%B4-csv-%ED%8C%8C%EC%84%9C%EB%A5%BC-%EC%B5%9C%EC%A0%81%ED%99%94%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49708 ALTER TABLE 수행으로 디스크 테이블의 인덱스 재구성이 필요할 때 인덱스 활성화 상태를 확인합니다.](#bug-49708alter-table-%EC%88%98%ED%96%89%EC%9C%BC%EB%A1%9C-%EB%94%94%EC%8A%A4%ED%81%AC-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%9D%98-%EC%9D%B8%EB%8D%B1%EC%8A%A4-%EC%9E%AC%EA%B5%AC%EC%84%B1%EC%9D%B4-%ED%95%84%EC%9A%94%ED%95%A0-%EB%95%8C-%EC%9D%B8%EB%8D%B1%EC%8A%A4-%ED%99%9C%EC%84%B1%ED%99%94-%EC%83%81%ED%83%9C%EB%A5%BC-%ED%99%95%EC%9D%B8%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49721 이중화 대상 테이블에 내부적으로 테이블을 재생성하는 DDL 문 수행 시 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-49721%EC%9D%B4%EC%A4%91%ED%99%94-%EB%8C%80%EC%83%81-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90-%EB%82%B4%EB%B6%80%EC%A0%81%EC%9C%BC%EB%A1%9C-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%9D%84-%EC%9E%AC%EC%83%9D%EC%84%B1%ED%95%98%EB%8A%94-ddl-%EB%AC%B8-%EC%88%98%ED%96%89-%EC%8B%9C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
  - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
  - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)



Fixed Bugs
==========

### BUG-48279 오프라인 이중화에서 DDL 로그를 처리할 때 송신자 메타 정보 파일을 업데이트하는 문제를 수정합니다.

-   **module** : rp

-   **Category** : Functional Error

-   **재현 빈도** : Unknown

-   **설명** : 오프라인 이중화에서 DDL 로그를 처리할 때 송신자 메타 정보 파일을 업데이트하는 문제를 수정합니다.
    
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

### BUG-48349 집합 연산자 중 INTERSECT 또는 MINUS를 사용한 SQL 문에 SET BUCKET COUNT 힌트가 적용되지 않습니다.

-   **module** : qp

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : 집합 연산자 중 INTERSECT 또는 MINUS를 사용한 SQL 문에 SET BUCKET COUNT 힌트가 적용되지 않는 문제를 수정합니다.
    
-   **재현 방법**

    -   **재현 절차**

            DROP TABLE t1 CASCADE;
            DROP TABLE t2 CASCADE;
            CREATE TABLE t1(i1 INTEGER);
            CREATE TABLE t2(i1 INTEGER) ;
            ALTER SESSION SET EXPLAIN PLAN = ON;
            ALTER SESSION SET TRCLOG_DETAIL_PREDICATE = 1;
            # INTERSECT
            SELECT /*+ set bucket count (256) hash bucket count (512) */ i1 FROM t1 INTERSECT SELECT i1 FROM t2;
            # MINUS
            SELECT /*+ set bucket count (256) hash bucket count (512) */ i1 FROM t1 MINUS SELECT i1 FROM t2;

    -   **수행 결과**

        -   INTERSECT 연산자

            ```
            SELECT /*+ set bucket count (256) hash bucket count (512) */ i1 FROM t1 INTERSECT SELECT i1 FROM t2;
            ------------------------------------------------------------
            PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: 236.82 )
             VIEW ( ACCESS: 0, COST: 236.16 )
              SET-INTERSECT ( ITEM_SIZE: 24, ITEM_COUNT: 0, BUCKET_COUNT: 512, ACCESS: 0, COST: 236.16 )
               PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: 118.08 )
                SCAN ( TABLE: SYS.T1, FULL SCAN, ACCESS: 0, COST: 116.76 )
               PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: 118.08 )
                SCAN ( TABLE: SYS.T2, FULL SCAN, ACCESS: 0, COST: 116.76 )
            ------------------------------------------------------------
            ```

        -   MINUS 연산자

            ```
            SELECT /*+ set bucket count (256) hash bucket count (512) */ i1 FROM t1 MINUS SELECT i1 FROM t2;
            ------------------------------------------------------------
            PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: 236.82 )
             VIEW ( ACCESS: 0, COST: 236.16 )
              SET-DIFFERENCE ( ITEM_SIZE: 24, ITEM_COUNT: 0, BUCKET_COUNT: 512, ACCESS: 0, COST: 236.16 )
               PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: 118.08 )
                SCAN ( TABLE: SYS.T1, FULL SCAN, ACCESS: 0, COST: 116.76 )
               PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: 118.08 )
                SCAN ( TABLE: SYS.T2, FULL SCAN, ACCESS: 0, COST: 116.76 )
            -----------------------------------------------------------
            ```

    -   **예상 결과**

        -   INTERSECT 연산자

            ```
            SELECT /*+ set bucket count (256) hash bucket count (512) */ i1 FROM t1 INTERSECT SELECT i1 FROM t2;
            ------------------------------------------------------------
            PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: 236.82 )
             VIEW ( ACCESS: 0, COST: 236.16 )
              SET-INTERSECT ( ITEM_SIZE: 24, ITEM_COUNT: 0, BUCKET_COUNT: 256, ACCESS: 0, COST: 236.16 )
               PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: 118.08 )
                SCAN ( TABLE: SYS.T1, FULL SCAN, ACCESS: 0, COST: 116.76 )
               PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: 118.08 )
                SCAN ( TABLE: SYS.T2, FULL SCAN, ACCESS: 0, COST: 116.76 )
            ------------------------------------------------------------
            ```

        -   MINUS 연산자

            ```
            SELECT /*+ set bucket count (256) hash bucket count (512) */ i1 FROM t1 MINUS SELECT i1 FROM t2;
            ------------------------------------------------------------
            PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: BLOCKED )
             VIEW ( ACCESS: 0, COST: BLOCKED )
              SET-DIFFERENCE ( ITEM_SIZE: BLOCKED, ITEM_COUNT: 0, BUCKET_COUNT: 256, ACCESS: 0, COST: BLOCKED )
               PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: BLOCKED )
                SCAN ( TABLE: SYS.T1, FULL SCAN, ACCESS: 0, COST: BLOCKED )
               PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: BLOCKED )
                SCAN ( TABLE: SYS.T2, FULL SCAN, ACCESS: 0, COST: BLOCKED )
            ------------------------------------------------------------
            ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49642 테이블스페이스 삭제와 생성이 동시에 수행 중 Altibase 서버가 비정상 종료한 경우 재시작 복구(Restart Recovery)가 실패할 수 있습니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : 테이블스페이스 삭제와 생성이 동시에 수행 중 Altibase 서버가 비정상 종료한 경우 Altibase 서버 구동 시 재시작 복구(Restart
    Recovery)가 실패하는 현상을 수정합니다.
    
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

### BUG-49643 LOB 칼럼을 포함한 테이블에 BEFORE UPDATE 트리거 수행 시 예외 처리를 추가합니다.

-   **module** : qp-psm-trigger-execute

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : LOB 칼럼을 포함한 테이블에 BEFORE UPDATE 트리거 수행 시 Altibase 서버가 비정상 종료하는 현상을 수정하고 BEFORE UPDATE 트리거에 LOB 컬럼 관련한 제약 사항을 추가합니다.
    
-   **재현 방법**

    -   **재현 절차**

            DROP TABLE T1;
            DROP TABLE T2;
             
            CREATE TABLE T1( I1 INTEGER, I3 CLOB ) ;
            CREATE TABLE T2( I1 INTEGER, I2 VARCHAR(10) );
             
            CREATE OR REPLACE TRIGGER TRIG1 
            BEFORE 
            UPDATE ON T1  
            REFERENCING NEW AS NEW_ROW OLD AS OLD_ROW 
            FOR EACH ROW 
            BEGIN :NEW_ROW.I1 := 100; 
            INSERT INTO T2 VALUES( :OLD_ROW.I1, 'OLD' ); 
            INSERT INTO T2 VALUES( :NEW_ROW.I1, 'NEW' ); 
            END;
            /
             
            INSERT INTO T1 SELECT LEVEL, LEVEL FROM DUAL CONNECT BY LEVEL <= 1;
            UPDATE T1 SET I1=I1+1;

    -   **수행 결과**

            ERR-91015 : Communication failure. 

    -   **예상 결과**

            ERR-3112F : Unsupported data type for parameter, RETURN, or local variable. LOB columns are not supported.

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49670 SQL Plan cache에 등록된 SQL 문 수행 중 Hard Parsing을 다시 진행할 때 Altibase 서버가 비정상 종료할 수 있습니다.

-   **module** : qp

-   **Category** : Fatal

-   **재현 빈도** : Unknown

-   **설명** : SQL Plan Cache에 등록된 SQL 문 수행 중 바인드 변수 변경 등으로 Hard Parsing을 다시 진행할 때 Check-In PCO 과정에서 메모리 동시성 오류로 Altibase 서버가 비정상 종료하는 현상을 수정합니다.
    
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

### BUG-49682 함수 기반 인덱스(function-based index)에 인덱스 키와 다른 데이터 타입의 데이터가 입력되는 경우 예외 처리를 변경합니다.

-   **module** : qp-non\_select

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : 함수 기반 인덱스(function-based index)에 인덱스 키와 다른 데이터 타입의 데이터가 입력되는 경우 Altibase 서버가 비정상 종료할 수 있습니다. 에러 메시지를 반환하도록 예외 처리를 변경합니다.
    
-   **재현 방법**

    -   **재현 절차**

            DROP TABLE T3;
            CREATE TABLE T3( I1 INTEGER, I2 VARCHAR(10) ) TABLESPACE SYS_TBS_DISK_DATA;
            CREATE INDEX T3_IDX11 ON T3( I1+1, I2+1 ) ;
            ALTER SESSION SET ARITHMETIC_OPERATION_MODE = 0;
            INSERT INTO T3 VALUES ( 5, 3 );

    -   **수행 결과**

            [ERR-91015 : Communication failure.]

    -   **예상 결과**

            iSQL> INSERT INTO T3 VALUES ( 5, 3 );
            [ERR-314AD : An error occurred while applying a value with an unexpected data type to the function-based index.]

-   **Workaround**

        ALTER SESSION SET ARITHMETIC_OPERATION_MODE = 1;

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code
        
        에러 메시지가 추가되었습니다. 
        
        ```
        0x314AD ( 201901) qpERR_ABORT_QMC_INVALID_FUNCTION_BASED_INDEX An error occurred while applying a value with an unexpected data type to the function-based index. 
        # *Cause: The specified value does not match the data type of the function-based index column.
        # *Action: Rebuild the function-based index and retry.
        ```
        
        

### BUG-49686 ALTER REPLICAITOIN replication\_name BUILD OFFLINE META 수행 시 File read error 에러가 발생합니다.

-   **module** : rp-jdbcAdapter

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : *ala\_replication\_name*\_META\_NEW.bin 또는 *ala\_replication\_name*\_SN\_NEW.bin 파일이 비정상적인 경우, ALTER
    REPLICAITOIN *replication\_name* BUILD OFFLINE META 수행 시 File read error 에러가 발생하는 현상을 수정합니다. OLD라는 이름을 가진 백업 파일이 정상적이면 백업 파일을 읽어 BUILD OFFLINE META를 수행합니다.
    
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

### BUG-49690 ALTER REPLICATION replication\_name BUILD OFFLINE META 구문 수행 시 송신자 메타 파일 또는 Restart SN 파일이 유효하지 않을 경우 반환하는 에러 메시지를 개선합니다.

-   **module** : rp-oraAdapter

-   **Category** : Usability

-   **재현 빈도** : Always

-   **설명** : ALTER REPLICATION replication\_name BUILD OFFLINE META 구문 수행 시 송신자 메타 파일 또는 Restart SN 파일이 유효하지 않을 경우 반환하는 에러 메시지를 개선합니다.
    
    송신자 메타 파일(*replication\_name*\_META\_NEW.bin, *replication\_name*\_META\_OLD.bin)이 모두 유효하지 않으면 ERR-611B3
    : Invalid sender meta files. (Replication name: *replication\_name*, File name: *replication\_name*\_META\_NEW.bin, 
    *replication\_name*\_META\_OLD.bin ) 에러를, Restart SN 파일이 모두 유효하지 않을 경우 ERR-611B4 : Invalid Restart SN files.
    (Replication name: *replication\_name*, File name: *replication\_name*\_SN\_NEW.bin, *replication\_name*\_SN\_OLD.bin )
    에러를 반환하도록 수정하였습니다.
    
-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

        - 송신자 메타 파일(replication_name_META_NEW.bin, replication_name_META_OLD.bin)이 모두 유효하지 않을 때

          ```
          ERR-611B3 : There is no valid meta file.
          ```

        - Restart SN 파일이 모두 유효하지 않을 때

          ```
          ERR-611B4 : There is no valid sn file.
          ```

    -   **예상 결과**

        -   송신자 메타 파일(replication_name_META_NEW.bin, replication_name_META_OLD.bin)이 모두 유효하지 않을 때
        
            ```
            ERR-611B3 : Invalid sender meta files. (Replication name: replication_name, File name: replication_name_META_NEW.bin, replication_name_META_OLD.bin )
            ```
        
        -   Restart SN 파일이 모두 유효하지 않을 때
        
            ```
            ERR-611B4 : Invalid Restart SN files. (Replication name: replication_name, File name: replication_name_SN_NEW.bin, replication_name_SN_OLD.bin )
            ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code
        -   에러 메시지가 추가되었습니다.

            ```
            0x611B3 ( 397747) rpERR_ABORT_ERR_NO_VALID_METAFILE Invalid sender meta files. (Replication name: <0%s>, File name: <1%s>_META_NEW.bin, <2%s>_META_OLD.bin ) 
            # *Cause:
            # - Sender meta files do not exist or are invalid.
            # *Action:
            # - 'BUILD OFFLINE META' failed. Verify the altibase_rp.log.
            
            0x611B4 ( 397748) rpERR_ABORT_ERR_NO_VALID_SNFILE Invalid Restart SN files. (Replication name: <0%s>, File name: <1%s>_SN_NEW.bin, <2%s>_SN_OLD.bin ) 
            # *Cause:
            # - Restart SN files do not exist or are invalid.
            # *Action:
            # - 'BUILD OFFLINE META' failed. Verify the altibase_rp.log.
            ```
            


### BUG-49696 증분 백업에서 언두 테이블스페이스의 세그먼트 헤더 정보 파일(txSegEntry.hdr) 백업 및 복원 기능을 추가합니다.

-   **module** : sm-disk-page

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 증분 백업에서 언두 테이블스페이스의 세그먼트 헤더 정보 파일(txSegEntry.hdr) 백업 및 복원 기능을 추가합니다.
    
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

### BUG-49697 오프라인 이중화에서 송신자 메타 파일 생성 과정을 개선하여 송신자 메타 파일 및 Restart SN 파일이 유실될 가능성을 방지합니다.

-   **module** : rp-oraAdapter

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 오프라인 이중화에서 송신자 메타 파일 생성 과정을 개선하여 송신자 메타 파일 및 Restart SN 파일이 유실될 가능성을 방지합니다.
    
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

### BUG-49706 iLoader in 성능 개선을 위해 CSV 파서를 최적화합니다.

-   **module** : ux-iloader

-   **Category** : Efficiency

-   **재현 빈도** : Always

-   **설명** : iLoader in 성능 개선을 위해 불필요한 memcpy 제거 및 CSV 파서를 최적화합니다.
    
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

### BUG-49708 ALTER TABLE 수행으로 디스크 테이블의 인덱스 재구성이 필요할 때 인덱스 활성화 상태를 확인합니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : ALTER TABLE 수행 시 비활성화 상태의 인덱스가 있으면 Altibase 서버가 비정상 종료하는 현상을 수정합니다. ALTER TABLE ~ ADD COLUMN 처럼 내부적으로 테이블의 인덱스를 재구성해야 할 때 이 현상이 발생합니다. 
    이 버그는 디스크 테이블에서만 발생합니다.

-   **재현 방법**

    -   **재현 절차**

            DROP TABLE T1;
            CREATE TABLE T1 ( I1 INTEGER, I2 INTEGER, I3 INTEGER ) TABLESPACE SYS_TBS_DISK_DATA;
            ALTER TABLE T1 ALL INDEX DISABLE;
            CREATE INDEX IDX5 ON T1(I2, I3);
            ALTER TABLE T1 ADD COLUMN ( C3 VARCHAR(10) FIXED, C4 VARCHAR(10) VARIABLE );

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49721 이중화 대상 테이블에 내부적으로 테이블을 재생성하는 DDL 문 수행 시 Altibase 서버가 비정상 종료할 수 있습니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : 이중화 대상 테이블에 내부적으로 테이블을 재생성하는 DDL 문 수행 시 Altibase 서버가 비정상 종료하는 현상을 수정합니다. 

    이 버그는 이중화 환경에서 REPLICATION_DDL_ENABLE = 1 설정하고 운영할 때 Active 서버에서 이 현상이 발생할 수 있으며 DDL 복제 기능을 사용하면 복제 트랜잭션이 발생하는 노드에서도 발생할 수 있습니다. 

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
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    7.1.0.7.5     |          6.5.1          |    8.10.1    |        7.1.7        |            7.4.7             |

> Altibase 7.1 패치 버전별 히스토리는 [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.1/Altibase_7_1_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

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
