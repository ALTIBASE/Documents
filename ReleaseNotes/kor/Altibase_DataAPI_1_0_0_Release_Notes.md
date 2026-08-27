

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Altibase Data API 1.0.0 Release Notes](#altibase-data-api-100-release-notes)
  - [1. 개요](#1-%EA%B0%9C%EC%9A%94)
  - [2. 주요 특징](#2-%EC%A3%BC%EC%9A%94-%ED%8A%B9%EC%A7%95)
    - [JWT Bearer 인증 및 Basic 인증 지원](#jwt-bearer-%EC%9D%B8%EC%A6%9D-%EB%B0%8F-basic-%EC%9D%B8%EC%A6%9D-%EC%A7%80%EC%9B%90)
    - [주요 HTTP 엔드포인트 제공](#%EC%A3%BC%EC%9A%94-http-%EC%97%94%EB%93%9C%ED%8F%AC%EC%9D%B8%ED%8A%B8-%EC%A0%9C%EA%B3%B5)
    - [JSON 기반 요청 및 응답](#json-%EA%B8%B0%EB%B0%98-%EC%9A%94%EC%B2%AD-%EB%B0%8F-%EC%9D%91%EB%8B%B5)
    - [NDJSON 스트리밍 지원](#ndjson-%EC%8A%A4%ED%8A%B8%EB%A6%AC%EB%B0%8D-%EC%A7%80%EC%9B%90)
    - [동적 사용자별 커넥션 풀 관리](#%EB%8F%99%EC%A0%81-%EC%82%AC%EC%9A%A9%EC%9E%90%EB%B3%84-%EC%BB%A4%EB%84%A5%EC%85%98-%ED%92%80-%EA%B4%80%EB%A6%AC)
    - [운영 및 모니터링 지원](#%EC%9A%B4%EC%98%81-%EB%B0%8F-%EB%AA%A8%EB%8B%88%ED%84%B0%EB%A7%81-%EC%A7%80%EC%9B%90)
  - [3. 호환성](#3-%ED%98%B8%ED%99%98%EC%84%B1)
  - [4. 다운로드](#4-%EB%8B%A4%EC%9A%B4%EB%A1%9C%EB%93%9C)
    - [패키지](#%ED%8C%A8%ED%82%A4%EC%A7%80)
    - [도커 이미지](#%EB%8F%84%EC%BB%A4-%EC%9D%B4%EB%AF%B8%EC%A7%80)
    - [매뉴얼](#%EB%A7%A4%EB%89%B4%EC%96%BC)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

<br/>

<br/>

<br/>

Altibase Data API 1.0.0 Release Notes
===============================

**(July 1, 2026)**

## 1. 개요

Altibase Data API는 Altibase SQL 실행 및 조회 기능을 HTTP API로 제공하는 Spring Boot 기반 서비스입니다. 클라이언트는 DB 사용자 인증 또는 JWT 토큰 기반 인증을 통해 SQL 조회, DML/DDL 실행, 대량 데이터 조회를 위한 스트리밍 기능을 사용할 수 있으며, Data API의 커넥션 풀 상태와 메트릭 정보를 조회할 수 있는 모니터링 API를 제공합니다.

## 2. 주요 특징

### JWT Bearer 인증 및 Basic 인증 지원

JWT Bearer 인증은 토큰 기반 세션 유지와 인증 흐름 제어를 지원하며, Basic 인증은 별도 토큰 관리 없이 매 요청마다 자격증명을 검증하여 스크립트·배치·모니터링 환경에 적합합니다.

### 주요 HTTP 엔드포인트 제공

SQL 실행, 결과 조회, 대용량 스트리밍, 인증 및 세션 관리에 필요한 엔드포인트를 제공합니다. 자세한 목록은 [**엔드포인트 요약**]([부록 A. 엔드포인트 요약 - Altibase 8.1 매뉴얼](https://manual.altibase.com/8.1/dev/data-api/Appendix-A.-API-Reference/))을 참조합니다.

### JSON 기반 요청 및 응답

요청은 SQL 텍스트와 바인드 값을 포함한 JSON 형식으로 전달되며, 조회 결과는 JSON 형식으로 반환됩니다.

### NDJSON 스트리밍 지원

대량 조회 결과를 NDJSON(Newline Delimited JSON) 형식으로 순차 전송할 수 있으며, 지연 실행 기반 스트리밍을 통해 메모리 사용량을 최소화합니다.

### 동적 사용자별 커넥션 풀 관리

사용자별 커넥션 풀을 생성 및 재사용하고, 세션 종료 시 안전하게 정리하여 리소스를 효율적으로 관리합니다.

### 운영 및 모니터링 지원

커넥션 풀 상태와 메트릭 정보를 조회할 수 있으며, Prometheus 수집용 메트릭을 제공합니다.



## 3. 호환성

- Java 17 이상에서 호환됩니다.
-  Altibase 7.1.0.5.6 이상에서 사용할 수 있습니다. (단, 패키지별로 지원하는 Altibase버전이 다릅니다.)
    - `data-api-1.0.0-altibase8.jar`: Altibase 8.x or later
    - `data-api-1.0.0-altibase7.jar`: Altibase 7.1.0.5.6 to 7.3.x.x.x



## 4. 다운로드

### 패키지

Data API 패키지는 아래의 파일로 제공되며, http://support.altibase.com/kr/product 에서 다운로드 받을 수 있습니다.

* data-api-1.0.0-altibase8.jar
* data-api-1.0.0-altibase7.jar

### 도커 이미지

Data API Docker 이미지는 다음 태그로 제공됩니다.

| 도커 태그                         | 지원하는 Altibase 버전           |
| --------------------------------- | -------------------------------- |
| altibase/data-api:1.0.0           | Altibase 8.x or later            |
| altibase/data-api:latest          | Altibase 8.x or later            |
| altibase/data-api:1.0.0-altibase7 | Altibase 7.1.0.5.6  to 7.3.x.x.x |

### 매뉴얼

- [Data API Manual - Altibase 8.1 매뉴얼](https://manual.altibase.com/8.1/dev/data-api/copyright/)
