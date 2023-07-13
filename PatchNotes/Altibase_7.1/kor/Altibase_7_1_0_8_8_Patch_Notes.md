# Altibase 7.1.0.8.8 Patch Notes

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Fixed Bugs](#fixed-bugs)
    - [BUG-46720  100MB 이상의 LOB 타입 데이터를 디스크 테이블에 INSERT 할 때, 서버가 비정상 종료 합니다.](#bug-46720-100mb-%EC%9D%B4%EC%83%81%EC%9D%98-lob-%ED%83%80%EC%9E%85-%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%A5%BC-%EB%94%94%EC%8A%A4%ED%81%AC-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90-insert-%ED%95%A0-%EB%95%8C-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C-%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-49885  DatabaseMetaData의 getTables와 getColumns 메서드를 이용하여 테이블 및 칼럼의 주석(커멘트)를 가져오도록 개선합니다.](#bug-49885-databasemetadata%EC%9D%98-gettables%EC%99%80-getcolumns-%EB%A9%94%EC%84%9C%EB%93%9C%EB%A5%BC-%EC%9D%B4%EC%9A%A9%ED%95%98%EC%97%AC-%ED%85%8C%EC%9D%B4%EB%B8%94-%EB%B0%8F-%EC%B9%BC%EB%9F%BC%EC%9D%98-%EC%A3%BC%EC%84%9D%EC%BB%A4%EB%A9%98%ED%8A%B8%EB%A5%BC-%EA%B0%80%EC%A0%B8%EC%98%A4%EB%8F%84%EB%A1%9D-%EA%B0%9C%EC%84%A0%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-49944  DatabaseMetaData의 getImportedKeysgetExportedKeys 메서드의 DELETE_RULE 값이 부정확합니다.](#bug-49944-databasemetadata%EC%9D%98-getimportedkeysgetexportedkeys-%EB%A9%94%EC%84%9C%EB%93%9C%EC%9D%98-delete_rule-%EA%B0%92%EC%9D%B4-%EB%B6%80%EC%A0%95%ED%99%95%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50363  AltibaseDatabaseMetaData.getProcedureColumns(), getFuncionColumns()의 성능을 개선해야 합니다.](#bug-50363-altibasedatabasemetadatagetprocedurecolumns-getfuncioncolumns%EC%9D%98-%EC%84%B1%EB%8A%A5%EC%9D%84-%EA%B0%9C%EC%84%A0%ED%95%B4%EC%95%BC-%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50187  autocommit 모드가 off인 환경에서 UTRANS TIMEOUT 발생시, 에러 로그의 Last Query가 잘못 기록됩니다.](#bug-50187-autocommit-%EB%AA%A8%EB%93%9C%EA%B0%80-off%EC%9D%B8-%ED%99%98%EA%B2%BD%EC%97%90%EC%84%9C-utrans-timeout-%EB%B0%9C%EC%83%9D%EC%8B%9C-%EC%97%90%EB%9F%AC-%EB%A1%9C%EA%B7%B8%EC%9D%98-last-query%EA%B0%80-%EC%9E%98%EB%AA%BB-%EA%B8%B0%EB%A1%9D%EB%90%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50307  PSM에서 NVL 함수에 record type을 사용하면 서버가 비정상 종료할 수 있습니다.](#bug-50307-psm%EC%97%90%EC%84%9C-nvl-%ED%95%A8%EC%88%98%EC%97%90-record-type%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%98%EB%A9%B4-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-50312  prepare 에러 발생 후 비정상 종료 발생 시, 덤프 스택에 쿼리를 기록하도록 개선합니다.](#bug-50312-prepare-%EC%97%90%EB%9F%AC-%EB%B0%9C%EC%83%9D-%ED%9B%84-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C-%EB%B0%9C%EC%83%9D-%EC%8B%9C-%EB%8D%A4%ED%94%84-%EC%8A%A4%ED%83%9D%EC%97%90-%EC%BF%BC%EB%A6%AC%EB%A5%BC-%EA%B8%B0%EB%A1%9D%ED%95%98%EB%8F%84%EB%A1%9D-%EA%B0%9C%EC%84%A0%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50325  이중화에서 RECEIVE_ONLY 옵션관련 에러메시지의 오타를 수정합니다.](#bug-50325-%EC%9D%B4%EC%A4%91%ED%99%94%EC%97%90%EC%84%9C-receive_only-%EC%98%B5%EC%85%98%EA%B4%80%EB%A0%A8-%EC%97%90%EB%9F%AC%EB%A9%94%EC%8B%9C%EC%A7%80%EC%9D%98-%EC%98%A4%ED%83%80%EB%A5%BC-%EC%88%98%EC%A0%95%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50343  내부적으로 디스크 인덱스 페이지 재활용 작업 중에 잘못된 페이지를 삭제 시도 하다가 서버가 비정상 종료할 수 있습니다.](#bug-50343-%EB%82%B4%EB%B6%80%EC%A0%81%EC%9C%BC%EB%A1%9C-%EB%94%94%EC%8A%A4%ED%81%AC-%EC%9D%B8%EB%8D%B1%EC%8A%A4-%ED%8E%98%EC%9D%B4%EC%A7%80-%EC%9E%AC%ED%99%9C%EC%9A%A9-%EC%9E%91%EC%97%85-%EC%A4%91%EC%97%90-%EC%9E%98%EB%AA%BB%EB%90%9C-%ED%8E%98%EC%9D%B4%EC%A7%80%EB%A5%BC-%EC%82%AD%EC%A0%9C-%EC%8B%9C%EB%8F%84-%ED%95%98%EB%8B%A4%EA%B0%80-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-50354  3,4번째 pod에서 aku -p start를 하는 경우 데이터 불일치가 발생할 수 있습니다.](#bug-50354-34%EB%B2%88%EC%A7%B8-pod%EC%97%90%EC%84%9C-aku--p-start%EB%A5%BC-%ED%95%98%EB%8A%94-%EA%B2%BD%EC%9A%B0-%EB%8D%B0%EC%9D%B4%ED%84%B0-%EB%B6%88%EC%9D%BC%EC%B9%98%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-50356  v$repgap 에서 REP_GAP_SIZE가 잘못된 값이 나오는 경우가 있습니다.](#bug-50356-vrepgap-%EC%97%90%EC%84%9C-rep_gap_size%EA%B0%80-%EC%9E%98%EB%AA%BB%EB%90%9C-%EA%B0%92%EC%9D%B4-%EB%82%98%EC%98%A4%EB%8A%94-%EA%B2%BD%EC%9A%B0%EA%B0%80-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-50381  PSM에서 초기화 하지 않은 변수를 HASH 함수의 인자로 사용하는 경우, 서버가 비정상 종료 할 수 있습니다.](#bug-50381-psm%EC%97%90%EC%84%9C-%EC%B4%88%EA%B8%B0%ED%99%94-%ED%95%98%EC%A7%80-%EC%95%8A%EC%9D%80-%EB%B3%80%EC%88%98%EB%A5%BC-hash-%ED%95%A8%EC%88%98%EC%9D%98-%EC%9D%B8%EC%9E%90%EB%A1%9C-%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94-%EA%B2%BD%EC%9A%B0-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C-%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Fixed Bugs
==========

### BUG-46720  100MB 이상의 LOB 타입 데이터를 디스크 테이블에 INSERT 할 때, 서버가 비정상 종료 합니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : 100MB 이상의 LOB 타입 데이터를 디스크테이블에 INSERT 하려는 경우, LOB INDEX를 생성하는 과정에서 페이지 할당에 실패하는 문제가 있어 수정합니다.

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

### BUG-49885  DatabaseMetaData의 getTables와 getColumns 메서드를 이용하여 테이블 및 칼럼의 주석(커멘트)를 가져오도록 개선합니다.

-   **module** : mm-jdbc

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : DatabaseMetaData.getTables(), getColumns() 메소드의 remarks 칼럼에 테이블 및 칼럼의 주석정보를 리턴하도록 수정합니다.

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

### BUG-49944  DatabaseMetaData의 getImportedKeysgetExportedKeys 메서드의 DELETE_RULE 값이 부정확합니다.

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : DatabaseMetaData.getImportedKeys/getExportedKeys에서
    DELETE\_RULE값이 올바르게 리턴되지 않는 문제를 수정하였습니다.

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

### BUG-50363  AltibaseDatabaseMetaData.getProcedureColumns(), getFuncionColumns()의 성능을 개선해야 합니다.

-   **module** : mm-jdbc

-   **Category** : Efficiency

-   **재현 빈도** : Always

-   **설명** : AltibaseDatabaseMetaData의 일부 메소드의 성능을 개선시켰습니다.

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

### BUG-50187  autocommit 모드가 off인 환경에서 UTRANS TIMEOUT 발생시, 에러 로그의 Last Query가 잘못 기록됩니다.

-   **module** : mm

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : autocommit 모드가 off인 환경에서 utrans timeout 발생시, 에러 로그의 Last Query가 잘못 기록되는 문제를 수정합니다.

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

### BUG-50307  PSM에서 NVL 함수에 record type을 사용하면 서버가 비정상 종료할 수 있습니다.

-   **module** : qp-psm-trigger-pvo

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : PSM에서 NVL 함수의 인자로 record type을 사용하면, 서버가 비정상 종료 할 수 있는 문제를 수정합니다.

- **재현 방법**

  - **재현 절차**

        CREATE OR REPLACE PROCEDURE PROC1 AS
        TYPE REC_TYPE IS RECORD(C1 INTEGER, C2 INTEGER);
        VAR1 REC_TYPE;
        BEGIN
          VAR1 := NVL(VAR1, VAR1);
        END;
        /
        EXEC PROC1;

  -   **수행 결과**

          [ERR-91015 : Communication failure.]

  -   **예상 결과**

          [ERR-21017 : The argument is not applicable.

          In procedure SYS.PROC1
          0005 :   VAR1 := NVL(VAR1, VAR1);
                          ^              ^
          ]

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50312  prepare 에러 발생 후 비정상 종료 발생 시, 덤프 스택에 쿼리를 기록하도록 개선합니다.

-   **module** : mm

-   **Category** : Functionality

-   **재현 빈도** : Rare

-   **설명** : prepareProtocol 처리 중에 내부적으로 잘못된 메모리의 접근으로 인한 세그먼트 결함 발생시, 덤프 스택에 쿼리 정보가 누락되는 문제를 수정합니다.

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

### BUG-50325  이중화에서 RECEIVE_ONLY 옵션관련 에러메시지의 오타를 수정합니다.

-   **module** : rp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 7.1.0.8.5에 추가된 RECEIVE_ONLY 옵션과 관련된 에러메시지의 오타를 수정합니다.

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

### BUG-50343  내부적으로 디스크 인덱스 페이지 재활용 작업 중에 잘못된 페이지를 삭제 시도 하다가 서버가 비정상 종료할 수 있습니다.

-   **module** : sm-disk-index

-   **Category** : Fatal

-   **재현 빈도** : Rare

-   **설명** : 내부적으로 디스크 인덱스 페이지 재활용 작업중에 잘못된 페이지를 삭제할 수 있는 문제를 발견하여 개선하였습니다.

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

### BUG-50354  3,4번째 pod에서 aku -p start를 하는 경우 데이터 불일치가 발생할 수 있습니다.

-   **module** :

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** :  3,4번째 pod에서 aku -p start를 하는 경우의 데이터 불일치 문제를 해결하였습니다.

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

### BUG-50356  v$repgap 에서 REP_GAP_SIZE가 잘못된 값이 나오는 경우가 있습니다.

-   **module** : rp

-   **Category** : Functional Error

-   **재현 빈도** : Rare

-   **설명** : 이중화 갭(GAP)이 드물게 음수로 나오는 문제가 있어 수정하였습니다.

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

### BUG-50381  PSM에서 초기화 하지 않은 변수를 HASH 함수의 인자로 사용하는 경우, 서버가 비정상 종료 할 수 있습니다.

-   **module** : qp-dml-execute

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : PSM에서 초기화 하지 않은 변수를 HASH 함수의 인자로 사용하는 경우, 서버가 비정상 종료하는 문제를 해결합니다.

- **재현 방법**

  - **재현 절차**

        CREATE OR REPLACE PROCEDURE proc1
        AS
          v1 integer;
          v2 integer;
        BEGIN
          v2 := HASH(v1);
        END;
        /
        EXEC proc1;

  -   **수행 결과**

          [ERR-91015 : Communication failure.]

  -   **예상 결과**

          [ERR-21010 : Value overflow
          at "SYS.PROC1", line 6]

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
| 7.1.0.8.8        | 6.5.1                   | 8.11.1       | 7.1.7               | 7.4.7                        |

> Altibase 7.1 패치 버전별 히스토리는 [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.1/Altibase_7_1_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의
> 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는
> 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

> 패치를 롤백하려는 경우,
> [메타다운그레이드](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Installation%20Guide.md#%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9Cmeta-downgrade)를
> 참고한다.

#### CM protocol Version

통신 프로토콜 버전은 변경되지 않았다.

#### Replication protocol Version

Replication 프로토콜 버전은 변경되지 않았다.

> 알티베이스 샤딩 프로토콜 및 메타는 상위, 하위 호환성을 보장하지
> 않는다. 즉, 샤딩 버전이 다른 경우, 재구성해야 한다.

### 프로퍼티

#### 추가된 프로퍼티

#### 변경된 프로퍼티

#### 삭제된 프로퍼티

### 성능 뷰

#### 추가된 성능 뷰

#### 변경된 성능 뷰

#### 삭제된 성능 뷰
