# Altibase 6.5.1.9.7 Patch Notes

<br>

<br>

# Table of Contents

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Fixed Bugs](#fixed-bugs)
    - [BUG-48201 assert()가 AIX 7.2에서 동작하지 않습니다.](#bug-48201-assert%EA%B0%80-aix-72%EC%97%90%EC%84%9C-%EB%8F%99%EC%9E%91%ED%95%98%EC%A7%80-%EC%95%8A%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-49584 메모리 테이블 생성 시 LOB 칼럼의 테이블 스페이스를 다른 테이블 스페이스로 지정해도 오류가 발생하지 않고 정상적으로 생성되는 문제가 있습니다.](#bug-49584-%EB%A9%94%EB%AA%A8%EB%A6%AC-%ED%85%8C%EC%9D%B4%EB%B8%94-%EC%83%9D%EC%84%B1-%EC%8B%9C-lob-%EC%B9%BC%EB%9F%BC%EC%9D%98-%ED%85%8C%EC%9D%B4%EB%B8%94-%EC%8A%A4%ED%8E%98%EC%9D%B4%EC%8A%A4%EB%A5%BC-%EB%8B%A4%EB%A5%B8-%ED%85%8C%EC%9D%B4%EB%B8%94-%EC%8A%A4%ED%8E%98%EC%9D%B4%EC%8A%A4%EB%A1%9C-%EC%A7%80%EC%A0%95%ED%95%B4%EB%8F%84-%EC%98%A4%EB%A5%98%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%98%EC%A7%80-%EC%95%8A%EA%B3%A0-%EC%A0%95%EC%83%81%EC%A0%81%EC%9C%BC%EB%A1%9C-%EC%83%9D%EC%84%B1%EB%90%98%EB%8A%94-%EB%AC%B8%EC%A0%9C%EA%B0%80-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-49985 GROUP BY GROUPING SETS 절에 빈 그룹(Empty Group)을 사용할 때 메모리 효율성을 개선합니다.](#bug-49985-group-by-grouping-sets-%EC%A0%88%EC%97%90-%EB%B9%88-%EA%B7%B8%EB%A3%B9empty-group%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%A0-%EB%95%8C-%EB%A9%94%EB%AA%A8%EB%A6%AC-%ED%9A%A8%EC%9C%A8%EC%84%B1%EC%9D%84-%EA%B0%9C%EC%84%A0%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50025 CREATE DATABASE 수행 후 바로 STARTUP SERVICE를 수행하면 Altibase 서버가 비정상 종료하거나 ERR-11110 : The index is inconsistent 에러가 발생합니다.](#bug-50025-create-database-%EC%88%98%ED%96%89-%ED%9B%84-%EB%B0%94%EB%A1%9C-startup-service%EB%A5%BC-%EC%88%98%ED%96%89%ED%95%98%EB%A9%B4-altibase-%EC%84%9C%EB%B2%84%EA%B0%80-%EB%B9%84%EC%A0%95%EC%83%81-%EC%A2%85%EB%A3%8C%ED%95%98%EA%B1%B0%EB%82%98-err-11110--the-index-is-inconsistent-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50057 ROLLUP 함수와 집계 함수 그리고 ORDER BY 절을 함께 사용하면 결과 오류가 발생합니다.](#bug-50057-rollup-%ED%95%A8%EC%88%98%EC%99%80-%EC%A7%91%EA%B3%84-%ED%95%A8%EC%88%98-%EA%B7%B8%EB%A6%AC%EA%B3%A0-order-by-%EC%A0%88%EC%9D%84-%ED%95%A8%EA%BB%98-%EC%82%AC%EC%9A%A9%ED%95%98%EB%A9%B4-%EA%B2%B0%EA%B3%BC-%EC%98%A4%EB%A5%98%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50058 DROP REPLICATION 수행 시 이중화 수신자 쓰레드가 종료되지 않을 수 있는 메모리 참조 오류를 수정합니다.](#bug-50058-drop-replication-%EC%88%98%ED%96%89-%EC%8B%9C-%EC%9D%B4%EC%A4%91%ED%99%94-%EC%88%98%EC%8B%A0%EC%9E%90-%EC%93%B0%EB%A0%88%EB%93%9C%EA%B0%80-%EC%A2%85%EB%A3%8C%EB%90%98%EC%A7%80-%EC%95%8A%EC%9D%84-%EC%88%98-%EC%9E%88%EB%8A%94-%EB%A9%94%EB%AA%A8%EB%A6%AC-%EC%B0%B8%EC%A1%B0-%EC%98%A4%EB%A5%98%EB%A5%BC-%EC%88%98%EC%A0%95%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50066 DDL 구문 수행 중 실패하면, 동시성 제어에서 해제된 메모리 사용(Free'd Memory Read) 오류가 발생할 수 있습니다.](#bug-50066-ddl-%EA%B5%AC%EB%AC%B8-%EC%88%98%ED%96%89-%EC%A4%91-%EC%8B%A4%ED%8C%A8%ED%95%98%EB%A9%B4-%EB%8F%99%EC%8B%9C%EC%84%B1-%EC%A0%9C%EC%96%B4%EC%97%90%EC%84%9C-%ED%95%B4%EC%A0%9C%EB%90%9C-%EB%A9%94%EB%AA%A8%EB%A6%AC-%EC%82%AC%EC%9A%A9freed-memory-read-%EC%98%A4%EB%A5%98%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A0-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-50072 메모리사용 통계정보 누락 가능성이 있습니다.](#bug-50072-%EB%A9%94%EB%AA%A8%EB%A6%AC%EC%82%AC%EC%9A%A9-%ED%86%B5%EA%B3%84%EC%A0%95%EB%B3%B4-%EB%88%84%EB%9D%BD-%EA%B0%80%EB%8A%A5%EC%84%B1%EC%9D%B4-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-50090 Statement 객체의 다음 결과가 ResultSet 객체가 아닐 때 getMoreResults()에서 true를 반환합니다.](#bug-50090-statement-%EA%B0%9D%EC%B2%B4%EC%9D%98-%EB%8B%A4%EC%9D%8C-%EA%B2%B0%EA%B3%BC%EA%B0%80-resultset-%EA%B0%9D%EC%B2%B4%EA%B0%80-%EC%95%84%EB%8B%90-%EB%95%8C-getmoreresults%EC%97%90%EC%84%9C-true%EB%A5%BC-%EB%B0%98%ED%99%98%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50096 DDL 복제 실패 이후 HeartBeat 쓰레드의 비정상적인 동작으로 이중화 송신자가 시작되지 않을 수 있습니다.](#bug-50096-ddl-%EB%B3%B5%EC%A0%9C-%EC%8B%A4%ED%8C%A8-%EC%9D%B4%ED%9B%84-heartbeat-%EC%93%B0%EB%A0%88%EB%93%9C%EC%9D%98-%EB%B9%84%EC%A0%95%EC%83%81%EC%A0%81%EC%9D%B8-%EB%8F%99%EC%9E%91%EC%9C%BC%EB%A1%9C-%EC%9D%B4%EC%A4%91%ED%99%94-%EC%86%A1%EC%8B%A0%EC%9E%90%EA%B0%80-%EC%8B%9C%EC%9E%91%EB%90%98%EC%A7%80-%EC%95%8A%EC%9D%84-%EC%88%98-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-50106 iSQL에서 desc 명령을 수행하면 ERR-31002 : A single-row subquery has returned more than one row. 에러가 발생합니다.](#bug-50106-isql%EC%97%90%EC%84%9C-desc-%EB%AA%85%EB%A0%B9%EC%9D%84-%EC%88%98%ED%96%89%ED%95%98%EB%A9%B4-err-31002--a-single-row-subquery-has-returned-more-than-one-row-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50164 휘발성 테이블에서 공간 부족의 이유로 메모리 할당이 실패할 하는경우, 페이지 락이 해제되지 않는 문제가 있습니다.](#bug-50164-%ED%9C%98%EB%B0%9C%EC%84%B1-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90%EC%84%9C-%EA%B3%B5%EA%B0%84-%EB%B6%80%EC%A1%B1%EC%9D%98-%EC%9D%B4%EC%9C%A0%EB%A1%9C-%EB%A9%94%EB%AA%A8%EB%A6%AC-%ED%95%A0%EB%8B%B9%EC%9D%B4-%EC%8B%A4%ED%8C%A8%ED%95%A0-%ED%95%98%EB%8A%94%EA%B2%BD%EC%9A%B0-%ED%8E%98%EC%9D%B4%EC%A7%80-%EB%9D%BD%EC%9D%B4-%ED%95%B4%EC%A0%9C%EB%90%98%EC%A7%80-%EC%95%8A%EB%8A%94-%EB%AC%B8%EC%A0%9C%EA%B0%80-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-50174 altibase.properties.release 파일에서 사용되지 않는 프로퍼티인 REPLICATION\_SERVICE\_WAIT\_MAX\_LIMIT를 제거합니다.](#bug-50174-altibasepropertiesrelease-%ED%8C%8C%EC%9D%BC%EC%97%90%EC%84%9C-%EC%82%AC%EC%9A%A9%EB%90%98%EC%A7%80-%EC%95%8A%EB%8A%94-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0%EC%9D%B8-replication%5C_service%5C_wait%5C_max%5C_limit%EB%A5%BC-%EC%A0%9C%EA%B1%B0%ED%95%A9%EB%8B%88%EB%8B%A4)
    - [BUG-50177 LOB이 포함된 디스크 테이블에 이중화가 걸려 있을때 undo tablespace full이 발생하면 이중화가 실패하는 문제가 있습니다.](#bug-50177-lob%EC%9D%B4-%ED%8F%AC%ED%95%A8%EB%90%9C-%EB%94%94%EC%8A%A4%ED%81%AC-%ED%85%8C%EC%9D%B4%EB%B8%94%EC%97%90-%EC%9D%B4%EC%A4%91%ED%99%94%EA%B0%80-%EA%B1%B8%EB%A0%A4-%EC%9E%88%EC%9D%84%EB%95%8C-undo-tablespace-full%EC%9D%B4-%EB%B0%9C%EC%83%9D%ED%95%98%EB%A9%B4-%EC%9D%B4%EC%A4%91%ED%99%94%EA%B0%80-%EC%8B%A4%ED%8C%A8%ED%95%98%EB%8A%94-%EB%AC%B8%EC%A0%9C%EA%B0%80-%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4)
    - [BUG-50205 RHEL 8에서 Altibase 서버 구동 시 error while loading shared libraries 에러가 발생합니다.](#bug-50205-rhel-8%EC%97%90%EC%84%9C-altibase-%EC%84%9C%EB%B2%84-%EA%B5%AC%EB%8F%99-%EC%8B%9C-error-while-loading-shared-libraries-%EC%97%90%EB%9F%AC%EA%B0%80-%EB%B0%9C%EC%83%9D%ED%95%A9%EB%8B%88%EB%8B%A4)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Fixed Bugs
==========

### BUG-48201  assert()가 AIX 7.2에서 동작하지 않습니다.

-   **module** : id

-   **Category** : Hang

-   **재현 빈도** : Always

-   **설명** : AIX 7.2에서 시그널핸들러가 올바른 인자를 받지 못하여
    비정상종료가 되어야 하는 상황에서 행(HANG)이 발생하는 문제를 해결합니다.

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

### BUG-49584  메모리 테이블 생성 시 LOB 칼럼의 테이블 스페이스를 다른 테이블 스페이스로 지정해도 오류가 발생하지 않고 정상적으로 생성되는 문제가 있습니다.

-   **module** : qp-ddl-dcl-execute

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : 메모리 테이블 생성 시 LOB 칼럼의 테이블 스페이스를 다른
    테이블 스페이스로 지정해도 오류가 발생하지 않고 정상적으로 생성되는 문제가 있습니다. 그로 인해 비정상 종료하는 문제가 있어 수정합니다.

- **재현 방법**

  - **재현 절차**

  - **수행 결과**

  - **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-49985  GROUP BY GROUPING SETS 절에 빈 그룹(Empty Group)을 사용할 때 메모리 효율성을 개선합니다.

-   **module** : qp-select

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : GROUP BY GROUPING SETS 절에 빈 그룹(Empty Group)을 사용할
    때 메모리 할당 시간을 감소하고 메모리 사용 효율을 개선합니다.

- **재현 방법**

  -   **재현 절차**

          ALTER SESSION SET EXPLAIN PLAN = ON;
          CREATE TABLE T1 ( I1 INTEGER, I2 INTEGER );
          SELECT I1,SUM(I2)
            FROM T1
           GROUP BY GROUPING SETS ( I1, () );

  - **수행 결과**

        I1          SUM(I2)
        ------------------------------------
        No rows selected.
        ------------------------------------------------------------
        PROJECT ( COLUMN_COUNT: 2, TUPLE_SIZE: 16, COST: 388.69 )
         VIEW ( ACCESS: 0, COST: 386.03 )
          BAG-UNION
           PROJECT ( COLUMN_COUNT: 2, TUPLE_SIZE: 16, COST: 130.13 )
            GROUP-AGGREGATION ( ITEM_SIZE: 40, GROUP_COUNT: 0, BUCKET_COUNT: 1024, ACCESS: 0, COST: 130.06 )
             SCAN ( TABLE: SYS.T1, FULL SCAN, ACCESS: 0, COST: 116.76 )
           PROJECT ( COLUMN_COUNT: 2, TUPLE_SIZE: 16, COST: 135.34 )
            GROUP-AGGREGATION ( ITEM_SIZE: 32, GROUP_COUNT: 0, BUCKET_COUNT: 5120, ACCESS: 0, COST: 130.06 )
             SCAN ( TABLE: SYS.T1, FULL SCAN, ACCESS: 0, COST: 116.76 )
        ------------------------------------------------------------

  -   **예상 결과**

          I1          SUM(I2)
          ------------------------------------
          No rows selected.
          ------------------------------------------------------------
          PROJECT ( COLUMN_COUNT: 2, TUPLE_SIZE: 16, COST: 260.21 )
           VIEW ( ACCESS: 1, COST: 260.19 )
            BAG-UNION
             PROJECT ( COLUMN_COUNT: 2, TUPLE_SIZE: 16, COST: 130.13 )
              GROUP-AGGREGATION ( ITEM_SIZE: 40, GROUP_COUNT: 0, BUCKET_COUNT: 1024, ACCESS: 0, COST: 130.06 )
               SCAN ( TABLE: SYS.T1, FULL SCAN, ACCESS: 0, COST: 116.76 )
             PROJECT ( COLUMN_COUNT: 2, TUPLE_SIZE: 16, COST: 130.06 )
              GROUP-AGGREGATION ( ITEM_SIZE: 32, GROUP_COUNT: 1, BUCKET_COUNT: 1, ACCESS: 1, COST: 130.06 )
               SCAN ( TABLE: SYS.T1, FULL SCAN, ACCESS: 0, COST: 116.76 )
          ------------------------------------------------------------

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50025  CREATE DATABASE 수행 후 바로 STARTUP SERVICE를 수행하면 Altibase 서버가 비정상 종료하거나 ERR-11110 : The index is inconsistent 에러가 발생합니다.

-   **module** : sm

-   **Category** : Assert

-   **재현 빈도** : Frequence

-   **설명** : CREATE DATABASE 수행 후 바로 STARTUP SERVICE를 수행하면
    Altibase 서버가 비정상 종료하거나 ERR-11110 : The index is
    inconsistent 에러가 발생하는 버그를 수정합니다.

    이 버그를 회피하려면 아래 순서로 STARTUP SERVICE를 수행해야 합니다.

    1) CREATE DATABASE

    2) SHUTDOWN ABORT

    3) STARTUP SERVICE

- **재현 방법**

  -   **재현 절차**

          $ is -sysdba
          iSQL(sysdba)> STARTUP PROCESS;
          iSQL(sysdba)> CREATE DATABASE MYDB INITSIZE=50M NOARCHIVELOG CHARACTER SET UTF8 NATIONAL CHARACTER SET UTF16;
          iSQL(sysdba)> STARTUP SERVICE;
          iSQL(sysdba)> CREATE USER ALTITEST IDENTIFIED BY ALTITEST;
          iSQL(sysdba)> DROP USER ALTITEST;

  - **수행 결과**

        Altibase 서버 비정상 종료
        또는
        iSQL(sysdba)> DROP USER ALTITEST;
        [ERR-11110 : The index is inconsistent]

  -   **예상 결과**

          iSQL(sysdba)> DROP USER ALTITEST;
          Drop success.

- **Workaround**

      데이터베이스를 생성한 후 SHUTDOWN ABORT 명령 수행하고 STARTUP을 수행합니다.

      $ is -sysdba

      iSQL(sysdba)> STARTUP PROCESS;
      iSQL(sysdba)> CREATE DATABASE MYDB INITSIZE=50M NOARCHIVELOG CHARACTER SET UTF8 NATIONAL CHARACTER SET UTF16;
      iSQL(sysdba)> SHUTDOWN ABORT;
      iSQL(sysdba)> STARTUP SERVICE;
      iSQL(sysdba)> CREATE USER ALTITEST IDENTIFIED BY ALTITEST;
      iSQL(sysdba)> DROP USER ALTITEST;

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50057  ROLLUP 함수와 집계 함수 그리고 ORDER BY 절을 함께 사용하면 결과 오류가 발생합니다.

-   **module** : qp-select

-   **Category** : Functional Error

-   **재현 빈도** : Frequence

-   **설명** : ROLLUP 함수와 집계 함수 그리고 ORDER BY 절을 함께 사용할
    때 발생하는 결과 오류를 수정합니다.

- **재현 방법**

  -   **재현 절차**

          DROP TABLE T1;
          CREATE TABLE T1( I1 VARCHAR(10), I2 VARCHAR(10), I3 VARCHAR(10) );
          INSERT INTO T1 VALUES(1,1,1);
          INSERT INTO T1 VALUES(1,2,2);
          INSERT INTO T1 VALUES(3,2,1);
          INSERT INTO T1 VALUES(10,2,1);
          SELECT /*+ NO_PLAN_CACHE */ TO_CHAR(COUNT(*) )
            FROM T1
           GROUP BY ROLLUP(I1), I2
           ORDER BY 1;

  - **수행 결과**

        TO_CHAR(COUNT(*))  
        ---------------------
        0           
        0           
        0           
        0           
        0           
        0           
        6 rows selected.

  -   **예상 결과**

          TO_CHAR(COUNT(*))  
          ---------------------
          1
          1
          1
          1
          1
          3
          6 rows selected.

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50058  DROP REPLICATION 수행 시 이중화 수신자 쓰레드가 종료되지 않을 수 있는 메모리 참조 오류를 수정합니다.

-   **module** : rp

-   **Category** : Other

-   **재현 빈도** : Unknown

-   **설명** : DROP REPLICATION 수행 시 이중화 수신자 쓰레드가 종료되지
    않을 수 있는 메모리 참조 오류를 수정합니다. 이 버그가 발생할
    가능성은 매우 낮습니다.

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

### BUG-50066  DDL 구문 수행 중 실패하면, 동시성 제어에서 해제된 메모리 사용(Free'd Memory Read) 오류가 발생할 수 있습니다.

-   **module** : qp

-   **Category** : Memory Error

-   **재현 빈도** : Frequence

-   **설명** : DDL 구문 수행 중 실패하면, 동시성 제어에서 해제된 메모리
    사용(Free'd Memory Read) 오류가 발생할 수 있는 문제를 예방합니다.

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

### BUG-50072  메모리사용 통계정보 누락 가능성이 있습니다.

-   **module** : id

-   **Category** : Maintainability

-   **재현 빈도** : Unknown

-   **설명** : v\$memstat에 관련된 메모리관리의 통계정보를 관리하는
    로직에 통계값의 누락이 발생할 가능성이 있는 코드가 있어서 그에
    대해 수정합니다. 통계정보 누락이 발생하면 altibase_boot.log에 로그를 남기도록 개선하였습니다.

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

### BUG-50090  Statement 객체의 다음 결과가 ResultSet 객체가 아닐 때 getMoreResults()에서 true를 반환합니다.

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** :  Statement 객체의 다음 결과가 ResultSet 객체가 아닐 때
    getMoreResults()에서 true를 반환하는 버그를 수정합니다. JDBC API에
    따라 false를 반환하도록 수정합니다.

    이 버그를 반영하려면 Altibase JDBC 드라이버를 패치해야 합니다.

    이 버그가 반영된 Altibase JDBC 드라이버 7.1.0.8.3
    이상에서 getMoreResults() 메소드의 수행 결과가 달라집니다.

    - 기존 : 최대 ResultSet 객체 수 만큼 true를 반환

    - 변경 : ResultSet 객체 수 - 1 만큼 true를 반환

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

### BUG-50096  DDL 복제 실패 이후 HeartBeat 쓰레드의 비정상적인 동작으로 이중화 송신자가 시작되지 않을 수 있습니다.

-   **module** : rp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : DDL 복제 실패 후 이중화를 종료할 때 HeartBeat 쓰레드가
    정상적으로 종료되지 않는 문제로, 이중화 송신자가 시작되지 않는
    현상을 수정합니다.

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

### BUG-50106  iSQL에서 desc 명령을 수행하면 ERR-31002 : A single-row subquery has returned more than one row. 에러가 발생합니다.

-   **module** : ux-isql

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : iSQL에서 desc 명령을 수행하면 ERR-31002 : A single-row
    subquery has returned more than one row. 에러가 발생하는 버그를
    수정합니다. 이 버그는 아래 조건을 만족할 때 발생합니다.

    1) 서로 다른 데이터베이스 사용자가 같은 이름의 테이블 A를 생성

    2) iSQL에서 SET PARTITIONS ON 수행 후

    3) DESC A 수행

