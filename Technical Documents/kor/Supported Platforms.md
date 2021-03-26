
**Table of Contents** 

- [Altibase 버전 별 지원 플랫폼](#altibase-%EB%B2%84%EC%A0%84-%EB%B3%84-%EC%A7%80%EC%9B%90-%ED%94%8C%EB%9E%AB%ED%8F%BC)
  - [Altibase 7.1](#altibase-71)
    - [지원 플랫폼](#%EC%A7%80%EC%9B%90-%ED%94%8C%EB%9E%AB%ED%8F%BC)
    - [Altibase 7.1 Java 호환성](#altibase-71-java-%ED%98%B8%ED%99%98%EC%84%B1)
      - [Oracle JDK / IBM Java](#oracle-jdk--ibm-java)
      - [OpenJDK](#openjdk)
  - [Altibase 6.5.1](#altibase-651)
    - [지원 플랫폼](#%EC%A7%80%EC%9B%90-%ED%94%8C%EB%9E%AB%ED%8F%BC-1)
    - [Altibase 6.5.1 Java 호환성](#altibase-651-java-%ED%98%B8%ED%99%98%EC%84%B1)
      - [Oracle JDK / IBM Java](#oracle-jdk--ibm-java-1)
      - [OpenJDK](#openjdk-1)



# Altibase 버전 별 지원 플랫폼



## Altibase 7.1

### 지원 플랫폼

Altibase 7.1 지원 플랫폼은 [Altibase 7.1 Installation 매뉴얼](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Installation.md#지원-플랫폼) 을 참고하세요. 

### Altibase 7.1 Java 호환성

#### Oracle JDK / IBM Java

|                      | JDK 4 | JDK 5 | JDK 6 | JDK 7 |
| :------------------- | :---: | :---: | :---: | :---: |
| **JDBC Driver**      |   ●   |   ●   |       |       |
| **DB Link**          |   ●   |   ●   |       |       |
| **Adapter for JDBC** | **X** | **X** | **X** |   ●   |
| **altiMon**          | **X** |   ●   |       |       |

#### OpenJDK

> *Altibase 7.1.0.2.6 이상에서 호환성 보장*

|                      | JDK 11 | JDK 12 |
| :------------------- | :----: | :----: |
| **JDBC Driver**      |   ●    |   ●    |
| **DB Link**          |   ●    |   ●    |
| **Adapter for JDBC** |   ●    |   ●    |
| **altiMon**          |   ●    |   ●    |









## Altibase 6.5.1

### 지원 플랫폼

> Altibase 서버는 64비트만 지원합니다.


|                           | Altibase 서버<br /> | Altibase 클라이언트<br />32비트 | Altibase 클라이언트<br />64비트 | 소프트웨어 요구사항 |
| ------------------------- | :-----------------: | :-----------------------------: | :-----------------------------: | ------------------- |
| **AIX on IBM Power Systems** |                     |                                 |                                 |                     |
| AIX 6.1 TL3<br />AIX 6.1  TL9<br />AIX 7.1 |          ●          |                ●                |                ●                |                     |
| **HP-UX Itanium (IA-64)** |                     |                                 |                                 |                     |
| HP-UX 11.31               | ● | ● | ● |                     |
|**Linux x86-64**|||||
|Red Hat Enterprise Linux 6<br/>Red Hat Enterprise Linux 7<br/>Red Hat Enterprise Linux 8|●|●|●|*- glibc 2.12 이상*|
|**Linux on Power**|||||
|POWER7 Red Hat Enterprise Linux 6<br/>POWER7 Red Hat Enterprise Linux 7|●|-|●||
|POWER8 Red Hat Enterprise Linux 6<br/>POWER8 Red Hat Enterprise Linux 7|●|-|●||
|**Linux on Power (Little Endian)**|||●||
|POWER8(LE) Red Hat Enterprise Linux 7|●|-||*\- Altibase 6.5.1.4.5 이상*<br />*- glibc 2.17 이상*|
|POWER9(LE) Red Hat Enterprise Linux 7|●|-|●|*\- Altibase 6.5.1.7.1 이상*<br />*- glibc 2.17 이상*|
|**Oracle Solaris (Sparc)**|||||
|Solaris 10|●|●|●||
|Solaris 11|●|●|●|*- Altibase* *6.5.1.4.2 이상*|
|**Microsoft Windows (x64)**|||||
|Microsoft Windows Server 2008<br/>Microsoft Windows Server 2012<br/>Microsoft Windows Server 2016<br/>Microsoft Windows Server 2019|●|●|●|*- Altibase 서버 6.5.1.7.7 이상 권장*|
|Microsoft Windows 7<br/>Microsoft Windows 8|●|●|●||
|Microsoft Windows 10|●|●|●|*- Altibase 클라이언트 6.5.1.6.2 이상*|



### Altibase 6.5.1 Java 호환성

#### Oracle JDK / IBM Java

|                 | JDK 4 | JDK 5 |
| :-------------- | :---: | :---: |
| **JDBC Driver** |   ●   |   ●   |
| **DB Link**     |   ●   |   ●   |

#### OpenJDK

> *Altibase 6.5.1.6.6 이상에서 호환성 보장*

|                 | JDK 11 | JDK 12 |
| :-------------- | :----: | :----: |
| **JDBC Driver** |   ●    |   ●    |
| **DB Link**     |   ●    |   ●    |

