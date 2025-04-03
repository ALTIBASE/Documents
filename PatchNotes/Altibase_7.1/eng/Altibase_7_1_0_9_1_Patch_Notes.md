# Altibase 7.1.0.9.1 Patch Notes

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Fixed Bugs
==========

### BUG-50621<a name=bug-50621></a> Fixed an issue that caused an abnormal server shutdown when creating a function-based index with an expression that exceeded the maximum length.

-   **module** : qp-ddl-dcl-pvo

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Fixed an issue that caused an abnormal server shutdown when creating a function-based index with an expression that exceeded the maximum length.
    
-   #### How to reproduce this bug

    -   **Reproduction conditions**

    -   **Actual Results**
    
    -   **Expected Results**
    
-   **Workaround**

-   **Changes**
    
    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50659<a name=bug-50659></a> Fixed result error when referencing subquery with external SELECT clause in ORDER BY with alias.

-   **module** : qp

-   **Category** : Reliability

-   **Reproducibility** : Always

-   **Description** : Fixed an issue that caused a result error when using an alias to reference a subquery with an external reference in the ORDER BY clause.
    
    This bug only occurs when all of the following four conditions are met:
    
    1. The disk table uses disk temp to perform ORDER BY.
    2. The alias of the subquery is used in the ORDER BY clause.
    3. The SELECT target includes more than one subquery, and one of the subqueries used in the ORDER BY clause contains an external reference column from a subquery that appears earlier in the SELECT.
    4. The external reference column used in the subquery is utilized in an inline view or a regular view in the FROM clause, and it is processed via View Merge optimization.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```sql
    drop table tb1;
    drop table tb2;
    drop table tb3;
    CREATE TABLE TB1 ( TB1_C1 VARCHAR(10) PRIMARY KEY,
                       TB1_C2 VARCHAR(10) NOT NULL,
                       TB1_C3 VARCHAR(10) NOT NULL )
    tablespace sys_tbs_disk_data
    ;
    insert into tb1 values ('aaa','aaa','aaa');
    insert into tb1 values ('bbb','aaa','bbb');
    insert into tb1 values ('ccc','aaa','ccc');
    insert into tb1 values ('ddd','ccc','ddd');
    insert into tb1 values ('eee','eee','eee');
    CREATE TABLE TB2 ( TB2_C1 VARCHAR(10) PRIMARY KEY,
                       TB2_C2 VARCHAR(10) NOT NULL,
                       TB2_C3 VARCHAR(10) NOT NULL,
                       TB2_C4 NUMERIC(5,2),
                       TB2_C5 DATE DEFAULT SYSDATE )
    tablespace sys_tbs_disk_data;
    insert into tb2 values('aaa','aaa','aaa',1,sysdate);
    insert into tb2 values('bbb','aaa','bbb',1,sysdate);
    insert into tb2 values('ccc','bbb','ccc',1,sysdate);
    insert into tb2 values('eee','eee','eee',1,sysdate);
    insert into tb2 values('fff','eee','fff',1,sysdate);
    CREATE TABLE Tb3 ( TB3_C1 VARCHAR(10) PRIMARY KEY,
                      TB3_C2 VARCHAR(10) NOT NULL )
    tablespace sys_tbs_disk_data;
    insert into tb3 values ( 'aaa','aaa' );
    insert into tb3 values ( 'bbb','bbb' );
    insert into tb3 values ( 'ccc','ccc' );
    insert into tb3 values ( 'fff','fff' );
    SELECT 
     (SELECT X.TB1_C3 FROM TB1 X WHERE X.TB1_C1 = A.TB2_C1)
    ,(SELECT X.TB1_C2 FROM TB1 X WHERE X.TB1_C1 = A.TB2_C1)  AS AAAA
    FROM TB2 A
    WHERE EXISTS (SELECT  1 FROM TB3 X WHERE X.TB3_C2 = A.TB2_C1 )
    ORDER BY AAAA ASC;
    ```

  - **Actual Results**

    ```sql
    aaa
    ccc
    bbb
    4 rows selected.
    ```

  -   **Expected Results**

      ```sql
      aaa         aaa
      ccc         aaa
      bbb         aaa
      4 rows selected.
      ```

- **Workaround**

  ```sql
  SELECT 
   (SELECT X.TB1_C3 FROM TB1 X WHERE X.TB1_C1 = A.TB2_C1)
  ,(SELECT X.TB1_C2 FROM TB1 X WHERE X.TB1_C1 = A.TB2_C1)  AS AAAA
  FROM TB2 A
  WHERE EXISTS (SELECT /*+ no_unnest */ 1 FROM TB3 X WHERE X.TB3_C2 = A.TB2_C1 )
  ORDER BY AAAA ASC;
  ```

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50663<a name=bug-50663></a> Fixed concurrency issues with functions in LobCursorList

-   **module** : sm

-   **Category** : Fatal

-   **Reproducibility** : Unknown

-   **Description** : Fixed concurrency issues with functions in LobCursorList.

-   #### How to reproduce this bug

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
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 7.1.0.9.1        | 6.5.1                   | 8.11.1       | 7.1.7               | 7.4.7                        |

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

#### Added Properties

#### Changed Properties

#### Deleted Properties

### Performance Views

#### Added Performance Views

#### Changed Performance Views

#### Deleted Performance Views
