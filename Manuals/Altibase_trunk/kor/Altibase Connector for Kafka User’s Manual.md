# Altibase Connector for Kafka User’s Manual

#### Trunk

Altibase® Tool & Utilities

<br><br><br><br><br><br><!-- PDF 변환을 위한 여백입니다. --> 







































<!-- PDF 변환을 위한 여백입니다. --> 

<div align="left">
    <img src="media/common/e5cfb3761673686d093a3b00c062fe7a.png">
</div>

<br><br><!-- PDF 변환을 위한 여백입니다. --> 









































<!-- PDF 변환을 위한 여백입니다. --> 

<pre>
Altibase Tool & Utilities Adapter for JDBC User’s Manual
Trunk
Copyright ⓒ 2001~2023 Altibase Corp. All Rights Reserved.<br>
본 문서의 저작권은 ㈜알티베이스에 있습니다. 이 문서에 대하여 당사의 동의없이 무단으로 복제 또는 전용할 수 없습니다.<br>
<b>㈜알티베이스</b>
08378 서울시 구로구 디지털로 306 대륭포스트타워Ⅱ 10층
전화 : 02-2082-1114
팩스 : 02-2082-1099
고객서비스포털 : <a href='http://support.altibase.com'>http://support.altibase.com</a>
홈페이지      : <a href='http://www.altibase.com/'>http://www.altibase.com</a></pre>




<br>

# 목차

* 서문
  * 이 매뉴얼에 대하여
* 1.소개
* 2.설치와 설정
* 3.사용법
  * 제약조건
  * 구동하기
  * 종료하기
  * 프로퍼티
* 부록



# 1.소개

Altibase Connector for Kafka(이하 Altibase 커넥터)는 사용자가 Kafka를 통해 Altibase의 변경 데이터를 다른 데이터베이스로 복제하거나, 다른 데이터베이스의 변경 데이터를 Altibase로 복제할 때 사용하는 도구이다.

Altibase 커넥터는 Altibase 에서 변경된 데이터를 Kafka로 전달하는 Altibase 소스 커넥터와 Kafka에서 수신한 메시지를 Altibase 서버에 적용하는 Altibase 싱크 커넥터로 구성되어 있다.



## 구조와 개념

사용자가 Kafka를 통해 Altibase에서 변경된 데이터를 다른 데이터베이스로 복제하거나, 다른 데이터베이스에서 변경된 데이터를 Altibase로 복제하기 위해서는 아래 그림과 같이 source connector 와 sink connector가 필요합니다. Altibase 

!!사진



### 소스 커넥터

Altibase 에서 변경된 데이터를 Kafka로 전달하는데 사용한다. 내부적으로 XLog 콜렉터가 포함되어 있어, XLog 송신자로 부터 메타 데이터와 XLog를 전달 받는다.

### 싱크 커넥터

Kafka에서 수신한 메시지를 Altibase 서버에 적용하는데 사용한다.

## 지원 OS

Altibase 커넥터가 지원하는 OS는 아래와 같다.

| 종류        | 지원 OS                                                 |
| ----------- | ------------------------------------------------------- |
| 소스 커넥터 | 현재 LINUX 운영체제만 지원한다.                         |
| 싱크 커넥터 | confluent JDBC connector가 지원하는 OS를 모두 지원한다. |

?? 지원 OS는 버전을 명시하여 구체적으로 적는것이 좋을 것 같음.

## 지원 데이터베이스

Altibase 커넥터가 지원하는 데이터베이스는 아래와 같다.

| 종류        | 지원하는 데이터베이스                                        |
| ----------- | ------------------------------------------------------------ |
| 소스 커넥터 | Altibase 7.1이상의 버전으로, 소스 커넥터와 동일한 버전을 사용해야 한다. |
| 싱크 커넥터 | JDBC 4.2 이상을 지원하는 데이터 베이스<br/>- Altibase<br/>- Oracle<br/>-MariaDB<br/>PostgreSQL |

??동일 버전이면 Altibase 8.1 아닌지요?? 소스 커넥터는 자체 버전이 있지 않나요??

??지원 데이터베이스는 지원하는 버전의 범위를 명시하는것이 좋습니다.

migration center 참고.

## 지원 데이터 타입

Altibase 커넥터가 지원하는 Altibase의 데이터 타입은 다음과 같다. LOB은 지원하지 않는다.

* 숫자형 데이터 타입
  * NUMBER
  * FLOAT[^1]
  * DOUBLE
  * REAL
  * BIGINT
  * INTEGER
  * SMALLINT
* 날짜형 데이터 타입
  * DATE
* 문자형 데이터 타입
  * CHAR
  * VARCHAR
  * NCHAR
  * NVARCHAR 데이터베이스 간 데이터 형식 차이로 인해, 데이터 전송 및 입력 시 문자열로 처리됩니다.

[^1]: FLOAT 타입은 다른 데이터베이스간 데이터 처리 형식의 차이가 있어서, 문자열로 변환되어 처리된다.

## 용어

XLog

소스 데이터베이스의 리두 로그(Redo Log)를 논리적인 형태로 변환한 로그로, XLog 송신자가 Altibase 소스 커넥터로 전송할 때 사용한다.

**XLog 송신자**
 XLog 송신자는 액티브 리두 로그를 분석하여 XLog 형태로 변환하고 이를 소스 커넥터의 XLog 콜렉터에 전달 한다.

