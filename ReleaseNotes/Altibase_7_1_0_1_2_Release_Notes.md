<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Altibase 7.1.0.1.2 Release Note](#altibase-71012-release-note)
  - [시스템 요구사항](#%EC%8B%9C%EC%8A%A4%ED%85%9C-%EC%9A%94%EA%B5%AC%EC%82%AC%ED%95%AD)
    - [하드웨어 최저 사양](#%ED%95%98%EB%93%9C%EC%9B%A8%EC%96%B4-%EC%B5%9C%EC%A0%80-%EC%82%AC%EC%96%91)
    - [운영 체제 및 플랫폼](#%EC%9A%B4%EC%98%81-%EC%B2%B4%EC%A0%9C-%EB%B0%8F-%ED%94%8C%EB%9E%AB%ED%8F%BC)
  - [릴리스 정보](#%EB%A6%B4%EB%A6%AC%EC%8A%A4-%EC%A0%95%EB%B3%B4)
    - [2.1 새로운 기능](#21-%EC%83%88%EB%A1%9C%EC%9A%B4-%EA%B8%B0%EB%8A%A5)
      - [2.1.1 Altibase Sharding 2.0](#211-altibase-sharding-20)
      - [2.1.2 메타 다운그레이드](#212-%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9C)
      - [2.1.3 기능 개선](#213-%EA%B8%B0%EB%8A%A5-%EA%B0%9C%EC%84%A0)
        - [2.1.3.1 SQL 확장](#2131-sql-%ED%99%95%EC%9E%A5)
          - [파티션 변환(Partition Exchange) DDL 지원](#%ED%8C%8C%ED%8B%B0%EC%85%98-%EB%B3%80%ED%99%98partition-exchange-ddl-%EC%A7%80%EC%9B%90)
          - [테이블의 테이블스페이스 변경](#%ED%85%8C%EC%9D%B4%EB%B8%94%EC%9D%98-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%8A%A4%ED%8E%98%EC%9D%B4%EC%8A%A4-%EB%B3%80%EA%B2%BD)
          - [하이브리드 파티션드 테이블(Hybrid Partitioned Table) 지원](#%ED%95%98%EC%9D%B4%EB%B8%8C%EB%A6%AC%EB%93%9C-%ED%8C%8C%ED%8B%B0%EC%85%98%EB%93%9C-%ED%85%8C%EC%9D%B4%EB%B8%94hybrid-partitioned-table-%EC%A7%80%EC%9B%90)
          - [COMPACT, AGING 구문 확장](#compact-aging-%EA%B5%AC%EB%AC%B8-%ED%99%95%EC%9E%A5)
          - [NOWAIT, WAIT 지원](#nowait-wait-%EC%A7%80%EC%9B%90)
          - [큐 생성시 사용자 정의 칼럼 지원](#%ED%81%90-%EC%83%9D%EC%84%B1%EC%8B%9C-%EC%82%AC%EC%9A%A9%EC%9E%90-%EC%A0%95%EC%9D%98-%EC%B9%BC%EB%9F%BC-%EC%A7%80%EC%9B%90)
          - [Table Function 지원](#table-function-%EC%A7%80%EC%9B%90)
          - [집계 함수 및 윈도우 함수 추가](#%EC%A7%91%EA%B3%84-%ED%95%A8%EC%88%98-%EB%B0%8F-%EC%9C%88%EB%8F%84%EC%9A%B0-%ED%95%A8%EC%88%98-%EC%B6%94%EA%B0%80)
          - [사용자 잠금(user lock) 함수 추가](#%EC%82%AC%EC%9A%A9%EC%9E%90-%EC%9E%A0%EA%B8%88user-lock-%ED%95%A8%EC%88%98-%EC%B6%94%EA%B0%80)
          - [기타 함수 추가](#%EA%B8%B0%ED%83%80-%ED%95%A8%EC%88%98-%EC%B6%94%EA%B0%80)
          - [LOCK TABLE에 'UNTIL NEXT DDL' 구문 지원](#lock-table%EC%97%90-until-next-ddl-%EA%B5%AC%EB%AC%B8-%EC%A7%80%EC%9B%90)
          - [트리거 생성시 ENABLE, DISABLE 지원](#%ED%8A%B8%EB%A6%AC%EA%B1%B0-%EC%83%9D%EC%84%B1%EC%8B%9C-enable-disable-%EC%A7%80%EC%9B%90)
          - [집계 함수 FIRST, LAST 추가](#%EC%A7%91%EA%B3%84-%ED%95%A8%EC%88%98-first-last-%EC%B6%94%EA%B0%80)
          - [날짜형 데이터 형식 지원](#%EB%82%A0%EC%A7%9C%ED%98%95-%EB%8D%B0%EC%9D%B4%ED%84%B0-%ED%98%95%EC%8B%9D-%EC%A7%80%EC%9B%90)
          - [공간 함수 REVERSE , MAKEENVELOPE 추가](#%EA%B3%B5%EA%B0%84-%ED%95%A8%EC%88%98-reverse--makeenvelope-%EC%B6%94%EA%B0%80)
          - [숫자 함수(Numeric Function) 추가](#%EC%88%AB%EC%9E%90-%ED%95%A8%EC%88%98numeric-function-%EC%B6%94%EA%B0%80)
        - [2.1.3.2 이중화 기능개선](#2132-%EC%9D%B4%EC%A4%91%ED%99%94-%EA%B8%B0%EB%8A%A5%EA%B0%9C%EC%84%A0)
          - [이중화 제약 조건 완화](#%EC%9D%B4%EC%A4%91%ED%99%94-%EC%A0%9C%EC%95%BD-%EC%A1%B0%EA%B1%B4-%EC%99%84%ED%99%94)
          - [SQL 반영 모드 (SQL APPLY MODE)](#sql-%EB%B0%98%EC%98%81-%EB%AA%A8%EB%93%9C-sql-apply-mode)
          - [이중화 대상 테이블에 수행 가능한 DDL 추가](#%EC%9D%B4%EC%A4%91%ED%99%94-%EB%8C%80%EC%83%81-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90-%EC%88%98%ED%96%89-%EA%B0%80%EB%8A%A5%ED%95%9C-ddl-%EC%B6%94%EA%B0%80)
        - [2.1.3.3 DBLink Two-Phase Commit (2PC) Level 지원 및 기능개선](#2133-dblink-two-phase-commit-2pc-level-%EC%A7%80%EC%9B%90-%EB%B0%8F-%EA%B8%B0%EB%8A%A5%EA%B0%9C%EC%84%A0)
          - [Two-Phase Commit(2PC) Level 지원](#two-phase-commit2pc-level-%EC%A7%80%EC%9B%90)
          - [DBLink 에서 일괄처리(Batch) 지원 REMOTE 함수](#dblink-%EC%97%90%EC%84%9C-%EC%9D%BC%EA%B4%84%EC%B2%98%EB%A6%ACbatch-%EC%A7%80%EC%9B%90-remote-%ED%95%A8%EC%88%98)
        - [2.1.3.4 응용 프로그램 개발 인터페이스 확장 및 개선](#2134-%EC%9D%91%EC%9A%A9-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%A8-%EA%B0%9C%EB%B0%9C-%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4-%ED%99%95%EC%9E%A5-%EB%B0%8F-%EA%B0%9C%EC%84%A0)
          - [PDO 드라이버 지원](#pdo-%EB%93%9C%EB%9D%BC%EC%9D%B4%EB%B2%84-%EC%A7%80%EC%9B%90)
          - [내장 SQL에서 FOR절에서 FETCH 구문 지원](#%EB%82%B4%EC%9E%A5-sql%EC%97%90%EC%84%9C-for%EC%A0%88%EC%97%90%EC%84%9C-fetch-%EA%B5%AC%EB%AC%B8-%EC%A7%80%EC%9B%90)
        - [2.1.3.5 내장 패키지 및 함수](#2135-%EB%82%B4%EC%9E%A5-%ED%8C%A8%ED%82%A4%EC%A7%80-%EB%B0%8F-%ED%95%A8%EC%88%98)
          - [저장 프로시저에서 AUTHID 지원](#%EC%A0%80%EC%9E%A5-%ED%94%84%EB%A1%9C%EC%8B%9C%EC%A0%80%EC%97%90%EC%84%9C-authid-%EC%A7%80%EC%9B%90)
          - [STANDARD시스템 패키지 제공](#standard%EC%8B%9C%EC%8A%A4%ED%85%9C-%ED%8C%A8%ED%82%A4%EC%A7%80-%EC%A0%9C%EA%B3%B5)
          - [UTL_COPYSWAP 시스템 패키지 제공](#utl_copyswap-%EC%8B%9C%EC%8A%A4%ED%85%9C-%ED%8C%A8%ED%82%A4%EC%A7%80-%EC%A0%9C%EA%B3%B5)
          - [UTL_SMTP 패키지 지원](#utl_smtp-%ED%8C%A8%ED%82%A4%EC%A7%80-%EC%A7%80%EC%9B%90)
          - [기타 시스템 정의 저장 패키지 추가](#%EA%B8%B0%ED%83%80-%EC%8B%9C%EC%8A%A4%ED%85%9C-%EC%A0%95%EC%9D%98-%EC%A0%80%EC%9E%A5-%ED%8C%A8%ED%82%A4%EC%A7%80-%EC%B6%94%EA%B0%80)
          - [커서 사용시 정적 SQL 지원](#%EC%BB%A4%EC%84%9C-%EC%82%AC%EC%9A%A9%EC%8B%9C-%EC%A0%95%EC%A0%81-sql-%EC%A7%80%EC%9B%90)
          - [FETCH 커서 구문에서 BULK COLLECTION INTO 지원](#fetch-%EC%BB%A4%EC%84%9C-%EA%B5%AC%EB%AC%B8%EC%97%90%EC%84%9C-bulk-collection-into-%EC%A7%80%EC%9B%90)
          - [NOCOPY 옵션 지원](#nocopy-%EC%98%B5%EC%85%98-%EC%A7%80%EC%9B%90)
          - [패키지 서브프로그램 다중정의(overloading) 지원](#%ED%8C%A8%ED%82%A4%EC%A7%80-%EC%84%9C%EB%B8%8C%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%A8-%EB%8B%A4%EC%A4%91%EC%A0%95%EC%9D%98overloading-%EC%A7%80%EC%9B%90)
          - [PSM 문자형 데이터 크기 결정](#psm-%EB%AC%B8%EC%9E%90%ED%98%95-%EB%8D%B0%EC%9D%B4%ED%84%B0-%ED%81%AC%EA%B8%B0-%EA%B2%B0%EC%A0%95)
          - [PRAGMA AUTONOMOUS_TRANSACTION, PRAGMA EXCEPTION_INIT 구문 지원](#pragma-autonomous_transaction-pragma-exception_init-%EA%B5%AC%EB%AC%B8-%EC%A7%80%EC%9B%90)
        - [2.1.3.6 클라이언트 툴](#2136-%ED%81%B4%EB%9D%BC%EC%9D%B4%EC%96%B8%ED%8A%B8-%ED%88%B4)
          - [JDBC Adapter 지원](#jdbc-adapter-%EC%A7%80%EC%9B%90)
          - [SQuirreL SQL 클라이언트 연동](#squirrel-sql-%ED%81%B4%EB%9D%BC%EC%9D%B4%EC%96%B8%ED%8A%B8-%EC%97%B0%EB%8F%99)
          - [Shard Manager 지원](#shard-manager-%EC%A7%80%EC%9B%90)
          - [altimon.sh 개선](#altimonsh-%EA%B0%9C%EC%84%A0)
          - [iSQL 호스트 변수 선언에서 INPUT/OUTPUT 타입관련 동작 변경](#isql-%ED%98%B8%EC%8A%A4%ED%8A%B8-%EB%B3%80%EC%88%98-%EC%84%A0%EC%96%B8%EC%97%90%EC%84%9C-inputoutput-%ED%83%80%EC%9E%85%EA%B4%80%EB%A0%A8-%EB%8F%99%EC%9E%91-%EB%B3%80%EA%B2%BD)
          - [isql 명령어 추가](#isql-%EB%AA%85%EB%A0%B9%EC%96%B4-%EC%B6%94%EA%B0%80)
          - [iLoader의 -prefetch_rows 지원](#iloader%EC%9D%98--prefetch_rows-%EC%A7%80%EC%9B%90)
          - [파티션 정보 출력](#%ED%8C%8C%ED%8B%B0%EC%85%98-%EC%A0%95%EB%B3%B4-%EC%B6%9C%EB%A0%A5)
          - [dataCompJ 추가](#datacompj-%EC%B6%94%EA%B0%80)
          - [비동기 prefetch 속성 추가](#%EB%B9%84%EB%8F%99%EA%B8%B0-prefetch-%EC%86%8D%EC%84%B1-%EC%B6%94%EA%B0%80)
          - [aexport 프로퍼티 추가](#aexport-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0-%EC%B6%94%EA%B0%80)
      - [2.1.4 효율성](#214-%ED%9A%A8%EC%9C%A8%EC%84%B1)
        - [2.1.4.1 서버 성능 향상](#2141-%EC%84%9C%EB%B2%84-%EC%84%B1%EB%8A%A5-%ED%96%A5%EC%83%81)
          - [디스크 버퍼 매니저의 성능 개선](#%EB%94%94%EC%8A%A4%ED%81%AC-%EB%B2%84%ED%8D%BC-%EB%A7%A4%EB%8B%88%EC%A0%80%EC%9D%98-%EC%84%B1%EB%8A%A5-%EA%B0%9C%EC%84%A0)
          - [메모리 Fetch 성능 개선](#%EB%A9%94%EB%AA%A8%EB%A6%AC-fetch-%EC%84%B1%EB%8A%A5-%EA%B0%9C%EC%84%A0)
          - [Result Cache 지원](#result-cache-%EC%A7%80%EC%9B%90)
          - [자동 통계정보 수집](#%EC%9E%90%EB%8F%99-%ED%86%B5%EA%B3%84%EC%A0%95%EB%B3%B4-%EC%88%98%EC%A7%91)
          - [힌트 추가](#%ED%9E%8C%ED%8A%B8-%EC%B6%94%EA%B0%80)
          - [실행 계획의 지연 기능](#%EC%8B%A4%ED%96%89-%EA%B3%84%ED%9A%8D%EC%9D%98-%EC%A7%80%EC%97%B0-%EA%B8%B0%EB%8A%A5)
          - [IPCDA 프로토콜 지원](#ipcda-%ED%94%84%EB%A1%9C%ED%86%A0%EC%BD%9C-%EC%A7%80%EC%9B%90)
          - [ACCESS LIST 관리 확장](#access-list-%EA%B4%80%EB%A6%AC-%ED%99%95%EC%9E%A5)
        - [2.1.4.2 자원 효율성](#2142-%EC%9E%90%EC%9B%90-%ED%9A%A8%EC%9C%A8%EC%84%B1)
          - [Mempool 메모리 사용 개선](#mempool-%EB%A9%94%EB%AA%A8%EB%A6%AC-%EC%82%AC%EC%9A%A9-%EA%B0%9C%EC%84%A0)
          - [쓰레드 재사용](#%EC%93%B0%EB%A0%88%EB%93%9C-%EC%9E%AC%EC%82%AC%EC%9A%A9)
          - [Startup Index Rebuild 과정의 CPU 사용률 개선](#startup-index-rebuild-%EA%B3%BC%EC%A0%95%EC%9D%98-cpu-%EC%82%AC%EC%9A%A9%EB%A5%A0-%EA%B0%9C%EC%84%A0)
          - [메모리 인덱스 재구성(Reorganization) 지원](#%EB%A9%94%EB%AA%A8%EB%A6%AC-%EC%9D%B8%EB%8D%B1%EC%8A%A4-%EC%9E%AC%EA%B5%AC%EC%84%B1reorganization-%EC%A7%80%EC%9B%90)
      - [2.1.5 고가용성](#215-%EA%B3%A0%EA%B0%80%EC%9A%A9%EC%84%B1)
        - [Query Execution 안정성 개선](#query-execution-%EC%95%88%EC%A0%95%EC%84%B1-%EA%B0%9C%EC%84%A0)
      - [2.1.6 기타](#216-%EA%B8%B0%ED%83%80)
        - [2.1.6.1 그 외 변경사항](#2161-%EA%B7%B8-%EC%99%B8-%EB%B3%80%EA%B2%BD%EC%82%AC%ED%95%AD)
          - [동적 SQL의 메소드4추가](#%EB%8F%99%EC%A0%81-sql%EC%9D%98-%EB%A9%94%EC%86%8C%EB%93%9C4%EC%B6%94%EA%B0%80)
          - [Hibernate와 연동지원](#hibernate%EC%99%80-%EC%97%B0%EB%8F%99%EC%A7%80%EC%9B%90)
          - [로드밸런서(Load Balancer) 로깅(Logging) 기능 추가](#%EB%A1%9C%EB%93%9C%EB%B0%B8%EB%9F%B0%EC%84%9Cload-balancer-%EB%A1%9C%EA%B9%85logging-%EA%B8%B0%EB%8A%A5-%EC%B6%94%EA%B0%80)
          - [Autoextend 모드 ON에서 테이블스페이스의 자동확장 크기 변경을 지원](#autoextend-%EB%AA%A8%EB%93%9C-on%EC%97%90%EC%84%9C-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%8A%A4%ED%8E%98%EC%9D%B4%EC%8A%A4%EC%9D%98-%EC%9E%90%EB%8F%99%ED%99%95%EC%9E%A5-%ED%81%AC%EA%B8%B0-%EB%B3%80%EA%B2%BD%EC%9D%84-%EC%A7%80%EC%9B%90)
          - [JRE 1.5 지원](#jre-15-%EC%A7%80%EC%9B%90)
          - [윈도우 플랫폼 지원 중단](#%EC%9C%88%EB%8F%84%EC%9A%B0-%ED%94%8C%EB%9E%AB%ED%8F%BC-%EC%A7%80%EC%9B%90-%EC%A4%91%EB%8B%A8)
          - [DataPort 기능 제거](#dataport-%EA%B8%B0%EB%8A%A5-%EC%A0%9C%EA%B1%B0)
          - [재해 복구(Disaster Recovery) 기능 제거](#%EC%9E%AC%ED%95%B4-%EB%B3%B5%EA%B5%ACdisaster-recovery-%EA%B8%B0%EB%8A%A5-%EC%A0%9C%EA%B1%B0)
          - [공유 메모리 기능 미지원](#%EA%B3%B5%EC%9C%A0-%EB%A9%94%EB%AA%A8%EB%A6%AC-%EA%B8%B0%EB%8A%A5-%EB%AF%B8%EC%A7%80%EC%9B%90)
    - [2.2 변경 사항](#22-%EB%B3%80%EA%B2%BD-%EC%82%AC%ED%95%AD)
      - [데이터베이스 버전](#%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4-%EB%B2%84%EC%A0%84)
      - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
        - [데이터베이스 바이너리 버전](#%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4-%EB%B0%94%EC%9D%B4%EB%84%88%EB%A6%AC-%EB%B2%84%EC%A0%84)
        - [통신 프로토콜 버전](#%ED%86%B5%EC%8B%A0-%ED%94%84%EB%A1%9C%ED%86%A0%EC%BD%9C-%EB%B2%84%EC%A0%84)
        - [메타 버전](#%EB%A9%94%ED%83%80-%EB%B2%84%EC%A0%84)
        - [이중화 프로토콜 버전](#%EC%9D%B4%EC%A4%91%ED%99%94-%ED%94%84%EB%A1%9C%ED%86%A0%EC%BD%9C-%EB%B2%84%EC%A0%84)
        - [샤딩 버전](#%EC%83%A4%EB%94%A9-%EB%B2%84%EC%A0%84)
      - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
        - [새로운 프로퍼티](#%EC%83%88%EB%A1%9C%EC%9A%B4-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
        - [변경된 프로퍼티](#%EB%B3%80%EA%B2%BD%EB%90%9C-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
        - [삭제된 프로퍼티](#%EC%82%AD%EC%A0%9C%EB%90%9C-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
      - [메타 테이블](#%EB%A9%94%ED%83%80-%ED%85%8C%EC%9D%B4%EB%B8%94)
      - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)
        - [새로운 성능 뷰](#%EC%83%88%EB%A1%9C%EC%9A%B4-%EC%84%B1%EB%8A%A5-%EB%B7%B0)
        - [수정된 성능 뷰](#%EC%88%98%EC%A0%95%EB%90%9C-%EC%84%B1%EB%8A%A5-%EB%B7%B0)
    - [2.3 패키지](#23-%ED%8C%A8%ED%82%A4%EC%A7%80)
    - [2.4 다운로드](#24-%EB%8B%A4%EC%9A%B4%EB%A1%9C%EB%93%9C)
      - [Package](#package)
      - [Manual](#manual)
      - [설치](#%EC%84%A4%EC%B9%98)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

</br>

</br>

</br>

Altibase 7.1.0.1.2 Release Note
===============================

**(2018.02)**



시스템 요구사항
---------------

### 하드웨어 최저 사양

* 1GB RAM (권장: 2GB)
* 1 CPU (권장: 2 CPUs)
* 4GB 하드 디스크 여유 공간 (권장: 12GB)

### 운영 체제 및 플랫폼

Altibase 7.1.0.1.2는 아래 표에 나열된 운영체제와 플랫폼 상에서 운영 가능하다.

| OS    | CPU                                         | Version               | Bit (Server) | Bit (Client) |
| ----- | ------------------------------------------- | --------------------- | ------------ | ------------ |
| AIX   | PowerPC                                     | 6.1 tl03 and higher   | 64-bit       | 64-bit       |
| HP-UX | IA64                                        | 11.31 and higher      | 64-bit       | 64-bit       |
| LINUX | x86-64, PowerPC (GNU glibc 2.12 and higher) | redhat 6.0 and higher | 64-bit       | 64-bit       |
| LINUX | PowerPC8(LE) (GNU glibc 2.17)               | Redhat 7.2            | 64-bit       | 64-bit       |

> Java 버전: Altibase 7.1은 JDK 1.5 이상에서 호환된다.
>
> Altibase 7.1부터 윈도우용 서버 및 클라이언트를 지원하지 않는다.  또한 32bit 클라이언트는 더 이상 지원하지 않는다.
>
> Linux PowerPC8_LE ( little endian) 플랫폼이 추가되었다.</br>



릴리스 정보
-----------

### 2.1 새로운 기능

#### 	2.1.1 Altibase Sharding 2.0

Altibase 7.1부터 Altibase Sharding 기능을 제공한다. Altibase Sharding은
Altibase에 샤딩 기술을 도입하여, 저장 용량과 시간당 처리량을 향상시키고,
대용량의 데이터베이스를 분산처리 할 수 있게 한다. Altibase Sharding은 하이브리드
샤딩으로, 기존의 SQL을 분석하여 자동으로 클라이언트 측 샤딩이나 서버측 샤딩으로
수행할 것인지를 분석하여 경로를 최적화 한다. Altibase Sharding은 다양한
분산방식과 분산객체, 유틸리티를 지원하고 있으며, 다양한 업무에 적용할 수 있다.
기존의 SQL을 수정하지 않고, 샤드 전용 라이브러리만 교체하는 것으로 Altibase
Sharding을 쉽게 적용할 수 있다. 뿐만 아니라, 기존 응용프로그램을 전혀 수정하지
않은 상태에서도 서버 측 샤딩을 적용할 수 있다.

#### 2.1.2 메타 다운그레이드

기존에는 메타버전이 다른 경우에 패치를 롤백하려면, 롤백하려는 버전의 메타로
수동으로 재구성한 다음, 패치 롤백을 수행해야 했다. Altibase 7.1.0.1.2부터는
메타버전이 다른 경우에도 패치 롤백을 수행할 수 있도록 메타 다운그레이드 명령어를
제공한다.

```
% server downgrade
```

#### 2.1.3 기능 개선

##### 2.1.3.1 SQL 확장

###### 파티션 변환(Partition Exchange) DDL 지원

파티션드 테이블의 파티션 뿐만 아니라 일반 테이블(논파티션드 테이블)과 파티션드
테이블 간에도 파티션 교환이 가능하도록 파티션 결합(CONJOIN)과 파티션
해제(DISJOIN) 구문을 제공한다.

* **CONJOIN TABLE**: 이 구문은 논 파티션드 테이블을 테이블의 파티션으로 변환한다.
  리스트 파티션과 범위 파티션은 지원하며, 해시 파티션은 지원하지 않는다. 대상
  테이블의 데이터는 전부 생성된 파티션으로 이동한다.

* **DISJOIN TABLE**: 이 구문은 파티션드 테이블의 파티션을 논 파티션드 테이블로
  변환한다. 해시 파티션은 지원하지 않으며, 논 파티션드 테이블은 기존 파티션의
  속성을 그대로 갖는다.

###### 테이블의 테이블스페이스 변경

ALTER TABLE 구문을 이용하여, 테이블의 테이블스페이스를 다른 테이블스페이스로
변경하는 기능을 지원한다.

테이블의 테이블스페이스 저장 공간을 이동할 수 있으며, 이 때 인덱스와 LOB 칼럼도
함께 이동한다. 단 파티션드 테이블은 한 파티션의 레코드만 이동할 수 있기 때문에,
모든 파티션의 레코드를 이동하기 위해서는 DDL을 여러 번 수행해야 한다

###### 하이브리드 파티션드 테이블(Hybrid Partitioned Table) 지원

하이브리드 파티션드 테이블을 지원하여, 파티션드 테이블이 디스크
테이블스페이스에서 메모리/휘발성 테이블스페이스로, 메모리/휘발성
테이블스페이스에서 디스크 테이블스페이스로 데이터를 이동할 수 있다. 

> 제약사항:
>
>  글로벌 인덱스(Global Index)는 지원되지 않는다.

###### COMPACT, AGING 구문 확장

파티션드 테이블에 파티션 단위로 COMPACT 및 AGING구문을 수행할 수 있다.

###### NOWAIT, WAIT 지원

INSERT, FOR UPDATE, DEQUEUE 문에 NOWAIT, WAIT옵션을 지원한다.

###### 큐 생성시 사용자 정의 칼럼 지원

큐를 생성할 때 사용자가 칼럼을 정의할 수 있다.

###### Table Function 지원

TABLE FUNCTION은 사용자 정의 함수에서 반환하는 associative array 타입이나 record
타입의 값을 테이블 형태로 변환하여 출력한다.

###### 집계 함수 및 윈도우 함수 추가

집계 함수와 윈도우 함수에서 사용할 수 있는 백분율 순위, 비율 분석 함수, 그룹의
누적 분포도, 정렬 함수, 상관 계수, 표본 공분산, 모공 분산 등을 지원한다.

* PERCENT_RANK
* CUME_DIST
* RATIO_TO_REPORT
* NTILE
* CORR
* COVAR_SAMP
* COVAR_POP

###### 사용자 잠금(user lock) 함수 추가

사용자가 세션에서 사용자 잠금을 요청하거나 해제할 수 있는 함수가 지원된다.

* USER_LOCK_REQUEST  
* USER_LOCK_RELEASE

###### 기타 함수 추가

현재 세션에 접속한 환경 정보(context)를 반환하는 함수가 지원된다.

* SYS_CONTEXT

VARBYTE 타입의 문자열을 인코딩 또는 디코딩하여 반환하는 함수를 아래와 같이
지원한다.

* BASE64_DECODE  
* BASE64_ENCODE

Quoted printable형태로 변환된 VARBYTE 타입의 문자열을 디코딩 또는 인코딩하여
VARBAYTE 타입의 문자열로 반환하는 함수를 아래와 같이 지원한다.

*  QUOTE_PRINTABLE_DECODE  
* QUOTE_PRINTABLE_ENCODE

특정 스키마에 소속되지 않고 전체 데이터베이스 수준에서 관리되는 알티베이스
파이프(PIPE)방식의 함수를 추가하였다. 추가된 함수는 아래와 같다.

* MSG_CREATE_QUEUE  
* MSG_DROP_QUEUE  
* MSG_SND_QUEUE  
* MSG_RCV_QUEUE

###### LOCK TABLE에 'UNTIL NEXT DDL' 구문 지원

세션이 NON-AUTOCOMMIT 모드일 때 테이블에 DDL(데이터 정의어)을 수행하면, DDL이
실행되기 직전에 자동으로 커밋을 수행한다. 그러나 lock_mode에서 EXCLUSIVE 모드를
지정하면, DDL을 수행하기 직전에 자동으로 커밋을 수행하지 않는다.

###### 트리거 생성시 ENABLE, DISABLE 지원

트리거 생성할 때 활성화(enable) 상태와 비활성화(disable) 상태를 설정할 수 있다. 이후 ALTER TRIGGER 구문으로 ENABLE/DISABLE 상태를 변경할 수 있다.

###### 집계 함수 FIRST, LAST 추가

Order by에 의해 정렬된 데이터에 대해, 첫 번째(FIRST) 또는 마지막 부분(LAST)을
집계하는 함수가 추가되었다. 함께 사용할 수 있는 함수는 MIN, MAX, SUM, AVG,
COUNT, VARIANCE, STDDEV 이다.

* KEEP (DENSE_RANK FIRST ORDER BY )

* KEEP (DENSE_RANK LAST ORDER BY)

###### 날짜형 데이터 형식 지원

ROUND(date), TRUNC(date) 등의 날짜 함수에서 아래의 날짜형 데이터 타입을
지원한다. 

* SCC, CC, SYYYY, YYYY, YYY, YY, Y, Q, MON, MM, RM, WW, DDD, DD, J, HH, HH12,
  HH24, MI

###### 공간 함수 REVERSE , MAKEENVELOPE 추가

* REVERSE(GEOMETRY): 입력한 공간 객체의 포인트를 역순으로 변경한다.
* MAKEENVELOPE(X1, Y1, X2, Y2) : 입력한 Double 형 변수 4개에 해당하는 LINESTRING(
  X1 Y1, X2 Y2 )를 ENVELOPE 수행한 결과인 POLYGON( X1 Y1, X2 Y1, X2 Y2, X1 Y2, X1
  Y1 )로 반환한다.

###### 숫자 함수(Numeric Function) 추가

* NUMAND
* NUMOR
* NUMSHIFT
* NUMXOR

##### 2.1.3.2 이중화 기능개선

###### 이중화 제약 조건 완화

양쪽 서버의 복제할 테이블의 컬럼타입, 프라이머리키, NOT NULL 제약이 동일하지
않아도 이중화가 지원된다.

###### SQL 반영 모드 (SQL APPLY MODE)

지역서버와 원격서버의 테이블스키마 정보가 다를 경우, 원격 서버에 XLog를 SQL로
변환하여 반영할 수 있는 기능을 제공한다.

REPLICATION_SQL_APPLY_ENABLE 가 추가되었으며, REPLICATION_SQL_APPLY_ENABLE 프로퍼티 값을 1로 설정하여 사용할 수 있다.

> 제약사항 :
>
> LAZY 모드에서만 SQL 반영모드로 동작한다. 테이블에 보안칼럼이 존재하면 SQL 반영모드로 동작하지 않는다.

###### 이중화 대상 테이블에 수행 가능한 DDL 추가

REPLICATION_DDL_ENABLE_LEVEL 프로퍼티를 추가하여, DDL 구문 수행을REPLICATION_DDL_ENABLE_LEVEL에 따라 허용하도록 하였다.

>  제약사항 : 
>
>  이중화 복구 옵션이 지정된 테이블에는 DDL 문을 실행할 수 없다. 
>
>  또한, 이중화가 EAGER모드로 실행 중일 때도 DDL문을 실행할 수 없다.

##### 2.1.3.3 DBLink Two-Phase Commit (2PC) Level 지원 및 기능개선

###### Two-Phase Commit(2PC) Level 지원

알티베이스와 이기종 데이터베이스 시스템 간에 수행하는 글로벌 트랜잭션의 정합성을
보장하기 위해 DB Link는 2PC 프로토콜을 제공한다.

DBLINK_GLOBAL_TRANSACTION_LEVEL프로퍼티를 Two-Phase Commit Level로 설정한 다음에 커밋을 수행하면 알티베이스와 원격 데이터베이스 시스템들이 2PC 프로토콜을 이용하여 메시지를 서로 주고 받으며 수행한다.

분산 트랜잭션의 정합성 보장과 관련하여 추가 및 수정된 프로퍼티는 아래와 같다.

- DBLINK_RECOVERY_MAX_LOGFILE
- DBLINK_GLOBAL_TRANSACTION_LEVEL

분산 트랜잭션의 정합성 보장과 관련하여 추가 및 수정된 성능 뷰는 아래와 같다.

- V$DBLINK_NOTIFIER_TRANSACTION_INFO
- V$DBLINK_LINKER_DATA_SESSION_INFO
- V$DBLINK_GLOBAL_TRANSACTION_INFO
- V$DBLINK_REMOTE_STATEMENT_INFO
- V$DBLINK_REMOTE_TRANSACTION_INFO
- V$SESSION

###### DBLink 에서 일괄처리(Batch) 지원 REMOTE 함수

알티베이스 DB Link가 일괄처리(Batch)할 수 있는 Remote함수와 관련 함수를 추가하였다. 추가된 함수는 저장 프로시저 내에서만 사용할 수 있다.

- IS_ARRAY_BOUND
- IS_FIRST_ARRAY_BOUND
- IS_LAST_ARRAY_BOUND
- REMOTE_ADD_BATCH
- REMOTE_ALLOC_STATEMENT_BATCH
- REMOTE_BIND_VARIABLE_BATCH
- REMOTE_EXECUTE_BATCH
- REMOTE_FREE_STATEMENT_BATCH
- REMOTE_GET_RESULT_COUNT_BATCH
- REMOTE_GET_RESULT_BATCH

##### 2.1.3.4 응용 프로그램 개발 인터페이스 확장 및 개선

###### PDO 드라이버 지원

PHP 응용프로그램에서 Altibase와 연동을 위하여 Altibase PDO 드라이버가 추가되었다.

###### 내장 SQL에서 FOR절에서 FETCH 구문 지원

내장 SQL 문에서 호스트배열을 사용할 때 FOR절에서 FETCH 구문을 사용할 수 있다.

##### 2.1.3.5 내장 패키지 및 함수

###### 저장 프로시저에서 AUTHID 지원

저장 프로시저 내의 프로시저, 함수, 패키지를 실행하는 권한을 명시할 수 있다. CREATE PROCEDURE, CREATE FUNCTION, CREATE PACKAGE 구문에서 다음의 절을 추가하여 명시할 수 있다.

* AUTHID CURRENT_USER : 사용자 권한으로 실행하도록 명시

* AUTHID DEFINER : 생성자의 권한으로 실행할 것을 명시

###### STANDARD시스템 패키지 제공

SYS_REFCURSOR 타입을 지원하기 위해 STANDARD 패키지가 추가되었다.

###### UTL_COPYSWAP 시스템 패키지 제공

UTL_COPYSWAP 패키지는 테이블 스키마 복사, 데이터 복제, 테이블 교환 등의
인터페이스를 제공한다. UTL_COPYSWAP 패키지를 구성하는 프로시저와 함수는 아래
표를 참고한다.

| 프로시저 및 함수패키지 | 설명                                                         |
| ---------------------- | ------------------------------------------------------------ |
| CHECK_PRECONDITION     | 권한, 세션 프로퍼티, 시스템 프로퍼티, 이중화 제약조건을 검사한다. |
| COPY_TABLE_SCHEMA      | 테이블 스키마를 복사한다. 이후에 복사한 테이블에 사용자가 원하는 DDL을 수행한다. |
| REPLICATE_TABLE        | 데이터를 복제한다.                                           |
| SWAP_TABLE             | 테이블을 교환한다.                                           |
| SWAP_TABLE_PARTITION   | 테이블 파티션을 교환한다. (7.1.0.1.3에 제공 예정)            |
| FINISH                 | COPY_TABLE_SCHEMA, REPLICATE_TABLE에서 생성한 것을 정리한다. |

###### UTL_SMTP 패키지 지원

EMAIL을 사용할 수 있도록 SMTP 프로토콜을 수행하는 UTL_SMTP 저장 패키지가
추가되었다. UTL_SMTP패키지를 구성하는 프로시저와 함수는 아래 표를 참고 한다.

| 프로시저 및 함수패키지 | 설명                                                                      |
|------------------------|---------------------------------------------------------------------------|
| OPEN_CONNECTION        | TCP 소켓을 생성하여, SMTP 서버에 접속한다.                                |
| HELO                   | SMTP 프로토콜의 초기화인 HELO domain 명령어를 전송한다.                   |
| MAIL                   | MTP 프로토콜의 송신자 설정인 MAIL FROM:\<reverse-path\>명령어를 전송한다. |
| RCPT                   | SMTP 프로토콜의 수신자 설정인 RCPT TO:\<forward-path\>명령어를 전송한다   |
| OPEN_DATA              | SMTP 프로토콜의 데이터 전송 시작인 DATA 명령어를 전송한다.                |
| WRITE_DATA             | SMTP 프로토콜으로 데이터를 전송한다.                                      |
| WRITE_RAW_DATA         | SMTP 프로토콜으로 RAW 데이터를 전송한다.                                  |
| CLOSE_DATA             | SMTP 프로토콜의 데이터 전송 종료인 \<CRLF\> . \<CRLF\>를 전송한다.        |
| QUIT                   | SMTP 프로토콜의 QUIT 명령어로 연결을 종료한다.                            |

###### 기타 시스템 정의 저장 패키지 추가

그 외에 Altibase에서 추가된 시스템 정의 저장 패키지는 아래와 같다.

- DBMS_ALERT: 데이터베이스에서 발생하는 이벤트를 다른 사용자에게 알리는
  기능으로 인터페이스로 제공한다.

- DBMS_APPLICATION_INFO  
  클라이언트의 애플리케이션 정보를 관리하기 위해 성능 뷰의 값을 설정한다.

- DBMS_CONCURRENT_EXEC  
  프로시저를 동시에 실행할 수 있다.

- DBMS_LOCK  
  사용자가 잠금(Lock)을 요청하거나 해제할 수 있는 인터페이스를 제공한다.

- DBMS_OUTPUT  
  버퍼에 저장된 문자열을 사용자가 클라이언트에게 출력한다.

- DBMS_RANDOM  
  임의의 숫자를 생성한다.

- DBMS_SQL  
  동적 SQL을 사용하는 프로시저와 함수를 제공한다.

- DBMS_STATS  
  다양한 데이터베이스 통계 정보를 사용할 수 있는 서브프로그램을 제공한다.

- DBMS_RECYCLEBIN  
  삭제(Drop)되어 휴지통에서 관리되고 있는 테이블을 시스템에서 완전히
  삭제(Purge)할 수 있다.

- DBMS_UTILITY  
  다양한 유틸리티의 서브프로그램을 제공한다.

- UTL_FILE  
  운영 체제에서 관리하는 텍스트 파일에 접근하여 읽기, 쓰기를 할 수 있다.

- UTL_RAW  

  RAW(VARBYTE) 타입의 데이터를 다른 데이터 타입으로 변환하거나 조작할 수 있다.

- UTL_TCP  

  저장 프로시저에서 TCP 접속을 제어한다.

###### 커서 사용시 정적 SQL 지원

OPEN FOR구문에서 동적 SQL뿐만 아니라 정적 SQL을 사용할 수 있다. 

> 정적SQL은 USING 절과 함께 사용할 수 없다.

###### FETCH 커서 구문에서 BULK COLLECTION INTO 지원

Fetch 구문에서 BULK COLLECT INTO기능을 지원한다. 또한 limit 기능을 지원하여, BULK COLLECT 절에서 반환되는 행의 개수를 조정할 수 있다.

###### NOCOPY 옵션 지원

저장 프로시저와 저장 함수에서 사용되는 매개 변수 및 지역 변수에 NOCOPY옵션을 지원한다. 이 옵션은 참조(reference)값을 활용하여 인자를 할당하는 방식이다. 

> NOCOPY옵션은 ASSOCIATIVE ARRAY타입만 지원한다.

###### 패키지 서브프로그램 다중정의(overloading) 지원

저장패키지에서 서브프로그램을 다중정의(overloading)할 수 있다. 즉, 서브프로그램의 이름은 같지만 인자이름 및 데이터 타입 등을 다르게 정의할 수 있다.

###### PSM 문자형 데이터 크기 결정

저장 프로시저와 저장 함수에서 사용하는 문자형 데이터 타입의 크기를 결정하는 프로퍼티가 추가되었다.  

* PSM_CHAR_DEFAULT_PRECISION  
* PSM_NCHAR_UTF8_DEFAULT_PRECISION  
* PSM_NCHAR_UTF16_DEFAULT_PRECISION  
* PSM_NVARCHAR_UTF8_DEFAULT_PRECISION  
* PSM_NVARCHAR_UTF16_DEFAULT_PRECISION
* PSM_PARAM_AND_RETURN_WITHOUT_PRECISION_ENABLE  
* PSM_VARCHAR_DEFAULT_PRECISION  

문자형 데이터 타입의 기본 크기를 설정하는 아래의 프로퍼티는 제거되었다.  

* CHAR_DEFAULT_PRECISION  
* NCHAR_DEFAULT_PRECISION  
* NVARCHAR_DEFAULT_PRECISION  
* VARCHAR_DEFAULT_PRECISION

###### PRAGMA AUTONOMOUS_TRANSACTION, PRAGMA EXCEPTION_INIT 구문 지원

저장 프로시저, 함수 및 저장 패키지 생성 구문에서 프라그마(Pragma) 구문을 지원한다. 

* PRAGMA AUTONOMOUS_TRANSACTION : 자율 트랜잭션 프라그마. PSM 객체가 트랜잭션 내에서 동작하는 방식을 변경할 수 있다.
* PRAGMA EXCEPTION_INIT : 예외 초기화 프라그마. 사용자가 예외 변수를 Altibase의 에러코드로 초기화 할 수 있는 기능이다.

##### 2.1.3.6 클라이언트 툴

###### JDBC Adapter 지원

JDBC Adapter는 알티베이스 데이터베이스에서 변경된 데이터를 JDBC를 지원하는
다른(타사의) 데이터베이스에 적용하는 유틸리티 이다. 이는 알티베이스에서 제공하는
ALA(Altibase Log Analysis API) 와 JDBC(Java DataBase Connectivity) 를 이용하여
변경된 데이터를 타겟 데이터베이스에 복제하는 구조이다.

> 현재는 Linux 운영체제에서만 사용할 수 있으며, JRE 7 이상에서 동작한다.

###### SQuirreL SQL 클라이언트 연동

DB 객체 브라우징과 SQL 수행을 위한 오픈소스 제품인 SQuirreL SQL 클라이언트를
Altibase와 연동하여 사용할 수 있다. 

###### Shard Manager 지원

Shard Manager는 Altibase Sharding의 데이터 노드와 샤드 객체에 대한 구성 및
관리를 돕는 도구이다. Altibase Sharding은 다수의 데이터베이스로 구성되기 때문에,
각 데이터베이스와 객체를 관리하는 데에 많은 비용이 들 수 있다. 이런 환경에서,
사용자는 Shard Manager를 사용하여 업무 효율성을 향상시킬 수 있다

###### altimon.sh 개선

Altibase 서버와 altiMon이 설치된 호스트 장비를 모니터링 하기 위해 altimon.sh를
개선하였다. altiMon은 주로 OS 정보와 DB정보를 모니터링 하며, OS 정보를 수집하기
위해서는 PICL 라이브러리를 사용할 수 있는 운영체제에서 가능하다.

###### iSQL 호스트 변수 선언에서 INPUT/OUTPUT 타입관련 동작 변경 

프로시저나 함수 실행에 사용하기 위한 호스트 변수를 선언할 때,  INPUT/OUTPUT을 명시하지 않으면 기본값은 클라이언트에서 전달받은 타입으로 설정된다.

> Altibase 6.5.1.4.1 이하에서는 INPUT/OUTPUT을 명시하지 않으면 기본값은 INPUT이다.

###### isql 명령어 추가

iSQL에서 SELECT 결과의 칼럼에 대한 표시 형식을 설정할 수 있는 명령어가 추가되었다.  

* SET NUMF[ORMAT] : 숫자 데이터 타입의 표시 형식 설정  
* COLUMN : 문자형 또는 숫자형 타입의 칼럼 표시 형식 설정  
* CL[EAR] COL[UMNS] : COLUMN명령어로 설정된 모든 칼럼의 설정을 해제

###### iLoader의 -prefetch_rows 지원

iLoader의 out모드에서 사용할 수 있는 -prefetch_rows옵션을 지원한다. select쿼리
수행 시에 데이터 베이스에서 한번에 가져오는 레코드 개수를 지정할 수 있다.

###### 파티션 정보 출력

DESC 명령어를 사용하여 테이블 구조를 볼 때 파티션에 대한 정보도 함께 보여준다.

###### dataCompJ 추가

Altibase 데이터베이스에서 이기종 데이터베이스로 데이터를 복제할 때, 데이터
정합성 확인과 데이터 불일치를 해소하기 위한 도구로써 dataCompJ가 추가되었다.

###### 비동기 prefetch 속성 추가

비동기 prefetch 관련 기능을 iLoader의 성능 옵션과 aexport 프로퍼티에 추가하였다.

-   ASYNC_PREPETCH = OFF\| ON\| AUTO (기본값: OFF) : OUT 명령어와 함께 사용

-   ILOADER_ASYNC_PREFETCH = ON\| OFF\| AUTO (기본값: ON)

###### aexport 프로퍼티 추가

aexport 유틸리티의 프로퍼티들이 아래와 같이 추가되었다.

* ILOADER_ARRAY  
* ILOADER_COMMIT  
* ILOADER_ERRORS  
* ILOADER_PARALLEL

#### 2.1.4 효율성

##### 2.1.4.1 서버 성능 향상

###### 디스크 버퍼 매니저의 성능 개선

자주 사용되는 페이지에 대해서 버퍼 풀에서 Victim으로 선정되지 않도록, 최근에
사용된 페이지에 대한 Flush 순서를 변경하여 디스크 버퍼 매니저의 속도를
향상시킨다.

-   DELAYED_FLUSH_LIST_PCT: Delayed flush list 의 최대 비율을 명시한다.(%)

-   DELAYED_FLUSH_PROTECTION_TIME_MSEC: 최근에 사용된 Page로 판단하기 위한 기준
    시간이다. 마지막으로 사용된 시간이 설정 값 이하라면 최근에 사용된 Page로
    판단한다. (Millisecond)

###### 메모리 Fetch 성능 개선

메모리 full scan 및 index scan 성능이 개선되었다.

###### Result Cache 지원

Result Cache를 사용하여 처음 실행한 쿼리의 중간 결과나 최종 결과를 서버에 저장하여, 같은 쿼리가 다시 실행되면 결과를 재사용할 수 있다.

###### 자동 통계정보 수집

옵티마이저가 사용할 수 있는 통계정보를 자동으로 수집할 수 있다.

###### 힌트 추가

정규화 형태, 조인방법, 조인순서, 테이블 접근방법, 병렬 질의 처리에 대한 힌트가
추가되었다.  

* INDEX_ASC  
* INDEX_DESC  
* LEADING  
* NO_EXPAND
* NO_INDEX 
* NO_PARALLEL 
* NO_USE_HASH  
* NO_USE_MERGE  
* NO_USE_NL  
* NO_USE_SORT  
* USE_CONCAT

###### 실행 계획의 지연 기능

실행 계획의 그래프를 기준으로 sorting, windowing, grouping, set, distinction의 계층적 실행(hierarchy execute)이 Fetch에서 수행되는 것을 지연시키는 기능을 제공한다. 사용자는 실행 계획에서 상위 PROJECTION 아래에 DELAY 플랜이 추가된 것을 확인할 수 있다.

###### IPCDA 프로토콜 지원

IPCDA(Inter Process Communication Direct Attach)는 Altibase에서 제공하는 프로토콜로써, IPC와 마찬가지로 공유 메모리를 이용하여 클라이언트와 데이터베이스 서버간에 데이터를 교환한다. IPCDA는 IPC보다 데이터 읽기, 쓰기를 단순화하고 클라이언트, 서버 사이의 유휴 시간을 줄여 성능이 향상되었다.

>  제약사항:
>
> IPC와 마찬가지로 CLI, ODBC는 지원하지만, JDBC는 지원하지 않는다. 또한 IPCDA를
> 사용할 때는 LOB 데이터를 사용할 수 없다. 현재는 Linux 운영체제에서만 사용할 수 있다.

###### ACCESS LIST 관리 확장

외부 파일에 기술된 IP 패킷의 접근 및 차단을 허용할 수 있도록 ACCESS_LIST_FILE
프로퍼티를 추가하였다

##### 2.1.4.2 자원 효율성

###### Mempool 메모리 사용 개선

인덱스 메모리 할당 시 필요한 양만 할당하여 메모리 낭비 및 단편화를 감소하였다.

###### 쓰레드 재사용

알티베이스 리소스 제약을 위해 사용하던 MAX_THREAD_COUNT 프로퍼티가 제거되고,
쓰레드 재사용 설정을 위한 THREAD_REUSE_ENABLE 프로퍼티가 추가되었다.

* THREAD_REUSE_ENABLE = 1

  쓰레드 종료시 바로 반납되지 않고 idle로 유지 후 재 사용된다. 재사용 하는 경우 쓰레드를 생성하는 system call 함수의 호출을 줄일 수 있어, 재사용 하지 않는 경우 보다 좋은 성능을 기대할 수 있다.

* THREAD_REUSE_ENABLE = 0

  쓰레드를 재사용하지 않으므로 쓰레드 종료시 바로 반납된다. (system call 함수를 사용한다는 의미)

###### Startup Index Rebuild 과정의 CPU 사용률 개선

Job Thread, Queue 의 내부 알고리즘 개선으로 인덱스 재빌드시 CPU 사용율을 개선하였다. 

또한, 인덱스 빌드에 사용하는 쓰레드 개수의 기본값이 변경되었다. 

* INDEX_BUILD_THREAD_COUNT

###### 메모리 인덱스 재구성(Reorganization) 지원

메모리 인덱스의 리프 노드를 통합하여 인덱스 공간을 재구성한다. 데이터에 비해 인덱스의 범위가 클 때, 특정 인덱스에 단편화 현상이 있을 경우에 사용하면 공간 효율성이 향상된다. 

* ALTER INDEX ... REORGANIZATION 구문 지원

> 메모리 B-tree인덱스만 사용할 수 있다.

#### 2.1.5 고가용성

##### Query Execution 안정성 개선

Query Execution 단계에서의 안정성이 개선되었다.

#### 2.1.6 기타

##### 2.1.6.1 그 외 변경사항

###### 동적 SQL의 메소드4추가

동적SQL에 메소드4를 추가한다. 이 메소드는 프로그램 실행 중에 사용자가 파라미터 마커의 값을 입력할 수 있다. BIND VARIABLES, SELECT LIST, ARRAY SIZE SET함수가 추가되었고 OPEN, FETCH, EXECUTE함수가 개선되었다.

###### Hibernate와 연동지원

Altibase가 비표준SQL을 제공할 수 있도록 Hibernate의 dialect클래스를 지원한다.

> Hibernate 공식 라이브러리는 AltibaseDialect.class을 포함하지 않기 때문에, AltibaseDialect.java파일을 컴파일하고 포팅해야 사용할 수 있다.

###### 로드밸런서(Load Balancer) 로깅(Logging) 기능 추가

로드밴런서의 주요동작에 대해서 로그를 기록하는 기능이 추가되었다. LB_MSGLOG_FLAG 프로퍼티를 통해 로그의 레벨을 설정하고, \$ALTIBASE_HOME/trc/altibase_lb.log 에 관련 메시지가 기록된다. 

또한, V\$tracelog에서 module_name에 "LB"가 추가되어 조회가 가능하다.

Service Thread 의 메시지로그관련하여 아래의 프로퍼티가 추가되었다.

* LB_MSGLOG_FLAG

* LB_MSGLOG_COUNT

* LB_MSGLOG_FILE

* LB_MSGLOG_SIZE

###### Autoextend 모드 ON에서 테이블스페이스의 자동확장 크기 변경을 지원

Autoextend 모드가 ON일 때 테이블스페이스의 자동확장 크기(extend size)를 변경하기
위해서 기존에는 autoextend off를 수행한 다음 변경해야 했으나, autoextend on 모드에서도 변경할 수 있다.

###### JRE 1.5 지원

JDK, JRE1.5 이상을 지원하며, JDK1.4, JRE 1.4를 더 이상 지원하지 않는다.

###### 윈도우 플랫폼 지원 중단

Altibase 7.1부터 윈도우용 서버 및 클라이언트를 지원하지 않는다.

###### DataPort 기능 제거

데이터를 이전할 수 있던 DataPort 기능 및 유틸리티(convdp)를 지원하지 않는다.

###### 재해 복구(Disaster Recovery) 기능 제거

###### 공유 메모리 기능 미지원

공유 메모리(Shared Memory) 모드를 7.1부터 지원하지 않는다. 공유 메모리를
지원하는 관리 도구 'shmutil' 및 프로퍼티를 삭제한다

### 2.2 변경 사항

DBA와 개발자가 알아야 할 추가, 변경, 및 제거된 기능을 아래에서 설명한다.

**Altibase 7.1 릴리즈 최종버전은 7.1.0.1.2 이며, 7.1.0.1.2 이후 버전부터 유지보수**
**한다.**

#### 데이터베이스 버전

데이터베이스 구성 요소 별 버전

| Altibase 버전 | 데이터베이스 바이너리 버전 | 통신 프로토콜 버전 | 메타 버전 | 이중화 프로토콜 버전 | 샤딩 버전 |
| ------------- | -------------------------- | ------------------ | --------- | -------------------- | --------- |
| 6.5.1         | 6.3.1                      | 7.1.3              | 8.1.1     | 7.4.2                | \-        |
| 7.1.0.1.2     | 6.5.1                      | 7.1.6              | 8.5.1     | 7.4.2                | 2.0.0     |

#### 호환성

##### 데이터베이스 바이너리 버전

데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그 파일의 호환성을 나타낸다. 데이터베이스 이미지 및 로그 파일의 형식이 변경되었으므로, 데이터베이스 업그레이드 시 기존 데이터베이스는 마이그레이션 되어야 한다.

| Altibase 버전 | 데이터베이스 바이너리 버전 |
| ------------- | -------------------------- |
| 6.5.1         | 6.3.1                      |
| 7.1.0.1.2     | 6.5.1                      |

##### 통신 프로토콜 버전

통신 프로토콜 버전이 변경되었다. Patch 버전(세번째 자리 버전)이 변경되어, Altibase 6.5.1에서 동작하도록 빌드된 클라이언트 응용 프로그램은 Altibase 7.1.0.1.2와 호환이 된다. 즉, 다시 빌드하지 않아도 된다.

| Altibase 버전 | 통신 프로토콜 버전 |
|---------------|--------------------|
| 6.5.1         | 7.1.3              |
| 7.1.0.1.2     | 7.1.6              |

##### 메타 버전

메타 버전이 변경되었다. Altibase 6.5.1 이하 버전에서 Altibase 7.1.0.1.2로 업그레이드 시, 자동으로 메타 업그레이드가 수행된다. 하지만, 업그레이드를 롤백하려는 경우에는 메타를 재구성해야 한다.

| Altibase 버전 | 메타 버전 |
|---------------|-----------|
| 6.5.1         | 8.1.1     |
| 7.1.0.1.2     | 8.5.1     |

##### 이중화 프로토콜 버전

이중화 프로토콜 버전이 변경되지 않았다. 따라서 Altibase 6.5.1 과 7.1.0.1.2 간의 이중화가 가능하다.

| Altibase 버전 | 이중화 프로토콜 버전 |
|---------------|----------------------|
| 6.5.1         | 7.4.2                |
| 7.1.0.1.2     | 7.4.2                |

##### 샤딩 버전

Altibase 7.1부터 샤딩 기능을 제공한다. 

> 주의사항: 
>
> 알티베이스 샤딩 프로토콜 및 메타는 상위, 하위 호환성을 보장하지 않는다. 즉, 샤딩 버전이 다른 경우 재구성해야 한다.

| Altibase 버전 | 샤딩 버전 |
|---------------|-----------|
| 7.1.0.1.2     | 2.0.0     |

#### 프로퍼티

Altibase 7.1.0.1.2 에서는 아래의 프로퍼티들이 추가, 변경, 삭제되었다.  
각 프로퍼티에 대한 자세한 내용은 [*General Reference*](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_2.md) 를 참고하기 바란다.

##### 새로운 프로퍼티

-   ACCESS_LIST_FILE
-   DBLINK_RECOVERY_MAX_LOGFILE
-   DELAYED_FLUSH_LIST_PCT
-   DELAYED_FLUSH_PROTECTION_TIME_MSEC
-   ILOADER_ARRAY
-   ILOADER_COMMIT
-   ILOADER_ERRORS
-   ILOADER_PARALLEL
-   IPCDA_CHANNEL_COUNT
-   IPCDA_DATABLOCK_SIZE
-   IPCDA_FILEPATH
-   LB_MSGLOG_FLAG
-   LB_MSGLOG_COUNT
-   LB_MSGLOG_FILE
-   LB_MSGLOG_SIZE
-   LOCK_MGR_CACHE_NODE
-   LOCK_MGR_DETECTDEADLOCK_INTERVAL
-   LOCK_MGR_MAX_SLEEP
-   LOCK_MGR_MIN_SLEEP
-   LOCK_MGR_SPIN_COUNT
-   LOCK_MGR_TYPE
-   LOCK_NODE_CACHE_COUNT
-   LOG_CREATE_METHOD
-   MEM_INDEX_KEY_REDISTRIBUTION
-   MEM_INDEX_KEY_REDISTRIBUTION_STANDARD_RATE
-   MSG_QUEUE_PERMISSION
-   OPTIMIZER_AUTO_STATS
-   OPTIMIZER_DELAYED_EXECUTION
-   OPTIMIZER_PERFORMANCE_VIEW
-   PSM_CURSOR_OPEN_LIMIT
-   PSM_CHAR_DEFAULT_PRECISION
-   PSM_NCHAR_UTF8_DEFAULT_PRECISION
-   PSM_NCHAR_UTF16_DEFAULT_PRECISION
-   PSM_NVARCHAR_UTF8_DEFAULT_PRECISION
-   PSM_NVARCHAR_UTF16_DEFAULT_PRECISION
-   PSM_PARAM_AND_RETURN_WITHOUT_PRECISION_ENABLE
-   PSM_VARCHAR_DEFAULT_PRECISION
-   REPLICATION_DDL_ENABLE_LEVEL
-   REPLICATION_SQL_APPLY_ENABLE
-   REPLICATION_IB_PORT_NO
-   RESULT_CACHE_ENABLE
-   RESULT_CACHE_MEMORY_MAXIMUM
-   TOP_RESULT_CACHE_MODE
-   TABLE_LOCK_MODE
-   THREAD_REUSE_ENABLE
-   USER_LOCK_POOL_INIT_SIZE
-   USER_LOCK_REQUEST_CHECK_INTERVAL
-   USER_LOCK_REQUEST_LIMIT
-   USER_LOCK_REQUEST_TIMEOUT

##### 변경된 프로퍼티

- CM_DISPATCHER_SOCKET_POLL_TYPE

  Altibase 서버의 Dispatcher에서 소켓감지를 위한 시스템콜을 선택하는
  프로퍼티로 EPOLL타입(3)이 추가되었다.

  >  EPOLL은 linux만 지원하여, Linux의 경우 기본값이 기존 1(SELECT)에서 3(EPOLL)로 변경되었다.

- DEFAULT_THREAD_STACK_SIZE

  기본값 및 최소값, 최대값이 변경되었다.

  기본값이 3145728 (Byte) 에서10485760 로 변경되었다.

  최소값은 65536(Byte) 에서 1048576으로 최대값은 10485760 에서 134217728 로 변경되었다.

- DBLINK_GLOBAL_TRANSACTION_LEVEL

  MAX값이 기본1에서 2로 변경되었다. 기존에는 0,1 만 지원했는데, 2가 추가되었다.

  * 2:Two-Phase Commit (2PC) Level.

- EXECUTOR_FAST_SIMPLE_QUERY

  기본값이 0에서 1로 변경되었다.

- INDEX_BUILD_THREAD_COUNT

  인덱스 빌드에 사용하는 쓰레드 개수의 기본값이 변경되었다. 기존에는 시스템의 CPU개수(논리 core 개수)였는데, 물리 core 개수로 변경되었다.

- NORMALFORM_MAXIMUM

  기본값이 128에서 2048(개)로 변경되었다.

- OPTIMIZER_AUTO_STATS

  기본값이 2에서 0(통계정보 수집안함)으로 변경되었다.

- REPLICATION_SYNC_TUPLE_COUNT

  이중화 Sync시 처리건수를 기존 5만건에서 50만건으로 변경되었다.

- REPLICATION_LOG_BUFFER_SIZE

  기본값이 30에서 0으로 변경되었다.

- REPLICATION_PREFETCH_LOGFILE_COUNT

  기본값이 0에서 3으로 변경되었다.

- REPLICATION_ACK_XLOG_COUNT

  읽기 전용에서 변경가능(writable) 속성으로 변경되었다.

- REPLICATION_TRANSACTION_POOL_SIZE

  기본값이 1에서 2로 변경되었다

- XA_INDOUBT_TX_TIMEOUT

  기본값이 20에서 60으로 변경되었다.

##### 삭제된 프로퍼티

-   CHAR_DEFAULT_PRECISION
-   NCHAR_DEFAULT_PRECISION
-   VARCHAR_DEFAULT_PRECISION
-   NVARCHAR_DEFAULT_PRECISION
-   DATAPORT_FILE_DIRECTORY
-   DATAPORT_IMPORT_COMMIT_UNIT
-   DATAPORT_IMPORT_STATEMENT_UNIT
-   DR_ENABLE
-   DR_RM_PORT_NO
-   DR_PORT_NO
-   DR_CONNECT_TIMEOUT
-   DR_RECEIVE_TIMEOUT
-   DR_SENDER_SLEEP_TIME
-   DR_SENDER_NEXT_CONNECTION_TIMEOUT
-   DR_HBT_DETECT_TIME
-   DR_HBT_DETECT_HIGHWATER_MARK
-   DR_CONNECT_RECEIVE_TIMEOUT
-   DR PREFETCH_LOGFILE_COUNT
-   DR_KEEP_ALIVE_CNT
-   DR_MAX_LOGFILE
-   DR_STANDBY_WAIT_TIMEOUT
-   IPC_PORT_NO
-   MAX_THREAD_COUNT
-   SHM_DB_KEY
-   SHM_PAGE_COUNT_PER_KEY
-   SHM_POLICY
-   SHM_MAX_SIZE
-   SHM_STARTUP_SIZE
-   SHM_CHUNK_SIZE
-   SHM_CHUNK_ALIGN_SIZE
-   STARTUP_SHM_CHUNK_SIZE

#### 메타 테이블

아래의 메타 테이블이 삭제되었다. 

-   SYS_DATA_PORTS\_

#### 성능 뷰

아래의 성능 뷰 들이 추가되었다.  

각 성능 뷰에 대한 자세한 내용은 [*General Reference*](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_4.md)를 참고하기 바란다. 

##### 새로운 성능 뷰

-   V\$ACCESS_LIST

    ALTIBASE에 접근하는 특정 IP 패킷의 접근 허용 및 제한 여부를 보여주는 성능 뷰

-   V\$DBLINK_NOTIFIER_TRANSACTION_INFO

    AltiLinker가 처리중인 장애가 발생한 분산 트랜잭션의 정보를 보여주는 성능 뷰

-   V\$RESERVED_WORDS

    예약어를 조회할 수 있는 성능 뷰

-   V\$SNAPSHOT

    스냅샷(SNAPSHOT)의 설정 상태와 메모리, 디스크 언두 테이블스페이스의 사용량을
    보여주는 성능

##### 수정된 성능 뷰

-   V\$DBLINK_LINKER_DATA_SESSION_INFO

| Column name          | 변경내역                                                     |
| -------------------- | ------------------------------------------------------------ |
| LOCAL_TRANSACTION_ID | 추가됨 (INTEGER) </br>현재 세션에서 수행중인 로컬 트랜잭션의 식별자 |

-   V\$DBLINK_REMOTE_STATMENT_INFO

| Column name           | 변경내역                                                     |
| --------------------- | ------------------------------------------------------------ |
| GLOBAL_TRANSACTION_ID | 추가됨 (INTEGER) </br>데이터베이스 링크를 사용하고 있는 글로벌 트랜잭션의 식별자 |

-   V\$DBLINK_REMOTE_TRANSACTION_INFO

| Column name           | 변경내역                                                     |
| --------------------- | ------------------------------------------------------------ |
| XID                   | 추가됨 (VARCHAR(256)) </br>트랜잭션 브랜치 식별자            |
| GLOBAL_TRANSACTION_ID | 추가됨 (INTEGER) </br>데이터베이스 링크를 사용하고 있는 글로벌 트랜잭션의 식별자 |

-   V\$DBLINK_GLOBAL_TRANSACTION_INFO

| Column name           | 변경내역                                                     |
| --------------------- | ------------------------------------------------------------ |
| GLOBAL_TRANSACTION_ID | 추가됨 (INTEGER) </br>데이터베이스 링크를 사용하고 있는 글로벌 트랜잭션의 식별자 |

-   V\$MUTEX

| Column name | 변경내역                                                  |
| ----------- | --------------------------------------------------------- |
| THREAD_ID   | 추가됨 (VARCHAR(64))</br> 현재 LOCK을 잡고 있는 쓰레드 ID |

-   V\$REPGAP

    V\$REPGAP에서 아래의 컬럼의 의미가 변경되어, REP_GAP의 값이 매우 커진다.
    Byte 단위 값을 의미하게 되었기 때문이다.

| Column name | 변경내역                                                                       |
|-------------|--------------------------------------------------------------------------------|
| REP_LAST_SN | 마지막 로그 레코드의 일련번호 -\> 마지막 로그 레코드의 식별 번호               |
| REP_SN      | 현재 전송중인 로그 레코드의 일련번호 -\> 현재 전송중인 로그 레코드의 식별 번호 |

-   V\$REPSENDER 의 STATUS(지역서버의 이중화 송신 쓰레드의 현재상태)에 FAILBACK
    EAGER, FAILBACK FLUSH, IDLE 상태값이 추가되었다.

| Column name | 변경내역                                                     |
| ----------- | ------------------------------------------------------------ |
| STATUS      | 아래의 상태값이 추가되었다.</br>7: FAILBACK EAGER </br>8: FAILBACK FLUSH</br> 9: IDLE |

-   V\$REPSENDER_PARALLEL 의 STATUS(지역서버의 이중화 송신 쓰레드의 현재상태)에
    FAILBACK EAGER, FAILBACK FLUSH, IDLE 상태값이 추가되었다.

| Column name | 변경내역                                                     |
| ----------- | ------------------------------------------------------------ |
| STATUS      | 아래의 상태값이 추가되었다.</br>7: FAILBACK EAGER </br>8: FAILBACK FLUSH </br>9: IDLE |

-   V\$SESSION

| Column name             | 변경내역                      |
|-------------------------|-------------------------------|
| ID                      | INTEGER -\> BIGINT            |
| FAILOVER_SOURCE         | VARCHAR(255) -\> VARCHAR(256) |
| SSL_CIPHER              | VARCHAR(257) -\>VARCHAR(256)  |
| SSL_CERTIFICATE_SUBJECT | VARCHAR(257) -\>VARCHAR(256)  |
| SSL_CERTIFICATE_ISSUER  | VARCHAR(257) -\>VARCHAR(256)  |

-   V\$TRANSACTION

| Column name     | 변경내역                                                     |
| --------------- | ------------------------------------------------------------ |
| ISOLATION_LEVEL | 추가됨 (INTEGER) </br>트랜잭션의 격리 수준(isolation level)</br>0: READ COMMITED</br> 1: REPEATABLE READ </br> 2: SERIALIZABLE |

### 2.3 패키지

| OS    | CPU                       | Archive Name                                                                                                             |
|-------|---------------------------|--------------------------------------------------------------------------------------------------------------------------|
| AIX   | PowerPC                   | altibase- server-7.1.0.1.2-AIX-POWERPC-64bit-release.run                                                                 |
|       |                           | altibase- client-7.1.0.1.2-AIX-POWERPC-64bit-release.run                                                                 |
| HP-UX | IA64                      | altibase- server-7.1.0.1.2-HPUX-IA64-64bit-release.run                                                                   |
|       |                           | altibase- client -7.1.0.1.2-HPUX-IA64-64bit-release.run                                                                  |
| LINUX | X86                       | altibase- server-7.1.0.1.2-LINUX-X86-64bit-release.run                                                                   |
|       |                           | altibase- client-7.1.0.1.2-LINUX-X86-64bit-release.run                                                                   |
|       | PowerPC                   | altibase- server-7.1.0.1.2-LINUX-POWERPC-64bit-release.run                                                               |
|       |                           | altibase- client-7.1.0.1.2-LINUX-POWERPC-64bit-release.run                                                               |
|       | PowerPCLE (Little Endian) | altibase- server-7.1.0.1.2-LINUX-POWERPCLE-64bit-release.run                                                             |
|       |                           | altibase- client-7.1.0.1.2-LINUX-POWERPCLE-64bit-release.run                                                             |

### 2.4 다운로드

#### Package

<http://support.altibase.com>

#### Manual

https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/README.md

#### 설치

[Altibase Installation Guide](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Installation.md) 참고
