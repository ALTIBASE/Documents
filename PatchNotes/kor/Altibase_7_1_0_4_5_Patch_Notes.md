<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Altibase 7.1.0.4.5 Patch Notes](#altibase-71045-patch-notes)
  - [New Features](#new-features)
    - [BUG-48134 altiComp에서 동일한 레코드(MOSO EQ)에 대해서도 로그 파일에 기록하는 기능이 필요합니다.](#bug-48134alticomp%EC%97%90%EC%84%9C-%EB%8F%99%EC%9D%BC%ED%95%9C-%EB%A0%88%EC%BD%94%EB%93%9Cmoso-eq%EC%97%90-%EB%8C%80%ED%95%B4%EC%84%9C%EB%8F%84-%EB%A1%9C%EA%B7%B8-%ED%8C%8C%EC%9D%BC%EC%97%90-%EA%B8%B0%EB%A1%9D%ED%95%98%EB%8A%94-%EA%B8%B0%EB%8A%A5%EC%9D%B4-%ED%95%84%EC%9A%94%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-48136 Altibase 7.1 Windows클라이언트 지원](#bug-48136altibase-71-windows%ED%81%B4%EB%9D%BC%EC%9D%B4%EC%96%B8%ED%8A%B8-%EC%A7%80%EC%9B%90)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-48120 index NDV와 Predicate NDV 의 차이로 비효율적인 인덱스가 선택될 수 있습니다.](#bug-48120index-ndv%EC%99%80-predicate-ndv-%EC%9D%98-%EC%B0%A8%EC%9D%B4%EB%A1%9C-%EB%B9%84%ED%9A%A8%EC%9C%A8%EC%A0%81%EC%9D%B8-%EC%9D%B8%EB%8D%B1%EC%8A%A4%EA%B0%80-%EC%84%A0%ED%83%9D%EB%90%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-48128 scalar subquery+ aggregation function + group\_sort일때 결과 오류가 발생합니다.](#bug-48128scalar-subquery-aggregation-function--group%5C_sort%EC%9D%BC%EB%95%8C-%EA%B2%B0%EA%B3%BC-%EC%98%A4%EB%A5%98%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-48135 Index NL Join Penalty 값을 조절할 수 있는 프로퍼티 추가](#bug-48135index-nl-join-penalty-%EA%B0%92%EC%9D%84-%EC%A1%B0%EC%A0%88%ED%95%A0-%EC%88%98-%EC%9E%88%EB%8A%94-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0-%EC%B6%94%EA%B0%80)
    - [BUG-48160 fixed table 출력시 lock table 잡힌 table을 lock 대기하지 않고 제외하고 출력하는 방법 추가](#bug-48160fixed-table-%EC%B6%9C%EB%A0%A5%EC%8B%9C-lock-table-%EC%9E%A1%ED%9E%8C-table%EC%9D%84-lock-%EB%8C%80%EA%B8%B0%ED%95%98%EC%A7%80-%EC%95%8A%EA%B3%A0-%EC%A0%9C%EC%99%B8%ED%95%98%EA%B3%A0-%EC%B6%9C%EB%A0%A5%ED%95%98%EB%8A%94-%EB%B0%A9%EB%B2%95-%EC%B6%94%EA%B0%80)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Altibase 7.1.0.4.5 Patch Notes
==============================

New Features
------------

### BUG-48134 altiComp에서 동일한 레코드(MOSO EQ)에 대해서도 로그 파일에 기록하는 기능이 필요합니다.

-   **module** : ux-audit(altiComp)

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **증상** : altiComp에서 동일한 레코드(MOSO EQ)에 대해서도 로그 파일에 기록하는 기능을 추가했습니다.
    
-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
        -   altComp.cfg 파일에 프로퍼티 추가되었습니다.

            [LOG_EQ_MOSO](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Utilities.md#log_eq_moso)

            PK를 포함한 모든 컬럼의 값이 일치하는 MOSO 레코드 정보를
실행 결과 파일에  기록할 지 결정하는 프로퍼티이다. 
            

프로퍼티 값은 “ON”, “OFF”를 가질 수 있으며, “ON”이면
            기록하고, “OFF”이면 기록 하지 않는다. 프로퍼티를 지정하지 않으면 "OFF"로 동작한다.
            
            기록 형식은 MOSO[m,n]-\>EQ:PK-\>{PCOL\_V} 이다.

-   m : Master Server의 레코드 순서
             -   n : Slave Server의 레코드 순서

            이 옵션은 대용량 테이블을 비교할 때, 부하를 많이 줄 수
            있으므로 주의해서 사용해야 한다.
    
    -   Compile Option
-   Error Code

### BUG-48136 Altibase 7.1 Windows클라이언트 지원

-   **module** : ul-odbc

-   **Category** : Other

-   **재현 빈도** : Always

-   **증상** : 7.1.0.4.5부터 Windows 클라이언트를 지원합니다.

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

### BUG-48120 index NDV와 Predicate NDV 의 차이로 비효율적인 인덱스가 선택될 수 있습니다.

-   **module** : qp-select-pvo

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **증상** : index NDV와 Predicate NDV 의 차이로 비효율적인 인덱스가 선택될 수 있어, __OPTIMIER\_SCAN\_COST\_MODE 프로퍼티가 추가되었습니다. 이 프로퍼티 값을 1로 설정하여 해결할 수 있습니다. 
    
- **재현 방법**

  -   **재현 절차**

          CREATE TABLE T1 ( i1 VARCHAR(4), i2 VARCHAR(4), i3 CHAR(8) )
          tablespace sys_tbs_disk_data;
          CREATE INDEX IX1 ON T1 ( i1, i2 );
          CREATE INDEX IX2 ON T1( i1, i3, i2 );
          INSERT INTO T1 
          SELECT MOD(LEVEL,10), MOD(LEVEL,100), '201912'||TRIM(TO_CHAR((MOD(LEVEL,30)+1),'09')) 
          FROM DUAL CONNECT BY LEVEL <= 150;
          EXEC GATHER_TABLE_STATS(USER_NAME(),'T1',NULL,1);
          alter session set explain plan = only;
          prepare SELECT * FROM T1 WHERE i2 = ? AND i1 = ? ;

  - **수행 결과**

        I1    I2    I3
        --------------------------
        No rows selected.
        ------------------------------------------------------------
        PROJECT ( COLUMN_COUNT: 3, TUPLE_SIZE: 22, COST: 1.10 )
         SCAN ( TABLE: SYS.T1, INDEX: SYS.IX2, RANGE SCAN, ACCESS: ??, COST: 1.10 )
          [ VARIABLE KEY ]
          OR
           AND
            I1 = ?
          [ VARIABLE KEY FILTER ]
          OR
           AND
            I2 = ?
        ------------------------------------------------------------

  -   **예상 결과**

          I1    I2    I3
          --------------------------
          No rows selected.
          ------------------------------------------------------------
          PROJECT ( COLUMN_COUNT: 3, TUPLE_SIZE: 22, COST: 3.00 )
           SCAN ( TABLE: SYS.T1, INDEX: SYS.IX1, RANGE SCAN, ACCESS: ??, COST: 3.00 )
            [ VARIABLE KEY ]
            OR
             AND
              I1 = ?
              I2 = ?
          ------------------------------------------------------------

-   **Workaround**

         index( T1 IX1) hint

-   **변경사항**

    -   Performance view
    -   Property
        -   추가
-   __OPTIMIER\_SCAN\_COST\_MODE
            -   설명 : scan cost 결정할 때 사용 모드
        -   0: 기존 동작과 동일
                -   1: BUG-48120 적용
    -   기본값 : 0
            -   속성: 변경가능, 단일값
    -   값의 범위: [0,1]
    
-   Compile Option
    
    -   Error Code

### BUG-48128 scalar subquery+ aggregation function + group\_sort일때 결과 오류가 발생합니다.

-   **module** : qp-select-pvo

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : target절 having절에 subquery를 사용하고

    subquery의 상위 쿼리에 aggregation 함수와  group by 절을 사용한 경우
    결과값이 달라지는 문제를 해결했습니다.

- **재현 방법**

  -   **재현 절차**

          drop table t1;
          drop table t2;
          create table t1 (i1 int, i2 int, i3 int, i4 int);
          create table t2 ( i1 int);
          insert into t1 values( 1,1,1,3);
          insert into t1 values( 2,2,2,4);
          insert into t2 values(1);
          
          select /*+ group_sort*/ max(i4), (select count(*) from t2 where i1 = t1.i1) as sub from t1 group by i1;

  - **수행 결과**

        MAX(I4)     SUB
        ------------------------------------
        3           1
        4           1

  -   **예상 결과**

          MAX(I4)     SUB
          ------------------------------------
          3           1
          4           0
          2 rows selected.

-   **Workaround**

        select /*+ group_hash*/ max(i4), (select count(*) from t2 where i1 = t1.i1) as sub from t1 group by i1;

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48135 Index NL Join Penalty 값을 조절할 수 있는 프로퍼티 추가

-   **module** : qp-select-pvo

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **증상** :  Index nested loop의 access cost에 대한 조정값이 오류가 있어 비효율적인 실행계획이 수립되는 문제가 있습니다. 이를 해결하기 위해 Index NL Join Penalty 값을 조절할 수 있는 프로퍼티를 추가하였습니다.

-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
        -   추가
            -   __OPTIMIZER_INDEX_NL_JOIN_PENALTY
                -   설명 : Index Nl JOIN의 Cost 계산에서 사용되는 Penalty
                -   기본값: 6
                -   최소값, 최대값: 0, 26
                -   속성: 변경가능, 단일값
    -   Compile Option
    -   Error Code

### BUG-48160 fixed table 출력시 lock table 잡힌 table을 lock 대기하지 않고 제외하고 출력하는 방법 추가

-   **module** : sm\_interface

-   **Category** : Hang

-   **재현 빈도** : Always

-   **증상** :

- **재현 방법**

  -   **재현 절차**

          alter system set fetch_timeout = 0;
          create table T0 ( idx integer );
          create table T1 ( idx integer );
          --# process 1
          autocommit off;
          lock table T0 in EXCLUSIVE MODE;
          --# process 2
          select * from x$table_info where table_oid = (select table_oid from system_.sys_tables_ where table_name = 'T1');

  -   **수행 결과**

          [ERR-01043 : The session has been closed by the server]

  -   **예상 결과**

          select * from x$table_info where table_oid = (select table_oid from system_.sys_tables_ where table_name = 'T1');
          TABLESPACE_ID TABLE_TYPE  TABLE_OID            MEM_PAGE_CNT
          -------------------------------------------------------------------------
          MEM_VAR_PAGE_CNT     MEM_SLOT_CNT MEM_SLOT_SIZE        FIXED_USED_MEM
          ---------------------------------------------------------------------------------
          VAR_USED_MEM         MEM_FIRST_PAGEID     DISK_TOTAL_PAGE_CNT
          -------------------------------------------------------------------
          DISK_PAGE_CNT        SEG_PID     META_PAGE   FST_EXTRID
          -----------------------------------------------------------------------
          LST_EXTRID           PCTFREE     PCTUSED     INIT_TRANS  MAX_TRANS
          ---------------------------------------------------------------------------
          INITEXTENTS NEXTEXTENTS MINEXTENTS  MAXEXTENTS  OLD_VERSION_COUNT
          ---------------------------------------------------------------------------
          STATEMENT_REBUILD_COUNT UNIQUE_VIOLATION_COUNT UPDATE_RETRY_COUNT
          ------------------------------------------------------------------------
          DELETE_RETRY_COUNT   COMPRESSED_LOGGING IS_CONSISTENT
          ----------------------------------------------------------
          1           8192        4084576              1
          0                    818         40                   0
          0                    2                    0
          0                    0           0           0
          0                    0           0           0           0
          0           0           0           0           0
          0                    0                    0
          0                    1           1
          1 row selected.

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
| 7.1.0.4.5        | 6.5.1                   | 8.9.1        | 7.1.7               | 7.4.6                        | 2.2.1            |

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
> [메타다운그레이드](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Installation.md#%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9Cmeta-downgrade)를 참고한다.

#### CM protocol Version

통신 프로토콜 버전은 변경되지 않았다.

#### Replication protocol Version

Replication 프로토콜 버전은 변경되지 않았다.

#### Sharding Version

샤딩 버전은 변경 되지 않았다.

> 알티베이스 샤딩 프로토콜 및 메타는 상위, 하위 호환성을 보장하지
> 않는다. 즉, 샤딩 버전이 다른 경우, 재구성해야 한다.

### 프로퍼티

#### 추가된 프로퍼티

* __OPTIMIER\_SCAN\_COST\_MODE

* __OPTIMIZER_INDEX_NL_JOIN_PENALTY

### 성능 뷰

추가/변경/삭제된 성능 뷰 없음