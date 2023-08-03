# Altibase 7.1.0.8.9 Patch Notes

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-50412  Unsupported property warning 로깅시 플래그 설정이 필요합니다.](#bug-50412-unsupported-property-warning-%EB%A1%9C%EA%B9%85%EC%8B%9C-%ED%94%8C%EB%9E%98%EA%B7%B8-%EC%84%A4%EC%A0%95%EC%9D%B4-%ED%95%84%EC%9A%94%ED%95%A9%EB%8B%88%EB%8B%A4)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-49999  큐 테이블의 동일 레코드에 DELETE와 DEQUEUE가 동시에 수행되는 경우, 트랜잭션을 대기하는 문제가 있습니다.](#bug-49999-%ED%81%90-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%9D%98-%EB%8F%99%EC%9D%BC-%EB%A0%88%EC%BD%94%EB%93%9C%EC%97%90-delete%EC%99%80-dequeue%EA%B0%80-%EB%8F%99%EC%8B%9C%EC%97%90-%EC%88%98%ED%96%89%EB%90%98%EB%8A%94-%EA%B2%BD%EC%9A%B0-%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98%EC%9D%84-%EB%8C%80%EA%B8%B0%ED%95%98%EB%8A%94-%EB%AC%B8%EC%A0%9C%EA%B0%80-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-50391  PUBLIC ROLE은 제거되면 안됩니다.](#bug-50391-public-role%EC%9D%80-%EC%A0%9C%EA%B1%B0%EB%90%98%EB%A9%B4-%EC%95%88%EB%90%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50402  bash쉘이 아닌 경우, 알티베이스 설치 인스톨러로 설치 중에 make_link.sh 에서 오류가 발생합니다.](#bug-50402-bash%EC%89%98%EC%9D%B4-%EC%95%84%EB%8B%8C-%EA%B2%BD%EC%9A%B0-%EC%95%8C%ED%8B%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4-%EC%84%A4%EC%B9%98-%EC%9D%B8%EC%8A%A4%ED%86%A8%EB%9F%AC%EB%A1%9C-%EC%84%A4%EC%B9%98-%EC%A4%91%EC%97%90-make_linksh-%EC%97%90%EC%84%9C-%EC%98%A4%EB%A5%98%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50406  HP-UX,AIX에서 altimon 구동이 실패하는 문제가 있습니다.](#bug-50406-hp-uxaix%EC%97%90%EC%84%9C-altimon-%EA%B5%AC%EB%8F%99%EC%9D%B4-%EC%8B%A4%ED%8C%A8%ED%95%98%EB%8A%94-%EB%AC%B8%EC%A0%9C%EA%B0%80-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-50422  aku 프로퍼티 AKU_SYS_PASWWORD의 오타를 수정합니다.](#bug-50422-aku-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0-aku_sys_paswword%EC%9D%98-%EC%98%A4%ED%83%80%EB%A5%BC-%EC%88%98%EC%A0%95%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50451  같은 query set내에 order by에 사용된 alias 가 target 절의 row_number 함수의 alias로 사용된 경우 서버가 비정상 종료 합니다.](#bug-50451-%EA%B0%99%EC%9D%80-query-set%EB%82%B4%EC%97%90-order-by%EC%97%90-%EC%82%AC%EC%9A%A9%EB%90%9C-alias-%EA%B0%80-target-%EC%A0%88%EC%9D%98-row_number-%ED%95%A8%EC%88%98%EC%9D%98-alias%EB%A1%9C-%EC%82%AC%EC%9A%A9%EB%90%9C-%EA%B2%BD%EC%9A%B0-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C-%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50453  LB trace log 메시지에 오류가 있어서 수정합니다.](#bug-50453-lb-trace-log-%EB%A9%94%EC%8B%9C%EC%A7%80%EC%97%90-%EC%98%A4%EB%A5%98%EA%B0%80-%EC%9E%88%EC%96%B4%EC%84%9C-%EC%88%98%EC%A0%95%ED%95%A9%EB%8B%88%EB%8B%A4)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-50412  Unsupported property warning 로깅시 플래그 설정이 필요합니다.

-   **module** : mm

-   **Category** : Usability

-   **재현 빈도** : Always

-   **설명** : Unsupported property warning 로그는 상황에 따라 대량의
    로그가 출력될 수 있기 때문에 MM\_MSGLOG\_FLAG 프로퍼티로 로깅여부를 설정할 수 있도록
    변경하였습니다.

    MM\_MSGLOG\_FLAG의 0번 비트 기본값을 0에서 1로 변경해서 디폴트로
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

### BUG-49999  큐 테이블의 동일 레코드에 DELETE와 DEQUEUE가 동시에 수행되는 경우, 트랜잭션을 대기하는 문제가 있습니다.

-   **module** : sm

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 큐는 레코드 락을 대기하면 안 되는데, 대기하는 문제가
    있어서 수정합니다. 이 문제는 Altibase 7.1.0.6.0 이상에서 재현되며, 이 패치를 적용한 이후부터는 발생하지 않습니다.

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

### BUG-50391  PUBLIC ROLE은 제거되면 안됩니다.

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
            - [ERR-314B6 : It is forbidden to drop the PUBLIC role.]
              - Cause: You cannot drop the PUBLIC role.
              - Action: Don't try dropping the PUBLIC role.

### BUG-50402  bash쉘이 아닌 경우, 알티베이스 설치 인스톨러로 설치 중에 make_link.sh 에서 오류가 발생합니다.

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

### BUG-50406  HP-UX,AIX에서 altimon 구동이 실패하는 문제가 있습니다.

-   **module** : ux-altiMon

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : BUG-50009 영향으로 HP-UX, AIX에서 altimon 구동이 실패하는 문제가 있어 수정합니다. 이 현상은 7.1.0.8.6 부터 발생하며, 이 버그가 반영된 7.1.0.8.9 패치부터는 발생하지 않습니다.

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

### BUG-50422  aku 프로퍼티 AKU\_SYS\_PASWWORD의 오타를 수정합니다.

-   **module** :

-   **Category** : Maintainability

-   **재현 빈도** : Always

-   **설명** : aku.conf 파일내에 프로퍼티의 오타를 수정합니다.

     변경전 : AKU\_SYS\_**PASW**WORD

     변경후 : AKU\_SYS\_**PASS**WORD

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

### BUG-50451  같은 query set내에 order by에 사용된 alias 가 target 절의 row\_number 함수의 alias로 사용된 경우 서버가 비정상 종료 합니다.

-   **module** : qp

-   **Category** : Fatal

-   **재현 빈도** : Always

- **설명** : 아래 조건을 모두 만족하는 질의문 수행 시, 비정상 종료하는 문제를 수정하였습니다.

  -   같은 쿼리셋내에 ORDER BY에 사용된 alias가 target절의 row_number 함수의 alias로 사용된 경우
  -   row_number 함수 OVER절에서 PARTITION BY나 ORDER BY에 사용된 컬럼이 GROUP BY에 사용된 경우
  -   GROUP BY에 사용된 컬럼을 TRIM 함수의 인자로 사용하고, 이 인자를 해당 TRIM 함수의 alias로 사용한 경우

- **재현 방법**

  - **재현 절차**

    ```sql
    DROP TABLE MD281;

    CREATE TABLE MD281 ( BID varchar(30)
    , LSTTRD_DD varchar(30)
    , EXPMM varchar(30)
    , EXPWW varchar(30)
    , SETLMULT double
    , TRADE_DATE varchar(30)
    );

    SELECT  CASE BID
                            WHEN 'WKI' THEN 1
                            WHEN 'WKM' THEN 2
                            ELSE 99 END - 1                           AS SEQ_WEEKDAY
                    ,   ROW_NUMBER() OVER(PARTITION BY BID
                                ORDER BY LSTTRD_DD ASC)               AS SEQ_WW
                    ,   TRIM(BID)                           AS BID
                    ,   TRIM(EXPMM)                                   AS EXPMM
                    ,   TRIM(EXPWW)                                   AS EXPWW
                    ,   TRIM(LSTTRD_DD)                               AS LSTTRD_DD
                    ,   MAX(ROUND(NVL(SETLMULT,0) * 1.))              AS SETLMULT
                FROM    MD281
                WHERE   TRADE_DATE = '20230629'
                GROUP BY BID, LSTTRD_DD, EXPMM, EXPWW
                ORDER BY SEQ_WEEKDAY, SEQ_WW;
    ```

  - **수행 결과**

    ```sql
    [ERR-31455 : Failed to work because an internal exception occurred
     from an OS.[Contact Altibase's Support Center]]
    ```

  -   **예상 결과**

      ```sql
      No rows selected.
      ```

- **Workaround**

  ```sql
  SELECT SEQ_WEEKDAY, SEQ_WW, BID, EXPMM, EXPWW, LSTTRD_DD, SETLMULT FROM (
  SELECT  CASE BID
                          WHEN 'WKI' THEN 1
                          WHEN 'WKM' THEN 2
                          ELSE 99 END - 1                           AS SEQ_WEEKDAY
                  ,   ROW_NUMBER() OVER(PARTITION BY BID  ORDER BY LSTTRD_DD ASC)  AS SEQ_WW
                  ,   TRIM(BID)                           AS BID
                  ,   TRIM(EXPMM)                                   AS EXPMM
                  ,   TRIM(EXPWW)                                   AS EXPWW
                  ,   TRIM(LSTTRD_DD)                               AS LSTTRD_DD
                  ,   MAX(ROUND(NVL(SETLMULT,0) * 1.))              AS SETLMULT
              FROM    MD281
              WHERE   TRADE_DATE = '20230629'
              GROUP BY BID, LSTTRD_DD, EXPMM, EXPWW
              ) ORDER BY SEQ_WEEKDAY, SEQ_WW;
  ```

- **변경사항**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

### BUG-50453  LB trace log 메시지에 오류가 있어서 수정합니다.

-   **module** : mm

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : LB trace log 메시지에 오류가 있어 수정합니다. "현재 서비스 쓰레드의 개수가 MULTIPLEXING_MAX_THREAD_COUNT 보다 크다"를 표시하는 메시지에서 현재 서비스 쓰레드가 아닌 새로 생성될 서비스 쓰레드의 개수가 표시되고 있는 문제를 수정하였습니다.

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
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 7.1.0.8.9        | 6.5.1                   | 8.11.1       | 7.1.7               | 7.4.7                        |

> Altibase 7.1 패치 버전별 히스토리는 [Version_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.1/Altibase_7_1_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의
> 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는
> 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

> 패치를 롤백하려는 경우,
> [메타다운그레이드](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Installation%20Guide.md#%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9Cmeta-downgrade)를
> 참고한다.

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
