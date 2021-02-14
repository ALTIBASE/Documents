

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Altibase Sharding Guide](#altibase-sharding-guide)
  - [서문](#%EC%84%9C%EB%AC%B8)
    - [이 매뉴얼에 대하여](#%EC%9D%B4-%EB%A7%A4%EB%89%B4%EC%96%BC%EC%97%90-%EB%8C%80%ED%95%98%EC%97%AC)
  - [Altibase Sharding 소개](#altibase-sharding-%EC%86%8C%EA%B0%9C)
    - [Altibase Sharding 개요](#altibase-sharding-%EA%B0%9C%EC%9A%94)
    - [Altibase Sharding 용어](#altibase-sharding-%EC%9A%A9%EC%96%B4)
  - [Altibase Sharding 관리](#altibase-sharding-%EA%B4%80%EB%A6%AC)
    - [Altibase 관리](#altibase-%EA%B4%80%EB%A6%AC)
    - [Zookeeper 관리](#zookeeper-%EA%B4%80%EB%A6%AC)
    - [샤딩 클러스터 백업/복구 고려사항](#%EC%83%A4%EB%94%A9-%ED%81%B4%EB%9F%AC%EC%8A%A4%ED%84%B0-%EB%B0%B1%EC%97%85%EB%B3%B5%EA%B5%AC-%EA%B3%A0%EB%A0%A4%EC%82%AC%ED%95%AD)
    - [클라이언트 설정](#%ED%81%B4%EB%9D%BC%EC%9D%B4%EC%96%B8%ED%8A%B8-%EC%84%A4%EC%A0%95)
    - [Altibase Sharding 제약사항](#altibase-sharding-%EC%A0%9C%EC%95%BD%EC%82%AC%ED%95%AD)
  - [Altibase Sharding 사용](#altibase-sharding-%EC%82%AC%EC%9A%A9)
    - [Altibase Sharding 사용 기본 흐름](#altibase-sharding-%EC%82%AC%EC%9A%A9-%EA%B8%B0%EB%B3%B8-%ED%9D%90%EB%A6%84)
    - [샤드 키워드](#%EC%83%A4%EB%93%9C-%ED%82%A4%EC%9B%8C%EB%93%9C)
    - [샤드 함수](#%EC%83%A4%EB%93%9C-%ED%95%A8%EC%88%98)
    - [샤드 실행계획](#%EC%83%A4%EB%93%9C-%EC%8B%A4%ED%96%89%EA%B3%84%ED%9A%8D)
    - [Fail-Over](#fail-over)
  - [Altibase Sharding 프로퍼티](#altibase-sharding-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
  - [Shard DDL](#shard-ddl)
    - [ADD](#add)
    - [DROP](#drop)
    - [JOIN](#join)
    - [FAILOVER](#failover)
    - [FAILBACK](#failback)
    - [MOVE](#move)
  - [Altibase Sharding 딕셔너리](#altibase-sharding-%EB%94%95%EC%85%94%EB%84%88%EB%A6%AC)
    - [샤드 메타 테이블](#%EC%83%A4%EB%93%9C-%EB%A9%94%ED%83%80-%ED%85%8C%EC%9D%B4%EB%B8%94)
    - [성능 뷰 (Performance View)](#%EC%84%B1%EB%8A%A5-%EB%B7%B0-performance-view)
    - [샤드 성능 뷰 (Shard Performance View)](#%EC%83%A4%EB%93%9C-%EC%84%B1%EB%8A%A5-%EB%B7%B0-shard-performance-view)
  - [5.Altibase Sharding 패키지](#5altibase-sharding-%ED%8C%A8%ED%82%A4%EC%A7%80)
    - [DBMS_SHARD](#dbms_shard)
  - [ShardCLI](#shardcli)
  - [ShardJDBC](#shardjdbc)

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

## Altibase Sharding 개념
이 장은 Altibase Sharding의 개요와 용어를 설명한다.

### Altibase Sharding 개요

#### 샤딩 개념 및 모델
샤딩(Sharding)은 하나의 데이터베이스에 저장했던 데이터를 여러개의 데이터베이스들에 분산하여 저장 및 처리하는 스케일 아웃 기술이다.

![](media/Sharding/1cd95d21b81794ed43c6eafff01f8e7c.png)

대부분의 샤딩 시스템들은 서버측 샤딩(server-side sharding)만을 지원하거나, 클라이언트측 샤딩(client-side sharding)만을 지원한다. 

알티베이스는 쿼리에 따라서 서버측 샤딩과 클라이언트측 샤딩으로 자동으로 판단하는 하이브리드 샤딩(hybrid sharding)을 지원한다.

#### 서버측 샤딩(server-side sharding)

![](media/Sharding/39b805a11697d8b7669b42bb61efc037.png)

서버측 샤딩은 응용프로그램들과 호환하기 위하여 분할된 데이터베이스를 통합하는 코디네이터(coordinator)가 필요하다. 코디네이터는 응용프로그램에서 요청 받은 질의처리에 필요한 데이터의 위치를 파악하고, 해당하는 샤드 노드들에 질의를 분산 처리하여 그 결과를 통합하여 반환한다.

서버측 샤딩은 코디네이터가 병목(bottle-neck)이 될 수 있는 단점이 있다. 

#### 클라이언트측 샤딩(client-side sharding)
일반적인 클라이언트측 샤딩의 특징은 다음과 같다.
-   커넥션 시점 샤딩  
    응용프로그램에서 특정 노드를 지정하여 접속하는 방식이다. 다른 노드에 접근하기 위해서는 재접속을 해야 한다.
-   SQL 작성 시점 샤딩  
    응용프로그램에서 쿼리를 작성(혹은 생성)할 때 수행할 노드를 지정하는 방식이다. 다른 노드에 접근하기 위해서는 쿼리를 재작성(혹은 재생성)해야 한다.

![](media/Sharding/c692bfbc33bf556ad6ed199b492dffd1.png)

클라이언트측 샤딩은 클라이언트에서 데이터가 위치한 샤드노드를 미리 알고, 해당 샤드노드에 직접 접속하여 처리하는 구조이다. 이 구조는 샤드노드 추가에 따른 코디네이터 부하 한계로 인한 제약점이 없다는 장점이 있다. 

그러나, 클라이언트 레벨에서 대량 데이터 조인 및 집계처리를 포함한 모든 형태의 분산처리를 직접하려면, 클라이언트들이 모두 컴퓨팅 파워가 서버급이어야 하는데, 그럴 수 없으므로, 클라이언트측 샤딩에서는 단순하게 처리할 수 있는것들만을 처리할 수 있는 단점이 있다.

#### 알티베이스 하이브리드 샤딩(Altibase hybrid sharding)
알티베이스 하이브리드 샤딩은 쿼리별로 처리 성능 및 효율에 맞추어 자동으로 서버측 샤딩 혹은 클라이언트측 샤딩으로 처리한다. 그래서, 각 샤딩방식의 장점을 취하고 단점을 보완할 수 있다.
- 쿼리별로 자동으로 판단함으로써, 기존 응용프로그램 소스나 기존 SQL의 수정을 최소화 할 수 있도록 하였다.
- 클라이언트측 쿼리로 판명되는 경우에, 쿼리를 수행하는 순간마다 쿼리에 bind 된 샤드키값에 의거하여, 자동으로 수행할 샤드 노드가 선택된다. 사용자는 샤드 노드를 구분할 필요가 없다.
- 사용자가 하이브리드 샤딩을 고려하여 쿼리를 튜닝할 수 있도록 추가적인 샤드 키워드를 제공한다.
- 샤드 전용 클라이언트 라이브러리를 사용하여야 하이브리드 샤딩방식이 적용된다. 샤드 전용 클라이언트 라이브러리를 사용하지 않으면 서버측 샤딩방식으로만 동작한다.

![altibase_hybrid_sharding_overview_small](media/Sharding/altibase_hybrid_sharding_overview_small.png)

#### Altibase Sharding 구성 개요

![sharding_overview_terminology](media/Sharding/sharding_overview_terminology.png)

-   응용프로그램 
-   샤드 라이브러리
-   샤드 노드
    -   샤드 코디네이터
    -   샤드 메타 데이터
    -   샤드 데이터
    -   샤드 레플리카
-   ZooKeeper

#### 샤딩 클러스터 시스템
개별 노드들은 사용자의 Shard DDL(ADD, DROP, JOIN, FAILOVER, FAILBACK) 구문 수행이나, 시스템의 자동 FAILOVER 수행에 의하여, 샤딩 클러스터 시스템에 참여하거나 제외될 수 있다. 

![](media/Sharding/sharding_cluster_system_view.png)

#### 샤딩 고가용성(High Availability)
Altibase Sharding 시스템은 모든 샤드 노드가 K-safety 만큼의 샤드 데이터 복제본을 유지하여, 모든 샤드 노드가 Active 노드이면서 동시에 Standby 노드의 역할을 한다.

Altibase Sharding 시스템은 단일 장애점(SPOF: single point of failure)이 없는 시스템 구성으로 높은 신뢰성을 가질 수 있다.

![](media/Sharding/sharding_replication_view.png)

#### 알티베이스 샤딩의 업무 적용 범위
다음과 같은 OLTP (Online Transaction Processing) 업무
-   대부분의 쿼리가 클라이언트측 샤딩으로 분류되는 업무
-   대용량 데이터를 대상으로 하는 업무
-   매우 짧은 시간에 읽거나 조작하는 업무를 하나의 트랜잭션 단위로 수행하는 업무
-   매우 많은 사용자가 동시에 수행하는 업무
-   매우 짧은 시간에 높은 처리량이 요구되는 업무

다음과 같은 OLAP (Online Analytical Processing) 업무
-   서버측 샤딩으로 수행되는 쿼리이지만, 샤드노드별로 분산처리 될 수 있는 것이 많은 업무

#### 최적 경로의 쿼리 수행을 통한 분산 트랜잭션의 우수한 성능
하나의 샤드 트랜잭션내의 다양한 쿼리들은 개별적으로 최적의 경로로 수행될수 있어서, 분산 트랜잭션의 성능이 우수하다.

![](media/Sharding/shard_query_analyzer_optimizer_executer.png)

위 그림은 하이브리드 샤딩으로 사용자의 쿼리가 수행되는 예를 보여준다.
- 설명의 편의상, t1 테이블은 node2 와 node3 에만 분산정의된 것으로 가정한다. 
- 또한, key=1 데이타는 node1 에 위치하고, key=2 데이타는 node2 에 위치하는 것으로 가정한다.
- Q3-1와 Q3-2는 샤드 쿼리 분석기가 Q3에서 생성한 분산 쿼리와 통합 쿼리이다.
```
Q1) insert into t1(key, c1) values (1, 100);
Q2) update t1 set c1=c1+1 where key=2;
Q3) select sum(c) total_count from (select count(*) c from t1);
    Q3-1) select count(*) c from t1;
    Q3-2) select sum(c) total_count from temp;
```

#### 분산 방식
Altibase Sharding은 아래와 같은 분산 방식을 제공한다.
-   해시(hash) 분산 방식
-   범위(range) 분산 방식
-   리스트(list) 분산 방식
-   클론(clone) 분산 방식
-   솔로(solo) 분산 방식

![](media/Sharding/636327fd7d5bf5268d74f89b0760cbe9.png)

##### 해시(Hash) 분산 방식
Altibase Sharding의 해시 분산은 샤드 키에 해당하는 값을 내장된 hash함수를 이용하여 분산하는 것을 말한다. 해시 함수는 데이터를 균등하게 분산하는데 이용된다. 

해시 함수로부터 구한 해시 값에 나머지 연산을 수행한 값을 이용하여, 전체 데이터를 1000개의 그룹으로 나누어 관리한다. 
-   hash_group[1] = { record(x) \| if (mod(hash(shard key value of x),1000)==0) };
-   hash_group[2] = { record(x) \| if (mod(hash(shard key value of x),1000)==1) };
-   …
-   hash_group[1000] = { record(x) \| if (mod(hash(shard key value of x),1000)==999) };

이렇게 구분된 1000개의 hash group을 사용자의 필요에 따라 분산 정의한 예시이다.
-   1\~300번 hash group    –\> 샤드 노드1
-   301\~600번 hash group  –\> 샤드 노드2
-   601\~1000번 hash group –\> 샤드 노드3

데이터를 분산하기 전 다음과 같은 해시 분산 방식으로 데이터를 분산했을 때, 데이터의 분포 상태를 예측할 수 있다.
```
iSQL> SELECT hash, count(*) FROM (SELECT mod(hash(user_id),1000)+1 hash FROM table) GROUP BY hash;
```

##### 범위(Range) 분산 방식
- 해시 분산 방식을 사용하면 데이터가 비교적 균등하게 분산되는 반면, 특정 데이터가 어느 노드에 위치하는지 직관적으로 알기는 어려워진다.
- 범위 분산 방식은 샤드 키 값으로 해당 데이터가 어느 노드에 위치하는지 관리자가 쉽게 알 수 있어 유리하다.
- 범위 분산 방식으로 데이터를 고르게 분산했더라도, 운영 중에 데이터가 변경됨으로써 불균형이 발생할 수 있기 때문에 지속적으로 데이터 분포의 모니터링이 필요하다.

아래는 alphanumeric 의 샤드 키 값에 대한 임의의 범위 분산 설정 예시이다.
-   { record(x) \| (shard key value of x) \<= ‘9’ }        -\> 샤드 노드 1
-   { record(x) \| ‘9’ \< (shard key value of x) \<= ‘M’ } -\> 샤드 노드 2
-   { record(x) \| ‘M’ \< (shard key value of x) \<= ‘Z’ } -\> 샤드 노드 3

범위 분산 방식 역시 데이터를 분산하기 전에 쿼리로 데이터의 분포를 예측할 수 있다.
```
iSQL> SELECT user_id, count(*) FROM table GROUP BY user_id;
```

##### 리스트(List) 분산 방식
리스트 분산은 샤드 키 값을 특정값과 일치하는지 확인하여 분산하는 방식이다. 

아래는 도시명을 이용한 임의의 리스트 분산 설정한 예시이다.
-   { record(x) \| (shard key value of x) = ‘서울’ } -\> 샤드 노드1
-   { record(x) \| (shard key value of x) = ‘부산’ } -\> 샤드 노드 2
-   { record(x) \| (shard key value of x) = ‘대구’ } -\> 샤드 노드 3

##### 복제(Clone) 분산 방식
복제 분산 방식은 샤드 키를 지정할 필요가 없고, 모든 샤드 노드들에 해당 샤드 객체의 데이터가 중복 저장된다.

##### 독립(Solo) 분산 방식
독립 분산은 복제 분산 방식은 샤드 키를 지정할 필요가 없고, 사용자가 지정한 하나의 노드에만 객체를 저장한다.
-   TABLE_1 –\> 샤드 노드 1
-   TABLE_2 –\> 샤드 노드 2
-   TABLE_3 –\> 샤드 노드 1

### Altibase Sharding 용어

#### 샤드 노드(shard node) 
샤딩 시스템을 구성하는 각각의 데이터베이스 인스턴스이다. 최대 128개의 샤드 노드를 지원한다.

#### sharded database
여러개의 샤드 노드들로 구성된 사용자 입장에서 논리적으로 하나인 데이터베이스를 sharded database 라고 한다. 

#### 샤드 클러스터 관리자
Split brain 방지등의 샤딩 클러스터 관리를 위하여 Apache Zookeeper를 사용한다.

#### 샤드 클러스터 관리자 메타 정보
샤드 클러스터 관리를 위하여 Zookeeper에서 관리하는 메타정보를 의미한다.

#### ZooKeeper client
샤드 노드별로 구동되는 Altibase server가 Zookeeper client로 동작한다.

#### 샤딩 클러스터 시스템(Sharding Cluster System)
여러개의 샤드 노드들로 구성된 sharded database 와 샤드 클러스터 관리자(ZooKeeper)를 합하여 샤딩 클러스터 시스템이라고 한다. 

#### 샤드 메타 데이터 (shard meta data) 
샤드 노드의 정보, 샤드 객체, 분산 설정 등 분산 정보가 저장되는 샤드 메타 테이블들의 데이터를 총칭하여 샤드 메타 데이터라고 한다. 샤드 메타 테이블들은 sys_shard 사용자의 객체로 관리된다.

#### 샤드 코디네이터(shard coordinator) 
분산된 데이터베이스를 통합하여 질의를 최적화하고 수행하는 분산 질의 처리기이다.

#### 샤드 라이브러리(shard library) 
하이브리드 샤딩을 지원하는 클라이언트 프로그램 라이브러리이다.

#### 샤드 데이터(shard data) 
분산된 데이터 조각이다. 전체 분산 데이터베이스의 데이터 일부를 가지고 있다.

#### 샤드 레플리카(shard replica) 
샤드 데이터에 대한 복제본이다. k-safety 값 만큼의 복제본을 가지고 있다.

#### 샤드 커넥션(shard connection)
각종 커넥션들을 통칭하여 샤드 커넥션이라고 한다.

#### 외부 커넥션(external connection)
외부 커넥션은 사용자 커넥션과 샤드 라이브러리 커넥션의 두 가지가 있다.

#### 사용자 커넥션(user connection)
사용자의 클라이언트 응용프로그램에서 명시적으로 접속한 연결이다.

#### 샤드 라이브러리 커넥션(shard library connection )
샤드 라이브러리를 사용한 클라이언트가 데이터 처리를 위해 모든 샤드 노드들에 자동으로 접속한 연결이다.

#### 내부 커넥션 (internal connection)
샤드 노드들 간에 내부적으로 사용하는 것으로 코디네이터 커넥션이 있다.

#### 코디네이터 커넥션 (coordinator connection)
샤드 노드들 간에 내부적으로 사용하는 연결이다.

#### 샤드 세션(shard session)
사용자 커넥션으로 연결된 세션과 관련된 모든 세션을 샤드 세션이라 한다.

#### 코디네이팅 샤드 노드(coordinating shard node)
샤드 노드들 중 사용자가 접속한(사용자 커넥션) 샤드노드를 말한다.

#### 로컬 객체(local object) 혹은 일반 객체
분산 정의를 하지 않은 객체를 지칭한다. 로컬 객체에 대한 작업은 샤딩 클러스터 전체와는 관련없이, user session으로 접속한 노드에서만 처리된다. 

#### 샤드 객체(shard object) 혹은 분산 객체
분산 저장 및 처리되는 객체를 지칭한다. 현재 지원하는 분산객체는 다음과 같다.
-   Table
-   Procedure
-   Sharded sequence

#### 샤드 테이블(shard table)
샤드 테이블은 일반 테이블에 샤드 분산 설정을 한 테이블을 말한다.
- 샤드 테이블을 설정하기 위해서 먼저 모든 샤드 노드에 동일한 스키마의 테이블이 생성되어 있어야 한다.
- 샤드 테이블은 샤드키 테이블과 솔로 테이블 그리고 클론 테이블이 있다.
- 샤드키 테이블은 분산 방식에 대응되는 파티션드 테이블로 생성되어 있어야 한다. 파티션 키가 샤드 키로 사용된다. 
  - 해시 분산 샤드키 테이블: RANGE_USING_HASH 파티셔닝
  - 범위 분산 샤드키 테이블: RANGE 파티셔닝
  - 리스트 분산 샤드키 테이블: LIST 파티셔닝
- 샤드키 테이블을 샤드객체로 등록시에 파티션별로 노드를 지정하도록 되어있다.
- 클론 테이블은 global_transaction_level 을 3 으로 설정한 경우에만 수정할 수 있다.
- 노드 추가시 리샤딩은 파티션 단위로만 할 수 있다. 그러므로, 향후 노드 확장을 고려하여, 파티션의 범위 및 갯수를 정하는 것이 좋다.
- 샤드 테이블 분산객체로 등록은 아래 구문을 사용한다. 자세한 설명은 DBMS_SHARD 패키지를 참조한다.
  - DBMS_SHARD.SET_SHARD_TABLE_SHARDKEY(...)
  - DBMS_SHARD.SET_SHARD_TABLE_SOLO(...)
  - DBMS_SHARD.SET_SHARD_TABLE_CLONE(...)

#### 샤드 프로시저
샤드 프로시저는 일반 프로시저에 샤드 분산 설정을 한 프로시저를 말한다.
- 샤드 프로시저를 설정하기 위해서 먼저 모든 샤드 노드에 동일한 내용의 프로시저가 생성되어 있어야 한다.
- 샤드 프로시저는 샤드키 프로시저와 솔로 프로시저 그리고 클론 프로시저가 있다.
- 샤드키 프로시저는 프로시저의 파라미터들 중 하나가 샤드 키로 사용되며, 프로시저가 호출될 때의 파라미터 값으로 샤드 노드를 선택하여 선택된 노드에서 프로시저가 수행된다.
- 샤드키 프로시저는 해시와 범위 그리고 리스트 분산방식을 지원한다.
- 샤드 프로시저 분산객체로 등록은 아래 구문을 사용한다. 자세한 설명은 DBMS_SHARD 패키지를 참조한다.
  - DBMS_SHARD.SET_SHARD_PROCEDURE_SHARDKEY(...)
  - DBMS_SHARD.SET_SHARD_PROCEDURE_SOLO(...)
  - DBMS_SHARD.SET_SHARD_PROCEDURE_CLONE(...)

#### 샤드키(shard key)
- 샤드키 테이블에 대한 샤드키는 데이터를 분산하는 기준이 되는 테이블의 컬럼이다.
- 샤드키 프로시저에 대한 샤드키는 호출되는 프로시저의 노드를 결정하는 프로시저의 파라미터를 말한다.
- 샤드키는 하나의 컬럼 혹은 파라미터에 대해서만 정의할 수 있다.
- 현재 샤드키로 사용할 수 있는 데이터 타입은 다음과 같다.
  -   smallint
  -   integer
  -   bigint
  -   char
  -   varchar

#### 샤드 키워드(shard keyword)
샤드 키워드를 이용하여, 임의의 쿼리를 수행할 샤드 노드의 범위를 정해서 쿼리를 수행하게 할 수 있다. 샤드 키워드의 종류는 다음과 같다.
-   SHARD
-   NODE[META]
-   NODE[DATA]

#### 샤드 쿼리(shard query)
샤드 쿼리는 동일한 쿼리를 샤드노드별로 별개로 수행하여 취합한 결과가 하나의 데이터베이스에서 처리한 결과와 동일 할 경우를 지칭한다. 논샤드 쿼리는 샤드 쿼리가 아닌 쿼리를 지칭한다.
- 샤드쿼리는 최대한 클라이언트측 샤딩으로 수행되며, 성능 및 스케일 아웃에 유리하다.
- 단, 샤드키워드를 사용한 쿼리는 논리적으로 샤드 쿼리에 해당하는 경우일지라도, 서버사이드로 수행된다.
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

#### 샤드 쿼리 분석기(shard query analyzer)
샤드 쿼리 분석기는 사용자의 쿼리를 서버측 샤딩으로 수행하는 쿼리와 클라이언트측 샤딩으로 수행하는 쿼리로 구분하는 역할을 한다.

#### 샤드 쿼리 최적화기(shard query optimizer)
샤드 코디네이터의 샤드 쿼리 최적화기는 서버측 샤딩에 대한 최적의 분산 쿼리를 생성하고, 분산 쿼리에 대한 분산 플랜을 생성한다.

사용자 쿼리가 서버측 샤딩으로 수행되는 쿼리로 분류된 경우, 해당 쿼리를 서버측에서 수행하기 위해서 분산부와 통합부로 구분한다. 분산부는 각 샤드 노드에서 수행할 부분이고, 통합부는 각 노드에서 수행한 결과를 모아서 수행할 부분이다.

#### 샤드 플랜(shard plan)
질의가 샤드 코디네이터에서 분산 수행되는 경우의 질의 수행계획을 말한다.

#### 샤드 쿼리 실행기 (Shard Query Executor)
샤드 쿼리 실행기는 클라이언트측 샤딩의 실행기와 서버측 샤딩의 실행기로 구분한다. 클라이언트측 샤딩의 실행기는 샤드 라이브러리에서 동작하며, 서버측 샤딩의 실행기는 샤드 노드에서 샤드 코디네이터를 통해서 동작한다.

#### 샤드 트랜잭션(shard transaction)
애플리케이션이 생성한 트랜잭션에서 수행하는 질의의 따라 샤드 노드들에 분산 트랜잭션을 생성하게 된다. 이 트랜잭션들을 샤드 트랜잭션이라고 한다.

클라이언트측 샤딩으로 생성된 트랜잭션과 서버측 샤딩으로 생성된 트랜잭션을 하나의 트랜잭션으로 통합하여 수행한다.

샤드 트랜잭션은 다음과 같이 분류할 수 있다.
-   다중 노드 트랜잭션(multiple node transaction)
    - 분산 트랜잭션을 개별 샤드 노드별로 처리한다. 노드장애등의 상황에서 커밋이 안되는 노드가 발생할 수 있다.
-   글로벌 트랜잭션(global transaction)
    - 분산 트랜잭션을 two-phase commit를 사용하여 처리하여, 분산 트랜잭션에 참여한 모든 샤드노드에 동일하게 커밋 혹은 롤백이 되는것을 보장한다.
-   글로벌 일관 트랜잭션(global consistent transaction)
    - 글로벌 트랜잭션에서 보장하는것에 추가하여, 글로벌 읽기 일관성을 보장한다.

#### 샤드 메타 번호(SMN: Shard Meta Number)
샤드 메타 번호(SMN)란 샤드 메타데이터에 대한 변경 버전 이력 관리 번호 이다.
- 분산 정의 변경은 노드 추가/제거, 샤드 객체 등록/해제 등의 변경을 말한다.
- SMN은 다음의 세 가지 유형의 SMN이 존재한다. 
  - Meta SMN: 샤드 메타 데이터를 변경하는 트랜잭션 내부에서만 존재하고, 해당 트랜잭션이 COMMIT 이 되는 순간 Data SMN 에 적용이 된다.
  - Data SMN: 데이터의 형상이 어떤 버전의 샤드 메타 기준으로 되어있는지에 대한 SMN
  - Session SMN: 개별 세션이 인식하고 있는 SMN
    - 각 세션은 최초 접속 시에 Data SMN을 자신의 Session SMN으로 할당받아 수행한다.
    - Data SMN이 변경되어 기존의 Session SMN과 다르게 되면, 자동으로 최신 Data SMN으로 Session SMN을 갱신한다.

#### 레플리카 셋(Replica Set)
레플리카 셋(Replica Set)이란 Altibase Sharding 시스템에서 무중단 서비스를 제공하기 위해 생성한 복제(Replication)들의 관계를 저장한 객체이다.

#### K-safety
K-safety는 장애 감내(fault tolerance) 허용값를 의미하며, 이 값은 0, 1 또는 2의 값을 가질 수 있으며, 샤드데이터가 복제된 갯수를 나타낸다. 이러한 복제들은 장애가 발생한 샤드노드에 대한 fail-over를 수행할 수 있도록 한다.

#### 리샤딩 (Resharding)
Altibase Sharding의 리샤딩이란 서비스 운영 중에 데이터 일부를 하나의 샤드 노드에서 다른 샤드 노드로 이동하는 것을 말한다.
- 리샤딩은 주로 노드 증설 혹은 특정 노드의 부하 집중에 따른 데이터 이동을 위하여 사용되며, 서비스 운영 중에 사용할 수 있는 장점을 가진다.
- 리샤딩은 "ALTER DATABASE SHARD MOVE" 구문으로 제공된다.

## Altibase Sharding 관리
이 장에서는 Altibase Sharding을 구성하고 사용환경을 설정하는 방법을 설명한다.

### Altibase 관리

#### Altibase Sharding 운영체제
Altibase Sharding은 아래의 운영체제를 지원한다.
| OS    | CPU                          | Version         | Bit (Server) | Bit (Client) |
| ----- | ---------------------------- | --------------- | ------------ | ------------ |
| LINUX | x86-64 (GNU glibc 2.12 이상) | redhat 6.0 이상 | 64-bit       | 64-bit       |
| LINUX | PowerPC7 (BE)                | redhat 6.5 이상 | 64-bit       | 64-bit       |
| LINUX | PowerPC8 (LE)                | redhat 7.2 이상 | 64-bit       | 64-bit       |

#### Altibase 디렉토리

Altibase Sharding 의 환경 설정에 관한 디렉토리는 Altibase 서버와 동일하다.

본 장에서는 Altibase Sharding 의 추가적인 내용만을 설명한다.

##### xlogfile 디렉토리 (???TBD???)

##### Zookeeper 디렉토리
?????

##### conf 디렉토리
altibase.properties.shard : 샤드 환경에서의 권장 설정값들이 기록되는 파일들이다.

##### trc 디렉토리
altibase_sd.log : 샤드 관련 경고 메시지나 트레이스 메시지 등이 기록되는 파일들이다.

#### Altibase 설치
Altibase 패키지 인스톨러를 이용하여 Altibase 소프트웨어의 설치를 완료한 후에 아래와 같은 샤딩 환경 설정을 하면 된다.

#### 샤드 환경 설정
기존의 설치된 Altibase를 샤드 노드로 설정하기 위해서는 다음 과정이 선행되어야 한다.
-   sharded database 생성
-   샤딩관련 프로퍼티 설정 : SHARD_ENABLE 및 기타 샤딩관련 프라퍼티를 설정한다.
-   샤드 패키지 생성 : DBMS_SHARD 패키지를 생성한다.

##### sharded database 생성 
논리적으로 하나인 sharded database를 생성하기 위해서는, 각 샤드 노드별로 sharded database의 일부 조각인 샤드 데이터베이스를 생성해야한다. 
- 샤드 데이터 베이스 생성 시에는 기존 데이터 베이스 생성과 동일하며 모든 샤드 노드의 데이터 베이스 생성은 동일하게 이뤄져야한다. 
- 샤드 데이터베이스를 생성 시에 입력된 데이터 베이스 이름은 논리적으로 하나인 sharded database 이름으로써, 모든 샤드 노드별 데이터베이스가 동일한 이름을 갖아야 한다. 
- create database *my_sharded_db_name* INITSIZE=10M noarchivelog character set *UTF8* national character set *UTF8*;
  이탤릭체로 표시된 부분과 *TRANSACTION_TABLE_SIZE* 는 모든 샤드 노드에서 동일해야한다.

##### 샤딩관련 프로퍼티 설정
SHARD_ENABLE 프로퍼티를 활성화한 후 서버를 재시작하면, 샤드 노드의 메타 저장소 및 코드네이터 기능이 활성화 된다.
```
iSQL> SELECT name, value1 FROM v$property WHERE name = 'SHARD_ENABLE';
NAME   : SHARD_ENABLE
VALUE1 : 1
```

샤드 노드 기능이 활성화되면, 샤드 패키지를 생성하거나 샤드관련 내장 함수, 성능 뷰를 사용할 수 있다.

SHARD_ENABLE 프로퍼티 이외에도, 여러가지 샤딩관련 프라퍼티들이 있다. 

샤딩관련 프라퍼티들의 권장설정값들은 \$ALTIBASE_HOME/conf/altibase.properties.shard 에 저장있다. 샤딩을 최초 구성시에는, 이 화일을 복사하여 \$ALTIBASE_HOME/conf/altibase.properties 를 만들고, 추가적인 변경사항을 고려해주면 된다.

##### 샤드 패키지 생성
샤드 패키지는 \$ALTIBASE_HOME/packages에 있다. 샤드 패키지는 샤드 기능을 제어할 수 있는 사용자 인터페이스를 제공한다.
```
is –f $ALTIBASE_HOME/packages/dbms_shard.sql
is –f $ALTIBASE_HOME/packages/dbms_shard.plb
```
DBMS_SHARD 패키지의 함수 및 프로시저에 대한 자세한 설명은 이 문서의 *DBMS_SHARD패키지* 설명을 참조한다.

### Zookeeper 관리

#### Zookeeper 설정
- Altibase Sharding은 Zookeeper 3.5.6 버전을 사용해야 한다.
- Zookeeper 관리를 위한 자세한 내용은 https://zookeeper.apache.org/doc/r3.5.5/zookeeperAdmin.html 를 참고한다.
- Zookeeper server의 3.5.6 버전의 binary는 \$ALTIBASE_HOME/ZookeeperServer에 존재하며 따로 설치 할 필요는 없다.
- Zookeeper server를 사용하기 위해서는 JDK 1.8 이상 버전을 사용해야 한다.
- \$ALTIBASE_HOME/ZookeeperServer/conf에 zoo.cfg를 생성한다.(zoo_sample.cfg를 복사해 필요한 부분만 바꿔 사용해도 된다.)
  - tickTime : The number of milliseconds of each tick
  - initLimit : The number of ticks that the initial synchronization phase can take
  - syncLimit : The number of ticks that can pass between sending a request and getting an acknowledgement
  - clientPort : Zookeeper 연결을 위한 port. 다수의 Zookeeper 서버가 기본적으로는 동일한 port를 사용해야 한다.
  - server.X : Zookeeper 서버의 IP와 내부 연결 port. 모든 장비에서 동일한 순서를 사용해야 한다. server의 숫자는 최소 3개, 최대 7개로 그 외의 경우 에러가 발생한다.
    - 예제 
      - server.1=192.168.1.10:2888:3888
      - server.2=192.168.1.11:2888:3888
      - server.3=192.168.1.12:2888:3888
  - dataDir : Zookeeper 데이터가 저장될 path. Zookeeper server를 사용하지 않고 client만 사용할 것이라면 없어도 상관 없다.(절대 경로를 사용해야 한다.)
    - zoo_sample.cfg 에서는 예제의 목적으로만 dataDir=/tmp/zookeeper 로 설정해 놓았다. 실제 운영하기 위해서는 안전한 곳으로 재지정이 필요하다.
- Zookeeper 서버를 사용하지 않고 client로만 사용하는 경우에도 zoo.cfg 파일에서 정보를 가져온다.

#### Zookeeper server 사용
- zoo.cfg에 저장된 dataDir에 접근해 server ID명을 데이터로 가지는 myid라는 이름의 파일을 생성한다.
  - 예제
    - 192.168.1.10 장비의 dataDir에 "1"이라는 데이터를 가지는 myid라는 파일을 생성한다.
    - 192.168.1.11 장비의 dataDir에 "2"이라는 데이터를 가지는 myid라는 파일을 생성한다.
    - 192.168.1.12 장비의 dataDir에 "3"이라는 데이터를 가지는 myid라는 파일을 생성한다.
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
- Zookeeper native client C library는 리눅스만 지원하고, Altibase server는 Zookeeper native client C library를 이용하여, Zookeeper에 클라이언트로서 접속하도록 되어 있다. 즉, 샤딩을 지원하는 알티베이스는 리눅스만 지원한다.
- Zookeeper server는 절반 이상이 살아있을때만 정상작동 하며 그 이하의 서버만 살아있을 경우 절반 이상이 될때까지 client의 요청을 무시한다.
- Zookeeper의 path에는 한개의 값만 존재할 수 있다. 단, 하위 path는 다수가 존재 할 수 있다.(동일 이름은 불가능하다)
- 각 Zookeeper client는 zoo.cfg에 있는 Zookeeper server 들 중 무작위로 하나를 선택해 연결한다.
- Zookeeper 의 snapshot files 혹은 transactional log files 에 corruption 이 발생한 경우의 troubleshooting 은  https://zookeeper.apache.org/doc/r3.5.5/zookeeperAdmin.html#sc_troubleshooting 을 참고한다.

#### Zookeeper 샤딩 클러스터 메타 데이터
Zookeeper에 샤딩 클러스터 메타 데이터를 아래와 같이 관리한다.
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

### 샤딩 클러스터 백업/복구 고려사항
#### 기본 고려사항
- 공통 고려사항
  - 백업과 복구는 각각의 개별 노드들에 대하여 독립적으로 수행하는것을 전제로 한다.
  - 개별 노드의 백업과 복구는 Administrator's Manual 을 참고한다. 
  - 여기서는 샤딩클러스터 환경에서의 추가적인 고려사항들만을 기술한다. 
  - 백업과 복구시에 Zookeeper도 같이 고려가 되어야 한다. 이에 대해서는 https://zookeeper.apache.org/doc/r3.5.5/zookeeperAdmin.html 를 참고한다.
  - 장비문제로 장비를 교체하여 복구를 하는 경우에는, 해당 장비의 IP정보는 예전 장비의 설정대로 맞추어 주어야 한다. 
- 논리적 백업/복구 고려사항
  - 샤딩클러스터에 참여된 상태에서는 기본적으로 쿼리 수행은 특정 노드를 대상으로 하지 않고, 전체 클러스터를 대상으로 한다.
  - 샤딩클러스터에 참여된 상태에서도 NODE[META] 샤드 키워드를 사용하면, 쿼리 수행은 사용자 세션이 접속한 샤드 노드로 대상이 국한된다.
  - iLoader에서도 NODE[META] 샤드 키워드를 사용할 수 있으며, 이에 대한 내용은 iLoader 매뉴얼을 참고한다.
- 오프라인 백업/복구 고려사항
  - 오프라인백업 및 복구시에 xlogfile들도 백업 및 복구해야 한다.
  - 샤딩클러스터 전체 노드들에 대하여, 한꺼번에 오프라인백업을 한 경우에는, 샤딩클러스터 전체 노드에 대하여 한꺼번에 복구하는 용도로 사용할수 있다. 
  - 오프라인백업을 이용하여, 특정 노드만을 복구하는 경우에는, 기본적으로는 해당 노드는 샤딩클러스터에 참여(failback 혹은 join) 시켜서 사용할수 없다.
- 온라인 백업/복구 고려사항
  - 완전복구된 노드에 대해서만, 샤딩클러스터에 참여(failback 혹은 join) 시켜서 사용하는 것을 기본으로 한다.
#### 상황별 고려사항
- k-safety가 1 이상에서, 특정 노드를 shutdown 했는데, 해당 노드에 장애 발생후, 해당 노드가 불완전복구된 상황
  - 이 경우에 해당 불완전복구된 노드를 join시키면 데이터 손실이 발생한다.
  - failover SHARD DDL을 이용하여, 해당 노드를 강제로 failover시키서, 해당 노드의 데이터를 다른 노드에서 정상운영되도록 한다.
  - 정상 failover 이후에, reorganize SHARD DDL을 이용하여, 해당 노드를 샤딩클러스터에서 제거한다.
  - 샤딩클러스터에서 제거된 노드는, 데이터도 모두 제거한 이후에, 새로운 노드로 샤딩클러스터에 추가하여 사용할 수 있다.
- k-safety가 1 이상에서, 노드 장애로 failover되어 데이터 손실없이 정상운영되고 있는데, 장애 노드가 불완전복구된 상황
  - 이 경우에 해당 불완전복구된 노드를 failback 시키면 데이터 손실이 발생한다.
  - reorganize SHARD DDL을 이용하여, 해당 노드를 샤딩클러스터에서 제거한다.
  - 샤딩클러스터에서 제거된 노드는, 데이터도 모두 제거한 이후에, 새로운 노드로 샤딩클러스터에 추가하여 사용할 수 있다.
- k-safety가 1 이상에서, 여러 노드들이 죽어서, 정상 failover되지 못한 노드가 있는데, failback 되어야할 노드가 불완전복구된 상황
  - 이 경우에 해당 불완전복구된 노드를 failback 시키면, 해당 노드에서 서비스하던 데이터들만 손실이 발생하는 것이 아니다. 
    이후에, 해당 노드에 k-safety 복제본을 가지고 있던 노드에 장애가 발생하면, failover시 데이터 손실이 발생할 수 있다.
  - reorganize SHARD DDL을 이용하여, 문제 노드들을 샤딩클러스터에서 제거한다.
  - 장애노드들의 데이터는 불완전복구본, 오프라인 백업본 혹은 논리적 백업본을 이용하여, 최대한의 데이터를 확보한다.
  - 각 장애노드에서 최대한 확보한 데이터는, 샤딩클러스터에 논리적 복구를 이용하여 데이터를 다시 적재하여 사용할 수 있다. 
- k-safety가 0 에서, 장애노드가 불완전복구된 상황
  - 불완전복구된 것이 가장 최신의 데이터를 갖고 있는 상황이라면, 불완전복구된 상태로 샤딩클러스터에 참여(failback 혹은 join) 시켜서 사용한다.
  - 오프라인 백업본이 가장 최신의 데이터를 갖고 있는 상황이라면, 오프라인 복구시킨 상태로 샤딩클러스터에 참여(failback 혹은 join) 시켜서 사용한다.
  - failback 혹은 join 이후에, 추가로 보완할 데이터가 확보되면, 해당 데이터는 샤딩클러스터에 논리적 복구를 이용하여 데이터를 다시 적재하여 사용할 수 있다.
  - 특정 노드에 영구장애가 발생하여, 어떠한 형태로도 샤딩클러스터에 참여(failback 혹은 join) 시켜서 사용할수 없는 경우에는 
    - reorganize SHARD DDL을 이용하여, 해당 노드를 샤딩클러스터에서 제거한다.
    - 해당 노드의 데이터는 불완전복구본, 오프라인 백업본 혹은 논리적 백업본을 이용하여, 최대한의 데이터를 확보한다.
    - 최대한 확보한 데이터는, 샤딩클러스터에 논리적 복구를 이용하여 데이터를 다시 적재하여 사용할 수 있다. 

### 클라이언트 설정

#### 샤딩 응용프로그램 서버 연결 설정
접속할 샤드노드의 우선순위가 있는 경우는, 해당 우선순위에 맞춰서, 기본 ip/port 및 AlternateServers를 설정한다.

접속할 샤드노드의 우선순위가 없는 경우는, LoadBalance=on을 설정한다. 그러면, 기본 ip/port 및 AlternateServers 에 설정된 샤드노드들에 대하여, 랜덤하게 접속한다.

#### 샤딩 응용프로그램 라이브러리 설정

##### ShardCLI

ShardCLI는 CLI 응용프로그램을 하이브리드 샤딩으로 동작할 수 있도록 하는 기능이다.

CLI 응용프로그램 빌드 시 기존의 ODBCCLI 라이브러리를 ShardCLI 라이브러리로 바꾸어야 한다.

ShardCLI 라이브러리는 libshardcli.a와 libshardcli_sl.so 두 개의 파일을 지원한다.

##### ShardJDBC

ShardJDBC는 JDBC 응용프로그램을 하이브리드 샤딩으로 동작할 수 있도록 하는 기능이다.

JDBC는 별도의 샤딩 라이브러리가 존재하는것은 아니고, JDBC 접속 URL에 sharding prefix를 붙여주면 ShardJDBC 로 동작한다.

##### 그외 API

ShardCLI와 ShardJDBC를 제외한 API를 사용하는 경우는 서버측 샤딩으로만 동작한다. 

#### Altibase Sharding 통신 방법
샤딩에서 사용하는 커넥션에 따라 지원하는 통신 방법은 다음과 같다.

##### 사용자 커넥션(User Connection)
사용자 커넥션 스트링의 CONN_TYPE 속성에 해당하며 Altibase 에서 제공하는 통신방법과 동일하다.
자세한 내용은 *Administrator manual*의 서버/클라이언트 통신 장을 참고한다.

##### 샤드 라이브러리 커넥션(Shard Library Connection)
샤드 라이브러리 커넥션의 통신 방법으로 사용자 커넥션 스트링의 SHARD_CONNTYPE 속성에 해당하며 다음의 통신 타입을 지원한다.
SHARD_CONNTYPE 을 명시하지 않을 경우 TCP 를 기본값으로 동작한다.
- 1: TCP (기본값)
- 8: IB (InfiniBand)

##### 코디네이터 커넥션(Coordinator Connection)
코디네이터와 샤드노드의 내부 커넥션 통신 방법으로 노드 설정시 지정 가능하며 다음의 통신 타입을 지원한다.
노드 설정의 인자로 명시하지 않을 경우 TCP 를 기본값으로 동작한다.
- 1: TCP (기본값)
- 8: IB (InfiniBand)

### Altibase Sharding 제약사항

#### 기본 조건
-   샤드 노드들은 샤드 메타 및 샤드 관련 객체들의 스키마 정보가 동일해야 한다.
-   샤드 노드별 데이터베이스들의 계정이름 및 암호는 모두 동일하게 설정되어 있어야 한다. 

#### 프라퍼티 제약조건
-   ISOLATION_LEVEL은 0(read committed)만 지원한다.
-   AUTO_COMMIT은 0(non-autocommit)만 지원한다.

#### 데이터 제약조건
-   샤드 테이블은 기본 키가 있어야 한다.
-   기본 키 중 하나를 파키션 키로 사용하는 파티션 테이블만 샤드키 테이블로 설정될 수 있으며, 파티션 키가 샤드키로 설정된다.
-   샤드 키 컬럼은 update할 수 없다.
-   샤드 키 테이블에서 기본 키 이외의 유니크 속성을 갖는 컬럼은 개별 샤드 노드별로만 유니크가 보장된다. 샤딩 시스템 전역으로 유니크 검사를 하지는 않는다.
-   global non-partitioned index를 지원하지 않는다.
-   global secondary index를 지원하지 않는다.
-   geometry 컬럼, 암호화 컬럼과 압축 컬럼을 지원하지 않는다.  
-   샤드 테이블에 대한 변경 가능 뷰(Updatable View)는 갱신할 수 없다.
-   materialized view를 지원하지 않는다.

#### DDL 제약사항
- 샤딩관련 객체에 대한 DDL을 수행할 수 없습니다.
- 이때 샤딩관련 객체에는, 
  - 샤드테이블 
  - 샤드테이블에 대해서 자동 생성되는 \_BAK\_ 테이블
  - 샤드테이블 및 \_BAK\_ 테이블과 관련된 인덱스
  - 샤드프로시져
  - 샤드테이블의 복제를 위하여 자동 생성되는 이중화객체
- 샤딩관련 객체에 DDL을 수행하기 위해서는, 샤딩객체에서 설정해제하고, DDL을 한 이후에 다시 샤딩객체로 설정하여야 합니다.
- 예외적으로 아래의 DDL은, 샤딩객체에서 설정해제하지 않고 수행할 수 있도록, 허용되어 있습니다. 이러한 허용 DDL의 종류를 지속적으로 늘려갈 예정입니다.
  - 이중화객체에 대한 FLUSH 구문
  - online partition split 구문

#### 쿼리 제약사항
-   다중 테이블 삽입절(INSERT)은 사용할 수 없다.
-   다중 로우 삽입절(INSERT)은 사용 할 수 없다.
-   이 외의 쿼리에 대한 제약사항은 샤드 쿼리 절을 참고한다.

#### 연결 제약조건
-   샤드 전용 클라이언트 라이브러리를 사용하여야 하이브리드 샤딩방식이 적용된다. 샤드 전용 클라이언트 라이브러리를 사용하지 않으면 서버측 샤딩방식으로만 동작한다.
    - 샤드 전용 클라이언트 라이브러리는 ShardCLI와 ShardJDBC 두가지만 제공한다.
-   다중-쓰레드(multi-thread) 클라이언트 프로그램에서 데이터베이스 커넥션 공유를 지원하지 않는다.
-   SSL 을 지원하지 않는다.
-   IPv6 를 지원하지 않는다.
-   ShardCLI 제약사항은 CLI User's Manual 에서 ShardCLI 부분을 참고한다.
-   ShardJDBC 제약사항은 JDBC User's Manual 에서 Sharding 부분을 참고한다.
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

## Altibase Sharding 사용

이 장에서는 Altibase Sharding 사용 방법을 자세히 설명한다. 앞에서 설명한 샤드 환경 설정과 Zookeeper 설정 이후의 사용 방법을 기술한다.

### Altibase Sharding 사용 기본 흐름
아래의 모든 작업은 sys 사용자로 작업하는것을 가정한다.

모든 작업은 auto commit off 상태에서 진행되어야 하므로, 작업 후에, COMMIT을 수행해 주어야 한다. 단, 노드 추가는 SHARD DDL을 사용하는데, SHARD DDL은 자동으로 COMMIT 혹은 ROLLBACK이 된다. 

1. 샤드 노드별로 아래 구문을 수행하여, 샤드 메타를 각각 생성한다.
   - DBMS_SHARD.CREATE_META()
2. 샤드 노드별로 아래 구문을 수행하여, 노드별 로컬 정보를 각각 설정한다.
   - DBMS_SHARD.SET_LOCAL_NODE(...)
3. 첫번째로 추가될 샤드 노드에 아래 구문을 수행하여, k-safety 관련 전역 복제 정보를 설정한다.
   - DBMS_SHARD.SET_REPLICATION(...)
   - 두번째 이후로 추가되는 노드들은 별도의 설정없이 동일한 k-safety 관련 전역 복제 정보를 사용한다.
   - 모든 노드에 설정해도 되지만, 전역정보 이므로, 첫 번째로 추가되는 노드의 설정과 동일하여야 한다.
4. 샤드 노드별로 각종 데이터베이스 객체들을 생성한다.
   - 객체 생성 DDL을 사용한다.
   - 모든 샤드 노드들은 동일한 데이터베이스 객체들을 갖아야 한다.
5. 샤드 노드별로 아래 SHARD DDL 구문을 수행하여, 모든 노드들을 샤딩 클러스터에 추가한다.
   - ALTER DATABASE SHARD ADD;
   - 개별 샤드 노드들은 샤딩 클러스터에 추가되지 전까지는, sys 사용자를 제외한 다른 일반 사용자의 접속은 차단된다.
6. 샤딩 클러스터에 참여된 하나의 노드에서, 아래 구문들을 이용하여, 객체별 분산정의를 한다.
   - DBMS_SHARD.SET_SHARD_TABLE_SHARDKEY(...), DBMS_SHARD.SET_SHARD_PROCEDURE_SHARDKEY(...) 등등
   - 위 구문들을 이용하여, 객체별 분산정의를 한후에, COMMIT 을 수행하면, 샤딩 클러스터에 참여된 모든 샤드노드들에 동시에 적용된다.

### 샤드 키워드
샤드 키워드를 이용하여, 임의의 쿼리를 수행할 샤드 노드의 범위를 정해서 쿼리를 수행하게 할 수 있다.

#### 구문

샤드 키워드는 다음 구문에 한해 제공하며 구문식은 다음과 같다.

-   SHARD
    - SELECT, INSERT, UPDATE, DELETE
-   NODE[META]
    - SELECT, INSERT, UPDATE, DELETE
-   NODE[DATA | DATA() | DATA('*node1_name'*, '*node2_name'*...)]
    - SELECT

![](media/Sharding/79bcb8f6b5cb10cc7a7b816363aa709f.jpg)

**shard_keyword_clause::=**

![](media/Sharding/d15e35752ab4fd66496232e1d1e055a1.jpg)

#### *SHARD* 샤드 키워드
SHARD 샤드 키워드를 사용하면, 쿼리에 존재하는 샤드객체의 분산정의가 존재하는 모든 샤드 노드(들)에 쿼리를 전송하고 수행하여 취합한다. 분산 수행할 수 있는 샤딩객체가 전혀 없을 때는 에러가 발생한다.

샤딩에서는 아래 두개의 쿼리가 동일한 결과를 얻어온다.
-   SELECT count(\*) FROM *s1;*
-   SELECT sum(cn) FROM SHARD ( SELECT count(\*) cn FROM s1);

집계함수 중 몇가지(SUM,MIN,MAX,COUNT,AVG)에 대해서는 시스템 내부적으로 자동으로 최적화되어 수행하지만, 그외의 경우에는 최적화되어서 수행되지 않으므로, 성능이 느릴수 있다. 이러한 경우에, 사용자가 샤드 키워드를 이용하여, 수동으로 쿼리 튜닝하는 방법으로 사용할 수 있다.
-   SELECT i1, sum(cn) FROM SHARD (SELECT i1, count(\*) cn FROM s1 GROUP BY i1);
-   SELECT \* FROM SHARD (SELECT \* FROM s1 limit 10) limit 10;

#### *NODE* 샤드 키워드
NODE 키워드는 인자로 명시한 노드에 쿼리를 분석 및 변환없이 수행하고, 그 수행 결과를 취합한다. 샤드 쿼리 분석기를 통하지 않고 해당 쿼리를 바로 전달한다. 사용 가능한 NODE 유형은 다음과 같다.
-   NODE[META] : 사용자 세션이 접속한 샤드 노드에 대해 쿼리 분석 및 변환없이 수행
-   NODE[DATA] 또는 NODE[DATA()] : 모든 샤드 노드들에 대해 쿼리 분석 및 변환없이 수행
-   NODE[DATA(*'node1_name*', *node2_name*',...)] : 명시된 노드(들)에 대해 쿼리 분석 및 변환없이 수행

노드를 구성하고 샤드 객체 구성 전 후의 데이터 상태를 확인할 경우에 유용하게 쓰일 수 있다. 아래는 몇가지 사용예이다.
```
NODE[META] SELECT count(*) FROM t1;
NODE[DATA] SELECT count(*) FROM s1;
SELECT * FROM NODE[META](SELECT count(*) FROM s1);
SELECT * FROM NODE[DATA('node1', 'node2')](SELECT count(*) FROM s1);
SELECT * FROM NODE[DATA('node2')](SELECT i1,sum(i1) FROM s1 GROUP BY i1);
```

> ##### 주의 사항
> NODE 샤드 키워드의 적용 결과는 단순히 해당 노드의 수행 결과를 얻어 취합하는 것이므로 결과의 정합성을 보장하지 않는다. 그러므로, NODE 샤드 키워드는 DBA가 임시적으로 사용하는 목적으로만 사용해야 한다.

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
Altibase Sharding 사용자는 iSQL을 통해 쿼리가 수행되는 실행계획을 조회할 수 있다.
- alter session set TRCLOG_DETAIL_SHARD = 1;
  단, TRCLOG_DETAIL_SHARD=1 의 경우 내부적으로 cache 된 plan을 사용하지 않고 새로이 plan을 생성하므로 사용상 주의가 필요하다.
- 샤드 최적화기가 생성한 실행계획과 샤드 노드에서 생성한 실행계획을 모두 조회할 수 있으며 쿼리를 분석하여 최적화 하는데 사용할 수 있다.

##### 설명
SHARD-COORDINATOR 실행노드는 사용자가 입력한 쿼리 중 샤드 노드에서 수행할 쿼리를 수행하고, 그 결과를 통합하여 상위 실행노드로 전달한다.
- 보다 상세한 수행 결과를 조회하기 위하여 다음 명령을 사용한다.
- ALTER SESSION SET TRCLOG_DETAIL_PREDICATE = 1;
- TRCLOG_DETAIL_PREDICATE 프로퍼티 값을 1로 설정하면, SHARD-COORDINATOR가 특정 샤드 노드로 쿼리를 보내어 수행한 이력 및 플랜을 조회할 수 있다. 

##### NON-SHARD QUERY REASON
사용자 쿼리를 논샤드 쿼리로 분석한 이유이다.

##### QUERY TRANSFORMABLE
사용자 쿼리가 논샤드 쿼리로 분류된 경우라면 서버측 샤딩을 수행하게 된다.

샤드 쿼리 최적화기는 해당 쿼리를 서버측에서 수행하기 위해 샤드 쿼리 변환을 통해 최적의 분산부 쿼리 생성을 시도하는데 이 경우 최적화된 분산부 쿼리 생성 가능성을 다음과 같이 표현한다.
- 변환된 분산부 쿼리 생성이 가능하면 'Yes'
- 변환된 분산부 쿼리 생성이 불가하면 'No'

#### 쿼리 튜닝
- GROUP BY 절에 샤드키 컬럼이 포함된 경우 샤드 쿼리로 판단한다.

### Fail-Over
사용자 커넥션에 대한 Fail-Over는 응용 프로그램에서 API의 연결 함수 호출시 입력한 연결 속성 문자열에 명시하거나 연결 설정 파일에 명시한 샤드 노드의 IP, PORT로 시도한다.
- 사용자 커넥션에 대한 Fail-Over는 Replication환경에서 Altibase Fail-Over의 사용법과 동일하며, Replication환경에서 Altibase Fail-Over의 사용법은 *Altibase Replication Manual*을 참고한다.

Fail-Over 콜백 함수는 사용자 커넥션에 대해서만 동작하며 샤드 라이브러리 커넥션에 대한 Fail-Over 콜백 함수는 지원하지 않는다.

#### 응용 프로그램 가이드
Altibase Sharding 환경에서는 여러 샤드 노드에서 수행중인 트랜잭션 및 커넥션이 있으며, 이들은 최적화 과정을 거쳐서 샤드 라이브러리 혹은 서버에서 내부적으로 처리된다. 

이러한 분산 환경에서 응용 프로그램이 트랜잭션 처리를 일관되게 하기 위해서는 NON-AUTOCOMMIT을 사용하여 다음의 가이드에 따라 작성되어야 Fail-Over가 정상적으로 처리될 수 있다.

##### CTF(Connection Time Failover)

CTF의 경우에는 데이터 베이스 연결이 되는지에 따라 성공 여부를 바로 알 수 있다.

다만, 분산 환경에서는 일부 노드의 에러로 인해 실패했을 때, 일부 노드에 접속 되어있을 수 있으므로 명시적으로 SQLDisconnect를 호출하여 전체 연결을 끊어 주어야 한다.

##### STF(Service Time Failover)
ShardCLI 경우는 SQLPrepare, SQLExecute, SQLFetch등에서 SQL_SUCCESS가 아닌 에러가 발생하면, SQLGetDiagRec에 statement 핸들을 넘기고, 이 함수의 5번째 인자에 반환되는 native 에러 코드 값이 ALTIBASE_FAILOVER_SUCCESS인 진단 레코드(diagnostic record)가 있으면 STF가 성공한 것으로 판단할 수 있다.

- NON-AUTOCOMMIT 트랜잭션

ShardCLI 함수에서 SQL_SUCCESS가 아닌 에러가 발생하였을 때 다음의 순서로 에러 로직을 처리한다.

1. STF가 성공한 경우(ALTIBASE_FAILOVER_SUCCESS) Rollback을 수행하며 Rollback이 성공하면 트랜잭션 재시작 위치로 되돌아 가서 응용 프로그램 로직을 수행한다.
   1. 트랜잭션 재시작 위치는 SQLPrepare,SQLExecute를 사용하는 경우 최초 SQLPrepare 이전으로 돌아가야 하며 Bind는 다시 하지 않아도 된다.
   2. SQLDirectExec를 사용하는 경우에는 SQLDirectExec 이전으로 돌아가면 된다.
   3. STF 성공 후 Rollback을 하는 중에 다시 Fail-Over가 발생할 수 있으므로 이 경우에는 Rollback을 한번 더 수행한다.
2. STF가 실패하고 더 이상 서비스 가능한 가용 노드가 없는 경우(ALTIBASE_SHARD_NODE_FAILOVER_IS_NOT_AVAILABLE) 전체 노드에 대한 연결을 명시적으로 끊고 최초 연결부터 재시도 한다.
   1. 샤딩 환경에서는 다수의 노드에 접속이 이뤄져 있으므로 명시적으로 SQLDisconnect를 호출해야 모든 노드에 연결이 끊긴다
3. 그 외의 에러에 대해서는 응용 프로그램 에러 처리 로직을 수행한다.

##### ShardCLI Failover Sample Code
- Altibase Sharding의 failover를 포함하는 ShardCLI sample 코드는 \$ALTIBASE_HOME/sample/SHARD/Fail-Over/failoversample.cpp에 있다.
- failoversample.cpp의 코드는 “CREATE TABLE T1 (I1 VARCHAR(20), I2 INTEGER);”의 구문으로 T1 테이블을 생성한 후 T1 테이블을 샤드 테이블로 등록하였다고 가정한다.
- 해당 프로그램은 최초 접속할 샤드 노드의 port와 alternate port를 순차적으로 입력받아 연결하고 응용 프로그램 로직을 수행하여 Direct-Execute 방식으로 데이터를 한 건 입력하고 Prepare-Execute 방식으로 질의를 수행한 후 검색된 데이터를 출력하는 프로그램이다.
- 예제 프로그램을 수행중에 특정 노드에 장애가 있는 경우 최초 접속시에 CTF가 동작하며 실행 중에는 STF를 통해 fail-over 된다.
- 주의할 점은, 접속을 재시도 하기 위해서는 남아 있을 수 있는 커넥션을 종료하기 위해서 SQLDisconnect를 명시적으로 호출해 주어야 하며, 에러가 발생했을 때에는 다수의 노드에서 발생했을 수 있는 에러를 확인하기 위해서 SQLDiagRec을 통해 모든 노드의 에러를 점검해야 한다.
- 에러 점검을 통해서 Service Time Fail-over가 되면 연결이 종료되지 않은 샤드 노드에 남아 있는 트랜잭션을 정리하기 위해서 SQLEndTran(ROLLBACK)을 호출해 준 후 다시 Prepare 혹은 DirecExecute 로직으로 돌아가서 수행 한다.


## Altibase Sharding 프로퍼티

| **분류**                  | **프로퍼티**                                                 | **동적 변경 허용** | **변경 레벨**   |
| ------------------------- | ------------------------------------------------------------ | ------------------ | --------------- |
| 초기화      | SHARD_ENABLE                                                                | No              |                 |
| 일반 사용자 접속제한 | SHARD_ADMIN_MODE                                                      | Yes                 | SYSTEM                |
| 내부 연결   | SHARD_INTERNAL_CONN_ATTR_RETRY_COUNT SHARD_INTERNAL_CONN_ATTR_RETRY_DELAY SHARD_INTERNAL_CONN_ATTR_CONNECTION_TIMEOUT SHARD_INTERNAL_CONN_ATTR_LOGIN_TIMEOUT | Yes                | SYSTEM          |
| 쿼리 분석   | TRCLOG_DETAIL_SHARD                                          | Yes                | SYSTEM, SESSION |
| 쿼리 변환   | SHARD_AGGREGATION_TRANSFORM_ENABLE<br />SHARD_TRANSFORM_MODE | Yes<br />Yes            | SYSTEM          |
| 메시지 로그 | SD_MSGLOG_COUNT <br />SD_MSGLOG_FILE<br />SD_MSGLOG_FLAG<br />SD_MSGLOG_SIZE | No<br />No<br />Yes<br />No       | SYSTEM          |
| SHARD DDL lock 처리 | SHARD_DDL_LOCK_TIMEOUT<br />SHARD_DDL_LOCK_TRY_COUNT | Yes<br />Yes           | SYSTEM, SESSION |
| 트랜잭션 | GLOBAL_TRANSACTION_LEVEL<br />VERSIONING_MIN_TIME<br />INDOUBT_FETCH_TIMEOUT<br />INDOUBT_FETCH_METHOD<br />SHARD_STATEMENT_RETRY | Yes<br />Yes<br />Yes<br />Yes<br />Yes | SYSTEM, SESSION |

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


#### SHARD_ADMIN_MODE
##### 데이터 타입
Unsigned Integer
##### 기본값
1
##### 속성
변경 가능, 단일 값
##### 값의 범위
[0, 1]
##### 설명
이 프로퍼티는 관리자 모드로 접근하는 것만 허용할지를 제어한다. 1 로 설정하는 경우에, SYS 또는 SYSTEM_ 사용자가 서버와 연결을 맺어 작업을 할 수 있고 그 외 일반 사용자들은 연결 자체가 실패한다.
- 0: OFF
- 1: ON

자동 설정(암시적 설정)
- SHARD_ENABLE 을 1 로 알티베이스 서버를 기동한 경우에, 자동으로 SHARD_ADMIN_MODE 는 1 로 설정 된다.
- 노드가 샤딩 클러스터에 참여하여 정상적으로 운영중에는 자동으로 SHARD_ADMIN_MODE 는 0 으로 변경된다.
- Shard DDL 혹은 비정상적 상황으로 인하여, 노드가 샤딩 클러스터에서 이탈한 경우에는, 자동으로 SHARD_ADMIN_MODE 는 1 으로 변경된다.

명시적 설정
- ALTER SYSTEM SET SHARD_ADMIN_MODE로 변경 가능하다.
- 일반사용자는 ALTER SYSTEM 권한을 가지는 경우 변경 가능하다.
- Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

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

- LIMIT 최적화 변환 기능 켜짐은 1 ( 이진수 표현 0b001 )
- SELECTION 최적화 변환 기능 켜짐은 2 ( 이진수 표현 0b010 )
- PROJECTION 최적화 변환 기능 켜짐은 4 ( 이진수 표현 0b100 )

위 값에 조합으로 제어된다.

예를 들어 다음 구문은 SHARD_TRANSFORM_MODE 값에 따라 아래와 같이 변환하여 수행한다.

SELECT * FROM T1 A LIMIT 1;

```
SHARD_TRANSFORM_MODE = 0;
-> SELECT * FROM SHARD( SELECT * FROM T1 A ) A LIMIT 1;
SHARD_TRANSFORM_MODE = 1;
-> SELECT * FROM SHARD( SELECT * FROM T1 A LIMIT FOR SHARD CAST( 1 AS BIGINT ) + CAST( 1 AS BIGINT ) - 1 ) A LIMIT 1;
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

#### SHARD_DDL_LOCK_TIMEOUT
##### 데이터 타입
Unsigned Integer
##### 기본값
3
##### 속성
변경가능, 단일 값
##### 값의 범위
[0, 65535]
##### 설명
Shard DDL은 다수의 노드에 DDL을 수행하는 것을 통해서 하나의 Shard DDL을 완료할 수 있다. 그러므로, 원격 노드에 수행되는 DDL에 대한 DDL_LOCK_TIMEOUT을 지정해야한다. 이 값은 Shard DDL 내부에서 사용되는 DDL에 대한 DDL_LOCK_TIMEOUT을 지정하기 위해 사용된다.

#### SHARD_DDL_LOCK_TRY_COUNT 
##### 데이터 타입
Unsigned Integer
##### 기본값
200
##### 속성
변경가능, 단일 값
##### 값의 범위
[0, 2^32 -1]
##### 설명
Shard DDL은 다수의 노드에 DDL을 수행하는데, 이 때, 각 노드에서 수행된 DDL이 lock timeout 등의 오류로 실패할 수 있다. 이 프로퍼티는 각 노드에서 수행되는 DDL을 재수행 하는 횟수를 지정한다.

#### GLOBAL_TRANSACTION_LEVEL
##### 데이터 타입
Unsigned Integer
##### 기본값
1
##### 속성
변경가능, 단일 값
##### 값의 범위
[1,2,3]
##### 설명
세션에 설정된 글로벌 트랜잭션 레벨을 나타낸다.(??? 시스템은 안되나 ???)
- 1 : multiple node transaction
- 2 : global transaction
- 3 : global consistent transaction
세션에서 global_transaction_level을 변경시에 이미 트랜잭션이 시작되어 있는 경우에는, 1 과 2 는 서로 변경이 되지만, 1 혹은 2 에서 3 으로 변경할 수는 없다. 3 에서 1 혹은 2 로 변경할 수도 없다.

#### VERSIONING_MIN_TIME
##### 데이터 타입
Unsigned Integer
##### 기본값
0
##### 속성
변경가능, 단일 값, millisecond
##### 값의 범위
[0 ~ 100000]
##### 설명
데이터베이스 스냅샷 유지 시간(millisecond)
- 샤딩에서 GLOBAL_TRANSACTION_LEVEL=3 으로 사용시 VERSIONING_MIN_TIME 을 0 이 아닌값으로 지정해야 합니다.
- 분산 정합성에서 2개 이상의 노드에서 동일한 스냅샷을 scan 하기 위해 요구자 SCN 을 사용하는데 이러한 요구자 SCN 을 허용하기 위해 데이터베이스 스냅샷을 유지하는 최소 시간이 프로퍼티 값입니다.
- 샤딩을 사용시에는 500 millisecond 가 권장값 입니다.

#### INDOUBT_FETCH_TIMEOUT
##### 데이터 타입
Unsigned Integer
##### 기본값
10
##### 속성
변경가능, 단일 값, second
##### 값의 범위
[0 ~ 86400]
##### 설명
Indoubt 트랜잭션 최대 대기 시간(second)

#### INDOUBT_FETCH_METHOD
##### 데이터 타입
Unsigned Integer
##### 기본값
1
##### 속성
변경가능, 단일 값, second
##### 값의 범위
[0,1]
##### 설명
Indoubt 트랜잭션으로 인한 최대 지연 후 처리 방법
- 0: skip
- 1: error

#### SHARD_STATEMENT_RETRY
##### 데이터 타입
Unsigned Integer
##### 기본값
1
##### 속성
변경가능, 단일 값
##### 값의 범위
[0 ~ 65535]
##### 설명
샤드 데이터베이스의 최신 스냅샷을 얻기 위한 재시도 횟수

## Shard DDL
- Shard DDL은 샤딩 클러스터 시스템의 노드 구성 형상에 영향을 주는 명령어이다. 샤드 노드 추가/삭제/참여/샤드이중화재구성/리샤딩 등이 있다.
- SYS 사용자이어야 한다.
- GLOBAL_TRANSACTION_LEVEL 설정 값이 2 또는 3 이어야 한다.
- SHARD_ENABLE 설정 값이 1 이어야 한다.
- SHARD 메타정보가 구성되어 있어야 한다.
- Zookeeper가 구성되어 있어야 한다.
- 다른 세션에서 이미 SHARD DDL을 수행중이면, 해당 SHARD DDL의 수행이 완료될때까지는 대기된다. 

### ADD

#### 구문
ALTER DATABASE SHARD ADD ;

#### 설명
본 구문을 수행하는 노드를 샤딩 클러스터에 추가 하기 위한 구문이다.

노드가 샤딩 클러스터에 추가되면, 자동으로 SHARD_ADMIN_MODE가 0 으로 변경되고, 일반 사용자도 해당 노드에 접속할 수 있게 된다.

샤딩 클러스터에 속한 모든 노드들이 정상적인 상황에서만 수행이 가능한 명령이다. 
- shutdown 된 노드가 있다면, 먼저 join을 수행하여야 한다.
- failover 된 노드가 있다면, 먼저 failback이 수행되어야 한다.
- drop 명령어에 의해서 샤딩 클러스터에서 제외된 노드는, 더이상 샤딩 클러스터에 속한 노드가 아니므로 상관없다. 

샤드 노드를 추가하기 전에, 각종 데이터베이스 객체들을 미리 생성하는 것이 편리하다.
- 기존에 이미 데이터베이스 객체들이 모두 생성된 샤드 노드가 있다면, 해당 노드에서 aexport 유틸리티를 이용하여, 객체 생성구문을 얻을 수 있다.
- 로컬 테이블들은 이미 추가된 다른 샤드노드들과 객체 생성 정보가 틀려도 된다.
- 샤드 객체들은 이미 추가된 다른 샤드노드들과 객체 생성 정보가 동일 하여야 한다.
- 샤드 테이블들은 모두 비어 있어야 한다.

샤드 노드를 추가하는 순간 아래와 같은 작업이 내부적으로 수행된다.
- Zookeeper 에 접속되고, Zookeeper 메타에 추가되는 샤드 노드에 대한 정보가 설정된다.
- 클론 테이블은 이미 추가된 다른 샤드 노드에서 복제하여 동일하게 데이터가 설정된다.
- 샤드 메타정보도 이미 추가된 다른 샤드 노드에서 복제하여 동일하게 데이터가 설정된다.

### DROP

#### 구문
ALTER DATABASE SHARD DROP ;

#### 설명
본 구문을 수행하는 노드를 샤딩 클러스터에 제거 하기 위한 구문이다.
- 샤딩 클러스터에 속한 모든 노드들이 정상적인 상황에서만 수행이 가능한 명령이다. 
- 본 구문의 수행 노드는 샤딩 클러스터에 추가되어 정상적으로 운영중인 상태이어야 한다. 
- 노드가 샤딩 클러스터에 제거되면, 자동으로 SHARD_ADMIN_MODE가 1 으로 변경되고, 일반 사용자는 해당 노드에 접속할 수 없게 된다.
- 클론 테이블을 제외하고, 해당 샤드 노드에 속한 샤드 테이블의 데이터 영역이 있다면, 샤드 노드 삭제를 할 수 없다. 
  리샤딩을 이용하여, 해당 데이터 영역을 다른 샤드 노드로 이동 먼저 시킨 후에, 샤드 노드 삭제를 할 수 있다. 

### JOIN

#### 구문
ALTER DATABASE SHARD JOIN ;

#### 설명
본 구문을 수행하는 노드를 샤딩 클러스터에 다시 참여 시키기 위한 구문이다.

본 구문의 수행 노드는 샤딩 클러스터에 추가된 후에, shutdown 명령으로 샤딩 클러스터에서 이탈된 상태이어야 한다. 

노드가 샤딩 클러스터에 다시 참여되면, 자동으로 SHARD_ADMIN_MODE가 0 으로 변경되고, 일반 사용자도 해당 노드에 접속할 수 있게 된다.

### FAILOVER

#### 구문
ALTER DATABASE SHARD FAILOVER "target_node_name" ;

#### 설명
특정 노드에 장애가 발생하였을 때, 다른 노드에서 장애가 발생한 노드의 데이터 영역을 서비스 할 수 있도록 하는 작업이다.

기본적으로는 Zookeeper에 의해 장애노드가 감지되면 자동으로 수행된다. 또한, 사용자가 수동으로 실행 할 수도 있다.

설정된 K-Safety 값에 따라 최대 2차 장애까지는 데이터의 손실없는 failover를 제공할 수 있다.

정상적인 상태의 노드들 중에 노드 이름으로 오름차순으로 정렬 했을때, 장애가 발생한 target node 의 이름과 비교해서 바로 다음 순서에 있는 노드를 next alive node 라고 한다. 이름 순으로 가장 마지막에 있던 노드의 next alive node는 이름 순으로 가장 처음에 위치하는 노드가 된다. 즉, 이름 순서는 환(ring)의 형태로 검색하도록 되어 있다.

failover가 완료되면, next alive node가 장애가 발생한 target node에서 서비스하던 데이터를 서비스 하게 된다.

자동으로 failover가 될때이든, 사용자가 수동으로 failover 명령어를 수행할 때이든, 장애가 발생한 target node 는 kill 된다.

사용자가 수동으로 failover 명령어를 수행할 때는, 수행 노드와 target node가 동일 노드일때는 명령수행이 실패한다. 또한, 수행노드는 정상적으로 운영중이 상태이어야 한다. 그리고, 이미 failover 된 노드를 다시 failover 시킬 수는 없다.

자동으로 failover가 수행되는 경우에, next alive node가 failover 명령어의 수행노드가 된다. 또한, 여러 노드에 장애가 발생할 경우 시스템 내부적으로, 장애가 발생한 노드들의 이름들로 list가 구성되고, 장애를 감지한 수행노드를 기준으로 정렬된 역순으로 failover 를 수행하게 된다.

예를들어, N1~6 노드가 존재하는데, N1 노드와 N3 노드가 장애노드가 되었을 때, N4가 감지하였을 경우 N3 노드 먼저 그리고, N1 노드 순서로 failover되고, N2 노드가 감지할 경우 N1 노드 먼저 그리고, N3 노드의 순서로 failover 된다.

failover된 노드는, 사용자의 failback 명령에 의해서만 다시 샤딩 클러스터에 참여할 수 있다.

### FAILBACK

#### 구문
ALTER DATABASE SHARD FAILBACK ;

#### 설명
본 구문을 수행하는 노드를 샤딩 클러스터에 다시 failback 시키기 위한 구문이다.

본 구문의 수행 노드는 아래 노드들이 대상이 된다.
- 장애가 발생하여 자동으로 failover 된 노드
- 사용자가 수동으로 failover 구문을 수행하여 failover 된 노드
- 사용자에 의한 shutdown 명령어에 의하지 않고, 비정상적 상태가 되었으나, failover는 되지 않은 노드
- 단, 사용자의 shutdown 명령어에 의해 shutdown된 노드에서는 failback 구문을 수행할 수 없다. 이 경우에는 JOIN 구문을 이용하여 샤딩 클러스터에 재 참여하여야 한다.

### MOVE

#### 구문
```
ALTER DATABASE SHARD MOVE { TABLE ["user_name" . ] "table_name" [ PARTITION {"(partition_name)"} ] | PROCEDURE ["user_name" . ] "procedure_name" KEY ( "value" ) }+  TO "node_name" ;
```

#### 설명
시스템 운영중에 본 구문을 수행하여, 샤드 테이블 및 샤드 프로시져의 분산정의를 변경하기 위한 구문이다.
- 샤드 객체의 분산 영역에 대한 정의를 사용자가 지정한 노드로 이동시킨다.
- 샤드키 테이블에 대하여는 개별 파티션별로 지정한 노드로 이동이 가능하다.
- 솔로 테이블에 대하여는 해당 테이블 전체에 대하여 지정한 노드로 이동이 가능하다.
- 샤드 프로시져에 대하여는 샤드키의 value 하나에 대하여 지정한 노드로 이동이 가능하다.
- 두 노드간의 이동이 가능하다. 원천 노드가 두개 이상인 경우는 수행할 수 없다. 
- 한번에 다수의 샤드 객체에 대한 변경이 가능하다.

#### 예제
```
ALTER DATABASE SHARD MOVE TABLE user1.table1 PARTITION (p1), TABLE user2.soloTable1, TABLE user1.table2 PARTITION (p2), PROCEDURE user1.shardproc1 key ( 123 )  TO NODE4; ;
```

## Altibase Sharding 딕셔너리
Altibase Sharding의 데이터 딕셔너리는 샤드 객체 정보를 저장하는 샤드 메타 테이블들과 단일 샤드 노드의 샤딩 관련 시스템 프로세스 정보를 보여주는 성능 뷰(Performance View)들,
그리고 전체 샤딩 시스템의 실시간 정보를 보여주는 샤드 성능 뷰(Shard Performance View)들로 나뉘어진다.

### 샤드 메타 테이블
분산 데이터베이스에 생성된 분산 객체에 대한 정보를 저장하고 있으며, SYS_SHARD 사용자의 테이블이다.
- 분산 데이터베이스 질의 및 분산 노드 관리시에 샤드 메타 테이블을 사용한다.
- 샤드 메타 테이블의 소유자는 일반 메타 테이블과는 달리 SYS_SHARD 사용자이며, 샤드 메타 테이블에 대한 변경은 DBMS_SHARD 패키지를 이용해야 한다.
- DBMS_SHARD 패키지 이외의 방법으로 샤드 메타 테이블을 변경하면 샤딩 시스템 구동이 실패하거나, 분산 데이터베이스 관련 정보를 상실하여 시스템에 치명적인 손상이 발생할 수 있다.
- Altibase Sharding에 새로운 기능이 제공되거나 기존 구문의 기능 변경 시 샤드 메타 테이블 스키마가 변경될 수 있다. 샤드 메타 테이블 스키마의 변경이 발생하면 데이터베이스 마이그레이션이 필요하다.
- Altibase Sharding하위 버전에서 상위 버전으로 업그레이드 시 이를 고려해야 한다.

#### 샤드 메타 테이블 종류
- VERSION_: Altibase Sharding의 버전을 기록하는 샤드 메타 테이블
- LOCAL_META_INFO_: 지역 데이터베이스의 샤드 정보를 기록하는 샤드 메타 테이블
- GLOBAL_META_INFO_: 샤드 메타 제어 정보를 기록하는 샤드 메타 테이블
- NODES_: 샤드 노드 정보를 기록하는 샤드 메타 테이블
- OBJECTS_: 샤드 객체 정보를 기록하는 샤드 메타 테이블
- RANGES_: 샤드 키 분산 테이블 정보를 기록하는 샤드 메타 테이블
- CLONES_: 복제 분산 테이블 정보를 기록하는 샤드 메타 테이블
- SOLOS_: 독립 분산 테이블 정보를 기록하는 샤드 메타 테이블
- REPLICA_SETS_: 샤드 노드의 레플리카 셋을 기록하는 샤드 메타 테이블
- FAILOVER_HISTORY_: 샤드 시스템의 Failover History를 기록하는 샤드 메타 테이블

#### SYS_SHARD.VERSION_
Altibase Sharding의 버전을 기록하는 메타 테이블이다.
- MAJOR_VER (INTEGER): Altibase Sharding 메이저 버전을 나타낸다.
- MINOR_VER (INTEGER): Altibase Sharding 마이너 버전을 나타낸다.
- PATCH_VER (INTEGER): Altibase Sharding 패치 버전을 나타낸다.

#### SYS_SHARD.LOCAL_META_INFO_
지역 데이터베이스의 샤드 노드 하나에 대한 정보만을 기록하는 메타 테이블이다.
- SHARD_NODE_ID (INTEGER): 지역 데이터베이스의 샤드 노드 식별자로 전체 샤딩 시스템에서 유일해야 한다.
- SHARDED_DB_NAME (VARCHAR(40)): 지역 샤드 노드가 참여할 논리적인 샤드된 데이터 베이스 이름을 나타내며, 지역 데이터 베이스의 DB 이름으로 자동으로 설정된다. 
- NODE_NAME (VARCHAR(40)): 지역 샤드 노드의 이름이다.
- HOST_IP (VARCHAR(64)): 지역 샤드 노드에서 서비스에 사용할 호스트 IP 이다. 
- PORT_NO (INTEGER): 지역 샤드 노드에서 서비스에 사용할 Port 이다. 
- INTERNAL_HOST_IP (VARCHAR(64)): 지역 샤드 노드에서 코디네이터가 내부적으로 사용하는 호스트 IP 이다. 
- INTERNAL_PORT_NO (INTEGER): 지역 샤드 노드에서 코디네이터가 내부적으로 사용할 Port 이다. 
- INTERNAL_REPLICATION_HOST_IP (VARCHAR(64)): 지역 샤드 노드에서 내부 복제용으로 사용할 호스트 IP 이다.
- INTERNAL_REPLICATION_PORT_NO (INTEGER): 지역 샤드 노드에서 내부 복제용으로 사용할 Port로 REPLICATION_PORT_NO 프로퍼티 값과 동일한 값으로 유지되어야 한다.
- INTERNAL_CONN_TYPE (INTEGER): 내부적으로 사용되는 코디네이터 연결 방식이다. 1로 설정된 경우 TCP를 사용하며 8인 경우 인피니 밴드를 사용한다.  
- K_SAFETY (INTEGER): 시스템 내에서 유지할 복제본의 개수를 나타낸다.  
- REPLICATION_MODE (INTEGER): 시스템에서 사용하는 샤드 이중화 모드를 나타낸다. 
  - 값이 12인 경우 'CONSISTENT' 샤드 이중화 모드를 의미하며, 10인 경우 샤드 이중화 모드 중 'NOWAIT' 모드를 나타낸다.  
- PARALLEL_COUNT (INTEGER): 샤드 이중화에서 사용하는 이중화 병렬 적용자의 수를 나타낸다. 

#### SYS_SHARD.GLOBAL_META_INFO_
샤드 메타 정보에 대한 내용을 기록하는 메타 테이블이다.
- ID (INTEGER):시스템 내부적으로 복제를 위해 사용되는 키 값
- SHARD_META_NUMBER (BIGINT):데이터베이스의 샤드 메타에서 유지하는 메타 정보 중 가장 최신 메타에 대한 샤드 메타 번호(Shard Meta Number)를 나타낸다.

#### SYS_SHARD.NODES_
Altibase Sharding의 모든 샤드 노드들의 정보를 기록하는 메타 테이블이다.
- NODE_ID (INTEGER): 샤드 노드의 지역 식별자
- NODE_NAME (VARCHAR(40)): 샤드 노드 이름
- HOST_IP (VARCHAR(64)): 샤드 라이브러리 또는 외부 응용프로그램에서 연결할 샤드 노드의 ip address를 나타낸다.
- PORT_NO (INTEGER): 샤드 라이브러리 또는 외부 응용프로그램에서 연결할 샤드 노드의 port 번호를 나타낸다.
- ALTERNATE_HOST_IP (VARCHAR(64)): Unused, reserved for future use
- ALTERNATE_PORT_NO (INTEGER): Unused, reserved for future use
- INTERNAL_HOST_IP (VARCHAR(64)): 샤드 노드의 코디네이터가 연결할 internal ip address
- INTERNAL_PORT_NO (INTEGER): 샤드 노드의 코디네이터가 연결할 internal port 번호
- INTERNAL_ALTERNATE_HOST_IP (VARCHAR(64)): Unused, reserved for future use
- INTERNAL_ALTERNATE_PORT_NO (INTEGER): Unused, reserved for future use
- INTERNAL_CONN_TYPE (INTEGER): 샤드 노드의 internal 연결 방식
- SMN (BIGINT): 샤드 메타 번호

#### SYS_SHARD.OBJECTS_
Altibase Sharding의 샤드 객체 정보를 기록하는 메타 테이블이다.
- SHARD_ID (INTEGER): 샤드 객체 식별자
- USER_NAME (VARCHAR(128)): 샤드 객체 소유자
- OBJECT_NAME (VARCHAR(128)): 샤드 객체 이름
- OBJECT_TYPE (CHAR(1)): 샤드 객체 종류 T : 테이블 P : 프로시저
- SPLIT_METHOD (CHAR(1)): 분산 방식(H: hash, R: range, L: list, C: clone, S: solo)
- KEY_COLUMN_NAME (VARCHAR(128)): 샤드 키 이름
- SUB_SPLIT_METHOD (CHAR(1)): Unused, reserved for future use
- SUB_KEY_COLUMN_NAME (VARCHAR(128)): Unused, reserved for future use
- DEFAULT_NODE_ID (INTEGER): 기본 샤드 노드 번호
- DEFAULT_PARTITION_NAME (VARCHAR(128)): 기본 파티션 이름
- DEFAULT_PARTITION_REPLICA_SET_ID (INTEGER): 기본 파티션에 연결된 레플리카셋 ID
- SMN (BIGINT): 샤드 메타 번호

#### SYS_SHARD.RANGES_
샤드 키 분산 테이블(HASH, RANGE, LIST)의 분산 정보를 기록하는 메타 테이블이다.
- SHARD_ID (INTEGER): 샤드 객체 식별자
- PARTITION_NAME (VARCHAR(128)): 샤드 객체의 파티션 이름
- VALUE (VARCHAR(100)): 샤드 키 값
- SUB_VALUE (VARCHAR(100)):: Unused, reserved for future use
- NODE_ID (INTEGER): VALUE를 기준으로 저장되는 데이터의 노드 번호를 나타낸다.
- SMN (BIGINT): 샤드 메타 번호
- REPLICA_SET_ID (INTEGER): 샤드 객체와 연결된 레플리카 셋의 식별번호

#### SYS_SHARD.CLONES_
샤드 객체에 클론 분산 방식이 적용된 분산 정보를 기록하는 메타 테이블이다.
- SHARD_ID (INTEGER): 샤드 객체 식별자
- NODE_ID (INTEGER): 샤드 노드의 지역 식별자
- SMN (BIGINT): 샤드 메타 번호
- REPLICA_SET_ID (INTEGER): 샤드 객체와 연결된 레플리카 셋의 식별번호

#### SYS_SHARD.SOLOS_
샤드 객체에 솔로 분산 방식이 적용된 샤드 테이블 정보를 기록하는 메타 테이블이다.
- SHARD_ID (INTEGER): 샤드 객체 식별자
- NODE_ID (INTEGER): 샤드 노드의 지역 식별자
- SMN (BIGINT): 샤드 메타 번호
- REPLICA_SET_ID (INTEGER): 샤드 객체와 연결된 레플리카 셋의 식별번호

#### SYS_SHARD.REPLICA_SETS_
Sharding HA를 제공하기 위해 생성한 데이터 복제(Replication)간의 관계를 나타내는 레플리카 셋을 저장한 메타 테이블이다.
- REPLICA_SET_ID (INTEGER): 레플리카 셋의 식별자
- PRIMARY_NODE_NAME (VARCHAR(40)): 레플리카 셋과 연결된 주 노드 이름
- FIRST_BACKUP_NODE_NAME (VARCHAR(40)): 레플리카 셋의 첫번째 Backup 노드 이름
- SECOND_BACKUP_NODE_NAME (VARCHAR(40)): 레플리카 셋의 두번째 Backup 노드 이름
- STOP_FIRST_BACKUP_NODE_NAME (VARCHAR(40)): 이중화가 중지된 상태에서의 레플리카 셋의 첫번째 Backup 노드 이름
- STOP_SECOND_BACKUP_NODE_NAME (VARCHAR(40)): 이중화가 중지된 상태에서의 레플리카 셋의 두번째 Backup 노드 이름
- FIRST_REPLICATION_NAME (VARCHAR(40)): 첫번째 Backup의 이중화 이름
- FIRST_REPL_FROM_NODE_NAME (VARCHAR(40)): 첫번째 Backup의 송신자 노드의 이름
- FIRST_REPL_TO_NODE_NAME (VARCHAR(40)): 첫번째 Backup의 수신자 노드의 이름
- SECOND_REPLICATION_NAME (VARCHAR(40)): 두번째 Backup의 이중화 이름
- SECOND_REPL_FROM_NODE_NAME (VARCHAR(40)): 두번째 Backup의 송신자 노드의 이름
- SECOND_REPL_TO_NODE_NAME (VARCHAR(40)): 두번째 Backup의 수신자 노드의 이름
- SMN (BIGINT): 샤드 메타 번호

#### SYS_SHARD.FAILOVER_HISTORY_
Failover 발생시 레플리카 셋(ReplicaSet)의 변경 내역을 저장한 메타 테이블이다.
- REPLICA_SET_ID (INTEGER): 레플리카 셋의 식별자
- PRIMARY_NODE_NAME (VARCHAR(40)): 레플리카 셋과 연결된 주 노드 이름
- FIRST_BACKUP_NODE_NAME (VARCHAR(40)): 레플리카 셋의 첫번째 Backup 노드 이름
- SECOND_BACKUP_NODE_NAME (VARCHAR(40)): 레플리카 셋의 두번째 Backup 노드 이름
- STOP_FIRST_BACKUP_NODE_NAME (VARCHAR(40)): 이중화가 중지된 상태에서의 레플리카 셋의 첫번째 Backup 노드 이름
- STOP_SECOND_BACKUP_NODE_NAME (VARCHAR(40)): 이중화가 중지된 상태에서의 레플리카 셋의 두번째 Backup 노드 이름
- FIRST_REPLICATION_NAME (VARCHAR(40)): 첫번째 Backup의 이중화 이름
- FIRST_REPL_FROM_NODE_NAME (VARCHAR(40)): 첫번째 Backup의 송신자 노드의 이름
- FIRST_REPL_TO_NODE_NAME (VARCHAR(40)): 첫번째 Backup의 수신자 노드의 이름
- SECOND_REPLICATION_NAME (VARCHAR(40)): 두번째 Backup의 이중화 이름
- SECOND_REPL_FROM_NODE_NAME (VARCHAR(40)): 두번째 Backup의 송신자 노드의 이름
- SECOND_REPL_TO_NODE_NAME (VARCHAR(40)): 두번째 Backup의 수신자 노드의 이름
- SMN (BIGINT): 샤드 메타 번호

### 성능 뷰 (Performance View)
Altibase Sharding에서 성능 뷰는 단일 샤드 노드에서 실행중인 프로세스에 대한 정보를 의미하며 현재 사용자 세션이 접속된 시스템에 대한 정보를 보여준다.

Altibase에서 제공하는 성능 뷰를 통해서 단일 샤드 노드의 다양한 실행 정보를 얻을수 있으며 자세한 내용은 *General Reference* 의 성능 뷰를 참고한다.

### 샤드 성능 뷰 (Shard Performance View)
Altibase Sharding에서 제공하는 샤딩 전용의 성능 뷰로 전체 샤딩 시스템과 관련한 내부 정보(예. 샤드 세션 정보)를 사용자가 모니터링 할 수 있다.

샤드 성능 뷰의 전체 목록은 iSQL에서 다음과 같이 조회할 수 있다.
iSQL\> SELECT \* FROM S$TAB;

샤드 성능 뷰의 스키마는 일반 테이블과 마찬가지로 iSQL 에서 DESC 명령어를 통해 확인할 수 있고, 데이터는 일반 테이블과 동일하게 SELECT문을 이용하여 검색할 수 있다.

#### 샤드 성능 뷰의 종류
- S$CONNECTION_INFO: 현재 세션에서의 코디네이팅 샤드 노드와 다른 샤드 노드의 연결 상태에 대한 정보
- S$DIST_LOCK_WAIT:
- S$LOCK_WAIT:
- S$PENDING_WAIT:
- S$PROPERTY: 모든 샤드 노드의 시스템 프로퍼티 정보
- S$SESSION: 모든 샤드 노드의 샤드 세션에 대한 세션 정보
- S$STATEMENT: 모든 샤드 노드의 세션에서 수행되는 모든 구문 정보
- S$TIME_SCN:
- S$TRANSACTION:

#### S$CONNECTION_INFO
현재 세션에서 코디네이터가 연결한 접속 상태에 대한 정보를 보여주는 성능 뷰 이다.
- NODE_ID (INTEGER): 샤드 노드의 지역 식별자
- NODE_NAME (VARCHAR(40)): 샤드 노드 이름
- COMM_NAME (VARCHAR(64)): 접속 정보
- TOUCH_COUNT (INTEGER): 현재 트랜잭션의 DML 발생 횟수
- LINK_FAILURE (INTEGER): 샤드 노드의 연결 상태 0: 정상 1: 실패

#### S$DIST_LOCK_WAIT
- NODE_NAME (VARCHAR(40)):   
- TRANS_ID (BIGINT): 
- SHARD_PIN (VARCHAR(20)):    
- FIRST_STMT_SCN (VARCHAR(29)):    
- FIRST_STMT_TIME (VARCHAR(64)):    
- DISTRIBUTION_LEVEL (INTEGER):        
- WAIT_FOR_TRANS_ID (BIGINT):         
- WAIT_FOR_SHARD_PIN (VARCHAR(20)):    
- WAIT_FOR_FIRST_STMT_SCN (VARCHAR(29)):    
- WAIT_FOR_FIRST_STMT_TIME (VARCHAR(64)):    
- WAIT_FOR_DISTRIBUTION_LEVEL (INTEGER):        
- DEADLOCK_DETECTION_CAUSE (VARCHAR(64)):    
- DEADLOCK_WAIT_TIME (BIGINT):         
- DEADLOCK_ELAPSED_TIME (BIGINT):  

#### S$LOCK_WAIT
- NODE_NAME (VARCHAR(40)):   
- TRANS_ID (BIGINT): 
- SHARD_PIN (VARCHAR(20)):    
- FIRST_STMT_SCN (VARCHAR(29)):    
- FIRST_STMT_TIME (VARCHAR(64)):    
- DISTRIBUTION_LEVEL (INTEGER):        
- WAIT_FOR_TRANS_ID (BIGINT):         
- WAIT_FOR_SHARD_PIN (VARCHAR(20)):    
- WAIT_FOR_FIRST_STMT_SCN (VARCHAR(29)):    
- WAIT_FOR_FIRST_STMT_TIME (VARCHAR(64)):    
- WAIT_FOR_DISTRIBUTION_LEVEL (INTEGER):        

#### S$PENDING_WAIT
- NODE_NAME (VARCHAR(40)):   
- TRANS_ID (BIGINT): 
- SHARD_PIN (VARCHAR(20)):    
- WAIT_FOR_TRANS_ID (BIGINT):         
- WAIT_FOR_XID (VARCHAR(256)):    
- WAIT_FOR_SHARD_PIN (VARCHAR(20)):    

#### S$PROPERTY
샤딩 시스템의 각 노드에 설정된 시스템 프로퍼티의 정보를 보여준다.
- NODE_NAME (VARCHAR(40)): 샤드 노드 이름
- 그 외 컬럼들은 V$PROPERTY 와 동일하다.

#### S$SESSION
샤드 세션과 관련한 모든 샤드 노드의 세션에 대한 정보를 보여준다.
- ID (VARCHAR(20)): 샤드 세션 식별자
- SHARD_META_NUMBER (BIGINT): 세션이 인식하고 있는 SMN
- NODE_NAME (VARCHAR(40)): 샤드 노드 이름
- SHARD_CLIENT (VARCHAR(1)): 샤드 클라이언트 라이브러리 사용 유무
  - Y : 샤드 클라이언트 라이브러리 사용
  - N : 샤드 클라이언트 라이브러리 미사용
- SHARD_SESSION_TYPE (VARCHAR(1)): 샤드 세션 유형
  - U : 사용자와 코디네이터간의 사용자(User) 세션
  - C : 코디네이터와 샤드 데이터간의 코디네이터(Coordinator) 세션
  - L : 사용자와 샤드 데이터간의 샤드 라이브러리(Library) 세션
- SESSION_ID (BIGINT): 샤드 노드의 V$SESSION.ID
- GLOBAL_TRANSACTION_LEVEL (INTEGER): 글로벌 트랜잭션 레벨
  - 1 : multiple node transaction
  - 2 : global transaction
  - 3 : global consistent transaction
- GCTX_COORD_SCN (BIGINT):
- GCTX_PREPARE_SCN (BIGINT):
- GCTX_GLOBAL_COMMIT_SCN (BIGINT):
- GCTX_LAST_SYSTEM_SCN (BIGINT):
- SHARD_STATEMENT_RETRY (INTEGER):
- INDOUBT_FETCH_TIMEOUT (INTEGER):        
- INDOUBT_FETCH_METHOD (INTEGER):
- 그 외 컬럼들은 V$SESSION 과 동일하다.

#### S$STATEMENT
모든 샤드 노드의 세션 별로 실행중이거나 가장 최근 실행된 구문에 대한 정보를 보여준다.
- SHARD_SESSION_ID (VARCHAR(20)): 샤드 세션 식별자
- NODE_NAME (VARCHAR(40)): 샤드 노드 이름
- SHARD_SESSION_TYPE (VARCHAR(1)): 세션의 샤드 세션 유형 (S$SESSION.SHARD_SESSION_TYPE 과 동일하다.)
- QUERY_TYPE (VARCHAR(1)): 사용자 쿼리에 대한 샤드 쿼리 타입
  - S (Shard query) : 분산 수행 결과와 단일 수행 결과의 정합성이 보장되는 경우
  - N (Non-shard query) : 분산 수행 결과와 단일 수행 결과의 정합성이 보장되지 않는 경우
  - 단, 코디네이터 커넥션을 통해 수행되는 구문의 경우 분석 대상이 아니므로 '-' 로 표시된다.
- GCTX_REQUEST_SCN (BIGINT):         
- GCTX_FIRST_STMT_SCN (BIGINT):         
- GCTX_FIRST_STMT_TIME (BIGINT):         
- DISTRIBUTION_LEVEL (INTEGER):  
- 그 외 컬럼들은 V$STATEMENT 와 동일하다.

#### S$TIME_SCN
- NODE_NAME (VARCHAR(40)):    
- TIME (VARCHAR(32)):
- SYSTEM_SCN (VARCHAR(29)):    
- BASE (CHAR(1)):  

#### S$TRANSACTION
- NODE_NAME (VARCHAR(40)):
- FIRST_MIN_DISK_VIEW_SCN (VARCHAR(29)):    
- LAST_REQUEST_VIEW_SCN (VARCHAR(29)):    
- PREPARE_SCN (VARCHAR(29)):    
- SHARD_PIN (VARCHAR(20)):
- GCTX_FIRST_STMT_TIME (VARCHAR(64)):    
- GCTX_FIRST_STMT_SCN (VARCHAR(29)):    
- DISTRIBUTION_LEVEL (INTEGER):      
- GLOBAL_CONSISTENCY (INTEGER):
- DEADLOCK_DETECTION_CAUSE (VARCHAR(64)):    
- DEADLOCK_WAIT_TIME (BIGINT):      
- DEADLOCK_ELAPSED_TIME (BIGINT):
- 그 외 컬럼들은 V$TRANSACTION 과 동일하다.

5.Altibase Sharding 패키지
------------------------
Altibase Sharding 패키지를 구성하는 프로시저와 함수에 대해 설명한다.
### DBMS_SHARD
DBMS_SHARD 패키지는 Altibase Sharding의 샤드 설정과 관리에 사용한다.
- 이미 수행중인 트랜잭션이 있는 경우 commit 혹은 rollback 처리 후에 DBMS_SHARD 패키지의 프로시저들을 수행할 수 있다.
- DBMS_SHARD 패키지의 프로시저들은 수행 성공하면 자동으로 commit 되며, 수행 실패하면 자동으로 rollback 된다.  
- DBMS_SHARD 패키지의 프로시저들은 global transaction level 2 이상에서만 수행할 수 있다.
- node name은 모두 대문자로 처리된다.

아래의 표와 같이 DBMS_SHARD 패키지를 구성하는 프로시저와 함수를 제공한다.
- CREATE_META: 샤드 노드에서 샤드 메타 테이블을 생성한다.
- SET_LOCAL_NODE: 지역 샤드 노드의 정보를 설정한다.
- SET_REPLICATION: 샤딩 클러스터 시스템의 데이터 복제 방식을 설정한다.
- SET_SHARD_TABLE_SHARDKEY: 샤드키 테이블 샤드객체로 등록한다.
- SET_SHARD_TABLE_SOLO: 솔로 테이블 샤드객체로 등록한다.
- SET_SHARD_TABLE_CLONE: 클론 테이블 샤드객체로 등록한다.
- SET_SHARD_PROCEDURE_SHARDKEY: 샤드키 프로시저 샤드객체로 등록한다.
- SET_SHARD_PROCEDURE_SOLO: 솔로 프로시저 샤드객체로 등록한다.
- SET_SHARD_PROCEDURE_CLONE: 클론 프로시저 샤드객체로 등록한다.
- UNSET_SHARD_TABLE: 샤드 테이블을 해제한다.
- UNSET_SHARD_PROCEDURE: 샤드 프로시저를 해제한다.

#### CREATE_META
##### 구문
```
DBMS_SHARD.CREATE_META()
```

##### 파라미터
없음.

##### 설명
현재 접속 노드에서 샤드 메타 테이블을 생성한다.

create_meta를 수행하면 SYS_SHARD 계정이 생성되고 샤드에 메타를 저장할 테이블과 인덱스, 시퀀스가 생성된다.

##### 예제
```
iSQL> EXEC dbms_shard.create_meta();
```

#### SET_LOCAL_NODE
##### 구문
```
DBMS_SHARD.SET_LOCAL_NODE( 
  shard_node_id in integer,
  node_name in varchar(10),
  host_ip in varchar(64),
  port_no in integer,
  internal_host_ip in varchar(64),
  internal_port_no in integer,
  internal_replication_host_ip in varchar(64),
  internal_replication_port_no in integer,
  conn_type in integer default NULL );
```
##### 파라미터
- shard_node_id: 지역 샤드 노드의 샤드 노드 식별자로 전체 시스템에서 유일해야한다.
  - shard_node_id 값 범위: 0\~65535 (TOBEMODIFIED) 1 \~ 9999 로 조정되어야 한다. sharded sequence 에서 shard_node_id를 사용하기 때문이다.
- node_name: 지역 샤드 노드에서 사용할 노드 이름을 입력하며, 샤드 노드 이름도 전체 시스템에서 유일해야한다. node_name 의 대소문자는 구별하지 않는다.
- host_ip: 지역 샤드 노드에서 서비스에 사용할 호스트 IP를 입력한다. 
- port_no: 지역 샤드 노드에서 서비스에 사용할 Port를 입력한다. 
- internal_host_ip: 지역 샤드 노드에서 코디네이터가 내부적으로 사용할 호스트 IP를 입력한다. 이더넷 및  인피니 밴드를 지원한다.
- internal_port_no: 지역 샤드 노드에서 코디네이터가 내부적으로 사용할 Port를 입력한다. 
- internal_replication_host_ip: 지역 샤드 노드에서 내부 복제용으로 사용할 호스트 IP를 입력한다. internal_host_ip와 동일한 라인을 사용할 것을 권장한다. 
- internal_replication_port_no: 지역 샤드 노드에서 내부 복제용으로 사용할 Port로 REPLICATION_PORT_NO 프로퍼티 값과 동일한 값을 입력해야한다. 
- conn_type: 내부적으로 사용되는 코디네이터 연결 방식으로 입력하지 않는 경우 TCP를 사용한다. 그 외 지원 타입은 *Altibase Sharding 통신 방법*의 코디네이터 커넥션을 참고한다.

##### 설명
지역 샤드 노드의 정보를 설정한다.
- 샤드 노드를 사용하기 위해서는 먼저 지역 샤드 노드의 정보를 등록해야한다. 
- 한번 샤딩 클러스터에 참여한 후에는, 지역 정보의 재 설정은 불가하며, 재설정을 위해서는 노드 제거 및 추가를 해야한다. 
- 한번도 샤딩 클러스터에 참여하지 않은 경우에만 변경가능하며, 변경은 최초 설정과 동일한 인터페이스를 통해 진행한다.
- 현재 ip address는 ip v4형식만 지원한다.

#### 예제
shard_node_id 가 1 이고, 'NODE1' 이름을 갖는 지역 샤드 노드의 정보를 등록한다. 
```
iSQL> EXEC DBMS_SHARD.SET_LOCAL_NODE(1, 'NODE1', '192.168.1.10', 20300, '192.168.1.11', 20300, '192.168.1.10', 30300 );
```

#### SET_REPLICATION
##### 구문
```
DBMS_SHARD.SET_REPLICATION(
  k_safety          in integer,
  replication_mode  in varchar(10) default NULL,
  parallel_count    in integer default NULL )
```

##### 파라미터
- k_safety: 시스템 내에서 유지할 복제본의 갯수
- replication_mode: 이중화에서 사용할 복제 방식
- parallel_count: 이중화 병렬 적용자의 수

##### 설명
샤딩 클러스터 시스템에서 사용할 복제 정보를 입력한다.

##### 예제
샤딩 클러스터 시스템에서 2개의 복제본을 유지하고 동기복제 방식을 사용하도록 설정한다.
```
iSQL> EXEC DBMS_SHARD.SET_REPLICATION(2,'consistent', 1);
```
#### SET_SHARD_TABLE_SHARDKEY
##### 구문
```
DBMS_SHARD.SET_SHARD_TABLE_SHARDKEY( 
  user_name                     in varchar(128),
  table_name                    in varchar(128),
  partiton_node_list            in varvchar(32000), 
  method_for_irregular          in char(1) default 'E' ,
  replication_parallel_count    in integer default 1 )
```

##### 파라미터
- user_name: 테이블 소유자의 이름
- table_name: 테이블 이름
- partiton_node_list: 파티션이름과 노드이름의 쌍들을 콤마로 구분한 리스트이며, 모든 파티션이름이 기술되어야 한다.
- method_for_irregular: 해당 테이블에 데이터가 기 존재 시 수행 옵션
  - E: (error) 기본 값으로 샤드 객체로 등록하려는 테이블에 분산정의에 맞지 않는 데이터가 존재하면 에러를 발생한다.
  - T: (truncate) 샤드 객체로 등록 하려는 테이블에 분산정의에 맞지 않는 데이터를 삭제 한다.
  - R: (remain) 샤드 객체로 등록 하려는 테이블에 분산정의에 맞지 않는 데이터가 존재해도 삭제하지 않고 그대로 둔다. 그렇지만, 분산정의에 맞지 않는 데이터는 이후에는 SQL에서 없는 데이터로 취급된다. 
- replication_parallel_count: 테이블과 백업 테이블 동기화 시 replication parallel count

##### 설명
샤드키 테이블 샤드객체로 등록한다.
- 전체 샤드 노드에 해당 테이블의 스키마와 인덱스 및 constraint는 동일해야 한다. 또한, view 테이블은 샤드 객체로 등록할 수 없다.
- 파티션 테이블만 등록될 수 있으며, 파티션키 컬럼은 PK 컬럼들중에 하나여야 하며, 파티션키 컬럼이 샤드키 컬럼으로 등록된다.
  - 파티션의 종류는 range with hash 와 range 그리고 list 세가지만 가능하다.
  - range with hash 파티션은 hash 분산으로 등록된다.
  - range 파티션은 range 분산으로 등록된다.
  - list 파티션은 list 분산으로 등록된다.
  - list 파티션 정의시 개별 파티션별로 list value는 하나씩만 가져야 한다.
- 본 프로시져 수행 시 백업 테이블은 재생성되고, 분산정의에 맞추어 원천테이블의 파티션별로 데이터가 백업 테이블의 파티션에 동기화 된다.

##### 예제
```
iSQL> EXEC DBMS_SHARD.SET_SHARD_TABLE_SHARDKEY('SYS','T1','P1 NODE1, P2 NODE2' );
iSQL> EXEC DBMS_SHARD.SET_SHARD_TABLE_SHARDKEY('SYS','T1','P1 NODE1, P2 NODE2', 'R', 5 );
```
#### SET_SHARD_TABLE_SOLO
##### 구문
```
DBMS_SHARD.SET_SHARD_TABLE_SOLO( 
  user_name                     in varchar(128),
  table_name                    in varchar(128),
  node_name                     in varchar(10),
  method_for_irregular          in char(1) default 'E' ,
  replication_parallel_count    in integer default 1 )
```

##### 파라미터
- user_name: 테이블 소유자의 이름
- table_name: 테이블 이름
- node_name: 솔로 테이블이 존재할 노드 이름
- method_for_irregular: 해당 테이블에 데이터가 기 존재 시 수행 옵션
  - E: (error) 기본 값으로 샤드 객체로 등록하려는 테이블에 분산정의에 맞지 않는 데이터가 존재하면 에러를 발생한다.
  - T: (truncate) 샤드 객체로 등록 하려는 테이블에 분산정의에 맞지 않는 데이터를 삭제 한다.
  - R: (remain) 샤드 객체로 등록 하려는 테이블에 분산정의에 맞지 않는 데이터가 존재해도 삭제하지 않고 그대로 둔다. 그렇지만, 분산정의에 맞지 않는 데이터는 이후에는 SQL에서 없는 데이터로 취급된다. 
- replication_parallel_count: 테이블과 백업 테이블 동기화 시 replication parallel count

##### 설명
솔로 테이블 샤드객체로 등록한다.
- 전체 샤드 노드에 해당 테이블의 스키마와 인덱스 및 constraint는 동일해야 한다. 또한, view 테이블은 샤드 객체로 등록할 수 없다.
- 본 프로시져 수행 시 백업 테이블은 재생성되고, 분산정의에 맞추어 원천테이블의 데이터가 백업 테이블에 동기화 된다.

##### 예제
```
iSQL> EXEC dbms_shard.set_shard_solo('sys','t2','node1');
iSQL> EXEC dbms_shard.set_shard_solo('sys','t2','node1', 'R',5);
```

#### SET_SHARD_TABLE_CLONE
##### 구문
```
DBMS_SHARD.SET_SHARD_TABLE_CLONE( 
  user_name                     in varchar(128),
  table_name                    in varchar(128),
  reference_node_name           in varchar(10) default NULL,
  replication_parallel_count    in integer default 1 )
```

##### 파라미터
- user_name: 테이블 소유자의 이름
- table_name: 테이블 이름
- reference_node_name: 최초 데이터 동기화의 기준이 되는 참조 노드 이름
- replication_parallel_count: 클론 테이블 최초 동기화 시 replication parallel count

##### 설명
클론 테이블 샤드객체로 등록한다.
- 전체 샤드 노드에 해당 테이블의 스키마와 인덱스 및 constraint는 동일해야 한다. 또한, view 테이블은 샤드 객체로 등록할 수 없다.
- reference_node_name이 설정 된 경우 전 노드의 해당 클론 테이블은 참조 노드의 테이블 데이터를 기준으로 동기화 된다.
- reference_node_name이 NULL인 경우는 전 노드의 해당 클론 테이블에 데이터가 존재하면 에러가 발생 한다.
- reference_node 이외의 노드의 데이터는 삭제 되고 에러가 발생해도 데이터가 원복되지는 않는다.

##### 예제
```
iSQL> EXEC dbms_shard.set_shard_table_clone('sys','t1','node1');
```

#### SET_SHARD_PROCEDURE_SHARDKEY

##### 구문
```
SET_SHARD_PROCEDURE_SHARDKEY(
  user_name in varchar(128),
  proc_name in varchar(128),
  split_method in varchar(1),
  key_param_name in varchar(128),
  value_node_list in varvchar(32000), 
  default_node_name in varchar(40) default NULL,
  proc_replace in char(1) default 'N')
```

##### 파라미터
- user_name: 프로시저 소유자의 이름
- proc_name: 프로시저 이름
- split_method: 분산 방식(H: 해시 분산 방식 R: 범위 분산 방식 L: 리스트 분산 방식)
- key_param_name: 샤드 키 파라미터 이름
- value_node_list: value와 node 이름의 쌍들을 콤마로 구분한 리스트
  - 해시분산 방식의 경우 지정 가능한 value 의 범위는 1 ~ 1000 사이의 정수이다.
- default_node_name: 기본 샤드 노드(범위가 지정되지 않은 샤드키 파라미터 값이 사용되면, 기본 샤드 노드의 프로시저가 호출된다.)
- proc_replace: 기존 분산정보 변경여부  ('Y': 변경, 'N': 에러발생)
  - Y: 기존에 동일이름의 샤드 프로시져가 있으면, 현재 등록하는 분산정보로 변경된다.
  - N: 기존에 동일이름의 샤드 프로시져가 있으면, 에러가 발생한다.

##### 설명
샤드키 프로시저 샤드객체로 등록한다.
- 전 노드의 해당 프로시저의 내용이 동일해야 한다.

##### 예제
```
iSQL> EXEC DBMS_SHARD.SET_SHARD_PROCEDURE_SHARDKEY( 'SYS', 'PROC1', 'L', 'KEY_PARAM','1 NODE1,2 NODE2, 3 NODE3');
iSQL> EXEC DBMS_SHARD.SET_SHARD_PROCEDURE_SHARDKEY( 'SYS', 'PROC1', 'L', 'KEY_PARAM','1 NODE1,2 NODE2, 3 NODE3', NULL ,'Y');
```

#### SET_SHARD_PROCEDURE_SOLO

##### 구문
```
SET_SHARD_PROCEDURE_SOLO(
  user_name in varchar(128),
  proc_name in varchar(128),
  node_name in varchar(10),
  proc_replace in char(1) default 'N')
```

##### 파라미터
- user_name: 프로시저 소유자의 이름
- proc_name: 프로시저 이름
- node_name: 솔로 프로시저가 호출될 노드의 이름
- proc_replace: 기존 분산정보 변경여부  ('Y': 변경, 'N': 에러발생)
  - Y: 기존에 동일이름의 샤드 프로시져가 있으면, 현재 등록하는 분산정보로 변경된다.
  - N: 기존에 동일이름의 샤드 프로시져가 있으면, 에러가 발생한다.

##### 설명
솔로 프로시저 샤드객체로 등록한다.
- 전 노드의 해당 프로시저의 내용이 동일해야 한다.

##### 예제
```
iSQL> EXEC DBMS_SHARD.SET_SHARD_PROCEDURE_SOLO( 'SYS', 'PROC1', 'NODE3');
iSQL> EXEC DBMS_SHARD.SET_SHARD_PROCEDURE_SOLO( 'SYS', 'PROC1', 'NODE3', 'Y');
```

#### SET_SHARD_PROCEDURE_CLONE

##### 구문
```
SET_SHARD_PROCEDURE_CLONE(
  user_name in varchar(128),
  proc_name in varchar(128),
  proc_replace in char(1) default 'N')
```

##### 파라미터
- user_name: 프로시저 소유자의 이름
- proc_name: 프로시저 이름
- proc_replace: 기존 분산정보 변경여부  ('Y': 변경, 'N': 에러발생)
  - Y: 기존에 동일이름의 샤드 프로시져가 있으면, 현재 등록하는 분산정보로 변경된다.
  - N: 기존에 동일이름의 샤드 프로시져가 있으면, 에러가 발생한다.

##### 설명
클론 프로시저 샤드객체로 등록한다.
- 전 노드의 해당 프로시저의 내용이 동일해야 한다.

##### 예제
```
iSQL> EXEC DBMS_SHARD.SET_SHARD_PROCEDURE_CLONE( 'SYS', 'PROC1');
iSQL> EXEC DBMS_SHARD.SET_SHARD_PROCEDURE_CLONE( 'SYS', 'PROC1', 'Y');
```

#### UNSET_SHARD_TABLE
##### 구문
```
DBMS_SHARD.UNSET_SHARD_TABLE(
  user_name  in varchar(128),
  table_name in varchar(128),
  drop_bak_tbl in char(1) default 'Y')
```

##### 파라미터
- user_name: 테이블 소유자의 이름
- table_name: 테이블 이름
- 백업 테이블 삭제 여부('Y': 삭제, 'N': 미삭제)

##### 설명
샤드 테이블을 해제한다.
- 샤드 테이블에 대한 분산정의만 해제되는 것이고, 테이블 자체가 삭제되는것은 아니다.

##### 예제
```
iSQL> EXEC dbms_shard.unset_shard_table('sys','t5');
iSQL> EXEC dbms_shard.unset_shard_table('sys','t5', 'N');
```

#### UNSET_SHARD_PROCEDURE
##### 구문
```
DBMS_SHARD.UNSET_SHARD_PROCEDURE(
  user_name in varchar(128),
  proc_name in varchar(128))
```

##### 파라미터
- user_name: 프로시저 소유자의 이름
- proc_name: 프로시저 이름

##### 설명
샤드 프로시저를 해제한다.
- 샤드 프로시저에 대한 분산정의만 해제되는 것이고, 프로시저 자체가 삭제되는것은 아니다.

##### 예제
```
iSQL> EXEC dbms_shard.unset_shard_procedure('sys','proc1');
```

## ShardCLI
```
SQLSetConnectAttr (
	SQLHDBC 	dbc,
	SQLINTEGER 	Attribute,
	SQLPOINTER	ValuePtr,
	SQLINTEGER 	StringLength );
```
다중 노드 트랜잭션으로 설정할 때에는 Attribute에는 ALTIBASE_GLOBAL_TRANSACTION_LEVEL을 ValuePtr에는 ALTIBASE_MULTIPLE_NODE_TRANSACTION을 입력한다. 

SQLSetConnectAttr에 대한 자세한 설명은 *CLI User's Manual > 2. Altibase CLI 함수*를 참조한다.

```
SQLSetConnectAttr(dbc, ALTIBASE_GLOBAL_TRANSACTION_LEVEL, (void*)ALTIBASE_MULTIPLE_NODE_TRANSACTION, 0);
```

## ShardJDBC

ShardJDBC는 연결속성의 형태로 지원한다.

```
DriverManager.getConnection("jdbc:sharding:Altibase://ip_address:port/mydb?shard_transaction_level=1");
```
