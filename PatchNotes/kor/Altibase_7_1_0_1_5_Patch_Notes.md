<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Altibase 7.1.0.1.5 Patch Notes](#altibase-71015-patch-notes)
  - [New Features](#new-features)
    - [BUG-46475  HP-UX, AIX용 JDBC adapter를 지원 해야 합니다.](#bug-46475-hp-ux-aix%EC%9A%A9-jdbc-adapter%EB%A5%BC-%EC%A7%80%EC%9B%90-%ED%95%B4%EC%95%BC-%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-46216  updatable join view 에서 key reserved 체크 기능 추가](#bug-46216--updatable-join-view-%EC%97%90%EC%84%9C-key-reserved-%EC%B2%B4%ED%81%AC-%EA%B8%B0%EB%8A%A5-%EC%B6%94%EA%B0%80)
    - [BUG-46425  JDBC Driver 에 sharding 기능 추가](#bug-46425-jdbc-driver-%EC%97%90-sharding-%EA%B8%B0%EB%8A%A5-%EC%B6%94%EA%B0%80)
    - [BUG-46352  OpenSSL 로딩시 버전을 출력해 주어야 합니다.](#bug-46352-openssl-%EB%A1%9C%EB%94%A9%EC%8B%9C-%EB%B2%84%EC%A0%84%EC%9D%84-%EC%B6%9C%EB%A0%A5%ED%95%B4-%EC%A3%BC%EC%96%B4%EC%95%BC-%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-46411  LOB Fetch 성능향상을 위해, LOB\_CACHE\_THRESHOLD 프로퍼티의 MAX값 변경](#bug-46411-lob-fetch-%EC%84%B1%EB%8A%A5%ED%96%A5%EC%83%81%EC%9D%84-%EC%9C%84%ED%95%B4-lob%5C_cache%5C_threshold-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0%EC%9D%98-max%EA%B0%92-%EB%B3%80%EA%B2%BD)
    - [BUG-46443  JDBC 성능 향상을 위해, 일반 바인드 파라미터 전송에 list protocol을 적용](#bug-46443-jdbc-%EC%84%B1%EB%8A%A5-%ED%96%A5%EC%83%81%EC%9D%84-%EC%9C%84%ED%95%B4-%EC%9D%BC%EB%B0%98-%EB%B0%94%EC%9D%B8%EB%93%9C-%ED%8C%8C%EB%9D%BC%EB%AF%B8%ED%84%B0-%EC%A0%84%EC%86%A1%EC%97%90-list-protocol%EC%9D%84-%EC%A0%81%EC%9A%A9)
    - [BUG-46465  JDBC 성능 향상을 위해 CmBufferWriter.encodeString 메서드를 refactoring해야 합니다.](#bug-46465-jdbc-%EC%84%B1%EB%8A%A5-%ED%96%A5%EC%83%81%EC%9D%84-%EC%9C%84%ED%95%B4-cmbufferwriterencodestring-%EB%A9%94%EC%84%9C%EB%93%9C%EB%A5%BC-refactoring%ED%95%B4%EC%95%BC-%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-46309  PSM안에서 dequeue 호출시 into 절을 누락하면 서버가 비정상 종료할 수 있습니다.](#bug-46309-psm%EC%95%88%EC%97%90%EC%84%9C-dequeue-%ED%98%B8%EC%B6%9C%EC%8B%9C-into-%EC%A0%88%EC%9D%84-%EB%88%84%EB%9D%BD%ED%95%98%EB%A9%B4-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-46392  order by 절의 표현식이 target 절에서 중복으로 참조되는 경우 비정상 종료가 발생할 수 있습니다.](#bug-46392-order-by-%EC%A0%88%EC%9D%98-%ED%91%9C%ED%98%84%EC%8B%9D%EC%9D%B4-target-%EC%A0%88%EC%97%90%EC%84%9C-%EC%A4%91%EB%B3%B5%EC%9C%BC%EB%A1%9C-%EC%B0%B8%EC%A1%B0%EB%90%98%EB%8A%94-%EA%B2%BD%EC%9A%B0-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-46416  view가 function, view에서 동시에 참조되는 경우 무한 대기 상태에 빠질 수 있습니다.](#bug-46416-view%EA%B0%80-function-view%EC%97%90%EC%84%9C-%EB%8F%99%EC%8B%9C%EC%97%90-%EC%B0%B8%EC%A1%B0%EB%90%98%EB%8A%94-%EA%B2%BD%EC%9A%B0-%EB%AC%B4%ED%95%9C-%EB%8C%80%EA%B8%B0-%EC%83%81%ED%83%9C%EC%97%90-%EB%B9%A0%EC%A7%88-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-46424  디스크 템프 테이블 생성시 상위 플랜 노드에서 필요한 값이 저장되지 않는 경우가 있습니다.](#bug-46424-%EB%94%94%EC%8A%A4%ED%81%AC-%ED%85%9C%ED%94%84-%ED%85%8C%EC%9D%B4%EB%B8%94-%EC%83%9D%EC%84%B1%EC%8B%9C-%EC%83%81%EC%9C%84-%ED%94%8C%EB%9E%9C-%EB%85%B8%EB%93%9C%EC%97%90%EC%84%9C-%ED%95%84%EC%9A%94%ED%95%9C-%EA%B0%92%EC%9D%B4-%EC%A0%80%EC%9E%A5%EB%90%98%EC%A7%80-%EC%95%8A%EB%8A%94-%EA%B2%BD%EC%9A%B0%EA%B0%80-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-46183  DEQUEUE의 WAIT TIME이 1초 미만인 경우, 설정한 시간만큼 대기하지 않는 문제가 있습니다.](#bug-46183-dequeue%EC%9D%98-wait-time%EC%9D%B4-1%EC%B4%88-%EB%AF%B8%EB%A7%8C%EC%9D%B8-%EA%B2%BD%EC%9A%B0-%EC%84%A4%EC%A0%95%ED%95%9C-%EC%8B%9C%EA%B0%84%EB%A7%8C%ED%81%BC-%EB%8C%80%EA%B8%B0%ED%95%98%EC%A7%80-%EC%95%8A%EB%8A%94-%EB%AC%B8%EC%A0%9C%EA%B0%80-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-46217  v\$table 에서 성능뷰만 조회되어야 합니다.](#bug-46217-vtable-%EC%97%90%EC%84%9C-%EC%84%B1%EB%8A%A5%EB%B7%B0%EB%A7%8C-%EC%A1%B0%ED%9A%8C%EB%90%98%EC%96%B4%EC%95%BC-%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-46266  V$LFG에서 삭제된 logfile 번호 컬럼(FIRST\_DELETED\_LOGFILE, LAST\_DELETED\_LOGFILE) 값이 잘못 출력됩니다.](#bug-46266--vlfg%EC%97%90%EC%84%9C-%EC%82%AD%EC%A0%9C%EB%90%9C-logfile-%EB%B2%88%ED%98%B8-%EC%BB%AC%EB%9F%BCfirst%5C_deleted%5C_logfile-last%5C_deleted%5C_logfile-%EA%B0%92%EC%9D%B4-%EC%9E%98%EB%AA%BB-%EC%B6%9C%EB%A0%A5%EB%90%A9%EB%8B%88%EB%8B%A4)
    - [BUG-46383  disk sort temp table 에서 잘못된 Page를 읽어서 hang이 걸리는 문제를 수정하였습니다.](#bug-46383-disk-sort-temp-table-%EC%97%90%EC%84%9C-%EC%9E%98%EB%AA%BB%EB%90%9C-page%EB%A5%BC-%EC%9D%BD%EC%96%B4%EC%84%9C-hang%EC%9D%B4-%EA%B1%B8%EB%A6%AC%EB%8A%94-%EB%AC%B8%EC%A0%9C%EB%A5%BC-%EC%88%98%EC%A0%95%ED%95%98%EC%98%80%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-46384  Disk Sort Temp Table에서 작업 완료되지 않은 page가 다른 page로 변경되어 오작동 하거나 hang이 발생하는 문제를 수정합니다.](#bug-46384-disk-sort-temp-table%EC%97%90%EC%84%9C-%EC%9E%91%EC%97%85-%EC%99%84%EB%A3%8C%EB%90%98%EC%A7%80-%EC%95%8A%EC%9D%80-page%EA%B0%80-%EB%8B%A4%EB%A5%B8-page%EB%A1%9C-%EB%B3%80%EA%B2%BD%EB%90%98%EC%96%B4-%EC%98%A4%EC%9E%91%EB%8F%99-%ED%95%98%EA%B1%B0%EB%82%98-hang%EC%9D%B4-%EB%B0%9C%EC%83%9D%ED%95%98%EB%8A%94-%EB%AC%B8%EC%A0%9C%EB%A5%BC-%EC%88%98%EC%A0%95%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-46322  disk sort temp table 중 특정 merge join에서 정상 상황임에도 비정상으로 판단하여 오류를 잘못 반환하는 문제 수정](#bug-46322-disk-sort-temp-table-%EC%A4%91-%ED%8A%B9%EC%A0%95-merge-join%EC%97%90%EC%84%9C-%EC%A0%95%EC%83%81-%EC%83%81%ED%99%A9%EC%9E%84%EC%97%90%EB%8F%84-%EB%B9%84%EC%A0%95%EC%83%81%EC%9C%BC%EB%A1%9C-%ED%8C%90%EB%8B%A8%ED%95%98%EC%97%AC-%EC%98%A4%EB%A5%98%EB%A5%BC-%EC%9E%98%EB%AA%BB-%EB%B0%98%ED%99%98%ED%95%98%EB%8A%94-%EB%AC%B8%EC%A0%9C-%EC%88%98%EC%A0%95)
    - [BUG-46410  sdcTempRow::filteringAndFetch()에서 row Ptr이 잘못 설정 될 수 있습니다.](#bug-46410-sdctemprowfilteringandfetch%EC%97%90%EC%84%9C-row-ptr%EC%9D%B4-%EC%9E%98%EB%AA%BB-%EC%84%A4%EC%A0%95-%EB%90%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-46442  파일에서 읽은 컬럼 값이 유효하지 않을 때 에러 메시지가 셋팅되지 않는 경우가 있습니다.](#bug-46442-%ED%8C%8C%EC%9D%BC%EC%97%90%EC%84%9C-%EC%9D%BD%EC%9D%80-%EC%BB%AC%EB%9F%BC-%EA%B0%92%EC%9D%B4-%EC%9C%A0%ED%9A%A8%ED%95%98%EC%A7%80-%EC%95%8A%EC%9D%84-%EB%95%8C-%EC%97%90%EB%9F%AC-%EB%A9%94%EC%8B%9C%EC%A7%80%EA%B0%80-%EC%85%8B%ED%8C%85%EB%90%98%EC%A7%80-%EC%95%8A%EB%8A%94-%EA%B2%BD%EC%9A%B0%EA%B0%80-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-46292  aexport 에서 객체를 생성할때, BIGINT 타입의 Object Id가 integer 타입으로 바인딩되어 Numeric value out of range 에러가 발생합니다.](#bug-46292-aexport-%EC%97%90%EC%84%9C-%EA%B0%9D%EC%B2%B4%EB%A5%BC-%EC%83%9D%EC%84%B1%ED%95%A0%EB%95%8C-bigint-%ED%83%80%EC%9E%85%EC%9D%98-object-id%EA%B0%80-integer-%ED%83%80%EC%9E%85%EC%9C%BC%EB%A1%9C-%EB%B0%94%EC%9D%B8%EB%94%A9%EB%90%98%EC%96%B4-numeric-value-out-of-range-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-46295  뷰 생성문 마지막 라인에 단일 행 주석이 포함될 경우, 생성된 SQL 파일이 정상적으로 실행되지 않습니다.](#bug-46295-%EB%B7%B0-%EC%83%9D%EC%84%B1%EB%AC%B8-%EB%A7%88%EC%A7%80%EB%A7%89-%EB%9D%BC%EC%9D%B8%EC%97%90-%EB%8B%A8%EC%9D%BC-%ED%96%89-%EC%A3%BC%EC%84%9D%EC%9D%B4-%ED%8F%AC%ED%95%A8%EB%90%A0-%EA%B2%BD%EC%9A%B0-%EC%83%9D%EC%84%B1%EB%90%9C-sql-%ED%8C%8C%EC%9D%BC%EC%9D%B4-%EC%A0%95%EC%83%81%EC%A0%81%EC%9C%BC%EB%A1%9C-%EC%8B%A4%ED%96%89%EB%90%98%EC%A7%80-%EC%95%8A%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-46310  receiver에서 stop중 V$REPRECEIVER\_TRANSTBL을 조회 하면 잘못된 메모리를 참조 할수 있습니다.](#bug-46310-receiver%EC%97%90%EC%84%9C-stop%EC%A4%91-vrepreceiver%5C_transtbl%EC%9D%84-%EC%A1%B0%ED%9A%8C-%ED%95%98%EB%A9%B4-%EC%9E%98%EB%AA%BB%EB%90%9C-%EB%A9%94%EB%AA%A8%EB%A6%AC%EB%A5%BC-%EC%B0%B8%EC%A1%B0-%ED%95%A0%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-46314  각 서버에서 이중화 대상 table 의 컬럼순서가 다른경우, update 수행시 이중화가 정상적으로 수행되지 않습니다.](#bug-46314-%EA%B0%81-%EC%84%9C%EB%B2%84%EC%97%90%EC%84%9C-%EC%9D%B4%EC%A4%91%ED%99%94-%EB%8C%80%EC%83%81-table-%EC%9D%98-%EC%BB%AC%EB%9F%BC%EC%88%9C%EC%84%9C%EA%B0%80-%EB%8B%A4%EB%A5%B8%EA%B2%BD%EC%9A%B0-update-%EC%88%98%ED%96%89%EC%8B%9C-%EC%9D%B4%EC%A4%91%ED%99%94%EA%B0%80-%EC%A0%95%EC%83%81%EC%A0%81%EC%9C%BC%EB%A1%9C-%EC%88%98%ED%96%89%EB%90%98%EC%A7%80-%EC%95%8A%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-46354  HBT에서 socket open 실패시 에러메시지를 출력해야 합니다.](#bug-46354-hbt%EC%97%90%EC%84%9C-socket-open-%EC%8B%A4%ED%8C%A8%EC%8B%9C-%EC%97%90%EB%9F%AC%EB%A9%94%EC%8B%9C%EC%A7%80%EB%A5%BC-%EC%B6%9C%EB%A0%A5%ED%95%B4%EC%95%BC-%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-46369  이중화 중 tablespace full이 발생했을때 SenderApply가 계속 restart 를 시도합니다.](#bug-46369-%EC%9D%B4%EC%A4%91%ED%99%94-%EC%A4%91-tablespace-full%EC%9D%B4-%EB%B0%9C%EC%83%9D%ED%96%88%EC%9D%84%EB%95%8C-senderapply%EA%B0%80-%EA%B3%84%EC%86%8D-restart-%EB%A5%BC-%EC%8B%9C%EB%8F%84%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-46385  eager replication 으로 사용시 create 순서로 start 하지 않으면 hang 이 발생 합니다.](#bug-46385-eager-replication-%EC%9C%BC%EB%A1%9C-%EC%82%AC%EC%9A%A9%EC%8B%9C-create-%EC%88%9C%EC%84%9C%EB%A1%9C-start-%ED%95%98%EC%A7%80-%EC%95%8A%EC%9C%BC%EB%A9%B4-hang-%EC%9D%B4-%EB%B0%9C%EC%83%9D-%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-46276  eager replication failback flush 상태 이전에 발생한 transaction 이 있으면 hang 이 발생 합니다.](#bug-46276-eager-replication-failback-flush-%EC%83%81%ED%83%9C-%EC%9D%B4%EC%A0%84%EC%97%90-%EB%B0%9C%EC%83%9D%ED%95%9C-transaction-%EC%9D%B4-%EC%9E%88%EC%9C%BC%EB%A9%B4-hang-%EC%9D%B4-%EB%B0%9C%EC%83%9D-%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-46393  lazy 이중화관련 테이블에만 트랜잭션이 발생하였는데 eager 이중화가 FLUSH FAILBACK 상태면 Commit 시 대기를 합니다.](#bug-46393-lazy-%EC%9D%B4%EC%A4%91%ED%99%94%EA%B4%80%EB%A0%A8-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90%EB%A7%8C-%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98%EC%9D%B4-%EB%B0%9C%EC%83%9D%ED%95%98%EC%98%80%EB%8A%94%EB%8D%B0-eager-%EC%9D%B4%EC%A4%91%ED%99%94%EA%B0%80-flush-failback-%EC%83%81%ED%83%9C%EB%A9%B4-commit-%EC%8B%9C-%EB%8C%80%EA%B8%B0%EB%A5%BC-%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-46400  클라이언트 통신 모듈 콜백 함수 리스트를 모두 초기화 해야 합니다.](#bug-46400-%ED%81%B4%EB%9D%BC%EC%9D%B4%EC%96%B8%ED%8A%B8-%ED%86%B5%EC%8B%A0-%EB%AA%A8%EB%93%88-%EC%BD%9C%EB%B0%B1-%ED%95%A8%EC%88%98-%EB%A6%AC%EC%8A%A4%ED%8A%B8%EB%A5%BC-%EB%AA%A8%EB%91%90-%EC%B4%88%EA%B8%B0%ED%99%94-%ED%95%B4%EC%95%BC-%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-46277  oraAdapter 연결후 oracle 서버가 종료되면 connection error를 skip하여 계속 connection error가 발생합니다.](#bug-46277-oraadapter-%EC%97%B0%EA%B2%B0%ED%9B%84-oracle-%EC%84%9C%EB%B2%84%EA%B0%80-%EC%A2%85%EB%A3%8C%EB%90%98%EB%A9%B4-connection-error%EB%A5%BC-skip%ED%95%98%EC%97%AC-%EA%B3%84%EC%86%8D-connection-error%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-46403  oraAdapter가 oracle의 timestamp 타입을 지원 할 수 있도록 수정 해야 합니다.](#bug-46403-oraadapter%EA%B0%80-oracle%EC%9D%98-timestamp-%ED%83%80%EC%9E%85%EC%9D%84-%EC%A7%80%EC%9B%90-%ED%95%A0-%EC%88%98-%EC%9E%88%EB%8F%84%EB%A1%9D-%EC%88%98%EC%A0%95-%ED%95%B4%EC%95%BC-%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-46448  jdbcAdapter연결 후 date 컬럼에 insert 시 마이크로 초값이 역전되서 전송됩니다.](#bug-46448-jdbcadapter%EC%97%B0%EA%B2%B0-%ED%9B%84-date-%EC%BB%AC%EB%9F%BC%EC%97%90-insert-%EC%8B%9C-%EB%A7%88%EC%9D%B4%ED%81%AC%EB%A1%9C-%EC%B4%88%EA%B0%92%EC%9D%B4-%EC%97%AD%EC%A0%84%EB%90%98%EC%84%9C-%EC%A0%84%EC%86%A1%EB%90%A9%EB%8B%88%EB%8B%A4)
    - [BUG-46455  RANGE\_USING\_HASH 를 적용한 partition table 의 split partition 수행시 데이터가 이동하지 않습니다.](#bug-46455-range%5C_using%5C_hash-%EB%A5%BC-%EC%A0%81%EC%9A%A9%ED%95%9C-partition-table-%EC%9D%98-split-partition-%EC%88%98%ED%96%89%EC%8B%9C-%EB%8D%B0%EC%9D%B4%ED%84%B0%EA%B0%80-%EC%9D%B4%EB%8F%99%ED%95%98%EC%A7%80-%EC%95%8A%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-46469 XA\_PREPARE\_REQ 로그 이름이 dump 되지 않습니다.](#bug-46469xa%5C_prepare%5C_req-%EB%A1%9C%EA%B7%B8-%EC%9D%B4%EB%A6%84%EC%9D%B4-dump-%EB%90%98%EC%A7%80-%EC%95%8A%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Altibase 7.1.0.1.5 Patch Notes
==============================

New Features
------------

### BUG-46475  HP-UX, AIX용 JDBC adapter를 지원 해야 합니다.

- **module** : rp-jdbcAdapter
- **Category** : Other
- **재현 빈도** : Always
- **증상** : Altibase 7.1 에서 HP-UX, AIX용 JDBC adapter를 지원하도록
  수정하였습니다.
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

### BUG-46216  updatable join view 에서 key reserved 체크 기능 추가

- **module** : qp-dml-execute

- **Category** : Enhancement

- **재현 빈도** : Always

- **증상** : updatable join view 에서 key reserved 체크 기능 추가. 

- **재현 방법**

  - **재현 절차**

    ```
    drop table t1;
    drop table t2;
    drop view v1;
    create table t1
    ( 
      i1 integer,
      i2 integer,
      i3 integer,
      i4 integer
    );
    create table t2
    ( 
      i1 integer,
      i2 integer,
      i3 integer,
      i4 integer
    );
    create view v1 as
    select t1.i1 a, t1.i2 b, t1.i3 c, t2.i1 d, t2.i2 e, t2.i3 f
    from t1, t2
    where t1.i1 = t2.i3;
    
    select t.table_name, c.column_name, c.is_key_preserved
    from system_.sys_users_ u, system_.sys_tables_ t, system_.sys_columns_ c
    where u.user_id = t.user_id and t.table_id = c.table_id and
    u.user_name = 'SYS' and t.table_name = 'V1'
    order by c.column_order;
    ```

  - **수행 결과**

    ```
    TABLE_NAME       : V1
    COLUMN_NAME      : A
    IS_KEY_PRESERVED : T
    
    TABLE_NAME       : V1
    COLUMN_NAME      : B
    IS_KEY_PRESERVED : T
    
    TABLE_NAME       : V1
    COLUMN_NAME      : C
    IS_KEY_PRESERVED : T
    
    TABLE_NAME       : V1
    COLUMN_NAME      : D
    IS_KEY_PRESERVED : T
    
    TABLE_NAME       : V1
    COLUMN_NAME      : E
    IS_KEY_PRESERVED : T
    
    TABLE_NAME       : V1
    COLUMN_NAME      : F
    IS_KEY_PRESERVED : T
    
    6 rows selected.
    ```

  - **예상 결과**

    ```
    select t.table_name, c.column_name, c.is_key_preserved
    from system_.sys_users_ u, system_.sys_tables_ t, system_.sys_columns_ c
    where u.user_id = t.user_id and t.table_id = c.table_id and
    u.user_name = 'SYS' and t.table_name = 'V1'
    order by c.column_order;
    
    TABLE_NAME       : V1
    COLUMN_NAME      : A
    IS_KEY_PRESERVED : F
    
    TABLE_NAME       : V1
    COLUMN_NAME      : B
    IS_KEY_PRESERVED : F
    
    TABLE_NAME       : V1
    COLUMN_NAME      : C
    IS_KEY_PRESERVED : F
    
    TABLE_NAME       : V1
    COLUMN_NAME      : D
    IS_KEY_PRESERVED : F
    
    TABLE_NAME       : V1
    COLUMN_NAME      : E
    IS_KEY_PRESERVED : F
    
    TABLE_NAME       : V1
    COLUMN_NAME      : F
    IS_KEY_PRESERVED : F
    
    6 rows selected.
    ```

- **Workaround**

- **변경사항**

  - Performance view
  - Property
  - Compile Option
  - Error Code

### BUG-46425  JDBC Driver 에 sharding 기능 추가

- **module** : mm-jdbc
- **Category** : Functionality
- **재현 빈도** : Always
- **증상** : JDBC Driver 에 sharding 기능을 추가하였습니다.
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

### BUG-46352  OpenSSL 로딩시 버전을 출력해 주어야 합니다.

-   **module** : cm

-   **Category** : Maintainability

-   **재현 빈도** : Always

-   **증상** : OpenSSL 로딩시 버전을 altibase\_boot.log에 출력하도록
    수정하였습니다.

    ex\> SSL\_version\_str  : OpenSSL 1.0.1e-fips 11 Feb 2013

          SSLeay\_version() : OpenSSL 1.0.1e-fips 11 Feb 2013

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

### BUG-46411  LOB Fetch 성능향상을 위해, LOB\_CACHE\_THRESHOLD 프로퍼티의 MAX값 변경

-   **module** : mm

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **증상** : Local 접속시 LOB Fetch 성능향상을 위해
    [LOB_CACHE_THRESHOLD](<https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_1.md#lob_cache_threshold-%EB%8B%A8%EC%9C%84-bytes>)의 MAX 값을 8192에서 524288로 조정합니다.

    > LOB\_CACHE\_THRESHOLD 값을 32768 초과해서 설정하는 경우, JDBC
    > Driver도 패치해야 합니다. 만약, 패치하지 않는 경우(기존 JDBC
    > Driver를 사용하는 경우), Buffer overflow가 발생합니다.

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

### BUG-46443  JDBC 성능 향상을 위해, 일반 바인드 파라미터 전송에 list protocol을 적용

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : JDBC 성능 향상을 위해 일반 바인드 파라미터 전송에 list protocol을 적용시켰습니다.

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

### BUG-46465  JDBC 성능 향상을 위해 CmBufferWriter.encodeString 메서드를 refactoring해야 합니다.

-   **module** : mm-jdbc

-   **Category** : Efficiency

-   **재현 빈도** : Always

-   **증상** : JDBC insert 성능 향상을 위해 내부함수를 리팩토링합니다.
    함

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

### BUG-46309  PSM안에서 dequeue 호출시 into 절을 누락하면 서버가 비정상 종료할 수 있습니다.

- **module** : qp-psm-trigger-execute

- **Category** : Fatal

- **재현 빈도** : Always

- **증상** : PSM에서 dequeue 수행시 into 절이 없는 경우에 서버가 비정상 종료하는 현상을 수정합니다.

- **재현 방법**

  - **재현 절차**

    ```
    create queue q1
    (
        c1 integer,
        c2 varchar(10),
        c3 varchar(10)
    );
    CREATE OR REPLACE PROCEDURE PROC1_ENQUEUE
    AS
    V1 INTEGER;
    BEGIN
        ENQUEUE into q1(c1, c2, c3) values(1, 'abc', '123');
    END;
    /
    CREATE OR REPLACE PROCEDURE PROC1_DEQUEUE
    AS
    V1 INTEGER;
    BEGIN
        DEQUEUE c1, c2, c3 from q1;
    END;
    /
    execute PROC1_DEQUEUE;
    ```

  - **수행 결과**

    ```
    iSQL> CREATE OR REPLACE PROCEDURE PROC1_DEQUEUE
    V1 INTEGER;
         AS
         V1 INTEGER;
         BEGIN
         DEQUEUE c1, c2, c3 from q1;
         END;
         /
    
    Create success.
    iSQL> execute PROC1_DEQUEUE;
    [ERR-91015 : Communication failure.]
    ```

  - **예상 결과**

    ```
    iSQL> CREATE OR REPLACE PROCEDURE PROC1_DEQUEUE
        2 AS
        3 V1 INTEGER;
        4 BEGIN
        5     DEQUEUE c1, c2, c3 from q1;
        6 END;
        7 /
    [ERR-3114D : A SELECT statement in a procedure or function must have an INTO clause.
    In procedure SYS.PROC1_DEQUEUE
    0005 :     DEQUEUE C1, C2, C3 from Q1;
              ^                          ^
    ]
    iSQL> execute PROC1_DEQUEUE;
    [ERR-31129 : Procedure or function not found : 
    0001 : execute PROC1_DEQUEUE
                  ^            ^
    .]
    ```

- **Workaround**

  ```
  CREATE OR REPLACE PROCEDURE PROC1_DEQUEUE
  AS
  V1 INTEGER;
  V2 VARCHAR(100);
  V3 VARCHAR(100);
  BEGIN
      DEQUEUE c1, c2, c3 into v1, v2 ,v3 from q1;
  END;
  /
  ```

- **변경사항**

  - Performance view
  - Property
  - Compile Option
  - Error Code

### BUG-46392  order by 절의 표현식이 target 절에서 중복으로 참조되는 경우 비정상 종료가 발생할 수 있습니다.

- **module** : qp-select-pvo

- **Category** : Fatal

- **재현 빈도** : Always

- **증상** : order by 절의 표현식이 target 절에서 중복으로 참조되는
  경우 재귀 호출로 인해서 스택 오버 플로우가 발생하면서 서버가 비정상
  종료할 수 있습니다.

- **재현 방법**

  - **재현 절차**

    ```
    drop table t1;
    create table t1 ( c1 int, c2 varchar(10) );
    insert into t1 values ( null, null );
    insert into t1 values ( 1, 1 );
    insert into t1 values ( 1, 11 );
    insert into t1 values ( 2, 2 );
    insert into t1 values ( 2, 22 );
    insert into t1 values ( 3, 3 );
    insert into t1 values ( 3, 33 );
    insert into t1 values ( 4, 4 );
    insert into t1 values ( 4, 44 );
    select
    substr(max(c2), 1, 3) as a1,
    decode(max(c2), '', 'null', substr(max(c2), 1, 3)) a2
    from t1
    group by c1
    order by a1;
    ```

  - **수행 결과**

    ```
    iSQL> select
    substr(max(c2), 1, 3) as a1,
    decode(max(c2), '', 'null', substr(max(c2), 1, 3)) a2
    from t1
    group by c1
    order by a1;
    [ERR-31455 : Failed to work because an internal exception occurred from an OS.[Contact Altibase's Support Center]]
    ```

  - **예상 결과**

    ```
    iSQL> select
         substr(max(c2), 1, 3) as a1,
         decode(max(c2), '', 'null', substr(max(c2), 1, 3)) a2
         from t1
         group by c1
         order by a1;
    A1          A2          
    ---------------------------
    11          11          
    22          22          
    33          33          
    44          44          
                null        
    5 rows selected.
    ```

- **Workaround**

- **변경사항**

  - Performance view
  - Property
  - Compile Option
  - Error Code

### BUG-46416  view가 function, view에서 동시에 참조되는 경우 무한 대기 상태에 빠질 수 있습니다.

- **module** : qp-psm-trigger-pvo

- **Category** : Hang

- **재현 빈도** : Always

- **증상** : 특정 조건에서 view를 재생성 하는 경우에 서버가 무한 대기
  상태에 빠지는 문제를 수정했습니다.

  무한 대기 상태에 빠지는 조건은 아래와 같습니다.

  ​1. View v1과 v2, function func1이 존재함.

  ​2. v2는 func1과 v1을 사용함.

  ​3. func1은 v1을 사용함.

  ​4. v1이 재생성 됨.

- **재현 방법**

  - **재현 절차**

    ```
    drop view v1;
    drop view v2;
    drop function func1;
    create or replace view v1 as select dummy c1 from dual;
    create or replace function func1 return integer
    as
    a varchar(1);
    begin
    select c1 into a from v1;
    return 1;
    end;
    /
    create or replace view v2 as select func1 c1 from v1;
    create or replace view v1 as select dummy c1 from dual;
    
    ```

  - **수행 결과**

    ```
    create or replace view v2 as select func1 c1 from v1; -- Create success
    create or replace view v1 as select dummy c1 from dual; -- Hang
    ```

  - **예상 결과**

    ```
    iSQL> create or replace view v2 as select func1 c1 from v1;
    Create success.
    iSQL> create or replace view v1 as select dummy c1 from dual;
    Create success.    
    ```

- **Workaround**

  ```
  create or replace view v2 as select func1 c1 from v1;
  drop view v1
  create or replace view v1 as select dummy c1 from dual;
  
  ```

- **변경사항**

  - Performance view
  - Property
  - Compile Option
  - Error Code

### BUG-46424  디스크 템프 테이블 생성시 상위 플랜 노드에서 필요한 값이 저장되지 않는 경우가 있습니다.

- **module** : qp-select-pvo

- **Category** : Functional Error

- **재현 빈도** : Always

- **증상** : 디스크 템프 테이블 생성시 상위 플랜 노드에서 필요한 값이
  저장되지 않는 경우가 있어, 이를 수정하였습니다.

- **재현 방법**

  - **재현 절차**

    ```
    drop table top_prod;
    create table top_prod
    (
    game_id       varchar(3) not null
    ,prod_ts_nm   varchar(100)
    ,prod_dtl_ts  numeric(3)
    ) tablespace sys_tbs_disk_data;
    
    insert into top_prod values (25, 25, 1);
    insert into top_prod values (255, 255, 2);
    
    select /*+ temp_tbs_disk */
           a.prod_ts_nm || ' ' || decode(a.game_id, '25', chr(to_number(a.prod_dtl_ts)+64), '255', chr(to_number(a.prod_dtl_ts)+64), '') as prod_ts_nm
             from top_prod a
     order by
           to_number(a.prod_dtl_ts);
    
    select /*+ temp_tbs_memory */
           a.prod_ts_nm || ' ' || decode(a.game_id, '25', chr(to_number(a.prod_dtl_ts)+64), '255', chr(to_number(a.prod_dtl_ts)+64), '') as prod_ts_nm
             from top_prod a
     order by
           to_number(a.prod_dtl_ts);
    
    ```

  - **수행 결과**

    ```
    iSQL> select /*+ temp_tbs_disk */
           a.prod_ts_nm || ' ' || decode(a.game_id, '25', chr(to_number(a.prod_dtl_ts)+64), '255', chr(to_number(a.prod_dtl_ts)+64), '') as prod_ts_nm
             from top_prod a
     order by
           to_number(a.prod_dtl_ts);
    PROD_TS_NM
    -----------------------------------------------------------------------------------------------------------
    25 B
    255 B
    2 rows selected.
    iSQL> select /*+ temp_tbs_memory */
           a.prod_ts_nm || ' ' || decode(a.game_id, '25', chr(to_number(a.prod_dtl_ts)+64), '255', chr(to_number(a.prod_dtl_ts)+64), '') as prod_ts_nm
             from top_prod a
     order by
           to_number(a.prod_dtl_ts);
    PROD_TS_NM
    -----------------------------------------------------------------------------------------------------------
    25 A
    255 B
    2 rows selected.
    
    ```

  - **예상 결과**

    ```
    iSQL> select /*+ temp_tbs_disk */
           a.prod_ts_nm || ' ' || decode(a.game_id, '25', chr(to_number(a.prod_dtl_ts)+64), '255', chr(to_number(a.prod_dtl_ts)+64), '') as prod_ts_nm
             from top_prod a
     order by
           to_number(a.prod_dtl_ts);
    PROD_TS_NM
    -----------------------------------------------------------------------------------------------------------
    25 A
    255 B
    2 rows selected.
    iSQL> select /*+ temp_tbs_memory */
           a.prod_ts_nm || ' ' || decode(a.game_id, '25', chr(to_number(a.prod_dtl_ts)+64), '255', chr(to_number(a.prod_dtl_ts)+64), '') as prod_ts_nm
             from top_prod a
     order by
           to_number(a.prod_dtl_ts);
    PROD_TS_NM
    -----------------------------------------------------------------------------------------------------------
    25 A
    255 B
    2 rows selected.
    
    ```

- **Workaround**

  ```
  temp_tbs_memory hint
  ```

- **변경사항**

  - Performance view
  - Property
  - Compile Option
  - Error Code

### BUG-46183  DEQUEUE의 WAIT TIME이 1초 미만인 경우, 설정한 시간만큼 대기하지 않는 문제가 있습니다.

-   **module** : mm-queue

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : DEQUEUE의 WAIT TIME이 1초 미만인 경우, 설정한 시간만큼
    대기하지 않는 문제를 수정하였습니다.

- **재현 방법**

  - **재현 절차**

        DROP QUEUE Q1;
        CREATE QUEUE Q1(16);
        SET TIMING ON;
        DEQUEUE /*+ NO_PLAN_CACHE */ MESSAGE FROM Q1 WAIT 900MSEC;

  - **수행 결과**

        iSQL> DEQUEUE /*+ NO_PLAN_CACHE */ MESSAGE FROM Q1 WAIT 900MSEC;
        MESSAGE           
        --------------------
        No rows selected.
        elapsed time : 0.00

  - **예상 결과**

        iSQL> DEQUEUE /*+ NO_PLAN_CACHE */ MESSAGE FROM Q1 WAIT 900MSEC;
        MESSAGE           
        --------------------
        No rows selected.
        elapsed time : 0.90

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-46217  v\$table 에서 성능뷰만 조회되어야 합니다.

-   **module** : ux-isql

-   **Category** : Usability

-   **재현 빈도** : Always

-   **증상** : 기존에는 [v$table](<https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_4.md#vtable>) 을 조회하면 성능 뷰 뿐만 아니라 x\$, d\$로 시작하는 뷰까지 조회되는 문제가 있었는데, 이를 수정하였습니다.

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

### BUG-46266  V$LFG에서 삭제된 logfile 번호 컬럼(FIRST\_DELETED\_LOGFILE, LAST\_DELETED\_LOGFILE) 값이 잘못 출력됩니다.

-   **module** : sm

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : V$LFG에서 삭제된 logfile 번호 컬럼 FIRST\_DELETED\_LOGFILE, LAST\_DELETED\_LOGFILE 값이 잘못 출력되던 문제를 수정하였습니다.

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

### BUG-46383  disk sort temp table 에서 잘못된 Page를 읽어서 hang이 걸리는 문제를 수정하였습니다.

- **module** : sm-disk-resource
- **Category** : Hang
- **재현 빈도** : Rare
- **증상** : disk sort temp table 에서 잘못된 Page를 읽어서 hang이
  걸리는 문제를 수정하였습니다.
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

### BUG-46384  Disk Sort Temp Table에서 작업 완료되지 않은 page가 다른 page로 변경되어 오작동 하거나 hang이 발생하는 문제를 수정합니다.

- **module** : sm-disk-resource
- **Category** : Hang
- **재현 빈도** : Rare
- **증상** : Disk Sort Temp Table에서 작업 완료되지 않은 page가 다른
  page로 변경되어 오작동 하거나 hang이 발생하는 문제를 수정합니다.
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

### BUG-46322  disk sort temp table 중 특정 merge join에서 정상 상황임에도 비정상으로 판단하여 오류를 잘못 반환하는 문제 수정

- **module** : sm-disk-resource

- **Category** : Functional Error

- **재현 빈도** : Always

- **증상** : disk sort temp table 중 특정 merge join에서 정상
  상황임에도 비정상으로 판단하여 오류를 잘못 반환하는 문제 수정합니다.

  temp table의 크기를 작게 설정하여 공간이 부족한 상황에서 발생합니다.

- **재현 방법**

  - **재현 절차**

    ```
    ALTER SYSTEM SET SORT_AREA_SIZE=1048576;
    ALTER SYSTEM SET TEMP_SORT_GROUP_RATIO=30;
    ALTER SYSTEM SET __OPTIMIZER_JOIN_DISABLE = 0;
    CREATE TABLE T1 ( I1 CHAR(30000) ) tablespace sys_tbs_disk_data;
    CREATE TABLE T2 ( I1 CHAR(30000) ) tablespace sys_tbs_disk_data;
    INSERT INTO T1 SELECT 1 FROM DUAL CONNECT BY LEVEL <= 9;
    INSERT INTO T2 SELECT 1 FROM DUAL CONNECT BY LEVEL <= 9;
    SELECT /*+USE_MERGE(T1,T2)*/ count( T1.I1 ) FROM T1 JOIN T2 ON T1.I1=T2.I1;
    ```

  - **수행 결과**

    ```
    iSQL> SELECT /*+USE_MERGE(T1,T2)*/ count( T1.I1 ) FROM T1 JOIN T2 ON T1.I1=T2.I1;
    [ERR-91015 : Communication failure.]
    ```

  - **예상 결과**

    ```
    iSQL> SELECT /*+USE_MERGE(T1,T2)*/ count( T1.I1 ) FROM T1 JOIN T2 ON T1.I1=T2.I1;
    COUNT(T1.I1)
    -----------------------
    81
    1 row selected.
    ```

- **Workaround**

- **변경사항**

  - Performance view
  - Property
  - Compile Option
  - Error Code

### BUG-46410  sdcTempRow::filteringAndFetch()에서 row Ptr이 잘못 설정 될 수 있습니다.

- **module** : sm-disk-resource

- **Category** : Fatal

- **재현 빈도** : Frequence

- **증상** : disk temp table 에서 size가 큰 row를 작은 크기의 work
  area 에서 fetch할때, 버퍼에 유지되어야 하는 페이지가 의도하지 않게
  replace될 수 있습니다.

  이 경우 잘못된 페이지에 접근하여 비정상 종료할수 있는데, 이를
  수정하였습니다.

- **재현 방법**

  - **재현 절차**

    ```
    ALTER SYSTEM SET TEMP_HASH_GROUP_RATIO=78;
    ALTER SYSTEM SET HASH_AREA_SIZE=524288;
    drop table T1;
    drop table T2;
    CREATE TABLE T1 ( I1 INTEGER, I2 VARCHAR(31000) ) tablespace sys_tbs_disk_data;
    CREATE TABLE T2 ( I1 INTEGER, I2 VARCHAR(31000) ) tablespace sys_tbs_disk_data;
    INSERT /*+APPEND*/ INTO T1 SELECT ROWNUM, rpad(mod(ROWNUM,100),30000,252)  FROM DUAL CONNECT BY LEVEL <= 1000;
    INSERT /*+APPEND*/ INTO T2 SELECT ROWNUM, rpad(mod(ROWNUM,100),30000,252) FROM DUAL CONNECT BY LEVEL <= 100;
    SELECT sum(T1.I1) FROM T1 LEFT OUTER JOIN T2 ON T1.I2 = T2.I2 group by T1.I2 ;
    ```

  - **수행 결과**

    ```
    iSQL> SELECT sum(T1.I1) FROM T1 LEFT OUTER JOIN T2 ON T1.I2 = T2.I2 group by T1.I2 ;
    [ERR-91015 : Communication failure.]
    [651]
    iSQL> SELECT sum(T1.I1) FROM T1 LEFT OUTER JOIN T2 ON T1.I2 = T2.I2 group by T1.I2 ;
    [ERR-1114D : This DML operation is not permitted.]
    ```

  - **예상 결과**

    ```
    iSQL> SELECT sum(T1.I1) FROM T1 LEFT OUTER JOIN T2 ON T1.I2 = T2.I2 group by T1.I2 ;
    SUM(T1.I1)
    -----------------------
    5180
    5330
    5390
    5250
    5000
    5500
    ... 
    5160
    5060
    5200
    5280
    100 rows selected.
    ```

- **Workaround**

  ```
  HASH_AREA_SIZE Property 와 SORT_AREA_SIZE property 를 넉넉하게 잡음
  ```

- **변경사항**

  - Performance view
  - Property
  - Compile Option
  - Error Code

### BUG-46442  파일에서 읽은 컬럼 값이 유효하지 않을 때 에러 메시지가 셋팅되지 않는 경우가 있습니다.

- **module** : ux-iloader
- **Category** : Usability
- **재현 빈도** : Always
- **증상** : 파일에서 읽은 컬럼 값이 유효하지 않을 때 에러는
  반환되지만 에러 메시지가 없는 경우가 있어, 수정하였습니다.
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

### BUG-46292  aexport 에서 객체를 생성할때, BIGINT 타입의 Object Id가 integer 타입으로 바인딩되어 Numeric value out of range 에러가 발생합니다.

-   **module** : ux-aexport

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **증상** : aexport 에서 객체를 생성할때, BIGINT 타입의 Object Id가
    integer 타입으로 바인딩되어 Numeric value out of range 에러가
    발생하는데, 이를 수정하였습니다.

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

### BUG-46295  뷰 생성문 마지막 라인에 단일 행 주석이 포함될 경우, 생성된 SQL 파일이 정상적으로 실행되지 않습니다.

-   **module** : ux-aexport

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : 뷰와 프로시저의 terminator(; 또는 ;/) 앞에 new line이
    추가됩니다.

    뷰와 프로시저는 마지막 라인에 주석을 작성할 수 있으며, 작성한 주석은
    해당 객체 생성문과 함께 그대로 메타에 기록됩니다.

    기존 aexport는 뷰나 프로시저의 DDL을 추출할 때, 이 주석의 존재
    가능성에 대한 고려 없이 문장 종결자(; 또는 ;/)를 덧붙였습니다. DDL
    마지막에 단일 행 주석이 올 시, 이 종결자가 무시되어 불완전한 문장이
    출력될 수 있습니다.

    따라서 새로운 라인에 종결자를 입력하도록 변경하였습니다.

-   **재현 방법**

    -   **재현 절차**

            import java.sql.Connection;
            import java.sql.DriverManager;
            import java.sql.SQLException;
            import java.sql.Statement;
            import java.util.Properties;
            public class Test4AltiJdbc
            {
                public static void main(String[] args) throws SQLException
                {
                    Properties props = new Properties();
                    Connection conn = null;
                    Statement stmt = null;
                    String url = "jdbc:Altibase://192.168.1.94:56794/mydb";
                    String sql = "CREATE OR REPLACE VIEW V1 AS SELECT SYSDATE d FROM dual -- e.g. 02-AUG-2018";
                    props.put("user", "sys");
                    props.put("password", "manager");
                    try
                    {
                        Class.forName("Altibase.jdbc.driver.AltibaseDriver");
                        conn = DriverManager.getConnection(url, props);
                        stmt = conn.createStatement();
                        stmt.execute(sql);
                    }
                    catch (Exception e)
                    {
                        e.printStackTrace();
                    }
                    finally
                    {
                        stmt.close();
                        conn.close();
                    }
                }
            }

    -   **수행 결과**

            daramix@rnd1:~/test/aexport$ cat ALL_CRT_VIEW_PROC.sql
            connect "SYS"/"MANAGER";
            drop view "SYS"."V1";
            CREATE OR REPLACE VIEW V1 AS SELECT SYSDATE D FROM DUAL -- e.g. 02-AUG-2018;

    -   **예상 결과**

            daramix@rnd1:~/test/aexport$ cat ALL_CRT_VIEW_PROC.sql
            connect "SYS"/"MANAGER";
            drop view "SYS"."V1";
            CREATE OR REPLACE VIEW V1 AS SELECT SYSDATE D FROM DUAL -- e.g. 02-AUG-2018
            ;

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-46310  receiver에서 stop중 V$REPRECEIVER\_TRANSTBL을 조회 하면 잘못된 메모리를 참조 할수 있습니다.

-   **module** : rp

-   **Category** : Fatal

-   **재현 빈도** : Rare

-   **증상** : receiver에서 stop하면서 할당되었던 메모리를 정리
    할때 V$REPRECEIVER\_TRANSTBL 조회 하면 잘못된 메모리를 참조하여
    문제가 발생하였습니다.

    메모리를 정리하는 위치를 Lock 구간으로 변경하여 잘못된 메모리를
    참조하지 않도록 수정하였습니다.

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

### BUG-46314  각 서버에서 이중화 대상 table 의 컬럼순서가 다른경우, update 수행시 이중화가 정상적으로 수행되지 않습니다.

-   **module** : dm

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : 각 서버에서 이중화 대상 table 의 컬럼순서가 다르더라도, update 수행시 이중화가 정상적으로 수행되도록 수정하였습니다.

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

### BUG-46354  HBT에서 socket open 실패시 에러메시지를 출력해야 합니다.

- **module** : rp-control

- **Category** : Maintainability

- **재현 빈도** : Always

- **증상** : 기존에는 socket open 실패시 내부 자원 부족 에러로
  판단하고, 장애감지로 여기지 않았습니다.

  이 경우 장애 감지 시간이 늘어나는데, 아무런 에러로그가 남지 않아,
  장애감지 시간 증가에 대한 이유를 확인하기가 어려운 문제가 있습니다.
  이에 socket open 실패시 , trc 로그에 에러메시지를 남기도록
  수정하였습니다. 또한 장애시 분석이 용이하도록 에러코드를
  추가하였습니다.

- **재현 방법**

  -   **재현 절차**

  -   **수행 결과**

  -   **예상 결과**

- **Workaround**

- **변경사항**

  - Performance view
  - Property
  - Compile Option
  - Error Code
    - 397,rpERR\_ABORT\_HBT\_DETECT\_PEER\_SERVER\_ERROR = The
      HeartBeat thread(HBT) detects peer server or network error.

       \# \*Cause:  1. Peer server is not running. 2. Network is not working.

      \# \*Action: 1. Confirm peer server is running. 2. Ensure that network is working normally.

    - 398,rpERR\_ABORT\_SEND\_TIMEOUT\_EXCEED = Timeout exceed while the replication Sender and Receiver were communicating.

       \# \*Cause : A timeout occurred while the replication Sender and Receiver were communicating.

      \# \*Action : Set a larger value for the REPLICATION\_SENDER\_SEND\_TIMEOUT property. Check the peer server or network connection.

### BUG-46369  이중화 중 tablespace full이 발생했을때 SenderApply가 계속 restart 를 시도합니다.

-   **module** : dm

-   **Category** : Other

-   **재현 빈도** : Always

-   **증상** : 이중화 중 연결이 끊어지는
    경우, REPLICATION\_SENDER\_SLEEP\_TIMEOUT 만큼 쉬고 다시 연결을
    시도하는데, tablespace가 full이 난 경우에는 해당 시간만큼 쉬지 않고
    계속 연결을 시도하는 문제가 있었습니다.

    이에 REPLICATION\_SENDER\_SLEEP\_TIMEOUT 에 설정된 시간 후에 연결을
    시도하도록 수정하였습니다.

-   **재현 방법**

    -   **재현 절차**

            이중화중 tablespace full 발생

    -   **수행 결과**

            SenderApply가 계속 restart 시도

    -   **예상 결과**

            60초 마다 시도

-   **Workaround**

        tablespace 증가

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-46385  eager replication 으로 사용시 create 순서로 start 하지 않으면 hang 이 발생 합니다.

-   **module** : dm

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : eager replication 에서 트랜잭션 대기시 참조하는 정보의
    인덱스는 이중화 create 시에 결정되고

    이중화 객체의 인덱스는 이중화 start 시에 결정됩니다.

    eager replication 에서 데이터를 보내거나 트랜잭션 대기를 할때 서로
    인덱스가 같다고 가정하고 처리 하고 있어서

    문제가 발생 하였습니다.

    이를 대기시 참조하는 정보에 이중화 객체의 인덱스 정보를 저장하여
    정확한 인덱스로 올바른 이중화 객체를 참조 할수 있도록 수정
    하였습니다.

-   **재현 방법**

    -   **재현 절차**

            create eager replication rep1;
            create eager replication rep2;
            alter replication rep2 start;
            alter replication rep1 start;
            altre replication rep1 stop;
            insert into t1 values ( ...)

    -   **수행 결과**

            insert into t1 values ( ...)HANG...

    -   **예상 결과**

            insert into t1 values ( ...)OK;

-   **Workaround**

        alter replication rep1 stop;
        alter replication rep2 stop;
        alter replication rep1 start;(create 한 순서대로 start)
        alter replication rep2 start;

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-46276  eager replication failback flush 상태 이전에 발생한 transaction 이 있으면 hang 이 발생 합니다.

- **module** : rp-control

- **Category** : Functional Error

- **재현 빈도** : Frequence

- **증상** :  flush failback 상태 이전에는 상대편 서버에 복제여부를
  확인하는 테이블에 update 를 수행하지 않습니다.

  그렇기 때문에 Flush failback 상태 이전에 시작된 transaction 이
  생성되어 DML 이 수행되고 Flush failback 상태로 변경이 되면 Commit
  시에 그 이전 DML 이 반영 여부를 확인 합니다.

  이 확인 할때 복제여부를 확인하는 테이블에 update 가 되지 않어 
  복제가 되지 않다라고 판단하고 계속 대기 하게 됩니다.

  Flush failback 상태 이전에 발생한 Transaction 에 대해서는 상대편
  서버가 어느 SN 까지 반영 되었는지 확인 하고 대기여부를 결정 하게
  수정 하였습니다.

  (Flush failback  상태 이전에 발생한 Transaction 은 parent Sender
  Thread 에서 전담해서 처리 하므로 Serialization 이 보장 됩니다.)

  flush failback  상태 이전에 복제여부를 확인하는 테이블을
  업데이트하는것은 성능한 이슈로 고려 하지 않았습니다.

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

### BUG-46393  lazy 이중화관련 테이블에만 트랜잭션이 발생하였는데 eager 이중화가 FLUSH FAILBACK 상태면 Commit 시 대기를 합니다.

-   **module** : rp

-   **Category** : Hang

-   **재현 빈도** : Always

-   **증상** : lazy 이중화와 eager 이중화가 각 다른 테이블에 생성 되어
    있고

    lazy 이중화 관련 테이블에만 트랜잭션이 발생하였는데 eager 이중화가
    flush failback 상태면 commit 시 대기를 하였습니다.

    eager 이중화가 Flush Failback 상태면 commit 시 대기를 상대편에서
    어느로그까지 처리 되었는지에 따라 대기 하고 있습니다.

    문제가 된 점은 eager 이중화에서 내가 보내도 되지 않은 로그이면
    로그정보에 대한 업데이트를 수행하지 않습니다.

    그렇기 때문에 lazy 이중화 관련 테이블에 트랜잭션이 발생시 eager
    이중화는 읽고 지나갔지만 로그 정보를 업데이트하지 않어 commit 대기시
    처리하지 못한 로그로 판단하고 대기하였습니다.

    이를 eage 이중화에서 내가 처리 하지 않는 로그도 읽었으면 로그 정보를
    업데이트 하여 lazy 이중화 관련 테이블에만 트랜잭션 발생시도 commit
    시 대기하지 않도록 수정 하였습니다.

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

### BUG-46400  클라이언트 통신 모듈 콜백 함수 리스트를 모두 초기화 해야 합니다.

-   **module** : cm

-   **Category** : Maintainability

-   **재현 빈도** : Always

-   **증상** : A7에 추가되는 프로토콜의 콜백함수를 cmpCallbackNULL
    함수로 초기화 하지 않는 문제를 수정하였습니다.

    초기화 하지 않으면 경우에 따라 segfault가 발생할 수 있는데
    cmpCallbackNULL 함수로 초기화를 하면

    "Communication module callback function does not exist." 에러가
    발생합니다.

    프로토콜이 잘못 해석되어진 경우라 일반적으로 발생할 일은 거의 없으며
    방어 차원에서 수정을 해야 합니다.

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

### BUG-46277  oraAdapter 연결후 oracle 서버가 종료되면 connection error를 skip하여 계속 connection error가 발생합니다.

- **module** : rp-oraAdapter

- **Category** : Other

- **재현 빈도** : Always

- **증상** : ORACLE\_SKIP\_ERROR가 1로 설정 되어 있을때 아래 error에
  대해서만  Skip을 하도록 하였습니다.

  ORA-00001: unique constraint () violated

  ORA-00054: resource busy and acquire with NOWAIT specified or
  timeout expired

  ORA-30006: resource busy; acquire with WAIT timeout expired

  ORA-24381: error(s) in array DML

- **재현 방법**

  - **재현 절차**

    ```
    oraAdpater 연결하여 DML중 oracle 서버가 종료
    계속 OCI library error: 3114 ORA-03114: not connected to ORACLE 발생
    ```

  - **수행 결과**

    ```
    계속 OCI library error: 3114 ORA-03114: not connected to ORACLE 발생
    ```

  - **예상 결과**

    ```
    oraAdapter restart 되어 Oracle instance #2에 접속 되어야 됨
    ```

- **Workaround**

- **변경사항**

  - Performance view
  - Property
  - Compile Option
  - Error Code

### BUG-46403  oraAdapter가 oracle의 timestamp 타입을 지원 할 수 있도록 수정 해야 합니다.

-   **module** : rp-oraAdapter

-   **Category** : Other

-   **재현 빈도** : Always

-   **증상** : oraAdapter를 통해 altibase의 date 타입을 oracle의
    timestamp 타입으로 복제가 가능 하도록 수정 하였습니다.

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

### BUG-46448  jdbcAdapter연결 후 date 컬럼에 insert 시 마이크로 초값이 역전되서 전송됩니다.

-   **module** : rp-jdbcAdapter

-   **Category** : Other

-   **재현 빈도** : Always

-   **증상** : jdbcAdapter에서 마이크로초 값을 받을때 앞에 0이 있을 경우
    생략이 되어서 값이 잘못 저장 되는 문제를 수정 하였습니다.

-   **재현 방법**

    -   **재현 절차**

            jdbcAdatepr를 연결 한 상태에서date 컬럼에 '2016-02-16 11:54:25.000008' insert

    -   **수행 결과**

            타겟 DB에 '2016-02-16 11:54:25.8' 으로 insert 됨

    -   **예상 결과**

            타겟 DB에 '2016-02-16 11:54:25.000008' 으로 insert 되어야 함

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-46455  RANGE\_USING\_HASH 를 적용한 partition table 의 split partition 수행시 데이터가 이동하지 않습니다.

- **module** : qx

- **Category** : Functional Error

- **재현 빈도** : Always

- **증상** : RANGE\_USING\_HASH 를 적용한 partition table 의 split
  partition 수행시 데이터가 이동하지 않는 현상 수정.

- **재현 방법**

  - **재현 절차**

        CREATE TABLE T1( i1 varchar(10) );
        CREATE TABLE H1( i1 varchar(10) primary key, i2 varchar(10), i3 varchar(10) )
        PARTITION BY RANGE_USING_HASH( I1 )
        (
            PARTITION p1 VALUES LESS THAN ('300'),
            PARTITION p2 VALUES LESS THAN ('700'),
            PARTITION p3 VALUES DEFAULT
        );
        INSERT INTO t1 SELECT to_char(level) FROM dual CONNECT BY level <= 3000;
        INSERT INTO H1 SELECT min(i1),'100','100' FROM t1 WHERE mod(hash(i1),1000) = '100';
        INSERT INTO H1 SELECT min(i1),'200','200' FROM t1 WHERE mod(hash(i1),1000) = '200';
        INSERT INTO H1 SELECT min(i1),'300','300' FROM t1 WHERE mod(hash(i1),1000) = '300';
        INSERT INTO H1 SELECT min(i1),'400','400' FROM t1 WHERE mod(hash(i1),1000) = '400';
        INSERT INTO H1 SELECT min(i1),'500','500' FROM t1 WHERE mod(hash(i1),1000) = '500';
        INSERT INTO H1 SELECT min(i1),'600','600' FROM t1 WHERE mod(hash(i1),1000) = '600';
        INSERT INTO H1 SELECT min(i1),'700','700' FROM t1 WHERE mod(hash(i1),1000) = '700';
        INSERT INTO H1 SELECT min(i1),'800','800' FROM t1 WHERE mod(hash(i1),1000) = '800';
        INSERT INTO H1 SELECT min(i1),'900','900' FROM t1 WHERE mod(hash(i1),1000) = '900';
        ALTER TABLE SYS.H1 SPLIT PARTITION P2 AT ('500') INTO (PARTITION P4, PARTITION P2);

  - **수행 결과**

        iSQL> SELECT * FROM H1 PARTITION (P2);
        H1.I1       H1.I2       H1.I3
        ----------------------------------------
        1856        300         300
        1692        400         400
        1927        500         500
        1998        600         600
        4 rows selected.
        iSQL> SELECT * FROM H1 PARTITION (P4);
        H1.I1       H1.I2       H1.I3
        ----------------------------------------
        No rows selected.

  - **예상 결과**

        iSQL> SELECT * FROM H1 PARTITION (P2);
        H1.I1       H1.I2       H1.I3
        ----------------------------------------
        1927        500         500
        1998        600         600
        2 rows selected.
        iSQL> SELECT * FROM H1 PARTITION (P4);
        H1.I1       H1.I2       H1.I3
        ----------------------------------------
        1856        300         300
        1692        400         400
        2 rows selected.

- **Workaround**

- **변경사항**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

### BUG-46469 XA\_PREPARE\_REQ 로그 이름이 dump 되지 않습니다.

-   **module** : sm-util

-   **Category** : Functional Error

-   **재현 빈도** : Rare

-   **증상** : dumplf 툴을 이용한 logfile dump 중 일부 로그의 로그
    타입이 나오지 않는 것을 수정함.

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

| altibase version | database binary version | meta version | cm protocol version | replication protocol version | sharding version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- | ---------------- |
| 7.1.0.1.5        | 6.5.1                   | 8.6.1        | 7.1.6               | 7.4.3                        | 2.1.0            |

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

Replication 프로토콜 버전은 변경되지 않았다.

#### Sharding Version

샤딩 버전은 변경 되지 않았다.

> 알티베이스 샤딩 프로토콜 및 메타는 상위, 하위 호환성을 보장하지
> 않는다. 즉, 샤딩 버전이 다른 경우, 재구성해야 한다. 샤딩 설정은 *[Altibase Sharding 설치와 설정](<https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Sharding.md#2altibase-sharding-%EC%84%A4%EC%B9%98%EC%99%80-%EC%84%A4%EC%A0%95>)*을 참고한다.

### 프로퍼티

#### 추가된 프로퍼티

#### 변경된 프로퍼티

* [LOB_CACHE_THRESHOLD](<https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_1.md#lob_cache_threshold-%EB%8B%A8%EC%9C%84-bytes>)

### 성능 뷰

#### 변경된 성능 뷰

* [v$table](<https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_4.md#vtable>)
