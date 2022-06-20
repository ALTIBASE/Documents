

Altibase 7.1.0.7.6 Patch Notes
==============================

<br/>

<br/>

# **Table of Contents** 

- [New Features](#new-features)
  - [BUG-49645 이중화 송신자에게 고정 IP 주소를 할당하는 기능을 추가합니다.](#bug-49645%EC%9D%B4%EC%A4%91%ED%99%94-%EC%86%A1%EC%8B%A0%EC%9E%90%EC%97%90%EA%B2%8C-%EA%B3%A0%EC%A0%95-ip-%EC%A3%BC%EC%86%8C%EB%A5%BC-%ED%95%A0%EB%8B%B9%ED%95%98%EB%8A%94-%EA%B8%B0%EB%8A%A5%EC%9D%84-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49747 Altibase 7 이상에서 Altibase 6.3.1 옵티마이저와 동일한 비용 계산식을 설정하는 기능을 추가합니다.](#bug-49747altibase-7-%EC%9D%B4%EC%83%81%EC%97%90%EC%84%9C-altibase-631-%EC%98%B5%ED%8B%B0%EB%A7%88%EC%9D%B4%EC%A0%80%EC%99%80-%EB%8F%99%EC%9D%BC%ED%95%9C-%EB%B9%84%EC%9A%A9-%EA%B3%84%EC%82%B0%EC%8B%9D%EC%9D%84-%EC%84%A4%EC%A0%95%ED%95%98%EB%8A%94-%EA%B8%B0%EB%8A%A5%EC%9D%84-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
- [Fixed Bugs](#fixed-bugs)
  - [BUG-49451 저장 프로시저 바디에서 사용한 SQL 문의 LOOP 절에 호스트 변수 또는 지역 변수 사용 시 ERR-31248 : Mismatched bind column count 에러가 발생합니다.](#bug-49451%EC%A0%80%EC%9E%A5-%ED%94%84%EB%A1%9C%EC%8B%9C%EC%A0%80-%EB%B0%94%EB%94%94%EC%97%90%EC%84%9C-%EC%82%AC%EC%9A%A9%ED%95%9C-sql-%EB%AC%B8%EC%9D%98-loop-%EC%A0%88%EC%97%90-%ED%98%B8%EC%8A%A4%ED%8A%B8-%EB%B3%80%EC%88%98-%EB%98%90%EB%8A%94-%EC%A7%80%EC%97%AD-%EB%B3%80%EC%88%98-%EC%82%AC%EC%9A%A9-%EC%8B%9C-err-31248--mismatched-bind-column-count-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49556 매개변수 값을 설정하지 않고 ParameterMetaData 메소드로 매개변수 정보를 조회하면 NullPointerException 에러가 발생합니다.](#bug-49556%EB%A7%A4%EA%B0%9C%EB%B3%80%EC%88%98-%EA%B0%92%EC%9D%84-%EC%84%A4%EC%A0%95%ED%95%98%EC%A7%80-%EC%95%8A%EA%B3%A0-parametermetadata-%EB%A9%94%EC%86%8C%EB%93%9C%EB%A1%9C-%EB%A7%A4%EA%B0%9C%EB%B3%80%EC%88%98-%EC%A0%95%EB%B3%B4%EB%A5%BC-%EC%A1%B0%ED%9A%8C%ED%95%98%EB%A9%B4-nullpointerexception-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49573 multiple update 구문에서 대상 테이블에 함수 기반 인덱스가 사용되고 SET 절에 서브쿼리가 사용된 경우 발생하는 메모리 오류를 개선합니다.](#bug-49573multiple-update-%EA%B5%AC%EB%AC%B8%EC%97%90%EC%84%9C-%EB%8C%80%EC%83%81-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90-%ED%95%A8%EC%88%98-%EA%B8%B0%EB%B0%98-%EC%9D%B8%EB%8D%B1%EC%8A%A4%EA%B0%80-%EC%82%AC%EC%9A%A9%EB%90%98%EA%B3%A0-set-%EC%A0%88%EC%97%90-%EC%84%9C%EB%B8%8C%EC%BF%BC%EB%A6%AC%EA%B0%80-%EC%82%AC%EC%9A%A9%EB%90%9C-%EA%B2%BD%EC%9A%B0-%EB%B0%9C%EC%83%9D%ED%95%98%EB%8A%94-%EB%A9%94%EB%AA%A8%EB%A6%AC-%EC%98%A4%EB%A5%98%EB%A5%BC-%EA%B0%9C%EC%84%A0%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49690 ALTER REPLICATION replication\_name BUILD OFFLINE META 구문 수행 시 송신자 메타 파일 또는 Restart SN 파일이 유효하지 않을 경우 반환하는 에러 메시지를 개선합니다.](#bug-49690alter-replication-replication_name-build-offline-meta-%EA%B5%AC%EB%AC%B8-%EC%88%98%ED%96%89-%EC%8B%9C-%EC%86%A1%EC%8B%A0%EC%9E%90-%EB%A9%94%ED%83%80-%ED%8C%8C%EC%9D%BC-%EB%98%90%EB%8A%94-restart-sn-%ED%8C%8C%EC%9D%BC%EC%9D%B4-%EC%9C%A0%ED%9A%A8%ED%95%98%EC%A7%80-%EC%95%8A%EC%9D%84-%EA%B2%BD%EC%9A%B0-%EB%B0%98%ED%99%98%ED%95%98%EB%8A%94-%EC%97%90%EB%9F%AC-%EB%A9%94%EC%8B%9C%EC%A7%80%EB%A5%BC-%EA%B0%9C%EC%84%A0%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49718 비활성화 상태의 인덱스에 인덱스 통계 정보를 설정할 때 예외 처리를 추가합니다.](#bug-49718%EB%B9%84%ED%99%9C%EC%84%B1%ED%99%94-%EC%83%81%ED%83%9C%EC%9D%98-%EC%9D%B8%EB%8D%B1%EC%8A%A4%EC%97%90-%EC%9D%B8%EB%8D%B1%EC%8A%A4-%ED%86%B5%EA%B3%84-%EC%A0%95%EB%B3%B4%EB%A5%BC-%EC%84%A4%EC%A0%95%ED%95%A0-%EB%95%8C-%EC%98%88%EC%99%B8-%EC%B2%98%EB%A6%AC%EB%A5%BC-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49722 SQL 반영 모드 및 오프라인 이중화에서 이중화 대상 테이블 간 PRIMARY KEY가 다른 경우 예외 처리를 추가합니다.](#bug-49722sql-%EB%B0%98%EC%98%81-%EB%AA%A8%EB%93%9C-%EB%B0%8F-%EC%98%A4%ED%94%84%EB%9D%BC%EC%9D%B8-%EC%9D%B4%EC%A4%91%ED%99%94%EC%97%90%EC%84%9C-%EC%9D%B4%EC%A4%91%ED%99%94-%EB%8C%80%EC%83%81-%ED%85%8C%EC%9D%B4%EB%B8%94-%EA%B0%84-primary-key%EA%B0%80-%EB%8B%A4%EB%A5%B8-%EA%B2%BD%EC%9A%B0-%EC%98%88%EC%99%B8-%EC%B2%98%EB%A6%AC%EB%A5%BC-%EC%B6%94%EA%B0%80%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49725 테이블 잠금 획득 실패로 이중화 SYNC 동작이 실패한 경우 이중화 송신자 측 altibase\_rp.log에 ERR-61152(errno=16) Replication synchronization failed. Check whether the index on the remote server is consistent. 에러가 발생합니다.](#bug-49725%ED%85%8C%EC%9D%B4%EB%B8%94-%EC%9E%A0%EA%B8%88-%ED%9A%8D%EB%93%9D-%EC%8B%A4%ED%8C%A8%EB%A1%9C-%EC%9D%B4%EC%A4%91%ED%99%94-sync-%EB%8F%99%EC%9E%91%EC%9D%B4-%EC%8B%A4%ED%8C%A8%ED%95%9C-%EA%B2%BD%EC%9A%B0-%EC%9D%B4%EC%A4%91%ED%99%94-%EC%86%A1%EC%8B%A0%EC%9E%90-%EC%B8%A1-altibase_rplog%EC%97%90-err-61152errno16-replication-synchronization-failed-check-whether-the-index-on-the-remote-server-is-consistent-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49728 디스크 인덱스 키 삽입 과정에서 인덱스 노드 공간 활용을 위해 인덱스 구조를 변경하고 인덱스 키 삽입 위치 계산 과정에서 Altibase 서버가 비정상 종료합니다.](#bug-49728%EB%94%94%EC%8A%A4%ED%81%AC-%EC%9D%B8%EB%8D%B1%EC%8A%A4-%ED%82%A4-%EC%82%BD%EC%9E%85-%EA%B3%BC%EC%A0%95%EC%97%90%EC%84%9C-%EC%9D%B8%EB%8D%B1%EC%8A%A4-%EB%85%B8%EB%93%9C-%EA%B3%B5%EA%B0%84-%ED%99%9C%EC%9A%A9%EC%9D%84-%EC%9C%84%ED%95%B4-%EC%9D%B8%EB%8D%B1%EC%8A%A4-%EA%B5%AC%EC%A1%B0%EB%A5%BC-%EB%B3%80%EA%B2%BD%ED%95%98%EA%B3%A0-%EC%9D%B8%EB%8D%B1%EC%8A%A4-%ED%82%A4-%EC%82%BD%EC%9E%85-%EC%9C%84%EC%B9%98-%EA%B3%84%EC%82%B0-%EA%B3%BC%EC%A0%95%EC%97%90%EC%84%9C-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%A9%EB%8B%88%EB%8B%A4)
  - [BUG-49739 MERGE JOIN을 사용한 CREATE AS SELECT 문을 수행한 세션이 SESSION CLOSE로 강제 종료되지 않습니다.](#bug-49739merge-join%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%9C-create-as-select-%EB%AC%B8%EC%9D%84-%EC%88%98%ED%96%89%ED%95%9C-%EC%84%B8%EC%85%98%EC%9D%B4-session-close%EB%A1%9C-%EA%B0%95%EC%A0%9C-%EC%A2%85%EB%A3%8C%EB%90%98%EC%A7%80-%EC%95%8A%EC%8A%B5%EB%8B%88%EB%8B%A4)
- [Changes](#changes)
  - [Version Info](#version-info)
  - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
  - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
  - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<br/>

New Features
============

### BUG-49645 이중화 송신자에게 고정 IP 주소를 할당하는 기능을 추가합니다.

-   **module** : rp

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : 이중화 송신자에게 고정 IP 주소를 할당하는 기능을 추가합니다. 이 기능은 특수한 목적으로 제공하고 있으므로 자세한 내용을 원할 경우 Altibase 기술 지원 센터로 연락해주세요.
    
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

### BUG-49747 Altibase 7 이상에서 Altibase 6.3.1 옵티마이저와 동일한 비용 계산식을 설정하는 기능을 추가합니다.

-   **module** : qp

-   **Category** : Other

-   **재현 빈도** : Always

-   **설명** : Altibase 7 이상에서 Altibase 6.3.1 옵티마이저와 동일한 비용 계산식을 설정하는 기능을 추가합니다.

    이 버그는 Altibase 6.3.1 에서 Altibase 7 이상으로 메이저 버전 업그레이드하는 사용자가 업그레이드 이후 SQL 실행 성능이 Altibase 6.3.1 보다 느려진 경우 참고해 볼 수 있습니다. Altibase 7 버전 사용자는 이 버그의 내용을 알 필요는 없습니다. 

    이 버그는 Altibase 7 이상에서 Altibase 6.3.1 옵티마이저의 비용 계산식을 사용하여, 가능한 Altibase 6.3.1과 동일한 실행 계획이 나오도록 노력하였으나, Altibase 6.3.1과 동일한 실행 계획이 나오는 것을 보장하지는 않습니다. 하지만 옵티마이저 일부분인 비용 계산식을 동일하게 맞추기 때문에 계산식을 제외한 부분에서 Altibase 6.3.1과 Altibase 7의 차이를 분석할 수 있습니다.

    이 기능은 특수한 목적으로 제공하고 있으므로 자세한 내용을 원할 경우 Altibase 기술 지원 센터로 연락해주세요. 

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

<br/>

Fixed Bugs
==========

### BUG-49451 저장 프로시저 바디에서 사용한 SQL 문의 LOOP 절에 호스트 변수 또는 지역 변수 사용 시 ERR-31248 : Mismatched bind column count 에러가 발생합니다.

-   **module** : qp-psm-trigger-execute

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 저장 프로시저 바디에서 사용한 SQL 문의 LOOP 절에 호스트 변수 또는 지역 변수 사용 시 ERR-31248 : Mismatched bind column count 에러가 발생하는 문제를 수정합니다.
    
-   **재현 방법**

    -   **재현 절차**

        ```sql
        VAR VAR1 INTEGER;
        VAR VAR2 INTEGER;
        EXEC :VAR2 := 1;
        
        BEGIN
          SELECT 1 INTO :VAR1 FROM DUAL LOOP :VAR2;
        END;
        /
        ```

    -   **수행 결과**

        ```sql
        iSQL> VAR VAR1 INTEGER;
        iSQL> VAR VAR2 INTEGER;
        iSQL> EXEC :VAR2 := 1;
        Execute success.
        iSQL>
        iSQL> BEGIN
            2   SELECT 1 INTO :VAR1 FROM DUAL LOOP :VAR2;
            3 END;
            4 /
        [ERR-31248 : Mismatched bind column count
        at "SYS.ANONYMOUS_BLOCK", line 2]
        iSQL>
        iSQL> PRINT VAR;
        [ HOST VARIABLE ]
        -------------------------------------------------------
        NAME                 TYPE                 VALUE
        -------------------------------------------------------
        VAR1                 INTEGER
        VAR2                 INTEGER              1            1
        ```

    -   **예상 결과**

        ```sql
        iSQL> VAR VAR1 INTEGER;
        iSQL> VAR VAR2 INTEGER;
        iSQL> EXEC :VAR2 := 1;
        Execute success.
        iSQL>
        iSQL> BEGIN
            2   SELECT 1 INTO :VAR1 FROM DUAL LOOP :VAR2;
            3 END;
            4 /
        Execute success.
        iSQL>
        iSQL> PRINT VAR;
        [ HOST VARIABLE ]
        -------------------------------------------------------
        NAME                 TYPE                 VALUE
        -------------------------------------------------------
        VAR1                 INTEGER              1
        VAR2                 INTEGER              1
        ```

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49556 매개변수 값을 설정하지 않고 ParameterMetaData 메소드로 매개변수 정보를 조회하면 NullPointerException 에러가 발생합니다.

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : 매개변수 값을 설정하지 않아도 PreparedStatement.getParameterMetaData()가 동작하도록 수정합니다.
    
    Spring JDBC 버전에 따라 이 에러가 발생하는 경우 spring.jdbc.getParameterType.ignore 값을 true로 설정해야 합니다. 아래 버전에 해당하는 Altibase JDBC Driver를 사용하면spring.jdbc.getParameterType.ignore=true를 설정하지 않아도 됩니다.
    
    - Altibase 6.5.1.9.2 이상
    
    - Altibase 7.1.0.7.6 이상

-   **재현 방법**

    -   **재현 절차**

        ```java
        CREATE TABLE t1 (c1 INT, c2 VARCHAR(10));
        
        Connection sConn = getConnection("20300");
        PreparedStatement sStmt = sConn.prepareStatement("INSERT INTO t1 VALUES (?, ?)");
        ParameterMetaData sMeta = sStmt.getParameterMetaData();
        System.out.println("parameter type===>" + sMeta.getParameterType(2));
        ```

    -   **수행 결과**

        ```java
        Exception in thread "main" java.lang.NullPointerException
        	at Altibase.jdbc.driver.AltibaseParameterMetaData.getParameterType(AltibaseParameterMetaData.java:66)
        	at ParameterBindingTest.doTest(ParameterBindingTest.java:16)
        	at ParameterBindingTest.main(ParameterBindingTest.java:8)
        ```

    -   **예상 결과**

            정상적으로 파라메터 메타 데이터 조회. Spring JDBC 경우, spring.jdbc.getParameterType.ignore값을 true로 설정하지 않아도 됨.

-   **Workaround**

        Spring JDBC 경우, spring.jdbc.getParameterType.ignore 값을 true로 설정

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49573 multiple update 구문에서 대상 테이블에 함수 기반 인덱스가 사용되고 SET 절에 서브쿼리가 사용된 경우 발생하는 메모리 오류를 개선합니다.

-   **module** : qp-dml-pvo

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : multiple update 구문에서 대상 테이블에 함수 기반 인덱스가 사용되고 SET 절에 서브쿼리가 사용된 경우 메모리 오류로 Altibase 서버가 비정상 종료하는 현상을 개선합니다.
    
-   **재현 방법**

    -   **재현 절차**

        ```sql
        CREATE TABLE T3( I1 VARCHAR, I2 VARCHAR, I3 VARCHAR, I4 VARCHAR ) ;
        CREATE TABLE T1 (I1 INTEGER, I2 INTEGER);
        CREATE TABLE T2 (I1 INTEGER, I2 INTEGER);
        
        CREATE INDEX T3_IDX28 ON T3( I3+2 DESC, I4||'C' DESC ) ;
        CREATE INDEX T3_IDX23 ON T3( I3+2, I4||'C' ) ;
        
        UPDATE T1 LEFT OUTER JOIN T3 ON T1.I1 = T3.I1 SET ( T1.I2, T3.I3 ) = ( SELECT 
        T2.I1, T2.I1 FROM T2 );
        
        INSERT INTO T1 VALUES (1, 2);
        ```

    -   **수행 결과**

            frequently fatal

    -   **예상 결과**

            no rows updated.
            1 rows inserted.

-   **Workaround**

    ```sql
    UPDATE T1 LEFT OUTER JOIN T3 ON T1.I1 = T3.I1
    SET T1.i2 = ( SELECT T2.I1 FROM T2 )
      , T3.i2 = ( SELECT T2.I1 FROM T2 );
    ```

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49690 ALTER REPLICATION replication\_name BUILD OFFLINE META 구문 수행 시 송신자 메타 파일 또는 Restart SN 파일이 유효하지 않을 경우 반환하는 에러 메시지를 개선합니다.

-   **module** : rp-oraAdapter

-   **Category** : Usability

-   **재현 빈도** : Always

-   **설명** : ALTER REPLICATION *replication\_name* BUILD OFFLINE META 구문 수행 시 송신자 메타 파일 또는 Restart SN 파일이 유효하지 않을 경우 반환하는 에러 메시지를 개선합니다.
    
    송신자 메타 파일(*replication\_name*\_META\_NEW.bin, *replication\_name*\_META\_OLD.bin)이 모두 유효하지 않으면 ERR-611B3 : Invalid sender meta files. (Replication name: *replication\_name*,
    File name: *replication\_name*\_META\_NEW.bin, *replication\_name*\_META\_OLD.bin ) 에러를, Restart SN 파일이 모두 유효하지 않을 경우 ERR-611B4 : Invalid Restart SN files. (Replication name: *replication\_name*, File name: *replication\_name*\_SN\_NEW.bin, *replication\_name*\_SN\_OLD.bin ) 에러를 반환하도록 수정하였습니다.
    
-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**
        -   송신자 메타 파일이 모두 유효하지 않을 때
            -   ERR-611B3 : There is no valid meta file.

        -   Restart SN 파일이 모두 유효하지 않을 때
            -   ERR-611B4 : There is no valid sn file.

    -   **예상 결과**
        -   송신자 메타 파일이 모두 유효하지 않을 때 
            -   ERR-611B3 : Invalid sender meta files. (Replication name: *replication_name*, File name: *replication_name*_META_NEW.bin, *replication_name*_META_OLD.bin )
        -   Restart SN 파일이 모두 유효하지 않을 때 
            -   ERR-611B4 : Invalid Restart SN files. (Replication name: *replication_name*, File name: *replication_name*_SN_NEW.bin, *replication_name*_SN_OLD.bin )

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code
        -   에러 메시지가 추가되었습니다.
            -   0x611B3 ( 397747) rpERR_ABORT_ERR_NO_VALID_METAFILE Invalid sender meta files. (Replication name: <0%s>, File name: <1%s>_META_NEW.bin, <2%s>_META_OLD.bin ) 
                \# *Cause:
                \# - Sender meta files do not exist or are invalid.
                \# *Action:
                \# - 'BUILD OFFLINE META' failed. Verify the altibase_rp.log.
            -   0x611B4 ( 397748) rpERR_ABORT_ERR_NO_VALID_SNFILE Invalid Restart SN files. (Replication name: <0%s>, File name: <1%s>_SN_NEW.bin, <2%s>_SN_OLD.bin ) 
                \# *Cause:
                \# - Restart SN files do not exist or are invalid.
                \# *Action:
                \# - 'BUILD OFFLINE META' failed. Verify the altibase_rp.log.

### BUG-49718 비활성화 상태의 인덱스에 인덱스 통계 정보를 설정할 때 예외 처리를 추가합니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : 비활성화 상태의 인덱스에 인덱스 통계 정보를 설정(SET\_INDEX\_STATS)하면 Altibase 서버가 비정상 종료하는 현상을 수정합니다. 비활성화 상태의 인덱스 경우 인덱스 통계 정보 설정을 수행해도 무시하도록 예외 처리를 추가합니다.
    
-   **재현 방법**

    -   **재현 절차**

        ```sql
        DROP TABLE T1;
        CREATE TABLE T1 (I1 INTEGER);
        ALTER TABLE T1 ALL INDEX DISABLE;
        CREATE INDEX T1_IDX ON T1(I1);
        EXEC SET_INDEX_STATS('SYS', 'T1_IDX', NULL, NULL, 30, NULL, NULL, NULL, TRUE);
        ```

    -   **수행 결과**

        ```sql
        [ERR-91015 : Communication failure.]
        ```

    -   **예상 결과**

            Execute success.

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49722 SQL 반영 모드 및 오프라인 이중화에서 이중화 대상 테이블 간 PRIMARY KEY가 다른 경우 예외 처리를 추가합니다.

-   **module** : rp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : SQL 반영 모드 및 오프라인 이중화에서 이중화 대상 테이블 간 PRIMARY KEY가 다름에도 성공하는 다음 2가지 상황에 예외 처리를 추가합니다.
    
    - SQL 반영 모드(REPLICATION\_SQL\_APPLY\_ENABLE = 1)에서 이중화를 시작한 경우

    - Adapter에서 BUILD OFFLINE META를 수행한 경우 
    
    이 버그 반영 후에는 [ERR-6100D : [Sender] Failed to handshake with the peer server (The index column ID of the replicated table does not match. [*local\_table\_name*(Name:*local\_index\_name*, ID:*local\_index\_id*):*remote\_table\_name*(Name:*remote\_index\_name*, ID:*remote\_index\_id*)].)] 에러가 발생합니다.
    
    이 버그는 지역 서버 및 원격 서버 모두를 패치해야 적용됩니다.
    
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

### BUG-49725 테이블 잠금 획득 실패로 이중화 SYNC 동작이 실패한 경우 이중화 송신자 측 altibase\_rp.log에 ERR-61152(errno=16) Replication synchronization failed. Check whether the index on the remote server is consistent. 에러가 발생합니다.

-   **module** : rp

-   **Category** : Message Error

-   **재현 빈도** : Always

-   **설명** : 테이블 잠금 획득 실패로 이중화 SYNC 동작이 실패한 경우 이중화 송신자 측 altibase\_rp.log에 ERR-61152(errno=16) Replication synchronization failed. Check whether the index on the remote server
    is consistent. 에러가 발생하는 현상을 수정합니다.
    
    ```bash
    [2022/05/12 01:11:18 B07A5858][PID:56396][Thread-70155392943552][LWP-56623]
    [SenderSyncParallel] Failed to lock table for replication synchronization. (User:user_name, Table:table_name, Partition:partition_name)
    [2022/05/12 01:11:18 B07A5859][PID:56396][Thread-70155392943552][LWP-56623]
    ERR-11075(errno=16) The transaction has exceeded the lock timeout specified by the user.
    
    [2022/05/12 01:11:18 B07A585A][PID:56396][Thread-70155392943552][LWP-56623]
    [SenderSyncParallel] Error in allocSCN()
    [2022/05/12 01:11:18 B07A585B][PID:56396][Thread-70155392943552][LWP-56623]
    [SenderSyncParallel] Error in syncParallel()
    [2022/05/12 01:11:18 B07A585C][PID:56396][Thread-70155392943552][LWP-56623]
    ERR-61011(errno=16) [Sender] Failed to start sync
    
    [2022/05/12 01:11:18 B07A585D][PID:56396][Thread-70155392943552][LWP-56623]
    ERR-61152(errno=16) Replication synchronization failed. Check whether the index on the remote server is consistent.
    
    [2022/05/12 01:11:18 B07A585E][PID:56396][Thread-70155392943552][LWP-56623]
    ERR-61011(errno=16) [Sender] Failed to start sync
    ```

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

### BUG-49728 디스크 인덱스 키 삽입 과정에서 인덱스 노드 공간 활용을 위해 인덱스 구조를 변경하고 인덱스 키 삽입 위치 계산 과정에서 Altibase 서버가 비정상 종료합니다.

-   **module** : sm-disk-index

-   **Category** : Fatal

-   **재현 빈도** : Rare

-   **설명** : 디스크 인덱스 키 삽입 과정에서 인덱스 노드 공간 활용을 위해 인덱스 구조를 변경하고 인덱스 키 삽입 위치 계산 과정에서 Altibase 서버가 비정상 종료하는 현상을 수정합니다.
    
    이 버그로 Altibase 서버 비정상 종료 현상 발생 시 altibase\_error.log 에 아래와 같은 로그가 발생합니다.

    ```bash
    -sdnRuntimeHeader (disk common)
    mTableTSID                : 45
    mIndexTSID                : 47
    mMetaRID                  : 667252498528
    mTableOID                 : 99865440
    mIndexID                  : 49577
    ...중략...
    
    BEGIN-STACK [NORMAL] ============================
    Caller[1] 000000010001D7A4      => .iduStack::dumpStack(const iduSignalDef*,siginfo_t*,ucontext_t*,idBool,char*,idBool)
    Caller[2] 0000000100026FEC      => .ideLog::writeErrorTraceInternal(unsigned int,ideLogModule,unsigned int,const char*,const char*,unsigned int,const char*,char*)
    Caller[3] 0000000100026D34      => .ideLog::writeErrorTrace(const char*,idBool,const char*,unsigned int,const char*,char*)
    Caller[4] 000000010001FDAC      => .ideLogError        
    Caller[5] 00000001007AAF50      => .sdnbBTree::findTargetKeyForDupKey(sdrMtx*,sdnbHeader*,sdnbStatistic*,sdnbKeyInfo*,sdpPhyPageHdr**,short*)
    ...중략...
    
    index TSID : 47, get page ID : 0
    IDE_ASSERT( 0 ), [sdnbModule.cpp:17227], errno=[16]
    errno=[16]
    ```

    이 버그는 인덱스를 재구성하거나 ALTER INDEX *index\_name* AGING 수행하면 발생 확률을 낮출 수 있습니다. 문제의 인덱스는 altibase\_error.log에서 mIndexID 으로 확인할 수 있습니다.
    
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

### BUG-49739 MERGE JOIN을 사용한 CREATE AS SELECT 문을 수행한 세션이 SESSION CLOSE로 강제 종료되지 않습니다.

-   **module** : qp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : MERGE JOIN을 사용한 CREATE AS SELECT 문을 수행한 세션이 SESSION CLOSE로 강제 종료되지 않는 현상을 수정합니다.
    
-   **재현 방법**

    -   **재현 절차**

        -   A 세션 

            ```sql
            CREATE TABLE T1 AS
            SELECT LEVEL AS C1, CAST('AAAAA' AS VARCHAR(10)) AS T1_CD
              FROM DUAL CONNECT BY LEVEL <= 7335;
              
             CREATE TABLE T2 AS 
            SELECT LEVEL AS C1, CAST('AAAAA' AS VARCHAR(10)) AS T2_CD
              FROM DUAL CONNECT BY LEVEL <= 10000;
              
             CREATE TABLE T3 AS 
            SELECT /*+ USE_MERGE (B A) */ A.*, B.T2_CD
              FROM T1 A INNER JOIN T2 B ON A.T1_CD = B.T2_CD
               AND B.T2_CD = 'AAAAA';
            ```

        - B 세션

          ```sql
          ALTER DATABASE database_name SESSION CLOSE session_id;
          ```

    -   **수행 결과**

            테이블 생성 완료 후 세션 종료. 

    -   **예상 결과**

            [ERR-01043 : The session has been closed by the server]

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

<br/>

Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| :--------------: | :---------------------: | :----------: | :-----------------: | :--------------------------: |
|    7.1.0.7.6     |          6.5.1          |    8.10.1    |        7.1.7        |            7.4.7             |

> Altibase 7.1 패치 버전별 히스토리는 [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.1/Altibase_7_1_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

> 패치를 롤백하려는 경우, [메타다운그레이드]([https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Installation%20Guide.md#%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9Cmeta-downgrade](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Installation Guide.md#메타-다운그레이드meta-downgrade))를 참고한다.

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
