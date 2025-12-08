# Altibase 7.1.0.10.6 Patch Notes

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [New Features](#new-features)
    - [BUG-51698 암호 관리를 위한 신규 유틸리티 altiEncrypt 추가](#bug-51698)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-51015 GROUP_SORT 힌트를 사용한 특정 조건에서 스칼라 서브쿼리와 GROUP BY 및 ORDER BY를 함께 사용하는 쿼리 수행시 발생하던 결과 오류를 수정](#bug-51015)
    - [BUG-51834 V\$DISK\_TEMP\_STAT.TBS\_ID 값이 모두 0 으로 조회됩니다.](#bug-51834)
    - [BUG-51841 ALA_SENDER_REPLICATION_PORT가 설정된 JDBCAdapter 환경에서 이중화 시작 과정 중 발생하던 교착(DeadLock) 유사 대기 현상을 개선](#bug-51841)
    - [BUG-51849 ANTI JOIN의 INVERSE HASH PLAN에서 잘못 적용된 CONSTANT FILTER로 인한 결과 오류 수정](#bug-51849)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-51698<a name=bug-51698></a> 암호 관리를 위한 신규 유틸리티 altiEncrypt 추가

-   **module** : rp

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : altiEncrypt 를 이용하여 dblink, aku, Adapter 의 Conf 파일에 PASSWORD를 암호화하여 설정 할 수 있도록 개선되었습니다. 암호화된 PASSWORD 사용으로 비밀번호 보안을 개선했습니다.

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

### BUG-51015<a name=bug-51015></a> GROUP_SORT 힌트를 사용한 특정 조건에서 스칼라 서브쿼리와 GROUP BY 및 ORDER BY를 함께 사용하는 쿼리 수행시 발생하던 결과 오류를 수정

-   **module** : qp-dml-pvo
-   **Category** : Functional Error
-   **재현 빈도** : Always
-   **설명** : GROUP_SORT 힌트를 사용한 특정 조건에서 스칼라 서브쿼리와 GROUP BY 및 ORDER BY 를 함께 사용하는 쿼리 수행 시 발생하던 결과 오류를 수정했습니다. 이 버그는 아래의 조건을 만족할 경우에만 발생합니다.
    -   SELECT구문의 타겟절에 스칼라 서브쿼리를 사용
    -   스칼라 서브쿼리의 alias가  상위 쿼리의 집계 함수와 ORDER BY절에서 사용될 때
    -   실행 계획을 GROUP_SORT로 지정했을 때
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

### BUG-51834<a name=bug-51834></a> V\$DISK\_TEMP\_STAT.TBS\_ID 값이 모두 0 으로 조회됩니다.

-   **module** : sm

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : V\$DISK\_TEMP\_STAT.TBS\_ID 값이 0으로 조회되는 오류를 수정했습니다.

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

### BUG-51841<a name=bug-51841></a> ALA_SENDER_REPLICATION_PORT가 설정된 JDBCAdapter 환경에서 이중화 시작 과정 중 발생하던 교착(DeadLock) 유사 대기 현상을 개선

-   **module** : rp-ala

-   **Category** : Hang

-   **재현 빈도** : Frequence

-   **설명** : ALA_SENDER_REPLICATION_PORT가 설정된 JDBCAdapter 환경에서 이중화 시작 과정 중 발생하던 교착(DeadLock) 유사 대기 현상을 개선했습니다. 또한 이중화 handshake 시 ack를 기다리는데 사용되는 프로퍼티를 REPLICATION\_RECEIVE_TIMEOUT 에서  REPLICATION\_CONNECT\_TIMEOUT으로 변경합니다.
    - 변경 전: REPLICATION\_RECEIVE_TIMEOUT (기본값 7200초)
    
    - 변경 후: REPLICATION\_CONNECT\_TIMEOUT (기본값 10초)
    
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

### BUG-51849<a name=bug-51849></a> ANTI JOIN의 INVERSE HASH PLAN에서 잘못 적용된 CONSTANT FILTER로 인한 결과 오류 수정

-   **module** : qp-dml-pvo

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : ANTI JOIN에서 INVERSE HASH 방식으로 PLAN 생성 시, CONSTANT FILTER가 잘못 적용되어 결과 오류가 발생하던 문제를 수정했습니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    drop table t1;
    drop table t2;
    create table t1(i1 integer , i2 integer);
    create index t1_i2_idx on t1(i2);
    create table t2(i1 integer, i2 integer);
    create index t2_i2_idx on t2(i2);
    insert into t1 select level, mod(level, 10)+1 from dual connect by level <= 100;
    insert into t1 values (999, 999);
    insert into t1 values (1000, null);
    insert into t2 select level, level+1 from dual connect by level <= 20;
    insert into t2 values (99, 99);
    insert into t2 values (100, null);
    drop table t3;
    create table t3 (i1 integer, i2 integer);
    SELECT * from (
    SELECT t1.*
      FROM t1
     WHERE 'N' = 'Y' AND NOT EXISTS (SELECT  /*+ INVERSE_JOIN */  1
                         FROM t2
                        WHERE t2.i1 = t1.i2)) X
    LEFT OUTER JOIN ( SELECT * FROM T3 ) Y ON X.i1 = Y.i1;
    ```

  -   **수행 결과**

          102 rows selected.

  -   **예상 결과**

          No rows selected.

-   **Workaround**

        NO_INVERSE_JOIN hint 사용

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
| 7.1.0.10.6       | 6.5.1                   | 8.12.1       | 7.1.7               | 7.4.7                        |

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

추가/변경/삭제된 프로퍼티 없음.

### 성능 뷰

추가/변경/삭제된 성능뷰 없음.
