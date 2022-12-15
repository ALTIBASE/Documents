Altibase 7.1.0.7.7 Patch Notes
==============================

<br/>

<br/>

# Table of Contents

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Fixed Bugs](#fixed-bugs)
    - [BUG-49746 If disk temporary space is used in a query statement using a window (analysis) function, ORDER BY clause, or GROUP BY clause, the result is an error.](#bug-49746if-disk-temporary-space-is-used-in-a-query-statement-using-a-window-analysis-function-order-by-clause-or-group-by-clause-the-result-is-an-error)
    - [BUG-49756 [ERR-31074: Unable to insert (or update) NULL into NOT NULL column.] error occurs when the EMPTY_CLOB() or EMPTY_BLOB() function is used for a LOB column that has a NOT NULL constraint in the values clause of an INSERT statement.](#bug-49756err-31074-unable-to-insert-or-update-null-into-not-null-column-error-occurs-when-the-empty_clob-or-empty_blob-function-is-used-for-a-lob-column-that-has-a-not-null-constraint-in-the-values-clause-of-an-insert-statement)
    - [BUG-49767 [ERR-2105A: The pattern contains an invalid range.] error occurs when using Korean in the regular expression in the REGEXP_LIKE function. Add regular expression method using PCRE2 library to support Korean search.](#bug-49767err-2105a-the-pattern-contains-an-invalid-range-error-occurs-when-using-korean-in-the-regular-expression-in-the-regexp_like-function-add-regular-expression-method-using-pcre2-library-to-support-korean-search)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [Altibase Server Properties](#altibase-server-properties)
    - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

<br/>

Fixed Bugs
==========

### BUG-49746 If disk temporary space is used in a query statement using a window (analysis) function, ORDER BY clause, or GROUP BY clause, the result is an error.

-   **module** : qp-select

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : An error occurs when executing a query that satisfies all of the conditions below.
    
    - Using the window (analysis) function
    
    - Using GROUP BY clause, ORDER BY clause, window (analysis) function
    
    - Columns used in the ORDER BY clause are used in the same order in the OVER clause of the window (analysis) function
    
    - Columns used in the ORDER BY clause are used as expressions in the SELECT clause

    - Use of disk temporary space when performing queries

    Check out the Work Around section on how to work around this bug.

    **Precautions when patching**

    This is a bug that has improved the result value error, and the result may be different when executing a query that satisfies the bug condition after patching.

-   **How to reproduce this bug**

    -   **Reproduction conditions**

        ```sql
        DROP TABLE T1;
        
        CREATE TABLE T1 ( I1 CHAR(8), I2 FLOAT ) TABLESPACE SYS_TBS_DISK_DATA;
        INSERT INTO T1 VALUES ('20220127', 0);
        INSERT INTO T1 VALUES ('20220127', 1);
        INSERT INTO T1 VALUES ('20220127', 2);
        INSERT INTO T1 VALUES ('20220126', 10);
        INSERT INTO T1 VALUES ('20220126', 15);
        INSERT INTO T1 VALUES ('20220125', 30);
        
        SELECT ROW_NUMBER() OVER(ORDER BY A.I1 DESC) RNUM
             , TO_CHAR(TO_DATE(A.I1, 'YYYYMMDD'), 'YYYY-MM-DD') AS YYYYMMDD
             , SUM(A.I2) AS CNT
          FROM T1 A
         GROUP BY A.I
         ORDER BY A.I1 DESC;
        ```

    -   **Actual Results**

        ```sql
        RNUM                 YYYYMMDD              CNT         
        -----------------------------------------------------------
        1                    2022-01-25            3           
        2                    2022-01-25            25          
        3                    2022-01-25            30          
        3 rows selected.
        ```

    -   **Expected Results**

        ```sql
        RNUM                 YYYYMMDD              CNT         
        -----------------------------------------------------------
        1                    2022-01-27            3           
        2                    2022-01-26            25          
        3                    2022-01-25            30          
        3 rows selected.
        ```

-   **Workaround**

    This bug can be avoided with the TEMP_TBS_MEMORY hint.

    ```sql
    SELECT /*+ TEMP_TBS_MEMORY */ ROW_NUMBER() OVER(ORDER BY A.I1 DESC) RNUM
         , TO_CHAR(TO_DATE(A.I1, 'YYYYMMDD'), 'YYYY-MM-DD') AS YYYYMMDD
         , SUM(A.I2) AS CNT
      FROM T1 A
     GROUP BY A.I
     ORDER BY A.I1 DESC;
    ```
    
-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49756 [ERR-31074: Unable to insert (or update) NULL into NOT NULL column.] error occurs when the EMPTY_CLOB() or EMPTY_BLOB() function is used for a LOB column that has a NOT NULL constraint in the values clause of an INSERT statement.

-   **module** : qp-dml-execute

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : [ERR-31074: Unable to insert (or update) NULL into NOT NULL column.] error occurs when the EMPTY_CLOB() or EMPTY_BLOB() function is used for a LOB column that has a NOT NULL constraint in the values clause of an INSERT statement. This bug has been fixed.
    
-   **How to reproduce this bug**

    -   **Reproduction conditions**

            CREATE TABLE t1(c1 CLOB NOT NULL);INSERT INTO t1 VALUES(EMPTY_CLOB());

    -   **Actual Results**

            [ERR-31074 : Unable to insert (or update) NULL into NOT NULL column. : C1]

    -   **Expected Results**

            1 row inserted.

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49767 [ERR-2105A: The pattern contains an invalid range.] error occurs when using Korean in the regular expression in the REGEXP_LIKE function. Add regular expression method using PCRE2 library to support Korean search.

-   **module** : qp

-   **Category** : Functionality

-   **Reproducibility** : Always

-   **Description** : Adds regular expression methods using the Perl Compatible Regular Expressions (PCRE2) library. It is possible to search in Korean, which is not supported by the existing regular expression processing method, and the following search function has been added.
    
    - Backreference

    - Lookahead

    - Lookbehind

    - Conditional pattern

    - Character with the xx property

    To use regular expressions from the PCRE2 library, you need to change the value of the REGEXP_MODE property to 1. For the description of the property, please refer to the property section. 
    
    There are syntax differences in some functions from Altibase's existing regular expression library.
    
    The version of the PCRE2 library used in Altibase is 10.40. For more information about the PCRE2 library, see the [PCRE2 home page](https://www.pcre.org/).
    
-   **How to reproduce this bug**

    -   **Reproduction conditions**

    -   **Actual Results**

    -   **Expected Results**

-   **Workaround**

-   **Changes**

    -   Performance view
    
    -   Property
        
        An Altibase server property that sets the regular expression processing method has been added.
    
        - **Property name**
          REGEXP_MODE
        
        - **Description**
          
          This property sets the regular expression processing method.
          
          - 0
          
            Altibase regular expression library that partially supports POSIX Basic Regular Expression (BRE) and Extended Regular Expression (ERE)
          
    
          - 1
          
            Perl Compatible Regular Expressions (PCRE2) library. Altibase server character set supports only US7ASCII or UTF-8.
          
        - **Default**
          0
        
        - **Attributes**
          Read-Write, Single value
        
    -   Compile Option
    
    -   Error Code
        
        ```
        0x2106B ( 135275) mtERR_ABORT_PCRE2_NOT_SUPPORTED_ENCODING Unsupported character set by PCRE2 library 
        # *Cause : The current session processes regular expression using the PCRE2 library. In this case, the Altibase server character set must be a character set supported by the PCRE2 library.
        # *Action :
        # - Check the character sets supported by the PCRE2 library in functions section in SQL Reference.
        # - Check the Altibase server character set.
        # - If the Altibase server character set is not supported by the PCRE2 library, change the value of the REGEXP_MODE property to 0.
        # - To process the regular expression using the PCRE2 library, Altibase server has to change its character set to another one that is supported by PCRE2 library. This requires recreating database.
        ```
        
        ```
        0x2106C ( 135276) mtERR_ABORT_PCRE2_UNEXPECTED_ERROR PCRE2 error: <1%s> (occurred in <0%s>) 
        # *Cause: An internal error occurred in PCRE2 library or while executing Altibase internal function.
        # *Action: Check the error message and contact Altibase's Support Center (http://support.altibase.com).
        ```
        



Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    7.1.0.7.7     |          6.5.1          |    8.10.1    |        7.1.7        |            7.4.7             |

> You can check the module version change history in [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.1/Altibase_7_1_Version_Histories.md).

#### Compatibility

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

#### Added Properties

- REGEXP_MODE

#### Changed Properties

#### Deleted Properties

### Performance Views

#### Added Performance Views

#### Changed Performance Views

#### Deleted Performance Views
