Altibase 7.3.0.1.6 Patch Notes
==============================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-51652 사용자 암호 입력 대신 암호화된 암호 파일로 로그인이 가능해야 합니다.](#bug-51652)
    - [BUG-52085 Altibase Backup Manager](#bug-52085)
    - [BUG-52026 Malformed packet 에러, 프로토콜 헤더 에러가 발생했을 때 분석을 위해 정보 출력을 보강해야 합니다.](#bug-52026)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-49298 이중화 Conflict시 정상 상황에서 불필요한 로그가 출력됩니다(Not Support Data Type).](#bug-49298)
    - [BUG-51529 adapter 실행 중 간헐적으로 발생하던 통신 오류(Protocol header error) 문제를 수정하였습니다.](#bug-51529)
    - [BUG-51792 불완전 복구시에 TBS Update 로그를 만날경우 redo 시점을 조정하지 않도록 수정합니다.](#bug-51792)
    - [BUG-52046 레코드 1건의 길이가 2.5MB 이상일 때 디스크 해시 템프 테이블 삽입 중 오류가 발생할 수 있는 문제를 수정하였습니다.](#bug-52046)
    - [BUG-52050 두개의 서버에서 하나의 remote서버 로 DDL Sync 수행 시 두번째 수행되는 DDL구문의 실패 에러가 잘못 나올 수 있습니다.](#bug-52050)
    - [BUG-52083 REPLICATION\_MAX\_LOGFILE 프로퍼티의 값이 1 이상이면, 체크포인트 수행 시 로그 파일의 수와 상관없이 모든 커밋된 로그파일이 삭제됩니다.](#bug-52083)
    - [BUG-52086 IPC 접속 환경에서 ServiceThread가 유효하지 않은 메모리를 참조할 수 있는 문제를 수정하였습니다.](#bug-52086)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-51652<a name=bug-51652></a> 사용자 암호 입력 대신 암호화된 암호 파일로 로그인이 가능해야 합니다.

-   **module** : ux-isql

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : iSQL에서 사용자 비밀번호를 암호화된 파일로 저장할 수
    있으며, 저장된 암호 파일은 iSQL, aexport, iLoader에서 -pf 옵션을
    통해 로그인 시 사용할 수 있습니다.

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

### BUG-52085<a name=bug-52085></a> Altibase Backup Manager

-   **module** : ux-abm

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : 백업을 효율적으로 수행하고 백업 파일을 안전하게 관리하기 위해 abm 유틸리티를 제공한다. 직관적인 인터페이스를 통해 백업 수행부터 파일의 압축, 암호화 및 복호화 작업을 손쉽게 수행할 수 있다. 자세한 설명은 **[Utilities Manual - abm](https://manual.altibase.com/7.3/tools/util/6.-abm/)** 을 참고 한다.
    
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

### BUG-52026<a name=bug-52026></a> Malformed packet 에러, 프로토콜 헤더 에러가 발생했을 때 분석을 위해 정보 출력을 보강해야 합니다.

- **module** : cm

- **Category** : Functionality

- **재현 빈도** : Unknown

- **설명** : Protocol header error가 발생했을 때 분석에 도움이 되도록
  세션 정보를 출력하도록 수정하였습니다.

  또한 세션 정보에 Client PID도 출력되도록 수정하였습니다.

- **재현 방법**

  -   **재현 절차**

  -   **수행 결과**

  -   **예상 결과**

- **Workaround**

- **변경사항**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

Fixed Bugs
==========

### BUG-49298<a name=bug-49298></a> 이중화 Conflict시 정상 상황에서 불필요한 로그가 출력됩니다(Not Support Data Type).

-   **module** : rp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 이중화 Conflict 시 BLOB, CLOB, GEOMETRY, JSON 타입의
    컬럼이 존재하면 $ALTIBASE_HOME/trc/altibase_rp.log 파일에 아래와 같이 불필요한 로그가 출력되는 현상을 수정했습니다.
    
    ```
    ERR-61069(errno=62) Internal server error in replication module (Not Support Data Type( id : 40 )).
    ```
    
    또한, altibase_rp_conflict.log 파일에 BLOB, CLOB, GEOMETY, JSON 타입은 데이터 타입과 상관 없이 "\<None printable data>"와 같이 출력되는 것을 "<None printable data( id : 30 )>"처럼 해당 컬럼의 데이터 타입의 ID도 함께 출력하도록 수정했습니다.
    
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

### BUG-51529<a name=bug-51529></a> adapter 실행 중 간헐적으로 발생하던 통신 오류(Protocol header error) 문제를 수정하였습니다.

-   **module** : rp-jdbcAdapter

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : adapter 실행 중 간헐적으로 발생하던 통신 오류(Protocol header error) 문제를 수정하였습니다.
    
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

### BUG-51792<a name=bug-51792></a> 불완전 복구시에 TBS Update 로그를 만날경우 redo 시점을 조정하지 않도록 수정합니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : 불완전 복구시에 TBS Update 로그를 만나면 Redo 시점을
    조정하지 않도록 합니다.

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

### BUG-52046<a name=bug-52046></a> 레코드 1건의 길이가 2.5MB 이상일 때 디스크 해시 템프 테이블 삽입 중 오류가 발생할 수 있는 문제를 수정하였습니다.

-   **module** : sm

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 레코드 1건의 길이가 2.5MB 이상일 때 디스크 해시 템프 테이블 삽입 중 오류가 발생할 수 있는 문제를 수정하였습니다.

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

### BUG-52050<a name=bug-52050></a> 두개의 서버에서 하나의 remote서버 로 DDL Sync 수행 시 두번째 수행되는 DDL구문의 실패 에러가 잘못 나올 수 있습니다.

-   **module** : rp

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : 두개의 서버에서 하나의 remote서버 로 DDL Sync 수행 시
    두번째 수행되는 DDL구문의 실패 에러가 잘못 나오는 경우에 대하여
    수정하였습니다.

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

### BUG-52083<a name=bug-52083></a> REPLICATION\_MAX\_LOGFILE 프로퍼티의 값이 1 이상이면, 체크포인트 수행 시 로그 파일의 수와 상관없이 모든 커밋된 로그파일이 삭제됩니다.

-   **module** : rp-sender

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : REPLICATION\_MAX\_LOGFILE 프로퍼티에 대한 동작 오류를
    수정합니다.

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

### BUG-52086<a name=bug-52086></a> IPC 접속 환경에서 ServiceThread가 유효하지 않은 메모리를 참조할 수 있는 문제를 수정하였습니다.

-   **module** : mm

-   **Category** : Memory Error

-   **재현 빈도** : Rare

-   **설명** : IPC 접속 환경에서 ServiceThread가 유효하지 않은 메모리를 참조할 수 있는 문제를 수정하였습니다.

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

Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 7.3.0.1.6        | 7.3.0                   | 9.4.1        | 7.1.8               | 7.4.9                        |

> Altibase 7.3 패치 버전별 히스토리는 [Version_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.3/Altibase_7_3_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의
> 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는
> 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

> 패치를 롤백하려는 경우,
> [메타다운그레이드](https://manual.altibase.com/7.3/start-here/install/3.-Uninstalling-Altibase-and-Meta-Downgrade/#%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9Cmeta-downgrade)를
> 참고한다.

#### CM protocol Version

통신 프로토콜 버전은 변경되지 않았다.

#### Replication protocol Version

Replication 프로토콜 버전은 변경되지 않았다.

### 프로퍼티

추가/변경/삭제된 프로퍼티 없음.

### 성능 뷰

추가/변경/삭제된 성능뷰 없음.
