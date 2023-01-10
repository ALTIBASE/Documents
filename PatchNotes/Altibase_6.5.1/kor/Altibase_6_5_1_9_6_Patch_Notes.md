Altibase 6.5.1.9.6 Patch Notes
================================

<br>

<br>

# Table of Contents

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Fixed Bugs](#fixed-bugs)
  - [BUG-50033 adapter를 시작할 때 ALA 로그 파일을 오픈할 수 없으면 코어 파일이 생성됩니다.](#bug-50033adapter를-시작할-때-ala-로그-파일을-오픈할-수-없으면-코어-파일이-생성됩니다)
  - [BUG-50038 jdbcAdapter 및 oraAdapter 구동에서 예외 상황 발생 시 에러 메시지를 보완합니다.](#bug-50038jdbcadapter-및-oraadapter-구동에서-예외-상황-발생-시-에러-메시지를-보완합니다)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
  - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
  - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Fixed Bugs
==========

### BUG-50033 adapter를 시작할 때​ ALA 로그 파일을 오픈할 수 없으면 코어 파일이 생성됩니다.

#### module

`rp-ala`

#### Category

`Assert`

#### 재현 빈도

`Rare`

#### 설명

adapter를 시작할 때​ ALA 로그 파일을 오픈할 수 없으면 시그널을 받고 adapter 프로세스가 강제 종료되며 코어 파일이 생성됩니다. 예외 처리를 변경하여 adapter 트레이스 로그(예, jdbcAdapter.trc)에 다음과 같은 에러 메시지를 출력하도록 개선하였습니다.

`ALA library error: 335873, Failed to open log file`

#### 재현 방법

-   **재현 절차**

-   **수행 결과**

-   **예상 결과**

#### Workaround

`없음`

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50038 jdbcAdapter 및 oraAdapter 구동에서 예외 상황 발생 시 에러 메시지를 보완합니다.

#### module

`rp-oraAdapter` `rp-jdbcAdapter`

#### Category

`Functional Error`

#### 재현 빈도

`Always`

**설명** :


jdbcAdapter 및 oraAdapter 구동에서 아래와 같은 예외 상황 발생 시 에러 메시지를 출력하도록 개선합니다.

-   초기화 실패

-   메모리 할당 실패

-   Adapter 프로퍼티 파일 읽기 실패

-   Adapter 트레이스 로그 파일 열기 실패

-   Adapter 에러 메시지 파일 읽기 실패

#### 재현 방법

-   **재현 절차**

-   **수행 결과**

-   **예상 결과**

#### Workaround

`없음`

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    6.5.1.9.6     |          6.3.1          |    8.1.1     |        7.1.3        |            7.4.5             |

> Altibase 6.5.1 패치 버전별 히스토리는 [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_6.5.1/Altibase_6_5_1_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

#### Meta Version

메타 버전은 변경되지 않았다.

#### CM protocol Version

통신 프로토콜 버전은 변경되지 않았다.

#### Replication protocol Version

Replication 프로토콜 버전은 변경되지 않았다.

### 프로퍼티

#### 추가된 프로퍼티

#### 변경된 프로퍼티

#### 삭제된 프로퍼티

### 성능 뷰

#### 추가된 성능 뷰

#### 변경된 성능 뷰

#### 삭제된 성능 뷰
