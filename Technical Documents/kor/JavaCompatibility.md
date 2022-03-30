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

<style type="text/css">
.tg  {border-collapse:collapse;border-color:#ccc;border-spacing:0;margin:0px auto;}
.tg td{background-color:#fff;border-color:#ccc;border-style:solid;border-width:1px;color:#333;
  font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{background-color:#f0f0f0;border-color:#ccc;border-style:solid;border-width:1px;color:#333;
  font-family:Arial, sans-serif;font-size:14px;font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-m5nv{border-color:#656565;text-align:center;vertical-align:top}
.tg .tg-di1h{border-color:#656565;text-align:center;vertical-align:middle}
.tg .tg-7z3s{border-color:#656565;font-weight:bold;text-align:left;vertical-align:middle}
.tg .tg-c9og{background-color:#efefef;border-color:#656565;font-weight:bold;text-align:left;vertical-align:top}
.tg .tg-c3ow{border-color:inherit;text-align:center;vertical-align:top}
.tg .tg-2bev{border-color:#656565;text-align:left;vertical-align:top}
.tg .tg-zx7a{background-color:#f0f0f0;border-color:#cccccc;font-weight:bold;text-align:center;vertical-align:top}
.tg .tg-5keg{background-color:#f0f0f0;border-color:#cccccc;font-weight:bold;text-align:left;vertical-align:top}
.tg .tg-rev3{background-color:#efefef;border-color:#656565;text-align:center;vertical-align:top}
.tg .tg-zs35{background-color:#efefef;border-color:#656565;text-align:left;vertical-align:top}
.tg .tg-hkgo{border-color:#656565;font-weight:bold;text-align:left;vertical-align:top}
.tg .tg-g7sd{border-color:inherit;font-weight:bold;text-align:left;vertical-align:middle}
.tg .tg-fymr{border-color:inherit;font-weight:bold;text-align:left;vertical-align:top}
.tg .tg-0pky{border-color:inherit;text-align:left;vertical-align:top}
</style>
<table class="tg" style="undefined;table-layout: fixed; width: 1443px">
<colgroup>
<col style="width: 25px">
<col style="width: 25px">
<col style="width: 193px">
<col style="width: 98px">
<col style="width: 83px">
<col style="width: 87px">
<col style="width: 113px">
<col style="width: 105px">
<col style="width: 99px">
<col style="width: 99px">
<col style="width: 99px">
<col style="width: 417px">
</colgroup>
<thead>
  <tr>
    <th class="tg-2bev" colspan="3"></th>
    <th class="tg-zx7a">Java 4</th>
    <th class="tg-zx7a">Java 5</th>
    <th class="tg-zx7a">Java 6</th>
    <th class="tg-zx7a">Java 7 (LTS)</th>
    <th class="tg-zx7a">Java 8 (LTS) ~ Java 10</th>
    <th class="tg-zx7a">Java  11</th>
    <th class="tg-zx7a">Java 12</th>
    <th class="tg-zx7a">Java 17 (LTS)</th>
    <th class="tg-5keg">참고 사항</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-c9og" colspan="3">Altibase Server Side</td>
    <td class="tg-rev3"></td>
    <td class="tg-rev3"></td>
    <td class="tg-rev3"></td>
    <td class="tg-rev3"></td>
    <td class="tg-rev3"></td>
    <td class="tg-rev3"></td>
    <td class="tg-rev3"></td>
    <td class="tg-rev3"></td>
    <td class="tg-zs35"></td>
  </tr>
  <tr>
    <td class="tg-2bev"></td>
    <td class="tg-hkgo" colspan="2">DB Link</td>
    <td class="tg-m5nv"></td>
    <td class="tg-m5nv">●</td>
    <td class="tg-m5nv">●</td>
    <td class="tg-m5nv">●</td>
    <td class="tg-m5nv">●</td>
    <td class="tg-m5nv">●</td>
    <td class="tg-m5nv">●</td>
    <td class="tg-m5nv">-</td>
    <td class="tg-2bev">- Java 9 이상은 Altibase 6.5.1.6.6 부터 지원</td>
  </tr>
  <tr>
    <td class="tg-c9og" colspan="3">Altibase JDBC Driver         </td>
    <td class="tg-rev3"></td>
    <td class="tg-rev3"></td>
    <td class="tg-rev3"></td>
    <td class="tg-rev3"></td>
    <td class="tg-rev3"></td>
    <td class="tg-rev3"></td>
    <td class="tg-rev3"></td>
    <td class="tg-rev3"></td>
    <td class="tg-zs35"></td>
  </tr>
  <tr>
    <td class="tg-2bev"></td>
    <td class="tg-hkgo" colspan="2">JDBC 3.0 API 지원 (Altbase.jar)</td>
    <td class="tg-m5nv">●</td>
    <td class="tg-m5nv">●</td>
    <td class="tg-m5nv">●</td>
    <td class="tg-m5nv">●</td>
    <td class="tg-m5nv">●</td>
    <td class="tg-m5nv">●</td>
    <td class="tg-m5nv">●</td>
    <td class="tg-m5nv">-</td>
    <td class="tg-2bev">- Java 11 이상은 Altibase 6.5.1.6.6 부터 지원</td>
  </tr>
  <tr>
    <td class="tg-c9og" colspan="3">Tools</td>
    <td class="tg-rev3"></td>
    <td class="tg-rev3"></td>
    <td class="tg-rev3"></td>
    <td class="tg-rev3"></td>
    <td class="tg-rev3"></td>
    <td class="tg-rev3"></td>
    <td class="tg-rev3"></td>
    <td class="tg-rev3"></td>
    <td class="tg-zs35"></td>
  </tr>
  <tr>
    <td class="tg-2bev"></td>
    <td class="tg-7z3s" colspan="2">dataCompJ 7.2</td>
    <td class="tg-m5nv"></td>
    <td class="tg-m5nv"></td>
    <td class="tg-m5nv"></td>
    <td class="tg-m5nv"></td>
    <td class="tg-di1h">●</td>
    <td class="tg-di1h">●</td>
    <td class="tg-di1h">●</td>
    <td class="tg-di1h">-</td>
    <td class="tg-2bev">- Java 11 이상은 dataCompJ 7.1부터 지원<br>- dataCompJ 7.2부터 최소 버전이 Java 8로 변경</td>
  </tr>
  <tr>
    <td class="tg-2bev"></td>
    <td class="tg-hkgo" colspan="2">Migration Center 7.9</td>
    <td class="tg-m5nv"></td>
    <td class="tg-m5nv"></td>
    <td class="tg-m5nv"></td>
    <td class="tg-m5nv"></td>
    <td class="tg-m5nv"></td>
    <td class="tg-m5nv"></td>
    <td class="tg-m5nv"></td>
    <td class="tg-m5nv">-</td>
    <td class="tg-2bev"></td>
  </tr>
  <tr>
    <td class="tg-2bev"></td>
    <td class="tg-hkgo"></td>
    <td class="tg-g7sd">Linux 및 Unix</td>
    <td class="tg-m5nv"></td>
    <td class="tg-m5nv"></td>
    <td class="tg-m5nv"></td>
    <td class="tg-di1h">●</td>
    <td class="tg-di1h">●</td>
    <td class="tg-di1h">●</td>
    <td class="tg-di1h">●</td>
    <td class="tg-m5nv">-</td>
    <td class="tg-2bev">- Java 11이상은 Migration Center 7.8부터 지원<br>- Migration Center 7.9부터 최소 버전이 Java 8로 변경</td>
  </tr>
  <tr>
    <td class="tg-2bev"></td>
    <td class="tg-hkgo"></td>
    <td class="tg-fymr">Windows</td>
    <td class="tg-m5nv" colspan="8">무관</td>
    <td class="tg-2bev">- JRE 8 번들 제공</td>
  </tr>
  <tr>
    <td class="tg-0pky"></td>
    <td class="tg-fymr" colspan="2">Altibase Hadoop Connector</td>
    <td class="tg-c3ow"></td>
    <td class="tg-c3ow"></td>
    <td class="tg-c3ow">●</td>
    <td class="tg-c3ow">●</td>
    <td class="tg-c3ow">●</td>
    <td class="tg-c3ow">-</td>
    <td class="tg-c3ow">-</td>
    <td class="tg-c3ow">-</td>
    <td class="tg-0pky"></td>
  </tr>
  <tr>
    <td class="tg-0pky"></td>
    <td class="tg-fymr" colspan="2">Replication Manager</td>
    <td class="tg-c3ow" colspan="8">무관</td>
    <td class="tg-0pky">- JRE 6 번들 제공</td>
  </tr>
</tbody>
</table>
