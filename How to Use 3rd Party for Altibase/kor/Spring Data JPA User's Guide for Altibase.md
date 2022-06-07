# Spring Data JPA User's Guide for Altibase

<br/>

<br/>



# 목차

-   [개요](#개요)
-   [Spring Data JPA 프로젝트 생성](#Spring-Data-JPA-프로젝트-생성)
-   [Hibernate에 Altibase Dialect 클래스 파일 추가](#Hibernate에-Altibase-Dialect-클래스-파일-추가)
-   [Altibase 연계 확인](#Altibase-연계-확인)





# 개요

STS(Spring Tool Suite) 에서 Spring Data JPA를 이용하여 Altibase 서버와 연동하는 방법을 설명한다.



#### JPA 와 Spring Data JPA

JPA(Java Persistence API)는 ORM(Object-Reliational Mapping)을 위한 J2EE 스펙으로, 자바 어플리케이션에서 관계형 데이터베이스를 사용하는 방식을 정의한 인터페이스이다. JPA라는 명세서의 구현체로 하이버네이트(Hibernate), 이클립스링크(EclipseLink), DataNucleus 등이 있다. Spring Data JPA는 Spring에서 제공하는 모듈로, JPA 구현체들을 추상화하여 개발자가 JPA를 더 쉽고 편하게 사용할 수 있게 도와준다.



# Spring Data JPA 프로젝트 생성

#### 1. 프로젝트 생성

Spring Starter Project로 프로젝트를 생성한다. 

<img src="Images/JPA/spring-starter-project.png" style="zoom:80%;" />

#### 2. New Spring Starter Project Dependencies

Spring Data JPA를 선택한다. Entity 클래스 작성 편의를 위해 Lombok도 추가한다.

<img src="Images/JPA/new-spring-starter-project-dependencies.png" style="zoom:80%;" />

#### 3. Finish 버튼 클릭

Finish 버튼을 클릭하면 Progress가 활성화되면서 관련 라이브러리를 내려받는다.



# Altibase Dialect 클래스 파일 추가

Spring Data JPA는 기본 JPA 구현 공급자로 하이버네이트(Hibernate)를 사용한다. 하이버네이트는 Altibase를 위한 Dialect 클래스를 제공하지 않으므로 사용자가 직접 컴파일하여 hibernate-core 라이브러리에 추가해야 한다.

#### 1. Altibase Dialect Java 소스 다운로드

Hibernate 버전에 해당하는 [Altibase Dialect Java 소스](https://github.com/ALTIBASE/hibernate-orm/blob/master/ALTIBASE_DIALECT_PORTING.md#altibasedialectjava-compile)를 내려받는다.

#### 2. hibernate-core 라이브러리 파일 위치 확인

hibernate-core 라이브러리 파일 위치를 확인한다.

- maven 프로젝트 : *user_home_directory*/.m2/repository 에 위치

  ```
  $ user_home_directory/.m2/repository/org/hibernate/hibernate-core/x.x.x.Final/hibernate-core-x.x.x.Final.jar
  ```

- gradle 프로젝트 : *user_home_directory*/.gradle/caches/modules-2/files-2.1 에 위치

  ```
  $ user_home_directory/.gradle/caches/modules-2/files-2.1/org.hibernate/x.x.x-Final/라이브러리_파일_해쉬_값/hibernate-core-x.x.x.Final.jar
  ```

#### 3. hibernate-core-x.x.x.Final.jar 압축 해제

Altibase Dialect Java 소스가 있는 디렉터리에서 hibernate-core-x.x.x.Final.jar 파일의 압축을 해제한다.

#### 4. Altibase Dialect 컴파일

Altibase Dialect 파일들을 다음 순서로 컴파일한다.

```
javac -d . -cp . SequenceInformationExtractorAltibaseDatabaseImpl.java
javac -d . -cp . AltibaseLimitHandler.java
javac -d . -cp . AltibaseDialect.java
```

### 5. 클래스 파일 생성 확인

컴파일이 완료되면 현재 디렉터리 아래에 다음과 같은 클래스 파일이 생성된다.

```
./org/hibernate/tool/schema/extract/internal/SequenceInformationExtractorAltibaseDatabaseImpl.class
./org/hibernate/dialect/pagination/AltibaseLimitHandler.class
./org/hibernate/dialect/AltibaseDialect.class
```

#### 6. Altibase Dialet Java 소스(*.java) 삭제

Altibase Dialet Java 소스(*.java)가 jar 파일에 포함되지 않도록 삭제하거나 다른 디렉터리로 이동한다.

#### 7. hibernate-core-x.x.x.Final.jar 파일 생성

hibernate-core-x.x.x.Final.jar 파일을 다시 생성한다.

```
jar -cvfm hibernate-core-x.x.x.Final.jar META-INF/MANIFEST.MF .
```

#### 8. hibernate-core-x.x.x.Final.jar 파일 복사

생성한 JAR 파일을 2번에서 확인한 라이브러리 위치에 복사한다.



# Altibase 연동 확인

샘플 소스를 작성하여 Altibase와의 연동 여부를 확인한다.

#### Altibase JDBC 드라이버 파일 추가

STS 메뉴에서 Project -> Properties -> Java Build Path -> Libraries -> Add External JARs 를 클릭하여 Altibase JDBC 드라이버 파일을 추가한다.

![](Images/JPA/add-jdbc-driver.png)

#### application.properties 설정

src/main/resources/application.properties 파일에 아래 내용을 추가한다.

![](Images/JPA/application.properties.png)

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

#### Entity 클래스 작성

아래와 같이 Entity 클래스를 작성한다.

![](Images/JPA/sample-source.png)

#### Start 버튼 클릭

Boot Dashboard에서 해당하는 프로젝트를 선택하고 상단의 Start 버튼을 클릭한다.

![](Images/JPA/boot-dashboard-2.png)

![](Images/JPA/boot-dashboard.png)

#### 프로젝트 수행 결과 확인

Console 창에서 프로젝트 수행 결과를 확인한다.  

![](Images/JPA/console-result.png)



#### 테이블 생성 확인

iSQL로 Altibase 서버에 접속하여 테이블의 생성 여부를 확인한다.

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
