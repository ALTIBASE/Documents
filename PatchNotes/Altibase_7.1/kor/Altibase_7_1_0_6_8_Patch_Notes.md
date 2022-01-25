# Table of Contents  

- [New Features](#new-features)
  - [BUG-49486 EXTRACT 함수에 오라클 문법을 추가 지원합니다.](#bug-49486extract-%ED%95%A8%EC%88%98%EC%97%90-%EC%98%A4%EB%9D%BC%ED%81%B4-%EB%AC%B8%EB%B2%95%EC%9D%84-%EC%B6%94%EA%B0%80-%EC%A7%80%EC%9B%90%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49525 LISTAGG 함수가 반환하는 VARCHAR 타입의 크기를 설정하는 Altibase 서버 프로퍼티를 추가합니다.](#bug-49525listagg-%ED%95%A8%EC%88%98%EA%B0%80-%EB%B0%98%ED%99%98%ED%95%98%EB%8A%94-varchar-%ED%83%80%EC%9E%85%EC%9D%98-%ED%81%AC%EA%B8%B0%EB%A5%BC-%EC%84%A4%EC%A0%95%ED%95%98%EB%8A%94-altibase-%EC%84%9C%EB%B2%84-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0%EB%A5%BC-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
- [Fixed Bugs](#fixed-bugs)
  - [BUG-48650 메모리 인덱스 탐색 중 타임아웃 발생 시 인덱스가 정상임에도 트레이스 로그 altibasese\_sm.log에 'A timeout occured during index fetch. Index [index name] link error is suspected.' 에러 메시지가 발생합니다.](#bug-48650%EB%A9%94%EB%AA%A8%EB%A6%AC-%EC%9D%B8%EB%8D%B1%EC%8A%A4-%ED%83%90%EC%83%89-%EC%A4%91-%ED%83%80%EC%9E%84%EC%95%84%EC%9B%83-%EB%B0%9C%EC%83%9D-%EC%8B%9C-%EC%9D%B8%EB%8D%B1%EC%8A%A4%EA%B0%80-%EC%A0%95%EC%83%81%EC%9E%84%EC%97%90%EB%8F%84-%ED%8A%B8%EB%A0%88%EC%9D%B4%EC%8A%A4-%EB%A1%9C%EA%B7%B8-altibasese_smlog%EC%97%90-a-timeout-occured-during-index-fetch-index-index-name-link-error-is-suspected-%EC%97%90%EB%9F%AC-%EB%A9%94%EC%8B%9C%EC%A7%80%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49365 이중화 대상 테이블에 DDL 수행 및 ALTER REPPLICATIN ~ ADD TABLE 수행 이후 "The row already exists in a unique index." 에러가 발생하며 이중화 Sender가 중단됩니다.](#bug-49365-%EC%9D%B4%EC%A4%91%ED%99%94-%EB%8C%80%EC%83%81-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90-ddl-%EC%88%98%ED%96%89-%EB%B0%8F-alter-repplicatin--add-table-%EC%88%98%ED%96%89-%EC%9D%B4%ED%9B%84-the-row-already-exists-in-a-unique-index-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%98%EB%A9%B0-%EC%9D%B4%EC%A4%91%ED%99%94-sender%EA%B0%80-%EC%A4%91%EB%8B%A8%EB%90%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49373 REMOTE\_TABLE 또는 REMOTE\_TABLE\_STORE 키워드로 조회한 CHAR/VARCHAR 타입의 데이터를 로컬 DB에 입력 시 invalid data type length 에러가 발생합니다.](#bug-49373remote_table-%EB%98%90%EB%8A%94-remote_table_store-%ED%82%A4%EC%9B%8C%EB%93%9C%EB%A1%9C-%EC%A1%B0%ED%9A%8C%ED%95%9C-charvarchar-%ED%83%80%EC%9E%85%EC%9D%98-%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%A5%BC-%EB%A1%9C%EC%BB%AC-db%EC%97%90-%EC%9E%85%EB%A0%A5-%EC%8B%9C-invalid-data-type-length-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49476 트랜잭션 커밋 수행 시 예외 처리 부족으로 Altibase 서버가 비정상 종료하는 현상을 분석하기 위해 디버그 로그를 추가합니다.](#bug-49476%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98-%EC%BB%A4%EB%B0%8B-%EC%88%98%ED%96%89-%EC%8B%9C-%EC%98%88%EC%99%B8-%EC%B2%98%EB%A6%AC-%EB%B6%80%EC%A1%B1%EC%9C%BC%EB%A1%9C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%98%EB%8A%94-%ED%98%84%EC%83%81%EC%9D%84-%EB%B6%84%EC%84%9D%ED%95%98%EA%B8%B0-%EC%9C%84%ED%95%B4-%EB%94%94%EB%B2%84%EA%B7%B8-%EB%A1%9C%EA%B7%B8%EB%A5%BC-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49489 CLOB 컬럼에 setObject 메소드에서 VARCHAR 타입으로 32000바이트를 초과하는 데이터를 입력한 경우 Invalid size of data to bind to a host variable 에러가 발생합니다.](#bug-49489clob-%EC%BB%AC%EB%9F%BC%EC%97%90-setobject-%EB%A9%94%EC%86%8C%EB%93%9C%EC%97%90%EC%84%9C-varchar-%ED%83%80%EC%9E%85%EC%9C%BC%EB%A1%9C-32000%EB%B0%94%EC%9D%B4%ED%8A%B8%EB%A5%BC-%EC%B4%88%EA%B3%BC%ED%95%98%EB%8A%94-%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%A5%BC-%EC%9E%85%EB%A0%A5%ED%95%9C-%EA%B2%BD%EC%9A%B0-invalid-size-of-data-to-bind-to-a-host-variable-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49527 SQL 수행 중 하나의 문장(statement)에서 필요한 임시 테이블스페이스의 익스텐트(Extent) 수가 128 배수인 경우 The tablespace does not have enough free space 에러가 발생할 수 있습니다.](#bug-49527sql-%EC%88%98%ED%96%89-%EC%A4%91-%ED%95%98%EB%82%98%EC%9D%98-%EB%AC%B8%EC%9E%A5statement%EC%97%90%EC%84%9C-%ED%95%84%EC%9A%94%ED%95%9C-%EC%9E%84%EC%8B%9C-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%8A%A4%ED%8E%98%EC%9D%B4%EC%8A%A4%EC%9D%98-%EC%9D%B5%EC%8A%A4%ED%85%90%ED%8A%B8extent-%EC%88%98%EA%B0%80-128-%EB%B0%B0%EC%88%98%EC%9D%B8-%EA%B2%BD%EC%9A%B0-the-tablespace-does-not-have-enough-free-space-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-49530 Altibase 서버 운용 중 비정상 종료 발생 시 코어 덤프가 생성되는 현상을 방지합니다.](#bug-49530altibase-%EC%84%9C%EB%B2%84-%EC%9A%B4%EC%9A%A9-%EC%A4%91-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C-%EB%B0%9C%EC%83%9D-%EC%8B%9C-%EC%BD%94%EC%96%B4-%EB%8D%A4%ED%94%84%EA%B0%80-%EC%83%9D%EC%84%B1%EB%90%98%EB%8A%94-%ED%98%84%EC%83%81%EC%9D%84-%EB%B0%A9%EC%A7%80%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49532 LEFT OUTER JOIN 왼쪽이 집합 연산을 포함한 인라인 뷰이고 ON 절의 AND 조건에 SUBQUERY가 포함된 경우 Altibase 서버가 비정상 종료합니다.](#bug-49532left-outer-join-%EC%99%BC%EC%AA%BD%EC%9D%B4-%EC%A7%91%ED%95%A9-%EC%97%B0%EC%82%B0%EC%9D%84-%ED%8F%AC%ED%95%A8%ED%95%9C-%EC%9D%B8%EB%9D%BC%EC%9D%B8-%EB%B7%B0%EC%9D%B4%EA%B3%A0-on-%EC%A0%88%EC%9D%98-and-%EC%A1%B0%EA%B1%B4%EC%97%90-subquery%EA%B0%80-%ED%8F%AC%ED%95%A8%EB%90%9C-%EA%B2%BD%EC%9A%B0-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49538 임시 테이블스페이스를 사용하는 SQL문 수행 시 Altibase 서버가 비정상 종료, Internal server error 에러 또는 결과 오류가 발생할 수 있습니다.](#bug-49538%EC%9E%84%EC%8B%9C-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%8A%A4%ED%8E%98%EC%9D%B4%EC%8A%A4%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94-sql%EB%AC%B8-%EC%88%98%ED%96%89-%EC%8B%9C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C-internal-server-error-%EC%97%90%EB%9F%AC-%EB%98%90%EB%8A%94-%EA%B2%B0%EA%B3%BC-%EC%98%A4%EB%A5%98%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
  - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
  - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-49486 EXTRACT 함수에 오라클 문법을 추가 지원합니다.

-   **module** : mt

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : EXTRACT 함수에 아래와 같은 오라클 문법을 추가합니다.

    ```sql
    EXTRACT( date_field_name FROM expression )
    ```

    *date\_field\_name* 은 오라클과 공통되는 YEAR, MONTH, DAY, HOUR, MINUTE, SECOND에 한하여 지원합니다.

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

### BUG-49525 LISTAGG 함수가 반환하는 VARCHAR 타입의 크기를 설정하는 Altibase 서버 프로퍼티를 추가합니다.

-   **module** : mt

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : LISTAGG 함수의 반환 데이터 크기를 설정하는 Altibase 서버 프로퍼티 LISTAGG\_PRECISION를 추가합니다.
    
    LISTAGG 함수가 반환하는 VARCHAR 타입의 크기 제약으로 반환 데이터 크기가 4000바이트를 초과하는 경우 ERR-21061 : result of string concatenation is too long. 에러가 발생합니다. 
    
    LISTAGG\_PRECISION 프로퍼티로 1바이트부터 VARCHAR 최대 크기 32000바이트까지 반환할 수 있습니다.
    
-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
        -   LISTAGG\_PRECISION 프로퍼티 추가

            ##### 데이터 타입

            Unsigned Integer

            ##### 기본값

            4000

            ##### 속성

            변경 가능, 단일 값

            ##### 값의 범위

            [0, 32000]

            ##### 설명

            이 프로퍼티는 LISTAGG 함수가 반환하는 VARCHAR 타입의 크기를 지정한다.

            Altibase 운영 중에 ALTER SYSTEM 구문으로 이 프로퍼티의 값을 변경할 수 있다.

    -   Compile Option
-   Error Code

Fixed Bugs
==========

### BUG-48650 메모리 인덱스 탐색 중 타임아웃 발생 시 인덱스가 정상임에도 트레이스 로그 altibasese\_sm.log에 'A timeout occured during index fetch. Index [index name] link error is suspected.' 에러 메시지가 발생합니다.

-   **module** : sm-mem-index

-   **Category** : Message Error

-   **재현 빈도** : Rare

-   **설명** : 메모리 인덱스 탐색 중 타임아웃 발생 시 인덱스가 정상임에도 트레이스 로그 altibasese\_sm.log에 'A timeout occured
    during index fetch. Index [*index name*] link error is suspected.' 에러 메시지가 발생하는 현상을 수정합니다.
    
    인덱스가 손상된 경우 SQL 수행이 실패하고 altibase\_sm.log에 "The Maximum number of loops alllowed is over 1000001. Index [*인덱스명*] link error is suspected." 에러 메시지를 출력하도록 변경합니다.

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

### BUG-49365 이중화 대상 테이블에 DDL 수행 및 ALTER REPPLICATIN ~ ADD TABLE 수행 이후 "The row already exists in a unique index." 에러가 발생하며 이중화 Sender가 중단됩니다. 

-   **module** : rp-control

-   **Category** : Usability

-   **재현 빈도** : Rare

-   **설명** : 

-   REPLICATION_DDL_ENABLE = 1 설정한 이중화 환경에서, 아래 2가지 작업을 순차적으로 수행한 이후에 ERR-11058 에러 발생하며 이중화가 중지되는 현상을 수정합니다.  

    1. 이중화 대상 테이블에 DDL 수행
    2. ALTER REPLICATION ~ ADD TABLE 수행. (ADD TABLE 대상은 DDL을 수행한 테이블 뿐 아니라 이중화 대상 테이블은 모두 해당)

    이 버그 현상 발생 시 altibase_rp.log에 아래와 같은 로그가 출력됩니다. 

    ERR-11058(errno=0) The row already exists in a unique index.
    ERR-610f8(errno=0) [Sender] Failed to add a XLog [TID:-1603452059, SN:133280338892, Type:2, Log Type:1, Change Log Type:0]
    ERR-61014(errno=0) [Sender] Failed to make XLOG in a log file at SN[133280338892]

    이 버그 현상 발생 시 이중화 객체를 DROP 후 재생성해야 합니다. 

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

### BUG-49373 REMOTE\_TABLE 또는 REMOTE\_TABLE\_STORE 키워드로 조회한 CHAR/VARCHAR 타입의 데이터를 로컬 DB에 입력 시 invalid data type length 에러가 발생합니다.

-   **module** : dblink

-   **Category** : Usability

-   **재현 빈도** : Always

-   **설명** : REMOTE\_TABLE 또는 REMOTE\_TABLE\_STORE 키워드로 조회한 CHAR/VARCHAR 타입의 데이터를 로컬 DB에 입력 시 invalid data type length 에러가 발생하는 현상을 수정합니다.
    
    본 버그는 아래 조건을 모두 만족할 때 발생합니다.

    - DB Link 사용

    - 지역 데이터베이스 캐릭터셋으로 한 글자 크기가 2바이트 이상인 캐릭터셋 사용

    - 지역과 원격 데이터베이스에 CHAR/VARCHAR 데이터 타입을 포함한 동일한 스키마 생성
    
    - 원격 데이터베이스에서 REMOTE\_TABLE 또는 REMOTE\_TABLE\_STORE 키워드를 사용하여 CHAR/VARCHAR 타입의 데이터 조회
    
    - 조회한 CHAR/VARCHAR 타입의 데이터를 CURSOR를 사용하여 지역 데이터베이스에 입력

    본 버그에서 지역 서버와 원격 서버 데이터베이스 간 CHAR 또는 VARCHAR 타입의 데이터 길이 변환 방식를 개선하면서 AltiLinker 프로퍼티 [NLS\_BYTE\_PER\_CHAR](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/DB%20Link%20User's%20Manual.md#targetsnls_byte_per_char)를 추가하였습니다. 추가적인 내용은 [Database Link User’s Manual - 3.데이터베이스 링크 환경 설정 - 환경 설정 - 문자 집합(Character Set)](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/DB%20Link%20User's%20Manual.md#%EB%AC%B8%EC%9E%90-%EC%A7%91%ED%95%A9character-set) 을 참고하세요.
    
-   **재현 방법**

    -   **재현 절차**

        ```sql
        local:
        CREATE TABLE DBLINK_TEST(ID NUMBER, TEST_DT CHAR(8), TEST_DT2 VARCHAR(8));
        INSERT INTO DBLINK_TEST values(1,'20211001','20211101');
        
        remote:
        CREATE TABLE DBLINK_TEST(ID NUMBER, TEST_DT CHAR(8), TEST_DT2 VARCHAR(8));
        INSERT INTO DBLINK_TEST values(1,'20211001','20211101');
        INSERT INTO DBLINK_TEST values(2,'20211002','20211102');
        CREATE OR REPLACE PROCEDURE SP_DBLINK_TEST
        AS
        CURSOR CUR1 IS
         SELECT * FROM REMOTE_TABLE(link1,'SELECT * FROM DBLINK_TEST WHERE ID = ''2''');
        BEGIN
         FOR M IN CUR1
          LOOP
           PRINTLN(length(M.TEST_DT));
           PRINTLN(length(M.TEST_DT2));
           INSERT INTO DBLINK_TEST VALUES(M.ID, M.TEST_DT, M.TEST_DT2);
          END LOOP;
        END;
        -- 결과
        iSQL> exec SP_DBLINK_TEST();
        16
        8
        [ERR-21069 : Invalid data type length : TEST_DT.
        In SP_DBLINK_TEST
        0012 :    INSERT INTO DBLINK_TEST VALUES(M.ID, M.TEST_DT, M.TEST_DT2);
        ```

    -   **수행 결과**

            insert success

    -   **예상 결과**

-   **Workaround**

        substring()을 씌워서 사용하거나 varchar 타입을 사용함

-   **변경사항**

    -   Performance view
    -   Property
        -   AltiLinker 프로퍼티 [TARGETS/NLS\_BYTE\_PER\_CHAR](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/DB%20Link%20User's%20Manual.md#targetsnls_byte_per_char) 추가
    -   Compile Option
-   Error Code

### BUG-49476 트랜잭션 커밋 수행 시 예외 처리 부족으로 Altibase 서버가 비정상 종료하는 현상을 분석하기 위해 디버그 로그를 추가합니다.

-   **module** : sm

-   **Category** : Other

-   **재현 빈도** : Unknown

-   **설명** : 트랜잭션 커밋 수행 시 예외 처리 부족으로 Altibase 서버가 비정상 종료하는 현상을 분석하기 위해 디버그 로그를 추가합니다.
    
    트레이스 로그 altibase\_error.log 에 콜스택과 트랜잭션 정보를 남깁니다.
    
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

### BUG-49489 CLOB 컬럼에 setObject 메소드에서 VARCHAR 타입으로 32000바이트를 초과하는 데이터를 입력한 경우 Invalid size of data to bind to a host variable 에러가 발생합니다.

-   **module** : mm-jdbc

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : Apache NiFi 1.12.1 이하 버전에서 CLOB 데이터 입력 시 Invalid size of data to bind to a host variable 에러가 발생하는
    현상을 조치하기 위한 버그입니다.
    
    setObject(int, Object, Types.VARCHAR)에서 VARCHAR 데이터가 최대 크기 32000바이트를 초과할 경우 CLOB으로 처리하도록 지원합니다. 이 버그에서 지원하는 적용하려면 JDBC 연결 속성 force_clob_bind를 활성화하고 LOB 데이터 처리를 위해 Non-Autocommit 모드로 설정해야 합니다. Non-Autocommit 모드가 아닌 경우 LobLocator cannot span the transaction 에러가 발생할 수 있습니다. LOB 데이터 처리 관련 내용은 [JDBC User’s Manual - 3.고급 기능 - LOB](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_trunk/kor/JDBC%20User's%20Manual.md#lob) 부분을 참고하세요. 
    
    이 버그는 특정 상황에서 발생하는 현상을 조치하기 위한 것으로 JDBC 연결 속성 force_clob_bind에 관한 설명을 JDBC User's Manual에 추가하지 않습니다.
    
-   **재현 방법**

    -   **재현 절차**

            iSQL>CREATE TABLE t1 (c1 int, c2 clob);
            Connection sConn = getConnection();
            PreparedStatement sPstmt = sConn.prepareStatement("INSERT INTO t1 VALUES (?, ?)");
            sPstmt.setInt(1, 1);
            sPstmt.setObject(2, "very long text...", Types.VARCHAR);  
            sPstmt.addBatch();
            sPstmt.executeBatch();
            sConn.commit();

    -   **수행 결과**

        ```java
        java.sql.BatchUpdateException: Batch update exception occurred:Invalid size of data to bind to a host variable [ Param ID = 7, Data Type = MTD_VARCHAR, Data Size = 42954, Declared Size of Host Variable = 32002 ]
        ```

    -   **예상 결과**

            insert without error

-   **Workaround**

        PreparedStatement.setObject(int, Object, Types.CLOB); 사용

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49527 SQL 수행 중 하나의 문장(statement)에서 필요한 임시 테이블스페이스의 익스텐트(Extent) 수가 128 배수인 경우 The tablespace does not have enough free space 에러가 발생할 수 있습니다.

-   **module** : sm-disk-resource

-   **Category** : Efficiency

-   **재현 빈도** : Always

-   **설명** : SQL 수행 중 하나의 문장(statement)에서 필요한 임시 테이블스페이스의 익스텐트(Extent) 수가 128 배수인 경우 The
    tablespace does not have enough free space 에러가 발생할 수 있습니다. 
    
    에러가 발생하는 문장 수행 전/후로 아래의 모니터링 쿼리를 수행하여 버그 발생 여부를 확인할 수 있습니다.

    ```sql
    SELECT NAME TBS_NAME, 
           ALLOCATED_PAGE_COUNT/EXTENT_PAGE_COUNT AS ALLOCATED_EXTENT_COUNT,
           CACHED_FREE_EXTENT_COUNT
      FROM X$TABLESPACES I, X$TABLESPACES_HEADER H
     WHERE I.ID = H.ID AND H.TYPE IN (5, 6);
    ```

    문장 수행 후 CACHED\_FREE\_EXTENT\_COUNT가 문장 수행 전으로 돌아오지 않거나 ALLOCATED\_EXTENT\_COUNT와 CACHED\_FREE\_EXTENT\_COUNT의 차이가 큰 경우 이 버그로 인한 현상으로 의심해볼 수 있습니다.
    
-   **재현 방법**

    -   **재현 절차**

            disk temp table 사용하는 쿼리 수행 시

    -   **수행 결과**

        ```sql
        iSQL> SELECT ALLOCATED_PAGE_COUNT/64, CACHED_FREE_EXTENT_COUNT FROM X$TABLESPACES WHERE ID ='4';
        ALLOCATED_PAGE_COUNT/64 CACHED_FREE_EXTENT_COUNT 
        ----------------------------------------------------
        5646                   5645                 
        1 row selected.
        iSQL> SELECT ... (disk temp table 사용하는 쿼리)
        iSQL> SELECT ALLOCATED_PAGE_COUNT/64, CACHED_FREE_EXTENT_COUNT FROM X$TABLESPACES WHERE ID ='4';
        ALLOCATED_PAGE_COUNT/64 CACHED_FREE_EXTENT_COUNT 
        ----------------------------------------------------
        5646                   5517 
        ```

    -   **예상 결과**

        ```sql
        iSQL> SELECT ALLOCATED_PAGE_COUNT/64, CACHED_FREE_EXTENT_COUNT FROM X$TABLESPACES WHERE ID ='4';
        ALLOCATED_PAGE_COUNT/64 CACHED_FREE_EXTENT_COUNT 
        ----------------------------------------------------
        5646                   5645                 
        1 row selected.
        iSQL> SELECT ... (disk temp table 사용하는 쿼리)
        iSQL> SELECT ALLOCATED_PAGE_COUNT/64, CACHED_FREE_EXTENT_COUNT FROM X$TABLESPACES WHERE ID ='4';
        ALLOCATED_PAGE_COUNT/64 CACHED_FREE_EXTENT_COUNT 
        ----------------------------------------------------
        5646                   5645
        ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49530 Altibase 서버 운용 중 비정상 종료 발생 시 코어 덤프가 생성되는 현상을 방지합니다.

-   **module** : id

-   **Category** : Maintainability

-   **재현 빈도** : Always

-   **설명** : Altibase 서버 운용 중 비정상 종료 발생 시 코어 덤프가 생성되는 현상을 방지합니다. setrlimit으로 코어 파일 크기를 0으로 설정합니다. setrlimit을 호출하는 시점은 Altibase 서버 구동 단계 중 "Initialize Operating System Parameters" 입니다.
    
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

### BUG-49532 LEFT OUTER JOIN 왼쪽이 집합 연산을 포함한 인라인 뷰이고 ON 절의 AND 조건에 SUBQUERY가 포함된 경우 Altibase 서버가 비정상 종료합니다.

-   **module** : qp-dml-pvo

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : LEFT OUTER JOIN 왼쪽이 집합 연산을 포함한 인라인 뷰이고 ON 절의 AND 조건에 SUBQUERY가 포함된 경우 Altibase 서버가 비정상 종료하는 현상을 수정합니다.
    
-   **재현 방법**

    -   **재현 절차**

        ```sql
        DROP TABLE T1;
        DROP TABLE T2;
        DROP TABLE T3;
        
        CREATE TABLE T1 ( I1 VARCHAR(10), I2 VARCHAR(10));
        CREATE TABLE T2 ( I1 VARCHAR(10), I2 VARCHAR(10));
        CREATE TABLE T3 ( I1 VARCHAR(10), I2 VARCHAR(10), I3 VARCHAR(10));
        
        SELECT A.I1
          FROM T1 A 
          LEFT OUTER JOIN (SELECT I1 , SUM(I2) AS TOT_GWASE_PYOJUN_PRC
                             FROM T2 TA
                            GROUP BY I1 ) C 
          ON A.I1 = C.I1 
          AND C.TOT_GWASE_PYOJUN_PRC >= (SELECT I1 FROM T3 ) ;
        ```

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

    ```sql
    SELECT A.i1
      FROM t1 A 
      LEFT OUTER JOIN (SELECT i1 , SUM(i2) AS TOT_GWASE_PYOJUN_PRC
                         FROM t2 TA
                     GROUP BY i1 ) C 
      ON A.i1 = C.i1
     WHERE C.TOT_GWASE_PYOJUN_PRC >= (SELECT i1 FROM t3 ) ;
    ```

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49538 임시 테이블스페이스를 사용하는 SQL문 수행 시 Altibase 서버가 비정상 종료, Internal server error 에러 또는 결과 오류가 발생할 수 있습니다.

-   **module** : sm

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 임시 테이블스페이스를 사용하는 SQL문 수행 시 Altibase 서버가 비정상 종료, Internal server error 에러 또는 결과 오류가
    발생하는 현상을 수정합니다.
    
    이 버그는 아래 조건을 모두 만족하는 경우 매우 낮은 확률로 발생합니다.
    
    - Altibase 7.1.0.5.1 이상

    - SQL 문장에 디스크 테이블을 포함하고 GROUP BY 절을 사용한 경우

    - 디스크 템프 테이블 연산 중 SORT 연산 수행

    - SORT\_AREA\_SIZE 공간 부족으로 디스크 임시 테이블스페이스 사용 시

      > 참고)
      >
      > Altibase 서버는 디스크 테이블에 대한 질의 처리 과정에서 SORT/HASH 연산이 필요할 경우 빠른 연산을 위해 미리 할당된 메모리를 이용한다. 만약 정해진 크기의 메모리를 모두 사용하고 SORT/HASH 연산을 위한 공간이 추가적으로 필요한 경우 디스크 임시 테이블스페이스를 사용한다. SORT\_AREA\_SIZE는 SORT 연산이 필요한 경우 사용할 수 있는 최대 메모리 크기를 지정한 Altibase 프로퍼티이다.

    이 현상이 발생하는 경우 altibase_error.log 에 아래와 같은 에러가 발생합니다.
    
    ```bash
     IDE_ERROR( sIsValid == ID_TRUE )[sdtSortSegment.h:751], errno=[11]
     [FAILURE] ERR-0109E(error=11) Internal server error.
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
|    7.1.0.6.8     |          6.5.1          |    8.10.1    |        7.1.7        |            7.4.7             |

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

- LISTAGG\_PRECISION

#### 변경된 프로퍼티

#### 삭제된 프로퍼티

### 성능 뷰

#### 추가된 성능 뷰

#### 변경된 성능 뷰

#### 삭제된 성능 뷰
