Altibase 6.3.1.12.7 Patch Notes
===============================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-50713 잘못된 패킷으로 Protocol header error가 발생한 경우, 에러메시지에 헤더 내용 출력하도록 개선합니다.](#bug-50713)
    - [BUG-47423 APRE에서 RETURNING INTO 절을 지원하도록 개선하였습니다.](#bug-47423)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-50810 API를 통한 LOB 데이터 작업시, "Internal server error"가 발생할 수 있습니다.](#bug-50810)
    - [BUG-50948 서버에 fetch할 데이터가 남아 있는 경우 ResultSet.close()를 해도 커서가 바로 닫히지 않을 수 있습니다.](#bug-50948)
    - [BUG-51357 WITH절을 사용하는 쿼리에서 내부 쿼리와 외부 쿼리 모두 RANK() OVER(...) 함수에 동일한 alias를 사용하는 경우, 서버가 비정상 종료할 수 있습니다.](#bug-51357)
    - [BUG-51423 SELECT Statement 의 순서에 따른 Lock 해제 현상 수정](#bug-51423)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-50713<a name=bug-50713></a> 잘못된 패킷으로 Protocol header error가 발생한 경우, 에러메시지에 헤더 내용 출력하도록 개선합니다.

-   **module** : cm

-   **Category** : Functionality

-   **재현 빈도** : Rare

-   **설명** : 잘못된 패킷이 수신되어 Protocol header error가 발생했을 때, 에러메시지에 헤더 내용을 출력하여 문제 분석에 도움을 주도록 개선하였습니다.
    - 수정전 : ERR-7101d(errno=0) Protocol header error.(TCP 127.0.0.1:41462)
    - 수정후 : ERR-710cc(errno=0) Protocol header error.(TCP 127.0.0.1:41462, 0, 3132333435363738393031323334353637383930)
    
-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code
        -   수정전 : ERR-7101d(errno=0) Protocol header error.(TCP 127.0.0.1:41462)
        -   수정후 : ERR-710cc(errno=0) Protocol header error.(TCP 127.0.0.1:41462, 0, 3132333435363738393031323334353637383930)

### BUG-47423<a name=bug-47423></a> APRE에서 RETURNING INTO 절을 지원하도록 개선하였습니다.

-   **module** : mm-apre

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : APRE에서 RETURNING INTO 절을 지원하도록 개선하였습니다.

-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**
    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

Fixed Bugs
==========

### BUG-50810<a name=bug-50810></a> API를 통한 LOB 데이터 작업시, "Internal server error"가 발생할 수 있습니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : API를 통해 LOB 데이터를 조회하거나 쓸 때 내부적으로
    쓰기(write) 작업이 실패하는 경우, 트랜잭션이 롤백되지 않아 잘못된
    페이지에 접근하는 오류가 발생할 수 있습니다.

    이제 LOB 데이터의 쓰기 작업이 실패할 경우, "Failed to complete LOB
    write operation." 에러메시지가 출력되도록 개선되었습니다. 이
    메시지가 나타나면, 사용자는 명시적으로 롤백(Rollback)을
    수행하여 잘못된 페이지에 접근하는 오류를 방지할 수 있습니다.

-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50948<a name=bug-50948></a> 서버에 fetch할 데이터가 남아 있는 경우 ResultSet.close()를 해도 커서가 바로 닫히지 않을 수 있습니다.

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : ResultSet 객체에서 조회할 데이터가 Altibase 서버에 남아 있을 때, ResultSet.close()를 호출해도 커서가 닫히지 않는 문제를 수정하였습니다. 이 문제가 발생하면 Altibase 서버 설정에 의해 FETCH_TIMEOUT 오류가 발생할 수 있습니다.
    
    이 버그가 수정된 버전을 반영하려면 Altibase JDBC 드라이버를 6.3.1.12.7 이상 버전으로 패치해야 합니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    iSQL> create table t1 (c1 int);
    iSQL> insert into t1 select level from dual connect by level <= 1000;
    [altibase.properties]
    FETCH_TIMEOUT = 5 
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

  - **수행 결과**

    ```sql
    [client]
    Exception in thread "main" java.sql.SQLException: Communication link failure: There was no response from the server, and the channel has reached end-of-stream.
    [server]
    [2024/06/03 09:51:01 4EF][PID:26603][Thread-139699788171328][LWP-26592]
    [Notify : Fetch Timeout] Session Closed by Server : Session ID = 2
        CLIENT_INFO           => TCP 192.168.1.48:54096(PID : 2065530879)
        Time Limit            => 5
        Running Time          => 6
        Transaction ID        => 5152
        Caused by Query       => SELECT * FROM t1
    ```

  -   **예상 결과**

          1

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-51357<a name=bug-51357></a> WITH절을 사용하는 쿼리에서 내부 쿼리와 외부 쿼리 모두 RANK() OVER(...) 함수에 동일한 alias를 사용하는 경우, 서버가 비정상 종료할 수 있습니다.

-   **module** : qp-select

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : WITH절을 사용하는 쿼리에서 내부 쿼리와 외부 쿼리 모두 RANK() OVER(...) 함수에 동일한 alias를 사용하는 경우, 서버가 비정상 종료되는 문제를 수정하였습니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    create table t1 ( i1 varchar(10) , i2 varchar(10) );
    ALTER SESSION SET STACK SIZE= 65536;
    WITH BASE AS (
    SELECT /*+ */A.i1 ,A.i2 ,RANK() OVER(ORDER BY i2) RNK
    FROM t1 A
    )
    SELECT ROW_RNK ,RANK() OVER(PARTITION BY i1 ORDER BY RNK DESC) RNK ,i1 ,i2
    FROM (
    SELECT A.i1 ,A.i2 ,A.RNK ROW_RNK ,RANK() OVER(PARTITION BY A.i1 ORDER BY A.i1 DESC) RNK
    FROM BASE A
    )
    ORDER BY ROW_RNK, RNK DESC;
    ```

  -   **수행 결과**

          [ERR-31455 : Failed to work because an internal exception occurred from an OS.[Contact Altibase's Support Center]]

  -   **예상 결과**

          no rows

- **Workaround**

  ```sql
  ALTER SESSION SET STACK SIZE= 65536;
  WITH BASE AS (
  SELECT /*+ */A.i1 ,A.i2 ,RANK() OVER(ORDER BY i2) RNK
  FROM t1 A
  )
  SELECT ROW_RNK ,RANK() OVER(PARTITION BY i1 ORDER BY RNK DESC) RNK2 ,i1 ,i2
  FROM (
  SELECT A.i1 ,A.i2 ,A.RNK ROW_RNK ,RANK() OVER(PARTITION BY A.i1 ORDER BY A.i1 DESC) RNK
  FROM BASE A
  )
  ORDER BY ROW_RNK, RNK2 DESC;
  ```

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-51423<a name=bug-51423></a> SELECT Statement 의 순서에 따른 Lock 해제 현상 수정

-   **module** : sm\_transaction

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : Non-AutoCommit 모드로 수행된 SELECT문에 대해서 자동으로 IS_LOCK을 해제하지 않도록 수정합니다.

-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

Changes
=======

### Version Info 

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 6.3.1.12.7       | 6.2.1                   | 6.3.1        | 7.1.1               | 7.4.1                        |

> Altibase 6.3.1 패치 버전별 히스토리는 [Version_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_6.3.1/Altibase_6_3_1_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의
> 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는
> 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

#### CM protocol Version

통신 프로토콜 버전은 변경되지 않았다.

#### Replication protocol Version

Replication 프로토콜 버전은 변경되지 않았다.

### 프로퍼티

추가/변경/삭제된 프로퍼티

### 성능 뷰

추가/변경/삭제된 성능뷰
