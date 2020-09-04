

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
    - [샤드 메타 설정](#%EC%83%A4%EB%93%9C-%EB%A9%94%ED%83%80-%EC%84%A4%EC%A0%95)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [디렉토리](#%EB%94%94%EB%A0%89%ED%86%A0%EB%A6%AC)
  - [3.Altibase Sharding 사용방법](#3altibase-sharding-%EC%82%AC%EC%9A%A9%EB%B0%A9%EB%B2%95)
    - [Altibase Sharding 제약사항](#altibase-sharding-%EC%A0%9C%EC%95%BD%EC%82%AC%ED%95%AD)
    - [Altibase Sharding 통신 방법](#altibase-sharding-%ED%86%B5%EC%8B%A0-%EB%B0%A9%EB%B2%95)
    - [샤드 노드](#%EC%83%A4%EB%93%9C-%EB%85%B8%EB%93%9C)
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
    - [Fail-Over](#fail-over)
    - [샤딩 분산 시스템 변경](#%EC%83%A4%EB%94%A9-%EB%B6%84%EC%82%B0-%EC%8B%9C%EC%8A%A4%ED%85%9C-%EB%B3%80%EA%B2%BD)
  - [4.Altibase Sharding 딕셔너리](#4altibase-sharding-%EB%94%95%EC%85%94%EB%84%88%EB%A6%AC)
    - [샤드 메타](#%EC%83%A4%EB%93%9C-%EB%A9%94%ED%83%80)
    - [SYS_SHARD.VERSION\_](#sys_shardversion_)
    - [SYS_SHARD.LOCAL_META_INFO\_](#sys_shardlocal_meta_info_)
    - [SYS_SHARD. GLOBAL_META_INFO\_](#sys_shard-global_meta_info_)
    - [SYS_SHARD.NODES\_](#sys_shardnodes_)
    - [SYS_SHARD.OBJECTS\_](#sys_shardobjects_)
    - [SYS_SHARD.RANGES\_](#sys_shardranges_)
    - [SYS_SHARD.CLONES\_](#sys_shardclones_)
    - [SYS_SHARD.SOLOS\_](#sys_shardsolos_)
    - [성능 뷰 (Performance View)](#%EC%84%B1%EB%8A%A5-%EB%B7%B0-performance-view)
    - [샤드 성능 뷰 (Shard Performance View)](#%EC%83%A4%EB%93%9C-%EC%84%B1%EB%8A%A5-%EB%B7%B0-shard-performance-view)
    - [S\$CONNECTION_INFO](#sconnection_info)
    - [S\$PROPERTY](#sproperty)
    - [S\$SESSION](#ssession)
    - [S\$STATEMENT](#sstatement)
  - [5.Altibase Sharding 패키지](#5altibase-sharding-%ED%8C%A8%ED%82%A4%EC%A7%80)
    - [DBMS_SHARD](#dbms_shard)
  - [6. shardLoader](#6-shardloader)
    - [설치 방법](#%EC%84%A4%EC%B9%98-%EB%B0%A9%EB%B2%95)
    - [shardLoader 설정](#shardloader-%EC%84%A4%EC%A0%95)
    - [명령행 옵션](#%EB%AA%85%EB%A0%B9%ED%96%89-%EC%98%B5%EC%85%98)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Altibase® Administration

Altibase Sharding Guide
=======================

![](media/Sharding/e5cfb3761673686d093a3b00c062fe7a.png)

Altibase Administration Altibase Sharding Guide

Release 7.2

Copyright ⓒ 2001\~2021 Altibase Corp. All Rights Reserved.

본 문서의 저작권은 ㈜알티베이스에 있습니다. 이 문서에 대하여 당사의 동의
없이 무단으로 복제 또는 전용할 수 없습니다.

**㈜알티베이스**

08378 서울시 구로구 디지털로 306 대륭포스트타워Ⅱ 10층

전화: 02-2082-1114 팩스: 02-2082-1099

고객서비스포털: <http://support.altibase.com>

homepage: [http://www.altibase.com](http://www.altibase.com/)

## 서문

### 이 매뉴얼에 대하여

이 매뉴얼은 Altibase의 분산 데이터베이스 기술인 Altibase Sharding에 대해 설명한다.

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

이 매뉴얼은 데이터베이스 서버로 Altibase 7.2 또는 그 이상의 버전을 사용한다는 가정 하에 작성되었다.

#### 문서화 규칙

이 절에서는 이 매뉴얼에서 사용하는 규칙에 대해 설명한다. 이 규칙을 이해하면 이 매뉴얼과 설명서 세트의 다른 매뉴얼에서 정보를 쉽게 찾을 수 있다.

여기서 설명하는 규칙은 다음과 같다.

-   구문 다이어그램

-   샘플 코드 규칙

##### 구문 다이어그램

이 매뉴얼에서는 다음 구성 요소로 구축된 다이어그램을 사용하여, 명령문의 구문을 설명한다.

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
-   JDBC User's Manual
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

## Altibase Sharding 소개

이 장은 Altibase Sharding의 개념과 특징에 대하여 설명한다.

### 샤딩 개요

#### 샤딩 개념 및 모델

샤딩(Sharding)은 하나의 데이터베이스에 저장했던 데이터를 여러개의 데이터베이스들에 분산하여 저장 및 처리하는 스케일 아웃 기술이다.

![](media/Sharding/1cd95d21b81794ed43c6eafff01f8e7c.png)

[그림 1‑1] sharding 개념

샤딩의 유형은 일반적으로 코디네이터를 이용하여 데이터를 분산하여 처리하는 서버측 샤딩(server-side sharding)과 클라이언트 레벨에서 데이터를 분산하여 처리하는 클라이언트측 샤딩(client-side sharding) 방식이 있다. 알티베이스는 이 두 가지 방식을 혼용한 하이브리드 샤딩(hybrid sharding) 방식이다.

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

반면에 코디네이터 처리 용량을 넘어서면 병목현상(bottle-neck)이 발생하여 샤딩 시스템을 확장하기 어려운 단점이 있다. 

#### 클라이언트측 샤딩(Client-side Sharding)

![](media/Sharding/c692bfbc33bf556ad6ed199b492dffd1.png)

[그림 1‑3] 클라이언트측 샤딩

클라이언트측 샤딩은 클라이언트 레벨에서 데이터가 위치한 데이터베이스를 미리 알고, 해당 데이터베이스에 직접 접속하여 처리하는 구조이다. 이 구조는 샤딩 확장에 따른 용량과 성능 확장이 가능하고 코디네이터 부하 한계로 인한 제약점이 없다는 장점이 있다. 

그러나, 클라이언트 레벨에서 대량 데이타 조인 및 집계처리를 포함한 모든 형태의 분산처리를 직접하려면, 클라이언트들이 모두 컴퓨팅 파워가 서버급이어야 하는데, 그럴 수 없으므로, 클라이언트측 샤딩에서는 단순하게 처리할 수 있는것들만을 처리하는 단점이 있다.

#### 하이브리드 샤딩(Hybrid Sharding)

하이브리드 샤딩은 클라이언트측 샤딩과 서버측 샤딩을 혼용하는 방식이다.

알티베이스는 쿼리별로 처리 성능 및 효율에 맞추어 자동으로 서버측 샤딩 혹은 클라이언트측 샤딩으로 처리한다. 그래서, 각 샤딩방식의 장점을 취하고 단점을 보완할 수 있다.

![](media/Sharding/944963501cb5f8370b7dfe663bec7608.jpg)

[그림 1‑4] 하이브리드 샤딩

### Altibase Sharding 용어

#### 샤드 노드(shard node) 

샤딩 시스템을 구성하는 각각의 데이터베이스 인스턴스이다. 최대 128개의 샤드 노드를 지원한다.

#### sharded database

여러개의 샤드 노드들로 구성된 사용자 입장에서 논리적으로 하나인 데이타베이스를 sharded database 라고 한다. 

#### 샤드 클러스터 관리자(ZooKeeper)

Split brain 방지등의 샤딩 클러스터 관리를 위하여 Apache ZooKeeper를 사용한다.

#### 샤딩 클러스터 시스템(Sharding Cluster System)

여러개의 샤드 노드들로 구성된 sharded database 와 샤드 클러스터 관리자(ZooKeeper)를 합하여 샤딩 클러스터 시스템이라고 한다. 

#### 샤드 메타(shard meta) 

샤드 노드의 정보, 샤드 객체, 분산 설정 등 분산 정보가 저장되는 메타 테이블들을 총칭하여 샤드 메타라고 한다. 샤드 메타 테이블들은 sys_shard 사용자의 객체로 관리된다.

#### 샤드 코디네이터(shard coordinator) 

분산된 데이터베이스를 통합하여 질의를 최적화하고 수행하는 분산 질의 처리기이다.

#### 샤드 라이브러리(shard library) 

하이브리드 샤딩을 지원하는 클라이언트 프로그램 라이브러리이다.

#### 샤드 데이터(shard data) 

분산된 데이터 조각이다. 전체 분산 데이터베이스의 데이터 일부를 가지고 있다.

#### 샤드 레플리카(shard replica) 

샤드 데이타에 대한 복제본이다. k-safety 값 만큼의 복제본을 가지고 있다.

#### 샤드 커넥션(shard connection)

각종 커넥션들을 통칭하여 샤드 커넥션이라고 한다.

#### 외부 커넥션(external connection)

외부 네트워크를 사용한 샤드 노드의 연결을 외부 커넥션이라고 하며 외부 커넥션은 사용자 커넥션과 샤드 라이브러리 커넥션의 두 가지가 있다.

#### 사용자 커넥션(user connection)

사용자의 클라이언트 응용프로그램에서 명시적으로 접속한 연결이다.

#### 샤드 라이브러리 커넥션(shard library connection )

샤드 라이브러리를 사용한 클라이언트가 데이터 처리를 위해 모든 샤드 노드들에 자동으로 접속한 연결이다.

#### 내부 커넥션 (internal connection)

내부 네트워크를 사용한 샤드 노드의 연결을 내부 커넥션이라고하며 샤드 노드들 간에 내부적으로 사용하는 것으로 코디네이터 커넥션이 있다.

#### 코디네이터 커넥션 (coordinator connection)

샤드 노드들 간에 내부적으로 사용하는 연결이다.

#### 샤드 세션(shard session)

사용자 커넥션으로 연결된 세션과 관련하여 열린 모든 세션의 그룹을 샤드 세션이라 한다.

#### 코디네이팅 샤드 노드(coordinating shard node)

샤드 노드들 중 사용자가 접속한(사용자 커넥션) 샤드 노드를 말한다.

#### 분산 방식(split method)

샤딩 시스템에서 데이터를 위치시키는 방법이다. 데이터의 특성에 맞게 적용할 수 있는 다양한 분산 방식을 제공한다. 현재 지원하는 분산 방식은 다음과 같다.

-   HASH
-   RANGE
-   LIST
-   COMPOSITE
-   CLONE
-   SOLO

#### 샤드 객체(shard object)

분산 저장 및 처리되는 객체를 지칭한다. 현재 지원하는 분산객체는 다음과 같다.

-   Table
-   Procedure

#### 샤드 테이블(shard table)

Altibase Sharding에서 제공하는 분산 방식에 따라 설정된 테이블을 샤드 테이블이라고 하며 샤드 테이블에 대한 정보는 샤드 메타에 등록된다. 
샤드 테이블은 다음과 같이 분류된다.

* 샤드 키 분산 테이블  
  * 단일 샤드 키 분산 테이블 ( HASH, RANGE, LIST )
  * 복합 샤드 키 분산 테이블 ( COMPOSITE )
* 복제 분산 테이블 ( CLONE )
* 독립 분산 테이블 ( SOLO )

#### 샤드 쿼리(shard query), 논샤드 쿼리(Non-shard query)

샤딩으로 분산된 데이터베이스에서 쿼리는 샤드 쿼리와 논샤드 쿼리로 분류한다.

샤드쿼리는 동일한 쿼리를 분산된 테이블의 레코드를 샤드노드별로 별개로 수행하여 취합한 결과가 하나의 데이타베이스에서 처리한 결과와 동일 할 경우를 지칭한다. 논샤드 쿼리는 샤드 쿼리가 아닌 모든
쿼리를 지칭한다.

샤드쿼리는 클라이언트측 샤딩으로 수행되며, 성능 및 스케일 아웃에 유리하다.

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

논샤드 쿼리의 몇 가지 예를 보면 다음과 같다.

```
SELECT count(*) FROM s1;
SELECT * FROM s1 order by k1;
```

논샤드 쿼리는 샤드 코디네이터의 중간 처리를 거치게 되어 질의 처리 성능이 샤드 쿼리에 비해 떨어지므로 논샤드 쿼리를 튜닝하여 샤드쿼리로 만드는 것이 성능 및 스케일아웃 측면에서 유리하다.

#### 샤드 뷰(shard view)

Altibase Sharding은 샤드 뷰를 제공한다. 쿼리가 논샤드 쿼리인 경우, 앞에 "SHARD" 키워드를 추가하면 샤드 노드에 논샤드 쿼리를 전송할 수 있다.

샤드 뷰를 사용하면 샤드 코디네이터의 부하를 줄이거나, 사용자가 의도하여 분산쿼리를 수행할 수 있다.

샤드 코디네이터의 부하를 줄이는 예는 다음과 같다.

```
SELECT sum(k1) FROM s1;
```

위 쿼리를 각 샤드 노드에서 부분 합을 얻고 코디네이터에서 취합하도록 다음과
같이 수정할 수 있다. 가능한 한 코디네이터의 부하를 샤드 노드로 분산하는 것이
스케일아웃 측면에서 더 유리하다.

```
SELECT sum(s) FROM SHARD(SELECT sum(k1) s FROM s1);
```

또한 아래와 같이 샤드 뷰를 이용하여 테이블의 레코드 수를 노드별로 얻는
쿼리 작성도 가능하다.

```
SELECT * FROM shard(SELECT shard_node_name(), count(*) FROM s1); 
```

#### 샤드 쿼리 분석기(shard query analyzer)

사용자의 쿼리가 서버측 샤딩으로 수행하는 쿼리와 클라이언트측 샤딩으로 수행하는 쿼리로 구분한다.

샤드 분석결과는 쿼리 수행 시마다 재사용 되므로, 샤드 코디네이터에서 샤드 쿼리 분석으로 생기는 부하는 크지 않다.

#### 샤드 쿼리 최적화기(shard query optimizer)

샤드 코디네이터의 샤드 쿼리 최적화기는 서버측 샤딩에 대한 최적의 분산 쿼리를 생성하고, 분산 쿼리에 대한 분산 플랜을 생성한다.

사용자 쿼리가 서버측 샤딩으로 수행되는 쿼리로 분류된 경우, 해당 쿼리를 서버측에서 수행하기 위해서 분산부와 통합부로 구분한다. 분산부는 각 샤드 노드에서 수행할 부분(분산) 쿼리이고, 통합부는 각 노드에서 수행한 결과를 모아서 수행할 나머지(통합) 쿼리이다.

가능한 많은 부분을 분산부로 처리하는 것이 성능을 극대화할 수 있기 때문에 샤드 쿼리 최적화기는 최대한 샤드 쿼리 변환(Shard Transformation)을 수행한다.

#### 샤드 쿼리 실행기 (Shard Query Executor)

샤드 쿼리 실행기는 클라이언트측 샤딩의 실행기와 서버측 샤딩의 실행기로 구분한다. 클라이언트측 샤딩의 실행기는 샤드 라이브러리에서 동작하며, 서버측 샤딩의 실행기는 샤드 노드에서 샤드 코디네이터를 통해서 동작한다.

#### 샤드 키(shard key)

분산 정의의 기준이 되는 컬럼 또는 파라미터이다. 현재 샤드 키로 사용할 수 있는 데이터 타입은 다음과 같다.

-   smallint
-   integer
-   bigint
-   char
-   varchar

#### 샤드 키워드(shard keyword)

Altibase Sharding에서 지원하는 키워드로 임의의 데이터가 존재하는 샤드 노드로 쿼리를 수행하게 할 수 있다. 샤드 키워드의 종류는 다음과 같다.

-   SHARD
-   NODE

샤드 지원 구문의 앞이나 SELECT문의 샤드 뷰 앞에 사용하면 해당 쿼리를 샤드 쿼리로 수행하여 결과를 반환한다.

```
SHARD SELECT shard_node_name(), count(*) FROM s1;
NODE[DATA] SELECT shard_node_name(), count(*) FROM v$session;
NODE[DATA(‘node1’)] SELECT * FROM s1;
```

#### 샤드 프로시저(shard procedure)

샤딩 시스템에 설정된 분산 정의된 프로시저로 지정된 인자의 값을 기준으로 분산 수행된다. 프로시저 내의 쿼리에 대해서는 사용자가 분산 처리하도록 작성해야 한다.

#### 샤드 플랜(shard plan)

질의가 샤드 코디네이터에서 분산 수행되는 경우의 질의 수행계획을 말한다. 샤드 플랜에는 샤드 노드에서 분산 수행되는 질의의 수행계획을 포함한다.

#### 샤드 트랜잭션(shard transaction)

애플리케이션이 생성한 트랜잭션에서 수행하는 질의의 따라 샤드 노드들에 분산 트랜잭션을 생성하게 된다. 이 트랜잭션들을 샤드 트랜잭션이라고 한다.

클라이언트측 샤딩으로 생성된 트랜잭션과 서버측 샤딩으로 생성된 트랜잭션을 하나의 트랜잭션으로 통합하여 수행한다.

샤드 트랜잭션은 다음과 같이 분류할 수 있다.

-   다중 노드 트랜잭션(multiple node transaction)
    분산 트랜잭션을 개별 샤드 노드별로 처리한다. 노드장애등의 상황에서 커밋이 안되는 노드가 발생할 수 있다.
-   글로벌 트랜잭션(global transaction)
    분산 트랜잭션을 two-phase commit를 사용하여 처리하여, 분산 트랜잭션에 참여한 모든 샤드노드에 동일하게 커밋 혹은 롤백이 되는것을 보장한다.
-   글로벌 일관 트랜잭션(global consistent transaction)
    글로벌 트랜잭션에서 보장하는것에 추가하여, 글로벌 읽기 일관성을 보장한다.

#### 샤드 메타 번호(Shard Meta Number )

샤드 메타 번호(SMN)란 샤드 메타에 대한 버전 관리 번호 이다.

#### 레플리카 셋(Replica Set)

레플리카 셋(Replica Set)이란 Altibase Sharding 시스템에서 무중단 서비스를 제공하기 위해 생성한 복제(Replication)들의 관계를 저장한 객체이다.

#### K-safety

K-safety는 장애 감내(fault tolerance) 허용값를 의미하며, 이 값은 샤드데이타가 복제된 갯수를 나타낸다. 이러한 복제들은 장애가 발생한 샤드노드에 대한 fail-over를 수행할 수 있다록 한다.

Altibase Sharding에서는 K-safety는 0, 1 또는 2의 값을 가질 수 있다. K-safety가 1 일때, 샤드노드 하나가 장애가 발행해도 전체 시스템은 정상적으로 운영된다. 추가적으로 샤드노드에 장애가 발생하더라도, 해당 노드의 복제본을 가진 노드가 장애가 발생하지 않는 한, 전체 시스템은 정상적으로 운영된다.

#### ShardCLI

ShardCLI는 CLI 응용프로그램을 하이브리드 샤딩으로 동작할 수 있도록 하는 기능이다.

CLI 응용프로그램 빌드 시 기존의 ODBCCLI 라이브러리를 ShardCLI 라이브러리로 바꾸어야 한다.

ShardCLI 라이브러리는 libshardcli.a와 libshardcli_sl.so 두 개의 파일을 지원한다.

#### ShardJDBC

ShardJDBC는 JDBC 응용프로그램을 하이브리드 샤딩으로 동작할 수 있도록 하는 기능이다.

JDBC는 별도의 샤딩 라이브러리가 존재하는것은 아니고, JDBC 접속 URL에 sharding prefix를 붙여주면 ShardJDBC 로 동작한다.

### Altibase Sharding 개요

#### Altibase Sharding 소개

Altibase Sharding은 Altibase에 샤딩 기술을 도입하여 저장 용량과 시간당 처리량을
향상시키고 대용량의 데이터베이스를 분산처리할 수 있게 한다.

Altibase Sharding은 하이브리드 샤딩으로써, 사용자 SQL을 분석하여 자동으로
클라이언트측 샤딩이나 서버측 샤딩으로 수행할 것인지를 분석하여 경로를
최적화한다.

Altibase Sharding은 다양한 분산 방식과 분산 객체, 유틸리티를 지원하고 있으며,
다양한 업무에서 샤딩을 적용할 수 있다.

샤드 전용 클라이언트 라이브러리를 사용하여야 하이브리드 샤딩방식이 적용된다. 샤드 전용 클라이언트 라이브러리를 사용하지 않으면 서버측 샤딩방식으로만 동작한다.

![altibase_hybrid_sharding_overview_small](media/Sharding/altibase_hybrid_sharding_overview_small.png)

[그림 1‑8] Altibase Sharding의 하이브리드 샤딩

#### Altibase Sharding 구성 개요

![sharding_overview_terminology](media/Sharding/sharding_overview_terminology.png)

-   응용프로그램 
-   샤드 라이브러리
-   샤드 노드
    -   샤드 코디네이터
    -   샤드 메타
    -   샤드 데이터
    -   샤드 레플리카
-   ZooKeeper

응용프로그램은 샤드 라이브러리를 사용하여 클라이언트측 샤딩과 서버측 샤딩을 사용할 수 있으며, 그 외의 라이브러리를 사용하는 경우 서버측 샤딩만을 사용할 수 있다.

샤드 코디네이터는 샤드 쿼리 분석기, 최적화기, 실행기로 구성되어있으며 쿼리를 분석하고 최적화하여 전체 샤드 노드들간의 데이터 및 트랜잭션 처리를 조율한다.

샤드 메타는 샤드 노드 구성 및 샤드 객체에 관련된 정보 및 샤딩에 필요한 메타 데이터를 저장한다.

샤드 데이터는 실제 데이터가 분산 저장되어 있는 데이터베이스이다.

샤드 레플리카는 샤드 데이타에 대한 복제본이다. k-safety 값 만큼의 복제본을 가지고 있다.

ZooKeeper는 split brain 방지등의 클러스터 관리를 수행한다.

#### 샤딩 클러스터 시스템

샤딩 클러스터 시스템은 사용자의 Shard DDL(ADD, DROP, JOIN, FAILBACK) 구문이나 샤딩 HA에 의해서 자동으로 Sharded Database 서비스에 참여하거나 제외될 수 있다. 

![](media/Sharding/sharding_cluster_system_view.png)

[그림 1‑10] Altibase Sharding cluster system view

#### 샤딩 복제 개요

Altibase Sharding 시스템은 모든 샤드 노드가 K-safety 만큼의 샤드 데이타 복제본을 유지하여, 모든 샤드 노드가 Active 노드이면서 동시에 Standby 노드의 역할을 한다.

Altibase Sharding 시스템은 단일 장애점(SPOF: single point of failure)이 없는 시스템 구성으로 높은 신뢰성을 가질 수 있다.

![](media/Sharding/sharding_replication_view.png)

[그림 1‑11] Altibase Sharding replication view

### Altibase Sharding 특징

#### 선형 확장성

Altibase Sharding은 scale-out시에 성능 병목없이 저장 용량과 시간당 처리량을 선형적으로 향상시켜 대용량의 데이터를 분산 처리할 수 있다.

#### No SPOF(No Single Point Of Failure)

Altibase Sharding의 모든 샤드 노드가 마스터 역할을 수행하여, 단일 장애점(single point of failure)이 없다는 특징을 갖는다.

#### 오류 독립성

하나의 샤드 노드가 비정상적이거나 속도가 느려지더라도 다른 샤드 노드의 성능이나 가용성에는 영향을 미치지 않는다.

#### 애플리케이션 호환성

기존 응용프로그램 소스나 기존 SQL을 수정하지 않고, 샤딩을 적용할 수 있다.

사용자가 하이브리드 샤딩을 고려하여 쿼리를 튜닝할 수 있도록 추가적인 샤드 키워드를 제공한다.

#### 사용자 정의 데이터 분산

Altibase Sharding을 통해 사용자는 데이터베이스의 데이터를 원하는 형태로 분산할
수 있도록 정의할 수 있다.

예를 들면, 특정 관할 구역에 대한 데이터를 사용자가 원하는 샤드 노드에 위치시킬
수 있기 때문에, 논리적으로 특정 구역에 대한 데이터를 모을 수 있다.

또한 지역적으로 가까운 데이터들을 물리적으로 가까운 샤드 노드에 위치시킬 수
있기 때문에, 물리적으로 특정 관할 구역에 가까운 데이터를 모아둘 수도 있다.

#### 복제를 통한 고가용성 

Altibase Sharding은 K-safety 값 만큼의 복제본을 유지하여, 고가용성(High Availability)을 보장한다.

#### 지능적인 하이브리드 샤딩

일반적으로 샤딩은 서버측 샤딩을 주로 제공하면서, 부분적으로 클라이언트측 샤딩을 지원한다. 그러나 알티베이스의 샤딩은 서버측 샤딩과 클라이언트측 샤딩을 동시에 제공한다.

일반적인 클라이언트측 샤딩의 특징은 다음과 같다.

-   커넥션 시점 샤딩  
    응용프로그램에서 특정 노드를 지정하여 접속하는 방식이다. 다른 노드에 접근하기 위해서는 재접속을 해야 한다.

-   SQL 작성 시점 샤딩  
    응용프로그램에서 쿼리를 작성(혹은 생성)할 때 수행할 노드를 지정하는 방식이다. 다른 노드에 접근하기 위해서는 쿼리를 재작성(혹은 재생성)해야 한다.

Altibase Sharding의 하이브리드 샤딩의 특징은 다음과 같다.

-   SQL 수행 시점 샤딩
    응용프로그램에서 쿼리를 수행하는 시점에 자동으로 수행할 샤드 노드가 선택된다. 사용자는 샤드 노드를 구분할 필요가 없다.

-   하이브리드 샤딩
    쿼리에 따라 클라이언트측이나 서버측으로 수행경로를 변경하여 성능을 최대화한다.

#### 쉬운 클러스터 관리

Shard DDL(ADD, DROP, JOIN, FAILBACK) 구문을 제공하여, 손쉬은 샤드 노드 관리를 할 수 있다.

#### 다양한 업무 적용 범위

클라이언트측 샤딩의 특징에 적합한 다음과 같은 OLTP (Online Transaction Processing) 업무

-   대용량 데이터베이스를 대상으로 하는 업무
-   매우 짧은 시간에 읽거나 조작하는 업무를 하나의 트랜잭션 단위로 수행하는 업무
-   매우 많은 사용자가 동시에 수행하는 업무
-   매우 짧은 시간에 높은 처리량이 요구되는 업무

서버측 샤딩의 특징에 적합한 다음과 같은 OLAP (Online Analytical Processing) 업무

-   샤드노드별로 분산처리 될 수 있는 것이 많은 업무

#### 최적 경로의 쿼리 수행을 통한 분산 트랜잭션의 우수한 성능

하나의 샤드 트랜잭션내의 다양한 쿼리들은 개별적으로 최적의 경로로 수행될수 있어서, 분산 트랜잭션의 성능이 우수하다.

![](media/Sharding/shard_query_analyzer_optimizer_executer.png)

[그림 1‑12] Shard Query Analyzer & Optimizer & Executor

위 그림은 하이브리드 샤딩으로 사용자의 쿼리가 수행되는 예를 보여준다. Q3-1와
Q3-2는 샤드 쿼리 분석기가 Q3에서 생성한 분산 쿼리와 통합 쿼리이다.

```
Q1) insert into t1(key, c1) values (1, 100);
Q2) update t1 set c1=c1+1 where key=2;
Q3) select sum(c) total_count from (select count(*) c from t1);
    Q3-1) select count(*) c from t1;
    Q3-2) select sum(c) total_count from temp;
```

#### 다양한 샤드 쿼리와 함수 지원

Altibase Sharding은 아래의 쿼리를 지원한다.

-   INSERT
-   INSERT SELECT
-   UPDATE
-   DELETE
-   SELECT
    - Join
    - Outer Join
    - Aggregate function
    - Grouping
    - Ordering
    - Subquery

쿼리가 샤드 쿼리인지 논샤드 쿼리인지 여부는 샤드 플랜을 조회하여 확인할 수 있다.
논샤드 쿼리로 플랜이 조회되는 경우 샤드 키워드를 이용하여 좀 더 효율적인
쿼리로 튜닝할 수 있다. 뿐만 아니라 다음과 같은 샤드 지원 함수들을 제공한다.

-   SHARD_NODE_NAME
-   SHARD_KEY

#### 다양한 분산 객체

일반적인 샤딩은 샤드 테이블에 한해 물리적 데이터 분산만 적용하지만, Altibase
Sharding은 샤드 프로시저도 분산하여 수행할 수 있다.

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

[그림 1‑13] Altibase Sharding 분산 방식

##### 해시(Hash) 분산 방식

Altibase Sharding의 해시 분산은 샤드 키에 해당하는 값을 내장된 hash함수를
이용하여 분산하는 것을 말한다.

해시 함수는 데이터를 균등하게 분산하는데 이용된다. 

해시 함수로부터 구한 해시 값에 나머지 연산을 수행한 값을 이용하여, 전체 데이터를 1000개의 그룹으로 나누어 관리한다. 

각 그룹마다 샤드 노드를 지정하여 데이터를 임의로 분산시킬 수 있다.

-   hash_group[1] = { record(x) \| if (mod(hash(shard key value of x),1000)==0) };
-   hash_group[2] = { record(x) \| if (mod(hash(shard key value of x),1000)==1) };
-   …
-   hash_group[1000] = { record(x) \| if (mod(hash(shard key value of x),1000)==999) };

이렇게 구분된 1000개의 hash group을 사용자의 필요에 따라 분산 정의한다. 예를
들면 user_id를 기준으로 해시 분산 방식으로 설정하는 경우, user_id의 해시 값을
1000개의 그룹으로 나누어 다음과 같이 설정한다.

-   1\~300번 hash group    –\> 샤드 노드1
-   301\~600번 hash group  –\> 샤드 노드2
-   601\~1000번 hash group –\> 샤드 노드3

데이터를 분산하기 전 다음과 같은 해시 분산 방식으로 데이터를 분산했을 때
데이터의 분포 상태를 예측할 수 있다.

```
iSQL> SELECT hash, count(*) FROM (SELECT mod(hash(user_id),1000)+1 hash FROM table) GROUP BY hash;
```

##### 범위(Range) 분산 방식

해시 분산 방식을 사용하면 데이터가 비교적 균등하게 분산되는 반면, 특정 데이터가
어느 노드에 위치하는지 알기 어려워진다.

범위 분산 방식은 샤드 키 값으로 해당 데이터가 어느 노드에 위치하는지
관리자가 쉽게 알 수 있어 유리하다. 또한 해시 분산 방식에 비해 비교적 샤드 노드
확장이 쉬운 장점이 있다. 다만, 데이터가 샤드 노드들에 고르게 분산될 수 있도록
범위를 지정하는 것이 좋다.

예를 들면 샤드키 user_id 로 범위 분산 방식을 적용하는 경우 다음과 같이
설정한다.

-   { record(x) \| (shard key value of x) \<= ‘9’ }        -\> 샤드 노드 1
-   { record(x) \| ‘9’ \< (shard key value of x) \<= ‘M’ } -\> 샤드 노드 2
-   { record(x) \| ‘M’ \< (shard key value of x) \<= ‘Z’ } -\> 샤드 노드 3

범위 분산 방식 역시 데이터를 분산하기 전에 쿼리로 데이터의 분포를 예측할 수
있다.

```
iSQL> SELECT user_id, count(*) FROM table GROUP BY user_id;
```

그러나 범위 분산 방식으로 데이터를 고르게 분산했더라도, 운영 중에 데이터가
변경됨으로써 불균형이 발생할 수 있기 때문에 지속적으로 데이터 분포의 모니터링이
필요하다.

##### 리스트(List) 분산 방식

리스트 분산은 샤드 키 값을 특정값과 일치하는지 확인하여 분산하는 방식이다. 범위
분산 방식보다 더 직관적이고 특정 샤드 키 값에 대하여 쿼리를 수행하는 경우에도
유리하다.

예를 들면 지역을 샤드 키로 설정하고 리스트 분산 방식으로 설정하면 다음과 같다.

-   { record(x) \| (shard key value of x) = ‘서울’ } -\> 샤드 노드1
-   { record(x) \| (shard key value of x) = ‘부산’ } -\> 샤드 노드 2
-   { record(x) \| (shard key value of x) = ‘대구’ } -\> 샤드 노드 3

이 경우 데이터를 지역별로 분산하여, 지역별 통계 쿼리 작성에 유리하다. 리스트
분산 방식도 범위 분산 방식처럼 데이터가 샤드 노드들에 고르게 분산될 수 있도록
지정하는 것이 좋다.

##### 복합(Composite) 샤드 키 분산 방식

복합 샤드 키 분산 방식은 두 개의 샤드 키를 적용한 분산 방식으로 각 샤드 키는
해시, 범위, 리스트 분산 방식 중 선택하여 적용한다.

예를 들면 지역명을 샤드 키(리스트 분산)로 적용하고 고객번호를 서브 샤드 키(해시
분산)로 적용하면 다음과 같다.

-   { record(x) \| (shard key value of x) = ‘서울’ and hash(sub-shard key value of x) \<= 500 }  -\> 샤드 노드1
-   { record(x) \| (shard key value of x) = ‘서울’ and hash(sub-shard key value of x) \<= 1000 } -\> 샤드 노드 2
-   { record(x) \| (shard key value of x) = ‘강원’ and hash(sub-shard key value of x) \<= 1000 } -\> 샤드 노드 3

##### 복제(Clone) 분산 방식

복제 분산 방식은 샤드 키를 지정할 필요가 없고, 모든 샤드 노드들에 해당 샤드 객체의 데이타가 중복 저장된다.

복제 분산이 적용된 샤드 객체에 대한 접근은 샤드 노드들 중에서 임의 선택하여 수행한다. 예를 들어 복제 분산이 적용된 샤드 테이블을 조회하는 경우, 트랜잭션에서 가장 먼저 접근한 샤드 노드를 우선하여 선택한다. 먼저 접근한 샤드 노드가 없는 경우에는, 노드를 임의로 선택하여 데이터를 조회한다.

##### 독립(Solo) 분산 방식

독립 분산은 복제 분산 방식은 샤드 키를 지정할 필요가 없고, 사용자가 지정한 하나의 노드에만 객체를 저장한다.

-   TABLE_1 –\> 샤드 노드 1
-   TABLE_2 –\> 샤드 노드 2
-   TABLE_3 –\> 샤드 노드 1

#### 쉬운 마이그레이션

기존 데이터베이스를 샤드 데이터베이스로 마이그레이션하는 경우, shardLoader
유틸리티를 사용하여 쉽고 빠르게 마이그레이션할 수 있다. shardLoader는 샤드
데이터베이스 데이터 업로드 전용 유틸리티로 사용방법은 iLoader와 유사하다.

shardLoader는 클라이언트측 샤딩 기능을 이용한 데이터 업로드 유틸리티로 데이터
노드의 수가 많을수록 업로드 속도도 향상된다.

기존의 iLoader도 사용가능 하지만, iLoader는 서버측 샤딩으로 동작하므로
shardLoader를 사용하는 것 보다는 성능이 떨어진다.

#### 다양한 분산 데이터 이동 방법 지원

샤딩 시스템을 운영하다보면, 샤드 노드의 불균형 상태가 발생할 수 있다.

-   특정 샤드 노드의 분산 데이터 집중
-   특정 샤드 노드의 읽기/쓰기 집중
-   특정 샤드 노드의 장애로 인한 교체
-   샤드 노드 증설

관리자는 이 때 데이터 분산 방법의 변경을 고려해야 한다. 데이터 분산 방법을 변경하고 데이터 이동을 위해서 다음의 두 가지 방법을 제공한다.

* 데이터 재구축 (Rebuild Data)
* 리샤딩 (Resharding)

##### 데이터 재구축 (Rebuild Data)

데이터 재구축은 샤딩 시스템의 구성을 전체적으로 점검하고 재구성 하는 방법으로
전체 샤딩 시스템의 데이터를 한번에 고려하여 재구축 할 수 있다.

이를 위해서 다음의 샤드 패키지를 제공하며, 샤드 데이터의 분산 방법을 변경 후
데이터 재구축 관련 패키지를 이용하여 데이터 점검과 이동을 할 수 있다.

- DBMS_SHARD.CHECK_DATA
- DBMS_SHARD.REBUILD_DATA
- DBMS_SHARD.REBUILD_DATA_NODE

이 샤드 패키지는 분산 정보와 데이터의 유효성을 확인하고 전체 샤딩 시스템을
고려하여 데이터를 재구축 하므로 서비스 운영중에 사용할 수 없다.

##### 리샤딩 (Resharding)

Altibase Sharding의 리샤딩이란 서비스 운영 중에 데이터 일부를 하나의 샤드
노드에서 다른 샤드 노드로 이동하는 것을 말한다.

리샤딩은 주로 노드 증설 혹은 특정 노드의 부하 집중에 따른 데이터 이동을 위하여
사용되며, 서비스 운영 중에 사용할 수 있는 장점을 가진다.

## Altibase Sharding 설치

이 장에서는 Altibase Sharding을 구성하고 사용환경을 설정하는 방법을 설명한다.

### Altibase Sharding 설치

Altibase Sharding은 별도의 설치가 필요없다.

Altibase 패키지 인스톨러를 이용하여 설치를 완료하였다면, 몇 가지 추가 설정만으로
Altibase Sharding을 사용할 수 있다. 추가 설정은 이 문서의 '*Altibase Sharding 설정*'을 참조한다.

#### 운영체제

Altibase Sharding은 현재 아래의 운영체제만 지원한다.

| OS    | CPU                          | Version         | Bit (Server) | Bit (Client) |
| ----- | ---------------------------- | --------------- | ------------ | ------------ |
| LINUX | x86-64 (GNU glibc 2.12 이상) | redhat 6.0 이상 | 64-bit       | 64-bit       |
| LINUX | PowerPC7 (BE)                | redhat 6.5 이상 | 64-bit       | 64-bit       |
| LINUX | PowerPC8 (LE)                | redhat 7.2 이상 | 64-bit       | 64-bit       |

[표 1. Altibase Sharding 지원 운영체제]

#### 데이터베이스 버전

-   Altibase : Altibase 7.2 이상

### Zookeeper 설정

#### Zookeeper 사용 환경 세팅
- Zookeeper server의 binary는 \$ALTIBASE_HOME/ZookeeperServer에 존재하며 따로 설치 할 필요는 없다.
- Zookeeper server를 사용하기 위해서는 JDK 1.8 이상 버전을 사용해야 한다.
- \$ALTIBASE_HOME/ZookeeperServer/conf에 zoo.cfg를 생성한다.(zoo_sample.cfg를 복사해 필요한 부분만 바꿔 사용해도 된다.)
  - tickTime : The number of milliseconds of each tick
  - initLimit : The number of ticks that the initial synchronization phase can take
  - syncLimit : The number of ticks that can pass between sending a request and getting an acknowledgement
  - clientPort : Zookeeper 연결을 위한 port. 다수의 Zookeeper 서버가 기본적으로는 동일한 port를 사용해야 한다.
  - server.X : Zookeeper 서버의 IP와 내부 연결 port. 모든 장비에서 동일한 순서를 사용해야 한다. server의 숫자는 최소 3개, 최대 7개로 그 외의 경우 에러가 발생한다.
    - ex) server.1=192.168.1.10:2888:3888
    -     server.2=192.168.1.11:2888:3888
    -     server.3=192.168.1.12:2888:3888
  - dataDir : Zookeeper 데이터가 저장될 path. Zookeeper server를 사용하지 않고 client만 사용할 것이라면 없어도 상관 없다.(절대 경로를 사용해야 한다.)
- Zookeeper 서버를 사용하지 않고 client로만 사용하는 경우에도 zoo.cfg 파일에서 정보를 가져온다.

#### Zookeeper server 기동
- zoo.cfg에 저장된 dataDir에 접근해 server ID명을 데이터로 가지는 myid라는 이름의 파일을 생성한다.
  - ex) 192.168.1.10 장비의 dataDir에 "1"이라는 데이터를 가지는 myid라는 파일을 생성한다.
  -     192.168.1.11 장비의 dataDir에 "2"이라는 데이터를 가지는 myid라는 파일을 생성한다.
  -     192.168.1.12 장비의 dataDir에 "3"이라는 데이터를 가지는 myid라는 파일을 생성한다.
- \$ALTIBASE_HOME/ZookeeperServer/bin의 zkServer.sh 스크립트를 사용해 서버를 띄운다.(zkServer.sh start를 수행한다.)
- zoo.cfg에 존재하는 모든 서버를 마찬가지로 띄운다.
- \$ALTIBASE_HOME/ZookeeperServer/bin의 zkCli.sh 스크립트를 사용해 정상적으로 연결되었는지 체크한다.

#### Zookeeper client 사용
- 샤드 노드들의 Altibase 서버가 Zookeeper client로 동작한다.
- SHARD DDL(alter database shard add / join / failback) 구문 사용시, 샤드 노드들의 Altibase 서버가 Zookeeper client로서 자동으로 Zookeeper server에 연결한다.
- Zookeeper server에 접속이 된 이후에는, Zookeeper server와 통신이 안될 경우, 해당 샤드노드의 알티베이스 서버가 죽는다.
- tickTime \* syncLimit 시간 이상 연결이 되지 않을 경우, 연결이 끊긴 것으로 판단한다.
- zkCli.sh : Zookeeper server에서 기본적으로 제공하는 client 프로그램으로 간단하게 데이터를 체크할 수 있다.
  - 기본적으로 zkCli.sh만 실행할 경우 localhost:2181에 연결되며 이를 변경하고 싶을 경우 -server 옵션으로 서버명(혹은 IP)와 port를 넣으면 된다.
  - [명령어 /path]의 형태로 명령을 내릴수 있으며 path는 반드시 full path여야 하며 마지막에 /가 들어가면 안된다.
  - 명령어 list
    - ls : 해당 path의 하위 path의 list를 가져온다.(값은 가져오지 않는다.)
      - watch 옵션을 줄 경우 하위 path가 추가되면 알람이 발생한다.
    - get : 해당 path의 데이터를 가져온다. 데이터가 없다면 null로 표기된다.
      - watch 옵션을 줄 경우 하위 path가 추가되면 알람이 발생한다.
    - set : 해당 path의 값을 세팅한다.
    - create : 해당 path를 생성한다. 단, 상위 path가 반드시 존재해야 한다.
      - \-e 옵션을 주면 ephemeral로 생성되어, 생성한 client와 연결이 끊기면 자동적으로 삭제된다.
    - delete : 해당 path를 제거한다. 단, 하위 path가 존재하면 실패한다.
    - deleteall : 해당 path와 하위 path를 모두 제거한다.

#### Zookeeper 사용시 주의 사항
- Zookeeper는 리눅스 외에서 사용할 수 없다.
- Zookeeper server는 절반 이상이 살아있을때만 정상작동 하며 그 이하의 서버만 살아있을 경우 절반 이상이 될때까지 client의 요청을 무시한다.
- Zookeeper의 path에는 한개의 값만 존재할 수 있다. 단, 하위 path는 다수가 존재 할 수 있다.(동일 이름은 불가능하다)
- 각 Zookeeper client는 zoo.cfg에 있는 Zookeeper server 들 중 무작위로 하나를 선택해 연결한다.

#### Zookeeper 메타
- Altibase Sharding에서 클러스터 관리를 위하여, Zookeeper 메타를 아래와 같이 관리한다.
  - (W) : watch를 걸 디렉토리
  - (E) : data 없이 비어있는 디렉토리
  - (ep) : ephemeral Node

| root path          | sub path               | 2nd sub path            | 3rd sub path                                                 | 설명                                                         |
| ------------------ | ---------------------- | ----------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| /altibase_shard(E) | /cluster_meta(E)       |                         |                                                              | 클러스터  메타                                               |
|                    |                        | /validation(E)          |                                                              | cluster의 모든 참석 노드가 동일하게 가지고 있어야 하는 값이다. 해당 값이 다를 경우 샤딩에 참여할 수 없다. |
|                    |                        |                         | /sharded_database_name                                       | DB  생성시 입력한 DB의 이름                                  |
|                    |                        |                         | /k-safety                                                    | 복사본의 수                                                  |
|                    |                        |                         | /replication_mode                                            | consistent(12) / ackwait(11) / notwait(10) 중 하나           |
|                    |                        |                         | /character_set                                               | DB 생성시 입력한 character set                               |
|                    |                        |                         | /national_character_set                                      | DB 생성시 입력한 national character set                      |
|                    |                        |                         | /binary_version                                              | 알티베이스의 binary version(sm version)                      |
|                    |                        |                         | /shard_version                                               | 알티베이스의 shard version                                   |
|                    |                        |                         | /parallel_count                                              | 이중화 복제를 처리하는 applier의 수                          |
|                    |                        |                         | /trans_TBL_size                                              | 트랜잭션 테이블의 크기                                       |
|                    |                        | /SMN                    |                                                              | 현재 정상 서비스를 제공하는 클러스터의 SMN                   |
|                    |                        | /failover_history       |                                                              | 장애 발생 기록 : 장애가 발생한 (노드 이름 : 장애 발생시 SMN )를 리스트로 관리한다. |
|                    |                        | /fault_detection_time   |                                                              | 아직  처리하지 않은 장애 중 첫 장애가 발생한 시간            |
|                    |                        | /zookeeper_meta_lock(E) | /locked(ep)                                                  | zookeeper의 클러스터 메타를 변경하는 작업을 수행시 사용하는 lock이다. lock을 잡았을 때 locked라는  path를 임시 노드로 생성한다.  lock을 잡는 노드와 해당  session의 ID를 값으로 가지며, 해당 값이 모두 동일한 대상이 lock을 잡으러 들어올 경우 lock을 잡은것으로 취급한다. |
|                    |                        | /shard_meta_lock(E)     | /locked(ep)                                                  | 샤드 메타를 변경하는 작업을 수행시 사용하는  lock이다. lock을 잡았을 때 locked라는 path를 임시 노드로 생성한다. lock을 잡는 노드와 해당 Tx의 ID를 값으로 가지며, 해당 값이 모두 동일한 대상이 lock을 잡으러 들어올 경우 lock을 잡은것으로 취급한다. |
|                    | /node_meta(E)          |                         |                                                              | 각 노드들의 메타 데이터이다. node_name별로 하위 path로 관리된다. |
|                    |                        | /node_name1(E)          |                                                              | 해당  노드의 이름(중복 불가)                                 |
|                    |                        |                         | /shard_node_id                                               | 해당 노드의 식별자 ID                                        |
|                    |                        |                         | [/node_ip:port](http://node_ipport/)                         | 해당 노드의 외부 IP 및 Port                                  |
|                    |                        |                         | [/internal_node_ip:port](http://internal_node_ipport/)       | 해당 노드의 내부 IP 및 Port                                  |
|                    |                        |                         | [/internal_replication_host_ip:port](http://internal_replication_host_ipport/) | 해당 노드의 replication 내부 IP 및 Port                      |
|                    |                        |                         | /conn_type                                                   | 해당 노드의 internal 연결 방식                               |
|                    |                        |                         | /state                                                       | add / run / shutdown / join / failover / failback 중 하나    |
|                    |                        |                         | /failoverTo                                                  | 해당 노드에 장애가 발생해  failover가 발생했을 경우 해당 노드의 데이터를 failover한  노드의 이름이다. failover가 완료된 후에 적는다.  해당 노드에  failover가 발생하지 않았을 경우나  failback이 완료된 경우에는 비어있다. |
|                    |                        | ...                     |                                                              |                                                              |
|                    | /connection_info(W)(E) | /node_name1(ep)(E)      |                                                              | 샤드노드가 접속되면, ephemeral 로 자동 생성되며, 접속이 끝어지면 자동으로 삭제된다. 어떤 샤드노드가 비정상종료하면, 삭제 이벤트가 발생하고, 이 이벤트를 다른 샤드노드들에서 감지한 후에, failover 동작이 개시된다. |
|                    |                        | /node_name2(ep)(E)      |                                                              |                                                              |
|                    |                        | ...                     |                                                              |                                                              |

### Altibase Sharding 설정

Altibase Hybrid Sharding을 위해 서버와 클라이언트의 샤딩 관련 설정은 통일성있게
적용해야 한다.

-   샤드 환경 설정
-   클라이언트 설정
    -   샤딩 응용프로그램 서버 연결 설정
    -   샤딩 응용프로그램 라이브러리 설정

#### 샤드 환경 설정

기존의 설치된 Altibase를 샤드 노드로 설정하기 위해서는 다음
과정이 필요하다.

-   프로퍼티 설정  
    SHARD_ENABLE

-   샤드 패키지 생성  
    DBMS_SHARD

##### 프로퍼티 설정 

SHARD_ENABLE 프로퍼티를 활성화한 후 서버를 재시작하면, 샤드 노드의 메타 저장소 및 코드네이터 기능이 활성화 된다.
기능이 활성화된다.

```
iSQL> SELECT name, value1 FROM v$property WHERE name = 'SHARD_ENABLE';
NAME   : SHARD_ENABLE
VALUE1 : 1
```

샤드 노드 기능이 활성화되면, 샤드 패키지를 생성하거나 샤드
관련 내장 함수, 성능 뷰를 사용할 수 있다.

##### 샤드 패키지 생성

샤드 패키지는
\$ALTIBASE_HOME/packages에 있다. 샤드 패키지는 샤드 기능을 제어할 수 있는 사용자
인터페이스를 제공한다.

```
is –f $ALTIBASE_HOME/packages/dbms_shard.sql
is –f $ALTIBASE_HOME/packages/dbms_shard.plb
```

DBMS_SHARD 패키지의 함수 및 프로시저에 대한 자세한 설명은 이 문서의 *DBMS_SHARD패키지*
설명을 참조한다.

#### 클라이언트 설정

##### 샤딩 응용프로그램 서버 연결 설정

접속할 샤드노드의 우선순위가 있는 경우는, 해당 우선순위에 맞춰서, 기본 ip/port 및 AlternateServers를 설정한다.

접속할 샤드노드의 우선순위가 없는 경우는, LoadBalance=on을 설정한다. 그러면, 기본 ip/port 및 AlternateServers 에 설정된 샤드노드들에 대하여, 랜덤하게 접속한다.

##### 샤딩 응용프로그램 라이브러리 설정

###### ShardCLI

ShardCLI는 CLI 응용프로그램을 하이브리드 샤딩으로 동작할 수 있도록 하는 기능이다.

CLI 응용프로그램 빌드 시 기존의 ODBCCLI 라이브러리를 ShardCLI 라이브러리로 바꾸어야 한다.

ShardCLI 라이브러리는 libshardcli.a와 libshardcli_sl.so 두 개의 파일을 지원한다.

###### ShardJDBC

ShardJDBC는 JDBC 응용프로그램을 하이브리드 샤딩으로 동작할 수 있도록 하는 기능이다.

JDBC는 별도의 샤딩 라이브러리가 존재하는것은 아니고, JDBC 접속 URL에 sharding prefix를 붙여주면 ShardJDBC 로 동작한다.

###### 그외 API

ShardCLI와 ShardJDBC를 제외한 API를 사용하는 경우는 서버측 샤딩으로만 동작한다. 

### 샤드 메타 설정

Sharding을 사용하기 위해서는 샤드 메타를 모든 샤드 노드에 생성해 주어야 한다.

샤드 메타 설정은 DBMS_SHARD 패키지를 이용한다.

#### 샤드 메타(Shard meta) 생성

샤드 패키지인 DBMS_SHARD 패키지에는 샤드 메타를 생성하는 서브 프로그램이 포함되어 있다. 최초 한번만 수행하면 샤드 메타가 생성된다. 

샤드 노드에서 샤드 메타 및 코디네이터를 활성화 하기 위해서 샤드 노드 식별자를 샤딩 시스템에서 유일한 값으로 지정해야 한다.

##### 구문

```
DBMS_SHARD.CREATE_META()
```

##### 설명

샤드 메타는 sys 사용자로 생성해야 한다. 샤드 메타를 생성하는 내부 과정은 다음과
같이 처리한다.

sys_shard 사용자를 생성한다.

sys_shard.version\_ 테이블을 생성하고, 현재 shard version을 입력한다.

sys_shard.local_meta_info_ 와 sys_shard.global_meta_info_ 테이블을 생성하고 샤드 메타 정보를 입력한다.

sys_shard.nodes_ 테이블과 인덱스를 생성한다.
 sys_shard.objects_ 테이블과 인덱스를 생성한다.
 sys_shard.ranges_ 테이블과 인덱스를 생성한다.
 sys_shard.clones _ 테이블과 인덱스를 생성한다.
 sys_shard.solos_ 테이블과 인덱스를 생성한다.
 sys_shard.replica_sets_ 테이블과 인덱스를 생성한다.
 sys_shard.failover_historys_ 테이블과 인덱스를 생성한다.

샤드 메타 생성 구문에 대한 자세한 설명은 DBMS_SHARD 패키지의 CREATE_META 을 참조한다.

##### 예제

\<질의\> 샤드 메타를 생성한다.

```
iSQL> EXEC DBMS_SHARD.CREATE_META();
```

#### 샤드 메타 관리

샤드 메타는 전체 샤딩 시스템의 분산 정보를 가지고 있으며 각 노드에서 샤드 메타 정보를 통해 데이터의 위치를 판단하여 질의를 분석하고 처리한다. 그러므로, 모든 샤드 노드에서 동일한 샤드 메타를 유지해야 한다.

또한, 샤드 메타는 시점 별로 다른 버전을 가질 수 있어서 이에 대한 형상 관리를 수행한다. 그러므로, 샤드 메타의 변경은 모든 노드에 동일하게 수행되어야 한다.

#### 샤드 메타 형상

SMN이란 샤드 메타의 분산 정의 변경 이력 번호 이며, 시스템 내부적으로 관리된다.

분산 정의 변경은 노드 등록/제거, 샤드 객체 등록/제거 등의 변경을 말한다.

좀 더 쉽게 설명하면 초기 상태의 샤드 메타는 SMN은 1이며, 노드를 추가하여 샤드 메타에 신규 정보가 추가되고 트랜잭션이 완료되면 새로운 샤드 메타 변경 이력은 SMN 2가 된다.

SMN은 다음의 세 가지 유형의 SMN이 존재한다. 

* Meta SMN
  * 샤드 메타가 유지하는 샤드 메타 변경 이력 중 가장 최신의SMN

* Data SMN 
  * 데이터의 형상이 어떤 버전의 샤드 메타 기준으로 되어있는지에 대한 SMN

* Session SMN
  * 개별 세션이 인식하고 있는 SMN

다음과 같은 샤드 메타의 변경을 유발하는 샤드 노드 설정은 샤드 메타에 변경 이력이 Meta SMN과 함께 저장된다.

Meta SMN의 변경은 실제 Altibase Sharding 시스템에서 인식하지 않으며 각 노드에서 샤드 메타 적용 구문(ALTER SYSTEM RELOAD SHARD META NUMBER LOCAL)을 통해 Data SMN을 변경하여 이후의 작업들이 변경된 SMN을 기준으로 동작할 수 있도록 해야한다. 

각 세션은 최초 접속 시에 Data SMN을 자신의 Session SMN으로 할당받아 수행한다.

샤드 메타 적용 구문이 수행되어 Data SMN이 변경되면 이전에 접속한 세션은 각각 자신의 접속 시점에 유지되던 Session SMN을 기준으로 샤딩 서비스를 수행하며 이를 보정해 주기 위해서 서버 내부에서 SMN 차이를 보정해 주는 코디네이터가 동작한다.

Session SMN은 해당 세션이 트랜잭션을 COMMIT하는 시점에 이전 Session SMN과 Data SMN을 비교하여 다른 경우 최신 Data SMN으로 갱신한다.

```
SMN 변경 예제>
iSQL> AUTOCOMMIT OFF;
iSQL> EXEC DBMS_SHARD.SET_NODE(‘node1’,‘192.168.1.10’,20300);
iSQL> EXEC DBMS_SHARD.SET_NODE(‘node2’,‘192.168.1.11’,20300, ‘192.168.1.101’,20300);
iSQL> COMMIT;
iSQL> ALTER SYSTEM RELOAD SHARD META NUMBER LOCAL;
iSQL> COMMIT;
```

### 디렉토리

Altibase Sharding 의 환경 설정에 관한 디렉토리는 Altibase 서버와 동일하다.

본 장에서는 Altibase Sharding 의 추가적인 내용만을 설명한다.

#### trc 디렉토리

altibase_sd.log

샤드 관련 경고 메시지나 트레이스 메시지 등이 기록되는 파일들이다.

## Altibase Sharding 사용

이 장에서는 Altibase Sharding 사용 방법을 자세히 설명한다. 앞에서 설명한 샤드 노드
설정과 샤드 패키지 생성 과정 이후의 사용 방법을 기술한다.

### Altibase Sharding 제약사항

#### 기본 조건

-   샤드 노드들은 샤드 메타 및 샤드 관련 객체들의 스키마 정보가 동일해야 한다.

#### 프라퍼티 제약조건
-   ISOLATION_LEVEL은 0(read committed)만 지원한다.
-   AUTO_COMMIT은 0(non-autocommit)만 지원한다.

#### 데이터 제약조건
-   샤드 테이블은 기본 키가 있어야 한다.
-   샤드 키 테이블에서 기본 키는 샤드 키를 포함하여야 한다. 그리고, 기본 키에서 샤드 키가 순서상 앞에 있어야 한다.
-   샤드 키 테이블에서 기본 키 이외의 유니크 속성을 갖는 컬럼은 개별 샤드 노드별로만 유니크가 보장된다. 샤딩 시스템 전역으로 유니크 검사를 하지는 않는다.
-   global non-partitioned index를 지원하지 않는다.
-   global secondary index를 지원하지 않는다.
-   geometry 컬럼, 암호화 컬럼과 압축 컬럼을 지원하지 않는다.  
-   샤드 테이블에 대한 변경 가능 뷰(Updatable View)는 갱신할 수 없다.
-   materialized view를 지원하지 않는다.
-   이 외의 쿼리에 대한 제약사항은 샤드 쿼리 절을 참고한다.

#### 연결 제약조건
-   샤드 전용 클라이언트 라이브러리를 사용하여야 하이브리드 샤딩방식이 적용된다. 샤드 전용 클라이언트 라이브러리를 사용하지 않으면 서버측 샤딩방식으로만 동작한다.
    - 샤드 전용 클라이언트 라이브러리는 ShardCLI와 ShardJDBC 두가지만 제공한다.
-   다중-쓰레드(multi-thread) 클라이언트 프로그램에서 데이타베이스 커넥션 공유를 지원하지 않는다.
-   SSL 을 지원하지 않는다.
-   IPv6 를 지원하지 않는다.
-   ShardCLI 제약사항은 CLI User's Manual 에서 ShardCLI 부분을 참고한다.
-   ShardJDBC 제약사항은 JDBC User's Manual 에서 Sharding 부분을 참고한다.

#### K-safety 가 1 이상에서의 제약조건
-   단일 샤드 키 테이블만 지원한다.
-   샤드 키 테이블은 분산 방식에 대응되는 파티션드 테이블(partitioned table)로 생성해야 하며 파티션 키와 샤드 키는 동일해야한다.
    - 각 파티션의 경계는 분산 경계를 포함해야 한다.
-   Altibase Sharding은 응용프로그램에서 데이터베이스로 커넥션을 생성할 때, 일부
    샤드 노드에서 장애가 발생하면 이를 에러로 처리하고 커넥션 생성이 실패한다.  
    (jdbc같은 경우 응용프로그램에서 데이터베이스로 커넥션을 생성할 때 META와의 접속까지만 
    이루어지기 때문에 노드 장애여부와 상관없이 META만 정상적이라면 커넥션이 생성된다.)

#### 하위 호환성

-   샤드 기능은 하위 호환성을 갖지 않는다. 샤드 버전이 동일한 서버, 클라이언트에 대해서만 샤드 기능을 사용할 수 있다.
-   샤드 버전은 다음과 같이 확인할 수 있다.

```
$ALTIBASE_HOME/bin/altibase -v
```
### Altibase Sharding 통신 방법
샤딩에서 사용하는 커넥션에 따라 지원하는 통신 방법은 다음과 같다.

#### 사용자 커넥션(User Connection)
사용자 커넥션 스트링의 CONN_TYPE 속성에 해당하며 Altibase 에서 제공하는 통신방법과 동일하다.
자세한 내용은 *Administrator manual*의 서버/클라이언트 통신 장을 참고한다.

#### 샤드 라이브러리 커넥션(Shard Library Connection)
샤드 라이브러리 커넥션의 통신 방법으로 사용자 커넥션 스트링의 SHARD_CONNTYPE 속성에 해당하며 다음의 통신 타입을 지원한다.
SHARD_CONNTYPE 을 명시하지 않을 경우 TCP 를 기본값으로 동작한다.
- 1: TCP (기본값)
- 8: IB (InfiniBand)

#### 코디네이터 커넥션(Coordinator Connection)
코디네이터와 샤드노드의 내부 커넥션 통신 방법으로 노드 설정시 지정 가능하며 다음의 통신 타입을 지원한다.
노드 설정의 인자로 명시하지 않을 경우 TCP 를 기본값으로 동작한다.
- 1: TCP (기본값)
- 8: IB (InfiniBand)

### 샤드 노드

Altibase Sharding을 사용하기 위하여 각 샤드 노드에 샤딩 관련 정보를 설정해야 한다.

샤딩 관련 메타 정보는 지역 샤드 노드 정보(SYS_SHARD.LOCAL_META_INFO_)를 제외하고는 모두 동일하게 유지해야 한다.

샤딩 시스템을 최초로 구성하거나 노드를 추가하기 위해서는 지역 샤드 노드의 정보를 설정한 후 모든 노드에 동일한 순서로 전체 샤드 노드 설정 과정을 거치거나 aexport 등을 이용해 복제하여, 샤드 메타 정보를 동일하도록 유지해야 한다.

샤드 노드 설정을 전역적으로 적용하기 위해서 샤드 매니저를 사용하는 것을 권장한다.

수동으로 설정 하는 경우 가용 노드를 포함한 모든 샤드 노드에서 동일한 설정 작업을 수행하고 작업의 완료를 알리기 위해서 샤드 메타 적용 구문(ALTER SYSTEM RELOAD SHARD META NUMBER LOCAL)을 수행해야 한다.

```
iSQL> AUTOCOMMIT OFF;
iSQL> EXEC DBMS_SHARD.SET_NODE(‘node1’,‘192.168.1.10’,20300);
iSQL> EXEC DBMS_SHARD.SET_NODE(‘node2’,‘192.168.1.11’,20300,
‘192.168.1.101’,20300);
iSQL> COMMIT;
iSQL> ALTER SYSTEM RELOAD SHARD META NUMBER LOCAL;
```

#### 샤드 노드 관련 메타 작업 주의 사항

샤드 메타를 생성하거나 샤드 노드 관련 정보를 변경하는 작업은 샤딩 시스템 전반에 영향을 미치므로 아래 주의사항을 숙지하고 진행하도록 한다. 

* 샤드 메타 생성 및 샤드 노드 관련 정보 변경 전에 접속한 연결에 대해서는 정상적인 샤딩 서비스를 이용할 수 없으므로 
  샤드 메타 생성 및 샤드 노드 관련 정보 변경 후 재접속해야 한다. 
* 샤드 메타 생성 및 샤드 노드 관련 정보 변경을 위해 사용한 연결은 변경 완료 후 종료해야 한다.
* 샤드 메타 생성 및 샤드 노드 관련 정보 변경 관련 작업은 샤딩 시스템 운영전에 완료해야 한다.

#### 지역 사드 노드 설정 

샤드 패키지인 DBMS_SHARD 패키지에는 지역 샤드 노드의 정보를 설정하는 서브 프로그램을 제공한다.

샤드 노드를 사용하기 위해서는 먼저 지역 샤드 노드의 정보를 등록해야한다. 

##### 구문

```
DBMS_SHARD.SET_LOCAL_NODE( shard_node_id in integer,
                           node_name in varchar(10),
			   host_ip in varchar(64),
			   port_no in integer,
			   internal_host_ip in varchar(64),
			   internal_port_no in integer,
                           internal_replication_host_ip in varchar(64),
                           internal_replication_port_no in integer,
                           conn_type in integer default NULL );
```

##### 설명

지역 노드를 샤드 노드로 사용하기 위해서 지역 샤드 노드의 정보를 입력한다.  

필수 적으로 입력되어야 하는 값은 다음과 같다. 

shard_node_id:  지역 샤드 노드의 샤드 노드 식별자로 전체 시스템에서 유일해야한다. 

node_name: 지역 샤드 노드에서 사용할 노드 이름을 입력하며, 샤드 노드 이름도 전체 시스템에서 유일해야한다. 

host_ip: 지역 샤드 노드에서 서비스에 사용할 호스트 IP를 입력한다. 

port_no: 지역 샤드 노드에서 서비스에 사용할 Port를 입력한다. 

internal_host_ip: 지역 샤드 노드에서 코디네이터가 내부적으로 사용할 호스트 IP를 입력한다. 이더넷 및  인피니 밴드를 지원한다.

internal_port_no: 지역 샤드 노드에서 코디네이터가 내부적으로 사용할 Port를 입력한다. 

internal_replication_host_ip: 지역 샤드 노드에서 내부 복제용으로 사용할 호스트 IP를 입력한다. internal_host_ip와 동일한 라인을 사용할 것을 권장한다. 

internal_replication_port_no: 지역 샤드 노드에서 내부 복제용으로 사용할 Port로 REPLICATION_PORT_NO 프로퍼티 값과 동일한 값을 입력해야한다. 

conn_type: 내부적으로 사용되는 코디네이터 연결 방식으로 입력하지 않는 경우 TCP를 사용한다. 그 외 지원 타입은 *Altibase Sharding 통신 방법*의 코디네이터 커넥션을 참고한다.

##### 예제

\<질의\> 샤드 노드 식별자가 0인 'NODE1' 이름을 갖는 지역 샤드 노드의 정보를 등록한다. 

```
iSQL> EXEC DBMS_SHARD.SET_LOCAL_NODE(0, 'NODE1', '192.168.1.10', 20300, '192.168.1.11', 20300, '192.168.1.10', 30300 );
```

#### 샤드 복제 정보 설정

샤딩 클러스터 시스템은 무중단 서비스를 위해서 이중화를 사용하여 데이터 복제를 지원한다. 샤딩 클러스터 시스템을 사용하기 위해서는 전체 샤딩 클러스터 시스템에서 사용할 이중화 방식을 설정해야한다. 

이 설정은 전체 시스템 내에서 최초로 등록되는 노드에서 지정되어야 한다. 

##### 구문

```
DBMS_SHARD.SET_REPLICATION( k_safety         in  integer,
                            replication_mode in  varchar(10) default NULL,
                            parallel_count   in  integer default NULL );
```

##### 설명

샤딩 클러스터 시스템에서 사용할 복제 정보를 입력한다.   

k_safety: 시스템 내에서 유지할 복제본의 개수를 지정한다.  0, 1, 2를 지원하며 '0'으로 설정하면 이중화를 사용하지 않는다.

replication_mode: 'CONSISTENT', 'NOWAIT' 의 두 가지 모드를 지원하며, 'CONSISTENT' 는 동기 모드로 COMMIT시 복제본에도 로그가 기록된 것을 확인하고 반환하여 일부 성능 저하가 발생할 수 있으나 복제본의 데이터 일관성을 보장한다.  'NOWAIT'은 비동기 모드로 복제 처리가 서비스 트랜잭션에 영향을 주지 않아 성능이 우수하다. 다만, 복제본의 데이터는 손실이 발생하거나 일관성이 깨질 수 있다. 

parallel_count: 샤딩 클러스터 시스템은 데이터 복제를 위해서 Altibase 이중화 기술을 사용한다. 이 때, 사용할 이중화 병렬 적용자의 수를 지정한다. 지정하지 않는 경우 1로 설정된다. 이중화 병렬 적용자에 대한 자세한 내용은 *'Altibase Replication Manual을 참고한다'*

##### 예제

\<질의\> 샤딩 클러스터 시스템에서 2개의 복제본을 유지하고 동기복제 방식을 사용하도록 설정한다.

```
iSQL>  EXEC DBMS_SHARD.SET_REPLICATION(2,'consistent', 1);
```

#### 샤드 노드 식별자 재설정

샤드 노드의 샤드 노드 식별자를 재설정한다.

##### 구문

```
DBMS_SHARD.RESET_SHARD_NODE_ID( SHARD_NODE_ID in integer )
```

##### 설명

샤드 노드에서 샤드 노드 식별자를 변경하고자 하는 경우 사용한다.

샤드 노드 식별자 설정 구문에 대한 자세한 설명은 DBMS_SHARD 패키지의 *RESET_SHARD_NODE_ID*를 참조한다.

##### 예제

\<질의\> 샤드 노드 식별자를 2로 변경한다. 

```
iSQL> EXEC DBMS_SHARD.RESET_SHARD_NODE_ID(2);
```

#### 샤드 노드 추가

샤드 패키지인 DBMS_SHARD 패키지에는 샤드 노드를 추가하는 서브 프로그램을
제공한다. 샤드 노드를 추가하기 위해서는 샤드 패키지를 생성해야 한다.

##### 구문

```
DBMS_SHARD.SET_NODE
```

##### 설명

샤드 노드를 추가한다. 필요에 따라 alternate 샤드 노드를 추가할 수 있다. 샤드
노드 이름의 대소문자는 구별하지 않는다.

현재 ip address는 ip v4형식만 지원한다.

##### 예제

```
iSQL> EXEC DBMS_SHARD.SET_NODE(‘node1’,‘192.168.1.10’,20300);
iSQL> EXEC DBMS_SHARD.SET_NODE(‘node2’,‘192.168.1.11’,20300, ‘192.168.1.101’,20300);
iSQL> SELECT * FROM sys_shard.nodes_;
```

#### 샤드 노드 삭제

샤드 패키지인 DBMS_SHARD 패키지에는 샤드 노드를 삭제하는 서브 프로그램을
제공한다.

##### 구문

```
DBMS_SHARD.UNSET_NODE
```

##### 설명

추가한 샤드 노드를 삭제한다.

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

샤드 객체 설정을 전역적으로 적용하기 위해서 샤드 매니저를 사용하는 것을
권장한다.

수동으로 설정 하는 경우 가용 노드를 포함한 모든 샤드 노드에서 동일한 설정 작업을
수행하고 작업의 완료를 알리기 위해서 샤드 메타 적용 구문(ALTER SYSTEM RELOAD
SHARD META NUMBER LOCAL)을 수행해야 한다.

```
iSQL> AUTOCOMMIT OFF;
iSQL> EXEC DBMS_SHARD.SET_SHARD_TABLE(‘user1’,‘t1’,‘h’,‘i1’,‘node1’);
iSQL> EXEC DBMS_SHARD.SET_SHARD_TABLE(‘user1’,‘t2’,‘r’,‘i1’,‘node1’);
iSQL> COMMIT;
iSQL> ALTER SYSTEM RELOAD SHARD META NUMBER LOCAL;
```

> 주의 사항
>
> * 샤드 객체 설정은 데이터의 이동을 수반하지 않는다. 데이터 이동 관련 내용은 *"리샤딩"*을 참고한다. 

#### 샤드 테이블 생성

샤드 테이블을 설정하기 위해서 먼저 각 샤드 노드에 테이블이 생성되어 있어야 한다.

샤드 테이블은 단일 샤드 키 분산 테이블과 복합 샤드 키 분산 테이블, 복제 분산
테이블 그리고 독립 분산 테이블이 있다.

복제 분산 테이블과 독립 분산 테이블 그리고 복합 샤드 키 분산 테이블은 Altibase의
일반 테이블 생성과 동일하며, 모든 샤드 노드에 동일한 스키마의 테이블을 생성한다.
단일 샤드 키 분산 테이블은 샤드 키 컬럼을 파티션 키로 하여 파티션드 테이블로
생성해야한다.

단일 샤드 키 분산 테이블은 분산 방식에 따라 각 샤드 테이블 유형에 대응되는
파티션드 테이블을 생성해야 한다.

| 샤드 테이블        | 파티셔닝 방법    |
| ------------------ | ---------------- |
| 해시 분산 테이블   | RANGE_USING_HASH |
| 범위 분산 테이블   | RANGE            |
| 리스트 분산 테이블 | LIST             |

[표 2]. 단일 샤드 키 분산 테이블 별 파티셔닝 방법

[표 2]에 나타난 것과 같이 해시 분산 테이블의 경우 RANGE_USING_HASH, 범위 분산
테이블의 경우 RANGE 그리고 리스트 분산 테이블의 경우 LIST 파티션드 테이블로
생성해야 하며, 파티션 키와 샤드 키는 동일한 컬럼을 사용해야 한다.

테이블 생성시 파티션의 범위는 분산 범위와 동일하거나 노드 확장을 위해서 더
세부적으로 지정하는 것을 추천한다.

만약 샤드 노드 2개를 사용하며 해시로 분산하며 향후 샤드 노드 2개를 더 추가할
계획을 가지고 있다면 4개의 파티션을 생성하는 것이 노드 추가 및 데이터 이동 시
유리하다.

##### 구문

CREATE TABLE

##### 설명

샤드 테이블을 생성한다. CREATE TABLE에 대한 자세한 내용은 *SQL Reference*를
참고한다.

##### 예제

```
iSQL> CREATE TABLE T1(I1 INTEGER PRIMARY KEY, I2 CHAR(10))
PARTITION BY RANGE_USING_HASH ( I1 )
(
 PARTITION P1 VALUES LESS THAN (250),
 PARTITION P2 VALUES LESS THAN (500),
 PARTITION P3 VALUES LESS THAN (750),
 PARTITION P4 VALUES DEFAULT
 );
Create success.

iSQL> CREATE TABLE T2(I1 CHAR(10) PRIMARY KEY, I2 CHAR(100));
Create success.
```

#### 샤드 테이블 설정

테이블을 샤드 테이블로 설정한다. 샤드 노드에 미리 생성되어 있는 테이블에 샤드
설정을 추가한다.

샤드 설정 후, 샤드 쿼리를 수행하기 위하여 모든 샤드 노드에 동일한 스키마의
테이블이 생성되어 있어야 한다. DBMS_SHARD 패키지는 샤드 테이블을 추가하는 서브
프로그램을 제공한다.

##### 구문

```
DBMS_SHARD.SET_SHARD_TABLE
DBMS_SHARD.SET_SHARD_TABLE_COMPOSITE
```

##### 설명

샤드 테이블을 설정한다. 샤드 테이블 설정 구문에 대한 자세한 설명은 DBMS_SHARD
패키지의 *SET_SHARD_TABLE* 또는 *SET_SHARD_TABLE_COMPOSITE*를 참조한다.

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
파라미터 값으로 샤드 노드를 선택하여 선택된 노드에서 프로시저가
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

본 장에서는 각 분산 방식에 대해 수동으로 설정하는 방법을 설명한다.

분산 정보 설정을 전역적으로 적용하기 위해서 샤드 매니저를 사용하는 것을
권장한다.

수동으로 설정 하는 경우 가용 노드를 포함한 모든 샤드 노드에서 동일한 설정 작업을
수행하고 작업의 완료를 알리기 위해서 샤드 메타 적용 구문(ALTER SYSTEM RELOAD
SHARD META NUMBER LOCAL)을 수행해야 한다.

```
iSQL> AUTOCOMMIT OFF;
iSQL> EXEC DBMS_SHARD.SET_SHARD_HASH(‘user1’,‘t1’,300,‘node1’);
iSQL> EXEC DBMS_SHARD.SET_SHARD_HASH(‘user1’,’‘t1’,600,‘node2’);
iSQL> EXEC DBMS_SHARD.SET_SHARD_HASH(‘user1’,’‘t1’,1000,‘node3’);
iSQL> COMMIT;
iSQL> ALTER SYSTEM RELOAD SHARD META NUMBER LOCAL;
```

> 주의 사항
>
> * 분산 설정은 데이터의 이동을 수반하지 않는다. 데이터 이동 관련 내용은 *"리샤딩"*을 참고한다. 

#### 해시(Hash) 분산 설정

해시 분산은 샤드 키 값을 hash하여 분산하는 방식이다.

Altibase Sharding은 hash 값을 0부터 999까지 1000개의 hash group으로 관리한다.

Hash group 0부터 299까지는 node1에 저장하고, hash group 300부터 599까지는
node2에 저장하고, hash group 600부터 999까지는 node3에 저장할 경우 다음과 같이
분산 정의한다.

-   hash_group[\<300] -\> node1
-   hash_group[\<600] -\> node2
-   hash_group[\<1000] -\> node3

만일 기본 샤드 노드가 node3으로 정의되어 있다면 마지막 정의는 생략해도
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

-   shard key value \< ‘H’ 경우 –\> node1
-   ‘H’ \<= shard key value \< ‘T’ 경우’ –\> node2
-   ‘M’ \<= shard key value \< ‘Z’ 경우 –\> node3

샤드 키 값이 NULL인 경우 만약 기본 샤드 노드가 정의되지 않았다면 에러가 발생하게
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

이 때 ‘서울’, ‘부산’, ‘대구’ 외의 샤드 키 값은 기본 샤드 노드에 저장된다. 만약
기본 샤드 노드가 정의되지 않았다면 에러가 발생한다.

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
상태를 의미한다. 복제 분산을 적용하는 샤드 객체는 샤드 키가 필요없고 복제될 샤드
노드만 지정한다.

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

> 주의 사항
>
> * 복제 분산 테이블로 설정 이후에 들어온 DML에 대해서 복제된다. 
> * 장애가 발생한 노드의 데이터의 동기화는 자동으로 이뤄지지 않으므로 장애 복구후 데이터 동기화는 수동으로  수행해야한다. 

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

#### 파티션(Partition) 기반 분산 설정

파티션 기반 분산 설정은 샤드 테이블의 파티션 정보를 이용하여 테이블의 파티셔닝 방식에 맞춰 자동으로 샤드 분산 방식을 설정해 준다. 파티션 기반 분산을 적용하는 샤드 객체는 샤드 키 값 대신 테이블의 파티션을 지정한다.

##### 구문

```
DBMS_SHARD.SET_SHARD_PARTITION_NODE
```

##### 설명

샤드 테이블의 파티셔닝 방식을 이용하여 자동으로 샤드 테이블 분산정보를 설정한다.

##### 예제

user1 사용자의 t1은 파티션드 테이블로 설정되어 있다고 가정한다.

```
iSQL> EXEC DBMS_SHARD.SET_SHARD_PARTITION_NODE(‘user1’,‘t1’,'p1',‘node1’);
iSQL> EXEC DBMS_SHARD.SET_SHARD_PARTITION_NODE(‘user1’,‘t1’,'p2',‘node2’);
iSQL> EXEC DBMS_SHARD.SET_SHARD_PARTITION_NODE(‘user1’,‘t1’,'p3',‘node3’);
iSQL> SELECT * FROM sys_shard.ranges_;
```

> 주의 사항
>
> * 파티션 기반 분산 설정은 단일 샤드 키 분산 설정에만 사용할 수 있다.
> * 파티션 기반 분산 설정은 일반 테이블 대상으로는 수행 할 수 없다. 파티션드 테이블 대상으로만 수행 하여야 한다.

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

샤드 키의 설정에 대한 설명은 이 장의 '샤드 객체'를 참고한다.

### 샤드 트랜잭션

Altibase Sharding은 분산된 여러 데이터베이스를 다루게 되므로 이에 대한 트랜잭션
처리가 필요하다. Altibase Sharding에서 다루는 여러 데이터베이스에 대한
트랜잭션을 다음과 같이 구분한다.

-   다중 노드 트랜잭션 (multiple node transaction)

#### 다중 노드 트랜잭션

Altibase Sharding에서 ACID는 보장하지는 않지만, 여러 샤드 노드에 대한
트랜잭션을 허용하는 트랜잭션을 말한다.

Altibase Sharding에서 트랜잭션을 시작할 때 다중 노드 트랜잭션을 선언하면 여러
샤드 노드에 모두 쿼리를 수행할 수 있다. 트랜잭션의 커밋, 롤백은 모든 샤드 노드로
순차적으로 수행된다.

커밋 또는 롤백 시 샤드 노드에 장애가 발생한 경우, 샤드 라이브러리는 그 즉시
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
Attribute에는 ALTIBASE_GLOBAL_TRANSACTION_LEVEL을 ValuePtr에는 ALTIBASE_MULTIPLE_NODE_TRANSACTION을 입력한다.
SQLSetConnectAttr에 대한 자세한 설명은 “*CLI User's Manual \> 2. Altibase CLI
함수”*를 참조한다.  
jdbc같은 경우 CLI의 SQLSetConnectAttr이 없기 때문에 연결속성의 형태로 지원한다.

##### 예제
###### ShardCLI

```
SQLSetConnectAttr(dbc, ALTIBASE_GLOBAL_TRANSACTION_LEVEL, (void*)ALTIBASE_MULTIPLE_NODE_TRANSACTION, 0);
```
###### ShardJDBC

```
DriverManager.getConnection("jdbc:sharding:Altibase://ip_address:port/mydb?shard_transaction_level=1");
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

Insert 값에 따라 단일 샤드 노드에서 수행하는 샤드 쿼리는 다음과 같다.

-   INSERT INTO s1(k1, i1) VALUES(?, 2);

-   INSERT INTO so1(i1) VALUES(?);

샤드 키 분산 테이블에 INSERT를 수행하는 경우 샤드 키에 해당하는 값에 수식이
있거나, 시퀀스, 또는 서브 쿼리가 있을 수 있다. 이 때 샤드 코디네이터가 그 값을 미리
계산한 후에 해당 노드로 전달한다.

-   INSERT INTO s1(i1, i2) VALUES(?+1, 2)

-   INSERT INTO s1(i1, i2) VALUES(seq1.nextval, 2)

-   INSERT INTO s1(i1, i2) VALUES((SELECT 1 FROM dual), 2)

여러 노드에 걸쳐 있는 복제 분산 테이블의 경우 다중 노드에 수행한다.

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

> ##### 제약 사항
>
> - 다중 테이블 삽입절은 사용할 수 없다.
> - 다중 로우 삽입절은 사용 할 수 없다.

#### INSERT SELECT

Insert select문은 항상 다중 노드 수행 쿼리이므로 내부 커넥션으로 수행된다.Insert
select문을 이용하면 다른 분산 테이블에 데이터를 복사할 수 있다.

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

조건절에 따라 UPDATE 문을 단일 노드 수행 쿼리와 다중 노드 수행
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

조건절에 따라 DELETE 문을 단일 노드 수행 쿼리와 다중 노드 수행
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
샤드 키에 해당하는 노드로 샤드 라이브러리 커넥션을 생성하여 해당 노드에 직접
수행한다. 하지만 샤드 키 필터를 적용하지 않을 경우 내부 커넥션을 생성하여 모든
노드에 수행한 후 샤드 코디네이터가 그 결과를 취합하여 사용자에게 전달한다.

-   SELECT \~ FROM s1, s2 WHERE s1.k1 = s2.k1 AND [s1.k1\|s2.k1] = ?  
    =\> 샤드 라이브러리 커넥션으로 특정 노드에 직접 수행

-   SELECT \~ FROM s1, s2 WHERE s1.k1 = s2.k1 AND [s1.i1\|s2.i1] = ?  
    =\> 내부 커넥션으로 모든 노드를 수행하고 취합 후 전달 받음

복제 분산 테이블(c1)의 경우 모든 샤드 테이블(s1,c1,so1)에 대해 inner join을
지원한다.

-   SELECT \~ FROM *c1, s1* WHERE *c1.i1 = s1.i1*

-   SELECT \~ FROM c1, so1 WHERE c1.i1 = so1.i1

독립 분산 테이블(so1)과 복제 분산 테이블(c1)의 inner join시 특정 노드를
지정하는 독립 분산 테이블(so1)의 특성상 필터의 유무와 무관하게 샤드 라이브러리 커넥션으로
동작한다.

- SELECT \~ FROM *c1, so1* WHERE *c1.i1 = so1.i1*

  =\> 샤드 라이브러리 커넥션으로 특정 노드로 직접 수행


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

-   SELECT \~ FROM *s1* RIGHT OUTER JOIN *c1* ON *c1.i1 = s1.i1* WHERE *s1.i1 = 1*
    

=\> SELECT \~ FROM *s1* INNER JOIN *c1* ON *c1.i1 = s1.i1* WHERE *s1.i1 = 1*
    

###### Semi- join

동일한 샤드 키 분산 방식이 적용된 샤드 테이블(s1,s2)간의 semi-join을 지원한다.

-   SELECT \~ FROM *s1* WHERE *EXISTS* (SELECT \~ FROM *s2* WHERE *s1.k1 = s2.k1* AND \~) AND \~

복제 분산 테이블(c1)의 경우 모든 샤드 테이블에 대해 semi-join을 지원한다.

-   SELECT \~ FROM c1 WHERE *EXISTS* (SELECT \~ FROM *s1* WHERE *c1.i1 = s1.i1* AND \~) AND \~
    
-   SELECT \~ FROM s1 WHERE *EXISTS* (SELECT \~ FROM *c1* WHERE *c1.i1 = so1.i1* AND \~) AND \~

##### Aggregate function

Altibase Sharding 은 샤드 테이블에 대해 아래 집계 함수를 지원한다.

-   COUNT

-   MIN

-   MAX

-   SUM

-   AVG

-   STDDEV

-   VARIANCE

샤드 키 분산 테이블의 경우 분산 데이터의 특성상 노드 각각에 대해 집계를
수행하므로 그 결과는 모든 데이터의 집계 결과와 논리적으로 같을 수 없다. 따라서
샤드 키 분산 테이블(s1)의 경우 샤드 키 컬럼으로 필터링 되는 경우에 한해
지원한다.

-   SELECT *count(\*)* FROM *s1* WHERE *k1 = ?* \~

-   SELECT *sum(k1)* FROM *s1* WHERE *k1 = ?* \~

특정 샤드 노드에서 동작하는 복제 분산 테이블(c1)과 독립 분산 테이블(so1)은
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

특정 노드에서 동작하는 복제 분산 테이블(c1)과 독립 분산 테이블(so1)은
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

Altibase Sharding 은 샤드 테이블을 포함하는 subquery 유형을 지원한다.

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

-   SELECT \* FROM *c1 a* WHERE a.i1 = (SELECT min(i1) FROM *c1* WHERE i1 = a.i1)

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

사용자는 특정 노드의 현재 데이터 상태를 확인하거나 특정 노드의 데이터를 취합하는 것을 원할 수 있다.

Altibase Sharding은 사용자의 요구사항을 처리하기 위해 샤드 메타, 코디네이터 또는 샤드 데이터(저장소) 역할로 특정 샤드 노드에 쿼리를 전송하고 그 수행 결과를 취합할 수 있는 샤드 키워드를 제공하며 iSQL 을 통해 사용 가능하다.

#### 구문

샤드 키워드는 다음 구문에 한해 제공하며 구문식은 다음과 같다.

-   SHARD
    - INSERT, UPDATE, DELETE
    - SELECT
-   NODE[META]
    - INSERT, UPDATE, DELETE
    - SELECT
-   NODE[DATA | DATA() | DATA('*node1_name'*, '*node2_name'*...)]
    - SELECT

![](media/Sharding/79bcb8f6b5cb10cc7a7b816363aa709f.jpg)

**shard_keyword_clause::=**

![](media/Sharding/d15e35752ab4fd66496232e1d1e055a1.jpg)

#### SHARD

SHARD 키워드를 사용하면 샤드 쿼리 분석기를 통해 쿼리에 존재하는 샤드 객체 분산 정보가 존재하는 모든 샤드 노드에 쿼리를 전송하고 수행하여 취합한다.

각 노드의 데이터를 취합한 결과가 논리적으로 동일할 수 없는 즉, 샤드 쿼리가 아닌 다음의 사례를 살펴보자.

-   SELECT count(\*) FROM *s1;*

일반 쿼리에 SHARD 키워드를 적용하면 분산 정보가 존재하는 모든 노드를 대상으로 쿼리를 수행하고 그 결과를 얻어온다.

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

NODE 키워드는 인자로 명시한 노드에 쿼리를 전송하고 그 수행 결과를 취합한다. 샤드 쿼리 분석기를 통하지 않고 해당 쿼리를 바로 전달한다.

사용 가능한 NODE 유형은 다음과 같다.

-   NODE[META] : 코디네이팅 샤드 노드에 대한 쿼리 수행
-   NODE[DATA] 또는 NODE[DATA()] : 모든 샤드 노드들에 대해 쿼리 분석 및 변환없이 수행
-   NODE[DATA(*'node1_name*', *node2_name*',...)] : 명시된 노드(들)에 대해 쿼리 분석 및 변환없이 수행

노드를 구성하고 샤드 객체 구성 전 후의 데이터 상태를 확인할 경우에 유용하게 쓰일 수 있다.

##### 구문

```
NODE[META] SELECT count(*) FROM t1;
NODE[DATA] SELECT count(*) FROM s1;
SELECT * FROM NODE[META](SELECT count(*) FROM s1);
SELECT * FROM NODE[DATA]('node1', 'node2')](SELECT count(*) FROM s1);
```

\<질의\> 코디네이팅 샤드 노드에 존재하는 t2테이블의 레코드 개수를 구하라.

```
iSQL> CREATE TABLE t2 AS SELECT * FROM s1
iSQL> EXEC dbms_shard.set_shard_table('sys','t2','H','i1');
iSQL> EXEC dbms_shard.set_shard_hash('sys','t2',1000,'node1');
iSQL> NODE[META] SELECT count(*) FROM t1;
```

\<질의\> 'node2' 에 존재하는 s1 샤드 테이블에 대해 샤드키가 아닌 i1 컬럼의 group별 합을 수행하라.

```
iSQL> SELECT * FROM NODE[DATA('node2')](SELECT i1,sum(i1) FROM s1 GROUP BY i1);
```

> ##### 주의 사항
>
> 샤드 키워드는 iSQL 을 통한 관리 목적으로 사용해야 한다.
>
> 샤드 키워드의 적용 결과는 단순히 해당 노드의 수행 결과를 얻어 취합하는 것이므로 결과의 정합성을 보장하지 않는다. 따라서 사용에 각별한 주의가 필요하다.

### 샤드 함수

Altibase Sharding은 사용자 편의를 위해 추가적인 샤드 함수를 제공한다.

#### shard_node_name

##### 구문

```
shard_node_name()
```

##### 설명

샤드 노드의 이름을 반환한다.

##### 예제

\<질의\> 샤드 노드 별 s1테이블의 레코드 개수를 구하라.

```
iSQL> shard SELECT shard_node_name(),count(*) FROM s1;
```

#### shard_key

##### 구문

```
shard_key(key_column, value)
```

##### 설명

샤드 노드를 지정하여 질의를 수행한다.

##### 예제

\<질의\> s1테이블의 k1이 1에 해당하는 샤드 노드에서 s1테이블의 레코드 개수를 구하라.

```
iSQL> SELECT count(*) FROM s1 WHERE shard_key(k1,1); 
```

### 샤드 실행계획

Altibase Sharding 사용자는 iSQL을 통해 쿼리가 수행되는 실행계획을 조회할 수
있다.

샤드 최적화기가 생성한 실행계획과 샤드 노드에서 생성한 실행계획을 모두 조회할 수
있으며 쿼리를 분석하여 최적화 하는데 사용할 수 있다.

일반적으로 Altibase Sharding에서 사용되는 논샤드 쿼리는 가능한 샤드 쿼리로
변경하여 사용하는 것이 성능상 유리하다.

#### 실행 노드 확인

샤드 최적화기가 생성한 실행노드의 기능과 explain plan으로 출력되는 형식, 해당
노드가 출력되는 쿼리 예제를 살펴본다.

##### 출력 형식

SHARD-COORDINATOR

##### 설명

SHARD-COORDINATOR 실행노드는 사용자가 입력한 쿼리 중 샤드 노드에서 수행할 쿼리를
수행하고, 그 결과를 통합하여 상위 실행노드로 전달한다.

보다 상세한 수행 결과를 조회하기 위하여 다음 명령을 사용한다.

ALTER SESSION SET TRCLOG_DETAIL_PREDICATE = 1;

TRCLOG_DETAIL_PREDICATE 프로퍼티 값을 1로 설정하면, SHARD-COORDINATOR가 특정
샤드 노드로 쿼리를 보내어 수행한 이력 및 플랜을 조회할 수 있다. 

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

#### 샤드 쿼리 분석

Altibase Sharding 은 isql을 통해 사용자 구문에 대한 샤드 쿼리 분석 결과를
확인하는 방법을 제공하며 다음과 같은 조건하에 동작한다.

- alter session set EXPLAIN PLAN = ON (or ONLY);
- alter session set TRCLOG_DETAIL_SHARD = 1;

단, TRCLOG_DETAIL_SHARD=1 의 경우 내부적으로 cache 된 plan을 사용하지 않고
새로이 plan을 생성하므로 사용상 주의가 필요하다.

##### ANALYSIS COST

샤드 쿼리 분석의 최소단위는 쿼리 구문이며 샤드 쿼리 분석기는 구문 단위의 분석을
수행한다.

주어진 구문에 대해 분석을 수행하고 구문 변환을 시도한 후 다시 반복해서 구문
분석을 시도한다.

샤드 쿼리 분석 비용은 사용자 구문에 대해 시도한 총 분석 횟수로 계산된다.

##### QUERY TYPE

사용자 쿼리는 다음과 같이 구분할 수 있다.

- 샤드 쿼리(Shard query) : 분산 수행 결과와 단일 수행 결과의 정합성이 보장되는
  구문
- 논샤드 쿼리(Non-shard query) : 분산 수행 결과와 단일 수행 결과의 정합성이
  보장되지 않는 구문

샤드 라이브러리를 연동한 경우라면 샤드 쿼리는 클라이언트측 샤딩을 수행하고
논샤드 쿼리는 서버측 샤딩을 수행한다.

##### NON-SHARD QUERY REASON

사용자 쿼리를 논샤드 쿼리로 분석한 이유이다.

##### QUERY TRANSFORMABLE

사용자 쿼리가 논샤드 쿼리로 분류된 경우라면 서버측 샤딩을 수행하게 된다.

샤드 쿼리 최적화기는 해당 쿼리를 서버측에서 수행하기 위해 샤드 쿼리 변환을 통해
최적의 분산부 쿼리 생성을 시도하는데 이 경우 최적화된 분산부 쿼리 생성 가능성을
다음과 같이 표현한다.

- 변환된 분산부 쿼리 생성이 가능하면 'Yes'
- 변환된 분산부 쿼리 생성이 불가하면 'No'

##### 쿼리 분석 예제

다음은 분산된 샤드 테이블 s1에 대한 샤드 쿼리분석 결과이다.

```
< Print shard analysis information Example >

iSQL> alter session set explain plan = only;
Alter success.
iSQL> alter session set trclog_detail_shard = 1;
Alter success.
iSQL> SELECT * FROM s1;

I1 I2 I3
----------------------------------------
No rows selected.
------------------------------------------------------------
PROJECT ( COLUMN_COUNT: 3, TUPLE_SIZE: 20, COST: BLOCKED )
SHARD-COORDINATOR
------------------------------------------------------------
[ SHARD ANALYSIS INFORMATION ]
ANALYSIS COST : 1
SHARD QUERY TYPE : Shard query
------------------------------------------------------------
iSQL> SELECT count(*) FROM s1;
COUNT(*)
-----------------------
No rows selected.
------------------------------------------------------------
PROJECT ( COLUMN_COUNT: 1, TUPLE_SIZE: 8, COST: BLOCKED )
GROUP-AGGREGATION ( ITEM_SIZE: ??, GROUP_COUNT: ??, BUCKET_COUNT: 1, ACCESS: ??, COST: BLOCKED )
SHARD-COORDINATOR
[ DISTRIBUTION QUERY ]
SELECT COUNT(*) FROM S1;
------------------------------------------------------------
[ SHARD ANALYSIS INFORMATION ]
ANALYSIS COST : 3
QUERY TYPE : Non-shard query
NON-SHARD QUERY REASON : GROUP BY needed multiple nodes.
QUERY TRANSFORMABLE : Yes
------------------------------------------------------------
```



### 쿼리 튜닝 

Altibase Sharding은 샤드 쿼리로 적용되지 않는 복잡한 논샤드 쿼리를 변환없이
사용할 수 있다는 장점이 있으나 논샤드 쿼리는 샤드 코디네이터의 처리 과정을
거치게 되므로 성능 저하를 유발할 수 있다.

그러므로, 샤딩 시스템을 좀 더 효율적으로 사용하기 위해서 샤드 키워드를 이용하여
쿼리를 튜닝하면 성능을 획기적으로 개선할 수 있다.

#### Grouping

grouping의 키로 샤드 키가 포함된 경우 샤드 쿼리 분석기는 샤드 쿼리로 판단한다.

그러나 grouping key에 샤드 키가 포함되지 않으면, 샤드 코디네이터가 전체 데이터를
수집하여 처리하므로 성능 저하의 원인이 될 수 있다. 이런 경우 grouping을 각 샤드
노드에서 수행하도록 변경하면 샤드 노드의 부하도 줄고 쿼리 속도도 빨라진다.

```
SELECT c1, count(*), sum(i2), avg(i2) FROM s1 GROUP BY c1;
```

위의 쿼리에 다음과 같이 SHARD 키워드를 사용하여 변경할 수 있다.

```
SELECT c1, sum(c), sum(s), sum(s)/count(a) FROM SHARD(SELECT c1, count(*) c, sum(i2) s, count(i2) a FROM s1 GROUP BY c1) GROUP BY c1;
```

#### Pushdown

서로 다른 분산방식의 테이블을 조인하는 경우, 조인은 샤드 코디네이터가 수행하게
된다.

이 때, 조인 비용을 줄이기 위해서 조건절을 샤드 노드에서 수행하도록 변경하면 샤드
코디네이터를 거치지 않아 쿼리 속도가 빨라진다.

다음과 같은 쿼리가 있다.

```
SELECT * FROM t1, t2 WHERE t1.i1=t2.i1 AND t1.i2>3;
```

이를 SHARD 키워드를 사용하여 다음과 같이 변경할 수 있다.

```
SELECT * FROM SHARD(SELECT * FROM T1 WHERE I2>3) t1, t2 WHERE t1.i1=t2.i1;
```

### 모니터링 

Altibase Sharding 사용자는 샤딩 시스템에서 제공하는 샤드 성능 뷰를 이용하여 모든 샤드 노드의 수행 상태를 확인할 수 있다.

모든 샤드 노드에 대해 쿼리를 동시에 수행하므로 샤딩 시스템의 모든 샤드 노드를 한번에 관찰하기에 유용하다.

샤드 성능 뷰는 내부적으로 NODE 키워드를 이용하여 모든 샤드 노드의 성능 뷰 정보와 그 외 추가적인 정보를 취합하여 생성된다. 따라서 노드의 상태에 따라 쿼리가 실패할 수도 있다.

#### Property 조회

S\$PROPERTY를 이용하여 샤딩 시스템에서 사용되는 모든 노드의 시스템 프로퍼티를 확인할 수 있다.

예를 들어 모든 샤드 노드의 PORT_NO 를 확인하는 방법은 다음과 같다.

```
iSQL> SELECT node_name, value1 from s$property WHERE name = 'PORT_NO';
NODE_NAME             VALUE1
-----------------------------------------------
NODE1                 20030
NODE2                 21030
NODE3                 22030
3 rows selected.
```

#### Session 조회

S\$SESSION을 이용하여 모든 샤드 노드의 모든 샤드 세션을 확인할 수 있다.

다음은 모든 샤드 세션을 확인하는 방법이다.

```
iSQL> SELECT id, node_name, session_id, shard_client, shard_session_type FROM s$session;
ID                    NODE_NAME     SESSION_ID     SHARD_CLIENT   SHARD_SESSION_TYPE
----------------------------------------------------------------------------------------------
1-1-1701180354        NODE1         2              N              U
1-1-1701180354        NODE1         1              N              C
1-1-1701180354        NODE2         1              N              C
1-1-1701180354        NODE3         1              N              C
4 rows selected.
```

#### Statement 조회

S\$STATEMENT를 이용하여 모든 샤드 세션에서 실행되는(또는 가장 최근 실행된) 구문을 확인할 수 있다.

다음은 모든 샤드 세션에서 수행되는 모든 구문을 확인하는 방법이다.

```
iSQL> SELECT shard_session_id, node_name, shard_session_type, session_id, id, query_type, substr(query, 1, 6) FROM s$statement;
SHARD_SESSION_ID    NODE_NAME    SHARD_SESSION_TYPE  SESSION_ID  ID          QUERY_TYPE    SUBSTR(QUERY, 1, 6)
------------------------------------------------------------------------------------------------------------------------
1-1-1701180354      NODE1        C                   1           65538       -             SELECT
1-1-1701180354      NODE1        U                   2           131072      N             SELECT
1-1-1701180354      NODE2        C                   1           65538       -             SELECT
1-1-1701180354      NODE3        C                   1           65538       -             SELECT
4 rows selected.
```

> #### 주의사항
>
> 특정 노드의 장애로 인해 샤드 성능 뷰로 조회가 불가능할 경우 NODE 키워드를 이용하여 다른 노드의 상태를 확인할 수 있다.
>
> ```
> NODE[DATA(‘node1’)] SELECT shard_node_name(), QUERY_TIME_LIMIT FROM v$session;
> ```

### Fail-Over

Altibase Sharding의 Fail-Over기능은 특정 샤드 노드에 장애가 발생 하였을 때, 해당
노드의 가용(Alternate) 서버로 자동 전환되는 기능이며 샤드 노드 설정 및 응용
프로그램 설정을 통해서 사용 가능하다.

Altibase Sharding의 Fail-Over를 이해하기 위해서는 Sharding에서 사용하는 각 커넥션에
대한 이해가 선행되어야 한다.
- 사용자 커넥션(User Connection)
- 샤드 라이브러리 커넥션(Shard Library Connection)
- 코디네이터 커넥션(Coordinator Connection)

Altibase Sharding 에서는 각 커넥션의 연결 장애 시 Fail-Over가 발생할 수 있다.

각 커넥션에 대한 Fail-Over는 장애를 인식하는 시점에 따라 CTF (Connection Time
Fail-Over)와 STF (Service Time Fail-Over)로 분류할 수 있으며, 커넥션 마다
Fail-Over의 동작이 다르므로 각 커넥션에 대한 Fail-Over 동작을 이해해야 한다.

Altibase Sharding에서의 Fail-Over는 다수의 샤드 노드에 대한 커넥션에 대해서
고려해야하므로 응용 프로그램 처리 가이드에 따라 처리할 것을 권장한다.

Fail-Over에 대한 개요 및 사용 방법은 *Altibase Replication Manual*을 참고한다.

#### 사용자 커넥션

사용자 커넥션에 대한 Fail-Over는 응용 프로그램에서 API의 연결 함수 호출시 입력한
연결 속성 문자열에 명시하거나 연결 설정 파일에 명시한 샤드 노드의 IP, PORT로
시도한다.

사용자 커넥션에 대한 Fail-Over는 Replication환경에서 Altibase Fail-Over의
사용법과 동일하며, Replication환경에서 Altibase Fail-Over의 사용법은 *Altibase
Replication Manual*을 참고한다.

#### 샤드 라이브러리 커넥션

샤드 라이브러리 커넥션은 사용자 커넥션 연결 시에 샤드 라이브러리에서 자동으로
샤드 노드에 접속하는 것을 말한다.

Fail-Over는 시스템 관리자가 등록한 샤드 노드의 외부 커넥션 IP,PORT로 시도한다.

예를들어, 관리자가 NODE1을 다음과 같은 프로시저를 통해서 설정할 수 있다.

```
iSQL> EXEC dbms_shard.set_node('node1', '192.168.1.30', 20300, '192.168.1.31', 20400);
Execute success.
```

위의 예제에서 NODE1의 샤드 라이브러리 커넥션은 “'192.168.1.30', 20300”에 연결을
시도하며 문제 발생시 “'192.168.1.31', 20400”으로 Fail-Over 시도한다.

샤드 라이브러리 커넥션에 대한 Fail-Over설정을 변경하기 위해서는 다음의
프로시저를 통해서 변경 가능하다.

```
iSQL> EXEC dbms_shard.reset_node_external('node1', '192.168.100.1', 20300,
'192.168.100.2', 20300);
Execute success.
```

만약, 샤드 라이브러리 커넥션의 통신 방법을 커넥션 별로 변경하고 싶은 경우 사용자
커넥션의 커넥션 스트링에 SHARD_CONNTYPE 속성으로 지정 가능하다.
지원 타입은 *Altibase Sharding 통신 방법*의 샤드 라이브러리 커넥션을 참고한다.

##### 제약 사항

- Altibase Sharding에서 Fail-Over 콜백 함수는 사용자 커넥션에 대해서만
  동작하며 샤드 라이브러리 커넥션에 대한 Fail-Over 콜백 함수는 지원하지
  않는다.

#### 코디네이터 커넥션

코디네이터 커넥션에 대한 Fail-Over는 시스템 관리자가 등록한 샤드 노드의 내부
커넥션 IP, PORT로 시도한다.

예를들어, 관리자가 NODE1을 다음과 같은 프로시저를 통해서 설정할 수 있다.

```
iSQL> EXEC dbms_shard.set_node('node1', '192.168.1.30', 20300, '192.168.1.31', 20400);
Execute success.
```

위의 예제에서 NODE1의 코디네이터 커넥션은 “'192.168.1.30', 20300”에 연결을
시도하며 문제 발생시 “'192.168.1.31', 20400”으로 Fail-Over 시도한다.

코디네이터 커넥션에 대한 Fail-Over설정을 변경하기 위해서는 다음의 프로시저를
통해서 변경 가능하다.

```
iSQL> EXEC dbms_shard.reset_node_internal('node1', '192.168.100.11', 20300,
'192.168.100.12', 20300 );
Execute success.
```

코디네이터 커넥션의 Fail-Over 동작은 다음의 프로퍼티를 통해서 세부적으로 설정
가능하다. 각 프로퍼티의 세부 설명은 이 문서의 프로퍼티 설명을 참조한다.

* SHARD_INTERNAL_CONN_ATTR_RETRY_COUNT
* SHARD_INTERNAL_CONN_ATTR_RETRY_DELAY
* SHARD_INTERNAL_CONN_ATTR_CONNECTION_TIMEOUT
* SHARD_INTERNAL_CONN_ATTR_LOGIN_TIMEOUT

#### 응용 프로그램 가이드

Altibase Sharding 환경에서는 여러 샤드 노드에서 수행중인 트랜잭션 및 커넥션이
있으며, 이들은 최적화 과정을 거쳐서 샤드 라이브러리 혹은 서버에서 내부적으로
처리된다. 그러므로 특정 노드의 장애나 접속 에러 시에도 일부 커넥션이 남아 있거나
트랜잭션이 완전히 철회되지 않을 수 있다.

이러한 분산 환경에서 응용 프로그램이 트랜잭션 처리를 일관되게 하기 위해서는
NON-AUTOCOMMIT을 사용하여 다음의 가이드에 따라 작성되어야 Fail-Over가 정상적으로
처리될 수 있다.

다만, 응용 프로그램이 다수의 샤드 노드를 접근하지 않도록 설계된 경우에는
AUTOCOMMIT 모드를 사용할 수 있으나 이 경우에도 AUTOCOMMIT에 대한 가이드에 따라
처리되어야 Fail-Over 이후에 서비스가 정상적으로 처리될 수 있다.

##### CTF(Connection Time Failover)

CTF의 경우에는 데이터 베이스 연결이 되는지에 따라 성공 여부를 바로 알 수 있다.

다만, 분산 환경에서는 일부 노드의 에러로 인해 실패했을 때, 일부 노드에 접속
되어있을 수 있으므로 명시적으로 SQLDisconnect를 호출하여 전체 연결을 끊어 주어야
한다.

CTF는 트랜잭션이 시작되기 전에 발생하므로 Commit 모드는 고려하지 않아도 된다.

##### STF(Service Time Failover)

ShardCLI 경우는 SQLPrepare, SQLExecute, SQLFetch등에서 SQL_SUCCESS가 아닌 에러가
발생하면, SQLGetDiagRec에 statement 핸들을 넘기고, 이 함수의 5번째 인자에
반환되는 native 에러 코드 값이 ALTIBASE_FAILOVER_SUCCESS인 진단
레코드(diagnostic record)가 있으면 STF가 성공한 것으로 판단할 수 있다.

- NON-AUTOCOMMIT 트랜잭션

ShardCLI 함수에서 SQL_SUCCESS가 아닌 에러가 발생하였을 때 다음의 순서로 에러
로직을 처리한다.

1. STF가 성공한 경우(ALTIBASE_FAILOVER_SUCCESS) Rollback을 수행하며 Rollback이
   성공하면 트랜잭션 재시작 위치로 되돌아 가서 응용 프로그램 로직을 수행한다.
   1. 트랜잭션 재시작 위치는 SQLPrepare,SQLExecute를 사용하는 경우 최초
      SQLPrepare 이전으로 돌아가야 하며 Bind는 다시 하지 않아도 된다.
   2. SQLDirectExec를 사용하는 경우에는 SQLDirectExec 이전으로 돌아가면 된다.
   3. STF 성공 후 Rollback을 하는 중에 다시 Fail-Over가 발생할 수 있으므로 이
      경우에는 Rollback을 한번 더 수행한다.
2. STF가 실패하고 더 이상 서비스 가능한 가용 노드가 없는
   경우(ALTIBASE_SHARD_NODE_FAILOVER_IS_NOT_AVAILABLE) 전체 노드에 대한 연결을
   명시적으로 끊고 최초 연결부터 재시도 한다.
   1. 샤딩 환경에서는 다수의 노드에 접속이 이뤄져 있으므로 명시적으로
      SQLDisconnect를 호출해야 모든 노드에 연결이 끊긴다
3. 그 외의 에러에 대해서는 응용 프로그램 에러 처리 로직을 수행한다.

- AUTOCOMMIT 트랜잭션

  ShardCLI 함수에서 SQL_SUCCESS가 아닌 에러가 발생하였을 때 다음의 순서로 에러
  로직을 처리한다.

1. STF가 성공한 경우(ALTIBASE_FAILOVER_SUCCESS) 트랜잭션 재시작 위치로 되돌아
   가서 응용 프로그램 로직을 수행한다.
   1. 트랜잭션 재시작 위치는 SQLPrepare, SQLExecute를 사용하는 경우 최초
      SQLPrepare 이전으로 돌아가야 하며 Bind는 다시 하지 않아도 된다.
   2. SQLDirectExec를 사용하는 경우에는 SQLDirectExec 이전으로 돌아가면 된다.
2. STF가 실패하고 더 이상 서비스 가능한 가용 노드가 없는 경우
   (ALTIBASE_SHARD_NODE_FAILOVER_IS_NOT_AVAILABLE) 전체 노드에 대한 연결을
   명시적으로 끊고 최초 연결부터 재시도 한다.
   1. 샤딩 환경에서는 다수의 노드에 접속이 이뤄져 있으므로 명시적으로
      SQLDisconnect를 호출해야 모든 노드에 연결이 끊긴다.

##### ShardCLI Failover Sample Code

Altibase Sharding의 failover를 포함하는 Shardcli sample 코드는
\$ALTIBASE_HOME/sample/SHARD/Fail-Over/failoversample.cpp에 있으며, 해당
프로그램은 ShardCLI를 이용하여 작성한 fail-over를 고려한 응용 프로그램 예제이다.

failoversample.cpp의 코드는 “CREATE TABLE T1 (I1 VARCHAR(20), I2 INTEGER);”의
구문으로 T1 테이블을 생성한 후 T1 테이블을 샤드 테이블로 등록하였다고 가정한다.

해당 프로그램은 최초 접속할 샤드 노드의 port와 alternate port를 순차적으로
입력받아 연결하고 응용 프로그램 로직을 수행하여 Direct-Execute 방식으로 데이터를
한 건 입력하고 Prepare-Execute 방식으로 질의를 수행한 후 검색된 데이터를
출력하는 프로그램이다.

예제 프로그램을 수행중에 특정 노드에 장애가 있는 경우 최초 접속시에 CTF가
동작하며 실행 중에는 STF를 통해 fail-over 된다.

주의할 점은, 접속을 재시도 하기 위해서는 남아 있을 수 있는 커넥션을 종료하기
위해서 SQLDisconnect를 명시적으로 호출해 주어야 하며, 에러가 발생했을 때에는
다수의 노드에서 발생했을 수 있는 에러를 확인하기 위해서 SQLDiagRec을 통해 모든
노드의 에러를 점검해야 한다.

에러 점검을 통해서 Service Time Fail-over가 되면 연결이 종료되지 않은 샤드
노드에 남아 있는 트랜잭션을 정리하기 위해서 SQLEndTran(ROLLBACK)을 호출해 준 후
다시 Prepare 혹은 DirecExecute 로직으로 돌아가서 수행 한다.

자세한 코드 내용은 \$ALTIBASE_HOME/sample/SHARD/Fail-Over/failoversample.cpp를
참고한다.

### 샤딩 분산 시스템 변경

샤딩 시스템 운영중에 데이터 저장소가 부족하거나 서비스 용량이 추가로 필요한 경우
신규 샤드 노드를 추가할 수 있다.

신규 노드가 추가되면 데이터를 이동시켜 부하를 나누어 줄 수 있으며, 이 때 기존
시스템 분석을 통해서 적절한 양의 데이터를 이동 시켜야 한다.

샤딩 시스템을 운영하면서 특정 샤드 노드에 데이터가 집중되는 현상이 발생할 수
있으며, 특정 샤드 노드에 데이터가 집중되면 부하의 불균형을 가져와 전체 시스템
성능이 저하되거나 저장 공간이 부족하여 시스템 운영에 문제를 불러일으킬 수 있다.

이런 문제를 해소하기 위해서 데이터가 집중된 샤드 노드의 데이터를 다른 샤드
노드로 분배해야 한다.

샤드 노드의 구성 변경이나 노드의 일부 하드웨어 장애로 인해서 샤드 노드를
제거하는 경우에도 제거되는 샤드 노드의 데이터를 보존하기 위해서는 운영중인 다른
샤드 노드로 데이터를 옮겨 준 후 샤드 노드를 제거해야 한다.

이 외에도 샤딩 시스템을 재구축 하기 위해서 샤드 키를 변경하는 등의 데이터 재구축
작업을 필요로 할 수 있으며, , 정리하면 샤딩 분산 시스템 변경을 필요로 하는
시점은 다음과 같은 경우이다.

- 샤드 노드 추가
- 샤드 데이터 분포 조정
- 샤드 노드 제거
- 샤딩 데이터 재구축

Altibase Sharding은 이와 같은 다양한 샤딩 시스템 변경에 대한 분산 데이터 이동
방법을 지원하기 위해서 서비스 중에 데이터를 이동시키는 리샤딩과 서비스 중지 후
데이터를 이동시키는 데이터 재구축을 제공한다. 이 외에도 분산 데이터의 정합성을
확인하기 위한 유효성 검사 방법을 제공한다.

- 유효성 검사
- 리샤딩
- 데이터 재구축

리샤딩과 데이터 재구축을 통한 데이터 이동을 비교하면 아래 표와 같다.

| 지원 항목        | 리샤딩                         | 데이터 재구축                             |
| ---------------- | ------------------------------ | ----------------------------------------- |
| 테이블 종류      | 파티션드 테이블                | 일반 테이블, 파티션드 테이블              |
| 분산 방식        | HASH, RANGE, LIST, SOLO, CLONE | HASH, RANGE, LIST, COMPOSITE              |
| 변경 작업        | 동일 분산 방식의 범위 변경     | 분산 방식 변경 및 범위 변경, 샤드 키 변경 |
| 데이터 이동 단위 | 파티션 단위                    | 테이블 단위                               |
| 서비스 중단 여부 | 서비스 무중단                  | 서비스 중단                               |
| 대상 노드        | 1 대 1                         | 1 대 N, N 대 N                            |

[표 3]. 리샤딩과 데이터 재구축 기능 비교

#### 노드 추가

샤딩 시스템에 샤드 노드를 추가하는 방법으로 샤드 매니저를 통한 방법과 수동으로
샤드 노드를 추가하는 방법을 제공한다.

수동으로 노드를 추가하는 것은 DBMS_SHARD 패키지의 SET_NODE 프로시저를 통해서
가능하다.

다만, 수동으로 샤드 노드를 추가하는 경우 기존 샤드 노드와 동일하게 샤드 메타를
복제해야하며, 샤드 메타의 일부가 다른 경우 데이터 서비스가 비정상 적으로 동작할
수 있으므로 권장하지 않는다.

수동으로 샤드 노드를 추가하는 것에 대한 자세한 설명은 본 장의 *“샤드 노드”* 절을
참고한다.

샤드 매니저를 통해 샤드 노드를 추가하는 경우 자동으로 샤드 메타를 복제하여 샤딩
시스템에 참여할 수 있도록 한다.

샤드 매니저를 통한 샤드 노드 추가는 6장 Altibase Sharding 유틸리티의 *Shard
Manager* 를 참고한다.

> 주의 사항 
>
> 노드 추가를 완료해도 해당 노드에 샤드 객체는 생성되어 있지 않으므로
> 동일한 스키마로 사용자가 샤드 객체를 생성해야한다.

#### 노드 제거

샤딩 시스템에서 노드를 제거하는 경우는 일반적이지 않으나 해당 노드에 영구적인
장애가 발생하거나 혹은 시스템의 축소를 위해서 노드를 제거할 수 있다.

샤드 노드를 제거하기 위해서는 노드 제거를 위한 데이터 이동 계획을 수립하고 이에
따라 해당 노드에 존재하는 데이터를 다른 샤드 노드로 이동시킨다.

데이터 이동이 완료되면 제거되는 노드에 사용자 커넥션으로 연결된 응용프로그램을
서비스 가능한 다른 샤드 노드로 이동시켜야한다.

그 후, 샤드 노드 추가와 동일하게 샤드 매니저나 DBMS_SHARD 패키지의 UNSET_NODE로
샤드 메타에서 해당 노드를 삭제한다.

샤드 노드 삭제가 시스템에서 인식되면 해당 노드에 존재하는 응용프로그램의 샤드
라이브러리 커넥션이 시간이 경과함에 따라 자동적으로 다른 샤드 노드로 이동한다.
시스템 관리자는 해당 노드의 세션이 모두 종료된 것을 확인하면 더 이상 시스템에
영향을 주지 않으므로 제거가 완료되었다고 볼 수 있다.

샤드 매니저를 통한 샤드 노드 삭제는 6장 Altibase Sharding 유틸리티의 *Shard
Manager* 를 참고하며 DBMS_SHARD 패키지의 UNSET_NODE에 대한 자세한 내용은 본 장의
*“샤드 노드”* 절을 참고한다.

> 주의 사항 
>
> 노드 제거가 완료되도 해당 노드에 샤드 객체를 명시적으로 DROP 하지 않으면 객체가 제거되지 않는다. 

#### 유효성 검사

샤드 테이블의 샤드 키 분산 방식 변경으로 인해 샤드 키와 데이터의 불일치가 발생할 수 있다. 분산 정보가 재설정 된 경우 기존의 분산 데이터는 샤드 키에 유효한(correct) 데이터와 유효하지 않은(incorrect) 데이터로 구분된다.

Altibase Sharding 은 샤드 키 분산 정보와 분산 데이터의 유효성을 검사하는 방법을 제공한다.

```
DBMS_SHARD.CHECK_DATA
```

사용 방법은 Altibase Sharding 패키지의 CHECK_DATA 를 참고한다.

#### 데이터 재구축

Altibase Sharding은 샤드 테이블의 분산 정보를 변경한 후, 기존의 데이터를 재구축하거나 특정 샤드 노드를 지정하여 데이터를 이동시키는 방법을 제공한다.

데이터 재구축을 위해서는 기존 분산 테이블을 해제(unset)한 후, 새로운 분산 방식으로 분산 테이블을 재설정(set)하는 과정을 선행해야 한다. 그러므로 진행중인 관련 테이블을 사용 중인 응용 프로그램을 종료 시킨 후 수행하여야 한다.

성능을 고려하여, 데이터 재구축은 변경된 분산 기준에 맞지 않는 데이터(incorrect data)만 이동(move)시키는 방식으로 수행되며 여러 세션에서 동시에 수행 가능하다. 단, 내부적으로 데이터의 이동이 수반되기 때문에 데이터의 정합성 보장을 위해서는 사용자 어플리케이션을 정지한 이후 수행해야 한다.

데이터 재구축은 샤드 키 분산(hash, range, list, composite) 방식을 적용한 샤드 테이블에 한해 지원하며, 복제 분산 방식과 독립 분산 방식은 지원하지 않는다.

- hash(500,1000) \<-\> hash(300,600,1000) (O)
- hash \<-\> range (O)
- hash \<-\> list,hash (O)
- range \<-\> clone (X)
- solo \<-\> hash (X)
- clone \<-\> solo (X)

Altibase Sharding 은 데이터 재구축 방법으로 아래와 같은 패키지 프로시저를 제공한다.

```
DBMS_SHARD.REBUILD_DATA
DBMS_SHARD.REBUILD_DATA_NODE
```

사용 방법은 Altibase Sharding 패키지의 REBUILD_DATA, REBUILD_DATA_NODE 를 참고한다.

#### 리샤딩

Altibase Sharding의 리샤딩은 서비스 중에 노드를 추가하거나 데이터의 분포가 특정
샤드 노드에 밀집되어있을 때 샤드 노드들의 데이터 범위를 변경하고 데이터를 재분배
하는 것을 말한다.

Altibase Sharding에서 제공하는 리샤딩은 데이터베이스 서비스에 영향을 최소화하여
백그라운드로 진행되므로, 응용 프로그램의 변화나 서비스 중단 없이 수행 가능하다.

서비스의 영향을 최소화 하기 위해서 데이터 이동은 한번에 하나의 샤드 노드에서
다른 하나의 샤드 노드로 이동하며 다수의 노드간 데이터 이동은 유발하지 않는다.

리샤딩은 온라인중에 데이터를 이동하기 위해서 내부적으로 이중화를 사용하며,
트랜잭션의 중단이 발생하지 않도록 Shard Meta Number(SMN)라는 개념을 두어 리샤딩
이전에 접속한 클라이언트와 이후에 접속한 클라이언트가 끊김없이 서비스 가능하도록
지원한다. SMN에 대한 자세한 내용은 2장 Altibase Sharding 설치와 설정의 *샤드
메타 설정*을 참고한다.

리샤딩은 샤드 테이블의 종류에 따라서 다음과 같이 분류될 수 있고, 샤드 매니저를
통해서 수행할 수 있다. 샤드 매니저의 리샤딩 사용 법에 대한 자세한 설명은 6장
Altibase Sharding 유틸리티의*Shard Manager*절을 참조한다.

- 단일 샤드 키 분산 테이블 리샤딩
- 복제 분산 테이블 리샤딩
- 독립 분산 테이블 리샤딩

##### 단일 샤드 키 분산 테이블 리샤딩

단일 샤드 키 분산 테이블의 리샤딩은 샤드 테이블의 파티션 단위로 수행 가능하다.

단일 샤드 키 분산 테이블 리샤딩을 계획할 때 주의해야할 것은 샤딩 시스템으로
요청되는 질의를 잘 고려하여 동일 샤드 키로 처리되는 샤드 테이블 그룹을 함께
이동시켜야 한다는 것이다.

만약, TABLE1과 TABLE2가 ID라는 컬럼으로 동일한 샤드 키와 설정을 가지고 있다면
리샤딩 이후에도 TABLE1과 TABLE2에 대해서 동일한 데이터 분포를 가질 수 있도록
해야한다. 그렇지 않고 TABLE1만 이동하는 경우 TABLE1과 TABLE2를 조인하는 질의가
요청되면 샤드 쿼리라고 하더라도 서버 사이드로 동작하여 성능 저하를 유발할 수
있다.

###### 샤드 데이터 분포 조정을 위한 리샤딩

샤드 데이터 분포가 특정 샤드 노드에 편향될 경우 해당 데이터를 다른 샤드 노드로
분산 시킬 수 있다.

리샤딩은 파티션 단위로 진행 가능하므로 샤드 테이블이 이미 파티션으로 분할
되어있다면 샤드 매니저를 통해 원하는 파티션을 선택해서 리샤딩이 가능하다.

그렇지 않고, 신규 샤드 노드로 전달해 줄 데이터가 파티션으로 분할되어있지 않은
경우 전체 샤드 노드에 파티션드 테이블 분할 구문을 사용하여 파티션을 분할해 준 후
리샤딩을 진행한다. 다만, 파티션드 테이블을 분할하는 경우 데이터가 이동하는 동안
테이블 락으로 인해서 데이터 양에 따라 서비스가 장시간 중단될 수 있으므로 노드
확장을 고려해서 미리 다수의 파티션으로 분할해 놓을 것을 권장한다.

파티션드 테이블의 분할 구문에 대한 자세한 내용은 *SQL Reference*를 참고한다.

###### 샤드 노드 추가를 동반한 리샤딩

노드 추가로 인한 단일 샤드 키 분산 테이블의 리샤딩은 아래와 같이 단계별로
구분해서 작업을 진행한다.

1. 노드 추가
2. 샤드 관련 객체들 생성 및 설정
3. 샤드 테이블 별 리샤딩

먼저 샤드 매니저를 통해 샤드 노드를 추가한 후 리샤딩을 원하는 테이블들을
선정한다. 수동으로도 샤드 노드를 추가하고 샤드 메타를 동기화 할 수 있으나
권장하지 않는다.

리샤딩을 원하는 테이블과 샤드 메타는 기존 샤드 노드와 동일하게 설정한 후
리샤딩을 수행해야하며 샤드 매니저를 통하여 샤드 노드를 추가하는 경우 자동으로
샤드 메타를 복제해 준다. 다만, 샤드 테이블은 생성되어 있지 않으므로 동일한
스키마로 사용자가 생성해야한다.

이 경우에도 파티션 단위로 리샤딩이 가능하므로 샤드 데이터 분포 조정의 설명과
동일하게 수행할 수 있다.

###### 샤드 노드 제거를 동반한 리샤딩

샤드 노드 제거를 위해서는 제거되는 노드에서 처리중인 데이터를 제거되지 않는 다른
샤드 노드로 옮긴 후 샤드 노드를 제거해야 데이터를 잃어버리지 않는다.

그러므로, 샤드 데이터 분포 조정과 동일하게 데이터를 이동 후 샤드 노드 제거를
진행한다.

노드 제거에서 설명한 것 처럼 노드 제거는 해당 노드가 가지고 있는 샤드 관련
객체를 삭제 후 노드 삭제를 진행한다. 노드 삭제가 모든 샤드 노드에서 적용되고
해당 샤드 메타가 적용되고 응용 프로그램의 연결이 모두 끊기면 노드 제거가
완료된다.

##### 복제 분산 테이블 리샤딩

복제 분산 테이블의 리샤딩은 신규 샤드 노드 추가를 동반한 경우에만 고려하여
리샤딩을 진행하면 된다. 데이터 분포에 대한 조정 및 샤드 노드 제거와 관련해서는
리샤딩을 고려할 필요가 없다.

신규 샤드 노드를 추가하는 경우 샤드 노드 추가 후 샤드 매니저를 통해 리샤딩을
수행하면 신규 노드에 복제 분산 테이블이 복제되어 서비스가 가능하다.

##### 독립 분산 테이블 리샤딩

독립 분산 테이블은 테이블 단위로 리샤딩이 가능하며 샤드 노드 추가나 삭제 그리고
데이터 분포 조정을 필요로 할 때 고려해야 한다.

독립 분산 테이블의 리샤딩은 테이블 단위로 진행 된다는 것을 제외하고 단일 키 분산
테이블과 동일하다.

## Altibase Sharding 딕셔너리

Altibase Sharding의 데이터 딕셔너리는 샤드 객체 정보를 저장하는 샤드 메타와 단일
샤드 노드의 샤딩 관련 시스템 프로세스 정보를 보여주는 성능 뷰(Performance View),
그리고 전체 샤딩 시스템의 실시간 정보를 보여주는 샤드 성능 뷰(Shard Performance
View)로 나뉘어진다.

본 장은 샤드 데이터베이스 객체 정보 및 Altibase Sharding시스템 정보를 제공하는
데이터 딕셔너리에 대해 설명한다.

### 샤드 메타

샤드 메타란 Altibase Sharding을 사용하는 전체 분산 데이터베이스에 생성된 객체에
대한 모든 정보를 저장하고 있는 SYS_SHARD사용자의 시스템 정의 테이블이다.

#### 구조 및 기능

샤드 메타 테이블은 분산 데이터베이스 객체를 관리하기 위해 시스템에 의해 정의된
테이블이다.

Altibase Sharding은 분산 데이터베이스 질의를 처리하기 위해 샤드 객체 정보를
조회하며 샤드 객체 및 노드 정보를 저장 및 변경할 때 샤드 메타 테이블을 사용한다.

샤드 메타 테이블의 소유자는 일반 메타 테이블과는 달리 SYS_SHARD 사용자이며, 샤드
메타에 대한 변경은 DBMS\_ SHARD 패키지를 이용해야 한다.

#### 샤드 메타 테이블 조회

DBMS_SHARD패키지를 이용하여 분산 데이터베이스 관련 정보를 등록, 삭제 및 변경 시
샤드 메타 테이블의 레코드가 시스템에 의해 생성, 삭제 또는 변경된다.

변경된 데이터베이스 객체 정보는 샤드 메타 테이블을 조회함으로써 확인할 수 있다.
샤드 메타 테이블의 레코드는 일반 테이블과 같이 SELECT 문으로 조회가 가능하다.

#### 샤드 메타 테이블 데이터 변경

Altibase Sharding 시스템 사용자가 DBMS_SHARD 패키지 이외의 방법으로 샤드 메타 를
변경하면 샤딩 시스템 구동이 실패하거나, 분산 데이터베이스 관련 정보를 상실하여
시스템에 치명적인 손상이 발생할 수 있다.

#### 샤드 메타 테이블 스키마 변경

Altibase Sharding에 새로운 기능이 제공되거나 기존 구문의 기능 변경 시 샤드 메타
테이블 스키마가 변경될 수 있다. 샤드 메타 테이블 스키마의 변경이 발생하면
데이터베이스 마이그레이션이 필요하다.

Altibase Sharding하위 버전에서 상위 버전으로 업그레이드 시 이를 고려해야 한다.

#### 샤드 메타 테이블 종류

다음 표는 샤드 메타 테이블의 목록이다.

| **샤드 메타 테이블 이름** | **설명**                                                   |
| ------------------------- | ---------------------------------------------------------- |
| **VERSION\_**             | Altibase Sharding의 버전을 기록하는 샤드 메타 테이블       |
| **LOCAL_META_INFO\_**     | 지역 데이터베이스의 샤드 정보를 기록하는 샤드 메타 테이블  |
| **GLOBAL_META_INFO\_**    | 샤드 메타 제어 정보를 기록하는 샤드 메타 테이블            |
| **NODES\_**               | 샤드 노드 정보를 기록하는 샤드 메타 테이블                 |
| **OBJECTS\_**             | 샤드 객체 정보를 기록하는 샤드 메타 테이블                 |
| **RANGES\_**              | 샤드 키 분산 테이블 정보를 기록하는 샤드 메타 테이블       |
| **CLONES\_**              | 복제 분산 테이블 정보를 기록하는 샤드 메타 테이블          |
| **SOLOS\_**               | 독립 분산 테이블 정보를 기록하는 샤드 메타 테이블          |
| **REPLICA_SETS_**         | 샤드 노드의 레플리카 셋을 기록하는 샤드 메타 테이블        |
| **FAILOVER_HISTORYS_**    | 샤드 시스템의 Failover History를 기록하는 샤드 메타 테이블 |

### SYS_SHARD.VERSION\_

Altibase Sharding의 버전을 기록하는 메타 테이블이다.

| Column name | Type    | Description                   |
| ----------- | ------- | ----------------------------- |
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

### SYS_SHARD.LOCAL_META_INFO\_

지역 데이터베이스의 샤드 정보를 기록하는 메타 테이블이다.

| Column name                  | Type        | Description               |
| ---------------------------- | ----------- | ------------------------- |
| SHARD_NODE_ID                | INTEGER     | 샤드 노드 식별자          |
| SHARDED_DB_NAME              | VARCHAR(40) | 샤드된 데이터 베이스 이름 |
| NODE_NAME                    | VARCHAR(40) | 샤드 노드 이름            |
| HOST_IP                      | VARCHAR(64) | 서비스 호스트 IP          |
| PORT_NO                      | INTEGER     | 서비스 포트               |
| INTERNAL_HOST_IP             | VARCHAR(64) | 코디네이터 호스트 IP      |
| INTERNAL_PORT_NO             | INTEGER     | 코디네이터 포트           |
| INTERNAL_REPLICATION_HOST_IP | VARCHAR(64) | 샤드 이중화 호스트 IP     |
| INTERNAL_REPLICATION_PORT_NO | INTEGER     | 샤드 이중화 포트          |
| INTERNAL_CONN_TYPE           | INTEGER     | 코디네이터 연결 타입      |
| K_SAFETY                     | INTEGER     | 복제본 수                 |
| REPLICATION_MODE             | INTEGER     | 샤드 이중화 모드          |
| PARALLEL_COUNT               | INTEGER     | 이중화 병렬 적용자 수     |

#### 칼럼 정보

##### SHARD_NODE_ID

지역 데이터베이스의 샤드 노드 식별자로 전체 샤딩 시스템에서 유일해야 한다.

SET_LOCAL_NODE 프로시저를 통해 최초로 지역 샤드 정보를 설정시에 입력해야하며
SET_LOCAL_NODE 혹은 RESET_SHARD_NODE_ID로 변경 가능하다.

##### SHARDED_DB_NAME

지역 샤드 노드가 참여할 논리적인 샤드된 데이터 베이스 이름을 나타내며, 지역 데이터 베이스의 DB 이름으로 자동으로 입력다. 

##### NODE_NAME

지역 샤드 노드의 이름이다.

##### HOST_IP

지역 샤드 노드에서 서비스에 사용할 호스트 IP 이다. 

##### PORT_NO 

지역 샤드 노드에서 서비스에 사용할 Port 이다. 

##### INTERNAL_HOST_IP

지역 샤드 노드에서 코디네이터가 내부적으로 사용하는 호스트 IP 이다. 

##### INTERNAL_REPLICATION_HOST_IP

지역 샤드 노드에서 내부 복제용으로 사용할 호스트 IP 이다.

##### INTERNAL_REPLICATION_PORT_NO

지역 샤드 노드에서 내부 복제용으로 사용할 Port로 REPLICATION_PORT_NO 프로퍼티 값과 동일한 값으로 유지되어야 한다.

#####  INTERNAL_CONN_TYPE

내부적으로 사용되는 코디네이터 연결 방식이다. 1로 설정된 경우 TCP를 사용하며 8인 경우 인피니 밴드를 사용한다.  

##### K_SAFETY

시스템 내에서 유지할 복제본의 개수를 나타낸다.  

##### REPLICATION_MODE

시스템에서 사용하는 샤드 이중화 모드를 나타낸다. 값이 12인 경우 'CONSISTENT' 샤드 이중화 모드를 의미하며, 10인 경우 샤드 이중화 모드 중 'NOWAIT' 모드를 나타낸다.  

##### PARALLEL_COUNT

샤드 이중화에서 사용하는 이중화 병렬 적용자의 수를 나타낸다. 

### SYS_SHARD. GLOBAL_META_INFO\_

샤드 메타 정보에 대한 내용을 기록하는 메타 테이블이다.

| Column name | Type    | Description                                        |
| ----------- | ------- | -------------------------------------------------- |
| ID          | INTEGER | 이중화를 위한 주 키                                |
| SMN         | BIGINT  | 샤드 메타가 가지고 있는 가장 최신의 샤드 메타 번호 |

#### 칼럼 정보

##### ID

시스템 내부적으로 복제를 위해 사용되는 키 값

##### SMN

데이터베이스의 샤드 메타에서 유지하는 메타 정보중 가장 최신 메타에 대한 샤드
메타 번호(Shard Meta Number)를 나타낸다.

### SYS_SHARD.NODES\_

Altibase Sharding의 샤드 노드 정보를 기록하는 메타 테이블이다.

| Column name                | Type        | Description                                 |
| -------------------------- | ----------- | ------------------------------------------- |
| NODE_ID                    | INTEGER     | 샤드 노드의 지역 식별자                     |
| NODE_NAME                  | VARCHAR(40) | 샤드 노드 이름                              |
| HOST_IP                    | VARCHAR(64) | 샤드 노드 external ip address               |
| PORT_NO                    | INTEGER     | 샤드 노드 external port 번호                |
| ALTERNATE_HOST_IP          | VARCHAR(64) | 샤드 노드의 external alternative ip address |
| ALTERNATE_PORT_NO          | INTEGER     | 샤드 노드의 external alternative port 번호  |
| INTERNAL_HOST_IP           | VARCHAR(64) | 샤드 노드의 internal ip address             |
| INTERNAL_PORT_NO           | INTEGER     | 샤드 노드의 internal port 번호              |
| INTERNAL_ALTERNATE_HOST_IP | VARCHAR(64) | 샤드 노드의 internal alternative ip address |
| INTERNAL_ALTERNATE_PORT_NO | INTEGER     | 샤드 노드의 internal alternative port 번호  |
| INTERNAL_CONN_TYPE         | INTEGER     | 샤드 노드의 internal 연결 방식              |
| SMN                        | BIGINT      | 샤드 메타 번호                              |

#### 칼럼 정보

##### NODE_ID

샤드 노드의 지역 식별자를 나타낸다.

##### NODE_NAME

샤드 노드의 이름을 나타내며 샤드 노드의 이름은 유일해야 한다.

##### HOST_IP

샤드 라이브러리 또는 외부 응용프로그램에서 연결할 샤드 노드의 ip address를
나타낸다.

##### PORT_NO

샤드 라이브러리 또는 외부 응용프로그램에서 연결할 샤드 노드의 port 번호를
나타낸다.

##### ALTERNATE_HOST_IP

샤드 라이브러리 또는 외부 응용프로그램에서 연결할 샤드 노드의 alternate 서버 ip
address를 나타낸다.

##### ALTERNATE_PORT_IP

샤드 라이브러리 또는 외부 응용프로그램에서 연결할 샤드 노드의 alternate 서버
port 번호를 나타낸다.

##### INTERNAL_HOST_IP

코디네이터가 연결할 샤드 노드의 ip address를 나타낸다.

##### INTERNAL_PORT_NO

코디네이터가 연결할 샤드 노드의 port 번호를 나타낸다.

##### INTERNAL_ALTERNATE_HOST_IP

코디네이터가 연결할 샤드 노드의 alternate 서버 ip address를 나타낸다.

##### INTERNAL_ALTERNATE_PORT_NO

코디네이터가 연결할 샤드 노드의 alternate 서버 port 번호를 나타낸다.

##### INTERNAL_CONN_TYPE

코디네이터가 연결할 샤드 노드의 연결 방식으로 지원 타입은 *Altibase Sharding 통신 방법*의 코디네이터 커넥션을 참고한다.

##### SMN

샤드 메타에 대한 버전 관리 번호를 나타낸다.

### SYS_SHARD.OBJECTS\_

Altibase Sharding의 샤드 객체 정보를 기록하는 메타 테이블이다.

| Column name            | Type         | Description                                                  |
| ---------------------- | ------------ | ------------------------------------------------------------ |
| SHARD_ID               | INTEGER      | 샤드 객체 식별자                                             |
| USER_NAME              | VARCHAR(128) | 샤드 객체 소유자                                             |
| OBJECT_NAME            | VARCHAR(128) | 샤드 객체 이름                                               |
| OBJECT_TYPE            | CHAR(1)      | 샤드 객체 종류 T : 테이블 P : 프로시저                       |
| SPLIT_METHOD           | CHAR(1)      | 분산 방식 H : 해시(hash) R : 범위(range) L : 리스트(list) C : 복제(clone) S : 독립(solo) |
| KEY_COLUMN_NAME        | VARCHAR(128) | 샤드 키 이름                                                 |
| SUB_SPLIT_METHOD       | CHAR(1)      | 서브 샤드 키 분산 방식 H : 해시(hash) R : 범위(range) L : 리스트(list) |
| SUB_KEY_COLUMN_NAME    | VARCHAR(128) | 서브 샤드 키 칼럼 이름                                       |
| DEFAULT_NODE_ID        | INTEGER      | 기본 샤드 노드 번호                                          |
| DEFAULT_PARTITION_NAME | VARCHAR(128) | 기본 파티션 이름                                             |
| SMN                    | BIGINT       | 샤드 메타 번호                                               |

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

샤드 객체의 기본 샤드 노드를 나타낸다. 분산 설정이 완전하지 않을 경우 설정 기준
이외의 데이터가 저장되는 샤드 노드이다.

##### DEFAULT_PARTITION_NAME

샤드 객체의 기본 샤드 노드로 분산된 파티션의 이름이다.

##### SMN

샤드 메타에 대한 버전 관리 번호를 나타낸다.

### SYS_SHARD.RANGES\_

샤드 키 분산 테이블(HASH, RANGE, LIST, COMPOSITE)의 분산 정보를 기록하는 메타
테이블이다.

| Column name    | Type         | Description                               |
| -------------- | ------------ | ----------------------------------------- |
| SHARD_ID       | INTEGER      | 샤드 객체 식별자                          |
| PARTITION_NAME | VARCHAR(128) | 샤드 객체의 파티션 이름                    |
| VALUE          | VARCHAR(100) | 샤드 키 값                                |
| SUB_VALUE      | VARCHAR(100) | 서브 샤드 키 값                           |
| NODE_ID        | INTEGER      | 샤드 노드 번호                            |
| SMN            | BIGINT       | 샤드 메타 번호                            |
| REPLICA_SET_ID | INTEGER      | 샤드 객체와 연결된 레플리카 셋의 식별번호 |

#### 칼럼 정보

##### SHARD_ID

샤드 객체의 번호를 나타낸다.

##### PARTITION_NAME

샤드 객체의 파티션 이름을 나타낸다. 

##### VALUE

샤드 키 값을 나타낸다.

##### SUB_VALUE

서브 샤드 키 값을 나타낸다.

##### NODE_ID

VALUE와 SUB_VALUE를 기준으로 저장되는 데이터의 노드 번호를 나타낸다.

##### SMN

샤드 메타에 대한 버전 관리 번호를 나타낸다.

##### REPLICA_SET_ID

샤드 객체와 연결된 레플리카 셋의 식별 번호를 나타낸다.

### SYS_SHARD.CLONES\_

샤드 객체에 복제 분산 방식이 적용된 분산 정보를 기록하는 메타 테이블이다.

| Column name | Type    | Description             |
| ----------- | ------- | ----------------------- |
| SHARD_ID    | INTEGER | 샤드 객체 식별자        |
| NODE_ID     | INTEGER | 샤드 노드의 지역 식별자 |
| SMN         | BIGINT  | 샤드 메타 번호          |

#### 칼럼 정보

##### SHARD_ID

샤드 객체 번호를 나타낸다.

##### NODE_ID

데이터가 복제 저장되는 샤드 노드의 지역 식별자 번호를 나타낸다.

##### SMN

샤드 메타에 대한 버전 관리 번호를 나타낸다.

### SYS_SHARD.SOLOS\_

샤드 객체에 독립 분산 방식이 적용된 샤드 테이블 정보를 기록하는 메타 테이블이다.

| Column name    | Type    | Description                               |
| -------------- | ------- | ----------------------------------------- |
| SHARD_ID       | INTEGER | 샤드 객체 식별자                          |
| NODE_ID        | INTEGER | 샤드 노드의 지역 식별자                   |
| SMN            | BIGINT  | 샤드 메타 번호                            |
| REPLICA_SET_ID | INTEGER | 샤드 객체와 연결된 레플리카 셋의 식별번호 |

#### 칼럼 정보

##### SHARD_ID

샤드 객체 번호를 나타낸다.

##### NODE_ID

데이터가 독립 저장되는 샤드 노드의 지역 식별자 번호를 나타낸다.

##### SMN

샤드 메타에 대한 버전 관리 번호를 나타낸다.

##### REPLICA_SET_ID

샤드 객체와 연결된 레플리카 셋의 식별 번호를 나타낸다.

### SYS_SHARD.REPLICA_SETS_

Altibase Sharding 시스템에서 무중단 서비스를 제공하기 위해 생성한 데이터 복제(Replication)간의 관계를 나타내는 레플리카 셋을 저장한 메타 테이블이다.

| Column name                | Type        | Description                           |
| -------------------------- | ----------- | ------------------------------------- |
| REPLICA_SET_ID             | INTEGER     | 레플리카 셋의 식별자                  |
| PRIMARY_NODE_NAME          | VARCHAR(40) | 레플리카 셋과 연결된 주 노드 이름     |
| FIRST_BACKUP_NODE_NAME     | VARCHAR(40) | 레플리카 셋의 첫번째 Backup 노드 이름 |
| SECOND_BACKUP_NODE_NAME    | VARCHAR(40) | 레플리카 셋의 두번째 Backup 노드 이름 |
| FIRST_REPLICATION_NAME     | VARCHAR(40) | 첫번째 Backup의 이중화 이름           |
| FIRST_REPL_FROM_NODE_NAME  | VARCHAR(40) | 첫번째 Backup의 송신자 노드의 이름    |
| FIRST_REPL_TO_NODE_NAME    | VARCHAR(40) | 첫번째 Backup의 수신자 노드의 이름    |
| SECOND_REPLICATION_NAME    | VARCHAR(40) | 두번째 Backup의 이중화 이름           |
| SECOND_REPL_FROM_NODE_NAME | VARCHAR(40) | 두번째 Backup의 송신자 노드의 이름    |
| SECOND_REPL_TO_NODE_NAME   | VARCHAR(40) | 두번째 Backup의 수신자 노드의 이름    |
| SMN                        | BIGINT      | 샤드 메타 번호                        |

#### 칼럼 정보

##### REPLICA_SET_ID

레플리카 셋의 식별 번호를 나타낸다.

##### PRIMARY_NODE_NAME

레플리카 셋과 연결된 샤드 객체가 저장되어 있는 NODE의 이름을 나타낸다.

##### FIRST_BACKUP_NODE_NAME

레플리카 셋의 첫번째 Backup을 담당하는 노드 이름을 나타낸다.

##### SECOND_BACKUP_NODE_NAME

레플리카 셋의 두번째 Backup을 담당하는 노드 이름을 나타낸다.

##### FIRST_REPLICATION_NAME

첫번째 Backup의 이중화 이름을 나타낸다.

##### FIRST_REPL_FROM_NODE_NAME

첫번째 Backup을 전송하는 송신자 노드의 이름을 나타낸다.

##### FIRST_REPL_TO_NODE_NAME

첫번째 Backup을 전송받는 수신자 노드의 이름을 나타낸다.

##### SECOND_REPLICATION_NAME

두번째 Backup의 이중화 이름을 나타낸다.

##### SECOND_REPL_FROM_NODE_NAME

두번째 Backup을 전송하는 송신자 노드의 이름을 나타낸다.

##### SECOND_REPL_TO_NODE_NAME

두번째 Backup을 전송받는 수신자 노드의 이름을 나타낸다.

##### SMN

샤드 메타에 대한 버전 관리 번호를 나타낸다.

### SYS_SHARD.FAILOVER_HISTORYS_

Failover 발생시 레플리카 셋(ReplicaSet)의 변경 내역을 저장한 메타 테이블이다.

| Column name                | Type        | Description                           |
| -------------------------- | ----------- | ------------------------------------- |
| REPLICA_SET_ID             | INTEGER     | 레플리카 셋의 식별자                  |
| PRIMARY_NODE_NAME          | VARCHAR(40) | 레플리카 셋과 연결된 주 노드 이름     |
| FIRST_BACKUP_NODE_NAME     | VARCHAR(40) | 레플리카 셋의 첫번째 Backup 노드 이름 |
| SECOND_BACKUP_NODE_NAME    | VARCHAR(40) | 레플리카 셋의 두번째 Backup 노드 이름 |
| FIRST_REPLICATION_NAME     | VARCHAR(40) | 첫번째 Backup의 이중화 이름           |
| FIRST_REPL_FROM_NODE_NAME  | VARCHAR(40) | 첫번째 Backup의 송신자 노드의 이름    |
| FIRST_REPL_TO_NODE_NAME    | VARCHAR(40) | 첫번째 Backup의 수신자 노드의 이름    |
| SECOND_REPLICATION_NAME    | VARCHAR(40) | 두번째 Backup의 이중화 이름           |
| SECOND_REPL_FROM_NODE_NAME | VARCHAR(40) | 두번째 Backup의 송신자 노드의 이름    |
| SECOND_REPL_TO_NODE_NAME   | VARCHAR(40) | 두번째 Backup의 수신자 노드의 이름    |
| SMN                        | BIGINT      | 샤드 메타 번호                        |

#### 칼럼 정보

##### REPLICA_SET_ID

레플리카 셋의 식별 번호를 나타낸다.

##### PRIMARY_NODE_NAME

레플리카 셋과 연결된 샤드 객체가 저장되어 있는 NODE의 이름을 나타낸다.

##### FIRST_BACKUP_NODE_NAME

레플리카 셋의 첫번째 Backup을 담당하는 노드 이름을 나타낸다.

##### SECOND_BACKUP_NODE_NAME

레플리카 셋의 두번째 Backup을 담당하는 노드 이름을 나타낸다.

##### FIRST_REPLICATION_NAME

첫번째 Backup의 이중화 이름을 나타낸다.

##### FIRST_REPL_FROM_NODE_NAME

첫번째 Backup을 전송하는 송신자 노드의 이름을 나타낸다.

##### FIRST_REPL_TO_NODE_NAME

첫번째 Backup을 전송받는 수신자 노드의 이름을 나타낸다.

##### SECOND_REPLICATION_NAME

두번째 Backup의 이중화 이름을 나타낸다.

##### SECOND_REPL_FROM_NODE_NAME

두번째 Backup을 전송하는 송신자 노드의 이름을 나타낸다.

##### SECOND_REPL_TO_NODE_NAME

두번째 Backup을 전송받는 수신자 노드의 이름을 나타낸다.

##### SMN

샤드 메타에 대한 버전 관리 번호를 나타낸다.

### 성능 뷰 (Performance View)

성능 뷰 (performance view)란 메모리에 존재하는 구조이지만 일반 테이블 형태로 제공되어 시스템 메모리, 프로세스 상태, 세션, 버퍼, 쓰레드 등에 대한 Altibase 시스템 내부 정보를 사용자에게 제공하는 뷰이다.

사용자가 테이블에 저장된 데이터를 검색하기 위하여 SQL을 사용하는 것처럼, Altibase 운용 시 사용되는 메모리 객체 (예. 세션 정보, 로그 정보)에 관한 정보를 SQL문을 이용하여 성능 뷰로부터 쉽게 검색할 수 있다.

Altibase Sharding에서 성능 뷰는 단일 샤드 노드에서 실행중인 프로세스에 대한 정보를 의미하며 현재 접속된 시스템에 대한 정보를 보여준다.

Altibase에서 제공하는 성능 뷰를 통해서 단일 샤드 노드의 다양한 실행 정보를 얻을수 있으며 자세한 내용은 *General Reference* 의 성능 뷰를 참고한다.

### 샤드 성능 뷰 (Shard Performance View)

Altibase Sharding에서 제공하는 샤딩 전용의 성능 뷰로 전체 샤딩 시스템과 관련한 내부 정보(예. 샤드 세션 정보)를 사용자가 모니터링 할 수 있다.

이 절에서는 Altibase Sharding이 지원하는 샤드 성능 뷰의 구조 및 기능, 종류, 조회 방법, 그리고 각 뷰에서 제공하는 정보에 대해 설명한다.

#### 구조 및 기능

기존의 성능 뷰와 다르게 샤드 성능 뷰는 전체 샤딩 시스템과 연관된 정보를 한눈에 볼 수 있도록 제공한다.

예를들어, 사용자는 전체 샤딩 시스템의 프로퍼티 설정을 보기 위해서 각 노드에 접속 후 해당 노드의 성능 뷰를 모두 검색해 볼 수 있다. 그러나, 이와 같은 방법으로 전체 샤딩 시스템의 프로퍼티를 검색하는 것은 샤드 노드가 늘 어남에 따라 사용자의 불편을 증가시킨다.

그러므로, 전체 샤드 시스템의 프로퍼티를 검색하기 위해서 특정 샤드 노드에 접속해서 샤드 성능 뷰를 통해 서비스 중인 샤드 노드의 프로퍼티를 검색할 수 있다.

이와 같이 사용자는 샤드 성능 뷰를 통해 편리하게 전체 시스템을 모니터링 할 수 있다.

#### 샤드 성능 뷰의 조회 방법

샤드 성능 뷰의 전체 목록은 iSQL에서 다음과 같이 조회할 수 있다.

iSQL\> SELECT \* FROM S\$TAB;

샤드 성능 뷰의 스키마는 일반 테이블과 마찬가지로 iSQL 에서 DESC 명령어를 통해 확인할 수 있고, 데이터는 일반 테이블과 동일하게 SELECT문을 이용하여 검색할 수 있다.

#### 샤드 성능 뷰의 종류

샤드 성능 뷰의 이름은 S\$로 시작한다. 아래 표는 전체 샤드 성능 뷰의 목록이다.

| **이름**           | **설명**                                                     |
| ------------------ | ------------------------------------------------------------ |
| S\$CONNECTION_INFO | 현재 세션에서의 코디네이팅 샤드 노드와 다른 샤드 노드의 연결 상태에 대한 정보 |
| S\$PROPERTY        | 모든 샤드 노드의 시스템 프로퍼티 정보                        |
| S\$SESSION         | 모든 샤드 노드의 샤드 세션에 대한 세션 정보                  |
| S\$STATEMENT       | 모든 샤드 노드의 세션에서 수행되는 모든 구문 정보            |

### S\$CONNECTION_INFO

현재 세션에서 코디네이터가 연결한 접속 상태에 대한 정보를 보여주는 성능 뷰 이다.

| Column name  | Type        | Description                           |
| ------------ | ----------- | ------------------------------------- |
| NODE_ID      | INTEGER     | 샤드 노드의 지역 식별자               |
| NODE_NAME    | VARCHAR(40) | 샤드 노드 이름                        |
| COMM_NAME    | VARCHAR(64) | 접속 정보                             |
| TOUCH_COUNT  | INTEGER     | 현재 트랜잭션의 DML 발생 횟수         |
| LINK_FAILURE | INTEGER     | 샤드 노드의 연결 상태 0: 정상 1: 실패 |

#### 칼럼 정보

##### NODE_ID

연결된 샤드 노드의 지역 식별자를 나타낸다.

##### NODE_NAME

연결된 샤드 노드의 이름을 나타낸다.

##### COMM_NAME

샤드 노드와의 현재 접속 상태를 나타낸다.

##### TOUCH_COUNT

샤드 노드와의 연결된 세션 중 현재 트랜잭션에서 발생한 DML 횟수를 나타낸다.

##### LINK_FAILURE

조회 시점의 샤드 노드와의 연결 상태를 나타낸다.

### S\$PROPERTY

샤딩 시스템의 각 노드에 설정된 시스템 프로퍼티의 정보를 보여준다.

| Column name | Type         | Description                    |
| ----------- | ------------ | ------------------------------ |
| NODE_NAME   | VARCHAR(256) | 샤드 노드 이름                 |
| 그 외 컬럼  |              | 샤드 노드의 V$PROPERTY 와 동일 |

#### 칼럼 정보

##### NODE_NAME

노드의 이름을 나타낸다.

##### 그 외 컬럼

위 항목을 제외한 모든 칼럼은 *General Reference* 의 V\$PROPERTY 의 칼럼 정보를 참고한다.

### S\$SESSION

샤드 세션과 관련한 모든 샤드 노드의 세션에 대한 정보를 보여준다.

| Column name        | Type        | Description                          |
| ------------------ | ----------- | ------------------------------------ |
| ID                 | VARCHAR(20) | 샤드 세션 식별자                     |
| SHARD_META_NUMBER  | BIGINT      | 세션이 인식하고 있는 SMN             |
| NODE_NAME          | BIGINT      | 샤드 노드 이름                       |
| SHARD_CLIENT       | VARCHAR(1)  | 샤드 클라이언트 라이브러리 사용 유무 |
| SHARD_SESSION_TYPE | VARCHAR(1)  | 샤드 세션 유형                       |
| SESSION_ID         | BIGINT      | 샤드 노드의 V\$SESSION.ID            |
| GLOBAL_TRANSACTION_LEVEL | INTEGER | 글로벌 트랜잭션 레벨 |
| 그 외 컬럼         |             | 샤드 노드의 V$SESSION 과 동일        |

#### 칼럼 정보

##### ID

샤드 세션을 구별하는 고유 식별자이다.

##### SHARD_META_NUMBER

세션이 인식하고 있는 SMN 으로 자세한 내용은 샤드 메타 설정의 Session SMN 을 참고한다.

##### NODE_NAME

샤드 노드 이름을 나타낸다.

##### SHARD_CLIENT

세션의 샤드 클라이언트 라이브러리의 사용 여부이다.

- Y : 샤드 클라이언트 라이브러리 사용
- N : 샤드 클라이언트 라이브러리 미사용

##### SHARD_SESSION_TYPE

세션의 샤드 세션 타입이다.

- U : 사용자와 코디네이터간의 사용자(User) 세션
- C : 코디네이터와 샤드 데이터간의 코디네이터(Coordinator) 세션
- L : 사용자와 샤드 데이터간의 샤드 라이브러리(Library) 세션

##### SESSION_ID

샤드 노드의 세션 식별자로 샤드 노드의 V$SESSION.ID 와 동일한 값이다.

##### GLOBAL_TRANSACTION_LEVEL

세션에 설정된 글로벌 트랜잭션 레벨을 나타낸다.

1 : 다중 노드 트랜잭션 (multiple node transaction)

샤딩 메뉴얼의 샤드 트랜잭션 항목을 참조한다

##### 그 외 컬럼

위 항목을 제외한 모든 칼럼은 *General Reference* 의 V\$SESSION 의 칼럼 정보를 참고한다.

### S\$STATEMENT

모든 샤드 노드의 세션 별로 실행중이거나 가장 최근 실행된 구문에 대한 정보를 보여준다.

| Column name        | Type        | Description                       |
| ------------------ | ----------- | --------------------------------- |
| SHARD_SESSION_ID   | VARCHAR(20) | 샤드 세션 식별자                  |
| NODE_NAME          | VARCHAR(40) | 샤드 노드 이름                    |
| SHARD_SESSION_TYPE | VARCHAR(1)  | 세션의 샤드 세션 유형             |
| QUERY_TYPE         | VARCHAR(1)  | 사용자 쿼리에 대한 샤드 쿼리 타입 |
| 그 외 컬럼         |             | 샤드 노드의 V$STATEMENT 와 동일   |

#### 칼럼 정보

##### SHARD_SESSION_ID

구문이 수행되는 세션의 샤드 세션 식별자이다.

##### NODE_NAME

구문이 수행되는 샤드 노드 이름이다.

##### SHARD_SESSION_TYPE

구문이 수행되는 세션의 샤드 세션 유형으로 S$SESSION.SHARD_SESSION_TYPE 과 동일하다.

##### QUERY_TYPE

Altibase Sharding 관점으로 분류한 사용자 쿼리 유형이다.

- S (Shard query) : 분산 수행 결과와 단일 수행 결과의 정합성이 보장되는 경우
- N (Non-shard query) : 분산 수행 결과와 단일 수행 결과의 정합성이 보장되지 않는 경우

단, 코디네이터 커넥션을 통해 수행되는 구문의 경우 분석 대상이 아니므로 '-' 로 표시된다.

##### 그 외 컬럼

위 항목을 제외한 모든 칼럼은 *General Reference*의 V\$STATEMENT의 칼럼 정보를 참고한다.

5.Altibase Sharding 패키지
------------------------

Altibase Sharding 패키지를 구성하는 프로시저와 함수에 대해 설명한다.

### DBMS_SHARD

DBMS_SHARD 패키지는 Altibase Sharding의 샤드 설정과 관리에 사용한다.

아래의 표와 같이 DBMS_SHARD 패키지를 구성하는 프로시저와 함수를 제공한다.

| 프로시저 및 함수              | 설명                                                         |
| ----------------------------- | ------------------------------------------------------------ |
| CREATE_META                   | 샤드 노드에서 샤드 메타 테이블을 생성한다.                   |
| RESET_SHARD_NODE_ID           | 현재 접속 노드 식별자를 변경한다.                            |
| EXECUTE_IMMEDIATE             | 샤드 노드로 ad-hoc 쿼리를 수행한다.                          |
| SET_REPLICATION               | 샤딩 클러스터 시스템의 데이터 복제 방식을 설정한다.          |
| SET_NODE                      | 샤드 노드를 등록한다.                                        |
| RESET_NODE_EXTERNAL           | 샤드 라이브러리 또는 외부 응용프로그램에서 연결할 샤드 노드 접속 정보를 변경한다. |
| RESET_NODE_INTERNAL           | 코디네이터가 연결할 샤드 노드 접속 정보를 변경한다.          |
| SET_SHARD_TABLE               | 샤드 테이블을 등록한다.                                      |
| SET_SHARD_TABLE_COMPOSITE     | 복합 샤드 키를 갖는 샤드 테이블을 등록한다.                  |
| SET_SHARD_PROCEDURE           | 샤드 프로시저를 등록한다.                                    |
| SET_SHARD_PROCEDURE_COMPOSITE | 복합 샤드 키를 갖는 샤드 프로시저를 등록한다.                |
| SET_SHARD_PARTITION_NODE      | 테이블의 파티셔닝 방식과 같은 방식으로 분산정보를 등록한다.  |
| SET_SHARD_HASH                | HASH 방식의 분산정보를 등록한다.                             |
| SET_SHARD_RANGE               | RANGE 방식의 분산정보를 등록한다.                            |
| SET_SHARD_LIST                | LIST 방식의 분산정보를 등록한다.                             |
| SET_SHARD_CLONE               | CLONE 방식의 분산정보를 등록한다.                            |
| SET_SHARD_SOLO                | SOLO 방식의 분산정보를 등록한다.                             |
| RESET_SHARD_RESIDENT_NODE     | 등록된 분산 정보의 샤드 노드를 변경한다.                     |
| RESET_SHARD_PARTITION_NODE    | 등록된 분산 정보의 샤드 노드를 변경한다.                     |
| SET_SHARD_COMPOSITE           | 복합 샤드 키 방식의 분산정보를 등록한다.                     |
| CHECK_DATA                    | 샤드 키와 데이터의 유효성을 확인한다.                        |
| REBUILD_DATA                  | 변경된 샤드 키 분산방식에 따라 모든 샤드 노드의 데이터를 재분배한다. |
| REBUILD_DATA_NODE             | 변경된 샤드 키 분산방식에 따라 특정 샤드 노드의 데이터를 재분배한다. |
| UNSET_NODE                    | 샤드 노드를 해제한다.                                        |
| UNSET_SHARD_TABLE             | 샤드 테이블을 해제한다.                                      |
| UNSET_SHARD_TABLE_BY_ID       | shard_id로 샤드 테이블을 해제한다.                           |
| UNSET_SHARD_PROCEDURE         | 샤드 프로시저를 해제한다.                                    |
| UNSET_SHARD_PROCEDURE_BY_ID   | shard_id로 샤드 프로시저를 해제한다.                         |

#### CREATE_META

##### 구문

```
CREATE_META()
```

##### 파라미터

| 이름          | 입출력 | 데이터 타입 | 설명             |
| ------------- | ------ | ----------- | ---------------- |
| SHARD_NODE_ID | IN     | INTEGER     | 샤드 노드 식별자 |

##### 설명

현재 접속 노드에서 샤드 메타 테이블을 생성한다.

create_meta를 수행하면 SYS_SHARD 계정이 생성되고 샤드에 메타를 저장할 테이블과
인덱스, 시퀀스가 생성된다. 이후부터 Altibase Sharding 기능을 사용할 수 있다.

SHARD_NODE_ID 파라미터는 샤드 노드 식별자이며 DBMS_SHARD.SET_LOCAL_NODE 혹은 DBMS_SHARD.RESET_SHARD_NODE_ID 를 통해서 변경 가능하다.

SHARD_NODE_ID는 전체 샤딩 시스템에서 유일한 값이어야 한다.

##### 예제

```
iSQL> EXEC dbms_shard.create_meta();
Execute success.
```

> ##### 주의 사항
>
> - 메타 테이블을 삭제하면 샤딩을 사용할 수 없으므로 주의해야 한다.
> - SHARD_NODE_ID 값 범위: 0\~65535

#### RESET_SHARD_NODE_ID

##### 구문

```
RESET_SHARD_NODE_ID(SHARD_NODE_ID in integer)
```

##### 파라미터

| 이름          | 입출력 | 데이터 타입 | 설명             |
| ------------- | ------ | ----------- | ---------------- |
| SHARD_NODE_ID | IN     | INTEGER     | 샤드 노드 식별자 |

##### 설명

샤드 노드 식별자를 변경한다.

##### 예제

```
iSQL> EXEC dbms_shard.reset_SHARD_NODE_ID(1);
Execute success.
```

> ##### 주의 사항
>
> - SHARD_NODE_ID는 Altibase Sharding 시스템 내에서 구별 가능한 유일값이어야 한다.
> - SHARD_NODE_ID 값 범위: 0\~65535

#### EXECUTE_IMMEDIATE

##### 구문

```
EXECUTE_IMMEDIATE(
 query     in varchar(65534),
 node_name in varchar(10) default NULL)
```

##### 파라미터

| 이름      | 입출력 | 데이터 타입    | 설명      |
| --------- | ------ | -------------- | --------- |
| query     | IN     | VARCHAR(65534) | 샤드 쿼리 |
| node_name | IN     | VARCHAR(10)    | 샤드 노드 |

##### 설명

샤드 노드에서 임의의 샤드 노드에 특정(ad-hoc) 쿼리를 수행한다. node_name을
지정하지 않으면, 모든 샤드 노드에 수행한다.

##### 예제

```
iSQL> EXEC dbms_shard.execute_immediate(‘TRUNCATE TABLE s1’,’node1’);
Execute success.
```

#### SET_REPLICATION

##### 구문

```
SET_REPLICATION(
 k_safety          in integer,
 replication_mode  in varchar(10) default NULL,
 parallel_count    in integer default NULL )
```

##### 파라미터

| 이름             | 입출력 | 데이터 타입 | 설명                               |
| ---------------- | ------ | ----------- | ---------------------------------- |
| k_safety         | IN     | INTEGER     | 시스템 내에서 유지할 복제본의 갯수 |
| replication_mode | IN     | VARCHAR(10) | 이중화에서 사용할 복제 방식        |
| parallel_count   | IN     | INTEGER     | 이중화 병렬 적용자의 수            |

##### 설명

샤딩 클러스터 시스템에서 사용할 복제 정보를 입력한다.   

##### 예제

\<질의\> 샤딩 클러스터 시스템에서 2개의 복제본을 유지하고 동기복제 방식을 사용하도록 설정한다.

```
iSQL>  EXEC DBMS_SHARD.SET_REPLICATION(2,'consistent', 1);
```

#### SET_NODE

##### 구문

```
SET_NODE(
 node_name          in varchar(10),
 host_ip            in varchar(16),
 port_no            in integer,
 alternate_host_ip  in varchar(16) default NULL,
 alternate_port_no  in integer default NULL,
 conn_type          in integer default NULL)
```

##### 파라미터

| 이름              | 입출력 | 데이터 타입 | 설명                                                         |
| ----------------- | ------ | ----------- | ------------------------------------------------------------ |
| node_name         | IN     | VARCHAR(10) | 샤드 노드 이름                                               |
| host_ip           | IN     | VARCHAR(16) | 샤드 노드의 IP                                               |
| port_no           | IN     | INTEGER     | 샤드 노드의 PORT 번호                                        |
| alternate_host_ip | IN     | VARCHAR(16) | 샤드 노드의 Alternate IP                                     |
| alternate_port_no | IN     | INTEGER     | 샤드 노드의 Alternate PORT 번호                              |
| conn_type         | IN     | INTEGER     | 내부적으로 사용되는 코디네이터 연결 방식으로 지원 타입은 *Altibase Sharding 통신 방법*의 코디네이터 커넥션을 참고한다. |

##### 설명

샤드 노드에서 샤드 노드의 이름과 IP 및 PORT 정보와 Alternate IP 및 Alternate
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
iSQL> EXEC dbms_shard.set_node('node4', '192.168.1.30', 20300, '192.168.1.31',
20400, 1);
Execute success.
```

#### RESET_NODE_EXTERNAL

##### 구문

```
RESET_NODE_EXTERNAL(node_name in varchar(10),
                    host_ip   in varchar(16),
                    port_no   in integer,
                    alternate_host_ip in varchar(16),
                    alternate_port_no in integer)
```

##### 파라미터

| 이름              | 입출력 | 데이터 타입 | 설명                            |
| ----------------- | ------ | ----------- | ------------------------------- |
| node_name         | IN     | VARCHAR(10) | 샤드 노드 이름                  |
| host_ip           | IN     | VARCHAR(16) | 샤드 노드의 Alternate IP        |
| port_no           | IN     | INTEGER     | 샤드 노드의 PORT 번호           |
| alternate_host_ip | IN     | VARCHAR(16) | 샤드 노드의 Alternate IP        |
| alternate_port_no | IN     | INTEGER     | 샤드 노드의 Alternate PORT 번호 |

##### 설명

샤드 메타에 설정한 외부(샤드 라이브러리 연결) 연결 접속 정보를 변경한다.

RESET_NODE_EXTERNAL 프로시저를 이용하여 샤드라이브러리와 샤드 노드 간 접속
정보를 변경 할 수 있으며,  
내부적으로 사용되는 코디네이터연결 접속 정보 변경을 위해서는 RESET_NODE_INTERNAL
프로시저를 사용해야 한다.

##### 예제

```
iSQL> EXEC dbms_shard.reset_node_external('node1', '192.168.100.1', 20300,
'192.168.100.2', 20300 );
Execute success.
```

#### RESET_NODE_INTERNAL

##### 구문

```
RESET_NODE_INTERNAL(node_name          in varchar(10),
                    host_ip            in varchar(16),
                    port_no            in integer,
                    alternate_host_ip  in varchar(16),
                    alternate_port_no  in integer,
                    conn_type          in integer)
```

##### 파라미터

| 이름              | 입출력 | 데이터 타입 | 설명                                                         |
| ----------------- | ------ | ----------- | ------------------------------------------------------------ |
| node_name         | IN     | VARCHAR(10) | 샤드 노드 이름                                               |
| host_ip           | IN     | VARCHAR(16) | 샤드 노드의 IP                                               |
| port_no           | IN     | INTEGER     | 샤드 노드의 PORT 번호                                        |
| alternate_host_ip | IN     | VARCHAR(16) | 샤드 노드의 Alternate IP                                     |
| alternate_port_no | IN     | INTEGER     | 샤드 노드의 Alternate PORT 번호                              |
| conn_type         | IN     | INTEGER     | 코디네이터 연결 방식으로 지원 타입은 *Altibase Sharding 통신 방법*의 코디네이터 커넥션을 참고한다. |

##### 설명

샤드 메타에 설정한 내부(코디네이터 연결) 연결 접속 정보를 변경한다..

RESET_NODE_INTERNAL 프로시저를 이용하여 코디네이터와 샤드 노드 간 접속 정보를
변경 할 수 있으며,  
샤드라이브러리에서 사용하는 외부 응용프로그램과 샤드 노드 간 접속 정보 변경을
위해서는 RESET_NODE_EXTERNAL 프로시저를 사용해야 한다.

##### 예제

```
iSQL> EXEC dbms_shard.reset_node_external ('node1', '192.168.100.1', 20300,
'192.168.100.2', 20300, 1);
Execute success.
```

#### SET_SHARD_TABLE

##### 구문

```
SET_SHARD_TABLE(
 user_name    		         in varchar(128),
 table_name        			 in varchar(128),
 split_method    			 in varchar(1) default NULL,
 partition_key_column_name   in varchar(128) default NULL,
 default_node_name 			 in varchar(40) default NULL)
```

##### 파라미터

| 이름                      | 입출력 | 데이터 타입  | 설명                                                         |
| ------------------------- | ------ | ------------ | ------------------------------------------------------------ |
| user_name                 | IN     | VARCHAR(128) | 테이블 소유자의 이름                                         |
| table_name                | IN     | VARCHAR(128) | 테이블 이름                                                  |
| split_method              | IN     | VARCHAR(1)   | 분산 방식 H: 해시 분산 방식 R: 범위 분산 방식 L: 리스트 분산 방식 C: 복제 분산 방식 S: 독립 분산 방식 |
| partition_key_column_name | IN     | VARCHAR(128) | 샤드 키 컬럼 이름                                            |
| default_node_name         | IN     | VARCHAR(40)  | 기본 샤드 노드                                               |

**설명**

모든 샤드 노드에 샤드 테이블 정보를 설정하고 복제용 테이블을 생성한다.

분산 방식을 지정하지 않을 경우, 테이블의 파티션 정보를 읽어 자동으로 설정한다. 
테이블의 파티션 키가 두개 이상이면 자동으로 선택하지 못하고 에러가 발생한다.

기본 샤드 노드란 샤드 키 분산 객체에 한해 분산 정보가 정의되지 않은 경우에
선택되는 샤드 노드를 의미하며, 지정하지 않을 수도 있다. 기본 샤드 노드를
지정하지 않을 경우, 샤드 키 분산 정보에 맞지 않는 샤드 키 값이 입력되면, 처리할
수 없으므로 에러가 발생한다.

파티션 테이블을 대상으로 할 경우 기본 샤드 노드를 지정하였으면 K-safety 값에 따라 기본 파티션의 복제를(Replication) 생성한다.

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
iSQL> EXEC dbms_shard.set_shard_table('sys','t6');
Execute success.
```

> ##### 주의사항
>
> - 샤드 테이블을 설정하기 위해서는 반드시 샤드 노드에 동일한 테이블 스키마가
>   생성되어야 한다.
> - 분산 방식을 지정할때 반드시 테이블의 파티셔닝 방법과 같은 분산 방식을 지정하여야 한다.
> - 테이블을 제거(drop)하더라도 샤드 테이블 정보는 삭제되지 않는다.
> - 일반 테이블은 K-safety 값이 0일 경우에만 샤드 테이블로 설정할 수 있다.
> - Non-Autocommit 에서만 수행 할 수 있다.
> - Global Transaction Level 2 이상에서만 수행 할 수 있다.

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

| 이름                | 입출력 | 데이터 타입  | 설명                                                         |
| ------------------- | ------ | ------------ | ------------------------------------------------------------ |
| user_name           | IN     | VARCHAR(128) | 테이블 소유자의 이름                                         |
| table_name          | IN     | VARCHAR(128) | 테이블 이름                                                  |
| split_method        | IN     | VARCHAR(1)   | 샤드 키 분산 방식 H: 해시 분산 방식 R: 범위 분산 방식 L: 리스트 분산 방식 |
| key_column_name     | IN     | VARCHAR(128) | 샤드 키 컬럼 이름                                            |
| sub_split_method    | IN     | VARCHAR(1)   | 서브 샤드 키 분산 방식 H: 해시 분산 방식 R: 범위 분산 방식 L: 리스트 분산 방식 |
| sub_key_column_name | IN     | VARCHAR(128) | 서브 샤드 키 컬럼 이름                                       |
| default_node_name   | IN     | VARCHAR(40)  | 기본 샤드 노드(default node)                                 |

**설명**

모든 샤드 노드에서 복합 샤드 키를 적용하는 샤드 테이블의 정보를 설정하고 복제용 테이블을 생성한다.

##### 예제

```
iSQL> EXEC dbms_shard.set_shard_table_composite(‘sys’,’t6’,’L’,’i1’,'L','i2',’node3’);
Execute success.
```

> ##### 주의사항
>
> - 복합 샤드키를 적용한 샤드 테이블 역시 샤드 노드에 동일한 테이블 스키마가
>   생성되어야 한다.
> - 테이블을 제거(drop)하더라도 샤드 테이블 정보는 삭제되지 않는다.
> - 복합 샤드키를 사용할 경우 무중단 서비스(HA)를 제공하지 않는다. K-Safety 값을 0으로 설정하여야 한다.
> - 복합 샤드키를 사용할 경우 일반 테이블 대상으로만 수행 할 수 있다.
> - Non-Autocommit 에서만 수행 할 수 있다.
> - Global Transaction Level 2 이상에서만 수행 할 수 있다.

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

| 이름              | 입출력 | 데이터 타입  | 설명                                                         |
| ----------------- | ------ | ------------ | ------------------------------------------------------------ |
| user_name         | IN     | VARCHAR(128) | 프로시저 소유자의 이름                                       |
| proc_name         | IN     | VARCHAR(128) | 프로시저 이름                                                |
| split_method      | IN     | VARCHAR(1)   | 분산 방식 H: 해시 분산 방식 R: 범위 분산 방식 L: 리스트 분산 방식 C: 복제 분산 방식 S: 독립 분산 방식 |
| key_param_name    | IN     | VARCHAR(128) | 샤드 키 파라미터 이름                                        |
| default_node_name | IN     | VARCHAR(40)  | 기본 샤드 노드                                               |

##### 설명

모든 샤드 노드에 샤드 프로시저의 정보를 설정한다.

Altibase Sharding 에서 지원하는 분산 방법의 종류는 샤드 테이블과 동일하다.

##### 예제

```
iSQL> EXEC dbms_shard.set_shard_procedure('sys','proc1','H','p1','node3');
Execute success.
iSQL> EXEC dbms_shard.set_shard_procedure('sys','proc2','R','p1','node3');
Execute success.
iSQL> EXEC dbms_shard.set_shard_procedure('sys','proc3','L','p1','node3');
Execute success.
iSQL> EXEC dbms_shard.set_shard_procedure('SYS','proc4','C');
Execute success.
iSQL> EXEC dbms_shard.set_shard_procedure('SYS','proc5','S');
Execute success.
```

> ##### 주의사항
>
> - 샤드 프로시저를 설정하기 위해서는 반드시 샤드 노드에 동일한 프로시저가
>   생성되어야 한다.
> - 프로시저를 제거(drop)하더라도 샤드 프로시저 정보는 삭제되지 않는다.
> - Non-Autocommit 에서만 수행 할 수 있다.
> - Global Transaction Level 2 이상에서만 수행 할 수 있다.

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

| 이름               | 입출력 | 데이터 타입  | 설명                                                         |
| ------------------ | ------ | ------------ | ------------------------------------------------------------ |
| user_name          | IN     | VARCHAR(128) | 프로시저 소유자의 이름                                       |
| proc_name          | IN     | VARCHAR(128) | 프로시저 이름                                                |
| split_method       | IN     | VARCHAR(1)   | 샤드 키 파라미터 분산 방식 H: 해시 분산 방식 R: 범위 분산 방식 L: 리스트 분산 방식 |
| key_param_name     | IN     | VARCHAR(128) | 샤드 키 파라미터 이름                                        |
| sub_split_method   | IN     | VARCHAR(1)   | 서브 샤드 키 파라미터 분산 방식 H: 해시 분산 방식 R: 범위 분산 방식 L: 리스트 분산 방식 |
| sub_key_param_name | IN     | VARCHAR(128) | 서브 샤드 키 파라미터 이름                                   |
| default_node_name  | IN     | VARCHAR(40)  | 기본 샤드 노드(default node)                                 |

##### 설명

모든 샤드 노드에 복합 샤드 키를 적용하는 샤드 프로시저의 정보를 설정한다.

Altibase Sharding에서 지원하는 분산 방법의 종류는 샤드 테이블과 동일하다.

##### 예제

```
iSQL> EXEC dbms_shard.set_shard_procedure_composite('sys','proc6','L','p1', 'L','p2','node3');
Execute success.
```

> ##### 주의사항
>
> - 복합 샤드 키 프로시저를 설정하기 위해서는 반드시 샤드 노드에 동일한
>   프로시저가 생성되어야 한다.
> - 프로시저를 제거(drop)하더라도 샤드 프로시저 정보는 삭제되지 않는다.
> - Non-Autocommit 에서만 수행 할 수 있다.
> - Global Transaction Level 2 이상에서만 수행 할 수 있다.

#### SET_SHARD_PARTITION_NODE

##### 구문

```
SET_SHARD_PARTITION_NODE(
 user_name 	    in varchar(128),
 object_name    in varchar(128),
 partition_name in varchar(128),
 node_name      in varchar(10) )
```

##### 파라미터

| 이름           | 입출력 | 데이터 타입  | 설명               |
| -------------- | ------ | ------------ | ------------------ |
| user_name      | IN     | VARCHAR(128) | 객체 소유자의 이름 |
| object_name    | IN     | VARCHAR(128) | 객체 이름          |
| partition_name | IN     | VARCHAR(128) | 객체의 파티션 이름 |
| node_name      | IN     | VARCHAR(10)  | 샤드 노드          |

##### 설명

모든 샤드 노드에 샤드 객체의 정보를 설정하고 K-Safety 값에 따라 자동으로 복제(Replication) 되도록 한다.

샤드 객체의 분산 방식은 객체의 파티션 분할 방식과 같게 설정된다.

파티션 테이블이 아닌 객체는 설정할수 없다.

기본 파티션을 대상으로 수행 할 경우 샤드 객체의 기본 노드가 변경된다. 
기본 노드가 변경될 경우 기존에 데이터 복제가 존재하면 제거하고 지정된 기본 노드를 대상으로 새롭게 데이터 복제를 생성해 준다.

##### 예제

```
iSQL> EXEC dbms_shard.set_shard_partition_node('sys','t1','p1','node1');
Execute success.
iSQL> EXEC dbms_shard.set_shard_partition_node('sys','t1','p2','node2');
Execute success.
```

> ##### 주의사항
>
> - Non-Autocommit 에서만 수행 할 수 있다.
> - Global Transaction Level 2 이상에서만 수행 할 수 있다.

#### SET_SHARD_HASH

##### 구문

```
SET_SHARD_HASH(    user_name in varchar(128),
                   object_name in varchar(128),
                   hash_max in integer,
                   node_name in varchar(10))
```

##### 파라미터

| 이름        | 입출력 | 데이터 타입  | 설명                                        |
| ----------- | ------ | ------------ | ------------------------------------------- |
| user_name   | IN     | VARCHAR(128) | 객체 소유자의 이름                          |
| object_name | IN     | VARCHAR(128) | 객체 이름                                   |
| hash_max    | IN     | INTEGER      | 해시 분산의 상한값 [1-1000] (non-inclusive) |
| node_name   | IN     | VARCHAR(10)  | 기본 샤드노드                               |

##### 설명

모든 샤드 노드에 해시 방식으로 분산되는 샤드 객체의 정보를 설정하고 K-Safety 값에 따라 자동으로 복제(Replication) 되도록 한다. 

지정 가능한 해시 상한값은 [ 1 \~ 1000 ]으로 정의한다.

실제 샤드 키에 대한 해시 값은 [ 0 \~ 999 ]이다.

구간별로 샤드 노드를 적절하게 지정해야 하며, 만약 지정하지 않을 경우 기본 샤드
노드로 데이터가 분산된다.

##### 예제

\<질의\> sys.t1 테이블에 샤드 키의 hash 값에 따라 데이터가 다음과 같이 분산된다.

- 0 \~ 499는 node1으로 분산
- 500 \~ 799는 node2로 분산
- 나머지 hash 값(800 \~ 999)은 기본 샤드 노드로 분산

```
iSQL> EXEC dbms_shard.set_shard_table('sys','t1','H','i1','node3');
Execute success.
iSQL> EXEC dbms_shard.set_shard_hash('sys','t1',500,'node1');
Execute success.
iSQL> EXEC dbms_shard.set_shard_hash('sys','t1',800,'node2');
Execute success
```

> ##### 주의사항
>
> - Non-Autocommit 에서만 수행 할 수 있다.
> - Global Transaction Level 2 이상에서만 수행 할 수 있다.

#### SET_SHARD_RANGE

##### 구문

```
SET_SHARD_RANGE(     user_name    in  varchar(128),
                     object_name  in  varchar(128),
                     value_max    in  varchar(100),
                     node_name    in  varchar(10))
```

##### 파라미터

| 이름        | 입출력 | 데이터 타입  | 설명                                      |
| ----------- | ------ | ------------ | ----------------------------------------- |
| user_name   | IN     | VARCHAR(128) | 객체 소유자의 이름                        |
| object_name | IN     | VARCHAR(128) | 객체 이름                                 |
| value_max   | IN     | VARCHAR(100) | 범위 분산 샤드 키의 상한값(non-inclusive) |
| node_name   | IN     | VARCHAR(10)  | 기본 샤드 노드                            |

##### 설명

모든 샤드 노드에 범위 분산 방식으로 샤드 객체의 분산 정보를 설정하고 K-Safety 값에 따라 자동으로 복제(Replication) 되도록 한다.

##### 예제

\<질의\> sys.t2 테이블에 샤드 키 값에 따라 데이터가 다음과 같이 분산된다.

- 0 \~ 299는 node1으로 분산
- 300 \~ 599는 node2로 분산
- 나머지 값은 기본 샤드 노드로 분산

```
iSQL> EXEC dbms_shard.set_shard_table('sys','t2','R','i1','node3');
Execute success.
iSQL> EXEC dbms_shard.set_shard_range('sys','t2',300,'node1');
Execute success.
iSQL> EXEC dbms_shard.set_shard_range('sys','t2',600,'node2');
Execute success. 
```

> ##### 주의사항
>
> - Non-Autocommit 에서만 수행 할 수 있다.
> - Global Transaction Level 2 이상에서만 수행 할 수 있다.

#### SET_SHARD_LIST

##### 구문

```
SET_SHARD_LIST(    user_name    in  varchar(128),
                   object_name  in  varchar(128),
                   value        in  varchar(100),
                   node_name    in  varchar(10))
```

##### 파라미터

| 이름        | 입출력 | 데이터 타입  | 설명                           |
| ----------- | ------ | ------------ | ------------------------------ |
| user_name   | IN     | VARCHAR(128) | 객체 소유자의 이름             |
| object_name | IN     | VARCHAR(128) | 객체 이름                      |
| value       | IN     | VARCHAR(100) | 리스트 분산의 샤드 키의 최대값 |
| node_name   | IN     | VARCHAR(10)  | 기본 샤드 노드                 |

##### 설명

모든 샤드 노드에 리스트 분산 방식의 샤드 객체에 대한 분산 정보를 설정하고 K-Safety 값에 따라 자동으로 복제(Replication) 되도록 한다.

##### 예제

```
iSQL> EXEC dbms_shard.set_shard_list('sys','t3','1a','node1');
Execute success.
iSQL> EXEC dbms_shard.set_shard_list('sys','t3','2a','node2');
Execute success.
iSQL> EXEC dbms_shard.set_shard_list('sys','t3','3a','node3');
Execute success.
```

> ##### 주의사항
>
> - 리스트 분산 방식으로 설정할 경우 다수의 파티셔닝 조건 값을 갖는 파티션은 설정할 수 없다.
> - Non-Autocommit 에서만 수행 할 수 있다.
> - Global Transaction Level 2 이상에서만 수행 할 수 있다.

#### SET_SHARD_COMPOSITE

##### 구문

```
SET_SHARD_COMPOSITE(
 user_name    in  varchar(128),
 object_name  in  varchar(128),
 value        in  varchar(100),
 sub_value    in  varchar(100),
 node_name    in  varchar(10))
```

##### 파라미터

| 이름        | 입출력 | 데이터 타입  | 설명                  |
| ----------- | ------ | ------------ | --------------------- |
| user_name   | IN     | VARCHAR(128) | 객체 소유자의 이름    |
| object_name | IN     | VARCHAR(128) | 객체 이름             |
| value       | IN     | VARCHAR(100) | 샤드 키의 최대값      |
| sub_value   | IN     | VARCHAR(100) | 서브 샤드 키의 최대값 |
| node_name   | IN     | VARCHAR(10)  | 기본 샤드 노드        |

##### 설명

모든 샤드 노드에 복합 샤드 키를 적용한 샤드 객체의 분산 정보를 설정한다.

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

> ##### 주의사항
>
> - 복합 샤드 키 샤드 객체의 경우 K-Safety가 0 일 때만 설정 가능하기 때문에 데이터 복제(Replication)를 제공하지 않는다.
> - 복합 샤드키를 사용할 경우 일반 테이블 대상으로만 수행 할 수 있다.
> - Non-Autocommit 에서만 수행 할 수 있다.
> - Global Transaction Level 2 이상에서만 수행 할 수 있다.

#### SET_SHARD_CLONE

##### 구문

```
SET_SHARD_CLONE(user_name    in  varchar(128),
                object_name  in  varchar(128),
                node_name    in  varchar(10))
```

##### 파라미터

| 이름        | 입출력 | 데이터 타입  | 설명               |
| ----------- | ------ | ------------ | ------------------ |
| user_name   | IN     | VARCHAR(128) | 객체 소유자의 이름 |
| object_name | IN     | VARCHAR(128) | 객체 이름          |
| node_name   | IN     | VARCHAR(10)  | 샤드 노드          |

##### 설명

모든 샤드 노드에 복제 분산 방식으로 샤드 객체의 분산 정보를 설정한다.

##### 예제

```
iSQL> EXEC dbms_shard.set_shard_clone('sys','t4','node1');
Execute success.
iSQL> EXEC dbms_shard.set_shard_clone('sys','t4','node2');
Execute success.
iSQL> EXEC dbms_shard.set_shard_clone('sys','t4','node3');
```

> ##### 주의사항
>
> - Non-Autocommit 에서만 수행 할 수 있다.
> - Global Transaction Level 2 이상에서만 수행 할 수 있다.

#### SET_SHARD_SOLO

##### 구문

```
SET_SHARD_SOLO(user_name    in  varchar(128),
               object_name  in  varchar(128),
               node_name    in  varchar(10))
```

##### 파라미터

| 이름        | 입출력 | 데이터 타입  | 설명               |
| ----------- | ------ | ------------ | ------------------ |
| user_name   | IN     | VARCHAR(128) | 객체 소유자의 이름 |
| object_name | IN     | VARCHAR(128) | 객체 이름          |
| node_name   | IN     | VARCHAR(10)  | 샤드 노드          |

##### 설명

모든 샤드 노드에 독립 분산 방식의 샤드 객체의 분산 정보를 설정하고 K-Safety 값에 따라 자동으로 복제(Replication) 되도록 한다.

##### 예제

```
iSQL> EXEC dbms_shard.set_shard_solo('sys','t5','node1');
Execute success.
iSQL> EXEC dbms_shard.set_shard_solo('sys','proc5','node1');
Execute success.
```

> ##### 주의사항
>
> - Non-Autocommit 에서만 수행 할 수 있다.
> - Global Transaction Level 2 이상에서만 수행 할 수 있다.

#### RESET_SHARD_RESIDENT_NODE

##### 구문

```
RESET_SHARD_RESIDENT_NODE( user_name     in varchar(128),
                           object_name   in varchar(128),
                           old_node_name in varchar(10),
                           new_node_name in varchar(10),
                           value         in varchar(100) default NULL,
                           sub_value     in varchar(100) default NULL )
```

##### 파라미터

| 이름          | 입출력 | 데이터 타입  | 설명                  |
| ------------- | ------ | ------------ | --------------------- |
| user_name     | IN     | VARCHAR(128) | 객체 소유자의 이름    |
| object_name   | IN     | VARCHAR(128) | 객체 이름             |
| old_node_name | IN     | VARCHAR(10)  | 현재 노드 이름        |
| new_node_name | IN     | VARCHAR(10)  | 변경할 노드 이름      |
| value         | IN     | VARCHAR(100) | 샤드 키의 최대값      |
| sub_value     | IN     | VARCHAR(100) | 서브 샤드 키의 최대값 |

##### 설명

등록된 분산 정보의 샤드 노드를 변경한다.

##### 예제

```
iSQL> EXEC dbms_shard.set_shard_table('sys','t1','H','i1');
Execute success.
iSQL> EXEC dbms_shard.set_shard_hash('sys','t1',500,'node1');
Execute success.
iSQL> EXEC dbms_shard.set_shard_hash('sys','t1',1000,'node3');
Execute success.
iSQL> EXEC dbms_shard.reset_shard_resident_node('sys','t1','node3','node2',1000);
Execute success.
```

#### RESET_SHARD_PARTITION_NODE

##### 구문

```
RESET_SHARD_PARTITION_NODE( user_name      in varchar(128),
                            object_name    in varchar(128),
                            old_node_name  in varchar(10),
                            new_node_name  in varchar(10),
                            partition_name in varchar(128) default NULL )
```

##### 파라미터

| 이름           | 입출력 | 데이터 타입  | 설명               |
| -------------- | ------ | ------------ | ------------------ |
| user_name      | IN     | VARCHAR(128) | 객체 소유자의 이름 |
| object_name    | IN     | VARCHAR(128) | 객체 이름          |
| old_node_name  | IN     | VARCHAR(10)  | 현재 노드 이름     |
| new_node_name  | IN     | VARCHAR(10)  | 변경할 노드 이름   |
| partition_name | IN     | VARCHAR(128) | 객체의 파티션 이름 |

##### 설명

등록된 분산 정보의 샤드 노드를 변경한다.

##### 예제

```
iSQL> EXEC dbms_shard.set_shard_table('sys','t1','H','i1');
Execute success.
iSQL> EXEC dbms_shard.set_shard_partition_node('sys','t1','p1','node1');
Execute success.
iSQL> EXEC dbms_shard.set_shard_partition_node('sys','t1','p2','node3');
Execute success.
iSQL> EXEC dbms_shard.reset_shard_partition_node('sys','t1','node3','node2','p2');
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

| 이름                 | 입출력 | 데이터 타입   | 설명                             |
| -------------------- | ------ | ------------- | -------------------------------- |
| user_name            | IN     | VARCHAR(128)  | 테이블 소유자의 이름             |
| table_name           | IN     | VARCHAR(128)  | 테이블 이름                      |
| additional_node_list | IN     | VARCHAR(1000) | 샤드 노드의 이름 (기본값 : null) |

##### 설명

샤드 테이블의 샤드 키와 데이터의 유효성을 확인한다.

additional_node_list는 테이블의 분산 정의에 등록되지 않은 샤드 노드의 정보를 확인한다. 샤드 노드의 이름은 쉼표(,)로 구분하여 나열한다.

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

node1\~node4로 분산한 t1 테이블을 노드 node1\~node2로 재설정한 후 node3, node4를 포함한 정보까지 확인할 수 있는 예제이다.

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
> 복합 샤드 키를 포함한 샤드 키 분산 테이블에 한해 적용된다.

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
| -------------------- | ------ | ------------- | -------------------------------------- |
| user_name            | IN     | VARCHAR(128)  | 테이블 소유자의 이름                   |
| table_name           | IN     | VARCHAR(128)  | 테이블 이름                            |
| batch_count          | IN     | BIGINT        | 일괄 처리 행의 단위 (기본값 : 전체 행) |
| additional_node_list | IN     | VARCHAR(1000) | 샤드 노드의 이름 (기본값 : null)       |

##### 설명

모든 샤드 노드의 데이터를 변경된 샤드 키 분산 방식으로 재분배한다.

additional_node_list는 테이블의 분산 정의에 등록되지 않은 샤드 노드를 포함하여 데이터를 재분배한다. 샤드 노드의 이름은 쉼표(,)로 구분하여 나열한다.

##### 예제

샤드 키 i1 으로 분산된 t1 테이블의 분산 정보를 재설정 한다고 가정한다.

- hash (333:NODE1, 666:NODE2, 1000:NODE3) -> hash( 500:NODE1, 1000:NODE2)

기존 NODE3 에 분산되어 있는 데이터를 추가적으로 적용해야 하므로 additional_node_list 로 NODE3 를 포함하여 수행한다.

```
iSQL> EXEC dbms_shard.check_data('sys','t1');
shard_key_column:I1
shard_information:{"SplitMethod":"H","DefaultNode":"NODE1","RangeInfo":[{"Value":"1000","Node":"NODE3"},{"Value":"333","Node":"NODE1"},{"Value":"666","Node":"NODE2"}]}

node_name:NODE1, record_count:3314, correct_count:3314, incorrect_count:0
node_name:NODE2, record_count:3312, correct_count:3312, incorrect_count:0
node_name:NODE3, record_count:3373, correct_count:3373, incorrect_count:0

iSQL> AUTOCOMMIT OFF;
iSQL> EXEC dbms_shard.unset_shard_table('sys','t1');
iSQL> EXEC dbms_shard.set_shard_table('sys','t1','h','i1','node1');
iSQL> EXEC dbms_shard.set_shard_hash('sys','t1',500,'node1');
iSQL> EXEC dbms_shard.set_shard_hash('sys','t1',1000,'node2');
iSQL> COMMIT;
iSQL> ALTER SYSTEM RELOAD SHARD META NUMBER LOCAL;

iSQL> ALTER SESSION SET global_transaction_level = 2;
iSQL> EXEC dbms_shard.rebuild_data('sys','t1',1000,'node3');
[12:09:16] target node(1/3): "NODE1"
[12:09:16] target node(2/3): "NODE2"
[12:09:16] 1000 moved
[12:09:16] 1663 moved
[12:09:16] target node(3/3): "NODE3"
[12:09:16] 1000 moved
[12:09:16] 2000 moved
[12:09:16] 3000 moved
[12:09:16] 3373 moved
[12:09:16] done.
Execute success.

iSQL> EXEC dbms_shard.check_data('sys','t1');
shard_key_column:I1
shard_information:{"SplitMethod":"H","DefaultNode":"NODE1","RangeInfo":[{"Value":"1000","Node":"NODE2"},{"Value":"500","Node":"NODE1"}]}

node_name:NODE1, record_count:4977, correct_count:4977, incorrect_count:0
node_name:NODE2, record_count:5022, correct_count:5022, incorrect_count:0

total_record_count   :9999
total_incorrect_count:0
Execute success.
iSQL> COMMIT; 
```

> ##### 주의사항
>
> - 복합 샤드 키를 포함한 샤드 키 테이블에 한해 적용된다.
> - 기존의 샤드 분산 테이블을 해제하고 새로운 분산방식을 적용한 후, 이 프로시저를 수행해야 한다.
> - 데이터의 정합성 보장을 위해서는 사용자 어플리케이션을 정지한 이후 수행해야 한다.

#### REBUILD_DATA_NODE

##### 구문

```
REBUILD_DATA_NODE(user_name   in  varchar(128),
                  table_name  in varchar(128),
                  node_name   in varchar(10),
                  batch_count in bigint default 0)
```

##### 파라미터

| 이름        | 입출력 | 데이터 타입  | 설명                             |
| ----------- | ------ | ------------ | -------------------------------- |
| user_name   | IN     | VARCHAR(128) | 테이블 소유자의 이름             |
| table_name  | IN     | VARCHAR(128) | 테이블 이름                      |
| node_name   | IN     | VARCHAR(10)  | 샤드 노드 이름                   |
| batch_count | IN     | BIGINT       | 일괄 처리 행의 단위 (기본값 : 0) |

##### 설명

변경된 샤드 키 분산방식에 따라 특정 샤드 노드의 데이터를 재분배한다.

##### 예제

```
iSQL> AUTOCOMMIT OFF;
iSQL> EXEC dbms_shard.unset_shard_table('sys', 't1');
iSQL> EXEC dbms_shard.set_shard_table('sys','t1','R','i1','node3');
iSQL> EXEC dbms_shard.set_shard_range('sys','t1',330,'node1');
iSQL> EXEC dbms_shard.set_shard_range('sys','t1',500,'node2');
iSQL> COMMIT;
iSQL> ALTER SYSTEM RELOAD SHARD META NUMBER LOCAL;

iSQL> EXEC dbms_shard.check_data('sys','t1');
shard_key_column:I1
shard_information:{"SplitMethod":"R","DefaultNode":"NODE3","RangeInfo":[{"Value":"330","Node":"NODE1"},{"Value":"500","Node":"NODE2"}]}
node_name:NODE1, record_count:330, correct_count:330, incorrect_count:0
node_name:NODE2, record_count:330, correct_count:170, incorrect_count:160
node_name:NODE3, record_count:340, correct_count:340, incorrect_count:0
total_record_count   :1000
total_incorrect_count:160
Execute success.

iSQL> ALTER SESSION SET global_transaction_level = 2;
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
> REBUILD_DATA 와 동일한 다음의 주의사항을 가지고 있다.
>
> - 복합 샤드 키를 포함한 샤드 키 테이블에 한해 적용된다.
> - 기존의 샤드 분산 테이블을 해제하고 새로운 분산방식을 적용한 후, 이 프로시저를 수행해야 한다.
> - 데이터의 정합성 보장을 위해서는 사용자 어플리케이션을 정지한 이후 수행해야 한다.

#### UNSET_NODE

##### 구문

```
UNSET_NODE(node_name in varchar(10))
```

##### 파라미터

| 이름      | 입출력 | 데이터 타입 | 설명      |
| --------- | ------ | ----------- | --------- |
| node_name | IN     | VARCHAR(10) | 샤드 노드 |

##### 설명

샤드 노드에서 이전에 설정한 샤드 노드 정보를 삭제한다.

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
| ---------- | ------ | ------------ | -------------------- |
| user_name  | IN     | VARCHAR(128) | 테이블 소유자의 이름 |
| table_name | IN     | VARCHAR(128) | 테이블 이름          |

##### 설명

모든 샤드 노드에서 데이터 복제(Replication)를 중지하고 샤드 테이블의 정보를 삭제한다.

UNSET_SHARD_TABLE() 함수를 사용하여 샤드 테이블 정보를 삭제하면, 분산 정보도
모두 삭제된다.

복제 테이블도 같이 삭제 된다.

##### 예제

```
iSQL> EXEC dbms_shard.unset_shard_table('sys','t5');
Execute success.
```

> ##### 주의사항
>
> - Non-Autocommit 에서만 수행 할 수 있다.
> - Global Transaction Level 2 이상에서만 수행 할 수 있다.

#### UNSET_SHARD_TABLE_BY_ID

##### 구문

```
UNSET_SHARD_TABLE_BY_ID(shard_id in integer)
```

##### 파라미터

| 이름     | 입출력 | 데이터 타입 | 설명           |
| -------- | ------ | ----------- | -------------- |
| shard_id | IN     | INTEGER     | 샤드 객체 번호 |

##### 설명

모든 샤드 메타에서 데이터 복제(Replication)를 중지하고 샤드 테이블의 정보를 삭제한다.

UNSET_SHARD_TABLE_BY_ID() 함수를 사용하여 샤드 테이블 정보를 삭제하면, 분산
정보도 모두 삭제된다.

복제 테이블도 같이 삭제 된다.

삭제된 shard_id는 sys_shard.objects_에서 조회할 수 있다.

##### 예제

```
iSQL> EXEC dbms_shard.unset_shard_table_by_id(123);
Execute success. 
```

> ##### 주의사항
>
> - Non-Autocommit 에서만 수행 할 수 있다.
> - Global Transaction Level 2 이상에서만 수행 할 수 있다.

#### UNSET_SHARD_PROCEDURE

##### 구문

```
UNSET_SHARD_PROCEDURE(
  user_name in varchar(128),
  proc_name in varchar(128))
```

##### 파라미터

| 이름      | 입출력 | 데이터 타입  | 설명                   |
| --------- | ------ | ------------ | ---------------------- |
| user_name | IN     | VARCHAR(128) | 프로시저 소유자의 이름 |
| proc_name | IN     | VARCHAR(128) | 프로시저 이름          |

##### 설명

모든 샤드 노드에서 샤드 프로시저의 정보를 삭제한다.

UNSET_SHARD_PROCEDURE() 함수를 사용하여 샤드 프로시저 정보를 삭제하면, 분산
정보도 모두 삭제된다.

##### 예제

```
iSQL> EXEC dbms_shard.unset_shard_procedure('sys','proc1');
Execute success.
```

> ##### 주의사항
>
> - Non-Autocommit 에서만 수행 할 수 있다.
> - Global Transaction Level 2 이상에서만 수행 할 수 있다.

#### UNSET_SHARD_PROCEDURE_BY_ID

##### 구문

```
UNSET_SHARD_PROCEDURE_BY_ID(
	shard_id in integer)
```

##### 파라미터

| 이름     | 입출력 | 데이터 타입 | 설명           |
| -------- | ------ | ----------- | -------------- |
| shard_id | IN     | INTEGER     | 샤드 객체 번호 |

##### 설명

모든 샤드 노드에서 샤드 프로시저의 정보를 삭제한다.

UNSET_SHARD_PROCEDURE_BY_ID() 함수를 사용하여 샤드 테이블 정보를 삭제하면, 각
분산 방식 때 정의했던 분산 정보도 모두 삭제된다.

샤드 메타를 삭제할 shard_id 는 sys_shard.objects_에서 조회할 수 있다.

##### 예제

```
iSQL> EXEC dbms_shard.unset_shard_procedure_by_id(123);
Execute success. 
```

> ##### 주의사항
>
> - Non-Autocommit 에서만 수행 할 수 있다.
> - Global Transaction Level 2 이상에서만 수행 할 수 있다.

## Altibase Sharding 프로퍼티

본 절에서는 Altibase Sharding 프로퍼티를 설명한다.

Altibase Sharding 

프로퍼티는 크게 다음과 같이 분류할 수 있다.

| **분류**                  | **프로퍼티**                                                 | **동적 변경 허용** | **변경 레벨**   |
| ------------------------- | ------------------------------------------------------------ | ------------------ | --------------- |
| 초기화 관련 프로퍼티      | SHARD_ENABLE                                                 | No                 |                 |
| 내부 연결 관련 프로퍼티   | SHARD_INTERNAL_CONN_ATTR_RETRY_COUNT SHARD_INTERNAL_CONN_ATTR_RETRY_DELAY SHARD_INTERNAL_CONN_ATTR_CONNECTION_TIMEOUT SHARD_INTERNAL_CONN_ATTR_LOGIN_TIMEOUT | Yes                | SYSTEM          |
| 쿼리 분석 관련 프로퍼티   | TRCLOG_DETAIL_SHARD                                          | Yes                | SYSTEM, SESSION |
| 쿼리 변환 관련 프로퍼티   | SHARD_AGGREGATION_TRANSFORM_ENABLE<br />SHARD_TRANSFORM_MODE | Yes Yes            | SYSTEM          |
| 메시지 로그 관련 프로퍼티 | SD_MSGLOG_COUNT <br />SD_MSGLOG_FILE<br />SD_MSGLOG_FLAG<br />SD_MSGLOG_SIZE | No No Yes No       | SYSTEM          |

#### SHARD_ENABLE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

Altibase Sharding의 샤드 노드로 설정한다.

0: Disabled

1: Enabled

#### SHARD_INTERNAL_CONN_ATTR_RETRY_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1024]

##### 설명

코디네이터 커넥션의 재접속 횟수를 설정한다.

#### SHARD_INTERNAL_CONN_ATTR_RETRY_DELAY (단위: 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 3600]

##### 설명

코디네이터 커넥션의 재접속 지연 시간을 설정한다.

#### SHARD_INTERNAL_CONN_ATTR_CONNECTION_TIMEOUT (단위: 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

코디네이터 커넥션의 데이터 수신 최대 지연 시간을 설정한다.

#### SHARD_INTERNAL_CONN_ATTR_LOGIN_TIMEOUT (단위: 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

60

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

코디네이터 커넥션 접속이 이루어진 후 인증 절차가 완료될 때까지 허용된 시간을
설정한다.

#### TRCLOG_DETAIL_SHARD

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

Isql에서 explain plan 기능과 함께 사용 시 샤드 분석 정보를 출력한다. 이 trace
log를 사용하기 위해 1을 설정한다.

단, 이 프로퍼티의 값을 1로 설정할 경우에는 내부적으로 cache 된 plan을 사용하지
않고 새로이 plan을 생성한다.

Altibas Sharding 운영 중 ALTER SESSION, ALTER SYSTEM 문을 이용하여 이 프로퍼티의
값을 변경할 수 있다.

#### SHARD_AGGREGATION_TRANSFORM_ENABLE

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

Altibase Sharding 환경에서 AGGREGATION 분산 수행을 최적화하기 위해 다음 집계 함수를 사용한 쿼리를 내부적으로 변환한다.

- SUM
- MIN
- MAX
- COUNT
- AVG

예를 들어 다음 구문은 SHARD_AGGREGATION_TRANSFORM_ENABLE 값에 따라 아래와 같이 변환하여 수행한다.

SELECT count(*) FROM t1;

```
SHARD_AGGREGATION_TRANSFORM_ENABLE = 0
-> SELECT count(*) FROM shard(SELECT * FROM t1)
SHARD_AGGREGATION_TRANSFORM_ENABLE = 1
-> SELECT sum(c) FROM shard(SELECT count(*) c FROM t1);
```

> 주의 사항
>
> - AVG의 경우 SUM(SUM()) / SUM(COUNT()) 로 변환되어서 부동소숫점 타입의 결과가 상이할 수 있다.

Altibase Sharding 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### SHARD_TRANSFORM_MODE

##### 데이터 타입

Unsigned Integer

##### 기본값

7

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 7]

##### 설명

Altibase Sharding 환경에서 쿼리의 Limit, Selection, Projection 최적화 변환 기능을 제어한다.

해당 프로퍼티 값은 BITMAP 형태이며,

- LIMIT 최적화 변환 기능 켜짐은 1 ( 001 )
- SELECTION 최적화 변환 기능 켜짐은 2 ( 010 )
- PROJECTION 최적화 변환 기능 켜짐은 4 ( 100 )

위 값에 조합으로 제어된다.

예를 들어 다음 구문은 SHARD_TRANSFORM_MODE 값에 따라 아래와 같이 변환하여 수행한다.

SELECT * FROM T1 A LIMIT 1;

```
SHARD_TRANSFORM_MODE = 0;
-> SELECT * FROM SHARD( SELECT * FROM T1 A ) A LIMIT 1;
SHARD_TRANSFORM_MODE = 1;
-> SELECT * FROM SHARD( SELECT * FROM T1 A LIMIT FOR SHARD CAST( 1 AS BIGINT ) + CAST( 1 AS BIGINT ) + 1 ) A LIMIT 1;
```

SELECT A.I1 FROM T1 A, T1 B WHERE A.I1 > 0;

```
SHARD_TRANSFORM_MODE = 0;
-> SELECT A.I1 FROM SHARD( SELECT * FROM T1 as A ) A, SHARD( SELECT * FROM T1 as B ) B WHERE A.I1 > 0;
SHARD_TRANSFORM_MODE = 2;
-> SELECT A.I1 FROM SHARD( SELECT * FROM T1 as A WHERE ( ( A.I1 > 0 ) ) ) A, SHARD( SELECT * FROM T1 as B ) B WHERE A.I1 > 0;
SHARD_TRANSFORM_MODE = 4;
-> SELECT A.I1 FROM SHARD( SELECT SYS.A.I1 AS I1 FROM T1 as A ) A, SHARD( SELECT NULL FROM T1 as B ) B WHERE A.I1 > 0;
```

> 주의 사항
>
> - LIMIT 의 경우, Shard Split Method 에 따라 분산된 데이터 형태 차이로 Standalone 과 결과 값이 다를 수 있다.

Altibase Sharding 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### SD_MSGLOG_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

10

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

샤드 관련 메시지 파일의 최대 개수를 지정한다.

#### SD_MSGLOG_FILE

##### 데이터 타입

String

##### 기본값

altibase_sd.log

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

샤드 관련 메시지가 기록되는 파일이다.

#### SD_MSGLOG_FLAG

##### 데이터 타입

Unsigned Integer

##### 기본값

65537

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

샤드 관련 경고 메시지나 트레이스 메시지를 SD_MSGLOG_FILE에 기록 할지 여부를
나타내는 플래그 값이다.

0 : 기본 에러 메시지

1 : 샤드 메타 에러 메시지

65536 : 샤드 메타 변경 트레이스 메시지

샤드 관련 트레이스 로깅 레벨을 확인하는 방법은 *General Reference*의
V\$TRACELOG를 참조한다.

#### SD_MSGLOG_SIZE

##### 데이터 타입

Unsigned Integer

##### 기본값

10 \* 1024 \* 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 232-1]

##### 설명

샤드 관련 메시지 파일의 최대 크기를 지정한다.

## Aktibase Sharding 유틸리티

### shardLoader

shardLoader는 iloader와 기능이 동일하다. 샤드 노드에 직접 접속하여 데이터를 처리하므로 빠른 데이터 적재가 가능하다. shardLoader는 데이터 마이그레이션과 데이터 재분배에 사용할 수 있다.

#### 설치 방법

shardLoader는 Altibase 패키지를 설치할 때 자동으로 설치된다. 실행 파일의 위치는 다음과 같다.

```
$ALTIBASE_HOME/bin
```

#### shardLoader 설정

iLoader와 동일하다. 사용방법은 “*iLoader User's Manual \> 1. iLoader 개요 \> iLoader의 소개 \> iLoader 설정”*을 참조한다.

#### 명령행 옵션

iLoader와 동일하다. 사용방법은 *iLoader User's Manual \> 2. iLoader 사용 방법 \>명령행 옵션”*을 참조한다.

> #### 주의사항
>
> shardLoader는 array 등 몇 가지 옵션을 제공하지 않는다. 해당 기능을 사용하기 위해서는 각 샤드 노드 별로 iLoader를 사용해야 한다.
