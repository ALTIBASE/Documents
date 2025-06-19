Altibase 7.1.0.4.2 Patch Notes
================================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [New Features](#new-features)
  - [BUG-48014 Support added for the ST_Collect function.](#bug-48014%C2%A0support-added-for-the-st_collect-function)
  - [BUG-48023  Restored the aexport performance that was degraded due to query plan changes in Altibase 7.1.](#bug-48023%C2%A0-restored-the-aexport-performance-that-was-degraded-due-to-query-plan-changes-in-altibase-71)
  - [BUG-48047  Provided AIX package with heapmin removed.](#bug-48047%C2%A0-provided-aix-package-with-heapmin-removed)
- [Fixed Bugs](#fixed-bugs)
  - [BUG-46438  Fixed an issue where an incorrect error message was displayed when a query failed due to the SORT_AREA_SIZE being too small.](#bug-46438%C2%A0-fixed-an-issue-where-an-incorrect-error-message-was-displayed-when-a-query-failed-due-to-the-sort_area_size-being-too-small)
  - [BUG-47761 Fixed an issue where replication start failed after performing SPLIT, MERGE, or DROP PARTITION on a replication target table.](#bug-47761%C2%A0fixed-an-issue-where-replication-start-failed-after-performing-split-merge-or-drop-partition-on-a-replication-target-table)
  - [BUG-47967 Fixed an issue where a result value error occurred when there were more than one external reference column in a subquery.](#bug-47967-fixed-an-issue-where-a-result-value-error-occurred-when-there-were-more-than-one-external-reference-column-in-a-subquery)
  - [BUG-48026 Fixed an issue where replication stops due to a network failure during the replication handshake.](#bug-48026-fixed-an-issue-where-replication-stops-due-to-a-network-failure-during-the-replication-handshake)
  - [BUG-48036 Fixed an issue where the status of the related object was not changed to invalid after alter table modify column.](#bug-48036-fixed-an-issue-where-the-status-of-the-related-object-was-not-changed-to-invalid-after-alter-table-modify-column)
  - [BUG-48045  Fixed an issue where result errors occurred when applying view optimization in a WITH clause.](#bug-48045%C2%A0-fixed-an-issue-where-result-errors-occurred-when-applying-view-optimization-in-a-with-clause)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [Compatibility](#compatibility)
  - [Altibase Server Properties](#altibase-server-properties)
  - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
------------

### BUG-48014 Support added for the ST_Collect function.

-   **module** : st

-   **Category** : Enhancement

-   **Reproducibility** : Always

- **Description** : Support added for the ST_Collect function.

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

### BUG-48023  Restored the aexport performance that was degraded due to query plan changes in Altibase 7.1.

-   **module** : ux-aexport

-   **Category** : Efficiency

-   **Reproducibility** : Always

-   **Description** : Restored the aexport performance that was degraded due to query plan changes in Altibase 7.1.
    
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

### BUG-48047  Provided AIX package with heapmin removed.

-   **module** : id

-   **Category** : Maintainability

-   **Reproducibility** : Unknown

-   **Description** : Provided AIX package with heapmin removed.

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

### BUG-46438  Fixed an issue where an incorrect error message was displayed when a query failed due to the SORT_AREA_SIZE being too small.

-   **module** : sm-disk-resource

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where an incorrect error message was displayed when a query failed due to the SORT_AREA_SIZE being too small. Now, the error message [ERR-11185 : Insufficient sort area space] will be displayed in such cases.

- **How to reproduce this bug**

  - **Reproduction conditions**

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

  -   **Actual Results**

          [ERR-11069 : Internal server error in the storage manager ([FAILURE] ERR-0109E(error=11) Internal server error.)]

  -   **Expected Results**

          [ERR-11185 : Insufficient sort area space]

-   **Workaround**

        SORT_AREA_SIZE를 늘려주세요,

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47761 Fixed an issue where replication start failed after performing SPLIT, MERGE, or DROP PARTITION on a replication target table.

-   **module** : rp

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** :  Fixed an issue where replication start failed after performing SPLIT, MERGE, or DROP PARTITION on a replication target table.

-   **How to reproduce this bug**

    -   **Reproduction conditions**

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

    -   **Actual Results**

            [Sender] Failed to handshake with the peer server (The replication's item count does not match [3:4].)]

    -   **Expected Results**

            Success

-   **Workaround**

-   **Changes**

    - Performance view
    
    - Property
    
      - 추가
    
        - REPLICATION_META_ITEM_COUNT_DIFF_ENABLE
    
          - Default value : 0
    
          - Range : 0,1
    
          - Description : This property allows starting replication even when the number of partition meta items in the replication tables of the Active and Standby servers differs, following SPLIT PARTITION, MERGE PARTITION, or DROP PARTITION operations in Lazy mode replication. By setting this property to 1, replication can be started even when the partition meta item count differs between the Active and Standby servers.
    
            The value of this property can be changed during Altibase operation using the ALTER SYSTEM command.
    
    - Compile Option
    
    -   Error Code

### BUG-47967 Fixed an issue where a result value error occurred when there were more than one external reference column in a subquery.

-   **module** : qp-select

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where a result value error occurred when there were more than one external reference column in a subquery.
    
- **How to reproduce this bug**

  -   **Reproduction conditions**

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

  - **Actual Results**

        I2          SQ_I2
        ---------------------------
        R001        R001
        RM01        R001
        2 rows selected.

  -   **Expected Results**

          I2          SQ_I2
          ---------------------------
          R001        R001
          RM01        RM01
          2 rows selected.

-   **Workaround**

         alter system set __FORCE_SUBQUERY_CACHE_DISABLE=1;

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48026 Fixed an issue where replication stops due to a network failure during the replication handshake.

-   **module** : dm

-   **Category** : Functional Error

-   **Reproducibility** : Rare

-   **Description** : Fixed an issue where replication stops due to a network failure during the replication handshake.
    
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

### BUG-48036 Fixed an issue where the status of the related object was not changed to invalid after alter table modify column.

-   **module** : qp-ddl-dcl-execute

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where the status of the related object was not changed to invalid after alter table modify column.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

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

  -   **Actual Results**

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

  -   **Expected Results**

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

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48045  Fixed an issue where result errors occurred when applying view optimization in a WITH clause.

-   **module** : qp-dml-pvo

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where result errors occurred when applying view optimization in a WITH clause.

- **How to reproduce this bug**

  -   **Reproduction conditions**

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
      
  - **Actual Results**

        ACTG_NO
        -----------------------
        
        1 row selected.

  -   **Expected Results**

          ACTG_NO
          -----------------------
          2
          1 row selected.

-   **Workaround**

        alter system set __OPTIMIZER_VIEW_TARGET_ENABLE = 0;

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

Changes
-------

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 7.1.0.4.2        | 6.5.1                   | 8.8.1        | 7.1.7               | 7.4.6                        |

> You can check the module version change history in [Version_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.1/Altibase_7_1_Version_Histories.md).

### Compatibility

#### Database binary version

The database binary version has not changed.

> The database binary version indicates the compatibility of database image files and log files. If this version needs to be patched to a different version, the database must be reorganized.

#### Meta Version

The meta version has not changed.

> If you want to roll back the patch after patching to a version with a changed meta version, see [Meta Downgrade](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/eng/Installation%20Guide.md#meta-downgrade).

#### CM protocol Version

The cm protocol version has not changed.

#### Replication protocol Version

The replication protocol version has not changed.

### Altibase Server Properties

#### Added properties

REPLICATION_META_ITEM_COUNT_DIFF_ENABLE

### Performance Views

No performance views were added, modified, or deleted.
