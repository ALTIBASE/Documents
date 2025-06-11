Altibase 7.1.0.10.2 Patch Notes
===============================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-51299 MEMORY_INDEX_BUILD_RUN_SIZE 프로퍼티의 최대값을 4,294,967,295로 변경합니다.](#bug-51299)
    - [BUG-51443 디스크 DB 미디어 복구 중 메모리를 많이 사용하는 경우가 있습니다.](#bug-51443)
    - [BUG-51455 SQLAllocHandle()을 이용하여 환경 핸들을 할당할 때, umask 값을 0으로 설정하던 기존 동작을 변경합니다.](#bug-51455)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-51357 WITH절을 사용하는 쿼리에서 내부 쿼리와 외부 쿼리 모두 RANK() OVER(...) 함수에 동일한 alias를 사용하는 경우, 서버가 비정상 종료할 수 있습니다.](#bug-51357)
    - [BUG-51374 버퍼 래치가 해제되지 않아, 서버 종료 중 예외가 발생하는 문제를 수정하였습니다.](#bug-51374)
    - [BUG-51399 DB 구동시 상태 전이 단계에서 예외 발생시 altibase\_boot.log에 ERR-42000이 출력되는 문제를 수정하였습니다.](#bug-51399)
    - [BUG-51403 메모리 테이블에서 대량 LOB Insert 시, 성능 저하 문제를 수정하였습니다.](#bug-51403)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# New Features

### BUG-51299<a name=bug-51299></a> MEMORY_INDEX_BUILD_RUN_SIZE 프로퍼티의 최대값을 4,294,967,295로 변경합니다.

-   **module** : sm-mem-index

-   **Category** : Other

-   **재현 빈도** : Always

-   **설명** : MEMORY_INDEX_BUILD_RUN_SIZE 프로퍼티의 최대값을 변경합니다.
    -   변경 전 : 18,446,744,073,709,551,615 (2<sup>64</sup>-1)
    -   변경 후 : 4,294,967,295 (2<sup>32</sup>-1)
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

### BUG-51443<a name=bug-51443></a> 디스크 DB 미디어 복구 중 메모리를 많이 사용하는 경우가 있습니다.

-   **module** : sm

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : 디스크 DB 불완전 복구시 메모리를 많이 사용하는 문제를 개선했습니다.

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

### BUG-51455<a name=bug-51455></a> SQLAllocHandle()을 이용하여 환경 핸들을 할당할 때, umask 값을 0으로 설정하던 기존 동작을 변경합니다.

-   **module** : core

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : SQLAllocHandle()을 이용하여 환경 핸들을 할당할 때 umask 값이 0으로 변경되지 않도록 수정하였습니다.

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

### BUG-51357<a name=bug-51357></a> WITH절을 사용하는 쿼리에서 내부 쿼리와 외부 쿼리 모두 RANK() OVER(...) 함수에 동일한 alias를 사용하는 경우, 서버가 비정상 종료할 수 있습니다.

-   **module** : qp-select

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : WITH절을 사용하는 쿼리에서 내부 쿼리와 외부 쿼리 모두 RANK() OVER(...) 함수에 동일한 alias를 사용하는 경우, 서버가 비정상 종료되는 문제를 수정하였습니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    create table t1 ( i1 varchar(10) , i2 varchar(10) );
    ALTER SESSION SET STACK SIZE= 65536;
    WITH BASE AS (
    SELECT /*+ */A.i1 ,A.i2 ,RANK() OVER(ORDER BY i2) RNK
    FROM t1 A
    )
    SELECT ROW_RNK ,RANK() OVER(PARTITION BY i1 ORDER BY RNK DESC) RNK ,i1 ,i2
    FROM (
    SELECT A.i1 ,A.i2 ,A.RNK ROW_RNK ,RANK() OVER(PARTITION BY A.i1 ORDER BY A.i1 DESC) RNK
    FROM BASE A
    )
    ORDER BY ROW_RNK, RNK DESC;
    ```

  -   **수행 결과**

          [ERR-31455 : Failed to work because an internal exception occurred from an OS.[Contact Altibase's Support Center]]

  -   **예상 결과**

          no rows

- **Workaround**

  ```sql
  ALTER SESSION SET STACK SIZE= 65536;
  WITH BASE AS (
  SELECT /*+ */A.i1 ,A.i2 ,RANK() OVER(ORDER BY i2) RNK
  FROM t1 A
  )
  SELECT ROW_RNK ,RANK() OVER(PARTITION BY i1 ORDER BY RNK DESC) RNK2 ,i1 ,i2
  FROM (
  SELECT A.i1 ,A.i2 ,A.RNK ROW_RNK ,RANK() OVER(PARTITION BY A.i1 ORDER BY A.i1 DESC) RNK
  FROM BASE A
  )
  ORDER BY ROW_RNK, RNK2 DESC;
  ```

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-51374<a name=bug-51374></a> 버퍼 래치가 해제되지 않아, 서버 종료 중 예외가 발생하는 문제를 수정하였습니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : 버퍼 래치가 해제되지 않아, 서버 종료 중 예외가 발생하는 문제를 수정하였습니다.

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

### BUG-51399<a name=bug-51399></a> DB 구동시 상태 전이 단계에서 예외 발생시 altibase\_boot.log에 ERR-42000이 출력되는 문제를 수정하였습니다.

-   **module** : mm

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : DB 구동시 상태 전이 단계에서 예외 발생시
    altibase\_boot.log에 ERR-42000이 출력되는 문제를 수정하였습니다.

    - 수정 전 : 에러 메시지 없이 ERR-42000 만 표시

      [2025/03/19 15:35:04 82C] [PID:40062] [Thread-140190385456896] [LWP-40066]
      ERR-42000(errno=0)
    
    - 수정 후 : 에러 코드와 메시지가 함께 표시됨
    
      [2025/03/19 15:35:49 58E] [PID:60907] [Thread-140158181746432] [LWP-60920]
      ERR-4107a(errno=0) Unable to start up in the specified phase in the current state.
    
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

### BUG-51403<a name=bug-51403></a> 메모리 테이블에서 대량 LOB Insert 시, 성능 저하 문제를 수정하였습니다.

-   **module** : sm

-   **Category** : Other

-   **재현 빈도** : Always

-   **설명** : 메모리 테이블에서 대량의 LOB INSERT시 성능 저하 문제가 있었습니다. 이번 버그에서 해당 문제사항을 수정하였습니다.
    
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
| 7.1.0.10.2       | 6.5.1                   | 8.12.1       | 7.1.7               | 7.4.7                        |

> Altibase 7.1 패치 버전별 히스토리는 [Version_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.1/Altibase_7_1_Version_Histories.md) 에서 확인할 수 있다.

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

### 프로퍼티

추가/변경/삭제된 프로퍼티

### 성능 뷰

추가/변경/삭제된 성능뷰
