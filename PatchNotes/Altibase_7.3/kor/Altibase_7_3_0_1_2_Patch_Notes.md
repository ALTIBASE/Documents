Altibase 7.3.0.1.2 Patch Notes
================================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
  - [BUG-49872 메모리 DB의 구동시 페이지 캐시 개선](#bug-49872)
  - [BUG-51509 태국어 문자에 대한 정렬을 지원]()
  - [BUG-51532 aexport에서 생성하는 iloader 스크립트의 병렬 수행 기능 추가]()
  - [BUG-51652 사용자 암호 입력 대신 암호화된 암호 파일로 로그인이 가능해야 합니다.]()
  - [BUG-51698 암호 관리를 위한 신규 유틸리티 altiEncrypt 추가]()
  - [BUG-51538 FixedTable의 count(\*) 메모리 최적화]()
- [Fixed Bugs](#fixed-bugs)
  - [BUG-50946 CCLOB 컬럼에 대해 SUBSTR 및 SUBSTRB 함수를 수행할 때 시작값이 음수인 경우, 잘못된 결과가 반환되는 문제 수정]()
  - [BUG-51029 빈 LOB 컬럼에 대한 AFTER UPDATE 트리거 동작 오류 수정]()
  - [BUG-51131 TO\_CHAR 함수에서 EEEE 출력 형식을 사용할 때, 실수부 자릿수가 잛은 NUMERIC 데이터는 EEEE 출력 형식이 적용되지 않는 문제 수정]()
  - [BUG-51323 UPDATE 구문의 SET 절에 사용된 서브쿼리 내 뷰를 WHERE 절의 서브쿼리에서 참조할 때 발생하는 오류 수정]()
  - [BUG-51347 중첩된 뷰에 대한 multiple update 구문 수행시 서버가 비정상 종료할 수 있습니다.]()
  - [BUG-51419 aexport에서 생성되는 시노님과 디렉토리 객체의 DDL문 생성 순서를 알파벳 순으로 변경했습니다.]()
  - [BUG-51519 Lead 함수 3번째 인자 사용시 특정 경우에 FATAL]()
  - [BUG-51525 executeBatch 수행 후 executeUpdate 시 exception 발생]()
  - [BUG-51543 복합키 인덱스가 존재하는 디스크 테이블에 동일한 인덱스의 데이터를 삽입하려고 할때 발생하는 에러를 수정합니다.]()
  - [BUG-51574 altiProfile 에서 출력되는 SESSION STAT 에 SESSION ID가 0인 세션의 통계정보가 주기적으로 표시 됩니다.]()
  - [BUG-51630 테이블, 뷰, 함수가 서로 참조하는 관계인 테이블에 DDL을 수행하면 오류가 발생합니다.]()
  - [BUG-51632 SELECT Statement 의 순서에 따른 Lock 해제 현상 수정]()
  - [BUG-51691 DDL 크기가 65,535 바이트를 초과하는 경우, aexport 실행 시 크기가 0인 빈 파일이 생성됩니다.]()
  - [BUG-51707 다중화 환경에서 LOB을 포함한 디스크 테이블을 가진 이중화가 있을 경우 다른 이중화에서 LOB로그를 읽다가 에러가 발생합니다.]()
  - [BUG-51766 altiMon 설정 파일인 config.xml.sample이 추가되었습니다.]()
  - [BUG-51790 메모리 인덱스 탐색 중 리프노드 간 연결이 깨진것을 판단하는 MAX LOOP값을 변경합니다.]()
- [Changes](#changes)
  - [Version Info](#version-info)
  - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
  - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
  - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
------------

### BUG-49872<a name=bug-49872></a> 메모리 DB의 구동시 페이지 캐시 개선

-   **module** : sm\_resource

-   **Category** : Enhancement

-   **재현 빈도** : Frequence

-   **설명** : 메모리 DB의 구동시 페이지 캐시 사용 방식을 개선하였습니다.

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

### BUG-51509<a name=bug-51509></a> 태국어 문자에 대한 정렬을 지원

-   **module** : qp

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : UTF-8 환경에서 태국어에 대한 정렬 기능이 지원됩니다. 이 기능은 NLS_COMP=1로 설정한 경우에만 사용할 수 있습니다. NLS_COMP 프로퍼티는 ReadOnly 속성으로 최초 DB를 생성할 때에 설정할 수 있으며, DB 생성 이후에 NLS_COMP 값을 변경하면 잘못된 결과가 발생할 수 있습니다.

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

### BUG-51532<a name=bug-51532></a> aexport에서 생성하는 iloader 스크립트의 병렬 수행 기능 추가

-   **module** : ux-aexport

-   **Category** : Enhancement

-   **재현 빈도** : Unknown

-   **설명** : aexport에서 생성된 iloader 스크립트를 병렬로 수행할 수 있는 기능이 추가되었습니다. 새로 추가된 프로퍼티 ILOADER_OUT_SCRIPT_PARALLEL, ILOADER_IN_SCRIPT_PARALLEL 의 값을 2 이상으로 설정하면, 병렬 수행이 가능한 iloader 스크립트가 생성됩니다.
    
-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
        -   ILOADER_OUT_SCRIPT_PARALLEL 추가
            -   설명: 원본 데이터베이스에서 데이터를 추출하는 스크립트를 병렬로 실행하도록 설정하는 프로퍼티이다. 이 값을 2 이상으로 설정하면 병렬로 동작한다.
            -   기본값: 1
        -   ILOADER_IN_SCRIPT_PARALLEL 추가
            -   설명: 대상 데이터베이스에 데이터를 로딩하는 스크립트를 병렬로 실행하도록 설정하는 프로퍼티이다. 이 값을 2 이상으로 설정하면 병렬로 동작한다.
            -   기본값: 1
    -   Compile Option
    -   Error Code

### BUG-51652<a name=bug-51652></a> 사용자 암호 입력 대신 암호화된 암호 파일로 로그인이 가능해야 합니다.

-   **module** : ux-isql

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : iSQL에서 사용자 비밀번호를 암호화된 파일로 저장하는 기능이 추가되었습니다. 저장된 암호화된 파일은 iSQL, aexport, iLoader에서 -pf 옵션을 통해 로그인 시 사용할 수 있습니다.
    
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

### BUG-51698<a name=bug-51698></a> 암호 관리를 위한 신규 유틸리티 altiEncrypt 추가

-   **module** : rp

-   **Category** : Functionality

-   **재현 빈도** : Always

- **설명** : altiEncrypt 를 이용하여 dblink, aku, Adapter 의 Conf 파일에
  PASSWORD를 암호화하여 설정 할 수 있도록 개선되었습니다. 암호화된 PASSWORD 사용으로 비밀번호 보안을 개선했습니다.

  - 사용법

    - ```
      altiEncrypt username password
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

### BUG-51538<a name=bug-51538></a> FixedTable의 count(\*) 메모리 최적화

-   **module** : qp-select-execute

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : FixedTable의 count(\*) 메모리 최적화

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

### BUG-50946<a name=bug-50946></a> CCLOB 컬럼에 대해 SUBSTR 및 SUBSTRB 함수를 수행할 때 시작값이 음수인 경우, 잘못된 결과가 반환되는 문제 수정

-   **module** : mt-function

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : CLOB 컬럼에 대해 SUBSTR 및 SUBSTRB 함수를 수행할 때 시작값이 음수인 경우, 잘못된 결과가 반환되는 문제를 수정하였습니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    DROP TABLE t1;
    CREATE TABLE t1(c1 CLOB);
    INSERT INTO t1 VALUES ('clob');
    SELECT substr(c1, -1, 1) FROM t1;
    SELECT substrb(c1, -1, 1) FROM t1;
    ```

  -   **수행 결과**

          NULL value return

  -   **예상 결과**

      ```sql
      SUBSTR(c1,-1,1)
      -----------------------
      b
      1 row selected.
      ```

-   **Workaround**

        None

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-51029<a name=bug-51029></a> 빈 LOB 컬럼에 대한 AFTER UPDATE 트리거 동작 오류 수정

-   **module** : qp-psm-trigger-execute

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : AFTER UPDATE 트리거 동작시, empty_CLOB과 같이 size가 0인 LOB 컬럼에 대해 DML을 수행할 때, 오류가 발생하는 문제를 수정했습니다.

- **재현 방법**

  - **재현 절차**

    ```sql
    DROP TABLE t1;
    DROP TABLE t2;
    CREATE TABLE t1 ( i1 clob, i2 CLOB ) TABLESPACE sys_tbs_disk_data;
    CREATE TABLE t2 ( i1 clob, i2 CLOB );
    INSERT INTO t1 VALUES( '1', empty_CLOB() );
    CREATE TRIGGER trig1
    AFTER UPDATE ON t1
    REFERENCING
      OLD AS OLDROW,
      NEW AS NEWROW
    FOR EACH ROW
    AS
    BEGIN
      INSERT INTO t2 VALUES ( newrow.i1, newrow.i2 );
    END;
    /
    UPDATE t1 SET i1 = i1 || 'a';
    ```

  -   **수행 결과**

          [ERR-110D0 : The lob size is bigger than the maximum lob size]

  -   **예상 결과**

          1 row updated

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-51131<a name=bug-51131></a> TO\_CHAR 함수에서 EEEE 출력 형식을 사용할 때, 실수부 자릿수가 잛은 NUMERIC 데이터는 EEEE 출력 형식이 적용되지 않는 문제 수정

-   **module** : mt-function

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : TO\_CHAR 함수에서 EEEE 출력 형식을 사용할 때, 실수부 자릿수가 잛은 NUMERIC 데이터는 EEEE 출력 형식이 적용되지 않는 문제를 수정하였습니다.
    
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

### BUG-51323<a name=bug-51323></a> UPDATE 구문의 SET 절에 사용된 서브쿼리 내 뷰를 WHERE 절의 서브쿼리에서 참조할 때 발생하는 오류 수정

-   **module** : qp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : UPDATE 구문의 SET 절에 사용된 서브쿼리 내 뷰를 WHERE 절의 서브쿼리에서 참조할 때 발생하는 오류를 수정하였습니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    DROP VIEW v1;
    DROP TABLE t1 CASCADE;
    
    CREATE VIEW v1 AS SELECT 1 AS X FROM DUAL LIMIT 1;
    CREATE TABLE t1 ( i1 integer );
    UPDATE t1 SET i1=(SELECT 2 FROM v1) WHERE i1 IN (SELECT 3 FROM v1);
    ```

  - **수행 결과**

    ```
    [ERR-31455 : Failed to work because an internal exception occurred from an OS.[Contact Altibase's Support Center]]
    ```

  - **예상 결과**

    ```
    No rows updated.
    ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-51347<a name=bug-51347></a> 중첩된 뷰에 대한 multiple update 구문 수행시 서버가 비정상 종료할 수 있습니다.

-   **module** : qp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 파티션드 테이블을 기반으로 생성한 중첩 뷰에 multiple
    update 구문을 수행시 서버가 비정상 종료하는 문제를 수정합니다.

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

### BUG-51419<a name=bug-51419></a> aexport에서 생성되는 시노님과 디렉토리 객체의 DDL문 생성 순서를 알파벳 순으로 변경했습니다.

-   **module** : ux-aexport

-   **Category** : Usability

-   **재현 빈도** : Always

-   **설명** : aexport 수행시 생성되는 시노님 및 디렉토리 객체 생성 DDL문의 순서를 알파벳 순으로 변경했습니다.
    
-   aexport 에서 생성되는 시노님과 디렉토리 객체의 DDL문 생성 순서를 알파벳 순으로 변경했습니다.
    
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

### BUG-51519<a name=bug-51519></a> Lead 함수 3번째 인자 사용시 특정 경우에 FATAL

-   **module** : qp-select-execute

-   **Category** : Fatal

-   **재현 빈도** : Rare

-   **설명** : Lead 함수의 3번째 인자 사용시 특정 조건에서 서버가 비정상 종료하는 문제를 수정하였습니다.

- **재현 방법**

  -   **재현 절차**

      ```sql
      DROP TABLE t1;
      CREATE TABLE t1 ( i1 int , i2 int , i3 int);
      INSERT into t1 values ( 1, 49106157, 1);
      
      DROP TABLE t2;
      create table t2 ( i1 int, i2 int, i3 int, i4 int);
      select i1, change, i2 from (
      select lead( buy - sell, 1, 0) over ( partition by i2 order by i1  ) as change, i2, i1
      from
      (
      select nvl( case when i3 = 1 then i2
                       when i3 = 2 then i2
                       when i3 = 3 then i2
                       else 0 end, 0) as buy, numeric'0' as sell, i1, i2
      from t1
      union all
      select nvl( case when i3 = 1 then i2
                       when i3 = 2 then i2
                       when i3 = 3 then i2
                       else 0 end, 0) as sell, numeric'0' as buy, i1, i2
      from t2
      ) order by i1 desc, i2 desc
      );
      ```
      
  -   **수행 결과**

          [ERR-91015 : Communication failure.]

  -   **예상 결과**

          I1          CHANGE      I2
          ----------------------------------------
          1           0           49106157
          1 row selected.

- **Workaround**

  ```sql
  --lead함수의 3번째 인자를 사용하지 않고, NVL 함수로 감싸도록 수정.
  select i1, change, i2 from (
  select nvl(lead( buy - sell, 1) over ( partition by i2 order by i1  ), 0) as change, i2, i1
  from
  (
  select nvl( case when i3 = 1 then i2
                   when i3 = 2 then i2
                   when i3 = 3 then i2
                   else 0 end, 0) as buy, numeric'0' as sell, i1, i2
  from t1
  union all
  select nvl( case when i3 = 1 then i2
                   when i3 = 2 then i2
                   when i3 = 3 then i2
                   else 0 end, 0) as sell, numeric'0' as buy, i1, i2
  from t2
  ) order by i1 desc, i2 desc
  );
  ```

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-51525<a name=bug-51525></a> executeBatch 수행 후 executeUpdate 시 exception 발생

-   **module** : mm-jdbc

-   **Category** : Other

-   **재현 빈도** : Always

-   **설명** : CLOB컬럼이 포함된 테이블에 대해 ExecuteBatch(), ExecuteUpdate()를 순차적으로 수행했을 때, exception이 발생하는 문제를 수정하였습니다.
    
    재현조건
    
    1. 하나의 PreparedStaement로 수행해야 함.
    
    2. 테이블에 LOB 컬럼이 있어야 함.
    
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

### BUG-51543<a name=bug-51543></a> 복합키 인덱스가 존재하는 디스크 테이블에 동일한 인덱스의 데이터를 삽입하려고 할때 발생하는 에러를 수정합니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : 복합키 인덱스가 존재하는 디스크 테이블에 동일한 인덱스의 데이터를 삽입하려고 할때 발생하는 에러를 수정합니다.

- **재현 방법**

  - **재현 절차**

    ```
    CREATE TABLE T1 ( I1 CHAR(1500), I2 CHAR(1500), I3 INT ) TABLESPACE SYS_TBS_DISK_DATA;
    CREATE INDEX IDX1 ON T1 ( I2, I1 );
    INSERT INTO T1 VALUES ( 2, 2, 221 );
    INSERT INTO T1 VALUES ( 1, 7, 8 );
    INSERT INTO T1 VALUES ( 2, 2, 221 );
    ```

  - **수행 결과**

    ```
    [ERR-11069 : Internal server error in the storage manager (fail to insert key)]
    ```

  - **예상 결과**

    ```
    1 row inserted.
    ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-51574<a name=bug-51574></a> altiProfile 에서 출력되는 SESSION STAT 에 SESSION ID가 0인 세션의 통계정보가 주기적으로 표시 됩니다.

-   **module** : mm

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : SESSION STAT을 프로파일링 할때, SESSION ID가 0인 세션의 통계정보가 주기적으로 여러회 출력되는 문제가 있었습니다. 불필요한 통계정보가 주기적으로 출력되는 문제를 수정하였습니다.
    
- **재현 방법**

  -   **재현 절차**

          export ALTIBASE_QUERY_PROF_FLAG=8
          server start
          altiProfile alti-1752732799-0.prof | grep "SESSION STAT"

  - **수행 결과**

        [SESSION STAT] 2025/07/17 15:18:20 (0)
        [SESSION STAT] 2025/07/17 15:18:20 (0)
        [SESSION STAT] 2025/07/17 15:18:23 (0)
        [SESSION STAT] 2025/07/17 15:18:23 (0)
        [SESSION STAT] 2025/07/17 15:18:26 (0)
        [SESSION STAT] 2025/07/17 15:18:26 (0)
        [SESSION STAT] 2025/07/17 15:18:29 (0)
        [SESSION STAT] 2025/07/17 15:18:29 (0)
        [SESSION STAT] 2025/07/17 15:18:32 (0)
        [SESSION STAT] 2025/07/17 15:18:32 (0)

  -   **예상 결과**

          No session stat of SID 0

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-51630<a name=bug-51630></a> 테이블, 뷰, 함수가 서로 참조하는 관계인 테이블에 DDL을 수행하면 오류가 발생합니다.

-   **module** : qp-ddl-dcl-execute

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 테이블, 뷰, 함수가 서로 참조하는 관계인 테이블에 DDL을 수행할 때, [ERR-01067 : The memory size allocated for the statement has exceeded the maximum limit] 오류가 발생하는 문제를 수정하였습니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    CREATE TABLE t1 (c1 CHAR(32000)) TABLESPACE SYS_TBS_DISK_DATA;
    CREATE OR REPLACE FUNCTION func1 RETURN CHAR(32000)
    AS
    var1 CHAR(32000);
    BEGIN
      SELECT c1 into var1 FROM t1 limit 1;
      RETURN var1;
    END;
    /
    CREATE OR REPLACE VIEW v1 AS SELECT func1() val1 FROM t1;
    ALTER TABLE t1 ADD (c2 varchar(32000));
    ALTER TABLE t1 ADD (c3 varchar(32000));
    ```

  - **수행 결과**

        [ERR-01067 : The memory size allocated for the statement has exceeded the maximum limit ( Name : Query_Prepare, Wanted Memory Size : 209732568, Max size : 209715200 ).]

  -   **예상 결과**

          Alter success.

-   **Workaround**

        Add column 전에 invalid 상태인 function을 compile하여 valid 상태로 변경한다.

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-51632<a name=bug-51632></a> SELECT Statement 의 순서에 따른 Lock 해제 현상 수정

-   **module** : sm\_transaction

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : Non-AutoCommit 모드로 수행된 SELECT문은 기본적으로 IS_LOCK이 자동으로 해제됩니다. 그러나 일부 상황에서는 자동 해제로 인해 예기치 않는 문제가 발생할 수 있어, 이를 방지하기 위한 비공개 프로퍼티가 추가되었습니다.

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

### BUG-51691<a name=bug-51691></a> DDL 크기가 65,535 바이트를 초과하는 경우, aexport 실행 시 크기가 0인 빈 파일이 생성됩니다.

-   **module** : ux-aexport

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : DDL 크기가 65,535 바이트를 초과하는 경우, aexport 실행 시 파일이 정상적으로 생성되지 않고 크기가 0인 빈 파일이 생성되는 문제를 수정했습니다.
    
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

### BUG-51707<a name=bug-51707></a> 다중화 환경에서 LOB을 포함한 디스크 테이블을 가진 이중화가 있을 경우 다른 이중화에서 LOB로그를 읽다가 에러가 발생합니다.

-   **module** : rp-sender

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 이중화가 디스크 LOB 트랜잭션 로그의 메타정보를 잘못 처리하여 발생하던 오류를 수정했습니다. 자신의 LOB 로그가 아닌 경우, 메타정보 처리를 SKIP하도록 수정하였습니다.
    
- **재현 방법**

  - **재현 절차**

        1. LOB을 포함한 디스크 테이블 T1을 가진 이중화 REP1 생성
        2. 이중화 REP2 생성
        3. REP1, REP2 START
        4. LOB 테이블에 INSERT를 수행

  -   **수행 결과**

          REP2에서 T1의 로그를 읽고 SKIP하기전에 없는 메타 정보를 처리하다가 에러 발

  -   **예상 결과**

          REP2에서 T1의 로그를 읽고 SKIP하여 정상 동작

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-51766<a name=bug-51766></a> altiMon 설정 파일인 config.xml.sample이 추가되었습니다.

-   **module** : ux-altiMon

-   **Category** : Usability

-   **재현 빈도** : Always

-   **설명** : 패치 적용 후 altiMon/conf 디렉토리에 사용자가 설정한 config.xml 파일이 삭제되는 문제가 있어서, 이제부터 altimon 설정 파일은 config.xml.sample 파일로 제공됩니다.
    
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

### BUG-51790<a name=bug-51790></a> 메모리 인덱스 탐색 중 리프노드 간 연결이 깨진것을 판단하는 MAX LOOP값을 변경합니다.

-   **module** : sm

-   **Category** : Enhancement

-   **재현 빈도** : Unknown

-   **설명** : 메모리 인덱스 탐색 중 접근할 수 있는 노드 수의 상한을 기존 100만에서 "전체 인덱스 노드 수의 10배"로 변경하였습니다.

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
| 7.3.0.1.2        | 7.3.0                   | 9.4.1        | 7.1.8               | 7.4.9                        |

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
> [메타다운그레이드](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/Installation%20Guide.md#%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9Cmeta-downgrade)를
> 참고한다.

#### CM protocol Version

통신 프로토콜 버전은 변경되지 않았다.

#### Replication protocol Version

Replication 프로토콜 버전은 변경되지 않았다.

### 프로퍼티

추가/변경/삭제된 프로퍼티 없음.

### 성능 뷰

추가/변경/삭제된 성능뷰 없음.
