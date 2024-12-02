# Altibase 7.1.0.9.5 Patch Notes

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Fixed Bugs](#fixed-bugs)
    - [BUG-50775 Fix an issue where execute processing is aborted if the result of SQLExecute() is SQL_NO_DATA when performing a Multiple Statement query.](#bug-50775)
    - [BUG-50782 Fix an issue where Name-based Binding did not work in Multiple Statement.](#bug-50782)
    - [BUG-50784 Address security vulnerabilities in CWE-114 and CWE-73](#bug-50784)
    - [BUG-50798 Fix an error in allocating the page control header (PCH) internally when a checkpoint image file was added during MEDIA RECOVERY.](#bug-50798)
    - [BUG-50803 Fix an issue where altibase_boot.log printed an incorrect errno.](#bug-50803)
    - [BUG-50804 Fix an issue where Session Time Failover (STF) did not work if the server connection was lost when AltibaseStatement.close() was called.](#bug-50804)
    - [BUG-50817 Change from holding an X Lock(Exclusive Lock) on the table to an IX Lock (Intent Exclusive Lock) when executing AGING statement on a disk table or disk index.](#bug-50817)
    - [BUG-50826 Fix an issue where the CLI function SQLPrimaryKeys() outputted the wrong name for the second column of the result.](#bug-50826)
    - [BUG-50840 Fix an error where pages were not allocated internally when a checkpoint image file was added during MEDIA RECOVERY.](#bug-50840)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [Compatibility](#Compatibility)
    - [Altibase Server Properties](#Altibase-Server-Properties)
    - [Performance Views](#Performance-Views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Fixed Bugs
==========

### BUG-50775<a name=bug-50775></a> Fix an issue where execute processing is aborted if the result of SQLExecute() is SQL_NO_DATA when performing a Multiple Statement query.

-   **module** : mm-cli
-   **Category** : Functional Error
-   **Reproducibility** : Always
-   **Description** : Altibase fixed to prevent execute processing from being aborted when the result of SQLExecute() is SQL_NO_DATA when executing a Multiple Statement query.
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

### BUG-50782<a name=bug-50782></a> Fix an issue where Name-based Binding did not work in Multiple Statement.

-   **module** : mm-cli

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Altibase fixed an issue where Name-based binding did not work correctly when binding multiple parameters in multiple statements.
    
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

### BUG-50784<a name=bug-50784></a> Address security vulnerabilities in CWE-114 and CWE-73.

-   **module** : mm-jdbc

-   **Category** : Security

-   **Reproducibility** : Always

-   **Description** : Altibase fixed security vulnerabilities in CWE-114 and CWE-73 detected in Veracode. The JDBC driver must be patched for this bug.

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

### BUG-50798<a name=bug-50798></a> Fix an error in allocating the page control header (PCH) internally when a checkpoint image file was added during MEDIA RECOVERY.

-   **module** : sm

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Altibase fixed an error in allocating the page control header (PCH) internally when a checkpoint image file was added during MEDIA RECOVERY.

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

### BUG-50803<a name=bug-50803></a> Fix an issue where altibase_boot.log printed an incorrect errno.

-   **module** : cm

-   **Category** : Other

-   **Reproducibility** : Always

-   **Description** : Altibase fixed an issue where the error number was output to altibase_boot.log with a "d" character after the error number, such as "errno=22d".
    
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

### BUG-50804<a name=bug-50804></a> Fix an issue where Session Time Failover (STF) did not work if the server connection was lost when AltibaseStatement.close() was called.

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Altibase fixed an issue where Session Time Failover (STF) did not work if the server connection was lost when AltibaseStatement.close() was called, resulting in a sockets error.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```java
    // stf=on
    try
    {
        sStmt = sCon.prepareStatement("SELECT 1 FROM dual");
        sRes = sStmt.executeQuery();
        if ( sRes.next() )
        {
            System.out.println( "VALUE : " + sRes.getString(1) );
        }
        // ==> Server connection is lost at this point
        sStmt.close();
    }
    catch ( SQLException e )
    {
        if (e.getErrorCode() == ErrorDef.FAILOVER_SUCCESS)
        {
            System.out.println( "SUCCESS" );
        }
        else 
        {
        System.out.println("FAIL";
        }
    }
    ```

  -   **Actual Results**

          FAIL

  -   **Expected Results**

          SUCCESS

-   **Workaround**

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50817<a name=bug-50817></a> Change from holding an X Lock(Exclusive Lock) on the table to an IX Lock (Intent Exclusive Lock) when executing AGING statement on a disk table or disk index.

-   **module** : sm
-   **Category** : Other
-   **Reproducibility** : Always
-   **Description** : Altibase changed from holding an X Lock(Exclusive Lock) on the table to an IX Lock (Intent Exclusive Lock) when executing AGING statement on a disk table or disk. This change solved an issue where an X Lock would cause a timeout while waiting for a transaction when performing AGING on a disk table or disk index to update page information.
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

### BUG-50826<a name=bug-50826></a> Fix an issue where the CLI function SQLPrimaryKeys() outputted the wrong name for the second column of the result.

-   **module** : mm-cli

-   **Category** : Functional Error

-   **Reproducibility** : Always

-   **Description** : Altiabse fixed an issue where the name of the second column of the result of the SQLPrimaryKeys() function was output as TABLE_CAT, which should be output as TABLE_SCHEM.
    
- **How to reproduce this bug**

  - **Reproduction conditions**

    ```java
    iSQL> CREATE TABLE ODBCTESTS (ID INTEGER PRIMARY KEY, NAME VARCHAR(24), AGE INTEGER);
    
    ....
        if( SQLPrimaryKeys( stmt,
                            NULL,
                            0,
                            NULL,
                            0,
                            (SQLCHAR*) "ODBCTESTS",
                            SQL_NTS ) != SQL_SUCCESS )
        {
            printf( "Error : SQLPrimaryKeys()\n" );
            exit(-1);
        }
        else
        {
            printf("RUN SQLPrimaryKeys : SUCCESS\n");
        }
        ...
        while( SQLFetch(stmt) == SQL_SUCCESS )
        {
            sRecCnt++;
            if ( sRecCnt > 2 )
            {
                break;
            }
            printf( "=============================================\n" );
            printf( "= %d-th Record\n", sRecCnt );
            printf( "=============================================\n" );
            // To Remove DIFF by INDEX_ID
            for ( i = 0; i < sColCnt -1; i++ )
            {
                if ( SQLGetData( stmt,
                                 i + 1,
                                 SQL_C_CHAR,
                                 & sData[i],
                                 32,
                                 & sDataLen ) != SQL_SUCCESS )
                {
                    printf( "Error : SQLGetData(%d)\n", i );
                    exit(-1);
                }
                else
                {
                    printf( "COLUMN #%d\n"
                            "   ColName = %s\n"
                            "   ColType = %d\n"
                            "   Value   = %s\n",
                            i+1, sColName[i], sColType[i], sData[i] );
                }
            }
        }
    ```

  - **Actual Results**

    ```java
    COLUMN #1
       ColName = TABLE_CAT
       ColType = 12
       Value   = mydb
    COLUMN #2
       ColName = TABLE_CAT
       ColType = 12
       Value   = SYS
    COLUMN #3
       ColName = TABLE_NAME
       ColType = 12
       Value   = ODBCTESTS
    COLUMN #4
       ColName = COLUMN_NAME
       ColType = 12
       Value   = ID
    COLUMN #5
       ColName = KEY_SEQ
       ColType = 5
       Value   = 1
    COLUMN #6
       ColName = PK_NAME
       ColType = 12
       Value   = __SYS_CON_PRIMARY_ID_202
    ```

  -   **Expected Results**

      ```java
      COLUMN #1
         ColName = TABLE_CAT
         ColType = 12
         Value   = mydb
      COLUMN #2
         ColName = TABLE_SCHEM
         ColType = 12
         Value   = SYS
      COLUMN #3
         ColName = TABLE_NAME
         ColType = 12
         Value   = ODBCTESTS
      COLUMN #4
         ColName = COLUMN_NAME
         ColType = 12
         Value   = ID
      COLUMN #5
         ColName = KEY_SEQ
         ColType = 5
         Value   = 1
      COLUMN #6
         ColName = PK_NAME
         ColType = 12
         Value   = __SYS_CON_PRIMARY_ID_202
      ```

-   **Workaround**

        Inquiry in column order

-   **Changes**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50840<a name=bug-50840></a> Fix an error where pages were not allocated internally when a checkpoint image file was added during MEDIA RECOVERY.

-   **module** : sm

-   **Category** : Fatal

-   **Reproducibility** : Always

-   **Description** : Altibase fixed an issue where the page was sometimes not allocated internally when a checkpoint image file was added during MEDIA RECOVERY.

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
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 7.1.0.9.5        | 6.5.1                   | 8.11.1       | 7.1.7               | 7.4.7                        |

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
