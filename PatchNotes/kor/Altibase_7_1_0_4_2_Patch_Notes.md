<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Altibase 7.1.0.4.2 Patch Notes](#altibase-71042-patch-notes)
  - [New Features](#new-features)
    - [BUG-48014 ST\_Collect 함수지원](#bug-48014st%5C_collect-%ED%95%A8%EC%88%98%EC%A7%80%EC%9B%90)
    - [BUG-48023 Alitbase 7.1에서 쿼리 플랜변경으로 인해 떨어진 aexport 성능을 원복합니다.](#bug-48023alitbase-71%EC%97%90%EC%84%9C-%EC%BF%BC%EB%A6%AC-%ED%94%8C%EB%9E%9C%EB%B3%80%EA%B2%BD%EC%9C%BC%EB%A1%9C-%EC%9D%B8%ED%95%B4-%EB%96%A8%EC%96%B4%EC%A7%84-aexport-%EC%84%B1%EB%8A%A5%EC%9D%84-%EC%9B%90%EB%B3%B5%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-48047 heapmin이 제거된 AIX 패키지 제공](#bug-48047heapmin%EC%9D%B4-%EC%A0%9C%EA%B1%B0%EB%90%9C-aix-%ED%8C%A8%ED%82%A4%EC%A7%80-%EC%A0%9C%EA%B3%B5)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-46438 SORT_AREA_SIZE 가 너무 작아서 쿼리 수행이 실패한 경우에 잘못된 에러메시지가 출력됩니다.](#bug-46438sort_area_size-%EA%B0%80-%EB%84%88%EB%AC%B4-%EC%9E%91%EC%95%84%EC%84%9C-%EC%BF%BC%EB%A6%AC-%EC%88%98%ED%96%89%EC%9D%B4-%EC%8B%A4%ED%8C%A8%ED%95%9C-%EA%B2%BD%EC%9A%B0%EC%97%90-%EC%9E%98%EB%AA%BB%EB%90%9C-%EC%97%90%EB%9F%AC%EB%A9%94%EC%8B%9C%EC%A7%80%EA%B0%80-%EC%B6%9C%EB%A0%A5%EB%90%A9%EB%8B%88%EB%8B%A4)
    - [BUG-47761 이중화 대상 테이블에 SPLIT/MERGE/DROP PARTITION 수행 후 이중화 start시 실패합니다.](#bug-47761%EC%9D%B4%EC%A4%91%ED%99%94-%EB%8C%80%EC%83%81-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90-splitmergedrop-partition-%EC%88%98%ED%96%89-%ED%9B%84-%EC%9D%B4%EC%A4%91%ED%99%94-start%EC%8B%9C-%EC%8B%A4%ED%8C%A8%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-47967 subquery의 외부참조 컬럼이 2개이상 존재할 경우 결과값이 달라집니다.](#bug-47967subquery%EC%9D%98-%EC%99%B8%EB%B6%80%EC%B0%B8%EC%A1%B0-%EC%BB%AC%EB%9F%BC%EC%9D%B4-2%EA%B0%9C%EC%9D%B4%EC%83%81-%EC%A1%B4%EC%9E%AC%ED%95%A0-%EA%B2%BD%EC%9A%B0-%EA%B2%B0%EA%B3%BC%EA%B0%92%EC%9D%B4-%EB%8B%AC%EB%9D%BC%EC%A7%91%EB%8B%88%EB%8B%A4)
    - [BUG-48026 이중화 handshake 중에 네트워크 장애가 발생하면 이중화가 멈추는 문제가 발생할수 있습니다.](#bug-48026%EC%9D%B4%EC%A4%91%ED%99%94-handshake-%EC%A4%91%EC%97%90-%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC-%EC%9E%A5%EC%95%A0%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%98%EB%A9%B4-%EC%9D%B4%EC%A4%91%ED%99%94%EA%B0%80-%EB%A9%88%EC%B6%94%EB%8A%94-%EB%AC%B8%EC%A0%9C%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A0%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-48036 alter table modify column한 이후에 related object의 상태가 invalid로 변경되지 않습니다.](#bug-48036alter-table-modify-column%ED%95%9C-%EC%9D%B4%ED%9B%84%EC%97%90-related-object%EC%9D%98-%EC%83%81%ED%83%9C%EA%B0%80-invalid%EB%A1%9C-%EB%B3%80%EA%B2%BD%EB%90%98%EC%A7%80-%EC%95%8A%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-48045 with 구문에 view 최적화 처리시 결과 오류가 발생합니다.](#bug-48045with-%EA%B5%AC%EB%AC%B8%EC%97%90-view-%EC%B5%9C%EC%A0%81%ED%99%94-%EC%B2%98%EB%A6%AC%EC%8B%9C-%EA%B2%B0%EA%B3%BC-%EC%98%A4%EB%A5%98%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Altibase 7.1.0.4.2 Patch Notes
================================

New Features
------------

### BUG-48014 ST\_Collect 함수지원

-   **module** : st

-   **Category** : Enhancement

-   **재현 빈도** : Always

- **증상** : ST_Collect 함수가 추가되었습니다.

  ##### 구문

  ```
  ST_COLLECT( GEOMETRY1, GEOMETRY2 );
  ```

  ##### 설명

  Geometry 객체들을 입력 받아 GeometryCollection 객체를 생성합니다. 이 때 input type이 동일하면 결과값은 Multi*가 되고, 동일하지 않으면 GeometryCollection이 됩니다.

  **반환 타입**

  GEOMETRY

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

### BUG-48023 Alitbase 7.1에서 쿼리 플랜변경으로 인해 떨어진 aexport 성능을 원복합니다.

-   **module** : ux-aexport

-   **Category** : Efficiency

-   **재현 빈도** : Always

-   **증상** : Altibase 7.1에서 쿼리 플랜변경으로 인해 떨어진 aexport 성능을 쿼리 튜닝을 통해 원복했습니다.
    
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

### BUG-48047 heapmin이 제거된 AIX 패키지 제공

-   **module** : id

-   **Category** : Maintainability

-   **재현 빈도** : Unknown

-   **증상** : 7.1.0.4.2 부터 heapmin이 제거된 AIX 패키지를 제공합니다.

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

### BUG-46438 SORT_AREA_SIZE 가 너무 작아서 쿼리 수행이 실패한 경우에 잘못된 에러메시지가 출력됩니다.

-   **module** : sm-disk-resource

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : SORT_AREA_SIZE 가 너무 작아서 쿼리 수행이 실패한 경우에 잘못된 에러메시지가 출력되는 문제가 있습니다.
    

내부적으로 에러를 잘못 판단하여 발생한 문제로, altibase_error.log 에 콜스택도 기록되는 문제도 있습니다.
    
    SORT_AREA_SIZE가 너무 작아서 쿼리 수행에 실패한 경우는 [ERR-11185 : Insufficient sort area space] 에러메시지가 출력되도록 수정하였습니다.

- **재현 방법**

  - **재현 절차**

        drop table T1;
         
        CREATE TABLE T1 ( I1 CHAR(8670) ) TABLESPACE SYS_TBS_DISK_DATA;
        INSERT /*+APPEND*/ INTO T1 SELECT RPAD(ROWNUM, 4096,  ROWNUM) FROM DUAL CONNECT BY LEVEL <= 30;
         
        ALTER SYSTEM SET SORT_AREA_SIZE = 524288;
        ALTER SYSTEM SET TEMP_SORT_GROUP_RATIO=5;
         
        SELECT SUBSTR(I1, 0, 2 )
           ,RANK() OVER (ORDER BY I1) RANK
           ,ROW_NUMBER() OVER (ORDER BY I1) NUM
           ,SUBSTR(LEAD( I1 ) OVER (ORDER BY I1),0,2 ) LEAD
           ,SUBSTR( LAG( I1 ) OVER (ORDER BY I1),0,2 ) LAG
        FROM T1
        ORDER BY I1 ;

  -   **수행 결과**

          [ERR-11069 : Internal server error in the storage manager ([FAILURE] ERR-0109E(error=11) Internal server error.)]

  -   **예상 결과**

          [ERR-11185 : Insufficient sort area space]

-   **Workaround**

        SORT_AREA_SIZE를 늘려주세요,

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47761 이중화 대상 테이블에 SPLIT/MERGE/DROP PARTITION 수행 후 이중화 start시 실패합니다.

-   **module** : rp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : 이중화 대상 테이블에 SPLIT/MERGE/DROP PARTITION 이후
    이중화 start시 실패하는 문제를 수정합니다. 이로 인해 기존과
    동작방식이 일부 변경되었으므로(추가된 스텝이 존재하므로) [Replicaton 매뉴얼#이중화대상테이블에DDL실행 예제]([https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Replication.md#%EC%98%88%EC%A0%9C-4](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Replication.md#예제-4))의 내용을 먼저 확인하시기 바랍니다.
    

이중화 대상인 테이블에 SPLIT PARTITION과 MERGE PARTITION, DROP
    PARTITION을 수행하려면, 원격서버에 REPLICATION\_DIFF\_META\_START\_ENABLE 프로퍼티를
    1로 설정해야 합니다. 이후 대상 테이블을 LOCK TABLE ...IN EXCLUSIVE
    MODE UNTIL NEXT DDL 구문으로 잠금 설정해야 합니다. 자세한 설명은
    매뉴얼 예제를 참고하시기 바랍니다.
    
-   **재현 방법**

    -   **재현 절차**

            Active  :
            ALTER SYSTEM SET REPLICATION_DDL_ENABLE = 1;
            ALTER SYSTEM SET REPLICATION_DDL_ENABLE_LEVEL = 1;
            LOCK TABLE T1 UNTIL NEXT DDL;
            ALTER REPLICATION REP1 FLUSH ALL;
            ALTER REPLICATION REP1 STOP;
            ALTER TABLE T1 SPLIT PARTITION P2 
                   INTO (PARTITION P3, PARTITION P4 ); 
            Standby : 
            ALTER SYSTEM SET REPLICATION_DDL_ENABLE = 1;
            ALTER SYSTEM SET REPLICATION_DDL_ENABLE_LEVEL = 1;
            LOCK TABLE T1 UNTIL NEXT DDL;
            ALTER REPLICATION REP1 FLUSH ALL;
            ALTER REPLICATION REP1 STOP;
            ALTER TABLE T1 SPLIT PARTITION P2 
                   INTO (PARTITION P3, PARTITION P4 );
            Active  :
            ALTER REPLICATION REP1 START;

    -   **수행 결과**

            [Sender] Failed to handshake with the peer server (The replication's item count does not match [3:4].)]

    -   **예상 결과**

            Success

-   **Workaround**

        DDL SYNC 기능을 이용하여 DDL 수행ORSQL_APPLY option을 끼고 이중화 START

-   **변경사항**

    - Performance view
    
    - Property
    
      - 추가
    
        - [REPLICATION_META_ITEM_COUNT_DIFF_ENABLE](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_2.md#replication_meta_item_count_diff_enable)
    
          - 데이터타입: Unsigned Integer
    
          - 기본값 : 0
    
          - 속성 : 변경가능, 단일값
    
          - 값의 범위 : 0,1
    
          - 설명: Lazy 모드로 이중화 수행 과정에서 SPLIT PARTITION과 MERGE PARTITION, DROP PARTITION을 수행하여 Active 서버와 Standby 서버의 이중화 테이블 파티션 메타 아이템 개수가 다른 경우에 이중화를 START 할 수 있는 프로퍼티이다. 이 값을 1로 설정하면 이중화 테이블 파티션 메타 아이템 개수가 다른 경우에도 이중화를 START 할 수 있다.
    
            Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.
    
    - Compile Option
    
    -   Error Code

### BUG-47967 subquery의 외부참조 컬럼이 2개이상 존재할 경우 결과값이 달라집니다.

-   **module** : qp-select

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : subquery의 외부참조 컬럼이 2개이상 존재할 경우 결과값이 달라지는 문제를 수정합니다.
    
- **재현 방법**

  -   **재현 절차**

          drop table t1;
          drop table sq;
          create table t1 ( i1 varchar(10), i2 varchar(10));
          create table sq ( i1 varchar(10), i2 varchar(10), i3 varchar(10));
          insert into t1 values('THREENINE', 'R001');
          insert into t1 values('THREENINE', 'RM01');
          insert into t1 values('THREENINE', 'R001');
          insert into sq values('THREENINE', 'R001', 'L001');
          insert into sq values('THREENINE', 'RM01', 'STAGE');
          set colsize 10
          select i2, ( select i2 from sq where i1 = t1.i1 and i2 = t1.i2 limit 1 ) as sq_i2 from t1 group by i1, i2;

  - **수행 결과**

        I2          SQ_I2
        ---------------------------
        R001        R001
        RM01        R001
        2 rows selected.

  -   **예상 결과**

          I2          SQ_I2
          ---------------------------
          R001        R001
          RM01        RM01
          2 rows selected.

-   **Workaround**

         alter system set __FORCE_SUBQUERY_CACHE_DISABLE=1;

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48026 이중화 handshake 중에 네트워크 장애가 발생하면 이중화가 멈추는 문제가 발생할수 있습니다.

-   **module** : dm

-   **Category** : Functional Error

-   **재현 빈도** : Rare

-   **증상** : 이중화 handshake 중에 네트워크 장애가 발생하면 HBT에 아직
    등록 되기전이므로 Sender는 네트워크 장애가 발생한지 모르고 계속 대기
    하는 문제가 있었습니다.

    HBT등록을 handshake 이전으로 하고 sender에서 ack를 대기할때 HBT
    에러를 체크하도록 수정하였습니다.

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

### BUG-48036 alter table modify column한 이후에 related object의 상태가 invalid로 변경되지 않습니다.

-   **module** : qp-ddl-dcl-execute

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : alter table modify column한 이후에 related  object의
    상태가 invalid로 변경되지 않는 문제를 수정하였습니다.

- **재현 방법**

  - **재현 절차**

        drop table emp;
        
        CREATE TABLE emp(
        eno INTEGER,
        ename CHAR(10),
        emp_job CHAR(15),
        join_date DATE,
        salary NUMBER(10,2),
        dno BYTE(2));
        
        CREATE OR REPLACE PROCEDURE proc1(p1 INTEGER)
        AS
        BEGIN
        DECLARE
        emp_rec emp%ROWTYPE;
        BEGIN
        SELECT * INTO emp_rec
        FROM emp
        WHERE eno = p1;
         END;
         END;
         /
        
        INSERT INTO emp VALUES (10, 'DKLEE', 'ENGINEER', '01-Jul-2000', 30000000, BYTE'D001');
        INSERT INTO emp VALUES (20, 'SWMYUNG', 'MANAGER', '01-Nov-1999', 50000000, BYTE'C002');
        
        exec proc1(10);
        set vertical on;
        
        select PROC_NAME, STATUS, to_char(CREATED,'yyyymmdd hh:mi:ss') as crt, to_char(LAST_DDL_TIME,'yyyymmdd hh:mi:ss') as last
        from system_.sys_procedures_ where proc_name like 'PROC1';
        
        alter table emp modify (ename char(20));
        
        select PROC_NAME, STATUS, to_char(CREATED,'yyyymmdd hh:mi:ss') as crt, to_char(LAST_DDL_TIME,'yyyymmdd hh:mi:ss') as last
        from system_.sys_procedures_ where proc_name like 'PROC1';
        
        alter procedure proc1 compile;
        
        select PROC_NAME, STATUS, to_char(CREATED,'yyyymmdd hh:mi:ss') as crt, to_char(LAST_DDL_TIME,'yyyymmdd hh:mi:ss') as last
        from system_.sys_procedures_ where proc_name like 'PROC1';

  -   **수행 결과**

          --BEFORE alter table modify column 
          iSQL> select PROC_NAME, STATUS, to_char(CREATED,'yyyymmdd hh:mi:ss') as crt, to_char(LAST_DDL_TIME,'yyyymmdd hh:mi:ss') as last
          from system_.sys_procedures_ where proc_name like 'PROC1';
          PROC_NAME : PROC1
          STATUS    : 0
          CRT       : 20200729 15:46:48
          LAST      : 20200729 15:46:48
          -- AFTER alter table modify column
          PROC_NAME : PROC1
          STATUS    : 0
          CRT       : 20200729 15:46:48
          LAST      : 20200729 15:46:48
          -- AFTER  alter procedure proc1 compile
          PROC_NAME : PROC1
          STATUS    : 0
          CRT       : 20200729 15:46:48
          LAST      : 20200729 15:46:48
          1 row selected.

  -   **예상 결과**

          --BEFORE alter table modify column 
          iSQL> select PROC_NAME, STATUS, to_char(CREATED,'yyyymmdd hh:mi:ss') as crt, to_char(LAST_DDL_TIME,'yyyymmdd hh:mi:ss') as last
          from system_.sys_procedures_ where proc_name like 'PROC1';
          PROC_NAME : PROC1
          STATUS    : 0
          CRT       : 20200729 15:46:48
          LAST      : 20200729 15:46:48
          -- AFTER alter table modify column
          PROC_NAME : PROC1
          STATUS    : 1
          CRT       : 20200729 15:46:48
          LAST      : 20200729 15:47:08
          -- AFTER  alter procedure proc1 compile
          PROC_NAME : PROC1
          STATUS    : 0
          CRT       : 20200729 15:46:48
          LAST      : 20200729 15:47:41
          1 row selected.

-   **Workaround**

        procedure 새로 생성

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48045 with 구문에 view 최적화 처리시 결과 오류가 발생합니다.

-   **module** : qp-dml-pvo

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : with 구문에 view 최적화 처리시 결과 오류문제를 수정합니다.

- **재현 방법**

  -   **재현 절차**

          drop table t1;
          create table t1 ( STOCK_TP varchar(20) );
          insert into t1 select 1 from dual connect by level < 10;
          WITH DOCU_AMT1 AS
                  (
                      SELECT
                          STOCK_TP, '1' DRCR_CD
                      FROM
                           t1
                      GROUP BY
                          STOCK_TP
                  )
                  ,T_ACTG_NO AS
                  (
                      SELECT
                          STOCK_TP,
                          ROW_NUMBER() OVER ( ORDER BY STOCK_TP ) ACTG_NO
                      FROM
                          DOCU_AMT1
                      GROUP BY
                          STOCK_TP
                  )
                  ,DOCU_AMT2 AS
                  (
                      SELECT DRCR_CD,
                          T_ACTG_NO.ACTG_NO TEMP_ACTG_NO
                      FROM
                          DOCU_AMT1 , T_ACTG_NO
                   )
                  ,DOCU_AMT3 AS
                  (
                      SELECT
                          DRCR_CD,
                          (SELECT 1 + TEMP_ACTG_NO FROM dual) ACTG_NO,
                                  'CA_IHCH_' || '201712' || '_' || LPAD( TO_CHAR( (SELECT 1 + DOCU_AMT2.TEMP_ACTG_NO FROM dual) ), 5, '0') DOCU_NO
                      FROM
                          DOCU_AMT2
                  )
                  ,DOCU_AMT4 AS
                  (
                      SELECT
                         ACTG_NO,
                         DOCU_NO,
                         (ROW_NUMBER() OVER (PARTITION BY DOCU_NO ORDER BY DRCR_CD DESC)) DOLINE_NO
                      FROM DOCU_AMT3
                  )
          SELECT DOCU_AMT4.ACTG_NO FROM DOCU_AMT4;
      
  - **수행 결과**

        ACTG_NO
        -----------------------
        
        1 row selected.

  -   **예상 결과**

          ACTG_NO
          -----------------------
          2
          1 row selected.

-   **Workaround**

        alter system set __OPTIMIZER_VIEW_TARGET_ENABLE = 0;

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
| 7.1.0.4.2        | 6.5.1                   | 8.8.1        | 7.1.7               | 7.4.6                        | 2.2.1            |

> Altibase 7.1 패치 버전별 히스토리는 [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7_1_Version_Histories.md)에서 확인할 수 있다.

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

Replication 프로토콜 버전은 변경되지 않았다..

#### Sharding Version

샤딩 버전은 변경 되지 않았다.

> 알티베이스 샤딩 프로토콜 및 메타는 상위, 하위 호환성을 보장하지
> 않는다. 즉, 샤딩 버전이 다른 경우, 재구성해야 한다.

### 프로퍼티

#### 추가된 프로퍼티

* [REPLICATION_META_ITEM_COUNT_DIFF_ENABLE](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_2.md#replication_meta_item_count_diff_enable)

### 성능 뷰

추가/변경/삭제된 성능뷰 없음