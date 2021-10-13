<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Altibase 7.2.0.0.0 Release Notes](#altibase-72000-release-notes)
  - [시스템 요구사항](#%EC%8B%9C%EC%8A%A4%ED%85%9C-%EC%9A%94%EA%B5%AC%EC%82%AC%ED%95%AD)
    - [하드웨어 최저 사양](#%ED%95%98%EB%93%9C%EC%9B%A8%EC%96%B4-%EC%B5%9C%EC%A0%80-%EC%82%AC%EC%96%91)
    - [운영 체제 및 플랫폼](#%EC%9A%B4%EC%98%81-%EC%B2%B4%EC%A0%9C-%EB%B0%8F-%ED%94%8C%EB%9E%AB%ED%8F%BC)
  - [릴리스 정보](#%EB%A6%B4%EB%A6%AC%EC%8A%A4-%EC%A0%95%EB%B3%B4)
    - [새로운 기능](#%EC%83%88%EB%A1%9C%EC%9A%B4-%EA%B8%B0%EB%8A%A5)
    - [변경 사항](#%EB%B3%80%EA%B2%BD-%EC%82%AC%ED%95%AD)
      - [데이터베이스 버전](#%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4-%EB%B2%84%EC%A0%84)
      - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
        - [데이터베이스 바이너리 버전](#%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4-%EB%B0%94%EC%9D%B4%EB%84%88%EB%A6%AC-%EB%B2%84%EC%A0%84)
        - [통신 프로토콜 버전](#%ED%86%B5%EC%8B%A0-%ED%94%84%EB%A1%9C%ED%86%A0%EC%BD%9C-%EB%B2%84%EC%A0%84)
        - [메타 버전](#%EB%A9%94%ED%83%80-%EB%B2%84%EC%A0%84)
        - [이중화 프로토콜 버전](#%EC%9D%B4%EC%A4%91%ED%99%94-%ED%94%84%EB%A1%9C%ED%86%A0%EC%BD%9C-%EB%B2%84%EC%A0%84)
      - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
        - [새로운 프로퍼티](#%EC%83%88%EB%A1%9C%EC%9A%B4-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
        - [변경된 프로퍼티](#%EB%B3%80%EA%B2%BD%EB%90%9C-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
        - [삭제된 프로퍼티](#%EC%82%AD%EC%A0%9C%EB%90%9C-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
      - [메타 테이블](#%EB%A9%94%ED%83%80-%ED%85%8C%EC%9D%B4%EB%B8%94)
      - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)
        - [새로운 성능 뷰](#%EC%83%88%EB%A1%9C%EC%9A%B4-%EC%84%B1%EB%8A%A5-%EB%B7%B0)
        - [수정된 성능 뷰](#%EC%88%98%EC%A0%95%EB%90%9C-%EC%84%B1%EB%8A%A5-%EB%B7%B0)
    - [패키지](#%ED%8C%A8%ED%82%A4%EC%A7%80)
    - [다운로드](#%EB%8B%A4%EC%9A%B4%EB%A1%9C%EB%93%9C)
      - [Package](#package)
      - [Manual](#manual)
      - [설치](#%EC%84%A4%EC%B9%98)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

</br>

</br>

</br>

Altibase 7.2.0.0.0 Release Notes
===============================



시스템 요구사항
---------------

### 하드웨어 최저 사양

* 1GB RAM (권장: 2GB)
* 1 CPU (권장: 2 CPUs)
* 4GB 하드 디스크 여유 공간 (권장: 12GB)

### 운영 체제 및 플랫폼

Altibase 7.2.0.0.0 는 아래 표에 나열된 운영체제와 플랫폼 상에서 운영 가능하다.

| OS    | CPU                                         | Version               | Bit (Server) | Bit (Client) |
| ----- | ------------------------------------------- | --------------------- | ------------ | ------------ |
| AIX   | PowerPC                                     | 6.1 tl03 and higher   | 64-bit       | 64-bit       |
| HP-UX | IA64                                        | 11.31 and higher      | 64-bit       | 64-bit       |
| LINUX | x86-64, PowerPC (GNU glibc 2.12 and higher) | redhat 6.0 and higher | 64-bit       | 64-bit       |
| LINUX | PowerPC8(LE) (GNU glibc 2.17)               | Redhat 7.2            | 64-bit       | 64-bit       |

> Java 버전: Altibase 7.2은 JDK 1.8 이상에서 호환된다.
> Altibase 7.2는 윈도우용 서버 및 클라이언트를 지원하지 않는다.  또한, 32bit 클라이언트를 지원하지 않는다.



릴리스 정보
-----------

### 새로운 기능

### 변경 사항

DBA와 개발자가 알아야 할 추가, 변경, 및 제거된 기능을 아래에서 설명한다.

#### 데이터베이스 버전

데이터베이스 구성 요소 별 버전

| Altibase 버전 | 데이터베이스 바이너리 버전 | 통신 프로토콜 버전 | 메타 버전 | 이중화 프로토콜 버전  | 샤딩 버전 |
| ------------- | ------------------------- | ------------------ | --------- | -------------------- | --------- |
| 7.1.0.1.2     | 6.5.1                     | 7.1.6              | 8.5.1     | 7.4.2                | N/A       |
| 7.2.0.0.0     | x.x.x                     | x.x.x              | x.x.x     | x.x.x                | 3.1.1     |

#### 호환성

##### 데이터베이스 바이너리 버전

데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그 파일의 호환성을 나타낸다. 데이터베이스 이미지 및 로그 파일의 형식이 변경되었으므로, 데이터베이스 업그레이드가 되지 않는다. 기존 데이터베이스는 마이그레이션 되어야 한다.

| Altibase 버전 | 데이터베이스 바이너리 버전 |
| ------------- | -------------------------- |
| 7.1.0.1.2     | 6.5.1                      |
| 7.2.0.0.0     | x.x.x                      |

##### 통신 프로토콜 버전

*Need to modify* 통신 프로토콜 버전이 변경되었다. Patch 버전(세번째 자리 버전)이 변경되어, Altibase 6.5.1에서 동작하도록 빌드된 클라이언트 응용 프로그램은 Altibase 7.1.0.1.2와 호환이 된다. 즉, 다시 빌드하지 않아도 된다.

| Altibase 버전 | 통신 프로토콜 버전 |
|---------------|--------------------|
| 7.1.0.1.2     | 7.1.6              |
| 7.2.0.0.0     | x.x.x              |

###### IPCDA 특이사항
- IPCDA는 FAST SIMPLE QUERY로 수행되지 않는 경우 Fetch시 1개 Row는 패킷 분할이 되지 않아 CM 패킷 사이즈 (32KB)를 넘을 수 없다. Altibase 7.2 통신 프로토콜이 변경됨에 따라 IPCDA는 사용자에게 전달할 수 있는 데이터 양이 달라질 수 있다.
- Altibase 7.2가 7.1에 비해 IPCDA는 사용자에게 전달할 수 있는 데이터양이 24byte 줄어든다.
- Altibase 7.2 통신 프로토콜에서 Exeucte 응답 프로토콜 (+8byte), IGNORE_Error 응답 프로토콜 (+8byte), 예비 Error 응답 프로토콜 (+8byte)이 추가되었기 때문이다.

##### 메타 버전

메타 버전이 변경되었다.

| Altibase 버전 | 메타 버전 |
|---------------|-----------|
| 7.1.0.1.2     | 8.5.1     |
| 7.2.0.0.0     | x.x.x     |

##### 이중화 프로토콜 버전

*Need to modify* 이중화 프로토콜 버전이 변경되지 않았다. 따라서 Altibase 6.5.1 과 7.1.0.1.2 간의 이중화가 가능하다.

| Altibase 버전 | 이중화 프로토콜 버전 |
|---------------|----------------------|
| 7.1.0.1.2     | 7.4.2                |
| 7.2.0.0.0     | x.x.x                |


##### 샤딩 버전

Altibase 7.2부터 샤딩 기능을 제공한다.

> 주의사항:
>
> 알티베이스 샤딩 프로토콜 및 메타는 상위, 하위 호환성을 보장하지 않는다. 즉, 샤딩 버전이 다른 경우 재구성해야 한다.
| Altibase 버전 | 샤딩 버전 |
|---------------|-----------|
| 7.2.0.0.0     | 3.1.1     |

#### 프로퍼티

Altibase 7.2.0.0.0 에서는 아래의 프로퍼티들이 추가, 변경, 삭제되었다.  
각 프로퍼티에 대한 자세한 내용은 *General Reference* 매뉴얼을 참고하기 바란다.

##### 새로운 프로퍼티

##### 변경된 프로퍼티

##### 삭제된 프로퍼티

#### 메타 테이블

#### 성능 뷰

각 성능 뷰에 대한 자세한 내용은 *General Reference* 매뉴얼을 참고하기 바란다.

##### 새로운 성능 뷰

##### 수정된 성능 뷰

### 패키지

| OS    | CPU                       | Archive Name                                                                                                             |
|-------|---------------------------|--------------------------------------------------------------------------------------------------------------------------|
| AIX   | PowerPC                   | altibase- server-7.2.0.0.0-AIX-POWERPC-64bit-release.run                                                                 |
|       |                           | altibase- client-7.2.0.0.0-AIX-POWERPC-64bit-release.run                                                                 |
| HP-UX | IA64                      | altibase- server-7.2.0.0.0-HPUX-IA64-64bit-release.run                                                                   |
|       |                           | altibase- client-7.2.0.0.0-HPUX-IA64-64bit-release.run                                                                  |
| LINUX | X86                       | altibase- server-7.2.0.0.0-LINUX-X86-64bit-release.run                                                                   |
|       |                           | altibase- client-7.2.0.0.0-LINUX-X86-64bit-release.run                                                                   |
|       | PowerPC                   | altibase- server-7.2.0.0.0-LINUX-POWERPC-64bit-release.run                                                               |
|       |                           | altibase- client-7.2.0.0.0-LINUX-POWERPC-64bit-release.run                                                               |
|       | PowerPCLE (Little Endian) | altibase- server-7.2.0.0.0-LINUX-POWERPCLE-64bit-release.run                                                             |
|       |                           | altibase- client-7.2.0.0.0-LINUX-POWERPCLE-64bit-release.run                                                             |

### 다운로드

#### Package

<http://support.altibase.com>

#### Manual
*Need to modify*

https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/README.md

#### 설치
*Need to modify*

[Altibase Installation Guide](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Installation.md) 참고
