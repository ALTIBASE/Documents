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

Altibase 버전 별 지원 OS 및 호환성 테스트를 완료한 OS 버전 정보를 안내하는 페이지입니다. 

이 페이지의 표에서 사용한 기호의 의미는 다음과 같습니다. 

**`x`** : Altibase가 지원하지 않음

**`●`** : 호환성 테스트를 통과함 

**`○`** : 호환성을 보장하지만 테스트를 진행한 적 없음

> [!NOTE]
>
> **Red Hat Enterprise Linux, CentOS, Oracle Linux 그리고 Rocky Linux의 호환성은 동일합니다.** 예를 들어, Red Hat Enterprise Linux 8.4에서 호환성 테스트를 통과했다면 나머지 세 OS의 8.4 버전 또한 호환성을 보장합니다. 
>
> 또한, Linux x86-64 플랫폼에서 Red Hat Enterprise Linux, CentOS, Oracle Linux, Rocky Linux는 메이저 버전이 같은 경우, 마이너 버전은 상관없이 호환성을 보장합니다. 아래 표에서 명시되지 않은 특정 마이너 버전에 대해 Altibase의 호환성 테스트 결과가 필요하다면 [Altibase 고객 지원 센터](http://support.altibase.com/kr/)로 문의하시기 바랍니다.

<br/>

# Altibase 7.3

## Altibase 7.3 Server & Client

>  Altibase 서버/클라이언트 모두 64-bit 만 지원합니다.<br>
>
>  Microsoft Windows 는 지원하지 않습니다. Windows용 클라이언트가 필요한 경우, Altibase 7.1의 클라이언트를 사용할 수 있습니다.

> Altibase 7.3 패치 버전을 명시하지 않은 경우 Altibase 7.3 모든 버전에서 지원함을 의미합니다.

> **Fedora, openSUSE 등 아래 표에서 포함하지 않은 리눅스 배포판은 공식 지원 대상이 아니므로 호환성을 보장하지 않습니다.**


| Altibase 7.3                                                 | Altibase 서버 | Altibase 클라이언트 | 소프트웨어 요구사항        |
| :----------------------------------------------------------- | :-----------: | :-----------------: | :------------------------- |
| **AIX on IBM Power Systems**                                 |               |                     |                            |
| AIX 6.1 TL3 <br />AIX 6.1 TL9                                |       ●       |          ●          |                            |
| AIX 7.1                                                      |     **○**     |        **○**        |                            |
| AIX 7.2                                                      |     **○**     |        **○**        |                            |
| **HP-UX Itanium (IA-64)**                                    |               |                     |                            |
| HP-UX 11.31                                                  |       ●       |          ●          |                            |
| **Linux x86-64**                                             |               |                     |                            |
| Red Hat Enterprise Linux 6.0<br />Red Hat Enterprise Linux 7.5 |       ●       |          ●          | *- GNU glibc 2.12 ~ 2.33*  |
| Red Hat Enterprise Linux 8.2<br />Red Hat Enterprise Linux 8.3<br />Red Hat Enterprise Linux 8.4<br />Red Hat Enterprise Linux 8.6 |     **○**     |        **○**        | *- GNU glibc 2.12 ~ 2.33*  |
| CentOS 6.8<br />CentOS 7.5                                   |       ●       |          ●          | *- GNU glibc 2.12 ~ 2.33*  |
| Oracle Linux 7.2<br/>Oracle Linux 7.4<br/>Oracle Linux 7.9<br/>Oracle Linux 8.4<br/>Oracle Linux 8.6 |     **○**     |        **○**        | *- GNU glibc 2.12 ~ 2.33*  |
| Rocky Linux 8.6                                              |       ●       |          ●          | *- GNU glibc 2.12 ~ 2.33*  |
| Ubuntu 12                                                    |     **○**     |        **○**        | - *GNU glibc 2.17 ~ 2.33*  |
| Ubuntu 16                                                    |     **○**     |        **○**        | -  *GNU glibc 2.23 ~ 2.33* |
| Ubuntu 18                                                    |     **○**     |        **○**        | - *GNU glibc 2.27 ~ 2.33*  |
| **Linux on Power**                                           |               |                     |                            |
| POWER7 Red Hat Enterprise Linux 6.5                          |       ●       |          ●          | *- GNU glibc 2.12 ~ 2.33*  |
| **Linux on Power** **(Little Endian)**                       |               |                     |                            |
| POWER8(LE) Red Hat Enterprise Linux 7.2                      |       ●       |          ●          | *- GNU glibc 2.17 ~ 2.33*  |
| **Microsoft Windows (x64)**                                  |               |                     |                            |
| Microsoft Windows 2008                                       |     **x**     |          ●          |                            |
| Microsoft Windows 10                                         |     **x**     |          ●          |                            |

<br/>

## Altibase 7.3 Library & Tools

| Altibase 7.3                                                 | PDO 드라이버<br/>PDO_ALTIBASE-1.x.x for PHP 5.3.3, 7.1.20 | PDO 드라이버<br />PDO_ALTIBASE-2.x.x for PHP 8.1.8 | altiMon | Adapter for JDBC | Adapter for Oracle | 소프트웨어 요구사항 |
| :----------------------------------------------------------- | :-------------------------------------------------------: | :------------------------------------------------: | :-----: | :--------------: | :----------------: | :------------------ |
| **AIX on IBM Power Systems**                                 |                                                           |                                                    |         |                  |                    |                     |
| AIX 6.1                                                      |                           **x**                           |                       **x**                        |    ●    |        ●         |         ●          |                     |
| AIX 7.1<br/>AIX 7.2                                          |                           **x**                           |                       **x**                        |  **○**  |      **○**       |       **○**        |                     |
| **HP-UX Itanium (IA-64)**                                    |                                                           |                                                    |         |                  |                    |                     |
| HP-UX 11.31                                                  |                           **x**                           |                       **x**                        |    ●    |        ●         |       **x**        |                     |
| **Linux x86-64**                                             |                                                           |                                                    |         |                  |                    |                     |
| Red Hat Enterprise Linux 6.0                                 |                             ●                             |                         ●                          |    ●    |        ●         |         ●          |                     |
| Red Hat Enterprise Linux 8.2<br/>Red Hat Enterprise Linux 8.3 |                           **○**                           |                       **○**                        |  **○**  |      **○**       |       **○**        |                     |
| Red Hat Enterprise Linux 8.4<br/>Red Hat Enterprise Linux 8.6 |                           **○**                           |                       **○**                        |  **○**  |      **○**       |       **○**        |                     |
| CentOS 6.8                                                   |                           **○**                           |                       **○**                        |  **○**  |        ●         |       **○**        |                     |
| Oracle Linux 7.2<br/>Oracle Linux 7.4<br/>Oracle Linux 7.9<br/>Oracle Linux 8.4<br/>Oracle Linux 8.6 |                           **○**                           |                       **○**                        |  **○**  |      **○**       |       **○**        |                     |
| Rocky Linux 8.6                                              |                           **○**                           |                       **○**                        |    ●    |        ●         |       **○**        |                     |
| Ubuntu 12                                                    |                           **○**                           |                       **○**                        |  **○**  |      **○**       |       **○**        |                     |
| Ubuntu 16<br/>Ubuntu 18                                      |                           **○**                           |                       **○**                        |  **○**  |      **○**       |       **○**        |                     |
| **Linux on Power**                                           |                                                           |                                                    |         |                  |                    |                     |
| POWER7 Red Hat Enterprise Linux 6.5                          |                           **○**                           |                       **○**                        |    ●    |        ●         |       **x**        |                     |
| **Linux on Power (Little Endian)**                           |                                                           |                                                    |         |                  |                    |                     |
| POWER8(LE) Red Hat Enterprise Linux 7.2                      |                           **○**                           |                       **○**                        |    ●    |        ●         |       **x**        |                     |
| **Microsoft Windows (x64)**                                  |                           **x**                           |                       **x**                        |  **x**  |      **x**       |       **x**        |                     |

<br/>

# Altibase 7.1

## Altibase 7.1 Server & Client

>  Altibase 서버/클라이언트 모두 64-bit 만 지원합니다.<br>Microsoft Windows 는 Altibase 클라이언트만 지원합니다.

> Altibase 7.1 패치 버전을 명시하지 않은 경우 Altibase 7.1 모든 버전에서 지원함을 의미합니다.

> **Fedora, openSUSE 등 아래 표에서 포함하지 않은 리눅스 배포판은 공식 지원 대상이 아니므로 호환성을 보장하지 않습니다.**


| Altibase 7.1                                                 | Altibase 서버 | Altibase 클라이언트 | 소프트웨어 요구사항                                         |
| :----------------------------------------------------------- | :-----------: | :-----------------: | :---------------------------------------------------------- |
| **AIX on IBM Power Systems**                                 |               |                     |                                                             |
| AIX 6.1 TL3 <br />AIX 6.1 TL9                                |       ●       |          ●          |                                                             |
| AIX 7.1                                                      |       ●       |          ●          |                                                             |
| AIX 7.2                                                      |       ●       |          ●          | *- Altibase 7.1.0.4.7 이상*                                 |
| **HP-UX Itanium (IA-64)**                                    |               |                     |                                                             |
| HP-UX 11.31                                                  |       ●       |          ●          |                                                             |
| **Linux x86-64**                                             |               |                     |                                                             |
| Red Hat Enterprise Linux 6.0<br />Red Hat Enterprise Linux 8.2<br />Red Hat Enterprise Linux 8.3<br />Red Hat Enterprise Linux 8.4 |       ●       |          ●          | *- GNU glibc 2.12 ~ 2.33*                                   |
| Red Hat Enterprise Linux 8.8                                 |     **○**     |        **○**        | *- GNU glibc 2.12 ~ 2.33*                                   |
| CentOS 6.8                                                   |       ●       |          ●          | *- GNU glibc 2.12 ~ 2.33*                                   |
| Oracle Linux 7.2<br/>Oracle Linux 7.4<br/>Oracle Linux 7.9<br/>Oracle Linux 8.4<br/>Oracle Linux 8.6(UEK) |       ●       |          ●          | *- GNU glibc 2.12 ~ 2.33*                                   |
| Oracle Linux 8.8                                             |     **○**     |        **○**        | *- GNU glibc 2.12 ~ 2.33*                                   |
| Rocky Linux 8.5<br/>Rocky Linux 8.8                          |       ●       |          ●          | *- GNU glibc 2.12 ~ 2.33*                                   |
| Ubuntu 12                                                    |       ●       |          ●          | - *GNU glibc 2.17 ~ 2.33*                                   |
| Ubuntu 16                                                    |       ●       |          ●          | -  *GNU glibc 2.23 ~ 2.33*<br />- *Altibase 7.1.0.7.2 이상* |
| Ubuntu 18                                                    |       ●       |          ●          | - *GNU glibc 2.27 ~2.33*<br />- *Altibase 7.1.0.7.2 이상*   |
| **Linux on Power**                                           |               |                     |                                                             |
| POWER7 Red Hat Enterprise Linux 6.5                          |       ●       |          ●          | *- GNU glibc 2.12 ~ 2.33*                                   |
| **Linux on Power** **(Little Endian)**                       |               |                     |                                                             |
| POWER8(LE) Red Hat Enterprise Linux 7.2                      |       ●       |          ●          | *- GNU glibc 2.17 ~ 2.33*<br />- *Altibase 7.1.0.0.8 이상*  |
| **Microsoft Windows (x64)**                                  |               |                     |                                                             |
| Microsoft Windows 2008                                       |     **x**     |          ●          | *- Altibase 클라이언트 7.1.0.4.5 이상*                      |
| Microsoft Windows 10                                         |     **x**     |          ●          |                                                             |

<br/>

## Altibase 7.1 Library & Tools

| Altibase 7.1                                                 | PDO 드라이버<br/>PDO_ALTIBASE-1.x.x for PHP 5.3.3, 7.1.20 | PDO 드라이버<br />PDO_ALTIBASE-2.x.x for PHP 8.1.8 | altiMon | Adapter for JDBC | Adapter for Oracle | 소프트웨어 요구사항                                          |
| :----------------------------------------------------------- | :-------------------------------------------------------: | :------------------------------------------------: | :-----: | :--------------: | :----------------: | :----------------------------------------------------------- |
| **AIX on IBM Power Systems**                                 |                                                           |                                                    |         |                  |                    |                                                              |
| AIX 6.1                                                      |                           **x**                           |                       **x**                        |    ●    |        ●         |         ●          |                                                              |
| AIX 7.1<br/>AIX 7.2                                          |                           **x**                           |                       **x**                        |    ●    |        ●         |       **○**        | - *altiMon : Altibase 7.1.0.1.9 이상*                        |
| **HP-UX Itanium (IA-64)**                                    |                                                           |                                                    |         |                  |                    |                                                              |
| HP-UX 11.31                                                  |                           **x**                           |                       **x**                        |    ●    |        ●         |       **x**        |                                                              |
| **Linux x86-64**                                             |                                                           |                                                    |         |                  |                    |                                                              |
| Red Hat Enterprise Linux 6.0                                 |                             ●                             |                         ●                          |    ●    |        ●         |         ●          |                                                              |
| Red Hat Enterprise Linux 8.2<br/>Red Hat Enterprise Linux 8.3 |                           **○**                           |                       **○**                        |  **○**  |        ●         |       **○**        |                                                              |
| Red Hat Enterprise Linux 8.4                                 |                           **○**                           |                       **○**                        |    ●    |        ●         |       **○**        |                                                              |
| Red Hat Enterprise Linux 8.8                                 |                           **○**                           |                       **○**                        |  **○**  |      **○**       |       **○**        |                                                              |
| CentOS 6.8                                                   |                           **○**                           |                       **○**                        |  **○**  |        ●         |       **○**        |                                                              |
| Oracle Linux 7.2<br/>Oracle Linux 7.4<br/>Oracle Linux 7.9<br/>Oracle Linux 8.4<br/>Oracle Linux 8.6(UEK) |                           **○**                           |                       **○**                        |  **○**  |        ●         |       **○**        |                                                              |
| Oracle Linux 8.8                                             |                           **○**                           |                       **○**                        |  **○**  |      **○**       |       **○**        |                                                              |
| Rocky Linux 8.5<br/>Rocky Linux 8.8                          |                           **○**                           |                       **○**                        |    ●    |        ●         |       **○**        |                                                              |
| Ubuntu 12                                                    |                           **○**                           |                       **○**                        |    ●    |        ●         |       **○**        |                                                              |
| Ubuntu 16<br/>Ubuntu 18                                      |                           **○**                           |                       **○**                        |    ●    |        ●         |       **○**        | - *altiMon : Altibase 7.1.0.7.2 이상*                        |
| **Linux on Power**                                           |                                                           |                                                    |         |                  |                    |                                                              |
| POWER7 Red Hat Enterprise Linux 6.5                          |                           **○**                           |                       **○**                        |    ●    |        ●         |       **x**        |                                                              |
| **Linux on Power (Little Endian)**                           |                                                           |                                                    |         |                  |                    |                                                              |
| POWER8(LE) Red Hat Enterprise Linux 7.2                      |                           **○**                           |                       **○**                        |    ●    |        ●         |       **x**        | - *altiMon : Altibase 7.1.0.3.6 이상*<br />- *Adapter for JDBC : Altibase 7.1.0.3.6 이상* |
| **Microsoft Windows (x64)**                                  |                           **x**                           |                       **x**                        |  **x**  |      **x**       |       **x**        |                                                              |

<br/>

# Altibase 6.5.1

## Altibase 6.5.1 Server & Client

> Altibase 서버는 64비트만 지원합니다.

>  Altibase 6.5.1 패치 버전을 명시하지 않은 경우 Altibase 6.5.1 모든 버전에서 지원함을 의미합니다.

>  **Ubuntu, Fedora, openSUSE 등 아래 표에서 포함하지 않은 리눅스 배포판은 공식 지원 대상이 아니므로 호환성을 보장하지 않습니다.**


| Altibase 6.5.1 | Altibase 서버 | Altibase 클라이언트<br />32비트 | Altibase 클라이언트 <br />64비트 | 소프트웨어 요구사항 |
| :------------------------ | :-----------------: | :-----------------------------: | :-----------------------------: | :------------------ |
| **AIX on IBM Power Systems** |                     |                                 |                                 |                     |
| AIX 6.1 TL3<br />AIX 6.1 TL9<br />AIX 7.1 |          ●          |                ●                |                ●                |                     |
| **HP-UX Itanium (IA-64)** |                     |                                 |                                 |                     |
| HP-UX 11.31               | ● | ● | ● |                     |
|**Linux x86-64**|||||
|Red Hat Enterprise Linux 6.0<br/>Red Hat Enterprise Linux 7.8<br/>Red Hat Enterprise Linux 8.3|●|●|●|*- GNU glibc 2.12 ~ 2.33*|
|CentOS 6.8<br/>CentOS 8.1|●|●|●|*- GNU glibc 2.12 ~ 2.33*|
|Oracle Linux 6.5<br/>Oracle Linux 7.2<br/>Oracle Linux 7.4<br/>Oracle Linux 7.9<br/>Oracle Linux 8.4<br/>Oracle Linux 8.6(UEK)|●|●|●|*- GNU glibc 2.12 ~ 2.33*|
|Rocky Linux 8.5|●|**○**|●|*- GNU glibc 2.12 ~ 2.33*|
|Ubuntu 12|●|●|●|*- GNU glibc 2.17 ~ 2.33*|
|**Linux on Power**|||||
|POWER7 Red Hat Enterprise Linux 6.5|●|○|●|*- glibc 2.12 ~ 2.33*|
|POWER8 Red Hat Enterprise Linux 7.1|●|○|●|*- glibc 2.12 ~ 2.33*|
|**Linux on Power (Little Endian)**|||●||
|POWER8(LE) Red Hat Enterprise Linux 7.2|●|○|●|*- glibc 2.17 ~ 2.33*<br />*- Altibase 6.5.1.4.5 이상*|
|POWER9(LE) Red Hat Enterprise Linux 7.6|●|○|●|*- glibc 2.17 ~ 2.33*<br />*- Altibase 6.5.1.7.6 이상*|
|**Oracle Solaris (Sparc)**|||||
|Solaris 10|●|●|●||
|Solaris 11|●|●|●|*- Altibase 6.5.1.4.2 이상*|
|**Microsoft Windows (x64)**|||||
|Microsoft Windows Server 2008<br/>Microsoft Windows Server 2012<br/>Microsoft Windows Server 2016<br/>Microsoft Windows Server 2019|●|●|●|*- Altibase 6.5.1.7.7 이상*|
|Microsoft Windows 7<br/>Microsoft Windows 8|●|●|●||
|Microsoft Windows 10|**○**|●|●|*- Altibase  6.5.1.6.2 이상*|

<br>

## Altibase 6.5.1 Library & Tools

| Altibase 6.5.1                                               | PDO 드라이버<br/>PDO_ALTIBASE-1.x.x for PHP 5.3.3, 7.1.20 | PDO 드라이버<br />PDO_ALTIBASE-2.x.x for PHP 8.1.8 | Adapter for JDBC | Adapter for Oracle | 소프트웨어 요구사항                                          |
| :----------------------------------------------------------- | :-------------------------------------------------------: | :------------------------------------------------: | :--------------: | :----------------: | :----------------------------------------------------------- |
| **AIX on IBM Power Systems**                                 |                                                           |                                                    |                  |                    |                                                              |
| AIX 5.3                                                      |                           **x**                           |                       **x**                        |      **x**       |         ●          |                                                              |
| AIX 6.1                                                      |                           **x**                           |                       **x**                        |        ●         |         ●          |                                                              |
| AIX 7.1                                                      |                           **x**                           |                       **x**                        |        ●         |       **○**        |                                                              |
| AIX 7.2                                                      |                           **x**                           |                       **x**                        |        ●         |       **○**        |                                                              |
| **HP-UX Itanium (IA-64)**                                    |                                                           |                                                    |                  |                    |                                                              |
| HP-UX 11.31                                                  |                           **x**                           |                       **x**                        |        ●         |       **x**        |                                                              |
| **Linux x86-64**                                             |                                                           |                                                    |                  |                    |                                                              |
| Red Hat Enterprise Linux 6.0                                 |                             ●                             |                         ●                          |        ●         |         ●          |                                                              |
| Red Hat Enterprise Linux 7.8<br/>Red Hat Enterprise Linux 8.3 |                           **○**                           |                       **○**                        |        ●         |       **○**        |                                                              |
| CentOS 6.8<br/>CentOS 8.1                                    |                           **○**                           |                       **○**                        |        ●         |       **○**        |                                                              |
| Oracle Linux 6.5<br/>Oracle Linux 7.2<br/>Oracle Linux 7.4<br/>Oracle Linux 7.9<br/>Oracle Linux 8.4<br/>Oracle Linux 8.6(UEK) |                           **○**                           |                       **○**                        |        ●         |       **○**        |                                                              |
| Rocky Linux 8.5                                              |                           **○**                           |                       **○**                        |        ●         |       **○**        |                                                              |
| Ubuntu 12                                                    |                           **○**                           |                       **○**                        |        ●         |       **○**        |                                                              |
| **Linux on Power**                                           |                                                           |                                                    |                  |                    |                                                              |
| POWER7 Red Hat Enterprise Linux 6.5                          |                           **○**                           |                       **○**                        |        ●         |       **x**        |                                                              |
| POWER8 Red Hat Enterprise Linux 7.1                          |                           **○**                           |                       **○**                        |        ●         |       **x**        |                                                              |
| **Linux on Power (Little Endian)**                           |                                                           |                                                    |                  |                    |                                                              |
| POWER8(LE) Red Hat Enterprise Linux 7.2                      |                           **○**                           |                       **○**                        |        ●         |       **x**        |                                                              |
| POWER9(LE) Red Hat Enterprise Linux 7.6                      |                           **○**                           |                         ●                          |        ●         |       **x**        |                                                              |
| **Sun Sparc**                                                |                                                           |                                                    |                  |                    |                                                              |
| Solaris 10                                                   |                           **x**                           |                       **x**                        |        ●         |         ●          | - *Adapter for Oracle : 6.5.1.9.3 이상*                      |
| Solaris 11                                                   |                           **x**                           |                       **x**                        |        ●         |         ●          | - *Adapter for JDBC : 6.5.1.4.2 이상*<br />- *Adapter for Oracle : 6.5.1.9.3 이상* |
| **Microsoft Windows (x64)**                                  |                           **x**                           |                       **x**                        |      **x**       |       **x**        |                                                              |

<br/>