XLog 콜렉터

XLog 콜렉터는 XLog 송신자로 부터 메타 데이터와 XLog를 전달 받는다. XLog 콜렉터는 메타 데이터, XLog 큐, 트랜잭션 테이블 및 XLog 풀을 가지고 있다.

Handshaking

Handshaking은 XLog 송신자가 XLog 콜렉터에게 XLog를 보내기 전에 프로토콜 버전과 메타 데이터를 확인하는 작업이다.

소스 데이터베이스(Source DB)

Kafka로 데이터를 공급하는 데이터베이스를 의미한다. 소스 커넥터는 소스 데이터베이스의 데이터를 읽어 Kafka 토픽으로 전송한다.

싱크 데이터베이스(Sink DB)

Kafka에서 전달된 데이터를 저장하는 대상 데이터베이스를 의미한다. 싱크 커넥터가 Kafka 토픽의 메시지를 읽어 싱크 데이터베이스에 저장한다.



# 2.설치와 설정

## 설치 전 확인 사항

Kafka 설치가 되어 있어야 함.

Kafka connector 설치 디렉토리 확인 - altibase connector를 옮겨놓을 디렉토리임.

Altibase 커넥터를 설치하고 실행하기 위해서는 다음의 시스템 요구사항을 만족해야 합니다.

또한 Altibase 커넥터가 올바르게 작동하려면 몇 가지 시스템 환경 설정도 필요합니다.   -> 어떤 설정인지요??

시스템 요구사항에 대해 보다 자세히 알고 싶으면, Altibase 고객서비스포털( http://support.altibase.com/kr/ )로 연락 바랍니다. 

## 소스 커넥터 설치

1. altibase-source-connect-X.X.X.X.X.zip 형식으로 제공된 파일의 압축을 해제합니다.

2. 압축 해제 후 디렉토리의 이름을 altibase-source-connect와 같이 적절한 이름으로 변경합니다.

3. 해당 디렉토리를 Kafka connector 설치 디렉토리로 이동시킵니다. (예: /usr/share/confluent-hub-components/)

4. Kafka connect를 재시작합니다.

## 싱크 커넥터 설치

1. confluentinc-Kafka-connect-jdbc-Altibase-x.x.x.zip 형식으로 제공된 파일의 압축을 해제합니다.
2. 압축 해제 후 디렉토리의 이름을 confluentinc-Kafka-connect-jdbc-Altibase와 같이 적절한 이름으로 변경합니다.
3. 해당 디렉토리를 Kafka connector 설치 디렉토리로 이동시킵니다. (예: /usr/share/confluent-hub-components/)
4. Kafka connect를 재시작합니다.

# 3.사용법

이 장에서는 Altibase의 소스 커넥터와 싱크 커넥터를 구동하고 종료하는 방법과 사용하는 방법을 자세히 설명합니다.

## 제약조건

Altibase 커넥터는 Confluent JDBC Connect의 메시지 형식을 사용하기 때문에, Confluent JDBC Connect의 기본적인 제약사항이 있다. Confluent JDBC connector과 관련된 제약조건은 [Confluent JDBC connector 공식 문서](https://docs.confluent.io/kafka-connectors/jdbc/10.7/sink-connector/overview.html)를 참고하기 바란다.

* INSERT구문과 UPDATE 구문의 메시지 형식이 동일하다.

  * INSERT 구문과 UPDATE 구문에서 생성되는 메시지 형식이 동일하여 싱크 커넥터에서 두 구문을 구분할 수 없다. 따라서 싱크 커넥터에 입력된 데이터에 대해 어떻게 처리할지를 insert.mode 설정을 통해 명시적으로 지정해야 한다. (참고URL)

    ?? 따라서 싱크 커넥터에 입력된 데이터에 대해 INSERT로 처리할지 또는 UPDATE로 처리할지를 insert.mode 설정을 통해 명시적으로 지정해야 한다. 

### 소스 커넥터의 제약조건

#### 데이터 제약조건

* 복제할 테이블에는 반드시 프라이머리 키가 존재해야 한다.
* Date 타입은 confluent JDBC Connector 메시지 형식의 제한으로 인해 마이크로초 단위는 제외되고, 밀리초 단위까지만 전달됩니다.
* FLOAT 타입은 다른 데이터베이스 간 데이터 형식 차이로 인해, 데이터 전송 및 입력 시 문자열로 처리됩니다.
* LOB 타입은 지원하지 않습니다.

#### 기타 제약조건

* 소스 커넥터는 task 수를 1개로만 설정합니다.

* 소스 커넥터에서 레코드를 Kafka로 전달할 때, 이중화 중지 후 재시작 등의 작업을 수행하면 일부 레코드가 중복해서 전달될 수 있습니다.  -> ??주의사항에 해당.

* 소스 데이터베이스인 Altibase 가 이중화 환경으로 구성되어 있는 경우, 이중화 동기화(Sync) 작업을 수행할 경우 소스 커넥터의 ala.xlog.pool.size 프로퍼티 값을 변경해야 한다. ala.xlog.pool.size의 기본값은 Altibase 의 REPLICATION_SYNC_TUPLE_COUNT 프로퍼티보다 작을 수 있으므로, 보다 큰 값으로 설정해야 한다. 그렇지 않을 경우 ala.xlog.pool.size에 설정된 개수만큼의 XLog만 전송되어, 일부 데이터가 전송되지 않을 수 있다.

  또한, ala.xlog.pool.size 값을 크게 설정할 경우 JVM의 힙(Heap) 크기가 필요한 메모리보다 작으면 Out of Memory(OOM)오류가 발생할 수 있다. 이 경우, Kafka Connect 의 힙 크기를 늘려주어야 한다.

### 싱크 커넥터의 제약조건

#### 데이터 제약 조건

* 복제할 테이블에는 반드시 프라이머리 키가 존재해야 한다.

* 트랜잭션을 지원하지 않는다.

* 싱크 데이터베이스가 Altibase인 상태에서 싱크 커넥터의 insert.mode의 값을 upsert로 설정할 경우 아래의 제약이 있다.

  * Altibase 의 COERCE_HOST_VAR_IN_SELECT_LIST_TO_VARCHAR 프로퍼티 값을 * 로 변경해야 한다. 그렇지 않을 경우 오류가 발생합니다. 이 경우 발생한 오류에 대한 해결방안은 [부록A.예외 상황 및 해결 방안]()을 확인한다.

  ??권장값을 알려주는 것이 좋습니다. 

  * Altibase 의 DEFAULT_DATE_FORMAT 프로퍼티 값을 ‘YYYY-MM-DD HH:MI:SS.SSSSSS’로 설정해야 한다. 그렇지 않을 경우, DATE 타입의 시간 정보가 누락될 수 있다. 이 프로퍼티를 수정할 경우, Altibase 서버를 재시작해야 한다.

  

  

## 구동 방법

### 소스 커넥터 구동하기

Altibase 소스 커넥터를 구동하기 위해서는 먼저 소스 데이터베이스(Altibase)에서 XLog 송신자를 생성한 다음 등록해야 합니다. 

* Altibase 서버에서 XLog 송신자를 생성

  XLog 송신자를 생성하기 위한 SQL 구문은 ['Log Analyzer User\'s Manual'의 XLog Sender를 위한 구문]()을 참고 한다.

  - 예시) XLog 송신자의 이름이 ALA이고, 소스 데이터베이스 서버의 IP가 192.168.0.2, 192.168.0.3, 192.168.0.4 이고, 소스 커넥터의 포트가 21301인 경우 

  ```
  CREATE REPLICATION ALA FOR ANALYSIS
          WITH ‘192.168.0.2’, 21301
               ‘192.168.0.3’, 21301
               ‘192.168.0.4’, 21301
          FROM SCOTT.TABLE1 TO SCOTT.TABLE1;
  ```

* Kafka Connect REST API를 이용하여 소스 커넥터를 등록

  소스 커넥터의 이름과 프로퍼티를 전달하여 등록한다. 

  * 예시) Kafka connect의 IP가 192.168.0.2 이고 소스 데이터베이스의 IP가 192.168.0.11, 이중화 포트 번호가 21300인 경우

    ```bash
    $ curl -m 30 --location --request POST 'http://192.168.0.2:8083/connectors' \
    --header 'Content-Type: application/json' \
    --data '{
        “name”: “Altibase-source-connector”,
        “config”: {
            “connector.class” : “com.altibase.connect.AltibaseSourceConnector”,
            “ala.sender.ip” : “192.168.0.11”,
            “tasks.max” : “1”,
            “ala.receiver.port” : “21300”
        }
    }'
    ```

    ??config에 필수 입력값, 선택 입력값 설명 추가되어야 하지 않을까요??

