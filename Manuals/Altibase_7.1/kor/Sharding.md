<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Altibase Sharding Guide](#altibase-sharding-guide)
  - [서문](#%EC%84%9C%EB%AC%B8)
    - [이 매뉴얼에 대하여](#%EC%9D%B4-%EB%A7%A4%EB%89%B4%EC%96%BC%EC%97%90-%EB%8C%80%ED%95%98%EC%97%AC)
  - [1.Altibase Sharding 소개](#1altibase-sharding-%EC%86%8C%EA%B0%9C)
    - [샤딩 개요](#%EC%83%A4%EB%94%A9-%EA%B0%9C%EC%9A%94)
    - [용어](#%EC%9A%A9%EC%96%B4)
    - [Altibase Sharding 개요](#altibase-sharding-%EA%B0%9C%EC%9A%94)
    - [Altibase Sharding 구성](#altibase-sharding-%EA%B5%AC%EC%84%B1)
    - [Altibase Sharding 특징](#altibase-sharding-%ED%8A%B9%EC%A7%95)
  - [2.Altibase Sharding 설치와 설정](#2altibase-sharding-%EC%84%A4%EC%B9%98%EC%99%80-%EC%84%A4%EC%A0%95)
    - [Altibase Sharding 설치](#altibase-sharding-%EC%84%A4%EC%B9%98)
    - [Altibase Sharding 설정](#altibase-sharding-%EC%84%A4%EC%A0%95)
    - [샤드 메타](#%EC%83%A4%EB%93%9C-%EB%A9%94%ED%83%80)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
  - [3.Altibase Sharding 딕셔너리](#3altibase-sharding-%EB%94%95%EC%85%94%EB%84%88%EB%A6%AC)
    - [SYS_SHARD.VERSION\_](#sys_shardversion_)
    - [SYS_SHARD.NODES\_](#sys_shardnodes_)
    - [SYS_SHARD.OBJECTS\_](#sys_shardobjects_)
    - [SYS_SHARD.RANGES\_](#sys_shardranges_)
    - [SYS_SHARD.CLONES\_](#sys_shardclones_)
    - [SYS_SHARD.SOLOS\_](#sys_shardsolos_)
    - [V\$SHARD_CONNECTION_INFO](#vshard_connection_info)
  - [4.Altibase Sharding 사용방법](#4altibase-sharding-%EC%82%AC%EC%9A%A9%EB%B0%A9%EB%B2%95)
    - [Altibase Sharding 제약사항](#altibase-sharding-%EC%A0%9C%EC%95%BD%EC%82%AC%ED%95%AD)
    - [데이터 노드](#%EB%8D%B0%EC%9D%B4%ED%84%B0-%EB%85%B8%EB%93%9C)
    - [샤드 객체](#%EC%83%A4%EB%93%9C-%EA%B0%9D%EC%B2%B4)
    - [분산 정보 설정](#%EB%B6%84%EC%82%B0-%EC%A0%95%EB%B3%B4-%EC%84%A4%EC%A0%95)
    - [샤드 키](#%EC%83%A4%EB%93%9C-%ED%82%A4)
    - [샤드 트랜잭션](#%EC%83%A4%EB%93%9C-%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98)
    - [샤드 쿼리](#%EC%83%A4%EB%93%9C-%EC%BF%BC%EB%A6%AC)
    - [샤드 키워드](#%EC%83%A4%EB%93%9C-%ED%82%A4%EC%9B%8C%EB%93%9C)
    - [샤드 함수](#%EC%83%A4%EB%93%9C-%ED%95%A8%EC%88%98)
    - [샤드 실행계획](#%EC%83%A4%EB%93%9C-%EC%8B%A4%ED%96%89%EA%B3%84%ED%9A%8D)
    - [쿼리 튜닝](#%EC%BF%BC%EB%A6%AC-%ED%8A%9C%EB%8B%9D)
    - [모니터링](#%EB%AA%A8%EB%8B%88%ED%84%B0%EB%A7%81)
    - [자동 데이터 재구축](#%EC%9E%90%EB%8F%99-%EB%8D%B0%EC%9D%B4%ED%84%B0-%EC%9E%AC%EA%B5%AC%EC%B6%95)
  - [5.Altibase Sharding 패키지](#5altibase-sharding-%ED%8C%A8%ED%82%A4%EC%A7%80)
    - [DBMS_SHARD](#dbms_shard)
  - [6.Altibase Sharding 유틸리티](#6altibase-sharding-%EC%9C%A0%ED%8B%B8%EB%A6%AC%ED%8B%B0)
    - [shardLoader](#shardloader)
    - [Shard Manager](#shard-manager)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Altibase® Administration

Altibase Sharding Guide
=======================

![](media/Sharding/e5cfb3761673686d093a3b00c062fe7a.png)

Altibase Administration Altibase Sharding Guide

Release 7.1

Copyright ⓒ 2001\~2018 Altibase Corp. All Rights Reserved.

본 문서의 저작권은 ㈜알티베이스에 있습니다. 이 문서에 대하여 당사의 동의
없이 무단으로 복제 또는 전용할 수 없습니다.

**㈜알티베이스**

08378 서울시 구로구 디지털로 306 대륭포스트타워Ⅱ 10층

전화: 02-2082-1114 팩스: 02-2082-1099

고객서비스포털: <http://support.altibase.com>

homepage: [http://www.altibase.com](http://www.altibase.com/)

서문
----

### 이 매뉴얼에 대하여

이 매뉴얼은 Altibase의 분산 데이터베이스 기술인 Altibase Sharding에 대해
설명한다.

#### 대상 사용자

이 매뉴얼은 다음과 같은 Altibase 사용자를 대상으로 작성되었다.

-   데이터베이스 관리자

-   응용프로그램 개발자

-   DB 설계자

다음과 같은 배경 지식을 가지고 이 매뉴얼을 읽는 것이 좋다.

-   컴퓨터, 운영 체제 및 운영 체제 유틸리티 운용에 필요한 기본 지식

-   관계형 데이터베이스 사용 경험 또는 데이터베이스 개념에 대한 이해

-   컴퓨터 프로그래밍 경험

-   데이터베이스 서버 관리, 운영 체제 관리 또는 네트워크 관리 경험

#### 소프트웨어 환경

이 매뉴얼은 데이터베이스 서버로 Altibase 7.1 또는 그 이상의 버전을 사용한다는
가정 하에 작성되었다.

#### 이 매뉴얼의 구성

이 매뉴얼은 다음과 같이 구성되어 있다.

-   제 1장 Altibase Sharding 소개  
    이 장은 샤딩의 일반적인 개념과 Altibase Shading을 설명한다.

-   제 2 장 Altibase Sharding 설치와 설정  
    이 장에서는 Altibase Sharding을 설정하는 방법을 설명한다.

-   제 3 장 Altibase Sharding 딕셔너리  
    이 장에서는 Altibase Sharding의 객체 및 시스템 정보를 제공하는 딕셔너리를
    설명한다.

-   제 4장 Altibase Sharding 사용 방법  
    이 장에서는 Altibase Sharding의 사용 방법을 설명한다.

-   제 5 장 Altibase Sharding 패키지  
    이 장에서는 Altibase Sharding 패키지를 구성하는 프로시저와 함수를 설명한다.

-   제 6장 Altibase Sharding 유틸리티  
    이 장에서는 Altibase Sharding에서 지원하는 유틸리티를 설명한다.

#### 문서화 규칙

이 절에서는 이 매뉴얼에서 사용하는 규칙에 대해 설명한다. 이 규칙을 이해하면 이
매뉴얼과 설명서 세트의 다른 매뉴얼에서 정보를 쉽게 찾을 수 있다.

여기서 설명하는 규칙은 다음과 같다.

-   구문 다이어그램

-   샘플 코드 규칙

##### 구문 다이어그램

이 매뉴얼에서는 다음 구성 요소로 구축된 다이어그램을 사용하여, 명령문의 구문을
설명한다.

| 구성 요소                        | 의미                                                         |
| -------------------------------- | ------------------------------------------------------------ |
| ![](media/Sharding/image004.gif) | 명령문이 시작한다. 완전한 명령문이 아닌 구문 요소는 화살표로 시작한다. |
| ![](media/Sharding/image006.gif) | 명령문이 다음 라인에 계속된다. 완전한 명령문이 아닌 구문 요소는 이 기호로 종료한다. |
| ![](media/Sharding/image008.gif) | 명령문이 이전 라인으로부터 계속된다. 완전한 명령문이 아닌 구문 요소는 이 기호로 시작한다. |
| ![](media/Sharding/image010.gif) | 명령문이 종료한다.                                           |
| ![](media/Sharding/image012.gif) | 필수 항목                                                    |
| ![](media/Sharding/image014.gif) | 선택적 항목                                                  |
| ![](media/Sharding/image016.gif) | 선택사항이 있는 필수 항목. 한 항목만 제공해야 한다.          |
| ![](media/Sharding/image018.gif) | 선택사항이 있는 선택적 항목.                                 |
| ![](media/Sharding/image020.gif) | 선택적 항목. 여러 항목이 허용된다. 각 반복 앞부분에 콤마가 와야 한다. |

##### 샘플 코드 규칙

코드 예제는 SQL, Stored Procedure, iSQL, 또는 다른 명령 라인 구문들을 예를 들어
설명한다.

아래 테이블은 코드 예제에서 사용된 인쇄 규칙에 대해 설명한다.

| 규칙         | 의미                                                         | 예제                                                         |
| ------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ ]          | 선택 항목을 표시                                             | VARCHAR [(*size*)][[FIXED \|] VARIABLE]                      |
| { }          | 필수 항목 표시. 반드시 하나 이상을 선택해야 되는 표시        | { ENABLE \| DISABLE \| COMPILE }                             |
| \|           | 선택 또는 필수 항목 표시의 인자 구분 표시                    | { ENABLE \| DISABLE \| COMPILE } [ ENABLE \| DISABLE \| COMPILE ] |
| . . .        | 그 이전 인자의 반복 표시 예제 코드들의 생략되는 것을 표시    | SQL\> SELECT ename FROM employee; <br/>ENAME<br/> ------------------------<br/> SWNO<br/> HJNO<br/> HSCHOI<br/> .<br/> .<br/> . <br/>20 rows selected. |
| 그 밖에 기호 | 위에서 보여진 기호 이 외에 기호들                            | EXEC :p1 := 1; acc NUMBER(11,2);                             |
| 기울임 꼴    | 구문 요소에서 사용자가 지정해야 하는 변수, 특수한 값을 제공해야만 하는 위치 | SELECT \* FROM *table_name*;<br/> CONNECT *userID*/*password*; |
| 소문자       | 사용자가 제공하는 프로그램의 요소들, 예를 들어 테이블 이름, 칼럼 이름, 파일 이름 등 | SELECT ename FROM employee;                                  |
| 대문자       | 시스템에서 제공하는 요소들 또는 구문에 나타나는 키워드       | DESC SYSTEM_.SYS_INDICES_;                                   |

#### 관련 자료

자세한 정보를 위하여 다음 문서 목록을 참조하기 바란다.

-   Administrator’s Manual

-   Replication Manual

-   CLI User's Manual

-   Utilities Manual

-   iLoader User's Manual

-   Error Message Reference

#### Altibase는 여러분의 의견을 환영합니다.

이 매뉴얼에 대한 여러분의 의견을 보내주시기 바랍니다. 사용자의 의견은 다음
버전의 매뉴얼을 작성하는데 많은 도움이 됩니다. 보내실 때에는 아래 내용과 함께
고객서비스포털( http://support.altibase.com/kr/ )로 보내주시기 바랍니다.

-   사용 중인 매뉴얼의 이름과 버전

-   매뉴얼에 대한 의견

-   사용자의 성함, 주소, 전화번호

이 외에도 Altibase 기술지원 설명서의 오류와 누락된 부분 및 기타 기술적인
문제들에 대해서 이 주소로 보내주시면 정성껏 처리하겠습니다. 또한, 기술적인
부분과 관련하여 즉각적인 도움이 필요한 경우에도 고객서비스포털을 통해 서비스를
요청하시기 바랍니다.

여러분의 의견에 항상 감사 드립니다.

1.Altibase Sharding 소개
----------------------

이 장은 Altibase Sharding의 개념과 특징에 대하여 설명한다.

### 샤딩 개요

#### 샤딩 개념 및 모델

샤딩(Sharding)은 한 대의 데이터베이스에 저장했던 데이터를 여러 대의
데이터베이스에 분산하여 저장 및 처리하는 스케일 아웃 기술이다.

![](media/Sharding/1cd95d21b81794ed43c6eafff01f8e7c.png)

[그림 1‑1] sharding 개념

샤딩의 유형은 일반적으로 코디네이터를 이용하여 데이터를 분산하여 처리하는 서버측
샤딩(server-side sharding)과 응용프로그램에서 데이터를 분산하여 처리하는
클라이언트측 샤딩(client-side sharding) 방식이 있다. 그리고 이 두 가지 방식을
모두 수용하는 하이브리드 샤딩(hybrid sharding) 방식도 가능하다.

-   서버측 샤딩(Server-side Sharding)

-   클라이언트측 샤딩(Client-side Sharding)

-   하이브리드 샤딩(hybrid sharding)

#### 서버측 샤딩(Server-side Sharding)

![](media/Sharding/39b805a11697d8b7669b42bb61efc037.png)

[그림 1‑2] 서버측 샤딩

서버측 샤딩은 응용프로그램들과 호환하기 위하여 분할된 데이터베이스를 통합하는
코디네이터(coordinator)가 필요하다. 코디네이터는 응용프로그램에서 요청 받은
질의처리에 필요한 데이터의 위치를 파악하고, 해당하는 데이터베이스들에 질의를
분산 처리하여 그 결과를 통합하여 반환한다.

이러한 구조는 응용프로그램의 수정이 적고, 데이터의 통합이 필요한 경우
코디네이터를 이용하여 질의를 수행할 수 있는 장점이 있지만, 코디네이터에 부하가
집중되어 확장이 어려운 단점이 있다.

#### 클라이언트측 샤딩(Client-side Sharding)

![](media/Sharding/c692bfbc33bf556ad6ed199b492dffd1.png)

[그림 1‑3] 클라이언트측 샤딩

클라이언트측 샤딩은 응용프로그램에서 데이터가 위치한 데이터베이스를 미리 알고,
직접 데이터베이스에 접속하는 구조이다.

데이터의 통합이 필요한 경우 응용프로그램에서 데이터를 통합해야 하므로
응용프로그램을 작성하는 것이 어렵지만, 확장성이 좋고, 데이터베이스에 직접
접속하므로 성능이 하락하지 않는다.

#### 하이브리드 샤딩(Hybrid Sharding)

하이브리드 샤딩은 클라이언트측 샤딩과 서버측 샤딩을 동시에 사용할 수 있는 샤딩
방식이다.

애플리케이션은 데이터의 통합이 필요한 경우 서버측 샤딩을 선택하거나, 확장과
성능이 필요한 경우 클라이언트측 샤딩을 선택하여 각 샤딩의 장점을 취하고 단점을
보완할 수 있다.

![](media/Sharding/944963501cb5f8370b7dfe663bec7608.jpg)

[그림 1‑4] 하이브리드 샤딩

### 용어

##### 데이터 노드(data node) 

데이터가 분할 저장된 데이터베이스이다. 최대 128개의 데이터 노드를 지원한다.

##### 메타 노드(meta node) 

데이터 노드와 샤드 객체 등 샤딩 관련 메타 정보를 저장하고, 사용자 쿼리를
분석하며 코디네이터의 기능을 수행하는 데이터베이스이다.

##### 메타 커넥션(meta connection)

서버측 샤딩으로 쿼리를 수행하기 위하여, 메타 노드에서 데이터 노드들에 커넥션을
생성하는 것을 메타 커넥션이라고 한다. 메타 커넥션은 세션 별로 생성되며 세션이
종료될 때 함께 종료된다.

##### 분산 방식(split method)

샤드 키의 값을 기준으로 데이터를 분산하는 방법이다. 다양한 데이터에 대하여
적용할 수 있는 다양한 분산 방식을 제공한다. 현재 지원하는 분산 방식은 다음과
같다.

-   HASH

-   RANGE

-   LIST

-   COMPOSITE

-   CLONE

-   SOLO

##### 샤드 객체(shard object)

분산 저장 및 처리되는 객체를 지칭한다. 현재 지원하는 분산객체는 다음과 같다.

-   Table

-   Procedure

##### 샤드 라이브러리(shard library)

하이브리드 샤딩을 지원하는 응용프로그램 라이브러리이다.

##### 샤드 메타(shard meta)

데이터 노드의 정보, 샤드 객체, 분산 설정 등 샤드 관련 정보가 저장되는 메타
테이블들을 총칭하여 샤드 메타라고 한다. 샤드 메타 테이블들은 sys_shard 사용자로
관리한다.

##### 샤드 커넥션(shard connection)

샤드 커넥션은 샤드 라이브러리를 사용한 응용프로그램이 연결한 메타 노드 및 데이터
노드들의 커넥션을 말한다.

##### 샤드 코디네이터(shard coordinator)

분산된 데이터베이스를 통합하여 질의를 최적화하고 수행하는 분산 질의 처리기이다.

##### 샤드 쿼리(shard query)

샤딩으로 분산된 데이터베이스에서 쿼리는 샤드 쿼리와 논샤드 쿼리로 분류한다.

샤드 쿼리는 분산된 테이블의 레코드를 쿼리 수행하여도 결과가 논리적으로 동일한
테이블의 레코드를 처리한 것과 동일하다. 논샤드 쿼리는 샤드 쿼리가 아닌 모든
쿼리를 지칭한다.

클라이언트측 샤딩으로 수행할 경우, 스케일 아웃이 가능하다. 샤딩으로
데이터베이스를 분산하면, 샤드 쿼리를 사용하는 것이 좋다.

![](media/Sharding/098aaf2d253164bcb0ac978ebf2d9574.jpg)

[그림 1‑5] 샤드 쿼리

![](media/Sharding/870bab9bec65fd621cc694638fe47c9f.jpg)

[그림 1‑6] 논샤드 쿼리

샤드 쿼리의 몇 가지 예를 보면 다음과 같다.

```
SELECT * FROM s1 WHERE k1=1;
SELECT * FROM s1;
UPDATE s1 SET i2=1 WHERE k1=1;
DELETE FROM s1 WHERE k1>3;
```

샤드 쿼리가 아닌 몇 가지 예를 보면 다음과 같다.

```
SELECT count(*) FROM s1;
SELECT k1, count(*) FROM s1 group by k1;
SELECT * FROM s1 order by k1;
```

Altibase Sharding은 스케일아웃을 위하여 가능한 한 샤드 쿼리를 샤드 라이브러리를
사용하여 하이브리드 샤딩(클라이언트측 샤딩)으로 수행하는 것을 권장한다.

논샤드 쿼리는 서버측 샤딩으로 수행되어 샤드 코디네이터의 단일 병목 부하를
발생시키므로, 코디네이터의 부하를 감소시키기 위해 논샤드 쿼리를 튜닝하는 것이
좋다.

##### 샤드 뷰(shard view)

Altibase Sharding은 샤드 뷰를 제공한다. 쿼리가 논샤드 쿼리인 경우, 앞에 "SHARD"
키워드를 추가하면 데이터 노드에 논샤드 쿼리를 전송할 수 있다.

샤드 뷰를 사용하면 샤드 코디네이터의 부하를 줄이거나, 사용자가 의도하여 분산
쿼리를 수행할 수 있다.

샤드 코디네이터의 부하를 줄이는 예는 다음과 같다.

```
SELECT sum(k1) FROM s1;
```

위 쿼리를 각 데이터 노드에서 부분 합을 얻고 코디네이터에서 취합하도록 다음과
같이 수정할 수 있다. 가능한 한 코디네이터의 부하를 데이터 노드로 분산하는 것이
스케일아웃 측면에서 더 유리하다.

```
SELECT sum(s) FROM SHARD(SELECT sum(k1) s FROM s1);
```

또한 아래와 같이 샤드 뷰를 이용하여 테이블의 레코드 수를 데이터 노드별로 얻는
쿼리 작성도 가능하다.

```
SELECT * FROM shard(SELECT shard_node_name(), count(*) FROM s1); 
```

##### 샤드 쿼리 분석기(shard query analyzer)

사용자의 쿼리가 샤드 쿼리인지 논샤드 쿼리인지 분석한다. 샤드 쿼리인 경우 샤드
코디네이터 없이 클라이언트측 샤딩에서 독립적으로 수행할 수 있도록 분석 결과를
생성한다.

샤드 분석결과는 쿼리 수행 시마다 재사용되어, 메타 노드에서 샤드 쿼리 분석으로
생기는 부하는 크지 않다.

##### 샤드 쿼리 최적화기(shard query optimizer)

사용자의 쿼리가 논샤드 쿼리이면 쿼리를 분석하여 데이터 노드에 수행할 부분과 샤드
코디네이터에서 수행할 부분으로 분리하고, 최적화하여 분산 플랜을 생성한다.

##### 샤드 키(shard key)

분산 정의의 기준이 되는 컬럼 또는 파라미터이다. 현재 샤드 키로 사용할 수 있는
데이터 타입은 다음과 같다.

-   smallint

-   integer

-   bigint

-   char

-   varchar

##### 샤드 키워드(shard keyword)

Altibase Sharding에서 지원하는 키워드로 논샤드 쿼리를 샤드 쿼리로 수행하게
하거나, 임의의 데이터 노드로 쿼리를 수행하게 할 수 있다. 샤드 키워드의 종류는
다음과 같다.

-   SHARD

-   NODE

샤드 지원 구문(SELECT, INSERT, UPDATE, DELETE)의 앞이나 SELECT문의 샤드 뷰 앞에
사용하면 해당 쿼리를 샤드 쿼리로 수행하여 결과를 반환한다.

```
SHARD SELECT shard_node_name(),count(*) FROM s1;
NODE[DATA] SELECT shard_node_name(),count(*) FROM v$session;
NODE[DATA(‘node1’)] DELETE FROM s1;
```

##### 샤드 테이블(shard table)

레코드들이 분산 정의된 테이블이다. 지정된 컬럼의 값을 기준으로 분산 저장된다.
lob 컬럼은 지원하지 않는다.

##### 샤드 프로시저(shard procedure)

분산 정의된 프로시저, 지정된 인자의 값을 기준으로 분산 수행된다. 프로시저 내의
쿼리에 대해서는 사용자가 분산 처리하도록 작성해야 한다.

##### 샤드 플랜(shard plan)

질의가 샤드 코디네이터에서 분산 수행되는 경우의 질의 수행계획을 말한다. 샤드
플랜에는 데이터 노드에서 분산 수행된 질의의 수행계획을 포함한다.

##### 샤드 트랜잭션(shard transaction)

애플리케이션이 생성한 트랜잭션에서 수행하는 질의의 따라 데이터 노드들에 분산
트랜잭션을 생성하게 된다. 이 트랜잭션들을 샤드 트랜잭션이라고 한다. 샤드
트랜잭션은 다음과 같이 분류할 수 있다.

-   단일 노드 트랜잭션(single node transaction)  
    하나의 데이터 노드 트랜잭션만 허용하며, 샤드 데이터 정합성을 보장한다.

-   다중 노드 트랜잭션(multiple node transaction)  
    분산 트랜잭션을 허용하지만, 샤드 트랜잭션의 일관성을 보장하지 않는다.

-   글로벌 트랜잭션(global transaction)  
    분산 트랜잭션을 허용하고, 샤드 트랜잭션의 일관성을 보장한다.

### Altibase Sharding 개요

#### Altibase Sharding 소개

Altibase Sharding은 Altibase에 샤딩 기술을 도입하여 저장 용량과 시간당 처리량을
향상시키고 대용량의 데이터베이스를 분산처리할 수 있게 한다.

Altibase Sharding은 하이브리드 샤딩으로써, 기존의 SQL을 분석하여 자동으로
클라이언트측 샤딩이나 서버측 샤딩으로 수행할 것인지를 분석하여 경로를
최적화한다.

Altibase Sharding은 다양한 분산 방식과 분산 객체, 유틸리티를 지원하고 있으며,
다양한 업무에서 샤딩을 적용할 수 있다.

기존의 SQL을 수정하지 않고, 샤드 전용 라이브러리만 교체하는 것으로 Altibase
Sharding을 쉽게 적용할 수 있다. 뿐만 아니라 기존 응용프로그램을 전혀 수정하지
않은 상태에서도 서버측 샤딩을 적용할 수 있다.

![](media/Sharding/7a0b84f2b574c527d591932fc02da11f.jpg)

[그림 1‑7] Altibase Sharding의 하이브리드 샤딩

#### Altibase Sharding 장점

Altibase Sharding은 일반적인 샤딩의 장점 외에도 추가적인 장점을 가지고 있다.

##### 선형 확장성

Altibase Sharding은 Altibase에 샤딩 기술을 도입하여 성능 병목을 제거하고 데이터
노드를 추가하여 저장 용량과 시간당 처리량을 선형적으로 향상시켜 대용량의
데이터를 분산 처리할 수 있다.

##### 오류 독립성

Altibase Sharding을 통해 사용자는 하나의 데이터베이스를 논리적으로 나누어 관리할
수 있다. 하나의 데이터 노드가 비정상적이거나 속도가 느려지더라도 다른
데이터노드의 성능이나 가용성에는 영향을 미치지 않는다.

##### 애플리케이션 호환성

Altibase Sharding은 서버측 샤딩과 클라이언트측 샤딩을 동시에 지원하는 하이브리드
샤딩을 지원한다. 사용자 쿼리의 쿼리 최적화를 통해, 자동으로 성능에 유리한
클라이언트측 샤딩으로 수행되거나 호환성이 높은 서버측 샤딩으로 수행된다.

특히, Altibase Sharding의 하이브리드 샤딩은 기존 응용프로그램 소스나 기존 SQL을
수정하지 않고, 샤드 전용 라이브러리만 교체하는 것으로 적용할 수 있다.

##### 사용자 정의 데이터 분산

Altibase Sharding을 통해 사용자는 데이터베이스의 데이터를 원하는 형태로 분산할
수 있도록 정의할 수 있다.

예를 들면, 특정 관할 구역에 대한 데이터를 사용자가 원하는 데이터 노드에 위치시킬
수 있기 때문에, 논리적으로 특정 구역에 대한 데이터를 모을 수 있다.

또한 지역적으로 가까운 데이터들을 물리적으로 가까운 데이터 노드에 위치시킬 수
있기 때문에, 물리적으로 특정 관할 구역에 가까운 데이터를 모아둘 수도 있다.

##### 이중화를 통한 고가용성 

Altibase Sharding은 이중화를 지원한다. 메타 노드와 데이터 노드를 모두 이중화할
수 있다. 이중화를 이용하여 샤딩환경에서도 안전한 HA(High Availability)를 구축할
수 있다.

### Altibase Sharding 구성 

Altibase Sharding은 다음 요소로 구성되어 있다.

-   응용프로그램 (샤드 라이브러리)

-   메타 노드

-   데이터 노드

응용프로그램은 샤드 라이브러리를 사용하여 클라이언트측 샤딩과 서버측 샤딩을
사용할 수 있으며, 그 외의 라이브러리를 사용하는 경우 서버측 샤딩만을 사용할 수
있다.

메타 노드는 샤드 메타를 저장하며 샤드 쿼리를 분석하고, 서버측 샤딩의 코디네이터
역할을 수행한다.

데이터 노드는 실제 데이터가 분산 저장되어 있는 데이터베이스이다.

#### 독립 구성

독립 구성은 메타 노드를 별도로 구성하므로 샤드 메타의 관리가 용이하고, 샤드
분석의 부하를 데이터 노드에 주지 않는 장점이 있다. 그러나 메타 노드용으로 더
많은 데이터베이스가 필요한 단점이 있다.

메타 노드와 데이터 노드를 별도의 데이터베이스로 분리하여 구성하면서 각각의
데이터베이스를 이중화하여 다음과 같이 구성할 수 있다.

![](media/Sharding/c4a06a357752b5edce05ce065f3937ee.png)

[그림 1‑8] Altibase Sharding 독립 구성

#### 통합 구성

통합 구성은 메타 노드를 데이터 노드와 함께 구성하므로 메타 노드를 위한 별도의
데이터베이스가 필요 없다. 그러나 샤드 메타를 관리자가 직접 복제해야 하고, 데이터
노드에 샤드 분석의 부하가 생기는 단점이 있다.

메타 노드와 데이터 노드는 하나의 데이터베이스에서 동시에 동작할 수 있기 때문에
다음과 같이 통합 구성도 가능하다.

![](media/Sharding/0927525e47fd4d983e50c28765538f99.png)

[그림 1‑9] Altibase Sharding 통합 구성

### Altibase Sharding 특징

Altibase Sharding은 인메모리 하이브리드 샤딩이다. 인메모리 데이터베이스인
Altibase DBMS를 기반으로 데이터를 분산 저장하며, 클라이언트측 샤딩과 서버측
샤딩을 동시에 지원한다.

#### 지능적인 클라이언트측 샤딩

일반적으로 샤딩은 서버측 샤딩을 주로 제공하면서, 부분적으로 클라이언트측 샤딩을
지원한다. 그러나 알티베이스의 샤딩은 클라이언트측 샤딩을 서버측 샤딩과 동일하게
제공한다.

일반적인 클라이언트측 샤딩의 특징은 다음과 같다.

-   커넥션 시점 샤딩  
    응용프로그램에서 특정 데이터 노드를 지정하여 접속하는 방식이다. 다른 데이터
    노드에 접근하기 위해서는 재접속을 해야 한다.

-   SQL생성 시점 샤딩  
    응용프로그램에서 쿼리를 생성할 때 수행할 데이터 노드를 지정하는 방식이다.
    다른 데이터 노드에 접근하기 위해서는 쿼리를 재생성해야 한다.

Altibase Sharding의 클라이언트측 샤딩의 특징은 다음과 같다.

-   SQL수행 시점 샤딩  
    서버측 샤딩과 동일하게, 응용프로그램에서 쿼리를 수행하는 시점에 자동으로
    수행할 데이터 노드가 선택된다. 사용자는 데이터 노드를 구분할 필요가 없다.

-   하이브리드 샤딩  
    쿼리에 따라 클라이언트측이나 서버측으로 수행경로를 변경하여 성능을 최대화한다.

#### 쉬운 SQL 작성

Altibase Sharding환경에서는 별도의 API나 SQL 힌트 등의 추가 인터페이스 없이
사용자의 질의(SQL)만으로 샤딩 기능을 사용할 수 있다. 또한 분산 테이블과 일반
테이블을 구분하지 않고 SQL을 작성하는 것만으로 샤딩을 사용할 수 있다.

특히, Altibase Sharding은 사용자가 하이브리드 샤딩을 고려하여 쿼리를 튜닝할 수
있도록 추가적인 샤드 키워드를 제공하여 쉽게 SQL을 작성할 수 있다.

#### 쉬운 샤드 설정

Altibase Sharding은 Altibase 패키지에 내장된 기본 기능이다. Altibase Sharding을
사용하려면, 이 기능을 활성화하고 샤드 설정만 추가하면 이미 사용중인
데이터베이스를 샤드 데이터베이스로 변경할 수 있다. 따라서 데이터베이스를
재생성할 필요가 없으며, 데이터 노드의 경우 아무런 설정없이 데이터 노드로 사용할
수 있다.

Altibase Sharding은 샤딩 시스템을 운영, 관리하는데 필요한 DBMS_SHARD 패키지를
제공한다. 이 패키지에서 제공하는 서브프로그램을 이용하여 샤드를 구성하고
관리하며, 데이터 노드에 직접 접속하지 않고도 데이터 노드들까지도 관리할 수 있는
기능을 제공한다.

#### 샤드 쿼리 분석기 (Shard Query Analyzer)

Altibase Sharding의 샤드 쿼리 분석기는 사용자의 질의를 분석하여 최적의 수행
경로와 수행 방법을 선택한다.

샤드 쿼리 분석기는 메타 노드에 입력되는 모든 쿼리를 분석하여 서버측 샤딩으로
수행하는 쿼리와 클라이언트측 샤딩으로 수행하는 쿼리로 구분한다.

클라이언트측 샤딩으로 수행하는 경우 샤딩의 확장성과 성능을 모두 극대화할 수
있으며, 서버측 샤딩으로 수행하는 경우 샤드 쿼리 최적화기가 가장 효율적인 분산
플랜을 생성한다.

#### 샤드 쿼리 최적화기 (Shard Query Optimizer)

샤드 쿼리 최적화기는 서버측 샤딩에 대한 최적의 분산 쿼리를 생성하고, 분산 쿼리에
대한 분산 플랜을 생성한다.

사용자 쿼리가 서버측 샤딩으로 수행되는 쿼리로 분류된 경우, 해당 쿼리를
서버측에서 수행하기 위해서 분산부와 통합부로 구분한다. 분산부는 데이터 노드에서
수행할 부분(분산) 쿼리이고, 통합부는 각 데이터 노드에서 수행한 결과를 모아서
수행할 나머지(통합) 쿼리이다.

가능한 많은 부분을 분산부로 처리하는 것이 성능을 극대화할 수 있기 때문에 샤드
쿼리 최적화기는 최대한 샤드 쿼리 변환(Shard Transformation)을 수행한다.

#### 샤드 쿼리 실행기 (Shard Query Executor)

Altibase Sharding의 샤드 쿼리 실행기는 클라이언트측 샤딩의 실행기와 서버측
샤딩의 실행기로 구분한다. 클라이언트측 샤딩의 실행기는 샤드 라이브러리에서
동작하며, 서버측 샤딩의 실행기는 메타 노드에서 샤드 코디네이터와 함께 동작한다.

##### OLTP 쿼리

클라이언트측 샤딩의 실행기는 응응프로그램의 클라이언트 라이브러리에서 동작한다.
사용자의 쿼리를 최초 prepare시 분석한 후 쿼리 execute 시에는 추가 분석없이
실행할 수 있으므로, 다음과 같은 OLTP (Online Transaction Processing) 업무 특성에
적합하다.

-   대용량 데이터베이스를 대상으로 하는 업무

-   매우 짧은 시간에 읽거나 조작하는 업무를 하나의 트랜잭션 단위로 수행하는 업무

-   읽거나 조작하는 데이터가 매우 적은 업무

-   매우 많은 사용자가 동시에 수행하는 업무

-   매우 짧은 시간에 높은 처리량이 요구되는 업무

##### OLAP 쿼리

서버측 샤딩의 실행기는 메타 노드에서 동작하고, 샤드 쿼리 분석기가 변환한 분산
쿼리와 통합 쿼리를 수행한다. 서버측 샤딩의 실행기는 분산 쿼리를 각 데이터
노드에서 동시에 병렬 수행하고 통합 쿼리를 수행하므로, 데이터 노드의 수에
비례하여 성능과 처리량을 늘어난다. 따라서 다음과 같은 OLAP (Online Analytical
Processing) 업무 특성에 적합하다.

-   동일한 데이터에 여러 기준을 적용하여 다차원 데이터 분석을 하는 업무

##### 샤드 트랜잭션

샤드 트랜잭션이란 클라이언트측 샤딩으로 생성된 트랜잭션과 서버측 샤딩으로 생성된
트랜잭션을 통합함으로써, 트랜잭션내의 쿼리를 클라이언트측인지 서버측 샤딩인지
구분하지 않고 수행하는 기능이다.

Altibase Sharding의 하이브리드 샤딩은 OLTP성 쿼리와 OLAP성 쿼리를 하나의
트랜잭션으로 지원하므로, 각 쿼리를 최적의 수행 경로로 수행한다.

![](media/Sharding/7efb8d872f52f863aef912658f4165f1.png)

[그림 1‑10] Shard Query Analyzer & Optimizer & Executor

위 그림은 하이브리드 샤딩으로 사용자의 쿼리가 수행되는 예를 보여준다. Q3-1와
Q3-2는 샤드 쿼리 분석기가 Q3에서 생성한 분산 쿼리와 통합 쿼리이다.

```
Q1) insert into t1(key, c1) values (1, 100);
Q2) update t1 set c1=c1+1 where key=2;
Q3) select sum(c) total_count from (select count(*) c from t1);
Q3-1) select count(*) c from t1;
Q3-2) select sum(c) total_count from temp;
```

#### 글로벌 트랜잭션

샤드 트랜잭션은 분산 트랜잭션의 일관성을 보장하기 위하여 2단계 커밋(2-Phase
Commit)을 이용한 글로벌 트랜잭션을 지원한다.

> ##### 주의 사항
>
> 복제(clone) 분할 방식을 사용하면 데이터가 서버에 중복하여 저장되기 때문에,
> 글로벌 트랜잭션을 이용하더라도 데이터의 일관성이 보장되지 않을 수 있다.

#### 다양한 샤드 쿼리와 함수 지원

Altibase Sharding은 아래의 쿼리를 지원한다.

-   INSERT

-   INSERT SELECT

-   UPDATE

-   DELETE

-   SELECT

    \- Join

    \- Outer Join

    \- Aggregate function

    \- Grouping

    \- Ordering

    \- Subquery

쿼리가 샤드 쿼리인지 논샤드 쿼리인지 여부는 샤드 플랜을 조회하여 확인할 수 있다.
논샤드 쿼리로 플랜이 조회되는 경우 샤드(SHARD) 키워드를 이용하여 좀 더 효율적인
쿼리로 튜닝할 수 있다. 뿐만 아니라 다음과 같은 샤드 지원 함수들을 제공한다.

-   SHARD_NODE_NAME

-   SHARD_KEY

#### 다양한 분산 객체

일반적인 샤딩은 샤드 테이블에 한해 물리적 데이터 분산만 적용하지만, Altibase
Sharding은 샤드 프로시저까지 분산하여 수행할 수 있다.

샤드 프로시저의 경우 인자를 샤드 키로 적용하여 논리적인 분산을 수행하는 방식으로
샤딩을 수행한다.

#### 다양한 분산 방식

Altibase Sharding은 아래와 같이 다양하게 데이터 분산 방식을 제공한다.

샤드 키는 테이블 종류(파티셔닝 테이블, 메모리 테이블, 디스크 테이블 등)와
상관없이 설정할 수 있으며 최대 두 개까지 샤드 키를 갖는 복합 키를 지원한다.

샤드 키 분산 방식은 아래와 같다.

-   해시(hash) 분산 방식

-   범위(range) 분산 방식

-   리스트(list) 분산 방식

-   복합(composite) 샤드 키 분산 방식

-   복제(clone) 분산 방식

-   독립(solo) 분산 방식

![](media/Sharding/636327fd7d5bf5268d74f89b0760cbe9.png)

[그림 1‑11] Altibase Sharding 분산 방식

##### 해시(Hash) 분산 방식

Altibase Sharding의 해시 분산은 샤드 키에 해당하는 값을 내장된 hash함수를
이용하여 분산하는 것을 말한다.

Altibase는 대부분의 데이터 타입에 최적화된 해시 함수를 제공한다. 해시 함수는
데이터를 균등하게 분산하는데 이용된다. Altibase Sharding은 해시 함수로부터 구한
해시 값에 나머지 연산을 수행한 값을 이용하여, 전체 데이터를 1000개의 그룹으로
나누어 관리한다. 각 그룹마다 데이터 노드를 지정하여 데이터를 임의로 분산시킬 수
있다.

-   hash_group[1] = { record(x) \| if (mod(hash(shard key value of x),1000)==0)
    };

-   hash_group[2] = { record(x) \| if (mod(hash(shard key value of x),1000)==1)
    };

-   …

-   hash_group[1000] = { record(x) \| if (mod(hash(shard key value of
    x),1000)==999) };

이렇게 구분된 1000개의 hash group을 사용자의 필요에 따라 분산 정의한다. 예를
들면 user\_ id를 기준으로 해시 분산 방식으로 설정하는 경우, user_id의 해시 값을
1000개의 그룹으로 나누어 다음과 같이 설정한다.

-   1\~300번 hash group – 데이터 노드1

-   301\~600번 hash group – 데이터 노드2

-   601\~1000번 hash group – 데이터 노드 3

데이터를 분산하기 전 다음과 같은 해시 분산 방식으로 데이터를 분산했을 때
데이터의 분포 상태를 예측할 수 있다.

```
iSQL> SELECT hash, count(*) FROM (SELECT mod(hash(user_id),1000)+1 hash FROM table) GROUP BY hash;
```

##### 범위(Range) 분산 방식

해시 분산 방식을 사용하면 데이터가 비교적 균등하게 분산되는 반면, 특정 데이터가
어느 데이터 노드에 위치하는지 알기 어려워진다..

범위 분산 방식은 샤드 키 값으로 해당 데이터가 어느 데이터 노드에 위치하는지
관리자가 쉽게 알 수 있어 유리하다. 또한 해시 분산 방식에 비해 비교적 데이터 노드
확장이 쉬운 장점이 있다. 다만, 데이터가 데이터 노드들에 고르게 분산될 수 있도록
범위를 지정하는 것이 좋다.

예를 들면 샤드키 user\_ id 로 범위 분산 방식을 적용하는 경우 다음과 같이
설정한다.

-   { record(x) \| (shard key value of x) \<= ‘9’ } -\> 데이터 노드 1

-   { record(x) \| ‘9’ \< (shard key value of x) \<= ‘M’ } -\> 데이터 노드 2

-   { record(x) \| ‘M’ \< (shard key value of x) \<= ‘Z’ } -\> 데이터 노드 3

범위 분산 방식 역시 데이터를 분산하기 전에 쿼리로 데이터의 분포를 예측할 수
있다.

```
iSQL> SELECT hash, count(*) FROM (SELECT mod(hash(user_id),1000)+1 hash FROM table) GROUP BY hash;
```

그러나 범위 분산 방식으로 데이터를 고르게 분산했더라도, 운영 중에 데이터가
변경됨으로써 불균형이 발생할 수 있기 때문에 지속적으로 데이터 분포의 모니터링이
필요하다.

##### 리스트(List) 분산 방식

리스트 분산은 샤드 키 값을 특정값과 일치하는지 확인하여 분산하는 방식이다. 범위
분산 방식보다 더 직관적이고 특정 샤드 키 값에 대하여 쿼리를 수행하는 경우에도
유리하다.

예를 들면 지역을 샤드 키로 설정하고 리스트 분산 방식으로 설정하면 다음과 같다.

-   { record(x) \| (shard key value of x) = ‘서울’ } -\> 데이터 노드1

-   { record(x) \| (shard key value of x) = ‘부산’ } -\> 데이터 노드 2

-   { record(x) \| (shard key value of x) = ‘대구’ } -\> 데이터 노드 3

이 경우 데이터를 지역별로 분산하여, 지역별 통계 쿼리 작성에 유리하다. 리스트
분산 방식도 범위 분산 방식처럼 데이터가 데이터 노드들에 고르게 분산될 수 있도록
지정하는 것이 좋다.

##### 복합(Composite) 샤드 키 분산 방식

복합 샤드 키 분산 방식은 두 개의 샤드 키를 적용한 분산 방식으로 각 샤드 키는
해시, 범위, 리스트 분산 방식 중 선택하여 적용한다.

예를 들면 지역명을 샤드 키(리스트 분산)로 적용하고 고객번호를 서브 샤드 키(해시
분산)로 적용하면 다음과 같다.

-   { record(x) \| (shard key value of x) = ‘서울’ and hash(sub-shard key value
    of x) \<= 500 } -\> 데이터 노드1

-   { record(x) \| (shard key value of x) = ‘서울’ and hash(sub-shard key value
    of x) \<= 1000 } -\> 데이터 노드 2

-   { record(x) \| (shard key value of x) = ‘강원’ and hash(sub-shard key value
    of x) \<= 1000 } -\> 데이터 노드 3

##### 복제(Clone) 분산 방식

샤딩 환경에서는 데이터가 분산 저장되기 때문에 여러 데이터 노드에서 수행되는
질의를 처리하기 어렵다. 이런 문제를 보완하기 위해 Altibase Sharding은 데이터
전체를 사용자가 지정한 여러 데이터 노드에 복제 저장하는 복제 분산 방식을
제공한다.

복제 분산 방식은 객체의 데이터를 분산하는 것이 아니라, 객체 자체를 중복 저장하는
방식이다. 복제 분산 방식을 적용한 샤드 테이블은 join, subquery등 샤드 쿼리의
제약이 거의 없이 사용할 수 있다.

복제 분산 방식은 샤드 키를 지정할 필요가 없고 사용자가 원하는 데이터 노드를
선택적으로 지정한다.

복제 분산이 적용된 샤드 객체에 대한 접근은 데이터 노드들 중에서 임의 선택하여
수행한다. 예를 들어 복제 분산이 적용된 샤드 테이블을 조회하는 경우, 복제
테이블이 저장된 데이터 노드들 중에서 트랜잭션에서 가장 먼저 접근한 데이터 노드를
우선하여 선택한다. 먼저 접근한 데이터 노드가 없는 경우에는, 노드를 임의로
선택하여 데이터를 조회한다.

##### 독립(Solo) 분산 방식

독립 분산은 샤드 키를 적용한 데이터 단위의 분산이 아닌 샤드 객체 단위의 분산
방식이다. 사용자가 지정한 하나의 노드에만 객체를 저장한다는 면에서 복제 분산
방식과 차이가 있다.

-   TABLE_1 –\> 데이터 노드 1

-   TABLE_2 –\> 데이터 노드 2

-   TABLE_3 –\> 데이터 노드 1

샤드 객체 전체를 하나의 데이터 노드에 위치시키기 때문에 샤드 키를 추가할 필요가
없고 샤드 객체 하나만을 대상으로 쿼리를 수행할 때 쿼리 제약이 없다.

#### 쉬운 마이그레이션

기존 데이터베이스를 샤드 데이터베이스로 마이그레이션하는 경우, shardLoader
유틸리티를 사용하여 쉽고 빠르게 마이그레이션할 수 있다. shardLoader는 샤드
데이터베이스 데이터 업로드 전용 유틸리티로 사용방법은 iLoader와 유사하다.

shardLoader는 클라이언트측 샤딩 기능을 이용한 데이터 업로드 유틸리티로 데이터
노드의 수가 많을수록 업로드 속도도 향상된다.

기존의 iLoader도 사용가능 하지만, iLoader는 서버측 샤딩으로 동작하므로
shardLoader를 사용하는 것 보다는 성능이 떨어진다.

#### 자동 데이터 재구축

샤딩 시스템을 운영하다보면, 데이터 노드의 불균형 상태가 발생할 수 있다.

-   특정 데이터 노드의 분산 데이터 집중

-   특정 데이터 노드의 읽기/쓰기 집중

-   특정 데이터 노드의 장애로 인한 교체

-   데이터 노드 증설

관리자는 이 때 데이터 분산 방법의 변경을 고려해야 한다. Altibase Sharding은
데이터 분산 방법이 변경될 경우 분산 정보와 데이터의 유효성을 확인하고 자동으로
데이터를 재구축 하기 위해서 다음과 같은 샤드 패키지를 제공한다.

-   DBMS_SHARD.CHECK_DATA

-   DBMS_SHARD.REBUILD\_ DATA

-   DBMS_SHARD.REBUILD_DATA_NODE

2.Altibase Sharding 설치와 설정
-----------------------------

이 장에서는 Altibase Sharding을 구성하고 사용환경을 설정하는 방법을 설명한다.

### Altibase Sharding 설치

Altibase Sharding은 별도의 설치가 필요없다.

Altibase 패키지 인스톨러를 이용하여 설치를 완료하였다면, 몇 가지 추가 설정만으로
Altibase Sharding을 사용할 수 있다. 추가 설정은 이 문서의 *'*'을 참조한다.

#### 운영체제

Altibase Sharding은 현재 아래의 운영체제에서만 지원한다.

| OS    | CPU                          | Version         | Bit (Server) | Bit (Client) |
|-------|------------------------------|-----------------|--------------|--------------|
| LINUX | x86-64 (GNU glibc 2.12 이상) | redhat 6.0 이상 | 64-bit       | 64-bit       |
| LINUX | PowerPC7 (BE)                | redhat 6.5 이상 | 64-bit       | 64-bit       |
| LINUX | PowerPC8 (LE)                | redhat 7.2 이상 | 64-bit       | 64-bit       |
| AIX   | PowerPC                      | 6.1 tl03 이상   | 64-bit       | 64-bit       |
| HP-UX | IA64                         | 11.31 이상      | 64-bit       | 64-bit       |

#### 데이터베이스 버전

-   Altibase : Altibase 7.1.0 이상

### Altibase Sharding 설정

Altibase Hybrid Sharding을 위해 서버와 클라이언트의 샤딩 관련 설정은 통일성있게
적용해야 한다.

-   서버 설정

-   메타 노드 설정

-   데이터 노드 설정

-   클라이언트 설정

-   서버측 샤딩 응용프로그램 설정

-   클라이언트측 샤딩 응용프로그램 설정

#### 서버 설정

##### 메타 노드 설정

기존의 설치된 Altibase를 Altibase Sharding의 메타 노드로 설정하기 위해서는 다음
과정이 필요하다.

-   프로퍼티 설정  
    SHARD_META_ENABLE

-   샤드 패키지 생성  
    DBMS_SHARD

###### 프로퍼티 설정 

SHARD_META_ENABLE 프로퍼티를 활성화한 후 서버를 재시작하면, 샤드 메타 노드의
기능이 활성화된다.

```
iSQL> SELECT name, value1 FROM v$property WHERE name = 'SHARD_META_ENABLE';
NAME   : SHARD_META_ENABLE
VALUE1 : 1
```

Altibase Sharding의 메타 노드 기능이 활성화되면, 샤드 패키지를 생성하거나 샤드
관련 내장 함수, 성능 뷰를 사용할 수 있다.

###### 샤드 패키지 생성

메타 노드 서버가 시작되면 샤드 패키지를 생성할 수 있다. 샤드 패키지는
\$ALTIBASE_HOME/packages에 있다. 샤드 패키지는 샤드 기능을 제어할 수 있는 사용자
인터페이스를 제공한다.

```
is –f $ALTIBASE_HOME/packages/dbms_shard.sql
is –f $ALTIBASE_HOME/packages/dbms_shard.plb
```

DBMS_SHARD 패키지의 함수 및 프로시저에 대한 자세한 설명은 이 문서의 *패키지*
설명을 참조한다.

##### 데이터 노드 설정

데이터 노드는 특별히 설정할 것이 없다.

필요에 따라 메타 노드와 데이터 노드를 하나의 데이터베이스에 설정하는 것도
가능하다.

#### 클라이언트 설정

##### 서버측 샤딩 응용프로그램 설정

응용프로그램은 최초 접속 시 데이터베이스 서버의 ip/port를 메타 노드의 ip/port로
바꾸어야 한다.

메타 노드를 이중화를 할 경우 connect시 AlternateServer를 추가 설정해야 한다.

##### 클라이언트측 샤딩 응용프로그램 설정

cli 응용프로그램 빌드 시 기존의 odbccli 라이브러리를shardcli 라이브러리로
바꾸어야 한다.

shardcli 라이브러리는 libshardcli.a와 libshardcli_sl.so 두 개의 파일을 지원한다.
응용프로그램은 최초 접속 데이터베이스 서버의 ip와 port를 메타 노드의 ip, port로
바꾸어야 한다.

APRE, ACI등 odbccli 기반의 응용프로그램에서도 odbccli를 shardcli 라이브러리로
교체하면 동일하게 적용 가능하다.

메타 노드를 이중화를 할 경우 접속 시 AlternateServer를 추가 설정해야 한다.

#### 메타 노드 다중화 설정

메타 노드의 다중화란 샤드 쿼리 분석에 필요한 샤드 메타의 다중화를 말한다.

샤드 메타만 있으면 어떠한 Altibase도 메타 노드가 될 수 있다.

샤드 메타의 개수는 제한이 없으며, 메타 노드가 실제 데이터를 갖고 있지 않으므로
메타 노드를 다른 노드로 쉽게 대체할 수 있다.

샤드 메타는 Altibase의 시스템 메타 테이블과 달리 일반 사용자의 일반 테이블들로
구성되어 있고 primary key가 있어 쉽게 복제가 가능하다.

메타 노드를 다중화하는 방법은 다음과 같다.

-   모든 메타 노드에 샤드 패키지를 이용하여 동일한 샤드 설정을 한다.

-   하나의 메타 노드에서 샤드 설정을 한 후, aexport & iloader를 이용하여
    sys_shard 사용자의 스키마를 복제한다.

-   메타 노드들을 이중화 구성하고, 하나의 메타 노드에서 샤드 설정을 한다.

```
iSQL> CREATE REPLICATION repl WITH ‘…’, 20300
FROM sys_shard.nodes_ TO sys_shard.nodes_,
FROM sys_shard.objects_ TO sys_shard.objects_,
FROM sys_shard.ranges_ TO sys_shard.ranges_,
FROM sys_shard.clones_ TO sys_shard.sys_clones_,
FROM sys_shard.solos_ TO sys_shard.sys_solos_;
```

### 샤드 메타

Altibase Sharding을 사용하기 위해서는 샤드 메타를 생성해야 한다. 메타 노드는
Altibase Sharding에 필요한 모든 메타 정보를 샤드 메타에 영구적으로 저장한다.

#### 샤드 메타(Shard meta) 생성

샤드 패키지인 DBMS_SHARD 패키지에는 샤드 메타를 생성하는 서브 프로그램이
포함되어 있다. 최초 한번만 수행하면 샤드 메타가 생성된다.

샤드 메타는 일반적인 SYSTEM\_ 사용자의 메타 테이블과는 달리 일반 테이블로
생성되어, SYS 사용자가 직접 샤드 메타를 수정하고 삭제할 수 있다. 그러나 가능한
한 사용자가 직접 수정하는 대신 DBMS_SHARD 패키지를 이용하는 것을 권고한다.

샤드 메타는 일반 사용자와 일반 테이블로 생성되기 때문에, aexport나 iloader를
이용하여 백업과 복구를 수행할 수 있다.

메타 노드를 이중화하는 경우, standby 서버로 사용되는 메타 노드에도 샤드 메타를
생성해야 하고, active 서버와 동일하게 샤드 메타 정보를 생성해야 한다. 샤드
메타가 일반 테이블이고 주요 키(primary key)를 갖고 있으므로 이중화로 샤드 메타
정보를 동기화할 수도 있다.

##### 구문

```
DBMS_SHARD.CREATE_META
```

##### 설명

샤드 메타는 sys 사용자로 생성해야 한다. 샤드 메타를 생성하는 내부 과정은 다음과
같이 처리한다.

sys_shard 사용자를 생성한다.

sys_shard.version\_ 테이블을 생성하고, 현재 shard version을 입력한다.

sys_shard.nodes\_ 테이블과 인덱스를 생성한다.  
sys_shard.objects\_ 테이블과 인덱스를 생성한다.  
sys_shard.ranges\_ 테이블과 인덱스를 생성한다.  
sys_shard. clones \_ 테이블과 인덱스를 생성한다.  
sys_shard.solos\_ 테이블과 인덱스를 생성한다.

##### 예제

\<질의\> 샤드 메타를 생성한다.

```
iSQL> EXEC DBMS_SHARD.CREATE_META();
```

### 프로퍼티

Altibase Sharding 프로퍼티를 설명한다.

#### SHARD_META_ENABLE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

Altibase Sharding의 메타 노드로 설정한다.

0: Disabled

1: Enabled

3.Altibase Sharding 딕셔너리
--------------------------

Altibase Sharding의 객체 및 시스템 정보를 제공하는 딕셔너리에 대해 설명한다.

### SYS_SHARD.VERSION\_

Altibase Sharding의 버전을 기록하는 메타 테이블이다.

| Column name | Type    | Description                   |
|-------------|---------|-------------------------------|
| MAJOR_VER   | INTEGER | Altibase Sharding 메이저 버전 |
| MINOR_VER   | INTEGER | Altibase Sharding 마이너 버전 |
| PATCH_VER   | INTEGER | Altibase sharding 패치 버전   |

#### 칼럼 정보

##### MAJOR_VER

메이저 버전을 나타낸다.

##### MINOR_VER

마이너 버전을 나타낸다.

##### PATCH_VER

패치 버전을 나타낸다.

### SYS_SHARD.NODES\_

Altibase Sharding의 데이터 노드 정보를 기록하는 메타 테이블이다.

| Column name       | Type        | Description                          |
|-------------------|-------------|--------------------------------------|
| NODE_ID           | INTEGER     | 데이터 노드 식별자                   |
| NODE_NAME         | VARCHAR(40) | 데이터 노드 이름                     |
| HOST_IP           | VARCHAR(64) | 데이터 노드 ip address               |
| PORT_NO           | INTEGER     | 데이터 노드 port 번호                |
| ALTERNATE_HOST_IP | VARCHAR(64) | 데이터 노드의 alternative ip address |
| ALTERNATE_PORT_NO | INTEGER     | 데이터 노드의 alternative port 번호  |

#### 칼럼 정보

##### NODE_ID

데이터 노드의 번호를 나타낸다.

##### NODE_NAME

데이터 노드의 이름을 나타내며 데이터 노드의 이름은 유일해야 한다.

##### HOST_IP

데이터 노드의 ip address를 나타낸다.

##### PORT_IP

데이터 노드의 port 번호를 나타낸다.

##### ALTERNATE_HOST_IP

데이터 노드의 alternate 서버 ip address를 나타낸다.

##### ALTERNATE_PORT_IP

데이터 노드의 alternate 서버 port 번호를 나타낸다.

### SYS_SHARD.OBJECTS\_

Altibase Sharding의 샤드 객체 정보를 기록하는 메타 테이블이다.

| Column name         | Type         | Description                                                                              |
|---------------------|--------------|------------------------------------------------------------------------------------------|
| SHARD_ID            | INTEGER      | 샤드 객체 식별자                                                                         |
| USER_NAME           | VARCHAR(128) | 샤드 객체 소유자                                                                         |
| OBJECT_NAME         | VARCHAR(128) | 샤드 객체 이름                                                                           |
| OBJECT_TYPE         | CHAR(1)      | 샤드 객체 종류 T : 테이블 P : 프로시저                                                   |
| SPLIT_METHOD        | CHAR(1)      | 분산 방식 H : 해시(hash) R : 범위(range) L : 리스트(list) C : 복제(clone) S : 독립(solo) |
| KEY_COLUMN_NAME     | VARCHAR(128) | 샤드 키 이름                                                                             |
| SUB_SPLIT_METHOD    | CHAR(1)      | 서브 샤드 키 분산 방식 H : 해시(hash) R : 범위(range) L : 리스트(list)                   |
| SUB_KEY_COLUMN_NAME | VARCHAR(128) | 서브 샤드 키 칼럼 이름                                                                   |
| DEFAULT_NODE_ID     | INTEGER      | 기본 데이터 노드 번호                                                                    |

#### 칼럼 정보

##### SHARD_ID

샤드 객체의 번호를 나타낸다.

##### USER_NAME

샤드 객체의 소유자 이름을 나타낸다.

##### OBJECT_NAME

샤드 객체 이름을 나타낸다.

##### OBJECT_TYPE

샤드 객체 종류를 나타낸다.

##### SPLIT_METHOD

샤드 객체 분산 방식을 나타낸다.

##### KEY_COLUMN_NAME

샤드 객체의 샤드 키 이름을 나타낸다.

##### SUB_SPLIT_METHOD

샤드 객체의 서브 샤드 키 분산 방식을 나타낸다.

##### SUB_KEY_COLUMN_NAME

샤드 객체의 서브 샤드 키 칼럼 이름을 나타낸다.

##### DEFAULT_NODE_ID

샤드 객체의 기본 데이터 노드를 나타낸다. 분산 설정이 완전하지 않을 경우 설정
기준 이외의 데이터가 저장되는 데이터 노드이다.

### SYS_SHARD.RANGES\_ 

샤드 객체(HASH, RANGE, LIST, COMPOSITE)의 분산 정보를 기록하는 메타 테이블이다.

| Column name | Type         | Description      |
|-------------|--------------|------------------|
| SHARD_ID    | INTEGER      | 샤드 객체 식별자 |
| VALUE       | VARCHAR(100) | 샤드 키 값       |
| SUB_VALUE   | VARCHAR(100) | 서브 샤드 키 값  |
| NODE_ID     | INTEGER      | 데이터 노드 번호 |

#### 칼럼 정보

##### SHARD_ID

샤드 객체의 번호를 나타낸다.

##### VALUE

샤드 키 값을 나타낸다.

##### SUB_VALUE

서브 샤드 키 값을 나타낸다.

##### NODE_ID

VALUE와 SUB_VALUE를 기준으로 저장되는 데이터의 노드 번호를 나타낸다.

### SYS_SHARD.CLONES\_

샤드 객체에 복제 분산 방식이 적용된 분산 정보를 기록하는 메타 테이블이다.

| Column name | Type    | Description      |
|-------------|---------|------------------|
| SHARD_ID    | INTEGER | 샤드 객체 식별자 |
| NODE_ID     | INTEGER | 데이터 노드 번호 |

#### 칼럼 정보

##### SHARD_ID

샤드 객체 번호를 나타낸다.

##### NODE_ID

데이터가 복제 저장되는 데이터 노드 번호를 나타낸다.

### SYS_SHARD.SOLOS\_

독립 분산 방식이 적용된 샤드 객체의 분산 정보를 기록하는 메타 테이블이다.

| Column name | Type    | Description      |
|-------------|---------|------------------|
| SHARD_ID    | INTEGER | 샤드 객체 식별자 |
| NODE_ID     | INTEGER | 데이터 노드 번호 |

#### 칼럼 정보

##### SHARD_ID

샤드 객체 번호를 나타낸다.

##### NODE_ID

데이터가 독립 저장되는 데이터 노드 번호를 나타낸다.

### <a name="vshard_connection_info"><a/>V\$SHARD_CONNECTION_INFO

샤드 코디네이터로써 현재 세션에서의 메타 노드와 데이터 노드의 연결 상태에 대한
정보를 보여주는 메타 테이블이다.

| Column name     | Type        | Description                                        |
|-----------------|-------------|----------------------------------------------------|
| NODE_ID         | INTEGER     | 데이터 노드 식별자                                 |
| NODE_NAME       | VARCHAR(40) | 데이터 노드 이름                                   |
| COMM_NAME       | VARCHAR(64) | 접속 정보                                          |
| AUTOCOMMIT_FLAG | INTEGER     | autocommit 플래그 0: non-autocommit 1: auto commit |
| TOUCH_COUNT     | INTEGER     | 현재 트랜잭션의 DML 발생 횟수                      |
| LINK_FAILURE    | INTEGER     | 데이터 노드의 연결 상태 0: 정상 1: 실패            |

#### 칼럼 정보

##### NODE_ID

데이터 노드의 고유 번호를 나타낸다.

##### NODE_NAME

데이터 노드의 이름을 나타낸다.

##### COMM_NAME

메타 노드와 데이터 노드간의 현재 접속 상태를 나타낸다.

##### AUTOCOMMIT_FLAG

메타 노드와 데이터 노드간의 연결된 세션에서 autocommit 여부를 나타낸다.

##### TOUCH_COUNT

메타 노드와 데이터 노드간의 연결된 세션 중 현재 트랜잭션에서 발생한 DML 횟수를
나타낸다.

##### LINK_FAILURE

조회 시점의 메타 노드와 데이터 노드간의 연결 상태를 나타낸다.

4.Altibase Sharding 사용방법
--------------------------

이 장에서는 Altibase Sharding 사용 방법을 자세히 설명한다. 앞에서 설명한 메타
노드 설정과 샤드 패키지 생성 과정 이후의 사용 방법을 기술한다.

### Altibase Sharding 제약사항

Altibase Sharding의 제약 조건을 설명한다. 이 조건을 만족하지 않을 경우 Altibase
Sharding을 사용할 수 없다.

#### 선행 조건

-   샤딩은 하나의 데이터베이스를 여러 데이터베이스로 나누어 저장하는 기술이다.
    따라서 각 데이터베이스는 서로 독립적으로 운영되고 관리되어야 한다.

-   샤딩의 HA(High Availability)를 구성하기 위해서는 메타 노드, 데이터 노드를
    모두 이중화해야 한다.

#### 데이터 제약조건

-   샤딩은 데이터가 분산 가능한 형태인 경우에 효과적이다. 사용자의 업무 형태,
    데이터 특성에 따라 샤딩의 적용 여부를 판단해야 한다.

-   데이터가 분산 가능하지 않거나 대부분의 질의가 샤드 쿼리가 아닌 경우, 샤딩을
    적용하더라도 여러 데이터베이스를 다루는 부하때문에 하나의 데이터베이스로
    운영하는 것에 비해 장점이 없다.

-   샤딩은 데이터가 분산 가능하고, 질의가 샤드 쿼리인 경우, 우수한 확장성을
    보장한다.

-   샤딩은 여러 데이터 노드에 데이터의 로드가 고르게 분산되어야 한다. 이를
    위하여 분산 방식과 샤드 키를 적절하게 선택해야 한다.

-   샤딩은 운영 중에 데이터가 고르게 분산되어 있는지 확인하고 필요한 경우에는
    데이터를 재분산해야한다.

#### 연결 제약조건

-   클라이언트와 서버 간에 연결관계가 복잡하다.

-   네트워크에서 발생할 수 있는 문제들이 샤딩 환경에서 확률적으로 더 많이 발생할
    수 있다.

#### 데이터 노드 장애

-   여러 개의 데이터 노드들 중에서 일부 데이터 노드에 네트워크나 서버 장애가
    발생하는 경우가 있다. 이것을 전체 데이터베이스 시스템의 장애로 볼 것인지,
    일부 데이터베이스 시스템의 장애로 볼 것인지는 응용프로그램마다 다를 수 있다.

-   Altibase Sharding은 응용프로그램에서 데이터베이스로 커넥션을 생성할 때, 일부
    데이터 노드에서 장애가 발생하면 이를 에러로 처리하고 커넥션 생성이 실패한다.

-   그러나 커넥션 생성 후, 사용자 쿼리가 prepare, bind, execute를 수행시에는
    일부 데이터 노드에 장애가 발생하더라도 장애가 발생하지 않는 데이터 노드로
    서비스를 계속 수행할 수 있다.

-   일부 데이터 노드의 장애에도 불구하고 나머지 데이터 노드에서 서비스를
    계속하기 위해서는 응용프로그램의 에러 처리 방식을 수정해야 한다.

-   즉, Altibase Sharding은 샤드 구성 전에 사용하던 기존의 응용프로그램을 그대로
    사용할 경우, 에러 처리는 일부 데이터 노드의 장애를 전체 데이터베이스의
    장애로 판단한다.

#### 하위 호환성

-   샤드 기능은 하위 호환성을 갖지 않는다. 다시말해 샤드 버전이 동일한 서버,
    클라이언트에 대해서만 샤드 기능을 사용할 수 있다.  
    샤드 버전은 다음과 같이 확인할 수 있다.

```
$ALTIBASE_HOME/bin/altibase -v
```

### 데이터 노드

Altibase Sharding을 사용하기 위하여 데이터 노드를 설정해야 한다. 운영중인 데이터
노드가 없더라도 데이터 노드의 설정은 가능하다.

#### 데이터 노드 추가

샤드 패키지인 DBMS_SHARD 패키지에는 데이터 노드를 추가하는 서브 프로그램을
제공한다. 데이터 노드를 추가하기 위해서는 샤드 패키지 생성해야 한다.

##### 구문

```
DBMS_SHARD.SET_NODE
```

##### 설명

데이터 노드를 추가한다. 필요에 따라 alternate 데이터 노드를 추가할 수 있다.
데이터 노드 이름의 대소문자는 구별하지 않는다.

현재 ip address는 ip v4형식만 지원한다.

##### 예제

```
iSQL> EXEC DBMS_SHARD.SET_NODE(‘node1’,‘192.168.1.10’,20300);
iSQL> EXEC DBMS_SHARD.SET_NODE(‘node2’,‘192.168.1.11’,20300, ‘192.168.1.101’,20300);
iSQL> SELECT * FROM sys_shard.nodes_;
```

> ##### 주의 사항
>
> 이미 운영중인 샤드 키 분산 테이블에서 신규 데이터 노드를 증설하고 추가적으로
> 분산 키를 신규 데이터 노드로 매핑할 경우, 현재 세션에서 신규 데이터 노드를
> 인식할 수 있도록 다음 과정을 수행해야 한다.
>
> ```
> iSQL> EXEC DBMS_SHARD.SET_NODE(‘node3’,‘192.168.1.12’,20300);
> iSQL> ALTER SESSION SET shard linker = on;
> ```
>

#### 샤드 링커 활성화

데이터 노드의 추가/변경/제거 이후에, 데이터 노드 연결 정보를 갱신하는 용도로
사용한다.

##### 구문

```
ALTER SESSION SET SHARD LINKER = ON
```

##### 설명

이전에 캐시에 등록된 실행계획을 사용하지 않으므로, 현재 세션에서 데이터 노드
연결 정보를 제거하고 다시 얻는다.

> ##### 주의사항
>
> 현재 세션에서 데이터 노드 연결 정보를 제거하므로, 데이터 노드에 수행한 작업이
> 있으면 미리 커밋 또는 롤백해야 한다.

#### 데이터 노드 삭제

샤드 패키지인 DBMS_SHARD 패키지에는 데이터 노드를 삭제하는 서브 프로그램을
제공한다.

##### 구문

```
DBMS_SHARD.UNSET_NODE
```

##### 설명

추가한 데이터 노드를 삭제한다.

##### 예제

```
iSQL> EXEC DBMS_SHARD.UNSET_NODE(‘node1’);
iSQL> SELECT * FROM sys_shard.nodes_;
```

### 샤드 객체 

Altibase Sharding은 현재 다음 두 가지 샤드 객체(shard object)를 지원한다. 샤드
객체란 일반 테이블 혹은 프로시저에 샤드 설정을 추가한 객체를 의미한다.

-   샤드 테이블

-   샤드 프로시저

샤드 객체에 샤드를 설정하기 위해서는 아래의 절차를 수행하여야 한다.

-   테이블에 샤드 키 컬럼 지정 또는 프로시저에 샤드 키 파라미터 지정

-   분산 방식 지정

-   분산 노드 지정

#### 샤드 테이블 설정

테이블을 샤드 테이블로 설정한다. 메타 노드에 미리 생성되어 있는 테이블에 샤드
설정을 추가한다.

샤드 설정 후, 샤드 쿼리를 수행하기 위하여 설정된 데이터 노드에 동일한 스키마의
테이블이 생성되어 있어야 한다. DBMS_SHARD 패키지는 샤드 테이블을 추가하는 서브
프로그램을 제공한다.

##### 구문

```
DBMS_SHARD.SET_SHARD_TABLE
DBMS_SHARD.SET_SHARD_TABLE_COMPOSITE
```

##### 설명

샤드 테이블을 설정한다. 샤드 테이블 설정 구문에 대한 자세한 설명은 DBMS_SHARD
패키지의 또는 99 을 참조한다.

##### 예제

```
iSQL> EXEC DBMS_SHARD.SET_SHARD_TABLE(‘user1’,‘t1’,‘h’,‘i1’,‘node1’);
iSQL> EXEC DBMS_SHARD.SET_SHARD_TABLE_COMPOSITE(‘user1’,‘t2’,‘h’,‘i1’,‘r',‘i2',‘node1’); 
iSQL> SELECT * FROM sys_shard.objects_;
```

#### 샤드 테이블 해제

샤드 테이블을 해제할 수 있다. 샤드 테이블을 해제한다고 해서 테이블까지 삭제되는
것은 아니며, 테이블을 삭제하더라도 샤드 테이블이 해제되지는 않는다. 샤드
테이블의 설정은 테이블의 이름에 기반하므로 테이블이 재생성되고 샤드 키 이름이
동일하게 생성된다면 이전에 생성한 샤드 설정은 유효하다.

DBMS_SHARD 패키지에는 샤드 테이블을 해제하는 서브 프로그램을 제공한다.

##### 구문

```
DBMS_SHARD.UNSET_SHARD_TABLE
```

##### 설명

샤드 테이블을 해제한다.

##### 예제

```
iSQL> EXEC DBMS_SHARD.UNSET_SHARD_TABLE(‘user1’,‘t1’);
```

#### 샤드 프로시저 설정

샤드 프로시저는 일반 프로시저에 샤드 설정을 추가한 프로시저를 말한다.

샤드 프로시저는 실제 데이터를 갖지 않지만, 데이터를 다루는데 사용하는 함수로서
프로시저가 분산된 데이터를 처리한다. 프로시저의 수행을 분산하여 샤딩에서 사용할
수 있다.

샤드 프로시저의 파라미터들 중 하나가 샤드 키로 사용되며, 프로시저가 호출될 때의
파라미터 값으로 데이터 노드를 선택하여 선택된 데이터 노드에서 프로시저가
수행된다.

DBMS_SHARD 패키지는 샤드 프로시저를 추가하는 서브 프로그램을 제공한다.

##### 구문

```
DBMS_SHARD.SET_SHARD_PROCEDURE
DBMS_SHARD.SET_SHARD_PROCEDURE_COMPOSITE
```

##### 설명

샤드 프로시저를 설정한다. 샤드 프로시저 설정 구문에 대한 자세한 설명은
DBMS_SHARD 패키지의 *SET_SHARD_PROCEDURE* 또는 *SET_SHARD_PROCEDURE_COMPOSITE*을
참조한다.

##### 예제

```
iSQL> EXEC DBMS_SHARD.SET_SHARD_PROCEDURE(‘user1’,‘proc1’,‘h’,‘p1’,‘node1’);
iSQL> EXEC DBMS_SHARD.SET_SHARD_PROCEDURE_COMPOSITE(‘user1’,‘proc2’,‘h’,‘p1’,‘l',‘p2',‘node1’);
iSQL> SELECT * FROM sys_shard.objects_;
```

#### 샤드 프로시저 해제

샤드 프로시저를 해제할 수 있다. 샤드 프로시저를 해제하여도 프로시저까지 삭제되는
것은 아니다. 또한, 프로시저를 삭제하더라도 샤드 프로시저가 해제되는 것은 아니다.
샤드 프로시저의 설정은 프로시저의 이름에 기반하므로 프로시저가 재생성되고 샤드
키 파라미터의 이름이 동일하게 생성된다면 이전에 생성한 샤드 설정은 유효하다.

DBMS_SHARD 패키지에는 샤드 프로시저를 해제하는 서브 프로그램을 제공한다.

##### 구문

```
DBMS_SHARD.UNSET_SHARD_PROCEDURE
```

##### 설명

샤드 프로시져를 해제한다.

##### 예제

```
iSQL> EXEC DBMS_SHARD.UNSET_SHARD_PROCEDURE (‘user1’,‘proc1’);
```

### 분산 정보 설정

Altibase Sharding은 샤드 객체에 대하여 다음과 같은 분산 방식(split method)으로
분산 정보를 설정한다.

-   단일 샤드 키 분산 설정

-   해시(hash) 분산 설정

-   범위(range) 분산 설정

-   리스트(list) 분산 설정

-   복합(composite) 샤드 키 분산 설정

-   복제(clone) 분산 설정

-   독립(solo) 분산 설정

본 장에서는 각 분산 방식에 대한 설정 방법을 설명한다.

#### 해시(Hash) 분산 설정

해시 분산은 샤드 키 값을 hash하여 분산하는 방식이다.

Altibase Sharding은 hash 값을 1부터 1000까지 1000개의 hash group으로 관리한다.

Hash group 1부터 300까지는 node1에 저장하고, hash group 301부터 600까지는
node2에 저장하고, hash group 601부터 1000까지는 node3에 저장할 경우 다음과 같이
분산 정의한다.

-   hash_group[\<=300] -\> node1

-   hash_group[\<=600] -\> node2

-   hash_group[\<=1000] -\> node3

만일 기본 데이터 노드가 node3으로 정의되어 있다면 마지막 정의는 생략해도
동일하다.

##### 구문 

```
DBMS_SHARD.SET_SHARD_HASH
```

##### 설명

해시 방식의 분산 정보를 설정한다.

##### 예제

user1 사용자의 t1은 이미 해시 분산으로 설정되어 있다고 가정한다.

```
iSQL> EXEC DBMS_SHARD.SET_SHARD_HASH(‘user1’,‘t1’,300,‘node1’);
iSQL> EXEC DBMS_SHARD.SET_SHARD_HASH(‘user1’,’‘t1’,600,‘node2’);
iSQL> EXEC DBMS_SHARD.SET_SHARD_HASH(‘user1’,’‘t1’,1000,‘node3’);
iSQL> SELECT * FROM sys_shard.ranges_;
```

#### 범위(Range) 분산 설정

범위 분산은 샤드 키 값의 범위를 지정하여 분산하는 방식이다.

샤드 키 값이 ‘H’ 보다 작은 경우 node1에 저장하고, ‘H’보다 크고 ‘T’보다 작은 경우
node2에 저장하고, ‘T’보다 크고 ‘Z’보다 작은 경우 node3에 저장한다.

-   shard key value \<= ‘H’ 경우 –\> node1

-   ‘H’ \< shard key value \<= ‘T’ 경우’ –\> node2

-   ‘M’ \< shard key value \<= ‘Z’ 경우 –\> node3

샤드 키 값이 NULL인 경우 만약 데이터 노드가 정의되지 않았다면 에러가 발생하게
된다.

##### 구문 

```
DBMS_SHARD.SET_SHARD_RANGE
```

##### 설명

범위 방식의 분산 정보를 설정한다.

##### 예제

user1 사용자의 t1은 이미 범위 분산으로 설정되어 있다고 가정한다.

```
iSQL> EXEC DBMS_SHARD.SET_SHARD_RANGE(‘user1’,‘t1’,‘H’,‘node1’);
iSQL> EXEC DBMS_SHARD.SET_SHARD_RANGE(‘user1’,‘t1’,‘T’,‘node2’);
iSQL> EXEC DBMS_SHARD.SET_SHARD_RANGE(‘user1’,‘t1’,‘Z’,’‘node3’);
iSQL> SELECT * FROM sys_shard.ranges_;
```

#### 리스트(List) 분산 설정

리스트 분산은 샤드 키 값을 equal 연산으로 비교하여 분산하는 방식이다.

샤드 키 값이 ‘서울’인 경우 node1에 저장하고, ‘부산’인 경우 node2에 저장하고,
‘대구’인 경우 node3에 저장한다.

-   ‘서울’ –\> node1

-   ‘부산’ –\> node2

-   ‘대구’ –\> node3

이 때 ‘서울’, ‘부산’, ‘대구’ 외의 샤드 키 값은 기본 데이터 노드에 저장된다. 만약
기본 데이터 노드가 정의되지 않았다면 에러가 발생한다.

##### 구문

```
DBMS_SHARD.SET_SHARD_LIST
```

##### 설명

리스트 방식의 분산정보를 설정한다.

##### 예제

user1 사용자의 t1은 이미 list 분산으로 설정되어 있다고 가정한다.

```
iSQL> EXEC DBMS_SHARD.SET_SHARD_LIST(‘user1’,‘t1’,‘서울’, ‘node1’);
iSQL> EXEC DBMS_SHARD.SET_SHARD_LIST(‘user1’,‘t1’,‘부산’, ‘node2’);
iSQL> EXEC DBMS_SHARD.SET_SHARD_LIST(‘user1’,‘t1’,‘대구’, ‘node3’);
iSQL> SELECT * FROM sys_shard.ranges_;
```

#### 복합(Composite) 샤드 키 분산 설정

Altibase Sharding 은 두 개의 샤드 키를 적용하는 분산 방법으로 복합 샤드 키
분산을 제공한다.

샤드 키 분산 방식(hash, range, list)중에서 두 개의 샤드 키를 적용한 다중 분산
기법으로써, 각각의 샤드 키는 서로 다른 분산 방법을 적용할 수 있다. 단, 복합 샤드
키를 적용할 경우에는 아래의 패키지를 적용하여 샤드 객체를 설정해야 한다.

-   SET_SHARD_TABLE_COMPOSITE

-   SET_SHARD_PROCEDURE_COMPOSITE

복합 샤드 키를 적용한 샤드 객체를 해제 방법은 샤드 객체 해제 방법과 동일하다.

##### 구문 

```
DBMS_SHARD.SET_SHARD_COMPOSITE
```

##### 설명

복합 샤드 키 분산 정보를 설정한다.

##### 예제

user1 사용자의 t1은 이미 복합 샤드 키 분산으로 설정되어 있다고 가정한다.

```
iSQL> EXEC DBMS_SHARD.SET_SHARD_COMPOSITE(‘user1’,‘t1’,‘서울’,‘강남구’,‘node1’);
iSQL> EXEC DBMS_SHARD.SET_SHARD_COMPOSITE(‘user1’,‘t1’,‘서울’,‘강북구’,‘node2’);
iSQL> EXEC DBMS_SHARD.SET_SHARD_COMPOSITE(‘user1’,‘t1’,‘서울’,‘강서구’,‘node3’);
iSQL> EXEC DBMS_SHARD.SET_SHARD_COMPOSITE(‘user1’,‘t1’,‘부산’,‘강서구’,‘node1’);
iSQL> EXEC DBMS_SHARD.SET_SHARD_COMPOSITE(‘user1’,‘t1’,‘부산’,‘금정구’,‘node2’);
iSQL> EXEC DBMS_SHARD.SET_SHARD_COMPOSITE(‘user1’,‘t1’,‘부산’,‘남구’,‘node3’);
iSQL> SELECT * FROM sys_shard.ranges_;
```

#### 복제(Clone) 분산 설정

복제 분산은 샤드 키를 적용한 데이터 분산이 아닌 샤드 객체가 복제되어 저장된
상태를 의미한다. 복제 분산을 적용하는 샤드 객체는 샤드 키가 필요없고 복제될
데이터 노드만 지정한다.

##### 구문

```
DBMS_SHARD.SET_SHARD_CLONE
```

##### 설명

복제 방식의 분산정보를 설정한다.

##### 예제

user1 사용자의 t1은 이미 복제 분산으로 설정되어 있다고 가정한다.

```
iSQL> EXEC DBMS_SHARD.SET_SHARD_CLONE(‘user1’,‘t1’,‘node1’);
iSQL> EXEC DBMS_SHARD.SET_SHARD_CLONE(‘user1’,‘t1’,‘node2’);
iSQL> EXEC DBMS_SHARD.SET_SHARD_CLONE(‘user1’,‘t1’,‘node3’);
iSQL> SELECT * FROM sys_shard.clones_;
```

#### 독립(Solo) 분산 설정

독립 분산은 샤드 키를 적용한 데이터 분산이 아닌 샤드 객체 단위의 분산 방식이다.
독립 분산 역시 샤드 키를 지정하지 않고 사용자가 원하는 하나의 노드를 지정한다.

##### 구문

```
DBMS_SHARD.SET_SHARD_SOLO
```

##### 설명

독립 방식의 분산정보를 설정한다.

##### 예제

user1 사용자의 t1은 이미 독립 분산으로 설정되어 있다고 가정한다.

```
iSQL> EXEC DBMS_SHARD.SET_SHARD_SOLO(‘user1’,‘t1’,‘node1’);
iSQL> SELECT * FROM sys_shard.solos_;
```

### 샤드 키

샤드 키(shard key)는 데이터를 분산하는 기준이 되는 테이블의 컬럼 혹은 프로시저의
파라미터를 말한다. 샤드 키는 최대 두 개의 컬럼 혹은 파라미터에 대해서 정의할 수
있다.

샤드 키는 다음과 같은 데이터 타입을 지원한다.

-   smallint

-   integer

-   bigint

-   char

-   varchar

샤드 키의 설정에 대한 설명은 이 장의 ''를 참고한다.

### 샤드 트랜잭션

Altibase Sharding은 분산된 여러 데이터베이스를 다루게 되므로 이에 대한 트랜잭션
처리가 필요하다. Altibase Sharding에서 다루는 여러 데이터베이스에 대한
트랜잭션을 다음과 같이 구분한다.

-   단일 노드 트랜잭션 (single node transaction)

-   다중 노드 트랜잭션 (multiple node transaction)

-   글로벌 트랜잭션 (global transaction)

#### 단일 노드 트랜잭션

Altibase Sharding에서 ACID를 보장하기 위하여 처음부터 단일 데이터 노드에 대한
트랜잭션만 허용하는 정책을 의미한다.

Altibase Sharding에서 트랜잭션을 시작할 때 단일 노드 트랜잭션을 선언하면,
트랜잭션 내에서 최초 쿼리를 수행하는 데이터 노드에서만 이후 쿼리가 수행된다.

##### 구문

```
SQLSetConnectAttr (
	SQLHDBC 	dbc,
	SQLINTEGER 	Attribute,
	SQLPOINTER	ValuePtr,
	SQLINTEGER 	StringLength );
```

##### 설명

단일 노드 트랜잭션을 설정한다. 단일 노드 트랜잭션으로 설정할 때에는
*StringLength* 인자 값에 ALTIBASE_SHARD_SINGLE_NODE_TRANSACTION을 입력한다.
SQLSetConnectAttr에 대한 자세한 설명은 “*CLI User's Manual \> 2. Altibase CLI
함수”를* 참조한다.

##### 예제

```
SQLSetConnectAttr(dbc, SQL_ATTR_AUTOCOMMIT, (void*)SQL_AUTOCOMMIT_OFF, 0);
혹은
SQLSetConnectAttr(dbc, SQL_ATTR_AUTOCOMMIT, (void*)SQL_AUTOCOMMIT_OFF, ALTIBASE_SHARD_SINGLE_NODE_TRANSACTION);
```

#### 다중 노드 트랜잭션

Altibase Sharding에서 ACID는 보장하지는 않지만, 여러 데이터 노드에 대한
트랜잭션을 허용하는 트랜잭션을 말한다.

Altibase Sharding에서 트랜잭션을 시작할 때 다중 노드 트랜잭션을 선언하면 여러
데이터 노드에 모두 쿼리를 수행할 수 있다. 트랜잭션의 커밋, 롤백은 모든 데이터
노드로 순차적으로 수행된다.

커밋 또는 롤백 시 데이터 노드에 장애가 발생한 경우, 샤드 라이브러리는 그 즉시
에러를 반환한다. 따라서, 데이터의 일관성 확인이 필요하다.

##### 구문

```
SQLSetConnectAttr (
	SQLHDBC 	dbc,
	SQLINTEGER 	Attribute,
	SQLPOINTER	ValuePtr,
	SQLINTEGER 	StringLength );
```

##### 설명

다중 노드 트랜잭션을 설정한다. 다중 노드 트랜잭션으로 설정할 때에는
*StringLength* 인자 값에 ALTIBASE_SHARD_MULTIPLE_NODE_TRANSACTION을 입력한다.
SQLSetConnectAttr에 대한 자세한 설명은 “*CLI User's Manual \> 2. Altibase CLI
함수”*를 참조한다.

##### 예제

```
SQLSetConnectAttr(dbc, SQL_ATTR_AUTOCOMMIT, (void*)SQL_AUTOCOMMIT_OFF, ALTIBASE_SHARD_MULTIPLE_NODE_TRANSACTION);
```

#### 글로벌 트랜잭션

Altibase Sharding에서 ACID를 보장하면서 여러 데이터 노드에 대한 트랜잭션
일관성을 보장하는 트랜잭션을 말한다.

##### 구문

```
SQLSetConnectAttr (
	SQLHDBC 	dbc,
	SQLINTEGER 	Attribute,
	SQLPOINTER	ValuePtr,
	SQLINTEGER 	StringLength );
```

##### 설명

글로벌 트랜잭션을 설정한다. 글로벌 트랜잭션으로 설정할 때에는 *StringLength*
인자 값에 ALTIBASE_SHARD_GLOBAL_TRANSACTION을 입력한다. SQLSetConnectAttr에 대한
자세한 설명은 “*CLI User's Manual \> 2. Altibase CLI 함수”*를 참조한다.

##### 예제

```
SQLSetConnectAttr(dbc, SQL_ATTR_AUTOCOMMIT, (void*)SQL_AUTOCOMMIT_OFF, ALTIBASE_SHARD_GLOBAL_TRANSACTION);
```

### 샤드 쿼리

샤드 쿼리(shard query)란 분산된 각 데이터베이스에서의 질의 결과의 합이
논리적으로 분산되지 않은 상태의 데이터베이스 질의 결과와 같은 경우를 말한다.

Altibase Sharding은 다음과 같은 구문을 지원한다.

-   INSERT

-   INSERT SELECT

-   UPDATE

-   DELETE

-   SELECT

각 구문에 대해 대표적인 샤드 쿼리의 판단 기준은 다음과 같다.

-   샤드 키에 대한 equal value 형식의 조건절이 있는 형태

-   SELECT \* FROM t1과 같이 단순히 결과를 취합하는 형태

그러나 현실에서는 보다 다양하고 복잡한 형태의 쿼리가 수행되므로 일부 사례 설명을
위해 아래와 같은 테이블이 생성되어 있다고 가정한다.

-   동일한 샤드 키 분산 방식을 적용한 샤드 테이블 s1, s2

-   (샤드 키 컬럼 k1, 일반 컬럼 i1)

-   복제 분산 방식을 적용한 샤드 테이블 c1 (일반 컬럼 i1)

-   독립 분산 방식을 적용한 샤드 테이블 so1 (일반 컬럼 i1)

-   일반 테이블 t1 (일반 컬럼 i1)

#### INSERT

모든 샤드 테이블(s1, c1, so1)에 대해 모든 형태의 insert 구문을 지원한다.

Insert 값에 따라 단일 데이터 노드에서 수행하는 샤드 쿼리는 다음과 같다.

-   INSERT INTO s1(k1, i1) VALUES(?, 2);

-   INSERT INTO so1(i1) VALUES(?);

샤드 키 분산 테이블에 INSERT를 수행하는 경우 샤드 키에 해당하는 값에 수식이
있거나, 시퀀스, 또는 서브 쿼리가 있을 수 있다. 이 때 메타 노드에서 그 값을 미리
계산한 후에 해당 데이터 노드로 전달한다.

-   INSERT INTO s1(i1, i2) VALUES(?+1, 2)

-   INSERT INTO s1(i1, i2) VALUES(seq1.nextval, 2)

-   INSERT INTO s1(i1, i2) VALUES((SELECT 1 FROM dual), 2)

여러 노드에 걸쳐 있는 복제 분산 테이블의 경우 다중 데이터 노드에 수행한다.

-   INSERT INTO c1(i1) VALUES (?)

##### 구문

```
INSERT INTO s1 VALUES(1, 2);
```

##### 예제

\<질의\> s1테이블에 insert를 수행하라.

```
iSQL> INSERT INTO s1 VALUES(1, 2);
```

#### INSERT SELECT

Insert select문은 항상 다중 데이터 노드 수행 쿼리이므로 메타 커넥션으로
수행된다.Insert select문을 이용하면 다른 분산 테이블에 데이터를 복사할 수 있다.

##### 구문

```
INSERT INTO s2 SELECT * FROM s1;
```

##### 예제

\<질의\> 분산 테이블 s1의 데이터를 분산 테이블 s2에 복사하라.

```
iSQL> INSERT INTO s2 SELECT * FROM s1;
```

#### UPDATE

조건절에 따라 UPDATE 문을 단일 데이터 노드 수행 쿼리와 다중 데이터 노드 수행
쿼리로 나눈다. 샤드 키 컬럼은 update할 수 없다.

##### 구문

```
UPDATE s1 SET i1=3 WHERE k1=1;
```

##### 예제

\<질의\> s1테이블의 k1컬럼이 1인 레코드에 대해 i1컬럼을 3으로 update하라.

```
iSQL> UPDATE s1 SET i1=3 WHERE k1=1;
```

\<질의\> s1테이블의 i1컬럼을 모두 3으로 update하라.

```
iSQL> UPDATE s1 SET i1=3;
```

#### DELETE

조건절에 따라 DELETE 문을 단일 데이터 노드 수행 쿼리와 다중 데이터 노드 수행
쿼리로 나눈다.

##### 구문

```
DELETE FROM s1 WHERE k1=1;
```

##### 예제

\<질의\> s1테이블에서 k1 칼럼의 값이 1인 레코드를 삭제한다.

```
iSQL> DELETE FROM s1 WHERE k1=1;
```

#### SELECT

Select문은 조건절에 따라 수행방법이 영향을 받는다.

##### 구문

```
SELECT * FROM s1 WHERE k1=1;
```

##### 예제

\<질의\> s1테이블의 k1칼럼의 값이 1인 레코드를 조회한다.

```
iSQL> SELECT * FROM s1 WHERE k1=1;
```

> ##### 주의 사항
>
> Select문은 사용 유형이 다양한 만큼 그 수행 여부에 영향을 줄 수 있는 요소가 많다.

Altibase Sharding은 샤드 테이블에 대해 다음과 같은 유형을 지원한다.

-   Join

-   Aggregate function

-   Grouping

-   Ordering

-   Subquery

##### Join

Select 시 샤드 테이블에 다음과 같은 형태의 join구문을 지원한다.

###### Inner join

동일한 샤드 키 분산 방식이 적용된 샤드 테이블(s1,s2)간의 샤드 키 inner join을
지원한다.

-   SELECT \~ FROM *s1, s2* WHERE *s1.k1 = s2.k1*

Join 구문 역시 쿼리 최적화를 통해 수행되기 때문에 샤드 키를 필터로 적용할 경우
샤드 키에 해당하는 데이터 노드로 샤드 커넥션을 생성하여 해당 노드에 직접
수행한다. 하지만 샤드 키 필터를 적용하지 않을 경우 메타 커넥션을 생성하여 모든
데이터 노드에 수행한 후 샤드 코디네이터가 그 결과를 취합하여 사용자에게
전달한다.

-   SELECT \~ FROM s1, s2 WHERE s1.k1 = s2.k1 AND [s1.k1\|s2.k1] = ?  
    =\> 샤드 커넥션으로 특정 노드에 직접 수행

-   SELECT \~ FROM s1, s2 WHERE s1.k1 = s2.k1 AND [s1.i1\|s2.i1] = ?  
    =\> 메타 커넥션으로 모든 노드를 수행하고 취합 후 전달 받음

복제 분산 테이블(c1)의 경우 모든 샤드 테이블(s1,c1,so1)에 대해 inner join을
지원한다.

-   SELECT \~ FROM *c1, s1* WHERE *c1.i1 = s1.i1*

-   SELECT \~ FROM c1, so1 WHERE c1.i1 = so1.i1

독립 분산 테이블(so1)과 복제 분산 테이블(c1)의 inner join시 특정 데이터 노드를
지정하는 독립 분산 테이블(so1)의 특성상 필터의 유무와 무관하게 샤드 커넥션으로
동작한다.

-   SELECT \~ FROM *c1, so1* WHERE *c1.i1 = so1.i1*

-   =\> 샤드 커넥션으로 특정 노드로 직접 수행

###### Outer join

동일한 샤드 키 분산 방식이 적용된 샤드 테이블(s1,s2)간의 샤드 키 outer join을
지원한다.

-   SELECT \~ FROM *s1* LEFT OUTER JOIN *s2* ON *s1.k1 = s2.k1*

-   SELECT \~ FROM *s1* RIGHT OUTER JOIN *s2* ON *s1.k1 = s2.k1*

-   SELECT \~ FROM *s1* FULL OUTER JOIN *s2* ON *s1.k1 = s2.k1*

샤드 키 분산 테이블(s1)과 복제 분산 테이블(c1)의 경우 아래 유형에 한해 지원한다.

-   SELECT \~ FROM *s1* LEFT OUTER JOIN *c1* ON *c1.i1 = s1.i1*

복제 분산 테이블(c1)과 독립 분산 테이블(so1)간의 모든 outer join 을 지원한다.

-   SELECT \~ FROM *c1* LEFT OUTER JOIN *so1* ON *c1.i1 = so1.i1*

-   SELECT \~ FROM *c1* RIGHT OUTER JOIN *so1* ON c*1.i1 = so1.i1*

-   SELECT \~ FROM *c1* FULL OUTER JOIN *so1* ON *so1.i1 = c1.i1*

Outer join이 inner join으로 변환될 경우를 지원한다. 다음 쿼리는 쿼리 변환기를
거쳐 inner join으로 변환되어 수행한다.

-   SELECT \~ FROM *s1* RIGHT OUTER JOIN *c1* ON *c1.i1 = s1.i1* WHERE *s1.i1 =
    1*

-   =\> SELECT \~ FROM *s1* INNER JOIN *c1* ON *c1.i1 = s1.i1* WHERE *s1.i1 = 1*

###### Semi- join

동일한 샤드 키 분산 방식이 적용된 샤드 테이블(s1,s2)간의 semi-join을 지원한다.

-   SELECT \~ FROM *s1* WHERE *EXISTS* (SELECT \~ FROM *s2* WHERE *s1.k1 =
    s2.k1* AND \~) AND \~

복제 분산 테이블(c1)의 경우 모든 샤드 테이블에 대해 semi-join을 지원한다.

-   SELECT \~ FROM c1 WHERE *EXISTS* (SELECT \~ FROM *s1* WHERE *c1.i1 = s1.i1*
    AND \~) AND \~

-   SELECT \~ FROM s1 WHERE *EXISTS* (SELECT \~ FROM *c1* WHERE *c1.i1 = so1.i1*
    AND \~) AND \~

###### 제약 사항

다음의 경우는 지원하지 않는다.

-   조인 조건이 없는 cartesian join

-   샤드 키 분산 방식이 다른 샤드 키 분산 테이블간의 join

-   다중 노드의 분산 정보를 갖는 샤드 키 분산 테이블과 독립 분산 테이블간의 join

-   샤드 테이블과 일반 테이블간의 join

-   Anti-join

##### Aggregate function

Altibase Sharding 은 샤드 테이블에 대해 아래 집계 함수를 지원한다.

-   COUNT

-   MIN

-   MAX

-   SUM

-   AVG

-   STDDEV

-   VARIANCE

샤드 키 분산 테이블의 경우 분산 데이터의 특성상 데이터 노드 각각에 대해 집계를
수행하므로 그 결과는 모든 데이터의 집계 결과와 논리적으로 같을 수 없다. 따라서
샤드 키 분산 테이블(s1)의 경우 샤드 키 컬럼으로 필터링 되는 경우에 한해
지원한다.

-   SELECT *count(\*)* FROM *s1* WHERE *k1 = ?* \~

-   SELECT *sum(k1)* FROM *s1* WHERE *k1 = ?* \~

특정 데이터 노드에서 동작하는 복제 분산 테이블(c1)과 독립 분산 테이블(so1)은
일반 테이블의 경우와 동일하게 수행한다.

-   SELECT *count(\*)* FROM *c1*\~

-   SELECT *sum(k1)* FROM *so1* \~

##### Grouping

Altibase Sharding은 샤드 테이블에 대해 다음 grouping 방식을 지원한다.

-   GROUP BY 구문

-   DISTINCT 구문

샤드 키 분산 테이블(s1)에서 샤드 키 컬럼을 grouping 대상으로 포함하는 모든
구문을 지원한다.

-   SELECT \~ FROM *s1* \~ GROUP BY *k1*,\~

-   SELECT distinct *k1*,\~ FROM *s1* \~

-   SELECT distinct *k1*,\~ FROM *s1* \~ GROUP BY *k1*,\~

특정 데이터 노드에서 동작하는 복제 분산 테이블(c1)과 독립 분산 테이블(so1)은
별다른 제약없이 수행된다.

-   SELECT \~ FROM *c1* \~ GROUP BY \~

-   SELECT distinct \~ FROM *c1* \~

-   SELECT distinct \~ FROM *so1* \~ GROUP BY \~

##### Ordering

Altibase Sharding 은 샤드 테이블(s1, c1, so1)에 대해 순차적 정렬 방식을
지원한다.

-   SELECT \~ FROM *s1* \~ORDER BY \~

-   SELECT \~ FROM *c1* \~ORDER BY \~

-   SELECT \~ FROM *so1* \~ORDER BY \~

##### Subquery

Altibase Sharding 은 샤드 테이블을 포함하는 subquery유형을 지원한다.

-   INSERT SELECT

-   Inline view

-   Subquery expression

###### INSERT SELECT

INSERT에 사용되는 샤드 테이블의 subquery 형태를 지원한다.

-   INSERT \~ SELECT \~ FROM *s1* \~

-   INSERT \~ SELECT \~ FROM *c1* \~

-   INSERT \~ SELECT \~ FROM *so1* \~

###### Inline view

From 절에 사용되는 샤드 테이블의 inline view 형태를 지원한다.

-   SELECT \~ FROM (SELECT \~ FROM s1 \~) s, \~

-   SELECT \~ FROM (SELECT \~ FROM c1 \~) c, \~

-   SELECT \~ FROM (SELECT \~ FROM so1 \~) so, \~

###### Subquery expression

샤드 키 분산 테이블(s1)을 사용한 subquery를 expression 형태로 사용할 경우에는
샤드 키에 대한 필터가 반드시 존재해야 한다. 이는 subquery expression의 결과가
single row여야 하고 grouping에 대한 샤드 키 필터가 존재해야 하는 이유와
동일하다.

-   SELECT (SELECT \~ FROM *s1* WHERE *s1.k1 = ?*) FROM \~

-   SELECT \~ FROM t1 WHERE t1.i1 = (SELECT max(i1) FROM *s1* WHERE *s1.k1 = ?*)

-   SELECT i1 FROM t1 WHERE i1 in (select *k1* from *s1*)

-   SELECT i1 FROM t1 WHERE i1 in (select *i1* from *s1*)

Subquery 내부에서 사용된 복제 분산 테이블(c1)과 독립 분산 테이블(so1)은 필터의
제한 없이 수행 가능하다.

-   SELECT (SELECT \~ FROM *c1*) FROM t1 \~

-   SELECT \~ FROM t1 WHERE t1.i1 = (SELECT max(i1) FROM *so1*)

복제 분산 테이블(c1)이 사용된 subquery는 샤드 테이블(s1,c1,so1)인 외부 컬럼과의
subquery join식을 지원한다.

-   SELECT \* FROM *s1* WHERE k1 in (SELECT i1 FROM *c1*)

-   SELECT \* FROM *s1* WHERE s1.i1 in (SELECT i1 FROM *c1* GROUP BY i1)

-   SELECT \* FROM *so1* WHERE i1 = (SELECT i1 FROM *c1* WHERE i1 = so1.i1)

-   SELECT \* FROM *c1 a* WHERE a.i1 = (SELECT min(i1) FROM *c1* WHERE i1 =
    a.i1)

###### 제약 사항

분산 키 적용 테이블(s1, ss1)간의 subquery join 식은 지원하지 않는다.

-   SELECT \~ FROM *s1* WHERE *s1.k1* in (SELECT *k1* FROM *ss1*)

분산 키 적용 테이블(s1)과 독립 분산 테이블(so1)의 subquery join식은 지원하지
않는다.

-   SELECT \~ FROM *s1* WHERE *s1.k1* in (SELECT *i1* FROM *so1*)

샤드 테이블이 사용된 subquery는 일반 테이블의 외부 컬럼과 join 식을 지원하지
않는다.

-   SELECT i1 FROM *t1* WHERE i1 in (SELECT k1 FROM *s1* WHERE *k1 = t1.i1*)

-   SELECT \* FROM *t1* WHERE i1 = (SELECT i1 FROM *c1* WHERE *i1 = t1.i1*)

-   SELECT \* FROM *t1* WHERE exists (SELECT i1 FROM *so1* WHERE *i1 = t1.i1*)

Unnesting, view merge 등의 서브 쿼리에 대한 변환이 수행될 경우 변환 결과에 따라
그 수행 여부가 결정된다.

### 샤드 키워드

사용자는 특정 노드의 현재 데이터 상태를 확인하거나 특정 노드의 데이터를 취합하는
것을 원할 수 있다.

Altibase Sharding은 사용자의 요구사항을 처리하기 위해 메타 또는 데이터 노드에
쿼리를 전송하고 그 수행 결과를 취합할 수 있는 샤드 키워드를 제공한다.

-   SHARD

-   NODE[META \| DATA \| DATA() \| DATA('*node1_name'*, '*node2_name'*...)]

#### 구문

샤드 키워드는 다음 구문에 한해 제공하며 구문식은 다음과 같다.

-   INSERT

-   UPDATE

-   DELETE

-   SELECT

![](media/Sharding/79bcb8f6b5cb10cc7a7b816363aa709f.jpg)

**shard_keyword_clause::=**

![](media/Sharding/d15e35752ab4fd66496232e1d1e055a1.jpg)

#### SHARD

SHARD 키워드를 사용하면 샤드 쿼리 분석기를 통해 분산 정보가 존재하는 모든 데이터
노드에 쿼리를 전송하고 수행하여 취합한다.

각 데이터 노드의 데이터를 취합한 결과가 논리적으로 동일할 수 없는 즉, 샤드
쿼리가 아닌 다음의 사례를 살펴보자.

-   SELECT count(\*) FROM *s1;*

일반 쿼리에 SHARD 키워드를 적용하면 분산 정보가 존재하는 모든 데이터 노드를
대상으로 쿼리를 수행하고 그 결과를 얻어온다.

-   SHARD SELECT count(\*) FROM *s1;*

-   SELECT \* FROM SHARD*(* SELECT count(\*) FROM *s1);*

아래와 같은 형태를 적절히 활용하면 사용자가 원하는 유용한 결과를 얻을 수 있다.

-   SELECT sum(cn) FROM SHARD ( SELECT count(\*) cn FROM s1);

-   SELECT i1, sum(cn) FROM SHARD (SELECT i1, count(\*) cn FROM s1) GROUP BY i1;

-   SELECT \* FROM SHARD (SELECT \* FROM s1 limit 10) limit 10;

##### 구문

```
SHARD SELECT * FROM s1 WHERE k1>1;
SELECT * FROM SHARD(SELECT * FROM s1 WHERE k1>1);
```

##### 예제

\<질의\> s1테이블의 전체 레코드 개수를 구하라.

```
iSQL> SELECT sum(cn) FROM SHARD(SELECT count(*) cn FROM s1);
```

#### NODE

NODE 키워드는 인자로 명시한 노드에 쿼리를 전송하고 그 수행 결과를 취합한다.

사용 가능한 NODE 유형은 다음과 같다.

-   NODE[META] : 메타 노드에 대한 쿼리 수행

-   NODE[DATA] 또는 NODE[DATA()] : 모든 데이터 노드들에 대한 수행

-   NODE[DATA(*'node1_name*', *node2_name*',...)] : 명시된 데이터 노드(들)에
    대한 쿼리 수행

노드를 구성하고 샤드 객체 구성 전 후의 데이터 상태를 확인할 경우에 유용하게 쓰일
수 있다.

##### 구문

```
NODE[META] SELECT count(*) FROM t1;
NODE[DATA] SELECT count(*) FROM s1;
SELECT * FROM NODE[META](SELECT count(*) FROM s1);
SELECT * FROM NODE[DATA]('node1', 'node2')](SELECT count(*) FROM s1);
```

\<질의\> 메타 노드에 존재하는 t2테이블의 전체 레코드 개수를 구하라. (t2의 샤드
구성 단계에서 아직 데이터를 이동시키지 않은 상태)

```
iSQL> CREATE TABLE t2 AS SELECT * FROM s1
iSQL> EXEC dbms_shard.set_shard_table('sys','t2','H','i1');
iSQL> EXEC dbms_shard.set_shard_hash('sys','t2',1000,'node1');
iSQL> NODE[META] SELECT count(*) FROM t1;
```

\<질의\> 'node2' 데이터 노드에 존재하는 s1 샤드 테이블에 대해 샤드키가 아닌 i1
컬럼의 group별 합을 수행하라.

```
iSQL> SELECT * FROM NODE[DATA('node2')](SELECT i1,sum(i1) FROM s1 GROUP BY i1);
```

> ##### 주의 사항
>
> 샤드 키워드의 적용 결과는 단순히 해당 노드의 수행 결과를 얻어 취합하는 것이므로
> 결과의 정합성을 보장하기 어렵다. 따라서 사용에 각별한 주의가 필요하다.

### 샤드 함수

Altibase Sharding은 사용자 편의를 위해 추가적인 샤드 함수를 제공한다.

#### shard_node_name

##### 구문

```
shard_node_name()
```

##### 설명

데이터 노드의 이름을 반환한다.

##### 예제

\<질의\> 데이터 노드 별 s1테이블의 레코드 개수를 구하라.

```
iSQL> shard SELECT shard_node_name(),count(*) FROM s1;
```

#### shard_key

##### 구문

```
shard_key(key_column, value)
```

##### 설명

데이터 노드를 지정하여 질의를 수행한다.

##### 예제

\<질의\> s1테이블의 k1이 1에 해당하는 데이터 노드에서 s1테이블의 레코드 개수를
구하라.

```
iSQL> SELECT count(*) FROM s1 WHERE shard_key(k1,1); 
```

### 샤드 실행계획

Altibase Sharding 사용자는 iSQL을 통해 쿼리가 수행되는 실행계획을 조회할 수
있다.

샤드 최적화기가 생성한 실행계획과 데이터 노드에서 생성한 실행계획까지 모두
조회할 수 있다.

#### 실행 노드

샤드 최적화기가 생성한 실행노드의 기능과 explain plan으로 출력되는 형식, 해당
노드가 출력되는 쿼리 예제를 살펴본다.

##### 출력 형식

SHARD-COORDINATOR

##### 설명

SHARD-COORDINATOR 실행노드는 사용자가 입력한 쿼리 중 데이터 노드에서 수행할
쿼리를 수행하고, 그 결과를 통합하여 상위 실행노드로 전달한다.

보다 상세한 수행 결과를 조회하기 위하여 다음 명령을 사용한다.

ALTER SESSION SET TRCLOG_DETAIL_PREDICATE = 1;

TRCLOG_DETAIL_PREDICATE 프로퍼티 값을 1로 설정하면, SHARD-COORDINATOR가 특정
데이터 노드로 쿼리를 보내어 수행한 이력과 데이터 노드에서의 플랜까지 조회가
가능하다.

다음은 쿼리 문의 실행 결과 출력이다.

```
iSQL> alter session set explain plan = on;
Alter success.
iSQL> alter session set trclog_detail_predicate = 1;
Alter success.
iSQL> select * from t1, t2 where t1.i1=t2.i1;
I1          I2          I1          I2
-----------------------------------------------------
7           test1       7           test2
10          test1       10          test2
1           test1       1           test2
3           test1       3           test2
5           test1       5           test2
6           test1       6           test2
8           test1       8           test2
2           test1       2           test2
4           test1       4           test2
9           test1       9           test2
10 rows selected.
------------------------------------------------------------
PROJECT ( COLUMN_COUNT: 4, TUPLE_SIZE: 32, COST: 1174.86 )
 SHARD-COORDINATOR
  [ SHARD EXECUTION ]
  NODE1 (executed)
   ::-----------------------------------------------------------
   ::PROJECT ( COLUMN_COUNT: 4, TUPLE_SIZE: 32, COST: 6339.74 )
   :: JOIN ( METHOD: INDEX_NL, COST: 935.45 )
   ::  SCAN ( TABLE: SYS.T1, FULL SCAN, ACCESS: 2, COST: 116.76 )
   ::  SCAN ( TABLE: SYS.T2, INDEX: SYS.IDX2, RANGE SCAN, ACCESS: 2, COST: 116.76 )
   ::-----------------------------------------------------------
  NODE2 (executed)
   ::-----------------------------------------------------------
   ::PROJECT ( COLUMN_COUNT: 4, TUPLE_SIZE: 32, COST: 6339.74 )
   :: JOIN ( METHOD: INDEX_NL, COST: 935.45 )
   ::  SCAN ( TABLE: SYS.T1, FULL SCAN, ACCESS: 5, COST: 116.76 )
   ::  SCAN ( TABLE: SYS.T2, INDEX: SYS.IDX2, RANGE SCAN, ACCESS: 5, COST: 116.76 )
   ::-----------------------------------------------------------
  NODE3 (executed)
   ::-----------------------------------------------------------
   ::PROJECT ( COLUMN_COUNT: 4, TUPLE_SIZE: 32, COST: 6339.74 )
   :: JOIN ( METHOD: INDEX_NL, COST: 935.45 )
   ::  SCAN ( TABLE: SYS.T1, FULL SCAN, ACCESS: 3, COST: 116.76 )
   ::  SCAN ( TABLE: SYS.T2, INDEX: SYS.IDX2, RANGE SCAN, ACCESS: 3, COST: 116.76 )
   ::-----------------------------------------------------------
------------------------------------------------------------
```

### 쿼리 튜닝 

Altibase Sharding 사용자는 샤드 키워드를 이용하여 메타 노드에 부하를 주는 쿼리를
튜닝할 수 있다.

#### Grouping

grouping의 키로 샤드 키가 포함된 경우 샤드 쿼리 분석기는 샤드 쿼리로 판단한다.

그러나 grouping key에 샤드 키가 포함되지 않으면, 분산 테이블의 모든 레코드를
grouping하게 되므로 메타 노드에 부하를 많이 줄 수 있다. 이런 경우 grouping을
데이터 노드에서 수행하도록 변경하면 메타 노드의 부하도 줄고 쿼리 속도도
빨라진다.

```
SELECT c1, count(*), sum(i2), avg(i2) FROM s1 GROUP BY c1;
```

위의 쿼리에 다음과 같이 SHARD 키워드를 사용하여 변경할 수 있다.

```
SELECT c1, sum(c), sum(s), sum(s)/count(a) FROM SHARD(SELECT c1, count(*) c, sum(i2) s, count(i2) a FROM s1 GROUP BY c1) GROUP BY c1;
```

#### Pushdown

서로 다른 분할방식의 테이블을 조인하는 경우, 조인은 메타 노드에서 수행하게 된다.

이 때, 조인 비용을 줄이기 위해서 조건절을 데이터 노드에서 수행하도록 변경하면
메타 노드의 부하도 줄고 쿼리 속도도 빨라진다.

다음과 같은 쿼리가 있다.

```
SELECT * FROM t1, t2 WHERE t1.i1=t2.i1 AND t1.i2>3;
```

이를 SHARD 키워드를 사용하여 다음과 같이 변경할 수 있다.

```
SELECT * FROM SHARD(SELECT * FROM T1 WHERE I2>3) t1, t2 WHERE t1.i1=t2.i1;
```

### 모니터링 

Altibase Sharding 사용자는 NODE 키워드를 이용하여 메타 노드에서 데이터 노드를
모니터링 할 수 있다. NODE 키워드는 샤드 객체로 등록하지 않았더라도 메타 노드에서
쿼리를 수행할 수 있도록 해준다.

NODE 키워드는 모든 데이터 노드에 대해 쿼리를 전송하므로 데이터 노드의 상태에
따라 쿼리가 실패할 수 있다.

NODE 키워드는 모든 데이터 노드에 대해 쿼리를 동시에 수행하므로 모든 데이터
노드를 한번에 관찰하기에 유용하다.

#### Session 조회

NODE 키워드를 이용하여 데이터 노드의 V\$SESSION 을 조회할 수 있다.

```
NODE[DATA] SELECT shard_node_name(), count(*) total_session, sum(decode(trans_id,0,0,1)) running_session from v$session;
```

뿐만 아니라, 특정 데이터 노드에 대해서도 수행이 가능하다.

```
NODE[DATA(‘node1’)] SELECT shard_node_name(), count(*) total_session, sum(decode(trans_id,0,0,1)) running_session from v$session;
```

#### Statement 조회

NODE 키워드를 이용하여 데이터 노드의 v\$statement을 조회할 수 있다.

```
NODE[DATA] SELECT shard_node_name(), sum(execute_success) from v$statement
```

뿐만 아니라, 특정 데이터 노드에 대해서도 수행이 가능하다.

```
NODE[DATA(‘node1’)] SELECT shard_node_name(), sum(execute_success) from v$statement
```

### 자동 데이터 재구축

Altibase Sharding은 샤드 테이블의 분산 정보를 변경한 후, 기존의 데이터를
자동으로 재구축하는 방법을 제공한다.

데이터 재구축을 위해서는 기존 분산 테이블을 해제(unset)한 후, 새로운 분산
방식으로 분산 테이블을 재설정(set)하는 과정을 선행해야 한다.

성능을 고려하여, 자동 데이터 재구축은 변경된 분산 기준에 맞지 않는
데이터(incorrect data)만 이동(move)시키는 방식으로 수행되며 여러 세션에서 동시에
수행 가능하다. 단, 내부적으로 데이터의 이동이 수반되기 때문에 데이터의 정합성
보장을 위해서 다음과 같은 환경으로 수행하길 권장한다.

-   Non-autocommit

-   Global Transaction

자동 데이터 재구축은 샤드 키 분산(hash, range, list, composite) 방식을 적용한
샤드 테이블에 한해 지원하며, 복제 분산 방식과 독립 분산 방식은 지원하지 않는다.

-   hash(500,1000) \<-\> hash(300,600,1000) (O)

-   hash \<-\> range (O)

-   hash \<-\> list,hash (O)

-   range \<-\> clone (X)

-   solo \<-\> hash (X)

-   clone \<-\> solo (X)

#### 유효성 검사

샤드 테이블의 샤드 키 분산 방식 변경으로 인해 샤드 키와 데이터의 불일치가
발생할 수 있다. 분산 정보가 재설정 된 경우 기존의 분산 데이터는 샤드 키에
유효한(correct) 데이터와 유효하지 않은(incorrect) 데이터로 구분된다.

Altibase Sharding 은 샤드 키 분산 정보와 분산 데이터의 유효성을 검사하는
방법을 제공한다.

##### 구문

```
DBMS_SHARD.CHECK_DATA
```

##### 설명

분산 테이블의 샤드 키 분산 정보와 데이터 노드별 유효 또는 유효하지 않은 데이터
행 수를 반환한다.

##### 예제

U1 사용자의 s1 테이블에 대한 샤드 키 k1의 분산방식을 다음과 같이 변경할 경우
변경 전 후의 데이터 유효성을 검사한다.

-   hash( 500:NODE1,1000:NODE2)

-   =\> range(330:NODE1,660:NODE2,default:NODE3)

```
iSQL> EXEC dbms_shard.check_data('u1','s1');
shard_key_column:K1
shard_information:{"SplitMethod":"H","RangeInfo":[{"Value":"500","Node":"NODE1"},{"Value":"1000","Node":"NODE2"}]}
node_name:NODE1, record_count:491, correct_count:491, incorrect_count:0
node_name:NODE2, record_count:509, correct_count:509, incorrect_count:0
total_record_count   :1000
total_incorrect_count:0
Execute success.

iSQL> EXEC dbms_shard.unset_shard_table('u1','s1');
iSQL> EXEC dbms_shard.set_shard_table('u1','s1','r','k1','node3');
iSQL> EXEC dbms_shard.set_shard_range('u1','s1',330,'node1');
iSQL> EXEC dbms_shard.set_shard_range('u1','s1',660,'node2');

iSQL> EXEC dbms_shard.check_data('u1','s1');
shard_key_column:K1
shard_information:{"SplitMethod":"R","DefaultNode":"NODE3",  "RangeInfo":[{"Value":"330","Node":"NODE1"},{"Value":"660","Node":"NODE2"}]}
node_name:NODE1, record_count:491, correct_count:178, incorrect_count:313
node_name:NODE2, record_count:509, correct_count:181, incorrect_count:328
node_name:NODE3, record_count:0, correct_count:0, incorrect_count:0
total_record_count   :1000
total_incorrect_count:641
Execute success.
```

#### 데이터 재구축

Altibase Sharding은 샤드 키 분산 방식이 변경된 샤드 테이블에 새로운 샤드
키를 적용하여 샤드 데이터를 재분배한다. 또한 특정 데이터 노드를 지정하여
수행할 수도 있다.

##### 구문

```
DBMS_SHARD.REBUILD_DATA
DBMS_SHARD.REBUILD_DATA_NODE
```

##### 설명

샤드 키 분산 방식에 따라 데이터를 재분배한다.

##### 예제

새로운 샤드 키 분산 방식으로 분산 테이블을 재설정하였다고 가정한다.

```
iSQL> ALTER SESSION SET autocommit = false;
iSQL> ALTER SESSION SET dblink_global_transaction_level = 2;

iSQL> EXEC dbms_shard.rebuild_data('u1','s1',100);
[11:34:47] target node(1/3): "NODE1"
[11:34:47] 100 moved
[11:34:47] 200 moved
[11:34:47] 300 moved
[11:34:47] 313 moved
[11:34:47] target node(2/3): "NODE2"
[11:34:47] 100 moved
[11:34:47] 200 moved
[11:34:47] 300 moved
[11:34:47] 328 moved
[11:34:47] target node(3/3): "NODE3"
[11:34:48] done.
Execute success.

iSQL> EXEC dbms_shard.check_data('u1','s1');
shard_key_column:K1
shard_information:{"SplitMethod":"R","DefaultNode":"NODE3","RangeInfo":[{"Value":"330","Node":"NODE1"},{"Value":"660","Node":"NODE2"}]}
node_name:NODE1, record_count:330, correct_count:330, incorrect_count:0
node_name:NODE2, record_count:330, correct_count:330, incorrect_count:0
node_name:NODE3, record_count:340, correct_count:340, incorrect_count:0
total_record_count   :1000
total_incorrect_count:0
Execute success.

iSQL> COMMIT;
```

5.Altibase Sharding 패키지
------------------------

Altibase Sharding 패키지를 구성하는 프로시저와 함수에 대해 설명한다.

### DBMS_SHARD

DBMS_SHARD 패키지는 Altibase Sharding의 샤드 설정과 관리에 사용한다.

아래의 표와 같이 DBMS_SHARD 패키지를 구성하는 프로시저와 함수를 제공한다.

| 프로시저 및 함수              | 설명                                                                   |
|-------------------------------|------------------------------------------------------------------------|
| CREATE_META                   | 메타 노드에서 샤드 메타 테이블을 생성한다.                             |
| EXECUTE_IMMEDIATE             | 데이터 노드로 ad-hoc 쿼리를 수행한다.                                  |
| SET_NODE                      | 데이터 노드를 등록한다.                                                |
| RESET_NODE                    | 데이터 노드 정보를 변경한다.                                           |
| RESET_ALTERNATE_NODE          | 데이터 노드의 alternate 정보를 변경한다.                               |
| SET_SHARD_TABLE               | 샤드 테이블을 등록한다.                                                |
| SET_SHARD_TABLE_COMPOSITE     | 복합 샤드 키를 갖는 샤드 테이블을 등록한다.                            |
| SET_SHARD_PROCEDURE           | 샤드 프로시저를 등록한다.                                              |
| SET_SHARD_PROCEDURE_COMPOSITE | 복합 샤드 키를 갖는 샤드 프로시저를 등록한다.                          |
| SET_SHARD_HASH                | HASH 방식의 분산정보를 등록한다.                                       |
| SET_SHARD_RANGE               | RANGE 방식의 분산정보를 등록한다.                                      |
| SET_SHARD_LIST                | LIST 방식의 분산정보를 등록한다.                                       |
| SET_SHARD_CLONE               | CLONE 방식의 분산정보를 등록한다.                                      |
| SET_SHARD_SOLO                | SOLO 방식의 분산정보를 등록한다.                                       |
| SET_SHARD_COMPOSITE           | 복합 샤드 키 방식의 분산정보를 등록한다.                               |
| CHECK_DATA                    | 샤드 키와 데이터의 유효성을 확인한다.                                  |
| REBUILD_DATA                  | 변경된 샤드 키 분산방식에 따라 모든 데이터 노드의 데이터를 재분배한다. |
| REBUILD_DATA_NODE             | 변경된 샤드 키 분산방식에 따라 특정 데이터 노드의 데이터를 재분배한다. |
| UNSET_NODE                    | 데이터 노드를 해제한다.                                                |
| UNSET_SHARD_TABLE             | 샤드 테이블을 해제한다.                                                |
| UNSET_SHARD_TABLE_BY_ID       | shard_id로 샤드 테이블을 해제한다.                                     |
| UNSET_SHARD_PROCEDURE         | 샤드 프로시저를 해제한다.                                              |
| UNSET_SHARD_PROCEDURE_BY_ID   | shard_id로 샤드 프로시저를 해제한다.                                   |

#### CREATE_META

##### 구문

```
CREATE_META()
```

##### 설명

메타 노드에서 샤드 메타 테이블을 생성한다.

create_meta()를 수행하면 SYS_SHARD 계정이 생성되고 샤드에 메타를 저장할 테이블과
인덱스, 시퀀스가 생성된다. 이후부터 Altibase Sharding 기능을 사용할 수 있다.

##### 예제

```
iSQL> EXEC dbms_shard.create_meta();
Execute success.
```

> ##### 주의 사항
>
> -   메타 테이블을 삭제하면 샤딩을 사용할 수 없으므로 주의해야 한다.
>

#### EXECUTE_IMMEDIATE

##### 구문

```
EXECUTE_IMMEDIATE(
 query     in varchar(65534),
 node_name in varchar(40) default NULL)
```

##### 파라미터

| 이름      | 입출력 | 데이터 타입    | 설명        |
|-----------|--------|----------------|-------------|
| query     | IN     | VARCHAR(65534) | 샤드 쿼리   |
| node_name | IN     | VARCHAR(40)    | 데이터 노드 |

##### 설명

메타 노드에서 임의의 데이터 노드에 특정(ad-hoc) 쿼리를 수행한다. node_name을
지정하지 않으면, 모든 데이터 노드에 수행한다.

##### 예제

```
iSQL> EXEC dbms_shard.execute_immediate(‘TRUNCATE TABLE s1’,’node1’);
Execute success.
```

#### SET_NODE

##### 구문

```
SET_NODE(
 node_name         in varchar(40),
 host_ip           in varchar(16),
 port_no           in integer,
 alternate_host_ip in varchar(16) default NULL,
 alternate_port_no in integer default NULL)
```

##### 파라미터

| 이름              | 입출력 | 데이터 타입 | 설명                              |
|-------------------|--------|-------------|-----------------------------------|
| node_name         | IN     | VARCHAR(40) | 데이터 노드 이름                  |
| host_ip           | IN     | VARCHAR(16) | 데이터 노드의 IP                  |
| port_no           | IN     | INTEGER     | 데이터 노드의 PORT 번호           |
| alternate_host_ip | IN     | VARCHAR(16) | 데이터 노드의 Alternate IP        |
| alternate_port_no | IN     | INTEGER     | 데이터 노드의 Alternate PORT 번호 |

##### 설명

메타 노드에서 데이터 노드의 이름과 IP 및 PORT 정보와 Alternate IP 및 Alternate
Port를 설정한다.

##### 예제

```
iSQL> EXEC dbms_shard.set_node('node1','192.168.1.11',20300);
Execute success.
iSQL> EXEC dbms_shard.set_node('node2','192.168.1.12',20300);
Execute success.
iSQL> EXEC dbms_shard.set_node('node3','192.168.1.13',20300);
Execute success.
iSQL> EXEC dbms_shard.set_node('NODE3','192.168.1.23',11094,'192.168.1.24',11094);
Execute success.
```

#### RESET_ALTERNATE_NODE

##### 구문

```
RESET_ALTERNATE_NODE(node_name in varchar(40),
                     host_ip   in varchar(16),
                     port_no   in integer)
```

##### 파라미터

| 이름      | 입출력 | 데이터 타입 | 설명                       |
|-----------|--------|-------------|----------------------------|
| node_name | IN     | VARCHAR(40) | 데이터 노드 이름           |
| host_ip   | IN     | VARCHAR(16) | 데이터 노드의 Alternate IP |
| port_no   | IN     | INTEGER     | 데이터 노드의 PORT 번호    |

##### 설명

메타 노드에서 데이터 노드의 Alternate IP와 PORT정보를 변경하거나 삭제한다

##### 예제

```
iSQL> EXEC dbms_shard.reset_alternate_node('node3','192.168.1.24',11094);
Execute success.
iSQL> EXEC dbms_shard.reset_alternate_node('node3',NULL,NULL);
Execute success.
```

#### RESET_NODE

##### 구문

```
RESET_NODE(node_name in varchar(40),
           host_ip   in varchar(16),
           port_no   in integer)
```

##### 파라미터

| 이름      | 입출력 | 데이터 타입 | 설명                    |
|-----------|--------|-------------|-------------------------|
| node_name | IN     | VARCHAR(40) | 데이터 노드 이름        |
| host_ip   | IN     | VARCHAR(16) | 데이터 노드의 IP        |
| port_no   | IN     | INTEGER     | 데이터 노드의 PORT 번호 |

##### 설명

메타 노드에서 이전에 설정한 데이터 노드의 IP와 PORT 정보를 변경한다.

##### 예제

```
iSQL> EXEC dbms_shard.reset_node('node1','192.168.1.111', 20300);
Execute success.
```

#### SET_SHARD_TABLE

##### 구문

```
SET_SHARD_TABLE(
 user_name         in varchar(128),
 table_name        in varchar(128),
 split_method      in varchar(1),
 key_column_name   in varchar(128) default NULL,
 default_node_name in varchar(40) default NULL)
```

##### 파라미터

| 이름              | 입출력 | 데이터 타입  | 설명                                                                                                  |
|-------------------|--------|--------------|-------------------------------------------------------------------------------------------------------|
| user_name         | IN     | VARCHAR(128) | 테이블 소유자의 이름                                                                                  |
| table_name        | IN     | VARCHAR(128) | 테이블 이름                                                                                           |
| split_method      | IN     | VARCHAR(1)   | 분산 방식 H: 해시 분산 방식 R: 범위 분산 방식 L: 리스트 분산 방식 C: 복제 분산 방식 S: 독립 분산 방식 |
| key_column_name   | IN     | VARCHAR(128) | 샤드 키 컬럼 이름                                                                                     |
| default_node_name | IN     | VARCHAR(40)  | 기본 데이터 노드                                                                                      |

**설명**

메타 노드에 샤드 테이블 정보를 설정한다.

기본 데이터 노드란 샤드 키 분산 객체에 한해 분산 정보가 정의되지 않은 경우에
선택되는 데이터 노드를 의미하며, 지정하지 않을 수도 있다. 기본 데이터 노드를
지정하지 않을 경우, 샤드 키 분산 정보에 맞지 않는 샤드 키 값이 입력되면, 처리할
수 없으므로 에러가 발생한다.

##### 예제

```
iSQL> EXEC dbms_shard.set_shard_table('sys','t1','H','i1','node3');
Execute success.
iSQL> EXEC dbms_shard.set_shard_table('sys','t2','R','i1', 'node3');
Execute success.
iSQL> EXEC dbms_shard.set_shard_table('sys','t3','L','i1', 'node3');
Execute success.
iSQL> EXEC dbms_shard.set_shard_table('sys','t4','C');
Execute success.
iSQL> EXEC dbms_shard.set_shard_table('sys','t5','S');
Execute success.
```

> ##### 주의사항
>
> -   샤드 테이블을 설정하기 위해서는 반드시 메타 노드와 데이터 노드에 동일한
>     테이블 스키마가 생성되어야 한다.
>
> -   테이블을 제거(drop)하더라도 샤드 테이블 정보는 삭제되지 않는다.
>

#### SET_SHARD_TABLE_COMPOSITE

##### 구문

```
SET_SHARD_TABLE_COMPOSITE(
 user_name  in varchar(128),
 table_name in varchar(128),
 split_method in varchar(1),
 key_column_name in varchar(128),
 sub_split_method in varchar(1),
 sub_key_column_name in varchar(128),
 default_node_name in varchar(40) default NULL)
```

##### 파라미터

| 이름                | 입출력 | 데이터 타입  | 설명                                                                           |
|---------------------|--------|--------------|--------------------------------------------------------------------------------|
| user_name           | IN     | VARCHAR(128) | 테이블 소유자의 이름                                                           |
| table_name          | IN     | VARCHAR(128) | 테이블 이름                                                                    |
| split_method        | IN     | VARCHAR(1)   | 샤드 키 분산 방식 H: 해시 분산 방식 R: 범위 분산 방식 L: 리스트 분산 방식      |
| key_column_name     | IN     | VARCHAR(128) | 샤드 키 컬럼 이름                                                              |
| sub_split_method    | IN     | VARCHAR(1)   | 서브 샤드 키 분산 방식 H: 해시 분산 방식 R: 범위 분산 방식 L: 리스트 분산 방식 |
| sub_key_column_name | IN     | VARCHAR(128) | 서브 샤드 키 컬럼 이름                                                         |
| default_node_name   | IN     | VARCHAR(40)  | 기본 데이터 노드(default node)                                                 |

**설명**

메타 노드에서 복합 샤드 키를 적용하는 샤드 테이블의 정보를 설정한다.

##### 예제

```
iSQL> EXEC dbms_shard.set_shard_table_composite(‘sys’,’t6’,’L’,’i1’,'L','i2',’node3’);
Execute success.
```

> ##### 주의사항
>
> -   복합 샤드키를 적용한 샤드 테이블 역시 메타 노드와 데이터 노드에 동일한
>     테이블 스키마가 생성되어야 한다.
>
> -   테이블을 제거(drop)하더라도 샤드 테이블 정보는 삭제되지 않는다.
>

#### SET_SHARD_PROCEDURE

##### 구문

```
SET_SHARD_PROCEDURE(
 user_name in varchar(128),
 proc_name in varchar(128),
 split_method in varchar(1),
 key_param_name in varchar(128) default NULL,
 default_node_name in varchar(40) default NULL)

```

##### 파라미터

| 이름              | 입출력 | 데이터 타입  | 설명                                                                                                  |
|-------------------|--------|--------------|-------------------------------------------------------------------------------------------------------|
| user_name         | IN     | VARCHAR(128) | 프로시저 소유자의 이름                                                                                |
| proc_name         | IN     | VARCHAR(128) | 프로시저 이름                                                                                         |
| split_method      | IN     | VARCHAR(1)   | 분산 방식 H: 해시 분산 방식 R: 범위 분산 방식 L: 리스트 분산 방식 C: 복제 분산 방식 S: 독립 분산 방식 |
| key_param_name    | IN     | VARCHAR(128) | 샤드 키 파라미터 이름                                                                                 |
| default_node_name | IN     | VARCHAR(40)  | 기본 데이터 노드                                                                                      |

##### 설명

메타 노드에 샤드 프로시저의 정보를 설정한다.

Altibase Sharding 에서 지원하는 분산 방법의 종류는 샤드 테이블과 동일하다.

##### 예제

```
iSQL> EXEC dbms_shard.set_shard_procdure('sys','proc1','H','p1','node3');
Execute success.
iSQL> EXEC dbms_shard.set_shard_procdure('sys','proc2','R','p1','node3');
Execute success.
iSQL> EXEC dbms_shard.set_shard_procdure('sys','proc3','L','p1','node3');
Execute success.
iSQL> EXEC dbms_shard.set_shard_procdure('SYS','proc4','C');
Execute success.
iSQL> EXEC dbms_shard.set_shard_procdure('SYS','proc5','S');
Execute success.
```

> ##### 주의사항
>
> -   샤드 프로시저를 설정하기 위해서는 반드시 메타 노드와 데이터 노드에 동일한
>     프로시저가 생성되어야 한다.
>
> -   프로시저를 제거(drop)하더라도 샤드 프로시저 정보는 삭제되지 않는다.
>

#### SET_SHARD_PROCEDURE_COMPOSITE

##### 구문

```
SET_SHARD_PROCEDURE_COMPOSITE(
 user_name in varchar(128),
 proc_name in varchar(128),
 split_method in varchar(1),
 key_param_name in varchar(128) default NULL,
 sub_split_method in varchar(1),
 sub_key_param_name in varchar(128) default NULL,
 default_node_name in varchar(40) default NULL)
```

##### 파라미터

| 이름               | 입출력 | 데이터 타입  | 설명                                                                                    |
|--------------------|--------|--------------|-----------------------------------------------------------------------------------------|
| user_name          | IN     | VARCHAR(128) | 프로시저 소유자의 이름                                                                  |
| proc_name          | IN     | VARCHAR(128) | 프로시저 이름                                                                           |
| split_method       | IN     | VARCHAR(1)   | 샤드 키 파라미터 분산 방식 H: 해시 분산 방식 R: 범위 분산 방식 L: 리스트 분산 방식      |
| key_param_name     | IN     | VARCHAR(128) | 샤드 키 파라미터 이름                                                                   |
| sub_split_method   | IN     | VARCHAR(1)   | 서브 샤드 키 파라미터 분산 방식 H: 해시 분산 방식 R: 범위 분산 방식 L: 리스트 분산 방식 |
| sub_key_param_name | IN     | VARCHAR(128) | 서브 샤드 키 파라미터 이름                                                              |
| default_node_name  | IN     | VARCHAR(40)  | 기본 데이터 노드(default node)                                                          |

##### 설명

메타 노드에 복합 샤드 키를 적용하는 샤드 프로시저의 정보를 설정한다.

Altibase Sharding에서 지원하는 분산 방법의 종류는 샤드 테이블과 동일하다.

##### 예제

```
iSQL> EXEC dbms_shard.set_shard_procdure_composite('sys','proc6','L','p1', 'L','p2','node3');
Execute success.
```

> ##### 주의사항
>
> -   복합 샤드 키 프로시저를 설정하기 위해서는 반드시 메타 노드와 데이터 노드에
>     동일한 프로시저가 생성되어야 한다.
>
> -   프로시저를 제거(drop)하더라도 샤드 프로시저 정보는 삭제되지 않는다.
>

#### SET_SHARD_HASH

##### 구문

```
SET_SHARD_HASH(    user_name in varchar(128),
                   object_name in varchar(128),
                   hash_max in integer,
                   node_name in varchar(40))
```

##### 파라미터

| 이름        | 입출력 | 데이터 타입  | 설명                         |
|-------------|--------|--------------|------------------------------|
| user_name   | IN     | VARCHAR(128) | 객체 소유자의 이름           |
| object_name | IN     | VARCHAR(128) | 객체 이름                    |
| hash_max    | IN     | INTEGER      | 해시 분산의 샤드 키의 최대값 |
| node_name   | IN     | VARCHAR(40)  | 기본 데이터 노드             |

##### 설명

메타 노드에 해시 방식으로 분산되는 샤드 객체의 정보를 설정한다. 해시 값은 [ 1 \~
1000 ]으로 정의한다.

구간별로 데이터 노드를 적절하게 지정해야 하며, 만약 지정하지 않을 경우 기본
데이터 노드로 데이터가 분산된다.

##### 예제

\<질의\> sys.t1 테이블에 샤드 키의 hash 값에 따라 데이터가 다음과 같이 분산된다.

-   1\~300은 node1으로 분산

-   301 \~ 600은 node2로 분산

-   나머지 hash 값은 기본 데이터 노드로 분산

```
iSQL> EXEC dbms_shard.set_shard_hash('sys','t1',500,'node1');
Execute success.
iSQL> EXEC dbms_shard.set_shard_hash('sys','t1',1000,'node2');
Execute success.
```

#### SET_SHARD_RANGE

##### 구문

```
SET_SHARD_RANGE(     user_name    in  varchar(128),
                     object_name  in  varchar(128),
                     value_max    in  varchar(100),
                     node_name    in  varchar(40))
```

##### 파라미터

| 이름        | 입출력 | 데이터 타입  | 설명                         |
|-------------|--------|--------------|------------------------------|
| user_name   | IN     | VARCHAR(128) | 객체 소유자의 이름           |
| object_name | IN     | VARCHAR(128) | 객체 이름                    |
| value_max   | IN     | VARCHAR(100) | 범위 분산의 샤드 키의 최대값 |
| node_name   | IN     | VARCHAR(40)  | 기본 데이터 노드             |

##### 설명

메타 노드에 범위 분산 방식으로 샤드 객체의 분산 정보를 설정한다.

##### 예제

```
iSQL> EXEC dbms_shard.set_shard_range('sys','t2',300,'node1');
Execute success.
iSQL> EXEC dbms_shard.set_shard_range('sys','t2',600,'node2');
Execute success. 
```

#### SET_SHARD_LIST

##### 구문

```
SET_SHARD_LIST(    user_name    in  varchar(128),
                   object_name  in  varchar(128),
                   value        in  varchar(100),
                   node_name    in  varchar(40))
```

##### 파라미터

| 이름        | 입출력 | 데이터 타입  | 설명                           |
|-------------|--------|--------------|--------------------------------|
| user_name   | IN     | VARCHAR(128) | 객체 소유자의 이름             |
| object_name | IN     | VARCHAR(128) | 객체 이름                      |
| value       | IN     | VARCHAR(100) | 리스트 분산의 샤드 키의 최대값 |
| node_name   | IN     | VARCHAR(40)  | 기본 데이터 노드               |

##### 설명

메타 노드에 리스트 분산 방식의 샤드 객체에 대한 분산 정보를 설정한다.

##### 예제

```
iSQL> EXEC dbms_shard.set_shard_list('sys','t3','1a','node1');
Execute success.
iSQL> EXEC dbms_shard.set_shard_list('sys','t3','2a','node2');
Execute success.
iSQL> EXEC dbms_shard.set_shard_list('sys','t3','3a','node3');
Execute success.
```

#### SET_SHARD_COMPOSITE

##### 구문

```
SET_SHARD_COMPOSITE(
 user_name    in  varchar(128),
 object_name  in  varchar(128),
 value        in  varchar(100),
 sub_value    in  varchar(100),
 node_name    in  varchar(40))
```

##### 파라미터

| 이름        | 입출력 | 데이터 타입  | 설명                  |
|-------------|--------|--------------|-----------------------|
| user_name   | IN     | VARCHAR(128) | 객체 소유자의 이름    |
| object_name | IN     | VARCHAR(128) | 객체 이름             |
| value       | IN     | VARCHAR(100) | 샤드 키의 최대값      |
| sub_value   | IN     | VARCHAR(100) | 서브 샤드 키의 최대값 |
| node_name   | IN     | VARCHAR(40)  | 기본 데이터 노드      |

##### 설명

메타 노드에 복합 샤드 키를 적용한 샤드 객체의 분산 정보를 설정한다.

##### 예제

```
iSQL> EXEC dbms_shard.set_shard_composite('sys','t6','서울','강남구','node1');
Execute success.
iSQL> EXEC dbms_shard.set_shard_composite('sys','t6','서울','강북구','node2');
Execute success.
iSQL> EXEC dbms_shard.set_shard_composite('sys','t6','서울','강서구','node3');
Execute success.

iSQL> EXEC dbms_shard.set_shard_composite('sys','proc6','서울','강남구','node1');
Execute success.
iSQL> EXEC dbms_shard.set_shard_composite('sys','proc6','서울','강북구','node2');
Execute success.
iSQL> EXEC dbms_shard.set_shard_composite('sys','proc6','서울','강서구','node3');
Execute success
```

#### SET_SHARD_CLONE

##### 구문

```
SET_SHARD_CLONE(    user_name    in  varchar(128),
                    object_name  in  varchar(128),
                    node_name    in  varchar(40))
```

##### 파라미터

| 이름        | 입출력 | 데이터 타입  | 설명               |
|-------------|--------|--------------|--------------------|
| user_name   | IN     | VARCHAR(128) | 객체 소유자의 이름 |
| object_name | IN     | VARCHAR(128) | 객체 이름          |
| node_name   | IN     | VARCHAR(40)  | 데이터 노드        |

##### 설명

메타 노드에 복제 분산 방식으로 샤드 객체의 분산 정보를 설정한다.

##### 예제

```
iSQL> EXEC dbms_shard.set_shard_clone('sys','t4','node1');
Execute success.
iSQL> EXEC dbms_shard.set_shard_clone('sys','t4','node2');
Execute success.
iSQL> EXEC dbms_shard.set_shard_clone('sys','t4','node3');
```

#### SET_SHARD_SOLO

##### 구문

```
SET_SHARD_SOLO(    user_name    in  varchar(128),
                   object_name  in  varchar(128),
                   node_name    in  varchar(40))
```

##### 파라미터

| 이름        | 입출력 | 데이터 타입  | 설명               |
|-------------|--------|--------------|--------------------|
| user_name   | IN     | VARCHAR(128) | 객체 소유자의 이름 |
| object_name | IN     | VARCHAR(128) | 객체 이름          |
| node_name   | IN     | VARCHAR(40)  | 데이터 노드        |

##### 설명

메타 노드에 독립 분산 방식의 샤드 객체의 분산 정보를 설정한다.

##### 예제

```
iSQL> EXEC dbms_shard.set_shard_solo('sys','t5','node1');
Execute success.
iSQL> EXEC dbms_shard.set_shard_solo('sys','proc5','node1');
Execute success.
```

#### CHECK_DATA

##### 구문

```
CHECK_DATA(user_name            in  varchar(128),
           table_name           in  varchar(128),
           additional_node_list in varchar(1000) default null)
```

##### 파라미터

| 이름                 | 입출력 | 데이터 타입   | 설명                               |
|----------------------|--------|---------------|------------------------------------|
| user_name            | IN     | VARCHAR(128)  | 테이블 소유자의 이름               |
| table_name           | IN     | VARCHAR(128)  | 테이블 이름                        |
| additional_node_list | IN     | VARCHAR(1000) | 데이터 노드의 이름 (기본값 : null) |

##### 설명

샤드 테이블의 샤드 키와 데이터의 유효성을 확인한다.

additional_node_list는 테이블의 분산 정의에 등록되지 않은 데이터 노드의 정보를
확인한다. 데이터 노드의 이름은 쉼표(,)로 구분하여 나열한다.

##### 예제

```
iSQL> EXEC dbms_shard.check_data('sys','t1');
shard_key_column:I1
shard_information:{"SplitMethod":"H","RangeInfo":[{"Value":"500","Node":"NODE1"},{"Value":"1000","Node":"NODE2"}]}
node_name:NODE1, record_count:491, correct_count:491, incorrect_count:0
node_name:NODE2, record_count:509, correct_count:509, incorrect_count:0
total_record_count   :1000
total_incorrect_count:0
Execute success.
```

node1\~node4로 분산한 t1 테이블을 노드 node1\~node2로 재설정한 후 node3, node4를
포함한 정보까지 확인할 수 있는 예제이다.

```
iSQL> EXEC dbms_shard.check_data('sys','t1','node3, node4');
shard_key_column:I1
shard_information:{"SplitMethod":"H","RangeInfo":[{"Value":"500","Node":"NODE1"},{"Value":"1000","Node":"NODE2"}]}
node_name:NODE1, record_count:491, correct_count:491, incorrect_count:0
node_name:NODE2, record_count:509, correct_count:509, incorrect_count:0
node_name:NODE3, record_count:100, correct_count:0, incorrect_count:100
node_name:NODE4, record_count:100, correct_count:0, incorrect_count:100
total_record_count   :1000
total_incorrect_count:200
Execute success.
```

> ##### 주의사항
>
> 복합 샤드 키를 포함한 샤드 키 테이블에 한해 적용된다.
>

#### REBUILD_DATA

##### 구문

```
REBUILD_DATA(user_name            in  varchar(128),
             table_name           in  varchar(128),
             batch_count          in bigint default 0,
             additional_node_list in varchar(1000) default null)
```

##### 파라미터

| 이름                 | 입출력 | 데이터 타입   | 설명                                   |
|----------------------|--------|---------------|----------------------------------------|
| user_name            | IN     | VARCHAR(128)  | 테이블 소유자의 이름                   |
| table_name           | IN     | VARCHAR(128)  | 테이블 이름                            |
| batch_count          | IN     | BIGINT        | 일괄 처리 행의 단위 (기본값 : 전체 행) |
| additional_node_list | IN     | VARCHAR(1000) | 데이터 노드의 이름 (기본값 : null)     |

##### 설명

모든 데이터 노드의 데이터를 변경된 샤드 키 분산 방식으로 재분배한다.

additional_node_list는 테이블의 분산 정의에 등록되지 않은 데이터 노드를 포함하여
데이터를 재분배한다. 데이터 노드의 이름은 쉼표(,)로 구분하여 나열한다.

##### 예제

```
iSQL> EXEC dbms_shard.unset_shard_table('sys','t1');
iSQL> EXEC dbms_shard.set_shard_table('sys','t1','R','i1','node3');
iSQL> EXEC dbms_shard.set_shard_range('sys','t1',330,'node1');
iSQL> EXEC dbms_shard.set_shard_range('sys','t1',660,'node2');
iSQL> EXEC dbms_shard.check_data('sys','t1');
shard_key_column:I1
shard_information:{"SplitMethod":"R", "DefaultNode":"NODE3", "RangeInfo":[{"Value":"330","Node":"NODE1"}, {"Value":"660","Node":"NODE2"}]}
node_name:NODE1, record_count:491, correct_count:178, incorrect_count:313
node_name:NODE2, record_count:509, correct_count:181, incorrect_count:328
node_name:NODE3, record_count:0, correct_count:0, incorrect_count:0
total_record_count   :1000
total_incorrect_count:641
Execute success.

iSQL> ALTER SESSION SET dblink_global_transaction_level = 2;
iSQL> ALTER SESSION SET autocommit = false;

iSQL> EXEC dbms_shard.rebuild_data('sys','t1',100);
[11:34:47] target node(1/3): "NODE1"
[11:34:47] 100 moved
[11:34:47] 200 moved
[11:34:47] 300 moved
[11:34:47] 313 moved
[11:34:47] target node(2/3): "NODE2"
[11:34:47] 100 moved
[11:34:47] 200 moved
[11:34:47] 300 moved
[11:34:47] 328 moved
[11:34:47] target node(3/3): "NODE3"
[11:34:48] done.
Execute success.

iSQL> EXEC dbms_shard.check_data('sys','t1');
shard_key_column:I1
shard_information:{"SplitMethod":"R","DefaultNode":"NODE3","RangeInfo":[{"Value":"330","Node":"NODE1"},{"Value":"660","Node":"NODE2"}]}
node_name:NODE1, record_count:330, correct_count:330, incorrect_count:0
node_name:NODE2, record_count:330, correct_count:330, incorrect_count:0
node_name:NODE3, record_count:340, correct_count:340, incorrect_count:0
total_record_count   :1000
total_incorrect_count:0
Execute success.
iSQL> COMMIT; 

iSQL> EXEC dbms_shard.rebuild_data('sys','t1',1000,'node3');
[17:33:02] target node(1/3): "NODE1"
[17:33:02] target node(2/3): "NODE2"
[17:33:02] 1000 moved
[17:33:02] 2000 moved
[17:33:02] 3000 moved
...
[17:33:02] 16000 moved
[17:33:02] 16617 moved
[17:33:02] target node(3/3): "NODE3"
[17:33:02] 1000 moved
[17:33:03] 2000 moved
[17:33:03] 3000 moved
[17:33:03] 4000 moved
...
[17:33:04] 33000 moved
[17:33:04] 33381 moved
[17:33:04] done.
Execute success.
```

> ##### 주의사항
>
> -   복합 샤드 키를 포함한 샤드 키 테이블에 한해 적용된다.
>
> -   기존의 샤드 분산 테이블을 해제하고 새로운 분산방식을 적용한 후, 이
>     프로시저를 수행해야 한다.
>
> -   Global transaction , Non-autocommit 모드에서 수행하여야 정합성이 보장된다.
>

#### REBUILD_DATA_NODE

##### 구문

```
REBUILD_DATA_NODE(user_name  in  varchar(128),
                 table_name  in varchar(128),
                 node_name   in varchar(40),
                 batch_count in bigint default 0)
```

##### 파라미터

| 이름        | 입출력 | 데이터 타입  | 설명                             |
|-------------|--------|--------------|----------------------------------|
| user_name   | IN     | VARCHAR(128) | 테이블 소유자의 이름             |
| table_name  | IN     | VARCHAR(128) | 테이블 이름                      |
| node_name   | IN     | VARCHAR(40)  | 데이터 노드 이름                 |
| batch_count | IN     | BIGINT       | 일괄 처리 행의 단위 (기본값 : 0) |

##### 설명

변경된 샤드 키 분산방식에 따라 특정 데이터 노드의 데이터를 재분배한다.

##### 예제

```
iSQL> EXEC dbms_shard.unset_shard_table('sys', 't1');
iSQL> EXEC dbms_shard.set_shard_table('sys','t1','R','i1','node3');
iSQL> EXEC dbms_shard.set_shard_range('sys','t1',330,'node1');
iSQL> EXEC dbms_shard.set_shard_range('sys','t1',500,'node2');

iSQL> EXEC dbms_shard.check_data('sys','t1');
shard_key_column:I1
shard_information:{"SplitMethod":"R","DefaultNode":"NODE3","RangeInfo":[{"Value":"330","Node":"NODE1"},{"Value":"500","Node":"NODE2"}]}
node_name:NODE1, record_count:330, correct_count:330, incorrect_count:0
node_name:NODE2, record_count:330, correct_count:170, incorrect_count:160
node_name:NODE3, record_count:340, correct_count:340, incorrect_count:0
total_record_count   :1000
total_incorrect_count:160
Execute success.

iSQL> ALTER SESSION SET dblink_global_transaction_level = 2;
iSQL> ALTER SESSION SET autocommit = false;

iSQL> EXEC dbms_shard.rebuild_data_node('sys','t1','node2',100);
[14:12:25] 100 moved
[14:12:25] 160 moved
Execute success.

iSQL> EXEC dbms_shard.check_data('sys','t1');
shard_key_column:I1
shard_information:{"SplitMethod":"R","DefaultNode":"NODE3","RangeInfo":[{"Value":"330","Node":"NODE1"},{"Value":"500","Node":"NODE2"}]}
node_name:NODE1, record_count:330, correct_count:330, incorrect_count:0
node_name:NODE2, record_count:170, correct_count:170, incorrect_count:0
node_name:NODE3, record_count:500, correct_count:500, incorrect_count:0
total_record_count   :1000
total_incorrect_count:0
Execute success.

iSQL> COMMIT;
```

> ##### 주의사항
>
> REBUILD_DATA 와 동일하다.
>

#### UNSET_NODE

##### 구문

```
UNSET_NODE(node_name in varchar(40))
```

##### 파라미터

| 이름      | 입출력 | 데이터 타입 | 설명        |
|-----------|--------|-------------|-------------|
| node_name | IN     | VARCHAR(40) | 데이터 노드 |

##### 설명

메타 노드에서 이전에 설정한 데이터 노드 정보를 삭제한다.

##### 예제

```
iSQL> EXEC dbms_shard.unset_node('node1');
Execute success.
```

#### UNSET_SHARD_TABLE

##### 구문

```
UNSET_SHARD_TABLE(     user_name  in varchar(128),
                       table_name in varchar(128))
```

##### 파라미터

| 이름       | 입출력 | 데이터 타입  | 설명                 |
|------------|--------|--------------|----------------------|
| user_name  | IN     | VARCHAR(128) | 테이블 소유자의 이름 |
| table_name | IN     | VARCHAR(128) | 테이블 이름          |

##### 설명

메타 노드에서 샤드 테이블의 정보를 삭제한다.

UNSET_SHARD_TABLE() 함수를 사용하여 샤드 테이블 정보를 삭제하면, 분산 정보도
모두 삭제된다.

##### 예제

```
iSQL> EXEC dbms_shard.unset_shard_table('sys','t5');
Execute success.
```

#### UNSET_SHARD_TABLE_BY_ID

##### 구문

```
UNSET_SHARD_TABLE_BY_ID(shard_id in integer)
```

##### 파라미터

| 이름     | 입출력 | 데이터 타입 | 설명           |
|----------|--------|-------------|----------------|
| shard_id | IN     | INTEGER     | 샤드 객체 번호 |

##### 설명

메타 노드에서 샤드 테이블의 정보를 삭제한다.

UNSET_SHARD_TABLE_BY_ID() 함수를 사용하여 샤드 테이블 정보를 삭제하면, 분산
정보도 모두 삭제된다.

삭제된 shard_id는 sys_shard.objects_에서 조회할 수 있다.

##### 예제

```
iSQL> EXEC dbms_shard.unset_shard_table_by_id(123);
Execute success.
```

#### UNSET_SHARD_PROCEDURE

##### 구문

```
UNSET_SHARD_PROCEDURE(
  user_name in varchar(128),
  proc_name in varchar(128))
```

##### 파라미터

| 이름      | 입출력 | 데이터 타입  | 설명                   |
|-----------|--------|--------------|------------------------|
| user_name | IN     | VARCHAR(128) | 프로시저 소유자의 이름 |
| proc_name | IN     | VARCHAR(128) | 프로시저 이름          |

##### 설명

메타 노드에서 샤드 프로시저의 정보를 삭제한다.

UNSET_SHARD_PROCEDURE() 함수를 사용하여 샤드 프로시저 정보를 삭제하면, 분산
정보도 모두 삭제된다.

##### 예제

```
iSQL> EXEC dbms_shard.unset_shard_procedure('sys','proc1');
Execute success.
```

#### UNSET_SHARD_PROCEDURE_BY_ID

##### 구문

```
UNSET_SHARD_PROCEDURE_BY_ID(
	shard_id in integer)
```

##### 파라미터

| 이름     | 입출력 | 데이터 타입 | 설명           |
|----------|--------|-------------|----------------|
| shard_id | IN     | INTEGER     | 샤드 객체 번호 |

##### 설명

메타 노드에서 샤드 프로시저의 정보를 삭제한다.

UNSET_SHARD_PROCEDURE_BY_ID() 함수를 사용하여 샤드 테이블 정보를 삭제하면, 각
분산 방식 때 정의했던 분산 정보도 모두 삭제된다.

샤드 메타를 삭제할 shard_id 는 sys_shard.objects_에서 조회할 수 있다.

##### 예제

```
iSQL> EXEC dbms_shard.unset_shard_procedure_by_id(123);
Execute success. 
```

6.Altibase Sharding 유틸리티
--------------------------

이 장에서는 Altibase Sharding에서 지원하는 유틸리티를 설명한다.

Altibase Sharding에서 지원하는 유틸리티는 다음과 같다.

-   shardLoader

-   Shard Manager

### shardLoader

shardLoader는 iloader와 기능이 동일하다. 데이터 노드에 직접 접속하여 데이터를
처리하므로 빠른 데이터 적재가 가능하다. shardLoader는 데이터 마이그레이션과
데이터 재분배에 사용할 수 있다.

#### 설치 방법

shardLoader는 Altibase 패키지를 설치할 때 자동으로 설치된다. 실행 파일의 위치는
다음과 같다.

```
$ALTIBASE_HOME/bin
```

#### shardLoader 설정

iLoader와 동일하다. 사용방법은 “*iLoader User's Manual \> 1. iLoader 개요 \>
iLoader의 소개 \> iLoader 설정”*을 참조한다.

#### 명령행 옵션

iLoader와 동일하다. 사용방법은 *iLoader User's Manual \> 2. iLoader 사용 방법 \>
명령행 옵션”*을 참조한다.

> #### 주의사항
>
> shardLoader는 lob 컬럼, array 등 몇 가지 옵션을 제공하지 않는다. 해당 기능을
> 사용하기 위해서는 각 데이터 노드 별로 iLoader를 사용해야 한다.

### Shard Manager

#### 개요

Shard Manager는 Altibase Sharding의 데이터 노드와 샤드 객체에 대한 구성 및
관리를 돕는 도구이다.

Altibase Sharding은 다수의 데이터베이스로 구성되기 때문에, 각 데이터베이스와
객체를 관리하는 비용이 많이 들 수 있다. 이러한 환경에서 관리자는 Shard Manager를
사용함으로써 여러 데이터베이스에서 수행해야 하는 반복 작업을 단순화하여 업무
효율성을 향상시키고, 데이터 노드와 샤드 객체를 시각화하여 구성에 대한 이해도를
증진시킬 수 있다.

#### 특징

Shard Manager의 특징은 다음과 같다.

-   데이터 노드를 손쉽게 등록/수정/해제할 수 있다.

-   객체를 샤드 객체로 손쉽게 등록/해제할 수 있다.

-   여러 노드에 걸쳐 존재하는 분산 객체의 개별 정보 및 분산 정보를 하나의 창에서
    확인할 수 있다.

-   한 메타 노드와 이에 등록된 데이터 노드들에 대해, SQL을 메타 노드/데이터
    노드/alternate 데이터 노드 단위로 한 번에 수행할 수 있다.

-   데이터 노드와 샤드 객체의 유효성을 검사하여 구조적 결함 정보를 제공한다.

-   샤드 테이블의 데이터 유효성을 확인하고, 자동 데이터 재구축을 수행할 수 있다.

#### 설치

이 절에서는 Shard Manager를 설치할 때 필요한 환경과 선행 조건, 그리고 설치 및
제거 방법을 안내한다.

##### 시스템 요구사항

Shard Manager는 아래와 같은 환경에서 설치 및 실행이 가능하다.

Linux용 Shard Manager는 JRE를 포함하지 않는다. 따라서 사용자가 실행 환경에
적합한 버전의 JRE를 설치해야 한다.

운영체제별 자세한 지원 사항은 다음의 링크된 페이지에서 확인할 수
있다( [http://www.eclipse.org/projects/project-plan.php?projectid=eclipse\#target_environments](http://www.eclipse.org/projects/project-plan.php?projectid=eclipse%23target_environments) ).

| 리소스                        | 최소 요구사항               |
|-------------------------------|-----------------------------|
| OS                            | Windows 32 bit Linux 64 bit |
| 메모리                        | 512 MB                      |
| Java Runtime Environment(JRE) | JRE Version 5               |
| 디스크 공간                   | 90 MB                       |
| 화면 해상도                   | 1024 \* 786 pixels          |
| CPU                           | Pentium III 800MHz          |

##### 호환가능 데이터베이스

Shard Manager와 호환가능한 데이터베이스는 아래와 같다.

-   Altibase Sharding 2.0 이상 버전을 지원한다.

-   메타 노드의 경우, 샤드 메타가 생성되어있어야 한다.

샤드 메타 생성에 대한 자세한 내용은 '*샤드 메타 생성'*을 참조한다.

##### 설치와 제거

제공된 압축(zip) 파일을 원하는 위치에 해제하면 Shard Manager 설치가 완료된다.
Shard Manager를 제거하기 위해서는 설치 시 생성한 Shard Manager 디렉토리를
삭제하면 제거가 완료된다.

#### 사용자 인터페이스

아래는 Shard Manager를 최초로 실행한 화면이다.

화면에서 빈 공간은 샤드 데이터베이스 뷰, 샤드 객체 뷰에 따라 다른 뷰(쿼리 뷰,
상세 뷰, 레코드 카운트 뷰, 메모리 테이블스페이스 사용률 뷰)를 보여준다.

![](media/Sharding/2adbdfe24edb1745d768c92b0b9813d2.jpg)

##### 샤드 데이터베이스 뷰

샤드 데이터베이스 뷰는 메타 노드와 종속된 데이터 노드를 하나의 그룹으로 표현하는
샤드 데이터베이스를 중심으로 샤드 정보를 보여준다. 기본 전체 화면의 왼쪽 상단에
위치한다.

샤드 데이터베이스 뷰에서 표현하는 정보는 3가지이다.

1.  샤드 데이터베이스: 사용자가 등록한 메타 노드와 그의 데이터 노드를 하나의
    그룹으로 나타낸다. 메타 노드로 접속을 성공하면, 샤드 데이터베이스는 메타
    노드로부터 데이터 노드의 정보를 가져와 트리 구조의 하위 노드로 표현한다.

![](media/Sharding/895a3cd4060bcf09e7c5e0642ad7e5ac.jpg)

2. 데이터 노드: 메타 노드에 등록된 데이터 노드이다. 하위 노드로 데이터 노드의
   연결 정보를 보여준다.

3. 데이터 노드의 연결정보: 메타 노드에 등록된 데이터 노드의 연결 정보이다.

![](media/Sharding/83b991eb082ed678de6996afa963d0dd.png)

**Label Expression**

-   샤드 데이터베이스: 샤드 데이터베이스 추가 시 사용자가 부여한 이름

-   데이터 노드: 메타 노드에 등록된 데이터 노드 이름

-   데이터 노드의 연결정보: IP 주소 : 포트 번호

**Icon Expression**

-   샤드 데이터베이스: 메타 노드에 성공적으로 접속하면 아이콘 오른쪽 하단에
    초록색 화살표를 표시한다.

-   데이터 노드의 연결정보: 원형 아이콘은 접속 성공 시 초록색, 실패 시
    빨간색으로 표시된다. 해당 연결 정보가 데이터 노드의 alternate이면 아이콘
    오른쪽 하단에 'A' 문자를 표시한다.

##### 샤드 객체 뷰

샤드 객체 뷰는 샤드 데이터베이스 뷰에서 선택된 샤드 데이터베이스에 속한 샤드
객체를 보여준다. 기본 전체화면의 왼쪽 하단에 위치한다.

각각의 객체는 객체 종류에 따라 'Procedures', 'Tables'의 트리 하위 노드로
표현된다.

-   프로시저: 샤드 메타에 등록된 샤드 프로시저이다.

-   프로시저 파라미터: 샤드 프로시저에서 샤드 키 또는 서브 샤드 키로 사용되는
    파라미터 정보테이블: 샤드 메타에 등록된 샤드 테이블이다.

-   테이블 컬럼: 샤드 테이블에서 샤드 키 또는 서브 샤드 키로 사용되는 컬럼 정보

![](media/Sharding/02d3bc710e2980772cbf5db795c0394c.jpg)

**Label Expression**

-   프로시저, 테이블: 사용자 이름.객체 이름

-   프로시저 파라미터: 프로시저 파라미터 이름 [데이터 타입]

-   테이블 컬럼: 테이블 컬럼 이름 [데이터 타입]

**Icon Expression**

-   프로시저 파라미터: 파라미터 타입에 따라 IN은 오른쪽, OUT은 왼쪽, IN OUT은
    양쪽 화살표 아이콘을 표시한다. 열쇠 그림 위의 숫자가 1이면 샤드 키, 2이면
    서브 샤드 키를 의미한다.

-   테이블 컬럼: 열쇠 그림 위의 숫자가 1이면 샤드 키, 2이면 서브 샤드 키를
    의미한다.

**칼럼 설명**

-   Name: 샤드 객체의 이름을 표시한다.

-   Split Method: 샤드 객체의 분산 방식을 표시한다.

**샤드 객체 뷰 툴바**

-   Add New Shard Object(![](media/Sharding/e74a11e0f77d2845b3ca5b8cd59e27e9.png)): 샤드 객체를 추가한다.

-   Rebuild Shard Table(![](media/Sharding/58646a62a61346f627ee5b1a1e1cd20a.png)): 샤드 테이블의 데이터 유효성을 확인하고, 자동 데이터 재구축을 수행한다.


##### 쿼리 뷰

쿼리 뷰는 사용자가 입력한 쿼리를 메타 노드와 데이터 노드, alternate 데이터
노드를 대상으로 수행하는 뷰이다.

샤드 데이터베이스를 연결할 때 자동으로 뷰가 나타나며, 대상 데이터베이스의 이름이
뷰의 제목으로 사용된다. 사용자가 쿼리 뷰를 열 때에는 샤드 데이터베이스 뷰에서
샤드 데이터베이스를 마우스 오른쪽 버튼을 누르거나 선택 후, Database 메뉴를 열어
'Open Query View'를 선택하면 생성된다. 기본 전체 화면 오른쪽 상단에 위치한다.

![](media/Sharding/c02b451a2bfb0ce232cad41d8acf3aa7.jpg)

##### 쿼리 뷰 툴바

-   Execute Statement (![](media/Sharding/de1f28e5e2b6fb8d2d6484ef3772e3e9.png)): 커서로 선택한 문자 블록 또는 해당 커서가 위치한 라인이 수행된다.

-   Execute Script (![](media/Sharding/436ca8084a13745802c439308c90c757.png)): 쿼리 뷰에 입력한 모든 SQL문이 수행된다.


사용자가 선택한 체크박스에 따라 메타 노드, 데이터 노드, alternate 데이터 노드를
대상으로 쿼리를 수행하며, 쿼리 수행 결과는 콘솔 뷰에 출력된다. 사용자는 쿼리
뷰에 다수의 SQL문을 입력할 수 있으며, 일부 또는 전체 SQL문을 선택하여 수행할 수
있다. SQL문은 사용자가 노드에 입력한 순서대로 수행된다.

##### 상세 뷰

상세 뷰는 특정 객체에 대해 각 노드에 저장된 해당 객체의 상세 정보와 메타 노드에
등록된 분산 정보를 보여준다. 대상 객체의 사용자 이름과 객체 이름이 개별 뷰의
제목으로 쓰인다. 샤드 객체 뷰에서 객체를 마우스 오른쪽 버튼으로 누르거나, 선택
후 Shard Object 메뉴를 열어 'Show Detail'을 선택하면 생성되며, 기본 전체화면의
오른쪽 상단에 위치한다.

상세 뷰는 샤드 객체의 정보를 'Detail'과 'Shard Info'라는 탭으로 분류하여
보여준다.

-   Detail: 각 노드에 저장된 객체의 상세 정보를 보여준다.

-   Shard Info: 대상 객체가 샤드 객체인 경우, 메타 노드에 등록된 분산 정보를
    보여준다.

![](media/Sharding/19423b77d3af3797a350474dd26c254c.png)

-   Owner Databases: 샤드 객체 뷰에서 선택된 객체와 동일한 스키마 이름과 객체
    이름을 가진 객체가 저장되어 있는 데이터베이스 리스트를 보여준다. (Label
    Expression: '데이터 노드 이름 (IP 주소 : 포트 번호)' or '샤드 데이터베이스
    이름-Meta Node')

-   Owner Databases에서 선택된 데이터베이스에 존재하는 분산 객체의 정보는 오른쪽
    화면에 탭 형식으로 분류하여 나타낸다. 샤드 테이블의 경우 'Properties',
    'Columns', 'Constraints'로 분류하고, 샤드 프로시저의 경우 'Properties',
    'Parameters', 'Code'로 분류한다.

![](media/Sharding/5f0510dd9b4f32fe8bf5922b1350c1ff.png)

-   Shard Information: 분산 방식과 샤드 키, 서브 샤드 키, 기본 노드를 보여준다.

-   Key Values: 선택한 샤드 객체가 분산된 데이터 노드의 이름과 샤드 키 값, 서브
    샤드 키의 값을 보여준다.

##### 메모리 테이블스페이스 사용률 뷰

메모리 테이블스페이스 사용률 뷰는 데이터 노드와 alternate 데이터 노드의 메모리
테이블스페이스 사용률을 보여준다. 접속한 데이터베이스를 마우스 오른쪽 버튼으로
누르거나, 선택 후 Database 메뉴를 열어 'Show Memory Tablespace Usage'를 클릭하면
생성된다. 생성 시 기본 전체화면 오른쪽 상단에 위치한다.

![](media/Sharding/c73e5de5c48796615e9d18100eb9af84.png)

**칼럼 설명**

-   Database: 데이터 노드의 연결정보로 접속한 데이터베이스(Label Expression:
    '데이터 노드 이름 (IP 주소 : 포트 번호)' or '샤드 데이터베이스 이름-Meta
    Node')

-   Tablespace Name: 메모리 테이블스페이스 이름, 노드에 존재하는 메모리
    테이블스페이스가 다수일 경우, 선택할 수 있다.

-   Max(MB): 메모리 테이블스페이스에서 사용할 수 있는 최대 메모리 크기,
    테이블스페이스 생성 시 최대 크기를 지정하지 않았다면 MEM_MAX_DB_SIZE
    프로퍼티에 지정된 크기를, AUTOEXTEND가 OFF라면 메모리 테이블스페이스가
    할당받은 크기를 출력한다.

-   Alloc(MB): 메모리 테이블스페이스에 할당된 메모리 크기

-   Used(MB): 'Alloc(MB)'의 값 중, 실제 사용하는 메모리 크기

-   Usage(%): 메모리 테이블스페이스 사용률 (= Alloc(MB) / Max(MB) \* 100)

##### 레코드 카운트 뷰

샤드 테이블의 레코드는 여러 데이터 노드에 분산되어 저장된다. 레코드 카운트 뷰는
각 데이터 노드의 분산 테이블에 저장된 레코드 개수를 표시한다. 샤드 객체 뷰에서
테이블을 마우스 오른쪽 버튼으로 누르거나, 선택 후 'Shard Object' 메뉴에서 'Show
Record Count'를 클릭하면 생성된다. 기본 전체화면의 오른쪽 상단에 위치한다.

![](media/Sharding/7a1740e78fa9f887b87a3342c279c503.png)

![](media/Sharding/8e66d1223f1450ce01e943d227ec6fe5.png)

**칼럼 설명**

-   Data Node: 메타 노드가 가진 데이터 노드의 이름

-   Address: 데이터 노드의 연결정보, alternate 데이터 노드가 존재할 경우,
    연결정보를 선택할 수 있다. (Label Expression: 'IP 주소 : 포트 번호')

-   Record Count: Data Node와 Address 컬럼에서 선택된 데이터베이스에 저장된
    테이블의 레코드 개수

##### 콘솔 뷰

프로그램 수행 중 사용자에게 전달할 정보가 기록되는 뷰이다. 프로그램의 수행
상태와 쿼리 실행결과 등이 기록된다. 기본 전체화면 오른쪽 하단에 위치한다.

![](media/Sharding/6bbda1671fc279b120c6c0736e63eb5f.jpg)

##### 문제 뷰

유효성 검사를 수행했을 때, 객체가 위반한 규칙에 대한 정보를 보여주는 뷰이다.
기본 전체화면 오른쪽 하단에 위치한다.

![](media/Sharding/ed1dfa284fb57c9f37b3fc4e10ac9d66.png)

**칼럼 설명**

-   No.: 선택한 객체가 위반한 규칙에 순차적으로 부여되는 일련번호이다.

-   Type: 규칙의 종류를 표시한다.

-   Resource: 규칙을 위반한 대상 객체를 표시한다. 예를 들어, 선택한 객체가
    'T1'이라는 이름의 테이블이고 위반한 규칙의 설명이 '데이터 노드가 가진 분산
    테이블의 컬럼 구성은 메타 노드에 등록된 샤드 테이블과 같아야 한다'라면
    구성이 달라 규칙을 위반한 컬럼의 이름을 표시한다.

-   Description: 위반한 규칙에 대한 상세 설명을 기술한다.

#### 샤드 데이터베이스 관리

이 절에서는 Shard Manager의 기능과 사용 방법에 대해 기술한다.

##### 샤드 데이터베이스 등록

1.  툴바 또는 Database 메뉴에 위치한 'Add New Shard Database'를 클릭한다.

2.  샤드 데이터베이스 이름과 메타 노드의 연결정보를 입력한다.

3.  'Test' 버튼을 클릭하여 입력한 연결정보를 통해 메타 노드에 접속이 정상적으로
    이루어지는지 확인한다.

4.  'Next' 버튼을 클릭하여 다음 페이지에서 메타 노드로부터 가져온 데이터 노드
    이름, 연결정보, 그리고 접속하는데 사용될 JDBC 드라이버 파일을 확인한다.

5.  각 데이터 노드 접속에 필요한 드라이버가 메타 노드와 다를 경우, Driver Path
    열에서 해당하는 칸에 위치한 연필 아이콘을 클릭하여 드라이버 파일을 변경한다.

6.  'Finish' 버튼을 클릭하여 샤드 데이터베이스를 저장한다.

7.  정상적으로 샤드 데이터베이스가 생성되었다면 해당 샤드 데이터베이스가 샤드
    데이터베이스 뷰에 나타난다.

##### 샤드 데이터베이스 편집

1.  샤드 데이터베이스 뷰에서 수정할 샤드 데이터베이스를 클릭한다.

2.  샤드 데이터베이스 뷰 위에서 마우스 오른쪽 버튼을 누르거나, Database 메뉴를
    열어 'Edit Shard Database'를 클릭한다.

3.  메타 노드 연결정보를 수정한 뒤, 'Test'버튼을 클릭하여 접속 여부를 확인한다.

4.  'Next' 버튼을 클릭하여 다음 페이지에서 수정된 메타 노드로부터 가져온 데이터
    노드 리스트를 확인한다.

5.  각 데이터 노드 접속에 필요한 드라이버 파일의 변경이 필요할 시, Driver Path
    열에서 해당하는 칸에 위치한 연필 아이콘을 클릭하여 파일을 변경한다.

6.  'Finish' 버튼을 클릭하여 수정된 샤드 데이터베이스를 저장한다.

##### 샤드 데이터베이스 제거

1.  샤드 데이터베이스 뷰에서 삭제할 샤드 데이터베이스를 마우스 오른쪽 버튼으로
    누르거나, 클릭 후 Database 메뉴를 열어 'Remove Shard Database'를 클릭한다.

2.  삭제 여부를 묻는 팝업 창에서 삭제할 샤드 데이터베이스가 맞는지 확인한 뒤,
    'Yes' 버튼을 클릭한다.

3.  정상적으로 샤드 데이터베이스가 삭제되었다면 해당 샤드 데이터베이스가 샤드
    데이터베이스 뷰에서 사라진다.

##### 샤드 데이터베이스 연결

샤드 데이터베이스 뷰에서 특정 샤드 데이터베이스를 연결한다. 연결할 샤드
데이터베이스를 더블클릭하거나, 마우스 오른쪽 버튼으로 눌러 'Connect'를 클릭한다.
연결이 정상적으로 수행되면 아이콘 오른쪽 하단에 초록색 화살표를 표시하고, 트리
하위 노드로 메타 노드에 등록된 데이터 노드를 표시한다.

##### 샤드 데이터베이스 연결 해제

샤드 데이터베이스 뷰에서 연결을 해제한다. 연결 해제할 샤드 데이터베이스를
더블클릭하거나, 마우스 오른쪽 버튼을 눌러 'Disconnect'를 클릭한다. 연결이
정상적으로 해제되었다면 아이콘 오른쪽 하단에 있는 초록색 화살표가 사라지고, 트리
하위 노드들이 사라진다.

##### 데이터 노드 추가

1.  메타 노드에 새 데이터 노드를 생성한다.

2.  샤드 데이터베이스 뷰에서 데이터 노드를 추가하고자 하는 연결된 상태의 샤드
    데이터베이스를 마우스 오른쪽 버튼으로 누르거나, 클릭 후 Data Node 메뉴를
    열어 'Add Data Node'를 클릭한다.

3.  데이터 노드 이름과 연결정보, 필요한 경우 alternate 데이터 노드의 연결
    정보까지 입력한다.

4.  'Test' 버튼을 클릭하여 입력한 연결정보에 접속이 정상적으로 이루어지는지
    확인한다.

5.  'OK' 버튼을 클릭하여 데이터 노드를 추가한다.

6.  정상적으로 데이터 노드가 추가되었다면, 샤드 데이터베이스 뷰 내 대상 샤드
    데이터베이스의 트리 하위 노드로 추가된 데이터 노드가 나타난다.

##### 데이터 노드 수정

1.  메타 노드에서 해당 데이터 노드의 연결 정보를 수정한다.

2.  샤드 데이터베이스 뷰에서 수정할 데이터 노드를 마우스 오른쪽 버튼으로
    누르거나, 클릭 후 Data Node 메뉴를 열어 'Edit Data Node'를 클릭한다.

3.  데이터 노드의 연결정보를 수정한다.

4.  'Test' 버튼을 클릭하여 입력한 연결정보에 접속이 정상적으로 이루어지는지
    확인한다.

5.  'OK' 버튼을 클릭하여 수정을 완료한다.

##### 데이터 노드 삭제

메타 노드에서 해당 데이터 노드를 삭제한다.

1.  샤드 데이터베이스 뷰에서 삭제할 데이터 노드를 마우스 오른쪽 버튼으로
    누르거나, 클릭 후 Data Node 메뉴를 열어 'Remove Data Node'를 클릭한다.

2.  삭제 여부를 묻는 팝업 창에서 삭제할 데이터 노드에 대한 정보를 확인한 뒤,
    'Yes' 버튼을 클릭한다.

3.  정상적으로 데이터 노드가 삭제되었다면 샤드 데이터베이스 뷰 내 대상 데이터
    노드가 사라진다.

##### Alternate 노드 삭제

메타 노드에서 해당 데이터 노드의 alternate 연결정보가 삭제된다.

1.  샤드 데이터베이스 뷰에서 삭제할 alternate 데이터 노드 연결정보의 트리 상위
    노드인 데이터 노드를 마우스 오른쪽 버튼으로 누르거나, 클릭 후 Data Node
    메뉴를 열어 'Remove Alternate Node'를 클릭한다.

2.  삭제 여부를 묻는 팝업 창에서 삭제할 alternate 데이터 노드를 확인한 뒤 'Yes'
    버튼을 클릭한다.

3.  정상적으로 alternate 데이터 노드가 삭제되었다면 샤드 데이터베이스 뷰 내 대상
    데이터 노드의 트리 하위 노드인 alternate 데이터 노드의 연결정보가 사라진다.

##### 메모리 테이블스페이스 사용률 확인

1.  샤드 데이터베이스 뷰에서 메모리 테이블스페이스의 사용률을 확인하려는 샤드
    데이터베이스를 마우스 오른쪽 버튼으로 누르거나, 클릭 후 Database 메뉴를 열어
    'Show Memory Tablespace Usage'를 클릭한다.

2.  확인하고자 하는 데이터베이스의 행에서 Tablespace Name 열에 해당하는 칸을
    클릭하여 원하는 메모리 테이블스페이스를 선택한다.

#### 샤드 객체 관리

##### 샤드 객체 설정

메타 노드에 샤드 객체의 분산 정보를 저장한다.

1. 샤드 객체 뷰의 툴바에 위치한 'Add New Shard Object' 버튼(![](media/Sharding/e74a11e0f77d2845b3ca5b8cd59e27e9.png)) 또는 메뉴에서 'Shard Object' - 'Add New Shard Object' 항목을 클릭한다.

2. 'Available Database Object' 테이블에서 샤드 객체로 지정할 항목의 체크박스를
   클릭하여 선택한다.

   ![](media/Sharding/cf92e33f6cacd1babf38d643c9754b92.png)

3. 분산 방식이 '복제(Clone)'나 '독립(Solo)'이 아니면, 선택한 샤드 객체의 샤드
   키와, 서브 샤드 키를 지정한 뒤, 샤드 키 분산 방식, 서브 샤드 키 분산 방식,
   기본 노드를 선택한다.

4. 'Key Values' 테이블에서 분산 정보에 등록할 노드와 샤드 키 값, 서브 샤드 키
   값을 작성한다.

5. 'Submit' 버튼을 클릭하여 샤드 객체 설정을 메타 노드에 요청한다.

6. 샤드 객체 설정이 완료되면, 해당 객체는 샤드 객체 뷰에 표시된다. 지정한 분산
   방식은 'Split Method'에 표시되고, 샤드 키와 서브 샤드 키는 객체의 하위
   노드로 표시된다.

##### 샤드 객체 해제

메타 노드에서 해당 객체에 대한 분산 정보를 삭제한다.

1.  샤드 객체 뷰에서 원하는 샤드 객체를 마우스 오른쪽 버튼으로 누르거나, 클릭 후
    'Shard Object' 메뉴를 열어 'Unset Shard Object'를 클릭한다.

2.  샤드 객체 해제 여부를 묻는 팝업 창에서 대상 객체를 확인한 뒤, 'Yes' 버튼을
    클릭하여 메타 노드에 샤드 객체 해제를 요청한다.

3.  샤드 객체 해제를 완료하면, 샤드 객체 뷰에서 해당하는 샤드 객체가 나타나지
    않는다.

##### 샤드 객체 정보 확인

샤드 객체 뷰에서 원하는 객체를 마우스 오른쪽 버튼으로 누르거나, 클릭 후 Shard
Object 메뉴를 열어 'Show Detail'을 클릭한다.

##### 샤드 객체 삭제

샤드 객체를 해제한 후, 메타 노드와 분산 정보에 등록된 데이터 노드에서 해당
객체를 삭제한다.

1.  샤드 객체 뷰에서 원하는 객체를 마우스 오른쪽 버튼으로 누르거나, 클릭 후
    Shard Object 메뉴를 열어, 객체 종류가 테이블일 경우 'Drop Table'를,
    프로시저일 경우 'Drop Procedure'를 클릭한다.

2.  삭제 여부를 묻는 팝업 창에서 삭제할 객체를 확인한 뒤, 'Yes' 버튼을 클릭한다.

3.  샤드 객체일 경우, Shard Manager가 해당 객체에 대해 샤드 객체 해제를 수행한
    뒤 삭제한다.

4.  정상적으로 객체가 삭제되었다면 샤드 객체 뷰 내 해당 객체가 사라진다.

##### 테이블 레코드 카운트 확인

1.  샤드 객체 뷰에서 원하는 테이블을 마우스 오른쪽 버튼으로 누르거나 클릭 후
    Shard Object 메뉴를 열어, 'Show Record Count'를 클릭한다.

2.  확인하고자 하는 데이터 노드의 행에서 Address 열에 해당하는 칸을 클릭하여
    원하는 연결정보를 선택한다.

##### 자동 데이터 재구축

샤드 테이블의 데이터 유효성 확인과 구조 변경에 따른 노드간 데이터 재분배를
손쉽게 수행한다.

1.  샤드 객체 뷰의 툴바에 위치한 'Rebuild Shard Table'(![](media/Sharding/58646a62a61346f627ee5b1a1e1cd20a.png)) 또는 메뉴에서 'Shard Object' - 'Rebuild Shard Table' 항목을 클릭한다.

2.  'Available Tables' 리스트에서 데이터 검증 또는 재구축을 할 샤드 테이블을
    선택하여 'Selected Tables' 리스트로 옮긴다.

3.  'Next' 버튼을 누르면 데이터 검증을 수행하고 다음 페이지로 이동한다.

4.  데이터 검증 결과를 확인한다. 검증 과정에서 오류가 발생한 샤드 테이블은
    자동으로 데이터 재구축 단계에서 제외된다.

5.  'Next' 버튼을 눌러 다음 페이지로 이동한다.

6.  데이터 재구축 시 사용할 일괄 처리 행의 단위(Batch Count) 값을 지정한다.

7.  'Rebuild' 버튼을 눌러 자동 데이터 재구축을 수행한다.

8.  'Selected Tables'에서 테이블을 선택하여 각 테이블의 재구축 수행 시 출력된
    로그와 노드의 레코드 카운트를 확인한다.

#### SQL 실행

##### 쿼리 뷰 열기

샤드 데이터베이스 뷰에서 원하는 샤드 데이터베이스를 마우스 오른쪽 버튼으로
누르거나, 클릭 후 Database 메뉴를 열어 'Show Query View'를 클릭한다.

##### SQL 실행

선택한 노드 종류에 해당하는 데이터베이스에서 입력한 SQL문이 실행된다.

1.  쿼리 뷰 내 SQL 입력 창에 실행하고자 하는 SQL문을 입력한다.

2.  쿼리 뷰 내 툴바에 위치한 체크박스 중, 입력한 SQL문을 실행하고자 하는 노드
    종류를 선택한다.

3.  입력한 SQL문 중 특정 쿼리만 수행하려면, 해당 구문을 마우스 커서로 드래그하여
    선택한 뒤 쿼리 뷰의 툴바에서 'Execute Statement'(![](media/Sharding/de1f28e5e2b6fb8d2d6484ef3772e3e9.png))을 클릭한다. 입력한 전체 SQL문을 모두 수행하고 싶을 경우에는 'Execute Script'(![](media/Sharding/436ca8084a13745802c439308c90c757.png))을 클릭하여 SQL 문을 실행한다.

4.  콘솔 뷰를 통해 각 데이터베이스에서의 실행 결과를 확인한다.

#### 샤드 데이터베이스 유효성 검사

데이터 노드 및 객체 구성에 대한 유효성 검사를 수행하는 방법에 대해 설명한다.
현재 Shard Manager에서 확인하는 구성 규칙은 다음과 같다.

1.  샤드 객체의 분산 정보에 포함된 데이터 노드가 메타 노드에 등록된 데이터
    노드인가?

2.  샤드 객체와 동일한 객체 타입, 사용자 이름, 객체 이름을 가진 객체가 분산할
    데이터 노드에 존재하는가?

3.  데이터 노드가 보유한 분산 테이블의 컬럼이 샤드 테이블의 컬럼과 동일한 이름,
    데이터 타입, 순서를 가지는가?

4.  데이터 노드가 보유한 분산 테이블의 제약사항이 샤드 테이블의 제약사항과
    동일한 종류 및 컬럼 구성을 가지는가?

5.  데이터 노드가 보유한 분산 프로시저의 파라미터가 샤드 프로시저의 파라미터와
    동일한 이름, 데이터 타입, 순서를 가지는가?

##### 샤드 데이터베이스 유효성 검사

샤드 데이터베이스 뷰 내에서 검사할 샤드 데이터베이스를 마우스 오른쪽 버튼으로
누르거나, 클릭 후 Database 메뉴를 열어 Validate/Validate를 클릭한다.

##### 규칙위반 검사

![](media/Sharding/49f7dcb7cfea869249daf9d6c6b482f2.jpg)

유효성 검사를 수행하여 규칙을 위반한 요소가 발견되면, 샤드 데이터베이스 뷰와
샤드 객체 뷰에서 규칙을 위반한 객체와 그 상위 트리 요소의 아이콘 왼쪽 하단에
엑스 표시가 있는 빨간 네모가 나타난다. 이러한 객체를 선택하면 Problems 뷰에서
위반한 규칙을 확인할 수 있다.

##### 유효성 검사 결과 삭제

유효성 검사 결과를 삭제하고자 할 때는 샤드 데이터베이스 뷰에서 해당 샤드
데이터베이스를 마우스 오른쪽 버튼으로 누르거나, 클릭 후 Database 메뉴를 열어
Validate/Clear Validation Result를 클릭한다.
