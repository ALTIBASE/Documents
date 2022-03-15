

- [Altibase Replication Manager 1.2 Release Notes](#altibase-replication-manager-12-release-notes)
  - [1\. 개요](#1-개요)
    - [1.1 시스템 요구사항](#11-시스템-요구사항)
    - [1.2 지원하는 OS 및 플랫폼](#12-지원하는-os-및-플랫폼)
  - [2\. 릴리즈 정보](#2-릴리즈-정보)
    - [2.1 Altibase Replication Manager 1.2](#21-altibase-replication-manager-12)
    - [2.2 변경사항](#22-변경사항)
    - [2.3 오픈소스 라이브러리](#23-오픈소스-라이브러리)
    - [2.4 패키지](#24-패키지)
    - [2.5 다운로드](#25-다운로드)



Altibase Replication Manager 1.2 Release Notes
===============================

**(Feburary 18, 2019)**


## 1. 개요

### 1.1 시스템 요구사항

#### 하드웨어 최저 사양

* 프로세서: 800MHz Pentium III 이상
* 메모리: 512 MB 이상
* 디스크: 50MB 이상 여유공간 (JRE 제외)
* 화면 해상도: 1024 * 768 픽셀 이상

### 1.2 지원하는 OS 및 플랫폼

| OS                 | CPU  | Windows System | Bit (Client) | JRE         |
| ------------------ | ---- | -------------- | ------------ | ----------- |
| Windows XP Vista 7 | x86  | Win32          | 32bit        | Java 6 이상 |
| LINUX              | x86  | GTK            | 32bit        | Java 6 이상 |

## 2. 릴리즈 정보

### 2.1 Altibase Replication Manager 1.2

Replication Manager는 Alitbase의 이중화를 효율적으로 관리하기 위한 GUI 툴이다.

#### 2.1.1 새로운 기능

| 버그 번호 |                제목                |
| :-------: | :--------------------------------: |
| BUG-46683 | 다중 IP를 가진 DB를 지원해야 한다. |

#### 2.1.2  수정된 버그

| 버그 번호 |                  제목                   |
| :-------: | :-------------------------------------: |
| BUG-46677 | Sync 작업 후에 GUI를 업데이트해야 한다. |

### 2.2 변경사항

Replication Manager에 추가, 삭제 또는 변경된 기능들은 다음과 같다.

#### 2.2.1 버전 업데이트

Replication Manager 버전

| Altibase Replication Manager 버전 |
| :-------------------------------- |
| 1.2                               |

#### 2.2.2 호환성

##### Altibase 호환성

- Replication Manager: Altibase 4.3.9 이상 버전

#### 2.2.3 프로퍼티

#### 2.2.4 에러 메시지

### 2.3 오픈소스 라이브러리

Replication Manager는 아래의 오픈소스 라이브러리와 로열티 프리 이미지에 기반한다. 라이선스는 텍스트 파일 형식으로 Replication Manager와 함께 제공된다.

| 라이브러리        | 오픈소스 라이선스                                            |
| ----------------- | ------------------------------------------------------------ |
| balcosqlformatter | Homepage: http://www.igapyon.jp/blanco/blancosqlformatter.html </br>License: LGPL (http://www.gnu.org/licenses/lgpl-3.0.txt) |
| Eclipse           | Homepage: http://www.eclipse.org <br/>License: Eclipse Public License (http://www.eclipse.org/legal/epl-v10.html) |
| JDOM              | Homepage: http://www.jfree.org/jfreechart/) <br/>License: LGPL (http://www.gnu.org/licenses/lgpl-3.0.txt) |
| JFreeChart        | Homepage: http://www.jfree.org/jfreechart/) <br/>License: LGPL (http://www.gnu.org/licenses/lgpl-3.0.txt) |
| Log4j             | Homepage: http://logging.apache.org/index.html<br/>License: Apache License 2.0 (http://www.apache.org/licenses/LICENSE-2.0.txt) |

| 라이브러리                | 로열티 프리 이미지                         |
| ------------------------- | ------------------------------------------ |
| asp.net_commercial_free2  | Homepage: www.asp.net                      |
| www.famfamfam.com         | Homepage: www.famfamfam.com                |
| fatcow-hosting-icons-2400 | Homepage: http://www.fatcow.com/free-icons |

### 2.4 패키지

| OS          | CPU | Archive Name                           |
| ----------- | --- | -------------------------------------- |
| Linux/glibc | x86 | ReplicationManager-linux.gtk.x86.zip   |
| Windows     | x86 | ReplicationManager-win32.win32.x86.zip |

### 2.5 다운로드

#### 2.5.1 패키지

<http://support.altibase.com>

#### 2.5.2 매뉴얼

[Replication Manager User's Manual.md](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Tools/kor/Replication%20Manager%20User's%20Manual.md)

#### 2.5.3 Installation

Replication Manager User's Manual을 참고한다.