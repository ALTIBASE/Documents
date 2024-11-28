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

This page provides information about the operating systems supported by Altibase.

For specific operating system not listed in the tables below, please contact the [Altibase's Customer Support](http://support.altibase.com/en/) for Altibase compatibility test results.

# Altibase 7.3

## Altibase 7.3 Server & Client

> [!note]
>
> **Common**
>
> - Both Altibase server and client only support 64-bit.
> - All versions of Altibase 7.3 support it unless the patch version is specified.
> - For all operating systems, all minor versions within the respective major version are supported, unless a particular minor version is specified.

| Operating System                                             | Altibase Server | Altibase Client | Software Requirements |
| :----------------------------------------------------------- | :-------------: | :-------------: | :-------------------- |
| **Unix**                                                     |                 |                 |                       |
| AIX 6.1 TL9                                                  |        ✅        |        ✅        |                       |
| AIX 7.1                                                      |        ✅        |        ✅        |                       |
| AIX 7.2                                                      |        ✅        |        ✅        |                       |
| HP-UX Itanium (IA-64) 11.31                                  |        ✅        |        ✅        |                       |
| **Linux (x86-64) - Red Hat-based**                           |                 |                 |                       |
| Oracle Linux 6 / Red Hat Enterprise Linux 6 / CentOS 6       |        ✅        |        ✅        | *- glibc 2.12 ~ 2.33* |
| Oracle Linux 7 / Red Hat Enterprise Linux 7 / CentOS 7       |        ✅        |        ✅        | *- glibc 2.12 ~ 2.33* |
| Oracle Linux 8 / Red Hat Enterprise Linux 8 / CentOS 8 / Rocky Linux 8 |        ✅        |        ✅        | *- glibc 2.12 ~ 2.33* |
| **Linux (x86-64) - Debian-based**                            |                 |                 |                       |
| Ubuntu 12                                                    |        ✅        |        ✅        | *- glibc 2.17 ~ 2.33* |
| Ubuntu 16                                                    |        ✅        |        ✅        | *- glibc 2.23 ~ 2.33* |
| Ubuntu 18                                                    |        ✅        |        ✅        | *- glibc 2.27 ~ 2.33* |
| **Linux on Power**                                           |                 |                 |                       |
| POWER7 w/Red Hat Enterprise Linux 6.5                        |        ✅        |        ✅        | *- glibc 2.12 ~ 2.33* |
| **Linux on Power** **(Little Endian)**                       |                 |                 |                       |
| POWER8(LE) w/Red Hat Enterprise Linux 7.2                    |        ✅        |        ✅        | *- glibc 2.17 ~ 2.33* |
| **Microsoft Windows (x64)**                                  |                 |                 |                       |
| Microsoft Windows 10                                         |        ❌        |        ✅        |                       |

<br/>

## Altibase 7.3 Library & Tools

| Operating System                                             | PDO Driver<br />PDO_ALTIBASE-1.x.x for PHP 5.3.3, 7.1.20 | PDO Driver<br />PDO_ALTIBASE-2.x.x for PHP 8.1.8 | altiMon | Adapter for JDBC | Adapter for Oracle | Software Requirements |
| :----------------------------------------------------------- | :------------------------------------------------------: | :----------------------------------------------: | :-----: | :--------------: | :----------------: | :-------------------- |
| **Unix**                                                     |                                                          |                                                  |         |                  |                    |                       |
| AIX 6.1                                                      |                            ❌                             |                        ❌                         |    ✅    |        ✅         |         ✅          |                       |
| AIX 7.1                                                      |                            ❌                             |                        ❌                         |    ✅    |        ✅         |         ✅          |                       |
| AIX 7.2                                                      |                            ❌                             |                        ❌                         |    ✅    |        ✅         |         ✅          |                       |
| HP-UX Itanium (IA-64) 11.31                                  |                            ❌                             |                        ❌                         |    ✅    |        ✅         |         ❌          |                       |
| **Linux (x86-64) - Red Hat-based**                           |                                                          |                                                  |         |                  |                    |                       |
| Oracle Linux 6 / Red Hat Enterprise Linux 6 / CentOS 6       |                            ✅                             |                        ✅                         |    ✅    |        ✅         |         ✅          |                       |
| Oracle Linux 7 / Red Hat Enterprise Linux 7 / CentOS 7       |                            ✅                             |                        ✅                         |    ✅    |        ✅         |         ✅          |                       |
| Oracle Linux 8 / Red Hat Enterprise Linux 8 / CentOS 8 / Rocky Linux 8 |                            ✅                             |                        ✅                         |    ✅    |        ✅         |         ✅          |                       |
| **Linux (x86-64) - Debian-based**                            |                                                          |                                                  |         |                  |                    |                       |
| Ubuntu 12                                                    |                            ✅                             |                        ✅                         |    ✅    |        ✅         |         ✅          |                       |
| Ubuntu 16                                                    |                            ✅                             |                        ✅                         |    ✅    |        ✅         |         ✅          |                       |
| Ubuntu 18                                                    |                            ✅                             |                        ✅                         |    ✅    |        ✅         |         ✅          |                       |
| **Linux on Power**                                           |                                                          |                                                  |         |                  |                    |                       |
| POWER7 w/ Red Hat Enterprise Linux 6.5                       |                            ✅                             |                        ✅                         |    ✅    |        ✅         |         ❌          |                       |
| **Linux on Power (Little Endian)**                           |                                                          |                                                  |         |                  |                    |                       |
| POWER8(LE) w/ Red Hat Enterprise Linux 7.2                   |                            ✅                             |                        ✅                         |    ✅    |        ✅         |         ❌          |                       |
| **Microsoft Windows (x64)**                                  |                                                          |                                                  |         |                  |                    |                       |
| ALL                                                          |                            ❌                             |                        ❌                         |    ❌    |        ❌         |         ❌          |                       |



# Altibase 7.1

## Altibase 7.1 Server & Client

> [!note]
>
> **Common**
>
> - Both Altibase server and client only support 64-bit.
> - All versions of Altibase 7.1 support it unless the patch version is specified.
> - For all operating systems, all minor versions within the respective major version are supported, unless a particular minor version is specified.

| Operating System                                             | Altibase Server | Altibase Client | Software Requirements                                 |
| :----------------------------------------------------------- | :-------------: | :-------------: | :---------------------------------------------------- |
| **AIX on IBM Power Systems**                                 |                 |                 |                                                       |
| AIX 6.1 TL3  AIX 6.1 TL9                                     |        ✅        |        ✅        |                                                       |
| AIX 7.1                                                      |        ✅        |        ✅        |                                                       |
| AIX 7.2 TL2                                                  |        ✅        |        ✅        | *- Altibase 7.1.0.4.7 or later*                       |
| HP-UX Itanium (IA-64) 11.31                                  |        ✅        |        ✅        |                                                       |
| **Linux (x86-64) - Red Hat-based**                           |                 |                 |                                                       |
| Oracle Linux 6 / Red Hat Enterprise Linux 6 / CentOS 6       |        ✅        |        ✅        | *- glibc 2.12 ~ 2.33*                                 |
| Oracle Linux 7 / Red Hat Enterprise Linux 7 / CentOS 7       |        ✅        |        ✅        | *- glibc 2.12 ~ 2.33*                                 |
| Oracle Linux 8 / Red Hat Enterprise Linux 8 / CentOS 8 / Rocky Linux 8 |        ✅        |        ✅        | *- glibc 2.12 ~ 2.33*                                 |
| **Linux (x86-64) - Debian-based**                            |                 |                 |                                                       |
| Ubuntu 12                                                    |        ✅        |        ✅        | *- glibc 2.17 ~ 2.33*                                 |
| Ubuntu 16                                                    |        ✅        |        ✅        | *- glibc 2.23 ~ 2.33* - *Altibase 7.1.0.7.2 or later* |
| Ubuntu 18                                                    |        ✅        |        ✅        | *- glibc 2.27 ~ 2.33* - *Altibase 7.1.0.7.2 or later* |
| **Linux on Power**                                           |                 |                 |                                                       |
| POWER7 w/ Red Hat Enterprise Linux 6.5                       |        ✅        |        ✅        | *- glibc 2.12 ~ 2.33*                                 |
| **Linux on Power** **(Little Endian)**                       |                 |                 |                                                       |
| POWER8(LE) w/ Red Hat Enterprise Linux 7.2                   |        ✅        |        ✅        | *- glibc 2.17 ~ 2.33* - *Altibase 7.1.0.0.8 or later* |
| **Microsoft Windows (x64)**                                  |                 |                 |                                                       |
| Microsoft Windows 2008                                       |        ❌        |        ✅        | *- Altibase Client 7.1.0.4.5 or later*                |
| Microsoft Windows 10                                         |        ❌        |        ✅        |                                                       |



## Altibase 7.1 Library & Tools

| Operating System                                             | PDO Driver<br />PDO_ALTIBASE-1.x.x for PHP 5.3.3, 7.1.20 | PDO Driver<br />PDO_ALTIBASE-2.x.x for PHP 8.1.8 | altiMon | Adapter for JDBC | Adapter for Oracle | Software Requirements                                        |
| :----------------------------------------------------------- | :------------------------------------------------------: | :----------------------------------------------: | :-----: | :--------------: | :----------------: | :----------------------------------------------------------- |
| **Unix**                                                     |                                                          |                                                  |         |                  |                    |                                                              |
| AIX 6.1                                                      |                            ❌                             |                        ❌                         |    ✅    |        ✅         |         ✅          |                                                              |
| AIX 7.1                                                      |                            ❌                             |                        ❌                         |    ✅    |        ✅         |         ✅          | - *altiMon : Altibase 7.1.0.1.9 or later*                    |
| AIX 7.2 TL2                                                  |                            ❌                             |                        ❌                         |    ✅    |        ✅         |         ✅          | - *altiMon : Altibase 7.1.0.1.9 or later*                    |
| HP-UX Itanium (IA-64) 11.31                                  |                            ❌                             |                        ❌                         |    ✅    |        ✅         |         ❌          |                                                              |
| **Linux (x86-64) - Red Hat-based**                           |                                                          |                                                  |         |                  |                    |                                                              |
| Oracle Linux 6 / Red Hat Enterprise Linux 6 / CentOS 6       |                            ✅                             |                        ✅                         |    ✅    |        ✅         |         ✅          |                                                              |
| Oracle Linux 7 / Red Hat Enterprise Linux 7 / CentOS 7       |                            ✅                             |                        ✅                         |    ✅    |        ✅         |         ✅          |                                                              |
| Oracle Linux 8 / Red Hat Enterprise Linux 8 / CentOS 8 / Rocky Linux 8 |                            ✅                             |                        ✅                         |    ✅    |        ✅         |         ✅          |                                                              |
| **Linux (x86-64) - Debian-based**                            |                                                          |                                                  |         |                  |                    |                                                              |
| Ubuntu 12                                                    |                            ✅                             |                        ✅                         |    ✅    |        ✅         |         ✅          |                                                              |
| Ubuntu 16                                                    |                            ✅                             |                        ✅                         |    ✅    |        ✅         |         ✅          | - *altiMon : Altibase 7.1.0.7.2 or later*                    |
| Ubuntu 18                                                    |                            ✅                             |                        ✅                         |    ✅    |        ✅         |         ✅          | - *altiMon : Altibase 7.1.0.7.2 or later*                    |
| **Linux on Power**                                           |                                                          |                                                  |         |                  |                    |                                                              |
| POWER7 w/ Red Hat Enterprise Linux 6.5                       |                            ✅                             |                        ✅                         |    ✅    |        ✅         |         ❌          |                                                              |
| **Linux on Power (Little Endian)**                           |                                                          |                                                  |         |                  |                    |                                                              |
| POWER8(LE) w/ Red Hat Enterprise Linux 7.2                   |                            ✅                             |                        ✅                         |    ✅    |        ✅         |         ❌          | - *altiMon : Altibase 7.1.0.3.6 or later*<br />- *Adapter for JDBC : Altibase 7.1.0.3.6 or later* |
| **Microsoft Windows (x64)**                                  |                                                          |                                                  |         |                  |                    |                                                              |
| ALL                                                          |                            ❌                             |                        ❌                         |    ❌    |        ❌         |         ❌          |                                                              |



# Altibase 6.5.1

## Altibase 6.5.1 Server & Client

> [!note]
>
> **Common**
>
> - Altibase server supports 64-bit only.
> - All versions of Altibase 6.5.1 support it unless the patch version is specified.
> - For all operating systems, all minor versions within the respective major version are supported, unless a particular minor version is specified.

| Operating System                                             | Altibase Server | Altibase Client<br />32-bit | Altibase Client<br />64-bit | Software Requirements                                 |
| :----------------------------------------------------------- | :-------------: | :-------------------------: | :-------------------------: | :---------------------------------------------------- |
| **UNIX**                                                     |                 |                             |                             |                                                       |
| AIX 6.1 TL3 AIX 6.1 TL9                                      |        ✅        |              ✅              |              ✅              |                                                       |
| AIX 7.1                                                      |        ✅        |              ✅              |              ✅              |                                                       |
| AIX 7.2                                                      |        ✅        |              ✅              |              ✅              |                                                       |
| HP-UX Itanium (IA-64) 11.31                                  |        ✅        |              ✅              |              ✅              |                                                       |
| Solaris 10 (Sun SPARC)                                       |        ✅        |              ✅              |              ✅              |                                                       |
| Solaris 11 (Sun SPARC)                                       |        ✅        |              ✅              |              ✅              | *- Altibase 6.5.1.4.2 or later*                       |
| **Linux (x86-64) - Red Hat-based**                           |                 |                             |                             |                                                       |
| Oracle Linux 6 / Red Hat Enterprise Linux 6 / CentOS 6       |        ✅        |              ✅              |              ✅              | *- glibc 2.12 ~ 2.33*                                 |
| Oracle Linux 7 / Red Hat Enterprise Linux 7 / CentOS 7       |        ✅        |              ✅              |              ✅              | *- glibc 2.12 ~ 2.33*                                 |
| Oracle Linux 8 / Red Hat Enterprise Linux 8 / CentOS 8 / Rocky Linux 8 |        ✅        |              ✅              |              ✅              | *- glibc 2.12 ~ 2.33*                                 |
| **Linux (x86-64) - Debian-based**                            |                 |                             |                             |                                                       |
| Ubuntu 12                                                    |        ✅        |              ✅              |              ✅              | *- glibc 2.17 ~ 2.33*                                 |
| **Linux on Power**                                           |                 |                             |                             |                                                       |
| POWER7 w/ Red Hat Enterprise Linux 6.5                       |        ✅        |              ✅              |              ✅              | *- glibc 2.12 ~ 2.33*                                 |
| POWER8 w/ Red Hat Enterprise Linux 7.1                       |        ✅        |              ✅              |              ✅              | *- glibc 2.12 ~ 2.33*                                 |
| **Linux on Power (Little Endian)**                           |                 |                             |                             |                                                       |
| POWER8(LE) w/ Red Hat Enterprise Linux 7.2                   |        ✅        |              ✅              |              ✅              | *- glibc 2.17 ~ 2.33* *- Altibase 6.5.1.4.5 or later* |
| POWER9(LE) w/ Red Hat Enterprise Linux 7.6                   |        ✅        |              ✅              |              ✅              | *- glibc 2.17 ~ 2.33* *- Altibase 6.5.1.7.6 or later* |
| **Microsoft Windows (x64)**                                  |                 |                             |                             |                                                       |
| Microsoft Windows Server 2008                                |        ✅        |              ✅              |              ✅              | *- Altibase 6.5.1.7.7 or later*                       |
| Microsoft Windows Server 2012                                |        ✅        |              ✅              |              ✅              | *- Altibase 6.5.1.7.7 or later*                       |
| Microsoft Windows Server 2016                                |        ✅        |              ✅              |              ✅              | *- Altibase 6.5.1.7.7 or later*                       |
| Microsoft Windows Server 2019                                |        ✅        |              ✅              |              ✅              | *- Altibase 6.5.1.7.7 or later*                       |
| Microsoft Windows 7                                          |        ✅        |              ✅              |              ✅              |                                                       |
| Microsoft Windows 8                                          |        ✅        |              ✅              |              ✅              |                                                       |
| Microsoft Windows 10                                         |        ✅        |              ✅              |              ✅              | *- Altibase  6.5.1.6.2 or later*                      |



## Altibase 6.5.1 Library & Tools

| Operating System                                             | PDO Driver<br/>PDO_ALTIBASE-1.x.x for PHP 5.3.3, 7.1.20 | PDO Driver<br />PDO_ALTIBASE-2.x.x for PHP 8.1.8 | Adapter for JDBC | Adapter for Oracle | Software Requirements                                        |
| :----------------------------------------------------------- | :-----------------------------------------------------: | :----------------------------------------------: | :--------------: | :----------------: | :----------------------------------------------------------- |
| **Unix**                                                     |                                                         |                                                  |                  |                    |                                                              |
| AIX 5.3                                                      |                            ❌                            |                        ❌                         |        ❌         |         ✅          |                                                              |
| AIX 6.1                                                      |                            ❌                            |                        ❌                         |        ✅         |         ✅          |                                                              |
| AIX 7.1                                                      |                            ❌                            |                        ❌                         |        ✅         |         ✅          |                                                              |
| AIX 7.2                                                      |                            ❌                            |                        ❌                         |        ✅         |         ✅          |                                                              |
| HP-UX Itanium (IA-64) 11.31                                  |                            ❌                            |                        ❌                         |        ✅         |         ❌          |                                                              |
| Solaris 10 (Sun SPARC)                                       |                            ❌                            |                        ❌                         |        ✅         |         ✅          | - *Adapter for Oracle : 6.5.1.9.3 or later*                  |
| Solaris 11 (Sun SPARC)                                       |                            ❌                            |                        ❌                         |        ✅         |         ✅          | - *Adapter for JDBC : 6.5.1.4.2 or later* - *Adapter for Oracle : 6.5.1.9.3 or later* |
| **Linux (x86-64) - Red Hat-based**                           |                                                         |                                                  |                  |                    |                                                              |
| Oracle Linux 6 / Red Hat Enterprise Linux 6 / CentOS 6       |                            ✅                            |                        ✅                         |        ✅         |         ✅          |                                                              |
| Oracle Linux 7 / Red Hat Enterprise Linux 7 / CentOS 7       |                            ✅                            |                        ✅                         |        ✅         |         ✅          |                                                              |
| Oracle Linux 8 / Red Hat Enterprise Linux 8 / CentOS 8 / Rocky Linux 8 |                            ✅                            |                        ✅                         |        ✅         |         ✅          |                                                              |
| **Linux (x86-64) - Debian-based**                            |                                                         |                                                  |                  |                    |                                                              |
| Ubuntu 12                                                    |                            ✅                            |                        ✅                         |        ✅         |         ✅          |                                                              |
| **Linux on Power**                                           |                                                         |                                                  |                  |                    |                                                              |
| POWER7 w/ Red Hat Enterprise Linux 6.5                       |                            ✅                            |                        ✅                         |        ✅         |         ❌          |                                                              |
| POWER8 w/ Red Hat Enterprise Linux 7.1                       |                            ✅                            |                        ✅                         |        ✅         |         ❌          |                                                              |
| **Linux on Power (Little Endian)**                           |                                                         |                                                  |                  |                    |                                                              |
| POWER8(LE) w/ Red Hat Enterprise Linux 7.2                   |                            ✅                            |                        ✅                         |        ✅         |         ❌          |                                                              |
| POWER9(LE) w/ Red Hat Enterprise Linux 7.6                   |                            ✅                            |                        ✅                         |        ✅         |         ❌          |                                                              |
| **Microsoft Windows (x64)**                                  |                                                         |                                                  |                  |                    |                                                              |
| ALL                                                          |                            ❌                            |                        ❌                         |        ❌         |         ❌          |                                                              |
