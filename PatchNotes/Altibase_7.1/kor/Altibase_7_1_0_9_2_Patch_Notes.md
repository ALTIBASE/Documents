# Altibase 7.1.0.9.2 Patch Notes

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [New Features](#new-features)
    - [BUG-50703 Row Referencing 절을 사용하는 트리거에서 사용하지 않는 컬럼을 내부적으로 복사하지 않도록 개선합니다.](#bug-50703)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-50527 NVL\_EQUAL, NVL\_NOT\_EQUAL 의 인자로 인덱스 컬럼에 대한 연산식을 적용할 경우 서버가 비정상 종료합니다.](#bug-50527)
    - [BUG-50542 하이브리드 파티션드 테이블이면서 GEOMETRY 컬럼 또는 LOB 컬럼이 포함되고 update trigger로 설정 된 경우, multiple update 구문 수행 시 비정상 종료 발생 합니다.](#bug-50542)
    - [BUG-50660 REFERENCING NEW ROW절을 사용하는 트리거가 참조하 테이블의 테이블 스페이스를 변경 후 트리거 동작시, 서버가 비정상 종료하는 경우가 있어서 수정합니다.](#bug-50660)
    - [BUG-50686 V\$TIME\_ZONE\_NAMES에서 America/Porto\_Velho 타임존의 UTC\_OFFSET 값이 올바르지 않습니다.](#bug-50686)
    - [BUG-50697 JDBC 에서 PreparedStatement를 이용하여 ping 쿼리 사용시 메모리 누수가 발생합니다.](#bug-50697)
    - [BUG-50700 하이브리드 파티션드 테이블에서 컬럼 제약을 체크하는 로직에서 잘못된 row offset 정보로 인해 잘못된(invalid) 메모리 접근의 오류가 발생할 수 있습니다.](#bug-50700)
  - [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# New Features

### BUG-50703<a name=bug-50703 ></a> Row Referencing 절을 사용하는 트리거에서 사용하지 않는 컬럼을 내부적으로 복사하지 않도록 개선합니다.

- **module** : qp-psm-trigger-execute

- **Category** : Enhancement

- **재현 빈도** : Always

- **설명** : Row Referencing 절을 사용하는 트리거가 실행될 때, 내부적으로 참조 레코드를 특정 변수에 복사하여 처리하는데, 이 과정에서 불필요한 컬럼도 복사 되었습니다. 이제는 실제로 사용되는 컬럼만 복사하도록 개선되었습니다. 

  이 패치의 적용으로 Referencing 절을 사용하는 트리거에서 LOB 컬럼을 사용하지 않는 경우, [ERR-21031 : Unable to convert the data type.] 오류가 발생하는 문제가 해결되었습니다.

  또한, 트리거의 동작을 유발하는 DML의 실행 성능이 개선되었습니다.

  > 주의: 이번 패치에서는 아래의 문제는 해결되지 않습니다.
  >
  > * 100MB이상의 LOB 데이터가 있는 테이블에 Row Referencing 절을 사용하는 트리거에서 실제로 LOB 컬럼을 참조하는 경우, [ERR-21031 : Unable to convert the data type.] 오류가 발생할 수 있습니다.

- **재현 방법**

  -   **재현 절차**
  -   **수행 결과**
  -   **예상 결과**

- **Workaround**

- **변경사항**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

Fixed Bugs
==========

### BUG-50527<a name=bug-50527 ></a> NVL\_EQUAL, NVL\_NOT\_EQUAL 의 인자로 인덱스 컬럼에 대한 연산식을 적용할 경우 서버가 비정상 종료합니다.

-   **module** : mt

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : NVL_EQUAL(), NVL_NOT_EQUAL() 함수의 인자로 인덱스 컬럼에 대한 연산식을 적용하는 경우, 서버가 비정상 종료하는 문제를 수정하였습니다.

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

### BUG-50542<a name=bug-50542 ></a> 하이브리드 파티션드 테이블이면서 GEOMETRY 컬럼 또는 LOB 컬럼이 포함되고 update trigger로 설정 된 경우, multiple update 구문 수행 시 비정상 종료 발생 합니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : 아래의 경우를 모두 만족하는 특정한 상황에서 mltiple update 구문 수행시 발생하는 비정상 종료 문제를 수정하였습니다.
    
    - 하이브리드 파티션드 테이블이면서 GEOMETRY 컬럼 또는 LOB 컬럼이 포함되어 있는경우
    - update trigger event가 설정되어 있는 경우
    
- **재현 방법**

  - **재현 절차**

    ```sql
    DROP TABLE T1;
    DROP TABLE T2;
    
    CREATE TABLE T1 ( I1 INTEGER, I2 FLOAT, I3 GEOMETRY  ) 
     PARTITION BY RANGE(I1) 
     ( PARTITION P1 VALUES DEFAULT TABLESPACE SYS_TBS_disk_DATA )
     TABLESPACE SYS_TBS_mem_DATA;
    
    CREATE TABLE T2 (I1 INTEGER, I2 VARCHAR(1000) );
     
    CREATE TRIGGER AFTER_UPDATE AFTER UPDATE ON T1
    REFERENCING 
    OLD AS OLDROW
    NEW AS NEWROW 
    FOR EACH ROW 
    AS 
    BEGIN 
    INSERT INTO T2 VALUES (7777, 'AFTER UPDATE'); 
    END;
    /
     
    INSERT INTO T1(I2) VALUES (178);
    UPDATE T1 LEFT OUTER JOIN T2 ON T1.I1 = T2.I1 SET T1.I1 = T1.I1 + 5, T2.I1 = T2.I1 + 10;
    ```

  - **수행 결과**

    ```sql
    [ERR-91015 : Communication failure.]
    ```

  -   **예상 결과**

      ```sql
      [ERR-1105F : No more than one update cursor can be used on a table.at "SYS.AFTER_UPDATE", line 8]
      ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50660<a name=bug-50660 ></a> REFERENCING NEW ROW절을 사용하는 트리거가 참조하 테이블의 테이블 스페이스를 변경 후 트리거 동작시, 서버가 비정상 종료하는 경우가 있어서 수정합니다.

-   **module** : qp-ddl-dcl-execute

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : 트리거가 동작할때, 아래의 조건을 모두 만족하는 경우 비정상 종료하는 문제를 수정하였습니다.

    1. REFERENCING NEW ROW절을 사용하는 트리거가  참조하는 테이블이 있고,
    2. 이 테이블의 테이블 스페이스를 아래와 같이 변경한 후

    * 메모리 테이블 스페이스라면, 디스크 테이블 스페이스로 변경 

    * 디스크 테이블 스페이스라면, 메모리 테이블 스페이스로 변경
    
    3. 트리거가 동작하면서 trigger_event에 정의된 DML을 수행
    
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

### BUG-50686<a name=bug-50686 ></a> V\$TIME\_ZONE\_NAMES에서 America/Porto\_Velho 타임존의 UTC\_OFFSET 값이 올바르지 않습니다.

-   **module** : mt

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : V\$TIME\_ZONE\_NAMES에서 America/Porto\_Velho 타임존의
    UTC\_OFFSET 값이 잘못된 값인 "04:00"으로 표시되고 있어서, 올바른
    값인 "-04:00" 로 수정합니다.

- **재현 방법**

  - **재현 절차**

    ```sql
    select * from v$time_zone_names where name='America/Porto_Velho';
    ```

  - **수행 결과**

    ```sql
    NAME                                      UTC_OFFSET
    ---------------------------------------------------------
    America/Porto_Velho                       04:00
    ```

  -   **예상 결과**

      ```sql
      NAME                                      UTC_OFFSET
      ---------------------------------------------------------
      America/Porto_Velho                       -04:00
      ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50697<a name=bug-50697 ></a> JDBC 에서 PreparedStatement를 이용하여 ping 쿼리 사용시 메모리 누수가 발생합니다.

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : JDBC 에서 PreparedStatement를 이용하여 ping 쿼리 사용시 메모리 누수가 발생하는 문제를 수정하였습니다. 이 버그를 적용하려면 JDBC 드라이버를 패치해야 합니다.
    
- **재현 방법**

  - **재현 절차**

    ```java
    Connection sConn = getConnection("20300");
    PreparedStatement sStmt = sConn.prepareStatement("/* PING */ SELECT 1 ");
    ResultSet sRs = sStmt.executeQuery();
    if (sRs.next())
    {
        sRs.close();
    }
    sStmt.executeQuery();
    sStmt.executeQuery();
    sStmt.executeQuery();
    sStmt.close();
    sConn.close();
    ```

  -   **수행 결과**

          메모리 사용량이 계속 증가함

  -   **예상 결과**

          메모리 사용량이 계속 증가하지 않음

-   **Workaround**

        ping 쿼리 대신 select 1 from dual 사용

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50700<a name=bug-50700 ></a> 하이브리드 파티션드 테이블에서 컬럼 제약을 체크하는 로직에서 잘못된 row offset 정보로 인해 잘못된(invalid) 메모리 접근의 오류가 발생할 수 있습니다.

-   **module** : qp

-   **Category** : Memory Error

-   **재현 빈도** : Always

-   **설명** : 하이브리드 파티션드 테이블에서 컬럼 제약을 체크하는
    로직에서 잘못된 row offset 정보로 인한 잘못된(invalid) 메모리 접근의
    오류가 발생하지 않도록 수정합니다.

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
-------

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 7.1.0.9.2        | 6.5.1                   | 8.11.1       | 7.1.7               | 7.4.7                        |

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
