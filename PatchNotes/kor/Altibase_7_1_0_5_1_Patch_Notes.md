

- [Altibase 7.1.0.5.1 Patch Notes](#altibase-71051-patch-notes)
  - [New Features](#new-features)
    - [BUG-48369 Disk temp table renewal](#bug-48369disk-temp-table-renewal)
    - [BUG-48409 온라인 로그파일 생성 방식을 개선합니다.](#bug-48409%EC%98%A8%EB%9D%BC%EC%9D%B8-%EB%A1%9C%EA%B7%B8%ED%8C%8C%EC%9D%BC-%EC%83%9D%EC%84%B1-%EB%B0%A9%EC%8B%9D%EC%9D%84-%EA%B0%9C%EC%84%A0%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-48425 altiComp 유틸리티에서 3가지 유형의 비교(DIFF) 결과에 대한 로그 기록 ON/OFF 기능이 추가되었습니다.](#bug-48425alticomp-%EC%9C%A0%ED%8B%B8%EB%A6%AC%ED%8B%B0%EC%97%90%EC%84%9C-3%EA%B0%80%EC%A7%80-%EC%9C%A0%ED%98%95%EC%9D%98-%EB%B9%84%EA%B5%90diff-%EA%B2%B0%EA%B3%BC%EC%97%90-%EB%8C%80%ED%95%9C-%EB%A1%9C%EA%B7%B8-%EA%B8%B0%EB%A1%9D-onoff-%EA%B8%B0%EB%8A%A5%EC%9D%B4-%EC%B6%94%EA%B0%80%EB%90%98%EC%97%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [Fixed Bugs](#fixed-bugs)
    - [BUG-48327 Semi Join 및 Anti Join 에서 비효율적인 인덱스를 선택하는 경우가 있습니다.](#bug-48327semi-join-%EB%B0%8F-anti-join-%EC%97%90%EC%84%9C-%EB%B9%84%ED%9A%A8%EC%9C%A8%EC%A0%81%EC%9D%B8-%EC%9D%B8%EB%8D%B1%EC%8A%A4%EB%A5%BC-%EC%84%A0%ED%83%9D%ED%95%98%EB%8A%94-%EA%B2%BD%EC%9A%B0%EA%B0%80-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-48422 디스크 버퍼에 페이지를 적재하는 과정에서 BCB(Buffer Control Block)와 버퍼 프레임 간 오류 발생 시 Altibase 서버가 비정상 종료합니다.](#bug-48422%EB%94%94%EC%8A%A4%ED%81%AC-%EB%B2%84%ED%8D%BC%EC%97%90-%ED%8E%98%EC%9D%B4%EC%A7%80%EB%A5%BC-%EC%A0%81%EC%9E%AC%ED%95%98%EB%8A%94-%EA%B3%BC%EC%A0%95%EC%97%90%EC%84%9C-bcbbuffer-control-block%EC%99%80-%EB%B2%84%ED%8D%BC-%ED%94%84%EB%A0%88%EC%9E%84-%EA%B0%84-%EC%98%A4%EB%A5%98-%EB%B0%9C%EC%83%9D-%EC%8B%9C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-48477 disk hash temp 재사용을 위한 초기화 과정에서 Altibase 서버가 비정상 종료할 수 있습니다.](#bug-48477disk-hash-temp-%EC%9E%AC%EC%82%AC%EC%9A%A9%EC%9D%84-%EC%9C%84%ED%95%9C-%EC%B4%88%EA%B8%B0%ED%99%94-%EA%B3%BC%EC%A0%95%EC%97%90%EC%84%9C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)


Altibase 7.1.0.5.1 Patch Notes
==============================

New Features
------------

### BUG-48369 Disk temp table renewal

-   **module** : sm-disk-resource

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **증상** : Disk temp table renewal 반영으로 Disk hash temp table 동작이 변경되었습니다. 
    
    ORDER BY 절을 사용하지 않은 SELECT 결과 순서가 바뀔 수 있습니다.
    
    Disk temp table을 사용하는 SQL 성능이 향상됩니다.
    
    Disk temp table을 사용하는 SQL 수행 시 이전보다 메모리를 적게 사용합니다.
    
    TEMP\_MAX\_PAGE\_COUNT 프로퍼티 삭제로 TEMP\_MAX\_PAGE\_COUNT의 제약을 받지 않고 디스크 임시 테이블스페이스 전체를 활용할 수 있습니다.    

- **재현 방법**
  -   **재현 절차**
      
  -   **수행 결과**
      
  -   **예상 결과**

-   **Workaround**

- **변경사항**

  -   Performance view
      
      -   V$DISK_TEMP_STAT 성능뷰에 OVER_ALLOC_COUNT, MAX_WORK_AREA_SIZE, RUNTIME_MAP_SIZE 컬럼이 추가 되었습니다.
  - Property
    -   속성 이름 : **[HASH\_AREA\_SIZE](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_1.md#hash_area_size-단위-바이트)**
        -   최소값, 최대값 : [512K, 2^64-1]  -\> [3M, 2^64-1]
        -   변경/추가/삭제 : 최소값 변경
        
    -   속성 이름 : **TEMP\_MAX\_PAGE\_COUNT**
        
         -   변경/추가/삭제 : 삭제
        
     -   속성 이름 : **[TOTAL\_WA\_SIZE](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_1.md#total_wa_size-단위-바이트)**
          - 속성 설명 :
         정렬 또는 해싱 작업을 위해 할당할 수 있는 메모리의 최대
         크기를 지정한다.  Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의
         값을 변경할 수 있다. ~~단, 변경 요청에 대한 응답은 바로 반환되지만, 변경된 값이 실제로 서버에 적용 되는 시점은 사용 중인 임시 테이블이 없을 때까지 지연된다. 임시 테이블에 대한
         설명은 TEMP\_MAX\_PAGE\_COUNT 프로퍼티 설명을 참고하도록 한다.~~
          - 변경/추가/삭제 : 속성 설명 변경
         
     - 속성 이름 : **[INIT\_TOTAL\_WA\_SIZE](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_1.md#init_total_wa_size-단위-바이트)**

        - 속성 설명 : 정렬 또는 해싱 작업을 위해 미리 할당 할 메모리의 크기를 지정한다.

          TOTAL\_WA\_SIZE  보다 더 클 경우  TOTAL\_WA\_SIZE 까지만 생성한다.

          Altibase 운영 중 ALTER SYSTEM 문을 이용하여 이 프로퍼티의 값을 변경할 수 있다.

       - 변경/추가/삭제 : 추가
       - 공개/비공개 : 공개
       - 최소값, 최대값, 기본값 : 0, 2^64-1, 2^64-1

  -   Compile Option
  -   Error Code

### BUG-48409 온라인 로그파일 생성 방식을 개선합니다.

-   **module** : sm\_recovery

-   **Category** : Enhancement

-   **재현 빈도** : Rare

-   **증상** : 온라인 로그파일 생성 오류로 불완전한 온라인 로그파일이 생성되는 것을 방지하기 위해 온라인 로그파일 생성 방식을 개선합니다. 
    
    1. logfile.tmp 이름의 임시 파일 생성
    2. 파일 초기화 및 LOG\_FILE\_SIZE 크기만큼 확장
    3. 임시 파일을 logfile.*\#* 으로 변경
           

-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
        - **__USE_TEMP_FOR_PREPARE_LOGFILE** 
        
          -   속성 설명 : prepare online logfile 생성 시 임시 파일 생성 여부 설정
        
          - 변경/추가/삭제 : 프로퍼티 추가 
          - 공개/비공개 : 비공개
          - 최소값, 최대값, 기본값 : 0, 1, 1
          - 값
            - 0 : prepare online logfile 생성 과정에서 임시 파일을 사용하지 않습니다.
            - 1 : prepare online logfile 생성 과정에서 임시 파일을 사용합니다. 
                  ZERO_SIZE_LOG_FILE_AUTO_DELETE  프로퍼티 설정을 무시합니다.
                  Altibase 서버 구동 시점에 online logfile 크기가 1 ~ 9,999,999바이트인 경우 online logfile 크기를 확장하는 기능을 비활성화합니다. 
          - 기존 동작 유지 방법 : __USE_TEMP_FOR_PREPARE_LOGFILE = 0    
        
    -   Compile Option
    -   Error Code

### BUG-48425 altiComp 유틸리티에서 3가지 유형의 비교(DIFF) 결과에 대한 로그 기록 ON/OFF 기능이 추가되었습니다.

-   **module** : ux-audit(altiComp)

-   **Category** : Functionality

-   **재현 빈도** : Always

- **증상** : 비교(DIFF) 기능에서 3가지 유형의 레코드 비교 결과를 실행 결과 파일에 기록할 것인지 설정하는 프로퍼티가 추가되었습니다.

  -   LOG\_DF\_MOSO
  -   LOG\_MOSX
  -   LOG\_MXSO

  예를 들어, DF\_MOSO 유형의 결과를 실행 결과 파일에 기록하지 않으려면 LOG\_DF\_MOSO = OFF 로 설정합니다.

  보다 자세한 내용은 Utilities 매뉴얼을 참고하세요. [Altibase 7.1 Utilities Manual](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Utilities.md#diff-log-옵션)

-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

- **변경사항**

  - Performance view

  - Property
    -   altComp.cfg 파일에 프로퍼티 추가되었습니다.
        -   [LOG\_DF\_MOSO](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Utilities.md#log_df_moso)
        -   [LOG\_MOSX](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Utilities.md#log_mosx)
        -   [LOG\_MXSO](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Utilities.md#log_mxso)

  - Compile Option

  - Error Code

  

Fixed Bugs
----------

### BUG-48327 Semi Join 및 Anti Join 에서 비효율적인 인덱스를 선택하는 경우가 있습니다.

-   **module** : qp-dml-pvo

-   **Category** : Efficiency

-   **재현 빈도** : Always

-   **증상** : Semi Join 및 Anti Join에서 인덱스 비용을 고려하지 않아 비효율적인 인덱스를 선택하는 문제를 수정하였습니다.
    
- **재현 방법**

  - **재현 절차**

    ```sql
    DROP TABLE T1;
    CREATE TABLE T1 ( I1 INT, I2 INT, I3 INT, I4 INT, I5 INT) TABLESPACE SYS_TBS_MEM_DATA;
    ALTER TABLE T1 ADD PRIMARY KEY (I1, I2, I3);
    CREATE INDEX IDX1 ON T1(I1, I3); 
    ALTER SESSION SET EXPLAIN PLAN = ON;
    ALTER SESSION SET TRCLOG_DETAIL_PREDICATE=1;
    SELECT *
      FROM T1 A
     WHERE I1 IN (SELECT /*+ NL_SJ NO_INVERSE_JOIN */ I1
                    FROM T1 B
                   WHERE I3 > 0 AND I4 > 0);
    ```

  - **수행 결과**

    ```sql
    ------------------------------------------------------------
    PROJECT ( COLUMN_COUNT: 5, TUPLE_SIZE: 20, COST: 526.09 )
     SEMI-JOIN ( METHOD: INDEX_NL, COST: 525.43 )
      SCAN ( TABLE: SYS.T1 A, FULL SCAN, ACCESS: 0, COST: 116.76 )
      SCAN ( TABLE: SYS.T1 $$1_$$VIEW1_$B, INDEX: SYS.__SYS_IDX_ID_248, RANGE SCAN, ACCESS: 0, COST: 124.68 )
        [ VARIABLE KEY ]
       OR
        AND
         A.I1 = $$1_$$VIEW1_$B.I1
       [ VARIABLE KEY FILTER ]
       OR
        AND
         I3 > 0
       [ FILTER ]
       I4 > 0
    ------------------------------------------------------------
    ```

  -   **예상 결과**

          ------------------------------------------------------------
          PROJECT ( COLUMN_COUNT: 5, TUPLE_SIZE: 20, COST: 526.09 )
           SEMI-JOIN ( METHOD: INDEX_NL, COST: 525.43 )
            SCAN ( TABLE: SYS.T1 A, FULL SCAN, ACCESS: 0, COST: 116.76 )
            SCAN ( TABLE: SYS.T1 $$1_$$VIEW1_$B, INDEX: SYS.IDX1, RANGE SCAN, ACCESS: 0, COST: 7.93 )
             [ VARIABLE KEY ]
             OR
              AND
               A.I1 = $$1_$$VIEW1_$B.I1
               I3 > 0
             [ FILTER ]
             I4 > 0
          -----------------------------------------------------------

- **Workaround**

  ```sql
  인덱스 힌트를 사용합니다.
  SELECT *
    FROM T1 A
   WHERE I1 IN (SELECT /*+ NL_SJ NO_INVERSE_JOIN INDEX(B IDX1) */ I1
                  FROM T1 B
                 WHERE I3 > 0 AND I4 > 0);
  ```

- **변경사항**

  - Performance view
  - Property

      -   __OPTIMIZER_INDEX_NL_JOIN_ACCESS_METHOD_POLICY
          -   속성 설명 : 조인 최적화 과정에서 인덱스 선택 기준 설정 
          -   변경/추가/삭제 : 설정 값 2가 추가되었습니다. 
          -   공개/비공개 : 비공개
          -   최소값, 최대값, 기본값 : 0, 2, 0
      
  - Compile Option
    
  - Error Code

    

### BUG-48422 디스크 버퍼에 페이지를 적재하는 과정에서 BCB(Buffer Control Block)와 버퍼 프레임 간 오류 발생 시 Altibase 서버가 비정상 종료합니다.

-   **module** : sm

-   **Category** : Assert

-   **재현 빈도** : Unknown

-   **증상** : 디스크 버퍼에 페이지를 적재하는 과정에서 BCB와 버퍼 프레임 간의 연결 검증 후 잘못된 경우 Altibase 서버 비정상 종료 현상을 수정합니다.
    
-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

- **변경사항**

  - Performance view

  - Property

  - Compile Option

  - Error Code

    

### BUG-48477 disk hash temp 재사용을 위한 초기화 과정에서 Altibase 서버가 비정상 종료할 수 있습니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Rare

-   **증상** : disk hash temp 재사용을 위한 초기화 과정에서 Altibase 서버가 비정상 종료하는 현상을 수정했습니다.
    
-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

- **변경사항**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

  

Changes
-------

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 7.1.0.5.1        | 6.5.1                   | 8.9.1        | 7.1.7               | 7.4.6                        |

> Altibase 7.1 패치 버전별 히스토리는 [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7_1_Version_Histories.md)에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

> 패치를 롤백하려는 경우, [메타다운그레이드](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Installation.md#%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9Cmeta-downgrade)를 참고한다.

#### CM protocol Version

통신 프로토콜 버전은 변경되지 않았다.

#### Replication protocol Version

Replication 프로토콜 버전은 변경되지 않았다..

### 프로퍼티

#### 추가된 프로퍼티

- [INIT\_TOTAL\_WA\_SIZE](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_1.md#init_total_wa_size-단위-바이트)
- __USE_TEMP_FOR_PREPARE_LOGFILE

#### 변경된 프로퍼티

- [HASH\_AREA\_SIZE](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_1.md#hash_area_size-단위-바이트)
- [TOTAL\_WA\_SIZE](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_1.md#total_wa_size-단위-바이트)
- __OPTIMIZER_INDEX_NL_JOIN_ACCESS_METHOD_POLICY

#### 삭제된 프로퍼티

- TEMP\_MAX\_PAGE\_COUNT

### 성능 뷰

#### 추가된 성능 뷰

#### 변경된 성능 뷰

- [V$DISK_TEMP_STAT](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_3.md#vdisk_temp_stat)

#### 삭제된 성능 뷰
