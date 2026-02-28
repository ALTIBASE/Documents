Altibase 7.3.0.1.5 Patch Notes
==============================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-51873 Altibase Connector for Kafka에 자동 재시작 기능이 추가되었습니다.](#bug-51873)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-50643 LOB 컬럼이 포함된 테이블의 SYNC 작업 중 특정 레코드에서 충돌(Conflict)이 발생 할 경우, 직전에 입력된 레코드의 마지막 LOB 컬럼값이 NULL로 변경되는 문제를 수정했습니다.](#bug-50643)
    - [BUG-51888 dblink, aku, Adapter에서 사용하는 암호화된 PASSWORD의 최대 허용 길이를 256자로 확장하였습니다.](#bug-51888)
    - [BUG-51977 SQLDriverConnectW()에서 접속이 실패했는데 SQL\_SUCCESS\_WITH\_INFO를 리턴하는 오류를 수정해야 합니다.](#bug-51977)
    - [BUG-51989 디스크 테이블에 인덱스가 존재하는 환경에서 Multiple Table Update 를 수행할 경우, 일부 행이 갱신되지 않는 문제를 수정하였습니다.](#bug-51989)
    - [BUG-51992 Row TimeStamping 이 실패 시 진단 정보를 altibase_dump.log 에 기록하도록 수정합니다.](#bug-51992)
    - [BUG-51994 중첩된 Left Outer Join 구문 수행 시 일부 결과가 누락되는 결과 오류를 수정하였습니다.](#bug-51994)
    - [BUG-52002 SQL_APPLY 모드로 SYNC 수행 중 충돌 발생 시, 레코드 갱신 처리 중 비정상 종료가 발생합니다.](#bug-52002)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-51873<a name=bug-51873></a> Altibase Connector for Kafka에 자동 재시작 기능이 추가되었습니다.

-   **module** :

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : Altibase source connector for Kafka에 DDL 메시지 수신 시
    자동 재시작 기능이 추가되었습니다. 이 기능을 사용하려면 `restart.ddl` 프로퍼티의 값을 true로 설정해야 합니다.(기본값은 false)

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

### BUG-50643<a name=bug-50643></a> LOB 컬럼이 포함된 테이블의 SYNC 작업 중 특정 레코드에서 충돌(Conflict)이 발생 할 경우, 직전에 입력된 레코드의 마지막 LOB 컬럼값이 NULL로 변경되는 문제를 수정했습니다.

-   **module** : rp
-   **Category** : Functional Error
-   **재현 빈도** : Always
-   **설명** : LOB 컬럼이 포함된 테이블의 SYNC 작업 중 특정 레코드에서 충돌(Conflict)이 발생 할 경우, 직전에 입력된 레코드의 마지막 LOB 컬럼값이 NULL로 변경되는 문제를 수정했습니다. 이 현상은 첫 번째 레코드에서 충돌이 발생한 경우에는 발생하지 않으며, 두 번째 이후의 레코드에서 충돌이 발생할 경우에만 재현되었으며, 이번 패치 적용으로 더이상 발생하지 않습니다.
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

### BUG-51888<a name=bug-51888></a> dblink, aku, Adapter에서 사용하는 암호화된 PASSWORD의 최대 허용 길이를 256자로 확장하였습니다.

-   **module** : rp

-   **Category** : Testcase Error

-   **재현 빈도** : Always

-   **설명** : dblink, aku, Adapter에서 사용하는 암호화 PASSWORD의 최대 허용 길이를 256자로 변경합니다. 참고로, altiEncryt는 최대 128자 길이의 암호 입력을 지원하며, 이를 256자 길이의 암호화 PASSWORD로 생성합니다.
    
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

### BUG-51977<a name=bug-51977></a> SQLDriverConnectW()에서 접속이 실패했는데 SQL\_SUCCESS\_WITH\_INFO를 리턴하는 오류를 수정해야 합니다.

-   **module** : mm-cli

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : SQLDriverConnectW()함수를 호출할 때 InConnectionString 인자에 유효하지 않은 IP 주소가 포함되어 있고, BufferLength 인자에 16과 같이 작은 값을 전달할 경우, 접속이 실패해야 하는데 `SQL_SUCCESS_WITH_INFO`가 반환되는 문제를 수정합니다.
    
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

### BUG-51989<a name=bug-51989></a> 디스크 테이블에 인덱스가 존재하는 환경에서 Multiple Table Update 를 수행할 경우, 일부 행이 갱신되지 않는 문제를 수정하였습니다.

-   **module** : sm\_index

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 디스크 테이블에 인덱스가 존재하는 환경에서 Multiple Table Update 를 수행할 경우, 일부 행이 갱신되지 않는 문제를 수정하였습니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    drop table t1;
    drop table t2;
    create table t1 ( i1 varchar(40), i2 varchar(10), SBI_ORDER_ID varchar(10) ) tablespace sys_tbs_disk_data;
    create index idx1 on t1 ( SBI_ORDER_ID );
    create table t2 ( i1 varchar(40), SBI_ORDER_ID varchar(10) ) tablespace sys_tbs_disk_data;
    create index idx2 on t2 ( SBI_ORDER_ID );
    
    insert into t1 select level, 10, '6000000077' from dual connect by level < 3;
    insert into t2 select level, '6000000077' from dual connect by level < 3;
    
    update t1 a, t2 b set a.i1 = 'AA', b.i1 = 'BB' where A.SBI_ORDER_ID = B.SBI_ORDER_ID and a.SBI_ORDER_ID = '6000000077';
    ```

  - **수행 결과**

        3 rows updated.

  -   **예상 결과**

          4 rows updated.

-   **Workaround**

        NO INDEX

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-51992<a name=bug-51992></a> Row TimeStamping 이 실패 시 진단 정보를 altibase_dump.log 에 기록하도록 수정합니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Unknown

-   **설명** : Row TimeStamping 이 실패하는 경우, 분석을 위한 진단 정보를 altibase_dump.log 에 기록합니다.

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

### BUG-51994<a name=bug-51994></a> 중첩된 Left Outer Join 구문 수행 시 일부 결과가 누락되는 결과 오류를 수정하였습니다.

-   **module** : qp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 중첩된 Left Outer Join 구문 수행 시 Join predicate 처리 오류로 인해, 일부 결과가 누락될 수 있는 문제를 수정하였습니다.

- **재현 방법**

  - **재현 절차**

    ```sql
    drop table t1;
    drop table t2;
    drop table t3;
    drop table t4;
    
    create table t1 (c1 integer primary key, c2 char(10), c3 char(10));
    create table t2 (c1 integer primary key, c2 char(10), c3 char(10));
    create table t3 (c1 integer primary key, c2 char(10), c3 char(10));
    create table t4 (c1 integer primary key, c2 char(10), c3 char(10));
    insert into t1 values (1,1,null);
    insert into t2 values (1,1,24);
    insert into t4 values (1,1,24);
    
    select t2.*, t3.*, t4.* from t1
              left outer join  t2 on t1.c1 = t2.c1
              left outer join  t3 on t1.c1 = t3.c1
              left outer join  t4 on
              (t4.c2=t3.c2 and t4.c3 = t3.c3)
              or
              (t4.c2=t2.c2 and t4.c3 = t2.c3)
              ;
    ```

  -   **수행 결과**

          C1          C2          C3          C1          C2          C3
          -------------------------------------------------------------------------------
          C1          C2          C3
          ----------------------------------------
          1           1           24
          1 row selected.
      
  -   **예상 결과**

          C1          C2          C3          C1          C2          C3
          -------------------------------------------------------------------------------
          C1          C2          C3
          ----------------------------------------
          1           1           24
          1           1           24
          1 row selected.

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-52002<a name=bug-52002></a> SQL\_APPLY 모드로 SYNC 수행 중 충돌 발생 시, 레코드 갱신 처리 중 비정상 종료가 발생합니다.

-   **module** : rp

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : SQL\_APPLY 모드로 SYNC 수행 중 충돌 발생 시, 충돌 해결
    정책에 따라 레코드 갱신이 이루어질 경우, 서버가 비정상적으로
    종료되는 현상을 수정했습니다.

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
| 7.3.0.1.5        | 7.3.0                   | 9.4.1        | 7.1.8               | 7.4.9                        |

> Altibase 7.3 패치 버전별 히스토리는 [Version_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.3/Altibase_7_3_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의
> 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는
> 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

> 패치를 롤백하려는 경우,
> [메타다운그레이드](https://manual.altibase.com/7.3/start-here/install/3.-Uninstalling-Altibase-and-Meta-Downgrade/#%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9Cmeta-downgrade)를
> 참고한다.

#### CM protocol Version

통신 프로토콜 버전은 변경되지 않았다.

#### Replication protocol Version

Replication 프로토콜 버전은 변경되지 않았다.

### 프로퍼티

추가/변경/삭제된 프로퍼티 없음.

### 성능 뷰

추가/변경/삭제된 성능뷰 없음.
