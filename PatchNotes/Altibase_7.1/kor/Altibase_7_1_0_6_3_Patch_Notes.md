<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  

- [Altibase 7.1.0.6.3 Patch Notes](#altibase-71063-patch-notes)
  - [New Features](#new-features)
    - [BUG-49274 altiComp에 사용자가 커밋 카운트를 조정하는 프로퍼티를 추가합니다.](#bug-49274alticomp%EC%97%90-%EC%82%AC%EC%9A%A9%EC%9E%90%EA%B0%80-%EC%BB%A4%EB%B0%8B-%EC%B9%B4%EC%9A%B4%ED%8A%B8%EB%A5%BC-%EC%A1%B0%EC%A0%95%ED%95%98%EB%8A%94-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0%EB%A5%BC-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-49324 statement 객체가 남은 상태에서 Altibase 비정상 종료 가능성을 회피하기 위해 예외 처리를 추가합니다.](#bug-49324statement-%EA%B0%9D%EC%B2%B4%EA%B0%80-%EB%82%A8%EC%9D%80-%EC%83%81%ED%83%9C%EC%97%90%EC%84%9C-altibase-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C-%EA%B0%80%EB%8A%A5%EC%84%B1%EC%9D%84-%ED%9A%8C%ED%94%BC%ED%95%98%EA%B8%B0-%EC%9C%84%ED%95%B4-%EC%98%88%EC%99%B8-%EC%B2%98%EB%A6%AC%EB%A5%BC-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-49354 BUG-49063에서 추가한 V\$QUEUE를 삭제하고 V\$QUEUE\_DELETE\_OFF를 추가합니다.](#bug-49354bug-49063%EC%97%90%EC%84%9C-%EC%B6%94%EA%B0%80%ED%95%9C-vqueue%EB%A5%BC-%EC%82%AD%EC%A0%9C%ED%95%98%EA%B3%A0-vqueue_delete_off%EB%A5%BC-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-49350 aexport 에서 큐(QUEUE) 객체 스키마 추출 시 [ERR-00000 : ] 에러가 발생합니다.](#bug-49350aexport-%EC%97%90%EC%84%9C-%ED%81%90queue-%EA%B0%9D%EC%B2%B4-%EC%8A%A4%ED%82%A4%EB%A7%88-%EC%B6%94%EC%B6%9C-%EC%8B%9C-err-00000---%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-49364 최하위 LEFT OUTER JOIN 에서 널 패딩(null padding)이 발생하고 중간 LEFT OUTER JOIN에서 널 패딩이 발생하지 않는 경우 SQL 결과 오류가 발생합니다.](#bug-49364%EC%B5%9C%ED%95%98%EC%9C%84-left-outer-join-%EC%97%90%EC%84%9C-%EB%84%90-%ED%8C%A8%EB%94%A9null-padding%EC%9D%B4-%EB%B0%9C%EC%83%9D%ED%95%98%EA%B3%A0-%EC%A4%91%EA%B0%84-left-outer-join%EC%97%90%EC%84%9C-%EB%84%90-%ED%8C%A8%EB%94%A9%EC%9D%B4-%EB%B0%9C%EC%83%9D%ED%95%98%EC%A7%80-%EC%95%8A%EB%8A%94-%EA%B2%BD%EC%9A%B0-sql-%EA%B2%B0%EA%B3%BC-%EC%98%A4%EB%A5%98%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->



Altibase 7.1.0.6.3 Patch Notes
==============================

New Features
------------

### BUG-49274 altiComp에 사용자가 커밋 카운트를 조정하는 프로퍼티를 추가합니다.

-   **module** : ux-audit(altiComp)

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : altiComp에 사용자가 커밋(commit) 카운트를 설정할 수 있는 프로퍼티 COUNT\_TO\_COMMIT를 추가합니다. 
    
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

### BUG-49324 statement 객체가 남은 상태에서 Altibase 비정상 종료 가능성을 회피하기 위해 예외 처리를 추가합니다.

-   **module** : qp-meta

-   **Category** : Memory Error

-   **재현 빈도** : Always

-   **설명** : statement 객체가 남은 상태에서 Altibase 비정상 종료 가능성을 회피하기 위해 예외 처리를 추가합니다.
    
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

### BUG-49354 BUG-49063에서 추가한 V\$QUEUE를 삭제하고 V\$QUEUE\_DELETE\_OFF를 추가합니다.

-   **module** : sm

-   **Category** : Usability

-   **재현 빈도** : Always

-   **설명** : BUG-49063 반영 전 생성한 큐(QUEUE) 객체 추출 시 발생한 버그 조치를 위해 V\$QUEUE를 삭제하고 V\$QUEUE\_DELETE\_OFF를 추가합니다.
    
-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
        -   V\$QUEUE 성능 뷰 삭제

        - [V\$QUEUE\_DELETE\_OFF](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_4.md#vqueue_delete_off) 추가
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49350 aexport 에서 큐(QUEUE) 객체 스키마 추출 시 [ERR-00000 : ] 에러가 발생합니다.

-   **module** : ux-aexport

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : aexport에서 큐(QUEUE) 객체 스키마 추출 시 [ERR-00000 : ] 에러가 발생하는 현상을 수정합니다.

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

### BUG-49364 최하위 LEFT OUTER JOIN 에서 널 패딩(null padding)이 발생하고 중간 LEFT OUTER JOIN에서 널 패딩이 발생하지 않는 경우 SQL 결과 오류가 발생합니다.

-   **module** : qp-select

-   **Category** : Reliability

-   **재현 빈도** : Always

-   **설명** : 최하위 LEFT OUTER JOIN 에서 널 패딩(null padding)이 발생하고 중간 LEFT OUTER JOIN에서 널 패딩이 발생하지 않는 경우 SQL 결과 오류가 발생합니다. 이 버그는 중첩된 LEFT OUTER JOIN에서 오른쪽 읽기 skip 기능을 활성화 한 경우 발생합니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    DROP TABLE AA CASCADE;
    DROP TABLE BB CASCADE;
    DROP TABLE CC CASCADE;
    DROP TABLE DD CASCADE;
    
    CREATE TABLE AA (KEY INT, VAL INT ) TABLESPACE SYS_TBS_DISK_DATA;
    CREATE TABLE BB (KEY INT, VAL INT ) TABLESPACE SYS_TBS_DISK_DATA;
    CREATE TABLE CC (KEY INT, VAL INT ) TABLESPACE SYS_TBS_DISK_DATA;
    CREATE TABLE DD (KEY INT, VAL INT ) TABLESPACE SYS_TBS_DISK_DATA;
    
    ALTER TABLE AA ADD CONSTRAINT AA_PK PRIMARY KEY (KEY);
    ALTER TABLE BB ADD CONSTRAINT BB_PK PRIMARY KEY (KEY);
    ALTER TABLE CC ADD CONSTRAINT CC_PK PRIMARY KEY (KEY);
    ALTER TABLE DD ADD CONSTRAINT DD_PK PRIMARY KEY (KEY);
    
    INSERT INTO AA VALUES(1, 1);
    INSERT INTO BB VALUES(1, 1);
    INSERT INTO CC VALUES(2, 2);
    INSERT INTO DD VALUES(1, 1);
    
    ALTER SESSION SET EXPLAIN PLAN=ON;
    ALTER SESSION SET TRCLOG_DETAIL_PREDICATE=1;
    ALTER SESSION SET TRCLOG_DETAIL_INFORMATION=1;
    ALTER SYSTEM SET __LEFT_OUTER_SKIP_RIGHT_ENABLE = 0;
    
    SELECT
           /*+ no_plan_cache LEADING(A) USE_NL(A B C D) */
           A.KEY
         , K.VAL
      FROM AA A
           LEFT OUTER JOIN CC C ON C.KEY = A.KEY AND C.KEY = 2
           LEFT OUTER JOIN DD D ON D.KEY = A.KEY
           LEFT OUTER JOIN BB K ON K.KEY = D.KEY;
    ```

  - **수행 결과**

    ```sql
    KEY         VAL
    ---------------------------
    1           1
    1 row selected.
    ```

  -   **예상 결과**

      ```sql
      KEY         VAL
      ---------------------------
      1           
      1 row selected.
      ```

- **Workaround**

  ```sql
  ALTER SYSTEM SET __LEFT_OUTER_SKIP_RIGHT_ENABLE = 0;
  ```

- **변경사항**

  -   Performance view

  -   Property
  -   Compile Option
  -   Error Code

Changes
-------

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    7.1.0.6.3     |          6.5.1          |    8.10.1    |        7.1.7        |            7.4.6             |

> Altibase 7.1 패치 버전별 히스토리는 [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.1/Altibase_7_1_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

> 메타 버전이 변경된 패치 버전을 롤백하려는 경우, [메타다운그레이드](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Installation%20Guide.md#%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9Cmeta-downgrade)를 참고한다.

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

- [V\$QUEUE\_DELETE\_OFF](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_4.md#vqueue_delete_off)

#### 변경된 성능 뷰

#### 삭제된 성능 뷰

- V\$QUEUE
