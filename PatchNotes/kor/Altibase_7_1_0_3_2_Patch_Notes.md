<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Altibase 7.1.0.3.2 Patch Notes](#altibase-71032-patch-notes)
  - [New Features](#new-features)
    - [BUG-47388  TABLE LOCK 병목구간 개선](#bug-47388-table-lock-%EB%B3%91%EB%AA%A9%EA%B5%AC%EA%B0%84-%EA%B0%9C%EC%84%A0)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-47344  apre parser에서 conflicts 발생](#bug-47344-apre-parser%EC%97%90%EC%84%9C-conflicts-%EB%B0%9C%EC%83%9D)
    - [BUG-47492  login\_timeout이 서버 hang 상태에서 적용되지 않는다.](#bug-47492-login%5C_timeout%EC%9D%B4-%EC%84%9C%EB%B2%84-hang-%EC%83%81%ED%83%9C%EC%97%90%EC%84%9C-%EC%A0%81%EC%9A%A9%EB%90%98%EC%A7%80-%EC%95%8A%EB%8A%94%EB%8B%A4)
    - [BUG-47522  connect by 절에 variable key로 subquery가 있는 경우 비정상 종료 될 수 있습니다.](#bug-47522-connect-by-%EC%A0%88%EC%97%90-variable-key%EB%A1%9C-subquery%EA%B0%80-%EC%9E%88%EB%8A%94-%EA%B2%BD%EC%9A%B0-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C-%EB%90%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-47538  공간부족으로 인한 로그앵커 백업 실패 메시지 수정 또는 교체](#bug-47538-%EA%B3%B5%EA%B0%84%EB%B6%80%EC%A1%B1%EC%9C%BC%EB%A1%9C-%EC%9D%B8%ED%95%9C-%EB%A1%9C%EA%B7%B8%EC%95%B5%EC%BB%A4-%EB%B0%B1%EC%97%85-%EC%8B%A4%ED%8C%A8-%EB%A9%94%EC%8B%9C%EC%A7%80-%EC%88%98%EC%A0%95-%EB%98%90%EB%8A%94-%EA%B5%90%EC%B2%B4)
    - [BUG-47541  apre에서 '\\"' 처리 문제](#bug-47541-apre%EC%97%90%EC%84%9C-%5C%5C-%EC%B2%98%EB%A6%AC-%EB%AC%B8%EC%A0%9C)
    - [BUG-47551  COALESCE 함수가 사용될때 OUTER JOIN ELIMINATION 이 잘못 설정됩니다.](#bug-47551-coalesce-%ED%95%A8%EC%88%98%EA%B0%80-%EC%82%AC%EC%9A%A9%EB%90%A0%EB%95%8C-outer-join-elimination-%EC%9D%B4-%EC%9E%98%EB%AA%BB-%EC%84%A4%EC%A0%95%EB%90%A9%EB%8B%88%EB%8B%A4)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Altibase 7.1.0.3.2 Patch Notes
==============================

New Features
------------

### BUG-47388  TABLE LOCK 병목구간 개선

-   **module** : sm\_resource

-   **Category** : Efficiency

-   **재현 빈도** : Frequence

-   **증상** : TABLE LOCK 관리자 타입에서 Spin lock 모드가 제거 되고, light Mutex
모드가 추가되었습니다.
    
    이에 따라, 아래의 프로퍼티는 제거되지 않았지만, 설정값은 무시됩니다.

    LOCK\_MGR\_SPIN\_COUNT

    LOCK\_MGR\_MIN\_SLEEP

    LOCK\_MGR\_MAX\_SLEEP

    LOCK\_MGR\_DETECTDEADLOCK\_INTERVAL

    기존에 LOCK\_MGR\_TYPE 을 1로 설정한 경우는 패치이후 서버 구동시점에
아래의 에러가 발생할 수 있습니다.
    

ERR-111b6(errno=9) LOCK_MGR_TYPE 1 is deprecated.
-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
        -   변경
            -   LOCK_MGR_TYPE 의 설정값의 MAX가 변경되었습니다.
                -   1 -> 2
                -   1(Spin Lock 모드)이 제거
                -   2 (Light Mutex모드) 추가
    -   Compile Option
    -   Error Code

Fixed Bugs
----------

### BUG-47344  apre parser에서 conflicts 발생

-   **module** : mm

-   **Category** : Compile Error

-   **재현 빈도** : Always

-   **증상** : apre parser에서 compile시 conflicts 발생 수정

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

### BUG-47492  login\_timeout이 서버 hang 상태에서 적용되지 않는다.

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : login\_timeout 이 서버 hang 상태에서 적용되지 않는 문제점을 수정합니다.
    
-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**
    
    -   **예상 결과**
    
-   **Workaround**

        use response_timeout

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47522  connect by 절에 variable key로 subquery가 있는 경우 비정상 종료 될 수 있습니다.

-   **module** : qp-dml-pvo

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **증상** : connect by 절에 variable key로 subquery가 있는 경우,
    subquery에 대한 plan이 생성되지 않아 비정상 종료되는 문제가
    있었습니다. connect by 절에 variable key로 subquery가 있는 경우,
    subquery keyrange 최적화를 수행하지 않고, subquery filter로
    수행되도록 변경합니다.

- **재현 방법**

  -   **재현 절차**

          drop table RELATE_INSTT;
          drop table META;
          CREATE TABLE RELATE_INSTT (
          INSTT_CD CHAR(7) NOT NULL,
          ABBR_NM VARCHAR(90),
          HRNK_INSTT_CD CHAR(7),
          DEL_YN CHAR(1) NOT NULL
          )
          TABLESPACE SYS_TBS_DISK_DATA;
          ALTER TABLE RELATE_INSTT ADD CONSTRAINT RELATE_INSTT_PK PRIMARY KEY (INSTT_CD, DEL_YN);
          CREATE TABLE META (
          --META_INFO_SEQ INTEGER NOT NULL,
          CREAT_INSTT_CD VARCHAR(10),
          DEL_YN CHAR(1) NOT NULL
          )
          TABLESPACE SYS_TBS_DISK_DATA;
          --ALTER TABLE META ADD CONSTRAINT META_PK PRIMARY KEY (META_INFO_SEQ, DEL_YN);
          --- RELATE_INSTT 테이블
          INSERT INTO RELATE_INSTT (INSTT_CD, DEL_YN, HRNK_INSTT_CD) VALUES ('ABCDEF1','N','0');
          INSERT INTO RELATE_INSTT (INSTT_CD, DEL_YN, HRNK_INSTT_CD) VALUES ('ABCDEF2','N','0');
          INSERT INTO RELATE_INSTT (INSTT_CD, DEL_YN, HRNK_INSTT_CD) VALUES ('ABCDEF3','N','0');
          INSERT INTO RELATE_INSTT (INSTT_CD, DEL_YN, HRNK_INSTT_CD) VALUES ('ABCDEF4','N','0');
          INSERT INTO RELATE_INSTT (INSTT_CD, DEL_YN, HRNK_INSTT_CD) VALUES ('ABCDEF5','N','0');
          INSERT INTO RELATE_INSTT (INSTT_CD, DEL_YN, HRNK_INSTT_CD) VALUES ('ABCDEF6','N','0');
          INSERT INTO RELATE_INSTT (INSTT_CD, DEL_YN, HRNK_INSTT_CD) VALUES ('ABCDEF7','N','0');
          INSERT INTO RELATE_INSTT (INSTT_CD, DEL_YN, HRNK_INSTT_CD) VALUES ('ABCDEF8','N','0');
          INSERT INTO RELATE_INSTT (INSTT_CD, DEL_YN, HRNK_INSTT_CD) VALUES ('ABCDEF9','N','1');
          INSERT INTO RELATE_INSTT (INSTT_CD, DEL_YN, HRNK_INSTT_CD) VALUES ('ABCDEF0','N','1');
          --- META 테이블
          INSERT INTO META (DEL_YN, CREAT_INSTT_CD) VALUES ('N','ABCDEF1');
          INSERT INTO META (DEL_YN, CREAT_INSTT_CD) VALUES ('N','ABCDEF2');
          INSERT INTO META (DEL_YN, CREAT_INSTT_CD) VALUES ('N','ABCDEF3');
          INSERT INTO META (DEL_YN, CREAT_INSTT_CD) VALUES ('N','ABCDEF4');
          INSERT INTO META (DEL_YN, CREAT_INSTT_CD) VALUES ('N','ABCDEF5');
          INSERT INTO META (DEL_YN, CREAT_INSTT_CD) VALUES ('N','ABCDEF6');
          INSERT INTO META (DEL_YN, CREAT_INSTT_CD) VALUES ('N','ABCDEF7');
          INSERT INTO META (DEL_YN, CREAT_INSTT_CD) VALUES ('N','ABCDEF8');
          INSERT INTO META (DEL_YN, CREAT_INSTT_CD) VALUES ('N','ABCDEF9');
          INSERT INTO META (DEL_YN, CREAT_INSTT_CD) VALUES ('N','ABCDEF0');
          alter system set trclog_detail_mtrnode=1;
          alter session set trclog_detail_predicate=1;
          alter session set explain plan =on;
           SELECT /*+ no_plan_cache*/ A.INSTT_CD
                , A.HRNK_INSTT_CD
           FROM RELATE_INSTT A
           START WITH A.HRNK_INSTT_CD = '0'
           CONNECT BY PRIOR A.INSTT_CD = A.HRNK_INSTT_CD AND A.DEL_YN = 'N' AND A.INSTT_CD IN (SELECT CREAT_INSTT_CD FROM META WHERE DEL_YN = 'N');

  -   **수행 결과**

          [ERR-91015 : Communication failure.]

  -   **예상 결과**

          INSTT_CD  HRNK_INSTT_CD
          ----------------------------
          ABCDEF1  0
          ABCDEF2  0
          ABCDEF3  0
          ABCDEF4  0
          ABCDEF5  0
          ABCDEF6  0
          ABCDEF7  0
          ABCDEF8  0
          8 rows selected.

-   **Workaround**

        alter system set __OPTIMIZER_HIERARCHY_TRANSFORMATION=1;

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47538  공간부족으로 인한 로그앵커 백업 실패 메시지 수정 또는 교체

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **증상** : 로그 앵커 백업시 실패하면 나오는 메시지를 다음과 같이
    변경합니다.

    - 변경전: "Disk Space was insufficient during archive log backup. Check Space!!"

      ​				"Skip archiveing logfile(\< ... \>)"
    
-   변경후: "Log anchor file backup has failed!!"     
    
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

### BUG-47541  apre에서 '\\"' 처리 문제

-   **module** : mm-apre

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : apre에서 '\\"' 문자 precompile시에 [ERR-306L : Unterminated string error.] 에러가 발생하던 부분을 수정합니다.
    
- **재현 방법**

  -   **재현 절차**

          if (a == '\"')
          {
          }
          precompile시에 에러가 나지 않도록 처리.

  -   **수행 결과**

          apre -t cpp select.sc
          -----------------------------------------------------------------
               Altibase C/C++ Precompiler.
               Release Version 7.1.0.3.1
               Copyright 2000, ALTIBASE Corporation or its subsidiaries.
               All Rights Reserved.
          -----------------------------------------------------------------
          [ERR-306L : Unterminated string error.]
          File  : select.sc
          Line  : 57
          Offset: 0-0
          Error_token:

  -   **예상 결과**

          apre -t cpp select.sc
          -----------------------------------------------------------------
               Altibase C/C++ Precompiler.
               Release Version 7.1.0.3.2
               Copyright 2000, ALTIBASE Corporation or its subsidiaries.
               All Rights Reserved.
          -----------------------------------------------------------------

-   **Workaround**

        #define TEST '\"'
        if (a == TEST)
        {
        }

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47551  COALESCE 함수가 사용될때 OUTER JOIN ELIMINATION 이 잘못 설정됩니다.

-   **module** : qp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** :  COALESCE 함수에 outer join에 관련되서 predicate시 push
    되지 않도록 수정.

-   **재현 방법**

    -   **재현 절차**

            drop table t1;
            create table t1
            (
                "PROD_ID" VARCHAR(30) fixed not null,
                "HIS_REGIST_DTTM" VARCHAR(20) fixed not null
            );
            drop table t2;
            create table t2
            (
                "HIS_REGIST_DTTM" VARCHAR(20) fixed not null,
                "PROD_ID" VARCHAR(30) fixed not null
            );
            insert into t1 values('12P533A', 20190811123415004268);
            insert into t1 values('12P533A', 20190811123415004268);
            insert into t1 values('12P533A', 20190811123415004268);
            insert into t1 values('12P533A', 20190811123415004268);
            insert into t1 values('12P533A', 20190811123415004268);
            insert into t1 values('12P533A', 20190811125344601636);
            insert into t1 values('12P533B', 20191018170223812026);
            insert into t1 values('12P533B', 20191018170223812026);
            insert into t1 values('12P533B',20191018170223812026);
            insert into t1 values('12P533B', 20191018170223812026);
            insert into t1 values('12P533B', 20191018170223812026);
            insert into t1 values('12P533B', 20191018170223812026);
            insert into t1 values('12P533B', 20191018170223812026);
            insert into t1 values('12P533B', 20191018170223812026);
            insert into t1 values('12P533B', 20191018170223812026);
            
            select /*+  */ B.PROD_ID, PROD_ID1
                            FROM (
                                   SELECT
                                          COALESCE(A2.PROD_ID, COALESCE(A.PROD_ID, 'N/A')) AS PROD_ID
                                         ,COALESCE(A.PROD_ID, 'N/A') AS PROD_ID1
                                      FROM t1 A
                           LEFT OUTER JOIN t2 A2
                                            ON A2.HIS_REGIST_DTTM = A.HIS_REGIST_DTTM
                                   ) B
               where b.prod_id like '%12P533A%';
        
    -   **수행 결과**
    
            No rows selected.
        
    -   **예상 결과**
    
            PROD_ID                         PROD_ID1                        
            -------------------------------------------------------------------
            12P533A                         12P533A                         
            12P533A                         12P533A                         
            12P533A                         12P533A                         
            12P533A                         12P533A                         
            12P533A                         12P533A                         
        12P533A                         12P533A                         
            6 rows selected.

-   **Workaround**

        alter system set __OPTIMIZER_OUTERJOIN_ELIMINATION = 0;

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
| 7.1.0.3.2        | 6.5.1                   | 8.7.1        | 7.1.7               | 7.4.5                        | 2.2.1            |

> Altibase 7.1 패치 버전별 히스토리는 [Version_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7_1_Version_Histories.md) 에서 확인할 수 있다.

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

#### 변경된 프로퍼티

[LOCK_MGR_TYPE](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_1.md#lock_mgr_type)

### 성능 뷰

추가/변경/삭제된 성능뷰 없음.