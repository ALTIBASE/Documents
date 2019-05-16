<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Altibase 7.1.0.2.2 Patch Notes](#altibase-71022-patch-notes)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-46602 Replication GAP이 4G(unsigned int max) 이상 인경우 v\$repgap에 REP\_GAP 값이 부정확 할 수 있습니다.](#bug-46602replication-gap%EC%9D%B4-4gunsigned-int-max-%EC%9D%B4%EC%83%81-%EC%9D%B8%EA%B2%BD%EC%9A%B0-v%5Crepgap%EC%97%90-rep%5C_gap-%EA%B0%92%EC%9D%B4-%EB%B6%80%EC%A0%95%ED%99%95-%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Altibase 7.1.0.2.2 Patch Notes
==============================

Fixed Bugs
----------

### BUG-46602 Replication GAP이 4G(unsigned int max) 이상 인경우 v\$repgap에 REP\_GAP 값이 부정확 할 수 있습니다.

-   **module** : rp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : Replication GAP이 4G(unsigned int max) 이상인
    경우 v\$repgap의 REP\_GAP 값이 부정확한 문제가 있어, 이를
    수정하였습니다.

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

| altibase version | database binary version | meta version | cm protocol version | replication protocol version | sharding version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- | ---------------- |
| 7.1.0.2.2        | 6.5.1                   | 8.7.1        | 7.1.6               | 7.4.4                        | 2.2.1            |

> Altibase 7.1 패치 버전별 히스토리는
> [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7_1_Version_Histories.md)
> 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의
> 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는
> 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

> 패치를 롤백하려는 경우,
> [메타다운그레이드](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Installation.md#%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9Cmeta-downgrade)를
> 참고한다.

#### CM protocol Version

통신 프로토콜 버전은 변경되지 않았다.

#### Replication protocol Version

Replication 프로토콜 버전은 변경되지 않았다..

#### Sharding Version

샤딩 버전은 변경 되지 않았다.

> 알티베이스 샤딩 프로토콜 및 메타는 상위, 하위 호환성을 보장하지
> 않는다. 즉, 샤딩 버전이 다른 경우, 재구성해야 한다.

### 프로퍼티

추가/변경/삭제된 프로퍼티 없음

### 성능 뷰

추가/변경/삭제된 성능 뷰 없음