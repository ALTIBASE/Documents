# Altibase 7.1.0.9.3 Patch Notes

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-50713 잘못된 패킷으로 Protocol header error가 발생한 경우, 에러메시지에 헤더 내용 출력하도록 개선합니다.](#bug-50713)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-48041 트리거에서 %ROWTYPE 또는 %TYPE을 사용할 때, 테이블 정의가 변경되면 트리거가 자동으로 재컴파일 되지 않는 문제를 수정합니다.](#bug-48041)
    - [BUG-50694 디스크테이블에서 서브쿼리 내의 group by 칼럼이 메인 쿼리의 참조로 사용되는 경우 서버가 비정상 종료하는 문제를 수정합니다.](#bug-50694)
    - [BUG-50710 External procedure를 호출하는 package를 생성하는 과정에서 서버가 비정상 종료할 수 있는 문제를 수정합니다.](#bug-50710)
    - [BUG-50714 패키지 내에서 constant 또는 nocopy 옵션이 있는 변수를 직접 변경할 때 잘못 동작하는 문제를 수정합니다.](#bug-50714)
    - [BUG-50729 종료된 쓰레드의 스택 크기가 v$memstat 에서 계속 출력됩니다.](#bug-50729)
    - [BUG-50758 APRE에서 double quote 문자에 대한 escape 처리 누락](#bug-50758)
    - [BUG-50778 getColumnCount 함수에 예외처리 추가](#bug-50778)
    - [BUG-50783 프로시저 실행 중 Table에 DDL 수행시, Invalid use of host variables error 가 발생하는 문제를 수정합니다.](#bug-50783)
    - [BUG-50789 매체 복구(MEDIA RECOVERY) 진행 중에 체크포인트 이미지 파일이 추가되는 경우, 복구가 실패하는 문제를 수정합니다.](#bug-50789)
    - [BUG-50792 스냅샷 지정시, 언두 테이블 스페이스의 최대값을 계산하는 로직의 오류를 수정합니다.](#bug-50792)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-50713<a name=bug-50713></a> 잘못된 패킷으로 Protocol header error가 발생한 경우, 에러메시지에 헤더 내용 출력하도록 개선합니다.

-   **module** : cm
-   **Category** : Functionality
-   **재현 빈도** : Rare
-   **설명** : 잘못된 패킷이 수신되어 Protocol header error가 발생했을 때, 에러메시지에 헤더 내용을 출력하여 문제 분석에 도움을 주도록 개선하였습니다.
    - 수정전 : ERR-7101d(errno=0) Protocol header error.(TCP 127.0.0.1:41462)
    - 수정후 : ERR-710cc(errno=0) Protocol header error.(TCP 127.0.0.1:41462, 0, 3132333435363738393031323334353637383930)
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
        -   수정전 : ERR-7101d(errno=0) Protocol header error.(TCP 127.0.0.1:41462)
        -   수정후 : ERR-710cc(errno=0) Protocol header error.(TCP 127.0.0.1:41462, 0, 3132333435363738393031323334353637383930)

Fixed Bugs
==========

### BUG-48041<a name=bug-48041></a> 트리거에서 %ROWTYPE 또는 %TYPE을 사용할 때, 테이블 정의가 변경되면 트리거가 자동으로 재컴파일 되지 않는 문제를 수정합니다.

-   **module** : qp-ddl-dcl-execute

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 트리거에서 %ROWTYPE 또는 %TYPE을 사용할 때, 테이블 정의가 변경되면 실행시점에 트리거가 자동으로 재컴파일 되지 않는 문제를 수정합니다.
    
- **재현 방법**

  -   **재현 절차**

      ```sql
      CREATE TABLE T1(C1 INT, C2 INT);
      CREATE TABLE T2(C1 INT);
      CREATE TABLE T3(C1 INT, C2 INT);
      CREATE OR REPLACE TRIGGER TRIG_ON_T1
           BEFORE INSERT ON T1
           REFERENCING NEW AS NEW_ROW
           FOR EACH ROW
           BEGIN
           DECLARE
           VAR1 T3%ROWTYPE;
           BEGIN
             VAR1.C2 := NEW_ROW.C1;
             INSERT INTO T2 VALUES(VAR1.C2);
           END;
           END;
           /
      
      INSERT INTO T1 VALUES(1,1);
      SELECT * FROM T1;
      SELECT * FROM T2;
      ALTER TABLE T3 DROP C2;
      INSERT INTO T1 VALUES(1,2);
      ```
      
  -   **수행 결과**
  
      ```sql
      iSQL> INSERT INTO T1 VALUES(1,2);
      1 row inserted.
      ```
      
  -   **예상 결과**
  
      ```sql
      iSQL> INSERT INTO T1 VALUES(1,2);
      [ERR-311F9 : The attempt to recompile the trigger SYS.TRIG_ON_T1 was aborted because the creation statement was invalid. :
      
       Column not found
      
      In trigger SYS.TRIG_ON_T1
      0009 :        VAR1.C2 := NEW_ROW.C1;
                        ^ ^
      ]
      ```
  
-   **Workaround**

        트리거 수정 후 재 컴파일

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50694<a name=bug-50694></a> 디스크테이블에서 서브쿼리 내의 group by 칼럼이 메인 쿼리의 참조로 사용되는 경우 서버가 비정상 종료하는 문제를 수정합니다.

- **module** : qp

- **Category** : Fatal

- **재현 빈도** : Always

- **설명** : 이 버그는 디스크테이블에서만 재현됩니다. 서브쿼리 내의 group by 칼럼이 메인 쿼리의 참조로 사용되는 경우 서버가 비정상 종료하는 문제를 수정합니다.

- **재현 방법**

  - **재현 절차**

    ```sql
    CREATE TABLE T1( I1 INTEGER, I2 INTEGER, I3 INTEGER ) TABLESPACE SYS_TBS_DISK_DATA;
    INSERT INTO T1 VALUES (2, NULL, NULL);
    SELECT * FROM T1 WHERE I1 > ALL ( SELECT MIN(I2) FROM DUAL WHERE I1 = '1' GROUP BY I1);
    ```

  - **수행 결과**

    ```sql
    [ERR-91015 : Communication failure.]
    ```

  - **예상 결과**

    ```sql
    iSQL> SELECT * FROM T1 WHERE I1 > ALL ( SELECT MIN(I2) FROM DUAL WHERE I1 = '1' GROUP BY I1);
    I1          I2          I3
    ----------------------------------------
    2
    1 row selected.
    ```

- **Workaround**

- **변경사항**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

### BUG-50710<a name=bug-50710></a> External procedure를 호출하는 package를 생성하는 과정에서 서버가 비정상 종료할 수 있는 문제를 수정합니다.

-   **module** : qp
-   **Category** : Fatal
-   **재현 빈도** : Always
-   **설명** : External procedure를 호출하는 package를 생성하는 과정에서 서버가 비정상 종료할 수 있는 문제를 수정합니다.
-   **재현 방법**

    -   **재현 절차**
    -   **수행결과**
    -   **예상결과**
-   **Workaround**
-   **변경사항**
    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50714<a name=bug-50714></a> 패키지 내에서 constant 또는 nocopy 옵션이 있는 변수를 직접 변경할 때 잘못 동작하는 문제를 수정합니다.

-   **module** : qp-psm-trigger-execute

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 패키지 내에서 constant 또는 nocpy 변수를 직접 변경할 때 잘못 동작하는 문제를 수정합니다.
    
    1. 패키지 내에서 constant 옵션이 있는 변수의 값을 직접 변경하려는 경우, 에러가 발생해야 하는데 값이 변경되는 문제를 수정했습니다. 이제 constant 옵션이 있는 변수의 값을 변경하려는 경우, 에러 메시지가 출력되면서 값을 변경할 수 없도록 개선되었습니다.
    2. 패키지 내에서 nocopy 옵션이 있는 변수의 경우 직접 값을 변경할 경우, ERR-31439 : An array (element) is not initialized. 에러가 발생하는 문제를 수정했습니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    CREATE OR REPLACE PACKAGE PKG1 AS
    VAR1 CONSTANT INTEGER := 1;
    end;
    /
    EXEC PKG1.VAR1 := 100;
    EXEC PRINTLN(PKG1.VAR1);
    
    CREATE OR REPLACE PACKAGE PKG2 AS
    TYPE ARR_TYPE IS TABLE OF CHAR(32000) INDEX BY INTEGER;
    VAR1 NOCOPY ARR_TYPE;
    VAR2 ARR_TYPE;
    RET INTEGER;
    END;
    /
    BEGIN
      FOR I IN 1 .. 10000 LOOP
        PKG2.VAR2(I) := I;
      END LOOP;
    END;
    /
    EXEC PKG2.VAR1 := PKG2.VAR2;
    ```

  - **수행 결과**

    ```sql
    iSQL> EXEC PKG1.VAR1 := 100;
    Execute success.
    iSQL> EXEC PRINTLN(PKG1.VAR1);
    100
    Execute success.
    iSQL> EXEC PKG2.VAR1 := PKG2.VAR2;
    [ERR-31439 : An array (element) is not initialized.
    at line 1]
    ```

  -   **예상 결과**

      ```sql
      iSQL> EXEC PKG1.VAR1 := 100;
      [ERR-3113F : The L-value of the ASSIGN statement is either a CONSTANT variable or an IN parameter.
      0001 : EXEC PKG1.VAR1 := 100
                 ^        ^
      ]
      iSQL> EXEC PRINTLN(PKG1.VAR1);
      1
      Execute success.
      iSQL> EXEC PKG2.VAR1 := PKG2.VAR2;
      Execute success.
      ```

- **Workaround**

  ```sql
  BEGIN
    PKG1.VAR1 := 100;
  END;
  /
  BEGIN
    PKG2.VAR1 := PKG2.VAR2;
  END;
  /
  ```

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50729<a name=bug-50729></a> 종료된 쓰레드의 스택 크기가 v\$memstat 에서 계속 출력됩니다.

-   **module** : id

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 쓰레드 종료 시 스택이 해제되어도 V$MEMSTAT 조회에 반영되지 않는 문제를 수정합니다. 이로 인해, 실제 메모리 사용량보다 더 많은 사용량으로 표시되는 문제가 해결되었습니다.

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

### BUG-50758<a name=bug-50758></a> APRE에서 double quote 문자에 대한 escape 처리 누락

-   **module** : mm-apre

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : EXEC SQL 구문에 "(double quote)문자가 포함된 경우, apre precompile후에 생성되는 .c, .cpp 파일에 escape 문자가 자동으로 추가되도록 수정하였습니다.
    
    예)

    .sc 파일 : EXEC SQL SELECT ' " ' FROM DUAL;

    ==\>

    .c 파일 : ulpSqlstmt.stmt = (char \*)"SELECT ' \\" ' FROM DUAL";

- **재현 방법**

  - **재현 절차**

    ```c
    int main()
    {
        EXEC SQL SELECT ' " ' FROM DUAL;
    }
    ```

  - **수행 결과**

    .c 파일에서 아래와 같이 변환된다.

    ```c
    int main()
    {
        /*  SELECT ' " ' FROM DUAL; */
    {
        struct ulpSqlstmt ulpSqlstmt;
        memset(&ulpSqlstmt, 0, sizeof(ulpSqlstmt));
        ulpSqlstmt.stmttype = 4;
        ulpSqlstmt.stmtname = NULL;
        ulpSqlstmt.ismt = 0;
        ulpSqlstmt.numofhostvar = 0;
        ulpSqlstmt.statusptr = NULL;
        ulpSqlstmt.errcodeptr = NULL;
        ulpSqlstmt.isatomic = 0;
        ulpSqlstmt.stmt = (char *)"SELECT ' " ' FROM DUAL";
     ...
    }
    }
    ```

  -   **예상 결과**

      .c 파일에서 아래와 같이 " 앞에 \이 추가된 것을 확인할 수 있다.
      
      ```c
      int main()
      {
          /*  SELECT ' " ' FROM DUAL; */
      {
          struct ulpSqlstmt ulpSqlstmt;
          memset(&ulpSqlstmt, 0, sizeof(ulpSqlstmt));
          ulpSqlstmt.stmttype = 4;
          ulpSqlstmt.stmtname = NULL;
          ulpSqlstmt.ismt = 0;
          ulpSqlstmt.numofhostvar = 0;
          ulpSqlstmt.statusptr = NULL;
          ulpSqlstmt.errcodeptr = NULL;
          ulpSqlstmt.isatomic = 0;
          ulpSqlstmt.stmt = (char *)"SELECT ' \" ' FROM DUAL";
      ...
      }
      }
      ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50778<a name=bug-50778></a> getColumnCount 함수에 예외처리 추가

-   **module** : qp
-   **Category** : Fatal
-   **재현 빈도** : Rare
-   **설명** : Prepare 과정 중에 컬럼 정보를 요청하기 위해 내부적으로 getColumnCount를 호출하는데, 예외적인 상황에서 잘못된 자료구조에 접근하여 서버가 비정상 종료되는 문제가 있었습니다. 이러한 상황에 대한 예외처리를 추가하였습니다.
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

### BUG-50783<a name=bug-50783></a> 프로시저 실행 중 Table에 DDL 수행시, Invalid use of host variables error 가 발생하는 문제를 수정합니다.

-   **module** : qp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 프로시저 실행 중 테이블에 DDL 구문 수행시, ERR-3123B : Invalid use of host variables 에러가 발생하는 문제를 수정합니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    -- session 1
    CREATE TABLE T1 (I1 INTEGER);
    INSERT INTO T1 VALUES(1);
    CREATE OR REPLACE PROCEDURE PROC1 AS
    VAR1 INTEGER;
    VAR2 INTEGER;
    BEGIN
      VAR1 := 1;
      FOR I IN 1 .. 10 LOOP
      SELECT VAR1 INTO VAR2 FROM T1;
      PRINTLN(VAR2);
      SLEEP(2);
      VAR1 := VAR1 + 1;
      END LOOP;
    END;
    /
    EXEC PROC1;
    
    -- session 2
    ALTER TABLE T1 ADD (I2 INTEGER);
    ```

  - **수행 결과**

    ```sql
    iSQL> EXEC PROC1;
    1
    2
    3
    4
    [ERR-3123B : Invalid use of host variables
    0001 : select :B0 from T1;
                 ^  ^
    
    at "SYS.PROC1", line 7]
    ```

  -   **예상 결과**

      ```sql
      iSQL> EXEC PROC1;
      1
      2
      3
      4
      5
      6
      7
      8
      9
      10
      Execute success.
      ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50789<a name=bug-50789></a> 매체 복구(MEDIA RECOVERY) 진행 중에 체크포인트 이미지 파일이 추가되는 경우, 복구가 실패하는 문제를 수정합니다.

-   **module** : sm
-   **Category** : Fatal
-   **재현 빈도** : Always
-   **설명** : 매체 복구(MEDIA RECOVERY) 진행 중에 체크포인트 이미지 파일이 추가되는 경우, 추가된 체크포인트 이미지 파일의 LSN을 알수 없어서 복구에 실패했습니다. 이 문제를 해결하기 위해 매체 복구 진행 중 생성된 파일의 헤더에 CreateLSN을 기록하도록 수정하였습니다.
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

### BUG-50792<a name=bug-50792></a> 스냅샷 지정시, 언두 테이블 스페이스의 최대값을 계산하는 로직의 오류를 수정합니다.

-   **module** : sm

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 스냅샷 지정시, 언두 테이블 스페이스의 최대값을 계산하는 로직의 오류를 수정합니다.
    
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
| 7.1.0.9.3        | 6.5.1                   | 8.11.1       | 7.1.7               | 7.4.7                        |

> Altibase 7.1 패치 버전별 히스토리는 [Version_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.1/Altibase_7_1_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의
> 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는
> 데이터베이스를 재구성해야 한다.

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
