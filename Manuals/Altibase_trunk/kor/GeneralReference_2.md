<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [General Reference](#general-reference)
  - [2.Altibase 프로퍼티](#2altibase-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [세션 관련 프로퍼티](#%EC%84%B8%EC%85%98-%EA%B4%80%EB%A0%A8-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [타임아웃 관련 프로퍼티](#%ED%83%80%EC%9E%84%EC%95%84%EC%9B%83-%EA%B4%80%EB%A0%A8-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [트랜잭션 관련 프로퍼티](#%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98-%EA%B4%80%EB%A0%A8-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [백업 및 복구 관련 프로퍼티](#%EB%B0%B1%EC%97%85-%EB%B0%8F-%EB%B3%B5%EA%B5%AC-%EA%B4%80%EB%A0%A8-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [이중화 프로퍼티](#%EC%9D%B4%EC%A4%91%ED%99%94-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [네트워크 관련 프로퍼티](#%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC-%EA%B4%80%EB%A0%A8-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [메시지 로그 관련 프로퍼티](#%EB%A9%94%EC%8B%9C%EC%A7%80-%EB%A1%9C%EA%B7%B8-%EA%B4%80%EB%A0%A8-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [데이터베이스 링크 관련 프로퍼티](#%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4-%EB%A7%81%ED%81%AC-%EA%B4%80%EB%A0%A8-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [감사 관련 프로퍼티](#%EA%B0%90%EC%82%AC-%EA%B4%80%EB%A0%A8-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [에이전트 관련 프로퍼티](#%EC%97%90%EC%9D%B4%EC%A0%84%ED%8A%B8-%EA%B4%80%EB%A0%A8-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [사용자 계정 보안 관련 프로퍼티](#%EC%82%AC%EC%9A%A9%EC%9E%90-%EA%B3%84%EC%A0%95-%EB%B3%B4%EC%95%88-%EA%B4%80%EB%A0%A8-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [Altibase Sharding 관련 프로퍼티](#altibase-sharding-%EA%B4%80%EB%A0%A8-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [기타 프로퍼티](#%EA%B8%B0%ED%83%80-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Altibase® Administration

# General Reference

![](media/GeneralReference/e5cfb3761673686d093a3b00c062fe7a.png)

Altibase Administration General Reference

Release 7.1

Copyright ⓒ 2001\~2018 Altibase Corp. All Rights Reserved.

본 문서의 저작권은 ㈜알티베이스에 있습니다. 이 문서에 대하여 당사의 동의
없이 무단으로 복제 또는 전용할 수 없습니다.

**㈜알티베이스**

08378 서울시 구로구 디지털로 306 대륭포스트타워Ⅱ 10층

전화: 02-2082-1114 팩스: 02-2082-1099

고객서비스포털: <http://support.altibase.com>

homepage: [http://www.altibase.com](http://www.altibase.com/)

## 2.Altibase 프로퍼티

### 세션 관련 프로퍼티

Altibase는 클라이언트-서버 구조로 사용 가능하며 세션 연결 프로퍼티는
클라이언트와 서버의 통신에 관한 프로퍼티를 규정하는 것이다. 다음과 같은
프로퍼티들이 있다.

#### CM_DISCONN_DETECT_TIME (단위: 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

3

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 2<sup>32</sup>-1]

##### 설명

세션 관리 쓰레드의 동작 주기를 설정하기 위한 프로퍼티이다. Altibase 서버에는
클라이언트와 서버의 연결이 단절되었는지 검사하기 위해 세션 관리 쓰레드가
존재한다.

일반적으로 클라이언트 프로세스가 비정상 종료하면 그 클라이언트와 연결된 세션은
곧바로 그 상태를 감지할 수 있다.

그러나 세션에서 수행 중인 작업이 세션 작업과는 무관한 Altibase 서버 내부의
작업이면서 오랜 시간을 요구하는 작업이라면, 해당 세션은 클라이언트 비정상 종료
여부를 확인할 수 없다. 즉 클라이언트와 연결이 종료되었는지를 해당 세션에서는
확인할 수 없기 때문에 클라이언트가 비정상 종료되었음에도 불구하고 Altibase
서버는 그 작업을 계속 진행하게 된다.

위와 같은 경우 그러한 세션을 감지하여 해당 트랜잭션들을 롤백시킬 필요가 있으며
이를 위해 세션 관리 쓰레드가 주기적으로 세션들의 상태를 검사하게 된다.

#### CONCURRENT_EXEC_DEGREE_DEFAULT

##### 데이터 타입

Unsigned Integer

##### 기본값

4

##### 속성

변경 가능, 단일 값

##### 값의 범위

[2, 1024]

##### 설명

각 세션에서 DBMS_CONCURRENT_EXEC 패키지를 이용하여 동시에 실행시킬 수 있는
프로시저 개수를 설정한다. 만약 사용자가 저장 패키지의 INITIALIZE 함수로 병렬
처리할 프로시저의 개수를 지정하지 않으면, 이 프로퍼티의 값이 적용된다.

그러나 Altibase서버에서 저장 패키지를 이용하여 수행될 수 있는 프로시저의 개수는
CONCURRENT_EXEC_DEGREE_MAX 프로퍼티의 값보다 클 수 없다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### CONCURRENT_EXEC_DEGREE_MAX

##### 데이터 타입

Unsigned Integer

##### 기본값

CPU 개수

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1024]

##### 설명

Altibase서버에서 DBMS_CONCURRENT_EXEC 패키지를 이용하여 실행시킬 수 있는 병렬
프로시저의 최대 개수를 설정한다.

이 프로퍼티의 값을 0으로 설정한 경우 DBMS_CONCURRENT_EXEC 패키지가 동작하지
않는다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 없다.

#### CONCURRENT_EXEC_WAIT_INTERVAL

##### 데이터 타입

Unsigned Integer

##### 기본값

100

##### 속성

변경 가능, 단일 값

##### 값의 범위

[10, 1000000]

##### 설명

DBMS_CONCURRENT_EXEC 패키지에서 요청한 프로시저가 정상적으로 동작하는지 여부를
검사하는 간격을 설정한다.

이 프로퍼티의 값은 DBMS_CONCURRENT_EXEC 패키지에서 REQUEST 함수와 WAIT_REQ
함수에 영향을 준다. 이 함수들은 패키지를 이용하여 요청된 프로시저의 작업이
완료될 때까지 기다리기 때문이다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### DEFAULT_THREAD_STACK_SIZE(단위 : 바이트)

##### 데이터 타입

Unsigned Integer

##### 기본값

10485760 (10MB)

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1048576, 134217728]

##### 설명

모든 쓰레드의 스택 사이즈를 지정한다.

#### IPC_CHANNEL_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 65535]

##### 설명

클라이언트와 서버 사이에 IPC 통신을 하기 위하여 반드시 설정되어야 하는
프로퍼티이다. IPC를 이용한 클라이언트와 서버 통신 채널의 최대 개수를 지정한다.
각 채널 수에 비례해서 공유 메모리와 세마포어를 할당받기 때문에 서버에 동시에
연결할 수 있는 최대 IPC 연결 개수를 설정하는 것은 중요하다.

#### IPC_FILEPATH

##### 데이터 타입

String

##### 기본값

\$ALTIBASE_HOME/trc/cm-ipc

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

Altibase 서버가 유닉스 환경에서 IPC 방식으로 클라이언트와 연결하기 위해 생성하는
소켓 파일이다.

서버를 구동하면 \$ALTIBASE_HOME/trc 디렉토리 아래에 cm-ipc로 소켓 파일이
생성되며, 이 파일은 삭제되지 않도록 주의해야 한다.

#### IPCDA_CHANNEL_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 65535]

##### 설명

클라이언트와 서버 사이에 IPCDA 통신을 하기 위하여 반드시 설정되어야 하는
프로퍼티이다.

IPCDA를 이용한 클라이언트와 서버간 통신 채널의 최대 개수를 지정한다. 채널 개수에
비례하여 공유 메모리와 세마포어를 할당받기 때문에 서버에 동시에 연결할 수 있는
최대 IPCDA 연결 개수를 설정하는 것이 중요하다. IPCDA의 채널 개수는 CPU 코어
개수의 1/2 값이 최적화된 값이다.

#### IPCDA_DATABLOCK_SIZE (단위: 킬로 바이트)

##### 데이터 타입

Unsigned Integer

##### 기본값

20480

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[32, 102400]

##### 설명

IPCDA를 이용하는 통신 채널 한 개의 공유 메모리의 크기를 설정하는 프로퍼티이다.
이 값을 1000으로 하고, IPCDA_CHANNEL_COUNT를 24로 하는 경우 서버에서 통신 채널로
사용되는 전체 메모리의 크기(IPCDA_CHANNEL_COUNT \* IPCDA_DATABLOCK_SIZE)는
1000KB \* 24 = 24000KB가 된다.

이 값은 시스템 메모리의 크기에 따라 공유 메모리를 사용하는 다른 프로그램의
운영에 장애가 되지 않도록 적절한 값을 설정해야 한다. 예를 들어 사용자의 시스템
메모리가 4GB인 시스템에서는 IPCDA_CHANNEL_COUNT를 24로 할 경우,
IPCDA_DATABLOCK_SIZE는 최댓값으로 하여도, 실제 사용 메모리는 2457600KB를
사용하기 때문에 최댓값으로 설정할 수 있다.

#### IPCDA_FILEPATH

##### 데이터 타입

String

##### 기본값

\$ALTIBASE_HOME/trc/cm-ipcda

##### 속성

읽기 전용, 다중 값

##### 값의 범위

없음

##### 설명

Altibase 서버가 유닉스 환경에서 IPCDA 방식으로 클라이언트와 연결하기 위해
생성하는 소켓 파일이다.

서버를 구동하면 \$ALTIBASE_HOME/trc 디렉토리 아래에 cm-ipcda로 소켓 파일이
생성되며, 이 파일은 삭제되지 않도록 주의해야 한다.

#### MAX_LISTEN

##### 데이터 타입

Unsigned Integer

##### 기본값

128

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 16384]

##### 설명

클라이언트와 Altibase 간의 통신 시 TCP/IP 또는 UNIX DOMAIN 소켓을 사용하는 경우
대기 큐(listen queue)의 크기를 지정하는 값이다.

#### MAX_STATEMENTS_PER_SESSION

##### 데이터 타입

Unsigned Integer

##### 기본값

1024

##### 속성

변경 가능, 단일 값

##### 값의 범위

[1, 65535]

##### 설명

한 세션에서 실행 가능한 statement의 최대 개수를 지정한다.

Altibase 운영 중 ALTER SYSTEM 또는 ALTER SESSION 문을 이용하여 이 프로퍼티의
값을 변경할 수 있다.

#### NET_CONN_IP_STACK

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1, 2]

##### 설명

클라이언트 서버간의 TCP/IP통신을 위해서 서버 측에 소켓을 생성할 때 사용하는
인터넷 프로토콜 스택을 지정한다.

0: IPv4만을 지원하는 인터넷 프로토콜 스택을 사용하게 된다.

1: 듀얼 스택 (IPv4와 IPv6 모두 지원하는 인터넷 프로토콜 스택)이 사용된다.

2: IPv6만을 지원하는 인터넷 프로토콜 스택을 사용하게 된다.

#### NLS_COMP

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

데이터베이스 생성시 지정된 캐릭터셋(character set)의 캐릭터들의 순서는 해당
국가에서 사용되는 사전과 그 이진 값의 순서가 동일하다고 보장할 수 없다.

이 프로퍼티의 값이 1로 설정되면, 각 캐릭터셋을 해당 언어의 사전 순서대로
비교한다. 현재 한국어에 대해서만 지원하기 때문에, 데이터베이스 캐릭터셋이
한글(KSC5601 완성형 또는 MS확장 완성형)로 설정됐을 때에만 지원한다.

#### NLS_CURRENCY

##### 데이터 타입

String

##### 기본값

NLS_TERRITORY의 값을 따른다.

##### 속성

변경 가능, 단일 값

##### 값의 범위

최대 10바이트 길이의 문자

##### 설명

지역 통화 기호를 지정하는 프로퍼티이다. 숫자형 데이터 형식 L을 통해 지역 통화
기호를 표시할 때 이 프로퍼티의 값이 사용된다. 이 프로퍼티의 값은 +, -, \<, \>
기호로 시작할 수 없다.

Altibase 운영 중 아래와 같이 ALTER SESSION문을 이용하여 이 프로퍼티의 값을
변경할 수 있다:

```
ALTER SESSION SET NLS_CURRENCY = '$';
```

> 주의: 아랍권의 통화 기호가 정확히 표시되려면 클라이언트 응용 프로그램(또는
> 쉘이나 에디터)이 아랍 문자의 표시를 지원해야 한다.

#### NLS_ISO_CURRENCY

##### 데이터 타입

String

##### 기본값

NLS_TERRITORY의 값을 따른다.

##### 속성

변경 가능, 단일 값

##### 값의 범위

V\$NLS_TERRITORY 성능 뷰에 존재하는 값

##### 설명

ISO 통화 기호를 지정하는 프로퍼티이다. 숫자형 데이터 형식 C를 통해 국제 통화
기호를 표시할 때 이 프로퍼티의 값이 사용된다. 이 프로퍼티에 지정할 수 있는 값은
V\$NLS_TERRITORY 성능 뷰에 존재하는 값(지역)에 한정된다.

Altibase 운영 중 아래와 같이 ALTER SESSION문을 이용하여 이 프로퍼티의 값을
변경할 수 있다:

```
ALTER SESSION SET NLS_ISO_CURRENCY = America;
```

#### NLS_NCHAR_CONV_EXCP

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

NCHAR 데이터 타입의 데이터를 다른 캐릭터셋으로 변환 시, 데이터 손실이 발생할 수
있다. 이 때 에러를 발생시킬 것인지 아니면 데이터 손실이 발생한 채로 변환을 할
것인지를 결정하는 프로퍼티이다.

이 프로퍼티는 서버에서 NCHAR타입 데이터를 다른 캐릭터셋으로 변환할 때에만 에러를
발생시킨다.

Altibase 운영 중 ALTER SESSION 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

0: FALSE (에러를 발생시키지 않는다.)

1: TRUE

#### NLS_NCHAR_LITERAL_REPLACE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

기본적으로 클라이언트는 쿼리 문 전체를 데이터베이스 문자 셋으로 변환하여
전송한다. 그러나, 특정 리터럴에 대해 이런 동작을 막으려면, 이 프로퍼티의 값을
1로 설정하고 그 리터럴 앞에 "N" 문자를 덧붙이면 된다. 즉, NCHAR 리터럴로 만드는
것이다.

이 프로퍼티의 값이 1일 때, 클라이언트는 쿼리 문 내의 모든 리터럴 앞에 "N" 문자가
있는지 찾는다. 만약 찾게 되면 클라이언트는 그 리터럴을 데이터베이스 문자 셋으로
변환하지 않고 그대로 전송하며 서버가 직접 내셔널 문자 셋으로 변환한다. 이것은
데이터베이스 문자 셋과는 다른 인코딩이 필요한 NCHAR 타입 데이터를 사용하고자 할
때 유용하다.

Altibase 운영 중 ALTER SESSION 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

0: "N" 문자가 있는지 검사하지 않고 쿼리 문 전체를 데이터베이스 문자 셋으로
변환한다.

1: "N" 문자가 붙어있는 NCHAR 리터럴은 데이터베이스 문자 셋으로 변환하지 않는다.

> 주의: 이 값을 1로 설정하는 것은 클라이언트의 비용이 크게 발생하므로, 사용시
> 주의가 필요하다.

#### NLS_NUMERIC_CHARACTERS

##### 데이터 타입

String

##### 기본값

NLS_TERRITORY의 값을 따른다.

##### 속성

변경 가능, 단일 값

##### 값의 범위

없음

##### 설명

소수점 문자와 그룹 구분자를 지정하는 프로퍼티이다. 그룹 구분자는 숫자에서
천단위로 구분해서 표기할 때 사용되며 일반적으로 쉼표(,)가 사용된다. 소수점
문자는 일반적으로 마침표(.)가 사용된다. 이 프로퍼티는 +, -, \<, \> 기호로 시작할
수 없다.

이 프로퍼티에 지정한 문자열에서 처음 두 개의 문자만 각각 소수점 문자와 그룹
구분자로 설정되고 나머지 문자는 무시된다.

Altibase 운영 중 아래와 같이 ALTER SESSION문을 이용하여 이 프로퍼티의 값을
변경할 수 있다:

```
ALTER SESSION SET NLS_NUMERIC_CHARACTERS='.,';
```

#### NLS_TERRITORY

##### 데이터 타입

String

##### 기본값

KOREA

##### 속성

변경 가능, 단일 값

##### 값의 범위

V\$NLS_TERRITORY 성능 뷰에 존재하는 값

##### 설명

지역의 이름을 지정하는 프로퍼티이다. 이 프로퍼티에 지정한 지역에 따라
NLS_NUMERIC_CHARACTER, NLS_CURRENCY, 및 NLS_ISO_CURRENCY 프로퍼티의 값이
자동으로 변경된다. V\$NLS_TERRITORY 성능 뷰를 조회해서 이 프로퍼티에 지정 가능한
지역의 이름을 확인할 수 있다.

Altibase 운영 중 아래와 같이 ALTER SESSION문을 이용하여 이 프로퍼티의 값을
변경할 수 있다. 지역의 이름은 대소문자를 구분하지 않으며, 작은 따옴표(')를
사용할 수 있다.

```
ALTER SESSION SET NLS_TERRITORY = America;
or
ALTER SESSION SET NLS_TERRITORY = 'America';
```

#### PORT_NO

##### 데이터 타입

Unsigned Integer

##### 기본값

20300

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1024, 65535]

