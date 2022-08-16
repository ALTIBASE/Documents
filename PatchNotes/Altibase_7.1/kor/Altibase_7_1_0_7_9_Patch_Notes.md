

# Altibase 7.1.0.7.9 Patch Notes





# **Table of Contents** 

- [New Features](#new-features)
  - [BUG-49776 IPC 및 IPCDA 채널을 생성하는 데 필요한 공유 메모리와 세마포어의 키를 사용자가 정의한 값으로 설정하는 기능을 추가합니다.](#bug-49776ipc-%EB%B0%8F-ipcda-%EC%B1%84%EB%84%90%EC%9D%84-%EC%83%9D%EC%84%B1%ED%95%98%EB%8A%94-%EB%8D%B0-%ED%95%84%EC%9A%94%ED%95%9C-%EA%B3%B5%EC%9C%A0-%EB%A9%94%EB%AA%A8%EB%A6%AC%EC%99%80-%EC%84%B8%EB%A7%88%ED%8F%AC%EC%96%B4%EC%9D%98-%ED%82%A4%EB%A5%BC-%EC%82%AC%EC%9A%A9%EC%9E%90%EA%B0%80-%EC%A0%95%EC%9D%98%ED%95%9C-%EA%B0%92%EC%9C%BC%EB%A1%9C-%EC%84%A4%EC%A0%95%ED%95%98%EB%8A%94-%EA%B8%B0%EB%8A%A5%EC%9D%84-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
- [Fixed Bugs](#fixed-bugs)
  - [BUG-48767 같은 파티션 키 값으로 여러 세션에서 동시에 파티션을 분할할 때 최솟값과 최댓값이 동일한 파티션이 생성될 수 있습니다.](#bug-48767%EA%B0%99%EC%9D%80-%ED%8C%8C%ED%8B%B0%EC%85%98-%ED%82%A4-%EA%B0%92%EC%9C%BC%EB%A1%9C-%EC%97%AC%EB%9F%AC-%EC%84%B8%EC%85%98%EC%97%90%EC%84%9C-%EB%8F%99%EC%8B%9C%EC%97%90-%ED%8C%8C%ED%8B%B0%EC%85%98%EC%9D%84-%EB%B6%84%ED%95%A0%ED%95%A0-%EB%95%8C-%EC%B5%9C%EC%86%9F%EA%B0%92%EA%B3%BC-%EC%B5%9C%EB%8C%93%EA%B0%92%EC%9D%B4-%EB%8F%99%EC%9D%BC%ED%95%9C-%ED%8C%8C%ED%8B%B0%EC%85%98%EC%9D%B4-%EC%83%9D%EC%84%B1%EB%90%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-48882 파티션 테이블 대상으로 이중화 SYNC 수행 시 이중화 송신자 시작 이전 시점의 로그를 읽는 문제를 수정합니다.](#bug-48882%ED%8C%8C%ED%8B%B0%EC%85%98-%ED%85%8C%EC%9D%B4%EB%B8%94-%EB%8C%80%EC%83%81%EC%9C%BC%EB%A1%9C-%EC%9D%B4%EC%A4%91%ED%99%94-sync-%EC%88%98%ED%96%89-%EC%8B%9C-%EC%9D%B4%EC%A4%91%ED%99%94-%EC%86%A1%EC%8B%A0%EC%9E%90-%EC%8B%9C%EC%9E%91-%EC%9D%B4%EC%A0%84-%EC%8B%9C%EC%A0%90%EC%9D%98-%EB%A1%9C%EA%B7%B8%EB%A5%BC-%EC%9D%BD%EB%8A%94-%EB%AC%B8%EC%A0%9C%EB%A5%BC-%EC%88%98%EC%A0%95%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-48907 이중화 SET 절에서 예외 발생 시 메모리 누수가 발생할 수 있는 문제를 개선합니다.](#bug-48907%EC%9D%B4%EC%A4%91%ED%99%94-set-%EC%A0%88%EC%97%90%EC%84%9C-%EC%98%88%EC%99%B8-%EB%B0%9C%EC%83%9D-%EC%8B%9C-%EB%A9%94%EB%AA%A8%EB%A6%AC-%EB%88%84%EC%88%98%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A0-%EC%88%98-%EC%9E%88%EB%8A%94-%EB%AC%B8%EC%A0%9C%EB%A5%BC-%EA%B0%9C%EC%84%A0%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49524 ALTER TABLE table\_name MODIFY COLUMN 수행 시 테이블스페이스 공간 부족으로 에러 발생 시 예외 처리를 개선합니다.](#bug-49524alter-table-table_name-modify-column-%EC%88%98%ED%96%89-%EC%8B%9C-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%8A%A4%ED%8E%98%EC%9D%B4%EC%8A%A4-%EA%B3%B5%EA%B0%84-%EB%B6%80%EC%A1%B1%EC%9C%BC%EB%A1%9C-%EC%97%90%EB%9F%AC-%EB%B0%9C%EC%83%9D-%EC%8B%9C-%EC%98%88%EC%99%B8-%EC%B2%98%EB%A6%AC%EB%A5%BC-%EA%B0%9C%EC%84%A0%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49711 multiple update 수행 시 유일 키 제약조건이 위배될 때 발생하는 안정성 문제를 개선합니다.](#bug-49711multiple-update-%EC%88%98%ED%96%89-%EC%8B%9C-%EC%9C%A0%EC%9D%BC-%ED%82%A4-%EC%A0%9C%EC%95%BD%EC%A1%B0%EA%B1%B4%EC%9D%B4-%EC%9C%84%EB%B0%B0%EB%90%A0-%EB%95%8C-%EB%B0%9C%EC%83%9D%ED%95%98%EB%8A%94-%EC%95%88%EC%A0%95%EC%84%B1-%EB%AC%B8%EC%A0%9C%EB%A5%BC-%EA%B0%9C%EC%84%A0%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49773 PSM에서 EXECUTE IMMEDIATE 문에 INTO 절을 사용하지 않고 DEQUEUE 문을 수행할 때 ERR-4108A : Queue not found 에러가 발생할 수 있습니다.](#bug-49773psm%EC%97%90%EC%84%9C-execute-immediate-%EB%AC%B8%EC%97%90-into-%EC%A0%88%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%98%EC%A7%80-%EC%95%8A%EA%B3%A0-dequeue-%EB%AC%B8%EC%9D%84-%EC%88%98%ED%96%89%ED%95%A0-%EB%95%8C-err-4108a--queue-not-found-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-49779 라이브러리(library) 객체를 변경하면 해당 객체가 사용된 저장 패키지 바디를 컴파일이 필요한 상태로 변경해야 합니다.](#bug-49779%EB%9D%BC%EC%9D%B4%EB%B8%8C%EB%9F%AC%EB%A6%AClibrary-%EA%B0%9D%EC%B2%B4%EB%A5%BC-%EB%B3%80%EA%B2%BD%ED%95%98%EB%A9%B4-%ED%95%B4%EB%8B%B9-%EA%B0%9D%EC%B2%B4%EA%B0%80-%EC%82%AC%EC%9A%A9%EB%90%9C-%EC%A0%80%EC%9E%A5-%ED%8C%A8%ED%82%A4%EC%A7%80-%EB%B0%94%EB%94%94%EB%A5%BC-%EC%BB%B4%ED%8C%8C%EC%9D%BC%EC%9D%B4-%ED%95%84%EC%9A%94%ED%95%9C-%EC%83%81%ED%83%9C%EB%A1%9C-%EB%B3%80%EA%B2%BD%ED%95%B4%EC%95%BC-%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49786 디스크 인덱스 재구성 중 예외가 발생하여 트랜잭션 롤백 수행 시, 비활성화 상태의 인덱스 때문에 발생하는 안정성 문제를 개선합니다.](#bug-49786%EB%94%94%EC%8A%A4%ED%81%AC-%EC%9D%B8%EB%8D%B1%EC%8A%A4-%EC%9E%AC%EA%B5%AC%EC%84%B1-%EC%A4%91-%EC%98%88%EC%99%B8%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%98%EC%97%AC-%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98-%EB%A1%A4%EB%B0%B1-%EC%88%98%ED%96%89-%EC%8B%9C-%EB%B9%84%ED%99%9C%EC%84%B1%ED%99%94-%EC%83%81%ED%83%9C%EC%9D%98-%EC%9D%B8%EB%8D%B1%EC%8A%A4-%EB%95%8C%EB%AC%B8%EC%97%90-%EB%B0%9C%EC%83%9D%ED%95%98%EB%8A%94-%EC%95%88%EC%A0%95%EC%84%B1-%EB%AC%B8%EC%A0%9C%EB%A5%BC-%EA%B0%9C%EC%84%A0%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49796 Altibase 6.5.1 이하 버전의 JDBC 드라이버에서 Altibase 7.1의 성능 뷰 조회 시 That had return update result 에러가 발생합니다.](#bug-49796altibase-651-%EC%9D%B4%ED%95%98-%EB%B2%84%EC%A0%84%EC%9D%98-jdbc-%EB%93%9C%EB%9D%BC%EC%9D%B4%EB%B2%84%EC%97%90%EC%84%9C-altibase-71%EC%9D%98-%EC%84%B1%EB%8A%A5-%EB%B7%B0-%EC%A1%B0%ED%9A%8C-%EC%8B%9C-that-had-return-update-result-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49807 해시를 사용한 범위 파티션드 테이블 객체(RANGE\_USING\_HASH) 추출 시 aexport가 비정상 종료할 수 있습니다.](#bug-49807%ED%95%B4%EC%8B%9C%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%9C-%EB%B2%94%EC%9C%84-%ED%8C%8C%ED%8B%B0%EC%85%98%EB%93%9C-%ED%85%8C%EC%9D%B4%EB%B8%94-%EA%B0%9D%EC%B2%B4range_using_hash-%EC%B6%94%EC%B6%9C-%EC%8B%9C-aexport%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-49813 altierr 수행 시 불필요한 텍스트가 나오는 현상을 수정합니다.](#bug-49813altierr-%EC%88%98%ED%96%89-%EC%8B%9C-%EB%B6%88%ED%95%84%EC%9A%94%ED%95%9C-%ED%85%8D%EC%8A%A4%ED%8A%B8%EA%B0%80-%EB%82%98%EC%98%A4%EB%8A%94-%ED%98%84%EC%83%81%EC%9D%84-%EC%88%98%EC%A0%95%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49841 이중화 쌍의 이름이 다른 이중화 객체를 대상으로 BUILD OFFLINE META 구문 수행 시 The primary key column count of the replicated table does not match 에러가 발생합니다.](#bug-49841%EC%9D%B4%EC%A4%91%ED%99%94-%EC%8C%8D%EC%9D%98-%EC%9D%B4%EB%A6%84%EC%9D%B4-%EB%8B%A4%EB%A5%B8-%EC%9D%B4%EC%A4%91%ED%99%94-%EA%B0%9D%EC%B2%B4%EB%A5%BC-%EB%8C%80%EC%83%81%EC%9C%BC%EB%A1%9C-build-offline-meta-%EA%B5%AC%EB%AC%B8-%EC%88%98%ED%96%89-%EC%8B%9C-the-primary-key-column-count-of-the-replicated-table-does-not-match-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
  - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
  - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)



New Features
============

### BUG-49776 IPC 및 IPCDA 채널을 생성하는 데 필요한 공유 메모리와 세마포어의 키를 사용자가 정의한 값으로 설정하는 기능을 추가합니다.

-   **module** : cm-ipc

-   **Category** : Functionality

-   **재현 빈도** : Impossible

-   **설명** : IPC 및 IPCDA 채널을 생성하는 데 필요한 공유 메모리와 세마포어의 키를 사용자가 정의한 값으로 설정하는 기능을 추가합니다.
    사용자는 다음 4가지 프로퍼티를 사용하여 공유 메모리와 세마포어의 키를 설정할 수 있습니다.
    
    - IPC\_SEM\_KEY

    - IPC\_SHM\_KEY

    - IPCDA\_SEM\_KEY

    - IPCDA\_SHM\_KEY

    IPC와 IPCDA 채널은 Altibase 서버 구동 시 생성되는데, 공유 메모리/세마포어 키가 사용 중이거나 다른 이유로 공유 메모리/세마포어를 생성하지 못하면 Altibase 서버 구동은 실패합니다. 이때, Altibase 서버 트레이스 로그 altibase\_boot.log에서 시스템 에러(errno)를 확인하고 그에 따른 적절한 처리를 해야 합니다.

    프로퍼티 설명은 Altibase 7.1 [General Reference-1.Data Types & Altibase Properties](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/General%20Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#ipc_sem_key) 매뉴얼에서 확인할 수 있습니다.
    
-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
    
    -   Property
    
      -   [IPC_SEM_KEY](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/General%20Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#ipc_sem_key)
    
        - 설명
    
          IPC 채널을 생성하는 데 필요한 세마포어 키(key)를 사용자가 정의한 값으로 설정하는 프로퍼티이다.
    
          기본값은 0으로 Altibase 서버 프로세스의 프로세스 식별자(PID)를 기준으로 세마포어 키를 자동으로 생성한다. 0이 아닌 값을 설정하면 IPC\_SEM\_KEY 값을 기준으로 IPC\_SEM\_KEY부터 IPC\_SEM\_KEY + (IPC\_CHANNEL\_COUNT + 1)만큼의 연속된 세마포어 키를 사용하여 IPC 채널을 생성한다. +1은 SYS 사용자가 관리자 모드(sysdba)로 접속하기 위해 예약된 IPC 채널이다. 예를 들어 IPC\_SEM\_KEY 값이 10000이고 IPC\_CHANNEL\_COUNT 값이 1000이면 세마포어 키로 10000부터 11000까지 사용한다.
    
        - 속성
          읽기 전용, 공개
    
      -   [IPC_SHM_KEY](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/General%20Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#ipc_shm_key)
    
          - 설명
    
            IPC 채널을 생성하는 데 필요한 공유 메모리 키(key)를 사용자가 정의한 값으로 설정하는 프로퍼티이다.
    
            기본값은 0으로 Altibase 서버 프로세스의 프로세스 식별자(PID)를 기준으로 공유 메모리 키를 자동으로 생성한다. 0이 아닌 값을 설정하면 IPC\_SHM\_KEY 값을 공유 메모리 키로 사용한다.
    
          - 속성
    
            읽기 전용, 공개
    
      -   [IPCDA_SEM_KEY](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/General%20Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#ipcda_sem_key)
    
          -   설명
    
              IPCDA 채널을 생성하는 데 필요한 세마포어 키(key)를 사용자가 정의한 값으로 설정하는 프로퍼티이다.
    
              기본값은 0으로 Altibase 서버 프로세스의 프로세스 식별자(PID)를 기준으로 세마포어 키를 자동으로 생성한다. 0이 아닌 값을 설정하면 IPCDA\_SEM\_KEY 값을 기준으로 IPCDA\_SEM\_KEY부터 IPCDA\_SEM\_KEY + IPC\_CHANNEL\_COUNT만큼의 연속된 세마포어 키를 사용하여
              IPCDA 채널을 생성한다. 예를 들어 IPCDA\_SEM\_KEY 값이 10000이고 IPC\_CHANNEL\_COUNT 값이 1000이면 세마포어 키로 10000부터 10999까지 사용한다.
    
          -   속성
    
              읽기 전용, 공개
    
      -   [IPCDA_SHM_KEY](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/General%20Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#ipcda_shm_key)
    
        -   설명
    
          IPCDA 채널을 생성하는 데 필요한 공유 메모리 키(key)를 사용자가 정의한 값으로 설정하는 프로퍼티이다.
    
          기본값은 0으로 Altibase 서버 프로세스의 프로세스 식별자(PID)를 기준으로 공유 메모리 키를 자동으로 생성한다. 0이 아닌 값을 설정하면 IPCDA\_SHM\_KEY 값을 기준으로 연속된 키 2개를 공유 메모리 키로 사용한다. 예를 들어 IPCDA\_SHM\_KEY=10000이면 10000, 10001을 공유 메모리 키 값으로 사용한다.
    
        -   속성
    
            읽기 전용, 공개
    
    -   Compile Option
    
    -   Error Code
    
      에러 메시지 2 가지가 추가되었습니다. 
    
      - IPC와 IPCDA 채널 생성 시 Altibase 서버 프로퍼티에 정의된 키로 공유 메모리를 생성할 수 없을 때
    
        ```
        0x710C6 ( 463046) cmERR_ABORT_SHMGET_ERROR_WITH_KEY A system call error occurred while creating shared memory for
        <0%s>. [key : <1%u>]
        # *Cause: shmget() system call failed.
        # *Action: Check the errno and take an appropriate action. For example, if the errno is EEXIST, check the shared memory status. If there is a shared memory that has the same key value, remove the shared memory or retry with
        another key value.
      - IPC와 IPCDA 채널 생성 시 Altibase 서버 프로퍼티에 정의된 키로 세마포어를 생성할 수 없을 때
    
        ```
        0x710C7 ( 463047) cmERR_ABORT_SEMGET_ERROR_WITH_KEY A system call error occurred while creating semaphore for
        <0%s>. [key : <1%u>]
        # *Cause: semget() system call failed.
        # *Action: Check the errno and take an appropriate action. For example, if the errno is EEXIST, check the
        semaphore status. If there is a semaphore that has the same key value, remove the semaphore or retry with another key
        value.
        ```
    
      

Fixed Bugs
==========

### BUG-48767 같은 파티션 키 값으로 여러 세션에서 동시에 파티션을 분할할 때 최솟값과 최댓값이 동일한 파티션이 생성될 수 있습니다.

-   **module** : qp-ddl-dcl-pvo

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** :

    같은 파티션 키 값으로 여러 세션에서 동시에 파티션을 분할할 때, 동시성 문제로 최솟값과 최댓값이 동일한 파티션이 생성되는 현상을 수정합니다. SPLIT PARTITION 구문 실행 시점에 최솟값과 최댓값이 같으면 에러가 발생하도록 수정하였습니다.
    
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

### BUG-48882 파티션 테이블 대상으로 이중화 SYNC 수행 시 이중화 송신자 시작 이전 시점의 로그를 읽는 문제를 수정합니다.

-   **module** : rp

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : ALTER REPLICATION replication\_name SYNC TABLE \~ PARTITION 수행 시 이중화 송신자 시작 이전 시점의 로그를 읽는 문제를 수정합니다. 이 버그 현상 발생 시 이중화 대상 서버 간 데이터가 일치하지 않을 수 있습니다.
    
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

### BUG-48907 이중화 SET 절에서 예외 발생 시 메모리 누수가 발생할 수 있는 문제를 개선합니다.

-   **module** : rp

-   **Category** : Memory Error

-   **재현 빈도** : Always

-   **설명** : 다음과 같은 이중화 SET 절에서 예외 발생 시 메모리 누수가 발생할 수 있는 문제를 개선합니다.
    -   ALTER REPLICATION replication\_name SET PARALLEL '*parallelFactor*'
    -   ALTER REPLICATION replication\_name SET GROUPING ENABLE/DISABLE
    -   ALTER REPLICATION replication\_name SET OFFLINE ENABLE WITH 
    -   ALTER REPLICATION replication\_name SET GAPLESS ENABLE/DISABLE
    
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

### BUG-49524 ALTER TABLE table\_name MODIFY COLUMN 수행 시 테이블스페이스 공간 부족으로 에러 발생 시 예외 처리를 개선합니다.

-   **module** : qp

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : ALTER TABLE MODIFY COLUMN 수행 시 테이블스페이스 공간 부족으로 에러 발생 시 Altibase 서버가 비정상 종료하는 현상을 수정합니다.
    
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

### BUG-49711 multiple update 수행 시 유일 키 제약조건이 위배될 때 발생하는 안정성 문제를 개선합니다.

-   **module** : qp-dml-execute

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : multiple update 수행 시 유일 키 제약조건이 위배되면 Altibase 서버가 비정상 종료하는 현상을 수정합니다.
    
    이 버그는 아래 조건을 모두 만족할 때 발생합니다.
    
    - multiple update 문
    - 변경 대상 테이블에 유일 키 제약조건을 포함한 인덱스가 2개 이상 존재
    - 변경 값이 유일 키 제약조건을 위배할 때
    
-   **재현 방법**

    -   **재현 절차**

        ```sql
        CREATE TABLE T1( I1 CHAR(12),
                         I2 NUMBER(9,3),
                         I3 CHAR DEFAULT 'C',
                         I4 NUMBER(9,3))
         PARTITION BY RANGE( I1 )
         ( PARTITION P1 VALUES DEFAULT )
         TABLESPACE SYS_TBS_DISK_DATA;
        
        CREATE UNIQUE INDEX T1IDX ON T1 ( I2 DESC );
        ALTER TABLE T1 ADD CONSTRAINT T1_UK2 UNIQUE(I2,I3,I4);
        
        CREATE TABLE T2 ( I1 INTEGER, I2 INTEGER, I3 INTEGER ) TABLESPACE SYS_TBS_DISK_DATA;
        
        INSERT INTO T1(I2) VALUES (960);
        INSERT INTO T1(I2) VALUES (742);
        INSERT INTO T2 VALUES ( 2, 1, 1 );
        
        UPDATE T1,T2 SET T1.I2 = 10;
        ```

    -   **수행 결과**

            Altibase 서버 비정상 종료

    -   **예상 결과**

        ```sql
        [ERR-11058 : The row already exists in a unique index.]
        ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49773 PSM에서 EXECUTE IMMEDIATE 문에 INTO 절을 사용하지 않고 DEQUEUE 문을 수행할 때 ERR-4108A : Queue not found 에러가 발생할 수 있습니다.

-   **module** : qp-psm-trigger-execute

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : PSM에서 EXECUTE IMMEDIATE 문에 INTO 절을 사용하지 않고 DEQUEUE 문을 수행할 때 ERR-4108A : Queue not found 에러가 발생하는 현상을 수정합니다. 큐가 비어있는 상태에서 버그 발생 조건을 만족하면 세션에서 큐 정보를 삭제하는 문제를 수정하였습니다.
    
    이 버그는 아래의 순서대로 큐와 PSM을 생성하고 수행할 때 발생합니다. 실제 수행 예시는 재현 절차를 참고하세요.

    1. 큐 생성
    
    2. PSM 생성
          - DEQUEUE 문을 동적 SQL로 수행
          - EXECUTE IMMEDIATE 문에 INTO 절 사용하지 않음

    

    3) PSM 수행 

    4) 임의의 DDL 문 수행
    
    5) PSM 수행

-   **재현 방법**

    -   **재현 절차**

        ```sql
        CREATE QUEUE q1(1000);
        
        CREATE OR REPLACE PROCEDURE dq_test ()
        AS
            OUT1 VARCHAR(1000);
        BEGIN
            EXECUTE IMMEDIATE('DEQUEUE MESSAGE INTO OUT1 FROM q1');
            PRINTLN(OUT1);
        END;
        /
        
        EXEC dq_test;
        
        CREATE TABLE t1 (c1 INTEGER);
        
        EXEC dq_test;
        ```

    -   **수행 결과**

        ```sql
        [ERR-4108A : Queue not found
        ```

    -   **예상 결과**

        ```sql
        Execute success.
        ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49779 라이브러리(library) 객체를 변경하면 해당 객체가 사용된 저장 패키지 바디를 컴파일이 필요한 상태로 변경해야 합니다.

-   **module** : qp-psm-trigger-execute

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 라이브러리(library) 객체를 CREATE OR REPLACE 문으로 변경하면 해당 객체가 사용된 저장 패키지 바디를 컴파일이 필요한 상태(invalid)로 변경합니다.
    
-   **재현 방법**

    -   **재현 절차**

        ```sql
        CREATE OR REPLACE LIBRARY lib1 AS 'normal.so';
        
        CREATE OR REPLACE PACKAGE pkg1 AS
        PROCEDURE proc1( a1 IN VARCHAR(30), a2 OUT VARCHAR(30) );
        END;
        /
        
        CREATE OR REPLACE PACKAGE BODY pkg1 AS
        PROCEDURE proc1( a1 IN VARCHAR(30), A2 OUT VARCHAR(30) )
        AS
        LANGUAGE C
        LIBRARY lib1
        NAME "andy_upper";
        END;
        /
        
        CREATE OR REPLACE LIBRARY lib1 AS 'normal.so';
        
        SELECT USER_ID, PACKAGE_NAME, PACKAGE_TYPE, STATUS FROM SYSTEM_.SYS_PACKAGES_;
        ```

    -   **수행 결과**

        ```sql
        USER_ID     PACKAGE_NAME                    PACKAGE_TYPE STATUS
        --------------------------------------------------------------------------
        2           PKG1                            6           0
        2           PKG1                            7           0
        2 rows selected.
        ```

    -   **예상 결과**

        ```sql
        USER_ID     PACKAGE_NAME                    PACKAGE_TYPE STATUS
        --------------------------------------------------------------------------
        2           PKG1                            6           0
        2           PKG1                            7           1
        2 rows selected.
        ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49786 디스크 인덱스 재구성 중 예외가 발생하여 트랜잭션 롤백 수행 시, 비활성화 상태의 인덱스 때문에 발생하는 안정성 문제를 개선합니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : 디스크 인덱스 재구성 중 예외가 발생하여 트랜잭션 롤백 수행 시, 비활성화 상태의 인덱스 때문에 Altibase 서버가 비정상 종료하는 개선합니다.
    
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

### BUG-49796 Altibase 6.5.1 이하 버전의 JDBC 드라이버에서 Altibase 7.1의 성능 뷰 조회 시 That had return update result 에러가 발생합니다.

-   **module** : qp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : Altibase 6.5.1 이하 버전의 JDBC 드라이버에서 Altibase 7.1의 성능 뷰 조회 시 That had return update result 에러가 발생하는 현상을 수정합니다.
    
    Altibase 7.1 서버에서 OPTIMIZER\_PERFORMANCE\_VIEW 프로퍼티 값을 0으로 설정하여 버그 현상을 회피할 수 있습니다. OPTIMIZER\_PERFORMANCE\_VIEW 프로퍼티는 ALTER SYSTEM 문으로 변경할 수 있습니다. 이 프로퍼티 값을 0으로 변경 시 성능 뷰 조회 성능이 느려질  수 있습니다.

-   **재현 방법**

    -   **재현 절차**

        ```java
        Connection sConn = getConnection(aIp, aPort);
        try
        {
            Statement sStmt = sConn.createStatement();
            ResultSet sRs = sStmt.executeQuery("SELECT 1 FROM dual");
            if (sRs.next())
            {
                System.out.println("[SUCCESS] SELECT 1 FROM dual ==> " + sRs.getString(1));
            }
            sRs.close();
            sStmt.close();
        }
        catch (SQLException aEx)
        {
            System.out.println("[FAIL] " + aEx.getMessage());
        }
        sConn.close();
        ```

    -   **수행 결과**

            [FAIL] That had return update result

    -   **예상 결과**

            [SUCCESS] SELECT 1 FROM dual ==> 1

-   **Workaround**

    Altibase 7.1 서버에서 OPTIMIZER_PERFORMANCE_VIEW 프로퍼티 값을 0으로 설정합니다. ALTER SYSTEM 문으로 변경할 수 있습니다. OPTIMIZER_PERFORMANCE_VIEW 프로퍼티 값 변경 시 성능 뷰 조회 성능이 저하될 수 있습니다. 

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49807 해시를 사용한 범위 파티션드 테이블 객체(RANGE\_USING\_HASH) 추출 시 aexport가 비정상 종료할 수 있습니다.

-   **module** : ux-aexport

-   **Category** : Memory Error

-   **재현 빈도** : Rare

-   **설명** : 해시를 사용한 범위 파티션드 테이블 객체(RANGE\_USING\_HASH) 추출 시 aexport가 비정상 종료하는 현상을 개선합니다.
    
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

### BUG-49813 altierr 수행 시 불필요한 텍스트가 나오는 현상을 수정합니다.

-   **module** : sm

-   **Category** : Message Error

-   **재현 빈도** : Always

-   **설명** : altierr 수행 시 불필요한 텍스트가 나오는 현상을 수정합니다.

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

### BUG-49841 이중화 쌍의 이름이 다른 이중화 객체를 대상으로 BUILD OFFLINE META 구문 수행 시 The primary key column count of the replicated table does not match 에러가 발생합니다.

-   **module** : rp-jdbcAdapter

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : Adapter for JDBC 또는 Adapter for Oracle 수행 환경에서 Altibase 서버에 장애 발생 시 오프라인 옵션으로 미전송 로그를 대상 데이터베이스에 반영하는 과정에서 발생하는 버그입니다.
    
    BUILD OFFLINE META 구문 수행 시 송신자 메타 파일(*replication\_name*\_META\_NEW.bin, *replication\_name*\_META\_OLD.bin)의 정보를 정렬하는 기준과
    오프라인 옵션을 수행하는 서버의 이중화 대상 테이블의 정보를 정렬하는 기준이 달라 발생하는 문제를 수정합니다.
    
    이 버그 현상은 이중화 쌍의 이름이 다른 이중화 객체를 대상으로 BUILD OFFLINE META 구문 수행 시 발생합니다. 이중화 쌍의 이름이 다른 이중화 객체는 아래 예시처럼, 이중화 대상 테이블을 설정하는 FROM 절과 TO 절의 user\_name.table\_name이 다른 경우를 의미합니다.
    
    ```sql
    CREATE REPLICATION ala FOR ANALYSIS OPTIONS META_LOGGING WITH '127.0.0.1', 30300
      FROM test.tablea TO scott.tablea,
      FROM sys.tablebTO scott.tableb,
      FROM sys.tablecTO scott.tablec,
      FROM sys.tabledTO scott.tabled,
      FROM sys.tableeTO scott.tablee;
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
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    7.1.0.7.9     |          6.5.1          |    8.10.1    |        7.1.7        |            7.4.7             |

> Altibase 7.1 패치 버전별 히스토리는 [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.1/Altibase_7_1_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

> 패치를 롤백하려는 경우, [메타다운그레이드](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Installation%20Guide.md#%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9Cmeta-downgrade)를 참고한다.

#### CM protocol Version

통신 프로토콜 버전은 변경되지 않았다.

#### Replication protocol Version

Replication 프로토콜 버전은 변경되지 않았다.

### 프로퍼티

#### 추가된 프로퍼티

- [IPC_SEM_KEY](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/General%20Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#ipc_sem_key)
- [IPC_SHM_KEY](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/General%20Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#ipc_shm_key)
- [IPCDA_SEM_KEY](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/General%20Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#ipcda_sem_key)
- [IPCDA_SHM_KEY](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/General%20Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#ipcda_shm_key)

#### 변경된 프로퍼티

#### 삭제된 프로퍼티

### 성능 뷰

#### 추가된 성능 뷰

#### 변경된 성능 뷰

#### 삭제된 성능 뷰
