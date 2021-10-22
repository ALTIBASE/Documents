<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Altibase 7.1.0.1.6 Patch Notes](#altibase-71016-patch-notes)
  - [New Features](#new-features)
    - [BUG-46406  merge 구문에 문법(syntax) 확장](#bug-46406-merge-%EA%B5%AC%EB%AC%B8%EC%97%90-%EB%AC%B8%EB%B2%95syntax-%ED%99%95%EC%9E%A5)
    - [BUG-46481  micro second sleep 을 지원하는 시스템 저장 프로시저 sleep2가 추가되었습니다.](#bug-46481-micro-second-sleep-%EC%9D%84-%EC%A7%80%EC%9B%90%ED%95%98%EB%8A%94-%EC%8B%9C%EC%8A%A4%ED%85%9C-%EC%A0%80%EC%9E%A5-%ED%94%84%EB%A1%9C%EC%8B%9C%EC%A0%80-sleep2%EA%B0%80-%EC%B6%94%EA%B0%80%EB%90%98%EC%97%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-46402  메모리 인덱스에 할당된 메모리는 mempool로 반환되지 않습니다.](#bug-46402-%EB%A9%94%EB%AA%A8%EB%A6%AC-%EC%9D%B8%EB%8D%B1%EC%8A%A4%EC%97%90-%ED%95%A0%EB%8B%B9%EB%90%9C-%EB%A9%94%EB%AA%A8%EB%A6%AC%EB%8A%94-mempool%EB%A1%9C-%EB%B0%98%ED%99%98%EB%90%98%EC%A7%80-%EC%95%8A%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-46436  모니터링 API의 ABISqlText에 time 항목을 추가해야 합니다.](#bug-46436-%EB%AA%A8%EB%8B%88%ED%84%B0%EB%A7%81-api%EC%9D%98-abisqltext%EC%97%90-time-%ED%95%AD%EB%AA%A9%EC%9D%84-%EC%B6%94%EA%B0%80%ED%95%B4%EC%95%BC-%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-46480  JDBC insert 성능개선을 위한 내부 함수 리펙토링](#bug-46480-jdbc-insert-%EC%84%B1%EB%8A%A5%EA%B0%9C%EC%84%A0%EC%9D%84-%EC%9C%84%ED%95%9C-%EB%82%B4%EB%B6%80-%ED%95%A8%EC%88%98-%EB%A6%AC%ED%8E%99%ED%86%A0%EB%A7%81)
    - [BUG-46485  iloader 성능개선을 위해 double 데이터의 바인딩 타입을 SQL\_C\_DOUBLE에서 SQL\_C\_CHAR로 수정해야 합니다](#bug-46485-iloader-%EC%84%B1%EB%8A%A5%EA%B0%9C%EC%84%A0%EC%9D%84-%EC%9C%84%ED%95%B4-double-%EB%8D%B0%EC%9D%B4%ED%84%B0%EC%9D%98-%EB%B0%94%EC%9D%B8%EB%94%A9-%ED%83%80%EC%9E%85%EC%9D%84-sql%5C_c%5C_double%EC%97%90%EC%84%9C-sql%5C_c%5C_char%EB%A1%9C-%EC%88%98%EC%A0%95%ED%95%B4%EC%95%BC-%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-46486  iloader 성능 개선을 위해, 버퍼로부터 데이터를 읽을 때 레코드 단위가 아니라 array 단위로 Lock을 획득하도록 수정해야 합니다](#bug-46486-iloader-%EC%84%B1%EB%8A%A5-%EA%B0%9C%EC%84%A0%EC%9D%84-%EC%9C%84%ED%95%B4-%EB%B2%84%ED%8D%BC%EB%A1%9C%EB%B6%80%ED%84%B0-%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%A5%BC-%EC%9D%BD%EC%9D%84-%EB%95%8C-%EB%A0%88%EC%BD%94%EB%93%9C-%EB%8B%A8%EC%9C%84%EA%B0%80-%EC%95%84%EB%8B%88%EB%9D%BC-array-%EB%8B%A8%EC%9C%84%EB%A1%9C-lock%EC%9D%84-%ED%9A%8D%EB%93%9D%ED%95%98%EB%8F%84%EB%A1%9D-%EC%88%98%EC%A0%95%ED%95%B4%EC%95%BC-%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-46085  캐싱된 플랜을 확인하는 과정에서 할당된 Query\_Prepare 메모리를 해제하지 않습니다.](#bug-46085-%EC%BA%90%EC%8B%B1%EB%90%9C-%ED%94%8C%EB%9E%9C%EC%9D%84-%ED%99%95%EC%9D%B8%ED%95%98%EB%8A%94-%EA%B3%BC%EC%A0%95%EC%97%90%EC%84%9C-%ED%95%A0%EB%8B%B9%EB%90%9C-query%5C_prepare-%EB%A9%94%EB%AA%A8%EB%A6%AC%EB%A5%BC-%ED%95%B4%EC%A0%9C%ED%95%98%EC%A7%80-%EC%95%8A%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-46389  APRE usage 에 silent 옵션이 누락되었습니다.](#bug-46389-apre-usage-%EC%97%90-silent-%EC%98%B5%EC%85%98%EC%9D%B4-%EB%88%84%EB%9D%BD%EB%90%98%EC%97%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-46390  IPCDA 세션 종료시 Client의 세션종료 여부를 확인하는 로직이 누락되어 있습니다.](#bug-46390-ipcda-%EC%84%B8%EC%85%98-%EC%A2%85%EB%A3%8C%EC%8B%9C-client%EC%9D%98-%EC%84%B8%EC%85%98%EC%A2%85%EB%A3%8C-%EC%97%AC%EB%B6%80%EB%A5%BC-%ED%99%95%EC%9D%B8%ED%95%98%EB%8A%94-%EB%A1%9C%EC%A7%81%EC%9D%B4-%EB%88%84%EB%9D%BD%EB%90%98%EC%96%B4-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-46483  HP jdbcAdapter 에서 LD\_LIBRARY\_PATH를 설정하지 않아도 oaUtility start 수행시 에러가 발생하지 않습니다.](#bug-46483-hp-jdbcadapter-에서-ld_library_path를-설정하지-않아도-oautility-start-수행시-에러가-발생하지-않습니다)
    - [BUG-46508  min, max 통계 정보 설정 시 테이블 메타 캐시의 컬럼 정보가 변경될 수 있습니다.](#bug-46508-min-max-%ED%86%B5%EA%B3%84-%EC%A0%95%EB%B3%B4-%EC%84%A4%EC%A0%95-%EC%8B%9C-%ED%85%8C%EC%9D%B4%EB%B8%94-%EB%A9%94%ED%83%80-%EC%BA%90%EC%8B%9C%EC%9D%98-%EC%BB%AC%EB%9F%BC-%EC%A0%95%EB%B3%B4%EA%B0%80-%EB%B3%80%EA%B2%BD%EB%90%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-46516  APRE PSM Array가 새로 생성된 사용자에서 동작하지 않습니다.](#bug-46516-apre-psm-array%EA%B0%80-%EC%83%88%EB%A1%9C-%EC%83%9D%EC%84%B1%EB%90%9C-%EC%82%AC%EC%9A%A9%EC%9E%90%EC%97%90%EC%84%9C-%EB%8F%99%EC%9E%91%ED%95%98%EC%A7%80-%EC%95%8A%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Altibase 7.1.0.1.6 Patch Notes
==============================

New Features
------------

### BUG-46406  merge 구문에 문법(syntax) 확장

- **module** : qp-dml-pvo
- **Category** : Other
- **재현 빈도** : Always
- **증상** : 아래의 [merge](<https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/SQL3.md#merge>) 문법을 허용하도록 수정되었습니다.
  1. merge 구문에 on 절 뒤에 괄호를 사용할수 있도록합니다. 
  2.  on 절 뒤에 괄호를 사용하는 경우, insert, update 에서 where  절 사용할 수 있도록 합니다.
  3. on절 뒤에 괄호를 사용하는 경우, delete 구문 사용할 수 있도록 합니다.
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

### BUG-46481  micro second sleep 을 지원하는 시스템 저장 프로시저 sleep2가 추가되었습니다.

- **module** : qx

- **Category** : Enhancement

- **재현 빈도** : Always

- **증상** : [dbms\_lock](<https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/StoredProcedure2.md#dbms_lock>) 패키지에 micro second sleep 을 지원하는 시스템 저장 프로시저 [sleep2](<https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/StoredProcedure2.md#sleep2>)가 추가되었습니다.

  구문)

  DBMS\_LOCK.SLEEP2(seconds IN INTEGER, microseconds IN INTEGER );

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

### BUG-46402  메모리 인덱스에 할당된 메모리는 mempool로 반환되지 않습니다.

-   **module** : sm-mem-index

-   **Category** : Efficiency

-   **재현 빈도** : Always

-   **증상** : 메모리 인덱스에 할당된 메모리는 영원히 free되지 않고
    재사용만 가능했습니다. 이부분을 실제 free가 이루어지도록 수정하였습니다.

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

### BUG-46436  모니터링 API의 ABISqlText에 time 항목을 추가해야 합니다.

-   **module** : mm-altibaseMonitor

-   **Category** : Functionality

-   **재현 빈도** : Always

- **증상** : altibaseMonitor의 ABISqlText에 아래 필드 추가.

  PARSE\_TIME                          파싱 소요 시간

  SOFT\_PREPARE\_TIME            Prepare 과정중 SQL Plan Cache에서 plan 탐색 시간

  LAST\_QUERY\_START\_TIME    가장 최근의 쿼리 시작 시간

  EXECUTE\_TIME                     실행 소요 시간

  FETCH\_TIME                         Fetch 소요 시간

  FETCH\_START\_TIME              현재 Fetch 시작 시간

  TOTAL\_TIME                         총 경과 시간

  VALIDATE\_TIME                     정당성 검사 소요 시간

  OPTIMIZE\_TIME                    최적화 소요 시간

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

### BUG-46480  JDBC insert 성능개선을 위한 내부 함수 리펙토링

-   **module** : mm-jdbc

-   **Category** : Efficiency

-   **재현 빈도** : Always

-   **증상** : JDBC insert 성능개선을 위하여 내부 함수 리펙토링 합니다.

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

### BUG-46485  iloader 성능개선을 위해 double 데이터의 바인딩 타입을 SQL\_C\_DOUBLE에서 SQL\_C\_CHAR로 수정해야 합니다

-   **module** : ux-iloader

-   **Category** : Efficiency

-   **재현 빈도** : Always

-   **증상** : iloade 내부적으로 double 타입을 처리할 때 파라미터 바인딩 타입을 변경함으로써 IN 성능을 개선 하였습니다.(사용자 인터페이스 변경 없음)

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

### BUG-46486  iloader 성능 개선을 위해, 버퍼로부터 데이터를 읽을 때 레코드 단위가 아니라 array 단위로 Lock을 획득하도록 수정해야 합니다

-   **module** : ux-iloader

-   **Category** : Efficiency

-   **재현 빈도** : Always

-   **증상** : IN 수행 시 작업 스레드들이 버퍼에서 데이터를 읽어갈 때 Lock 획득 단위를 변경함으로써 성능을 개선하였습니다.

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

### BUG-46085  캐싱된 플랜을 확인하는 과정에서 할당된 Query\_Prepare 메모리를 해제하지 않습니다.

-   **module** : qp-select-pvo

-   **Category** : Memory Error

-   **재현 빈도** : Always

-   **증상** : 캐싱된 플랜을 확인하는 과정에서 할당된 Query\_Prepare 메모리를 해제하지 않는 문제를 수정하였습니다.

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

### BUG-46389  APRE usage 에 silent 옵션이 누락되었습니다.

-   **module** : mm-apre

-   **Category** : Maintainability

-   **재현 빈도** : Always

-   **증상** : APRE -h 출력에 silent 옵션과 설명을 추가하였습니다.

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

### BUG-46390  IPCDA 세션 종료시 Client의 세션종료 여부를 확인하는 로직이 누락되어 있습니다.

-   **module** : mm

-   **Category** : Memory Error

-   **재현 빈도** : Frequence

-   **증상** : IPCDA 세션 종료시 Client 어플리케이션의 세션종료 여부를 확인하는 로직을 추가하였습니다.

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

### BUG-46483  HP jdbcAdapter 에서 LD\_LIBRARY\_PATH를 설정하지 않아도 oaUtility start 수행시 에러가 발생하지 않습니다.

-   **module** : rp-jdbcAdapter

-   **Category** : Maintainability

-   **재현 빈도** : Always

-   **증상** : HP 장비에서 LD\_LIBRARY\_PATH에 libjvm.so Path가 설정되어 있지 않으면 에러가 발생하도록 수정합니다.

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

### BUG-46508  min, max 통계 정보 설정 시 테이블 메타 캐시의 컬럼 정보가 변경될 수 있습니다.

-   **module** : qp-meta

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **증상** : min, max 통계 정보 설정 시 테이블 메타 캐시의 컬럼 정보가
    변경될 수 있습니다.

-   **재현 방법**

    -   **재현 절차**

            create table t1 ( c1 varchar(10) ) tablespace sys_tbs_disk_data;
            insert into t1 select level from dual connect by level <= 10000;
            exec set_column_stats('sys', 't1', 'c1', NULL, 9995, 0, 5, '1111111111', '9999999999');
            select /*+ no_merge(a) */ count(*) from (select * from t1) a;
            exec set_column_stats('sys', 't1', 'c1', NULL, 9995, 0, 5, '1', '9999');
            select /*+ no_merge(a) */ count(*) from (select * from t1) a;

    -   **수행 결과**

            iSQL> exec set_column_stats('sys', 't1', 'c1', NULL, 9995, 0, 5, '1', '9999');
            Execute success.
            iSQL> select /*+ no_merge(a) */ count(*) from (select * from t1) a;
            [ERR-91015 : Communication failure.]

    -   **예상 결과**

            iSQL> exec set_column_stats('sys', 't1', 'c1', NULL, 9995, 0, 5, '1', '9999');
            Execute success.
            iSQL> select /*+ no_merge(a) */ count(*) from (select * from t1) a;
            COUNT(*)             
            -----------------------
            10000                
            1 row selected.

-   **Workaround**

        iSQL> exec set_column_stats('sys', 't1', 'c1', NULL, 9995, 0, 5);
        Execute success.
        iSQL> select /*+ no_merge(a) */ count(*) from (select * from t1) a;
        COUNT(*)             
        -----------------------
        10000                
        1 row selected.

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-46516  APRE PSM Array가 새로 생성된 사용자에서 동작하지 않습니다.

-   **module** : mm-apre
-   **Category** : Functional Error
-   **재현 빈도** : Always
-   **증상** :  APRE 에서 PSM Arrary를 처리하는 로직에서 SYSTEM\_.DBA\_USERS\_  메타테이블을 조회하는데, 새로 생성된 사용자의 경우 권한 문제로 해당 테이블에 접근이 불가능합니다. 이를 SYSTEM\_.SYS\_USERS\_ 로  접근하도록 변경하여 수정하였습니다.
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
| 7.1.0.1.6        | 6.5.1                   | 8.6.1        | 7.1.6               | 7.4.3                        |

> Altibase 7.1 패치 버전별 히스토리는
> [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7_1_Version_Histories.md)
> 에서 확인할 수 있다.

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

### 프로퍼티

추가/삭제/변경된 프로퍼티 없음

### 성능 뷰

추가/삭제/변경된 성능뷰 없음
