# Altibase 버전 별 Java 호환성

<br/>

<br/>

# Table of Contents

- [개요](#개요)
- [Altibase 7.3](#altibase-73)
- [Altibase 7.1](#altibase-71)
- [Altibase 6.5.1](#altibase-651)
- [Tools](#tools)

<br/>

<br/>

# 개요

자바 기반의 Altibase 라이브러리 및 유틸리티의 자바 버전 별 호환성 여부를 안내하는 페이지입니다. 

자바 호환성 테스트는 Oracle OpenJDK를 대상으로 진행합니다. Oracle JDK, Oracle OpenJDK, IBM SDK 모두 바이너리 호환성을 보장하고 있으므로 벤더 사 구분 없이 호환성 테스트를 마친 자바 버전만 명시합니다.

이 페이지의 표에서 사용한 기호의 의미는 다음과 같습니다. 

**`x`** : 지원하지 않는 버전을 의미합니다.

`●` : 호환성 테스트를 완료한 버전을 의미합니다. 

**`-`** : 호환성 테스트를 진행하지는 않았으며 호환성 여부는 JDK 하위 호환성 정책에 따릅니다. 해당 버전에 대해 Altibase의 호환성 테스트 결과가 필요한 경우 Altibase로 문의하시기 바랍니다. 

<br/>

<br/>

# Altibase 7.3

### Altibase Server Side

| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Java 5 | Java 6 | Java 7 | Java 8 | Java 9 | Java 10 | Java 11 | Java 12 | Java 17 ~ 19 |
| ------------------------------------------------------------ | :----: | :----: | :----: | :----: | :----: | :-----: | :-----: | :-----: | :----------: |
| **altiMon**                                                  |   x    |   x    |   x    |   ●    |   ●    |    ●    |    ●    |    ●    |      ●       |
| **Adapter for JDBC**                                         |   x    |   x    |   x    |   ●    |   ●    |    ●    |    ●    |    ●    |      ●       |
| **DB Link**                                                  |   x    |   x    |   x    |   ●    |   ●    |    ●    |    ●    |    ●    |      ●       |



### Altibase JDBC 드라이버

| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Java 5 | Java 6 ~ Java 7 | Java 8 | Java 9 ~ Java 10 | Java 11 | Java 12 | Java 17 ~ 19 |
| :----------------------------------------------------------- | :----: | :-------------: | :----: | :--------------: | :-----: | :-----: | :----------: |
| **Altibase.jar**                                             |   x    |        x        |   ●    |        ●         |    ●    |    ●    |      ●       |

<br/>

<br/>

# Altibase 7.1

### Altibase Server Side

| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Java 5 | Java 6 | Java 7 | Java 8 | Java 9 | Java 10 | Java 11 | Java 12 | Java 17 ~ 19 |
| ------------------------------------------------------------ | :----: | :----: | :----: | :----: | :----: | :-----: | :-----: | :-----: | :----------: |
| **altiMon**                                                  |   ●    |   ●    |   ●    |   ●    |   ●    |    ●    |  ●[^1]  |    ●    |      ●       |
| **Adapter for JDBC**                                         |   x    |   x    |   ●    |   ●    |   ●    |    ●    |  ●[^2]  |    ●    |      ●       |
| **DB Link**                                                  |   ●    |   ●    |   ●    |   ●    | ●[^3]  |    ●    |    ●    |    ●    |      ●       |

[^1]: altiMon에서 Java 11 이상은 Altibase 7.1.0.2.6부터 지원합니다.
[^2]: Adapter for JDBC에서 Java 11 이상은 Altibase 7.1.0.2.6부터 지원합니다.
[^3]: DB Link에서 Java 9 이상은 Altibase 7.1.0.2.5부터 지원합니다.



### Altibase JDBC 드라이버

| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Java 5 | Java 6 ~ Java 7 | Java 8 | Java 9 ~ Java 10 | Java 11[^4] | Java 12 | Java 17 ~ 19 |
| :----------------------------------------------------------- | :----: | :-------------: | :----: | :--------------: | :---------: | :-----: | :----------: |
| **Altibase.jar**                                             |   ●    |        ●        |   ●    |        ●         |      ●      |    ●    |      ●       |
| **Altibase42.jar**                                           |   x    |        x        |   ●    |        ●         |      ●      |    ●    |      ●       |

[^4]: JDBC 3.0 API를 지원하는 JDBC 드라이버(Altibase.jar)에서 Java 11 이상은 Altibase 7.1.0.2.6부터 지원합니다.

<br/>

<br/>

# Altibase 6.5.1

### Altibase Server Side

| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Java 5 | Java 6 ~ Java 8 | Java 9 | Java 10 | Java 11 | Java 12 | Java 17 ~ 19 |
| ------------------------------------------------------------ | :----: | :-------------: | :----: | :-----: | :-----: | :-----: | :----------: |
| **DB Link**                                                  |   ●    |        ●        | ●[^5]  |    ●    |    ●    |    ●    |      ●       |

[^5]: DB Link에서 Java 9 이상은 Altibase 6.5.1.6.6부터 지원합니다.



### Altibase JDBC Driver

| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | **Java 4** | Java 5 ~  Java 8 | Java 9 | Java 10 | Java 11 | Java 12 | Java 17 ~ 19 |
| ------------------------------------------------------------ | :--------: | :--------------: | :----: | :-----: | :-----: | :-----: | :----------: |
| **JDBC 드라이버**                                            |     ●      |        ●         |   ●    |    ●    |  ●[^6]  |    ●    |      ●       |

[^6]: JDBC 드라이버에서 Java 11 이상은 Altibase 6.5.1.6.6부터 지원합니다.

<br/>

<br/>

# Tools

| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | Java 6 | Java 7 | Java 8 | Java 9 ~ Java 10 | Java 11 | Java 12 | Java 17 | Java 18 |
| ------------------------------------------------------------ | :----: | :----: | :----: | :--------------: | :-----: | :-----: | :-----: | :-----: |
| **altiShapeLoader 1.0**                                      |   x    |   x    |   ●    |        ●         |    ●    |    ●    |    -    |    ●    |
| **Altibase Hadoop Connector**                                |   ●    |   ●    |   ●    |        ●         |    -    |    -    |    -    |    -    |
| **dataCompJ 7.2**                                            |   x    |   x    | ●[^7]  |        ●         |  ●[^8]  |    ●    |    -    |    ●    |
| **Migration Center 7.10**                                    |        |        |        |                  |         |         |         |         |
| &nbsp;&nbsp;&nbsp;&nbsp;**Linux 및 Unix**                    |   x    |   x    | ●[^9]  |        ●         | ●[^10]  |    ●    |    -    |    ●    |
| &nbsp;&nbsp;&nbsp;&nbsp;**Windows**[^11]                     |        |        |        |                  |         |         |         |         |
| **Replication Manager**[^11]                                 |        |        |        |                  |         |         |         |         |

[^7]: dataCompJ 7.2부터 최소 자바 버전이 Java 8로 변경되었습니다.
[^8]: dataCompJ 에서 Java 11 이상은 dataComJ 7.1 부터 지원합니다.
[^9]: Migration Center 7.9부터 최소 버전이 Java 8로 변경되었습니다.
[^10]: Migration Center에서 Java 11 이상은 Migration Center 7.8 부터 지원합니다.
[^11]: Migration Center Windows 용과 Replication Manager는 제품 내에 JRE 번들을 제공하고 있어 자바 버전에 영향을 받지 않습니다.

<br/>
