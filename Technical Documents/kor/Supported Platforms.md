# Altibase 버전 별 지원 플랫폼

<br/>

<br/>

# Table of Contents

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [개요](#개요)
- [Altibase 7.3](#altibase-73)
  - [Altibase 7.3 Server & Client](#altibase-73-server--client)
  - [Altibase 7.3 Library & Tools](#altibase-73-library--tools)
- [Altibase 7.1](#altibase-71)
  - [Altibase 7.1 Server & Client](#altibase-71-server--client)
  - [Altibase 7.1 Library & Tools](#altibase-71-library--tools)
- [Altibase 6.5.1](#altibase-651)
  - [Altibase 6.5.1 Server & Client](#altibase-651-server--client)
  - [Altibase 6.5.1 Library & Tools](#altibase-651-library--tools)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

<br/>

<br/>

# 개요

이 매뉴얼에서는 Altibase 버전 별 지원 OS 및 호환성 테스트를 완료한 OS 버전 정보를 안내합니다.

아래 표에서 명시되지 않은 특정 마이너 버전에 대해 Altibase의 호환성 테스트 결과가 필요하다면 [Altibase 고객 지원 센터](http://support.altibase.com/kr/)로 문의하시기 바랍니다.

# Altibase 7.3

## Altibase 7.3 Server & Client

> [!note]
>
> **공통**
>
> - Altibase 서버와 클라이언트 모두 64비트만 지원합니다.
> - 아래 표에서 Altibase의 패치 버전이 따로 명시되어 있지 않으면, Altibase 7.3의 모든 버전에서 지원함을 의미합니다.
> - 아래 표에서 운영 체제의 마이너 버전이 따로 명시되어 있지 않으면, 해당 메이저 버전의 모든 마이너 버전을 지원함을 의미합니다.
>
> **Linux**
>
> - 아래 표에 없는 리눅스 배포판(Fedora, openSUSE 등)은 공식 지원 대상이 아니며 호환성을 보장하지 않습니다.
>
> **Windows**
>
> - Microsoft Windows에서는 Altibase 클라이언트만 지원합니다.


| 운영 체제                                                    | Altibase 서버 | Altibase 클라이언트 | 소프트웨어 요구사항   |
| :----------------------------------------------------------- | :-----------: | :-----------------: | :-------------------- |
| **Unix**                                                     |               |                     |                       |
| AIX 6.1 TL9                                                  |       ✅       |          ✅          |                       |
| AIX 7.1                                                      |     ✅     |          ✅          |                       |
| AIX 7.2                                                      |       ✅       |          ✅          |                       |
| HP-UX Itanium (IA-64) 11.31                                  |       ✅       |          ✅          |                       |
| **Linux (x86-64) - Red Hat 계열**                            |               |                     |                       |
| Oracle Linux 6 / Red Hat Enterprise Linux 6 / CentOS 6       |       ✅       |          ✅          | *- glibc 2.12 ~ 2.33* |
| Oracle Linux 7 / Red Hat Enterprise Linux 7 / CentOS 7       |       ✅       |        ✅        | *- glibc 2.12 ~ 2.33* |
| Oracle Linux 8 / Red Hat Enterprise Linux 8 / CentOS 8 / Rocky Linux 8 |       ✅       |          ✅          | *- glibc 2.12 ~ 2.33* |
| **Linux (x86-64) - Debian 계열**                             |               |                     |                       |
| Ubuntu 12                                                    |       ✅       |        ✅        | *- glibc 2.17 ~ 2.33* |
| Ubuntu 16                                                    |       ✅       |        ✅        | *- glibc 2.23 ~ 2.33* |
| Ubuntu 18                                                    |       ✅       |          ✅          | *- glibc 2.27 ~ 2.33* |
| **Linux on Power**                                           |               |                     |                       |
| POWER7 w/Red Hat Enterprise Linux 6.5                        |       ✅       |          ✅          | *- glibc 2.12 ~ 2.33* |
| **Linux on Power** **(Little Endian)**                       |               |                     |                       |
| POWER8(LE) w/Red Hat Enterprise Linux 7.2                    |       ✅       |          ✅          | *- glibc 2.17 ~ 2.33* |
| **Microsoft Windows (x64)**                                  |               |                     |                       |
| Microsoft Windows 10                                         |       ❌       |          ✅          |                       |



## Altibase 7.3 Library & Tools

| 운영 체제                                                    | PDO 드라이버<br/>PDO_ALTIBASE-1.x.x for PHP 5.3.3, 7.1.20 | PDO 드라이버<br />PDO_ALTIBASE-2.x.x for PHP 8.1.8 | altiMon | Adapter for JDBC | Adapter for Oracle | 소프트웨어 요구사항 |
| :----------------------------------------------------------- | :-------------------------------------------------------: | :------------------------------------------------: | :-----: | :--------------: | :----------------: | :------------------ |
| **Unix**                                                     |                                                           |                                                    |         |                  |                    |                     |
| AIX 6.1                                                      |                             ❌                             |                         ❌                          |    ✅    |        ✅         |         ✅          |                     |
| AIX 7.1                                                      |                             ❌                             |                         ❌                          |    ✅    |        ✅         |         ✅          |                     |
| AIX 7.2                                                      |                             ❌                             |                         ❌                          |    ✅    |        ✅         |         ✅          |                     |
| HP-UX Itanium (IA-64) 11.31                                  |                             ❌                             |                       ❌                        |    ✅    |        ✅         |         ❌          |                     |
| **Linux (x86-64) - Red Hat 계열**                            |                                                           |                                                    |         |                  |                    |                     |
| Oracle Linux 6 / Red Hat Enterprise Linux 6 / CentOS 6       |                             ✅                             |                         ✅                          |    ✅    |        ✅         |         ✅          |                     |
| Oracle Linux 7 / Red Hat Enterprise Linux 7 / CentOS 7       |                             ✅                             |                         ✅                          |    ✅    |        ✅         |       ✅        |                     |
| Oracle Linux 8 / Red Hat Enterprise Linux 8 / CentOS 8 / Rocky Linux 8 |                             ✅                             |                         ✅                          |    ✅    |        ✅         |       ✅        |                     |
| **Linux (x86-64) - Debian 계열**                             |                                                           |                                                    |         |                  |                    |                     |
| Ubuntu 12                                                    |                             ✅                             |                         ✅                          |    ✅    |        ✅         |         ✅          |                     |
| Ubuntu 16                                                    |                             ✅                             |                         ✅                          |    ✅    |        ✅         |         ✅          |                     |
| Ubuntu 18                                                    |                             ✅                             |                         ✅                          |    ✅    |        ✅         |         ✅          |                     |
| **Linux on Power**                                           |                                                           |                                                    |         |                  |                    |                     |
| POWER7 w/ Red Hat Enterprise Linux 6.5                       |                             ✅                             |                         ✅                          |    ✅    |        ✅         |         ❌          |                     |
| **Linux on Power (Little Endian)**                           |                                                           |                                                    |         |                  |                    |                     |
| POWER8(LE) w/ Red Hat Enterprise Linux 7.2                   |                             ✅                             |                         ✅                          |    ✅    |        ✅         |         ❌          |                     |
| **Microsoft Windows (x64)**                                  |                                                           |                                                    |         |                  |                    |                     |
| ALL                                                          |                             ❌                             |                         ❌                          |    ❌    |        ❌         |         ❌          |                     |



# Altibase 7.1

## Altibase 7.1 Server & Client

> [!note]
>
> **공통**
>
> - Altibase 서버와 클라이언트 모두 64비트만 지원합니다.
> - 아래 표에서 Altibase의 패치 버전이 따로 명시되어 있지 않으면, Altibase 7.1의 모든 버전에서 지원함을 의미합니다.
> - 아래 표에서 운영 체제의 마이너 버전이 따로 명시되어 있지 않으면, 해당 메이저 버전의 모든 마이너 버전을 지원함을 의미합니다.
>
> **Linux**
>
> - 아래 표에 없는 리눅스 배포판(Fedora, openSUSE 등)은 공식 지원 대상이 아니며 호환성을 보장하지 않습니다.
>
> **Windows**
>
> - Microsoft Windows에서는 Altibase 클라이언트만 지원합니다.


| 운영 체ㅔ                                                    | Altibase 서버 | Altibase 클라이언트 | 소프트웨어 요구사항                                    |
| :----------------------------------------------------------- | :-----------: | :-----------------: | :----------------------------------------------------- |
| **AIX on IBM Power Systems**                                 |               |                     |                                                        |
| AIX 6.1 TL3 <br />AIX 6.1 TL9                                |       ✅       |          ✅          |                                                        |
| AIX 7.1                                                      |       ✅       |          ✅          |                                                        |
| AIX 7.2 TL2                                                  |       ✅       |          ✅          | *- Altibase 7.1.0.4.7 이상*                            |
| HP-UX Itanium (IA-64) 11.31                                  |       ✅       |          ✅          |                                                        |
| **Linux (x86-64) - Red Hat 계열**                            |               |                     |                                                        |
| Oracle Linux 6 / Red Hat Enterprise Linux 6 / CentOS 6       |       ✅       |          ✅          | *- glibc 2.12 ~ 2.33*                                  |
| Oracle Linux 7 / Red Hat Enterprise Linux 7 / CentOS 7       |       ✅       |          ✅          | *- glibc 2.12 ~ 2.33*                                  |
| Oracle Linux 8 / Red Hat Enterprise Linux 8 / CentOS 8 / Rocky Linux 8 |       ✅       |          ✅          | *- glibc 2.12 ~ 2.33*                                  |
| **Linux (x86-64) - Debian 계열**                             |               |                     |                                                        |
| Ubuntu 12                                                    |       ✅       |          ✅          | *- glibc 2.17 ~ 2.33*                                  |
| Ubuntu 16                                                    |       ✅       |          ✅          | *- glibc 2.23 ~ 2.33*<br />- *Altibase 7.1.0.7.2 이상* |
| Ubuntu 18                                                    |       ✅       |          ✅          | *- glibc 2.27 ~ 2.33*<br />- *Altibase 7.1.0.7.2 이상* |
| **Linux on Power**                                           |               |                     |                                                        |
| POWER7 w/ Red Hat Enterprise Linux 6.5                       |       ✅       |          ✅          | *- glibc 2.12 ~ 2.33*                                  |
| **Linux on Power** **(Little Endian)**                       |               |                     |                                                        |
| POWER8(LE) w/ Red Hat Enterprise Linux 7.2                   |       ✅       |          ✅          | *- glibc 2.17 ~ 2.33*<br />- *Altibase 7.1.0.0.8 이상* |
| **Microsoft Windows (x64)**                                  |               |                     |                                                        |
| Microsoft Windows 2008                                       |       ❌       |          ✅          | *- Altibase 클라이언트 7.1.0.4.5 이상*                 |
| Microsoft Windows 10                                         |       ❌       |          ✅          |                                                        |



## Altibase 7.1 Library & Tools

| 운영 체제                                                    | PDO 드라이버<br/>PDO_ALTIBASE-1.x.x for PHP 5.3.3, 7.1.20 | PDO 드라이버<br />PDO_ALTIBASE-2.x.x for PHP 8.1.8 | altiMon | Adapter for JDBC | Adapter for Oracle | 소프트웨어 요구사항                                          |
| :----------------------------------------------------------- | :-------------------------------------------------------: | :------------------------------------------------: | :-----: | :--------------: | :----------------: | :----------------------------------------------------------- |
| **Unix**                                                     |                                                           |                                                    |         |                  |                    |
| AIX 6.1                                                      |                             ❌                             |                         ❌                          |    ✅    |        ✅         |         ✅          |                                                              |
| AIX 7.1                                                      |                             ❌                             |                         ❌                          |    ✅    |        ✅         |         ✅          | - *altiMon : Altibase 7.1.0.1.9 이상*                        |
| AIX 7.2 TL2                                                  |                             ❌                             |                         ❌                          |    ✅    |        ✅         |         ✅          | - *altiMon : Altibase 7.1.0.1.9 이상*                        |
| HP-UX Itanium (IA-64) 11.31                                  |                             ❌                             |                         ❌                          |    ✅    |        ✅         |         ❌          |                                                              |
| **Linux (x86-64) - Red Hat 계열**                            |                                                           |                                                    |         |                  |                    |                                                              |
| Oracle Linux 6 / Red Hat Enterprise Linux 6 / CentOS 6       |                             ✅                             |                         ✅                          |    ✅    |        ✅         |         ✅          |                                                              |
| Oracle Linux 7 / Red Hat Enterprise Linux 7 / CentOS 7       |                             ✅                             |                         ✅                          |    ✅    |        ✅         |         ✅          |                                                              |
| Oracle Linux 8 / Red Hat Enterprise Linux 8 / CentOS 8 / Rocky Linux 8 |                             ✅                             |                         ✅                          |    ✅    |        ✅         |         ✅          |                                                              |
| **Linux (x86-64) - Debian 계열**                             |                                                           |                                                    |         |                  |                    |                                                              |
| Ubuntu 12                                                    |                             ✅                             |                         ✅                          |    ✅    |        ✅         |         ✅          |                                                              |
| Ubuntu 16                                                    |                             ✅                             |                         ✅                          |    ✅    |        ✅         |         ✅          | - *altiMon : Altibase 7.1.0.7.2 이상*                        |
| Ubuntu 18                                                    |                             ✅                             |                         ✅                          |    ✅    |        ✅         |         ✅          | - *altiMon : Altibase 7.1.0.7.2 이상*                        |
| **Linux on Power**                                           |                                                           |                                                    |         |                  |                    |                                                              |
| POWER7 w/ Red Hat Enterprise Linux 6.5                       |                             ✅                             |                         ✅                          |    ✅    |        ✅         |         ❌          |                                                              |
| **Linux on Power (Little Endian)**                           |                                                           |                                                    |         |                  |                    |                                                              |
| POWER8(LE) w/ Red Hat Enterprise Linux 7.2                   |                             ✅                             |                         ✅                          |    ✅    |        ✅         |         ❌          | - *altiMon : Altibase 7.1.0.3.6 이상*<br />- *Adapter for JDBC : Altibase 7.1.0.3.6 이상* |
| **Microsoft Windows (x64)**                                  |                                                           |                                                    |         |                  |                    |                                                              |
| ALL                                                          |                             ❌                             |                         ❌                          |    ❌    |        ❌         |         ❌          |                                                              |



# Altibase 6.5.1

## Altibase 6.5.1 Server & Client

> [!note]
>
> **공통**
>
> - Altibase 서버는 64비트만 지원합니다.
> - 아래 표에서 Altibase의 패치 버전이 따로 명시되어 있지 않으면, Altibase 7.5.1의 모든 버전에서 지원함을 의미합니다.
> - 아래 표에서 운영 체제의 마이너 버전이 따로 명시되어 있지 않으면, 해당 메이저 버전의 모든 마이너 버전을 지원함을 의미합니다.
>
> **Linux**
>
> - 아래 표에 없는 리눅스 배포판(Fedora, openSUSE 등)은 공식 지원 대상이 아니며 호환성을 보장하지 않습니다.


| 운영 체제 | Altibase 서버 | Altibase 클라이언트<br />32비트 | Altibase 클라이언트 <br />64비트 | 소프트웨어 요구사항 |
| :------------------------ | :-----------------: | :-----------------------------: | :-----------------------------: | :------------------ |
| **UNIX** |                     |                                 |                                 |                     |
| AIX 6.1 TL3<br />AIX 6.1 TL9 |          ✅          |                ✅                |                ✅                |                     |
| AIX 7.1 | ✅ | ✅ | ✅ | |
| AIX 7.2 | ✅ | ✅ | ✅ | |
| HP-UX Itanium (IA-64) 11.31 |       ✅       |                ✅                | ✅ |                     |
| Solaris 10 (Sun SPARC)                                       |       ✅       |                ✅                |                ✅                 | |
| Solaris 11 (Sun SPARC)                                       |       ✅       |                ✅                |                ✅                 | *- Altibase 6.5.1.4.2 이상* |
|**Linux (x86-64) - Red Hat 계열**|||||
| Oracle Linux 6 / Red Hat Enterprise Linux 6 / CentOS 6       |       ✅       |                ✅                |                ✅                 |*- glibc 2.12 ~ 2.33*|
|Oracle Linux 7 / Red Hat Enterprise Linux 7 / CentOS 7|       ✅       |                ✅                |                ✅                 |*- glibc 2.12 ~ 2.33*|
|Oracle Linux 8 / Red Hat Enterprise Linux 8 / CentOS 8 / Rocky Linux 8|       ✅       |                ✅                |                ✅                 |*- glibc 2.12 ~ 2.33*|
|**Linux (x86-64) - Debian 계열**|||||
|Ubuntu 12|       ✅       |                ✅                |                ✅                 |*- glibc 2.17 ~ 2.33*|
|**Linux on Power**|||||
|POWER7 w/ Red Hat Enterprise Linux 6.5|       ✅       |                ✅                |                ✅                 |*- glibc 2.12 ~ 2.33*|
|POWER8 w/ Red Hat Enterprise Linux 7.1|       ✅       |                ✅                |                ✅                 |*- glibc 2.12 ~ 2.33*|
|**Linux on Power (Little Endian)**|||||
|POWER8(LE) w/ Red Hat Enterprise Linux 7.2|       ✅       |                ✅                |                ✅                 |*- glibc 2.17 ~ 2.33*<br />*- Altibase 6.5.1.4.5 이상*|
|POWER9(LE) w/ Red Hat Enterprise Linux 7.6|       ✅       |                ✅                |                ✅                 |*- glibc 2.17 ~ 2.33*<br />*- Altibase 6.5.1.7.6 이상*|
|**Microsoft Windows (x64)**|||||
|Microsoft Windows Server 2008|       ✅       |                ✅                |                ✅                 |*- Altibase 6.5.1.7.7 이상*|
|Microsoft Windows Server 2012|✅|✅|✅|*- Altibase 6.5.1.7.7 이상*|
|Microsoft Windows Server 2016|✅|✅|✅|*- Altibase 6.5.1.7.7 이상*|
|Microsoft Windows Server 2019|✅|✅|✅|*- Altibase 6.5.1.7.7 이상*|
|Microsoft Windows 7|       ✅       |                ✅                |                ✅                 ||
|Microsoft Windows 8|✅|✅|✅||
|Microsoft Windows 10|       ✅       |                ✅                |                ✅                 |*- Altibase  6.5.1.6.2 이상*|



## Altibase 6.5.1 Library & Tools

| 운영 체제                                                    | PDO 드라이버<br/>PDO_ALTIBASE-1.x.x for PHP 5.3.3, 7.1.20 | PDO 드라이버<br />PDO_ALTIBASE-2.x.x for PHP 8.1.8 | Adapter for JDBC | Adapter for Oracle | 소프트웨어 요구사항                                          |
| :----------------------------------------------------------- | :-------------------------------------------------------: | :------------------------------------------------: | :--------------: | :----------------: | :----------------------------------------------------------- |
| **Unix**                                                     |                                                           |                                                    |                  |                    |                                                              |
| AIX 5.3                                                      |                             ❌                             |                         ❌                          |        ❌         |         ✅          |                                                              |
| AIX 6.1                                                      |                             ❌                             |                         ❌                          |        ✅         |         ✅          |                                                              |
| AIX 7.1                                                      |                             ❌                             |                         ❌                          |        ✅         |         ✅          |                                                              |
| AIX 7.2                                                      |                             ❌                             |                         ❌                          |        ✅         |         ✅          |                                                              |
| HP-UX Itanium (IA-64) 11.31                                  |                             ❌                             |                         ❌                          |        ✅         |         ❌          |                                                              |
| Solaris 10 (Sun SPARC)                                       |                             ❌                             |                         ❌                          |        ✅         |         ✅          | - *Adapter for Oracle : 6.5.1.9.3 이상*                      |
| Solaris 11 (Sun SPARC)                                       |                             ❌                             |                         ❌                          |        ✅         |         ✅          | - *Adapter for JDBC : 6.5.1.4.2 이상*<br />- *Adapter for Oracle : 6.5.1.9.3 이상* |
| **Linux (x86-64) - Red Hat 계열**                            |                                                           |                                                    |                  |                    |                                                              |
| Oracle Linux 6 / Red Hat Enterprise Linux 6 / CentOS 6       |                             ✅                             |                         ✅                          |        ✅         |         ✅          |                                                              |
| Oracle Linux 7 / Red Hat Enterprise Linux 7 / CentOS 7       |                             ✅                             |                         ✅                          |        ✅         |         ✅          |                                                              |
| Oracle Linux 8 / Red Hat Enterprise Linux 8 / CentOS 8 / Rocky Linux 8 |                             ✅                             |                         ✅                          |        ✅         |         ✅          |                                                              |
| **Linux (x86-64) - Debian 계열**                             |                                                           |                                                    |                  |                    |                                                              |
| Ubuntu 12                                                    |                             ✅                             |                         ✅                          |        ✅         |         ✅          |                                                              |
| **Linux on Power**                                           |                                                           |                                                    |                  |                    |                                                              |
| POWER7 w/ Red Hat Enterprise Linux 6.5                       |                             ✅                             |                         ✅                          |        ✅         |         ❌          |                                                              |
| POWER8 w/ Red Hat Enterprise Linux 7.1                       |                             ✅                             |                         ✅                          |        ✅         |         ❌          |                                                              |
| **Linux on Power (Little Endian)**                           |                                                           |                                                    |                  |                    |                                                              |
| POWER8(LE) w/ Red Hat Enterprise Linux 7.2                   |                             ✅                             |                         ✅                          |        ✅         |         ❌          |                                                              |
| POWER9(LE) w/ Red Hat Enterprise Linux 7.6                   |                             ✅                             |                         ✅                          |        ✅         |         ❌          |                                                              |
| **Microsoft Windows (x64)**                                  |                                                           |                                                    |                  |                    |                                                              |
| ALL                                                          |                             ❌                             |                         ❌                          |        ❌         |         ❌          |                                                              |
