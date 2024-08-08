Altibase 7.1.0.9.9 Patch Notes
================================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [New Features](#new-features)
    - [BUG-47423 APRE에서 RETURNING INTO 절을 지원하도록 개선하였습니다.](#bug-47423)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-50949 aku 설정 파일에 주석 입력시, # 이후에 글자를 입력하지 않는 경우 오류가 발생합니다.](#bug-50949)
    - [BUG-50997  외부 쿼리를 참조하는 서브 쿼리에서 집계 함수를 사용하는 경우, 특정 조건에서 결과값 오류가 발생합니다.](#bug-50997)
    - [BUG-51004 altibase_stmt_bind_param에 바인딩하는 변수의 타입 또는 포인터가 바뀌는 경우, "Function sequence error"가 발생할 수 있습니다.](#bug-51004)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

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

### BUG-50949<a name=bug-50949></a> aku 설정 파일에 주석 입력시, # 이후에 글자를 입력하지 않는 경우 오류가 발생합니다.

-   **module** : aku

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : aku 설정 파일(aku.conf)에 주석 입력시, \# 이후에 글자를 입력하지 않을 경우 오류가 발생하는 문제를 수정하였습니다.
    
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

### BUG-50997<a name=bug-50997></a>  외부 쿼리를 참조하는 서브 쿼리에서 집계 함수를 사용하는 경우, 특정 조건에서 결과값 오류가 발생합니다.

-   **module** : qp

-   **Category** : Functional Error

-   **재현 빈도** : Always

- **설명** : 외부 쿼리를 참조하는 서브 쿼리에서 집계 함수를 사용하는 경우, 특정 조건에서 발생하는 결과값 오류를 수정하였습니다.
  이 버그는 다음의 조건을 모두 만족할 때만 발생합니다.

  1. AND 연산자의 조건에서 OR 연산자가 포함된 경우.
  2. OR 연산자의 조건에 외부 쿼리를 참조하는 서브 쿼리가 존재합니다.
  3. 2.의 서브 쿼리가 집계 함수를 사용합니다.

- **재현 방법**

  - **재현 절차**

    ```sql
    drop table T1;
    drop table T2; 
    
    create table T1
    (
     REV integer,
     REVTYPE smallint,
     id integer
    );
    
    insert into T1 values(7,              7,           0);
    insert into T1 values(6,              5,           2);
    insert into T1 values(5,              6,           1);
    
    create table T2
    (
     REV integer ,
     REVTYPE smallint,
     id integer
    );
    
    insert into T2 values(15,          3,      2);           
    insert into T2 values(17,          1,      0);           
    insert into T2 values(10,          3,      1);           
    
    select A.id 
    from T1 A, T2 B
    where 
       A.id = B.id
      and 
    (
        (B.REV = (select min(BB.REV) from T2 BB where BB.REV < 23 and B.id = BB.id )
          and 
         A.REV = (select (AA.REV) from T1 AA where AA.REV < 23 and A.id = AA.id)
        )
      or  (
        A.REVTYPE = 2
         and B.REVTYPE <= 2
           )
    );
    ```

  - **수행 결과**

    ```
    ID
    --------------
    1
    1 row selected.
    ```

  - **예상 결과**

    ```
    ID
    --------------
    0
    2
    1
    3 rows selected.
    ```

- **Workaround**

- **변경사항**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

### BUG-51004<a name=bug-51004></a> altibase_stmt_bind_param에 바인딩하는 변수의 타입 또는 포인터가 바뀌는 경우, "Function sequence error"가 발생할 수 있습니다. 

-   **module** : ux-cdbc

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : altibase_stmt_bind_param에 바인딩하는 변수의 타입 또는 포인터가 바뀌는 경우, "Function sequence error"가 발생하지 않도록 수정했습니다.
    
- **재현 방법**

  - **재현 절차**

        altibase_stmt_prepare (select ... )
        altibase_stmt_bind_param(sStmt, sBind1)
        altibase_stmt_execute
        altibase_stmt_free_result
        altibase_stmt_bind_param(sStmt, sBind2)
        altibase_stmt_execute

  - **수행 결과**

        altibase_stmt_prepare (select ... )
        altibase_stmt_bind_param(sStmt, sBind1)
        altibase_stmt_execute
        altibase_stmt_free_result
        altibase_stmt_bind_param(sStmt, sBind2)  -> Function sequence error
        altibase_stmt_execute

  -   **예상 결과**

          altibase_stmt_prepare (select ... )
          altibase_stmt_bind_param(sStmt, sBind1)
          altibase_stmt_execute
          altibase_stmt_free_result
          altibase_stmt_bind_param(sStmt, sBind2)  -> Success
          altibase_stmt_execute

-   **Workaround**

        없음

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    7.1.0.9.9     |          6.5.1          |    8.11.1    |        7.1.7        |            7.4.7             |

> Altibase 7.1 패치 버전별 히스토리는 [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.1/Altibase_7_1_Version_Histories.md) 에서 확인할 수 있다.

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

#### 추가된 프로퍼티

#### 변경된 프로퍼티

#### 삭제된 프로퍼티

### 성능 뷰

#### 추가된 성능 뷰

#### 변경된 성능 뷰

#### 삭제된 성능 뷰