##### 설명

TCP/IP로 클라이언트와 서버가 통신할 때 사용하는 포트 번호이다. 사용자는 루트
영역(일반적으로 1023번까지)을 제외한 나머지 영역(최대 65535)에 대해 다른
프로그램에서 사용하지 않는 번호면 임의로 지정할 수 있다. Altibase 응용
프로그램은 이 포트 번호를 사용하여 서버와 연결할 수 있다.

#### PSM_CURSOR_OPEN_LIMIT

##### 데이터 타입

Unsigned Integer

##### 기본값

32

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1,1024]

##### 설명

세션에서 DBMS_SQL 패키지를 사용하여 열 수 있는 커서의 개수를 지정한다.

#### PSM_FILE_OPEN_LIMIT

##### 데이터 타입

Unsigned Integer

##### 기본값

16

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0,128]

##### 설명

세션당 최대로 열 수 있는 저장 프로시저 파일 핸들의 개수를 지정한다.

#### TIME_ZONE

##### 데이터 타입

String

##### 기본값

OS_TZ

##### 속성

변경 가능, 단일 값

##### 값의 범위

V\$TIME_ZONE_NAMES 성능 뷰에 존재하는 값

##### 설명

타임 존을 설정하는 프로퍼티이다. 해당되는 지역 이름이나 약어 또는 UTC 오프셋(예.
+09:00)과 같은 문자열로 지정할 수 있다.

Altibase 운영 중 ALTER SESSION 문을 이용하여 해당 세션의 타임 존을 변경할 수
있다.

#### UNIXDOMAIN_FILEPATH

##### 데이터 타입

String

##### 기본값

\$ALTIBASE_HOME/trc/cm-unix

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

Altibase 서버가 유닉스 도메인 방식으로 클라이언트와 연결하기 위해 생성하는 소켓
파일이다.

서버를 구동하면 \$ALTIBASE_HOME/trc 디렉토리 아래에 cm-unix로 기본 소켓 파일이
생성되며, 이 파일은 삭제되지 않도록 주의해야 한다.

#### USE_MEMORY_POOL

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0,1]

##### 설명

메모리 풀링 기능의 사용 유무를 지정한다. 메모리 풀링이란 서버에서 메모리를 미리
할당하여 사용하는 기능이다.

이 기능을 사용하면, 메모리를 미리 할당하기 때문에 메모리 사용량이 많아진다.

0: 사용하지 않음

1: 사용

#### USER_LOCK_POOL_INIT_SIZE(단위 : 개수)

##### 데이터 타입

Unsigned Integer

##### 기본값

128

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[128, 10000]

##### 설명

데이터베이스에서 사용자 잠금(User Lock)을 사용할 수 있는 개수를 설정할 수 있다.

이 프로퍼티의 값을 초과하여 사용자 잠금의 개수를 사용할 수 있으나, 성능 저하가
발생할 수 있다. 또한 한 번 생성된 사용자 잠금을 해제하여도 제거되는 것은
아니므로, 해제된 사용자 잠금을 재사용하는 것이 효과적이다.

#### USER_LOCK_REQUEST_CHECK_INTERVAL(단위 : 마이크로 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

10000

##### 속성

변경 가능, 단일 값

##### 값의 범위

[10, 999999]

##### 설명

다른 세션이 사용자 잠금(User Lock)을 획득할 수 있는지 검사하는 주기를 설정한다.
다른 세션에서 현재 사용중인 사용자 잠금을 요청하면, 사용자 잠금이 해제되기
전까지 세션이 대기한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### USER_LOCK_REQUEST_LIMIT(단위 : 개수)

##### 데이터 타입

Unsigned Integer

##### 기본값

10

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 10000]

##### 설명

하나의 세션이 요청할 수 있는 사용자 잠금(User Lock)의 개수를 설정한다. Altibase
운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### USER_LOCK_REQUEST_TIMEOUT(단위 : 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

10

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

세션에서 사용자 잠금(User Lock)을 요청한 후 획득할 때까지 대기하는 최대 시간을
설정한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### XA_HEURISTIC_COMPLETE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2]

##### 설명

PREPARE 상태(IN_DOUBT 상태)인 전역 트랜잭션을 일정 시간이 지나면 임의로 종료시킬
수 있는 프로퍼티이다. 이 때 COMMIT으로 종료시킬 것인지, ROLLBACK으로 종료시킬
것인지를 선택할 수 있으며, 트랜잭션을 종료시킬 때 명령을 기다리는 시간은
XA_INDOUBT_TX_TIMEOUT 프로퍼티에 정의된 값을 사용한다.

0: 종료하지 않음.

1: 트랜잭션 커밋

2: 트랜잭션 롤백

분산 트랜잭션 환경에서는 2 단계 커밋 프로토콜(2 Phase Commit Protocol, XA)을
사용하여 트랜잭션을 수행한다. 트랜잭션을 수행중에 전역(global) 트랜잭션
관리자(Coordinator)로부터 PREPARE 명령을 받은 후 COMMIT이나 ROLLBACK 명령을 받지
못한 상태가 오래 지속될 경우, 데이터베이스 성능에 영향을 줄 수 있다.

### 타임아웃 관련 프로퍼티

#### BLOCK_ALL_TX_TIME_OUT (단위: 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

3

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

버퍼 매니저가 해쉬 테이블의 크기를 조정할 때 트랜잭션의 접근을 제한할 수 있다.
이 프로퍼티의 최소값 0은 대기하지 않고 즉시 오류 처리됨을 의미한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### DDL_LOCK_TIMEOUT (단위 : 초)

##### 데이터 타입

Short integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[-1, 65535]

##### 설명

DDL 문을 수행할 때 해당 테이블에 이미 다른 트랜잭션에 의해 잠금(Lock)이 획득되어
있는 경우 잠금을 대기하는 옵션을 설정하는 것이다. 잠금을 요구하여 곧바로
획득되지 않을 경우 이 프로퍼티의 값이 –1로 설정되어 있으면 무한정 대기하고
양수로 설정되어 있으면 지정된 값 만큼 대기하고 다시 시도한다.

기본값은 0으로, DDL 수행시 잠금을 요구한 시점에서 잠금을 획득할 수 없는 경우
해당 DDL은 즉시 오류 처리된다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### DDL_TIMEOUT(단위 : 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

DDL 문의 실행 시간이 이 프로퍼티에 설정한 시간(초)을 초과하면, 그 구문의 실행은
취소된다. 기본 설정 값은 0으로, Altibase는 DDL 구문 수행이 끝날 때까지 무한
대기한다.

이 프로퍼티의 값은 Altibase 실행 중에 ALTER SYSTEM 또는 ALTER SESSION 구문으로
변경 가능하다.

> Note: Altibase 버전 5.5.1 까지는, DDL구문의 실행 시간도 UTRANS_TIMEOUT 과
> QUERY_TIMEOUT 프로퍼티의 영향을 받았다. DML과 DCL구문의 실행시간은 여전히
> UTRANS_TIMEOUT 과 QUERY_TIMEOUT 프로퍼티의 영향을 받는다.

#### FETCH_TIMEOUT(단위 : 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

60

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

응용 프로그램에서 SELECT 문을 수행하는 시간이 길어짐에 따라 데이터베이스
메모리가 비정상적으로 증가하는 것을 막기 위하여 이 값을 설정한다. 질의 수행
시간이 프로퍼티 파일에 설정된 값보다 커지면 세션 연결을 해제하고 현재 트랜잭션을
철회한다.

Altibase 운영 중 ALTER SYSTEM 문 또는 ALTER SESSION 문을 이용하여 이 프로퍼티의
값을 변경할 수 있다.

#### IDLE_TIMEOUT (단위 : 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

서버에 접속된 클라이언트가 비정상적으로 오랜 시간 연결을 맺고 있고, 만약 이러한
클라이언트의 수가 점차적으로 많아진다면 결국에는 서비스를 할 수 있는 연결 개수가
현저히 작아져, 나중에는 서비스가 불가능한 상황이 될 수 있다.

이러한 현상을 미리 방지하기 위해 이 값을 설정한다. 한 세션의 유휴 시간이
프로퍼티 파일에 설정된 값보다 커지면 세션 연결을 해제하고 현재 트랜잭션을
철회한다.

Altibase 운영 중 ALTER SYSTEM 문 또는 ALTER SESSION 문을 이용하여 이 프로퍼티의
값을 변경할 수 있다.

#### LOGIN_TIMEOUT(단위 : 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

Altibase의 포트로 접속이 이루어진 후 인증 절차가 완료될 때까지 허용된 시간이다.
이 시간 안에 인증이 이루어지지 않으면 서버는 접속을 끊는다.

#### MULTIPLEXING_POLL_TIMEOUT(단위 : 마이크로 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

10000

##### 속성

변경 가능, 단일 값

##### 값의 범위

[1000, 1000000]

##### 설명

멀티플렉싱을 하는 서비스 쓰레드가 세션을 감지하는 주기를 나타낸다.

#### QUERY_TIMEOUT (단위 : 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

600

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

특정 질의들(정렬 혹은 긴 조인 등)의 수행 시간이 길어짐에 따라 데이터베이스
메모리가 비정상적으로 증가하는 것을 막기 위하여 이 값을 설정한다. 질의 수행
시간이 프로퍼티 파일에 설정된 값보다 커지면 현재 트랜잭션 연산을 부분 철회한다.

Altibase 운영 중 ALTER SYSTEM 문 또는 ALTER SESSION 문을 이용하여 이 프로퍼티의
값을 변경할 수 있다.

#### SHUTDOWN_IMMEDIATE_TIMEOUT

##### 데이터 타입

Unsigned Integer

##### 기본값

60

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

IMMEDIATE 옵션으로 Altibase 서버를 종료할 때, 끝나지 않은 트랜잭션들은 롤백
처리된다. 이 프로퍼티는 트랜잭션을 롤백하기 위해 대기하는 시간을 지정한다. 이
시간을 초과하게 되면, 종료되지 않은 트랜잭션이 롤백되지 않은 채로 서버는 강제
종료된다. 이 값이 0이면, 모든 트랜잭션이 롤백될 때까지 대기한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### UTRANS_TIMEOUT (단위 : 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

3600

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

변경 연산(UPDATE, INSERT, DELETE)을 수행하는 트랜잭션의 수행 시간이 길어짐에
따라 로그 파일의 개수가 비정상적으로 증가하는 것을 막기 위하여 이 값을 설정한다.
수행 시간이 프로퍼티 파일에 설정된 값보다 커지면 세션 연결을 해제하고 현재
트랜잭션을 철회한다.

Altibase 운영 중 ALTER SYSTEM 문 또는 ALTER SESSION 문을 이용하여 이 프로퍼티의
값을 변경할 수 있다.

#### XA_INDOUBT_TX_TIMEOUT (단위: 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

60

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

2 단계 커밋 프로토콜에서 IN-DOUBT 상태의 오래 실행되는 전역 트랜잭션을 임의로
종료시키는 시간 기준에 대한 프로퍼티이다.

### 트랜잭션 관련 프로퍼티

#### AUTO_COMMIT

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

세션에서 SQL 문을 수행할 때 하나의 SQL 문을 하나의 트랜잭션으로 처리하여 커밋할
것인지를 결정하는 프로퍼티이다. 이 값이 1 이면 auto-commit 모드이고 0 이면
non-autocommit 모드이다. non-autocommit 모드인 경우 응용 프로그램에서 트랜잭션의
시작과 끝을 명시적으로 알려주어야 한다.

세션 단위로 이를 설정할 수 있는데, 서버 구동 시 AUTO_COMMIT의 값이 1일지라도
세션 별로 이 모드를 변경할 수 있다. 예를 들어, 클라이언트에서 ALTER SESSION SET
AUTOCOMMIT = FALSE (non-autocommit)를 실행하면 이 세션은 이 후에 발생하는
트랜잭션을 반영할 것인지 또는 롤백할 것인지를 사용자가 명시해 주어야 한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### ISOLATION_LEVEL

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2]

##### 설명

트랜잭션의 고립화 수준(isolation level)을 지정한다. 고립화 수준에 따라 하나의
트랜잭션이 여러 번 같은 테이블에 대한 검색을 수행할 때의 결과가 다르다.

트랜잭션의 고립화 수준에 대한 자세한 설명은 *Administrator’s Manual*을 참고하기
바란다.

| 고립화 수준         | 특징                                                         |
| ------------------- | ------------------------------------------------------------ |
| 0 (Committed Read)  | Altibase의 기본 모드이다. 검색 트랜잭션이 읽은 데이터는 완료된 다른 트랜잭션에 의해 변경된 데이터임을 보장한다. 검색 트랜잭션이 한번 읽고 다시 읽을 때 다른 트랜잭션이 동시에 INSERT 혹은 DELETE를 수행하고 커밋했다면 그것이 반영되어 새로운 행(row)이 보이거나 혹은 보였던 행이 보이지 않게 될 수 있다. |
| 1 (Repeatable Read) | 한 트랜잭션 수행 동안 동일 레코드를 여러 번 반복해서 읽는 경우 항상 동일한 레코드의 내용을 검색하게 됨을 보장한다. 한번 읽을 때 읽은 행(row)에 잠금(lock)이 걸린다. 그래서 다시 읽을 때 이전에 보였던 행이 안 보이는 경우는 없으나, 그 사이에 새로 삽입된 행은 보일 수 있다. |
| 2 (No Phantom)      | 여러 번 반복해서 읽어도 모두 동일한 결과가 보이는 것을 보장한다. |

#### TRANSACTION_TABLE_SIZE(단위 : 트랜잭션 개수)

##### 데이터 타입

Unsigned Integer

##### 기본값

1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[16,16384]

##### 설명

Altibase 서비스 중에 동시에 생성될 수 있는 트랜잭션 개수를 데이터베이스를 생성할
때 설정할 수 있으며, 이에 대해 메모리가 미리 할당된다.

이 프로퍼티는 2n 크기만큼 값을 증감시켜야 하며, 감소시킬 때에는 반드시
데이터베이스를 다시 생성해야 한다.

#### SHARED_TRANS_HASH_BUCKET_COUNT(단위 : 해시 저장소 개수)

##### 데이터 타입

Unsigned Integer

##### 기본값

1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[16,16384]

##### 설명

Altibase Sharding 서비스 중에 생성되는 공유 트랜잭션 관리를 위한 자료구조의 Hash 저장소 크기를 설정한다.

### 백업 및 복구 관련 프로퍼티

데이터베이스가 변경될 때 변경 로그를 유지하는데, 이에 관한 처리를 어떻게 할
것인지를 정하는 프로퍼티들이 있다.

#### ARCHIVE_DIR

##### 데이터 타입

String

##### 기본값

\$ALTIBASE_HOME/arch_logs

##### 속성

읽기 전용, 다중 값

##### 값의 범위

없음

##### 설명

데이터베이스를 아카이브 로그(Archivelog) 모드로 운영하는 경우 아카이브
로그파일들이 백업될 디렉토리를 설정하는 프로퍼티이다. 사용자가 명시적으로 이
값을 지정하지 않으면 기본으로 Altibase가 설치된 디렉토리 밑의 arch_logs
디렉토리에 아카이브 로그파일들이 백업된다. 이 프로퍼티의 개수는 LOG_DIR 프로퍼티
개수와 정확히 일치해야 한다.

사용자가 이 값을 명시적으로 지정할 수 있으나 지정된 디렉토리는 미리 생성되어
있어야 하며, 그렇지 않은 경우 오류 메시지를 출력함과 동시에 Altibase 서버가
구동되지 않는다.

#### ARCHIVE_FULL_ACTION

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

ARCHIVE_DIR에 설정된 디렉토리가 속한 파일 시스템에 충분한 디스크 공간이 없는
경우 아카이브 로그 백업(archive log backup)을 수행하는 아카이브로그 쓰레드의
동작을 제어하는 프로퍼티이다.

값이 0인 경우 아카이브로그 쓰레드는 오류 메시지를 출력한 후, 아카이브 로그파일을
백업하는 작업을 중지하게 된다. 이후 충분한 디스크 공간이 확보된 후에라도
사용자가 명시적으로 아카이브 로그 백업을 활성화하는 명령을 입력하지 않는 한
아카이브 로그 백업은 재개되지 않는다. 이 경우 체크포인트가 발생하면 아카이브
로그파일이 백업되지 않았더라도 불필요한 로그 파일들은 삭제되기 때문에 운영시
주의가 필요하다.

값이 1인 경우 아카이브로그 쓰레드는 충분한 디스크 공간이 확보되어 아카이브
로그파일을 백업할 수 있을 때까지 기다린다. 이 기간 동안은 체크포인트가
발생하더라도 아카이브 로그파일을 백업할 수 없기 때문에 로그 파일들은 삭제되지
않는다.

#### ARCHIVE_MULTIPLEX_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 10]

##### 설명

Altibase 서버가 아카이브 로그 파일의 복사본<sup>9</sup>을 몇 개 유지할 것인지를
지정한다. 프로퍼티 설정 이후에 새로이 아카이브 되는 로그 파일부터 복사본이
유지된다.

[<sup>9</sup>] 아카이브 로그 파일 다중화(Multiplexing Archive Logfiles): 아카이브 로그

파일을 별도의 디스크에 복사해 두어, 아카이브 로그 파일 원본의 손상에 대비하는
기능이다.

ARCHIVE_MULTIPLEX_COUNT와 ARCHIVE_MULTIPLEX_DIR 프로퍼티는 서버가
중지(shutdown)된 상태에서 설정할 수 있다.

#### ARCHIVE_MULTIPLEX_DIR

##### 데이터 타입

String

##### 기본값

""

##### 속성

읽기 전용, 다중 값

