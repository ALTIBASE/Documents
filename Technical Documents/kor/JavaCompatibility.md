# Altibase 버전 별 Java 호환성



# **Table of Contents** 

- [Altibase 버전 별 Java 호환성](#altibase-%EB%B2%84%EC%A0%84-%EB%B3%84-java-%ED%98%B8%ED%99%98%EC%84%B1)
- [Altibase 7.2](#altibase-72)
- [Altibase 7.1](#altibase-71)
- [Altibase 6.5.1](#altibase-651)

<br/>

<br/>

# Altibase 7.2

### Altibase Server Side

|             | Java 8 (LTS) | Java 9 | Java 10 | Java 11 (LTS) | Java 12 | Java 17 (LTS) | 참고 사항 |
| ----------- | :----------: | :----: | :-----: | :-----------: | :-----: | :-----------: | --------- |
| **DB Link** |      ●       |   ●    |    ●    |       ●       |    ●    |       -       |           |
| **altiMon** |      ●       |   ●    |    ●    |       ●       |    ●    |       -       |           |

### Altibase JDBC Driver

|                                          | Java 8 (LTS) | Java 9 | Java 10 | Java 11 (LTS) | Java 12 | Java 17 (LTS) | 참고 사항 |
| ---------------------------------------- | :----------: | :----: | :-----: | :-----------: | :-----: | :-----------: | --------- |
| **JDBC 4.2 API 부분 지원(Altibase.jar)** |      ●       |   ●    |    ●    |       ●       |    ●    |       -       |           |

### Tools

|                          | Java 8 (LTS) | Java 9 | Java 10 | Java 11 (LTS) | Java 12 | Java 17 (LTS) | 참고 사항                 |
| ------------------------ | :----------: | :----: | :-----: | :-----------: | :-----: | :-----------: | ------------------------- |
| **Adapter for JDBC**     |      ●       |   ●    |    ●    |       ●       |    ●    |       -       |                           |
| **dataCompJ 7.2**        |      ●       |   ●    |    ●    |       ●       |    ●    |       -       |                           |
| **Migration Center 7.9** |      ●       |   ●    |    ●    |       ●       |    ●    |       -       |                           |
| **Linux 및 Unix**        |      ●       |   ●    |    ●    |       ●       |    ●    |       -       |                           |
| **Windows**              |              |        |         |               |         |               | - *무관. JRE 8 번들 제공* |
| **altiShapeLoader 1.0**  |      ●       |   ●    |    ●    |       ●       |    ●    |       -       |                           |
| **Replication Manager**  |              |        |         |               |         |               | - *무관. JRE 6 번들 제공* |

<br/>

<br/>

# Altibase 7.1

### Altibase Server Side

|             | Java 5 ~ Java 7 | Java 8 (LTS) | Java 9 | Java 10 | Java 11 (LTS) | Java 12 | Java 17 (LTS) | 참고 사항                                       |
| ----------- | :-------------: | :----------: | :----: | :-----: | :-----------: | :-----: | :-----------: | :---------------------------------------------- |
| **DB Link** |        ●        |      ●       |   ●    |    ●    |       ●       |    ●    |       -       | - *Java 9 이상은 Altibase 7.1.0.2.5 부터 지원*  |
| **altiMon** |        ●        |      ●       |   ●    |    ●    |       ●       |    ●    |       -       | - *Java 11 이상은 Altibase 7.1.0.2.6 부터 지원* |

### Altibase JDBC Driver

|                                             | Java 5 ~ Java 7 | Java 8 (LTS) | Java 9 | Java 10 | Java 11 (LTS) | Java 12 | Java 17 (LTS) | 참고 사항                                       |
| ------------------------------------------- | --------------- | ------------ | ------ | ------- | ------------- | ------- | ------------- | ----------------------------------------------- |
| **JDBC 3.0 API 지원 (Altibase.jar)**        | ●               | ●            | ●      | ●       | ●             | ●       | -             | - *Java 11 이상은 Altibase 7.1.0.2.6 부터 지원* |
| **JDBC 4.2 API 부분 지원 (Altibase42.jar)** |                 | ●            | ●      | ●       | ●             | ●       | -             | - *Altibase 7.1.0.5.6 부터 지원*                |

### Tools

|                               | Java 6 | Java 7 (LTS) | Java 8 (LTS) | Java 9 ~ Java 10 | Java 11 (LTS) | Java 12 | Java 17 (LTS) | 참고 사항                                                    |
| ----------------------------- | :----: | :----------: | :----------: | :--------------: | :-----------: | :-----: | :-----------: | ------------------------------------------------------------ |
| **Adapter for JDBC**          |        |      ●       |      ●       |        ●         |       ●       |    ●    |       -       | - *Java 11 이상은 Altibase 7.0.1.2.6 부터 지원*              |
| **dataCompJ 7.2**             |        |              |      ●       |        ●         |       ●       |    ●    |       -       | - *Java 11 이상은 dataComJ 7.1 부터 지원*<br />- *dataCompJ 7.2 부터 최소 버전이 Java 8로 변경됨* |
| **Migration Center 7.9**      |        |              |              |                  |               |         |               |                                                              |
| ***Linux 및 Unix***           |        |              |      ●       |        ●         |       ●       |    ●    |       -       | - *Java 11 이상은 Migration Center 7.8 부터 지원*<br />- *Migration Center 7.9 부터 최소 버전이 Java 8로 변경됨* |
| ***Windows***                 |        |              |              |                  |               |         |               | - *무관. JRE 8 번들 제공*                                    |
| **altiShapeLoader 1.0**       |        |              |      ●       |        ●         |       ●       |    ●    |       -       |                                                              |
| **Altibase Hadoop Connector** |   ●    |      ●       |      ●       |        ●         |       -       |    -    |       -       |                                                              |
| **Replication Manager**       |        |              |              |                  |               |         |               | - *무관. JRE 6 번들 제공*                                    |

<br/>

<br/>

# Altibase 6.5.1

### Altibase Server Side

|             | Java 5 ~ Java 7 | Java 8 (LTS) | Java 9 | Java 10 | Java 11 (LTS) | Java 12 | Java 17 (LTS) | 참고 사항                                      |
| ----------- | :-------------: | :----------: | :----: | :-----: | :-----------: | :-----: | :-----------: | :--------------------------------------------- |
| **DB Link** |        ●        |      ●       |   ●    |    ●    |       ●       |    ●    |       -       | - *Java 9 이상은 Altibase 6.5.1.6.6 부터 지원* |

### Altibase JDBC Driver

|                                          | **Java 4 ~ Java 7 (LTS) ** | Java 8 (LTS) | Java 9 | Java 10 | Java 11 (LTS) | Java 12 | Java 17 (LTS) | 참고 사항 |
| ---------------------------------------- | :------------------------: | :----------: | :----: | :-----: | :-----------: | :-----: | :-----------: | --------- |
| **JDBC 4.2 API 부분 지원(Altibase.jar)** |             ●              |      ●       |   ●    |    ●    |       ●       |    ●    |       -       |           |

### Tools

|                               | Java 6 | Java 7 (LTS) | Java 8 (LTS) | Java 9 ~ Java 10 | Java 11 (LTS) | Java 12 | Java 17 (LTS) | 참고 사항                                                    |
| ----------------------------- | :----: | :----------: | :----------: | :--------------: | :-----------: | :-----: | :-----------: | ------------------------------------------------------------ |
| **dataCompJ 7.2**             |        |              |      ●       |        ●         |       ●       |    ●    |       -       | - *Java 11 이상은 dataComJ 7.1 부터 지원*<br />- *dataCompJ 7.2 부터 최소 버전이 Java 8로 변경됨* |
| **Migration Center 7.9**      |        |              |              |                  |               |         |               |                                                              |
| ***Linux 및 Unix***           |        |              |      ●       |        ●         |       ●       |    ●    |       -       | - *Java 11 이상은 Migration Center 7.8 부터 지원*<br />- *Migration Center 7.9 부터 최소 버전이 Java 8로 변경됨* |
| ***Windows***                 |        |              |              |                  |               |         |               | - *무관. JRE 8 번들 제공*                                    |
| **Altibase Hadoop Connector** |   ●    |      ●       |      ●       |        ●         |       -       |    -    |       -       |                                                              |
| **Replication Manager**       |        |              |              |                  |               |         |               | - *무관. JRE 6 번들 제공*                                    |

<table style="undefined;table-layout: fixed; width: 1443px;"><colgroup> <col style="width: 25px;" /> <col style="width: 25px;" /> <col style="width: 193px;" /> <col style="width: 98px;" /> <col style="width: 83px;" /> <col style="width: 87px;" /> <col style="width: 113px;" /> <col style="width: 105px;" /> <col style="width: 99px;" /> <col style="width: 99px;" /> <col style="width: 99px;" /> <col style="width: 417px;" /> </colgroup>
<thead>
<tr>
<th colspan="3">&nbsp;</th>
<th>Java 4</th>
<th>Java 5</th>
<th>Java 6</th>
<th>Java 7 (LTS)</th>
<th>Java 8 (LTS) ~ Java 10</th>
<th>Java 11</th>
<th>Java 12</th>
<th>Java 17 (LTS)</th>
<th style="text-align: left;">참고 사항</th>
</tr>
</thead>
<tbody>
<tr>
<td colspan="3"><strong>Altibase Server Side</strong></td>
<td style="text-align: center;">&nbsp;</td>
<td style="text-align: center;">&nbsp;</td>
<td style="text-align: center;">&nbsp;</td>
<td style="text-align: center;">&nbsp;</td>
<td style="text-align: center;">&nbsp;</td>
<td style="text-align: center;">&nbsp;</td>
<td style="text-align: center;">&nbsp;</td>
<td style="text-align: center;">&nbsp;</td>
<td>&nbsp;</td>
</tr>
<tr>
<td>&nbsp;</td>
<td colspan="2"><strong>DB Link</strong></td>
<td style="text-align: center;">&nbsp;</td>
<td style="text-align: center;">●</td>
<td style="text-align: center;">●</td>
<td style="text-align: center;">●</td>
<td style="text-align: center;">●</td>
<td style="text-align: center;">●</td>
<td style="text-align: center;">●</td>
<td style="text-align: center;">-</td>
<td>- Java 9 이상은 Altibase 6.5.1.6.6 부터 지원</td>
</tr>
<tr>
<td colspan="3"><strong>Altibase JDBC Driver</strong></td>
<td style="text-align: center;">&nbsp;</td>
<td style="text-align: center;">&nbsp;</td>
<td style="text-align: center;">&nbsp;</td>
<td style="text-align: center;">&nbsp;</td>
<td style="text-align: center;">&nbsp;</td>
<td style="text-align: center;">&nbsp;</td>
<td style="text-align: center;">&nbsp;</td>
<td style="text-align: center;">&nbsp;</td>
<td>&nbsp;</td>
</tr>
<tr>
<td>&nbsp;</td>
<td colspan="2"><strong>JDBC 3.0 API 지원 (Altbase.jar)</strong></td>
<td style="text-align: center;">●</td>
<td style="text-align: center;">●</td>
<td style="text-align: center;">●</td>
<td style="text-align: center;">●</td>
<td style="text-align: center;">●</td>
<td style="text-align: center;">●</td>
<td style="text-align: center;">●</td>
<td style="text-align: center;">-</td>
<td>- Java 11 이상은 Altibase 6.5.1.6.6 부터 지원</td>
</tr>
<tr>
<td colspan="3"><strong>Tools</strong></td>
<td style="text-align: center;">&nbsp;</td>
<td style="text-align: center;">&nbsp;</td>
<td style="text-align: center;">&nbsp;</td>
<td style="text-align: center;">&nbsp;</td>
<td style="text-align: center;">&nbsp;</td>
<td style="text-align: center;">&nbsp;</td>
<td style="text-align: center;">&nbsp;</td>
<td style="text-align: center;">&nbsp;</td>
<td>&nbsp;</td>
</tr>
<tr>
<td>&nbsp;</td>
<td colspan="2"><strong>dataCompJ 7.2</strong></td>
<td style="text-align: center;">&nbsp;</td>
<td style="text-align: center;">&nbsp;</td>
<td style="text-align: center;">&nbsp;</td>
<td style="text-align: center;">&nbsp;</td>
<td style="text-align: center;">●</td>
<td style="text-align: center;">●</td>
<td style="text-align: center;">●</td>
<td style="text-align: center;">-</td>
<td>- Java 11 이상은 dataCompJ 7.1부터 지원<br />- dataCompJ 7.2부터 최소 버전이 Java 8로 변경</td>
</tr>
<tr>
<td>&nbsp;</td>
<td colspan="2"><strong>Migration Center 7.9</strong></td>
<td style="text-align: center;">&nbsp;</td>
<td style="text-align: center;">&nbsp;</td>
<td style="text-align: center;">&nbsp;</td>
<td style="text-align: center;">&nbsp;</td>
<td style="text-align: center;">&nbsp;</td>
<td style="text-align: center;">&nbsp;</td>
<td style="text-align: center;">&nbsp;</td>
<td style="text-align: center;">-</td>
<td>&nbsp;</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>&nbsp;</td>
<td><strong>Linux 및 Unix</strong></td>
<td style="text-align: center;">&nbsp;</td>
<td style="text-align: center;">&nbsp;</td>
<td style="text-align: center;">&nbsp;</td>
<td style="text-align: center;">●</td>
<td style="text-align: center;">●</td>
<td style="text-align: center;">●</td>
<td style="text-align: center;">●</td>
<td style="text-align: center;">-</td>
<td>- Java 11이상은 Migration Center 7.8부터 지원<br />- Migration Center 7.9부터 최소 버전이 Java 8로 변경</td>
</tr>
<tr>
<td>&nbsp;</td>
<td>&nbsp;</td>
<td><strong>Windows</strong></td>
<td style="text-align: center;" colspan="8">무관</td>
<td>- JRE 8 번들 제공</td>
</tr>
<tr>
<td>&nbsp;</td>
<td colspan="2"><strong>Altibase Hadoop Connector</strong></td>
<td style="text-align: center;">&nbsp;</td>
<td style="text-align: center;">&nbsp;</td>
<td style="text-align: center;">●</td>
<td style="text-align: center;">●</td>
<td style="text-align: center;">●</td>
<td style="text-align: center;">-</td>
<td style="text-align: center;">-</td>
<td style="text-align: center;">-</td>
<td>&nbsp;</td>
</tr>
<tr>
<td>&nbsp;</td>
<td colspan="2"><strong>Replication Manager</strong></td>
<td style="text-align: center;" colspan="8">무관</td>
<td>- JRE 6 번들 제공</td>
</tr>
</tbody>
</table>
