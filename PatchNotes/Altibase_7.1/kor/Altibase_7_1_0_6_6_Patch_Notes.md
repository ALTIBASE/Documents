<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  

- [Altibase 7.1.0.6.6 Patch Notes](#altibase-71066-patch-notes)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-49039 비활성화한 인덱스가 있는 경우 V\$SEGMENT 조회 시 Altibase 서버가 비정상 종료합니다.](#bug-49039%EB%B9%84%ED%99%9C%EC%84%B1%ED%99%94%ED%95%9C-%EC%9D%B8%EB%8D%B1%EC%8A%A4%EA%B0%80-%EC%9E%88%EB%8A%94-%EA%B2%BD%EC%9A%B0-vsegment-%EC%A1%B0%ED%9A%8C-%EC%8B%9C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-49423 SQL PLAN CACHE 처리 시 statement 객체가 정리되지 않은 경우 Altibase 서버가 비정상 종료하거나 CPU 사용률이 증가할 수 있습니다.](#bug-49423-sql-plan-cache-%EC%B2%98%EB%A6%AC-%EC%8B%9C-statement-%EA%B0%9D%EC%B2%B4%EA%B0%80-%EC%A0%95%EB%A6%AC%EB%90%98%EC%A7%80-%EC%95%8A%EC%9D%80-%EA%B2%BD%EC%9A%B0-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%98%EA%B1%B0%EB%82%98-cpu-%EC%82%AC%EC%9A%A9%EB%A5%A0%EC%9D%B4-%EC%A6%9D%EA%B0%80%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-49433 트랜잭션 커밋 수행 시 statement 객체가 정리되지 않은 경우 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-49433%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98-%EC%BB%A4%EB%B0%8B-%EC%88%98%ED%96%89-%EC%8B%9C-statement-%EA%B0%9D%EC%B2%B4%EA%B0%80-%EC%A0%95%EB%A6%AC%EB%90%98%EC%A7%80-%EC%95%8A%EC%9D%80-%EA%B2%BD%EC%9A%B0-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Altibase 7.1.0.6.6 Patch Notes
==============================

Fixed Bugs
----------

### BUG-49039 비활성화한 인덱스가 있는 경우 V\$SEGMENT 조회 시 Altibase 서버가 비정상 종료합니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : 비활성화한 인덱스가 있는 경우 V$SEGMENT 조회 시 Altibase 서버가 비정상 종료하는 현상을 수정합니다.

- **재현 방법**

  - **재현 절차**

    ```sql
    CREATE TABLE D1 ( I1 INTEGER, I2 CHAR(3000), I3 INTEGER ) TABLESPACE SYS_TBS_DISK_DATA;
    CREATE INDEX D1_I1_I2 ON D1(I1,I2);
    ALTER TABLE D1 ALL INDEX DISABLE;
    SELECT COUNT(*) FROM V$SEGMENT;
    ```

  - **수행 결과**

    ```
    Altibase 서버 비정상 종료
    ```

  - **예상 결과**

    ```
    SQL문 정상 수행
    ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49423 SQL PLAN CACHE 처리 시 statement 객체가 정리되지 않은 경우 Altibase 서버가 비정상 종료하거나 CPU 사용률이 증가할 수 있습니다. 

- **module** : mm-plancache

- **Category** : Maintainability

- **재현 빈도** : Frequence

- **설명** : SQL PLAN CACHE 처리 시 statement 객체가 정리되지 않은 경우 Altibase 서버가 비정상 종료하거나 CPU 사용률이 증가하는 현상을 수정합니다. 
  본 버그로 인한 Altibase 서버 비정상 종료 현상 발생 시 altibase_error.log 에 아래와 같은 로그가 남습니다. 

  ```bash
  IDE_ASSERT( aTrans->mStatus == SMX_TX_END ), [smxTransMgr.h:272], errno=[2]
  [[ASSERT] ERROR LINE => [smxTransMgr.h:272]
  ```

  또한 수행 중인 SQL문이 없거나 적음에도 CPU 사용률이 증가하는 현상을 나타날 수 있습니다. 

- **재현 방법**

  - **재현 절차**

  - **수행 결과**

  - **예상 결과**

- **Workaround**

- **변경사항**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

### BUG-49433 트랜잭션 커밋 수행 시 statement 객체가 정리되지 않은 경우 Altibase 서버가 비정상 종료할 수 있습니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : 트랜잭션 커밋(commit) 수행 시 statement 객체가 정리되지 않은 경우 Altibase 서버가 비정상 종료하는 현상을
    수정합니다. statement 객체를 강제 정리하고 문제 분석을 위한 콜스택을 Altibase 트레이스 로그에 기록합니다.
    
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
|    7.1.0.6.6     |          6.5.1          |    8.10.1    |        7.1.7        |            7.4.7             |

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

#### 변경된 성능 뷰

#### 삭제된 성능 뷰
