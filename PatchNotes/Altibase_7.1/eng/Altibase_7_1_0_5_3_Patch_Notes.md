

Altibase 7.1.0.5.3
================================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Fixed Bugs](#fixed-bugs)
  - [BUG-48594 Improved CPU bottleneck caused by SQL PLAN CACHE when executing SQL statements that include synonyms.](#bug-48594%C2%A0improved-cpu-bottleneck-caused-by-sql-plan-cache-when-executing-sql-statements-that-include-synonyms)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [Compatibility](#compatibility)
  - [Altibase Server Properties](#altibase-server-properties)
  - [Performance Views](#performance-views)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Fixed Bugs
----------

### BUG-48594 Improved CPU bottleneck caused by SQL PLAN CACHE when executing SQL statements that include synonyms. 

-   **module** : qp-dml-execute
-   **Category** : Enhancement
-   **재현 빈도** : Always
-   **내용** : Improved CPU bottleneck caused by SQL PLAN CACHE when executing SQL statements that include synonyms. To apply this improvement, set __SQL_PLAN_CACHE_VALID_MODE to 1.
-   **재현 방법**
	-   **재현 절차**
	-   **수행 결과**
	-   **예상 결과**
-   **Workaround**
-   **변경사항**
    -   Performance view
    -   Property
        -   New
            -   __SQL_PLAN_CACHE_VALID_MODE (hidden property)
            -   Description: Determines whether to enable the CPU bottleneck improvement feature during the SQL PLAN CACHE validation phase.
            -   default value: 0
            -   Range : 0,1
    -   Compile Option
    -   Error Code


Changes
-------

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    7.1.0.5.3     |          6.5.1          |    8.9.1     |        7.1.7        |            7.4.6             |

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
