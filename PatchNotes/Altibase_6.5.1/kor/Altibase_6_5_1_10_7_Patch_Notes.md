Altibase 6.5.1.10.7 Patch Notes
===============================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Fixed Bugs](#fixed-bugs)
  - [BUG-51630 테이블, 뷰, 함수가 서로 참조하는 관계인 테이블에 DDL을 수행하면 오류가 발생합니다.](#bug-51530)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
  - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
  - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Fixed Bugs
==========

### BUG-51630<a name=bug-51530></a> 테이블, 뷰, 함수가 서로 참조하는 관계인 테이블에 DDL을 수행하면 오류가 발생합니다.

-   **module** : qp-ddl-dcl-execute

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 테이블, 뷰, 함수가 서로 참조하는 관계인 테이블에 DDL을 수행할 때, [ERR-01067 : The memory size allocated for the statement has exceeded the maximum limit] 오류가 발생하는 문제를 수정하였습니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    CREATE TABLE t1 (c1 CHAR(32000)) TABLESPACE SYS_TBS_DISK_DATA;
    CREATE OR REPLACE FUNCTION func1 RETURN CHAR(32000)
    AS
    var1 CHAR(32000);
    BEGIN
      SELECT c1 into var1 FROM t1 limit 1;
      RETURN var1;
    END;
    /
    CREATE OR REPLACE VIEW v1 AS SELECT func1() val1 FROM t1;
    ALTER TABLE t1 ADD (c2 varchar(32000));
    ALTER TABLE t1 ADD (c3 varchar(32000));
    ```

  - **수행 결과**

    ```sql
    [ERR-01067 : The memory size allocated for the statement has exceeded the maximum limit ( Name : Query_Prepare, Wanted Memory Size : 209732568, Max size : 209715200 ).]
    ```

  -   **예상 결과**

          Alter success.

-   **Workaround**

        Add column 전에 invalid 상태인 function을 compile하여 valid 상태로 변경한다.

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
| 6.5.1.10.7       | 6.3.1                   | 8.1.1        | 7.1.3               | 7.4.5                        |

> Altibase 6.5.1 패치 버전별 히스토리는 [Version_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_6.5.1/Altibase_6_5_1_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의
> 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는
> 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

#### CM protocol Version

통신 프로토콜 버전은 변경되지 않았다.

#### Replication protocol Version

Replication 프로토콜 버전은 변경되지 않았다.

### 프로퍼티

추가/변경/삭제된 프로퍼티 없음.

### 성능 뷰

추가/변경/삭제된 성능뷰 없음.
