# Altibase 7.1.0.8.4 Patch Notes

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-50145 Add a feature to create the `aku_start_completed` file when `aku -p start` is successful.

-   **module** : aku

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : Add a feature to create the `aku_start_completed` file in the `/tmp` directory when the `aku -p start` command completes successfully. This file will be deleted when `aku -p end` or `aku -p clean` is executed. If the `aku_start_completed` file already exists in `/tmp`, an error message will be displayed, and the `aku -p start` command will terminate.
    
    If an error occurs during the execution of `aku -p start`, the `aku_start_completed` file will not be created.
    
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

### BUG-50206 Add a property `AKU_ADDRESS_CHECK_COUNT` to check the connectivity to the local address during `aku -p start`.

-   **module** : aku

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : Add the `AKU_ADDRESS_CHECK_COUNT` property to the `aku.conf` configuration file. This property allows you to set the number of times to check if the local DNS is registered with the endpoint during `aku -p start`. The default value is 30.

-   **재현 방법**
    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
        -   New
            -   AKU_ADDRESS_CHECK_COUNT
                -   Default value : 30
                -   Description: When `aku -p start` is executed, it attempts to connect to the local IP the number of times specified by the `AKU_ADDRESS_CHECK_COUNT`.
    -   Compile Option
    -   Error Code

### BUG-50191 New threads have been added in altimon to measure CPU usage: one for measuring OS CPU usage and another for measuring Altibase CPU usage.

-   **module** : ux-altiMon

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : New threads have been added in altimon to measure CPU usage: one for measuring OS CPU usage and another for measuring Altibase CPU usage.
    
    User can configure the execution interval of the CPU usage (%) measurement thread using the `CpuSamplingInterval` element in the `config.xml` file. The unit is in seconds, and the default value is 3 seconds.
    
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

### BUG-49101  버퍼에서 페이지 읽기에 실패하는 경우, 페이지의 락이 해제되지 않아 다음 페이지 락에서 HANG이 발생할 수 있습니다.

-   **module** : sm

-   **Category** : Hang

-   **재현 빈도** : Always

-   **설명** : 페이지 읽기에 실패하는 경우 페이지의 락이 해제되지 않는 문제를 수정합니다.

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

### BUG-49584  LOB 칼럼을 포함한 메모리 파티션드 테이블에 테이블스페이스를 변경하는 DDL 수행시, LOB 칼럼의 테이블 스페이스는 변경되지 않는 문제가 있습니다.

-   **module** : qp-ddl-dcl-execute

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : LOB 칼럼을 포함한 메모리 파티션드 테이블에 테이블스페이스를 변경하는 DDL 수행시, LOB 칼럼의 테이블 스페이스는 변경되지 않는 문제가 있습니다. 이후 ALTER TABLE ... MODIFY COLUMN 구문을 수행하면 비정상 종료하는 문제가 있어, 수정합니다.

- **재현 방법**

  - **재현 절차**

        CREATE MEMORY TABLESPACE MEM_TEST_TBS_0 SIZE 32M AUTOEXTEND ON;
        CREATE TABLE T1 ( I1 INTEGER DEFAULT 1, I2 VARCHAR(4) , I3 CLOB )
        PARTITION BY RANGE ( I1 )
        ( PARTITION P1 VALUES LESS THAN( 10 ),
        PARTITION P2 VALUES DEFAULT
        ) ;
        ALTER TABLE T1 ALTER TABLESPACE MEM_TEST_TBS_0 ;
        INSERT INTO T1 VALUES (3, 1, 17);
    
        ALTER TABLE T1 MODIFY (I2 VARCHAR(1));

  -   **수행 결과**

          [ERR-91015 : Communication failure.]

  -   **예상 결과**

          Alter success.

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49890  ALTER SESSION SET REGEXP\_MODE = 1 변경 시 PCRE2 라이브러리에서 지원하지 않는 캐릭터셋 일 때 에러 메시지를 변경해야 합니다.

-   **module** : qp

