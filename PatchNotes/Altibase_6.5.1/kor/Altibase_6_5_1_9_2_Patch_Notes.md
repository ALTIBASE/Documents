Altibase 6.5.1.9.2 Patch Notes
==============================

<br/>

<br/>

# **Table of Contents**  

- [New Features](#new-features)
  - [BUG-49645 이중화 송신자에게 고정 IP 주소를 할당하는 기능을 추가합니다.](#bug-49645%EC%9D%B4%EC%A4%91%ED%99%94-%EC%86%A1%EC%8B%A0%EC%9E%90%EC%97%90%EA%B2%8C-%EA%B3%A0%EC%A0%95-ip-%EC%A3%BC%EC%86%8C%EB%A5%BC-%ED%95%A0%EB%8B%B9%ED%95%98%EB%8A%94-%EA%B8%B0%EB%8A%A5%EC%9D%84-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)

- [Fixed Bugs](#fixed-bugs)
  - [BUG-48349 집합 연산자 중 INTERSECT 또는 MINUS를 사용한 SQL 문에 SET BUCKET COUNT 힌트가 적용되지 않습니다.](#bug-48349%EC%A7%91%ED%95%A9-%EC%97%B0%EC%82%B0%EC%9E%90-%EC%A4%91-intersect-%EB%98%90%EB%8A%94-minus%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%9C-sql-%EB%AC%B8%EC%97%90-set-bucket-count-%ED%9E%8C%ED%8A%B8%EA%B0%80-%EC%A0%81%EC%9A%A9%EB%90%98%EC%A7%80-%EC%95%8A%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-49451 저장 프로시저 바디에서 사용한 SQL 문의 LOOP 절에 호스트 변수 또는 지역 변수 사용 시 ERR-31248 : Mismatched bind column count 에러가 발생합니다.](#bug-49451%EC%A0%80%EC%9E%A5-%ED%94%84%EB%A1%9C%EC%8B%9C%EC%A0%80-%EB%B0%94%EB%94%94%EC%97%90%EC%84%9C-%EC%82%AC%EC%9A%A9%ED%95%9C-sql-%EB%AC%B8%EC%9D%98-loop-%EC%A0%88%EC%97%90-%ED%98%B8%EC%8A%A4%ED%8A%B8-%EB%B3%80%EC%88%98-%EB%98%90%EB%8A%94-%EC%A7%80%EC%97%AD-%EB%B3%80%EC%88%98-%EC%82%AC%EC%9A%A9-%EC%8B%9C-err-31248--mismatched-bind-column-count-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49505 복잡도가 높은 SQL문 수행 시 PREPARE\_STMT\_MEMORY\_MAXIMUM 초과로 SQL Plan Cache에 실행 계획을 등록하지 못한 경우 예외 처리를 추가합니다.](#bug-49505%EB%B3%B5%EC%9E%A1%EB%8F%84%EA%B0%80-%EB%86%92%EC%9D%80-sql%EB%AC%B8-%EC%88%98%ED%96%89-%EC%8B%9C-prepare_stmt_memory_maximum-%EC%B4%88%EA%B3%BC%EB%A1%9C-sql-plan-cache%EC%97%90-%EC%8B%A4%ED%96%89-%EA%B3%84%ED%9A%8D%EC%9D%84-%EB%93%B1%EB%A1%9D%ED%95%98%EC%A7%80-%EB%AA%BB%ED%95%9C-%EA%B2%BD%EC%9A%B0-%EC%98%88%EC%99%B8-%EC%B2%98%EB%A6%AC%EB%A5%BC-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49556 매개변수 값을 설정하지 않고 ParameterMetaData 메소드로 매개변수 정보를 조회하면 NullPointerException 에러가 발생합니다.](#bug-49556%EB%A7%A4%EA%B0%9C%EB%B3%80%EC%88%98-%EA%B0%92%EC%9D%84-%EC%84%A4%EC%A0%95%ED%95%98%EC%A7%80-%EC%95%8A%EA%B3%A0-parametermetadata-%EB%A9%94%EC%86%8C%EB%93%9C%EB%A1%9C-%EB%A7%A4%EA%B0%9C%EB%B3%80%EC%88%98-%EC%A0%95%EB%B3%B4%EB%A5%BC-%EC%A1%B0%ED%9A%8C%ED%95%98%EB%A9%B4-nullpointerexception-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49571 Windows 환경에서 Altibase 서버에서 의도적으로 Altibase 서버를 비정상 종료시킬 때 콜스택이 출력되지 않는 현상을 개선합니다.](#bug-49571windows-%ED%99%98%EA%B2%BD%EC%97%90%EC%84%9C-altibase-%EC%84%9C%EB%B2%84%EC%97%90%EC%84%9C-%EC%9D%98%EB%8F%84%EC%A0%81%EC%9C%BC%EB%A1%9C-altibase-%EC%84%9C%EB%B2%84%EB%A5%BC-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%EC%8B%9C%ED%82%AC-%EB%95%8C-%EC%BD%9C%EC%8A%A4%ED%83%9D%EC%9D%B4-%EC%B6%9C%EB%A0%A5%EB%90%98%EC%A7%80-%EC%95%8A%EB%8A%94-%ED%98%84%EC%83%81%EC%9D%84-%EA%B0%9C%EC%84%A0%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49580 메모리 테이블 또는 휘발성 메모리 테이블에 LOB 데이터 입력 시 과도한 메모리 사용을 개선합니다.](#bug-49580%EB%A9%94%EB%AA%A8%EB%A6%AC-%ED%85%8C%EC%9D%B4%EB%B8%94-%EB%98%90%EB%8A%94-%ED%9C%98%EB%B0%9C%EC%84%B1-%EB%A9%94%EB%AA%A8%EB%A6%AC-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90-lob-%EB%8D%B0%EC%9D%B4%ED%84%B0-%EC%9E%85%EB%A0%A5-%EC%8B%9C-%EA%B3%BC%EB%8F%84%ED%95%9C-%EB%A9%94%EB%AA%A8%EB%A6%AC-%EC%82%AC%EC%9A%A9%EC%9D%84-%EA%B0%9C%EC%84%A0%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49614 THREAD\_REUSE\_ENABLE=0 설정하고 Altibase 서버 운영 시 V\$MEMSTAT에 부정확한 메모리 통계 정보가 출력되는 현상을 개선합니다.](#bug-49614thread_reuse_enable0-%EC%84%A4%EC%A0%95%ED%95%98%EA%B3%A0-altibase-%EC%84%9C%EB%B2%84-%EC%9A%B4%EC%98%81-%EC%8B%9C-vmemstat%EC%97%90-%EB%B6%80%EC%A0%95%ED%99%95%ED%95%9C-%EB%A9%94%EB%AA%A8%EB%A6%AC-%ED%86%B5%EA%B3%84-%EC%A0%95%EB%B3%B4%EA%B0%80-%EC%B6%9C%EB%A0%A5%EB%90%98%EB%8A%94-%ED%98%84%EC%83%81%EC%9D%84-%EA%B0%9C%EC%84%A0%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49642 테이블스페이스 삭제와 생성이 동시에 수행 중 Altibase 서버가 비정상 종료한 경우 재시작 복구(Restart Recovery)가 실패할 수 있습니다.](#bug-49642%ED%85%8C%EC%9D%B4%EB%B8%94%EC%8A%A4%ED%8E%98%EC%9D%B4%EC%8A%A4-%EC%82%AD%EC%A0%9C%EC%99%80-%EC%83%9D%EC%84%B1%EC%9D%B4-%EB%8F%99%EC%8B%9C%EC%97%90-%EC%88%98%ED%96%89-%EC%A4%91-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%9C-%EA%B2%BD%EC%9A%B0-%EC%9E%AC%EC%8B%9C%EC%9E%91-%EB%B3%B5%EA%B5%ACrestart-recovery%EA%B0%80-%EC%8B%A4%ED%8C%A8%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-49643 LOB 칼럼을 포함한 테이블에 BEFORE UPDATE 트리거 수행 시 예외 처리를 추가합니다.](#bug-49643lob-%EC%B9%BC%EB%9F%BC%EC%9D%84-%ED%8F%AC%ED%95%A8%ED%95%9C-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90-before-update-%ED%8A%B8%EB%A6%AC%EA%B1%B0-%EC%88%98%ED%96%89-%EC%8B%9C-%EC%98%88%EC%99%B8-%EC%B2%98%EB%A6%AC%EB%A5%BC-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49670 SQL Plan cache에 등록된 SQL 문 수행 중 Hard Parsing을 다시 진행할 때 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-49670sql-plan-cache%EC%97%90-%EB%93%B1%EB%A1%9D%EB%90%9C-sql-%EB%AC%B8-%EC%88%98%ED%96%89-%EC%A4%91-hard-parsing%EC%9D%84-%EB%8B%A4%EC%8B%9C-%EC%A7%84%ED%96%89%ED%95%A0-%EB%95%8C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-49681 디스크 테이블스페이스에 접근하는 트랜잭션 처리 중 버퍼 풀(Buffer Pool) 부족으로 버퍼 교체 발생 시 동시성 문제로 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-49681%EB%94%94%EC%8A%A4%ED%81%AC-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%8A%A4%ED%8E%98%EC%9D%B4%EC%8A%A4%EC%97%90-%EC%A0%91%EA%B7%BC%ED%95%98%EB%8A%94-%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98-%EC%B2%98%EB%A6%AC-%EC%A4%91-%EB%B2%84%ED%8D%BC-%ED%92%80buffer-pool-%EB%B6%80%EC%A1%B1%EC%9C%BC%EB%A1%9C-%EB%B2%84%ED%8D%BC-%EA%B5%90%EC%B2%B4-%EB%B0%9C%EC%83%9D-%EC%8B%9C-%EB%8F%99%EC%8B%9C%EC%84%B1-%EB%AC%B8%EC%A0%9C%EB%A1%9C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-49682 함수 기반 인덱스(function-based index)에 인덱스 키와 다른 데이터 타입의 데이터가 입력되는 경우 예외 처리를 변경합니다.](#bug-49682%ED%95%A8%EC%88%98-%EA%B8%B0%EB%B0%98-%EC%9D%B8%EB%8D%B1%EC%8A%A4function-based-index%EC%97%90-%EC%9D%B8%EB%8D%B1%EC%8A%A4-%ED%82%A4%EC%99%80-%EB%8B%A4%EB%A5%B8-%EB%8D%B0%EC%9D%B4%ED%84%B0-%ED%83%80%EC%9E%85%EC%9D%98-%EB%8D%B0%EC%9D%B4%ED%84%B0%EA%B0%80-%EC%9E%85%EB%A0%A5%EB%90%98%EB%8A%94-%EA%B2%BD%EC%9A%B0-%EC%98%88%EC%99%B8-%EC%B2%98%EB%A6%AC%EB%A5%BC-%EB%B3%80%EA%B2%BD%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49706 iLoader in 성능 개선을 위해 CSV 파서를 최적화합니다.](#bug-49706iloader-in-%EC%84%B1%EB%8A%A5-%EA%B0%9C%EC%84%A0%EC%9D%84-%EC%9C%84%ED%95%B4-csv-%ED%8C%8C%EC%84%9C%EB%A5%BC-%EC%B5%9C%EC%A0%81%ED%99%94%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49708 ALTER TABLE 수행으로 디스크 인덱스를 재구성이 해야 할 때 인덱스 활성화 상태를 확인하는 과정을 추가합니다.](#bug-49708alter-table-%EC%88%98%ED%96%89%EC%9C%BC%EB%A1%9C-%EB%94%94%EC%8A%A4%ED%81%AC-%EC%9D%B8%EB%8D%B1%EC%8A%A4%EB%A5%BC-%EC%9E%AC%EA%B5%AC%EC%84%B1%EC%9D%B4-%ED%95%B4%EC%95%BC-%ED%95%A0-%EB%95%8C-%EC%9D%B8%EB%8D%B1%EC%8A%A4-%ED%99%9C%EC%84%B1%ED%99%94-%EC%83%81%ED%83%9C%EB%A5%BC-%ED%99%95%EC%9D%B8%ED%95%98%EB%8A%94-%EA%B3%BC%EC%A0%95%EC%9D%84-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49718 비활성화 상태의 인덱스에 인덱스 통계 정보를 설정할 때 예외 처리를 추가합니다.](#bug-49718%EB%B9%84%ED%99%9C%EC%84%B1%ED%99%94-%EC%83%81%ED%83%9C%EC%9D%98-%EC%9D%B8%EB%8D%B1%EC%8A%A4%EC%97%90-%EC%9D%B8%EB%8D%B1%EC%8A%A4-%ED%86%B5%EA%B3%84-%EC%A0%95%EB%B3%B4%EB%A5%BC-%EC%84%A4%EC%A0%95%ED%95%A0-%EB%95%8C-%EC%98%88%EC%99%B8-%EC%B2%98%EB%A6%AC%EB%A5%BC-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49725 테이블 잠금 획득 실패로 이중화 SYNC 동작이 실패한 경우 이중화 송신자 측 altibase\_rp.log에 ERR-61152(errno=16) Replication synchronization failed. Check whether the index on the remote server is consistent. 에러가 발생합니다.](#bug-49725%ED%85%8C%EC%9D%B4%EB%B8%94-%EC%9E%A0%EA%B8%88-%ED%9A%8D%EB%93%9D-%EC%8B%A4%ED%8C%A8%EB%A1%9C-%EC%9D%B4%EC%A4%91%ED%99%94-sync-%EB%8F%99%EC%9E%91%EC%9D%B4-%EC%8B%A4%ED%8C%A8%ED%95%9C-%EA%B2%BD%EC%9A%B0-%EC%9D%B4%EC%A4%91%ED%99%94-%EC%86%A1%EC%8B%A0%EC%9E%90-%EC%B8%A1-altibase_rplog%EC%97%90-err-61152errno16-replication-synchronization-failed-check-whether-the-index-on-the-remote-server-is-consistent-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49728 디스크 인덱스 키 삽입 과정에서 인덱스 노드 공간 활용을 위해 인덱스 구조를 변경하고 인덱스 키 삽입 위치 계산 과정에서 Altibase 서버가 비정상 종료합니다.](#bug-49728%EB%94%94%EC%8A%A4%ED%81%AC-%EC%9D%B8%EB%8D%B1%EC%8A%A4-%ED%82%A4-%EC%82%BD%EC%9E%85-%EA%B3%BC%EC%A0%95%EC%97%90%EC%84%9C-%EC%9D%B8%EB%8D%B1%EC%8A%A4-%EB%85%B8%EB%93%9C-%EA%B3%B5%EA%B0%84-%ED%99%9C%EC%9A%A9%EC%9D%84-%EC%9C%84%ED%95%B4-%EC%9D%B8%EB%8D%B1%EC%8A%A4-%EA%B5%AC%EC%A1%B0%EB%A5%BC-%EB%B3%80%EA%B2%BD%ED%95%98%EA%B3%A0-%EC%9D%B8%EB%8D%B1%EC%8A%A4-%ED%82%A4-%EC%82%BD%EC%9E%85-%EC%9C%84%EC%B9%98-%EA%B3%84%EC%82%B0-%EA%B3%BC%EC%A0%95%EC%97%90%EC%84%9C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49739 MERGE JOIN을 사용한 CREATE AS SELECT 문을 수행한 세션이 SESSION CLOSE로 강제 종료되지 않습니다.](#bug-49739merge-join%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%9C-create-as-select-%EB%AC%B8%EC%9D%84-%EC%88%98%ED%96%89%ED%95%9C-%EC%84%B8%EC%85%98%EC%9D%B4-session-close%EB%A1%9C-%EA%B0%95%EC%A0%9C-%EC%A2%85%EB%A3%8C%EB%90%98%EC%A7%80-%EC%95%8A%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-49743 Altibase 서버 구동 시 리빌드되지 않은 인덱스 접근 시 Altibase 서버가 비정상 종료합니다.](#bug-49743altibase-%EC%84%9C%EB%B2%84-%EA%B5%AC%EB%8F%99-%EC%8B%9C-%EB%A6%AC%EB%B9%8C%EB%93%9C%EB%90%98%EC%A7%80-%EC%95%8A%EC%9D%80-%EC%9D%B8%EB%8D%B1%EC%8A%A4-%EC%A0%91%EA%B7%BC-%EC%8B%9C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49746 윈도우(분석) 함수, ORDER BY 절, GROUP BY 절을 사용한 질의문에서 디스크 임시 공간을 사용하면 결과 오류가 발생합니다.](#bug-49746%EC%9C%88%EB%8F%84%EC%9A%B0%EB%B6%84%EC%84%9D-%ED%95%A8%EC%88%98-order-by-%EC%A0%88-group-by-%EC%A0%88%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%9C-%EC%A7%88%EC%9D%98%EB%AC%B8%EC%97%90%EC%84%9C-%EB%94%94%EC%8A%A4%ED%81%AC-%EC%9E%84%EC%8B%9C-%EA%B3%B5%EA%B0%84%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%98%EB%A9%B4-%EA%B2%B0%EA%B3%BC-%EC%98%A4%EB%A5%98%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49756 INSERT 문 values 절에 NOT NULL 제약 조건을 가진 LOB 컬럼에 EMPTY\_CLOB() 또는 EMPTY\_BLOB() 함수를 사용하면 ERR-31074 : Unable to insert (or update) NULL into NOT NULL column. 에러가 발생합니다.](#bug-49756insert-%EB%AC%B8-values-%EC%A0%88%EC%97%90-not-null-%EC%A0%9C%EC%95%BD-%EC%A1%B0%EA%B1%B4%EC%9D%84-%EA%B0%80%EC%A7%84-lob-%EC%BB%AC%EB%9F%BC%EC%97%90-empty_clob-%EB%98%90%EB%8A%94-empty_blob-%ED%95%A8%EC%88%98%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EB%A9%B4-err-31074--unable-to-insert-or-update-null-into-not-null-column-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49769 altibase.properties.sample 파일에서 지원하지 않는 REPLICATION\_NET\_CONN\_IP\_STACK 프로퍼티를 삭제합니다.](#bug-49769altibasepropertiessample-%ED%8C%8C%EC%9D%BC%EC%97%90%EC%84%9C-%EC%A7%80%EC%9B%90%ED%95%98%EC%A7%80-%EC%95%8A%EB%8A%94-replication_net_conn_ip_stack-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0%EB%A5%BC-%EC%82%AD%EC%A0%9C%ED%95%A9%EB%8B%88%EB%8B%A4)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
  - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
  - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<br/>

# New Features

### BUG-49645 이중화 송신자에게 고정 IP 주소를 할당하는 기능을 추가합니다.

-   **module** : rp

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : 이중화 송신자에게 고정 IP 주소를 할당하는 기능을 추가합니다. 이 기능은 특수한 목적으로 제공하고 있으므로 자세한
    내용을 원할 경우 Altibase 기술 지원 센터로 연락해주세요.

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

<br/>

Fixed Bugs
==========

### BUG-48349 집합 연산자 중 INTERSECT 또는 MINUS를 사용한 SQL 문에 SET BUCKET COUNT 힌트가 적용되지 않습니다.

-   **module** : qp

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : 집합 연산자 중 INTERSECT 또는 MINUS를 사용한 SQL 문에 SET BUCKET COUNT 힌트가 적용되지 않는 문제를 수정합니다.
    
-   **재현 방법**

    -   **재현 절차**

        ```sql
        DROP TABLE t1 CASCADE;
        DROP TABLE t2 CASCADE;
        
        CREATE TABLE t1(i1 INTEGER);
        CREATE TABLE t2(i1 INTEGER) ;
        
        ALTER SESSION SET EXPLAIN PLAN = ON;
        ALTER SESSION SET TRCLOG_DETAIL_PREDICATE = 1;
        
        # INTERSECT
        SELECT /*+ set bucket count (256) hash bucket count (512) */ i1 FROM t1 INTERSECT SELECT i1 FROM t2;
        
        # MINUS
        SELECT /*+ set bucket count (256) hash bucket count (512) */ i1 FROM t1 MINUS SELECT i1 FROM t2;
        ```

    -   **수행 결과**

        ```sql
        # INTERSECT
        SELECT /*+ set bucket count (256) hash bucket count (512) */ i1 FROM t1 INTERSECT SELECT i1 FROM t2;
        ------------------------------------------------------------
        PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: 236.82 )
         VIEW ( ACCESS: 0, COST: 236.16 )
          SET-INTERSECT ( ITEM_SIZE: 24, ITEM_COUNT: 0, BUCKET_COUNT: 512, ACCESS: 0, COST: 236.16 )
           PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: 118.08 )
            SCAN ( TABLE: SYS.T1, FULL SCAN, ACCESS: 0, COST: 116.76 )
           PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: 118.08 )
            SCAN ( TABLE: SYS.T2, FULL SCAN, ACCESS: 0, COST: 116.76 )
        ------------------------------------------------------------
        
        # MINUS
        SELECT /*+ set bucket count (256) hash bucket count (512) */ i1 FROM t1 MINUS SELECT i1 FROM t2;
        ------------------------------------------------------------
        PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: 236.82 )
         VIEW ( ACCESS: 0, COST: 236.16 )
          SET-DIFFERENCE ( ITEM_SIZE: 24, ITEM_COUNT: 0, BUCKET_COUNT: 512, ACCESS: 0, COST: 236.16 )
           PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: 118.08 )
            SCAN ( TABLE: SYS.T1, FULL SCAN, ACCESS: 0, COST: 116.76 )
           PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: 118.08 )
            SCAN ( TABLE: SYS.T2, FULL SCAN, ACCESS: 0, COST: 116.76 )
        -----------------------------------------------------------
        ```

    -   **예상 결과**

        ```sql
        # INTERSECT
        SELECT /*+ set bucket count (256) hash bucket count (512) */ i1 FROM t1 INTERSECT SELECT i1 FROM t2;
        ------------------------------------------------------------
        PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: 236.82 )
         VIEW ( ACCESS: 0, COST: 236.16 )
          SET-INTERSECT ( ITEM_SIZE: 24, ITEM_COUNT: 0, BUCKET_COUNT: 256, ACCESS: 0, COST: 236.16 )
           PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: 118.08 )
            SCAN ( TABLE: SYS.T1, FULL SCAN, ACCESS: 0, COST: 116.76 )
           PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: 118.08 )
            SCAN ( TABLE: SYS.T2, FULL SCAN, ACCESS: 0, COST: 116.76 )
        ------------------------------------------------------------
        
        # MINUS
        SELECT /*+ set bucket count (256) hash bucket count (512) */ i1 FROM t1 MINUS SELECT i1 FROM t2;
        ------------------------------------------------------------
        PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: BLOCKED )
         VIEW ( ACCESS: 0, COST: BLOCKED )
          SET-DIFFERENCE ( ITEM_SIZE: BLOCKED, ITEM_COUNT: 0, BUCKET_COUNT: 256, ACCESS: 0, COST: BLOCKED )
           PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: BLOCKED )
            SCAN ( TABLE: SYS.T1, FULL SCAN, ACCESS: 0, COST: BLOCKED )
           PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 4, COST: BLOCKED )
            SCAN ( TABLE: SYS.T2, FULL SCAN, ACCESS: 0, COST: BLOCKED )
        ------------------------------------------------------------
        ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49451 저장 프로시저 바디에서 사용한 SQL 문의 LOOP 절에 호스트 변수 또는 지역 변수 사용 시 ERR-31248 : Mismatched bind column count 에러가 발생합니다.

-   **module** : qp-psm-trigger-execute

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 저장 프로시저 바디에서 사용한 SQL 문의 LOOP 절에 호스트 변수 또는 지역 변수 사용 시 ERR-31248 : Mismatched bind column count 에러가 발생하는 문제를 수정합니다.
    
-   **재현 방법**

    -   **재현 절차**

        ```sql
        VAR VAR1 INTEGER;
        VAR VAR2 INTEGER;
        EXEC :VAR2 := 1;
        
        BEGIN
          SELECT 1 INTO :VAR1 FROM DUAL LOOP :VAR2;
        END;
        /
        
        PRINT VAR;
        ```

    -   **수행 결과**

        ```sql
        iSQL> VAR VAR1 INTEGER;
        iSQL> VAR VAR2 INTEGER;
        iSQL> EXEC :VAR2 := 1;
        Execute success.
        iSQL>
        iSQL> BEGIN
            2   SELECT 1 INTO :VAR1 FROM DUAL LOOP :VAR2;
            3 END;
            4 /
        [ERR-31248 : Mismatched bind column count
        at "SYS.ANONYMOUS_BLOCK", line 2]
        iSQL>
        iSQL> PRINT VAR;
        [ HOST VARIABLE ]
        -------------------------------------------------------
        NAME                 TYPE                 VALUE
        -------------------------------------------------------
        VAR1                 INTEGER
        VAR2                 INTEGER              1
        ```

    -   **예상 결과**

        ```sql
        iSQL> VAR VAR1 INTEGER;
        iSQL> VAR VAR2 INTEGER;
        iSQL> EXEC :VAR2 := 1;
        Execute success.
        iSQL>
        iSQL> BEGIN
            2   SELECT 1 INTO :VAR1 FROM DUAL LOOP :VAR2;
            3 END;
            4 /
        Execute success.
        iSQL>
        iSQL> PRINT VAR;
        [ HOST VARIABLE ]
        -------------------------------------------------------
        NAME                 TYPE                 VALUE
        -------------------------------------------------------
        VAR1                 INTEGER              1
        VAR2                 INTEGER              1
        ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49505 복잡도가 높은 SQL문 수행 시 PREPARE\_STMT\_MEMORY\_MAXIMUM 초과로 SQL Plan Cache에 실행 계획을 등록하지 못한 경우 예외 처리를 추가합니다.

-   **module** : qp

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : 복잡도가 높은 SQL문 수행 시 PREPARE\_STMT\_MEMORY\_MAXIMUM 초과로 SQL Plan Cache에 실행 계획을 등록하지 못한 경우 Altibase 서버가 비정상 종료하는 현상을 수정합니다.
    
-   **재현 방법**

    -   **재현 절차**

        ```sql
        DROP TABLE BUG_49505;
         
        CREATE TABLE BUG_49505 
        ( 
          I1  INTEGER, 
          I2  INTEGER,
          I3  INTEGER, 
          I4  INTEGER,
          I5  INTEGER,
          I6  INTEGER, 
          I7  INTEGER, 
          I8  INTEGER,
          I9  INTEGER, 
          I10 INTEGER, 
          I11 INTEGER, 
          I12 GEOMETRY
        )
        PARTITION BY RANGE( I1 )
        ( 
          PARTITION P1 VALUES LESS THAN ( 10 ), 
          PARTITION P2 VALUES LESS THAN ( 20 ), 
          PARTITION P3 VALUES LESS THAN ( 30 ), 
          PARTITION P4 VALUES DEFAULT 
        ) ;
         
        ALTER TABLE BUG_49505 MERGE PARTITIONS P2, P3 INTO PARTITION P3 ;
        ALTER TABLE BUG_49505 DROP PARTITION P1;
         
        SELECT COUNT(*) FROM ( SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 );
        ```

    -   **수행 결과**

            Altibase 서버 비정상 종료 

    -   **예상 결과**

            동일 쿼리 첫 번째 수행 시 
            ERR-01067 : The memory size allocated for the statement has exceeded the maximum limit ( Name : Query_Prepare, Wanted Memory Size : 209719025, Max size : 209715200 ).
            
            동일 쿼리 재 수행 시 
            COUNT(*)             
            -----------------------
            0                    
            1 row selected.

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49556 매개변수 값을 설정하지 않고 ParameterMetaData 메소드로 매개변수 정보를 조회하면 NullPointerException 에러가 발생합니다.

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 매개변수 값을 설정하지 않아도 PreparedStatement.getParameterMetaData()가 동작하도록 수정합니다. 
    
    Spring JDBC 버전에 따라 이 에러가 발생하는 경우 spring.jdbc.getParameterType.ignore 값을 true로 설정해야 합니다. Altibase 6.5.1.9.2 이상 Altibase JDBC Driver를 사용하면 spring.jdbc.getParameterType.ignore=true를 설정하지 않아도 됩니다.
    
    이 버그를 적용하려면 Altibase JDBC 드라이버를 패치해야 합니다. 
    
-   **재현 방법**

    -   **재현 절차**

            CREATE TABLE t1 (c1 INT, c2 VARCHAR(10));
            
            Connection sConn = getConnection("20300");
            PreparedStatement sStmt = sConn.prepareStatement("INSERT INTO t1 VALUES (?, ?)");
            ParameterMetaData sMeta = sStmt.getParameterMetaData();
            System.out.println("parameter type===>" + sMeta.getParameterType(2));

    -   **수행 결과**

            Exception in thread "main" java.lang.NullPointerException
            	at Altibase.jdbc.driver.AltibaseParameterMetaData.getParameterType(AltibaseParameterMetaData.java:66)
            	at ParameterBindingTest.doTest(ParameterBindingTest.java:16)
            	at ParameterBindingTest.main(ParameterBindingTest.java:8)

    -   **예상 결과**

            정상적으로 파라메터 메타 데이터 조회. 
            Spring JDBC 경우, spring.jdbc.getParameterType.ignore값을 true로 설정하지 않아도 됨.

-   **Workaround**

        Spring JDBC 경우, spring.jdbc.getParameterType.ignore 값을 true로 설정

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49571 Windows 환경에서 Altibase 서버에서 의도적으로 Altibase 서버를 비정상 종료시킬 때 콜스택이 출력되지 않는 현상을 개선합니다.

-   **module** : id

-   **Category** : Functional Error

-   **재현 빈도** : Rare

-   **설명** : Windows 환경에서 Altibase 서버에서 의도적으로 Altibase 서버를 비정상 종료시킬 때 콜스택이 출력되지 않는 현상을 개선합니다.
    
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

### BUG-49580 메모리 테이블 또는 휘발성 메모리 테이블에 LOB 데이터 입력 시 과도한 메모리 사용을 개선합니다.

-   **module** : sm-mem-resource

-   **Category** : Efficiency

-   **재현 빈도** : Always

-   **설명** : 메모리 테이블 또는 휘발성 메모리 테이블에 LOB 데이터 입력 시 LOB 정보를 관리하는 런타임 객체에서 메모리를 과도하게 사용하는 현상을 개선합니다.
    
    - 이 버그 현상 예시

      4G 크기의 LOB 데이터 입력 시 메모리 196G를 사용합니다. INSERT 진행 중 메모리를 과도하게 사용하다가 트랜잭션 종료 후 반납합니다.

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

### BUG-49614 THREAD\_REUSE\_ENABLE=0 설정하고 Altibase 서버 운영 시 V\$MEMSTAT에 부정확한 메모리 통계 정보가 출력되는 현상을 개선합니다.

-   **module** : id

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : Altibase 서버 프로퍼티 THREAD\_REUSE\_ENABLE=0 설정하여 쓰레드 재사용 기능을 사용하지 않을 때 V\$MEMSTAT의 ALLOC\_SIZE에 부정확한 메모리 통계 정보가 출력되는 현상을 개선합니다.
    
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

### BUG-49642 테이블스페이스 삭제와 생성이 동시에 수행 중 Altibase 서버가 비정상 종료한 경우 재시작 복구(Restart Recovery)가 실패할 수 있습니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : 테이블스페이스 삭제와 생성이 동시에 수행 중 Altibase 서버가 비정상 종료한 경우 Altibase 서버 구동 시 재시작 복구(Restart
    Recovery)가 실패하는 현상을 수정합니다.
    
-   **재현 방법**

    -   **재현 절차**

            CREATE MEMORY TABLESPACE USER_MEMORY_TBS2 SIZE 8M AUTOEXTEND ON;
            DROP TABLESPACE USER_MEMORY_TBS2 INCLUDING CONTENTS AND DATAFILES;
            CREATE MEMORY TABLESPACE USER_MEMORY_TBS1 SIZE 8M AUTOEXTEND ON;

    -   **수행 결과**

            CREATE MEMORY TABLESPACE USER_MEMORY_TBS2 SIZE 8M AUTOEXTEND ON;
            Create success.
            
            DROP TABLESPACE USER_MEMORY_TBS2 INCLUDING CONTENTS AND DATAFILES;
            [ERR-91015 : Communication failure.]
            
            CREATE MEMORY TABLESPACE USER_MEMORY_TBS1 SIZE 8M AUTOEXTEND ON;
            [ERR-91015 : Communication failure.]

    -   **예상 결과**

            CREATE MEMORY TABLESPACE USER_MEMORY_TBS2 SIZE 8M AUTOEXTEND ON;
            Create success.
            
            DROP TABLESPACE USER_MEMORY_TBS2 INCLUDING CONTENTS AND DATAFILES;
            Drop success.
            
            CREATE MEMORY TABLESPACE USER_MEMORY_TBS1 SIZE 8M AUTOEXTEND ON;
            Create success.

-   **Workaround**

        동시에 테이블스페이스 생성/삭제를 수행하지 않는다.

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49643 LOB 칼럼을 포함한 테이블에 BEFORE UPDATE 트리거 수행 시 예외 처리를 추가합니다.

-   **module** : qp-psm-trigger-execute

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : LOB 칼럼을 포함한 테이블에 BEFORE UPDATE 트리거 수행 시 Altibase 서버가 비정상 종료하는 현상을 수정하고 BEFORE UPDATE 트리거에 LOB 컬럼 관련한 제약 사항을 추가합니다.
    
    `LOB 칼럼이 있는 테이블은 'BEFORE UPDATE ... FOR EACH ROW' 구문으로 트리거를 생성할 수 있으나, 트리거의 동작을 유발하는 DML 문이 실행될 때 오류가 발생한다.`
    
    위 제약 사항은 [Altibase 7.1 SQL Reference](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/SQL%20Reference.md#create-trigger) 매뉴얼을 참고하시기 바랍니다.
    
-   **재현 방법**

    -   **재현 절차**

        ```sql
        DROP TABLE T1;
        DROP TABLE T2;
         
        CREATE TABLE T1( I1 INTEGER, I3 CLOB ) ;
        CREATE TABLE T2( I1 INTEGER, I2 VARCHAR(10) );
         
        CREATE OR REPLACE TRIGGER TRIG1 
        BEFORE 
        UPDATE ON T1  
        REFERENCING NEW AS NEW_ROW OLD AS OLD_ROW 
        FOR EACH ROW 
        BEGIN :NEW_ROW.I1 := 100; 
        INSERT INTO T2 VALUES( :OLD_ROW.I1, 'OLD' ); 
        INSERT INTO T2 VALUES( :NEW_ROW.I1, 'NEW' ); 
        END;
        /
         
        INSERT INTO T1 SELECT LEVEL, LEVEL FROM DUAL CONNECT BY LEVEL <= 1;
        UPDATE T1 SET I1=I1+1;
        ```

    -   **수행 결과**

        ```sql
        ERR-91015 : Communication failure. 
        ```

    -   **예상 결과**

        ```sql
        ERR-3112F : Unsupported data type for parameter, RETURN, or local variable. LOB columns are not supported.
        ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49670 SQL Plan cache에 등록된 SQL 문 수행 중 Hard Parsing을 다시 진행할 때 Altibase 서버가 비정상 종료할 수 있습니다.

-   **module** : qp

-   **Category** : Fatal

-   **재현 빈도** : Unknown

-   **설명** : SQL Plan Cache에 등록된 SQL 문 수행 중 바인드 변수 변경 등으로 Hard Parsing을 다시 진행할 때 Check-In PCO 과정에서 메모리 동시성 오류로 Altibase 서버가 비정상 종료하는 현상을 수정합니다.
    
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

### BUG-49681 디스크 테이블스페이스에 접근하는 트랜잭션 처리 중 버퍼 풀(Buffer Pool) 부족으로 버퍼 교체 발생 시 동시성 문제로 Altibase 서버가 비정상 종료할 수 있습니다.

-   **module** : sm-disk-page

-   **Category** : Assert

-   **재현 빈도** : Rare

-   **설명** :

    디스크 테이블스페이스에 접근하는 트랜잭션 처리 중 버퍼 풀(Buffer Pool) 부족으로 버퍼 교체 발생 시 동시성 문제로 Altibase 서버가 비정상 종료하는 현상을 수정합니다.
    
    이 버그로 Altibase 서버가 비정상 종료하는 경우 altibase\_error.log에 아래와 같은 형태의 로그를 출력합니다.

    ```bash
    BCB Info..
    mID 7922
    mState 2
    mFrame 7fc8d69a4000
    mSpaceID 6
    ...중략...
    
    IDE_ASSERT( 0 ), [sdbBufferPool.cpp:852], errno=[16]
    errno=[16]
    
    [ASSERT] ERROR LINE => [sdbBufferPool.cpp:852]
    ERR-0109e(errno=16) Internal server error.
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

### BUG-49682 함수 기반 인덱스(function-based index)에 인덱스 키와 다른 데이터 타입의 데이터가 입력되는 경우 예외 처리를 변경합니다.

-   **module** : qp-non\_select

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : 함수 기반 인덱스(function-based index)에 인덱스 키와 다른 데이터 타입의 데이터가 입력되는 경우 Altibase 서버가 비정상 종료할 수 있습니다. 에러 메시지를 반환하도록 예외 처리를 변경합니다.
    
-   **재현 방법**

    -   **재현 절차**

        ```sql
        DROP TABLE T3;
        CREATE TABLE T3( I1 INTEGER, I2 VARCHAR(10) ) TABLESPACE SYS_TBS_DISK_DATA;
        CREATE INDEX T3_IDX11 ON T3( I1+1, I2+1 ) ;
        ALTER SESSION SET ARITHMETIC_OPERATION_MODE = 0;
        INSERT INTO T3 VALUES ( 5, 3 );
        ```
        
    -   **수행 결과**
    
            [ERR-91015 : Communication failure.]
    
    -   **예상 결과**
    
        ```sql
        iSQL> INSERT INTO T3 VALUES ( 5, 3 );
        [ERR-314AD : An error occurred while applying a value with an unexpected data type to the function-based index.]
        ```
    
-   **Workaround**

        ALTER SESSION SET ARITHMETIC_OPERATION_MODE = 1;

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code
        
        에러 메시지가 추가되었습니다.
        
        ```
        0x314AD ( 201901) qpERR_ABORT_QMC_INVALID_FUNCTION_BASED_INDEX An error occurred while applying a value with an unexpected data type to the function-based index. 
        # *Cause: The specified value does not match the data type of the function-based index column.
        # *Action: Rebuild the function-based index and retry.
        ```
        
        

### BUG-49706 iLoader in 성능 개선을 위해 CSV 파서를 최적화합니다.

-   **module** : ux-iloader

-   **Category** : Efficiency

-   **재현 빈도** : Always

-   **설명** : iLoader in 성능 개선을 위해 불필요한 memcpy 제거 및 CSV 파서를 최적화합니다.
    
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

### BUG-49708 ALTER TABLE 수행으로 디스크 인덱스를 재구성이 해야 할 때 인덱스 활성화 상태를 확인하는 과정을 추가합니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : ALTER TABLE 수행 시 비활성화 상태의 인덱스가 있으면 Altibase 서버가 비정상 종료하는 현상을 수정합니다. ALTER TABLE \~
    ADD COLUMN처럼 내부적으로 테이블의 인덱스를 재구성해야 할 때 이 현상이 발생합니다. 
    
    이 버그는 디스크 테이블에서만 발생합니다.

-   **재현 방법**

    -   **재현 절차**

        ```sql
        DROP TABLE T1;
        CREATE TABLE T1 ( I1 INTEGER, I2 INTEGER, I3 INTEGER ) TABLESPACE SYS_TBS_DISK_DATA;
        ALTER TABLE T1 ALL INDEX DISABLE;
        CREATE INDEX IDX5 ON T1(I2, I3);
        ALTER TABLE T1 ADD COLUMN ( C3 VARCHAR(10) FIXED, C4 VARCHAR(10) VARIABLE );
        ```

    -   **수행 결과**

        ```sql
        ERR-91015 : Communication failure.
        ```

    -   **예상 결과**

        ```sql
        Alter success.
        ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49718 비활성화 상태의 인덱스에 인덱스 통계 정보를 설정할 때 예외 처리를 추가합니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : 비활성화 상태의 인덱스에 인덱스 통계 정보를 설정(SET\_INDEX\_STATS)하면 Altibase 서버가 비정상 종료하는 현상을
    수정합니다. 비활성화 상태의 인덱스 경우 인덱스 통계 정보 설정을 수행해도 무시하도록 예외 처리를 추가합니다.
    
-   **재현 방법**

    -   **재현 절차**

        ```sql
        DROP TABLE T1;
        CREATE TABLE T1 (I1 INTEGER);
        ALTER TABLE T1 ALL INDEX DISABLE;
        CREATE INDEX T1_IDX ON T1(I1);
        EXEC SET_INDEX_STATS('SYS', 'T1_IDX', NULL, NULL, 30, NULL, NULL, NULL, TRUE);
        ```
        
    -   **수행 결과**
    
            [ERR-91015 : Communication failure.]
    
    -   **예상 결과**
    
            Execute success.
    
-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49725 테이블 잠금 획득 실패로 이중화 SYNC 동작이 실패한 경우 이중화 송신자 측 altibase\_rp.log에 ERR-61152(errno=16) Replication synchronization failed. Check whether the index on the remote server is consistent. 에러가 발생합니다.

-   **module** : rp

-   **Category** : Message Error

-   **재현 빈도** : Always

-   **설명** : 테이블 잠금 획득 실패로 이중화 SYNC 동작이 실패한 경우 이중화 송신자 측 altibase\_rp.log에 ERR-61152(errno=16) Replication synchronization failed. Check whether the index on the remote server is consistent. 에러가 발생하는 현상을 수정합니다.
    
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

### BUG-49728 디스크 인덱스 키 삽입 과정에서 인덱스 노드 공간 활용을 위해 인덱스 구조를 변경하고 인덱스 키 삽입 위치 계산 과정에서 Altibase 서버가 비정상 종료합니다.

-   **module** : sm-disk-index

-   **Category** : Fatal

-   **재현 빈도** : Rare

-   **설명** : 디스크 인덱스 키 삽입 과정에서 인덱스 노드 공간 활용을 위해 인덱스 구조를 변경하고 인덱스 키 삽입 위치 계산 과정에서
    Altibase 서버가 비정상 종료하는 현상을 수정합니다.
    
    이 버그로 Altibase 서버 비정상 종료 현상 발생 시 altibase\_error.log 에 아래와 같은 로그가 발생합니다.
    
    ```bash
    -sdnRuntimeHeader (disk common)
    mTableTSID                : 45
    mIndexTSID                : 47
    mMetaRID                  : 667252498528
    mTableOID                 : 99865440
    mIndexID                  : 49577
    ...중략...
    
    BEGIN-STACK [NORMAL] ============================
    Caller[1] 000000010001D7A4      => .iduStack::dumpStack(const iduSignalDef*,siginfo_t*,ucontext_t*,idBool,char*,idBool)
    Caller[2] 0000000100026FEC      => .ideLog::writeErrorTraceInternal(unsigned int,ideLogModule,unsigned int,const char*,const char*,unsigned int,const char*,char*)
    Caller[3] 0000000100026D34      => .ideLog::writeErrorTrace(const char*,idBool,const char*,unsigned int,const char*,char*)
    Caller[4] 000000010001FDAC      => .ideLogError        
    Caller[5] 00000001007AAF50      => .sdnbBTree::findTargetKeyForDupKey(sdrMtx*,sdnbHeader*,sdnbStatistic*,sdnbKeyInfo*,sdpPhyPageHdr**,short*)
    ...중략...
    
    index TSID : 47, get page ID : 0
    IDE_ASSERT( 0 ), [sdnbModule.cpp:17227], errno=[16]
    errno=[16]
    ```
    
    이 버그는 인덱스를 재구성하거나 ALTER INDEX *index\_name* AGING 수행하면 발생 확률을 낮출 수 있습니다. 문제의 인덱스는
    altibase\_error.log에서 mIndexID 으로 확인할 수 있습니다.
    
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

### BUG-49739 MERGE JOIN을 사용한 CREATE AS SELECT 문을 수행한 세션이 SESSION CLOSE로 강제 종료되지 않습니다.

-   **module** : qp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : MERGE JOIN을 사용한 CREATE AS SELECT 문을 수행한 세션이 SESSION CLOSE로 강제 종료되지 않는 현상을 수정합니다.
    
-   **재현 방법**

    -   **재현 절차**

        -   A 세션

            ```sql
            CREATE TABLE T1 AS
            SELECT LEVEL AS C1, CAST('AAAAA' AS VARCHAR(10)) AS T1_CD
              FROM DUAL CONNECT BY LEVEL <= 7335;
             CREATE TABLE T2 AS 
            SELECT LEVEL AS C1, CAST('AAAAA' AS VARCHAR(10)) AS T2_CD
              FROM DUAL CONNECT BY LEVEL <= 10000;
             CREATE TABLE T3 AS 
            SELECT /*+ USE_MERGE (B A) */ A.*, B.T2_CD
              FROM T1 A INNER JOIN T2 B ON A.T1_CD = B.T2_CD
               AND B.T2_CD = 'AAAAA';
            ```

        -   B 세션

            ```sql
            ALTER DATABASE database_name SESSION CLOSE session_id;
            ```

    -   **수행 결과**

            테이블 생성 완료 후 세션 종료. 

    -   **예상 결과**

            [ERR-01043 : The session has been closed by the server]

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49743 Altibase 서버 구동 시 리빌드되지 않은 인덱스 접근 시 Altibase 서버가 비정상 종료합니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : Altibase 서버 구동 시 리빌드되지 않은 인덱스 접근 시 Altibase 서버가 비정상 종료하는 현상을 수정합니다. 이 버그 현상은
    비공개 프로퍼티 INDEX\_REBUILD\_AT\_STARTUP 값을 0으로 설정하고 Altibase 서버 구동 후 사용자 인덱스에 접근하는 DML 수행 시
    발생합니다. 앞으로 DML 수행 시 리빌드되지 않은 인덱스에 접근하면 아래와 같은 에러 메시지가 발생하도록 수정하였습니다.
    
    `ERR-111BE : Failed to scan the index because it was not rebuilt.(Index Name :index_name)`
    
    이 에러 메시지는 새로 추가된 에러 메시지로, 자세한 내용은 Error Code 항목을 참고하세요.
    
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
        
        ```
        0x111BE (  70078) smERR_ABORT_NOT_BUILT_INDEX Failed to scan the index because it was not rebuilt. (Index Name :<0%s>) 
        # *Cause: This index was not rebuilt when the Altibase server was starting up. The value of INDEX_REBUILD_AT_STARTUP property is set to 0.
        # *Action: Rebuild this index. Or to rebuild all the indexes, delete INDEX_REBUILD_AT_STARTUP = 0 in altibase.properties and restart the Altibase server.
        ```
        
        

### BUG-49746 윈도우(분석) 함수, ORDER BY 절, GROUP BY 절을 사용한 질의문에서 디스크 임시 공간을 사용하면 결과 오류가 발생합니다.

-   **module** : qp-select

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 아래 조건을 모두 만족하는 질의문 수행 시 결과 오류가 발생합니다.
    
    - 윈도우(분석) 함수 사용
    
    - GROUP BY 절, ORDER BY 절, 윈도우(분석) 함수 사용
    
    - ORDER BY 절에 사용된 컬럼이 윈도우(분석) 함수 OVER 절에서 같은 순서로 사용
    
    - ORDER BY 절에 사용된 컬럼이 SELECT 절에서 표현식으로 사용

    - 쿼리 수행 시 디스크 임시 공간 사용

    이 버그 현상을 회피하는 방법은  Work Around 부분을 확인해주세요.

    **패치 시 주의 사항**

    결괏값 오류를 개선한 버그로, 패치 후 버그 조건에 만족하는 질의문 수행 시 결과가 달라질 수 있습니다.

-   **재현 방법**

    -   **재현 절차**

            DROP TABLE T1;
            CREATE TABLE T1 ( I1 CHAR(8), I2 FLOAT ) TABLESPACE SYS_TBS_DISK_DATA;
            INSERT INTO T1 VALUES ('20220127', 0);
            INSERT INTO T1 VALUES ('20220127', 1);
            INSERT INTO T1 VALUES ('20220127', 2);
            INSERT INTO T1 VALUES ('20220126', 10);
            INSERT INTO T1 VALUES ('20220126', 15);
            INSERT INTO T1 VALUES ('20220125', 30);
            SELECT ROW_NUMBER() OVER(ORDER BY A.I1 DESC) RNUM
                 , TO_CHAR(TO_DATE(A.I1, 'YYYYMMDD'), 'YYYY-MM-DD') AS YYYYMMDD
                 , SUM(A.I2) AS CNT
              FROM T1 A
             GROUP BY A.I
             ORDER BY A.I1 DESC;

    -   **수행 결과**

        ```sql
        RNUM                 YYYYMMDD              CNT         
        -----------------------------------------------------------
        1                    2022-01-25            3           
        2                    2022-01-25            25          
        3                    2022-01-25            30          
        3 rows selected.
        ```

    -   **예상 결과**

        ```sql
        RNUM                 YYYYMMDD              CNT         
        -----------------------------------------------------------
        1                    2022-01-27            3           
        2                    2022-01-26            25          
        3                    2022-01-25            30          
        3 rows selected.
        ```

-   **Workaround**

    이 버그 현상은 다음 2가지 방법 중 하나로 회피할 수 있습니다. 

    - TEMP_TBS_MEMORY 힌트 사용

      ```sql
      SELECT /*+ TEMP_TBS_MEMORY */ ROW_NUMBER() OVER(ORDER BY A.I1 DESC) RNUM
           , TO_CHAR(TO_DATE(A.I1, 'YYYYMMDD'), 'YYYY-MM-DD') AS YYYYMMDD
           , SUM(A.I2) AS CNT
        FROM T1 A
       GROUP BY A.I
       ORDER BY A.I1 DESC;
      ```

    - 비공개 프로퍼티 __OPTIMIZER_ORDER_BY_ELIMINATION_ENABLE 변경

      Altibase 6.5.1 이상에서 사용할 수 있는 방법입니다. SQL 문 변경 없이 프로퍼티 변경만으로 회피할 수 있습니다. 

      이 방법은 버그 조건에 만족하는 SQL 문 뿐 아니라 프로퍼티 영향을 받는 다른 SQL 문의 실행 계획이 변경으로 SQL 문 수행 성능이 저하될 수 있습니다. 

      ```sql
      ALTER SYSTEM SET __OPTIMIZER_ORDER_BY_ELIMINATION_ENABLE = 0 ; 
      ```

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49756 INSERT 문 values 절에 NOT NULL 제약 조건을 가진 LOB 컬럼에 EMPTY\_CLOB() 또는 EMPTY\_BLOB() 함수를 사용하면 ERR-31074 : Unable to insert (or update) NULL into NOT NULL column. 에러가 발생합니다.

-   **module** : qp-dml-execute

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : INSERT 문 values 절에 NOT NULL 제약 조건을 가진 LOB 컬럼에 EMPTY\_CLOB() 또는 EMPTY\_BLOB() 함수를 사용하면 ERR-31074 : Unable to insert (or update) NULL into NOT NULL column. 에러가 발생하는 현상을 수정합니다.
    
-   **재현 방법**

    -   **재현 절차**

        ```sql
        CREATE TABLE t1(c1 CLOB NOT NULL);
        INSERT INTO t1 VALUES(EMPTY_CLOB());
        ```

    -   **수행 결과**

        ```sql
        [ERR-31074 : Unable to insert (or update) NULL into NOT NULL column. : C1]
        ```

    -   **예상 결과**

            1 row inserted.

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49769 altibase.properties.sample 파일에서 지원하지 않는 REPLICATION\_NET\_CONN\_IP\_STACK 프로퍼티를 삭제합니다.

-   **module** : rp

-   **Category** : Maintainability

-   **재현 빈도** : Always

-   **설명** :

    altibase.properties.sample 파일에서 지원하지 않아 주석 처리된 REPLICATION\_NET\_CONN\_IP\_STACK 프로퍼티를 삭제합니다. 

    삭제된 부분은 아래와 같습니다.

    ```bash
    # Replication receiver IP stack configuration
    # If this property is not set, it will be the same as the value of
    # NET_CONN_IP_STACK. If you want to set the IP stack configuration
    # differently for replication, you need to set this property.
    # - REPLICATION_NET_CONN_IP_STACK    = 0 # 0: IPv4 setack only
                                             # 1: Dual stack
                                             # 2: IPv6 stack only
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
|    6.5.1.9.2     |          6.3.1          |    8.1.1     |        7.1.3        |            7.4.5             |

> Altibase 6.5.1 패치 버전 별 히스토리는 [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_6.5.1/Altibase_6_5_1_Version_Histories.md) 에서 확인할 수 있다.

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
