# Altibase 7.3.0.1.3 Patch Notes

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-51467 서버 비정상 종료시 altibase_error.log에 콜스택 외 클라이언트 정보를 출력하도록 개선](#bug-51467)
    - [BUG-51698 암호 관리를 위한 신규 유틸리티 altiEncrypt 추가](#bug-51698)
    - [BUG-51864 Altibase Connector for Kafka(Altibase 커넥터) 제공](#bug-51864)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-50945 SUBSTR 함수 내에서 EMPTY_CLOB()가 인자로 사용될 경우, [ERR-01003 : Unexpected end of string] 오류가 발생합니다.](#bug-50945)
    - [BUG-50976 CLOB 컬럼에 대한 MERGE INTO 구문 수행시 잘못된 값이 입력됩니다.](#bug-50976)
    - [BUG-51015 GROUP_SORT 힌트를 사용한 특정 조건에서 스칼라 서브쿼리와 GROUP BY 및 ORDER BY를 함께 사용하는 쿼리 수행시 발생하던 결과 오류를 수정](#bug-51015)
    - [BUG-51540 VARIABLE 컬럼을 포함한 메모리 인덱스 AGING이 실패할 수 있습니다.](#bug-51540)
    - [BUG-51804 VARIABLE 컬럼을 포함한 메모리 테이블 생성 후(FLUSH 이전 단계에서) 서버가 강제 종료될 경우, 예기치 않은 동작이 발생할 수 있는 문제를 수정합니다.](#bug-51804)
    - [BUG-51834 V$DISK_TEMP_STAT.TBS_ID 값이 모두 0 으로 조회됩니다.](#bug-51834)
    - [BUG-51841 ALA_SENDER_REPLICATION_PORT가 설정된 JDBCAdapter 환경에서 이중화 시작 과정 중 발생하던 교착(DeadLock) 유사 대기 현상을 개선](#bug-51841)
    - [BUG-51849 ANTI JOIN의 INVERSE HASH PLAN에서 잘못 적용된 CONSTANT FILTER로 인한 결과 오류 수정](#bug-51849)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# New Features


### BUG-51467<a name=bug-51467></a> 서버 비정상 종료시 altibase_error.log에 콜스택 외 클라이언트 정보를 출력하도록 개선

-   **module** : mm

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : 서버 비정상 종료시 altibase_error.log에 콜스택 외 클라이언트 정보를 출력하도록 개선합니다. 
    
    - CliPkgVer: 클라이언트 버전 
    
    - CliProtoVer: 클라이언트 통신 프로토콜 버전 
    
    - CliType: 클라이언트 타입
    
    - AppInfo: 어플리케이션 정보
    
      ```bash
      기존 콜스택 정보 아래에 추가로 출력됩니다.
      
      BEGIN-DUMP Diagnostic Information ===============
          Statement: 00007F75D24A9808                  
          Session: 000000000A22F148                    
              CliPkgVer: 7.4.0.0.0                     
              CliProtoVer: 7.1.9                       
              CliType: CLI-64LE                        
              AppInfo: isql                                
          Task: 000000000A16EF00                       
          Link: 00007F74E0000990                       
              ConnType: 1                              
      END-DUMP Diagnostic Information =================
      ```
    
- **재현 방법**

  -   **재현 절차**

  -   **수행 결과**

  -   **예상 결과**

- **Workaround**

- **변경사항**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

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

### BUG-51864<a name=bug-51864></a> Altibase Connector for Kafka(Altibase 커넥터) 제공

-   **module** : rp-kafkaConnector
-   **Category** : Other
-   **재현 빈도** : Always
-   **설명** : Confluent JDBC connector 프로토콜 호환성을 가진 Altibase connector for Kafka(이하 Altibase 커넥터)가 개발되었습니다. Altibase 커넥터를 사용하면 Kafka를 통해 Altibase의 변경 데이터를 다른 데이터베이스로 복제하거나, 다른 데이터베이스의 변경 데이터를 Altibase로 복제할 수 있습니다. Altibase 커넥터는 다음 두 종류의 커넥터로 구성됩니다.
    -   **Altibase 소스 커넥터**: Altibase의 변경 데이터를 Kafka로 스트리밍하여 다른 데이터베이스로 복제
    
    -   **Altibase 싱크 커넥터**: Kafka를 통해 수신한 다른 데이터베이스의 변경 데이터를 Altibase 및 기타 지원 싱크 데이터베이스로 적용
    
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

### BUG-50945<a name=bug-50945></a> SUBSTR 함수 내에서 EMPTY_CLOB()가 인자로 사용될 경우, [ERR-01003 : Unexpected end of string] 오류가 발생합니다.

-   **module** : mt-function

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : SUBSTR 함수 내에서 EMPTY_CLOB()가 인자로 사용될 경우 발생하던 [ERR-01003 : Unexpected end of string] 오류를 수정합니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    SELECT substr( empty_clob(), 1, 1 ) FROM dual;
    ```

  - **수행 결과**

    ```sql
    [ERR-01003 : Unexpected end of string]
    ```

  -   **예상 결과**

      ```sql
      iSQL> SELECT SUBSTR( EMPTY_CLOB(), 1, 1 ) FROM dual;
      SUBSTRB(EMPTY_CLOB(),1,1)
      -----------------------------
      1 row selected.
      ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50976<a name=bug-50976></a> CLOB 컬럼에 대한 MERGE INTO 구문 수행시 잘못된 값이 입력됩니다.

-   **module** : qp-dml-pvo

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : CLOB 컬럼에 대한 MERGE INTO 구문을 수행할 경우, 잘못된 값이 입력되는 문제를 수정합니다.
    
- **재현 방법**

  -   **재현 절차**

          drop table t1;
          drop table t2;
          create table t1( i1 clob, i2 clob );
          create table t2( i1 clob, i2 clob );
          insert into t1 values( '1', '1' );
          insert into t2 values( '1', '1' );
          insert into t2 values( '22', null);
          merge into t1 using t2 on (length(t1.i1) = length(t2.i1))
          when matched then
          update set t1.i2 = t1.i2 || t2.i2
          when not matched then
          insert (i1,i2) values (t2.i1, t2.i2);
          select i1 from t1;

  - **수행 결과**

    ```sql
    I1
    -----------------------------------------------------------------------------------
    1
    2 rows selected.
    ```

  -   **예상 결과**

      ```sql
      I1
      -----------------------------------------------------------------------------------
      1
      22
      2 rows selected.
      ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-51015<a name=bug-51015></a> GROUP_SORT 힌트를 사용한 특정 조건에서 스칼라 서브쿼리와 GROUP BY 및 ORDER BY를 함께 사용하는 쿼리 수행시 발생하던 결과 오류를 수정

-   **module** : qp-dml-pvo

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : GROUP_SORT 힌트를 사용한 특정 조건에서 스칼라 서브쿼리와 GROUP BY 및 ORDER BY 를 함께 사용하는 쿼리 수행 시 발생하던 결과 오류를 수정했습니다. 이 버그는 아래의 조건을 만족할 경우에만 발생합니다.
    - SELECT구문의 타겟절에 스칼라 서브쿼리를 사용
    - 스칼라 서브쿼리의 alias가 상위 쿼리의 집계 함수와 ORDER BY절에서 사용될 때
    - 실행 계획을 GROUP_SORT로 지정했을 때
    
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

### BUG-51540<a name=bug-51540></a> VARIABLE 컬럼을 포함한 메모리 인덱스 AGING이 실패할 수 있습니다.

-   **module** : sm

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : VARIABLE 컬럼을 포함하는 메모리 인덱스가 있을때, 메모리 인덱스 AGING 이 실패하는 문제를 수정했습니다.

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

### BUG-51804<a name=bug-51804></a> VARIABLE 컬럼을 포함한 메모리 테이블 생성 후(FLUSH 이전 단계에서) 서버가 강제 종료될 경우, 예기치 않은 동작이 발생할 수 있는 문제를 수정합니다.

-   **module** : sm

-   **Category** : Other

-   **재현 빈도** : Always

-   **설명** : VARIABLE 컬럼을 포함한 메모리 테이블 생성 후 (FLUSH 이전 단계에서) 서버가 강제 종료될 경우, 예기치 않은 동작이 발생할 수 있는 문제를 수정합니다.

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

### BUG-51834<a name=bug-51834></a> V$DISK_TEMP_STAT.TBS_ID 값이 모두 0 으로 조회됩니다.

-   **module** : sm
-   **Category** : Functional Error
-   **재현 빈도** : Always
-   **설명** : V$DISK_TEMP_STAT.TBS_ID 값이 0으로 조회되는 오류를 수정했습니다.
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

### BUG-51841<a name=bug-51841></a> ALA_SENDER_REPLICATION_PORT가 설정된 JDBCAdapter 환경에서 이중화 시작 과정 중 발생하던 교착(DeadLock) 유사 대기 현상을 개선

-   **module** : rp-ala

-   **Category** : Hang

-   **재현 빈도** : Frequence

-   **설명** : ALA_SENDER_REPLICATION_PORT가 설정된 JDBCAdapter 환경에서 이중화 시작 과정 중 발생하던 교착(DeadLock) 유사 대기 현상을 개선했습니다. 또한 이중화 handshake 시 ack를 기다리는데 사용되는 프로퍼티를 REPLICATION_RECEIVE_TIMEOUT 에서  REPLICATION_CONNECT_TIMEOUT으로 변경합니다.
    -   변경 전: REPLICATION_RECEIVE_TIMEOUT (기본값 7200초)
    -   변경 후: REPLICATION_CONNECT_TIMEOUT (기본값 10초)

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
| 7.3.0.1.3        | 7.3.0                   | 9.4.1        | 7.1.8               | 7.4.9                        |

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
