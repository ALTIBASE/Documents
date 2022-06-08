# Altibase 6.1.1.10.3 Patch Notes

<br/>

<br/>

# Table of Contents 

- [Fixed Bugs](#fixed-bugs)
  - [BUG-49283 UNIQUE INSERT 수행 시 LOCK WAIT 상황에서 V\$SESSION\_WAIT에 no wait event가 발생합니다. wait event가 수집되지 않습니다.](#bug-49283unique-insert-수행-시-lock-wait-상황에서-vsession_wait에-no-wait-event가-발생합니다-wait-event가-수집되지-않습니다)
  - [BUG-49673 가비지 콜렉션(Ager) 수행 시 Delete Thread가 삭제한 오래된 버전의 데이터를 삭제 대상으로 잘못 판단하여 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-49673가비지-콜렉션ager-수행-시-delete-thread가-삭제한-오래된-버전의-데이터를-삭제-대상으로-잘못-판단하여-altibase-서버가-비정상-종료할-수-있습니다)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [호환성](#호환성)
  - [프로퍼티](#프로퍼티)
  - [성능 뷰](#성능-뷰)

<br/>

Fixed Bugs
==========

### BUG-49283 UNIQUE INSERT 수행 시 LOCK WAIT 상황에서 V\$SESSION\_WAIT에 no wait event가 발생합니다. wait event가 수집되지 않습니다.

-   **module** : sm

-   **Category** : Functional Error

-   **재현 빈도** : Unknown

-   **설명** : UNIQUE INSERT 수행 시 LOCK WAIT 상황에서 V\$SESSION\_WAIT 또는 V\$STATEMENT 에 wait event가 수집되지 않는 현상을 수정합니다.
    이 버그는 디스크 테이블에만 해당합니다. 메모리 테이블 경우 대기 이벤트가 없어 같은 상황에서 no wait event 발생하는 것은 정상 상황입니다.
    
-   **재현 방법**

    -   **재현 절차**

        -   A 세션

            ```sql
            iSQL> CREATE TABLE bug49283 (c1 INTEGER PRIMARY KEY) TABLESPACE SYS_TBS_DISK_DATA;
            iSQL> ALTER SYSTEM SET TIMED_STATISTICS = 1;
            iSQL> AUTOCOMMIT OFF;
            iSQL> INSERT INTO bug49283 VALUES(1);
            ```

        -   B 세션

            ```sql
            iSQL> AUTOCOMMIT OFF;
            iSQL> INSERT INTO bug49283 VALUES(1);
            ```

        -   A 세션

            ```
            iSQL> SELECT * FROM V$LOCK_WAIT;
            iSQL> SELECT SID, EVENT FROM V$SESSION_WAIT WHERE SID <> SESSION_ID();
            iSQL> SELECT TX_ID, SESSION_ID, EVENT, SUBSTR(QUERY, 1, 60) QRY 
                    FROM V$STATEMENT WHERE SESSION_ID <> SESSION_ID();
            ```

    -   **수행 결과**

        ```sql
        iSQL> SELECT * FROM V$LOCK_WAIT;
        TRANS_ID    WAIT_FOR_TRANS_ID    
        ------------------------------------
        1408        21633                
        1 row selected.
        iSQL> SELECT SID, EVENT FROM V$SESSION_WAIT WHERE SID <> SESSION_ID();
        SID         EVENT                                     
        ---------------------------------------------------------
        2           no wait event   
        1 row selected.
        iSQL> SELECT TX_ID, SESSION_ID, EVENT, SUBSTR(QUERY, 1, 60) QRY FROM V$STATEMENT WHERE SESSION_ID <> SESSION_ID();
        TX_ID       SESSION_ID  EVENT                                     QRY                                       
        -----------------------------------------------------------------------------------------------------------------
        1408        2           no wait event                             INSERT INTO bug49283_m VALUES(1)          
        1 row selected.
        ```

    -   **예상 결과**

        ```sql
        iSQL> SELECT * FROM V$LOCK_WAIT;
        TRANS_ID    WAIT_FOR_TRANS_ID    
        ------------------------------------
        1408        21633                
        1 row selected.
        iSQL> SELECT SID, EVENT FROM V$SESSION_WAIT WHERE SID <> SESSION_ID();
        SID         EVENT                                     
        ---------------------------------------------------------
        2           enq: TX - row lock contention, data row   
        1 row selected.
        iSQL> SELECT TX_ID, SESSION_ID, EVENT, SUBSTR(QUERY, 1, 60) QRY FROM V$STATEMENT WHERE SESSION_ID <> SESSION_ID();
        TX_ID       SESSION_ID  EVENT                                     QRY                                       
        -----------------------------------------------------------------------------------------------------------------
        1408        2           enq: TX - row lock contention, data row   INSERT INTO bug49283 VALUES(1)            
        1 row selected.
        ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49673 가비지 콜렉션(Ager) 수행 시 Delete Thread가 삭제한 오래된 버전의 데이터를 삭제 대상으로 잘못 판단하여 Altibase 서버가 비정상 종료할 수 있습니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Rare

-   **설명** : 메모리 테이블에 변경 트랜잭션 수행 중 다중 버전 동시성 제어(MVCC)으로 생성된 복제본은 어떤 트랜잭션에서도 참조하지 않으면 가비지 콜렉션(Ager)에 의해 삭제됩니다. 가비지 콜렉션 수행 시 Delete Thread가 삭제한 오래된 버전의 데이터를 삭제 대상으로 판단하여, 잘못된 메모리 접근으로 Altibase 서버가 비정상 종료하는 현상이 발생합니다. Altibase 서버가 비정상 종료할 때 altibase\_error.log 로그에 아래와 에러 메시지가 남습니다.
    
    IDE_ASSERT(aFreePageHeader->mFreeSlotCount == 0)[smpFixedPageList.cpp:1519], errno=[16]
    
    이러한 버그로 Altibase 서버가 비정상 종료하는 현상을 방지하고 삭제 대상을 잘못 판단하는 원인 분석을 위해 디버깅 로그를 추가합니다. Altibase 서버 비정상 종료 현상 방지 및 디버깅 로그는 새로 추가한 비공개 프로퍼티의 값을 변경해야 적용됩니다.
    
    - **이름**
    
      \_\_NEED\_OIDLIST\_DUMP
    
    - **설명**
    
      가비지 콜렉션 수행 시 잘못된 메모리 접근으로 Altibase 서버가 비정상 종료하는 현상을 방지합니다. 그리고 가비지 콜렉션에서 삭제 대상을 잘못 판단하는 원인을 파악하기 위해 디버깅 로그를 출력합니다.
    
      - 0 : Altibase 서버 비정상 종료 방지 및 디버깅 로그 출력 미적용
    
      - 1 : Altibase 서버 비정상 종료 방지 및 디버깅 로그 출력 적용
    
    - **기본값**
    
      0
    
    - **속성**
    
      비공개
    
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

<br/>

Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    6.1.1.10.3    |          6.1.1          |    5.14.1    |        5.6.3        |            6.1.1             |

> Altibase 6.1.1 패치 버전 별 히스토리는 [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_6.1.1/Altibase_6_1_1_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는 데이터베이스를 재구성해야 한다.

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
