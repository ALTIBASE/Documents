# Altibase 6.5.1.9.5 Patch Notes

<br/>

<br/>

# Table of Contents

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Fixed Bugs](#fixed-bugs)
  - [BUG-49913 Lateral view로 사용된 파티션드 테이블이 병렬 질의로 처리되어 발생하는 안정성 문제를 개선합니다.](#bug-49913lateral-view%EB%A1%9C-%EC%82%AC%EC%9A%A9%EB%90%9C-%ED%8C%8C%ED%8B%B0%EC%85%98%EB%93%9C-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%9D%B4-%EB%B3%91%EB%A0%AC-%EC%A7%88%EC%9D%98%EB%A1%9C-%EC%B2%98%EB%A6%AC%EB%90%98%EC%96%B4-%EB%B0%9C%EC%83%9D%ED%95%98%EB%8A%94-%EC%95%88%EC%A0%95%EC%84%B1-%EB%AC%B8%EC%A0%9C%EB%A5%BC-%EA%B0%9C%EC%84%A0%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49987 FROM 절에 인라인 뷰, GROUP BY 절에 문자 함수, SELECT 절과 분석 함수 ORDER BY 절에 GROUP BY 절의 키를 사용할 때 발생하는 안정성 문제를 개선합니다.](#bug-49987from-%EC%A0%88%EC%97%90-%EC%9D%B8%EB%9D%BC%EC%9D%B8-%EB%B7%B0-group-by-%EC%A0%88%EC%97%90-%EB%AC%B8%EC%9E%90-%ED%95%A8%EC%88%98-select-%EC%A0%88%EA%B3%BC-%EB%B6%84%EC%84%9D-%ED%95%A8%EC%88%98-order-by-%EC%A0%88%EC%97%90-group-by-%EC%A0%88%EC%9D%98-%ED%82%A4%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%A0-%EB%95%8C-%EB%B0%9C%EC%83%9D%ED%95%98%EB%8A%94-%EC%95%88%EC%A0%95%EC%84%B1-%EB%AC%B8%EC%A0%9C%EB%A5%BC-%EA%B0%9C%EC%84%A0%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49994 윈도우 함수의 window\_order\_clause 절에서 NULLS 및 window\_frame\_clause 절 사용 시 정합성 오류가 발생할 수 있습니다.](#bug-49994%EC%9C%88%EB%8F%84%EC%9A%B0-%ED%95%A8%EC%88%98%EC%9D%98-window_order_clause-%EC%A0%88%EC%97%90%EC%84%9C-nulls-%EB%B0%8F-window_frame_clause-%EC%A0%88-%EC%82%AC%EC%9A%A9-%EC%8B%9C-%EC%A0%95%ED%95%A9%EC%84%B1-%EC%98%A4%EB%A5%98%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-50032 oaUtility 유틸리티에 force 옵션을 추가합니다.](#bug-50032oautility-%EC%9C%A0%ED%8B%B8%EB%A6%AC%ED%8B%B0%EC%97%90-force-%EC%98%B5%EC%85%98%EC%9D%84-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-50054 ALTER REPLICATION \~ SYNC가 30초 이상 지속하면 HeartBeat 쓰레드에 의해 이중화 SYNC가 실패합니다.](#bug-50054alter-replication--sync%EA%B0%80-30%EC%B4%88-%EC%9D%B4%EC%83%81-%EC%A7%80%EC%86%8D%ED%95%98%EB%A9%B4-heartbeat-%EC%93%B0%EB%A0%88%EB%93%9C%EC%97%90-%EC%9D%98%ED%95%B4-%EC%9D%B4%EC%A4%91%ED%99%94-sync%EA%B0%80-%EC%8B%A4%ED%8C%A8%ED%95%A9%EB%8B%88%EB%8B%A4)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
  - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
  - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Fixed Bugs
==========

### BUG-49913 Lateral view로 사용된 파티션드 테이블이 병렬 질의로 처리되어 발생하는 안정성 문제를 개선합니다.

#### module

`qp`

#### Category

`Fatal`

#### 재현 빈도 

`Always`

#### 설명 

Lateral view로 사용된 파티션드 테이블을 병렬 질의로 처리되어 Altibase 서버가 비정상 종료합니다. Lateral view는 병렬
질의를 지원하는 대상이 아니므로 병렬 질의로 처리하지 않도록 수정합니다.

이 버그는 아래와 같은 조건에서 발생합니다.

- 파티션드 테이블에 PARALLEL 절을 지정하거나 PARALLEL 힌트를 사용

- 파티션드 테이블이 사용된 인라인 뷰를 Lateral View로 정의(LATERAL 또는 APPLY 키워드 사용)

#### 재현 방법

-   **재현 절차**

    ```sql
    DROP TABLE T1; 
    DROP TABLE T2;
    
    CREATE TABLE T2( I1 INTEGER, I2 INTEGER ) 
    PARTITION BY HASH(I1) 
    ( PARTITION P1, 
      PARTITION P2 
    ) TABLESPACE SYS_TBS_MEM_DATA;
    
    ALTER TABLE T2 PARALLEL 4;
    
    CREATE TABLE T1 (I1 INTEGER, I2 INTEGER);
    INSERT INTO T2 VALUES( 4, 4 );
    
    SELECT *
      FROM T1 
      OUTER APPLY (SELECT SUM(T1.I1) AS I1 FROM T2
                   INTERSECT
                   SELECT COUNT(T1.I2) AS I1 FROM T2 );
    ```

-   **수행 결과**

    ```sql
    [ERR-91015 : Communication failure.]
    ```

-   **예상 결과**

    ```sql
    I1          I2          I1                   
    -------------------------------------------------
    No rows selected.
    ```

#### Workaround

/*+ NOPARALLEL */ 힌트 사용

```sql
SELECT *
  FROM T1 
  OUTER APPLY (SELECT /*+ NOPARALLEL */ SUM(T1.I1) AS I1 FROM T2
               INTERSECT
               SELECT /*+ NOPARALLEL */ COUNT(T1.I2) AS I1 FROM T2 );
```

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-49987 FROM 절에 인라인 뷰, GROUP BY 절에 문자 함수, SELECT 절과 분석 함수 ORDER BY 절에 GROUP BY 절의 키를 사용할 때 발생하는 안정성 문제를 개선합니다.

#### module 
`qp-select`

#### CategoryFatal

#### 재현 빈도 Always

#### 설명

FROM 절에 인라인 뷰, GROUP BY 절에 문자 함수, SELECT 절과 분석 함수 ORDER BY 절에 GROUP BY 절의 키를 사용할 때 Altibase 서버가 비정상 종료하는 현상을 수정합니다.

#### 재현 방법

-   **재현 절차**

    ```sql
    CREATE TABLE T1 ( YYYYMM VARCHAR(6) );
    INSERT INTO T1 VALUES ('201901');
    
    CREATE TABLE T2 ( YYYYMM VARCHAR(6) );
    INSERT INTO T2 VALUES ('202001');
    
    SELECT SUBSTR(B1.YYYYMM,1,4) || 'A' AS ACT_YYYY              
         , ROW_NUMBER() OVER( ORDER BY SUBSTR(B1.YYYYMM,1,4)) AS PK_COL
      FROM T1 B2
         , (SELECT A2.YYYYMM AS YYYYMM FROM T2 A2) B1
      WHERE B2.YYYYMM (+)= B1.YYYYMM
      GROUP BY SUBSTR(B1.YYYYMM,1,4);
    ```

-   **수행 결과**

    ```sql
    [ERR-91015 : Communication failure.]
    ```

-   **예상 결과**

        정상 수행

#### Workaround

`없음`

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-49994 윈도우 함수의 window\_order\_clause 절에서 NULLS 및 window\_frame\_clause 절 사용 시 정합성 오류가 발생할 수 있습니다.

#### module

`qp-select`

#### Category

`Functional Error`

#### 재현 빈도 

`Always`

#### 설명

윈도우 함수의 window\_order\_clause 절에서 NULLS 및 window\_frame\_clause 절 사용 시 결과 오류가 발생하는 문제를
개선합니다.

#### 재현 방법

-   **재현 절차**

    ```sql
    CREATE TABLE T1 ( I1 INTEGER, I2 INTEGER, I3 INTEGER );
    INSERT INTO T1 VALUES(   1,    1,    1);
    INSERT INTO T1 VALUES(   1,    1,    1);
    INSERT INTO T1 VALUES(   2,    1,    1);
    INSERT INTO T1 VALUES(   2,    2,    1);
    INSERT INTO T1 VALUES(   2,    1,    2);
    INSERT INTO T1 VALUES(   2,    1,    1);
    INSERT INTO T1 VALUES(   2,    3,    1);
    INSERT INTO T1 VALUES(   3,    3,    1);
    INSERT INTO T1 VALUES(   1,    1,    3);
    INSERT INTO T1 VALUES(   1,    2,    3);
    INSERT INTO T1 VALUES(NULL,    2,    3);
    INSERT INTO T1 VALUES(NULL, NULL,    3);
    INSERT INTO T1 VALUES(NULL, NULL, NULL);
    
    SELECT COUNT(I3) OVER (PARTITION BY I1 ORDER BY I2 NULLS LAST ROWS UNBOUNDED PRECEDING) C1
         , COUNT(I3) OVER (PARTITION BY I1 ORDER BY I2 NULLS LAST RANGE 1 PRECEDING) C7
      FROM T1
     GROUP BY I1,I2,I3
     ORDER BY C1,C7;
    ```

-   **수행 결과**

    ```sql
    C1                   C7
    ---------------------------------------------
    1                    1
    1                    1
    2                    1
    2                    1
    1                    2
    2                    2
    1                    2
    2                    2
    4                    2
    3                    3
    3                    3
    11 rows selected.
    ```

-   **예상 결과**

    ```sql
    C1                   C7
    ---------------------------------------------
    1                    1
    1                    1
    1                    2
    1                    2
    2                    1
    2                    1
    2                    2
    2                    2
    3                    3
    3                    3
    4                    2
    11 rows selected.
    ```


#### Workaround

```sql
SELECT *
  FROM (SELECT COUNT(I3) OVER (PARTITION BY I1 ORDER BY I2 NULLS LAST ROWS UNBOUNDED PRECEDING) C1
             , COUNT(I3) OVER (PARTITION BY I1 ORDER BY I2 NULLS LAST RANGE 1 PRECEDING) C7
          FROM T1
         GROUP BY I1,I2,I3 )
 ORDER BY C1,C7;
```

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50032 oaUtility 유틸리티에 force 옵션을 추가합니다.

#### module

`rp-oraAdapter`

#### Category

`Enhancement`

#### 재현 빈도

`Rare`

#### 설명

oaUtility 유틸리티에 force 옵션을 추가합니다. 이 옵션은 복제 대상 테이블에 프라이머리 키 제약 조건이 있는지 확인하지 않고 oraAdapter를 시작합니다.

#### 재현 방법

-   **재현 절차**

-   **수행 결과**

-   **예상 결과**

#### Workaround

`없음`

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50054 ALTER REPLICATION \~ SYNC가 30초 이상 지속하면 HeartBeat 쓰레드에 의해 이중화 SYNC가 실패합니다.

#### module

`rp-sender`

#### Category

`Functional Error`

#### 재현 빈도

`Frequence`

#### 설명

ALTER REPLICATION \~ SYNC가 일정 시간 이상 지속하면 HeartBeat 쓰레드에 의해 이중화 SYNC가 실패하는 현상을 수정합니다.

HeartBeat 쓰레드에서 원격 서버의 IP가 아닌 127.0.0.1로 원격 서버의 상태를 점검하는 문제가 발견되었습니다. 이로인해 이중화 SYNC를 시작하는 시점부터 HeartBeat 쓰레드에서 원격 서버와의 통신이 실패하고 REPLICATION\_HBT\_DETECT\_HIGHWATER\_MARK 및
REPLICATION\_HBT\_DETECT\_TIME 프로퍼티 설정에 따라 일정 시간이 경과하면 이중화 대상 서버 간의 통신을 중단됩니다.

이 버그의 현상이 발생하면 altibase\_rp.log에 아래와 같은 로그가 남습니다.     

~~~bash
[2022/12/01 10:12:52 2E2D][PID:25068][Thread-47083656578816][LWP-18522]
[PJChild] [0] TABLE RLH_MCPTT_DATA SYNC START
[2022/12/01 10:12:55 2E2E][PID:25068][Thread-47068758411008][LWP-25103]
ERR-6102a(errno=22) Bind failure
 
[2022/12/01 10:12:55 2E2F][PID:25068][Thread-47068758411008][LWP-25103]
[HBT] Peer Server Connection Fails.
      [2001:4200:210:1000:731::16:20317] Ref=1 Mode=1 Fail Count=1
...
[2022/12/01 10:13:19 2E3F][PID:25068][Thread-47068758411008][LWP-25103]
[HBT] Peer Server Connection Fails.
      [2001:4200:210:1000:731::16:20317] Ref=1 Mode=1 Fail Count=9
[2022/12/01 10:13:19 2E40][PID:25068][Thread-47068758411008][LWP-25103]
[HBT] Host status info.
      [2001:4200:210:1000:731::16:20317] Ref=1 Mode=4 Last Error=22 mFault=Fault Detected
[2022/12/01 10:13:20 2E41][PID:25068][Thread-47083656578816][LWP-18522]
ERR-620eb(errno=11) Exit flag is set.
 
[2022/12/01 10:13:20 2E42][PID:25068][Thread-47083656578816][LWP-18522]
ERR-6101d(errno=11) [Sender] Failed to sync a table
 
[2022/12/01 10:13:20 2E43][PID:25068][Thread-47083656578816][LWP-18522]
ERR-6101d(errno=11) [Sender] Failed to sync a table
 
[2022/12/01 10:13:20 2E44][PID:25068][Thread-47083656578816][LWP-18522]
[PJChild] Error in run()
[2022/12/01 10:13:20 2E45][PID:25068][Thread-47081406347008][LWP-25662]
[SenderApply] Replication RP_K0D0 Got Error
[2022/12/01 10:13:20 2E46][PID:25068][Thread-47081406347008][LWP-25662]
ERR-6118d(errno=62) The HeartBeat thread(HBT) detects peer server or network error.
 
[2022/12/01 10:13:21 2E47][PID:25068][Thread-47078724155136][LWP-25633]
[PJMgr] child thread[0] failure in run()
[2022/12/01 10:13:21 2E48][PID:25068][Thread-47081003693824][LWP-25656]
[SenderSyncParallel] Error in syncParallel()
[2022/12/01 10:13:21 2E49][PID:25068][Thread-47081003693824][LWP-25656]
ERR-6118d(errno=62) The HeartBeat thread(HBT) detects peer server or network error.
 
[2022/12/01 10:13:21 2E4A][PID:25068][Thread-47081003693824][LWP-25656]
ERR-61152(errno=62) Replication synchronization failed. Check whether the index on the remote server is consistent.
 
[2022/12/01 10:13:21 2E4B][PID:25068][Thread-47081003693824][LWP-25656]
ERR-61011(errno=62) [Sender] Failed to start sync
~~~



#### 재현 방법

-   **재현 절차**

-   **수행 결과**

-   **예상 결과**

#### Workaround

`없음`

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    6.5.1.9.5     |          6.3.1          |    8.1.1     |        7.1.3        |            7.4.5             |

> Altibase 6.5.1 패치 버전 별 히스토리는 [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_6.5.1/Altibase_6_5_1_Version_Histories.md) 에서 확인할 수 있다.

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