-   **Category** : Usability

-   **재현 빈도** : Always

-   **설명** : PCRE2 라이브러리에서 지원하지 않는 캐릭터셋 일 때 에러
    메시지를 변경합니다.

    (버그 반영 전) ERR-2106B : Unsupported character set by PCRE2 library

    (버그 반영 후) ERR-2106B : Unable to execute this operation because of the database server character set.

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
        -   0x2106B ( 135275) mtERR_ABORT_PCRE2_NOT_SUPPORTED_ENCODING Unable to execute this operation because of the database server character set.
            -   Cause: The current database server character set is not supported in REGEXP_MODE=1 (i.e., PCRE2 compatibility mode).
            -   Action:
                -   Check the character sets supported by REGEXP_MODE = 1 in the SQL Reference.
                -   Check the Altibase server character set in v$nls_parameters.
                -   If the current regexp_mode property value is 0, change the database
                -   server character set to one supported by REGEXP_MODE = 1.
                -   If the current regexp_mode property value is 1, change it to 0 or change the database server character set to one supported by REGEXP_MODE = 1.
                -   To change the database server character set, you need to re-create the database.

### BUG-50010  GroupMetric 중 DBMetric의 수행시 동시성 고려가 필요합니다.

-   **module** : ux-altiMon

-   **Category** : Functional Error

-   **재현 빈도** : Rare

-   **설명** : 서버의 부하가 비정상적으로 높은 상황에서 모니터링 수행작업이 지연될때, 동일한 모니터링작업이 동시에 수행되는 경우 동시성 문제가 발생할 수 있어서 수정합니다.

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

### BUG-50024  altimon에서 DB 모니터링 쿼리 결과값이 없는 경우, GroupMetrics로 데이터를 출력할때 값이 누락됩니다.

-   **module** : ux-altiMon

-   **Category** : Usability

-   **재현 빈도** : Always

-   **설명** : DB 모니터링 쿼리 결과가 no rows 인 경우, GroupMetrics로 데이터를 출력할때 출력값 이 누락되는 문제를 수정합니다.

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

### BUG-50066  DDL 구문 수행 중 실패하면, 동시성 제어에서 해제된 메모리 사용(Free'd Memory Read) 오류가 발생할 수 있습니다.

-   **module** : qp

-   **Category** : Memory Error

-   **재현 빈도** : Frequence

