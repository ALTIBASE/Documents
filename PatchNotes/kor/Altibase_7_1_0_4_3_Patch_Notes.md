<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Altibase 7.1.0.4.3 Patch Notes](#altibase-71043-patch-notes)
  - [New Features](#new-features)
    - [BUG-48038 ST_IsCollection 함수지원](#bug-48038%C2%A0st_iscollection-%ED%95%A8%EC%88%98%EC%A7%80%EC%9B%90)
    - [BUG-48052 Subquery Unnest 시 Prepare 시간 단축](#bug-48052%C2%A0subquery-unnest-%EC%8B%9C-prepare-%EC%8B%9C%EA%B0%84-%EB%8B%A8%EC%B6%95)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-47902 이중화가 SQL APPLY 모드로 수행 중일때 item 수가 같으나 테이블 구성이 다를 경우 이중화 start가 실패 할수 있습니다.](#bug-47902%C2%A0%EC%9D%B4%EC%A4%91%ED%99%94%EA%B0%80-sql-apply-%EB%AA%A8%EB%93%9C%EB%A1%9C-%EC%88%98%ED%96%89-%EC%A4%91%EC%9D%BC%EB%95%8C-item-%EC%88%98%EA%B0%80-%EA%B0%99%EC%9C%BC%EB%82%98-%ED%85%8C%EC%9D%B4%EB%B8%94-%EA%B5%AC%EC%84%B1%EC%9D%B4-%EB%8B%A4%EB%A5%BC-%EA%B2%BD%EC%9A%B0-%EC%9D%B4%EC%A4%91%ED%99%94-start%EA%B0%80-%EC%8B%A4%ED%8C%A8-%ED%95%A0%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-47924 aexport 에서 레코드를 가진 파티션이 여러 개 있는 로컬 파티션드 인덱스는 CREATE INDEX DDL이 여러번 나타납니다.](#bug-47924%C2%A0aexport-%EC%97%90%EC%84%9C-%EB%A0%88%EC%BD%94%EB%93%9C%EB%A5%BC-%EA%B0%80%EC%A7%84-%ED%8C%8C%ED%8B%B0%EC%85%98%EC%9D%B4-%EC%97%AC%EB%9F%AC-%EA%B0%9C-%EC%9E%88%EB%8A%94-%EB%A1%9C%EC%BB%AC-%ED%8C%8C%ED%8B%B0%EC%85%98%EB%93%9C-%EC%9D%B8%EB%8D%B1%EC%8A%A4%EB%8A%94-create-index-ddl%EC%9D%B4-%EC%97%AC%EB%9F%AC%EB%B2%88-%EB%82%98%ED%83%80%EB%82%A9%EB%8B%88%EB%8B%A4)
    - [BUG-48000 잘못된 프로퍼티를 설정한 다음, server stop , server kill을 수행하면 [ERR-91145 : Unable to open altibase.properties file.] 오류 발생합니다.](#bug-48000%C2%A0%EC%9E%98%EB%AA%BB%EB%90%9C-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0%EB%A5%BC-%EC%84%A4%EC%A0%95%ED%95%9C-%EB%8B%A4%EC%9D%8C-server-stop--server-kill%EC%9D%84-%EC%88%98%ED%96%89%ED%95%98%EB%A9%B4-err-91145--unable-to-open-altibaseproperties-file-%EC%98%A4%EB%A5%98-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-48022 Disk queue 에서 복수개의 클라이언트에서 동시 동작시 비정상 종료 할 수 있습니다.](#bug-48022%C2%A0disk-queue-%EC%97%90%EC%84%9C-%EB%B3%B5%EC%88%98%EA%B0%9C%EC%9D%98-%ED%81%B4%EB%9D%BC%EC%9D%B4%EC%96%B8%ED%8A%B8%EC%97%90%EC%84%9C-%EB%8F%99%EC%8B%9C-%EB%8F%99%EC%9E%91%EC%8B%9C-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C-%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-48051 geomFromWkb 함수로 insert한 레코드에 asbinary 함수를 사용하면 비정상종료하거나 변환한결과가 달라집니다.](#bug-48051%C2%A0geomfromwkb-%ED%95%A8%EC%88%98%EB%A1%9C-insert%ED%95%9C-%EB%A0%88%EC%BD%94%EB%93%9C%EC%97%90-asbinary-%ED%95%A8%EC%88%98%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EB%A9%B4-%EB%B9%84%EC%A0%95%EC%83%81%EC%A2%85%EB%A3%8C%ED%95%98%EA%B1%B0%EB%82%98-%EB%B3%80%ED%99%98%ED%95%9C%EA%B2%B0%EA%B3%BC%EA%B0%80-%EB%8B%AC%EB%9D%BC%EC%A7%91%EB%8B%88%EB%8B%A4)
    - [BUG-46427 Disk sort temp 에서 temp table 의 page 분배를 담당하는 프로퍼티- TEMP_SORT_GROUP_RATIO 와 SORT_AREA_SIZE 를 잘못 조정 할 경우, 쿼리수행이 불가능할 정도로 page 가 적게 할당 될 수 있는 문제가 있습니다.](#bug-46427%C2%A0disk-sort-temp-%EC%97%90%EC%84%9C-temp-table-%EC%9D%98-page-%EB%B6%84%EB%B0%B0%EB%A5%BC-%EB%8B%B4%EB%8B%B9%ED%95%98%EB%8A%94-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0--temp_sort_group_ratio-%EC%99%80-sort_area_size-%EB%A5%BC-%EC%9E%98%EB%AA%BB-%EC%A1%B0%EC%A0%95-%ED%95%A0-%EA%B2%BD%EC%9A%B0-%EC%BF%BC%EB%A6%AC%EC%88%98%ED%96%89%EC%9D%B4-%EB%B6%88%EA%B0%80%EB%8A%A5%ED%95%A0-%EC%A0%95%EB%8F%84%EB%A1%9C-page-%EA%B0%80-%EC%A0%81%EA%B2%8C-%ED%95%A0%EB%8B%B9-%EB%90%A0-%EC%88%98-%EC%9E%88%EB%8A%94-%EB%AC%B8%EC%A0%9C%EA%B0%80-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Altibase 7.1.0.4.3 Patch Notes
==============================

New Features
------------

### BUG-48038 ST_IsCollection 함수지원

-   **module** : st

-   **Category** : Enhancement

-   **재현 빈도** : Always

- **증상** : [ST_ISCOLLECTION](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/SpatialSQL.md#st_iscollection) 함수를 지원합니다.

  ##### 구문

  ```
  ST_ISCOLLECTION( GEOMETRY )
  ```

  ##### 설명

  인자로 받은 공간 객체가 Multi*이거나 GeometryCollection이면 1을 반환하고, 그렇지 않으면 0을 반환합니다.

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

### BUG-48052 Subquery Unnest 시 Prepare 시간 단축

-   **module** : qp-dml-pvo

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **증상** : Subquery Unnest 시 Prepare 시간 단축

-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

        alter system set OPTIMIZER_UNNEST_SUBQUERY=0

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

Fixed Bugs
----------

### BUG-47902 이중화가 SQL APPLY 모드로 수행 중일때 item 수가 같으나 테이블 구성이 다를 경우 이중화 start가 실패 할수 있습니다.

-   **module** : rp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : 이중화가 SQL APPLY 모드로 수행 중일때 item 총 개수가 같으면, 내부적으로 테이블 구성이 같은지를 확인하지 않아서 발생한 문제입니다.
    

item 개수가 같고, 테이블 구성이 다른 경우에도 이중화가 실패하지 않도록 수정하였습니다.
    
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

### BUG-47924 aexport 에서 레코드를 가진 파티션이 여러 개 있는 로컬 파티션드 인덱스는 CREATE INDEX DDL이 여러번 나타납니다.

-   **module** : ux-aexport

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : aexport에서 레코드를 가진 파티션이 여러 개 있는 로컬 파티션드 인덱스는 CREATE INDEX DDL 구문이 여러번 나타나는 현상을 수정했습니다.
    
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

### BUG-48000 잘못된 프로퍼티를 설정한 다음, server stop , server kill을 수행하면 [ERR-91145 : Unable to open altibase.properties file.] 오류 발생합니다.

-   **module** : ux-isql

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : isql과 altipasswd에서 내부적으로 idp 에러가 ut 에러 메세지로 가려지는 문제를 수정했습니다.
    
- **재현 방법**

  - **재현 절차**

        % export ALTIBASE_ISOLATION_LEVEL=3
        % server start

  - **수행 결과**

        % server start
        -----------------------------------------------------------------
             Altibase Client Query utility.
             Release Version 7.1.0.4.3
             Copyright 2000, ALTIBASE Corporation or its subsidiaries.
             All Rights Reserved.
        -----------------------------------------------------------------
        ISQL_CONNECTION = UNIX, SERVER = localhost
        [ERR-91145 : Unable to open altibase.properties file.]

  -   **예상 결과**

          % server start
          -----------------------------------------------------------------
               Altibase Client Query utility.
               Release Version 7.1.0.4.3
               Copyright 2000, ALTIBASE Corporation or its subsidiaries.
               All Rights Reserved.
          -----------------------------------------------------------------
          ISQL_CONNECTION = UNIX, SERVER = localhost
          [ERR-910FB : Connected to idle instance]
          idp checkRange() Error : Property [ISOLATION_LEVEL] 3 Overflowed the Value Range.(0~2)

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48022 Disk queue 에서 복수개의 클라이언트에서 동시 동작시 비정상 종료 할 수 있습니다.

-   **module** : sm-disk-index

-   **Category** : Fatal

-   **재현 빈도** : Frequence

-   **증상** : queue 를 Disk Tablespace 로 지정해서 생성하여, 복수개의 client 의 동시 동작에서 비정상 종료 합니다. 비정상 종료 원인 분석 결과 dequeue 실패한 쿼리가 index key를 제거하는 문제가 있어서 수정하였습니다.

-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

        disk tablespace에 queue를 생성하지 않거나,하나의 transaction 만 queue에 접근하도록 제한합니다.

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48051 geomFromWkb 함수로 insert한 레코드에 asbinary 함수를 사용하면 비정상종료하거나 변환한결과가 달라집니다.

-   **module** : st-function

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : POLYGON이 포함된 타입 ( POLYGON, MULTIPOLYGON,
    GEOMETRYCOLLECTION) 에 대해 geomFromWkb 함수로 insert한 레코드에
    asbinary 함수를 사용하면 비정상종료하거나 변환한결과가 달라집니다.

- **재현 방법**

  - **재현 절차**

        create table test( obj geometry );
        
        -- MULTIPOLYGON(((8 6,22 4,38 14,34 36,22 46,17 44,22 28,16 22,8 28,2 27,4 26)),((4 35,8 31,14 41,14 53,10 55,8 45,4 43,4 35))) 에 대한 WKB
        insert into TEST values ( geomFromWkb( BINARY'0106000000020000000103000000010000000b000000000000000000204000000000000018400000000000003640000000000000104000000000000043400000000000002c4000000000000041400000000000004240000000000000364000000000000047400000000000003140000000000000464000000000000036400000000000003c400000000000003040000000000000364000000000000020400000000000003c4000000000000000400000000000003b4000000000000010400000000000003a40010300000001000000080000000000000000001040000000000080414000000000000020400000000000003f400000000000002c4000000000008044400000000000002c400000000000804a4000000000000024400000000000804b40000000000000204000000000008046400000000000001040000000000080454000000000000010400000000000804140' ) );
        
        select astext(geomfromwkb( asbinary(obj) ) ) from test;

  - **수행 결과**

        -- linux 
        select astext(geomfromwkb( asbinary(obj) ) ) from test;
        ASTEXT(GEOMFROMWKB( ASBINARY(OBJ) ) )
        --------------------------------------------------------------------------------------------------------
        MULTIPOLYGON(((8 6, 22 4, 38 14, 34 36, 22 46, 17 44, 22 28, 16 22, 8 28, 2 27, 4 26, 0 4, 0 NAN)),
        ())
        1 row selected.
        
        -- aix 
        비정상 종료

  -   **예상 결과**

          MULTIPOLYGON(((8 6,22 4,38 14,34 36,22 46,17 44,22 28,16 22,8 28,2 27,4 26)),((4 35,8 31,14 41,14 53,10 55,8 45,4 43,4 35)))
          1 row selected.

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code
        -   83, stERR\_ABORT\_INVALID\_GEOMETRY\_MADEBY\_GEOMFROMWKB =
            Invalid Geometry(\<0%s\>)\
            \
            \# \*Cause: An attempt was made to perform an operation on
            an invalid geometry.\
            \
            \# \*Action: Check the error number from the trace log and
            contact Altibase’s Support Center
            (http://support.altibase.com).

### BUG-46427 Disk sort temp 에서 temp table 의 page 분배를 담당하는 프로퍼티- TEMP_SORT_GROUP_RATIO 와 SORT_AREA_SIZE 를 잘못 조정 할 경우, 쿼리수행이 불가능할 정도로 page 가 적게 할당 될 수 있는 문제가 있습니다. 

-   **module** : sm-disk-resource

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : disk sort temp 에서 temp table 의 page 분배를 담당하는 프로퍼티들을 잘못 조정 할 경우, 동작 불가능할 정도로 page 가 적게 할당 될 수 있어, 최소한의 필요한 page 를 가지도록 수정합니다.

- **재현 방법**

  - **재현 절차**

    ```
    ALTER SYSTEM SET QUERY_TIMEOUT = 0;
    ALTER SYSTEM SET DDL_TIMEOUT = 0;
    ALTER SYSTEM SET FETCH_TIMEOUT = 0;
    ALTER SYSTEM SET UTRANS_TIMEOUT = 0;
    ALTER SYSTEM SET IDLE_TIMEOUT = 0;
    ALTER SYSTEM SET TEMP_SORT_GROUP_RATIO=90;
    ALTER SYSTEM SET SORT_AREA_SIZE=524288;
    CREATE TABLE T1 ( I1 CHAR(1000), I2 CHAR(2000) ) tablespace
    sys_tbs_disk_data;
    CREATE TABLE T2 ( I1 CHAR(1000), I2 CHAR(2000) ) tablespace
    sys_tbs_disk_data;
    INSERT /*+APPEND*/ INTO T1 SELECT ROWNUM/5,ROWNUM
    FROM DUAL CONNECT BY LEVEL <= 300;
    INSERT /*+APPEND*/ INTO T2 SELECT
    ROWNUM/5+1,ROWNUM+1 FROM DUAL CONNECT BY LEVEL <=
    300;
    select count(I1) from ( SELECT I1,I2, SUM(I1) OVER ( PARTITION BY
    I1, I2), SUM(I2) OVER ( PARTITION BY I1, I2), SUM(I1) OVER
    ( PARTITION BY I2) , SUM(I1) OVER ( PARTITION BY I1) FROM T1
    ORDER BY I1,i2 );
    ```

  - 결과**

    ```
    [ERR-11069 : Internal server error in the storage manager
    ([FAILURE] ERR-0109E(error=16) Internal server error.)]
    ```

  - **예상 결과**

    ```
    COUNT( I1 )
    -----------------------
    300
    1 row selected.
    ```

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
| 7.1.0.4.3        | 6.5.1                   | 8.8.1        | 7.1.7               | 7.4.6                        | 2.2.1            |

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

#### Sharding Version

샤딩 버전은 변경 되지 않았다.

> 알티베이스 샤딩 프로토콜 및 메타는 상위, 하위 호환성을 보장하지
> 않는다. 즉, 샤딩 버전이 다른 경우, 재구성해야 한다.

### 프로퍼티

추가/변경/삭제된 프로퍼티 없음

### 성능 뷰

추가/변경/삭제된 성능뷰 없음