Altibase 7.1.0.4.3 Patch Notes
==============================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [New Features](#new-features)
  - [BUG-48038  Added support for the ST_IsCollection function.](#bug-48038%C2%A0-added-support-for-the-st_iscollection-function)
  - [BUG-48052  Reduced preparation time for Subquery Unnesting.](#bug-48052%C2%A0-reduced-preparation-time-for-subquery-unnesting)
- [Fixed Bugs](#fixed-bugs)
  - [BUG-47902  Fixed an issue where replication start fails when the number of items is the same, but the table structure is different, while running in SQL APPLY mode.](#bug-47902%C2%A0-fixed-an-issue-where-replication-start-fails-when-the-number-of-items-is-the-same-but-the-table-structure-is-different-while-running-in-sql-apply-mode)
  - [BUG-47924 Fixed an issue where multiple CREATE INDEX DDL statements appeared for a local partitioned index with multiple partitions in aexport](#bug-47924%C2%A0fixed-an-issue-where-multiple-create-index-ddl-statements-appeared-for-a-local-partitioned-index-with-multiple-partitions-in-aexport)
  - [BUG-48000 Fixed an issue where [ERR-91145 : Unable to open altibase.properties file.] occurred after setting an incorrect property and performing server stop or server kill.](#bug-48000%C2%A0fixed-an-issue-where-err-91145--unable-to-open-altibaseproperties-file-occurred-after-setting-an-incorrect-property-and-performing-server-stop-or-server-kill)
  - [BUG-48022 Fixed an issue where the server would crash during simultaneous operations by multiple clients when a queue was created with Disk Tablespace.](#bug-48022-fixed-an-issue-where-the-server-would-crash-during-simultaneous-operations-by-multiple-clients-when-a-queue-was-created-with-disk-tablespace)
  - [BUG-48051 Fixed an issue where using the `asbinary` function on records inserted with the `geomFromWkb` function caused incorrect behavior.](#bug-48051-fixed-an-issue-where-using-the-asbinary-function-on-records-inserted-with-the-geomfromwkb-function-caused-incorrect-behavior)
  - [BUG-46427 Fixed an issue where improper adjustment of properties responsible for distributing pages for temp tables in disk sort temp could result in an insufficient allocation of pages, making the operation impossible. Now, it ensures the allocation of the minimum required pages.](#bug-46427%C2%A0fixed-an-issue-where-improper-adjustment-of-properties-responsible-for-distributing-pages-for-temp-tables-in-disk-sort-temp-could-result-in-an-insufficient-allocation-of-pages-making-the-operation-impossible-now-it-ensures-the-allocation-of-the-minimum-required-pages)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [Compatibility](#compatibility)
  - [Altibase Server Properties](#altibase-server-properties)
  - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
------------

### BUG-48038  Added support for the ST_IsCollection function.

-   **module** : st

-   **Category** : Enhancement

-   **Reproducibility** : Always

- **Description** : Added support for the ST_IsCollection function.

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

### BUG-48052  Reduced preparation time for Subquery Unnesting.

-   **module** : qp-dml-pvo

-   **Category** : Enhancement

-   **Reproducibility** : Always

-   **Description** : Reduced preparation time for Subquery Unnesting.

-   **How to reproduce this bug**

    -   **Reproduction conditions**

    -   **Actual Results**

    -   **Expected Results**

-   **Workaround**

        alter system set OPTIMIZER_UNNEST_SUBQUERY=0

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

Fixed Bugs
----------

### BUG-47902  Fixed an issue where replication start fails when the number of items is the same, but the table structure is different, while running in SQL APPLY mode.

-   **module** : rp

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where replication start fails when the number of items is the same, but the table structure is different, while running in SQL APPLY mode.

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

### BUG-47924 Fixed an issue where multiple CREATE INDEX DDL statements appeared for a local partitioned index with multiple partitions in aexport

-   **module** : ux-aexport

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where multiple CREATE INDEX DDL statements appeared for a local partitioned index with multiple partitions in aexport
    
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

### BUG-48000 Fixed an issue where [ERR-91145 : Unable to open altibase.properties file.] occurred after setting an incorrect property and performing server stop or server kill.

-   **module** : ux-isql

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where [ERR-91145 : Unable to open altibase.properties file.] occurred after setting an incorrect property and performing server stop or server kill.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

        % export ALTIBASE_ISOLATION_LEVEL=3
        % server start

  - **Actual Results**

        % server start
        -----------------------------------------------------------------
             Altibase Client Query utility.
             Release Version 7.1.0.4.3
             Copyright 2000, ALTIBASE Corporation or its subsidiaries.
             All Rights Reserved.
        -----------------------------------------------------------------
        ISQL_CONNECTION = UNIX, SERVER = localhost
        [ERR-91145 : Unable to open altibase.properties file.]

  -   **Expected Results**

          % server start
          -----------------------------------------------------------------
               Altibase Client Query utility.
               Release Version 7.1.0.4.3
               Copyright 2000, ALTIBASE Corporation or its subsidiaries.
               All Rights Reserved.
          -----------------------------------------------------------------
          ISQL_CONNECTION = UNIX, SERVER = localhost
          idp checkRange() Error : Property [ISOLATION_LEVEL] 3 Overflowed the Value Range.(0~2)
          [ERR-50032 : Client unable to establish connection. (Failed to invoke the connect() system function, errno=111)]

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48022 Fixed an issue where the server would crash during simultaneous operations by multiple clients when a queue was created with Disk Tablespace.

-   **module** : sm-disk-index

-   **Category** : Fatal

-   **Reproducibility** : Frequence

-   **Description** : Fixed an issue where the server would crash during simultaneous operations by multiple clients when a queue was created with Disk Tablespace.

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

### BUG-48051 Fixed an issue where using the `asbinary` function on records inserted with the `geomFromWkb` function caused incorrect behavior.

-   **module** : st-function

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where using the `asbinary` function on records inserted with the `geomFromWkb` function caused incorrect behavior.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

        create table test( obj geometry );
        
        -- MULTIPOLYGON(((8 6,22 4,38 14,34 36,22 46,17 44,22 28,16 22,8 28,2 27,4 26)),((4 35,8 31,14 41,14 53,10 55,8 45,4 43,4 35))) 에 대한 WKB
        insert into TEST values ( geomFromWkb( BINARY'0106000000020000000103000000010000000b000000000000000000204000000000000018400000000000003640000000000000104000000000000043400000000000002c4000000000000041400000000000004240000000000000364000000000000047400000000000003140000000000000464000000000000036400000000000003c400000000000003040000000000000364000000000000020400000000000003c4000000000000000400000000000003b4000000000000010400000000000003a40010300000001000000080000000000000000001040000000000080414000000000000020400000000000003f400000000000002c4000000000008044400000000000002c400000000000804a4000000000000024400000000000804b40000000000000204000000000008046400000000000001040000000000080454000000000000010400000000000804140' ) );
        
        select astext(geomfromwkb( asbinary(obj) ) ) from test;

  - **Actual Results**

        -- linux 
        select astext(geomfromwkb( asbinary(obj) ) ) from test;
        ASTEXT(GEOMFROMWKB( ASBINARY(OBJ) ) )
        --------------------------------------------------------------------------------------------------------
        MULTIPOLYGON(((8 6, 22 4, 38 14, 34 36, 22 46, 17 44, 22 28, 16 22, 8 28, 2 27, 4 26, 0 4, 0 NAN)),
        ())
        1 row selected.
        
        -- aix 
        비정상 종료

  -   **Expected Results**

          MULTIPOLYGON(((8 6,22 4,38 14,34 36,22 46,17 44,22 28,16 22,8 28,2 27,4 26)),((4 35,8 31,14 41,14 53,10 55,8 45,4 43,4 35)))
          1 row selected.

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code
        -   83, stERR\_ABORT\_INVALID\_GEOMETRY\_MADEBY\_GEOMFROMWKB =
            Invalid Geometry(\<0%s\>)\
            \
            \# \*Cause: An attempt was made to perform an operation on
            an invalid geometry.\
            \
            \# \*Action: Check the error number from the trace log and
            contact Altibase’s Support Center
            (http://support.altibase.com).

### BUG-46427 Fixed an issue where improper adjustment of properties responsible for distributing pages for temp tables in disk sort temp could result in an insufficient allocation of pages, making the operation impossible. Now, it ensures the allocation of the minimum required pages.

-   **module** : sm-disk-resource

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an issue where improper adjustment of properties responsible for distributing pages for temp tables in disk sort temp could result in an insufficient allocation of pages, making the operation impossible. Now, it ensures the allocation of the minimum required pages.

- **How to reproduce this bug**

  - **Reproduction conditions**

    ```
    ALTER SYSTEM SET QUERY_TIMEOUT = 0;
    ALTER SYSTEM SET DDL_TIMEOUT = 0;
    ALTER SYSTEM SET FETCH_TIMEOUT = 0;
    ALTER SYSTEM SET UTRANS_TIMEOUT = 0;
    ALTER SYSTEM SET IDLE_TIMEOUT = 0;
    ALTER SYSTEM SET TEMP_SORT_GROUP_RATIO=90;
    ALTER SYSTEM SET SORT_AREA_SIZE=524288;
    CREATE TABLE T1 ( I1 CHAR(1000), I2 CHAR(2000) ) tablespace
    sys_tbs_disk_data;
    CREATE TABLE T2 ( I1 CHAR(1000), I2 CHAR(2000) ) tablespace
    sys_tbs_disk_data;
    INSERT /*+APPEND*/ INTO T1 SELECT ROWNUM/5,ROWNUM
    FROM DUAL CONNECT BY LEVEL <= 300;
    INSERT /*+APPEND*/ INTO T2 SELECT
    ROWNUM/5+1,ROWNUM+1 FROM DUAL CONNECT BY LEVEL <=
    300;
    select count(I1) from ( SELECT I1,I2, SUM(I1) OVER ( PARTITION BY
    I1, I2), SUM(I2) OVER ( PARTITION BY I1, I2), SUM(I1) OVER
    ( PARTITION BY I2) , SUM(I1) OVER ( PARTITION BY I1) FROM T1
    ORDER BY I1,i2 );
    ```

  - 결과**

    ```
    [ERR-11069 : Internal server error in the storage manager
    ([FAILURE] ERR-0109E(error=16) Internal server error.)]
    ```

  - **Expected Results**

    ```
    COUNT( I1 )
    -----------------------
    300
    1 row selected.
    ```

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
| 7.1.0.4.3        | 6.5.1                   | 8.8.1        | 7.1.7               | 7.4.6                        |

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
