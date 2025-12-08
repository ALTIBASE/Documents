# Altibase 7.1.0.10.5 Patch Notes

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-51532 aexport에서 생성하는 iloader 스크립트의 병렬 수행 기능 추가](#bug-51532)
    - [BUG-51652 사용자 암호 입력 대신 암호화된 암호 파일로 로그인이 가능해야 합니다.](#bug-51652)
    - [BUG-51698 altiEncrypt를 이용하여 dblink, aku, Adapter 의 설정 파일에 있는 PASSWORD를 암호화 지원](#bug-51698)
    - [BUG-51538 FixedTable의 count(\*) 메모리 최적화](#bug-51538)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-50945 SUBSTR 함수 내에서 EMPTY_CLOB()가 인자로 사용될 경우, [ERR-01003 : Unexpected end of string] 오류가 발생합니다.](#bug-50945)
    - [BUG-50946 CLOB 컬럼 에 대한 SUBSTR, SUBSTRB 함수 호출 시, 시작값이 음수일 경우 잘못된 결과가 반환됩니다.](#bug-50946)
    - [BUG-50992 DDL로 인해 어뎁터가 종료된 경우, 오프라인 어뎁터를 수행하여도 데이터 동기화가 이루어지지 않는다.](#bug-50992)
    - [BUG-51029 빈 LOB 컬럼에 대한 AFTER UPDATE 트리거 동작 오류 수정](#bug-51029)
    - [BUG-51131 TO_CHAR 함수에서 EEEE 출력 형식을 사용할 때, 특정 NUMERIC 데이터에 EEEE 출력 형식이 적용되지 않는 문제 수정](#bug-51131)
    - [BUG-51323 UPDATE 구문의 SET 절에 사용된 서브쿼리 내 뷰를 WHERE 절의 서브쿼리에서 참조할 때 발생하는 오류 수정](#bug-51323)
    - [BUG-51347 중첩된 뷰에 대한 multiple update 구문 수행시 서버가 비정상 종료할 수 있습니다.](#bug-51347)
    - [BUG-51419 aexport에서 생성되는 시노님과 디렉토리 객체의 DDL문 생성 순서를 알파벳 순으로 변경했습니다.](#bug-51419)
    - [BUG-51457 MEM_DB_DIR 로 지정된 경로가 없는 경우, 잘못된 에러가 출력됩니다.](#bug-51457)
    - [BUG-51480 altibase가 생성하는 파일에 대해 다른 사용자(other)에게 쓰기(w) 권한이 부여되지 않도록 수정합니다.](#bug-51480)
    - [BUG-51491 Temporary table 여부를 검사하는 로직의 오류로 인해 서버가 비정상 종료될 수 있는 문제를 수정합니다.](#bug-51491)
    - [BUG-51519 Lead 함수 3번째 인자 사용시 특정 경우에 서버가 비정상 종료하는 문제를 수정합니다.](#bug-51519)
    - [BUG-51525 executeBatch 수행 후 executeUpdate 시 exception 발생](#bug-51525)
    - [BUG-51543 디스크 인덱스에서 낮은 확률로 [ERR-11069 : Internal server error in the storage manager (fail to insert key)] 오류 발생](#bug-51543)
    - [BUG-51630 테이블, 뷰, 함수가 서로 참조하는 관계인 테이블에 DDL을 수행하면 오류가 발생합니다.](#bug-51630)
    - [BUG-51707 다중화 환경에서 LOB을 포함한 디스크 테이블을 가진 이중화가 있을 경우 다른 이중화에서 LOB로그를 읽다가 에러가 발생합니다.](#bug-51707)
    - [BUG-51766 altiMon 설정 파일인 config.xml.sample이 추가되었습니다.](#bug-51766)
    - [BUG-51790 메모리 인덱스 탐색 중 리프노드 간 연결이 깨진것을 판단하는 MAX LOOP값을 변경합니다.](#bug-51790)
    - [BUG-51804 VARIABLE 컬럼을 포함한 메모리 테이블 생성 후(FLUSH 이전 단계에서) 서버가 강제 종료될 경우, 예기치 않은 동작이 발생할 수 있는 문제를 수정합니다.](#bug-51804)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-51532<a name=bug-51532></a> aexport에서 생성하는 iloader 스크립트의 병렬 수행 기능 추가

-   **module** : ux-aexport

-   **Category** : Enhancement

-   **재현 빈도** : Unknown

-   **설명** : aexport에서 생성하는 iloader 스크립트의 병렬 수행이
    가능한 기능을 추가했습니다.

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

### BUG-51652<a name=bug-51652></a> 사용자 암호 입력 대신 암호화된 암호 파일로 로그인이 가능해야 합니다.

-   **module** : ux-isql

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : iSQL에서 사용자 비밀번호를 암호화된 파일로 저장할 수
    있으며, 저장된 암호 파일은 iSQL, aexport, iLoader에서 -pf 옵션을
    통해 로그인 시 사용할 수 있습니다.

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

### BUG-51698<a name=bug-51698></a> altiEncrypt를 이용하여 dblink, aku, Adapter 의 설정 파일에 있는 PASSWORD를 암호화 지원

-   **module** : rp

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : Password를 암호화 하는 툴인 altiEncrypt 가 추가되었다.

    이제 altiEncrypt 툴을 이용하여 dblink, aku, Adapter 의 설정 파일(conf 파일)에
    PASSWORD를 암호화 하여 설정 할 수 있다.

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

### BUG-51538<a name=bug-51538></a> FixedTable의 count(\*) 메모리 최적화

-   **module** : qp-select-execute

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : FixedTable의 count(\*) 메모리 최적화 수정

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
    SELECT SUBSTR( EMPTY_CLOB(), 1, 1 ) FROM dual;
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

### BUG-50946<a name=bug-50946></a> CLOB 컬럼 에 대한 SUBSTR, SUBSTRB 함수 호출 시, 시작값이 음수일 경우 잘못된 결과가 반환됩니다.

-   **module** : mt-function

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : CLOB 컬럼에 대해 SUBSTR 또는 SUBSTRB 함수 호출 시, 시작값이 음수일 경우 잘못된 결과가 반환되는 문제를 수정했습니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    DROP TABLE t1;
    CREATE TABLE t1(c1 CLOB);
    INSERT INTO t1 VALUES ('CLOB');
    SELECT SUBSTR(c1, -1, 1) FROM t1;
    SELECT SUBSTRB(c1, -1, 1) FROM t1;
    ```

  - **수행 결과**

    ```sql
    iSQL> SELECT SUBSTR(c1, -1, 1) FROM t1;
    SUBSTR(C1, -1, 1) :
    
    1 row selected.
    iSQL> SELECT SUBSTRB(c1, -1, 1) FROM t1;
    SUBSTRB(C1, -1, 1) :
    
    1 row selected.
    ```

  -   **예상 결과**

      ```sql
      iSQL> SELECT SUBSTR(c1, -1, 1) FROM t1;
      SUBSTR(C1,-1,1) : B
      
      1 row selected.
      iSQL> SELECT SUBSTRB(c1, -1, 1) FROM t1;
      SUBSTRB(C1,-1,1) : B
      
      1 row selected.
      ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50992<a name=bug-50992></a> DDL로 인해 어뎁터가 종료된 후, 바로 오프라인 어뎁터를 수행할 경우 데이터 동기화가 이루어지지 않는 문제 수정

-   **module** : rp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : DDL로 인해 어뎁터가 종료된 후, 바로 오프라인 어뎁터를 수행할 경우 데이터 동기화가 이루어지지 않는 문제를 수정합니다.
    
-   **재현 방법**

    -   **재현 절차**

            Meta Logging 옵션이 켜진 Adapter 생성하여 start
            이중화 테이블에 DDL 수행
            이중화 stop
            standby에서 offline adapter 수행

    -   **수행 결과**

            데이타 동기화가 이루어지지 않음

    -   **예상 결과**

            데이타 동기화

-   **Workaround**

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

### BUG-51131<a name=bug-51131></a> TO_CHAR 함수에서 EEEE 출력 형식을 사용할 때, 특정 NUMERIC 데이터에 EEEE 출력 형식이 적용되지 않는 문제 수정

-   **module** : mt-function

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : TO_CHAR 함수에서 EEEE 출력 형식을 사용할 때, 실수부 자릿수가 짧은 NUMERIC 데이터는 EEEE 출력 형식이 적용되지 않는 문제를 수정하였습니다.
    
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

### BUG-51323<a name=bug-51323></a> UPDATE 구문의 SET 절에 사용된 서브쿼리 내 뷰를 WHERE 절의 다른 서브쿼리에서 참조할 때 발생하는 오류 수정

-   **module** : qp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : UPDATE 구문의 SET 절에 사용된 서브쿼리 내 뷰를 WHERE 절의 다른 서브쿼리에서 참조할 때 발생하는 오류를 수정하였습니다.
    
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

-   **설명** : 파티션드 테이블을 기반으로 생성한 중첩 뷰에 multiple update 구문을 수행시 서버가 비정상 종료하는 문제를 수정합니다.
    
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
-   **설명** : aexport 에서 생성되는 시노님과 디렉토리 객체의 DDL문 생성 순서를 알파벳 순으로 변경했습니다.
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

### BUG-51457<a name=bug-51457></a> MEM_DB_DIR 로 지정된 경로가 없는 경우, 잘못된 에러가 출력됩니다.

-   **module** : sm

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : MEM_DB_DIR 로 지정된 경로가 없는 경우, 잘못된 에러가 출력되는 문제를 수정합니다.

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

### BUG-51480<a name=bug-51480></a> altibase가 생성하는 파일에 대해 다른 사용자(other)에게 쓰기(w) 권한이 부여되지 않도록 수정합니다.

-   **module** : id

-   **Category** : Security

-   **재현 빈도** : Frequence

-   **설명** : altibase가 생성하는 파일에 대해 다른 사용자(other)에게 쓰기(w) 권한이 부여되지 않도록 수정합니다.

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

### BUG-51491<a name=bug-51491></a> Temporary table 여부를 검사하는 로직의 오류로 인해 서버가 비정상 종료될 수 있는 문제를 수정합니다.

-   **module** : qp

-   **Category** : Fatal

-   **재현 빈도** : Unknown

-   **설명** : Temporary table 여부를 검사하는 로직의 오류로 인해 서버가 비정상 종료될 수 있는 문제를 수정합니다.
    
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

### BUG-51519<a name=bug-51519></a> Lead 함수 3번째 인자 사용시 특정 경우에 서버가 비정상 종료하는 문제를 수정합니다.

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

      ```sql
      I1          CHANGE      I2
      ----------------------------------------
      1           0           49106157
      1 row selected.
      ```

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
    
    -   재현조건
    

    1. 하나의 PreparedStaement로 수행해야 함.

    2. 테이블에 LOB 컬럼이 있어야 함.

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

### BUG-51543<a name=bug-51543></a> 디스크 인덱스에서 낮은 확률로 [ERR-11069 : Internal server error in the storage manager (fail to insert key)] 오류 발생

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : 디스크 인덱스에서 낮은 확률로 [ERR-11069 : Internal server error in the storage manager (fail to insert key)] 오류가 발생하는 문제를 수정합니다. 이 오류는 아래의 조건을 만족하는 경우에 발생할 수 있습니다.

    - 삭제된것과 동일한 값을 INSERT 하거나 동일한 값으로 UPDATE하는 경우
    - 인덱스 노드(페이지) 하나에 최대 2개의 키만 들어갈 수 있을 정도로 인덱스 키의 크기가 큰 경우

- **재현 방법**

  - **재현 절차**

    ```sql
    CREATE TABLE T1 ( I1 CHAR(1500), I2 CHAR(1500), I3 INT ) TABLESPACE SYS_TBS_DISK_DATA;
    CREATE INDEX IDX1 ON T1 ( I2, I1 );
    INSERT INTO T1 VALUES ( 2, 2, 221 );
    INSERT INTO T1 VALUES ( 1, 7, 8 );
    UPDATE T1 SET I1 = 2 WHERE I2 = 2;
    ```

  - **수행 결과**

    ```sql
    [ERR-11069 : Internal server error in the storage manager (fail to insert key)]
    ```

  - **예상 결과**

    ```sql
    1 row inserted.
    ```

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
        4. LOB 테이블에 INSERT를 수행1.

  -   **수행 결과**

          REP2에서 T1의 로그를 읽고 SKIP하기전에 없는 메타 정보를 처리하다가 에러 발생

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

### BUG-51804<a name=bug-51804></a> VARIABLE 컬럼을 포함한 메모리 테이블 생성 후(FLUSH 이전 단계에서) 서버가 강제 종료될 경우, 예기치 않은 동작이 발생할 수 있는 문제를 수정합니다.

-   **module** : sm

-   **Category** : Other

-   **재현 빈도** : Rare

-   **설명** : VARIABLE 컬럼을 포함한 메모리 테이블 생성 후 (FLUSH 이전 단계에서) 서버가 강제 종료될 경우, 예기치 않은 동작이 발생할 수 있는 문제를 수정합니다.

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
| 7.1.0.10.5       | 6.5.1                   | 8.12.1       | 7.1.7               | 7.4.7                        |

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
