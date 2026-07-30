Altibase 7.3.0.2.3 Patch Notes
==============================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
  - [BUG-52430 ALA에서 Handshake 과정 중 Sender IP 확인 여부를 선택할 수 있는 기능을 추가](#bug-52430)
- [Fixed Bugs](#fixed-bugs)
  - [BUG-51279 7.3.0.x.x 버전에서 7.3.1.x.x 버전으로 패치할 수 없는 문제 수정](#bug-51279)
  - [BUG-51719 Receiver 초기화 오류 메시지에 Replication 이름이 올바르게 표시되지 않는 문제 수정](#bug-51719)
  - [BUG-52325 이중화 환경에서 Supplemental Log 처리 안정성 개선](#bug-52325)
  - [BUG-52381 iLoader -lightmode 옵션 이용 시, LOB 데이터 삽입 오류 수정](#bug-52381)
  - [BUG-52384 동일한 Prepared Statement에서 바인드 값만 변경하며 반복 실행하는 경우, 트리거 내부 statement 가 재사용되지 않는 문제 수정](#bug-52384)
  - [BUG-52466 Volatile Tablespace 내 Temporary Table의 Primary Key 제약조건 재생성 후 인덱스 접근 시 발생하는 결과 오류 수정](#bug-52466)
  - [BUG-52484 잘못된 프로토콜 헤더 수신 시 진단 정보 출력 과정에서 서버가 비정상 종료되는 문제 수정](#bug-52484)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
  - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
  - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-52430<a name=bug-52430></a> ALA에서 Handshake 과정 중 Sender IP 확인 여부를 선택할 수 있는 기능을 추가

-   **module** : rp-kafkaConnector

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : ALA에서 Handshake 수행 시 Sender IP를 검증할지 여부를 선택할 수 있는 기능을 추가했습니다.
    
    새로 추가된 `ALA_SetVerifySenderIP()` 함수를 사용하여 Sender IP 검증을 활성화하거나 비활성화할 수 있으며, 기본값은 검증 수행(`ALA_TRUE`)입니다.
    
    또한 oraAdapter, jdbcAdapter, Altibase Source Connector for Kafka에도 동일한 기능을 설정할 수 있는 프로퍼티를 추가했습니다.
    
    - `ALA_VERIFY_SENDER_IP` (0: 검증 안 함, 1: 검증 수행)
    - `ala.verify.sender.ip` (false: 검증 안 함, true: 검증 수행)
    
-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
        -   ALA\_VERIFY\_SENDER\_IP (ALA 프로퍼티)
            -   값 범위: 0, 1
                -   1: (기본값) Sender IP 를 확인
                -   0: Sender IP 를 확인하지 않음
        -   ala.verify.sender.ip (커넥터 프로퍼티)
            -   타입: boolean
                -   true: (기본값) Sender IP 를 확인
                -   false: Sender IP 를 확인하지 않음
    -   Compile Option
    -   Error Code

Fixed Bugs
==========

### BUG-51279<a name=bug-51279></a> 7.3.0.x.x 버전에서 7.3.1.x.x 버전으로 패치할 수 없는 문제 수정

- **module** : installer

- **Category** : Portability

- **재현 빈도** : Always

- **설명** : 기존에는 일부 7.3.0.x.x 버전에서 7.3.1.x.x버전으로 패치할 수 없는 문제가 있었습니다. 이 문제를 수정하여 7.3.0.2.3 부터는 7.3.1.x.x 버전으로 정상적으로 패치할 수 있습니다. 

-   **재현 방법**
    -   **재현 절차**
    
    -   **수행 결과**
    
    -   **예상 결과**
    
- **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-51719<a name=bug-51719></a> Receiver 초기화 오류 메시지에 Replication 이름이 올바르게 표시되지 않는 문제 수정

-   **module** : rp
-   **Category** : Message Error
-   **재현 빈도** : Always
-   **설명** : Receiver 초기화 실패 시 출력되는 오류 메시지 `rpERR_ABORT_RP_RECEIVER_INITIALIZE_FAIL`에서 Replication 이름이 정상적으로 표시되지 않던 문제를 수정했습니다.
    -   변경 전: **The receiver(%s) has not started, because the replication meta information has been changed.**
    -   변경 후: **The receiver(<0%s>) has not started, because the replication meta information has been changed.**
    
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

### BUG-52325<a name=bug-52325></a> 이중화 환경에서 Supplemental Log 처리 안정성 개선

-   **module** : sm\_interface

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : 이중화 환경에서 Supplemental Log가 활성화된 디스크 테이블에 대해 UPDATE 작업 수행시 서버 비정상 종료되는 문제를 수정하였습니다.

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

### BUG-52381<a name=bug-52381></a> iLoader -lightmode 옵션 이용 시, LOB 데이터 삽입 오류 수정

-   **module** : sm

-   **Category** : Functional Error

-   **재현 빈도** : Always

- **설명** : iLoader 에서 -lightmode 옵션을 이용하여 LOB 데이터를 로딩할 때, 정상적으로 처리되지 않던 문제를 수정했습니다.

  또한, -lightmode 옵션을 이용한 데이터 로딩 중 장애가 발생하여 테이블의 정합성이 보장되지 않을 경우, 해당 테이블에 대한 DML 수행 시 다음의 오류가 반환되도록 개선되었습니다.

  **[ERR-11120 : The table is inconsistent.]**

  이 오류가 발생하면, 대상 테이블을 삭제한 후 재 생성해야 합니다.

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

### BUG-52384<a name=bug-52384></a> 동일한 Prepared Statement에서 바인드 값만 변경하며 반복 실행하는 경우, 트리거 내부 statement 가 재사용되지 않는 문제 수정

-   **module** : qp-psm-trigger-execute

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 동일한 Prepared Statement에서 바인드 값만 변경하며 반복 실행하는 경우, 트리거 내부의 Statement가 재사용되지 않고 매번 새로 할당되는 문제가 있었습니다. 이로 인해 세션 내 Statement 수가 계속 증가하여 `There are too many statements in the session` 오류가 발생할 수 있었습니다. 수정 이후에는 이전에 할당된 트리거 Statement가 정상적으로 정리되어, 반복 실행 시에도 Statement가 불필요하게 증가하지 않습니다.
    
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

### BUG-52466<a name=bug-52466></a> Volatile Tablespace 내 Temporary Table의 Primary Key 제약조건 재생성 후 인덱스 접근 시 발생하는 결과 오류 수정

-   **module** : qp-dml-pvo

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : Volatile Tablespace 내 Temporary Table의 Primary Key 제약조건 재생성 후 인덱스 접근 시 발생하는 오류를 수정합니다.
    
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

### BUG-52484<a name=bug-52484></a> 잘못된 프로토콜 헤더 수신 시 진단 정보 출력 과정에서 서버가 비정상 종료되는 문제 수정

-   **module** : mm
-   **Category** : Fatal
-   **재현 빈도** : Rare
-   **설명** : 잘못된 프로토콜 헤더를 수신했을때 진단정보 출력과정에서
    서버가 비정상 종료하는 문제를 수정하였습니다. 이 문제는 6.1.1 이하 클라이언트가 A5 프로토콜의 헤더 사인 값(0x06) 대신 잘못된 값을 전송하는 경우 발생할 수 있습니다. 이제 잘못된 헤더를 수신하더라도 서버가 비정상 종료되지 않도록 개선되었습니다.
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
| 7.3.0.2.3        | 7.3.0                   | 9.4.1        | 7.1.8               | 7.4.9                        |

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
