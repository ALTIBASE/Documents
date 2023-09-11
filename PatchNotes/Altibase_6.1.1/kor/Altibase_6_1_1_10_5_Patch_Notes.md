# Altibase 6.1.1.10.5 Patch Notes

<br/>

<br/>

# Table of Contents

- [Fixed Bugs](#fixed-bugs)
  - [BUG-40266 갱신 트랜잭션이 대기하는 상황이면, altibase_boot.log에 메시지를 출력하도록 개선합니다.](#bug-40266)
  - [BUG-50558 Query rebuild 중에 잘못된 bind data에 접근하여 서버가 비정상 종료할 수 있는 문제를 수정합니다.](#bug-50558)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
  - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
  - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

</br>

Fixed Bugs
==========

### BUG-40266 갱신 트랜잭션이 대기하는 상황이면, altibase_boot.log에 메시지를 출력하도록 개선합니다.<b id=bug-40266></b>

-   **module** : sm

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : 갱신 트랜잭션이 대기하는 상황의 경우 사용자는 이유를 알지 못한채 무한정 대기해야 했으나, 이 버그의 처리로 altibase_boot.log의 메시지를 확인하여 원인 파악을 할 수 있게 개선하였습니다.

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

### BUG-50558 Query rebuild 중에 잘못된 bind data에 접근하여 서버가 비정상 종료할 수 있는 문제를 수정합니다.<b id=bug-50558></b>

-   **module** : qp-select-pvo

-   **Category** : Memory Error

-   **재현 빈도** : Rare

-   **설명** : Rebuild시에 bind data를 잘못 접근하는 문제를 수정했습니다.

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
| 6.1.1.10.5       | 6.1.1                   | 5.14.1       | 5.6.3               | 6.1.1                        |

> Altibase 6.1.1 패치 버전별 히스토리는 [Version_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_6.1.1/Altibase_6_1_1_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의
> 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는
> 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

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
