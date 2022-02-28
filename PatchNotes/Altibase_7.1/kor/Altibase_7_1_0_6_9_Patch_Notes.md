Altibase 7.1.0.6.9 Patch Notes
==============================

<br/>

<br/>

# Table of Contents  

- [Fixed Bugs](#fixed-bugs)
  - [BUG-47420 LENGTH()로 LOB 길이 출력 시 Altibase 서버가 비정상 종료하고 디스크 테이블에 LOB 데이터 타입의 최대 크기를 초과하여 입력되는 현상을 수정합니다.](#bug-47420length%EB%A1%9C-lob-%EA%B8%B8%EC%9D%B4-%EC%B6%9C%EB%A0%A5-%EC%8B%9C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%98%EA%B3%A0-%EB%94%94%EC%8A%A4%ED%81%AC-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90-lob-%EB%8D%B0%EC%9D%B4%ED%84%B0-%ED%83%80%EC%9E%85%EC%9D%98-%EC%B5%9C%EB%8C%80-%ED%81%AC%EA%B8%B0%EB%A5%BC-%EC%B4%88%EA%B3%BC%ED%95%98%EC%97%AC-%EC%9E%85%EB%A0%A5%EB%90%98%EB%8A%94-%ED%98%84%EC%83%81%EC%9D%84-%EC%88%98%EC%A0%95%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49133 SORT\_AREA\_SIZE 값을 최소값 524288으로 설정하고 TEMP\_HASH\_BUCKET\_DENSITY 설정값을 65이상 설정한 경우 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-49133sort_area_size-%EA%B0%92%EC%9D%84-%EC%B5%9C%EC%86%8C%EA%B0%92-524288%EC%9C%BC%EB%A1%9C-%EC%84%A4%EC%A0%95%ED%95%98%EA%B3%A0-temp_hash_bucket_density-%EC%84%A4%EC%A0%95%EA%B0%92%EC%9D%84-65%EC%9D%B4%EC%83%81-%EC%84%A4%EC%A0%95%ED%95%9C-%EA%B2%BD%EC%9A%B0-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-49439 AUDIT disconnect 설정 환경에서 데이터베이스 세션 종료 시 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-49439audit-disconnect-%EC%84%A4%EC%A0%95-%ED%99%98%EA%B2%BD%EC%97%90%EC%84%9C-%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4-%EC%84%B8%EC%85%98-%EC%A2%85%EB%A3%8C-%EC%8B%9C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-49473 DBMS\_METADATA 패키지의 GET\_DDL 함수에 시퀀스 객체 지정 시 시퀀스 속성과 다른 MIN, MAX 값을 가진 구문이 추출될 수 있습니다.](#bug-49473dbms_metadata-%ED%8C%A8%ED%82%A4%EC%A7%80%EC%9D%98-get_ddl-%ED%95%A8%EC%88%98%EC%97%90-%EC%8B%9C%ED%80%80%EC%8A%A4-%EA%B0%9D%EC%B2%B4-%EC%A7%80%EC%A0%95-%EC%8B%9C-%EC%8B%9C%ED%80%80%EC%8A%A4-%EC%86%8D%EC%84%B1%EA%B3%BC-%EB%8B%A4%EB%A5%B8-min-max-%EA%B0%92%EC%9D%84-%EA%B0%80%EC%A7%84-%EA%B5%AC%EB%AC%B8%EC%9D%B4-%EC%B6%94%EC%B6%9C%EB%90%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-49543 디스크 테이블 변경 트랜잭션 수행 중 삭제된 디스크 인덱스 키를 다시 삭제하는 버그로 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-49543%EB%94%94%EC%8A%A4%ED%81%AC-%ED%85%8C%EC%9D%B4%EB%B8%94-%EB%B3%80%EA%B2%BD-%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98-%EC%88%98%ED%96%89-%EC%A4%91-%EC%82%AD%EC%A0%9C%EB%90%9C-%EB%94%94%EC%8A%A4%ED%81%AC-%EC%9D%B8%EB%8D%B1%EC%8A%A4-%ED%82%A4%EB%A5%BC-%EB%8B%A4%EC%8B%9C-%EC%82%AD%EC%A0%9C%ED%95%98%EB%8A%94-%EB%B2%84%EA%B7%B8%EB%A1%9C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-49553 SQL Plan Cache의 PCO(Plan Cache Object 교체 과정에서 해제한 메모리를 다시 해제하는 버그로 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-49553sql-plan-cache%EC%9D%98-pcoplan-cache-object-%EA%B5%90%EC%B2%B4-%EA%B3%BC%EC%A0%95%EC%97%90%EC%84%9C-%ED%95%B4%EC%A0%9C%ED%95%9C-%EB%A9%94%EB%AA%A8%EB%A6%AC%EB%A5%BC-%EB%8B%A4%EC%8B%9C-%ED%95%B4%EC%A0%9C%ED%95%98%EB%8A%94-%EB%B2%84%EA%B7%B8%EB%A1%9C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-49563 OPTIMIZER\_FEATURE\_ENABLE 프로퍼티 값에 영향을 받는 프로퍼티를 추가합니다.](#bug-49563optimizer_feature_enable-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0-%EA%B0%92%EC%97%90-%EC%98%81%ED%96%A5%EC%9D%84-%EB%B0%9B%EB%8A%94-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0%EB%A5%BC-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49564 OPTIMIZER\_FEATURE\_ENABLE 프로퍼티 값에 영향을 받는 프로퍼티 2개를 추가합니다.](#bug-49564optimizer_feature_enable-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0-%EA%B0%92%EC%97%90-%EC%98%81%ED%96%A5%EC%9D%84-%EB%B0%9B%EB%8A%94-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0-2%EA%B0%9C%EB%A5%BC-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49565 Altibase 서버 구동 중 Refine Memory Table 단계에서 실패할 때 altibase\_error.log에 출력되는 에러 메시지를 보완합니다.](#bug-49565altibase-%EC%84%9C%EB%B2%84-%EA%B5%AC%EB%8F%99-%EC%A4%91-refine-memory-table-%EB%8B%A8%EA%B3%84%EC%97%90%EC%84%9C-%EC%8B%A4%ED%8C%A8%ED%95%A0-%EB%95%8C-altibase_errorlog%EC%97%90-%EC%B6%9C%EB%A0%A5%EB%90%98%EB%8A%94-%EC%97%90%EB%9F%AC-%EB%A9%94%EC%8B%9C%EC%A7%80%EB%A5%BC-%EB%B3%B4%EC%99%84%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49572 CAST 연산자의 인자가 TIMESTAMP 인 경우 DATE로 변환하여 동작하는 Altibase 서버 프로퍼티를 추가합니다.](#bug-49572cast-%EC%97%B0%EC%82%B0%EC%9E%90%EC%9D%98-%EC%9D%B8%EC%9E%90%EA%B0%80-timestamp-%EC%9D%B8-%EA%B2%BD%EC%9A%B0-date%EB%A1%9C-%EB%B3%80%ED%99%98%ED%95%98%EC%97%AC-%EB%8F%99%EC%9E%91%ED%95%98%EB%8A%94-altibase-%EC%84%9C%EB%B2%84-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0%EB%A5%BC-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49576 Adapter for JDBC에서 지원하는 데이터 타입에 LOB을 추가합니다.](#bug-49576adapter-for-jdbc%EC%97%90%EC%84%9C-%EC%A7%80%EC%9B%90%ED%95%98%EB%8A%94-%EB%8D%B0%EC%9D%B4%ED%84%B0-%ED%83%80%EC%9E%85%EC%97%90-lob%EC%9D%84-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
  - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
  - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

Fixed Bugs
==========

### BUG-47420 LENGTH()로 LOB 길이 출력 시 Altibase 서버가 비정상 종료하고 디스크 테이블에 LOB 데이터 타입의 최대 크기를 초과하여 입력되는 현상을 수정합니다.

-   **module** : sm

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : LOB 데이터 입력 및 LENGTH() 출력 관련한 문제를 수정하였습니다.
    
    1. 디스크 테이블에서 LOB 데이터가 최대 크기(4G-1bytes)를 초과하여 입력되는 문제
    
    2. 메모리/휘발성 테이블에 LOB 데이터를 최대 크기를 초과하여 입력 시 실패하지만 롤백 후 데이터가 일부 남아있는 문제

    3. 디스크/메모리/휘발성 메모리 테이블에서 LENGTH()로 LOB 데이터 길이 출력 시 Altibase 서버 비정상 종료 현상
    
    이 버그 반영 이후 디스크 테이블에 4GB-1byte이상 LOB 데이터 입력 시 0x110D0, The lob size is bigger than the maximum lob size 에러가 발생합니다.
    
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

### BUG-49133 SORT\_AREA\_SIZE 값을 최소값 524288으로 설정하고 TEMP\_HASH\_BUCKET\_DENSITY 설정값을 65이상 설정한 경우 Altibase 서버가 비정상 종료할 수 있습니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : SORT\_AREA\_SIZE 값을 최소값 524288으로 설정하고 TEMP\_HASH\_BUCKET\_DENSITY 설정값을 65이상 설정한 경우 Altibase
    서버가 비정상 종료하는 현상을 수정합니다.
    
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

### BUG-49439 AUDIT disconnect 설정 환경에서 데이터베이스 세션 종료 시 Altibase 서버가 비정상 종료할 수 있습니다.

-   **module** : mm-altiaudit

-   **Category** : Maintainability

-   **재현 빈도** : Rare

-   **설명** : AUDIT disconnect 설정 환경에서 데이터베이스 세션 종료 시 Altibase 서버가 비정상 종료하는 현상을 수정합니다. 
    
-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

        altibase_error.log 에 아래와 같은 콜스택을 남기며 Altibase 서버가 비정상 종료합니다. 

        ```bash
        BEGIN-STACK [CRASH] =============================
        Caller[0] 0000000000417208      => mmmSignalHandler
        Caller[1] 00007F004DB5D5E0      => not found
        Caller[2] 0000000000442C3F      => mmtAuditManager::auditBySession(mmcStatement*)
        Caller[3] 000000000046925F      => mmcStatement::finalize()
        Caller[4] 0000000000470E6B      => mmcStatementManager::freeStatement(mmcStatement*)
        Caller[5] 0000000000462669      => mmcSession::finalize()
        Caller[6] 000000000041D62F      => mmtSessionManager::freeSession(mmcTask*)
        Caller[7] 0000000000413558      => mmcTask::finalize()
        Caller[8] 000000000041C9ED      => mmtSessionManager::freeTask(mmcTask*)
        Caller[9] 000000000042A485      => mmtServiceThread::terminateTask(mmcTask*)
        Caller[10] 000000000042AD82     => mmtServiceThread::executeTask()
        Caller[11] 000000000042B75C     => mmtServiceThread::run()
        Caller[12] 0000000000EA4A1B     => idtContainer::staticRunner(void*)
        Caller[13] 00007F004DB55E25     => not found
        Caller[14] 00007F004CC2434D     => not found
        END-STACK =======================================
        ```

    -   **예상 결과**

        AUDIT disconnect 설정을 비활성화합니다.

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49473 DBMS\_METADATA 패키지의 GET\_DDL 함수에 시퀀스 객체 지정 시 시퀀스 속성과 다른 MIN, MAX 값을 가진 구문이 추출될 수 있습니다.

-   **module** :

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : DBMS\_METADATA 패키지의 GET\_DDL 함수에 시퀀스 객체 지정 시 시퀀스 속성과 다른 MIN, MAX 값을 가진 구문이 추출되는 현상을 수정합니다.
    
    시퀀스 객체 생성 시 다음 2가지에 해당하는 경우 이 버그에 노출 가능성이 있습니다.

    - INCREMENT BY이 0보다 작고 MINVALUE 값으로 1을 명시한 경우
    
    - INCREMENT BY이 0보다 작고 MAXVALUE 값으로 9223372036854775806을 명시한 경우
    
-   **재현 방법**

    -   **재현 절차**

        ```sql
        CREATE SEQUENCE S1 INCREMENT BY -1 MINVALUE 1 MAXVALUE 10000;
        CREATE SEQUENCE S2 INCREMENT BY 1 MINVALUE 10 MAXVALUE 9223372036854775806;
        SELECT  DBMS_METADATA.GET_DDL('SEQUENCE', 'S1', 'SYS') FROM DUAL;
        SELECT  DBMS_METADATA.GET_DDL('SEQUENCE', 'S2', 'SYS') FROM DUAL;
        ```

    -   **수행 결과**

        ```
        iSQL> SELECT  DBMS_METADATA.GET_DDL('SEQUENCE', 'S1', 'SYS') FROM DUAL;
        DBMS_METADATA.GET_DDL('SEQUENCE','S1','SYS                                                            -----------------------------------------------------------------------------------------------------
        CREATE SEQUENCE "SYS"."S1" START WITH 10000 INCREMENT BY -1 MAXVALUE 10000                            
        1 row selected.
        iSQL> SELECT  DBMS_METADATA.GET_DDL('SEQUENCE', 'S2', 'SYS') FROM DUAL;
        DBMS_METADATA.GET_DDL('SEQUENCE','S2','SYS                                                            -----------------------------------------------------------------------------------------------------
        CREATE SEQUENCE "SYS"."S2" START WITH 9223372036854775806 INCREMENT BY -1                             
        1 row selected.
        ```

    -   **예상 결과**

        ```
        iSQL> SELECT  DBMS_METADATA.GET_DDL('SEQUENCE', 'S1', 'SYS') FROM DUAL;
        DBMS_METADATA.GET_DDL('SEQUENCE','S1','SYS
        -----------------------------------------------------------------------------------------------------
        CREATE SEQUENCE "SYS"."S1" START WITH 10000 INCREMENT BY -1 MINVALUE 1 MAXVALUE 10000                 
        1 row selected.
        iSQL> SELECT  DBMS_METADATA.GET_DDL('SEQUENCE', 'S2', 'SYS') FROM DUAL;
        DBMS_METADATA.GET_DDL('SEQUENCE','S2','SYS
        -----------------------------------------------------------------------------------------------------
        CREATE SEQUENCE "SYS"."S2" START WITH 9223372036854775806 INCREMENT BY -1 MINVALUE 1 MAXVALUE 922337 
        2036854775806                                                                                         
        1 row selected.
        ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49543 디스크 테이블 변경 트랜잭션 수행 중 삭제된 디스크 인덱스 키를 다시 삭제하는 버그로 Altibase 서버가 비정상 종료할 수 있습니다.

-   **module** : sm-disk-index

-   **Category** : Fatal

-   **재현 빈도** : Rare

-   **설명** : 디스크 테이블 변경 트랜잭션 수행 중 삭제된 디스크 인덱스 키를 다시 삭제 시도하는 경우 Altibase 서버가 비정상 종료하는 현상을 회피하고 원인 분석을 위한 로그를 추가합니다. 
    
    이 버그 반영 이후 현상 발생 시 다음과 같은 에러 메시지를 출력합니다. 

    ERR-11069 : Internal server error in the storage manager (fail to delete key - invalid key state)
    
    또한 디스크 인덱스 키를 다시 삭제 시도하는 원인 분석을 위해 트레이스 로그, altibase\_error.log에 아래와 같은 에러 메시지를 추가적으로 기록합니다.
    
    deleteKeyFromLeafNode() INVALID KEY STATE ( IndexID: *IndexID*, LeafKey: *LeafKey*, key state : *key state*, sequence number : *sequence number* )

    Delete Key by same TX (TID:*TID*),((smxTrans\*)(aMtx-\>mTrans))-\>mTransID );

    문제의 페이지를 덤프한 결과도 altibase\_dump.log 에 기록합니다.

-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

        이 버그로 인한 Altibase 서버 비정상 종료 발생 시 altibase_error.log 에 아래와 같은 콜스택이 남습니다. 

        ```
        [2021/12/13 21:58:29 32E85D][PID:6885][Thread-140305053693696][LWP-6948]
        
        leaf sequence number : 130
        
        [2021/12/13 21:58:29 32E861] Dump of Stack
        BEGIN-STACK [NORMAL] ============================
        Caller[0] 0000000000EC4DD8      => _ZN6ideLog23writeErrorTraceInternalEj12ideLogModulejPKcS2_jS2_P13__va_list_tag.constprop.2
        Caller[1] 0000000000EC8075      => ideLog::writeErrorTrace(char const*, idBool, char const*, unsigned int, char const*, __va_list_tag*)
        Caller[2] 0000000000EC3B2F      => ideLogError
        Caller[3] 0000000000D42CEF      => _ZN9sdnbBTree21deleteKeyFromLeafNodeEP6idvSQLP13sdnbStatisticP6sdrMtxP10sdnbHeaderP13sdpPhyPageHdrPs6idBoolPSB_.constprop.42
        Caller[4] 0000000000D62FC3      => sdnbBTree::deleteKey(idvSQL*, void*, void*, char*, smiIterator*, unsigned long)
        Caller[5] 0000000000DDEC3E      => smiTableCursor::deleteKeys(smiTableCursor*, scGRID, idBool)
        Caller[6] 0000000000DDEEA8      => smiTableCursor::deleteRowDRDB(smiTableCursor*, smiDMLRetryInfo const*)
        Caller[7] 0000000000DDAF45      => smiTableCursor::deleteRow(smiDMLRetryInfo const*)
        ...중략...
        END-STACK =======================================
        [2021/12/13 21:58:29 32E860][PID:6885][Thread-140305053693696][LWP-6948]
        IDE_ASSERT( 0 ), [sdnbModule.cpp:5950], errno=[16]
        errno=[16]
        
        [2021/12/13 21:58:29 32E862][PID:6885][Thread-140305053693696][LWP-6948]
        [ASSERT] ERROR LINE => [sdnbModule.cpp:5950]
        ERR-0109e(errno=16) Internal server error.
        
        altibase: /home/hdb651_p/work/altidev4/src/sm/sdn/sdnb/sdnbModule.cpp:5950: static IDE_RC sdnbBTree::deleteKeyFromLeafNode(idvSQL*, sdnbStatistic*, sdrMtx*, sdnbHeader*, sdpPhyPageHdr*, SShort*, idBool, idBool*): Assertion `0' failed.
        ```

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49544 언두 테이블스페이스에서 다수의 데이터 파일을 사용하는 경우 파일 확장 시 여유 공간이 있음에도 The tablespace does not have enough free space ( TBS Name : ). 에러가 발생하는 원인 분석을 위한 디버깅 로그를 추가합니다. 

-   **module** : sm-disk-page

-   **Category** : Functional Error

-   **재현 빈도** : Frequence

-   **설명** : 언두 테이블스페이스에서 다수의 데이터 파일을 사용하는 경우 파일 확장 시 여유 공간이 있음에도 The tablespace does not have enough free space ( TBS Name : ). 에러가 발생하는 원인 분석을 위한 디버깅 로그를 추가합니다. 

    Failed to expand UndoTBS File.
    UndoTBS FileName : *file_name*, FileID : *file_id*, CurrSize = *curr_size*, NextSize = *next_size*, MaxSize = *max_size*

    이 로그는 히든 프로퍼티 __ADDITIONAL_INFO_FOR_UNDOTBS_EXPAND_FAIL을 활성화해야 기록됩니다. (0 : 비활성화, 기본값 1 : 활성화)

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

### BUG-49553 SQL Plan Cache의 PCO(Plan Cache Object 교체 과정에서 해제한 메모리를 다시 해제하는 버그로 Altibase 서버가 비정상 종료할 수 있습니다.

-   **module** : qp

-   **Category** : Fatal

-   **재현 빈도** : Impossible

-   **설명** : SQL Plan Cache의 PCO(Plan Cache Object 교체 과정에서 해제한 메모리를 다시 해제하는 버그로 Altibase 서버가 비정상 종료하는 현상을 수정합니다.
    
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

### BUG-49563 OPTIMIZER\_FEATURE\_ENABLE 프로퍼티 값에 영향을 받는 프로퍼티를 추가합니다.

-   **module** : qp-dml-pvo

-   **Category** : Maintainability

-   **재현 빈도** : Unknown

-   **설명** : Altibase 6.3.1 옵티마이저와 동일한 옵티마이저 설정을 위해 \_\_OPTIMIZER\_INDEX\_COST\_MODE 프로퍼티의 설정값 2가
    추가되었습니다. 이 프로퍼티는 히든 프로퍼티로 관련 내용은 매뉴얼에 기록되지 않습니다.
    
    OPTIMIZER\_FEATURE\_ENABLE 설정값이 6.3.1.0.1 인 경우 이 프로퍼티의 설정값은 2가 됩니다.
    
    OPTIMIZER\_FEATURE\_ENABLE 프로퍼티 값을 6.5.1.0.0 이전 버전으로 설정하여 운영 중인 경우 Altibase 7.1.0.6.9 이전과 실행 계획이 달라질 수 있습니다.

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

### BUG-49564 OPTIMIZER\_FEATURE\_ENABLE 프로퍼티 값에 영향을 받는 프로퍼티 2개를 추가합니다.

-   **module** : qp-dml-pvo

-   **Category** : Maintainability

-   **재현 빈도** : Impossible

-   **설명** : OPTIMIZER\_FEATURE\_ENABLE 프로퍼티 값에 영향을 받는 프로퍼티 2개를 추가합니다.
    
    - \_\_OPTIMIZER\_AVG\_TRANSFORM\_ENABLE
    
    - \_\_OPTIMIZER\_INDEX\_NL\_JOIN\_ACCESS\_METHOD\_POLICY
    
    위 프로퍼티들은 Altibase 6.3.1 옵티마이저와 동일한 옵티마이저 설정을 위한 히든 프로퍼티로 매뉴얼에 기록되지 않습니다.
    
    OPTIMIZER\_FEATURE\_ENABLE 프로퍼티 값을 7.1.0.0.0 이전 버전으로 설정하여 운용 중인 Altibase 7.1.0.6.9 이전과 실행 계획이 변경될 수 있습니다.

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

### BUG-49565 Altibase 서버 구동 중 Refine Memory Table 단계에서 실패할 때 altibase\_error.log에 출력되는 에러 메시지를 보완합니다.

-   **module** : sm

-   **Category** : Functional Error

-   **재현 빈도** : Unknown

-   **설명** : Altibase 서버 구동 중 Refine Memory Table 단계에서 실패할 때 원인 분석을 위해 altibase\_error.log에 출력되는 에러 메시지를 보완합니다.
    
    이 버그 반영 후 ERR-00000(errno=16) 부분에 ERR-11088 Invalid row SCN 과 같이 보다 정확한 에러 코드와 에러 메시지를 출력합니다.

    ```
    [2022/01/11 00:14:56 416][PID:2150][Thread-47881693447936][LWP-2279]
    [FATAL] ERROR LINE => [smtPJMgr.cpp:154] MSG[error]
    ====== CURRENT IDE ERROR STACK =====
    ERR-00000(errno=16)
    [========= FATAL Terminated ==========]
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

### BUG-49572 CAST 연산자의 인자가 TIMESTAMP 인 경우 DATE로 변환하여 동작하는 Altibase 서버 프로퍼티를 추가합니다.

-   **module** : qp-select

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : CAST 연산자의 인자가 TIMESTAMP 인 경우 DATE로 변환하여 동작하는 Altibase 서버 프로퍼티 TIMESTAMP\_TO\_DATE를 추가합니다. 이 프로퍼티는 Tableau 연동을 위해 제공하는 것으로 기본 설정은 비활성화되어 있습니다.
    
    -   **프로퍼티 이름**
    
        TIMESTAMP\_TO\_DATE
    
    - **설명**
    
      - 0 - CAST 연산자의 인자가 TIMESTAMP인 경우 ERR-21011 : Invalid literal 에러가 발생한다. (기존 동작과 동일)
      - 1 - CAST 연산자의 인자가 TIMESTAMP인 경우 DATE로 변환하여 동작한다. 

    - **기본값**

      0

    - **속성**

      변경 가능, **비공개**

    본 버그를 적용하려면 TIMESTAMP\_TO\_DATE 값을 1로 설정해야 합니다.

-   **재현 방법**

    -   **재현 절차**

            SELECT CAST(SYSDATE AS TIMESTAMP) FROM DUAL;

    -   **수행 결과**

            [ERR-21011 : Invalid literal]

    -   **예상 결과**

            CAST(SYSDATEASTIMESTAMP) 
            ---------------------------
            21-FEB-2022  1 row selected.

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49576 Adapter for JDBC에서 지원하는 데이터 타입에 LOB을 추가합니다.

-   **module** : rp-jdbcAdapter

-   **Category** : Efficiency

-   **재현 빈도** : Always

-   **설명** : Adapter for JDBC에서 지원하는 데이터 타입에 LOB을 추가합니다.
    
    LOB 데이터 타입 지원 관련한 Adapter for JDBC 동작 및 제약 사항은 Adapter for JDBC 매뉴얼을 참고하시기 바랍니다.
    
    [Adapter for JDBC User’s Manual - 2.설치와 설정 - 프로퍼티 - OTHER\_DATABASE\_BATCH\_DML\_MAX\_SIZE](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase\_7.1/kor/Adapter%20for%20JDBC%20User's%20Manual.md\#other\_database\_batch\_dml\_max\_size-%EB%8B%A8%EC%9C%84-%EA%B0%9C%EC%88%98)

    [Adapter for JDBC User’s Manual - 2.설치와 설정 - 프로퍼티 - OTHER\_DATABASE\_ERROR\_RETRY\_COUNT](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase\_7.1/kor/Adapter%20for%20JDBC%20User's%20Manual.md\#other\_database\_error\_retry\_count-%EB%8B%A8%EC%9C%84-%ED%9A%9F%EC%88%98)
    
    [Adapter for JDBC User’s Manual - 2.설치와 설정 - 프로퍼티 - OTHER\_DATABASE\_SKIP\_ERROR](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase\_7.1/kor/Adapter%20for%20JDBC%20User's%20Manual.md\#other\_database\_skip\_error)
    
    [Adapter for JDBC User’s Manual - 3.사용법 - jdbcAdapter 제약조건 - LOB 데이터 타입 제약 사항](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase\_7.1/kor/Adapter%20for%20JDBC%20User's%20Manual.md\#lob-%EB%8D%B0%EC%9D%B4%ED%84%B0-%ED%83%80%EC%9E%85-%EC%A0%9C%EC%95%BD-%EC%82%AC%ED%95%AD)

-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

            ALA Log converter error: Unsupported data type.

    -   **예상 결과**

            LOB 데이터 타입 지원

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
|    7.1.0.6.9     |          6.5.1          |    8.10.1    |        7.1.7        |            7.4.7             |

> Altibase 7.1 패치 버전별 히스토리는 [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7_1_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

#### Meta Version

메타 버전은 변경되지 않았다.

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