* XLog 송신자를 시작시킨다.

  ```
  iSQL> ALTER REPLICATION ALA START;
  ```

  ??소스커넥터를 구동시킨 이후, 소스커넥터의 프로퍼티 설정을 변경하려고 하는 경우는 어떻게 해야 하나요??

### 싱크 커넥터 구동하기

싱크 커넥터를 구동하기 전에 싱크 데이터베이스(Altibase)가 실행 중인지 확인한 후 진행한다.

* Kafka Connect REST API를 이용하여 싱크 커넥터를 등록

  싱크 커넥터의 이름과 프로퍼티를 전달하여 싱크 커넥터를 등록한다.

  * 예시) Kafka connect의 IP가 192.168.0.2, Sink DB의 IP가 192.168.0.12, 이중화 포트가 21300, 데이터베이스 이름이 mydb인 경우

    ```bash
    $ curl -m 30 --location --request POST 'http://192.168.0.2:8083/connectors' \
    --header 'Content-Type: application/json' \
    --data '{
        “name”: “Altibase-sink-connector”,
        “config”: {
            “connector.class” : “io.confluent.connect.jdbc.JdbcsinkConnector”,
            “tasks.max” : “1”,
            “connection.user” : “scott”,
            “connection.password” : “tiger”,
            “connection.url” : “jdbc:Altibase://192.168.0.12:21300/mydb”,
            “topics” : “TABLE1”,
            “insert.mode” : “upsert”,
            “delete.enabled” : “true”,
            “pk.mode” : “record_key”
        }
    }'
    ```

## 상태 확인

