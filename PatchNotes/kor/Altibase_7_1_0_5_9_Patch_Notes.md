<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents** 

- [Altibase 7.1.0.5.9 Patch Notes](#altibase-71059-patch-notes)
  - [New Features](#new-features)
    - [BUG-49213 DDL 복제 실패 시 내부적인 예외 처리를 개선합니다.](#bug-49213ddl-%EB%B3%B5%EC%A0%9C-%EC%8B%A4%ED%8C%A8-%EC%8B%9C-%EB%82%B4%EB%B6%80%EC%A0%81%EC%9D%B8-%EC%98%88%EC%99%B8-%EC%B2%98%EB%A6%AC%EB%A5%BC-%EA%B0%9C%EC%84%A0%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-49102 파티션 키 2개 이상인 RANGE 파티션드 테이블에 SPLIT PARTITION 수행하고 DBMS Stats 프로시저 COPY_TABLE_STATS를 수행한 경우 간헐적으로 결과 오류가 발생할 수 있습니다.](#bug-49102%ED%8C%8C%ED%8B%B0%EC%85%98-%ED%82%A4-2%EA%B0%9C-%EC%9D%B4%EC%83%81%EC%9D%B8-range-%ED%8C%8C%ED%8B%B0%EC%85%98%EB%93%9C-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90-split-partition-%EC%88%98%ED%96%89%ED%95%98%EA%B3%A0-dbms-stats-%ED%94%84%EB%A1%9C%EC%8B%9C%EC%A0%80-copy_table_stats%EB%A5%BC-%EC%88%98%ED%96%89%ED%95%9C-%EA%B2%BD%EC%9A%B0-%EA%B0%84%ED%97%90%EC%A0%81%EC%9C%BC%EB%A1%9C-%EA%B2%B0%EA%B3%BC-%EC%98%A4%EB%A5%98%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-49155 트레이스 로그 파일 교체 시 동시성 문제가 있습니다.](#bug-49155%ED%8A%B8%EB%A0%88%EC%9D%B4%EC%8A%A4-%EB%A1%9C%EA%B7%B8-%ED%8C%8C%EC%9D%BC-%EA%B5%90%EC%B2%B4-%EC%8B%9C-%EB%8F%99%EC%8B%9C%EC%84%B1-%EB%AC%B8%EC%A0%9C%EA%B0%80-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-49181 이중화 환경에서 DDL 복제 기능 사용 시 DDL문 수행 중 V$REPRECEIVER 조회 시 Altibase 서버가 비정상 종료 할 수 있습니다.](#bug-49181%EC%9D%B4%EC%A4%91%ED%99%94-%ED%99%98%EA%B2%BD%EC%97%90%EC%84%9C-ddl-%EB%B3%B5%EC%A0%9C-%EA%B8%B0%EB%8A%A5-%EC%82%AC%EC%9A%A9-%EC%8B%9C-ddl%EB%AC%B8-%EC%88%98%ED%96%89-%EC%A4%91-vrepreceiver-%EC%A1%B0%ED%9A%8C-%EC%8B%9C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C-%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-49202 Windows 환경에서 온라인 로그 파일 생성 문제로 Altibase 서버 구동이 실패합니다.](#bug-49202windows-%ED%99%98%EA%B2%BD%EC%97%90%EC%84%9C-%EC%98%A8%EB%9D%BC%EC%9D%B8-%EB%A1%9C%EA%B7%B8-%ED%8C%8C%EC%9D%BC-%EC%83%9D%EC%84%B1-%EB%AC%B8%EC%A0%9C%EB%A1%9C-altibase-%EC%84%9C%EB%B2%84-%EA%B5%AC%EB%8F%99%EC%9D%B4-%EC%8B%A4%ED%8C%A8%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-49217 Adapter for JDBC, Adapter for Oracle 에서 INSERT 문 처리 시 컬럼 이름을 명시하여 복제하도록 수정하였습니다.](#bug-49217adapter-for-jdbc-adapter-for-oracle-%EC%97%90%EC%84%9C-insert-%EB%AC%B8-%EC%B2%98%EB%A6%AC-%EC%8B%9C-%EC%BB%AC%EB%9F%BC-%EC%9D%B4%EB%A6%84%EC%9D%84-%EB%AA%85%EC%8B%9C%ED%95%98%EC%97%AC-%EB%B3%B5%EC%A0%9C%ED%95%98%EB%8F%84%EB%A1%9D-%EC%88%98%EC%A0%95%ED%95%98%EC%98%80%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-49224 이중화 Active-Active 환경에서 DDL 복제 기능 사용 시 원격 서버에서 DDL_LOCK_TIMEOUT에 의해 DDL문이 실패한 경우 지역 서버의 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-49224%EC%9D%B4%EC%A4%91%ED%99%94-active-active-%ED%99%98%EA%B2%BD%EC%97%90%EC%84%9C-ddl-%EB%B3%B5%EC%A0%9C-%EA%B8%B0%EB%8A%A5-%EC%82%AC%EC%9A%A9-%EC%8B%9C-%EC%9B%90%EA%B2%A9-%EC%84%9C%EB%B2%84%EC%97%90%EC%84%9C-ddl_lock_timeout%EC%97%90-%EC%9D%98%ED%95%B4-ddl%EB%AC%B8%EC%9D%B4-%EC%8B%A4%ED%8C%A8%ED%95%9C-%EA%B2%BD%EC%9A%B0-%EC%A7%80%EC%97%AD-%EC%84%9C%EB%B2%84%EC%9D%98-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-49233 JDBC 4.2 스펙이 적용된 JDBC Driver에서 지원하지 않는 기능 호출 시 SQLFeatureNotSupportedException 예외로 처리하도록 수정합니다.](#bug-49233jdbc-42-%EC%8A%A4%ED%8E%99%EC%9D%B4-%EC%A0%81%EC%9A%A9%EB%90%9C-jdbc-driver%EC%97%90%EC%84%9C-%EC%A7%80%EC%9B%90%ED%95%98%EC%A7%80-%EC%95%8A%EB%8A%94-%EA%B8%B0%EB%8A%A5-%ED%98%B8%EC%B6%9C-%EC%8B%9C-sqlfeaturenotsupportedexception-%EC%98%88%EC%99%B8%EB%A1%9C-%EC%B2%98%EB%A6%AC%ED%95%98%EB%8F%84%EB%A1%9D-%EC%88%98%EC%A0%95%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Altibase 7.1.0.5.9 Patch Notes
==============================

New Features
------------

### BUG-49213 DDL 복제 실패 시 내부적인 예외 처리를 개선합니다.

-   **module** : rp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : DDL 복제 실패 시 내부적인 예외 처리를 개선합니다.

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

### BUG-49102 파티션 키 2개 이상인 RANGE 파티션드 테이블에 SPLIT PARTITION 수행하고 DBMS Stats 프로시저 COPY\_TABLE\_STATS를 수행한 경우 간헐적으로 결과 오류가 발생할 수 있습니다.

-   **module** : qp

-   **Category** : Functional Error

-   **재현 빈도** : Frequence

-   **설명** : 파티션 키 2개 이상인 RANGE 파티션드 테이블에 SPLIT
    PARTITION 수행하고 DBMS Stats 프로시저 COPY\_TABLE\_STATS를 수행한
    경우 간헐적으로 발생하는 결과 오류를 수정합니다.

- **재현 방법**

  - **재현 절차**

    ```sql
    DROP TABLE T1 CASCADE;
    
    CREATE TABLE T1
    (
        I1   INTEGER,
        I2   INTEGER
    )
    PARTITION BY RANGE( I1, I2 )
    (
        PARTITION P1   VALUES LESS THAN (  101,10 ),
        PARTITION P2   VALUES LESS THAN (  201,20 ),
        PARTITION P3   VALUES LESS THAN (  301,30 ),
        PARTITION PMAX VALUES LESS THAN ( 1001,40 ),
        PARTITION DEF VALUES DEFAULT 
    ) TABLESPACE SYS_TBS_DISK_DATA;
    
    INSERT INTO T1 SELECT LEVEL, 1 FROM DUAL CONNECT BY LEVEL <= 1000;
    
    EXEC GATHER_TABLE_STATS('SYS', 'T1');
    
    ALTER TABLE T1 SPLIT PARTITION PMAX AT ( 400, 40 ) INTO ( PARTITION P4, PARTITION PMAX );
    
    -- DBMS_CONCURRENT_EXEC, DBMS_STATS 저장 패키지 설치 필요
    EXEC DBMS_STATS.COPY_TABLE_STATS('SYS', 'T1', 'P3', 'P4');
    ```

  - **수행 결과**

    ```sql
    SELECT PARTITION_NAME, NUM_DIST, NUM_NULL, AVG_LEN, MIN,MAX
      FROM V$DBMS_STATS S, SYSTEM_.SYS_TABLE_PARTITIONS_ T
     WHERE S.TYPE = 'C' AND S.TARGET_ID = T.PARTITION_OID
     ORDER BY 1, MIN, MAX; 
    PARTITION_NAME   NUM_DIST             NUM_NULL             AVG_LEN              MIN            MAX      
    --------------------------------------------------------------------------------------------------------
    P1               1                    0                    4                    1              1        
    P1               101                  0                    4                    1              101      
    P2               1                    0                    4                    1              1        
    P2               100                  0                    4                    102            201      
    P3               1                    0                    4                    1              1        
    P3               100                  0                    4                    202            301      
    P4               100                  0                    4                    30             40       
    P4               1                    0                    4                    301            400      
    PMAX             1                    0                    4                    1              1        
    PMAX             699                  0                    4                    302            1000   
    ```

  -   **예상 결과**

      ```sql
      SELECT PARTITION_NAME, NUM_DIST, NUM_NULL, AVG_LEN, MIN,MAX
        FROM V$DBMS_STATS S, SYSTEM_.SYS_TABLE_PARTITIONS_ T
       WHERE S.TYPE = 'C' AND S.TARGET_ID = T.PARTITION_OID
       ORDER BY 1, MIN, MAX; 
      PARTITION_NAME   NUM_DIST             NUM_NULL             AVG_LEN              MIN            MAX      
      --------------------------------------------------------------------------------------------------------
      P1               1                    0                    4                    1              1        
      P1               101                  0                    4                    1              101      
      P2               1                    0                    4                    1              1        
      P2               100                  0                    4                    102            201      
      P3               1                    0                    4                    1              1        
      P3               100                  0                    4                    202            301      
      P4               1                    0                    4                    30             40       
      P4               100                  0                    4                    301            400      
      PMAX             1                    0                    4                    1              1        
      PMAX             699                  0                    4                    302            1000
      ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49155 트레이스 로그 파일 교체 시 동시성 문제가 있습니다.

-   **module** : id

-   **Category** : Reliability

-   **재현 빈도** : Rare

-   **설명** : 트레이스 로그 파일 교체 시 동시성 문제가 있어
    수정하였습니다.

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

### BUG-49181 이중화 환경에서 DDL 복제 기능 사용 시 DDL문 수행 중 V\$REPRECEIVER 조회 시 Altibase 서버가 비정상 종료 할 수 있습니다.

-   **module** : rp

-   **Category** : Fatal

-   **재현 빈도** : Rare

-   **설명** : Altibase 이중화 환경에서 DDL 복제 기능
    사용(REPLICATION\_DDL\_SYNC = 1 설정) 시, DDL문 수행 중
    V\$REPRECEIVER 조회 시 동시성 문제로 Altibase 서버가 비정상 종료하는
    현상을 수정합니다.

- **재현 방법**

  - **재현 절차**

        Altibase 이중화 환경에서 Altibase 서버 프로퍼티 REPLICATION_DDL_SYNC = 1 설정
        TRUNCATE 테이블 수행 중
        V$REPRECEIVER 조회

  -   **수행 결과**

          Altibase 서버 비정상 종료

  -   **예상 결과**

          정상적으로 V$REPRECEIVER 조회

-   **Workaround**

        REPLICATION_DDL_SYNC = 1 설정 상태에서 DDL문 수행 중 V$REPRECEIVER를 조회하지 않는다.

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49202 Windows 환경에서 온라인 로그 파일 생성 문제로 Altibase 서버 구동이 실패합니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : Windows 환경에서 온라인 로그 파일 생성 문제로 Altibase
    서버 구동이 실패하는 현상을 수정합니다.

-   **재현 방법**

    -   **재현 절차**

            Windows에서 Altibase 서버 프로세스 강제 종료 후 구동

    -   **수행 결과**

            $ALTIBASE_HOME/trc/altibase_sm.log 에 The log file manager thread was aborted and restarted : because of insufficient memory or disk capacity or other problems 메시지가 발생하며 Altibase 서버 구동이 실패합니다. 

    -   **예상 결과**

-   **Workaround**

        altibase.properites 파일에 __USE_TEMP_FOR_PREPARE_LOGFILE=0 을 추가하고 Altibase 서버를 구동합니다. 

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49217 Adapter for JDBC, Adapter for Oracle 에서 INSERT 문 처리 시 컬럼 이름을 명시하여 복제하도록 수정하였습니다.

-   **module** : rp-jdbcAdapter

-   **Category** : Other

-   **재현 빈도** : Always

-   **설명** : Adapter for JDBC, Adapter for Oracle 에서 INSERT 문에 처리 시 컬럼 이름을 명시하여 복제하도록 수정하였습니다.
    
    jdbcAdapter.conf, oraAdapter.conf 에 사용할 수 프로퍼티가 추가되었습니다. 비공개 프로퍼티로 매뉴얼 및 conf 파일에 추가되어 있지 않습니다.
    
    **OTHER\_DATABASE\_SET\_COLUMN\_TO\_INSERT 프로퍼티 추가**
    
    **설명**
    
    Adapter for JDBC 의 INSERT 문 처리 시 컬럼 이름 지정 여부를 설정한다.
    
    0 :  INSERT 처리 시 컬럼 이름을 명시하지 않는다. 컬럼 순서가 다른 경우, 데이터 복제가 실패한다. 
    
    1 : INSERT 처리 시 컬럼 이름을 명시한다. 컬럼 순서가 다른 경우, 컬럼 이름으로 구분하여 데이터를 복제한다.

    **기본값**
    
    1
    
    **속성** : 읽기 전용, 비공개

    **ORACLE\_SET\_COLUMN\_TO\_INSERT 프로퍼티 추가**

    **설명**

    Adapter for Oracle 의 INSERT 문 처리 시 컬럼 이름 지정 여부를 설정한다.

    0 : INSERT 처리 시 컬럼 이름을 명시하지 않는다. 컬럼 순서가 다른 경우, 데이터 복제가 실패한다. 

    1 : INSERT 처리 시 컬럼 이름을 명시한다. 컬럼 순서가 다른 경우, 컬럼 이름으로 구분하여 데이터를 복제한다.

    **기본값**
    
    1
    
    **속성** : 읽기 전용, 비공개

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

### BUG-49224 이중화 Active-Active 환경에서 DDL 복제 기능 사용 시 원격 서버에서 DDL_LOCK_TIMEOUT에 의해 DDL문이 실패한 경우 지역 서버의 Altibase 서버가 비정상 종료할 수 있습니다. 

-   **module** : rp

-   **Category** : Other

-   **재현 빈도** : Rare

-   **설명** : 이중화 Active-Active 환경에서 DDL 복제 기능 사용 시 원격 서버에서 DDL_LOCK_TIMEOUT에 의해 DDL문이 실패한 경우 지역 서버의 Altibase 서버가 비정상 종료하는 현상을 수정합니다. 
    
- **재현 방법**

  - **재현 절차**

        Altibase 이중화 Active-Active 환경이고 DDL 복제 기능 사용(REPLICATION_DDL_SYNC = 1 설정) 
        
        지역 서버에서 T1 테이블에 TRUNCATE 수행 중 
        원격 서버에서 T1 테이블에 INSERT 수행
        지역 서버에서 TRUNCATE 실패 처리
        원격 서버에서 T1 테이블에 INSERT 수행

  -   **수행 결과**

          지역 서버에서 TRUNCATE 실패 후 원격 서버에서 수행한 INSERT문을 지역 서버의 Receiver 가 처리하다가 Altibase 서버 비정상 종료

  -   **예상 결과**

          Truncate 실패 이후 이중화 정상 동작

-   **Workaround**

        Altibase 서버 비정상 종료 없이 이중화 정상 동작

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49233 JDBC 4.2 스펙이 적용된 JDBC Driver에서 지원하지 않는 기능 호출 시 SQLFeatureNotSupportedException 예외로 처리하도록 수정합니다.

-   **module** : mm-jdbc

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : JDBC 4.2 스펙이 적용된 JDBC Driver에서 지원하지 않는 기능
    호출 시 SQLException 대신 SQLFeatureNotSupportedException 예외로
    처리하도록 수정합니다.

- **재현 방법**

  - **재현 절차**

    ```java
    Connection sConn = getConnection();sConn.setTypeMap(new HashMap());
    ```

  - **수행 결과**

    ```java
    Exception in thread "main" java.sql.SQLException: Unsupported feature: User defined type
    ```

  -   **예상 결과**

      ```java
      Exception in thread "main" java.sql.SQLFeatureNotSupportedException: User defined type
      ```

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
| 7.1.0.5.9        | 6.5.1                   | 8.9.1        | 7.1.7               | 7.4.6                        |

> Altibase 7.1 패치 버전별 히스토리는 [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7_1_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의
> 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는
> 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

> 패치를 롤백하려는 경우,
> [메타다운그레이드](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Installation.md#%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9Cmeta-downgrade)를
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
