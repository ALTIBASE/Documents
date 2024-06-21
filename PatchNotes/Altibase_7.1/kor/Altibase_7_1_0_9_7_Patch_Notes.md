Altibase 7.1.0.9.7 Patch Notes
==============================

<br/>

<br/>

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

# Table of Contents

- [Fixed Bugs](#fixed-bugs)
  - [BUG-50005 aku 실행 시 옵션을 입력하지 않거나 잘못된 옵션을 입력했을 때 오류 메시지를 출력하지 않고 help 메시지만 출력하도록 변경하였습니다.](#bug-50005aku-%EC%8B%A4%ED%96%89-%EC%8B%9C-%EC%98%B5%EC%85%98%EC%9D%84-%EC%9E%85%EB%A0%A5%ED%95%98%EC%A7%80-%EC%95%8A%EA%B1%B0%EB%82%98-%EC%9E%98%EB%AA%BB%EB%90%9C-%EC%98%B5%EC%85%98%EC%9D%84-%EC%9E%85%EB%A0%A5%ED%96%88%EC%9D%84-%EB%95%8C-%EC%98%A4%EB%A5%98-%EB%A9%94%EC%8B%9C%EC%A7%80%EB%A5%BC-%EC%B6%9C%EB%A0%A5%ED%95%98%EC%A7%80-%EC%95%8A%EA%B3%A0-help-%EB%A9%94%EC%8B%9C%EC%A7%80%EB%A7%8C-%EC%B6%9C%EB%A0%A5%ED%95%98%EB%8F%84%EB%A1%9D-%EB%B3%80%EA%B2%BD%ED%95%98%EC%98%80%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-50249 PICL 라이브러리에서 운영체제의 자원 상태를 수집할 때, 예외 상황이 발생하면 altimon.log에 기록해야 합니다. (AIX, HP-UX)](#bug-50249picl-%EB%9D%BC%EC%9D%B4%EB%B8%8C%EB%9F%AC%EB%A6%AC%EC%97%90%EC%84%9C-%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C%EC%9D%98-%EC%9E%90%EC%9B%90-%EC%83%81%ED%83%9C%EB%A5%BC-%EC%88%98%EC%A7%91%ED%95%A0-%EB%95%8C-%EC%98%88%EC%99%B8-%EC%83%81%ED%99%A9%EC%9D%B4-%EB%B0%9C%EC%83%9D%ED%95%98%EB%A9%B4-altimonlog%EC%97%90-%EA%B8%B0%EB%A1%9D%ED%95%B4%EC%95%BC-%ED%95%A9%EB%8B%88%EB%8B%A4-aix-hp-ux)
  - [BUG-50849 ODBC 이스케이프 시퀀스(escape sequence)에 대문자를 사용하면 parse error 에러가 발생합니다.](#bug-50849odbc-%EC%9D%B4%EC%8A%A4%EC%BC%80%EC%9D%B4%ED%94%84-%EC%8B%9C%ED%80%80%EC%8A%A4escape-sequence%EC%97%90-%EB%8C%80%EB%AC%B8%EC%9E%90%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EB%A9%B4-parse-error-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-50875 Logical Ager가 삭제해야 할 인덱스 키를 찾지 못할 때 Altibase 서버가 비정상 종료합니다.](#bug-50875logical-ager%EA%B0%80-%EC%82%AD%EC%A0%9C%ED%95%B4%EC%95%BC-%ED%95%A0-%EC%9D%B8%EB%8D%B1%EC%8A%A4-%ED%82%A4%EB%A5%BC-%EC%B0%BE%EC%A7%80-%EB%AA%BB%ED%95%A0-%EB%95%8C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-50878 aexport.properties 파일에서 ILOADER\_FIELD\_TERM, ILOADER\_ROW\_TERM 프로퍼티의 값을 변경합니다.](#bug-50878aexportproperties-%ED%8C%8C%EC%9D%BC%EC%97%90%EC%84%9C-iloader_field_term-iloader_row_term-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0%EC%9D%98-%EA%B0%92%EC%9D%84-%EB%B3%80%EA%B2%BD%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-50891 사용하지 않는 INSPECTION\_LARGE\_HEAP\_THRESHOLD 프로퍼티를 삭제하였습니다.](#bug-50891%EC%82%AC%EC%9A%A9%ED%95%98%EC%A7%80-%EC%95%8A%EB%8A%94-inspection_large_heap_threshold-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0%EB%A5%BC-%EC%82%AD%EC%A0%9C%ED%95%98%EC%98%80%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-50905 연결 스트링에 DSN 속성을 입력하지 않으면 Invalid attribute value. 에러가 발생합니다.](#bug-50905%EC%97%B0%EA%B2%B0-%EC%8A%A4%ED%8A%B8%EB%A7%81%EC%97%90-dsn-%EC%86%8D%EC%84%B1%EC%9D%84-%EC%9E%85%EB%A0%A5%ED%95%98%EC%A7%80-%EC%95%8A%EC%9C%BC%EB%A9%B4-invalid-attribute-value-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-50907 조인에서 하이브리드 파티션드 테이블이 사용되고 SERIAL\_EXECUTE\_MODE 프로퍼티가 1일 때, 결과 값에 오류가 발생할 수 있습니다.](#bug-50907%EC%A1%B0%EC%9D%B8%EC%97%90%EC%84%9C-%ED%95%98%EC%9D%B4%EB%B8%8C%EB%A6%AC%EB%93%9C-%ED%8C%8C%ED%8B%B0%EC%85%98%EB%93%9C-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%9D%B4-%EC%82%AC%EC%9A%A9%EB%90%98%EA%B3%A0-serial_execute_mode-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0%EA%B0%80-1%EC%9D%BC-%EB%95%8C-%EA%B2%B0%EA%B3%BC-%EA%B0%92%EC%97%90-%EC%98%A4%EB%A5%98%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-50914 altibase\_store\_result, altibase\_next\_result를 순차적으로 실행할 때, 두 번째 결과 집합에서 HY010 Function sequence error. 에러가 발생합니다.](#bug-50914altibase_store_result-altibase_next_result%EB%A5%BC-%EC%88%9C%EC%B0%A8%EC%A0%81%EC%9C%BC%EB%A1%9C-%EC%8B%A4%ED%96%89%ED%95%A0-%EB%95%8C-%EB%91%90-%EB%B2%88%EC%A7%B8-%EA%B2%B0%EA%B3%BC-%EC%A7%91%ED%95%A9%EC%97%90%EC%84%9C-hy010-function-sequence-error-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-50919 altibase\_stmt\_next\_result 함수를 실행할 때, 두 번째 결과 집합에서 HY010 Function sequence error. 에러가 발생합니다.](#bug-50919altibase_stmt_next_result-%ED%95%A8%EC%88%98%EB%A5%BC-%EC%8B%A4%ED%96%89%ED%95%A0-%EB%95%8C-%EB%91%90-%EB%B2%88%EC%A7%B8-%EA%B2%B0%EA%B3%BC-%EC%A7%91%ED%95%A9%EC%97%90%EC%84%9C-hy010-function-sequence-error-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-50920 데이터 업로드 시 에러가 발생한 경우, 어느 칼럼에서 발생했는지 알 수 없습니다.](#bug-50920%EB%8D%B0%EC%9D%B4%ED%84%B0-%EC%97%85%EB%A1%9C%EB%93%9C-%EC%8B%9C-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%9C-%EA%B2%BD%EC%9A%B0-%EC%96%B4%EB%8A%90-%EC%B9%BC%EB%9F%BC%EC%97%90%EC%84%9C-%EB%B0%9C%EC%83%9D%ED%96%88%EB%8A%94%EC%A7%80-%EC%95%8C-%EC%88%98-%EC%97%86%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-50923 SQLPrepare 함수의 SQL 텍스트 문자열 인자가 빈 문자열일 때 에러가 발생하지 않습니다.](#bug-50923sqlprepare-%ED%95%A8%EC%88%98%EC%9D%98-sql-%ED%85%8D%EC%8A%A4%ED%8A%B8-%EB%AC%B8%EC%9E%90%EC%97%B4-%EC%9D%B8%EC%9E%90%EA%B0%80-%EB%B9%88-%EB%AC%B8%EC%9E%90%EC%97%B4%EC%9D%BC-%EB%95%8C-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%98%EC%A7%80-%EC%95%8A%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-50938 AKU 에서 이용하는 문자열 값의 길이 제한이 실제와 다르게 설정되어 있습니다.](#bug-50938aku-%EC%97%90%EC%84%9C-%EC%9D%B4%EC%9A%A9%ED%95%98%EB%8A%94-%EB%AC%B8%EC%9E%90%EC%97%B4-%EA%B0%92%EC%9D%98-%EA%B8%B8%EC%9D%B4-%EC%A0%9C%ED%95%9C%EC%9D%B4-%EC%8B%A4%EC%A0%9C%EC%99%80-%EB%8B%A4%EB%A5%B4%EA%B2%8C-%EC%84%A4%EC%A0%95%EB%90%98%EC%96%B4-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-50950 aku -p start를 실행할 때 첫 번째 이중화 객체 생성이 실패해도 AKU가 즉시 종료되지 않습니다.](#bug-50950aku--p-start%EB%A5%BC-%EC%8B%A4%ED%96%89%ED%95%A0-%EB%95%8C-%EC%B2%AB-%EB%B2%88%EC%A7%B8-%EC%9D%B4%EC%A4%91%ED%99%94-%EA%B0%9D%EC%B2%B4-%EC%83%9D%EC%84%B1%EC%9D%B4-%EC%8B%A4%ED%8C%A8%ED%95%B4%EB%8F%84-aku%EA%B0%80-%EC%A6%89%EC%8B%9C-%EC%A2%85%EB%A3%8C%EB%90%98%EC%A7%80-%EC%95%8A%EC%8A%B5%EB%8B%88%EB%8B%A4)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
  - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
  - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Fixed Bugs
----------

### BUG-50005 aku 실행 시 옵션을 입력하지 않거나 잘못된 옵션을 입력했을 때 오류 메시지를 출력하지 않고 help 메시지만 출력하도록 변경하였습니다.

#### module

aku

#### Category 

Enhancement

#### 재현 빈도 

Always


#### 설명 

aku 실행 시 옵션을 입력하지 않거나 잘못된 옵션을 입력했을 때 오류 메시지를 출력하지 않고 help 메시지만 출력하도록 변경하였습니다.

#### 재현 방법

-   **재현 절차**

    ```bash
    $ aku
    ```

-   **수행 결과**

    ```bash
    Error while getting option.
    ===============================================================================
                  Altibase Kubernetes Utility Help Screen                          
    ===============================================================================
       Usage   : aku        [-h]                                                   
                            [--help]                                               
                            [-v ]                                                  
                            [--version ]                                           
                            [-i ]                                                  
                            [--info ]                                              
                            [-p pod_action ]                                       
                            [--pod pod_action]                                     
                 -h, --help    : this screen                                       
                 -v, --version : version information                               
                 -i, --info    : option information                                
                 -p, --pod     : [start | stop | clean] specify pod_action         
    ===============================================================================
    ```

-   **예상 결과**

    ```bash
    ===============================================================================
                  Altibase Kubernetes Utility Help Screen                          
    ===============================================================================
       Usage   : aku        [-h]                                                   
                            [--help]                                               
                            [-v ]                                                  
                            [--version ]                                           
                            [-i ]                                                  
                            [--info ]                                              
                            [-p pod_action ]                                       
                            [--pod pod_action]                                     
                 -h, --help    : this screen                                       
                 -v, --version : version information                               
                 -i, --info    : option information                                
                 -p, --pod     : [start | stop | clean] specify pod_action         
    ===============================================================================
    ```

#### Workaround

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50249 PICL 라이브러리에서 운영체제의 자원 상태를 수집할 때, 예외 상황이 발생하면 altimon.log에 기록해야 합니다. (AIX, HP-UX)
#### module

ux-altiMon

#### Category

Functionality

#### 재현 빈도

Rare

#### 설명 

altiMon의 모니터링 항목 중 운영체제의 자원 상태를 수집하는 PICL 라이브러리에서 예외 상황이 발생하면 altimon.log에 기록하도록 수정하였습니다. 예외 상황은 다음 정보를 조회하는 시스템 함수 호출이 실패할 때 발생합니다.

- Altibase 프로세스 정보 조회 시

- 파일 시스템 사용량 조회 시

- 메모리 사용량 조회 시

- SWAP 메모리 사용량 조회 시

- 시스템 시간 조회 시

이 버그는 AIX와 HP-UX를 대상으로 합니다. Linux는 BUG-50009에서 처리되었으며 관련 내용은 [Altibase 7.1.0.8.6 패치 노트](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.1/kor/Altibase_7_1_0_8_6_Patch_Notes.md)에서 확인할 수 있습니다.

#### 재현 방법

-   **재현 절차**

-   **수행 결과**

-   **예상 결과**

#### Workaround

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50849 ODBC 이스케이프 시퀀스(escape sequence)에 대문자를 사용하면 parse error 에러가 발생합니다.
#### module

mm-cli

#### Category

Functional Error

#### 재현 빈도

Always

#### 설명 

SQLCLI에서 ODBC 이스케이프 시퀀스(escape sequence)에 대문자를 사용하면 "parse error" 에러가 발생하는 현상을 수정하였습니다. 이제 ODBC 이스케이프 시퀀스 대소문자를 구분하지 않습니다. 이전 버전에서는 대문자를 사용하면 "parse error" 에러가 발생하였으나, 이 버그가 반영된 버전부터는 에러가 발생하지 않습니다.

ODBC 이스케이스 시퀀스 항목은 [Microsoft ODBC 페이지](https://learn.microsoft.com/ko-kr/sql/odbc/reference/appendixes/odbc-escape-sequences?view=sql-server-ver16)를 참고해 주십시오.

이 버그를 반영하려면 Altibase CLI 드라이버(libodbccli.a)를 패치해야 합니다.

#### 재현 방법

-   **재현 절차**

    ```c
    CREATE TABLE T1(i1 int, i2 int);
    CREATE OR REPLACE PROCEDURE proc1
    AS
      v1 constant INTEGER := 1;
      v2 constant t1.i1%TYPE := 1;
    BEGIN
      INSERT INTO t1 VALUES (v1, v2);
    END;
    rc = SQLExecDirect(stmt, (SQLCHAR *)"{ CALL proc1() }", SQL_NTS);
    if (!SQL_SUCCEEDED(rc))
    {
        PRINT_DIAGNOSTIC(SQL_HANDLE_STMT, stmt, "SQLExecDirect");
        goto EXIT_STMT;
    }
    printf("stored procedure call success\n");
    ```

-   **수행 결과**

    ```c
    Error : 158 : SQLExecDirect
      Diagnostic Record 1
        SQLSTATE     : 42000
        Message text : SQL syntax error
    line 1: parse error
    { CALL proc1() }
    ^
    ```

-   **예상 결과**

    프로시저 호출 성공

#### Workaround

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50875 Logical Ager가 삭제해야 할 인덱스 키를 찾지 못할 때 Altibase 서버가 비정상 종료합니다.
#### module

sm-mem-index

#### Category

Fatal

#### 재현 빈도

Unknown


#### 설명

- Logical Ager가 삭제해야 할 인덱스 키를 찾지 못할 때 Altibase 서버가 비정상 종료하는 현상을 수정합니다. Logical Ager가 알 수 없는 이유로 더 이상 참조되지 않는 인덱스 키를 찾는데 실패하면 해당 인덱스의 상태를 ISCONSISTENT로 변경합니다. ISCONSISTENT 상태의 인덱스는 V\$MEM\_BTREE\_HEADER에서 조회할 수 있습니다.

- ISCONSISTENT 상태의 인덱스가 있는 메모리 테이블에 INSERT 문이 정상적으로 수행되는 현상을 수정합니다. 이 버그가 반영된 버전에서는 ISCONSISTENT 상태의 인덱스가 있는 메모리 테이블에 INSERT 문을 수행하면 [ERR-11110 : The index is inconsistent] 에러가 발생합니다.

#### 재현 방법

-   **재현 절차**

-   **수행 결과**

-   **예상 결과**

#### Workaround

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50878 aexport.properties 파일에서 ILOADER\_FIELD\_TERM, ILOADER\_ROW\_TERM 프로퍼티의 값을 변경합니다.
#### module

ux-aexport

#### Category

Usability

#### 재현 빈도

Always

#### 설명 

aexport.properties 및 aexport.properties.sample 파일에서 ILOADER\_FIELD\_TERM, ILOADER\_ROW\_TERM 프로퍼티의 값을 기존보다 복잡한 형태로 변경합니다. ILOADER\_FIELD\_TERM 프로퍼티의 값은`^`에서 `^C_c^`으로, ILOADER\_ROW\_TERM 프로퍼티의 값은 `%n`에서 `^R_r^%n`으로 변경되었습니다.

#### 재현 방법

-   **재현 절차**

-   **수행 결과**

    ```bash
    $ cat aexport.properties | grep TERM
    #ILOADER_FIELD_TERM = ^#ILOADER_ROW_TERM = %n
    ```

-   **예상 결과**

    ```bash
    $ cat aexport.properties | grep TERM
    #ILOADER_FIELD_TERM = ^C_c^#ILOADER_ROW_TERM = ^R_r^%n
    ```

#### Workaround

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50891 사용하지 않는 INSPECTION\_LARGE\_HEAP\_THRESHOLD 프로퍼티를 삭제하였습니다.
#### module

sm

#### Category

Maintainability

#### 재현 빈도

Always

#### 설명 


사용하지 않는 `INSPECTION_LARGE_HEAP_THRESHOLD` 프로퍼티를 삭제하였습니다. 이 버그가 반영된 버전에서는 V\$PROPERTY에서 `INSPECTION_LARGE_HEAP_THRESHOLD` 프로퍼티를 조회할 수 없습니다.

#### 재현 방법

-   **재현 절차**

-   **수행 결과**

-   **예상 결과**

#### Workaround

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50905 연결 스트링에 DSN 속성을 입력하지 않으면 Invalid attribute value. 에러가 발생합니다.
#### module

ul-odbc

#### Category

Functional Error

#### 재현 빈도

Always

#### 설명 


연결 스트링에 DSN 속성을 입력하지 않으면 "Invalid attribute value." 에러가 발생하는 현상을 수정합니다. 이 현상은 'odbc.ini' 파일에 ODBC 데이터 소스 정보가 포함되어 있고, 연결 스트링에 DSN 속성을 입력하지 않을 때 발생합니다. DSN 속성을 사용하지 않아도 연결이 성공하도록 수정하였습니다.

이 버그를 적용하려면 Altibase ODBC 드라이버를 패치해야 합니다.

- 32비트 ODBC 드라이버 : libaltibase\_odbc-64bit-ul32.so

- 64비트 ODBC 드라이버 : libaltibase\_odbc-64bit-ul64.so

#### 재현 방법

-   **재현 절차**

    odbc.ini 파일 예시

    ```bash
    [ODBC Data Sources]
    BUG_50905_ALTIODBC_UL32 = Altibase ODBC 7.3 Driver
    [BUG_50905_ALTIODBC_UL32]
    Driver      = /data/eheejung/work/altidev4_r96980/altibase_home/lib/libaltibase_odbc-64bit-ul32.so
    Description = Altibase ODBC
    SERVER      = 127.0.0.1
    PORT        = 20300
    Database    = mydb
    [ODBC]
    Trace = 1
    TraceFile = /tmp/odbc.log
    ```

    연결 문자열 예시

    ```c
    (SQLCHAR *)"Driver=/usr/altibase/altibase_home/lib/libaltibase_odbc-64bit-ul32.so;Server=127.0.0.1;User=SYS;Password=MANAGER;Port=20300"
        
    (SQLCHAR *)"Driver=BUG_50905_ALTIODBC_UL32;Server=127.0.0.1;User=SYS;Password=MANAGER;Port=20300"
    ```

-   **수행 결과**

    ```bash
    Error : 49 : SQLDriverConnect
      Diagnostic Record 1
        SQLSTATE     : HY024
        Message text : Invalid attribute value.
        Message len  : 24
        Native error : 0x51015
    ```

-   **예상 결과**

    연결 성공

#### Workaround

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50907 조인에서 하이브리드 파티션드 테이블이 사용되고 SERIAL\_EXECUTE\_MODE 프로퍼티가 1일 때, 결과 값에 오류가 발생할 수 있습니다.
#### module

qp

#### Category

Reliability

#### 재현 빈도

Always

#### 설명 


조인에서 하이브리드 파티션드 테이블이 사용되고 `SERIAL_EXECUTE_MODE` 프로퍼티가 1일 때, 결과 값에 오류가 발생하는 현상을 수정하였습니다. 이 버그는 조인 방식이 FULL_NL일 때 발생하며, `USE_HASH`힌트를 사용하여 이 문제를 회피할 수 있습니다.

#### 재현 방법

-   **재현 절차**

    ```sql
    CREATE VOLATILE DATA TABLESPACE VOL_TBS SIZE 32M AUTOEXTEND ON;
    
    CREATE TABLE t1( i1 int, c1 clob )
    PARTITION BY RANGE(i1)
    (
        PARTITION p1 VALUES LESS THAN (1) TABLESPACE SYS_TBS_MEM_DATA,
        PARTITION p2 VALUES LESS THAN (2) TABLESPACE SYS_TBS_DISK_DATA,
        PARTITION p3 VALUES LESS THAN (3) TABLESPACE VOL_TBS,
        PARTITION pd VALUES DEFAULT TABLESPACE SYS_TBS_DISK_DATA
    ) TABLESPACE SYS_TBS_DISK_DATA UNCOMPRESSED LOGGING;
    
    CREATE TABLE t2( i1 int, c1 clob )
    PARTITION BY RANGE(i1)
    (
        PARTITION p1 VALUES LESS THAN (2) TABLESPACE SYS_TBS_DISK_DATA,
        PARTITION p2 VALUES LESS THAN (4) TABLESPACE SYS_TBS_MEM_DATA,
        PARTITION p3 VALUES LESS THAN (6) TABLESPACE SYS_TBS_DISK_DATA,
        PARTITION pd VALUES DEFAULT TABLESPACE VOL_TBS
    ) TABLESPACE SYS_TBS_DISK_DATA UNCOMPRESSED LOGGING;
    
    INSERT INTO t1 VALUES( 0, '0' );
    INSERT INTO t1 VALUES( 1, '1' );
    INSERT INTO t1 VALUES( 2, '2' );
    INSERT INTO t1 VALUES( 3, '3' );
    INSERT INTO t1 VALUES( 4, '4' );
    INSERT INTO t2 SELECT * FROM t1;
    
    CREATE VIEW v1 AS SELECT t1.i1 i1 FROM t1, t2 WHERE t1.i1 = t2.i1;
    
    SELECT i1 FROM v1;
    ```

-   **수행 결과**

    ```sql
    SELECT i1 FROM v1;
    I1
    --------------
    0
    1
    2
    4
    4 rows selected.
    ```

-   **예상 결과**

    ```sql
    I1
    --------------
    0
    1
    2
    3
    4
    5 rows selected.
    ```

#### Workaround

`USE_HASH` 힌트를 사용하여 문제 현상을 회피할 수 있습니다.

```sql
SELECT /*+ USE_HASH( t1, t2 ) */ i1 FROM v1;
```

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50914 altibase\_store\_result, altibase\_next\_result를 순차적으로 실행할 때, 두 번째 결과 집합에서 HY010 Function sequence error. 에러가 발생합니다.

#### module

ux-cdbc

#### Category

Functional Error

#### 재현 빈도

Always

#### 설명 

altibase\_store\_result, altibase\_next\_result를 순차적으로 실행하여 결과 집합을 가져올 때, 두 번째 결과 집합에서 발생하는 "HY010 Function sequence error." 에러를 수정하였습니다. 

이 버그를 반영하려면 ACI 라이브러리(libalticapi.a)를 패치해야 합니다.

**재현 방법**

-   **재현 절차**

        -- 스키마
        CREATE TABLE RESULT1 (I1 INTEGER, I2 VARCHAR(10));
        INSERT INTO RESULT1 VALUES (11, '11_AAA');
        INSERT INTO RESULT1 VALUES (12, '12_BBB');
        INSERT INTO RESULT1 VALUES (13, '13_CCC');
        CREATE TABLE RESULT2 (I1 INTEGER, I2 VARCHAR(10), I3 VARCHAR(10));
        INSERT INTO RESULT2 VALUES (21, '21_AAA', '221_AAA');
        INSERT INTO RESULT2 VALUES (22, '22_BBB', '222_BBB');
        INSERT INTO RESULT2 VALUES (23, '23_CCC', '223_CCC');
        CREATE TABLE RESULT3 (I1 INTEGER, I2 VARCHAR(10));
        INSERT INTO RESULT3 VALUES (31, '31_AAA');
        INSERT INTO RESULT3 VALUES (32, '32_BBB');
        INSERT INTO RESULT3 VALUES (33, '33_CCC');
        CREATE TABLE RESULT4 (I1 INTEGER, I2 VARCHAR(10));
        INSERT INTO RESULT4 VALUES (41, NULL);
        INSERT INTO RESULT4 VALUES (NULL, '42_BBB');
        INSERT INTO RESULT4 VALUES (NULL, NULL);
        CREATE TYPESET MY_TYPE
        AS
           TYPE MY_CUR IS REF CURSOR;
        END;
        /
        CREATE OR REPLACE PROCEDURE PROC_RESULTSET
        (
           P1 OUT MY_TYPE.MY_CUR,
           P2 OUT MY_TYPE.MY_CUR,
           P3 OUT MY_TYPE.MY_CUR,
           P4 OUT MY_TYPE.MY_CUR
        )
        AS
            sSQL_STMT VARCHAR(200);
        BEGIN
            sSQL_STMT := 'SELECT * FROM RESULT1';
            OPEN P1 FOR sSQL_STMT;
            sSQL_STMT := 'SELECT * FROM RESULT2';
            OPEN P2 FOR sSQL_STMT;
            sSQL_STMT := 'SELECT * FROM RESULT3';
            OPEN P3 FOR sSQL_STMT;
            sSQL_STMT := 'SELECT * FROM RESULT4';
            OPEN P4 FOR sSQL_STMT;
        END;
        /
        --  ACI 코드 예시   
        sRC = altibase_query(sAB, "EXEC PROC_RESULTSET");
        while (1)
        {
            sRes = altibase_store_result(sAB);
            ...중략...
            while ((sRow = altibase_fetch_row(sRes)) != NULL)
            {
            ...중략...
            }
            ...중략...
            sRC = altibase_next_result(sAB);
            ...중략...
        }

-   **수행 결과**

        HY010 Function sequence error.

-   **예상 결과**

    결과 집합을 정상적으로 조회

#### Workaround

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50919 altibase\_stmt\_next\_result 함수를 실행할 때, 두 번째 결과 집합에서 HY010 Function sequence error. 에러가 발생합니다.

#### module

ux-cdbc

#### Category

Functional Error

#### 재현 빈도

Always

#### 설명 


altibase\_stmt\_next\_result() 함수로 두 번째 결과 집합에 접근할 때 발생하는 "HY010 Function sequence error." 에러를 수정하였습니다.

이 버그를 반영하려면 ACI 라이브러리(libalticapi.a)를 패치해야 합니다.

#### 재현 방법

-   **재현 절차**

        -- 스키마
        CREATE TABLE fetch1 (id INTEGER, val VARCHAR(10));
        INSERT INTO fetch1 VALUES (1, 'a1');
        INSERT INTO fetch1 VALUES (2, 'b2');
        CREATE TABLE fetch2 (id INTEGER, val VARCHAR(10), etc VARCHAR(10));
        INSERT INTO fetch2 VALUES (4, 'd4', 'asd');
        INSERT INTO fetch2 VALUES (5, 'e5', 'qwe');
        INSERT INTO fetch2 VALUES (6, 'f6', 'zxc');
        CREATE TYPESET fetch_type
        AS
                TYPE fetch_cur IS REF CURSOR;
        END;
        /
        CREATE OR REPLACE PROCEDURE fetch_proc
        (
                p1 OUT fetch_type.fetch_cur,
                p2 OUT fetch_type.fetch_cur
        )
        AS
        BEGIN
                OPEN p1 FOR 'SELECT * FROM fetch1';
                OPEN p2 FOR 'SELECT * FROM fetch2';
        END;
        /
        -- ACI 코드 예시
        sRC = altibase_stmt_prepare(sStmt, "EXEC fetch_proc");
        ...중략...
        sRC = altibase_stmt_execute(sStmt);
        ...중략...  
        while (1)
        {
            ...중략...
            while ((sRC = altibase_stmt_fetch(sStmt)) != ALTIBASE_NO_DATA)
            {
            ...중략...
            }
            ...중략...
            sRC = altibase_stmt_next_result(sStmt);
            ...중략...
        }

-   **수행 결과**

        HY010 Function sequence error.

-   **예상 결과**

    결과 집합을 정상적으로 조회


#### Workaround

#### 변경사항

-   Performance view
    
-   Property
-   Compile Option
-   Error Code

### BUG-50920 데이터 업로드 시 에러가 발생한 경우, 어느 칼럼에서 발생했는지 알 수 없습니다.

#### module

ux-iloader

#### Category

Usability

#### 재현 빈도

Always

#### 설명 

데이터 업로드 시 에러가 발생한 경우, 어느 칼럼에서 발생했는지 알 수 없는 문제를 수정하였습니다. 

이제 `-verbose` 옵션을 사용하여 데이터 업로드에 실패한 칼럼의 정보를 로그 파일에서 확인할 수 있습니다. `-verbose` 옵션은 `-log` 옵션과 같이 사용해야 합니다. 데이터 업로드 시 `-verbose` 옵션을 사용하면 에러 메시지와 함께 테이블에서 해당 칼럼의 위치를 `-log logfile` 파일에 기록합니다. 단, 반환된 에러에서 칼럼의 정보를 알 수 없으면 칼럼의 위치가 기록되지 않습니다. 

**재현 방법**

-   **재현 절차**

    ```
    -- 테이블 스키마
    CREATE TABLE BUG_50920 (c1 INT, c2 int);
    
    -- 테이블에 업로드 할 파일 내용
    cat BUG_50920.dat
    1,1
    2,2147483648
    2147483648, 3
    2147483648, 2147483648
    
    -- 데이터 업로드 수행
    iloader -s localhost -u SYS -p manager formout -f BUG_50920.fmt -T BUG_50920
    iloader -s localhost -u SYS -p manager in -f BUG_50920.fmt -d BUG_50920.dat -log BUG_50920.log -silent
    cat BUG_50920.log
    iloader -s localhost -u SYS -p manager in -f BUG_50920.fmt -d BUG_50920.dat -log BUG_50920.log -silent -verbose
    cat BUG_50920.log
    ```

-   **수행 결과**

    ```bash
    $ iloader -s localhost -u SYS -p manager in -f BUG_50920.fmt -d BUG_50920.dat -log BUG_50920.log -silent
    UPLOAD : 14.3730 msec
         Load Count  : 1(BUG_50920)
         Error Count : 3
         
    $ cat BUG_50920.log
    TableName : BUG_50920
    Start Time : Wed Jun 19 19:19:33 2024
    Record 2 : 2,2147483648
    [ERR-51072 : Numeric value out of range.]
    Record 3 : 2147483648,3
    [ERR-51072 : Numeric value out of range.]
    Record 4 : 2147483648,2147483648
    [ERR-51072 : Numeric value out of range.]
    End Time : Wed Jun 19 19:19:33 2024
    Total Row Count : 4
    Load Row Count  : 1
    Error Row Count : 3
    
    $ iloader -s localhost -u SYS -p manager in -f BUG_50920.fmt -d BUG_50920.dat -log BUG_50920.log -silent -verbose
    [ERR-9103B : Invalid option (-verbose)]
    ```

-   **예상 결과**

    ```bash
    $ iloader -s localhost -u SYS -p manager in -f BUG_50920.fmt -d BUG_50920.dat -log BUG_50920.log -silent
    UPLOAD : 15.8760 msec
         Load Count  : 1(BUG_50920)
         Error Count : 3
         
    $ cat BUG_50920.log
    TableName : BUG_50920
    Start Time : Wed Jun 19 19:20:50 2024
    Record 2 : 2,2147483648
    [ERR-51072 : Numeric value out of range.]
    Record 3 : 2147483648,3
    [ERR-51072 : Numeric value out of range.]
    Record 4 : 2147483648,2147483648
    [ERR-51072 : Numeric value out of range.]
    End Time : Wed Jun 19 19:20:50 2024
    Total Row Count : 4
    Load Row Count  : 1
    Error Row Count : 3
    
    $ iloader -s localhost -u SYS -p manager in -f BUG_50920.fmt -d BUG_50920.dat -log BUG_50920.log -silent -verbose
    UPLOAD : 15.4300 msec
         Load Count  : 1(BUG_50920)
         Error Count : 3
         
    $ cat BUG_50920.log
    TableName : BUG_50920
    Start Time : Wed Jun 19 19:21:20 2024
    Record 2 : 2,2147483648
    [ERR-51072 : Numeric value out of range. at Column [2]]
    Record 3 : 2147483648,3
    [ERR-51072 : Numeric value out of range. at Column [1]]
    Record 4 : 2147483648,2147483648
    [ERR-51072 : Numeric value out of range. at Column [1]]
    End Time : Wed Jun 19 19:21:20 2024
    Total Row Count : 4
    Load Row Count  : 1
    Error Row Count : 3
    ```

#### Workaround

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50923 SQLPrepare 함수의 SQL 텍스트 문자열 인자가 빈 문자열일 때 에러가 발생하지 않습니다.

#### module

mm-cli

#### Category

Functional Error

#### 재현 빈도

Always

#### 설명 

SQLPrepare 함수의 SQL 텍스트 문자열 인자가 빈 문자열일 때 에러가 발생하지 않는 문제를 수정했습니다.

이 버그를 수정하기 전에는 SQLExecute 함수에서 "Failure to find statement" 에러가 발생했으나 이 버그가 수정된 버전에서는 SQLPrepare 함수에서 "SQL statement too short" 에러가 발생합니다.

이 버그를 반영하려면 Altibase CLI 드라이버(libodbccli.a)를 패치해야 합니다.

**재현 방법**

-   **재현 절차**

    ```c
    rc = SQLPrepare(stmt, (SQLCHAR *)"", SQL_NTS);
    if (!SQL_SUCCEEDED(rc))
    {
        PRINT_DIAGNOSTIC(SQL_HANDLE_STMT, stmt, "SQLPrepare");
        goto EXIT_STMT;
    }
    rc = SQLExecute(stmt);
    if (!SQL_SUCCEEDED(rc))
    {
        PRINT_DIAGNOSTIC(SQL_HANDLE_STMT, stmt, "SQLExecute");
        goto EXIT_STMT;
    }
    ```

-   **수행 결과**

    SQLPrepare에서 에러가 발생하지 않고 SQLExecute에서 에러가 발생.

    ```bash
    Error : 236 : SQLExecute
      Diagnostic Record 1
        SQLSTATE     : HY000
        Message text : Failure to find statement
        Message len  : 25
        Native error : 0x41098
    ```

-   **예상 결과**

    SQLPrepare에서 에러가 발생. 
    
    ```bash
    Error : 160 : SQLPrepare                                           
      Diagnostic Record 1                                              
        SQLSTATE     : HY000                                           
        Message text : SQL statement too short                         
        Message len  : 23                                              
        Native error : 0x41039
    ```

#### Workaround

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

### BUG-50938 AKU 에서 이용하는 문자열 값의 길이 제한이 실제와 다르게 설정되어 있습니다.

#### module

aku

#### Category

Functional Error

#### 재현 빈도

Always

#### 설명

aku 유틸리티에서 사용하는 문자열 길이의 제한을 올바르게 수정합니다.

`AKU_STS_NAME`, `AKU_SVC_NAME` 프로퍼티를 쿠버네티스의 제한에 따라 40에서 63으로 변경합니다. 이중화 대상 테이블의 사용자 이름과 이중화 대상 테이블의 이름의 길이를 40에서 128로 변경합니다. 이 제한은 Altibase 객체의 최대 길이를 따릅니다.

#### 재현 방법

-   **재현 절차**

-   **수행 결과**

-   **예상 결과**

#### Workaround

#### 변경사항

-   Performance view
-   Property
    
-   Compile Option
-   Error Code

### BUG-50950 aku -p start를 실행할 때 첫 번째 이중화 객체 생성이 실패해도 AKU가 즉시 종료되지 않습니다.

#### module

aku

#### Category

Functional Error

#### 재현 빈도

Always

#### 설명 

`aku -p start` 수행 중 이중화 객체 생성 단계에서 첫 번째 이중화 객체 생성 중 실패가 발생하면, 바로 종료되지 않고 두 번째 이중화 객체 생성을 시도한 뒤 종료되는 버그를 수정하였습니다. 이중화 객체 생성 중 실패하면 다른 작업을 수행하지 않고 바로 종료되도록 변경하였습니다.

#### 재현 방법

-   **재현 절차**

-   **수행 결과**

-   **예상 결과**

#### Workaround

#### 변경사항

-   Performance view
-   Property
-   Compile Option
-   Error Code

Changes
-------

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    7.1.0.9.7     |          6.5.1          |    8.11.1    |        7.1.7        |            7.4.7             |

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

#### 변경된 프로퍼티

#### 삭제된 프로퍼티

### 성능 뷰

#### 추가된 성능 뷰

#### 변경된 성능 뷰

#### 삭제된 성능 뷰
