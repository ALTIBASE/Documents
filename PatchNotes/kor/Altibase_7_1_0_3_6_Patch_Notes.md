Altibase 7.1.0.3.6 Patch Notes
==============================

New Features
------------

### BUG-47677  -extra\_col\_delimiter 옵션을 지원해야 합니다.

-   **module** : ux-iloader

-   **Category** : Usability

-   **재현 빈도** : Always

-   **증상** : 그동안 비공식적으로 지원되던 -informix
    옵션을 -extra\_col\_delimiter 이름으로 공식지원합니다.

    이 옵션은 레코드 마지막 컬럼 뒤에 컬럼 구분자와 레코드 구분자가
    연달아 위치한 경우, 이를 레코드의 끝으로 인식하기 위한 옵션입니다. 자세한 내용은 매뉴얼 [iloader#일반옵션]([https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/iLoader.md#%EC%9D%BC%EB%B0%98-%EC%98%B5%EC%85%98](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/iLoader.md#일반-옵션))을 참고한다.

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

### BUG-47691  PowerPC 와 PowerPC LE(little endian) 에서 jdbcAdapter 의 지원

-   **module** : rp-jdbcAdapter

-   **Category** : Portability

-   **재현 빈도** : Always

-   **증상** :  PowerPC 와 PowerPC LE(little endian) 용 jdbcAdapter 를 제공합니다.

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

### BUG-47692  PowerPC LE(little endian) 용 altimon 패키지 제공

-   **module** : ux-altiMon

-   **Category** : Other

-   **재현 빈도** : Always

-   **증상** : PowerPC LE 용 패키지에 altimon을 사용할 수 있도록 PICL
    Library를 제공합니다. 라이브러리 이름은 linux-ppc64.so 입니다. 자세한 내용은 [Utility 매뉴얼#altimon]([https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Utilities.md#%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9C](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Utilities.md#운영체제))을 참고합니다.

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

### BUG-47727  v$transaction 에 undo 진행 상태 모니터링 컬럼 추가

-   **module** : sm\_transaction

-   **Category** : Functionality

-   **재현 빈도** : Always

-   **증상** : UNDO 진행상태 모니터링이 용이하도록 V$TRANSACTION에 다음
    컬럼을 추가한다.

    - [PROCESSED_UNDO_TIME](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_4.md#processed_undo_time): 언두 시작 시점부터 현재까지 진행된 시간 (초)

    - [ESTIMATED_TOTAL_UNDO_TIME](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_4.md#estimated_total_undo_time): 언두 완료될때 까지 추정되는 총 소요
      시간 (초)

    - [TOTAL_LOG_COUNT](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_4.md#total_log_count) 한 트랜잭션의 모든 로그 갯수

    - [TOTAL_UNDO_LOG_COUNT](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_4.md#total_undo_log_count): 한 트랜잭션에서 앞으로 진행되야할 총 언두
      로그의 갯수  

    - [PROCESSED_UNDO_LOG_COUNT](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_4.md#processed_undo_log_count): 한 트랜잭션에서 언두완료된 로그 갯수

-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
        -   V\$TRANSACTION

            컬럼 추가)

            - [PROCESSED_UNDO_TIME](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_4.md#processed_undo_time): 언두 시작 시점부터 현재까지 진행된 시간 (초)

            - [ESTIMATED_TOTAL_UNDO_TIME](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_4.md#estimated_total_undo_time): 언두 완료될때 까지 추정되는 총 소요
  시간 (초)
            
            - [TOTAL_LOG_COUNT](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_4.md#total_log_count) 한 트랜잭션의 모든 로그 갯수
            
            - [TOTAL_UNDO_LOG_COUNT](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_4.md#total_undo_log_count): 한 트랜잭션에서 앞으로 진행되야할 총 언두
              로그의 갯수  
            
            - [PROCESSED_UNDO_LOG_COUNT](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_4.md#processed_undo_log_count): 한 트랜잭션에서 언두완료된 로그 갯수
        
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47762  32bit Linux 클라이언트 제공

-   **module** : pkg-map

-   **Category** : Other

-   **재현 빈도** : Always

-   **증상** : altibase v7.1의 32bit Linux 클라이언트를 제공합니다.

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

### BUG-47639  JDBC 드라이버에서 lob 컬럼값이 NULL일때 ResultSet.getBlob()이나 ResultSet.getClob()이 NULL을 반환하도록 연결속성이 추가되었습니다.

- **module** : mm-jdbc

- **Category** : Enhancement

- **재현 빈도** : Always

- **증상** : 현재 JDBC 드라이버는 LOB컬럼값이 null 일때,  ResultSet.getBlob()이나 ResultSet.getClob()을 호출하면 null이 아닌 LOB 객체를 반환합니다. 이로 인해, Hibernate 통합 테스트에서 다수의 테스트가 실패하는 문제가 있습니다. </br> 패치 적용 후 부터는 lob 컬럼값이 null인 경우, ResultSet.getBlob()  및 ResultSet.getClob() 수행시 NULL을 반환할수 있도록 JDBC 연결 속성 - lob_null_select가  추가되었습니다. Hibernate에서 Lob 관련 기능을 사용하려면 lob_null_select 속성을 off로 설정하는 것을 권장합니다. 이 경우 반환되는 NULL 에 대한 예외처리를 해줘야 합니다. </br>자세한 내용은 [JDBC매뉴얼]([https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/JDBC.md#lob-%EA%B4%80%EB%A0%A8-%EC%86%8D%EC%84%B1](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/JDBC.md#lob-관련-속성))을 참고합니다.  </br> Hibernate 는 5.4 이상 버전을 사용하는 것을 권장합니다.

- **재현 방법**

  - **재현 절차**

        create table t3 (i1 int, i2 blob);
        insert into t3 values (1, null);
        insert into t3 values (1, '');
        Connection sConn = getConnection();
        // Select
        PreparedStatement sStmt = sConn.prepareStatement("SELECT i1, i2 FROM t3");
        ResultSet sRs = sStmt.executeQuery();
        while (sRs.next())
        {
            int sI1 = sRs.getInt(1);
            Blob sI2 = sRs.getBlob(2);
            System.out.println("sI2==>" + sI2);
            System.out.println("sRs.wasNull()==>" + sRs.wasNull());
        }

  - **수행 결과**

        sI2==>Altibase.jdbc.driver.AltibaseBlob@6d21714c
        sRs.wasNull()==>true
        sI2==>Altibase.jdbc.driver.AltibaseBlob@108c4c35
        sRs.wasNull()==>true

  - **예상 결과**

        sI2==>null
        sRs.wasNull()==>true
        sI2==>null
        sRs.wasNull()==>true

- **Workaround**

- **변경사항**

  -   Performance view
  -   Property
  -   Compile Option
  -   Error Code

Fixed Bugs
----------

### BUG-45803  eager replication 중인 table에 ALTER TABLE ... RENAME CONSTRAINT 의 DDL이 실패하지 않는 문제가 있습니다.

-   **module** : rp

-   **Category** : Other

-   **재현 빈도** : Always

-   **증상** : eager replication 중인 table에 ALTER TABLE ... RENAME
    CONSTRAINT 의 DDL 구문이 실패해야 하는데, 수행되는 문제를
    수정합니다. 내부적으로 rename constraint 시에 replication 여부를
    확인하는 로직이 누락되어있어, 수정하였습니다.

- **재현 방법**

  - **재현 절차**

        eager replication 생성
        ALTER TABLE T1 RENAME CONSTRAINT T1_FK TO T1_FK_RE;

  -   **수행 결과**

          Alter success.

  -   **예상 결과**

          [ERR-31324 : Cannot execute DDL statements on a replicated table while replication is running in eager mode.]

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47580  Compact Disk Page 실패에 대한 정보 보강

-   **module** : sm-disk-page

-   **Category** : Fatal

-   **재현 빈도** : Rare

-   **증상** : Compact Disk Page 실패하는 경우, 에러로그에 아무런 정보를
    남기지 않고 비정상 종료하는 문제가 있습니다. Compact Disk
    Page 실패에 대한 예외처리를 추가하여 비정상종료하지 않고, [ERR-41082
    : Internal server error]를 출력하도록 수정합니다. 또한,
    altibase\_error.log 에 실패 정보(compactPage Failure)를 남기도록
    수정합니다.

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

### BUG-47628  AltibaseDatabaseMetaData.getSQLKeywords() 로 리턴되는 키워드에 누락이 있습니다.

-   **module** : mm-jdbc

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : AltibaseDatabaseMetaData.getSQLKeywords() 로 리턴되는
    키워드에 누락이 발생하는 문제 수정.

-   **재현 방법**

    -   **재현 절차**

            Connection sConn = getConnection("20300");DatabaseMetaData sMetaData = sConn.getMetaData();String sKeywords = sMetaData.getSQLKeywords();System.out.println("Keywords =>" + sKeywords);sConn.close();

    -   **수행 결과**

            ADD,ALTER,COLUMN,DATE,DROP,FOREGIN,RENAME,IDENTIFIED,INDEX,NUMBER,REPLECATION,BROWSE,BULK,CHECKPOINT,DATABASE,DISK,DUMMY,DUMP,IF,INDEX,LOAD,OFF,PLAN,PRINT,READ,RETURN,ROWCOUNT,RULE,SAVE,STATISTICS,TRIGGER,TRUNCATE

    -   **예상 결과**

            AT,IF,END,KEY,AGER,BODY,CAST,CUBE,EACH,EXEC,EXIT,FIFO,FULL,GOTO,JOIN,LEFT,LESS,LIFO,AFTER,AUDIT,BEGIN,CLOSE,CYCLE,ELSIF,FETCH,FIXED,FLUSH,INNER,LIMIT,ACCESS,BACKUP,BEFORE,COMMIT,CURSOR,ELSEIF,ENABLE,ESCAPE,EXTENT,ARCHIVE,CASCADE,COMMENT,COMPILE,CONJOIN,DECLARE,DECRYPT,DEQUEUE,DISABLE,DISJOIN,ENQUEUE,EXECUTE,FLUSHER,LIBRARY,COALESCE,CONTINUE,DATABASE,DELAUDIT,DISASTER,FUNCTION,INITRANS,LANGUAGE,DIRECTORY,FLASHBACK,FOLLOWING,ISOLATION,ARCHIVELOG,AUTOEXTEND,CHECKPOINT,COMPRESSED,DISCONNECT,EXTENTSIZE,CONSTRAINTS,DETERMINISTIC,AUTHID,CURRENT_USER,DEFINER,AS,BY,IN,IS,OF,ON,OR,TO,ADD,ALL,AND,ANY,ASC,FOR,NEW,NOT,OLD,OUT,ROW,SET,TOP,LOB,OFF,LINK,LOOP,MOVE,OPEN,OVER,READ,STEP,THAN,TYPE,WAIT,WORK,BULK,CASE,DESC,DROP,ELSE,FROM,INTO,LIKE,LOCK,MODE,NULL,SOME,THEN,TRUE,VIEW,WHEN,WITH,ALTER,APPLY,CROSS,FALSE,GRANT,GROUP,INDEX,LEVEL,MINUS,ORDER,PRIOR,START,TABLE,UNION,WHERE,LOCAL,MERGE,NULLS,OUTER,PIVOT,PURGE,QUEUE,RAISE,RIGHT,SHARD,SPLIT,STORE,UNTIL,USING,WHILE,WRITE,LINKER,MODIFY,ONLINE,OTHERS,REMOVE,RETURN,REVOKE,ROLLUP,COLUMN,CREATE,DELETE,EXISTS,HAVING,INSERT,NOCOPY,RENAME,ROWNUM,SELECT,UNIQUE,UNLOCK,UPDATE,VALUES,WITHIN,BETWEEN,CONNECT,DEFAULT,FOREIGN,INSTEAD,LATERAL,PRIMARY,SESSION,SQLCODE,SQLERRM,TRIGGER,VC2COLL,WRAPPED,_PROWID,LOGGING,MAXROWS,NOAUDIT,NOCYCLE,OFFLINE,PACKAGE,REBUILD,RECOVER,REPLACE,ROWTYPE,SEGMENT,STORAGE,SYNONYM,TYPESET,UNPIVOT,MAXTRANS,MOVEMENT,PARALLEL,ROLLBACK,ROWCOUNT,SEQUENCE,TRUNCATE,VARIABLE,VOLATILE,WHENEVER,COMPRESS,CONSTANT,DISTINCT,EXCEPTION,INTERSECT,PARTITION,RETURNING,LOGANCHOR,NOLOGGING,PRECEDING,PROCEDURE,SAVEPOINT,STATEMENT,TEMPORARY,CONSTRAINT,IDENTIFIED,PRIVILEGES,REORGANIZE,TABLESPACE,NOPARALLEL,PARAMETERS,PARTITIONS,REFERENCES,REFERENCING,LOCALUNIQUE,REPLICATION,SUPPLEMENTAL,MATERIALIZED,NOARCHIVELOG,REMOTE_TABLE,UNCOMPRESSED,SPECIFICATION,VARIABLE_LARGE,SHRINK_MEMPOOL,CONNECT_BY_ROOT,DUMP_CALLSTACKS,REMOTE_TABLE_STORE,KEEP,

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47647  오류없이 쿼리수행이 성공한 경우에도, The tablespace does not have enough free space ( TBS Name : ). 에러가 기록됩니다.

-   **module** : sm-disk-resource

-   **Category** : Message Error

-   **재현 빈도** : Always

-   **증상** : Undo tablespace는 max size까지 확장된 후에도 Free page를
    할당 받을 수 있습니다. 그러나 max size에 도달하기만 해도
    altibase\_sm.log에 The tablespace does not have enough free space (
    TBS Name :\<SYS\_TBS\_DISK\_UNDO\> ).에러가 기록되는 문제가
    있습니다. 해당 에러메시지는 free page를 더이상 할당 받을 수 없을때
    출력하도록 수정합니다. 또한 내부적으로 undo page 할당이 실패한
    경우와 TSS(Transaction Status Slot) page 할당 실패를 구별하여 에러를
    출력하도록 수정합니다.

    undo page 할당 실패시 : The tablespace does not have enough free
    space ( TBS Name :\<SYS\_TBS\_DISK\_UNDO\> ). Undo Page allocation
    failed.

    TSS page 할당 실패시: The tablespace does not have enough free space
    ( TBS Name :\<SYS\_TBS\_DISK\_UNDO\> ). TSS Page allocation failed.

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

### BUG-47650  endStmt() 실패시 서버가 비정상종료 합니다.

-   **module** : mm

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : endStmt 수행시에 dblink 관련 오류가 발생하였을때
    서버 비정상종료되는 문제를 수정합니다.  endStmt 실패시 assert를 발생시키지 않고 에러를 반환하도록 수정합니다.

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

### BUG-47658  aexport 통계값 처리시 single quotation 처리가 필요합니다

-   **module** : ux-aexport

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : aexport 통계값안에 single quotation이 있으면, 이를 값으로
    인식하기 위해 escape character(')를 추가해줘야 합니다.

    기존 aexport에서 값 처리시 single quotation에 대한 escape character
    처리가 빠져서 통계 데이터 파일을 잘못 인식하는 경우가 있어 이를
    수정했습니다.

- **재현 방법**

  - **재현 절차**

        drop table t1;
        create table t1 ( i1 varchar(200));
        insert into t1 values('가나''다');
        insert into t1 values('가나다라마바사아');
        exec gather_table_stats('sys', 't1');
        
        % aexport -s localhost -u sys -p manager
        % cat ALL_EXE_STATS.sql
        % is -f ALL_EXE_STATS.sql

  - **수행 결과**

        % cat ALL_EXE_STATS.sql
        EXEC SET_TABLE_STATS('"SYS"', '"T1"', NULL, 2, 2, 19, 0.000000);
        EXEC SET_COLUMN_STATS('"SYS"', '"T1"', '"I1"', NULL, 2, 0, 19, '가나'다', '가나다라마바사아');
        
        % is -f ALL_EXE_STATS.sql
        iSQL> EXEC SET_TABLE_STATS('"SYS"', '"T1"', NULL, 2, 2, 19, 0.000000);
        Execute success.
        iSQL> EXEC SET_COLUMN_STATS('"SYS"', '"T1"', '"I1"', NULL, 2, 0, 19, '가나'다', '가나다라마바사아');
        [Error] Unterminated command.

  -   **예상 결과**

          % cat ALL_EXE_STATS.sql
          EXEC SET_TABLE_STATS('"SYS"', '"T1"', NULL, 2, 2, 19, 0.000000);
          EXEC SET_COLUMN_STATS('"SYS"', '"T1"', '"I1"', NULL, 2, 0, 19, '가나''다', '가나다라마바사아');
          % is -f ALL_EXE_STATS.sql
          iSQL> EXEC SET_TABLE_STATS('"SYS"', '"T1"', NULL, 2, 2, 19, 0.000000);
          Execute success.
          iSQL> EXEC SET_COLUMN_STATS('"SYS"', '"T1"', '"I1"', NULL, 2, 0, 19, '가나''다', '가나다라마바사아');
          Execute success.

- **Workaround**

      사용자가 ALL_EXE_STATS.sql 파일을 직접 수정해야 한다.
      내용: 값안의 single quotation을 찾아서 single quotation 두개로 수동 변환.

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47690  INLIST 조건에 복합 Index를 사용할 경우 비정상 종료 할수 있습니다.

-   **module** : qp

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **증상** : INLIST 조건에 복합 Index를 사용할 경우 비정상 종료 할 수
    있어, 수정하였습니다.

- **재현 방법**

  -   **재현 절차**

          drop table t1;
          CREATE TABLE t1
          (
              FCT_CODE            VARCHAR(30) NOT NULL,
              PLANT_CODE          VARCHAR(30) NOT NULL,
              PARTS_CODE          VARCHAR(30) NOT NULL
          );
          drop index idx01;
          CREATE INDEX IDX01 ON t1 (FCT_CODE,PLANT_CODE,PARTS_CODE);
          insert into t1 values ( 1,1,'2203-007449');
          insert into t1 values ( 1,1,'GH63-14327A');
          insert into t1 values ( 1,1,'GH82-07284A');
          insert into t1 values ( 1,1,'GH82-13952A');
          insert into t1 values ( 1,1,'GH82-13952A');
          insert into t1 values ( 1,1,'GH82-13970A');
          insert into t1 values ( 1,1,'GH82-15493A');
          insert into t1 values ( 1,1,'GH94-16242A');
          insert into t1 values ( 1,1,'GH96-12150A');
          insert into t1 values ( 1,1,'GH96-12150B');
          insert into t1 values ( 1,1,'GH96-12150C');
          insert into t1 values ( 1,1,'GH96-12150D');
          insert into t1 values ( 1,1,'GH96-12151A');
          insert into t1 values ( 1,1,'GH96-12151B');
          insert into t1 values ( 1,1,'GH96-12151C');
          insert into t1 values ( 1,1,'GH96-12151D');
          insert into t1 values ( 1,1,'GH96-12152A');
          insert into t1 values ( 1,1,'GH96-12152B');
          insert into t1 values ( 1,1,'GH96-12152C');
          insert into t1 values ( 1,1,'GH96-12194A');
          insert into t1 values ( 1,1,'GH96-12664A');
          insert into t1 values ( 1,1,'GH96-12665A');
          insert into t1 values ( 1,1,'GH96-12666A');
          insert into t1 values ( 1,1,'GH96-12667A');
          insert into t1 values ( 1,1,'GH96-12671A');
          insert into t1 values ( 1,1,'GH96-12671B');
          insert into t1 values ( 1,1,'GH96-12671C');
          insert into t1 values ( 1,1,'GH96-12671D');
          insert into t1 values ( 1,1,'GH96-12671F');
          insert into t1 values ( 1,1,'GH96-12672A');
          insert into t1 values ( 1,1,'GH96-12672B');
          insert into t1 values ( 1,1,'GH96-12672C');
          insert into t1 values ( 1,1,'GH96-12672D');
          insert into t1 values ( 1,1,'GH96-12841A');
          drop table t2;
          CREATE TABLE t2
          (
              FCT_CODE            VARCHAR(30) NOT NULL,
              PLANT_CODE          VARCHAR(30) NOT NULL,
              LRNK_PARTS_CODE     VARCHAR(30) NOT NULL
          );
          drop index idx2;
          create index idx2 on t2 ( FCT_CODE, PLANT_CODE, LRNK_PARTS_CODE );
          insert into t2 values ( 'C5H0A', 'P516','''2203-007449''');
          insert into t2 values ( 'C5H0A', 'P516','''GH63-14327A''');
          insert into t2 values ( 'C5H0A', 'P516','''GH82-07284A''');
          insert into t2 values ( 'C5H0A', 'P516','''GH82-13952A''');
          insert into t2 values ( 'C5H0A', 'P516','''GH82-13952A''');
          insert into t2 values ( 'C5H0A', 'P516','''GH82-13970A''');
          insert into t2 values ( 'C5H0A', 'P516','''GH82-15493A''');
          insert into t2 values ( 'C5H0A', 'P516','''GH94-16242A''');
          insert into t2 values ( 'C5H0A', 'P516','''GH96-12150A''');
          insert into t2 values ( 'C5H0A', 'P516','''GH96-12150B''');
          insert into t2 values ( 'C5H0A', 'P516','''GH96-12150C''');
          insert into t2 values ( 'C5H0A', 'P516','''GH96-12150D''');
          insert into t2 values ( 'C5H0A', 'P516','''GH96-12151A''');
          insert into t2 values ( 'C5H0A', 'P516','''GH96-12151B''');
          insert into t2 values ( 'C5H0A', 'P516','''GH96-12151C''');
          insert into t2 values ( 'C5H0A', 'P516','''GH96-12151D''');
          insert into t2 values ( 'C5H0A', 'P516','''GH96-12152A''');
          insert into t2 values ( 'C5H0A', 'P516','''GH96-12152B''');
          insert into t2 values ( 'C5H0A', 'P516','''GH96-12152C''');
          insert into t2 values ( 'C5H0A', 'P516','''GH96-12194A''');
          insert into t2 values ( 'C5H0A', 'P516','''GH96-12664A''');
          insert into t2 values ( 'C5H0A', 'P516','''GH96-12665A''');
          insert into t2 values ( 'C5H0A', 'P516','''GH96-12666A''');
          insert into t2 values ( 'C5H0A', 'P516','''GH96-12667A''');
          insert into t2 values ( 'C5H0A', 'P516','''GH96-12671A''');
          insert into t2 values ( 'C5H0A', 'P516','''GH96-12671B''');
          insert into t2 values ( 'C5H0A', 'P516','''GH96-12671C''');
          insert into t2 values ( 'C5H0A', 'P516','''GH96-12671D''');
          insert into t2 values ( 'C5H0A', 'P516','''GH96-12671F''');
          insert into t2 values ( 'C5H0A', 'P516','''GH96-12672A''');
          insert into t2 values ( 'C5H0A', 'P516','''GH96-12672B''');
          insert into t2 values ( 'C5H0A', 'P516','''GH96-12672C''');
          insert into t2 values ( 'C5H0A', 'P516','''GH96-12672D''');
          insert into t2 values ( 'C5H0A', 'P516','''GH96-12841A''');
          insert into t2 values ( 'C5H0A', 'P516','''GH96-12841B''');
          insert into t2 values ( 'C5H0A', 'P516','''GH96-12841D''');
          insert into t2 values ( 'C5H0A', 'P516','''GH96-12841E''');
          insert into t2 values ( 'C5H0A', 'P516','''GH96-12861C''');
          insert into t2 values ( 'C5H0A', 'P516','''GH96-12946A''');
          insert into t2 values ( 'C5H0A', 'P516','''GH96-12946B''');
          insert into t2 values ( 'C5H0A', 'P516','''GH96-12946D''');
          insert into t2 values ( 'C5H0A', 'P516','''GH96-12946E''');
          insert into t2 values ( 'C5H0A', 'P516','''GH96-13048A''');
          insert into t2 values ( 'C5H0A', 'P516','''GH96-13048B''');
          insert into t2 values ( 'C5H0A', 'P516','''GH96-13048C''');
          WITH QQQ AS (
                  SELECT CAST(LISTAGG(''''||PARTS_CODE||'''',',') WITHIN GROUP (ORDER BY PARTS_CODE) AS VARCHAR(32000)) AS QR_NO FROM t1
                  )
          SELECT * FROM t2 A
          WHERE FCT_CODE = 'C5H0A'
          AND PLANT_CODE = 'P516'
          AND INLIST (A.LRNK_PARTS_CODE, (SELECT QR_NO FROM QQQ B))
              ;

  -   **수행 결과**

          [ERR-91015 : Communication failure.]

  -   **예상 결과**

          A.FCT_CODE A.PLANT_CODE
          -------------------------------------------------------------------
          A.LRNK_PARTS_CODE
          ----------------------------------
          C5H0A P516
          '2203-007449'
          ...
          ... 중간 생략..
          34 rows selected.

-   **Workaround**

        not use index or use one index

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47693  CLOB 컬럼에 empty 데이터가 있는 경우 조회 결과가 틀립니다

-   **module** : qp-select

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : CLOB 컬럼에 empty 데이터가 있는 경우 조회 결과가 틀리는
    현상 수정

- **재현 방법**

  -   **재현 절차**

          drop table tt;
          create table tt(i1 int,i2 clob);
          INSERT INTO TT VALUES ( 1, 'ABCDEFG1' );
          INSERT INTO TT VALUES ( 2, empty_clob() );
          INSERT INTO TT VALUES ( 3, null );
          INSERT INTO TT VALUES ( 11, 'ABCDEFG2' );
          INSERT INTO TT VALUES ( 12, empty_clob() );
          INSERT INTO TT VALUES ( 13, null );
          INSERT INTO TT VALUES ( 21, 'ABCDEFG3' );
          INSERT INTO TT VALUES ( 22, empty_clob() );
          INSERT INTO TT VALUES ( 23, null );
          select * from tt where i2 = 'ABCDEFG1';

  - **수행 결과**

        iSQL> select * from tt where i2 = 'ABCDEFG1';
        TT.I1
        --------------
        TT.I2
        -----------------------------------------------------------------------------------
        1
        ABCDEFG1
        2
        
        2 rows selected.

  -   **예상 결과**

          iSQL> select * from tt where i2 = 'ABCDEFG1';
          TT.I1
          --------------
          TT.I2
          -----------------------------------------------------------------------------------
          1
          ABCDEFG1
          1 rows selected.

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47702  \<\> 연산자가 있을 경우 Selectivity가 1인 INDEX에 대한 잘못된 index 선택 오류

-   **module** : qp

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : \<\> 연산자가 있을 경우 Selectivity가 1인 INDEX에 대한
    잘못된 index 선택 오류 수정

- **재현 방법**

  - **재현 절차**

        drop table t_zone_cell;
        create table t_zone_cell
        (
        ZONE_CODE                                VARCHAR(20) NOT NULL,
        FILE_TYPE                                VARCHAR(5)  ,
        CUID                                     VARCHAR(10) NOT NULL,
        LOCATION_ID                              VARCHAR(14) NOT NULL,
        BTS_NAME                                 VARCHAR(128)    VARIABLE  ,
        DATE                                     DATE        NOT NULL,
        CREATE_DATE                              DATE        ,
        STATUS                                   CHAR(1)     NOT NULL,
        ZONE_ID                                  VARCHAR(6)
        );
        alter table t_zone_cell add primary key(ZONE_CODE, LOCATION_ID);
        create index IX_ZONE_CELL on t_zone_cell(STATUS);
        insert into t_zone_cell select rownum, 'A', 'A', 'A', 'A', sysdate, sysdate, 'M', 'A' from dual connect by level < 201236;
        exec GATHER_TABLE_STATS( 'SYS', 't_zone_cell' );
        alter session set explain plan = on;
        alter system set trclog_detail_predicate=1;
        alter system set TRCLOG_EXPLAIN_GRAPH = 1;
        
        select * from t_zone_cell WHERE ZONE_CODE = 'a' AND FILE_TYPE = 'a' AND LOCATION_ID = 'a' AND   STATUS <> 'D'   ;

  -   **수행 결과**

          use index ix_zone_cell

  -   **예상 결과**

          use pk index

-   **Workaround**

        NO INDEX ( t_zone_cell, IX_ZONE_CELL );

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47714  cmERR\_ABORT\_SELECT\_ERROR 에러 발생시 CLI 메모리가 증가합니다.

-   **module** : mm-cli

-   **Category** : Memory Error

-   **재현 빈도** : Always

-   **증상** : sqlcli에서 cmERR_ABORT_SELECT_ERROR 에러 발생시, Client의 메모리가 증가하거나, 서버의 응답을 무한 대기(Hang)할 수 있습니다.
    

이 문제를 해결하기 위해, SQLCLI Library 를 이용한 송수신(send, receive) 단계에서 각종 OS 이상 에러 발생시, 연결을 disconnect 하여 이후의 오동작을 발생하지 않게 합니다. 패치 적용 후에는 이 경우 Client는 Sever와 Connection이 끊기게 되므로 Connection을 다시 하여야 합니다.
    
-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

        cmERR_ABORT_SELECT_ERROR 에러 발생시 
        SQLDisconnect - SQLDriverConnect 
        로 재연결 후 쿼리 실행.

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47715  redo log가 누락되는 현상이 발생하여 recovery 에서 실패합니다.

-   **module** : sm-disk-recovery

-   **Category** : Fatal

-   **재현 빈도** : Rare

-   **증상** : mini transaction 을 rollback 하는 경우 redo log가 기록되지 않는 문제가 있어, 수정합니다.
    
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

### BUG-47732  empty lob을 PSM 내부에서 select 할 때 에러 발생합니다

-   **module** : qp-psm-trigger-execute

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : empty lob을 PSM 내부에서 select 할 때 에러없이 수행되되록 수정합니다.

-   **재현 방법**

    -   **재현 절차**

            drop table t1;
            create table t1(i1 int,c1 clob);
            insert into t1 values(1, empty_clob());
            insert into t1 values(2, 'abc');
            insert into t1 values(3, null);
            create or replace procedure proc2(v1 in integer)
            as
              v2 clob;
            begin
              select c1 into v2 from t1 where i1 = v1;
              system_.println('c1 = ' || v2);
            end;
            /
            exec proc2(1);
            exec proc2(2);
            exec proc2(3);

    -   **수행 결과**

            iSQL> exec proc2(1);
            [ERR-2100D : Invalid data type length
            at "SYS.PROC2", line 5]
            iSQL> exec proc2(2);
            c1 = abc
            Execute success.
            iSQL> exec proc2(3);
            c1 =
            Execute success.

    -   **예상 결과**

            iSQL> exec proc2(1);
            c1 =
            Execute success.
            iSQL> exec proc2(2);
            c1 = abc
            Execute success.
            iSQL> exec proc2(3);
            c1 =
            Execute success.

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47734  INDEX Scan시 문자 사이에 탭이 있을경우, 데이터가 조회되지 않는 문제가 있습니다.

-   **module** : mt

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** : INDEX Scan시 문자 사이에 탭이 있을 경우, 잘못 탐색하는
    문제가 있어 수정합니다.

-   **재현 방법**

    -   **재현 절차**

            alter session set explain plan = on;
            alter session set trclog_detail_predicate = 1;
            drop table t2;
            create table t2 as select upja_cd, cp_nm, CP_COM_NM from t1 where cp_nm like '(주)엠서클%';
            create index idx11 on t2  ( cp_nm);
            select * from t2 where cp_nm = '(주)엠서클' and upja_cd = '55';

    -   **수행 결과**

            No rows

    -   **예상 결과**

            1 rows selected

-   **Workaround**

        update 컬럼

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47735  2개 이상의 session으로 Disk LOB insert 중 deadlock 으로 hang 발생.

-   **module** : sm-disk-page

-   **Category** : Hang

-   **재현 빈도** : Frequence

-   **증상** :  2개 이상의 session으로 Disk LOB insert 중 내부적으로
    deadlock이 발생할 수 있어, 수정하였습니다.

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

### BUG-47736  uniqueness가 깨진 memory index 있는 경우에 서버를 띄우면 안됩니다.

-   **module** : sm-mem-index

-   **Category** : Efficiency

-   **재현 빈도** : Always

-   **증상** : 서버 구동시에 memory unique index 에 인덱스 키 중복이
    발생해도 정상적으로 startup되는 문제가 있습니다. 키 중복이 발생하는
    경우, memory unique index 정보를 출력하고 startup 실패하도록
    수정합니다.

    기존에 memory unique index 에 키 중복이 있는 고객의 경우, 이번 패치
    적용후 startup 이 실패할 수 있습니다. 이 경우, 패치 후
    INDEX\_REBUILD\_AT\_STARTUP = 0 으로 starup 
    후에 altibase\_error.log를 확인하여 정리 후 재구동 해야 합니다.

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

### BUG-47741  HP-UX에서 iSQL 암호 입력 시 Here document 처리를 해야 합니다

-   **module** : ux-isql

-   **Category** : Functional Error

-   **재현 빈도** : Always

-   **증상** :

- **재현 방법**

  -   **재현 절차**

          아래와 같이 스크립트 작성 (vi streamInput.sh)
          #!/bin/sh
          ISQL="${ALTIBASE_HOME}/bin/isql -s localhost -u sys -silent"
          ${ISQL} << EOF
          select * from tab;
          EOF
      
  - **수행 결과**

        % ./streamInput.sh
        [ERR-4102E : Invalid password]

  -   **예상 결과**

          % ./streamInput.sh
          Write Password :
          USER NAME TABLE NAME TYPE
          --------------------------------------------------------------------------------------
          SYSTEM_ DBA_USERS_ SYSTEM TABLE
          SYSTEM_ STO_COLUMNS_ SYSTEM TABLE
          ... 중간생략

-   **Workaround**

        % vi ./streamInput.sh
        #!/bin/sh
        ISQL="${ALTIBASE_HOME}/bin/isql -s localhost -u sys -silent -p $2"
        ${ISQL} << EOF
        select * from tab;
        EOF
    
-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47744  View Merge되는 인라인뷰의 컬럼을 특정 Aggregation에 사용한경우 비정상 종료할 수 있습니다.

-   **module** : qp-select-pvo

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **증상** : View Merge되는 인라인뷰의 컬럼을 특정 Aggregation에
    사용한 경우 비정상 종료 할 수 있는 문제를 수정합니다.

- **재현 방법**

  -   **재현 절차**

          CREATE TABLE T1 ( i1 NUMERIC(5) );
          SELECT CAST( MIN(V1.i1) KEEP(DENSE_RANK FIRST ORDER BY i1 ASC NULLS LAST) AS VARCHAR(10)) AS C_DEPTH
                 FROM (
                       SELECT i1
                         FROM T1
                      ) as V1
               ;

  - **수행 결과**

        [ERR-31455 : Failed to work because an internal exception occurred from an OS.[Contact Altibase's Support Center]] 또는 드물게 비정상 종료 발생할 수 있습니다.

  -   **예상 결과**

          C_DEPTH
          --------------
          
          1 row selected.

-   **Workaround**

        1) main query에 /*+ no_merge( view_name ) */  또는 /*+ oredered */ 힌트 사용
        2) in-line view에 /*+ no_merge */ 
        SELECT CASE WHEN ( 0 = 0 )
                            THEN MIN(i1) KEEP(DENSE_RANK FIRST ORDER BY i1 ASC NULLS LAST)
                          ELSE 1
                          END AS C_DEPTH
               FROM (
                     SELECT /*+ no_merge */ i1
                       FROM T1
                    )
             ;

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47745 sdcRow::makeTrailingNullUpdateInfo()의 디버깅 정보 출력 위치 변경.

-   **module** : sm-disk-collection

-   **Category** : Message Error

-   **재현 빈도** : Rare

-   **증상** : altibase\_error.log 에 의미 없는 로그인 [ Column ], [
    Value ] 가 반복적으로 기록되는 문제가 있습니다. altibase\_dump.log
    에 기록되는 로그의 일부가 altibase\_error.log 에 출력되고 있어
    수정합니다.

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

### BUG-47750 CONNECT BY 절에 variable 컬럼을 포함한 조인 오퍼레이션을 사용한 경우 Altibase 서버가 비정상 종료할 수 있습니다.

-   **module** : qp

-   **Category** : Fatal

-   **재현 빈도** : Frequence

-   **증상** : Connect by 구문에 Variable column 과 join이 함께 사용할
    경우 비정상 종료할 수 있어, 수정합니다.

- **재현 방법**

  - **재현 절차**

        drop table t1;
        drop table t2;
        create table t1 ( i1  VARCHAR(80)     VARIABLE , i2  VARCHAR(80)     VARIABLE );
        insert into t1 values ( 2222222222222222222222222222222222222222 , 1111111111111111111111111111111111111111);
        insert into t1 values ( 3333333333333333333333333333333333333333 , 2222222222222222222222222222222222222222);
        insert into t1 values ( 4444444444444444444444444444444444444444 , 3333333333333333333333333333333333333333);
        insert into t1 values ( 5555555555555555555555555555555555555555 , 4444444444444444444444444444444444444444);
        insert into t1 values ( 6666666666666666666666666666666666666666 , 5555555555555555555555555555555555555555);
        
        create table t2 ( i1  VARCHAR(80)     VARIABLE , i2  VARCHAR(80)     VARIABLE );
        insert into t2 values ( 1111111111111111111111111111111111111111 , 47);
        insert into t2 values ( 2222222222222222222222222222222222222222 , 36);
        insert into t2 values ( 3333333333333333333333333333333333333333 , 26);
        insert into t2 values ( 4444444444444444444444444444444444444444 , 16);
        insert into t2 values ( 47, 6);
        select t1.i1, t1.i2 from t1 left outer join t2 on t2.i1 = t1.i1  connect by t1.i1 = prior t1.i2 ;

  - **수행 결과**

        iSQL>  select t1.i1, t1.i2 from t1 left outer join t2 on t2.i1 = t1.i1 connect by t1.i1 = prior t1.i2 ;
        I1
        ------------------------------------------------------------------------------------
        I2
        ------------------------------------------------------------------------------------
        2222222222222222222222222222222222222222
        1111111111111111111111111111111111111111
        3333333333333333333333333333333333333333
        2222222222222222222222222222222222222222
        4444444444444444444444444444444444444444
        3333333333333333333333333333333333333333
        5555555555555555555555555555555555555555
        4444444444444444444444444444444444444444
        6666666666666666666666666666666666666666
        5555555555555555555555555555555555555555
        5 rows selected.

  -   **예상 결과**

      
          I1
          ------------------------------------------------------------------------------------
          I2
          ------------------------------------------------------------------------------------
          2222222222222222222222222222222222222222
          1111111111111111111111111111111111111111
          3333333333333333333333333333333333333333
          2222222222222222222222222222222222222222
          2222222222222222222222222222222222222222
          1111111111111111111111111111111111111111
          4444444444444444444444444444444444444444
          3333333333333333333333333333333333333333
          3333333333333333333333333333333333333333
          2222222222222222222222222222222222222222
          2222222222222222222222222222222222222222
          1111111111111111111111111111111111111111
          5555555555555555555555555555555555555555
          4444444444444444444444444444444444444444
          4444444444444444444444444444444444444444
          3333333333333333333333333333333333333333
          3333333333333333333333333333333333333333
          2222222222222222222222222222222222222222
          2222222222222222222222222222222222222222
          1111111111111111111111111111111111111111
          6666666666666666666666666666666666666666
          5555555555555555555555555555555555555555
          5555555555555555555555555555555555555555
          4444444444444444444444444444444444444444
          4444444444444444444444444444444444444444
          3333333333333333333333333333333333333333
          3333333333333333333333333333333333333333
          2222222222222222222222222222222222222222
          2222222222222222222222222222222222222222
          1111111111111111111111111111111111111111
          15 rows selected.

- **Workaround**

      iSQL> select A.i1, A.i2 
            from ( select t1.i1, t1.i2 from t1 left outer join t2 on t2.i1 = t1.i1 ) A
            connect by A.i1 = prior A.i2 ;

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47752 LEFT OUTER JOIN 오른쪽이 집합 연산을 포함한 인라인 뷰이고 ON 절이 OR 조건으로 구성된 경우 Altibase 서버가 비정상 종료합니다.

-   **module** : qp-select-execute

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **증상** : left outer join의 on절이 OR 조건으로 구성되어있고, 오른쪽
    view에 aggregation이 존재할 경우 비정상 종료할수 있는 문제를
    수정합니다.

- **재현 방법**

  -   **재현 절차**

          drop table t1;
          create table t1 ( i1 integer, i2 varchar(10));
          insert into t1 values ( 1, 'AAA');
          insert into t1 values ( 2, 'BBB');
          drop table t2;
          create table t2 (
          TERM_SQ                                 integer,
          TAXCRE_RT                              integer,
          TO_AMT                                   integer );
          insert into t2 values(17,          0,       3980000 );
          insert into t2 values(17,          0,       4490000 );
          SELECT   TG.GUBUN_CD,  TG.GUBUN_NM
          FROM (   SELECT  i1 AS GUBUN_CD,    i2 AS GUBUN_NM   FROM t1 
                       ) TG
                    LEFT OUTER JOIN (
                      SELECT  HDI.TERM_SQ, SUM(HDI.TAXCRE_RT)  AS NPN_RT
                      FROM t2 HDI
                      GROUP BY HDI.TERM_SQ
                      ) HDI
                  ON (TG.GUBUN_CD = '1' AND HDI.TERM_SQ = 17) OR (TG.GUBUN_CD = '2' AND HDI.TERM_SQ = 18 )
          ;

  -   **수행 결과**

          [ERR-91015 : Communication failure.]

  -   **예상 결과**

          GUBUN_CD    GUBUN_NM
          ---------------------------
          1           AAA
          2           BBB
          2 rows selected.

-   **Workaround**

        no

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-47754 중단된 log record로 Recovery를 시도하는 경우, 비정상 종료 할 수 있습니다.

-   **module** : sm\_recovery

-   **Category** : Fatal

-   **재현 빈도** : Rare

-   **증상** : 서버 비정상 종료시 logfile의 마지막 log record는 일부만
    기록되다가 멈추게 됩니다. 이후 Reovery수행 중 log record를 확인하는
    과정에서, 기록이 중단된 log record는 무시하고 기록이 완료된
    log까지 Recovery 합니다.

    그런데 log record 를 확인 하는 로직에서 문제가 있어, 기록이 완료되지
    않은 log record를 기록완료된 log로 판단하고 recovery를 시도하게 되어
    비정상 종료 합니다.

    log record를 검증하는 코드의 오류를 분석하여, 정확하게 검증하도록
    수정하였습니다.

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

### BUG-47758 트랜잭션 고립화 수준(isolation level)에 따라 CONNECT BY 절을 포함한 SQL 수행 시 Altibase 서버가 비정상 종료할 수 있습니다.

-   **module** : sm\_collection

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **증상** : CONNECT BY 의 open cursor 에서 isolation level을 잘못 설정하는 문제가 있어 수정합니다.

- **재현 방법**

  -   **재현 절차**

          drop table T1;
          create table T1 ( IDX INTEGER , PARENT_IDX INTEGER ) tablespace sys_tbs_disk_data;
          INSERT INTO T1 VALUES( 1, 0 );
          AUTOCOMMIT OFF;
          SET TRANSACTION ISOLATION LEVEL REPEATABLE READ;
          SELECT IDX FROM T1 CONNECT BY PRIOR IDX = PARENT_IDX ;

  - **수행 결과**

        iSQL> SELECT IDX FROM T1 CONNECT BY PRIOR IDX = PARENT_IDX ;
        [ERR-91015 : Communication failure.]

  -   **예상 결과**

          iSQL> SELECT IDX FROM T1 CONNECT BY PRIOR IDX = PARENT_IDX ;
          IDX
          --------------
          1
          1 row selected.

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

Changes
-------

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version | sharding version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- | ---------------- |
| 7.1.0.3.6        | 6.5.1                   | 8.7.1        | 7.1.7               | 7.4.5                        | 2.2.1            |

> Altibase 7.1 패치 버전별 히스토리는 [Version_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7_1_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의
> 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는
> 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

> 패치를 롤백하려는 경우, [메타다운그레이드](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Installation.md#%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9Cmeta-downgrade)를 참고한다.

#### CM protocol Version

통신 프로토콜 버전은 변경되지 않았다.

#### Replication protocol Version

Replication 프로토콜 버전은 변경되지 않았다.

#### Sharding Version

샤딩 버전은 변경 되지 않았다.

> 알티베이스 샤딩 프로토콜 및 메타는 상위, 하위 호환성을 보장하지
> 않는다. 즉, 샤딩 버전이 다른 경우, 재구성해야 한다.

### 프로퍼티

추가/변경/삭제된 프로퍼티 없음.

### 성능 뷰

#### 변경된 성능 뷰

[v$transaction](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/GeneralReference_4.md#vtransaction)