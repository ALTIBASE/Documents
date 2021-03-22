**Table of Contents**  

- [Altibase 7.1.0.5.3](#altibase-71053)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-48594 시노님(synonym)을 포함한 SQL 수행 시 SQL PLAN CACHE 로 인한 CPU 병목을 개선합니다.](#bug-48594%EC%8B%9C%EB%85%B8%EB%8B%98synonym%EC%9D%84-%ED%8F%AC%ED%95%A8%ED%95%9C-sql-%EC%88%98%ED%96%89-%EC%8B%9C-sql-plan-cache-%EB%A1%9C-%EC%9D%B8%ED%95%9C-cpu-%EB%B3%91%EB%AA%A9%EC%9D%84-%EA%B0%9C%EC%84%A0%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)



Altibase 7.1.0.5.3
================================

Fixed Bugs
----------

### BUG-48594 시노님(synonym)을 포함한 SQL 수행 시 SQL PLAN CACHE 로 인한 CPU 병목을 개선합니다. 

-   **module** : qp-dml-execute

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **내용** : 시노님(synonym)을 포함한 SQL 수행 시 SQL PLAN CACHE 처리 과정에서 잦은 시스템콜(malloc)로 인한 CPU 병목 현상을 개선합니다. 개선 방식 사용을 원할 경우 __SQL_PLAN_CACHE_VALID_MODE = 1 을 설정해야 합니다.

-   **재현 방법**
-   **재현 절차**
    
-   **수행 결과**
    
-   **예상 결과**
    
-   **Workaround**

-   **변경사항**
    -   Performance view
        
    -   Property
        -   속성 이름 : __SQL_PLAN_CACHE_VALID_MODE
            -   속성 설명 : SQL PLAN CACHE Validation 단계에서 CPU 병목 현상 개선 기능 사용 여부를 결정합니다. 
            -   변경/추가/삭제 : 추가
            -   공개/비공개 : 비공개
            -   최소값,최대값,기본값 : 0, 1, 0
        
    -   Compile Option

    -   Error Code


Changes
-------

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    7.1.0.5.3     |          6.5.1          |    8.9.1     |        7.1.7        |            7.4.6             |

> Altibase 7.1 패치 버전별 히스토리는 [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7_1_Version_Histories.md)에서 확인할 수 있다.

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

#### Sharding Version

샤딩 버전은 변경 되지 않았다.

> 알티베이스 샤딩 프로토콜 및 메타는 상위, 하위 호환성을 보장하지 않는다. 즉, 샤딩 버전이 다른 경우, 재구성해야 한다.

### 프로퍼티

#### 추가된 프로퍼티

#### 변경된 프로퍼티

#### 삭제된 프로퍼티

### 성능 뷰

#### 추가된 성능 뷰

#### 변경된 성능 뷰

#### 삭제된 성능 뷰
