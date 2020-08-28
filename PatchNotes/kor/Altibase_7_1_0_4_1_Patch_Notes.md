<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Altibase 7.1.0.4.1 Patch Notes](#altibase-71041-patch-notes)
  - [New Features](#new-features)
    - [BUG-47931 ST_MakePolygon, ST_Polygon 함수 지원](#bug-47931st_makepolygon-st_polygon-%ED%95%A8%EC%88%98-%EC%A7%80%EC%9B%90)
    - [BUG-47985 ST_LinestringFromWKB 함수 지원](#bug-47985st_linestringfromwkb-%ED%95%A8%EC%88%98-%EC%A7%80%EC%9B%90)
    - [BUG-48007 aexport 에서 내부적으로 Not null 컬럼 정보 수집 방법을 변경하여 성능을 개선합니다.](#bug-48007aexport-%EC%97%90%EC%84%9C-%EB%82%B4%EB%B6%80%EC%A0%81%EC%9C%BC%EB%A1%9C-not-null-%EC%BB%AC%EB%9F%BC-%EC%A0%95%EB%B3%B4-%EC%88%98%EC%A7%91-%EB%B0%A9%EB%B2%95%EC%9D%84-%EB%B3%80%EA%B2%BD%ED%95%98%EC%97%AC-%EC%84%B1%EB%8A%A5%EC%9D%84-%EA%B0%9C%EC%84%A0%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-47888 altibase 실행파일의 버전과 dumptrc의 버전이 다를 경우, dumptrc로 출력된 콜스택이 부정확 할 수 있습니다.](#bug-47888altibase-%EC%8B%A4%ED%96%89%ED%8C%8C%EC%9D%BC%EC%9D%98-%EB%B2%84%EC%A0%84%EA%B3%BC-dumptrc%EC%9D%98-%EB%B2%84%EC%A0%84%EC%9D%B4-%EB%8B%A4%EB%A5%BC-%EA%B2%BD%EC%9A%B0-dumptrc%EB%A1%9C-%EC%B6%9C%EB%A0%A5%EB%90%9C-%EC%BD%9C%EC%8A%A4%ED%83%9D%EC%9D%B4-%EB%B6%80%EC%A0%95%ED%99%95-%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-47959  PSM 인자에 precision을 지정하지 않은 경우 PSM 실행(execution)시, 잘못된 메모리 참조로 altibase 서버가 비정상 종료 할 수 있습니다.](#bug-47959-psm-%EC%9D%B8%EC%9E%90%EC%97%90-precision%EC%9D%84-%EC%A7%80%EC%A0%95%ED%95%98%EC%A7%80-%EC%95%8A%EC%9D%80-%EA%B2%BD%EC%9A%B0-psm-%EC%8B%A4%ED%96%89execution%EC%8B%9C-%EC%9E%98%EB%AA%BB%EB%90%9C-%EB%A9%94%EB%AA%A8%EB%A6%AC-%EC%B0%B8%EC%A1%B0%EB%A1%9C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C-%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-48004 altibase 6.5.1 대비 altibase 7.1 에서 aexport 성능 이슈가 있습니다.](#bug-48004altibase-651-%EB%8C%80%EB%B9%84-altibase-71-%EC%97%90%EC%84%9C-aexport-%EC%84%B1%EB%8A%A5-%EC%9D%B4%EC%8A%88%EA%B0%80-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-48015 ALA protocol 변경으로 인해 jdbcAdapter가 Altibase 6.5.1 이하 버전과 연동 되지 않습니다.](#bug-48015ala-protocol-%EB%B3%80%EA%B2%BD%EC%9C%BC%EB%A1%9C-%EC%9D%B8%ED%95%B4-jdbcadapter%EA%B0%80-altibase-651-%EC%9D%B4%ED%95%98-%EB%B2%84%EC%A0%84%EA%B3%BC-%EC%97%B0%EB%8F%99-%EB%90%98%EC%A7%80-%EC%95%8A%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-48016 array에서 SQLExecute 실패하는 레코드가 있으면, array \* commit\_unit이 아닌 파일이 끝날때 한번만 호출됩니다.](#bug-48016array%EC%97%90%EC%84%9C-sqlexecute-%EC%8B%A4%ED%8C%A8%ED%95%98%EB%8A%94-%EB%A0%88%EC%BD%94%EB%93%9C%EA%B0%80-%EC%9E%88%EC%9C%BC%EB%A9%B4-array-%5C-commit%5C_unit%EC%9D%B4-%EC%95%84%EB%8B%8C-%ED%8C%8C%EC%9D%BC%EC%9D%B4-%EB%81%9D%EB%82%A0%EB%95%8C-%ED%95%9C%EB%B2%88%EB%A7%8C-%ED%98%B8%EC%B6%9C%EB%90%A9%EB%8B%88%EB%8B%A4)
    - [BUG-48018 disk table에 left outer join 시 OR 절과 결합된 constant predicate이 존재할경우 결과 오류](#bug-48018disk-table%EC%97%90-left-outer-join-%EC%8B%9C-or-%EC%A0%88%EA%B3%BC-%EA%B2%B0%ED%95%A9%EB%90%9C-constant-predicate%EC%9D%B4-%EC%A1%B4%EC%9E%AC%ED%95%A0%EA%B2%BD%EC%9A%B0-%EA%B2%B0%EA%B3%BC-%EC%98%A4%EB%A5%98)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Altibase 7.1.0.4.1 Patch Notes
==============================

New Features
------------

### BUG-47931 ST_MakePolygon, ST_Polygon 함수 지원

- **module** : st

- **Category** : Enhancement

- **재현 빈도** : Always

- **증상** : [ST_MakePolygon](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/SpatialSQL.md#st_makepolygon) 함수와 [ST_Polygon](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/SpatialSQL.md#st_polygon) 함수가 추가되었습니다. 

  ST_MakePolygon 함수는 LineString 객체를 입력 받아 Polygon 객체를 생성합니다. 이 때 LineString은 반드시 Ring 형태여야 합니다.

  ST_Polygon 함수는 LineString과 SRID를 입력 받아 SRID를 갖는 Polygon 객체를 생성합니다.

  ```
  ST_MAKEPOLYGON( GEOMETRY )
  ST_POLYGON( GEOMETRY, SRID )
  ```

-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

- **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47985 ST_LinestringFromWKB 함수 지원

-   **module** : st-function

-   **Category** : Enhancement

-   **재현 빈도** : Always

- **증상** : ST_LINESTRINGFROMWKB 함수가 추가되었습니다.

  **구문**

  ```
  ST_LINESTRINGFROMWKB( WKB[, SRID] )
  ```

  **설명**

  WKB(Well-Known Binary) 형태 또는 EWKT(Extended Well-Known Text)
  형태의 공간 객체와 SRID를 입력 받아 폴리곤 객체를 생성합니다.

  WKB의 값이 NULL이거나 SRID의 값이 NULL인 경우에는 NULL을 반환합니다.

  LINEFROMWKB와 달리 라인스트링이 아닌 공간 객체를 표현한 WKT또는
  EWKT인 경우에는 NULL을 반환합니다.

  WKT 형태 또는 EWKT 형태가 문법이 잘못된 경우 에러를 출력합니다.

  SRID를 입력하지 않으면 생성된 객체의 SRID는 0입니다.

  **반환 타입**

  GEOMETRY

- **재현 방법**

  -   **재현 절차**

          SELECT ASEWKT(ST_LINESTRINGFROMWKB( ASBINARY( geometry'linestring(1 1, 4 1)') , 130)) as geom;

  -   **수행 결과**

  -   **예상 결과**

          GEOM
          ------------------------
          SRID=130;LINESTRING(1 1, 4 1)

-   **Workaround**

        ST_LINEFROMWKB() + SET_SRID()(단, linestring이 아닌 경우 에러 발생)

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48007 aexport 에서 내부적으로 Not null 컬럼 정보 수집 방법을 변경하여 성능을 개선합니다.

-   **module** : ux-aexport

-   **Category** : Efficiency

-   **재현 빈도** : Always

-   **증상** : Not null 컬럼 정보 수집 방법을 개별 컬럼 단위에서 테이블 단위로 변경하여 성능을 개선하였습니다.
    
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

### BUG-47888 altibase 실행파일의 버전과 dumptrc의 버전이 다를 경우, dumptrc로 출력된 콜스택이 부정확 할 수 있습니다.

-   **module** : id

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **증상** : altibase 실행파일의 버전과 dumptrc의 버전이 다를 경우는
    경고메시지를 보여주고, 콜스택을 출력하지 않도록 수정되었습니다. 
    
    altibase 실행파일의 버전과 dumptrc의 버전이 다른 경우, 정확한 콜스택을 출력하기 위해서 -x 옵션이 추가되었습니다.

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

### BUG-47959  PSM 인자에 precision을 지정하지 않은 경우 PSM 실행(execution)시, 잘못된 메모리 참조로 altibase 서버가 비정상 종료 할 수 있습니다.

-   **module** : qp

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **증상** :  PSM 인자에 precision을 지정하지 않은 경우에 대한 예외처리가 누락되어 있어 발생한 문제로, 비정상 종료하지 않고 정상적으로 실행(execution)되도록 수정하였습니다.

- **재현 방법**

  - **재현 절차**

        drop table t6;
        drop table t7;
        drop table t8;
        
        create table t6( PLZ_ID  VARCHAR(6)      FIXED );
        insert into t6 values ('101001');
        create table t7( PLZ_ID  VARCHAR(6) FIXED, RECVR_TN  VARCHAR(1)      FIXED );
        insert into t7 values ('101001', '0');
        create table t8( MAJOR_CD   VARCHAR(3) FIXED, SCLSS_CD VARCHAR(6)  FIXED );
        
        CREATE OR REPLACE FUNCTION FUNC_CONV_CODENAME (P_LCLSS_CD IN VARCHAR2, P_SCLSS_CD IN VARCHAR2, P_WRITE_TYPE IN VARCHAR2)
        RETURN VARCHAR2 IS
            V_RTN VARCHAR2(100);
            V_COUNT NUMBER;
        BEGIN
            V_COUNT := 0;
        
            SELECT COUNT(*)
              INTO V_COUNT
              FROM t8
             WHERE MAJOR_CD = P_LCLSS_CD
               AND SCLSS_CD = P_SCLSS_CD;
            RETURN V_RTN;
         EXCEPTION
         WHEN OTHERS THEN
            V_RTN := P_SCLSS_CD;
            RETURN V_RTN;
        END;
        ;
        /


        
            SELECT  /*+ no_plan_cache */
               FUNC_CONV_CODENAME('592', T1.ERR_CD,     cast('en' as varchar(4))) AS ERR_CD      --이상내역
               ,FUNC_CONV_CODENAME('526', T1.RECVR_TN,   cast('en' as varchar(4))) AS RECVR_TN    --발생/복구 구분
            FROM  ( SELECT 
                         ''         AS ERR_CD        ---에러코드       
                        ,cast('Gen. Count:' as varchar(50)) || ' ' || nvl(sum(CASE WHEN T2.RECVR_TN = '0' THEN 1 else 0 end), 0) AS RECVR_TN  --발생건수(0:발생, 1:복구(526))
                   FROM  T6 T1, T7 T2
                  WHERE  T1.PLZ_ID       = T2.PLZ_ID
                  group  by T1.PLZ_ID 
                )  T1;


        
            SELECT  /*+ no_plan_cache */
               FUNC_CONV_CODENAME('592', T1.ERR_CD,     cast('en' as varchar(4))) AS ERR_CD      --이상내역
               ,FUNC_CONV_CODENAME('526', T1.RECVR_TN,   cast('en' as varchar(4))) AS RECVR_TN    --발생/복구 구분
            FROM  ( SELECT 
                         ''         AS ERR_CD        ---에러코드       
                        ,cast('Gen. Count:' as varchar(50)) || ' ' || nvl(sum(CASE WHEN T2.RECVR_TN = '0' THEN 1 else 0 end), 0) AS RECVR_TN  --발생건수(0:발생, 1:복구(526))
                   FROM  T6 T1, T7 T2
                  WHERE  T1.PLZ_ID       = T2.PLZ_ID
                  group  by T1.PLZ_ID 
                )  T1;

  -   **수행 결과**

          [ERR-91015 : Communication failure.]

  -   **예상 결과**

          1 row selected.

-   **Workaround**

        No

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48004 altibase 6.5.1 대비 altibase 7.1 에서 aexport 성능 이슈가 있습니다.

-   **module** : ux-aexport

-   **Category** : Efficiency

-   **재현 빈도** : Always

-   **증상** : altibase 6.5.1에서 altibase 7.1 으로 업그레이드시,
    aexport 성능 하락 이슈가 있어 수정하였습니다.

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

### BUG-48015 ALA protocol 변경으로 인해 jdbcAdapter가 Altibase 6.5.1 이하 버전과 연동 되지 않습니다.

-   **module** : rp-jdbcAdapter

-   **Category** : Other

-   **재현 빈도** : Always

-   **증상** : altibase 7.1.0.4.0 에서 ALA protocol이 버전이 7.4.6으로 변경됨에 따라 Altibase 7.1.0.4.0의 jdbcAdapter가 Altibase 하위버전(6.5.1 이하 버전)과 호환 되지 않는 문제가 있었습니다.
    

Altibase 버전에 맞춰 ALA protocol을 변경하도록
    수정하여 jdbcAdpater가 하위 버전과 호환 되도록 수정하였습니다.
    
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

### BUG-48016 array에서 SQLExecute 실패하는 레코드가 있으면, array \* commit\_unit이 아닌 파일이 끝날때 한번만 호출됩니다.

-   **module** : ux-iloader

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : iLoader에서 array로 data in을 하는 도중 data insert가
    실패하면 commit이 skip되고, 마지막에 한번만 commit이 호출되는 오류를
    수정했습니다.

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

### BUG-48018 disk table에 left outer join 시 OR 절과 결합된 constant predicate이 존재할경우 결과 오류

-   **module** : qp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : disk table에 left outer join 시 OR 절과 결합된 constant
    predicate이 존재할경우 결과 오류 문제를 수정합니다.

- **재현 방법**

  - **재현 절차**

        drop table MA_PLANT_MST;
        drop table MA_BIZAREA_MST;
        create table MA_PLANT_MST( 
        COMPANY_CD                               VARCHAR(28)                 NOT NULL,
        PLANT_CD                                 VARCHAR(28)                 NOT NULL,
        PLANT_NM                                 VARCHAR(200)                NOT NULL
        ) tablespace sys_tbs_disk_data;
        alter table MA_PLANT_MST add primary key ( COMPANY_CD, PLANT_CD );
        INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('1000', 'DETAIL_AUTH_NOT_USED', 'TEST');
        INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('1001', 'DETAIL_AUTH_NOT_USED', 'TEST');
        INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('1002', 'DETAIL_AUTH_NOT_USED', 'TEST');
        INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('1003', 'DETAIL_AUTH_NOT_USED', 'TEST');
        INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('1004', 'DETAIL_AUTH_NOT_USED', 'TEST');
        INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('1005', 'DETAIL_AUTH_NOT_USED', 'TEST');
        INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('1006', 'DETAIL_AUTH_NOT_USED', 'TEST');
        INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('1007', 'DETAIL_AUTH_NOT_USED', 'TEST');
        INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('1008', 'DETAIL_AUTH_NOT_USED', 'TEST');
        INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('1009', 'DETAIL_AUTH_NOT_USED', 'TEST');
        INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('1010', 'DETAIL_AUTH_NOT_USED', 'TEST');
        INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('1011', 'DETAIL_AUTH_NOT_USED', 'TEST');
        INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('1012', 'DETAIL_AUTH_NOT_USED', 'TEST');
        INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('1013', 'DETAIL_AUTH_NOT_USED', 'TEST');
        INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('KC_TEST', 'DETAIL_AUTH_NOT_USED1', 'TEST');
        INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('KC_TEST', 'DETAIL_AUTH_NOT_USED2', 'TEST');
        INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('KC_TEST', 'DETAIL_AUTH_NOT_USED3', 'TEST');
        INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('KC_TEST', 'DETAIL_AUTH_NOT_USED4', 'TEST');
        INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('KC_TEST', 'DETAIL_AUTH_NOT_USED5', 'TEST');
        INSERT INTO MA_PLANT_MST (COMPANY_CD, PLANT_CD, PLANT_NM) VALUES ('KC_TEST', 'DETAIL_AUTH_NOT_USED6', 'TEST');
        
        create table MA_BIZAREA_MST( 
        COMPANY_CD                               VARCHAR(28)                 NOT NULL,
        PLANT_CD                                 VARCHAR(28)                 NOT NULL,
        PLANT_NM                                 VARCHAR(200)                NOT NULL
        ) tablespace sys_tbs_disk_data;
        var AA varchar(7);
        var BB varchar(1);
        var CC varchar(28);
        exec :AA := 'KC_TEST';
        exec :BB := 'N';
        exec :CC := 'DETAIL_AUTH_NOT_USED';
        PREPARE
        SELECT   *
                        FROM    MA_PLANT_MST MPM
                        LEFT    OUTER JOIN MA_BIZAREA_MST MBM ON MBM.COMPANY_CD = MPM.COMPANY_CD
                        WHERE   MPM.COMPANY_CD = :AA
                        AND             (:BB = 'N' OR MPM.PLANT_CD IN
                         (
                                :CC
                         )
                                        );

  -   **수행 결과**

          No rows selected.

  -   **예상 결과**

          6 rows selected.

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
| 7.1.0.4.1        | 6.5.1                   | 8.8.1        | 7.1.7               | 7.4.6                        | 2.2.1            |

> Altibase 7.1 패치 버전별 히스토리는 [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7_1_Version_Histories.md)에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의
> 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는
> 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

> 패치를 롤백하려는 경우,
> [메타다운그레이드](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Installation.md#%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9Cmeta-downgrade)를
> 참고한다.

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

추가/변경/삭제된 성능 뷰 없음.