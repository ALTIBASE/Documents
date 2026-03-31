Altibase 7.3.0.1.8 Patch Notes
================================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-52188 비정상 종료 시 진단 덤프 정보 수집 안정성 개선](#bug-52188)
    - [BUG-52192 파일 백업 과정에서 시스템 콜 호출 실패 시 오류 메시지 개선](#bug-52192)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-51201 이중화 대상 파티션이 PK를 기준으로 나뉘어있지 않은 경우, 파티션의 순서에 따라 XLog 반영 순서가 역전될 수 있습니다.](#bug-51201)
    - [BUG-51324 디스크 인덱스 통계정보 병렬 수집 시 성능 저하 문제 수정](#bug-51324)
    - [BUG-52171 SQL 함수를 사용하는 트리거가 있는 테이블의 이름을 변경할 때 서버 비정상 종료 문제 수정](#bug-52171)
    - [BUG-52119 SUPPLEMENTAL LOG 활성화 상태에서 jdbcAdapter를 통해 이중화 대상 테이블에 반영하는 과정에서, UPDATE 실패 문제 수정](#bug-52119)
    - [BUG-52205 이중화 환경에서 오프라인 이중화 관련 메타 정보를 업데이트하는 과정 중 발생하던 메모리 접근 오류 수정](#bug-52205)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-52188<a name=bug-52188></a> 비정상 종료 시 진단 덤프 정보 수집 안정성 개선

-   **module** : mm

-   **Category** : Reliability

-   **재현 빈도** : Rare

-   **설명** : 비정상 종료 시 특정 상황에서 세션 및 태스크 진단 정보가 누락되던 오류를 수정했습니다.
    또한 장애 분석에 도움이 되도록 통신 읽기 버퍼와 서비스 스레드 Statement ID 정보도 함께 덤프하도록 개선하였습니다.

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

### BUG-52192<a name=bug-52192></a> 파일 백업 과정에서 시스템 콜 호출 실패 시 오류 메시지 개선

-   **module** : sm

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : 기존에는 파일 백업 과정에서 시스템 콜 호출 실패가 발생하더라도 로그에 상세 정보가 충분히 기록되지 않아 정확한 원인을 파악하기 어려웠습니다. 이제는 오류 발생시 실패한 시스템 콜 호출 정보를 포함한 보다 상세한 오류 메시지가 출력되도록 개선하였습니다.

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

### BUG-51201<a name=bug-51201></a> 이중화 대상 파티션이 PK를 기준으로 나뉘어있지 않은 경우, 파티션의 순서에 따라 XLog 반영 순서가 역전될 수 있습니다.

-   **module** : rp-jdbcAdapter

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : Active 서버의 이중화 대상 파티션이 PK를 기준으로
    나뉘어있지 않은 경우, 파티션의 순서에 따라 어댑터에서 반영하는
    XLog의 순서가 역전될 수 있는 것을 수정했습니다.

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

### BUG-51324<a name=bug-51324></a> 디스크 인덱스 통계정보 병렬 수집 시 성능 저하 문제 수정

-   **module** : sm

-   **Category** : Other

-   **재현 빈도** : Always

-   **설명** : 디스크 인덱스 통계정보 수집을 병렬로 수행할 때 수행시간이 더 소모되는 문제를 수정했습니다.
    
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

### BUG-52171<a name=bug-52171></a> SQL 함수를 사용하는 트리거가 있는 테이블의 이름을 변경할 때 서버 비정상 종료 문제 수정

-   **module** : qp-psm-trigger-execute

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : SQL 함수를 사용하는 트리거가 있는 테이블의 이름을 변경할 때 서버가 비정상 종료할 수 있는 문제를 수정했습니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    create table t1 (c1 integer);
    create or replace trigger trig_on_t1
    before insert on t1
    referencing new as new_row
    for each row
    as
    var1 varchar(10);
    begin
      var1 := nvl('a', 'a');
    end;
    /
    rename t1 to tx;
    ```

  -   **수행 결과**

          [ERR-91015 : Communication failure.]

  -   **예상 결과**

          Rename success.

- **Workaround**

  트리거를 제거(Drop)하고, 테이블의 이름을 변경한 다음 다시 트리거를 생성한다.

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-52119<a name=bug-52119></a> SUPPLEMENTAL LOG 활성화 상태에서 jdbcAdapter를 통해 이중화 대상 테이블에 반영하는 과정에서, UPDATE 실패 문제 수정

-   **module** : rp-jdbcAdapter

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : SUPPLEMENTAL LOG 활성화 상태에서 jdbcAdapter를 통해 이중화 대상 테이블에 반영하는 과정에서, UPDATE 수행 시 PK 업데이트 오류가 발생하는 문제를 수정합니다.

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

### BUG-52205<a name=bug-52205></a> 이중화 환경에서 오프라인 이중화 관련 메타 정보를 업데이트하는 과정 중 발생하던 메모리 접근 오류 수정

-   **module** : rp

-   **Category** : Memory Error

-   **재현 빈도** : Always

-   **설명** : 이중화 환경에서 오프라인 이중화 관련 메타 정보를 업데이트하는 과정 중 발생하던 메모리 접근 오류 수정했습니다.

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
| 7.3.0.1.8        | 7.3.0                   | 9.4.1        | 7.1.8               | 7.4.9                        |

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