##### 값의 범위

없음

##### 설명

아카이브 로그 파일의 복사본이 위치할 경로를 지정한다. ARCHIVE_MULTIPLEX_DIR
프로퍼티는 ARCHIVE_MULTIPLEX_COUNT에 명시한 아카이브 로그 파일의 개수만큼
설정해야 한다. 이 때 각각의 경로는 서로 다른 디스크에 둘 것을 권장한다.

#### ARCHIVE_THREAD_AUTOSTART

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

아카이브 로그파일을 주기적으로 백업하는 쓰레드인 아카이브로그 쓰레드를
알티베이스 구동시 자동으로 활성화시킬 것인지를 지정하는 프로퍼티이다. 이 값을
1로 하는 경우 아카이브 쓰레드가 자동으로 활성화된다.

이 프로퍼티는 디렉토리에 아카이브 로그파일 백업을 위한 충분한 디스크 공간이
없어서 아카이브로그 쓰레드가 비활성화되면, 이후에 디스크 공간을 확보하여
아카이브로그 쓰레드를 다시 활성화하고자 할 때 사용할 수 있다.

#### CHECKPOINT_ENABLED

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

체크포인트를 ON 또는 OFF 시키는 프로퍼티이다.

0: OFF

1: ON

이 값을 0(OFF)으로 지정하면 체크포인트 쓰레드가 동작하지 않으며,
CHECKPOINT_INTERVAL_IN_SEC와 CHECKPOINT_INTERVAL_IN_LOG 프로퍼티에서 지정한
주기로 동작할 수 없다. 그러나 사용자가 명시적으로 체크포인트를 수행하면 수행할
수 있다.

#### CHECKPOINT_INTERVAL_IN_LOG

##### 데이터 타입

Unsigned Integer

##### 기본값

100

##### 속성

변경 가능, 단일 값

##### 값의 범위

[1, 2<sup>32</sup>-1]

##### 설명

체크포인트 주기를 설정하는 프로퍼티이다. 즉, 이 프로퍼티에 설정된 값만큼 로그
파일이 생성되면, 다음 체크포인트가 발생한다.

그러나 이 프로퍼티 값에 의해 체크포인트 수행이 요구될 때, 이미 체크포인트가 진행
중이거나 기타 다른 이유로 인하여 체크포인트가 수행되지 못하는 경우가 발생할 수
있다. 이 경우 이미 진행 중인 체크포인트가 끝난 후 바로 체크포인트를 수행하는
것이 아니라 현재의 체크포인트 요구는 바로 취소된다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### CHECKPOINT_INTERVAL_IN_SEC(단위 : 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

6000

##### 속성

변경 가능, 단일 값

##### 값의 범위

[3, 2592000]

##### 설명

체크포인트의 주기를 초 단위 시간으로 정하는 것이다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### COMMIT_WRITE_WAIT_MODE 

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

트랜잭션을 커밋할 때 로그가 로그 파일에 반영될 때까지 기다릴 것인지 여부를
설정하는 프로퍼티이다. Altibase는 기본으로 성능을 위해 기다리지 않는 값으로
설정된다.

이 프로퍼티는 시스템 전체에 대해서 혹은 사용자의 세션 단위로 설정할 수 있으며,
Altibase 운영 중 ALTER SYSTEM 또는 ALTER SESSION 구문으로 변경할 수 있다.

0: Do Not Wait

1: Wait

#### INCREMENTAL_BACKUP_CHUNK_SIZE

##### 데이터 타입

Unsigned Integer

##### 기본값

4

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

데이터의 페이지가 변경되는 것을 페이지 단위로 추적하기 위해 설정하는
프로퍼티이다. 예를 들어 이 프로퍼티의 값이 4로 설정되면, 4개의 페이지 단위로
변경 추적 정보를 기록하기 때문에, 한 묶음에 속하는 4개의 페이지 중 하나라도
변경된다면 그 묶음의 모든 페이지가 백업된다.

이 프로퍼티를 변경하려면 아래의 단계를 거쳐서 changeTracking 파일을 다시
생성해야 한다.

1. 서버 종료 후 프로퍼티 파일에서 값 변경
2. 서버 구동
3. 변경 추적 기능 비활성화 후 다시 활성화

#### INCREMENTAL_BACKUP_INFO_RETENTION_PERIOD

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

backupInfo 파일에 저장되는 백업 정보가 유지되는 기간(단위: 일)을 지정하는
프로퍼티이다.

ALTER DATABASE DELETE OBSOLETE BACKUP FILES 구문으로 삭제되는 백업 정보는 유효
기간이 지난 가장 오래된 레벨 0 백업부터 유효 기간이 지나지 않은 가장 오래된 레벨
0 바로 이전의 레벨 1 백업까지이다.

> 참고: 증분 백업에 대한 복구에는 레벨 0로 백업된 백업 파일이 반드시 필요하다.
> 따라서 이 프로퍼티에 지정한 유지 기간이 지난 백업 정보와 거기에 대응하는 백업
> 파일이 있더라도, 레벨 0 백업이 유일하다면, 삭제 명령을 실행하더라도 유지 기간이
> 지난 백업 정보와 백업 파일이 삭제되지 않는다.

#### LOG_BUFFER_TYPE 

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

로그 버퍼 타입을 결정하는 프로퍼티이다.

0: 운영체제 커널의 로그 버퍼를 사용

1: 프로세스 메모리의 로그 버퍼를 사용

이 프로퍼티는 시스템 운영 중에 변경할 수 없다.

#### LOG_MULTIPLEX_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 10]

##### 설명

Altibase 서버가 로그 파일의 복사본<sup>10</sup>을 몇 개 유지할 것인지를 지정한다. 원본
로그 파일이 생성되거나 삭제될 때 로그 파일의 복사본도 동시에 생성되거나
삭제된다.

[<sup>10</sup>] 로그 파일 다중화(Multiplexing Log Files): 데이터베이스의 모든 변경 사항이

기록되는 로그 파일을 별도의 디스크에 복사해 두어, 로그 파일 원본의 손상에
대비하는 기능이다.

LOG_MULTIPLEX_COUNT와 LOG_MULTIPLEX_DIR 프로퍼티는 서버가 중지(shutdown)된
상태에서 설정할 수 있다.

#### LOG_MULTIPLEX_DIR

##### 데이터 타입

String

##### 기본값

""

##### 속성

읽기 전용, 다중 값

##### 값의 범위

없음

##### 설명

로그 파일의 복사본이 위치할 경로를 지정한다. LOG_MULTIPLEX_COUNT에 명시한
개수만큼 LOG_MULTIPLEX_DIR 프로퍼티를 설정해야 한다. 또한, 각 경로를 서로 다른
디스크에 둘 것을 권장한다.

#### PREPARE_LOG_FILE_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

5

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

로그 생성시 해당 로그파일에 충분한 공간이 없으면 새로운 로그 파일을 생성하며, 이
경우 트랜잭션의 응답 시간은 늦어지게 된다. 이처럼 로그파일 생성으로 인해
트랜잭션의 수행이 늦어지는 것을 막기 위해 Altibase는 여분의 로그파일을 미리
생성해 둔다. 이 여분의 로그파일의 개수를 지정하는 것이 이 프로퍼티이다.

**SNAPSHOT_MEM_THRESHOLD(단위: 백분율)**

##### 데이터 타입

Unsigned Integer

##### 기본값

80

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 100]

##### 설명

스냅샷 설정(BEGIN SNAPSHOT) 이후 메모리 데이터베이스에서 사용할 수 있는
임계치(Threshod)를 설정하는 프로퍼티이다.

현재 사용되는 메모리의 크기는 프로퍼티 MEM_MAX_DB_SIZE의 몇 퍼센트를
사용하고 있는지 확인하고, 설정한 임계치를 초과하면 스냅샷(shapshot)은
자동으로 중지된다.

**SNAPSHOT_DISK_UNDO_THRESHOLD(단위: 백분율)**

##### 데이터 타입

Unsigned Integer

##### 기본값

80

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 100]

##### 설명

스냅샷 설정(BEGIN SNAPSHOT) 이후 디스크에서 사용할 수 있는
임계치(Threshold)를 설정하는 프로퍼티이다.

현재까지 사용된 디스크 언두 테이블스페이스의 크기는 프로퍼티
SYS_UNDO_FILE_MAX_SIZE 에서 몇 퍼센트를 사용하는지 확인하고, 설정한 임계치를
초과하면 스냅샷(shapshot)은 자동으로 중지된다.

### 이중화 프로퍼티

다음 속성값들은 데이터베이스의 이중화 기능을 위한 값들이다. 데이터베이스
이중화에 대한 자세한 내용은 *Getting Started Guide*의 데이터베이스 이중화 장과
*Replication Manual*을 참조하기 바란다.

#### REPLICATION_ACK_XLOG_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

100

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

수신 쓰레드가 송신 쓰레드에게 ACK를 보내는 주기를 나타낸다.

수신 쓰레드는 XLog를 받아서 하나씩 반영하는 작업을 하는데, 반영한 XLog의 개수가
REPLICATION_ACK_XLOG_COUNT를 넘게 되면 송신 쓰레드에게 ACK를 전송한다.

이 값이 너무 작으면 송신 쓰레드에 ACK를 자주 보내게 되어 성능 저하를 가져올 수
있다.

너무 큰 경우에는 송신 쓰레드가 ACK를 받기 위해 대기하는 시간을 초과하여 네트워크
장애로 판단할 수 있다. 또한, 오랜 시간 ACK를 받지 못하는 경우 이중화 재시작 SN이
갱신되지 않아, 체크포인트시 송신 쓰레드가 가장 최근의 로그 레코드부터 다시
시작되며, 이중화하지 못한 로그 파일이 삭제되는 현상이 발생할 수 있다.

#### REPLICATION_ALLOW_DUPLICATE_HOSTS 

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

이중화 객체들의 원격 서버 IP 주소와 포트 번호를 서로 동일하게 설정하는 것을
허용할 것인지 지정한다.

0: 허용하지 않는다.

1: 허용한다.

#### REPLICATION_BEFORE_IMAGE_LOG_ENABLE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

이중화 수신자의 "이전 이미지(before image)"가 송신자로부터 받은 XLog의 이전
이미지와 다르면 데이터 충돌이 발생할 수 있다.

사용자가 충돌이 발생한 데이터를 확인할 수 있도록, 이 프로퍼티를 설정하여
트레이스 로그에 이중화 수신자의 이전 이미지를 기록할 수 있다.

0: 기록하지 않음

1: 기록함

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_COMMIT_WRITE_WAIT_MODE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

이중화 수신자가 수신한 XLOG를 복제 트랜잭션으로 수행 완료한 후에 디스크에 반영될
때까지 기다릴지 여부를 지정한다. 이 값이 0이면 기다리지 않으며, 1이면 디스크에
반영될 때까지 기다린다.

#### REPLICATION_CONNECT_RECEIVE_TIMEOUT (단위: 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

60

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

이중화 시작시 대상 호스트에 접속을 시도한 후, 대기하는 시간이다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_CONNECT_TIMEOUT (단위: 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

10

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

이중화를 수행하기 위해 대상 호스트에 대한 연결 수행 시, 이 프로퍼티에 설정된
시간 값 이상 응답이 없을 경우 연결을 더 이상 시도하지 않는다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_DDL_ENABLE 

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

이중화 대상 테이블에 DDL 구문을 허용할 것인지를 나타낸다. 1로 설정한 경우 이중화
대상 테이블에 DDL을 실행할 수 있다.

DDL을 수행하기 전에 현재 세션에서 수행하는 트랜잭션의 이중화 프로퍼티를 NONE
이외의 값으로 설정해야 송신 쓰레드에서 DDL 실행을 알 수 있다. 이중화에서
허용하는 DDL 목록과 제약사항은 *Replication Manual*을 참조한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_DDL_ENABLE_LEVEL

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

이중화 대상 테이블에 사용할 수 있는 DDL 구문의 범위를 결정한다. 이 프로퍼티를
사용하려면 먼저 REPLICATION_DDL_ENABLE 프로퍼티의 값을 1로 설정해야 한다.
REPLICATION_DDL_ENABLE_LEVEL 값에 따라 허용되는 DDL 구문은 아래와 같다.

- REPLICATION_DDL_ENABLE_LEVEL = 0

ALTER TABLE table_name ADD COLUMN ( column_name DATA_TYPE );

ALTER TABLE table_name DROP COLUMN column_name;

ALTER TABLE table_name ALTER COLUMN column_name SET DEFAULT

ALTER TABLE table_name ALTER COLUMN column_name DROP DEFAULT

ALTER TABLE table_name TRUNCATE PARTITION

TRUNCATE TABLE table_name;

CREATE INDEX index_name ON table_name ( column_name );

DROP INDEX index_name; -- for Normal Index

- REPLICATION_DDL_ENABLE_LEVEL = 1

ALTER TABLE table_name ADD COLUMN ( column_name DATA_TYPE NOT NULL );

ALTER TABLE table_name ADD COLUMN ( column_name DATA_TYPE UNIQUE );

ALTER TABLE table_name ALTER COLUMN ( column_name NOT NULL );

ALTER TABLE table_name ALTER COLUMN ( column_name NULL );

ALTER TABLE table_name MODIFY COLUMN ( column_name DATA_TYPE );

ALTER TABLE table_name MODIFY COLUMN ( column_name NULL );

ALTER TABLE table_name MODIFY COLUMN ( column_name NOT NULL );

ALTER TABLE table_name DROP COLUMN column_name; ( NOT NULL, NULL, Unique,
function-base index 가 있는 컬럼도 삭제 가능)

ALTER TABLE table_name ADD CONSTRAINT constraint_name UNIQUE ( column_name );

ALTER TABLE table_name ADD CONSTRAINT constraint_name UNIQUE ( column_name )
LOCAL;

ALTER TABLE table_name DROP CONSTRAINT constraint_name; ( Unique, Local Unique )

CREATE UNIQUE INDEX index_name ON table_name ( column_name );

CREATE INDEX index_name ON table_name ( expression );

DROP INDEX index_name; ( unique, function-base 인덱스도 삭제 가능 )

#### REPLICATION_DDL_SYNC

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

이중화중 DDL 복제 여부를 나타낸다.

0 : 이중화중 DDL 복제를 허용하지 않음.  DDL 수행 시 이중화 지역 서버 ( Local Server ) 에서만 수행된다.   

1 : 이중화중 DDL 복제를 허용함.  DDL 수행 시 이중화 원격 서버 ( Remote Server )에 DDL 이 복제된다.   

Altibase 운영 중 ALTER SYSTEM 문 또는 ALTER SESSION 문을 이용하여 이 프로퍼티 값을 변경할 수 있다.

#### REPLICATION_DDL_SYNC_TIMEOUT ( 단위 : 초 )

##### 데이터 타입

Unsigned Integer

##### 기본값

7200

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

DDL 복제의 실행 시간이 이 프로퍼티에 설정한 시간(초)을 초과하면, 그 구문의 실행은 이중화 지역, 원격 서버 모두 취소된다.
DDL 복제를 수행하는 이중화 지역서버를 기준으로 Timeout 값이 측정된다.
Altibase 운영 중 ALTER SYSTEM 문 또는 ALTER SESSION 문을 이용하여 이 프로퍼티 값을 변경할 수 있다.

#### REPLICATION_EAGER_PARALLEL_FACTOR

##### 데이터 타입

Unsigned Integer

##### 기본값

'CPU개수/2'와 '512' 중 작은 값

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 512]

##### 설명

EAGER모드로 이중화 수행시 여러 개의 송신 쓰레드가 병렬로 작업을 하게 된다. 이
프로퍼티는 병렬 작업할 송신 쓰레드의 개수를 지정한다. 이중화 송신 쓰레드의
개수를 늘리면 이중화 성능이 향상될 수 있다.

그러나, 이 프로퍼티를 사용하여 송신 쓰레드 개수를 늘릴 경우, 송신 쓰레드가
보내는 트랜잭션의 순서가 보장되지 않는다는 점을 주의해야 한다. 이에 대한 자세한
내용은 *Replication Manual*을 참고한다.

이 프로퍼티를 설정하지 않으면 기본값은 CPU개수와 512중 더 작은 값이 된다.

#### REPLICATION_EAGER_RECEIVER_MAX_ERROR_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

5

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

Eager 모드로 이중화를 진행할 때, 이중화 수신자가 데이터 복제를 재시도하는 횟수를
설정할 수 있는 프로퍼티이다.

만약 이 값이 5로 설정되었을 때, Xlog 복제에 오류가 발생하면 이중화 수신자는 최대
5회까지 복제를 재시도한다. 재시도에서도 성공하지 못하면 Altibase 서버를 강제로
종료한다. 이 값을 0으로 설정하면, 이중화 수신자가 Xlog 복제에 실패할 경우 성공할
때까지 복제를 재시도하며, 서버를 강제 종료하지 않는다.

Eager 모드의 이중화는 이중화 수신자와 송신자간의 데이터 일치가 중요한 환경에서
주로 사용된다. 따라서 사전에 데이터 불일치를 예방하기 위해 데이터 복제를
중단하고 서버를 종료하는 것이다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_FAILBACK_INCREMENTAL_SYNC

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

이 프로퍼티는 증분 동기화(Incremental Sync) 수행 여부를 설정한다. 증분 동기화란
EAGER 모드의 이중화 작업 중 한 쪽 서버의 장애로 인해 데이터 불일치가 발생한
경우, 이 후 장애 서버가 다시 구동되는 중에 서버가 불일치 데이터를 동기화하는
것을 말한다.

- 0: 증분 동기화를 비활성화시킨다.
- 1: 증분 동기화를 활성화시킨다.

