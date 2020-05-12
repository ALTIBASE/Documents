<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [AIX Setup Guide for Altibase](#aix-setup-guide-for-altibase)
  - [Overview](#overview)
  - [Kernel Parameters](#kernel-parameters)
    - [Posix AIO](#posix-aio)
    - [File Cache](#file-cache)
    - [Configuration on AIX](#configuration-on-aix)
    - [Resource Limitations](#resource-limitations)
    - [How to Change](#how-to-change)
  - [User Settings](#user-settings)
    - [Resource Limitations](#resource-limitations-1)
    - [Hard-Limit & Soft-Limit](#hard-limit--soft-limit)
    - [Environment Variables](#environment-variables)
  - [Summary](#summary)
    - [Setting Examples](#setting-examples)
  - [Enclosure](#enclosure)
    - [AIX Memory Related Patches](#aix-memory-related-patches)
    - [Limit of the Number of IPC Channels](#limit-of-the-number-of-ipc-channels)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# AIX Setup Guide for Altibase



## Overview

This document provides guides for setting appropriate values and various user environment settings of kernel parameters for installing and operating Altibase in the AIX (Advanced Interactive eXecutive) Operating System.

In this document, the guide is presented only for operating system related items to be set before Altibase is installed, and refer to the separate document "*Altibase Configuration File Guide"* for setting Altibase properties for setting Altibase itself.



## Kernel Parameters

When operating Altibase on the AIX OS, it describes the types of kernel parameters that need to be changed, and why the settings need to be changed, and introduces how to change the kernel parameters.

For details related to each kernel parameter, refer to the guide provided by IBM.

### Posix AIO

Posix AIO is a kernel parameter in AIX that allows a process to simultaneously process disk I/O processing and application program operations, resulting in improved performance.

If the corresponding kernel parameter is not set, Altibase cannot be used, so it must be set in advance.

However, starting from AIX 6.1, the default value of Posix AIO is amiable, there is no need to set it separately.

### File Cache

This kernel parameter is not an essential element to change, but the proper file cache setting prevents the swap out of the memory area used by Altibase and suppresses the requirement for swap out. It is recommended to minimize the phenomenon that the I/O delay time leads to the degradation of Altibase.

For reference, there are no relevant parameters under AIX 5.2 ML03, and there is no change starting from AIX 6.1, so it is not necessary to refer to it depending on the operation system version.

File cache is a kind of system buffer managed at the operating system level to solve the bottleneck caused by the speed difference between main memory and auxiliary memory. These file caches are managed by unique policies of each operating system, but commonly have a direct correlation with the swap policy.

Swapping itself has the usefulness of handling applications or data files larger than main memory, but in systems where long-term resident application such as DBMS are operated, the disk I/O delay of the operating system layer due to swapping since the response time of the DBMS may be irregular or delayed with time, file cache is a consideration factor depending on the system use.

Therefore, in order to guarantee Altibase's consistent response time, it is recommended to set the file cache and swap-related kernel parameters in advance so that swap does not occur as much as possible.

### Configuration on AIX

The default memory manager of AIX is to convert unused memory areas to file cache as much as possible.

In this state, if an additional memory allocation request occurs and the free memory is insufficient at the moment, the process allocates the swapped-out area in the memory or file cache area that is not easily accessed.

At this time, when a transaction approaching the swapped out area occurs, the performance is not uniform.

In this way, the process by which the memory manager acquires the memory requested by the process or the file cache in order to allocate additional memory is called stealing. The stealing target can be specified by the file cache related kernel parameter lru_file_repage.

Generally, three kernel parameters are changed as well as lru_file_repage.

| Kernel Parameter | Recommended Value | Remark                                         |
| ---------------- | ----------------- | ---------------------------------------------- |
| minperm          | 10%               | -                                              |
| lru_file_repage  | 0                 | Supported in AIX 5.2 ML5, AIX 5.3 ML2 or later |
| strict_maxclient | 0                 | Supported in AIX 5.2 ML4 or later              |

When set as above, stealing occurs only in the file cache when the file cache share compared to the total memory is used above minperm.

Since this setting can be checked during AIX operation, if performance or other problems occur, it is recommended to change it in consultation with AIX engineers.

### Resource Limitations

In the case of AIX, some of the resource limit items are set through the following kernel parameter changes, not the user configuration file setting using ulimit, which is commonly used.

Altibase is a single-process, multi-thread-based application program, so if the system does not have an application program specifically running outside of Altibase, there is no need to consider the number of process limits per user. In some cases, it may be necessary to appropriately expand the limit on the number of processes per user by predicting the number.

The relevant kernel parameters are as follow.

| Kernel Parameter                             | Description                                          | Recommended Value                                            |
| -------------------------------------------- | ---------------------------------------------------- | ------------------------------------------------------------ |
| Maximum number of PROCESSES allowed per user | The number of processes that can be created per user | More than the number of processes that can be running simultaneously |

### How to Change

To change the kernel parameters related to file cache, use the virtual memory-related kernel utility emo, and for other changes, describe the method using the system kernel-related utility smit.

Generally, the user needs to connect to the root account, and it is recommended to restart the system after changing to properly apply even the kernel parameters applied in real time.

#### Posix AIO

After running smit, move the items in the order of "Devices", "Asynchronous I/O" to changed the defined state of "Configured Defined Asynchronous I/O" to Available.

However, if only this process is performed, the following process must be performed as the previous Posix AIO setting may be reset when the system is restarted.

After running smit, move the items in the order of “Devices”, “Asynchronous I / O”, “Posix Asynchronous I / O”, and “Change / Show Characteristics of Asynchronous I / O”,
change the item of “STATE to be configured at system restart” to Available.

The current configuration of AIO-related kernel parameter can be checked as follows.

###### Check AIO related kernel parameter settings

```
# lsdev –C | grep aio
aio0         Available               Asynchronous I/O (Legacy)
posix_aio0  Available               Posix Asynchronous I/O
```

##### File Cache

The change method is as follows.

###### How to change file cache

```
# vmo -p -o minperm%=10
# vmo -p -o lru_file_repage=0
# vmo -p -o strict_maxclient=0
```

The confirmation method is as follows.

###### How to check file cache

```
# vmo –L
```

##### Resource Limitation

After running smit, move to "System Environments", "Change/Show Characteristics of Operating System", and change the "Maximum number of PROCESSES allowed per user" value to the number of processes that can be run simultaneously.



## User Settings

This describes resource limits, environment variables, and various environment settings of user accounts in the system for operating Altibase in the AIX OS.

For instructions and specifics related to configuration, refer to the guide provided by IBM.

### Resource Limitations

In the Unix OS, logical limits for the resource available per user account are set.

Among the resource limit items, the items in the general Unix OS that need to be extended for stable service operation are as follows.

| Classification          | Description                                                  | Recommended Value |
| ----------------------- | ------------------------------------------------------------ | ----------------- |
| data seg size(data)     | The maximum size of one process data area                    | unlimited         |
| file size (size)        | The maximum size of files that can be created                | unlimited         |
| open files (nofiles)    | The maximum number of files that can be accessed by one process at the same time | unlimited         |
| max memory size (rss)   | The maximum size of available memory                         | unlimited         |
| virtual memory (memory) | The maximum size of available virtual memory                 | unlimited         |
| max user process        | The number of processes that can be created per user         | unlimited         |

It is intended to remove problems that may occur due to logical limitations even when there are abundant physical resources when expanding the memory and data file area used by a specific user. This setting has no effect on other processes. It is recommended to set the maximum value allowed by (unlimited if possible).

For example, the meaning of open files includes not only the files accessed by the process, but also the number of communication sockets. If Altibase is operated in an environment where this value is limited to 10, it means that more than 10 sessions can be accessed simultaneously. (Considering the file used by Altibase, there may not be an accessible session.)

To change the method, edit the environment configuration file using, the ulimit command, edit the system resource configuration file, or use the kernel-related utilities provided for each operating system.

### Hard-Limit & Soft-Limit

Resource limit values are divided into the concept of hard-limit and soft-limit. The hard-limit means the maximum value of kernel-level resource limit that cannot be changed except the system administrator account (root), and the soft-limit means that the hard-limit can be changed within the current user account (refer to the ulimit -S/-H option for details.)

However, this method may not be intended due to the global hard-limit, so it is recommended to systematically apply it through editing system-wide resource configuration files rather than applying user account units using environment configuration files.

For reference, the system configuration file related to user resource limit in AIX is /etc/security/limits.

### Environment Variables

#### Setting for Multi-Threaded Applications 

Separate environment variables need to be set for Altibase, a multi-thread based application program. For reference, this document mentions only representative ones, but is should be noted that all environment variables related to multi-threads supported by AIX need to be considered.

The following items can run Altibase without setting the recommended environment variables in order to prevent performance degradation in a multi-threaded SMP system, but since it can cause failure due to unknown reasons, it must be set.

| Environment Variable   | Description                                                  |
| ---------------------- | ------------------------------------------------------------ |
| AIXTHREAD_MNRATIO      | The number of k kernel threads for processing n user threads |
| AIXTHREAD_SCOPE        | Sets the thread model to 1:1                                 |
| AIXTHREAD_MUTEX_DEBUG  | The mutex and condition variables being used by the pthread library,<br />The overhead of the read/write lock used by the debugger.<br />Sets to remove. |
| AIXTHREAD_RWLOCK_DEBUG | The mutex and condition variables being used by the pthread library,<br />The overhead of the read/write lock used by the debugger.<br />Sets to remove. |
| AIXTHREAD_COND_DEBUG   | The mutex and condition variables being used by the pthread library,<br />The overhead of the read/write lock used by the debugger.<br />Sets to remove. |
| SPINLOOPTIME           | The number of attempts to acquire a lock in the state of CPU resource acquisition |
| YIELDLOOPTIME          | The number of times to yield CPU resources while holding lock |
| MALLOCMULTIHEAP        | Sets up in a multi-threaded environment that uses malloc     |
| AIXTHREAD_MUTEX_FAST   | As an option to change the operating system's internal mutex_locking behavior.<br />If the mutex_contention is severe, set it to ON to improve the performance.<br />Can be represented. It is provided in AIX 5.2 and later. |

More information on environmental variables can be found on the IBM website.



## Summary

For stable operation of Altibase on the AIX operating system, kernel parameter settings and user environment settings must be performed in advance. If the setting is not performed properly, it should be noted that the problem can be caused by each limit value even though the system has sufficient resources.

### Setting Examples

#### Kernel Parameters

Refer to the table below and set the appropriate kernel parameters. For reference, in AIX, some of the resource limit items are adjusted by changing kernel parameters.

| Classification      | Kernel Parameter                                 | Recommended Value                                            | Remark                                                 |
| ------------------- | ------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------ |
| Posix AIO           | Configure Defined Asynchronous I/O               | Available                                                    | Required under AIX 6.1                                 |
| File Cache          | lru_file_repage                                  | 0                                                            | Considered under AIX6.1<br/>(Requires lru_file_repage) |
| File Cache          | strict_maxclient                                 | 0                                                            | Considered under AIX6.1<br/>(Requires lru_file_repage) |
| File Cache          | minperm                                          | 10                                                           | Considered under AIX6.1<br/>(Requires lru_file_repage) |
| Resource limitation | The maximum number of PROCESSES allowed per user | More than the number of processes that can be running simultaneously | Corresponds to max user process                        |

#### User Resource Limits

Refer to the table below, if possible, set it to unlimited.

| Classification        | Description                                                  | Recommended Value                            |
| :-------------------- | :----------------------------------------------------------- | :------------------------------------------- |
| data seg size(data)   | The maximum size of process data area                        | unlimited                                    |
| file size (fsize)     | The maximum size of created file                             | unlimited                                    |
| open files (nofiles)  | The maximum number of files that can be accessed by one process at the same time | unlimited                                    |
| max memory size (rss) | The maximum size of available memory                         | unlimited                                    |
| max user process      | The number of processes that can be created per user         | Maximum number of PROCESSES allowed per user |

#### User Environment Variables

In the case of sh, bash, and ksh, examples of settings required environment variables using the environment setting file are as follows. In the case of csh, it is declared through a shell command such as setenv instead of export.

###### User Environment Variable Setting Examples

```
#For Multi-Threaded Application
AIXTHREAD_MNRATIO=1:1; export AIXTHREAD_MNRATIO
AIXTHREAD_SCOPE=S; export AIXTHREAD_SCOPE
AIXTHREAD_MUTEX_DEBUG= OFF; export AIXTHREAD_MUTEX_DEBUG
AIXTHREAD_RWLOCK_DEBUG=OFF; export AIXTHREAD_RWLOCK_DEBUG
AIXTHREAD_COND_DEBUG = OFF; export AIXTHREAD_COND_DEBUG
SPINLOOPTIME = 1000; export SPINLOOPTIME
YIELDLOOPTIME = 50; export YIELDLOOPTIME
MALLOCMULTIHEAP=1; export MALLOCMULTIHEAP
 
# For Resource Limitation
ulimit –d unlimited  #data segment size, data
ulimit –f unlimited  #file size, fsize
ulimit –n unlimited  #file descriptor(open files), nofiles
ulimit –m unlimited  #max memory size, rss
```

For reference, in the case of ksh, an error may occur when defining another environment variable using the environment variable with it being predefined.



## Enclosure

### AIX Memory Related Patches

There is a bug that can cause a memory leak in the heapmin function provided by the AIX platform.

Related IBM official document is as follows.

http://www-01.ibm.com/support/docview.wss?uid=swg1IV28577

As a measure of this, the user must patch or upgrade to the AIX native compiler where AIX bug IV28577 is resolved.

It can be checked whether or not the patch is done with the following command.

###### Check heapmin Related Patch

```
-bash-3.2$ instfix -i | grep IV28577
All filesets for IV28577 were found.
```

If there is no patch, it is recommended that an AIX engineer perform a patch or upgrade because no return value appears.

In addition, it is recommended to apply the latest patch to avoid various problems known in AIX.

### Limit of the Number of IPC Channels

Among the semaphore parameters of AIX, the semume value basically limits the number of semaphore undo entries. It is automatically set in AIX and set to 1024, and cannot be changed by the user.

Altibase uses undo entries to ensure resource between IPC connections, and from Altibase 5.1.5.72 or later, undo entries for each IPC channel have been changed from the previous two to use three.

Since the semume (number of undo entry resources) is fixed at 1024, Altibase uses 2 or 3 undo entries per IPC channel based on version 5.1.5.72, so the maximum number of IPC channels that can be used is limited.

Therefore, the maximum number of IPC channels that can be used for each version is as follows: 

* Up to 512 IPC channels (= 1024/2) can be used under 5.1.5.72 version
* Up to 341 IPC channels (= 1024/3) can be used in 5.1.5.72 or later

In other words, since the OS semaphore resource value (semume) cannot be arbitrarily changed in AIX, only 341 or more IPC connections can be used in AIX equipment.
