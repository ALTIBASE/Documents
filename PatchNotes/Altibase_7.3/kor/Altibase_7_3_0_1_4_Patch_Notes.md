Altibase 7.3.0.1.4 Patch Notes
==============================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-51881 태국어 캐릭터셋 지원](#bug-51881)
    - [BUG-51867 Altibase Connector for Kafka에 태국어 지원 기능 추가](#bug-51867)
    - [BUG-51880 쿼리 수행의 안정성 개선을 위한 내부 로직 개선(column count 관리 구조 변경)](#bug-51880)
    - [BUG-51902 신규 CLI 함수 SQLRowCount2가 추가되었습니다.](#bug-51902)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-51805 디스크 인덱스 예외상황에서 인덱스ID가 기록되지 않습니다.](#bug-51805)
    - [BUG-51878 In-place update 사용 시 NULL 문자열을 빈 문자열로 변경할 때의 로그가 잘못 기록되어, 로그 검증 과정에서 서버가 종료될 수 있는 문제를 수정하였습니다.](#bug-51878)
    - [BUG-51899 인덱스 추가/삭제시 Runtime Header에 저장된 인덱스 헤더 주소가 갱신되지 않을수 있습니다.](#bug-51899)
    - [BUG-51909 서버 비정상 종료시 콜스택에 클라이언트 PID, COMMIT MODE, COMM\_NAME, statement 정보 등을 추가로 출력해야 합니다.](#bug-51909)
    - [BUG-51920 ORDER BY절에 LOB 타입을 사용시 비정상 종료 문제 수정](#bug-51920)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-51881<a name=bug-51881></a> 태국어 캐릭터셋 지원

-   **module** : qp

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : 데이터베이스 생성시 태국어 캐릭터셋(TH8TISASCII)을 지정할 수 있도록 개선되었습니다. ISO/IEC 14651 표준 기반의 태국어 정렬을 지원하며, 태국어 정렬을 사용하려면 아래의 프로퍼티 설정을 추가해야 합니다.
    -   NLS_COMP=1

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

### BUG-51867<a name=bug-51881></a> Altibase Connector for Kafka에 태국어 지원 기능 추가

-   **module** : rp-kafkaConnector

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : Altibase Connector for Kafka(Altibase 커넥터) 에서 태국어를 지원하도록 개선되었습니다.

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

### BUG-51880<a name=bug-51881></a> 쿼리 수행의 안정성 개선을 위한 내부 로직 개선(column count 관리 구조 변경)

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

### BUG-51902<a name=bug-51881></a> 신규 CLI 함수로 SQLRowCount2가 추가되었습니다. 

-   **module** : ul-odbc

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : UPDATE, INSERT 또는 DELETE 문에 의해 영향을 받은 행들의 수를 반환할 때, 최대 64비트 정수 범위의 행 개수를 반환하기 위해 신규 CLI 함수로 [SQLRowCount2](https://manual.altibase.com/7.3/dev/cli/2.-Altibase-CLI-Functions/SQLRowCount/#sqlrowcount2)가 추가되었습니다. 

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

### BUG-51805<a name=bug-51805></a> 디스크 인덱스 예외상황에서 인덱스ID가 기록되지 않습니다.

-   **module** : sm

-   **Category** : Functional Error

-   **재현 빈도** : Unknown

-   **설명** : 디스크 인덱스 예외상황에서 에러 메시지에 인덱스 ID가 기록되지 않는 문제 수정합니다.
    
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

### BUG-51878<a name=bug-51878></a> In-place update 사용 시 NULL 문자열을 빈 문자열로 변경할 때의 로그가 잘못 기록되어, 로그 검증 과정에서 서버가 종료될 수 있는 문제를 수정하였습니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : In-place update 사용 시 NULL 문자열을 빈 문자열로 변경하는 경우 로그가 잘못 기록되어, 로그 검증 과정에서 서버가 종료될 수 있는 문제를 수정하였습니다.
    
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

### BUG-51899<a name=bug-51899></a> 인덱스 추가/삭제시 Runtime Header에 저장된 인덱스 헤더 주소가 갱신되지 않을수 있습니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : 인덱스를 추가하거나 삭제할때 인덱스 헤더 주소가 갱신되지 않을 수 있는 문제를 수정하였습니다.

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

### BUG-51909<a name=bug-51909></a> 서버 비정상 종료시 콜스택에 클라이언트 PID, COMMIT MODE, COMM\_NAME, statement 정보 등을 추가로 출력해야 합니다.

-   **module** : mm

-   **Category** : Other

-   **재현 빈도** : Rare

-   **설명** : 서버 비정상 종료시 분석에 도움이 되도록 클라이언트 PID, COMMIT MODE,
    COMM\_NAME, statement 정보등을 altibase\_error.log에 출력하도록
    추가하였습니다. 기존 콜스택 정보 밑에 추가로 출력됩니다.

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

### BUG-51920<a name=bug-51920></a> ORDER BY절에 LOB 타입을 사용시 비정상 종료 문제 수정

-   **module** : qp-dml-execute
-   **Category** : Fatal
-   **재현 빈도** : Always
-   **설명** : ORDER BY절에서는 LOB 타입을 사용할 수 없는데, LOB 컬럼을 사용한경우 비정상 종료하는 문제를 수정했습니다. 이제 ORDER BY절에서 LOB 타입을 사용하면 [ERR-31246 : Incomparable data types (GEOMETRY,LOB) cannot
be used in ORDER BY, GROUP BY, HAVING and CONNECT BY clauses.] 오류가 정상적으로 반환됩니다.
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
| 7.3.0.1.4        | 7.3.0                   | 9.4.1        | 7.1.8               | 7.4.9                        |

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
