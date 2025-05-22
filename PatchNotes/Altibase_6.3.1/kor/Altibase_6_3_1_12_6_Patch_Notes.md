# Altibase 6.3.1.12.6 Patch Notes

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-50713 잘못된 패킷으로 Protocol header error가 발생한 경우, 에러메시지에 헤더 내용 출력하도록 개선합니다.](#bug-50713)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-40266 갱신 트랜잭션이 대기하는 상황이면 altibase_boot.log에 메시지를 출력하도록 개선합니다.](#bug-40266)
    - [BUG-49987 FROM 절에 인라인 뷰, GROUP BY 절에 문자 함수, SELECT 절과 분석 함수 ORDER BY 절에 GROUP BY 절의 키를 사용할 때 발생하는 안정성 문제를 개선합니다.](#bug-49987)
    - [BUG-50533 Altibase 6.1.1 클라이언트로 Altibase 6.3.1 서버에 접속을 시도할 때, 연결 실패에 대한 audit 정보가 잘못 기록되는 문제를 수정합니다.](#bug-50533)
    - [BUG-50697 JDBC 에서 PreparedStatement를 이용하여 ping 쿼리 사용시 메모리 누수가 발생합니다.](#bug-50697)
    - [BUG-50791 TO_CHAR 함수를 ALIAS로 조건절에 사용시 뷰에 대한 조건절 Pushdown 이 2번 이상 발생할 경우, 비정상 종료되는 문제를 수정합니다.](#bug-50791)
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

Fixed Bugs
==========

### BUG-40266<a name=bug-40266></a> 갱신 트랜잭션이 대기하는 상황이면 altibase_boot.log에 메시지를 출력하도록 개선합니다.

-   **module** : sm

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : 갱신 트랜잭션이 대기하는 상황의 경우 사용자는 이유를 알지 못한채 무한정 대기해야 했으나, 이 버그의 처리로 altibase_boot.log의 메시지를 확인하여 원인 파악을 할 수 있게 개선하였습니다.

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

### BUG-49987<a name=bug-49987></a> FROM 절에 인라인 뷰, GROUP BY 절에 문자 함수, SELECT 절과 분석 함수 ORDER BY 절에 GROUP BY 절의 키를 사용할 때 발생하는 안정성 문제를 개선합니다.

-   **module** : qp-select

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : FROM 절에 인라인 뷰, GROUP BY 절에 문자 함수, SELECT 절과
    분석 함수 ORDER BY 절에 GROUP BY 절의 키를 사용할 때 Altibase 서버가
    비정상 종료하는 현상을 수정합니다.

- **재현 방법**

  - **재현 절차**

    ```sql
    CREATE TABLE T1 ( YYYYMM VARCHAR(6) );
    INSERT INTO T1 VALUES ('201901');
    CREATE TABLE T2 ( YYYYMM VARCHAR(6) );
    INSERT INTO T2 VALUES ('202001');
    SELECT SUBSTR(B1.YYYYMM,1,4) || 'A' AS ACT_YYYY              
         , ROW_NUMBER() OVER( ORDER BY SUBSTR(B1.YYYYMM,1,4)) AS PK_COL
      FROM T1 B2
         , (SELECT A2.YYYYMM AS YYYYMM FROM T2 A2) B1
      WHERE B2.YYYYMM (+)= B1.YYYYMM
      GROUP BY SUBSTR(B1.YYYYMM,1,4);
    ```

  - **수행 결과**

    ```sql
    [ERR-91015 : Communication failure.]
    ```

  -   **예상 결과**

      ```sql
      ACT_YYYY  PK_COL
      ----------------------------------
      2020A    1
      1 row selected.
      ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50533<a name=bug-50533></a> Altibase 6.1.1 클라이언트로 Altibase 6.3.1 서버에 접속을 시도할 때, 연결 실패에 대한 audit 정보가 잘못 기록되는 문제를 수정합니다.

-   **module** : mm-altiaudit

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : Altibase 6.1.1 클라이언트로 Altibase 6.3.1 서버에 접속을 시도할 때, 연결 실패에 대해서 CONNECT가 기록되어야 하는데 DISCONNECT로 기록되는 문제 수정합니다.

- **재현 방법**

  - **재현 절차** 

    - a. Altibase 6.3.1 서버의 isql에서 아래의 명령어 수행

      ```sql
      audit connect, disconnect;
      ALTER SYSTEM START AUDIT;
      ```

    - b. Altibase 6.1.1 클라이언트에서 1의 6.3.1 서버로 접속을 시도 (잘못된 비밀번호로 접속을 시도한다)

    - c. Altibase 6.3.1 서버의 isql에서 아래의 명령어 수행 후 $ALTIBASE_HOME/trc/ 에서 audit 로그 확인

      ```sql
      ALTER SYSTEM STOP AUDIT;
      ```

  -   **수행 결과**

  - **수행 결과**

  - **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
        
    -   Property
    -   Compile Option
-   Error Code

### BUG-50697<a name=bug-50697></a> JDBC 에서 PreparedStatement를 이용하여 ping 쿼리 사용시 메모리 누수가 발생합니다.

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : JDBC 에서 PreparedStatement를 이용하여 ping 쿼리 사용시 메모리 누수가 발생하는 문제를 수정하였습니다. 이 버그를 적용하려면 JDBC 드라이버를 패치해야 합니다.
    
- **재현 방법**

  - **재현 절차**

    ```java
    Connection sConn = getConnection("20300");
    PreparedStatement sStmt = sConn.prepareStatement("/* PING */ SELECT 1 ");
    ResultSet sRs = sStmt.executeQuery();
    if (sRs.next())
    {
        sRs.close();
    }
    sStmt.executeQuery();
    sStmt.executeQuery();
    sStmt.executeQuery();
    sStmt.close();
    sConn.close();
    ```

  -   **수행 결과**

          메모리 사용량이 계속 증가함

  -   **예상 결과**

          메모리 사용량이 계속 증가하지 않음

-   **Workaround**

        ping 쿼리 대신 select 1 from dual 사용

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50791<a name=bug-50791></a> TO_CHAR 함수를 ALIAS로 조건절에 사용시 뷰에 대한 조건절 Pushdown 이 2번 이상 발생할 경우, 비정상 종료되는 문제를 수정합니다.

-   **module** : qp

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : TO_CHAR 함수를 alias로 조건절에 사용시 뷰에 대한 조건절 Pushdown이 2번 이상 발생할 경우, 서버가 비정상 종료되는 문제를 수정합니다. 이 버그는 아래의 4가지 조건이 모두 일치하는 경우에만 발생합니다.
    
    1. TO_CHAR 함수의 2번째 인자로 숫자 형식이나 날짜 형식이 있는 경우
    2. TO_CHAR 함수의 1번째 인자가 Numeric 타입이 아닌 경우
    3. TO_CHAR 함수의 1번째 인자의 컬럼이 서브쿼리의 뷰에 존재하며, 뷰 머징이 되지 않고 Pushdown되는 경우
    4. 서브쿼리의 타겟절에서 TO_CHAR 함수를 사용하고 ALIAS를 지정하며, 이 ALIAS를 메인쿼리의 조건절에서 사용할 때, TO_CHAR 함수가 사용된 뷰로 Pushdown 되는 경우
    
- **재현 방법**

  - **재현 절차**

    ```sql
    select * from (
         select 
               (select c.USER_NAME from SYSTEM_.SYS_COMMENTS_ c where c.table_name = a.table_name and c.COLUMN_NAME is null limit 1) as usernm,
               a.table_name, 
               (select c.comments from SYSTEM_.SYS_COMMENTS_ c where c.table_name = a.table_name and c.COLUMN_NAME is null limit 1) as tablenm,
               to_char((b.fixed_alloc_mem+b.var_alloc_mem)/1024/1024,'999,999,999') || 'MB' as alloc,
               to_char((b.fixed_used_mem+b.var_used_mem)/1024/1024,'999,999,999') || 'MB' as used
          from system_.sys_tables_ a, v$memtbl_info b
         where a.table_oid = b.table_oid
           and a.user_id <> (select user_id from system_.sys_users_ where user_name = 'SYSTEM_')
           and a.table_type = 'T'
          order by (b.fixed_alloc_mem+b.var_alloc_mem) desc)
          where alloc != '0MB';
    ```

  - **수행 결과**

    ```sql
    [ERR-91015 : Communication failure.]
    ```

  -   **예상 결과**

      ```sql
      No rows selected.
      ```

- **Workaround**

  ```sql
  NO_PUSH_SELECT_VIEW hint 사용
  
  select /*+ NO_PUSH_SELECT_VIEW(AA) */ * from (
       select /*+  */
             (select /*+   */c.USER_NAME from SYSTEM_.SYS_COMMENTS_ c where c.table_name = a.table_name and c.COLUMN_NAME is null limit 1) as usernm,
             a.table_name, 
             (select /*+  */c.comments from SYSTEM_.SYS_COMMENTS_ c where c.table_name = a.table_name and c.COLUMN_NAME is null limit 1) as tablenm,
             to_char((b.fixed_alloc_mem+b.var_alloc_mem)/1024/1024,'999,999,999') || 'MB' as alloc,
             to_char((b.fixed_used_mem+b.var_used_mem)/1024/1024,'999,999,999') || 'MB' as used
        from system_.sys_tables_ a, v$memtbl_info b
       where a.table_oid = b.table_oid
         and a.user_id <> (select /*+ */user_id from system_.sys_users_ where user_name = 'SYSTEM_')
         and a.table_type = 'T'
        order by (b.fixed_alloc_mem+b.var_alloc_mem) desc) AA
        where alloc != '0MB';
  ```

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
| 6.3.1.12.6       | 6.2.1                   | 6.3.1        | 7.1.1               | 7.4.1                        |

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

#### 추가된 프로퍼티

#### 변경된 프로퍼티

#### 삭제된 프로퍼티

### 성능 뷰

#### 추가된 성능 뷰

#### 변경된 성능 뷰

#### 삭제된 성능 뷰
