<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Altibase 7.1.0.4.8 Patch Notes](#altibase-71048-patch-notes)
  - [New Features](#new-features)
    - [BUG-46787  ACL(Access Control List)에 차단 설정된 IP 주소에서 접속 시도 시 altibase_boot.log에 기록되는 에러 메시지에 IP 주소를 추가합니다.](#bug-46787aclaccess-control-list%EC%97%90-%EC%B0%A8%EB%8B%A8-%EC%84%A4%EC%A0%95%EB%90%9C-ip-%EC%A3%BC%EC%86%8C%EC%97%90%EC%84%9C-%EC%A0%91%EC%86%8D-%EC%8B%9C%EB%8F%84-%EC%8B%9C-altibase_bootlog%EC%97%90-%EA%B8%B0%EB%A1%9D%EB%90%98%EB%8A%94-%EC%97%90%EB%9F%AC-%EB%A9%94%EC%8B%9C%EC%A7%80%EC%97%90-ip-%EC%A3%BC%EC%86%8C%EB%A5%BC-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-48208 트리거와 PSM에서 TIMESTAMP 관련 제약을 제거하여 TIMESTAMP 컬럼을 가진 테이블을 포함할 수 있게 변경합니다.](#bug-48208%ED%8A%B8%EB%A6%AC%EA%B1%B0%EC%99%80-psm%EC%97%90%EC%84%9C-timestamp-%EA%B4%80%EB%A0%A8-%EC%A0%9C%EC%95%BD%EC%9D%84-%EC%A0%9C%EA%B1%B0%ED%95%98%EC%97%AC-timestamp-%EC%BB%AC%EB%9F%BC%EC%9D%84-%EA%B0%80%EC%A7%84-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%9D%84-%ED%8F%AC%ED%95%A8%ED%95%A0-%EC%88%98-%EC%9E%88%EA%B2%8C-%EB%B3%80%EA%B2%BD%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-48230 DEQUEUE 병렬 수행 시 성능 저하 현상을 개선합니다.](#bug-48230dequeue-%EB%B3%91%EB%A0%AC-%EC%88%98%ED%96%89-%EC%8B%9C-%EC%84%B1%EB%8A%A5-%EC%A0%80%ED%95%98-%ED%98%84%EC%83%81%EC%9D%84-%EA%B0%9C%EC%84%A0%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-48292 oraAdapter 종료 시 oraAdapter.trc에 적용 완료한 마지막 SN을 기록하는 로그를 추가합니다.](#bug-48292oraadapter-%EC%A2%85%EB%A3%8C-%EC%8B%9C-oraadaptertrc%EC%97%90-%EC%A0%81%EC%9A%A9-%EC%99%84%EB%A3%8C%ED%95%9C-%EB%A7%88%EC%A7%80%EB%A7%89-sn%EC%9D%84-%EA%B8%B0%EB%A1%9D%ED%95%98%EB%8A%94-%EB%A1%9C%EA%B7%B8%EB%A5%BC-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-48234 Recursive WITH 문에 JOIN 절을 포함한 경우 WITH 문 수행이 느린 현상이 있습니다.](#bug-48234recursive-with-%EB%AC%B8%EC%97%90-join-%EC%A0%88%EC%9D%84-%ED%8F%AC%ED%95%A8%ED%95%9C-%EA%B2%BD%EC%9A%B0-with-%EB%AC%B8-%EC%88%98%ED%96%89%EC%9D%B4-%EB%8A%90%EB%A6%B0-%ED%98%84%EC%83%81%EC%9D%B4-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-48253 하나의 세션에서 Altibase 서버로부터 CLI 함수 응답을 받지 않은 상태에서 다른 CLI 함수를 수행할 경우 무한 대기(hang) 현상이 발생할 수 있습니다.](#bug-48253%ED%95%98%EB%82%98%EC%9D%98-%EC%84%B8%EC%85%98%EC%97%90%EC%84%9C-altibase-%EC%84%9C%EB%B2%84%EB%A1%9C%EB%B6%80%ED%84%B0-cli-%ED%95%A8%EC%88%98-%EC%9D%91%EB%8B%B5%EC%9D%84-%EB%B0%9B%EC%A7%80-%EC%95%8A%EC%9D%80-%EC%83%81%ED%83%9C%EC%97%90%EC%84%9C-%EB%8B%A4%EB%A5%B8-cli-%ED%95%A8%EC%88%98%EB%A5%BC-%EC%88%98%ED%96%89%ED%95%A0-%EA%B2%BD%EC%9A%B0-%EB%AC%B4%ED%95%9C-%EB%8C%80%EA%B8%B0hang-%ED%98%84%EC%83%81%EC%9D%B4-%EB%B0%9C%EC%83%9D%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-48273 PIVOT 절의 집계 함수 처리 과정에서 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-48273pivot-%EC%A0%88%EC%9D%98-%EC%A7%91%EA%B3%84-%ED%95%A8%EC%88%98-%EC%B2%98%EB%A6%AC-%EA%B3%BC%EC%A0%95%EC%97%90%EC%84%9C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-48275 EMERGENCY_STARTUP_POLICY 프로퍼티 비활성화 상태에서 Recovery 수행 중 ERR-1116e Could not perform emergency startup due to current LOG_BUFFER_TYPE setting. 에러가 발생하는 경우가 있습니다.](#bug-48275__emergency_startup_policy-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0-%EB%B9%84%ED%99%9C%EC%84%B1%ED%99%94-%EC%83%81%ED%83%9C%EC%97%90%EC%84%9C-recovery-%EC%88%98%ED%96%89-%EC%A4%91-err-1116e-could-not-perform-emergency-startup-due-to-current-log_buffer_type-setting-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%98%EB%8A%94-%EA%B2%BD%EC%9A%B0%EA%B0%80-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-48280 executeQuery 함수를 사용하여 DEQUEUE문 수행 시 NullPointerException 에러가 발생합니다.](#bug-48280executequery-%ED%95%A8%EC%88%98%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EC%97%AC-dequeue%EB%AC%B8-%EC%88%98%ED%96%89-%EC%8B%9C-nullpointerexception-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-48287 REPLICATION_SYNC_LOG 프로퍼티가 1 인 경우 오프라인 이중화를 수행하면 행(hang) 현상이 발생합니다.](#bug-48287replication_sync_log-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0%EA%B0%80-1-%EC%9D%B8-%EA%B2%BD%EC%9A%B0-%EC%98%A4%ED%94%84%EB%9D%BC%EC%9D%B8-%EC%9D%B4%EC%A4%91%ED%99%94%EB%A5%BC-%EC%88%98%ED%96%89%ED%95%98%EB%A9%B4-%ED%96%89hang-%ED%98%84%EC%83%81%EC%9D%B4-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-48299 하나의 SQL에서 사용한 컬럼 수가 32768개를 초과할 경우 ERR-3111D : There are too many DML statements in the stored procedure, or the SQL query is too long. 에러가 발생합니다.](#bug-48299%ED%95%98%EB%82%98%EC%9D%98-sql%EC%97%90%EC%84%9C-%EC%82%AC%EC%9A%A9%ED%95%9C-%EC%BB%AC%EB%9F%BC-%EC%88%98%EA%B0%80-32768%EA%B0%9C%EB%A5%BC-%EC%B4%88%EA%B3%BC%ED%95%A0-%EA%B2%BD%EC%9A%B0-err-3111d--there-are-too-many-dml-statements-in-the-stored-procedure-or-the-sql-query-is-too-long-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

  

Altibase 7.1.0.4.8 Patch Notes
==============================

New Features
------------

### BUG-46787 ACL(Access Control List)에 차단 설정된 IP 주소에서 접속 시도 시 altibase\_boot.log에 기록되는 에러 메시지에 IP 주소를 추가합니다.

-   **module** : mm

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **증상** : 차단 설정된 IP 주소에서 Altibase 서버로 접속 시도 시 altibase\_boot.log에 기록되는 에러 메시지가 변경되었습니다. 
    
    ACL 설정 뒤에 접속을 시도한 클라이언트 IP 주소가 추가되었습니다.
    
    \* 변경 전
    
    ERR-410e9(errno=0) Connection is not permitted by the ACCESS\_LIST:0.0.0.0
    
    Dispatcher callback failed
    
    \* 변경 후
    
    ERR-410e9(errno=0) Connection is not permitted by the ACCESS\_LIST:0.0.0.0 **( IP : *Client IP Address* )**
    
    Dispatcher callback failed    

- **재현 방법**

  -   **재현 절차**

          1) Altibase 서버 설정
             Altibase 서버 IP Address가 192.168.1.145 이고 서비스 포트가 20300 이라고 가정합니다.
             altibase.properties 설정 예
             ACCESS_LIST = DENY, 0.0.0.0, 0.0.0.0         # 127.0.0.1 외에 모든 접속을 차단
          2) 차단 설정된 IP 에서 접속 시도
             $ is -s 192.168.1.145 -port 20300

  - **수행 결과**

    ```bash
    ERR-410e9(errno=0) Connection is not permitted by the ACCESS_LIST: 0.0.0.0
    Dispatcher callback failed                                                                      
    ```

  -   **예상 결과**

      ```bash
      ERR-410e9(errno=0) Connection is not permitted by the ACCESS_LIST: 0.0.0.0 ( IP : Client IP Address )
      Dispatcher callback failed
      ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48208 트리거와 PSM에서 TIMESTAMP 관련 제약을 제거하여 TIMESTAMP 컬럼을 가진 테이블을 포함할 수 있게 변경합니다.

-   **module** : qp-psm-trigger-pvo

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **증상** : 트리거와 PSM 생성 시 TIMESTAMP 컬럼을 가진 테이블을 포함한 경우 ERR-31028 : Unable to create a column with the specified data type. 에러가 발생합니다. 이는 TIMESTAMP 관련 제약으로 발생하는 정상적인 에러이나 사용자 편의를 위해 제약 사항을 제거하여 트리거 및 PSM 생성이 가능하도록 변경합니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    DROP TRIGGER i3;
    DROP TABLE test_tri CASCADE;
    CREATE TABLE test_tri (c1 INTEGER, c2 TIMESTAMP);
    CREATE TRIGGER i3
    BEFORE INSERT ON test_tri
    REFERENCING NEW ROW NEW_ROW
    FOR EACH ROW
    AS BEGIN
    NEW_ROW.c2 := '2020100500' ;
    END;
    /
    ```

  - **수행 결과**

    ```sql
    [ERR-31028 : Unable to create a column with the specified data type.
    In trigger SYS.I3
    0003 : referencing new row NEW_ROW
                              ^      ^
    ]
    ```

  -   **예상 결과**

      ```SQL
      Create success.
      ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48230 DEQUEUE 병렬 수행 시 성능 저하 현상을 개선합니다.

-   **module** : sm

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **증상** : 8개 이상 클라이언트에서 DEQUEUE를 동시에 수행할 경우 성능이 하락하는 현상이 있습니다. 병렬로 DEQUEUE 수행 시 발생하는 병목을 제거하여 성능을 개선합니다.
    
    디스크 QUEUE 테이블 지원 중단합니다. 
    
    이 버그 반영 이후 CREATE QUEUE 구문에서 디스크 테이블스페이스 지정 시 ERR-311E5 : The table is not a memory or volatile table. 에러 발생합니다.
    
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

### BUG-48292 oraAdapter 종료 시 oraAdapter.trc에 적용 완료한 마지막 SN을 기록하는 로그를 추가합니다.

-   **module** : rp-oraAdapter

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **증상** : Altibase 서버 장애로 oraAdapter가 종료한 경우 마지막적용된 SN을 확인할 수 없습니다. 이 문제를 개선하기 위해 oraAdapter.trc에 적용 완료한 마지         막 SN을 기록하는 로그를 추가합니다.
    
    로그 형태 : Last SN : 0

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

### BUG-48234 Recursive WITH 문에 JOIN 절을 포함한 경우 WITH 문 수행이 느린 현상이 있습니다.

-   **module** : qp-dml-execute

-   **Category** : Efficiency

-   **재현 빈도** : Always

-   **증상** : Recursive WITH 문에 JOIN 절을 포함한 경우 JOIN 처리 비용 계산 문제로 WITH 문 수행 시간이 오래 소요되는 문제를 개선했습니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    DROP TABLE pm_eq_dtl;
    CREATE TABLE pm_eq_dtl 
    (
        company_cd      VARCHAR(28)     FIXED, 
        eqp_cd          VARCHAR(200)    VARIABLE, 
        vlid_to_dt      VARCHAR(32)     VARIABLE, 
        vlid_from_dt    VARCHAR(32)     VARIABLE, 
        eqp_tab_no_dc   VARCHAR(400)    VARIABLE, 
        plant_cd        VARCHAR(28)     FIXED, 
        plan_plant_cd   VARCHAR(28)     FIXED, 
        plangrp_cd      VARCHAR(28)     FIXED, 
        wc_cd           VARCHAR(28)     FIXED, 
        maint_wc_cd     VARCHAR(28)     FIXED, 
        wc_plant_cd     VARCHAR(28)     FIXED, 
        up_eqp_cd       VARCHAR(28)     FIXED 
    );
    ALTER TABLE pm_eq_dtl ADD PRIMARY KEY (company_cd, eqp_cd, vlid_to_dt);
    
    INSERT INTO pm_eq_dtl (company_cd, eqp_cd, vlid_to_dt, up_eqp_cd)
    SELECT '1000', LEVEL, '99991231', NULL FROM DUAL CONNECT BY LEVEL < 16317;
    
    INSERT INTO pm_eq_dtl (company_cd, eqp_cd, vlid_to_dt, up_eqp_cd)
    SELECT '1000', LEVEL*100000, '99991231', LEVEL FROM DUAL CONNECT BY LEVEL < 143358;
    
    WITH cte_lvl(company_cd, eqp_cd, lvl) 
    AS
    (SELECT company_cd, eqp_cd, 6 lvl
       FROM pm_eq_dtl
      WHERE company_cd = '1000'
        AND vlid_to_dt = '99991231'
        AND up_eqp_cd IS NULL
      UNION ALL
     SELECT a.company_cd, a.eqp_cd, b.lvl+1 lvl
       FROM pm_eq_dtl a INNER JOIN cte_lvl b ON b.company_cd = a.company_cd
        AND b.eqp_cd = a.up_eqp_cd
      WHERE a.company_cd = '1000'
        AND a.vlid_to_dt = '99991231'
        AND a.up_eqp_cd IS NOT NULL 
    ) 
    SELECT COUNT(*) FROM cte_lvl;
    ```

  -   **수행 결과**

          SQL 수행 시간이 길어 멈춘 것 같은 현상을 보입니다.

  -   **예상 결과**

      ```sql
      COUNT(*)             
      -----------------------
      32633
      ```

- **Workaround**

  ```sql
  WITH cte_lvl(company_cd, eqp_cd, lvl) 
  AS
  (SELECT company_cd, eqp_cd, 6 lvl
     FROM pm_eq_dtl
    WHERE company_cd = '1000'
      AND vlid_to_dt = '99991231'
      AND up_eqp_cd IS NULL
    UNION ALL
   SELECT /*+ USE_HASH(a, b) */ a.company_cd, a.eqp_cd, b.lvl+1 lvl
     FROM pm_eq_dtl a INNER JOIN cte_lvl b ON b.company_cd = a.company_cd
      AND b.eqp_cd = a.up_eqp_cd
    WHERE a.company_cd = '1000'
      AND a.vlid_to_dt = '99991231'
      AND a.up_eqp_cd IS NOT NULL 
  ) 
  SELECT COUNT(*) FROM cte_lvl;
  ```

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48253 하나의 세션에서 Altibase 서버로부터 CLI 함수 응답을 받지 않은 상태에서 다른 CLI 함수를 수행할 경우 무한 대기(hang) 현상이 발생할 수 있습니다.

-   **module** : mm-cli

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **증상** : CLI 처리 중 내부적으로 뮤텍스 락(mutex lock) 획득 후 해제 없이 다시 획득하려는 경우 CLI에서 Lock sequence error. 에러 메시지 출력 후 세션을 종료하도록 변경합니다. 애플리케이션 세션이 종료되므로 재연결하여 처리해야합니다.
    
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
        -   에러 메시지가 추가되었습니다.

            ```bash
에러 메시지가 추가되었습니다.
            
            0x51099 ( 331929) ulERR_ABORT_LOCK_SEQUENCE_ERR Lock sequence error. 
            # *Cause: invalid Lock call sequence.
            # *Action: Try disconnect and reconnect 
            ```
            
            

### BUG-48273 PIVOT 절의 집계 함수 처리 과정에서 Altibase 서버가 비정상 종료할 수 있습니다.

-   **module** : qp-select-execute

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **증상** : ORDER BY 절 또는 JOIN 절 오른쪽 대상에서 PIVOT을 사용한 경우 PIVOT 절의 집계 함수 처리 과정에서 Altibase 서버가 비정상 종료하는 문제를 수정했습니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    DROP TABLE t14;
    CREATE TABLE t14 (
    rslt_reprt_pk   NUMERIC(22),
    evl_score       VARCHAR(5),
    chklist_item_pk NUMERIC(22)
    ) TABLESPACE SYS_TBS_DISK_DATA;
    
    INSERT INTO t14 VALUES( 205, '1', 135);
    INSERT INTO t14 VALUES( 205, NULL, 1349);
    INSERT INTO t14 VALUES( 205, NULL, 1340);
    INSERT INTO t14 VALUES( 205, NULL, 1341);
    INSERT INTO t14 VALUES( 205, '1', 134);
    INSERT INTO t14 VALUES( 205, NULL, 1339);
    INSERT INTO t14 VALUES( 205, NULL, 1330);
    INSERT INTO t14 VALUES( 205, NULL, 1331);
    INSERT INTO t14 VALUES( 205, '1', 133);
    INSERT INTO t14 VALUES( 205, NULL, 1329);
    INSERT INTO t14 VALUES( 205, NULL, 1320);
    INSERT INTO t14 VALUES( 205, NULL, 1321);
    INSERT INTO t14 VALUES( 205, '1', 132);
    INSERT INTO t14 VALUES( 205, NULL, 1319);
    INSERT INTO t14 VALUES( 205, NULL, 1310);
    INSERT INTO t14 VALUES( 205, NULL, 1311);
    INSERT INTO t14 VALUES( 205, '1', 131);
    INSERT INTO t14 VALUES( 205, 'A', 13);
    INSERT INTO t14 VALUES( 205, NULL, 1269);
    INSERT INTO t14 VALUES( 205, NULL, 1260);
    
    DROP TABLE t24;
    CREATE TABLE t24 (
    rslt_reprt_pk       NUMERIC(22),
    chk_oprtn_pk        NUMERIC(22),
    last_trsct_sttus_cd VARCHAR(2)
    ) TABLESPACE SYS_TBS_DISK_DATA;
    
    INSERT INTO t24 VALUES(196, 612, '02');
    INSERT INTO t24 VALUES(203, 683, '02');
    INSERT INTO t24 VALUES(205, 717, '07');
    INSERT INTO t24 VALUES(224, 726, '03');
    INSERT INTO t24 VALUES(232, 751, '02');
    INSERT INTO t24 VALUES(243, 808, '02');
    INSERT INTO t24 VALUES(251, 811, '05');
    INSERT INTO t24 VALUES(314, 1002, '03');
    INSERT INTO t24 VALUES(345, 937, '02');
    INSERT INTO t24 VALUES(347, 933, '02');
    INSERT INTO t24 VALUES(353, 820, '02');
    INSERT INTO t24 VALUES(356, 819, '03');
    INSERT INTO t24 VALUES(357, 999, '02');
    INSERT INTO t24 VALUES(363, 998, '03');
    INSERT INTO t24 VALUES(365, 959, '02');
    INSERT INTO t24 VALUES(386, 951, '02');
    INSERT INTO t24 VALUES(388, 994, '02');
    INSERT INTO t24 VALUES(182, 596, '06');
    INSERT INTO t24 VALUES(208, 729, '08');
    INSERT INTO t24 VALUES(247, 815, '06');
    
    DROP TABLE t34;
    CREATE TABLE t34 (
    rslt_reprt_pk NUMERIC(22)
    ) TABLESPACE SYS_TBS_DISK_DATA;
    INSERT INTO t34 VALUES(196);
    INSERT INTO t34 VALUES(203);
    INSERT INTO t34 VALUES(205);
    INSERT INTO t34 VALUES(205);
    INSERT INTO t34 VALUES(205);
    INSERT INTO t34 VALUES(224);
    
    SELECT /*+ USE_HASH( t34, tt4 ) */ * 
      FROM t34, 
           (SELECT *
              FROM (SELECT a.rslt_reprt_pk,
                           a.chklist_item_pk,
                           a.evl_score,
                           b.chk_oprtn_pk
                      FROM t14 a ,
                           t24 b
                     WHERE a.rslt_reprt_pk = b.rslt_reprt_pk
                       AND b.last_trsct_sttus_cd = '07'
                   ) 
             PIVOT ( MAX(evl_score) FOR chklist_item_pk IN (
             11, 111, 112, 113, 114, 115, 12, 124, 121, 122, 123, 125, 126, 13, 134, 136, 135, 133, 132, 131,
             22, 221, 222, 223, 23, 233, 234, 231, 232, 21, 211, 212,      
             32, 321, 322, 31, 311, 41, 411, 414, 413, 412, 42, 424, 421, 423, 422, 43, 431,
             52, 521, 522, 523, 53, 533, 534, 532, 531, 51, 511, 512, 513))
           ) tt4
      WHERE t34.rslt_reprt_pk = tt4.rslt_reprt_pk
    ;
    ```

  -   **수행 결과**

          Altibase 서버가 비정상 종료합니다.

  -   **예상 결과**

      ```SQL
      RSLT_REPRT_PK RSLT_REPRT_PK CHK_OPRTN_PK 11          111         112         113         114         115         12          124         121         122         123         125         126         13          134         136         135         133         132         131         22          221         222         223         23          233         234         231         232         21          211         212         32          321         322         31          311         41          411         414         413         412         42          424         421         423         422         43          431         52          521         522         523         53          533         534         532         531         51          511         512         513         
      -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
      205         205         717                                                                                                                                                                     A           1                       1           1           1           1                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
      205         205         717                                                                                                                                                                     A           1                       1           1           1           1                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
      205         205         717                                                                                                                                                                     A           1                       1           1           1           1                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   
      3 rows selected.
      ```

- **Workaround**

  ```sql
  /*+ USE_HASH( t34, tt4 ) */ 힌트를 /*+ USE_HASH( tt4, t34  ) */ 로 변경하여 수행합니다.
  ```

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48275 \_\_EMERGENCY\_STARTUP\_POLICY 프로퍼티 비활성화 상태에서 Recovery 수행 중 ERR-1116e Could not perform emergency startup due to current LOG\_BUFFER\_TYPE setting. 에러가 발생하는 경우가 있습니다.

-   **module** : sm\_recovery

-   **Category** : Message Error

-   **재현 빈도** : Rare

-   **증상** : Recovery 수행 중 오류 상황과 관계없이 출력되는 에러 메시지를 제거하고 필요한 메시지를 추가합니다. 
    
    altibase\_error.log에 다음과 같이 기록됩니다.
    
    [2020/11/09 13:44:44F8][PID:17326][Thread-140124726007552][LWP-17451]
    
    DRDB WAL protocol violation : DB UpdateLSN=[0,10,1176611] \>RedoLSN=[0,8,0]   
    
    [2020/11/09 13:44:44FA][PID:17326][Thread-140124726007552][LWP-17451]
    
    Last Updated SpaceID: 2, PageID: 9, FileID: 0, FPageID: 9                    \<\<-- 추가된 메시지
    
    [2020/11/09 13:44:44FB][PID:17326][Thread-140124726007552][LWP-17451]
    
    Last Updated File : /system001.dbf                                                         \<\<-- 추가된 메시지

- **재현 방법**
  -   **재현 절차**
      
  -   **수행 결과**
      
  -   **예상 결과**

-   **Workaround**

- **변경사항**

-   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48280 executeQuery 함수를 사용하여 DEQUEUE문 수행 시 NullPointerException 에러가 발생합니다.

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : executeQuery 함수를 사용하여 DEQUEUE문 수행 시 NullPointerException 에러가 발생하는 문제를 개선했습니다.
    
- **재현 방법**

  - **재현 절차**

    ```java
    CREATE QUEUE q1 (c1 INTEGER, c2 VARCHAR(10));
    [THREAD1]
    Connection sConn = getConnection();
    Statement sStmt = sConn.createStatement();
    ResultSet sRs = sStmt.executeQuery("DEQUEUE c1, c2 FROM q1 WAIT 10");
    while( sRS.next() )
    {
        System.out.println( "  EmpName : " + sRS.getInt(1) + " " + sRS.getString(2) );
    }
    [THREAD2]
    ENQUEUE INTO q1(c1, c2) VALUES (1, 'AAA');
    ```

  - **수행 결과**

    ```java
    Exception in thread "main" java.lang.NullPointerException    
    at Altibase.jdbc.driver.datatype.RowHandle.initToStore(RowHandle.java:71)   
    at Altibase.jdbc.driver.AltibaseForwardOnlyResultSet.next(AltibaseForwardOnlyResultSet.java:264)    
    at DequeueTest.main(DequeueTest.java:59)
    ```

  -   **예상 결과**

      ```JAVA
      EmpName : 1 aaa
      ```

-   **Workaround**

        execute() 와 getResultSet() 을 사용해서 DEQUEUE 문을 수행합니다.

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48287 REPLICATION\_SYNC\_LOG 프로퍼티가 1 인 경우 오프라인 이중화를 수행하면 행(hang) 현상이 발생합니다.

-   **module** : rp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : 오프라인 이중화에서 REPLICATION\_SYNC\_LOG 프로퍼티 영향으로 행(hang) 현상이 발생하는 현상을 수정합니다. 오프라인 이중화의 경우 REPLICATION\_SYNC\_LOG 프로퍼티 영향을 받지 않도록 변경합니다.
    
-   **재현 방법**

    -   **재현 절차**

            REPLICATION_SYNC_LOG = 1
            Standby 서버에서 오프라인 이중화 수행

    -   **수행 결과**

            오프라인 이중화가 끝나지 않음

    -   **예상 결과**

            오프라인 이중화가 정상적으로 완료

-   **Workaround**

        REPLICATION_SYNC_LOG 를 0으로 설정한다.

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48299 하나의 SQL에서 사용한 컬럼 수가 32768개를 초과할 경우 ERR-3111D : There are too many DML statements in the stored procedure, or the SQL query is too long. 에러가 발생합니다.

-   **module** : qp-select-pvo

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : 하나의 SQL에서 사용 가능한 컬럼 수를 32768개에서 65535개로 변경합니다.
    
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

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    7.1.0.4.8     |          6.5.1          |    8.9.1     |        7.1.7        |            7.4.6             |

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

Replication 프로토콜 버전은 변경되지 않았다..

### 프로퍼티

추가/변경/삭제된 프로퍼티 없음

### 성능 뷰

추가/변경/삭제된 프로퍼티 없음
