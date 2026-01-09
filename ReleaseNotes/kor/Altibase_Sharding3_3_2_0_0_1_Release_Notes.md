<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Altibase Sharding 3 Release Notes](#altibase-sharding-3-release-notes)
  - [1. 시스템 요구사항](#1-%EC%8B%9C%EC%8A%A4%ED%85%9C-%EC%9A%94%EA%B5%AC%EC%82%AC%ED%95%AD)
    - [하드웨어 최소 사양](#%ED%95%98%EB%93%9C%EC%9B%A8%EC%96%B4-%EC%B5%9C%EC%86%8C-%EC%82%AC%EC%96%91)
    - [운영 체제 및 플랫폼](#%EC%9A%B4%EC%98%81-%EC%B2%B4%EC%A0%9C-%EB%B0%8F-%ED%94%8C%EB%9E%AB%ED%8F%BC)
  - [2. 릴리스 정보](#2-%EB%A6%B4%EB%A6%AC%EC%8A%A4-%EC%A0%95%EB%B3%B4)
    - [2.1 Altibase Sharding 3 의 새로운 기능](#21-altibase-sharding-3-%EC%9D%98-%EC%83%88%EB%A1%9C%EC%9A%B4-%EA%B8%B0%EB%8A%A5)
    - [2.2 버전 및 호환성](#22-%EB%B2%84%EC%A0%84-%EB%B0%8F-%ED%98%B8%ED%99%98%EC%84%B1)
    - [2.3 패키지](#23-%ED%8C%A8%ED%82%A4%EC%A7%80)
    - [2.4 다운로드](#24-%EB%8B%A4%EC%9A%B4%EB%A1%9C%EB%93%9C)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

</br>

</br>

</br>

Altibase Sharding 3 Release Notes
===============================

**(2026.02)** </br>



## 1. 시스템 요구사항

### 하드웨어 최소 사양

* 1GB RAM (권장: 2GB)
* 1 CPU (권장: 2 CPUs)
* 4GB 하드 디스크 여유 공간 (권장: 12GB)



### 운영 체제 및 플랫폼

Altibase Sharding 3은 아래에 나열된 운영체제와 플랫폼 상에서 운영 가능하다.

| **Linux x86-64**                                             | Altibase 서버 | Altibase 클라이언트 | 소프트웨어 요구사항       |
| ------------------------------------------------------------ | ------------- | ------------------- | ------------------------- |
| Red Hat Enterprise Linux 6<br/> Red Hat Enterprise Linux 7<br/> Red Hat Enterprise Linux 8 | ●             | ●                   | *- GNU glibc 2.12 ~ 2.33* |
| Red Hat Enterprise Linux 9                                   | ●             | ●                   | *- GNU glibc 2.34*        |

> Altibase 서버/클라이언트 모두 64-bit 만 지원한다.<br>
> Java 버전: JDK 1.5 이상에서 호환된다.

<br/><br/>

## 2. 릴리스 정보

### 2.1 Altibase Sharding 3 의 새로운 기능

Altibase Sharding 3는 대용량 데이터베이스 환경에서 분산 처리를 효율적으로 수행할 수 있도록 설계된 **하이브리드 샤딩** 시스템이다. 기존 SQL을 분석하여 클라이언트 측 샤딩과 서버 측 샤딩 중 최적의 실행 경로를 자동으로 결정함으로써, 쿼리 처리 성능을 최적화 한다.

또한, 다양한 분산 방식, 분산 객체, 관련 유틸리티를 제공하여 유연한 샤딩 구성을 지원한다.

기존 SQL을 수정하지 않고, 샤드 전용 라이브러리 교체만으로 Altibase Sharding을 손쉽게 적용할 수 있다. 뿐만 아니라 기존 응용 프로그램을 전혀 수정하지 않은 상태에서도 서버측 샤딩을 적용할 수  있다. 

#### 주요 특징

* 지능적인 클라이언트 측 샤딩
* 쉬운 SQL 작성 및 샤드 키워드(SHARD) 제공
* 쉬운 샤드 설정
* No SPOF(No Single Point Of Failure)
* 쿼리 최적화를 위한 샤드 쿼리 분석기(Shard Query Analyzer), 샤드 쿼리 최적화기(Shard Query Optimizer), 샤드 쿼리 실행기(Shard Query Executor) 내장
* 다양한 샤드 쿼리 및 함수 지원
* 다양한 분산 객체 지원
* 다양한 분산 방식 지원
* shardLoader를 통한 쉬운 마이그레이션 지원
* 데이터 재구축(Rebuild) 및 리샤딩(Resharding)을 통한 분산 데이터 이동 지원

</br>

### 2.2 버전 및 호환성

#### 2.2.1 데이터베이스 버전

데이터베이스 구성 요소 별 버전

| Altibase 버전 | 데이터베이스 바이너리 버전 | 메타 버전 | 통신 프로토콜 버전 | 이중화 프로토콜 버전 | 샤드 버전 |
| :-----------: | :------------------------: | :-------: | :----------------: | :------------------: | --------- |
|   3.2.0.0.1   |           6.5.1            |   3.1.1   |       7.1.7        |        7.4.7         | 3.2.1     |

#### 2.2.2 호환성

##### 데이터베이스 바이너리 버전

데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그 파일의 호환성을 나타낸다.

##### 메타 버전

메타 테이블의 호환성을 의미한다.

##### 통신 프로토콜 버전

Altibase 서버와 클라이언트 간 통신 규약 호환성을 의미하며 클라이언트 하위 호환성을 알 수 있다.

##### 이중화 프로토콜 버전

이중화 프로토콜 버전은 Altibase 이중화 하위 호환성이나 이중화 부가기능 호환 여부를 나타낸다.

> ###### Altibase 이중화 하위 호환성
>
> Altibase 이중화 하위 호환성이란 이중화 프로토콜 버전이 낮은 버전에서 높은 버전으로 단방향 이중화가 가능함을 의미하며 이중화 프로토콜 버전에서 상위 두 자리(메이저와 마이너 버전)가 같은 경우 보장한다.
> Altibase 이중화 하위 호환성은 LAZY 모드 이중화로 제한한다.
>
> EAGER 모드 이중화는 하위 호환성을 보장하지 않는다.
> DDL 복제는 이중화 프로토콜 버전 세 자리가 모두 일치해야하므로 하위 호환성을 보장하지 않는다.
> 오프라인 이중화를 포함한 이중화 부가기능은 하위 호환성을 보장하지 않는다.

##### 샤드 버전

샤드 버전은 하위 호환성을 보장하지 않는다.

</br>

### 2.3 패키지

* AltibaseSharding-server-3.2.0.0.1-LINUX-X86-64bit-release.run
* AltibaseSharding-client-3.2.0.0.1-LINUX-X86-64bit-release.run

</br>

### 2.4 다운로드

#### Package

http://support.altibase.com

#### Manual

http://manual.altibase.com/as3