이중화에 참가하는 양쪽 Altibase 서버 모두 이 프로퍼티를 같은 값으로 설정해야
한다. 증분 동기화 및 Eager 이중화 장애 복구에 대한 자세한 내용은 *Replication
Manual*을 참고한다.

#### REPLICATION_GAP_UNIT (단위: 바이트)

##### 데이터 타입

Unsigned Long

##### 기본값

1048576 (1MB)

##### 속성

변경 가능, 단일 값

##### 값의 범위

[1, 2<sup>64</sup>-1]

##### 설명

이중화 갭의 크기를 조회하는 REP_GAP의 값을  표현하는 단위를 설정한다.

REP_GAP의 값은 REP_GAP_SIZE의 값을 이 프로퍼티로 나눈 결과값이며, 나머지는 올림한다.

기본값이면 V$REPGAP의 REP_GAP_SIZE는 바이트 단위로, REP_GAP은 메가바이트 단위로 조회된다.



#### REPLICATION_GAPLESS_ALLOW_TIME (단위: 마이크로 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

2000

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

갭 해소 옵션이 설정된 이중화 송신자는 이 프로퍼티에 설정한 시간만큼 이중화
격차(Replication Gap)를 허용한다. 이중화 송신자는 이 프로퍼티에 설정된 시간 안에
이중화 격차를 해소할 수 없다고 판단하면 서비스 트랜잭션의 커밋을 지연시키는
기능이 동작한다.

예를 들어 이 프로퍼티가 5이고, 송신자가 초당 처리하는 로그가 1,000건이라면
이중화 격차를 허용할 수 있는 로그의 개수는 5,000건이다. 만약 현재의 이중화
격차가 10,000건이라면, 허용하는 로그의 개수보다 5,000건을 초과하였으므로, 이중화
격차가 허용하는 로그 개수에 만족하기 위해서 트랜잭션이 5초간 지연되어야 한다는
것을 의미한다.

이 값이 0이면 이중화 격차를 허용하지 않는다는 의미이므로, 트랜잭션이 커밋되기
전에 이중화 격차를 해소시키고 커밋을 수행한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_GAPLESS_MAX_WAIT_TIME (단위: 마이크로 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

10*,*000*,*000

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

이중화 갭 해소(Gapless) 옵션이 설정된 이중화 송신자가 이중화 격차를 해소하기
위하여 트랜잭션 커밋을 지연시킬 수 있는 최대 시간을 의미한다.

이 값이 0이면 이중화 격차를 해소할 때까지 트랜잭션의 커밋을 지연시킨다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_GROUPING_TRANSACTION_MAX_COUNT (단위 : 개)

##### 데이터 타입

Unsigned Integer

##### 기본값

5

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 1000]

##### 설명

Ahead Analyzer 쓰레드가 복수의 트랜잭션을 한 번에 최대 몇 개까지 그룹화하여
수신자에 전송할 것인지 정하는 프로퍼티이다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_GROUPING_AHEAD_READ_NEXT_LOG_FILE (단위 : 개)

##### 데이터 타입

Unsigned Integer

##### 기본값

2

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 2<sup>32</sup>-1]

##### 설명

선행 분석(Ahead Analyzer) 쓰레드가 분석을 시작할 때, 송신자(Sender)가 현재 읽는
로그 파일 번호보다 얼마나 큰 번호의 로그 파일을 읽을 것인지 설정한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_HBT_CONNECT_WAIT_TIME(단위 : 마이크로초)

##### 데이터 타입

Unsigned Integer

##### 기본값

100000

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

REPLICATION_HBT_DETECT_HIGHWATER_MARK 프로퍼티의 횟수만큼 HeartBeat
쓰레드<sup>11</sup>가 상대 호스트를 검사할 때마다, 호스트에 접속을 시도한 후 응답을
대기하는 시간이다.

[<sup>11</sup>] REPLICATION_HBT_DETECT_TIME 프로퍼티 각주 참조

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_HBT_DETECT_HIGHWATER_MARK

##### 데이터 타입

Unsigned Integer

##### 기본값

5

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

연결(Connection) 응답을 하지 않는 경우 몇 회 이후에 장애로 판단할 것인지
결정한다. 따라서, 임의의 호스트의 장애를 판단하는 최대 시간은
REPLICATION_HBT_DETECT_TIME \* REPLICATION_HBT_DETECT_HIGHWATER_MARK 이다.

즉, HeartBeat 쓰레드는 기본값인 30초 (5회 시도\* 6초) 동안 연결이 되지 않을 경우
장애로 판단한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_HBT_DETECT_TIME(단위 : 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

6

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 2592000]

##### 설명

HeartBeat 쓰레드<sup>12</sup>의 검사 주기를 설정한다. 기본값인 6초 마다 HeartBeat
쓰레드는 해당 호스트에 대한 장애를 검사한다.

[<sup>12</sup>] HeartBeat 쓰레드: Altibase의 리플리케이션은 송신 쓰레드와 수신 쓰레드

간에 데이터 통신 수행 시 물리적인 장애가 발생했을 때, 신속하게 장애를 검출하기
위하여 HeartBeat 쓰레드를 만들어서 상대 호스트의 상태를 주기적으로 검사하는
기법을 도입했다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_IB_LATENCY

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

rsocket의 RDMA_LATENCY 옵션 값이다.

이 값이1이면 CPU 자원을 소모하더라도, 적은 대기 시간을 사용한다.

#### REPLICATION_IB_PORT_NO

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 65535]

##### 설명

이중화로 연결할 때 인피니밴드(InfiniBand)를 이용하여 접속할 경우 지역 서버의
이중화 포트 번호를 나타낸다.

인피니밴드를 이용하기 위해 IB_ENABLE 프로퍼티의 값이 1이어야 한다. 이 값이 0인
경우에는 인피니밴드로 이중화를 연결할 수 없다.

#### REPLICATION_INSERT_REPLACE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

이 프로퍼티는 이중화 중 INSERT 충돌이 발생했을 때 삽입된 내용을 유지할 지를
결정한다. 이 값이 0이면, INSERT는 커밋되지 않고 데이터 충돌은 에러 처리 된다.
반면에 이 값이 1이면 데이터 충돌은 무시되고 INSERT는 커밋된다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_KEEP_ALIVE_CNT 

##### 데이터 타입

Unsigned Integer

##### 기본값

600

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

송신 쓰레드가 패킷을 전송하지 않고 (REPLICATION_SENDER_SLEEP_TIME \*
REPLICATION_KEEP_ALIVE_CNT) 시간 동안 Sleep하면, KEEP_ALIVE신호를 전송한다.

#### REPLICATION_LOCK_TIMEOUT (단위: 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

5

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 3600]

##### 설명

이중화 데드락이 발생하는 경우 수신 쓰레드 쪽에서는 무한정 잠금을 기다리게 되어
서비스가 중단될 수 있다. 이러한 경우를 방지하기 위해 수신 쓰레드는 해당 작업의
수행에 대해 잠금을 요구할 때, 최대 이 프로퍼티에 설정된 시간만큼만 잠금을
획득하기 위해 기다린다.

명시된 시간 내에 잠금을 획득하지 못하는 경우 해당 작업은 철회된다.

#### REPLICATION_LOG_BUFFER_SIZE (단위 : MB)

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2<sup>12</sup>-1]

##### 설명

이중화 전용 로그 버퍼를 사용함으로써 이중화 성능을 개선하는 프로퍼티이다. 이중화
전용 로그 버퍼에는 이중화에 필요한 로그만 필터링하여 저장하기 때문에 더 많은
로그가 버퍼에 존재한다.

송신 쓰레드는 로그를 읽기 위해서 로그 버퍼 또는 디스크에서 로그를 읽는다. 그러나
디스크에서 로그를 읽는 경우 송신 쓰레드의 처리 속도가 현저히 떨어질 수 있다.
더욱이 이중화를 실행하면 필요하지 않은 로그까지 읽어야 하는 부담이 발생한다.
이중화 전용 로그 버퍼는 이러한 부담을 완화시켜준다.

다수의 이중화 송신 쓰레드가 수행중일 때는 이중화 성능과 서비스 성능이 저하될 수
있다. 이중화 로그 버퍼가 하나이므로 다수의 송신 쓰레드가 접근한다면 동기화
오버헤드가 발생할 확률이 높아지기 때문이다.

이중화 로그 버퍼에서 읽은 로그는 REPLICATION_SYNC_LOG 값을 1로 하여도 디스크에
기록되지 않은 상태에서 수신 쓰레드로 전송될 수 있다.

REPLICATION_LOG_BUFFER_SIZE를 너무 작게 설정하면, 사용하지 않는 것(0)보다 더
좋지 못한 성능을 낼 수 있다.

#### REPLICATION_MAX_COUNT (단위 : 개)

##### 데이터 타입

Unsigned Integer

##### 기본값

32

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 10240]

##### 설명

Altibase에 생성할 수 있는 이중화 객체의 최대 개수를 지정한다.

기본값은 32이며, 한 서버에서 최대 32개의 원격 서버와 이중화로 연결할 수 있음을
의미한다.

#### REPLICATION_MAX_LISTEN

##### 데이터 타입

Unsigned Integer

##### 기본값

32

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 512]

##### 설명

이중화 송신 쓰레드와 수신 쓰레드를 관리하는 Altibase 서버간의 통신 시 TCP/IP
소켓을 사용하는 경우 대기 큐(listen queue)의 크기를 지정하는 값이다. .

#### REPLICATION_MAX_LOGFILE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 65535]

##### 설명

이중화를 위하여 재시작 리두 시점(Restart Redo Point)을 기준으로 삭제하지 않을
최대 로그파일의 개수이다.

이중화 시작 후, 지역 서버와 원격 서버간의 네트워크 속도 등의 문제로 지역 서버의
변경내용이 아직 원격 서버에 반영되지 않았을 경우, 체크포인트가 발생해도 서버는
로그 파일을 삭제할 수 없다. 이러한 문제가 발생하면, 지역서버의 로그파일 개수가
계속 증가하게 되고 결국 디스크가 가득 차버릴 수 있다(Disk Full).

따라서 체크포인트가 발생하였을 때, 재시작 리두 시점 (Restart Redo Point) 이전
로그 파일들의 개수가 이 프로퍼티로 정해 놓은 값보다 클 경우 이중화는 잠시
중단되며, Altibase는 중단된 시점의 일시 (날짜, 시각)와 “재시작 SN”을
SYS_REPLICATION\_ 메타 테이블의 GIVE_UP_TIME과 GIVE_UP_XSN 컬럼에 각각 저장한다.
그리고 재시작 리두 시점 이전 로그파일들을 삭제한다. 현재 로그파일의 마지막(가장
큰) SN값이 새로운 이중화 “재시작 SN” 이 되며, 이 값도 SYS_REPLICATION\_ 메타
테이블의 XSN 컬럼에 저장된다. 이중화는 이 새로운 “재시작SN”부터 다시 수행될
것이다. 이런 디폴트 작업 방식을 변경하고 싶다면,
REPLICATION_SENDER_START_AFTER_GIVING_UP 프로퍼티 값을 변경하면 된다. 또,
SYS_REPLICATION\_ 메타 테이블에서 특정 replication과 관련된 모든 정보들을
초기화하고 싶다면, “ALTER REPLICATION replication_name RESET” 을 실행해라.

0으로 설정한 경우에는 이 기능을 적용하지 않는다. 참고로 체크포인트를 수행할 때
로그파일을 지우기 때문에, CHECKPOINT_INTERVAL_IN_SEC와 CHECKPOINT_IN_LOG의 값을
함께 고려해야 한다.

#### REPLICATION_POOL_ELEMENT_COUNT(단위 : 개)

##### 데이터 타입

Unsigned Integer

##### 기본값

10

##### 속성

변경 가능, 단일 값

##### 값의 범위

[1, 1024]

##### 설명

송신 쓰레드가 로그를 분석하여 칼럼 값을 복사할 때 사용하는 메모리의 개수이다. 이
때 메모리는 메모리 풀에서 미리 할당하며, 메모리 크기는
REPLICATION_POOL_ELEMENT_SIZE에서 지정한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_POOL_ELEMENT_SIZE(단위 : Byte)

##### 데이터 타입

Unsigned Integer

##### 기본값

256

##### 속성

변경 가능, 단일 값

##### 값의 범위

[128, 65536]

##### 설명

송신 쓰레드가 로그를 분석하여 각각의 칼럼 값을 복사할 때 사용하는 메모리의
크기이다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_PORT_NO

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 65535]

##### 설명

이중화 연결을 할 때 지역 서버의 이중화 포트 번호이다. 이중화를 사용하지 않으려면
이 프로퍼티를 0으로 설정한다.

#### REPLICATION_PREFETCH_LOGFILE_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

3

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1024]

##### 설명

각각의 로그 파일 그룹에 대해서 미리 읽을 로그 파일의 수를 나타낸다. 로그 파일을
미리 읽어 둠으로써 송신 쓰레드가 파일에서 로그 레코드를 읽는 시간을 줄인다.

#### REPLICATION_RECEIVE_TIMEOUT(단위 : 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

7200

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

송신 쓰레드와 수신 쓰레드에서 공통적으로 사용하는 프로퍼티로 송신/수신
쓰레드로부터 어떤 메시지를 기다리는 최대 시간을 지정하는 프로퍼티이다.

송신 쓰레드에서는 상대편 수신 쓰레드로부터 응답을 기다리는 최대 시간이며 명시된
시간이 경과하게 되면 REPLICATION_SENDER_SLEEP_TIMEOUT에서 지정된 시간만큼
sleep한 후 다시 상대편 수신 쓰레드와의 접속을 시도한다. 이 경우 기존 사용하던
소켓은 닫고 새로운 소켓을 생성하여 재연결을 시도한다.

수신 쓰레드에서는 상대편 송신 쓰레드로부터 어떤 메시지를 기다리는 최대 시간이다.
명시된 시간이 경과하게 되면 수신 쓰레드는 자동 종료되며 이후 상대편 송신
쓰레드가 어떤 메시지를 다시 보내게 되는 경우 다시 생성된다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_RECEIVER_APPLIER_ASSIGN_MODE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

이중화 수신자가 적용자(Applier)에게 XLog를 할당할 때 어떤 모드로 적용자에게
분배할 것인지를 선택하는 프로퍼티이다.

0: XLog Count Mode

1: Transaction Count Mode

이 값이 0이면 수신자는 XLog 개수가 가장 적게 할당된 적용자에게 XLog를 할당한다.
1인 경우에는 할당된 트랜잭션이 가장 적은 적용자에게 XLog를 할당한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_RECEIVER_APPLIER_QUEUE_SIZE

##### 데이터 타입

Unsigned Integer

##### 기본값

20

##### 속성

변경 가능, 단일 값

##### 값의 범위

[2, 2<sup>32</sup>-1]

##### 설명

수신자가 적용자 쓰레드들의 대기 큐에 전달할 수 있는 최대 XLog의 개수이다.

이 값이 클수록 적용자(Applier)에 전달하는 XLog의 개수가 많아질 수 있으나, 대기
큐에 XLog 들이 쌓이므로 메모리를 보다 많이 사용하게 된다. 이 값은 적용자 숫자의
2배 가량으로 설정하는 것을 권고한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_RECOVERY_MAX_LOGFILE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>–1]

##### 설명

이중화를 이용한 데이터 복구를 위하여 재시작 리두 시점(Restart Redo Point)을
기준으로 삭제하지 않을 최대 로그 파일의 개수를 의미한다.

이중화를 이용한 데이터 복구를 하기 위하여 원격 서버에서 디스크에 반영(flush)되지
않은 로그에 해당하는 지역 서버의 로그를 삭제하지 않고 유지한다. 이 때
체크포인트가 발생해도 로그 파일을 삭제할 수 없어 지역 서버의 로그파일 개수가
계속 증가하게 되면 결국 디스크 풀이 발생할 수 있다.

따라서 체크포인트가 발생하였을 때 복구 옵션을 위한 로그 파일 개수의 최대 값을
넘는 경우, 이중화를 이용한 복구를 포기하고, 로그 파일들을 삭제한다. 그리고
이중화를 다시 시작한다.

0으로 설정한 경우, 이 기능을 적용하지 않는다.

체크포인트를 수행할 때 로그 파일을 지우기 때문에, CHECKPOINT_INTERVAL_IN_SEC와
CHECKPOINT_IN_LOG의 값을 함께 고려해야 한다.

#### REPLICATION_RECOVERY_MAX_TIME (단위 : 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

2<sup>32</sup>–1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>–1]

##### 설명

이중화 모듈이 복구를 진행하는 중에 최대 시간이 지나면, 복구를 중단하고 지금까지
복구된 상태로 서비스를 진행할 수 있도록 한다.

이 값을 0으로 설정하는 경우, 이중화를 이용한 복구 과정을 진행하지 않는다.

Altibase는 이중화를 이용한 데이터 복구가 완료하기 전에 서비스 단계로 진행할 수
없어, 서비스 지연을 가져올 수 있다.

#### REPLICATION_SENDER_AUTO_START

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

Altibase가 서버 종료시 stop 시키지 않은 이중화 객체가 있었다면, 서버 재구동 시
이러한 이중화 객체들이 자동으로 시작되는 것이 기본 동작이다. 이 값을 0으로
설정하면, 서버 구동 시 이중화 객체가 자동으로 시작되는 것을 막을 수 있다.

#### REPLICATION_SENDER_COMPRESS_XLOG

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

이 프로퍼티는 이중화를 위해 데이터가 네트워크 상에서 전송될 때, 전송하는 패킷의
압축 여부를 지정한다.

0: 전송할 데이터를 압축하지 않음

1: 전송할 데이터를 압축함

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_SENDER_ENCRYPT_XLOG

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

