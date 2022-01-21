
**Table of Contents**  

- [Altibase 7.1.0.5.8 Patch Notes](#altibase-71058-patch-notes)
  - [New Features](#new-features)
    - [BUG-47815 쿼리 프로세싱(QP) 모듈 관련한 트레이스 로깅 레벨이 잘못 설정된 부분을 수정하고 작업 스케줄러 수행 관련 로깅 레벨을 추가합니다.](#bug-47815%EC%BF%BC%EB%A6%AC-%ED%94%84%EB%A1%9C%EC%84%B8%EC%8B%B1qp-%EB%AA%A8%EB%93%88-%EA%B4%80%EB%A0%A8%ED%95%9C-%ED%8A%B8%EB%A0%88%EC%9D%B4%EC%8A%A4-%EB%A1%9C%EA%B9%85-%EB%A0%88%EB%B2%A8%EC%9D%B4-%EC%9E%98%EB%AA%BB-%EC%84%A4%EC%A0%95%EB%90%9C-%EB%B6%80%EB%B6%84%EC%9D%84-%EC%88%98%EC%A0%95%ED%95%98%EA%B3%A0-%EC%9E%91%EC%97%85-%EC%8A%A4%EC%BC%80%EC%A4%84%EB%9F%AC-%EC%88%98%ED%96%89-%EA%B4%80%EB%A0%A8-%EB%A1%9C%EA%B9%85-%EB%A0%88%EB%B2%A8%EC%9D%84-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-49108 작업 스케줄러(Job Scheduler) 수행 기록을 위한 altibase_job.log를 추가합니다.](#bug-49108%EC%9E%91%EC%97%85-%EC%8A%A4%EC%BC%80%EC%A4%84%EB%9F%ACjob-scheduler-%EC%88%98%ED%96%89-%EA%B8%B0%EB%A1%9D%EC%9D%84-%EC%9C%84%ED%95%9C-altibase_joblog%EB%A5%BC-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-49122 PUBLIC 롤(Role) 이 삭제된 경우 aexport 수행 시 segmentaion faulut 에러가 발생합니다.](#bug-49122public-%EB%A1%A4role-%EC%9D%B4-%EC%82%AD%EC%A0%9C%EB%90%9C-%EA%B2%BD%EC%9A%B0-aexport-%EC%88%98%ED%96%89-%EC%8B%9C-segmentaion-faulut-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-49136 UNION ALL 을 사용하여 생성한 뷰에 대해 INSERT 문 수행 시 Altibase 서버가 비정상 종료합니다.](#bug-49136union-all-%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%98%EC%97%AC-%EC%83%9D%EC%84%B1%ED%95%9C-%EB%B7%B0%EC%97%90-%EB%8C%80%ED%95%B4-insert-%EB%AC%B8-%EC%88%98%ED%96%89-%EC%8B%9C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)



Altibase 7.1.0.5.8 Patch Notes
==============================

New Features
------------

### BUG-47815 쿼리 프로세싱(QP) 모듈 관련한 트레이스 로깅 레벨이 잘못 설정된 부분을 수정하고 작업 스케줄러 수행 관련 로깅 레벨을 추가합니다.

-   **module** : qp-psm-trigger-execute

-   **Category** : Maintainability

-   **재현 빈도** : Always

-   **설명** : 쿼리 프로세싱(QP) 모듈 관련한 트레이스 로깅 레벨이 잘못 설정된 부분을 수정하고 작업 스케줄러 수행 관련 로깅 레벨을 추가합니다. 추가된 로깅 레벨은 V\$TRACELOG에서 확인할 수 있습니다.
    
-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
        -   V\$TRACELOG

            쿼리 프로세싱 관련 TRCLEVEL 3 Job Scheduler Trace Log, TRCLEVEL 4 DCL Trace Log 가 추가되었다.

            ```sql
            iSQL> SELECT MODULE_NAME, TRCLEVEL, FLAG, POWLEVEL, DESCRIPTION FROM V$TRACELOG WHERE MODULE_NAME = 'QP';
            MODULE_NAME                TRCLEVEL    FLAG                       POWLEVEL             DESCRIPTION                
            ------------------------------------------------------------------------------------------------------------------------
            QP                         1           X                          1                    PSM Error Line Trace Log   
            QP                         2           O                          2                    DDL Trace Log              
            QP                         3           X                          4                    Job Scheduler Trace Log    
            QP                         4           X                          8                    DCL Trace Log              
            QP                         5           X                          16                   ---                        
            QP                         6           X                          32                   ---                        
            ...중략...
            QP                         31          X                          1073741824           ---                        
            QP                         32          X                          2147483648           Debug                      
            QP                         99          SUM                        2                    Total Sum of Trace Log Va  
                                                                                                   lues                       
            33 rows selected.
            ```
        
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49108 작업 스케줄러(Job Scheduler) 수행 기록을 위한 altibase_job.log를 추가합니다.

-   **module** : qp

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : 작업 스케줄러(Job Scheduler) 수행 기록을 위한 트레이스 로그 altibase\_job.log를 추가합니다. 
    
    생성 위치는 \$ALTIBASE\_HOME/trc (SERVER\_MSGLOG\_DIR 프로퍼티 기본설정) 입니다.
    
    작업 스케줄러 관련한 트레이스 로그 분리로 다음 프로퍼티들이 추가되었습니다.

    - JOB\_MSGLOG\_FILE
    
    - JOB\_MSGLOG\_SIZE
    
    - JOB\_MSGLOG\_COUNT
    
    - JOB\_MSGLOG\_FLAG
    
    프로퍼티에 관한 설명은 property 부분을 참고하세요.
    
-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
        -   V\$TRACELOG

            작업 스케줄러 관련 로그 수준이 추가되었다.

            ```sql
            iSQL> SELECT MODULE_NAME, TRCLEVEL, FLAG, POWLEVEL, DESCRIPTION FROM V$TRACELOG WHERE MODULE_NAME = 'JOB';
            MODULE_NAME                TRCLEVEL    FLAG                       POWLEVEL             DESCRIPTION                
            ------------------------------------------------------------------------------------------------------------------------
            JOB                        1           O                          1                    JOB Trace Log              
            JOB                        2           X                          2                    ---                        
            JOB                        3           X                          4                    ---                        
            ...중략...
            JOB                        31          X                          1073741824           ---                        
            JOB                        32          X                          2147483648           Debug                      
            JOB                        99          SUM                        1                    Total Sum of Trace Log Va  
                                                                                                   lues                       
            33 rows selected.
            ```
            
            
        
    -   Property
        -   **JOB\_MSGLOG\_FILE 프로퍼티 추가**
            - 설명
            
              작업 스케줄러 수행 로그를 기록하는 파일이다.
            
            - 기본값
            
              altibase\_job.log
            
            - 속성
            
              읽기 전용, 단일 값
            
        - **JOB\_MSGLOG\_SIZE 프로퍼티 추가**
          
          - 설명
          
            작업 스케줄러 트레이스 로그 파일의 최대 크기를 지정한다. 값의 범위는 [0, 232-1] 이다. 
          
          - 기본값
            
            10 \* 1024 \* 1024
            
          - 속성
          
            읽기 전용, 단일 값
          
        - **JOB\_MSGLOG\_COUNT 프로퍼티 추가**
        
          - 설명
        
            작업 스케줄러 트레이스 로그 파일의 최대 개수를 지정한다. 값의 범위는 [0, 232-1] 이다.
        
          - 기본값
            
            10
            
          - 속성
        
            읽기 전용, 단일 값
        
        - **JOB\_MSGLOG\_FLAG 프로퍼티 추가**
        
          - 설명
            
            작업 스케줄러(Job Scheduler) 수행 기록 설정 및 로그 수준 설정
            이 프로퍼티의 값은 V\$TRACELOG 의 POWLEVEL 조합으로 설정한다. 
            
            아래 예에서 TRCLEVEL 1 JOB Trace Log가 설정된 상태이다. 설정 여부는 FLAG 값으로 확인할 수 있다. TRCLEVEL 1 JOB Trace Log과 TRCLEVEL 32 Debug 외에 다른 TRCLEVEL은 정의되지 않은 상태이다.
            
            ```sql
            iSQL> SELECT MODULE_NAME, TRCLEVEL, FLAG, POWLEVEL, DESCRIPTION FROM V$TRACELOG WHERE MODULE_NAME = 'JOB';
            MODULE_NAME                TRCLEVEL    FLAG                       POWLEVEL             DESCRIPTION                
            ------------------------------------------------------------------------------------------------------------------------
            JOB                        1           O                          1                    JOB Trace Log              
            JOB                        2           X                          2                    ---                        
            JOB                        3           X                          4                    ---                        
            ...중략...
            JOB                        31          X                          1073741824           ---                        
            JOB                        32          X                          2147483648           Debug                      
            JOB                        99          SUM                        1                    Total Sum of Trace Log Va  
                                                                                                   lues                       
            33 rows selected.
            ```
            
          - 기본값
            
            1
            
          - 속성
          
            변경 가능, 공개
        
    -   Compile Option
    -   Error Code

Fixed Bugs
----------

### BUG-49122 PUBLIC 롤(Role) 이 삭제된 경우 aexport 수행 시 segmentaion faulut 에러가 발생합니다.

-   **module** : ux-aexport

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : PUBLIC 롤(Role) 이 삭제된 경우 aexport 수행 시 segmentaion faulut 에러가 발생하는 현상을 수정하였습니다.
    
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

### BUG-49136 UNION ALL 을 사용하여 생성한 뷰에 대해 INSERT 문 수행 시 Altibase 서버가 비정상 종료합니다.

-   **module** : qp

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : UNION ALL 을 사용하여 생성한 뷰에 대해 INSERT 문 수행 시
    Altibase 서버가 비정상 종료하는 현상을 수정하였습니다.

- **재현 방법**

  - **재현 절차**

    ```sql
    CREATE TABLE T2 (I1 INTEGER PRIMARY KEY);
    CREATE VIEW V2 AS SELECT * FROM T2 UNION ALL SELECT * FROM T2;
    INSERT INTO V2(I1,I2) VALUES (12, 12);
    ```

  -   **수행 결과**

          ERR-31455 : Failed to work because an internal exception occurred from an OS.[Contact Altibase's Support Center] 에러가 발생하거나Altibase 서버 비정상 종료

  -   **예상 결과**

          [ERR-313A4 : Cannot modify a column for a non key-preserved table]

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

Changes
-------

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    7.1.0.5.8     |          6.5.1          |    8.9.1     |        7.1.7        |            7.4.6             |

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

- JOB_MSGLOG_FILE
- JOB_MSGLOG_SIZE
- JOB_MSGLOG_COUNT 
- JOB_MSGLOG_FLAG

#### 변경된 프로퍼티

#### 삭제된 프로퍼티

### 성능 뷰

#### 추가된 성능 뷰

#### 변경된 성능 뷰

- V$TRACELOG

#### 삭제된 성능 뷰