Altibase 커넥터는 Kafka 에서 제공하는 REST API와 로그 메시지를 통해 상태를 확인할 수 있다. 이 API는 커넥터가 정상 작동 중인지, 실행 중인지, 실패했는지 등을 확인할 때 사용된다.

REST API를 통한 상태 확인 방법

* 예시) Kafka connect의 IP가 192.168.0.2 일 때, Altibase-source-connector의 상태를 확인하는 요청

  ```bash
  $ curl -m 30 --location --request GET 'http://192.168.0.2:8083/connectors/Altibase-source-connector/status' 2>/dev/null | tail -n 1 | python3 -m json.tool 2>/dev/null | sed 's/\\n/\n/g' | sed 's/\\t/\t/g'
  ```

  결과

  ```json
  {
      “name“: “Altibase-source-connector“,
      “connector“: {
          “state“: “RUNNING“,
          “worker_id“: “connect-1:8083“
      },
      “tasks“: [
          {
              “id“: 0,
              “state“: “RUNNING“,
              “worker_id“: “connect-1:8083“
          }
      ],
      “type“: “source“
  }
  ```

커넥터 또는 task의 상태가 FAILED 인 경우는 어떠한 오류로 실패했는지를 "trace" 속성에서 확인할 수 있다. FAILED 상태에서 발생할 수 있는 오류에 대해서는 부록 A를 참고하기 바란다.

로그를 통한 상태 확인 방법

Altibase 커넥터에서 생성하는 로그는 Kafka Connect의 설정에 따라 출력이 되며, Kafka Connect 또는 다른 커넥터와 같이 stdout또는 로그 파일에 출력될 수 있다.

?? 어떻게 확인하는지 설명이 필요함.



## 종료 방법

### 소스 커넥터 종료하기

소스 커넥터를 종료할 때는, Altibase 서버의 XLog 송신자도 함께 중지 해야 한다.

* 소스 커넥터 종료 요청
* XLog 송신자 종료

### 싱크 커넥터 종료하기

* 소스 커넥터 종료 요청

### 커넥터 제거

* 예시) Kafka Connector의 IP가 IP가 192.168.0.2 일 때, Altibase-source-connector를 제거하는 경우

  ```bash
  $ curl -m 30 --location --request DELETE 'http://192.168.0.2:8083/connectors/Altibase-source-connector'
  ```

  

## 프로퍼티

### 소스 커넥터 프로퍼티

Altibase 의 소스 커넥터에서 지원하는 프로퍼티를 소개한다.

#### ala.sender.ip

| 항목        | 설명                                                         |
| ----------- | ------------------------------------------------------------ |
| 데이터 타입 | String                                                       |
| 기본값      | 127.0.0.1                                                    |
| 설명        | XLog 송신자의 IP 주소를 지정하는 프로퍼티이다. Altibase가 설치된 서버의 IP 주소 를 설정한다. |

#### ala.sender.ip

##### 데이터 타입

String

##### 기본값

127.0.0.1

##### 설명

XLog 송신자의 IP 주소를 지정하는 프로퍼티이다. Altibase가 설치된 서버의 IP 주소 를 설정한다.

#### ala.sender.port

| 항목        | 설명                                                         |
| ----------- | ------------------------------------------------------------ |
| 데이터 타입 | Int                                                          |
| 기본값      | 0                                                            |
| 범위        | [0, 65535]                                                   |
| 설명        | Altibase 서버에 XLog 송신자를 시작한 다음 소스 커넥터를 구동할 때 XLog 송신자와 접속되는 방식을 지정한다.<br/>- 0: XLog 송신자가 접속을 시도할 때까지 소스 커넥터가 대기한다.<br/>- 1: 명시된 포트번호로 소스 커넥터가 XLog와 직접 접속을 시도한다. |

#### ala.receiver.port

| 항목        | 설명                                                         |
| ----------- | ------------------------------------------------------------ |
| 데이터 타입 | Int                                                          |
| 기본값      | 47146                                                        |
| 범위        | [1024, 65535]                                                |
| 설명        | XLog 콜렉터가 XLog를 수신하기 위해 사용하는 포트 번호를 지정하는 프로퍼티 이다. |

#### ala.handshake.timeout

| 항목        | 설명                                                         |
| ----------- | ------------------------------------------------------------ |
| 데이터 타입 | Int                                                          |
| 기본값(초)  | 600                                                          |
| 범위        | [1, 2147483647]                                              |
| 설명        | XLog 콜렉터가 XLog를 수신하기 위해 사용하는 포트 번호를 지정하는 프로퍼티 이다. |

#### ala.replication.name

| 항목        | 설명                                                         |
| ----------- | ------------------------------------------------------------ |
| 데이터 타입 | String                                                       |
| 기본값      | ALA                                                          |
| 설명        | XLog 송신자의 이름을 지정하는 프로퍼티이다. 소스 커넥터를 구동할 때 생성한 XLog의 이름으로 설정한다. |

#### ala.xlog.pool.size

| 항목        | 설명                                          |
| ----------- | --------------------------------------------- |
| 데이터 타입 | Int                                           |
| 기본값      | 100000                                        |
| 범위        | [1000, 2147483647]                            |
| 설명        | XLog 콜렉터가 할당할 수 있는 XLog의 개수이다. |

