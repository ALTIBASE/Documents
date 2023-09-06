# Altibase 버전 별 Replication 호환성

<br/>

<br/>

# Table of Contents

- [개요](#개요)
- [Altibase 7.3](#altibase-73)
- [Altibase 7.1](#altibase-71)
- [Altibase 6.5.1](#altibase-651)
- [Altibase 6.3.1](#altibase-631)
- [Altibase 6.1.1](#altibase-611)
- [버전별 이중화 프로토콜 버전](#버전별-이중화-프로토콜-버전)

<br/>

<br/>

# 개요

Altibase 는 Version 6 이후 부터 이중화 하위 호환성을 보장합니다.

이중화 하위 호환성 이란, 낮은 버전에서 높은 버전으로 이중화를 통한 데이터 전송이 가능하다는 것을 의미합니다. 이중화 프로토콜의 상위 두 자리가 같은 경우, 이중화 하위 호환성을 보장합니다.

단, eager 모드 및 오프라인 이중화는 해당되지 않습니다. Eager 모드 및 오프라인 이중화의 경우는 두 서버의 버전이 모두 일치하는 경우에만 사용할 수 있기 때문입니다.

<br/>

<br/>

# Altibase 7.3

| 송신자(Sender) | 수신자(Receiver) | 이중화 모드 | 호환 여부 | 비고                                                         |
| -------------- | ---------------- | ----------- | --------- | ------------------------------------------------------------ |
| 7.1            | 7.3              | LAZY        | O         | Altibase 7.3 Release Test </br>7.1.0.8.8 과 7.3.0.0.1 이중화 호환성 확인 완료 |
| 6.5.1          | 7.3              | LAZY        | O         |                                                              |
| 6.3.1          | 7.3              | LAZY        | O         |                                                              |
| 6.1.1          | 7.3              | LAZY        | O         |                                                              |
| 7.3            | 7.3              | LAZY        | O         |                                                              |
| 7.3            | 7.1              | LAZY        | O         |                                                              |
| 7.3            | 6.5.1            | LAZY        | O         |                                                              |
| 7.3            | 6.3.1            | LAZY        | O         |                                                              |
| 7.3            | 6.1.1            | LAZY        | X         |                                                              |



<br/>

<br/>

# Altibase 7.1

| 송신자(Sender) | 수신자(Receiver) | 이중화 모드 | 호환 여부 | 비고                                                         |
| -------------- | ---------------- | ----------- | --------- | ------------------------------------------------------------ |
| 6.5.1          | 7.1              | LAZY        | O         | Altibase 7.1 Release Test </br> 6.5.1.2.6과 7.1 이중화 호환성 확인 완료 |
| 6.3.1          | 7.1              | LAZY        | O         |                                                              |
| 6.1.1          | 7.1              | LAZY        | O         |                                                              |
| 7.1            | 7.1              | LAZY        | O         |                                                              |
| 7.1            | 6.5.1            | LAZY        | O         | Altibase 7.1 Release Test</br> 6.5.1.2.6과 7.1 이중화 호환성 확인 완료 |
| 7.1            | 6.3.1            | LAZY        | O         |                                                              |
| 7.1            | 6.1.1            | LAZY        | X         |                                                              |

<br/>

<br/>

# Altibase 6.5.1

| 송신자(Sender) | 수신자(Receiver) | 이중화 모드 | 호환 여부 | 비고                             |
| -------------- | ---------------- | ----------- | --------- | -------------------------------- |
| 6.1.1          | 6.5.1            | LAZY        | O         |                                  |
| 6.3.1          | 6.5.1            | LAZY        | O         |                                  |
| 6.5.1          | 6.5.1            | LAZY        | O         |                                  |
| 6.5.1          | 6.1.1            | LAZY        | O         | TASK-7081으로 검증완료(20181025) |
| 6.5.1          | 6.3.1            | LAZY        | O         |                                  |

<br/>

<br/>

# Altibase 6.3.1

| 송신자(Sender) | 수신자(Receiver) | 이중화 모드 | 호환 여부 | 비고                                                         |
| -------------- | ---------------- | ----------- | --------- | ------------------------------------------------------------ |
| 6.1.1          | 6.3.1            | LAZY        | O         |                                                              |
| 6.3.1          | 6.1.1            | LAZY        | X         | 6.3.1 에 한해서, "__REPLICATION_USE_V6_PROTOCOL" 히든 프로퍼티를 사용하여 가능함 |

<br/>

<br/>

# Altibase 6.1.1

| 송신자(Sender) | 수신자(Receiver) | 이중화 모드 | 호환 여부 | 비고                                                        |
| -------------- | ---------------- | ----------- | --------- | ----------------------------------------------------------- |
| 6.1.1          | 6.1.1            | -           | O         | 6.1.1 버전에서는 상위 버전으로 데이터 전송만 가능함(단방향) |

<br/>

<br/>

# 버전별 이중화 프로토콜 버전

## Altibase 7.1

| altibase version          | replication protocol version | Bug#                                                         |
| :------------------------ | :--------------------------: | ------------------------------------------------------------ |
| **7.1.0.6.5** ~           |          **7.4.7**           | [BUG-49398](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.1/kor/Altibase_7_1_0_6_5_Patch_Notes.md#bug-49398ddl-%EB%B3%B5%EC%A0%9C-%EC%8B%A4%ED%96%89-%EC%8B%9C-%ED%85%8C%EC%9D%B4%EB%B8%94-%EC%9E%A0%EA%B8%88-%ED%9A%8D%EB%93%9D-%EC%8B%A4%ED%8C%A8-%EB%98%90%EB%8A%94-%EA%B5%90%EC%B0%A9-%EC%83%81%ED%83%9Cdeadlock%EB%A5%BC-%EC%82%AC%EC%9C%A0%EB%A1%9C-%EC%9D%BC%EC%8B%9C%EC%A0%81%EC%9C%BC%EB%A1%9C-ddl-%EC%88%98%ED%96%89%EC%9D%B4-%EC%8B%A4%ED%8C%A8%ED%95%98%EB%8A%94-%EA%B2%BD%EC%9A%B0-%EC%9E%AC%EC%8B%9C%EB%8F%84%ED%95%98%EB%8A%94-%EA%B8%B0%EB%8A%A5%EC%9D%84-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4) |
| **7.1.0.4.0** ~ 7.1.0.6.4 |          **7.4.6**           | [BUG-47805](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.1/kor/Altibase_7_1_0_4_0_Patch_Notes.md#bug-47805-sridspatial-reference-identifier-interface-%EC%A7%80%EC%9B%90), [BUG-47873](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.1/kor/Altibase_7_1_0_4_0_Patch_Notes.md#bug-47873-geometry-%EC%BB%AC%EB%9F%BC%EC%9D%98-srid-%EC%86%8D%EC%84%B1%EC%97%90-%EB%8C%80%ED%95%B4%EC%84%9C-replication--%EC%A7%80%EC%9B%90) |
| **7.1.0.2.4** ~ 7.1.0.3.9 |          **7.4.5**           | [BUG-46940](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.1/kor/Altibase_7_1_0_2_4_Patch_Notes.md#bug-46940-%EC%9D%B4%EC%A4%91%ED%99%94-start%ED%9B%84-xlog%EA%B0%80-receiver%EB%A1%9C-%EC%A0%84%EC%86%A1%ED%95%98%EC%A7%80-%EC%95%8A%EB%8A%94-%EB%AC%B8%EC%A0%9C%EA%B0%80-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4) |
| **7.1.0.1.8** ~ 7.1.0.2.3 |          **7.4.4**           | [BUG-46120](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.1/kor/Altibase_7_1_0_1_8_Patch_Notes.md#bug-46120-active-server%EC%99%80-standby-server%EC%9D%98-%ED%95%B4%EC%8B%9C-%ED%8C%8C%ED%8B%B0%EC%85%98%EB%93%9C-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%9D%98-%ED%8C%8C%ED%8B%B0%EC%85%98-%EA%B0%9C%EC%88%98%EA%B0%80-%EB%8B%A4%EB%A5%B8-%EA%B2%BD%EC%9A%B0-%EC%9D%B4%EC%A4%91%ED%99%94%EA%B0%80-%EC%8B%A4%ED%8C%A8%ED%95%B4%EC%95%BC-%ED%95%A9%EB%8B%88%EB%8B%A4) |
| **7.1.0.1.4** ~ 7.1.0.1.7 |          **7.4.3**           | [BUG-45946](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.1/kor/Altibase_7_1_0_1_4_Patch_Notes.md#bug-45946-%EC%9D%B4%EC%A4%91%ED%99%94%EB%A5%BC-%ED%86%B5%ED%95%98%EC%97%AC-ddl-%EB%8F%99%EA%B8%B0%ED%99%94ddl-synchronization%EB%A5%BC-%ED%97%88%EC%9A%A9%ED%95%A9%EB%8B%88%EB%8B%A4) |
| **7.1.0.1.2** ~7.1.0.1.3  |          **7.4.2**           |                                                              |

## Altibase 6.5.1

| **altibase version**      | **replication protocol version** | Bug#      |
| :------------------------ | :------------------------------: | --------- |
| ***6.5.1.6.9*** ~         |           ***7.4.5***            | BUG-46940 |
| ***6.5.1.6.8***           |           ***7.4.4***            | BUG-47144 |
| **6.5.1.0.0** ~ 6.5.1.6.7 |            **7.4.2**             |           |

## Altibase 6.3.1

| **altibase version** | **replication protocol version** | Bug# |
| :------------------- | :------------------------------: | ---- |
| **6.3.1.0.0** ~      |            **7.4.1**             |      |

## Altibase 6.1.1

| **altibase version** | **replication protocol version** | Bug# |
| :------------------- | :------------------------------: | ---- |
| **6.1.1.0.0** ~      |            **6.1.1**             |      |
