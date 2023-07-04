# Altibase 7.1.0.8.7 Patch Notes

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-48520  네트워크 관련 에러메시지를 altibase_cm.log에 기록하게 설정할 수 있습니다.](#bug-48520-%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC-%EA%B4%80%EB%A0%A8-%EC%97%90%EB%9F%AC%EB%A9%94%EC%8B%9C%EC%A7%80%EB%A5%BC-altibase_cmlog%EC%97%90-%EA%B8%B0%EB%A1%9D%ED%95%98%EA%B2%8C-%EC%84%A4%EC%A0%95%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-50287  aku -p start 성공 후 지정 시간만큼 대기하는 기능을 추가합니다.](#bug-50287-aku--p-start-%EC%84%B1%EA%B3%B5-%ED%9B%84-%EC%A7%80%EC%A0%95-%EC%8B%9C%EA%B0%84%EB%A7%8C%ED%81%BC-%EB%8C%80%EA%B8%B0%ED%95%98%EB%8A%94-%EA%B8%B0%EB%8A%A5%EC%9D%84-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50293  iSQL에서 잘못된 사용자 아이디 또는 암호로 접속을 시도할 때 출력되는 에러메시지를 "Invalid User ID or Password"로 변경할 수 있습니다.](#bug-50293-isql%EC%97%90%EC%84%9C-%EC%9E%98%EB%AA%BB%EB%90%9C-%EC%82%AC%EC%9A%A9%EC%9E%90-%EC%95%84%EC%9D%B4%EB%94%94-%EB%98%90%EB%8A%94-%EC%95%94%ED%98%B8%EB%A1%9C-%EC%A0%91%EC%86%8D%EC%9D%84-%EC%8B%9C%EB%8F%84%ED%95%A0-%EB%95%8C-%EC%B6%9C%EB%A0%A5%EB%90%98%EB%8A%94-%EC%97%90%EB%9F%AC%EB%A9%94%EC%8B%9C%EC%A7%80%EB%A5%BC-invalid-user-id-or-password%EB%A1%9C-%EB%B3%80%EA%B2%BD%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-50341  prepare시 error 발생한 query에 대해 로깅하는 기능 추가](#bug-50341-prepare%EC%8B%9C-error-%EB%B0%9C%EC%83%9D%ED%95%9C-query%EC%97%90-%EB%8C%80%ED%95%B4-%EB%A1%9C%EA%B9%85%ED%95%98%EB%8A%94-%EA%B8%B0%EB%8A%A5-%EC%B6%94%EA%B0%80)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-48092  시퀀스의 minvalue 와 maxvalue가 음수인 경우, 시퀀스의 cycle 옵션을 변경한 뒤 서버를 재시작 하면 잘못 시퀀스값을 반환합니다.](#bug-48092-%EC%8B%9C%ED%80%80%EC%8A%A4%EC%9D%98-minvalue-%EC%99%80-maxvalue%EA%B0%80-%EC%9D%8C%EC%88%98%EC%9D%B8-%EA%B2%BD%EC%9A%B0-%EC%8B%9C%ED%80%80%EC%8A%A4%EC%9D%98-cycle-%EC%98%B5%EC%85%98%EC%9D%84-%EB%B3%80%EA%B2%BD%ED%95%9C-%EB%92%A4-%EC%84%9C%EB%B2%84%EB%A5%BC-%EC%9E%AC%EC%8B%9C%EC%9E%91-%ED%95%98%EB%A9%B4-%EC%9E%98%EB%AA%BB-%EC%8B%9C%ED%80%80%EC%8A%A4%EA%B0%92%EC%9D%84-%EB%B0%98%ED%99%98%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50069  서버 미기동 상태에서 isql -sysdba 접속시 발생하는 [ERR-910FB : Connected to idle instance]의 메시지를 [Connected to idle instance] 메시지로 변경합니다.](#bug-50069-%EC%84%9C%EB%B2%84-%EB%AF%B8%EA%B8%B0%EB%8F%99-%EC%83%81%ED%83%9C%EC%97%90%EC%84%9C-isql--sysdba-%EC%A0%91%EC%86%8D%EC%8B%9C-%EB%B0%9C%EC%83%9D%ED%95%98%EB%8A%94-err-910fb--connected-to-idle-instance%EC%9D%98-%EB%A9%94%EC%8B%9C%EC%A7%80%EB%A5%BC-connected-to-idle-instance-%EB%A9%94%EC%8B%9C%EC%A7%80%EB%A1%9C-%EB%B3%80%EA%B2%BD%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50097  iloader -direct 옵션에 잘못된 값을 사용하는 경우에 대한 오류처리가 되어 있지 않습니다.](#bug-50097-iloader--direct-%EC%98%B5%EC%85%98%EC%97%90-%EC%9E%98%EB%AA%BB%EB%90%9C-%EA%B0%92%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%98%EB%8A%94-%EA%B2%BD%EC%9A%B0%EC%97%90-%EB%8C%80%ED%95%9C-%EC%98%A4%EB%A5%98%EC%B2%98%EB%A6%AC%EA%B0%80-%EB%90%98%EC%96%B4-%EC%9E%88%EC%A7%80-%EC%95%8A%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-50304  JDBC 드라이버에서 CM 프로토콜 헤더의 패킷 시퀀스의 순환이 고려되지 않아, Invalid packet sequence number 오류가 발생합니다.](#bug-50304-jdbc-%EB%93%9C%EB%9D%BC%EC%9D%B4%EB%B2%84%EC%97%90%EC%84%9C-cm-%ED%94%84%EB%A1%9C%ED%86%A0%EC%BD%9C-%ED%97%A4%EB%8D%94%EC%9D%98-%ED%8C%A8%ED%82%B7-%EC%8B%9C%ED%80%80%EC%8A%A4%EC%9D%98-%EC%88%9C%ED%99%98%EC%9D%B4-%EA%B3%A0%EB%A0%A4%EB%90%98%EC%A7%80-%EC%95%8A%EC%95%84-invalid-packet-sequence-number-%EC%98%A4%EB%A5%98%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50309  디스크 인덱스 빌드시 쓰레드당 SORT AREA SIZE가 큰 경우 빌드에 실패합니다.](#bug-50309-%EB%94%94%EC%8A%A4%ED%81%AC-%EC%9D%B8%EB%8D%B1%EC%8A%A4-%EB%B9%8C%EB%93%9C%EC%8B%9C-%EC%93%B0%EB%A0%88%EB%93%9C%EB%8B%B9-sort-area-size%EA%B0%80-%ED%81%B0-%EA%B2%BD%EC%9A%B0-%EB%B9%8C%EB%93%9C%EC%97%90-%EC%8B%A4%ED%8C%A8%ED%95%A9%EB%8B%88%EB%8B%A4)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-48520  네트워크 관련 에러메시지를 altibase_cm.log에 기록하게 설정할 수 있습니다.

-   **module** : mm

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : NETWORK\_ERROR\_LOG\_FILE 프로퍼티를 통해 네트워크 관련 에러메시지가 기록되는 로그를 변경할 수 있습니다. 디폴트는 altibase_boot.log에 기록됩니다. 이 프로퍼티의 값을 1로 변경하면, altibase_cm.log에 기록합니다.

-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
        -   추가
            -   NETWORK\_ERROR\_LOG\_FILE
                -   0: 네트워크 관련 에러메시지가 altibase_boot.log에 기록되도록 설정
                -   1: 네트워크 관련 에러메시지가 altibase_cm.log에 기록되도록 설정

    -   Compile Option
    -   Error Code

### BUG-50287  aku -p start 성공 후 지정 시간만큼 대기하는 기능을 추가합니다.

-   **module** :

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : aku -p start 시 slave pod 인 경우 이중화 동작 완료 후 ADMIN_MODE를 0으로 변경하기 전에 일정 시간 대기하는 기능이 추가되었습니다. AKU_DELAY_START_COMPLETE_TIME에 설정된 시간만큼 대기합니다.

-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
        -   추가
            -   AKU_DELAY_START_COMPLETE_TIME
                -   기본값: 0
    -   Compile Option
    -   Error Code

### BUG-50293  iSQL에서 잘못된 사용자 아이디 또는 암호로 접속을 시도할 때 출력되는 에러메시지를 "Invalid User ID or Password"로 변경할 수 있습니다.

-   **module** : ux-isql

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : iSQL에서 잘못된 사용자 아이디 또는 암호로 접속을 시도하면, [ERR-31010 : User not found] 또는 [ERR-4102E : Invalid password]와 같이 상세한 접속 실패 이유가 출력됩니다. 그런데, 이렇게 상세한 접속 실패 에러메시지 대신에 [ERR-91149 : Invalid UserID or Password] 가 출력되도록 설정 할 수 있습니다.

    [ISQL_SECURE_LOGIN_MSG](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/iSQL%20User's%20Manual.md#isql_secure_login_msg) 프로퍼티를 1로 설정하면, 사용자 아이디 또는 암호가 틀린 경우, [ERR-91149 : Invalid UserID or Password] 에러메시지가 출력됩니다.

    예)

    ```
    export ISQL_SECURE_LOGIN_MSG=1
    ```

-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
        -   추가
            -   [ISQL_SECURE_LOGIN_MSG](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/iSQL%20User's%20Manual.md#isql_secure_login_msg)
                -   0 : 기존과 동일하게 명확한 접속 실패 이유의 에러메시지가 출력된다. (기본설정)
                -   1: 사용자 아이디 또는 암호가 틀린 경우, [ERR-91149 : Invalid UserID or Password] 에러메시지가 출력된다.
    -   Compile Option
    -   Error Code

### BUG-50341  prepare시 error 발생한 query에 대해 로깅하는 기능 추가

- **module** : qp

- **Category** : Enhancement

- **재현 빈도** : Always

- **설명** : prepare시 error 발생한 query에 대해 로깅하는 기능 추가하였습니다. QP_MSGLOG_FLAG 프로퍼티를 66으로 변경하면, 로깅이 시작됩니다.

  ```
  alter system set QP_MSGLOG_FLAG = 66;
  ```

-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

- **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

Fixed Bugs
==========

### BUG-48092  시퀀스의 minvalue 와 maxvalue가 음수인 경우, 시퀀스의 cycle 옵션을 변경한 뒤 서버를 재시작 하면 잘못 시퀀스값을 반환합니다.

-   **module** : sm

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 시퀀스의 minvalue와 maxvalue가 음수인 경우, 시퀀스의 cycle 옵션을 수정한 다음 서버를 재시작하면, 잘못된 시퀀스 값을 반환하는 문제를 수정합니다.

- **재현 방법**

  -   **재현 절차**

          create sequence s2 minvalue -20 maxvalue -1;
          select s2.nextval;
          select s2.nextval;
          alter sequence s2 cycle;
          alter sequence s2 nocycle;
          -- server restart
          select s2.nextval;

  - **수행 결과**

        NEXTVAL
        -----------------------
        -19
        1 row selected.

  -   **예상 결과**

          [ERR-11044 : Sequence upper bound exceeded]

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50069  서버 미기동 상태에서 isql -sysdba 접속시 발생하는 [ERR-910FB : Connected to idle instance]의 메시지를 [Connected to idle instance] 메시지로 변경합니다.

-   **module** : ux-isql

-   **Category** : Usability

-   **재현 빈도** : Always

-   **설명** : 서버 미기동 상태에서 isql -sysdba 접속시 발생하는 [ERR-910FB : Connected to idle instance] 메세지를 [Connected to idle instance] 메시지로 변경합니다.

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

### BUG-50097  iloader -direct 옵션에 잘못된 값을 사용하는 경우에 대한 오류처리가 되어 있지 않습니다.

-   **module** : ux-iloader

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : iloader -direct 옵션에 잘못된 값을 사용하는 경우에 대한 오류처리가 되어 있지 않습니다. 이 경우 -direct 옵션에 잘못된 값은 무시하고 동작되는데, 그 뒤에 나열된 옵션들의 동작도 무시되는 문제가 있습니다. 잘못된 값이 사용되면 [ERR-9103B : Invalid option ] 에러메시지가 출력되도록 수정하였습니다.

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

### BUG-50304  JDBC 드라이버에서 CM 프로토콜 헤더의 패킷 시퀀스의 순환이 고려되지 않아, Invalid packet sequence number 오류가 발생합니다.

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : Altibase 프로토콜은 여러 개의 패킷으로 전송될 수 있는데, 각 패킷을 구분하기 위해 패킷 시퀀스 번호가 프로토콜 헤더에 포함되어 있습니다. 패킷 시퀀스는 단일 세션 내 패킷의 고유 일렬번호인데,  0부터 2,147,483,647(Interger.MAX_VALUE) 사이에서 순차적으로 증가하여 순환되며, 세션이 종료되면 초기화됩니다. 그런데 장시간 세션을 종료하지 않는 경우, 패킷 시퀀스가 최대치까지 증가할 수 있습니다. 최대치까지 증가하는 경우 시퀀스가 순환되어 사용되어야 하는데, JDBC 드라이버에서는 패킷 시퀀스의 순환이 고려되지 않아 Invalid packet sequence number 오류가 발생합니다. JDBC 드라이버에서 패킷 시퀀스가 순환되도록  수정하였습니다.

    본 버그를 적용하려면, Altibase JDBC 드라이버를 패치해야 합니다.

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

### BUG-50309  디스크 인덱스 빌드시 쓰레드당 SORT AREA SIZE가 큰 경우 빌드에 실패합니다.

-   **module** : sm-disk-index

-   **Category** : Other

-   **재현 빈도** : Always

-   **설명** : 디스크 인덱스 빌드시

    빌드쓰레드당 SORT AREA SIZE 가 UINT MAX (4G-1 bytes) 를
    넘어가면 빌드에 실패합니다.

    빌드쓰레드당 SORT AREA SIZE 가 최대 UNIT MAX 로 제한되도록
    수정합니다.

-   **재현 방법**

    -   **재현 절차**

            alter system set SORT_AREA_SIZE = 21474836480;
            alter system set INDEX_BUILD_THREAD_COUNT = 1;
            create table t (id int) tablespace sys_tbs_disk_data;
            insert into t values (1);
            create index i on t ( id);

    -   **수행 결과**

            [ERR-41082 : Internal server error (mmcStatement::execute code=0x42000000 )]

    -   **예상 결과**

            Create success.

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
| 7.1.0.8.7        | 6.5.1                   | 8.11.1       | 7.1.7               | 7.4.7                        |

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

> 알티베이스 샤딩 프로토콜 및 메타는 상위, 하위 호환성을 보장하지
> 않는다. 즉, 샤딩 버전이 다른 경우, 재구성해야 한다.

### 프로퍼티

#### 추가된 프로퍼티

* [ISQL_SECURE_LOGIN_MSG](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/iSQL%20User's%20Manual.md#isql_secure_login_msg)
* AKU_DELAY_START_COMPLETE_TIME

#### 변경된 프로퍼티

#### 삭제된 프로퍼티

### 성능 뷰

#### 추가된 성능 뷰

#### 변경된 성능 뷰

#### 삭제된 성능 뷰
