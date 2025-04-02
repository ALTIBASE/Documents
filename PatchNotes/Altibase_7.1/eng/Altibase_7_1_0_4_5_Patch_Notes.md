Altibase 7.1.0.4.5 Patch Notes
==============================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [New Features](#new-features)
  - [BUG-48134 Added the functionality to log records with the same value (MOSO EQ) in altiComp.](#bug-48134%C2%A0added-the-functionality-to-log-records-with-the-same-value-moso-eq-in-alticomp)
  - [BUG-48136 Support for Altibase 7.1 on Windows clients](#bug-48136%C2%A0support-for-altibase-71-on-windows-clients)
- [Fixed Bugs](#fixed-bugs)
  - [BUG-48120 Added the __OPTIMIZER_SCAN_COST_MODE property to resolve the issue of inefficient index selection due to the difference between index NDV and predicate NDV.](#bug-48120-added-the-__optimizer_scan_cost_mode-property-to-resolve-the-issue-of-inefficient-index-selection-due-to-the-difference-between-index-ndv-and-predicate-ndv)
  - [BUG-48128 Fixed an issue where the result values differed when a subquery was used in the target clause's HAVING clause, and the subquery's parent query included an aggregation function and GROUP BY clause.](#bug-48128%C2%A0fixed-an-issue-where-the-result-values-differed-when-a-subquery-was-used-in-the-target-clauses-having-clause-and-the-subquerys-parent-query-included-an-aggregation-function-and-group-by-clause)
  - [BUG-48135 Added a property to adjust the Index NL Join Penalty value.](#bug-48135%C2%A0added-a-property-to-adjust-the-index-nl-join-penalty-value)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [Compatibility](#compatibility)
  - [Altibase Server Properties](#altibase-server-properties)
  - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
------------

### BUG-48134 Added the functionality to log records with the same value (MOSO EQ) in altiComp.

-   **module** : ux-audit(altiComp)

-   **Category** : Enhancement

-   **Reproducibility** : Always

-   **Description** : Added the functionality to log records with the same value (MOSO EQ) in altiComp.
    
-   **How to reproduce this bug**

    -   **Reproduction conditions**

    -   **Actual Results**

    -   **Expected Results**

-   **Workaround**

- **Changes**

  - Performance view

  - Property
    - altComp.cfg 파일에 프로퍼티 추가되었습니다.

      [LOG_EQ_MOSO](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Utilities.md#log_eq_moso)

      PK를 포함한 모든 컬럼의 값이 일치하는 MOSO 레코드 정보를
      실행 결과 파일에  기록할 지 결정하는 프로퍼티이다. 

      프로퍼티 값은 “ON”, “OFF”를 가질 수 있으며, “ON”이면 기록하고, “OFF”이면 기록 하지 않는다. 프로퍼티를 지정하지 않으면 "OFF"로 동작한다. 기록 형식은 MOSO[m,n]->EQ:PK->{PCOL_V} 이다.

      - m : Master Server의 레코드 순서
      - n : Slave Server의 레코드 순서

      이 옵션은 대용량 테이블을 비교할 때, 부하를 많이 줄 수 있으므로 주의해서 사용해야 한다.

  - Compile Option

  - Error Code

### BUG-48136 Support for Altibase 7.1 on Windows clients

-   **module** : ul-odbc

-   **Category** : Other

-   **Reproducibility** : Always

-   **Description** : Support for Windows clients introduced from Altibase 7.1.0.4.5

-   **How to reproduce this bug**
    -   **Reproduction conditions**
    
    -   **Actual Results**
    
    -   **Expected Results**
    
-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

Fixed Bugs
----------

### BUG-48120 Added the __OPTIMIZER_SCAN_COST_MODE property to resolve the issue of inefficient index selection due to the difference between index NDV and predicate NDV.

-   **module** : qp-select-pvo

-   **Category** : Enhancement

-   **Reproducibility** : Always

-   **Description** : Added the __OPTIMIZER_SCAN_COST_MODE property to resolve the issue of inefficient index selection due to the difference between index NDV and predicate NDV.
    
- **How to reproduce this bug**

  -   **Reproduction conditions**

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

  - **Actual Results**

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

  -   **Expected Results**

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

-   **Changes**

    -   Performance view
    -   Property
-   Compile Option
    
    -   Error Code

### BUG-48128 Fixed an issue where the result values differed when a subquery was used in the target clause's HAVING clause, and the subquery's parent query included an aggregation function and GROUP BY clause.

-   **module** : qp-select-pvo

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where the result values differed when a subquery was used in the target clause's HAVING clause, and the subquery's parent query included an aggregation function and GROUP BY clause.

- **How to reproduce this bug**

  -   **Reproduction conditions**

          drop table t1;
          drop table t2;
          create table t1 (i1 int, i2 int, i3 int, i4 int);
          create table t2 ( i1 int);
          insert into t1 values( 1,1,1,3);
          insert into t1 values( 2,2,2,4);
          insert into t2 values(1);
          
          select /*+ group_sort*/ max(i4), (select count(*) from t2 where i1 = t1.i1) as sub from t1 group by i1;

  - **Actual Results**

        MAX(I4)     SUB
        ------------------------------------
        3           1
        4           1

  -   **Expected Results**

          MAX(I4)     SUB
          ------------------------------------
          3           1
          4           0
          2 rows selected.

-   **Workaround**

        select /*+ group_hash*/ max(i4), (select count(*) from t2 where i1 = t1.i1) as sub from t1 group by i1;

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48135 Added a property to adjust the Index NL Join Penalty value.

-   **module** : qp-select-pvo
-   **Category** : Enhancement
-   **Reproducibility** : Always
-   **Description** :  Added a property to adjust the Index NL Join Penalty value to resolve the issue of inefficient execution plans caused by incorrect adjustment values for the Index Nested Loop's access cost.
-   **How to reproduce this bug**

    -   **Reproduction conditions**

    -   **Actual Results**

    -   **Expected Results**
-   **Workaround**
-   **Changes**

    -   Performance view
    -   Property
        -   New
            -   __OPTIMIZER_INDEX_NL_JOIN_PENALTY
                -   Description : Index Nl JOIN의 Cost 계산에서 사용되는 Penalty
                -   Default Value: 6
                -   Range: [0, 26]
    -   Compile Option
    -   Error Code

Changes
-------

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 7.1.0.4.5        | 6.5.1                   | 8.9.1        | 7.1.7               | 7.4.6                        |

> You can check the module version change history in [Version_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.1/Altibase_7_1_Version_Histories.md).

### Compatibility

#### Database binary version

The database binary version has not changed.

> The database binary version indicates the compatibility of database image files and log files. If this version needs to be patched to a different version, the database must be reorganized.

#### Meta Version

The meta version has not changed.

> If you want to roll back the patch after patching to a version with a changed meta version, see [Meta Downgrade](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/eng/Installation Guide.md#meta-downgrade).

#### CM protocol Version

The cm protocol version has not changed.

#### Replication protocol Version

The replication protocol version has not changed.

### Altibase Server Properties

#### Added properties

#### Changed properties

#### Deleted properties

### Performance Views

#### Added performance views

#### Changed performance views

#### Deleted performance views
