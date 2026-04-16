Altibase 7.3.0.2.0 Patch Notes
==============================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-52233 abm에서 gzip 압축 레벨 설정 기능 추가](#bug-52233%C2%A0abm%EC%97%90%EC%84%9C-gzip-%EC%95%95%EC%B6%95-%EB%A0%88%EB%B2%A8-%EC%84%A4%EC%A0%95-%EA%B8%B0%EB%8A%A5-%EC%B6%94%EA%B0%80)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-51905 adapter에서 LOB 컬럼이 포함된 디스크 테이블 이중화 오류 수정](#bug-51905%C2%A0adapter%EC%97%90%EC%84%9C-lob-%EC%BB%AC%EB%9F%BC%EC%9D%B4-%ED%8F%AC%ED%95%A8%EB%90%9C-%EB%94%94%EC%8A%A4%ED%81%AC-%ED%85%8C%EC%9D%B4%EB%B8%94-%EC%9D%B4%EC%A4%91%ED%99%94-%EC%98%A4%EB%A5%98-%EC%88%98%EC%A0%95)
    - [BUG-52106 abm 에러 메시지 개선1](#bug-52106%C2%A0abm-%EC%97%90%EB%9F%AC-%EB%A9%94%EC%8B%9C%EC%A7%80-%EA%B0%9C%EC%84%A01)
    - [BUG-52122 abm 에러 메시지 개선2](#bug-52122%C2%A0abm-%EC%97%90%EB%9F%AC-%EB%A9%94%EC%8B%9C%EC%A7%80-%EA%B0%9C%EC%84%A02)
    - [BUG-52168 BUFFER AREA SIZE 확장 후 디스크 테이블 DML 성능 미반영 문제 수정](#bug-52168%C2%A0buffer-area-size-%ED%99%95%EC%9E%A5-%ED%9B%84-%EB%94%94%EC%8A%A4%ED%81%AC-%ED%85%8C%EC%9D%B4%EB%B8%94-dml-%EC%84%B1%EB%8A%A5-%EB%AF%B8%EB%B0%98%EC%98%81-%EB%AC%B8%EC%A0%9C-%EC%88%98%EC%A0%95)
    - [BUG-52220 이중화 환경에서 LOB 컬럼과 Supplemental Log가 설정된 디스크 테이블에 DROP COLUMN 구문 수행 시 서버 비정상 종료 문제 수정](#bug-52220%C2%A0%EC%9D%B4%EC%A4%91%ED%99%94-%ED%99%98%EA%B2%BD%EC%97%90%EC%84%9C-lob-%EC%BB%AC%EB%9F%BC%EA%B3%BC-supplemental-log%EA%B0%80-%EC%84%A4%EC%A0%95%EB%90%9C-%EB%94%94%EC%8A%A4%ED%81%AC-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90-drop-column-%EA%B5%AC%EB%AC%B8-%EC%88%98%ED%96%89-%EC%8B%9C-%EC%84%9C%EB%B2%84-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C-%EB%AC%B8%EC%A0%9C-%EC%88%98%EC%A0%95)
    - [BUG-52226 SQL_APPLY 모드에서 DELETE 로그 처리 시 standby 서버 비정상 종료 문제 수정](#bug-52226%C2%A0sql_apply-%EB%AA%A8%EB%93%9C%EC%97%90%EC%84%9C-delete-%EB%A1%9C%EA%B7%B8-%EC%B2%98%EB%A6%AC-%EC%8B%9C-standby-%EC%84%9C%EB%B2%84-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C-%EB%AC%B8%EC%A0%9C-%EC%88%98%EC%A0%95)
    - [BUG-52236 하위 버전 클라이언트(6.1.1)에서 7.3 서버 접속 시 바인드 값이 없는 경우 ASSERT 발생 문제 수정](#bug-52236%C2%A0%ED%95%98%EC%9C%84-%EB%B2%84%EC%A0%84-%ED%81%B4%EB%9D%BC%EC%9D%B4%EC%96%B8%ED%8A%B8611%EC%97%90%EC%84%9C-73-%EC%84%9C%EB%B2%84-%EC%A0%91%EC%86%8D-%EC%8B%9C-%EB%B0%94%EC%9D%B8%EB%93%9C-%EA%B0%92%EC%9D%B4-%EC%97%86%EB%8A%94-%EA%B2%BD%EC%9A%B0-assert-%EB%B0%9C%EC%83%9D-%EB%AC%B8%EC%A0%9C-%EC%88%98%EC%A0%95)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-52233<a name=bug-52233></a> abm에서 gzip 압축 레벨 설정 기능 추가

-   **module** : ux-abm

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : abm에서 gzip 압축 레벨을 사용자가 직접 설정할 수 있도록 개선되었습니다. 이를 위해 `abm.properties` 파일에 ` GZIP_COMP_LEVEL`프로퍼티가 추가되었으며, 기본값은 6입니다.

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

Fixed Bugs
==========

### BUG-51905<a name=bug-51905></a> adapter에서 LOB 컬럼이 포함된 디스크 테이블 이중화 오류 수정

-   **module** : rp-jdbcAdapter

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : adapter에서 LOB 컬럼이 포함된 디스크 테이블 이중화 오류를 수정하였습니다.
    
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

### BUG-52106<a name=bug-52106></a> abm 에러 메시지 개선1

-   **module** : ux-abm

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : BACKUP INCREMENTAL 수행 중 서버 에러 메세지가 누락되는 현상을 수정하였습니다.
    
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

### BUG-52122<a name=bug-52122></a> abm 에러 메시지 개선2

-   **module** : ux-abm

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : Change Tracking 비활성 상태에서 잘못된 에러메시지가 출력되는 문제를 수정하였습니다.
    
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

### BUG-52168<a name=bug-52168></a> BUFFER AREA SIZE 확장 후 디스크 테이블 DML 성능 미반영 문제 수정

-   **module** : sm

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 서비스 중 DISK BUFFER AREA SIZE를 확장하더라도 디스크 테이블의 DML 성능이 향상되지 않던 문제를 수정하였습니다.

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

### BUG-52220<a name=bug-52220></a> 이중화 환경에서 LOB 컬럼과 Supplemental Log가 설정된 디스크 테이블에 DROP COLUMN 구문 수행 시 서버 비정상 종료 문제 수정

-   **module** : sm
-   **Category** : Fatal
-   **재현 빈도** : Always
-   **설명** : LOB 컬럼과 Supplemental Log가 설정된 디스크 테이블이 이중화(Replication)에 포함된 경우, DROP COLUMN 구문 수행 시 서버가 비정상 종료되던 문제를 수정하였습니다.
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

### BUG-52226<a name=bug-52226></a> SQL_APPLY 모드에서 DELETE 로그 처리 시 standby 서버 비정상 종료 문제 수정

-   **module** : rp-receiver

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : Supplemental Log가 설정된 테이블의 이중화 환경에서 standby 서버가 SQL_APPLY 모드로 동작할 때, DELETE 로그 처리 중 비정상 종료되는 문제를 수정합니다.

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

### BUG-52236<a name=bug-52236></a> 하위 버전 클라이언트(6.1.1)에서 7.3 서버 접속 시 바인드 값이 없는 경우 ASSERT 발생 문제 수정

-   **module** : qp

-   **Category** : Assert

-   **재현 빈도** : Always

-   **설명** : 하위 버전 클라이언트에서 7.3 서버에 접속하여 요청을 수행할 때, 바인드 값 없이 전달된 프로토콜을 처리하는 과정에서 ASSERT가 발생하여 서버가 비정상 종료되는 문제가 있었습니다. 이를 수정하여 정상 처리되도록 개선하였습니다.

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
| 7.3.0.2.0        | 7.3.0                   | 9.4.1        | 7.1.8               | 7.4.9                        |

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
