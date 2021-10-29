<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Altibase 7.1.0.3.1 Patch Notes](#altibase-71031-patch-notes)
  - [New Features](#new-features)
    - [BUG-47458  SQL Apply에서 Lob을 지원하도록 수정 합니다.](#bug-47458-sql-apply%EC%97%90%EC%84%9C-lob%EC%9D%84-%EC%A7%80%EC%9B%90%ED%95%98%EB%8F%84%EB%A1%9D-%EC%88%98%EC%A0%95-%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-47489  multiple update, delete 구문의 지원](#bug-47489-multiple-update-delete-%EA%B5%AC%EB%AC%B8%EC%9D%98-%EC%A7%80%EC%9B%90)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-47219  Global 트랜잭션과 이중화를 동시에 사용하면, 이중화 sender 시작시 Hang이 발생할 수 있습니다.](#bug-47219-global-%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98%EA%B3%BC-%EC%9D%B4%EC%A4%91%ED%99%94%EB%A5%BC-%EB%8F%99%EC%8B%9C%EC%97%90-%EC%82%AC%EC%9A%A9%ED%95%98%EB%A9%B4-%EC%9D%B4%EC%A4%91%ED%99%94-sender-%EC%8B%9C%EC%9E%91%EC%8B%9C-hang%EC%9D%B4-%EB%B0%9C%EC%83%9D%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-47472  서버 구동중 이중화 자동시작 단계에서 HANG 이 발생하였습니다.](#bug-47472-%EC%84%9C%EB%B2%84-%EA%B5%AC%EB%8F%99%EC%A4%91-%EC%9D%B4%EC%A4%91%ED%99%94-%EC%9E%90%EB%8F%99%EC%8B%9C%EC%9E%91-%EB%8B%A8%EA%B3%84%EC%97%90%EC%84%9C-hang-%EC%9D%B4-%EB%B0%9C%EC%83%9D%ED%95%98%EC%98%80%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-47474  인덱스 인터널 노드 탐색 중 이미 제거된 var slot에 접근할 경우에 문제가 발생합니다.](#bug-47474-%EC%9D%B8%EB%8D%B1%EC%8A%A4-%EC%9D%B8%ED%84%B0%EB%84%90-%EB%85%B8%EB%93%9C-%ED%83%90%EC%83%89-%EC%A4%91-%EC%9D%B4%EB%AF%B8-%EC%A0%9C%EA%B1%B0%EB%90%9C-var-slot%EC%97%90-%EC%A0%91%EA%B7%BC%ED%95%A0-%EA%B2%BD%EC%9A%B0%EC%97%90-%EB%AC%B8%EC%A0%9C%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-47509  복합 인덱스가 존재할 때 inner join에서 where 구문에 OR 조건의 predicate이 on절의 predicate이 합쳐질때 결과오류가 발생할 수 있습니다.](#bug-47509-%EB%B3%B5%ED%95%A9-%EC%9D%B8%EB%8D%B1%EC%8A%A4%EA%B0%80-%EC%A1%B4%EC%9E%AC%ED%95%A0-%EB%95%8C-inner-join%EC%97%90%EC%84%9C-where-%EA%B5%AC%EB%AC%B8%EC%97%90-or-%EC%A1%B0%EA%B1%B4%EC%9D%98-predicate%EC%9D%B4-on%EC%A0%88%EC%9D%98-predicate%EC%9D%B4-%ED%95%A9%EC%B3%90%EC%A7%88%EB%95%8C-%EA%B2%B0%EA%B3%BC%EC%98%A4%EB%A5%98%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-47516  __PSM\_STATEMENT\_LIST\_COUNT=0 으로 설정시 잘못된 memory를 free하게 됨.](#bug-47516-__psm%5C_statement%5C_list%5C_count0-%EC%9C%BC%EB%A1%9C-%EC%84%A4%EC%A0%95%EC%8B%9C-%EC%9E%98%EB%AA%BB%EB%90%9C-memory%EB%A5%BC-free%ED%95%98%EA%B2%8C-%EB%90%A8)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Altibase 7.1.0.3.1 Patch Notes
==============================

New Features
------------

### BUG-47458  SQL Apply에서 Lob을 지원하도록 수정 합니다.

-   **module** : rp

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **증상** : 이중화 SQL Apply 에서 Lob type을 지원하도록 수정합니다.

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

### BUG-47489  multiple update, delete 구문의 지원

-   **module** : qp
-   **Category** : Enhancement
-   **재현 빈도** : Always
-   **증상** : multiple update, delete 구문을 지원합니다. 자세한 내용은 SQL 매뉴얼- [multiple_delete](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/SQL3.md#delete) , [multiple_update](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/SQL3.md#update) 을 참고하시기 바랍니다.
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
----------

### BUG-47219  Global 트랜잭션과 이중화를 동시에 사용하면, 이중화 sender 시작시 Hang이 발생할 수 있습니다.

-   **module** : dm

-   **Category** : Hang

-   **재현 빈도** : Rare

-   **증상** : 글로벌 트랜잭션과 이중화를 동시에 사용하면, 내부적으로 XA pending 트랜잭션과 이중화 Sender 시작 중 table lock 간에 경합으로 deadlock 발생할 수 있습니다. lock 경합이 발생하지 않도록 수정합니다.
    
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

### BUG-47472  서버 구동중 이중화 자동시작 단계에서 HANG 이 발생하였습니다.

-   **module** : sm

-   **Category** : Hang

-   **재현 빈도** : Impossible

-   **증상** : 서버 재구동 중 이중화가 자동으로 시작되는 시점에 sender
    가 suspend 상태가 되면, V\$LOCK 과  V\$LOCK\_WAIT  정보를 알수가
    없어 문제 분석에 어려움이 있습니다. Sender가 suspend 상태가 되면
    디버깅을 위한 V\$LOCK 과  V\$LOCK\_WAIT 정보를 altibase\_dump.log 에
    남기도록 수정합니다.

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

### BUG-47474  인덱스 인터널 노드 탐색 중 이미 제거된 var slot에 접근할 경우에 문제가 발생합니다.

-   **module** : sm-mem-index

-   **Category** : Assert

-   **재현 빈도** : Rare

-   **증상** : ager를 동시에 다수를 사용하는 경우, 동시성 문제로 인해
    인덱스 인터널 노드 탐색중 탐색대상 row가 ager에 의해 제거되는 경우가
    있습니다.

    이런 경우 내부적으로는 인터널 노드 재탐색을 수행하지만 탐색 대상이
    var cloumn인 경우는 재탐색을 수행하기전 잘못된 slot 접근으로 비정상
    종료가 발생합니다.

    이를 수정하여 탐색대상이 var column인 경우에도 재탐색을 정상적으로
    수행하도록 합니다.

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

### BUG-47509  복합 인덱스가 존재할 때 inner join에서 where 구문에 OR 조건의 predicate이 on절의 predicate이 합쳐질때 결과오류가 발생할 수 있습니다.

-   **module** : qp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : 복합 인덱스가 존재할 때 inner join에서 where 구문에 OR 조건의 predicate이 on절의 predicate이 합쳐질때 결과오류를 수정합니다.
    
- **재현 방법**

  -   **재현 절차**

          drop table t1;
          drop table t2;
          drop table t3;
          drop table t4;
          drop index idx1;
          drop index idx2;
          drop index idx3_1_2;
          drop index idx4;
          create table t1 ( i1 varchar(100), i2 varchar(100), i3 varchar(100));
          create table t2 ( i1 varchar(100), i2 varchar(100), i3 varchar(100));
          create table t3 ( i1 varchar(100), i2 varchar(100), i3 varchar(100));
          create table t4 ( i1 varchar(100), i2 varchar(100), i3 varchar(100));
          insert into t1 values ( '1', '1', '1');
          insert into t1 values ( '2', '2', '2');
          insert into t1 values ( '3', '3', '3');
          insert into t2 values ( '1', '1', '1');
          insert into t2 values ( '2', '2', '2');
          insert into t2 values ( '3', '3', '3');
          insert into t3 values ( '1', '1', '1');
          insert into t3 values ( '2', '2', '2');
          insert into t3 values ( '3', '3', '3');
          insert into t4 values ( '1', '1', '1');
          insert into t4 values ( '2', '2', '2');
          insert into t4 values ( '3', '3', '3');
          create index idx1 on t1(i1);
          create index idx2 on t2(i1);
          create index idx3_1_2 on t3(i1,i2);
          create index idx4 on t4(i1);
          var p1 char(10);
          exec :p1 := NULL;
          
          prepare select /*+ USE_INDEX_NL( t2, t3 ) */ count(*) cnt from t2 inner join t3 on t2.i1 = t3.i1 where (t3.i2 = :p1 or :p1 is null);
      
  - **수행 결과**

        CNT
        -----------------------
        0
        1 row selected.

  -   **예상 결과**

          CNT
          -----------------------
          3
          1 row selected.

-   **Workaround**

        prepare select /*+ USE_INDEX_NL( t3, t2 ) */ count(*) cnt from t2 inner join t3 on t2.i1 = t3.i1 where (t3.i2 = :p1 or :p1 is null);

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47516  __PSM\_STATEMENT\_LIST\_COUNT=0 으로 설정시 잘못된 memory를 free하게 됨.

-   **module** : qp

-   **Category** : Memory Error

-   **재현 빈도** : Always

-   **증상** : PSM_STATEMENT_LIST 관련 메모리 이슈에 대한 예외처리를 추가하였습니다.

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
-------

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 7.1.0.3.1        | 6.5.1                   | 8.7.1        | 7.1.7               | 7.4.5                        |

> Altibase 7.1 패치 버전별 히스토리는 [Version_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7_1_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의
> 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는
> 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

> 패치를 롤백하려는 경우, [메타다운그레이드](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Installation.md#%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9Cmeta-downgrade)를 참고한다.

#### CM protocol Version

통신 프로토콜 버전은 변경되지 않았다.

#### Replication protocol Version

Replication 프로토콜 버전은 변경되지 않았다.

### 프로퍼티

추가/변경/삭제된 프로퍼티 없음.

### 성능 뷰

추가/변경/삭제된 성능뷰 없음.
