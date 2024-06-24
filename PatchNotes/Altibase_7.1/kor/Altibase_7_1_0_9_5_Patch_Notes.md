# Altibase 7.1.0.9.5 Patch Notes

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Fixed Bugs](#fixed-bugs)
    - [BUG-50775 Multiple Statement 쿼리를 수행할 때 SQLExecute() 결과값이 SQL_NO_DATA일 경우, execute 처리가 중단되는 문제를 수정합니다.](#bug-50775)
    - [BUG-50782 Multiple Statement 에서 Named-base Binding 이 동작하지 않는 문제를 수정합니다.](#bug-50782)
    - [BUG-50784 CWE-114 및 CWE-73 의 보안 취약점 해결](#bug-50784)
    - [BUG-50798 매체 복구(MEDIA RECOVERY) 진행 중에 체크포인트 이미지 파일이 추가되는 경우, 내부적으로 PCH(Page Control Header)를 할당하는 과정에서 오류가 있어서 수정하였습니다.](#bug-50798)
    - [BUG-50803 altibase\_boot.log 에 잘못된 errno 가 출력되는 문제를 수정합니다.](#bug-50803)
    - [BUG-50804 AltibaseStatement.close()시 서버 커넥션이 단절된 경우 STF(Session Time Failover)가 동작하지 않는 문제를 수정합니다.](#bug-50804)
    - [BUG-50817 DISK TABLE, DISK INDEX AGING 수행 시, 테이블에 X Lock(Exclusive Lock) 잡던 것을 IX Lock(Intent Exclusive Lock)으로 변경합니다.](#bug-50817)
    - [BUG-50826 CLI 함수 SQLPrimaryKeys()의 결과 컬럼의 2번째 열의 이름이 잘못 출력되는 문제를 수정합니다.](#bug-50826)
    - [BUG-50840 매체 복구(MEDIA RECOVERY) 진행 중에 체크포인트 이미지 파일이 추가되는 경우, 내부적으로 페이지가 할당되지 않는 경우가 있어서 수정합니다.](#bug-50840)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Fixed Bugs
==========

### BUG-50775<a name=bug-50775></a> Multiple Statement 쿼리를 수행할 때 SQLExecute() 결과값이 SQL_NO_DATA일 경우, execute 처리가 중단되는 문제를 수정합니다.

-   **module** : mm-cli

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : Multiple Statement 쿼리를 수행할 때 SQLExecute() 결과값이 SQL\_NO\_DATA일 경우, execute가 중단되지 않도록 수정하였습니.
    
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

### BUG-50782<a name=bug-50782></a> Multiple Statement 에서 Named-base Binding 이 동작하지 않는 문제를 수정합니다.

-   **module** : mm-cli

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : Multiple statement에서 여러개의 파라미터 바인딩을 할 때, Named-base binding 이 제대로 동작하지 않던 문제가 해결되었습니다.
    
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

### BUG-50798<a name=bug-50798></a> 매체 복구(MEDIA RECOVERY) 진행 중에 체크포인트 이미지 파일이 추가되는 경우, 내부적으로 PCH(Page Control Header)를 할당하는 과정에서 오류가 있어서 수정하였습니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : 매체 복구(MEDIA RECOVERY) 진행 중에 체크포인트 이미지 파일이 추가되는 경우, 내부적으로 PCH(Page Control Header)를 할당하는 과정에서 오류가 있어서 수정하였습니다.

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

### BUG-50817<a name=bug-50817></a> DISK TABLE, DISK INDEX AGING 수행 시, 테이블에 X Lock(Exclusive Lock) 잡던 것을 IX Lock(Intent Exclusive Lock)으로 변경합니다.

-   **module** : sm
-   **Category** : Other
-   **재현 빈도** : Always
-   **설명** : DISK TABLE, DISK INDEX AGING 구문 수행 시, 테이블에 X Lock(Exclusive Lock) 잡던 것을 IX Lock(Intent Exclusive Lock)으로 변경합니다. 페이지 정보를 갱신하기 위해 디스크 테이블 또는 디스크 인덱스에 AGING을 수행할 때, X Lock으로 인해 트랜잭션을 대기하다가 timeout이 발생하는 문제가 해결되었습니다.
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

    ```java
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
    ```

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

-   **Workaround**

        컬럼 순서로 조회

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50840<a name=bug-50840></a> 매체 복구(MEDIA RECOVERY) 진행 중에 체크포인트 이미지 파일이 추가되는 경우, 내부적으로 페이지가 할당되지 않는 경우가 있어서 수정합니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : 매체 복구(MEDIA RECOVERY) 진행 중에 체크포인트 이미지 파일이 추가되는 경우, 내부적으로 페이지가 할당되지 않는 경우가 있어서 수정하였습니다. 

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
| 7.1.0.9.5        | 6.5.1                   | 8.11.1       | 7.1.7               | 7.4.7                        |

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

#### 추가된 프로퍼티

#### 변경된 프로퍼티

#### 삭제된 프로퍼티

### 성능 뷰

#### 추가된 성능 뷰

#### 변경된 성능 뷰

#### 삭제된 성능 뷰
