# Spring Data JPA User's Guide for Altibase

-   [개요](#개요)
-   [Spring Data JPA 프로젝트 생성](#Spring-Data-JPA-프로젝트-생성)
-   [Hibernate에 Altibase Dialect 클래스 파일 추가](#Hibernate에-Altibase-Dialect-클래스-파일-추가)
-   [Altibase 연계 확인](#Altibase-연계-확인)





## 개요

Spring Data JPA에서 Altibase와 연동하기 위한 설정 방법을 설명한다.



### JPA 와 Spring Data JPA

JPA(Java Persistence API)는 ORM(Object-Reliational Mapping)을 위한 J2EE 스펙으로, 자바 어플리케이션에서 관계형 데이터베이스를 사용하는 방식을 정의한 인터페이스이다. 이 JAP 구현제로는 Hibernate, DataNucleus, EclipseLink 등이 있는데 Spring Data JPA는 내부적으로 Hibernate를 사용하여  JPA를 쉽게 사용할 수 있도록 제공하는 모듈이다. 원본 Hibernate 모듈엔 Altibase Dialect 클래스는 없다. 그래서 Altibase에서 제공하는 소스를 컴파일하여 Hibernate에 추가하면 Spring Data JPA에서 Altibase와 연동하여 사용할 수 있다. (Hibernate 자체 사용에 대해서는 [링크 문서](https://aid.altibase.com/pages/viewpage.action?pageId=14057878)를 참조한다.)

본 문서는 다음 순서로 진행한다.

1. Spring Data JPA를 사용하는 Spring 프로젝트 생성
2. 라이브러리중 Hibernate를 찾아 Altibase Dialect 클래스 파일을 추가하고 패키지 재생성
3. Spring 프로젝트 샘플 코드 수행을 통해 Altibase 연계여부 확인



## Spring Data JPA 프로젝트 생성

본 문서에서는 STS(Spring Tool Suite)를 사용하여 프로젝트를 생성한다.

1. STS에서 Spring Starter Project로 신규 프로젝트를 생성한다. 

   ![](C:\MyFolder\1.기술문서\altibase manual\Documents\How to Use 3rd Party for Altibase\kor\Images\JPA\spring-starter-01.png)

1. Spring Starter Project의 Dependencies에서 Spring Data JPA를 찾아서 선택해 준다. Entity 클래스 작성 편의를 위해 Lombok도 추가한다.

   ![](C:\MyFolder\1.기술문서\altibase manual\Documents\How to Use 3rd Party for Altibase\kor\Images\JPA\spring-starter-02.png)

3. Finish 버튼을 클릭하면 Progress 가 활성화되면서 관련 라이브러리를 인터넷을 통해 다운로드 받는다.

   

## Hibernate에 Altibase Dialect 클래스 파일 추가

- Spring Data JPA와 관련된 Hibernate 라이브러리에는 Altibase Dialect 관련 파일이 포함되어 있지 않으므로 Altibase Dialect 관련 클래스를 컴파일하여 기존 hibernate-core 라이브러리에 추가해야 한다.

- Altibase Dialect 관련 파일을 추가하기 위해서는 다음 순서로 진행한다.

  1. Hibernate 버전용 [Altibase Dialect Java 소스](https://github.com/ALTIBASE/hibernate-orm/blob/master/ALTIBASE_DIALECT_PORTING.md#altibasedialectjava-compile)를 다운로드 한다. 

  2. maven / gradle 프로젝트에 따른 hibernate-core 라이브러리 파일 위치를 확인한다.

     - maven : *user_home_directory*/.m2/repository 에 위치

       ```
       $ user_home_directory/.m2/repository/org/hibernate/hibernate-core/x.x.x.Final/hibernate-core-x.x.x.Final.jar
       ```

     - gradle : *user_home_directory*/.gradle/caches/modules-2/files-2.1 에 위치

       ```
       $ user_home_directory/.gradle/caches/modules-2/files-2.1/org.hibernate/x.x.x-Final/라이브러리_파일_해쉬_값/hibernate-core-x.x.x.Final.jar
       ```

  3. hibernate-core-x.x.x.Final.jar 파일을 Altibase Dialect Java 소스가 있는 디렉토리에 압축을 푼다.

  4. Altibase Dialect 파일들을 다음 순서로 컴파일 한다.

     ```
     javac -d . -cp . SequenceInformationExtractorAltibaseDatabaseImpl.java
     javac -d . -cp . AltibaseLimitHandler.java
     javac -d . -cp . AltibaseDialect.java
     ```

  5. 컴파일이 완료되면 현재 디렉토리 아래에 다음과 같은 클래스 파일이 생성된다.

     ```
     ./org/hibernate/tool/schema/extract/internal/SequenceInformationExtractorAltibaseDatabaseImpl.class
     ./org/hibernate/dialect/pagination/AltibaseLimitHandler.class
     ./org/hibernate/dialect/AltibaseDialect.class
     ```

  6. 7번 수행 시 jar 파일에 포함시키지 않기 위해 다운로드 받았던 Altibase Dialet Java 소스(*.java) 를 삭제 혹은 다른 곳으로 옮긴다.

  7. 새로 컴파일된 Altibase Dialect 관련 클래스를 이용하여 새로운 jar 파일을 생성한다.
  
     ```
     jar -cvfm hibernate-core-x.x.x.Final.jar META-INF/MANIFEST.MF .
     ```
  
  7. 새로 생성된 jar 파일을 2번의 기존 라이브러리 디렉토리에 복사한다.



## Altibase 연계 확인

STS에서 샘플 소스 작성을 통해 Altibase와의 연계 여부를 확인한다.

1. STS의 Project -> Peroperties -> Java Build Path -> Libraries -> Add External JARs 클릭하여 Altibase JDBC 드라이버 파일을 추가한다.

   ![](C:\MyFolder\1.기술문서\altibase manual\Documents\How to Use 3rd Party for Altibase\kor\Images\JPA\add-jdbc-driver.png)

2. src/main/resources/application.properties 파일에 아래 내용을 추가한다.

   ```
   # Altibase DB
   spring.datasource.driver-class-name=Altibase.jdbc.driver.AltibaseDriver
   spring.datasource.url=jdbc:Altibase://172.16.135.35:20300/mydb   # ex) jdbc:Altibase://db_ip:db_port/db_name
   spring.datasource.username=sys
   spring.datasource.password=manager
   
   # to avoid isValid() error in Hikari CP
   spring.datasource.hikari.connection-test-query=select 1 from dual
   
   #JPA/Hibernate
   spring.jpa.database-platform=org.hibernate.dialect.AltibaseDialect
   spring.jpa.hibernate.ddl-auto=create   # 기존테이블 삭제 후 다시 생성 (DROP & CREATE)
   spring.jpa.show-sql=true
   ```

3. 아래와 같 Entity 클래스를 작성한다.

   ![](C:\MyFolder\1.기술문서\altibase manual\Documents\How to Use 3rd Party for Altibase\kor\Images\JPA\sample-source.png)

4. STS의 Boot Dashboard에서 해당 프로젝트를 선택하고 상단 Start 버튼 클릭하여 수행한다.

   ![](C:\MyFolder\1.기술문서\altibase manual\Documents\How to Use 3rd Party for Altibase\kor\Images\JPA\boot-bashboard.png)

5. STS의 Console 창에 결과가 출력된다. application.properties의 spring.jpa.show-sql=true 설정에 의해 메세지 마지막 부분에는 DDL 문장이 출력되어 있다. (출력된 오류는, 시작 시 테이블을 먼저 drop 하는데 초기엔 테이블이 없기 때문에 발생된 오류로 재 수행시 해당 오류는 발생하지 않는다.) 

   ![](C:\MyFolder\1.기술문서\altibase manual\Documents\How to Use 3rd Party for Altibase\kor\Images\JPA\console-result.png)

6. Altibase의 서버에 접속하여 iSQL로 테이블이 생성되어 있는지 확인하여 연계 여부를 확인한다.

   ```
   iSQL> desc account;
   [ TABLESPACE : SYS_TBS_MEM_DATA ]
   [ ATTRIBUTE ]
   ------------------------------------------------------------------------------
   NAME                                     TYPE                        IS NULL
   ------------------------------------------------------------------------------
   ID                                       BIGINT          FIXED       NOT NULL
   PASSWORD                                 VARCHAR(255)    VARIABLE
   USERNAME                                 VARCHAR(255)    VARIABLE
   [ INDEX ]
   ------------------------------------------------------------------------------
   NAME                                     TYPE     IS UNIQUE     COLUMN
   ------------------------------------------------------------------------------
   UK_GEX1LMAQPG0IR5G1F5EFTYAA1             BTREE    UNIQUE        USERNAME ASC
   __SYS_IDX_ID_173                         BTREE    UNIQUE        ID ASC
   [ PRIMARY KEY ]
   ------------------------------------------------------------------------------
   ID
   ```
