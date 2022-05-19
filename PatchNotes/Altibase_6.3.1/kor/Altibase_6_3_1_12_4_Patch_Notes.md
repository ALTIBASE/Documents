Altibase 6.3.1.12.4 Patch Notes
===============================

<br/>

<br/>

# **Table of Contents**

- [Fixed Bugs](#fixed-bugs)
  - [BUG-49505 복잡도가 높은 SQL문 수행 시 PREPARE\_STMT\_MEMORY\_MAXIMUM 초과로 SQL Plan Cache에 실행 계획을 등록하지 못한 경우 예외 처리를 추가합니다.](#bug-49505%C2%A0%EB%B3%B5%EC%9E%A1%EB%8F%84%EA%B0%80-%EB%86%92%EC%9D%80-sql%EB%AC%B8-%EC%88%98%ED%96%89-%EC%8B%9C-prepare%5C_stmt%5C_memory%5C_maximum-%EC%B4%88%EA%B3%BC%EB%A1%9C-sql-plan-cache%EC%97%90-%EC%8B%A4%ED%96%89-%EA%B3%84%ED%9A%8D%EC%9D%84-%EB%93%B1%EB%A1%9D%ED%95%98%EC%A7%80-%EB%AA%BB%ED%95%9C-%EA%B2%BD%EC%9A%B0-%EC%98%88%EC%99%B8-%EC%B2%98%EB%A6%AC%EB%A5%BC-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49636 Altibase 서버 프로퍼티 ARCHIVE\_FULL\_ACTION 설정 값에 따른 아카이브로그 쓰레드의 동작을 개선합니다.](#bug-49636%C2%A0altibase-%EC%84%9C%EB%B2%84-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0-archive%5C_full%5C_action-%EC%84%A4%EC%A0%95-%EA%B0%92%EC%97%90-%EB%94%B0%EB%A5%B8-%EC%95%84%EC%B9%B4%EC%9D%B4%EB%B8%8C%EB%A1%9C%EA%B7%B8-%EC%93%B0%EB%A0%88%EB%93%9C%EC%9D%98-%EB%8F%99%EC%9E%91%EC%9D%84-%EA%B0%9C%EC%84%A0%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49670 SQL Plan cache에 등록된 SQL 문 수행 중 Hard Parsing을 다시 진행할 때 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-49670%C2%A0sql-plan-cache%EC%97%90-%EB%93%B1%EB%A1%9D%EB%90%9C-sql-%EB%AC%B8-%EC%88%98%ED%96%89-%EC%A4%91-hard-parsing%EC%9D%84-%EB%8B%A4%EC%8B%9C-%EC%A7%84%ED%96%89%ED%95%A0-%EB%95%8C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [BUG-49702 WITH 절 또는 인라인 뷰에 집계 함수를 포함한 서브쿼리가 WHERE 절에 사용된 경우 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-49702%C2%A0with-%EC%A0%88-%EB%98%90%EB%8A%94-%EC%9D%B8%EB%9D%BC%EC%9D%B8-%EB%B7%B0%EC%97%90-%EC%A7%91%EA%B3%84-%ED%95%A8%EC%88%98%EB%A5%BC-%ED%8F%AC%ED%95%A8%ED%95%9C-%EC%84%9C%EB%B8%8C%EC%BF%BC%EB%A6%AC%EA%B0%80-where-%EC%A0%88%EC%97%90-%EC%82%AC%EC%9A%A9%EB%90%9C-%EA%B2%BD%EC%9A%B0-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
  - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
  - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)





Fixed Bugs
==========

### BUG-49505 복잡도가 높은 SQL문 수행 시 PREPARE\_STMT\_MEMORY\_MAXIMUM 초과로 SQL Plan Cache에 실행 계획을 등록하지 못한 경우 예외 처리를 추가합니다.

-   **module** : qp

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : 복잡도가 높은 SQL문 수행 시 PREPARE\_STMT\_MEMORY\_MAXIMUM 초과로 SQL Plan Cache에 실행 계획을 등록하지 못한 경우 Altibase 서버가 비정상 종료하는 현상을 수정합니다.
    
-   **재현 방법**

    -   **재현 절차**

        ```sql
        DROP TABLE BUG_49505;
         
        CREATE TABLE BUG_49505 
        ( 
          I1  INTEGER, 
          I2  INTEGER,
          I3  INTEGER, 
          I4  INTEGER,
          I5  INTEGER,
          I6  INTEGER, 
          I7  INTEGER, 
          I8  INTEGER,
          I9  INTEGER, 
          I10 INTEGER, 
          I11 INTEGER, 
          I12 GEOMETRY
        )
        PARTITION BY RANGE( I1 )
        ( 
          PARTITION P1 VALUES LESS THAN ( 10 ), 
          PARTITION P2 VALUES LESS THAN ( 20 ), 
          PARTITION P3 VALUES LESS THAN ( 30 ), 
          PARTITION P4 VALUES DEFAULT 
        ) TABLESPACE SYS_TBS_DISK_DATA;
         
        ALTER TABLE BUG_49505 MERGE PARTITIONS P2, P3 INTO PARTITION P3 ;
        ALTER TABLE BUG_49505 DROP PARTITION P1;
         
        SELECT COUNT(*) FROM ( SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 UNION ALL SELECT * FROM BUG_49505 );
        ```

    -   **수행 결과**

            Altibase 서버 비정상 종료 

    -   **예상 결과**

            Altibase 서버 비정상 종료하지 않음

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49636 Altibase 서버 프로퍼티 ARCHIVE\_FULL\_ACTION 설정 값에 따른 아카이브로그 쓰레드의 동작을 개선합니다.

-   **module** : sm

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : 디스크 공간 부족으로 로그 파일 백업이 실패하는 경우 ARCHIVE\_FULL\_ACTION 설정 값에 따른 아카이브로그 쓰레드의 동작을
    개선합니다.
    
    **ARCHIVE\_FULL\_ACTION 설정 값에 따른 동작 차이**
    
    - ARCHIVE\_FULL\_ACTION = 0 
    
      - 변경 전 : 디스크 공간 부족으로 로그 파일 백업이 실패하는 경우 아카이브로그 쓰레드가 중지된다. 아카이브로그 쓰레드를 시작하려면 사용자가 명시적으로 ALTER SYSTEM ARCHIVE LOG START를 수행해야 한다. 
    
      - 변경 후 : 디스크 공간 부족으로 로그 파일 백업이 실패하는 경우 아카이브로그 쓰레드가 중지되지 않으며 차례로 다음 로그 파일 백업을 시도한다. 백업에 실패한 로그파일은 트레이스 로그(altibase\_sm.log)에 기록한다.
    
    - ARCHIVE\_FULL\_ACTION = 1 
    
      변경이 없습니다.
    
    - ARCHIVE\_FULL\_ACTION = 2

      - 설정값 2가 추가되었습니다. 

        디스크 공간 부족 실패 외에 다른 이유로 로그 파일 백업이 실패하는 경우 트레이스 로그(altibase\_sm.log)에 에러 메시지를 출력하고 다음 로그 파일의 백업을 시도합니다.

    **ARCHIVE\_FULL\_ACTION 속성 변경**

    읽기 전용에서 변경 가능으로 변경합니다.

    - 변경 전
    
      ```sql
      iSQL> ALTER SYSTEM SET ARCHIVE_FULL_ACTION = 2;
      [ERR-0104E : The property [ARCHIVE_FULL_ACTION] is read-only.]
      ```
    
    - 변경 후
    
      ```sql
      iSQL> ALTER SYSTEM SET ARCHIVE_FULL_ACTION = 2;
      Alter success.
      ```

      

    ARCHIVE\_FULL\_ACTION 설정 값에 관한 보다 자세한 설명은 [Altibase 7.1 General Reference-1.Data Types & Altibase Properties](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase\_7.1/kor/General%20Reference-1.Data%20Types%20%26%20Altibase%20Properties.md\#archive\_full\_action)에서 확인할 수 있습니다. Altibase 6.3.1 매뉴얼은 업데이트되지 않아 Altibase 7.1 매뉴얼로 안내합니다. 

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

### BUG-49670 SQL Plan cache에 등록된 SQL 문 수행 중 Hard Parsing을 다시 진행할 때 Altibase 서버가 비정상 종료할 수 있습니다.

-   **module** : qp

-   **Category** : Fatal

-   **재현 빈도** : Unknown

-   **설명** : SQL Plan Cache에 등록된 SQL 문 수행 중 바인드 변수 변경 등으로 Hard Parsing을 다시 진행할 때 Check-In PCO 과정에서 메모리 동시성 오류로 Altibase 서버가 비정상 종료하는 현상을 수정합니다.
    
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

### BUG-49702 WITH 절 또는 인라인 뷰에 집계 함수를 포함한 서브쿼리가 WHERE 절에 사용된 경우 Altibase 서버가 비정상 종료할 수 있습니다.

-   **module** : qp-select

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : WITH 절 또는 인라인 뷰에 집계 함수를 포함한 서브쿼리가 WHERE 절에 사용된 경우 쿼리 최적화 단계에서 쿼리 변환 중 Altibase 서버가 비정상 종료하는 현상을 수정합니다.
    
-   **재현 방법**

    -   **재현 절차**

        ```sql
        DROP TABLE T1;
        CREATE TABLE T1
        (
          C1 VARCHAR(1), C2 DATE
        ) TABLESPACE SYS_TBS_DISK_DATA
        ;
        
        DROP TABLE T2;
        CREATE TABLE T2
        (
          C1 VARCHAR(1), C2 VARCHAR(1)
        ) TABLESPACE SYS_TBS_DISK_DATA
        ;
        
        DROP TABLEe T3;
        CREATE TABLE T3
        (
          C1 VARCHAR(1)
        ) TABLESPACE SYS_TBS_DISK_DATA
        ;
        
        SELECT COUNT(1)
          FROM
             (
               SELECT TO_CHAR(A.C2,'YYYY') AS DT
                 FROM T1 A, T2 X
                WHERE 1 = 1
                  AND X.C1 = A.C1
                  AND X.C2 = (SELECT MAX(C2) FROM T2 WHERE C1 = A.C1)
             ) D, T3
         GROUP BY T3.C1, D.DT;
        ```

    -   **수행 결과**

            Altibase 서버 비정상 종료

    -   **예상 결과**

        ```sql
        COUNT(1)             
        -----------------------
        No rows selected.
        ```

-   **Workaround**

    NO_UNNEST 힌트 사용

    ```sql
    SELECT COUNT(1)
      FROM
         (
           SELECT TO_CHAR(A.C2,'YYYY') AS DT
             FROM T1 A, T2 X
            WHERE 1 = 1
              AND X.C1 = A.C1
              AND X.C2 = (SELECT /*+ NO_UNNEST */ MAX(C2) FROM T2 WHERE C1 = A.C1)
         ) D, T3
     GROUP BY T3.C1, D.DT;
    ```

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    6.3.1.12.4    |          6.2.1          |    6.3.1     |        7.1.1        |            7.4.1             |

> Altibase 6.3.1 패치 버전별 히스토리는 [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7_1_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전이 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전이 변경되지 않았다.

#### CM protocol Version

통신 프로토콜 버전이 변경되지 않았다.

#### Replication protocol Version

Replication 프로토콜 버전이 변경되지 않았다.

### 프로퍼티

#### 추가된 프로퍼티

#### 변경된 프로퍼티

#### 삭제된 프로퍼티

### 성능 뷰

#### 추가된 성능 뷰

#### 변경된 성능 뷰

#### 삭제된 성능 뷰
