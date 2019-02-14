<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Altibase 7.1.0.1.8 Patch Notes](#altibase-71018-patch-notes)
  - [New Features](#new-features)
    - [BUG-46174 저장 프로시저내 insert, update 구문에서 레코드 타입변수 사용하도록 기능 확장](#bug-46174-%EC%A0%80%EC%9E%A5-%ED%94%84%EB%A1%9C%EC%8B%9C%EC%A0%80%EB%82%B4-insert-update-%EA%B5%AC%EB%AC%B8%EC%97%90%EC%84%9C-%EB%A0%88%EC%BD%94%EB%93%9C-%ED%83%80%EC%9E%85%EB%B3%80%EC%88%98-%EC%82%AC%EC%9A%A9%ED%95%98%EB%8F%84%EB%A1%9D-%EA%B8%B0%EB%8A%A5-%ED%99%95%EC%9E%A5)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-46120 Active Server와 Standby Server의 해시 파티션드 테이블의 파티션 개수가 다른 경우, 이중화가 실패해야 합니다.](#bug-46120-active-server%EC%99%80-standby-server%EC%9D%98-%ED%95%B4%EC%8B%9C-%ED%8C%8C%ED%8B%B0%EC%85%98%EB%93%9C-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%9D%98-%ED%8C%8C%ED%8B%B0%EC%85%98-%EA%B0%9C%EC%88%98%EA%B0%80-%EB%8B%A4%EB%A5%B8-%EA%B2%BD%EC%9A%B0-%EC%9D%B4%EC%A4%91%ED%99%94%EA%B0%80-%EC%8B%A4%ED%8C%A8%ED%95%B4%EC%95%BC-%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-46396 aexport가 생성하는 DDL 마지막 라인에 덧붙이는 newline으로 인해 iSQL에서 Syntax Error가 발생할 수 있습니다.](#bug-46396-aexport%EA%B0%80-%EC%83%9D%EC%84%B1%ED%95%98%EB%8A%94-ddl-%EB%A7%88%EC%A7%80%EB%A7%89-%EB%9D%BC%EC%9D%B8%EC%97%90-%EB%8D%A7%EB%B6%99%EC%9D%B4%EB%8A%94-newline%EC%9C%BC%EB%A1%9C-%EC%9D%B8%ED%95%B4-isql%EC%97%90%EC%84%9C-syntax-error%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-46515 dumptrc을 사용해서 콜스택 출력시 altibase_error.log의 콜스택이 생략되는 경우가 있어, 이를 수정하였습니다.](#bug-46515-dumptrc%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%B4%EC%84%9C-%EC%BD%9C%EC%8A%A4%ED%83%9D-%EC%B6%9C%EB%A0%A5%EC%8B%9C-altibase_errorlog%EC%9D%98-%EC%BD%9C%EC%8A%A4%ED%83%9D%EC%9D%B4-%EC%83%9D%EB%9E%B5%EB%90%98%EB%8A%94-%EA%B2%BD%EC%9A%B0%EA%B0%80-%EC%9E%88%EC%96%B4-%EC%9D%B4%EB%A5%BC-%EC%88%98%EC%A0%95%ED%95%98%EC%98%80%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-46539 merge 구문에 parser conflicts 발생](#bug-46539-merge-%EA%B5%AC%EB%AC%B8%EC%97%90-parser-conflicts-%EB%B0%9C%EC%83%9D)
    - [BUG-46550 JDBC 드라이버에서 addBatch시에 directByteBuffer 사용시 메모리 증가하는 문제가 있습니다.](#bug-46550-jdbc-%EB%93%9C%EB%9D%BC%EC%9D%B4%EB%B2%84%EC%97%90%EC%84%9C-addbatch%EC%8B%9C%EC%97%90-directbytebuffer-%EC%82%AC%EC%9A%A9%EC%8B%9C-%EB%A9%94%EB%AA%A8%EB%A6%AC-%EC%A6%9D%EA%B0%80%ED%95%98%EB%8A%94-%EB%AC%B8%EC%A0%9C%EA%B0%80-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-46551  jdbcAdapter로 altibase 5.5.1 에 데이터 전송시 ArrayIndexOutOfBoundsException 이 발생하는 경우가 있습니다.](#bug-46551--jdbcadapter%EB%A1%9C-altibase-551-%EC%97%90-%EB%8D%B0%EC%9D%B4%ED%84%B0-%EC%A0%84%EC%86%A1%EC%8B%9C-arrayindexoutofboundsexception-%EC%9D%B4-%EB%B0%9C%EC%83%9D%ED%95%98%EB%8A%94-%EA%B2%BD%EC%9A%B0%EA%B0%80-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-46552 isql에서 /dev/null을 사용하지 않아야 합니다.](#bug-46552-isql%EC%97%90%EC%84%9C-devnull%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%98%EC%A7%80-%EC%95%8A%EC%95%84%EC%95%BC-%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-46567 dumpStack의 동시성 문제 수정](#bug-46567-dumpstack%EC%9D%98-%EB%8F%99%EC%8B%9C%EC%84%B1-%EB%AC%B8%EC%A0%9C-%EC%88%98%EC%A0%95)
    - [BUG-46572 APRE에서 packge를 사용시 psm array가 제대로 인식되지 않습니다.](#bug-46572-apre%EC%97%90%EC%84%9C-packge%EB%A5%BC-%EC%82%AC%EC%9A%A9%EC%8B%9C-psm-array%EA%B0%80-%EC%A0%9C%EB%8C%80%EB%A1%9C-%EC%9D%B8%EC%8B%9D%EB%90%98%EC%A7%80-%EC%95%8A%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-46574 Checkpoint Image 생성 도중에 서버가 비정상 종료되면 재구동에 실패 합니다.](#bug-46574-checkpoint-image-%EC%83%9D%EC%84%B1-%EB%8F%84%EC%A4%91%EC%97%90-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%EB%90%98%EB%A9%B4-%EC%9E%AC%EA%B5%AC%EB%8F%99%EC%97%90-%EC%8B%A4%ED%8C%A8-%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-46586 STF(Service Time Failover) 상황에서 재시도 횟수만큼 에러가 출력되는 문제가 있습니다.](#bug-46586-stfservice-time-failover-%EC%83%81%ED%99%A9%EC%97%90%EC%84%9C-%EC%9E%AC%EC%8B%9C%EB%8F%84-%ED%9A%9F%EC%88%98%EB%A7%8C%ED%81%BC-%EC%97%90%EB%9F%AC%EA%B0%80-%EC%B6%9C%EB%A0%A5%EB%90%98%EB%8A%94-%EB%AC%B8%EC%A0%9C%EA%B0%80-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-46598 V$REPGAP 퍼포먼스뷰의 REP_GAP 컬럼을 size 단위로 변경합니다.](#bug-46598-vrepgap-%ED%8D%BC%ED%8F%AC%EB%A8%BC%EC%8A%A4%EB%B7%B0%EC%9D%98-rep_gap-%EC%BB%AC%EB%9F%BC%EC%9D%84-size-%EB%8B%A8%EC%9C%84%EB%A1%9C-%EB%B3%80%EA%B2%BD%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Altibase 7.1.0.1.8 Patch Notes



## New Features

### BUG-46174 저장 프로시저내 insert, update 구문에서 레코드 타입변수 사용하도록 기능 확장

* **module** : qp-psm-trigger-execute

* **Category**: Functionality

* **재현 빈도** : Always

* **증상**: 저장 프로시저 내에서 insert update 구문에서도
  레코드타입 변수를 사용할수 있도록 합니다.
  이때, 레코드 변수의 칼럼의 개수와 명시한 테이블의 칼럼의 개수가 동일해야 합니다. 또한 레코드 타입 내부에 정의한 칼럼은 명시한 테이블 칼럼의 타입과 순서대로 정확히 일치하거나 호환이 가능해야
  합니다. 만약 테이블의 칼럼에 NOT NULL 제약조건이
  있으면 대응되는 레코드의 칼럼에 NULL 값을 사용할 수 없습니다.  

* **재현 방법**

  * **재현 절차**

    ```
    create table t1( c1 int, c2 int );
    insert into t1 values( 0, 0);
    create or replace procedure proc1 
    as
    	type tr is record ( c1 int, c2 int );
    	var tr;
    begin
    	var.c1 := 1;
     	var.c2 :=2;
     	update t1 set row = var;
     	var.c1 := 3;
     	var.c2 :=4;
        insert into t1 values var;
    end;
    /
    exec proc1;
    select * from t1;
    ```

  * **수행 결과**

    ```
    [ERR-31001 : SQL syntax error
    
    line 7: missing or invalid syntax
    update T1 set row = var;
                  ^ ^
    
    ]
    iSQL> exec proc1;
    [ERR-31129 : Procedure or function not found :
    0001 : exec PROC1
               ^    ^
    .]
    iSQL> select * from t1;
    C1          C2
    ---------------------------
    0           0
    1 row selected.
    ```

  * **예상 결과**

    ```
    exec proc1;
    Execute success.
    select * from t1;
    C1 C2 
    ---------------------------
    1 2 
    3 4 
    2 rows selected.
    
    ```

* **Workaround** 

* **변경사항** 

  * Performance view
  * Property
  * Compile Option
  * Error Code

## Fixed Bugs

### BUG-46120 Active Server와 Standby Server의 해시 파티션드 테이블의 파티션 개수가 다른 경우, 이중화가 실패해야 합니다. 

- **module** : rp

- **Category**: Functional Error

- **재현 빈도** : Always

- **증상**: Active Server와 Standby Server의 해시 파티션드 테이블의 파티션 개수가 다른 경우, 이중화 실패 에러가 발생하도록 수정하였습니다. 이로 인해 replication protocol version이 7.4.3 에서 7.4.4 로 변경되었습니다.

- **재현 방법**

  - **재현 절차**

    ```
    -- Active
    CREATE TABLE T1
    (
    C1 INTEGER PRIMARY KEY,
    C2 INTEGER
    )
    PARTITION BY HASH( C1 )
    (
    PARTITION P1,
    PARTITION P2
    );
    -- Standby 
    CREATE TABLE T1
    (
    C1 INTEGER PRIMARY KEY,
    C2 INTEGER
    )
    PARTITION BY HASH( C1 )
    (
    PARTITION P1,
    PARTITION P2,
    PARTITION P3
    );
    CREATE REPLICATION REP1
    WITH '${HOST_IP@DB1}', ${ALTIBASE_REPLICATION_PORT_NO@DB1}
    FROM SYS.T1 PARTITION P2 TO SYS.T1 PARTITION P2;
    -- Active 에서
    ALTER REPLICATION REP1 START;
    ```

  - **수행 결과**

    ```
    $T1> ALTER REPLICATION REP1 START;
    Alter success.
    ```

  - **예상 결과**

    ```
    $T1> ALTER REPLICATION REP1 START;
    Fail..
    ```

- **Workaround** 

- **변경사항** 

  - Performance view
  - Property
  - Compile Option
  - Error Code

### BUG-46396 aexport가 생성하는 DDL 마지막 라인에 덧붙이는 newline으로 인해 iSQL에서 Syntax Error가 발생할 수 있습니다.

- **module** : ux-aexport

- **Category**:  Enhancement

- **재현 빈도** : Always

- **증상**: aexport가 생성하는 PSM(procedure, function, view) DDL의 마지막 라인에 덧붙이는 라인으로 인해 iSQL 프롬프트 상에서 수행 시 [ERR-91010 : Syntax Error] 에러가 발생할 수 있어, 이를 수정하였습니다.

- **재현 방법**

  - **재현 절차** 

    ```
    iSQL> CREATE VIEW "V1" AS SELECT SYSDATE FROM dual
        2
    iSQL> ;
    ```

  - **수행 결과**

    ```
    [ERR-91010 : Syntax Error]
    ```

  - **예상 결과**

- **Workaround**

- **변경사항** 

  - Performance view
  - Property
  - Compile Option
  - Error Code

### BUG-46515 dumptrc을 사용해서 콜스택 출력시 altibase_error.log의 콜스택이 생략되는 경우가 있어, 이를 수정하였습니다.

- **module** : id

- **Category**:  Enhancement

- **재현 빈도** : Rare

- **증상**: dumptrc을 사용해서 콜스택 출력시 문자열파싱에 오류가 있었습니다. 이로 인해 altibase_error.log의 콜스택이 생략되는 경우가 발생하여 이를 수정합니다. 

- **재현 방법**

  - **재현 절차** 

  - **수행 결과**

  - **예상 결과**

- **Workaround** 

- **변경사항** 
  - Performance view
  - Property
  - Compile Option
  - Error Code

### BUG-46539 merge 구문에 parser conflicts 발생

- **module** : qp-ddl-dcl-pvo 

- **Category**:  Other

- **재현 빈도** : Always

- **증상**: merge query에서 ON clause의 parsing rule 변경 

- **재현 방법**

  - **재현 절차** 

    ```
    drop table t1;
    drop table t2;
    create table t1( i1 integer, i2 integer );
    insert into t1 values (1, 100);
    insert into t1 values (2, 100);
    insert into t1 values (2, 200);
    insert into t1 values (3, 100);
    insert into t1 values (3, 300);
    insert into t1 values (4, 400);
    create table t2( i1 integer, i2 integer );
    insert into t2 values (1, 1);
    insert into t2 values (2, 2);
    insert into t2 values (3, 3);
    insert into t2 values (6, null);
    merge into t1 using t2 on (t1.i1 = t2.i1) and (t1.i1 = t2.i1)
    when matched then 
    update set t1.i2 = t1.i2+t2.i2;
    
    ```

  - **수행 결과**

    ```
    iSQL> merge into t1 using t2 on (t1.i1 = t2.i1) and (t1.i1 = t2.i1)
    2 when matched then
    3 update set t1.i2 = t1.i2+t2.i2;
    [ERR-31001 : SQL syntax error
    line 1: missing or invalid syntax
    merge into T1 using T2 on (T1.I1 = T2.I1) and (t1.i1 = t2.i1)
    ^ ^
    ]
    
    ```

  - **예상 결과**

    ```
    iSQL> merge into t1 using t2 on (t1.i1 = t2.i1) and (t1.i1 = t2.i1)
    2 when matched then
    3 update set t1.i2 = t1.i2+t2.i2;
    5 rows merged.
    ```

- **Workaround** 

  ```
  merge into t1 using t2 on ((t1.i1 = t2.i1) and (t1.i1 = t2.i1))
  when matched then 
  update set t1.i2 = t1.i2+t2.i2;
  ```

- **변경사항** 

  - Performance view
  - Property
  - Compile Option
  - Error Code

### BUG-46550 JDBC 드라이버에서 addBatch시에 directByteBuffer 사용시 메모리 증가하는 문제가 있습니다.

- **module** : mm-jdbc 

- **Category**:  Memory Error

- **재현 빈도** : Frequence

- **증상**: addBatch()시 사용하는 버퍼를 allocate() 메소드를 이용해 JAVA heap 영역에서 할당하도록 수정하였습니다.  

- **재현 방법**

  - **재현 절차** 

  - **수행 결과**

  - **예상 결과**

- **Workaround** 

- **변경사항** 
  - Performance view
  - Property
  - Compile Option
  - Error Code

### BUG-46551  jdbcAdapter로 altibase 5.5.1 에 데이터 전송시 ArrayIndexOutOfBoundsException 이 발생하는 경우가 있습니다.

- **module** : rp-jdbcAdapter

- **Category**:  Other

- **재현 빈도** : Always

- **증상**: jdbcAdapter로 데이터 전송 batch 작업 진행 시 에러가 발생하면, jdbc driver에서 자체적으로 에러가 발생한 batch 작업을 정리하는데, Altibase 6.1.1 이하의 경우 jdbc driver가 자체적으로 정리하는 기능이 없어 ArrayIndexOutOfBoundException이 발생합니다.
  jdbc driver 수정하는 작업은 호환성 이슈가 있어 수정하지 않습니다. 이에, jdbcAdapter 에서 내부적으로 배치작업을 정리할 수 있도록 수정하였습니다.

- **재현 방법**

  - **재현 절차** 

  - **수행 결과**

  - **예상 결과**

- **Workaround** 

- **변경사항**
  - Performance view
  - Property
  - Compile Option
  - Error Code

### BUG-46552 isql에서 /dev/null을 사용하지 않아야 합니다.

- **module** : ux-isql

- **Category**:  Other

- **재현 빈도** : Always

- **증상**: ISQL_HIST_FILE 환경변수가 설정되어 있지 않은 경우 /dev/null로 출력하던 것을 아예 출력하지 않도록 수정하였습니다.

- **재현 방법**

  - **재현 절차** 

  - **수행 결과**

  - **예상 결과**

- **Workaround** 

- **변경사항** 
  - Performance view
  - Property
  - Compile Option
  - Error Code

### BUG-46567 dumpStack의 동시성 문제 수정

- **module** : id

- **Category**:  Reliability

- **재현 빈도** : Rare

- **증상**: 여러 쓰레드간 dumpStack시 동시성 문제 발생가능성이 있어, 이를 수정하였습니다.

- **재현 방법**

  - **재현 절차** 

  - **수행 결과**

  - **예상 결과**

- **Workaround** 

- **변경사항** 
  - Performance view
  - Property
  - Compile Option
  - Error Code

### BUG-46572 APRE에서 packge를 사용시 psm array가 제대로 인식되지 않습니다.

- **module** : mm-apre

- **Category**:  Functional Error

- **재현 빈도** : Always

- **증상**: psm array 실행 여부 확인시, package_name.procedure_name 의 형태도 인식 가능하도록 수정하였습니다.  

- **재현 방법**

  - **재현 절차** 

  - **수행 결과**

  - **예상 결과**

- **Workaround**

- **변경사항** 
  - Performance view
  - Property
  - Compile Option
  - Error Code

### BUG-46574 Checkpoint Image 생성 도중에 서버가 비정상 종료되면 재구동에 실패 합니다. 

- **module** : sm

- **Category**:  Fatal

- **재현 빈도** : Always

- **증상**: Checkpoint Image 생성도중에 비정상 종료 또는 디스크 부족 등의 이유로 헤더만 기록하고 로그앵커 업데이트까지 진행하지 못하게 되면, 디스크에는 파일이 존재하지만 로그앵커에는 없는 파일로 판단되어 재구동시 검증코드에서 비정상종료하는 문제가 있습니다. 재구동시 리커버리 할때 로그앵커에 존재하지 않는 파일도 생성하도록 합니다.

- **재현 방법**

  - **재현 절차** 

  - **수행 결과**

  - **예상 결과**

- **Workaround** 

- **변경사항**
  - Performance view
  - Property
  - Compile Option
  - Error Code

### BUG-46586 STF(Service Time Failover) 상황에서 재시도 횟수만큼 에러가 출력되는 문제가 있습니다.

- **module** : ul-odbc

- **Category**:  Message Error

- **재현 빈도** : Always

- **증상**: STF(Service Time Failover) 상황에서 재시도 횟수만큼 에러가 출력되는 문제가 있어 수정하였습니다.

- **재현 방법**

  - **재현 절차** 

  - **수행 결과**

  - **예상 결과**

- **Workaround** 

- **변경사항** 
  - Performance view
  - Property
  - Compile Option
  - Error Code

### BUG-46598 V$REPGAP 퍼포먼스뷰의 REP_GAP 컬럼을 size 단위로 변경합니다.

- **module** : rp

- **Category**:  Usability

- **재현 빈도** : Always

- **증상**: 기존 V$REPGAP,V$REPGAP_PARALLEL의 REP_GAP은 REP_LAST_SN과 REP_SN간의 로그 일련번호의 간격입니다. 
  로그 일련번호는 내부적으로 쉬프트 연산을 포함한 비트 연산이기 때문에, REP_GAP이
  매우 큰 값으로 나오는 문제가 있습니다.
  REP_GAP을 로그 일련번호의 간격에서 실제 사이즈 개념으로 수정합니다.
  기본 값으로 MB 단위이며, 새로 추가된 프로퍼티 REPLICATION_GAP_UNIT을 통해 단위를 수정 할 수 있습니다.
  이 값은 REP_GAP_SIZE 에서
  REPLICATION_GAP_UNIT을 나눈 값으로, 나머지가 있으면 올림합니다.
  또한, REP_GAP_SIZE 컬럼을 추가하여 바이트 단위의 이중화 갭도 확인할 수 있도록
  수정하였습니다. 

- **재현 방법**

  - **재현 절차** 

  - **수행 결과**

  - **예상 결과**

- **Workaround**

- **변경사항** 

  - Performance view

    - [V$REPGAP](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_4.md#vrepgap), [V$REPGAP_PARALLEL](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_4.md#vrepgap_parallel)

      컬럼 수정) 

      **REP_GAP**

      이중화 갭의 로그파일 사이즈를 프로퍼티 REPLICATION_GAP_UNIT에 설정된 단위로 보여준다. 기본값은 MB 단위이며 REP_GAP_SIZE에서 REPLICATION_GAP_UNIT 프로퍼티를 나눈값이다. (나머지가 있으면 올림)

      컬럼 추가)

      **REP_GAP_SIZE**  BIGINT

      이중화 갭의 로그파일 사이즈를 의미하며, BYTE 단위이다.

  - Property

    - **추가**

      - [REPLICATION_GAP_UNIT](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_2.md#replication_gap_unit-%EB%8B%A8%EC%9C%84-%EB%B0%94%EC%9D%B4%ED%8A%B8) (단위: 바이트)
        - 데이터 타입 : Unsigned Long
        - 기본값 : 1048576 (1MB)
        -  속성: 변경 가능, 단일 값
        - 값의 범위 : [1, 2^64 -1]
        - 설명 : 이중화 갭의 크기를 조회하는 REP_GAP의 값을 표현하는 단위를 설정한다. REP_GAP의 값은 REP_GAP_SIZE의 값을 이 프로퍼티로 나눈 결과값이며, 나머지는 올림한다. 기본값이면 V$REPGAP의 REP_GAP_SIZE는 바이트 단위로, REP_GAP은 메가바이트 단위로 조회된다.

  - Compile Option

  - Error Code

## Changes

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version | sharding version |
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: | :--------------: |
|    7.1.0.1.8     |          6.5.1          |    8.7.1     |        7.1.6        |            7.4.4             |      2.1.0       |

> Altibase 7.1 패치 버전별 히스토리는 [Version_Histories](https://github.com/jina-altibase/Documents/blob/master/Altibase_7_1_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다. 

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는 데이터베이스를 재구성해야 한다.

#### 	Meta Version

메타 버전이 8.6.1 에서 8.7.1로 변경되었다. 7.1.0.1.7 이하에서 7.1.0.1.8로 패치하면, 자동으로 메타 업그레이드가 수행된다. 

> 패치를 롤백하려는 경우, [메타다운그레이드](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Installation.md#%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9Cmeta-downgrade)를 참고한다.

#### CM protocol Version

통신 프로토콜 버전은 변경되지 않았다.

#### 	Replication protocol Version

이중화 프로토콜 버전이 7.4.3에서 7.4.4로 변경되었지만, 하위 호환성을 보장한다.

#### 	Sharding Version

샤딩 버전은 변경되지 않았다. 단, 7.1.0.1.3 이하에서 7.1.0.1.8로 패치하려는 경우, 샤딩은 재구성해야 한다.

> 알티베이스 샤딩 프로토콜 및 메타는 상위, 하위 호환성을 보장하지 않는다. 즉, 샤딩 버전이 다른 경우, 재구성해야 한다.

### 프로퍼티

#### 추가된 프로퍼티

* [REPLICATION_GAP_UNIT](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_2.md#replication_gap_unit-%EB%8B%A8%EC%9C%84-%EB%B0%94%EC%9D%B4%ED%8A%B8)

### 성능 뷰

#### 수정된 성능 뷰

* [V$REPGAP](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_4.md#vrepgap)
* [V$REPGAP_PARALLEL](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_4.md#vrepgap_parallel)