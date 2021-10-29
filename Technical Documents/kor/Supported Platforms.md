<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents** 

- [Altibase 버전 별 지원 플랫폼](#altibase-%EB%B2%84%EC%A0%84-%EB%B3%84-%EC%A7%80%EC%9B%90-%ED%94%8C%EB%9E%AB%ED%8F%BC)
  - [Altibase 7.1](#altibase-71)
  - [Altibase 6.5.1](#altibase-651)

  

<!-- END doctoc generated TOC please keep comment here to allow auto update -->



# Altibase 버전 별 지원 플랫폼

## Altibase 7.2

>  *Altibase 서버/클라이언트 모두 64-bit 만 지원합니다.*<br>
>
>  **Ubuntu, Fedora, openSUSE 등 아래 표에서 포함하지 않은 리눅스 배포판은 공식 지원 대상이 아니므로 호환성을 보장하지 않습니다.**


|                                                              | Altibase 서버<br /> | Altibase 클라이언트<br /> | 소프트웨어 요구사항                                          |
| ------------------------------------------------------------ | :-----------------: | :-----------------------: | :----------------------------------------------------------- |
| **Linux x86-64**                                             |                     |                           |                                                              |
| Red Hat Enterprise Linux 6.x<br/>Red Hat Enterprise Linux 7.x<br/>Red Hat Enterprise Linux 8.x /><br />CentOS 6.x<br/>CentOS 7.x<br/>CentOS 8.x<br /><br />Oracle Linux 6.x<br/>Oracle Linux 7.x<br/>Oracle Linux 8.x |          ●          |             ●             | *- GNU glibc 2.12 이상*<br />- Altibase JDBC Driver : JRE 1.8 이상 |



## Altibase 7.1

>  *Altibase 서버/클라이언트 모두 64-bit 만 지원합니다.*<br>*Microsoft Windows 는 Altibase 클라이언트만 지원합니다.*
>
>  *Altibase 7.1 패치 버전을 명시하지 않은 경우 Altibase 7.1 모든 버전에서 지원함을 의미합니다.*
>
>  **Ubuntu, Fedora, openSUSE 등 아래 표에서 포함하지 않은 리눅스 배포판은 공식 지원 대상이 아니므로 호환성을 보장하지 않습니다.**


|                                                              | Altibase 서버<br /> | Altibase 클라이언트<br /> | 소프트웨어 요구사항                                      |
| ------------------------------------------------------------ | :-----------------: | :-----------------------: | :------------------------------------------------------- |
| **AIX on IBM Power Systems**                                 |                     |                           |                                                          |
| AIX 6.1 TL3 <br />AIX 6.1 TL9<br />                          |          ●          |             ●             |                                                          |
| AIX 7.1<br />AIX 7.2                                         |          ●          |             ●             | *- AIX 7.2 경우 Altibase 7.1.0.4.7 이상*                 |
| **HP-UX Itanium (IA-64)**                                    |                     |                           |                                                          |
| HP-UX 11.31                                                  |          ●          |             ●             |                                                          |
| **Linux x86-64**                                             |                     |                           |                                                          |
| Red Hat Enterprise Linux 6.x<br/>Red Hat Enterprise Linux 7.x<br/>Red Hat Enterprise Linux 8.x<br /><br />CentOS 6.x<br/>CentOS 7.x<br/>CentOS 8.1<br/>CentOS 8.2<br/>CentOS 8.3<br /><br />Oracle Linux 6.5<br/>Oracle Linux 6.6<br/>Oracle Linux 7.1<br/>Oracle Linux 7.2<br/>Oracle Linux 7.4<br />Oracle Linux 7.9<br />Oracle Linux 8.4 |          ●          |             ●             | *- GNU glibc 2.12 이상*                                  |
| **Linux on Power**                                           |                     |                           |                                                          |
| POWER7 Red Hat Enterprise Linux 6.5<br/>POWER7 Red Hat Enterprise Linux 7.1<br />POWER8 Red Hat Enterprise Linux 6.5<br/>POWER8 Red Hat Enterprise Linux 7.1 |          ●          |             ●             | *- GNU glibc 2.12 이상*                                  |
| **Linux on Power** **(Little Endian)**                       |                     |                           |                                                          |
| POWER8(LE) Red Hat Enterprise Linux 7.2                      |          ●          |             ●             | *- GNU glibc 2.17 이상*<br />- *Altibase 7.1.0.3.6 이상* |
| **Microsoft Windows (x64)**                                  |                     |                           |                                                          |
| Microsoft Windows 2008                                       |        **X**        |             ●             | *- Altibase 클라이언트 7.1.0.4.5 이상*                   |



## Altibase 6.5.1

> *Altibase 서버는 64비트만 지원합니다.*
>
> *Altibase 6.5.1 패치 버전을 명시하지 않은 경우 Altibase 6.5.1 모든 버전에서 지원함을 의미합니다.*
>
> **Ubuntu, Fedora, openSUSE 등 아래 표에서 포함하지 않은 리눅스 배포판은 공식 지원 대상이 아니므로 호환성을 보장하지 않습니다.**


|                           | Altibase 서버<br /> | Altibase 클라이언트<br />32비트 | Altibase 클라이언트<br />64비트 | 소프트웨어 요구사항 |
| ------------------------- | :-----------------: | :-----------------------------: | :-----------------------------: | ------------------- |
| **AIX on IBM Power Systems** |                     |                                 |                                 |                     |
| AIX 6.1 TL3<br />AIX 6.1  TL9<br />AIX 7.1 |          ●          |                ●                |                ●                |                     |
| **HP-UX Itanium (IA-64)** |                     |                                 |                                 |                     |
| HP-UX 11.31               | ● | ● | ● |                     |
|**Linux x86-64**|||||
|Red Hat Enterprise Linux 6.x<br/>Red Hat Enterprise Linux 7.8<br/>Red Hat Enterprise Linux 8.x<br /><br />CentOS 6.x<br/>CentOS 7.8<br/>CentOS 8.1<br/>CentOS 8.2<br/>CentOS 8.3<br /><br />Oracle Linux 6.5<br/>Oracle Linux 6.6<br/>Oracle Linux 7.1<br/>Oracle Linux 7.2<br/>Oracle Linux 7.4<br />Oracle Linux 7.9<br />Oracle Linux 8.4|●|●|●|*- glibc 2.12 이상*|
|**Linux on Power**|||||
|POWER7 Red Hat Enterprise Linux 6.5<br/>POWER7 Red Hat Enterprise Linux 7.1|●|-|●|*- glibc 2.12 이상*|
|POWER8 Red Hat Enterprise Linux 6.5<br/>POWER8 Red Hat Enterprise Linux 7.1|●|-|●|*- glibc 2.12 이상*|
|**Linux on Power (Little Endian)**|||●||
|POWER8(LE) Red Hat Enterprise Linux 7.2|●|-|●|*- glibc 2.17 이상*<br />*- Altibase 6.5.1.4.5 이상*|
|POWER9(LE) Red Hat Enterprise Linux 7.6|●|-|●|*- glibc 2.17 이상*<br />*- Altibase 6.5.1.7.1 이상*|
|**Oracle Solaris (Sparc)**|||||
|Solaris 10|●|●|●||
|Solaris 11|●|●|●|*- Altibase 6.5.1.4.2 이상*|
|**Microsoft Windows (x64)**|||||
|Microsoft Windows Server 2008<br/>Microsoft Windows Server 2012<br/>Microsoft Windows Server 2016<br/>Microsoft Windows Server 2019|●|●|●|*- Altibase 6.5.1.7.7 이상*|
|Microsoft Windows 7<br/>Microsoft Windows 8|●|●|●||
|Microsoft Windows 10|●|●|●|*- Altibase  6.5.1.6.2 이상*|

