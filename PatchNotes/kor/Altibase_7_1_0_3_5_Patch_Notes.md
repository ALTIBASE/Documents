<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Altibase 7.1.0.3.5 Patch Notes](#altibase-71035-patch-notes)
  - [New Features](#new-features)
    - [BUG-47648  disk partition에서 사용되는 prepared memory 사용량 개선](#bug-47648-disk-partition%EC%97%90%EC%84%9C-%EC%82%AC%EC%9A%A9%EB%90%98%EB%8A%94-prepared-memory-%EC%82%AC%EC%9A%A9%EB%9F%89-%EA%B0%9C%EC%84%A0)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-45803  eager replication 중인 table에 ALTER TABLE ... RENAME CONSTRAINT 의 DDL이 실패하지 않는 문제가 있습니다.](#bug-45803-eager-replication-%EC%A4%91%EC%9D%B8-table%EC%97%90-alter-table--rename-constraint-%EC%9D%98-ddl%EC%9D%B4-%EC%8B%A4%ED%8C%A8%ED%95%98%EC%A7%80-%EC%95%8A%EB%8A%94-%EB%AC%B8%EC%A0%9C%EA%B0%80-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-47618  logical ager 에서 key를 찾지 못하였을 때 예외 처리 강화](#bug-47618-logical-ager-%EC%97%90%EC%84%9C-key%EB%A5%BC-%EC%B0%BE%EC%A7%80-%EB%AA%BB%ED%95%98%EC%98%80%EC%9D%84-%EB%95%8C-%EC%98%88%EC%99%B8-%EC%B2%98%EB%A6%AC-%EA%B0%95%ED%99%94)
    - [BUG-47655  TRANSACTION\_TABLE\_SIZE 부족 오류 메시지 수정](#bug-47655-transaction%5C_table%5C_size-%EB%B6%80%EC%A1%B1-%EC%98%A4%EB%A5%98-%EB%A9%94%EC%8B%9C%EC%A7%80-%EC%88%98%EC%A0%95)
    - [BUG-47659  SET\_COLUMN\_STATS 사용시 작은 따옴표( ' ) 포함된 경우 error 발생합니다.](#bug-47659-set%5C_column%5C_stats-%EC%82%AC%EC%9A%A9%EC%8B%9C-%EC%9E%91%EC%9D%80-%EB%94%B0%EC%98%B4%ED%91%9C---%ED%8F%AC%ED%95%A8%EB%90%9C-%EA%B2%BD%EC%9A%B0-error-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Altibase 7.1.0.3.5 Patch Notes
==============================

New Features
------------

### BUG-47648  disk partition에서 사용되는 prepared memory 사용량 개선

-   **module** : qp

-   **Category** : Efficiency

-   **재현 빈도** : Always

-   **증상** : disk partition에서 사용되는 prepared memory 사용량 개선

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

### BUG-45803  eager replication 중인 table에 ALTER TABLE ... RENAME CONSTRAINT 의 DDL이 실패하지 않는 문제가 있습니다.

-   **module** : rp

-   **Category** : Other

-   **재현 빈도** : Always

-   **증상** : eager replication 중인 table에 ALTER TABLE ... RENAME
    CONSTRAINT 의 DDL 구문이 실패해야 하는데, 수행되는 문제를
    수정합니다. 내부적으로 rename constraint 시에 replication 여부를
    확인하는 로직이 누락되어있어, 수정하였습니다.

-   **재현 방법**

    -   **재현 절차**

            eager replication 생성ALTER TABLE T1 RENAME CONSTRAINT T1_FK TO T1_FK_RE;

    -   **수행 결과**

            Alter success.

    -   **예상 결과**

            [ERR-31324 : Cannot execute DDL statements on a replicated table while replication is running in eager mode.]

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47618  logical ager 에서 key를 찾지 못하였을 때 예외 처리 강화

-   **module** : sm-mem-index

-   **Category** : Fatal

-   **재현 빈도** : Rare

-   **증상** : logical ager 에서 내부적으로 key를 찾지 못해 비정상
    종료하는 문제가 있어, 이를 회피하도록 예외처리를 보강하였습니다.

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

### BUG-47655  TRANSACTION\_TABLE\_SIZE 부족 오류 메시지 수정

-   **module** : sm\_transaction

-   **Category** : Message Error

-   **재현 빈도** : Frequence

-   **증상** : TRANSACTION_TABLE_SIZE가 FULL이 아닌경우에도 TRANSACTION_TABLE_SIZE_FULL 오류가 출력되는 경우가 있어서, 수정합니다.
    
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

### BUG-47659  SET\_COLUMN\_STATS 사용시 작은 따옴표( ' ) 포함된 경우 error 발생합니다.

-   **module** : qp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** :  SET\_COLUMN\_STATS 사용시 작은 따옴표( ' ) 포함된 경우 error가 발생하지 않도록 수정합니다.
    
- **재현 방법**

  -   **재현 절차**

          drop table t1;
          create table t1 ( i1 varchar(200));
          insert into t1 values ('111 ''222'' 333 ');
          EXEC SET_COLUMN_STATS('"SYS"', '"T1"', '"I1"', NULL, 1, 0, 16, '111 ''222'' 333 ', '111 ''222'' 333 ');

  - **수행 결과**

        EXEC SET_COLUMN_STATS('"SYS"', '"T1"', '"I1"', NULL, 1, 0, 16, '111 ''222'' 333 ', '111 ''222'' 333 ');
        [ERR-21011 : Invalid literal]

  -   **예상 결과**

          Execute success.

-   **Workaround**

        EXEC SET_COLUMN_STATS('"SYS"', '"T1"', '"I1"', NULL, 1, 0, 16, '111 ''''222'''' 333 ', '111 ''''222'''' 333 ');

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
| 7.1.0.3.5        | 6.5.1                   | 8.7.1        | 7.1.7               | 7.4.5                        | 2.2.1            |

> Altibase 7.1 패치 버전별 히스토리는 [Version_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7_1_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의
> 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는
> 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

> 패치를 롤백하려는 경우,
> [메타다운그레이드](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Installation.md#%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9Cmeta-downgrade)를
> 참고한다.

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