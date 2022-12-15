Altibase 7.1.0.7.1 Patch Notes
==============================

<br/>

<br/>

# Table of Contents 

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [New Features](#new-features)
    - [BUG-49617 Adds a property to configure LOB data type support to Adapter for JDBC and Adapter for Oracle.](#bug-49617adds-a-property-to-configure-lob-data-type-support-to-adapter-for-jdbc-and-adapter-for-oracle)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-49610 If you used FF# as the date type data type in the TO_DATE function, it accepts fewer digits than #.](#bug-49610if-you-used-ff-as-the-date-type-data-type-in-the-to_date-function-it-accepts-fewer-digits-than-)
    - [BUG-49625 The TO_DATE function returns incorrect results when SSSSSS is used as the date data type.](#bug-49625the-to_date-function-returns-incorrect-results-when-ssssss-is-used-as-the-date-data-type)
    - [BUG-49630 Disable the Table OID reuse feature.](#bug-49630disable-the-table-oid-reuse-feature)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [Altibase Server Properties](#altibase-server-properties)
    - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# New Features

### BUG-49617 Adds a property to configure LOB data type support to Adapter for JDBC and Adapter for Oracle.
-   **module** : rp-jdbcAdapter, rp-oraAdapter

-   **Category** : Usability

-   **Reproducibility** : Always

-   **Description** :  Adds a property to configure LOB data type support to Adapter for JDBC and Adapter for Oracle.
    
    - ADAPTER_LOB_TYPE_SUPPORT
      This property configures whether LOB data types are supported.
      
      - 0: LOB data type is not supported. (default)
      
      - 1: LOB data type is supported.
      
        Added ADAPTER_LOB_TYPE_SUPPORT = 0 to the last line of jdbcAdapter.conf and oraAdapter.conf files. To use the LOB data type support function, ADAPTER must be restarted after changing the value to 1.
    
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

#  Fixed Bugs

### BUG-49610 If you used FF# as the date type data type in the TO_DATE function, it accepts fewer digits than #.

-   **module** : mt

-   **Category** : Functionality

-   **Reproducibility** : Always

-   **Description** : If you used FF# as the date type data type in the TO_DATE function, it accepts fewer digits than #.
    
    If FF6, a number of 6 digits or less is allowed. (=FF)
    
    If FF5, a number of 5 digits or less is allowed.
    
    If FF4, a number of 4 digits or less is allowed.
    
    If FF3, a number of 3 digits or less is allowed.
    
    If FF2, a number of 2 digits or less is allowed.
    
    If FF1, a number of 1 digits or less is allowed.
    
-   **How to reproduce this bug**

    -   **Reproduction conditions**

        ```sql
        ALTER SESSION SET DEFAULT_DATE_FORMAT = 'YYYY-MM-DD HH:MI:SS:SSSSSS';
        SELECT TO_DATE('2022-02-06 13:26:41.51001', 'yyyy-MM-dd hh24:mi:ss.ff6') FROM DUAL;
        ```

    -   **Actual Results**

        ```sql
        [ERR-21038 : Literals in the input do not match the format string.]
        ```

    -   **Expected Results**

        ```sql
        2022-02-06 13:26:41:510010
        ```

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49625 The TO_DATE function returns incorrect results when SSSSSS is used as the date data type.

-   **module** : mt

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Fixed an error that returned incorrect results when SSSSSS was used as the date data type in the TO_DATE function.
    
-   **How to reproduce this bug**

    -   **Reproduction conditions**

        ```sql
        ALTER SESSION SET DEFAULT_DATE_FORMAT = 'YYYY-MM-DD HH:MI:SS:SSSSSS';
        DROP TABLE T1 CASCADE;
        CREATE TABLE T1 (C1 VARCHAR(30), C2 DATE);
        INSERT INTO T1 VALUES('2022-01-11 02:17:39.958', TO_DATE('2022-01-11 02:17:39.958', 'YYYY-MM-DD HH:MI:SS.SSSSSS'));
        SELECT C1, TO_CHAR(C2, 'YYYY-MM-DD HH24:MI:SS.FF3') FROM T1;
        ```

    -   **Actual Results**

        ```sql
        iSQL> SELECT C1, TO_CHAR(C2, 'YYYY-MM-DD HH24:MI:SS.FF3') FROM T1;
        C1                              TO_CHAR(C2,'YYYY-MM-DDHH24:MI:SS.FF3')
        -------------------------------------------------------------------------
        2022-01-11 02:17:39.958         2022-01-11 02:17:39.000
        1 row selected.
        ```

    -   **Expected Results**

        ```sql
        iSQL> SELECT C1, TO_CHAR(C2, 'YYYY-MM-DD HH24:MI:SS.FF3') FROM T1;
        C1                              TO_CHAR(C2,'YYYY-MM-DDHH24:MI:SS.FF3')
        -------------------------------------------------------------------------
        2022-01-11 02:17:39.958         2022-01-11 02:17:39.958
        1 row selected.
        ```

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49630 Disable the Table OID reuse feature.

-   **module** : sm

-   **Category** : Other

-   **Reproducibility** : Always

-   **Description** : Disable the Table OID reuse feature.

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

Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    7.1.0.7.1     |          6.5.1          |    8.10.1    |        7.1.7        |            7.4.7             |

> You can check the module version change history in [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7_1_Version_Histories.md).

#### Compatibility

#### Database binary version

The database binary version has not changed.


#### Meta Version

The meta version has not changed.

#### CM protocol Version

The cm protocol version has not changed.

#### Replication protocol Version

The replication protocol version has not changed.

### Altibase Server Properties

#### Added Properties

#### Changed Properties

#### Deleted Properties

### Performance Views

#### Added Performance Views

#### Changed Performance Views

#### Deleted Performance Views