이 프로퍼티는 이중화를 수행할 때 송신 쓰레드의 로그를 암호화하여 전송할 것인지
여부를 지정할 수 있다.

0: 전송 로그를 비암호화

1: 전송 로그를 암호화

#### REPLICATION_SENDER_SEND_TIMEOUT (단위: 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

7200

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

송신 쓰레드가 원격 서버로 패킷을 전송할 때 대기하는 최대 시간을 지정하는
프로퍼티이다.

이 값은 REPLICATION_RECEIVE_TIMEOUT(기본값:7200초) 프로퍼티의 값과 동일한 값을
설정할 것을 권고한다. 이 값을 0으로 설정하면 송신 쓰레드가 블로킹 소켓(blocking
socket)을 사용한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_SENDER_SLEEP_TIME (단위: 마이크로 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

10000

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

이 프로퍼티는 송신 쓰레드가 더 이상 읽을 로그가 없을 때, Sleep하는 시간을
지정한다. 특정 플랫폼에서는 짧은 시간의 Sleep이 무시되므로, 적당한 값을 지정해야
한다. REPLICATION_KEEP_ALIVE_CNT와 함께 KEEP_ALIVE를 전송하는 데 사용된다.

#### REPLICATION_SENDER_SLEEP_TIMEOUT(단위: 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

60

##### 속성

변경가능, 단일 값

##### 값의 범위

[0, 2592000]

##### 설명

이중화 송신 쓰레드가 오류 상황에서 sleep을 해야 할 때 얼마나 할 것인지를
결정한다.

Altibase 운영 중에 ALTER SYSTEM 구문을 이용하여 이 프로퍼티의 값을 변경할 수
있다.

#### REPLICATION_SENDER_START_AFTER_GIVING_UP

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

이 프로퍼티는 재시작 리두 시점 (Restart Redo Point) 이전 로그 파일들의 개수가
REPLICATION_MAX_LOGFILE 프로퍼티로 설정된 값을 초과하여 이중화가 잠시 중단된
이후, 다시 시작하는 방식을 결정한다.

0으로 설정된 경우에는, 이중화 "재시작 SN" (즉 SYS_REPLICATIONS\_ 메타 테이블의
XSN 컬럼의 값)이 -1로 초기화되며, 이중화는 중지된다. 그리고, SYS_REPLICATIONS\_
메타 테이블의 IS_STARTED 컬럼의 값이 0으로 바뀐다.

1로 설정된 경우, 이중화 "재시작 SN" 값은 현재 로그 파일의 마지막 (가장 큰)
SN으로 변경되고, 이중화는 이 "재시작 SN" 부터 다시 수행된다.

#### REPLICATION_SERVER_FAILBACK_MAX_TIME

##### 데이터 타입

Unsigned Integer

##### 기본값

2<sup>32</sup>-1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

EAGER 모드 이중화에서, 비정상 종료된 서버가 재구동 될 때, 다른 쪽(즉, 원격)
서버의 데이터와 동기화된 후에야 서비스가 재개된다. 이 때, 다른 서버의 로그를
비정상 종료했던 서버에 반영하는 과정이 이 프로퍼티에 설정된 시간(초)보다 오래
걸린다면, 비정상 종료했던 서버는 동기화가 완료되는 것을 포기하게 된다.

#### REPLICATION_SQL_APPLY_ENABLE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

Lazy 모드로 이중화 수행 과정에서 Active 서버와 Standby 서버의 이중화 테이블 메타 정보가 다른 경우, 아래의 조건에 따라 XLog가 SQL 문으로 변환되어 반영된다.

- 0: XLog를 이용하여 이중화가 동작한다. 이때, 메타 정보가 다르면 Handshaking 에러가 발생한다.
- 1: 아래의 조건에서 이중화를 수행하면, XLog가 SQL 문으로 변환이 되어 이중화 테이블에 반영한다.
- 컬럼 정보  
  데이타 타입이 다를 경우  
  size, precision, scale 이 다를 경우
- 제약 조건  
  check 제약 조건이 다를 경우  
  Not Null 제약 조건이 다를 경우  
  다른 메타 정보 중 LOB 컬럼이 포함된 경우
- 인덱스  
  유니크 인덱스나 Function-based 인덱스가 이중화 대상 컬럼과 이중화 대상이
  아닌 컬럼으로 구성되어 있을 경우  
  유니크 인덱스의 구성 정보가 다를 경우  
  Function-based 인덱스의 구성 정보가 다를 경우

#### REPLICATION_SYNC_APPLY_METHOD

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

이중화 수행 중에 지역 서버와 원격 서버간의 불일치한 데이터를 어떤 방식으로
동기화 할 것인지 설정한다.

- 0: Normal Insert
- 1: Direct-Path Insert

이중화 SYNC 과정에서 Direct-Path Insert 방식을 이용할 경우, 
데이터 동기화 이후 Index를 재생성한다. 따라서, 이중화 SYNC 과정이 도중에 실패할 경우, 
Index inconsistent 가 발생할 수 있다.

Direct-Path Insert에 대한 자세한 설명은 *Administrator’s Manual*을 참조하기
바란다. Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수
있다.

#### REPLICATION_SYNC_LOCK_TIMEOUT (단위: 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

30

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

이중화 송신 쓰레드가 동기화 대상 테이블의 잠금(lock)을 획득하기 위해 대기하는
시간을 정하는 프로퍼티이다. ALTER REPLICATION .. SYNC 구문으로 이중화 동기화를
실행하면, 이중화 송신 쓰레드는 데이터 동기화를 수행한 후 계속해서 이중화를
시작할 로그 위치를 결정한다. 이 때 동기화 대상 테이블이 다른 트랜잭션에 의해
데이터가 변경되지 않도록 송신 쓰레드는 공유 잠금(S Lock)을 획득한다. 그러나 이미
다른 트랜잭션에 의해 잠금이 되었다면, 이 프로퍼티에 지정한 시간만큼 대기한다.

예를 들어 이 프로퍼티의 값이 30인 경우, 30초 동안 잠금을 획득할 수 없으면 동기화
시도는 오류 처리된다. 만약 이 값을 0으로 설정하면 이중화 대상 테이블에 대한
잠금은 획득하지 않지만, 데이터의 충돌이 발생할 수 있다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_SYNC_LOG

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

이중화 수행 시 송신 쓰레드가 보내는 로그는 디스크에 내려갔는지의 여부에 관계없이
메모리 상의 로그를 보내기 때문에, 시스템 또는 매체 장애(media failure)와 같은
상황에서 데이터 불일치 등의 문제가 발생할 소지가 있다.

이러한 문제를 해결하기 위해서 이 값을 1로 설정하면, 송신 쓰레드는 디스크에
내려간 로그만 보내게 된다.

#### REPLICATION_SYNC_TUPLE_COUNT

##### 데이터 타입

Unsigned long

##### 기본값

50000

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 2<sup>64</sup>-1]

##### 설명

병렬 동기화시 송신 쓰레드가 한번에 읽어서 처리할 수 있는 레코드의 최대 개수를
지정한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_TIMESTAMP_RESOLUTION

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

Active-Active 이중화 환경에서 데이터 충돌이 발생하였을 때 이 프로퍼티의 값에
따라 해결방식이 다르게 적용된다.

이 프로퍼티의 값이 1로 설정되고, 이중화 대상 테이블에 TIMESTAMP 컬럼이 있는
경우에 Timestamp-based Scheme 방식으로 충돌이 해결된다.

그러나 이중화 대상 테이블에 TIMESTAMP 컬럼이 있어도, 이 프로퍼티의 값이 0이면
이미 설정되어 있는 Conflict Resolution Scheme 방식이 사용된다.

데이터 충돌에 대한 자세한 설명은 *Replication Manual*을 참고한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_TRANSACTION_POOL_SIZE

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

이 프로퍼티는 트랜잭션 풀에 미리 생성해 두는 트랜잭션의 개수를 지정한다. 이중화
수신자는 데이터를 복제할 때 트랜잭션을 사용한다. 그리고 성능 향상을 위해 이중화
수신자 별로 트랜잭션 풀(pool)을 만들고, 이 곳에 트랜잭션들을 미리 생성해 두고
사용할 수 있다.

만약 풀에 존재하는 트랜잭션의 수가 부족하다면, 이중화 수신자는 새로운 트랜잭션을
생성하여 이를 사용할 것이다. 그리고 사용이 끝난 트랜잭션은 풀에 반환되는데, 이
때 존재하는 트랜잭션의 개수가 이 프로퍼티에 지정된 값보다 크면, 풀에 반환되지
않고 바로 해제된다.

이 값을 너무 크게 지정하면, 일반 트랜잭션의 개수에 제한을 줄 수 있으므로 적절한
값으로 설정해야 한다. 이 프로퍼티에 허용된 최대값은 232-1이지만, 실제 최대값은
TRANSACTION_TABLE_SIZE 프로퍼티에 지정한 값과 같다. 만약 사용자가 이 값을
TRANSACTION_TABLE_SIZE의 값보다 크게 지정하면, 내부적으로 이 프로퍼티의 값이
TRANSACTION_TABLE_SIZE의 값으로 설정된다.

Altibase 구동 중에 이 프로퍼티의 값을 변경할 수 있다. 하지만 이중화 수신 쓰레드
생성시 트랜잭션 풀이 초기화되므로, 이중화를 재시작해야 변경된 프로퍼티의 값이
적용된다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REPLICATION_UPDATE_REPLACE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

이중화 작업중 변경작업 충돌(update conflict) 시 변경된 내용의 반영을 결정한다.
값이 0 이면 충돌이 있을 경우 반영하지 않고 오류 처리하며, 1 일 경우 충돌을
무시하고 반영한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

### 네트워크 관련 프로퍼티

#### IB_CONCHKSPIN

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2147483]

##### 설명

rsocket의 RDMA_CONCHKSPIN 옵션 값을 설정한다. 인피니밴드의 연결 확인을 어느
주기로 할 것인지 설정하는 값이다. 이 값이 0이면 rsocket의 기본값을 사용한다.

이 프로퍼티는 Altibase rdma-core ( <https://github.com/ALTIBASE/rdma-core> )를
사용할 때에만 사용할 수 있다.

#### IB_ENABLE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

Altibase에서 인피니밴드(InfiniBand, IB)의 사용 여부를 설정한다. 이 기능은
Linux에서만 사용할 수 있다.

0 : IB사용하지 않음 (기본값)

1: IB사용

#### IB_LATENCY 

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

rsocket의 RDMA_LATENCY 옵션 값을 설정한다.

이 프로퍼티의 값이 1이면 CPU 자원을 더 소모하더라도, 대기 시간을 줄이기 위하여
튜닝 코드를 사용한다.

이 프로퍼티는 Altibase rdma-core ( <https://github.com/ALTIBASE/rdma-core> )를
사용할 때에만 사용할 수 있다.

#### IB_LISTENER_DISABLE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

Altibase를 시작할 때 인피니밴드 리스너(InfiniBand Listener)의 시작 여부를 설정할
수 있다.

0: 인피니밴드 리스너 시작(기본값)

1: 인피니밴드 리스너 시작하지 않음

#### IB_MAX_LISTEN 

##### 데이터 타입

Unsigned Integer

##### 기본값

128

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1024]

##### 설명

인피니밴드(InfiniBand, IB)로 접속하여 동시에 Altibase를 사용할 수 있는
클라이언트의 최대 숫자이다.

#### IB_PORT_NO

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1024, 65535]

##### 설명

인피니밴드(InfiniBand, IB)를 이용하여 통신하기 위해 사용하는 포트 번호이다.

#### SNMP_ALARM_QUERY_TIMEOUT

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

세션에서 쿼리 타임아웃이 발생했을 때 트랩을 보낼지 여부를 결정한다. 디폴트 값은
1이며 트랩을 보낸다. 자세한 내용은 SNMP Agent Guide의
altiPropertyAlarmQueryTimeout를 참고하기 바란다.

#### SNMP_ALARM_FETCH_TIMEOUT

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

FETCH TIMEOUT이 발생했을 때 트랩을 보낼지 여부를 결정한다. 기본값은 1이며 트랩을
보낸다. 자세한 내용은 SNMP Agent Guide의 altiPropertyAlarmFetchTimeout를
참고하기 바란다.

#### SNMP_ALARM_UTRANS_TIMEOUT

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

UTRANS TIMEOUT이 발생했을 때 트랩을 보낼지 여부를 결정한다.

0: 트랩을 발생시키지 않는다.

1: 트랩을 발생시킨다.

자세한 내용은 SNMP Agent Guide의 altiPropertyAlarmUtransTimeout를 참고하기
바란다.

#### SNMP_ALARM_SESSION_FAILURE_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

3

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

세션에서 연속으로 프로퍼티에 설정한 횟수만큼 오류가 발생했을 때 트랩을 보낸다.
기본값은 3이고, 0이면 트랩을 보내지 않는다. 자세한 내용은 SNMP Agent Guide의
altiPropertyAlarmSessionFailureCount를 참고하기 바란다.

#### SNMP_ENABLE 

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

SNMP 서비스를 사용하기 위해서는 1 (Enable)로 설정해야 한다. 기본값은 0
(Disable)이다.

0 : SNMP 사용

1: SNMP 사용하지 않음

#### SNMP_MSGLOG_FLAG 

##### 데이터 타입

Unsigned Integer

##### 기본값

3

##### 속성

변경 가능, 단일 값

##### 값의 범위

[3, 12]

##### 설명

로그 출력의 레벨(Level)을 설정한다. 레벨은 '1', '2', '4', '8' 4가지가 있으며
각각의 합으로 설정된다. 기본값은 3(1 + 2)이며, 레벨이 Level1, Level3가 되면
관련된 로그가 출력된다.

#### SNMP_PORT_NO 

##### 데이터 타입

Unsigned Integer

##### 기본값

20400

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1024, 65535]

##### 설명

Altibase와 altisnmpd(Altibase sub agent)간에 통신을 하기 위해 사용되는 UDP
포트이다.

#### SNMP_TRAP_PORT_NO 

##### 데이터 타입

Unsigned Integer

##### 기본값

20400

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1024, 65535]

##### 설명

Altibase와 altisnmpd(Altibase sub agent)간에 트랩을 보내기 위해 통신을 하는 UDP
포트이다.

#### SNMP_RECV_TIMEOUT (단위 : 밀리세크초)

##### 데이터 타입

Unsigned Integer

##### 기본값

1000

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 2<sup>32</sup>-1]

##### 설명

통신을 사용하기 위한 타임아웃 값이다.

Altibase와 altisnmpd(Altibase sub agent)간에 통신을 할 때 이 프로퍼티에 설정한
값만큼 대기한다.

#### SNMP_SEND_TIMEOUT (단위 : 밀리세크초)

##### 데이터 타입

Unsigned Integer

##### 기본값

100

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 2<sup>32</sup>-1]

##### 설명

통신을 사용하기 위한 타임아웃 값이다.

Altibase와 altisnmpd(Altibase sub agent)간에 통신을 할 때 이 프로퍼티에 설정한
값만큼 대기한다.

#### SSL_CA

##### 데이터 타입

String

##### 기본값

없음

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

CA 인증서의 소유권을 인정받기 위해서 CA 인증서를 저장하는 파일의 경로를 지정할
수 있다. CA 인증서 파일은 사용자 지정 경로나 X.509 형식의 디렉토리에 위치한다.
예를 들어 \$ALTIBASE_HOME/cert/ ca-cert.pem으로 할 수 있다.

#### SSL_CAPATH

##### 데이터 타입

String

##### 기본값

없음

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

CA 디렉토리 형식의 CAPATH를 지정할 수 있다. 예를 들어서, 지정할 경우
\$ALTIBASE_HOME/etc/ssl/certs로 할 수 있다.

#### SSL_CERT

##### 데이터 타입

String

##### 기본값

없음

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

Altibase 서버의 인증서 파일 경로를 지정한다. 예를 들어
\$ALTIBASE_HOME/cert/server-cert.pem으로 지정할 수 있다.

#### SSL_CIPHER_LIST 

##### 데이터 타입

String

##### 기본값

없음

##### 속성

읽기 전용, 단일 값

##### 값의 범위

255

##### 설명

