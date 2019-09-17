Altibase 7.1.0.2.6 Patch Notes
==============================

[TOC]

New Features
------------

### BUG-46824 APRE에 anonymous block을 지원해야 합니다.

-   **module** : mm-apre

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **증상** : APRE에서 anonymous block 을 지원하도록 개선되었습니다.

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

### BUG-46887 dbms\_metadata.get\_ddl 패키지 지원

-   **module** : ut

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **증상** : DBMS\_METADATA 패키지 지원으로, 서버에서 DB객체의 DDL을 조회할 수 있는 기능을 제공합니다. $ALTIBASE_HOME/packages 아래에 dbms_metadata.sql, dbms_metadata.plb로 제공합니다.

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

### BUG-47159 dbms\_metadata.get\_ddl 패키지를 aexport 에 적용

- **module** : ux-aexport
- **Category** : Functionality
- **재현 빈도** : Always
- **증상** : DBMS\_METADATA 패키지를 aexport에 적용
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

### BUG-46922 Percentile\_Cont , Percentile\_Disc 함수의 메모리 재사용 기능 향상

-   **module** : mt-function

-   **Category** : Efficiency

-   **재현 빈도** : Always

-   **증상** : Percentile\_Cont , Percentile\_Disc 함수의 메모리 재사용 기능이 향상되었습니다.

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

### BUG-47082 메모리 인덱스 VALUE BASE BOTTOM-UP 빌드 성능 향상

- **module** : sm-mem-index

- **Category** : Enhancement

- **재현 빈도** : Always

- **증상** : 메모리 인덱스의 VALUE BASE BOTTOM-UP 빌드 속도를 향상시켰습니다.

  이로 인해 STARTUP시 VALUE BASE 인덱스 생성속도도 향상되었으며, VALUE BASE 인덱스 생성 중 추가로 요구되는 메모리 사이즈가 절반으로 줄었습니다.

- **재현 방법**

  -   **재현 절차**

  -   **수행 결과**

  -   **예상 결과**

- **Workaround**

