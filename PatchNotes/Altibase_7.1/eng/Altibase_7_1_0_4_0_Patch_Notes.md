Altibase 7.1.0.4.0 Patch Notes
================================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [New Features](#new-features)
  - [BUG-47805  Support for SRID(Spatial Reference IDentifier) interface](#bug-47805-%C2%A0support-for-sridspatial-reference-identifier-interface)
  - [BUG-47873 Replication Support for SRID Attribute in GEOMETRY Column.](#bug-47873%C2%A0replication-support-for-srid-attribute-in-geometry-column)
  - [BUG-47816  Support for ST_Transform](#bug-47816%C2%A0-support-for-st_transform)
  - [BUG-47857  Support for ST_MakePoint](#bug-47857%C2%A0-support-for-st_makepoint)
  - [BUG-47883  Support for ST_MakeLine](#bug-47883%C2%A0-support-for-st_makeline)
  - [BUG-47919  Support for ST_MakeEnvelope with SRID parameter](#bug-47919%C2%A0-support-for-st_makeenvelope-with-srid-parameter)
  - [BUG-47966  Support for ST_PolygonFromText](#bug-47966%C2%A0-support-for-st_polygonfromtext)
  - [BUG-47974  Removed Mutex Bottleneck When File Count Exceeds MAX_OPEN_DATAFILE_COUNT Property](#bug-47974%C2%A0-removed-mutex-bottleneck-when-file-count-exceeds-max_open_datafile_count-property)
  - [BUG-47963  Added the feature to show the number of identical records in altiComp](#bug-47963%C2%A0-added-the-feature-to-show-the-number-of-identical-records-in-alticomp)
- [Fixed Bugs](#fixed-bugs)
  - [BUG-47786 Fixed Result Error Issue During Subquery Unnesting Caused by Inverse Join](#bug-47786-fixed-result-error-issue-during-subquery-unnesting-caused-by-inverse-join)
  - [BUG-47840  Optimized Execution Memory for Simple Partition Insert](#bug-47840%C2%A0-optimized-execution-memory-for-simple-partition-insert)
  - [BUG-47868  Fixed Incorrect Memory Size Calculation for Internal SQL Conversion in Anonymous Block in APRE.](#bug-47868%C2%A0-fixed-incorrect-memory-size-calculation-for-internal-sql-conversion-in-anonymous-block-in-apre)
  - [BUG-47884 Fixed Mismatch Between Index and Index Statistics During Query Preparation.](#bug-47884%C2%A0fixed-mismatch-between-index-and-index-statistics-during-query-preparation)
  - [BUG-47889 Enabled Case Sensitivity for Passwords in altipasswd](#bug-47889-enabled-case-sensitivity-for-passwords-in-altipasswd)
  - [BUG-47900 Fixed an issue where an incorrect SN value was written to logs when an error occurred during a replication update XSN.](#bug-47900%C2%A0fixed-an-issue-where-an-incorrect-sn-value-was-written-to-logs-when-an-error-occurred-during-a-replication-update-xsn)
  - [BUG-47901 Resolved an issue where the timeout in the replication sendStop function was not being properly handled when a timeout occurred.](#bug-47901%C2%A0resolved-an-issue-where-the-timeout-in-the-replication-sendstop-function-was-not-being-properly-handled-when-a-timeout-occurred)
  - [BUG-47910 Fixed a bug where the unique constraint of a table for which no statistical information was collected was included in the ALL_EXE_STATS.sql file for tables where statistics were not collected.](#bug-47910%C2%A0fixed-a-bug-where-the-unique-constraint-of-a-table-for-which-no-statistical-information-was-collected-was-included-in-the-all_exe_statssql-file-for-tables-where-statistics-were-not-collected)
  - [BUG-47917 Fixed Parsing Error in External Procedure Creation with 'AS LANGUAGE C'.](#bug-47917%C2%A0fixed-parsing-error-in-external-procedure-creation-with-as-language-c)
  - [BUG-47918 Fixed Issue with DDL Sync Failure During PARTITION SPLIT Using Identical Partition Names.](#bug-47918%C2%A0fixed-issue-with-ddl-sync-failure-during-partition-split-using-identical-partition-names)
  - [BUG-47944  Fixed an issue where performing a meta downgrade from metaversion 8.8.1 or 8.7.1 to a lower version fails.](#bug-47944%C2%A0-fixed-an-issue-where-performing-a-meta-downgrade-from-metaversion-881-or-871-to-a-lower-version-fails)
  - [BUG-47945  Added Debugging Code for Disk Buffer CheckPoint List Error.](#bug-47945%C2%A0-added-debugging-code-for-disk-buffer-checkpoint-list-error)
  - [BUG-47948  Fixed the concurrency problem occurring when executing DROP TABLESPACE for 'memory_tablespace' and querying V$DATABASE simultaneously.](#bug-47948%C2%A0-fixed-the-concurrency-problem-occurring-when-executing-drop-tablespace-for-memory_tablespace-and-querying-vdatabase-simultaneously)
  - [BUG-47953 Fixed Server shut down During Corrupt Page Recovery Using DW_BUFFER with USE_DW_BUFFER Enabled.](#bug-47953%C2%A0fixed-server-shut-down-during-corrupt-page-recovery-using-dw_buffer-with-use_dw_buffer-enabled)
  - [BUG-47954  Resolved an issue where the sender would stop when a truncate operation was performed simultaneously in an replication active-active environment.](#bug-47954%C2%A0-resolved-an-issue-where-the-sender-would-stop-when-a-truncate-operation-was-performed-simultaneously-in-an-replication-active-active-environment)
  - [BUG-47970  Fixed issue where page latch would not release for inconsistent pages in Disk Index.](#bug-47970-%C2%A0fixed-issue-where-page-latch-would-not-release-for-inconsistent-pages-in-disk-index)
  - [BUG-47986  Fixed issue where INNER JOIN on disk tables with OR clause predicate combined with constant filter would incorrectly use the index, causing result errors.](#bug-47986%C2%A0-fixed-issue-where-inner-join-on-disk-tables-with-or-clause-predicate-combined-with-constant-filter-would-incorrectly-use-the-index-causing-result-errors)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [Compatibility](#compatibility)
  - [Altibase Server Properties](#altibase-server-properties)
  - [Performance Views](#performance-views)
  - [Meta Tables](#meta-tables)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
------------

### BUG-47805  Support for SRID(Spatial Reference IDentifier) interface

-   **module** : st-spatial

-   **Category** : Functionality

-   **Reproducibility** : Always

- **Description** : Added SRID (Spatial Reference Identifier) support for ESRI ArcGIS integration, enabling SRID specification in GEOMETRY columns and objects.

  > Upgrade/Downgrade Notice: 
>
  > GEOMETRY column compatibility issue with Meta version 8.7.1 and below (7.1.0.3.9 and below) after upgrade to Meta version 8.8.1.

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

### BUG-47873 Replication Support for SRID Attribute in GEOMETRY Column.

- **module** : rp

- **Category** : Functionality

- **Reproducibility** : Always

- **Description** : With the support of the SRID attribute for GEOMETRY columns, replication now supports SRID attributes.

  Customers who do not use GEOMETRY columns will not encounter issues before or after the patch.

  For customers using GEOMETRY columns, please be aware of the following replication considerations:

  > **Replication Considerations for GEOMETRY Columns:**
  >
  > - Replication from a version supporting SRID (7.1.0.4.0 or above) to a version that does not support SRID (7.1.0.3.9 or below) is not possible.
  > - Replication from a version not supporting SRID (7.1.0.3.9 or below) to a version that supports SRID (7.1.0.4.0 or above) is possible."
  
- **How to reproduce this bug**

  -   **Reproduction conditions**

  -   **Actual Results**

  -   **Expected Results**

- **Workaround**

- **Changes**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

### BUG-47816  Support for ST_Transform 

-   **module** : st-function

-   **Category** : Functionality

-   **Reproducibility** : Always

- **Description** : Support for ST_Transform

  ```
  GEOMETRY ST_Transform( GEOMETRY, INTEGER to_srid );
  GEOMETRY ST_Transform( GEOMETRY, VARCHAR to_proj4text );
  GEOMETRY ST_Transform( GEOMETRY, VARCHAR from_proj4text, VARCHAR to_proj4text );
  GEOMETRY ST_Transform( GEOMETRY, VARCHAR from_proj4text, INTEGER to_srid );
  ```

>Caution
>
>Support for PROJ4TEXT Syntax in PROJ Library Version 4 Format

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

### BUG-47857  Support for ST_MakePoint

-   **module** : st

-   **Category** : Enhancement

-   **Reproducibility** : Always

- **Description** : Support for ST_MakePoint.

  ```
  ST_MAKEPOINT( x, y )
  ```

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

### BUG-47883  Support for ST_MakeLine

-   **module** : st

-   **Category** : Enhancement

-   **Reproducibility** : Always

- **Description** : [ST_MakeLine](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/SpatialSQL.md#st_makeline) 함수가 추가되었습니다.

  ```
  ST_MAKELINE( GEOMETRY1, GEOMETRY2 )
  ```

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

### BUG-47919  Support for ST_MakeEnvelope with SRID parameter

-   **module** : st-function

-   **Category** : Functionality

-   **Reproducibility** : Always

- **Description** : Support for ST_MakeEnvelope with SRID parameter.

  ```
  ST_MAKEENVELOPE( X1, Y1, X2, Y2[, SRID=0] )
  ```

- **How to reproduce this bug**

  -   **Reproduction conditions**

          SELECT ASEWKT( MAKEENVELOPE( 0, -1, 2, 3, 1000000 ) ) FROM DUAL;

  -   **Actual Results**

  -   **Expected Results**

          ASEWKT( MAKEENVELOPE( 0, -1, 2, 3, 1000000
          --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
          SRID=1000000;POLYGON((0 -1, 2 -1, 2 3, 0 3, 0 -1))

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47966  Support for ST_PolygonFromText

-   **module** : st-function

-   **Category** : Enhancement

-   **Reproducibility** : Always

- **Description** : Support for ST_PolygonFromText

  구문은 아래와 같습니다.

  ```
  ST_PolygonFromText( wkt [, SRID] )
  ```

-   **How to reproduce this bug**

    -   **Reproduction conditions**

            create table t1 ( geom geometry );
            insert into t1
            values(
            ST_PolygonFromText('POLYGON((-71.1776585052917 42.3902909739571,-71.1776820268866 42.3903701743239,
            -71.1776063012595 42.3903825660754,-71.1775826583081 42.3903033653531,-71.1776585052917 42.3902909739571))')
            );
            insert into t1
            values(
            ST_PolygonFromText('POLYGON((-71.1776585052917 42.3902909739571,-71.1776820268866 42.3903701743239,
            -71.1776063012595 42.3903825660754,-71.1775826583081 42.3903033653531,-71.1776585052917 42.3902909739571))', 140)
            );
            select asewkt( the_geom ) from t1;

    -   **Actual Results**

    -   **Expected Results**

            1 row inserted.
            1 row inserted.
            ASEWKT(THE_GEOM)
            -----------------------------------------------------------------------------------------------------------------------------------------
            SRID=0;POLYGON((-71.17766 42.39029, -71.17768 42.39037, -71.17761 42.39038, -71.17758 42.3903, -71.17766 42.39029))
            SRID=140;POLYGON((-71.17766 42.39029, -71.17768 42.39037, -71.17761 42.39038, -71.17758 42.3903, -71.17766 42.39029))
            2 rows selected.

-   **Workaround**

        ST_PolyFromTextSET_SRID + ST_PolyFromText

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47974  Removed Mutex Bottleneck When File Count Exceeds MAX_OPEN_DATAFILE_COUNT Property

-   **module** : sm\_resource
-   **Category** : Enhancement
-   **Reproducibility** : Frequence
-   **Description** : Removed Mutex Bottleneck When File Count Exceeds MAX_OPEN_DATAFILE_COUNT Property
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

### BUG-47963  Added the feature to show the number of identical records in altiComp

- **module** : ux-audit(altiComp)

- **Category** : Enhancement

- **Reproducibility** : Always

- **Description** : Added the feature(EQ) to show the number of identical records in altiComp

  ```
  [EQ_T->EQ_T]
  Fetch Rec In Master: 3
  Fetch Rec In Slave : 3
  MOSX = DF, Count :          1
  MXSO = DF, Count :          1
  MOSO = DF, Count :          1
  MOSO = EQ, Count :          1
  ```

- **How to reproduce this bug**

  -   **Reproduction conditions**

  -   **Actual Results**

  -   **Expected Results**

- **Workaround**

- **Changes**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

Fixed Bugs
----------

### BUG-47786 Fixed Result Error Issue During Subquery Unnesting Caused by Inverse Join

-   **module** : qp

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Resolved an issue where a result error occurred during subquery unnesting due to the use of Inverse Join

- **How to reproduce this bug**

  - **Reproduction conditions**

        drop table TB1;
        drop table TB2;
        drop table TB3;
        drop table TB4;
        drop table TB5;
        
        create table TB1(
        CUST_CODE                                VARCHAR(30)                 NOT NULL,
        SW_VER                                   VARCHAR(50)                 NOT NULL
        ) tablespace sys_tbs_disk_data;
        
        alter table TB1 add primary key( CUST_CODE );
        
        insert into TB1 values ( 'A', '111');
        insert into TB1 values ( 'B', '111');
        insert into TB1 values ( 'C', '111');
        insert into TB1 values ( 'D', '111');
        insert into TB1 values ( 'E', '111');
        insert into TB1 values ( 'F', '111');
        insert into TB1 values ( 'G', '111');
        insert into TB1 values ( 'H', '111');
        
        create table TB2 (
        RB_SKU_CODE                              VARCHAR(30)                 NOT NULL,
        DEL_YN                                   VARCHAR(1)                  NOT NULL,
        USE_YN                                   VARCHAR(1)                  NOT NULL
        ) tablespace sys_tbs_disk_data;;
        
        insert into TB2 values ( 'a', 'Y', 'N');
        insert into TB2 values ( 'b', 'Y', 'N');
        insert into TB2 values ( 'c', 'Y', 'N');
        insert into TB2 values ( 'd', 'Y', 'N');
        insert into TB2 values ( 'e', 'Y', 'N');
        insert into TB2 values ( 'f', 'Y', 'N');
        insert into TB2 values ( 'g', 'Y', 'N');
        insert into TB2 values ( 'h', 'Y', 'N');
        
        alter table TB2 add primary key( RB_SKU_CODE );
        
        create table TB3 (
        FCT_CODE                                 VARCHAR(30)                 NOT NULL,
        PLANT_CODE                               VARCHAR(30)                 NOT NULL,
        STRG_ID                                  VARCHAR(50)                 NOT NULL,
        RB_SKU_CODE                              VARCHAR(30)                 NOT NULL,
        MIX_REASON_CODE                          VARCHAR(30)                 NOT NULL,
        SW_VER                                   VARCHAR(50)                 NOT NULL,
        DEL_YN                                   VARCHAR(1)                  NOT NULL,
        USE_YN                                   VARCHAR(1)                  NOT NULL
        ) tablespace sys_tbs_disk_data;;
        
        insert into TB3  select 'C310A', 'V341', 'SSS'||level, 'SM6G975UZKATMB', '111', 'Z', 'N', 'Y' from dual connect by level < 30;
        insert into TB3  select 'C310A', 'V341', 'SSS'||'133', 'SM6G975UZKATMB', '111', 'Z', 'N', 'Y' from dual;
        insert into TB3  select 'C310A', 'V341', 'SSS'||'134', 'SM6G975UZKATMB', '222', 'Z', 'N', 'Y' from dual;
        insert into TB3  select 'C310A', 'V340', 'SSS'||'11', 'SM6G975UZKATMB', '111', 'Z', 'N', 'Y' from dual;
        insert into TB3  select 'C310A', 'V340', 'SSS'||'12', 'SM6G975UZKATMB', '222', 'Z', 'N', 'Y' from dual;
        insert into TB3  select 'C310A', 'V340', 'SSS'||'13', 'SM6G975UZKATMB', '222', 'Z', 'N', 'Y' from dual;
        insert into TB3  select 'C310A', 'V340', 'SSS'||'14', 'SM6G975UZKATMB', '222', 'Z', 'N', 'Y' from dual;
        insert into TB3  select 'C310A', 'V340', 'SSS'||'15', 'SM6G975UZKATMB', '111', 'Z', 'N', 'Y' from dual;
        insert into TB3  select 'C310A', 'V340', 'SSS'||'16', 'SM6G975UZKATMB', '222', 'Z', 'N', 'Y' from dual;
        insert into TB3  select 'C310A', 'V340', 'SSS'||'17', 'SM6G975UZKATMB', '222', 'Z', 'N', 'Y' from dual;
        insert into TB3  select 'C310A', 'V340', 'SSS'||'18', 'SM6G975UZKATMB', '222', 'Z', 'N', 'Y' from dual;
        
        create table TB4 (
        COMM_CODE varchar(30 ),
        TYPE_CODE varchar(30 ),
        DEL_YN                                   VARCHAR(1)                  NOT NULL,
        USE_YN                                   VARCHAR(1)                  NOT NULL
        ) tablespace sys_tbs_disk_data;
        
        insert into TB4 select 'SSS'||level, 'PICK_STRG', 'N', 'Y' from dual connect by level < 30;
        
        alter table TB4 add primary key( TYPE_CODE, COMM_CODE );
        
        create table TB5(
        COMM_CODE varchar(30 ),
        CUST_CODE varchar(30 ),
        CUST_TYPE_CODE varchar(30),
        CUST_COMM_CODE varchar(30),
        COB_MULTI_MIX_REASON_YN varchar(30),
        DEL_YN                                   VARCHAR(1)                  NOT NULL,
        USE_YN                                   VARCHAR(1)                  NOT NULL,
        ATTR_C1_CODE varchar(30)
        )tablespace sys_tbs_disk_data;
        
        insert into TB5 values ( '111', '3433418X', 'COBCUST', '111', 'Y', 'N', 'Y', '973');
        insert into TB5 values ( '222', '3433418X', 'MULTI_MIX_REASON', '111', 'Y', 'N', 'Y', '973');
        insert into TB5 values ( '111', '3433418X', 'MULTI_MIX_REASON', '222', 'Y', 'N', 'Y', '973');
        
        drop index idx1;
        create index idx1 on TB5 ( CUST_CODE, CUST_TYPE_CODE);
        
        SELECT A.DEL_YN, A.USE_YN  
        FROM TB3 A
             , (SELECT DECODE(COUNT(T2.CUST_COMM_CODE),0,'N','Y') COB_MULTI_MIX_REASON_YN
                  FROM TB5 T1
                     , TB5 T2
                 WHERE T1.CUST_CODE = '3433418X'
                   AND T1.CUST_TYPE_CODE = 'COBCUST'
                   AND T2.CUST_CODE = '3433418X'
                   AND T1.DEL_YN = 'N'
                   AND T1.USE_YN = 'Y'
                   AND T2.CUST_TYPE_CODE = 'MULTI_MIX_REASON'
                   AND T2.ATTR_C1_CODE LIKE '%' || '973' || '%'
                   AND T2.DEL_YN = 'N'
                   AND T2.USE_YN = 'Y') G                                  
         WHERE 1 = 1
           AND A.FCT_CODE              = 'C310A'
           AND A.STRG_ID               IN (SELECT COMM_CODE FROM TB4 WHERE TYPE_CODE = 'PICK_STRG' AND DEL_YN = 'N' AND USE_YN = 'Y') 
           AND A.RB_SKU_CODE           = 'SM6G975UZKATMB'            
           AND ((G.COB_MULTI_MIX_REASON_YN = 'N' AND A.MIX_REASON_CODE = '000')
                 OR
                (G.COB_MULTI_MIX_REASON_YN = 'Y' 
        		     AND A.MIX_REASON_CODE IN (SELECT T2.CUST_COMM_CODE
                                                FROM TB5 T1
                                                   , TB5 T2
                                                WHERE T1.CUST_CODE = '3433418X'
                                                  AND T1.CUST_TYPE_CODE = 'COBCUST'
                                                  AND T2.CUST_CODE = '3433418X'
                                                  AND T1.DEL_YN = 'N'
                                                  AND T1.USE_YN = 'Y'
                                                  AND T2.CUST_TYPE_CODE = 'MULTI_MIX_REASON'
                                                  AND T2.ATTR_C1_CODE LIKE '%' || '973' || '%'
                                                  AND T2.DEL_YN = 'N'
                                                  AND T2.USE_YN = 'Y')))   
           AND ( A.RB_SKU_CODE, A.SW_VER ) NOT IN (SELECT /*+*/ B.RB_SKU_CODE ,  A.SW_VER 
                                                     FROM TB1 A, TB2 B
                                                    WHERE B.RB_SKU_CODE = 'x'
                                                      AND A.CUST_CODE = 'x'  
                                                      AND B.DEL_YN = 'N' AND B.USE_YN = 'Y') 
          AND A.DEL_YN = 'N' AND A.USE_YN = 'Y'
          ;

  - **Actual Results**

        DEL_YN  USE_YN
        -------------------
        N  Y
        N  Y
        N  Y
        N  Y
        N  Y
        N  Y
        6 rows selected.

  -   **Expected Results**

          DEL_YN  USE_YN
          -------------------
          N  Y
          N  Y
          N  Y
          N  Y
          N  Y
          N  Y
          N  Y
          N  Y
          N  Y
          N  Y
          N  Y
          N  Y
          N  Y
          N  Y
          N  Y
          N  Y
          N  Y
          N  Y
          N  Y
          N  Y
          N  Y
          N  Y
          N  Y
          N  Y
          N  Y
          N  Y
          N  Y
          N  Y
          N  Y
          N  Y
          N  Y
          N  Y
          N  Y
          N  Y
          N  Y
          N  Y
          N  Y
          37 rows selected.

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47840  Optimized Execution Memory for Simple Partition Insert

-   **module** : qp
-   **Category** : Efficiency
-   **Reproducibility** : Always
-   **Description** : Improved execution memory usage during simple partition insert operations to enhance performance and resource efficiency.
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

### BUG-47868  Fixed Incorrect Memory Size Calculation for Internal SQL Conversion in Anonymous Block in APRE.

-   **module** : mm-apre

-   **Category** : Functional Error

-   **Reproducibility** : Rare

-   **Description** : Resolved an issue where the memory size for the internal SQL conversion was incorrectly calculated when using Anonymous Blocks in APRE.

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

### BUG-47884 Fixed Mismatch Between Index and Index Statistics During Query Preparation.

-   **module** : qp-dml-pvo

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Resolved an issue where the index and its corresponding statistics were not properly matched during query preparation.
    
-   **How to reproduce this bug**

    -   **Reproduction conditions**

            drop table t1;
            create table t1(i1 varchar(10), i2 varchar(20), i3 varchar(30));
            create index t1_idx1 on t1(i2);
            create index t1_idx2 on t1(i3);
            insert into t1 ( select level, mod(level, 30), mod(level, 40) from dual connect by level<=1000);
            alter table t1 add constraint t1_pk primary key (i1);
            create index t1_idx3 on t1(i2, i3);
            exec gather_database_stats();
            alter system set trclog_explain_graph=1;
            alter session set explain plan = on;
            select * from t1;
            var v1 bigint;
            var v2 bigint;
            var v3 bigint;
            var v4 bigint;
            var v5 bigint;
            var v6 bigint;
            var v7 bigint;
            exec GET_INDEX_STATS( 'SYS', 'T1_PK', NULL,  :v1,:v2,:v3,:v4,:v5,:v6,:v7);
            print v3;
            exec GET_INDEX_STATS( 'SYS', 'T1_IDX1', NULL,  :v1,:v2,:v3,:v4,:v5,:v6,:v7);
            print v3;
            exec GET_INDEX_STATS( 'SYS', 'T1_IDX2', NULL,  :v1,:v2,:v3,:v4,:v5,:v6,:v7);
            print v3;
            exec GET_INDEX_STATS( 'SYS', 'T1_IDX3', NULL,  :v1,:v2,:v3,:v4,:v5,:v6,:v7);
            print v3;

    -   **Actual Results**

            |  |== Index Information ==
            |  |  T1_IDX3 : 120
            |  |  T1_IDX1 : 1000
            |  |  T1_PK : 40
            |  |  T1_IDX2 : 30
            iSQL> exec GET_INDEX_STATS( 'SYS', 'T1_PK', NULL,  :v1,:v2,:v3,:v4,:v5,:v6,:v7);
            Execute success.
            iSQL> print v3;
            NAME                 TYPE                 VALUE
            -------------------------------------------------------
            V3                   BIGINT               1000
            iSQL> exec GET_INDEX_STATS( 'SYS', 'T1_IDX1', NULL,  :v1,:v2,:v3,:v4,:v5,:v6,:v7);
            Execute success.
            iSQL> print v3;
            NAME                 TYPE                 VALUE
            -------------------------------------------------------
            V3                   BIGINT               30
            iSQL> exec GET_INDEX_STATS( 'SYS', 'T1_IDX2', NULL,  :v1,:v2,:v3,:v4,:v5,:v6,:v7);
            Execute success.
            iSQL> print v3;
            NAME                 TYPE                 VALUE
            -------------------------------------------------------
            V3                   BIGINT               40
            iSQL> exec GET_INDEX_STATS( 'SYS', 'T1_IDX3', NULL,  :v1,:v2,:v3,:v4,:v5,:v6,:v7);
            Execute success.
            iSQL> print v3;
            NAME                 TYPE                 VALUE
            -------------------------------------------------------
            V3                   BIGINT               120

    -   **Expected Results**

            |  |== Index Information ==
            |  |  T1_IDX3 : 120
            |  |  T1_IDX1 : 30
            |  |  T1_PK : 1000
            |  |  T1_IDX2 : 40
            iSQL> exec GET_INDEX_STATS( 'SYS', 'T1_PK', NULL,  :v1,:v2,:v3,:v4,:v5,:v6,:v7);
            Execute success.
            iSQL> print v3;
            NAME                 TYPE                 VALUE
            -------------------------------------------------------
            V3                   BIGINT               1000
            iSQL> exec GET_INDEX_STATS( 'SYS', 'T1_IDX1', NULL,  :v1,:v2,:v3,:v4,:v5,:v6,:v7);
            Execute success.
            iSQL> print v3;
            NAME                 TYPE                 VALUE
            -------------------------------------------------------
            V3                   BIGINT               30
            iSQL> exec GET_INDEX_STATS( 'SYS', 'T1_IDX2', NULL,  :v1,:v2,:v3,:v4,:v5,:v6,:v7);
            Execute success.
            iSQL> print v3;
            NAME                 TYPE                 VALUE
            -------------------------------------------------------
            V3                   BIGINT               40
            iSQL> exec GET_INDEX_STATS( 'SYS', 'T1_IDX3', NULL,  :v1,:v2,:v3,:v4,:v5,:v6,:v7);
            Execute success.
            iSQL> print v3;
            NAME                 TYPE                 VALUE
            -------------------------------------------------------
            V3                   BIGINT               120

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47889 Enabled Case Sensitivity for Passwords in altipasswd

-   **module** : ux-isql

-   **Category** : Functionality

-   **Reproducibility** : Always

-   **Description** : Modified altipasswd to enforce case sensitivity for passwords based on the CASE_SENSITIVE_PASSWORD value in altibase.properties.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

  - **Actual Results**
  
  - **Expected Results**
  
-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47900 Fixed an issue where an incorrect SN value was written to logs when an error occurred during a replication update XSN.

-   **module** : rp

-   **Category** : Other

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where an incorrect SN value was written to logs when an error occurred during a replication update XSN.
    
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

### BUG-47901 Resolved an issue where the timeout in the replication sendStop function was not being properly handled when a timeout occurred.

-   **module** : rp

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Resolved an issue where the timeout in the replication sendStop function was not being properly handled when a timeout occurred.
    
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

### BUG-47910 Fixed a bug where the unique constraint of a table for which no statistical information was collected was included in the ALL_EXE_STATS.sql file for tables where statistics were not collected.

-   **module** : ux-aexport

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed a bug where the unique constraint of a table for which no statistical information was collected was included in the ALL_EXE_STATS.sql file for tables where statistics were not collected.
    
- **How to reproduce this bug**

  -   **Reproduction conditions**

          #######################
          # iSQL
          #######################
          /*  initialize */
          EXEC DELETE_DATABASE_STATS();
          drop table t1 cascade;
          drop table t2 cascade;
          drop table t3 cascade;
          /*  target table */
          create table t1 (c1 integer primary key, c2 char(10));
          create table t3 (c1 integer primary key, c2 char(10));
          insert into t1 values (1, 't1');
          insert into t3 values (3, 't3');
          /* gather statistics */
          EXEC GATHER_DATABASE_STATS();
          
          create table t2 (c1 integer primary key, c2 char(10), c3 char(10));
          alter table t2 add unique("C2");
          alter table t2 add unique("C3");
          #######################
          # shell
          #######################
          aexport -s 127.0.0.1 -u sys -p manager
          cat ALL_EXE_STATS.sql;

  - **Actual Results**

        $ cat ALL_EXE_STATS.sql;
        ...
        EXEC SET_TABLE_STATS('"SYS"', '"T1"', NULL, 1, 1, 16, 0.000000);
        EXEC SET_COLUMN_STATS('"SYS"', '"T1"', '"C1"', NULL, 1, 0, 4, '1', '1');
        EXEC SET_COLUMN_STATS('"SYS"', '"T1"', '"C2"', NULL, 1, 0, 12, 't1        ', 't1        ');
        EXEC SET_PRIMARY_KEY_STATS('"SYS"', '"T1"', 1, 1, 0, 0, 0, 1);
        EXEC SET_UNIQUE_KEY_STATS('"SYS"', '"T2"', '"C2"', EXEC SET_UNIQUE_KEY_STATS('"SYS"', '"T2"', '"C3"', EXEC SET_TABLE_STATS('"SYS"', '"T3"', NULL, 1, 1, 16, 0.000000);
        EXEC SET_COLUMN_STATS('"SYS"', '"T3"', '"C1"', NULL, 1, 0, 4, '3', '3');
        EXEC SET_COLUMN_STATS('"SYS"', '"T3"', '"C2"', NULL, 1, 0, 12, 't3        ', 't3        ');
        EXEC SET_PRIMARY_KEY_STATS('"SYS"', '"T3"', 1, 1, 0, 0, 0, 1);

  -   **Expected Results**

          $ cat ALL_EXE_STATS.sql;
          ...
          EXEC SET_COLUMN_STATS('SYS', 'T1', 'C1',NULL, 1, 0, 4, '1', '1');
          EXEC SET_COLUMN_STATS('SYS', 'T1', 'C2',NULL, 1, 0, 12, 't1        ', 't1        ');
          EXEC SET_TABLE_STATS('SYS', 'T3', NULL, 1, 1, 16, 0.000000);
          EXEC SET_COLUMN_STATS('SYS', 'T3', 'C1',NULL, 1, 0, 4, '3', '3');
          EXEC SET_COLUMN_STATS('SYS', 'T3', 'C2',NULL, 1, 0, 12, 't3        ', 't3        ');

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47917 Fixed Parsing Error in External Procedure Creation with 'AS LANGUAGE C'.

-   **module** : qp-psm-trigger-pvo

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed Parsing Error in External Procedure Creation with 'AS LANGUAGE C'.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

        Drop Library TestLib2;
        Drop Procedure SimpleExternalProcedure;
        
        CREATE OR REPLACE LIBRARY TestLib2 AS 'str_uppercase2.so';
        
        CREATE OR REPLACE PROCEDURE SimpleExternalProcedure (a1 in varchar2, a2 out varchar2)  AS  language c  name  "str_uppercase2" library TestLib2;
        /

  - **Actual Results**

        [ERR-31001 : SQL syntax error
        0001 : CREATE OR REPLACE PROCEDURE SIMPLEEXTERNALPROCEDURE (A1 in VARCHAR2, A2 out VARCHAR2)  AS  language C  NAME  "str_uppercase2" library TestLib2
                                                                                                                  ^^
        ]

  -   **Expected Results**

          Create success.

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47918 Fixed Issue with DDL Sync Failure During PARTITION SPLIT Using Identical Partition Names.

-   **module** : rp

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixed a problem where replication DDL Sync would cause an abnormal termination when performing a PARTITION SPLIT with identical partition names.
    
-   **How to reproduce this bug**

    -   **Reproduction conditions**

            create table part_tbl
            (c1 integer primary key,
            c2 char(1200)
            ) 
            partition by range (c1)
            (partition d1 values default tablespace USER_DATA_MEM) tablespace USER_DATA_MEM;
            
            alter table part_tbl split partition D1 AT ( 5001 ) INTO ( PARTITION P_0_5000 TABLESPACE USER_DATA_DISK, PARTITION D1 TABLESPACE USER_DATA_MEM);
        
    -   **Actual Results**
    
        비정상 종료
    
-   **Expected Results**
    
        success
    
-   **Workaround**

        alter table part_tbl split partition D1 AT ( 5001 ) INTO ( PARTITION P_0_5000 TABLESPACE USER_DATA_DISK, PARTITION D1);

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47944  Fixed an issue where performing a meta downgrade from metaversion 8.8.1 or 8.7.1 to a lower version fails.

-   **module** : qp-meta

-   **Category** : Functional Error

-   **Reproducibility** : Always

- **Description** : Fixed an issue where performing a meta downgrade from metaversion 8.8.1 or 8.7.1 to a lower version fails.

-   **How to reproduce this bug**

    -   **Reproduction conditions**

            meta downgrade

    -   **Actual Results**

            % is
            -----------------------------------------------------------------
                 Altibase Client Query utility.
                 Release Version 7.1.0.4.0
                 Copyright 2000, ALTIBASE Corporation or its subsidiaries.
                 All Rights Reserved.
            -----------------------------------------------------------------
            ISQL_CONNECTION = TCP, SERVER = localhost, PORT_NO = 3096
            iSQL>  SELECT META_MAJOR_VER, META_MINOR_VER, META_PATCH_VER,
                2  PREV_META_MAJOR_VER, PREV_META_MINOR_VER, PREV_META_PATCH_VER
                3  FROM SYSTEM_.SYS_DATABASE_;
            META_MAJOR_VER META_MINOR_VER META_PATCH_VER PREV_META_MAJOR_VER PREV_META_MINOR_VER 
            -------------------------------------------------------------------------------------------
            PREV_META_PATCH_VER 
            ----------------------
            8           8           1           8           7           
            1           
            1 row selected.
            % quit
            % server stop
            -----------------------------------------------------------------
                 Altibase Client Query utility.
                 Release Version 7.1.0.4.0
                 Copyright 2000, ALTIBASE Corporation or its subsidiaries.
                 All Rights Reserved.
            -----------------------------------------------------------------
            ISQL_CONNECTION = UNIX, SERVER = localhost
            Ok..Shutdown Proceeding....
            TRANSITION TO PHASE : Shutdown Altibase
              [RP] Finalization : PASS
            shutdown immediate success.
            % server downgrade
            -----------------------------------------------------------------
                 Altibase Client Query utility.
                 Release Version 7.1.0.4.0
                 Copyright 2000, ALTIBASE Corporation or its subsidiaries.
                 All Rights Reserved.
            -----------------------------------------------------------------
            ISQL_CONNECTION = UNIX, SERVER = localhost
            [ERR-910FB : Connected to idle instance]
            Connecting to the DB server.. Connected.
            TRANSITION TO PHASE : PROCESS
            TRANSITION TO PHASE : CONTROL
            TRANSITION TO PHASE : META
              [SM] Recovery Phase - 1 : Preparing Database
                                      : Dynamic Memory Version => Parallel Loading
              [SM] Recovery Phase - 2 : Loading Database 
              [SM] Recovery Phase - 3 : Skipping Recovery & Starting Threads...
                                        Refining Disk Table 
              [SM] Refine Memory Table : .................................................................................................................................. [SUCCESS]
              [SM] Rebuilding Indices [Total Count:131] ................................................................................................................................... [SUCCESS]
            TRANSITION TO PHASE : DOWNGRADE
            [FAILURE] Value overflow 
            0001 : INSERT INTO SYS_DATABASE_ VALUES ( 'mydb', '',8, 7, 1,8, 4564593104, 1 )
                                                                           ^         ^
            Startup Failed....
            [ERR-91015 : Communication failure.]

    -   **Expected Results**

            meta downgrade success

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47945  Added Debugging Code for Disk Buffer CheckPoint List Error.

-   **module** : sm-disk-resource

-   **Category** : Fatal

-   **Reproducibility** : Rare

-   **Description** : Added Debugging Code for Disk Buffer CheckPoint List Error.

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

### BUG-47948  Fixed the concurrency problem occurring when executing DROP TABLESPACE for 'memory_tablespace' and querying V$DATABASE simultaneously.

-   **module** : sm-mem-resource

-   **Category** : Fatal

-   **Reproducibility** : Frequence

-   **Description** : Fixed the concurrency problem occurring when executing DROP TABLESPACE for 'memory_tablespace' and querying V$DATABASE simultaneously.
    
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

### BUG-47953 Fixed Server shut down During Corrupt Page Recovery Using DW_BUFFER with USE_DW_BUFFER Enabled.

-   **module** : sm-disk-recovery

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixed Server shut down during Corrupt Page Recovery Using DW_BUFFER with USE_DW_BUFFER Enabled.

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

### BUG-47954  Resolved an issue where the sender would stop when a truncate operation was performed simultaneously in an replication active-active environment.

-   **module** : rp

-   **Category** : Functional Error

-   **Reproducibility** : Frequence

-   **Description** : Resolved an issue where the sender would stop when a truncate operation was performed simultaneously in an replication active-active environment.
    
-   **How to reproduce this bug**

    -   **Reproduction conditions**

            CREATE TABLE T1 ( I1 INTEGER PRIMARY KEY, I2 CHAR(20), I3 VARCHAR(20) )
            PARTITION BY RANGE(I1)
            (
                PARTITION P1 VALUES LESS THAN (10),
                PARTITION P2 VALUES LESS THAN (20),
                PARTITION P3 VALUES LESS THAN (30),
                PARTITION P4 VALUES LESS THAN (40),
                PARTITION def VALUES DEFAULT
            );
            ...
            CREATE REPLICATION REP1 WITH '123.123.123.123', 21300
                FROM SYS.T1 PARTITION P1 TO SYS.T1 PARTITION P1,
                FROM SYS.T2 PARTITION P1 TO SYS.T2 PARTITION P1,
                FROM SYS.T3 PARTITION P1 TO SYS.T3 PARTITION P1,
                FROM SYS.T4 PARTITION P1 TO SYS.T4 PARTITION P1;
            ...
            ALTER REPLICATION REP1 START;
            ALTER REPLICATION REP2 START;
            ALTER REPLICATION REP3 START;
            ALTER REPLICATION REP4 START;
            TRUNCATE TABLE T1;
            TRUNCATE TABLE T2;
            TRUNCATE TABLE T3;
            TRUNCATE TABLE T4;

    -   **Actual Results**

            Sender Does Not Restart Due to Receiver Lock Timeout

    -   **Expected Results**

            Sender will Restart.

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47970  Fixed issue where page latch would not release for inconsistent pages in Disk Index.

-   **module** : sm-disk-index

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed issue where page latch would not release for inconsistent pages in Disk Index.    

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

### BUG-47986  Fixed issue where INNER JOIN on disk tables with OR clause predicate combined with constant filter would incorrectly use the index, causing result errors.

-   **module** : qp

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed issue where INNER JOIN on disk tables with OR clause predicate combined with constant filter would incorrectly use the index, causing result errors.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

        drop table t1;
        drop table t2;
        create table t1 (
        MODULE_CD                                VARCHAR(20) primary key,
        MODULE_NM                                VARCHAR(200)                
        ) tablespace sys_tbs_disk_data;
        insert into t1 (MODULE_CD) values ('OS');
        insert into t1 (MODULE_CD) values('CR');
        insert into t1 (MODULE_CD) values('MP');
        insert into t1 (MODULE_CD) values('BM');
        insert into t1 (MODULE_CD) values('BP');
        insert into t1 (MODULE_CD) values('CI');
        insert into t1 (MODULE_CD) values('CO');
        
        create table t2 (
        MODULE_CD                                VARCHAR(20) ,
        CLASS_CD                                 VARCHAR(20)             
        )tablespace sys_tbs_disk_data;
        insert into t2 (MODULE_CD) values ('OS');
        insert into t2 (MODULE_CD) values('CR');
        insert into t2 (MODULE_CD) values('MP');
        insert into t2 (MODULE_CD) values('BM');
        insert into t2 (MODULE_CD) values('BP');
        insert into t2 (MODULE_CD) values('CI');
        insert into t2 (MODULE_CD) values('CO');
        insert into t2 (MODULE_CD) values('FI');
        insert into t2 (MODULE_CD) values('HR');
        insert into t2 (MODULE_CD) values ('OS');
        insert into t2 (MODULE_CD) values('CR');
        insert into t2 (MODULE_CD) values('MP');
        insert into t2 (MODULE_CD) values('BM');
        insert into t2 (MODULE_CD) values('BP');
        insert into t2 (MODULE_CD) values('CI');
        insert into t2 (MODULE_CD) values('CO');
        insert into t2 (MODULE_CD) values('FI');
        insert into t2 (MODULE_CD) values('HR');
        insert into t2 (MODULE_CD) values ('OS');
        insert into t2 (MODULE_CD) values('CR');
        insert into t2 (MODULE_CD) values('MP');
        insert into t2 (MODULE_CD) values('BM');
        insert into t2 (MODULE_CD) values('BP');
        insert into t2 (MODULE_CD) values('CI');
        insert into t2 (MODULE_CD) values('CO');
        insert into t2 (MODULE_CD) values('FI');
        insert into t2 (MODULE_CD) values('HR');
        
        var FORM varchar(80);
        exec :FORM := NULL;
        PREPARE 
             SELECT /*+ USE_INDEX_NL(cdcm, cmi) */ count(*)
                   FROM t1 CMI
                         INNER JOIN t2 CDCM ON CDCM.MODULE_CD = CMI.MODULE_CD
        WHERE ( :FORM IS NULL OR :FORM = '' OR CMI.MODULE_CD = NULL);

  - **Actual Results**

        COUNT(*)
        -----------------------
        0
        1 row selected.

  -   **Expected Results**

          COUNT(*)
          -----------------------
          21
          1 row selected.

- **Workaround**

      PREPARE 
           SELECT /*+ USE_HASH(t1, t2) */ count(*)
                 FROM t1 CMI
                       INNER JOIN t2 CDCM ON CDCM.MODULE_CD = CMI.MODULE_CD
      WHERE ( :FORM IS NULL OR :FORM = '' OR CMI.MODULE_CD = NULL);

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
| 7.1.0.4.0        | 6.5.1                   | 8.8.1        | 7.1.7               | 7.4.6                        |

> You can check the module version change history in [Version_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.1/Altibase_7_1_Version_Histories.md).

### Compatibility

#### Database binary version

The database binary version has not changed.

> The database binary version indicates the compatibility of database image files and log files. If this version needs to be patched to a different version, the database must be reorganized.

#### Meta Version

Meta version are changed from 8.7.1 to 8.8.1 due to support for SRID interface.

- If there are no GEOMETRY type columns, upgrade and downgrade patches can be performed as before.

- If there are GEOMETRY type columns, there is no issue with the upgrade, but downgrading to meta version 8.7.1 or earlier (7.1.0.3.9 or earlier) is not possible.


> If you want to roll back the patch after patching to a version with a changed meta version, see [Meta Downgrade](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/eng/Installation Guide.md#meta-downgrade).

#### CM protocol Version

The cm protocol version has not changed.

#### Replication protocol Version

Due to the change in the replication protocol version from 7.4.5 to 7.4.6, customers using GEOMETRY columns will not be able to perform replication with earlier versions.

Additionally, with the internal change in the ALA protocol, the following error (BUG-48015) occurs in the 7.1.0.4.0 JDBC Adapter and oraAdapter. This issue will be addressed in the next patch (7.1.0.4.1).

> BUG-48015 Fixed compatibility issue between jdbcAdapter in Altibase 7.1.0.4.0 and earlier versions of Altibase (6.5.1 and below).

### Altibase Server Properties

No properties were added, modified, or deleted.

### Performance Views

No performance views were added, modified, or deleted.

### Meta Tables

#### Added Tables

* [GEOMETRY_COLUMNS](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/SpatialSQL.md#geometry_columns) 

* [SPATIAL_REF_SYS](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/SpatialSQL.md#spatial_ref_sys)

#### Deleted Tables

* STO_COLUMNS_
* STO_DATUMS_
* STO_ELLIPSOIDS_
* STO_GEOCCS_
* STO_GEOGCS_
* STO_GEOMETRY_COLUMNS
* STO_PRIMEMS_
* STO_PROJCS_
* STO_PROJECTIONS_
* STO_SPATIAL_REF_SYS
* STO_SRS_
* STO_USER_COLUMNS_
