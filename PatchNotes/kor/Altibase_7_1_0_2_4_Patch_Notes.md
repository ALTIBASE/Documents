<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Altibase 7.1.0.2.4 Patch Notes](#altibase-71024-patch-notes)
  - [New Features](#new-features)
    - [BUG-46892 Mathematics 사용 메모리 제한 기능과 Mathematics Temp 사용 모니터링 기능 추가](#bug-46892mathematics-%EC%82%AC%EC%9A%A9-%EB%A9%94%EB%AA%A8%EB%A6%AC-%EC%A0%9C%ED%95%9C-%EA%B8%B0%EB%8A%A5%EA%B3%BC-mathematics-temp-%EC%82%AC%EC%9A%A9-%EB%AA%A8%EB%8B%88%ED%84%B0%EB%A7%81-%EA%B8%B0%EB%8A%A5-%EC%B6%94%EA%B0%80)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-46940 이중화 start후 XLOG가 receiver로 전송하지 않는 문제가 있습니다.](#bug-46940%EC%9D%B4%EC%A4%91%ED%99%94-start%ED%9B%84-xlog%EA%B0%80-receiver%EB%A1%9C-%EC%A0%84%EC%86%A1%ED%95%98%EC%A7%80-%EC%95%8A%EB%8A%94-%EB%AC%B8%EC%A0%9C%EA%B0%80-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-46942 target에 NVL등의 함수를 alias로 선언하고 JOIN이 존재하며 order by에 해당 alias를 연산하는 경우 비정상 종료](#bug-46942target%EC%97%90-nvl%EB%93%B1%EC%9D%98-%ED%95%A8%EC%88%98%EB%A5%BC-alias%EB%A1%9C-%EC%84%A0%EC%96%B8%ED%95%98%EA%B3%A0-join%EC%9D%B4-%EC%A1%B4%EC%9E%AC%ED%95%98%EB%A9%B0-order-by%EC%97%90-%ED%95%B4%EB%8B%B9-alias%EB%A5%BC-%EC%97%B0%EC%82%B0%ED%95%98%EB%8A%94-%EA%B2%BD%EC%9A%B0-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C)
    - [BUG-46955 메모리 인덱스 POINTER BASE BOTTOM-UP 빌드 속도 향상](#bug-46955%EB%A9%94%EB%AA%A8%EB%A6%AC-%EC%9D%B8%EB%8D%B1%EC%8A%A4-pointer-base-bottom-up-%EB%B9%8C%EB%93%9C-%EC%86%8D%EB%8F%84-%ED%96%A5%EC%83%81)
    - [BUG-46977 Anonymous block의 select into 구문에서 ?로도 bind가 가능해야 합니다.](#bug-46977anonymous-block%EC%9D%98-select-into-%EA%B5%AC%EB%AC%B8%EC%97%90%EC%84%9C-%EB%A1%9C%EB%8F%84-bind%EA%B0%80-%EA%B0%80%EB%8A%A5%ED%95%B4%EC%95%BC-%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Altibase 7.1.0.2.4 Patch Notes
==============================

New Features
------------

### BUG-46892 Mathematics 사용 메모리 제한 기능과 Mathematics Temp 사용 모니터링 기능 추가

- **module** : mt-function

- **Category** : Memory Error

- **재현 빈도** : Always

- **증상** : Mathematics 사용 메모리 제한 기능과 Mathematics Temp 사용
  모니터링 기능을 추가합니다.

  Mathematics은 일반적인 연산 함수나 Listagg와 같은 분석 함수에서
  사용하는 메모리를 합해서 보여줍니다.

  특히 분석 함수는 데이터 분포에 따라 메모리를 많이 사용할 수
  있습니다.

  따라서 모니터링을 위해, v\$statement에 MATHEMATICS\_TEMP\_MEMORY
  정보를 추가하였습니다.

  또한 Mathematics Temp의 메모리 사용 제한을 위해서 프로퍼티를
  제공합니다. 

- **재현 방법**

  -   **재현 절차**

  -   **수행 결과**

  -   **예상 결과**

- **Workaround**

- **변경사항**

  - Performance view

    - V$STATEMENT

      컬럼 추가)

      **MATHEMATICS_TEMP_MEMORY** BIGINT

      분석함수에서 사용하는 MATHEMATICS TEMP 메모리 사용량를 보여준다.

  - Property
    -   추가
        -   MATHEMATICS\_TEMP\_MEMORY\_MAXIMUM 
            -   데이터타입: Unsigned Long
            -   기본값: 0
            -   속성: 변경가능, 단일 값
            -   값의 범위: [0, 2^64 -1]
            -   설명: 분석함수에서 사용하는MATHEMATICS TEMP 메모리 용량을 제어한다.

  - Compile Option

  - Error Code

Fixed Bugs
----------

### BUG-46940 이중화 start후 XLOG가 receiver로 전송하지 않는 문제가 있습니다.

- **module** : dm

- **Category** : Other

- **재현 빈도** : Always

- **증상** : 원인

  이중화 구성 후 sender가 receiver로 Xlog를 보내서 receiver에
  restartXSN 값이 증가된 상태에서

  Sender 쪽에 db를 재구성하게 되면 XSN값이 초기화되어 다시 처음부터
  시작 하게 됩니다.

  그러나 receiver 쪽에서는 이중화를 drop 시키지 않아 이전 Meta 정보를
  가지고 있어, 이전의 restartXSN값을 Sender로 보내게 되고

  Sender에서는 현재 XSN 값이 restartXSN보다 작으므로 이전에 보낸것으로
  판단하여 skip하게 되어 Xlog를 전송하지 않아 문제가 발생합니다.

  대책

  Sender 쪽에 이중화를 새로 생성하게 되면 Sender에서 flag를 전송하여
  receiver로 meta정보를 초기화 시키도록 하였습니다.

  그러면 receiver에서도 초기화된 restartXSN보다 값을 sender로 보내어
  Sender가 Xlog를 skip하지 않고 정상적으로 보내게 됩니다.

- **재현 방법**

  -   **재현 절차**

  -   **수행 결과**

  -   **예상 결과**

- **Workaround**

      한쪽은 db를 재구성시 양쪽의 이중화를 drop후 재생성 한다.

- **변경사항**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

### BUG-46942 target에 NVL등의 함수를 alias로 선언하고 JOIN이 존재하며 order by에 해당 alias를 연산하는 경우 비정상 종료

-   **module** : qp-dml-execute

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **증상** : target에 NVL등의 함수를 alias로 선언하고 JOIN이 존재하며
    order by에 해당 alias를 연산하는 경우 비정상 종료 수정

-   **재현 방법**

    -   **재현 절차**

            DROP TABLE T1;
            CREATE TABLE T1 (I1 INTEGER);
            INSERT INTO T1 VALUES (10);
            INSERT INTO T1 VALUES (20);
            SELECT /*+  no_plan_cache*/  NVL(B.BB ,0)  MM
            FROM ( select I1 AA
                   FROM T1
                   WHERE I1 = 10
                 ) A 
                 LEFT OUTER JOIN 
                 ( SELECT /*+ GROUP_SORT */ I1 BB                         
                   FROM T1
                 ) B ON A.AA = B.BB 
                 LEFT OUTER JOIN
                 ( SELECT /*+ GROUP_SORT */ I1 CC
                   FROM T1
                 ) C ON A.AA = C.CC
            ORDER BY MM - 1;
            [ERR-91015 : Communication failure.]

    -   **수행 결과**

    -   **예상 결과**

            DROP TABLE T1;
            CREATE TABLE T1 (I1 INTEGER);
            INSERT INTO T1 VALUES (10);
            SELECT /*+  no_plan_cache*/  NVL(B.BB ,0)  MM
            FROM ( select I1 AA
                   FROM T1
                   WHERE I1 = 10
                 ) A 
                 LEFT OUTER JOIN 
                 ( SELECT /*+ GROUP_SORT */ I1 BB                         
                   FROM T1
                 ) B ON A.AA = B.BB 
                 LEFT OUTER JOIN
                 ( SELECT /*+ GROUP_SORT */ I1 CC
                   FROM T1
                 ) C ON A.AA = C.CC
            ORDER BY MM - 1; 
            MM
            --------------
            10

- **Workaround**

  
      iSQL> SELECT /*+ ordered no_plan_cache*/  NVL(B.BB ,0)  MM
          2 FROM ( select I1 AA
          3        FROM T1
          4        WHERE I1 = 10
          5      ) A
          6      LEFT OUTER JOIN
          7      ( SELECT /*+ GROUP_SORT */ I1 BB
          8        FROM T1
          9      ) B ON A.AA = B.BB
          10      LEFT OUTER JOIN
          11      ( SELECT /*+ GROUP_SORT */ I1 CC
          12        FROM T1
          13      ) C ON A.AA = C.CC
          14 ORDER BY MM - 1;
      MM
      --------------
      10

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-46955 메모리 인덱스 POINTER BASE BOTTOM-UP 빌드 속도 향상

-   **module** : sm-mem-index

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **증상** : 메모리 인덱스의 POINTER BASE BOTTOM-UP 빌드 속도를 향상시켰습니다.

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

### BUG-46977 Anonymous block의 select into 구문에서 ?로도 bind가 가능해야 합니다.

-   **module** : qp-psm-trigger-pvo

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** :

- **재현 방법**

  - **재현 절차**

        BEGIN
          SELECT 1 INTO ? FROM DUAL;
        END;
        /

  - **수행 결과**

        $ java SimpleSQL
        ERROR CODE    : 200705
        ERROR MESSAGE : SQL syntax error
        
        line 1: parse error
        BEGIN SELECT 1 INTO ? FROM DUAL; END;
                            ^
        
        
        java.sql.SQLException: SQL syntax error
        
        line 1: parse error
        BEGIN SELECT 1 INTO? FROM DUAL; END;
                           ^
        
        
                at Altibase.jdbc.driver.ex.Error.processServerError(Error.java:369)
                at Altibase.jdbc.driver.AltibasePreparedStatement.(AltibasePreparedStatement.java:125)
                at Altibase.jdbc.driver.AltibaseCallableStatement.(AltibaseCallableStatement.java:46)
                at Altibase.jdbc.driver.AltibaseConnection.prepareCall(AltibaseConnection.java:1183)
                at SimpleSQL.main(SimpleSQL.java:45)

  -   **예상 결과**

          $ java SimpleSQL1

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
| 7.1.0.2.4        | 6.5.1                   | 8.7.1        | 7.1.7               | 7.4.5                        | 2.2.1            |

> Altibase 7.1 패치 버전별 히스토리는
> [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7_1_Version_Histories.md)
> 에서 확인할 수 있다.

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

통신 프로토콜 버전이 7.1.6에서 7.1.7로 변경되었지만, 하위 호환성을 보장한다.

#### Replication protocol Version

이중화 프로토콜 버전이 7.4.4에서 7.4.5로 변경되었지만, 하위 호환성을 보장한다.

#### Sharding Version

샤딩 버전은 변경 되지 않았다.

> 알티베이스 샤딩 프로토콜 및 메타는 상위, 하위 호환성을 보장하지
> 않는다. 즉, 샤딩 버전이 다른 경우, 재구성해야 한다.

### 프로퍼티

#### 추가된 프로퍼티

* MATHEMATICS\_TEMP\_MEMORY\_MAXIMUM

### 성능 뷰

#### 변경된 성능 뷰

* V$STATEMENT