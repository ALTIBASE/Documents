<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Altibase Windows 2026 Release Notes](#altibase-windows-2026-release-notes)
  - [1. 시스템 요구사항](#1-%EC%8B%9C%EC%8A%A4%ED%85%9C-%EC%9A%94%EA%B5%AC%EC%82%AC%ED%95%AD)
    - [하드웨어 최저 사양](#%ED%95%98%EB%93%9C%EC%9B%A8%EC%96%B4-%EC%B5%9C%EC%A0%80-%EC%82%AC%EC%96%91)
    - [운영 체제 및 플랫폼](#%EC%9A%B4%EC%98%81-%EC%B2%B4%EC%A0%9C-%EB%B0%8F-%ED%94%8C%EB%9E%AB%ED%8F%BC)
  - [2. 릴리스 정보](#2-%EB%A6%B4%EB%A6%AC%EC%8A%A4-%EC%A0%95%EB%B3%B4)
    - [2.1 Altibase Windows 2026 의 새로운 기능](#21-altibase-windows-2026-%EC%9D%98-%EC%83%88%EB%A1%9C%EC%9A%B4-%EA%B8%B0%EB%8A%A5)
    - [2.2 버전 및 호환성](#22-%EB%B2%84%EC%A0%84-%EB%B0%8F-%ED%98%B8%ED%99%98%EC%84%B1)
    - [2.3 패키지](#23-%ED%8C%A8%ED%82%A4%EC%A7%80)
    - [2.4 다운로드](#24-%EB%8B%A4%EC%9A%B4%EB%A1%9C%EB%93%9C)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

</br>

</br>

</br>

Altibase Windows 2026 Release Notes
===============================

**(2025.11)** </br>



## 1. 시스템 요구사항

### 하드웨어 최소 사양

* 1GB RAM (권장: 2GB)
* 1 CPU (권장: 2 CPUs)
* 4GB 하드 디스크 여유 공간 (권장: 12GB)



### 운영 체제 및 플랫폼

Altibase Windows 2026은 아래에 나열된 운영체제와 플랫폼 상에서 운영 가능하다.

* Microsoft Windows Server 2025
* Microsoft Windows Server 2022
* Microsoft Windows11

> Altibase 서버/클라이언트 모두 64-bit 만 지원한다.<br>
> Java 버전: JDK 1.5 이상에서 호환된다.

<br/><br/>

## 2. 릴리스 정보

### 2.1 Altibase Windows 2026 의 새로운 기능

Altibase Windows 2026은 임베디드 환경에서 서버-클라이언트 간 통합운영을 지원하며, 데이터 처리, 저장, 동기화의 효율적인 운영을 지원한다.

* 임베디드 장비와 Altibase 하이브리드 DBMS 통합 지원
* 온라인 오프라인 동기화 지원으로 서버와 항상 연결되지 않아도 로컬 처리 후 서버 연결시 자동 동기화 기능을 지원한다.
* 또한 수천대이상의 장비간 이중화 및 데이터 복제를 지원한다.

</br>

### 2.2 버전 및 호환성

#### 2.2.1 데이터베이스 버전

데이터베이스 구성 요소 별 버전

| Altibase 버전 | 데이터베이스 바이너리 버전 | 메타 버전 | 통신 프로토콜 버전 | 이중화 프로토콜 버전 |
| :-----------: | :------------------------: | :-------: | :----------------: | :------------------: |
|   2.6.0.0.1   |           2.6.0            |   2.1.1   |       7.1.3        |        7.4.5         |

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

</br>

### 2.3 패키지

* AltibaseWindows2026-server-2.6.0.0.1-WINDOWS-X86-64bit-release.exe
* AltibaseWindows2026-client-2.6.0.0.1-WINDOWS-X86-64bit-release.exe

</br>

### 2.4 다운로드

#### Package

http://support.altibase.com

#### Manual

http://support.altibase.com/kr/manual
