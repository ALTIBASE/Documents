# Altibase 7.1.0.8.4 Patch Notes

<br>



<br>

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [New Features](#new-features)
    - [BUG-50145 aku -p start가 성공하면 aku_start_completed 파일을 생성하는 기능을 추가합니다.](#bug-50145%C2%A0aku--p-start%EA%B0%80-%EC%84%B1%EA%B3%B5%ED%95%98%EB%A9%B4-aku_start_completed-%ED%8C%8C%EC%9D%BC%EC%9D%84-%EC%83%9D%EC%84%B1%ED%95%98%EB%8A%94-%EA%B8%B0%EB%8A%A5%EC%9D%84-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50206 aku -p start시 local address에 접속가능 여부를 확인하기 위한 프로퍼티 AKU_ADDRESS_CHECK_COUNT 를 추가합니다.](#bug-50206%C2%A0aku--p-start%EC%8B%9C-local-address%EC%97%90-%EC%A0%91%EC%86%8D%EA%B0%80%EB%8A%A5-%EC%97%AC%EB%B6%80%EB%A5%BC-%ED%99%95%EC%9D%B8%ED%95%98%EA%B8%B0-%EC%9C%84%ED%95%9C-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0-aku_address_check_count-%EB%A5%BC-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50191 altimon에서 CPU 사용률을 측정하기 위해 OS CPU 사용율 측정 쓰레드, 알티베이스 CPU 사용률 측정 쓰레드가 추가되었습니다.](#bug-50191%C2%A0altimon%EC%97%90%EC%84%9C-cpu-%EC%82%AC%EC%9A%A9%EB%A5%A0%EC%9D%84-%EC%B8%A1%EC%A0%95%ED%95%98%EA%B8%B0-%EC%9C%84%ED%95%B4-os-cpu-%EC%82%AC%EC%9A%A9%EC%9C%A8-%EC%B8%A1%EC%A0%95-%EC%93%B0%EB%A0%88%EB%93%9C-%EC%95%8C%ED%8B%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4-cpu-%EC%82%AC%EC%9A%A9%EB%A5%A0-%EC%B8%A1%EC%A0%95-%EC%93%B0%EB%A0%88%EB%93%9C%EA%B0%80-%EC%B6%94%EA%B0%80%EB%90%98%EC%97%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-49101 버퍼에서 페이지 읽기에 실패하는 경우, 페이지의 락이 해제되지 않아 다음 페이지 락에서 HANG이 발생할 수 있습니다.](#bug-49101%C2%A0%EB%B2%84%ED%8D%BC%EC%97%90%EC%84%9C-%ED%8E%98%EC%9D%B4%EC%A7%80-%EC%9D%BD%EA%B8%B0%EC%97%90-%EC%8B%A4%ED%8C%A8%ED%95%98%EB%8A%94-%EA%B2%BD%EC%9A%B0-%ED%8E%98%EC%9D%B4%EC%A7%80%EC%9D%98-%EB%9D%BD%EC%9D%B4-%ED%95%B4%EC%A0%9C%EB%90%98%EC%A7%80-%EC%95%8A%EC%95%84-%EB%8B%A4%EC%9D%8C-%ED%8E%98%EC%9D%B4%EC%A7%80-%EB%9D%BD%EC%97%90%EC%84%9C-hang%EC%9D%B4-%EB%B0%9C%EC%83%9D%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-49584 LOB 칼럼을 포함한 메모리 파티션드 테이블에 테이블스페이스를 변경하는 DDL 수행시, LOB 칼럼의 테이블 스페이스는 변경되지 않는 문제가 있습니다.](#bug-49584%C2%A0lob-%EC%B9%BC%EB%9F%BC%EC%9D%84-%ED%8F%AC%ED%95%A8%ED%95%9C-%EB%A9%94%EB%AA%A8%EB%A6%AC-%ED%8C%8C%ED%8B%B0%EC%85%98%EB%93%9C-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%8A%A4%ED%8E%98%EC%9D%B4%EC%8A%A4%EB%A5%BC-%EB%B3%80%EA%B2%BD%ED%95%98%EB%8A%94-ddl-%EC%88%98%ED%96%89%EC%8B%9C-lob-%EC%B9%BC%EB%9F%BC%EC%9D%98-%ED%85%8C%EC%9D%B4%EB%B8%94-%EC%8A%A4%ED%8E%98%EC%9D%B4%EC%8A%A4%EB%8A%94-%EB%B3%80%EA%B2%BD%EB%90%98%EC%A7%80-%EC%95%8A%EB%8A%94-%EB%AC%B8%EC%A0%9C%EA%B0%80-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-49890 ALTER SESSION SET REGEXP_MODE = 1 변경 시 PCRE2 라이브러리에서 지원하지 않는 캐릭터셋 일 때 에러 메시지를 변경해야 합니다.](#bug-49890%C2%A0alter-session-set-regexp_mode--1-%EB%B3%80%EA%B2%BD-%EC%8B%9C-pcre2-%EB%9D%BC%EC%9D%B4%EB%B8%8C%EB%9F%AC%EB%A6%AC%EC%97%90%EC%84%9C-%EC%A7%80%EC%9B%90%ED%95%98%EC%A7%80-%EC%95%8A%EB%8A%94-%EC%BA%90%EB%A6%AD%ED%84%B0%EC%85%8B-%EC%9D%BC-%EB%95%8C-%EC%97%90%EB%9F%AC-%EB%A9%94%EC%8B%9C%EC%A7%80%EB%A5%BC-%EB%B3%80%EA%B2%BD%ED%95%B4%EC%95%BC-%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50010 GroupMetric 중 DBMetric의 수행시 동시성 고려가 필요합니다.](#bug-50010%C2%A0groupmetric-%EC%A4%91-dbmetric%EC%9D%98-%EC%88%98%ED%96%89%EC%8B%9C-%EB%8F%99%EC%8B%9C%EC%84%B1-%EA%B3%A0%EB%A0%A4%EA%B0%80-%ED%95%84%EC%9A%94%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50024 altimon에서 DB 모니터링 쿼리 결과값이 없는 경우, GroupMetrics로 데이터를 출력할때 값이 누락됩니다.](#bug-50024%C2%A0altimon%EC%97%90%EC%84%9C-db-%EB%AA%A8%EB%8B%88%ED%84%B0%EB%A7%81-%EC%BF%BC%EB%A6%AC-%EA%B2%B0%EA%B3%BC%EA%B0%92%EC%9D%B4-%EC%97%86%EB%8A%94-%EA%B2%BD%EC%9A%B0-groupmetrics%EB%A1%9C-%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%A5%BC-%EC%B6%9C%EB%A0%A5%ED%95%A0%EB%95%8C-%EA%B0%92%EC%9D%B4-%EB%88%84%EB%9D%BD%EB%90%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50066 DDL 구문 수행 중 실패하면, 동시성 제어에서 해제된 메모리 사용(Free'd Memory Read) 오류가 발생할 수 있습니다.](#bug-50066%C2%A0ddl-%EA%B5%AC%EB%AC%B8-%EC%88%98%ED%96%89-%EC%A4%91-%EC%8B%A4%ED%8C%A8%ED%95%98%EB%A9%B4-%EB%8F%99%EC%8B%9C%EC%84%B1-%EC%A0%9C%EC%96%B4%EC%97%90%EC%84%9C-%ED%95%B4%EC%A0%9C%EB%90%9C-%EB%A9%94%EB%AA%A8%EB%A6%AC-%EC%82%AC%EC%9A%A9freed-memory-read-%EC%98%A4%EB%A5%98%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-50086 Hyper-threading off 환경에서 물리 코어 수를 잘못 산정하는 문제가 있습니다.](#bug-50086%C2%A0hyper-threading-off-%ED%99%98%EA%B2%BD%EC%97%90%EC%84%9C-%EB%AC%BC%EB%A6%AC-%EC%BD%94%EC%96%B4-%EC%88%98%EB%A5%BC-%EC%9E%98%EB%AA%BB-%EC%82%B0%EC%A0%95%ED%95%98%EB%8A%94-%EB%AC%B8%EC%A0%9C%EA%B0%80-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-50130 패키지 인스톨러 설치시, 저장 패키지 생성 구문에서 오류가 발생합니다.](#bug-50130%C2%A0%ED%8C%A8%ED%82%A4%EC%A7%80-%EC%9D%B8%EC%8A%A4%ED%86%A8%EB%9F%AC-%EC%84%A4%EC%B9%98%EC%8B%9C-%EC%A0%80%EC%9E%A5-%ED%8C%A8%ED%82%A4%EC%A7%80-%EC%83%9D%EC%84%B1-%EA%B5%AC%EB%AC%B8%EC%97%90%EC%84%9C-%EC%98%A4%EB%A5%98%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50164 휘발성 테이블에서 공간 부족의 이유로 확장이 실패할 하는경우, 페이지 락이 해제되지 않는 문제가 있습니다.](#bug-50164%C2%A0%ED%9C%98%EB%B0%9C%EC%84%B1-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90%EC%84%9C-%EA%B3%B5%EA%B0%84-%EB%B6%80%EC%A1%B1%EC%9D%98-%EC%9D%B4%EC%9C%A0%EB%A1%9C-%ED%99%95%EC%9E%A5%EC%9D%B4-%EC%8B%A4%ED%8C%A8%ED%95%A0-%ED%95%98%EB%8A%94%EA%B2%BD%EC%9A%B0-%ED%8E%98%EC%9D%B4%EC%A7%80-%EB%9D%BD%EC%9D%B4-%ED%95%B4%EC%A0%9C%EB%90%98%EC%A7%80-%EC%95%8A%EB%8A%94-%EB%AC%B8%EC%A0%9C%EA%B0%80-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-50174 altibase.properties.release 파일에서 사용되지 않는 프로퍼티인 REPLICATION_SERVICE_WAIT_MAX_LIMIT를 제거합니다.](#bug-50174%C2%A0altibasepropertiesrelease-%ED%8C%8C%EC%9D%BC%EC%97%90%EC%84%9C-%EC%82%AC%EC%9A%A9%EB%90%98%EC%A7%80-%EC%95%8A%EB%8A%94-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0%EC%9D%B8-replication_service_wait_max_limit%EB%A5%BC-%EC%A0%9C%EA%B1%B0%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50177 LOB이 포함된 디스크 테이블에 이중화가 걸려 있을때 undo tablespace full이 발생하면 이중화가 실패하는 문제가 있습니다.](#bug-50177%C2%A0lob%EC%9D%B4-%ED%8F%AC%ED%95%A8%EB%90%9C-%EB%94%94%EC%8A%A4%ED%81%AC-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90-%EC%9D%B4%EC%A4%91%ED%99%94%EA%B0%80-%EA%B1%B8%EB%A0%A4-%EC%9E%88%EC%9D%84%EB%95%8C-undo-tablespace-full%EC%9D%B4-%EB%B0%9C%EC%83%9D%ED%95%98%EB%A9%B4-%EC%9D%B4%EC%A4%91%ED%99%94%EA%B0%80-%EC%8B%A4%ED%8C%A8%ED%95%98%EB%8A%94-%EB%AC%B8%EC%A0%9C%EA%B0%80-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-50196 NOCYLE 옵션으로 생성된 시퀀스가 ALTER SEQUENCE 구문을 수행한 후 서버를 재구동하면, CYCLE로 동작하는 문제가 있습니다.](#bug-50196%C2%A0nocyle-%EC%98%B5%EC%85%98%EC%9C%BC%EB%A1%9C-%EC%83%9D%EC%84%B1%EB%90%9C-%EC%8B%9C%ED%80%80%EC%8A%A4%EA%B0%80-alter-sequence-%EA%B5%AC%EB%AC%B8%EC%9D%84-%EC%88%98%ED%96%89%ED%95%9C-%ED%9B%84-%EC%84%9C%EB%B2%84%EB%A5%BC-%EC%9E%AC%EA%B5%AC%EB%8F%99%ED%95%98%EB%A9%B4-cycle%EB%A1%9C-%EB%8F%99%EC%9E%91%ED%95%98%EB%8A%94-%EB%AC%B8%EC%A0%9C%EA%B0%80-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-50197 메모리 파티션드 테이블 생성 구문에서 LOB 테이블 스페이스 지정에 대한 검증이 미흡합니다.](#bug-50197%C2%A0%EB%A9%94%EB%AA%A8%EB%A6%AC-%ED%8C%8C%ED%8B%B0%EC%85%98%EB%93%9C-%ED%85%8C%EC%9D%B4%EB%B8%94-%EC%83%9D%EC%84%B1-%EA%B5%AC%EB%AC%B8%EC%97%90%EC%84%9C-lob-%ED%85%8C%EC%9D%B4%EB%B8%94-%EC%8A%A4%ED%8E%98%EC%9D%B4%EC%8A%A4-%EC%A7%80%EC%A0%95%EC%97%90-%EB%8C%80%ED%95%9C-%EA%B2%80%EC%A6%9D%EC%9D%B4-%EB%AF%B8%ED%9D%A1%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-50145 aku -p start가 성공하면 aku_start_completed 파일을 생성하는 기능을 추가합니다.

-   **module** :

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : aku -p start 가 정상적으로 완료되면 /tmp 디렉토리에
    aku\_start\_completed 파일을 생성하는 기능을 추가합니다. 이 파일은 aku -p end, aku - p clean 수행시 삭제됩니다. 만약 /tmp에 이미 aku\_start\_completed 파일이 존재하는 경우, aku -p start 명령어를 수행하면 에러메시지가 출력되며 종료합니다.

    aku - p start 수행중 에러가 발생하면, aku_start_completed 파일은 생성되지 않습니다.
    
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

### BUG-50206 aku -p start시 local address에 접속가능 여부를 확인하기 위한 프로퍼티 AKU_ADDRESS_CHECK_COUNT 를 추가합니다.

-   **module** :

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : aku 설정 파일(aku.conf) 파일에 AKU_ADDRESS_CHECK_COUNT 프로퍼티를 추가합니다. 이 프로퍼티를 통해 aku -p start시 local DNS가 엔드포인트에 등록되었는지 확인하는 횟수를 설정할 수 있습니다. 기본값은 30 입니다.

-   **재현 방법**
    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
        -   AKU_ADDRESS_CHECK_COUNT
            -   기본값: 30
            -   설명: aku -p start가 수행되면 AKU_ADDRESS_CHECK_COUNT 설정된 횟수만큼 local ip에 접속을 시도한다.
    -   Compile Option
    -   Error Code

### BUG-50191 altimon에서 CPU 사용률을 측정하기 위해 OS CPU 사용율 측정 쓰레드, 알티베이스 CPU 사용률 측정 쓰레드가 추가되었습니다.

-   **module** : ux-altiMon

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 여러 개의 CPU 모니터링 요소 사용시 상호 시간 간섭현상으로
    부정확한 값을 반환할 수 있습니다. 이를 방지하기 위해, 모니터링
    요소와 독립적인 CPU 사용률 측정 쓰레드가 설정된 간격마다 값을
    측정하며, 모니터링 요소가 측정된 값을 참조하는 형식으로
    변경하였습니다.

    config.xml에 CpuSamplingInterval 항목으로 CPU 사용률(%)을 측정하는
    쓰레드의 실행 주기를 설정할 수 있습니다. 단위는 초(second)입니다. 설정하지
    않을시 기본값은 3초 입니다.

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

### BUG-49101 버퍼에서 페이지 읽기에 실패하는 경우, 페이지의 락이 해제되지 않아 다음 페이지 락에서 HANG이 발생할 수 있습니다.

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

### BUG-49584 LOB 칼럼을 포함한 메모리 파티션드 테이블에 테이블스페이스를 변경하는 DDL 수행시, LOB 칼럼의 테이블 스페이스는 변경되지 않는 문제가 있습니다.

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

### BUG-49890 ALTER SESSION SET REGEXP_MODE = 1 변경 시 PCRE2 라이브러리에서 지원하지 않는 캐릭터셋 일 때 에러 메시지를 변경해야 합니다.

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

### BUG-50010 GroupMetric 중 DBMetric의 수행시 동시성 고려가 필요합니다.

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

### BUG-50024 altimon에서 DB 모니터링 쿼리 결과값이 없는 경우, GroupMetrics로 데이터를 출력할때 값이 누락됩니다.

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

### BUG-50066 DDL 구문 수행 중 실패하면, 동시성 제어에서 해제된 메모리 사용(Free'd Memory Read) 오류가 발생할 수 있습니다.

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

### BUG-50086 Hyper-threading off 환경에서 물리 코어 수를 잘못 산정하는 문제가 있습니다.

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

### BUG-50130 패키지 인스톨러 설치시, 저장 패키지 생성 구문에서 오류가 발생합니다.

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

### BUG-50164 휘발성 테이블에서 공간 부족의 이유로 확장이 실패할 하는경우, 페이지 락이 해제되지 않는 문제가 있습니다.

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

### BUG-50174 altibase.properties.release 파일에서 사용되지 않는 프로퍼티인 REPLICATION_SERVICE_WAIT_MAX_LIMIT를 제거합니다.

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

### BUG-50177 LOB이 포함된 디스크 테이블에 이중화가 걸려 있을때 undo tablespace full이 발생하면 이중화가 실패하는 문제가 있습니다.

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

### BUG-50196 NOCYLE 옵션으로 생성된 시퀀스가 ALTER SEQUENCE 구문을 수행한 후 서버를 재구동하면, CYCLE로 동작하는 문제가 있습니다.

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

### BUG-50197 메모리 파티션드 테이블 생성 구문에서 LOB 테이블 스페이스 지정에 대한 검증이 미흡합니다.

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
