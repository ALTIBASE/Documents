Altibase 7.1.0.7.7 Patch Notes
==============================

<br/>

<br/>

# Table of Contents

- [Fixed Bugs](#fixed-bugs)
  - [BUG-49746 윈도우(분석) 함수, ORDER BY 절, GROUP BY 절을 사용한 질의문에서 디스크 임시 공간을 사용하면 결과 오류가 발생합니다.](#bug-49746%EC%9C%88%EB%8F%84%EC%9A%B0%EB%B6%84%EC%84%9D-%ED%95%A8%EC%88%98-order-by-%EC%A0%88-group-by-%EC%A0%88%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%9C-%EC%A7%88%EC%9D%98%EB%AC%B8%EC%97%90%EC%84%9C-%EB%94%94%EC%8A%A4%ED%81%AC-%EC%9E%84%EC%8B%9C-%EA%B3%B5%EA%B0%84%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%98%EB%A9%B4-%EA%B2%B0%EA%B3%BC-%EC%98%A4%EB%A5%98%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49756 INSERT 문 values 절에 NOT NULL 제약 조건을 가진 LOB 컬럼에 EMPTY\_CLOB() 또는 EMPTY\_BLOB() 함수를 사용하면 ERR-31074 : Unable to insert (or update) NULL into NOT NULL column. 에러가 발생합니다.](#bug-49756insert-%EB%AC%B8-values-%EC%A0%88%EC%97%90-not-null-%EC%A0%9C%EC%95%BD-%EC%A1%B0%EA%B1%B4%EC%9D%84-%EA%B0%80%EC%A7%84-lob-%EC%BB%AC%EB%9F%BC%EC%97%90-empty_clob-%EB%98%90%EB%8A%94-empty_blob-%ED%95%A8%EC%88%98%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EB%A9%B4-err-31074--unable-to-insert-or-update-null-into-not-null-column-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49767 REGEXP\_LIKE 함수에서 정규 표현식에 한글 사용 시 ERR-2105A : The pattern contains an invalid range. 에러가 발생합니다. 한글 검색 지원을 위해 PCRE2 라이브러리을 사용한 정규 표현식 방식을 추가합니다.](#bug-49767regexp_like-함수에서-정규-표현식에-한글-사용-시-err-2105a--the-pattern-contains-an-invalid-range-에러가-발생합니다-한글-검색-지원을-위해-pcre2-라이브러리을-사용한-정규-표현식-방식을-추가합니다)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
  - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
  - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<br/>

Fixed Bugs
==========

### BUG-49746 윈도우(분석) 함수, ORDER BY 절, GROUP BY 절을 사용한 질의문에서 디스크 임시 공간을 사용하면 결과 오류가 발생합니다.

-   **module** : qp-select

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 아래 조건을 모두 만족하는 질의문 수행 시 결과 오류가 발생합니다.
    
    - 윈도우(분석) 함수 사용
    
    - GROUP BY 절, ORDER BY 절, 윈도우(분석) 함수 사용
    
    - ORDER BY 절에 사용된 컬럼이 윈도우(분석) 함수 OVER 절에서 같은 순서로 사용
    
    - ORDER BY 절에 사용된 컬럼이 SELECT 절에서 표현식으로 사용

    - 쿼리 수행 시 디스크 임시 공간 사용

    이 버그 현상을 회피하는 방법은  Work Around 부분을 확인해주세요.

    **패치 시 주의 사항**

    결괏값 오류를 개선한 버그로, 패치 후 버그 조건에 만족하는 질의문 수행 시 결과가 달라질 수 있습니다.

-   **재현 방법**

    -   **재현 절차**

        ```sql
        DROP TABLE T1;
        
        CREATE TABLE T1 ( I1 CHAR(8), I2 FLOAT ) TABLESPACE SYS_TBS_DISK_DATA;
        INSERT INTO T1 VALUES ('20220127', 0);
        INSERT INTO T1 VALUES ('20220127', 1);
        INSERT INTO T1 VALUES ('20220127', 2);
        INSERT INTO T1 VALUES ('20220126', 10);
        INSERT INTO T1 VALUES ('20220126', 15);
        INSERT INTO T1 VALUES ('20220125', 30);
        
        SELECT ROW_NUMBER() OVER(ORDER BY A.I1 DESC) RNUM
             , TO_CHAR(TO_DATE(A.I1, 'YYYYMMDD'), 'YYYY-MM-DD') AS YYYYMMDD
             , SUM(A.I2) AS CNT
          FROM T1 A
         GROUP BY A.I
         ORDER BY A.I1 DESC;
        ```

    -   **수행 결과**

        ```sql
        RNUM                 YYYYMMDD              CNT         
        -----------------------------------------------------------
        1                    2022-01-25            3           
        2                    2022-01-25            25          
        3                    2022-01-25            30          
        3 rows selected.
        ```

    -   **예상 결과**

        ```sql
        RNUM                 YYYYMMDD              CNT         
        -----------------------------------------------------------
        1                    2022-01-27            3           
        2                    2022-01-26            25          
        3                    2022-01-25            30          
        3 rows selected.
        ```

-   **Workaround**

    이 버그 현상은 `TEMP_TBS_MEMORY` 힌트로 회피할 수 있습니다. 

    ```sql
    SELECT /*+ TEMP_TBS_MEMORY */ ROW_NUMBER() OVER(ORDER BY A.I1 DESC) RNUM
         , TO_CHAR(TO_DATE(A.I1, 'YYYYMMDD'), 'YYYY-MM-DD') AS YYYYMMDD
         , SUM(A.I2) AS CNT
      FROM T1 A
     GROUP BY A.I
     ORDER BY A.I1 DESC;
    ```
    
-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49756 INSERT 문 values 절에 NOT NULL 제약 조건을 가진 LOB 컬럼에 EMPTY\_CLOB() 또는 EMPTY\_BLOB() 함수를 사용하면 ERR-31074 : Unable to insert (or update) NULL into NOT NULL column. 에러가 발생합니다.

-   **module** : qp-dml-execute

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : INSERT 문 values 절에 NOT NULL 제약 조건을 가진 LOB 컬럼에 EMPTY\_CLOB() 또는 EMPTY\_BLOB() 함수를 사용하면 ERR-31074 : Unable to insert (or update) NULL into NOT NULL column. 에러가 발생하는 현상을 수정합니다.
    
-   **재현 방법**

    -   **재현 절차**

            CREATE TABLE t1(c1 CLOB NOT NULL);INSERT INTO t1 VALUES(EMPTY_CLOB());

    -   **수행 결과**

            [ERR-31074 : Unable to insert (or update) NULL into NOT NULL column. : C1]

    -   **예상 결과**

            1 row inserted.

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49767 REGEXP\_LIKE 함수에서 정규 표현식에 한글 사용 시 ERR-2105A : The pattern contains an invalid range. 에러가 발생합니다. 한글 검색 지원을 위해 PCRE2 라이브러리을 사용한 정규 표현식 방식을 추가합니다.

-   **module** : qp

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **설명** : 펄 호환 정규 표현식 (Perl Compatible Regular Expressions, PCRE2) 라이브러리을 사용한 정규 표현식 방식을 추가합니다. 기존 정규 표현식 처리 방식에서 지원하지 않는 한글 검색이 가능하며 아래와 같은 검색 기능이 추가되었습니다.
    
    - 역참조(Backreference)

    - 전방 탐색(Lookahead)

    - 후방 탐색(Lookbehind)

    - 조건부 정규 표현식(Conditional pattern)

    - 문자 속성 정규 표현식(Character with the xx property)

    PCRE2 라이브러리의 정규 표현식을 사용하려면 REGEXP\_MODE 프로퍼티 값을 1로 변경해야 합니다. 프로퍼티에 관한 설명은 property 부분을 참고하세요. 
    
    Altibase 기존 정규 표현식 라이브러리와 일부 기능에서 문법 차이가 있습니다. 
    
    보다 자세한 내용은 [SQL Reference-A.부록: 정규 표현식](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/SQL%20Reference.md#a%EB%B6%80%EB%A1%9D-%EC%A0%95%EA%B7%9C-%ED%91%9C%ED%98%84%EC%8B%9D) 매뉴얼을 참고하시기 바랍니다.
    
    Altibase 에서 사용한 PCRE2 라이브러리의 버전은 10.40 입니다. PCRE2 라이브러리에 대한 자세한 내용은 [PCRE2 홈페이지](https://www.pcre.org/)를 참조하세요. 
    
-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
    
    -   Property
        
        정규 표현식 처리 방식을 설정하는 Altibase 서버 프로퍼티가 추가되었습니다.
    
        - **이름**
          REGEXP_MODE
        
        - **설명**
          ​정규 표현식 처리 방식을 설정하는 프로퍼티이다.
    
          - 0
          
            POSIX Basic Regular Expression(BRE)과 Extended Regular Expression(ERE)를 일부 지원하는 Altibase 정규 표현식 라이브러리
          
          - 1
    
            펄 호환 정규 표현식 (Perl Compatible Regular Expressions, PCRE2) 라이브러리
          
            Altibase 서버 캐릭터셋이 US7ASCII 또는 UTF-8 에서만 지원한다.
          
        - **기본값**
          0
        
        - **속성**
          변경 가능, 단일 값
        
    -   Compile Option
    
    -   Error Code
        
        ```
        0x2106B ( 135275) mtERR_ABORT_PCRE2_NOT_SUPPORTED_ENCODING Unsupported character set by PCRE2 library 
        # *Cause : The current session processes regular expression using the PCRE2 library. In this case, the Altibase server character set must be a character set supported by the PCRE2 library.
        # *Action :
        # - Check the character sets supported by the PCRE2 library in functions section in SQL Reference.
        # - Check the Altibase server character set.
        # - If the Altibase server character set is not supported by the PCRE2 library, change the value of the REGEXP_MODE property to 0.
        # - To process the regular expression using the PCRE2 library, Altibase server has to change its character set to another one that is supported by PCRE2 library. This requires recreating database.
        ```
        
        ```
        0x2106C ( 135276) mtERR_ABORT_PCRE2_UNEXPECTED_ERROR PCRE2 error: <1%s> (occurred in <0%s>) 
        # *Cause: An internal error occurred in PCRE2 library or while executing Altibase internal function.
        # *Action: Check the error message and contact Altibase's Support Center (http://support.altibase.com).
        ```
        

<br/>

Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    7.1.0.7.7     |          6.5.1          |    8.10.1    |        7.1.7        |            7.4.7             |

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

- REGEXP_MODE

#### 변경된 프로퍼티

#### 삭제된 프로퍼티

### 성능 뷰

#### 추가된 성능 뷰

#### 변경된 성능 뷰

#### 삭제된 성능 뷰