> [!NOTE]
>
> XLog 콜렉터에는 Altibase 서버의 트랜잭션이 커밋되기 전의 레코드 변경 작업 내용이 XLog로 각각 쌓인다. 만약, Altibase 서버에 발생하는 트랜잭션이 다수의 레코드를 변경시키는 경우에는 XLog 콜렉터가 할당할 수 있는 XLog가 부족하여 정상적으로 복제할 수 없다. 따라서, Altibase 서버의 트랜잭션 유형에 따라서 이 프로퍼티 값을 조정해야 한다.
>
> Altibase 서버가 이중화 환경으로 구성되어 있는 경우, Sync 작업을 수행할 경우 ala.xlog.pool.size 를  Altibase 의 REPLICATION_SYNC_TUPLE_COUNT 프로퍼티 값보다 크게 설정해야 한다.
>
> 이 프로퍼티 값을 크게 설정했을 때, jvm의 heap size가 필요한 메모리에 비해 작게 설정되어 있다면 Out of Memory 오류가 발생할 수 있으므로, Kafka connect의 heap size를 적절한 크기로 같이 늘려주어야 한다.

#### ala.receive.xlog.timeout

| 항목        | 설명                                                         |
| ----------- | ------------------------------------------------------------ |
| 데이터 타입 | Long                                                         |
| 기본값(초)  | 300                                                          |
| 범위        | [1, 4294967294]                                              |
| 설명        | XLog 콜렉터가 XLog를 수신하기 위해 대기하는 시간을 지정하는 프로퍼티이다. |

#### ala.log.directory

| 항목        | 설명                                                         |
| ----------- | ------------------------------------------------------------ |
| 데이터 타입 | String                                                       |
| 기본값      | /tmp                                                         |
| 설명        | ALA가 트레이스 로그를 저장하는 디렉토리를 지정하는 프로퍼티이다. |

#### data.skip.insert

| 항목        | 설명                                                         |
| ----------- | ------------------------------------------------------------ |
| 데이터 타입 | Boolean                                                      |
| 기본값      | false                                                        |
| 설명        | Altibase 서버에서 실행된 INSERT 구문을 Kafka에 스킵할 지 여부를 결정하는 프로퍼티이다. 이 프로퍼티를 true로 설정하면 Altibase에서 실행된 INSERT 구문이 Kafka에는 전송되지 않는다.<br/>- false: 구문 실행을 스킵하지 않는다. 즉, 정상적으로 구문을 실행한다.<br/>- true: 구문 실행을 스킵한다. |

#### data.skip.update

| 항목        | 설명                                                         |
| ----------- | ------------------------------------------------------------ |
| 데이터 타입 | Boolean                                                      |
| 기본값      | false                                                        |
| 설명        | Altibase 서버에서 실행된 UPDATE구문을 Kafka에 스킵할 지 여부를 결정하는 프로퍼티이다. 이 프로퍼티를 true로 설정하면 Altibase에서 실행된 UPDATE구문이 Kafka에는 전송되지 않는다.<br/>- false: 구문 실행을 스킵하지 않는다. 즉, 정상적으로 구문을 실행한다.<br/>- true: 구문 실행을 스킵한다. |

#### data.skip.delete

| 항목        | 설명                                                         |
| ----------- | ------------------------------------------------------------ |
| 데이터 타입 | Boolean                                                      |
| 기본값      | false                                                        |
| 설명        | Altibase 서버에서 실행된 DELETE구문을 Kafka에 스킵할 지 여부를 결정하는 프로퍼티이다. 이 프로퍼티를 true로 설정하면 Altibase에서 실행된 DELETE구문이 Kafka에는 전송되지 않는다.<br/>- false: 구문 실행을 스킵하지 않는다. 즉, 정상적으로 구문을 실행한다.<br/>- true: 구문 실행을 스킵한다. |

#### topic.prefix

| 항목        | 설명                                                         |
| ----------- | ------------------------------------------------------------ |
| 데이터 타입 | String                                                       |
| 기본값      |                                                              |
| 설명        | Altibase 서버에서 실행된 구문을 Kafka에 전송할 때 사용되는 토픽은 기본적으로 테이블 이름으로 사용하는데, 테이블 이름 앞에 접두사를 붙이고 싶은 경우, 이 프로퍼티의 값을 설정하여 접두사를 붙일 수 있다. |

#### poll.interval.ms

| 항목           | 설명                                                         |
| -------------- | ------------------------------------------------------------ |
| 데이터 타입    | Int                                                          |
| 기본값(밀리초) | 1000                                                         |
| 범위           | [0, 50000]                                                   |
| 설명           | XLog 송신자가 새로운 XLog를 전송하지 않는 경우, 다음 XLog 확인을 위해 대기하는 시간을 설정하는 프로퍼티이다. |

#### poll.data.count

| 항목           | 설명                                                         |
| -------------- | ------------------------------------------------------------ |
| 데이터 타입    | Int                                                          |
| 기본값(밀리초) | 1000                                                         |
| 범위           | [1, 2147483647]                                              |
| 설명           | XLog 처리 시, 한 번에 Kafka로 전송할 최대 레코드의 수를 설정하는 프로퍼티이다. 값이 너무 작을 경우, 소스 커넥터에서 시간당 처리되는 XLog의 수가 줄어들 수 있다. |

#### poll.ignore.commit

