<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Altibase 7.1.0.3.4 Patch Notes](#altibase-71034-patch-notes)
  - [New Features](#new-features)
    - [BUG-47608  iloader로 특정 샤드노드에 데이터를 in/out 하기 위한 옵션(-stmt_prefix)을 제공합니다.](#bug-47608-iloader%EB%A1%9C-%ED%8A%B9%EC%A0%95-%EC%83%A4%EB%93%9C%EB%85%B8%EB%93%9C%EC%97%90-%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%A5%BC-inout-%ED%95%98%EA%B8%B0-%EC%9C%84%ED%95%9C-%EC%98%B5%EC%85%98-stmt_prefix%EC%9D%84-%EC%A0%9C%EA%B3%B5%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-47614  partition table insert시 optimize 성능 개선](#bug-47614-partition-table-insert%EC%8B%9C-optimize-%EC%84%B1%EB%8A%A5-%EA%B0%9C%EC%84%A0)
    - [BUG-47625  Insert execution 성능 개선](#bug-47625-insert-execution-%EC%84%B1%EB%8A%A5-%EA%B0%9C%EC%84%A0)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-46001  eager replication 에서 alter tablespace 수행 시 partitioned table 에 대한 고려가 되어있지 않습니다.](#bug-46001-eager-replication-%EC%97%90%EC%84%9C-alter-tablespace-%EC%88%98%ED%96%89-%EC%8B%9C-partitioned-table-%EC%97%90-%EB%8C%80%ED%95%9C-%EA%B3%A0%EB%A0%A4%EA%B0%80-%EB%90%98%EC%96%B4%EC%9E%88%EC%A7%80-%EC%95%8A%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-46545  이중화에서 statement end 실패시, 예외처리에서 failure 처리(statement end 수행)를 하지 않습니다.](#bug-46545-%EC%9D%B4%EC%A4%91%ED%99%94%EC%97%90%EC%84%9C-statement-end-%EC%8B%A4%ED%8C%A8%EC%8B%9C-%EC%98%88%EC%99%B8%EC%B2%98%EB%A6%AC%EC%97%90%EC%84%9C-failure-%EC%B2%98%EB%A6%ACstatement-end-%EC%88%98%ED%96%89%EB%A5%BC-%ED%95%98%EC%A7%80-%EC%95%8A%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-47615  update inplace 에서 예외 발생시 index key를 정리하다 비정상 종료 합니다.](#bug-47615-update-inplace-%EC%97%90%EC%84%9C-%EC%98%88%EC%99%B8-%EB%B0%9C%EC%83%9D%EC%8B%9C-index-key%EB%A5%BC-%EC%A0%95%EB%A6%AC%ED%95%98%EB%8B%A4-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C-%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-47631  DBLINK 실행시 targetDB에 user의 password의 일부가 잘리는 경우가 있습니다.](#bug-47631-dblink-%EC%8B%A4%ED%96%89%EC%8B%9C-targetdb%EC%97%90-user%EC%9D%98-password%EC%9D%98-%EC%9D%BC%EB%B6%80%EA%B0%80-%EC%9E%98%EB%A6%AC%EB%8A%94-%EA%B2%BD%EC%9A%B0%EA%B0%80-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Altibase 7.1.0.3.4 Patch Notes
==============================

New Features
------------

### BUG-47608  iloader로 특정 샤드노드에 데이터를 in/out 하기 위한 옵션(-stmt_prefix)을 제공합니다.

-   **module** : ux-iloader

-   **Category** : Efficiency

-   **재현 빈도** : Always

-   **증상** : iloader로 특정 샤드 노드에 데이터를 in/out하기 위한 옵션으로 -stmt_prefix 가 추가되었습니다. 자세한 내용은 [iLoader User's Manual -일반옵션]([https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/iLoader.md#%EC%9D%BC%EB%B0%98-%EC%98%B5%EC%85%98](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/iLoader.md#일반-옵션)) 을 참고하시기 바랍니다.

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

### BUG-47614  partition table insert시 optimize 성능 개선

-   **module** : qp

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **증상** : partition table insert시 optimize 성능 개선

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

### BUG-47625  Insert execution 성능 개선

-   **module** : qp

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **증상** : 단순 insert values에 대한  성능개선

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

### BUG-46001  eager replication 에서 alter tablespace 수행 시 partitioned table 에 대한 고려가 되어있지 않습니다.

-   **module** : dm

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : table에 eager replication 이 설정 되어 있으면 DDL을 허용하지 않는데, 
    

partitioned table의 경우 alter tablespace 구문이 실패하지 않지 않고 수행되는 문제가 있어 수정합니다.
    
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

### BUG-46545  이중화에서 statement end 실패시, 예외처리에서 failure 처리(statement end 수행)를 하지 않습니다.

-   **module** : rp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : 이중화에서 statement end가 실패할 경우에 statement end를
    다시 처리 해주어야 하는데, 처리 되지 않는 문제가 있습니다.

    statement end가 실패할 경우에 statement end를 다시 처리하도록 수정하였습니다.
    
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

### BUG-47615  update inplace 에서 예외 발생시 index key를 정리하다 비정상 종료 합니다.

-   **module** : sm-mem-index

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **증상** :

- **재현 방법**

  - **재현 절차**

        drop table T1;
        create table T1 ( idx integer primary key, data integer );
        insert into T1 select rownum, rownum from dual connect by level <=3;
        create index T1X on T1(data);
        autocommit off;
        lock table T1 IN EXCLUSIVE MODE;
        
        update T1 set idx = idx +1 where idx = 1;
        update T1 set idx = idx +1 where idx <= 2;
        commit;

  - **수행 결과**

        iSQL> update T1 set idx = idx +1 where idx = 1;
        [ERR-91015 : Communication failure.]

  -   **예상 결과**

          iSQL> update T1 set idx = idx +1 where idx = 1;
          [ERR-11058 : The row already exists in a unique index.]
          iSQL> update T1 set idx = idx +1 where idx <= 2;
          [ERR-11058 : The row already exists in a unique index.]
          iSQL> commit;
          Commit success.

-   **Workaround**

        LOCK_ESCALATION_MEMORY_SIZE = 1048576000;

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47631  DBLINK 실행시 targetDB에 user의 password의 일부가 잘리는 경우가 있습니다.

-   **module** : dblink

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : DBLINK 실행시 targetDB의 user password를 암호화하여
    Meta에 저장할때 암호화 알고리즘에 문제가 있어서 password의 일부가
    잘리는 경우가 있어 수정합니다.

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

| altibase version | database binary version | meta version | cm protocol version | replication protocol version | sharding version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- | ---------------- |
| 7.1.0.3.4        | 6.5.1                   | 8.7.1        | 7.1.7               | 7.4.5                        | 2.2.1            |

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

#### Sharding Version

샤딩 버전은 변경 되지 않았다.

> 알티베이스 샤딩 프로토콜 및 메타는 상위, 하위 호환성을 보장하지
> 않는다. 즉, 샤딩 버전이 다른 경우, 재구성해야 한다.

### 프로퍼티

추가/변경/삭제된 프로퍼티 없음

### 성능 뷰

추가/변경/삭제된 성능뷰 없음