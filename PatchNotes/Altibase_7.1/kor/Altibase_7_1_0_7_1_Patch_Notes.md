Altibase 7.1.0.7.1 Patch Notes
==============================

<br/>

<br/>

# Table of Contents 

- [Fixed Bugs](#fixed-bugs)

  - [BUG-49610 TO\_DATE 함수에서 날짜 형 데이터 형식으로 FF\#를 사용한 경우 \#보다 작은 자릿수를 허용합니다.](#bug-49610to_date-%ED%95%A8%EC%88%98%EC%97%90%EC%84%9C-%EB%82%A0%EC%A7%9C-%ED%98%95-%EB%8D%B0%EC%9D%B4%ED%84%B0-%ED%98%95%EC%8B%9D%EC%9C%BC%EB%A1%9C-ff%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%9C-%EA%B2%BD%EC%9A%B0-%EB%B3%B4%EB%8B%A4-%EC%9E%91%EC%9D%80-%EC%9E%90%EB%A6%BF%EC%88%98%EB%A5%BC-%ED%97%88%EC%9A%A9%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49625 TO\_DATE 함수에서 날짜형 데이터 형식으로 SSSSSS를 사용한 경우 잘못된 결과를 반환합니다.](#bug-49625to_date-%ED%95%A8%EC%88%98%EC%97%90%EC%84%9C-%EB%82%A0%EC%A7%9C%ED%98%95-%EB%8D%B0%EC%9D%B4%ED%84%B0-%ED%98%95%EC%8B%9D%EC%9C%BC%EB%A1%9C-ssssss%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%9C-%EA%B2%BD%EC%9A%B0-%EC%9E%98%EB%AA%BB%EB%90%9C-%EA%B2%B0%EA%B3%BC%EB%A5%BC-%EB%B0%98%ED%99%98%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49630 \_\_CATALOG\_SLOT\_REUSABLE 기본값을 0으로 변경합니다.](#bug-49630__catalog_slot_reusable-%EA%B8%B0%EB%B3%B8%EA%B0%92%EC%9D%84-0%EC%9C%BC%EB%A1%9C-%EB%B3%80%EA%B2%BD%ED%95%A9%EB%8B%88%EB%8B%A4)

- [Changes](#changes)

  - [Version Info](#version-info)

  - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)

  - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)

  - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

    

#  Fixed Bugs

### BUG-49610 TO\_DATE 함수에서 날짜 형 데이터 형식으로 FF\#를 사용한 경우 \#보다 작은 자릿수를 허용합니다.

-   **module** : mt

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : TO\_DATE 함수에서 날짜 형 데이터 형식으로 FF*\#*를 사용한 경우 *\#*보다 작은 자릿수를 허용합니다.
    
    FF6 이면 6자리 이하의 수 허용합니다. (=FF)
    
    FF5 이면 5자리 이하의 수 허용합니다.
    
    FF4 이면 4자리 이하의 수 허용합니다.
    
    FF3 이면 3자리 이하의 수 허용합니다.
    
    FF2 이면 2자리 이하의 수 허용합니다.
    
    FF1 이면 1자리 이하의 수 허용합니다.
    
-   **재현 방법**

    -   **재현 절차**

        ```sql
        ALTER SESSION SET DEFAULT_DATE_FORMAT = 'YYYY-MM-DD HH:MI:SS:SSSSSS';
        SELECT TO_DATE('2022-02-06 13:26:41.51001', 'yyyy-MM-dd hh24:mi:ss.ff6') FROM DUAL;
        ```

    -   **수행 결과**

        ```sql
        [ERR-21038 : Literals in the input do not match the format string.]
        ```

    -   **예상 결과**

        ```sql
        2022-02-06 13:26:41:510010
        ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49625 TO\_DATE 함수에서 날짜형 데이터 형식으로 SSSSSS를 사용한 경우 잘못된 결과를 반환합니다.

-   **module** : mt

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : TO\_DATE 함수에서 날짜형 데이터 형식으로 SSSSSS를 사용한 경우 잘못된 결과를 반환하는 오류를 수정합니다.
    
-   **재현 방법**

    -   **재현 절차**

        ```sql
        ALTER SESSION SET DEFAULT_DATE_FORMAT = 'YYYY-MM-DD HH:MI:SS:SSSSSS';
        DROP TABLE T1 CASCADE;
        CREATE TABLE T1 (C1 VARCHAR(30), C2 DATE);
        INSERT INTO T1 VALUES('2022-01-11 02:17:39.958', TO_DATE('2022-01-11 02:17:39.958', 'YYYY-MM-DD HH:MI:SS.SSSSSS'));
        SELECT C1, TO_CHAR(C2, 'YYYY-MM-DD HH24:MI:SS.FF3') FROM T1;
        ```

    -   **수행 결과**

        ```sql
        iSQL> SELECT C1, TO_CHAR(C2, 'YYYY-MM-DD HH24:MI:SS.FF3') FROM T1;
        C1                              TO_CHAR(C2,'YYYY-MM-DDHH24:MI:SS.FF3')                  
        -----------------------------------------------------------------------------------------------------
        2022-01-11 02:17:39.958         2022-01-11 02:17:39.000                                 
        1 row selected.
        ```

    -   **예상 결과**

        ```sql
        iSQL> SELECT C1, TO_CHAR(C2, 'YYYY-MM-DD HH24:MI:SS.FF3') FROM T1;
        C1                              TO_CHAR(C2,'YYYY-MM-DDHH24:MI:SS.FF3')                  
        -----------------------------------------------------------------------------------------------------
        2022-01-11 02:17:39.958         2022-01-11 02:17:39.958                                 
        1 row selected.
        ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49630 \_\_CATALOG\_SLOT\_REUSABLE 기본값을 0으로 변경합니다.

-   **module** : sm

-   **Category** : Other

-   **재현 빈도** : Always

-   **설명** : \_\_CATALOG\_SLOT\_REUSABL 기본값을 0으로 변경합니다.

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
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    7.1.0.7.1     |          6.5.1          |    8.10.1    |        7.1.7        |            7.4.7             |

> Altibase 7.1 패치 버전별 히스토리는 [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7_1_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

#### Meta Version

메타 버전은 변경되지 않았다.

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
