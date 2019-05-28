<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Altibase 7.1.0.1.3 Patch Notes](#altibase-71013-patch-notes)
  - [New Features](#new-features)
    - [BUG-45145  iSQL에 히스토리 저장 기능 추가](#bug-45145-isql%EC%97%90-%ED%9E%88%EC%8A%A4%ED%86%A0%EB%A6%AC-%EC%A0%80%EC%9E%A5-%EA%B8%B0%EB%8A%A5-%EC%B6%94%EA%B0%80)
    - [BUG-45802  fetch across rollback 기능을 지원합니다.](#bug-45802-fetch-across-rollback-%EA%B8%B0%EB%8A%A5%EC%9D%84-%EC%A7%80%EC%9B%90%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-45830  awrite 유틸리티가 추가되었습니다.](#bug-45830-awrite-%EC%9C%A0%ED%8B%B8%EB%A6%AC%ED%8B%B0%EA%B0%80-%EC%B6%94%EA%B0%80%EB%90%98%EC%97%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-45858  계층형 쿼리(Hierarchy Query) 조인 지원](#bug-45858-%EA%B3%84%EC%B8%B5%ED%98%95-%EC%BF%BC%EB%A6%AChierarchy-query-%EC%A1%B0%EC%9D%B8-%EC%A7%80%EC%9B%90)
    - [BUG-45921  Queue Sequence 초기화 DDL 지원](#bug-45921-queue-sequence-%EC%B4%88%EA%B8%B0%ED%99%94-ddl-%EC%A7%80%EC%9B%90)
    - [BUG-45924  모니터링 API의 ABISqlText에 sql\_cache\_text\_id 항목을 추가해야 합니다.](#bug-45924-%EB%AA%A8%EB%8B%88%ED%84%B0%EB%A7%81-api%EC%9D%98-abisqltext%EC%97%90-sql%5C_cache%5C_text%5C_id-%ED%95%AD%EB%AA%A9%EC%9D%84-%EC%B6%94%EA%B0%80%ED%95%B4%EC%95%BC-%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-45934  계층형 쿼리(Hierarchy Query) 조인에서 Lob 사용시 제약이 있습니다.](#bug-45934-%EA%B3%84%EC%B8%B5%ED%98%95-%EC%BF%BC%EB%A6%AChierarchy-query-%EC%A1%B0%EC%9D%B8%EC%97%90%EC%84%9C-lob-%EC%82%AC%EC%9A%A9%EC%8B%9C-%EC%A0%9C%EC%95%BD%EC%9D%B4-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-45978  RDMA(Remote Direct Memory Access) 통신 기반인 Infiniband를 지원](#bug-45978-rdmaremote-direct-memory-access-%ED%86%B5%EC%8B%A0-%EA%B8%B0%EB%B0%98%EC%9D%B8-infiniband%EB%A5%BC-%EC%A7%80%EC%9B%90)
    - [BUG-45936  online table partition swap을 위한 package 지원](#bug-45936-online-table-partition-swap%EC%9D%84-%EC%9C%84%ED%95%9C-package-%EC%A7%80%EC%9B%90)
    - [BUG-45953  이중화 생성/추가시 IP 부분에 hostname으로도 지정가능하도록 지원](#bug-45953-%EC%9D%B4%EC%A4%91%ED%99%94-%EC%83%9D%EC%84%B1%EC%B6%94%EA%B0%80%EC%8B%9C-ip-%EB%B6%80%EB%B6%84%EC%97%90-hostname%EC%9C%BC%EB%A1%9C%EB%8F%84-%EC%A7%80%EC%A0%95%EA%B0%80%EB%8A%A5%ED%95%98%EB%8F%84%EB%A1%9D-%EC%A7%80%EC%9B%90)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-45344  A5 client 로 상위버전 서버와 통신 할 경우 메모리가 해제된 변수에 접근 할수 있습니다.](#bug-45344-a5-client-%EB%A1%9C-%EC%83%81%EC%9C%84%EB%B2%84%EC%A0%84-%EC%84%9C%EB%B2%84%EC%99%80-%ED%86%B5%EC%8B%A0-%ED%95%A0-%EA%B2%BD%EC%9A%B0-%EB%A9%94%EB%AA%A8%EB%A6%AC%EA%B0%80-%ED%95%B4%EC%A0%9C%EB%90%9C-%EB%B3%80%EC%88%98%EC%97%90-%EC%A0%91%EA%B7%BC-%ED%95%A0%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-45618  이중화 연결관련 Send 함수와 Receive 함수에서 thread 종료상태를 체크하도록 변경](#bug-45618-%EC%9D%B4%EC%A4%91%ED%99%94-%EC%97%B0%EA%B2%B0%EA%B4%80%EB%A0%A8-send-%ED%95%A8%EC%88%98%EC%99%80-receive-%ED%95%A8%EC%88%98%EC%97%90%EC%84%9C-thread-%EC%A2%85%EB%A3%8C%EC%83%81%ED%83%9C%EB%A5%BC-%EC%B2%B4%ED%81%AC%ED%95%98%EB%8F%84%EB%A1%9D-%EB%B3%80%EA%B2%BD)
    - [BUG-45722  TERM ON 상태에서 명령어는 출력되지 않는 기능 필요](#bug-45722-term-on-%EC%83%81%ED%83%9C%EC%97%90%EC%84%9C-%EB%AA%85%EB%A0%B9%EC%96%B4%EB%8A%94-%EC%B6%9C%EB%A0%A5%EB%90%98%EC%A7%80-%EC%95%8A%EB%8A%94-%EA%B8%B0%EB%8A%A5-%ED%95%84%EC%9A%94)
    - [BUG-45813  병렬 적용자(Parallel Applier) 의 트랜잭션 대기시에 CPU 자원을 비효율적으로 사용하는 경우가 있습니다.](#bug-45813-%EB%B3%91%EB%A0%AC-%EC%A0%81%EC%9A%A9%EC%9E%90parallel-applier-%EC%9D%98-%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98-%EB%8C%80%EA%B8%B0%EC%8B%9C%EC%97%90-cpu-%EC%9E%90%EC%9B%90%EC%9D%84-%EB%B9%84%ED%9A%A8%EC%9C%A8%EC%A0%81%EC%9C%BC%EB%A1%9C-%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94-%EA%B2%BD%EC%9A%B0%EA%B0%80-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-45825  Update 구문에 window function 사용 시 unexpected error 발생](#bug-45825-update-%EA%B5%AC%EB%AC%B8%EC%97%90-window-function-%EC%82%AC%EC%9A%A9-%EC%8B%9C-unexpected-error-%EB%B0%9C%EC%83%9D)
    - [BUG-45838  PreparedStatement.setObject(Index, Value, Sqltype, Scale)에 value로 null이 허용되어야 합니다.](#bug-45838-preparedstatementsetobjectindex-value-sqltype-scale%EC%97%90-value%EB%A1%9C-null%EC%9D%B4-%ED%97%88%EC%9A%A9%EB%90%98%EC%96%B4%EC%95%BC-%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-45856  job scheduler 동작중에 scheduler가 멈추는 상황이 생길 수 있습니다.](#bug-45856-job-scheduler-%EB%8F%99%EC%9E%91%EC%A4%91%EC%97%90-scheduler%EA%B0%80-%EB%A9%88%EC%B6%94%EB%8A%94-%EC%83%81%ED%99%A9%EC%9D%B4-%EC%83%9D%EA%B8%B8-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-45857  디스크 템프 테이블에서 정상적인 예외 상황인 경우 altibase\_error.log 에 콜스택이 남지 않도록 수정](#bug-45857-%EB%94%94%EC%8A%A4%ED%81%AC-%ED%85%9C%ED%94%84-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90%EC%84%9C-%EC%A0%95%EC%83%81%EC%A0%81%EC%9D%B8-%EC%98%88%EC%99%B8-%EC%83%81%ED%99%A9%EC%9D%B8-%EA%B2%BD%EC%9A%B0-altibase%5C_errorlog-%EC%97%90-%EC%BD%9C%EC%8A%A4%ED%83%9D%EC%9D%B4-%EB%82%A8%EC%A7%80-%EC%95%8A%EB%8F%84%EB%A1%9D-%EC%88%98%EC%A0%95)
    - [BUG-45864  dblink 에 설정된 altilinker.jar 파일을 찾을 수 없거나 권한이 적절하지 않을때 발생하는 에러메시지에 대한 Action 내용 수정](#bug-45864-dblink-%EC%97%90-%EC%84%A4%EC%A0%95%EB%90%9C-altilinkerjar-%ED%8C%8C%EC%9D%BC%EC%9D%84-%EC%B0%BE%EC%9D%84-%EC%88%98-%EC%97%86%EA%B1%B0%EB%82%98-%EA%B6%8C%ED%95%9C%EC%9D%B4-%EC%A0%81%EC%A0%88%ED%95%98%EC%A7%80-%EC%95%8A%EC%9D%84%EB%95%8C-%EB%B0%9C%EC%83%9D%ED%95%98%EB%8A%94-%EC%97%90%EB%9F%AC%EB%A9%94%EC%8B%9C%EC%A7%80%EC%97%90-%EB%8C%80%ED%95%9C-action-%EB%82%B4%EC%9A%A9-%EC%88%98%EC%A0%95)
    - [BUG-45872  altiComp 의 비교(Diff)기능 수행시, LOB 데이터의 길이가 4096 보다 클 때 Invalid Lob range 에러 발생하는 문제 수정](#bug-45872-alticomp-%EC%9D%98-%EB%B9%84%EA%B5%90diff%EA%B8%B0%EB%8A%A5-%EC%88%98%ED%96%89%EC%8B%9C-lob-%EB%8D%B0%EC%9D%B4%ED%84%B0%EC%9D%98-%EA%B8%B8%EC%9D%B4%EA%B0%80-4096-%EB%B3%B4%EB%8B%A4-%ED%81%B4-%EB%95%8C-invalid-lob-range-%EC%97%90%EB%9F%AC-%EB%B0%9C%EC%83%9D%ED%95%98%EB%8A%94-%EB%AC%B8%EC%A0%9C-%EC%88%98%EC%A0%95)
    - [BUG-45883  master와 slave 간에 서로 다른 이름의 테이블에 속해 있는 LOB 타입 컬럼을 diff하거나 sync할 때 잘못된 결과를 출력합니다.](#bug-45883-master%EC%99%80-slave-%EA%B0%84%EC%97%90-%EC%84%9C%EB%A1%9C-%EB%8B%A4%EB%A5%B8-%EC%9D%B4%EB%A6%84%EC%9D%98-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90-%EC%86%8D%ED%95%B4-%EC%9E%88%EB%8A%94-lob-%ED%83%80%EC%9E%85-%EC%BB%AC%EB%9F%BC%EC%9D%84-diff%ED%95%98%EA%B1%B0%EB%82%98-sync%ED%95%A0-%EB%95%8C-%EC%9E%98%EB%AA%BB%EB%90%9C-%EA%B2%B0%EA%B3%BC%EB%A5%BC-%EC%B6%9C%EB%A0%A5%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-45893  system\_.dba\_users\_ 테이블에 접근하는 쿼리가 Plan cahce에 등록되어 있는 경우, 사용자 세션에서는 해당 쿼리를 사용할 수 없도록 수정](#bug-45893-system%5C_dba%5C_users%5C_-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90-%EC%A0%91%EA%B7%BC%ED%95%98%EB%8A%94-%EC%BF%BC%EB%A6%AC%EA%B0%80-plan-cahce%EC%97%90-%EB%93%B1%EB%A1%9D%EB%90%98%EC%96%B4-%EC%9E%88%EB%8A%94-%EA%B2%BD%EC%9A%B0-%EC%82%AC%EC%9A%A9%EC%9E%90-%EC%84%B8%EC%85%98%EC%97%90%EC%84%9C%EB%8A%94-%ED%95%B4%EB%8B%B9-%EC%BF%BC%EB%A6%AC%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%A0-%EC%88%98-%EC%97%86%EB%8F%84%EB%A1%9D-%EC%88%98%EC%A0%95)
    - [BUG-45904  page 생성 과정 중 page 헤더초기화에서 예외가 발생 할 경우 page hash에서 BCB도 정리해야 합니다.](#bug-45904-page-%EC%83%9D%EC%84%B1-%EA%B3%BC%EC%A0%95-%EC%A4%91-page-%ED%97%A4%EB%8D%94%EC%B4%88%EA%B8%B0%ED%99%94%EC%97%90%EC%84%9C-%EC%98%88%EC%99%B8%EA%B0%80-%EB%B0%9C%EC%83%9D-%ED%95%A0-%EA%B2%BD%EC%9A%B0-page-hash%EC%97%90%EC%84%9C-bcb%EB%8F%84-%EC%A0%95%EB%A6%AC%ED%95%B4%EC%95%BC-%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-45909  AltiComp 에서 LOB 타입 컬럼에 대한 diff, sync 처리 방식 개선](#bug-45909-alticomp-%EC%97%90%EC%84%9C-lob-%ED%83%80%EC%9E%85-%EC%BB%AC%EB%9F%BC%EC%97%90-%EB%8C%80%ED%95%9C-diff-sync-%EC%B2%98%EB%A6%AC-%EB%B0%A9%EC%8B%9D-%EA%B0%9C%EC%84%A0)
    - [BUG-45925  Server에서 Numeric의 double 변환의 오차와 Client에서 Numeric의 double 변환 오차가 같도록 수정](#bug-45925-server%EC%97%90%EC%84%9C-numeric%EC%9D%98-double-%EB%B3%80%ED%99%98%EC%9D%98-%EC%98%A4%EC%B0%A8%EC%99%80-client%EC%97%90%EC%84%9C-numeric%EC%9D%98-double-%EB%B3%80%ED%99%98-%EC%98%A4%EC%B0%A8%EA%B0%80-%EA%B0%99%EB%8F%84%EB%A1%9D-%EC%88%98%EC%A0%95)
    - [BUG-45935  keep 구문에서 parallel 힌트 사용시 비정상 종료하는 문제를 수정하였습니다.](#bug-45935-keep-%EA%B5%AC%EB%AC%B8%EC%97%90%EC%84%9C-parallel-%ED%9E%8C%ED%8A%B8-%EC%82%AC%EC%9A%A9%EC%8B%9C-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%98%EB%8A%94-%EB%AC%B8%EC%A0%9C%EB%A5%BC-%EC%88%98%EC%A0%95%ED%95%98%EC%98%80%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-45958  BIT 타입 데이터에 대해 altiComp (DIFF, SYNC)가 동작하지 않습니다.](#bug-45958-bit-%ED%83%80%EC%9E%85-%EB%8D%B0%EC%9D%B4%ED%84%B0%EC%97%90-%EB%8C%80%ED%95%B4-alticomp-diff-sync%EA%B0%80-%EB%8F%99%EC%9E%91%ED%95%98%EC%A7%80-%EC%95%8A%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-45976  IPCDA 모드에서 세마포어가 삭제된 경우를 체크해야 합니다.](#bug-45976-ipcda-%EB%AA%A8%EB%93%9C%EC%97%90%EC%84%9C-%EC%84%B8%EB%A7%88%ED%8F%AC%EC%96%B4%EA%B0%80-%EC%82%AD%EC%A0%9C%EB%90%9C-%EA%B2%BD%EC%9A%B0%EB%A5%BC-%EC%B2%B4%ED%81%AC%ED%95%B4%EC%95%BC-%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-45979  인덱스 캐시 만들다가 실패하는 경우, 잘못된 페이지 정보로 접근할 수 있습니다.](#bug-45979-%EC%9D%B8%EB%8D%B1%EC%8A%A4-%EC%BA%90%EC%8B%9C-%EB%A7%8C%EB%93%A4%EB%8B%A4%EA%B0%80-%EC%8B%A4%ED%8C%A8%ED%95%98%EB%8A%94-%EA%B2%BD%EC%9A%B0-%EC%9E%98%EB%AA%BB%EB%90%9C-%ED%8E%98%EC%9D%B4%EC%A7%80-%EC%A0%95%EB%B3%B4%EB%A1%9C-%EC%A0%91%EA%B7%BC%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-45981  HBT 에 REPLICATION\_HBT\_DETECT\_TIME 를 1로 설정시, 장애체크를 쉬지않고 수행하는 문제가 있습니다.](#bug-45981-hbt-%EC%97%90-replication%5C_hbt%5C_detect%5C_time-%EB%A5%BC-1%EB%A1%9C-%EC%84%A4%EC%A0%95%EC%8B%9C-%EC%9E%A5%EC%95%A0%EC%B2%B4%ED%81%AC%EB%A5%BC-%EC%89%AC%EC%A7%80%EC%95%8A%EA%B3%A0-%EC%88%98%ED%96%89%ED%95%98%EB%8A%94-%EB%AC%B8%EC%A0%9C%EA%B0%80-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-45989  aexport를 실행하는 디렉토리에 대해 쓰기 권한이 없을 때 segmentation fault 발생합니다.](#bug-45989-aexport%EB%A5%BC-%EC%8B%A4%ED%96%89%ED%95%98%EB%8A%94-%EB%94%94%EB%A0%89%ED%86%A0%EB%A6%AC%EC%97%90-%EB%8C%80%ED%95%B4-%EC%93%B0%EA%B8%B0-%EA%B6%8C%ED%95%9C%EC%9D%B4-%EC%97%86%EC%9D%84-%EB%95%8C-segmentation-fault-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-45990  Autonomous transaction pragma를 포함하는 PSM을 query를 통해 동시에 실행하면 서버가 비정상 종료할 수 있습니다.](#bug-45990-autonomous-transaction-pragma%EB%A5%BC-%ED%8F%AC%ED%95%A8%ED%95%98%EB%8A%94-psm%EC%9D%84-query%EB%A5%BC-%ED%86%B5%ED%95%B4-%EB%8F%99%EC%8B%9C%EC%97%90-%EC%8B%A4%ED%96%89%ED%95%98%EB%A9%B4-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Altibase 7.1.0.1.3 Patch Notes
==============================

New Features
------------

### BUG-45145  iSQL에 히스토리 저장 기능 추가

-   **module** : ux-isql

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **증상** : isql에 히스토리 저장 기능이 추가되었다.

    isql에서 대화식(interactive)으로 실행한 명령어들을 프로그램 종료시
    파일로 자동 저장하는 기능이다. 

    이 기능을 활성화시키면, iSQL 재구동시 파일에 저장된 이전 명령어들을
    자동으로 로딩하므로 사용자가 방향키(↑)를 눌러서 이전 명령어에
    접근하고 실행할 수 있다.

    히스토리 저장 기능을 사용하기 위해서는 다음과 같이 ISQL\_HIST\_FILE
    환경변수를 설정해야 한다.

    \$ export ISQL\_HIST\_FILE=\~/.isql\_history

    사용자가 대화식으로 입력한 모든 정보가 기록되기 때문에 사용자 암호
    같은 민감한 정보도 함께 파일에 기록될 수 있으므로 파일 접근 관리에
    유의해야 한다.

    히스토리 저장 기능을 끄기 위해서는 ISQL\_HIST\_FILE 환경변수를
    해제한다.

    \$ unset ISQL\_HIST\_FILE

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

### BUG-45802  fetch across rollback 기능을 지원합니다.

- **module** : sm\_transaction

- **Category** : Usability

- **재현 빈도** : Rare

- **증상** : fetch across rollback 기능을 지원합니다.

  CURSOR HOLD ON 기능을 이용하여 rollback 할 때, Fetch out of sequence
  에러가 발생하는 문제를 해결하기 위하여 fetch across rollback 기능을
  제공합니다.

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

### BUG-45830  awrite 유틸리티가 추가되었습니다.

-   **module** : ut

-   **Category** : Other

-   **재현 빈도** : Always

-   **증상** : 로그 파일을 생성할때 사용되는 시스템콜을 결정하기 위해
    시스템콜의 응답시간을 출력하는 awrite 유틸리티를 추가합니다.

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

### BUG-45858  계층형 쿼리(Hierarchy Query) 조인 지원

- **module** : qp

- **Category** : Enhancement

- **재현 빈도** : Always

- **증상** : 계층형 쿼리(Hierarchy Query) 조인 지원

- **재현 방법**

  - **재현 절차**

    ```
    drop table t1;
    drop table t2;
    
    create table t1 ( i1 integer, i2 integer);
    insert into t1 values ( 2 , 7);
    insert into t1 values ( 3 , 17);
    insert into t1 values ( 4 , 27);
    insert into t1 values ( 5 , 37);
    insert into t1 values ( 6 , 47);
    
    create table t2 ( i1 integer, i2 integer);
    insert into t2 values ( 1 , 47);
    insert into t2 values ( 2 , 36);
    insert into t2 values ( 3 , 26);
    insert into t2 values ( 4 , 16);
    insert into t2 values ( 47, 6);
    
    select  * from t1 left outer join t2 on t1.i1 = t2.i1 + 1 connect by prior t1.i1 = t2.i1;
    ```

  - **수행 결과**

    ```
    iSQL>  select  * from t1 left outer join t2 on t1.i1 = t2.i1 + 1 connect by prior t1.i1 = t2.i1;
    [ERR-311A0 : A hierarchical query cannot have a join operation
    0001 : select  * from T1 left outer join T2 on T1.I1 = T2.I1 + 1 connect by prior T1.I1 = T2.I1
                                                                                     ^            ^
    .]
    ```

  - **예상 결과**

    ```
    iSQL> select  * from t1 left outer join t2 on t1.i1 = t2.i1 + 1 connect by prior t1.i1 = t2.i1;
    T1.I1       T1.I2       T2.I1       T2.I2
    -----------------------------------------------------
    2           7           1           47
    3           17          2           36
    4           27          3           26
    5           37          4           16
    3           17          2           36
    4           27          3           26
    5           37          4           16
    4           27          3           26
    5           37          4           16
    5           37          4           16
    6           47
    11 rows selected.
    ```

- **Workaround**

- **변경사항**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

### BUG-45921  Queue Sequence 초기화 DDL 지원

-   **module** : qp-ddl-dcl-execute

-   **Category** : Enhancement

-   **재현 빈도** : Always

- **증상** : Queue Sequence 초기화를 위한 DDL 구문이 추가되었습니다. [ALTER QUEUE](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/SQL1.md#alter-queue)을 참고합니다.

  예문) ALTER QUEUE q1 MSGID RESET;

  제약조건으로 q1에 데이터가 없어야 합니다.

  데이터가 있는 Queue 의 Sequence 를 초기화 하려고 하는 경우, 아래와
  같은 에러메시지를 확인할 수 있습니다.

  [ERR-31470 : A queue is not empty. Only empty queue can reset a msgid.]

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

### BUG-45924  모니터링 API의 ABISqlText에 sql\_cache\_text\_id 항목을 추가해야 합니다.

-   **module** : mm-altibaseMonitor

-   **Category** : Functionality

-   **재현 빈도** : Impossible

- **증상** : 모니터링 API의 ABISqlText에 sql\_cache\_text\_id 항목을 추가하였습니다.

  typedef struct

  {

      int       mSessID;

      int       mStmtID;

      char      mSqlText[16384+1];

      int       mTextLength;

      int       mQueryStartTime;

      int       mExecuteFlag;

      **char      mSqlCacheTextID[64+1];**   ==\> 추가된 항목

  } ABISqlText;

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

### BUG-45934  계층형 쿼리(Hierarchy Query) 조인에서 Lob 사용시 제약이 있습니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **증상** : Hierarchy Query Join에서 Lob 사용시 에러를 내도록
    수정하였습니다.

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

### BUG-45978  RDMA(Remote Direct Memory Access) 통신 기반인 Infiniband를 지원

- **module** : cm

- **Category** : Functionality

- **재현 빈도** : Always

- **증상** : 통신 성능 향상을 위해 RDMA(Remote Direct Memory Access)
  통신 기반인 Infiniband를 지원

- **재현 방법**

  - **재현 절차**
  - **수행 결과**
  - **예상 결과**

- **Workaround**

- **변경사항**

  - Performance view

    - 변경
      - [V\$STATNAME](<https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_4.md#vstatname>) 에 IB관련 항목 추가되어 sequence 변경있음.

  - Property

    - 추가

      - [IB_ENABLE](<https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_2.md#ib_enable>) 

        - 데이터 타입 :Unsigned Integer

        - 기본값 : 0

        - 속성 : 읽기 전용, 단일 값

        - 값의 범위 : [0, 1]

        - 설명 : Altibase에서 인피니밴드(InfiniBand, IB)의 사용 여부를 설정한다. 이 기능은 Linux에서만 사용할 수 있다.

          0 : IB사용하지 않음 (기본값)

          1: IB사용                                                                                                                    

      - [IB_PORT_NO](<https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_2.md#ib_port_no>)

        - 데이터 타입 :Unsigned Integer
        - 기본값 : 0
        - 속성 :읽기 전용, 단일 값
        - 값의 범위 : [1024, 65535]
        - 설명 : 인피니밴드(InfiniBand, IB)를 이용하여 통신하기 위해 사용하는 포트 번호                                                                                                                             

      - [IB_MAX_LISTEN](<https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_2.md#ib_max_listen>)

        - 데이터 타입 :Unsigned Integer
        - 기본값 : 128
        - 속성 :읽기 전용, 단일 값
        - 값의 범위 : [0, 1024]
        - 설명 : 인피니밴드(InfiniBand, IB)로 접속하여 동시에 Altibase를 사용할 수 있는 클라이언트의 최대 숫자                                                                                                                       

      - [IB_LISTENER_DISABLE](<https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_2.md#ib_listener_disable>)

        - 데이터 타입 :Unsigned Integer

        - 기본값 : 0

        - 속성 :읽기 전용, 단일 값

        - 값의 범위 :[0, 1]

        - 설명 :Altibase를 시작할 때 인피니밴드 리스너(InfiniBand Listener)의 시작 여부를 설정할 수 있다.

          0: 인피니밴드 리스너 시작(기본값)

          1: 인피니밴드 리스너 시작하지 않음                                                                                                                

      - [IB_LATENCY](<https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_2.md#ib_latency>)

        - 데이터 타입 :Unsigned Integer
        - 기본값 : 0
        - 속성 : 읽기 전용, 단일 값
        - 값의 범위 : [0, 1]
        - 설명 : rsocket의 RDMA_LATENCY 옵션 값을 설정한다. 이 프로퍼티의 값이 1이면 CPU 자원을 더 소모하더라도, 대기 시간을 줄이기 위하여 튜닝 코드를 사용한다.
          이 프로퍼티는 Altibase rdma-core ( https://github.com/ALTIBASE/rdma-core )를 사용할 때에만 사용할 수 있다.                                                                                                                            

      - [IB_CONCHKSPIN](<https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_2.md#ib_conchkspin>) 

        - 데이터 타입 :Unsigned Integer

        - 기본값 : 0 

        - 속성 :읽기 전용, 단일 값

        - 값의 범위 :[0, 2147483]

        - 설명 : rsocket의 RDMA_CONCHKSPIN 옵션 값을 설정한다. 인피니밴드의 연결 확인을 어느 주기로 할 것인지 설정하는 값이다. 

          이 값이 0이면 rsocket의 기본값을 사용한다.
          이 프로퍼티는 Altibase rdma-core ( https://github.com/ALTIBASE/rdma-core )를 사용할 때에만 사용할 수 있다.

  - Compile Option

  - Error Code

### BUG-45936  online table partition swap을 위한 package 지원

-   **module** : qp

-   **Category** : Other

-   **재현 빈도** : Always

-   **증상** : 이중화 환경에서 online table partition swap을 위한 package 지원. [UTL_COPYSWAP](<https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/StoredProcedure2.md#utl_copyswap>) 시스템 패키지에 테이블 파티션 교환을 위한 [SWAP_TABLE_PARTITION](<https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/StoredProcedure2.md#swap_table_partition>) 함수가 추가되었다.

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

### BUG-45953  이중화 생성/추가시 IP 부분에 hostname으로도 지정가능하도록 지원

-   **module** : dm

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **증상** : 이중화 생성/추가시 IP 부분에 hostname 도 허용 합니다.

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

### BUG-45344  A5 client 로 상위버전 서버와 통신 할 경우 메모리가 해제된 변수에 접근 할수 있습니다.

-   **module** : cm

-   **Category** : Memory Error

-   **재현 빈도** : Always

-   **증상** : 하위 버젼(Alitbase v5.x) Client 로 상위버전(ALTIBASE 6.3.1 이상)
    서버와 통신할때, 반환된 메모리에 접근할 수 있는 문제를
    해결하였습니다.

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

### BUG-45618  이중화 연결관련 Send 함수와 Receive 함수에서 thread 종료상태를 체크하도록 변경

-   **module** : rp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : 이중화 연결관련 Send 함수와 Receive 함수에서 thread
    종료상태를 체크하도록 '종료 flag'를 추가하였습니다.

    이중화 연결관련 Send 함수와 Receive함수에서 thread 종료상태를 알수가
    없어, Sender와 Receiver thread가 Send(Receive) 함수에서 block 되어
    있을 경우 사용자가 이중화 stop 구문을 수행하더라도 이중화가 종료가
    되지 않는 문제가 있었습니다.

    이 경우, REPLICATION\_SENDER\_SEND\_TIMEOUT에 설정된 시간만큼 대기
    후에 이중화  stop 구문이 완료되었습니다.

    이 기능으로 Sender와 Receiver thread가 Send(Receive) 함수에서 block
    되어 있는경우, 사용자가 이중화 stop 구문 수행시 바로 이중화가 종료
    될수 있도록 개선되었습니다.

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

### BUG-45722  TERM ON 상태에서 명령어는 출력되지 않는 기능 필요

-   **module** : ux-isql

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **증상** : TERM ON 상태에서 ECHO OFF를 설정하면 명령어는 출력되지
    않도록 수정. 기존에는 TERM ON일 때 ECHO OFF를 설정하여도 아무런 영향이 없었음.

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

### BUG-45813  병렬 적용자(Parallel Applier) 의 트랜잭션 대기시에 CPU 자원을 비효율적으로 사용하는 경우가 있습니다.

-   **module** : dm

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : 병렬 적용자(Parallel Applier) 의 트랜잭션 대기시에 CPU
    자원을 비효율적으로 사용하는 경우가 있어, 이를 수정하였습니다.

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

### BUG-45825  Update 구문에 window function 사용 시 unexpected error 발생

- **module** : qp-dml-execute

- **Category** : Other

- **재현 빈도** : Always

- **증상** : Update 구문에 window function이 사용될 경우 unexpected
  error 가 발생한다.

  정확한 에러 메시지를 출력하도록 수정하였다.

- **재현 방법**

  -   **재현 절차**

          drop table t1;
          create table t1( i1 integer, i2 integer, i3 integer );
          insert into t1 values ( 1, 1, 1 );
          insert into t1 values ( 1, 2, 1 );
          insert into t1 values ( 1, 3, 2 );
          insert into t1 values ( 1, 4, 2 );
          insert into t1 values ( 1, 5, 0 );
          insert into t1 values ( 1, 6, 0 );
          insert into t1 values ( 2, 7, 1 );
          insert into t1 values ( 2, 8, 1 );
          insert into t1 values ( 2, 9, 2 );
          insert into t1 values ( 2, 10, 2 );
          update t1 set i1 = nvl(lag( i3 ) over ( partition by i1 order by i2 ),0) ;

  -   **수행 결과**

          iSQL> update t1 set i1 = nvl(lag( i3 ) over ( partition by i1 order by i2 ),0) ;
          [ERR-31318 : Unexpected errors may have occurred: qtc::estimate4OverClause: Invalid callback]

  -   **예상 결과**

          iSQL> update t1 set i1 = nvl(lag( i3 ) over ( partition by i1 order by i2 ),0) ;
          [ERR-3146D : An analytic function is not allowed here. 0001 : update T1 set I1 = NVL(LAG( I3 ) over ( partition by I1 order by I2 ),0)                              ^                                             ^]

- **Workaround**

- **변경사항**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code
      -   1133,qpERR\_ABORT\_QCV\_NOT\_ALLOWED\_ANALYTIC = An analytic
          function is not allowed here. \<0%s\>
          \# \*Cause: An analytic function cannot be used here.
          \# \*Action: Check all analytic functions.

### BUG-45838  PreparedStatement.setObject(Index, Value, Sqltype, Scale)에 value로 null이 허용되어야 합니다.

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : PreparedStatement.setObject(Index, Value, Sqltype, Scale)
    인터페이스 사용시 value가 null인 경우 exception이 발생하는 문제를
    수정하였습니다.

- **재현 방법**

  -   **재현 절차**

          create table t1 (c1 varchar(20), c2 numeric);
          sPreStmt.setObject( 1, "Susan" );
          sPreStmt.setObject( 2, null, Types.NUMERIC, 5 );
          sPreStmt.execute();

  - **수행 결과**

        Exception in thread "main" java.lang.NullPointerException
                at Altibase.jdbc.driver.AltibasePreparedStatement.setObject(AltibasePreparedStatement.java:1021)
                at SimpleSQL.main(SimpleSQL.java:72)

  -   **예상 결과**

          No errors.

-   **Workaround**

        sPreStmt.setObject( 2, null, Types.NUMERIC );

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-45856  job scheduler 동작중에 scheduler가 멈추는 상황이 생길 수 있습니다.

-   **module** : qp

-   **Category** : Hang

-   **재현 빈도** : Rare

-   **증상** : scheduler 동작중에 scheduler가 멈출 수 있는 상황을 수정하였습니다.

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

### BUG-45857  디스크 템프 테이블에서 정상적인 예외 상황인 경우 altibase\_error.log 에 콜스택이 남지 않도록 수정

- **module** : sm

- **Category** : Message Error

- **재현 빈도** : Always

- **증상** : 디스크 템프 테이블에서 정상적인 예외 상황인 경우에도
  \$ALTIBASE\_HOME/trc/altibase\_error.log 에 콜스택이 남는 문제가
  있어, 사용자가 보기에 문제가 있는것처럼 오인할 수 있습니다.

  이에, 정상적인 예외상황의 경우에는 \$ALTIBASE\_HOME/trc/altibase\_error.log 에 콜스택이 남지
  않도록 수정하였으며, \$ALTIBASE\_HOME/trc/altibase\_dump.log 에 해당내역을 남기도록
  수정하였습니다.

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

### BUG-45864  dblink 에 설정된 altilinker.jar 파일을 찾을 수 없거나 권한이 적절하지 않을때 발생하는 에러메시지에 대한 Action 내용 수정

- **module** : dblink

- **Category** : Other

- **재현 빈도** : Always

- **증상** :

  dblink 사용시에 altilinker.jar를 찾는 과정에서 해당 파일을 찾을 수
  없거나 권한이 적절하지 않을때 발생하는 에러메시지에 대한 Action을
  아래와 같이 수정한다.

  (변경전)

  \# *Action:

  \#   - Check the property of 'ALTILINKER\_TRACE\_LOG\_DIR' in the dblink.conf property file. 

  (변경후)

  \# *Action:

  \#   - Can not find or access 'ALTIBASE\_HOME/bin/altilinker.jar'
  file. 

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

### BUG-45872  altiComp 의 비교(Diff)기능 수행시, LOB 데이터의 길이가 4096 보다 클 때 Invalid Lob range 에러 발생하는 문제 수정

-   **module** : ux-audit(altiComp)

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : altiComp에서 LOB 타입에 대한 비교(diff) 수행시 데이터 길이 계산에 오류가 있었습니다. 이를 수정하였습니다.

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

### BUG-45883  master와 slave 간에 서로 다른 이름의 테이블에 속해 있는 LOB 타입 컬럼을 diff하거나 sync할 때 잘못된 결과를 출력합니다.

-   **module** : ux-audit(altiComp)

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : master와 slave 간에 서로 다른 이름의 테이블에 속해 있는
    LOB 타입 컬럼을 diff하거나 sync할 때, 잘못된 결과를 출력는 문제를 수정하였습니다.

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

### BUG-45893  system\_.dba\_users\_ 테이블에 접근하는 쿼리가 Plan cahce에 등록되어 있는 경우, 사용자 세션에서는 해당 쿼리를 사용할 수 없도록 수정

-   **module** : qp-dml-execute

-   **Category** : Functional Error

-   **재현 빈도** : Always

- **증상** : plan cache에 등록된 쿼리가  SYSTEM\_ 만 사용할 수 있는 테이블을 조회하는 쿼리인 경우, 사용자
  세션에서 동일한 쿼리 수행시 조회가 되는 문제가 있었습니다.

  예) select count(\*) from system\_.dba\_users\_; 

  DBA\_USERS\_ 테이블은 SYSTEM\_ 만 사용할 수 있는 테이블이기 때문에, 사용자 세션에서는 조회할 수 없어야 합니다. 

  만약, 사용자 세션에서 위의 쿼리를 수행하려고 하면, 아래의 에러메시지를 출력하도록 수정하였습니다.

  [ERR-31031 : Table or view was not found : DBA\_USERS\_]

- **재현 방법**

  - **재현 절차**

        select count(*) from system_.dba_users_;
        create user aa identified by aa;
        connect aa/aa;
        select count(*) from system_.dba_users_;

  - **수행 결과**

        iSQL> select count(*) from system_.dba_users_;
        COUNT(*)
        -----------------------
        4
        1 row selected.

  - **예상 결과**

        iSQL> select count(*) from system_.dba_users_;
        [ERR-31031 : Table or view was not found : DBA_USERS_]

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-45904  page 생성 과정 중 page 헤더초기화에서 예외가 발생 할 경우 page hash에서 BCB도 정리해야 합니다.

-   **module** : sm-disk-page

-   **Category** : Assert

-   **재현 빈도** : Rare

- **증상** : extent 를 할당 후 page 초기화 중 예상치못한 에러가 발생하는 경우, 페이지 해시(HASH)에서 해당 BCB정보가 제거되지 않는 문제가 있습니다.

  페이지 헤더 초기화 실패시, 페이지 해시에서도 해당 BCB 정보를 제거하도록 예외처리 부분이 수정되었습니다.

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

### BUG-45909  AltiComp 에서 LOB 타입 컬럼에 대한 diff, sync 처리 방식 개선

-   **module** : ux-audit(altiComp)

-   **Category** : Efficiency

-   **재현 빈도** : Always

-   **증상** : AltiComp 에서 LOB 칼럼에 대한 DIFF/SYNC 시, 간헐적으로 hang이 발생하는 문제 수정하였습니다.

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

### BUG-45925  Server에서 Numeric의 double 변환의 오차와 Client에서 Numeric의 double 변환 오차가 같도록 수정

-   **module** : ul-odbc

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : Server에서 Numeric의 double 변환의 오차와 Client에서
    Numeric의 double 변환 오차에 차이가 있던 문제가 해결되었습니다.

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

### BUG-45935  keep 구문에서 parallel 힌트 사용시 비정상 종료하는 문제를 수정하였습니다.

-   **module** : qx

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **증상** : keep은 parallel 지원하지 않도록 수정하였습니다.

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

### BUG-45958  BIT 타입 데이터에 대해 altiComp (DIFF, SYNC)가 동작하지 않습니다.

-   **module** : ux-audit(altiComp)

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : altiComp에서 DIFF, SYNC 에서 BIT, VARBIT 타입을 지원하도록 수정하였습니다.

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

### BUG-45976  IPCDA 모드에서 세마포어가 삭제된 경우를 체크해야 합니다.

-   **module** : cm

-   **Category** : Hang

-   **재현 빈도** : Always

- **증상** : IPCDA에서 세마포어 삭제된 경우 Hang이 걸리는 문제를 수정하였습니다.

-   **재현 방법**

    -   **재현 절차**

            isql with IPCDA
            select 1 from dual;
            server kill;
            server start;
            quit isql

    -   **수행 결과**

            Hang.

    -   **예상 결과**

            Isql exited

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-45979  인덱스 캐시 만들다가 실패하는 경우, 잘못된 페이지 정보로 접근할 수 있습니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Impossible

-   **증상** : 인덱스 캐시 정보를 구축할 때 잘못된 페이지 정보로 접근하는 경우, 서버가 비정상 종료 할 수 있는 문제를 수정하였습니다.

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

### BUG-45981  HBT 에 REPLICATION\_HBT\_DETECT\_TIME 를 1로 설정시, 장애체크를 쉬지않고 수행하는 문제가 있습니다.

-   **module** : dm

-   **Category** : Functional Error

-   **재현 빈도** : Frequence

-   **증상** : REPLICATION\_HBT\_DETECT\_TIME 을 1로 설정하면 HBT이 쉬지않고 장애를 체크하는 문제가 있어, 이를 수정하였습니다.

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

### BUG-45989  aexport를 실행하는 디렉토리에 대해 쓰기 권한이 없을 때 segmentation fault 발생합니다.

-   **module** : ux-aexport

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **증상** : aexport를 실행하는 디렉토리에 대해 실행 유저의 쓰기 권한이 없어 파일열기를 실패하는 경우, 에러메시지를 출력하도록 수정하였습니다.

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

### BUG-45990  Autonomous transaction pragma를 포함하는 PSM을 query를 통해 동시에 실행하면 서버가 비정상 종료할 수 있습니다.

-   **module** : qp-psm-trigger-execute

-   **Category** : Fatal

-   **재현 빈도** : Rare

- **증상** : Autonomous transaction pragma를 포함하는 PSM을 query를 통해 여러 세션에서 동시에 실행하면 낮은 확률로 서버가 비정상 종료할 수 있습니다.

  서버를 비정상 종료시키지 않도록 수정했습니다.

- **재현 방법**

  -   **재현 절차**

          create or replace function func1 return integer as
          var1 integer;
          var2 integer;
          pragma autonomous_transaction;
          begin
            select count(*) into var1 from dual;
            for p1 in 1 .. 100000 loop
              var2 := p1;
            end loop;
            return var1;
          end;
          /
          select func1 from dual;

  -   **수행 결과**

          Abnormal shutdown.

  - **예상 결과**

        iSQL> select func1 from dual;
        FUNC1
        --------------
        1
        1 row selected.

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
| 7.1.0.1.3        | 6.5.1                   | 8.5.1        | 7.1.6               | 7.4.2                        | 2.0.0            |


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

#### Sharding Version

샤딩 버전은 변경 되지 않았다.

> 알티베이스 샤딩 프로토콜 및 메타는 상위, 하위 호환성을 보장하지
> 않는다. 즉, 샤딩 버전이 다른 경우, 재구성해야 한다.

### 프로퍼티

#### 추가된 프로퍼티

- [IB_ENABLE](<https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_2.md#ib_enable>)                                                                                                                          
- [IB_PORT_NO](<https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_2.md#ib_port_no>)                                                                                                                               
- [IB_MAX_LISTEN](<https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_2.md#ib_max_listen>)                                                                                                                             
- [IB_LISTENER_DISABLE](<https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_2.md#ib_listener_disable>)                                                                                                                    
- [IB_LATENCY](<https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_2.md#ib_latency>)                                                                                                                                
- [IB_CONCHKSPIN](<https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_2.md#ib_conchkspin>)  

### 성능 뷰

#### 변경된 성능 뷰

* [V\$STATNAME](<https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_4.md#vstatname>)
