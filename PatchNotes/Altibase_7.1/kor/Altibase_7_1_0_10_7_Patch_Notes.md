Altibase 7.1.0.10.7 Patch Notes
===============================

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-51902 신규 CLI 함수로 SQLRowCount2가 추가되었습니다.](#bug-51902)
    - [BUG-51467 서버 비정상 종료시 altibase_error.log에 콜스택 외 클라이언트 정보를 출력하도록 개선](#bug-51467)
    - [BUG-51540 VARIABLE 컬럼을 포함한 메모리 인덱스 AGING이 실패할 수 있습니다.](#bug-51540)
    - [BUG-51864 Altibase Connector for Kafka(Altibase 커넥터) 제공](#bug-51864)
    - [BUG-51880 쿼리 수행의 안정성 개선을 위한 내부 로직 개선(column count 관리 구조 변경)](#bug-51880)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-51899 인덱스 추가/삭제시 Runtime Header에 저장된 인덱스 헤더 주소가 갱신되지 않을수 있습니다.](#bug-51899)
    - [BUG-51909 서버 비정상 종료시 콜스택에 클라이언트 PID, COMMIT MODE, COMM_NAME, statement 정보 등을 추가로 출력해야 합니다.](#bug-51909)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# New Features

### BUG-51902<a name=bug-51902></a> 신규 CLI 함수로 SQLRowCount2가 추가되었습니다.

- **module** : ul-odbc

- **Category** : Functional Error

- **재현 빈도** : Always

- **설명** : UPDATE, INSERT 또는 DELETE 문에 의해 영향을 받은 행들의 수를 반환할 때, 최대 64비트 정수 범위의 행 개수를 반환하기 위해 신규 CLI 함수로 [SQLRowCount2](https://manual.altibase.com/7.1/dev/cli/2.-Altibase-CLI-Functions/SQLRowCount/#sqlrowcount2)가 추가되었습니다.

- **재현 방법**

  -   **재현 절차**

  -   **수행 결과**

  -   **예상 결과**

- **Workaround**

- **변경사항**
  - Performance view
  
  - Property
  
  - Compile Option

  - Error Code

### BUG-51467<a name=bug-51467></a> 서버 비정상 종료시 altibase_error.log에 콜스택 외 클라이언트 정보를 출력하도록 개선

-   **module** : mm

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : 서버 비정상 종료시 altibase_error.log에 콜스택 외 클라이언트 정보를 출력하도록 개선합니다.
    
    - CliPkgVer: 클라이언트 버전
    
    - CliProtoVer: 클라이언트 통신 프로토콜 버전
    
    - CliType: 클라이언트 타입
    
    - AppInfo: 어플리케이션 정보
    
      ```
      기존 콜스택 정보 아래에 추가로 출력됩니다.
      
      BEGIN-DUMP Diagnostic Information ===============
          Statement: 00007F75D24A9808                  
          Session: 000000000A22F148                    
              CliPkgVer: 7.1.0.10.7                     
              CliProtoVer: 7.1.7                       
              CliType: CLI-64LE                        
              AppInfo: isql                                
          Task: 000000000A16EF00                       
          Link: 00007F74E0000990                       
              ConnType: 1                              
      END-DUMP Diagnostic Information =================
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

### BUG-51540<a name=bug-51540></a> VARIABLE 컬럼을 포함한 메모리 인덱스 AGING이 실패할 수 있습니다.

-   **module** : sm

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : VARIABLE 컬럼을 포함하는 메모리 인덱스가 있을때, 메모리 인덱스 AGING 이 실패하는 문제를 수정했습니다.

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

### BUG-51864<a name=bug-51864></a> Altibase Connector for Kafka(Altibase 커넥터) 제공

-   **module** : rp-kafkaConnector

-   **Category** : Other

-   **재현 빈도** : Always

-   **설명** : Confluent JDBC connector 프로토콜 호환성을 가진 Altibase connector for Kafka(이하 Altibase 커넥터)가 개발되었습니다. Altibase 커넥터를 사용하면 Kafka를 통해 Altibase의 변경 데이터를 다른 데이터베이스로 복제하거나, 다른 데이터베이스의 변경 데이터를 Altibase로 복제할 수 있습니다. Altibase 커넥터는 다음 두 종류의 커넥터로 구성됩니다.
- **Altibase 소스 커넥터**: Altibase의 변경 데이터를 Kafka로 스트리밍하여 다른 데이터베이스로 복제
    - **Altibase 싱크 커넥터**: Kafka를 통해 수신한 다른 데이터베이스의 변경 데이터를 Altibase 및 기타 지원 싱크 데이터베이스로 적용

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

### BUG-51880<a name=bug-51880></a> 쿼리 수행의 안정성 개선을 위한 내부 로직 개선(column count 관리 구조 변경)

-   **module** : qp

-   **Category** : Fatal

-   **재현 빈도** : Unknown

-   **설명** : 잘못된 메모리 참조 예방 및 안정성 보강을 위해 column count 관리 구조를 변경했습니다.
    
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

# Fixed Bugs

### BUG-51899<a name=bug-51899></a> 인덱스 추가/삭제시 Runtime Header에 저장된 인덱스 헤더 주소가 갱신되지 않을수 있습니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : 인덱스를 추가하거나 삭제할때 인덱스 헤더 주소가 갱신되지 않을 수 있는 문제를 수정하였습니다.

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

### BUG-51909<a name=bug-51909></a> 서버 비정상 종료시 콜스택에 클라이언트 PID, COMMIT MODE, COMM_NAME, statement 정보 등을 추가로 출력해야 합니다.

-   **module** : mm

-   **Category** : Other

-   **재현 빈도** : Rare

-   **설명** : 서버 비정상 종료시 분석에 도움이 되도록 클라이언트 PID, COMMIT MODE, COMM_NAME, statement 정보등을 altibase_error.log에 출력하도록 추가하였습니다. 기존 콜스택 정보 밑에 추가로 출력됩니다.
    
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
| 7.1.0.10.7       | 6.5.1                   | 8.12.1       | 7.1.7               | 7.4.7                        |

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

추가/변경/삭제된 프로퍼티 없음.

### 성능 뷰

추가/변경/삭제된 성능뷰 없음.
