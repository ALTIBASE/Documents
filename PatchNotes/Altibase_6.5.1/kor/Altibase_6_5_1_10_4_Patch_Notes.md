Altibase 6.5.1.10.4 Patch Notes
===============================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Fixed Bugs](#fixed-bugs)
    - [BUG-51144 테이블 스키마와 인덱스 스키마가 다른 Cross-schema reference 인덱스 통계 정보 수집을 지원해야 합니다.](#bug-51144)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Fixed Bugs
==========

### BUG-51144<a name=bug-51144></a> 테이블 스키마와 인덱스 스키마가 다른 Cross-schema reference 인덱스 통계 정보 수집을 지원해야 합니다.

-   **module** : ux-aexport

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : COLLECT_DBMS_STATS를 ON으로 설정한 상태에서 aexport를 수행할 때 발생하던 문제를 수정했습니다. 테이블 소유자와 인덱스 소유자가 다른 경우, 인덱스 통계 정보를 추출하는 과정에서 aexport가 비정상적으로 종료되는 결함을 수정했습니다.
    
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

Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 6.5.1.10.4       | 6.3.1                   | 8.1.1        | 7.1.3               | 7.4.5                        |

> Altibase 6.5.1 패치 버전별 히스토리는 [Version_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_6.5.1/Altibase_6_5_1_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의
> 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는
> 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

#### CM protocol Version

통신 프로토콜 버전은 변경되지 않았다.

#### Replication protocol Version

Replication 프로토콜 버전은 변경되지 않았다.

### 프로퍼티

추가/변경/삭제된 프로퍼티 없음.

### 성능 뷰

추가/변경/삭제된 성능뷰 없음.
