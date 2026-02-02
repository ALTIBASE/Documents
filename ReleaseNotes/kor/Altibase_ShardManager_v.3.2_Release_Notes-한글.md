

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Altibase Shard Manager Release Notes](#altibase-shard-manager-release-notes)
  - [1. Abstract](#1-abstract)
    - [1.1 System Requirements](#11-system-requirements)
    - [1.2 Supported Operating Systems and Platforms](#12-supported-operating-systems-and-platforms)
  - [2. Release Information](#2-release-information)
    - [2.1 Altibase Shard Manager](#21-altibase-shard-manager)
    - [2.2 Version and Compatibility](#22-version-and-compatibility)
    - [2.3 Open Source Libraries /Royalty-Free Images Used](#23-open-source-libraries-royalty-free-images-used)
    - [2.4 Packages](#24-packages)
    - [2.5 Downloads](#25-downloads)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

<br/>

<br/>

<br/>

Altibase Shard Manager Release Notes
===============================

**(Feb. 6, 2026)**

## 1. 개요

### 1.1 시스템 요구사항

#### 하드웨어 최소 사양

* 프로세서: 800MHz Pentium III 이상
* 메모리: 512 MB 이상
* 디스크 : 120MB 이상 여유공간
* 화면 해상도 : 1024 * 768 픽셀 이상

### 1.2 지원 OS

| OS      | CPU    | Windows System | Bit (Client) | JRE              |
| ------- | ------ | -------------- | ------------ | ---------------- |
| LINUX   | x86_64 | GTK            | 64bit        | Java 6 or higher |
| Windows | x86    | Win32          | 32bit        | Java 6 or higher |

## 2. 릴리즈 정보

### 2.1 Altibase Shard Manager

Altibase Shard Manger는 Altibase Sharding 3.2의 샤드 데이터베이스 및 객체 관리를 위한 그래픽 도구입니다. GUI 및 CLI 기반의 통합 인터페이스를 제공하여, 샤드 노드와 객체에 대한 시각적 관리부터 리샤딩 작업까지 마우스 클릭만으로 손쉽게 수행할 수 있습니다.

#### 2.1.1 주요 기능

- 사용자 편의를 위한 그래픽 인터페이스(GUI) 및 명령 줄 인터페이스(CLI)를 동시에 지원
- 샤드 데이터베이스 연결 및 관리
- 샤드 데이터베이스 요약 보고서 제공(HTML 형식)
  - Shard Configuration 레포트

  - Record Count 레포트

- 샤드 노드 관리
- 샤드 객체 관리
- 샤드 테이블 리샤딩(Resharding) 지원


### 2.2 버전 및 호환성

#### 2.2.1 버전

* Altibase Shard Manager Version: 3.2

#### 2.2.2 호환성

* 호환되는 Altibase 버전: Altibase Sharding 3.2

### 2.3 사용된 오픈 소스 라이브러리 / 로열티 프리 이미지

Shard manager는 다음 오픈 소스 라이브러리와 로열티 프리 이미지를 기반으로 합니다. 라이선스는 Shard Manager와 함께 텍스트 파일 형식으로 배포됩니다.

#### 오픈소스 라이브러리

| Library              | Open Source License                                          |
| -------------------- | ------------------------------------------------------------ |
| Eclipse              | Homepage: http://www.eclipse.org <br/>License: Eclipse Public License (http://www.eclipse.org/legal/epl-v10.html) |
| Apache Commons Codec | Homepage: http://commons.apache.org/codec/<br/>License: Apache License 2.0<br/>(http://www.apache.org/licenses/LICENSE-2.0.txt) |
| Apache Commons Lang  | Homepage: http://commons.apache.org/proper/commons-lang/<br/>License: Apache License 2.0<br/>(http://www.apache.org/licenses/LICENSE-2.0.txt) |
| Apache Commons IO    | Homepage: http://commons.apache.org/proper/commons-io/<br/>License: Apache License 2.0<br/>(http://www.apache.org/licenses/LICENSE-2.0.txt) |
| Apache Commons CLI   | Homepage: https://commons.apache.org/proper/commons-cli/<br/>License: Apache License 2.0<br/>(http://www.apache.org/licenses/LICENSE-2.0.txt) |
| Log4j                | Homepage: http://logging.apache.org/index.html<br/>License: Apache License 2.0<br/>(http://www.apache.org/licenses/LICENSE-2.0.txt) |
| JDOM                 | Homepage: http://www.jdom.org/<br/>License: Apache-style Open Source License<br/>(http://www.jdom.org/docs/faq.html#a0030) |

#### 로열티 프리 이미지

| Library                      | Royalty-Free Images                                 |
| ---------------------------- | --------------------------------------------------- |
| 16x16 Free Application Icons | Homepage: http://www.aha-soft.com                   |
| asp.net_commercial_free2     | Homepage: www.asp.net                               |
| Eclipse                      | Homepage: www.eclipse.org                           |
| www.famfamfam.com            | Homepage: www.famfamfam.com                         |
| fatcow-hosting-icons-2400    | Homepage: http://www.fatcow.com/free-icons          |
| fugue-icons-3.2.3-src        | Homepage: http://code.google.com/p/fugue-icons-src/ |
| SqlExplorer                  | Homepage: http://eclipsesql.sourceforge.net/        |

### 2.4 패키지

| OS      | CPU    | 파일 이름                         |
| ------- | ------ | --------------------------------- |
| Linux   | x86_64 | ShardManager-linux.gtk.x86_64.zip |
| Windows | x86    | ShardManager-win32.win32.x86.zip  |

### 2.5 다운로드

#### 2.5.1 패키지

<http://support.altibase.com/kr/product>

#### 2.5.2 매뉴얼

https://manual.altibase.com/as3/admin/sharding/7.Shard-Manager/
