<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Altibase 8.1.0.0.1 Release Notes](#altibase-81001-release-notes)
  - [1. 시스템 요구사항](#1-%EC%8B%9C%EC%8A%A4%ED%85%9C-%EC%9A%94%EA%B5%AC%EC%82%AC%ED%95%AD)
    - [하드웨어 최저 사양](#%ED%95%98%EB%93%9C%EC%9B%A8%EC%96%B4-%EC%B5%9C%EC%A0%80-%EC%82%AC%EC%96%91)
    - [운영 체제 및 플랫폼](#%EC%9A%B4%EC%98%81-%EC%B2%B4%EC%A0%9C-%EB%B0%8F-%ED%94%8C%EB%9E%AB%ED%8F%BC)
  - [2. 릴리스 정보](#2-%EB%A6%B4%EB%A6%AC%EC%8A%A4-%EC%A0%95%EB%B3%B4)
    - [2.1 Altibase 8.1 의 새로운 기능](#21-altibase-81-%EC%9D%98-%EC%83%88%EB%A1%9C%EC%9A%B4-%EA%B8%B0%EB%8A%A5)
    - [2.2 변경 사항](#22-%EB%B3%80%EA%B2%BD-%EC%82%AC%ED%95%AD)
    - [2.3 패키지](#23-%ED%8C%A8%ED%82%A4%EC%A7%80)
    - [2.4 다운로드](#24-%EB%8B%A4%EC%9A%B4%EB%A1%9C%EB%93%9C)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

</br>

</br>

</br>

Altibase 8.1.0.0.1 Release Notes
===============================

**(2026.02)** </br>



## 1. 시스템 요구사항

### 하드웨어 최저 사양

* 1GB RAM (권장: 2GB)
* 1 CPU (권장: 2 CPUs)
* 4GB 하드 디스크 여유 공간 (권장: 12GB)



### 운영 체제 및 플랫폼

Altibase 8.1.0.0.1 는 아래 표에 나열된 운영체제와 플랫폼 상에서 운영 가능하다.


|                                                           | Altibase 서버 | Altibase 클라이언트 | 소프트웨어 요구사항     |
| --------------------------------------------------------- | :-----------: | :-----------------: | :---------------------- |
| **AIX on IBM Power Systems**                              |               |                     |                         |
| AIX 7.2                                                   |       ●       |          ●          |                         |
| **Linux x86-64**                                          |               |                     |                         |
| Red Hat Enterprise Linux 9                                |       ●       |          ●          | - GNU glibc 2.34        |
| Red Hat Enterprise Linux 7<br/>Red Hat Enterprise Linux 8 |       ●       |          ●          | - GNU glibc 2.12 ~ 2.33 |
| **Microsoft Windows (x64)**                               |               |                     |                         |
| Microsoft Windows 2008                                    |     **x**     |          ●          |                         |
| Microsoft Windows 10                                      |     **x**     |          ●          |                         |

> Altibase 서버/클라이언트 모두 64-bit 만 지원한다.<br>
> Red Hat Enterprise Linux 7, 8, 9 마이너 버전에 대해 호환성을 보장한다.
>
> Java 버전: JDK 1.8 이상에서 호환된다.

<br/><br/>

## 2. 릴리스 정보

### 2.1 Altibase 8.1 의 새로운 기능

#### 2.1.1 JSON 데이터 타입의 지원

Altibase 8.1부터 IETF의 RFC 8259 표준을 준수하는 Native JSON 데이터 타입을 지원한다. Altibase에서 지원하는 JSON 데이터 타입은 최대 2 GB 크기까지 저장할 수 있어, 대용량 JSON 데이터의 효율적인 처리를 지원한다. 또한, ISO/IEC 19075-6(2021) 표준을 따르는 JSON 경로 표현식을 지원하여, 표준 기반의 JSON 질의 및 데이터 추출이 가능하다. 그리고 JSON 데이터 처리를 위해 다음과 같은 주요 JSON 함수를 제공한다.

* JSON_ARRAY
* JSON_OBJECT
* JSON_EXISTS
* JSON_QUERY
* JSON_VALUE
* JSON_VALID

이를 통해 관계형 데이터와 JSON 데이터의 통합 처리 및 표준 기반 애플리케이션 개발이 가능하다.

#### 2.1.2 Temporary LOB 데이터 타입의 지원

대용량 텍스트 및 바이너리 데이터를 효율적으로 처리하기 위한 Temporary LOB 을 지원한다. Temporary LOB은 실행 시점(Execution)에 메모리 영역에 생성되는 임시 LOB으로, 특정 세션이나 트랜잭션내에서 존재한다. 해당 세션 또는 트랜잭션이 종료되면 자동으로 삭제된다. 알티베이스의 Temporary LOB은 세션 Temporary LOB과 트랜잭션 Temporary LOB 유형으로 구분되어 동작한다.

* 세션 Temporary LOB: PSM 내에서 **ASSOCIATIVE ARRAY, VARRAY, PACKAGE 변수**로 LOB을 사용하는 경우 세션 Temporary LOB으로 처리된다.
* 트랜잭션 Temporary LOB: 아래의 경우는 트랜잭션 Temporary LOB으로 처리된다.
  * `TO_CLOB`, `TO_BLOB` 함수 호출시
  * CLOB을 인자로 받는 `SUBSTR`, `CONCAT` 함수 처리시
  * PSM 내부에서 LOB 타입 변수를 처리할 때

현재 사용중인 Temporary LOB의 정보는 V$TEMPORARY_LOBS를 통해 조회할 수 있다.

#### 2.1.3 KADA (Key-optimized Altibase Document Access) API 제공

Altibase 8.1은 JSON 기반 Document 데이터를 보다 효율적으로 활용할 수 있도록 KADA(Key-optimized Altibase Document Access) API를 제공한다. KADA는 Key 기반 Document 접근을 지원하며, Java API와 REST API형태로 제공된다.

* KADA for Java API

  * NoSQL 방식의 CRUD 지원: SQL 질의문을 작성할 필요 없이, 고유 키(Key)를 이용하여 JSON 문서를 생성(Create), 조회(Read), 수정(Update), 삭제(Delete)할 수 있는 직관적인 API를 제공한다.

  * 유연한 애플리케이션 구현: MongoDB와 유사한 쿼리 연산자 및 문법을 지원

  * 수동 트랜잭션 제어 가능

  * 리소스 관리: AutoCloseable 인터페이스를 통해 안전한 리소스 해제

* KADA for REST API

  HTTP 기반으로 Altibase 데이터베이스의 JSON 문서를 관리할 수 있는 REST API를 제공한다.

  * JWT 인증 지원
  * 멀티테넌트 격리 지원
  * ACL 기반 컬렉션 공유 기능 제공

#### 2.1.4 Altibase 커넥터 제공(Source & Sink)

Altibase 8.1에서는 Altibase와 Apache Kafka 간의 실시간 데이터 연동 및 동기화를 위한 전용 커넥터를 제공한다. 이를 통해 지연 없는 실시간 데이터 파이프라인과 이벤트 기반 아키텍처를 손쉽게 구축할 수 있다.

* Altibase 소스 커넥터: Altibase의 변경 데이터를 감지하여 Kafka 토픽으로 전송한다.
* Altibase 싱크 커넥터: Kafka 토픽에 쌓인 메시지를 Altibase 테이블에 반영한다. 

#### 2.1.5 ABM(Altibase Backup Manager) 제공

abm은 Altibase 데이터베이스의 물리적 백업을 지원하는 유틸리티로, 백업 프로세스를 효율적으로 수행하고 백업 파일을 안전하게 관리하기 위해 제공한다. 직관적인 인터페이스를 통해 백업 수행부터 파일의 압축, 암호화 및 복호화 작업을 손쉽게 수행할 수 있다. 

#### 2.1.6 이중화 통신시 SSL/TLS 보안 프로토콜 지원

Altibase 8.1은 이중화(Replication) 통신에서 SSL/TLS 암호화 프로토콜을 지원한다. 이를 통해 이중화 통신시 데이터 전송을 암호화 하여 보안성을 강화 하였다.

이중화 생성 시 USING SSL 구문을 이용하여 SSL/TLS 통신을 설정할 수 있다. 또한 SSL 통신 설정을 위해 REPLICATION_SSL_PORT_NO 프로퍼티가 추가되었다.

#### 2.1.7 보안 강화를 위한 유틸리티 및 기능 추가

* altiEncrypt 제공

  altiEncrypt는 비밀번호 암호화를 수행하는 유틸리티이다. altiEncrypt를 사용하여 암호화된 비밀번호를 설정하면, 평문 비밀번호가 노출되는 것을 방지할 수 있다. altiEncrypt를 사용하여 암호화한 비밀번호는 aku, dblink, 어댑터의 conf 파일에서 사용할 수 있다.

* iSQL 비밀번호 파일 생성 기능 추가

  iSQL에서 사용자 비밀번호를 암호화된 비밀번호 파일로 생성하는 구문을 지원한다. 이렇게 생성된 비밀번호 파일은 iSQL 뿐만 아니라 aexport, iLoader, abm에서 -pf 옵션을 통해 로그인할 때 사용할 수 있다. 이를 통해 비밀번호의 평문 저장을 방지하고 보안성을 강화 할 수 있다.

#### 2.1.8 성능 개선

* **체크포인트 스케일 싱글 방식의 지원**

  메모리 데이터베이스 체크포인트 이미지 파일 관리 방식을 개선하기 위해, 체크포인트 스케일 싱글 방식을 지원한다. 체크포인트 스케일을 싱글 방식으로 설정하면, 메모리 테이블스페이스를 생성할 때 하나의 체크포인트 이미지 파일을 만들게 된다. 이후 체크포인트를 수행하면 내부적으로는 핑퐁 체크포인트 방식으로 동작하지만, 결과적으로 안정적인 체크포인트 이미지 파일 하나만 남게 된다. 이를 통해 디스크 사용량의 효율성을 높일 수 있다. (PROJ-2765)

* **서버 구동시 메모리 인덱스 빌드 과정의 성능 개선**

* **서버 종료 및 메모리 인덱스 삭제시 성능 개선**

* **로그 파일 준비 쓰레드(Log File Prepare Thread)의 성능 개선**

  * LOG_FILE_SIZE 의 기본값이 10MB에서 100MB로 변경되었습니다.
  * LOG_CREATE_METHOD 의 기본값 변경

* **LOB 대량 삽입 작업의 성능 개선** 

* **메모리 데이터베이스의 구동시 페이지 캐시 개선**

#### 2.1.9 외부 연동을 위한 지원 및 기능 개선

* **MindsDB Altibase Handler 공식 지원**

Altibase는 오픈소스 AI 데이터 플랫폼인 MindsDB와의 연동을 위해 Altibase Handler를 개발하였으며, MindsDB v24.5.4에 공식 반영 되었다. 이를 통해 MindsDB 환경에서 Altibase를 데이터 소스로 직접 연결하여 사용할 수 있으며, 머신러닝 모델 학습 및 예측 워크플로우에서 Altibase 데이터를 활용할 수 있다.

* **.NET 8 환경 지원**

Altibase ADO.NET 드라이버 및 Altibase EF(Entity Framework) Core가 .NET 8.0 환경에서 동작할 수 있도록 개선되었다.

* **Node.js 드라이버 제공(node-odbc-altibase)**

Node.js 환경에서 Altibase 서버에 접근할 수 있도록 node-odbc-altibase 드라이버를 제공한다. 이를 통해  자바스크립트 기반 애플리케이션과의 연동을 지원한다.

#### 2.1.11 ODBC 드라이버 개선

* **Updateable Dynaset 지원**

* **키 집합(KEY DRIVEN) 커서의 읽기 성능 개선**

  SQL_CURSOR_KEYSET_DRIVEN 커서로 select를 수행할 때, 서버-클라이언트간 통신 횟수(fetch 프로토콜)를 줄여 성능을 개선했습니다.

#### 2.1.12 AKU(Altibase Kubernetes Utility)의 기능 개선

* 최대 6개 노드까지의 스케일 업 지원
* 다중 이중화 지원 : aku.conf 파일에서 REPLICATIONS 설정에서 쉼표로 구분하여 다중 이중화를 설정 할 수 있다.  자세한 내용은  aku 매뉴얼을 참고 한다.
* 멀티 쓰레드 기반 병렬 처리로 성능 개선
* 이중화 대상 테이블의 이름 및 사용자 이름의 길이 제한이 기존 40자에서 최대 128자로 변경되었다.

#### 2.1.13 태국어 캐릭터셋 지원

태국어 캐릭터셋을 공식 지원한다. UTF8 환경에서 ISO/IEC 14651 표준 기반의 태국어 정렬을 지원하여, 태국어 데이터의 정확하고 일관된 처리가 가능하다. 이를 통해 현지화 서비스 및 글로벌 환경에서의 데이터 신뢰성을 강화하였다. 

* 태국어 정렬 기능을 이용하려면 NLS_COMP=1로 설정해야 하며, 해당 프로퍼티는 데이터베이스 생성 시 지정해야 한다.

#### 2.1.14 기타 기능 개선

* **테이블 통계 잠금 기능 지원**

  테이블의 통계를 잠그거나 잠금을 해제하기 위해 DBMS_STATS 패키지에 LOCK_TABLE_STATS, UNLOCK_TABLE_STATS 프로시저가 추가되었다.

* **JSON 형식의 실행 계획(PLAN)을 지원**

  실행 계획을 JSON 형식으로 출력하는 기능을 지원한다. 이 기능을 통해 실행 계획의 구조화된 정보를 JSON 객체로 생성할 수 있으며, 외부 도구와의 연동, 시각화 및 성능 분석 작업을 보다 효율적으로 수행할 수 있다.

* **JDBC 에서 Statement Caching 기능 지원**

  JDBC 드라이버에서 PreparedStatement 및 CallableStatement에 대한 Statement Caching을 지원한다. 이를 통해 동일 SQL의 반복 실행 시 성능을 향상할 수 있다. 해당 기능은 연결 속성 `stmt_cache_enable` 설정을 통해 활성화할 수 있으며, 기존 애플리케이션 코드 수정 없이 적용 가능하다.
  
* **이증화 META LOGGING 기능 확대**

  기존에는 JDBC Adapter와 OraAdapter에서만 사용가능하던 META LOGGING 옵션이, 이제 일반 이중화에서도 사용하도록 개선되었습니다.

</br>



### 2.2 변경 사항

DBA와 개발자가 알아야 할 추가, 변경, 제거된 기능을 아래에서 설명한다.

#### 2.2.1 데이터베이스 버전

데이터베이스 구성 요소 별 버전

| Altibase 버전 | 데이터베이스 바이너리 버전 | 메타 버전 | 통신 프로토콜 버전 | 이중화 프로토콜 버전 |
| :-----------: | :------------------------: | :-------: | :----------------: | :------------------: |
|   8.1.0.0.1   |           8.1.0            |  10.1.1   |       7.1.9        |        7.4.9         |
|   7.3.0.1.2   |           7.3.0            |   9.4.1   |       7.1.8        |        7.4.9         |
|   7.3.0.0.1   |           7.3.0            |   9.3.1   |       7.1.8        |        7.4.9         |

#### 2.2.2 호환성

##### 데이터베이스 바이너리 버전

데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그 파일의 호환성을 나타낸다.

로그 파일 로깅 구조 개선으로 데이터베이스 바이너리 버전이 변경되었다. **Altibase 8.1 이전 버전 데이터베이스와 호환되지 않으므로 Altibase 버전 업그레이드 시 마이그레이션 작업이 필요하다.**

##### 메타 버전

메타 메이저 버전(META MAJOR VERSION)이 변경되었으므로, **Altibase 8.1 이전 버전에서 Altibase 8.1로 업그레이드시 메타를 재구성해야 한다.**

##### 통신 프로토콜 버전

Altibase 서버와 클라이언트 간 통신 규약 호환성을 의미하며 클라이언트 하위 호환성을 알 수 있다.

통신 프로토콜 버전 중 상위 두 자리는 같고 패치 버전이 변경되었다. 메이저 버전과 마이너 버전이 같으면 클라이언트 하위 호환성을 보장한다.

> 클라이언트 하위 호환성은 하위 버전 Altibase 라이브러리로 컴파일한 사용자 응용 프로그램(Altibase 클라이언트)이 상위 버전 Altibase 에서 정상 동작하는 것을 보장한다.

##### 이중화 프로토콜 버전

이중화 프로토콜 버전은 Altibase 이중화 하위 호환성이나 이중화 부가기능 호환 여부를 나타낸다.

메이저 버전과 마이너 버전 변경이 없어 LAZY 모드 이중화는 Altibase 이중화 하위 호환성을 보장하지만 패치 버전 변경으로 이중화 부가기능은 호환되지 않는다.

> ###### Altibase 이중화 하위 호환성
>
> Altibase 이중화 하위 호환성이란 이중화 프로토콜 버전이 낮은 버전에서 높은 버전으로 단방향 이중화가 가능함을 의미하며 이중화 프로토콜 버전에서 상위 두 자리(메이저와 마이너 버전)가 같은 경우 보장한다.
> Altibase 이중화 하위 호환성은 LAZY 모드 이중화로 제한한다.
>
> EAGER 모드 이중화는 하위 호환성을 보장하지 않는다.
> 오프라인 이중화를 포함한 이중화 부가기능은 하위 호환성을 보장하지 않는다.
>
> DDL 복제는 이중화 프로토콜 버전 세 자리가 모두 일치할 경우, 하위 호환성을 보장한다.

</br>

#### 2.2.3 기타 변경사항

##### iLoader API 빌드 환경 변경(신규 라이브러리 추가)

iLoader API를 사용하는 응용 프로그램에서 암호화된 비밀번호 파일로 로그인하는 기능을 사용하려면, iLoader API 컴파일 시 신규 라이브러리인 `libaltiutil.a`를 추가해서 컴파일 해야 한다. 

##### aexport 프로퍼티 변경사항

| 프로퍼티 이름      | 변경 전 | 변경 후 |
| ------------------ | ------- | ------- |
| ILOADER_FIELD_TERM | ^       | ^C_c^   |
| ILOADER_ROW_TERM   | %n      | ^R_r^%n |

##### Altibase 저장 패키지 변경사항

DBMS_METADATA 패키지를 업데이트 해야 한다.

#### 2.2.4 Altibase 서버 프로퍼티

Altibase 8.1.0.0.1 에서 추가, 변경, 삭제된 Altibase 서버 프로퍼티들이다. 각 프로퍼티에 대한 자세한 내용은 [General Reference-1.Data Types & Altibase Properties](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md)를 참고하기 바란다.

##### 새로운 프로퍼티

-   CHECKPOINT_SCALE_SINGLE_DW_BUFFER_SIZE
-   MEMORY_TEMPLOB_MAX_ALLOC_SIZE
-   MEMORY_TEMPLOB_PIECE_SIZE
-   REPLICATION_SSL_PORT_NO
-   PSM_CASE_SENSITIVE_MODE
-   TEMPORARY_LOB_ENABLE
-   TRCLOG_EXPLAIN_TYPE
-   TRCLOG_JSON_PLAN_INDENT_DEPTH

##### 변경된 프로퍼티

- CHECKPOINT_INTERVAL_IN_LOG
  - 기본값이 100 에서 10으로 변경되었다.

- FAST_START_LOGFILE_TARGET
  - 기본값이 100에서 10으로 변경되었다.

- LOG_CREATE_METHOD
  - 기본값이 0에서 1로 변경되었다.

- LOG_FILE_SIZE
  - 기본값이 10485760 에서 104857600으로 변경되었다.
  - 최대값이 18446744073709551615에서 4294967295으로 변경되었다.

- MEMORY_INDEX_BUILD_RUN_SIZE
  - 최대값이 18446744073709551615에서 4294967295으로 변경되었다.

- MEMORY_INDEX_BUILD_VALUE_LENGTH_THRESHOLD
  - 최대값이 18446744073709551615에서 4294967295으로 변경되었다.

- OPTIMIZER_FEATURE_ENABLE
  - 기본값이 7.3.0.0.1에서 8.1.0.0.1로 변경되었다.

##### 삭제된 프로퍼티

-   INSPECTION_LARGE_HEAP_THRESHOLD



#### 2.2.5 메타 테이블

추가/삭제/변경된 메타테이블 없음

#### 2.2.6 성능 뷰

아래의 성능 뷰 들이 추가되었다. 각 성능 뷰에 대한 자세한 내용은 [**General Reference-2.The Data Dictionary**](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-2.The%20Data%20Dictionary.md)를 참고하기 바란다.

##### 새로운 성능 뷰

-   V$LOCK_TABLE_STATS
-   V$MEM_STABLE
-   V$TEMPORARY_LOBS

</br>

### 2.3 패키지

| OS    | CPU     | 서버/클라이언트     | 패키지 인스톨러 이름                                     |
| ----- | ------- | ------------------- | -------------------------------------------------------- |
| AIX   | PowerPC | Altibase 서버       | altibase- server-8.1.0.0.1-AIX-POWERPC-64bit-release.run |
|       |         | Altibase 클라이언트 | altibase- client-8.1.0.0.1-AIX-POWERPC-64bit-release.run |
| LINUX | x86-64  | Altibase 서버       | altibase-server-8.1.0.0.1-LINUX-X86-64bit-release.run    |
|       |         | Altibase 클라이언트 | altibase-client-8.1.0.0.1-LINUX-X86-64bit-release.run    |

</br>

### 2.4 다운로드

#### Package

http://support.altibase.com

#### Manual

https://manual.altibase.com/8.1/

