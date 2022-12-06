# Altibase 6.3.1.12.5 Patch Notes

<br/>

<br/>



# Table of Contents 

- [New Features](#new-features)
  - [BUG-49776 IPC 및 IPCDA 채널을 생성하는 데 필요한 공유 메모리와 세마포어의 키를 사용자가 정의한 값으로 설정하는 기능을 추가합니다.](#bug-49776ipc-%EB%B0%8F-ipcda-%EC%B1%84%EB%84%90%EC%9D%84-%EC%83%9D%EC%84%B1%ED%95%98%EB%8A%94-%EB%8D%B0-%ED%95%84%EC%9A%94%ED%95%9C-%EA%B3%B5%EC%9C%A0-%EB%A9%94%EB%AA%A8%EB%A6%AC%EC%99%80-%EC%84%B8%EB%A7%88%ED%8F%AC%EC%96%B4%EC%9D%98-%ED%82%A4%EB%A5%BC-%EC%82%AC%EC%9A%A9%EC%9E%90%EA%B0%80-%EC%A0%95%EC%9D%98%ED%95%9C-%EA%B0%92%EC%9C%BC%EB%A1%9C-%EC%84%A4%EC%A0%95%ED%95%98%EB%8A%94-%EA%B8%B0%EB%8A%A5%EC%9D%84-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
- [Fixed Bugs](#fixed-bugs)
  - [BUG-49739 MERGE JOIN을 사용한 CREATE AS SELECT 문을 수행한 세션이 SESSION CLOSE로 강제 종료되지 않습니다.](#bug-49739merge-join%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%9C-create-as-select-%EB%AC%B8%EC%9D%84-%EC%88%98%ED%96%89%ED%95%9C-%EC%84%B8%EC%85%98%EC%9D%B4-session-close%EB%A1%9C-%EA%B0%95%EC%A0%9C-%EC%A2%85%EB%A3%8C%EB%90%98%EC%A7%80-%EC%95%8A%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-49741 AIX에서, SMO 연산을 수행하는 메모리 인덱스에 접근하는 트랜잭션이 있을 때 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-49741aix%EC%97%90%EC%84%9C-smo-%EC%97%B0%EC%82%B0%EC%9D%84-%EC%88%98%ED%96%89%ED%95%98%EB%8A%94-%EB%A9%94%EB%AA%A8%EB%A6%AC-%EC%9D%B8%EB%8D%B1%EC%8A%A4%EC%97%90-%EC%A0%91%EA%B7%BC%ED%95%98%EB%8A%94-%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98%EC%9D%B4-%EC%9E%88%EC%9D%84-%EB%95%8C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-49746 윈도우(분석) 함수, ORDER BY 절, GROUP BY 절을 사용한 질의문에서 디스크 임시 공간을 사용하면 결과 오류가 발생합니다.](#bug-49746%EC%9C%88%EB%8F%84%EC%9A%B0%EB%B6%84%EC%84%9D-%ED%95%A8%EC%88%98-order-by-%EC%A0%88-group-by-%EC%A0%88%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%9C-%EC%A7%88%EC%9D%98%EB%AC%B8%EC%97%90%EC%84%9C-%EB%94%94%EC%8A%A4%ED%81%AC-%EC%9E%84%EC%8B%9C-%EA%B3%B5%EA%B0%84%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%98%EB%A9%B4-%EA%B2%B0%EA%B3%BC-%EC%98%A4%EB%A5%98%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49773 PSM에서 EXECUTE IMMEDIATE 문에 INTO 절을 사용하지 않고 DEQUEUE 문을 수행할 때 ERR-4108A : Queue not found 에러가 발생할 수 있습니다.](#bug-49773psm%EC%97%90%EC%84%9C-execute-immediate-%EB%AC%B8%EC%97%90-into-%EC%A0%88%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%98%EC%A7%80-%EC%95%8A%EA%B3%A0-dequeue-%EB%AC%B8%EC%9D%84-%EC%88%98%ED%96%89%ED%95%A0-%EB%95%8C-err-4108a--queue-not-found-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-49779 라이브러리(library) 객체를 변경하면 해당 객체가 사용된 저장 패키지 바디를 컴파일이 필요한 상태로 변경해야 합니다.](#bug-49779%EB%9D%BC%EC%9D%B4%EB%B8%8C%EB%9F%AC%EB%A6%AClibrary-%EA%B0%9D%EC%B2%B4%EB%A5%BC-%EB%B3%80%EA%B2%BD%ED%95%98%EB%A9%B4-%ED%95%B4%EB%8B%B9-%EA%B0%9D%EC%B2%B4%EA%B0%80-%EC%82%AC%EC%9A%A9%EB%90%9C-%EC%A0%80%EC%9E%A5-%ED%8C%A8%ED%82%A4%EC%A7%80-%EB%B0%94%EB%94%94%EB%A5%BC-%EC%BB%B4%ED%8C%8C%EC%9D%BC%EC%9D%B4-%ED%95%84%EC%9A%94%ED%95%9C-%EC%83%81%ED%83%9C%EB%A1%9C-%EB%B3%80%EA%B2%BD%ED%95%B4%EC%95%BC-%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49827 \$ALTIBASE\_HOME/sample 아래의 APRE, CAPI, CHECKSERVER, SPATIAL, SQLCLI 샘플 코드를 ODBC 표준에 맞춰 수정합니다.](#bug-49827altibase_homesample-%EC%95%84%EB%9E%98%EC%9D%98-apre-capi-checkserver-spatial-sqlcli-%EC%83%98%ED%94%8C-%EC%BD%94%EB%93%9C%EB%A5%BC-odbc-%ED%91%9C%EC%A4%80%EC%97%90-%EB%A7%9E%EC%B6%B0-%EC%88%98%EC%A0%95%ED%95%A9%EB%8B%88%EB%8B%A4)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
  - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
  - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

<br/>

<br/>

New Features
============

### BUG-49776 IPC 및 IPCDA 채널을 생성하는 데 필요한 공유 메모리와 세마포어의 키를 사용자가 정의한 값으로 설정하는 기능을 추가합니다.

#### Module

`cm-ipc`

#### Category 

 `Functionality` 

#### 설명

IPC 및 IPCDA 채널을 생성하는 데 필요한 공유 메모리와 세마포어의 키를 사용자가 정의한 값으로 설정하는 기능을 추가합니다. 

사용자는 아래 4가지 프로퍼티를 사용하여 공유 메모리와 세마포어의 키를 설정할 수 있습니다.

- IPC\_SEM\_KEY

- IPC\_SHM\_KEY

- IPCDA\_SEM\_KEY

- IPCDA\_SHM\_KEY

IPC와 IPCDA 채널은 Altibase 서버 구동 시 생성되는데, 프로퍼티로 설정한 공유 메모리/세마포어 키가 사용 중이거나 다른 이유로 공유 메모리/세마포어를 생성하지 못하면 Altibase 서버 구동은 실패합니다. 이때, Altibase 서버 트레이스 로그 altibase\_boot.log에서 시스템 에러(errno)를 확인하고 그에 따른 적절한 처리를 해야 합니다.

프로퍼티 설명은 `Altibase 7.1` [General Reference-1.Data Types & Altibase Properties](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/General%20Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#ipc_sem_key) 매뉴얼에서 확인하기 바랍니다.


#### 변경사항

-   Performance view

-   Property

    -   `IPC_SEM_KEY`

        IPC 채널을 생성하는 데 필요한 세마포어 키(key)를 사용자가 정의한 값으로 설정하는 프로퍼티이다.

        기본값은 0으로 Altibase 서버 프로세스의 프로세스 식별자(PID)를 기준으로 세마포어 키를 자동으로 생성한다. 0이 아닌 값을 설정하면 IPC_SEM_KEY 값을 기준으로 IPC_SEM_KEY부터 IPC_SEM_KEY + (IPC_CHANNEL_COUNT + 1)만큼의 연속된 세마포어 키를 사용하여 IPC 채널을 생성한다. +1은 SYS 사용자가 관리자 모드(sysdba)로 접속하기 위해 예약된 IPC 채널이다. 예를 들어 IPC_SEM_KEY 값이 10000이고 IPC_CHANNEL_COUNT 값이 1000이면 세마포어 키로 10000부터 11000까지 사용한다.

    -   `IPC_SHM_KEY`

        IPC 채널을 생성하는 데 필요한 공유 메모리 키(key)를 사용자가 정의한 값으로 설정하는 프로퍼티이다.

        기본값은 0으로 Altibase 서버 프로세스의 프로세스 식별자(PID)를 기준으로 공유 메모리 키를 자동으로 생성한다. 0이 아닌 값을 설정하면 IPC_SHM_KEY 값을 공유 메모리 키로 사용한다.

    -   `IPCDA_SEM_KEY`

        IPCDA 채널을 생성하는 데 필요한 세마포어 키(key)를 사용자가 정의한 값으로 설정하는 프로퍼티이다.

        기본값은 0으로 Altibase 서버 프로세스의 프로세스 식별자(PID)를 기준으로 세마포어 키를 자동으로 생성한다. 0이 아닌 값을 설정하면 IPCDA_SEM_KEY 값을 기준으로 IPCDA_SEM_KEY부터 IPCDA_SEM_KEY + IPC_CHANNEL_COUNT만큼의 연속된 세마포어 키를 사용하여 IPCDA 채널을 생성한다. 예를 들어 IPCDA_SEM_KEY 값이 10000이고 IPC_CHANNEL_COUNT 값이 1000이면 세마포어 키로 10000부터 10999까지 사용한다.

    -   `IPCDA_SHM_KEY`

        IPCDA 채널을 생성하는 데 필요한 공유 메모리 키(key)를 사용자가 정의한 값으로 설정하는 프로퍼티이다.

        기본값은 0으로 Altibase 서버 프로세스의 프로세스 식별자(PID)를 기준으로 공유 메모리 키를 자동으로 생성한다. 0이 아닌 값을 설정하면 IPCDA_SHM_KEY 값을 기준으로 연속된 키 2개를 공유 메모리 키로 사용한다. 예를 들어 IPCDA_SHM_KEY=10000이면 10000, 10001을 공유 메모리 키 값으로 사용한다.

-   Compile Option

-   Error Code

    에러 메시지 2가지가 추가되었습니다. 

    - IPC와 IPCDA 채널 생성 시 Altibase 서버 프로퍼티에 정의된 키로 공유 메모리를 생성할 수 없을 때

      ```
      0x710C6 ( 463046) cmERR_ABORT_SHMGET_ERROR_WITH_KEY A system call error occurred while creating shared memory for <0%s>. [key : <1%u>] 
      # *Cause: shmget() system call failed.
      # *Action: Check the errno and take an appropriate action. For example, if the errno is EEXIST, check the shared memory status. If there is a shared memory that has the same key value, remove the shared memory or retry with another key value.
      ```

    - IPC와 IPCDA 채널 생성 시 Altibase 서버 프로퍼티에 정의된 키로 세마포어를 생성할 수 없을 때

      ```
      0x710C7 ( 463047) cmERR_ABORT_SEMGET_ERROR_WITH_KEY A system call error occurred while creating semaphore for <0%s>. [key : <1%u>] 
      # *Cause: semget() system call failed.
      # *Action: Check the errno and take an appropriate action. For example, if the errno is EEXIST, check the semaphore status. If there is a semaphore that has the same key value, remove the semaphore or retry with another key value.
      ```

<br/>

<br/>

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

    - A 세션

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

    - B 세션

      ~~~sql
      ALTER DATABASE database_name SESSION CLOSE session_id;
      ~~~

-   **수행 결과**

        테이블 생성 완료 후 세션 종료. 

-   **예상 결과**

        [ERR-01043 : The session has been closed by the server]

#### Workaround

`없음`

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-49741 AIX에서, SMO 연산을 수행하는 메모리 인덱스에 접근하는 트랜잭션이 있을 때 Altibase 서버가 비정상 종료할 수 있습니다.

#### module

`sm-mem-index`

#### Category

`Fatal`

#### 재현 빈도

`Rare`

#### 설명

AIX에서, SMO(Structure Modification Operation) 연산을 수행하는 메모리 인덱스에 접근하는 트랜잭션이 있을 때 Altibase 서버가 비정상 종료하는 현상을 수정합니다.

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

### BUG-49746 윈도우(분석) 함수, ORDER BY 절, GROUP BY 절을 사용한 질의문에서 디스크 임시 공간을 사용하면 결과 오류가 발생합니다.

#### module

`qp-select`

#### Category

`Functional Error`

#### 재현 빈도 

`Always`

#### 설명

아래 조건을 모두 만족하는 질의문 수행 시 결과 오류가 발생합니다.

- 윈도우(분석) 함수 사용

- GROUP BY 절, ORDER BY 절, 윈도우(분석) 함수 사용

- ORDER BY 절에 사용된 컬럼이 윈도우(분석) 함수 OVER 절에서 같은 순서로 사용

- ORDER BY 절에 사용된 컬럼이 SELECT 절에서 표현식으로 사용

- 쿼리 수행 시 디스크 임시 공간 사용

>  이 버그 현상을 회피하는 방법은 Work Around 부분을 확인해주세요.

> 패치 시 주의 사항
>
> 결괏값 오류를 개선한 버그로, 패치 후 버그 조건에 만족하는 질의문 수행 시 결과가 달라질 수 있습니다.

#### 재현 방법

-   **재현 절차**

    ```sql
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
    ```

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

#### Workaround

이 버그 현상은 TEMP_TBS_MEMORY 힌트 사용으로 회피할 수 있습니다. 

~~~sql
SELECT /*+ TEMP_TBS_MEMORY */ ROW_NUMBER() OVER(ORDER BY A.I1 DESC) RNUM
     , TO_CHAR(TO_DATE(A.I1, 'YYYYMMDD'), 'YYYY-MM-DD') AS YYYYMMDD
     , SUM(A.I2) AS CNT
  FROM T1 A
 GROUP BY A.I
 ORDER BY A.I1 DESC;
~~~

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-49773 PSM에서 EXECUTE IMMEDIATE 문에 INTO 절을 사용하지 않고 DEQUEUE 문을 수행할 때 ERR-4108A : Queue not found 에러가 발생할 수 있습니다.

#### module

`qp-psm-trigger-execute`

#### Category

`Functional Error`

#### 재현 빈도 

`Always`

#### 설명

PSM에서 EXECUTE IMMEDIATE 문에 INTO 절을 사용하지 않고 DEQUEUE 문을 수행할 때 ERR-4108A : Queue not found 에러가 발생하는 현상을 수정합니다. 큐가 비어있는 상태에서 버그 발생 조건을 만족하면 세션에서 큐 정보를 삭제하는 문제를 수정하였습니다.

이 버그는 아래의 순서대로 큐와 PSM을 생성하고 수행할 때 발생합니다. 실제 수행 예시는 재현 방법을 참고하세요.

1. 큐 생성
2. PSM 생성
      - DEQUEUE 문을 동적 SQL로 수행
      - EXECUTE IMMEDIATE 문에 INTO 절 사용하지 않음


3) PSM 수행 

4) 임의의 DDL 문 수행

5) PSM 수행

#### 재현 방법

-   **재현 절차**

    ```sql
    DROP QUEUE q1;
    DROP TABLE t1;
    CREATE QUEUE q1(1000);
    CREATE OR REPLACE PROCEDURE dq_test ()
    AS
        OUT1 VARCHAR(1000);
    BEGIN
        EXECUTE IMMEDIATE('DEQUEUE MESSAGE INTO OUT1 FROM q1');
        PRINTLN(OUT1);
    END;
    /
    EXEC dq_test;
    CREATE TABLE t1 (c1 INTEGER);
    EXEC dq_test;
    ```

-   **수행 결과**

    ```sql
    [ERR-4108A : Queue not found
    ```

-   **예상 결과**

    ```sql
    Execute success.
    ```

#### Workaround

EXECUTE IMMEDIATE 문에 INTO 절 사용합니다.

~~~sql
EXECUTE IMMEDIATE('DEQUEUE MESSAGE INTO OUT1 FROM q1') INTO OUT1;
~~~

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code



### BUG-49779 라이브러리(library) 객체를 변경하면 해당 객체가 사용된 저장 패키지 바디를 컴파일이 필요한 상태로 변경해야 합니다.

#### module

`qp-psm-trigger-execute`

#### Category

`Functional Error`

#### 재현 빈도

`Always`

#### 설명

라이브러리(library) 객체를 CREATE OR REPLACE 문으로 변경하면 해당 객체가 사용된 저장 패키지 바디를 컴파일이 필요한 상태(invalid)로 변경합니다.

#### 재현 방법

-   **재현 절차**

    ```sql
    CREATE OR REPLACE LIBRARY lib1 AS 'normal.so';
    
    CREATE OR REPLACE PACKAGE pkg1 AS
    PROCEDURE proc1( a1 IN VARCHAR(30), a2 OUT VARCHAR(30) );
    END;
    /
    
    CREATE OR REPLACE PACKAGE BODY pkg1 AS
    PROCEDURE proc1( a1 IN VARCHAR(30), A2 OUT VARCHAR(30) )
    AS
    LANGUAGE C
    LIBRARY lib1
    NAME "andy_upper";
    END;
    /
    
    CREATE OR REPLACE LIBRARY lib1 AS 'normal.so';
    
    SELECT USER_ID, PACKAGE_NAME, PACKAGE_TYPE, STATUS FROM SYSTEM_.SYS_PACKAGES_;
    ```

-   **수행 결과**

    ```sql
    USER_ID     PACKAGE_NAME                    PACKAGE_TYPE STATUS
    --------------------------------------------------------------------------
    2           PKG1                            6           0
    2           PKG1                            7           0
    2 rows selected.
    ```

-   **예상 결과**

    ```sql
    USER_ID     PACKAGE_NAME                    PACKAGE_TYPE STATUS
    --------------------------------------------------------------------------
    2           PKG1                            6           0
    2           PKG1                            7           1
    2 rows selected.
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

$ALTIBASE\_HOME/sample 아래의 APRE, CAPI, CHECKSERVER, SPATIAL, SQLCLI 샘플 코드를 ODBC 표준에 맞춰 수정합니다.

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
|    6.3.1.12.5    |          6.2.1          |    6.3.1     |        7.1.1        |            7.4.1             |

> Altibase 6.3.1 패치 버전별 히스토리는 [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_6.3.1/Altibase_6_3_1_Version_Histories.md) 에서 확인할 수 있다.

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

- [IPC_SEM_KEY](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/General%20Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#ipc_sem_key)
- [IPC_SHM_KEY](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/General%20Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#ipc_shm_key)
- [IPCDA_SEM_KEY](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/General%20Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#ipcda_sem_key)
- [IPCDA_SHM_KEY](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/General%20Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#ipcda_shm_key)

#### 변경된 프로퍼티

#### 삭제된 프로퍼티

### 성능 뷰

#### 추가된 성능 뷰

#### 변경된 성능 뷰

#### 삭제된 성능 뷰
