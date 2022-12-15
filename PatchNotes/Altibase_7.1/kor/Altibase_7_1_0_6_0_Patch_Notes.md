# Altibase 7.1.0.6.0 Patch Notes

<br/>

<br/>



# **Table of Contents** 

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Fixed Bugs](#fixed-bugs)
    - [BUG-49063 큐 테이블의 동일 레코드에 DELETE와 DEQUEUE가 동시에 일어날 경우 Altibase 서버가 비정상 종료합니다.](#bug-49063-%ED%81%90-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%9D%98-%EB%8F%99%EC%9D%BC-%EB%A0%88%EC%BD%94%EB%93%9C%EC%97%90-delete%EC%99%80-dequeue%EA%B0%80-%EB%8F%99%EC%8B%9C%EC%97%90-%EC%9D%BC%EC%96%B4%EB%82%A0-%EA%B2%BD%EC%9A%B0-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-49242 aexport 객체 모드에서 큐(QUEUE) 객체가 추출되지 않습니다.](#bug-49242-aexport-%EA%B0%9D%EC%B2%B4-%EB%AA%A8%EB%93%9C%EC%97%90%EC%84%9C-%ED%81%90queue-%EA%B0%9D%EC%B2%B4%EA%B0%80-%EC%B6%94%EC%B6%9C%EB%90%98%EC%A7%80-%EC%95%8A%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-49243 20000바이트 이상의 길이가 긴 SQL문 사용 시 altibase\_error.log 에 콜스택이 출력되지 않습니다.](#bug-49243-20000%EB%B0%94%EC%9D%B4%ED%8A%B8-%EC%9D%B4%EC%83%81%EC%9D%98-%EA%B8%B8%EC%9D%B4%EA%B0%80-%EA%B8%B4-sql%EB%AC%B8-%EC%82%AC%EC%9A%A9-%EC%8B%9C-altibase_errorlog-%EC%97%90-%EC%BD%9C%EC%8A%A4%ED%83%9D%EC%9D%B4-%EC%B6%9C%EB%A0%A5%EB%90%98%EC%A7%80-%EC%95%8A%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-49271 디스크 테이블을 포함한 트래잭션 처리 중 해시 템프 테이블 재사용 과정에서 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-49271-%EB%94%94%EC%8A%A4%ED%81%AC-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%9D%84-%ED%8F%AC%ED%95%A8%ED%95%9C-%ED%8A%B8%EB%9E%98%EC%9E%AD%EC%85%98-%EC%B2%98%EB%A6%AC-%EC%A4%91-%ED%95%B4%EC%8B%9C-%ED%85%9C%ED%94%84-%ED%85%8C%EC%9D%B4%EB%B8%94-%EC%9E%AC%EC%82%AC%EC%9A%A9-%EA%B3%BC%EC%A0%95%EC%97%90%EC%84%9C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Fixed Bugs
==========

### BUG-49063 큐 테이블의 동일 레코드에 DELETE와 DEQUEUE가 동시에 일어날 경우 Altibase 서버가 비정상 종료합니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Rare

-   **설명** : QEUEUE 성능 개선을 위해 BUG-48230(Altibase 7.1.0.4.8)에서
    페이지에 X Latch를 잡지 않도록 수정하였습니다. 이후 DELETE와 DEQUEUE
    동시 수행 시 Altibase 서버 비정상 종료 현상이 발생합니다. 

    이 현상을 회피하기 위해 큐 테이블에 DELETE 구문 허용 여부를 설정하는
    구문을 추가합니다.

    - CREATE QUEUE 및 ALTER QUEUE 구문에 DELETE 추가
      - DELETE ON
    
          - QUEUE 테이블에 DELETE 문 가능
    
          - DELETE 문을 허용하지 않은 경우보다 DEQUEUE 병렬 수행 성능이
          저하됨.
    
      - DELETE OFF
    
          - QUEUE 테이블에 DELETE 문 불가능
    
          - DELETE 문을 허용한 경우보다 DEQUEUE 병렬 수행 성능이 향상됨. 
    
    관련하여 V\$QEUEUE 성능 뷰가 추가되었고 큐 테이블 생성 시 디스크
    테이블스페이스를 지정할 경우 발생하는 에러 메시지가 변경되었습니다.

-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
        -   V$QEUEUE 성능 뷰가 추가되었습니다. 
            
        -   ```sql
            iSQL> DESC V$QUEUE
            [ ATTRIBUTE ]                                                         
            ------------------------------------------------------------------------------
            NAME                                     TYPE                         
            ------------------------------------------------------------------------------
            TABLE_OID                                BIGINT         
            DELETE_ON                                VARCHAR(1)     
            QUEUED                                   BIGINT                
            ```
            
            - DELETE_ON	
              - T : DELETE 수행 가능. DEQUEUE 시 lock wait 발생으로 DELETE 수행 불가한 경우보다 성능이 느릴 수 있음. 
              - F : DELETE 수행 불가. DELETE 가능한 경우보다 DEQUEUE 성능이 빠름.
            - QUEUED 
              - 큐에 있는 아이템 수 
        
    -   Property
    -   Compile Option
    -   Error Code
        -   큐 테이블 생성 시 디스크 테이블스페이스를 지정할 경우 발생하는 에러 메시지가 변경되었습니다. 
            
            ```sql
            CREATE QUEUE Q1 ( 7 ) TABLESPACE SYS_TBS_DISK_DATA;
            -[ERR-311E5 : The table is not a memory or volatile table.]
            +[ERR-3147B : The QUEUE table cannot be used on disk tablespace.]
            ```

### BUG-49242 aexport 객체 모드에서 큐(QUEUE) 객체가 추출되지 않습니다.

- **module** : ux-aexport

- **Category** : Functional Error

- **재현 빈도** : Always

- **설명** : aexport 객체 모드에서 큐(QUEUE) 객체가 추출되지 않는 버그를 수정합니다.

- **재현 방법**

  - **재현 절차**

    ```sql
    iSQL> CREATE QUEUE q1(10);
    Create success.
    ```

  - **수행 결과**

    ```bash
    % aexport -s 127.0.0.1 -u sys -p manager -object sys.q1
    The SYS.Q1 object not exist
    ```

  - **예상 결과**

    ```bash
    % aexport -s 127.0.0.1 -u sys -p manager -object sys.q1
    ##### QUEUE #####
    ** "SYS"."Q1"
    create queue "Q1" (10);
    ```

- **Workaround**

  -   전체 DB 모드/사용자 모드로 export

- **변경사항**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

### BUG-49243 20000바이트 이상의 길이가 긴 SQL문 사용 시 altibase\_error.log 에 콜스택이 출력되지 않습니다.

-   **module** : id

-   **Category** : Testcase Fail

-   **재현 빈도** : Always

-   **설명** : 20000바이트 이상의 길이가 긴 SQL문 사용 시
    altibase\_error.log 에 콜스택이 잘리는 현상을 수정합니다. 이
    현상은 BUG-48433이 반영된 Altibase 7.1.0.5.2 버전부터
    발생하는 버그입니다.

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

### BUG-49271 디스크 테이블을 포함한 트래잭션 처리 중 해시 템프 테이블 재사용 과정에서 Altibase 서버가 비정상 종료할 수 있습니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : 디스크 테이블을 포함한 트래잭션 처리 중 임시 데이터
    처리를 위한 해시 템프 테이블 재사용 시 초기화되지 않은 페이지에
    접근하여 Altibase 서버가 비정상 종료하는 현상을 수정하였습니다.

- **재현 방법**

  - **재현 절차**

    ```sql
    CREATE TABLE T10 (CIF int, AGE int) TABLESPACE SYS_TBS_DISK_DATA;
    
    CREATE TABLE T1 (CIF int, ACNO int, DPNT_CLSN_Q int, DPNT_CNPR int,  ORD_DT int, BNS_TCD int ) TABLESPACE SYS_TBS_DISK_DATA;
    CREATE TABLE T2 (CIF int, ACNO int) TABLESPACE SYS_TBS_DISK_DATA;
    CREATE TABLE T3 (BAS_DT int, BIZDT_YN int, EXG_COD int ) TABLESPACE SYS_TBS_DISK_DATA;
    
    INSERT INTO T10 SELECT  MOD(LEVEL,50000), MOD(LEVEL,100) FROM DUAL CONNECT BY LEVEL <=50000;
    INSERT INTO T1  SELECT  7, 9, 1, 1, 5, 2 FROM DUAL CONNECT BY LEVEL <=100;
    INSERT INTO T2  SELECT  MOD(LEVEL,50000), 9  FROM DUAL CONNECT BY LEVEL <=50000;
    INSERT INTO T3  SELECT  1, 1, 0 FROM DUAL CONNECT BY LEVEL <=10;
    
    ALTER SYSTEM SET HASH_AREA_SIZE = 3145728;
    
    SELECT V1.CIF
         , CASE WHEN V1.AGE < 10 THEN '0' ELSE SUBSTR(V1.AGE, 1, 1) END AS AGE_GROUP
         , V2.OPENRANK_TYPE
      FROM (
             SELECT CIF, AGE
               FROM T10
           ) V1
          ,(
             SELECT V98.CIF  AS CIF
                  , CASE WHEN V98.CUT_LINE = 0 AND RANK = 1 THEN '10'
                         WHEN RANK <= V98.CUT_LINE THEN '10'
                    ELSE NULL END AS OPENRANK_TYPE
               FROM
                   (
                     SELECT V99.CIF AS CIF
                          , V99.DPNT_CNPR AS DPNT_ACBK_PR
                          , TRUNC(COUNT(DISTINCT V99.CIF) OVER() * 0.1) AS CUT_LINE
                          , RANK() OVER(ORDER BY V99.DPNT_CNPR DESC) AS RANK
                       FROM
                           (
                             SELECT T2.CIF  AS CIF
                                  , SUM(T1.DPNT_CLSN_Q * T1.DPNT_CNPR) AS DPNT_CNPR
                               FROM T1, T2
                              WHERE T1.ACNO= T2.ACNO
                                AND  T1.BNS_TCD= '2'
                                AND  T1.ORD_DT >= ( SELECT BAS_DT
                                                      FROM T3
                                                     WHERE BAS_DT <= 3
                                                       AND BIZDT_YN = 1
                                                       AND EXG_COD = 0
                                                  ORDER BY BAS_DT DESC
                                                   )
                       WHERE RK = 5
                     )
                       GROUP  BY T2.CIF
                   ) V99
               ) V98
            ) V2
       WHERE V1.CIF = V2.CIF
         AND V2.OPENRANK_TYPE IS NOT NULL  ;
    ```

  - **수행 결과**

    ```sql
    [ERR-91015 : Communication failure.]
    ```

  -   **예상 결과**

      ```sql
      50000 rows selected.
      ```

- **Workaround**

- **변경사항**

  -   Performance view
  -   Property

  -   Compile Option
  -   Error Code

Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    7.1.0.6.0     |          6.5.1          |    8.9.1     |        7.1.7        |            7.4.6             |

> Altibase 7.1 패치 버전별 히스토리는 [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.1/Altibase_7_1_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

> 패치를 롤백하려는 경우, [메타다운그레이드](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Installation%20Guide.md#%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9Cmeta-downgrade)를 참고한다.

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

- V$QEUEUE

#### 변경된 성능 뷰

#### 삭제된 성능 뷰
