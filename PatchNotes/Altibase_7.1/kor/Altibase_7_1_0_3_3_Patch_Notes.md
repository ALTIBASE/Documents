<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Altibase 7.1.0.3.3 Patch Notes](#altibase-71033-patch-notes)
  - [New Features](#new-features)
    - [BUG-47589  C/C++ Internal procedure 기능 지원](#bug-47589-cc-internal-procedure-%EA%B8%B0%EB%8A%A5-%EC%A7%80%EC%9B%90)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-47527  Windows 서비스로 Altibase를 실행하는 경우, memstat 정보가 정상적으로 출력되지 않습니다.](#bug-47527-windows-%EC%84%9C%EB%B9%84%EC%8A%A4%EB%A1%9C-altibase%EB%A5%BC-%EC%8B%A4%ED%96%89%ED%95%98%EB%8A%94-%EA%B2%BD%EC%9A%B0-memstat-%EC%A0%95%EB%B3%B4%EA%B0%80-%EC%A0%95%EC%83%81%EC%A0%81%EC%9C%BC%EB%A1%9C-%EC%B6%9C%EB%A0%A5%EB%90%98%EC%A7%80-%EC%95%8A%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-47540  메모리 인덱스의 동시성을 고려하지 않은 자동 통계 정보 수집과정 중 비정상 종료합니다.](#bug-47540-%EB%A9%94%EB%AA%A8%EB%A6%AC-%EC%9D%B8%EB%8D%B1%EC%8A%A4%EC%9D%98-%EB%8F%99%EC%8B%9C%EC%84%B1%EC%9D%84-%EA%B3%A0%EB%A0%A4%ED%95%98%EC%A7%80-%EC%95%8A%EC%9D%80-%EC%9E%90%EB%8F%99-%ED%86%B5%EA%B3%84-%EC%A0%95%EB%B3%B4-%EC%88%98%EC%A7%91%EA%B3%BC%EC%A0%95-%EC%A4%91-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-47577  DDL\_LOCK\_TIMEOUT 시간이 제대로 동작하지 않는 경우가 있습니다](#bug-47577-ddl%5C_lock%5C_timeout-%EC%8B%9C%EA%B0%84%EC%9D%B4-%EC%A0%9C%EB%8C%80%EB%A1%9C-%EB%8F%99%EC%9E%91%ED%95%98%EC%A7%80-%EC%95%8A%EB%8A%94-%EA%B2%BD%EC%9A%B0%EA%B0%80-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-47586  ABORT Error Message가 기록되지 않습니다.](#bug-47586-abort-error-message%EA%B0%80-%EA%B8%B0%EB%A1%9D%EB%90%98%EC%A7%80-%EC%95%8A%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-47576  외부 참조가 있는 subquery unnesting 시에 결과 오류가 납니다.](#bug-47576-%EC%99%B8%EB%B6%80-%EC%B0%B8%EC%A1%B0%EA%B0%80-%EC%9E%88%EB%8A%94-subquery-unnesting-%EC%8B%9C%EC%97%90-%EA%B2%B0%EA%B3%BC-%EC%98%A4%EB%A5%98%EA%B0%80-%EB%82%A9%EB%8B%88%EB%8B%A4)
    - [BUG-47600  Update 시 left outer 와 inner join시 같이 사용된 경우 비정상 종료합니다.](#bug-47600-update-%EC%8B%9C-left-outer-%EC%99%80-inner-join%EC%8B%9C-%EA%B0%99%EC%9D%B4-%EC%82%AC%EC%9A%A9%EB%90%9C-%EA%B2%BD%EC%9A%B0-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Altibase 7.1.0.3.3 Patch Notes
==============================

New Features
------------

### BUG-47589  C/C++ Internal procedure 기능 지원

-   **module** : qp-psm-trigger-execute

-   **Category** : Functionality

-   **재현 빈도** : Always

- **증상** : [Internal procedure](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/ExternalProcedure.md#internal-mode) 기능을 지원합니다.

  External procedure는 external procedure agent process를 통해서 외부
  library를 load하고, server process와 external procedure agent간의
  통신을 통해서 외부 함수를 호출합니다.

  Internal procedure는 외부 library를 server process가 직접 load하고,
  직접 외부 함수를 호출합니다.

  따라서 internal procedure는 external procedure에 비해서 빠르게
  동작합니다.

  Internal procedure를 사용하기 위해서는 external procedure와 동일하게
  외부 library와 library객체를 생성한 뒤,

  external procedure 생성 구문에서 LANGUAGE와 C사이에 "INTERNAL"을
  추가하여 internal procedure를 생성하면 됩니다.

  예) CREATE (or REPLACE) PROCEDURE/FUNCTION ...

  ​       LANGUAGE (EXTERNAL/ INTERNAL) C ...

-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    - Performance view
    
      - 추가
    
        - [V$LIBRARY](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_4.md#vlibrary)
    
          C/C++ Internal procedure에서 동적으로 로드한 라이브러리의 정보를 보여준다. 라이브러리 정보를 통해서 원하는 라이브러리를 제대로 로드했는지 확인할 수 있다.
    
          | Column name     | Type        | Description                                          |
          | :-------------- | :---------- | :--------------------------------------------------- |
          | FILE_SPEC       | CHAR(4000)  | 동적 라이브러리 파일의 경로                          |
          | REFERENCE_COUNT | INTEGER     | 동적 라이브러리를 참조하는 Internal procedure의 개수 |
          | FILE_SIZE       | INTEGER     | 동적 라이브러리의 파일 크기 (Bytes)                  |
          | CREATE_TIME     | VARCHAR(48) | 동적 라이브러리가 생성된 시간                        |
          | OPEN_TIME       | VARCHAR(48) | 동적 라이브러리를 로드한 시간                        |
    
        - [V$PROCINFO](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_4.md#vprocinfo)
    
          프로시저의 상태 및 타입정보를 확인할 수 있다.
    
          | Column name  | Type        | Description                                                  |
          | :----------- | :---------- | :----------------------------------------------------------- |
          | PROC_OID     | BIGINT      | 저장 프로시저 식별자                                         |
          | MODIFY_COUNT | INTEGER     | 저장 프로시저가 재 생성 또는 재 컴파일 된 횟수               |
          | STATUS       | VARCHAR(7)  | 객체의 상태를 나타낸다. INVALID이면 실행 불가능 상태이다.    |
          | SESSION_ID   | INTEGER     | 저장 프로시저의 STATUS를 변경한 세션의 ID를 나타낸다.        |
          | PROC_TYPE    | VARCHAR(10) | 저장 프로시저의 타입을 나타낸다. NORMAL : 일반 프로시저, </br>EXTERNAL C, </br>INTERNAL C |
    
    - Property
    
    - Compile Option
    
    -   Error Code

Fixed Bugs
----------

### BUG-47527  Windows 서비스로 Altibase를 실행하는 경우, memstat 정보가 정상적으로 출력되지 않습니다.

-   **module** : id

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : 윈도우 서비스모드에서 사용시 v\$memstat에 부정확한 값이
    출력되는 경우가 있어 수정합니다.

-   **재현 방법**

    -   **재현 절차**

            Altibase를 Windows 서비스로 실행합니다.

    -   **수행 결과**

            아래는 비정상적인 출력의 예입니다.
            iSQL> SELECT * FROM V$MEMSTAT;
            ...
            External_Procedure                                                
            0                    0                    0                    
            Fixed_Table                                                       
            0                    0                    0                    
            GIS_Disk_Index                                                    
            0                    0                    0                    
            Mathematics                                                       
            0                    0                    0                    
            Query_Common                                                      
            0                    0                    65560                
            Query_Execute                                                     
            0                    0                    65560                
            Query_PSM_Concurrent_Execute                                      
            0                    0                    0                    
            SYSTEM                                                            
            0                    0                    32                   
            Storage_Disk_Collection                                           
            0                    0                    0                    
            Storage_Disk_Index                                                
            0                    0                    0                    
            Thread_Stack                                                      
            0                    0                    0                    
            Timer_Manager                                                     
            0                    0                    0                    
            Transaction_DiskPage_Touched_List                                 
            0                    0                    0                    
            Transaction_Table                                                 
            0                    0                    0                    
            Transaction_Table_Info                                            
            0                    0                    0                    
            ...

    -   **예상 결과**

            아래는 정상적인 출력의 예입니다.
            iSQL> SELECT * FROM V$MEMSTAT;
            ...
            External_Procedure                                                
            120528               2                    120528               
            Fixed_Table                                                       
            983400               15                   1048960              
            GIS_Disk_Index                                                    
            263000               9                    263000               
            Mathematics                                                       
            2210568              623                  2210568              
            Query_Common                                                      
            265632               37                   331192               
            Query_Execute                                                     
            196712               3                    262272               
            Query_PSM_Concurrent_Execute                                      
            216                  3                    216                  
            SYSTEM                                                            
            40635264             2738                 40635296             
            Storage_Disk_Collection                                           
            33000                3                    33000                
            Storage_Disk_Index                                                
            1149496              29                   1149496              
            Thread_Stack                                                      
            304087040            29                   304087040            
            Timer_Manager                                                     
            80                   1                    80                   
            Transaction_DiskPage_Touched_List                                 
            66392                9                    66392                
            Transaction_Table                                                 
            5669864              1035                 5669864              
            Transaction_Table_Info                                            
            1662976              21504                1662976              
            ...

-   **Workaround**

        아래와 같이 사용자로 로그온하여 Altibase 를 실행합니다.
        1. 사용자로 Windows 로그온
        2. cmd 실행
        3. server restart 명령 수행

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47540  메모리 인덱스의 동시성을 고려하지 않은 자동 통계 정보 수집과정 중 비정상 종료합니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Rare

-   **증상** : 메모리 인덱스에서 통계 정보 자동 수집과정 중 동시성 문제로 비정상 종료가 드물게 발생합니다. 비정상 종료를 유발하는 부분을 분석하여 회피하도록 수정하였습니다.
    
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

### BUG-47577  DDL\_LOCK\_TIMEOUT 시간이 제대로 동작하지 않는 경우가 있습니다

-   **module** : sm

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : DDL\_LOCK\_TIMEOUT 프로퍼티에 설정된 값을 가져오는 함수의 리턴 타입과 DDL\_LOCK 대기 중 다른 타임아웃을 체크하는 루틴의 문제가 있어서 이를 수정했습니다.
    
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

### BUG-47586  ABORT Error Message가 기록되지 않습니다.

-   **module** : id

-   **Category** : Functional Error

-   **재현 빈도** : Frequence

-   **증상** : 서버 비정상종료시 에러코드가 출력되지 않는 경우가 있어 수정합니다.
    
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

### BUG-47576  외부 참조가 있는 subquery unnesting 시에 결과 오류가 납니다.

- **module** : qp

- **Category** : Functional Error

- **재현 빈도** : Always

- **증상** : 외부 참조가 있는 subquery unnesting 시에 결과 오류수정.

- **재현 방법**

  - **재현 절차**

        drop table t1;
        create table t1 ( i1 varchar(30), i2 varchar(30), i3 varchar(40), i4 varchar(30), i5 varchar(30));
        drop table t2;
        create table t2 ( i1 varchar(30), i2 varchar(30), i3 varchar(40), i4 varchar(30), i5 varchar(30));
        insert into t1 select level, level +1, level +2, level +3, level +4 from dual connect by level < 10;
        insert into t1 select level, level +1, level +2, level +3, level +4 from dual connect by level < 10;
        insert into t2 select level, level +1, level +2, level +3, level +4 from dual connect by level < 10;
        insert into t2 select level, level +1, level +2, level +3, level +4 from dual connect by level < 30;
        drop index idx1;
        create index idx1 on t2 ( i1);
        alter session set explain plan = on;
        alter session set trclog_detail_predicate = 1;
        SELECT 
            B.i1
        FROM t1 B
        INNER JOIN t2 C
               ON C.i2 = B.i2
              AND C.i2 IN (SELECT /*+  */MAX(X.i1)
                                          FROM t2 X
                                         WHERE X.i1 < B.i1
                                       );

  - **수행 결과**

        I1
        ----------------------------------
        9
        9
        9
        9
        4 rows selected.

  - **예상 결과**

        No rows selected.

- **Workaround**

      use no_unnest 힌트

- **변경사항**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

### BUG-47600  Update 시 left outer 와 inner join시 같이 사용된 경우 비정상 종료합니다.

-   **module** : qp

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **증상** : Update 시 left outer 와 inner join시 같이 사용된 경우 비정상 종료되는 문제를 수정합니다..
    
-   **재현 방법**

    -   **재현 절차**

            drop table t1;
             drop table t2;
             drop table t3;
             drop table t4;
            create table t1 ( i1 varchar(30), i2 varchar(30), i3 varchar(30), i4 varchar(30), i5 varchar(30) );
            create table t2 ( i1 varchar(30), i2 varchar(30), i3 varchar(30), i4 varchar(30), i5 varchar(30) );
            create table t3 ( i1 varchar(30), i2 varchar(30), i3 varchar(30), i4 varchar(30), i5 varchar(30) );
            create table t4 ( i1 varchar(30), i2 varchar(30), i3 varchar(30), i4 varchar(30), i5 varchar(30) );
            insert into t1  select level, level+1, level+2, level+3, leve+4 from dual connect by level < 10;
            insert into t2  select level, level+1, level+2, level+3, leve+4 from dual connect by level < 10;
            insert into t3  select level, level+1, level+2, level+3, leve+4 from dual connect by level < 10;
            insert into t4  select level, level+1, level+2, level+3, leve+4 from dual connect by level < 10;
            update (  SELECT
                                      A.i1 A_i1,
                                      A.i2 A_i2,
                                      A.i3 A_i3,
                                      A.i4 A_i4,
                                      B.i1 B_i1,
                                      B.i2 B_i2,
                                      C.i1 C_i1,
                                      C.i2 C_i2
                                    FROM t1 A
                                    INNER JOIN t2 B
                                        ON    A.i1 = B.i1
                                        AND  A.i2 = B.i2
                                    LEFT OUTER JOIN t3 C
                                            ON C.i1 = B.i1
                                            AND C.i4  = B.i4
                                   LEFT OUTER JOIN t4 D
                                            ON D.i1 = B.i1
                                            AND D.i4  = B.i4      
                                  ) set A_i1 = B_i1,
                                        A_i2 = C_i2;

    -   **수행 결과**

            [ERR-31455 : Failed to work because an internal exception occurred from an OS.[Contact Altibase's Support Center]]

    -   **예상 결과**

            [ERR-313A4 : Cannot modify a column for a non key-preserved table]

-   **Workaround**

        NO

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

Changes
-------

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 7.1.0.3.3        | 6.5.1                   | 8.7.1        | 7.1.7               | 7.4.5                        |

> Altibase 7.1 패치 버전별 히스토리는 [Version_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7_1_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의
> 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는
> 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

> 패치를 롤백하려는 경우,[메타다운그레이드](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Installation.md#%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9Cmeta-downgrade)를 참고한다.

#### CM protocol Version

통신 프로토콜 버전은 변경되지 않았다.

#### Replication protocol Version

Replication 프로토콜 버전은 변경되지 않았다.

### 프로퍼티

추가/변경/삭제된 프로퍼티 없음.

### 성능 뷰

#### 추가된 성능 뷰

[V$LIBRARY](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_4.md#vlibrary)

[V$PROCINFO](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_4.md#vprocinfo)
