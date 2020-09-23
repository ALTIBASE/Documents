<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Altibase 7.1.0.2.8 Patch Notes](#altibase-71028-patch-notes)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-47149  Standby server에서 conflict를 포함한 트랜잭션 abort가 발생한 순간, 사용자가 V$REPRECEIVER_TRANSTBL 를 조회하면 서버가 비정상 종료할 수 있습니다.](#bug-47149-sender%EC%97%90%EC%84%9C-conflict%EB%A5%BC-%ED%8F%AC%ED%95%A8%ED%95%9C-%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98-abort%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%9C-%EC%88%9C%EA%B0%84-%EC%82%AC%EC%9A%A9%EC%9E%90%EA%B0%80-vrepreceiver_transtbl-%EB%A5%BC-%EC%A1%B0%ED%9A%8C%ED%95%98%EB%A9%B4-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-47155  sender가 updateXSN()을 호출할 때, sender의 mXSN보다 업데이트 할 SN값이 크다면, update을 수행하지 않습니다.](#bug-47155-sender%EA%B0%80-updatexsn%EC%9D%84-%ED%98%B8%EC%B6%9C%ED%95%A0-%EB%95%8C-sender%EC%9D%98-mxsn%EB%B3%B4%EB%8B%A4-%EC%97%85%EB%8D%B0%EC%9D%B4%ED%8A%B8-%ED%95%A0-sn%EA%B0%92%EC%9D%B4-%ED%81%AC%EB%8B%A4%EB%A9%B4-update%EC%9D%84-%EC%88%98%ED%96%89%ED%95%98%EC%A7%80-%EC%95%8A%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-47306  이중화가 여러개 구성되어있는 경우 온라인 DDL 수행시 DDL이 실패하는 문제 수정](#bug-47306-%EC%9D%B4%EC%A4%91%ED%99%94%EA%B0%80-%EC%97%AC%EB%9F%AC%EA%B0%9C-%EA%B5%AC%EC%84%B1%EB%90%98%EC%96%B4%EC%9E%88%EB%8A%94-%EA%B2%BD%EC%9A%B0-%EC%98%A8%EB%9D%BC%EC%9D%B8-ddl-%EC%88%98%ED%96%89%EC%8B%9C-ddl%EC%9D%B4-%EC%8B%A4%ED%8C%A8%ED%95%98%EB%8A%94-%EB%AC%B8%EC%A0%9C-%EC%88%98%EC%A0%95)
    - [BUG-47325  조회 결과 출력시 개행문자로 인해 잘못된 위치에서 줄바꿈을 합니다](#bug-47325-%EC%A1%B0%ED%9A%8C-%EA%B2%B0%EA%B3%BC-%EC%B6%9C%EB%A0%A5%EC%8B%9C-%EA%B0%9C%ED%96%89%EB%AC%B8%EC%9E%90%EB%A1%9C-%EC%9D%B8%ED%95%B4-%EC%9E%98%EB%AA%BB%EB%90%9C-%EC%9C%84%EC%B9%98%EC%97%90%EC%84%9C-%EC%A4%84%EB%B0%94%EA%BF%88%EC%9D%84-%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-47334  HASH, SORT Size가 32GB를 넘지 못합니다.](#bug-47334-hash-sort-size%EA%B0%80-32gb%EB%A5%BC-%EB%84%98%EC%A7%80-%EB%AA%BB%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-47359  SQL\_NUMERIC\_STRUCT가 apre keyword에 누락되어 있습니다.](#bug-47359-sql%5C_numeric%5C_struct%EA%B0%80-apre-keyword%EC%97%90-%EB%88%84%EB%9D%BD%EB%90%98%EC%96%B4-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-47361  IS NOT NULL이 SERIAL EXECUTE로 수행 되지 않습니다.](#bug-47361-is-not-null%EC%9D%B4-serial-execute%EB%A1%9C-%EC%88%98%ED%96%89-%EB%90%98%EC%A7%80-%EC%95%8A%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-47364  File Resize Recovery 에서 예외 처리가 되어 있지 않은 부분이 있어 수정합니다.](#bug-47364-file-resize-recovery-%EC%97%90%EC%84%9C-%EC%98%88%EC%99%B8-%EC%B2%98%EB%A6%AC%EA%B0%80-%EB%90%98%EC%96%B4-%EC%9E%88%EC%A7%80-%EC%95%8A%EC%9D%80-%EB%B6%80%EB%B6%84%EC%9D%B4-%EC%9E%88%EC%96%B4-%EC%88%98%EC%A0%95%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Altibase 7.1.0.2.8 Patch Notes
==============================

Fixed Bugs
----------

### BUG-47149  Standby Server에서 conflict를 포함한 트랜잭션 abort가 발생한 순간, 사용자가 V$REPRECEIVER_TRANSTBL 를 조회하면 서버가 비정상 종료할 수 있습니다.

-   **module** : rp

-   **Category** : Fatal

-   **재현 빈도** : Rare

-   **증상** : standby server 에서 conflict 를 포함한
    transaction abort가 발생한 순간, V$REPRECEIVER\_TRANSTBL 를
    조회하면 서버가 비정상 종료할 수 있습니다.

    V$REPRECEIVER\_TRANSTBL 의 LOCAL\_TID(local\_transaction\_id)
    컬럼을 조회하는 도중에 free된 transaction 정보를 참조하기 때문입니다.
    

따라서, transaction begin 시점에 LOCAL\_TID를 가져오도록 수정하였습니다.
    
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

### BUG-47155  sender가 updateXSN()을 호출할 때, sender의 mXSN보다 업데이트 할 SN값이 크다면, update을 수행하지 않습니다.

-   **module** : dm

-   **Category** : Functional Error

-   **재현 빈도** : Unknown

-   **증상** : 이중화 active- active 환경에서 한방향 replication만 기동되는 문제가 있어, 수정하였습니다. sender 가 마지막으로 보냈던 xsn 을 업데이트 할때 잘못된 값이 update 가 되는것을 방지하기 위해 마지막으로 쓰인 로그보다 높은 SN 값을 쓰려고 한다면 재시도 하도록
    변경합니다. 재시도를 여러차례 해도 문제가 생길 시 이중화를 종료합니다.

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

### BUG-47306  이중화가 여러개 구성되어있는 경우 온라인 DDL 수행시 DDL이 실패하는 문제 수정

-   **module** : rp

-   **Category** : Functional Error

-   **재현 빈도** : Frequence

-   **증상** : 이중화가 여러개 구성되어 있는 경우, 온라인 DDL 수행시 동시성 문제로  DDL이 실패할 수 있어
    

수정합니다.
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

### BUG-47325  조회 결과 출력시 개행문자로 인해 잘못된 위치에서 줄바꿈을 합니다

-   **module** : ux-isql

-   **Category** : Usability

-   **재현 빈도** : Always

-   **증상** : 조회 결과 출력시 개행문자로 인해 잘못된 위치에서 줄바꿈되는 문제가 있어 수정하였습니다.
    
-   **재현 방법**

    -   **재현 절차**

            drop table t1;
            create table t1(i1 varchar(200));
            insert into t1 values('USING INDEX PCTFREE 10 INITRANS 2 MAXTRANS 255 COMPUTE STATISTICS NOCOMPRESS LOGGING' || chr(10) || 'USING INDEX PCTFREE 10 INITRANS 2 MAXTRANS 255 COMPUTE STATISTICS NOCOMPRESS LOGGING');
            set colsize 50
            select * From t1;

    -   **수행 결과**

            iSQL> select * From t1;
            T1.I1
            ------------------------------------------------------
            USING INDEX PCTFREE 10 INITRANS 2 MAXTRANS 255 COM
            PUTE STATISTICS NOCOMPRESS LOGGING
            USING INDEX PCT
            FREE 10 INITRANS 2 MAXTRANS 255 COMPUTE STATISTICS
             NOCOMPRESS LOGGING

    -   **예상 결과**

            SQL> select * From t1;
            USING INDEX PCTFREE 10 INITRANS 2 MAXTRANS 255 COM
            PUTE STATISTICS NOCOMPRESS LOGGING
            USING INDEX PCTFREE 10 INITRANS 2 MAXTRANS 255 COM
            PUTE STATISTICS NOCOMPRESS LOGGING

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47334  HASH, SORT Size가 32GB를 넘지 못합니다.

-   **module** : sm-disk-resource

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** :  SORT_AREA_SIZE, HASH_AREA_SIZE 를 32GB 이상 설정할수 없는 문제를 수정하였습니다.

- **재현 방법**

  -   **재현 절차**

  -   **수행 결과**

  -   **예상 결과**

-   **Workaround**

        SORT_AREA_SIZE, HASH_AREA_SIZE Property 를 34331426816 이하로 설정

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

-   -   

### BUG-47359  SQL\_NUMERIC\_STRUCT가 apre keyword에 누락되어 있습니다.

-   **module** : mm-apre

-   **Category** : Other

-   **재현 빈도** : Always

-   **증상** : apre keyword 에 SQL\_NUMERIC\_STRUCT이 누락되어, 수정하였습니다. apre -keyword 로 조회할 수 있습니다.

-   **재현 방법**

    -   **재현 절차**

            apre -keyword

    -   **수행 결과**

    - **예상 결과**
    
-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47361  IS NOT NULL이 SERIAL EXECUTE로 수행 되지 않습니다.

-   **module** : mt

-   **Category** : Other

-   **재현 빈도** : Always

-   **증상** :  IS NOT NULL을 SERIAL EXECUTE로 수행 되도록 수정.

- **재현 방법**

  -   **재현 절차**

          alter session set explain plan = on;
          alter session set trclog_detail_predicate =1;
          alter session set serial_execute_mode = 1;
          SET VERTICAL ON;
          DROP TABLE T2;
          CREATE TABLE T2 (I1 INT, I2 INT, I3 INT);
          INSERT INTO T2 VALUES (1,1,1);
          INSERT INTO T2 VALUES (2,NULL,2);
          INSERT INTO T2 VALUES (3,3,3);
          SELECT * FROM T2 WHERE I2 IS NOT NULL;
      
  - **수행 결과**

    ```
    iSQL> SELECT * FROM T2 WHERE I2 IS NOT NULL;
    I1 : 1
    I2 : 1
    I3 : 1
    I1 : 3
    I2 : 3
    I3 : 3
    3 rows selected.
    ------------------------------------------------------------
    PROJECT ( COLUMN_COUNT: 3, TUPLE_SIZE: 12, COST: 122.96 )
     SCAN ( TABLE: SYS.T2, FULL SCAN, ACCESS: 3, COST: 119.40 )
      [ FILTER  ]
      I2 IS NOT NULL
    ------------------------------------------------------------
    ```

    

  -   **예상 결과**

          iSQL> SELECT * FROM T2 WHERE I2 IS NOT NULL;
          I1 : 1
          I2 : 1
          I3 : 1
          I1 : 3
          I2 : 3
          I3 : 3
          2 rows selected.
          ------------------------------------------------------------
          PROJECT ( COLUMN_COUNT: 3, TUPLE_SIZE: 12, COST: 122.96 )
           SCAN ( TABLE: SYS.T2, FULL SCAN, ACCESS: 3, COST: 119.40 )
            [ FILTER SERIAL EXECUTE ]
            I2 IS NOT NULL
          ------------------------------------------------------------

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47364  File Resize Recovery 에서 예외 처리가 되어 있지 않은 부분이 있어 수정합니다.

-   **module** : sm-disk-recovery

-   **Category** : Hang

-   **재현 빈도** : Always

-   **증상** : File Resize Recovery 에서 예외 처리가 되어 있지 않은 부분이 있어 수정합니다.

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
-------

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version | sharding version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- | ---------------- |
| 7.1.0.2.8        | 6.5.1                   | 8.7.1        | 7.1.7               | 7.4.5                        | 2.2.1            |

> Altibase 7.1 패치 버전별 히스토리는 [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7_1_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의
> 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는
> 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

> 패치를 롤백하려는 경우, [메타다운그레이드](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Installation.md#%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9Cmeta-downgrade)를 참고한다.

#### CM protocol Version

통신 프로토콜 버전은 변경되지 않았다.

#### Replication protocol Version

Replication 프로토콜 버전은 변경되지 않았다.

#### Sharding Version

샤딩 버전은 변경 되지 않았다.

> 알티베이스 샤딩 프로토콜 및 메타는 상위, 하위 호환성을 보장하지
> 않는다. 즉, 샤딩 버전이 다른 경우, 재구성해야 한다.

### 프로퍼티

추가/변경/삭제된 프로퍼티 없음

### 성능 뷰

추가/변경/삭제된 성능뷰 없음
