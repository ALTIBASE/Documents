<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  

- [Altibase 7.1.0.5.7 Patch Notes](#altibase-71057-patch-notes)
  - [New Features](#new-features)
    - [BUG-48427 Altibase .NET Data Provider에 실행 계획 조회 기능을 추가합니다.](#bug-48427altibase-net-data-provider%EC%97%90-%EC%8B%A4%ED%96%89-%EA%B3%84%ED%9A%8D-%EC%A1%B0%ED%9A%8C-%EA%B8%B0%EB%8A%A5%EC%9D%84-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-48431 deferred prepare 사용 시 불필요한 통신 프로토콜을 최적화하여 성능을 개선하였습니다.](#bug-48431deferred-prepare-%EC%82%AC%EC%9A%A9-%EC%8B%9C-%EB%B6%88%ED%95%84%EC%9A%94%ED%95%9C-%ED%86%B5%EC%8B%A0-%ED%94%84%EB%A1%9C%ED%86%A0%EC%BD%9C%EC%9D%84-%EC%B5%9C%EC%A0%81%ED%99%94%ED%95%98%EC%97%AC-%EC%84%B1%EB%8A%A5%EC%9D%84-%EA%B0%9C%EC%84%A0%ED%95%98%EC%98%80%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-48515 ACCESS_LIST 프로퍼티에서 동일 IP의 세션 수 제한 기능을 제공합니다.](#bug-48515access%5C_list-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0%EC%97%90%EC%84%9C-%EB%8F%99%EC%9D%BC-ip%EC%9D%98-%EC%84%B8%EC%85%98-%EC%88%98-%EC%A0%9C%ED%95%9C-%EA%B8%B0%EB%8A%A5%EC%9D%84-%EC%A0%9C%EA%B3%B5%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-48618 iSQL 커맨드 라인 옵션 -KEEP_SYSDBA 를 추가합니다.](#bug-48618isql-%EC%BB%A4%EB%A7%A8%EB%93%9C-%EB%9D%BC%EC%9D%B8-%EC%98%B5%EC%85%98--keep%5C_sysdba-%EB%A5%BC-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-49028 APRE C/C++ Precompiler와 aexport에 오프라인 이중화 메타 복제(Offline Option) 관련 구문을 추가합니다.](#bug-49028apre-cc-precompiler%EC%99%80-aexport%EC%97%90-%EC%98%A4%ED%94%84%EB%9D%BC%EC%9D%B8-%EC%9D%B4%EC%A4%91%ED%99%94-%EB%A9%94%ED%83%80-%EB%B3%B5%EC%A0%9Coffline-option-%EA%B4%80%EB%A0%A8-%EA%B5%AC%EB%AC%B8%EC%9D%84-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-49032 Altibase 이중화 환경에서 원격 서버의 이중화 관련 메타 테이블 정보를 확인할 수 있는 성능 뷰가 추가되었습니다.](#bug-49032altibase-%EC%9D%B4%EC%A4%91%ED%99%94-%ED%99%98%EA%B2%BD%EC%97%90%EC%84%9C-%EC%9B%90%EA%B2%A9-%EC%84%9C%EB%B2%84%EC%9D%98-%EC%9D%B4%EC%A4%91%ED%99%94-%EA%B4%80%EB%A0%A8-%EB%A9%94%ED%83%80-%ED%85%8C%EC%9D%B4%EB%B8%94-%EC%A0%95%EB%B3%B4%EB%A5%BC-%ED%99%95%EC%9D%B8%ED%95%A0-%EC%88%98-%EC%9E%88%EB%8A%94-%EC%84%B1%EB%8A%A5-%EB%B7%B0%EA%B0%80-%EC%B6%94%EA%B0%80%EB%90%98%EC%97%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-48460 DISCARD 상태의 테이블스페이스로 인해 Restart Recovery 수행 중 언두 단계에서 Altibase 서버 구동이 실패합니다.](#bug-48460discard-%EC%83%81%ED%83%9C%EC%9D%98-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%8A%A4%ED%8E%98%EC%9D%B4%EC%8A%A4%EB%A1%9C-%EC%9D%B8%ED%95%B4-restart-recovery-%EC%88%98%ED%96%89-%EC%A4%91-%EC%96%B8%EB%91%90-%EB%8B%A8%EA%B3%84%EC%97%90%EC%84%9C-altibase-%EC%84%9C%EB%B2%84-%EA%B5%AC%EB%8F%99%EC%9D%B4-%EC%8B%A4%ED%8C%A8%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-48523 세션 종료 시 statement 객체가 정리되지 않은 경우 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-48523%EC%84%B8%EC%85%98-%EC%A2%85%EB%A3%8C-%EC%8B%9C-statement-%EA%B0%9D%EC%B2%B4%EA%B0%80-%EC%A0%95%EB%A6%AC%EB%90%98%EC%A7%80-%EC%95%8A%EC%9D%80-%EA%B2%BD%EC%9A%B0-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-49029 COUNT KEEP 함수 사용 시 OVER 절이 생략된 경우 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-49029count-keep-%ED%95%A8%EC%88%98-%EC%82%AC%EC%9A%A9-%EC%8B%9C-over-%EC%A0%88%EC%9D%B4-%EC%83%9D%EB%9E%B5%EB%90%9C-%EA%B2%BD%EC%9A%B0-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-49031 OFFLINE 상태인 메모리 테이블스페이스가 존재하는 경우 V$SNAPSHOT 조회 시 Altibase 서버가 비정상 종료합니다.](#bug-49031offline-%EC%83%81%ED%83%9C%EC%9D%B8-%EB%A9%94%EB%AA%A8%EB%A6%AC-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%8A%A4%ED%8E%98%EC%9D%B4%EC%8A%A4%EA%B0%80-%EC%A1%B4%EC%9E%AC%ED%95%98%EB%8A%94-%EA%B2%BD%EC%9A%B0-v%5Csnapshot-%EC%A1%B0%ED%9A%8C-%EC%8B%9C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-49060 altibase_ipc.log 파일의 권한을 -rw-r--r-- 으로 변경합니다.](#bug-49060altibase%5C_ipclog-%ED%8C%8C%EC%9D%BC%EC%9D%98-%EA%B6%8C%ED%95%9C%EC%9D%84--rw-r--r---%EC%9C%BC%EB%A1%9C-%EB%B3%80%EA%B2%BD%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-49061 syspassword 파일의 권한을 -rw-r--r-- 으로 변경합니다.](#bug-49061syspassword-%ED%8C%8C%EC%9D%BC%EC%9D%98-%EA%B6%8C%ED%95%9C%EC%9D%84--rw-r--r---%EC%9C%BC%EB%A1%9C-%EB%B3%80%EA%B2%BD%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-49062 조회 트랜잭션에서 시퀀스 사용 시 UTRANS_TIMEOUT 이 발생하며 세션이 종료됩니다.](#bug-49062%EC%A1%B0%ED%9A%8C-%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98%EC%97%90%EC%84%9C-%EC%8B%9C%ED%80%80%EC%8A%A4-%EC%82%AC%EC%9A%A9-%EC%8B%9C-utrans%5C_timeout-%EC%9D%B4-%EB%B0%9C%EC%83%9D%ED%95%98%EB%A9%B0-%EC%84%B8%EC%85%98%EC%9D%B4-%EC%A2%85%EB%A3%8C%EB%90%A9%EB%8B%88%EB%8B%A4)
    - [BUG-49071 이중화 객체에 이중화 대상 추가 시 USER 이름이 잘못된 경우 알맞지 않은 에러 메시지가 발생합니다.](#bug-49071%EC%9D%B4%EC%A4%91%ED%99%94-%EA%B0%9D%EC%B2%B4%EC%97%90-%EC%9D%B4%EC%A4%91%ED%99%94-%EB%8C%80%EC%83%81-%EC%B6%94%EA%B0%80-%EC%8B%9C-user-%EC%9D%B4%EB%A6%84%EC%9D%B4-%EC%9E%98%EB%AA%BB%EB%90%9C-%EA%B2%BD%EC%9A%B0-%EC%95%8C%EB%A7%9E%EC%A7%80-%EC%95%8A%EC%9D%80-%EC%97%90%EB%9F%AC-%EB%A9%94%EC%8B%9C%EC%A7%80%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-49077 트랜잭션 고립화 수준(isolation level)이 REPEATABLE READ 인 경우 COUNT(*) 수행 시 ERR-0109E : Internal server error. 에러가 발생합니다.](#bug-49077%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98-%EA%B3%A0%EB%A6%BD%ED%99%94-%EC%88%98%EC%A4%80isolation-level%EC%9D%B4-repeatable-read-%EC%9D%B8-%EA%B2%BD%EC%9A%B0-count%5C-%EC%88%98%ED%96%89-%EC%8B%9C-err-0109e--internal-server-error-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-49082 BUG-48523 반영 이후 Altibase 서버 비정상 종료 현상이 발생하여 BUG-48523을 롤백합니다.](#bug-49082bug-48523-%EB%B0%98%EC%98%81-%EC%9D%B4%ED%9B%84-altibase-%EC%84%9C%EB%B2%84-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C-%ED%98%84%EC%83%81%EC%9D%B4-%EB%B0%9C%EC%83%9D%ED%95%98%EC%97%AC-bug-48523%EC%9D%84-%EB%A1%A4%EB%B0%B1%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-49087 JDBC 커넥션 객체를 close 할 때 예외가 발생한 경우 socket fd(file descriptor)가 정리되지 않고 남아있는 현상이 있습니다.](#bug-49087jdbc-%EC%BB%A4%EB%84%A5%EC%85%98-%EA%B0%9D%EC%B2%B4%EB%A5%BC-close-%ED%95%A0-%EB%95%8C-%EC%98%88%EC%99%B8%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%9C-%EA%B2%BD%EC%9A%B0-socket-fdfile-descriptor%EA%B0%80-%EC%A0%95%EB%A6%AC%EB%90%98%EC%A7%80-%EC%95%8A%EA%B3%A0-%EB%82%A8%EC%95%84%EC%9E%88%EB%8A%94-%ED%98%84%EC%83%81%EC%9D%B4-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-49095 Materialized view에 _PROWID 예약어를 사용한 경우 Altibase 서버가 비정상 종료합니다.](#bug-49095materialized-view%EC%97%90-%5C_prowid-%EC%98%88%EC%95%BD%EC%96%B4%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%9C-%EA%B2%BD%EC%9A%B0-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-49106 UNION 절을 사용하여 생성한 뷰 테이블을 DELETE 할 경우 Altibase 서버가 비정상 종료합니다.](#bug-49106union-%EC%A0%88%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%98%EC%97%AC-%EC%83%9D%EC%84%B1%ED%95%9C-%EB%B7%B0-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%9D%84-delete-%ED%95%A0-%EA%B2%BD%EC%9A%B0-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-49107 DISK TEMP TABLE에서 HASH 연산 시 특정 상황에서 Altibase 서버가 비정상 종료합니다.](#bug-49107disk-temp-table%EC%97%90%EC%84%9C-hash-%EC%97%B0%EC%82%B0-%EC%8B%9C-%ED%8A%B9%EC%A0%95-%EC%83%81%ED%99%A9%EC%97%90%EC%84%9C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-49109 휘발성 테이블에서 가비지 콜렉션 쓰레드(Ager) 동작 중 발생한 Altibase 서버 비정상 종료 원인 분석을 위해 트레이스 로그를 추가합니다.](#bug-49109%ED%9C%98%EB%B0%9C%EC%84%B1-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90%EC%84%9C-%EA%B0%80%EB%B9%84%EC%A7%80-%EC%BD%9C%EB%A0%89%EC%85%98-%EC%93%B0%EB%A0%88%EB%93%9Cager-%EB%8F%99%EC%9E%91-%EC%A4%91-%EB%B0%9C%EC%83%9D%ED%95%9C-altibase-%EC%84%9C%EB%B2%84-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C-%EC%9B%90%EC%9D%B8-%EB%B6%84%EC%84%9D%EC%9D%84-%EC%9C%84%ED%95%B4-%ED%8A%B8%EB%A0%88%EC%9D%B4%EC%8A%A4-%EB%A1%9C%EA%B7%B8%EB%A5%BC-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Altibase 7.1.0.5.7 Patch Notes
==============================

New Features
------------

### BUG-48427 Altibase .NET Data Provider에 실행 계획 조회 기능을 추가합니다.

-   **module** : ux-win-adonet

-   **Category** : Enhancement

-   **재현 빈도** : Always

- **설명** : Altibase .NET Data Provider에 실행 계획 조회 기능을 추가합니다.

  이 버그를 반영하려면 Altibase.Data.AltibaseClient.dll 을 패치하고 응용 프로그램을 재 컴파일해야 합니다. 

  **사용 방법**

     ADO.net 에서 실행 계획을 조회하기 위해서는 비 표준 인터페이스를 사용해야 한다. 

  1. AltibaseConnection 객체의 비 표준 인터페이스를 사용해 실행 계획 조회 기능을 셋팅한다. 만약 Connection이 ADO.net 표준 인터페이스인 DbConnection 일 경우 AltibaseConnection으로 캐스팅해야 한다.

     ```c#
     DbConnection sConn = new AltibaseConnection();
     ((AltibaseConnection)sConn).ExplainPlan = ExplainPlan.PLAN_ON;
     ```

     이 때 ExplainPlan 함수의 매개변수로는 ExplainPlan enum 값이 들어가야 하며 enum 값의 종류는 다음과 같다.

     - ExplainPlan.PLAN_OFF

     - ExplainPlan.PLAN_ON

     - ExplainPlan.PLAN_ONLY

  2. AltibaseCommand 객체의 비 표준 인터페이스를 이용해 실행 계획 문자열을 가져온다.

     ```c#
     DbCommand sCommand = sConn.CreateCommand();
     sCommand.CommandText = aQuery;
     sCommand.Prepare();
     sCommand.ExecuteReader();
     string sPlanText = ((AltibaseCommand)sCommand).GetExplainPlan();
     Console.WriteLine(sPlanText);
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

### BUG-48431 deferred prepare 사용 시 불필요한 통신 프로토콜을 최적화하여 성능을 개선하였습니다.

-   **module** : mm-jdbc

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : deferred prepare 사용 시 불필요한 통신 프로토콜을 최적화하여 성능을 개선하였습니다. 이 버그를 반하려면 Altibase JDBC Driver 패치 및 응용 프로그램 재컴파일 해야 합니다. 
    
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

### BUG-48515 ACCESS_LIST 프로퍼티에서 동일 IP의 세션 수 제한 기능을 제공합니다.

-   **module** : mm

-   **Category** : Functionality

-   **재현 빈도** : Always

- **설명** : 동일 IP 의 세션 수를 제한하는 기능을 제공하기 위해 ACCESS_LIST 프로퍼티에 limit 항목을 추가합니다. 

  ACCESS_LIST = operation, address, mask, **[limit]**

  address 에서 접속한 세션 수가 limit을 초과한 경우 신규 접속을 허용하지 않습니다.
  이 경우, Altibase 클라이언트 측에서는 ERR-91015 : Communication failure. 에러가 발생하며 접속이 실패하고 Altibase 서버 측에서는 altibase_boot.log에 아래와 같은 메시지가 발생합니다.

  ```bash
  ERR-410f0(errno=0) New connection try exceeds ACL limit: ( IP :192.168.1.203, ACL: 192.168.1.203, Limit : 2, Connected : 2 )
  Dispatcher callback failed
  ```

- **재현 방법**

  -   **재현 절차**
  -   **수행 결과**
  -   **예상 결과**

-   **Workaround**

- **변경사항**

  - Performance view
    - V$ACCESS_LIST 변경

      LIMIT, CONNECTED 컬럼이 추가되었습니다. 

      - LIMIT

        ACCESS_LIST에 명시된 접속 가능한 IP 주소 영역에서 허용되는
        최대 접속 세션 개수.

      - CONNECTED
         ACCESS_LIST에 해당하는 현재 접속된 세션 개수

      보다 자세한 설명은 [General Reference Manual](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_3.md#vaccess_list)을 참고해주세요.

  -   Property
      -   ACCESS_LIST 변경

          limit 항목이 추가되었습니다.

          ACCESS_LIST = operation, address, mask, **[limit]**

          limit 은 선택 입력 항목으로 ACCESS_LIST에 명시된 접속 가능한 IP 주소 영역에서 허용되는 최대 접속 세션 개수를 지정합니다. 

          보다 자세한 설명은 [General Reference Manual](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_2.md#access_list)을 참고해주세요. 

  - Compile Option

  - Error Code

    설정한 세션 수를 초과하여 접속을 시도할 경우 아래와 같은 에러 메시지가 발생합니다. 

    ```bash
    mmERR_ABORT_IP_ACL_CONNECT_OVER = New connection try exceeds ACL limit: ( IP : <0%s>, ACL: <1%s>, Limit : <2%d>, Connected : <3%d> )
    # *Cause: New connection try aborted because it exceeds access control list (ACL) limit.
    # *Action: Change the limit value of the ACCESS_LIST.
    ```

    

### BUG-48618 iSQL 커맨드 라인 옵션 -KEEP_SYSDBA 를 추가합니다.

-   **module** : ux-isql

-   **Category** : Usability

-   **재현 빈도** : Always

-   **설명** : iSQL에서 sysdba 모드로 Altibase 서버에 접속 시 관리자 모드를 유지하기 위한 -KEEP_SYSDBA 옵션을 추가합니다. sysdba 모드에서 startup service 를 수행할 때, -KEEP_SYSDBA 옵션을 사용하지 않으면 관리자 모드에서 일반 사용자 모드로 변경되고 -KEEP_SYSDBA 옵션을 사용하면 관리자 모드가 유지됩니다.
    
    이 버그를 반영하려면 iSQL 을 패치해야 합니다.     

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

### BUG-49028 APRE C/C++ Precompiler와 aexport에 오프라인 이중화 메타 복제(Offline Option) 관련 구문을 추가합니다.

-   **module** : rp

-   **Category** : Other

-   **재현 빈도** : Always

-   **설명** : APRE C/C++ Precompiler와 aexport에 오프라인 이중화 메타 복제(Offline Option) 관련 구문을 추가합니다. 이 버그를 반영하려면 apre 와 aexport 를 패치하고 apre 응용 프로그램을 재컴파일 해야 합니다. 
    
    CREATE REPLICATION ala_replication_name FOR ANALYSIS OPTIONS **META_LOGGING**
    
    ​          WITH 'remote_host_ip', remote_host_port_no 
    
    ​          FROM user_name.table_name TO user_name.table_name;          
    
    ALTER REPLICATION ala_replication_name **BUILD OFFLINE META [AT SN(sn)]**;
    
    ALTER REPLICATION ala_replication_name **RESET OFFLINE META**;

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

### BUG-49032 Altibase 이중화 환경에서 원격 서버의 이중화 관련 메타 테이블 정보를 확인할 수 있는 성능 뷰가 추가되었습니다.

-   **module** : rp

-   **Category** : Usability

-   **재현 빈도** : Always

-   **설명** : Altibase 이중화 환경에서 원격 서버의 이중화 관련 메타 테이블 정보를 확인할 수 있는 성능 뷰 6가지가 추가되었습니다. 이중화가 정상 동작하지 않을 때 메타 정보 오류 여부를 확인할 수 있습니다. 이 성능 뷰들은 수신 쓰레드(Receiver Thread)가 수행된 서버에서만 조회할 수 있습니다.
    
    - V$REPL_REMOTE_META_REPLICATIONS
    - V$REPL_REMOTE_META_ITEMS
    - V$REPL_REMOTE_META_COLUMNS
    - V$REPL_REMOTE_META_INDEX_COLUMNS
    - V$REPL_REMOTE_META_INDICES
    - V$REPL_REMOTE_META_CHECKS       
    
-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

- **변경사항**

    - Performance view

      원격 서버의 이중화 관련 메타 테이블 정보를 확인할 수 있는 성능 뷰 6가지가 추가되었습니다.

      - [V$REPL_REMOTE_META_REPLICATIONS](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_4.md#vrepl_remote_meta_replications)
        
        원격 서버의 이중화 관련 정보를 기록하고 있는 SYS_REPLICATIONS_ 메타 테이블의 정보를 보여준다.
        
      - [V$REPL_REMOTE_META_ITEMS](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_4.md#vrepl_remote_meta_items)

        원격 서버의 이중화 대상 테이블에 관련된 정보를 가진 SYS_REPL_ITEMS_ 메타 테이블 정보를 보여준다.

      - [V$REPL_REMOTE_META_COLUMNS](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_4.md#vrepl_remote_meta_columns)

        원격 서버의 이중화 송신 쓰레드가 현재 복제중인 이중화 대상 칼럼의 정보를 가진 SYS_REPL_OLD_COLUMNS_ 메타 테이블 정보를 보여 준다.

      - [V$REPL_REMOTE_META_INDEX_COLUMNS](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_4.md#vrepl_remote_meta_index_columns)

        원격 서버의 이중화 송신 쓰레드가 현재 사용 중인 이중화 대상 인덱스 칼럼의 정보를 가진 SYS_REPL_OLD_INDEX_COLUMNS_ 메타 테이블 정보를 보여 준다.

      - [V$REPL_REMOTE_META_INDICES](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_4.md#vrepl_remote_meta_indices)

        원격 서버의 이중화 송신 쓰레드가 현재 복제 중인 이중화 대상 인덱스의 정보를 가진 SYS_REPL_OLD_INDICES_ 메타 테이블의 정보를 보여 준다.

      - [V$REPL_REMOTE_META_CHECKS](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_4.md#vrepl_remote_meta_checks)

        원격 서버의 이중화 송신 쓰레드가 현재 복제 중인 이중화 테이블의 제약 조건에 관한 정보를 보여 준다.

    -   Property
        
    -   Compile Option
        
    -   Error Code

Fixed Bugs
----------

### BUG-48460 DISCARD 상태의 테이블스페이스로 인해 Restart Recovery 수행 중 언두 단계에서 Altibase 서버 구동이 실패합니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Rare

-   **설명** : DISCARD 상태의 테이블스페이스로 인해 Restart Recovery 수행 중 언두 단계에서 Altibase 서버 구동이 실패하는 현상을 수정합니다.
    
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

### BUG-48523 세션 종료 시 statement 객체가 정리되지 않은 경우 Altibase 서버가 비정상 종료할 수 있습니다.

-   **module** : sm_transaction

-   **Category** : Fatal

-   **재현 빈도** : Rare

-   **설명** : 세션 종료 시 statement 객체가 정리되지 않은 경우 Altibase 서버가 비정상 종료 현상을 개선합니다.
    
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

### BUG-49029 COUNT KEEP 함수 사용 시 OVER 절이 생략된 경우 Altibase 서버가 비정상 종료할 수 있습니다.

-   **module** : qp-select-pvo

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : COUNT KEEP 함수 사용 시 OVER 절이 생략된 경우 예외 처리 부족으로 Altibase 서버가 비정상 종료하는 현상을 수정하였습니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    DROP TABLE BUG_49029;
    CREATE TABLE BUG_49029 ( I1 VARCHAR(1000), I2 VARCHAR(1000), I3 VARCHAR(2000), PRIMARY KEY(I1));
    
    SELECT COUNT(I1) KEEP ( DENSE_RANK FIRST ORDER BY I2, I3 NULLS FIRST) 
      FROM BUG_49029;
    ```

  - **수행 결과**

    ```
    ERR-31455 : Failed to work because an internal exception occurred from an OS.[Contact Altibase's Support Center] 에러가 발생하거나
    Altibase 서버 비정상 종료
    ```

  -   **예상 결과**

      ```sql
      COUNT(I1)KEEP(DENSE_RANKFIRSTORDERBYI2,I3N 
      ---------------------------------------------
      0                    
      1 row selected.
      ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49031 OFFLINE 상태인 메모리 테이블스페이스가 존재하는 경우 V$SNAPSHOT 조회 시 Altibase 서버가 비정상 종료합니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : OFFLINE 상태인 메모리 테이블스페이스가 존재하는 경우 V$SNAPSHOT 조회 시 Altibase 서버 비정상 종료 현상을 수정합니다.
    
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

### BUG-49060 altibase_ipc.log 파일의 권한을 -rw-r--r-- 으로 변경합니다.

-   **module** : cm-ipc

-   **Category** : Maintainability

-   **재현 빈도** : Always

-   **설명** : 데이터베이스 보안 강화를 위해 $ALTIBASE_HOME/trc/altibase_ipc.log 파일의 권한을 rw-rw-rw-
    에서 -rw-r--r-- 으로 변경합니다.
    
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

### BUG-49061 syspassword 파일의 권한을 -rw-r--r-- 으로 변경합니다.

-   **module** : ux-isql

-   **Category** : Maintainability

-   **재현 빈도** : Always

-   **설명** : 데이터베이스 보안 강화를 위해 $ALTIBASE_HOME/conf/syspassword 파일의 권한을 rw-rw-rw-에서
    -rw-r--r-- 으로 변경합니다.
    
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

### BUG-49062 조회 트랜잭션에서 시퀀스 사용 시 UTRANS_TIMEOUT 이 발생하며 세션이 종료됩니다.

-   **module** : sm

-   **Category** : Functional Error

-   **재현 빈도** : Rare

-   **설명** : 시퀀스 객체 생성/변경에서 CACHE 절을 사용한 경우 시퀀스 사용 시 내부적으로 UPDATE 문을 수행합니다. 이로 인해 사용자가 수행한 조회 트랜잭션이 변경 트랜잭션으로 변경되어 UTRANS_TIMEOUT 에 걸려 세션이 종료하는 현상입니다. 이 현상을 개선하기 위해 \__SEQ_CACHE_UPT_TX_ENABLE 프로퍼티를 추가합니다. 
    
    \__SEQ_CACHE_UPT_TX_ENABLE = 0 은 기존과 같이 사용자의 조회 트랜잭션이 변경 트랜잭션으로 바뀌고

    __SEQ_CACHE_UPT_TX_ENABLE = 1 은 별도 트랜잭션으로 관리하여 사용자 트랜잭션에 영향을 주지 않습니다. 
    
-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

- **변경사항**

     -   Performance view
     - Property
       -   __SEQ_CACHE_UPT_TX_ENABLE 프로퍼티 추가

           -   설명

               시퀀스 값 캐시 과정에서 내부적으로 수행하는 UPDATE 문에 대한 처리 동작을 제어한다. 

               0 : 별도의 트랜잭션으로 관리하지 않는다. 사용자 트랜잭션에 영향을 준다.

               1 : 별도의 트랜잭션으로 관리한다. 사용자 트랜잭션에 영향을 주지 않는다.
               
           - 기본값 : 0
           
           - 속성 : 읽기 전용, 비공개

     - Compile Option
     - Error Code

### BUG-49071 이중화 객체에 이중화 대상 추가 시 USER 이름이 잘못된 경우 알맞지 않은 에러 메시지가 발생합니다.

-   **module** : rp

-   **Category** : Message Error

-   **재현 빈도** : Always

-   **설명** : 이중화 객체에 이중화 대상 테이블 추가 시 USER 이름이 잘못된 경우 The primary key column count of the replicated table does not match 와 같이 적합하지 않은 에러 메시지가 발생하여 The user name of the replicated table's owner does not match 메시지로 수정하였습니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    CREATE TABLE T1 (I1 INTEGER PRIMARY KEY, I2 INTEGER);
    CREATE TABLE T2 (I1 INTEGER, I2 INTEGER);
    ALTER TABLE T2 ADD CONSTRAINT PK_T2 PRIMARY KEY (I1, I2);
    CREATE REPLICATION REP1 WITH '127.0.0.1', 27172 FROM SYS.T1 TO SYS.T1;
    ALTER REPLICATION REP1 ADD TABLE FROM SYS.T2 TO SCOTT.T2;
    ALTER REPLICATION REP1 START;
    ```

  - **수행 결과**

    ```sql
    ERR-6100D : [Sender] Failed to handshake with the peer server (The primary key column count of the replicated table does not match [T1(1):T2(2)].)
    ```

  -   **예상 결과**

      ```sql
      ERR-6100D : [Sender] Failed to handshake with the peer server (The user name of the replicated table's owner does not match [T2(SYS):T2(SCOTT)].)
      ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49077 트랜잭션 고립화 수준(isolation level)이 REPEATABLE READ 인 경우 COUNT(*) 수행 시 ERR-0109E : Internal server error. 에러가 발생합니다.

-   **module** : qp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 트랜잭션 고립화 수준(isolation level)이 REPEATABLE READ 인 경우 COUNT(*) 수행 시 ERR-0109E : Internal server error. 에러가 발생하는 현상을 수정합니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    CREATE TABLE BUG_49077 ( IDX INTEGER , PARENT_IDX INTEGER ) TABLESPACE SYS_TBS_DISK_DATA;
    INSERT INTO BUG_49077 VALUES( 1, 0 );
    INSERT INTO BUG_49077 VALUES( 1, 0 );
    INSERT INTO BUG_49077 VALUES( 1, 0 );
    INSERT INTO BUG_49077 VALUES( 1, 0 );
    INSERT INTO BUG_49077 VALUES( 1, 0 );
    AUTOCOMMIT OFF;
    SET TRANSACTION ISOLATION LEVEL REPEATABLE READ;
    SELECT COUNT ( * ) FROM BUG_49077 WHERE IDX = 1;
    COMMIT;
    AUTOCOMMIT ON;
    ```

  - **수행 결과**

    ```sql
    iSQL> SELECT COUNT ( * ) FROM BUG_49077 WHERE IDX = 1;
    [ERR-0109E : Internal server error.]
    ```

  -   **예상 결과**

      ```sql
      iSQL> SELECT COUNT ( * ) FROM BUG_49077 WHERE IDX = 1;
      COUNT                
      -----------------------
      5                    
      1 row selected.
      ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49082 BUG-48523 반영 이후 Altibase 서버 비정상 종료 현상이 발생하여 BUG-48523을 롤백합니다.

-   **module** : sm_transaction

-   **Category** : Fatal

-   **재현 빈도** : Rare

-   **설명** : BUG-48523 반영 이후 Altibase 서버 비정상 종료 현상이 발생하여 BUG-48523을 롤백합니다.
    
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

### BUG-49087 JDBC 커넥션 객체를 close 할 때 예외가 발생한 경우 socket fd(file descriptor)가 정리되지 않고 남아있는 현상이 있습니다.

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : JDBC 커넥션 객체를 close 할 때 예외가 발생한 경우 socket fd(file descriptor)가 정리되지 않고 남아있는 현상을 수정하였습니다. 이 버그를 반영하려면 Altibase JDBC Driver 패치 및 응용 프로그램 재컴파일을 해야합니다. 
    
- **재현 방법**

  - **재현 절차**

    ```java
    AltibaseConnection sConn = (AltibaseConnection)getConnection("21165"); 
                       // 최초 접속 성공
    try
    {
        sConn.close(); // close 도중 예외 발생
    }
    catch (SQLException aEx)
    {
        System.out.println(aEx.getMessage());
    }
    CmChannel sChannel = sConn.channel();
    System.out.println("Socket FD ===>" + sChannel.getSocketFD()); 
                       // socket이 정리되지 않고 socket fd가 남아있음
    ```

  - **수행 결과**

    ```java
    Communication link failure: There was no response from the server, and the channel has reached end-of-stream.
    Socket FD ===>42
    ```

  -   **예상 결과**

      ```java
      Communication link failure: There was no response from the server, and the channel has reached end-of-stream.
      Exception in thread "main" java.sql.SQLException: Connection already closed.
      ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49095 Materialized view에 _PROWID 예약어를 사용한 경우 Altibase 서버가 비정상 종료합니다.

-   **module** : qp-dml-pvo

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : Materialized view에서 _PROWID 예약어는 사용할 수 없으므로 ERR-31385 : _PROWID is not supported. 에러 메시지가 발생하도록 수정하였습니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    CREATE TABLE T1 (I1 INT, I2 INT);
    WITH W3 
    AS ( SELECT /*+ */ _PROWID AS i2 FROM T1 )
    SELECT E.I2, F.I2 FROM W3 E, W3 F;
    ```

  - **수행 결과**

    ```sql
    ERR-91015 : Communication failure. 발생하며 Altibase 서버가 비정상 종료하거나 
    ERR-31455 : Failed to work because an internal exception occurred from an OS.[Contact Altibase's Support Center] 에러 메시지가 발생합니다. 
    ```

  -   **예상 결과**

      _PROWID 예약어를 사용할 수 없는 문장이므로 에러 메시지를 출력해야 합니다. 
      
      ```sql
      ERR-31385 : _PROWID is not supported.
      ```

- **Workaround**

  NO_MATERIALIZE 힌트를 사용하여 Altibase 서버 비정상 종료 현상을 회피할 수 있습니다. 

  ```sql
  WITH W3 
  AS ( SELECT /*+ NO_MATERIALIZE */ _PROWID AS i2 FROM T1 )
  SELECT E.I2, F.I2 FROM W3 E, W3 F;
  I2                   I2                   
  ---------------------------------------------
  592710729729         592710729729         
  1 row selected.
  ```

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49106 UNION 절을 사용하여 생성한 뷰 테이블을 DELETE 할 경우 Altibase 서버가 비정상 종료합니다.

-   **module** : qp

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : UNION 절을 사용한 뷰 테이블은 DELETE 할 수 없으므로 ERR-313A4 : Cannot modify a column for a non key-preserved table 에러 메시지가 발생하도록 수정하였습니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    CREATE TABLE M2 ( I1 INTEGER, I2 INTEGER );
    CREATE OR REPLACE VIEW V1 
    AS 
    SELECT * FROM M2 UNION SELECT * FROM M2;
    
    DELETE FROM V1 WHERE T2_I2=4;
    ```

  - **수행 결과**

    ```sql
    ERR-91015 : Communication failure. 발생하며 Altibase 서버 비정상 종료하거나 
    ERR-31455 : Failed to work because an internal exception occurred from an OS.[Contact Altibase's Support Center] 에러 메시지가 발생합니다. 
    ```

  -   **예상 결과**

      ```sql
      ERR-313A4 : Cannot modify a column for a non key-preserved table
      ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49107 DISK TEMP TABLE에서 HASH 연산 시 특정 상황에서 Altibase 서버가 비정상 종료합니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Unknown

-   **설명** : DISK TEMP TABLE에서 HASH 연산 시 특정 상황에서 Altibase 서버가 비정상 종료하는 현상을 회피하고 원인 분석을 위한 로그를 추가합니다. 이 버그 현상 발생 시 altibase_dump.log 에 아래와 같은 로그가 남게 됩니다.
    
    ```bash
    DUMP HASH WASEGMENT:
    WASegPtr              : 0x7fb19e2031d8
    SpaceID               : 4
    Type                  : 1 HASH
    HashSlotCount         : 65536
    InMemory              : OutMemory
    Unique                : 0
    OpenCursorType        : 0
    EndWPID               : 384
    InsertGroup BeginWPID : 128
    InsertGroup EndWPID   : 320
    InsertGroup ReuseWPID : 131
    FetchGroup BeginWPID  : 384
    FetchGroup EndWPID    : 384
    FetchGroup ReuseWPID  : 384
    SubHashGroup BeginWPID : 320
    SubHashGroup EndWPID   : 384
    SubHashGroup ReuseWPID : 352
    WAExtentListCount     : 8
    MaxWAExtentCount      : 6
    AllocWAPageCount      : 384
    NPageHashBucketCnt    : 384
    NPageCount            : 386
    SubHashPageCount      : 64
    SubHashBuildCount     : 3
    HashSlotPageCount     : 128
    ```

-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
        -   __TEMPDUMP_ENABLE 프로퍼티 삭제

        -   __TEMPDUMP_LEVEL 프로퍼티 추가

            -   설명

                DISK TEMP TABLE 관련 로깅 여부 및 로그 레벨을 설정합니다. 

                0 : 로깅 비활성화. 

                1 : 로깅 활성화. 디스크 템프 테이블 헤더 및 상태 정보 출력

            - 기본값 : 0 
            
            - 속성 : 변경 가능, 비공개
        
    -   Compile Option
        
    - Error Code

### BUG-49109 휘발성 테이블에서 가비지 콜렉션 쓰레드(Ager) 동작 중 발생한 Altibase 서버 비정상 종료 원인 분석을 위해 트레이스 로그를 추가합니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Rare

-   **설명** : 휘발성 테이블에서 가비지 콜렉션 쓰레드(Ager) 동작 중 발생한 Altibase 서버 비정상 종료 원인 분석을 위해 트레이스 로그를 추가합니다.
    
    본 버그로 인한 Altibase 서버 비정상 종료 상황 발생 시 altibase_error.log에 아래 형태의 로그를 출력합니다.

    ```bash
    smpFixedPageList::setFreeSlot
    CreateSCN    : ...
    LimitSCN      : ...
    NextOIDIsNULL : ...
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
-------

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    7.1.0.5.7     |          6.5.1          |    8.9.1     |        7.1.7        |            7.4.6             |

> Altibase 7.1 패치 버전별 히스토리는 [Version_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7_1_Version_Histories.md)에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

> 패치를 롤백하려는 경우, [메타다운그레이드](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Installation.md#%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9Cmeta-downgrade)를 참고한다.

#### CM protocol Version

통신 프로토콜 버전은 변경되지 않았다.

#### Replication protocol Version

Replication 프로토콜 버전은 변경되지 않았다.

### 프로퍼티

#### 추가된 프로퍼티

- __SEQ_CACHE_UPT_TX_ENABLE
- __TEMPDUMP_LEVEL

#### 변경된 프로퍼티

- [ACCESS_LIST](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_2.md#access_list)

#### 삭제된 프로퍼티

- __TEMPDUMP_ENABLE

### 성능 뷰

#### 추가된 성능 뷰

- [V$REPL_REMOTE_META_REPLICATIONS](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_4.md#vrepl_remote_meta_replications)

- [V$REPL_REMOTE_META_ITEMS](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_4.md#vrepl_remote_meta_items)

- [V$REPL_REMOTE_META_COLUMNS](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_4.md#vrepl_remote_meta_columns)

- [V$REPL_REMOTE_META_INDEX_COLUMNS](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_4.md#vrepl_remote_meta_index_columns)

- [V$REPL_REMOTE_META_INDICES](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_4.md#vrepl_remote_meta_indices)

- [V$REPL_REMOTE_META_CHECKS](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_4.md#vrepl_remote_meta_checks)

#### 변경된 성능 뷰

- [V$ACCESS_LIST](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_3.md#vaccess_list)

#### 삭제된 성능 뷰
