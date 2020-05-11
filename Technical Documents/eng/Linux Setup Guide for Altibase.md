<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Linux Configuration Guide for Altibase](#linux-configuration-guide-for-altibase)
  - [Overview](#overview)
  - [Linux Compatibility](#linux-compatibility)
    - [glibc Compatibility Version](#glibc-compatibility-version)
    - [glibc Recommended Version](#glibc-recommended-version)
    - [How to Check the glibc Version](#how-to-check-the-glibc-version)
  - [Kernel Parameters](#kernel-parameters)
    - [CPU Frequency Governor](#cpu-frequency-governor)
    - [RemoveIPC](#removeipc)
    - [Swappiness](#swappiness)
    - [THP(Transparent Huge Pages)](#thptransparent-huge-pages)
    - [max_map_count](#max_map_count)
    - [Shared Memory](#shared-memory)
    - [Semaphore](#semaphore)
  - [How to Change Kernel Parameters](#how-to-change-kernel-parameters)
    - [CPU frequency Governor](#cpu-frequency-governor)
    - [RemoveIPC](#removeipc-1)
    - [swappiness](#swappiness)
    - [max_map_count](#max_map_count-1)
    - [Shared Memory and Semaphore](#shared-memory-and-semaphore)
  - [User Setting](#user-setting)
    - [Resource Limitation](#resource-limitation)
    - [Related Error Message](#related-error-message)
    - [View and Change Resource Settings](#view-and-change-resource-settings)
    - [How to Change the Settings](#how-to-change-the-settings)
    - [Environment Variables](#environment-variables)
  - [Others](#others)
    - [Red Hat Enterprise Linux Recommended Swap Size](#red-hat-enterprise-linux-recommended-swap-size)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Linux Configuration Guide for Altibase



## Overview

This document provides a guide to kernel parameters and OS user configuration for stable operation of ALtibase server on the Linux system.

This document is based on the version below:

* Altibase 5.5.1 or later

* Red Hat Enterprise Linux 6 or later



## Linux Compatibility

Linux has many distribution types, but Altibase compatibility check is based on glib version regardless of distribution type and kernel version.

### glibc Compatibility Version

Starting from Altibase 5.5.1, the compatibility is checked based on the glibc version. The glibc versions with guaranteed compatibility for each Altibase server version are as follows.

| Altibase Server Version | glibc Version |
| ----------------------- | ------------- |
| Altibase 7.1.0          | 2.12~2.20     |
| Altibase 6.5.1          | 2.12~2.20     |
| Altibase 6.3.1          | 2.3.4~2.20    |
| Altibase 6.1.1          | 2.3.4~2.20    |
| Altibase 5.5.1          | 2.3.4~2.20    |

### glibc Recommended Version

glibc-2.12-1.166.el6_7.1 or later is recommended.

In the previous version of glibc, there was a bug in which a system call (malloc/free) function could cause deadlock due to a race condition.

### How to Check the glibc Version

How to check the glibc version is as follows.

```
$ rpm -q glibc
```



## Kernel Parameters

This section describes the types of kernel parameters, recommended values, and recommended reasons for configuring Altibase in Linux to operate stably.

The recommended parameter types are as follows:

* CPU frequency Governor
* RemoveIPC
* swappiness
* THP
* max_map_count
* Shared memory
* Semaphore

### CPU Frequency Governor

Altibase server is a system that absolutely requires maximum processing performance and shortest response time, so CPU clock speed should always be kept at the highest level.

Linux keeps pace with green IT (environmentally friendly computing) and efficiently minimizes power consumption of the system as the core of power management and provides CPUfreq Governor for this.

The default setting of OnDemand Governor in RHEL 6 has a case where the Altibase server performance cannot guarantee consistency due to the delay due to frequency change. Therefore, it is recommended to set it to 'performance' or disable this function itself.

| Kernel Parameter                              | Description                                                  | Recommended Value |
| --------------------------------------------- | ------------------------------------------------------------ | ----------------- |
| CPU frequency Governor<br/>(CPUfreq Governor) | This is a performance adjuster that adjusts CPU frequency change rules, etc. for power management in Linux.<br />The default value of RHEL 6 is OnDemand, the CPU operates at the highest clock frequency when the system load is high, and operates at the lowest frequency when the system is idle. | performance       |

#### Linux Kernel Version

* CPUfreq Governor has beens supported starting from Red Enterprise Linux 6.
* The kernel version of RHEL 6 is 2.6.32-71.
* Red Hat Enterprise Linux Release Dates

### RemoveIPC

RemoveIPC is an option added in RHEL 7.2. It is a Linux property that removes the System V IPC and POSIX IPC objects when the OS user terminates the session.

In the case of the default setting 'yes', cases of abnormal termination of the Altibase server and applications due to forced semaphore allocation and return in the Altibase environment using IP have been reported. Even in an environment that does not use IPC, 'no' is recommended because no case has been reported that affects system performance due to RemoveIPC-related actions and system calls occurring in the kernel.

| Kernel Parameter | Description                                                  | Recommended Value |
| ---------------- | ------------------------------------------------------------ | ----------------- |
| RemoveIPC        | Removes all IPC resources when the OS user logs out.<br />The root user and system user are not affected by this setting. The default value is 'yes'. | no                |

#### Linux Kernel Version

* RemoveIPC is an option added in Red Hat Enterprise Linux 7.2.
* The kernel version of RHEL 7.2 is 3.10.0-327.
* Red Hat Enterprise Linux Release Dates

### Swappiness

This is a recommended kernel parameter to minimize the effect of disk I/O on the performance of Altibase server when swapping occurs.

Swapping refers to the operation (swap out) of lowering the physical memory area, which is less frequently used, into the swap area in a situation where the physical memory is insufficient. The swap is to use the disk as a memory and when the swap out occurs, the system performance decreases due to DISK I/O.

Therefore, it is important to property set the swappiness to maintain stable and consistent performance of the Altibase server.

| Kernel Parameter | Description                                                  | Recommended Value |
| ---------------- | ------------------------------------------------------------ | ----------------- |
| swappiness       | This can be set between 0 to 100.<br />A low value makes the kernel use pages from page cache as much as possible, and a high value prefers to swap out cold pages in physical memory. | 1                 |

* Disabling swappiness completely increases the likelihood that the Altibase server process will be killed abnormally by the OOM Killer in low memory situations.
* Recommendation '1' is a setting to minimize swapping without disabling swappiness.
* The page cache is a memory area managed by Linux to improve file I/O performance.

#### Linux Kernel Version

* Swappiness applies to all kernel versions



### THP(Transparent Huge Pages)

THP is a setting adopted by Linux for managing a car amount of memory. It is a setting to automate the function of expanding a memory page fo 4096 bytes in units of 2MB or 1GB.

However, in the Altibase operating environment, cases of performance issues due to memory allocation delays and fragmentation have been reported, so deactivation is recommended.

| Kernel Parameter          | Description                                                  | Recommended Value |
| ------------------------- | ------------------------------------------------------------ | ----------------- |
| THP(transparent_hugepage) | This automates the function to expand the memory page unit managed by the kernel from the existing 4K to 2M or 1G.<br />The default value is 'always' | Never             |

#### Linux Kernel Version

* THP (Transparent Huge Pages) has been supported starting with Red Hat Enterprise Linux 6.
* The kernel version of RHEL 6 is 2.6.32-71.
* Red Hat Enterprise Linux Release Dates

### max_map_count

When operating a terabyte unit memory table, memory allocation may fail due to the max_map_count parameter limitation. It is recommended to set it to a sufficiently far value because it can seriously affect the operation of Altibase such as transaction failure.

| Kernel Parameter | Description                                                  | Recommended Value |
| ---------------- | ------------------------------------------------------------ | ----------------- |
| max_map_count    | This is the maximum number of memory map areas that a process can use.<br />In most cases, the default is 65530, but if the user needs to map more than this file to the application, the user should increase this value. | 2147483647        |

* If memory allocation fails due to this parameter limitation,
  * The following message may be left in the Altibase trace log altibase_boot.log.
    * Failed to mmmap log file ( errno=ENOMEM(12), Not enough memory 
  * In the application, an error such as Memory [iduMemMgr :: malloc] failed. may occur.

### Shared Memory

This is a  kernel parameter required when multiple applications need to exchange information with each other on one server.

* When the communication method between Altibase server and client is IPC or IPCDA type
* Two or more Altibase applications communicate over IPC

The OS provides a resource called IPC (Inter Process Communication). A memory area for exchanging information between processes among various IPC resources is called shared memory. The shared memory can be set by the user by dividing it into one or more areas by specifying a unit, and this is called a segment.

For example, the user may set a shared memory having one segment at 10 MB, or configure a 10 segment shared memory at 10MB, Therefore, it is necessary to set the segment-related kernel parameters such as the maximum size or number of segments.

Shared memory related parameters provided by Linux and recommended values from Altibase are as follows.

| Kernel Parameter | Description                                                  | Recommended Value |
| ---------------- | ------------------------------------------------------------ | ----------------- |
| shmmni           | The maximum number of shared memory segments that can be created. The default value is 4096. | 4096              |
| shmmax           | The maximum size of one shared memory segment, in bytes.<br />For x86 systems, the minimum setting is 268435456 bytes (256MB) and for 64-bit systems it is 2147483648 bytes (2GB). | 2147483648        |

### Semaphore

This is a kernel parameter required to implement synchronization between processes when the communication method between the Altibase server and the client is IPC or IPCDA type.

Semaphore is a resource provided by the OS to restrict access to shared resources in IPC. Since the shared memory is used as a communication buffer in the IPC or IPCDA communication method, semaphore operation is used to control read/write concurrency for this resource. Depending on the semaphore operation, the process can be in a waiting or in progress state. Since semaphore operations occur simultaneously, it is necessary to set the number of semaphores and the appropriate kernel parameters for the operations.

Semaphore-related parameters provided by Linux and recommended values from Altibase are as follows.

| Kernel Parameter | Description                                                  | Recommended Value |
| ---------------- | ------------------------------------------------------------ | ----------------- |
| semmsl           | The maximum number of semaphores in a set of semaphores and must be logically equal to or less than semmns.<br />If set too large, several semaphore IDs can monopolize the entire system semaphore | 2000              |
| semmns           | The maximum number of semaphores in the operating system, and 16 bytes of kernel memory are allocated to one. | 32000             |
| semopm           | The maximum number of operations handled by the semop system call. | 512               |
| semmni           | The maximum number of semaphore sets can be set within 65535 and 85 bytes of kernel memory are allocated per set. | 5029              |



## How to Change Kernel Parameters

Let's learn how to check and change the settings of each kernel parameter.

### CPU frequency Governor

It is recommended that the CPU frequency governor is set as performance.

#### How to Check Set Value

This is a verification method commonly used in RHEL 6 and 7. Normally, it is checked with the cat command. If the cpupowerutils package is installed, it can also be checked with the cpupower command.

##### cat command

This is verification method commonly user in RHEL 6 and 7.

###### CPU frequency governor setting confirmation method and output example-cat

```
$ cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor | sort -u
performance
 
   # If CPUfreq driver is not installed, the following output may be displayed.
   # In this case, it is not necessary to consider the CPU frequency governor setting.
$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
cat: /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor: There is no such file or directory
```

##### **How to check whether the CPUfreq governor driver is installed**

###### Red Hat Enterprise Linux 6

```
$ lsmod | grep cpufreq
acpi_cpufreq            7699  0
freq_table              4936  1 acpi_cpufreq
mperf                   1557  1 acpi_cpufreq
 
# Or
 
$ cpupower frequency-info | grep driver
 driver: acpi-cpufreq
 
   # If CPUfreq driver is not installed, the output result is as follows.
   # lsmod output does not appear.
$ lsmod | grep cpufreq                                    
$ cpupower frequency-info | grep driver
 no or unknown cpufreq driver is active on this CPU
```

###### Red Hat Enterprise Linux 7

```
$ cpupower frequency-info | grep driver
  driver: intel_pstate
```

##### cpupower command

How to check CPU frequency governor settings-cpupower

```
  # Statements and output examples
   # The output may differ depending on the cpupower command version
$ cpupower frequency-info --policy
analyzing CPU 0:
  current policy: frequency should be within 1.20 GHz and 3.60 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
 
   # Output result when CPUfreq driver is not installed
$ cpupower frequency-info --policy
analyzing CPU 0:
  Unable to determine current policy
```

##### How to check clock speed per CPU core

Check if the clock speed of all CPU cores is set with the following command.

```
$ grep MHz /proc/cpuinfo | sort -u
```

#### How to Change the Settings

**<u>Red Hat Enterprise Linux 6</u>**

This is how to change the CPU frequency governor in Red Hat Enterprise Linux 6.

##### 1. Change Immediately

Settings using the governor directive and the cpupower command can be changed while online, but initialized when the OS is restarted.

###### Governor directives using the cat command

CPUfreq Governor immediate change in RHEL 6 1-cat command

```
# The following instructions are repeated as many as the the number of CPU cores.
$ echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
$ echo performance > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
...
```

###### cpupower

CPUfreq Governor immediate change in RHEL 6 2-cpupower command

```
$ cpupower frequency-set -g performance
```

###### tuned

For systems with tuned system tools enabled, refer to [RHEL 7 CPUfreq Governor Permanently Applied-tuned].

##### Permanent Application

This is a way to keep the settings even after restarting the OS.

###### Tuned

Refer to [RHEL 7 CPUfreq Governor permanently applied-tuned].

###### rc.local

Used when the tuned service is disabled.

How to apply RHEL 6 CPUfreq Governor permanently 2-rc.local

```
# Add the following command to the number of CPU cores in the /etc/rc.d/rc.local file.
echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo performance > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
...
```



**<u>Red Hat Enterprise Linux 7</u>**

This is how to change the CPU frequency governor in Red Hat Enterprise Linux 7.

##### Change immediately 

###### Cpupower

Configuration changes using the cpupower command are initialized when the OS is restarted.

Apply RHEL 7 CPUfreq Governor settings immediately-cpupower.

```
$ cpupower frequency-set -g performance
```

##### Permanent application

###### tuned

Use the throughput-performance or latency-performance profiles provided by Linux. Using these two profiles, it can see the following effects:

* CPUfreq governor is set to performance
* CPU clock speed is fixed as maximum

For reference, the default profile of Red Hat Enterprise Linux 7 is throughput-performance.

There are two ways to set the throughput-performance or latency-performance profile.

###### First method: Include the throughput-performance profile in the active profile.

Permanent application of RHEL 7 CPUfreq Governor-How to include throughput-performance profile in active tuned profile

```
# 1. Check the activated tuned profile
      # The following is an example when the tuned active profile is not throughput-performance or latency-performance.
      # An example of the execution of the commander, and in the result below, the active profile is virtual-guest.
$ tuned-adm active
Current active profile: virtual-guest
 
   # 2. Go to the profile path.
      # The default path of tuned profile is /usr/lib/tuned/profile_name. 
      # [main] Add include to the [main] type as shown below.
      # Delete the [cpu] type, if any.
$ cd /usr/lib/tuned/virtual-guest
$ vi tuned.conf
 
[main]
include=throughput-performance
 
   # 3. Apply the changed profile.
$ tuned-adm profile virtual-guest
```

###### Second method: Change the active profile to throughput-performance.

Permanent application of RHEL 7 CPUfreq Governor-Example of changing active profile to throughput-performance

```
$ tuned-adm profile throughput-performance
```



### RemoveIPC

RemoveIPC applies to Red Hat Enterprise Linux 7.2 and later, and the recommended value is 'no'.

#### How to Check Set Value

Make sure RemoveIPC = no is set in the logind.conf file.

Check RemoveIPC settings

```

$ grep RemoveIPC /etc/systemd/logind.conf
RemoveIPC=no
```

#### How to Change the Settings

**<u>Red Hat Enterprise Linux 7</u>**

###### Change Immediate

RemoveIPC does not provide a way to change immediately on Linux

###### Permanent Application

Open the /etc/systemd/logind.conf file with an editor and change RemoveIPC = no.

How to change RemoveIPC

```
$ vi /etc/systemd/logind.conf
 
#  This file is part of systemd.
...
[Login]
...
RemoveIPC=no
```

Restart the OS or execute the following command to apply the changes.

Apply after changing RemoveIPC

```
$ systemctl restart systemd-logind.service
```



### swappiness

Check the current setting value, and if the setting is not recommended, change it by referring to the guide below.

#### How to Check Set Value

Checking the settings is the same regardless of the Linux version. There are two ways to do this.

###### Use cat

How to check swappiness setting 1-cat

```
$ cat /proc/sys/vm/swappiness         # Altibase's recommended setting is 1.
```

###### Use sysctl

How to check swappiness setting 2-sysctl

```
$ sysctl -a | grep swappiness         # Altibase's recommended setting is 1.
```

#### How to Change the Settings

**<u>Red Hat Enterprise Linux 6</u>**

This is how to change swappiness in Red Hat Enterprise Linux 6.

##### Change Immediately

Use the echo or sysctl command.

How to change RHEL 6 swappiness immediately 1-echo

```
$ echo 1 > /proc/sys/vm/swappiness
```

How to change RHEL 6 swappiness immediately 2-sysctl

```
$ sysctl -w vm.swappiness=1
```

##### Permanent Application

It can be configured in two ways, sysctl.conf and rc.local, so they all apply the same way.

###### sysct.conf

How to permanently apply RHEL 6 swappiness 1-sysctl

```
$ vi /etc/sysctl.conf
vm.swappiness = 1                   # Add vm.swappiness = 1 to the sysctl.conf file or change the value.
```

###### rc.local

How to permanently apply RHEL 6 swappiness 2-rc.local

```
$ vi /etc/rc.d/rc.local
echo 1 > /proc/sys/vm/swappiness    # Add this command to the rc.local file.
```

**<u>Red Hat Enterprise 7</u>**

This is how to change swappiness in Red Hat Enterprise Linux 7.

##### Change Immediately

Use the echo or sysctl command.

How to change RHEL 7 swappiness immediately 1-echo

```
$ echo 1 > /proc/sys/vm/swappiness
```

How to change RHEL 7 swappiness immediately 2-sysctl

```
$ sysctl -w vm.swappiness=1
```

##### Permanent Application

It can be set in two ways, tuned profile and sysctl.conf, so they are all applied identically.

###### tuned

How to permanently apply RHEL 7 swappiness-tuned

```
# Check the activated Tuned profile.
$ tuned-adm active
 
   # Example
   # In the results below, the active profile is throughput-performance.
$ tuned-adm active
Current active profile: throughput-performance
 
 
   # Go to the profile path.
   # The default path for tuned profiles is / usr / lib / tuned / profile_name.
   # Example when the active profile is throughput-performance.
$ cd /usr/lib/tuned/throughput-performance
 
   # Open the tuned.conf file.
   # Add or change swappiness setting in [sysctl] type. If there is no [sysctl] type, add it.
$ vi tuned.conf
[sysctl]
vm.swappiness=1
 
   # Apply the changed profile.
$ tuned-adm profile 'profile_name'
```

###### **/etc/sysctl.conf**

How to permanently apply RHEL 7 swappiness-sysctl.conf

```
$ vi /etc/sysctl.conf
vm.swappiness = 1
```

Restart the OS to see the changes. Restarting the OS may be performed at once after all kernel parameters are changed.

### max_map_count

Check the current setting value, and if the setting is not recommended, change it by referring to the guide below.

#### How to Check Set Value

Checking the settings is the same regardless of the Linux version. There are two ways to do this.

###### Use cat

How to check max_map_count setting 1-cat

```
$ cat /proc/sys/vm/max_map_count        # The recommended setting value for Altibase is 2147483647.
```

###### Use sysctl

How to check max_map_count setting 2-sysctl

```
$ sysctl -a | grep max_map_count        # The recommended setting value for Altibase is 2147483647.
```

#### How to Change the Setting

**<u>Red Hat Enterprise Linux 6</u>**

This is how to change the max_map_count parameter setting in Red Hat Enterprise Linux 6.

##### Change Immediately

Use the sysctl command.

How to change RHEL 6 max_map_count immediately-sysctl

```
$ sysctl -w vm.max_map_count=2147483647
```

##### Permanent Application

It can be configured in two ways, sysctl.conf and rc.local, so they all apply the same way.

###### sysct.conf

RHEL 6 max_map_count Permanent application method 1-sysctl

```
$ vi /etc/sysctl.conf
vm.max_map_count = 2147483647                   # Add vm.max_map_count = 2147483647 to the sysctl.conf file or change the value.
```

##### rc.local

How to permanently apply RHEL 6 max_map_count 2-rc.local

```
$ vi /etc/rc.d/rc.local
echo 2147483647 > /proc/sys/vm/max_map_count    # Add this command to the rc.local file.
```

**<u>Red Hat Enterprise Linux 7</u>**

This is how to change max_map_count in Red Hat Enterprise Linux 7.

##### Change Immediately

Use the sysctl command.

How to change RHEL 7 max_map_count immediately-sysctl

```
$ sysctl -w vm.max_map_count=2147483647
```

##### Permanent Application

It can be set in two ways, tuned profile and sysctl.conf, so they are all applied identically.

###### tuned

How to permanently apply RHEL 7 max_map_count-tuned

```
 # Check the activated Tuned profile.
$ tuned-adm active
 
   # Example.
   # In the results below, the active profile is throughput-performance.
$ tuned-adm active
Current active profile: throughput-performance
 
 
   # 
Go to the profile path.
   # The default path of tuned profile is /usr/lib/tuned/profile_name.
   # Example when the active profile is throughput-performance.
$ cd /usr/lib/tuned/throughput-performance
 
   # Open the tuned.conf file.
   # [sysctl] Add or change the swappiness setting for the type. If there is no [sysctl] type, add it.
$ vi tuned.conf
[sysctl]
vm.max_map_count=2147483647
 
   # Apply the changed profile.
$ tuned-adm profile 'profile_name'
```

###### /etc/sysctl.conf

How to permanently apply RHEL 7 max_map_count-sysctl.conf

```
$ vi /etc/sysctl.conf
vm.max_map_count=2147483647
```

Restart the OS to see the changes. Restarting the OS may be performed at once after all kernel parameters are changed.

### Shared Memory and Semaphore

#### How to Check Set Value

###### lpcs command

How to check shared memory and semaphore 1-Using ipcs command

```
   # Check shared memory kernel parameter settings
$ ipcs -m -l
------ Shared Memory Limits --------
max number of segments = 4096                         # shmmni (Recommended: 4096)
max seg size (kbytes) = 2097152                       # shmmax (Recommended: 2097152)
max total shared memory (kbytes) = 137438953472      
min seg size (bytes) = 1
 
 
   # Check the semaphore kernel parameter settings
$ ipcs -s -l
------ Semaphore Limits --------
max number of arrays = 5029                           # semmni (Recommended: 5029)
max semaphores per array = 2000                       # semmsl (Recommended: 2000)
max semaphores system wide = 32000                    # semmns (Recommended: 32000)
max ops per semop call = 512                          # semopm (Recommended: 512)
semaphore max value = 32767
```

###### sysctl command

How to check shared memory and semaphore 2-Using sysctl command

```
   # Examples of statements and results
$ sysctl -a | grep -e kernel.shmmax -e kernel.shmmni -e kernel.sem
kernel.shmmax = 2147483648
kernel.shmmni = 4096
kernel.sem = 20000        32000   512     5029
```

#### How to Change the Settings

##### Change Immediately

Use the echo command.

Immediate change shared memory and semaphores

```
   # Shared Memory Settings
echo 4096 > /proc/sys/kernel/shmmni
echo 2147483648 > /proc/sys/kernel/shmmax
 
   # Semaphore settings
echo 2000 32000 512 5029 > /proc/sys/kernel/sem
```

##### Permanent Application

Add to /etc/sysctl.conf file.

Shared memory and semaphore permanent application-/etc/sysctl.conf

```
$ vi /etc/sysctl.conf
kernel.shmmni = 4096
kernel.shmmax = 2147483648
kernel.sem = 20000        32000   512     5029
```

Restart the OS to see the changes. Restarting the OS may be performed at once after all kernel parameters are changed.

## User Setting

This section describes the user settings required to install and operate the Altibase server on Linux. A user is an OS user, and is a user who installs the Altibase server and runs the Altibase server process.

The user login configuration file in the bash shell is .bash_profile. The user configuration file differs depending on the shell, but it is described based on the Linux default shell because it is a bash shell.

The user setting is divided into the following two categories:

* Resource limitation
* Setting variable

### Resource Limitation

Linux provides settings to limit system resources such as CPU, memory, and files. Proper configuration is necessary because the purpose of preventing a specific user from monopolizing system resources, or the limitation of file creation or memory allocation, has a fatal effect on the operation of the Altibase server.

The resource items and recommended values in the Altibase server operating environment are as follows.

| ulimit command                    | Items in limits.conf | Description                                                  | Recommended Value |
| --------------------------------- | -------------------- | ------------------------------------------------------------ | ----------------- |
| data set size (kbytes, -d)        | data                 | The maximum memory size of the process data area             | unlimited         |
| file size (blocks, -f)            | fsize                | The maximum size of files that can be created                | unlimited         |
| open files (-n)                   | nofile               | The maximum number of open file descriptors a process can open | 1048576           |
| max memory size (kbytes, -m)      | rss                  | The maximum amount of available memory                       | unlimited         |
| virtual memory       (kbytes, -v) | as                   | The maximum amount of virtual memory available               | unlimited         |
| max user processes         (-u)   | nproc                | The maximum number of processes (including threads) that the user can run | unlimited         |

### Related Error Message

This is an error message cause by resource limitation. If the following message is checked while operating the Altibase server, it is necessary to check the resource limit settings.

* Insufficient max user processes
  * Failed to create a thread object.
  * resource temporarily unavailable
* Insufficient open files
  * Too many open files

### View and Change Resource Settings

Resource limits are set for each user, but apply individually to user processes.

To reflect the changed resource limit settings to the Altibase server, the Altibase server must be restarted.

#### How to Check Set Value

This command checks the resource limit setting value.

```
$ ulimit -a        # If -S or -H option is not specified, -S (Soft-Limit) is output.
 
$ ulimit -Ha       # Output the Hard-Limit setting value.
```

Check the resource limit set in the Altibase server process with the following command.

```
$ cat /proc/`ps -ef | grep 'altibase -p' | grep -v grep | awk '{print $2}'`/limits
```

If the desired settings are not applied to the Altibase server process, the Altibase server must be restarted.

### How to Change the Settings

##### Execute ulimit command

ulimit is a command to set resource limits. The ulimit configuration command is added to the .bash_profile of the configuration file of the OS user who installs and runs the Altibase server.

User resource limit setting example-added to .bash_profile

```

#For Resource Limitation
ulimit -d  unlimited  # data segment size
ulimit -f  unlimited  # file size
ulimit -n  1048576    # file descriptor(open files)
ulimit -m  unlimited  # max memory size(rss)
ulimit -v  unlimited  # virtual memory
ulimit -u  unlimited  # user process
```

##### Apply the configuration file (.bash_profile)

Apply ulimit setting with the following command.

```
. ~/.bash_profile
```

When applying the configuration file, the following error may occur.

```
bash: ulimit: open files: cannot modify limit: Command not accepted
-bash: ulimit: max user processes: cannot modify limit: Command not accepted
```

This is an error caused by Hard-Limit.

###### **Hard-Limit & Soft-Limit**

System resource limits include Hard-Limit and Soft-Limit. Hard-Limit means the maximum resource limit setting value that can be set by the OS general user, and Soft-Limit means the resource limit value set by the user.

If Hard-Limit is smaller than the value that user wants to set as ulimit, 'cannot modify limit' error occurs.

How to check Hard-Limit

```
$ ulimit -H -u -n    # The -H option means Hard-Limit.
max user processes              (-u) 1024
open files                      (-n) 4096
```

##### Change /etc/security/limits.conf

Hard-Limit changes require root privileges. Add the following setting to the limits.conf file and save it.

Hard-Limit configuration example-OS user name is altibase

```
#<domain>      <type>  <item>         <value>
altibase         -     nofile          1048576
altibase         -     nproc           unlimited
```

Log in as the OS user and perform step 2 again.

### Environment Variables

This is an environment variable to be set after installing the Altibase server.

| Classification            | Environment Variable | Description                                                  | Setting Value                                        |
| ------------------------- | -------------------- | ------------------------------------------------------------ | ---------------------------------------------------- |
| Required (Auto Setting)   | ALTIBASE_HOME        | Specifies the path where Altibase is installed               | Depends on the environment                           |
| Required (Auto Setting)   | PATH                 | Finds the location Altibase's utilities and shell scripts    | $ALTIBASE_HOME/bin                                   |
| Required (Auto Setting)   | LD_LIBRARY_PATH      | Finds the location of the Altibase dynamic library           | $ALTIBASE_HOME/lib                                   |
| Required (Auto Setting)   | CLASSPATH            | Finds the location of the Java Class file                    | $ALTIBASE_HOME/lib                                   |
| Required (Manual Setting) | ALTIBASE_NLS_USE     | Sets the Altibase character set.<br />Set the same as the Altibase server character set. | Same as Altibase server character set                |
| Required (Manual Setting) | LANG                 | Defines the user's system locale                             | It is affected by the Altibase server character set. |
| Select (Manual Setting)   | MALLOC_ARENA_MAX     | A feature added in Red Hat Enterprise Linux 6 to improve performance issues due to memory contention between threads in a multithreaded application environment.<br />The default is the number of CPU cores * MALLOC_ARENA_TEST.<br />The default value of MALLOC_ARENA_TEST environment: 2 for 32-bit, 8 for 64-bit.<br />The MALLOC_ARENA_MAX environment variable works properly in glibc2.10 or later. | -                                                    |

* Environment variable MALLOC_ARENA_MAX
  * This environment variable is optional.
  * In general, consider keeping the default value and setting it smaller than the default value if a memory issue is found.
  * Since this environment variable affects the performance and memory usage of the Altibase server process according to the set value, it is difficult to recommend the same value collectively.
  * The default value of this environment variable is influenced by the number of CPU cores. As the number of CPU cores increases, the VSZ of the Altibase server process may increase excessively.

#### How to Set Environment Variables

##### How to Check the Set Value

Check if the required environment variables are set correctly.

###### env command

The env result prints all environment variables set for the session.

```
$ env
```

###### echo command

The specified environment variable settings are output. If the value is not output, it means that the environment variable is not set.

```
   # This is an example of checking the ALTIBASE_HOME environment variable setting value using the echo command.
$ echo $ALTIBASE_HOME
```

##### How to Change the Settings

This is a method of setting the ALTIBASE_NLS_USE and LANG environment variables that must be manually set among the required environment variables.

###### Check the Altibase server character set

```
iSQL> SELECT NLS_CHARACTERSET FROM V$NLS_PARAMETERS;
```

###### Set environment variables in .bash_profile file

Environment variables are set in units of OS user sessions. Therefore, it must be added to the user configuration file .bash_profile to be applied every time an OS user connects.

The table below shows the ALTIBASE_NLS_USE and LANG environment variable settings according to the Altibase server character set.

| Altibase Server Character Set | ALTIBASE_NLS_USE | LANG        |
| ----------------------------- | ---------------- | ----------- |
| MS949                         | MS949            | ko_KR.euckr |
| KOS16KSC5601                  | KOS16KSC5601     | ko_KR.euckr |
| UTF88                         | UTF8             | Ko_KR.utf8  |

Refer to the table above and add environment variables to the user configuration file .bash_profile.

Environment variable setting example-added to .bash_profile

```
   # This is an example when the Altibase server character set is UTF8.
   # Add the following contents to .bash_profile and save.
export ALTIBASE_NLS_USE=UTF8
export LANG=ko_KR.utf8
```

###### Apply to the configuration file .bash_profile

Apply the environment variable added with the following command.

```
. ~/.bash_profile
```



## Others

### Red Hat Enterprise Linux Recommended Swap Size

Red Hat Linux recommends the following for Swap sizing.

* In the past, twice as much swap space as physical memory was recommended, but today with terabytes of memory, the past recommendation is not practical.
* For systems with more than 140 logical processors or systems with more than 3 TB of RAM, a minimum swap space of 100 GB is recommended.

For details, refer to the Red Hat CUSTOMER PORTAL page.

[What is the recommended swap size for Red Hat platforms?](https://access.redhat.com/solutions/15244)
