# Altibase 7.1.0.7.8 Patch Notes

<br/>

<br/>

# **Table of Contents**

- [New Features](#new-features)
  - [BUG-49782 Altibase 7 이상에서 Altibase 6.3.1 옵티마이저와 유사한 실행 계획을 생성하는 기능을 추가합니다.](#bug-49782altibase-7-%EC%9D%B4%EC%83%81%EC%97%90%EC%84%9C-altibase-631-%EC%98%B5%ED%8B%B0%EB%A7%88%EC%9D%B4%EC%A0%80%EC%99%80-%EC%9C%A0%EC%82%AC%ED%95%9C-%EC%8B%A4%ED%96%89-%EA%B3%84%ED%9A%8D%EC%9D%84-%EC%83%9D%EC%84%B1%ED%95%98%EB%8A%94-%EA%B8%B0%EB%8A%A5%EC%9D%84-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)

- [Fixed Bugs](#fixed-bugs)
  - [BUG-48012 GEOMFROMTEXT 함수와 같은 ST\_GEOMETRYFROMTEXT 함수를 추가합니다. 두 함수에서 WKT의 값이 NULL이면 NULL을 반환하도록 변경합니다.](#bug-48012geomfromtext-함수와-같은-st_geometryfromtext-함수를-추가합니다-두-함수에서-srid의-값이-null이면-null을-반환하도록-변경합니다)
  - [BUG-49730 널 데이터가 저장된 LOB 컬럼을 두 개 이상 가진 테이블에 UPDATE문 수행 시 Adapter가 비정상 종료합니다.](#bug-49730%EB%84%90-%EB%8D%B0%EC%9D%B4%ED%84%B0%EA%B0%80-%EC%A0%80%EC%9E%A5%EB%90%9C-lob-%EC%BB%AC%EB%9F%BC%EC%9D%84-%EB%91%90-%EA%B0%9C-%EC%9D%B4%EC%83%81-%EA%B0%80%EC%A7%84-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90-update%EB%AC%B8-%EC%88%98%ED%96%89-%EC%8B%9C-adapter%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49743 Altibase 서버 구동 시 리빌드되지 않은 인덱스 접근 시 Altibase 서버가 비정상 종료합니다.](#bug-49743altibase-%EC%84%9C%EB%B2%84-%EA%B5%AC%EB%8F%99-%EC%8B%9C-%EB%A6%AC%EB%B9%8C%EB%93%9C%EB%90%98%EC%A7%80-%EC%95%8A%EC%9D%80-%EC%9D%B8%EB%8D%B1%EC%8A%A4-%EC%A0%91%EA%B7%BC-%EC%8B%9C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49763 디스크 테이블 조회 중 대상 테이블의 컬럼 정보 문제로 Altibase 서버가 비정상 종료하는 원인을 분석하기 위한 예외 처리를 추가합니다.](#bug-49763%EB%94%94%EC%8A%A4%ED%81%AC-%ED%85%8C%EC%9D%B4%EB%B8%94-%EC%A1%B0%ED%9A%8C-%EC%A4%91-%EB%8C%80%EC%83%81-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%9D%98-%EC%BB%AC%EB%9F%BC-%EC%A0%95%EB%B3%B4-%EB%AC%B8%EC%A0%9C%EB%A1%9C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%98%EB%8A%94-%EC%9B%90%EC%9D%B8%EC%9D%84-%EB%B6%84%EC%84%9D%ED%95%98%EA%B8%B0-%EC%9C%84%ED%95%9C-%EC%98%88%EC%99%B8-%EC%B2%98%EB%A6%AC%EB%A5%BC-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49766 REGEXP\_MODE 프로퍼티 값을 1로 변경할 때 데이터베이스 서버 캐릭터셋을 체크합니다.](#bug-49766regexp_mode-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0-%EA%B0%92%EC%9D%84-1%EB%A1%9C-%EB%B3%80%EA%B2%BD%ED%95%A0-%EB%95%8C-%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4-%EC%84%9C%EB%B2%84-%EC%BA%90%EB%A6%AD%ED%84%B0%EC%85%8B%EC%9D%84-%EC%B2%B4%ED%81%AC%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49769 altibase.properties.sample 파일에서 지원하지 않는 REPLICATION\_NET\_CONN\_IP\_STACK 프로퍼티를 삭제합니다.](#bug-49769altibasepropertiessample-%ED%8C%8C%EC%9D%BC%EC%97%90%EC%84%9C-%EC%A7%80%EC%9B%90%ED%95%98%EC%A7%80-%EC%95%8A%EB%8A%94-replication_net_conn_ip_stack-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0%EB%A5%BC-%EC%82%AD%EC%A0%9C%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49778 디스크 인덱스가 선택되고 집계 함수를 사용한 서브쿼리가 Subquery Unnesting으로 쿼리 변환 시 결과 오류가 발생합니다.](#bug-49778%EB%94%94%EC%8A%A4%ED%81%AC-%EC%9D%B8%EB%8D%B1%EC%8A%A4%EA%B0%80-%EC%84%A0%ED%83%9D%EB%90%98%EA%B3%A0-%EC%A7%91%EA%B3%84-%ED%95%A8%EC%88%98%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%9C-%EC%84%9C%EB%B8%8C%EC%BF%BC%EB%A6%AC%EA%B0%80-subquery-unnesting%EC%9C%BC%EB%A1%9C-%EC%BF%BC%EB%A6%AC-%EB%B3%80%ED%99%98-%EC%8B%9C-%EA%B2%B0%EA%B3%BC-%EC%98%A4%EB%A5%98%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
  - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
  - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

# New Features
### BUG-49782 Altibase 7 이상에서 Altibase 6.3.1 옵티마이저와 유사한 실행 계획을 생성하는 기능을 추가합니다.

-   **module** : qp

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : Altibase 7 이상에서 Altibase 6.3.1 옵티마이저와 유사한 실행 계획을 생성하는 기능을 추가합니다.

    디스크 테이블에 접근하는 트랜잭션에서 메모리 임시 테이블을 사용할 때 Index nested loop 조인 대신 HASH 조인이 선택되어 쿼리 성능이 느린 상황을 프로퍼티로 조정할 수 있습니다.

    이 기능은 특수한 목적으로 제공하고 있으므로 자세한 내용을 원할 경우 Altibase 기술 지원 센터로 연락해주세요.

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

# Fixed Bugs

### BUG-48012 GEOMFROMTEXT 함수와 같은 ST\_GEOMETRYFROMTEXT 함수를 추가합니다. 두 함수에서 SRID의 값이 NULL이면 NULL을 반환하도록 변경합니다.

-   **module** : st-function

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : GEOMFROMTEXT 함수와 같은 ST\_GEOMETRYFROMTEXT 함수를 추가합니다. 두 함수에서 SRID의 값이 NULL이면 NULL을 반환하도록 변경합니다. 
    
    버그 반영 전/후 조건에 맞는 질의문 수행 시 결과가 달라집니다. 수행 결과 차이는 수행 결과와 예상 결과 항목을 참고하세요.
    
-   **재현 방법**

    -   **재현 절차**

        ```sql
        SELECT ST_ASEWKT(ST_GEOMETRYFROMTEXT( 'POINT(10 20)', 120));
        SELECT ST_ASEWKT(ST_GEOMFROMTEXT( 'POINT(10 20)', NULL));
        ```

    -   **수행 결과**

        ```sql
        iSQL> SELECT ST_ASEWKT(ST_GEOMETRYFROMTEXT( 'POINT(10 20)', 120));
        [ERR-31129 : Procedure or function not found :
        0001 : SELECT ST_ASEWKT(ST_GEOMETRYFROMTEXT( 'POINT(10 20)', 120))
                               ^                  ^
        .]
        
        iSQL> SELECT ST_ASEWKT(ST_GEOMFROMTEXT( 'POINT(10 20)', NULL));
        ST_ASEWKT(ST_GEOMFROMTEXT('POINT(1020)',NU  
        ----------------------------------------------
        SRID=0;POINT(10 20)                       
        1 row selected.
        ```

    -   **예상 결과**

        ```sql
        iSQL> SELECT ST_ASEWKT(ST_GEOMETRYFROMTEXT( 'POINT(10 20)', 120));
        ST_ASEWKT(ST_GEOMETRYFROMTEXT('POINT(1020)  
        ----------------------------------------------
        SRID=120;POINT(10 20)                     
        1 row selected.
        
        iSQL> SELECT ST_ASEWKT(ST_GEOMFROMTEXT( 'POINT(10 20)', NULL));
        ST_ASEWKT(ST_GEOMFROMTEXT('POINT(1020)',NU  
        ----------------------------------------------
        1 row selected.
        ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49730 널 데이터가 저장된 LOB 컬럼을 두 개 이상 가진 테이블에 UPDATE문 수행 시 Adapter가 비정상 종료합니다.

-   **module** : rp-jdbcAdapter

-   **Category** : Testcase Fail

-   **재현 빈도** : Always

-   **설명** : 널 데이터가 저장된 LOB 컬럼을 두 개 이상 가진 테이블에 UPDATE문 수행 시 Adapter가 비정상 종료하는 현상을 수정합니다.
    
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

### BUG-49743 Altibase 서버 구동 시 리빌드되지 않은 인덱스 접근 시 Altibase 서버가 비정상 종료합니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : Altibase 서버 구동 시 리빌드되지 않은 인덱스 접근 시 Altibase 서버가 비정상 종료하는 현상을 수정합니다. 이 버그 현상은
    비공개 프로퍼티 INDEX\_REBUILD\_AT\_STARTUP 값을 0으로 설정하고 Altibase 서버 구동 후 사용자 인덱스에 접근하는 DML 수행 시
    발생합니다. 앞으로 DML 수행 시 리빌드되지 않은 인덱스에 접근하면 아래와 같은 에러 메시지가 발생하도록 수정하였습니다.
    
    ERR-111BE : Failed to scan the index because it was not rebuilt. (Index Name :*index\_name*)

    이 에러 메시지는 새로 추가된 에러 메시지로, 자세한 내용은 Error Code 항목을 참고하세요.
    
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
        
        ```
        0x111BE (  70078) smERR_ABORT_NOT_BUILT_INDEX Failed to scan the index because it was not rebuilt. (Index Name :<0%s>) 
        # *Cause: This index was not rebuilt when the Altibase server was starting up. The value of INDEX_REBUILD_AT_STARTUP property is set to 0.
        # *Action: Rebuild this index. Or to rebuild all the indexes, delete INDEX_REBUILD_AT_STARTUP = 0 in altibase.properties and restart the Altibase server.
        ```
        
        

### BUG-49763 디스크 테이블 조회 중 대상 테이블의 컬럼 정보 문제로 Altibase 서버가 비정상 종료하는 원인을 분석하기 위한 예외 처리를 추가합니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Impossible

-   **설명** : 디스크 테이블 조회 중 대상 테이블 컬럼 정보에 이상이 생기면 Altibase 서버가 비정상 종료합니다. 이 버그 발생 시
    altibase\_error.log 에 아래와 같은 에러가 발생합니다.
    
    ```
    Signal 5(SIGTRAP) caught.
    Fault address was 0x0000000100369858
    ```

    Altibase 서버가 비정상 종료하지 않도록 예외 처리를 변경하고 원인 분석을 위한 예외 처리를 추가합니다.
    
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

### BUG-49766 REGEXP\_MODE 프로퍼티 값을 1로 변경할 때 데이터베이스 서버 캐릭터셋을 체크합니다.

-   **module** : qp

-   **Category** : Usability

-   **재현 빈도** : Always

-   **설명** : REGEXP\_MODE 프로퍼티 값을 1로 변경할 때 데이터베이스 서버 캐릭터셋을 체크합니다. PCRE2 라이브러리에서 지원하지 않는 캐릭터셋인 경우 ERR-2106B : Unsupported character set by PCRE2 library 에러가 발생합니다.
    
-   **재현 방법**

    -   **재현 절차**

            ALTER SESSION SET REGEXP_MODE = 1;

    -   **수행 결과**

            Alter success.

    -   **예상 결과**

            ERR-2106B : Unsupported character set by PCRE2 library

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49769 altibase.properties.sample 파일에서 지원하지 않는 REPLICATION\_NET\_CONN\_IP\_STACK 프로퍼티를 삭제합니다.

-   **module** : rp

-   **Category** : Maintainability

-   **재현 빈도** : Always

-   **설명** :

    altibase.properties.sample 파일에서 지원하지 않아 주석 처리된 REPLICATION\_NET\_CONN\_IP\_STACK 프로퍼티를 삭제합니다. 

    삭제된 부분은 아래와 같습니다. 

    ```
    # Replication receiver IP stack configuration
    # If this property is not set, it will be the same as the value of
    # NET_CONN_IP_STACK. If you want to set the IP stackconfiguration
    # differently for replication, you need to set this property.
    # - REPLICATION_NET_CONN_IP_STACK    = 0 # 0: IPv4 setack only
                                             # 1: Dual stack
                                             # 2: IPv6 stack only
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

### BUG-49778 디스크 인덱스가 선택되고 집계 함수를 사용한 서브쿼리가 Subquery Unnesting으로 쿼리 변환 시 결과 오류가 발생합니다.

-   **module** : qp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 디스크 인덱스가 선택되고 집계 함수를 사용한 서브쿼리가 Subquery Unnesting으로 쿼리 변환 시 결과 오류가 발생하는 현상을 수정합니다. 결과 오류를 수정한 버그로 조건에 만족하는 질의 수행 시 결과 및 실행 계획이 변경됩니다. 버그 수정 전/후 실행 계획 차이는 수행 결과 및 예상 결과 항목을 참고하시기 바랍니다.
    
-   **재현 방법**

    -   **재현 절차**

        ```sql
        DROP TABLE T2;
        
        CREATE TABLE T2 (
        "TRADE_DATE" CHAR(8) NOT NULL,
        "DATE_ID"    NUMERIC(10),
        "DAY_TYPE"   NUMERIC(4)
        ) TABLESPACE SYS_TBS_DISK_DATA;
        
        ALTER TABLE T2 ADD CONSTRAINT "T2_SKSDATEI" PRIMARY KEY("TRADE_DATE");
        
        INSERT INTO T2 VALUES('19801207', 1, 1);
        INSERT INTO T2 VALUES('20220625', 2, 2);
        INSERT INTO T2 VALUES('20220627', 3, 3);
        
        ALTER SESSION SET OPTIMIZER_DISK_INDEX_COST_ADJ = 1;
        ALTER SESSION SET EXPLAIN PLAN = ON;
        ALTER SESSION SET TRCLOG_DETAIL_PREDICATE = 1;
        
        SELECT MAX(TRADE_DATE) FROM T2 WHERE TRADE_DATE < (SELECT MAX(TRADE_DATE) FROM T2);
        ```

    -   **수행 결과**

        ```sql
        iSQL> SELECT MAX(TRADE_DATE) FROM T2 WHERE TRADE_DATE < (SELECT MAX(TRADE_DATE) FROM T2);
        MAX(TRADE_DATE)                           
        --------------------------------------------
        19801207                                  
        1 row selected.
        ------------------------------------------------------------
        PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 10, COST: 381.30 )
         FILTER
          [ FILTER ]
          $VIEW1.COL1 IS NOT NULL
          VIEW ( ACCESS: 1, COST: 379.98 )
           PROJECT ( COLUMN_COUNT: 2, TUPLE_SIZE: 14, COST: 260.58 )
            WINDOW SORT ( ITEM_SIZE: 24, ITEM_COUNT: 3, DISK_PAGE_COUNT: 0, ACCESS: 7, SORT_COUNT: 0, COST: 251.34 )
             [ ANALYTIC FUNCTION INFO ]
             SORT_KEY[0]: ()
              MAX(TRADE_DATE) OVER ()
             SCAN ( TABLE: SYS.T2, INDEX: SYS.T2_SKSDATEI, RANGE SCAN, ACCESS: 3, DISK_PAGE_COUNT: 64, COST: 117.82 )
        ------------------------------------------------------------
        ```

    -   **예상 결과**

        ```sql
        iSQL> SELECT MAX(TRADE_DATE) FROM T2 WHERE TRADE_DATE < (SELECT MAX(TRADE_DATE) FROM T2);
        MAX(TRADE_DATE)  
        -------------------
        20220625  
        1 row selected.
        ------------------------------------------------------------
        PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 10, COST: 384.37 )
         GROUP-AGGREGATION ( ITEM_SIZE: 32, GROUP_COUNT: 1, BUCKET_COUNT: 1, ACCESS: 1, COST: 384.37 )
          FILTER
           [ FILTER ]
           $VIEW1.COL1 IS NOT NULL
           VIEW ( ACCESS: 3, COST: 379.98 )
            PROJECT ( COLUMN_COUNT: 2, TUPLE_SIZE: 14, COST: 260.58 )
             WINDOW SORT ( ITEM_SIZE: 24, ITEM_COUNT: 3, DISK_PAGE_COUNT: 0, ACCESS: 9, SORT_COUNT: 0, COST: 251.34 )
              [ ANALYTIC FUNCTION INFO ]
              SORT_KEY[0]: ()
               MAX(TRADE_DATE) OVER ()
              SCAN ( TABLE: SYS.T2, INDEX: SYS.T2_SKSDATEI, FULL SCAN, ACCESS: 3, DISK_PAGE_COUNT: 64, COST: 117.82 )
        ------------------------------------------------------------
        ```

-   **Workaround**

    NO_UNNEST 힌트 사용

    ```sql
    SELECT MAX(TRADE_DATE) FROM T2 
     WHERE TRADE_DATE < (SELECT /*+ NO_UNNEST */ MAX(TRADE_DATE) FROM T2);
    ```

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
|    7.1.0.7.8     |          6.5.1          |    8.10.1    |        7.1.7        |            7.4.7             |

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
