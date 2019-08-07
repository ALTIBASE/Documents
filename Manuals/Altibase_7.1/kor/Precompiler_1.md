<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Precompiler User’s Manual](#precompiler-users-manual)
  - [서문](#%EC%84%9C%EB%AC%B8)
    - [이 매뉴얼에 대하여](#%EC%9D%B4-%EB%A7%A4%EB%89%B4%EC%96%BC%EC%97%90-%EB%8C%80%ED%95%98%EC%97%AC)
  - [1.C/C++ 전처리기 소개](#1cc-%EC%A0%84%EC%B2%98%EB%A6%AC%EA%B8%B0-%EC%86%8C%EA%B0%9C)
    - [C/C++ 전처리기](#cc-%EC%A0%84%EC%B2%98%EB%A6%AC%EA%B8%B0)
    - [명령행 옵션](#%EB%AA%85%EB%A0%B9%ED%96%89-%EC%98%B5%EC%85%98)
    - [내장 SQL문을 이용한 프로그램 작성 순서 및 방법](#%EB%82%B4%EC%9E%A5-sql%EB%AC%B8%EC%9D%84-%EC%9D%B4%EC%9A%A9%ED%95%9C-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%A8-%EC%9E%91%EC%84%B1-%EC%88%9C%EC%84%9C-%EB%B0%8F-%EB%B0%A9%EB%B2%95)
  - [2.호스트 변수와 지시자 변수](#2%ED%98%B8%EC%8A%A4%ED%8A%B8-%EB%B3%80%EC%88%98%EC%99%80-%EC%A7%80%EC%8B%9C%EC%9E%90-%EB%B3%80%EC%88%98)
    - [호스트 변수](#%ED%98%B8%EC%8A%A4%ED%8A%B8-%EB%B3%80%EC%88%98)
    - [호스트 변수 분류](#%ED%98%B8%EC%8A%A4%ED%8A%B8-%EB%B3%80%EC%88%98-%EB%B6%84%EB%A5%98)
    - [지시자 변수](#%EC%A7%80%EC%8B%9C%EC%9E%90-%EB%B3%80%EC%88%98)
    - [지시자 변수 분류](#%EC%A7%80%EC%8B%9C%EC%9E%90-%EB%B3%80%EC%88%98-%EB%B6%84%EB%A5%98)
    - [지시자 변수값의 의미](#%EC%A7%80%EC%8B%9C%EC%9E%90-%EB%B3%80%EC%88%98%EA%B0%92%EC%9D%98-%EC%9D%98%EB%AF%B8)
    - [예제 프로그램](#%EC%98%88%EC%A0%9C-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%A8)
  - [3.호스트 변수 선언부](#3%ED%98%B8%EC%8A%A4%ED%8A%B8-%EB%B3%80%EC%88%98-%EC%84%A0%EC%96%B8%EB%B6%80)
    - [호스트 변수 선언부](#%ED%98%B8%EC%8A%A4%ED%8A%B8-%EB%B3%80%EC%88%98-%EC%84%A0%EC%96%B8%EB%B6%80)
    - [자료형 정의](#%EC%9E%90%EB%A3%8C%ED%98%95-%EC%A0%95%EC%9D%98)
    - [함수 인자 선언부](#%ED%95%A8%EC%88%98-%EC%9D%B8%EC%9E%90-%EC%84%A0%EC%96%B8%EB%B6%80)
  - [4.C Preprocessor](#4c-preprocessor)
    - [C Preprocessor 개요](#c-preprocessor-%EA%B0%9C%EC%9A%94)
    - [C Preprocessor 구문](#c-preprocessor-%EA%B5%AC%EB%AC%B8)
    - [Preprocessor 제약사항](#preprocessor-%EC%A0%9C%EC%95%BD%EC%82%AC%ED%95%AD)
    - [Preprocessor 예제](#preprocessor-%EC%98%88%EC%A0%9C)
    - [ALTIBASE_APRE 매크로](#altibase_apre-%EB%A7%A4%ED%81%AC%EB%A1%9C)
    - [주의 사항](#%EC%A3%BC%EC%9D%98-%EC%82%AC%ED%95%AD)
  - [5.호스트 변수 데이터 타입](#5%ED%98%B8%EC%8A%A4%ED%8A%B8-%EB%B3%80%EC%88%98-%EB%8D%B0%EC%9D%B4%ED%84%B0-%ED%83%80%EC%9E%85)
    - [개요](#%EA%B0%9C%EC%9A%94)
    - [일반 데이터 타입](#%EC%9D%BC%EB%B0%98-%EB%8D%B0%EC%9D%B4%ED%84%B0-%ED%83%80%EC%9E%85)
    - [확장된 데이터 타입](#%ED%99%95%EC%9E%A5%EB%90%9C-%EB%8D%B0%EC%9D%B4%ED%84%B0-%ED%83%80%EC%9E%85)
    - [칼럼 타입과 호스트 변수 타입](#%EC%B9%BC%EB%9F%BC-%ED%83%80%EC%9E%85%EA%B3%BC-%ED%98%B8%EC%8A%A4%ED%8A%B8-%EB%B3%80%EC%88%98-%ED%83%80%EC%9E%85)
  - [6.내장 SQL문](#6%EB%82%B4%EC%9E%A5-sql%EB%AC%B8)
    - [개요](#%EA%B0%9C%EC%9A%94-1)
    - [연결 관련 SQL문](#%EC%97%B0%EA%B2%B0-%EA%B4%80%EB%A0%A8-sql%EB%AC%B8)
    - [기본 내장 SQL문](#%EA%B8%B0%EB%B3%B8-%EB%82%B4%EC%9E%A5-sql%EB%AC%B8)
    - [기타 내장 SQL문](#%EA%B8%B0%ED%83%80-%EB%82%B4%EC%9E%A5-sql%EB%AC%B8)
    - [OPTION문](#option%EB%AC%B8)
  - [7.실행 시간 에러 처리](#7%EC%8B%A4%ED%96%89-%EC%8B%9C%EA%B0%84-%EC%97%90%EB%9F%AC-%EC%B2%98%EB%A6%AC)
    - [개요](#%EA%B0%9C%EC%9A%94-2)
    - [sqlca](#sqlca)
    - [SQLCODE](#sqlcode)
    - [SQLSTATE](#sqlstate)
    - [WHENEVER문](#whenever%EB%AC%B8)
    - [예제 프로그램](#%EC%98%88%EC%A0%9C-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%A8-1)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Altibase® Application Development

Precompiler User’s Manual
=========================

![](media/Precompiler/e5cfb3761673686d093a3b00c062fe7a.png)

Altibase Application Development Precompiler User’s Manual

Release 7.1

Copyright ⓒ 2001\~2018 Altibase Corp. All Rights Reserved.

본 문서의 저작권은 ㈜알티베이스에 있습니다. 이 문서에 대하여 당사의 동의 없이
무단으로 복제 또는 전용할 수 없습니다.

㈜알티베이스

08378 서울시 구로구 디지털로 306 대륭포스트타워Ⅱ 10층

전화: 02-2082-1114 팩스: 02-2082-1099

고객서비스포털: <http://support.altibase.com>

homepage: [http://www.altibase.com](http://www.altibase.com/)

서문
----

### 이 매뉴얼에 대하여

본 매뉴얼은 Altibase 내장 SQL문의 사용 방법과 C/C++ 전처리기의 사용 방법에 대해
설명한다. 사용자는 본 매뉴얼을 통해 Altibase 내장 SQL문을 이용한 응용 프로그램을
작성하고, 이를 전처리할 수 있다.

#### 대상 사용자

이 매뉴얼은 다음과 같은 Altibase 사용자를 대상으로 작성되었다.

-   데이터베이스 관리자

-   성능 관리자

-   데이터베이스 사용자

-   응용 프로그램 개발자

-   기술지원부

다음과 같은 배경 지식을 가지고 이 매뉴얼을 읽는 것이 좋다.

-   컴퓨터, 운영 체제 및 운영 체제 유틸리티 운용에 필요한 기본 지식

-   관계형 데이터베이스 사용 경험 또는 데이터베이스 개념에 대한 이해

-   컴퓨터 프로그래밍 경험

-   데이터베이스 서버 관리, 운영 체제 관리 또는 네트워크 관리 경험

#### 소프트웨어 환경

이 매뉴얼은 데이터베이스 서버로 Altibase 버전 7.1을 사용한다는 가정 하에
작성되었다.

#### 이 매뉴얼의 구성

이 매뉴얼은 다음과 같이 구성되어 있다.

-   제 1장 C/C++ 전처리기 소개  
    이 장은 C/C++ 전처리기 소개 및 사용 방법과 내장 SQL문을 이용한 프로그램 작성
    순서에 대해 설명한다.

-   제 2장 호스트 변수와 지시자 변수  
    이 장은 호스트 변수, 지시자 변수에 대한 설명과 분류 및 지시자 변수값의
    의미에 대해 설명한다.

-   제 3장 호스트 변수 선언부  
    이 장은 호스트 변수 선언부와 함수 인자 선언부에 대해 설명한다.

-   제 4장 C Processor

-   제 5장 호스트 변수 데이터 타입  
    이 장은 호스트 변수의 데이터 타입으로 사용 가능한 데이터 타입들에 대해
    설명한다.

-   제 6장 내장 SQL 문  
    이 장은 연결 관련 SQL 문, 기본 내장 SQL 문, 기타 내장 SQL 문에 대해
    설명한다.

-   제 7장 실행시간 에러 처리  
    이 장은 실행 시간 에러 처리를 위해 참조할 수 있는 변수들에 대해 설명한다.

-   제 8장 커서 처리 SQL 문  
    이 장은 커서 처리 SQL 문에 대해 설명한다.

-   제 9장 배열 처리 SQL 문  
    이 장은 배열 호스트 변수 사용, 제한 사항, 구조체와 배열에 관해 설명한다.

-   제 10장 동적 SQL 문  
    이 장은 동적 SQL 문에 대해 설명한다.

-   제 11장 저장 프로시저 처리 SQL 문  
    이 장은 저장 함수 또는 저장 프로시저의 사용 방법에 대해 설명한다.

-   제 12장 다중 연결 프로그램  
    이 장은 다중 연결 프로그램 작성 방법에 대해 설명한다.

-   제 13장 멀티쓰레드 프로그램  
    이 장은 멀티쓰레드 환경에서의 프로그램 작성 방법에 대해 설명한다.

-   제 14장 전처리 오류 코드/메시지  
    이 장은 전처리 시 발생하는 오류 코드 및 오류 메시지에 대해 설명한다.

-   A. 부록 : LOB 데이터와 파일  
    이 장에서는 BLOB, CLOB 타입의 데이터를 입력하거나 출력할 때 파일 시스템을
    사용하는 방법에 대해 설명한다.

-   B 부록 : Proc\*C에서 APRE로 변환  
    오라클의 pro\*C(C++)로 작성된 응용 프로그램을 Altibase C/C++ Precompiler
    응용 프로그램으로 전환할 때 참조한다.

-   C 부록 : 동적 SQL의 메소드4 사용  
    이 장은 사용자가 프로그램 실행 시에 파라미터 마커의 값에 입력할 수 있는 동적
    SQL의 메소드4를 사용할 시 참조한다.

-   D 부록 : Sample code  
    이 장은 매뉴얼에 사용된 예제 프로그램과 사용하는 테이블 정보에 대해
    설명한다.

-   E 부록 : FAQ  
    이 장은 C/C++ 전처리기와 Altibase 내장 SQL문의 사용 방법에 대해 사용자들이
    자주하는 질문을 모은 것이다.

#### 문서화 규칙

이 절에서는 이 매뉴얼에서 사용하는 규칙에 대해 설명한다. 이 규칙을 이해하면 이
매뉴얼과 설명서 세트의 다른 매뉴얼에서 정보를 쉽게 찾을 수 있다.

여기서 설명하는 규칙은 다음과 같다.

-   구문 다이어그램

-   샘플 코드 규칙

##### 구문 다이어그램

이 매뉴얼에서는 다음 구성 요소로 구축된 다이어그램을 사용하여, 명령문의 구문을
설명한다.

| 구성 요소                           | 의미                                                         |
| ----------------------------------- | ------------------------------------------------------------ |
| ![](media/Precompiler/image004.gif) | 명령문이 시작한다. 완전한 명령문이 아닌 구문 요소는 화살표로 시작한다. |
| ![](media/Precompiler/image006.gif) | 명령문이 다음 라인에 계속된다. 완전한 명령문이 아닌 구문 요소는 이 기호로 종료한다. |
| ![](media/Precompiler/image008.gif) | 명령문이 이전 라인으로부터 계속된다. 완전한 명령문이 아닌 구문 요소는 이 기호로 시작한다. |
| ![](media/Precompiler/image010.gif) | 명령문이 종료한다.                                           |
| ![](media/Precompiler/image012.gif) | 필수 항목                                                    |
| ![](media/Precompiler/image014.gif) | 선택적 항목                                                  |
| ![](media/Precompiler/image016.gif) | 선택사항이 있는 필수 항목. 한 항목만 제공해야 한다.          |
| ![](media/Precompiler/image018.gif) | 선택사항이 있는 선택적 항목                                  |
| ![](media/Precompiler/image020.gif) | 선택적 항목. 여러 항목이 허용된다. 각 반복 앞부분에 콤마가 와야 한다. |

##### 샘플 코드 규칙

코드 예제는 SQL, Stored Procedure, iSQL 또는 다른 명령 라인 구문들을 예를 들어
설명한다.

아래 테이블은 코드 예제에서 사용된 인쇄 규칙에 대해 설명한다.

| 규칙         | 의미                                                         | 예제                                                         |
| ------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ ]          | 선택 항목을 표시                                             | VARCHAR [(*size*)] [[FIXED \|] VARIABLE]                     |
| { }          | 필수 항목 표시. 반드시 하나 이상을 선택해야 되는 표시        | { ENABLE \| DISABLE \| COMPILE }                             |
| \|           | 선택 또는 필수 항목 표시의 인자 구분 표시                    | { ENABLE \| DISABLE \| COMPILE } [ ENABLE \| DISABLE \| COMPILE ] |
| . . .        | 그 이전 인자의 반복 표시 예제 코드들의 생략되는 것을 표시    | SQL\> SELECT ename FROM employee;<br/> ENAME<br/>  -----------------------<br/> SWNO <br/> HJNO<br/>  HSCHOI <br/> .<br/> .<br/> . <br/>20 rows selected. |
| 그 밖에 기호 | 위에서 보여진 기호 이 외에 기호들                            | EXEC :p1 := 1; acc NUMBER(11,2);                             |
| 기울임 꼴    | 구문 요소에서 사용자가 지정해야 하는 변수, 특수한 값을 제공해야만 하는 위치 | SELECT \* FROM *table_name*;<br/> CONNECT *userID*/*password*; |
| 소문자       | 사용자가 제공하는 프로그램의 요소들, 예를 들어 테이블 이름, 칼럼 이름, 파일 이름 등 | SELECT ename FROM employee;                                  |
| 대문자       | 시스템에서 제공하는 요소들 또는 구문에 나타나는 키워드       | DESC SYSTEM_.SYS_INDICES_;                                   |

#### 관련 자료

자세한 정보를 위하여 다음 문서 목록을 참조하기 바란다.

-   Installation Guide

-   Administrator’s Manual

-   CLI User's Manual

-   SQL Reference

-   Stored Procedures Manual

-   iSQL User’s Manual

-   Error Message Reference

#### Altibase는 여러분의 의견을 환영합니다.

이 매뉴얼에 대한 여러분의 의견을 보내주시기 바랍니다. 사용자의 의견은 다음
버전의 매뉴얼을 작성하는데 많은 도움이 됩니다. 보내실 때에는 아래 내용과 함께
고객서비스포털( http://support.altibase.com/kr/ )로 보내주시기 바랍니다.

-   사용 중인 매뉴얼의 이름과 버전

-   매뉴얼에 대한 의견

-   사용자의 성함, 주소, 전화번호

이 외에도 Altibase 기술지원 설명서의 오류와 누락된 부분 및 기타 기술적인
문제들에 대해서 이 주소로 보내주시면 정성껏 처리하겠습니다. 또한, 기술적인
부분과 관련하여 즉각적인 도움이 필요한 경우에도 고객서비스포털을 통해 서비스를
요청하시기 바랍니다.

여러분의 의견에 항상 감사드립니다.

1.C/C++ 전처리기 소개
-------------------

### C/C++ 전처리기

#### 소개

C/C++ 전처리기 (precompiler)는 내장 SQL문이 포함된 소스 프로그램을 입력 받아,
내장 SQL문들을 Altibase CLI 함수 호출로 변환하여, 호스트 언어로 컴파일 될 수
있는 수정된 소스 프로그램을 생성한다.

사용자는 간단한 내장 SQL문을 사용하여 쉽게 응용 프로그램을 작성하고, 작성된 응용
프로그램을 전처리 한 후, compile, link 할 수 있다.

내장 SQL문을 이용한 프로그램 작성은 ODBC를 이용한 프로그램 작성에 비해 프로그램
작성법이 쉬우면서도 동등한 성능을 가지는 프로그램을 작성할 수 있다.

#### 환경 설정

C/C++ 전처리기로 전처리된 결과 파일을 컴파일 및 링크하기 위해서 필요한 환경
설정은 다음과 같다.

##### 헤더파일

-   필요한 헤더파일은 *ulpLibInterface.h*이며, \$ALTIBASE_HOME/include
    디렉터리에 있다.

-   전처리된 응용 프로그램을 컴파일하기 위해서는 –I \$ALTIBASE_HOME/include
    옵션이 필요하다.

##### 라이브러리

-   필요한 라이브러리는 *libapre.a*와 *libodbccli.a*이며, \$ALTIBASE_HOME/lib
    디렉토리에 있다.
-   컴파일된 오브젝트 파일은 다음의 옵션과 함께 링크해야 한다:

```
–L $ALTIBASE_HOME/lib –lapre, –lodbccli, -lpthread
```

> #### 주의사항
>
> Altibase 클라이언트 라이브러리는 system signal 발생에 대해 안전하지 않다.
>
> 따라서 외부 원인에 의해 네트워크 접속이 종료된 경우, SIGPIPE 신호를 받아
> 진행중인 응용 프로그램이 강제로 종료될 수도 있다. 이러한 강제 종료를 막기
> 위해서는 SIGPIPE 신호를 사용자 애플리케이션에서 처리해야 한다. 그러나 SIGPIPE
> 신호 처리를 하던 중에 Altibase 클라이언트 라이브러리의 함수를 호출하면
> 프로그램이 멈출 수 있기 때문에 호출하면 안된다.
>
> 하지만 신호 처리가 끝난 후에는 Altibase 클라이언트 라이브러리의 함수를 호출하는
> 것이 가능하다.

#### 전처리 실행

C/C++ 전처리기는 내장 SQL문을 포함하는 C 또는 C++로 작성된 프로그램을 전처리하여
변환된 C 또는 C++ 프로그램을 생성한다. 입력 파일은 .sc 확장자를 가지는 C 또는
C++로 작성된 프로그램이며, 출력 파일은 .c 또는 .cpp를 확장자를 가진다. 출력
파일의 확장자는 사용자가 지정할 수 있으며 기본적으로 .c이다.

##### 실행방법

```
apre [ <apre-options> ] <filename>
```

##### 실행인자

-   \<*filename*\> : 내장 SQL문을 포함하는 소스 프로그램으로, 확장자는 반드시
    .sc이어야 한다. 소스 프로그램은 1개 이상 나열할 수 있으며 나열된 소스를 모두
    처리하게 된다. 또한 \*.sc와 같은 문법을 지원한다.

[예제 1] c로 작성된 프로그램을 전처리하는 명령을 보여준다. 전처리 후 생성되는
파일은 sample1.c 이다.

```
$ apre sample1.sc
```

[예제 2] 여러 개의 프로그램을 전처리하는 명령을 보여준다 .

```
$ apre sample1.sc sample2.sc 
$ apre *.sc
```

-   \<*apre-options*\> : APRE\*C/C++ 명령행 옵션이다. 자세한 설명은 다음 절
    APRE\*C/C++ 명령행 옵션을 참고한다.

##### 실행화면

C/C++ 전처리기의 실행화면은 다음과 같다.

```
$ apre sample1.sc
--------------------------------------------------------
  APRE C/C++ Precompiler.
  Release Version 7.1.0.0.0
  Copyright 2000, Altibase Corporation or its subsidiaries.
  All rights reserved.
--------------------------------------------------------
```

### 명령행 옵션

전처리시 명령행에 입력할 수 있는 여러 옵션들이 있다. 이 명령행 옵션들의 기능에
대한 설명은 아래와 같다.

##### 실행옵션

```
-h
```

: APRE 실행 방법을 보여준다. 보여주는 화면은 다음과 같다.

```
$ apre -h
===========================================================
APRE (Altibase Precompiler) C/C++ Precompiler HELP Screen
===========================================================
Usage  :  apre [<options>] <filename>

-h               : Display this help information.
-t <c|cpp>       : Specify the file extension for the output file.
                   c   - File extension is '.c' (default)
                   cpp - File extension is '.cpp'
-o <output_path> : Specify the directory path for the output file.
                   (default : current directory)
-mt              : When precompiling a multithreaded application,
                   this option must be specified.
-I<include_path> : Specify the directory paths for files included using APRE C/C++.
                   (default : current directory)
-parse <none|partial|full>
                 : Control which non-SQL code is parsed.
-D<define_name>  : Use to define a preprocessor symbol.
-v               : Output the version of APRE.
-n               : Specify when CHAR variables are not null-padded.
-unsafe_null     : Specify to suppress errors when NULL values are fetched
                   and indicator variables are not used.
-align           : Specify when using alignment in AIX.
-spill <values>  : Specify the register allocation spill area size.
-keyword         : Display all reserved keywords.
-debug <macro|symbol>
                 : Use for debugging.
                   macro   - Display macro table.
                   symbol  - Display symbol table.
-nchar_var <variable_name_list>
                 : Process the specified variables using
                   the Altibase national character set.
-nchar_utf16     : Set client nchar encoding to UTF-16.
-lines           : Add #line directives to the generated code.
-silent          : No display Copyright.
================================================
```

#### \-t \<c\|cpp\>

C/C++ 전처리기로 전처리하여 생성되는 결과 파일의 확장자를 지정한다. c로 지정하면
.c 파일이 생성되고, cpp로 지정하면 .cpp 파일이 생성된다. 지정하지 않으면 .c
파일을 생성한다.

##### 예제

C++로 작성된 프로그램을 전처리하는 명령을 보여준다. 전처리 후 생성되는 파일은
sample1.cpp 이다.

```
$ apre –t cpp sample1.sc
```

#### \-o \<output_path\>

C/C++ 전처리기로 전처리한 결과 파일이 생성될 위치를 지정한다. 지정하지 않으면,
현재 디렉토리에 결과 파일이 생성된다. 결과 파일이 생성될 위치는 하나만 지정할 수
있다.

#### \-mt

전처리할 파일이 멀티쓰레드 프로그램일 경우, 반드시 이 옵션을 지정하여야 한다. 이
옵션은 각각의 소스 파일(.sc)에 적용할 수 없으므로, 두 개 이상의 소스 파일을
전처리하여 실행 프로그램을 만드는 경우에는 모든 소스 파일에 이 옵션을 적용해야
한다.

“EXEC SQL OPTION(THREADS=TRUE);”내장 SQL문으로 대신할 수 있다. 즉, 전처리할 파일
안에서 위 내장 SQL문을 선언하였다면 전처리 시 이 옵션은 생략 가능하다.

다만, 여러 파일을 한번에 전처리 할 경우, 이 옵션이 내장 SQL보다 우선 적용된다.
즉, 이 옵션을 선택하면 전처리 할 파일들은 모두 적용된다.

OPTION문에 대한 자세한 설명은 6장 내장 SQL문을 참조하기 바란다.

#### \-I\<include_path\>

전처리 시 사용될 헤더 파일의 위치를 지정한다. 지정하지 않으면, 전처리 시
사용되는 헤더파일은 현재 디렉토리에서 찾는다. 디렉토리 지정 시 절대경로와
상대경로 모두 가능하다.

##### 예제

전처리 시 사용될 헤더파일의 위치를 지정하는 방법을 보여준다. 여기에서는 전처리
시 사용되는 헤더파일을 현재 디렉토리와 /include 디렉토리에서 순서대로 찾는다.
예제에서 보는 바와 같이 지정할 디렉토리가 하나 이상일 경우 -I 옵션을 여러 번
사용한다. 그리고 디렉토리는 절대경로, 상대경로 모두 가능하다.

```
$ apre –I. -I/include sample1.sc
```

#### \-parse \<none\|partial\|full\>

전처리시 소스파일에 대한 파싱 처리 범위를 결정한다. 위 옵션에 따라 소스파일에서
\#include 로 포함하는 헤더파일에 대한 처리범위도 달라진다. -parse옵션을 주지
않았을 경우 partial로 처리된다.

##### none

EXEC SQL BEGIN/END DECLARE SECTION 안에 있는 호스트 변수 선언들과 매크로
명령들을 처리하며, 외부에 선언된 변수들과 매크로들은 무시된다. 소스파일 내의
내장SQL구문들은 모두 처리된다.

##### partial

모든 매크로 명령들을 처리하며, 호스트 변수는 EXEC SQL BEGIN/END DECLARE SECTION
안에 선언된 것들만 처리된다. \#include로 포함된 헤더파일은 매크로 명령들만
처리된다. 반면 소스파일 내의 내장SQL구문들은 모두 처리된다.

##### full

전처리기에 내장된 C 파서가 동작하여 EXEC SQL BEGIN/END DECLARE SECTION 밖에
선언된 변수들도 처리가 되며, 모든 매크로 명령들이 처리된다. 또한, \#include로
포함된 헤더파일의 매크로 명령들뿐 아니라 변수 선언부분도 처리 된다. 마지막으로
소스파일 내의 내장SQL구문들이 모두 처리된다.

그러나, 사용자가 이 옵션을 지정하여도 성능 저하가 발생할 수 있기 때문에,
Altibase 전처리기는 \#include를 사용하여 포함된 시스템 헤더 파일을 파싱하지
않는다. 따라서, 시스템 헤더 파일에 정의되어 있는 타입이 호스트 변수로 사용되면,
전처리 중에 오류가 발생한다. 이를 방지하기 위해 사용자는 시스템 헤더 파일에서
사용하고자 하는 타입을 Altibase가 제공하는
\$ALTIBASE_HOME/include/aprePredefinedTypes.h 헤더 파일에 정의해야 한다.

단, “\*.sc” 소스 파일에는 aprePredefinedTypes.h가 아닌 시스템 헤더 파일을
\#include로 포함해야 한다. APRE 전처리 시에는 aprePredefinedTypes.h 파일을
자동으로 참조하지만, 컴파일 시에는 시스템 헤더 파일이 참조되어야 하기 때문이다.

> ##### 주의사항
>
> \-parse 옵션을 full로 설정했을 경우 C 파서가 동작하기 때문에 C++ 소스 코드는
> 전처리 중 파싱 에러를 발생시킬 수 있다. 따라서 C++ 소스 코드에서는 –parse 옵션을
> 아예 사용하지 않던가 또는 –parse 옵션을 사용하더라도 partial/none으로 설정해
> 줘야 한다.

##### 예제

```
$ apre -parse none –t cpp sample1.sc
$ apre -parse partial –t cpp sample1.sc
$ apre -parse full –t cpp sample1.sc
```

#### \-D\<define_name\>

전처리시 사용될 매크로 이름을 저장한다. 이 명령행 옵션은 코드 내에
\#define매크로를 정의하는 것과 같은 기능을 한다.

##### 예제

sample1.sc을 전처리하기 전 Altibase라는 매크로를 정의하고 싶다면 아래와 같이
명령행 옵션을 설정한다.

```
$ apre -DAltibase –t cpp sample1.sc
```

#### \-v

C/C++ 전처리기의 버전을 보여준다.

##### 예제

C/C++ 전처리기의 버전을 확인하는 방법이다.

```
$ apre –v
Altibase Precompiler2(APRE) Ver. 7.1.0.0.1 XEON_LINUX_redhat_Enterprise_AS4-64bit-7.1.0.0.1-release-GCC3.4.6 (xeon-redhat-linux-gnu) Oct 23 2013 09:28:30
```

#### \-n

호스트 변수의 데이터 타입이 CHAR이며 null character (‘\\0’)로 끝나지 않을 때
사용하는 옵션이다. 여러 개의 소스 파일(.sc)을 전처리하여 한 개의 실행 프로그램을
만드는 경우에는 필요한 모든 소스 파일에 이 옵션을 적용해야 한다. 입력 호스트
변수의 크기가 데이터베이스 칼럼 크기보다 작거나 같아야 한다.

#### \-unsafe_null

지시자 변수를 지정하지 않았을 경우, 널(null) 값을 Fetch해도 에러가 발생하지
않도록 설정하는 옵션이다. 여러 개의 소스 파일(.sc)을 전처리하여 한 개의 실행
프로그램을 만드는 경우에는 필요한 모든 소스 파일에 이 옵션을 적용해야 한다.

SELECT질의문 수행시 FETCH한 칼럼 값이 널인 경우에 지시자 변수 값이 설정되어 있지
않으면 에러가 발생한다.

#### \-spill \<values\>

AIX 장비에서 전처리할 때에만 이 옵션을 설정할 수 있으며, 다음과 같이 소스 파일
내에서도 지정할 수 있다.

```
#pragma options spill=<values>
```

#### \-keyword

Embedded SQL구문과 관련된 예약어 목록을 보여준다.

##### 예제

```
$ apre -keyword

:: Keywords for C code ::
:: Keywords for C code ::
ALTIBASE_APRE APRE_BINARY APRE_BINARY2 APRE_BIT APRE_BLOB APRE_BLOB_LOCATOR APRE_BYTES APRE_CLOB APRE_CLOB_LOCATOR APRE_DUPKEY_ERR APRE_INTEGER APRE_NIBBLE APRE_NUMERIC APRE_VARBYTES MAX_CHAR_PTR SESC_DECLARE SESC_INCLUDE SES_BINARY SES_BIT SES_BLOB SES_BLOB_LOCATOR SES_BYTES SES_CLOB SES_CLOB_LOCATOR SES_DUPKEY_ERR SES_INTEGER SES_NIBBLE SES_NUMERIC SES_VARBYTES SQLFailOverCallback SQLLEN SQL_DATE_STRUCT SQL_TIMESTAMP_STRUCT SQL_TIME_STRUCT SQL_NUMERIC_STRUCT VARCHAR

:: Keywords for Embedded SQL statement ::
ABSOLUTE ADD AFTER AGER ALL ALLOCATE ALTER AND ANY ARCHIVE ARCHIVELOG AS ASC ASENSITIVE AT AUTOCOMMIT BACKUP BATCH BEFORE BEGIN BETWEEN BLOB_FILE BREAK BY CASCADE CASE CAST CLEAR_RECPTRS CLOB_FILE CLOSE COALESCE COLUMN COMMIT COMPILE CONNECT CONSTANT CONSTRAINT CONSTRAINTS CONTINUE CREATE CUBE CURSOR CYCLE DATABASE DEALLOCATE DECLARE DEFAULT DELETE DEQUEUE DESC DESCRIPTOR DIRECTORY DISABLE DISABLE_RECPTR DISCONNECT DISTINCT DO DROP EACH ELSE ELSEIF ELSIF ENABLE ENABLEALL_RECPTRS ENABLE_RECPTR END ENQUEUE ESCAPE EXCEPTION EXEC EXECUTE EXISTS EXIT EXTENTSIZE FALSE FETCH FIFO FIRST FIXED FLUSH FOR FOREIGN FOUND FREE FROM FULL FUNCTION GOTO GRANT GROUP GROUPING HAVING HOLD IDENTIFIED IF IMMEDIATE IN INDEX INDICATOR INNER INSENSITIVE INSERT INTERSECT INTO IS ISOLATION JOIN KEY LAST LEFT LESS LEVEL LIFO LIKE LIMIT LOB LOCAL LOCK LOGANCHOR LOOP MAXROWS MERGE MINUS MODE MOVE MOVEMENT NEW NEXT NOARCHIVELOG NOCYCLE NOPARALLEL NOT NULL OF OFF OFFLINE OLD ON ONERR ONLINE ONLY OPEN OPTION OR ORDER OTHERS OUT OUTER PARALLEL PARTITION PARTITIONS PREPARE PRIMARY PRIOR PRIVILEGES PROCEDURE PUBLIC QUEUE RAISE READ REBUILD RECOVER REFERENCES REFERENCING RELATIVE RELEASE RENAME REPLACE REPLICATION RESTRICT RETURN REVERSE REVOKE RIGHT ROLLBACK ROLLUP ROW ROWCOUNT ROWTYPE SAVEPOINT SCROLL SELECT SENSITIVE SEQUENCE SESSION SET SETS SOME SPLIT SQLCODE SQLERRM SQLERROR SQLLEN START STATEMENT STEP STORE SYNONYM TABLE TABLESPACE TEMPORARY THAN THEN THREADS TO TRIGGER TRUE TRUNCATE TYPE TYPESET UNION UNIQUE UNTIL UPDATE USER USING VALUES VARCHAR VARIABLE VIEW VOLATILE WAIT WAKEUP_RECPTR WHEN WHENEVER WHERE WHILE WITH WORK WRITE
```

#### \-debug \<macro\|symbol\>

디버깅을 하기 위한 용도로 쓰이며, 소스 내에 정의된 매크로 이름이나 선언된 변수의
목록을 출력한다.

##### macro

정의된 매크로 이름의 정보를 저장하고 있는 매크로 목록을 출력한다.

##### symbol

선언된 변수들의 정보를 저장하고 있는 목록을 출력한다.

##### 예제

sample1.sc안에 정의된 모든 매크로를 보여준다.

```
$ apre –debug macro sample1.sc
```

sample1.sc안에 선언된 변수의 정보를 보여준다.

```
$ apre –debug symbol sample1.sc
```

매크로와 변수 모두 출력한다.

```
$ apre –debug macro symbol sample1.sc
```

#### \-lines

전처리로 생성되는 .c 또는 .cpp 파일에 \#line이 삽입되도록 설정하여, '\*.sc' 소스
파일의 내용과 비교할 수 있다.

##### 예제

sample.sc 파일이 전처리로 생성된 후에 \#line을 있는 것을 확인할 수 있다.

```
$ apre –debug macro symbol sample1.sc
```

#### \-nchar_utf16

이 옵션은 전처리 할 때 내셔널 캐릭터 타입의 문자를 UTF-16으로 인코딩하도록
설정해주는 옵션이다. 이 옵션은 각각의 소스 파일(.sc)에 적용할 수 없으므로, 두 개
이상의 소스 파일을 전처리하여 실행 프로그램을 만드는 경우에는 모든 소스 파일에
이 옵션을 적용해야 한다. 이 옵션을 사용하지 않을 경우에는 기본적으로
ALTIBASE_NLS_USE에서 설정한 방식으로 인코딩된다.

그러나 ALTIBASE_NLS_USE에서 설정한 인코딩 방식을 사용할 시에는 유니코드 문자를
정확히 출력할 수 없으므로 조회 연산시에 데이터 손실이 발생할 수 있다.

##### 예제

UTF-16으로 프로그램을 전처리한다.

```
$ apre -nchar_utf16 -t cpp sample.sc
```

#### \-nchar_var \<variable_name_list\>

Altibase가 지원하는 내셔널 캐릭터 타입의 데이터를 전처리기에서 처리하기 위해서
사용하는 옵션이다. 변수명과 변수명 사이에는 공백을 허용하지 않으며, 구조체 안의
멤버 변수는 여기에 지정할 수 없다.

#### -silent

silent 모드를 켜는 옵션이다. silent 모드를 켜면 Copyright 등의 부가적인 설명들을 보여주지 않는다.

### 내장 SQL문을 이용한 프로그램 작성 순서 및 방법

본 절에서는 내장 SQL문을 이용하여 프로그램을 작성할 경우, 어떤 순서와 방법으로
작성해야 하는지 전체적인 흐름에 대하여 간단히 설명한다.

다음 설명을 통해 프로그램 작성 순서 및 방법에 대해 알아보고 프로그램의 전체적인
흐름을 파악해보자.

#### 호스트 변수 선언

프로그램 작성 시 가장 먼저 해야 할 일은 사용할 호스트 변수와 지시자 변수들의
선언이다. –partial 명령행 옵션으로 “full”을 사용하지 않을 경우, 호스트 변수는
호스트 변수 선언부에 선언해야 한다.

호스트 변수와 지시자 변수에 대한 자세한 설명은 2장을 참조하기 바란다.

##### 호스트 변수 선언시 주의 사항

-   중첩된 구조체를 호스트 변수로 사용할 수 없다. 즉, 구조체의 구성 요소는
    구조체일 수 없다.

-   매크로는 배열 타입의 호스트 변수 선언 시 배열 요소 개수를 지정하는 용도로만
    사용 가능하다. 예를 들어 내장 SQL문에서 호스트 변수를 사용할 수 있는 위치에
    매크로 정의를 사용할 수 없다.

-   문자형 타입(char, varchar)으로 호스트 변수 선언시 호스트 변수 크기는
    대응되는 칼럼 크기보다 1 크게 선언하여야 한다. 그렇지 않으면 SELECT문이나
    FETCH문 수행 후 칼럼값이 잘려서 반환되기 때문에 sqlca.sqlcode값이
    SQL_SUCCESS_WITH_INFO가 된다.

##### 배열 호스트 변수 선언시 주의 사항

배열 호스트 변수 사용에 대한 자세한 설명은 9장을 참조하기 바란다.

-   배열 호스트 변수는 1차원 배열만을 허용한다. 예외적으로, 문자열 표현을 위해
    ‘char’ 타입과 ‘varchar’ 타입에 한해 2차원 배열을 허용한다.

-   호스트 변수가 구조체의 배열인 경우 지시자 변수를 사용할 수 없다.

-   SELECT문 또는 FETCH문의 INTO절에 구조체의 배열을 호스트 변수로 사용할 경우
    출력 호스트 변수는 하나만 사용할 수 있다. 즉 다른 호스트 변수들과 함께
    사용할 수 없다. 따라서 INTO절에 사용할 호스트 변수가 구조체의 배열
    타입이라면 이 구조체의 구성 요소 개수는 SELECT절의 칼럼 개수와 동일해야
    한다.

-   마찬가지로 INSERT문의 VALUES절에 구조체의 배열을 호스트 변수로 사용할 경우
    입력 호스트 변수는 하나만 사용할 수 있다. 즉 다른 호스트 변수들과 함께
    사용할 수 없다. 따라서 VALUES절에 사용할 호스트 변수가 구조체의 배열
    타입이라면 이 구조체의 구성 요소 개수는 INSERT문의 칼럼 개수와 동일해야
    한다.

-   ‘varchar’ 타입도 내부적으로 구조체이므로 위의 제한 사항이 적용된다.

-   배열 타입과 배열이 아닌 타입을 함께 사용할 수 없다.

-   SELECT문 또는 FETCH문 수행 시 배열 타입의 출력 호스트 변수를 사용하였다면
    반환되는 레코드 개수가 배열 크기보다 작을 경우 sqlca.sqlcode는
    SQL_SUCCESS이다.

-   SELECT문 또는 CURSOR문 수행 시 입력 호스트 변수는 배열일 수 없다.

-   FOR절은 입력 호스트 변수가 배열일 경우 INSERT문, UPDATE문, DELETE문을
    사용하고, 출력 호스트 변수가 배열이면 FETCH문에서 사용할 수 있다.

-   AUTOCOMMIT 모드의 경우 배열 타입의 호스트 변수를 사용할 경우 배열 전체가
    하나의 트랜잭션이 아니고 배열 요소 각각이 하나의 트랜잭션이다. 따라서 배열
    요소 중 일부는 성공하고 일부는 실패한다면 성공한 트랜잭션의 변경 사항은
    데이터베이스 서버에 영구히 저장된다.

-   포인터 타입은 배열로 선언할 수 없다.

##### 지시자 변수 선언시 주의 사항

-   지시자 변수의 데이터 타입은 ‘int’ 타입이어야 한다.

-   입력 호스트 변수로 ‘varchar’ 타입 사용시 별도의 지시자 변수를 지정하지 않은
    경우 구성 요소 len의 값을 반드시 지정하여야 한다. len에는 arr의 값이 NULL 이
    아니면 arr 값의 길이를, NULL 이면 -1을 지정하여야 한다.

-   호스트 변수가 숫자형 데이터 타입일 때, 지시자 변수가 -1이 아닌 경우 지시자
    변수값은 무의미하다.

-   호스트 변수의 타입이 이진 데이터 타입일 경우 반드시 지시자 변수를 사용하여야
    한다.

##### 호스트 변수 선언부

호스트 변수 선언부에 대한 자세한 설명은 3장을 참조하기 바란다.

-   호스트 변수의 데이터 타입으로 사용할 자료형 정의(typedef)는 호스트 변수
    선언부에서 정의되어야 한다.

##### 예제

다음은 호스트 변수를 선언하는 예를 보여준다.

< 예제 프로그램 : insert.sc >

```
/* declare host variables */
EXEC SQL BEGIN DECLARE SECTION;
char usr[10];
char pwd[10];
char    s_gno[10+1];
char    s_gname[20+1];
char    s_goods_location[9+1];
int     s_stock;
double  s_price;
EXEC SQL END DECLARE SECTION;
```

#### 데이터베이스 서버에 연결

호스트 변수의 선언이 끝나면 다른 내장 SQL문의 수행에 앞서 데이터베이스 서버에
연결하여야 한다.

모든 내장 SQL문은 데이터베이스 서버와의 연결이 성공하고 난 뒤 수행 가능하다.

데이터베이스 서버와의 연결에 대한 자세한 설명은 6장을 참조하기 바란다.

##### CONNECT문, 다중 연결, SESSION 관련 주의 사항

-   프로그램 안에서 connect 후 같은 연결 이름으로 다시 connect를 시도한다면,
    connect 이전에 반드시 FREE문 또는 DISCONNECT문을 수행하여야 한다. 이 때,
    데이터베이스 서버가 running 상태라면 DISCONNECT문을 수행하여야 하고, running
    상태가 아니라면 FREE문을 수행하여야 한다.

-   USING절을 이용하여 연결 방식을 지정할 경우, CONNTYPE을 2 또는 3으로
    지정한다면 DSN 또는 PORT_NO를 함께 지정하더라도 DSN, PORT_NO 옵션은 무시되고
    로컬 데이터베이스 서버로 연결을 시도한다.

-   connect 시 연결 옵션 2개 지정하여 수행하는 경우 처음 옵션으로 연결 성공하면
    sqlca.sqlcode는 SQL_SUCCESS이고, 처음 실패하고 두 번째 옵션으로 연결
    성공하면 sqlca.sqlcode는 SQL_SUCCESS_WITH_INFO이고, 둘 다 실패하면
    sqlca.sqlcode는 SQL_ERROR이다.

-   한 connection 당 내장 SQL문은 최대 1024개까지만 허용한다.

-   AUTOCOMMIT OFF session에서 commit을 하지 않고 프로그램을 종료할 경우, commit
    하지 않은 SQL문은 모두 rollback 처리 된다. 그러나 DISCONNECT문을 수행하고
    프로그램을 종료할 경우, 수행한 모든 내장 SQL문이 commit 처리된다.

-   다음의 내장 SQL문에서는 AT절을 허용하지 않는다.  
    INCLUDE문: EXEC SQL INCLUDE …  
    OPTION문: EXEC SQL OPTION …  
    WHENEVER문: EXEC SQL WHENEVER …

##### 예제

다음은 데이터베이스 서버에 연결하는 예를 보여준다.

\< 예제 프로그램 : connect1.sc \>

```
/* declare host variables */
EXEC SQL BEGIN DECLARE SECTION;
char usr[10];
char pwd[10];
EXEC SQL END DECLARE SECTION;

/* set username */
strcpy(usr, "SYS");
/* set password */
strcpy(pwd, "MANAGER");

EXEC SQL CONNECT :usr IDENTIFIED BY :pwd;  
if (sqlca.sqlcode == SQL_SUCCESS) /* check sqlca.sqlcode */
{
    printf("Success connection to altibase server\n\n");
}
else
{
    printf("Error : [%d] %s\n\n", SQLCODE, sqlca.sqlerrm.sqlerrmc);
    exit(1);
}
```

#### 내장 SQL문 수행

데이터베이스 서버에 연결 성공 후 내장 SQL문을 수행할 수 있다. 여기에서 내장
SQL문은 SELECT, INSERT 등의 DML, CREATE 등의 DDL, 시스템 제어문, 커서 관련
SQL문, 동적 SQL문 등 Altibase SQL문을 수행할 수 있는 모든 내장 SQL문을 의미한다.

다양한 내장 SQL문들의 사용 방법에 대한 자세한 설명은 6장, 8장, 9장, 10장 그리고
11장을 참조하기 바란다.

##### 예제

다양한 내장 SQL문의 사용 예를 보여준다.

[예제 1] 다음은 UPDATE문의 사용 예를 보여준다.

\< 예제 프로그램 : update.sc \>

```
/* declare host variables */
EXEC SQL BEGIN DECLARE SECTION;
int      s_eno;
short    s_dno;
varchar  s_emp_job[15+1];
EXEC SQL END DECLARE SECTION;

s_eno = 2;
s_dno = 1001;
strcpy(s_emp_job.arr, "ENGINEER");
s_emp_job.len = strlen(s_emp_job.arr);

EXEC SQL UPDATE EMPLOYEES 
SET DNO     = :s_dno,
                EMP_JOB = :s_emp_job
            WHERE ENO = :s_eno;
```

[예제 2] 다음은 CURSOR문의 사용 예를 보여준다.

\< 예제 프로그램 : hostvar.h \>

```
EXEC SQL BEGIN DECLARE SECTION;
typedef struct department
{
    short dno; 
    char  dname[30+1];
    char  dep_location[9+1];
    int   mgr_no;
} department;

typedef struct dept_ind
{
    int dno; 
    int dname;
    int dep_location;
    int mgr_no;
} dept_ind;
EXEC SQL END DECLARE SECTION;
```

\< 예제 프로그램 : cursor1.sc \>

```
/* specify path of header file */
EXEC SQL OPTION (INCLUDE=./include);
/* include header file for precompile */
EXEC SQL INCLUDE hostvar.h;

/* declare host variables */
EXEC SQL BEGIN DECLARE SECTION;
/* structure host variables */
department s_department;
/* structure indicator variables */
dept_ind s_dept_ind;
EXEC SQL END DECLARE SECTION;

/* declare cursor */
EXEC SQL DECLARE DEPT_CUR CURSOR FOR 
             SELECT *
             FROM DEPARTMENTS; 
    
/* open cursor */
EXEC SQL OPEN DEPT_CUR;
    
/* fetch cursor in loop */
while(1)
{
    /* use indicator variables to check null value */
    EXEC SQL FETCH DEPT_CUR INTO :s_department :s_dept_ind;
    if (sqlca.sqlcode == SQL_SUCCESS) /* check sqlca.sqlcode */
    {
    printf("%d     %s %s          %d\n", 
              s_department.dno, s_department.dname, 
              s_department.dep_location, 
s_department.mgr_no);
}
else if (sqlca.sqlcode == SQL_NO_DATA)
{
    break;
}
else 
{
    printf("Error : [%d] %s\n", SQLCODE, sqlca.sqlerrm.sqlerrmc);
    break;
}
}

/* close cursor */
EXEC SQL CLOSE DEPT_CUR;
```

#### 실행 시간 에러 처리

-   모든 내장 SQL문 수행 후 반드시 수행 결과를 확인하여야 한다. 내장 SQL문의
    수행 결과는 sqlca.sqlcode에 저장되며 결과에 따라 SQLSTATE, SQLCODE 등의 값을
    참조할 수 있다.

내장 SQL문의 수행 결과를 확인하기 위해 참조할 수 있는 다양한 변수들에 대한
자세한 설명은 7장을 참조하기 바란다.

##### 실행시간 에러처리 관련 주의 사항

다음은 SQLCA, SQLCODE, SQLSTATE와 WHENEVER문 등 실행시간 에러처리와 관련한 주의
사항이다.

-   모든 내장 SQL문 수행 후에는 반드시 sqlca.sqlcode값을 체크하여 에러처리를
    정확히 해주어야 한다.

-   SELECT문에서 출력 호스트 변수의 크기가 대응되는 칼럼 크기보다 작을 경우,
    호스트 변수에는 호스트 변수 크기만큼 데이터가 잘려서 저장되고, 이 때의
    sqlca.sqlcode값은 SQL_SUCCESS_WITH_INFO이다.

-   update, delete 연산 시 영향받은 레코드 개수가 0개이면 이 때의
    sqlca.sqlcode값은 SQL_NO_DATA이다. update, delete 연산 시 영향받은 레코드
    개수 확인 방법은 sqlca.sqlerrd[2]값을 참조하면 되고, 위의 경우 이 값은
    0이다.

-   SQLCODE에는 에러코드가 음수값으로 저장되어 있는 반면 *Error Message
    Reference* 에는 에러코드가 16진수 양수값으로 설명되어 있다. 따라서 *Error
    Message Reference* 참조 시 SQLCODE의 절대값을 16진수로 변환하여 참조하여야
    한다.

-   WHENEVER문의 적용범위는 프로그램의 흐름과는 다르며, 현재 파일내에서만
    유효하다.

-   WHENEVER문은 적용하고자 하는 내장 SQL문 이전에 선언하여야 한다.

-   WHENEVER문은 connection에 독립적이다. 즉, connection이 하나 이상인 파일에서
    WHENEVER문을 선언하면 connection이 다르더라도 해당 범위의 모든 내장 SQL문이
    영향을 받는다.

##### 예제

다음은 내장 SQL문 수행 후 수행 결과를 확인하는 예를 보여준다.

\< 예제 프로그램 : delete.sc \>

```
/* declare host variables */
EXEC SQL BEGIN DECLARE SECTION;
int      s_eno;
short    s_dno;
EXEC SQL END DECLARE SECTION;

s_eno = 5;
s_dno = 1000;

EXEC SQL DELETE FROM EMPLOYEES 
WHERE ENO > :s_eno AND 
DNO > :s_dno AND 
EMP_JOB LIKE 'P%';

/* check sqlca.sqlcode */
if (sqlca.sqlcode == SQL_SUCCESS) 
{
    /* sqlca.sqlerrd[2] holds the 
rows-processed(deleted) count */
    printf("%d rows deleted\n\n", sqlca.sqlerrd[2]);
}
else 
{
    printf("Error : [%d] %s\n\n", 
SQLCODE, sqlca.sqlerrm.sqlerrmc);
}
```

#### 데이터베이스 서버와의 연결 해제

모든 내장 SQL문의 수행이 끝나고 프로그램을 종료하기 전에 데이터베이스 서버와의
연결을 해제한다. 데이터베이스 서버와의 연결 해제 시 이 연결에 할당된 자원들이
모두 해제된다. 데이터베이스 서버와의 연결이 해제된 이후에는 내장 SQL문을 수행할
수 없다.

데이터베이스 서버와의 연결 해제에 대한 자세한 설명은 6장을 참조하기 바란다.

##### 예제

다음은 데이터베이스 서버와의 연결을 해제하는 예를 보여준다.

\< 예제 프로그램 : connect1.sc \>

```
EXEC SQL DISCONNECT;
```

#### Make 방법

precompiler를 이용하여 프로그램을 작성할 경우의 전처리 과정이다

```
apre [<apre – option>] <filename>
```

##### 예제

다음은 connect1.sc 파일을 전처리하는 예를 보여준다.

```
$ apre connect1.sc
```

2.호스트 변수와 지시자 변수
-------------------------

### 호스트 변수 

#### 개요

호스트 변수(host variables)는 호스트 언어로 작성된 애플리케이션과 데이터베이스
서버와의 데이터 교환 역할을 한다. 즉, 테이블의 칼럼값을 호스트 변수에 저장하거나
호스트 변수값을 데이터베이스 테이블의 칼럼에 삽입하는 등의 역할을 한다.

#### 선언 방법

호스트 변수 선언 방법은 다음과 같다.

-   호스트 변수 선언부 또는 함수 인자 선언부에서 선언한다. 만약 호스트 변수
    선언부 또는 함수 인자 선언부에서 선언하지 않은 변수를 내장 SQL문에서 사용할
    경우 전처리 시 “The host variable [variable_name] is unknown.” 오류가
    발생한다.  
    호스트 변수 선언부 또는 함수 인자 선언부에 대한 자세한 설명은 3장을 참조하기
    바란다.

-   호스트 변수 선언 구문은 다음과 같다.  
    datatype variable_name;  
    즉, C 또는 C++ 프로그램에서의 변수 선언 방법과 동일하다.  
    호스트 변수의 데이터 타입에 대한 자세한 설명은 5장을 참조하기 바란다.

-   배열 호스트 변수 선언은 char 타입과 varchar 타입에 대해 2차원 배열 선언이
    가능하고 그 외 타입들은 1차원 배열 선언이 가능하다. 배열 처리 SQL문에 대한
    자세한 설명은 9장을 참고하기 바란다.

-   Altibase가 지원하는 내셔널 캐릭터 타입을 Precompiler에서 처리하기 위해서는
    호스트 변수로 char 타입과 varchar 타입만 사용이 가능하고, 다음과 같은
    예약어를 사용해야 한다.  
    character set [is] nchar_cs  
    그러나 컴파일할 때 명령행에 옵션 nchar_var를 설정하면, 예약어를 사용하지
    않고도 사용할 수 있다.

-   호스트 변수명은 알파벳(a\~z, A\~Z), 밑줄("_"), 또는 달러 기호("\$")로
    시작하여야 하며, 그 길이는 50 bytes로 제한된다.

#### 사용 방법

호스트 변수는 내장 SQL문에서 스칼라 표현식이 허용되는 위치에 사용할 수 있다.

호스트 변수는 내장 SQL문에서 다른 SQL 구성 요소와 구분되어야 하므로 “**:**” 을
접두어로 가진다.

#### 예제

다음 예제는 s_dno, s_dname, s_dep_location 을 호스트 변수로 선언하고 사용하는
예를 보여준다.

\< 예제 프로그램 : select.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
short      s_dno;
char       s_dname[30+1];
char       s_dep_location[9+1];
EXEC SQL END DECLARE SECTION;

EXEC SQL SELECT DNAME, DEP_LOCATION
INTO :s_dname, :s_dep_location
FROM DEPARTMENTS
WHERE DNO = :s_dno;
```

### 호스트 변수 분류

호스트 변수는 데이터베이스 서버에 데이터 입력용으로 사용되는지,
데이터베이스로부터 데이터 출력용으로 사용되는지에 따라 입력 호스트 변수 또는
출력 호스트 변수로 구분된다.

#### 출력 호스트 변수

출력 호스트 변수는 SELECT문과 FETCH문의 INTO절에 사용되는 호스트 변수로 이
호스트 변수에는 질의 결과가 저장된다. ODBC의 SQLBindCol() 함수에 사용하는 변수와
같은 역할을 한다.

##### 예제

다음 예제는 출력 호스트 변수의 사용 예를 보여준다.

여기에서는 s_dname, s_dep_location이 출력 호스트 변수로 사용되었다. 조건에 맞는
레코드의 DNAME, DEP_LOCATION 칼럼값이 각각 호스트 변수 s_dname, s_dep_location에
저장된다.

\< 예제 프로그램 : select.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
short      s_dno;
char       s_dname[30+1];
char       s_dep_location[9+1];
EXEC SQL END DECLARE SECTION;

s_dno = 1001;
EXEC SQL SELECT DNAME, DEP_LOCATION
INTO :s_dname, :s_dep_location
FROM DEPARTMENTS
WHERE DNO = :s_dno;
```

#### 입력 호스트 변수

입력 호스트 변수는 출력 호스트 변수의 경우를 제외한 모든 경우의 호스트 변수로,
주로 SQL문의 입력값을 지정하기 위한 용도로 사용된다. 예를 들어, SELECT문의
WHERE절에 조건값을 지정하거나, INSERT문의 VALUES절에 레코드의 칼럼값을 지정하는
역할을 한다.

입력 호스트 변수는 내장 SQL문에서 스칼라 표현식이 허용되는 위치에 사용된다.
그러나 호스트 변수를 SELECT문의 TARGET절이나 GROUP BY절, ORDER BY절에 사용하기
위해서는 CAST 연산자를 이용하여 그 타입을 명시해야 한다. 단 GROUP BY절에 CAST
연산자를 사용해서 호스트 변수의 타입을 명시한 표현식이 존재하는 경우 해당
표현식을 target 절에서 사용할 수 없다.

Where절에서 호스트 변수의 사용은 가능하다. 그러나 Where절의 join predicate에
호스트 변수가 사용되는 경우, 데이터 타입을 알 수 없어 항상 NL join method를
사용하는 execution plan이 만들어진다. 이런 상황을 피하려면, 호스트 변수를 사용할
때 CAST 연산자를 사용하여 타입이 결정되도록 하면 더 좋은 join method를 선택할 수
있다.

##### 예제

입력 호스트 변수의 다양한 사용 예를 보여준다.

[예제 1] 다음은 INSERT문에서의 입력 호스트 변수의 사용 예이다. 여기에서는 s_gno,
s_gname, s_goods_location, s_stock, s_price가 입력 호스트 변수로 사용되었다.
입력 호스트 변수값이 칼럼값으로 삽입된다.

\< 예제 프로그램 : insert.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
char    s_gno[10+1];
char    s_gname[20+1];
char    s_goods_location[9+1];
int     s_stock;
double  s_price;
EXEC SQL END DECLARE SECTION;

strcpy(s_gno, "F111100002");
strcpy(s_gname, "XX-101");
strcpy(s_goods_location, "FD0003");
s_stock = 5000;
s_price = 9980.21;

EXEC SQL INSERT INTO GOODS 
VALUES (:s_gno, :s_gname, :s_goods_location, 
:s_stock, :s_price);
```

[예제 2] 다음은 UPDATE문에서의 입력 호스트 변수의 사용 예이다. 여기에서는 s_dno,
s_emp_job, s_eno가 입력 호스트 변수로 사용되었다. 조건에 맞는 레코드의 DNO,
EMP_JOB 칼럼값을 각각 s_dno, s_emp_job 값으로 변경한다.

\< 예제 프로그램 : update.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
int      s_eno;
short    s_dno;
varchar  s_emp_job[15+1];
EXEC SQL END DECLARE SECTION;

s_eno = 2;
s_dno = 1001;
strcpy(s_emp_job.arr, "ENGINEER");
s_emp_job.len = strlen(s_emp_job.arr);

EXEC SQL UPDATE EMPLOYEES 
SET DNO = :s_dno,
                          EMP_JOB = :s_emp_job
            WHERE ENO = :s_eno;
```

[예제 3] 다음은 DELETE문에서의 입력 호스트 변수의 사용 예이다. 여기에서는 s_eno,
s_dno가 입력 호스트 변수로 사용되었다. 호스트 변수값을 이용하여 조건에 맞는
레코드를 삭제한다.

\< 예제 프로그램 : delete.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
int      s_eno;
short    s_dno;
EXEC SQL END DECLARE SECTION;

s_eno = 5;
s_dno = 1000;

EXEC SQL DELETE FROM EMPLOYEES 
WHERE ENO > :s_eno AND 
DNO > :s_dno AND 
EMP_JOB LIKE 'P%';
```

[예제 4] 다음은 SELECT문에서의 입력 호스트 변수의 사용 예이다. 여기에서는
s_dno가 입력 호스트 변수로 사용되었다. 입력 호스트 변수 값을 이용하여 조건에
맞는 레코드를 검색한다.

\< 예제 프로그램 : select.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
short      s_dno;
char       s_dname[30+1];
char       s_dep_location[9+1];
EXEC SQL END DECLARE SECTION;

s_dno = 1001;
EXEC SQL SELECT DNAME, DEP_LOCATION
INTO :s_dname, :s_dep_location
FROM DEPARTMENTS
WHERE DNO = :s_dno;
```

[예제 5] 다음은 SELECT문의 target절에서 입력 호스트 변수를 사용하는 예이다.
여기에서는 s_call이 입력 호스트 변수로 사용되었다.

\<예제 프로그램 : host_target.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
double s_call;
EXEC SQL END DECLARE SECTION;

s_call = 0.045;

EXEC SQL SELECT 원금 * ( 1 – CAST( :s_call AS DOUBLE ) ) FROM 계좌;
```

[예제 6] 다음은 SELECT문의 group by절에서 입력 호스트 변수를 사용하는 예이다.
여기에서는 s_period가 입력 호스트 변수로 사용되었다.

\<예제 프로그램 : host_group.sc \>

```
int s_period;
EXEC SQL END DECLARE SECTION;

s_period = 1;    /* 1(월별), 3(분기별), 6(반기별) */

EXEC SQL SELECT SUM(매출) FROM sales 
                 GROUP BY FLOOR( 월 / CAST( :s_period AS INTEGER ) );
```

[예제 7] 다음은 where절의 join predicate에서 입력 호스트 변수를 사용하는 예이다.
여기에서는 s_diff가 입력 호스트 변수로 사용되었다.

\<예제 프로그램 : host_join.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
int s_diff;
EXEC SQL END DECLARE SECTION;

s_diff = 1;

EXEC SQL SELECT * FROM t1, t2
                 WHERE t1.i1 = t2.i1 + CAST( :s_diff AS INTEGER );
```

### 지시자 변수 

#### 개요

테이블의 칼럼값이 NULL인 경우 호스트 언어에서는 이와 같은 NULL을 표현할 수
없으므로 별도의 처리 방법이 필요하다.

C/C++ 전처리에서는 NULL값 처리를 위해 지시자 변수(Indicator Variables)를
지원한다.

지시자 변수란 NULL값 처리를 위해 내장 SQL문에서 호스트 변수와 함께 사용하는
변수이다.

#### 역할

-   지시자 변수는 대응되는 칼럼값이 널(NULL)인지 아닌지 판단하는 근거를
    프로그래머에게 제공한다. 입력 지시자 변수값을 –1(SQL_NULL_DATA)로 지정하면
    대응되는 호스트 변수값을 NULL로 처리한다.  
    출력 지시자 변수값이 –1(SQL_NULL_DATA)인 경우 대응되는 칼럼값이 NULL이
    반환되었음을 의미한다.  
    예를 들어, INSERT문의 특정 호스트 변수값을 NULL로 지정한다든지, SELECT한
    칼럼값이 NULL인지 아닌지 판단하기 위해 지시자 변수를 사용한다.

-   입력값의 길이를 지정하거나 반환된 칼럼값의 길이가 저장된다.  
    호스트 변수의 데이터 타입이 타입이거나 이진 타입일 경우에만 해당된다.  
    입력 지시자 변수에는 입력값의 길이를 지정해준다.  
    출력 지시자 변수에는 반환되는 칼럼값의 길이가 저장된다.  
    호스트 변수가 타입이고 널문자(‘\\0’)로 끝나는 경우, 입력값 또는 반환되는
    칼럼값이 NULL이 아니라면 지시자 변수는 지정하지 않아도 무방하다.  
    호스트 변수가 이진 타입일 경우, 반드시 지시자 변수를 지정하여야 한다.(입력값
    또는 반환되는 칼럼값이 NULL이 아닌 경우에도) 이유는 이진 타입의 경우
    널문자로 끝나지 않을 수 있기 때문에 데이터베이스 서버에서 입력값의 길이를 알
    수 있는 방법이 필요하고, 사용자는 반환되는 칼럼의 길이를 알 수 있는 방법이
    필요하다. 따라서 이 경우 반드시 지시자 변수를 지정하여야 한다. 이진 타입에
    대한 자세한 설명은 5장을 참조하기 바란다.

#### 선언

지시자 변수의 선언 방법은 다음과 같다.

-   호스트 변수 선언부 또는 함수 인자 선언부에서 선언한다. 만약 호스트 변수
    선언부 또는 함수 인자 선언부에서 선언하지 않은 변수를 지시자 변수로 사용할
    경우 전처리 시 “The host variable [variable_name] is unknown.” 오류가
    발생한다. 호스트 변수 선언부 또는 함수 인자 선언부에 대한 자세한 설명은
    3장을 참조하기 바란다.
-   변수 선언 구문은 다음과 같다.  
    datatype indicator_variable_name;  
    datatype은 int 또는 SQLLEN 타입이어야 한다. 또는 int 및 SQLLEN 타입들로만
    구성된 구조체 타입도 가능하다.

-   지시자 변수명은 알파벳(a\~z, A\~Z), 밑줄("_") 또는 달러 기호("\$")로
    시작하여야 하며, 그 길이는 50 bytes로 제한된다.

#### 사용

내장 SQL문에서 지시자 변수 사용 구문은 다음과 같다.

```
<:host_variable> [INDICATOR] <:indicator_variable>
```

여기에서 “INDICATOR” 키워드는 생략 가능하다.

호스트 변수가 구조체가 아니면 지시자 변수도 구조체가 아니어야 하고 호스트 변수가
구조체이면 지시자 변수도 구조체이어야 한다.

#### 지시자 변수를 반드시 지정해야 하는 경우

다음 경우는 반드시 지시자 변수를 지정하여야 한다.

-   입력값을 NULL로 지정할 경우.  
    지시자 변수에 –1(SQL_NULL_DATA)을 지정한다.

-   출력 호스트 변수에 대응되는 칼럼이 NOT NULL 칼럼이 아닌 경우.  
    지시자 변수를 지정하지 않았는데 SELECT 또는 FETCH 한 칼럼값이 NULL인 경우,
    내장 SQL문의 수행 결과(sqlca.sqlcode)는 SQL_SUCCESS_WITH_INFO가 된다.

-   APRE_BINARY, APRE_BINARY2, APRE_BLOB, APRE_BYTES 타입을 입출력 호스트 변수로
    사용하는 경우.  
    이진 타입의 경우 데이터가 널문자로 끝나지 않을 수 있기 때문에 데이터베이스
    서버에 입력값의 길이를 알려줄 방법이 필요하다. 따라서 지시자 변수에 입력값의
    길이를 지정해준다. 마찬가지로 출력 호스트 변수로 사용할 경우 데이터베이스
    서버는 반환되는 칼럼값의 길이를 지시자 변수에 저장한다. APRE_BINARY 타입과
    APRE_BINARY2, APRE_BLOB , APRE_BYTES, APRE_VARBYTES 타입에 대한 자세한 설명은
    5장을 참조하기 바란다.

-   APRE_NIBBLE 타입을 출력 호스트 변수로 사용하는 경우.  
    NIBBLE 타입 컬럽에 NULL값을 입력하거나, NIBBLE 타입 칼럼으로부터 NULL값을
    받아 올 경우 지시자 변수가 필요하다. APRE_NIBBLE 타입에 대한 자세한 설명은
    5장을 참조하기 바란다.

#### 제한 사항

-   호스트 변수가 구조체이면 지시자 변수도 구조체이어야 한다. 이 때, 두 구조체의
    구성 요소 개수도 같아야 한다.

```
예) EXEC SQL BEGIN DECLARE SECTION;
struct tag1 { int i1; int i2; } var1;
struct tag2 { int i1_ind; int i2_ind; } var1_ind1;
struct tag3 { int i1_ind; int i2_ind; 
int i3_ind; } var1_ind2; 
EXEC SQL END DECLARE SECTION;

EXEC SQL INSERT INTO T1(I1, I2) 
VALUES (:var1 :var1_ind1);	(O)
EXEC SQL INSERT INTO T1(I1, I2) 
VALUES (:var1 :var1_ind2);	(X)
```

-   호스트 변수가 구조체의 배열인 경우 지시자 변수는 지정할 수 없다.

```
예) EXEC SQL BEGIN DECLARE SECTION;
struct tag1 { int i1; int i2; char i3[11]; } var1[10];
struct tag2 { int i1_ind; int i2_ind; int i3_ind; } var1_ind1[10];
EXEC SQL END DECLARE SECTION;

EXEC SQL INSERT INTO T1(I1, I2, I3) 
VALUES (:var1 :var1_ind1);	(X)
```

-   호스트 변수가 varchar 타입인 경우, 지시자 변수를 지정하면 지정한 변수를
    지시자 변수로 사용하고, 지정하지 않으면 varchar 타입의 구성 요소인 len
    변수가 자동으로 지시자 변수가 된다. 따라서 이 경우, len 변수를 지시자
    변수처럼 사용하면 된다.

```
예) EXEC SQL BEGIN DECLARE SECTION;
varchar var1;
int var1_ind;
EXEC SQL END DECLARE SECTION;

/* T1테이블의 I1칼럼에 ‘TEST’ 삽입, 
var1.len이 지시자 변수로 사용된 경우 */
strcpy(var1.arr, “TEST”);
var1.len = strlen(var1.arr);
EXEC SQL INSERT INTO T1(I1) 
VALUES (:var1);

/* T1테이블의 I1칼럼에 NULL 삽입,
var1.len이 지시자 변수로 사용된 경우 */
var1.len = -1;
EXEC SQL INSERT INTO T1(I1) 
VALUES (:var1);

/* T1테이블의 I1칼럼에 ‘TEST’ 삽입,
var1_ind를 지시자 변수로 사용한 경우 */
strcpy(var1.arr, “TEST”);
var1_ind = strlen(var1.arr);
EXEC SQL INSERT INTO T1(I1) 
VALUES (:var1 :var1_ind);	
```

#### 예제

다음은 s_goods_location의 지시자 변수로 s_goods_location_ind를, s_price의 지시자
변수로 s_price_ind를 사용하는 예를 보여준다. 두 지시자 변수값 모두
SQL_NULL_DATA를 지정하였으므로 대응되는 칼럼 값에는 NULL이 삽입된다.

\< 예제 프로그램 : indicator.sc \>

```
/* declare host variables */
EXEC SQL BEGIN DECLARE SECTION;
char    s_gno[10+1];
char    s_gname[20+1];
char    s_goods_location[9+1];
int     s_stock;
double  s_price;

/* declare indicator variables */
int      s_goods_location_ind;
int      s_price_ind;
EXEC SQL END DECLARE SECTION;

/* set host variables */
strcpy(s_gno, "X111100002");
strcpy(s_gname, "XX-101");
strcpy(s_goods_location, "FD0003");
s_stock = 5000;
s_price = 9980.21;

/* set indicator variables */
s_goods_location_ind = SQL_NULL_DATA;
s_price_ind          = SQL_NULL_DATA;

EXEC SQL INSERT INTO GOODS 
VALUES (:s_gno, 
:s_gname,
:s_goods_location :s_goods_location_ind,
:s_stock,
:s_price :s_price_ind);
```

### 지시자 변수 분류

지시자 변수는 출력 호스트 변수와 함께 사용되는지, 입력 호스트 변수와 함께
사용되는지에 따라 출력 지시자 변수 또는 입력 지시자 변수로 구분된다.

#### 출력 지시자 변수 

출력 호스트 변수에 대응되는 칼럼이 NOT NULL 칼럼이 아니라면 반드시 지시자 변수와
함께 사용하여야 한다. 이유는 SELECT 또는 FETCH 한 칼럼값이 NULL인 경우 지시자
변수를 지정하지 않으면 내장 SQL문의 수행 결과(sqlca.sqlcode)는 SQL_SUCCESS가
아니라 SQL_SUCCESS_WITH_INFO가 되기 때문이다.

지시자 변수값이 –1 (SQL_NULL_DATA)이라면 대응되는 칼럼값이 NULL이 반환됨을
의미한다. 따라서 이 때 출력 호스트 변수값은 무의미(garbage value)하다. 지시자
변수값이 –1 (SQL_NULL_DATA)이 아니라면 대응되는 칼럼값은 NULL이 아니며 출력
호스트 변수에는 대응되는 칼럼값이 저장된다. 이 경우의 지시자 변수값에 대해서는
다음 절의 “지시자 변수값의 의미” 에서 자세히 다루도록 하겠다.

##### 예제

다음은 출력 지시자 변수의 사용 예를 보여준다.

여기에서는 s_goods의 지시자 변수로 s_good_ind를 사용하였다. s_goods가
구조체이므로 s_good_ind도 구조체로 선언되었으며 두 구조체의 구성 요소 개수는
같다. SELECT문 수행 후 s_good_ind의 구성 요소 각각을 –1 인지 검사한다.

\< 예제 프로그램 : hostvar.h \>

```
EXEC SQL BEGIN DECLARE SECTION;
typedef struct goods
{
    char   gno[10+1];
    char   gname[20+1];
    char   goods_location[9+1];
    int    stock;
    double price;
} goods;

typedef struct good_ind
{
    int gno;
    int gname;
    int goods_location;
    int stock;
    int price;
} good_ind;
EXEC SQL END DECLARE SECTION;
```

\< 예제 프로그램 : indicator.sc \>

```
/* specify path of header file */
EXEC SQL OPTION (INCLUDE=./include);
/* include header file for precompile */
EXEC SQL INCLUDE hostvar.h;

EXEC SQL BEGIN DECLARE SECTION;
goods     s_goods;
good_ind s_good_ind;
EXEC SQL END DECLARE SECTION;

EXEC SQL SELECT * 
INTO :s_goods :s_good_ind 
FROM GOODS 
WHERE GNO = :s_gno;

/* GNO, GNAME은 NOT NULL 칼럼이므로 지시자 변수값 검사 생략 */ 
if (sqlca.sqlcode == SQL_SUCCESS) 
{
        if (s_good_ind.goods_location == SQL_NULL_DATA)
        {
            strcpy(s_goods.goods_location, "NULL");
        }
        if (s_good_ind.stock == SQL_NULL_DATA)
        {
            s_goods.stock = -1;
        }
        if (s_good_ind.price == SQL_NULL_DATA)
        {
            s_goods.price = -1;
        }
}
```

#### 입력 지시자 변수 

입력값으로 NULL을 지정하기 위해서 입력 지시자 변수를 사용한다. 이 때 대응되는
지시자 변수값을 –1 (SQL_NULL_DATA)로 지정한다.

입력값이 NULL이 아닌 경우 지시자 변수는 지정하지 않아도 무방하나 지정할 경우
주의해서 사용하여야 한다. 입력 호스트 변수 타입에 따라 지시자 변수값의 의미가
달라지는데 자세한 내용은 다음 절 “지시자 변수값의 의미” 를 참조하기 바란다.

##### 예제

다음은 입력 지시자 변수의 사용 예를 보여준다.

여기에서는 s_goods_location의 지시자 변수로 s_goods_location_ind, s_price의
지시자 변수로 s_price_ind를 사용하였다. s_goods_location_ind와 s_price_ind에
SQL_NULL_DATA(-1)를 지정함으로써 GOODS_LOCATION, PRICE 칼럼에 각각 NULL을
삽입한다.

\< 예제 프로그램 : indicator.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
/* declare host variables */
char    s_gno[10+1];
char    s_gname[20+1];
char    s_goods_location[9+1];
int     s_stock;
double  s_price;

/* declare indicator variables */
int      s_goods_location_ind;
int      s_price_ind;
EXEC SQL END DECLARE SECTION;

/* set host variables */
strcpy(s_gno, "X111100002");
strcpy(s_gname, "XX-101");
strcpy(s_goods_location, "FD0003");
s_stock = 5000;
s_price = 9980.21;

/* set indicator variables */
s_goods_location_ind = SQL_NULL_DATA;
s_price_ind            = SQL_NULL_DATA;

EXEC SQL INSERT INTO GOODS 
VALUES (:s_gno, 
                   :s_gname, 
                   :s_goods_location :s_goods_location_ind, 
                   :s_stock, 
:s_price :s_price_ind);
```

### 지시자 변수값의 의미

다음 표는 지시자 변수 종류, 지시자 변수값, 호스트 변수 타입에 따른 지시자
변수값의 의미를 설명한다.

지시자 변수값이 –1이면 조건에 상관없이 항상 NULL을 의미하지만 –1이 아닐 경우
지시자 변수 종류, 호스트 변수 타입 등의 조건에 따라 지시자 변수값의 의미가
달라지므로 다음 표를 잘 이해하여 지시자 변수 사용에 참고하도록 한다.

특히, 입력 지시자 변수의 경우 프로그램 작성자가 값을 지정하고 지정한 값을
전처리기 또는 데이터베이스 서버가 내부적으로 사용하므로 정확한 값 지정을 하여야
한다.

<table>
    <tr>
    	<th>지시자
변수 종류
</th>
		<th colspan="2">입력 지시자 변수</th>
		<th colspan="2">출력 지시자 변수</th>	
    </tr>
    <tr>
    	<td><img src="media/Precompiler/diagonal.png" width="150px" height="100px"/></td>
    	<td>-1</td>
    	<td>-1 이외의 값</td>
    	<td>-1</td>
    	<td>-1 이외의 값</td>
    </tr>
    <tr>
    	<td>숫자형 타입</td>
    	<td rowspan="8">입력값이 NULL임을 의미함.</td>
    	<td>내부적으로 참조하지 않음. 의미 없음</td>
    	<td rowspan="8">반환된 값이 NULL임을 의미함.
실제 호스트 변수값은 의미가 없음.
(garbage value)
</td>
		<td>호스트 변수의 크기(sizeof)가 저장되어 있음.</td>
    </tr>
    <tr>
    	<td>문자형 타입</td>
    	<td>입력값의 길이(strlen)를 지정해야 함.</td>
    	<td>반환된 값의 길이(strlen)가 저장되어 있음.</td>   	
    </tr>
    <tr>
    	<td>날짜형 타입</td>
    	<td>내부적으로 참조하지 않음. 의미 없음.</td>
    	<td>호스트 변수의 크기(sizeof)가 저장되어 있음.</td>
    </tr>
    <tr>
    	<td>APRE_BINARY</td>
    	<td>입력값의 길이(bytes)를 지정해야 함.</td>
    	<td>반환된 값의 길이(bytes)가 저장되어 있음.</td>
    </tr>
    <tr>
    	<td>APRE_BINARY2</td>
    	<td>입력값의 길이(bytes)를 지정해야 함.</td>
    	<td>반환된 값의 길이(bytes)가 저장되어 있음.</td>
    </tr>
    <tr>
    	<td>APRE_BLOB</td>
    	<td>입력값의 길이(bytes)를 지정해야 함</td>
    	<td>반환된 값의 길이(bytes)가 저장되어 있음.</td>
    </tr>
    <tr>
    	<td>APRE_CLOB</td>
    	<td>입력값의 길이(bytes)를 지정해야 함</td>
    	<td>반환된 값의 길이(bytes)가 저장되어 있음.</td>
    </tr>
    <tr>
    	<td>APRE_BYTES</td>
    	<td>입력값의 길이(bytes)를 지정해야 함.</td>
    	<td>반환된 값의 길이(bytes)가 저장되어 있음.</td>
    </tr>
    <tr>
    	<td>APRE_NIBBLE</td>
    	<td>내부적으로 참조하지 않음. 의미 없음.</td>
    	<td>반환된 값의 길이(bytes)가 저장되어 있음.</td>
    </tr>
<table>

일반적으로 지시자 변수는 NULL 처리를 위해 사용하지만, 위 표에서 보는 바와 같이
입력 지시자 변수에서 그 값이 –1이 아니어도 내부적으로 참조해서 사용하는 경우가
있다. 따라서 입력 지시자 변수를 사용할 경우 NULL이 아닌 경우도 그 값을 정확히
지정해야 한다.

입력 지시자 변수값이 –1이 아닌 경우, 호스트 변수 타입이 이나 이진 타입이면
데이터베이스 서버에서는 지시자 변수값을 입력값의 길이로 인식하고 그 길이만큼
입력값으로 처리한다.

### 예제 프로그램

##### indicator.sc 

$ALTIBASE_HOME/sample/APRE/indicator.sc 참고

##### 실행결과

```
$ is –f schema/schema.sql
$ make indicator
$ ./indicator
<INDICATOR VARIABLES>
-----------------------------------------------------------
[Scalar Indicator Variables]                                      
-----------------------------------------------------------
Success insert

-----------------------------------------------------------
[Structure Indicator Variables]                                   
-----------------------------------------------------------
GNO        GNAME                GOODS_LOCATION  STOCK  PRICE      
-----------------------------------------------------------
X111100002 XX-101               NULL            5000   -1.00

-----------------------------------------------------------
 [Scalar Array Indicator Variables]                                
-----------------------------------------------------------
3 rows updated
3 times update success

-----------------------------------------------------------
 [Arrays In Structure]                                             
-----------------------------------------------------------
3 rows inserted
3 times inserte success

-----------------------------------------------------------
 [Indicator Variable(.len) of VARCHAR With Output Host Variables]  
-----------------------------------------------------------
v_address.arr = [Pusan University]
v_address.len = 16

-----------------------------------------------------------
 [Indicator Variable(.len) of VARCHAR With Input Host Variables]   
-----------------------------------------------------------
Success update

-----------------------------------------------------------
 [Indicator Variable of DATE Type With Input Host Variables]       
-----------------------------------------------------------
Success update

-----------------------------------------------------------
 [Indicator Variable of DATE Type With Output Host Variables]      
-----------------------------------------------------------
d_arrival_date2 = NULL
```

3.호스트 변수 선언부
------------------

### 호스트 변수 선언부

호스트 변수의 이름, 타입, 길이 등의 정보는 전처리 과정에서 중요한 정보이다.
따라서, 사용될 호스트 변수는 C/C++ 전처리기가 인식할 수 있는 구문으로 표기되어야
하며, 이것은 호스트 변수 선언부에서 이루어진다.

호스트 변수 선언부에서는 프로그램에서 사용할 호스트 변수를 선언한다.

#### 구문

호스트 변수 선언부는 다음의 구문으로 지원한다.

```
EXEC SQL BEGIN DECLARE SECTION;
/* variable_declarations */
EXEC SQL END DECLARE SECTION;
```

이 구문의 호스트 변수 선언부는 “EXEC SQL BEGIN DECLARE SECTION;” 문장으로
시작되며, “EXEC SQL END DECLARE SECTION;” 문장으로 끝난다. 프로그램에서 사용할
호스트 변수는 이 두 문장 사이에 선언되어야 한다.

호스트 변수 선언부는 전처리할 파일(.sc)과 전처리에서 사용하는 헤더파일(.h) 내에
위치할 수 있다.

하지만, \#include로 포함된 헤더파일(.h) 내에는 호스트 변수 선언부가 올 수
없으므로, 호스트 변수 선언부 없이 호스트 변수를 선언하고 -parse 명령행 옵션을
full로 설정하여 precompile하면 된다. EXEC SQL INCLUDE로 포함된 헤더파일(.h)의
경우에는 호스트 변수 선언부를 헤더 파일 내에 사용할 수 있다.

그 이유는 \#include로 포함된 헤더파일(.h)은 전처리할 파일(.sc)에서만 참조하는
것이 아니라 내장 SQL이 포함되지 않은 C(.c) 또는 C++(.cpp) 소스 파일에서도 참조할
수가 있는데, 이 때 컴파일 오류가 발생하기 때문이다. 자세한 내용은 4장의
"\#include 제약"을 참고하기 바란다.

#### 변수 선언 범위(Scope)

호스트 변수 선언부는 전역 또는 지역에 위치할 수 있다. 변수 선언 범위는 C/C++과
유사하며, 같은 이름의 변수가 다른 범위에서 중첩되어 선언되면, 가장 가까운
범위에서 선언된 변수가 상위 범위의 변수 선언에 우선한다(overriding).

이러한 중첩은 최대 50단계까지 허용된다.

##### 예제

다음은 다른 범위에서 같은 이름의 변수를 선언하여 사용하는 예를 보여준다.
myfunc() 함수 안에서는 지역으로 선언된 name(\#2)이 전역 변수인 name(\#1)보다
우선 순위가 높으므로 이후의 name(\#3)은 지역 변수를 참조한다.

```
EXEC SQL BEGIN DECLARE SECTION;	
char name[20];			<- #1
EXEC SQL END DECLARE SECTION;	

int myfunc(void)
{
EXEC SQL BEGIN DECLARE SECTION;	
char name[20];			<- #2
EXEC SQL END DECLARE SECTION;	

EXEC SQL INSERT INTO T1 VALUES (:name);		<- #3
}
```

#### 예제

다음은 다양한 호스트 변수 선언 예를 보여준다.

```
EXEC SQL BEGIN DECLARE SECTION;	<- #1
int x, y, z;	<- #2
char c1[50], c2[100]; 		<- #3
varchar v1[50]; 		<- #4
struct tag1 
{	
int  x;
char  y[50];
varchar  z[50];
} st1;            		<- #5
struct tag1 st2; 		<- #6
EXEC SQL END DECLARE SECTION; 	<- #7
```

\#1 : 호스트 변수 선언부의 시작을 표시한다.

\#2 : int 타입의 변수 x, y, z를 호스트 변수로 선언한다.

\#3 : char 타입의 변수 c1, c2를 각각 50, 100 바이트 크기로 선언한다.

\#4 : varchar 타입의 변수 v1를 50 바이트 크기로 선언한다.

\#5 : tag1구조체 타입의 변수 st1을 선언하고, 태그이름을 tag1으로 정의한다.

\#6 : tag1 구조체 타입의 변수 st2를 선언한다.

\#7 : 호스트 변수 선언부의 끝을 표시한다.

### 자료형 정의 

내장 SQL문에는 내장 SQL문이 지원하는 자료형 외에 사용자가 typedef문을 이용하여
정의한 자료형을 호스트 변수의 자료형으로 사용할 수 있다.

#### 설명

호스트 변수의 자료형으로 사용될 자료형 정의(typedef)는 전처리기가 인식할 수 있는
구문으로 표기되어야 하며, 자료형 정의(typedef)의 위치는 호스트 변수 선언부로
제한된다. 자료형 정의(typedef)된 새로운 자료형은 다른 자료형과 함께 호스트
변수의 자료형으로 사용할 수 있다.

#### 예제

자료형 정의의 다양한 예를 보여준다.

[예제 1] 다음은 자료형 정의(typedef)의 사용 예를 보여준다.

```
EXEC SQL BEGIN DECLARE SECTION;	
typdef unsigned int UINT;
typdef unsigned char UCHAR;
EXEC SQL END DECLARE SECTION; 
```

[예제 2] 다음은 구조체 자료형 정의의 다양한 예를 보여준다.

(1) 구조체 정의 후 자료형 정의

```
EXEC SQL BEGIN DECLARE SECTION;	
struct department
{
    short dno;
    char  dname[30+1];
    char  dep_location[9+1];
    int   mgr_no;
};
typedef struct department department;
EXEC SQL END DECLARE SECTION; 
```

(2) 구조체 정의와 자료형 정의를 동시에

```
EXEC SQL BEGIN DECLARE SECTION;	
typedef struct department
{
    short dno;
    char  dname[30+1];
    char  dep_location[9+1];
    int   mgr_no;
} department;
EXEC SQL END DECLARE SECTION; 	
```

(3) 자료형 정의 후 구조체 정의

```
EXEC SQL BEGIN DECLARE SECTION;	
typedef struct department department;
struct department
{
    short dno;
    char  dname[30+1];
    char  dep_location[9+1];
    int   mgr_no;
};
EXEC SQL END DECLARE SECTION; 	
```

### 함수 인자 선언부

함수의 인자를 호스트 변수로 사용할 경우 C/C++ 전처리기에게 함수 인자에 대한
정보를 제공해 줄 방법이 필요하다. 함수 인자 선언부가 함수 인자에 대한 정보를
C/C++ 전처리기에게 알려주는 역할을 한다.

#### 구문

함수 인자 선언부의 구문은 다음과 같다.

```
EXEC SQL BEGIN ARGUMENT SECTION;
/* 호스트 변수로 사용할 함수 인자를 선언 */
EXEC SQL END ARGUMENT SECTION;
```

함수 인자 선언부는 “EXEC SQL BEGIN ARGUMENT SECTION;” 문장으로 시작되며, “EXEC
SQL END ARGUMENT SECTION;” 문장으로 끝난다. 호스트 변수로 사용할 함수 인자들은
이 두 문장 사이에 선언하어야 한다.

함수 인자 선언 시 함수 정의 시와 똑같이(같은 이름, 같은 타입) 선언해 주어야
한다.

#### 설명

함수 인자 선언부는 전처리 할 소스 파일(.sc)내에 있는 함수 안에만 위치할 수 있다.

호스트 변수 선언부의 제한 사항이 함수 인자 선언부에도 그대로 적용된다.

#### 예제 프로그램

##### argument.sc

$ALTIBASE_HOME/sample/APRE/argument.sc  참고

##### 실행결과

```
$ is –f schema/schema.sql
$ make argument
$ ./argument
         <ARGUMENT> 
```

4.C Preprocessor
--------------

### C Preprocessor 개요

APRE\*C/C++ 은 대부분의 C preprocessor 명령들(source file inclusion (\#include),
macro definitions (\#define), and conditional inclusion (\#if))들을 처리한다.

#### C Preprocessor의 수행

APRE\*C/C++ preprocessor는 대부분의 C preprocessor 명령들을 인지하여 효과적으로
매크로를 치환한다. 또한 파일 include, 조건적인 소스코드 포함 또는 배제도
수행한다. APRE\*C/C++ preprocessor 는 preprocess단계에서 얻어진 매크로 값들을
가지고 precompile을 수행하며, 소스파일(\*.sc)을 변환하여 출력파일(\*.c/cpp)을
생성한다.

##### 예제

다음은 APRE\*C/C++ preprocessor처리 예이다.

```
#include “my_header.h”
...
#if A
char name[10];
#endif
...
```

my_header.h 파일이 현재 디렉터리에 있으며 코드는 아래와 같다.

```
#define A 1
```

위 예제에서 APRE\*C/C++ preprocessor는 먼저 my_header.h를 읽어 A라는 정의된 값을
기억하며, \#if 가 처리될 때 A를 1로 치환하여 조건문을 처리하게 된다. 조건이
참이므로 변수 name 선언부분은 소스파일에 포함되게 된다. 만약 거짓이라면 변환된
소스파일에서 배제된다.

### C Preprocessor 구문

APRE\*C/C++ preprocessor 에서 지원하는 C Preprocessor 구문은 \#define, \#undef,
\#include, \#if, \#ifdef, \#ifndef, \#else, \#elif, \#endif등이 있다.

#### \#define, \#undef

APRE\*C/C++ preprocessor에서 사용될 매크로 이름을 정의 또는 해제한다.

##### 예제

```
...
#define A
#define func()
...
#undef A
#undef func
```

위의 예제에서 APRE\*C/C++ preprocessor는 \#define구문을 처리하여 A와 func이라는
이름을 심볼테이블에 저장한다. 그러면 다음에 해당 이름이 사용될 때 매크로가
확장된다. 마지막으로 \#undef를 만나면 저장된 이름을 심볼테이블에서 제거한다.

#### \#include

APRE\*C/C++ preprocessor에 포함될 외부 소스 파일을 읽어 들여 그 파일 안에 define
매크로나 변수들을 읽어온다. 자세한 내용은 C Processor 개요의 예제를 참고한다.

\#include 에 포함되는 파일은 –parse 명령행 옵션에 따라 처리 범위가 달라진다.

#### \#if

조건절을 확장한 후 계산하여 다음에 위치한 소스 코드를 전처리할 것인지의 여부를
결정한다.

##### 예제

```
#define A 1 + 1
#define B A - 2
...
#if B
int var;
#endif
...
#if defined(A)
int var2;
#endif
```

위 예제에서 APRE\*C/C++ preprocessor가 첫 \#if를 처리하기 위해 B를 A-2로
확장하고 A는 1+1로 확장하여 결과적으로 1+1-2를 계산하여 결과값 0을 얻는다.
따라서 첫 \#if에서부터 \#endif까지의 소스 코드는 제거된다. 두번째 \#if문은
\#ifdef와 같은 기능을 하는 defined또한 처리됨을 보여준다.

#### \#ifdef

다음에 오는 이름이 define된 이름인지 확인한 후 소스 코드를 전처리할 지의 여부를
결정한다.

##### 예제

```
#define A
#ifdef A
int var;
#endif
...
```

위의 예제에서 A가 define되어 있으므로 int var;는 전처리(precompile)시 포함된다.

#### \#ifndef

\#ifdef의 반대 조건을 가지고 있으며 define된 이름이 없을 경우 다음에 위치한
소스코드를 전처리 한다.

##### 예제

```
#define A
#ifndef A
int var;
#endif
...
```

A가 define되어 있으므로 int var;는 전처리시 배제된다.

#### \#else

\#if, \#ifdef, \#ifndef 조건절이 모두 거짓일 경우 마지막 \#else 다음에 오는 소스
코드를 전처리 한다.

##### 예제

```
...
#define A 0
#if A
int var1;
#else
int var2;
#endif
...
```

위의 예제에서 \#if조건절이 거짓이므로 \#else부터 \#endif까지의 소스코드를
전처리한다.

#### \#elif

앞선 \#if, \#ifdef, \#ifndef 조건절이 거짓일경우 \#elif 조건절을 확장한 뒤
계산하여 다음에 위치한 소스 코드를 전처리할 지의 여부를 결정한다.

##### 예제

```
...
#define A 0
#define B 1
#if A
int var1;
#elif B
int var2;
#else
int var3;
#endif
...
```

\#if조건절이 거짓이고 \#elif 조건절이 참이므로 \#elif부터 \#endif까지의
소스코드를 전처리한다.

#### \#endif

\#if, \#ifdef, \#ifndef 구문들의 마지막에 위치한다.

### Preprocessor 제약사항

APRE\*C/C++ Preprocessor에서 처리되지 않는 구문들과 몇몇 제약사항들에 대해
설명한다.

#### 무시되는 구문

몇몇 C Preprocessor 구문들은 APRE\*C/C++ Preprocessor 에서 무시된다. 이들은
전처리(precompile)시 필요하지 않는 구문들이다. 예를 들어 \#pragma 는 C
컴파일러에서 사용되는 구문이므로 전처리시에는 처리될 필요가 없다. 전처리시
무시되는 구문들은 아래와 같다.

##### \#

Preprocessor 매크로 인자를 스트링 상수로 바꿔주는 구문이다.

##### \#\#

매크로 정의시 두 preprocessor 토큰들을 합쳐주는 구문이다.

##### \#error

컴파일 타임 에러 메세지를 생성해주는 구문이다.

##### \#pragma

C컴파일러에게 부가적인 정보를 넘겨줄 때 사용되는 구문이다.

##### \#line

C 컴파일러에게 라인 넘버에 대한 정보를 알려줄 때 사용되는 구문이다.

#### \#define 제약

APRE\*C/C++ 에서 \#define를 사용하는데 있어 다음과 같은 제약이 존재한다. SQL
구문 안에서는 define된 이름이 확장되지 않는다. 따라서 SQL 구문 안에 define된
이름을 매크로의 용도로 사용하면 안 된다.

##### 예제

```
#define RESEARCH_DEPT   40
...
EXEC SQL SELECT empno, sal
    INTO :emp_number, :salary /* host arrays */
    FROM emp
    WHERE deptno = RESEARCH_DEPT;  /* INVALID! */
```

위의 예제에서 where절의 RESEARCH_DEPT는 40으로 확장되지 않기 때문에 에러가
발생될 것이다.

#### \#if 제약

\#if의 조건절에 매크로 함수가 올 경우 의도하지 않는 결과를 얻을 수 있다. 되도록
사용하지 않기를 권장한다.

##### 예제

```
#define fun(X,Y) X-Y
...
#if fun(1,1)
int var;
#else
int var2;
#endif
...
```

#### \#include 제약

APRE\*C/C++ Preprocessor는 \#include에 의해 포함된 헤더파일 안에 내장SQL구문이
포함되어 있을 경우에 에러를 발생한다. 또한 VARCHAR 선언도 포함되어서는 안 된다.
내장 SQL 구문이나 VARCHAR 선언이 포함된 헤더파일을 포함하고자 한다면 EXEC SQL
INCLUDE 구문을 이용해야 한다.

EXEC SQL INCLUDE 를 사용하면 전처리기는 해당 헤더파일을 출력될
소스코드(.c/.cpp)파일 안에 포함시킨다. 따라서 VARCHAR선언이나 내장 SQL구문들이
헤더 파일에 포함되어도 상관없다. 하지만 \#include를 사용하면 전처리기는 그
헤더파일내의 매크로 명령 부분이나 C 변수 선언부만 처리하게 된다.

### Preprocessor 예제

\#define과 \#ifdef를 이용해 선택적으로 삽입하는 간단한 예제를 살펴보겠다.
Altibase가 define되어 있으면 호스트 변수 s_goods_alti를 삽입하고 그 외의
경우에는 s_goods_ora를 삽입한다.

##### 예제

< 예제 프로그램 : macro.sc > 

```
/*********************************************************

 * SAMPLE : MACRO

 *          1. Using #define, #if, #ifdef 

 *********************************************************/



/* specify path of header file */

EXEC SQL OPTION (INCLUDE=./include);

/* include header file for precompile */

EXEC SQL INCLUDE hostvar.h;



/* define Altibase */

#define Altibase



int main()

{

    /* declare host variables */

    char usr[10];

    char pwd[10];

    char conn_opt[1024];



    /* structure type */

#ifdef Altibase

    goods   s_goods_alti;

#else

    goods   s_goods_ora;

#endif



    int i;



    printf("<INSERT>\n");



    /* set username */

    strcpy(usr, "SYS");

    /* set password */

    strcpy(pwd, "MANAGER");

    /* set various options */

    strcpy(conn_opt, "DSN=127.0.0.1;CONNTYPE=1"); /* PORT_NO=20300 */



    /* connect to altibase server */

    EXEC SQL CONNECT :usr IDENTIFIED BY :pwd USING :conn_opt;  

    /* check sqlca.sqlcode */

    if (sqlca.sqlcode != SQL_SUCCESS) 

    {

        printf("Error : [%d] %s\n\n", SQLCODE, sqlca.sqlerrm.sqlerrmc);

        exit(1);

    }



    /* use structure host variables */



#ifdef Altibase

    strcpy(s_goods_alti.gno, "F111100010");

    strcpy(s_goods_alti.gname, "Altibase");

    strcpy(s_goods_alti.goods_location, "AD0010");

    s_goods_alti.stock = 9999;

    s_goods_alti.price = 99999.99;

#else

    strcpy(s_goods_ora.gno, "F111100011");

    strcpy(s_goods_ora.gname, "ORACLE");

    strcpy(s_goods_ora.goods_location, "AD0011");

    s_goods_ora.stock = 0001;

    s_goods_ora.price = 00000.01;

#endif



    /* the select insertion useing #ifdef. */



EXEC SQL INSERT INTO GOODS VALUES (

#ifdef Altibase

:s_goods_alti

#else

:s_goods_ora

#endif

);



    printf("------------------------------------------------------------------\n");

    printf("[Structure Host Variables]                                        \n");

    printf("------------------------------------------------------------------\n");



    /* check sqlca.sqlcode */

    if (sqlca.sqlcode == SQL_SUCCESS) 

    {

        /* sqlca.sqlerrd[2] holds the rows-processed(inserted) count */

        printf("%d rows inserted\n\n", sqlca.sqlerrd[2]);

    }

    else 

    {

        printf("Error : [%d] %s\n\n", SQLCODE, sqlca.sqlerrm.sqlerrmc);

    }



    /* disconnect */

    EXEC SQL DISCONNECT;

    /* check sqlca.sqlcode */

    if(sqlca.sqlcode != SQL_SUCCESS) 

    {

        printf("Error : [%d] %s\n\n", SQLCODE, sqlca.sqlerrm.sqlerrmc);

    }

}
```

### ALTIBASE_APRE 매크로

APRE\*C/C++ 는 ALTIBASE_APRE라는 매크로를 미리 정의하고 있는데, 이는 소스 코드의
특정 부분을 전처리(precompile)할지의 여부를 결정할 때 사용될 수 있다. 전처리 시
필요하지 않는 아주 큰 헤더파일이 include되어 있을 경우 유용하다.

아래 예제는 header.h파일을 전처리하지 않도록 하는 ALTIBASE_APRE 매크로의 예이다.

##### 예제

```
#ifndef ALTIBASE_APRE
#include <header.h>
#endif
```

ALTIBASE_APRE 는 전처리 중에 정의되어 있기 때문에, header.h 파일은 읽혀지지 않을
것이다. 하지만 전처리를 마친 후, 외부 컴파일러 (C/C++ compiler)는
ALTIBASE_APRE가 정의 되어 있다는 것을 알지 못하므로 header.h파일을 포함하여
컴파일 할 것이다.

ALTIBASE_APRE 매크로는 preprocessor 구문인 \#ifdef 혹은 \#ifndef에서 사용될 수
있다.

> ### 주의 사항
>
> APRE\*C/C++ Preprocessor에 의해 전처리시 주의해야 할 사항에 대해 살펴본다.
>

#### defined 매크로

C 컴파일러의 명령행 옵션을 이용하여 매크로를 정의할 것이라면, 대부분의 경우
APRE\*C/C++사용할 때도 -D 옵션을 이용하여 매크로를 정의 해야 한다. 예를 들어 C
컴파일러로 아래와 같이 컴파일 명령을 내릴 것이라면,

```
cc -DDEBUG ...
```

컴파일전, APRE\*C/C++ 실행 시에도 아래와 같이 매크로를 정의해야 한다.

```
apre -DDEBUG ...
```

#### include 경로

전처리 중 사용되는 include 파일들에 대한 위치는 모두 -I 옵션에 의해 지정되어
있어야 한다. 예를 들어 /home/project/include 위치에 있는 헤더파일을 참조 하고자
할 때 APRE\*C/C++ 전처리, C 컴파일 시, 모두 아래처럼 include 경로를 지정해 줘야
한다.

```
apre -I/home/project/include test.sc
cc -I/home/project/include ... test.c
```

5.호스트 변수 데이터 타입
-----------------------

### 개요

호스트 변수는 용도와 기능, 선언 방법 등에서 C 또는 C++ 프로그램에서의 일반
변수와 구분된다. 따라서 호스트 변수의 데이터 타입 또한 일반 변수의 데이터 타입과
차이가 있다. 본 장에서는 다음의 내용들에 대해서 설명한다.

-   호스트 변수의 데이터 타입으로 사용할 수 있는 데이터 타입

-   내장 SQL문이 제공하는 확장된 데이터 타입

-   칼럼 타입과 호스트 변수 타입과의 관계

#### 용어 설명

여기에서는 본 장에서 사용될 몇 가지 용어에 대하여 설명한다. 앞으로 사용될
용어들의 의미를 정확히 이해하여 본 장의 내용을 이해하는데 도움이 되길 바란다.

##### 호스트 변수

호스트 변수는 호스트 변수 선언부에 선언하고 내장 SQL문에서 사용하는 변수를
말한다.

##### 일반 변수

C 또는 C++ 프로그램에서 선언되고 사용되는 모든 변수를 말한다. 본 장에서는
개발자의 이해를 돕기 위해 호스트 변수와의 비교 대상으로 사용된다.

##### 호스트 변수 타입(또는 호스트 변수 데이터 타입)

호스트 변수 타입은 호스트 변수의 데이터 타입으로, C 또는 C++에서 사용되는
대부분의 데이터 타입과 내장 SQL문에서 제공하는 확장된 데이터 타입 등을 포함한다.

##### 일반 변수 타입(또는 일반 변수 데이터 타입)

일반 변수 타입은 C 또는 C++ 프로그램에서 사용하는 데이터 타입으로 본 장에서는
개발자의 이해를 돕기 위해 호스트 변수 타입과의 비교 대상으로 사용된다.

##### 칼럼 타입

칼럼 타입은 데이터베이스 서버의 테이블에 정의된 칼럼의 데이터 타입으로, 호스트
변수의 데이터 타입 결정 시 대응되는 칼럼 타입을 고려하여 호환 가능한 데이터
타입을 사용하여야 한다.

#### 호스트 변수 데이터 타입

다음은 호스트 변수의 데이터 타입으로 사용할 수 있는 데이터 타입들이다.

-   C 또는 C++에서 사용하는 대부분의 데이터 타입

-   내장 SQL문이 제공하는 확장된 데이터 타입

-   호스트 변수 선언부에서 타입 선언된 데이터 타입

### 일반 데이터 타입

호스트 변수의 데이터 타입으로 C 또는 C++에서 지원하는 대부분의 데이터 타입을
사용할 수 있다. 여기에서는 호스트 변수의 데이터 타입으로 사용 가능한 일반 데이터
타입들에 대해 설명한다.

#### 숫자형 타입

다음은 호스트 변수의 데이터 타입으로 사용 가능한 숫자형 타입들이다.

##### 정수 타입

int, short int, long int, short, long, long long, unsigned int, unsigned short
int, unsigned long int, unsigned short, unsigned long, unsigned long long

##### 실수 타입

float, double

##### 제한 사항

long double 타입은 지원하지 않는다. 따라서 호스트 변수의 데이터 타입으로 long
double 타입은 사용할 수 없다.

####  문자형 타입

다음은 호스트 변수의 데이터 타입으로 사용 가능한 타입들이다.

##### 문자 타입

char, unsigned char

> ##### 주의 사항
>
> 이 타입을 출력 호스트 변수로 사용할 경우 대응되는 칼럼 타입이 CHAR 타입이라면
> 호스트 변수는 칼럼 크기보다 1 크게 선언하여야 한다. 이유는 CHAR 타입(칼럼
> 타입)은 고정 길이이므로 칼럼 길이만큼 데이터가 반환되는데, 호스트 변수에는 이
> 데이터와 함께 마지막에 널문자를 붙여서 저장해야 하기 때문이다. 만약 1 크게
> 선언하지 않았다면, SELECT문이나 FETCH문 수행 후 sqlca.sqlcode 값은 SQL_SUCCESS가
> 아니라 SQL_SUCCESS_WITH_INFO 이 될 것이다.
>
> 일반적으로 칼럼의 대응되는 호스트 변수를 입출력 호스트 변수 각각 따로 선언하지
> 않고 하나의 호스트 변수를 사용하는 경우가 많기 때문에, 이 타입을 호스트 변수로
> 선언할 경우 대응되는 칼럼 크기보다 1 크게 선언하기를 추천한다.

#### 포인터 타입

호스트 변수로 사용 가능한 대부분의 데이터 타입은 포인터의 베이스 타입으로 사용할
수 있다.

##### char\*

char\*를 호스트 변수의 데이터 타입으로 사용할 수 있다.

함수 인자를 호스트 변수로 사용할 경우 char\*를 사용하면 편리하다. 함수 인자의
호스트 변수 사용에 대한 자세한 설명은 3장을 참조하기 바란다.

##### MAX_CHAR_PTR

Character string을 가리키는 포인터를 호스트 변수로 사용할 경우, APRE전처리기는
포인터가 참조하는 스크링의 최대 사이즈를 65000이라고 가정한다. 이것은 APRE가
실제로 할당된 크기를 알 수가 없기 때문이다. 그러므로 MAX_CHAR_PTR 매크로에
정의된 사이즈보다 더 작은 사이즈가 할당된 char\* type 을 출력 호스트 변수로
사용할 경우, 그 사이즈보다 큰 사이즈의 값이 저장되어 메모리 오류가 발생할 수도
있다.

만약 65000보다 더 크게 선언해야 한다면 char\* 타입의 호스트 변수를 내장
SQL문에서 사용하기 전에 MAX_CHAR_PTR 매크로를 원하는 크기로 재정의하면 된다.

MAX_CHAR_PTR매크로를 정의하는 방법은 다음과 같다.

```
#define MAX_CHAR_PTR 90000
```

MAX_CHAR_PTR 매크로를 정의한 후에, 정의된 크기만큼 char\*의 호스트 변수를
선언하거나 메모리를 할당하여 사용할 수 있다.

##### 구조체 포인터

구조체의 포인터를 호스트 변수의 데이터 타입으로 사용할 수 있다. 함수의 인자를
호스트 변수로 사용할 경우 구조체의 포인터 타입을 사용하면 편리하며, 함수 인자의
호스트 변수 사용에 대한 자세한 설명은 3장을 참조한다.

포인터로 선언한 후에는 반드시 적절한 메모리 할당을 받아야 한다. 메모리 할당이
되었는지 여부는 APRE 전처리기가 알 수 없으므로 주의해야 한다.

##### 배열 포인터

1차원 배열을 포인터 타입의 변수에 대입해서 INSERT내장 문의 입력 호스트 변수로
사용할 때, FOR 구문을 사용해서 배열 요소의 크기를 지정해야 한다.

단, 아래에 나열한 타입은 1차원 배열을 가리키는 포인터를 INSERT내장 문에서 FOR
구문과 함께 사용하거나, 2차원 배열을 가리키는 포인터를 호스트 변수로 사용할 때
원하지 않는 결과를 초래하게 된다.

char, varchar, APRE_BINARY, APRE_BINARY2, APRE_BYTES, APRE_NIBBLE,
APRE_NUMERIC, APRE_BLOB, APRE_CLOB, APRE_BIT, APRE_VARBYTES

아래는 int타입의 배열과 포인터 변수를 INSERT 내장 문에서 입력 호스트 변수로
사용하는 예제이다.

```
int sInt[10];
int *sIntptr;
sIntptr = sInt;

EXEC SQL FOR 10 INSERT INTO T2 VALUES ( :sIntptr );
```

FOR 구문에 대한 자세한 설명은 9장을 참조하기 바란다.

또한 아래와 같이 2차원 배열 포인터를 호스트 변수로 사용할 경우 정상적으로
동작하지 않을 수 있다.

```
int sInt[2][10];
int (*sIntptr)[10];
sIntptr = sInt;
EXEC SQL FOR 10 INSERT INTO T2 VALUES ( :sIntptr );
```

##### 예제

[예제 1] 다음은 char\* 타입인 v_ename을 입력 호스트 변수로 사용하는 예를
보여준다.

\< 예제 프로그램 : argument.sc \>

```
void ins_employee(int v_eno, char* v_ename, short v_dno)
{
EXEC SQL BEGIN ARGUMENT SECTION;
    int    v_eno;
    char*  v_ename;
    short  v_dno;
    EXEC SQL END ARGUMENT SECTION;

    EXEC SQL INSERT INTO TODAY_EMPLOYEE 
VALUES (:v_eno, :v_ename, :v_dno);
}
```

[예제 2] 다음은 MAX_CHAR_PTR를 정의하는 예를 보여준다.

```
#define MAX_CHAR_PTR 90000
EXEC SQL BEGIN DECLARE SECTION;
char* var1;
EXEC SQL END DECLARE SECTION;

또는

EXEC SQL BEGIN DECLARE SECTION;
#define MAX_CHAR_PTR 90000
char* var1;
EXEC SQL END DECLARE SECTION;
```

[예제 3] 다음은 구조체 포인터를 정의하는 다양한 예를 보여준다.

(1) 일반적인 구조체 포인터의 정의

```
struct tag1 
{ 
    int a; 
} *A; 
A = (struct tag1*)(malloc(sizeof(struct tag1))); 
INSERT INTO T1 VALUES ( :A ); 혹은 INSERT INTO T1 VALUES (:A->a); 
```

(2) 구조체 정의 후 구조체 포인터 정의

```
struct tag1 
{ 
    int a; 
}; 
struct tag1 *A; 
A = (struct tag1*)(malloc(sizeof(struct tag1))); 
SELECT I1 INTO :A FROM T1; 혹은 SELECT I1 INTO :A->a FROM T1; 
```

(3) 구조체 타입의 자료형 정의 후 포인터 정의

```
typedef struct tag1 
{ 
    int a; 
}tag1; 
tag1 *A; 
A = (tag1*)(malloc(sizeof(tag1))); 
SELECT I1 INTO :A FROM T1; 혹은 SELECT I1 INTO :A->a FROM T1; 
```

다음은 구조체 포인터인 vDataT2를 입력 호스트 변수로 사용하는 예를 보여준다.

\< 예제 프로그램 : pointer.sc \>

```
EXEC SQL BEGIN DECLARE SECTION; 
typedef struct tag 
{    
    char n1[11]; 
    int  n2; 
}tag; 
     
tag *dataT2; 
EXEC SQL END DECLARE SECTION; 

 void ins_t2(tag* vDataT2) 
{ 
    EXEC SQL BEGIN ARGUMENT SECTION; 
    tag *vDataT2; 
    EXEC SQL END ARGUMENT SECTION; 

    EXEC SQL INSERT INTO T2 VALUES (:vDataT2->n1, :vDataT2->n2); 
}
```

#### 구조체 타입

##### struct

호스트 변수의 데이터 타입으로 구조체를 사용할 수 있다.

구조체 타입은 테이블의 전체 칼럼을 검색하거나 삽입하는 경우 내장 SQL문에서
호스트 변수를 일일이 나열하지 않고 구조체 타입의 호스트 변수 하나만 사용하면
되므로 개발의 편의성을 제공한다. 예를 들어 INSERT문의 VALUES절이나 SELECT문의
INTO절에 구조체 타입의 호스트 변수를 사용할 수 있다.

구조체의 배열이나 구성 요소가 배열인 구조체도 호스트 변수의 데이터 타입으로 사용
가능하다. 배열 타입에 대한 자세한 설명은 9장을 참조하기 바란다.

##### 제한 사항

-   호스트 변수가 구조체이면 지시자 변수도 구조체이어야 한다. 이 때, 두 구조체의
    구성 요소 개수도 같아야 한다.

```
예) EXEC SQL BEGIN DECLARE SECTION;
struct tag1 { int i1; int i2; } var1;
struct tag2 { int i1_ind; int i2_ind; } var1_ind1;
struct tag3 { int i1_ind; int i2_ind; int i3_ind; } var1_ind2; 
EXEC SQL END DECLARE SECTION;

EXEC SQL INSERT INTO T1(I1, I2) 
VALUES (:var1 :var1_ind1);	(O)
EXEC SQL INSERT INTO T1(I1, I2) 
VALUES (:var1 :var1_ind2);	(X)
```

-   중첩된 구조체를 호스트 변수로 사용할 수 없다. 즉, 구조체의 구성 요소는
    구조체일 수 없다.

```
예) EXEC SQL BEGIN DECLARE SECTION;
struct tag1 
{ 	
int i1; 
struct tag2 
{ 
int i2; 
int i3; 
} sub_var; 
} var1; 		(X)
EXEC SQL END DECLARE SECTION;
```

-   구조체의 배열일 경우 지시자 변수를 지정할 수 없다. 따라서 구조체의 배열
    타입을 출력 호스트 변수로 사용할 경우 반환되는 칼럼값이 NULL이 아님을
    보장해야 한다. 왜냐하면 반환되는 칼럼 값이 NULL인데 지시자 변수를 지정하지
    않았다면 sqlca.sqlcode값이 SQL_SUCCESS_WITH_INFO이기 때문이다.

```
예) EXEC SQL BEGIN DECLARE SECTION;
struct tag1 {int i1; int i2; char i3[11]; } var1[10];
struct tag2 {int i1_ind; int i2_ind; int i3_ind; } var1_ind[10];
EXEC SQL END DECLARE SECTION;

EXEC SQL INSERT INTO T1(I1, i2, i3) 
VALUES (:var1 :var1_ind);	(X)
```

-   SELECT문 또는 FETCH문의 INTO절에 구조체의 배열을 호스트 변수로 사용할 경우
    출력 호스트 변수는 하나만 사용할 수 있다. 즉 다른 호스트 변수들과 함께
    사용할 수 없다. 따라서 INTO절에 사용할 호스트 변수가 구조체의 배열
    타입이라면 이 구조체의 구성 요소 개수는 SELECT절의 칼럼 개수와 동일해야
    한다.  
    마찬가지로 INSERT문의 VALUES절에 구조체의 배열을 호스트 변수로 사용할 경우
    입력 호스트 변수는 하나만 사용할 수 있다. 즉 다른 호스트 변수들과 함께
    사용할 수 없다. 따라서 VALUES절에 사용할 호스트 변수가 구조체의 배열
    타입이라면 이 구조체의 구성 요소 개수는 INSERT문의 칼럼 개수와 동일해야
    한다.

```
예) EXEC SQL BEGIN DECLARE SECTION;
struct tag1 { int i1; int i2; } var1[10];
int var2[10];
EXEC SQL END DECLARE SECTION;

EXEC SQL INSERT INTO T1(I1, I2, i3) 
VALUES (:var1, :var2);		(X)
```

-   마지막 2개의 제한 사항은 호스트 변수가 구조체의 배열일 경우 사용될 모든
    호스트 변수를 구조체가 포함해야 한다는 내부적인 규칙 때문이다.

##### 예제

다음은 구조체 타입의 사용 예를 보여준다.

구조체를 goods이름으로 타입 선언 한 후, goods 타입의 s_goods를 호스트 변수를
선언하고 s_goods를 INSERT문의 입력 호스트 변수로 사용한다.

\< 예제 프로그램 : hostvar.h \>

```
EXEC SQL BEGIN DECLARE SECTION;
typedef struct goods
{
    char   gno[10+1];
    char   gname[20+1];
    char   goods_location[9+1];
    int    stock;
    double price;
} goods;
EXEC SQL END DECLARE SECTION;
```

\< 예제 프로그램 : insert.sc \>

```
/* specify path of header file */
EXEC SQL OPTION (INCLUDE=./include);
/* include header file for precompile */
EXEC SQL INCLUDE hostvar.h;

EXEC SQL BEGIN DECLARE SECTION;
goods   s_goods;
EXEC SQL END DECLARE SECTION;

strcpy(s_goods.gno, "F111100003");
strcpy(s_goods.gname, "XX-102");
strcpy(s_goods.goods_location, "AD0003");
s_goods.stock = 6000;
s_goods.price = 10200.96;

EXEC SQL INSERT INTO GOODS VALUES (:s_goods);
```

### 확장된 데이터 타입

C 또는 C++ 에서 지원하는 데이터 타입 외에 APRE는 확장된 데이터 타입도 호스트
변수로 사용하도록 제공한다. 여기에서는 확장된 데이터 타입들의 종류와 사용 방법에
대해 설명한다.

#### VARCHAR

##### varchar

대소문자 구별없이 varchar와 VARCHAR가 모두 허용되며, 내부적으로 구조체 타입이다.
예를 들어

```
varchar a[10];
```

와 같이 선언하였다면 내부적으로

```
struct { int len; char arr[10] ;}a;
```

와 같은 구조를 가진다. 따라서, varchar 타입의 변수값을 참조하려면, a.arr과 같이
varchar 타입의 구성 요소를 명시해야 한다.

varchar 타입은 내부적으로 지시자 변수를 포함하고 있다. 구성 요소 len이 지시자
변수 역할을 한다. 따라서 지시자 변수를 필요로 할 때 varchar 타입을 사용하면
별도의 지시자 변수를 지정하지 않아도 되므로 편리하게 사용할 수 있다.

varchar 타입은 내부적으로 지시자 변수를 포함하고 있지만 별도의 지시자 변수
지정도 가능하다. 이것은 varchar 타입이 구조체의 구성요소 일 경우, 그 구조체에
대응되는 구조체 타입의 지시자 변수 선언 시 구조체 멤버인 varchar 타입에 대응되는
지시자 변수가 구조체 안에 포함되는 것을 가능하게 해준다.

##### 장점

이 타입은 지시자 변수를 포함하고 있으므로 별도의 지시자 변수 지정이 필요 없다.
따라서 지시자 변수를 필요로 할 경우 사용하면 편리하다.

##### 제한 사항

-   이 타입은 별도의 지시자 변수 지정이 없으면 자동으로 구성 요소 len이 지시자
    변수의 역할을 한다. 따라서 입력 호스트 변수로 사용할 경우 별도의 지시자
    변수를 지정하지 않았다면 len의 값을 반드시 적절하게 지정하여야 한다.
    입력값을 NULL로 지정하고 싶다면 len에는 –1을, 그렇지 않으면 입력값(arr값)의
    길이를 지정한다.

```
예) EXEC SQL BEGIN DECLARE SECTION;
varchar var1;
EXEC SQL END DECLARE SECTION;

strcpy(var1.arr, “ABC”);
var1.len = strlen(var1.arr);
EXEC SQL INSERT INTO T1(I1) 
VALUES (:var1);		(O)
```

-   이 타입을 출력 호스트 변수로 사용할 경우 대응되는 칼럼 타입이 CHAR
    타입이라면 호스트 변수는 칼럼 크기보다 1 크게 선언하여야 한다. 이유는 CHAR
    타입(칼럼 타입)은 고정 길이이므로 칼럼 길이만큼 데이터가 반환되는데, 호스트
    변수에는 이와 함께 마지막에 널문자를 저장해야 하기 때문이다. 만약 1 크게
    선언하지 않았다면 SELECT문이나 FETCH문 수행 후 sqlca.sqlcode 값은
    SQL_SUCCESS_WITH_INFO 이 되 것이다.

-   SELECT문 또는 FETCH문의 INTO절에 varchar의 이차원 배열을 호스트 변수로
    사용할 경우 출력 호스트 변수는 하나만 사용할 수 있다. 즉, 다른 호스트
    변수들과 함께 사용할 수 없다. 따라서 INTO절에 varchar타입의 이차원 배열을
    사용한다면 SELECT절의 칼럼 개수는 1개여야 한다.  
    마찬가지로 INSERT문의 VALUES절에 varchar타입의 이차원 배열을 호스트 변수로
    사용할 경우 입력 호스트 변수는 하나만 사용할 수 있다. 즉, 다른 호스트
    변수들과 함께 사용할 수 없다. 따라서 VALUES절에 varchar타입의 이차원 배열을
    사용한다면 INSERT문의 칼럼 개수는 1개여야 한다.  
    이것은 varchar가 내부적으로 구조체이므로 구조체의 제한 사항이 적용된 것이다.

```
예) EXEC SQL BEGIN DECLARE SECTION;
varchar var1[10][10+1];
int var2[10];
EXEC SQL END DECLARE SECTION;

EXEC SQL INSERT INTO T1(I1, I2) 
VALUES (:var1, :var2);		(X)
```

##### 예제

다음은 varchar 타입의 사용 예를 보여준다.

varchar 타입의 호스트 변수를 입력 호스트 변수와 출력 호스트 변수로 사용한다.
s_cus_job을 입력 호스트 변수로 s_address를 출력 호스트 변수로 사용한다.
s_cus_job.len에는 s_cus_job.arr의 데이터 길이를 지정한다. SELECT문 수행 후
s_address.len 값이 –1인지 검사한다.

\< 예제 프로그램 : varchar.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
char    s_cname[20+1];
varchar s_cus_job[20+1];
varchar s_address[60+1];
EXEC SQL END DECLARE SECTION;

strcpy(s_cus_job.arr, "WEBMASTER");
s_cus_job.len = strlen(s_cus_job.arr);

EXEC SQL SELECT CNAME, ADDRESS 
INTO :s_cname, :s_address 
FROM CUSTOMERS 
            WHERE CNO = BIGINT'7' 
AND CUS_JOB = :s_cus_job;
```

#### 날짜형 타입

날짜형 타입은 칼럼 타입이 date일 경우에만 사용 가능하다.

3가지의 날짜형 타입이 제공되므로 개발자는 용도에 맞게 사용하면 된다.

##### SQL_DATE_STRUCT 

이 타입은 년, 월, 일로 구성 되어 있다. 이 타입의 구조는 다음과 같다.

```
typedef struct tagDATE_STRUCT {
SQLSMALLINT  year;
SQLSMALLINT month;
SQLSMALLINT day;
} DATE_STRUCT;
```

##### 예제

다음은 SQL_DATE_STRUCT 타입의 사용 예를 보여준다.

s_date를 입력 또는 출력 호스트 변수로 사용하는 예이다.

\< 예제 프로그램 : date.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
SQL_DATE_STRUCT s_date;
int s_ind;
EXEC SQL END DECLARE SECTION;

EXEC SQL SELECT JOIN_DATE 
INTO :s_date :s_ind 
FROM EMPLOYEES 
WHERE ENO = 3;

s_date.year  = 2003;
s_date.month = 5;
s_date.day   = 9;

EXEC SQL UPDATE EMPLOYEES 
SET JOIN_DATE = :s_date 
WHERE ENO = 3;
```

##### SQL_TIME_STRUCT 

이 타입 사용 시 시, 분, 초 값을 참조할 수 있다. 이 타입의 구조는 다음과 같다.

```
typedef struct tagTIME_STRUCT {
SQLSMALLINT hour;
SQLSMALLINT minute;
SQLSMALLINT second;
} TIME_STRUCT;
```

##### 예제

다음은 SQL_TIME_STRUCT 타입의 사용 예를 보여준다.

s_time을 입력 또는 출력 호스트 변수로 사용하는 예이다.

\< 예제 프로그램 : date.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
SQL_TIME_STRUCT s_time;
int s_ind;
EXEC SQL END DECLARE SECTION;

EXEC SQL SELECT JOIN_DATE 
INTO :s_time :s_ind 
FROM EMPLOYEES 
WHERE ENO = 3;

s_time.hour   = 12;
s_time.minute = 12;
s_time.second = 12;

EXEC SQL UPDATE EMPLOYEES 
SET JOIN_DATE = :s_time 
WHERE ENO = 4;
```

##### SQL_TIMESTAMP_STRUCT 

이 타입 사용 시 년, 월, 일, 시, 분, 초 값을 참조할 수 있다. 이 타입의 구조는
다음과 같다. 이 구조체 참조 시에 fraction은 10억분의 1초(Nano second)임에 주의
한다.

```
typedef struct tagTIMESTAMP_STRUCT {
SQLSMALLINT  year;
SQLSMALLINT month;
SQLSMALLINT day;
SQLSMALLINT hour;
SQLSMALLINT minute;
SQLSMALLINT second;
SQLINTEGER  fraction;
} TIMESTAMP_STRUCT;
```

##### 예제

다음은 SQL_TIMESTAMP_STRUCT 타입의 사용 예를 보여준다.

s_timestamp를 입력 또는 출력 호스트 변수로 사용하는 예이다.

\< 예제 프로그램 : date.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
SQL_TIMESTAMP_STRUCT s_timestamp;
int s_ind;
EXEC SQL END DECLARE SECTION;

EXEC SQL SELECT JOIN_DATE 
INTO :s_timestamp :s_ind 
FROM EMPLOYEES 
WHERE ENO = 3;

s_timestamp.year     = 2003;
s_timestamp.month    = 5;
s_timestamp.day      = 9;
s_timestamp.hour     = 4;
s_timestamp.minute   = 0;
s_timestamp.second   = 15;
s_timestamp.fraction = 100000;

EXEC SQL UPDATE EMPLOYEES 
SET JOIN_DATE = :s_timestamp 
WHERE ENO = 5;    
```

##### SQL_NUMERIC_STRUCT 

이 타입 사용 시 NUMERIC 데이터를 전달할 수 있다. 

이 타입의 구조는 다음과 같다. 

```
typedef struct tagSQL_NUMERIC_STRUCT
{
	SQLCHAR		precision;
	SQLSCHAR	scale;
	SQLCHAR		sign;	/* 1=pos 0=neg */
	SQLCHAR		val[SQL_MAX_NUMERIC_LEN];
} SQL_NUMERIC_STRUCT;
```

##### 예제

다음은 SQL_NUMERIC_STRUCT 타입의 사용 예를 보여준다.

s_price를 입력 또는 출력 호스트 변수로 사용하는 예이다.

\< 예제 프로그램 : date.sc \>

```
/* declare host variables */
EXEC SQL BEGIN DECLARE SECTION;
char                 s_gno[10+1];
char                 s_gname[20+1];
char                 s_goods_location[9+1];
int                  s_stock;
SQL_NUMERIC_STRUCT   s_price;
EXEC SQL END DECLARE SECTION;

int s_price_val = 0;

/* use scalar host variables */
strcpy(s_gno, "F111100002");
strcpy(s_gname, "XX-101");
strcpy(s_goods_location, "FD0003");
s_stock = 5000;

/* set value 123.4 on SQL_NUMERIC_STRUCT */
memset(&s_price, 0, sizeof(s_price));
s_price.precision = 4;
s_price.scale = 1;
s_price.sign = 1;
s_price_val = 1234;
memcpy(&s_price.val, &s_price_val, sizeof(int));

printf("------------------------------------------------------------------\n");
printf("[SQL_NUMERIC_STRUCT Insert]\n");
printf("------------------------------------------------------------------\n");

EXEC SQL INSERT INTO GOODS VALUES (:s_gno, :s_gname, :s_goods_location, :s_stock, :s_price);

memset(s_gname, 0, sizeof(s_gname));
memset(s_goods_location, 0, sizeof(s_goods_location));
s_stock = 0;
memset(&s_price, 0, sizeof(s_price));

printf("------------------------------------------------------------------\n");
printf("[SQL_NUMERIC_STRUCT Select]\n");
printf("------------------------------------------------------------------\n");

EXEC SQL SELECT GNAME, GOODS_LOCATION, STOCK, PRICE INTO :s_gname, :s_goods_location, :s_stock, :s_price FROM GOODS WHERE GNO = :s_gno;
/* check sqlca.sqlcode */
if (sqlca.sqlcode == SQL_SUCCESS)
{
    /* sqlca.sqlerrd[2] holds the rows-processed(inserted) count */
    printf("%d rows select s_gno=%s, s_gname=%s, s_goods_location=%s, s_stock=%d, s_price=%.15G \n\n", 
            sqlca.sqlerrd[2], s_gno, s_gname, s_goods_location, s_stock, APRE_NUMERIC_TO_DOUBLE(s_price));
}
else
{
    printf("Error : [%d] %s\n\n", SQLCODE, sqlca.sqlerrm.sqlerrmc);
}   
```

#### 이진 타입

이진 타입은 칼럼 타입이 blob, BYTE, NIBBLE일 경우 호스트 변수의 타입으로 사용할
수 있다.

이진 타입은 내부적으로 다음과 같이 타입 정의가 되어있다.

```
typedef char APRE_CLOB;
typedef char APRE_BLOB;
typedef char APRE_BINARY;
typedef char APRE_BINARY2;
typedef char APRE_BYTES;
typedef char APRE_NIBBLE;
typedef char APRE_VARBYTES;
```

아래는 각 타입에 대한 설명이다.

##### APRE_CLOB

칼럼 타입이 CLOB인 경우에만 사용이 가능하다.

반드시 지시자 변수를 지정해야 한다.

이 타입의 호스트 변수가 입력 호스트 변수로 사용될 경우, NULL을 입력값으로
지정하려면 지시자 변수에는 –1을 지정하고, 그 외의 값(NULL이 아닌 값)을
입력값으로 지정하려면 지시자 변수에는 호스트 변수에 저장된 값의 길이를 지정한다.

이 타입의 호스트 변수가 출력 호스트 변수로 사용될 때에는 지시자 변수가 –1이면
NULL이 반환된 경우이고, 0보다 큰 값이면 지시자 변수에는 호스트 변수에 저장된
값의 길이가 저장된다.

##### 예제

다음은 APRE_CLOB 타입의 사용 예를 보여준다.

입력 호스트 변수로 ins_clob을, 입력 지시자 변수로 ins_clob_ind를 사용한다.
ins_clob_ind에는 ins_clob에 저장된 데이터의 길이를 입력한다. 출력 호스트 변수로
sel_clob을, 출력 지시자 변수로 sel_clob_ind를 사용한다. SELECT문 수행 후
sel_clob_ind에는 sel_clob값이 NULL이면 –1이, 그렇지 않으면 sel_clob의 길이가
저장될 것이다.

\< 예제 프로그램 : binary.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
APRE_CLOB ins_clob[10+1];
APRE_CLOB sel_clob[10+1];
SQLLEN ins_clob_ind;  
SQLLEN sel_clob_ind; 
EXEC SQL END DECLARE SECTION;

memset(ins_clob, 0x41, 10);
ins_clob_ind = 10; /* set length of ins_clob value to indicator variable */

EXEC SQL INSERT INTO T_CLOB
VALUES (:ins_clob :ins_clob_ind);

EXEC SQL SELECT *
INTO :sel_clob :sel_clob_ind
FROM T_CLOB;
```

##### APRE_BLOB

칼럼 타입이 BLOB 인 경우에만 사용이 가능하다.

반드시 지시자 변수를 지정해야 한다.

이 타입의 호스트 변수가 입력 호스트 변수로 사용될 경우, NULL을 입력값으로
지정하려면 지시자 변수에는 –1을 지정한다. 그 외의 값(NULL이 아닌 값)을
입력값으로 지정하려면 지시자 변수에는 호스트 변수에 저장된 값의 길이를 지정한다.

이 타입의 호스트 변수가 출력 호스트 변수로 사용될 경우, 지시자 변수가 –1이면
NULL이 반환된 경우이고, 0보다 큰 값이면 지시자 변수에는 호스트 변수에 저장된
값의 길이가 저장된다.

##### 예제

다음은 APRE_BLOB 타입의 사용 예를 보여준다.

입력 호스트 변수로 ins_blob을, 입력 지시자 변수로 ins_blob_ind를 사용한다.
ins_blob_ind에는 ins_blob의 길이가 저장된다. 출력 호스트 변수로 sel_blob을, 출력
지시자 변수로 sel_blob_ind를 사용한다. SELECT문 수행 후 sel_blob_ind에는
sel_blob값이 NULL이면 –1이, 그렇지 않으면 sel_blob의 길이가 저장된다.

\< 예제 프로그램 : binary.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
APRE_BLOB ins_blob[10+1];
APRE_BLOB sel_blob[10+1];
SQLLEN ins_blob_ind; 
SQLLEN sel_blob_ind;
EXEC SQL END DECLARE SECTION;

memset(ins_blob, 0x21, 10);
ins_blob_ind = 10; /* set length of ins_blob value to indicator variable */

EXEC SQL INSERT INTO T_BLOB
VALUES (:ins_blob :ins_blob_ind);

EXEC SQL SELECT *
INTO :sel_blob :sel_blob_ind
FROM T_BLOB;
```

##### APRE_BINARY

APRE_BLOB 과 동일한 특성을 가진다.

##### 예제

다음은 APRE_BINARY 타입의 사용 예를 보여준다.

입력 호스트 변수로 ins_blob을, 입력 지시자 변수로 ins_blob_ind를 사용한다.
ins_blob_ind에는 ins_blob의 길이가 저장된다. 출력 호스트 변수로 sel_blob을, 출력
지시자 변수로 sel_blob_ind를 사용한다. SELECT문 수행 후 sel_blob_ind에는
sel_blob값이 NULL이면 –1이, 그렇지 않으면 sel_blob의 길이가 저장된다.

\< 예제 프로그램 : binary.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
APRE_BINARY ins_blob[10+1]; 
APRE_BINARY sel_blob[10+1];
int ins_blob_ind;   
int sel_blob_ind;  
EXEC SQL END DECLARE SECTION;

memset(ins_blob, 0x21, 10);
ins_blob_ind = 10; /* set length of ins_blob value to indicator variable */

EXEC SQL INSERT INTO T_BLOB 
VALUES (:ins_blob :ins_blob_ind);

EXEC SQL SELECT * 
INTO :sel_blob :sel_blob_ind 
FROM T_BLOB;
```

##### APRE_BINARY2

APRE_BLOB, APRE_BINARY 와 동일한 특성을 가진다. 다만 입력 호스트 변수의 데이터 사이즈가
128KB 이하일 때 성능향상이 있으며, 최대 데이터 사이즈가 100MB라는 제한이 있다.
데이터 사이즈가 128KB를 초과할 때는 성능 향상 및 메모리 절약을 위해 APRE_BLOB, APRE_BINARY 타입
사용을 추천한다.

##### 예제

다음은 APRE_BINARY2 타입의 사용 예를 보여준다.

입력 호스트 변수로 ins_blob을, 입력 지시자 변수로 ins_blob_ind를 사용한다.
ins_blob_ind에는 ins_blob의 길이가 저장된다. 출력 호스트 변수로 sel_blob을, 출력
지시자 변수로 sel_blob_ind를 사용한다. SELECT문 수행 후 sel_blob_ind에는
sel_blob값이 NULL이면 –1이, 그렇지 않으면 sel_blob의 길이가 저장된다.

\< 예제 프로그램 : binary.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
APRE_BINARY2 ins_blob[10+1];
APRE_BINARY2 sel_blob[10+1];
int ins_blob_ind;
int sel_blob_ind;
EXEC SQL END DECLARE SECTION;

memset(ins_blob, 0x21, 10);
ins_blob_ind = 10; /* set length of ins_blob value to indicator variable */

EXEC SQL INSERT INTO T_BLOB
VALUES (:ins_blob :ins_blob_ind);

EXEC SQL SELECT *
INTO :sel_blob :sel_blob_ind 
FROM T_BLOB;
```

##### APRE_BYTES

칼럼 타입이 BYTE인 경우에만 사용 가능하다.

그 외 다른 특성은 APRE_BLOB 과 동일하다.

##### 예제

다음은 APRE_BYTES 타입의 사용 예를 보여준다.

입력 호스트 변수로 ins_bytes를, 입력 지시자 변수로 ins_bytes_ind를 사용한다.
ins_bytes_ind에는 ins_bytes의 길이가 저장된다. 출력 호스트 변수로 sel_bytes를,
출력 지시자 변수로 sel_bytes_ind를 사용한다. SELECT문 수행 후 sel_bytes_ind에는
sel_bytes값이 NULL이면 –1이, 그렇지 않으면 sel_bytes의 길이가 저장된다.

\< 예제 프로그램 : binary.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
APRE_BYTES ins_bytes[5+1]; 
APRE_BYTES sel_bytes[5+1];
int ins_bytes_ind;   
int sel_bytes_ind;  
EXEC SQL END DECLARE SECTION;

memset(ins_bytes, 0x21, 5);
ins_bytes_ind = 5; /* set length of ins_bytes value to indicator variable */

EXEC SQL INSERT INTO T_BYTES 
VALUES (:ins_bytes :ins_bytes_ind);

EXEC SQL SELECT * 
INTO :sel_bytes :sel_bytes_ind 
FROM T_BYTES;
```

##### APRE_NIBBLE

칼럼 타입이 NIBBLE인 경우에만 사용 가능하다.

입력 호스트 변수의 경우, NULL을 입력값으로 지정하려면 지시자 변수를, 그 외의
값(NULL이 아닌 값)을 입력값으로 지정하려면 호스트 변수의 첫 번째 byte를
이용한다. 이 때, 지시자 변수가 우선한다. 즉, 내부적으로 지시자 변수를 먼저
검사하여 –1이면 NULL로 처리하고 그렇지 않으면 호스트 변수의 첫 번째 byte값을
입력 데이터의 길이로 처리한다. 따라서 NULL을 입력값으로 지정하려면 지시자 변수에
–1을 지정하고, 그 외의 값(NULL이 아닌 값)을 입력값으로 지정하려면 호스트 변수의
첫 번째 byte에 입력 데이터의 길이를 지정한다.

첫 번째 byte에는 입력 데이터의 길이가 저장되므로 실제 데이터는 호스트 변수의 두
번째 byte부터 저장된다. 따라서, 입력 데이터의 길이는 호스트 변수의 두 번째
byte부터 계산되며 nibble수를 의미한다. 1nibble은 4bit이다.

출력 호스트 변수의 경우, 지시자 변수값이 –1이면 NULL이 반환된 경우이고, 그렇지
않으면 지시자 변수에는 호스트 변수에 저장된 데이터의 전체 길이(bytes수)가
저장된다. 그리고 호스트 변수의 첫 번째 byte에는 실제 데이터의 길이(nibbles수,
4bit=1)가 저장되며, 실제 데이터는 두 번째 byte부터 저장된다. 따라서 NULL이 아닌
경우 지시자 변수값과 첫 번째 byte값과의 관계는 다음과 같다.

지시자 변수값 = ((첫번째byte값+1)/2 + 1(첫번째byte))

##### 예제

다음은 APRE_NIBBLE 타입의 사용 예를 보여준다.

입력 호스트 변수로 ins_nibble을 사용한다. 입력값이 NULL이 아니므로
ins_nibble[0]에 입력 데이터의 길이(nibble수) 10을 지정한다.

출력 호스트 변수로 sel_nibble을, 출력 지시자 변수로 sel_nibble_ind를 사용한다.
SELECT문 수행 후 sel_nibble값이 NULL이면 sel_nibble_ind에는 –1이, 그렇지 않으면
sel_nibble의 길이(bytes수)가 저장된다. 그리고 sel_nibble[0]에는
sel_nibble[1]부터 계산된 실제 데이터의 길이(nibble수)가 저장된다.

\< 예제 프로그램 : binary.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
APRE_NIBBLE ins_nibble[5+2]; 
APRE_NIBBLE sel_nibble[5+2];
int sel_nibble_ind;  
EXEC SQL END DECLARE SECTION;

memset(ins_nibble+1, 0x21, 5);
ins_nibble[0] = 10; /* set length of ins_nibble value to ins_nibble[0] */

EXEC SQL INSERT INTO T_NIBBLE 
VALUES (:ins_nibble);

EXEC SQL SELECT * 
INTO :sel_nibble :sel_nibble_ind 
FROM T_NIBBLE;
```

##### APRE_VARBYTES 

칼럼 타입이 VARBYTE인 경우에만 사용 가능하다.

그 외 다른 특성은 APRE_BLOB 과 동일하다.

#### 예제 프로그램

##### varchar.sc 

$ALTIBASE_HOME/sample/APRE/varchar.sc 참고

##### 실행결과

```
$ is –f schema/schema.sql
$ make varchar
$ ./varchar
<VARCHAR TYPE>
-----------------------------------------------------------
[Scalar VARCHAR]                                                  
-----------------------------------------------------------
s_cname       = [DKHAN               ]
s_address.arr = [YeongdeungpoGu Seoul]
s_address.len = [20]

-----------------------------------------------------------
[Array of VARCHAR]                                                
-----------------------------------------------------------
CUS_JOB                                                           
-----------------------------------------------------------
ENGINEER
DOCTOR
DESIGNER
ENGINEER
WEBMASTER
WEBPD
PLANER
PD
DESIGNER
NULL
MANAGER
BANKER
ENGINEER
BANKER
MANAGER
PLANER
NULL
ENGINEER
NULL
WEBMASTER

-----------------------------------------------------------
[Structure Included VARCHAR]                                      
-----------------------------------------------------------
Success insert

-----------------------------------------------------------
[Array of Structure Included VARCHAR]                             
-----------------------------------------------------------
3 rows inserted
3 times insert success
```

##### date.sc 

$ALTIBASE_HOME/sample/APRE/date.sc 참고

##### 실행결과

```
$ is –f schema/schema.sql
$ make date
$ ./date
<DATE TYPE>
------------------------------------------------------
[SQL_DATE_STRUCT]                                                 
------------------------------------------------------
JOIN_DATE of ENO is 3 : 2000/1/11

------------------------------------------------------
[SQL_TIME_STRUCT]                                                 
------------------------------------------------------
JOIN_DATE of ENO is 3 : 0:0:0

------------------------------------------------------
[SQL_TIMESTAMP_STRUCT]                                            
------------------------------------------------------
JOIN_DATE of ENO is 3 : 2000/1/11 0:0:0:0

------------------------------------------------------
[SQL_DATE_STRUCT]                                                 
------------------------------------------------------
Success update with SQL_DATE_STRUCT
1 rows updated

------------------------------------------------------
[SQL_TIME_STRUCT]                                                 
------------------------------------------------------
Success update with SQL_TIME_STRUCT
1 rows updated

------------------------------------------------------
[SQL_TIMESTAMP_STRUCT]                                            
------------------------------------------------------
Success update with SQL_TIMESTAMP_STRUCT
1 rows updated

------------------------------------------------------
[Array of Structure Included Date Type]                           
------------------------------------------------------
Success insert
3 rows inserted
3 times insert success
```

##### binary.sc 

$ALTIBASE_HOME/sample/APRE/binary.sc 참고

##### 실행결과

```
$ is –f schema/schema.sql
$ make binary
$ ./binary
<BINARY TYPE>
------------------------------------------------------
[APRE_CLOB]                                                     
------------------------------------------------------
Success insert with APRE_CLOB
sel_clob     = AAAAAAAAAA
sel_clob_ind = 10

------------------------------------------------------
 [APRE_BLOB]                                                     
------------------------------------------------------
Success insert with APRE_BLOB
sel_blob     = !!!!!!!!!!
sel_blob_ind = 10
------------------------------------------------------
[APRE_BINARY]                                                      
------------------------------------------------------
Success insert with APRE_BINARY
sel_blob     = !!!!!!!!!!
sel_blob_ind = 10

------------------------------------------------------
[APREBYTES]                                                       
------------------------------------------------------
Success insert with APRE_BYTES
sel_bytes     = !!!!!
sel_bytes_ind = 5

------------------------------------------------------
[APRE_NIBBLE]                                                      
------------------------------------------------------
Success insert with APRE_NIBBLE
sel_nibble     = !!!!!
sel_nibble_ind = 6
sel_nibble[0]  = 10
```

### 칼럼 타입과 호스트 변수 타입

칼럼 타입마다 다양한 호스트 변수 타입을 사용할 수 있다. 여기에서는 칼럼 타입에
따른 변환 가능한 호스트 변수 타입을 알아보고 그 중에서도 칼럼 타입별 최적의
호스트 변수 타입을 알아보기로 한다.

#### 입력 호스트 변수

다음 표는 칼럼 타입별 사용 가능한 입력 호스트 변수 타입을 나열한 표이다. 그리고
‘최소 변환 비용을 가지는 호스트 변수 타입’은 권장 타입으로써 이 타입을 사용할 때
성능 향상을 기대할 수 있다.
<table>
	<tr>
		<th colspan="2">칼럼 타입</th>
		<th>변환 가능한 
호스트 변수 타입
</th>
		<th>최소 변환 비용을 가지는 
호스트 변수 타입
</th>
	</tr>
	<tr>
		<td rowspan="2">문자형 타입</td>
		<td>CHAR</td>
		<td>char, varchar, 
short, int, long, long long,
double, float,
SQL_DATE_STRUCT,
SQL_TIME_STRUCT,
SQL_TIMESTAMP_STRUCT,
</td>
		<td>char, varchar</td>
	</tr>
	<tr>
		<td>VARCHAR</td>
		<td>char, varchar, 
short, int, long, long long,
double, float,
SQL_DATE_STRUCT,
SQL_TIME_STRUCT,
SQL_TIMESTAMP_STRUCT,
</td>
		<td>char, varchar</td>
	</tr>
	<tr>
		<td rowspan="3">정수형 타입</td>
		<td>SMALLINT</td>
		<td>char, varchar, 
short, int, long, long long,
double, float
</td>
		<td>short</td>
	</tr>
	<tr>
		<td>INTEGER</td>
		<td>char, varchar, 
short, int, long, long long,
double, float
</td>
		<td>int</td>
	</tr>
	<tr>
		<td>BIGINT</td>
		<td>char, varchar, 
short, int, long, long long,
double, float
</td>
		<td>long, long long</td>		
	</tr>
	<tr>
		<td rowspan="4">실수형 타입</td>
		<td>NUMERIC
NUMBER
DECIMAL
</td>
		<td>char, varchar, 
short, int, long, long long,
double, float, SQL_NUMERIC_STRUCT
</td>
		<td>char,
long, long long,
float, double
</td>
	</tr>
    <tr>
    	<td>FLOAT</td>
    	<td>char, varchar, 
short, int, long, long long,
double, float
</td>
    	<td>float</td>
    </tr>
    <tr>
    	<td>REAL</td>
    	<td>char, varchar, 
short, int, long, long long,
double, float
</td>
    	<td>double</td>
    </tr>
    <tr>
    	<td>DOUBLE</td>
    	<td>char, varchar, 
short, int, long, long long,
double, float
</td>
    	<td>double</td>
    </tr>
    <tr>
    	<td>날짜형 타입</td>
    	<td>DATE</td>
    	<td>char, 
SQL_DATE_STRUCT,
SQL_TIME_STRUCT,
SQL_TIMESTAMP_STRUCT
</td>
    	<td>char, 
SQL_DATE_STRUCT,
SQL_TIME_STRUCT, 
SQL_TIMESTAMP_STRUCT
</td>
    </tr>
    <tr>
    	<td rowspan="6">이진 타입</td>
    	<td>CLOB</td>
    	<td>APRE_CLOB</td>
    	<td>APRE_CLOB</td>
    </tr>
    <tr>
    	<td>BLOB</td>
    	<td>APRE_BLOB,
APRE_BINARY,
APRE_BINARY2</td>
    	<td>APRE_BLOB,
APRE_BINARY,
APRE_BINARY2</td>
    </tr>
    <tr>
    	<td>BYTE</td>
    	<td>APRE_BYTES, APRE_VARBYTES</td>
    	<td>APRE_BYTES, APRE_VARBYTES</td>
    </tr>
    <tr>
    	<td>NIBBLE</td>
    	<td>APRE_NIBFBLE</td>
    	<td>APRE_NIBBLE</td>
    </tr>
    <tr>
    	<td>VARBYTE</td>
    	<td>APRE_BYTES, APRE_VARBYTES</td>
    	<td>APRE_BYTES, APRE_VARBYTES</td>
    </tr>
</table>

#### 출력 호스트 변수

다음 표는 칼럼 타입별 사용 가능한 출력 호스트 변수 타입을 나열한 표이다. 그리고
‘최소 변환 비용을 가지는 호스트 변수 타입’은 권장 타입으로서 이 타입 사용 시
성능 향상을 기대할 수 있다.
<table>
	<tr>
		<th colspan="2">칼럼 타입</th>
		<th>변환 가능한 
호스트 변수 타입
</th>
		<th>최소 변환 비용을 가지는 
호스트 변수 타입
</th>
	</tr>
	<tr>
		<td rowspan="2">문자형 타입</td>
		<td>CHAR</td>
		<td>char, varchar, 
APRE_BINARY, APRE_BINARY2
</td>
		<td>char, varchar</td>
	</tr>
	<tr>
		<td>VARCHAR</td>
		<td>char, varchar, 
APRE_BINARY, APRE_BINARY2
</td>
		<td>char, varchar</td>
	</tr>
	<tr>
		<td rowspan="3">정수형 타입</td>
		<td>SMALLINT</td>
		<td>char, varchar, 
short, int, long, long long,
double, float,
APRE_BINARY, APRE_BINARY2
</td>
		<td>short</td>
	</tr>
	<tr>
		<td>INTEGER</td>
		<td>char, varchar, 
short, int, long, long long,
double, float,
APRE_BINARY, APRE_BINARY2
</td>
		<td>int</td>
	</tr>
	<tr>
		<td>BIGINT</td>
		<td>char, varchar, 
short, int, long, long long,
double, float,
APRE_BINARY, APRE_BINARY2
</td>
		<td>long, long long</td>		
	</tr>
	<tr>
		<td rowspan="4">실수형 타입</td>
		<td>NUMERIC
NUMBER
DECIMAL
</td>
		<td>char, varchar, 
short, int, long, long long,
double, float,
APRE_BINARY, APRE_BINARY2, SQL_NUMERIC_STRUCT
</td>
		<td>char,
long, long long,
float, double
</td>
	</tr>
    <tr>
    	<td>FLOAT</td>
    	<td>char, varchar, 
short, int, long, long long,
double, float,
APRE_BINARY, APRE_BINARY2
</td>
    	<td>float</td>
    </tr>
    <tr>
    	<td>REAL</td>
    	<td>char, varchar, 
short, int, long, long long,
double, float,
APRE_BINARY, APRE_BINARY2
</td>
    	<td>double</td>
    </tr>
    <tr>
    	<td>DOUBLE</td>
    	<td>char, varchar, 
short, int, long, long long,
double, float,
APRE_BINARY, APRE_BINARY2
</td>
    	<td>double</td>
    </tr>
    <tr>
    	<td>날짜형 타입</td>
    	<td>DATE</td>
    	<td>char, 
SQL_DATE_STRUCT,
SQL_TIME_STRUCT,
SQL_TIMESTAMP_STRUCT,
APRE_BINARY, APRE_BINARY2
</td>
    	<td>char, 
SQL_DATE_STRUCT,
SQL_TIME_STRUCT, 
SQL_TIMESTAMP_STRUCT
</td>
    </tr>
    <tr>
    	<td rowspan="6">이진 타입</td>
    	<td>CLOB</td>
    	<td>APRE_CLOB</td>
    	<td>APRE_CLOB</td>
    </tr>
    <tr>
    	<td>BLOB</td>
    	<td>APRE_BLOB,
APRE_BINARY,
APRE_BINARY2</td>
    	<td>APRE_BLOB,
APRE_BINARY,
APRE_BINARY2</td>
    </tr>
     <tr>
    	<td>BYTE</td>
    	<td>APRE_BYTES, APRE_VARBYTES,
APRE_BINARY, APRE_BINARY2
</td>
    	<td>APRE_BYTES, APRE_VARBYTES</td>
    </tr>
     <tr>
    	<td>NIBBLE</td>
    	<td>APRE_NIBBLE,
APRE_BINARY, APRE_BINARY2
</td>
    	<td>APRE_NIBBLE</td>
    </tr>
     <tr>
    	<td>VARBYTE</td>
    	<td>APRE_BYTES, APRE_VARBYTES, APRE_BINARY, APRE_BINARY2</td>
    	<td>APRE_BYTES, APRE_VARBYTES</td>
    </tr>
</table>

출력 호스트 변수의 경우 모든 칼럼 타입에 대해 APRE_BINARY, APRE_BINARY2 타입을 호스트 변수로
사용할 수 있다. APRE_BINARY,  APRE_BINARY2 타입은 칼럼값을 해당 타입에 맞게 변환해서 호스트
변수에 저장하는게 아니라 메모리 내용 그대로 호스트 변수에 저장(memcpy)한다.
따라서, APRE_BINARY, APRE_BINARY2 타입을 호스트 변수로 사용하려면 각 칼럼 타입별로 내부적으로
어떻게 메모리에 저장되는지 저장방식을 알아야 하고, 이를 해석할 줄 알아야 한다.
이처럼 APRE_BINARY, APRE_BINARY2 타입을 호스트 변수로 사용할 경우 타입 변환 비용이 없어 성능은
좋을지 모르나 개발자 관점에서 사용하기 복잡하여 일반적으로 APRE_BINARY, APRE_BINARY2 타입은
BLOB 타입(칼럼 타입)을 제외하고는 사용을 추천하지 않는다.

6.내장 SQL문
----------

### 개요

내장 SQL문은 응용 프로그램 내에 포함되어 있는 SQL문을 말한다.

#### 구문

```
EXEC SQL … ;
```

내장 SQL문은 “EXEC SQL”문장으로 시작해서 “;”으로 끝난다.

“EXEC SQL”과 “;”사이에 SELECT, UPDATE 등의 DML문, CREATE, DROP 등의 DDL문 등
다양한 SQL문을 사용할 수 있다.

##### 제한 사항

SQL문 길이는 최대 32Kbytes까지 허용한다.

##### 예제

다음은 내장 SQL문의 사용 예를 보여준다.

< SELECT문 : select.sc >

```
EXEC SQL BEGIN DECLARE SECTION;
short      s_dno;
char       s_dname[30+1];
char       s_dep_location[9+1];
EXEC SQL END DECLARE SECTION;

EXEC SQL SELECT DNAME, DEP_LOCATION 
INTO :s_dname, :s_dep_location
           FROM DEPARTMENTS 
WHERE DNO = :s_dno;
```

< INSERT문 : insert.sc >

```
EXEC SQL BEGIN DECLARE SECTION;
char    s_gno[10+1];
char    s_gname[20+1];
char    s_goods_location[9+1];
int     s_stock;
double  s_price;
EXEC SQL END DECLARE SECTION;

EXEC SQL INSERT INTO GOODS 
VALUES (:s_gno, :s_gname, 
:s_goods_location, 
:s_stock, :s_price);
```

각 내장 SQL문에 대한 구문은 뒤에서 더 자세히 다루도록 한다.

#### 내장 SQL문 분류

내장 SQL문은 크게 두 가지로 분류된다. 수행할 SQL문이 프로그램 작성 시
결정되느냐, 실행 시간에 결정되느냐에 따라 정적 SQL문과 동적 SQL문으로 나눌 수
있다. 본 장에서는 정적 SQL문에 대해서만 언급하기로 한다. 동적 SQL문에 대한
자세한 설명은 10장을 참조하기 바란다.

내장 SQL문은 데이터 처리 방식과 역할에 따라 다음과 같이 분류할 수 있다.

##### 호스트 변수 선언부 

내장 SQL문에서 사용할 호스트 변수를 선언한다. 자세한 내용은 3장을 참조하기
바란다.

##### 함수 인자 선언부 

호스트 변수로 사용할 함수 인자를 선언한다. 자세한 내용은 3장을 참조하기 바란다.

##### 연결 관련 SQL문

데이터베이스에 연결, 연결 해제와 관련된 SQL문을 말한다.

##### 기본 내장 SQL문

SELECT, UPDATE, INSERT, DELETE 등의 DML문과 CREATE, DROP, ALTER 등의 DDL문이
포함된다.

##### 커서 처리 SQL문

커서를 이용한 데이터 처리 SQL문을 말한다. 커서 정의, 커서 열기, 커서 이용하여
데이터 가져오기, 커서 닫기 등의 SQL문이 여기에 포함된다. 자세한 내용은 8장을
참조하기 바란다.

##### SQL/PSM 처리 SQL문

저장 프로시저와 저장 함수 관련 SQL문을 말한다. 저장 프로시저/함수의 생성,
재컴파일, 실행, 삭제 등의 SQL문이 여기에 포함된다. 자세한 내용은 11장을 참조하기
바란다.

##### 기타 내장 SQL문

위의 경우를 제외한 모든 Altibase SQL문을 말한다. 작업 제어문, 시스템 제어문,
트랜잭션 처리문 등이 여기에 포함된다.

##### OPTION문

C/C++전처리기가 제공하는 다양한 옵션 설정에 관련된 내장 SQL문을 말한다.

### 연결 관련 SQL문

연결 관련 SQL문은 데이터베이스 서버와의 연결에 관련된 SQL문을 말한다.
CONNECT문과 DISCONNECT문이 여기에 속한다.

#### CONNECT

데이터베이스 서버에 연결한다.

##### 구문

```
EXEC SQL CONNECT <:user> IDENTIFIED BY <:passwd>
[ USING <:conn_opt1> [ , <:conn_opt2> ] ];
```

##### 인자

-   \<:*user*\>: 데이터베이스 서버에 연결할 사용자 이름

-   \<:*passwd*\>: 데이터베이스 서버에 연결할 사용자 암호

-   \<:*conn_opt1*\>: 데이터베이스 서버와의 연결 방식을 지정

    -   DSN: 연결할 데이터베이스 서버의 IP주소

    -   CONNTYPE: 데이터베이스 서버와의 통신 방법

        -   1: TCP/IP

        -   2: UNIX DOMAIN

        -   3: IPC

    -   PORT_NO: 데이터베이스 서버에 연결할 연결 포트 번호

    -   NLS_USE: 사용 언어 지정

        -   KO16KSC5601: 한국어

        -   US7ASCII: 영어

        -   MS949

        -   BIG5

        -   GB231280

        -   MS936

        -   UTF8

        -   SHIFTJIS

        -   MS932

        -   EUCJP

    -   BATCH: 연결할 세션의 Batch Processing Mode 지정

        -   ON: Batch Processing Mode

        -   OFF: Non Batch Processing Mode

-   \<:*conn_opt2*\>: 연결 방식을 지정하는 방법은 *conn_opt1*과 동일하다.
    *conn_opt1*을 이용한 데이터베이스 서버와의 연결 실패 시 자동으로
    *conn_opt2*를 이용하여 데이터베이스 서버와의 연결을 시도한다.

##### 설명

내장 SQL문 한 프로그램 내에서 하나 이상의 연결을 허용한다. 한 프로그램 내에서
여러 개의 연결을 할 경우, 연결 이름을 가지지 않는 연결은 하나만 허용하는데,
여기에서는 이 연결(연결 이름을 가지지 않는 경우)에 관해서만 다루기로 한다.

한 애플리케이션 내에서 두 개 이상의 연결을 이용하는 다중 연결 프로그램이나
멀티쓰레드 프로그램 방법에 대한 자세한 설명은 12장과 13장을 참조하기 바란다.

> \* 주의: 만일 연결 스트링에 PORT_NO와 NLS_USE 값을 명시하지 않은 경우 프로퍼티
> 파일에 설정된 값과 동일한 값으로 다음 환경변수를 이용하여 반드시 설정해야 한다.

```
export ALTIBASE_PORT_NO=20300
export ALTIBASE_NLS_USE=US7ASCII 
```

##### 연결 옵션 2개 지정하는 경우 수행 결과

**SQL_SUCCESS**: 처음 옵션으로 연결 성공한 경우.

**SQL_SUCCESS_WITH_INFO**: 처음 옵션으로 연결 실패하고, 두 번째 옵션으로 연결
성공하는 경우. 처음 연결 실패 에러 메시지는 sqlca.sqlerrm.sqlerrmc에 저장된다.

**SQL_ERROR**: 처음 옵션으로 연결 실패하고, 두 번째 옵션으로도 연결 실패하는
경우. 두 번의 연결 실패에 대한 에러 메시지는 sqlca.sqlerrm.sqlerrmc에 연속하여
저장된다.

> ##### 주의 사항
>
> CONNECT 후 다시 CONNECT를 수행한다면 “Already connected” 오류가 발생한다. 따라서
> CONNECT 후 다시 CONNECT를 수행하려면 먼저 FREE 또는 DISCONNECT를 수행하여야
> 한다. 이 때, 데이터베이스 서버가 running 상태라면 DISCONNECT를, running 상태가
> 아니라면 FREE를 수행하여야 한다.
>
> USING절을 이용하여 연결 방식을 지정할 경우, CONNTYPE을 2 또는 3으로 지정한다면
> DSN 또는 PORT_NO를 함께 지정하더라도 DSN, PORT_NO 옵션은 무시되고 로컬
> 데이터베이스 서버로 연결을 시도한다.

##### 예제

데이터베이스 서버에 연결하는 다양한 예를 보여준다.

[예제 1] 다음은 사용자 이름과 사용자 암호를 이용하여 데이터베이스 서버에
연결하는 예를 보여준다. 이 경우, 다른 필요한 연결 정보는 환경 변수로부터 읽을
것이다.

\< 예제 프로그램: connect1.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
char usr[10];
char pwd[10];
EXEC SQL END DECLARE SECTION;

strcpy(usr, "SYS");
strcpy(pwd, "MANAGER"); 

EXEC SQL CONNECT :usr IDENTIFIED BY :pwd; 
```

[예제 2] 다음은 USING절에 연결 방식을 지정하여 데이터베이스 서버에 연결하는 예를
보여준다. usr과 pwd에 저장된 사용자 이름과 사용자 암호, conn_opt3에 저장된 연결
정보를 이용하여 데이터베이스 서버에 연결한다. 이 때 conn_opt3에 지정하지 않은
연결 정보는 환경 변수로부터 읽을 것이다.

\< 예제 프로그램: connect1.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
char usr[10];
char pwd[10];
char conn_opt3[100];
EXEC SQL END DECLARE SECTION;

strcpy(usr, "SYS");
strcpy(pwd, "MANAGER"); 
strcpy(conn_opt3, "DSN=192.168.11.12;CONNTYPE=1;PORT_NO=53000"); 

EXEC SQL CONNECT :usr IDENTIFIED BY :pwd USING :conn_opt3;  
```

[예제 3] 다음은 USING절에 연결 방식을 2개 지정하여 데이터베이스 서버에 연결하는
예를 보여준다. 먼저 usr과 pwd에 저장된 사용자 이름과 사용자 암호, conn_opt1에
저장된 연결 정보를 이용하여 데이터베이스 서버에 연결을 시도하고, 실패할 경우
같은 사용자 이름과 사용자 암호, conn_opt2에 저장된 연결 정보를 이용하여
데이터베이스 서버에 연결한다.

\< 예제 프로그램: connect2.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
char usr[10];
char pwd[10];
char conn_opt1[100];
char conn_opt2[100];
EXEC SQL END DECLARE SECTION;

strcpy(usr, "SYS");
strcpy(pwd, "MANAGER"); 
strcpy(conn_opt1, "DSN=192.168.11.12;CONNTYPE=1;PORT_NO=53000"); 
strcpy(conn_opt2, "DSN=192.168.11.22;CONNTYPE=1;PORT_NO=53000");

EXEC SQL CONNECT :usr IDENTIFIED BY :pwd USING :conn_opt1, :conn_opt2;  
if (sqlca.sqlcode == SQL_SUCCESS) /* check sqlca.sqlcode */
{
    printf("Success connection to altibase server with first option\n\n");
}
else if (sqlca.sqlcode == SQL_SUCCESS_WITH_INFO)
{
    /* fail connection with first option and then success connection with second option */
    printf("Success connection to altibase server with second option\n");
    printf("First connection error : [%d] %s\n\n", SQLCODE, sqlca.sqlerrm.sqlerrmc);
}
else
{
    printf("Fail connection to altibase server both first option and second option\n");
    printf("Error : [%d]\n", SQLCODE);
    printf("%s\n\n", sqlca.sqlerrm.sqlerrmc);
    exit(1);
}
```

#### DISCONNECT

데이터베이스 서버와의 연결을 해제한다.

##### 구문

```
EXEC SQL DISCONNECT;
```

##### 인자

없음

##### 설명

데이터베이스 서버와의 연결을 해제하고, 연결에 할당된 자원을 모두 해제한다.

##### 예제

다음 예제는 DISCONNECT문의 사용 예를 보여준다.

\< 예제 프로그램: connect1.sc \>

```
EXEC SQL DISCONNECT;
```

#### 예제 프로그램

##### connect1.sc 

$ALTIBASE_HOME/sample/APRE/connect1.sc 참고

##### 실행결과

```
$ is –f schema/schema.sql
$ make connect1
$ connect1
<CONNECT 1>
------------------------------------------------------
[Connect]
------------------------------------------------------
Success connection to altibase server

------------------------------------------------------
[Disconnect]
------------------------------------------------------
Success disconnection from altibase server
```

##### connect2.sc 

$ALTIBASE_HOME/sample/APRE/connect2.sc 참고

##### 실행결과

```
$ is –f schema/schema.sql
$ make connect2
$ connect2
<CONNECT 2>
------------------------------------------------------
[Connect With Two ConnOpt]
------------------------------------------------------
Fail connection to altibase server both first option and second option
Error : [-327730]
Failed first connection : Client unable to establish connection
Failed second connection : Client unable to establish connection
```

### 기본 내장 SQL문

기본 내장 SQL문에는 SELECT, UPDATE, INSERT, DELETE 등의 DML문과 CREATE, DROP,
ALTER 등의 DDL문이 있다.

#### SELECT

데이터베이스에서 조건에 맞는 레코드를 검색하여 호스트 변수에 저장한다. 기본적인
구문은 Altibase SQL의 SELECT문과 동일하나, 호스트 변수를 사용하기 위해
추가적으로 INTO절이 필요하다.

##### 구문

```
EXEC SQL SELECT [ ALL | DISTINCT ] <target_list>
INTO <host_var_list> 
FROM <table_expression> [ WHERE … ]; 
```

##### 인자

-   \<target_list\> : *SQL Reference*참조

-   \<*host_var_list*\> : 출력 호스트 변수와 출력 지시자 변수 리스트

-   \<table_expression\> : *SQL Reference*참조

##### 설명

호스트 변수가 배열이 아니라면 반환되는 레코드는 한 건이어야 한다. 한 건 이상이
반환될 경우 “Too many rows returned.” 오류가 발생한다. 이 경우 CURSOR문을
이용해야 한다.

호스트 변수가 배열이라면 반환되는 레코드 개수는 배열 크기보다 작거나 같아야
한다. 배열 크기보다 많은 건수가 반환될 경우 “Too many rows returned.” 오류가
발생한다. 이 경우 배열 크기를 크게 하던지 CURSOR문을 이용하여야 한다.

##### 수행 결과

<table>
	<tr>
		<th colspan="2">호스트 변수가 배열이 아닌 경우</th>
		<th colspan="2">호스트 변수가 배열인 경우</th>	
	</tr>
	<tr>
		<td>반환된 레코드 개수</td>
		<td>수행 결과</td>
		<td>반환된 레코드 개수</td>
		<td>수행 결과</td>
	</tr>
	<tr>
		<td>0</td>
		<td>SQL_NO_DATA</td>
		<td>0</td>
		<td>SQL_NO_DATA</td>
	</tr>
	<tr>
		<td rowspan="2">1</td>
		<td rowspan="2">SQL_SUCCESS</td>
		<td>배열 크기보다 작은 경우</td>
		<td>SQL_SUCCESS</td>
	</tr>
	<tr>
		<td>배열 크기와 같은 경우</td>
		<td>SQL_SUCCESS</td>
	</tr>
	<tr>
		<td>1보다 큰 경우</td>
		<td>SQL_ERROR</td>
		<td>배열 크기보다 큰 경우</td>
		<td>SQL_ERROR</td>
	</tr>
</table>

수행 결과가 SQL_NO_DATA의 경우 반환된 레코드 개수는 0개이므로 이 때의 호스트
변수 값은 무의미(garbage value)하다.

##### 제한 사항

-   입력 호스트 변수는 배열일 수 없다.

```
예) EXEC SQL BEGIN DECLARE SECTION;
int var1;
int var2[10];
int var3[10];
EXEC SQL END DECLARE SECTION;

EXEC SQL SELECT * INTO :var1 
FROM T1 WHERE i1 = :var3;	(X)
          또는
EXEC SQL SELECT * INTO :var2 
FROM T1 WHERE i1 = :var3;	(X)
```

-   GROUP BY 절에 CAST 연산자를 사용해서 호스트 변수의 타입을 명시한 표현식이
    존재하는 경우 해당 표현식을 TARGET 절에서 사용할 수 없다.

```
예) 
prepare select trunc(QTY - cast(:jstm as integer)) / cast(:unit as integer) from orders;		(O)

prepare SELECT trunc(QTY - cast(:jstm as integer)) from orders GROUP BY trunc(QTY - cast(:jstm as integer));	(X)
```

-   INTO절의 호스트 변수가 구조체의 배열이라면 출력 호스트 변수는 하나만 사용할
    수 있다. 자세한 설명은 5장 “호스트 변수 데이터 타입”을 참조한다.

-   INTO절의 호스트 변수가 varchar 타입의 배열일 때, 다른 출력 호스트 변수와
    함께 사용할 수 없다. 자세한 설명은 5장 “호스트 변수 데이터 타입”을 참조한다.

-   SELECT 문의 LIMIT 절에는 입력 호스트 변수만 사용 가능하고, 입력 지시자
    변수는 사용할 수 없다. 또한, 입력 호스트 변수의 데이터 타입은 int만
    지원한다.

##### 예제

다양한 SELECT 문의 사용 예를 보여준다.

[예제 1] 다음은 DNO가 s_dno의 값을 가지는 레코드를 검색하여 DNAME, DEP_LOCATION
칼럼 값을 각각 s_dname, s_dep_location 호스트 변수에 저장하는 예를 보여준다.

\< 예제 프로그램 : select.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
short s_dno;
char  s_dname[30+1];
char  s_dep_location[9+1];
EXEC SQL END DECLARE SECTION;

s_dno = 1001;
EXEC SQL SELECT DNAME, DEP_LOCATION 
INTO :s_dname, :s_dep_location
FROM DEPARTMENTS 
WHERE DNO = :s_dno;
```

[예제 2] 다음은 구조체 타입의 호스트 변수를 사용하는 경우로, DNO가 s_dno의 값을
가지는 레코드를 검색하여 모든 칼럼값을 각각 대응되는 s_department의 구성 요소에
저장하는 예를 보여준다.

\< 예제 프로그램 : hostvar.h \>

```
EXEC SQL BEGIN DECLARE SECTION;
typedef struct department
{
    short dno; 
    char  dname[30+1];
    char  dep_location[9+1];
    int   mgr_no;
} department;
EXEC SQL END DECLARE SECTION;
```

< 예제 프로그램 : select.sc >

```
/* specify path of header file */
EXEC SQL OPTION (INCLUDE=./include);
/* include header file for precompile */
EXEC SQL INCLUDE hostvar.h;

EXEC SQL BEGIN DECLARE SECTION;
short s_dno;
department s_department;
EXEC SQL END DECLARE SECTION;

s_dno = 1002;
EXEC SQL SELECT * 
INTO :s_department
FROM DEPARTMENTS 
WHERE DNO = :s_dno;
```

[예제 3] 다음은 T_LOB 테이블을 검색하여, INTEGER 칼럼을 sI1 호스트 변수에, CLOB
칼럼을 APRE_FILE_CREATE 옵션으로 생성한 sI2FName의 파일에 저장하는 예를
보여준다.

\<예제 프로그램 : clobSample.sc\>

```
EXEC SQL BEGIN DECLARE SECTION;
int          sI1;
char         sI2FName[33];
unsigned int sI2FOpt;
SQLLEN       sI2Ind;
EXEC SQL END DECLARE SECTION;

strcpy(sI2FName, aOutFileName);
sI2FOpt = APRE_FILE_CREATE;
 
EXEC SQL SELECT * INTO :sI1, CLOB_FILE :sI2FName OPTION :sI2FOpt INDICATOR :sI2Ind FROM T_LOB;
```

> \* BLOB, CLOB 타입의 칼럼의 데이터를 조회하여 파일로 저장하는 예제는 부록 A를
> 참조하기 바란다.

#### INSERT

테이블에 새로운 레코드를 삽입한다.

##### 구문

```
SQL Reference 참조
```

##### 인자

없음

##### 설명

VALUES절에 호스트 변수와 지시자 변수를 사용할 수 있다.

##### 예제

다양한 INSERT문의 사용 예를 보여준다.

[예제 1] 다음은 GOODS 테이블에 새로운 레코드를 삽입하는 예를 보여준다.

\< 예제 프로그램 : insert.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
char    s_gno[10+1];
char    s_gname[20+1];
char    s_goods_location[9+1];
int     s_stock;
double  s_price;
EXEC SQL END DECLARE SECTION;

strcpy(s_gno, "F111100002");
strcpy(s_gname, "XX-101");
strcpy(s_goods_location, "FD0003");
s_stock = 5000;
s_price = 9980.21;

EXEC SQL INSERT INTO GOODS 
VALUES (:s_gno, :s_gname, :s_goods_location, 
:s_stock, :s_price);
```

[예제 2] 다음은 구조체 타입의 호스트 변수를 사용하여 GOODS 테이블에 새로운
레코드를 삽입하는 예를 보여준다.

\< 예제 프로그램 : hostvar.h \>

```
EXEC SQL BEGIN DECLARE SECTION;
typedef struct goods
{
    char   gno[10+1];
    char   gname[20+1];
    char   goods_location[9+1];
    int    stock;
    double price;
} goods;
EXEC SQL END DECLARE SECTION;
```

\< 예제 프로그램 : insert.sc \>

```
/* specify path of header file */
EXEC SQL OPTION (INCLUDE=./include);
/* include header file for precompile */
EXEC SQL INCLUDE hostvar.h;

EXEC SQL BEGIN DECLARE SECTION;
goods   s_goods;
EXEC SQL END DECLARE SECTION;

strcpy(s_goods.gno, "F111100003");
strcpy(s_goods.gname, "XX-102");
strcpy(s_goods.goods_location, "AD0003");
s_goods.stock = 6000;
s_goods.price = 10200.96;

EXEC SQL INSERT INTO GOODS VALUES (:s_goods);
```

> \* 파일의 데이터를 읽어서 BLOB, CLOB 타입의 칼럼에 입력하는 예제는 부록 A를
> 참조하기 바란다.

#### UPDATE

조건을 만족하는 레코드를 찾아 명시한 칼럼들의 값을 변경한다.

##### 구문

```
SQL Reference 참조
```

##### 인자

없음

##### 설명

SET절과 WHERE절에 호스트 변수와 지시자 변수를 사용할 수 있다.

##### 제한 사항

-   배열 타입과 배열이 아닌 타입을 함께 사용할 수 없다. 예를 들어, SET절의
    호스트 변수가 배열 타입이라면 WHERE절의 호스트 변수도 배열 타입이어야 한다.

```
예) EXEC SQL BEGIN DECLARE SECTION;
int var1[10]; 
int var2[10];
int var3;
EXEC SQL END DECLARE SECTION;

EXEC SQL UPDATE T1 
SET I1 = :var1, I2 = :var2 
WHERE I1 = :var3;       	    (X)
```

##### 예제

다양한 UPDATE문의 사용 예를 보여준다.

[예제 1] 다음은 ENO 칼럼값이 s_eno와 같은 DNO, EMP_JOB 칼럼값을 각각 s_dno,
s_emp_job.arr 값으로 변경하는 예를 보여준다.

\< 예제 프로그램 : update.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
int      s_eno;
short    s_dno;
varchar  s_emp_job[15+1];
EXEC SQL END DECLARE SECTION;

s_eno = 2;
s_dno = 1001;
strcpy(s_emp_job.arr, "ENGINEER");
s_emp_job.len = strlen(s_emp_job.arr);

EXEC SQL UPDATE EMPLOYEES 
SET DNO      = :s_dno,
     EMP_JOB = :s_emp_job
WHERE ENO = :s_eno;
```

[예제 2] 다음은 구조체 타입의 호스트 변수를 사용하는 경우로, ENO 칼럼값이
s_eno와 같은 DNO, EMP_JOB, JOIN_DATE 칼럼값을 각각 s_employees.s_dno,
s_employees.s_emp_job.arr값과 SYSDATE로 변경하는 예를 보여준다.

\< 예제 프로그램 : hostvar.h \>

```
EXEC SQL BEGIN DECLARE SECTION;
typedef struct employee
{
      int        eno;
      char      ename[20+1];
      varchar   emp_job[15+1];
      char      emp_tel[15+1];
      short     dno;
      double    salary;
      char      sex;
      char      birth[4+1];
      char      join_date[19+1];
      char      status[1+1];
} employee;
EXEC SQL END DECLARE SECTION;
```

\< 예제 프로그램 : update.sc \>

```
/* specify path of header file */
EXEC SQL OPTION (INCLUDE=./include);
/* include header file for precompile */
EXEC SQL INCLUDE hostvar.h;

EXEC SQL BEGIN DECLARE SECTION;
employee s_employee;
EXEC SQL END DECLARE SECTION;

s_eno = 20;
s_employee.dno = 2001;
strcpy(s_employee.emp_job.arr, "TESTER");
s_employee.emp_job.len = strlen(s_employee.emp_job.arr);

EXEC SQL UPDATE EMPLOYEES 
SET DNO        = :s_employee.dno,
     EMP_JOB   = :s_employee.emp_job,
               JOIN_DATE = SYSDATE
           WHERE ENO = :s_eno;
```

#### DELETE

조건을 만족하는 레코드를 해당 테이블에서 삭제한다.

##### 구문

```
SQL Reference 참조
```

##### 인자

없음

##### 설명

WHERE절에 호스트 변수와 지시자 변수를 사용할 수 있다.

##### 예제

다음은 조건에 맞는 레코드를 EMPLOYEES 테이블에서 삭제하는 예를 보여준다.

\< 예제 프로그램 : delete.sc \>

```
EXEC SQL BEGIN DECLARE SECTION;
int      s_eno;
short    s_dno;
EXEC SQL END DECLARE SECTION;

s_eno = 5;
s_dno = 1000;

EXEC SQL DELETE FROM EMPLOYEES 
           WHERE ENO > :s_eno AND 
DNO > :s_dno AND 
EMP_JOB LIKE 'P%';
```

#### 예제 프로그램

##### select.sc

$ALTIBASE_HOME/sample/APRE/select.sc 참고

##### 실행결과

```
$ is –f schema/schema.sql
$ make select
$ ./select
<SELECT>
------------------------------------------------------
[Scalar Host Variables]                                           
------------------------------------------------------
DNO      DNAME                          DEP_LOCATION              
------------------------------------------------------
1001     RESEARCH DEVELOPMENT DEPT 1    New York 

------------------------------------------------------
[Structure Host Variables]                                        
------------------------------------------------------------------
DNO      DNAME                          DEP_LOCATION       MGR_NO 
------------------------------------------------------------------
1002     RESEARCH DEVELOPMENT DEPT 2    Sydney             13

------------------------------------------------------
[Error Case : Scalar Host Variables]                              
------------------------------------------------------
Error : [-594092] Returns too many rows
```

##### insert.sc 

$ALTIBASE_HOME/sample/APRE/insert.sc 참고

##### 실행결과

```
$ is –f schema/schema.sql
$ make insert
$ ./insert
<INSERT>
------------------------------------------------------
[Scalar Host Variables]                                           
------------------------------------------------------
1 rows inserted

------------------------------------------------------
[Structure Host Variables]                                        
------------------------------------------------------
1 rows inserted
```

##### update.sc 

$ALTIBASE_HOME/sample/APRE/update.sc 참고

##### 실행결과

```
$ is –f schema/schema.sql
$ make update
$ ./update
<UPDATE>
------------------------------------------------------
[Scalar Host Variables]                                           
------------------------------------------------------
1 rows updated

------------------------------------------------------
[Structure Host Variables]                                        
------------------------------------------------------
1 rows updated
```

##### delete.sc 

$ALTIBASE_HOME/sample/APRE/delete.sc 참고

##### 실행결과

```
$ is –f schema/schema.sql
$ make delete
$ ./delete
<DELETE>
------------------------------------------------------
[Scalar Host Variables]                                           
------------------------------------------------------
7 rows deleted
```

### 기타 내장 SQL문

작업 제어문, 시스템 제어문, 트랜잭션 처리문 등과 INCLUDE 문, THREADS OPTION문
등이 여기에 속한다.

#### AUTOCOMMIT

##### 구문

```
EXEC SQL AUTOCOMMIT { ON | OFF };
```

##### 인자

없음

##### 설명

현재 세션의 AUTOCOMMIT 모드를 변경한다.

##### 예제

다음은 AUTOCOMMIT 모드를 변경하는 예를 보여준다.

```
EXEC SQL AUTOCOMMIT ON; -- AUTOCOMMIT 모드로 변경
EXEC SQL AUTOCOMMIT OFF; -- NON-AUTOCOMMIT 모드로 변경
```

#### COMMIT

##### 구문

```
EXEC SQL COMMIT;
```

##### 인자

없음

##### 설명

현재의 트랜잭션을 성공적으로 종료한다. 트랜잭션에서 수행된 변경 연산의 결과는
데이터베이스에 영구히 저장된다.

> ##### 주의 사항
>
> 현재 세션이 AUTOCOMMIT 모드이더라도 오류는 발생하지 않는다.
>

##### 예제

다음 예제는 COMMIT문의 사용 예를 보여준다.

```
EXEC SQL COMMIT;
```

#### SAVEPOINT 

##### 구문

```
EXEC SQL SAVEPOINT <savepoint_name>;
```

##### 인자

\<savepoint_name\>: 저장점 이름

##### 설명

저장점은 지금까지의 트랜잭션을 임시 저장하는 것이다. 이 내장 SQL문은 트랜잭션
내에서 롤백 할 지점을 명시적으로 지정하기 위한 저장점을 지정한다.

> ##### 주의 사항
>
> 현재 세션이 AUTOCOMMIT 모드이더라도 오류는 발생하지 않는다.
>

##### 예제

다음 예제는 SAVEPOINT문의 사용 예를 보여준다.

```
EXEC SQL SAVEPOINT sp;
```

#### ROLLBACK

##### 구문

```
EXEC SQL ROLLBACK [ TO SAVEPOINT <savepoint_name> ];
```

##### 인자

\<savepoint_name\> : 저장점 이름

##### 설명

가장 최근의 DDL문이나 COMMIT문 이전 상태로 트랜잭션을 철회시켜, 트랜잭션에서
수행된 변경 연산의 결과는 취소된다.

저장점 이름을 지정하면, 현재부터 그 지점까지의 트랜잭션만 철회된다.

> ##### 주의 사항
>
> 현재 세션이 AUTOCOMMIT 모드이더라도 오류는 발생하지 않는다.
>

##### 예제

다음 예제는 ROLLBACK문의 사용 예를 보여준다.

```
EXEC SQL ROLLBACK;
또는
EXEC SQL ROLLBACK TO SAVEPOINT sp;
```

#### BATCH

연결 속성을 변경하여 Batch Processing을 작동시키거나 정지 시킬 수 있다.

##### 구문

```
EXEC SQL BATCH { ON | OFF };
```

##### 인자

없음

##### 설명

배치 처리 모드를 활성화하면 SELECT문이나 COMMIT이 수행되기 전까지 내장 SQL문의
수행(서버로의 전송)을 지연한다. 이것은 COMMIT되지 않은 INSERT, UPDATE,
DELETE문은 같은 트랜잭션에서만 읽을 수 있다는 점을 이용한 것이다.

INSERT, UPDATE, DELETE문이 자주 발생하는 경우 배치 처리 모드를 활성화하면 성능
향상을 기대할 수 있다.

##### 예제

다음 예제는 BATCH문의 사용 예를 보여준다.

```
EXEC SQL BATCH ON;	- 배치 처리 모드로 동작
EXEC SQL BATCH OFF; 	- 배치 처리 모드를 사용하지 않음
```

#### FREE

데이터베이스 서버와의 연결 및 내장 SQL문 수행 시 할당 받았던 자원을 모두
해제한다.

##### 구문

```
EXEC SQL FREE;
```

##### 인자

없음

##### 설명

CONNECT 후 내장 SQL문을 수행하다가 서버와의 연결이 끊어져서 다시 CONNECT를
수행하려면 먼저 FREE문을 수행하여야 한다. 이 때, 데이터베이스 서버는 running
상태가 아니어야 한다. 만약 데이터베이스 서버가 running 상태라면 FREE문 대신
DISCONNECT문을 수행하여야 한다.

##### 예제

다음 예제는 FREE문의 사용 예를 보여준다.

\< 예제 프로그램 : free.sc \>

```
EXEC SQL FREE;
```

#### INCLUDE

전처리 시 포함할 헤더파일을 지정한다.

##### 구문

```
EXEC SQL INCLUDE <filename>;
```

##### 인자

-   \<*filename*\> : 전처리 시 사용할 헤더 파일의 이름

##### 설명

호스트 변수와 호스트 변수의 데이터 타입으로 사용할 타입 정의는 전처리를 하기
위해 APRE가 알아야 할 중요한 정보이다. 따라서, 호스트 변수가 선언되어 있거나
호스트 변수 타입으로 사용할 타입 정의가 되어 있는 헤더 파일은 반드시 INCLUDE문을
이용하여 include하여야 한다(-parse 전처리 명령행 옵션을 “full”로 설정하지
않는다면).

이 구문은 전처리 할 파일(.sc)과 EXEC SQL INCLUDE로 포함한 헤더파일(.h) 내에서
사용할 수 있으며 \#include로 포함한 헤더파일 내에서는 사용할 수 없다.

##### 제한 사항

헤더 파일은 상호 참조할 수 없다. 즉, myheader1.h가 myheader2.h를 참조하고
myheader2.h가 myheader1.h를 참조해서 사용할 수 없다.

예) <myheader1.h>

```
EXEC SQL INCLUDE myheader2.h;
…

<myheader2.h>
EXEC SQL INCLUDE myheader1.h;	(X)
…
```

##### 예제

다음은 전처리 시 사용할 헤더파일을 INCLUDE 구문을 이용하여 지정하는 예를
보여준다.

\< 예제 프로그램 : insert.sc \>

```
EXEC SQL INCLUDE hostvar.h;
```

#### 예제 프로그램

##### free.sc 

$ALTIBASE_HOME/sample/APRE/free.sc 참고

##### 실행 결과

```
$ is –f schema/schema.sql
$ make free
$ ./free
<FREE>
------------------------------------------------------
[Connect]
------------------------------------------------------
Success connection to altibase server

------------------------------------------------------
[Free]
------------------------------------------------------
Error : [-331796] Function sequence error

------------------------------------------------------
[Reconnect]
------------------------------------------------------
Error : [-589826] Already connected
```

### OPTION문

C/C++ 전처리기에서 제공하는 다양한 옵션들을 OPTION문을 이용하여 지정할 수 있다.

#### INCLUDE

전처리 시 사용하는 헤더 파일의 위치를 지정하기 위해서 내장 SQL문은 다양한 방법을
제공한다. 그 중 하나가 바로 INCLUDE OPTION문이다.

##### 구문

```
EXEC SQL OPTION (INCLUDE = <pathname>);
```

##### 인자

-   \<*pathname*\> : 전처리 시 사용할 헤더 파일의 위치

##### 설명

전처리 시 사용할 헤더 파일의 위치를 지정한다.

여러 개의 위치를 지정하기 위해서는 콤마(,)로 구분한다.

이 OPTION문은 반드시 INCLUDE문 이전에 선언하여야 한다.

##### 예제

다음은 hostvar.h의 위치인 ./include 디렉토리를 INCLUDE OPTION문을 이용하여
지정하고 hostvar.h를 include하는 예를 보여준다.

\< 예제 프로그램 : insert.sc \>

```
EXEC SQL OPTION (INCLUDE=./include);
EXEC SQL INCLUDE hostvar.h;
```

#### THREADS

내장 SQL문은 멀티쓰레드 프로그램을 지원한다. 이 OPTION문은 전처리 할 파일이
멀티쓰레드 프로그램인지 아닌지 판단하는 근거를 전처리기에게 제공한다.

##### 구문

```
EXEC SQL OPTION (THREADS = { TRUE | FALSE });
```

##### 인자

없음

##### 설명

-   TRUE : 전처리 할 파일이 멀티쓰레드 프로그램인 경우

-   FALSE : 전처리 할 파일이 멀티쓰레드 프로그램이 아닌 경우

기본적으로 THREADS OPTION값은 FALSE이다. 전처리 할 파일이 멀티쓰레드
프로그램이라면 THREADS OPTION값을 TRUE로 지정하여야 한다. 멀티쓰레드 프로그램
전처리 시 command line에서 -mt 옵션을 지정한다면 이 OPTION문은 생략 가능하다.

##### 예제

다음은 전처리 할 파일이 멀티쓰레드 프로그램일 경우 OPTION문을 이용하여 THREADS
OPTION값을 TRUE로 지정하는 예를 보여준다.

\< 예제 프로그램 : mt1.sc \>

```
EXEC SQL OPTION (THREADS=TRUE); 
```

7.실행 시간 에러 처리 
--------------------

### 개요

응용 프로그램 안에서 실행 시간 에러 (run-time error)에 대한 처리가 가능해야
한다. 내장 SQL문은 SQLCODE, SQLSTATE 등의 변수와 WHENEVER문 등의 지원으로 실행
시간 에러 처리에 대한 방법을 프로그래머에게 제공한다.

#### 실행결과 

내장 SQL문 수행 후 실행결과는 **sqlca.sqlcode**에 저장되며, 그 값은 다음과 같다.

-   **SQL_SUCCESS**  
    내장 SQL문을 성공적으로 수행한 경우

-   **SQL_SUCCESS_WITH_INFO**  
    내장 SQL문을 수행하였으나 warning이 발견된 경우

-   **SQL_NO_DATA**  
    SELECT문이나 FETCH문 수행 후 반환되는 레코드가 없는 경우

-   **SQL_ERROR**  
    내장 SQL문 수행시 에러가 발생한 경우

### sqlca

sqlca는 전처리 시 선언된, ulpSqlca 구조체의 인스턴스이다. ulpSqlca 는 내장 SQL문
수행 결과를 저장하기 위한 구조체로 ulpLibInterface.h 파일에 정의되어 있다.
프로그램 개발자는 응용 프로그램 안에서 sqlca 변수를 이용해 내장 SQL문의 수행
결과를 참조할 수 있다.

#### 자료 구조 

```
typedef struct ulpSqlca
{
    char sqlcaid[8];  /* not used */
    int  sqlcabc;     /* not used */
    int  sqlcode;
    struct
    {
        short sqlerrml;
        char sqlerrmc[2048];
    }sqlerrm;
    char sqlerrp[8];  /* not used */
    int  sqlerrd[6];
    char sqlwarn[8]; /* not used */
    char sqlext[8];  /* not used */
} ulpSqlca;
```

#### 구성 요소

ulpSqlca 구조체는 여러 가지 구성 요소를 포함한다. 이 구성 요소들 중에는 현재
사용하지 않고 미래를 위해 예약된 구성 요소도 있는데, 그 구성 요소에 대한 설명은
생략한다.

각 구성 요소의 의미는 다음과 같다.

##### sqlcode

내장 SQL문의 실행결과가 저장된다. 내장 SQL문의 실행결과는 다음값들 중 하나일
것이다.

-   SQL_SUCCESS

-   SQL_SUCCESS_WITH_INFO

-   SQL_NO_DATA

-   SQL_ERROR

##### sqlerrm.sqlerrmc 

에러메시지가 저장된다. 저장할 수 있는 에러메시지의 최대길이는 2048 bytes 이다.

##### sqlerrm.sqlerrml 

반환된 에러메시지 길이가 저장된다.

##### sqlerrd[2] 

INSERT, UPDATE, DELETE 연산 시 영향 받은 레코드 개수가 저장된다.

SELECT문이나 FETCH문 수행 시 출력 호스트 변수가 배열일 경우, 반환되는 레코드
개수가 저장된다. 이 경우 반환되는 레코드 개수는 누적되지 않고 현재 FETCH된
레코드 개수이다. 따라서 이 값은 호스트 변수의 배열 크기보다 클 수 없다.

##### sqlerrd[3] 

배열 타입의 입력 호스트 변수 사용시 내장 SQL문 수행 후 이 값을 참조할 수 있다.
이 변수에는 성공적으로 처리된 횟수가 저장된다. 따라서 이 값은 배열 크기보다 클
수 없다. 예를 들어 배열 크기 3의 입력 호스트 변수를 사용하여 UPDATE를
수행하였다고 할 때, 배열요소의 0번째는 성공, 1번째는 실패, 2번째는 성공한 경우
이 변수에는 2가 저장된다. 반면에, sqlca.sqlerrd[2]에는 UPDATE된 레코드 개수가
저장되기 때문에 2보다 큰 값이 저장될 수도 있다.

> #### 주의 사항
>
> -   모든 내장 SQL문 수행 후 반드시 sqlca.sqlcode 값을 체크하여 정확한 에러처리를
>     해주어야 한다.
>
> -   SELECT문에서 문자형 타입의 칼럼의 값을 fetch할 경우, 출력 호스트 변수의
>     크기가 대응되는 칼럼 크기 + 1 보다 작을 경우, 호스트 변수에는 호스트 변수
>     크기만큼 데이터가 잘려서 저장될 수도 있는데, 이 때의 sqlca.sqlcode값은
>     SQL_SUCCESS_WITH_INFO이다.
>
> -   UPDATE, DELETE 연산 시 영향받은 레코드 개수가 0개이면 이 때의
>     sqlca.sqlcode값은 SQL_NO_DATA이다. UPDATE, DELETE 연산 시 영향 받은 레코드
>     개수 확인 방법은 sqlca.sqlerrd[2]값을 참조하면 되고, 이 경우 이 값은 0이다.
>

### SQLCODE

SQLCODE에는 내장 SQL문 수행 결과가 SQL_ERROR일 경우 에러코드가 저장된다.

#### 자료 구조

```
int SQLCODE;
```

#### 설명

0: 내장 SQL문을 성공적으로 수행한 경우. 즉, sqlca.sqlcode 값이 SQL_SUCCESS 인
경우

1: 내장 SQL문을 수행하였으나 warning이 발견된 경우. 즉, sqlca.sqlcode 값이
SQL_SUCCESS_WITH_INFO 인 경우

100: SELECT문이나 FETCH문 수행 후 반환되는 레코드가 없는 경우. 즉, sqlca.sqlcode
값이 SQL_NO_DATA인 경우

\-1: 내장 SQL문 수행 시 에러가 발생하였지만 해당 에러코드가 없는 경우. 이 때의
sqlca.sqlcode 값은 SQL_ERROR 이다.

\-그 외 음수값: 내장 SQL문 수행시 에러가 발생한 경우. 이 경우, 이 값은 실제 에러
코드이다.

#### 에러 코드

에러 코드는 에러가 발생한 위치에 따라 데이터베이스 서버에서 발생한 에러와 내장
SQL문에서 발생한 에러로 구분된다.

##### 내장 SQL문 에러

실행 시간에 내장SQL문에서 발생한 에러로 C/C++ 전처리기(APRE)가 에러코드를
반환한다. 아래 설명 외의 에러코드는 *Error Message Reference*를 참조하기 바란다.

-   \-589826 : 같은 연결 이름으로 이미 연결되어 있는 경우

-   \-589841 : 연결 이름의 길이가 50 bytes를 초과하는 경우

-   \-589857 : 선언되지 않은 커서 이름으로 다른 커서 처리 SQL문을 수행하는 경우

-   \-589858 : PREPARE되지 않은 SQL문 식별자로 다른 동적 SQL문을 수행하는 경우

#####  데이터베이스 서버 에러

실행 시간에 데이터베이스 서버에서 발생한 에러로 데이터베이스 서버에서 에러코드를
반환한다. 각 에러코드에 대한 자세한 설명은 *Error Message Reference*를 참조하기
바란다.

> #### 주의 사항
>
> SQLCODE에는 에러코드가 10진수 음수값으로 저장되어 있는 반면 *Error Message
> Reference* 에는 에러코드가 16진수 양수값과 10진수 양수값으로 설명되어 있다.
> 따라서 *Error Message Reference* 참조 시 SQLCODE의 절대값 또는 절대값을 16진수로
> 변환하여 참조하여야 한다.

### SQLSTATE

SQLSTATE에는 상태코드가 저장된다. 이 상태코드를 통해 어떤 에러가 발생했는지,
또는 어떤 warning이 발견되었는지 알 수 있다. SQLSTATE는 내장 SQL문의 결과가
SQL_ERROR 또는 SQL_SUCCESS_WITH_INFO 인 경우 참조할 수 있다.

#### 자료구조

```
char SQLSTATE[6];
```

#### 상태코드

-   00000 – 내장 SQL문을 성공적으로 수행한 경우

-   01004 – 호스트 변수가 타입일 때, 호스트 변수의 크기를 대응되는 칼럼의 크기 +
    1 보다 작게 지정한 경우. 이 때 반환되는 데이터는 호스트 변수의 크기만큼
    잘려서 저장된다.

-   07006 – 호스트 변수 타입이 대응되는 칼럼 타입과 타입 호환되지 않는 타입을
    사용한 경우

-   07009 – 칼럼 개수와 대응되는 호스트 변수 개수가 일치하지 않은 경우

-   08001 – 데이터베이스 서버가 startup 되어 있지 않은 경우

-   08S01 – 데이터베이스 서버와의 연결이 끊어진 경우

-   21S01 – INSERT구문의 컬럼 개수와 입력 호스트 변수의 개수가 일치하지 않은
    경우

-   22002 – 지시자 변수를 지정하지 않은 상태에서 NULL 데이터가 반환된 경우

-   HY000 – 일반적인 에러

-   HY001 – 메모리 할당 시 에러가 발생한 경우

-   HY009 – 호스트 변수와 지시자 변수가 널 포인터인 경우

-   HY010 – OPEN 되지 않은 커서를 FETCH 하는 경우

-   HY090 – 지시자 변수의 값이 유효하지 않은 경우

### WHENEVER문

APRE는 실행시간 에러 처리를 위한 방법으로 WHENEVER문을 지원한다.

#### 구문

```
EXEC SQL WHENEVER <condition> <action>;
```

##### 인자

-   \<*condition*\> : 내장 SQL문 실행결과

-   \<*action*\> : 내장 SQL문 실행결과에 따른 처리 방법

#### 조건

WHENEVER문에서 지정할 수 있는 조건은 다음과 같다.

##### SQLERROR

내장 SQL문 수행 시 에러가 발생한 경우. 즉, sqlca.sqlcode 값이 SQL_ERROR일 때를
의미한다.

##### NOT FOUND

SELECT문이나 FETCH문 수행 후 반환되는 레코드가 없는 경우. 즉, sqlca.sqlcode 값이
SQL_NO_DATA일 때를 의미한다.

#### 처리 방법

내장 SQL문 수행 결과가 WHENEVER문에서 지정한 조건과 일치하면 지정한 처리 방법이
실행된다.

WHENEVER문에서 지정할 수 있는 처리 방법은 다음과 같다.

##### CONTINUE

계속 진행한다.

##### DO BREAK

현재의 반복문을 빠져나가서 계속 진행한다. 이것은 반복문 안에서 ‘break;’ 명령을
사용한 것과 동일한 효과를 가진다. ‘DO BREAK’는 반복문 안에서만 지정 가능하며,
반복문이 끝나면 이 WHENEVER문은 효력을 잃는다.

##### DO CONTINUE

현재의 반복문 처음으로 이동하여 계속 진행한다. 이것은 반복문 안에서 ‘continue;’
명령을 사용한 것과 동일한 효과를 가진다. ‘DO CONTINUE’는 반복문 안에서만 지정
가능하며, 반복문이 끝나면 이 WHENEVER문은 효력을 잃게 된다.

##### DO *function_name*

function_name으로 지정한 함수를 호출한다.

##### GOTO label_name

*label_name*의 위치로 이동하여 계속 진행한다.

##### STOP

데이터베이스 서버와의 연결을 해제하고 현재 프로그램을 종료한다.

#### 설명

WHENEVER문의 적용범위는 프로그램의 흐름과는 다르며, 현재 파일 내에서만 유효하다.

WHENEVER문은 적용하고자 하는 내장 SQL문 이전에 선언하여야 한다.

WHENEVER문이 선언되면 현재범위(current scope)와 현재의 하위범위(lower scope)에서
수행되는 모든 내장 SQL문의 수행 결과가 영향을 받는다. 즉, 내장 SQL문 수행 결과가
WHENEVER문에서 지정한 조건과 일치하면 지정한 action을 수행하게 된다.

WHENEVER문은 2가지 조건 즉, ‘SQLERROR’와 ‘NOT FOUND’에 대해 독립적이다.

WHENEVER문을 선언한 범위를 빠져나오면 그 WHENEVER문은 효력을 상실하며, 그 범위
바깥의 내장 SQL문은 빠져 나온 현재범위(current scope) 또는 현재의 상위범위(upper
scope)에 선언된 WHENEVER문의 영향을 받는다.

WHENEVER문이 선언된 범위(scope)에서 같은 조건으로 다른 WHENEVER문이 선언된다면
이전 WHENEVER문은 효력을 상실하고 새로 선언된 WHENEVER문이 적용된다.

같은 조건의 WHENEVER문이 중첩되어 선언된 경우, 가장 가까운 위치의 WHENEVER문의
영향을 받는다.

WHENEVER문은 connection에 독립적이다. 즉, connection이 하나 이상인 파일에서
WHENEVER문을 선언하면 connection이 다르더라도 해당 범위의 모든 내장 SQL문이
영향을 받는다.

전역에 WHENEVER문을 선언하였다면 현재 파일의 모든 내장 SQL문의 수행 결과가
영향을 받는다.

### 예제 프로그램

##### runtime_error_check.sc

$ALTIBASE_HOME/sample/APRE/runtime_error_check.sc 참고

##### 실행결과

```
$ is –f schema/schema.sql
$ make runtime_error_check
$ ./runtime_error_check
<RUNTIME ERROR CHECK>
------------------------------------------------------
[SQL_SUCCESS]                                                     
------------------------------------------------------
sqlca.sqlcode = 0

-----------------------------------------------------------
 [SQL_SUCCESS_WITH_INFO With SQLSTATE=01004]                      
-----------------------------------------------------------
sqlca.sqlcode          = 1
sqlca.sqlerrm.sqlerrmc = String data right truncated.
SQLSTATE               = 01004
SQLCODE                = 1

-----------------------------------------------------------
[SQL_ERROR With SQLSTATE=22002]                      
-----------------------------------------------------------
sqlca.sqlcode          = -1
sqlca.sqlerrm.sqlerrmc = Indicator variable required but not supplied.
SQLSTATE               = 22002
SQLCODE                = -331841

-----------------------------------------------------------
[SQL_NO_DATA With SELECT]                                        
-----------------------------------------------------------
sqlca.sqlcode          = 100
sqlca.sqlerrm.sqlerrmc = Not found data
SQLSTATE               = 02000
SQLCODE                = 100

-----------------------------------------------------------
[SQL_NO_DATA With FETCH]                                         
-----------------------------------------------------------
sqlca.sqlcode          = 100
sqlca.sqlerrm.sqlerrmc = Not found data
SQLSTATE               = 02000
SQLCODE                = 100
2 rows fetched

-----------------------------------------------------------
[SQL_ERROR]                                                      
-----------------------------------------------------------
sqlca.sqlcode          = -1
sqlca.sqlerrm.sqlerrmc = The row already exists in a unique index.
SQLSTATE               = 23000
SQLCODE                = -69720

-----------------------------------------------------------
[SQL_ERROR With SQLSTATE=HY010]                                  
-----------------------------------------------------------
sqlca.sqlcode          = -1
sqlca.sqlerrm.sqlerrmc = Function sequence error.
SQLSTATE               = HY010
SQLCODE                = -331796

-----------------------------------------------------------
[sqlca.sqlerrd[2]]                                               
-----------------------------------------------------------
sqlca.sqlcode    = 0
sqlca.sqlerrd[2] = 12

-----------------------------------------------------------
sqlca.sqlerrd[3] With Array In-Binding]                          
-----------------------------------------------------------
sqlca.sqlcode    = 0
sqlca.sqlerrd[2] = 12
sqlca.sqlerrd[3] = 3
```

##### whenever1.sc 

$ALTIBASE_HOME/sample/APRE/whenever1.sc 참고

##### whenever2.sc 

$ALTIBASE_HOME/sample/APRE/whenever2.sc 참고

##### 실행결과

```
$ is –f schema/schema.sql
$ make whenever
$ ./whenever
<WHENEVER>
Success connection

------------------------------------------------------------------
DNO      DNAME                          DEP_LOCATION       MGR_NO 
------------------------------------------------------------------
1001     PAPER TEAM                     New York           16
1002     RESEARCH DEVELOPMENT DEPT 2    Sydney             13
1003     SOLUTION DEVELOPMENT DEPT      Japan              14
2001     QUALITY ASSURANCE DEPT         Seoul              17
3001     CUSTOMER SUPPORT DEPT          London             4
3002     PRESALES DEPT                  Peking             5
4001     MARKETING DEPT                 Seoul              8
4002     BUSINESS DEPT                  LA                 7 
```