| 항목        | 설명                                                         |
| ----------- | ------------------------------------------------------------ |
| 데이터 타입 | Boolean                                                      |
| 기본값      | true                                                         |
| 설명        | XLog 처리 중에 수신된 COMMIT XLog에 대한 처리를 무시할지 여부를 결정하는 프로퍼티이다. 값이 false인 경우, COMMIT XLog 호출 빈도에 따라 소스 커넥터에서 시간당 처리되는 XLog의 수가 줄어들 수 있다.<br/>- true: COMMIT XLog를 무시하고 다음 XLog를 처리한다.<br/>- false: COMMIT XLog 수신 시 해당 XLog 이전에 수신한 레코드들을 Kafka에 전송한다. |

### 싱크 커넥터 프로퍼티

싱크 커넥터는 Confluent JDBC connector 의 설정 프로퍼티를 그대로 사용하며, Altibase에서 별도로 추가된 프로퍼티는 없습니다. Confluent JDBC Connector에서 제공하는 설정 프로퍼티에 대한 자세한 내용은 https://docs.confluent.io/Kafka-connectors/jdbc/10.7/sink-connector/sink_config_options.html 를 참고한다.

## 허용된 DDL

XLog 송신자는 DML을 대상으로만 XLog를 수집하지만, 다음의 몇가지 DDL을 허용한다.

- ALTER INDEX SET PERSISTENT = ON/OFF
- ALTER INDEX REBUILD PARTITION
- GRANT OBJECT
- REVOKE OBJECT
- CREATE TRIGGER
- DROP TRIGGER

복제 대상 테이블에 허용된 DDL

일반적으로 복제 대상 테이블에 데이터 정의어(DDL)를 수행하면, 소스 커넥터는 현재 DDL 이전에 발생한 모든 변경 사항을 Kafka에 전달한 후 FAILED 상태로 변경된다.

소스 커넥터가 FAILED 상태가 되면, Sink DB에 동일한 DDL을 수행하여 테이블 스키마를 동일하게 만든 후 소스 커넥터를 restart하여 복제를 다시 수행할 수 있다.

그 외 수행할 수 있는 DDL은 *Replication Manual* 의 '이중화 대상 테이블에 DDL 실행'을 참조하기 바란다.

## 오프라인 옵션

Altibase 커넥터를 이용하여 Altibase에서 변경된 데이터를 Sink DB에 적용하는 환경에서, 서비스를 제공하는 Altibase 서버에서 장애가 발생하면 Sink DB에 적용하지 못한 로그를 전송할 수 없게 된다.

이 때 Altibase 서버에 META_LOGGING Option을 수행 중이고, Altibase 서버와 동일한 데이터베이스 구성을 가진 Standby 서버가 있다면 Standby 서버에서 오프라인 옵션으로 장애가 발생한 Altibase 서버의 로그 파일에 직접 접근하여 미전송 로그를 가져와서 Sink DB에 반영할 수 있다.

l META_LOGGING

송신자 메타 정보와 재시작 SN 정보를 파일로 남겨서 장애 발생시 Standby 서버에서 미전송 로그를 읽어 올 때 필요한 메타 정보를 구성할 수 있게 한다. 파일은 로그 파일 경로의 ala_meta_files 폴더 안에 생성된다.

l SET OFFLINE ENABLE WITH 'log_dir'

오프라인 이중화 옵션을 사용할 수 있도록 설정한다. 이중화가 중지되어 있는 상태에서만 이 구문을 수행할 수 있다. 장애가 발생한 Altibase 서버의 로그 파일 경로를 설정하여 Standby 서버가 직접 로그 파일에 접근하도록 한다.

l SET OFFLINE DISABLE

오프라인 이중화 옵션을 사용하지 못하도록 설정한다. 이중화가 중지되어 있는 상태에서만 이 구문을 수행할 수 있다.

l BUILD OFFLINE META

설정된 로그 파일 경로의 ala_meta_files 폴더에서 송신자 메타 파일과 재시작 SN 파일을 읽어 오프라인 이중화에 필요한 메타 정보를 구성한다.

l RESET OFFLINE META

RESET OFFLINE META 명령어는 BUILD OFFLINE META 실행 후 오프라인 이중화의 메타 정보를 초기화할 때 사용한다. 다음과 같은 상황에서 수행할 수 있다.

n 오프라인 이중화 수행 중 에러가 발생해서 메타 정보를 새로 구성해야 하는 경우

n 오프라인 이중화를 수행할 필요가 없어 메타 정보가 더 이상 필요하지 않은 경우

단, 오프라인 이중화를 수행하는 중에 DDL 로그로 인해 에러가 발생할 때는 RESET OFFLINE META를 수행하지 않아도 된다. 이 경우 RESET OFFLINE META를 실행하면 DDL 로그를 계속 다시 읽어 에러가 반복 발생할 수 있다.

l START WITH OFFLINE

설정된 오프라인 경로를 이용하여 이중화를 수행한다. 오프라인 이중화는 일회성 작업으로써, 미전송된 로그를 모두 반영한 후 바로 종료된다. 오프라인 이중화가 종료된 후에는 다시 이중화를 시작할 수 있다.

오프라인 이중화를 수행 할 때 이중화 갭에 DDL 로그가 포함되어 있으면 작업이 중단된다. 이때, 사용자는 Active 서버에서 수행한 DDL 문을 오프라인 이중화를 수행하는 서버에서도 수행했는지 확인하고 다시 오프라인 이중화를 수행해야 한다.

 

