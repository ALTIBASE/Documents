Altibase 7.3.0.1.0 Patch Notes
==============================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Fixed Bugs](#fixed-bugs)
    - [BUG-51170 SM 모듈의 condition wait 의 Spurious wakeup 대응](#bug-51170)
    - [BUG-51277 통계 잠금 된 테이블에 통계 자료를 변경할 수 있는 문제를 수정합니다.](#bug-51277)
    - [BUG-51299 MEMORY_INDEX_BUILD_RUN_SIZE 프로퍼티의 최대값을 4,294,967,295로 변경합니다.](#bug-51299)
    - [BUG-51306 jdbcAdapter 및 oraAdapter에서 empty_clob() 또는 empty_blob() 입력을 null로 처리하던 문제를 수정하였습니다.](#bug-51306)
    - [BUG-51372 이중화 재 시작시 LOB 트랜잭션 로그 처리 오류 수정](#bug-51372)
    - [BUG-51374 버퍼 래치가 해제되지 않아, 서버 종료 중 예외가 발생하는 문제를 수정하였습니다.](#bug-51374)
    - [BUG-51399 DB 구동시 상태 전이 단계에서 예외 발생시 altibase\_boot.log에 ERR-42000이 출력되는 문제를 수정하였습니다.](#bug-51399)
    - [BUG-51403 메모리 테이블에서 대량 LOB Insert 시, 성능 저하 문제를 수정하였습니다.](#bug-51403)
    - [BUG-51408 Active 서버의 Sender에서 이중화 Handshake를 빠르게 시도할 경우, Standby 서버의 Receiver에서 Lock timeout이 빈번하게 발생하던 문제를 개선하였습니다.](#bug-51408)
    - [BUG-51417 APRE에서 FREE 구문은 더 이상 지원하지않습니다.](#bug-51417)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Fixed Bugs
==========

### BUG-51170<a name=bug-51170></a> SM 모듈의 condition wait 의 Spurious wakeup 대응

-   **module** : sm\_resource

-   **Category** : Fatal

-   **재현 빈도** : Rare

-   **설명** : pthread_cond_wait, pthread_cond_timewait 에서 spurious wakup 대응 코드를 보완하여, 의도하지 않은 동작을 수행하지 않도록 수정합니다.

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

### BUG-51277<a name=bug-51277></a> 통계 잠금 된 테이블에 통계 자료를 변경할 수 있는 문제를 수정합니다.

-   **module** : qp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 통계 잠금된 테이블의 특정 인덱스에 대해 통계 정보를 변경할 수 있는 문제를 수정했습니다.

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

### BUG-51299<a name=bug-51299></a> MEMORY\_INDEX\_BUILD\_RUN\_SIZE 프로퍼티의 최대값을 4,294,967,295로 변경합니다.

-   **module** : sm-mem-index

-   **Category** : Other

-   **재현 빈도** : Always

-   **설명** : MEMORY\_INDEX\_BUILD\_RUN\_SIZE 프로퍼티의 최대값을 변경합니다.
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
    -   BUG-51306 empty_clob(), empty_blob()을 입력할 경우, jdbcAdapter에서 잘못처리하는 문제를 수정합니다.

### BUG-51306<a name=bug-51306></a> jdbcAdapter 및 oraAdapter에서 empty_clob() 또는 empty_blob() 입력을 null로 처리하던 문제를 수정하였습니다.

-   **module** : rp-jdbcAdapter
-   **Category** : Functional Error
-   **재현 빈도** : Always
-   **설명** : jdbcAdapter 및 oraAdapter에서 empty_clob() 또는 empty_blob() 입력을 null로 처리하던 문제를 수정하였습니다. 단, target DB가 Altibase 인 경우에는 여전히 해당 입력이 null로 처리되는 제약이 있습니다.
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

### BUG-51372<a name=bug-51372></a> 이중화 재 시작시 LOB 트랜잭션 로그 처리 오류 수정

-   **module** : rp-sender

-   **Category** : Functional Error

-   **재현 빈도** : Rare

-   **설명** : 이중화 재시작이 발생하는 시점에서 송신자가 LOB 트랜잭션 로그를 전송할 때, 이미 처리된 로그를 제외하는 로직에 문제가 있었습니다. 이로 인해 전송되지 않아야 할 일부 LOB 트랜잭션 로그가 잘못 전송되었으며, 그 결과 수신자에서 "Transaction has not begun." 오류가 발생하는 문제가 있었습니다. 문제가 되는 로직을 개선하여, 불필요한 LOB 트랜잭션 로그가 전송되지 않도록 조치하였습니다.
    
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
    
- **재현 방법**

  -   **재현 절차**

  -   **수행 결과**

  -   **예상 결과**

- **Workaround**

- **변경사항**

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

### BUG-51408<a name=bug-51408></a> Active 서버의 Sender에서 이중화 Handshake를 빠르게 시도할 경우, Standby 서버의 Receiver에서 Lock timeout이 빈번하게 발생하던 문제를 개선하였습니다.

-   **module** : rp-sender

-   **Category** : Enhancement

-   **재현 빈도** : Frequence

-   **설명** : Active 서버의 Sender에서 이중화 Handshake를 빠르게 시도할 경우, Standby 서버의 Receiver에서 Lock timeout이 빈번하게 발생하던 문제를 개선하였습니다.

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

### BUG-51417<a name=bug-51417></a> APRE에서 FREE 구문은 더 이상 지원하지않습니다. 

-   **module** : mm-apre

-   **Category** : Other

-   **재현 빈도** : Always

-   **설명** : APRE에서 FREE 구문은 Altibase 5 이상에서는 지원하지 않아, 제거합니다. 
    
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
| 7.3.0.1.0        | 7.3.0                   | 9.4.1        | 7.1.8               | 7.4.9                        |

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
