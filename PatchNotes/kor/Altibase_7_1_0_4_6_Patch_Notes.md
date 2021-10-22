<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Altibase 7.1.0.4.6 Patch Notes](#altibase-71046-patch-notes)
  - [New Features](#new-features)
    - [BUG-48161  bucket count max 조절하는 프로퍼티 추가](#bug-48161-bucket-count-max-%EC%A1%B0%EC%A0%88%ED%95%98%EB%8A%94-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0-%EC%B6%94%EA%B0%80)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-48111  Sequence에 ENABLE SYNC TABLE 옵션을 사용하면 sequence의 CYCLE 여부를 확인할 수 없습니다.](#bug-48111-sequence%EC%97%90-enable-sync-table-%EC%98%B5%EC%85%98%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%98%EB%A9%B4-sequence%EC%9D%98-cycle-%EC%97%AC%EB%B6%80%EB%A5%BC-%ED%99%95%EC%9D%B8%ED%95%A0-%EC%88%98-%EC%97%86%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-48145  Altibase 7.1.0.3.0 이상 클라이언트(CLI)에서 GLOBAL\_TRANSACTION\_LEVEL을 지원하지 않는 서버(7.1.0.2.9 이하 서버)에 접속되지 않는 문제가 있습니다.](#bug-48145-altibase-71030-%EC%9D%B4%EC%83%81-%ED%81%B4%EB%9D%BC%EC%9D%B4%EC%96%B8%ED%8A%B8cli%EC%97%90%EC%84%9C-global%5C_transaction%5C_level%EC%9D%84-%EC%A7%80%EC%9B%90%ED%95%98%EC%A7%80-%EC%95%8A%EB%8A%94-%EC%84%9C%EB%B2%8471029-%EC%9D%B4%ED%95%98-%EC%84%9C%EB%B2%84%EC%97%90-%EC%A0%91%EC%86%8D%EB%90%98%EC%A7%80-%EC%95%8A%EB%8A%94-%EB%AC%B8%EC%A0%9C%EA%B0%80-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Altibase 7.1.0.4.6 Patch Notes
==============================

New Features
------------

### BUG-48161  bucket count max 조절하는 프로퍼티 추가

-   **module** : qp-select-pvo

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **증상** : bucket count max 를 조절하기 위한 세션 프로퍼티가 추가되었습니다.

-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
        -   추가
            -   __OPTIMIZER_BUCKET_COUNT_MAX
                -   설명: Bucket Count Max 조절
                -   기본값: 102400000
                -   최소값: 1024
                -   최대값: 102400000
    -   Compile Option
    -   Error Code

Fixed Bugs
----------

### BUG-48111  Sequence에 ENABLE SYNC TABLE 옵션을 사용하면 sequence의 CYCLE 여부를 확인할 수 없습니다.

-   **module** : qp-meta

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : Sequence 생성시 ENABLE SYNC TABLE 옵션을 사용했을 때,
    V\$SEQ에서 CYCLE 옵션이 제대로 표시되지 않는 문제를 수정했습니다.

    기존에는 ENABLE SYNC TABLE 옵션이 있는 SEQUENCE는 CYCLE 옵션이
    표시되지 않거나, UNKNOWN으로 표시되었습니다.

    BUG 수정 이후에는 CYCLE 옵션이 정상적으로 출력됩니다.

-   **재현 방법**

    -   **재현 절차**

            CREATE SEQUENCE S1 MINVALUE 1 MAXVALUE 5 CACHE 2 CYCLE ENABLE SYNC TABLE;
            select a.table_name, b.is_cycle from system_.sys_tables_ a, v$seq b where a.table_oid = b.seq_oid and a.table_name = 'S1';
            select * from seq;

    -   **수행 결과**

            iSQL> select a.table_name, b.is_cycle from system_.sys_tables_ a, v$seq b where a.table_oid = b.seq_oid and a.table_name = 'S1';
            TABLE_NAME                      IS_CYCLE
            -------------------------------------------------------------------
            S1                              UNKNOWN
            1 row selected.
            iSQL> select * from seq;
            USER_NAME                       SEQUENCE_NAME                   CURRENT_VALUE        INCREMENT_BY         MIN_VALUE            MAX_VALUE            CYCLE                           CACHE_SIZE
            ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
            SYS                             S1                                                   1                    1                    5                                                    2
            1 row selected.

    -   **예상 결과**

            iSQL> select a.table_name, b.is_cycle from system_.sys_tables_ a, v$seq b where a.table_oid = b.seq_oid and a.table_name = 'S1';
            TABLE_NAME                      IS_CYCLE
            -------------------------------------------------------------------
            S1                              YES
            1 row selected.
            iSQL> select * from seq;
            USER_NAME                       SEQUENCE_NAME                   CURRENT_VALUE        INCREMENT_BY         MIN_VALUE            MAX_VALUE            CYCLE                           CACHE_SIZE
            ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
            SYS                             S1                                                   1                    1                    5                    YES                             2
            1 row selected.

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48145  Altibase 7.1.0.3.0 이상 클라이언트(CLI)에서 GLOBAL\_TRANSACTION\_LEVEL을 지원하지 않는 서버(7.1.0.2.9 이하 서버)에 접속되지 않는 문제가 있습니다.

-   **module** : sharding

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : 7.1.0.3.0 이상의 클라이언트(CLI)가 7.1.0.2.9 이하 서버에 접속시
    프로퍼티 GLOBAL\_TRANSACTION\_LEVEL로 인해 접속 되지 않는 문제를 수정하였습니다.

    참고로 ShardCLI인 경우에는 GLOBAL\_TRANSACTION\_LEVEL이 반드시
    필요하므로 접속 되지 않는게 정상입니다.

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
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 7.1.0.4.6        | 6.5.1                   | 8.9.1        | 7.1.7               | 7.4.6                        |

> Altibase 7.1 패치 버전별 히스토리는 [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7_1_Version_Histories.md)에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의
> 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는
> 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

> 패치를 롤백하려는 경우, [메타다운그레이드](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Installation.md#%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9Cmeta-downgrade)를 참고한다.

#### CM protocol Version

통신 프로토콜 버전은 변경되지 않았다.

#### Replication protocol Version

Replication 프로토콜 버전은 변경되지 않았다.

### 프로퍼티

#### 추가된 프로퍼티

* __OPTIMIZER_BUCKET_COUNT_MAX

### 성능 뷰
