<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Solaris Setup Guide for Altibase](#solaris-setup-guide-for-altibase)
  - [Overview](#overview)
  - [Kernel Parameters](#kernel-parameters)
    - [Shared Memory](#shared-memory)
    - [Semaphore](#semaphore)
    - [How to Change](#how-to-change)
  - [User Settings](#user-settings)
    - [Resource Limitations](#resource-limitations)
    - [Environment Variables](#environment-variables)
    - [Terminal Configuration](#terminal-configuration)
  - [Overview](#overview-1)
    - [Setting Examples](#setting-examples)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Solaris Setup Guide for Altibase

## Overview

This document provides guides for setting appropriate values of kernel parameters and various user environment settings for installing and operating Altibase in the Solaris Operating System. In this document, the guide is presented only for operating system related items to be set before Altibase is installed. For the Altibase property configuration file (altibase.properties) for Altibase self-configuration, refer to the separate document "*Altibase Configuration File guide*".

The test environment of this document is as follows:

* ALTIBASE : Altibase 6 or later
* OS : Sun OS 5.8 ~ 5.10

## Kernel Parameters

This section describes the types of kernel parameters that need to be changed when operating Altibase on the Solaris OS, and explains why the settings need to be changed.

The last part introduces how to change kernel parameters in Solaris.

### Shared Memory

When developing an application, two or more processes need to exchange information. The operating system provides a resource called IPC (Inter Process Communication). The memory area used by two or more processes to exchange information among various IPC resources is called shared memory.

The shared memory can be set by dividing it into one or more areas by designating a unit. One shared memory area is called a segment.

For example, a user may set a shared memory having one segment at 10 megabytes, or a 100 megabyte shared memory by configuring a 10 megabyte area as 10 segments.

Altibase loads memory DB in the heap area of the process by default, but it can be loaded and used in shared memory depending on the user's settings. (Refer to the "*Altibase Property Setting Guide*" document for the setting method related to this.) Alternatively, the communication buffer of the client accessing the DBMS can be set to be exchanged through the shared memory. Therefore, it is necessary to change the kernel parameter settings for the maximum size of the part that uses memory or the number of segments.

The kernel parameters related to shared memory in a typical Unix system are as follows.

| Kernel Parameter | Description                                                  | Recommended Value |
| ---------------- | ------------------------------------------------------------ | ----------------- |
| shmmax           | The maximum size of one shared memory segment                | 2G + 1            |
| shmmni           | The maximum number of shared memory segments in the system   | 500 or more       |
| shmseg           | The maximum number of processes that can access one shared memory | 200 or more       |

#### Considerations When Loading Memory DB into Shared Memory

When loading a memory DB into shared memory, the following items should be additionally considered:

* shmmax

  In case of shmmax, one segment is created as much as the size of the STARTUP_SHM_CHUNK_SIZE item in the Altibase configuration file during the operation phase, so set it to a value larger than STARTUP_SHM_CHUNK_SIZE.

* Shmmni

  When memory DB usage increases, Altibase automatically increases the memory area. In this case, a set meant is also newly created. The size of this segment is set in the Altibase configuration file in EXPAND_CHUNK_PAGE_COUNT * 32K, so shmmni should be set as much as possible.

### Semaphore

This is a kind of IPC resource like shared memory. The difference is that shared memory is provided as a way to share data between processes, while semaphores are resources provided by the operating system as a way to implement synchronization between processes. Synchronization means that only one process can access and change a specific resource or object at a time. (Unlike mutex, inquiry is possible at the same time.)

Altibase uses a shared memory as a communication buffer between the two ends when an Altibase server and a client exist in the local server as described above. At this time, it is necessary to control the concurrency of the memory. (Because it should not write at the same time.)

In this case, a semaphore operation occurs to control access to read/write access to memory.

Depending on the semaphore operation, the process can go into a waiting state or a progress state. Since these semaphore operations occur simultaneously, it is necessary to set the appropriate number of semaphores and kernel parameters for the operation. 

The kernel parameters related to semaphore in the Unix system are as follows.

| Kernel Parameter | Description                                                  | Recommended Value |
| ---------------- | ------------------------------------------------------------ | ----------------- |
| semmns           | The maximum number semaphores in the system, and 16 bytes of kernel memory are allocated | 8192              |
| semmni           | The maximum number of semaphore sets can be set within 65535, and 84 bytes of kernel memory are allocated per set. | 5092              |
| semmsl           | The maximum number of semaphores in a set of semaphores and must be logically equal to or less than semmns. If set too large, several semaphore IDs can monopolize the entire system semaphore. | 2000              |
| semmap           | Semaphore space obtained by semget call                      | 5024              |
| semmnu           | The maximum number of undo structures in the system          | 1024              |
| semopm           | The maximum number of operations processed by semi system call | 512               |
| semume           | The maximum number of undo entries per process               | 512               |
| semvmx           | Limits the maximum value of one semaphore and does not specify a value greater than 32767 | 32767             |

### How to Change

In solaris, kernel parameters are set through the /etc/system file. Starting from 5.10, kernel parameters can be applied to each user account by introducing a project concept in addition to the existing method.

Here is an example of setting in both ways. Basically, access to the root account is required, and in order to apply properly, the system must be restarted after the change.

#### 5.10 or later

In Solaris 5.10, some of the existing kernel parameter items have disappeared, so the user can run the configuration items related to shared memory and semaphores at the shell prompt using the Solaris utilities projadd and projmod.

```
# projadd -U altibase -K "project.max-sem-ids=(priv,5029,deny)" user.altibase
# projmod -a -K "project.max-shm-memory=(priv, maximum physical memory, deny)" user.altibase
# projmod -a -K "process.max-sem-nsems=(priv,2000,deny)"  user.altibase
# projmod -a -K "process.max-sem-ops=(priv,512,deny)"  user.altibase
# projmod -a -K "project.max-shm-ids=(priv,1024,deny)" user.altibase
# projmod -a -K "project.max-msg-messages=(priv,100,deny)"  user.altibase
# projmod -a -K "project.max-msg-ids=(priv,100,deny)" user.altibase
# projmod -a -K "process.max-msg-qbytes=(priv,1048576,deny)" user.altibase
```

Note that max-shm-memory should be set the maximum value of physical memory.

The user can check the setting change with the following command.

```
# projadd –l
```



## User Settings

This describes resource limits, environment variables, and various environment settings of user accounts in the system for operating Altibase on the Solaris OS.

For details related to configuration refer to the guide provided by Solaris.

### Resource Limitations

In the Unix OS, logical limits for the resources available per user account are set. Among the resource limit items, the items in the general Unix OS that needed to be extended for stable service operation are as follows.

| Classification          | Description                                                  | Recommended Value |
| ----------------------- | ------------------------------------------------------------ | ----------------- |
| data seg size(data)     | The maximum size of one process data area                    | unlimited         |
| file size (fsize)       | The maximum size of files that can be created                | unlimited         |
| open files (nofiles)    | The maximum number of files that can be accessed by one process at the same time | unlimited         |
| max memory size (rss)   | The maximum size of available memory                         | unlimited         |
| virtual memory (memory) | The maximum size of available virtual memory                 | unlimited         |
| max user process        | The number of processes that can be created per user         | unlimited         |

It is intended to remove problems that may occur due to logical limitations even when expanding the memory and data file area used by a specific user. This setting has no effect on other processes. It is recommended to set the maximum value allowed by (unlimited if possible).

For example, the meaning of open files includes not only the files accessed by the process, but also the number of communication sockets. If Altibase is operated in an environment where this value is limited to 10, it means that more than 10 sessions can be accessed simultaneously. (Considering the file used by Altibase, there may not be an accessible session.)

To change the method, edit the environment configuration file using the ulimit command, edit the system resource configuration file, or use the kernel-related utilities provided for each operating system.

#### Hard-Limit & Soft-Limit

Resource limit values are divided into the concept of hard-limit and soft-limit. The hard-limit means the maximum value of the kernel-level resource limit that cannot be changed except the system administrator account (root), and the soft-limit means that the hard-limit can be changed within the current user account. (Refer to the ulimit -S / -H option for details.)

The soft-limit is effective while the user maintains a session by accessing it, and changes are immediately reflected. However, when other sessions of the same user account are connected, the existing soft-limit is reflected, so the ulimit command is often added to the user account configuration file. 

However, this method may not be intended due to the hard-limit, so it is recommended to systematically apply it through editing system-wide resource configuration files rather than applying user account units using environment configuration files.

For reference, Solaris does not have a system configuration file related to user resource limitation, and is described in /etc/system. There are also other way to use /etc/default/login or /etc/profile. 

### Environment Variables

The essential environment variables are as follows. The following environment variables must be set in the environment configuration file of the user account according to the syntax of the user's shell.

| Environment Variable | Description                                                  |
| -------------------- | ------------------------------------------------------------ |
| ALTIBASE_HOME        | Specifies the path where Altibase is installed.              |
| PATH                 | Specifies the path to use binary and shell scripts in ALTIBASE_HOME/bin regardless of the path. |
| LD_LIBRARY_PATH      | When using Altibase dynamic library, it specifies the path where the library exists. |

In addition, the following environment variable that exists only in Solaris must be added.

| Variable           | Description                                  |
| ------------------ | -------------------------------------------- |
| LD_LIBRARY_PATH_64 | Sets when linking dynamic library to 64-bit. |

#### Character Set Consideration

Prior to Altibase 5.3, a separate property existed in relation to the NLS_USE item in relation to the character set, but has been replaced by an environment variable starting from Altibase 5.3.

For this reason, if the user sets KO16KSC5601/MS949/UTF8, etc. for DB character set in US version of Altibase 5.3 or later, the user must set the environment variable ALTIBASE_NLS_USE. Otherwise, it is connected to the default setting of US7ASCII, and after input, it is searched in the form of an unknown string at the time of inquiry.

### Terminal Configuration

In addition to the considerations regarding the use of the character set mentioned in the [Environment Variables] section, the font of the terminal to be used must also be set the same as the character set in the DB.



## Overview

For stable operation of Altibase in the Solaris OS, kernel parameter setting and user environment setting must be performed in advanced. If the setting is not performed properly, it should be noted that the problem can be caused by each limit value even though the system has sufficient resources.

### Setting Examples

#### Kernel Parameters

Refer to the table below and set the appropriate kernel parameters.

| Classification | Kernel Parameter | Recommended Value | Remark                                  |
| -------------- | ---------------- | ----------------- | --------------------------------------- |
| Shared Memory  | shmmax           | 2G+1              | -                                       |
| Shared Memory  | shmmni           | 500               | -                                       |
| Shared Memory  | shmseg           | 200               | -                                       |
| Semaphore      | semmns           | 8192              | -                                       |
| Semaphore      | semmni           | 5029              | -                                       |
| Semaphore      | semmsl           | 2000              | Be carefult not to set as a large value |
| Semaphore      | semmap           | 5024              | -                                       |
| Semaphore      | semmnu           | 1024              | -                                       |
| Semaphore      | semopm           | 512               | -                                       |
| Semaphore      | semume           | 512               | -                                       |
| Semaphore      | semvmx           | 32767             | Generally does not exceed 32767.        |

For additional factors to be considered when loading a memory DB into shared memory, refer to the [Shared Memory] section.

#### User Resource Limitation

In the case of sh, bash, and ksh, examples of setting required environment variables using the environment setting file are as follows. In the case of csh, it is declared through a shell command such as setenv instead of export.

```
#For ALTIBASE
ALTIBASE_HOME=/ALTIBASE;  export ALTIBASE_HOME;
PATH=$ALTIBASE_HOME/bin:$PATH;  export PATH;
ALTIBASE_NLS_USE=MS949;  export ALTIBASE_NLS_USE;
LD_LIBRARY_PATH=$ALTIBASE_HOME/lib:$LD_LIBRARY_PATH;
export LD_LIBRARY_PATH;
 
LD_LIBRARY_PATH_64=$ALTIBASE_HOME/lib:$LD_LIBRARY_PATH_64;
export LD_LIBRARY_PATH_64;
 
 
#For Resource Limitation
ulimit –d unlimited  #data segment size,  data
ulimit –f unlimited  #file size, fsize
ulimit –n unlimited  #file descriptor(open files), nofiles
ulimit –v unlimited  #virtual memory, memory
```

For reference, in the case of ksh, an error may occur when defining another environment variable using the environment variable with being predefined.