- **재현 방법**

  - **재현 절차**

        CONNECT SYS/MANAGER
        CREATE TABLE T1 (C1 INTEGER, C2 INTEGER);

        CREATE USER USER1 IDENTIFIED BY USER1;
        CONNECT USER1/USER1
        CREATE TABLE T1 (C1 INTEGER, C2 INTEGER);
        SET PARTITIONS ON;
        DESC T1;

  - **수행 결과**

        DESC T1;
        [ TABLESPACE : SYS_TBS_MEM_DATA ]
        [ ATTRIBUTE ]
        ------------------------------------------------------------------------------
        NAME                                     TYPE                        IS NULL
        ------------------------------------------------------------------------------
        C1                                       INTEGER         FIXED
        C2                                       INTEGER         FIXED
        T1 has no index
        T1 has no primary key

  -   **예상 결과**

          DESC T1;
          [ TABLESPACE : SYS_TBS_MEM_DATA ]
          [ ATTRIBUTE ]
          ------------------------------------------------------------------------------
          NAME                                     TYPE                        IS NULL
          ------------------------------------------------------------------------------
          C1                                       INTEGER         FIXED
          C2                                       INTEGER         FIXED
          T1 has no index
          T1 has no primary key

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50164  휘발성 테이블에서 공간 부족의 이유로 메모리 할당이 실패할 하는경우, 페이지 락이 해제되지 않는 문제가 있습니다.

