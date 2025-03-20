Altibase 7.1.0.9.8 Patch Notes
==============================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [New Features](#new-features)
  - [BUG-50912 TCP 소켓 옵션 SO_LINGER를 설정하는 연결 속성 socket_immediate_close를 추가합니다.](#bug-50912-tcp-%EC%86%8C%EC%BC%93-%EC%98%B5%EC%85%98-so_linger%EB%A5%BC-%EC%84%A4%EC%A0%95%ED%95%98%EB%8A%94-%EC%97%B0%EA%B2%B0-%EC%86%8D%EC%84%B1-socket_immediate_close%EB%A5%BC-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
- [Fixed Bugs](#fixed-bugs)
  - [BUG-50948 서버에 fetch할 데이터가 남아 있는 경우 ResultSet.close()를 해도 커서가 바로 닫히지 않을 수 있습니다.](#bug-50948-%EC%84%9C%EB%B2%84%EC%97%90-fetch%ED%95%A0-%EB%8D%B0%EC%9D%B4%ED%84%B0%EA%B0%80-%EB%82%A8%EC%95%84-%EC%9E%88%EB%8A%94-%EA%B2%BD%EC%9A%B0-resultsetclose%EB%A5%BC-%ED%95%B4%EB%8F%84-%EC%BB%A4%EC%84%9C%EA%B0%80-%EB%B0%94%EB%A1%9C-%EB%8B%AB%ED%9E%88%EC%A7%80-%EC%95%8A%EC%9D%84-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-50969 altibase\_stmt\_bind\_param 함수의 두 번째 인자의 메모리 주소가 변경되면 Some parameters were not bound. 에러가 발생합니다.](#bug-50969-altibase%5C_stmt%5C_bind%5C_param-%ED%95%A8%EC%88%98%EC%9D%98-%EB%91%90-%EB%B2%88%EC%A7%B8-%EC%9D%B8%EC%9E%90%EC%9D%98-%EB%A9%94%EB%AA%A8%EB%A6%AC-%EC%A3%BC%EC%86%8C%EA%B0%80-%EB%B3%80%EA%B2%BD%EB%90%98%EB%A9%B4-some-parameters-were-not-bound-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-50975 SIMPLE QUERY 최적화 기능을 활성화하고 JDBC 연결 속성에 remove\_redundant\_transmission을 사용할 때, SQL 문 수행 중 메모리 오류가 발생할 수 있습니다.](#bug-50975-simple-query-%EC%B5%9C%EC%A0%81%ED%99%94-%EA%B8%B0%EB%8A%A5%EC%9D%84-%ED%99%9C%EC%84%B1%ED%99%94%ED%95%98%EA%B3%A0-jdbc-%EC%97%B0%EA%B2%B0-%EC%86%8D%EC%84%B1%EC%97%90-remove%5C_redundant%5C_transmission%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%A0-%EB%95%8C-sql-%EB%AC%B8-%EC%88%98%ED%96%89-%EC%A4%91-%EB%A9%94%EB%AA%A8%EB%A6%AC-%EC%98%A4%EB%A5%98%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
  - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
  - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->



New Features
==========

### BUG-50912 Added connection property socket_immediate_close to configure TCP socket option SO_LINGER. 

#### module

mm-jdbc

#### Category 

Functionality

#### Reproducibility 

Always


#### Description 

The connection property `socket_immediate_close` has been added to control the activation of the SO_LINGER TCP socket option.

- true: Sets the SO_LINGER value to 0. The connection is terminated immediately when the socket is closed, and any remaining data is not transmitted.
- false: Disables SO_LINGER. The socket is closed immediately, but if there is data remaining in the socket buffer, the kernel will attempt to send it for a period of time.

The default value is **false**, and this connection property is supported starting from Altibase JDBC driver version 7.1.0.9.8 and above.

#### How to reproduce this bug

-   **Reproduction conditions**

-   **Actual Results**

-   **Expected Results**

#### Workaround

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code

Fixed Bugs
==========

### BUG-50948 Fixed an issue where the cursor may not close immediately after calling `ResultSet.close()` if there is remaining data to fetch from the server.
#### module

mm-jdbc

#### Category

Functionality

#### Reproducibility

Rare

#### Description 

Fixed an issue where the cursor would not close immediately after calling `ResultSet.close()` if there was remaining data to fetch from the Altibase server. This could result in a `Fetch Timeout` error due to server settings.

To resolve this bug, update to Altibase JDBC Driver version 7.1.0.7.8 or later.

#### How to reproduce this bug

- **Reproduction conditions**

  ```
  iSQL> create table t1 (c1 int);
  iSQL> insert into t1 select level from dual connect by level <= 1000;
  
  [altibase.properties]
  FETCH_TIMEOUT = 5 
  
  [Altibase Client Side]
  sStmt.setFetchSize(1);
  ResultSet sRs = sStmt.executeQuery("SELECT * FROM t1");
  if (sRs.next())
  {
      System.out.println("col1 ===>" + sRs.getInt(1));
  }
  sRs.close();
  Thread.sleep(7000);
  sRs = sStmt.executeQuery("SELECT 1 FROM dual");
  if (sRs.next())
  {
      System.out.println(sRs.getString(1));
  }
  ```

- **Actual Results**

  ```bash
  [Altibase Client Side]
  Exception in thread "main" java.sql.SQLException: Communication link failure: There was no response from the server, and the channel has reached end-of-stream.
  
  [Altibase Server Side]
  [2024/06/03 09:51:01 4EF][PID:26603][Thread-139699788171328][LWP-26592]
  [Notify : Fetch Timeout] Session Closed by Server : Session ID = 2
      CLIENT_INFO           => TCP 192.168.1.48:54096(PID : 2065530879)
      Time Limit            => 5
      Running Time          => 6
      Transaction ID        => 5152
      Caused by Query       => SELECT * FROM t1
  ```

- **Expected Results**

  ```
  1
  ```

#### Workaround

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50969 Fixed an issue where changing the memory address of the second argument in the `altibase_stmt_bind_param` function caused a **"Some parameters were not bound."** error.
#### module

ux-cdbc

#### Category

Functional Error

#### Reproducibility

Always

#### Description 

Fixed an issue where changing the memory address of the second argument in the `altibase_stmt_bind_param` function could cause a **"Some parameters were not bound."** error or an abnormal client termination.

This issue occurred when repeatedly executing the `altibase_stmt_bind_param` and `altibase_stmt_execute` functions. To apply this fix, update the ACI library (`libalticapi.a`).

#### How to reproduce this bug

- **Reproduction conditions**

  ```c
  sRC = altibase_stmt_prepare(sStmt, "INSERT INTO bug50969 VALUES(?, ?)");
  ...details omitted...
  memset(sBind1, 0, sizeof(sBind1));
  ...details omitted....
  sRC = altibase_stmt_bind_param(sStmt, sBind1);
  ...details omitted....
  sCount++;
  sBind1Count = 11;
  if (altibase_stmt_execute(sStmt) != ALTIBASE_SUCCESS)
  {
      PRINT_STMT_ERROR(sStmt);
      goto end_stmt;
  }
  altibase_stmt_free_result(sStmt);
  memset(sBind2, 0, sizeof(sBind2));
  ...details omitted....
  sRC = altibase_stmt_bind_param(sStmt, sBind2);
  ...details omitted....
  sCount++;
  sBind2Count = 12;
  if (altibase_stmt_execute(sStmt) != ALTIBASE_SUCCESS)
  {
      PRINT_STMT_ERROR(sStmt);
      goto end_stmt;
  }
  ```

-   **Actual Results**

    ```c
    [51051] HY000 Some parameters were not bound.
    ```
    
-   **Expected Results**

    ```c
    SELECT * FROM bug50969;
    C1          C2
    ---------------------------
    11          1
    12          2
    2 rows selected.
    ```

#### Workaround

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50975 Fixed a memory error that could occur when executing SQL statements with SIMPLE QUERY optimization enabled and the JDBC connection property `remove_redundant_transmission` set.
#### module

mm

#### Category

Memory Error

#### Reproducibility

Always


#### Description

Fixed a memory error that could occur when executing SQL statements with SIMPLE QUERY optimization enabled and the JDBC connection property `remove_redundant_transmission` set. 

#### How to reproduce this bug

- **Reproduction conditions**

  ```
  [Altibase Server side]
  ALTER SYSTEM SET EXECUTOR_FAST_SIMPLE_QUERY = 1;
  CREATE TABLE BUG 
  (
    C1           INTEGER       NOT NULL,
    C2           INTEGER       NOT NULL,
    C3           DECIMAL(12,2),
    C4           DECIMAL(4,4),
    C5           INTEGER,
    C6           VARCHAR(10),
    C7           VARCHAR(20),
    C8           VARCHAR(20),
    C9           VARCHAR(20),
    C10          CHAR(2),
    C11          CHAR(9)
  );
  
  [Altibase Client Side]
  String sURL      = "jdbc:Altibase://127.0.0.1:" + sPort + "/mydb" +
                             "?remove_redundant_transmission=1";
  ...details omitted...
  /* Initialize environment */
  try
  {
      sCon = DriverManager.getConnection( sURL, sProps );
      sStmt = sCon.createStatement();
      sRS = sStmt.executeQuery( "SELECT C6, C7, C8, C9, C10, C11 FROM BUG50975");
      sRowCount = 0;
      /* Fetch all data */
      while( sRS.next() )
      {
          sRowCount++;
      }
      System.out.println(sRowCount + " rows selected");
      /* Finalize process */
      sStmt.close();
      sCon.close();
  }
  ```

- **Actual Results**

  ```
  Server abnormal termination
  ```

- **Expected Results**

  ```
  no error
  ```
  

#### Workaround

#### Changes

-   Performance view
-   Property
-   Compile Option
-   Error Code

Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    7.1.0.9.8     |          6.5.1          |    8.11.1    |        7.1.7        |            7.4.7             |

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