이 프로퍼티는 Altibase가 클라이언트와 협의하여 사용할 수 있는 암호 알고리즘의
이름 후보들이다. 암호 알고리즘은 사용자의 보안 정책에 따라 하나 또는 그 이상의
암호를 사용할 수 있다. 두 개 이상의 암호를 사용할 경우 콜론(:)으로 구분한다.
사용자가 사용할 수 있는 암호 목록은
OpenSSL( [http://www.openssl.org](http://www.openssl.org/)/ )에서 확인하거나
아래처럼 명령어를 사용하여 확인할 수 있다.

```
$ openssl ciphers
```

#### SSL_CLIENT_AUTHENTICATION

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

서버와 클라이언트가 SSL로 통신을 할 때 클라이언트에게 인증서를 요청할 것인지를
설정할 수 있다. 기본값이 0일 때에는 클라이언트가 서버만 인증서를 통해 확인하다.
이 값을 1로 하면, 서버는 SSL 핸드쉐이크중에 클라이언트에게 인증서를 요청한다.

0: 서버만 인증(기본값)

1: 서버와 클라이언트 동시 인증

#### SSL_ENABLE 

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

Altibase가 SSL/TLS를 이용할지 여부를 설정할 수 있다. 기본값은 0 (Disable)이다.

0 : SSL/TLS 사용하지 않음

1: SSL/TLS 사용

#### SSL_KEY

##### 데이터 타입

String

##### 기본값

없음

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

Altibase 서버의 개인 키(private key)가 저장된 파일 경로를 지정한다.

예를 들어 \$ALTIBASE_HOME/cert/server-key.pem으로 지정할 수 있다.

#### SSL_MAX_LISTEN

##### 데이터 타입

Unsigned Integer

##### 기본값

128

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 16384]

##### 설명

SSL/TLS로 접속하여 동시에 Altibase를 사용할 수 있는 대기 큐(listen queue)의 최대
크기를 지정한다. 이 값이 클수록 Altibase에 더 많은 메모리가 필요하다.

#### SSL_PORT_NO 

##### 데이터 타입

Unsigned Integer

##### 기본값

20443

##### 속성

변경 가능, 단일 값

##### 값의 범위

[1024, 65535]

##### 설명

서버와 클라이언트가 SSL/TLS를 이용하여 통신하기 위해 사용되는 포트번호를
설정한다.

#### TCP_ENABLE

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

Altibase 서버가 통신 프로토콜로 TCP/IP를 선택하여 통신할 것인지를 설정할 수
있다.

0 : TCP/IP 사용하지 않음

1: TCP/IP 사용

### 메시지 로그 관련 프로퍼티

#### ALL_MSGLOG_FLUSH

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

이 값이 1인 경우 데이터베이스의 모든 메시지가 기록 즉시 디스크에 반영되고 0인
경우에는 일정 주기에 한 번씩 디스크에 반영된다. 과도한 로깅으로 인한 성능저하를
예방하기 위해서는 0으로 설정하는 것이 적절하고, 데이터베이스 문제 진단 시에는
1로 설정하고 작업한다.

#### COLLECT_DUMP_INFO

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

서버가 비정상 종료할 때 메시지 파일과 로그 파일 등의 정보를 수집할 것인지 여부를
지정한다.

0: 메시지 파일과 로그 파일의 정보를 수집하지 않음

1: 메시지 파일과 로그 파일의 정보를 수집함

#### DK_MSGLOG_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

10

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

데이터베이스 링크를 할 때 연결 프로세스에 지정할 수 있는 메시지 파일의 최대
개수를 설정한다.

#### DK_MSGLOG_FILE

##### 데이터 타입

String

##### 기본값

altibase_lk.log

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

데이터베이스 링크가 연결 프로세스 처리 과정에서 발생하는 메시지를 기록되는
파일이다.

#### DK_MSGLOG_FLAG

##### 데이터 타입

Unsigned Integer

##### 기본값

6

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

데이터베이스 링크의 연결 프로세스 모듈에서 발생하는 경고 메시지나 추적 메시지를
LK_MSGLOG_FILE에 기록할 것인지 여부를 나타내는 플래그 값이다.

0이면 기록하지 않고, 0보다 큰값이면 기록한다.

#### DK_MSGLOG_RESERVE_SIZE (단위 : 바이트)

##### 데이터 타입

Unsigned Integer

##### 기본값

10 \* 1024 \* 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

데이터베이스 링크의 메시지 파일을 저장하기 위해 디스크에 미리 확보해 둘 공간의
크기를 지정한다.

#### DK_MSGLOG_SIZE

##### 데이터 타입

Unsigned Integer

##### 기본값

10 \* 1024 \* 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

데이터베이스 링크에서 연결 프로세스의 메시지 파일 최대 크기를 지정한다.

#### DUMP_MSGLOG_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

10

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

서버 오류에 대한 디버깅 정보가 기록되는 메시지 파일의 최대 개수를 지정한다.

#### DUMP_MSGLOG_FILE

##### 데이터 타입

String

##### 기본값

altibase_dump.log

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

서버 오류에 대한 디버깅 정보가 기록되는 메시지 파일명을 지정한다.

#### DUMP_MSGLOG_SIZE (단위 : 바이트)

##### 데이터 타입

Unsigned Integer

##### 기본값

10 \* 1024 \* 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

디버깅 정보가 기록되는 메시지 파일의 최대 크기를 지정한다.

#### DUMP_MSGLOG_RESERVE_SIZE (단위 : 바이트)

##### 데이터 타입

Unsigned Integer

##### 기본값

10 \* 1024 \* 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

디버깅 정보가 기록되는 메시지 파일을 저장하기 위해 디스크에 미리 확보할 공간의
크기를 지정한다.

#### ERROR_MSGLOG_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

10

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

서버 오류 메시지 파일의 최대 개수를 지정한다.

#### ERROR_MSGLOG_FILE

##### 데이터 타입

String

##### 기본값

altibase_error.log

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

서버에서 발생하는 오류 메시지를 기록할 파일명을 지정한다. Altibase 서버 비정상
종료시 프로세스의 콜 스택도 이 파일에 기록된다.

#### ERROR_MSGLOG_SIZE (단위 : 바이트)

##### 데이터 타입

Unsigned Integer

##### 기본값

10 \* 1024 \* 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

서버 오류 메시지가 저장되는 파일의 최대 크기를 지정한다.

#### ERROR_MSGLOG_RESERVE_SIZE (단위 : 바이트)

##### 데이터 타입

Unsigned Integer

##### 기본값

10 \* 1024 \* 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

서버 오류 메시지가 저장되는 파일을 위해 디스크에 미리 확보해 둘 공간의 크기를
지정한다.

#### LB_MSGLOG_COUNT 

##### 데이터 타입

Unsigned Integer

##### 기본값

10

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

서비스 쓰레드 관련 메시지 파일의 최대 개수를 설정한다.

#### LB_MSGLOG_FILE 

##### 데이터 타입

String

##### 기본값

altibase_lb.log

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

서비스 쓰레드 관련 메시지를 기록하는 파일이다.

#### LB_MSGLOG_FLAG 

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

LB_MSGLOG_FILE에 기록될 서비스 쓰레드 관련 메시지 항목을 지정한다.

0: 기록하지 않음

1: 서비스 쓰레드의 생성 및 해제

2: Task 이동에 대한 로그

3: 서비스 쓰레드의 생성 및 해제, Task 이동에 대한 로그

#### LB_MSGLOG_SIZE

##### 데이터 타입

Unsigned Integer

기본값

10 \* 1024 \* 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

서비스 쓰레드 관련 메시지가 기록되는 파일의 최대 크기를 지정한다.

#### MM_MSGLOG_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

10

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

메인 모듈을 위한 메시지 파일의 최대 개수를 지정한다.

#### MM_MSGLOG_FILE

##### 데이터 타입

String

##### 기본값

altibase_mm.log

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

메일 모듈 처리 시에 발생하는 메시지가 기록되는 파일이다.

#### MM_MSGLOG_RESERVE_SIZE (단위 : 바이트)

##### 데이터 타입

Unsigned Integer

##### 기본값

10 \* 1024 \* 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

메인 모듈을 위한 메시지 파일을 저장하기 위해 디스크에 미리 확보해 둘 공간의
크기를 지정한다.

#### MM_MSGLOG_SIZE(단위 : 바이트)

##### 데이터 타입

Unsigned Integer

##### 기본값

10 \* 1024 \* 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

메인 모듈의 메시지 파일의 최대 크기를 지정한다.

#### MM_SESSION_LOGGING

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

데이터베이스 서버에 대한 모든 로그온, 로그오프 이벤트를 발생시키는 세션 정보를
MM_MSGLOG_FILE에 기록할 지 여부를 지정한다. 세션 정보는 세션 ID, 사용자 이름,
클라이언트 IP 주소, 클라이언트 프로그램의 PID, 그리고 클라이언트 프로그램에 대한
세부 정보를 포함한다.

#### NETWORK_ERROR_LOG 

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

서버 메시지 파일에 네트워크 관련 에러 메시지의 출력 여부를 지정한다.

네트워크 환경이 불안정하여 에러 메시지의 출력이 많을 때 0으로 설정하면, 네트워크
관련 에러 메시지의 출력을 막을수 있다.

#### QP_MSGLOG_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

10

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

질의 처리기 메시지 파일의 최대 개수를 지정한다.

#### QP_MSGLOG_FILE

##### 데이터 타입

String

##### 기본값

altibase_qp.log

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

질의 연산 (Query Processing) 처리 시에 발생하는 메시지가 기록되는 파일이다.

#### QP_MSGLOG_FLAG

##### 데이터 타입

Unsigned Integer

##### 기본값

2

##### 속성

변경가능, 단일 값

##### 값의 범위

[0, 2<sup>32</sup> –1]

##### 설명

쿼리 프로세싱 모듈에서 발생하는 경고 메시지나 트레이스 메시지를 QP_MSGLOG_FILE에
기록 할지 여부를 나타내는 플래그 값이다.

0이면 기록하지 않고, 0 보다 큰값이면 기록한다.

#### QP_MSGLOG_RESERVE_SIZE (단위 : 바이트)

##### 데이터 타입

Unsigned Integer

##### 기본값

10 \* 1024 \* 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

질의 처리기의 메시지 파일을 저장하기 위해 디스크에 미리 확보해 둘 공간의 크기를
지정한다.

#### QP_MSGLOG_SIZE(단위 : 바이트)

##### 데이터 타입

Unsigned Integer

##### 기본값

10 \* 1024 \* 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

질의 처리기 메시지 파일의 최대 크기를 지정한다.

#### QUERY_PROF_FLAG

##### 데이터 타입

Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 2<sup>6</sup>-1]

##### 설명

서버 내에서 수행되는 작업과 서버의 상태 정보를 파일로 기록하여 분석할 수 있도록
한다. 사용자는 값을 조합하여 원하는 정보를 기록하도록 설정할 수 있으며, 값에
따라서 기록되는 정보는 다음과 같다.

- 0 : 기록하지 않음
- 1 : SQL 문이 실행될 때마다 실행된 SQL문, 실행시간, 실행정보, 색인 및 디스크
  접근 정보 출력. 단, 실행시간이 제대로 출력되게 하려면 TIMED_STATISTICS
  프로퍼티를 1로 설정해야 한다.
- 2 : SQL 문이 실행될 때마다 BIND 파라미터 출력
- 4 : SQL 문이 실행될 때마다 실행계획 출력
- 8 : 3초마다 세션 정보 출력 (V\$SESSTAT 의 데이터)
- 16 : 3초마다 시스템 정보 출력 (V\$SYSSTAT 의 데이터)
- 32 : 3초마다 메모리 정보 출력 (V\$MEMSTAT 의 데이터)

예를 들어 프로퍼티를 1+4+32=37로 설정하면, SQL 문이 실행될 때마다 SQL 문의 실행
정보와 실행계획을 출력하고 3초마다 메모리 정보를 출력한다.

파일에 대한 분석은 altiProfile 유틸리티로 가능하며, 자세한 설명은 *Utilities
Manual의 유틸리티*를 참조한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### QUERY_PROF_LOG_DIR

##### 데이터 타입

String

##### 기본값

\$ALTIBASE_HOME/trc

##### 속성

변경 가능, 단일 값

##### 값의 범위

[1, 1024 ]

##### 설명

Altibase에서 수행된 작업과 서버의 상태 정보가 기록되는 파일이 위치할 디렉토리
경로를 지정한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### RP_CONFLICT_MSGLOG_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

10

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

이중화 충돌시 트레이스 로그가 기록되는 파일의 최대 개수를 지정한다.

#### RP_CONFLICT_MSGLOG_DIR

##### 데이터 타입

String

##### 기본값

\$ALTIBASE_HOME/trc

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

이중화 충돌이 발생할 때 트레이스 로그가 기록되는 파일이 위치할 디렉토리를
지정한다.

#### RP_CONFLICT_MSGLOG_ENABLE

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

이중화 충돌에 대한 트레이스 로그를 기록할 것인지 여부를 지정한다.

#### RP_CONFLICT_MSGLOG_FILE

##### 데이터 타입

String

##### 기본값

altibase_rp_conflict.log

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

이중화 충돌에 대한 트레이스 로그가 기록되는 파일이다.

#### RP_CONFLICT_MSGLOG_FLAG

##### 데이터 타입

Unsigned Integer

##### 기본값

6

##### 속성

변경가능, 단일 값

##### 값의 범위

[0, 2<sup>32</sup> –1]

##### 설명

이중화 충돌과 관련된 트레이스 로그의 로깅 레벨을 지정한다.

설정 가능한 값은 아래와 같다:

2: 충돌 메시지 기록

4: 충돌을 유발한 SQL문 기록

6: 충돌 메시지와 충돌을 유발한 SQL문을 모두 기록

#### RP_CONFLICT_MSGLOG_RESERVE_SIZE (단위 : 바이트)

##### 데이터 타입

Unsigned Integer

##### 기본값

10 \* 1024 \* 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

이중화 충돌에 대한 트레이스 로그 파일의 저장을 위해 디스크에 미리 확보해 둘
공간의 크기를 지정한다.

#### RP_CONFLICT_MSGLOG_SIZE(단위 : 바이트)

##### 데이터 타입

Unsigned Integer

##### 기본값

10 \* 1024 \* 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

이중화 충돌에 대한 트레이스 로그 파일의 최대 크기를 지정한다.

#### RP_MSGLOG_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

10

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

이중화 메시지 파일의 최대 개수를 지정한다.

#### RP_MSGLOG_FILE

##### 데이터 타입

String

##### 기본값

altibase_rp.log

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

복제 관리자 (Replication) 처리 과정에서 발생하는 메시지가 기록되는 파일이다.

#### RP_MSGLOG_FLAG

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경가능, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

복제 관리자(Replication Manager) 모듈에서 발생하는 경고 메시지나 트레이스
메시지를 RP_MSGLOG_FILE에 기록 할지 여부를 나타내는 플래그 값이다.

0이면 기록하지 않고, 0보다 큰 값이면 기록한다.

#### RP_MSGLOG_RESERVE_SIZE (단위 : 바이트)

##### 데이터 타입

Unsigned Integer

##### 기본값

10 \* 1024 \* 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

이중화 메시지 파일의 저장을 위해 디스크에 미리 확보해 둘 공간의 크기를 지정한다.

#### RP_MSGLOG_SIZE (단위 : 바이트)

##### 데이터 타입

Unsigned Integer

##### 기본값

10 \* 1024 \* 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

이중화 메시지 파일의 최대 크기를 지정한다.

#### SERVER_MSGLOG_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

10

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

서버 메시지 파일의 최대 개수를 지정한다.

#### SERVER_MSGLOG_DIR

##### 데이터 타입

String

##### 기본값

\$ALTIBASE_HOME/trc

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

서버 구동 및 종료 등에 대한 시스템 정보가 기록되어 있는 서버 모듈의 메시지
파일인 SERVER_MSGLOG_FILE과 서버 관리 프로그램에서 사용하는 내부 파일인
altibase.lock이 위치할 경로이다.

또한, SM_MSGLOG_FILE, QP_MSGLOG_FILE, RP_MSGLOG_FILE 등과 같은 서버 모듈의
메시지 파일을 위한 기본 경로로 사용된다.

#### SERVER_MSGLOG_FILE

##### 데이터 타입

String

##### 기본값

altibase_boot.log

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

서버 모듈에 대한 메시지를 남기는 파일명을 지정한다.

Altibase의 구동 및 경고, 비정상 종료 시에 출력되는 메시지를 기록하는 파일이다.

#### SERVER_MSGLOG_FLAG

##### 데이터 타입

Unsigned Integer

##### 기본값

7

##### 속성

변경가능, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

서버 모듈에서 발생하는 경고 메시지나 트레이스 메시지를 SERVER_MSGLOG_FILE에 기록
할지 여부를 나타내는 플래그 값이다.

0이면 기록하지 않고, 0 보다 큰 값이면 기록한다.

#### SERVER_MSGLOG_RESERVE_SIZE (단위 : 바이트)

##### 데이터 타입

Unsigned Integer

##### 기본값

10 \* 1024 \* 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

서버 메시지 파일의 저장을 위해 디스크에 미리 확보해 둘 공간의 크기를 지정한다.

#### SERVER_MSGLOG_SIZE(단위 : 바이트)

##### 데이터 타입

Unsigned Integer

##### 기본값

10 \* 1024 \* 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

서버 메시지 파일의 최대 크기를 지정한다.

#### SM_MSGLOG_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

10

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

저장 관리자 메시지 파일의 최대 개수를 지정한다.

#### SM_MSGLOG_FILE

##### 데이터 타입

String

##### 기본값

altibase_sm.log

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

저장 관리자(Storage Manager) 처리 과정에서 발생하는 메시지가 기록되는 파일이다.

#### SM_MSGLOG_FLAG

##### 데이터 타입

Unsigned Integer

##### 기본값

2147483647

##### 속성

변경가능, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

저장 관리자(Storage Manager)모듈에서 발생하는 경고 메시지나 트레이스 메시지를
SM_MSGLOG_FILE에 기록 할지 여부를 나타내는 플래그 값이다. 0이면 기록하지 않고,
0보다 큰값이면 기록한다.

#### SM_MSGLOG_RESERVE_SIZE (단위 : 바이트)

##### 데이터 타입

Unsigned Integer

##### 기본값

10 \* 1024 \* 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

저장 관리자의 메시지 파일을 저장하기 위해 디스크에 미리 확보해 둘 공간의 크기를
지정한다.

#### SM_MSGLOG_SIZE(단위 : 바이트)

##### 데이터 타입

Unsigned Integer

##### 기본값

10 \* 1024 \* 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

저장 관리자 메시지 파일의 최대 크기를 지정한다.

#### TRC_MSGLOG_RESERVE_SIZE (단위 : 바이트)

##### 데이터 타입

Unsigned Integer

##### 기본값

10 \* 1024 \* 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

서버를 시작하면서 발생하는 경고 메시지 등이 기록될 수 있는 트레이스 로그 파일의
공간을 디스크에 미리 확보하기 위하여 크기를 지정한다.

#### TRCLOG_DETAIL_PREDICATE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

