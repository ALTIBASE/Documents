# Altibase 7.1.0.7.3 Patch Notes

<br/>

<br/>

# **Table of Contents**  

- [New Features](#new-features)
  - [BUG-49580 메모리 테이블 또는 휘발성 메모리 테이블에 LOB 데이터 입력 시 과도한 메모리 사용을 개선합니다.](#bug-49580%EB%A9%94%EB%AA%A8%EB%A6%AC-%ED%85%8C%EC%9D%B4%EB%B8%94-%EB%98%90%EB%8A%94-%ED%9C%98%EB%B0%9C%EC%84%B1-%EB%A9%94%EB%AA%A8%EB%A6%AC-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90-lob-%EB%8D%B0%EC%9D%B4%ED%84%B0-%EC%9E%85%EB%A0%A5-%EC%8B%9C-%EA%B3%BC%EB%8F%84%ED%95%9C-%EB%A9%94%EB%AA%A8%EB%A6%AC-%EC%82%AC%EC%9A%A9%EC%9D%84-%EA%B0%9C%EC%84%A0%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49668 동시에 수행할 수 있는 디스크 트랜잭션의 최대 수(TRANSACTION\_SEGMENT\_COUNT 프로퍼티의 최대값)를 512에서 16384로 증가합니다.](#bug-49668%EB%8F%99%EC%8B%9C%EC%97%90-%EC%88%98%ED%96%89%ED%95%A0-%EC%88%98-%EC%9E%88%EB%8A%94-%EB%94%94%EC%8A%A4%ED%81%AC-%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98%EC%9D%98-%EC%B5%9C%EB%8C%80-%EC%88%98transaction_segment_count-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0%EC%9D%98-%EC%B5%9C%EB%8C%80%EA%B0%92%EB%A5%BC-512%EC%97%90%EC%84%9C-16384%EB%A1%9C-%EC%A6%9D%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
- [Fixed Bugs](#fixed-bugs)
  - [BUG-48065 DROP SEQUENCE 구문과 해당 시퀀스에 SELECT 구문을 동시에 수행하는 경우 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-48065drop-sequence-%EA%B5%AC%EB%AC%B8%EA%B3%BC-%ED%95%B4%EB%8B%B9-%EC%8B%9C%ED%80%80%EC%8A%A4%EC%97%90-select-%EA%B5%AC%EB%AC%B8%EC%9D%84-%EB%8F%99%EC%8B%9C%EC%97%90-%EC%88%98%ED%96%89%ED%95%98%EB%8A%94-%EA%B2%BD%EC%9A%B0-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-49505 복잡도가 높은 SQL문 수행 시 PREPARE\_STMT\_MEMORY\_MAXIMUM 초과로 SQL Plan Cache에 실행 계획을 등록하지 못한 경우 예외 처리를 추가합니다.](#bug-49505%EB%B3%B5%EC%9E%A1%EB%8F%84%EA%B0%80-%EB%86%92%EC%9D%80-sql%EB%AC%B8-%EC%88%98%ED%96%89-%EC%8B%9C-prepare_stmt_memory_maximum-%EC%B4%88%EA%B3%BC%EB%A1%9C-sql-plan-cache%EC%97%90-%EC%8B%A4%ED%96%89-%EA%B3%84%ED%9A%8D%EC%9D%84-%EB%93%B1%EB%A1%9D%ED%95%98%EC%A7%80-%EB%AA%BB%ED%95%9C-%EA%B2%BD%EC%9A%B0-%EC%98%88%EC%99%B8-%EC%B2%98%EB%A6%AC%EB%A5%BC-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49569 UNION ALL 연산자를 사용한 SELECT 문에서 select\_list 절에 LOB, GEOMETRY 또는 이진 데이터 타입이 사용된 경우 예외 처리를 추가합니다.](#bug-49569union-all-%EC%97%B0%EC%82%B0%EC%9E%90%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%9C-select-%EB%AC%B8%EC%97%90%EC%84%9C-select_list-%EC%A0%88%EC%97%90-lob-geometry-%EB%98%90%EB%8A%94-%EC%9D%B4%EC%A7%84-%EB%8D%B0%EC%9D%B4%ED%84%B0-%ED%83%80%EC%9E%85%EC%9D%B4-%EC%82%AC%EC%9A%A9%EB%90%9C-%EA%B2%BD%EC%9A%B0-%EC%98%88%EC%99%B8-%EC%B2%98%EB%A6%AC%EB%A5%BC-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49649 LOB 컬럼을 포함한 복제 트랜잭션 수행 시 Unable to find record in \~ 에러가 발생한 경우 수신자(Receiver)가 중지됩니다.](#bug-49649lob-%EC%BB%AC%EB%9F%BC%EC%9D%84-%ED%8F%AC%ED%95%A8%ED%95%9C-%EB%B3%B5%EC%A0%9C-%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98-%EC%88%98%ED%96%89-%EC%8B%9C-unable-to-find-record-in--%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%9C-%EA%B2%BD%EC%9A%B0-%EC%88%98%EC%8B%A0%EC%9E%90receiver%EA%B0%80-%EC%A4%91%EC%A7%80%EB%90%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49654 문자열을 포함한 CHECK 제약조건을 가진 테이블을 대상으로 이중화 객체 생성 후 이중화를 시작하면 ERR-31001 SQL syntax error 에러가 발생합니다.](#bug-49654%EB%AC%B8%EC%9E%90%EC%97%B4%EC%9D%84-%ED%8F%AC%ED%95%A8%ED%95%9C-check-%EC%A0%9C%EC%95%BD%EC%A1%B0%EA%B1%B4%EC%9D%84-%EA%B0%80%EC%A7%84-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%9D%84-%EB%8C%80%EC%83%81%EC%9C%BC%EB%A1%9C-%EC%9D%B4%EC%A4%91%ED%99%94-%EA%B0%9D%EC%B2%B4-%EC%83%9D%EC%84%B1-%ED%9B%84-%EC%9D%B4%EC%A4%91%ED%99%94%EB%A5%BC-%EC%8B%9C%EC%9E%91%ED%95%98%EB%A9%B4-err-31001-sql-syntax-error-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49661 디스크 임시 테이블스페이스를 사용하는 SQL문 수행 시 특정 상황에서 ERR-11069 : Internal server error in the storage manager ([FAILURE] ERR-110C1(error=11) The data file containing page [129832016] does not exist. 에러가 발생합니다.](#bug-49661%EB%94%94%EC%8A%A4%ED%81%AC-%EC%9E%84%EC%8B%9C-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%8A%A4%ED%8E%98%EC%9D%B4%EC%8A%A4%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94-sql%EB%AC%B8-%EC%88%98%ED%96%89-%EC%8B%9C-%ED%8A%B9%EC%A0%95-%EC%83%81%ED%99%A9%EC%97%90%EC%84%9C-err-11069--internal-server-error-in-the-storage-manager-failure-err-110c1error11-the-data-file-containing-page-129832016-does-not-exist-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [Database binary version](#database-binary-version)
    - [Meta Version](#meta-version)
    - [CM protocol Version](#cm-protocol-version)
    - [Replication protocol Version](#replication-protocol-version)
  - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [추가된 프로퍼티](#%EC%B6%94%EA%B0%80%EB%90%9C-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [변경된 프로퍼티](#%EB%B3%80%EA%B2%BD%EB%90%9C-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [삭제된 프로퍼티](#%EC%82%AD%EC%A0%9C%EB%90%9C-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
  - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)
    - [추가된 성능 뷰](#%EC%B6%94%EA%B0%80%EB%90%9C-%EC%84%B1%EB%8A%A5-%EB%B7%B0)
    - [변경된 성능 뷰](#%EB%B3%80%EA%B2%BD%EB%90%9C-%EC%84%B1%EB%8A%A5-%EB%B7%B0)
    - [삭제된 성능 뷰](#%EC%82%AD%EC%A0%9C%EB%90%9C-%EC%84%B1%EB%8A%A5-%EB%B7%B0)



New Features
============

### BUG-49580 메모리 테이블 또는 휘발성 메모리 테이블에 LOB 데이터 입력 시 과도한 메모리 사용을 개선합니다.

-   **module** : sm-mem-resource

-   **Category** : Other

-   **재현 빈도** : Always

-   **설명** : 메모리 테이블 또는 휘발성 메모리 테이블에 LOB 데이터 입력 시 LOB 정보를 관리하는 런타임 객체에서 메모리를 과도하게 사용하는 현상을 개선합니다.
    
    - 이 버그 현상 예시

      4G 크기의 LOB 데이터 입력 시 메모리 196G를 사용합니다. INSERT 진행 중 메모리를 과도하게 사용하다가 트랜잭션 종료 후 반납합니다.

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

### BUG-49668 동시에 수행할 수 있는 디스크 트랜잭션의 최대 수(TRANSACTION\_SEGMENT\_COUNT 프로퍼티의 최대값)를 512에서 16384로 증가합니다.

-   **module** : sm\_recovery

-   **Category** : Usability

-   **재현 빈도** : Always

-   **설명** : 디스크 테이블 트랜잭션의 성능 향상을 위해 동시에 수행할 수 있는 디스크 트랜잭션의 최대 수를 512에서 16384로 증가합니다. 
    
    관련 프로퍼티인 TRANSACTION\_SEGMENT\_COUNT의 최댓값과 속성이 변경되었습니다.
    
    - 최댓값이 512에서 16384로 변경되었습니다.
    - 프로퍼티의 속성이 '변경 가능'에서 '읽기 전용'으로 변경되었습니다.

    TRANSACTION\_SEGMENT\_COUNT 프로퍼티의 설정값이 900을 초과할 경우 언두 테이블스페이스의 세그먼트 헤더 정보를 저장한 별도의 파일(txSegEntry.hdr)이 생성됩니다. 이 파일에 위치는 언두 테이블스페이스의 데이터 파일과 같은 곳에 있으며 변경할 수 없습니다. txSegEntry.hdr에 관한 보다 자세한 내용은 매뉴얼을 참고하시기 바랍니다.

    - [Administrator's Manual - 6.테이블 스페이스 - 언두 테이블스페이스](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase\_7.1/kor/Administrator's%20Manual.md\#%EC%96%B8%EB%91%90-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%8A%A4%ED%8E%98%EC%9D%B4%EC%8A%A4)
    
    - [Administrator's Manual - 10. 백업 및 복구 - 데이터베이스 백업 - 범위에 따른 백업 분류](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase\_7.1/kor/Administrator's%20Manual.md\#%EB%B2%94%EC%9C%84%EC%97%90-%EB%94%B0%EB%A5%B8-%EB%B0%B1%EC%97%85-%EB%B6%84%EB%A5%98)
    
    - [Administrator's Manual - 10. 백업 및 복구 - 데이터베이스 백업 - 방식에 따른 백업 분류](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase\_7.1/kor/Administrator's%20Manual.md\#%EB%B0%A9%EC%8B%9D%EC%97%90-%EB%94%B0%EB%A5%B8-%EB%B0%B1%EC%97%85-%EB%B6%84%EB%A5%98)
    
-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
    
    -   Property
        -   TRANSACTION\_SEGMENT\_COUNT : 최대값이 900에서 16384로 증가
        
    -   Compile Option
    
    -   Error Code

Fixed Bugs
==========

### BUG-48065 DROP SEQUENCE 구문과 해당 시퀀스에 SELECT 구문을 동시에 수행하는 경우 Altibase 서버가 비정상 종료할 수 있습니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : DROP SEQUENCE 구문과 해당 시퀀스에 SELECT 구문을 동시에 수행하는 경우 Altibase 서버가 비정상 종료하는 현상을 수정합니다.
    
    아래 조건 중 하나라도 해당하면 이 버그에 노출되어 있습니다.
    
    - Altibase 7.1.0.1.2 \~ 7.1.0.7.0 버전
    
    - altibase.properties에 \_\_CATALOG\_SLOT\_REUSABLE = 1을 추가한 경우
    
-   **재현 방법**

    -   **재현 절차**

            CREATE SEQUENCE S1;
            -- SESSION 1
            declare
              cursor c1 is select s1.nextval from dual connect by level < 5;
              var1 integer;
            begin
              open c1;
              loop
                fetch c1 into var1;
                exit when c1%notfound;
                println(var1);
                sleep(10);
              end loop;
            end;
            /
            -- SESSION 2
            DROP SEQUENCE S1;

    -   **수행 결과**

            1234
            Execute success.

    -   **예상 결과**

            1
            [ERR-1107C : The sequence has already been dropped.at "SYS.ANONYMOUS_BLOCK", line 7]

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49505 복잡도가 높은 SQL문 수행 시 PREPARE\_STMT\_MEMORY\_MAXIMUM 초과로 SQL Plan Cache에 실행 계획을 등록하지 못한 경우 예외 처리를 추가합니다.

-   **module** : qp

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : 복잡도가 높은 SQL문 수행 시 PREPARE\_STMT\_MEMORY\_MAXIMUM 초과로 SQL Plan Cache에 실행 계획을 등록하지 못한 경우 Altibase 서버가 비정상 종료하는 현상을 수정합니다.
    
-   **재현 방법**

    -   **재현 절차**

            DROP TABLE BUG-49505;
             
            CREATE TABLE BUG-49505 
            ( 
              I1  INTEGER, 
              I2  INTEGER,
              I3  INTEGER, 
              I4  INTEGER,
              I5  INTEGER,
              I6  INTEGER, 
              I7  INTEGER, 
              I8  INTEGER,
              I9  INTEGER, 
              I10 INTEGER, 
              I11 INTEGER, 
              I12 GEOMETRY
            )
            PARTITION BY RANGE( I1 )
            ( 
              PARTITION P1 VALUES LESS THAN ( 10 ), 
              PARTITION P2 VALUES LESS THAN ( 20 ), 
              PARTITION P3 VALUES LESS THAN ( 30 ), 
              PARTITION P4 VALUES DEFAULT 
            );
             
            ALTER TABLE BUG-49505 MERGE PARTITIONS P2, P3 INTO PARTITION P3 ;
            ALTER TABLE BUG-49505 DROP PARTITION P1;
             
            SELECT COUNT(*) FROM ( SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 UNION ALL SELECT * FROM BUG-49505 );

    -   **수행 결과**

            Altibase 서버 비정상 종료 

    -   **예상 결과**

        동일 쿼리 첫 번째 수행 시 
        
            ERR-01067 : The memory size allocated for the statement has exceeded the maximum limit ( Name : Query_Prepare, Wanted Memory Size : 209719025, Max size : 209715200 ).
        
        동일 쿼리 재 수행 시
        
        ```
        COUNT(*)             
        -----------------------
        0                    
        1 row selected.
        ```
        
        

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49569 UNION ALL 연산자를 사용한 SELECT 문에서 select\_list 절에 LOB, GEOMETRY 또는 이진 데이터 타입이 사용된 경우 예외 처리를 추가합니다.

-   **module** : qp

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : UNION ALL 연산자를 사용한 SELECT 문에서 select\_list 절에 LOB, GEOMETRY, NIBBLE, BYTE, VARBYTE 데이터 타입 중 2가지를 같이 사용한 경우 Altibase 서버가 비정상 종료하거나 무한 대기하는 상황에 예외 처리를 추가하였습니다. 
    
    이 버그가 반영된 버전에서는 ERR-91022 : LOB and GEOMETRY type data cannot be displayed 또는 ERR-21043 : Unexpected errors may have occurred: mtvCalculate\_Blob2BlobLocator: not BLOB module 에러가 발생합니다.
    
-   **재현 방법**

    -   **재현 절차**

            DROP TABLE t1 CASCADE;
            DROP TABLE t2 CASCADE;
            CREATE TABLE t1( I1  BLOB );
            CREATE TABLE t2 ( I1 BYTE(12) );
            INSERT INTO t2 VALUES (1);
            SELECT i1 FROM t1 UNION ALL SELECT i1 FROM t2;

    -   **수행 결과**

            [ERR-91015 : Communication failure.]

    -   **예상 결과**

            [ERR-91022 : LOB and GEOMETRY type data cannot be displayed]

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49649 LOB 컬럼을 포함한 복제 트랜잭션 수행 시 Unable to find record in \~ 에러가 발생한 경우 수신자(Receiver)가 중지됩니다.

-   **module** : rp-receiver

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** :  LOB 컬럼을 포함한 복제 트랜잭션 수행 시 Unable to find record in \~ 에러가 발생한 경우 수신자(Receiver)가 중지되지 않고
    정상적으로 데이터 충돌 처리하도록 수정합니다. 
    
    이 버그 발생 시 수신자, 송신자에서 확인할 수 있는 현상입니다.
    
    - **수신자 측**
    
      트레이스 로그에 아래와 같은 에러가 남습니다.
    
      - **altibase\_rp\_conflict.log**
    
        ```
        ERR-610f7(errno=62) [Receiver] Unable to find record in ...
        ```
    
      - **altibase\_rp.log**
    
        ```
        ERR-610f7(errno=62) [Receiver] Unable to find record in openLOBCursor() function
        ERR-61048(errno=62) [Receiver] replication_name receiver has recvXLog error in run()
        [Receiver] RepName:replication_name is processed at ~ 
        [Receiver] RepName:replication_name is received at ~
        ERR-6104b(errno=62) [Receiver] replication_name receiver is ended(by thr_exit)
        Error Stop!
        [Receiver] Replication replication_name Stopped ...
        ```
    
    - **송신자 측**

      송신자 측에서 REPLICATION\_SENDER\_SLEEP\_TIMEOUT 프로퍼티 설정에 따라 재시작을 반복하지만 수신자 측에서 Unable to find record in openLOBCursor() function 에러로 수신자가 정상적으로 시작되지 않습니다 .이로 인해 이중화 갭이 발생합니다.

      트레이스 로그에 아래와 같은 에러가 남습니다.

      - **altibase\_rp.log**

        ```
        [SenderApply] Replication replication_name Start
        [Sender] Replication replication_name:0 Start... at[93025988]
        [SenderApply] Replication replication_name Got Error
        ERR-620f0(errno=11) [Sender] Stop sender thread replication_name:0 at [93027296], Restart SN[93025988]
        ERR-7101a(errno=16) Connection closed
        ERR-61022(errno=11) [Sender] Sender Sleep : 60 seconds
        ```

    이 버그가 반영된 버전에서는 LOB 컬럼을 포함한 복제 트랜잭션 수행 시 존재하지 않는 프라이머리 키 값인 경우 수신자 측 트레이스 로그 altibase\_rp\_conflict.log에 아래와 같은 형태의 로그가 남습니다.

    ```
    ERR-610f7(errno=16) [Receiver] Unable to find record in openLOBCursor() function
    A failure occurred while opening LOB Cursor (Table : ) (PK : ) ; (TID : ) COMMIT (TID : )
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

### BUG-49654 문자열을 포함한 CHECK 제약조건을 가진 테이블을 대상으로 이중화 객체 생성 후 이중화를 시작하면 ERR-31001 SQL syntax error 에러가 발생합니다.

-   **module** : rp-sender

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 문자열을 포함한 CHECK 제약조건을 가진 테이블을 대상으로 이중화 객체 생성 후 이중화를 시작하면 ERR-31001 SQL syntax error 에러가 발생하는 현상을 수정합니다.
    
    이 버그로 인한 ERR-31001 SQL syntax error 에러는 아래 3가지 상황에서 발생할 수 있습니다.

    - 문자열을 포함한 CHECK 제약조건을 가진 테이블을 대상으로 이중화 객체 생성 후 이중화를 시작하는 경우
    
      ALTER REPLICATION *replication\_name* START 수행 시 ERR-6104F : [Sender] Failed to initialize 에러 발생하며 altibase\_rp.log에 ERR-31001(errno=11) SQL syntax error 발생 
    
    - 문자열을 포함한 CHECK 제약조건을 가진 테이블을 이중화 객체에 추가하는 경우   

      ALTER REPLICATION *replication\_name* ADD TABLE 수행 시 ERR-31001 : SQL syntax error 에러 발생
    
    - 이중화 대상 테이블에 문자열을 포함한 CHECK 제약조건을 추가하는 경우 
      ALTER TABLE *table\_name* ADD CONSTRAINT *constraint\_name* CHECK 수행 시 altibase\_rp.log에 ERR-31001(errno=62) SQL syntax error가 발생하며 이중화 송신자가 중지
    
      이 상황이 발생하면 이중화 객체 삭제 후 재생성해야 합니다. 
    
-   **재현 방법**

    -   **재현 절차**

            CREATE TABLE RCSC_AUID
            (
               TS TIMESTAMP,
               AUID VARCHAR(96) not null,
               AUID_USE SMALLINT default 1,
               XDMS VARCHAR(8),
               XDMS_USE SMALLINT default 1,
               PRIMARY KEY (AUID)
            );
            
            ALTER TABLE RCSC_AUID 
            ADD CONSTRAINT RCSC_RCSC_AUID_CHECK_01 
            CHECK( XDMS in ('GMS', 'CMS', 'IdMS', 'KMS', 'PROXY') );
            
            ALTER REPLICATION REP1 START;

    -   **수행 결과**

            ERR-6104F : [Sender] Failed to initialize 에러 발생하며 altibase_rp.log에 ERR-31001(errno=11) SQL syntax error 발생 

    -   **예상 결과**

-   **Workaround**

        없음

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49661 디스크 임시 테이블스페이스를 사용하는 SQL문 수행 시 특정 상황에서 ERR-11069 : Internal server error in the storage manager ([FAILURE] ERR-110C1(error=11) The data file containing page [129832016] does not exist. 에러가 발생합니다.

-   **module** : sm

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 디스크 임시 테이블스페이스를 사용하는 SQL문 수행 시 특정 상황에서 ERR-11069 : Internal server error in the storage manager ([FAILURE] ERR-110C1(error=11) The data file containing page [129832016] does not exist. 에러가 발생하는 현상을 수정합니다.

    이 버그는 아래 조건을 모두 만족하는 경우 매우 낮은 확률로 발생합니다.

    - Altibase 7.1.0.5.7 이상

    - 디스크 템프 테이블 연산 중 HASH 연산 수행

    - HASH\_AREA\_SIZE 부족으로 디스크 임시 테이블스페이스을 사용하는 경우


    > 참고 : 디스크 테이블에 대한 질의 처리 과정에서 SORT/HASH 연산이 필요할 경우 빠른 연산을 위해 메모리에 일정 크기를 할당하여 사용한다. 만약 정해진 크기의 메모리를 모두 사용하고 SORT/HASH 연산을 위한 공간이 추가적으로 필요한 경우 디스크 임시 테이블스페이스를 사용한다.
    
    \_\_TEMPDUMP\_LEVEL 프로퍼티 설정값이 1인 경우 이 버그로 인한 현상이 발생하면 altibase\_dump.log에 아래와 같은 에러가 추가로 기록됩니다.
    
    ```
    [DUMP] ERR-110C1(error=11) The data file containing page [page_number] does not exist. ( Tablespace - ID : tablespace_id, Type : tablespace_type )
    DUMP TEMPTABLEHEADER: ..... 
    TEMP STATS:  ......
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

Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    7.1.0.7.3     |          6.5.1          |    8.10.1    |        7.1.7        |            7.4.7             |

> Altibase 7.1 패치 버전별 히스토리는 [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7_1_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

> 패치를 롤백하려는 경우, [메타다운그레이드](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Installation.md#%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9Cmeta-downgrade)를 참고한다.

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
