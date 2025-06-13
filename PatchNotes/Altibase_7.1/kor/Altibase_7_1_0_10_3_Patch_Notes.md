Altibase 7.1.0.10.3 Patch Notes
===============================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-51446 서버 비정상 종료 시(SIGSEGV 등) altibase_error.log에 콜스택 외 추가 진단 정보를 출력하도록 개선](#bug-51446)
    - [BUG-51452 불완전 복구에서 로그 앵커 백업 파일과 데이터 백업 파일의 익스텐드(Extend) 범위의 불일치 경우에 대한 보완](#bug-5145284)
    - [BUG-51466 Altibase EF Core에서 GUID 데이터타입 지원](#bug-51466)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-51471 BUFFER\_AREA\_SIZE를 820G 이상으로 설정할 경우, DB 생성이 실패하는 문제를 수정합니다.](#bug-51471)
    - [BUG-51475 aexport 수행시 생성되는 이중화 객체의 생성 DDL에 `AS MASTER/SLAVE`절이 누락되는 문제를 수정합니다.](#bug-51475)
    - [BUG-51476 DBMS_METADATA패키지를 이용하여 이중화 생성 DDL을 추출할 때, `AS MASTER/SALVE`절이 누락되는 문제를 수정합니다.](#bug-51476)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-51446<a name=bug-51446></a> 서버 비정상 종료 시(SIGSEGV 등) altibase_error.log에 콜스택 외 추가 진단 정보를 출력하도록 개선

-   **module** : mm

-   **Category** : Maintainability

-   **재현 빈도** : Frequence

-   **설명** : 서버 비정상 종료 시(SIGSEGV 등) altibase_error.log에 콜스택 외 추가 진단 정보를 출력하도록 개선합니다.

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

### BUG-51452<a name=bug-51452></a> 불완전 복구에서 로그 앵커 백업 파일과 데이터 백업 파일의 익스텐드(Extend) 범위의 불일치 경우에 대한 보완

-   **module** : sm

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : 로그 앵커 백업 파일과 데이터 백업 파일의 익스텐드 범위가 일치하지 않을 경우, 불완전 복구 과정에서 페이지 상태가 유효하지 않아 서버가 비정상 종료될 수 있습니다. 이번 패치에서 두 파일의 익스텐드 범위가 일치하지 않더라도 불완전 복구가 수행될 수 있도록 개선하였습니다.

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

### BUG-51466<a name=bug-51466></a> Altibase EF Core에서 GUID 데이터타입 지원

-   **module** : adonet
-   **Category** : Functionality
-   **재현 빈도** : Always
-   **설명** : Altibase EF Core 에서 지원되는 .NET Core의 데이터 타입에 Guid 데이터 타입이 추가되었습니다. 

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

### BUG-51471<a name=bug-51471></a> BUFFER\_AREA\_SIZE를 820G 이상으로 설정할 경우, DB 생성이 실패하는 문제를 수정합니다.

-   **module** : sm

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : BUFFER\_AREA\_SIZE를 820G 이상으로 설정할 경우, DB 생성이 실패하는 문제를 수정합니다.

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

### BUG-51475<a name=bug-51475></a> aexport 수행시 생성되는 이중화 객체의 생성 DDL에 `AS MASTER/SLAVE`절이 누락되는 문제를 수정합니다.

-   **module** : ux-aexport

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : aexport 수행시 생성되는 이중화 객체의 생성 DDL에 `AS MASTER/SLAVE`절이 누락되는 문제를 수정합니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    DROP TABLE t1;
    CREATE TABLE t1 (c1 INT PRIMARY KEY, c2 INT);
    CREATE REPLICATION rep1 AS MASTER WITH 'localhost', 31136 FROM sys.t1 TO sys.t1;
    
    $aexport -s localhost -u sys -p manager
    ```

  - **수행 결과**

    ```sql
    $cat ALL_CRT_REP.sql
    
    DROP REPLICATION "REP1";
    CREATE REPLICATION "REP1" WITH 'localhost', 31136
    FROM "SYS"."T1" TO "SYS"."T1";
    ```

  -   **예상 결과**

      ```sql
      $cat ALL_CRT_REP.sql
      
      DROP REPLICATION "REP1";
      CREATE REPLICATION "REP1" AS MASTER
      WITH 'localhost', 31136
      FROM "SYS"."T1" TO "SYS"."T1";
      ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-51476<a name=bug-51476></a> DBMS_METADATA패키지를 이용하여 이중화 생성 DDL을 추출할 때, `AS MASTER/SALVE`절이 누락되는 문제를 수정합니다.

-   **module** : ux-dbms_metadata

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : DBMS_METADATA패키지를 이용하여 이중화 생성 DDL을 추출할 때, `AS MASTER/SALVE`절이 누락되는 문제를 수정합니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    set vertical on;
    drop table t1;
    create table t1 (c1 int primary key, c2 int);
    create replication rep1 as master with 'localhost', 31136 from sys.t1 to sys.t1;
    
    select to_char(dbms_metadata.get_ddl('REPLICATION','REP1',null)) as ddl from dual;
    ```

  - **수행 결과**

    ```sql
    DDL : CREATE REPLICATION "REP1" WITH 'localhost', 31136
    FROM "SYS"."T1" TO "SYS"."T1"
    1 row selected.
    ```

  -   **예상 결과**

      ```sql
      DDL : CREATE REPLICATION "REP1" AS MASTER
      WITH 'localhost', 31136
      FROM "SYS"."T1" TO "SYS"."T1"
      1 row selected.
      ```

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
| 7.1.0.10.3       | 6.5.1                   | 8.12.1       | 7.1.7               | 7.4.7                        |

> Altibase 7.1 패치 버전별 히스토리는 [Version_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.1/Altibase_7_1_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의
> 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는
> 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

> 패치를 롤백하려는 경우,
> [메타다운그레이드](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Installation%20Guide.md#%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9Cmeta-downgrade)를
> 참고한다.

#### CM protocol Version

통신 프로토콜 버전은 변경되지 않았다.

#### Replication protocol Version

Replication 프로토콜 버전은 변경되지 않았다.

### 프로퍼티

추가/변경/삭제된 프로퍼티

### 성능 뷰

추가/변경/삭제된 성능뷰
