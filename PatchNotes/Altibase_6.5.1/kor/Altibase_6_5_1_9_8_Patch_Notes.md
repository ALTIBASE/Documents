# Altibase 6.5.1.9.8 Patch Notes

<br>

<br>

# **Table of Contents**

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-48520  네트워크 관련 에러메시지를 altibase_cm.log에 기록하게 설정할 수 있습니다.](#bug-48520-%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC-%EA%B4%80%EB%A0%A8-%EC%97%90%EB%9F%AC%EB%A9%94%EC%8B%9C%EC%A7%80%EB%A5%BC-altibase_cmlog%EC%97%90-%EA%B8%B0%EB%A1%9D%ED%95%98%EA%B2%8C-%EC%84%A4%EC%A0%95%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-50341  prepare시 error 발생한 query에 대해 로깅하는 기능 추가](#bug-50341-prepare%EC%8B%9C-error-%EB%B0%9C%EC%83%9D%ED%95%9C-query%EC%97%90-%EB%8C%80%ED%95%B4-%EB%A1%9C%EA%B9%85%ED%95%98%EB%8A%94-%EA%B8%B0%EB%8A%A5-%EC%B6%94%EA%B0%80)
    - [BUG-50412  Unsupported property warning 로깅시 플래그 설정이 필요합니다.](#bug-50412-unsupported-property-warning-%EB%A1%9C%EA%B9%85%EC%8B%9C-%ED%94%8C%EB%9E%98%EA%B7%B8-%EC%84%A4%EC%A0%95%EC%9D%B4-%ED%95%84%EC%9A%94%ED%95%A9%EB%8B%88%EB%8B%A4)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-40266  갱신 트랜잭션이 대기하는 상황이면 altibase_boot.log에 메시지를 출력하도록 개선합니다.](#bug-40266-%EA%B0%B1%EC%8B%A0-%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98%EC%9D%B4-%EB%8C%80%EA%B8%B0%ED%95%98%EB%8A%94-%EC%83%81%ED%99%A9%EC%9D%B4%EB%A9%B4-altibase_bootlog%EC%97%90-%EB%A9%94%EC%8B%9C%EC%A7%80%EB%A5%BC-%EC%B6%9C%EB%A0%A5%ED%95%98%EB%8F%84%EB%A1%9D-%EA%B0%9C%EC%84%A0%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-47333  외부프로시저에서 라이브러리 로딩에 실패한 다음, 실패의 원인을 해결해도 외부 프로시저 실행에 실패하는 문제가 있습니다.](#bug-47333-%EC%99%B8%EB%B6%80%ED%94%84%EB%A1%9C%EC%8B%9C%EC%A0%80%EC%97%90%EC%84%9C-%EB%9D%BC%EC%9D%B4%EB%B8%8C%EB%9F%AC%EB%A6%AC-%EB%A1%9C%EB%94%A9%EC%97%90-%EC%8B%A4%ED%8C%A8%ED%95%9C-%EB%8B%A4%EC%9D%8C-%EC%8B%A4%ED%8C%A8%EC%9D%98-%EC%9B%90%EC%9D%B8%EC%9D%84-%ED%95%B4%EA%B2%B0%ED%95%B4%EB%8F%84-%EC%99%B8%EB%B6%80-%ED%94%84%EB%A1%9C%EC%8B%9C%EC%A0%80-%EC%8B%A4%ED%96%89%EC%97%90-%EC%8B%A4%ED%8C%A8%ED%95%98%EB%8A%94-%EB%AC%B8%EC%A0%9C%EA%B0%80-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-47812  ALTER TRIGGER DDL과 DROP TRIGGER DDL에서 발생하는 동시성 문제로 비정상종료합니다.](#bug-47812-alter-trigger-ddl%EA%B3%BC-drop-trigger-ddl%EC%97%90%EC%84%9C-%EB%B0%9C%EC%83%9D%ED%95%98%EB%8A%94-%EB%8F%99%EC%8B%9C%EC%84%B1-%EB%AC%B8%EC%A0%9C%EB%A1%9C-%EB%B9%84%EC%A0%95%EC%83%81%EC%A2%85%EB%A3%8C%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-48193  group by rollup 결과값이 다른 문제를 수정합니다.](#bug-48193-group-by-rollup-%EA%B2%B0%EA%B3%BC%EA%B0%92%EC%9D%B4-%EB%8B%A4%EB%A5%B8-%EB%AC%B8%EC%A0%9C%EB%A5%BC-%EC%88%98%EC%A0%95%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-49287  원격 서버의 트랜잭션 세그먼트가 모두 사용 중인 상태에서 이중화 Receiver가 디스크 테이블에 변경 트랜잭션 반영 시 무한 대기하는 현상이 발생합니다.](#bug-49287-%EC%9B%90%EA%B2%A9-%EC%84%9C%EB%B2%84%EC%9D%98-%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98-%EC%84%B8%EA%B7%B8%EB%A8%BC%ED%8A%B8%EA%B0%80-%EB%AA%A8%EB%91%90-%EC%82%AC%EC%9A%A9-%EC%A4%91%EC%9D%B8-%EC%83%81%ED%83%9C%EC%97%90%EC%84%9C-%EC%9D%B4%EC%A4%91%ED%99%94-receiver%EA%B0%80-%EB%94%94%EC%8A%A4%ED%81%AC-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90-%EB%B3%80%EA%B2%BD-%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98-%EB%B0%98%EC%98%81-%EC%8B%9C-%EB%AC%B4%ED%95%9C-%EB%8C%80%EA%B8%B0%ED%95%98%EB%8A%94-%ED%98%84%EC%83%81%EC%9D%B4-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-49352  TRANSACTION_SEGMENT_COUNT 의 최대값을 900으로 변경합니다.](#bug-49352-transaction_segment_count-%EC%9D%98-%EC%B5%9C%EB%8C%80%EA%B0%92%EC%9D%84-900%EC%9C%BC%EB%A1%9C-%EB%B3%80%EA%B2%BD%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-49399  트랜잭션에서 실행하는 구문과 체크포인트 동작의 동시성 제어에 오류가 있어서 수정합니다.](#bug-49399-%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98%EC%97%90%EC%84%9C-%EC%8B%A4%ED%96%89%ED%95%98%EB%8A%94-%EA%B5%AC%EB%AC%B8%EA%B3%BC-%EC%B2%B4%ED%81%AC%ED%8F%AC%EC%9D%B8%ED%8A%B8-%EB%8F%99%EC%9E%91%EC%9D%98-%EB%8F%99%EC%8B%9C%EC%84%B1-%EC%A0%9C%EC%96%B4%EC%97%90-%EC%98%A4%EB%A5%98%EA%B0%80-%EC%9E%88%EC%96%B4%EC%84%9C-%EC%88%98%EC%A0%95%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50069  서버 미기동 상태에서 isql -sysdba 접속시 발생하는 [ERR-910FB : Connected to idle instance]의 메시지를 [Connected to idle instance] 메시지로 변경합니다.](#bug-50069-%EC%84%9C%EB%B2%84-%EB%AF%B8%EA%B8%B0%EB%8F%99-%EC%83%81%ED%83%9C%EC%97%90%EC%84%9C-isql--sysdba-%EC%A0%91%EC%86%8D%EC%8B%9C-%EB%B0%9C%EC%83%9D%ED%95%98%EB%8A%94-err-910fb--connected-to-idle-instance%EC%9D%98-%EB%A9%94%EC%8B%9C%EC%A7%80%EB%A5%BC-connected-to-idle-instance-%EB%A9%94%EC%8B%9C%EC%A7%80%EB%A1%9C-%EB%B3%80%EA%B2%BD%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50097  iloader -direct 옵션에 잘못된 값을 사용하는 경우에 대한 오류처리가 되어 있지 않습니다.](#bug-50097-iloader--direct-%EC%98%B5%EC%85%98%EC%97%90-%EC%9E%98%EB%AA%BB%EB%90%9C-%EA%B0%92%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94-%EA%B2%BD%EC%9A%B0%EC%97%90-%EB%8C%80%ED%95%9C-%EC%98%A4%EB%A5%98%EC%B2%98%EB%A6%AC%EA%B0%80-%EB%90%98%EC%96%B4-%EC%9E%88%EC%A7%80-%EC%95%8A%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-50187  autocommit 모드가 off인 환경에서 UTRANS TIMEOUT 발생시, 에러 로그의 Last Query가 잘못 기록됩니다.](#bug-50187-autocommit-%EB%AA%A8%EB%93%9C%EA%B0%80-off%EC%9D%B8-%ED%99%98%EA%B2%BD%EC%97%90%EC%84%9C-utrans-timeout-%EB%B0%9C%EC%83%9D%EC%8B%9C-%EC%97%90%EB%9F%AC-%EB%A1%9C%EA%B7%B8%EC%9D%98-last-query%EA%B0%80-%EC%9E%98%EB%AA%BB-%EA%B8%B0%EB%A1%9D%EB%90%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50196  NOCYLE 옵션으로 생성된 시퀀스가 ALTER SEQUENCE 구문을 수행한 후 서버를 재구동하면, CYCLE로 동작하는 문제가 있습니다.](#bug-50196-nocyle-%EC%98%B5%EC%85%98%EC%9C%BC%EB%A1%9C-%EC%83%9D%EC%84%B1%EB%90%9C-%EC%8B%9C%ED%80%80%EC%8A%A4%EA%B0%80-alter-sequence-%EA%B5%AC%EB%AC%B8%EC%9D%84-%EC%88%98%ED%96%89%ED%95%9C-%ED%9B%84-%EC%84%9C%EB%B2%84%EB%A5%BC-%EC%9E%AC%EA%B5%AC%EB%8F%99%ED%95%98%EB%A9%B4-cycle%EB%A1%9C-%EB%8F%99%EC%9E%91%ED%95%98%EB%8A%94-%EB%AC%B8%EC%A0%9C%EA%B0%80-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-50197  메모리 파티션드 테이블 생성 구문에서 LOB 테이블 스페이스 지정에 대한 검증이 미흡합니다.](#bug-50197-%EB%A9%94%EB%AA%A8%EB%A6%AC-%ED%8C%8C%ED%8B%B0%EC%85%98%EB%93%9C-%ED%85%8C%EC%9D%B4%EB%B8%94-%EC%83%9D%EC%84%B1-%EA%B5%AC%EB%AC%B8%EC%97%90%EC%84%9C-lob-%ED%85%8C%EC%9D%B4%EB%B8%94-%EC%8A%A4%ED%8E%98%EC%9D%B4%EC%8A%A4-%EC%A7%80%EC%A0%95%EC%97%90-%EB%8C%80%ED%95%9C-%EA%B2%80%EC%A6%9D%EC%9D%B4-%EB%AF%B8%ED%9D%A1%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50210  MERGE 구문의 USING 절에서 조회한 테이블이 LOB칼럼을 포함하고, ON절 또는 MATCHED ... UPDATE 절 에서 그 LOB 칼럼을 사용하면, ERR-2100C : Conversion not applicable. 오류가 발생합니다.](#bug-50210-merge-%EA%B5%AC%EB%AC%B8%EC%9D%98-using-%EC%A0%88%EC%97%90%EC%84%9C-%EC%A1%B0%ED%9A%8C%ED%95%9C-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%9D%B4-lob%EC%B9%BC%EB%9F%BC%EC%9D%84-%ED%8F%AC%ED%95%A8%ED%95%98%EA%B3%A0-on%EC%A0%88-%EB%98%90%EB%8A%94-matched--update-%EC%A0%88-%EC%97%90%EC%84%9C-%EA%B7%B8-lob-%EC%B9%BC%EB%9F%BC%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%98%EB%A9%B4-err-2100c--conversion-not-applicable-%EC%98%A4%EB%A5%98%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50232  JOIN predicate 에 _PROWID 를 사용하는 경우, 잘못된 메모리를 참조할 수 있습니다.](#bug-50232-join-predicate-%EC%97%90-_prowid-%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94-%EA%B2%BD%EC%9A%B0-%EC%9E%98%EB%AA%BB%EB%90%9C-%EB%A9%94%EB%AA%A8%EB%A6%AC%EB%A5%BC-%EC%B0%B8%EC%A1%B0%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-50241  APRE에서 INTO 구문 앞에 호스트 변수가 있는 경우 구조체 배열(row-wise binding)로 바인딩을 하지 못합니다.](#bug-50241-apre%EC%97%90%EC%84%9C-into-%EA%B5%AC%EB%AC%B8-%EC%95%9E%EC%97%90-%ED%98%B8%EC%8A%A4%ED%8A%B8-%EB%B3%80%EC%88%98%EA%B0%80-%EC%9E%88%EB%8A%94-%EA%B2%BD%EC%9A%B0-%EA%B5%AC%EC%A1%B0%EC%B2%B4-%EB%B0%B0%EC%97%B4row-wise-binding%EB%A1%9C-%EB%B0%94%EC%9D%B8%EB%94%A9%EC%9D%84-%ED%95%98%EC%A7%80-%EB%AA%BB%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50248  계층적 질의의 target 절에 사용한 함수의 별칭(alias) 을 ORDER SIBILINGS BY 절에서 사용한 칼럼 이름과 동일하게 사용한 경우, 비정상 종료 할 수 있습니다.](#bug-50248-%EA%B3%84%EC%B8%B5%EC%A0%81-%EC%A7%88%EC%9D%98%EC%9D%98-target-%EC%A0%88%EC%97%90-%EC%82%AC%EC%9A%A9%ED%95%9C-%ED%95%A8%EC%88%98%EC%9D%98-%EB%B3%84%EC%B9%ADalias-%EC%9D%84-order-sibilings-by-%EC%A0%88%EC%97%90%EC%84%9C-%EC%82%AC%EC%9A%A9%ED%95%9C-%EC%B9%BC%EB%9F%BC-%EC%9D%B4%EB%A6%84%EA%B3%BC-%EB%8F%99%EC%9D%BC%ED%95%98%EA%B2%8C-%EC%82%AC%EC%9A%A9%ED%95%9C-%EA%B2%BD%EC%9A%B0-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C-%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-50264  서버 부하 시 세션 관리자에서 동반 수행되는 특정 시스템 호출 지연으로, 기준 시간 갱신이 지연되어 UTRANS_TIMEOUT 이 발생합니다.](#bug-50264-%EC%84%9C%EB%B2%84-%EB%B6%80%ED%95%98-%EC%8B%9C-%EC%84%B8%EC%85%98-%EA%B4%80%EB%A6%AC%EC%9E%90%EC%97%90%EC%84%9C-%EB%8F%99%EB%B0%98-%EC%88%98%ED%96%89%EB%90%98%EB%8A%94-%ED%8A%B9%EC%A0%95-%EC%8B%9C%EC%8A%A4%ED%85%9C-%ED%98%B8%EC%B6%9C-%EC%A7%80%EC%97%B0%EC%9C%BC%EB%A1%9C-%EA%B8%B0%EC%A4%80-%EC%8B%9C%EA%B0%84-%EA%B0%B1%EC%8B%A0%EC%9D%B4-%EC%A7%80%EC%97%B0%EB%90%98%EC%96%B4-utrans_timeout-%EC%9D%B4-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50279  NULLIF, COALESCE, CASE2 함수의 인자로 사용자 정의 타입(User Defined Type)을 사용하는 경우, 서버가 비정상 종료할 수 있습니다.](#bug-50279-nullif-coalesce-case2-%ED%95%A8%EC%88%98%EC%9D%98-%EC%9D%B8%EC%9E%90%EB%A1%9C-%EC%82%AC%EC%9A%A9%EC%9E%90-%EC%A0%95%EC%9D%98-%ED%83%80%EC%9E%85user-defined-type%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94-%EA%B2%BD%EC%9A%B0-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-50293  iSQL에서 잘못된 사용자 아이디 또는 암호로 접속을 시도할 때 출력되는 에러메시지를 "Invalid User ID or Password"로 변경할 수 있습니다.](#bug-50293-isql%EC%97%90%EC%84%9C-%EC%9E%98%EB%AA%BB%EB%90%9C-%EC%82%AC%EC%9A%A9%EC%9E%90-%EC%95%84%EC%9D%B4%EB%94%94-%EB%98%90%EB%8A%94-%EC%95%94%ED%98%B8%EB%A1%9C-%EC%A0%91%EC%86%8D%EC%9D%84-%EC%8B%9C%EB%8F%84%ED%95%A0-%EB%95%8C-%EC%B6%9C%EB%A0%A5%EB%90%98%EB%8A%94-%EC%97%90%EB%9F%AC%EB%A9%94%EC%8B%9C%EC%A7%80%EB%A5%BC-invalid-user-id-or-password%EB%A1%9C-%EB%B3%80%EA%B2%BD%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-50307  PSM에서 NVL 함수에 record type을 사용하면 서버가 비정상 종료할 수 있습니다.](#bug-50307-psm%EC%97%90%EC%84%9C-nvl-%ED%95%A8%EC%88%98%EC%97%90-record-type%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%98%EB%A9%B4-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-50309  디스크 인덱스 빌드시 빌드 쓰레드당 SORT AREA SIZE가 4G-1 bytes를 초과하면 잘못된 동작을 할 수 있습니다.](#bug-50309-%EB%94%94%EC%8A%A4%ED%81%AC-%EC%9D%B8%EB%8D%B1%EC%8A%A4-%EB%B9%8C%EB%93%9C%EC%8B%9C-%EB%B9%8C%EB%93%9C-%EC%93%B0%EB%A0%88%EB%93%9C%EB%8B%B9-sort-area-size%EA%B0%80-4g-1-bytes%EB%A5%BC-%EC%B4%88%EA%B3%BC%ED%95%98%EB%A9%B4-%EC%9E%98%EB%AA%BB%EB%90%9C-%EB%8F%99%EC%9E%91%EC%9D%84-%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-50312  prepare 에러 발생 후 비정상 종료 발생 시, 덤프 스택에 쿼리를 기록하도록 개선합니다.](#bug-50312-prepare-%EC%97%90%EB%9F%AC-%EB%B0%9C%EC%83%9D-%ED%9B%84-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C-%EB%B0%9C%EC%83%9D-%EC%8B%9C-%EB%8D%A4%ED%94%84-%EC%8A%A4%ED%83%9D%EC%97%90-%EC%BF%BC%EB%A6%AC%EB%A5%BC-%EA%B8%B0%EB%A1%9D%ED%95%98%EB%8F%84%EB%A1%9D-%EA%B0%9C%EC%84%A0%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50343  내부적으로 디스크 인덱스 페이지 재활용 작업중에 잘못된 페이지를 삭제 시도 하다가 서버가 비정상 종료할 수 있습니다.](#bug-50343-%EB%82%B4%EB%B6%80%EC%A0%81%EC%9C%BC%EB%A1%9C-%EB%94%94%EC%8A%A4%ED%81%AC-%EC%9D%B8%EB%8D%B1%EC%8A%A4-%ED%8E%98%EC%9D%B4%EC%A7%80-%EC%9E%AC%ED%99%9C%EC%9A%A9-%EC%9E%91%EC%97%85%EC%A4%91%EC%97%90-%EC%9E%98%EB%AA%BB%EB%90%9C-%ED%8E%98%EC%9D%B4%EC%A7%80%EB%A5%BC-%EC%82%AD%EC%A0%9C-%EC%8B%9C%EB%8F%84-%ED%95%98%EB%8B%A4%EA%B0%80-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-50391  public role 은 제거되면 안됩니다.](#bug-50391-public-role-%EC%9D%80-%EC%A0%9C%EA%B1%B0%EB%90%98%EB%A9%B4-%EC%95%88%EB%90%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50402  bash쉘이 아닌 경우, 알티베이스  설치 인스톨러로 설치중에 make\_link.sh 에서 오류가 발생합니다.](#bug-50402-bash%EC%89%98%EC%9D%B4-%EC%95%84%EB%8B%8C-%EA%B2%BD%EC%9A%B0-%EC%95%8C%ED%8B%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4--%EC%84%A4%EC%B9%98-%EC%9D%B8%EC%8A%A4%ED%86%A8%EB%9F%AC%EB%A1%9C-%EC%84%A4%EC%B9%98%EC%A4%91%EC%97%90-make%5C_linksh-%EC%97%90%EC%84%9C-%EC%98%A4%EB%A5%98%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50453  LB trace log 메시지에 오류가 있어서 수정합니다.](#bug-50453-lb-trace-log-%EB%A9%94%EC%8B%9C%EC%A7%80%EC%97%90-%EC%98%A4%EB%A5%98%EA%B0%80-%EC%9E%88%EC%96%B4%EC%84%9C-%EC%88%98%EC%A0%95%ED%95%A9%EB%8B%88%EB%8B%A4)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->


==============================

New Features
============

### BUG-48520  네트워크 관련 에러메시지를 altibase\_cm.log에 기록하게 설정할 수 있습니다.

-   **module** : mm

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : NETWORK\_ERROR\_LOG\_FILE 프로퍼티를 통해 네트워크 관련
    에러메시지가 기록되는 로그를 변경할 수 있습니다. 디폴트는
    altibase\_boot.log에 기록됩니다. 이 프로퍼티의 값을 1로 변경하면,
    altibase\_cm.log에 기록합니다.

-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
        -   추가
            - NETWORK_ERROR_LOG_FILE
              - 0: 네트워크 관련 에러메시지가 altibase_boot.log에 기록되도록 설정
              - 1: 네트워크 관련 에러메시지가 altibase_cm.log에 기록되도록 설정

    -   Compile Option
    -   Error Code

### BUG-50341  prepare시 error 발생한 query에 대해 로깅하는 기능 추가

-   **module** : qp

-   **Category** : Enhancement

-   **재현 빈도** : Always

- **설명** : prepare시 error 발생한 query에 대해 로깅하는 기능 추가하였습니다. QP_MSGLOG_FLAG 프로퍼티를 66으로 변경하면, 로깅이 시작됩니다.

  ```
  alter system set QP_MSGLOG_FLAG = 66;
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

### BUG-50412  Unsupported property warning 로깅시 플래그 설정이 필요합니다.

-   **module** : mm

-   **Category** : Usability

-   **재현 빈도** : Always

-   **설명** : Unsupported property warning 로그는 상황에 따라 대량의
    로그가 출력될 수 있기 때문에 MM\_MSGLOG\_FLAG 프로퍼티로 로깅여부를 설정할 수 있도록
    변경하였습니다. MM\_MSGLOG\_FLAG의 0번 비트 기본값을 0에서 1로 변경해서 디폴트로
    로그가 출력되도록 변경하였습니다.

-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
        -   MM\_MSGLOG\_FLAG의 0번 비트 디폴트 값을 0에서 1로 변경.

    -   Compile Option
    -   Error Code

Fixed Bugs
==========

### BUG-40266  갱신 트랜잭션이 대기하는 상황이면 altibase\_boot.log에 메시지를 출력하도록 개선합니다.

-   **module** : sm

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : 갱신 트랜잭션이 대기하는 상황의 경우 사용자는 이유를 알지 못한채 무한정 대기해야 했으나, 이 버그의 처리로
    altibase\_boot.log의 메시지를 확인하여 원인 파악을 할 수 있게 개선하였습니다.

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

### BUG-47333  외부프로시저에서 라이브러리 로딩에 실패한 다음, 실패의 원인을 해결해도 외부 프로시저 실행에 실패하는 문제가 있습니다.

-   **module** : qp-psm-trigger-execute

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 외부 프로시저에서 라이브러리 로딩에 실패한 다음, 실패의 원인을 해결하더라도 외부 프로시저를 실행할 수 없는 문제를 수정합니다. 이 문제가 발생하면, 이 패치의 적용전의 경우 클라이언트를 재 접속하는 것으로 문제를 해결할 수 있었습니다. 이 패치의 적용으로 클라이언트의 재접속을 하지 않고도 문제를 해결할 수 있습니다.

- **재현 방법**

  -   **재현 절차**

          CREATE LIBRARY LIB1 AS 'andy_upper.so';
          CREATE PROCEDURE PROC1 ( istr in varchar(100), ostr out varchar(100) ) AS
          LANGUAGE C
          LIBRARY LIB1 NAME "andy_upper";
          /
          VAR VAR1 VARCHAR(100);
          VAR VAR2 VARCHAR(100);
          EXEC :VAR1 := 'aaaa';
          EXEC PROC1(:VAR1, :VAR2);
          CREATE OR REPLACE LIBRARY LIB1 AS 'invalid_library_name.so';
          EXEC PROC1(:VAR1, :VAR2);
          CREATE OR REPLACE LIBRARY LIB1 AS 'andy_upper.so';
          EXEC PROC1(:VAR1, :VAR2);

  - **수행 결과**

        iSQL> CREATE OR REPLACE LIBRARY LIB1 AS 'invalid_library_name.so';
        Create success.
        iSQL> EXEC PROC1(:VAR1, :VAR2);
        [ERR-0109F : Library file for external procedure/function not found : ......./lib/invalid_library_name.so]

        iSQL> CREATE OR REPLACE LIBRARY LIB1 AS 'andy_upper.so';
        Create success.
        iSQL> EXEC PROC1(:VAR1, :VAR2);
        [ERR-010A0 : Function for external procedure/function not found]

  -   **예상 결과**

          iSQL> CREATE OR REPLACE LIBRARY LIB1 AS 'invalid_library_name.so';
          Create success.
          iSQL> EXEC PROC1(:VAR1, :VAR2);
          [ERR-0109F : Library file for external procedure/function not found : ......./lib/invalid_library_name.so]

          iSQL> CREATE OR REPLACE LIBRARY LIB1 AS 'andy_upper.so';
          Create success.
          iSQL> EXEC PROC1(:VAR1, :VAR2);
          Execute success.

-   **Workaround**

        Client 접속을 해제하고, 다시 접속한다.

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47812  ALTER TRIGGER DDL과 DROP TRIGGER DDL에서 발생하는 동시성 문제로 비정상종료합니다.

-   **module** : qp-psm-trigger-execute

-   **Category** : Fatal

-   **재현 빈도** : Frequence

-   **설명** : ALTER TRIGGER DDL과 DROP TRIGGER DDL에서 발생하는 동시성
    문제로 비정상종료합니다.

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

### BUG-48193  group by rollup 결과값이 다른 문제를 수정합니다.

-   **module** : qp-select-pvo

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : group by rollup 결과값이 다른 문제를 수정합니다.

- **재현 방법**

  -   **재현 절차**

          drop table t1;
          drop table t2;
          create table t1 (i1 int, i2 int, i3 int, i4 int);
          create table t2 ( i1 int);
          insert into t1 values( 1,1,1,3);
          insert into t1 values( 2,2,2,4);
          insert into t2 values(1);
          select i1,
                 max(i4),
                 (select min(i1) from t2 where i1 = t1.i1) as sub
          from t1 group by rollup(i1);

  - **수행 결과**

        iSQL> select i1,
               max(i4),
               (select min(i1) from t2 where i1 = t1.i1) as sub
        from t1 group by rollup(i1);
        I1          MAX(I4)     SUB
        ----------------------------------------
        1           3           1
        2           4           1
                    4           1
        3 rows selected.

  -   **예상 결과**

          iSQL> select i1,
                 max(i4),
                 (select min(i1) from t2 where i1 = t1.i1) as sub
          from t1 group by rollup(i1);
          I1          MAX(I4)     SUB
          ----------------------------------------
          1           3           1
          2           4
                      4
          3 rows selected.

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49287  원격 서버의 트랜잭션 세그먼트가 모두 사용 중인 상태에서 이중화 Receiver가 디스크 테이블에 변경 트랜잭션 반영 시 무한 대기하는 현상이 발생합니다.

-   **module** : rp-receiver

-   **Category** : Hang

-   **재현 빈도** : Always

-   **설명** : 원격 서버의 트랜잭션 세그먼트가 모두 사용 중인 상태에서
    이중화 Receiver가 디스크 테이블에 변경 트랜잭션 반영 시 무한
    대기하는 현상을 수정합니다.

    원격 서버의 트랜잭션 세그먼트가 모두 사용 중인 경우,
    \$ALTIBASE\_HOME/trc/altibase\_boot.log 에 아래와 같은 에러 메시지가
    발생합니다.

    TRANSACTION\_SEGMENT\_COUNT is full !!

    Transaction (TID:169992) is waiting for TXSegs allocation.

    위 현상 발생 시 이중화 Receiver가 약 10초 만큼 대기 후 해당 작업을
    취소하고 Receiver를 종료하도록 수정되었습니다.

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

### BUG-49352  TRANSACTION\_SEGMENT\_COUNT 의 최대값을 900으로 변경합니다.

-   **module** : sm

-   **Category** : Usability

-   **재현 빈도** : Always

- **설명** : TRANSACTION_SEGMENT_COUNT의 최대값을 기존 512에서 900개로 확장합니다. 또한 TRANSACTION_SEGMENT_COUNT에 설정된 값보다 많은 갯수의 트랜잭션 세그먼트가 생성되는 현상을 보정하였습니다.

  이 버그의 영향은 기본값(256), 최대값(512)로 운영중인 서버는 영향이 없습니다. 그 외의 값으로 운영하던 서버는 기존보다 적은 수의 트랜잭션 세그먼트가 생성될 수 있지만, 사용자가 설정한 갯수로 생성되는 것이기 때문에 문제가 아닙니다.

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

### BUG-49399  트랜잭션에서 실행하는 구문과 체크포인트 동작의 동시성 제어에 오류가 있어서 수정합니다.

-   **module** : sm-mem-recovery

-   **Category** : Reliability

-   **재현 빈도** : Always

-   **설명** : 트랜잭션에서 실행하는 구문과 체크포인트 동작의 동시성 제어에 오류가 있어서 수정합니다.

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

### BUG-50069  서버 미기동 상태에서 isql -sysdba 접속시 발생하는 [ERR-910FB : Connected to idle instance]의 메시지를 [Connected to idle instance] 메시지로 변경합니다.

-   **module** : ux-isql

-   **Category** : Usability

-   **재현 빈도** : Always

-   **설명** : 서버 미기동 상태에서 isql -sysdba 접속시 발생하는 [ERR-910FB : Connected to idle instance] 메세지를 [Connected to idle instance] 메시지로 변경합니다.

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

### BUG-50097  iloader -direct 옵션에 잘못된 값을 사용하는 경우에 대한 오류처리가 되어 있지 않습니다.

-   **module** : ux-iloader

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : iloader -direct 옵션에 잘못된 값을 사용하는 경우에 대한 오류처리가 되어 있지 않습니다. 이 경우 -direct 옵션에 잘못된 값은 무시하고 동작되는데, 그 뒤에 나열된 옵션들의 동작도 무시되는 문제가 있습니다. 잘못된 값이 사용되면 [ERR-9103B : Invalid option ] 에러메시지가 출력되도록 수정하였습니다.

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

### BUG-50187  autocommit 모드가 off인 환경에서 UTRANS TIMEOUT 발생시, 에러 로그의 Last Query가 잘못 기록됩니다.

-   **module** : mm

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : autocommit 모드가 off인 환경에서 utrans timeout 발생시, 에러 로그의 Last Query가 잘못 기록되는 문제를 수정합니다.

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

### BUG-50196  NOCYLE 옵션으로 생성된 시퀀스가 ALTER SEQUENCE 구문을 수행한 후 서버를 재구동하면, CYCLE로 동작하는 문제가 있습니다.

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

          iSQL> SELECT seq2.NEXTVAL FROM dual;
          [ERR-11044 : Sequence upper bound exceeded]

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50197  메모리 파티션드 테이블 생성 구문에서 LOB 테이블 스페이스 지정에 대한 검증이 미흡합니다.

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

### BUG-50210  MERGE 구문의 USING 절에서 조회한 테이블이 LOB칼럼을 포함하고, ON절 또는 MATCHED ... UPDATE 절 에서 그 LOB 칼럼을 사용하면, ERR-2100C : Conversion not applicable. 오류가 발생합니다.

-   **module** : qp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : MERGE 구문의 USING 절에서 조회한 테이블이 LOB칼럼을 포함하고, ON절 또는 MATCHED ... UPDATE 절 에서 그 LOB 칼럼을 사용하면, ERR-2100C : Conversion not applicable. 오류가 발생하는 문제를 수정합니다.

-   **재현 방법**

    -   **재현 절차**

            DROP TABLE T1 ;
            DROP TABLE T2 ;
            CREATE TABLE T1 ( I1 INT, I2 CLOB );
            INSERT INTO T1 VALUES ( 1,1);
            INSERT INTO T1 VALUES ( 2,2);
            CREATE TABLE T2 ( I1 INT, I2 CLOB );
            INSERT INTO T2 VALUES ( 1,10);
            INSERT INTO T2 VALUES ( 2,20);
            MERGE INTO T1 A USING T2 B ON A.I1 = B.I1
            WHEN MATCHED THEN
            UPDATE SET A.I2 = B.I2;

    -   **수행 결과**

            [ERR-2100C : Conversion not applicable.]

    -   **예상 결과**

            2 row merged.

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50232  JOIN predicate 에 _PROWID 를 사용하는 경우, 잘못된 메모리를 참조할 수 있습니다.

-   **module** : qp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : JOIN predicate에 _PROWID를 사용하는 경우, 잘못된 메모리를 참조 할 수 있어 수정합니다.

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

### BUG-50241  APRE에서 INTO 구문 앞에 호스트 변수가 있는 경우 구조체 배열(row-wise binding)로 바인딩을 하지 못합니다.

-   **module** : mm-apre

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 구조체 배열 호스트 변수가 SQL 구문 내 첫번째 호스트 변수가 아닐때,

     row-wise 바인딩을 제대로 못하는 문제를 수정하였습니다.

- **재현 방법**

  -   **재현 절차**

  - **수행 결과**

  -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50248  계층적 질의의 target 절에 사용한 함수의 별칭(alias) 을 ORDER SIBILINGS BY 절에서 사용한 칼럼 이름과 동일하게 사용한 경우, 비정상 종료 할 수 있습니다.

-   **module** : qp-select-execute

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : 계층적 질의의 target 절에 사용한 함수의 별칭(alias) 을 ORDER SIBILINGS BY 절에서 사용한 칼럼 이름과 동일하게 사용한 경우, 비정상 종료하는 문제를 수정합니다.

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

### BUG-50264  서버 부하 시 세션 관리자에서 동반 수행되는 특정 시스템 호출 지연으로, 기준 시간 갱신이 지연되어 UTRANS_TIMEOUT 이 발생합니다.

-   **module** : mm

-   **Category** : Functional Error

-   **재현 빈도** : Frequence

-   **설명** : 서버 부하 시 세션 관리자에서 관리하는 기준 시간(base time) 갱신이 지연되는 문제가 있어, UTRANS_TIMEOUT이 발생합니다. 세션 관리자에서 지연을 유발하는 시스템 호출을 별도의 쓰레드로 분리하여 기준 시간 갱신이 지연되지 않도록 수정합니다.

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

### BUG-50279  NULLIF, COALESCE, CASE2 함수의 인자로 사용자 정의 타입(User Defined Type)을 사용하는 경우, 서버가 비정상 종료할 수 있습니다.

-   **module** : mt-function

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : NULLIF, COALESCE, CASE2 함수의 인자로 사용자 정의 타입(User Defined Type)을 사용하는 경우, 서버가 비정상 종료하는 문제를 수정합니다.

-   **재현 방법**

    -   **재현 절차**

            create or replace procedure proc1
            as
             type aa_type is table of integer;
             var1 aa_type;
             var2 varchar(128);
            begin
              var1 := nullif(var1, var1);
            end;
            /
            exec proc1;

    -   **수행 결과**

            [ERR-91015 : Communication failure.]

    -   **예상 결과**

            [ERR-2100C : Conversion not applicable.
            In PROC1
            0007 :   var1 := nullif(var1, var1);
                            ^            ^
            ]

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50293  iSQL에서 잘못된 사용자 아이디 또는 암호로 접속을 시도할 때 출력되는 에러메시지를 "Invalid User ID or Password"로 변경할 수 있습니다.

-   **module** : ux-isql

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** :

-   iSQL에서 잘못된 사용자 아이디 또는 암호로 접속을 시도하면, [ERR-31010 : User not found] 또는 [ERR-4102E : Invalid password]와 같이 상세한 접속 실패 이유가 출력됩니다. 그런데, 이렇게 상세한 접속 실패 에러메시지 대신에 [ERR-91149 : Invalid UserID or Password] 가 출력되도록 설정 할 수 있습니다.

    ISQL_SECURE_LOGIN_MSG 프로퍼티를 1로 설정하면, 사용자 아이디 또는 암호가 틀린 경우, [ERR-91149 : Invalid UserID or Password] 에러메시지가 출력됩니다.

    ```
    export ISQL_SECURE_LOGIN_MSG=1
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

### BUG-50307  PSM에서 NVL 함수에 record type을 사용하면 서버가 비정상 종료할 수 있습니다.

-   **module** : qp-psm-trigger-pvo

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : PSM에서 NVL 함수의 인자로 record type을 사용하면, 서버가 비정상 종료 할 수 있는 문제를 수정합니다.

-   **재현 방법**

    -   **재현 절차**

            CREATE OR REPLACE PROCEDURE PROC1 AS
            TYPE REC_TYPE IS RECORD(C1 INTEGER, C2 INTEGER);
            VAR1 REC_TYPE;
            BEGIN
              VAR1 := NVL(VAR1, VAR1);
            END;
            /
            EXEC PROC1;

    -   **수행 결과**

            [ERR-91015 : Communication failure.]

    -   **예상 결과**

            [ERR-21017 : The argument is not applicable.

            In procedure SYS.PROC1
            0005 :   VAR1 := NVL(VAR1, VAR1);
                            ^              ^
            ]

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50309  디스크 인덱스 빌드시 빌드 쓰레드당 SORT AREA SIZE가 4G-1 bytes를 초과하면 잘못된 동작을 할 수 있습니다.

-   **module** : sm-disk-index

-   **Category** : Other

-   **재현 빈도** : Always

-   **설명** : 디스크 인덱스 빌드시 빌드 쓰레드당 SORT AREA SIZE 가 UINT MAX (4G-1 bytes) 를 초과하는 경우, 잘못된 동작을 할 수 있어 수정합니다. 빌드 쓰레드당 SORT AREA SIZE 가 최대 UNIT MAX 로 제한되도록 수정합니다.

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

### BUG-50312  prepare 에러 발생 후 비정상 종료 발생 시, 덤프 스택에 쿼리를 기록하도록 개선합니다.

-   **module** : mm

-   **Category** : Functionality

-   **재현 빈도** : Rare

-   **설명** : prepareProtocol 처리 중에 내부적으로 잘못된 메모리의 접근으로 인한 세그먼트 결함 발생시, 덤프 스택에 쿼리 정보가 누락되는 문제를 수정합니다.

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

### BUG-50343  내부적으로 디스크 인덱스 페이지 재활용 작업중에 잘못된 페이지를 삭제 시도 하다가 서버가 비정상 종료할 수 있습니다.

-   **module** : sm-disk-index

-   **Category** : Fatal

-   **재현 빈도** : Rare

-   **설명** : 내부적으로 디스크 인덱스 페이지 재활용 작업 중에 잘못된
    페이지를 삭제할 수 있는 문제를 발견하여 개선하였습니다.

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

### BUG-50391  public role 은 제거되면 안됩니다.

-   **module** : qp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : DROP ROLE PUBLIC; 구문으로 PUBLIC ROLE을 제거할 수 있던 문제를 수정합니다. 사용자가 실수로 제거하려는 경우, 제거 할 수 없다는 에러메시지를 출력하도록 수정합니다.

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
        -   에러 메시지 추가
            -   [ERR-314B6 : It is forbidden to drop the PUBLIC role.]
                -   Cause: You cannot drop the PUBLIC role.
                -   Action: Don't try dropping the PUBLIC role.

### BUG-50402  bash쉘이 아닌 경우, 알티베이스  설치 인스톨러로 설치중에 make\_link.sh 에서 오류가 발생합니다.

-   **module** : installer

-   **Category** : Maintainability

-   **재현 빈도** : Rare

-   **설명** : 알티베이스의 설치 인스톨러를 이용하여 설치 할때, bash 쉘 환경이 아닌경우 make_link.sh 에서 오류가 발생하는 문제를 수정합니다.

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

### BUG-50453  LB trace log 메시지에 오류가 있어서 수정합니다.

-   **module** : mm

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : LB trace log 메시지에 오류가 있어 수정합니다. "현재 서비스
    쓰레드의 개수가 MULTIPLEXING\_MAX\_THREAD\_COUNT 보다
    크다"를 표시하는 메시지에서 현재 서비스 쓰레드가 아닌 새로
    생성될 서비스 쓰레드의 개수가 표시되고 있는 문제를 수정하였습니다.

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

 Version Info
| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 6.5.1.9.8        | 6.3.1                   | 8.1.1        | 7.1.3               | 7.4.5                        |

> Altibase 6.5.1 패치 버전별 히스토리는 [Version_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_6.5.1/Altibase_6_5_1_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

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
