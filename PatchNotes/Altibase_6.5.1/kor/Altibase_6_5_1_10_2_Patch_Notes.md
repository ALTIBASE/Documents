Altibase 6.5.1.10.2 Patch Notes
=================================

* [New Features](#new-features)
  * [BUG-47423 APRE에서 RETURNING INTO 절을 지원하도록 개선하였습니다.](#bug-47423)
* [Fixed Bugs](#fixed-bugs)
  * [BUG-50948 서버에 fetch할 데이터가 남아 있는 경우 ResultSet.close()를 해도 커서가 바로 닫히지 않을 수 있습니다.](#bug-50948)
  * [BUG-51012 SQLColumns함수에서 SchemaName(스키마 이름) 인자에 NULL이 전달될 경우, 잘못된 데이터가 반환됩니다.](#bug-51012)
  * [BUG-51013 ODBC 드라이버를 이용하여 다이너셋(dynaset) 테스트를 수행할 때, Altibase 데이터베이스에 연결이 성공했으나 다이너셋을 지원하지 않는다는 오류가 발생합니다.](#bug-51013)
  * [BUG-51041 디스크 테이블에서 DML 을 수행하는 중에 내부적으로테이블 정보를 기록하는 페이지가 깨진 경우, 서버가 비정상 종료되는 문제가 있습니다.](#bug-51041)
* [Changes](#changes)
     - [Version Info](#version-info)
     - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
     - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
     - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

New Features
============

### BUG-47423<a name=bug-47423></a>  APRE에서 RETURNING INTO 절을 지원하도록 개선하였습니다.

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

### BUG-50948<a name=bug-50948></a> 서버에 fetch할 데이터가 남아 있는 경우 ResultSet.close()를 해도 커서가 바로 닫히지 않을 수 있습니다.

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : ResultSet 객체에서 조회할 데이터가 Altibase 서버에 남아
    있을 때, ResultSet.close()를 호출해도 커서가 닫히지 않습니다.

    ResultSet 객체에서 조회할 데이터가 Altibase 서버에 남아 있을 때,
    ResultSet.close()를 호출해도 커서가 닫히지 않는 문제를
    수정하였습니다. 이 문제가 발생하면 Altibase 서버 설정에 의해 
    FETCH\_TIMEOUT 오류가 발생할 수 있습니다.

    이 버그가 수정된 버전을 반영하려면 Altibase JDBC 드라이버를
    6.5.1.10.2 이상 버전으로 패치해야 합니다.

- **재현 방법**

  - **재현 절차**

    ```java
    iSQL> create table t1 (c1 int);
    iSQL> insert into t1 select level from dual connect by level <= 1000;
    
    [altibase.properties]
    FETCH_TIMEOUT = 5
        
    [Altibase 클라이언트]
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

    ```java
    [Altibase 클라이언트]
    Exception in thread "main" java.sql.SQLException: Communication link failure: There was no response from the server, and the channel has reached end-of-stream.
        
    [Altibase 서버]
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

### BUG-51012<a name=bug-51012></a> SQLColumns함수에서 SchemaName(스키마 이름) 인자에 NULL이 전달될 경우, 잘못된 데이터가 반환됩니다.

-   **module** : mm-cli

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : SQLColumns함수에서 SchemaName(스키마 이름) 인자에 NULL이 전달될 경우, 잘못된 데이터가 반환되는 문제를 수정합니다.
    
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

### BUG-51013<a name=bug-51013></a> ODBC 드라이버를 이용하여 다이너셋(dynaset) 테스트를 수행할 때, Altibase 데이터베이스에 연결이 성공했으나 다이너셋을 지원하지 않는다는 오류가 발생합니다.

-   **module** : mm-cli

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : ODBC 드라이버를 이용하여 다이너셋 테스트를 수행할 때, Altibase 데이터베이스에 연결이 성공했으나 다이너셋을 지원하지 않는다는 오류가 발생하는 문제를 해결했습니다.
    
    SQLGetInfo 함수에서 SCROLL_OPTIONS, SCROLL_CONCURRENCY 의 매개변수가 전달될 때, 내부 로직에서 누락된 값이 있어 올바르게 동작하도록 수정했습니다.
    
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

### BUG-51041<a name=bug-51041></a> 디스크 테이블에서 DML 을 수행하는 중에 내부적으로테이블 정보를 기록하는 페이지가 깨진 경우, 서버가 비정상 종료되는 문제가 있습니다.

-   **module** : sm

-   **Category** : Enhancement

-   **재현 빈도** : Unknown

-   **설명** : 디스크 테이블에서 DML을 수행하는 중에 내부적으로 테이블
    정보를 기록하는 페이지가 깨진 경우, 페이지 덤프와 같이 분석 가능한
    정보를 기록하고 예외가 발생하도록 수정되었습니다.

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
| 6.5.1.10.2       | 6.3.1                   | 8.1.1        | 7.1.3               | 7.4.5                        |

> Altibase 6.5.1 패치 버전별 히스토리는 [Version_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_6.5.1/Altibase_6_5_1_Version_Histories.md) 에서 확인할 수 있다..

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

#### 추가된 프로퍼티

#### 변경된 프로퍼티

#### 삭제된 프로퍼티

### 성능 뷰

#### 추가된 성능 뷰

#### 변경된 성능 뷰

#### 삭제된 성능 뷰
