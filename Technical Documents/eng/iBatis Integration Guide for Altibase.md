<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [iBatis Integration Guide for Altibase](#ibatis-integration-guide-for-altibase)
  - [1.iBatis Overview](#1ibatis-overview)
    - [What is iBATIS?](#what-is-ibatis)
    - [iBATIS Download](#ibatis-download)
  - [2.Sample Preparation using iBATIS](#2sample-preparation-using-ibatis)
    - [Creating SqlMap File](#creating-sqlmap-file)
    - [Creating SqlMapConfig File](#creating-sqlmapconfig-file)
    - [Creating SqlMapConfig file - iBatis.Net Integration](#creating-sqlmapconfig-file---ibatisnet-integration)
    - [Creating Application](#creating-application)
  - [3.Altibase Integration](#3altibase-integration)
    - [How to Get ALTIBASE JDBC Driver](#how-to-get-altibase-jdbc-driver)
    - [How to Set Up in JDBC Driver](#how-to-set-up-in-jdbc-driver)
    - [Setting up dataSource in SqlMapConfig file to link with ALTIBASE](#setting-up-datasource-in-sqlmapconfig-file-to-link-with-altibase)
    - [Connection Using FailOver](#connection-using-failover)
    - [Connecting ALTIBASE 5 and Previous Versions at the Same Time](#connecting-altibase-5-and-previous-versions-at-the-same-time)
    - [Calling Procedure/Function](#calling-procedurefunction)
  - [4.iBATIS, Spring, ALTIBASE Integration](#4ibatis-spring-altibase-integration)
    - [When Setting dataSource in Spring](#when-setting-datasource-in-spring)
    - [When Setting dataSource to iBATIS](#when-setting-datasource-to-ibatis)
    - [Using ALTIBASE's ConnectionPool](#using-altibases-connectionpool)
    - [Transaction Management](#transaction-management)
  - [5.Consideration when Integrating iBATIS](#5consideration-when-integrating-ibatis)
    - [LOB Data Processing](#lob-data-processing)
  - [Appendix](#appendix)
    - [Creating DB Tables and Sequences](#creating-db-tables-and-sequences)
    - [Creating Project](#creating-project)
    - [Creating SqlMap File](#creating-sqlmap-file-1)
    - [Creating SqlMapConfig File](#creating-sqlmapconfig-file-1)
    - [Creating Application](#creating-application-1)
    - [Adding Related JAR Files](#adding-related-jar-files)
    - [Running Application](#running-application)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# iBatis Integration Guide for Altibase

This document describes how to integrate with Altibase in iBatis environment and iBATIS + SPRING environment.

iBATIS 2.3.4, Spring Framework 2.5.6, Altibase version 5.3.3, and Eclipse were used as development IDE, and examples are provided separately for each chapter.

In addition to this document, the documents to be referenced during the development are as follows:

* Altibase Development Guide
* JAVA Development Guide
* JBOSS Integration Guide for Altibase
* TOMCAT Integration Guide for Altibase
* WEBSPHERE Integration Guide for Altibase
* WEBLOGIC Integration Guide for Altibase
* Spring Integration Guide for Altibase
* HIBERNATE Integration Guide for Altibase
* iBatis Integration Guide for Altibase



## 1.iBatis Overview

This section describes the concepts and features of iBATIS, and how to download and use it.

### What is iBATIS?

iBATIS is an ORM (Object Relational Mapping) framework that enables programmers to handle DB more conveniently, and helps to handle persistence logic by mapping the relationship between DB tables and JAVA objects. In other words, if iBATIS is used, CRUD (create, query, modify, delete) can be easily done in the DB by mapping DB tables and JavaBeans (SqlMap XML file).

In the way of programming using the existing JDBC, SQL statements were written in the program source, but using iBATIS, the SQL statements are separated from the program and written separately in the XML file. This reduces the burden of programmers programming when using existing JDBC. In addition, if the user wants to change the SQL, the SQL can be changed freely because the user only needs to change the SQL statement in the XML file rather than modifying the program as before.

The following figure shows how to communicate SQL written in xml (SqlMap.xml) in iBATIS with DB.

![img](http://aid.altibase.com/download/attachments/7340058/iBatis_overview.png?version=1&modificationDate=1416816827000&api=v2)

When the user writes each SQL statement for CRUD in SqlMap XML file and writes these files in SqlMapConfig XML file, it automatically creates mapped statements objects through iBATIS API and executes SQL statements in DB through it.

For more detailed architecture of iBATIS, please refer to the following site: [http://ibatis.apache.org]

### iBATIS Download

To use iBATIS, iBATIS related jar files are required. This jar file can be downloaded from http://ibatis.apache.or/java.cgi. When you unzip the downloaded file, a jar file exists in the lib directory inside the extracted directory. The user can use this jar file to link with iBATIS. If the iBATIS package is abates-2.3.4.726.zip, the abates-2.3.4.726.jar file is located in the lib directory of the extracted directory.

In the previous version of iBATIS, ibatis-comm.jar and ibatis-sqlmap.jar files were required, but in iBATIS version 2.3.4, the ibatis-comm.jar file and ibatis-sqlmap.jar file are abates-2.3.4.x.jar files. In this document, abates-2.3.4.726.jar was used.



## 2.Sample Preparation using iBATIS

To process SQL statements using iBATIS, SqlMapConfig XML file and SqlMap XML file must be created. These files allow programmers to easily map JavaBeans to PreparedStatement parameters and ResultsSets.

This section describes how to create SqlMapConfig XML file, SqlMap XML file, and how to actually process SQL using this file in application. For more information on writing the sample program, please refer to the appendix.

### Creating SqlMap File

SqlMap XML file is a file that specifies the SQL statements to be transferred to DB, mapping of parameters to be bound to PreparedStatement, and mappings of ResultSet.

The following is an example of writing SqlMap XML file that processes CRUD in person table (Person.xml).

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE sqlMap PUBLIC "-//iBATIS.com//DTD SQL Map 2.0//EN"
"http://www.ibatis.com/dtd/sql-mapconfig-2.dtd">
 
<sqlMap namespace="Person">
    <resultMap id="PersonResult" class="examples.domain.Person">
        <result property="id" column="per_id" />
        <result property="name" column="per_name" />
        <result property="birthDate" column="per_birth_date" />
        <result property="weightInKilograms" column="per_weight_kg" />
        <result property="heightInMeters" column="per_height_m" />
</resultMap>
 
<select id="getPerson" parameterClass="int" resultClass="examples.domain.Person">
        <![CDATA[
            SELECT
            PER_ID as id,
            PER_NAME as name,
            PER_BIRTH_DATE as birthDate,
            PER_WEIGHT_KG as weightInKilograms,
            PER_HEIGHT_M as heightInMeters
            FROM PERSON
            WHERE PER_ID = #value#
        ]]>
</select>
 
<insert id="insertPerson" parameterClass="examples.domain.Person">
        <![CDATA[
            INSERT INTO
            PERSON (PER_ID, PER_NAME, PER_BIRTH_DATE,
PER_WEIGHT_KG, PER_HEIGHT_M)
            VALUES (#id#, #name#, #birthDate#,
#weightInKilograms#, #heightInMeters#)
        ]]>
</insert>
 
<update id="updatePerson" parameterClass="examples.domain.Person">
        <![CDATA[
            UPDATE PERSON
            SET PER_NAME = #name#,
            PER_BIRTH_DATE = #birthDate#,
            PER_WEIGHT_KG = #weightInKilograms#,
            PER_HEIGHT_M = #heightInMeters#
            WHERE PER_ID = #id#
        ]]>
</update>
 
<delete id="deletePerson" parameterClass="int">
        <![CDATA[
            DELETE PERSON
            WHERE PER_ID = #id#
        ]]>
</delete>
 
<select id="getAllPersons"  resultMap="PersonResult">
        <![CDATA[
            SELECT * FROM person
        ]]>
</select>
</sqlMap>
```

After executing the SELECT statement in the <\resultMap> tag, define the Map object of the data to be stored in the ResultSet, and in the <\insert>, \<update>, \<delete>, and \<select> tags, define each SQL statement for CRUD operation. do.

For more information on each tag, refer to http://ibatis.apache.org or refer to the attached document iBATIS-SqlMaps-2-en.pdf.

### Creating SqlMapConfig File

SqlMapConfig file is a SQL Maps configuration file that writes dataSource for DB connection, path of SqlMap file, and other properties to control SqlMapClient.

The following is an example of the SqlMapConfig file (SqlMapConfigExample.xml).

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE sqlMapConfig PUBLIC "-//iBATIS.com//DTD SQL Map Config 2.0//EN"
"http://www.ibatis.com/dtd/sql-map-config-2.dtd">
 
<sqlMapConfig>
 
<properties resource="db.properties" />
     
<settings
cacheModelsEnabled="true"
enhancementEnabled="true"
lazyLoadingEnabled="true"
maxRequests="32"
maxSessions="10"
maxTransactions="5"
useStatementNamespaces="false"
/>
 
<transactionManager type="JDBC" >
    <dataSource type="SIMPLE">
       <property name="JDBC.Driver" value="${driver}"/>
       <property name="JDBC.ConnectionURL" value="${url}"/>
       <property name="JDBC.Username" value="${username}"/>
       <property name="JDBC.Password" value="${password}"/>
<property name="Pool.MaximumActiveConnections" value="10"/>
<property name="Pool.MaximumIdleConnections" value="5"/>
<property name="Pool.MaximumCheckoutTime" value="120000"/>
<property name="Pool.TimeToWait" value="500"/>
<property name="Pool.PingQuery" value="select 1 from dual"/>
<property name="Pool.PingEnabled" value="false"/>
<property name="Pool.PingConnectionsOlderThan" value="1"/>
<property name="Pool.PingConnectionsNotUsedFor" value="1"/>
</dataSource>
</transactionManager>
 
<sqlMap resource="Person.xml" />
     
</sqlMapConfig>
```

In the \<properties> tag, specify the path and name of the properties file in which properties defined in the form are written, in the \<settings> tag, write the properties to control the SqlMapClient, and in the \<transactionManager> and \<dataSource>, write the DB information to connect.
In addition, the \<SqlMap> tag writes the path and name of the previously created SqlMap files.

For more detailed information on each tag, refer to http://ibatis.apache.org or refer to the attached document iBATIS-SqlMaps-2-en.pdf.

### Creating SqlMapConfig file - iBatis.Net Integration

How to set up Altibase connection of SqlMap.config when connecting through ODBC is explained briefly.

First, the user needs to install the Altibase ODBC Driver and add the user DSN in the ODBC Data Source Administrator.

For how to install and configure ODBC, refer to the technical document 'Altibase Windows ODBC'

```
<!-- Database connection information -->
<database>
<provider name="Odbc2.0"/>
<dataSource name="Altibase" connectionString="DSN=Altibase5;USER ID=sys;PASSWORD=manager"/>
</database>
```

Among the various DBMS provides defined in providers.config, the provider to use when connecting to Altibase is Odbc2.0. Write Odbc2.0 in the <provider\> tag.

In the \<dataSource> tag, enter the DSN added by the ODBC data source manager in connectionString.

### Creating Application

CRUD operations can be processed by integrating with objects mapped to DB tables using SqlMapClient instance in the application.

In order to integrate with DB using iBATIS, the user must first obtain the SqlMapClient object through the SqlMapConfig file. Then, the user can connect to the DB by calling method corresponding to CRUD through the SqlMapClient object.

The following is an application that inserts, changes, deletes, and queries data in the person table of the DB.

Ex) SimpleConnection's PersonApp.java

```
…
String resource ="SqlMapConfigExample.xml";
Reader reader = Resources.getResourceAsReader(resource);
SqlMapClient sqlMap = SqlMapClientBuilder.buildSqlMapClient(reader);
         
//insert Person
Person newPerson1 = new Person();
…
sqlMap.insert ("insertPerson", newPerson1);
…  
     
//select all Persons
List<Person> list = (List<Person>)sqlMap.queryForList("getAllPersons");
…  
     
//update Person
sqlMap.update("updatePerson", newPerson1);
…
 
//get Person
Person person = (Person) sqlMap.queryForObject ("getPerson", personPk);
…
         
//delete Person
sqlMap.delete ("deletePerson", new Integer(1));
…
```

First, read the SqlMapConfig file to get the SqlMapClient object. (

String resource ="SqlMapConfigExample.xml";

Reader reader = Resources.getResourceAsReader(resource);

SqlMapClient sqlMap = SqlMapClientBuilder.buildSqlMapClient(reader);

)

Then, call each method of SqlMapClient class corresponding to CRUD. (

 sqlMap.insert(), sqlMap.queryForList(), sqlMap.queryForObject(),sqlMap.update(), sqlMap.delete()

)

For detailed description of each method, refer to http://ibatis.apache.org or refer to the attached document iBATIS-SqlMaps-2-en.pdf file.\



## 3.Altibase Integration

To connect Altibase in iBatis, the user can set the Altibase JDBC Driver and specify the dataSource for ALTIBASE in the SqlMapConfig file. This chapter section describes how to get the Altibase JDBC driver, how to set the JDBC Driver, and how to set the dataSource in SqlMapConfig. In addition, this section explains how to use the FailOver function, how to work with multiple versions of Altibase, and how to call the stored procedure/function.

### How to Get ALTIBASE JDBC Driver

The JDBC driver provided by ALTIBASE is Altibase.jar file. This file is located in the $ ALTIBASE_HOME / lib directory of the server where ALTIBASE is installed.

As of ALTIBASE 5, Altibase.jar and Altibase5.jar files exist in the \$ALTIBASE_HOME/lib directory. Altibase.jar is a generic JDBC driver file. JDBC driver file used when Therefore, when interlocking with one ALTIBASE DB or multiple ALTIBASEs with the same version, use the $ ALTIBASE_HOME / lib / Altibase.jar file.

It is necessary to check the ALTIBASE JDBC Driver version to verify that the ALTIBASE DB Server to be interlocked with the ALTIBASE JDBC Driver is compatible.

To check the ALTIBASE JDBC Driver version, execute the following command.

```
$ java –jar Altibase.jar
JDBC Driver Info :  Altibase Ver = 5.3.3.13 for JavaVM v1.4, CMP:5.6.1, $Revision: 14502 $ Jan 13 2010 14:35:28
```

At this time, if the cm protocol version of the ALTIBASE DB server and the CMP of the ALTIBASE JDBC Driver are the same, they are compatible.

```
$ altibase -v
version 5.3.3.13 XEON_LINUX_redhat_Enterprise_AS4-64bit-5.3.3.13-release-GCC3.4.6 
(xeon-redhat-linux-gnu) Jan 13 2010 14:35:30, binary db version 5.4.1, meta version 5.6.1, 
cm protocol version 5.6.1, replication protocol version 5.4.1
```

It is recommended that the user uses the ALTIBASE JDBC Driver file, which is the same as or higher than the version of ALTIBASE DB Server, because JDBC related bugs may have been fixed as the version was upgraded.

### How to Set Up in JDBC Driver

The downloaded JDBC driver, Altibase.jar, can be added to the class-agh or placed in an appropriate directory on the web server.

If the user is developing using Eclipse, the user can add the ALTIBASE JDBC Driver to the project as follows.

Project – JRE System Library [DOCKI: J2SE-1.5]-Properties – Installed JREs – Click jre among the items – Click Edit – Add External JARs to add Altibase.jar, ALTIBASE JDBC Driver.


![img](http://aid.altibase.com/download/attachments/7340078/eclipse_jdbc.png?version=1&modificationDate=1416818525000&api=v2)

![img](http://aid.altibase.com/download/attachments/7340078/eclipse_jdbc2.png?version=1&modificationDate=1416818549000&api=v2)

### Setting up dataSource in SqlMapConfig file to link with ALTIBASE

The user can connect to ALTIBASE by specifying the property for ALTIBASE in the \<transactionManager> tag of the SqlMapConfig file. At this time, the user can directly enter the property values in the SqlMapConfig file, or the user can create a separate properties file and load the property values written in this file for use.

The following is an example of defining properties for ALTIBASE in a properties file called db.properties, and reading these properties and using them in the SqlMapConfig file.

Ex) SimpleConnection db.properties file

```

driver=Altibase.jdbc.driver.AltibaseDriver
url=jdbc:Altibase://192.168.1.35:21129/mydb
username=sys
password=manager
```

The description of each value set in this file is as follows.

| Property | Description                                                  |
| -------- | ------------------------------------------------------------ |
| driver   | ALTIBASE JDBC driver class name                              |
| url      | Connection string information for connection with ALTIBASE<br />Enter "jdbc:Altibase://IP:port_no/db_name" |
| username | Database account                                             |
| password | Database password                                            |

Ex) SimpleConnection's SqlMapConfigExample.xml file

```
<sqlMapConfig>
<properties resource="db.properties" />
 
<transactionManager type="JDBC" >
<dataSource type="SIMPLE"> -- SIMPLE is the built-in transaction manager name
    <property name="JDBC.Driver" value="${driver}"/>
    <property name="JDBC.ConnectionURL" value="${url}"/>
    <property name="JDBC.Username" value="${username}"/>
    <property name="JDBC.Password" value="${password}"/>
</dataSource>
</transactionManager>
 
<sqlMap resource="Person.xml" />
     
</sqlMapConfig>
```

The driver, url, username, and password properties specified in db.properties are read and set in the JDBC.Driver, JDBC.ConnectionURL, JDBC.Username, and JDBC.password properties of the dataSource.

To execute the example SimpleConnection project above, Altibase.jar and ibatis-2.3.4.x.jar files are required.

![img](http://aid.altibase.com/download/attachments/7340078/eclipse_jdbc3.png?version=1&modificationDate=1416818723000&api=v2)

### Connection Using FailOver

FailOver is supported as of ALTIBASE 5.3.3. To use the FailOver function, the user can put FailOver-related properties in the part where the user writes the connection url of the dataSource.
The following is an example of connecting to ALTIBASE using FailOver. Connection url part is defined in db.properties file.

Ex) FailOverSample's db.properties file

```
driver=Altibase.jdbc.driver.AltibaseDriver
url=jdbc:Altibase://192.168.6.224:21129/mydb?
AlternateServers=(192.168.1.35:21129)&amp;
ConnectionRetryCount=1&amp;ConnectionRetryDelay=1&amp;
SessionFailOver=on&amp;LoadBalance=off
username=sys
password=manager
```

FailOver related properties that can be defined in the connection url specified in the above file are as follows.

| Property             | Description                                                  |
| -------------------- | ------------------------------------------------------------ |
| AlternateServer      | Indicates the available servers to be connected when a failure occurs (IP Address1:Port1, IP Address2:Port2,...) and describes them. |
| ConnectionRetryCount | If there is a failure to connect to the available server, the number of attempts to connect is repeated |
| ConnectionRetryDelay | Time to wait before attempting to connect again when the available server connection fails (in seconds) |
| LoadBalance          | If set to on, random selection is made including the default server and available servers when the first connection is attempted.<br />If set to off, it connects to the default server when it tries to connect for the first time, and if it fails, it connects to the server described by AlternateServer. |
| SessionFailOver      | Indicates whether to perform STF (Service Time Fail-Over).<br />on: STF, off: CTF<br />CTF(Connection Time Fail-Over) refer to recognizing a failure at the time of DBMS connection and retrying the connection to another normal Server.<br />STF(Service Time Fail-Over) means that it detects a failure duding service, reconnects to the DBMS of another available node, restores the properties of the session, and allows the user application to perform the business logic again. (STF performs Fail-Over only for DB access, and failed transactions must be reprocessed by the user.) |

In order to execute the above example FailOverSample project, Altibase.jar and ibatis-2.3.4.x.jar files are needed as in “Set dataSource in SqlMapConfig file to link with ALTIBASE”.

### Connecting ALTIBASE 5 and Previous Versions at the Same Time

Starting with ALTIBASE 5, the ALTIBASE 5 version-specific JDBC Driver (Altibase5.jar) is provided so that one application can connect to ALTIBASE 5 and ALTIBASE 4 or ALTIBASE 3 simultaneously. By using this driver, the user can access two versions of ALTIBASE between ALTIBASE 5-ALTIBASE 4, or ALTIBASE 5-ALTIBASE 3, ALTIBASE 5.1.5-ALTIBASE 5.3.3.

In order to distinguish it from the existing Altibase.jar, Altibase5.jar for ALTIBASE 5 is required separately. In addition, in the part that is specified in the dataSource, the JDBC Driver class name should also specify Altibase5.jdbc.driver.AltibaseDriver for ALTIBASE 5 instead of the existing Altibase.jdbc.driver.AltibaseDriver.

In order to integrate with other versions of ALTIBASE in iBATIS, you need to create a separate SqlMapConfig file for each version and read each SqlMapConfig file in the application.

Please note that in this case, the program should load Altibase5.jdbc.driver.AltibaseDriver first and then Altibase.jdbc.driver.AltibaseDriver.

The following is an example of loading the drivers of two versions of ALTIBASE using Altibase.jar and Altibase5.jar files.

Ex) db.properties1 file of MultiVersionConneciton

Settings for ALTIBASE 5 version

```
driver=Altibase5.jdbc.driver.AltibaseDriver
url=jdbc:Altibase://192.168.6.224:21129/mydb
username=sys
password=manager
```

Ex) db.properties2 file of MultiVersionConnection

Settings for ALTIBASE 5 and earlier

```
driver=Altibase.jdbc.driver.AltibaseDriver
url=jdbc:Altibase://192.168.1.35:21129/mydb
username=sys
password=manager
```

Ex) MultiVersionConneciton's SqlMapConfigExample1.xml file

Settings for ALTIBASE 5 version

```
<sqlMapConfig>
<properties resource="db.properties1" />
<transactionManager type="JDBC" >
   <dataSource type="SIMPLE">
      <property name="JDBC.Driver" value="${driver}"/>
      <property name="JDBC.ConnectionURL" value="${url}"/>
      <property name="JDBC.Username" value="${username}"/>
      <property name="JDBC.Password" value="${password}"/>
</dataSource>
</transactionManager>
<sqlMap resource="Person.xml" />
</sqlMapConfig>
```

Ex) MultiVersionConneciton's SqlMapConfigExample2.xml file

Setting for ALTIBASE 5 and earlier

```
<sqlMapConfig>
<properties resource="db.properties2" />
<transactionManager type="JDBC" >
   <dataSource type="SIMPLE">
      <property name="JDBC.Driver" value="${driver}"/>
      <property name="JDBC.ConnectionURL" value="${url}"/>
      <property name="JDBC.Username" value="${username}"/>
      <property name="JDBC.Password" value="${password}"/>
</dataSource>
</transactionManager>
<sqlMap resource="Person.xml" />
</sqlMapConfig>
```

Ex) PersonApp.java file of MultiVersionConnection

```
…  
String resource1 ="SqlMapConfigExample1.xml";
Reader reader1 = Resources.getResourceAsReader(resource1);
SqlMapClient sqlMap1 = SqlMapClientBuilder.buildSqlMapClient(reader1);
         
String resource2 ="SqlMapConfigExample2.xml";
Reader reader2 = Resources.getResourceAsReader(resource2);
SqlMapClient sqlMap2 = SqlMapClientBuilder.buildSqlMapClient(reader2);
…
```

In the PersonApp.java example above, to load Altibase5.jdbc.driver.AltibaseDriver before Altibase.jdbc.driver.AltibaseDriver, read the SqlMapConfigExample1.xml file using Altibase5.jdbc.driver.AltibaseDriver as JDBC.Driver first. have. The driver for ALTIBASE5 must be loaded first.

In order to execute the MultiVersionConnection project included in the example, not only the ibatis-2.3.4.x.jar file used previously, but also Altibase.jar and Altibase5.jar files are needed. These files exist in the lib directory of the directory where ALTIBASE is installed ($ ALTIBASE_HOME). The user can use the Altibase5.jar file of the ALTIBASE 5 version and the Altibase.jar file of the previous version.

![img](http://aid.altibase.com/download/attachments/7340078/eclipse_jdbc4.png?version=1&modificationDate=1416819145000&api=v2)

### Calling Procedure/Function

When calling the stored procedure/function created in DB in iBATIS, set the information on the parameter defined in the stored procedure / function in the SqlMap file, and in the <procedure> tag, call the procedure/function applied to CallableStatement applied to the tag. Just define it.

The following is an example of calling the stored procedure/function.

Ex) ProcedureSample Procedure/Function creation statement

```
CREATE OR REPLACE PROCEDURE sum_proc
(
    p_num1 IN NUMBER,
    p_num2 IN NUMBER,
    p_num3 OUT NUMBER
)
AS
BEGIN
    p_num3 := p_num1 + p_num2;
END;
/
 
CREATE OR REPLACE FUNCTION sum_func
(
    p_num1 IN NUMBER,
    p_num2 IN NUMBER
)
RETURN NUMBER
AS
    v_num NUMBER;
BEGIN
    v_num := p_num1 + p_num2;
    RETURN v_num;
END;
/
```

Ex) Procedure.xml(SqlMap) file of Procedure

```
<sqlMap namespace="Procedure">
   
  <parameterMap id="ProcedureParam" class="java.util.Map">
<parameter property="p_num1" jdbcType="NUMERIC"
javaType="int" mode="IN"  />
<parameter property="p_num2" jdbcType="NUMERIC"
javaType="int" mode="IN"  />
    <parameter property="p_num3" jdbcType="NUMERIC"
javaType="int" mode="OUT"/>
</parameterMap>
     
 
<parameterMap id="FunctionParam" class="java.util.Map">
     <parameter property="p_num3" jdbcType="NUMERIC"
javaType="int" mode="OUT"/>
<parameter property="p_num1" jdbcType="NUMERIC"
javaType="int" mode="IN" />
<parameter property="p_num2" jdbcType="NUMERIC"
javaType="int" mode="IN" />
</parameterMap>
     
<procedure id="sumProc" parameterMap="ProcedureParam" >
{call sum_proc(?,?,?)}
</procedure>
     
<procedure id="sumFunc" parameterMap="FunctionParam"  >
{call ? := sum_func(?,?)}
</procedure>
 
</sqlMap>
```

Define the type and IN / OUT settings for the parameters of the procedure/function in the \<paramaterMap> tag, and specify the id value of the \<paramaterMap> tag in the parameterMap attribute in the \<procedure> tag. Then, in the \<procedure> tag, write a statement that calls Procedure / Function.

To execute the ProcedureSample example, the Altibase.jar and ibatis-2.3.4.x.jar files are required, as in “Configuring a dataSource in the SqlMapConfig file to link with ALTIBASE”.

## 4.iBATIS, Spring, ALTIBASE Integration

To integrate with Altibase, the user can specify a dataSource in iBATIS or a dataSource in Spring. This chapter describes how to interface with ALTIBASE using these two methods.

### When Setting dataSource in Spring

In order to user iBATIS and Spring together, the user can specify iBATIS SqlMapClientFactoryBean in Spring's applicationContext.xml file. After that, if each DAO bean is set to refer to the SqlMapClientFactoryBean, methods corresponding to CRUD can be called using the SqlMapClient object from other beans.

To set the dataSource in Spring in an environment in which iBATIS and Spring are linked, select one of the methods described in the "ALTIBASE_Spring_Linking Guide" document, specify the dataSource in applicationContext.xml, and connect with iBATIS in the SqlMapClientFactoryBean bean of iBATIS.

At this time, specify the name of the SqlMapConfig file in the configLocation property of the SqlMapClientFactoryBean bean.

The following is an example of specifying dataSource and SqlMapClientFactoryBean in applicationContext.xml file.

Ex) ApplicationContext.xml file of SpringbatisConnection1

```
…
<!-- DriverManagerDataSource Data Source setting using classes -->
 <bean id="dataSource" class="org.springframework.jdbc.datasource.DriverManagerDataSource">
<!--  JDBC Driver class name setting -->
<property name="driverClassName" value="Altibase.jdbc.driver.AltibaseDriver"/>
<!-- connection url-->
   <property name="url" value="jdbc:Altibase://192.168.1.35:21129/mydb"/>
   <!-- DB User account setting -->
   <property name="username" value="sys"/>
   <!-- DB User password setting -->
   <property name="password" value="manager" />
</bean>
     
<bean id="sqlMapClient" class="org.springframework.orm.ibatis.SqlMapClientFactoryBean">
<property name="dataSource" ref="dataSource"/>
   <property name="configLocation" value="SqlMapConfigExample.xml"/>
</bean>  
 
<!-- Bean setting of DAO class -->
<bean id="personDao" class="examples.domain.PersonDao">
<property name="sqlMapClient" ref="sqlMapClient"/>
</bean>
…
```

Altibase.jar, ibatis-2.3.4.x.jar file and spring-jdbc.jar, spring-orm.jar, spring.jar, commons-logging.jar files are required to execute the above examples SpringIbatisConnection1 project. spring-jdbc.jar, spring-orm.jar, spring.jar, and commons-logging.jar files are files included in Spring Framework. For detailed directory location, refer to the document "*ALTIBASE Spring Linking Guide*".

![img](http://aid.altibase.com/download/attachments/7340080/eclipse_jdbc5.png?version=1&modificationDate=1416819407000&api=v2)

### When Setting dataSource to iBATIS

The method of setting up the data source for iBATIS in an environment connected to iBATIS and Spring is the same as described in the section "Configuring the data source in the SqlMapConfig file to interact with ALTIBASE" above. The user can specify ALTIBASE in \<Attributes for connecting to transactionManager> in SqlMapConfig file.

However, in order to integrate iBATIS in Spring, the SqlMapClientFactoryBean of iBATIS must be specified in the applicationContext.xml file as in the above "*When Setting the dataSource in Spring*".

The following is an example of integrating with ALTIBASE by setting the dataSource in iBATIS in the iBATIS and SPRING integrating environment.

Ex) ApplicationContext.xml file of SpringIbatisConnection2

```
…
<bean id="sqlMapClient" class="org.springframework.orm.ibatis.SqlMapClientFactoryBean">
<property name="configLocation" value="SqlMapConfigExample.xml"/>
</bean>  
 
<!-- Bean setting of DAO class -->
<bean id="personDao" class="examples.domain.PersonDao">
<property name="sqlMapClient" ref="sqlMapClient"/>
</bean>
 …
```

Ex) SqlMapConfigExample.xml file of SpringIbatisConnection2

```
<sqlMapConfig>
<properties resource="db.properties" />
<transactionManager type="JDBC" >
<dataSource type="SIMPLE">
<property name="JDBC.Driver" value="${driver}"/>
     <property name="JDBC.ConnectionURL" value="${url}"/>
     <property name="JDBC.Username" value="${username}"/>
     <property name="JDBC.Password" value="${password}"/
</dataSource>
</transactionManager>
 
<sqlMap resource="Person.xml" />
     
</sqlMapConfig>
```

In the example above, we can see that the dataSource is set in SqlMapConfigExample.xml, and the SqlMapClientFactoryBean is set in the applicationContext.xml file by reading this SqlMapConfigExample.xml file.

To run SpringIbatisConnection2 example, Altibase.jar, ibatis-2.3.4.x.jar file and spring-orm.jar, spring.jar, and commons-logging.jar files are required. The spring-orm.jar, spring.jar, and commons-logging.jar files are files included in the Spring Framework. For detailed directory location, refer to the document "*ALTIBASE Spring Linking Guide*".

![img](http://aid.altibase.com/download/attachments/7340080/eclipse_jdbc5.png?version=1&modificationDate=1416819407000&api=v2)

### Using ALTIBASE's ConnectionPool

The user can user ALTIBASE ConnectionPool by using the ABConnectionPoolDataSource class provided by ALTIBASE. In iBATIS and Spring integrating environment, the user can define dataSource bean by using ABConnectionPoolDataSource class in Spring's applicationContext.xml file.

It should be noted that there is no way to used ALTIBASE ConnectionPool only in iBATIS without integrating with Spring. For more detailed information, please refer to the document "ALTIBASE Spring Linking Guide".

Ex) AltibaseConnection Pool's applicationContext.xml file attached to "*Altibase Spring Linking Guide*"

```
…
<bean id="dataSource"
class="Altibase.jdbc.driver.AltibaseConnectionPoolDataSource">
<       <!-- connection url-->
          <property name="url" value="jdbc:Altibase://192.168.1.35:21129/mydb"/>
  <!-- DB User account setting -->
  <property name="user" value="sys"/>
  <!-- DB User password setting -->
<property name="password" value="manager" />
</bean>
…
```

### Transaction Management

When linking with DB in iBATIS, if dataSource is specified in \<transactionManager> of SqlMapConfig file, setAutoCommit (false) automatically when each CRUD method defined in SqlMap file is called; is called. After that, when the method is terminated, the transaction is committed and the mode is changed back to the default autocommit mode.

This also allows programmers to explicitly manage transactions in the application.

If iBATIS and Spring are integrated, transactions can be managed in Spring as well.

This chapter introduces these transaction management methods.

#### Transaction Management in iBATIS

When linking with DB in iBATIS, if dataSource is specified in \<transactionManager> of SqlMapConfig file, setAutoCommit (false) automatically when each CRUD method defined in SqlMap file is called; is called. After that, when the method is terminated, the transaction is committed and the mode is changed back to the default autocommit mode.

In addition, the programmer can manage transactions directly in the application.

At this time, to start a transaction, call startTransaction () method of SqlMapClient, commitTransaction () method to commit, or endTransaction () method to rollback without commit.

The following is an example of explicitly processing a transaction in an application.

Ex) PersonS.java file of TransactionSample

```
…
SqlMapClient sqlMap = SqlMapClientBuilder.buildSqlMapClient(reader);
 
//start transaction
sqlMap.startTransaction();
 
//insert Person
Person newPerson1 = new Person();
…
sqlMap.insert ("insertPerson", newPerson1);
 
//commit
sqlMap.commitTransaction ();
                 
Person newPerson2 = new Person();
…
sqlMap.insert ("insertPerson", newPerson2);
 
// selected 2 rows.
List<Person> list = (List<Person>)sqlMap.queryForList("getAllPersons");
System.out.println("Selected "+list.size()+" records.");
for(int i=0; i< list.size();i++){
System.out.println(list.get(i));
}
         
//rollback
sqlMap.endTransaction();
 
// selected only 1 row.
list = (List<Person>)sqlMap.queryForList("getAllPersons");
System.out.println("Selected "+list.size()+" records.");
for(int i=0; i< list.size();i++){
System.out.println(list.get(i));
}
…
```

In order to execute the above example TransactionSample project, Altibase.jar and abates-2.3.4x.jar files are needed as in "Set dataSource in SqlMapConfig file to link with ALTIBASE".

#### Transaction Management in Spring

If iBATIS and Spring are connected, transactions can be managed in Spring. This document includes an example (LobSpringIbatisSample) for managing/processing transactions declaratively in Spring's applicationContext.xml file. For more detailed information, refer to the document *"ALTIBASE Spring Linking Guide"*.

## 5.Consideration when Integrating iBATIS

### LOB Data Processing

In order to process LOB in iBATIS, jdbcType must be specified as CLOB/BLOB in the part of setting the information about parameter and result in SqlMap file.

Otherwise, incorrect data can be entered or an incorrect data can be queried by the length limit. Or, an error such as invalid length may occur.

Therefore, mapping for parameter and result must be designated as CLOB/BLOB

The following is an example of setting parameterMap and resultMap for CLOB type data.

Ex) LobSample's LobSample.xml (SqlMap) file

```
<sqlMap namespace="LobSample">
   <resultMap id="LobSampleResult" class="com.altibase.lob.LobSample">
    <result property="lob_id" column="lob_id" />
     <result property="lobcolumn" column="lobcolumn"
jdbcType="CLOB" javaType="java.lang.String" />
</resultMap>
   
   <parameterMap id="LobSampleParam" class="com.altibase.lob.LobSample">
    <parameter property="lob_id" />
    <parameter property="lobcolumn"
jdbcType="CLOB" javaType="java.lang.String" />
</parameterMap>
     
<select id="getLobSample" parameterClass="int" resultMap="LobSampleResult">
        SELECT lob_id, lobcolumn
        FROM lobsample
        WHERE lob_id = #value#
</select>
     
<insert id="insertLobSample" parameterMap="LobSampleParam">
        INSERT INTO lobsample (lob_id,lobcolumn)
        VALUES (?,?)
</insert>
         
    …
</sqlMap>
```

In addition, the important thing to be careful when processing LOB is that in order to process LOB data in ALTIBASE, the transaction must be managed after changing the autocommit mode to false. When setting dataSource in \<transactionManager> of SqlMapConfig file when integrating iBATIS, setAutoCommit(false); There is no consideration when processing LOB because the autocommit mode is changed to false by calling the method. However, if iBATIS and Spring are integrated together, if the user manages transactions in Spring, the user must specify TransactionManager bean to process LOB.

In addition, in the case of declarative transaction processing in Spring, propagation must be specified as one of PROPAGATION_REQUIRED, PROPAGATION_REQUIRES_NEW, and PROPAGATION_NESTED.

If TransactionManager is not specified or propagation is set to a value other than the above described when using declarative transaction, a null value is returned when querying LOB data, or "java.sql.SQLException: [DOCKI: 0]: An error such as LobLocator can not span the transaction 101858625" occurs.

In addition, when entering LOB data, "java", "java.sql.SQLException: [DOCKI: 0]: An error such as LobLocator can not span the transaction 101858625" occurs.

The following example is an example of processing LOB data by declaratively processing a transaction in Spring's applicationContext.xml.

For more detailed information on how to process transaction declaratively, please refer to the document *"ALTIBASE Spring Linking Guide".*

Ex) LobSpringIbatisSample's applicationContext.xml file

```
…
<bean id="dataSource"
class="org.springframework.jdbc.datasource.DriverManagerDataSource">
<property name="driverClassName" value="Altibase.jdbc.driver.AltibaseDriver"/>
<property name="url" value="jdbc:Altibase://192.168.1.35:21129/mydb"/>
<property name="username" value="sys"/>
<property name="password" value="manager" />
</bean>
     
<bean id="sqlMapClient"
 class="org.springframework.orm.ibatis.SqlMapClientFactoryBean">
   <property name="dataSource" ref="dataSource"/>
   <property name="configLocation" value="SqlMapConfigExample.xml"/>
</bean>  
<bean id="transactionManager"
 class="org.springframework.jdbc.datasource.DataSourceTransactionManager">
   <property name="dataSource" ref="dataSource"/>
</bean>
     
<bean id="txProxyTemplate" abstract="true"
class="org.springframework.transaction.interceptor.TransactionProxyFactoryBean">
  <property name="transactionManager"  ref="transactionManager" />       
  <property name="transactionAttributes">
     <props>
    <prop key="insert*">PROPAGATION_REQUIRED</prop>
    <prop key="update*">PROPAGATION_REQUIRED</prop>
    <prop key="delete*">PROPAGATION_REQUIRED</prop>
    <prop key="get*">PROPAGATION_REQUIRED</prop>
    </props>
  </property>
</bean>
     
<bean id="lobSampleDao" parent="txProxyTemplate">
<property name="target">
     <bean class="com.altibase.lob.LobSampleDao">
        <property name="sqlMapClient" ref="sqlMapClient"/>
     </bean>
  </property>
</bean>
…
```

To run the LobSpringIbatisSample project above, Altibase.jar, ibatis-2.3.4.x.jar, spring-jdbc.jar, spring.orm.jar, spring.jar, commons-logging,kar, and club-nodep-xx files are needed.

![img](http://aid.altibase.com/download/attachments/7340082/eclipse_jdbc6.png?version=1&modificationDate=1416819767000&api=v2)

## Appendix

Based on the sampleConnection example, the method of integrating with ALTIBASE in iBATIS is explained in details.

> Note: IDE uses Eclipse.

### Creating DB Tables and Sequences

The following tables and sequences are created in the DB. (Refer to create_tbl.sql file)

```
CREATE TABLE PERSON(
    PER_ID NUMBER (5, 0) NOT NULL,
    PER_NAME VARCHAR (40) NOT NULL,
    PER_BIRTH_DATE DATE,
    PER_WEIGHT_KG NUMBER (4, 2) NOT NULL,
    PER_HEIGHT_M NUMBER (4, 2) NOT NULL,
    PRIMARY KEY (PER_ID)
);
 
CREATE SEQUENCE PERSON_SEQ;
```

### Creating Project

Create a project called SimpleConnection in Eclipse.

1. Click Menu-File-Java Project
2. Project name: Enter SimpleConnection
3. Click the Finish button

![img](http://aid.altibase.com/download/attachments/7340084/additional_1.png?version=1&modificationDate=1416819881000&api=v2)

### Creating SqlMap File

Create SqlMap file that defines CRUD SQL statement of Person table and methods to be mapped (Person.xml).

1. Right-click on the SimpleConnection project-src directory and click New-File.
2. Create Person.xml in File name:.

![img](http://aid.altibase.com/download/attachments/7340084/additional_2.png?version=1&modificationDate=1416819945000&api=v2)

Write the the following in the Person.xml file.

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE sqlMap PUBLIC "-//iBATIS.com//DTD SQL Map 2.0//EN"
"http://www.ibatis.com/dtd/sql-mapconfig-2.dtd">
 
<sqlMap namespace="Person">
    <resultMap id="PersonResult" class="examples.domain.Person">
        <result property="id" column="per_id" />
        <result property="name" column="per_name" />
        <result property="birthDate" column="per_birth_date" />
        <result property="weightInKilograms" column="per_weight_kg" />
        <result property="heightInMeters" column="per_height_m" />
</resultMap>
 
<select id="getPerson" parameterClass="int" resultClass="examples.domain.Person">
        <![CDATA[
            SELECT
            PER_ID as id,
            PER_NAME as name,
            PER_BIRTH_DATE as birthDate,
            PER_WEIGHT_KG as weightInKilograms,
            PER_HEIGHT_M as heightInMeters
            FROM PERSON
            WHERE PER_ID = #value#
        ]]>
</select>
 
<insert id="insertPerson" parameterClass="examples.domain.Person">
        <![CDATA[
            INSERT INTO
            PERSON (PER_ID, PER_NAME, PER_BIRTH_DATE,
PER_WEIGHT_KG, PER_HEIGHT_M)
            VALUES (#id#, #name#, #birthDate#,
#weightInKilograms#, #heightInMeters#)
        ]]>
</insert>
 
<update id="updatePerson" parameterClass="examples.domain.Person">
        <![CDATA[
            UPDATE PERSON
            SET PER_NAME = #name#,
            PER_BIRTH_DATE = #birthDate#,
            PER_WEIGHT_KG = #weightInKilograms#,
            PER_HEIGHT_M = #heightInMeters#
            WHERE PER_ID = #id#
        ]]>
</update>
 
<delete id="deletePerson" parameterClass="int">
        <![CDATA[
            DELETE PERSON
            WHERE PER_ID = #id#
        ]]>
</delete>
 
<select id="getAllPersons"  resultMap="PersonResult">
        <![CDATA[
            SELECT * FROM person
        ]]>
</select>
</sqlMap>
```

SQL matching the ID defined in \<insert>, \<update>, \<delete>, and \<select> tags defined in the above file when calling insert, update, delete, queryForXXX () method of SqlMapClient in the application are automatically executed.

### Creating SqlMapConfig File

1. Create a properties file (db.properties) that defines properties for ALTIBASE connection. (Right click on SimpleConnection project-src directory and click New-File. Create db.properties in File name :)

```
driver=Altibase.jdbc.driver.AltibaseDriver
url=jdbc:Altibase://192.168.1.35:21129/mydb
username=sys
password=manager
```

2. Set the dataSource and SqlMap files for interworking with ALTIBASE in the SqlMapConfig file (SqlMapConfigExample.xml). (Right click on the SimpleConnection project-src directory and click New-File. Create SqlMapConfigExample.xml in File name:)

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE sqlMapConfig PUBLIC "-//iBATIS.com//DTD SQL Map Config 2.0//EN"
"http://www.ibatis.com/dtd/sql-map-config-2.dtd">
 
<sqlMapConfig>
 
<properties resource="db.properties" />
 
<transactionManager type="JDBC" >
    <dataSource type="SIMPLE">
       <property name="JDBC.Driver" value="${driver}"/>
       <property name="JDBC.ConnectionURL" value="${url}"/>
       <property name="JDBC.Username" value="${username}"/>
       <property name="JDBC.Password" value="${password}"/>
    </dataSource>
</transactionManager>
 
<sqlMap resource="Person.xml" />
 
</sqlMapConfig>
```

### Creating Application

1. Create a Person class (Person.java) that is a DO object for the person table.
2. Right-click in the src directory of the SimpleConnection project and click New-Class.
3. Enter examples.domain in Package: and Person in Name:

![img](http://aid.altibase.com/download/attachments/7340084/additional_3.png?version=1&modificationDate=1416820163000&api=v2)

Write the following in the Person.java file.

```
package examples.domain;
import java.sql.*;
public class Person {
    private int id;
    private String name;
    private Date birthDate;
    private double weightInKilograms;
    private double heightInMeters;
    public int getId () {
        return id;
    }
    public void setId (int id) {
        this.id = id;
    }
    public void setName(String name) {
        this.name = name;
    }
    public String getName() {
        return name;
    }
    public void setBirthDate(Date birthDate) {
        this.birthDate = birthDate;
    }
    public Date getBirthDate() {
        return birthDate;
    }
    public void setWeightInKilograms(double weightInKilograms) {
        this.weightInKilograms = weightInKilograms;
    }
    public double getWeightInKilograms() {
        return weightInKilograms;
    }
    public void setHeightInMeters(double heightInMeters) {
        this.heightInMeters = heightInMeters;
    }
    public double getHeightInMeters() {
        return heightInMeters;
    }
    public String toString(){
                return "id="+id+", name="+name+", birthData="+birthDate+",
weightInKillograms="+weightInKilograms+
",heightInMeters="+heightInMeters;
    }
}
```

3. Write a main program (PersonApp.java) that executes CRUD in the DB.
4. Right-click in the src directory of the SimpleConnection project and click New-Class.
5. Enter PersonApp in Name :.

![img](http://aid.altibase.com/download/attachments/7340084/additional_4.png?version=1&modificationDate=1416820260000&api=v2)

Write the following in the PersonApp.java file.

```
import java.io.IOException;
import java.io.Reader;
import java.sql.SQLException;
import java.util.List;
import examples.domain.Person;
import com.ibatis.common.resources.Resources;
import com.ibatis.sqlmap.client.SqlMapClient;
import com.ibatis.sqlmap.client.SqlMapClientBuilder;
 
public class PersonApp {
 
public static void main(String[] args) throws Exception {
    String resource ="SqlMapConfigExample.xml";
    Reader reader = Resources.getResourceAsReader(resource);
    SqlMapClient sqlMap = SqlMapClientBuilder.buildSqlMapClient(reader);
 
    //insert Person
    Person newPerson1 = new Person();
    newPerson1.setName("KIM");
    newPerson1.setBirthDate (new java.sql.Date(1978,1-1,1));
    newPerson1.setHeightInMeters(1.82);
    newPerson1.setWeightInKilograms(80.23);
    sqlMap.insert ("insertPerson", newPerson1);
 
    Person newPerson2 = new Person();
    newPerson2.setName("LEE");
    newPerson2.setBirthDate (new java.sql.Date(1975,5-1,5));
    newPerson2.setHeightInMeters(1.57);
    newPerson2.setWeightInKilograms(45.23);
    sqlMap.insert ("insertPerson", newPerson2);
    System.out.println();
    System.out.println("insert Person");
 
    List<Person> list = (List<Person>)sqlMap.queryForList("getAllPersons");
    System.out.println("Selected "+list.size()+" records.");
    for(int i=0; i< list.size();i++){
        System.out.println(list.get(i));
    }
 
    //update Person
    newPerson1.setHeightInMeters(1.93);
    newPerson1.setWeightInKilograms(86.36);
    sqlMap.update("updatePerson", newPerson1);
    System.out.println();
    System.out.println("update Person");
    list = sqlMap.queryForList("getAllPersons");
    System.out.println("Selected "+list.size()+" records.");
    for(int i=0; i< list.size();i++){
        System.out.println(list.get(i).toString());
    }
    System.out.println();
    System.out.println("get Person");
 
    //get Person
    Integer personPk = new Integer(1);
    Person person = (Person) sqlMap.queryForObject ("getPerson", personPk);
    System.out.println(person);
 
    //delete Person
    sqlMap.delete ("deletePerson", new Integer(1));
    sqlMap.delete ("deletePerson", new Integer(2));
    System.out.println();
    System.out.println("delete Person");
    list = sqlMap.queryForList("getAllPersons");
    System.out.println("Selected "+list.size()+" records.");
    for(int i=0; i< list.size();i++){
        System.out.println(list.get(i));
    }
 
}
}
```

### Adding Related JAR Files

Add the Altibase.jar and ibatis-2.3.4.x.jar files.

Right-click on SimpleConnection project, click Properties-Java Build Path-Click Add External JARS in Libraries to add Altibase.jar and ibatis-2.3.4.x.jar files.

![img](http://aid.altibase.com/download/attachments/7340084/additional_5.png?version=1&modificationDate=1416820366000&api=v2)

### Running Application

Run the SimpleConnection project.

After clicking the SimpleConnection project, run from the menu or click the Run button.

![img](http://aid.altibase.com/download/attachments/7340084/additional_6.png?version=1&modificationDate=1416820405000&api=v2)
