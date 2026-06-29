

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Altibase KADA 1.0.3 Release Notes](#altibase-kada-103-release-notes)
  - [1. 신규 기능 및 변경 사항](#1-%EC%8B%A0%EA%B7%9C-%EA%B8%B0%EB%8A%A5-%EB%B0%8F-%EB%B3%80%EA%B2%BD-%EC%82%AC%ED%95%AD)
    - [KADA REST API](#kada-rest-api)
    - [KADA JAVA API](#kada-java-api)
  - [2. 다운로드](#2-%EB%8B%A4%EC%9A%B4%EB%A1%9C%EB%93%9C)
    - [패키지](#%ED%8C%A8%ED%82%A4%EC%A7%80)
    - [매뉴얼](#%EB%A7%A4%EB%89%B4%EC%96%BC)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

<br/>

<br/>

<br/>

Altibase KADA 1.0.3 Release Notes
===============================

**(July 1, 2026)**

## 1. 신규 기능 및 변경 사항

### KADA REST API

#### Bug Fixes

##### BUG-52369 삭제된 공유 컬렉션 조회 시 잘못된 오류 응답 반환 문제 수정

삭제된 공유 컬렉션을 조회할때 권한 오류(`403 Forbidden`)가 반환되는 문제를 수정하였습니다. 이제 `404 Not Found` 가 반환됩니다.

##### BUG-52371 OpenAPI 및 Swagger UI의 버전 정보 표시 오류 수정

OpenAPI 문서와 Swagger UI 에 표시되는 버전 정보가 실제 설치된 KADA REST API버전과 일치하지 않는 문제를 수정하였습니다. 이제 설치된 버전에 맞는 버전 정보가 표시됩니다.

### KADA JAVA API

변경 사항 없음.

## 2. 다운로드

### 패키지 (ZIP)

* [document-access-java-1.0.3-ALL.zip](http://ux-jenkins.altibase.local:8080/job/KADA_1.0.3/lastSuccessfulBuild/artifact/document-access-java/build/distributions/document-access-java-1.0.3-ALL.zip)
* [document-access-rest-1.0.3-ALL.zip](http://ux-jenkins.altibase.local:8080/job/KADA_1.0.3/lastSuccessfulBuild/artifact/document-access-rest/build/distributions/document-access-rest-1.0.3-ALL.zip)

### 도커 이미지 (TAR)

* [document-access-rest-1.0.3.tar](http://ux-jenkins.altibase.local:8080/job/KADA_1.0.3/lastSuccessfulBuild/artifact/build/docker/document-access-rest-1.0.3.tar)

### 매뉴얼

- [KADA for Java User's Manual - Altibase 8.1 매뉴얼](https://manual.altibase.com/8.1/dev/kada-java/copyright/)
- [KADA for REST API Manual - Altibase 8.1 매뉴얼](https://manual.altibase.com/8.1/dev/kada-rest/copyright/)
