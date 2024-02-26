# Spring Data JPA with Hibernate 6.4 User's Guide for Altibase

<br/>

<br/>



# 목차

- [개요](#개요)
- [스프링 부트를 이용한 Altibase 연동](#스프링-부트를-이용한-Altibase-연동)
- [예제](#예제)

<br/>

# 개요

Hibernate 6.4가 포함된 Spring Data JPA와 스프링 부트(Spring Boot)를 이용하여 Altibase 서버와 연동하는 방법을 설명한다. 

이 문서는 아래 버전을 기준으로 작성되었다.

- Spring Boot 3.2.2
- Spring Data JPA 3.2.2
- Java 17
- Altibase 서버 7.1.0.9.3 이상
- Altibase JDBC 드라이버 7.1.0.9.0 이상 

<br/>

# 스프링 부트를 이용한 Altibase 연동

(1안)Hibernate 6.4 부터 AltibaseDialect가 hibernate-community-dialect에 포함되기 때문에, 좀 더 간결한 방법으로 Altibase 서버와 연동할 수 있게 되었다.

(2안)Hibernate 6.4 부터 AltibaseDialect가 hibernate-community-dialect에 포함되기 때문에, 스프링부트 3.2.2 이상을 이용하면 간단하게 pom.xml에 의존성만 추가하면 Altibase 서버와 연동할 수 있다.

## 1. Spring initializr를 통한 스프링 부트 프로젝트 생성

https://start.spring.io/ 에 접속한 다음, 아래와 같이 입력 후 Generate를 선택하여 프로젝트를 생성한다. Dependencies 에서 "ADD DEPENDENCIES..."를 클릭하여 "Spring Web", "Spring Data JPA" 를 추가한다. 예제 코드의 작성 편의를 위해 "Lombok"도 추가한다.

<img src="Images/JPA/spring_initializr.png"/>

## 2. pom.xml에 의존성 추가

### AltibaseDialect 의존성 추가

Hibernate 6.4 부터 AltibaseDialect가 hibernate-community-dialect에 포함되기 때문에, 버전 6.4 이상의 "hibernate-community-dialect" 의존성을 추가한다. (Hibernate 6.4 이전에는 직접 Altibase Dialect를 컴파일하여 추가하는 작업이 필요하였으나, 이제는 필요없다.)

```xml
<dependency>
    <groupId>org.hibernate.orm</groupId>
    <artifactId>hibernate-community-dialects</artifactId>
    <version>6.4.1.Final</version>
</dependency>
```

### Altibase JDBC 드라이버 의존성 추가

Altibase 7.1.0.9.0 및 Altibase 7.3.0.0.2부터  [Maven Central Repository](https://mvnrepository.com/artifact/com.altibase/altibase-jdbc)에서 Altibase JDBC 드라이버를 다운로드할 수 있어서, 아래와 같이 의존성을 추가하면 된다.

* Altibase 7.3 의 의존성 추가 예시

  ```xml
  <dependency>
      <groupId>com.altibase</groupId>
      <artifactId>altibase-jdbc</artifactId>
      <version>7.3.0.0.2</version>
  </dependency>
  ```

* Altibase 7.1의 의존성 추가 예시

  ```xml
  <dependency>
      <groupId>com.altibase</groupId>
      <artifactId>altibase-jdbc</artifactId>
      <version>7.1.0.9.2</version>
  </dependency>
  ```

### pom.xml sample

## 3. application.properties 설정

### Altibase JDBC 드라이버 설정

```java
# Database
spring.datasource.driver-class-name=Altibase.jdbc.driver.AltibaseDriver
spring.datasource.url=jdbc:Altibase://localhost:20300/mydb
spring.datasource.username=sys
spring.datasource.password=manager

# JPA
spring.jpa.properties.hibernate.jdbc.lob.non_contextual_creation=true
```

> [!NOTE]
>
> **Connection.createNClob SQLFeatureNotSupportedException** 
>
> Hibernate가 구동될 때 Connection.createNClob()을 호출하여 NClob 타입을 지원하는지 확인하는 과정에서 java.sql.SQLFeatureNotSupportedException 에러가 발생할 수 있다. Altibase 는 NClob 타입을 지원하지 않기 때문에 발생하며, 이 에러 메시지는 무시해도 된다. 해당 에러메시지를 제거하려면 application.properties에 다음의 설정을 추가하면 된다.
>
> ```
> spring.jpa.properties.hibernate.jdbc.lob.non_contextual_creation=true
> ```

#### Altibase JDBC 드라이버 연결 속성

Altibase 7.1 JDBC 드라이버를 이용하는 경우, 아래와 같이 연결속성을 추가해야 한다. Altibase 7.3 JDBC 드라이버는 이 작업을 수행하지 않아도 된다.

```java
jdbc:Altibase://127.0.0.1:20300/mydb?lob_null_select=false
```

## 4. 어플리케이션 코드 작성 

아래는 스프링 부트 어플리케이션의 예제이다.

```java
package com.example.AltitestJPA;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class AltitestJpaApplication {

	public static void main(String[] args) {
		SpringApplication.run(AltitestJpaApplication.class, args);
	}
}
```

## 5. Altibase 서버 연결 확인

maven을 이용하여 어플리케이션을 빌드하고 수행하면, 콘솔에 아래와 같이 "Added connection Altibase.jdbc.driver.AltibaseConnection" 를 확인하여  Altibase 서버와 연결되었음을 알 수 있다.

```java
... 
2024-02-23T16:33:03.171+09:00  INFO 48644 --- [           main] o.hibernate.jpa.internal.util.LogHelper  : HHH000204: Processing PersistenceUnitInfo [name: default]
2024-02-23T16:33:03.252+09:00  INFO 48644 --- [           main] org.hibernate.Version                    : HHH000412: Hibernate ORM core version 6.4.1.Final
2024-02-23T16:33:03.294+09:00  INFO 48644 --- [           main] o.h.c.internal.RegionFactoryInitiator    : HHH000026: Second-level cache disabled
2024-02-23T16:33:03.582+09:00  INFO 48644 --- [           main] o.s.o.j.p.SpringPersistenceUnitInfo      : No LoadTimeWeaver setup: ignoring JPA class transformer
2024-02-23T16:33:03.614+09:00  INFO 48644 --- [           main] com.zaxxer.hikari.HikariDataSource       : HikariPool-1 - Starting...
2024-02-23T16:33:03.706+09:00  INFO 48644 --- [           main] com.zaxxer.hikari.pool.HikariPool        : HikariPool-1 - Added connection Altibase.jdbc.driver.AltibaseConnection@2a99ca99
2024-02-23T16:33:03.708+09:00  INFO 48644 --- [           main] com.zaxxer.hikari.HikariDataSource       : HikariPool-1 - Start completed.
... 이하 생략
```

만약 Altibase 서버에 접속이 실패할 경우, 아래의 로그를 확인할 수 있다.

```java
...
2024-02-23T16:37:14.839+09:00  INFO 73180 --- [           main] com.zaxxer.hikari.HikariDataSource       : HikariPool-1 - Starting...
2024-02-23T16:37:17.966+09:00 ERROR 73180 --- [           main] com.zaxxer.hikari.pool.HikariPool        : HikariPool-1 - Exception during pool initialization.

java.sql.SQLException: Communication link failure: Connection refused: no further information
	at Altibase.jdbc.driver.ex.Error.throwCommunicationErrorException(Error.java:278) ~[altibase-jdbc-7.3.0.0.2.jar:na]
	at Altibase.jdbc.driver.cm.CmTcpSocket.open(CmTcpSocket.java:53) ~[altibase-jdbc-7.3.0.0.2.jar:na]
	at Altibase.jdbc.driver.cm.CmChannel.open(CmChannel.java:535) ~[altibase-jdbc-7.3.0.0.2.jar:na]
	at Altibase.jdbc.driver.cm.CmChannel.open(CmChannel.java:456) ~[altibase-jdbc-7.3.0.0.2.jar:na]
	at Altibase.jdbc.driver.AltibaseConnection.<init>(AltibaseConnection.java:132) ~[altibase-jdbc-7.3.0.0.2.jar:na]
	at Altibase.jdbc.driver.AltibaseDriver.createConnection(AltibaseDriver.java:70) ~[altibase-jdbc-7.3.0.0.2.jar:na]
	at Altibase.jdbc.driver.AltibaseDriver.connect(AltibaseDriver.java:65) ~[altibase-jdbc-7.3.0.0.2.jar:na]
	at com.zaxxer.hikari.util.DriverDataSource.getConnection(DriverDataSource.java:138) ~[HikariCP-5.0.1.jar:na]
	at com.zaxxer.hikari.pool.PoolBase.newConnection(PoolBase.java:359) ~[HikariCP-5.0.1.jar:na]
	at com.zaxxer.hikari.pool.PoolBase.newPoolEntry(PoolBase.java:201) ~[HikariCP-5.0.1.jar:na]
	at com.zaxxer.hikari.pool.HikariPool.createPoolEntry(HikariPool.java:470) ~[HikariCP-5.0.1.jar:na]
	at com.zaxxer.hikari.pool.HikariPool.checkFailFast(HikariPool.java:561) ~[HikariCP-5.0.1.jar:na]
	at com.zaxxer.hikari.pool.HikariPool.<init>(HikariPool.java:100) ~[HikariCP-5.0.1.jar:na]
	at com.zaxxer.hikari.HikariDataSource.getConnection(HikariDataSource.java:112) ~[HikariCP-5.0.1.jar:na]
	at org.hibernate.engine.jdbc.connections.internal.DatasourceConnectionProviderImpl.getConnection(DatasourceConnectionProviderImpl.java:122) ~[hibernate-core-6.4.1.Final.jar:6.4.1.Final]
	at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator$ConnectionProviderJdbcConnectionAccess.obtainConnection(JdbcEnvironmentInitiator.java:428) ~[hibernate-core-6.4.1.Final.jar:6.4.1.Final]
	at org.hibernate.resource.transaction.backend.jdbc.internal.JdbcIsolationDelegate.delegateWork(JdbcIsolationDelegate.java:61) ~[hibernate-core-6.4.1.Final.jar:6.4.1.Final]
	at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.getJdbcEnvironmentUsingJdbcMetadata(JdbcEnvironmentInitiator.java:276) ~[hibernate-core-6.4.1.Final.jar:6.4.1.Final]
	at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.initiateService(JdbcEnvironmentInitiator.java:107) ~[hibernate-core-6.4.1.Final.jar:6.4.1.Final]
	at org.hibernate.engine.jdbc.env.internal.JdbcEnvironmentInitiator.initiateService(JdbcEnvironmentInitiator.java:68) ~[hibernate-core-6.4.1.Final.jar:6.4.1.Final]
	at org.hibernate.boot.registry.internal.StandardServiceRegistryImpl.initiateService(StandardServiceRegistryImpl.java:129) ~[hibernate-core-6.4.1.Final.jar:6.4.1.Final]
	at org.hibernate.service.internal.AbstractServiceRegistryImpl.createService(AbstractServiceRegistryImpl.java:263) ~[hibernate-core-6.4.1.Final.jar:6.4.1.Final]
	at org.hibernate.service.internal.AbstractServiceRegistryImpl.initializeService(AbstractServiceRegistryImpl.java:238) ~[hibernate-core-6.4.1.Final.jar:6.4.1.Final]
	at org.hibernate.service.internal.AbstractServiceRegistryImpl.getService(AbstractServiceRegistryImpl.java:215) ~[hibernate-core-6.4.1.Final.jar:6.4.1.Final]
	at org.hibernate.boot.model.relational.Database.<init>(Database.java:45) ~[hibernate-core-6.4.1.Final.jar:6.4.1.Final]
	at org.hibernate.boot.internal.InFlightMetadataCollectorImpl.getDatabase(InFlightMetadataCollectorImpl.java:223) ~[hibernate-core-6.4.1.Final.jar:6.4.1.Final]
	at org.hibernate.boot.internal.InFlightMetadataCollectorImpl.<init>(InFlightMetadataCollectorImpl.java:191) ~[hibernate-core-6.4.1.Final.jar:6.4.1.Final]
	at org.hibernate.boot.model.process.spi.MetadataBuildingProcess.complete(MetadataBuildingProcess.java:170) ~[hibernate-core-6.4.1.Final.jar:6.4.1.Final]
	at org.hibernate.jpa.boot.internal.EntityManagerFactoryBuilderImpl.metadata(EntityManagerFactoryBuilderImpl.java:1432) ~[hibernate-core-6.4.1.Final.jar:6.4.1.Final]
	at org.hibernate.jpa.boot.internal.EntityManagerFactoryBuilderImpl.build(EntityManagerFactoryBuilderImpl.java:1503) ~[hibernate-core-6.4.1.Final.jar:6.4.1.Final]
	at org.springframework.orm.jpa.vendor.SpringHibernateJpaPersistenceProvider.createContainerEntityManagerFactory(SpringHibernateJpaPersistenceProvider.java:75) ~[spring-orm-6.1.3.jar:6.1.3]
	at org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean.createNativeEntityManagerFactory(LocalContainerEntityManagerFactoryBean.java:376) ~[spring-orm-6.1.3.jar:6.1.3]
	at org.springframework.orm.jpa.AbstractEntityManagerFactoryBean.buildNativeEntityManagerFactory(AbstractEntityManagerFactoryBean.java:409) ~[spring-orm-6.1.3.jar:6.1.3]
	at org.springframework.orm.jpa.AbstractEntityManagerFactoryBean.afterPropertiesSet(AbstractEntityManagerFactoryBean.java:396) ~[spring-orm-6.1.3.jar:6.1.3]
	at org.springframework.orm.jpa.LocalContainerEntityManagerFactoryBean.afterPropertiesSet(LocalContainerEntityManagerFactoryBean.java:352) ~[spring-orm-6.1.3.jar:6.1.3]
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.invokeInitMethods(AbstractAutowireCapableBeanFactory.java:1820) ~[spring-beans-6.1.3.jar:6.1.3]
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.initializeBean(AbstractAutowireCapableBeanFactory.java:1769) ~[spring-beans-6.1.3.jar:6.1.3]
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:599) ~[spring-beans-6.1.3.jar:6.1.3]
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:521) ~[spring-beans-6.1.3.jar:6.1.3]
	at org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:325) ~[spring-beans-6.1.3.jar:6.1.3]
	at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:234) ~[spring-beans-6.1.3.jar:6.1.3]
	at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:323) ~[spring-beans-6.1.3.jar:6.1.3]
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:199) ~[spring-beans-6.1.3.jar:6.1.3]
	at org.springframework.context.support.AbstractApplicationContext.getBean(AbstractApplicationContext.java:1231) ~[spring-context-6.1.3.jar:6.1.3]
	at org.springframework.context.support.AbstractApplicationContext.finishBeanFactoryInitialization(AbstractApplicationContext.java:949) ~[spring-context-6.1.3.jar:6.1.3]
	at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:624) ~[spring-context-6.1.3.jar:6.1.3]
	at org.springframework.boot.web.servlet.context.ServletWebServerApplicationContext.refresh(ServletWebServerApplicationContext.java:146) ~[spring-boot-3.2.2.jar:3.2.2]
	at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:754) ~[spring-boot-3.2.2.jar:3.2.2]
	at org.springframework.boot.SpringApplication.refreshContext(SpringApplication.java:456) ~[spring-boot-3.2.2.jar:3.2.2]
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:334) ~[spring-boot-3.2.2.jar:3.2.2]
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1354) ~[spring-boot-3.2.2.jar:3.2.2]
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1343) ~[spring-boot-3.2.2.jar:3.2.2]
	at com.example.AltitestJPA.AltitestJpaApplication.main(AltitestJpaApplication.java:10) ~[classes/:na]
Caused by: java.net.ConnectException: Connection refused: no further information
	at java.base/sun.nio.ch.Net.pollConnect(Native Method) ~[na:na]
	at java.base/sun.nio.ch.Net.pollConnectNow(Net.java:672) ~[na:na]
	at java.base/sun.nio.ch.NioSocketImpl.timedFinishConnect(NioSocketImpl.java:554) ~[na:na]
	at java.base/sun.nio.ch.NioSocketImpl.connect(NioSocketImpl.java:602) ~[na:na]
	at java.base/java.net.SocksSocketImpl.connect(SocksSocketImpl.java:327) ~[na:na]
	at java.base/java.net.Socket.connect(Socket.java:633) ~[na:na]
	at Altibase.jdbc.driver.cm.CmTcpSocket.connectTcpSocket(CmTcpSocket.java:75) ~[altibase-jdbc-7.3.0.0.2.jar:na]
	at Altibase.jdbc.driver.cm.CmTcpSocket.open(CmTcpSocket.java:47) ~[altibase-jdbc-7.3.0.0.2.jar:na]
	... 51 common frames omitted
... 이하 생략
```



# 예제

간단한 예제를 위해 com.example.AltitestJPA 패키지 아래에 테스트용 Book.java 엔티티 클래스를 생성한 후, 어플리케이션을 구동하여 테이블이 자동으로 생성되는지 확인해본다.

### Entity 클래스 생성

```java
//Book.java
package com.example.AltitestJPA;

import jakarta.persistence.Entity;
import jakarta.persistence.GeneratedValue;
import jakarta.persistence.GenerationType;
import jakarta.persistence.Id;
import lombok.Getter;
import lombok.NoArgsConstructor;
import lombok.Setter;

@Entity
@Getter @Setter @NoArgsConstructor
public class Book {
    @Id
    @GeneratedValue(strategy = GenerationType.SEQUENCE)
    private Integer id;
    private String title;
    private String author;

}
```

### application.properties 설정

JPA 예제 테스트를 위해 아래와 같이 설정한다.

```java
# Altibase DB
spring.datasource.driver-class-name=Altibase.jdbc.driver.AltibaseDriver
spring.datasource.url=jdbc:Altibase://localhost:20300/mydb  
spring.datasource.username=sys
spring.datasource.password=manager


# JPA/Hibernate
spring.jpa.properties.hibernate.jdbc.lob.non_contextual_creation=true
spring.jpa.hibernate.ddl-auto=create                            
spring.jpa.show-sql=true
```

### 테이블 생성 확인

* 콘솔

콘솔에서 아래와 같이 테이블 생성 쿼리가 수행된 것을 확인할 수 있다.

```java
...
Hibernate: drop table book cascade constraints
Hibernate: drop sequence book_seq
Hibernate: create sequence book_seq start with 1 increment by 50
Hibernate: create table book (id integer not null, author varchar(255), title varchar(255), primary key (id))
...이하 생략
```

* iSQL에서 확인

iSQL로 Altibase 서버에 접속하여 테이블의 생성 여부를 확인한다.

```sql
iSQL> desc book;
[ TABLESPACE : SYS_TBS_MEM_DATA ]
[ ATTRIBUTE ]
------------------------------------------------------------------------------
NAME                                     TYPE                        IS NULL
------------------------------------------------------------------------------
ID                                       INTEGER         FIXED       NOT NULL
AUTHOR                                   VARCHAR(255)    VARIABLE
TITLE                                    VARCHAR(255)    VARIABLE
[ INDEX ]
------------------------------------------------------------------------------
NAME                                     TYPE     IS UNIQUE     COLUMN
------------------------------------------------------------------------------
__SYS_IDX_ID_143                         BTREE    UNIQUE        ID ASC
[ PRIMARY KEY ]
------------------------------------------------------------------------------
ID
```

