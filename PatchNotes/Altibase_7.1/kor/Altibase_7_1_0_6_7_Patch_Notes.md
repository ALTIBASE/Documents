<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  

- [Altibase 7.1.0.6.7 Patch Notes](#altibase-71067-patch-notes)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-49384 REMOTE\_BIND\_VARIABLE 함수에서 널(NULL) 값 바인드 시 ERR-21017 : The argument is not applicable. 에러가 발생합니다.](#bug-49384remote_bind_variable-%ED%95%A8%EC%88%98%EC%97%90%EC%84%9C-%EB%84%90null-%EA%B0%92-%EB%B0%94%EC%9D%B8%EB%93%9C-%EC%8B%9C-err-21017--the-argument-is-not-applicable-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-49417 디스크 인덱스 테이블스페이스 공간이 부족한 상황에서 디스크 테이블에 변경 트랜잭션 발생 시 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-49417%EB%94%94%EC%8A%A4%ED%81%AC-%EC%9D%B8%EB%8D%B1%EC%8A%A4-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%8A%A4%ED%8E%98%EC%9D%B4%EC%8A%A4-%EA%B3%B5%EA%B0%84%EC%9D%B4-%EB%B6%80%EC%A1%B1%ED%95%9C-%EC%83%81%ED%99%A9%EC%97%90%EC%84%9C-%EB%94%94%EC%8A%A4%ED%81%AC-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90-%EB%B3%80%EA%B2%BD-%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98-%EB%B0%9C%EC%83%9D-%EC%8B%9C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-49429 디스크 임시 테이블스페이스의 익스텐트(extent)크기가 512K가 아닌 경우 Altibase 서버가 비정상 종료합니다.](#bug-49429%EB%94%94%EC%8A%A4%ED%81%AC-%EC%9E%84%EC%8B%9C-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%8A%A4%ED%8E%98%EC%9D%B4%EC%8A%A4%EC%9D%98-%EC%9D%B5%EC%8A%A4%ED%85%90%ED%8A%B8extent%ED%81%AC%EA%B8%B0%EA%B0%80-512k%EA%B0%80-%EC%95%84%EB%8B%8C-%EA%B2%BD%EC%9A%B0-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Altibase 7.1.0.6.7 Patch Notes
==============================

Fixed Bugs
----------

### BUG-49384 REMOTE\_BIND\_VARIABLE 함수에서 널(NULL) 값 바인드 시 ERR-21017 : The argument is not applicable. 에러가 발생합니다.

-   **module** : dblink

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : 데이터베이스 링크(Database Link, DBLink)의 REMOTE\_BIND\_VARIABLE 함수에서 널(NULL) 값 바인드 시 ERR-21017 :
    The argument is not applicable. 에러가 발생하는 현상을 수정하였습니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    REMOTE_BIND_VARIABLE( 'link1', STATEMENT_ID, 1, NULL);
    ```

  - **수행 결과**

    ```sql
    [ERR-21017 : The argument is not applicable.
    In PROC1
    0013 :            RESULT := REMOTE_BIND_VARIABLE( 'link1', STATEMENT_ID, 1, NULL);
                     ^                                                                       ^
    ]
    ```

  -   **예상 결과**

          success

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49417 디스크 인덱스 테이블스페이스 공간이 부족한 상황에서 디스크 테이블에 변경 트랜잭션 발생 시 Altibase 서버가 비정상 종료할 수 있습니다.

-   **module** : sm-disk-index

-   **Category** : Fatal

-   **재현 빈도** : Rare

-   **설명** : 디스크 인덱스 테이블스페이스 공간이 부족한 상황에서 디스크 테이블에 변경 트랜잭션 발생 시 Altibase 서버가 비정상
    종료하는 현상을 수정합니다.
    
    본 버그로 인한 Altibase 서버 비정상 종료 발생 시 altibase\_error.log 에 아래와 같은 로그가 남습니다.
    
    ```bash
    IDE_ASSERT( sSegMgmtOp->mAllocNewPage( aStatistics, aMtx, aIndex->mIndexTSID, &(aIndex- >mSegmentDesc.mSegHandle),
    SDP_PAGE_INDEX_BTREE, (UChar **)aNewPage ) == IDE_SUCCESS ),
    [sdnbModule.cpp:23858], errno=[11]
    
    ERR-11123(errno=11) The tablespace does not have enough free space (
    TBS Name :tablespace_name ).
    ```
    
    디스크 인덱스 테이블스페이스에 여유 공간을 확보하여 Altibase 서버 비정상 종료 현상을 회피할 수 있습니다.
    
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

### BUG-49429 디스크 임시 테이블스페이스의 익스텐트(extent)크기가 512K가 아닌 경우 Altibase 서버가 비정상 종료합니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : 디스크 임시 테이블스페이스의 익스텐트(extent)크기가 512K가 아닌 경우 Altibase 서버가 비정상 종료하는 현상을
    수정하였습니다.
    
    - **발생 조건**
      - CREATE TEMPORARY TABLESPACE 구문 수행 시 
        - EXTENTSIZE 절에 512K 아닌 값을 사용하거나 
        - Altibase 서버 프로퍼티 SYS\_TEMP\_TBS\_EXTENT\_SIZE 또는 USER\_TEMP\_TBS\_EXTENT\_SIZE 값이 512K가 아닌 값으로 설정된 경우
      - 본 버그는 BUG-48369가 반영된 Altibase 7.1.0.5.1 이상에서 발생합니다.
    
    - **현상**
    
      디스크 임시 테이블스페이스를 사용하는 SQL 수행 시 Altibase 서버가 비정상 종료하며 트레이스 로그 altibase\_error.log에 아래와 같은 로그가 남습니다. 

      ```bash
      IDE_ASSERT( sExtDesc.mLength == SDT_WAEXTENT_PAGECOUNT )
      ```
    
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
-------

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    7.1.0.6.7     |          6.5.1          |    8.10.1    |        7.1.7        |            7.4.7             |

> Altibase 7.1 패치 버전별 히스토리는 [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7_1_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

> 패치를 롤백하려는 경우, [메타다운그레이드](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Installation.md#%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9Cmeta-downgrade)를 참고한다.

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

#### 변경된 성능 뷰

#### 삭제된 성능 뷰