### 제약사항

l 송신자 메타 정보 파일과 재시작 SN 파일의 읽기, 쓰기 기능은 ALA만 사용할 수 있다.

l 오프라인 이중화를 수행할 Standby 서버의 ALA 객체 이름은 Active 서버의 ALA 객체 이름과 동일해야 한다.

l 압축 테이블을 이중화 대상으로 가지는 ALA 객체에 대해서는 오프라인 이중화를 지원하지 않는다.

l 오프라인 이중화가 디스크 이상으로 Active 서버의 로그 파일과 송신자 메타 파일 경로에 접근하지 못할 경우에는 실패한다.

l Active 서버와 Standby 서버의 로그 파일 크기는 동일해야 한다. 로그 파일 크기는 데이터베이스 생성 시에 정해지므로 오프라인 옵션을 사용하기 전에 이를 꼭 확인하여야 한다.

l 로그 파일과 송신자 메타 파일을 사용자 임의로 변경(이름 변경, 다른 시스템에 로그 파일을 복제, 삭제)할 경우 비정상 종료와 같은 문제를 발생시킬 수 있다.

l Standby 서버에 BUILD OFFLINE META 수행 후 재 구동할 경우 로그를 분석하는데 사용할 Remote Meta 정보가 사라지기 때문에 BUILD OFFLINE META를 다시 수행해야 한다.

l META_LOGGING Option을 사용할 경우 ALA도 이중화와 동일하게 갭을 Archive 로그로 처리 하지 않는다.

두 Altibase 서버의 SM버전, OS, OS비트수 (32또는 64) 또는 로그 파일의 크기가 서로 다르면, 오프라인 이중화를 시작하거나 오프라인 옵션으로 ALA 객체를 생성할 때 실패한다.

<br/>

# 부록 A.예외 상황(Exception Cases) 및 해결 방안

이 장에서는 Altibase 커넥터에서 확인될 수 있는 예외 상황과 해결 방안에 대해 설명한다.

## 소스 커넥터에서 예외 상황 및 해결 방안

#### "Received REPL_STOP message from Source DB."

##### 원인

이중화 중지

##### 해결 방안

태스크 또는 커넥터를 재시작 한다.

#### "Received CHANGE_META message from Source DB."

##### 원인

이중화 메타 변경

##### 해결 방안

태스크 또는 커넥터를 재시작 한다.

#### "Failed to convert XLog to SourceRecord."

Message2: Column count is mismatched. Replication: <*COLUMN_COUNT_META*>, XLog: <*COLUMN_COUNT_XLOG*>

##### 원인

Source DB의 이중화 대상 테이블에 SUPPLEMENTAL LOG DATA 설정이 되어있지 않았을 때 UPDATE DML을 수신하면 발생

##### 해결 방안

이중화 대상 테이블에 아래의 쿼리를 수행.

```sql
ALTER TABLE table_name ADD SUPPLEMENTAL LOG DATA ( ALL ) COLUMNS;
```

#### "Receiver thread is failed."

Message2: ALA_EnableLogging(): 335873, Failed to open log file

##### 원인

로그 파일 생성 불가

##### 해결 방안

* ala.log.directory 프로퍼티 값 확인

* 대상 디렉토리 유효성 또는 권한 확인

#### "Receiver thread is failed."

Message2: Receiving XLog timeout.

##### 원인

XLog 수신 대기 timeout

##### 해결 방안

ala.receive.xlog.timeout 프로퍼티 값을 변경한다.

#### "Receiver thread is failed."

Message2: ALA_Handshake(): Failed to wake up sender DB.

##### 원인

ala.sender.port 값이 0이 아닐 때, XLog 송신자 wake up 불가

##### 해결 방안

* wake up 필요하지 않으면 ala.sender.port 값을 0으로 변경.

* ala.sender.port 값을 sender의 이중화 포트 번호로 변경

## 싱크 커넥터에서 예외 상황 및 해결 방안

#### "Exiting WorkerSinkTask due to unrecoverable exception"

Message2: Communication link failure: Connect timed out
Message3: java.sql/java.sql.DriverManager.getConnection

##### 원인

해당 connection url로 연결 불가

##### 해결 방안

* connection.url 값을 유효한 값으로 변경
* 네트워크 상태 확인
* DBMS 상태 확인

#### "Exiting WorkerSinkTask due to unrecoverable exception"

##### Message2: Invalid password

##### 원인

유효하지 않은 비밀번호

##### 해결 방안

connection.password 값을 유효한 값으로 변경

#### "Exiting WorkerSinkTask due to unrecoverable exception"

##### Message2: User not found

##### 원인

사용자가 존재하지 않음

##### 해결 방안

* connection.user 값을 유효한 값으로 변경

* Sink DB에서 해당 사용자 확인

#### "Exiting WorkerSinkTask due to unrecoverable exception"

Message2: The row already exists in a unique index.

##### 원인

동일 primary key를 가지는 메시지가 전송됨

##### 해결 방안

* DLQ 사용

* insert.mode 값을 upsert 또는 update로 변경

#### "Exiting WorkerSinkTask due to unrecoverable exception"

