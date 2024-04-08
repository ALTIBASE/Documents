# Altibase 7.3.0.0.5 Patch Notes

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-50768 V\$DISK\_BTREE\_HEADER, V\$MEM\_BTREE\_HEADER 성능뷰에 인덱스의 상태 정보를 출력하도록 개선되었습니다.](#bug-50768)
    - [BUG-50784 CWE-114 및 CWE-73 의 보안 취약점 해결](#bug-50784)
    - [BUG-50812 윈도우 클라이언트에서 cdbc(C API) 지원](#bug-50812)
    - [BUG-50822 체크포인트 주기와 서버 재구동 시간의 단축을 위해 CHECKPOINT_INTERVAL_IN_LOG, FAST_START_LOGFILE_TARGET 프로퍼티의 기본값 변경을 변경합니다.](#bug-50822)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-50433 Disk Page Recovery 또는 Service 중에 Corrupted Page 에 접근하는 문제를 회피하도록 개선합니다.](#bug-50433)
    - [BUG-50453 LB trace log 메시지에 오류가 있어서 수정합니다.](#bug-50453)
    - [BUG-50130 패키지 인스톨러 설치시, 저장 패키지 생성 구문에서 오류가 발생합니다.](#bug-50130)
    - [BUG-50778 getColumnCount 함수에 예외처리 추가](#bug-50778)
    - [BUG-50781 하나의 IPC 채널에 2개의 클라이언트가 세마포어를 제어해, 수신된 데이터가 재수신되어 Invalid protocol sequence 에러가 발생하는 문제를 수정하였습니다.](#bug-50781)
    - [BUG-50782 Multiple statement에서 Name-based Binding이 동작하지 않는 문제를 수정하였습니다.](#bug-50782)
    - [BUG-50783 프로시저 실행 중 Table에 DDL 수행시, Invalid use of host variables error 가 발생하는 문제를 수정합니다.](#bug-50783)
    - [BUG-50789 매체 복구(MEDIA RECOVERY) 진행 중에 체크포인트 이미지 파일이 추가되는 경우, 복구가 실패하는 문제를 수정합니다.](#bug-50789)
    - [BUG-50791 TO_CHAR 함수를 ALIAS로 조건절에 사용시 뷰에 대한 조건절 Pushdown 이 2번 이상 발생할 경우, 비정상 종료되는 문제를 수정합니다.](#bug-50791)
    - [BUG-50792 스냅샷 지정시, 언두 테이블 스페이스의 최대값을 계산하는 로직의 오류를 수정합니다.](#bug-50792)
    - [BUG-50799 윈도우용 설치 파일에 odbccli_sl.dll 이 누락된 문제를 수정합니다.](#bug-50799)
    - [BUG-50803 altibase\_boot.log 에 잘못된 errno 가 출력되는 문제를 수정합니다.](#bug-50803)
    - [BUG-50804 AltibaseStatement.close()시 서버 커넥션이 단절된 경우 STF(Session Time Failover)가 동작하지 않는 문제를 수정합니다.](#bug-50804)
    - [BUG-50826 CLI 함수 SQLPrimaryKeys()의 결과 컬럼의 2번째 열의 이름이 잘못 출력되는 문제를 수정합니다.](#bug-50826)
    - [BUG-50843 이중화 DDL 구문의 길이가 65534를 초과하는 경우 aexport의 오류를 수정합니다.](#bug-50843)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-50768<a name=bug-50768></a> V\$DISK\_BTREE\_HEADER, V\$MEM\_BTREE\_HEADER 성능뷰에 인덱스의 상태 정보를 출력하도록 개선되었습니다.

-   **module** : sm

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : V\$DISK\_BTREE\_HEADER, V\$MEM\_BTREE\_HEADER 에 인덱스의
    상태 정보를 나타내는 INDEX\_STATUS 컬럼이 추가되었습니다.

    또한 V\$MEM\_BTREE\_HEADER에 인덱스의 일관성 여부를 나타내는
    IS\_CONSISTENT 컬럼도 추가되었습니다.

-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
        - V$DISK_BTREE_HEADER
          - INDEX_STATUS 컬럼 추가 : 인덱스의 상태를 표시
        - V$MEM_BTREE_HEADER
          - INDEX_STATUS 컬럼 추가 :인덱스의 상태를 표시
          - IS_CONSISTENT 컬럼 추가 : 인덱스의 일관성 여부를 표시
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50784<a name=bug-50784></a> CWE-114 및 CWE-73 의 보안 취약점 해결

-   **module** : mm-jdbc

-   **Category** : Security

-   **재현 빈도** : Always

-   **설명** : Veracode에서 검출된 CWE-114 및 CWE-73 의 보안 취약점을 해결하였습니다. 이 버그를 적용하려면 JDBC 드라이버를 패치해야 합니다.

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

### BUG-50812<a name=bug-50812></a> 윈도우 클라이언트에서 cdbc(C API) 지원

-   **module** : ux-cdbc

-   **Category** : Portability

-   **재현 빈도** : Always

-   **설명** : windows 7.3 클라이언트에서 cdbc(C API) 를 지원하도록 개선되었습니다.

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

### BUG-50822<a name=bug-50822></a> 체크포인트 주기와 서버 재구동 시간의 단축을 위해 CHECKPOINT_INTERVAL_IN_LOG, FAST_START_LOGFILE_TARGET 프로퍼티의 기본값 변경을 변경합니다.

-   **module** : sm

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : 체크포인트 주기와 서버 재구동 시간의 단축을 위해 CHECKPOINT_INTERVAL_IN_LOG, FAST_START_LOGFILE_TARGET 프로퍼티의 기본값 변경을 변경합니다.
    -   CHECKPOINT_INTERVAL_IN_LOG 의 기본값을 100 -> 10 으로 변경

    -   FAST_START_LOGFILE_TARGET 의 기본값을 100 -> 10 으로 변경

-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
        -   CHECKPOINT_INTERVAL_IN_LOG
        -   FAST_START_LOGFILE_TARGET
    -   Compile Option
    -   Error Code

Fixed Bugs
==========

### BUG-50433<a name=bug-50433></a> Disk Page Recovery 또는 Service 중에 Corrupted Page 에 접근하는 문제를 회피하도록 개선합니다.

-   **module** : sm
-   **Category** : Fatal
-   **재현 빈도** : Unknown
-   **설명** : 1. Disk Page Recovery 또는 Service 중에 손상된 페이지(Corrupted Page)에 접근할 수 있어, 이를 회피하도록 수정하였습니다. 
2. 서비스중에 손상된 Disk Index Page 가 발견되는 경우, 해당 페이지는 inconsistent flag 설정하고, 해당 인덱스는 inconsistent index 로 설정하도록 수정하였습니다.
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

### BUG-50453<a name=bug-50453></a> LB trace log 메시지에 오류가 있어서 수정합니다.

-   **module** : mm

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : LB trace log 메시지에 오류가 있어 수정합니다. "현재 서비스 쓰레드의 개수가 MULTIPLEXING_MAX_THREAD_COUNT 보다 크다"를 표시하는 메시지에서 현재 서비스 쓰레드가 아닌 새로 생성될 서비스 쓰레드의 개수가 표시되고 있는 문제를 수정하였습니다.
    -   변경전 출력: NewServiceThreadCount(902) >= MaxThrCnt(1024)

    -   변경후 출력: CurrentServiceThreadCount(1024) >= MaxThrCnt(1024)

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

### BUG-50130<a name=bug-50130></a> 패키지 인스톨러 설치시, 저장 패키지 생성 구문에서 오류가 발생합니다.

-   **module** : pkg-map

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 저장 패키지 생성 구문에 불필요한 파일이 포함되어 있어서,
    주석처리하고 수행되지 않도록 수정합니다.

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

### BUG-50781<a name=bug-50781></a> 하나의 IPC 채널에 2개의 클라이언트가 세마포어를 제어해, 수신된 데이터가 재수신되어 Invalid protocol sequence 에러가 발생하는 문제를 수정하였습니다.

-   **module** : cm-ipc

-   **Category** : Functional Error

-   **재현 빈도** : Rare

-   **설명** : 하나의 IPC 채널에 2개의 클라이언트가 세마포어를 제어해 수신된 데이터가 재수신되는 현상이 있었고, 그로 인해 Invalid protocol sequence 에러 발생하는 문제를 수정하였습니다.
    
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

### BUG-50782<a name=bug-50782></a> Multiple statement에서 Name-based Binding이 동작하지 않는 문제를 수정하였습니다.

-   **module** : mm-cli

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 여러개의 statement에서 여러개의 파라미터 바인딩을 할 때, name-based binding이 제대로 동작하지 않던 문제가 해결되었습니다.
    
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

-   **설명** : 프로시저 실행 중 테이블에 DDL 구문 수행시, ERR-3123B : Invalid use of host variables 에러가 발생하는 문제를 수정합니다.
    
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

### BUG-50791<a name=bug-50791></a> TO_CHAR 함수를 ALIAS로 조건절에 사용시 뷰에 대한 조건절 Pushdown 이 2번 이상 발생할 경우, 비정상 종료되는 문제를 수정합니다.

-   **module** : qp

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : TO_CHAR 함수를 alias로 조건절에 사용시 뷰에 대한 조건절 Pushdown이 2번 이상 발생할 경우, 서버가 비정상 종료되는 문제를 수정합니다. 이 버그는 아래의 4가지 조건이 모두 일치하는 경우에만 발생합니다.
    
    1. TO_CHAR 함수의 2번째 인자로 숫자 형식이나 날짜 형식이 있는 경우
    2. TO_CHAR 함수의 1번째 인자가 Numeric 타입이 아닌 경우
    3. TO_CHAR 함수의 1번째 인자의 컬럼이 서브쿼리의 뷰에 존재하며, 뷰 머징이 되지 않고 Pushdown되는 경우
    4. 서브쿼리의 타겟절에서 TO_CHAR 함수를 사용하고 ALIAS를 지정하며, 이 ALIAS를 메인쿼리의 조건절에서 사용할 때, TO_CHAR 함수가 사용된 뷰로 Pushdown 되는 경우
    
- **재현 방법**

  - **재현 절차**

    ```sql
    SELECT * FROM (
         SELECT 
               (SELECT c.comments FROM SYSTEM_.SYS_COMMENTS_ c LIMIT 1) AS tablenm,
               TO_CHAR(b.fixed_alloc_mem,'999,999,999') || 'MB' AS alloc
          FROM v$memtbl_info b)
          WHERE alloc != '0MB';
    ```
    
  -   **수행 결과**
  
          [ERR-91015 : Communication failure.]
  
  -   **예상 결과**
  
          에러 없이 수행
  
- **Workaround**

  ```sql
  NO_PUSH_SELECT_VIEW hint 사용
  
  SELECT * FROM (
       SELECT /*+ NO_PUSH_SELECT_VIEW(b) */
             (SELECT /*+ NO_PUSH_SELECT_VIEW(c) */ c.comments FROM SYSTEM_.SYS_COMMENTS_ c LIMIT 1) AS tablenm,
             TO_CHAR(b.fixed_alloc_mem,'999,999,999') || 'MB' AS alloc
        FROM v$memtbl_info b)
        WHERE alloc != '0MB';
  ```

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

### BUG-50799<a name=bug-50799></a> 윈도우용 설치 파일에 odbccli_sl.dll 이 누락된 문제를 수정합니다.

-   **module** : pkg-map
-   **Category** : Portability
-   **재현 빈도** : Always
-   **설명** : 윈도우용 설치 파일에 odbccli_sl.dll 이 누락된 문제를 해결 하였습니다.
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

### BUG-50803<a name=bug-50803></a> altibase\_boot.log 에 잘못된 errno 가 출력되는 문제를 수정합니다.

-   **module** : cm

-   **Category** : Other

-   **재현 빈도** : Always

-   **설명** : altibase\_boot.log 에 에러 번호 출력시, "errno=22d"와 같이 에러 번호 뒤에 "d" 문자가 함께 출력되는 문제를 수정합니다.
    
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

### BUG-50804<a name=bug-50804></a> AltibaseStatement.close()시 서버 커넥션이 단절된 경우 STF(Session Time Failover)가 동작하지 않는 문제를 수정합니다.

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : AltibaseStatement.close()시 서버 커넥션이 단절된 경우
    STF(Session Time Failover)가 동작해야 하는데, 소캣 에러가 발생하는
    문제를 수정합니다.

- **재현 방법**

  - **재현 절차**

    ```java
    // stf=on
    try
    {
        sStmt = sCon.prepareStatement("SELECT 1 FROM dual");
        sRes = sStmt.executeQuery();
        if ( sRes.next() )
        {
            System.out.println( "VALUE : " + sRes.getString(1) );
        }
        // ==> 이 시점에서 서버커넥션 단절
        sStmt.close();
    }
    catch ( SQLException e )
    {
        if (e.getErrorCode() == ErrorDef.FAILOVER_SUCCESS)
        {
            System.out.println( "SUCCESS" );
        }
        else 
        {
        System.out.println("FAIL";
        }
    }
    ```

  -   **수행 결과**

          FAIL

  -   **예상 결과**

          SUCCESS

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50826<a name=bug-50826></a> CLI 함수 SQLPrimaryKeys()의 결과 컬럼의 2번째 열의 이름이 잘못 출력되는 문제를 수정합니다.

-   **module** : mm-cli

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : SQLPrimaryKeys() 함수의 결과 컬럼의 2번째 열의 이름이 TABLE_SCHEM이 출력되어야 하는데, TABLE_CAT으로 출력되는 문제를 수정합니다.
    
- **재현 방법**

  - **재현 절차**

    ```java
    iSQL> CREATE TABLE ODBCTESTS (ID INTEGER PRIMARY KEY, NAME VARCHAR(24), AGE INTEGER);
    
    ....
        if( SQLPrimaryKeys( stmt,
                            NULL,
                            0,
                            NULL,
                            0,
                            (SQLCHAR*) "ODBCTESTS",
                            SQL_NTS ) != SQL_SUCCESS )
        {
            printf( "Error : SQLPrimaryKeys()\n" );
            exit(-1);
        }
        else
        {
            printf("RUN SQLPrimaryKeys : SUCCESS\n");
        }
        ...
        while( SQLFetch(stmt) == SQL_SUCCESS )
        {
            sRecCnt++;
            if ( sRecCnt > 2 )
            {
                break;
            }
            printf( "=============================================\n" );
            printf( "= %d-th Record\n", sRecCnt );
            printf( "=============================================\n" );
            // To Remove DIFF by INDEX_ID
            for ( i = 0; i < sColCnt -1; i++ )
            {
                if ( SQLGetData( stmt,
                                 i + 1,
                                 SQL_C_CHAR,
                                 & sData[i],
                                 32,
                                 & sDataLen ) != SQL_SUCCESS )
                {
                    printf( "Error : SQLGetData(%d)\n", i );
                    exit(-1);
                }
                else
                {
                    printf( "COLUMN #%d\n"
                            "   ColName = %s\n"
                            "   ColType = %d\n"
                            "   Value   = %s\n",
                            i+1, sColName[i], sColType[i], sData[i] );
                }
            }
        }
    ```

  - **수행 결과**

        COLUMN #1
           ColName = TABLE_CAT
           ColType = 12
           Value   = mydb
        COLUMN #2
           ColName = TABLE_CAT
           ColType = 12
           Value   = SYS
        COLUMN #3
           ColName = TABLE_NAME
           ColType = 12
           Value   = ODBCTESTS
        COLUMN #4
           ColName = COLUMN_NAME
           ColType = 12
           Value   = ID
        COLUMN #5
           ColName = KEY_SEQ
           ColType = 5
           Value   = 1
        COLUMN #6
           ColName = PK_NAME
           ColType = 12
           Value   = __SYS_CON_PRIMARY_ID_202

  -   **예상 결과**

      ```java
      COLUMN #1
         ColName = TABLE_CAT
         ColType = 12
         Value   = mydb
      COLUMN #2
         ColName = TABLE_SCHEM
         ColType = 12
         Value   = SYS
      COLUMN #3
         ColName = TABLE_NAME
         ColType = 12
         Value   = ODBCTESTS
      COLUMN #4
         ColName = COLUMN_NAME
         ColType = 12
         Value   = ID
      COLUMN #5
         ColName = KEY_SEQ
         ColType = 5
         Value   = 1
      COLUMN #6
         ColName = PK_NAME
         ColType = 12
         Value   = __SYS_CON_PRIMARY_ID_202
      ```

- **Workaround**

      컬럼 순서로 조회

- **변경사항**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

### BUG-50843<a name=bug-50843></a> 이중화 DDL 구문의 길이가 65534를 초과하는 경우 aexport의 오류를 수정합니다.

-   **module** : ux-aexport
-   **Category** : Functional Error
-   **재현 빈도** : Always
-   **설명** : 이중화 DDL 구문의 길이가 65534를 초과하는 경우 aexport를 실행하면, ALL_CRT_REP.sql 파일의 크기가 0인 빈 파일이 생성되는 문제를 수정합니다.
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
| 7.3.0.0.5        | 7.3.0                   | 9.3.1        | 7.1.8               | 7.4.9                        |

> Altibase 7.3 패치 버전별 히스토리는 [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.3/Altibase_7_3_Version_Histories.md) 에서 확인할 수 있다.

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

#### 추가된 프로퍼티

#### 변경된 프로퍼티

#### 삭제된 프로퍼티

### 성능 뷰

#### 추가된 성능 뷰

#### 변경된 성능 뷰

#### 삭제된 성능 뷰
