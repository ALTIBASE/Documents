Altibase 7.3.0.1.4 Patch Notes
==============================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-51881 태국어 캐릭터셋 지원](#bug-51881%C2%A0%ED%83%9C%EA%B5%AD%EC%96%B4-%EC%BA%90%EB%A6%AD%ED%84%B0%EC%85%8B-%EC%A7%80%EC%9B%90)
    - [BUG-51867 Altibase Connector for Kafka에 태국어 지원 기능 추가](#bug-51867%C2%A0altibase-connector-for-kafka%EC%97%90-%ED%83%9C%EA%B5%AD%EC%96%B4-%EC%A7%80%EC%9B%90-%EA%B8%B0%EB%8A%A5-%EC%B6%94%EA%B0%80)
    - [BUG-51880 쿼리 수행의 안정성 개선을 위한 내부 로직 개선(column count 관리 구조 변경)](#bug-51880%C2%A0%EC%BF%BC%EB%A6%AC-%EC%88%98%ED%96%89%EC%9D%98-%EC%95%88%EC%A0%95%EC%84%B1-%EA%B0%9C%EC%84%A0%EC%9D%84-%EC%9C%84%ED%95%9C-%EB%82%B4%EB%B6%80-%EB%A1%9C%EC%A7%81-%EA%B0%9C%EC%84%A0column-count-%EA%B4%80%EB%A6%AC-%EA%B5%AC%EC%A1%B0-%EB%B3%80%EA%B2%BD)
    - [BUG-51902 신규 CLI 함수 SQLRowCount2가 추가되었습니다.](#bug-51902%C2%A0%EC%8B%A0%EA%B7%9C-cli-%ED%95%A8%EC%88%98-sqlrowcount2%EA%B0%80-%EC%B6%94%EA%B0%80%EB%90%98%EC%97%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-51805 디스크 인덱스 예외상황에서 인덱스ID가 기록되지 않습니다.](#bug-51805%C2%A0%EB%94%94%EC%8A%A4%ED%81%AC-%EC%9D%B8%EB%8D%B1%EC%8A%A4-%EC%98%88%EC%99%B8%EC%83%81%ED%99%A9%EC%97%90%EC%84%9C-%EC%9D%B8%EB%8D%B1%EC%8A%A4id%EA%B0%80-%EA%B8%B0%EB%A1%9D%EB%90%98%EC%A7%80-%EC%95%8A%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-51878 In-place update 사용 시 NULL 문자열을 빈 문자열로 변경할 때의 로그가 잘못 기록되어, 로그 검증 과정에서 서버가 종료될 수 있는 문제를 수정하였습니다.](#bug-51878%C2%A0in-place-update-%EC%82%AC%EC%9A%A9-%EC%8B%9C-null-%EB%AC%B8%EC%9E%90%EC%97%B4%EC%9D%84-%EB%B9%88-%EB%AC%B8%EC%9E%90%EC%97%B4%EB%A1%9C-%EB%B3%80%EA%B2%BD%ED%95%A0-%EB%95%8C%EC%9D%98-%EB%A1%9C%EA%B7%B8%EA%B0%80-%EC%9E%98%EB%AA%BB-%EA%B8%B0%EB%A1%9D%EB%90%98%EC%96%B4-%EB%A1%9C%EA%B7%B8-%EA%B2%80%EC%A6%9D-%EA%B3%BC%EC%A0%95%EC%97%90%EC%84%9C-%EC%84%9C%EB%B2%84%EA%B0%80-%EC%A2%85%EB%A3%8C%EB%90%A0-%EC%88%98-%EC%9E%88%EB%8A%94-%EB%AC%B8%EC%A0%9C%EB%A5%BC-%EC%88%98%EC%A0%95%ED%95%98%EC%98%80%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-51899 인덱스 추가/삭제시 Runtime Header에 저장된 인덱스 헤더 주소가 갱신되지 않을수 있습니다.](#bug-51899%C2%A0%EC%9D%B8%EB%8D%B1%EC%8A%A4-%EC%B6%94%EA%B0%80%EC%82%AD%EC%A0%9C%EC%8B%9C-runtime-header%EC%97%90-%EC%A0%80%EC%9E%A5%EB%90%9C-%EC%9D%B8%EB%8D%B1%EC%8A%A4-%ED%97%A4%EB%8D%94-%EC%A3%BC%EC%86%8C%EA%B0%80-%EA%B0%B1%EC%8B%A0%EB%90%98%EC%A7%80-%EC%95%8A%EC%9D%84%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-51909 서버 비정상 종료시 콜스택에 클라이언트 PID, COMMIT MODE, COMM\_NAME, statement 정보 등을 추가로 출력해야 합니다.](#bug-51909%C2%A0%EC%84%9C%EB%B2%84-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%EC%8B%9C-%EC%BD%9C%EC%8A%A4%ED%83%9D%EC%97%90-%ED%81%B4%EB%9D%BC%EC%9D%B4%EC%96%B8%ED%8A%B8-pid-commit-mode-comm%5C_name-statement-%EC%A0%95%EB%B3%B4-%EB%93%B1%EC%9D%84-%EC%B6%94%EA%B0%80%EB%A1%9C-%EC%B6%9C%EB%A0%A5%ED%95%B4%EC%95%BC-%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-51920 ORDER BY절에 LOB 타입을 사용시 비정상 종료 문제 수정](#bug-51920%C2%A0order-by%EC%A0%88%EC%97%90-lob-%ED%83%80%EC%9E%85%EC%9D%84-%EC%82%AC%EC%9A%A9%EC%8B%9C-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C-%EB%AC%B8%EC%A0%9C-%EC%88%98%EC%A0%95)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-51881 태국어 캐릭터셋 지원

-   **module** : qp

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : 데이터베이스 생성시 태국어 캐릭터셋(TH8TISASCII)을 지정할 수 있도록 개선되었습니다. ISO/IEC 14651 표준 기반의 태국어 정렬을 지원하며, 태국어 정렬을 사용하려면 altibase.properties 파일에 아래의 프로퍼티를 추가로 설정해야 합니다.
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

### BUG-51867 Altibase Connector for Kafka에 태국어 지원 기능 추가

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

### BUG-51880 쿼리 수행의 안정성 개선을 위한 내부 로직 개선(column count 관리 구조 변경)

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

### BUG-51902 신규 CLI 함수 SQLRowCount2가 추가되었습니다. 

-   **module** : ul-odbc

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : UPDATE, INSERT 또는 DELETE 문에 의해 영향을 받은 행들의 수를 반환할 때, 최대 64비트 정수 범위의 행 개수를 반환하기 위해 신규 CLI 함수 SQLRowCount2가 추가되었습니다. 

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

### BUG-51805 디스크 인덱스 예외상황에서 인덱스ID가 기록되지 않습니다.

-   **module** : sm

-   **Category** : Functional Error

-   **재현 빈도** : Unknown

-   **설명** : 디스크 인덱스 예외상황에서 에러메시지에 인덱스 ID가 기록되지 않는 문제 수정합니다.
    
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

### BUG-51878 In-place update 사용 시 NULL 문자열을 빈 문자열로 변경할 때의 로그가 잘못 기록되어, 로그 검증 과정에서 서버가 종료될 수 있는 문제를 수정하였습니다.

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

### BUG-51899 인덱스 추가/삭제시 Runtime Header에 저장된 인덱스 헤더 주소가 갱신되지 않을수 있습니다.

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

### BUG-51909 서버 비정상 종료시 콜스택에 클라이언트 PID, COMMIT MODE, COMM\_NAME, statement 정보 등을 추가로 출력해야 합니다.

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

### BUG-51920 ORDER BY절에 LOB 타입을 사용시 비정상 종료 문제 수정

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
