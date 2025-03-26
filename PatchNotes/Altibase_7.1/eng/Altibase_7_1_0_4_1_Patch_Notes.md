Altibase 7.1.0.4.1 Patch Notes
==============================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [New Features](#new-features)
  - [BUG-47931 Added support for ST_MakePolygon and ST_Polygon functions.](#bug-47931-added-support-for-st_makepolygon-and-st_polygon-functions)
  - [BUG-47985 Added support for ST_LinestringFromWKB](#bug-47985%C2%A0added-support-for-st_linestringfromwkb)
  - [BUG-48007 Improved performance by changing the method for collecting Not Null column information internally in aexport.](#bug-48007%C2%A0improved-performance-by-changing-the-method-for-collecting-not-null-column-information-internally-in-aexport)
- [Fixed Bugs](#fixed-bugs)
  - [BUG-47888 Improvement in dumptrc](#bug-47888%C2%A0improvement-in-dumptrc)
  - [BUG-47959 Fixed an issue where the server crashes due to incorrect memory reference when executing a PSM with an unspecified precision for the argument.](#bug-47959%C2%A0fixed-an-issue-where-the-server-crashes-due-to-incorrect-memory-reference-when-executing-a-psm-with-an-unspecified-precision-for-the-argument)
  - [BUG-48004  Improved the performance in aexport.](#bug-48004%C2%A0-improved-the-performance-in-aexport)
  - [BUG-48015 Fixed compatibility issue between jdbcAdapter in Altibase 7.1.0.4.0 and earlier versions of Altibase (6.5.1 and below).](#bug-48015%C2%A0fixed-compatibility-issue-between-jdbcadapter-in-altibase-71040-and-earlier-versions-of-altibase-651-and-below)
  - [BUG-48016 Fixed issue where commit was skipped and only called once at the end when data insert failed during array data insertion in iLoader.](#bug-48016%C2%A0fixed-issue-where-commit-was-skipped-and-only-called-once-at-the-end-when-data-insert-failed-during-array-data-insertion-in-iloader)
  - [BUG-48018 Fixed result error when performing LEFT OUTER JOIN on disk table with OR clause combined with constant predicate.](#bug-48018%C2%A0fixed-result-error-when-performing-left-outer-join-on-disk-table-with-or-clause-combined-with-constant-predicate)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [Compatibility](#compatibility)
  - [Altibase Server Properties](#altibase-server-properties)
  - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
------------

### BUG-47931 Added support for ST_MakePolygon and ST_Polygon functions.

- **module** : st

- **Category** : Enhancement

- **Reproducibility** : Always

- **Description** : 

-   **How to reproduce this bug**

    -   **Reproduction conditions**

    -   **Actual Results**

    -   **Expected Results**

- **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47985 Added support for ST_LinestringFromWKB

-   **module** : st-function

-   **Category** : Enhancement

-   **Reproducibility** : Always

- **Description** : Added support for ST_LinestringFromWKB.

- **How to reproduce this bug**

  -   **Reproduction conditions**

          SELECT ASEWKT(ST_LINESTRINGFROMWKB( ASBINARY( geometry'linestring(1 1, 4 1)') , 130)) as geom;

  -   **Actual Results**

  -   **Expected Results**

          GEOM
          ------------------------
          SRID=130;LINESTRING(1 1, 4 1)

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48007 Improved performance by changing the method for collecting Not Null column information internally in aexport.

-   **module** : ux-aexport

-   **Category** : Efficiency

-   **Reproducibility** : Always

-   **Description** : Improved performance by changing the method for collecting Not Null column information internally in aexport.
    
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

### BUG-47888 Improvement in dumptrc

-   **module** : id

-   **Category** : Enhancement

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where a warning message is now shown and the call stack is not printed when the version of the Altibase executable and the dumptrc version are different.
    
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

### BUG-47959 Fixed an issue where the server crashes due to incorrect memory reference when executing a PSM with an unspecified precision for the argument.

-   **module** : qp

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** :  Fixed an issue where the server crashes due to incorrect memory reference when executing a PSM with an unspecified precision for the argument.

- **How to reproduce this bug**

  - **Reproduction conditions**

    -   **Actual Results**
  
  
    -   **Expected Results**
  

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48004  Improved the performance in aexport.

-   **module** : ux-aexport

-   **Category** : Efficiency

-   **Reproducibility** : Always

-   **Description** : Improved the performance in aexport.
    
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

### BUG-48015 Fixed compatibility issue between jdbcAdapter in Altibase 7.1.0.4.0 and earlier versions of Altibase (6.5.1 and below).

-   **module** : rp-jdbcAdapter

-   **Category** : Other

-   **Reproducibility** : Always

-   **Description** : Fixed compatibility issue where the jdbcAdapter in Altibase 7.1.0.4.0, due to the ALA protocol being updated to version 7.4.6, was not compatible with earlier versions of Altibase (6.5.1 and below).    

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

### BUG-48016 Fixed issue where commit was skipped and only called once at the end when data insert failed during array data insertion in iLoader.

-   **module** : ux-iloader

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed issue where commit was skipped and only called once at the end when data insert failed during array data insertion in iLoader.
    
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

### BUG-48018 Fixed result error when performing LEFT OUTER JOIN on disk table with OR clause combined with constant predicate.

-   **module** : qp

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed result error when performing LEFT OUTER JOIN on disk table with OR clause combined with constant predicate.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

        drop table MA_PLANT_MST;
        drop table MA_BIZAREA_MST;
        create table MA_PLANT_MST( 
        COMPANY_CD                               VARCHAR(28)                 NOT NULL,
        PLANT_CD                                 VARCHAR(28)                 NOT NULL,
        PLANT_NM                                 VARCHAR(200)                NOT NULL
        ) tablespace sys_tbs_disk_data;
        alter table MA_PLANT_MST add primary key ( COMPANY_CD, PLANT_CD );
        INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('1000', 'DETAIL_AUTH_NOT_USED', 'TEST');
        INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('1001', 'DETAIL_AUTH_NOT_USED', 'TEST');
        INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('1002', 'DETAIL_AUTH_NOT_USED', 'TEST');
        INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('1003', 'DETAIL_AUTH_NOT_USED', 'TEST');
        INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('1004', 'DETAIL_AUTH_NOT_USED', 'TEST');
        INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('1005', 'DETAIL_AUTH_NOT_USED', 'TEST');
        INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('1006', 'DETAIL_AUTH_NOT_USED', 'TEST');
        INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('1007', 'DETAIL_AUTH_NOT_USED', 'TEST');
        INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('1008', 'DETAIL_AUTH_NOT_USED', 'TEST');
        INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('1009', 'DETAIL_AUTH_NOT_USED', 'TEST');
        INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('1010', 'DETAIL_AUTH_NOT_USED', 'TEST');
        INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('1011', 'DETAIL_AUTH_NOT_USED', 'TEST');
        INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('1012', 'DETAIL_AUTH_NOT_USED', 'TEST');
        INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('1013', 'DETAIL_AUTH_NOT_USED', 'TEST');
        INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('KC_TEST', 'DETAIL_AUTH_NOT_USED1', 'TEST');
        INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('KC_TEST', 'DETAIL_AUTH_NOT_USED2', 'TEST');
        INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('KC_TEST', 'DETAIL_AUTH_NOT_USED3', 'TEST');
        INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('KC_TEST', 'DETAIL_AUTH_NOT_USED4', 'TEST');
        INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('KC_TEST', 'DETAIL_AUTH_NOT_USED5', 'TEST');
        INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('KC_TEST', 'DETAIL_AUTH_NOT_USED6', 'TEST');
        
        create table MA_BIZAREA_MST( 
        COMPANY_CD                               VARCHAR(28)                 NOT NULL,
        PLANT_CD                                 VARCHAR(28)                 NOT NULL,
        PLANT_NM                                 VARCHAR(200)                NOT NULL
        ) tablespace sys_tbs_disk_data;
        var AA varchar(7);
        var BB varchar(1);
        var CC varchar(28);
        exec :AA := 'KC_TEST';
        exec :BB := 'N';
        exec :CC := 'DETAIL_AUTH_NOT_USED';
        PREPARE
        SELECT   *
                        FROM    MA_PLANT_MST MPM
                        LEFT    OUTER JOIN MA_BIZAREA_MST MBM ON MBM.COMPANY_CD = MPM.COMPANY_CD
                        WHERE   MPM.COMPANY_CD = :AA
                        AND             (:BB = 'N' OR MPM.PLANT_CD IN
                         (
                                :CC
                         )
                                        );

  -   **Actual Results**

          No rows selected.

  -   **Expected Results**

          6 rows selected.

-   **Workaround**

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
| 7.1.0.4.1        | 6.5.1                   | 8.8.1        | 7.1.7               | 7.4.6                        |

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

No properties were added, modified, or deleted.

### Performance Views

No performance views were added, modified, or deleted.