Isql에서 Explain plan 기능 사용 시 where 절의 predicate 분류 상태를 나타낸다. 이
trace log를 사용하기 위해 1을 설정한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### XA_MSGLOG_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

10

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>–1]

##### 설명

서버용 XA 메시지 파일의 최대 개수를 지정한다.

#### XA_MSGLOG_FILE

##### 데이터 타입

String

##### 기본값

altibase_xa.log

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

서버용 XA 메시지 로그가 기록되는 파일이다.

#### XA_MSGLOG_FLAG

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경가능, 단일 값

##### 값의 범위

[0, 3]

##### 설명

서버용 XA 메시지 로그의 기록 단계를 설정하는 속성으로 설정값은 다음과 같다.

0: XA 관련 최소 필수 메시지만 기록

1: XA 연산 호출을 기록

2: XID 할당, 해제 등을 기록함

3: XA 관련 모든 메시지 로그를 기록함

#### XA_MSGLOG_RESERVE_SIZE (단위 : 바이트)

##### 데이터 타입

Unsigned Integer

##### 기본값

10 \* 1024 \* 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

서버용 XA 메시지 파일의 저장을 위해 디스크에 미리 확보해 둘 공간의 크기를
지정한다.

#### XA_MSGLOG_SIZE 

##### 데이터 타입

Unsigned Integer

##### 기본값

10 \* 1024 \* 1024

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>–1]

##### 설명

서버용 XA 메시지 파일의 최대 크기를 지정한다.

### 데이터베이스 링크 관련 프로퍼티 

#### DBLINK_ALTILINKER_CONNECT_TIMEOUT(단위: 초)

##### 데이터 타입

Unsigned Integer

##### 기본값

100

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

Altibase 서버에서 AltiLinker로 접속할 때, 접속 대기 최대 시간을 지정한다.

#### DBLINK_DATA_BUFFER_ALLOC_RATIO

##### 데이터 타입

Unsigned Integer

##### 기본값

50

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

데이터베이스 링크로 원격 서버에서 수행한 질의의 결과 집합을 로컬 서버가 가져와서
저장하는 공간을 데이터베이스 링크 전용 데이터 버퍼라고 한다. 이 프로퍼티는
데이터베이스 링크 전용 데이터 버퍼의 남은 공간에서 원격 질의별로 할당 받을
record buffer의 비율을 지정한다.

#### DBLINK_DATA_BUFFER_BLOCK_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

128

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 2<sup>12</sup>-1]

##### 설명

데이터베이스 링크를 위해 원격 서버에서 수행한 질의의 결과 집합을 로컬 서버에서
받아와서 저장하는 공간을 데이터 버퍼라고 한다. 이 프로퍼티는 데이터 버퍼를
구성하는 메모리 블럭(record buffer block)의 초기 할당 개수를 지정한다. 데이터
버퍼의 크기는 DBLINK_DATA_BUFFER_BLOCK_COUNT \* DBLINK_DATA_BUFFER_BLOCK_SIZE가
될 것이다..

#### DBLINK_DATA_BUFFER_BLOCK_SIZE (단위: 바이트)

##### 데이터 타입

Unsigned Integer

##### 기본값

2 MBytes

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 29]

##### 설명

데이터베이스 링크를 위해 원격 서버에서 수행한 질의의 결과 집합을 로컬 서버에서
받아와서 저장하는 공간을 데이터 버퍼라고 한다. 이 프로퍼티는 데이터 버퍼를
구성하는 메모리 블럭(record buffer block)의 크기를 지정한다.

#### DBLINK_ENABLE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

데이터베이스 링크 사용 여부를 결정한다. 데이터베이스 링크를 사용하고자 할 때는
이 값을 1로 설정한다. 값이 0이면 데이터베이스 링크를 사용할 수 없다.

#### DBLINK_GLOBAL_TRANSACTION_LEVEL

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 2]

##### 설명

글로벌 트랜잭션 수행 레벨을 지정한다. 이 프로퍼티를 0으로 설정할 경우,
DBLINK_REMOTE_STATEMENT_AUTOCOMMIT 프로퍼티를 원격 데이터베이스의 AUTOCOMMIT
모드와 동일하게 지정해야 한다.

0: remote statement execution level. 이 레벨에서는 하나의 글로벌 트랜잭션에
참여하는 서버들(로컬 및 원격 서버)의 각 트랜잭션이 별개의 트랜잭션으로
인식되므로, 글로벌 트랜잭션을 커밋하기 위해서는 각 서버의 트랜잭션을 별도로
commit해 주어야 한다. 즉, 이 레벨에서는 글로벌 트랜잭션이라 하더라도 로컬
서버에서 수행하는 commit이 원격 서버에 영향을 미치지 않는다.

1: simple transaction commit level. 이 레벨에서는 하나의 글로벌 트랜잭션에
참여하는 서버들(로컬 및 원격 서버)의 모든 트랜잭션이 하나의 트랜잭션으로
인식된다. 즉, 로컬 서버에서 글로벌 트랜잭션을 커밋하면 해당 트랜잭션에 참여하는
모든 트랜잭션들이 커밋된다.

2:Two-Phase Commit (2PC) Level. 이 레벨에서는 하나의 글로벌 트랜잭션에 참여하는
데이터베이스 시스템의 트랜잭션 정합성을 보장하기 위해 2PC 프로토콜을 지원한다.
글로벌 트랜잭션이 시작되면 트랜잭션이 종료할 때까지 이 프로퍼티 값을 변경 할 수
없다.

#### DBLINK_RECOVERY_MAX_LOGFILE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[1, 2<sup>32</sup>-1]

##### 설명

이 프로퍼티는 트랜잭션 수행 중에 이기종 데이터베이스 시스템에 장애가 발생할
경우, 알티베이스가 분산 트랜잭션 복구를 위해 유지하는 로그 파일의 최대 개수이다.
이 프로퍼티 값이 0이면 분산 트랜잭션 복구를 위한 로그를 삭제하지 않아 정합성이
보장된다. 그러나 프로퍼티 값을 1보다 큰 값으로 설정하면, 로그 파일의 개수가
초과할 경우에 분산 트랜잭션이 완료되지 않더라도 체크포인트에 의해 로그가
삭제되므로 정합성을 보장할 수 없다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### DBLINK_REMOTE_STATEMENT_AUTOCOMMIT

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

원격 데이터베이스의 AUTOCOMMIT 모드를 지정한다.

DBLINKE_GLOBAL_TRANSACTION_LEVEL을 0으로 설정한 경우에만 이 프로퍼티가 적용된다.

0: autocommit-off

1: autocommit-on

#### DBLINK_REMOTE_TABLE_BUFFER_SIZE (단위 : MB)

##### 데이터 타입

Unsigned Integer

##### 기본값

50

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

REMOTE_TABLE 키워드를 사용하여 원격 서버에서 질의를 수행하면, 질의 결과를 임시로
저장할 수 있는 메모리 버퍼이다.

저장된 질의 결과는 질의 처리기에 전달된 후 삭제된다. 그러나 결과 집합중의 하나의
레코드가 이 프로퍼티에 지정한 크기보다 크면 저장할 수 없으므로, 프로퍼티의 값을
조정해야 한다.

### 감사 관련 프로퍼티 

#### AUDIT_FILE_SIZE (단위: 바이트)

##### 데이터 타입

Unsigned Int

##### 기본값

100M

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 2<sup>32</sup>-1]

##### 설명

감사된 구문의 정보가 기록되는 바이너리 파일의 크기를 바이트 단위로 지정한다. 이
프로퍼티는 AUDIT_OUTPUT_METHOD 프로퍼티의 값이 0일 때 적용된다.

Altibase 운영 중에는 아래와 같이 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을
변경할 수 있다.

```
ALTER SYSTEM SET AUDIT_FILE_SIZE=10000;
```

단, 서버가 auditing을 수행 중이라면 다음 생성되는 파일부터 변경된 크기가
적용된다. 만약 프로퍼티의 변경을 바로 적용하려면 ALTER SYSTEM STOP AUDIT과 ALTER
SYSTEM START AUDIT 구문으로 auditing을 재시작하라.

#### AUDIT_LOG_DIR

##### 데이터 타입

String

##### 기본값

\$ALTIBASE_HOME/trc

##### 속성

변경 가능, 다중값

##### 값의 범위

없음

##### 설명

감사된 구문 정보가 기록되는 바이너리 파일이 생성될 디렉토리를 지정한다. 이
프로퍼티는 AUDIT_OUTPUT_METHOD 프로퍼티의 값이 0일 때 적용된다.

Altibase 운영 중에는 아래와 같이 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을
변경할 수 있다.

```
ALTER SYSTEM SET AUDIT_LOG_DIR='/tmp';
```

단, 서버가 auditing을 수행 중이라면 다음 생성되는 파일부터 변경된 디렉토리가
적용된다. 만약 프로퍼티의 변경을 바로 적용하려면 ALTER SYSTEM STOP AUDIT과 ALTER
SYSTEM START AUDIT 구문으로 auditing을 재시작하라.

#### AUDIT_OUTPUT_METHOD

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 불가, 단일값

##### 값의 범위

[0, 9]

##### 설명

감사된 구문 정보가 기록되는 파일의 형태를 지정한다. Altibase는 감사 정보를
바이너리 또는 시스로그(syslog)로 저장할 수 있다. 단 syslog는 리눅스
운영체제에서만 지원한다.

기본값을 설정한 경우 감사된 정보가 바이너리 형태로 AUDIT_LOG_DIR 프로퍼티에서
지정한 디렉토리에 저장된다. 1\~9의 값을 설정한 경우, syslog를 사용해서
syslog.conf(또는 rsyslog.conf)에 로그가 쌓이게 된다. syslog의 순서는 syslog.conf
파일의 LOG_INFO를 사용한다.

0: 바이너리 파일로 AUDIT_LOG_DIR 프로퍼티에서 지정한 디렉토리에 저장

1: user 퍼실리티를 /var/log/messages에 저장. 파일명은 시스템 설정시 변경 가능.

2: 사용자 정의에 따라 local0 facility에 저장

3: 사용자 정의에 따라 local1 facility에 저장

4: 사용자 정의에 따라 local2 facility에 저장

5: 사용자 정의에 따라 local3 facility에 저장

6: 사용자 정의에 따라 local4 facility에 저장

7: 사용자 정의에 따라 local5 facility에 저장

8: 사용자 정의에 따라 local6 facility에 저장

9: 사용자 정의에 따라 local7 facility에 저장

#### AUDIT_TAG_NAME_IN_SYSLOG

##### 데이터 타입

String

##### 기본값

AUDIT

##### 속성

변경 불가, 단일값

##### 값의 범위

없음

##### 설명

시스로그(syslog)를 사용해서 감사된 구문의 정보를 기록할 때 구분자로 "AUDIT"
태그가 사용된다.

### 에이전트 관련 프로퍼티 

#### EXTPROC_AGENT_CONNECT_TIMEOUT

##### 데이터 타입

Unsigned Integer

##### 기본값

60 초

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[5, 2<sup>32</sup>-1]

##### 설명

사용자가 외부 프로시저를 호출할 때, Altibase가 외부 프로시저용 에이전트에 연결을
시도하는 최대 시간을 초 단위로 설정한다. 이 프로퍼티에 설정한 시간 동안 연결을
할 수 없다면 외부 프로시저 호출은 연결을 실패했다는 오류 메시지와 함께 종료된다.
연결이 맺어진 후의 외부 프로시저 호출은 이 프로퍼티 값의 영향을 받지 않는다.

#### EXTPROC_AGENT_CALL_RETRY_COUNT

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

변경 가능, 단일 값

##### 값의 범위

[1, 10]

##### 설명

사용자가 외부 프로시저를 호출할 때, Altibase가 외부 프로시저용 에이전트 연결을
재시도하는 횟수를 설정한다.

Altibase는 에이전트 프로세스에 외부 에이전트가 있는지 확인한 후 사용할 수 있다.
그러나 사용하려는 외부 에이전트가 EXTPROC_AGENT_CONNECT_TIMEOUT 프로퍼티 값에
의해 타임아웃 되어 종료될 수 있다. 그러면 이 프로퍼티에서 설정한 횟수만큼 외부
에이전트에 연결을 재시도한다.

Altibase 운영 중에 ALTER SYSTEM 구문으로 이 프로퍼티 값을 변경할 수 있다.

#### EXTPROC_AGENT_IDLE_TIMEOUT

##### 데이터 타입

Unsigned Integer

##### 기본값

300 초

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[5, 2<sup>32</sup>-1]

##### 설명

외부 프로시저용 에이전트 프로세스가 idle 상태로 대기하는 최대 시간을 초 단위로
설정한다. 사용자가 외부 프로시저를 호출했을 때 에이전트 프로세스가 idle 상태로
대기 중이라면, 에이전트 프로세스로의 연결 과정 없이 프로시저를 수행할 수 있어
응답 시간이 적게 걸릴 것이다. 그러나, 사용자의 외부 프로시저 호출이 없는데도
에이전트 프로세스가 종료하지 않고 대기하는 것은 자원 낭비가 될 수 있으므로 외부
프로시저의 호출 빈도가 높은 경우에만 대기 시간을 늘릴 것을 권장한다.

#### EXTPROC_AGENT_SOCKET_FILEPATH

##### 데이터 타입

String

##### 기본값

\$ALTIBASE_HOME/trc

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

Altibase 서버가 외부 프로시저 에이전트(external procedure agent)와 통신하기 위해
생성하는 소켓 파일의 경로이다.

외부 프로시저를 사용하면, 세션이 외부 프로시저 에이전트를 생성하면서
socket_sessionID로 소켓 파일을 생성한다. 임의로 이 파일을 삭제하지 않도록
주의해야 한다.

생성된 소켓 파일은 세션이 정상적으로 종료할 때 자동으로 삭제된다.

### 사용자 계정 보안 관련 프로퍼티 

#### CASE_SENSITIVE_PASSWORD

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

데이터베이스에서 사용자 암호의 대소문자를 구분할지 여부를 결정한다. 기본값은
대소문자를 구분하지 않는 0이며, 데이터베이스 내에서 사용자 암호가 대문자로
다뤄진다.

- 0: 대소문자 구분을 하지 않는다.
- 1: 대소문자 구분을 한다. 단, 사용자 생성 구문에서 암호를 큰따옴표(")로 묶은
  경우에만 대소문자가 구분된다. 큰따옴표를 쓰지않은 암호는 대문자로 인식된다.

알티베이스 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### FAILED_LOGIN_ATTEMPTS

##### 데이터 타입

Unsigned Int

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1000]

##### 설명

로그인을 시도할 때 이 프로퍼티에 설정된 횟수 이상 실패하면, 해당 계정은 로그인이
불가능하다.

#### PASSWORD_LOCK_TIME

##### 데이터 타입

Unsigned Int

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 3650]

##### 설명

계정이 한 번 잠긴 후 다시 풀리기 위해 경과되어야 하는 날짜(단위: 일)를 지정한다.

#### PASSWORD_LIFE_TIME

##### 데이터 타입

Unsigned Int

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 3650]

##### 설명

계정의 패스워드가 유효한 기간(단위: 일)을 지정한다.

#### PASSWORD_GRACE_TIME

##### 데이터 타입

Unsigned Int

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 3650]

##### 설명

계정의 패스워드가 만료되는 시점 이후의 유예 기간(단위: 일)을 지정한다.

#### PASSWORD_REUSE_TIME

##### 데이터 타입

Unsigned Int

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 3650]

##### 설명

동일한 패스워드를 재사용하기 위해 경과해야 하는 기간(단위:일)을 지정한다. 즉,
여기에 설정한 기간이 지난 후에 동일한 패스워드를 재사용할 수 있다.

#### PASSWORD_REUSE_MAX

##### 데이터 타입

Unsigned Int

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1000]

##### 설명

동일한 패스워드를 재사용하기 위한 패스워드 변경 횟수를 지정한다. 즉, 여기에
설정한 횟수만큼 패스워드를 변경한 후에 동일한 패스워드를 재사용할 수 있다.

#### PASSWORD_VERIFY_FUNCTION

##### 데이터 타입

String

##### 기본값

""

##### 속성

읽기 전용, 단일 값

##### 값의 범위

최대 길이 40바이트

##### 설명

패스워드를 검증할 사용자 정의 콜백 함수(CALLBACK function)를 지정한다.

### Altibase Sharding 관련 프로퍼티

#### SHARD_META_ENABLE 

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

Altibase Sharding의 메타 노드로 설정한다.

0: Disabled

1: Enabled

### 기타 프로퍼티 

#### ACCESS_LIST

##### 형식

ACCESS_LIST = operation, address, mask

##### 값의 범위

- operation ::= [PERMIT\|DENY]  
  검사 규칙과 일치하는 IP 패킷의 접근을 허용할 것인지 제한할 것인지 기술한다.
- address  
  검사할 패킷의 IP 주소를 기술한다.
- mask  
  명시한 주소값이 IPv4 주소 형식이면, 이것은 서브넷 마스크로, 패킷의 IP 주소
  중, 특정 부분만 검사하도록 설정한다.  
  명시한 주소값이 IPv6 주소 형식이면, 이것은 등록된 IPv6 주소들과 비교할
  prefix비트의 길이를 나타낸다. 즉, 등록된 주소의 마스크 비트 길이에 해당하는
  값이 접근하는 패킷의 IP 주소의 마스크 비트 길이에 해당하는 값과 일치한다면
  접근이 허용된다.

##### 검사 규칙

```
IF 
BITXOR(BITAND(IP_패킷,mask), BITAND(address,mask)) = 0
THEN  일치
ELSE  불일치
```

##### 설명

