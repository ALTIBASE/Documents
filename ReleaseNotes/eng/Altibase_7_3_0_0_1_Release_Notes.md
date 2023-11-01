<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Altibase 7.3.0.0.1 Release Notes](#altibase-73001-release-notes)
  - [1. 시스템 요구사항](#1-%EC%8B%9C%EC%8A%A4%ED%85%9C-%EC%9A%94%EA%B5%AC%EC%82%AC%ED%95%AD)
    - [하드웨어 최저 사양](#%ED%95%98%EB%93%9C%EC%9B%A8%EC%96%B4-%EC%B5%9C%EC%A0%80-%EC%82%AC%EC%96%91)
    - [운영 체제 및 플랫폼](#%EC%9A%B4%EC%98%81-%EC%B2%B4%EC%A0%9C-%EB%B0%8F-%ED%94%8C%EB%9E%AB%ED%8F%BC)
  - [2. 릴리스 정보](#2-%EB%A6%B4%EB%A6%AC%EC%8A%A4-%EC%A0%95%EB%B3%B4)
    - [2.1 Altibase 7.3 의 새로운 기능](#21-altibase-73-%EC%9D%98-%EC%83%88%EB%A1%9C%EC%9A%B4-%EA%B8%B0%EB%8A%A5)
      - [2.1.1 AKU(Altibase Kubernetes Utility)의 지원](#211-akualtibase-kubernetes-utility%EC%9D%98-%EC%A7%80%EC%9B%90)
      - [2.1.2 AltiShapeLoader 1.0제공](#212-altishapeloader-10%EC%A0%9C%EA%B3%B5)
      - [2.1.3 JDBC 4.2 스펙 지원](#213-jdbc-42-%EC%8A%A4%ED%8E%99-%EC%A7%80%EC%9B%90)
      - [2.1.4 OpensSSL 3.0.8 지원](#214-opensssl-308-%EC%A7%80%EC%9B%90)
      - [2.1.5 기능 개선 - SQL 확장](#215)
      - [2.1.6 기능 개선 - Spatial SQL 개선](#216)
      - [2.1.7 기능 개선 - 이중화 기능 개선](#217)
      - [2.1.8 기능 개선 - 응용 프로그램 개발 인터페이스](#218)
      - [2.1.9 기능 개선 - 내장패키지 및 함수](#219)
      - [2.1.10 기능 개선 - 유틸리티](#2110)
      - [2.1.11 기능 개선 - JDBC Adapter, oraAdpater](#2111)
      - [2.1.12 성능 개선](#2112-%EC%84%B1%EB%8A%A5-%EA%B0%9C%EC%84%A0)
      - [2.1.13 고가용성](#2113-%EA%B3%A0%EA%B0%80%EC%9A%A9%EC%84%B1)
      - [2.1.14 DBeaver 패키지 제공](#2114-dbeaver-%ED%8C%A8%ED%82%A4%EC%A7%80-%EC%A0%9C%EA%B3%B5)
    - [2.2 변경 사항](#22-%EB%B3%80%EA%B2%BD-%EC%82%AC%ED%95%AD)
      - [2.2.1 데이터베이스 버전](#221-%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4-%EB%B2%84%EC%A0%84)
      - [2.2.2 호환성](#222-%ED%98%B8%ED%99%98%EC%84%B1)
      - [2.2.3 기타 변경사항](#223-%EA%B8%B0%ED%83%80-%EB%B3%80%EA%B2%BD%EC%82%AC%ED%95%AD)
      - [2.2.4 Altibase 서버 프로퍼티](#224-altibase-%EC%84%9C%EB%B2%84-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
      - [2.2.5 메타 테이블](#225-%EB%A9%94%ED%83%80-%ED%85%8C%EC%9D%B4%EB%B8%94)
      - [2.2.6 성능 뷰](#226-%EC%84%B1%EB%8A%A5-%EB%B7%B0)
    - [2.3 패키지](#23-%ED%8C%A8%ED%82%A4%EC%A7%80)
    - [2.4 다운로드](#24-%EB%8B%A4%EC%9A%B4%EB%A1%9C%EB%93%9C)
      - [Package](#package)
      - [Manual](#manual)
      - [설치](#%EC%84%A4%EC%B9%98)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

</br>

</br>

</br>

Altibase 7.3.0.0.1 Release Notes
===============================

**(2023.08)** </br>



## 1. System Requirements

### Minimum Hardware Requirements

* 1GB RAM (Recommended: 2GB)
* 1 CPU (Recommended: 2 CPUs)
* 4 GB free hard disk space (Recommended: 12 GB)



### Operating Systems and Platforms

Altibase 7.3.0.0.1 can be run on the operating systems and platforms listed in the table below.


|                                                              | Altibase Server | Altibase Client | Software requirements   |
| ------------------------------------------------------------ | :-------------: | :-------------: | :---------------------- |
| **AIX on IBM Power Systems**                                 |                 |                 |                         |
| AIX 6.1                                                      |        ●        |        ●        |                         |
| **Linux x86-64**                                             |                 |                 |                         |
| Red Hat Enterprise Linux 6<br/>Red Hat Enterprise Linux 7<br/>Red Hat Enterprise Linux 8 |        ●        |        ●        | - GNU glibc 2.12 ~ 2.33 |
| **Linux on Power**                                           |                 |                 |                         |
| Red Hat Enterprise Linux 6.5 and higher                      |        ●        |        ●        | - GNU glibc 2.12 ~ 2.33 |
| **Linux on Power** **(Little Endian)**                       |                 |                 |                         |
| Red Hat Enterprise Linux 7.3 and higher                      |        ●        |        ●        | - GNU glibc 2.17 ~ 2.33 |
| **HP-UX Itanium (IA-64)**                                    |                 |                 |                         |
| HP-UX 11.31                                                  |        ●        |        ●        |                         |

> Altibase 7.3 server and client both support 64-bit only.
>
> Altibase 7.3 is compatible with minor versions of Red Hat Enterprise Linux 6, 7 and 8.
>
> Java 버전: Altibase 7.3 is compatiable with JDK 1.8 and higher.

<br/><br/>

## 2. Release Nots

### 2.1 New Features

#### 2.1.1 AKU(Altibase Kubernetes Utility)

AKU(Altibase Kubernetes Utility) is a utility that helps with synchronizing data or resetting synchronization information when Pods start and terminate in a Statefulset in Kubernetes.

#### 2.1.2 AltiShapeLoader 1.0

altiShapeLoader  is developed for importing and exporting shapefiles<sup id="shapefile1">[[1]](#shapefile)</sup> and is based on the GeoTools, which is a Java-based open source framework.

#### 2.1.3 Partial Support for JDBC 4.2

In Altibase 7.3, partial support for JDBC API Specification 4.2 is provided. For more detailed information about the JDBC 4.2 API supported by the Altibase 7.3 JDBC driver, please refer to [**JDBC User's Manual** - JDBC 4.2 API References](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/JDBC%20User's%20Manual.md#6-jdbc-42-api-references). Additionally, for information on the changes and compatibility issues, please consult [Changes and Compatibility Issues with Altibase 7.3 JDBC Driver]() Section in this manual.

#### 2.1.4 OpensSSL 3.0.8 Support

To enhance security, Altibase supports the latest version of OpenSSL 3.0.8, and no longer provide support for OpenSSL versions 1.0.x. Altibase now extends its protocol support to include TLS 1.3, in addition to TLS 1.0 and 1.2. If users want to specify particular cipher algorithms for TLS 1.3, please set them in the server property, SSL_CIPHER_SUITES. For more detailed information, please refer to [**Altibase SSL TLS User's Guide** - server properties to connect over ssl](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/Altibase%20SSL%20TLS%20User's%20Guide.md#step-2-set-server-properties-to-connect-over-ssl).

Additionally, Altibase supports the FIPS(Federal Information Processing Standards) module. To use the FIPS module with SSL, you must set the SSL_LOAD_CONFIG property to 1. Refer to [Altibase SSL TLS User's Guide - Step4. FIPS module with SSL]()

#### 2.1.5 Funtionality Improvement - SQL Extension<b id="215"></b>

##### VARRAY TYPE

Within stored procedures, the VARRAY type is now supported as a new user-defined type. The VARRAY type is capable of storing a sequence of data with the same data type. For more details, please refer to [Stored Procedures Manual - VARRAY]().

##### Anonymous Block 

An anonymous block is a form of a stored procedure composed of a body block without a header, declared with a structure like DECLARE...BEGIN...END;. Anonymous blocks do not create PSM (Persistent Stored Module) objects, are not stored in the database, and do not return a value in the RETURN clause. Unlike stored procedures, anonymous blocks allow the use of INPUT, OUTPUT, and INOUT bind variables.

##### Internal Mode in C/C++ External Procedure

In Internal mode within External Procedures, it directly loads dynamic libraries and invokes external procedures from Altibase Server without the need for an agent process, resulting in improved efficiency compared to external mode. For more details, refer to [**External Procedures Manual**](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/External%20Procedures%20Manual.md).

##### Multiple Delete, Update

Provides support for multiple delete, multiple update statements. Refer to [**SQL Reference Manual** - multiple_delete](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/SQL%20Reference.md#multiple_delete) , [multiple_update](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/SQL%20Reference.md#multiple_update) 을 참고한다.

##### Regular Expression for Korean searching

Provides PCRE2 compatibility mode for support Regular Expressions used in Korean searching. Refer to [**SQL Reference Manual**](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/SQL%20Reference.md).

##### Fetch Across Rollback

To address the 'Fetch out of sequence' error issue, we now provide the 'fetch across rollback' feature.

##### Improved Queue Functionality with Delete Statement Control

Queue functionality has been enhanced to allow the use of DELETE statements. Additionally, new 'DELETE ON' and 'DELETE OFF' clauses have been introduced to control the execution of DELETE statements within queues. Refer to [**SQL Reference Manual**](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/SQL%20Reference.md) and V$QUEUE_DELETE_OFF performance view for more information.

##### Sequence Restart Statement

Supports the restart_clause with ALTER SEQUENCE statement. Refer to [**SQL Reference Manual** - restart_clause](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/eng/SQL%20Reference.md#restart_clause).

</br>

#### 2.1.6 Funtionality Improvement - Spatial SQL<b id="216"></b>

##### SRID(Spatial Reference Identifier) interface

SRID (Spatial Reference Identifier) is an identifier used to distinguish spatial objects, represented by a 4-byte integer, and can be applied to GEOMETRY columns. You can specify the SRID when creating a table and also alter the SRID using the ALTER TABLE statement.

The support for SRID introduces new ways to represent GEOMETRY data types:

- Extended Well-Known Text (EWKT) format: It includes SRID (Spatial Reference Identifier) information in the WKT format to represent spatial objects.
- Extended Well-Known Binary (EWKB) format: It includes SRID (Spatial Reference Identifier) information in the WKB format to represent spatial objects.

##### Spatial Functions

New functions have been introduced as follows.

* ASEWKT
* ASEWKB
* GEOMFROMEWKT
* GEOMFROMEWKB
* SETSRID
* SRID
* ST_Collect
* ST_IsCollection
* ST_LinestringFromWKB
* ST_MakeEnvelope
* ST_MakeLine
* ST_MakePoint
* ST_Point
* ST_PolygonFromText
* ST_Transform

##### Spatial object Creation Functions

New functions have been introduced as follows.

* ACSGetGeometrySRID

#### 2.1.7 Funtionality Improvement - Replication<b id="217"></b>

##### 이중화 대상 테이블에 DDL 복제 기능 추가

이중화를 통하여 DDL 복제(Synchronization)가 가능하게 되었다. 이 기능을 사용하기 위해서는 각노드의 [REPLICATION_DDL_SYNC](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#replication_ddl_sync) 프로퍼티를 1로 설정해야 한다. 또한, 각 노드의 [REPLICATION_DDL_ENABLE](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#replication_ddl_enable) 프로퍼티를 1로 설정하고, [REPLICATION_DDL_ENABLE_LEVEL](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#replication_ddl_enable_level)이 동일하게 설정해야 한다.

DDL 복제를 사용하기 위해 다음의 제약 조건을 확인해야 한다.

- DDL 복제를 수행할 노드들의 이중화가 동작하고 있어야 한다.

- DDL 복제를 수행할 지역 노드와 원격 노드의 테이블 이름이 같아야 한다.
- DDL 복제를 수행할 지역 노드와 원격 노드의 테이블 파티션이름이 같아야 한다.
- DDL 복제를 수행할 이중화 대상 사용자의 이름이 같아야 한다.
- 한번에 하나의 노드에서만 DDL 복제를 수행해야 한다.
- DDL 복제를 수행할 각 이중화 노드의 REPLICATION_DDL_ENABLE과 REPLICATION_DDL_ENABLE_LEVEL 프로퍼티 값이 같아야 한다.
- Altibase Patch 버전(5자리)이 동일해야한다.
- Propagation 옵션 사용시 DDL 복제를 허용하지 않는다.

#####  이중화 수신 전용(RECEIVE_ONLY) 옵션 제공

이중화를 수신 전용 옵션으로 설정하여, 다른 노드로 변경 데이터를 전송하지 않는 기능을 제공한다. 수신 전용으로 이중화를 생성하면, 로그를 읽지 않으므로 네트워크 장애등의 이중화 이슈가 발생하여도 시스템에 영향을 주지 않는다. 자세한 설명은 [**Replication Manual** -  이중화 수신 전용 옵션](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/Replication%20Manual.md#%EC%9D%B4%EC%A4%91%ED%99%94-%EC%88%98%EC%8B%A0-%EC%A0%84%EC%9A%A9-%EC%98%B5%EC%85%98receive-only-option) 을 참고한다.



#### 2.1.8 기능 개선 - 응용 프로그램 개발 인터페이스<b id="218"></b>

##### 인피니밴드(InfiniBand) 지원

통신 성능 향상을 위해 RDMA(Remote Direct Memory Access) 통신 기반인 Infiniband를 지원한다.

##### JDBC 에 추가된 기능

- **Auto-loading of JDBC driver class**

  명시적으로 Class.forName() 클래스를 로딩할 필요없이 META-INF/services/java.sql.Driver 파일을 이용한 자동 드라이버 로딩 기능 지원

- **Wrapper Pattern Support**

  프록시에서 구현 객체에 대한 참조를 얻는 JDBC 4.0 표준 인터페이스를 지원한다. 커넥션풀 등에서 생성하는 프록시 객체에서 JDBC 객체를 획득할 수 있다.

  ```java
  try (Connection sWrappedCon = dbPool.getConnection()) {
      if (sWrappedCon.isWrapperFor(AltibaseConnection.class)) {
          AltibaseConnection connection = sWrappedCon.unwrap(AltibaseConnection.class);
          ...
          ...
  }
  ```

- **National Character Set Support**

  JDBC 4.0 스펙인 표준 다국어 처리 인터페이스 지원

- **Aborting Connections**

  비동기적으로 데이터베이스와의 물리적 연결을 종료하는 Connection.abort() 인터페이스 지원

- **Standard Socket Network Timeout API Support**

  데이터베이스 서버로부터 소켓 응답 대기 시간을 설정하는 표준 인터페이스Connection.setNetworkTimeout() 지원

- **Connection Management Enhancements**

  Validation Query없이 Connection 객체에서 유효성 검사를 수행하는 Connection.isValid() 지원

- **Large Update Counts Support**

  대용량 레코드 업데이트를 위한 executeLargeUpdate(), executeLargeBatch() 지원

- **Set Client Information Support**

  Connection.setClientInfo()를 이용한 클라이언트 어플리케이션 속성(name) 설정 지원

- **java.sql.SQLType interface Support**

  JDBC 4.2 표준 인터페이스 java.sql.SQLType을 구현한 AltibaseJDBCType 지원

- **Try-with-resources 구문을 통한 자동 JDBC 리소스 해제 **

  ```java
  try (Statement stmt = con.createStatement()) {
        ResultSet rs = stmt.executeQuery(query);
        while (rs.next()) {
          String coffeeName = rs.getString("aaa");
          int supplierID = rs.getInt("bbb");
        }
      }
  }
  ```

- **SQLException에 Enhanced for-each loop 사용을 지원**

  ```java
  catch(SQLException ex) {
       for(Throwable e : ex ) {
          LOG.error("Error occurred: " + e);
       }
  }
  ```

</br>

#### 2.1.9 기능 개선 - 내장패키지 및 함수<b id="219"></b>

##### DBMS_STANDARD 패키지 제공

DBMS_STANDARD 패키지를 통해서 트리거 이벤트를 확인하는 함수를 제공한다.

##### DBMS_METADATA 패키지 제공

DBMS_METADATA 패키지는 데이터베이스 딕셔너리로부터 객체 생성 DDL 구문 또는 권한 GRANT 구문을 추출하는 기능을 제공한다.

##### DBMS_SQL_PLAN_CACHE 패키지 제공

특정 실행 계획(Execution Plan)을 SQL Plan Cache에 유지하거나 삭제하는 기능을하는 저장 프로시저를 제공한다.

##### DBMS_OUTPUT 패키지에 print_enable/print_disable 프로시저 추가

PSM내에서 println 기능을 enable, disable 할수 있는 기능을 제공하며, 세션 단위로 수행된다.

##### DBMS_LOCK 패키지에 sleep2 프로시저 추가

마이크로초(micro second) sleep 을 지원하는 시스템 저장 프로시저 sleep2가 추가되었다.

##### SYS_SPATIAL 패키지

SPATIAL_REF_SYS 테이블에 Spatial Reference System 메타 데이터를 등록, 삭제하는 기능을 제공한다.

##### UTL_COPYSWAP 패키지

UTL_COPYSWAP 패키지는 테이블 스키마 복사, 데이터 복제, 테이블 교환 인터페이스를 제공한다.

</br>

#### 2.1.10 기능 개선 - 유틸리티<b id="2110"></b>

##### AltiMon의 AIX 7, Power Linux LE(Little endian)에서 동작 지원

AIX 7 버전 및 Power Linux LE에서도 altimon을 사용할 수 있다.

##### AltiComp 커밋 카운트 설정 기능 추가

커밋(commit) 카운트를 설정할 수 있는 프로퍼티 COUNT_TO_COMMIT가 추가되었다. 관련 내용은 [**Utilities Manual**](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/Utilities%20Manual.md#count_to_commit) 에서 확인할 수 있다.

</br>

#### 2.1.11 기능 개선 - JDBC Adapter, oraAdpater<b id="2111"></b>

##### LOB데이터 타입 지원

LOB 데이터 타입의 지원을 위해 ADAPTER_LOB_TYPE_SUPPORT 프로퍼티가 추가되었다. LOB 데이터 타입 지원 기능을 사용하려면 ADAPTER_LOB_TYPE_SUPPORT 프로퍼티의 값을 1로 변경한 다음, ADAPTER를 재시작 해야 한다.

##### 오프라인 옵션 제공

어뎁터(JDBC Adapter, oraAdapter)를 이용하여 Altibase에서 변경된 데이터를 타켓 데이터베이스에 적용할때, Altibase 서버에서 장애가 발생하는 경우를 대비하기 위한 기능이다. 자세한 설명은 [**Adapter for JDBC User's Manual** - 오프라인 옵션](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_trunk/kor/Adapter%20for%20JDBC%20User's%20Manual.md#%EC%98%A4%ED%94%84%EB%9D%BC%EC%9D%B8-%EC%98%B5%EC%85%98offline-option) 및 [**Adapter for Oracle User's Manual** - 오프라인 옵션](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_trunk/kor/Adapter%20for%20Oracle%20User's%20Manual.md#%EC%98%A4%ED%94%84%EB%9D%BC%EC%9D%B8-%EC%98%B5%EC%85%98offline-option) 을 참고한다.

</br>

#### 2.1.12 성능 개선

##### TABLE LOCK 병목구간 개선

테이블 잠금(TABLE LOCK) 관리자 타입을 지정하는 LOCK_MGR_TYPE 프로퍼티를 삭제하고, 새로운 테이블 잠금 모드(light mutex mode)를 적용하여 테이블 잠금 병목구간을 개선하였다.

##### TABLESPACE MANAGER MUTEX 병목구간 개선

테이블 스페이스 뮤텍스에서 불필요한 잠금(LOCK)을 제거하도록 개선하였다.

##### 디스크 템프 테이블 성능 개선

디스크 템프 테이블을 사용하는 SQL의 성능을 향상시키고, 메모리 사용량을 개선하였다.

##### 트랜잭션 로그 기록 성능 향상

로그 압축 알고리즘을 압축 속도가 빠른 LZ4 로 변경하였다.

##### OLTP Scalability 향상

- Linux x86-64 CPU 코어 수 24코어 이상에서 조회 트랜잭션 성능 저하 현상 개선
- 메모리 DB 삭제(DELETE) 트랜잭션 성능 향상을 위해 로깅 구조 개선
- 디스크 DB 변경 트랜잭션 성능 향상을 위해 In-place MVCC 동작 방식 개선
- INSERT/UPDATE 트랜잭션 처리 시 불필요한 트랜잭션 로그 기록을 제거
- 트랜잭션 로그파일 압축 시 메모리 할당/해제 병목 개선
- 커밋 병목 및 가비지 콜렉션 쓰레드 병목 개선

  - 트랜잭션 커밋 후 테이블 정보 업데이트 병목 개선
- 메모리 DB 트랜잭션 성능 향상
  - 디스크 읽기를 유발하는 함수의 병목을 제거
  - Group Commit Log 기능 추가

##### 인덱스 성능 개선

* 서버 시작 시 POINTER BASE 인덱스 생성 시간 단축 및 메모리 사용량 개선
* 서버 시작 시 VALUE BASE 인덱스 생성 시간 단축 및 메모리 사용량 개선

##### 데이터베이스 구동 성능 개선

서버 구동시 인덱스 빌드에 사용되는 쓰레드들의 관리를 개선하여, 서버 구동 성능이 향상되었다.

##### 휘발성/비휘발성 메모리 DB 트랜잭션 성능 향상

메모리 테이블 객체 식별자 추적 단계를 간소화하여 휘발성/비휘발성 메모리 DB 트랜잭션 성능이 향상되었다.

##### DEQUEUE 병렬 수행시 성능 개선

병렬로 DEQUEUE 수행 시 발생하는 병목을 제거하여 성능을 개선하였다.

##### Common Subexpression Elimination의 PREPARE 시간 단축

CSE(Common Subexpression Elimination)는 조건절의 중복된 조건식을 찾아 제거하는 최적화 기능이다. CSE 수행 알고리즘을 개선하여 관련 쿼리의 성능을 개선하였다.

##### 메모리 파티션드 테이블의 Simple query 최적화로 성능개선

기존에는 메모리 테이블에 대해서만 simple query 최적화를 지원하였으나, 메모리 파티션드 테이블의 경우도 지원하게 되었다. 메모리 파티션드 테이블의 simple query 최적화 지원으로 메모리 파티션드 테이블의 DML 성능이 개선되었다.

##### Row Filter 수행 성능 개선 - SERIAL FILTER 적용

Filter 연산자를 직렬화 및 함수 호출구조의 최적화를 통해 row filter 수행 성능을 개선하였다. 이 기능을 사용하기 위해 SERIAL_FILTER 힌트 및 SERIAL_EXECUTE_MODE 프로퍼티가 추가되었다. 실행 계획에서 FILTER SERIAL EXECUTE 를 확인할 수 있다.

##### 스칼라 서브쿼리(Scalar Subquery) 성능 개선

스칼라 서브쿼리의 수행방식을 개선하여 수행 성능을 개선하였다.

##### PSM에서 for loop절의 성능개선

##### 이중화 Sender 성능 향상

- 압축 로그에서 이중화에 필요한 로그만 압축 해제하는 기능 추가
- xLog 압축 알고리즘을 LZO에서 LZ4로 변경

##### 마이그레이션 성능 개선

대용량 데이터 이전을 위한 데이터 삽입의 성능이 개선되었다. iloader의 성능 옵션에 -lightmod가 추가되었다. 자세한 설명은 [**iLoader User's Maunal** - 성능옵션](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/iLoader%20User's%20Manual.md#%EC%84%B1%EB%8A%A5-%EC%98%B5%EC%85%98)에서 확인할 수 있다.

##### JDBC fetch 성능 개선

JDBC fetch 성능 향상을 위해 ResultSet 객체 사용방식을 개선하였다. 동일한 PreparedStatement 객체에서 여러개의 ResultSet 객체를 생성하는 경우, 첫번재 ResultSet 객체를 재사용한다. ResultSet 객체의 재사용을 하지 않으려면 JDBC 연결 속성 중 reuse_resultset 속성의 값을 false로 변경하면 된다.

</br>

#### 2.1.13 고가용성

##### DDL PVO 안정성 향상

DDL PVO 단계에서의 예외처리 개선으로 안정성을 향상시켰다.

##### 프로토콜 유효성 검증 개선

유효하지 않은 패킷(malformed packet) 전송으로인한 서버에서의 비정상 종료 및 비정상 동작이 발생하지 않도록 개선되었다. 프로토콜 처리시 패킷의 유효성을 체크하여 비정상적인 경우, 클라이언트의 접속을 끊고 진단로그를 남기도록 개선되었다. 이를 위해 CM_MSGLOG_FLAG 의 기본값이 3으로, SERVER_MSGLOG_FLAG의 기본값이 15로 변경되었다.

##### 트랜잭션 안정성 개선 - Multiple Rollback Segment

동시에 수행가능한 최대 디스크 트랜잭션의 개수를 기존 512개에서 16384로 확장하였다.

##### 언두(undo) 테이블스페이스 재사용 안정성 향상

언두 테이블스페이스와 디스크 인덱스의 불필요한 관계를 제거하여 버그 발생 위험 요소 제거하였다. 디스크 페이지 공간 효율 개선으로 관련 프로퍼티들의 기본값 및 최대값이 변경되었다.

- INDEX_INITTRANS 최대값이 30에서 50으로 변경
- INDEX_MAXTRANS 기본값과 최대값이 30에서 50으로 변경

#### 2.1.14 DBeaver 패키지 제공

윈도우즈용 DBeaver 패키지를 제공한다. 자세한 내용은 [**Altibase 3rd Party Connector Guide** - 1.DBeaver](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Tools/Altibase_release/kor/Altibase%203rd%20Party%20Connector%20Guide.md#1dbeaver) 를 참고한다.

</br>

### 2.2 Changes

The following describes the features that DBAs and developers need to be aware of, which include additions, modifications, and removals.

#### 2.2.1 Database Version

Version by Database Component

| Altibase server/client Version | Database Binary Version | Meta Version | Communication Protocol Version | Replication Protocol Version |
| :----------------------------: | :---------------------: | :----------: | :----------------------------: | :--------------------------: |
|           7.1.0.8.8            |          6.5.1          |    8.11.1    |             7.1.7              |            7.4.7             |
|           7.3.0.0.1            |          7.3.0          |    9.3.1     |             7.1.8              |            7.4.9             |

#### 2.2.2 Compatibility

##### Database Binary Version

The database binary version indciates the compatibility of the database image file and log file.

The database binary version has been updated due to enhancements in the logging structure of log files. As a result, Altibase 7.3 and earlier versions are not compatible, requiring migration efforts when upgrading to Altibase 7.3.

##### Meta Version

Given that the major version of Meta has changed, it is necessary to reconfigure the metadata when upgrading from the earlier version to Altibase 7.3.

##### Communication Protocol Version

Altibase 서버와 클라이언트 간 통신 규약 호환성을 의미하며 클라이언트 하위 호환성을 알 수 있다.

통신 프로토콜 버전 중 상위 두 자리는 같고 패치 버전이 변경되었다. 메이저 버전과 마이너 버전이 같으면 클라이언트 하위 호환성을 보장한다.

> 클라이언트 하위 호환성은 하위 버전 Altibase 라이브러리로 컴파일한 사용자 응용 프로그램(Altibase 클라이언트)이 상위 버전 Altibase 에서 정상 동작하는 것을 보장한다.

##### Replication Protocol Version

이중화 프로토콜 버전은 Altibase 이중화 하위 호환성이나 이중화 부가기능 호환 여부를 나타낸다.

메이저 버전과 마이너 버전 변경이 없어 LAZY 모드 이중화는 Altibase 이중화 하위 호환성을 보장하지만 패치 버전 변경으로 이중화 부가기능은 호환되지 않는다.

> ###### Altibase 이중화 하위 호환성
>
> Altibase 이중화 하위 호환성이란 이중화 프로토콜 버전이 낮은 버전에서 높은 버전으로 단방향 이중화가 가능함을 의미하며 이중화 프로토콜 버전에서 상위 두 자리(메이저와 마이너 버전)가 같은 경우 보장한다.
> Altibase 이중화 하위 호환성은 LAZY 모드 이중화로 제한한다.
>
> EAGER 모드 이중화는 하위 호환성을 보장하지 않는다.
> DDL 복제는 이중화 프로토콜 버전 세 자리가 모두 일치해야하므로 하위 호환성을 보장하지 않는다.
> 오프라인 이중화를 포함한 이중화 부가기능은 하위 호환성을 보장하지 않는다.

</br>

#### 2.2.3 기타 변경사항

##### aexport 변경사항

Altibase 7.3 aexport를 구동하기 위해서는 DBMS_METADATA 패키지를 반드시 설치해야 한다. 그렇지 않은 경우, 아래의 에러메시지가 출력된다.

```
[ERR-91144 : DBMS_METADATA package does not exist.]
```

##### Changes and Compatibility Issues with Altibase 7.3 JDBC Driver

Altibase JDBC 4.2는 Altibase JDBC 3.0 에 대해 하위 호환성을 보장하지만 일부 인터페이스의 경우 JDBC API Specification 4.2에 따라 동작이 변경되었다.

###### 미지원 기능에 대한 예외 처리 클래스 변경

다음 인터페이스에 대한 예외 처리 클래스가 SQLException에서 SQLFeatureNotSupportedException으로 변경되었다. SQLFeatureNotSupportedException은 SQLException의 하위 클래스이므로 기존 사용자 프로그램은 수정없이 그대로 동작한다.

- Altibase.jdbc.driver.AltibaseConnection
  - setTypeMap(Map)
- Altibase.jdbc.driver.AltibaseStatement
  - setCursorName(String)
- Altibase.jdbc.driver.AltibasePreparedStatement
  - setArray(int, Array)
  - setRef(int, Ref)
  - setURL(int, URL)
  - setUnicodeStream(int, InputStream, int)
- Altibase.jdbc.driver.Blob
  - position(Blob, long)
  - position(byte[], long)
- Altibase.jdbc.driver.Clob
  - position(Clob, long)
  - position(String, long)
- Altibase.jdbc.driver.CallableStatement
  - getArray(int)
  - getObject(int, Map)
  - getRef(int)
  - getURL(int)
- Altibase.jdbc.driver.AltibaseDatabaseMetaData
  - getColumnPrivileges(String, String, String, String)
  - getUDTs(String, String, String, int[])
- Altibase.jdbc.driver.AltibaseResultSet
  - getCursorName()
  - getArray(int)
  - getObject(int, Map)
  - getRef(int)
  - getURL(int)
  - getUnicodeStream(int)
  - updateArray(int, Array)
  - updateRef(int, Ref)

###### DatabaseMetaData의 일부 인터페이스 결과에 항목 추가

getProcedures(), getProcedureColumns(), getFunctions(), getFunctionColumns() 인터페이스 결과에 SPECIFIC_NAME 컬럼이 추가되었다.
Altibase JDBC 7.3 에서 SPECIFIC_NAME은 다음과 같은 형태로 구현하였다.

```java
ProcName(FuncName) + '_' + ouid
```

###### 연결 속성 기본값 변경

- [reuse_resultset](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/JDBC%20User's%20Manual.md#reuse_resultset)
  - Altibase 7.3 기본값은 true로 ResultSet 객체를 재사용하지만, Altibase 7.1 기본값은 false로 재사용하지 않는다.
- [lob_null_select](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/JDBC%20User's%20Manual.md#lob_null_select)
  - LOB 컬럼 값이 NULL일 때 getBlob(), getClob() 수행시 NULL을 반환할 수 있도록 JDBC 연결속성 lob_null_select가 추가되었다.
  - Altibase 7.3 기본값은 off로 NULL을 반환한다. Altibase 7.1 기본값은 on으로 LOB 객체를 반환한다.

###### Altibase JDBC 4.2만을 위한 JDBC 연결 속성 추가

- [getprocedures_return_functions](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/JDBC%20User's%20Manual.md#getprocedures_return_functions)
  - DatabaseMetaData.getProcedures(), getProcedureColumns()의 결과에 function 결과를 포함할지 설정한다. JDBC API Specification 4.2 표준은 function 정보를 제외하지만 Altibase JDBC 4.2는 클라이언트 하위 호환성을 위해 하위 버전과 같게 유지한다. 표준에 따라 function정보를 제외하려면 속성값을 false로 설정한다.

###### CLIENT_TYPE 변경

Altibase 7.3 JDBC 세션의 CLIENT_TYPE은 NEW_JDBC42이다. Altibase 7.3 JDBC Driver 를 이용하여 컴파일 또는 실행한 경우 V$SESSION의 CLIENT_TYPE 값은 NEW_JDBC42 로 조회해야 한다.

</br>

##### SQL 결과 및 실행 계획 변화

- 서브쿼리의 인라인 뷰에 ORDER BY절 사용 시 SQL 성능 개선

  이 영향을 받는 SQL의 실행 계획에 변화가 있다. SUBQUERY FILTER 안에 SORT 플랜 노드 없어진다.

- 중첩된 LEFT OUTER JOIN 수행 방식을 최적화

  이 영향을 받는 SQL에서 실행 계획 변경 및 SQL 수행 결과가 달라질 수 있다.

- Subquery Unnesting 관련 기능 변경 및 추가

  이 영향을 받는 SQL에서 실행 계획이 변경될 수 있다.

</br>

##### Replication Restrictions

###### Replication Restrictions between Altibase 7.1 and Altibase 7.3

Because the replication protocol version has been changed, DDL synchronization are not supported between Altibase 7.1 and Altibase 7.3.

Because the database binary version has been changed, offline replication are not supported between Altibase 7.1 and Altibase 7.3.

###### Replication Restrictions between Altibase 6.5.1 and Altibase 7.3

Replication from Altibase 7.3 to Altibase 6.5.1 may fail when the target table contains data with SRID values.

</br>

#### 2.2.4 Properties

Altibase 7.3.0.0.1 에서 추가, 변경, 삭제된 Altibase 서버 프로퍼티들이다. 각 프로퍼티에 대한 자세한 내용은 [General Reference-1.Data Types & Altibase Properties](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md)를 참고하기 바란다.

##### New Properties

-   [DISK_INDEX_BUILD_SORT_AREA_SIZE](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#disk_index_build_merge_page_count-%EB%8B%A8%EC%9C%84-%ED%8E%98%EC%9D%B4%EC%A7%80-%EC%88%98)
-   [DBLINK_GLOBAL_TRANSACTION_LEVEL](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#dblink_global_transaction_level)
-   [IB_CONCHKSPIN](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#ib_conchkspin)
-   [IB_ENABLE](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#ib_enable)
-   [IB_LATENCY](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#ib_latency)
-   [IB_LISTENER_DISABLE](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#ib_listener_disable)
-   [IB_MAX_LISTEN](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#ib_max_listen)
-   [IB_PORT_NO](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#ib_port_no)
-   [INIT_TOTAL_WA_SIZE](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#init_total_wa_size-%EB%8B%A8%EC%9C%84-%EB%B0%94%EC%9D%B4%ED%8A%B8)
-   [IPCDA_SEM_KEY](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#ipcda_sem_key)
-   [IPCDA_SHM_KEY](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#ipcda_shm_key)
-   [IPC_SHM_KEY](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#ipc_shm_key)
-   [IPC_SEM_KEY](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#ipc_sem_key)
-   [JOB_MSGLOG_COUNT](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#job_msglog_count)
-   [JOB_MSGLOG_FILE](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#job_msglog_file)
-   [JOB_MSGLOG_FLAG](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#job_msglog_flag)
-   [JOB_MSGLOG_SIZE](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#job_msglog_size%EB%8B%A8%EC%9C%84--%EB%B0%94%EC%9D%B4%ED%8A%B8)
-   [LISTAGG_PRECISION](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#listagg_precision-%EB%8B%A8%EC%9C%84-%EB%B0%94%EC%9D%B4%ED%8A%B8)
-   [MATHEMATICS_TEMP_MEMORY_MAXIMUM](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#mathematics_temp_memory_maximum-%EB%8B%A8%EC%9C%84--%EB%B0%94%EC%9D%B4%ED%8A%B8)
-   [NETWORK_ERROR_LOG_FILE](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#network_error_log_file)
-   [PSM_MAX_DDL_REFERENCE_DEPTH](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#psm_max_ddl_reference_depth)
-   [REGEXP_MODE](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#regexp_mode)  
-   [REPLICATION_DDL_SYNC](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#replication_ddl_sync)
-   [REPLICATION_DDL_SYNC_TIMEOUT](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#replication_ddl_sync_timeout--%EB%8B%A8%EC%9C%84--%EC%B4%88-)
-   [REPLICATION_GAP_UNIT](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#replication_gap_unit-%EB%8B%A8%EC%9C%84-%EB%B0%94%EC%9D%B4%ED%8A%B8)
-   [REPLICATION_IB_LATENCY](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#replication_ib_latency)
-   [REPLICATION_IB_PORT_NO](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#replication_ib_port_no)
-   [REPLICATION_META_ITEM_COUNT_DIFF_ENABLE](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#replication_meta_item_count_diff_enable)
-   [REPLICATION_RECEIVER_APPLIER_YIELD_COUNT](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#replication_receiver_applier_yield_count)
-   [REPLICATION_SENDER_IP](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#replication_sender_ip)
-   [SERIAL_EXECUTE_MODE](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#serial_execute_mode)
-   [SERVICE_THREAD_RECV_TIMEOUT](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#service_thread_recv_timeout%EB%8B%A8%EC%9C%84--%EC%B4%88)
-   [SSL_CIPHER_SUITES](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#ssl_cipher_suites)
-   [SSL_LOAD_CONFIG](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#ssl_load_config)        
-   [ST_MSGLOG_COUNT](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#st_msglog_count)
-   [ST_MSGLOG_FILE](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#st_msglog_file)
-   [ST_MSGLOG_FLAG](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#st_msglog_flag)
-   [ST_MSGLOG_SIZE](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#st_msglog_size)
-   [VARRAY_MEMORY_MAXIMUM](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#varray_memory_maximum)

##### Modified Properties

- [ARCHIVE_FULL_ACTION](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#archive_full_action)

  읽기 전용에서 변경 가능으로 속성이 변경되었다. 기본값 변경은 없으나, 설정값 2가 추가되었다.

- [CM_MSGLOG_FLAG](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#cm_msglog_flag)

  기본값이 3으로 변경되었다.

- [EXECUTE_STMT_MEMORY_MAXIMUM](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#execute_stmt_memory_maximum-%EB%8B%A8%EC%9C%84--%EB%B0%94%EC%9D%B4%ED%8A%B8)

  기본값이 1073741824에서 2147483648로 변경되었다.

- [HASH_AREA_SIZE](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#hash_area_size-%EB%8B%A8%EC%9C%84-%EB%B0%94%EC%9D%B4%ED%8A%B8)

  최소값이 512K 에서 3M로 변경되었다.

- [INDEX_INITRANS](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#index_initrans-%EB%8B%A8%EC%9C%84--%EA%B0%9C%EC%88%98)

  최대값이 30에서 50으로 변경되었다.

- [INDEX_MAXTRANS](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#index_maxtrans-%EB%8B%A8%EC%9C%84--%EA%B0%9C%EC%88%98)

  기본값과 최값이 30에서 50으로 변경되었다.

- [LOB_CACHE_THRESHOLD](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#lob_cache_threshold-%EB%8B%A8%EC%9C%84-bytes)

  최대값이 8192에서 524288로 변경되었다.

- [MEMORY_INDEX_BUILD_RUN_SIZE](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#memory_index_build_run_size-%EB%8B%A8%EC%9C%84--%EB%B0%94%EC%9D%B4%ED%8A%B8)

  기본값이 32768에서 131072으로 변경되었다.

- [MM_MSGLOG_FILE](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#mm_msglog_file)

  기본값이 1로 변경되었다.

- [PSM_CHAR_DEFAULT_PRECISION](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#psm_char_default_precision)

  기본값이 32767에서 32000으로 변경되었다.

- [PSM_NCHAR_UTF16_DEFAULT_PRECISION](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#psm_nchar_utf16_default_precision)

  기본값이 16383에서 16000으로 변경되었다.

- [PSM_NCHAR_UTF8_DEFAULT_PRECISION](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#psm_nchar_utf8_default_precision)

  기본값이 10921에서 10666으로 변경되었다.

- [PSM_NVARCHAR_UTF16_DEFAULT_PRECISION](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#psm_nvarchar_utf16_default_precision)

  기본값이 16383에서 16000으로 변경되었다.

- [PSM_NVARCHAR_UTF8_DEFAULT_PRECISION](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#psm_nvarchar_utf8_default_precision)

  기본값이 10921에서 10666으로 변경되었다.

- [PSM_VARCHAR_DEFAULT_PRECISION](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#psm_varchar_default_precision)

  기본값이 32767에서 32000으로 변경되었다.

- [REPLICATION_EAGER_PARALLEL_FACTOR](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#replication_eager_parallel_factor)

  최소값이 1에서 2로 변경되었다.

- [SERVER_MSGLOG_FLAG](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#server_msglog_flag)

  기본값이 7에서 15로 변경되었다.

- [TOTAL_WA_SIZE](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#total_wa_size-%EB%8B%A8%EC%9C%84-%EB%B0%94%EC%9D%B4%ED%8A%B8)

  최소값이 0으로 변경되었다.

- [TRANSACTION_SEGMENT_COUNT](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-1.Data%20Types%20%26%20Altibase%20Properties.md#transaction_segment_count-%EB%8B%A8%EC%9C%84--%EA%B0%9C%EC%88%98)

  최대값이 512에서 16384로 변경되었다.

##### Removed Properties

-   GLOBAL_TRANSACTION_LEVEL
-   LOCK_MGR_TYPE
-   LOCK_MGR_SPIN_COUNT
-   LOCK_MGR_MIN_SLEEP
-   LOCK_MGR_MAX_SLEEP
-   LOCK_MGR_DETECTDEADLOCK_INTERVAL
-   TEMP_MAX_PAGE_COUNT
-   TRANSACTION_START_MODE

#### 2.2.5 Meta Tables

##### New Meta Tables

* [SYS_GEOMETRIES_](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-2.The%20Data%20Dictionary.md#sys_geometries_)
* [SYS_GEOMETRY_COLUMNS_](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-2.The%20Data%20Dictionary.md#sys_geometry_columns_)
* [SYS_REPL_RECEIVER_](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-2.The%20Data%20Dictionary.md#sys_repl_receiver_)
* [SYS_REPL_TABLE_OID_IN_USE_](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-2.The%20Data%20Dictionary.md#sys_repl_table_oid_in_use_)
* [USER_SRS_](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-2.The%20Data%20Dictionary.md#user_srs_)

##### Modified Meta Tables

* [SYS_REPLICATIONS_](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-2.The%20Data%20Dictionary.md#sys_repl_hosts_)
  
  New columns have been introduced below.
  
  * REMOTE_LAST_DDL_XSN
  
* [SYS_REPL_HOSTS_](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-2.The%20Data%20Dictionary.md#sys_repl_hosts_)
  
  New columns have been introduced below.
  
  * CONN_TYPE
  * IB_LATENCY
  
* [SYS_REPL_OLD_COLUMNS_](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-2.The%20Data%20Dictionary.md#sys_repl_old_columns_)
  
  New columns have been introduced below.
  
  * MT_SRID
  
* [SYS_REPL_OLD_ITEMS_](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-2.The%20Data%20Dictionary.md#sys_repl_old_items_)
  
  New columns have been introduced below.
  
  * REMOTE_USER_NAME 
  * REMOTE_TABLE_NAME
  * REMOTE_PARTITION_NAME
  * PARTITION_COUNT
  * PARTITION_METHOD
  * PARTITION_ORDER
  * PARTITION_MIN_VALUE
  * PARTITION_MAX_VALUE
  * INVALID_MAX_SN

##### Removed Meta Tables

The following meta tables have been removed.

-   STO_COLUMNS_
-   STO_DATUMS_
-   STO_ELLIPSOIDS_
-   STO_GEOCCS_
-   STO_GEOGCS_
-   STO_PRIMEMS_
-   STO_PROJCS_
-   STO_PROJECTIONS_
-   STO_SRS_
-   STO_USER_COLUMNS_

#### 2.2.6 Performance Views

The following performance views have been added.

For more informaiton on each performance view, please refer to the [**General Reference-2.The Data Dictionary**](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-2.The%20Data%20Dictionary.md).

##### New Performance Views

-   [V$LIBRARY](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-2.The%20Data%20Dictionary.md#vlibrary)
-   [V$PROCINFO](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-2.The%20Data%20Dictionary.md#vprocinfo)
-   [V$QUEUE_DELETE_OFF](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-2.The%20Data%20Dictionary.md#vqueue_delete_off)
-   [V$REPL_REMOTE_META_CHECKS](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-2.The%20Data%20Dictionary.md#vrepl_remote_meta_checks)
-   [V$REPL_REMOTE_META_COLUMNS](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-2.The%20Data%20Dictionary.md#vrepl_remote_meta_columns)
-   [V$REPL_REMOTE_META_INDEX_COLUMNS](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-2.The%20Data%20Dictionary.md#vrepl_remote_meta_index_columns)
-   [V$REPL_REMOTE_META_INDICES](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-2.The%20Data%20Dictionary.md#vrepl_remote_meta_indices)
-   [V$REPL_REMOTE_META_ITEMS](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-2.The%20Data%20Dictionary.md#vrepl_remote_meta_indices)
-   [V$REPL_REMOTE_META_REPLICATIONS](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/General_Reference-2.The%20Data%20Dictionary.md#vrepl_remote_meta_replications)

##### Removed Performance Views

* V$ST_ANGULAR_UNIT
* V$ST_AREA_UNIT
* V$ST_LINEAR_UNIT

</br>

### 2.3 Packages

| OS    | CPU                       | File Names                                                  |
| ----- | ------------------------- | ----------------------------------------------------------- |
| AIX   | PowerPC                   | altibase- server-7.3.0.0.1-AIX-POWERPC-64bit-release.run    |
|       |                           | altibase- client-7.3.0.0.1-AIX-POWERPC-64bit-release.run    |
| HP-UX | IA64                      | altibase- server-7.3.0.0.1-HPUX-IA64-64bit-release.run      |
|       |                           | altibase- client-7.3.0.0.1-HPUX-IA64-64bit-release.run      |
| LINUX | x86-64                    | altibase-server-7.3.0.0.1-LINUX-X86-64bit-release.run       |
|       |                           | altibase-client-7.3.0.0.1-LINUX-X86-64bit-release.run       |
| LINUX | PowerPC                   | altibase-server-7.3.0.0.1-LINUX-POWERPC-64bit-release.run   |
|       |                           | altibase-client-7.3.0.0.1-LINUX-POWERPC-64bit-release.run   |
| LINUX | PowerPCLE (Little Endian) | altibase-server-7.3.0.0.1-LINUX-POWERPCLE-64bit-release.run |
|       |                           | altibase-client-7.3.0.0.1-LINUX-POWERPCLE-64bit-release.run |

</br>

### 2.4 Download

#### Package

http://support.altibase.com

#### Manual

https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/README.md

#### Installation

https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.3/kor/Installation%20Guide.md

------

<a name="shapefile">[1]</a> Shapefile: A file format developed by ESRI, a software developer specializing in Geographic Information Systems (GIS). In the GIS field, the Shapefile is considered a standard file format and consists of the following three essential files.  [↩](#shapefile1)

- shp : contains spatial data information representing points, lines, and shapes in a vector format.
- shx : Index file, which contains the location of the shape information stored in the shp file.
- dbf : dBASE table file containing attribute information about the shape information in the shp file.

References : [Geoprocessing considerations for shapefile output](https://desktop.arcgis.com/en/arcmap/latest/manage-data/shapefiles/geoprocessing-considerations-for-shapefile-output.htm)
