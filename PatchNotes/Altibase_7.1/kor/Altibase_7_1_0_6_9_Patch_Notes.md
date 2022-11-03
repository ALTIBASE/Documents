Altibase 7.1.0.6.9 Patch Notes
==============================

<br/>

<br/>

# Table of Contents  

- [Fixed Bugs](#fixed-bugs)
  - [BUG-47420 LENGTH()로 LOB 길이 출력 시 Altibase 서버가 비정상 종료하고 디스크 테이블에 LOB 데이터 타입의 최대 크기를 초과하여 입력되는 현상을 수정합니다.](#bug-47420length로-lob-길이-출력-시-altibase-서버가-비정상-종료하고-디스크-테이블에-lob-데이터-타입의-최대-크기를-초과하여-입력되는-현상을-수정합니다)
  - [BUG-49133 SORT\_AREA\_SIZE 값을 최소값 524288으로 설정하고 TEMP\_HASH\_BUCKET\_DENSITY 설정값을 65이상 설정한 경우 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-49133sort_area_size-값을-최소값-524288으로-설정하고-temp_hash_bucket_density-설정값을-65이상-설정한-경우-altibase-서버가-비정상-종료할-수-있습니다)
  - [BUG-49439 AUDIT disconnect 설정 환경에서 데이터베이스 세션 종료 시 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-49439audit-disconnect-설정-환경에서-데이터베이스-세션-종료-시-altibase-서버가-비정상-종료할-수-있습니다)
  - [BUG-49473 DBMS\_METADATA 패키지의 GET\_DDL 함수에 시퀀스 객체 지정 시 시퀀스 속성과 다른 MIN, MAX 값을 가진 구문이 추출될 수 있습니다.](#bug-49473dbms_metadata-패키지의-get_ddl-함수에-시퀀스-객체-지정-시-시퀀스-속성과-다른-min-max-값을-가진-구문이-추출될-수-있습니다)
  - [BUG-49543 디스크 테이블 변경 트랜잭션 수행 중 삭제된 디스크 인덱스 키를 다시 삭제하는 버그로 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-49543디스크-테이블-변경-트랜잭션-수행-중-삭제된-디스크-인덱스-키를-다시-삭제하는-버그로-altibase-서버가-비정상-종료할-수-있습니다)
  - [BUG-49544 언두 테이블스페이스에서 다수의 데이터 파일을 사용하는 경우 파일 확장 시 여유 공간이 있음에도 The tablespace does not have enough free space ( TBS Name : ). 에러가 발생하는 원인 분석을 위한 디버깅 로그를 추가합니다. ](#bug-49544-언두-테이블스페이스에서-다수의-데이터-파일을-사용하는-경우-파일-확장-시-여유-공간이-있음에도-the-tablespace-does-not-have-enough-free-space--tbs-name---에러가-발생하는-원인-분석을-위한-디버깅-로그를-추가합니다)
  - [BUG-49553 SQL Plan Cache의 PCO(Plan Cache Object 교체 과정에서 해제한 메모리를 다시 해제하는 버그로 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-49553sql-plan-cache의-pcoplan-cache-object-교체-과정에서-해제한-메모리를-다시-해제하는-버그로-altibase-서버가-비정상-종료할-수-있습니다)
  - [BUG-49565 Altibase 서버 구동 중 Refine Memory Table 단계에서 실패할 때 altibase\_error.log에 출력되는 에러 메시지를 보완합니다.](#bug-49565altibase-서버-구동-중-refine-memory-table-단계에서-실패할-때-altibase_errorlog에-출력되는-에러-메시지를-보완합니다)
  - [BUG-49576 Adapter for JDBC에서 지원하는 데이터 타입에 LOB을 추가합니다.](#bug-49576adapter-for-jdbc에서-지원하는-데이터-타입에-lob을-추가합니다)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [호환성](#호환성)
  - [프로퍼티](#프로퍼티)
  - [성능 뷰](#성능-뷰)

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
