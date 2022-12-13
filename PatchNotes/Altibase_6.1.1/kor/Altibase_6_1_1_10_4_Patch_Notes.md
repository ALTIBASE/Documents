Altibase 6.1.1.10.4 Patch Notes
=================================

<br/>

<br/>

# Table of Contents

- [New Features](#new-features)
  - [BUG-49927 Altibase CLI에서 연결 속성 TIMEOUT, CONNECTION\_TIMEOUT의 적용 범위를 설정하는 환경 변수 ALTIBASE\_CLI\_APPLY\_SEND\_TIMEOUT를 추가합니다.](#bug-49927altibase-cli%EC%97%90%EC%84%9C-%EC%97%B0%EA%B2%B0-%EC%86%8D%EC%84%B1-timeout-connection_timeout%EC%9D%98-%EC%A0%81%EC%9A%A9-%EB%B2%94%EC%9C%84%EB%A5%BC-%EC%84%A4%EC%A0%95%ED%95%98%EB%8A%94-%ED%99%98%EA%B2%BD-%EB%B3%80%EC%88%98-altibase_cli_apply_send_timeout%EB%A5%BC-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
- [Fixed Bugs](#fixed-bugs)
  - [BUG-49739 MERGE JOIN을 사용한 CREATE AS SELECT 문을 수행한 세션이 SESSION CLOSE로 강제 종료되지 않습니다.](#bug-49739merge-join%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%9C-create-as-select-%EB%AC%B8%EC%9D%84-%EC%88%98%ED%96%89%ED%95%9C-%EC%84%B8%EC%85%98%EC%9D%B4-session-close%EB%A1%9C-%EA%B0%95%EC%A0%9C-%EC%A2%85%EB%A3%8C%EB%90%98%EC%A7%80-%EC%95%8A%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-49827 \$ALTIBASE\_HOME/sample 아래의 APRE, CAPI, CHECKSERVER, SPATIAL, SQLCLI 샘플 코드를 ODBC 표준에 맞춰 수정합니다.](#bug-49827altibase_homesample-%EC%95%84%EB%9E%98%EC%9D%98-apre-capi-checkserver-spatial-sqlcli-%EC%83%98%ED%94%8C-%EC%BD%94%EB%93%9C%EB%A5%BC-odbc-%ED%91%9C%EC%A4%80%EC%97%90-%EB%A7%9E%EC%B6%B0-%EC%88%98%EC%A0%95%ED%95%A9%EB%8B%88%EB%8B%A4)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
  - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
  - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)



# New Features

### BUG-49927 Altibase CLI에서 연결 속성 TIMEOUT, CONNECTION\_TIMEOUT의 적용 범위를 설정하는 환경 변수 ALTIBASE\_CLI\_APPLY\_SEND\_TIMEOUT를 추가합니다.

#### module

`mm-cli`

#### Category

`Enhancement`

#### 설명

Altibase CLI에서 연결 속성 TIMEOUT, CONNECTION\_TIMEOUT의 적용 범위를 설정하는 환경 변수 ALTIBASE\_CLI\_APPLY\_SEND\_TIMEOUT를 추가합니다.

 이 환경 변수는 Altibase CLI에서 Altibase 서버로 연결을 요청하거나 질의 처리를 요청하는 과정에서 Altibase 외적인 문제로 무한 대기 현상이 발생하는 것을 방지하기 위해 제공합니다.

- **ALTIBASE\_CLI\_APPLY\_SEND\_TIMEOUT 환경 변수**

   Altibase CLI의 연결 속성 TIMEOUT, CONNECTION\_TIMEOUT의 적용 범위를 설정합니다. 값으로 on 또는 off를 설정할 수 있으며 기본값은 off입니다. 

  - **off** 

    - TIMEOUT 연결 속성

      Altibase 서버로 연결 요청 이후 Altibase 서버로부터 응답 시간에 대한 타임아웃을 설정합니다.

    - CONNECTION\_TIMEOUT

       Altibase 서버에 질의 처리 요청 이후 Altibase 서버로부터 응답 시간에 대한 타임아웃을 설정합니다.
  
  
    - **on**
  
      - TIMEOUT 연결 속성
  
        Altibase 서버로 연결 요청 이후 Altibase 서버로부터 응답 시간에 대한 타임아웃 뿐 아니라 연결 요청에 대한 타임아웃도 설정합니다. 
  
      - CONNECTION\_TIMEOUT 연결 속성
  
        Altibase 서버에 질의 처리 요청 이후 Altibase 서버로부터 응답 시간에 대한 타임아웃 뿐 아니라 질의 처리 요청에 대한 타임아웃도 설정합니다. 
  


 이 버그를 적용하려면 Altibase CLI 드라이버를 패치하고 환경 변수 설정 후 사용자 응용 프로그램을 시작해야 합니다. 

**Altibase CLI 드라이버 패치**

- libodbccli.a

- libodbccli\_sl.so

 **환경 변수 설정 방법**

 `export ALTIBASE_CLI_APPLY_SEND_TIMEOUT = on`



Fixed Bugs
==========

### BUG-49739 MERGE JOIN을 사용한 CREATE AS SELECT 문을 수행한 세션이 SESSION CLOSE로 강제 종료되지 않습니다.

#### module

`qp`

#### Category

`Functional Error`

#### 재현 빈도 

`Always`

#### 설명

MERGE JOIN을 사용한 CREATE AS SELECT 문을 수행한 세션이 SESSION CLOSE로 강제 종료되지 않는 현상을 수정합니다.

#### 재현 방법

-   **재현 절차**

    -   A 세션

        ~~~sql
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
        ~~~

    -   B 세션

        ~~~sql
        ALTER DATABASE database_name SESSION CLOSE session_id;
        ~~~

-   **수행 결과**

    테이블 생성 완료 후 세션 종료

-   **예상 결과**

    ```sql
    [ERR-01043 : The session has been closed by the server]
    ```

#### Workaround

`없음`

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-49827 \$ALTIBASE\_HOME/sample 아래의 APRE, CAPI, CHECKSERVER, SPATIAL, SQLCLI 샘플 코드를 ODBC 표준에 맞춰 수정합니다.

#### module

`mm`

#### Category

`Other`

#### 재현 빈도 

`Always`

#### 설명

\$ALTIBASE\_HOME/sample 아래의 APRE, CAPI, CHECKSERVER, SPATIAL, SQLCLI 샘플 코드를 ODBC 표준에 맞춰 수정합니다.

#### 재현 방법

-   **재현 절차**

-   **수행 결과**

-   **예상 결과**

#### Workaround

`없음`

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code



Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    6.1.1.10.4    |          6.1.1          |    5.14.1    |        5.6.3        |            6.1.1             |

> Altibase 6.1.1 패치 버전별 히스토리는 [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_6.1.1/Altibase_6_1_1_Version_Histories.md) 에서 확인할 수 있다.

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