Message2: Sink connector '*CONNECTOR_NAME*' is configured with 'delete.enabled=false' and 'pk.mode=none' and therefore requires records with a non-null Struct value and non-null Struct schema, but found record at

##### 원인

delete.enabled 값이 false인 상태에서 tombstone 메시지가 전달됨

##### 해결 방안

* DLQ 사용

* delete.enabled 값을 true로 변경하고, pk.mode 값을 record_key로 변경

* 소스 커넥터의 data.skip.delete 값을 true로 변경

#### "Exiting WorkerSinkTask due to unrecoverable exception"

Message2: Table \“*TABLE_NAME*\“ is missing and auto-creation is disabled

##### 원인

대상 테이블이 존재하지 않음

##### 해결 방안

- 사용자 이름 확인
- 테이블 확인 ( 생성 여부 및 이름의 대소문자 여부 )
- 대소문자 문제인 경우 quote.sql.identifiers 값을 never로 변경
- table.types 값이 대상 테이블의 타입과 동일한지 확인
- 존재하지 않는 테이블을 생성하고자 할 경우, auto.create 값을 true로 변경

#### "Exiting WorkerSinkTask due to unrecoverable exception"

Message2: Table \“*TABLE_NAME*\“ is missing fields (*SCHEMA_INFO*) and auto-evolution is disabled

##### 원인

대상 컬럼이 존재하지 않음

##### 해결 방안

* 테이블 스키마 확인
* 테이블 스키마 변경을 원하는 경우, auto.evolve 값을 true로 변경

#### "Exiting WorkerSinkTask due to unrecoverable exception"

Message2: Write to table '\“*TABLE_NAME*\“' in UPSERT mode requires key field names to be known, check the primary key configuration

##### 원인

insert.mode 값이 upsert 인데 pk.mode 값이 none임

##### 해결 방안

* insert.mode 값 변경
* pk.mode 값 설정

#### "Exiting WorkerSinkTask due to unrecoverable exception"

Message2: PK mode for table '*TABLE_NAME*' is RECORD_KEY with configured PK fields [*COLUMN_NAME*], but record key schema does not contain field: *COLUMN_NAME*

##### 원인

primary key 목록에 없는 컬럼을 pk.fields 컬럼에 추가함

##### 해결 방안

* pk.fields 컬럼 확인

* 테이블 스키마 확인

#### "Exiting WorkerSinkTask due to unrecoverable exception"

Message2: PK mode for table '*TABLE_NAME*' is RECORD_VALUE with configured PK fields [*COLUMN_NAME*], but record value schema does not contain field: *COLUMN_NAME*

##### 원인

value 목록에 없는 컬럼을 pk.fields 컬럼에 추가함

##### 해결 방안

* pk.fields 컬럼 확인

* 테이블 스키마 확인

#### "Exiting WorkerSinkTask due to unrecoverable exception"

Message2: No fields found using key and value schemas for table: *TABLE_NAME*

##### 원인

key 목록 또는 value 목록의 컬럼 중 아무것도 whitelist에 존재하지 않음

##### 해결 방안

* fields.whitelist 값 확인

* 테이블 스키마 확인

#### "Exiting WorkerSinkTask due to unrecoverable exception"

Message2: Batch update exception occurred: [Batch 1]:Unable to insert (or update) NULL into NOT NULL column. : *COLUMN_NAME*

##### 원인

- not null 컬럼에 null 값을 입력할 경우 발생
- NOT NULL 제약사항이 있고, DEFAULT 값이 설정되지 않은 컬럼을 fields.whitelist에 추가하지 않음

##### 해결 방안

* fields.whitelist 값 확인
* 테이블 스키마 확인

#### "Exiting WorkerSinkTask due to unrecoverable exception"

Message2: java.sql.SQLException: Invalid use of host variables
Message3: 0001 : MERGE INTO \“*TABLE_NAME*\“ USING ( ... ) INCOMING ON( ... ) WHEN MATCHED THEN UPDATE SET ... WHEN NOT MATCHED THEN INSERT( … ) VALUES( … )

##### 원인

Sink DB의 COERCE_HOST_VAR_IN_SELECT_LIST_TO_VARCHAR 프로퍼티 값이 0일 때 발생

##### 해결 방안

* insert.mode 값을 insert 또는 update로 변경

* Sink DB의 COERCE_HOST_VAR_IN_SELECT_LIST_TO_VARCHAR 값을 유효한 값으로 변경 후 재시작

#### "Exiting WorkerSinkTask due to unrecoverable exception"

Message2: java.sql.SQLException: SQL syntax error
      line 1: missing or invalid syntax
      UPDATE \“*TABLE_NAME*\“ SET WHERE \“*COLUMN_NAME*\“ = ?

##### 원인

insert.mode 값이 update 로 설정되어 있을 때, tombstone 메시지를 수신함

##### 해결 방안

* insert.mode 값을 insert 또는 upsert로 변경

* 소스 커넥터의 data.skip.delete 값을 true로 변경

#### "No matching QuoteMethod found for "

##### 원인

quote.sql.identifiers 값이 빈 값일 때 발생

##### 해결 방안

quote.sql.identifiers 값을 유효한 값으로 변경

#### "Not a valid JDBC URL"

##### 원인

JDBC URL 형식이 비정상적임

##### 해결 방안

connection.url 값을 유효한 값으로 변경