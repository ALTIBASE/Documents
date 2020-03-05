<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Altibase 7.1.0.3.0 Patch Notes](#altibase-71030-patch-notes)
  - [New Features](#new-features)
    - [BUG-47347  DML로 인한 LOCK 상황에서 Partition Split이 가능하도록 개선합니다.](#bug-47347-dml%EB%A1%9C-%EC%9D%B8%ED%95%9C-lock-%EC%83%81%ED%99%A9%EC%97%90%EC%84%9C-partition-split%EC%9D%B4-%EA%B0%80%EB%8A%A5%ED%95%98%EB%8F%84%EB%A1%9D-%EA%B0%9C%EC%84%A0%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-47416  CLI에서 LOB file 바인딩시 2GB 제한을 제거해야 합니다.](#bug-47416-cli%EC%97%90%EC%84%9C-lob-file-%EB%B0%94%EC%9D%B8%EB%94%A9%EC%8B%9C-2gb-%EC%A0%9C%ED%95%9C%EC%9D%84-%EC%A0%9C%EA%B1%B0%ED%95%B4%EC%95%BC-%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-47456  updateBinaryStream()에서 4GB 데이터를 업데이트 할 수 있도록 개선](#bug-47456-updatebinarystream%EC%97%90%EC%84%9C-4gb-%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%A5%BC-%EC%97%85%EB%8D%B0%EC%9D%B4%ED%8A%B8-%ED%95%A0-%EC%88%98-%EC%9E%88%EB%8F%84%EB%A1%9D-%EA%B0%9C%EC%84%A0)
    - [BUG-47431  APRE의 PSM Array를 확인하는 쿼리에 성능 저하가 있습니다.](#bug-47431-apre%EC%9D%98-psm-array%EB%A5%BC-%ED%99%95%EC%9D%B8%ED%95%98%EB%8A%94-%EC%BF%BC%EB%A6%AC%EC%97%90-%EC%84%B1%EB%8A%A5-%EC%A0%80%ED%95%98%EA%B0%80-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-47436  altiMon에서 Altibase 접속정보를 설정할 때, 추가적인 연결 속성을 지정하는 기능이 필요합니다](#bug-47436-altimon%EC%97%90%EC%84%9C-altibase-%EC%A0%91%EC%86%8D%EC%A0%95%EB%B3%B4%EB%A5%BC-%EC%84%A4%EC%A0%95%ED%95%A0-%EB%95%8C-%EC%B6%94%EA%B0%80%EC%A0%81%EC%9D%B8-%EC%97%B0%EA%B2%B0-%EC%86%8D%EC%84%B1%EC%9D%84-%EC%A7%80%EC%A0%95%ED%95%98%EB%8A%94-%EA%B8%B0%EB%8A%A5%EC%9D%B4-%ED%95%84%EC%9A%94%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-47437  altiMon에서 action script 수행시 metric 이름, 레벨, 기준값, 측정값을 인자로 넘겨줘야 합니다.](#bug-47437-altimon%EC%97%90%EC%84%9C-action-script-%EC%88%98%ED%96%89%EC%8B%9C-metric-%EC%9D%B4%EB%A6%84-%EB%A0%88%EB%B2%A8-%EA%B8%B0%EC%A4%80%EA%B0%92-%EC%B8%A1%EC%A0%95%EA%B0%92%EC%9D%84-%EC%9D%B8%EC%9E%90%EB%A1%9C-%EB%84%98%EA%B2%A8%EC%A4%98%EC%95%BC-%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-47434  SQLCLI에서 반환되는 에러를 출력할 때 에러 코드도 포함해야 합니다](#bug-47434-sqlcli%EC%97%90%EC%84%9C-%EB%B0%98%ED%99%98%EB%90%98%EB%8A%94-%EC%97%90%EB%9F%AC%EB%A5%BC-%EC%B6%9C%EB%A0%A5%ED%95%A0-%EB%95%8C-%EC%97%90%EB%9F%AC-%EC%BD%94%EB%93%9C%EB%8F%84-%ED%8F%AC%ED%95%A8%ED%95%B4%EC%95%BC-%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-47353  샤드 객체와 구성에 대한 report를 제공해야 합니다.](#bug-47353-%EC%83%A4%EB%93%9C-%EA%B0%9D%EC%B2%B4%EC%99%80-%EA%B5%AC%EC%84%B1%EC%97%90-%EB%8C%80%ED%95%9C-report%EB%A5%BC-%EC%A0%9C%EA%B3%B5%ED%95%B4%EC%95%BC-%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-46632  메모리 덤프시 TRACE LOG가 2KB를 초과하는 경우 출력되지 않는 문제가 있습니다.](#bug-46632-%EB%A9%94%EB%AA%A8%EB%A6%AC-%EB%8D%A4%ED%94%84%EC%8B%9C-trace-log%EA%B0%80-2kb%EB%A5%BC-%EC%B4%88%EA%B3%BC%ED%95%98%EB%8A%94-%EA%B2%BD%EC%9A%B0-%EC%B6%9C%EB%A0%A5%EB%90%98%EC%A7%80-%EC%95%8A%EB%8A%94-%EB%AC%B8%EC%A0%9C%EA%B0%80-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-47371  이중화 대상이 아닌 table partition 인 경우에는 이중화 flag로 설정하지 않도록 수정합니다.](#bug-47371-%EC%9D%B4%EC%A4%91%ED%99%94-%EB%8C%80%EC%83%81%EC%9D%B4-%EC%95%84%EB%8B%8C-table-partition-%EC%9D%B8-%EA%B2%BD%EC%9A%B0%EC%97%90%EB%8A%94-%EC%9D%B4%EC%A4%91%ED%99%94-flag%EB%A1%9C-%EC%84%A4%EC%A0%95%ED%95%98%EC%A7%80-%EC%95%8A%EB%8F%84%EB%A1%9D-%EC%88%98%EC%A0%95%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-47404  restart recovery 에서 WAL 검사가 잘못 되고 있습니다.](#bug-47404-restart-recovery-%EC%97%90%EC%84%9C-wal-%EA%B2%80%EC%82%AC%EA%B0%80-%EC%9E%98%EB%AA%BB-%EB%90%98%EA%B3%A0-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-47410  cross apply (Lateral View) 사용 시 Leading Hint 를 사용하면 비정상종료 할 수 있습니다.](#bug-47410-cross-apply-lateral-view-%EC%82%AC%EC%9A%A9-%EC%8B%9C-leading-hint-%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EB%A9%B4-%EB%B9%84%EC%A0%95%EC%83%81%EC%A2%85%EB%A3%8C-%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-47412  EXECUTE\_STMT\_MEMORY 사용량을 줄이도록 PSM 객체간 dependency 검사 쿼리를 수정해야 합니다](#bug-47412-execute%5C_stmt%5C_memory-%EC%82%AC%EC%9A%A9%EB%9F%89%EC%9D%84-%EC%A4%84%EC%9D%B4%EB%8F%84%EB%A1%9D-psm-%EA%B0%9D%EC%B2%B4%EA%B0%84-dependency-%EA%B2%80%EC%82%AC-%EC%BF%BC%EB%A6%AC%EB%A5%BC-%EC%88%98%EC%A0%95%ED%95%B4%EC%95%BC-%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-47414  디스크 테이블에서 outer apply (Lateral View)를 사용하는 경우 결과 값 오류가 발생할 수 있습니다.](#bug-47414-%EB%94%94%EC%8A%A4%ED%81%AC-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90%EC%84%9C-outer-apply-lateral-view%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94-%EA%B2%BD%EC%9A%B0-%EA%B2%B0%EA%B3%BC-%EA%B0%92-%EC%98%A4%EB%A5%98%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-47415  로그앵커 백업 시 경로가 비어있으면 비정상 종료할 수 있습니다.](#bug-47415-%EB%A1%9C%EA%B7%B8%EC%95%B5%EC%BB%A4-%EB%B0%B1%EC%97%85-%EC%8B%9C-%EA%B2%BD%EB%A1%9C%EA%B0%80-%EB%B9%84%EC%96%B4%EC%9E%88%EC%9C%BC%EB%A9%B4-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-47424  { ? = call } 이 포함된 sql문을 escape처리하면서 StringIndexOutOfBoundsException 예외가 발생합니다.](#bug-47424----call--%EC%9D%B4-%ED%8F%AC%ED%95%A8%EB%90%9C-sql%EB%AC%B8%EC%9D%84-escape%EC%B2%98%EB%A6%AC%ED%95%98%EB%A9%B4%EC%84%9C-stringindexoutofboundsexception-%EC%98%88%EC%99%B8%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-47461  windows 2016에서 isql, iloader 로 파라미터의 일부가 잘리는 문제가 있습니다.](#bug-47461-windows-2016%EC%97%90%EC%84%9C-isql-iloader-%EB%A1%9C-%ED%8C%8C%EB%9D%BC%EB%AF%B8%ED%84%B0%EC%9D%98-%EC%9D%BC%EB%B6%80%EA%B0%80-%EC%9E%98%EB%A6%AC%EB%8A%94-%EB%AC%B8%EC%A0%9C%EA%B0%80-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Altibase 7.1.0.3.0 Patch Notes
==============================

New Features
------------

### BUG-47347  DML로 인한 LOCK 상황에서 Partition Split이 가능하도록 개선합니다.

-   **module** : qp-ddl-dcl-execute

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **증상** :  DML로 인한 LOCK 상황에서 Partition Split이 가능하도록 개선합니다.
    
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

### BUG-47416  CLI에서 LOB file 바인딩시 2GB 제한을 제거해야 합니다.

-   **module** : mm-cli

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : File 바인딩 (SQLBindFileToParam)을 이용해 LOB 데이터 Insert시 최대 사이즈가 2GB-1byte로 제한 되어 있는 부분을 4GB - 1byte로 수정하였습니다. LOB의 최대 사이즈는 4GB-1byte(4,294,967,295)입니다.
    
- **재현 방법**

  -   **재현 절차**

  -   **수행 결과**

  -   **예상 결과**

-   **Workaround**

        Use SQLPutLob() instead of SQLBindFileToParam()

-   **변경사항**

    - Performance view
    
    - Property
    
      - SQLBindFileToParam을 이용한 LOB file 바인딩시, LOB Insert  최대 사이즈
    
        변경전 : 2GB - 1byte
    
        변경후 : 4GB - 1byte
    
    - Compile Option
    
    - Error Code
    
      -   에러메시지가 아래와 같이변경되었습니다.
    
          - 변경전: General error. The size of the provided file <0%s> is too big. The maximum file size is about 2GB.
    
          - 변경후: General error. The size of the provided file <0%s> is too big. The maximum file size is 4,294,967,295 bytes (4GB-1byte).

### BUG-47456  updateBinaryStream()에서 4GB 데이터를 업데이트 할 수 있도록 개선

- **module** : mm-jdbc

- **Category** : Functionality

- **재현 빈도** : Always

- **증상** : updateBinaryStream()을 사용해서 LOB 데이터를 update 할 때
  길이인자가 int 타입이라 4GB 데이터로 update 할 수 없습니다.

  그래서 long 타입을 지원하는 interface를 추가하여, 4GB 데이터를 업데이트 할수 있도록 수정되었습니다.

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

### BUG-47431  APRE의 PSM Array를 확인하는 쿼리에 성능 저하가 있습니다.

-   **module** : mm-apre

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **증상** : APRE의 PSM Array를 확인하는 쿼리의 성능을 개선하였습니다.

    수정후 0.445673 -\> 0.001323 처리 시간 단축됨. (단위 : microseconds)

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

### BUG-47436  altiMon에서 Altibase 접속정보를 설정할 때, 추가적인 연결 속성을 지정하는 기능이 필요합니다

-   **module** : ux-altiMon

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **증상** : altiMon 에서 모니터링 대상인 Alitbase 접속정보를 설정할때, 추가적인 연결 속성을 지정하는 기능이 추가되었습니다.
    

 config.xml에 \<ConnectionProperties\> 태그를 추가하여 설정할 수 있다.
    
     예) <ConnectionProperties> login_timeout=3;fetch_timeout=60 <ConnectionProperties>

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

### BUG-47437  altiMon에서 action script 수행시 metric 이름, 레벨, 기준값, 측정값을 인자로 넘겨줘야 합니다.

-   **module** : ux-altiMon

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **증상** : altiMon에서 action script 수행시 metric 이름, 레벨, threshold 값, 측정값이 인자로 전달되도록 수정합니다.
    
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

### BUG-47434  SQLCLI에서 반환되는 에러를 출력할 때 에러 코드도 포함해야 합니다

-   **module** : ux-audit(altiComp)

-   **Category** : Usability

-   **재현 빈도** : Always

-   **증상** : 서버 또는 SQLCLI 라이브러리에서 반환되는 에러 메시지에 에러 코드가 포함되도록 수정하였습니다.

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

### BUG-47353  샤드 객체와 구성에 대한 report를 제공해야 합니다.

-   **module** : ux-shardManager

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **증상** : 샤드 객체와 구성에 대한 Configuration & report가
    추가되었습니다.

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

### BUG-46632  메모리 덤프시 TRACE LOG가 2KB를 초과하는 경우 출력되지 않는 문제가 있습니다.

-   **module** : id

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** :  메모리 덤프시 TRACE LOG가 2KB를 초과하는 경우, 2KB까지 출력하도록 수정합니다.
    
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

### BUG-47371  이중화 대상이 아닌 table partition 인 경우에는 이중화 flag로 설정하지 않도록 수정합니다.

-   **module** : rp

-   **Category** : Maintainability

-   **재현 빈도** : Always

-   **증상** :  이중화 대상이 아닌 table partition 인 경우에는 이중화 flag로 설정하지 않도록 수정합니다.
    
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

### BUG-47404  restart recovery 에서 WAL 검사가 잘못 되고 있습니다.

-   **module** : sm\_recovery

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : 1. logfile이 잘못되어 이후 log가 더 있음에도 불구하고 잘못된 logfile까지만 redo하였을 때 WAL이 깨어진 것을 검증하지 못하는 버그
    
2. WAL을 확인 하는 부분이, 이후 logfile을 reset 하는 부분 보다 뒤에 있어서 한번 잘못된 recovery를 시도 하면 버그 1의 문제가 해결되어 WAL이 잘못된 것을 찾아내더라도 이미 이후 logfile이 모두 reset되어 recovery 재시도가 불가능하게 만드는 버그 
   

위의 두 버그를 수정하였습니다.
    
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

### BUG-47410  cross apply (Lateral View) 사용 시 Leading Hint 를 사용하면 비정상종료 할 수 있습니다.

-   **module** : qp-select

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **증상** : cross apply (Lateral View) 사용 시 Leading Hint 를 사용하면 비정상종료 할 수 있습니다.
    
- **재현 방법**

  -   **재현 절차**

          drop table t1;
          drop table t2;
          drop table t3;
          create table t1 (c1 int, c2 int, c3 int, c4 int);
          create table t2 (c1 int, c2 int, c3 int, c4 int);
          create table t3 (c1 int, c2 int, c3 int, c4 int);
          create index ix_t3 on t3(c1, c2, c3);
          insert into t1 values(1,1,1,1);
          insert into t2 values(1,1,1,1);
          insert into t3 values(1,1,1,1);
          select /*+ leading(a, b) */ a.c1, a.c2, a.c3
          from t1 a
              inner join t2 q
              on ( a.c1 = q.c1
          and a.c2 = q.c2 )
          cross apply ( select /*+index(b, ix_t3) no_merge*/ distinct b.c1, b.c2, b.c3, b.c4
          from t3 b
          where b.c1 = a.c1
          and b.c2 = a.c2
          and b.c3 = q.c3 ) b;

  -   **수행 결과**

          [ERR-91015 : Communication failure.]

  -   **예상 결과**

          C1          C2          C3          
          ----------------------------------------
          1           1           1           
          1 row selected.

- **Workaround**

      select /*+ ordered */ a.c1, a.c2, a.c3
      from t1 a
          inner join t2 q
          on ( a.c1 = q.c1
      and a.c2 = q.c2 )
      cross apply ( select /*+index(b, ix_t3) no_merge*/ distinct b.c1, b.c2, b.c3, b.c4
      from t3 b
      where b.c1 = a.c1
      and b.c2 = a.c2
      and b.c3 = q.c3 ) b;

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47412  EXECUTE\_STMT\_MEMORY 사용량을 줄이도록 PSM 객체간 dependency 검사 쿼리를 수정해야 합니다

-   **module** : ux-aexport

-   **Category** : Efficiency

-   **재현 빈도** : Always

-   **증상** :  PSM 객체간 dependency 검사 쿼리를 수정하여 EXECUTE\_STMT\_MEMORY 사용량을 줄이도록 개선하였습니다.
    
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

### BUG-47414  디스크 테이블에서 outer apply (Lateral View)를 사용하는 경우 결과 값 오류가 발생할 수 있습니다.

-   **module** : qp-select-execute

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : 디스크 테이블에서 outer apply (Lateral View)를 사용하는 경우 결과 값 오류가 발생할 수 있습니다.
    
- **재현 방법**

  -   **재현 절차**

          drop table t1;
          drop table t2;
          drop table t3;
          drop table t4;
          drop table t5;
          create table t1( c1 int, c2 int, c3 int )
          tablespace sys_tbs_disk_data;
          create table t2( c1 int, c2 int, c3 int )
          tablespace sys_tbs_disk_data;
          create table t3( c1 int, c2 int, c3 int )
          tablespace sys_tbs_disk_data;
          create table t4( c1 int, c2 int, c3 int )
          tablespace sys_tbs_disk_data;
          create table t5( c1 int, c2 int, c3 int )
          tablespace sys_tbs_disk_data;
          insert into t1 (select level, level, level  from dual connect by level<=6);
          insert into t2 (select level, level, level  from dual connect by level<=6);
          insert into t3 (select level, level, level  from dual connect by level<=5);
          insert into t4 (select level, level, level  from dual connect by level<=5);
          insert into t5 (select level, level, level  from dual connect by level<=5);
          iSQL> select c.c2, LV1.c3
               from t1 a
                   inner join t2 q on ( a.c1 = q.c1 and a.c2 = q.c2 )
                   outer apply ( select /*+ no_merge*/ distinct c1, c2, c3
                                 from t3 b
                                 where b.c1 = a.c1 and b.c3 = q.c3 ) LV1
                   left outer join t4 c on ( c.c1 = a.c1 and c.c2 = LV1.c2 );
      
  - **수행 결과**

        C2          C3
        ---------------------------


    ​    
    ​    
    ​    
    ​    
    ​    

        6 rows selected.

  -   **예상 결과**

          C2          C3
          ---------------------------
          1           1
          2           2
          3           3
          4           4
          5           5
          
          6 rows selected.

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47415  로그앵커 백업 시 경로가 비어있으면 비정상 종료할 수 있습니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **증상** : 로그앵커 백업 시 경로가 비어있으면 [ERR-11189 : The length of the path is zero.] 에러를 출력하도록 수정합니다.
    
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

### BUG-47424  { ? = call } 이 포함된 sql문을 escape처리하면서 StringIndexOutOfBoundsException 예외가 발생합니다.

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** :  { ? = call } 형태의 escape sql문이 정상적으로 실행되지
    않는 문제 수정

- **재현 방법**

  -   **재현 절차**

          CREATE OR REPLACE FUNCTION func
          (
            i1_in IN integer
          )      
          RETURN VARCHAR(30)     
          AS     
          RET_VALUE VARCHAR(30);     
          BEGIN     
                  SELECT '111' INTO RET_VALUE     
                  FROM dual;           
                  RETURN RET_VALUE;     
          END;
          sConn = getConnection("20300");
          sQuery = "{ ? = call func(?) }";
          // sQuery = "execute ? := func(?)";
          sCallableStmt = sConn.prepareCall(sQuery);
          sCallableStmt.registerOutParameter(1, Types.VARCHAR);
          sCallableStmt.setInt(2, 111);
          sCallableStmt.execute();
          sReturnValue = sCallableStmt.getString(1);
          System.out.println("RETURN VALUE FROM func: " + sReturnValue);

  - **수행 결과**

        java.lang.StringIndexOutOfBoundsException: String index out of range: 1
        	at java.lang.String.charAt(String.java:686)
        	at Altibase.jdbc.driver.util.AltiSqlProcessor.convertToNative(AltiSqlProcessor.java:243)
        	at Altibase.jdbc.driver.util.AltiSqlProcessor.porcessEscapeExpr(AltiSqlProcessor.java:181)
        	at Altibase.jdbc.driver.util.AltiSqlProcessor.processEscape(AltiSqlProcessor.java:133)
        	at Altibase.jdbc.driver.AltibasePreparedStatement.(AltibasePreparedStatement.java:85)
        	at Altibase.jdbc.driver.AltibaseCallableStatement.(AltibaseCallableStatement.java:46)
        	at Altibase.jdbc.driver.AltibaseConnection.prepareCall(AltibaseConnection.java:1212)
        	at FunctionCallTest.main(FunctionCallTest.java from InputFileObject:36)
        String index out of range: 1

  -   **예상 결과**

          RETURN VALUE FROM func: 111

-   **Workaround**

        use execute ? := instead of escape 

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47461  windows 2016에서 isql, iloader 로 파라미터의 일부가 잘리는 문제가 있습니다.

-   **module** : ut

-   **Category** : Portability

-   **재현 빈도** : Always

-   **증상** : windows 2016에서 isql, iloader 로 파라미터의 일부가 잘리는 문제를 수정합니다.
    

또한 altiProfile 소스파일의 encoding 문제로 인한 빌드 이슈가 있어서 수정하였습니다.
    
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
| 7.1.0.3.0        | 6.5.1                   | 8.7.1        | 7.1.7               | 7.4.5                        | 2.2.1            |

> Altibase 7.1 패치 버전별 히스토리는 [Version_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7_1_Version_Histories.md) 에서 확인할 수 있다.

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
> 않는다. 즉, 샤딩 버전이 다른 경우, 재구성해야 한다.

### 프로퍼티

추가/변경/삭제된 프로퍼티 없음

### 성능 뷰

추가/변경/삭제된 성능뷰 없음