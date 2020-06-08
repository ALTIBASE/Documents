<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Altibase 7.1.0.3.9 Patch Notes](#altibase-71039-patch-notes)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-47836 LEFT OUTER JOIN 시 복합 인덱스가 사용되고 OR 절 predicate시 사용될 경우 결과가 틀릴수 있습니다.](#bug-47836left-outer-join-%EC%8B%9C-%EB%B3%B5%ED%95%A9-%EC%9D%B8%EB%8D%B1%EC%8A%A4%EA%B0%80-%EC%82%AC%EC%9A%A9%EB%90%98%EA%B3%A0-or-%EC%A0%88-predicate%EC%8B%9C-%EC%82%AC%EC%9A%A9%EB%90%A0-%EA%B2%BD%EC%9A%B0-%EA%B2%B0%EA%B3%BC%EA%B0%80-%ED%8B%80%EB%A6%B4%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-47846 sql 문자열이 32000자를 넘어갈 때 쿼리를 중복 실행하는 경우 encoding 에러가 발생할 수 있습니다.](#bug-47846sql-%EB%AC%B8%EC%9E%90%EC%97%B4%EC%9D%B4-32000%EC%9E%90%EB%A5%BC-%EB%84%98%EC%96%B4%EA%B0%88-%EB%95%8C-%EC%BF%BC%EB%A6%AC%EB%A5%BC-%EC%A4%91%EB%B3%B5-%EC%8B%A4%ED%96%89%ED%95%98%EB%8A%94-%EA%B2%BD%EC%9A%B0-encoding-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Altibase 7.1.0.3.9 Patch Notes
==============================

Fixed Bugs
----------

### BUG-47836 LEFT OUTER JOIN 시 복합 인덱스가 사용되고 OR 절 predicate시 사용될 경우 결과가 틀릴수 있습니다.

-   **module** : qp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : LEFT OUTER JOIN 시 복합인덱스가 사용되고 OR절 predicate시 사용될 경우 결과오류 수정
    
- **재현 방법**

  - **재현 절차**

        drop table CA_ACGRP_MST;
        drop table CA_ACGRP_LDTL;
        create table "CA_ACGRP_MST"
        (
            "GAAP_CD" VARCHAR(20)  ,
            "FORM_CD" VARCHAR(20)  ,
            "ACGRP_CD" VARCHAR(20)  ,
            "UP_GRP_CD" VARCHAR(20) 
        );
        alter table "CA_ACGRP_MST" add constraint "CA_ACGRP_MST_PK" primary key("GAAP_CD","FORM_CD","ACGRP_CD");
        
        insert into CA_ACGRP_MST    (   GAAP_CD,    FORM_CD,    ACGRP_CD,   UP_GRP_CD)                                  values (    1,  'D0012',    2,  3);
        insert into CA_ACGRP_MST    (   GAAP_CD,    FORM_CD,    ACGRP_CD,   UP_GRP_CD)                                  values (    1,  'D0012',    1,  3);
        insert into CA_ACGRP_MST    (   GAAP_CD,    FORM_CD,    ACGRP_CD,   UP_GRP_CD)                                  values (    1,  'D0012',    3,  3);
        insert into CA_ACGRP_MST    (   GAAP_CD,    FORM_CD,    ACGRP_CD,   UP_GRP_CD)                                  values (    1,  'D0022',    2,  3);
        insert into CA_ACGRP_MST    (   GAAP_CD,    FORM_CD,    ACGRP_CD,   UP_GRP_CD)                                  values (    1,  'D0032',    2,  3);
        
        create table "CA_ACGRP_LDTL"
        (
            "GAAP_CD" VARCHAR(20)  ,
            "FORM_CD" VARCHAR(20)  ,
            "ACGRP_CD" VARCHAR(20)  ,
            "LANG_CD" VARCHAR(20)  
        );
        alter table "CA_ACGRP_LDTL" add constraint "CA_ACGRP_LDTL_PK" primary key("GAAP_CD","FORM_CD","ACGRP_CD","LANG_CD");
        insert into CA_ACGRP_LDTL   (   GAAP_CD,    FORM_CD,    ACGRP_CD,   LANG_CD)                                        values (    1,  'D0012',    2,  'KO');
        insert into CA_ACGRP_LDTL   (   GAAP_CD,    FORM_CD,    ACGRP_CD,   LANG_CD)                                        values (    1,  'D0012',    1,  'KO');
        insert into CA_ACGRP_LDTL   (   GAAP_CD,    FORM_CD,    ACGRP_CD,   LANG_CD)                                        values (    1,  'D0012',    3,  'KO');
        insert into CA_ACGRP_LDTL   (   GAAP_CD,    FORM_CD,    ACGRP_CD,   LANG_CD)                                        values (    1,  'D0022',    2,  'KO');
        insert into CA_ACGRP_LDTL   (   GAAP_CD,    FORM_CD,    ACGRP_CD,   LANG_CD)                                        values (    1,  'D0032',    2,  'KO');
        var LANG varchar(20);
        var FORM varchar(80);
        var GAAP varchar(20);
        exec :LANG := 'KO';    
        exec :FORM := 'D0012';    
        exec :GAAP := '1';    
        PREPARE 
        SELECT /*  */
            A.GAAP_CD, 
            A.FORM_CD, 
            A.ACGRP_CD AS ACCT_CD
        FROM     CA_ACGRP_MST A
        LEFT OUTER JOIN CA_ACGRP_LDTL AA ON
        A.ACGRP_CD = AA.ACGRP_CD 
        WHERE    A.GAAP_CD = '1' AND  (A.FORM_CD = :FORM OR '' = :FORM );

  - **수행 결과**

        GAAP_CD               FORM_CD               ACCT_CD
        ----------------------------------------------------------------------
        1                     D0012                 1
        1                     D0012                 2
        1                     D0012                 2
        1                     D0012                 2
        1                     D0012                 3
        1                     D0022                 2
        1                     D0022                 2
        1                     D0022                 2
        1                     D0032                 2
        1                     D0032                 2
        1                     D0032                 2
        11 rows selected.
        ------------------------------------------------------------

  -   **예상 결과**

          GAAP_CD               FORM_CD               ACCT_CD
          ----------------------------------------------------------------------
          1                     D0012                 1
          1                     D0012                 2
          1                     D0012                 2
          1                     D0012                 2
          1                     D0012                 3
          5 rows selected.
          ------------------------------------------------------------

- **Workaround**

      PREPARE 
      SELECT /*+ NO INDEX(A,CA_ACGRP_MST_PK) */
          A.GAAP_CD, 
          A.FORM_CD, 
          A.ACGRP_CD AS ACCT_CD
      FROM     CA_ACGRP_MST A
      LEFT OUTER JOIN CA_ACGRP_LDTL AA ON
      A.ACGRP_CD = AA.ACGRP_CD 
      WHERE    A.GAAP_CD = '1' AND  (A.FORM_CD = :FORM OR '' = :FORM );
      
      * work around 사용 시 결과는 올바르지만 출력 순서가 달라질 수 있습니다. 

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47846 sql 문자열이 32000자를 넘어갈 때 쿼리를 중복 실행하는 경우 encoding 에러가 발생할 수 있습니다.

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : sql이 32000자가 넘어갈 때 문자열 인코딩 중 illegalStateException 이 발생할 수 있는 문제 수정.
    
- **재현 방법**

  -   **재현 절차**

          private void doTest() throws SQLException
              {
                  Connection sConn = getConnection("20300");
                  String sSql = makeSql();
                  Statement sStmt = sConn.createStatement();
                  ResultSet sRs = sStmt.executeQuery(sSql);
                  sRs.next();
                  sRs.close();
                  sStmt = sConn.createStatement();
                  sRs = sStmt.executeQuery(sSql);  // 두번째 execute 할때 encoding 에러 발생
                  sRs.next();
                  sRs.close();
              }
              private String makeSql()
              {
                  StringBuilder sSb1 = new StringBuilder();
                  for (int i = 0; i < 110; i++)
                  {
                      sSb1.append("가");
                  }
                  String sQuery = "select '" + sSb1.toString() + "' c0 from dual ";
                  StringBuilder sSb2 = new StringBuilder();
                  sSb2.append(sQuery);
                  for (int i = 0; i < 250; i++)
                  {
                      sSb2.append("union all ").append(sQuery);
                  }
                  return sSb2.toString();
              }

  - **수행 결과**

        Exception in thread "main" java.lang.IllegalStateException: Current state = CODING_END, new state = CODING
        	at java.nio.charset.CharsetEncoder.throwIllegalStateException(CharsetEncoder.java:992)
        	at java.nio.charset.CharsetEncoder.encode(CharsetEncoder.java:572)
        	at Altibase.jdbc.driver.cm.CmBufferWriter.encodeWithCharsetEncoder(CmBufferWriter.java:241)
        	at Altibase.jdbc.driver.cm.CmBufferWriter.prepareToWriteString(CmBufferWriter.java:79)
        	at Altibase.jdbc.driver.cm.CmOperation.writePrepare(CmOperation.java:396)
        	at Altibase.jdbc.driver.cm.CmProtocol.directExecuteAndFetch(CmProtocol.java:363)
        	at Altibase.jdbc.driver.AltibaseStatement.executeQuery(AltibaseStatement.java:723)

  - **예상 결과**

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
| 7.1.0.3.9        | 6.5.1                   | 8.7.1        | 7.1.7               | 7.4.5                        | 2.2.1            |

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

Replication 프로토콜 버전은 변경되지 않았다..

#### Sharding Version

샤딩 버전은 변경 되지 않았다.

> 알티베이스 샤딩 프로토콜 및 메타는 상위, 하위 호환성을 보장하지
> 않는다. 즉, 샤딩 버전이 다른 경우, 재구성해야 한다.

### 프로퍼티

추가/변경/삭제된 프로퍼티 없음

### 성능 뷰

추가/변경/삭제된 성능 뷰 없음