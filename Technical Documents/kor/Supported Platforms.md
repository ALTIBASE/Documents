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

Altibase가 지원하는 OS 정보를 안내합니다.

아래 표에 명시되지 않은 OS에 대한 Altibase의 호환성 정보는 [Altibase 고객 지원 센터](http://support.altibase.com/kr/)로 문의해 주시기 바랍니다.

# Altibase 7.3

## Altibase 7.3 Server & Client

> [!note]
>
> **공통**
>
> - Altibase 서버와 클라이언트 모두 64비트만 지원합니다.
> - 아래 표에서 Altibase의 패치 버전이 따로 명시되어 있지 않으면, Altibase 7.3의 모든 버전에서 지원함을 의미합니다.
> - 아래 표에서 운영 체제의 마이너 버전이 따로 명시되어 있지 않으면, 해당 메이저 버전의 모든 마이너 버전을 지원함을 의미합니다.

| 운영 체제                                                    | Altibase 서버 | Altibase 클라이언트 | 소프트웨어 요구사항                                   |
| :----------------------------------------------------------- | :-----------: | :-----------------: | :---------------------------------------------------- |
| **Linux on IBM LinuxONE (s390x)**                            |               |                     |                                                       |
| Red Hat Enterprise Linux 8                                   |       ✅       |          ✅          | *- glibc 2.17 ~ 2.33*</br>- *Altibase 7.3.0.1.2 이상* |
| **Linux (x86-64) - Red Hat 계열**                            |               |                     |                                                       |
| Oracle Linux 9 / Red Hat Enterprise Linux 9 / CentOS 9 / Rocky Linux 9 |       ✅       |          ✅          | *- glibc 2.34 </br> - Altibase 7.3.0.0.9 이상*        |
| Oracle Linux 8 / Red Hat Enterprise Linux 8 / CentOS 8 / Rocky Linux 8 |       ✅       |          ✅          | *- glibc 2.12 ~ 2.33*                                 |
| Oracle Linux 7 / Red Hat Enterprise Linux 7 / CentOS 7       |       ✅       |          ✅          | *- glibc 2.12 ~ 2.33*                                 |
| Oracle Linux 6 / Red Hat Enterprise Linux 6 / CentOS 6       |       ✅       |          ✅          | *- glibc 2.12 ~ 2.33*                                 |
| **Linux (x86-64) - Debian 계열**                             |               |                     |                                                       |
| Ubuntu 18                                                    |       ✅       |          ✅          | *- glibc 2.27 ~ 2.33*                                 |
| Ubuntu 16                                                    |       ✅       |          ✅          | *- glibc 2.23 ~ 2.33*                                 |
| Ubuntu 12                                                    |       ✅       |          ✅          | *- glibc 2.17 ~ 2.33*                                 |
| **Linux on Power**                                           |               |                     |                                                       |
| POWER7 w/Red Hat Enterprise Linux 6.5                        |       ✅       |          ✅          | *- glibc 2.12 ~ 2.33*                                 |
| **Linux on Power** **(Little Endian)**                       |               |                     |                                                       |
| POWER8(LE) w/Red Hat Enterprise Linux 7.2                    |       ✅       |          ✅          | *- glibc 2.17 ~ 2.33*                                 |
| **AIX on IBM Power Systems**                                 |               |                     |                                                       |
| AIX 7.2                                                      |       ✅       |          ✅          |                                                       |
| AIX 7.1                                                      |       ✅       |          ✅          |                                                       |
| AIX 6.1 TL9 이상                                             |       ✅       |          ✅          |                                                       |
| **HP-UX Itanium (IA-64)**                                    |               |                     |                                                       |
| HP-UX Itanium (IA-64) 11.31                                  |       ✅       |          ✅          |                                                       |
| **Microsoft Windows (x64)**                                  |               |                     |                                                       |
| Microsoft Windows 10                                         |       ❌       |          ✅          |                                                       |


## Altibase 7.3 Library & Tools

| 운영 체제                                                    | PDO 드라이버<br/>PDO_ALTIBASE-1.x.x for PHP 5.3.3, 7.1.20 | PDO 드라이버<br />PDO_ALTIBASE-2.x.x for PHP 8.1.8 | altiMon | Adapter for JDBC | Adapter for Oracle | 소프트웨어 요구사항         |
| :----------------------------------------------------------- | :-------------------------------------------------------: | :------------------------------------------------: | :-----: | :--------------: | :----------------: | :-------------------------- |
| **Linux on IBM LinuxONE (s390x)**                            |                                                           |                                                    |         |                  |                    |                             |
| Red Hat Enterprise Linux 8                                   |                             ✅                             |                         ✅                          |    ✅    |        ✅         |         ✅          | - *Altibase 7.3.0.1.2 이상* |
| **Linux (x86-64) - Red Hat 계열**                            |                                                           |                                                    |         |                  |                    |                             |
| Oracle Linux 9 / Red Hat Enterprise Linux 9 / CentOS 9 / Rocky Linux 9 |                             ✅                             |                         ✅                          |    ✅    |        ✅         |         ✅          |                             |
| Oracle Linux 8 / Red Hat Enterprise Linux 8 / CentOS 8 / Rocky Linux 8 |                             ✅                             |                         ✅                          |    ✅    |        ✅         |         ✅          |                             |
| Oracle Linux 7 / Red Hat Enterprise Linux 7 / CentOS 7       |                             ✅                             |                         ✅                          |    ✅    |        ✅         |         ✅          |                             |
| Oracle Linux 6 / Red Hat Enterprise Linux 6 / CentOS 6       |                             ✅                             |                         ✅                          |    ✅    |        ✅         |         ✅          |                             |
| **Linux (x86-64) - Debian 계열**                             |                                                           |                                                    |         |                  |                    |                             |
| Ubuntu 18                                                    |                             ✅                             |                         ✅                          |    ✅    |        ✅         |         ✅          |                             |
| Ubuntu 16                                                    |                             ✅                             |                         ✅                          |    ✅    |        ✅         |         ✅          |                             |
| Ubuntu 12                                                    |                             ✅                             |                         ✅                          |    ✅    |        ✅         |         ✅          |                             |
| **Linux on Power**                                           |                                                           |                                                    |         |                  |                    |                             |
| POWER7 w/ Red Hat Enterprise Linux 6.5                       |                             ✅                             |                         ✅                          |    ✅    |        ✅         |         ❌          |                             |
| **Linux on Power (Little Endian)**                           |                                                           |                                                    |         |                  |                    |                             |
| POWER8(LE) w/ Red Hat Enterprise Linux 7.2                   |                             ✅                             |                         ✅                          |    ✅    |        ✅         |         ❌          |                             |
| **AIX on IBM Power Systems**                                 |                                                           |                                                    |         |                  |                    |                             |
| AIX 7.2                                                      |                             ❌                             |                         ❌                          |    ✅    |        ✅         |         ✅          |                             |
| AIX 7.1                                                      |                             ❌                             |                         ❌                          |    ✅    |        ✅         |         ✅          |                             |
| AIX 6.1                                                      |                             ❌                             |                         ❌                          |    ✅    |        ✅         |         ✅          |                             |
| **HP-UX Itanium (IA-64)**                                    |                                                           |                                                    |         |                  |                    |                             |
| HP-UX Itanium (IA-64) 11.31                                  |                             ❌                             |                         ❌                          |    ✅    |        ✅         |         ❌          |                             |
| **Microsoft Windows (x64)**                                  |                                                           |                                                    |         |                  |                    |                             |
| ALL                                                          |                             ❌                             |                         ❌                          |    ❌    |        ❌         |         ❌          |                             |


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

| 운영 체제                                                    | Altibase 서버 | Altibase 클라이언트 | 소프트웨어 요구사항                                    |
| :----------------------------------------------------------- | :-----------: | :-----------------: | :----------------------------------------------------- |
| **AIX on IBM Power Systems**                                 |               |                     |                                                        |
| AIX 7.2 TL2 이상                                             |       ✅       |          ✅          | *- Altibase 7.1.0.4.7 이상*                            |
| AIX 7.1                                                      |       ✅       |          ✅          |                                                        |
| AIX 6.1 TL3 이상                                             |       ✅       |          ✅          |                                                        |
| HP-UX Itanium (IA-64) 11.31                                  |       ✅       |          ✅          |                                                        |
| **Linux (x86-64) - Red Hat 계열**                            |               |                     |                                                        |
| Oracle Linux 9 / Red Hat Enterprise Linux 9 / CentOS 9 / Rocky Linux 9 |       ✅       |          ✅          | *- glibc 2.34 </br> - Altibase 7.1.0.10.0 이상*        |
| Oracle Linux 8 / Red Hat Enterprise Linux 8 / CentOS 8 / Rocky Linux 8 |       ✅       |          ✅          | *- glibc 2.12 ~ 2.33*                                  |
| Oracle Linux 7 / Red Hat Enterprise Linux 7 / CentOS 7       |       ✅       |          ✅          | *- glibc 2.12 ~ 2.33*                                  |
| Oracle Linux 6 / Red Hat Enterprise Linux 6 / CentOS 6       |       ✅       |          ✅          | *- glibc 2.12 ~ 2.33*                                  |
| **Linux (x86-64) - Debian 계열**                             |               |                     |                                                        |
| Ubuntu 18                                                    |       ✅       |          ✅          | *- glibc 2.27 ~ 2.33*<br />- *Altibase 7.1.0.7.2 이상* |
| Ubuntu 16                                                    |       ✅       |          ✅          | *- glibc 2.23 ~ 2.33*<br />- *Altibase 7.1.0.7.2 이상* |
| Ubuntu 12                                                    |       ✅       |          ✅          | *- glibc 2.17 ~ 2.33*                                  |
| **Linux on Power**                                           |               |                     |                                                        |
| POWER7 w/ Red Hat Enterprise Linux 6.5                       |       ✅       |          ✅          | *- glibc 2.12 ~ 2.33*                                  |
| **Linux on Power** **(Little Endian)**                       |               |                     |                                                        |
| POWER8(LE) w/ Red Hat Enterprise Linux 7.2                   |       ✅       |          ✅          | *- glibc 2.17 ~ 2.33*<br />- *Altibase 7.1.0.0.8 이상* |
| **Microsoft Windows (x64)**                                  |               |                     |                                                        |
| Microsoft Windows 10                                         |       ❌       |          ✅          |                                                        |
| Microsoft Windows 2008                                       |       ❌       |          ✅          | *- Altibase 클라이언트 7.1.0.4.5 이상*                 |


## Altibase 7.1 Library & Tools

| 운영 체제                                                    | PDO 드라이버<br/>PDO_ALTIBASE-1.x.x for PHP 5.3.3, 7.1.20 | PDO 드라이버<br />PDO_ALTIBASE-2.x.x for PHP 8.1.8 | altiMon | Adapter for JDBC | Adapter for Oracle | 소프트웨어 요구사항                                          |
| :----------------------------------------------------------- | :-------------------------------------------------------: | :------------------------------------------------: | :-----: | :--------------: | :----------------: | :----------------------------------------------------------- |
| **Unix**                                                     |                                                           |                                                    |         |                  |                    |                                                              |
| AIX 7.2 TL2 이상                                             |                             ❌                             |                         ❌                          |    ✅    |        ✅         |         ✅          | - *altiMon : Altibase 7.1.0.1.9 이상*                        |
| AIX 7.1                                                      |                             ❌                             |                         ❌                          |    ✅    |        ✅         |         ✅          | - *altiMon : Altibase 7.1.0.1.9 이상*                        |
| AIX 6.1                                                      |                             ❌                             |                         ❌                          |    ✅    |        ✅         |         ✅          |                                                              |
| HP-UX Itanium (IA-64) 11.31                                  |                             ❌                             |                         ❌                          |    ✅    |        ✅         |         ❌          |                                                              |
| **Linux (x86-64) - Red Hat 계열**                            |                                                           |                                                    |         |                  |                    |                                                              |
| Oracle Linux 9 / Red Hat Enterprise Linux 9 / CentOS 9 / Rocky Linux 9 |                             ✅                             |                         ✅                          |    ✅    |        ✅         |         ✅          | *- Altibase 7.1.0.10.0 이상*                                 |
| Oracle Linux 8 / Red Hat Enterprise Linux 8 / CentOS 8 / Rocky Linux 8 |                             ✅                             |                         ✅                          |    ✅    |        ✅         |         ✅          |                                                              |
| Oracle Linux 7 / Red Hat Enterprise Linux 7 / CentOS 7       |                             ✅                             |                         ✅                          |    ✅    |        ✅         |         ✅          |                                                              |
| Oracle Linux 6 / Red Hat Enterprise Linux 6 / CentOS 6       |                             ✅                             |                         ✅                          |    ✅    |        ✅         |         ✅          |                                                              |
| **Linux (x86-64) - Debian 계열**                             |                                                           |                                                    |         |                  |                    |                                                              |
| Ubuntu 18                                                    |                             ✅                             |                         ✅                          |    ✅    |        ✅         |         ✅          | - *altiMon : Altibase 7.1.0.7.2 이상*                        |
| Ubuntu 16                                                    |                             ✅                             |                         ✅                          |    ✅    |        ✅         |         ✅          | - *altiMon : Altibase 7.1.0.7.2 이상*                        |
| Ubuntu 12                                                    |                             ✅                             |                         ✅                          |    ✅    |        ✅         |         ✅          |                                                              |
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
> - 아래 표에서 Altibase의 패치 버전이 따로 명시되어 있지 않으면, Altibase 6.5.1의 모든 버전에서 지원함을 의미합니다.
> - 아래 표에서 운영 체제의 마이너 버전이 따로 명시되어 있지 않으면, 해당 메이저 버전의 모든 마이너 버전을 지원함을 의미합니다.

| 운영 체제                                                    | Altibase 서버 | Altibase 클라이언트<br />32비트 | Altibase 클라이언트 <br />64비트 | 소프트웨어 요구사항                                    |
| :----------------------------------------------------------- | :-----------: | :-----------------------------: | :------------------------------: | :----------------------------------------------------- |
| **UNIX**                                                     |               |                                 |                                  |                                                        |
| AIX 7.2                                                      |       ✅       |                ✅                |                ✅                 |                                                        |
| AIX 7.1                                                      |       ✅       |                ✅                |                ✅                 |                                                        |
| AIX 6.1 TL3 이상                                             |       ✅       |                ✅                |                ✅                 |                                                        |
| HP-UX Itanium (IA-64) 11.31                                  |       ✅       |                ✅                |                ✅                 |                                                        |
| Solaris 11 (Sun SPARC)                                       |       ✅       |                ✅                |                ✅                 | *- Altibase 6.5.1.4.2 이상*                            |
| Solaris 10 (Sun SPARC)                                       |       ✅       |                ✅                |                ✅                 |                                                        |
| **Linux (x86-64) - Red Hat 계열**                            |               |                                 |                                  |                                                        |
| Oracle Linux 8 / Red Hat Enterprise Linux 8 / CentOS 8 / Rocky Linux 8 |       ✅       |                ✅                |                ✅                 | *- glibc 2.12 ~ 2.33*                                  |
| Oracle Linux 7 / Red Hat Enterprise Linux 7 / CentOS 7       |       ✅       |                ✅                |                ✅                 | *- glibc 2.12 ~ 2.33*                                  |
| Oracle Linux 6 / Red Hat Enterprise Linux 6 / CentOS 6       |       ✅       |                ✅                |                ✅                 | *- glibc 2.12 ~ 2.33*                                  |
| **Linux (x86-64) - Debian 계열**                             |               |                                 |                                  |                                                        |
| Ubuntu 12                                                    |       ✅       |                ✅                |                ✅                 | *- glibc 2.17 ~ 2.33*                                  |
| **Linux on Power**                                           |               |                                 |                                  |                                                        |
| POWER8 w/ Red Hat Enterprise Linux 7.1                       |       ✅       |                ✅                |                ✅                 | *- glibc 2.12 ~ 2.33*                                  |
| POWER7 w/ Red Hat Enterprise Linux 6.5                       |       ✅       |                ✅                |                ✅                 | *- glibc 2.12 ~ 2.33*                                  |
| **Linux on Power (Little Endian)**                           |               |                                 |                                  |                                                        |
| POWER9(LE) w/ Red Hat Enterprise Linux 7.6                   |       ✅       |                ✅                |                ✅                 | *- glibc 2.17 ~ 2.33*<br />*- Altibase 6.5.1.7.6 이상* |
| POWER8(LE) w/ Red Hat Enterprise Linux 7.2                   |       ✅       |                ✅                |                ✅                 | *- glibc 2.17 ~ 2.33*<br />*- Altibase 6.5.1.4.5 이상* |
| **Microsoft Windows (x64)**                                  |               |                                 |                                  |                                                        |
| Microsoft Windows Server 2019                                |       ✅       |                ✅                |                ✅                 | *- Altibase 6.5.1.7.7 이상*                            |
| Microsoft Windows Server 2016                                |       ✅       |                ✅                |                ✅                 | *- Altibase 6.5.1.7.7 이상*                            |
| Microsoft Windows Server 2012                                |       ✅       |                ✅                |                ✅                 | *- Altibase 6.5.1.7.7 이상*                            |
| Microsoft Windows Server 2008                                |       ✅       |                ✅                |                ✅                 | *- Altibase 6.5.1.7.7 이상*                            |
| Microsoft Windows 10                                         |       ✅       |                ✅                |                ✅                 | *- Altibase  6.5.1.6.2 이상*                           |
| Microsoft Windows 8                                          |       ✅       |                ✅                |                ✅                 | *- Altibase 6.5.1.7.7 이상*                            |
| Microsoft Windows 7                                          |       ✅       |                ✅                |                ✅                 | *- Altibase 6.5.1.7.7 이상*                            |


## Altibase 6.5.1 Library & Tools

| 운영 체제                                                    | PDO 드라이버<br/>PDO_ALTIBASE-1.x.x for PHP 5.3.3, 7.1.20 | PDO 드라이버<br />PDO_ALTIBASE-2.x.x for PHP 8.1.8 | Adapter for JDBC | Adapter for Oracle | 소프트웨어 요구사항                                          |
| :----------------------------------------------------------- | :-------------------------------------------------------: | :------------------------------------------------: | :--------------: | :----------------: | :----------------------------------------------------------- |
| **Unix**                                                     |                                                           |                                                    |                  |                    |                                                              |
| AIX 7.2                                                      |                             ❌                             |                         ❌                          |        ✅         |         ✅          |                                                              |
| AIX 7.1                                                      |                             ❌                             |                         ❌                          |        ✅         |         ✅          |                                                              |
| AIX 6.1                                                      |                             ❌                             |                         ❌                          |        ✅         |         ✅          |                                                              |
| AIX 5.3                                                      |                             ❌                             |                         ❌                          |        ❌         |         ✅          |                                                              |
| HP-UX Itanium (IA-64) 11.31                                  |                             ❌                             |                         ❌                          |        ✅         |         ❌          |                                                              |
| Solaris 11 (Sun SPARC)                                       |                             ❌                             |                         ❌                          |        ✅         |         ✅          | - *Adapter for JDBC : 6.5.1.4.2 이상*<br />- *Adapter for Oracle : 6.5.1.9.3 이상* |
| Solaris 10 (Sun SPARC)                                       |                             ❌                             |                         ❌                          |        ✅         |         ✅          | - *Adapter for Oracle : 6.5.1.9.3 이상*                      |
| **Linux (x86-64) - Red Hat 계열**                            |                                                           |                                                    |                  |                    |                                                              |
| Oracle Linux 8 / Red Hat Enterprise Linux 8 / CentOS 8 / Rocky Linux 8 |                             ✅                             |                         ✅                          |        ✅         |         ✅          |                                                              |
| Oracle Linux 7 / Red Hat Enterprise Linux 7 / CentOS 7       |                             ✅                             |                         ✅                          |        ✅         |         ✅          |                                                              |
| Oracle Linux 6 / Red Hat Enterprise Linux 6 / CentOS 6       |                             ✅                             |                         ✅                          |        ✅         |         ✅          |                                                              |
| **Linux (x86-64) - Debian 계열**                             |                                                           |                                                    |                  |                    |                                                              |
| Ubuntu 12                                                    |                             ✅                             |                         ✅                          |        ✅         |         ✅          |                                                              |
| **Linux on Power**                                           |                                                           |                                                    |                  |                    |                                                              |
| POWER8 w/ Red Hat Enterprise Linux 7.1                       |                             ✅                             |                         ✅                          |        ✅         |         ❌          |                                                              |
| POWER7 w/ Red Hat Enterprise Linux 6.5                       |                             ✅                             |                         ✅                          |        ✅         |         ❌          |                                                              |
| **Linux on Power (Little Endian)**                           |                                                           |                                                    |                  |                    |                                                              |
| POWER9(LE) w/ Red Hat Enterprise Linux 7.6                   |                             ✅                             |                         ✅                          |        ✅         |         ❌          |                                                              |
| POWER8(LE) w/ Red Hat Enterprise Linux 7.2                   |                             ✅                             |                         ✅                          |        ✅         |         ❌          |                                                              |
| **Microsoft Windows (x64)**                                  |                                                           |                                                    |                  |                    |                                                              |
| ALL                                                          |                             ❌                             |                         ❌                          |        ❌         |         ❌          |                                                              |