-   **module** : sm

-   **Category** : Hang

-   **재현 빈도** : Always

-   **설명** : 휘발성 테이블에서 페이지 할당을 시도할때는 페이지 락을 요구하는데, 공간 부족의 이유로 예외가 발생하는 경우 페이지 락이 해제되지 않는 문제가 있어 개선합니다.

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

### BUG-50174  altibase.properties.release 파일에서 사용되지 않는 프로퍼티인 REPLICATION\_SERVICE\_WAIT\_MAX\_LIMIT를 제거합니다.

-   **module** : rp

-   **Category** : Maintainability

-   **재현 빈도** : Always

-   **설명** : 사용하지 않는 프로퍼티가 altibase.properties.release
    파일에 남아 있어서 제거합니다.

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

### BUG-50177  LOB이 포함된 디스크 테이블에 이중화가 걸려 있을때 undo tablespace full이 발생하면 이중화가 실패하는 문제가 있습니다.

-   **module** : rp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **설명** : LOB 로그 처리 중 undo tablespace full이 발생하더라도
    이중화가 정상적으로 동작하도록 수정 합니다.

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

### BUG-50205  RHEL 8에서 Altibase 서버 구동 시 error while loading shared libraries 에러가 발생합니다.

-   **module** : installer

-   **Category** : Maintainability

-   **재현 빈도** : Unknown

-   **설명** : RHEL 8 에서 ncurses (tinfo 포함) 라이브러리 버전이 6.1 로
    변경되었습니다. Altibase는 ncurses 5 버전이 필요하기 때문에 RHEL
    8에서 Altibase 서버 구동 시 에러가 발생할 수 있습니다. 

    ncurses 라이브러리는 ncurses 5 \~ ncurses 6.2 까지 소스 레벨의
    호환성(API)와 바이너리 호환성 (ABI)를 동시에 보장하므로, Altibase
    서버 패키지 인스톨러에서 libncurses.so.5, libtinfo.so.5 파일이 없는
    경우 \$ALTIBASE\_HOME/lib에 심볼릭 링크를 생성합니다.

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
|    6.5.1.9.7     |          6.3.1          |    8.1.1     |        7.1.3        |            7.4.5             |

> Altibase 6.5.1 패치 버전별 히스토리는 [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_6.5.1/Altibase_6_5_1_Version_Histories.md) 에서 확인할 수 있다.

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