Altibase에 접근하고자 하는 IP 패킷을 주소에 따라 접근을 제한하거나 허용할 수
있다. IP 패킷의 주소를 검사 규칙에 따라 검사하여, 일치하면 operation에
기술된 대로 허용 또는 제한하며 불일치하면 무시하고 다음 리스트를 검사한다.

IP 패킷의 주소를 여러 개가 지정될 경우 기술된 순서대로 검사한다. 일치하는
조건이 없을 경우, 접근이 허용된다.

만약 ACCESS_LIST_FILE 프로퍼티에 값을 기술하면 ACCESS_LIST 프로퍼티에 정의된
목록 대신 외부 파일의 목록을 사용할 수 있다. 외부 파일은 최대 1024개의 항목까지
사용할 수 있으며, 'ACCESS_LIST='는 생략하고 내용만 작성해야 한다.

##### 예제

IP 주소가 192.168.1.55인 패킷만 접근을 제한하고 나머지는 허용한다.

```
ACCESS_LIST = deny, 192.168.1.55, 255.255.255.255
```

192.168.3.\*과 219.211.253.\* 주소들은 접근을 허용하고 나머지는 모두 제한한다.

```
ACCESS_LIST = permit, 192.168.3.0, 255.255.255.0
ACCESS_LIST = permit, 219.211.253.0, 255.255.255.0
ACCESS_LIST = deny ,0.0.0.0, 0.0.0.0
```

로컬 호스트를 제외한 모든 IPv4, IPv6 주소들의 접근을 제한한다.

```
ACCESS_LIST = deny, 0.0.0.0, 0.0.0.0
ACCESS_LIST = deny, ::1, 1
ACCESS_LIST = deny, fe80::, 1
```

외부 파일에 검사할 IP 주소를 기술한다. 192.168.3.\*과 fe80으로 시작하는 IPv6
주소를 제외한 모든 IP 주소의 접근을 제한한다.

```
permit, 192.168.3.0, 255.255.255.0
permit, fe80::, 16
deny, 0.0.0.0, 0.0.0.0
deny, ::1, 1
deny, fe80::, 1
```

**ACCESS_LIST_FILE**

##### 데이터 타입

String

##### 기본값

없음

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

ACCESS_LIST가 외부 파일 경로를 참조할 때 설정한다. 파일명과 경로를 정확히
설정하지 않은 경우 서버를 구동할 수 없다. 외부 파일 경로는 절대경로를 지정해야
한다. 파일에 ACCESS_LIST를 기술할 때의 형식은 ACCESS_LIST 프로퍼티의 설명을
참조한다.

이 프로퍼티를 사용하지 않을 때에는 ACCESS_LIST 프로퍼티에 기술된 목록을
사용한다.

#### ADMIN_MODE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

이 프로퍼티는 관리자 모드로 접근하는 것만 허용한다.

0: OFF

1: ON

이 값을 1로 설정하면 관리자 모드로 활성화되어 SYS 또는 SYSTEM\_ 사용자가 SYSDBA
옵션으로 서버와 연결을 맺어 작업을 할 수 있고 그 외 일반 사용자들은 연결 자체가
실패한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### ARITHMETIC_OPERATION_MODE

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

Altibase 서버의 산술 연산 모드를 설정하는 프로퍼티이다.

0: 서버가 정밀도 우선 산술 연산 모드로 동작한다. 이 모드에서는 서버가 FLOAT 또는
NUMERIC 타입을 주로 사용하여 산술 연산의 오차를 줄인다. 단, "성능 우선 산술 연산
모드"에 비해 처리 속도가 떨어질 수 있다.

1: 서버가 성능 우선 산술 연산 모드로 동작한다. 이 모드에서는 서버가 산술 연산 시
DOUBLE 타입을 주로 사용하여 성능을 높이지만, 상대적으로 오차가 발생할 수 있다.

#### CHECK_MUTEX_DURATION_TIME_ENABLE

##### 데이터 타입

Unsigned Integer

##### 기본 값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

MUTEX_DURATION_TIME을 확인할 것인지 여부를 설정한다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

0: check disable

1: check enable

#### COERCE_HOST_VAR_IN_SELECT_LIST_TO_VARCHAR

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 32000]

##### 설명

이 프로퍼티는 select target list 절에 CAST 연산자 없이 호스트 변수를 사용할 수
있도록 해 준다.

이 프로퍼티를 1 이상의 값으로 설정하면, CAST 연산자 없이 사용된 호스트 변수에
대해서 Altibase 서버가 임의로 VARCHAR 타입으로 처리한다. 또한 설정된 값이
VARCHAR 타입의 크기(precision)가 된다.

이 프로퍼티의 값을 0으로 설정하면, CAST 연산자 없이 호스트 변수를 사용할 경우
에러가 발생한다.

#### DEFAULT_DATE_FORMAT

##### 데이터 타입

String

##### 기본값

DD-MON-RRRR

##### 속성

읽기 전용, 단일 값

##### 값의 범위

없음

##### 설명

테이블의 칼럼 도메인 중 DATE 타입 데이터의 기본 형식을 지정한다. 이 타입은 날짜,
시간을 저장할 수 있는 형식으로 제공되어야 한다. 형식은 “DD MON RRRR” 과 같이
따옴표 내에 공백도 사용할 수 있다.

```
DEFAULT_DATE_FORMAT = YYYY/MM/DD
iSQL> select sysdate from dual;
SYSDATE
--------------
2008/06/16
1 row selected.
```

#### EXEC_DDL_DISABLE

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

일반적으로 초기 데이터베이스를 구축한 이후에는 DML구문을 훨씬 더 빈번하게
수행하며 DDL 구문의 수행은 기존 데이터베이스 스키마를 변경시키는 작업이므로
상당한 주의를 요한다.

따라서 Altibase 운영 중 DDL구문을 수행하지 못하도록 운영자가 설정할 수 있으며 이
프로퍼티의 값을 1로 설정하면 Altibase 운영 중 DDL구문을 수행할 수 없으며 0인
경우 DDL구문을 수행할 수 있다.

Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### GROUP_CONCAT_PRECISION

##### 데이터 타입

Unsigned Integer

##### 기본값

4000

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 32000]

##### 설명

이 프로퍼티는 GROUP_CONCAT 함수가 반환하는 VARCHAR 타입의 크기를 지정한다.

Altibase 운영 중에 ALTER SYSTEM 구문으로 이 프로퍼티의 값을 변경할 수 있다.

#### JOB_SCHEDULER_ENABLE 

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

작업 스케줄러의 동작을 제어한다. 이 프로퍼티의 값을 1로 설정하여도
JOB_THREAD_COUNT 프로퍼티가 0이면 작업 스케줄러가 동작하지 않는다.

0: JOB스케줄러가 JOB 실행을 종료한다.

1: JOB스케줄러가 JOB 실행을 시작한다.

Altibase 운영 중에 ALTER SYSTEM 구문으로 이 프로퍼티의 값을 변경할 수 있다.

#### JOB_THREAD_COUNT 

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 128]

##### 설명

이 프로퍼티는 JOB을 실행하기 위한 쓰레드를 서버 구동 시 몇 개 생성할 것인지를
지정한다. 이 값이 0일 경우 작업 스케줄러(JOB Scheduler)를 위한 쓰레드가 생성되지
않는다.

#### JOB_THREAD_QUEUE_SIZE 

##### 데이터 타입

Unsigned Integer

##### 기본값

64

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[64, 1024]

##### 설명

이 프로퍼티는 JOB을 실행하기 위한 큐(Queue)를 서버 구동 시에 얼마나 생성할
것인지를 지정한다. 이 값이 크면, 동일 시간에 더 많은 JOB을 실행할 수 있다.

#### MSG_QUEUE_PERMISSION

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0, 1]

##### 설명

메시지 큐의 접근 권한(permission type)을 설정한다. Altibase 운영 중 ALTER SYSTEM
문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

0: (rw-rw-rw 0666) - 모든 사용자는 읽기와 쓰기만 할 수 있으며 실행하기는 할 수
없다.

1: (rw-r-r 0644) - 소유자는 읽기와 쓰기만 할 수 있으며, 그 외의 사용자는 읽기만
할 수 있다.

#### PSM_CHAR_DEFAULT_PRECISION

##### 데이터 타입

Unsigned Integer

##### 기본값

32000

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 65534]

##### 설명

아래와 같은 경우에 CHAR 타입의 크기를 명시하지 않으면 Altibase는
PSM_CHAR_DEFAULT_PRECISION 프로퍼티에 설정된 값을 CHAR크기로 결정한다.

- 저장 프로시저 생성시 데이터 타입이 CHAR인 파라미터의 크기를 명시하지 않을 때
- 저장 함수 생성시 데이터 타입이 CHAR인 파라미터 또는 반환 값의 크기를
  명시하지 않을 때

#### PSM_IGNORE_NO_DATA_FOUND_ERROR

##### 데이터 타입

Unsigned Integer

##### 기본값

0

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

Altibase의 PSM에서 제공하는 시스템-정의 예외 중 NO_DATA_FOUND가 있다. 이 예외는
PSM(저장 프로시저 및 함수, 트리거) 내에 포함된 "SELECT \~ INTO" 구문이 실행될 때
결과 집합이 없으면 발생한다. PSM_IGNORE_NO_DATA_FOUND_ERROR 프로퍼티를 사용하면
저장 함수에 대해서는 NO_DATA_FOUND 예외가 발생하지 않도록 할 수 있다.

- 0: 결과 집합이 없는 경우에 NO_DATA_FOUND 예외가 발생한다.
- 1: 결과 집합이 없는 경우에 NO_DATA_FOUND 예외가 발생하지 않는다.

Altibase 운영 중에 ALTER SYSTEM 구문으로 이 프로퍼티의 값을 변경할 수 있다.

#### PSM_NCHAR_UTF16_DEFAULT_PRECISION

##### 데이터 타입

Unsigned Integer

##### 기본값

16000

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 32766]

##### 설명

Altibase 캐릭터 셋(character set)이 UTF16이고 아래와 같은 경우에 NCHAR타입의
크기를 명시하지 않으면 Altibase는 PSM_NCHAR_UTF16_DEFAULT_PRECISION 프로퍼티에
설정된 값을 NCHAR크기로 결정한다.

- 저장 프로시저 생성시 데이터 타입이 NCHAR인 파라미터의 크기를 명시하지 않을
  때
- 저장 함수 생성시 데이터 타입이 NCHAR인 파라미터 또는 반환 값의 크기를
  명시하지 않을 때

#### PSM_NCHAR_UTF8_DEFAULT_PRECISION

##### 데이터 타입

Unsigned Integer

##### 기본값

10666

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 21843]

##### 설명

Altibase 캐릭터 셋(character set)이 UTF8이고 아래와 같은 경우에 NCHAR타입의
크기를 명시하지 않으면 Altibase는 PSM_NCHAR_UTF8_DEFAULT_PRECISION 프로퍼티에
설정된 값을 NCHAR크기로 결정한다.

- 저장 프로시저 생성시 데이터 타입이 NCHAR인 파라미터의 크기를 명시하지 않을
  때
- 저장 함수 생성시 데이터 타입이 NCHAR인 파라미터 또는 반환 값의 크기를
  명시하지 않을 때

#### PSM_NVARCHAR_UTF16_DEFAULT_PRECISION

##### 데이터 타입

Unsigned Integer

##### 기본값

16000

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 32766]

##### 설명

Altibase 캐릭터 셋(character set)이 UTF16이고 아래와 같은 경우에 NVARCHAR타입의
크기를 명시하지 않으면 Altibase는 PSM_NVARCHAR_UTF16_DEFAULT_PRECISION
프로퍼티에 설정된 값을 NVARCHAR크기로 결정한다.

- 저장 프로시저 생성시 데이터 타입이 NVARCHAR인 파라미터의 크기를 명시하지
  않을 때
- 저장 함수 생성시 데이터 타입이 NVARCHAR인 파라미터 또는 반환 값의 크기를
  명시하지 않을 때

#### PSM_NVARCHAR_UTF8_DEFAULT_PRECISION

##### 데이터 타입

Unsigned Integer

##### 기본값

10666

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 21843]

##### 설명

Altibase 캐릭터 셋(character set)이 UTF8이고 아래와 같은 경우에 NVARCHAR타입의
크기를 명시하지 않으면 Altibase는 PSM_NVARCHAR_UTF8_DEFAULT_PRECISION 프로퍼티에
설정된 값을 NVARCHAR크기로 결정한다.

- 저장 프로시저 생성시 데이터 타입이 NVARCHAR인 파라미터의 크기를 명시하지
  않을 때
- 저장 함수 생성시 데이터 타입이 NVARCHAR인 파라미터 또는 반환 값의 크기를
  명시하지 않을 때

#### PSM_PARAM_AND_RETURN_WITHOUT_PRECISION_ENABLE

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[0,1]

##### 설명

저장 프로시저를 생성할 때 파라미터의 크기를 정의하지 않았거나 저장 함수를 생성할
때 파라미터 및 반환 값의 데이터 크기를 정의하지 않았다면, 이 프로퍼티 값에 따라
사용할 수 있는 데이터 크기가 달라진다.

파라미터 또는 반환 값의 타입이 CHAR, NCHAR, NVARCHAR, VARCHAR 이고 이 프로퍼티의
값이 1이면, 데이터 타입의 크기는 아래의 프로퍼티에 설정한 값으로 결정된다.
그러나 이 값이 0으로 설정하면 데이터 타입의 크기는 1이다.

- PSM_CHAR_DEFAULT_PRECISION
- PSM_NCHAR_UTF8_DEFAULT_PRECISION
- PSM_NCHAR_UTF16_DEFAULT_PRECISION
- PSM_NVARCHAR_UTF8_DEFAULT_PRECISION
- PSM_NVARCHAR_UTF16_DEFAULT_PRECISION
- PSM_PARAM_AND_RETURN_WITHOUT_PRECISION_ENABLE
- PSM_VARCHAR_DEFAULT_PRECISION

#### PSM_VARCHAR_DEFAULT_PRECISION

##### 데이터 타입

Unsigned Integer

##### 기본값

32000

##### 속성

읽기 전용, 단일 값

##### 값의 범위

[1, 65534]

##### 설명

아래와 같은 경우에 VARCHAR 타입의 크기를 명시하지 않으면 Altibase는
PSM_VARCHAR_DEFAULT_PRECISION 프로퍼티에 설정된 값을 VARCHAR의 크기로 결정한다.

- 저장 프로시저 생성시 데이터 타입이 VARCHAR인 파라미터의 크기를 명시하지 않을
  때
- 저장 함수 생성시 데이터 타입이 VARCHAR인 파라미터 또는 반환 값의 크기를
  명시하지 않을 때

#### QUERY_STACK_SIZE (단위 : 개)

##### 데이터 타입

Unsigned Integer

##### 기본값

1024

##### 속성

변경 가능, 단일 값

##### 값의 범위

[8, 65536]

##### 설명

질의 수행 시 연산 및 비교 등의 연산자를 처리하기 위해 시스템 내부적으로 사용하는
스택의 크기를 설정하는 시스템 프로퍼티이다.

복잡한 연산식 또는 저장프로시저와 같이 많은 구문이 사용될 경우 stack overflow
오류가 날 수 있고 이 때 프로퍼티 값을 큰 값으로 변경해야 한다. 응용 프로그램
환경에 따라 적절한 값을 설정해야 하며 필요 이상 큰 값으로 설정할 경우 불필요한
메모리 공간 낭비가 될 수 있으므로 유의해야 한다.

이 프로퍼티는 altibase.properties 파일내에 명시할 수 있으며 ALTER SYSTEM 또는
ALTER SESSION 명령문으로 변경할 수 있다.

ALTER SESSION문으로 변경하는 경우 다음과 같이 값을 변경할 수 있다.

ALTER SESSION SET STACK SIZE = *n*;

#### RECURSION_LEVEL_MAXIMUM

##### 데이터 타입

Unsigned Integer

##### 기본값

1000

##### 속성

변경 가능, 단일 값

##### 값의 범위

[5, 2<sup>32</sup>-1]

##### 설명

이 프로퍼티에 설정한 횟수(level) 만큼 재귀 질의를 반복하여 수행한다.

Altibase 운영 중 ALTER SESSION 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

#### REMOTE_SYSDBA_ENABLE

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

SYS 사용자가 원격에서 SYSDBA 모드로 접속할 수 있는지 여부를 설정한다. ALTER
SYSTEM 명령문으로 값을 변경할 수 있다.

0: 원격에서 SYSDBA 모드로 접속 불가

1: 원격에서 SYSDBA 모드로 접속 가능 (기본값)

#### SELECT_HEADER_DISPLAY

##### 데이터 타입

Unsigned Integer

##### 기본값

1

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 1]

##### 설명

SELECT 쿼리의 결과 출력 시 iSQL 상에 칼럼 이름만 출력할 것인지, 테이블 이름과
함께 칼럼 이름을 출력할 것인지를 설정하는 시스템 프로퍼티이다.

이 프로퍼티는 altibase.properties 파일에 명시할 수 있으며 ALTER SYSTEM 또는
ALTER SESSION 명령문으로 변경할 수 있다. 값이 0인 경우 iSQL 상에서 결과 출력 시
테이블 이름과 칼럼 이름이 함께 출력된다.

#### SYS_CONNECT_BY_PATH_PRECISION

##### 데이터 타입

Unsigned Integer

##### 기본값

4000

##### 속성

변경 가능, 단일 값

##### 값의 범위

[0, 32000]

##### 설명

이 프로퍼티는 SYS_CONNECT_BY_PATH_PRECISION 함수가 반환하는 VARCHAR 타입의
크기를 지정한다.

Altibase 운영 중에 ALTER SYSTEM 구문으로 이 프로퍼티의 값을 변경할 수 있다.

