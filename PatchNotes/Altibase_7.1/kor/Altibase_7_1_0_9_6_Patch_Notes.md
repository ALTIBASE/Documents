# Altibase 7.1.0.9.6 Patch Notes

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-50868 AKU 다중 이중화 지원 및 기능 개선](#bug-50868)
    - [BUG-50873 aku -p clean 동작 개선](#bug-50873)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-50864 로그 파일의 크기가 비정상적으로 변경된 경우, 잘못된 에러 메세지가 출력됩니다.](#bug-50864)
    - [BUG-50866 온라인 백업된 파일을 이용해서 복구를 시도할 때 MustRedo LSN까지의 로그파일이 없는 경우, 복구가 실패했음에도 불구하고 "Database media recovery successful"메시지를 출력합니다.](#bug-50866)
    - [BUG-50869 IPCDA 접속 과정에서 쓰레드 매니저가 행이 걸리는 현상이 발생합니다.](#bug-50869)
    - [BUG-50881 IPCDA 접속 중에 클라이언트가 종료하면 서버가 비정상 종료합니다.](#bug-50881)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-50868<a name=bug-50868></a> AKU 다중 이중화 지원 및 기능 개선

- **module** : aku

- **Category** : Enhancement

- **재현 빈도** : Always

- **설명** : AKU에서 이중화는 단일 일중화만 지원했으나, 이제 다중 이중화를 지원하도록 개선되었습니다. aku.conf 파일에 "Replication Properties" 설정에서 아래와 같이 다중 이중화를 설정할 수 있습니다.

  ```shell
  #=================================================================
  # Replication Properties
  #=================================================================
  REPLICATIONS = (
      REPLICATION_NAME_PREFIX = AKU_REP1
      SYNC_PARALLEL_COUNT     = 1
      (
          SYS.T1, SYS.T2, SYS.T3
      )
  ),
  (
      REPLICATION_NAME_PREFIX = AKU_REP2
      SYNC_PARALLEL_COUNT     = 1
      (
          SYS.T4, SYS.T5, SYS.T6
      )
  ),
  (
      REPLICATION_NAME_PREFIX = AKU_REP3
      SYNC_PARALLEL_COUNT     = 1
      (
          SYS.T7,
          SYS.T8,
          SYS.T9
      )
  )
  ```

  자세한 내용은 ***Utilitis 매뉴얼** - 3.aku* 에서 [이중화 테이블을 설정하는 방법](https://github.com/ALTIBASE/Documents/blob/79673b1851988b2954f2caada8d2ef40b409fcad/Manuals/Altibase_7.1/kor/Utilities%20Manual.md#altibase-%EC%9D%B4%EC%A4%91%ED%99%94-%ED%85%8C%EC%9D%B4%EB%B8%94-%EC%84%A4%EC%A0%95-%EB%B0%A9%EB%B2%95)을 참고하세요. 또한, 이중화 대상 테이블을 지정하는 방식에 "user\_name.table\_name"의 형식도 지원하도록 개선되었습니다.

  * 변경 전(기존)

    ```
    REPLICATIONS = (
        REPLICATION_NAME_PREFIX = "AKU_REP"
        SYNC_PARALLEL_COUNT     = 1
        (
            (
                USER_NAME      = "SYS"
                TABLE_NAME     = "T1"
            ),
            (
                USER_NAME      = "SYS"
                TABLE_NAME     = "T2"
            ),
            (
                USER_NAME      = "SYS"
                TABLE_NAME     = "T3"
            )
        )
    )
    ```

  * 변경 후 (기존의 설정방식도 지원하면서, 아래의 설정도 추가로 지원합니다.)

    ```
    REPLICATIONS = (
        REPLICATION_NAME_PREFIX = AKU_REP1
        SYNC_PARALLEL_COUNT     = 1
        (
            SYS.T1, SYS.T2, SYS.T3
        )
    )
    ```

- 그 외 기능 개선

  -   ALTIBASE\_NLS\_USE 환경 변수를 이용하여 Altibase 서버의
      문자집합과 동일한 문자집합을 사용 가능하도록 개선되었습니다.
      
  - aku.conf 파일 내 주석을 허용하도록 개선되었습니다.

  - 단일 쓰레드에서 순차적으로 실행되던 작업들이 이제 멀티 쓰레드를 사용하여 병렬로 수행되므로 AKU에서의 이중화 성능이 향상되었습니다.

  - AKU에서 이중화 생성할 때 REPLICATION_MAX_COUNT를 초과한 경우, 오류를 반환하도록 수정되었습니다.

  -   쿼리 수행 실패 시 재시도는 1초 대기 후 1회만 재시도하였으나,
      AKU\_QUERY\_RETRY\_COUNT 및 AKU\_QUERY\_RETRY\_DELAY\_MSEC
      프로퍼티를 이용하여 설정 가능하도록 변경되었습니다.

  - 마스터 파드의 장애로 `aku -p start` 명령 수행이 실패한 경우에 대한 조치 방법이 매뉴얼에 추가되었습니다. 자세한 내용은 ***Utilitis 매뉴얼** - 3.aku* 에서 [마스터 파드 장애로 aku -p start 명령 수행이 실패했을 때](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/Utilities%20Manual.md#4-%EB%A7%88%EC%8A%A4%ED%84%B0-%ED%8C%8C%EB%93%9C-%EC%9E%A5%EC%95%A0%EB%A1%9C-aku--p-start-%EB%AA%85%EB%A0%B9-%EC%88%98%ED%96%89%EC%9D%B4-%EC%8B%A4%ED%8C%A8%ED%96%88%EC%9D%84-%EB%95%8C)를 참고하세요.

  - 마스터 파드의 장애 복구 시에 마스터파드와 연결된 슬레이브 파드의 이중화 중 XSN이 -1인 것이 존재할 경우에 대한 예외처리가 추가되었습니다. 이 경우, 아래의 오류 메시지를 확인할 수 있습니다.

    ```
    The SLAVE server is detected to have failed. Check and perform a manual recovery.
    ```

- **재현 방법**

  -   **재현 절차**

  -   **수행 결과**

  -   **예상 결과**

- **Workaround**

- **변경사항**

  -   Performance view
  -   Property
      -   AKU_QUERY_RETRY_COUNT 프로퍼티 추가
          -   AKU 수행 중 쿼리 수행에 실패했을 때, 재시도 횟수
          -   기본값 : 5
          -   최소값 : 0
          -   최대값 : 2<sup>32</sup> - 1
      -   AKU_QUERY_RETRY_DELAY_MSEC 프로퍼티 추가
          -   AKU 수행 중 쿼리 수행에 실패하여 재시도 할 때, 다음
              재시도까지 대기 시간 ( msec 단위 )
          -   기본값 : 1000
          -   최소값 : 0
          -   최대값 : 2<sup>32</sup> - 1
  -   Compile Option
  -   Error Code

### BUG-50873<a name=bug-50873></a> aku -p clean 동작 개선

-   **module** : aku

-   **Category** : Functional Error

-   **재현 빈도** : Rare

-   **설명** : `aku -p clean` 수행시, 로컬 파드의 이중화 객체만 삭제되었는데, 이 경우 로컬파드와 관련된 모든 파드의 이중화는 중지되지 않는 문제가 있었습니다. 로컬 파드의 이중화 객체가 삭제되면, 삭제된 객체와 관련된 모든 파드의 이중화 객체가 중지되도록 개선되었습니다. 
    
    예를 들어, 4개의 파드로 구성된 환경에서 세번째 파드에서 `aku -p clean`을 수행하면,

    (기존) 세번째 파드의 이중화 객체 AKU_REP_03, AKU_REP_13, AKU_REP_23 의 객체에만 이중화 중지 및 삭제되었는데,
    
    (변경 후 ) 세번째 파드의 이중화 객체 AKU_REP_03, AKU_REP_13, AKU_REP_23 의 객체가 이중화 중지 및 삭제되고, 마스터 파드, 파드 1, 파드2 에 존재하는 AKU_REP_03, AKU_REP_13, AKU_REP_23 객체는 이중화 중지됩니다.
    
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

### BUG-50864<a name=bug-50864></a> 로그 파일의 크기가 비정상적으로 변경된 경우, 잘못된 에러 메세지가 출력됩니다.

-   **module** : sm

-   **Category** : Message Error

-   **재현 빈도** : Always

-   **설명** : 로그 파일의 크기가 비정상적으로 변경된 경우, [ERR-111AC : OS return Log file size is zero. (로그파일 경로 및 이)] 메시지가 출력되는 문제를 수정합니다. [ERR-111C1 : The log file size has changed. : (current file size: , expected file size: )]"의 에러메시지를 출력하도록 수정하였습니다.

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
        -   **0x111C1 (  70081) smERR_ABORT_WrongLogFileSize** The log file size has changed. : <0%s> (current file size:<1%u>, expected file size:<2%u>)
            -   **Cause**: The log file size has changed abnormally, so that the file is invalid.
            -   **Action**: Check if the backed-up file for the log file exists and restore it. If it's not available, contact Altibase's Support Center (http://support.altibase.com).

### BUG-50866<a name=bug-50866></a> 온라인 백업된 파일을 이용해서 복구를 시도할 때 MustRedo LSN까지의 로그파일이 없는 경우, 복구가 실패했음에도 불구하고 "Database media recovery successful"메시지를 출력합니다.

-   **module** : sm
-   **Category** : Fatal
-   **재현 빈도** : Always
-   **설명** : 온라인 백업된 파일을 이용해서 복구를 시도할 때 MustRedo LSN까지의 로그파일이 없는 경우, [ERR-91015 : Communication failure.] 에러를 출력하도록 수정하였습니다. 이 경우, altibase_boot.log 에 "Recovery failure, need more logfile ..."의 로그를 확인할 수 있습니다.
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

### BUG-50869<a name=bug-50869></a> IPCDA 접속 과정에서 쓰레드 매니저가 행이 걸리는 현상이 발생합니다.

-   **module** : cm

-   **Category** : Hang

-   **재현 빈도** : Always

-   **설명** : IPCDA 쓰레드 매니저(Thread Manager)와 서비스 쓰레드(Service Thread) 간에 동기가 맞지 않아 서버에서 행(HANG)이 발생하는 문제를 수정하였습니다.
    
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

### BUG-50881<a name=bug-50881></a> IPCDA 접속 중에 클라이언트가 종료하면 서버가 비정상 종료합니다.

-   **module** : cm

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : IPCDA 클라이언트 접속 중 (Handshake 프로토콜 처리 이전)에 클라이언트가 종료되면 서버가 비정상 종료하는 문제를 수정하였습니다.
    
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
| 7.1.0.9.6        | 6.5.1                   | 8.11.1       | 7.1.7               | 7.4.7                        |

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

#### 추가된 프로퍼티

#### 변경된 프로퍼티

#### 삭제된 프로퍼티

### 성능 뷰

#### 추가된 성능 뷰

#### 변경된 성능 뷰

#### 삭제된 성능 뷰
