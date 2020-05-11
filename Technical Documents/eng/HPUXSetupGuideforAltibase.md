<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [HPUX Setup Guide for Altibase](#hpux-setup-guide-for-altibase)
  - [Overview](#overview)
  - [Kernel Parameters](#kernel-parameters)
    - [Shared Memory](#shared-memory)
    - [Semaphore](#semaphore)
    - [File Cache](#file-cache)
    - [Resource Limitation](#resource-limitation)
    - [How to Change](#how-to-change)
  - [User Settings](#user-settings)
    - [Resource Limitation](#resource-limitation-1)
    - [Environment Variables](#environment-variables)
  - [Multi-Thread Related Patch](#multi-thread-related-patch)
  - [Summary](#summary)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# HPUX Setup Guide for Altibase



## Overview

This document provides guides for setting appropriate values of kernel parameters and various user environment settings for installing and operating Altibase in Hewlett Packard Unix (UPUX) Operating System.

In this document, the guide is presented only for the operating system related items to be set before Altibase is installed, and refer to the separate document "Altibase Configuration File Guide" for setting Altibase properties for setting Altibase itself.



## Kernel Parameters

When operating Altibase on the HPUX operating system, it describes the types of kernel parameters that need to be changed and why they need to be changed and introduces how to change the kernel parameters.

For details related to each kernel parameter, please refer to the guide provided by HP.

### Shared Memory

When developing an application program, there is a need for two or more processes to exchange information. The operating system provides a resource called IPC (Inter Process Communication). The memory area used by two or more processes to exchange information among various IPC resources is called shared memory.

When the Altibase server and client use the IPC connection method, shared memory is used as a communication buffer, so the kernel parameter values such as the maximum size for the part using memory or the number of segments must be set correctly.

The recommended kernel parameters and Altibase values related to shared memory in a typical Unix system are as follows.

| Kernel Parameter | Description                                                  | Recommended Value |
| ---------------- | ------------------------------------------------------------ | ----------------- |
| shmmax           | The maximum size of one shared memory segment                | 2GB+1             |
| shmmni           | The maximum number of shared memory segments in the system   | 500 or more       |
| shmseg           | The maximum number of shared memory segments attached to one process | 200 or more       |

* IPC_CHANNEL_COUNT: Maximum number of IPC connections that can connect to the Altibase server at the same time

### Semaphore

This is a kind of IPC resource like shared memory. The different is the shared memory is provided as a way to shared data between processes, while semaphores are resources provided by the operating system as a way to implement synchronization between processes.

Synchronization means that only one process can access and change a specific resource or object at a time (unlike mutex, inquiry is possible at the same time).

As described above, Altibase uses shared memory as a communication buffer between both ends when Altibase server and client exist in the local server. At this time, it is necessary to control the concurrency of the memory. (Because the user should not write at the same time)

In this case, a semaphore operation occurs to control access to read/write access to memory.

Depending on the semaphore operation, the process can go into a waiting state or a progress state. Since these semaphore operations occur simultaneously, it is necessary to set the appropriate number of semaphores and kernel parameters for the operation.

The kernel parameters related to semaphores in a typical Unix system are as follows.

| Kernel Parameter | Description                                                  | Recommended Value |
| ---------------- | ------------------------------------------------------------ | ----------------- |
| semmni           | The maximum number of semaphore sets in the system. 84 bytes of kernel memory are allocated per set | 5029              |
| semmns           | The maximum number of semaphores in the system, with 16 bytes of kernel memory allocated | 8192              |
| semmsl           | The maximum number of semaphores in a set of semaphores and must be logically less than or equal to semmns<br />If set too large, several semaphore IDs can monopolize the entire system semaphore. | 2000              |
| semmnu           | The maximum number of undo structures in the system          | 1024              |
| semume           | The maximum number of undo entries per process               | 512               |
| semvmx           | The maximum value of one semaphore                           | 32767             |

* IPC_CHANNEL_COUNT: The maximum number of IPC connections that can connect to the Altibase server at the same time

### File Cache

This kernel parameter is not an essential element to change, but the proper file cache setting prevents the swap out of the memory are used by Altibase and suppresses the requirement for swap out, resulting in the disk of the operating system layer due to swapping. It is recommended to minimize the phenomenon that the I/O delay time leads to the deflation of Altibase.

File cache is a kind of system buffer managed at the operating system level to solve the bottleneck caused by the speed difference between main memory and auxiliary memory. These file caches are managed by unique policies of each operating system. But commonly have a direct correlation with the swap policy.

Swapping itself has the usefulness of handling applications or data files larger than main memory, but in systems where long-term resident applications such as DBMS are operated, the disk I/O delay of the operating system layer due to swapping since the response time of the DBMS may be irregular or delayed with time, file cache is a consideration factor depending on the system use.

Therefore, in order to guarantee Altibase's consistent response time, it is recommended to set file cache and swap-related kernel parameters in advance so that swap does not occur as much as possible.

#### Configuration on HPUX

It is recommended to adjust the file cache through the kernel parameters below.

| Kernel Parameter | Description                                                  | Recommended Value |
| ---------------- | ------------------------------------------------------------ | ----------------- |
| dbc_min_pct      | Limits the minimum size of the file cache to a percentage of total memory. The default value is 5%, and renamed to filecache_min from HPUX 11.31. | 5%                |
| dbc_max_pct      | Limits the maximum size of the file cache to a percentage of total memory. The default value is 50%. Since HPUX 11.31, the name is changed to filecache_max. | 5~20%             |

For reference, HP's recommendation for dbc_max_pct is 20% for systems with 8 GB or less physical memory and 10% for systems with 8 GB or more, so refer to it.

### Resource Limitation

In the case of HPUX, some of the resource limit items are set through the following kernel parameter changes, not the user configuration file setting using the ulimit, which is commonly used.

| Kernel Parameter | Description                                                  | Recommended Value                                            |
| ---------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| maxdiz           | The sum of allocable data segments by one 32-bit process     | 2 GB                                                         |
| maxdsiz_64bit    | The sum of allocable data segments by one 64-bit process     | 1 TB<br/>Up to 4 TB<br/>Considering the maximum size of the predicted Altibase process |
| max_thread_proc  | The maximum number of threads a process can have             | 600 or more                                                  |
| maxfiles         | The maximum number of files that a process can open simultaneously (soft-limit)<br/>Can be increased to maxfiles_lim (hard-limit). | 2048 or more                                                 |
| nproc            | The maximum number of processes in the system                | 6142                                                         |
| maxusers         | Default values of nproc, callout, ninode, and file           | 124<br/>Only under 11.23                                     |

In the case of “maxusers”, since HPUX 11.23 has disappeared, it is not necessary to consider it in HPUX 11.23 or later. In HPUX 11.23 and below, instead of setting “nproc” directly, setting “maxusers” to 124 is replaced.

### How to Change

In the case of HPUX, the Tunable kernel parameter utility (kmtune in HPUX 11.11, kctune is mainly used in HPUX 11.23) or the utility called sam, which can change all kernel parameters in the system, is mainly used to modify kernel parameters. Here is an example of using kctune.

Generally, the user needs to connect with the root account, and it is recommended to restart the system after changing to properly apply when the kernel parameters applied in real time.

#### Shared Memory

If there was no separate configuration before, the user can change shmmni and shmseg by changing kernel parameters related to shared memory.

Shared memory change example

```
$ kctune shmmni=500
$ kctune shmseg=200
```

#### Semaphore

If there was no separate setting before, the user can change only semmns, semmni, semmnu, and semume by changing kernel parameters related to semaphores.

Semaphore change example

```
$ kctune semmns=8192
$ kctune semmni=5029
$ kctune semmnu=1024
$ kctune semume=512
```

#### File Cache

For dbc_max_pct, according to HP's recommendation, 20% is recommended for systems with 8 GB or less physical memory, and 10% for systems with 8 GB or more.

Example of file cache change

```
$ kctune dbc_min_pct=5
$ kctune dbc_max_pct=10
Or
$ kctune filecache_min=5%
 
$ kctune filecache_max=10%
```

#### Resource Limitation	

The method to change the kernel parameters related to the resource limit mentioned above is as follows.

Example of changing resource limits

```
$ kctune maxdsiz=2147483648
$ kctune maxdsiz_64bit=4396972765184
$ kctune max_thread_proc=600
$ kctune maxfiles=2048
$ kctune nproc=6142
```

In HPUX 11.23 and below, "nproc" is not set directly, but "maxusers" is set to 124.



## User Settings

This section describes resource limits, environment variables, and various environment settings of user accounts in the system for operating Altibase in the HPUX operating system.

Refer to the guide provided by HP for specific commands and specifics related to configuration.

### Resource Limitation

In the UNIX operating system, logical limits are set for available resources on a user account basis. Among the resource limit items, general items that need to be expanded for stable service operation as follows.

| Item                    | Description                                             | Recommended Value |
| ----------------------- | ------------------------------------------------------- | ----------------- |
| virtual memory (memory) | The maximum size of available virtual memory            | unlimited         |
| open files (nofiles)    | The maximum number of files that can be accessed by one | unlimited         |
| max user process        | The number of processes that can be created per user    | unlimited         |
| max memory size (rss)   | The maximum size of available memory                    | unlimited         |
| file size (fsize)       | The maximum size of files that can be created           | unlimited         |
| data seg size(data)     | The maximum size of one process data area               | unlimited         |

The resource limit change is to proactively remove problems that may occur due to logical limitations even when there is a lot of physical resources when expanding the memory and dat file area used by a specific user. It is recommended to set.

For example, the meaning of open files includes the number of communication sockets as well as the files accessed by the process, so the maximum number of concurrent clients, the number of data files used simultaneously, the number of redo log files, and the number of trace log files must be considered.

To change the method, edit the environment configuration file using the ulimit command, edit the system resource configuration file, or use the kernel-related utilities provided for each operating system.

#### Hard-Limit & Soft-Limit

Resource limit values are divided into the concept of hard-limit and soft-limit.

The hard-limit means the maximum value of the kernel-wide resource limit that cannot be changed except the root account, and the soft-limit means that the hard-limit can be changed within the current user account. (Refer to the ulimit –S / -H option for details.)

The soft-limit is effective while the user maintains a session by accessing it, and changes are immediately reflected. However, if other sessions of the same user account are connected, the existing soft-limit is reflected, so it is recommended to add the ulimit command to the user account configuration file.

However, this method may not be intended due to the global hard-limit, so it is recommended to systematically apply it through editing system-wide resource configuration files rather than applying user account units using environment configuration files.

However, since HPUX does not have system-wide resource configuration file, sam or kctune is used to change the hard-limit for resource limitation.



### Environment Variables

The environment variables that must be set are as follows. Set the following environment variables in the environment configuration file of the user account according to the user's shell syntax.

| Environment Variable | Description                                                  |
| -------------------- | ------------------------------------------------------------ |
| ALTIBASE_HOME        | Specifies the path where Altibase is installed.              |
| PATH                 | Adds ALTIBASE_HOME/bin. This is the setting to execute binary and shell scripts in this path regardless of the path. |
| LD_LIBRARY_PATH      | Adds ALTIBASE_HOME/lib. Configuration for using Altibase's dynamic library. |

In addition, the following environment variables that exist only in HPUX must be added.

| Environment Variable | Description                                                  |
| -------------------- | ------------------------------------------------------------ |
| SHLIB_PATH           | Adds ALTIBASE_HOME/lib. Set when linking a dynamic library with 32 bits. |

#### Settings for Multi-threaded Application (1)

For Altibase, a multi-thread-based application program, a separate environment variable setting is required. For reference, this document mentions only representative ones, and it should be noted that all multi-thread-related environment variables supported by HPUX need to be considered.

All of the elements below are essential. Among them, the environment variable PTHREAD_FORCE_SCOPE_SYSTEM related to the MxN thread model must be set.

| Environment Variable        | Description                                        | Remark                           |
| --------------------------- | -------------------------------------------------- | -------------------------------- |
| PTHREAD_FORCE_SCOPE_SYSTEM  | Set the thread contention area as system           | Supported in HPUX 11.23 or later |
| PERF_ENABLE                 | Omit part of user-space sleep queue operation      | HPUX 11.23 only                  |
| PTHREAD_FAST_SHARED_OBJECTS | Application of private algorithm to shared objects | Supported in HPUX 11.31 or later |
| PTHREAD_DISABLE_HANDOFF     | Application of multiple CPU environment            | Supported in HPUX 11.23 or later |

#### Settings for Multi-threaded Application (2)

It is mentioned that this is also a tunable element that cannot provide a recommended value as a setting for a multi-thread-based application, or something to be considered in the initial stage.

In an operating system that uses only one memory allocation area to request memory for a specific process, when multiple threads of a multi-threaded application program concurrently request memory (malloc, free), contention due to a lock operation occurs, resulting in performance degradation.

To solve this problem, HPUX provides up to 64 memory allocations per process, called arenas, to distribute threads between arenas to reduce lock contention caused by memory request.

It can be set with the following environment variables.

| Environment Variable | Description                                                  | Remark                                                       |
| -------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| _M_ARENA_OPTS=x:y    | x: The number of arenas to be allocated per process. The default value is 8. [Range: 1-64]<br/><br/>y: The expansion unit of the arena, expressed as the number of memory pages. The default is 32. [Range: 1-4096] | The larger the number of arenas (x), the more the system memory usage increases and the smaller the performance of the Altibase decreases, so it is necessary to set the appropriate number. |

Generally, if it is not a multi-threaded application, it operates as one arena regardless of setting, and when it is set as an invalid value, it operates as a default.

For example, if the user sets up as follows, 24 arenas are allocated to multi-threaded applications only, and each arena increases in units of 64*4KB (typical memory page size) when expanded.

_M_ARENA_OPTS setting example

```
$ export _M_ARENA_OPTS = 24:64
```

In general, the higher the number of threads in an application program, the higher the number of arenas to improve performance.

However, if it is set too large, fragmentation of the heap area may occur, and the size of the process may be too large due to inefficient use of memory.

For example, if there is a concern about insufficient memory due to the lack of physical memory of the system itself, in some cases, it is set to 1: 8 to operate as a single-threaded application program. If it is a bottleneck, it is common to increase the value within the resource range.

## Multi-Thread Related Patch

Altibase is a single process, multi-threaded application. Therefore, a multi-thread related HPUX patch is needed. Among these, 'thread library cumulative patch' has a direct effect on performance, so it must be checked whether a patch exists.

The method to check the patch list of the current system is as follows.

How to check multi-thread related patch

```
$ swlist -l patch | grep pthread
$ PHCO_38955    1.0          pthread library cumulative patch
$ PHKL_35709    1.0          pthread_cond_timedwait,hires timers,callout
$ PHKL_37122    1.0          pthread_condvar_prio_boost patch
```

In addition to this, it is recommended to apply the latest patch to avoid various problems known from HPUX.

#### Additional Considerations When Applying PHCO_33675 and PHCO_34718

When the patch was applied in HPUX 11.23, it was reported through HP that the application program kept the shared mutex for a longer period of time and deteriorated the performance.

After checking the patch list, if the patch exists, the following environment variables should be added and set to 1 to restore system performance.

| Environment Variable         | Description                                         | Remark                        |
| :--------------------------- | :-------------------------------------------------- | :---------------------------- |
| PTHREAD_SHARED_MUTEX_OLDSPIN | Performance downgrade due to PHCO_33675, PHCO_34718 | Considered only on HPUX 11.23 |



## Summary

For stable operation of Altibase in the HPUX operating system, it is necessary to perform kernel parameter settings and user environment settings in advance. If the setting is not performed properly, it should be noted that the problem can be caused by the limit values even though there are sufficient system resources.

#### Kernel Parameters

Refer to the table below to set the kernel parameters properly. For reference, in HPUX, some of the resource limit items are adjusted by changing kernel parameters.

| Classification  | Kernel Parameter | Recommended Value          | Remark                                                       |
| :-------------- | :--------------- | :------------------------- | :----------------------------------------------------------- |
| Shared memory   | shmmni           | 500 or more                | > shmseg                                                     |
| Shared memory   | shmseg           | 200 or more                |                                                              |
| Semaphore       | semmns           | 8192                       |                                                              |
| Semaphore       | semmni           | 5029                       |                                                              |
| Semaphore       | semmnu           | 5029                       | semmni                                                       |
| Semaphore       | semume           | 5029                       | semmni                                                       |
| File cache      | dbc_min_pct      | 5 or less                  |                                                              |
| File cache      | dbc_max_pct      | 20 or less                 | 20% recommended for systems with 8 GB or less physical memory, 10% recommended for systems with 8 GB or more |
| Resource limit  | maxdsiz          | 2GB                        | Compatible with data seg size (32bit)                        |
| Resource limit  | maxdsiz_64bit    | 1 TB / Maximum: around 4TB | Compatible with data seg size (64bit)                        |
| Resource limit  | maxfiles         | 5029 or more               | Compatible with open files                                   |
| Resource limit  | max_thread_proc  | 5029 or more               |                                                              |
| Resource limit  | nproc            | 6142                       | Compatible with max user process<br />>= semmnu + 4          |
| Resource limite | maxusers         | 124                        | Not available starting in HPUX 11.23                         |

####  User Resource Limitation

Please refer to the table below and set it as unlimited as possible.

| Classification        | Description                                                  | Recommended Value                         |
| --------------------- | ------------------------------------------------------------ | ----------------------------------------- |
| data set size (data)  | The maximum size of process data area                        | maxdsiz<br />maxdsiz_64bit<br />unlimited |
| file size             | The maximum size of created file                             | unlimited                                 |
| open files (no files) | The maximum number of files that can be accessed by more process at the same time | maxfiles<br />unlimited                   |
| max memory size (rss) | The maximum size of available memory                         | unlimited                                 |
| max user process      | The number of processes that can be created per user         | nproc<br />unlimited                      |

#### User Environment Variables

In case of sh, bash, ksh, examples of setting required environment variables using the environment setting file are as follows. In the case of csh, it is set through a shell command such as serene instead of export.

User environment variable setting example

```
# For Multi-Threaded Applications
PTHREAD_FORCE_SCOPE_SYSTEM=ON; export PTHREAD_FORCE_SCOPE_SYSTEM;
PTHREAD_FAST_SHARED_OBJECTS=ON; export PTHREAD_FAST_SHARED_OBJECTS;
PTHREAD_DISABLE_HANDOFF=ON; export PTHREAD_DISABLE_HANDOFF;
PERF_ENABLE=1; export PERF_ENABLE;
_M_ARENA_OPTS=8:32; export _M_ARENA_OPTS;
 
# For Altibase
ALTIBASE_HOME=/ALTIBASE; export ALTIBASE_HOME;
PATH=$ALTIBASE_HOME/bin:$PATH; export PATH;
ALTIBASE_NLS_USE=MS949; export ALTIBASE_NLS_USE;
SHLIB_PATH=$ALTIBASE_HOME/lib:$SHLIB_PATH; export SHLIB_PATH; # For 32bit
LD_LIBRARY_PATH=$ALTIBASE_HOME/lib:$LD_LIBRARY_PATH; export LD_LIBRARY_PATH; # For 64bit
 
# For Resource Limitation
ulimit –f unlimited  # file size, fsize
ulimit -m unlimited  # max memory size, rss
```

For reference, in the case of ksh, an error may occur when defining another environment variable using the environment variable without the environment variable being predefined.

In the above example, “_M_ARENA_OPTS” is simply a default value, and should be properly set according to the system. For details, refer to “Configuration for Multi-threaded Application (2)” in the [Environment Variables] section.

In addition, refer to "Additional consideration when applying PHCO_33675 and PHCO_34718" in the [Multi-thread related patches] section.