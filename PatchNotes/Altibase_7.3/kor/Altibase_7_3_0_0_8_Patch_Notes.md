Altibase 7.3.0.0.8 Patch Notes
==============================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->

<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
  - [BUG-48885 통계 잠금 기능(LOCK_TABLE_STATS) 추가](#bug-48885)

- [Fixed Bugs](#fixed-bugs)
  - [BUG-50650 체크포인트 수행 중 내부적으로 Memory recovery LSN이 갱신되지 않은 상태에서 서버가 종료된 경우, 서버 재시작에 실패할 수 있습니다.](#bug-50650)
  - [BUG-51041 디스크 테이블에서 DML 을 수행하는 중에 내부적으로테이블 정보를 기록하는 페이지가 깨진 경우, 서버가 비정상 종료되는 문제가 있습니다.](#bug-51041)

- [Changes](#changes)
  - [Version Info](#version-info)
  - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
  - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
  - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-48885<a name=bug-48885></a> 통계 잠금 기능(LOCK_TABLE_STATS) 추가

-   **module** : sm

-   **Category** : Enhancement

-   **재현 빈도** : Always

- **설명** : 테이블의 통계를 잠글 수 있는 기능이 추가되었습니다. DBMS_STATS 패키지에 LOCK_TABLE_STATS, UNLOCK_TABLE_STATS 프로시저가 추가되었습니다. 이 프로시저를 이용하여 테이블의 통계를 잠그거나 잠금을 해제할 수 있습니다.

  통계 잠금이 설정된 테이블에 대해 GATHER_TABLE_STATS 로 통계 자료 수집을 시도할 경우, **[ERR-111C9 Table statistic(s) are locked.]** 오류 메시지를 확인할 수 있습니다.

-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    - Performance view
    
      - V$LOCK_TABLE_STATS 추가
    
        - 설명: 테이블 통계 잠금 상태를 보여주는 뷰
        - 칼럼 정보
    
          | Column name | Type       | Description                                                  |
          | ----------- | ---------- | ------------------------------------------------------------ |
          | TABLE_OID   | BIGINT     | 테이블 객체 식별자                                           |
          | STAT_LOCKED | VARCHAR(6) | 테이블 통계 잠금 여부</br>-NONE: 통계 잠금 해제 상태 </br>-LOCKED: 통계 잠금 상태 |
    - Property
    - Compile Option
    - Error Code
    
      -   추가
          -   **[ERR-111C9 Table statistic(s) are locked.]**
          -   **Cause**: Table statistic(s) have been locked.
          -   **Action**: Find the table whose statistic(s) are locked and then unlock the table using the UNLOCK_TABLE_STATS procedure.

Fixed Bugs
==========

### BUG-50650<a name=bug-50650></a> 체크포인트 수행 중 내부적으로 Memory recovery LSN이 갱신되지 않은 상태에서 서버가 종료된 경우, 서버 재시작에 실패할 수 있습니다.

-   **module** : sm-mem-recovery

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : 체크포인트 수행 중에 더티 페이지가 체크포인트 이미지 파일에 기록된 후 Memory recovery LSN이 갱신되기 전에 서버가 종료되면, 서버 재시작 시 복구에 실패하여 재시작이 실패하는 문제가 있었습니다. 이를 수정하여 Memory recovery LSN이 갱신되기 전에 서버가 종료되더라도, 서버 재 구동시 정상적으로 복구가 진행되도록 개선하였습니다.

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

### BUG-51041<a name=bug-51041></a> 디스크 테이블에서 DML 을 수행하는 중에 내부적으로테이블 정보를 기록하는 페이지가 깨진 경우, 서버가 비정상 종료되는 문제가 있습니다.

-   **module** : sm

-   **Category** : Enhancement

-   **재현 빈도** : Unknown

-   **설명** : 디스크 테이블에서 DML을 수행하는 중에 내부적으로 테이블
    정보를 기록하는 페이지가 깨진 경우, 페이지 덤프와 같이 분석 가능한
    정보를 기록하고 예외가 발생하도록 수정되었습니다.

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
| 7.3.0.0.8        | 7.3.0                   | 9.4.1        | 7.1.8               | 7.4.9                        |

> Altibase 7.3 패치 버전별 히스토리는 [Version_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.3/Altibase_7_3_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의
> 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는
> 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전이 9.3.1에서 9.4.1로 변경되었다.

> 패치를 롤백하려는 경우, [메타다운그레이드](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Installation%20Guide.md#%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9Cmeta-downgrade)를 참고한다.

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

V$LOCK_TABLE_STATS

#### 변경된 성능 뷰

#### 삭제된 성능 뷰
