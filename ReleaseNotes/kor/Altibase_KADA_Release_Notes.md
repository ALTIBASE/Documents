

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

<br/>

Altibase KADA Release Notes
===============================

또는 Altibase KADA Release History 라는 제목이 어떠한지요?



## Version 1.0.3 (2026-07-01)

### Downloads

**Binary Package (ZIP)**

* [document-access-java-1.0.3-ALL.zip](http://ux-jenkins.altibase.local:8080/job/KADA_1.0.3/lastSuccessfulBuild/artifact/document-access-java/build/distributions/document-access-java-1.0.3-ALL.zip)
* [document-access-rest-1.0.3-ALL.zip](http://ux-jenkins.altibase.local:8080/job/KADA_1.0.3/lastSuccessfulBuild/artifact/document-access-rest/build/distributions/document-access-rest-1.0.3-ALL.zip)

**Docker Image (TAR)**

* [document-access-rest-1.0.3.tar](http://ux-jenkins.altibase.local:8080/job/KADA_1.0.3/lastSuccessfulBuild/artifact/build/docker/document-access-rest-1.0.3.tar)

### KADA REST API

#### Bug Fixes

##### BUG-52369 삭제된 공유 컬렉션 조회 시 잘못된 오류 응답 반환 문제 수정

삭제된 공유 컬렉션을 조회할때 권한 오류(`403 Forbidden`)가 반환되는 문제를 수정하였습니다. 이제 `404 Not Found` 가 반환됩니다.

##### BUG-52371 OpenAPI 및 Swagger UI의 버전 정보 표시 오류 수정

OpenAPI 문서와 Swagger UI 에 표시되는 버전 정보가 실제 설치된 KADA REST API버전과 일치하지 않는 문제를 수정하였습니다. 이제 설치된 버전에 맞는 버전 정보가 표시됩니다.

### KADA JAVA API

변경 사항 없음.

<br/>

## Version 1.0.2 (2026-07-01)

### Downloads

**Binary Package (ZIP)**

* 

**Docker Image (TAR)**

* 

### KADA REST API

#### Bug Fixes

##### BUG-52276 보안 취약점 및 데이터 무결성 강화

JSON 쿼리 처리, API Key 인증, 테넌트 격리 및 문서 갱신 처리에서 확인된 여러 보안 취약점과 데이터 무결성 문제를 수정하였습니다. 이를 통해 인증 및 권한 검증을 강화하고 데이터 접근 제어의 안정성을 개선하였습니다.

##### BUG-52274 공유 컬렉션의 SHARED 권한 적용 오류 수정

`SHARED` 권한만 가진 토큰으로 공유 컬렉션의 생성, 메타데이터 조회, 문서 삽입 및 삭제 요청을 수행할 때 `403 Forbidden`이 반환되는 문제를 수정하였습니다.

### KADA JAVA API

변경 사항 없음.

<br/>

## Version 1.0.1 (2026-07-01)

### Downloads

**Binary Package (ZIP)**

* 

**Docker Image (TAR)**

* 

### KADA REST API

#### Bug Fixes

##### BUG-52258 Document 검색 API에서  `totalCount` 및 `hasMore` 반환 오류 수정

Document 검색 API에서 `totalCount`와 `hasMore` 값이 올바르게 계산되지 않아 페이징 정보가 잘못 반환되는 문제를 수정하였습니다.

### KADA JAVA API

변경 사항 없음.
