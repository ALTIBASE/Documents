Altibase 7.3.0.2.5 Patch Notes
==============================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Fixed Bugs](#fixed-bugs)
  - [BUG-52533 DDL Sync 중 TableOID가 변경되어도 이중화 메타를 다시 빌드하지 않는 문제 수정](#bug-52533)
  - [BUG-52553 DDL 수행 중 Commit 실패로 서버가 비정상 종료되는 문제 수정](#bug-52553)
  - [BUG-52560 Altibase source connector for Kafka에서 스키마 생성 시 컬럼 순서를 유지하지 않는 문제 수정](#bug-52560)
  - [BUG-52573 iloader help 화면에서 "-lightmode" 옵션 제거](#bug-52573)
  - [BUG-52575 이중화에서 잘못된 Update Log 처리 시 Sender가 비정상 종료되는 문제 수정](#bug-52575)
  - [BUG-52589 Disk Hash Temp Table 사용 시 잘못된 결과가 반환되는 문제 수정](#bug-52589)
  - [BUG-52603 보안 취약점 KVE-2026-2355 수정](#bug-52603)
  - [BUG-52620 서버 패키지에서 altiMon 분리](#bug-52620)
  - [BUG-52621 DDL 수행 후 이중화 재시작 시 잘못된 Table OID 참조로 비정상 종료되는 문제 수정](#bug-52621)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
  - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
  - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Fixed Bugs
==========

Fixed Bugs
----------

### BUG-52533<a name=bug-52533></a> DDL Sync 중 TableOID가 변경되어도 이중화 메타를 다시 빌드하지 않는 문제 수정

-   **module** : rp

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : DDL Sync 수행 중 TableOID가 변경되었음에도 이중화 메타를
    다시 빌드하지 않아 문제가 발생할 수 있었습니다. 이를 수정하여 DDL Sync
    중 TableOID가 변경되면 이중화 메타를 다시 빌드하도록 하였으며, 이와
    관련된 에러 코드를 추가하였습니다.
    
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

### BUG-52553<a name=bug-52553></a> DDL 수행 중 Commit 실패로 서버가 비정상 종료되는 문제 수정

-   **module** : qp-ddl-dcl-execute

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : DDL 수행 과정에서 Commit이 실패할 경우 서버가 비정상 종료될 수 있는 문제를 수정했습니다.

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

### BUG-52560<a name=bug-52560></a> Altibase source connector for Kafka에서 스키마 생성 시 컬럼 순서를 유지하지 않는 문제 수정

-   **module** : rp-kafkaConnector

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : Altibase Source Connector for Kafka에서 스키마 생성 시 컬럼 순서가 원본 테이블의 컬럼 순서와 다르게 등록될 수 있는 문제를 수정했습니다. 기존에는 PK 컬럼과 일반 컬럼의 순서가 변경되어 스키마가 생성될 수 있었습니다. 원본 테이블의 컬럼 순서대로 스키마가 생성되도록 수정했습니다.
    
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

### BUG-52573<a name=bug-52573></a> iloader help 화면에서 "-lightmode" 옵션 제거

-   **module** : ux-iloader

-   **Category** : Usability

-   **재현 빈도** : Always

-   **설명** : iloader의 help 화면에서 "-lightmode" 옵션을 제거했습니다.

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

### BUG-52575<a name=bug-52575></a> 이중화에서 잘못된 Update Log 처리 시 Sender가 비정상 종료되는 문제 수정

-   **module** : rp

-   **Category** : Fatal

-   **재현 빈도** : Impossible

-   **설명** : 이중화에서 잘못된 Update Log를 읽을 경우 FATAL 오류로 인해 서버가 비정상 종료되는 문제를 수정했습니다. 잘못된 Update Log가 감지되면 오류 로그를 기록하고 Sender를 종료하도록 변경했습니다. 
    
    사용자는 아래 에러가 altibase\_rp.log에 남을 경우 이중화를 drop후 재
    생성하여야 합니다.
    
    ERR-11069(errno=62) Internal server error in the storage manager
    ([smiLogRec::analyzeColumnMVImageMemory] Column Count is 0(zero) at
    [LSN: 16818,50008944)])

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

### BUG-52589 Disk Hash Temp Table 사용 시 잘못된 결과가 반환되는 문제 수정

-   **module** : sm-disk-resource

-   **Category** : Reliability

-   **재현 빈도** : Always

-   **설명** : 특정 조건에서 GROUP BY 수행 중 Disk Hash Temp Table을 사용할 경우 잘못된 결과가 반환될 수 있는 문제를 수정했습니다.

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

### BUG-52603<a name=bug-52603></a> 보안 취약점 KVE-2026-2355 수정

-   **module** : id

-   **Category** : Maintainability

-   **재현 빈도** : Always

-   **설명** : 복제(HA) 수신 처리 과정에서 압축 데이터를 해제할 때 출력 버퍼의 경계를 검사하지 않아 스택 버퍼 오버플로우가 발생할 수 있는 보안 취약점 KVE-2026-2355를 수정했습니다.

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

### BUG-52620<a name=bug-52620></a> 서버 패키지에서 altiMon 분리

-   **module** : ux-altiMon

-   **Category** : Maintainability

-   **재현 빈도** : Always

-   **설명** : 서버 패키지에 포함되어 있던 altiMon 바이너리를 분리하여 서버 패키지에 포함되지 않도록 변경했습니다.

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

### BUG-52621<a name=bug-52621></a> DDL 수행 후 이중화 재시작 시 잘못된 Table OID 참조로 비정상 종료되는 문제 수정

-   **module** : rp

-   **Category** : Fatal

-   **재현 빈도** : Unknown

-   **설명** : DDL 수행 후 이중화를 재시작하는 과정에서 기존 이중화 항목(old item)의 Table OID를 통해 테이블 정보를 조회할 때 잘못된 OID가 사용되어 서버가 비정상 종료될 수 있는 문제를 수정했습니다.
    
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
| 7.3.0.2.5        | 7.3.0                   | 9.4.1        | 7.1.8               | 7.4.9                        |

> Altibase 7.3 패치 버전별 히스토리는 [Version_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.3/Altibase_7_3_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의
> 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는
> 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

> 패치를 롤백하려는 경우, [메타다운그레이드](https://manual.altibase.com/7.3/start-here/install/3.-Uninstalling-Altibase-and-Meta-Downgrade/#%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9Cmeta-downgrade)를 참고한다.

#### CM protocol Version

통신 프로토콜 버전은 변경되지 않았다.

#### Replication protocol Version

Replication 프로토콜 버전은 변경되지 않았다.

### 프로퍼티

추가/변경/삭제된 프로퍼티 없음.

### 성능 뷰

추가/변경/삭제된 성능뷰 없음.