-   **설명** : DDL 구문 수행 중 실패하면, 동시성 제어에서 해제된 메모리
    사용(Free'd Memory Read) 오류가 발생할 수 있는 문제를 예방합니다.

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

### BUG-50086  Hyper-threading off 환경에서 물리 코어 수를 잘못 산정하는 문제가 있습니다.

-   **module** : id

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : Hyper-threading off 환경에서 물리 코어 수를 잘못 산정하는
    문제가 있어 수정합니다.

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

### BUG-50130  패키지 인스톨러 설치시, 저장 패키지 생성 구문에서 오류가 발생합니다.

-   **module** : qp
-   **Category** : Functional Error
-   **재현 빈도** : Always
-   **설명** : 저장 패키지 생성 구문에 불필요한 파일이 포함되어 있어서, 주석처리하고 수행되지 않도록 수정합니다.
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

### BUG-50164  휘발성 테이블에서 공간 부족의 이유로 확장이 실패할 하는경우, 페이지 락이 해제되지 않는 문제가 있습니다.

-   **module** : sm

-   **Category** : Hang

-   **재현 빈도** : Always

-   **설명** : 휘발성 테이블에서 페이지 할당을 시도할때는 페이지 락을
    요구하는데, 공간 부족의 이유로 예외가 발생하는 경우 페이지 락이
    해제될 수 있도록 수정합니다.

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

### BUG-50174  altibase.properties.release 파일에서 사용되지 않는 프로퍼티인 REPLICATION_SERVICE_WAIT_MAX_LIMIT를 제거합니다.

-   **module** : rp

-   **Category** : Maintainability

-   **재현 빈도** : Always

-   **설명** : 사용하지 않는 프로퍼티가 altibase.properties.release
    파일에 남아 있어서 제거합니다.

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

### BUG-50177  LOB이 포함된 디스크 테이블에 이중화가 걸려 있을때 undo tablespace full이 발생하면 이중화가 실패하는 문제가 있습니다.

-   **module** : rp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : LOB 로그 처리 중 undo tablespace full이 발생하더라도
    이중화가 정상적으로 동작하도록 수정 합니다.

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

### BUG-50196  NOCYLE 옵션으로 생성된 시퀀스가 ALTER SEQUENCE 구문을 수행한 후 서버를 재구동하면, CYCLE로 동작하는 문제가 있습니다.

-   **module** : sm

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : NOCYLE 옵션으로 생성된 시퀀스가 ALTER SEQUENCE 구문을
    수행한 후 서버를 재구동하면,  CYCLE로 동작하는 문제를 수정합니다.

- **재현 방법**

  - **재현 절차**

        create sequence seq2 start with 8 cache 3 maxvalue 10 nocycle;
        SELECT seq2.NEXTVAL FROM dual;
        alter sequence seq2 increment by 3;
    
        server restart 수행
    
        SELECT seq2.NEXTVAL FROM dual;

  -   **수행 결과**

          NEXTVAL
          -----------------------
          4
          1 row selected.

  -   **예상 결과**

          [ERR-11044 : Sequence upper bound exceeded]

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50197  메모리 파티션드 테이블 생성 구문에서 LOB 테이블 스페이스 지정에 대한 검증이 미흡합니다.

-   **module** : qp-ddl-dcl-pvo

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 메모리 파티션드 테이블 생성 구문에서 LOB 테이블 스페이스
    지정에 대한 검증을 올바르게 수정합니다.

-   **재현 방법**

    -   **재현 절차**

            DROP TABLE T1;
            DROP TABLESPACE MEM_TEST_TBS_0  INCLUDING CONTENTS AND DATAFILES;
            DROP TABLESPACE MEM_TEST_TBS_1  INCLUDING CONTENTS AND DATAFILES;
            DROP TABLESPACE MEM_TEST_TBS_2  INCLUDING CONTENTS AND DATAFILES;
            CREATE MEMORY TABLESPACE MEM_TEST_TBS_0  SIZE 32M AUTOEXTEND ON;
            CREATE MEMORY TABLESPACE MEM_TEST_TBS_1  SIZE 32M AUTOEXTEND ON;
            CREATE MEMORY TABLESPACE MEM_TEST_TBS_2  SIZE 32M AUTOEXTEND ON;
            CREATE TABLE T1 ( I1 INTEGER DEFAULT 1, I2 VARCHAR(4), I3 CLOB )
            PARTITION BY HASH ( I1 )
            ( PARTITION P1 TABLESPACE MEM_TEST_TBS_0 LOB (I3) STORE AS ( TABLESPACE MEM_TEST_TBS_1 ),
              PARTITION P2 TABLESPACE MEM_TEST_TBS_2 LOB (I3) STORE AS ( TABLESPACE MEM_TEST_TBS_1 )
            ) TABLESPACE MEM_TEST_TBS_1;

    -   **수행 결과**

            Create success.

    -   **예상 결과**

            [ERR-31245 : Unable to create a LOB type column with the specified tablespace.]

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
| 7.1.0.8.4        | 6.5.1                   | 8.10.1       | 7.1.7               | 7.4.7                        |

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

> 알티베이스 샤딩 프로토콜 및 메타는 상위, 하위 호환성을 보장하지
> 않는다. 즉, 샤딩 버전이 다른 경우, 재구성해야 한다.

### 프로퍼티

#### 추가된 프로퍼티

#### 변경된 프로퍼티

#### 삭제된 프로퍼티

### 성능 뷰

#### 추가된 성능 뷰

#### 변경된 성능 뷰

#### 삭제된 성능 뷰
