<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Altibase 7.1.0.4.4 Patch Notes](#altibase-71044-patch-notes)
  - [New Features](#new-features)
    - [BUG-47652 iSQL, aexport, iLoader로 생성되는 파일에 대한 접근 권한 제어가 필요합니다](#bug-47652isql-aexport-iloader%EB%A1%9C-%EC%83%9D%EC%84%B1%EB%90%98%EB%8A%94-%ED%8C%8C%EC%9D%BC%EC%97%90-%EB%8C%80%ED%95%9C-%EC%A0%91%EA%B7%BC-%EA%B6%8C%ED%95%9C-%EC%A0%9C%EC%96%B4%EA%B0%80-%ED%95%84%EC%9A%94%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-47902 이중화가 sql apply 모드로 수행 중일때 item 갯수가 같으나 table 구성이 다를 경우 이중화 start가 실패 할수 있습니다.](#bug-47902%EC%9D%B4%EC%A4%91%ED%99%94%EA%B0%80-sql-apply-%EB%AA%A8%EB%93%9C%EB%A1%9C-%EC%88%98%ED%96%89-%EC%A4%91%EC%9D%BC%EB%95%8C-item-%EA%B0%AF%EC%88%98%EA%B0%80-%EA%B0%99%EC%9C%BC%EB%82%98-table-%EA%B5%AC%EC%84%B1%EC%9D%B4-%EB%8B%A4%EB%A5%BC-%EA%B2%BD%EC%9A%B0-%EC%9D%B4%EC%A4%91%ED%99%94-start%EA%B0%80-%EC%8B%A4%ED%8C%A8-%ED%95%A0%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-48066 DDL SYNC를 1로 하고 LOCK TABLE을 한 상태에서 DDL을 수행할 경우 DeadLock이 발생합니다.](#bug-48066ddl-sync%EB%A5%BC-1%EB%A1%9C-%ED%95%98%EA%B3%A0-lock-table%EC%9D%84-%ED%95%9C-%EC%83%81%ED%83%9C%EC%97%90%EC%84%9C-ddl%EC%9D%84-%EC%88%98%ED%96%89%ED%95%A0-%EA%B2%BD%EC%9A%B0-deadlock%EC%9D%B4-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-48069 GEOMETRY 컬럼이 포함된 테이블을 이중화 start한 후 이중화 stop, start를 다시 하면 start가 실패합니다.](#bug-48069geometry-%EC%BB%AC%EB%9F%BC%EC%9D%B4-%ED%8F%AC%ED%95%A8%EB%90%9C-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%9D%84-%EC%9D%B4%EC%A4%91%ED%99%94-start%ED%95%9C-%ED%9B%84-%EC%9D%B4%EC%A4%91%ED%99%94-stop-start%EB%A5%BC-%EB%8B%A4%EC%8B%9C-%ED%95%98%EB%A9%B4-start%EA%B0%80-%EC%8B%A4%ED%8C%A8%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-48076 disk table에 with 구문 사용 시 or 절과 결합된 constant predicate가 존재할 경우 결과 오류](#bug-48076disk-table%EC%97%90-with-%EA%B5%AC%EB%AC%B8-%EC%82%AC%EC%9A%A9-%EC%8B%9C-or-%EC%A0%88%EA%B3%BC-%EA%B2%B0%ED%95%A9%EB%90%9C-constant-predicate%EA%B0%80-%EC%A1%B4%EC%9E%AC%ED%95%A0-%EA%B2%BD%EC%9A%B0-%EA%B2%B0%EA%B3%BC-%EC%98%A4%EB%A5%98)
    - [BUG-48091 사용자 psm에서 메타를 사용하는 경우 meta upgrade가 실패합니다.](#bug-48091%EC%82%AC%EC%9A%A9%EC%9E%90-psm%EC%97%90%EC%84%9C-%EB%A9%94%ED%83%80%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94-%EA%B2%BD%EC%9A%B0-meta-upgrade%EA%B0%80-%EC%8B%A4%ED%8C%A8%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-48096 altibase\_cli.ini.sample 이 패키지에 누락되어 있어서 추가합니다.](#bug-48096altibase%5C_cliinisample-%EC%9D%B4-%ED%8C%A8%ED%82%A4%EC%A7%80%EC%97%90-%EB%88%84%EB%9D%BD%EB%90%98%EC%96%B4-%EC%9E%88%EC%96%B4%EC%84%9C-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-48101 distinct sort에 중복된 target을 사용하는 경우 결과 오류가 발생합니다.](#bug-48101distinct-sort%EC%97%90-%EC%A4%91%EB%B3%B5%EB%90%9C-target%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94-%EA%B2%BD%EC%9A%B0-%EA%B2%B0%EA%B3%BC-%EC%98%A4%EB%A5%98%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-48113 DATE 변환시 malloc free 제거](#bug-48113date-%EB%B3%80%ED%99%98%EC%8B%9C-malloc-free-%EC%A0%9C%EA%B1%B0)
    - [BUG-48116 recursive with 구문의 view가 재시작 할경우 조건에 따라 비정상 종료할 수 있습니다.](#bug-48116recursive-with-%EA%B5%AC%EB%AC%B8%EC%9D%98-view%EA%B0%80-%EC%9E%AC%EC%8B%9C%EC%9E%91-%ED%95%A0%EA%B2%BD%EC%9A%B0-%EC%A1%B0%EA%B1%B4%EC%97%90-%EB%94%B0%EB%9D%BC-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-48119 7.1.0.3.0 이상의 클라이언트에서 7.1.0.2.9 이하의 서버로 is, iloader 수행시, Incompatible property 에러 발생합니다.](#bug-4811971030-%EC%9D%B4%EC%83%81%EC%9D%98-%ED%81%B4%EB%9D%BC%EC%9D%B4%EC%96%B8%ED%8A%B8%EC%97%90%EC%84%9C-71029-%EC%9D%B4%ED%95%98%EC%9D%98-%EC%84%9C%EB%B2%84%EB%A1%9C-is-iloader-%EC%88%98%ED%96%89%EC%8B%9C-incompatible-property-%EC%97%90%EB%9F%AC-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-48125 Merge 쿼리 동작시 Trigger가 있을 경우 간헐적으로 에러가 발생하거나 비정상 종료 할 수 있습니다.](#bug-48125merge-%EC%BF%BC%EB%A6%AC-%EB%8F%99%EC%9E%91%EC%8B%9C-trigger%EA%B0%80-%EC%9E%88%EC%9D%84-%EA%B2%BD%EC%9A%B0-%EA%B0%84%ED%97%90%EC%A0%81%EC%9C%BC%EB%A1%9C-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%98%EA%B1%B0%EB%82%98-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C-%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Altibase 7.1.0.4.4 Patch Notes
==============================

New Features
------------

### BUG-47652 iSQL, aexport, iLoader로 생성되는 파일에 대한 접근 권한 제어가 필요합니다

-   **module** : ux-isql

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **증상** : iSQL, aexport, iLoader로 생성되는 파일에 대한 접근
    권한제어가 가능한 환경 변수 ALTIBASE\_UT\_FILE\_PERMISSION ,
    ISQL\_FILE\_PERMISSION, AEXPORT\_FILE\_PERMISSION,
    ILO\_FILE\_PERMISSION 이 추가되었습니다.

    파일에 대한 접근 권한제어를 설정하기 위해서는 위 프로퍼티의 값을
    파일 권한설정 값으로 선언하면 됩니다.

    예를 들어, iSQL로 생성되는 파일만 user:rw,  group:rw,  other:--
    권한으로 설정하고자 하면, 아래와 같이 환경변수를 추가하면 됩니다.

     % export ISQL_FILE_PERMISSION=660

    이 기능은 리눅스 및 유닉스 계열에서만 사용 가능합니다. (윈도우에서는
    지원하지 않는 기능입니다.)

-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

- **변경사항**

  -   Performance view
  - Property
    - [ALTIBASE_UT_FILE_PERMISSION](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/iSQL.md#altibase_ut_file_permission)
       - 속성 설명 : aexport, iLoader, iSQL이 생성하는 파일들의
      권한을 설정하는 공통 환경변수
       - 변경/추가/삭제 : 추가
       - 공개/비공개 : 공개
       - 최소값, 최대값, 기본값 : 값을 설정하지 않으면 666 (user:rw,  group:rw,  other: rw)로 설정

    - [ISQL_FILE_PERMISSION](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/iSQL.md#isql_file_permission)
       - 속성 설명 : iSQL이 생성하는 파일들의 권한을 설정하는 환경
      변수로, ALTIBASE_UT_FILE_PERMISSION이 설정되어
      있더라도 ISQL_FILE_PERMISSION이 우선합니다.
       - 변경/추가/삭제 : 추가
       - 공개/비공개 : 공개
       - 최소값, 최대값, 기본값 : 값을 설정하지 않으면 666 (user:rw,  group:rw,  other: rw)로 설정

    - [AEXPORT_FILE_PERMISSION](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Utilities.md#aexport_file_permission)
       - 속성 설명 : aexport가 생성하는 파일들의 권한을 설정하는
      환경 변수로, ALTIBASE_UT_FILE_PERMISSION이 설정되어
      있더라도 AEXPORT_FILE_PERMISSION이 우선합니다.
       - 변경/추가/삭제 : 추가
       - 공개/비공개 : 공개
       - 최소값, 최대값, 기본값 : 값을 설정하지 않으면 666 (user:rw,  group:rw,  other: rw)로 설정

    - [ILO_FILE_PERMISSION](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/iLoader.md#ilo_file_permission)
       - 속성 설명 : iLoader가 생성하는 파일들의 권한을 설정하는
      환경 변수로, ALTIBASE_UT_FILE_PERMISSION이 설정되어
      있더라도 ILO_FILE\_PERMISSION이 우선합니다.
       - 변경/추가/삭제 : 추가
       - 공개/비공개 : 공개
       - 최소값, 최대값, 기본값 : 값을 설정하지 않으면 666 (user:rw,  group:rw,  other: rw)로 설정

  -   Compile Option
  -   Error Code
      -   326, HY000, utERR\_ABORT\_FilePerm\_OutOfRange\_Error = File
          permission value is out of range (\<0%s\>=\<1%s\>)
          \# \*Cause: File permission value is out of range.
          \# \*Action: Use valid file permission value.

Fixed Bugs
----------

### BUG-47902 이중화가 sql apply 모드로 수행 중일때 item 갯수가 같으나 table 구성이 다를 경우 이중화 start가 실패 할수 있습니다.

-   **module** : rp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : 이중화가 sql apply 모드로 수행 중일때 item 갯수가 같으나
    table 구성이 다를 경우, 이중화 start가 실패 할수 있습니다.

    item 갯수가 같아도 동일한 partition item이 있는지 체크하도록 하여
    문제 발생하지 않도록 수정하였습니다.

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

### BUG-48066 DDL SYNC를 1로 하고 LOCK TABLE을 한 상태에서 DDL을 수행할 경우 DeadLock이 발생합니다.

-   **module** : rp

-   **Category** : Other

-   **재현 빈도** : Always

-   **증상** : DDL SYNC 1인 상태에서  LOCK TABLE T1 IN EXCLUSIVE MODE
    UNTIL NEXT DDL 을 한후 DDL을 하면 deadlock이 발생합니다.

    DDL SYNC 1일때 DDL을 수행하면 DDL SYNC를 수행하기 위해 새로운
    트랜젝션을 열어서 is lock을 잡게 되는데 이미 Table lock을 잡고
    있고 timeout 값이 ULONG MAX 여서 deadlock이 발생하게 됩니다.

    그래서 DDL SYNC 1이고 LOCK TABLE ... UNTIL NEXT DDL인 경우에 DDL을
    수행하면 에러처리하도록 수정하였습니다.

    그리고 DDL Sync시에도 Table에 Lock을 잡을때 timeout 값을 DDL Lock
    timeout 값을 쓰도록 수정하였습니다.

-   **재현 방법**

    -   **재현 절차**

            ALTER SYSTEM SET REPLICATION_DDL_SYNC = 1;
            ALTER SESSION SET REPLICATION_DDL_SYNC = 1;   
            ALTER REPLICATION REP1 START;
            AUTOCOMMIT OFF;
            LOCK TABLE T1 IN EXCLUSIVE MODE UNTIL NEXT DDL;
            ALTER REPLICATION REP1 STOP;
            ALTER TABLE T1 SPLIT PARTITION P2 AT(20) INTO( PARTITION P3, PARTITION P4 );

    -   **수행 결과**

            hang

    -   **예상 결과**

            ALTER FAIL

-   **Workaround**

        LOCK TABLE T1 IN EXCLUSIVE MODE UNTIL NEXT DDL; 하지 않거나 REPLICATION_DDL_SYNC를 0으로 함

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48069 GEOMETRY 컬럼이 포함된 테이블을 이중화 start한 후 이중화 stop, start를 다시 하면 start가 실패합니다.

-   **module** : rp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : 이중화 old meta table에 srid 관련 column이 없어서 이중화
    재시작시 srid 정보가 잘못되어 발생한 문제입니다.

    SYS\_REPL\_OLD\_COLUMNS\_ meta table에 MT\_SRID column을 추가하여
    srid 정보를 저장하도록 수정하였습니다.

-   **재현 방법**

    -   **재현 절차**

            CREATE TABLE T1 ( I1 INTEGER PRIMARY KEY, OBJ GEOMETRY SRID 100 );
            CREATE REPLICATION REP1 WITH ...
                   FROM SYS.T1 TO SYS.T1;
            ALTER REPLICATION REP1 START;
            ALTER REPLICATION REP1 STOP;
            ALTER REPLICATION REP1 START;

    -   **수행 결과**

            [ERR-6100D : [Sender] Failed to handshake with the peer server (The geometry SRID of the replicated table's column does not match. [T1(Name:OBJ, SRID:0):T1(Name:OBJ, SRID: 100)].)]

    -   **예상 결과**

            Alter success.

-   **Workaround**

        이중화 재생성

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48076 disk table에 with 구문 사용 시 or 절과 결합된 constant predicate가 존재할 경우 결과 오류

-   **module** : qp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : disk table에 with 구문 사용 시 or 절과 결합된 constant
    predicate가 존재할 경우 결과 오류 수정

-   **재현 방법**

    -   **재현 절차**

            drop table MA_PLANT_MST;
            create table MA_PLANT_MST( 
            COMPANY_CD                               VARCHAR(28)                 NOT NULL,
            PLANT_CD                                 VARCHAR(28)                 NOT NULL,
            PLANT_NM                                 VARCHAR(200)                NOT NULL
            ) tablespace sys_tbs_disk_data;
            alter table MA_PLANT_MST add primary key ( COMPANY_CD, PLANT_CD );
            INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('1000', 'DETAIL_AUTH_NOT_USED', 'TEST');
            INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('1001', 'DETAIL_AUTH_NOT_USED', 'TEST');
            INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('1002', 'DETAIL_AUTH_NOT_USED', 'TEST');
            INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('1003', 'DETAIL_AUTH_NOT_USED', 'TEST');
            INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('1004', 'DETAIL_AUTH_NOT_USED', 'TEST');
            INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('1005', 'DETAIL_AUTH_NOT_USED', 'TEST');
            INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('1006', 'DETAIL_AUTH_NOT_USED', 'TEST');
            INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('1007', 'DETAIL_AUTH_NOT_USED', 'TEST');
            INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('1008', 'DETAIL_AUTH_NOT_USED', 'TEST');
            INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('1009', 'DETAIL_AUTH_NOT_USED', 'TEST');
            INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('1010', 'DETAIL_AUTH_NOT_USED', 'TEST');
            INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('1011', 'DETAIL_AUTH_NOT_USED', 'TEST');
            INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('1012', 'DETAIL_AUTH_NOT_USED', 'TEST');
            INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('1013', 'DETAIL_AUTH_NOT_USED', 'TEST');
            INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('KC_TEST', 'DETAIL_AUTH_NOT_USED1', 'TEST');
            INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('KC_TEST', 'DETAIL_AUTH_NOT_USED2', 'TEST');
            INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('KC_TEST', 'DETAIL_AUTH_NOT_USED3', 'TEST');
            INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('KC_TEST', 'DETAIL_AUTH_NOT_USED4', 'TEST');
            INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('KC_TEST', 'DETAIL_AUTH_NOT_USED5', 'TEST');
            INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('KC_TEST', 'DETAIL_AUTH_NOT_USED6', 'TEST');
            CREATE OR REPLACE FUNCTION upper_function(p1 IN VARCHAR)
            RETURN VARCHAR
            AS
            BEGIN
              RETURN UPPER(p1);
            END;
            /
            PREPARE
            WITH MPM_W AS
            (
            SELECT  *
                            FROM    MA_PLANT_MST MPM
                            WHERE COMPANY_CD = 'KC_TEST'
            )
            SELECT /*+ */ * FROM MPM_W WHERE MPM_W.PLANT_CD IN
                             (
                                    'test'
                             ) OR upper_function(lower('KC_TEST')) = 'KC_TEST';

    -   **수행 결과**

            No rows selected.

    -   **예상 결과**

            KC_TEST                       DETAIL_AUTH_NOT_USED1TEST                                                                                                                                                                                               KC_TEST                       DETAIL_AUTH_NOT_USED2TEST                                                                                                                                                                                               KC_TEST                       DETAIL_AUTH_NOT_USED3TEST                                                                                                                                                                                               KC_TEST                       DETAIL_AUTH_NOT_USED4TEST                                                                                                                                                                                               KC_TEST                       DETAIL_AUTH_NOT_USED5TEST                                                                                                                                                                                               KC_TEST                       DETAIL_AUTH_NOT_USED6TEST                                                                                                                                                                                               6 rows selected.

-   **Workaround**

        둘 중 하나의 방법으로 Work Around 가능합니다.
        1. 히든 프로퍼티 사용
        alter system set __OPTIMIZER_OR_VALUE_INDEX = 0;
        2. 인덱스 추가 후 사용 하도록 쿼리 변경
        CREATE INDEX MPM_I2 ON MA_PLANT_MST( COMPANY_CD );
        PREPARE
        WITH MPM_W AS
        (
        SELECT  *
                        FROM    MA_PLANT_MST MPM
                        WHERE COMPANY_CD = 'KC_TEST'
        )
        SELECT /*+ INDEX(MPM_W, MPM_I2) */ * FROM MPM_W WHERE MPM_W.PLANT_CD IN
                         (
                                'test'
                         ) OR upper_function(lower('KC_TEST')) = 'KC_TEST';

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48091 사용자 psm에서 메타를 사용하는 경우 meta upgrade가 실패합니다.

-   **module** : qp-meta

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : 사용자 psm에서 메타를 사용하는 경우 meta upgrade가
    실패합니다.

-   **재현 방법**

    -   **재현 절차**

            1) 메타 테이블을 PSM내부에 사용
            SYS_PROCEDURES_ 
            SYS_PACKAGES_
            SYS_REPL_HOSTS_
            SYS_REPL_OLD_ITEMS_
            SYS_REPLICATIONS_
            2) 메타버전 8.3.1 이하에서 8.3.1 이상으로 패치하는 경우

    -   **수행 결과**

            [ERR-91015 : Communication failure.]

    -   **예상 결과**

            server start success.
            --- STARTUP Process SUCCESS ---
            Command executed successfully.

-   **Workaround**

        psm backup -> drop  -> patch 

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48096 altibase\_cli.ini.sample 이 패키지에 누락되어 있어서 추가합니다.

-   **module** : pkg-map

-   **Category** : Usability

-   **재현 빈도** : Always

-   **증상** : altibase\_cli.ini.sample 이 패키지에 누락되어 있어서 추가합니다.
    
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

### BUG-48101 distinct sort에 중복된 target을 사용하는 경우 결과 오류가 발생합니다.

-   **module** : qp-select-pvo

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : distinct에 중복된 target을 사용하는 경우 결과 오류 문제를
    수정합니다.

- **재현 방법**

  -   **재현 절차**

          drop table t1;
          create table t1 (i1 varchar(11), i2 int);
          insert into t1 values( '20000230712', 179820);
          insert into t1 values( '20000230714', 227810);
          insert into t1 values( '20000230718', 460280);
          select /*+ distinct_sort*/
               distinct 
                  a.i1
                , 1* a.i2
                , 1 * b.c2
                , a.i2 - b.c2 a1
                , a.i2 - b.c2 a2
          from ( select /*+ no_merge*/ i1, i2 from t1 ) a 
             left outer join 
               ( select i1, (i2 * 0) as c2 from t1 ) b
             on b.i1 = a.i1;

  - **수행 결과**

        I1           1*A.I2                 1*B.C2                 A1                     A2
        ---------------------------------------------------------------------------------------------------------------
        20000230712  179820                 0                      460280                 460280
        20000230714  227810                 0                      460280                 460280
        20000230718  460280                 0                      460280                 460280
        3 rows selected.

  -   **예상 결과**

          I1           1*A.I2                 1*B.C2                 A1                     A2
          ---------------------------------------------------------------------------------------------------------------
          20000230712  179820                 0                      179820                 179820
          20000230714  227810                 0                      227810                 227810
          20000230718  460280                 0                      460280                 460280
          3 rows selected.

-   **Workaround**

        distinct_hash

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48113 DATE 변환시 malloc free 제거

-   **module** : mt-function

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **증상** : DATE 변환시 malloc free 제거

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

### BUG-48116 recursive with 구문의 view가 재시작 할경우 조건에 따라 비정상 종료할 수 있습니다.

-   **module** : qp-dml-execute

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **증상** : recursive with 구문의 view가 재시작 할경우 조건에 따라 비정상 종료하는 문제를 수정하였습니다.
    
- **재현 방법**

  -   **재현 절차**

          drop table t1;
          create table t1 ( COMPANY_CD varchar(28), PCA_GRP_CD varchar(80) );
          insert into t1 values ( '1000', '22000' );
          insert into t1 values ( '1000', '23000' );
          insert into t1 values ( '1000', '24000' );
          insert into t1 values ( '1000', '25000' );
          drop table t2;
          create table t2 ( COMPANY_CD varchar(28), PCA_GRP_CD varchar(80), PCA_CD VARCHAR(80) VARIABLE);
          insert into t2 values ( '1000', '24000', '24507');
          insert into t2 values ( '1000', '25000', '25509' );
          insert into t2 values ( '1000', '25000', '25500' );
          drop table t3;
          create table t3 ( COMPANY_CD varchar(28), PCA_GRP_CD varchar(80), ACCT_CD VARCHAR(80) VARIABLE, i1 int );
          insert into t3 values ( '1000', '25000', '10112030', 1 );
          drop table t4;
          create table t4 ( COMPANY_CD varchar(28), PCA_GRP_CD varchar(80) );
          insert into t4 values ( '1000', '22000' );
          insert into t4 values ( '1000', '23000' );
          drop table t5;
          create table t5 ( COMPANY_CD varchar(28), PC_CD varchar(80), DOCU_NO VARCHAR(80) VARIABLE, ACCT_CD VARCHAR(80) VARIABLE, i1 int );
          insert into t5 values ( '1000', '1000', 'FIA202008030009', '14410010', 1 );
          insert into t5 values ( '1000', '2000', 'FI203006300003', '10112030', 1 );
          drop table t6;
          create table t6 ( COMPANY_CD varchar(28), PC_CD varchar(80), DOCU_NO VARCHAR(80) VARIABLE, MNGD_CD VARCHAR(80) VARIABLE, i1 int );
          insert into t6 values ( '1000', '2000', 'FI203006300003', '25500', 1 );
          WITH T_MA_PCAGRP_MST( COMPANY_CD, PCA_GRP_CD, ROOT_PCA_GRP_CD ) AS (
                      SELECT COMPANY_CD, PCA_GRP_CD, PCA_GRP_CD AS ROOT_PCA_GRP_CD
                      FROM   t1
                      WHERE  COMPANY_CD = '1000'
                      UNION ALL
                      SELECT MPM.COMPANY_CD, MPM.PCA_GRP_CD, T_MPM.ROOT_PCA_GRP_CD
                      FROM   t1 MPM
                             INNER JOIN T_MA_PCAGRP_MST T_MPM
                             ON  MPM.COMPANY_CD = T_MPM.COMPANY_CD
                             AND MPM.PCA_GRP_CD = T_MPM.PCA_GRP_CD
                      WHERE  MPM.COMPANY_CD = '1000'
                  ),
              T_MA_PCAGRP_DTL AS (
                      SELECT MPD.PCA_CD, MPD.COMPANY_CD, T_MPM.ROOT_PCA_GRP_CD
                      FROM   t2 MPD
                             INNER JOIN T_MA_PCAGRP_MST T_MPM
                             ON  MPD.COMPANY_CD = T_MPM.COMPANY_CD
                             AND MPD.PCA_GRP_CD = T_MPM.PCA_GRP_CD
                      WHERE  MPD.COMPANY_CD = '1000'
                  )
             SELECT A.COMPANY_CD 
                    FROM t3 A
                         INNER JOIN t4 C ON C.COMPANY_CD = A.COMPANY_CD 
                         INNER JOIN t5 B ON C.COMPANY_CD = B.COMPANY_CD 
                         INNER JOIN t6 E ON E.COMPANY_CD = B.COMPANY_CD AND E.PC_CD = B.PC_CD AND E.DOCU_NO = B.DOCU_NO 
                         LEFT OUTER JOIN t3 H ON 
                            A.COMPANY_CD = H.COMPANY_CD 
                            AND H.PCA_GRP_CD IN ( SELECT /*+  */ ROOT_PCA_GRP_CD FROM T_MA_PCAGRP_DTL WHERE  PCA_CD = E.MNGD_CD   )
                            AND H.ACCT_CD = B.ACCT_CD;

  -   **수행 결과**

          [ERR-91015 : Communication failure.]

  -   **예상 결과**

          COMPANY_CD
          --------------------------------
          1000
          1000
          2 rows selected.

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48119 7.1.0.3.0 이상의 클라이언트에서 7.1.0.2.9 이하의 서버로 is, iloader 수행시, Incompatible property 에러 발생합니다.

-   **module** : rp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** :
    GLOBAL_TRANSACTION_LEVEL (구DBLINK_GLOBAL_TRANSACTION_LEVEL) 프로퍼티가 7.1.0.3.0 에서 이름이 변경되었습니다. 이로 인해, 7.1.0.3.0 이상의 클라이언트에서 7.1.0.2.9 이하의 서버로 is, iloader 수행시  [ERR-5108B : Incompatible property : [GLOBAL_TRANSACTION_LEVEL]. Upgrade server.] 에러로 접속이 되지 않습니다. 이 프로퍼티는 ShardCLI에서만 사용되는 프로퍼티로, ALTIBASE CLI 접속시에 해당 프로퍼티를 체크하지 않도록 수정합니다
    
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

### BUG-48125 Merge 쿼리 동작시 Trigger가 있을 경우 간헐적으로 에러가 발생하거나 비정상 종료 할 수 있습니다.

-   **module** : qp-psm-trigger-execute

-   **Category** : Fatal

-   **재현 빈도** : Rare

-   **증상** : Merge 쿼리 동작시 Trigger가 있을 경우 간헐적으로  에러가 발생하거나 비정상 종료 하는 문제를 수정하였습니다.
    
-   **재현 방법**

    -   **재현 절차**

            drop table t1;
            create table t1 (
            SVC_CONT_ID                              VARCHAR(20)     FIXED ,
            EFCT_ST_DT                               DATE            FIXED ,
            EFCT_FNS_DT                              DATE            FIXED ,
            APLY_BILL_TGT_YM                         varchar(20)
            );
            insert into t1 values( 'S2030835670',           to_date('30-JUN-2020'),  to_date('31-DEC-9999'),  '202006');
            insert into t1 values( 'S2030860590',           to_date('30-JUN-2020'),  to_date('31-DEC-9999'),  '202006');
            insert into t1 values( 'S2030837090',           to_date('10-JUN-2020'),  to_date('31-DEC-9999'),  '202006');
            insert into t1 values( 'S2030837070',           to_date('20-JUN-2020'),  to_date('31-DEC-9999'),  '202006');
            insert into t1 values( 'S2030843010',           to_date('23-JUN-2020'),  to_date('31-DEC-9999'),  '202006');
            insert into t1 values( 'S2030849390',           to_date('19-JUN-2020'),  to_date('31-DEC-9999'),  '202006');
            insert into t1 values( 'S2030860630',           to_date('29-JUN-2020'),  to_date('31-DEC-9999'),  '202006');
            insert into t1 values( 'S0000407100',           to_date('26-JUN-2020'),  to_date('31-DEC-9999'),  '202006');
            insert into t1 values( 'S0000263580',           to_date('04-JUN-2020'),  to_date('31-DEC-9999'),  '202006');
            insert into t1 values( 'S2030848490',           to_date('24-JUN-2020'),  to_date('31-DEC-9999'),  '202006');
            insert into t1 values( 'S2030858690',           to_date('30-JUN-2020'),  to_date('31-DEC-9999'),  '202006');
            insert into t1 values( 'S2030837610',           to_date('22-JUN-2020'),  to_date('31-DEC-9999'),  '202006');
            insert into t1 values( 'S0000327500',           to_date('04-JUN-2020'),  to_date('31-DEC-9999'),  '202006');
            insert into t1 values( 'S2030849550',           to_date('04-JUN-2020'),  to_date('31-DEC-9999'),  '202006');
            insert into t1 values( 'S2030836150',           to_date('23-JUN-2020'),  to_date('31-DEC-9999'),  '202006');
            insert into t1 values( 'S2030837530',           to_date('27-JUN-2020'),  to_date('31-DEC-9999'),  '202006');
            insert into t1 select level, sysdate, sysdate, level from dual connect by level < 90000;
            drop table t2;
            create table t2 (
                 SVC_CONT_ID                              VARCHAR(20)     FIXED ,
                 SVC_CONT_SBSC_DT                         DATE            FIXED,
                  BM_CTG_CD                                VARCHAR(20)     FIXED ,
                  LAST_SVC_CONT_STTUS_CD                   VARCHAR(3)      FIXED 
            );
            insert into t2 values( 'S2030858690',           to_date('01-JAN-2020'),  '928001', 'C');
            insert into t2 values( 'S0000263580',           to_date('02-OCT-2018'),  '928001', 'C');
            insert into t2 values( 'S0000327500',           to_date('03-NOV-2018'),  '928001', 'C');
            insert into t2 values( 'S2030849550',           to_date('05-APR-2020'),  '928001', 'C');
            insert into t2 values( 'S2030848490',           to_date('28-MAY-2020'),  '928001', 'C');
            insert into t2 values( 'S2030837530',           to_date('17-APR-2020'),  '928001', 'C');
            insert into t2 values( 'S2030835670',           to_date('13-APR-2020'),  '928001', 'C');
            insert into t2 values( 'S2030837610',           to_date('17-MAR-2020'),  '928001', 'C');
            insert into t2 values( 'S2030837090',           to_date('13-APR-2020'),  '928001', 'C');
            insert into t2 values( 'S2030837070',           to_date('05-FEB-2020'),  '928001', 'C');
            insert into t2 values( 'S2030836150',           to_date('14-APR-2020'),  '928001', 'C');
            insert into t2 values( 'S2030843010',           to_date('15-MAY-2020'),  '928001', 'C');
            insert into t2 values( 'S2030849390',           to_date('30-MAY-2020'),  '928001', 'C');
            insert into t2 values( 'S2030860590',           to_date('26-JUN-2020'),  '928001', 'C');
            insert into t2 values( 'S2030860630',           to_date('26-JUN-2020'),  '928001', 'C');
            insert into t2 values( 'S0000407100',           to_date('19-JUL-2018'),  '928001', 'C');
            insert into t2 select level, sysdate, level, 'X' from dual connect by level < 70000;
            drop table t3;
            create table t3 (
                 SVC_CONT_ID                              VARCHAR(20)     FIXED,
                 PROD_ID                                  VARCHAR(20)     FIXED 
            );
            insert into t3 values('S0000263580','P00100001');
            insert into t3 values('S2030849550','P00100161');
            insert into t3 values('S0000327500','P00100001');
            insert into t3 values('S2030837530','P00100001');
            insert into t3 values('S2030837610','P00100046');
            insert into t3 values('S2030836150','P00100158');
            insert into t3 values('S2030835670','P00100158');
            insert into t3 values('S2030837530','P00100046');
            insert into t3 values('S2030837070','P00100158');
            insert into t3 values('S2030837090','P00100158');
            insert into t3 values('S2030848490','P00100164');
            insert into t3 values('S2030858690','P00100161');
            insert into t3 values('S2030837070','P00100164');
            insert into t3 values('S2030843010','P00100046');
            insert into t3 values('S2030860630','P00100161');
            insert into t3 values('S2030849550','P00100158');
            insert into t3 values('S2030849390','P00100161');
            insert into t3 values('S2030860590','P00100161');
            insert into t3 values('S0000407100','P00100001');
            insert into t3 values('S2030843010','P00100001');
            insert into t3  select level, level from dual connect by level < 110000;
            drop trigger trig1;
            create or replace trigger trig1
            after UPDATE
            on t1
            REFERENCING NEW AS NEW_ROW OLD AS OLD_ROW
            FOR EACH ROW
            AS
            SVC_CONT_ID     VARCHAR(20);
            BEGIN    
                SVC_CONT_ID := 'XX';
                insert into t3  values ( SVC_CONT_ID, NULL );
            END;
            /
            drop trigger trig2;
            create or replace trigger trig2
            after UPDATE
            on t1
            REFERENCING NEW AS NEW_ROW OLD AS OLD_ROW
            FOR EACH ROW
            AS
            SVC_CONT_ID     VARCHAR(20);
            BEGIN    
                SVC_CONT_ID := 'XX';
                insert into t2 (SVC_CONT_ID) values ( SVC_CONT_ID );
            END;
            /
             MERGE INTO t1 A
                USING (
                        SELECT B.* FROM t2 B
                        JOIN t3 C ON B.SVC_CONT_ID = C.SVC_CONT_ID AND C.PROD_ID LIKE 'P%'
                            AND PROD_ID != 'P00100165'
                        WHERE B.SVC_CONT_SBSC_DT IS NOT NULL AND B.BM_CTG_CD = '928001'
                    ) B  ON (A.SVC_CONT_ID = B.SVC_CONT_ID AND B.LAST_SVC_CONT_STTUS_CD = 'C'
                    AND A.EFCT_ST_DT BETWEEN TO_DATE('202006', 'YYYYMM') AND LAST_DAY(TO_DATE('202006', 'YYYYMM'))+0.99999
                     AND A.EFCT_ST_DT - B.SVC_CONT_SBSC_DT > 1
                     )
                 WHEN MATCHED THEN
                 UPDATE SET A.APLY_BILL_TGT_YM = '202006';

    -   **수행 결과**

    -   **예상 결과**
    
            20 rows merged.
    
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
| 7.1.0.4.4        | 6.5.1                   | 8.8.1        | 7.1.7               | 7.4.6                        | 2.2.1            |

> Altibase 7.1 패치 버전별 히스토리는 [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7_1_Version_Histories.md)에서 확인할 수 있다.

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

Replication 프로토콜 버전은 변경되지 않았다..

#### Sharding Version

샤딩 버전은 변경 되지 않았다.

> 알티베이스 샤딩 프로토콜 및 메타는 상위, 하위 호환성을 보장하지
> 않는다. 즉, 샤딩 버전이 다른 경우, 재구성해야 한다.

### 프로퍼티

#### 추가된 프로퍼티

* [ALTIBASE_UT_FILE_PERMISSION](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/iSQL.md#altibase_ut_file_permission)
* [ISQL_FILE_PERMISSION](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/iSQL.md#isql_file_permission)
* [AEXPORT_FILE_PERMISSION](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Utilities.md#aexport_file_permission)
* [ILO_FILE_PERMISSION](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/iLoader.md#ilo_file_permission)

### 성능 뷰

추가/변경/삭제된 성능 뷰 없음.