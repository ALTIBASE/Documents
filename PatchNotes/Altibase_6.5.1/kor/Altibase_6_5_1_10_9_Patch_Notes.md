# Altibase 6.5.1.10.9 Patch Notes

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-51446 서버 비정상 종료 시(SIGSEGV 등) altibase_error.log에 콜스택 외 추가 진단 정보를 출력하도록 개선](#bug-51446)
    - [BUG-51467 서버 비정상 종료시 altibase_error.log에 콜스택 외 클라이언트 정보를 출력하도록 개선](#bug-51467)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-51880 쿼리 수행의 안정성 개선을 위한 내부 로직 개선(column count 관리 구조 변경)](#bug-51880)
    - [BUG-48433 dumptrc 수행 시 altibase_error.log 에 콜스택과 OS 에러 메시지가 섞이는 문제를 개선합니다.](#bug-48433)
    - [BUG-49243 20000바이트 이상의 길이가 긴 SQL문 사용 시 altibase_error.log 에 콜스택이 출력되지 않습니다.](#bug-49243)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# New Features

### BUG-51446<a name=bug-51446></a> 서버 비정상 종료 시(SIGSEGV 등) altibase_error.log에 콜스택 외 추가 진단 정보를 출력하도록 개선

- **module** : mm
- **Category** : Maintainability
- **재현 빈도** : Frequence
- **설명** : 서버 비정상 종료 시(SIGSEGV 등) altibase_error.log에 콜스택 외 추가 진단 정보를 출력하도록 개선합니다.
- **재현 방법**
  - **재현 절차**
  - **수행 결과**
  - **예상 결과**
- **Workaround**
- **변경사항**
  - Performance view
  - Property
  - Compile Option
  - Error Code

### BUG-51467<a name=bug-51467></a> 서버 비정상 종료시 altibase_error.log에 콜스택 외 클라이언트 정보를 출력하도록 개선

- **module** : mm

- **Category** : Functionality

- **재현 빈도** : Always

- **설명** : 서버 비정상 종료시 altibase_error.log에 콜스택 외 클라이언트 정보를 출력하도록 개선합니다.

  - CliPkgVer: 클라이언트 버전

  - CliProtoVer: 클라이언트 통신 프로토콜 버전

  - CliType: 클라이언트 타입

  - AppInfo: 어플리케이션 정보

    ```bash
    기존 콜스택 정보 아래에 추가로 출력됩니다.
    
    BEGIN-DUMP Diagnostic Information ===============
        Statement: 00007F75D24A9808                  
        Session: 000000000A22F148                    
            CliPkgVer: 7.4.0.0.0                     
            CliProtoVer: 7.1.9                       
            CliType: CLI-64LE                        
            AppInfo: isql                                
        Task: 000000000A16EF00                       
        Link: 00007F74E0000990                       
            ConnType: 1                              
    END-DUMP Diagnostic Information =================
    ```

Fixed Bugs
==========

### BUG-51880<a name=bug-51880></a> 쿼리 수행의 안정성 개선을 위한 내부 로직 개선(column count 관리 구조 변경)

-   **module** : qp

-   **Category** : Fatal

-   **재현 빈도** : Unknown

-   **설명** : 잘못된 메모리 참조 예방 및 안정성 보강을 위해 column count 관리 구조를 변경했습니다.
    
-   **재현 방법**
    -   **재현 절차**
    
    -   **수행 결과**
    
    -   **예상 결과**
    
-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-48433<a name=bug-48433></a> dumptrc 수행 시 altibase_error.log 에 콜스택과 OS 에러 메시지가 섞이는 문제를 개선합니다.

- **module** : id
- **Category** : Fatal
- **재현 빈도** : Unknown
- **증상** : dumptrc 수행 시 altibase_error.log 에 콜스택과 OS 에러 메시지가 섞이는 문제를 개선합니다.
- **재현 방법**
  - **재현 절차**
  - **수행 결과**
  - **예상 결과**
- **Workaround**
- **변경사항**
  - Performance view
  - Property
  - Compile Option
  - Error Code

### BUG-49243<a name=bug-49243></a> 20000바이트 이상의 길이가 긴 SQL문 사용 시 altibase_error.log 에 콜스택이 출력되지 않습니다.

- **module** : id
- **Category** : Testcase Fail
- **재현 빈도** : Always
- **설명** : 20000바이트 이상의 길이가 긴 SQL문 사용 시 altibase_error.log 에 콜스택이 잘리는 현상을 수정합니다. 이 현상은 BUG-48433이 반영된 Altibase 7.1.0.5.2 버전부터 발생하는 버그입니다.
- **재현 방법**
  - **재현 절차**
  - **수행 결과**
  - **예상 결과**
- **Workaround**
- **변경사항**
  - Performance view
  - Property
  - Compile Option
  - Error Code

Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 6.5.1.10.9       | 6.3.1                   | 8.1.1        | 7.1.3               | 7.4.5                        |

> Altibase 6.5.1 패치 버전별 히스토리는 [Version_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_6.5.1/Altibase_6_5_1_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의
> 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는
> 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

#### CM protocol Version

통신 프로토콜 버전은 변경되지 않았다.

#### Replication protocol Version

Replication 프로토콜 버전은 변경되지 않았다.

### 프로퍼티

추가/변경/삭제된 프로퍼티 없음.

### 성능 뷰

추가/변경/삭제된 성능뷰 없음.
