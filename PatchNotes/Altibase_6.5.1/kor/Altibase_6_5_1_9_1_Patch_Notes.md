Altibase 6.5.1.9.1 Patch Notes
==============================

<br/>

<br/>

# **Table of Contents**

- [New Features](#new-features)
  - [BUG-49563 OPTIMIZER\_FEATURE\_ENABLE 프로퍼티 값에 영향을 받는 프로퍼티를 추가합니다.](#bug-49563optimizer_feature_enable-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0-%EA%B0%92%EC%97%90-%EC%98%81%ED%96%A5%EC%9D%84-%EB%B0%9B%EB%8A%94-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0%EB%A5%BC-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49616 Standard Edition, Enterprise Edition에서 라이센스 발급 기준으로 MEM\_MAX\_DB\_SIZE를 추가합니다.](#bug-49616standard-edition-enterprise-edition%EC%97%90%EC%84%9C-%EB%9D%BC%EC%9D%B4%EC%84%BC%EC%8A%A4-%EB%B0%9C%EA%B8%89-%EA%B8%B0%EC%A4%80%EC%9C%BC%EB%A1%9C-mem_max_db_size%EB%A5%BC-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49636 Altibase 서버 프로퍼티 ARCHIVE\_FULL\_ACTION 설정 값에 따른 아카이브로그 쓰레드의 동작을 개선합니다.](#bug-49636altibase-%EC%84%9C%EB%B2%84-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0-archive_full_action-%EC%84%A4%EC%A0%95-%EA%B0%92%EC%97%90-%EB%94%B0%EB%A5%B8-%EC%95%84%EC%B9%B4%EC%9D%B4%EB%B8%8C%EB%A1%9C%EA%B7%B8-%EC%93%B0%EB%A0%88%EB%93%9C%EC%9D%98-%EB%8F%99%EC%9E%91%EC%9D%84-%EA%B0%9C%EC%84%A0%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49655 디스크 테이블 및 디스크 인덱스에서 사용 중인 데이터 페이지수를 조회할 수 있도록 X\$SEGMENT에 TOTAL\_USED\_PAGE\_CNT 컬럼을 추가합니다.](#bug-49655%EB%94%94%EC%8A%A4%ED%81%AC-%ED%85%8C%EC%9D%B4%EB%B8%94-%EB%B0%8F-%EB%94%94%EC%8A%A4%ED%81%AC-%EC%9D%B8%EB%8D%B1%EC%8A%A4%EC%97%90%EC%84%9C-%EC%82%AC%EC%9A%A9-%EC%A4%91%EC%9D%B8-%EB%8D%B0%EC%9D%B4%ED%84%B0-%ED%8E%98%EC%9D%B4%EC%A7%80%EC%88%98%EB%A5%BC-%EC%A1%B0%ED%9A%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EB%8F%84%EB%A1%9D-xsegment%EC%97%90-total_used_page_cnt-%EC%BB%AC%EB%9F%BC%EC%9D%84-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
- [Fixed Bugs](#fixed-bugs)
  - [BUG-47420 LENGTH()로 LOB 길이 출력 시 Altibase 서버가 비정상 종료하고 디스크 테이블에 LOB 데이터 타입의 최대 크기를 초과하여 입력되는 현상을 수정합니다.](#bug-47420length%EB%A1%9C-lob-%EA%B8%B8%EC%9D%B4-%EC%B6%9C%EB%A0%A5-%EC%8B%9C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%98%EA%B3%A0-%EB%94%94%EC%8A%A4%ED%81%AC-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90-lob-%EB%8D%B0%EC%9D%B4%ED%84%B0-%ED%83%80%EC%9E%85%EC%9D%98-%EC%B5%9C%EB%8C%80-%ED%81%AC%EA%B8%B0%EB%A5%BC-%EC%B4%88%EA%B3%BC%ED%95%98%EC%97%AC-%EC%9E%85%EB%A0%A5%EB%90%98%EB%8A%94-%ED%98%84%EC%83%81%EC%9D%84-%EC%88%98%EC%A0%95%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49423 SQL PLAN CACHE 처리 시 statement 객체가 정리되지 않은 경우 Altibase 서버가 비정상 종료하거나 CPU 사용률이 증가할 수 있습니다.](#bug-49423sql-plan-cache-%EC%B2%98%EB%A6%AC-%EC%8B%9C-statement-%EA%B0%9D%EC%B2%B4%EA%B0%80-%EC%A0%95%EB%A6%AC%EB%90%98%EC%A7%80-%EC%95%8A%EC%9D%80-%EA%B2%BD%EC%9A%B0-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%98%EA%B1%B0%EB%82%98-cpu-%EC%82%AC%EC%9A%A9%EB%A5%A0%EC%9D%B4-%EC%A6%9D%EA%B0%80%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-49439 AUDIT disconnect 설정 환경에서 데이터베이스 세션 종료 시 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-49439audit-disconnect-%EC%84%A4%EC%A0%95-%ED%99%98%EA%B2%BD%EC%97%90%EC%84%9C-%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4-%EC%84%B8%EC%85%98-%EC%A2%85%EB%A3%8C-%EC%8B%9C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-49530 Altibase 서버 운용 중 비정상 종료 발생 시 코어 덤프가 생성되는 현상을 방지합니다.](#bug-49530altibase-%EC%84%9C%EB%B2%84-%EC%9A%B4%EC%9A%A9-%EC%A4%91-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C-%EB%B0%9C%EC%83%9D-%EC%8B%9C-%EC%BD%94%EC%96%B4-%EB%8D%A4%ED%94%84%EA%B0%80-%EC%83%9D%EC%84%B1%EB%90%98%EB%8A%94-%ED%98%84%EC%83%81%EC%9D%84-%EB%B0%A9%EC%A7%80%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49543 디스크 테이블 변경 트랜잭션 수행 중 삭제된 디스크 인덱스 키를 다시 삭제하는 버그로 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-49543%EB%94%94%EC%8A%A4%ED%81%AC-%ED%85%8C%EC%9D%B4%EB%B8%94-%EB%B3%80%EA%B2%BD-%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98-%EC%88%98%ED%96%89-%EC%A4%91-%EC%82%AD%EC%A0%9C%EB%90%9C-%EB%94%94%EC%8A%A4%ED%81%AC-%EC%9D%B8%EB%8D%B1%EC%8A%A4-%ED%82%A4%EB%A5%BC-%EB%8B%A4%EC%8B%9C-%EC%82%AD%EC%A0%9C%ED%95%98%EB%8A%94-%EB%B2%84%EA%B7%B8%EB%A1%9C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-49549 파티션드 테이블에 사용한 집계 함수가 병렬 수행될 경우 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-49549%ED%8C%8C%ED%8B%B0%EC%85%98%EB%93%9C-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90-%EC%82%AC%EC%9A%A9%ED%95%9C-%EC%A7%91%EA%B3%84-%ED%95%A8%EC%88%98%EA%B0%80-%EB%B3%91%EB%A0%AC-%EC%88%98%ED%96%89%EB%90%A0-%EA%B2%BD%EC%9A%B0-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-49553 SQL Plan Cache의 PCO(Plan Cache Object 교체 과정에서 해제한 메모리를 다시 해제하는 버그로 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-49553sql-plan-cache%EC%9D%98-pcoplan-cache-object-%EA%B5%90%EC%B2%B4-%EA%B3%BC%EC%A0%95%EC%97%90%EC%84%9C-%ED%95%B4%EC%A0%9C%ED%95%9C-%EB%A9%94%EB%AA%A8%EB%A6%AC%EB%A5%BC-%EB%8B%A4%EC%8B%9C-%ED%95%B4%EC%A0%9C%ED%95%98%EB%8A%94-%EB%B2%84%EA%B7%B8%EB%A1%9C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-49557 이중화 객체에 DDL 수행 시 The table structure has been modified. 에러가 반복되는 경우 altibase\_qp.log에 로그가 과도하게 출력되는 현상을 개선합니다.](#bug-49557%EC%9D%B4%EC%A4%91%ED%99%94-%EA%B0%9D%EC%B2%B4%EC%97%90-ddl-%EC%88%98%ED%96%89-%EC%8B%9C-the-table-structure-has-been-modified-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%98%EB%B3%B5%EB%90%98%EB%8A%94-%EA%B2%BD%EC%9A%B0-altibase_qplog%EC%97%90-%EB%A1%9C%EA%B7%B8%EA%B0%80-%EA%B3%BC%EB%8F%84%ED%95%98%EA%B2%8C-%EC%B6%9C%EB%A0%A5%EB%90%98%EB%8A%94-%ED%98%84%EC%83%81%EC%9D%84-%EA%B0%9C%EC%84%A0%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49559 복합 인덱스가 있는 테이블에 ROW\_NUMBER 함수를 사용한 경우 중복된 정렬 작업을 제거하여 SQL 수행 성능을 개선합니다.](#bug-49559%EB%B3%B5%ED%95%A9-%EC%9D%B8%EB%8D%B1%EC%8A%A4%EA%B0%80-%EC%9E%88%EB%8A%94-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90-row_number-%ED%95%A8%EC%88%98%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%9C-%EA%B2%BD%EC%9A%B0-%EC%A4%91%EB%B3%B5%EB%90%9C-%EC%A0%95%EB%A0%AC-%EC%9E%91%EC%97%85%EC%9D%84-%EC%A0%9C%EA%B1%B0%ED%95%98%EC%97%AC-sql-%EC%88%98%ED%96%89-%EC%84%B1%EB%8A%A5%EC%9D%84-%EA%B0%9C%EC%84%A0%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49565 Altibase 서버 구동 중 Refine Memory Table 단계에서 실패할 때 altibase\_error.log에 출력되는 에러 메시지를 보완합니다.](#bug-49565altibase-%EC%84%9C%EB%B2%84-%EA%B5%AC%EB%8F%99-%EC%A4%91-refine-memory-table-%EB%8B%A8%EA%B3%84%EC%97%90%EC%84%9C-%EC%8B%A4%ED%8C%A8%ED%95%A0-%EB%95%8C-altibase_errorlog%EC%97%90-%EC%B6%9C%EB%A0%A5%EB%90%98%EB%8A%94-%EC%97%90%EB%9F%AC-%EB%A9%94%EC%8B%9C%EC%A7%80%EB%A5%BC-%EB%B3%B4%EC%99%84%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49569 UNION ALL 연산자를 사용한 SELECT 문에서 select\_list 절에 LOB, GEOMETRY 또는 이진 데이터 타입이 사용된 경우 예외 처리를 추가합니다.](#bug-49569union-all-%EC%97%B0%EC%82%B0%EC%9E%90%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%9C-select-%EB%AC%B8%EC%97%90%EC%84%9C-select_list-%EC%A0%88%EC%97%90-lob-geometry-%EB%98%90%EB%8A%94-%EC%9D%B4%EC%A7%84-%EB%8D%B0%EC%9D%B4%ED%84%B0-%ED%83%80%EC%9E%85%EC%9D%B4-%EC%82%AC%EC%9A%A9%EB%90%9C-%EA%B2%BD%EC%9A%B0-%EC%98%88%EC%99%B8-%EC%B2%98%EB%A6%AC%EB%A5%BC-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49613 = 연산자와 CAST 연산자에 사용된 서브쿼리의 결과가 NULL일 때 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-49613-%EC%97%B0%EC%82%B0%EC%9E%90%EC%99%80-cast-%EC%97%B0%EC%82%B0%EC%9E%90%EC%97%90-%EC%82%AC%EC%9A%A9%EB%90%9C-%EC%84%9C%EB%B8%8C%EC%BF%BC%EB%A6%AC%EC%9D%98-%EA%B2%B0%EA%B3%BC%EA%B0%80-null%EC%9D%BC-%EB%95%8C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-49619 디스크 인덱스에서 언두 테이블스페이스를 사용하는 경우 다른 트랜젝션에 의해 언두 영역이 재사용되어 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-49619%EB%94%94%EC%8A%A4%ED%81%AC-%EC%9D%B8%EB%8D%B1%EC%8A%A4%EC%97%90%EC%84%9C-%EC%96%B8%EB%91%90-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%8A%A4%ED%8E%98%EC%9D%B4%EC%8A%A4%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94-%EA%B2%BD%EC%9A%B0-%EB%8B%A4%EB%A5%B8-%ED%8A%B8%EB%9E%9C%EC%A0%9D%EC%85%98%EC%97%90-%EC%9D%98%ED%95%B4-%EC%96%B8%EB%91%90-%EC%98%81%EC%97%AD%EC%9D%B4-%EC%9E%AC%EC%82%AC%EC%9A%A9%EB%90%98%EC%96%B4-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-49620 NVL\_EQUAL(expr1, exp2, expr3)에서 expr1에 인덱스가 존재하고 expr2의 컬럼의 데이터 타입이 expr1과 다른 경우 테이블 스캔 방식을 변경하여 제품의 안정성을 향상합니다.](#bug-49620nvl_equalexpr1-exp2-expr3%EC%97%90%EC%84%9C-expr1%EC%97%90-%EC%9D%B8%EB%8D%B1%EC%8A%A4%EA%B0%80-%EC%A1%B4%EC%9E%AC%ED%95%98%EA%B3%A0-expr2%EC%9D%98-%EC%BB%AC%EB%9F%BC%EC%9D%98-%EB%8D%B0%EC%9D%B4%ED%84%B0-%ED%83%80%EC%9E%85%EC%9D%B4-expr1%EA%B3%BC-%EB%8B%A4%EB%A5%B8-%EA%B2%BD%EC%9A%B0-%ED%85%8C%EC%9D%B4%EB%B8%94-%EC%8A%A4%EC%BA%94-%EB%B0%A9%EC%8B%9D%EC%9D%84-%EB%B3%80%EA%B2%BD%ED%95%98%EC%97%AC-%EC%A0%9C%ED%92%88%EC%9D%98-%EC%95%88%EC%A0%95%EC%84%B1%EC%9D%84-%ED%96%A5%EC%83%81%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49625 TO\_DATE 함수에서 날짜형 데이터 형식으로 SSSSSS를 사용한 경우 잘못된 결과를 반환합니다.](#bug-49625to_date-%ED%95%A8%EC%88%98%EC%97%90%EC%84%9C-%EB%82%A0%EC%A7%9C%ED%98%95-%EB%8D%B0%EC%9D%B4%ED%84%B0-%ED%98%95%EC%8B%9D%EC%9C%BC%EB%A1%9C-ssssss%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%9C-%EA%B2%BD%EC%9A%B0-%EC%9E%98%EB%AA%BB%EB%90%9C-%EA%B2%B0%EA%B3%BC%EB%A5%BC-%EB%B0%98%ED%99%98%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49632 반환 데이터 타입이 LOB인 저장 함수가 ORDER BY/GROUP BY/윈도우 함수의 PARTITION BY 하위절에 사용될 때 예외 처리를 변경하여 제품의 안정성을 향상합니다.](#bug-49632%EB%B0%98%ED%99%98-%EB%8D%B0%EC%9D%B4%ED%84%B0-%ED%83%80%EC%9E%85%EC%9D%B4-lob%EC%9D%B8-%EC%A0%80%EC%9E%A5-%ED%95%A8%EC%88%98%EA%B0%80-order-bygroup-by%EC%9C%88%EB%8F%84%EC%9A%B0-%ED%95%A8%EC%88%98%EC%9D%98-partition-by-%ED%95%98%EC%9C%84%EC%A0%88%EC%97%90-%EC%82%AC%EC%9A%A9%EB%90%A0-%EB%95%8C-%EC%98%88%EC%99%B8-%EC%B2%98%EB%A6%AC%EB%A5%BC-%EB%B3%80%EA%B2%BD%ED%95%98%EC%97%AC-%EC%A0%9C%ED%92%88%EC%9D%98-%EC%95%88%EC%A0%95%EC%84%B1%EC%9D%84-%ED%96%A5%EC%83%81%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49649 LOB 컬럼을 포함한 복제 트랜잭션 수행 시 Unable to find record in \~ 에러가 발생한 경우 수신자(Receiver)가 중지됩니다.](#bug-49649lob-%EC%BB%AC%EB%9F%BC%EC%9D%84-%ED%8F%AC%ED%95%A8%ED%95%9C-%EB%B3%B5%EC%A0%9C-%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98-%EC%88%98%ED%96%89-%EC%8B%9C-unable-to-find-record-in--%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%9C-%EA%B2%BD%EC%9A%B0-%EC%88%98%EC%8B%A0%EC%9E%90receiver%EA%B0%80-%EC%A4%91%EC%A7%80%EB%90%A9%EB%8B%88%EB%8B%A4)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
  - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
  - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

New Features
============

### BUG-49563 OPTIMIZER\_FEATURE\_ENABLE 프로퍼티 값에 영향을 받는 프로퍼티를 추가합니다.

-   **module** : qp-dml-pvo

-   **Category** : Maintainability

-   **재현 빈도** : Unknown

-   **설명** : Altibase 6.3.1 옵티마이저와 동일한 옵티마이저 설정을 위해 \_\_OPTIMIZER\_INDEX\_COST\_MODE 프로퍼티의 설정값 2가
    추가되었습니다. 이 프로퍼티는 히든 프로퍼티로 관련 내용은 매뉴얼에 기록되지 않습니다.
    
    OPTIMIZER\_FEATURE\_ENABLE 설정값이 6.3.1.0.1 인 경우 이 프로퍼티의 설정값은 2가 됩니다.
    
    OPTIMIZER\_FEATURE\_ENABLE 프로퍼티 값을 6.5.1.0.0 이전 버전으로 설정하여 운영 중인 경우 Altibase 6.5.1.9.1 이전과 실행 계획이 달라질 수 있습니다.

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

### BUG-49616 Standard Edition, Enterprise Edition에서 라이센스 발급 기준으로 MEM\_MAX\_DB\_SIZE를 추가합니다.

-   **module** : id
-   **Category** : Enhancement
-   **재현 빈도** : Unknown
-   **설명** : Standard Edition, Enterprise Edition에서 라이센스 발급 기준으로 MEM\_MAX\_DB\_SIZE를 추가합니다. 이 버그에 영향을 받은
    Altibase 버전은 아래와 같습니다.
    -   Altibase 7.1
    -   Altibase 6.5.1
    
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

### BUG-49636 Altibase 서버 프로퍼티 ARCHIVE\_FULL\_ACTION 설정 값에 따른 아카이브로그 쓰레드의 동작을 개선합니다.

-   **module** : sm

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : 디스크 공간 부족으로 로그 파일 백업이 실패하는 경우 ARCHIVE\_FULL\_ACTION 설정 값에 따른 아카이브로그 쓰레드의 동작을
    개선합니다.
    
    **ARCHIVE\_FULL\_ACTION 설정 값에 따른 동작 차이**
    
    - ARCHIVE\_FULL\_ACTION = 0 
      - 변경 전 : 디스크 공간 부족으로 로그 파일 백업이 실패하는 경우 아카이브로그 쓰레드가 중지된다. 아카이브로그 쓰레드를 시작하려면 사용자가 명시적으로 ALTER SYSTEM ARCHIVE LOG START를 수행해야 합니다.
      - 변경 후 : 디스크 공간 부족으로 로그 파일 백업이 실패하는 경우 아카이브로그 쓰레드가 중지되지 않으며 차례로 다음 로그 파일 백업을 시도합니다. 백업에 실패한 로그파일은 트레이스 로그(altibase\_sm.log)에 기록합니다.
      
    - ARCHIVE\_FULL\_ACTION = 1 
      - 변경이 없습니다.
    
    - ARCHIVE\_FULL\_ACTION = 2
      - 설정값 2가 추가되었습니다. 디스크 공간 부족 실패 외에 다른 이유로 로그 파일 백업이 실패하는 경우 트레이스 로그(altibase\_sm.log)에 에러 메시지를 출력하고 다음 로그 파일의 백업을 시도합니다.
    
    **ARCHIVE\_FULL\_ACTION 속성 변경**

    읽기 전용에서 변경 가능으로 변경합니다.

    - 변경 전

      ```sql
      iSQL> ALTER SYSTEM SET ARCHIVE_FULL_ACTION = 2;
      [ERR-0104E : The property [ARCHIVE_FULL_ACTION] is read-only.]
      ```
    
    - 변경 후
    
      ```sql
      iSQL> ALTER SYSTEM SET ARCHIVE_FULL_ACTION = 2;
      Alter success
      ```
    
    ARCHIVE\_FULL\_ACTION 설정 값에 관한 설명은 [General Reference-1.Data Types & Altibase Properties](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/General%20Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#archive_full_action)에서도 확인할 수 있습니다.

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

### BUG-49655 디스크 테이블 및 디스크 인덱스에서 사용 중인 데이터 페이지수를 조회할 수 있도록 X\$SEGMENT에 TOTAL\_USED\_PAGE\_CNT 컬럼을 추가합니다.

-   **module** : sm

-   **Category** : Other

-   **재현 빈도** : Always

-   **설명** : 디스크 테이블 및 디스크 인덱스에서 사용 중인 데이터 페이지 수를 조회할 수 있도록 X\$SEGMENT에 TOTAL\_USED\_PAGE\_CNT 컬럼을 추가합니다. TOTAL\_USED\_PAGE\_CNT 컬럼은 메타 페이지와 FREE 페이지를 제외한
    데이터만 있는 페이지 수를 의미합니다.
    
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

### BUG-47420 LENGTH()로 LOB 길이 출력 시 Altibase 서버가 비정상 종료하고 디스크 테이블에 LOB 데이터 타입의 최대 크기를 초과하여 입력되는 현상을 수정합니다.

-   **module** : sm

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : LOB 데이터 입력 및 LENGTH() 출력 관련한 문제를 수정하였습니다.
    
    -   디스크 테이블에서 LOB 데이터가 최대 크기(4G-1bytes)를 초과하여 입력되는 문제
    -   메모리/휘발성 테이블에 LOB 데이터를 최대 크기를 초과하여 입력 시 실패하지만 롤백 후 데이터가 일부 남아있는 문제
    -   디스크/메모리/휘발성 메모리 테이블에서 LENGTH()로 LOB 데이터 길이 출력 시 Altibase 서버 비정상 종료 현상

    이 버그가 반영된 Altibase 6.5.1.9.1 이상에서 디스크 테이블에 4GB-1byte이상 LOB 데이터 입력 시 0x110D0, The lob size is bigger than the maximum lob size 에러가 발생합니다.
    
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

### BUG-49423 SQL PLAN CACHE 처리 시 statement 객체가 정리되지 않은 경우 Altibase 서버가 비정상 종료하거나 CPU 사용률이 증가할 수 있습니다.

-   **module** : mm-plancache

-   **Category** : Maintainability

-   **재현 빈도** : Frequence

-   **설명** : SQL PLAN CACHE 처리 시 statement 객체가 정리되지 않은 경우 Altibase 서버가 비정상 종료하거나 CPU 사용률이 증가하는 현상을 수정합니다. 
    
    본 버그로 인한 Altibase 서버 비정상 종료 현상 발생 시 altibase\_error.log 에 아래와 같은 로그가 남습니다. 

    ```
    IDE_ASSERT( aTrans->mStatus == SMX_TX_END ),
    [smxTransMgr.h:272], errno=[2]
    
    [ASSERT] ERROR LINE => [smxTransMgr.h:272]
    ```
    
    또한 수행 중인 SQL문이 없거나 적음에도 CPU 사용률이 증가하는 현상을 나타날 수 있습니다.
    
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

### BUG-49439 AUDIT disconnect 설정 환경에서 데이터베이스 세션 종료 시 Altibase 서버가 비정상 종료할 수 있습니다.

-   **module** : mm-altiaudit

-   **Category** : Maintainability

-   **재현 빈도** : Rare

-   **설명** : AUDIT disconnect 설정 환경에서 데이터베이스 세션 종료 시 Altibase 서버가 비정상 종료하는 현상을 수정합니다. 
    
-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

        altibase_error.log 에 아래와 같은 콜스택을 남기며 Altibase 서버가 비정상 종료합니다. 

        ```
        BEGIN-STACK [CRASH] =============================
        Caller[0] 0000000000417208      => mmmSignalHandler
        Caller[1] 00007F004DB5D5E0      => not found
        Caller[2] 0000000000442C3F      => mmtAuditManager::auditBySession(mmcStatement*)
        Caller[3] 000000000046925F      => mmcStatement::finalize()
        Caller[4] 0000000000470E6B      => mmcStatementManager::freeStatement(mmcStatement*)
        Caller[5] 0000000000462669      => mmcSession::finalize()
        Caller[6] 000000000041D62F      => mmtSessionManager::freeSession(mmcTask*)
        Caller[7] 0000000000413558      => mmcTask::finalize()
        Caller[8] 000000000041C9ED      => mmtSessionManager::freeTask(mmcTask*)
        Caller[9] 000000000042A485      => mmtServiceThread::terminateTask(mmcTask*)
        Caller[10] 000000000042AD82     => mmtServiceThread::executeTask()
        Caller[11] 000000000042B75C     => mmtServiceThread::run()
        Caller[12] 0000000000EA4A1B     => idtContainer::staticRunner(void*)
        Caller[13] 00007F004DB55E25     => not found
        Caller[14] 00007F004CC2434D     => not found
        END-STACK =======================================
        ```

    -   **예상 결과**

-   **Workaround**

    AUDIT disconnect 설정을 비활성화합니다.

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49530 Altibase 서버 운용 중 비정상 종료 발생 시 코어 덤프가 생성되는 현상을 방지합니다.

-   **module** : id

-   **Category** : Maintainability

-   **재현 빈도** : Always

-   **설명** : Altibase 서버 운용 중 비정상 종료 발생 시 코어 덤프가 생성되는 현상을 방지합니다.
    
    setrlimit으로 코어 파일 크기를 0으로 설정합니다. setrlimit을 호출하는 시점은 Altibase 서버 구동 단계 중 "Initialize Operating
    System Parameters" 입니다.
    
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

### BUG-49543 디스크 테이블 변경 트랜잭션 수행 중 삭제된 디스크 인덱스 키를 다시 삭제하는 버그로 Altibase 서버가 비정상 종료할 수 있습니다.

-   **module** : sm-disk-index

-   **Category** : Fatal

-   **재현 빈도** : Rare

-   **설명** : 
    
-   디스크 테이블 변경 트랜잭션 수행 중 삭제된 디스크 인덱스 키를 다시 삭제 시도하는 경우 Altibase 서버가 비정상 종료하는 현상을 회피하고 원인 분석을 위한 로그를 추가합니다. 

    이 버그 반영 이후 현상 발생 시 다음과 같은 에러 메시지를 출력합니다. 

    ```
    ERR-11069 : Internal server error in the storage manager (fail to delete key - invalid key state)
    ```

    또한 디스크 인덱스 키를 다시 삭제 시도하는 원인 분석을 위해 트레이스 로그, altibase\_error.log에 아래와 같은 에러 메시지를 추가적으로 기록합니다.

    ```
    deleteKeyFromLeafNode() INVALID KEY STATE ( IndexID: IndexID, LeafKey: LeafKey, key state : key state, sequence number : sequence number )
    
    Delete Key by same TX (TID:TID),((smxTrans*)(aMtx->mTrans))->mTransID );
    ```

    문제의 페이지를 덤프한 결과도 altibase\_dump.log 에 기록합니다.

-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

        이 버그로 인한 Altibase 서버 비정상 종료 발생 시 altibase_error.log 에 아래와 같은 콜스택이 남습니다. 

        ```
        [2021/12/13 21:58:29 32E85D][PID:6885][Thread-140305053693696][LWP-6948]
        
        leaf sequence number : 130
        
        [2021/12/13 21:58:29 32E861] Dump of Stack
        BEGIN-STACK [NORMAL] ============================
        Caller[0] 0000000000EC4DD8      => _ZN6ideLog23writeErrorTraceInternalEj12ideLogModulejPKcS2_jS2_P13__va_list_tag.constprop.2
        Caller[1] 0000000000EC8075      => ideLog::writeErrorTrace(char const*, idBool, char const*, unsigned int, char const*, __va_list_tag*)
        Caller[2] 0000000000EC3B2F      => ideLogError
        Caller[3] 0000000000D42CEF      => _ZN9sdnbBTree21deleteKeyFromLeafNodeEP6idvSQLP13sdnbStatisticP6sdrMtxP10sdnbHeaderP13sdpPhyPageHdrPs6idBoolPSB_.constprop.42
        Caller[4] 0000000000D62FC3      => sdnbBTree::deleteKey(idvSQL*, void*, void*, char*, smiIterator*, unsigned long)
        Caller[5] 0000000000DDEC3E      => smiTableCursor::deleteKeys(smiTableCursor*, scGRID, idBool)
        Caller[6] 0000000000DDEEA8      => smiTableCursor::deleteRowDRDB(smiTableCursor*, smiDMLRetryInfo const*)
        Caller[7] 0000000000DDAF45      => smiTableCursor::deleteRow(smiDMLRetryInfo const*)
        ...중략...
        END-STACK =======================================
        [2021/12/13 21:58:29 32E860][PID:6885][Thread-140305053693696][LWP-6948]
        IDE_ASSERT( 0 ), [sdnbModule.cpp:5950], errno=[16]
        errno=[16]
        
        [2021/12/13 21:58:29 32E862][PID:6885][Thread-140305053693696][LWP-6948]
        [ASSERT] ERROR LINE => [sdnbModule.cpp:5950]
        ERR-0109e(errno=16) Internal server error.
        
        altibase: /home/hdb651_p/work/altidev4/src/sm/sdn/sdnb/sdnbModule.cpp:5950: static IDE_RC sdnbBTree::deleteKeyFromLeafNode(idvSQL*, sdnbStatistic*, sdrMtx*, sdnbHeader*, sdpPhyPageHdr*, SShort*, idBool, idBool*): Assertion `0' failed.
        ```

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49549 파티션드 테이블에 사용한 집계 함수가 병렬 수행될 경우 Altibase 서버가 비정상 종료할 수 있습니다.

-   **module** : qp

-   **Category** : Fatal

-   **재현 빈도** : Frequence

-   **설명** : 파티션드 테이블에 사용한 집계 함수가 병렬 수행될 경우 Altibase 서버가 비정상 종료하는 현상을 수정합니다.
    
-   **재현 방법**

    -   **재현 절차**

        ```sql
        DROP TABLE t1 cascade;
        CREATE TABLE T1( I1 INTEGER, I2 INTEGER ) PARTITION BY HASH(I1)
         ( PARTITION P1, PARTITION P2 );
        ALTER TABLE T1 PARALLEL 2;
        VAR V1 integer;
        PREPARE SELECT /*+ no_plan_cache */ COUNT(*) FROM T1 WHERE (I1=:V1 OR I1=999) AND (I2=1 OR I2=2);
        ```

    -   **수행 결과**

            Altibase 서버 비정상 종료

    -   **예상 결과**

        ```sql
        COUNT(*)             
        -----------------------
        0                    
        1 row selected.
        ```

    -   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49553 SQL Plan Cache의 PCO(Plan Cache Object 교체 과정에서 해제한 메모리를 다시 해제하는 버그로 Altibase 서버가 비정상 종료할 수 있습니다.

-   **module** : qp

-   **Category** : Fatal

-   **재현 빈도** : Impossible

-   **설명** : SQL Plan Cache의 PCO(Plan Cache Object 교체 과정에서 해제한 메모리를 다시 해제하는 버그로 Altibase 서버가 비정상 종료하는 현상을 수정합니다.
    
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

### BUG-49557 이중화 객체에 DDL 수행 시 The table structure has been modified. 에러가 반복되는 경우 altibase\_qp.log에 로그가 과도하게 출력되는 현상을 개선합니다.

-   **module** : rp-control

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : 
    
-   이중화 객체에 DDL 수행 시 The table structure has been modified. 에러가 반복되는 경우 altibase\_qp.log에 로그가 과도하게 기록되는 현상을 개선합니다.

    The table structure has been modified. 에러는 보통 재시도하면 해결되는 종류의 에러로, 실패 시 재시도를 무한 반복합니다.
    지속적인 재시도에도 실패하는 경우 실패 처리하는 프로퍼티를 추가합니다. 히든 프로퍼티로 매뉴얼에 설명을 추가하지 않습니다.

    - 이름

      REPLICATION\_DDL\_REBUILD\_ERROR\_MAX\_COUNT

    - 설명

      이중화 객체에 DDL 수행 시 The table structure has been modified. 에러가 반복되는 경우 재시도 횟수를 설정합니다. 설정값을 초과하는 경우 ERR-61069 : Internal server error in replication module (The number of DDL rebuild attempts
      RPU\_REPLICATION\_DDL\_REBUILD\_ERROR\_MAX\_COUNTT was exceeded.).에러가 발생합니다. 0으로 설정하면 재시도하지 않으며 1 이상 설정 시 설정값만큼 재시도 후 실패 처리합니다. 

    - 값  

      0 \~ 65534

    - 기본값

      10 

    - 속성

      읽기 전용, **비공개**

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

### BUG-49559 복합 인덱스가 있는 테이블에 ROW\_NUMBER 함수를 사용한 경우 중복된 정렬 작업을 제거하여 SQL 수행 성능을 개선합니다.

-   **module** : qp

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : 복합 인덱스가 있는 테이블에 ROW\_NUMBER 함수를 사용한 경우 중복된 정렬 작업을 피하고자 Preserved Order 기능을 추가하여 SQL 수행 성능을 개선하였습니다.

    > 참고 : Preserved Order 기능
    >
    > Altibase는 이미 정렬된 테이블을 ORDER BY 구문으로 똑같이 정렬시킬 때 중복된 정렬 작업을 피하기 위해 Preserved Order라는 개념을 사용합니다. 예를 들어 테이블 t1에 i1 컬럼이 Ascending 정렬된 인덱스를 가지고 있을 때, i1 컬럼을 ORDER BY 구문으로 Ascending 정렬하면 따로 정렬 작업을 수행하지 않고 그대로 읽도록 하는 개념입니다.
    >

    관련하여 히든 프로퍼티 \_\_OPTIMIZER\_ROW\_NUMBER 가 추가되었습니다. 히든 프로퍼티로 매뉴얼에 설명을 추가하지 않습니다.

    - 이름

      \_\_OPTIMIZER\_ROW\_NUMBER

    - 설명

      본 버그에서 추가된 기능 사용 여부를 결정합니다.

    - 값

      - 0 : Preserved Order 기능을 사용하지 않음.

      - 1 : Preserved Order 기능을 사용함.

    - 기본값

      - 0

    - 속성

      변경 가능, 비공개

    이전 버전과의 호환성을 위해 이 프로퍼티 기본값 0 으로 개선한 기능 사용이 비활성화되어 있습니다. Altibase 6.5.1.9.1 이상에서 이 버그에서 개선한 기능을 사용하려면 이 프로퍼티 값을 1로 설정해야 합니다. 프로퍼티 설정값을 1로 설정하면, 이 버그의 영향을 받은 SQL 문의 실행 계획에서 WINDOW SORT 노드의 SORT\_COUNT 수가 줄어듭니다.

    이 프로퍼티 변경은 ALTER SYSTEM 으로 변경할 수 있습니다. 기본값과 다른 값을 영구 적용하고자 할 경우 altibase.properties 에 추가하고 Altibase 서버를 재시작해야 합니다. 

-   **재현 방법**

    -   **재현 절차**

            DROP TABLE T1;
            CREATE TABLE T1 ( I1 INT, I2 INT, I3 INT, I4 INT);
            DROP INDEX IDX1;
            CREATE INDEX IDX1 ON T1 (  I1, I2, I3 DESC );
            ALTER SESSION SET EXPLAIN PLAN = ON;
            SELECT ROW_NUMBER() OVER ( ORDER BY I3 DESC ), * FROM T1 WHERE I1 = 1 AND I2 = 2;

    -   **수행 결과**

        ```sql
        ------------------------------------------------------------
        PROJECT ( COLUMN_COUNT: 5, TUPLE_SIZE: 24, COST: 0.26 )
         WINDOW SORT ( ITEM_SIZE: 24, ITEM_COUNT: 0, ACCESS: 0, SORT_COUNT: 1, COST: 0.19 )
          SCAN ( TABLE: SYS.T1, INDEX: SYS.IDX1, RANGE SCAN, ACCESS: 0, COST: 0.01 )
        ------------------------------------------------------------
        ```

    -   **예상 결과**

        SORT_COUNT 가 줄어듭니다.
        
        ```sql
        ------------------------------------------------------------
        PROJECT ( COLUMN_COUNT: 5, TUPLE_SIZE: 24, COST: 0.26 )
         WINDOW SORT ( ITEM_SIZE: 24, ITEM_COUNT: 0, ACCESS: 0, SORT_COUNT: 0, COST: 0.19 )
          SCAN ( TABLE: SYS.T1, INDEX: SYS.IDX1, RANGE SCAN, ACCESS: 0, COST: 0.01 )
        ------------------------------------------------------------
        ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49565 Altibase 서버 구동 중 Refine Memory Table 단계에서 실패할 때 altibase\_error.log에 출력되는 에러 메시지를 보완합니다.

-   **module** : sm

-   **Category** : Functional Error

-   **재현 빈도** : Unknown

-   **설명** : Altibase 서버 구동 중 Refine Memory Table 단계에서 실패할 때 원인 분석을 위해 altibase\_error.log에 출력되는 에러 메시지를 보완합니다.

    이 버그 반영 후 ERR-00000(errno=16) 부분에 ERR-11088 Invalid row SCN 과 같이 보다 정확한 에러 코드와 에러 메시지를 출력합니다.

    ```
    [2022/01/11 00:14:56 416][PID:2150][Thread-47881693447936][LWP-2279]
    [FATAL] ERROR LINE => [smtPJMgr.cpp:154] MSG[error]
    ====== CURRENT IDE ERROR STACK =====
    ERR-00000(errno=16)
    [========= FATAL Terminated ==========]
    ```

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

### BUG-49569 UNION ALL 연산자를 사용한 SELECT 문에서 select\_list 절에 LOB, GEOMETRY 또는 이진 데이터 타입이 사용된 경우 예외 처리를 추가합니다.

-   **module** : qp

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : UNION ALL 연산자를 사용한 SELECT 문에서 select\_list 절에 LOB, GEOMETRY, NIBBLE, BYTE, VARBYTE 데이터 타입 중 2가지를 같이 사용한 경우 Altibase 서버가 비정상 종료하거나 무한 대기하는 상황에 예외 처리를 추가하였습니다. 
    
    이 버그가 반영된 버전에서는 ERR-91022 : LOB and GEOMETRY type data cannot be displayed 또는 ERR-21043 : Unexpected errors may have occurred: mtvCalculate\_Blob2BlobLocator: not BLOB module 에러가 발생합니다.
    
-   **재현 방법**

    -   **재현 절차**

            DROP TABLE t1 CASCADE;
            DROP TABLE t2 CASCADE;
            CREATE TABLE t1( I1  BLOB );
            CREATE TABLE t2 ( I1 BYTE(12) );
            INSERT INTO t2 VALUES (1);
            SELECT i1 FROM t1 UNION ALL SELECT i1 FROM t2;

    -   **수행 결과**

            [ERR-91015 : Communication failure.]

    -   **예상 결과**

            [ERR-91022 : LOB and GEOMETRY type data cannot be displayed]

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49613 = 연산자와 CAST 연산자에 사용된 서브쿼리의 결과가 NULL일 때 Altibase 서버가 비정상 종료할 수 있습니다.

-   **module** : qp

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : = 연산자와 CAST 연산자에 사용된 서브쿼리의 결과가 NULL일 때 Altibase 서버가 비정상 종료하는 현상을 수정합니다.

-   **재현 방법**

    -   **재현 절차**

        ```sql
        CREATE TABLE T1 ( I1 INTEGER, I2 INTEGER, I3 INTEGER ) TABLESPACE SYS_TBS_DISK_DATA;
        INSERT INTO T1 VALUES (1, 1, NULL);
        CREATE TABLE T2 ( I1 INTEGER ) TABLESPACE SYS_TBS_DISK_DATA;
        SELECT * FROM T1 WHERE I1 = (SELECT DISTINCT I1 || I2 FROM T2);
        ```

    -   **수행 결과**

            [ERR-91015 : Communication failure.]

    -   **예상 결과**

            No rows selected.

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49619 디스크 인덱스에서 언두 테이블스페이스를 사용하는 경우 다른 트랜젝션에 의해 언두 영역이 재사용되어 Altibase 서버가 비정상 종료할 수 있습니다.

-   **module** : sm-disk-index

-   **Category** : Fatal

-   **재현 빈도** : Rare

-   **설명** : 디스크 인덱스에서 언두 테이블스페이스를 사용하는 경우 다른 트랜젝션에 의해 언두 영역이 재사용되어 Altibase 서버가 비정상 종료하는 현상을 수정합니다.

    본 버그로 인한 Altibase 서버 비정상 종료 발생 시 트레이스 로그에 아래와 같은 로그가 기록됩니다.

    - altibase\_error.log

      ```bash
      [ASSERT] ERROR LINE => [sdnIndexCTL.cpp:2208]
      ```

    - altibase\_boot.log 에 아래와 같은 형태의 인덱스 및 언두 페이지 정보 기록

      ```
      [2022/02/09 16:42:10] [Thread-28749] [Level-0]
        Undo PageID               : 56023
        Undo Slot Number          : 91
        UndoRec Hdr Type          : 2
        Chained CTS's Commit SCN  : 61801506952
        Min DskView SCN           : 61801348159
      ```

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

### BUG-49620 NVL\_EQUAL(expr1, exp2, expr3)에서 expr1에 인덱스가 존재하고 expr2의 컬럼의 데이터 타입이 expr1과 다른 경우 테이블 스캔 방식을 변경하여 제품의 안정성을 향상합니다.

-   **module** : qp

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : NVL\_EQUAL(expr1, exp2, expr3)에서 expr1에 인덱스가 존재하고 expr2의 컬럼의 데이터 타입이 expr1과 다른 경우 Altibase 서버가 비정상 종료하는 현상을 수정합니다.

-   **재현 방법**

    -   **재현 절차**

        ```sql
        CREATE TABLE T1( I1 INTEGER, I2 VARCHAR(10) ) PARTITION BY HASH( I1 ) ( PARTITION P1, PARTITION P2 TABLESPACE SYS_TBS_MEM_DATA, PARTITION P3 ) TABLESPACE SYS_TBS_DISK_DATA;
        CREATE INDEX IDX1 ON T1(I1) LOCAL;
        SELECT * FROM T1 WHERE NVL_EQUAL(I1,I2,2);
        ```

    -   **수행 결과**

        ```sql
        Altibase 서버 비정상 종료
        
        ALTER SESSION SET EXPLAIN PLAN = ONLY; 수행 후 SELECT 수행 시 실행 계획
        ------------------------------------------------------------
        PROJECT ( COLUMN_COUNT: 2, TUPLE_SIZE: 16, COST: 58.66 )
         PARTITION-COORDINATOR ( TABLE: SYS.T1, PARTITION: 3/3, ACCESS: ??, COST: 57.87 )
          SCAN ( PARTITION: P3, INDEX: SYS.IDX1, RANGE SCAN, ACCESS: ??, COST: 23.09 )
          SCAN ( PARTITION: P2, INDEX: SYS.IDX1, RANGE SCAN, ACCESS: ??, COST: 11.69 )
          SCAN ( PARTITION: P1, INDEX: SYS.IDX1, RANGE SCAN, ACCESS: ??, COST: 23.09 )
        ------------------------------------------------------------
        ```

    -   **예상 결과**

        ```sql
        I1          I2          
        ---------------------------
        No rows selected.
        
        
        ALTER SESSION SET EXPLAIN PLAN = ONLY; 수행 후 SELECT 수행 시 실행 계획
        ------------------------------------------------------------
        PROJECT ( COLUMN_COUNT: 2, TUPLE_SIZE: 16, COST: 386.68 )
         PARTITION-COORDINATOR ( TABLE: SYS.T1, PARTITION: 3/3, FULL SCAN, ACCESS: 0, COST: 385.88 )
          SCAN ( PARTITION: P3, FULL SCAN, ACCESS: 0, DISK_PAGE_COUNT: 64, COST: 129.28 )
          SCAN ( PARTITION: P2, FULL SCAN, ACCESS: 0, COST: 127.32 )
          SCAN ( PARTITION: P1, FULL SCAN, ACCESS: 0, DISK_PAGE_COUNT: 64, COST: 129.28 )
        ------------------------------------------------------------
        ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49625 TO\_DATE 함수에서 날짜형 데이터 형식으로 SSSSSS를 사용한 경우 잘못된 결과를 반환합니다.

-   **module** : mt

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : TO\_DATE 함수에서 날짜형 데이터 형식으로 SSSSSS를 사용한 경우 잘못된 결과를 반환하는 오류를 수정합니다. 버그 조건에 해당하는SQL 수행 시 버그 반영 전/후 SQL 수행 결과가 달라질 수 있습니다.
    
    이 버그는 아래 버전에 반영되었습니다.

    - Altiabse 6.5.1.9.1

-   **재현 방법**

    -   **재현 절차**

        ```sql
        ALTER SESSION SET DEFAULT_DATE_FORMAT = 'YYYY-MM-DD HH:MI:SS:SSSSSS';
        DROP TABLE T1 CASCADE;
        CREATE TABLE T1 (C1 VARCHAR(30), C2 DATE);
        INSERT INTO T1 VALUES('2022-01-11 02:17:39.958', TO_DATE('2022-01-11 02:17:39.958', 'YYYY-MM-DD HH:MI:SS.SSSSSS'));
        SELECT C1, TO_CHAR(C2, 'YYYY-MM-DD HH24:MI:SS.FF3') FROM T1;
        ```

    -   **수행 결과**

        ```sql
        iSQL> SELECT C1, TO_CHAR(C2, 'YYYY-MM-DD HH24:MI:SS.FF3') FROM T1;
        C1                              TO_CHAR(C2,'YYYY-MM-DDHH24:MI:SS.FF3')
        -------------------------------------------------------------------------
        2022-01-11 02:17:39.958         2022-01-11 02:17:39.000
        1 row selected.
        ```

    -   **예상 결과**

        ```sql
        iSQL> SELECT C1, TO_CHAR(C2, 'YYYY-MM-DD HH24:MI:SS.FF3') FROM T1;
        C1                              TO_CHAR(C2,'YYYY-MM-DDHH24:MI:SS.FF3')
        -------------------------------------------------------------------------
        2022-01-11 02:17:39.958         2022-01-11 02:17:39.958
        1 row selected.
        ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49632 반환 데이터 타입이 LOB인 저장 함수가 ORDER BY/GROUP BY/윈도우 함수의 PARTITION BY 하위절에 사용될 때 예외 처리를 변경하여 제품의 안정성을 향상합니다.

-   **module** : qp

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : 반환 데이터 타입이 LOB인 저장 함수가 ORDER BY/GROUP BY/윈도우 함수의 PARTITION BY 하위절에 사용될 때 Altibase 서버가 비정상 종료하는 현상을 개선합니다.
    
-   **재현 방법**

    -   **재현 절차**

            CREATE TABLE T1( I1 CHAR(10), I2 CHAR(10), I3 CHAR(10), I4 CHAR(10) ) TABLESPACE SYS_TBS_MEM_DATA;
            CREATE FUNCTION FUNC1
            (V1 CLOB) 
            RETURN CLOB 
            AS
              V2 CLOB; 
            BEGIN 
              V2 := V1; 
              RETURN V2; 
            END;
            /
            INSERT INTO T1(I2) VALUES (637);
            SELECT GROUPING_ID(FUNC1(I1)) 
              FROM T1 
             GROUP BY GROUPING SETS(1), FUNC1(I1);

    -   **수행 결과**

            Altibase 서버 비정상 종료

    -   **예상 결과**

            [ERR-3123E : An incomparable data type (GEOMETRY,LOB) cannot be used in a SELECT statement that has a DISTINCT clause.]

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49649 LOB 컬럼을 포함한 복제 트랜잭션 수행 시 Unable to find record in \~ 에러가 발생한 경우 수신자(Receiver)가 중지됩니다.

-   **module** : rp-receiver

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : LOB 컬럼을 포함한 복제 트랜잭션 수행 시 Unable to find record in \~ 에러가 발생한 경우 수신자(Receiver)가 중지되지 않고
    정상적으로 데이터 충돌 처리하도록 수정합니다. 
    
    이 버그 발생 시 수신자, 송신자에서 확인할 수 있는 현상입니다.
    
    - **수신자 측**
    
      트레이스 로그에 아래와 같은 에러가 남습니다.
    
      - **altibase\_rp\_conflict.log**
    
        ```
        ERR-610f7(errno=62) [Receiver] Unable to find record in ...
        ```
    
      - **altibase\_rp.log**
    
        ```
        ERR-610f7(errno=62) [Receiver] Unable to find record in openLOBCursor() function
        ERR-61048(errno=62) [Receiver] replication_name receiver has recvXLog error in run()
        [Receiver] RepName:replication_name is processed at ~ 
        [Receiver] RepName:replication_name is received at ~
        ERR-6104b(errno=62) [Receiver] replication_name receiver is ended(by thr_exit)
        Error Stop!
        [Receiver] Replication replication_name Stopped ...
        ```
    
    - **송신자 측**

      송신자 측에서 REPLICATION\_SENDER\_SLEEP\_TIMEOUT 프로퍼티 설정에 따라 재시작을 반복하지만 수신자 측에서 Unable to find record in openLOBCursor() function 에러로 수신자가 정상적으로 시작되지 않습니다 .이로 인해 이중화 갭이 발생합니다.

      트레이스 로그에 아래와 같은 에러가 남습니다.

      - **altibase\_rp.log**

        ```
        [SenderApply] Replication replication_name Start
        [Sender] Replication replication_name:0 Start... at[93025988]
        [SenderApply] Replication replication_name Got Error
        ERR-620f0(errno=11) [Sender] Stop sender thread replication_name:0 at [93027296], Restart SN[93025988]
        ERR-7101a(errno=16) Connection closed
        ERR-61022(errno=11) [Sender] Sender Sleep : 60 seconds
        ```

    이 버그가 반영된 버전에서는 LOB 컬럼을 포함한 복제 트랜잭션 수행 시 존재하지 않는 프라이머리 키 값인 경우 수신자 측 트레이스 로그 altibase\_rp\_conflict.log에 아래와 같은 형태의 로그가 남습니다.

    ```
    ERR-610f7(errno=16) [Receiver] Unable to find record in openLOBCursor() function
    A failure occurred while opening LOB Cursor (Table : ) (PK : ) ; (TID : ) COMMIT (TID : )
    ```

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
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    6.5.1.9.1     |          6.3.1          |    8.1.1     |        7.1.3        |            7.4.5             |

> Altibase 6.5.1 패치 버전별 히스토리는 [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_6.5.1/Altibase_6_5_1_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

#### CM protocol Version

통신 프로토콜 버전은 변경되지 않았다.

#### Replication protocol Version

Replication 프로토콜 버전은 변경되지 않았다.

### 프로퍼티

#### 추가된 프로퍼티

#### 변경된 프로퍼티

#### 삭제된 프로퍼티

### 성능 뷰

#### 추가된 성능 뷰

#### 변경된 성능 뷰

#### 삭제된 성능 뷰
