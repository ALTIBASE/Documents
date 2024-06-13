# Altibase Supported Platforms by Version

<br/>

<br/>

# Table of Contents

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Overview](#Overview)
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

# Overview

This page provides information on the supported operating systems and the versions that have passed compatibility tests for each version of Altibase.

The symbols used in the tables on this page have the following meanings:

**`x`** : Altibase is not supported

**`●`** : Passed compatibility tests

**`○`** : Tests have not been conducted, but compatibility is guaranteed

> [!NOTE]
>
> **The versions of Red Hat Enterprise Linux, CentOS, Oracle Linux, and Rocky Linux that are compatible are the same.** If compatibility tests are passed on Red Hat Enterprise Linux 8.4, then Oracle Linux 8.4 and Rocky Linux 8.4 are also guaranteed to be compatible. 
>
> **For Red Hat Enterprise Linux, CentOS, Oracle Linux, and Rocky Linux, compatibility is guaranteed if the major versions are the same, regardless of the minor version.** For specific minor versions not listed in the tables below, please contact the [Altibase's Customer Support](http://support.altibase.com/en/) for Altibase compatibility test results.

<br/>

# Altibase 7.3

## Altibase 7.3 Server & Client

>  Both Altibase server and client only support 64-bit.
>
>  Microsoft Windows supports Altibase client only.

> All versions of Altibase 7.3 support it unless the patch version is specified.

> **Fedora, openSUSE, and other Linux distributions not listed in the table below are not officially supported, and compatibility is not guaranteed.**


| Altibase 7.3                                                 | Altibase Server | Altibase Client | Software Requirements        |
| :----------------------------------------------------------- | :-----------: | :-----------------: | :------------------------- |
| **AIX on IBM Power Systems**                                 |               |                     |                            |
| AIX 6.1 TL9                                                  |       ●       |          ●          |                            |
| AIX 7.1<br/>AIX 7.2                                          |     **○**     |        **○**        |                            |
| **HP-UX Itanium (IA-64)**                                    |               |                     |                            |
| HP-UX 11.31                                                  |       ●       |          ●          |                            |
| **Linux x86-64**                                             |               |                     |                            |
| Red Hat Enterprise Linux 6.0<br />Red Hat Enterprise Linux 7.5 |       ●       |          ●          | *- GNU glibc 2.12 ~ 2.33*  |
| Red Hat Enterprise Linux 8.2<br />Red Hat Enterprise Linux 8.3<br />Red Hat Enterprise Linux 8.4<br />Red Hat Enterprise Linux 8.6<br/>Red Hat Enterprise Linux 8.8 |     **○**     |        **○**        | *- GNU glibc 2.12 ~ 2.33*  |
| Oracle Linux 7.2<br/>Oracle Linux 7.4<br/>Oracle Linux 7.9<br/>Oracle Linux 8.4<br/>Oracle Linux 8.6<br/>Oracle Linux 8.8 |     **○**     |        **○**        | *- GNU glibc 2.12 ~ 2.33*  |
| Rocky Linux 8.6<br/>Rocky Linux 8.8                          |       ●       |          ●          | *- GNU glibc 2.12 ~ 2.33*  |
| CentOS 6.8<br />CentOS 7.5                                   |       ●       |          ●          | *- GNU glibc 2.12 ~ 2.33*  |
| Ubuntu 12                                                    |     **○**     |        **○**        | - *GNU glibc 2.17 ~ 2.33*  |
| Ubuntu 16                                                    |     **○**     |        **○**        | -  *GNU glibc 2.23 ~ 2.33* |
| Ubuntu 18                                                    |     **○**     |        **○**        | - *GNU glibc 2.27 ~ 2.33*  |
| **Linux on Power**                                           |               |                     |                            |
| POWER7 Red Hat Enterprise Linux 6.5                          |       ●       |          ●          | *- GNU glibc 2.12 ~ 2.33*  |
| **Linux on Power** **(Little Endian)**                       |               |                     |                            |
| POWER8(LE) Red Hat Enterprise Linux 7.2                      |       ●       |          ●          | *- GNU glibc 2.17 ~ 2.33*  |
| **Microsoft Windows (x64)**                                  |               |                     |                            |
| Microsoft Windows 2008<br/>Microsoft Windows 10              |     **x**     |          ●          |                            |

<br/>

## Altibase 7.3 Library & Tools

| Altibase 7.3                                                 | PDO Driver<br/>PDO_ALTIBASE-1.x.x for PHP 5.3.3, 7.1.20 | PDO Driver<br />PDO_ALTIBASE-2.x.x for PHP 8.1.8 | altiMon | Adapter for JDBC | Adapter for Oracle | Software Requirements |
| :----------------------------------------------------------- | :-----------------------------------------------------: | :----------------------------------------------: | :-----: | :--------------: | :----------------: | :-------------------- |
| **AIX on IBM Power Systems**                                 |                                                         |                                                  |         |                  |                    |                       |
| AIX 6.1                                                      |                          **x**                          |                      **x**                       |    ●    |        ●         |         ●          |                       |
| AIX 7.1<br/>AIX 7.2                                          |                          **x**                          |                      **x**                       |  **○**  |      **○**       |       **○**        |                       |
| **HP-UX Itanium (IA-64)**                                    |                                                         |                                                  |         |                  |                    |                       |
| HP-UX 11.31                                                  |                          **x**                          |                      **x**                       |    ●    |        ●         |       **x**        |                       |
| **Linux x86-64**                                             |                                                         |                                                  |         |                  |                    |                       |
| Red Hat Enterprise Linux 6.0                                 |                            ●                            |                        ●                         |    ●    |        ●         |         ●          |                       |
| Red Hat Enterprise Linux 8.2<br/>Red Hat Enterprise Linux 8.3<br/>Red Hat Enterprise Linux 8.4<br/>Red Hat Enterprise Linux 8.6<br/>Red Hat Enterprise Linux 8.8 |                          **○**                          |                      **○**                       |  **○**  |      **○**       |       **○**        |                       |
| Oracle Linux 7.2<br/>Oracle Linux 7.4<br/>Oracle Linux 7.9<br/>Oracle Linux 8.4<br/>Oracle Linux 8.6<br/>Oracle Linux 8.8 |                          **○**                          |                      **○**                       |  **○**  |      **○**       |       **○**        |                       |
| Rocky Linux 8.6<br/>Rocky Linux 8.8                          |                          **○**                          |                      **○**                       |    ●    |        ●         |       **○**        |                       |
| CentOS 6.8                                                   |                          **○**                          |                      **○**                       |  **○**  |        ●         |       **○**        |                       |
| Ubuntu 12<br/>Ubuntu 16<br/>Ubuntu 18                        |                          **○**                          |                      **○**                       |  **○**  |      **○**       |       **○**        |                       |
| **Linux on Power**                                           |                                                         |                                                  |         |                  |                    |                       |
| POWER7 Red Hat Enterprise Linux 6.5                          |                          **○**                          |                      **○**                       |    ●    |        ●         |       **x**        |                       |
| **Linux on Power (Little Endian)**                           |                                                         |                                                  |         |                  |                    |                       |
| POWER8(LE) Red Hat Enterprise Linux 7.2                      |                          **○**                          |                      **○**                       |    ●    |        ●         |       **x**        |                       |
| **Microsoft Windows (x64)**                                  |                          **x**                          |                      **x**                       |  **x**  |      **x**       |       **x**        |                       |

<br/>

# Altibase 7.1

## Altibase 7.1 Server & Client

>  Both Altibase server and client only support 64-bit.
>
>  Microsoft Windows supports Altibase client only.

> All versions of Altibase 7.1 support it unless the patch version is specified.

> **Fedora, openSUSE, and other Linux distributions not listed in the table below are not officially supported, and compatibility is not guaranteed.**


| Altibase 7.1                                                 | Altibase Server | Altibase Client | Software Requirements                                        |
| :----------------------------------------------------------- | :-------------: | :-------------: | :----------------------------------------------------------- |
| **AIX on IBM Power Systems**                                 |                 |                 |                                                              |
| AIX 6.1 TL3 <br />AIX 6.1 TL9                                |        ●        |        ●        |                                                              |
| AIX 7.1                                                      |        ●        |        ●        |                                                              |
| AIX 7.2                                                      |        ●        |        ●        | *- Altibase 7.1.0.4.7 or later*                              |
| **HP-UX Itanium (IA-64)**                                    |                 |                 |                                                              |
| HP-UX 11.31                                                  |        ●        |        ●        |                                                              |
| **Linux x86-64**                                             |                 |                 |                                                              |
| Red Hat Enterprise Linux 6.0<br />Red Hat Enterprise Linux 8.2<br />Red Hat Enterprise Linux 8.3<br />Red Hat Enterprise Linux 8.4 |        ●        |        ●        | *- GNU glibc 2.12 ~ 2.33*                                    |
| Red Hat Enterprise Linux 8.8                                 |      **○**      |      **○**      | *- GNU glibc 2.12 ~ 2.33*                                    |
| Oracle Linux 7.2<br/>Oracle Linux 7.4<br/>Oracle Linux 7.9<br/>Oracle Linux 8.4<br/>Oracle Linux 8.6(UEK) |        ●        |        ●        | *- GNU glibc 2.12 ~ 2.33*                                    |
| Oracle Linux 8.8                                             |      **○**      |      **○**      | *- GNU glibc 2.12 ~ 2.33*                                    |
| Rocky Linux 8.5<br/>Rocky Linux 8.8                          |        ●        |        ●        | *- GNU glibc 2.12 ~ 2.33*                                    |
| CentOS 6.8                                                   |        ●        |        ●        | *- GNU glibc 2.12 ~ 2.33*                                    |
| Ubuntu 12                                                    |        ●        |        ●        | - *GNU glibc 2.17 ~ 2.33*                                    |
| Ubuntu 16                                                    |        ●        |        ●        | -  *GNU glibc 2.23 ~ 2.33*<br />- *Altibase 7.1.0.7.2 or later* |
| Ubuntu 18                                                    |        ●        |        ●        | - *GNU glibc 2.27 ~2.33*<br />- *Altibase 7.1.0.7.2 or later* |
| **Linux on Power**                                           |                 |                 |                                                              |
| POWER7 Red Hat Enterprise Linux 6.5                          |        ●        |        ●        | *- GNU glibc 2.12 ~ 2.33*                                    |
| **Linux on Power** **(Little Endian)**                       |                 |                 |                                                              |
| POWER8(LE) Red Hat Enterprise Linux 7.2                      |        ●        |        ●        | *- GNU glibc 2.17 ~ 2.33*<br />- *Altibase 7.1.0.0.8 or later* |
| **Microsoft Windows (x64)**                                  |                 |                 |                                                              |
| Microsoft Windows 2008                                       |      **x**      |        ●        | *- Altibase Client 7.1.0.4.5 or later*                       |
| Microsoft Windows 10                                         |      **x**      |        ●        |                                                              |

<br/>

## Altibase 7.1 Library & Tools

| Altibase 7.1                                                 | PDO Driver<br/>PDO_ALTIBASE-1.x.x for PHP 5.3.3, 7.1.20 | PDO Driver<br />PDO_ALTIBASE-2.x.x for PHP 8.1.8 | altiMon | Adapter for JDBC | Adapter for Oracle | Software Requirements                                        |
| :----------------------------------------------------------- | :-----------------------------------------------------: | :----------------------------------------------: | :-----: | :--------------: | :----------------: | :----------------------------------------------------------- |
| **AIX on IBM Power Systems**                                 |                                                         |                                                  |         |                  |                    |                                                              |
| AIX 6.1                                                      |                          **x**                          |                      **x**                       |    ●    |        ●         |         ●          |                                                              |
| AIX 7.1<br/>AIX 7.2                                          |                          **x**                          |                      **x**                       |    ●    |        ●         |       **○**        | - *altiMon : Altibase 7.1.0.1.9 or later*                    |
| **HP-UX Itanium (IA-64)**                                    |                                                         |                                                  |         |                  |                    |                                                              |
| HP-UX 11.31                                                  |                          **x**                          |                      **x**                       |    ●    |        ●         |       **x**        |                                                              |
| **Linux x86-64**                                             |                                                         |                                                  |         |                  |                    |                                                              |
| Red Hat Enterprise Linux 6.0                                 |                            ●                            |                        ●                         |    ●    |        ●         |         ●          |                                                              |
| Red Hat Enterprise Linux 8.2<br/>Red Hat Enterprise Linux 8.3 |                          **○**                          |                      **○**                       |  **○**  |        ●         |       **○**        |                                                              |
| Red Hat Enterprise Linux 8.4                                 |                          **○**                          |                      **○**                       |    ●    |        ●         |       **○**        |                                                              |
| Red Hat Enterprise Linux 8.8                                 |                          **○**                          |                      **○**                       |  **○**  |      **○**       |       **○**        |                                                              |
| Oracle Linux 7.2<br/>Oracle Linux 7.4<br/>Oracle Linux 7.9<br/>Oracle Linux 8.4<br/>Oracle Linux 8.6(UEK) |                          **○**                          |                      **○**                       |  **○**  |        ●         |       **○**        |                                                              |
| Oracle Linux 8.8                                             |                          **○**                          |                      **○**                       |  **○**  |      **○**       |       **○**        |                                                              |
| Rocky Linux 8.5<br/>Rocky Linux 8.8                          |                          **○**                          |                      **○**                       |    ●    |        ●         |       **○**        |                                                              |
| CentOS 6.8                                                   |                          **○**                          |                      **○**                       |  **○**  |        ●         |       **○**        |                                                              |
| Ubuntu 12                                                    |                          **○**                          |                      **○**                       |    ●    |        ●         |       **○**        |                                                              |
| Ubuntu 16<br/>Ubuntu 18                                      |                          **○**                          |                      **○**                       |    ●    |        ●         |       **○**        | - *altiMon : Altibase 7.1.0.7.2 or later*                    |
| **Linux on Power**                                           |                                                         |                                                  |         |                  |                    |                                                              |
| POWER7 Red Hat Enterprise Linux 6.5                          |                          **○**                          |                      **○**                       |    ●    |        ●         |       **x**        |                                                              |
| **Linux on Power (Little Endian)**                           |                                                         |                                                  |         |                  |                    |                                                              |
| POWER8(LE) Red Hat Enterprise Linux 7.2                      |                          **○**                          |                      **○**                       |    ●    |        ●         |       **x**        | - *altiMon : Altibase 7.1.0.3.6 or later*<br />- *Adapter for JDBC : Altibase 7.1.0.3.6 or later* |
| **Microsoft Windows (x64)**                                  |                          **x**                          |                      **x**                       |  **x**  |      **x**       |       **x**        |                                                              |

<br/>

# Altibase 6.5.1

## Altibase 6.5.1 Server & Client

> Altibase server supports 64-bit only.

>  All versions of Altibase 6.5.1 support it unless the patch version is specified.

>  **Ubuntu, Fedora, openSUSE, and other Linux distributions not listed in the table below are not officially supported, and compatibility is not guaranteed.**


| Altibase 6.5.1 | Altibase Server | Altibase Client<br />32-bit | Altibase Client<br />64-bit | Software Requirements |
| :------------------------ | :-----------------: | :-----------------------------: | :-----------------------------: | :------------------ |
| **AIX on IBM Power Systems** |                     |                                 |                                 |                     |
| AIX 6.1 TL3<br />AIX 6.1 TL9<br />AIX 7.1 |          ●          |                ●                |                ●                |                     |
| **HP-UX Itanium (IA-64)** |                     |                                 |                                 |                     |
| HP-UX 11.31               | ● | ● | ● |                     |
|**Linux x86-64**|||||
|Red Hat Enterprise Linux 6.0<br/>Red Hat Enterprise Linux 7.8<br/>Red Hat Enterprise Linux 8.3|●|●|●|*- GNU glibc 2.12 ~ 2.33*|
|Red Hat Enterprise Linux 8.8|**○**|**○**|**○**|*- GNU glibc 2.12 ~ 2.33*|
|Oracle Linux 6.5<br/>Oracle Linux 7.2<br/>Oracle Linux 7.4<br/>Oracle Linux 7.9<br/>Oracle Linux 8.4<br/>Oracle Linux 8.6(UEK)|●|●|●|*- GNU glibc 2.12 ~ 2.33*|
|Oracle Linux 8.8|**○**|**○**|**○**|*- GNU glibc 2.12 ~ 2.33*|
|Rocky Linux 8.5<br/>Rocky Linux 8.8|●|**○**|●|*- GNU glibc 2.12 ~ 2.33*|
|CentOS 6.8<br/>CentOS 8.1|●|●|●|*- GNU glibc 2.12 ~ 2.33*|
|Ubuntu 12|●|●|●|*- GNU glibc 2.17 ~ 2.33*|
|**Linux on Power**|||||
|POWER7 Red Hat Enterprise Linux 6.5|●|○|●|*- glibc 2.12 ~ 2.33*|
|POWER8 Red Hat Enterprise Linux 7.1|●|○|●|*- glibc 2.12 ~ 2.33*|
|**Linux on Power (Little Endian)**|||●||
|POWER8(LE) Red Hat Enterprise Linux 7.2|●|○|●|*- glibc 2.17 ~ 2.33*<br />*- Altibase 6.5.1.4.5 or later*|
|POWER9(LE) Red Hat Enterprise Linux 7.6|●|○|●|*- glibc 2.17 ~ 2.33*<br />*- Altibase 6.5.1.7.6 or later*|
|**Oracle Solaris (Sparc)**|||||
|Solaris 10|●|●|●||
|Solaris 11|●|●|●|*- Altibase 6.5.1.4.2 or later*|
|**Microsoft Windows (x64)**|||||
|Microsoft Windows Server 2008<br/>Microsoft Windows Server 2012<br/>Microsoft Windows Server 2016<br/>Microsoft Windows Server 2019|●|●|●|*- Altibase 6.5.1.7.7 or later*|
|Microsoft Windows 7<br/>Microsoft Windows 8|●|●|●||
|Microsoft Windows 10|**○**|●|●|*- Altibase  6.5.1.6.2 or later*|

<br>

## Altibase 6.5.1 Library & Tools

| Altibase 6.5.1                                               | PDO Driver<br/>PDO_ALTIBASE-1.x.x for PHP 5.3.3, 7.1.20 | PDO Driver<br />PDO_ALTIBASE-2.x.x for PHP 8.1.8 | Adapter for JDBC | Adapter for Oracle | Software Requirements                                        |
| :----------------------------------------------------------- | :-----------------------------------------------------: | :----------------------------------------------: | :--------------: | :----------------: | :----------------------------------------------------------- |
| **AIX on IBM Power Systems**                                 |                                                         |                                                  |                  |                    |                                                              |
| AIX 5.3                                                      |                          **x**                          |                      **x**                       |      **x**       |         ●          |                                                              |
| AIX 6.1                                                      |                          **x**                          |                      **x**                       |        ●         |         ●          |                                                              |
| AIX 7.1<br/>AIX 7.2                                          |                          **x**                          |                      **x**                       |        ●         |       **○**        |                                                              |
| **HP-UX Itanium (IA-64)**                                    |                                                         |                                                  |                  |                    |                                                              |
| HP-UX 11.31                                                  |                          **x**                          |                      **x**                       |        ●         |       **x**        |                                                              |
| **Linux x86-64**                                             |                                                         |                                                  |                  |                    |                                                              |
| Red Hat Enterprise Linux 6.0                                 |                            ●                            |                        ●                         |        ●         |         ●          |                                                              |
| Red Hat Enterprise Linux 7.8<br/>Red Hat Enterprise Linux 8.3 |                          **○**                          |                      **○**                       |        ●         |       **○**        |                                                              |
| Red Hat Enterprise Linux 8.8                                 |                          **○**                          |                      **○**                       |      **○**       |       **○**        |                                                              |
| Oracle Linux 6.5<br/>Oracle Linux 7.2<br/>Oracle Linux 7.4<br/>Oracle Linux 7.9<br/>Oracle Linux 8.4<br/>Oracle Linux 8.6(UEK) |                          **○**                          |                      **○**                       |        ●         |       **○**        |                                                              |
| Oracle Linux 8.8                                             |                          **○**                          |                      **○**                       |      **○**       |       **○**        |                                                              |
| Rocky Linux 8.5<br/>Rocky Linux 8.8                          |                          **○**                          |                      **○**                       |        ●         |       **○**        |                                                              |
| CentOS 6.8<br/>CentOS 8.1                                    |                          **○**                          |                      **○**                       |        ●         |       **○**        |                                                              |
| Ubuntu 12                                                    |                          **○**                          |                      **○**                       |        ●         |       **○**        |                                                              |
| **Linux on Power**                                           |                                                         |                                                  |                  |                    |                                                              |
| POWER7 Red Hat Enterprise Linux 6.5                          |                          **○**                          |                      **○**                       |        ●         |       **x**        |                                                              |
| POWER8 Red Hat Enterprise Linux 7.1                          |                          **○**                          |                      **○**                       |        ●         |       **x**        |                                                              |
| **Linux on Power (Little Endian)**                           |                                                         |                                                  |                  |                    |                                                              |
| POWER8(LE) Red Hat Enterprise Linux 7.2                      |                          **○**                          |                      **○**                       |        ●         |       **x**        |                                                              |
| POWER9(LE) Red Hat Enterprise Linux 7.6                      |                          **○**                          |                        ●                         |        ●         |       **x**        |                                                              |
| **Sun Sparc**                                                |                                                         |                                                  |                  |                    |                                                              |
| Solaris 10                                                   |                          **x**                          |                      **x**                       |        ●         |         ●          | - *Adapter for Oracle : 6.5.1.9.3 or later*                  |
| Solaris 11                                                   |                          **x**                          |                      **x**                       |        ●         |         ●          | - *Adapter for JDBC : 6.5.1.4.2 or later*<br />- *Adapter for Oracle : 6.5.1.9.3 or later* |
| **Microsoft Windows (x64)**                                  |                          **x**                          |                      **x**                       |      **x**       |       **x**        |                                                              |