- **변경사항**

  -   Performance view
  -   Property
      -   변경
          -   [MEMORY_INDEX_BUILD_RUN_SIZE](<https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_1.md#memory_index_build_run_size-%EB%8B%A8%EC%9C%84--%EB%B0%94%EC%9D%B4%ED%8A%B8>)의 디폴트값을 변경합니다. 
              -   32768 -> 131072

  -   Compile Option
  -   Error Code

Fixed Bugs
----------

### BUG-46409 Alter replication set 구문 중 meta 초기화가 안된 구문이 있습니다.

-   **module** : rp

-   **Category** : Other

-   **재현 빈도** : Always

-   **증상** : 내부적으로 Alter replication set 구문을 처리하는 로직에서 meta 초기화가 누락된 부분이 있어, 수정하였습니다.

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

### BUG-46783 이중화 중 DDL 수행 시 receiver 가 종료할 경우 이미 free 된 이중화 이름을 복사 할 수 있습니다.

-   **module** : rp-control

-   **Category** : Memory Error

-   **재현 빈도** : Frequence

-   **증상** : 이중화 중 DDL 수행 시 receiver 가 종료할 경우 이미 free 된 이중화 이름을 복사 할 수 있어 수정합니다.

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

### BUG-46879 openjdk11 에서 jdbcAdapter 구동 실패 수정

- **module** : rp-jdbcAdapter

- **Category** : Functional Error

- **재현 빈도** : Always

- **증상** : openjdk 11에서 jdbcAdapter 구동이 되지 않는 문제를 수정하였습니다. 

  또한, jdbcAdapter 실행시 jvm생성시 stderr가 발생하면 ALA socket으로 error가 전송되는 문제가 있었는데, $ALTIBASE_HOME/trc/stderr.log에 쓰도록 로그파일이 추가되었습니다.

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

### BUG-47090 AIX, HP 장비에서 sysdba로 remote 접속을 막는 기능이 제대로 동작하지 않습니다.

-   **module** : cm

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : AIX, HP 장비에서 sysdba로 remote 접속을 막는 기능이 제대로 동작하지 않아 수정하였습니다.

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

### BUG-47095 partition simple query 수행 시, 메모리 초기화 누락

-   **module** : qp-dml-execute

-   **Category** : Memory Error

-   **재현 빈도** : Always

-   **증상** : partition simple query 수행시, 내부적으로 초기화하지 않은 변수를 사용하는 문제가 있어 수정하였습니다.

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

### BUG-47105 cpu 정보를 가져올 때 on-line 인지 off-line 인지 체크하지 않아, 서버가 boot 과정에서 실패할 수 있습니다.

- **module** : id

- **Category** : Functional Error

- **재현 빈도** : Always

- **증상** : 리눅스플래폼에서 cpu중 일부만 활성화한 상태에서 altibase 서버구동시 실패하는 문제를 해결합니다.

- **재현 방법**

  -   **재현 절차**

          cpu의 상태를 off-line으로 변경

  -   **수행 결과**

  -   **예상 결과**

- **Workaround**

- **변경사항**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

### BUG-47115 OpenJDK11 환경에서 jdbcAdapter 테스트 수행시, StackOverflowError가 발생하는 문제 수정

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : OpenJDK11환경에서 JdbcAdapter 테스트 수행시
    StackOverflowError가 발생하는 문제 수정.

-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

        use JRE 1.7 

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47119 이중화 접속시 sendHandshakeAck 를 보낼 때 패킷 계산이 잘못되어 메모리를 긁을 수 있습니다.

-   **module** : rp

-   **Category** : Other

-   **재현 빈도** : Always

-   **증상** : 이중화 접속시 sendHandshakeAck 를 보낼 때 패킷 계산이
    잘못되어 메모리를 긁을 수 있어 수정합니다.

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

### BUG-47121 jdbcAdapter conf 파일에 OTHER\_DATABASE\_JDBC\_MAX\_HEAP\_SIZE 가 설정이 되지 않는 문제가 있습니다.

- **module** : rp-jdbcAdapter

- **Category** : Other

- **재현 빈도** : Always

- **증상** : 매뉴얼에는 OTHER\_DATABASE\_JDBC\_MAX\_HEAP\_SIZE 로 되어
  있으나 소스상에서는 OTHER\_DATABASE\_JDBC\_JVM\_MAX\_HEAP\_SIZE 로
  되어 있어서 프로퍼티가 설정되지 않는 문제가 있었습니다.

  소스에도 매뉴얼과 동일하게 OTHER\_DATABASE\_JDBC\_MAX\_HEAP\_SIZE 를
  사용하도록 하여 문제 수정하였습니다.

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

### BUG-47126 호스트 변수에 길이가 긴 값을 할당하면 segment fault 발생합니다

-   **module** : ux-isql

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : 호스트 변수에 할당한 스트링 값을 저장하는 변수가 256 길이로 고정되어 있어서 발생하는 문제로, 동적할당으로 변경하였습니다.

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

### BUG-47128 Query rebuild시 query\_binding memory가 지속적으로 증가할 수 있습니다.

-   **module** : qp-dml-execute

-   **Category** : Memory Error

-   **재현 빈도** : Always

-   **증상** : Query rebuild 발생시 이전에 bind data를 저장하기 위한
    memory를 해제하지 않는 문제를 수정합니다.

    Bind가 있는 query를 prepare 한 뒤 반복해서 execute 할 때, rebuild가
    발생하면 해당 문제가 발생합니다.

    Statement를 닫거나 session을 종료하면 bind를 위해 할당한 memory를
    memory manager에서 일괄 반납하므로 이전에 해제하지
    못한 memory도 모두 해제합니다.

-   **재현 방법**

    -   **재현 절차**

            session 1
            loop
            {
              update with binding
            }
            session 2
            loop
            {
              truncate table
            }

    -   **수행 결과**

            query_binding size is continually increased.

    -   **예상 결과**

            query_binding size is fixed.

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47135 openjdk에서 실행시 jvm 생성이 안 됩니다

- **module** : ux-altiMon

- **Category** : Portability

- **재현 빈도** : Always

- **증상** : openjdk에서 altimon.sh 실행시 아래 에러 메시지를
  출력하고 jvm 생성이 안 되는 문제를 수정하였습니다.

  % cat altimon\_stderr.log

  Error: Could not create the Java Virtual Machine.

  Error: A fatal exception has occurred. Program will exit.

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

### BUG-47136  alter tablespace swap시, 테이블 스페이스 사용량를 계산하는 로직 오류 수정 

-   **module** : qp

-   **Category** : Other

-   **재현 빈도** : Always

-   **증상** : alter tablespace swap시, 테이블 스페이스 사용량를 계산하는 로직의 오류로 [ERR-3144E : Need more free space of tablespace.] 에러가 발생하는 경우가 있어 수정하였습니다.

-   **재현 방법**

    -   **재현 절차**

            DROP TABLESPACE DISK_TBS_0 INCLUDING CONTENTS AND DATAFILES;
            DROP TABLESPACE MEM__TBS_0 INCLUDING CONTENTS AND DATAFILES;
            CREATE DISK     TABLESPACE DISK_TBS_0 DATAFILE 'disk_tbs_0' SIZE 4M AUTOEXTEND ON MAXSIZE 40M;
            CREATE MEMORY   TABLESPACE MEM__TBS_0                       SIZE 4M AUTOEXTEND ON MAXSIZE 40M;
            iSQL> create table t1
                 (
                     c1 integer,
                     c2 char(100),
                     c3  integer,
                     c4  char(100),
                     c5  char(100),
                     c6  char(100),
                     c7  char(100),
                     c8  char(100),
                     c9  integer,
                     c10 date
                   ) TABLESPACE MEM__TBS_0;
            Create success.
            iSQL> alter table t1 add primary key(c3,c1) ;
            Alter success.
            iSQL>
            iSQL> insert into t1 select level, level, 3, level, level, level, level, level, level, sysdate
                 from dual connect by level <=  50000;
            50000 rows inserted.
            iSQL> alter table t1 alter tablespace DISK_TBS_0;
            [ERR-3144E : Need more free space of tablespace. Tablespace Name: DISK_TBS_0, Progress : 1%, Threshold : 80%, Estimated Page Count : 400.]

    -   **수행 결과**

    -   **예상 결과**

            DROP TABLESPACE DISK_TBS_0 INCLUDING CONTENTS AND DATAFILES;
            DROP TABLESPACE MEM__TBS_0 INCLUDING CONTENTS AND DATAFILES;
            CREATE DISK     TABLESPACE DISK_TBS_0 DATAFILE 'disk_tbs_0' SIZE 4M AUTOEXTEND ON MAXSIZE 40M;
            CREATE MEMORY   TABLESPACE MEM__TBS_0                       SIZE 4M AUTOEXTEND ON MAXSIZE 40M;
            iSQL> create table t1
                2 (
                3     c1 integer,
                4     c2 char(100),
                5     c3  integer,
                6     c4  char(100),
                7     c5  char(100),
                8     c6  char(100),
                9     c7  char(100),
                10     c8  char(100),
                11     c9  integer,
                12     c10 date
                13   ) TABLESPACE MEM__TBS_0;
            Create success.
            iSQL> alter table t1 add primary key(c3,c1) ;
            Alter success.
            iSQL>
            iSQL> insert into t1 select level, level, 3, level, level, level, level, level, level, sysdate
                2 from dual connect by level <=  50000;
            50000 rows inserted.
            iSQL> alter table t1 alter tablespace DISK_TBS_0;
            Alter success.

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47140 하위버전과 이중화시 해시 파티션드 테이블의 파티션 개수가 같은 경우에도 이중화 실패가 발생할수 있습니다.

-   **module** : rp

-   **Category** : Other

-   **재현 빈도** : Always

-   **증상** :  이중화시 해시 파티션드 테이블의 파티션 개수를 체크하도록
    프로토콜을 추가하였는데 하위버전과 이중화시  해시 파티션드 테이블을
    사용하면 파티션 개수를 잘못 체크하여 이중화 start 시 에러가 발생하는
    문제를 수정하였습니다.

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

### BUG-47142 BLOB컬럼과 DECIMAL 컬럼을 포함한 테이블에서 첫번째 컬럼의 타입이 BLOB 이고, HASH 조인을 할 경우 에러가 발생합니다.

-   **module** : qp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : BLOB컬럼과 DECIMAL 컬럼을 포함한 테이블에서 HASH 조인을
    할 경우, 과도한 메모리 할당을 요구하는 문제가 있어, 수정하였습니다.

-   **재현 방법**

    -   **재현 절차**

            drop table t1;
            drop table t2;                    
            CREATE TABLE t1 ( COL   blob,
                                             COL_DECIMAL     DECIMAL );
             CREATE TABLE T2( COL   blob,
                                              COL_DECIMAL     DECIMAL );
            select * from  t1 left outer join t2 on t1.col_decimal = t2.col_decimal;
            [651]
            select /*+ USE_HASH(t1,t2) */ * from  t1 left outer join t2 on t1.col_decimal = t2.col_decimal;

    -   **수행 결과**

            iSQL> select * from  t1 left outer join t2 on t1.col_decimal = t2.col_decimal;
            [ERR-31318 : Unexpected errors may have occurred: qtc::fixAfterValidation: tuple row size is larger than 4GB]
            [651]
            iSQL> select /*+ USE_HASH(t1,t2) */ * from  t1 left outer join t2 on t1.col_decimal = t2.col_decimal;
            [ERR-31318 : Unexpected errors may have occurred: qtc::fixAfterValidation: tuple row size is larger than 4GB]

    -   **예상 결과**

            iSQL> select * from  t1 left outer join t2 on t1.col_decimal = t2.col_decimal;[ERR-91022 : LOB and GEOMETRY type data cannot be displayed]

-   **Workaround**

        drop table t1;
        drop table t2;                    
        CREATE TABLE t1 ( COL_DECIMAL     DECIMAL ,
                                        COL_int1   blob);
         CREATE TABLE T2( COL_DECIMAL     DECIMAL,
                                          COL_int1   blob );
        select * from  t1 left outer join t2 on t1.col_decimal = t2.col_decimal;
        [651]
        use_hash 힌트 제거

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47173 host variable precision이 컬럼 size보다 큰 경우 simple query 수행 시 에러처리 되는 것을 개선해야합니다.

-   **module** : qp-dml-execute

-   **Category** : Other

-   **재현 빈도** : Always

-   **증상** :  fast simple query에서 index생성 시 bind되는 varchar,
    char type precision이 테이블의 varchar, char precision보다 큰 경우
    에러 처리되는 부분을 개선함

-   **재현 방법**

    -   **재현 절차**

            VAR A CHAR(9);
                EXEC :A := 'ABCDEFGHI';
                CREATE TABLE T1 (I1 CHAR(5) PRIMARY KEY, I2 CHAR(5));
                VAR A CHAR(9);
                EXEC :A := 'ABCDEFGHI';
                PREPARE SELECT * FROM T1 WHERE I1 = :A;
                [ERR-2100D : Invalid data type length]

    -   **수행 결과**

    -   **예상 결과**

            VAR A CHAR(9);
                EXEC :A := 'ABCDEFGHI';
                CREATE TABLE T1 (I1 CHAR(5) PRIMARY KEY, I2 CHAR(5));
                VAR A CHAR(9);
                EXEC :A := 'ABCDEFGHI';
                PREPARE SELECT * FROM T1 WHERE I1 = :A;
            I1     I2     
            -----------------
            No rows selected.

-   **Workaround**

            VAR A CHAR(9);
            EXEC :A := 'ABCDEFGHI';
            CREATE TABLE T1 (I1 CHAR(5) PRIMARY KEY, I2 CHAR(5));
            VAR A CHAR(9);
            EXEC :A := 'ABCDEFGHI';
            PREPARE SELECT  /*+ NO_EXEC_FAST*/  * FROM T1 WHERE I1 = :A;
        I1     I2     
        -----------------
        No rows selected.

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47195 PARTITION SWAP 후 비정상종료시 재구동 실패.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **증상** : PARTITON SWAP 후 비정상종료 된경우

    서버 구동 실패하는 버그를 수정하였습니다.

-   **재현 방법**

    -   **재현 절차**

            CREATE TABLE tb_test2
                (
                    c1  integer primary key
                )
                PARTITION BY RANGE_USING_HASH ( c1 )
                (
                    PARTITION P1 VALUES LESS THAN ( 200 ),
                    PARTITION PD VALUES DEFAULT
                );
               CREATE TABLE tb_test2_rebuild
                (
                    c1  integer primary key
                )
                PARTITION BY RANGE_USING_HASH ( c1 )
                (
                    PARTITION P1 VALUES LESS THAN ( 200 ),
                    PARTITION PD VALUES DEFAULT
                );
            ALTER TABLE SYS.tb_test2_rebuild REPLACE SYS.tb_test2 PARTITION P1;
            이후 command line에서 다음을 실행
            server kill
            server start

    -   **수행 결과**

            서버 시작 실패

    -   **예상 결과**

            서버가 정상적으로 구동됨.

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
| 7.1.0.2.6        | 6.5.1                   | 8.7.1        | 7.1.7               | 7.4.5                        | 2.2.1            |

> Altibase 7.1 패치 버전별 히스토리는 [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7_1_Version_Histories.md)
> 에서 확인할 수 있다.

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

#### 변경된 프로퍼티

[MEMORY_INDEX_BUILD_RUN_SIZE](<https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_1.md#memory_index_build_run_size-%EB%8B%A8%EC%9C%84--%EB%B0%94%EC%9D%B4%ED%8A%B8>)

### 성능 뷰

추가/변경/삭제된 성능뷰 없음