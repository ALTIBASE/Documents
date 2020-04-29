- [Error Message Reference](#error-message-reference)
  - [Preface](#preface)
    - [About This Manual](#about-this-manual)
    - [Audience](#audience)
    - [Software Environment](#software-environment)
    - [Organization](#organization)
    - [Altibase Welcomes Your Opinions](#altibase-welcomes-your-opinions)
  - [1.ID Error Code](#1id-error-code)
    - [FATAL](#fatal)
    - [ABORT](#abort)
    - [IGNORE](#ignore)
  - [2.SM Error Code](#2sm-error-code)
    - [FATAL](#fatal-1)
    - [ABORT](#abort-1)
    - [IGNORE](#ignore-1)
    - [RETRY](#retry)
  - [3.MT Error Code](#3mt-error-code)
    - [FATAL](#fatal-2)
    - [ABORT](#abort-2)
    - [IGNORE](#ignore-2)
  - [4.RP Error Code](#4rp-error-code)
    - [FATAL](#fatal-3)
    - [ABORT](#abort-3)
    - [IGNORE](#ignore-3)
  - [5.QP Error Code](#5qp-error-code)
    - [FATAL](#fatal-4)
    - [ABORT](#abort-4)
    - [RETRY](#retry-1)
  - [6.SD Error Code](#6sd-error-code)
    - [ABORT](#abort-5)
  - [7.ST Error Code](#7st-error-code)
    - [FATAL](#fatal-5)
    - [ABORT](#abort-6)
    - [IGNORE](#ignore-4)
  - [8.MM Error Code](#8mm-error-code)
    - [FATAL](#fatal-6)
    - [ABORT](#abort-7)
    - [IGNORE](#ignore-5)
  - [9.ODBC Error Code](#9odbc-error-code)
    - [FATAL](#fatal-7)
    - [ABORT](#abort-8)
    - [IGNORE](#ignore-6)
  - [10.APRE Error Code](#10apre-error-code)
    - [ABORT](#abort-9)
  - [11.Utilities Error Code](#11utilities-error-code)
    - [FATAL](#fatal-8)
    - [ABORT](#abort-10)
    - [IGNORE](#ignore-7)
  - [12.CM Error Code](#12cm-error-code)
    - [FATAL](#fatal-9)
    - [ABORT](#abort-11)
    - [IGNORE](#ignore-8)
    - [RETRY](#retry-2)
  - [13.Database Link Error Code](#13database-link-error-code)
    - [FATAL](#fatal-10)
    - [ABORT](#abort-12)
    - [**RETRY**](#retry)
  - [14.Log Analyzer Error Code](#14log-analyzer-error-code)
    - [**FATAL**](#fatal)
    - [**ABORT**](#abort)
    - [IGNORE](#ignore-9)



Altibase® Message

Error Message Reference
=======================

![](media/errorMessage/e5cfb3761673686d093a3b00c062fe7a.png)

Altibase Message Error Message Reference

Release 7.1

Copyright ⓒ 2001\~ 2018 Altibase Corp. All Rights Reserved.

This manual contains proprietary information of Altibase Corporation; it is
provided under a license agreement containing restrictions on use and disclosure
and is also protected by copyright patent and other intellectual property law.
Reverse engineering of the software is prohibited.

All trademarks, registered or otherwise, are the property of their respective
owners

**Altibase Corp.**

10F, Daerung PostTower II,

306, Digital-ro, Guro-gu, Seoul 08378, Korea

Telephone: +82-2-2082-1000 Fax: 82-2-2082-1099

homepage: [http://www.altibase.com](http://www.altibase.com/)

Preface
-------

### About This Manual

This manual describes error codes and messages that are displayed when Altibase
or the operating program is performed.

Error messages may be changed without notice.

### Audience

This manual has been prepared for the following Altibase users:

-   Database administrators
-   Performance administrators
-   Database users
-   Application developers
-   Technical Supporters

It is recommended for those reading this manual possess the following background knowledge:

-   Basic knowledge in the use of computers, operating systems, and operating system utilities
-   Experience in using relational database and an understanding of database concepts
-   Computer programming experience
-   Experience in database server management, operating system management, or network administration

### Organization

This manual is organized as follows:

-   Chapter 1: ID Error Code

-   Chapter 2: SM Error Code

-   Chapter 3: MT Error Code

-   Chapter 4: RP Error Code

-   Chapter 5: DR Error Code

-   Chapter 6: QP Error Code

-   Chapter 7: ST Error Code

-   Chapter 8: MM Error Code

-   Chapter 9: ODBC Error Code

-   Chapter 10: APRE Error Code

-   Chapter 11: Uilities Error Code

-   Chapter 12: CM Error Code

-   Chapter 13: Database Link Error Code

-   Chapter 14: Log Analyzer Error Code

#### Altibase Welcomes Your Comments and Feedbacks

Please let us know what you like or dislike about our manuals. To help us with better future versions of our manuals, please tell us if there is any corrections or classifications that you would find useful.

Include the following information:

- The name and version of the manual that you are using
- Any comments about the manual
- Your name, address, and phone number

If you need immediate assistance regarding any errors, omissions, and other technical issues, please contact Altibase's Support Portal (http://altibase.com/support-center/en/).

Thank you. We always welcome your feedbacks and suggestions.

1.ID Error Code
---------------

### FATAL

**0x00012 ( 18) idERR_FATAL_idc_SHM_ATTACH Unable to attach shared memory**

**Cause:** Failed to invoke the shmat() function.

**Action:** Verify that you have permission to access shared memory. Check the
error number from the trace log and contact Altibase’s Support Center
(http://support.altibase.com/en/).

**0x00013 ( 19) idERR_FATAL_idc_SHM_CTL Unable to delete shared memory**

**Cause:** Failed to invoke the shmctl() function.

**Action:** Verify that you have permission to access shared memory. Check the
error number from the trace log and contact Altibase’s Support Center
(http://support.altibase.com/en/).

**0x00014 ( 20) idERR_FATAL_idc_SEM_CTL Unable to delete a semaphore**

**Cause:** Failed to invoke the semctl() function.

**Action:** Verify that you have permission to access the semaphore. Check the
error number from the trace log and contact Altibase’s Support Center
(http://support.altibase.com/en/).

**0x00015 ( 21) idERR_FATAL_idc_SEM_OP Unable to execute operations on a
semaphore**

**Cause:** Failed to invoke the semop() function.

**Action:** Check the error number from altibase_boot.log and verify that the
semaphore group exists.

**0x0001F ( 31) idERR_FATAL_idc_SVC_INET_BIND_ERROR Unable to bind the INET
socket.(\<0%d\>)**

**Cause:** Failed to invoke the bind() function on the INET socket because the
port was already in use by another process.

**Action:** Verify that the port is not being used by another process. If it is,
close that process or select a different port.

**0x00020 ( 32) idERR_FATAL_idc_SVC_UNIX_BIND_ERROR Unable to bind the UNIX
domain socket**

**Cause:** Failed to invoke the bind() function on a UNIX domain socket. The
port was in use by another process.

**Action:** Verify that the port is not being used by another process. If it is,
close that process or select a different port.

**0x0002C ( 44) idERR_FATAL_FILE_OPEN Unable to open a file [\<0%s\>]**

**Cause:** The path of the file is invalid or the storage manager does not have
permission to open the file.

**Action:** Verify that the path and file name are correct and that you have
read/write permission for the file.

**0x00032 ( 50) idERR_FATAL_IDU_MEMORY_ALLOCATION Memory allocation failed**

**Cause:** Insufficient memory.

**Action:** Verify that the system has enough available memory.

**0x00035 ( 53) idERR_FATAL_ThrMutexLock Failed to invoke the mutex_lock()
system function**

**Cause:** The system failed to lock a mutex.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x00036 ( 54) idERR_FATAL_ThrMutexUnlock Failed to invoke the mutex_unlock()
system function**

**Cause:** The system failed to unlock a mutex.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x0003B ( 59) idERR_FATAL_LongFileName Filename too long**

**Cause:** The file name is too long.

**Action:** Shorten the file name.

**0x0003D ( 61) idERR_FATAL_SysOpen Unable to invoke the open() function on
[\<0%s\>]**

**Cause:** The system failed to open the file.

**Action:** Verify that the file exists and that the operating system has not
already opened the maximum possible number of files.

**0x0003F ( 63) idERR_FATAL_SysRead Unable to invoke the read() function on
[\<0%s\>]**

**Cause:** The system failed to read the file because the disk is physically
damaged or a bad sector has occurred.

**Action:** Execute the fsck command to troubleshoot and fix any filesystem
errors.

**0x00041 ( 65) idERR_FATAL_Sysfstat Unable to invoke the fstat() function on
[\<0%s\>]**

**Cause:** The system failed to call the fstat() function.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x00065 ( 101) idERR_FATAL_idc_UNIX_PATH_TRUNCATED Unix domain socket path
truncated.**

**Cause:** A Unix domain socket path has been truncated.

**Action:** The Altibase socket path is too long. Shorten it.

**0x00070 ( 112) idERR_FATAL_DirectIO_Invalid_Argument Invalid argument for
direct I/O write or read operation on file \<0%s\> (arguments: offset:\<1%lu\>
buffer:\<2%lu\> size:\<3%lu\>)**

**Cause:** An argument for the direct I/O write or read operation was invalid.

**Action:** Verify that the arguments for the direct I/O read or write operation
are valid.

**0x00071 ( 113) idERR_FATAL_WrongDirectIOPageSize The page size for Direct I/O
should be exactly 512, 1024, 2048, 4096, or 8192.**

**Cause:** The DIRECT_IO_PAGE_SIZE property is not set to an acceptable value.

**Action:** Set the DIRECT_IO_PAGE_SIZE property to one of 512, 1024(1K),
2048(2K), 4096(4K), or 8192(8K).

**0x00072 ( 114) idERR_FATAL_SysSeek Unable to invoke the seek() function on
[\<0%s\>]**

**Cause:** The system failed to change the access position in the file because
the disk is physically damaged or a bad sector has occurred.

**Action:** Execute the fsck command to troubleshoot and fix any filesystem
errors.

**0x000AD ( 173) idERR_FATAL_THREAD_JOINERROR System error while joining**

**Cause:** The system failed to join a mutex.

**Action:** Check the error number from the altibase_boot.log file and take
appropriate action.

**0x000B1 ( 177) idERR_FATAL_Shm_No_Permission No permission for the shared
memory database**

**Cause:** A shared memory region has already been created with the same key but
a different UID.

**Action:** Please remove the shared memory region, or create a shared memory
region with another key.

**0x000B5 ( 181) idERR_FATAL_PROCESS_CHECK_ALIVE Unable to check if a process is
alive.**

**Cause:** Failed to invoke the semctl() function

**Action:** Please verify that you have permission to access the semaphore and
send a bug report to the vendor.

**0x000B6 ( 182) idERR_FATAL_SEM_DELETE Unable to delete the semaphore.**

**Cause:** Failed to invoke the semctl() function

**Action:** Please verify that you have permission to access the semaphore and
send a bug report to the vendor.

**0x000B7 ( 183) idERR_FATAL_SEM_GET Unable to create or get a semaphore.**

**Cause:** Failed to invoke the semop() function

**Action:** Please verify the error number and make sure that the semaphore
group exists.

**0x000B9 ( 185) idERR_FATAL_SYSTEM_PROCESS_ALREADY_STARTED [0%s] Process has
been already started.**

**Cause:** System process which is one of Deamon or WServer has been started
before this operation.

**Action:** Check the other system process is alive or started.

**0x000BC ( 188) idERR_FATAL_UNCOMPATIBLE_SHARED_MEMORY The version of the
shared memory is not compatible with the version of the shared memory manager.
Shared Memory Version =\> [ Version ID = \<0%s\> ] Shared Memory Manager=\>[
Version ID = \<1%s\> ]**

**Cause:** The shared memory created before is no compatitle with the current
shared memory manager.

**Action:** Please remove shared memory created by Altibase and restart
Altibase.

**0x000C2 ( 194) idERR_FATAL_INVALID_SHM_SEGCOUNT The max number of shared
memory segments is invalid.**

**Cause:** The maximum of the segment count is 0.

**Action:** Check SHM_MAX_SIZE and SHM_CHUNK_SIZE since the number of the max
shared memory segments is calculated by SHM_MAX_SIZE / SHM_CHUNK_SIZE.

**0x000C5 ( 197) idERR_FATAL_REGISTER_NEW_PROCESS_DISABLED A process can not
access a database in a shared memory.**

**Cause:** Database is a invalid state to be accessed by a process.

**Action:** Check the system process is shutting down or the state of a shared
memory area.

**0x000C7 ( 199) idERR_FATAL_REMOVE_SYSTEM_SHARED_MEMORY_SEGMENT The remove
operation of a system shared memory segment is failed.**

**Cause:** There is a process to attach a system shared memory segment.

**Action:** Check if there is a process to attach a system shared memory
segment.

**0x000C8 ( 200) idERR_FATAL_Invalid_SHM_DB_KEY When the SHM_DB_KEY value is 0,
a shared memory database cannot be used. Set the SHM_DB_KEY property.**

**Cause:** SHM_DB_KEY value is 0.

**Action:** Please set the SHM_DB_KEY property.

**0x000CB ( 203) idERR_FATAL_NOT_OWNER_OF_SHARED_MEMORY Try to access a shared
memory chunk which is not owned: SHMKEY is \<0%d\>.**

**Cause:** Try to access a shared memory chunk which is not owned.

**Action:** Please check if there is already created shared memory associated
with SHM_DB_KEY.

**0x000CC ( 204) idERR_FATAL_CREATE_SYSTEM_SEGMENT Cannot create the system
segment.**

**Cause:** Unavailable system resource.

**Action:** Please check your system.

**0x000D2 ( 210) idERR_FATAL_CHANGE_OWNER_OF_SHARED_MEMORY_SEGMENT Cannot change
the owner of the shared memory segment.**

**Cause:** Failed to invoke the shmctl() function.

**Action:** Verify that you have permission to access shared memory. Check the
error number from the trace log and contact Altibase's Support Center
(http://support.altibase.com/en/).

### ABORT

**0x01001 ( 4097) idERR_ABORT_idnCharacterSetNotFound No character set was
found.**

**Cause:** No character set was found.

**Action:** Specify a valid value for the NLS_USE property.

**0x01002 ( 4098) idERR_ABORT_idnInvalidCharacter Invalid character in use**

**Cause:** An invalid character is being used.

**Action:** Verify that every character in the input string is a valid
character.

**0x01003 ( 4099) idERR_ABORT_idnReachEnd Unexpected end of string**

**Cause:** Unexpected end of string.

**Action:** Verify that the form of the string is legal.

**0x01006 ( 4102) idERR_ABORT_idnLikeEscape Invalid use of escape characters in
LIKE predicate.**

**Cause:** The server has detected the invalid use of escape characters in a
LIKE predicate.

**Action:** Verify that the use of escape characters in the LIKE predicate is
syntactically correct.

**0x01007 ( 4103) idERR_ABORT_idaNullValue A NULL value is not allowed for this
data type.**

**Cause:** This data type cannot have a NULL value.

**Action:** Verify that there is no NULL value in the field.

**0x01008 ( 4104) idERR_ABORT_idaInvalidNumeric Unable to cast the string to the
INTEGER type.**

**Cause:** It is impossible to cast the string to the INTEGER type.

**Action:** Change the string appropriately.

**0x01009 ( 4105) idERR_ABORT_idaInvalidNibble Unable to cast the string to the
NIBBLE type.**

**Cause:** It is impossible to cast the string to the NIBBLE type.

**Action:** Change the string appropriately.

**0x0100A ( 4106) idERR_ABORT_idaInvalidBytes Unable to cast the string to the
BYTE type.**

**Cause:** It is impossible to cast the string to the BYTE type.

**Action:** Change the string appropriately.

**0x0100B ( 4107) idERR_ABORT_idaOverflow Value exceeds range supported by
type**

**Cause:** The value is out of the range supported by the type.

**Action:** Change the input value so that it falls within the range of values
supported by the given type.

**0x0100C ( 4108) idERR_ABORT_idaDivideByZero Division by zero**

**Cause:** An attempt is being made to divide a value by zero.

**Action:** Verify that the value is not being divided by zero.

**0x0100D ( 4109) idERR_ABORT_idaLengthOutbound Length exceeded**

**Cause:** The data type length has been exceeded.

**Action:** Verify that the length of the data type is correct.

**0x0100E ( 4110) idERR_ABORT_idaPrecisionOutbound Precision exceeded**

**Cause:** The precision of the data type has been exceeded.

**Action:** Verify that the precision of the data type is correct.

**0x0100F ( 4111) idERR_ABORT_idaScaleOutbound Scale exceeded**

**Cause:** The scale of the data type has been exceeded.

**Action:** Verify that the scale of the data type is correct.

**0x01010 ( 4112) idERR_ABORT_idaLargerThanPrecision Precision exceeded**

**Cause:** The precision of the data type has been exceeded.

**Action:** Verify that the precision of the data type is correct.

**0x01011 ( 4113) idERR_ABORT_idaInvalidParameter Invalid Argument**

**Cause:** Invalid argument.

**Action:** Verify that the arguments are valid in context.

**0x01025 ( 4133) idERR_ABORT_idc_MARSHAL_BUFFER_FULL Insufficient communication
buffer**

**Cause:** The communication buffer is not large enough.

**Action:** Verify that the communication buffer size specified in the property
file is greater than 64kB.

**0x01026 ( 4134) idERR_ABORT_idc_SOCKET_CLOSED Socket communication error**

**Cause:** The socket of the client has already been closed.

**Action:** Debug the client program.

**0x01027 ( 4135) idERR_ABORT_idc_ERR_FULL_IPC_CHANNEL No remaining IPC channels
(MAX=\<0%d\>, USED=\<1%d\>, BUFSIZE=\<2%d\>)**

**Cause:** All IPC channels have been allocated to clients.

**Action:** Use the INET/UNIX Domain channel or create more IPC channels.

**0x01028 ( 4136) idERR_ABORT_idc_SEM_INIT_OP Unable to invoke the semop()
function as described by system semaphore properties.**

**Cause:** The semaphore might have been deleted.

**Action:** Verify that the semaphore exists.

**0x01031 ( 4145) idERR_ABORT_IDU_MEMORY_INVALID_STATUS An error has been
detected in the memory manager.**

**Cause:** Internal memory manager error.

**Action:** Set the MEMORY_ALLOCATOR_USE_PRIVATE property to 0 and restart the
server. For further information about this property, refer to the *General
Reference*.

**0x0103C ( 4156) idERR_ABORT_SysCreat Unable to invoke the create() function on
[\<0%s\>]**

**Cause:** The system failed to create the file.

**Action:** Verify that the storage manager has sufficient permission for the
directory in which the file is created.

**0x01040 ( 4160) idERR_ABORT_SysWrite Unable to invoke the write() function on
[\<0%s\>]**

**Cause:** The system failed to write data to the file due to a physical disk
failure or a full disk.

**Action:** Execute the fsck command to troubleshoot and fix any filesystem
errors.

**0x01043 ( 4163) idERR_ABORT_Session_Closed The session has been closed by the
server**

**Cause:** The session has been closed by the server. This could be the result
of a session timeout.

**Action:** Check the altibase_boot.log file or other log files. Check the
properties related to session timeout.

**0x01044 ( 4164) idERR_ABORT_Query_Timeout Client's query exceeded the
execution time limit.**

**Cause:** The query ran for too long.

**Action:** Check any properties related to session timeouts, and increase if
necessary. Check the status of the system if the properties are set
appropriately.

**0x01047 ( 4167) idERR_ABORT_idm_Id_Not_Found ID not found.**

**Cause:** The ID was not found.

**Action:** Verify that the ID is valid.

**0x01048 ( 4168) idERR_ABORT_idm_Unable_To_Get_Attribute Unable to get idm
attributes**

**Cause:** Unable to get idm attributes.

**Action:** Verify the id and attributes.

**0x01049 ( 4169) idERR_ABORT_idm_Unable_To_Set_Attribute Unable to set idm
attributes**

**Cause:** Unable to set idm attributes.

**Action:** Verify the id and attributes.

**0x0104B ( 4171) idERR_ABORT_idp_NameNotFound Unable to find the property name
[\<0%s\>].**

**Cause:** The specified property name is not registered in the system.

**Action:** Check the property name.

**0x0104C ( 4172) idERR_ABORT_idp_RangeOverflow Property value overflow
[\<0%s\>]**

**Cause:** The specified property value exceeded the allowable range.

**Action:** Refer to the General Reference, and enter a property value that
falls within the range.

**0x0104D ( 4173) idERR_ABORT_idp_NoSuchEntry The entry [\<1%d\>] of the
property [\<0%s\>] does not exist.**

**Cause:** The specified property entry does not exist.

**Action:** Check whether the property entry exists.

**0x0104E ( 4174) idERR_ABORT_idp_ReadOnlyEntry The property [\<0%s\>] is
read-only.**

**Cause:** The specified property entry cannot be modified.

**Action:** Refer to the specification of the property.

**0x01050 ( 4176) idERR_ABORT_idu_NotFoundLicenseFile License File does not
exist.**

**Cause:** License file does not exist.

**Action:** Install a valid license.

**0x01051 ( 4177) idERR_ABORT_IDU_MEMORY_ALLOCATION Memory [\<0%s\>] failed.**

**Cause:** Insufficient memory.

**Action:** Verify that the system has enough memory.

**0x01052 ( 4178) idERR_ABORT_SysOpen Unable to invoke the open() function on
[\<0%s\>]**

**Cause:** The system failed to open the file.

**Action:** Verify that the file exists and that the operating system has not
already opened the maximum possible number of files.

**0x01054 ( 4180) idERR_ABORT_ASYNC_IO_FAILED AIO operation failed [\<0%d\>].**

**Cause:** - The asynchronous I/O operation timed out.

**Action:** - Please check the files on which operation was to occur.

**0x01055 ( 4181) idERR_ABORT_ASYNC_IO_READ_FAILED AIO read operation failed
[\<0%d\>].**

**Cause:** - The asynchronous I/O read operation failed.

**Action:** - Please check the files to be read.

**0x01056 ( 4182) idERR_ABORT_ASYNC_IO_WRITE_FAILED AIO write operation failed
[\<0%d\>].**

**Cause:** - The asynchronous I/O write operation failed.

**Action:** - Please check the files which could not be written to.

**0x01057 ( 4183) idERR_ABORT_ASYNC_IO_RETURN_FAILED AIO return operation failed
[\<0%d\>].**

**Cause:** - The asynchronous I/O aio_return() operation failed.

**Action:** - Please check the files on which operation was to occur.

**0x01058 ( 4184) idERR_ABORT_DISK_SPACE_EXHAUSTED Failed to create, extend or
sync a file ( Name : \<0%s\>, Start Offset : \<1%d\>, Write Size : \<2%d\> )**

**Cause:** The disk space or the user's disk quota has been exhausted.

**Action:** Increase the disk space or the user's quota for the log file, memory
db file, or disk tablespace datafile.

**0x01059 ( 4185) idERR_ABORT_EXCEED_FILE_SIZE_LIMIT Failed to increase size of
file ( Name : \<0%s\>, Start Offset : \<1%d\>, Write Size : \<2%d\> )**

**Cause:** An attempt to increase the data file size exceeded the file size
limit of the process or the maximum file size allowed by the operating system.

**Action:** Change the system file size limit.

**0x0105A ( 4186) idERR_ABORT_EXCEED_OPEN_FILE_LIMIT Failed to create file( Name
: \<0%s\>, Start Offset : \<1%d\>, Write size : \<2%d\> )**

**Cause:** The limit on the total number of open files for the system or the
maximum number of file descriptors has been reached.

**Action:** Close open files that are not in use or change system properties.

**0x0105B ( 4187) idERR_ABORT_IDU_FILE_INVALID_PATH Invalid directory path.**

**Cause:** A corresponding directory object does not exist.

**Action:** Correct the directory object parameter or create a corresponding
directory object with the CREATE DIRECTORY command.

**0x0105C ( 4188) idERR_ABORT_IDU_FILE_INVALID_FILEHANDLE Invalid file handle.**

**Cause:** A file handle was specified for which no corresponding open file
exists.

**Action:** Verify that the file handle is a value returned from a call to
FOPEN.

**0x0105D ( 4189) idERR_ABORT_IDU_FILE_INVALID_OPERATION Invalid file
operation.**

**Cause:** An attempt was made to read from a file or directory that does not
exist, or file or directory access was denied by the operating system.

**Action:** Verify the file and directory access privileges on the file system,
and, if reading, verify that the file exists.

**0x0105E ( 4190) idERR_ABORT_IDU_FILE_DELETE_FAILED File remove operation
failed.**

**Cause:** An attempt to delete a file was refused by the operating system.

**Action:** Verify that the file exists and that delete privileges have been
granted for the directory and the file.

**0x0105F ( 4191) idERR_ABORT_IDU_FILE_RENAME_FAILED File rename operation
failed.**

**Cause:** A file rename attempt was refused by the operating system, either
because the source or destination directory does not exist or is inaccessible,
the source file isn't accessible, or a file with that name already exists.

**Action:** Verify that the source file, source directory, and destination
directory exist and are accessible, and that no file with the desired name
already exists.

**0x01060 ( 4192) idERR_ABORT_IDU_FILE_NO_DATA_FOUND No data found in file.**

**Cause:** Cannot read any data from the file.

**Action:** Check whether the file is empty or the position has reached
end-of-file.

**0x01061 ( 4193) idERR_ABORT_IDU_FILE_READ_ERROR File read error.**

**Cause:** An attempt to read from a file failed.

**Action:** Verify that the file exists, that it is accessible, and that it is
open in read mode.

**0x01062 ( 4194) idERR_ABORT_IDU_FILE_WRITE_ERROR File write error.**

**Cause:** Failed to write to a file.

**Action:** Verify that the file exists, that it is accessible, and that it is
open in write or append mode.

**0x01063 ( 4195) idERR_ABORT_MESSAGE_OVERFLOW Message too long.**

**Cause:** The message to be processed is too long.

**Action:** Make the message length shorter than 2\^61.

**0x01066 ( 4198) idERR_ABORT_idp_Value_Convert_Error The property [\<0%s\>]
value [\<1%s\>] cannot be converted.**

**Cause:** The data format is invalid.

**Action:** Enter a valid data format.

**0x01067 ( 4199) idERR_ABORT_MAX_MEM_SIZE_EXCEED The memory size allocated for
the statement has exceeded the maximum limit ( Name : \<0%s\>, Wanted Memory
Size : \<1%lu\>, Max size : \<2%lu\> ).**

**Cause:** The memory size allocated for the statement has exceeded the maximum
limit.

**Action:** Increase the XXXXXXX_STMT_MEMORY_MAXIMUM property value.

**0x01068 ( 4200) idERR_ABORT_QUEUE_EMPTY Queue empty**

**Cause:** Queue empty

**Action:** Internal error.

**0x01069 ( 4201) idERR_ABORT_QUEUE_FULL Queue full**

**Cause:** Queue full

**Action:** Internal error.

**0x0106A ( 4202) idERR_ABORT_Query_Canceled Query canceled by client.**

**Cause:** The query has been canceled by the client.

**Action:** No action is necessary.

**0x0106B ( 4203) idERR_ABORT_Session_Disconnected The session has been
disconnected by the client**

**Cause:** The session has been disconnected by the client.

**Action:** No action is necessary.

**0x0106C ( 4204) idERR_ABORT_Invalid_Profile_State The query profile has
already been activated. Turn it off first.**

**Cause:** The query profile has already been activated.

**Action:** Query profiling is already enabled so no further action is required.
However, if the value of the QUERY_PROF_FLAG property must be changed, first set
the value to 0 and then set it to the desired value.

**0x0106F ( 4207) idERR_ABORT_BY_RECOVERY_TEST Recovery Test Abort Error**

**Cause:** The recovery test resulted in an abort error.

**Action:** Internal error.

**0x01073 ( 4211) idERR_ABORT_GPKI_API_Init GPKI_API_Init error: [\<0%d\>]**

**Cause:** The GPKI module failed to call the function.

**Action:** Check the error number from the altibase_boot.log file and refer to
the GPKI Manual.

**0x01074 ( 4212) idERR_ABORT_GPKI_API_GetVersion GPKI_API_GetVersion error:
[\<0%d\>]**

**Cause:** The GPKI module failed to call the function.

**Action:** Check the error number from the altibase_boot.log file and refer to
the GPKI Manual.

**0x01075 ( 4213) idERR_ABORT_GPKI_API_Finish GPKI_API_Finish error: [\<0%d\>]**

**Cause:** The GPKI module failed to call the function.

**Action:** Check the error number from the altibase_boot.log file and refer to
the GPKI Manual.

**0x01076 ( 4214) idERR_ABORT_GPKI_STORAGE_ReadCert GPKI_STORAGE_ReadCert error:
[\<0%d\>]**

**Cause:** The GPKI module failed to call the function.

**Action:** Check the error number from the altibase_boot.log file and refer to
the GPKI Manual.

**0x01077 ( 4215) idERR_ABORT_GPKI_STORAGE_ReadPriKey GPKI_STORAGE_ReadPriKey
error: [\<0%d\>]**

**Cause:** The GPKI module failed to call the function.

**Action:** Check the error number from the altibase_boot.log file and refer to
the GPKI Manual.

**0x01078 ( 4216) idERR_ABORT_GPKI_PRIKEY_CheckKeyPair GPKI_PRIKEY_CheckKeyPair
error: [\<0%d\>]**

**Cause:** The GPKI module failed to call the function.

**Action:** Check the error number from the altibase_boot.log file and refer to
the GPKI Manual.

**0x01079 ( 4217) idERR_ABORT_GPKI_CRYPT_GenRandom GPKI_CRYPT_GenRandom error:
[\<0%d\>]**

**Cause:** The GPKI module failed to call the function.

**Action:** Check the error number from the altibase_boot.log file and refer to
the GPKI Manual.

**0x0107A ( 4218) idERR_ABORT_GPKI_VersionMismatched Version mismatch error**

**Cause:** The GPKI module version is different from that of the client.

**Action:** Check the error number from the altibase_boot.log file and refer to
the GPKI Manual.

**0x0107B ( 4219) idERR_ABORT_GPKI_BINSTR_SetData GPKI_BINSTR_SetData error:
[\<0%d\>]**

**Cause:** The GPKI module failed to call the function.

**Action:** Check the error number from the altibase_boot.log file and refer to
the GPKI Manual.

**0x0107C ( 4220) idERR_ABORT_GPKI_CMS_MakeSignedAndEnvData
GPKI_CMS_MakeSignedAndEnvData error: [\<0%d\>]**

**Cause:** The GPKI module failed to call the function.

**Action:** Check the error number from the altibase_boot.log file and refer to
the GPKI Manual.

**0x0107D ( 4221) idERR_ABORT_GPKI_CRYPT_GetKeyAndIV GPKI_CRYPT_GetKeyAndIV
error: [\<0%d\>]**

**Cause:** The GPKI module failed to call the function.

**Action:** Check the error number from the altibase_boot.log file and refer to
the GPKI Manual.

**0x0107E ( 4222) idERR_ABORT_GPKI_CMS_ProcessSignedAndEnvData
GPKI_CMS_ProcessSignedAndEnvData error: [\<0%d\>]**

**Cause:** The GPKI module failed to call the function.

**Action:** Check the error number from the altibase_boot.log file and refer to
the GPKI Manual.

**0x0107F ( 4223) idERR_ABORT_GPKI_CERT_Verify GPKI_CERT_Verify error:
[\<0%d\>]**

**Cause:** The GPKI module failed to call the function.

**Action:** Check the error number from the altibase_boot.log file and refer to
the GPKI Manual.

**0x01080 ( 4224) idERR_ABORT_GPKI_CERT_Load GPKI_CERT_Load error: [\<0%d\>]**

**Cause:** The GPKI module failed to call the function.

**Action:** Check the error number from the altibase_boot.log file and refer to
the GPKI Manual.

**0x01081 ( 4225) idERR_ABORT_GPKI_CERT_GetSubjectName GPKI_CERT_GetSubjectName
error: [\<0%d\>]**

**Cause:** The GPKI module failed to call the function.

**Action:** Check the error number from the altibase_boot.log file and refer to
the GPKI Manual.

**0x01082 ( 4226) idERR_ABORT_GPKI_CERT_Unload GPKI_CERT_Unload error:
[\<0%d\>]**

**Cause:** The GPKI module failed to call the function.

**Action:** Check the error number from the altibase_boot.log file and refer to
the GPKI Manual.

**0x01083 ( 4227) idERR_ABORT_GPKI_ValueMismatched Value mismatch error**

**Cause:** The random value is different from that of the client.

**Action:** Check the GPKI module version.

**0x01084 ( 4228) idERR_ABORT_GPKI_CRYPT_Encrypt GPKI_CRYPT_Encrypt error:
[\<0%d\>]**

**Cause:** The GPKI module failed to call the function.

**Action:** Check the error number from the altibase_boot.log file and refer to
the GPKI Manual.

**0x01086 ( 4230) idERR_ABORT_GPKI_CRYPT_Decrypt GPKI_CRYPT_Decrypt error:
[\<0%d\>]**

**Cause:** The GPKI module failed to call the function.

**Action:** Check the error number from the altibase_boot.log file and refer to
the GPKI Manual.

**0x01088 ( 4232) idERR_ABORT_GPKI_dlopen dlopen error [\<0%s\>]**

**Cause:** dlopen error.

**Action:** Check the shared library.

**0x01089 ( 4233) idERR_ABORT_GPKI_dlsym dlsym error**

**Cause:** dlsym error.

**Action:** Check the shared library.

**0x0108A ( 4234) idERR_ABORT_GPKI_dlclose dlclose error**

**Cause:** dlclose error

**Action:** Check the shared library.

**0x0108B ( 4235) idERR_ABORT_CannotShrinkFile The data file size cannot be
shrunk.**

**Cause:** The data file size cannot be shrunk.

**Action:** Change the desired data file size setting.

**0x0108D ( 4237) idERR_ABORT_idu_InvalidLicense License invalid or expired.**

**Cause:** The license is invalid or has expired.

**Action:** Install a valid license.

**0x0108E ( 4238) idERR_ABORT_idu_UNLOAD_ERROR [\<0%s\>] module unload error.**

**Cause:** Dlclose error.

**Action:** Check the error number from the altibase_boot.log file and take
appropriate action.

**0x0108F ( 4239) idERR_ABORT_MODULE_IS_NOT_LOADED [\<0%s\>] module not
loaded.**

**Cause:** A module is not loaded.

**Action:** Check the error number from the altibase_boot.log file and take
appropriate action.

**0x01090 ( 4240) idERR_ABORT_FINALIZE_ERROR [\<0%s\>] : cannot finalize
module.**

**Cause:** Failed to finalize.

**Action:** Check the error number from the altibase_boot.log file and take
appropriate action.

**0x01091 ( 4241) idERR_ABORT_CannotOpenDir The system failed to open the
directory.**

**Cause:** The system failed to open the directory.

**Action:** Check the error number from the altibase_boot.log file and take
appropriate action.

**0x01092 ( 4242) idERR_ABORT_INVALID_CHARACTER character conversion error**

**Cause:** The source data abnormally terminated in the middle of a multibyte
character.

**Action:** Use a complete multibyte character.

**0x01093 ( 4243) idERR_ABORT_PARTIAL_MULTIBYTE_CHARACTER partial multibyte
character**

**Cause:** A partial multibyte character was found at the end of the input.

**Action:** Use a complete multibyte character.

**0x01095 ( 4245) idERR_ABORT_DATA_LOSS_IN_CONVERSION Character data loss in
conversion from NCHAR to CHAR**

**Cause:** When character set conversion happens between CHAR and NCHAR either
implicitly or explicitly, some characters are lost due to unmapped characters in
the destination character set.

**Action:** Verify that all characters can be mapped to the destination
character set, or set NLS_NCHAR_CONV_EXCP to false.

**0x01096 ( 4246) idERR_ABORT_FILE_OPEN Unable to open a file [\<0%s\>]**

**Cause:** The path or filename is invalid, or the storage manager does not have
permission to open the file.

**Action:** Verify that the path and filename are correct and that you have
read/write permission for the file.

**0x01098 ( 4248) idERR_ABORT_idp_Property_NotFound Unable to find the property
[SID=\<0%s\>, Name=\<%1s\>].**

**Cause:** The specified property is not registered in the system.

**Action:** Verify that the specified property is registered in the system.

**0x01099 ( 4249) idERR_ABORT_idp_Value_Accept_Error The property [\<0%s\>]
value [\<1%s\>] is not acceptable.**

**Cause:** The data format is invalid.

**Action:** Enter a valid data format.

**0x0109A ( 4250) idERR_ABORT_idp_Initialize_Error Property initialization
failed.**

**Cause:** A property is set to an invalid value.

**Action:** Identify and correct the mis-configured property.

**0x0109B ( 4251) idERR_ABORT_SysSeek Unable to invoke the seek() function on
[\<0%s\>]**

**Cause:** The system failed to write data to the file due to a physical disk
failure or a full disk.

**Action:** Execute the fsck command to troubleshoot and fix any filesystem
errors.

**0x0109D ( 4253) idERR_ABORT_InsufficientMemory Insufficient memory**

**Cause:** Insufficient memory.

**Action:** Verify that the system has enough available memory.

**0x0109E ( 4254) idERR_ABORT_InternalServerError Internal server error.**

**Cause:** An unexpected internal server error has occurred.

**Action:** Check the error number from the trace log and contact Altibase's
Support Center (http://support.altibase.com).

**0x0109F ( 4255) idERR_ABORT_IDX_LIBRARY_NOT_FOUND Library file for external
procedure/function not found : \<0%s\>\<1%s\>\<2%s\>**

**Cause:** The library file for the external procedure/function was not found.

**Action:** Verify that the specified library file exists in the library path.

**0x010A0 ( 4256) idERR_ABORT_IDX_FUNCTION_NOT_FOUND Function for external
procedure/function not found**

**Cause:** A user-defined function for the external procedure/function was not
found in the library.

**Action:** Verify that the specified function exists in the library file.

**0x010A1 ( 4257) idERR_ABORT_IDX_ENTRY_FUNCTION_NOT_FOUND Entry function for
external procedure/function not found**

**Cause:** An entry function for the external procedure/function was not found
in the library.

**Action:** Add the entry function to the library file.

**0x010A2 ( 4258) idERR_ABORT_IDX_INVALID_PROPERTY_MANIPULATION Invalid
manipulation on a parameter property value of a parameter**

**Cause:** There was an invalid manipulation of a parameter’s property value.

**Action:** Check the function in the library.

**0x010A3 ( 4259) idERR_ABORT_IDX_AGENT_PROCESS_FAILURE Failed to start an agent
process**

**Cause:** Failed to create or start an agent.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x010A4 ( 4260) idERR_ABORT_IDX_CALL_PROCEDURE_FAILURE Failed to call external
procedure/function**

**Cause:** Failed to call the specified external procedure/function.

**Action:** Check the external procedure definition.

**0x010A5 ( 4261) idERR_ABORT_IDX_AGENT_CONNECTION_FAILURE Failed to connect to
the agent : \<0%s\>**

**Cause:** Failed to connect to the agent.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x010A6 ( 4262) idERR_ABORT_IDX_AGENT_CONNECTION_LOST Connection to the agent
has been lost**

**Cause:** Connection to the agent has been lost.

**Action:** Check the trace logs of the agent.

**0x010A9 ( 4265) idERR_ABORT_DOUBLEFREE Tried to free a memory block already
freed**

**Cause:** Thread count has reached the limit.

**Action:** Increase the MAX_THREAD_COUNT property.

**0x010AA ( 4266) idERR_ABORT_DISK_OR_DEVICE_BUSY Disk or device busy ( Name :
\<0%s\>, Start Offset : \<1%d\>, Write Size : \<2%d\> )**

**Cause:** The disk space or the user's disk quota has been exhausted.

**Action:** Increase the disk space or the user's quota for the log file, memory
db file, or disk tablespace datafile.

**0x010AE ( 4270) idERR_ABORT_already_created The shared memory region is
already in use.**

**Cause:** The shared memory region is already in use.

**Action:** Please change the shared memory key value to a different value.

**0x010AF ( 4271) idERR_ABORT_SysShmGet Failed to invoke the shmget() system
function**

**Cause:** The system failed to allocate a new shared memory region due to the
lack of resources on the system.

**Action:** Please adjust parameters in order to obtain sufficient shared memory
resources.

**0x010B2 ( 4274) idERR_ABORT_No_More_Shm_Key Unable to find an available shared
memory key.**

**Cause:** No more shared memory keys are available.

**Action:** Please remove all of the shared memory regions and try again.

**0x010B3 ( 4275) idERR_ABORT_NoMore_SHM_Page Insufficient memory for database**

**Cause:** The system failed to increase the amount of memory because the
database was created in a shared memory region.

**Action:** Please shut down the database and make sure that the system has
sufficient memory using xdbshmutil.

**0x010B4 ( 4276) idERR_ABORT_Shm_Max_Size A shared memory size consumed excceds
the size than expected.**

**Cause:** The shared memory size property value is less than the size which the
process needs.

**Action:** Please increase the size of the shared memory property.

**0x010C1 ( 4289) idERR_ABORT_LATCH_TIMEOUT Timeout happens while trying to do
latch.**

**Cause:** There is a thread or process acquiring a latch for long time.

**Action:** Check which a process or thread get a latch for a long time.

**0x010C9 ( 4297) idERR_ABORT_Invalid_Process_ID The process ID is invalid.**

**Cause:** There is no process in XDB processes.

**Action:** Please check if the process ID is valid.

**0x010CA ( 4298) idERR_ABORT_Invalid_Thread_ID The thread ID is invalid.**

**Cause:** There is no thread in XDB processes.

**Action:** Please check if the thread ID is valid.

**0x010CD ( 4301) idERR_ABORT_SET_LATCH_STACK_OVERFLOW Set latch stack overflow
happens while trying to lock table.**

**Cause:** There are too many table locks acquired in a transaction.

**Action:** Reduce a table count referenced in a transaction (Maximum table
count in a transaction is 128 in LOCK_MGR_TYPE=1).

**0x010CF ( 4303) idERR_ABORT_IDX_AGENT_CONNECTION_LOST_WHILE_RECV Connection to
the agent has been lost while receiving (step : \<0%d\>)**

**Cause:** Connection to the agent has been lost while receiving.

**Action:** Check the trace logs of the agent.

**0x010D0 ( 4304) idERR_ABORT_IDX_AGENT_CONNECTION_LOST_WHILE_SEND Connection to
the agent has been lost while sending (step : \<0%d\>)**

**Cause:** Connection to the agent has been lost while sending.

**Action:** Check the trace logs of the agent.

**0x010D1 ( 4305) idERR_ABORT_IDX_AGENT_CONNECTION_LOST_BY_PEER Connection to
the agent has been lost by peer (step : \<0%d\>, Read Count : \<1%d\>, Buffer
Size : \<2%d\>)**

**Cause:** Connection to the agent has been lost by peer.

**Action:** Check the trace logs of the agent.

**0x010D3 ( 4307) idERR_ABORT_IDU_SHM_INCOMPATIBLE_CONFIG Incompatible changes
to the shared memory configuration have been detected. Previously =\> [ SHM
Chunk Size = \<0%u\>, SHM Max Chunk Count = \<1%lu\> ] Now =\> [ SHM Chunk Size
= \<2%u\>, SHM Max Chunk Count = \<3%lu\> ]**

**Cause:** Some of the shared memory configuration have been changed and the
changes require the database to be reloaded into the shared memory.

**Action:** Clear the shared memory by issuing xdbshmutil -e command and start
the server again.

**0x010D4 ( 4308) idERR_ABORT_INVALID_ENCRYPTED_TEXT Malformed or corrupted
wrapped unit.**

**Cause:** The format of the wrapped unit being compiled is not understood by
the compiler. This may be because the unit was edited or modified after it was
wrapped.

**Action:** Rewrap the unit.

**0x010DD ( 4317) idERR_ABORT_FILENAME_TOO_LONG The filename is too long
[\<0%s\>]**

**Cause:** The filename is too long.

**Action:** Shorten the filename.

**0x010DE ( 4318) idERR_ABORT_FILE_ALREADY_EXIST The file already exists
[\<0%s\>]**

**Cause:** The file already exists.

**Action:** Try another filename.

**0x010DF ( 4319) idERR_ABORT_INVALID_ACCESS Access denied [\<0%s\>]**

**Cause:** The file cannot be accessed.

**Action:** Verify the permission of the file, or the parent directory.

**0x010E0 ( 4320) idERR_ABORT_NO_SUCH_FILE No such file exists [\<0%s\>]**

**Cause:** The file does not exist.

**Action:** Verify that the path and the filename are correct.

**0x010E1 ( 4321) idERR_ABORT_WRONG_Profile_Flag The value of QUERY_PROF_FLAG
property exceeds the maximum value(\<0%d\>).**

**Cause:** The current value of QUERY_PROF_FLAG property exceeds the maximum
value 63.

**Action:** Modify the value of QUERY_PROF_FLAG property to be less than or
equal to 63.

**0x010EB ( 4331) idERR_ABORT_NOT_SUPPORT_FALLOCATE The operation is not
supported by the filesystem(or kernel) (\<0%s\>)**

**Cause:** The filesystem(or kernel) containing the file does not support this
operation.

**Action:** Set the LOG_CREATE_METHOD property value to 0 and restart the
server.

**0x010EC ( 4332) idERR_ABORT_Sysfallocate Unable to invoke the fallocate()
function on [\<0%s\>].**

**Cause:** The system failed to call the fallocate() function.

**Action:** Set the LOG_CREATE_METHOD property value to 0 and restart the
server.

**0x010ED ( 4333) idERR_ABORT_InternalServerErrorWithString Internal server
error ( \<0%s\> ).**

**Cause:** An unexpected internal server error has occurred.

**Action:** Check the error number from the trace log and contact Altibase's
Support Center (http://support.altibase.com/en/).

**0x010EE ( 4334) idERR_ABORT_IDU_MEMORY_INVALID_SET_STATUS An error has been
detected in the memory manager. [\<0%s\>]**

**Cause:** Internal memory manager error.

**Action:** Set the MEMORY_ALLOCATOR_USE_PRIVATE property to 0 and restart the
server. Check the error number from the trace log and contact Altibase’s Support
Center (http://support.altibase.com/en/).

### IGNORE

**0x02000 ( 8192) idERR_IGNORE_NoError No ID module error**

**Cause:** This is not an error.

**Action:** You may safely ignore this message.

**0x02016 ( 8214) idERR_IGNORE_idc_CHANNEL_OPEN_FAILED Unable to open a
communication channel because none has been created**

**Cause:** Failed to open a communication channel because no communication
channel has been created yet.

**Action:** Check kernel properties.

**0x0206E ( 8302) idERR_IGNORE_VAR_STRING_APPEND_FORMAT_TOO_LONG VarString
appendFormat too long**

**Cause:** VarString appendFormat too long.

**Action:** Internal error.

**0x020A7 ( 8359) idERR_IGNORE_THREAD_CREATEFAIL Thread object cannot be
created.**

**Cause:** A thread object cannot be created.

**Action:** Check kernel properties.

**0x020A8 ( 8360) idERR_IGNORE_THREADCOUNT_EXCEEDED The number of Threads has
reached to maximum count : \<0%d\>**

**Cause:** Thread count has reached the limit.

**Action:** Increase the MAX_THREAD_COUNT property.

**0x020AB ( 8363) idERR_IGNORE_THREAD_NOTSTARTED Joining a thread that is not
started**

**Cause:** Trying to join a thread that is not started.

**Action:** Check the error number from the trace log and contact Altibase's
Support Center (http://support.altibase.com/en/).

**0x020AC ( 8364) idERR_IGNORE_THREAD_UNBOUND Joining a detached thread**

**Cause:** Trying to join a thread that is not joinable

**Action:** Check the error number from the trace log and contact Altibase's
Support Center (http://support.altibase.com/en/).

**0x020C4 ( 8388) idERR_IGNORE_FAIL_OPEN_ISQL_PTY_FILE can not to open a file
that includes the path of pty.**

**Cause:** Failed to can not to open a file that includes the path of xdbisql
pty.

**Action:** This error does not originate with Altibase.

**0x020C6 ( 8390) idERR_IGNORE_FAIL_COMMIT_TRANS_DUE_TO_MAX_ROW Transaction
faces a error while committing.**

**Cause:** The table has more rows than the max row limitation.

**Action:** Check the table's max rows.

**0x020E2 ( 8418) idERR_IGNORE_NO_SUCH_CPUINFO Unable to retrieve CPU
information (errno:\<0%d\>).**

**Cause:** CPU affinity configuration is not found.

**Action:** Verify the error number in the trace log and contact Altibase
Support Center (http://support.altibase.com/en/).

**0x020E3 ( 8419) idERR_IGNORE_EXCEED_NUMA_NODE The NUMA node number [\<0%d\>]
exceeds the maximum value [\<1%d\>].**

**Cause:** The NUMA node number exceeds the maximum value.

**Action:** Verify the NUMA node number and valid range in the trace log and
contact Altibase Support Center. (http://support.altibase.com/en/).

**0x020E4 ( 8420) idERR_IGNORE_EXCEED_CPUNO The CPU number [\<0%d\>]/[\<1%d\>]
exceeded the supported maximum value [\<2%d\>]/[\<3%d\>].**

**Cause:** The CPU number exceeds the maximum value.

**Action:** Verify the CPU number and valid range in the trace log and contact
Altibase Support Center. (http://support.altibase.com/en/).

**0x020E5 ( 8421) idERR_IGNORE_INVALID_CPUNO Invalid CPU number [\<0%d\>]. The
Valid range is 0 to \<1%d\>.**

**Cause:** The CPU number is invalid.

**Action:** Verify the CPU number and valid range in the trace log and contact
Altibase Support Center (http://support.altibase.com/en/).

**0x020E6 ( 8422) idERR_IGNORE_INVALID_NUMA_NODE_NO Invalid NUMA node number
[\<0%d\>]. The Valid range is 0 to \<1%d\>.**

**Cause:** The NUMA node number is invalid.

**Action:** Verify the NUMA node number and valid range in the trace log and
contact Altibase Support Center (http://support.altibase.com/en/).

**0x020E7 ( 8423) idERR_IGNORE_BINDTHREAD_FAILED Unable to set CPU affinity
(errno:\<0%d\>).**

**Cause:** The system function failed to bind cpusets on a thread.

**Action:** Verify the error number in the trace log and contact Altibase
Support Center (http://support.altibase.com/en/).

**0x020E8 ( 8424) idERR_IGNORE_BIND_PROCESS_FAILED Failed to set CPU affinity on
a process (errno:\<0%d\>).**

**Cause:** The system function failed to bind cpusets on a process.

**Action:** Verify the error number in the trace log and contact Altibase
Support Center (http://support.altibase.com/en/).

**0x020E9 ( 8425) idERR_IGNORE_UNBINDTHREAD_FAILED Failed to unset CPU affinity
on a thread.**

**Cause:** The CPU number is invalid.

**Action:** This message can be disregarded.

**0x020EA ( 8426) idERR_IGNORE_UNBIND_PROCESS_FAILED Failed to unset CPU
affinity on a process.**

**Cause:** The CPU number is invalid.

**Action:** This message can be disregarded.

\# Server Internal Message

2.SM Error Code
---------------

### FATAL

**0x10002 ( 65538) smERR_FATAL_FileDelete Unable to delete \<0%s\> file**

**Cause:** The system failed to unlink the file.

**Action:** Terminate unnecessary processes.

**0x10006 ( 65542) smERR_FATAL_MunmapFail Failed to invoke the unmap() system
function**

**Cause:** Insufficient system resources.

**Action:** Verify that there are enough system resources. Check the error
number from the trace log and contact Altibase's Support Center
(http://support.altibase.com/en/).

**0x1000A ( 65546) smERR_FATAL_SysShmDt Failed to invoke the shmdt() system
function**

**Cause:** The system failed to detach a shared memory region from a process.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x1000B ( 65547) smERR_FATAL_SysShmCtl Failed to invoke the shmctl() system
function**

**Cause:** The system failed to remove shared memory.

**Action:** Change kernel parameters related to shared memory.

**0x1000C ( 65548) smERR_FATAL_Systhrjoin Failed to invoke the thr_join() system
function**

**Cause:** The system failed to join threads.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x1000D ( 65549) smERR_FATAL_ThrMutexInit Unable to initialize a mutex.**

**Cause:** The system failed to initialize a mutex.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com).

**0x1000E ( 65550) smERR_FATAL_ThrMutexDestroy Failed to invoke the
mutex_destroy() system function**

**Cause:** The system failed to remove a mutex.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x1000F ( 65551) smERR_FATAL_ThrMutexLock Failed to invoke the mutex_lock()
system function**

**Cause:** The system failed to lock a mutex.

\# \*Action : Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x10010 ( 65552) smERR_FATAL_ThrMutexUnlock Failed to invoke the
mutex_unlock() system function**

**Cause:** The system failed to unlock a mutex.

\# \*Action : Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x10011 ( 65553) smERR_FATAL_ThrCondInit Failed to invoke the cond_init()
system function**

**Cause:** The system failed to initialize a condition variable.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x10012 ( 65554) smERR_FATAL_ThrCondSignal Failed to invoke the cond_signal()
system function**

**Cause:** The system failed to signal using a condition variable.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x10013 ( 65555) smERR_FATAL_ThrCondDestroy Failed to invoke the
cond_destroy() system function**

**Cause:** The system failed to remove a condition variable.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x10014 ( 65556) smERR_FATAL_ThrCondWait Failed to invoke the cond_wait()
system function**

**Cause:** Invalid condition value or invalid mutex.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x10019 ( 65561) smERR_FATAL_SysRead Failed to invoke the read() system
function**

**Cause:** The system failed to read from the file.

**Action:** Check the file system.

**0x1001A ( 65562) smERR_FATAL_Sysfstat Failed to invoke the fstat() system
function**

**Cause:** The system failed to invoke the fstat() function.

**Action:** Check the file system.

**0x1001C ( 65564) smERR_FATAL_PageCorrupted A page is corrupt. ( Current Space
ID : \<0%d\>, Current Page ID : \<1%d\> )**

**Cause:** The page was not completely written.

**Action:** Recover the tablespace that contains the corrupt page using backup
and recovery utilities.

**0x10043 ( 65603) smERR_FATAL_WrongLogFileSize The size of the log file is
wrong \<0%s\>.**

**Cause:** The file system has a problem.

**Action:** Check the file system.

**0x10048 ( 65608) smERR_FATAL_TooLongDBName Database filename too long ( A
database file name must be shorter than \<0%d\> characters. )**

**Cause:** The database file name is too long.

**Action:** Use a database file name whose length does not exceed the limit.

**0x1004B ( 65611) smERR_FATAL_Shm_No_Permission No permission for the shared
memory database**

**Cause:** A shared memory region has already been created with the same key,
but with a different UID.

**Action:** Remove the shared memory region, or create a shared memory region
with another key.

**0x10050 ( 65616) smERR_FATAL_smnNotSupportedIndex The index type is not
supported.**

**Cause:** The index type is not supported.

**Action:** Refer to the list of supported index types.

**0x10052 ( 65618) smERR_FATAL_smiCursorNotOpened The cursor has not been opened
yet.**

**Cause:** The cursor has not been opened yet.

**Action:** Open the cursor before using it.

**0x10054 ( 65620) smERR_FATAL_smiNoSelectedRow No rows were selected.**

**Cause:** No rows were selected.

**Action:** Select a row to update or delete.

**0x10057 ( 65623) smERR_FATAL_Uncommitted_Row_Found An uncommitted row was
found.**

**Cause:** An uncommitted row was found.

\# \*Action : Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x1005E ( 65630) smERR_FATAL_smiChildStatementExist One or more child
statements exists.**

**Cause:** A cursor cannot be opened when a child statement exists.

**Action:** Do not open a cursor when a child statement exists.

**0x10063 ( 65635) smERR_FATAL_Overflow_DB_Size The database size is larger than
specified in the property. (Specified Page Limit=\<0%lu\> : Allocated Page
Size=\<1%vu\>)**

**Cause:** The database page count is too low.

**Action:** Increase the MEM_MAX_DB_SIZE property value.

**0x10068 ( 65640) smERR_FATAL_smnColumnNotFound Column not found**

**Cause:** Unable to find the column.

**Action:** Verify that the column you are looking for is valid.

**0x1006A ( 65642) smERR_FATAL_Shm_Link_Not_Exist A shared memory link has been
disconnected. Remove it and try again.**

**Cause:** One or more shared memory links are not connected.

**Action:** Remove the shared memory regions and try again.

**0x1006B ( 65643) smERR_FATAL_Shm_Link_Invalid_State Invalid shared memory link
found. Remove it and try again.(key = \<0%d\>)**

**Cause:** The system failed to link a shared memory region.

**Action:** Remove all of the shared memory regions, and try again.

**0x1006C ( 65644) smERR_FATAL_Shm_Link_Invalid_Version Invalid shared memory
link version. Remove it and try again (key = \<0%d\>).**

**Cause:** One or more shared memory links has an invalid version.

**Action:** Remove all shared memory regions, and try again.

**0x1006E ( 65646) smERR_FATAL_smiCantExecuteDDL Unable to execute a DDL.**

**Cause:** Either another statement already exists or a cursor is already open.

**Action:** Verify that no other statement currently exists. Ensure that cursors
are opened only once.

**0x1006F ( 65647) smERR_FATAL_smiCantOpenUpdateCursor Unable to open an update
cursor.**

**Cause:** A read-only statement is not allowed to open an update cursor.

**Action:** Verify that an update cursor is not opened in a read-only statement.

**0x10070 ( 65648) smERR_FATAL_smiCantRestartUpdateCursor Unable to restart an
update cursor.**

**Cause:** An update cursor cannot be restarted.

**Action:** Verify that no attempt to restart an update cursor is being made.

**0x1007A ( 65658) smERR_FATAL_smiCantEndStatement_too_many Unable to end the
statement because it has child statements (The number of child statements is
[\<0%d\>].)**

**Cause:** The statement has child statements.

**Action:** End all of the child statements.

**0x1007B ( 65659) smERR_FATAL_smiCantEndStatement_not_closed Unable to end the
statement because it has open cursors.**

**Cause:** The statement has open cursors.

**Action:** Close all of the open cursors.

**0x1007F ( 65663) smERR_FATAL_ShmDB_Signature_Mismatch The DB signature in the
shared memory region and the backup database file are different. (Backup DB :
\<0%s\>, Shared DB : \<1%s\>)**

**Cause:** The shared memory region and the backup database file have different
timestamps.

**Action:** Remove all of the shared memory regions and try again.

**0x10082 ( 65666) smERR_FATAL_DISABLED_ABORT_IN_LOGGING_LEVEL_0 ABORT is
disabled.**

**Cause:** There is no log when LOGGING_LEVEL is set to 0.

**Action:** Check the value of the LOGGING_LEVEL and whether a transaction was
aborted.

**0x10085 ( 65669) smERR_FATAL_CannotOpenDir The system failed to open the
directory. ( Directory Name : \<0%s\> )**

**Cause:** The system failed to invoke the opendir() system function.

**Action:** Check the altibase_error.log file for details.

**0x10086 ( 65670) smERR_FATAL_CannotReadDir The system failed to read the
directory.**

**Cause:** The system failed to invoke the readdir_r() system function.

**Action:** Check the altibase_boot.log file.

**0x1008A ( 65674) smERR_FATAL_MEMBASE_INVALID The database is inconsistent.**

**Cause:** The database is inconsistent.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x1008D ( 65677) smERR_FATAL_NotFoundDataFile The data file containing page
[\<0%d\>] does not exist. ( Tablespace - ID : \<1%d\>, Type : \<2%d\> )**

**Cause:** The data file does not exist.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x1009C ( 65692) smERR_FATAL_INVALID_SHARED_MEMORY_DATABASE When the
TRANSACTION_DURABILITY_LEVEL value is not 3, a shared memory database cannot be
used. Set the SHM_DB_KEY property to 0.**

**Cause:** An attempt was made to use a shared memory database when the
TRANSACTION_DURABILITY_LEVEL value was not 3.

**Action:** Please set the TRANSACTION_DURABILITY_LEVEL value to 3, or set the
SHM_DB_KEY value to 0.

**0x100BA ( 65722) smERR_FATAL_MISMATCHED_FILENO_IN_LOGFILE Mismatched log file
NO. The number of the log file(\<0%s\>) was originally \#\<1%d\>, which is
different from the one indicated by its name, \#\<2%d\>.**

**Cause:** The log file has been renamed.

**Action:** Check if the logfile has been renamed, and rename it to its original
name.

**0x100C3 ( 65731) smERR_FATAL_INVALID_MEM_MAX_DB_SIZE MEM_MAX_DB_SIZE(\<0%d\>)
is less than EXPAND_CHUNK_PAGE_COUNT(\<1%d\>) \* PAGE_SIZE.**

**Cause:** The MEM_MAX_DB_SIZE property value is invalid.

**Action:** Use a larger value for the MEM_MAX_DB_SIZE property.

**0x100D4 ( 65748) smERR_FATAL_TooLongTBSName Tablespace file name too long. (A
tablespace file name must be shorter than \<0%d\> characters.)**

**Cause:** The tablespace file name is too long.

**Action:** Verify that the tablespace file name does not exceed the limit.

**0x100D5 ( 65749) smERR_FATAL_Shm_Link_Invalid_TBSID Invalid shared memory
linkage tablespace ID. Remove it and try again (Tablespace ID on Shared Memory
Chunk= \<0%d\>, Expected Tablespace ID on Shared Memory Chunk= \<1%d\>).**

**Cause:** The tablespace ID and the tablespace ID stored in the tablespace
header in shared memory are different.

**Action:** Remove all shared memory regions and restart the server.

**0x100D6 ( 65750)
smERR_FATAL_INVALID_SHARED_MEMORY_DATABASE_TRIAL_TO_DIFFERENT_RESTORE_MODE
Invalid Shared Memory. An attempt was made to restore a tablespace in a
different mode. Remove all shared memory regions and restart Altibase.**

**Cause:** A shared memory region is invalid.

**Action:** Remove all shared memory regions and try again.

**0x1010C ( 65804) smERR_FATAL_ALLOC_NEW_EXPAND_CHUNK Fatal error during alloc
new expand chunk**

**Cause:** Insufficient available memory.

**Action:** Verify that there is enough available memory and disk space.

**0x1013A ( 65850) smERR_FATAL_ErrNeedMoreLog There are insufficient logfiles,
or invalid logfiles at '\<0%s\>'.**

**Cause:** There are insufficient or invalid logfiles.

**Action:** Check the logfiles.

**0x10191 ( 65937) smERR_FATAL_PageFlushStopped Failed to flush pages.
[err:%d]**

**Cause:** The secondary flusher has stopped due to an unexpected problem.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com).

**0x10192 ( 65938) smERR_FATAL_PageReadStopped Failed to read a page.**

**Cause:** Cannot read page from the secondary buffer.

**Action:** Check the secondary buffer path.

**0x101AF ( 65967) smERR_FATAL_InvalidLSNOffset Invalid LSN Offset (File
No=\<0%u\>, Offset=\<1%u\>)**

**Cause:** LSN Offset is invalid.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center(http://support.altibase.com).

### ABORT

**0x11000 ( 69632) smERR_ABORT_already_created The shared memory region is
already in use.**

**Cause:** The shared memory region is already in use.

**Action:** Change the shared memory key value to a different value.

**0x11001 ( 69633) smERR_ABORT_NoMore_SHM_Page Insufficient memory for
database**

**Cause:** The system failed to increase the amount of memory because the
database was created in a shared memory region.

**Action:** Shut down the database and verify that the system has sufficient
memory using shmutil.

**0x11003 ( 69635) smERR_ABORT_FileDelete Unable to delete \<0%s\> file**

**Cause:** The system failed to unlink the file.

**Action:** Terminate unnecessary processes.

**0x11008 ( 69640) smERR_ABORT_SysShmGet Failed to invoke the shmget() system
function**

**Cause:** The system failed to allocate a new shared memory region due to the
lack of resources on the system.

**Action:** Adjust parameters in order to obtain sufficient shared memory
resources.

**0x11009 ( 69641) smERR_ABORT_SysShmAt Failed to invoke the shmat() system
function**

**Cause:** The system failed to attach a shared memory region to a process.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x11016 ( 69654) smERR_ABORT_NotFoundSavepoint Savepoint not found**

**Cause:** There is no such savepoint in the transaction.

**Action:** Verify that the use of the savepoint is correct.

**0x11018 ( 69656) smERR_ABORT_BACKUP_DISK_INVALID The version of data file for
backup is not compatible with the version of storage manager. Backup DB =\> [
Version ID = \<0%s\>, Bit = \<1%d\>, Endian = \<2%s\> LogSize = \<3%lu\>
Transaction Table Size = \<4%d\> ] Server=\>[ Version ID = \<5%s\>, Bit =
\<6%d\>, Endian = \<7%s\> LogSize = \<8%lu\> Transaction Table Size = \<9%d\>
]**

**Cause:** Database data files are not backwards compatible.

**Action:** Import or export the database, or use a previous version of the
storage manager that is compatible with the data file.

**0x1101F ( 69663) smERR_ABORT_InvalidAutoExtFileSize The MAXSIZE of the data
file cannot be less than its current size. ( Request Max Size : \<0%lu\> pages,
Current Size : \<1%lu\> pages )**

**Cause:** The MAXSIZE of the data file is less than the current size of the
data file.

**Action:** Set the MAXSIZE of the data file appropriately.

**0x11020 ( 69664) smERR_ABORT_InitExceedMaxFileSize The INITSIZE of the data
file exceeds the maximum file size. ( Request Init Size : \<0%lu\> pages,
Maximum File Size : \<1%lu\> pages )**

**Cause:** The INITSIZE of the data file exceeds the maximum file size.

**Action:** Set the INITSIZE of the data file correctly.

**0x11022 ( 69666) smERR_ABORT_MaxExceedMaxFileSize The MAXSIZE of the data file
exceeds the maximum file size. ( Request Max Size : \<0%lu\> pages, Maximum File
Size : \<1%lu\> pages )**

**Cause:** The MAXSIZE of the data file exceeds the maximum file size.

**Action:** Set the MAXSIZE of the data file correctly.

**0x11023 ( 69667) smERR_ABORT_InvalidFilePathABS The data file path is not an
absolute path.**

**Cause:** The data file path must be an absolute path.

**Action:** Check the environment variable ALTIBASE_HOME for this account.

**0x11024 ( 69668) smERR_ABORT_InvalidFilePathKeyWord The data file path
contains special keywords or reserved system keywords.**

**Cause:** The data file path contains special keywords or reserved system
keywords.

**Action:** Verify that the data file path does not contain special keywords or
reserved system keywords.

**0x11025 ( 69669) smERR_ABORT_AlreadyExistFile The data file already exists (
File Name : \<0%s\> ).**

**Cause:** The data file already exists.

**Action:** Add the 'REUSE' clause to the CREATE statement, or remove the
existing datafile.

**0x11027 ( 69671) smERR_ABORT_NotExistFile The data file does not exist.**

**Cause:** The data file does not exist.

**Action:** Verify that the data file exists.

**0x11028 ( 69672) smERR_ABORT_NoReadPermFile The path[ \<0%s\> ] does not pass
the test for read permission.**

**Cause:** The path does not pass the test for read permission.

**Action:** Grant read permission for the path.

**0x11029 ( 69673) smERR_ABORT_NoWritePermFile The path[ \<0%s\> ] does not pass
the test for write permission.**

**Cause:** The path does not pass the test for write permission.

**Action:** Grant write permission for the path.

**0x1102A ( 69674) smERR_ABORT_NotFoundTableSpaceNodeByName Tablespace node not
found ( Name : \<0%s\> )**

**Cause:** The tablespace was not found.

**Action:** Verify that the desired tablespace exists.

**0x1102B ( 69675) smERR_ABORT_NotFoundTableSpaceNode Tablespace node not found
( ID : \<0%d\> )**

**Cause:** The tablespace was not found.

**Action:** Verify that the desired tablespace exists.

**0x1102C ( 69676) smERR_ABORT_MustBeDataFileOnlineMode The data file node must
be in online mode (FID:\<0%d\>).**

**Cause:** The data file node must be in online mode.

**Action:** Change the data file node to online mode and try again.

**0x11030 ( 69680) smERR_ABORT_InvalidExtendFileSize The data file cannot be
increased in size because the requested size is bigger than the maximum size. (
Request Size : \<0%lu\> pages, Maximum File size : \<1%lu\> pages )**

**Cause:** The datafile cannot be resized to a value that exceeds its maximum
size.

**Action:** Resize the datafile to a size that does not exceed its maximum
limit.

**0x11031 ( 69681) smERR_ABORT_NotEnoughTableSpaceID Unable to create
tablespace. (current greatest tablespace ID : \<0%d\>)**

**Cause:** The number of tablespaces has reached the maximum.

**Action:** Use an existing tablespace or rebuild the database.

**0x11032 ( 69682) smERR_ABORT_AlreadySetAutoExtendMode The attribute of
AUTOEXTEND mode has already been set. (FID :\<0%d\>)**

**Cause:** The AUTOEXTEND mode has already been set.

**Action:** No action is necessary.

**0x11033 ( 69683) smERR_ABORT_forbiddenOpWhileBackup \<0%s\> cannot operate
while a tablespace is in the process of being backed up.**

**Cause:** A tablespace is currently being backed up.

**Action:** Wait until the tablespace backup process finishes.

**0x11034 ( 69684) smERR_ABORT_NotFoundDataFileNode Data file node not found (
\<0%s\> )**

**Cause:** The data file node was not found.

**Action:** Verify that the data file exists.

**0x11035 ( 69685) smERR_ABORT_NotEnoughFreeSpace The tablespace does not have
enough free space ( TBS Name :\<0%s\>, Type : \<1%d\>, Used Page Limit : \<2%d\>
).**

**Cause:** The tablespace does not have enough free space.

**Action:** Add a new data file.

**0x11036 ( 69686) smERR_ABORT_CannotRemoveDataFileNode The data file is in
use.**

**Cause:** The data file is in use.

**Action:** No action is necessary.

**0x11037 ( 69687) smERR_ABORT_CannotDropTableSpace Unable to drop
system-related tablespaces.**

**Cause:** SYSTEM, UNDO, and SYSTEM TEMP tablespaces cannot be dropped.

**Action:** Verify that the tablespace is not a system tablespace.

**0x11038 ( 69688) smERR_ABORT_CannotOfflineTableSpace Unable to change the
tablespace to offline mode.**

**Cause:** SYSTEM, UNDO or SYSTEM TEMP tablespaces cannot be offlined.

**Action:** Verify that the tablespace is not a system tablespace.

**0x11039 ( 69689) smERR_ABORT_InvalidLogAnchorFile The log anchor file does not
exist or is not valid.**

**Cause:** The loganchor file does not exist or is invalid.

**Action:** Specify the loganchor file directory for the LOGANCHOR_DIR property.

**0x1103E ( 69694) smERR_ABORT_MediaRecoDataFile \<0%s\> is only allowed during
the control phase.**

**Cause:** The user tried to execute ALTER DATABASE CREATE data file, or tried
to rename a file, during the service phase.

**Action:** Shut down and start up in the control phase.

**0x11041 ( 69697) smERR_ABORT_Aborted A deadlock situation has been detected.**

**Cause:** A deadlock victim transaction has been stopped and terminated due to
the deadlock resolution scheme.

**Action:** The transaction was rolled back. Re-execute the transaction.

**0x11044 ( 69700) smERR_ABORT_SequenceReachMaxValue Sequence upper bound
exceeded**

**Cause:** Sequence upper bound exceeded.

**Action:** Reinitialize the sequence.

**0x11045 ( 69701) smERR_ABORT_SequenceReachMinValue Sequence lower bound
exceeded**

**Cause:** Sequence lower bound exceeded.

**Action:** Reinitialize the sequence.

**0x11046 ( 69702) smERR_ABORT_SequenceNotInitialized The sequence has not been
initialized yet.**

**Cause:** An attempt was made to use a sequence that has not been initialized
yet.

**Action:** Reinitialize the sequence first.

**0x11047 ( 69703) smERR_ABORT_NotDir Not a directory**

**Cause:** The specified path is not a directory.

**Action:** Specify a valid directory name.

**0x11049 ( 69705) smERR_ABORT_TooManyPage Too many pages were allocated (
Maximum Number of Pages=\<0%ld\> ).**

**Cause:** The number of pages has exceeded the maximum limit.

**Action:** The system failed to increase the size of the database. Refer to the
SQL manual.

**0x1104A ( 69706) smERR_ABORT_smiTraverseNotApplicable Unable to traverse**

**Cause:** Failed to next-traverse a cursor because the cursor was not used in
the proper order.

**Action:** Traverse the cursor in the correct order.

**0x1104D ( 69709) smERR_ABORT_smiUpdateStatementExist An update statement
already exists.**

**Cause:** An UPDATE statement already exists.

**Action:** Do not use the savepoint operation when an UPDATE statement exists
on one of the parent statements.

**0x1104E ( 69710) smERR_ABORT_smiStatementExist One or more statements exist.**

**Cause:** One or more statements exist.

**Action:** A transaction operation can be used only when no statements exist.

**0x1104F ( 69711) smERR_ABORT_smiUpdateOverflow Too many update cursors on a
transaction**

**Cause:** The number of update cursors on a transaction exceeds the limitation.

**Action:** Roll back the work of the transaction.

**0x11051 ( 69713) smERR_ABORT_smiCursorOpened The cursor has already been
opened.**

**Cause:** The cursor has already been opened.

**Action:** Open another cursor, or do not open the same cursor twice.

**0x11053 ( 69715) smERR_ABORT_smiWriteNotApplicable The function is not allowed
to be used in read-only mode.**

**Cause:** This function cannot be used in read-only mode.

**Action:** Verify that the function can be used in read-only mode.

**0x11058 ( 69720) smERR_ABORT_smnUniqueViolation The row already exists in a
unique index.**

**Cause:** A duplicate key was inserted or updated.

**Action:** Do not insert or update a duplicate key, or drop the unique
constraint.

**0x11059 ( 69721) smERR_ABORT_smnNotFoundByIndexName Index type name not
found**

**Cause:** It is impossible to find the index type name

**Action:** Select an appropriate index.

**0x1105A ( 69722) smERR_ABORT_smcFixedPageSizeError The fixed record size
exceeds the size of one page.**

**Cause:** A table could not be created because the record size exceeds the size
of one page.

**Action:** Create a table for which the record size is less than the size of
one page.

**0x1105B ( 69723) smERR_ABORT_smcVarColumnSizeError A variable column size
exceeds the maximum size for a variable column.**

**Cause:** A variable column that is larger than a page cannot be created.

**Action:** Reduce the size of the variable column so that it is less than the
size of one page.

**0x1105C ( 69724) smERR_ABORT_Too_Long_Var_Data A variable data size exceeds
the maximum size of a variable item.**

**Cause:** A variable data size exceeds the maximum size of a variable item.

**Action:** Change the variable data's length so that it does not exceed 32KB.

**0x1105D ( 69725) smERR_ABORT_smiCantBeginUpdateStatement Unable to begin a new
update statement.**

**Cause:** Either the statement is read-only, or more than one UPDATE child
statement has been requested.

**Action:** Verify that the request to begin a new UPDATE statement is valid.

**0x1105F ( 69727) smERR_ABORT_smiUpdateSameTable No more than one update cursor
can be used on a table.**

**Cause:** Only one update cursor can be used on a table.

**Action:** Do not use more than one update cursor on a table.

**0x11060 ( 69728) smERR_ABORT_Already_Locked A lock has already been acquired
by another transaction.**

**Cause:** A lock has already been acquired by another transaction.

**Action:** This situation occurs when a user executes a DDL, and a locked item
has already been modified by another transaction.

**0x11061 ( 69729) smERR_ABORT_Column_Mismatch Unable to alter the table because
the information does not correspond to the definition of the column.**

**Cause:** Table information (e.g. a constraint) cannot be modified because it
is not in the specified column.

**Action:** Try again with the correct column and modification information.

**0x11062 ( 69730) smERR_ABORT_Index_Not_Found The index was not found on the
database.**

**Cause:** The index was not found in the database.

**Action:** Verify that the index is correct.

**0x11064 ( 69732) smERR_ABORT_Table_Not_Found The table was not found in the
database.**

**Cause:** The specified table was not found in the database.

**Action:** Verify that the specified table exists in the database.

**0x11065 ( 69733) smERR_ABORT_Maximum_Index_Count The number of indices in the
table exceeds the limit(\<0%d\>).**

**Cause:** The number of indices in the table exceeds the limit.

**Action:** Do not create more than the allowed number of indices for a table.

**0x11066 ( 69734) smERR_ABORT_Invalid_ID_Value Invalid column ID**

**Cause:** The column IDs in the column list do not increment sequentially.

**Action:** Verify that the column ID is correct and create the table again.

**0x11067 ( 69735) smERR_ABORT_Maximum_Column_count Too many columns in a
table**

\# \*Cause : Too many columns were specified in the CREATE/ALTER TABLE
statement.

**Action:** Reduce the number of columns to 1024 or less.

**0x11069 ( 69737) smERR_ABORT_INTERNAL_ARG Internal server error in the storage
manager (\<0%s\>)**

**Cause:** Internal server error.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x1106D ( 69741) smERR_ABORT_No_More_Shm_Key Unable to find an available
shared memory key.**

**Cause:** No more shared memory keys are available.

**Action:** Remove all of the shared memory regions and try again.

**0x11071 ( 69745) smERR_ABORT_smiNotRootStatement Statement must be the root of
the statement.**

**Cause:** The statement is not the root of the statement.

**Action:** Abort the transaction.

**0x11072 ( 69746) smERR_ABORT_smiInvalidCursorOpen Invalid cursor open**

**Cause:** Invalid cursor open

**Action:** Abort the transaction.

**0x11074 ( 69748) smERR_ABORT_InvalidBackupFile [\<0%s\>] is an invalid backup
file for the table.**

**Cause:** The table backup file is invalid.

**Action:** Check the database version or backup file.

**0x11075 ( 69749) smERR_ABORT_smcExceedLockTimeWait The transaction has
exceeded the lock timeout specified by the user.**

**Cause:** The transaction failed to lock the object.

**Action:** Increase the transaction's lock timeout value or check whether the
data has a transaction with a long-term lock.

**0x11076 ( 69750) smERR_ABORT_NoExistFile File not found (\<0%s\>)**

**Cause:** The db file or log file does not exist.

**Action:** Verify that the path and filename are correct.

**0x11077 ( 69751) smERR_ABORT_NoExistPath Directory path not found (\<0%s\>).**

**Cause:** The directory path does not exist.

**Action:** Create the directory path or specify a valid directory.

**0x11079 ( 69753) smERR_ABORT_BackupWrite Disk full.**

**Cause:** The disk is full.

**Action:** Provide additional disk space.

**0x1107C ( 69756) smERR_ABORT_droped_Sequence The sequence has already been
dropped.**

**Cause:** The sequence has already been dropped.

**Action:** Check whether the sequence exists.

**0x11084 ( 69764) smERR_ABORT_DISABLED_INDEX The Index is disabled.**

**Cause:** The Index with the table is disabled.

**Action:** Enable the index associated with the table.

**0x11087 ( 69767) smERR_ABORT_ExceedMaxRows The record count has reached the
maximum limit.**

**Cause:** The number of records has reached or exceeded the maximum limit.

**Action:** Increase the values of MAXROWS for the table.

**0x11088 ( 69768) smERR_ABORT_INVALID_ROW_SCN Invalid row SCN**

**Cause:** Invalid row SCN

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x11089 ( 69769) smERR_ABORT_INVALID_COLUMN_SIZE Invalid column size**

**Cause:** The size of the column is invalid.

**Action:** Check the altibase_error.log file for details.

**0x1108C ( 69772) smERR_ABORT_Invalid_MaxRows Invalid MAXROWS value**

**Cause:** The values of MAXROWS is less than the number of records.

**Action:** Increase the values of MAXROWS.

**0x1108E ( 69774) smERR_ABORT_NotFoundDataFileNodeByID Data file node not found
(ID : \<0%d\>)**

**Cause:** The data file node does not exist.

**Action:** Check the data file.

**0x1108F ( 69775) smERR_ABORT_CanStartARCH Archive thread cannot be started in
NO ARCHIVE mode**

**Cause:** The user tried to start an archive thread in NO ARCHIVE mode.

**Action:** Shut down, start up to the control phase and then execute the ALTER
DATABASE ARCHIVELOG statement.

**0x11090 ( 69776) smERR_ABORT_BackupDatafile The system failed to back up
\<0%s\> \<1%s\> file.**

**Cause:** An error occurred while copying a memory region or a data file of a
disk tablespace.

**Action:** Check the disk.

**0x11091 ( 69777) smERR_ABORT_DontNeedBackupTempTBS TEMP tablespace backup not
required.**

**Cause:** The user tried to back up the TEMP tablespace.

**Action:** Do not back up the TEMP tablespace. It is unnecessary because the
TEMP tablespace is initialized whenever the server starts.

**0x11093 ( 69779) smERR_ABORT_WrongStartupPhase Wrong startup phase. proceed to
the correct startup phase.**

**Cause:** Wrong startup phase. Proceed to the correct startup phase.

**Action:** Proceed to the correct startup phase.

**0x11094 ( 69780) smERR_ABORT_ErrArchiveLogMode Execution impossible in NO
ARCHIVE mode.**

**Cause:** Restart recovery cannot be performed in noarchivelog mode.

**Action:** To execute restart recovery, switch to archivelog mode.

**0x11095 ( 69781) smERR_ABORT_NeedMediaRecovery Start up in the CONTROL phase
and then execute a complete media recovery.**

**Cause:** The data file does not exist or is not valid.

**Action:** Run a complete media recovery in the CONTROL phase.

**0x11098 ( 69784) smERR_ABORT_BackupLogMode \<0%s\> cannot be executed in
NOARCHIVELOG mode.**

**Cause:** Restart recovery cannot be performed in noarchivelog mode.

**Action:** To execute restart recovery, switch to archivelog mode.

**0x11099 ( 69785) smERR_ABORT_UseFileInOtherTBS The file name [\<0%s\>] is in
use by another tablespace.**

**Cause:** The file name is in use by another tablespace.

**Action:** Select another name for the destination file.

**0x1109A ( 69786) smERR_ABORT_SelfCopy Unable to copy the file because the
source and destination are the same.**

**Cause:** The source and the destination path and filename are the same.

**Action:** Choose another destination path.

**0x1109B ( 69787) smERR_ABORT_NotSupport \<0%s\> is not supported yet.**

**Cause:** An attempt was made to execute an unsupported command.

**Action:** No action is necessary.

**0x110A1 ( 69793) smERR_ABORT_InvalidFileHdr Invalid data file header
{SID:\<0%d\> - FID:\<1%d\>}**

**Cause:** Invalid data file header

**Action:** Copy a valid data file to [MEM_DB_DIR].

**0x110A2 ( 69794) smERR_ABORT_NeedResetLogs Incomplete media recovery.
Resetlogs required.**

**Cause:** The media recovery attempt was incomplete because the resetlogs are
needed.

**Action:** Start up in the meta phase using the RESETLOGS option.

**0x110A4 ( 69796) smERR_ABORT_BACKUP_GOING Backup in progress. Wait until the
current backup is completed.**

**Cause:** It is impossible to switch logfiles while a backup is in progress.

**Action:** Wait until the current backup process is completed.

**0x110A5 ( 69797) smERR_ABORT_NotBeginBackup Tablespace : \<0%d\> BACKUP is not
in progress.**

**Cause:** The tablespace backup has not yet begun.

**Action:** Execute the following statement first: ALTER TABLESPACE
tablespacename BEGIN BACKUP.

**0x110A6 ( 69798) smERR_ABORT_NoActiveBeginBackup The backup process is not
currently underway.**

**Cause:** The backup process is not currently underway.

**Action:** Execute the following statement first: ALTER TABLESPACE
tablespacename BEGIN BACKUP.

**0x110A8 ( 69800) smERR_ABORT_NoExecutePermFile No execution permission for the
path [ \<0%s\> ].**

**Cause:** File execution is not permitted for this path.

**Action:** Add file execution permission for this path.

**0x110A9 ( 69801) smERR_ABORT_AlreadyBeginBackup The tablespace \<0%d\> backup
is in the BEGIN state.**

**Cause:** The tablespace backup has already begun.

**Action:** Alter the previously completed backup of the tablespace.

**0x110AA ( 69802) smERR_ABORT_AlreadyExistTableSpaceName Duplicate tablespace
names [ \<0%s\> ].**

**Cause:** Duplicate tablespace names.

**Action:** Check the tablespace names.

**0x110AC ( 69804) smERR_ABORT_TableLockUse X or S table lock is not allowed
while the TABLE_LOCK_ENABLE property is 0.**

**Cause:** The user tried to execute a DDL command when the TABLE_LOCK_ENABLE
property was 0.

**Action:** Change the TABLE_LOCK_ENABLE value to 1.

**0x110AD ( 69805) smERR_ABORT_ActiveTransExits The alter system
TABLE_LOCK_ENABLE can't be executed when an active transaction exists.**

**Cause:** A transaction is still active.

**Action:** End all active transactions and try again.

**0x110AF ( 69807) smERR_ABORT_OSFileSizeLimit_ERROR The maximum file size of
the OS is less than the database file size that was specified in the CREATE
DATABASE statement ( \<0%lu\> MB ).**

**Cause:** The maximum file size of the OS is less than that specified in the
property.

**Action:** Increase the maximum file size of the OS.

**0x110B0 ( 69808) smERR_ABORT_GETLIMIT_ERROR Failed to invoke the getrlimit()
system function**

**Cause:** The system failed to map the log file.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x110B1 ( 69809) smERR_ABORT_CantAllocTrans Unable to allocate a nested
transaction object**

**Cause:** There is no free transaction object available.

**Action:** Wait until there is room for a free transaction object.

**0x110B2 ( 69810) smERR_ABORT_InvalidDB Database information is invalid.**

**Cause:** Database information is invalid.

**Action:** Check the error number from altibase_sm.log and contact Altibase's
Support Center (http://support.altibase.com/en/).

**0x110B3 ( 69811) smERR_ABORT_DIFFERENT_DB_FREE_PAGE_LIST_COUNT Different Page
List Count. The value of the PAGE_LIST_GROUP_COUNT property is different from
the one used when createdb was executed. ( current
PAGE_LIST_GROUP_COUNT:\<0%d\>, createdb's PAGE_LIST_GROUP_COUNT \<1%d\> )**

**Cause:** The value of the PAGE_LIST_GROUP_COUNT property is different from the
one used when createdb was executed.

**Action:** Set the PAGE_LIST_GROUP_COUNT value to exactly the same value
specified when the database was created.

**0x110B4 ( 69812) smERR_ABORT_DIFFERENT_DB_EXPAND_CHUNK_PAGE_COUNT Different
Expand Chunk Page Count. The value of the EXPAND_CHUNK_PAGE_COUNT property is
different from the one used when createdb was executed. ( current
EXPAND_CHUNK_PAGE_COUNT:\<0%d\>, createdb EXPAND_CHUNK_PAGE_COUNT \<1%d\> )**

**Cause:** The value of the EXPAND_CHUNK_PAGE_COUNT property is different from
the one used when createdb was executed.

**Action:** Set the EXPAND_CHUNK_PAGE_COUNT to exactly the same value specified
when the database was created.

**0x110B5 ( 69813) smERR_ABORT_TOO_MANY_PER_LIST_PAGE_COUNT_ERROR Too many pages
in per list page count. ( Change property values to meet the condition
EXPAND_CHUNK_PAGE_COUNT(\<0%lu\>) is greater than or equal to 2 \*
PER_LIST_DIST_PAGE_COUNT(\<1%lu\>) \* PAGE_LIST_GROUP_COUNT(\<2%lu\>). )**

**Cause:** An expand chunk must have enough pages to be distributed to all
database free page list at least twice. The user has specified property values
that does not satisfy this condition, EXPAND_CHUNK_PAGE_COUNT \<= 2 \*
PER_LIST_DIST_PAGE_COUNT \* PAGE_LIST_GROUP_COUNT.

**Action:** Change EXPAND_CHUNK_PAGE_COUNT or PER_LIST_DIST_PAGE_COUNT to meet
the condition EXPAND_CHUNK_PAGE_COUNT \<= 2 \* PER_LIST_DIST_PAGE_COUNT \*
PAGE_LIST_GROUP_COUNT.

**0x110B7 ( 69815) smERR_ABORT_InvalidUseResetLog There is no need to use
resetlog.**

**Cause:** There is no need to use resetlog.

**Action:** Do not use resetlog when not necessary.

**0x110BC ( 69820) smERR_ABORT_WaitLogFileOpen Unable to open log file\<%s\>.**

**Cause:** The system failed to open the log file.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com).

**0x110C1 ( 69825) smERR_ABORT_NotFoundDataFile The data file containing page
[\<0%d\>] does not exist. ( Tablespace - ID : \<1%d\>, Type : \<2%d\> )**

**Cause:** The data file does not exist.

**Action:** Verify that the data file exists.

**0x110C4 ( 69828) smERR_ABORT_CannotSpanTransByLobLocator LobLocator cannot
span the transaction \<0%d\>.**

**Cause:** The transaction pointed to by Loblocator has ended.

**Action:** No action is necessary.

**0x110C5 ( 69829) smERR_ABORT_LobCursorClosed LobCursor already closed \<0%d\>
,\<1%d\>.**

**Cause:** An attempt was made to use a lob cursor that was already closed.

**Action:** No action is necessary.

**0x110C6 ( 69830) smERR_ABORT_CanNotModifyLob Cannot modify a lob using a
read-only LobCursor.**

**Cause:** An attempt was made to modify a lob using a read-only lob cursor.

**Action:** No action is necessary.

**0x110C7 ( 69831) smERR_ABORT_MissMatchedLobTransID While copying a lob,
mismatched source lob \<0%d\> and destination lob \<1%d\> transaction ID were
found.**

**Cause:** An attempt was made to modify a lob using a read-only lob cursor.

**Action:** No action is necessary.

**0x110C8 ( 69832) smERR_ABORT_overflowLobCursorID Lob cursor ID overflow**

**Cause:** Too many lob cursors have been opened.

**Action:** Close the lob cursor.

**0x110C9 ( 69833) smERR_ABORT_PrePareWriteProtocol Lob write preparation
protocol error**

**Cause:** Before writing was completed, another attempt to write to the lob was
made.

**Action:** No action is necessary.

**0x110CA ( 69834) smERR_ABORT_FinishWriteProtocol Lob write finish protocol
error**

**Cause:** The lob could not be written to before writing was completed.

**Action:** No action is necessary.

**0x110CB ( 69835) smERR_ABORT_RangeError The lob operation range (\<0%d\> \~
\<1%d\>) is not in the target range (\<2%d\> \~ \<3%d\>)**

**Cause:** Lob write range error.

**Action:** No action is necessary.

**0x110CC ( 69836) smERR_ABORT_LobCursorTooOld The lob cursor is too old.**

**Cause:** Because another statement updated the same row, this lob cursor
became too old.

**Action:** Reopen the lob cursor.

**0x110CD ( 69837) smERR_ABORT_InvalidLobStartOffset Lob operation start offset
[\<0%d\>] \> current lob length [\<1%d\>]**

**Cause:** While preparing for writing, the operation start offset was found to
be greater than the current length of the lob.

**Action:** No action is necessary.

**0x110D0 ( 69840) smERR_ABORT_MaxLobErrorSize The lob size is bigger than the
maximum lob size**

**Cause:** The lob size is bigger than the maximum lob size.

**Action:** Ensure that the lob size is correct.

**0x110D1 ( 69841) smERR_ABORT_INVALIDE_LOB_CURSOR_MODE If the table cursor is
read-only, the lob cursor must also be read-only.**

**Cause:** The LOB cursor must be read-only if the table cursor is read-only.

**Action:** Verify that the LOB cursor is read-only.

**0x110D7 ( 69847) smERR_ABORT_INVALID_STARTUP_PHASE_NOT_CONTROL \<0%s\> is only
allowed during the control phase.**

**Cause:** The user tried to execute a statement which may only be executed in
the CONTROL phase.

**Action:** Shut down, start up to the CONTROL phase and try again.

**0x110D8 ( 69848) smERR_ABORT_CPATH_NOT_EXIST The checkpoint path '\<0%s\>'
does not exist.**

**Cause:** The user tried to use a checkpoint path that does not exist.

**Action:** Verify that the checkpoint path exists.

**0x110D9 ( 69849) smERR_ABORT_CPATH_NO_READ_PERMISSION The checkpoint path
'\<0%s\>' does not have READ permission.**

**Cause:** The user tried to use a checkpoint path that does not have READ
permission.

**Action:** Verify that the checkpoint path has READ permission.

**0x110DA ( 69850) smERR_ABORT_CPATH_NO_WRITE_PERMISSION The checkpoint path
'\<0%s\>' does not have WRITE permission.**

**Cause:** The user tried to use a checkpoint path that does not have WRITE
permission.

**Action:** Verify that the checkpoint path has WRITE permission.

**0x110DB ( 69851) smERR_ABORT_CPATH_NO_EXEC_PERMISSION The checkpoint path
'\<0%s\>' does not have EXECUTE permission.**

**Cause:** The user tried to use a checkpoint path that does not have EXECUTE
permission.

**Action:** Verify that the checkpoint path has EXECUTE permission.

**0x110DC ( 69852) smERR_ABORT_CPATH_NOT_A_DIRECTORY The checkpoint path
'\<0%s\>' is not a directory.**

**Cause:** The user tried to use a checkpoint path that is not a directory.

**Action:** Verify that the checkpoint path is a directory.

**0x110DD ( 69853) smERR_ABORT_CPATH_NODE_NOT_EXIST The checkpoint path node
'\<0%s\>' does not exist.**

**Cause:** The user tried to rename or drop a checkpoint path that does not
exist.

**Action:** Verify that the checkpoint path exists.

**0x110DE ( 69854) smERR_ABORT_UNABLE_TO_DROP_LAST_CPATH A tablespace needs at
least one checkpoint path. Unable to drop the checkpoint path '\<0%s\>'.**

**Cause:** The user tried to drop the only checkpoint path in the tablespace.

**Action:** Rename the checkpoint path instead of dropping it.

**0x110DF ( 69855) smERR_ABORT_CPATH_ALREADY_EXISTS The checkpoint path node
'\<0%s\>' already exists.**

**Cause:** The user tried to add a checkpoint path that already exists.

**Action:** Do not try to add a checkpoint path that already exists.

**0x110E0 ( 69856) smERR_ABORT_ALTER_TBS_AUTOEXTEND_ALREADY_SET The attribute of
AUTOEXTEND mode has already been set.**

**Cause:** The AUTOEXTEND mode has already been set.

**Action:** No action is necessary.

**0x110E1 ( 69857) smERR_ABORT_ALTER_TBS_NEXTSIZE_NOT_ALIGNED_TO_CHUNK_SIZE The
NEXT attribute must be a multiple of the expand chunk size ( \<0%lu\>K )**

**Cause:** The NEXT attribute must be a multiple of the expand chunk size. The
expand chunk size is calculated by EXPAND_CHUNK_PAGE_COUNT \* PAGE_SIZE

**Action:** Verify that the NEXT size is aligned to EXPAND_CHUNK_PAGE_COUNT \*
PAGE_SIZE.

**0x110E2 ( 69858) smERR_ABORT_ALTER_TBS_MAXSIZE_LESSTHAN_CURRENT_SIZE The
MAXSIZE attribute must be greater than or equal to the current size of the
tablespace ( \<0%lu\>K )**

**Cause:** The MAXSIZE attribute is less than the current size of the
tablespace.

**Action:** Verify that the MAXSIZE attribute is greater than or equal to the
current size of the tablespace.

**0x110E3 ( 69859) smERR_ABORT_ALTER_TBS_AT_DROPPED_TBS Unable to alter a
dropped tablespace**

**Cause:** The tablespace was dropped.

**Action:** Verify that the tablespace exists.

**0x110E4 ( 69860) smERR_ABORT_ALTER_TBS_AT_OFFLINE_TBS Unable to alter an
offline tablespace**

**Cause:** The tablespace is offline.

**Action:** Verify that the tablespace is online before attempting to alter it.

**0x110E5 ( 69861) smERR_ABORT_INVALID_CIMAGE_HEADER Invalid Checkpoint Image
Header {SID:\<0%d\> - PPID:\<1%d\> - FID:\<2%d\>}**

**Cause:** Invalid Checkpoint Image header.

**Action:** Copy a valid Checkpoint Image to [MEM_DB_DIR].

**0x110E6 ( 69862) smERR_ABORT_DefaultDBFileSizeNotAlignedToChunkSize The value
of the DEFAULT_MEM_DB_FILE_SIZE property must be a multiple of the expand chunk
size ( EXPAND_CHUNK_PAGE_COUNT \* PAGE_SIZE(32K) = \<0%lu\>K )**

**Cause:** The value of DEFAULT_MEM_DB_FILE_SIZE property is not a multiple of
the expand chunk size.

**Action:** Verify that the value of DEFAULT_MEM_DB_FILE_SIZE property is a
multiple of the expand chunk size.

**0x110E7 ( 69863) smERR_ABORT_CANNOT_ALTER_STATUS_OF_SYSTEM_TABLESPACE Unable
to change the system tablespace status to OFFLINE or ONLINE.**

**Cause:** It is impossible to alter the status of a system tablespace whose
type is SYSTEM, UNDO, or SYSTEM TEMP.

**Action:** Verify that the tablespace is not a system tablespace.

**0x110E8 ( 69864) smERR_ABORT_CANNOT_ALTER_AUTOEXTEND_DICTIONARY_TABLESPACE
Unable to alter the AUTOEXTEND mode of the dictionary tablespace.**

**Cause:** It is impossible to alter the AUTOEXTEND mode of the dictionary
tablespace.

**Action:** Verify that the tablespace is not the dictionary tablespace.

**0x110E9 ( 69865)
smERR_ABORT_ALTER_TBS_ONOFF_ALLOWED_ONLY_AT_META_SERVICE_PHASE ALTER TABLESPACE
ONLINE/OFFLINE execution is allowed only during the META/SERVICE phase.**

**Cause:** It is impossible to alter the status of a tablespace during the
PROCESS or CONTROL phases.

**Action:** Attempt this action during the META or SERVICE startup phases.

**0x110EA ( 69866) smERR_ABORT_SplitSizeNotAlignedToChunkSize The split size of
the memory checkpoint image file must be a multiple of the expand chunk size (
EXPAND_CHUNK_PAGE_COUNT \* PAGE_SIZE(32K) = \<0%lu\>K )**

**Cause:** The split size of the memory checkpoint image file is not a multiple
of the expand chunk size.

**Action:** Verify that the split size of the memory checkpoint image file is a
multiple of the expand chunk size.

**0x110EB ( 69867) smERR_ABORT_INVALID_CIMAGE_FILESPEC_FORMAT Invalid Checkpoint
Image Filespec Format '\<0%s\>'.**

**Cause:** Invalid checkpoint image filespec format.

**Action:** Check checkpoint image filespec format.

**0x110EC ( 69868) smERR_ABORT_INPUT_UNSTABLE_CIMAGE The checkpoint image
'\<0%s\>' is not stable.**

**Cause:** The user tried to input a checkpoint image that is not stable.

**Action:** Check the loganchor file and input a stable checkpoint image.

**0x110ED ( 69869) smERR_ABORT_ERROR_MEDIA_RECOVERY_TYPE Execute incomplete
media recovery in the CONTROL phase, or execute a restart recovery.**

**Cause:** Either media recovery is complete or unnecessary.

**Action:** Restart normally.

**0x110EE ( 69870) smERR_ABORT_TBSInitSizeNotAlignedToChunkSize The initial size
of the tablespace must be a multiple of the expand chunk size (
EXPAND_CHUNK_PAGE_COUNT \* PAGE_SIZE(32K) = \<0%lu\>K )**

**Cause:** The initial size of the tablespace is not a multiple of the expand
chunk size.

**Action:** Verify that the initial size of the tablespace is a multiple of the
expand chunk size.

**0x110EF ( 69871) smERR_ABORT_UNABLE_TO_EXTEND_CHUNK_WHEN_AUTO_EXTEND_OFF
Unable to extend the tablespace(\<0%s\>) when AUTOEXTEND mode is OFF**

**Cause:** The user tried to extend the tablespace when the AUTOEXTEND mode of
the tablespace was OFF.

**Action:** Use the ALTER TABLESPACE AUTOEXTEND ON statement to set AUTOEXTEND
mode to ON.

**0x110F0 ( 69872) smERR_ABORT_UNABLE_TO_EXTEND_CHUNK_MORE_THAN_MEM_MAX_DB_SIZE
Unable to extend the tablespace (\<0%s\>) because the database would be larger
than MEM_MAX_DB_SIZE(\<1%lu\>K).**

**Cause:** The user tried to extend the tablespace, but the size of the database
would be larger than MEM_MAX_DB_SIZE.

**Action:** Enlarge MEM_MAX_DB_SIZE or drop another tablespace.

**0x110F1 ( 69873) smERR_ABORT_UNABLE_TO_EXTEND_CHUNK_MORE_THAN_TBS_MAXSIZE
Unable to extend the tablespace (\<0%s\>) because the current size of the
tablespace (\<1%lu\>K) would be larger than MAXSIZE (\<2%lu\>K) of the
tablespace.**

**Cause:** The user tried to extend the tablespace, but the size of the
tablespace would exceed MAXSIZE for the tablespace.

**Action:** Use the ALTER TABLESPACE AUTOEXTEND ON MAXSIZE statement to change
the MAXSIZE for the tablespace.

**0x110F3 ( 69875) smERR_ABORT_PAGE_RANGE_ERROR Invalid Page Range. Valid Page
Range = 1 \~ \<0%d\>.**

**Cause:** The page range is invalid.

**Action:** Specify a valid page range.

**0x110F4 ( 69876) smERR_ABORT_TABLESPACE_IS_ALREADY_ONLINE The tablespace is
already in ONLINE mode**

**Cause:** The user tried to execute “ALTER TABLESPACE ONLINE” on a tablespace
that is already in ONLINE mode.

**Action:** Verify that the table space is not in ONLINE mode before attempting
this action.

**0x110F5 ( 69877) smERR_ABORT_TABLESPACE_IS_ALREADY_OFFLINE The tablespace is
already in OFFLINE mode**

**Cause:** The user tried to execute “ALTER TABLESPACE OFFLINE” on a tablespace
that is already in OFFLINE mode.

**Action:** Verify that the table space is not in OFFLINE mode before attempting
this action.

**0x110F6 ( 69878) smERR_ABORT_DUMP_EMPTY_OBJECT Empty dump object.**

**Cause:** You did not specify a dump object for the dump table.

**Action:** Verify that you have set a dump object for the dump table.

**0x110F8 ( 69880) smERR_ABORT_CannotDiscardTableSpace Unable to change the
tablespace to discard mode.**

**Cause:** It is impossible to change the tablespace to discard mode because its
type is SYSTEM, UNDO or SYSTEM_TEMP.

**Action:** Verify that the tablespace is not a system tablespace.

**0x110F9 ( 69881) smERR_ABORT_MEDIA_RECOVERY_IS_NOT_SUPPORT_SHARED_MEMORY Media
Recovery is not supported by the shared memory version.**

**Cause:** ALTER DATABASE RECOVER DATABASE is not supported for shared memory
versions.

**Action:** Verify that the SHM_DB_KEY property is set to zero.

**0x110FA ( 69882) smERR_ABORT_CannotAllocLogBufferMemory Cannot allocate memory
for the volatile log buffer.**

**Cause:** Insufficient memory.

**Action:** Retry this statement in autocommit mode.

**0x110FB ( 69883) smERR_ABORT_UNABLE_TO_USE_OFFLINE_TBS Unable to use an
offline tablespace. (NAME=\<0%s\>)**

**Cause:** The user tried to use an offline tablespace.

**Action:** Execute the ALTER TABLESPACE ONLINE statement and try again.

**0x110FC ( 69884) smERR_ABORT_UNABLE_TO_USE_DISCARDED_TBS Unable to use a
discarded tablespace. (NAME=\<0%s\>)**

**Cause:** The user tried to use a discarded tablespace.

**Action:** Execute the DROP TABLESPACE statement and recreate the tablespace.

**0x110FD ( 69885) smERR_ABORT_TBS_ALREADY_DISCARDED The tablespace has already
been discarded.**

**Cause:** The user tried to discard a tablespace that has already been
discarded.

**Action:** Execute the DROP TABLESPACE statement and recreate the tablespace.

**0x110FE ( 69886) smERR_ABORT_AUTOEXT_ON_UNALLOWED_FOR_USED_UP_FILE The
autoextend attribute of a data file that has been used up cannot be switched
on.**

**Cause:** The user tried to turn on the autoextend attribute for a data file
that has been used up.

**Action:** Try again with a current or unused data file.

**0x110FF ( 69887) smERR_ABORT_StmtMaxDepthLevel The statement depth has reached
the maximum level.**

**Cause:** The depth of the statement is greater than 255.

**Action:** Investigate the reason for the statement depth.

**0x11100 ( 69888)
smERR_ABORT_UNABLE_TO_EXTEND_CHUNK_MORE_THAN_VOLATILE_MAX_DB_SIZE Unable to
extend the tablespace (\<0%s\>) because the database would be larger than
VOLATILE_MAX_DB_SIZE (\<1%lu\>K).**

**Cause:** The user tried to extend the tablespace, but the size of the database
would be larger than VOLATILE_MAX_DB_SIZE.

**Action:** Increase the VOLATILE_MAX_DB_SIZE value or drop another tablespace.

**0x11101 ( 69889) smERR_ABORT_UNABLE_TO_BACKUP_FOR_VOLATILE_TABLESPACE Unable
to back up a volatile tablespace.**

**Cause:** The user tried to back up a volatile tablespace.

**Action:** It is not necessary to back up volatile tablespaces.

**0x11102 ( 69890) smERR_ABORT_UNABLE_TO_ALTER_ONLINE_CUZ_MEM_MAX_DB_SIZE Unable
to change the tablespace status (NAME=\<0%s\>, SIZE=\<1%lu\>K) to ONLINE because
the database would be larger than MEM_MAX_DB_SIZE (\<2%lu\>K). ( Current
Database Size = \<3%lu\>K )**

**Cause:** The user tried to bring the tablespace online, but the size of the
database would be larger than MEM_MAX_DB_SIZE.

**Action:** Increase the MEM_MAX_DB_SIZE value or bring another tablespace
offline, and try again.

**0x11103 ( 69891) smERR_ABORT_UNABLE_TO_CREATE_CUZ_MEM_MAX_DB_SIZE Unable to
create the tablespace (NAME=\<0%s\>, SIZE=\<1%lu\>K) because the database would
be larger than MEM_MAX_DB_SIZE (\<2%lu\>K). ( Current Database Size = \<3%lu\>K
)**

**Cause:** The user tried to create a tablespace, but the size of the database
would be larger than MEM_MAX_DB_SIZE.

**Action:** Increase the MEM_MAX_DB_SIZE value or bring another tablespace
offline.

**0x11104 ( 69892) smERR_ABORT_FileNameIsNullString The length of the filename
is zero.**

**Cause:** The filename is an empty string.

**Action:** Enter a valid filename for the file to be created.

**0x11105 ( 69893) smERR_ABORT_InvalidExtendFileSizeOSLimit The data file cannot
be extended because the requested size is bigger than the OS file limit size. (
Request Size : \<0%lu\> pages, OS File Limit Size : \<1%lu\> pages )**

**Cause:** The resize (extend) value is too big.

**Action:** Use a suitable value for the resize action.

**0x11107 ( 69895) smERR_ABORT_UNABLE_TO_CREATE_CUZ_VOL_MAX_DB_SIZE Unable to
create the tablespace (NAME=\<0%s\>, SIZE=\<1%lu\>K) because the database would
be larger than VOLATILE_MAX_DB_SIZE(\<2%lu\>K). ( Current Total Volatile
Tablespace Size = \<3%lu\>K )**

**Cause:** The user tried to create the tablespace, but the total size of the
volatile tablespace would be larger than VOLATILE_MAX_DB_SIZE.

**Action:** Increase the VOLATILE_MAX_DB_SIZE value or drop another volatile
tablespace.

**0x11108 ( 69896) smERR_ABORT_LogFileSizeNotAlignedToDirectIOPageSize The size
of the logfile is not aligned to DIRECT_IO_PAGE_SIZE.**

**Cause:** The size of the logfile is not an exact multiple of
DIRECT_IO_PAGE_SIZE.

**Action:** Verify that the size of the logfile is an exact multiple of
DIRECT_IO_PAGE_SIZE.

**0x11109 ( 69897) smERR_ABORT_MAX_AGER_COUNT_LT_MIN_AGER_COUNT
MAX_LOGICAL_AGER_COUNT property is less than MIN_LOGICAL_AGER_COUNT property. (
MAX_LOGICAL_AGER_COUNT=\<0%d\>, MIN_LOGICAL_AGER_COUNT=\<1%d\> )**

**Cause:** The user has specified a maximum number of logical agers that is less
than the minimum number of logical agers.

**Action:** Verify that the MAX_LOGICAL_AGER_COUNT value is greater than or
equal to the MIN_LOGICAL_AGER_COUNT value.

**0x1110A ( 69898) smERR_ABORT_AGER_COUNT_OUT_OF_MAX_COUNT The
LOGICAL_AGER_COUNT property value is greater than the MAX_LOGICAL_AGER_COUNT
property value. ( LOGICAL_AGER_COUNT=\<0%d\>, MAX_LOGICAL_AGER_COUNT=\<1%d\> )**

**Cause:** The LOGICAL_AGER_COUNT property value is greater than the
MAX_LOGICAL_AGER_COUNT property value.

**Action:** Verify the LOGICAL_AGER_COUNT property value is less than or equal
to the MAX_LOGICAL_AGER_COUNT property value.

**0x1110B ( 69899) smERR_ABORT_AGER_COUNT_OUT_OF_MIN_COUNT The
LOGICAL_AGER_COUNT property value is less than the MIN_LOGICAL_AGER_COUNT
property value. ( LOGICAL_AGER_COUNT=\<0%d\>, MIN_LOGICAL_AGER_COUNT=\<1%d\> )**

**Cause:** The LOGICAL_AGER_COUNT property value is less than the
MIN_LOGICAL_AGER_COUNT property value.

**Action:** Verify the LOGICAL_AGER_COUNT property value is greater than or
equal to the MIN_LOGICAL_AGER_COUNT property value.

**0x1110D ( 69901) smERR_ABORT_NOT_NULL_VIOLATION Unable to add NOT NULL
constraint to the specified column because it already contains null values**

**Cause:** The NOT NULL constraint cannot be added to the specified column
because it already contains null values.

**Action:** Remove all null values from the column prior to adding the NOT NULL
constraint.

**0x11110 ( 69904) smERR_ABORT_INCONSISTENT_INDEX The index is inconsistent**

**Cause:** The index is inconsistent.

**Action:** Check index consistency and rebuild the index.

**0x11112 ( 69906) smERR_ABORT_Not_Support_MMap The OS does not support mmap.**

**Cause:** The OS does not support mmap.

**Action:** Check LOG_BUFFER_TYPE.

**0x11114 ( 69908) smERR_ABORT_INVALID_DUMP_OBJECT Invalid dump object**

**Cause:** The object is not valid for a dump table.

**Action:** Verify that a valid dump object has been used for the dump table.

**0x11115 ( 69909) smERR_ABORT_TBS_ATTR_FLAG_ALREADY_SET The tablespace
attribute has already been set to the given value.**

**Cause:** The LOG COMPRESS attribute already corresponds to the given value.

**Action:** No action is necessary.

**0x11116 ( 69910) smERR_ABORT_TABLE_ATTR_FLAG_ALREADY_SET The table attribute
has already been set to the given value.**

**Cause:** The attribute is already the same as the given value.

**Action:** No action is necessary.

**0x11117 ( 69911) smERR_ABORT_UNABLE_TO_COMPRESS_VOLATILE_TBS_LOG Log
compression is not supported for volatile tablespaces.**

**Cause:** The user tried to compress a volatile tablespace log.

**Action:** No action is necessary.

**0x11118 ( 69912) smERR_ABORT_TOO_MANY_UPDATE_LOG The update log size
'\<0%lu\>' is bigger than TRX_UPDATE_MAX_LOGSIZE '\<1%lu\>'**

**Cause:** The update log size '\<%lu\>' is bigger than TRX_UPDATE_MAX_LOGSIZE
'\<%lu\>'

**Action:** TRX_UPDATE_MAX_LOGSIZE is too small.

**0x1111A ( 69914) smERR_ABORT_Invalid_DataFile_Create_LSN The create LSN
(\<0%u\>, \<1%u\>, \<2%u\>) of the data file (\<3%s\>) is bigger than the
restart redo LSN (\<4%u\>, \<5%u\>, \<6%u\>).**

**Cause:** The data file is invalid.

**Action:** Verify that the data file was backed up correctly.

**0x1111F ( 69919) smERR_ABORT_PageCorrupted A page is corrupt. ( Current Space
ID : \<0%d\>, Current Page ID : \<1%d\> )**

**Cause:** The page was not written completely.

**Action:** Recover the tablespace that contains the corrupt page with backup
and recovery utilities.

**0x11120 ( 69920) smERR_ABORT_INCONSISTENT_TABLE The table is inconsistent.**

**Cause:** The table is inconsistent.

**Action:** Recreate the table.

**0x11121 ( 69921) smERR_ABORT_CANNOT_ADD_DataFile It is impossible to add any
more data files.**

**Cause:** The number of files has reached the limit.

**Action:** Refrain from attempting this action.

**0x11122 ( 69922) smERR_ABORT_CANT_SHRINK_BELOW_HWM It is impossible to shrink
this file. ( Request Size : \<0%lu\> pages, Used File Size : \<1%lu\> pages )**

**Cause:** An attempt was made to shrink the file below HWM.

**Action:** Refrain from attempting this action.

**0x11123 ( 69923) smERR_ABORT_NOT_ENOUGH_SPACE The tablespace does not have
enough free space ( TBS Name :\<0%s\> ).**

**Cause:** The tablespace does not have enough free space.

**Action:** Add a new data file.

**0x11124 ( 69924) smERR_ABORT_FILE_IS_TOO_SMALL Not even one extent can be
created. ( Request Init Size : \<0%lu\> pages, Minimum File Size : \<1%lu\>
pages )**

**Cause:** The file is too small for even one extent.

**Action:** Retry with a greater size.

**0x11126 ( 69926) smERR_ABORT_SegmentExceedMaxExtents Max no. of extents
reached for segment ( TBSID : \<0%u\>, SEGHDR_FID : \<1%u\>, SEGHDR_FPID :
\<2%u\>, CurrExtCnt : \<3%u\>, MaxExtCnt : \<4%u\> ).**

**Cause:** The maximum number of extents has been reached for this segment.

**Action:** Increase the MAXEXTENTS value for this segment.

**0x11127 ( 69927) smERR_ABORT_NotExistSegment The segment does not exist or is
not in a valid state.**

**Cause:** The segment does not exist or is not in a valid state.

**Action:** Verify that the segment object is valid.

**0x11128 ( 69928) smERR_ABORT_SHRINK_SIZE_IS_TOO_SMALL The requested size of
the data file is less than the minimum file size. ( Request Size : \<0%lu\>
pages, Minimum File Size : \<1%lu\> pages )**

**Cause:** The file is too small for even one extent.

**Action:** Increase the file size.

**0x11129 ( 69929) smERR_ABORT_TOO_MANY_DATA_FILE The Tablespace has too many
data files.**

**Cause:** An attempt was made to create the Tablespace with too many data
files.

**Action:** Reduce the number of data files in the Tablespace to 1024 or less.

**0x1112D ( 69933) smERR_ABORT_smiInvalidFlusherID The flusher ID [\<0%d\>] must
be less than \<1%d\>.**

**Cause:** The flusher ID is invalid.

**Action:** Check the flusher count.

**0x1112E ( 69934) smERR_ABORT_sdbFlusherNotStarted The flusher [\<0%d\>] was
not started.**

**Cause:** The flusher was not started.

**Action:** Check the flusher status.

**0x1112F ( 69935) smERR_ABORT_sdbFlusherRunning The flusher [\<0%d\>] is
already running.**

**Cause:** The flusher cannot be started because it is already running.

**Action:** Check the flusher status.

**0x11130 ( 69936) smERR_ABORT_ILLEGAL_REQ_BUFFER_SIZE BUFFER_AREA_SIZE has to
be larger than current BUFFER_AREA_SIZE.**

**Cause:** The current version of Altibase doesn't support decreasing the buffer
area size.

**Action:** If you want to decrease the buffer area size, first shut down
Altibase and set a suitable value for the property. Then start Altibase again.

**0x11132 ( 69938) smERR_ABORT_INVALID_BUFFER_EXPAND_SIZE \|BUFFER_AREA_SIZE -
current BUFFER_AREA_SIZE\| must be larger than BUFFER_AREA_CHUNK_SIZE.**

**Cause:** \|BUFFER_AREA_SIZE - current BUFFER_AREA_SIZE\| is smaller than
BUFFER_AREA_CHUNK_SIZE.

**Action:** Enter another value for BUFFER_AREA_SIZE.

**0x11134 ( 69940) smERR_ABORT_Not_Support_function Altibase doesn't support
this function**

**Cause:** Altibase doesn't support this function.

**Action:** Check the manual.

**0x11135 ( 69941) smERR_ABORT_AlreadyExistLogFile The Log file already
exists.**

**Cause:** The Log file already exists.

**Action:** Confirm that you have executed destroydb.

**0x11136 ( 69942) smERR_ABORT_AlreadyExistLogAnchorFile The LogAnchor file
already exists.**

**Cause:** The LogAnchor file already exists.

**Action:** Confirm that you have executed destroydb.

**0x11137 ( 69943) smERR_ABORT_UseFileInTheTBS The file name [\<0%s\>] is in use
by the tablespace [\<1%s\>].**

**Cause:** The file name is in use by a tablespace.

**Action:** Choose another destination file name.

**0x11138 ( 69944) smERR_ABORT_BUFFER_MANAGER_BUSY The buffer area size cannot
be changed because of transactions.**

**Cause:** There are currently executing transactions.

**Action:** Try again when the system is not busy.

**0x11139 ( 69945) smERR_ABORT_CannotCreateSegInUndoTBS Cannot create segments
in an undo tablespace.**

**Cause:** Cannot create a table or index in an undo tablespace.

**Action:** Use another tablespace.

**0x1113B ( 69947) smERR_ABORT_Datafile_Header_Read_Failure File header not read
from database file '\<0%s\>'.**

**Cause:** The DBFile was not found, or the DBFileHdr value in the DBFile could
not be read.

**Action:** Check the DBFile.

**0x1113C ( 69948) smERR_ABORT_Datafile_Header_Write_Failure File header of
database file '\<0%s\>' not written.**

**Cause:** The DBFile was not found, or the DBFileHdr was not written in the
DBFile.

**Action:** Check the DBFile.

**0x1113D ( 69949) smERR_ABORT_NotFoundDataFileByPath Data file not found
'\<0%s\>'.**

**Cause:** Data file not found.

**Action:** Check the data file.

**0x1113E ( 69950) smERR_ABORT_EXTENT_SIZE_IS_TOO_SMALL An extent size for an
auto segment space managed tablespace must have at least 5 blocks.**

**Cause:** The user tried to create a tablespace with an invalid (too small)
extent size.

**Action:** Create a tablespace with a valid (greater than PAGESIZE \* 5) extent
size.

**0x11140 ( 69952) smERR_ABORT_LogSizeExceedLogFileSize The size of a log record
exceeds the logfile size ( logfile size \<0%d\> bytes, log record size \<1%d\>
bytes ).**

**Cause:** The size of a log record exceeds the logfile size.

**Action:** Change the property to a suitable value and recreate the database.

**0x11141 ( 69953) smERR_ABORT_Invalid_Mtx_LatchStack_Size The mini
transaction's latchstack size is not 1.**

**Cause:** Internal mtx misuse.

**Action:** Send a bug report to the vendor.

**0x11145 ( 69957) smERR_ABORT_AllFlushersStopped You cannot run the DCL command
because all flushers are stopped.**

**Cause:** All flushers are stopped.

**Action:** Start some flushers.

**0x11146 ( 69958) smERR_ABORT_DW_FILE_NOT_FOUND There is no double write
file.**

**Cause:** The DOUBLE_WRITE_DIRECTORY property has been modified.

**Action:** Check your properties.

**0x11147 ( 69959) smERR_ABORT_INVALID_LOGFILE Invalid logfile ( File Name :
\<0%s\> ).**

**Cause:** The log file is invalid.

**Action:** Check the logfile.

**0x11149 ( 69961) smERR_ABORT_WrongVerifyDiskIndexCount The number of
\__SM_VERIFY_DISK_INDEX_NAME(\<0%d\>) is not
\__SM_VERIFY_DISK_INDEX_COUNT(\<1%d\>).**

**Cause:** The number of \__SM_VERIFY_DISK_INDEX_NAME is different from
\__SM_VERIFY_DISK_INDEX_COUNT.

**Action:** Check \__SM_VERIFY_DISK_INDEX_COUNT and the number of
\__SM_VERIFY_DISK_INDEX_NAME.

**0x1114A ( 69962) smERR_ABORT_TX_ALLOC Failed to allocate a transaction.**

**Cause:** Allocating the transaction took too long.

**Action:** Check the transaction table status.

**0x1114C ( 69964) smERR_ABORT_DROP_CPATH_NOT_YET_MOVED_CIMG_IN_CPATH The
checkpoint image '\<0%s\>' has not yet been moved from the checkpoint path
'\<1%s\>'.**

**Cause:** An attempt was made to drop a checkpoint path that contains a
checkpoint image.

**Action:** Move the checkpoint image to another checkpoint path.

**0x1114D ( 69965) smERR_ABORT_DML_AFTER_INSERT_APPEND This DML operation is not
permitted.**

**Cause:** An attempt was made to execute DML operations during Direct-Path
INSERT.

**Action:** Execute DML operations after Direct-Path INSERT is Terminated.

**0x1114E ( 69966) smERR_ABORT_NOT_FOUND_LOGFILE No log files could be found in
the '\<0%s\>' directory.**

**Cause:** The specified directory did not contain any log files.

**Action:** Check the specified directory.

**0x1114F ( 69967) smERR_ABORT_EXIST_ACTIVE_TRANS_IN_RECOV Recovery failure.
Active transactions exist.**

**Cause:** All transactions that were commenced during the startup phase must be
completed before the recovery phase.

**Action:** Check for and end all active transactions during the control phase.

**0x11150 ( 69968) smERR_ABORT_InitSizeExceedMaxSize The INITSIZE of the data
file exceeds the MAXSIZE of the data file.**

**Cause:** The INITSIZE of the data file exceeds the MAXSIZE of the data file.

**Action:** Check the INITSIZE and MAXSIZE of the data file.

**0x11151 ( 69969) smERR_ABORT_InitSizePropExceedMaxSizeProp The value of the
\<0%s\> property exceeds the value of the \<1%s\> property.**

**Cause:** The value of the INITSIZE property exceeds the value of the MAXSIZE
property.

**Action:** Check the properties pertaining to the size of the data file.

**0x11152 ( 69970) smERR_ABORT_MaxSizePropExceedOSLimit The value of the \<0%s\>
property exceeds the OS file size limit. ( Max Size Property : \<1%lu\>, OS file
size limit : \<2%lu\> )**

**Cause:** The MAXSIZE property of the data file exceeds the OS file size limit.

**Action:** Set the MAXSIZE of the data file appropriately.

**0x11153 ( 69971) smERR_ABORT_InitSizeExceedOSLimit The INITSIZE of the data
file exceeds the OS file size limit. ( Request Init Size : \<0%lu\> pages, OS
file size limit : \<1%lu\> pages )**

**Cause:** The MAXSIZE of the data file exceeds the OS file size limit.

**Action:** Set the MAXSIZE of the data file appropriately.

**0x11154 ( 69972) smERR_ABORT_MaxSizeExceedOSLimit The MAXSIZE of the data file
exceeds the OS file size limit. ( Request Max Size : \<0%lu\> pages, OS file
size limit : \<1%lu\> pages )**

**Cause:** The MAXSIZE of the data file exceeds the OS file size limit.

**Action:** Set the MAXSIZE of the data file appropriately.

**0x11155 ( 69973) smERR_ABORT_InvalidFileSizeOnLogAnchor The file size reported
for the file \<0%s\> is invalid. ( Init Size : \<1%lu\> pages, Current Size :
\<2%lu\> pages, Max Size : \<3%lu\> pages, Maximum File Size \<4%lu\> pages )**

**Cause:** Invalid information about the size of a data file is stored in a
loganchor file.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x11156 ( 69974) smERR_ABORT_InvalidExtendFileSizeMaxSize The requested size
of the data file exceeds the MAXSIZE for the data file. ( Requested Size :
\<0%lu\> pages, Max Size : \<1%lu\> pages )**

**Cause:** The specified file size value is too big.

**Action:** Set the value for the file size appropriately.

**0x11157 ( 69975) smERR_ABORT_WRONG_ENTRY_ID
\__MANUAL_BINDING_TRANSACTION_SEGMENT_BY_ENTRY_ID '\<0%d\>' exceeds the total
entry count '\<1%d\>'.**

**Cause:** The entry ID specified in
\__MANUAL_BINDING_TRANSACTION_SEGMENT_BY_ENTRY_ID is too high.

**Action:** Set the value of \__MANUAL_BINDING_TRANSACTION_SEGMENT_BY_ENTRY_ID
property to a value less than the total entry count.

**0x11158 ( 69976) smERR_ABORT_NOT_AVAILABLE_ENTRY
\__MANUAL_BINDING_TRANSACTION_SEGMENT_BY_ENTRY_ID '\<0%d\>' has already been
bound in another transaction.**

**Cause:** The entry ID specified in
\__MANUAL_BINDING_TRANSACTION_SEGMENT_BY_ENTRY_ID has already been bound in
another transaction.

**Action:** Retry after a moment, or set the
\__MANUAL_BINDING_TRANSACTION_SEGMENT_BY_ENTRY_ID property to another value and
try again.

**0x11159 ( 69977) smERR_ABORT_DATA_PORT_INTERNAL_ERROR Internal import/export
error.**

**Cause:** Unexpected internal error.

**Action:** Notify Altibase technical support staff.

**0x1115A ( 69978) smERR_ABORT_CORRUPTED_BLOCK A block is corrupt. ( BlockID
\<0%d\> ).**

**Cause:** A block appears to be corrupt.

**Action:** Check the DataPort file.

**0x1115B ( 69979) smERR_ABORT_VERSION_NOT_SUPPORTED The DataPort file version
is not supported. ( \<0%d\> \> \<1%d\> ).**

**Cause:** The version of the DataPort file is too high.

**Action:** Check the version of the database and the DataPort file.

**0x1115C ( 69980) smERR_ABORT_CANT_OPEN_FILE Cannot find the file. ( '\<0%s\>'
).**

**Cause:** The DataPort file does not exist.

**Action:** Check the DataPort file name and try again.

**0x1115D ( 69981) smERR_ABORT_COLUMN_CHAINING_THRESHOLD_LAGER_THAN_BLOCK_SIZE
The column-chaining threshold is greater than the maximum size(=BlockSize/2)(
ColumnChainingThreshold:\<0%d\>, BlockSize:\<1%d\> ).**

**Cause:** The column-chaining threshold is greater than the maximum
size(=BlockSize/2).

**Action:** Set the column-chaining threshold to a value less than
(BlockSize/2).

**0x1115E ( 69982) smERR_ABORT_CORRUPTED_HEADER The DataPort file header is
corrupt.**

**Cause:** The Dataport file header appears to be corrupt.

**Action:** Check the DataPort file.

**0x1115F ( 69983) smERR_ABORT_CheckpointPathIsNullString The length of the
checkpoint path is zero.**

**Cause:** The value specified for the checkpoint path is a null string.

**Action:** Provide a valid checkpoint path to be created.

**0x11160 ( 69984) smERR_ABORT_InvalidCheckpointPathABS The checkpoint path is
not an absolute path.**

**Cause:** The checkpoint path is not an absolute path.

**Action:** Check the ALTIBASE_HOME environment variable for this account.

**0x11161 ( 69985) smERR_ABORT_InvalidCheckpointPathKeyWord The checkpoint path
contains special keywords or system reserved keywords.**

**Cause:** The checkpoint path contains special keywords or system reserved
keywords.

**Action:** Set the checkpoint path appropriately.

**0x11162 ( 69986) smERR_ABORT_TooLongCheckpointPath The checkpoint path is too
long \<0%s\> \<1%s\>.**

**Cause:** The checkpoint path is too long.

**Action:** Specify a checkpoint path that is within the allowable length for a
checkpoint path.

**0x11163 ( 69987) smERR_ABORT_TooLongFilePath The total length of the file path
and name is too long \<0%s\> \<1%s\>.**

**Cause:** The total length of the file path and name is too long.

**Action:** Specify a file path and/or filename such that the total length of
the file path and name is within the allowable length.

**0x11164 ( 69988) smERR_ABORT_AlreadyExistDBFiles The data file(s) already
exists.**

**Cause:** The data file(s) already exists.

**Action:** Ensure that you have executed destroydb and try again.

**0x11165 ( 69989) smERR_ABORT_INTERNAL The storage manager experienced an
internal server error.**

**Cause:** Internal server error.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x11166 ( 69990) smERR_ABORT_TRANSACTION_TABLE_SIZE_IS_NOT_POWER_OF_TWO
TRANSACTION_TABLE_SIZE ['\<0%d\>'] is not a power of two.**

**Cause:** The value of the TRANSACTION_TABLE_SIZE property is not a power of
two(=2\^n).

**Action:** Check the altibase.properties file and set the value of
TRANSACTION_TABLE_SIZE to a power of two (2\^n).

**0x11167 ( 69991) smERR_ABORT_DB_FILE_SIZE_EXCEEDS_LIMIT The size of the DB
file(\<0%s\>) exceeds the size specified in the MEM_MAX_DB_SIZE property.**

**Cause:** The MEM_MAX_DB_SIZE property is set to a value that is less than the
current size of the DB file.

**Action:** Check the altibase.properties file and increase the value of the
MEM_MAX_DB_SIZE property

**0x11168 ( 69992) smERR_ABORT_LOG_FILE_MISSING Non-continuous log file numbers.
( \<0%s\> ).**

**Cause:** Either the server failed to remove an old log file, or a current log
file has been lost for some unknown reason.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x11169 ( 69993) smERR_ABORT_FAILURE_DURABILITY_AT_STARTUP Restart recovery
aborted to protect database durability.**

**Cause:** A log file has been lost. If restart recovery continues, DB
durability and DB objects may be broken.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x1116A ( 69994) smERR_ABORT_FAILURE_DRDB_WAL_AT_STARTUP Restart recovery
aborted due to Write-Ahead-Logging failure.**

**Cause:** The server cannot find a log file that is necessary for restoring a
DRDB object. If

restart recovery continues, DB consistency may be broken.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x1116B ( 69995) smERR_ABORT_FAILURE_MRDB_WAL_AT_STARTUP Restart recovery
aborted due to Write-Ahead-Logging failure.**

**Cause:** The server cannot find a log file that is necessary for restoring an
MRDB object. If restart recovery continues, DB consistency may be broken.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x1116C ( 69996) smERR_ABORT_INCONSISTENT_DB Access blocked to prevent DB
inconsistency from worsening.**

**Cause:** A SQL statement attempted to access a portion of the DB that is
already inconsistent.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x1116D ( 69997) smERR_ABORT_INCONSISTENT_PAGE A page is inconsistent. (
Current Space ID : \<0%d\>, Current Page ID : \<1%d\> )**

**Cause:** The page is not consistent.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x1116E ( 69998) smERR_ABORT_ERR_INCONSISTENT_DB_AND_LOG_BUFFER_TYPE Could not
perform emergency startup due to current LOG_BUFFER_TYPE setting.**

**Cause:** The current log buffer type setting (=0) forcefully records all logs,
including emergency logs. However, emergency logs must not be recorded.

**Action:** Set the value of the LOG_BUFFER_TYPE property to 1.

**0x1116F ( 69999) smERR_ABORT_LOGFILE_TOO_BIG_WITH_DIRECT_IO The logfile is too
big. ( \<0%d\> \> \<1%d\> )**

**Cause:** The size of the logfile exceeds the DIRECT I/O limitation.

**Action:** Verify that the logfile is smaller than the DIRECT I/O limitation,
or set the value of the LOG_IO_TYPE property to 0.

**0x11171 ( 70001) smERR_ABORT_InvalidChangeTrackingFile The change-tracking
file is not valid. ( File Name :\<0%s\> )**

**Cause:** The file was corrupted by an abnormal shutdown or some other
unexpected activity.

**Action:** Disable and re-enable the change-tracking manger.

**0x11172 ( 70002) smERR_ABORT_ChangeTrackingState Unexpected change-tracking
manager state.**

**Cause:** The change-tracking manager is already enabled or disabled.

**Action:** Check the state of the change-tracking manager.

**0x11173 ( 70003) smERR_ABORT_ErrUntilTag Can\`t perform media recovery at
point of backup tag. ( Backup Tag Name :\<0%s\> )**

**Cause:** An attempt was made to restore the database using an invalid backup
tag.

**Action:** Restore the database using the correct backup tag.

**0x11174 ( 70004) smERR_ABORT_InvalidBackupInfoFile The backup information file
is not valid. ( File Name :\<0%s\> )**

**Cause:** The file was corrupted by an abnormal shutdown or some other
unexpected activity.

**Action:** Restore the backup information file from a recent backup.

**0x11175 ( 70005) smERR_ABORT_InvalidRestoreTime Can\`t restore database to
specified point of time**

**Cause:** No backup file predating the specified time exists.

**Action:** Restore the database to a more recent point in time.

**0x11176 ( 70006) smERR_ABORT_NotDefinedIncrementalBackupPath No incremental
backup path defined**

**Cause:** No incremental backup path has been defined.

**Action:** Specify an incremental backup directory.

**0x11177 ( 70007) smERR_ABORT_AlreadyExistIncrementalBackupPath Incremental
backup path already exists (Dir Name :\<0%s\> )**

**Cause:** The incremental backup path already exists.

**Action:** Change the incremental backup directory, or wait and try incremental
backup again.

**0x11178 ( 70008) smERR_ABORT_BackupInfoState Unexpected Backup Information
Manager state**

**Cause:** The Backup Information Manager is already enabled or disabled.

**Action:** Check the state of the Backup Information Manager.

**0x11179 ( 70009) smERR_ABORT_AlreadyExistPath Directory already exists (Dir
Name :\<0%s\> ).**

**Cause:** The specified directory already exists.

**Action:** Delete or rename the existing directory, or specify a different
directory.

**0x1117A ( 70010) smERR_ABORT_ThereIsNoDatabaseIncrementalBackup There is no
incremental database backup.**

**Cause:** An incremental database backup has not been performed.

**Action:** Perform an incremental database backup before restoring the
database.

**0x1117B ( 70011) smERR_ABORT_ThereIsNoIncrementalBackup There is no
incremental backup.**

**Cause:** An incremental backup has not been performed.

**Action:** Perform an incremental backup before restoring the database.

**0x1117C ( 70012) smERR_ABORT_FailToCreateDirectory Failed to create directory
(Dir Name :\<0%s\> )**

**Cause:** The specified directory could not be created.

**Action:** Check the directory path or permission.

**0x11180 ( 70016) smERR_ABORT_DuplicateMultiplexDirPath A multiplex directory
path (\<0%s\>) has been specified more than once**

**Cause:** Duplicate multiplex directory path settings exist in
LOG_MULTIPLEX_DIR and/or ARCHIVE_MULTIPLEX_DIR.

**Action:** Check the LOG_MULTIPLEX_DIR and ARCHIVE_MULTIPLEX_DIR property
settings and remove duplicate paths.

**0x11181 ( 70017) smERR_ABORT_WrongLogMultiplexDirCount Number of
LOG_MULTIPLEX_DIR(\<0%d\>) directories not equal to
LOG_MULTIPLEX_COUNT(\<1%d\>)**

**Cause:** The number of directories specified using the LOG_MULTIPLEX_DIR
property is different from the value of LOG_MULTIPLEX_COUNT.

**Action:** Set the value of LOG_MULTIPLEX_COUNT to the number of directories
specified using LOG_MULTIPLEX_DIR.

**0x11182 ( 70018) smERR_ABORT_WrongArchMultiplexDirCount Number of
ARCH_MULTIPLEX_DIR(\<0%d\>) directories not equal to
ARCH_MULTIPLEX_COUNT(\<1%d\>)**

**Cause:** The number of directories specified using the ARCH_MULTIPLEX_DIR
property is different from the value of ARCH_MULTIPLEX_COUNT.

**Action:** Set the value of ARCH_MULTIPLEX_COUNT to the number of directories
specified using ARCH_MULTIPLEX_DIR.

**0x11183 ( 70019) smERR_ABORT_NOT_ENOUGH_NEXTENTSIZE Insufficient page
descriptor area in the temp table.**

**Cause:** There is not enough room in the temporary table for the page
descriptor information.

**Action:** Increase the value of the TEMP_MAX_PAGE_COUNT property.

**0x11184 ( 70020) smERR_ABORT_NOT_ENOUGH_WORKAREA Insufficient free space in
work area**

**Cause:** There is not enough free space in the work area.

**Action:** Increase the value of the TOTAL_WA_SIZE property.

**0x11185 ( 70021) smERR_ABORT_INVALID_SORTAREASIZE Insufficient sort area
space**

**Cause:** Cannot manage the page descriptor area due to the decrease in the
sort area size.

**Action:** Increase the value of the SORT_AREA_SIZE property.

**0x11186 ( 70022) smERR_ABORT_INVALID_HASHAREASIZE Insufficient hash area
space**

**Cause:** Cannot manage the page descriptor area due to the decrease in the
hash area size.

**Action:** Increase the value of the HASH_AREA_SIZE property.

**0x11187 ( 70023) smERR_ABORT_TEMP_FLUSHER_STOPPED Cannot sort or hash because
all temp flushers are stopped.**

**Cause:** The temporary flushers have stopped due to some unexpected problem.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x11188 ( 70024) smERR_ABORT_ALL_INDEX_DISABLED All Indexes are disabled.**

**Cause:** The requested action could not be performed because all of the
indexes for the table are disabled.

**Action:** Enable the index(es) and try again.

**0x11189 ( 70025) smERR_ABORT_PathIsNullString The length of the path is
zero.**

**Cause:** The path is an empty string.

**Action:** Provide a valid path to be created.

**0x1118A ( 70026) smERR_ABORT_TablespaceLockUse X or S tablespace lock is not
allowed while the TABLESPACE_LOCK_ENABLE property is 0.**

**Cause:** The user tried to execute a DDL command when the
TABLESPACE_LOCK_ENABLE property was 0.

**Action:** Change the TABLESPACE_LOCK_ENABLE value to 1.

**0x1118C ( 70028) smERR_ABORT_sdsFlusherNotStarted The Secondary flusher
[\<0%d\>] was not started.**

**Cause:** The flusher was not started.

**Action:** Check the secondary flusher status.

**0x1118D ( 70029) smERR_ABORT_sdsFlusherRunning The Secondary flusher [\<0%d\>]
is already running.**

**Cause:** The flusher cannot be started because it is already running.

**Action:** Check the secondary flusher status.

**0x1118E ( 70030) smERR_ABORT_AllSecondaryFlushersStopped You cannot run the
DCL command because all secondary flushers are stopped.**

**Cause:** All secondary flushers are stopped.

**Action:** Start some secondary flushers.

**0x1118F ( 70031) smERR_ABORT_PageMovedownStopped Failed to movedown pages.**

**Cause:** Cannot movedown page to the secondary buffer.

**Action:** Check the secondary buffer.

**0x11190 ( 70032) smERR_ABORT_PageMoveUpStopped Failed to moveup a page.**

**Cause:** Cannot moveup page to the secondary buffer.

**Action:** Check the secondary buffer.

**0x11193 ( 70035) smERR_ABORT_InvalidSecondaryBufferHdr Invalid Secondary
Buffer File file header**

**Cause:** Invalid Secondary Buffer File header

**Action:** Copy a valid file to [SECONDARY_BUFFER_FILE_DIRECTORY]

**0x11194 ( 70036) smERR_ABORT_invalid_secondary_buffer_propperty Invalid
Secondary Buffer property. size=\<0%d\>, PATH = \<1%s\>**

**Cause:** The SECONDARY_BUFFER_XXXX property value is invalid.

**Action:** Check the environment variable SECONDARY_BUFFER_XXXX.

**0x11195 ( 70037) smERR_ABORT_service_secondary_buffer_in_recv Recovery
failure. Secondary Buffer is serving.**

**Cause:** Secondary Buffer service cannot be served before the recovery phase.

**Action:** Check the environment variable SECONDARY_BUFFER_XXXX.

**0x11196 ( 70038) smERR_ABORT_CannotCreateSecondaryBuffer Unable to create
Secondary Buffer.**

**Cause:** A secondary file could not be created.

**Action:** Check the environment variable SECONDARY_BUFFER_XXXX.

**0x11199 ( 70041) smERR_ABORT_Cannot_Perform_Level1_Backup Cannot perform level
1 backup.**

**Cause:** Level 0 backup does not exist.

**Action:** Perform a level 0 backup prior to executing a level 1 backup.

**0x1119A ( 70042) smERR_ABORT_UnableToExecuteAlterTable Unable to execute ALTER
TABLE on [ TableOID: \<0%lu\> ].**

**Cause:** Another transaction is performing an ALTER TABLE statement on the
table.

**Action:** Check whether another transaction is performing an ALTER TABLE
statement on the table.

**0x1119B ( 70043) smERR_ABORT_TablespaceDoesNotExist Tablespace[ID: %d] does
not exist.**

**Cause:** Tablespace which is written in the SCT_UPDATE_DRDB_CREATE_DBF log
does not exist in the database.

**Action:** Restore with a valid backup file.

**0x1119E ( 70046) smERR_ABORT_SDMOpenFailed Unable to open SDM device.**

**Cause:** Device does not support Smart SSD features or the device path may be
incorrectly specified.

**Action:** Check whether the device specified in the configuration file
supports Smart SSD features and is correct.

**0x111A0 ( 70048) smERR_ABORT_Maximum_Column_count_in_temptable Too many
columns in a temptable**

**Cause:** Too many columns in a temptable

**Action:** Cannot use queries based on the disk temp table.

**0x111A1 ( 70049) smERR_ABORT_TooManySlotIndiskTempTable Too many slot in disk
temp table.**

**Cause:** Cannot manage the page descriptor area bacause value of the
properties pertaining to the size of the disk temp table is incompatible.

**Action:** Increase the value of the SORT_AREA_SIZE/HASH_AREA_SIZE property or
decrease the value of the TEMP_MAX_PAGE_COUNT

**0x111A2 ( 70050) smERR_ABORT_NO_CALLBACK The database link is not
initialized.**

**Cause:** No callback functions are registered for the remote table.

**Action:** Please check that the database link is enabled.

**0x111A3 ( 70051) smERR_ABORT_Invalid_slot Invalid slot access.**

**Cause:** Invalid slot access.

\#\*Action: Refrain from attempting this action.

**0x111A4 ( 70052) smERR_ABORT_TooSmallDirectKeySize Failed to create a direct
key index because the column is larger than the available space in the index.**

**Cause:** The column on which the direct key index is to be created is bigger
than the maximum size set for the direct key index.

**Action:** Set a larger value for the MAXSIZE option of the direct key index.

**0x111A5 ( 70053) smERR_ABORT_NonDirectKeyOption The DIRECTKEY option is only
supported for memory B-Tree indexes.**

**Cause:** The DIRECTKEY option is only supported for memory B-Tree indexes.

**Action:** Create a memory B-Tree index or do not use the DIRECTKEY option for
this index.

**0x111A6 ( 70054) smERR_ABORT_InvalidDirectKeyMaxSize The value of the MAXSIZE
option exceeds the maximum limit.**

**Cause:** The maximum size of the direct key index exceeds the limit.

**Action:** Check the maximum size of the direct key index and change it so that
it is between 8 bytes and one-third of the memory B-Tree node.

**0x111A7 ( 70055) smERR_ABORT_InvalidDataTypeInDirectKey Direct key indexes do
not support this data type.**

**Cause:** The direct key index was used for an unsupported data type.

**Action:** Create direct key indexes only on CHAR, VARCHAR, NCHAR, and NVARCHAR
columns.

**0x111A8 ( 70056) smERR_ABORT_NoCompressionInDirectKey Direct key indexes do
not support compressed columns.**

**Cause:** An attempt was made to create a direct key index on a compressed
column.

**Action:** Either create a memory B-Tree index or do not use the DIRECTKEY
option for this index.

**0x111A9 ( 70057) smERR_ABORT_NoDirectKeyOnPartTable Direct key indexes do not
support partitioned tables.**

**Cause:** An attempt was made to create a direct key index on a partitioned
table.

**Action:** Either create a memory B-Tree index or do not use the DIRECTKEY
option for this index.

**0x111AA ( 70058) smERR_ABORT_ReorgFail A memory index is failed to
reorganizate.**

**Cause:** The system failed to lock a mutex.

**Action:** Retry the reorganization.

**0x111AB ( 70059) smERR_ABORT_TOO_MANY_TRAVERSAL It takes too long to retrieve
the index. (TableOID: \<0%lu\>, IndexID: \<1%u\>)**

**Cause:** An index is corrupt.

**Action:** Drop and rebuild the index.

**0x111AC ( 70060) smERR_ABORT_LogFileSizeIsZero OS return Log file size is
zero. ( \<0%s\> ).**

**Cause:** The log file prepare thread has been failed during a creation of the
log file or OS error.

**Action:** Check the log files size. If the size of log file exists zero,
remove its below.

**0x111AD ( 70061) smERR_ABORT_InvalidDatafileHeader The data file '\<0%s\>' has
an invalid header. : DATABASE SID=\<1%u\>, FID=\<2%u\>, RedoLSN=control[\<3%u\>,
\<4%u\>], [\<5%u\>, \<6%u\>], CreateLSN=control[\<7%u\>, \<8%u\>], [\<9%u\>,
\<10%u\>], DBVer=\<11%u\>, CtrVer=\<12%u\>, FileVer=\<13%u\>**

**Cause:** The data file creation LSN does not match one of the log anchor
files.

**Action:** Verify the data file.

**0x111AE ( 70062) smERR_ABORT_InvalidDataFileCreateLSN The create LSN (\<0%u\>,
\<1%u\>) of the data file (\<2%s\>) is bigger than the restart redo LSN
(\<3%u\>, \<4%u\>).**

**Cause:** The data file is invalid.

**Action:** Verify that the data file was backed up correctly.

**0x111B0 ( 70064) smERR_ABORT_NotFoundLog Cannot find the log record (LSN \>=
\<0%u\>,\<1%u\> ) that is needed in the logfile (\<2%s\>).**

**Cause:** The log file is invalid.

**Action:** Check the logfile.

**0x111B1 ( 70065) smERR_ABORT_InvalidLog Invalid Log
(FileNo:\<0%d\>,Offset:\<1%d\>)**

**Cause:** The log file is invalid.

**Action:** Check the logfile.

**0x111B2 ( 70066) smERR_ABORT_InvalidBCB The BCB does not exist or is not
valid. ( SpaceID:\<0%u\>, PageID:\<1%u\> )**

**Cause:** The BCB does not exist or is not valid.

**Action:** Please shut down and restart to rebuild BCB List.

\#

**0x111B3 ( 70067) smERR_ABORT_smnUniqueViolationInReplTrans Unique violation
caused conflict resolution in replication.**

**Cause:** Unique violation caused conflict resolution on replication.

**Action:** Check the conflict message written on
\$ALTIBASE_HOME/trc/altibase_rp.log.

**0x111B4 ( 70068) smERR_ABORT_NOT_SUPPORT_FALLOCATE The operation is not
supported by the filesystem(or kernel).**

**Cause:** The filesystem(or kernel) containing the file does not support this
operation.

**Action:** Set the LOG_CREATE_METHOD property value to 0 and restart the
server.

### IGNORE

**0x12007 ( 73735) smERR_IGNORE_SyncFail Failed to invoke the msync() system
function**

**Cause:** The system failed to synchronize a file with mapped memory.

**Action:** Ignore this error message.

**0x1214B ( 74059) smERR_IGNORE_CAN_NOT_USE_THIS_LOCATOR You can't use this
LobLocator.**

**Cause:** A NULL LobLocator cannot be used.

**Action:** Refrain from attempting this action.

### RETRY

**0x1304C ( 77900) smERR_RETRY_Already_Modified A record has already been
updated.**

**Cause:** Another transaction has already updated the same record.

**Action:** No action is necessary.

**0x13055 ( 77909) smERR_REBUILD_smiTableModified The table structure has been
modified.**

**Cause:** The table structure has been modified.

**Action:** Build the query again.

**0x13111 ( 78097) smERR_REBUILD_smiTBSModified The tablespace structure has
been modified**

**Cause:** The tablespace has been dropped.

**Action:** Build the query again.

**0x1318B ( 78219) smERR_RETRY_Row_Retry A record has already been updated.**

**Cause:** Another transaction has already updated the same record.

**Action:** No action is necessary.

3.MT Error Code
---------------

### FATAL

**0x20001 ( 131073) mtERR_FATAL_NOT_APPLICABLE Not applicable**

**Cause:** This error occurs due to a logical programming error.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x20003 ( 131075) mtERR_FATAL_MEMORY_SHORTAGE Out of memory**

**Cause:** Out of memory

**Action:** Verify that the system has sufficient memory.

**0x20004 ( 131076) mtERR_FATAL_CONVERSION_COLLISION Two or more conversions
\<0%s\> are defined for two data types.**

**Cause:** This is a data type conversion error.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x20005 ( 131077) mtERR_FATAL_INCOMPATIBLE_TYPE Incompatible data type
\<0%s\>.**

**Cause:** Incompatible data type

**Action:** Check the compatibility of the data types.

**0x20006 ( 131078) mtERR_FATAL_COLUMN_EXCEED Column exceed.**

**Cause:** The conversion path between MT data types exceeds the buffer size.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x20044 ( 131140) mtERR_FATAL_THR_MUTEXINIT Failed to invoke the mutex_init()
system function**

**Cause:** The system failed to initialize a mutex.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x20045 ( 131141) mtERR_FATAL_THR_MUTEXLOCK Failed to invoke the mutex_lock()
system function**

**Cause:** The system failed to lock a mutex.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x20046 ( 131142) mtERR_FATAL_THR_MUTEXUNLOCK Failed to invoke the
muntex_unlock() system function**

**Cause:** The system failed to unlock a mutex.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

### ABORT

**0x21002 ( 135170) mtERR_ABORT_NOT_APPLICABLE Not applicable**

**Cause:** This error occurs due to a logical programming error.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x21007 ( 135175) mtERR_ABORT_LANGUAGE_MODULE_NOT_FOUND Language module
\<0%s\> not found.**

**Cause:** The language module was not found.

**Action:** Check the language.

**0x21008 ( 135176) mtERR_ABORT_DATATYPE_MODULE_NOT_FOUND Data type module
\<0%s\> not found.**

**Cause:** The data type module was not found.

**Action:** Check the data type.

**0x21009 ( 135177) mtERR_ABORT_CONVERSION_MODULE_NOT_FOUND Conversion module
\<0%s\> not found.**

**Cause:** The conversion module was not found.

**Action:** Check the compatibility of the data types.

**0x2100A ( 135178) mtERR_ABORT_FUNCTION_MODULE_NOT_FOUND Function module
\<0%s\> not found.**

**Cause:** The function module was not found.

**Action:** Use the correct function name.

**0x2100B ( 135179) mtERR_ABORT_INVALID_FUNCTION_ARGUMENT Invalid number of
arguments for a function.**

**Cause:** The number of arguments for the function was invalid.

**Action:** Check the number of arguments required by the function.

**0x2100C ( 135180) mtERR_ABORT_CONVERSION_NOT_APPLICABLE Conversion not
applicable.**

**Cause:** The conversion is not applicable.

**Action:** Check the compatibility of the data types.

**0x2100D ( 135181) mtERR_ABORT_INVALID_LENGTH Invalid data type length**

**Cause:** The length of the data type was invalid.

**Action:** Check the length of the data type.

**0x2100E ( 135182) mtERR_ABORT_INVALID_PRECISION Invalid data type precision**

**Cause:** The precision of the data type was invalid.

**Action:** Check the precision of the data type.

**0x2100F ( 135183) mtERR_ABORT_INVALID_SCALE Invalid data type scale**

**Cause:** The scale of the data type was invalid.

**Action:** Check the scale of the data type.

**0x21010 ( 135184) mtERR_ABORT_VALUE_OVERFLOW Value overflow**

**Cause:** Value overflow

**Action:** Change the value or data type.

**0x21011 ( 135185) mtERR_ABORT_INVALID_LITERAL Invalid literal**

**Cause:** Invalid literal.

**Action:** Check the constant of the data type.

**0x21013 ( 135187) mtERR_ABORT_STACK_OVERFLOW Calculation stack overflow**

**Cause:** Calculation stack overflow.

**Action:** Alter Alter the calculation stack size using the ALTER SESSION
statement.

**0x21014 ( 135188) mtERR_ABORT_NOT_AGGREGATION The function is not an aggregate
function.**

**Cause:** The function is not an aggregate function.

**Action:** Remove the ALL or DISTINCT keyword.

**0x21016 ( 135190) mtERR_ABORT_DIVIDE_BY_ZERO Division by zero**

**Cause:** An attempt was made to divide a number by zero.

**Action:** Find and remove the attempt to divide a number by zero.

**0x21017 ( 135191) mtERR_ABORT_ARGUMENT_NOT_APPLICABLE The argument is not
applicable.**

**Cause:** The argument is not applicable to the function.

**Action:** Verify that the argument falls within the valid range.

**0x21018 ( 135192) mtERR_ABORT_NOT_SUPPORTED_OBJECT_TYPE The specified object
type is currently not supported.**

**Cause:** Unsupported object type

**Action:** For geometry types, only the POINT type is currently supported.

**0x21019 ( 135193) mtERR_ABORT_OBJECT_TYPE_NOT_APPLICABLE Inapplicable object
type**

**Cause:** The specified object type is not applicable to the function.

**Action:** Check the type of the object.

**0x2101A ( 135194) mtERR_ABORT_INVALID_WKT Error parsing well-known-text**

**Cause:** The specified well-known-text is not correct.

**Action:** Check the well-known-text.

**0x2101B ( 135195) mtERR_ABORT_TO_CHAR_MAX_PRECISION The value exceeds the
maximum precision ( \<0%d\> ) of the format.**

**Cause:** The maximum precision of the format has been exceeded.

**Action:** Check the size of the format string.

**0x2101C ( 135196) mtERR_ABORT_VALIDATE_INVALID_VALUE Invalid data value**

**Cause:** The value of the data exceeds the logical value scope.

**Action:** Check the data value.

**0x2101D ( 135197) mtERR_ABORT_VALIDATE_INVALID_LENGTH Invalid data length**

**Cause:** The length of the data exceeds the valid scope.

**Action:** Check the length of the data.

**0x2101E ( 135198) mtERR_ABORT_CODING_INVALID_FMT Invalid coding format**

**Cause:** The compiled coding format is not valid.

**Action:** Check the compiled format.

**0x2101F ( 135199) mtERR_ABORT_CODING_DATA_FMT_MISMATCH Mismatched data and
format**

**Cause:** The data string mismatches the specified format.

**Action:** Check the data string.

**0x21020 ( 135200) mtERR_ABORT_INVALID_LITERAL_AFTER_ESCAPE Missing or invalid
literal following the escape character**

**Cause:** The escape character must be followed by either '%' or '_'.

**Action:** Check the LIKE predicate.

**0x21021 ( 135201) mtERR_ABORT_INVALID_ESCAPE Invalid escape literal**

**Cause:** The length of the escape literal is greater than one. The escape
literal is invalid.

**Action:** Check the escape character of the LIKE predicate.

**0x2102A ( 135210) mtERR_ABORT_NOT_SUPPORTED_YET Not supported yet.**

**Cause:** The digest algorithm is not supported yet.

**Action:** No action is necessary.

**0x2102B ( 135211) mtERR_ABORT_INVALID_DIGEST_ALGORITHM Invalid digest
algorithm.**

**Cause:** The digest algorithm name is unknown.

**Action:** Check the second argument of the digest function.

**0x2102C ( 135212) mtERR_ABORT_ARGUMENT_VALUE_OUT_OF_RANGE The argument
'\<0%d\>' is out of range.**

**Cause:** The argument value is out of range.

**Action:** Check the argument value.

**0x2102D ( 135213) mtERR_ABORT_DATEDIFF_OUT_OF_RANGE_IN_SECOND The interval
between startdate and enddate exceeded 68 years.**

**Cause:** If the date field name is 'SECOND', the interval between startdate
and enddate must be less than 68 years.

**Action:** Check the startdate and enddate values.

**0x2102E ( 135214) mtERR_ABORT_DATEDIFF_OUT_OF_RANGE_IN_MICROSECOND The
interval between startdate and enddate exceeded 30 days.**

**Cause:** If the date field name is 'MICROSECOND', the interval between
startdate and enddate must be less than 30 days.

**Action:** Check the startdate and enddate values.

**0x2102F ( 135215) mtERR_ABORT_INVALID_SIZE_OF_SECOND_AND_MICROSECOND The value
of SSSSSSSS must be an eight-digit number.**

**Cause:** The value of SSSSSSSS has less than eight digits.

**Action:** Check the value of SSSSSSSS.

**0x21030 ( 135216) mtERR_ABORT_INVALID_CHARACTER Invalid character use.**

**Cause:** An invalid character is being used.

**Action:** Verify that every character in the input string is a valid
character.

**0x21031 ( 135217) mtERR_ABORT_CONVERSION_DISABLE Unable to convert the data
type.**

**Cause:** Unable to convert the data type.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x21041 ( 135233) mtERR_ABORT_ONLY_USE_DEC_OR_HEX_IN_DUMP_FUNC Only a decimal
or hexadecimal number is allowed.**

**Cause:** Only a decimal or hexadecimal number is allowed.

**Action:** Check the number.

**0x21042 ( 135234) mtERR_ABORT_INVALID_U_TYPE_STRING '\\' must be followed by
four hexadecimal characters.**

**Cause:** '\\' must be followed by four hexadecimal characters.

**Action:** Fix the string.

**0x2104B ( 135243) mtERR_ABORT_INVALID_STORED_DATA_LENGTH The data saved in the
DBMS are not the expected length.**

**Cause:** The disk page is broken or the meta table has invalid data.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x21022 ( 135202) mtERR_ABORT_INVALID_DATE Invalid date literal**

**Cause:** The character to be converted to the date type is invalid.

**Action:** Check the arguments in the date conversion function.

**0x21023 ( 135203) mtERR_ABORT_INVALID_YEAR The year is invalid or out of
range.**

**Cause:** The year part of the date literal is invalid or out of range.

**Action:** Check the arguments in the date conversion function.

**0x21024 ( 135204) mtERR_ABORT_INVALID_MONTH The month value must be from 1 to
12.**

**Cause:** The month part of the date literal is invalid or out of range.

**Action:** Check the arguments in the date conversion function.

**0x21025 ( 135205) mtERR_ABORT_INVALID_DAY Invalid day of the month**

**Cause:** The day part of the date literal is invalid or out of range.

**Action:** Check the arguments in the date conversion function.

**0x21026 ( 135206) mtERR_ABORT_INVALID_HOUR The hour value must be between 1
and 12 inclusive.**

**Cause:** An invalid hour was specified for a date using the 12-hour time
format.

**Action:** Enter an hour value between 1 and 12.

**0x21027 ( 135207) mtERR_ABORT_INVALID_MINUTE The minutes value must be between
0 and 59 inclusive.**

**Cause:** The minutes part of the date literal is invalid or out of range.

**Action:** Check the arguments in the date conversion function.

**0x21028 ( 135208) mtERR_ABORT_INVALID_SECOND The seconds value must be between
0 and 59 inclusive.**

**Cause:** The seconds part of the date literal is invalid or out of range.

**Action:** Check the arguments in the date conversion function.

**0x21029 ( 135209) mtERR_ABORT_INVALID_MICROSECOND The microseconds value must
be between 0 and 999999 inclusive.**

**Cause:** The microseconds part of the date literal is invalid or out of range.

**Action:** Check the arguments in the date conversion function.

**0x21032 ( 135218) mtERR_ABORT_DATE_NOT_ENOUGH_INPUT The input literal is not
long enough for the date format.**

**Cause:** The data to be converted to the date format was incomplete; the date
format picture was longer than the input data.

**Action:** Either add more input or shorten the date format picture, then retry
the operation.

**0x21033 ( 135219) mtERR_ABORT_DATE_NOT_ENOUGH_FORMAT The date format picture
ends before the entire input string was converted.**

**Cause:** The first part of the format picture was converted into a valid date,
but the remaining data was not required.

**Action:** Check the specifications for date format pictures and correct the
statement.

**0x21034 ( 135220) mtERR_ABORT_DATE_INVALID_HOUR24 Hours must be between 0 and
23 inclusive.**

**Cause:** An invalid hour value was specified for a date.

**Action:** Enter an hour value between 0 and 23 inclusive.

**0x21035 ( 135221) mtERR_ABORT_DATE_INVALID_DAY_OF_YEAR The day of the year
must be between 1 and 365 (366 for leap year) inclusive.**

**Cause:** An invalid day of the year was specified in a date. The day of the
year (DDD) must be between 1 and 365 inclusive for a non-leap year or 1 and 366
inclusive for a leap year.

**Action:** Enter a day of the year value between 1 and 365 (or 366) inclusive.

**0x21036 ( 135222) mtERR_ABORT_DATE_INVALID_SEC_IN_DAY The seconds value in the
date must be between 0 and 86399 inclusive.**

**Cause:** An invalid value for the number of seconds was specified in a date.

**Action:** Specify a seconds value between 0 and 86399 inclusive.

**0x21037 ( 135223) mtERR_ABORT_DATE_CONFLICT_FORMAT The same (purpose) format
element(s) is (are) used twice or more.**

**Cause:** The same (purpose) format element is listed more than once in a date
specification.

**Action:** Check the format code.

**0x21038 ( 135224) mtERR_ABORT_DATE_LITERAL_MISMATCH Literals in the input do
not match the format string.**

**Cause:** Literals in the input must be the same length as literals in the
format string (with the exception of leading whitespaces). If the "FX" modifier
has been toggled on, the literal must match exactly, with no extra whitespace.

**Action:** Correct the format string to match the literal.

**0x21039 ( 135225) mtERR_ABORT_DATE_NOT_RECOGNIZED_FORMAT The date format (
\<0%s\> ) was not recognized.**

**Cause:** A date specification contained an invalid format code.

**Action:** Check that only valid date format codes are used.

**0x2103A ( 135226) mtERR_ABORT_DATE_NON_NUMERIC_INPUT A non-numeric character
was found where a numeric character was expected.**

**Cause:** The input data to be converted using the date format model was
incorrect. The input data contained a non-number where a number was required by
the format model.

**Action:** Fix the input data or the date format model so that they match each
other in number and type. Then retry the operation.

**0x2103B ( 135227) mtERR_ABORT_DATE_SSSSS_CONFLICT_SS The seconds-of-minute
value conflicts with the seconds-in-day value.**

**Cause:** A date specification contained both seconds of the minute and seconds
in the day, but the values did not correspond. If both types of seconds are
specified, the seconds of the minute value (SS) must correspond to the second
portion of the seconds past midnight value (SSSSS).

**Action:** Remove the seconds-of-minute value from the date specification or
enter a value that corresponds to the given seconds-in-day value.

**0x2103C ( 135228) mtERR_ABORT_DATE_SSSSS_CONFLICT_MI The minutes-of-hour value
conflicts with the seconds-in-day value.**

**Cause:** A date specification contained both minutes of the hour and seconds
in the day, but the values did not correspond. If both minutes in the hour (MI)
and seconds past midnight (SSSSS) are specified, the minutes value must be the
minute in which the seconds value falls.

**Action:** Remove the minutes value from the date specification or enter the
correct minute value for the specified seconds value.

**0x2103D ( 135229) mtERR_ABORT_DATE_SSSSS_CONFLICT_HH The hour value conflicts
with the seconds-in-day value.**

**Cause:** A date specification contained both an hour value and a seconds in
the day value, but the values did not correspond. If an hour is specified
together with a seconds-past-midnight (SSSSS) value, it must be the hour in
which the seconds value falls.

**Action:** Remove the hour value from the date specification or specify the
correct seconds-past-midnight value.

**0x2103E ( 135230) mtERR_ABORT_DATE_DDD_CONFLICT_DD Day of month conflicts with
day of year.**

**Cause:** A date containing the day of the month was specified, but the
day-of-the-month value did not correspond to the day-of-the-year value. If the
day-of-the-month value is specified as part of a date, it must be the same day
specified in the day-of-the-year value.

**Action:** Remove the day-of-the-month value from the date specification or
enter the correct day-of-the-year value.

**0x2103F ( 135231) mtERR_ABORT_DATE_DDD_CONFLICT_MM The month value conflicts
with the day-of-year value.**

**Cause:** The wrong month was specified in a date. If a month is specified as
part of a date, it must be the month in which the date occurs.

**Action:** Remove the month value from the date specification or enter the
correct date value.

**0x21040 ( 135232) mtERR_ABORT_DATE_DAY_CONFLICT A day-of-week value conflicts
with a date value.**

**Cause:** A day-of-the-week value was specified as part of a date, but the day
of the week did not correspond to the specified date value. If the day of the
week is specified with a date, it must be the same day of the week as the date.

**Action:** Remove the day-of-the-week value from the date specification or
enter a date value corresponding to the correct day of the week.

**0x21043 ( 135235) mtERR_ABORT_UNEXPECTED_ERROR Unexpected errors may have
occurred: \<0%s\>: \<1%s\>**

**Cause:** This error occurs due to a logical programming error.

**Action:** Check the error number from the trace log and contact Altibase's
Support Center (http://support.altibase.com/en/).

**0x21047 ( 135239) mtERR_ABORT_NULL_VALUE No NULL value is allowed to be used
as the data type.**

**Cause:** No NULL value is allowed to be used as the data type.

**Action:** Verify that there is no NULL value in the field.

**0x21048 ( 135240) mtERR_ABORT_OVERFLOW Out of range of value supported by the
type**

**Cause:** Out of range of value supported by the type

**Action:** Change the input value to be in the range of value supported by the
given type.

**0x21049 ( 135241) mtERR_ABORT_INVALID_NUMERIC Unable to cast the string to
INTEGER type**

**Cause:** It is impossible to cast the string to the INTEGER type.

**Action:** Change the string appropriately.

**0x2104A ( 135242) mtERR_ABORT_REACH_END Unexpected end of string**

**Cause:** Unexpected end of string

**Action:** Verify that the form of the string is legal.

**0x2104D ( 135245) mtERR_ABORT_WRONG_PATTERN Invalid pattern string**

**Cause:** A search attempt was made using an invalid pattern string.

**Action:** Verify that the pattern string is valid.

**0x2104E ( 135246) mtERR_ABORT_TZ_REGION_NOT_FOUND Time zone region not found**

**Cause:** The time zone region could not be found.

**Action:** Check the time zone region in the V\$TIME_ZONE_NAMES performance
view.

**0x2104F ( 135247) mtERR_ABORT_TZ_FMT_MISMATCH Time zone format string
mismatch**

**Cause:** The string literal does not match the format string.

**Action:** Check the time zone format string.

**0x21050 ( 135248) mtERR_ABORT_TZ_HOUR_OUT_OF_RANGE Time zone offset out of
range**

**Cause:** The time zone hour (offset) was less than -12 or greater than 14.

**Action:** Set the time zone hour to a value between -12 and 14 (inclusive).

**0x21051 ( 135249) mtERR_ABORT_TZ_LENGTH_EXCEED Time zone string too long**

**Cause:** The length of the TIME_ZONE value exceeds the maximum length.

**Action:** Check the time zone string.

**0x21052 ( 135250) mtERR_ABORT_LONG_PATTERN Pattern string too long**

**Cause:** A search attempt was made using an excessively long pattern string.

**Action:** Verify that the size of the pattern string is less than 4KB.

**0x21053 ( 135251) mtERR_ABORT_REGEXP_REQUIRED_PAREN The pattern requires
parentheses, brackets, or braces.**

**Cause:** The pattern requires parentheses, brackets, or braces.

**Action:** Check whether the pattern contains a closing parenthesis.

**0x21054 ( 135252) mtERR_ABORT_REGEXP_CLASS_EMPTY The pattern contains an empty
bracket.**

**Cause:** The pattern contains an empty bracket.

**Action:** Check whether the pattern contains an empty bracket.

**0x21055 ( 135253) mtERR_ABORT_REGEXP_CONST_OVERFLOW The pattern exceeds the
maximum supported numeric range(10 digits).**

**Cause:** The pattern exceeds the maximum supported numeric range(10 digits).

**Action:** Check whether the pattern contains a number with more than 10
digits.

**0x21056 ( 135254) mtERR_ABORT_REGEXP_REQUIRED_NUMBER The pattern requires
numbers({m} {m,} {m,n}: m and n must be numbers).**

**Cause:** The pattern requires numbers({m} {m,} {m,n}: m and n must be
numbers).

**Action:** Check whether valid numbers are input in the pattern format, {m}
{m,} {m,n}.

**0x21057 ( 135255) mtERR_ABORT_REGEXP_REQUIRED_COMMA The pattern requires
braces or commas.**

**Cause:** The pattern requires braces or commas.

**Action:** Check whether the pattern contains braces or commas.

**0x21058 ( 135256) mtERR_ABORT_REGEXP_UNEXPECTED_CAHR The pattern contains an
unexpected character.**

**Cause:** The pattern contains an unexpected character.

**Action:** Verify that the pattern string is valid.

**0x21059 ( 135257) mtERR_ABORT_REGEXP_UNFINISHED_RANGE The pattern contains an
unfinished range.**

**Cause:** The pattern contains an unfinished range.

**Action:** Verify that the pattern string is valid.

**0x2105A ( 135258) mtERR_ABORT_REGEXP_INVALID_RANGE The pattern contains an
invalid range.**

**Cause:** The pattern contains an invalid range.

**Action:** Verify that the pattern format [A-Z] is valid.

**0x2105B ( 135259) mtERR_ABORT_REGEXP_CLASS_INVALID_CHAR The pattern contains a
predefined character class.**

**Cause:** The pattern contains a predefined character class.

**Action:** Check whether the pattern contains a predefined character class.

**0x2105C ( 135260) mtERR_ABORT_REGEXP_LONG_PATTERN The pattern’s size exceeds
1024.**

**Cause:** The pattern’s size exceeds 1024.

**Action:** Verify that the size of the pattern string is less than 1KB.

**0x2105D ( 135261) mtERR_ABORT_CRYPT_PADDING_UNEXPECTED_CAHR The padded text
contains an unexpected padding character.**

**Cause:** The padded text contains an unexpected padding character.

**Action:** Only a value returned by the PKCS7PAD16() function is valid for the
PKCS7UNPAD( ) function.

**0x21061 ( 135265) mtERR_ABORT_TOO_LONG_CONCATENATION result of string
concatenation is too long.**

**Cause:** String concatenation result is more than the maximum size.

**Action:** Make sure that the result is less than the maximum size.

**0x21062 ( 135266) mtERR_ABORT_INVALID_PERCENTILE_VALUE The percentile value
should be a number between 0 and 1.**

**Cause:** A percentile value for PERCENTILE_CONT or PERCENTILE_DISC function is
specified out of range.

**Action:** Specify a value from [0,1].

**0x21063 ( 135267) mtERR_ABORT_WITHIN_GORUP_COLUMN_OVERFLOW The order by column
of within group exceeds the maximum limit.**

**Cause:** The column of the path exceeds the maximum limit.

**Action:** check order by column count.

**0x21064 ( 135268) mtERR_ABORT_MISSING_WITHIN_GROUP WITHIN keyword required for
this function.**

**Cause:** The function requires the WITHIN keyword.

**Action:** Add the proper WITHIN keyword for the function.

**0x21065 ( 135269) mtERR_ABORT_NOT_ALLOWED_WITHIN_GROUP A WITHIN keyword is not
allowed here.**

**Cause:** A WITHIN keyword is not allowed here.

**Action:** Remove the WITHIN keyword.

**0x21066 ( 135270) mtERR_ABORT_MEMORY_ALLOCATION Insufficient memory for the
Mathematics Module.**

**Cause:** The memory manager could not allocate sufficient memory for the
Mathematics Module.

**Action:** Verify that the system has sufficient memory.

**0x21067 ( 135271) mtERR_ABORT_INVALID_ENCODED_STRING invalid encode string.**

**Cause:** An error occurred while decoding the input string.

**Action:** Verify that source data is a valid encoded string.

**0x21068 ( 135272) mtERR_ABORT_SMTP_REPLY_ERROR SMTP Reply Error: \<0%s\>**

**Cause:** The SMTP server reply an error message.

**Action:** check an error message.

### IGNORE

**0x22000 ( 139264) mtERR_IGNORE_NOERROR Ignore this message.**

**Cause:** This is not an error.

**Action:** Ignore this message.

**0x2205E ( 139358) mtERR_IGNORE_CDBC_NOT_SUPPORTED Unsupported data type.**

**Cause:** Unsupported data type.

**Action:** Check your source code and use a valid data type.

**0x2205F ( 139359) mtERR_IGNORE_CDBC_SMALL_BUFFER Buffer is smaller than the
minimum size.**

**Cause:** You allocated a buffer smaller than the minimum size.

**Action:** Check your source code and allocate a buffer of an appropriate size.

**0x22060 ( 139360) mtERR_IGNORE_CDBC_NULL_SCOLUMN Argument value is null.**

**Cause:** The value of the function argument is null.

**Action:** Check your source code and set a value for the function argument.

4.RP Error Code
---------------

### FATAL

**0x60002 ( 393218) rpERR_FATAL_RP_MEMORY_ALLOCATION Unable to allocate memory**

**Cause:** The system failed to allocate sufficient memory.

**Action:** Verify that sufficient memory is available.

**0x60006 ( 393222) rpERR_FATAL_RP_SENDER_INVALID_OPTION Internal error**

**Cause:** An invalid replication option was set for the replication Sender.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x60071 ( 393329) rpERR_FATAL_ThrCondInit Failed to invoke the cond_init()
system function**

**Cause:** The system failed to invoke the cond_init() function.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x600A2 ( 393378) rpERR_FATAL_ThrCondBroadcast Failed to invoke a system
function, cond_broadcast(), errno is (\<0%d\>).**

**Cause:**

\# - The system failed to invoke the cond_broadcast() function.

**Action:**

\# - Please send a bug report to the vendor.

**0x600B4 ( 393396) rpERR_FATAL_ThrMutexInit Unable to initialize a mutex.**

**Cause:** The system failed to initialize a mutex.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x600B5 ( 393397) rpERR_FATAL_ThrMutexDestroy Failed to invoke the
mutex_destroy() system function**

**Cause:** The system failed to remove a mutex.

**Action:** Please send a bug report to the vendor.

**0x60125 ( 393509) rpERR_FATAL_RPD_REPL_META_CRASH A replication meta table
crashed.**

**Cause:** A replication meta table crashed.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x60167 ( 393575) rpERR_FATAL_ThrLatchInit Unable to initialize a latch.**

**Cause:** The system failed to initialize a latch.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

### ABORT

**0x61003 ( 397315) rpERR_ABORT_RP_READ_SOCKET Unable to read from a socket**

**Cause:** The connection to replication has been disconnected or failed to
receive data within the specified time.

**Action:** Increase the replication-related timeout or check the local and
remote altibase_rp.log file to find out why the connection is broken.

**0x61004 ( 397316) rpERR_ABORT_RP_WRITE_SOCKET Unable to write to a socket**

**Cause:** Network error

**Action:** Check the network.

**0x61008 ( 397320) rpERR_ABORT_RP_META_NO_SUCH_DATA Unable to find meta
information.**

**Cause:** Failed to find information from the replication metadata either
because the database crashed or an error occurred.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x61009 ( 397321) rpERR_ABORT_RP_JOIN_THREAD Unable to join the sender
thread**

**Cause:** The system failed to join the sender thread.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x6100A ( 397322) rpERR_ABORT_RP_ALREADY_STARTED The sender has already been
started.**

**Cause:** The sender has already been started.

**Action:** Check whether the sender has already been started.

**0x6100B ( 397323) rpERR_ABORT_RP_MAXIMUM_THREADS_REACHED Out of replication
threads ( replication thread count \> \<0%d\>)**

**Cause:** The number of replications currently running on the system has
exceeded the maximum limit.

**Action:** Check the maximum number of replication threads.

**0x6100D ( 397325) rpERR_ABORT_RP_SENDER_HANDSHAKE [Sender] Failed to handshake
with the peer server (\<0%s\>)**

**Cause:** Network or server error. The replication definition might contain an
error.

**Action:** Check the network. Verify that the replication definition is the
same on the corresponding server.

**0x6100E ( 397326) rpERR_ABORT_RP_PEER_WAKEUP Failed to wake up peer sender**

**Cause:** When the server started, it attempted to connect to the remote
database, but failed.

**Action:** Start the remote database.

**0x61010 ( 397328) rpERR_ABORT_RP_SENDER_START [Sender] Failed to start the
sender thread**

**Cause:** The communication or handshaking failed.

**Action:** Check the network, the server, and the replication definition.

**0x61011 ( 397329) rpERR_ABORT_RP_SENDER_SYNCSTART [Sender] Failed to start
sync**

**Cause:** The communication or handshaking failed.

**Action:** Check the network, the server, and the replication definition.

**0x61012 ( 397330) rpERR_ABORT_RP_SENDER_CONNECT_PEER [Sender] Failed to
connect to the peer server**

\# Cause:

\# - 1. Peer server is not running.

\# - 2. IP address or Port number is invalid.

\# - 3. Network is not working.

**Action:**

\# - 1. Confirm peer server is running.

\# - 2. Verify both IP address and port number are correctly entered.

\# - 3. Ensure that network is working normally.

**0x61013 ( 397331) rpERR_ABORT_RP_SENDER_DO_REPLICATION [Sender] Replication
failed**

**Cause:** The replication Sender failed during replication.

**Action:** Check the error number from the altibase_rp.log file and take
appropriate action.

**0x61014 ( 397332) rpERR_ABORT_RP_SENDER_MAKE_XLOG_IN_LOGFILE [Sender] Failed
to make XLOG in a log file at SN[\<0%lu\>]**

**Cause:** The replication Sender failed to convert the log of the corresponding
SN in the log file to an XLog.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x61015 ( 397333) rpERR_ABORT_RP_SENDER_CHECK_LOG [Sender] Failed to check a
physical log at SN[\<0%lu\>]**

**Cause:** The replication Sender cannot read the log of the corresponding SN.

**Action:** The replication Sender that sends logs to the Altibase Log Analyzer
must specify the SN to another position.

**0x6101D ( 397341) rpERR_ABORT_RP_SENDER_SYNC_TABLE [Sender] Failed to sync a
table**

**Cause:** The replication Sender failed to synchronize the table.

**Action:** Check the network status or the status of the corresponding server,
and take appropriate action.

**0x61022 ( 397346) rpERR_ABORT_RP_SENDER_SLEEP [Sender] Sender Sleep : \<0%d\>
seconds**

**Cause:** The sender is in sleep.

**Action:** This message is for information only.

**0x61023 ( 397347) rpERR_ABORT_RP_REPLICATION_DISABLED Replication is
disabled**

**Cause:** The replication feature of Altibase could not be used. Replication
was not initialized on startup because the port is not set correctly.

**Action:** Set the port correctly.

**0x61025 ( 397349) rpERR_ABORT_RP_REPLICATION_DENY Replication denied
(\<0%s\>)**

**Cause:** Replication access was denied because the corresponding server has
not yet started.

**Action:** Restart replication after a brief delay. If replication has already
started, wait for the corresponding server to start.

**0x61026 ( 397350) rpERR_ABORT_RP_REPLICATION_NOK Unable to process the
replication (\<0%s\>)**

**Cause:** Replication was not possible because some conditions were not
satisfied.

**Action:** Try again later.

**0x61027 ( 397351) rpERR_ABORT_RP_REPLICATION_NOT_STARTED Replication did not
start.**

**Cause:** The replication did not start.

**Action:** Verify that replication was started.

**0x61028 ( 397352) rpERR_ABORT_RP_REPLICATION_SELF_REPLICATION A case of
self-replication has been detected. (Peer=\<0%s\>:\<1%u\>)**

**Cause:** The IP address and port for replication are the same as those of the
local server.

**Action:** Check the IP address and port for replication.

**0x61029 ( 397353) rpERR_ABORT_RP_ENTRY_EXIST [Sender] Entry already exists in
insert()**

**Cause:** The same transaction table slot is being used.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x6102C ( 397356) rpERR_ABORT_START_RECEIVER [Receiver] Failed to start the
receiver**

**Cause:** The replication Receiver has failed to start either because the
versions are different or there is a network error.

**Action:** Check the replication version between the two nodes, or check the
network.

**0x6102D ( 397357) rpERR_ABORT_LISTEN [Receiver] Failed to listen to a
replication socket (Port No:\<0%d\>)**

\# Cause: REPLICATION_PORT_NO port is occupied by other application or not yet
released.

**Action:** Use other port number or terminate the application using the
REPLICATION_PORT_NO port.

**0x6102E ( 397358) rpERR_ABORT_SOCKET_CREATE [Receiver] Failed to create a
replication socket.**

**Cause:** Insufficient memory

**Action:** Increase the amount of available memory in the system.

**0x61030 ( 397360) rpERR_ABORT_META_BUILD [Receiver] Failed to build meta
information**

**Cause:** The system failed to create metadata.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x61031 ( 397361) rpERR_ABORT_META_MISMATCH [Receiver] Meta information does
not match**

**Cause:** The receiver's meta information does not match the sender's meta
information.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x61032 ( 397362) rpERR_ABORT_SEND_ACK [Receiver] Failed to send ACK**

**Cause:** Failed to send a handshake ACK to the replication Sender.

**Action:** Check the network.

**0x61033 ( 397363) rpERR_ABORT_TX_BEGIN [Receiver] Transaction begin failure**

**Cause:** The replication Receiver failed to start an internal transaction.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x61034 ( 397364) rpERR_ABORT_TX_COMMIT [Receiver] Transaction commit
failure**

**Cause:** The replication Receiver failed to commit an internal transaction.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x61035 ( 397365) rpERR_ABORT_UPDATE_CONFLICT [Receiver] An update conflict
occurred.**

**Cause:** An update conflict occurred while the replication was in process.

**Action:** You may safely ignore this message if you have restarted
replication.

**0x61037 ( 397367) rpERR_ABORT_NOT_EXIST_TABLE_DEL [Receiver]
err_not_exist_table in deleteXLog()**

**Cause:** The table does not exist.

**Action:** Check the altibase_rp.log file.

**0x61038 ( 397368) rpERR_ABORT_NOT_EXIST_TABLE_INS [Receiver]
err_not_exist_table in insertXLog()**

**Cause:** The table does not exist.

**Action:** Check the altibase_rp.log file.

**0x61039 ( 397369) rpERR_ABORT_NOT_EXIST_TABLE_UPT [Receiver]
err_not_exist_table in updateXLog()**

**Cause:** The table does not exist.

**Action:** Check the altibase_rp.log file.

**0x61042 ( 397378) rpERR_ABORT_TX_COMMIT2 [Receiver] err_tx in commit()**

**Cause:** The replication Receiver failed to commit a replicated transaction.

**Action:** Check the error code from the altibase_rp.log file and take
appropriate action. If the maximum number of rows has been set for creating
tables, commit can fail.

**0x61043 ( 397379) rpERR_ABORT_TX_ERROR [Receiver] err_tx in err_tx()**

**Cause:** The replication Receiver failed to roll back a committed transaction.

**Action:** Check the error code from the altibase_rp.log file and take
appropriate action.

**0x61046 ( 397382) rpERR_ABORT_PROTOCOL_RUN [Receiver] protocol error in
run()**

**Cause:** The replication Receiver received an unexpected protocol from the
replication Sender.

**Action:** Check the replication protocol version between the two nodes. If the
versions are different, change it to the same version. If the versions are the
same, check the error number from the trace log and contact Altibase’s Support
Center (http://support.altibase.com/en/).

**0x61047 ( 397383) rpERR_ABORT_ERROR_RECVXLOG2 [Receiver] \<0%s\> receiver has
error in recvXLog()**

**Cause:** Unable to read data from the network connection.

**Action:** Check the network connection.

**0x6104B ( 397387) rpERR_ABORT_END_THREAD [Receiver] \<0%s\> receiver is ended
(by thr_exit)**

**Cause:** Unable to read data from the network connection.

**Action:** Check the network connection.

**0x6104F ( 397391) rpERR_ABORT_RP_SENDER_INIT [Sender] Failed to initialize**

**Cause:** The replication Sender failed to initialize.

**Action:** Restart the replication Sender. If the replication Sender repeatedly
fails to start, check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x61053 ( 397395) rpERR_ABORT_INVALID_PARAM [Sender] Invalid parameter**

**Cause:** Internal server error

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x61055 ( 397397) rpERR_ABORT_MEMORY_ALLOC Memory allocation failure
[Function=\<0%s\>, Variable=\<1%s\>]**

**Cause:** The system failed to allocate memory.

**Action:** Check the status of the memory available for allocation and retry.

**0x61056 ( 397398) rpERR_ABORT_ALREADY_FINAL [Receiver] to be ended (already
finalized by manager)**

**Cause:** The replication Receiver terminated abnormally. This error mainly
occurs due to a network error or a rollback of a long-running transaction.

**Action:** Check the error number from the altibase_rp.log file and take
appropriate action. If the replication Receiver has rolled back a long-running
transaction, increase the value of replication_receive_timeout on both nodes.

**0x6105A ( 397402) rpERR_ABORT_BEGIN_ERROR_IN_RUN [Receiver] begin error in
run()**

**Cause:** The replication Receiver failed to add a new transaction.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x6105B ( 397403) rpERR_ABORT_ABORT_ERROR_IN_RUN [Receiver] abort error in
run()**

**Cause:** The replication Receiver failed to roll back a transaction.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x6105C ( 397404) rpERR_ABORT_COMMIT_ERROR_IN_RUN [Receiver] commit error in
run()**

**Cause:** The replication Receiver failed to commit a replicated transaction.

**Action:** Check the error number from the altibase_rp.log file and take
appropriate action.

**0x61069 ( 397417) rpERR_ABORT_RP_INTERNAL_ARG Internal server error in
replication module (\<0%s\>).**

**Cause:** Program eror.

**Action:** Check the error number from the trace log and contact Altibase's
Support Center (http://support.altibase.com/en/).

**0x6106B ( 397419) rpERR_ABORT_RP_SENDER_SEND_ERROR [Sender] Failed to send
XLog to peer network**

**Cause:** The peer network has a problem.

**Action:** The system will retry automatically.

**0x6106C ( 397420) rpERR_ABORT_RP_SENDER_RECV_ERROR [Sender] Failed to receive
XLog from peer network**

**Cause:** The peer network has a problem or is offline.

**Action:** The system will retry automatically.

**0x6106D ( 397421) rpERR_ABORT_RP_SET_SAVEPOINT_ERROR_IN_RUN [Receiver]
smiTrans set(savepoint) error in run()**

**Cause:** The replication Receiver failed to create a savepoint.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x6106E ( 397422) rpERR_ABORT_RP_ABORT_SAVEPOINT_ERROR_IN_RUN [Receiver]
smiTrans abort(savepoint) error in run()**

**Cause:** The replication Receiver failed to roll back to a savepoint.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x6106F ( 397423) rpERR_ABORT_RP_NOT_DROP_ONE_TABLE You cannot drop only one
replicated table.**

**Cause:** You cannot drop a table when only one replicated table is remaining.

**Action:** Drop the replication object, or insert another table and drop the
table.

**0x61075 ( 397429) rpERR_ABORT_TIMEOUT_EXCEED Timeout exceed.**

\# \*Cause : A timeout occurred while the replication Sender and Receiver were
communicating.

\# \*Action : Set a larger value for the REPLICATION_RECEIVE_TIMEOUT property.

**0x61076 ( 397430) rpERR_ABORT_INVALID_XSN [Sender] Invalid XSN[\<0%ld\>] \>
Current[\<1%ld\>] occurred**

**Cause:** The restart SN value of the replication Sender is invalid.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x61077 ( 397431) rpERR_ABORT_RP_SENDER_UPDATE_XSN [Sender] Failed to update
XSN**

**Cause:** The replication Sender failed to update the restart SN value.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x61078 ( 397432) rpERR_ABORT_RP_TRANSACTION_TABLE_IN_INSERT [Receiver]
replication transaction table error during insert() operation**

**Cause:** The replication Receiver failed to insert data into the transaction
table.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x6107A ( 397434) rpERR_ABORT_NOT_HAVE_HOST Invalid Host [\<0%s\>, \<1%d\>]**

**Cause:** Host Information (IP, Port) doesn't belong to this replication.

**Action:** Attempt this operation again using the correct host information.

**0x6107B ( 397435) rpERR_ABORT_COLUMN_COUNT_MISMATCH \<0%s\> column count
mismatch of \<1%s\> table. ( column count of received XLog is \<2%d\> and column
count of meta is \<3%d\>)**

**Cause:** The sender and receiver table column counts do not match.

**Action:** Reorganize replicated tables and recreate the replication after
checking both the sender and receiver table meta information.

**0x6107C ( 397436) rpERR_ABORT_COLUMN_ID_MISMATCH \<0%s\> \<1%d\>'th column ID
mismatch of \<2%s\> table. ( column ID of received XLog is \<3%d\> and column ID
of meta is \<4%d\>)**

**Cause:** The sender and receiver table column IDs do not match.

**Action:** Reorganize replicated tables and recreate the replication after
checking both the sender and receiver table meta information.

**0x61082 ( 397442) rpERR_ABORT_INDEX_COUNT_IS_NOT_AVAILABLE [Meta] Index Count
isn't available [\<0%u\>]**

**Cause:** Index count mismatch

**Action:** Check the number of table indexes.

**0x61085 ( 397445) rpERR_ABORT_FREE_LINK [Network] Free link operation failed**

**Cause:** Failed to free network memory resources.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x61086 ( 397446) rpERR_ABORT_FREE_DISPATCHER [Network] Free dispatcher
operation failed**

**Cause:** Failed to free network dispatcher resources.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x61087 ( 397447) rpERR_ABORT_SHUTDOWN_LINK [Network] Shutdown link operation
failed**

**Cause:** Failed to shut down the network because the corresponding party has
terminated first.

**Action:** You may safely ignore this message.

**0x61088 ( 397448) rpERR_ABORT_CLOSE_LINK [Network] Close link operation
failed**

**Cause:** Failed to close a network socket.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x61089 ( 397449) rpERR_ABORT_ALLOC_LINK [Network] Alloc link operation
failed**

**Cause:** Failed to allocate network resources.

**Action:** Check the state of system resources. If they are insufficient, take
appropriate action.

**0x6108A ( 397450) rpERR_ABORT_CONNECT_FAIL [Network] Connection failed**

**Cause:** The system failed to invoke connect() function.

**Action:** Verify that the corresponding server is alive, or check the network.

**0x6108B ( 397451) rpERR_ABORT_SEND_FAIL [Network] Send operation failed**

**Cause:** The replication Sender failed to send data to the corresponding
server.

**Action:** Verify that the corresponding server is alive, or check the network
status.

**0x6108C ( 397452) rpERR_ABORT_OPEN_LOB_CURSOR [SmExec] A failure occurred
while opening LOB Cursor**

**Cause:** The replication Receiver tried to open a LOB cursor to apply LOB
data, but failed.

**Action:** Check whether the LOB data of the replication target table is the
same and take appropriate action.

**0x6108D ( 397453) rpERR_ABORT_CLOSE_LOB_CURSOR [SmExec] A failure occurred
while closing the LOB Cursor**

**Cause:** The replication Receiver tried to close a LOB cursor to finish
applying LOB data, but failed.

**Action:** Check whether the LOB data of the replication target table is the
same and take appropriate action.

**0x6108E ( 397454) rpERR_ABORT_LOB_PREPARE_WRITE [SmExec] A failure occurred
while preparing for LOB writing**

**Cause:** The replication Receiver tried to prepare to write the LOB cursor to
finish applying LOB data, but failed.

**Action:** Check whether the LOB data of the replication target table is the
same and take appropriate action.

**0x6108F ( 397455) rpERR_ABORT_LOB_FINISH_WRITE [SmExec] A failure occurred
while finishing LOB writing**

**Cause:** The replication Receiver tried to finish writing to the LOB cursor to
finish applying LOB data, but failed.

**Action:** Check whether the LOB data of the replication target table is the
same and take appropriate action.

**0x61090 ( 397456) rpERR_ABORT_LOB_PARTIAL_WRITE [SmExec] A failure occurred
while writing the LOB piece**

**Cause:** The replication Receiver tried to partially write to the LOB cursor
to finish applying LOB data, but failed.

**Action:** Check whether the LOB data of the replication target table is the
same and take appropriate action.

**0x61091 ( 397457) rpERR_ABORT_LOB_GET_LENGTH [SmExec] A failure occurred while
getting the LOB piece length**

**Cause:** The replication Receiver tried to get the length of the LOB cursor to
finish applying LOB data, but failed.

**Action:** Check whether the LOB data of the replication target table is the
same and take appropriate action.

**0x61092 ( 397458) rpERR_ABORT_LOB_READ [SmExec] A failure occurred while
reading an LOB piece**

**Cause:** The replication Receiver tried to read the LOB cursor to finish
applying LOB data, but failed.

**Action:** Check whether the LOB data of the replication target table is the
same and take appropriate action.

**0x61094 ( 397460) rpERR_ABORT_RP_SENDER_NOT_FOUND_TABLE The given table isn't
found in the meta.**

**Cause:** Unable to find the table in the meta.

**Action:** Check the altibase_rp.log file and replication definition.

**0x61095 ( 397461) rpERR_ABORT_RP_RECEIVER_NOT_FOUND_TABLE The given table
isn't found in the meta.**

**Cause:** Unable to find the table in the meta.

**Action:** Check the altibase_rp.log file and replication definition.

**0x61096 ( 397462) rpERR_ABORT_RP_RECEIVER_NOT_FOUND_COLUMN The given column
isn't found in the meta information.**

**Cause:** Unable to find the column in the meta information.

**Action:** Check the altibase_rp.log file and replication definition.

**0x61097 ( 397463) rpERR_ABORT_GET_MODULE The module couldn't be found on the
server using the module ID.**

**Cause:** Unable to find the module pointer on the server.

**Action:** Verify the altibase_rp.log file and replication definition.

**0x61098 ( 397464) rpERR_ABORT_SENDER_INVALID_XLOG_TYPE [Sender] Invalid XLog
type [\<0%u\>] in sender analysis**

**Cause:** The XSN read and created by the replication Sender is invalid.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x61099 ( 397465) rpERR_ABORT_RECEIVER_INVALID_XLOG_TYPE [Receiver] Invalid
XLog type [\<0%u\>] in receiver analysis**

**Cause:** The replication Receiver received an invalid XLog.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x6109A ( 397466) rpERR_ABORT_ITEM_NOT_EXIST [Meta] Replication meta item
doesn't exist [Replication Name:\<0%s\>]**

**Cause:** The replication metadata item does not exist due to a database error.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x6109C ( 397468) rpERR_ABORT_CONVERT_ENDIAN Endian conversion operation
failed**

**Cause:** A server with different Endians failed to convert the Endians during
replication.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x6109E ( 397470) rpERR_ABORT_NOT_EXIST_TABLE [Receiver] The specified table
doesn't exist.**

**Cause:** The table does not exist.

**Action:** Check the altibase_rp.log file.

**0x6109F ( 397471) rpERR_ABORT_RP_ALREADY_STARTED_RECEIVER The receiver has
already been started.**

**Cause:** The receiver has already been started.

**Action:** Check whether the receiver has already been started.

**0x610A0 ( 397472) rpERR_ABORT_GIVEUP_SENDER_STOP [Sender] Stopping \<0%s\>
sender thread (sender read = SN[\<1%ld\>], current = SN[\<2%ld\>], distance from
checkpoint = \<3%ld\>)**

**Cause:** The system tried to restart the sender thread with the current log
file as specified by the REPLICATION_MAX_LOGFILE property.

**Action:** Check the status of the replication object, then synchronize the
replication data and then restart replication.

**0x610A1 ( 397473) rpERR_ABORT_GIVEUP_SENDER_RESET [Sender] Resetting \<0%s\>
sender XSN (sender XSN = SN[\<1%ld\>], current = SN[\<2%ld\>], distance from
checkpoint = \<3%ld\>)**

**Cause:** The system tried to change the current log file as specified by the
REPLICATION_MAX_LOGFILE property.

**Action:** Check the status of the replication object, then synchronize the
replication data and then restart replication.

**0x610A3 ( 397475) rpERR_ABORT_ROLE_NOT_SUPPORT_RECEIVER [Receiver] The
receiver is not supported in this role.**

**Cause:** The replication receiver is not supported in this role.

**Action:** Check the role of the replication.

**0x610A4 ( 397476) rpERR_ABORT_RECEIVER_UNEXPECTED_PROTOCOL [Receiver]
Unexpected replication protocol [\<0%u\>]**

**Cause:** The replication Receiver received an undefined protocol for
replication.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x610A5 ( 397477) rpERR_ABORT_RECEIVER_TX_NOT_BEGIN [Receiver] Transaction has
not begun. Received XLog [Type:\<0%d\>, TID:\<1%u\>, SN:\<2%ld\>]**

**Cause:** The replication Receiver received the XLog of a transaction that has
not yet started.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x610A6 ( 397478) rpERR_ABORT_LOGBUFFER_ALLOC Replication log buffer memory
allocation failed.**

**Cause:** The system failed to allocate memory.

**Action:** Verify that sufficient memory is available.

**0x610A7 ( 397479) rpERR_ABORT_RP_SENDER_UPDATE_INVALID_MAX_SN [Sender] Failed
to update INVALID MAX SN**

**Cause:** Failed to update replication metadata (INVALID MAX SN) due to a
database error.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x610A8 ( 397480) rpERR_ABORT_RECOVERY_INFO_EXIST Recovery information already
exists.**

**Cause:** Adding a table into or deleting a table from the replication is
prohibited if the recovery option is enabled.

**Action:** Disable the recovery option or create another replication and try
again.

**0x610A9 ( 397481) rpERR_ABORT_RECOVERY_ALREADY_STARTED The recovery sender has
already been started.**

**Cause:** The recovery sender has already been started.

**Action:** Wait for complete recovery or cancel the recovery.

**0x610AA ( 397482) rpERR_ABORT_RP_MAXIMUM_RECOVERYITEM_REACHED Irreplicable
recovery information**

**Cause:** The amount of available recovery information on the system exceeds
the maximum limit.

**Action:** Retry after

\# - 1. Increase value of the REPLICATION_MAX_COUNT property.

\# - 2. Remove the replication which enables other RECOVERY option.

\# - 3. Disable RECOVERY option.

**0x610AC ( 397484) rpERR_ABORT_GIVEUP_RECOVERY_DESTROY [Receiver] Destroy
\<0%s\> recovery information (recovery info min sn = SN[\<1%ld\>], distance from
checkpoint = \<2%ld\>)**

**Cause:** The number of logs that the replication Receiver stored for
replication recovery has exceeded REPLICATION_MAX_LOGFILE. Recovery data and log
files necessary for replication recovery have been dropped.

**Action:** To use the replication recovery option, increase the value of the
REPLICATION_MAX_LOGFILE property.

**0x610AD ( 397485) rpERR_ABORT_RP_RECOVERY_REQUEST Failed to send \<0%s\>
recovery request**

**Cause:** Failed to request replication recovery either because the
corresponding server has not started or there is a network error.

**Action:** Replication recovery is impossible if the corresponding server has
been terminated. To disable this option, set REPLICATION_RECOVERY_MAX_TIME to 0,
and restart. If a network error has occurred, increase
REPLICATION_RECOVERY_REQUEST_TIMEOUT, and restart replication. If connection
fails, check the error number from the trace log and contact Altibase’s Support
Center (http://support.altibase.com/en/).

**0x610B0 ( 397488) rpERR_ABORT_MISMATCH_OLD_ITEMS_COUNT Old items count
mismatch (\<0%d\>:\<1%d\>)**

**Cause:** The number of rows selected from SYS_REPL_OLD_ITEMS\_ is invalid due
to a database error.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x610B1 ( 397489) rpERR_ABORT_INVALID_CONDITION_NODE Failed to compare
conditions**

**Cause:** Failed to compare conditions.

**Action:** Check the condition node.

**0x610B2 ( 397490) rpERR_ABORT_CONDITION_COLUMN_IS_NOT_FOUND Condition column
not found.**

**Cause:** The condition column could not be found.

**Action:** Check the existence of a condition column.

**0x610B6 ( 397494) rpERR_ABORT_RECEIVER_NOT_FOUND_TABLE Table not found in the
meta [SN=\<0%ld\>, Table OID=\<1%ld\>]**

**Cause:** Failed to find the table with the table OID from replication Receiver
metadata due to a database error.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x610B7 ( 397495) rpERR_ABORT_RECEIVER_NOT_FOUND_PK_COLUMN PK Column not found
in the meta [SN=\<0%ld\>, Table OID=\<1%ld\>, PK Column Seq=\<2%d\>]**

**Cause:** Failed to find the primary key column from metadata due to a database
error.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x610B8 ( 397496) rpERR_ABORT_RECEIVER_NOT_FOUND_COLUMN Column not found in
the meta [SN=\<0%ld\>, Table OID=\<1%ld\>, Column ID=\<2%d\>]**

**Cause:** Failed to find the column from metadata due to a database error.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x610B9 ( 397497) rpERR_ABORT_RP_NOT_DROP_ONE_HOST You cannot drop only one
host.**

\# Cause: Replication cannot be dropped when only one host is remaining.

**Action:** Drop the replication object, or insert another host and drop the
host.

**0x610BA ( 397498) rpERR_ABORT_RP_ABORT_PSM_SVP [Receiver] smiTrans abort PSM
savepoint error in run()**

**Cause:** The replication receiver failed to abort to the savepoint.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x610BB ( 397499) rpERR_ABORT_MISMATCH_OFFLINE_LOG_LFGCOUNT Offline log LFG
counts do not match.**

**Cause:** The sender and receiver offline log LFG counts do not match.

**Action:** Check the LFG counts.

**0x610BC ( 397500) rpERR_ABORT_MISMATCH_OFFLINE_LOG_OSVERSION Offline log
system OS versions do not match.**

**Cause:** The sender and receiver offline log system OS versions do not match.

**Action:** Confirm that the operating systems of Active and Standby server are
the same or unset OFFLINE option.

**0x610BD ( 397501) rpERR_ABORT_MISMATCH_OFFLINE_LOG_SMVERSION Offline log SM
versions do not match.**

**Cause:** The sender and receiver offline log SM versions do not match.

**Action:** Confirm that the database versions of Active and Standby server are
the same or unset OFFLINE option.

**0x610BE ( 397502) rpERR_ABORT_MISMATCH_OFFLINE_LOG_COMPILEBIT Offline log
compile bits do not match.**

**Cause:** The sender and receiver offline log compile bits do not match.

**Action:** Confirm that the compile bit versions of Active and Standby server
are the same or unset OFFLINE option.

**0x610BF ( 397503) rpERR_ABORT_SENDER_NOT_FOUND_COLUMN Column not found in the
meta.**

**Cause:** Failed to find the column from metadata due to a database error.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x610C0 ( 397504) rpERR_ABORT_MISMATCH_OFFLINE_LOG_FILESIZE Offline log file
size does not match.**

**Cause:** The sender and receiver offline log file sizes do not match.

**Action:** Check the log file size.

**0x610C1 ( 397505) rpERR_ABORT_INVALID_CM_VARIABLE_SIZE Invalid CM variable
size [\<0%s\>]**

**Cause:** Internal communication logic error.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x610C2 ( 397506) rpERR_ABORT_RP_NOT_FOUND_OFFMETA The meta information for
the offline sender cannot be found in memory.**

**Cause:** The remote sender has not been started since the local server was
started.

**Action:** Start the replication in the remote server.

**0x610C3 ( 397507) rpERR_ABORT_INVALID_OFFLINE_RESTARTSN [Offline Sender]
Failed to get valid XSN**

**Cause:** The replication stopped before XSN update.

**Action:** In this case, you cannot use the offline sender.

**0x610C4 ( 397508) rpERR_ABORT_NOT_EXIST_REPL_ITEM Replication items not
found.**

**Cause:**

\# - When the ALTER REPLICATION DROP TABLE statement is executed, the table is
not in the replication.

\# - When the ALTER REPLICATION REP START statement is executed, the table on
the sender (Active) side is not in the receiver (standby).

**Action:** Ensure that the replication table exists on both sides or that the
table is included in the replication.

**0x610C5 ( 397509) rpERR_ABORT_TX_ALLOC_TIMEOUT [Receiver] Transaction
allocation exceeds timeout.**

**Cause:** The transaction allocation failed because it timed out.

**Action:** Check transaction table status.

**0x610C6 ( 397510) rpERR_ABORT_INVALID_CONT_LOG Invalid log exists before
current analyzing log [SN:\<0%lu\>].**

**Cause:** The previously analyzed log has an invalid continue flag.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x610C7 ( 397511) rpERR_ABORT_RP_OFFLINE_SENDER_ABNORMALLY_EXIT Offline sender
exits without finishing some jobs.**

**Cause:** An offline replication Sender has exited without finishing some jobs.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com).

**0x610C8 ( 397512) rpERR_ABORT_RP_WRONG_OPERATION_TYPE Invalid Operation type
[\<0%u\>] of replication protocol.**

**Cause:** The replication protocol's operation type is invalid.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x610C9 ( 397513) rpERR_ABORT_RP_OVERFLOW Size of log record is greater than
size of replication log buffer.**

**Cause:** Replication is delayed or replication log buffer size is too small.

**Action:**

\# - Increase REPLICATION_LOG_BUFFER_SIZE and restart the system.

\# - Find and resolve cause of the delay.

**0x610CB ( 397515) rpERR_ABORT_REPLICATION_NAME_MISMATCH The replication name
does not match [\<0%s\>:\<1%s\>].**

**Cause:** The replication name does not match.

**Action:** Check the replication's name.

**0x610CC ( 397516) rpERR_ABORT_CONFLICT_RESOLUTION Master/Slave conflict
resolution of the replication is not allowed [\<0%d\>:\<1%d\>].**

**Cause:** The master/slave conflict resolution scheme for this replication
object is not allowed.

**Action:** Check the conflict resolution scheme of the replication object.

**0x610CD ( 397517) rpERR_ABORT_REPLICATION_ITEM_COUNT_MISMATCH The
replication's item count does not match [\<0%d\>:\<1%d\>].**

**Cause:** The replication item count mismatch.

**Action:** Check the replication items.

**0x610CE ( 397518) rpERR_ABORT_ROLE_MISMATCH The replication's role does not
match [\<0%d\>:\<1%d\>].**

**Cause:** The replication role mismatch.

**Action:** Check the replication role.

**0x610CF ( 397519) rpERR_ABORT_TRANSACTION_TABLE_SIZE_MISMATCH The transaction
table size of the replication does not match [\<0%u\>:\<1%u\>].**

**Cause:** Replication transaction table size mismatch.

**Action:** Check the transaction table size.

**0x610D0 ( 397520) rpERR_ABORT_OPTION_MISMATCH The replication's option does
not match [\<0%d\>:\<1%d\>].**

**Cause:** The replication's option mismatch.

**Action:** Check the replication's option.

**0x610D1 ( 397521) rpERR_ABORT_CHARACTER_SET_MISMATCH The character set of the
database does not match. (DB=[\<0%s\>:\<1%s\>], National=[\<2%s\>:\<3%s\>]).**

**Cause:** Database character set mismatch.

**Action:** Check the character set of the database.

**0x610D2 ( 397522) rpERR_ABORT_PRIMARY_KEY_COUNT_MISMATCH The primary key
column count of the replicated table does not match
[\<0%s\>(\<1%d\>):\<2%s\>(\<3%d\>)].**

**Cause:** The primary key column count of the replicated table mismatch.

**Action:** Check the primary key of the replicated table.

**0x610D3 ( 397523) rpERR_ABORT_USER_NAME_MISMATCH The user name of the
replicated table's owner does not match [\<0%s\>(\<1%s\>):\<2%s\>(\<3%s\>)].**

**Cause:** Replicated table's owner user name mismatch.

**Action:** Check the user name of the replicated table's owner.

**0x610D4 ( 397524) rpERR_ABORT_TABLE_NAME_MISMATCH The replicated table name
does not match [\<0%s\>:\<1%s\>].**

**Cause:** Replicated table name mismatch.

**Action:** Check the replicated table name.

**0x610D5 ( 397525) rpERR_ABORT_PARTITION_NAME_MISMATCH The partition name of
the replicated table does not match [\<0%s\>:\<1%s\>].**

**Cause:** Replicated table partition name mismatch.

**Action:** Check the partition name of the replicated table.

**0x610D6 ( 397526) rpERR_ABORT_PARTITION_METHOD_MISMATCH The partition method
of the replicated table does not match [\<0%s\>(\<1%d\>):\<2%s\>(\<3%d\>)].**

**Cause:** Replicated table partition method mismatch.

**Action:** Check the partition method of the replicated table.

**0x610D7 ( 397527) rpERR_ABORT_PARTITION_ORDER_MISMATCH The partition order of
the replicated table does not match [\<0%s\>(\<1%d\>):\<2%s\>(\<3%d\>)].**

**Cause:** Replicated table partition order mismatch.

**Action:** Check the partition order of the replicated table.

**0x610D8 ( 397528) rpERR_ABORT_UNIQUE_INDEX_COUNT_MISMATCH The unique index
count of the replicated table does not match [\<0%s\>:\<1%s\>].**

**Cause:** Replicated table unique index count mismatch.

**Action:** Check the unique index count of the replicated table.

**0x610D9 ( 397529) rpERR_ABORT_NON_REPLICATION_COLUMN_NOT_NULL The
non-replicated column of the replicated table has NOT NULL constraint.
[\<0%s\>:\<1%s\>(\<2%s\>)].**

**Cause:** The replicated table's non-replicated column has a NOT NULL
constraint.

**Action:** Check the non-replicated column of the replicated table.

**0x610DA ( 397530) rpERR_ABORT_COLUMN_TYPE_MISMATCH The column type of the
replicated table does not match.
[\<0%s\>.\<1%s\>(\<2%u\>):\<3%s\>.\<4%s\>(\<5%u\>)].**

**Cause:** Replicated table column type mismatch.

**Action:** Check the column type of the replicated table.

**0x610DB ( 397531) rpERR_ABORT_COLUMN_SIZE_MISMATCH The column size of the
replicated table does not match. [\<0%s\>(Name:\<1%s\>, Size:\<2%d\>,
Precision:\<3%d\>, Scale:\<4%d\>):\<5%s\>(Name:\<6%s\>, Size:\<7%d\>, Precision:
\<8%d\>, Scale: \<9%d\>)].**

**Cause:** Replicated table column size mismatch.

**Action:** Check the column size of the replicated table.

**0x610DC ( 397532) rpERR_ABORT_ENCRYPT_PRECISION_MISMATCH The encrypt precision
of the replicated table's column does not match. [\<0%s\>(Name:\<1%s\>,
Precision:\<2%d\>):\<3%s\>(Name:\<4%s\>, Precision: \<5%d\>)].**

**Cause:** Replicated table's column encryption precision mismatch.

**Action:** Check the the encrypt precision of the replicated table's column.

**0x610DD ( 397533) rpERR_ABORT_COLUMN_CHARACTER_SET_MISMATCH The column
character set of the replicated table does not match.
[\<0%s\>.\<1%s\>(\<2%u\>):\<3%s\>.\<4%s\>(\<5%u\>)].**

**Cause:** Replicated table's column character set mismatch.

**Action:** Check the column character set of the replicated table.

**0x610DE ( 397534) rpERR_ABORT_COLUMN_CONSTRAINT_MISMATCH NOT NULL constraints
of the replicated table's column does not match.
[\<0%s\>.\<1%s\>(\<2%d\>):\<3%s\>.\<4%s\>(\<5%d\>)].**

**Cause:** Replicated table's NOT NULL constraints mismatch.

**Action:** Check the column's constraint of the replicated table.

**0x610DF ( 397535) rpERR_ABORT_POLICY_MISMATCH The encrypt policy name of the
replicated table's column does not match. [\<0%s\>(Name:\<1%s\>,
Policy:\<2%s\>):\<3%s\>(Name:\<4%s\>, Policy:\<5%s\>)].**

**Cause:** Replicated table's column encryption policy name mismatch.

**Action:** Check the encrpyt policy name of the replicated table's column.

**0x610E0 ( 397536) rpERR_ABORT_POLICY_CODE_MISMATCH The encrypt policy code of
the replicated table's column does not match. [\<0%s\>(Name:\<1%s\>,
Policy:\<2%s\>):\<3%s\>(Name:\<4%s\>, Policy:\<5%s\>)].**

**Cause:** Replicated table's column encryption policy code mismatch.

**Action:** Check the encryption policy name of the replicated table's column.

**0x610E1 ( 397537) rpERR_ABORT_ECC_POLICY_MISMATCH The encrypted comparision
code policy name of the replicated table's column does not match.
[\<0%s\>(Name:\<1%s\>, ECC Policy:\<2%s\>):\<3%s\>(Name:\<4%s\>, ECC
Policy:\<5%s\>)].**

**Cause:** The replicated table's column encryption comparison code policy name
mismatch.

**Action:** Check the encrypted comparison code policy name of the replicated
table's column.

**0x610E2 ( 397538) rpERR_ABORT_ECC_POLICY_CODE_MISMATCH The encrypted
comparison policy code of the replicated table's column does not match.
[\<0%s\>(Name:\<1%s\>, ECC Policy:\<2%s\>):\<3%s\>(Name:\<4%s\>, ECC
Policy:\<5%s\>)].**

**Cause:** Replicated table's column encryption comparison code mismatch.

**Action:** Check the encrypted comparison code of the replicated table's
column.

**0x610E3 ( 397539) rpERR_ABORT_INDEX_NAME_MISMATCH The index name of the
replicated table does not match.
[\<0%s\>(Name:\<1%s\>):\<2%s\>(Name:\<3%s\>)].**

**Cause:** Replicated table index name mismatch.

**Action:** Check the index name of the replicated table.

**0x610E4 ( 397540) rpERR_ABORT_INDEX_TYPE_MISMATCH The index type of the
replicated table does not match. [\<0%s\>(Name:\<1%s\>,
Type:\<2%u\>):\<3%s\>(Name:\<4%s\>, Type:\<5%u\>)].**

**Cause:** Replicated table index name mismatch.

**Action:** Check the index name of the replicated table.

**0x610E5 ( 397541) rpERR_ABORT_INDEX_UNIQUENESS_MISMATCH The index uniqueness
of the replicated table does not match. [\<0%s\>(Name:\<1%s\>,
Uniqueness:\<2%d\>):\<3%s\>(Name:\<4%s\>, Uniqueness:\<5%d\>)].**

**Cause:** Replicated table index uniqueness mismatch.

**Action:** Check the index uniqueness of the replicated table.

**0x610E6 ( 397542) rpERR_ABORT_LOCAL_INDEX_UNIQUENESS_MISMATCH The local index
uniqueness of the replicated table does not match. [\<0%s\>(Name:\<1%s\>,
Uniqueness:\<2%d\>):\<3%s\>(Name:\<4%s\>, Uniqueness:\<5%d\>)].**

**Cause:** Replicated table local index uniqueness mismatch.

**Action:** Check the local index uniqueness of the replicated table.

**0x610E7 ( 397543) rpERR_ABORT_INDEX_COLUMN_COUNT_MISMATCH The index column
count of the replicated table does not match. [\<0%s\>(Name:\<1%s\>,
Count:\<2%u\>):\<3%s\>(Name:\<4%s\>, Count:\<5%u\>)].**

**Cause:** Replicated table index column count mismatch.

**Action:** Check the index column count of the replicated table.

**0x610E8 ( 397544) rpERR_ABORT_INDEX_COLUMN_ID_MISMATCH The index column ID of
the replicated table does not match. [\<0%s\>(Name:\<1%s\>,
ID:\<2%u\>):\<3%s\>(Name:\<4%s\>, ID:\<5%u\>)].**

**Cause:** Replicated table index column ID mismatch.

**Action:** Check the index column ID of the replicated table.

**0x610E9 ( 397545) rpERR_ABORT_INDEX_COLUMN_ORDER_MISMATCH The index column
order of the replicated table does not match. [\<0%s\>(Name:\<1%s\>, ID:\<2%d\>,
Flag:\<3%d\>):\<4%s\>(Name:\<5%s\>, ID:\<6%d\>, Flag:\<7%d\>)].**

**Cause:** Replicated table index column order mismatch.

**Action:** Check the index column order of the replicated table.

**0x610EA ( 397546) rpERR_ABORT_MIXED_UNIQUE_INDEX_COLUMN The unique index of
the replicated table is composed of replication column and non-replication
column [\<0%s\>(\<1%s\>)].**

**Cause:** The unique index of the replicated table is composed of a replication
column and a non-replication column.

**Action:** Check the unique index of the replicated table.

**0x610ED ( 397549) rpERR_ABORT_CANCEL_COMMIT_BY_REPL Transaction's commit was
canceled by replication conflict.**

**Cause:** Replication conflict occurred in the standby host.

**Action:** Execute rollback and check your application update logic.

**0x610EF ( 397551) rpERR_ABORT_ABNORMAL_TYPE [\<0%s\>:\<1%u\>] sender have
abnormal type.**

**Cause:** The replication Sender type is set to an invalid value.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x610F1 ( 397553) rpERR_ABORT_RP_SENDER_UPDATE_REMOTE_FAULT_DETECT_TIME
[Sender] Failed to update REMOTE_FAULT_DETECT_TIME**

**Cause:** Failed to update the REMOTE_FAULT_DETECT_TIME column in the
SYS_REPLICATIONS\_ meta table due to a database error.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x610F2 ( 397554) rpERR_ABORT_SENDER_APPLY_ABNORMAL_EXIT [Sender] The apply
thread exits abnormally.**

**Cause:** While the replication Sender was terminating, a related thread
terminated abnormally due to a network error.

**Action:** Some data may have been unsent. Restart the replication Sender and
then stop it, to terminate it normally.

**0x610F3 ( 397555) rpERR_ABORT_FAILBACK_SENDER_NOT_EXIST [Receiver] Failback
sender does not exist.**

**Cause:** Failback sender does not exist.

**Action:** Check the status of the replication sender.

**0x610F4 ( 397556) rpERR_ABORT_FAILBACK_PK_QUEUE_TIMEOUT_EXCEED [Receiver] The
queue for failback is full.**

**Cause:** The queue for failback is full.

**Action:** Check status of the replication sender.

**0x610F5 ( 397557) rpERR_ABORT_FAILBACK_INCREMENTAL_SYNC_MISMATCH The
REPLICATION_FAILBACK_INCREMENTAL_SYNC property mismatch. [\<0%u\>:\<1%u\>]**

**Cause:** The REPLICATION_FAILBACK_INCREMENTAL_SYNC property mismatch.

**Action:** Check the REPLICATION_FAILBACK_INCREMENTAL_SYNC property.

**0x610F6 ( 397558) rpERR_ABORT_RP_LOG_BUFFER_PROPERTY_CONFLICT The replication
log buffer cannot be used when the REPLICATION_SYNC_LOG property is 1.**

**Cause:** The REPLICATION_LOG_BUFFER_SIZE property is greater than 0 and the
REPLICATION_SYNC_LOG property is 1.

**Action:** Check the REPLICATION_LOG_BUFFER_SIZE and REPLICATION_SYNC_LOG
properties.

**0x610F7 ( 397559) rpERR_ABORT_NOT_FOUND_RECORD [Receiver] Unable to find
record in \<0%s\> function**

**Cause:** The record does not exist.

**Action:**

\# - Find the conflicted record in altibase_rp.log or altibase_rp_conflict.log
file and match the data or find and resolve the cause of the conflict (such as
app logic).

\# - In case that there is no primary key information for the log about conflict
in altibase_rp.log or altibase_rp_conflict.log file, set the third bit of
RP_MSGLOG_FLAG or the RP_CONFLICT_MSGLOG_FLAG to output the primary key
information into the log.

\# - It is possible to match the data using tools such as AltiComp if conflict
has already occurred.

**0x610F8 ( 397560) rpERR_ABORT_RP_SENDER_ADD_XLOG [Sender] Failed to add a XLog
[TID:\<0%u\>, SN:\<1%lu\>, Type:\<2%d\>, Log Type:\<3%d\>, Change Log
Type:\<4%d\>]**

**Cause:** The replication Sender failed to create an XLog from a log.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x610FB ( 397563) rpERR_ABORT_UNEXPECTED_HANDSHAKE_ACK Unexpected replication
handshake ACK [Result:\<0%u\>]**

**Cause:** The replication Sender received an unexpected ACK while handshaking
the replication Receiver.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com).

**0x610FC ( 397564) rpERR_ABORT_HANDSHAKE_DISCONNECT Disconnection during
handshaking [\<0%s\>]**

**Cause:** A network error has occurred.

**Action:** Check the network status and ensure that all systems are connected
to the network.

**0x610FD ( 397565) rpERR_ABORT_SENDER_INFO_NOT_EXIST No Sender information for
replication \<0%s\>.**

**Cause:** There is no information about the replication Sender.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x610FE ( 397566) rpERR_ABORT_RPC_REPLICATION_ALREADY_STARTED Replication has
already started.**

**Cause:** Replication is currently underway.

**Action:** Stop the current replication to start again.

**0x610FF ( 397567) rpERR_ABORT_RPC_NOT_SUPPORT_REPLICATION_DDL This replication
DDL is no longer supported.**

**Cause:** An attempt to use a deprecated DDL statement was made.

**Action:** Refer to the Replication User's Manual.

**0x61100 ( 397568) rpERR_ABORT_RPC_DUPLICATE_REPLICATION Duplicate replication
names. The replication name already exists in the database.**

**Cause:** The replication name already exists in the database. The IP address
and the port number must be unique.

**Action:** Use another replication name. Consult the meta tables in order to
find replications that use the same IP address and port number.

**0x61101 ( 397569) rpERR_ABORT_RPC_DUPLICATE_REPL_OPTION Duplicate option
names.**

**Cause:** Duplicate option names exist.

**Action:** Check option names for duplicates.

**0x61102 ( 397570) rpERR_ABORT_RPC_MAX_REPLICATION_COUNT No more replications
may be created. A database cannot have more than the maximum number of
replications.**

**Cause:** A database cannot have more than the maximum number of replications.

**Action:** Decrease the number of replications or increase the value of
REPLICATION_MAX_COUNT property.

**0x61103 ( 397571) rpERR_ABORT_RPC_ROLE_NOT_SUPPORT_UNIX_DOMAIN UNIX domain
socket is not supported in this role.**

**Cause:** This role does not support UNIX_DOMAIN in the 'WITH' clause.

**Action:** Check the role of the replication.

**0x61104 ( 397572) rpERR_ABORT_RPC_ROLE_SUPPORT_ONE_SOCKET_TYPE One socket type
is supported in this role.**

**Cause:** This role supports one socket type.

**Action:** Check the role of the replication.

**0x61105 ( 397573) rpERR_ABORT_RPC_ROLE_SUPPORT_ONE_UNIX_DOMAIN Only one UNIX
domain socket is supported in this role.**

**Cause:** This role supports one UNIX domain socket.

**Action:** Check the role of the replication.

**0x61106 ( 397574) rpERR_ABORT_RPC_ROLE_NOT_SUPPORT_REPL_RECOVERY Recovery
option not supported in this role.**

**Cause:** This role does not support the recovery option.

**Action:** Check the options or the role of the replication.

**0x61107 ( 397575) rpERR_ABORT_RPC_NOT_SUPPORT_REPL_OFFLINE_AND_RECOVERY
Offline option is not supported with recovery option.**

**Cause:** Offline option is not supported with the recovery option.

**Action:** Check the replication options.

**0x61108 ( 397576) rpERR_ABORT_RPC_NOT_SUPPORT_REPL_OFFLINE_AND_EAGER The
offline option is not supported with eager mode.**

**Cause:** Simultaneous use of eager mode and the offline option is not
supported.

**Action:** Change the option or mode of the replication.

**0x61109 ( 397577) rpERR_ABORT_RPC_ROLE_NOT_SUPPORT_REPL_OFFLINE Offline option
not supported in this role.**

**Cause:** This role does not support the offline option.

**Action:** Check the options or the role of the replication.

**0x6110A ( 397578) rpERR_ABORT_RPC_ROLE_NOT_SUPPORT_DEFAULT_REPL_MODE The
default replication mode is not supported in this role.**

**Cause:** This role does not support the default replication mode.

**Action:** Check the role of the replication.

**0x6110B ( 397579) rpERR_ABORT_RPC_INVALID_HOST_IP_PORT The host IP address or
port number is invalid.**

**Cause:** Invalid host IP address or port number.

**Action:** Check the host IP address and port number.

**0x6110C ( 397580) rpERR_ABORT_RPC_ALREADY_EXIST_REPL_HOST Replication hosts
already exist.**

**Cause:** Replication hosts already exist.

**Action:** Check the meta tables.

**0x6110D ( 397581) rpERR_ABORT_RPC_REPLICATED_OBJECT_TYPE The replicated object
type must be a table. \<0%s\>**

**Cause:** Only a table may be replicated.

**Action:** Check the object type.

**0x6110E ( 397582) rpERR_ABORT_RPC_NOT_EXIST_USER User not found**

**Cause:**

\# - The user is not in the meta database.

**Action:**

\# - Check the error number from the trace log and contact Altibase's Support
Center (http://support.altibase.com/en/).

**0x6110F ( 397583) rpERR_ABORT_RPC_NOT_EXISTS_USER User not found : \<0%s\>**

**Cause:** The name of the specified user was not found in the database.

**Action:** Verify that the user exists in the database.

**0x61110 ( 397584) rpERR_ABORT_RPC_NOT_EXIST_TABLE Table not found**

**Cause:**

\# - The table is not in the meta database.

**Action:**

\# - Check the error number from the trace log and contact Altibase's Support
Center (http://support.altibase.com).

**0x61111 ( 397585) rpERR_ABORT_RPC_NOT_EXISTS_TABLE Table not found : \<0%s\>**

**Cause:** The name of the specified table was not found in the database.

**Action:** Verify that the table exists in the database. Verify that there are
no typos in the table name.

**0x61112 ( 397586) rpERR_ABORT_RPC_REPLICATE_TABLE_WITH_REFERENCE Replication
is not allowed on tables that have referential constraints. (\<0%s\>.\<1%s\>)**

**Cause:** The user tried to replicate a table that has referential constraints.

**Action:** Verify that the table to be replicated does not have any referential
constraints.

**0x61113 ( 397587) rpERR_ABORT_RPC_NOT_EXISTS_PRIMARY_KEY A replicated table
must have a primary key. (\<0%s\>.\<1%s\>)**

**Cause:** No primary key was found in the table to be replicated. For
replication, specify a table having a primary key.

**Action:** Create a primary key for the table to be replicated.

**0x61114 ( 397588) rpERR_ABORT_RPC_REPL_RECOVERY_COUNT A table can recover only
one replication.**

**Cause:** Table recovery already supported by another replication.

**Action:** Check the replication recovery count.

**0x61115 ( 397589) rpERR_ABORT_RPC_NOT_APPLICABLE_POLICY This column policy is
not compatible with replication. [\<0%s\>]**

**Cause:** This column policy is not compatible with replication.

**Action:** Check the column policy.

**0x61116 ( 397590) rpERR_ABORT_RPC_CANNOT_USE_VOLATILE_TABLE Replication not
allowed on volatile tables.**

**Cause:** A volatile table cannot be replicated.

**Action:** Verify that the table to be replicated is not a volatile table.

**0x61117 ( 397591) rpERR_ABORT_RPC_CANNOT_USE_TEMPORARY_TABLE Temporary tables
cannot be replicated.**

**Cause:** An attempt was made to add a temporary table to a replication object.

**Action:** Verify that none of the tables to be replicated are temporary
tables.

**0x61118 ( 397592) rpERR_ABORT_RPC_NOT_SUPPORT_MAX_ROWS_AND_EAGER Replication
in eager mode is not supported with the MAX ROWS table option.**

**Cause:** A table with the MAX_ROWS option specified cannot be replicated in
eager mode.

**Action:** Check the replication mode.

**0x61119 ( 397593) rpERR_ABORT_RPC_NOT_ALLOW_ADD_TABLE An ADD TABLE statement
is not allowed in recovery support replication.**

**Cause:** An ADD TABLE statement is not allowed in a recovery support
replication.

**Action:** Check the replication options.

**0x6111A ( 397594) rpERR_ABORT_RPC_NOT_EXIST_REPL_ITEM No replication items
found.**

**Cause:** No replication items were found.

**Action:** Check the meta tables.

**0x6111B ( 397595) rpERR_ABORT_RPC_NOT_EXIST_REPLICATION Undefined replication
name. The replication name was not found in the database.**

**Cause:** The replication name was not found in the database. The name is
incorrect or the replication has not been created yet.

**Action:** Verify that the replication name is typed correctly. Consult meta
tables to see if the same replication name exists in the database.

**0x6111C ( 397596) rpERR_ABORT_RPC_ALREADY_RECOVERY_SET Recovery option already
set.**

**Cause:** The replication recovery option has already been set.

**Action:** Check the replication options.

**0x6111D ( 397597) rpERR_ABORT_RPC_ALREADY_RECOVERY_UNSET The recovery option
was already unset.**

**Cause:** The replication recovery option was already unset.

**Action:** Check the replication options.

**0x6111E ( 397598) rpERR_ABORT_RPC_NOT_ALLOW_DROP_TABLE An DROP TABLE statement
is not allowed in recovery support replication.**

**Cause:** A DROP TABLE statement is not allowed in recovery support
replication.

**Action:** Check the replication options.

**0x6111F ( 397599) rpERR_ABORT_RPC_NOT_EXIST_REPL_HOST Replication hosts not
found.**

**Cause:** No replication hosts were found.

**Action:** Check the meta tables.

**0x61120 ( 397600) rpERR_ABORT_RPC_NOT_SUPPORT_AT_SN_CLAUSE Replication cannot
start from a specific SN unless it is used with the Log Analyzer.**

**Cause:** The AT SN clause was specified, but the role of the replication
object is not "Log Analyzer".

**Action:** Either specify the FOR ANALYSIS clause in the CREATE REPLICATION
statement, or do not use the AT SN clause in the ALTER REPLICATION statement.

**0x61121 ( 397601) rpERR_ABORT_RPC_NOT_SUPPORT_RETRY_AND_EAGER The retry option
is not supported when replication is running in eager mode.**

**Cause:** The retry option is not supported in eager mode.

**Action:** Either remove the retry option or change the replication mode.

**0x61122 ( 397602) rpERR_ABORT_RPC_ROLE_NOT_SUPPORT_SYNC Replication SYNC is
not supported in this role.**

**Cause:** This role does not support SYNC.

**Action:** Check the role of the replication.

**0x61123 ( 397603) rpERR_ABORT_RPC_ALREADY_OFFLINE_SET Offline option already
set.**

**Cause:** The replication offline option was already set.

**Action:** Check the replication options.

**0x61124 ( 397604) rpERR_ABORT_RPC_ALREADY_OFFLINE_UNSET Offline option already
unset.**

**Cause:** The replication offline option was already unset.

**Action:** Check the replication options.

**0x61126 ( 397606) rpERR_ABORT_RPD_REPL_NOT_FOUND Replication not found**

**Cause:** The specified replication has not been created yet.

**Action:** Create the replication first. Verify that the replication name is
valid.

**0x61127 ( 397607) rpERR_ABORT_RPD_INTERNAL_ARG Internal server error in meta
module (\<0%s\>).**

**Cause:** Failed to execute DML on replication metadata due to a database
error.

**Action** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x61128 ( 397608) rpERR_ABORT_RPD_TOO_MANY_REPLICATION_OLD_ITEMS Internal
server error. There are too many old item metas for replication. (\<0%s\>)**

**Cause:** A larger number of rows than those existing were returned from
SYS_REPL_OLD_ITEMS_. This is an internal server error.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x61129 ( 397609) rpERR_ABORT_RPD_NOT_ENOUGH_REPLICATION_OLD_ITEMS Internal
server error. There are too few old item metas for replication. (\<0%s\>)**

**Cause:** A smaller number of rows than those existing were returned from
SYS_REPL_OLD_ITEMS_. This is an internal server error.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x6112A ( 397610) rpERR_ABORT_RPD_NOT_EXIST_REPL_OFFLINE_DIR_PATH Replication
offline log dir not found.**

**Cause:** No replication offline log directory path was found.

**Action:** Check the meta tables.

**0x6112B ( 397611) rpERR_ABORT_RPD_TOO_MANY_REPLICATION_OFFLINE_DIR_PATH
Internal server error. Too many offline log dir paths for replication.**

**Cause:** Too many directories were specified for offline replication.

**Action:** Specify only one directory.

**0x6112C ( 397612) rpERR_ABORT_RPD_NOT_ENOUGH_REPLICATION_OFFLINE_DIR_PATH
Internal server error. Too few offline log dir paths for replication.**

**Cause:** A directory has not been specified for offline replication.

**Action:** Specify a directory.

**0x6112D ( 397613) rpERR_ABORT_RPD_MAX_REPLICATION Internal server error.**

**Cause:** This is an internal error related to metadata of the replication
object.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x6112E ( 397614) rpERR_ABORT_RPD_TOO_MANY_REPLICATION_HOSTS Internal server
error. There are too many hosts for replication.**

**Cause:** This is an internal error related to metadata of replication hosts.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x6112F ( 397615) rpERR_ABORT_RPD_NOT_ENOUGH_REPLICATION_HOSTS Internal server
error. There are too few hosts for replication.**

**Cause:** This is an internal error related to metadata of replication hosts.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x61130 ( 397616) rpERR_ABORT_RPD_TOO_MANY_REPLICATION_ITEMS Internal server
error. There are too many tables for replication.**

**Cause:** This is an internal error related to SYS_REPL_ITEMS\_ .

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x61131 ( 397617) rpERR_ABORT_RPD_NOT_ENOUGH_REPLICATION_ITEMS Internal server
error. There are too few tables for replication.**

**Cause:** This is an internal error related to SYS_REPL_ITEMS_.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x61132 ( 397618) rpERR_ABORT_RPD_MAXIMUM_OBJECT_NUMBER_EXCEED The number of
elements \<0%s\> exceeds the maximum limit (\<1%ld\>).**

**Cause:** The specified number of elements exceeds the maximum limit.

**Action:** Reduce the specified number of elements.

**0x61133 ( 397619) rpERR_ABORT_RPD_TOO_MANY_REPLICATION_OLD_COLUMNS Internal
server error. There are too many old column metas for replication. (\<0%s\>,
\<1%lu\>)**

**Cause:** This is an internal error related to SYS_REPL_ITEMS_.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x61134 ( 397620) rpERR_ABORT_RPD_NOT_ENOUGH_REPLICATION_OLD_COLUMNS Internal
server error. There are too few old column metas for replication. (\<0%s\>,
\<1%lu\>)**

**Cause:** This is an internal error related to SYS_REPL_ITEMS_.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x61135 ( 397621) rpERR_ABORT_RPD_TOO_MANY_REPLICATION_OLD_INDICES Internal
server error. There are too many old index metas for replication. (\<0%s\>,
\<1%lu\>)**

**Cause:** This is an internal error related to SYS_REPL_ITEMS_.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x61136 ( 397622) rpERR_ABORT_RPD_NOT_ENOUGH_REPLICATION_OLD_INDICES Internal
server error. There are too few old index metas for replication. (\<0%s\>,
\<1%lu\>)**

**Cause:** This is an internal error related to SYS_REPL_ITEMS_.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x61137 ( 397623) rpERR_ABORT_RPD_TOO_MANY_REPLICATION_OLD_INDEX_COLS Internal
server error. There are too many old index column metas for replication.
(\<0%s\>, \<1%lu\>, \<2%u\>)**

**Cause:** This is an internal error related to SYS_REPL_ITEMS_.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x61138 ( 397624) rpERR_ABORT_RPD_NOT_ENOUGH_REPLICATION_OLD_INDEX_COLS
Internal server error. There are too few old index column metas for replication.
(\<0%s\>, \<1%lu\>, \<2%u\>)**

**Cause:** This is an internal error related to SYS_REPL_ITEMS_.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x61139 ( 397625) rpERR_ABORT_RPD_ALREADY_SUPPORT_RECOVERY The table recovery
is already supported by another replication \<0%s\>**

**Cause:** The recovery of this table is already supported by an existing
replication.

**Action:** Check the replication item.

**0x6113A ( 397626) rpERR_ABORT_NOT_EXIST_SYNC_TABLE A table to be synchronized
does not exist.**

**Cause:** The table is not a replication target object.

**Action:** Check whether the table is a replication target object.

**0x6113B ( 397627) rpERR_ABORT_SEND_SYNC_TABLES Failed to send information
about a table to synchronize.**

**Cause:** A network error has occurred.

**Action:** Check the network status and ensure that all systems are connected
to the network.

**0x6113C ( 397628) rpERR_ABORT_INVALID_SYNC_TABLE_NUMBER The number of tables
to be synchronized is invalid.**

**Cause:** The number of tables to be synchronized is invalid.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x6113D ( 397629) rpERR_ABORT_REBUILD_INDEX Failed to rebuild indexes after
synchronization operation.**

**Cause:** The table may be locked, or meta information may be corrupted.

**Action:** Wait for the lock to be released and then try again.

**0x6113E ( 397630) rpERR_ABORT_RP_SYNC Synchronization failed. Indexes on the
remote server may have been inconsistent.**

**Cause:** Check the log files on the remote server to determine the cause of
failure.

**Action:** Identify and rectify the cause of synchronization failure.
Additionally, check whether indexes on the remote server have been inconsistent,
and rebuild the indexes if necessary.

**0x6113F ( 397631) rpERR_ABORT_SEND_SYNC_START Failed to send signal starting
replication synchronization.**

**Cause:** A network error has most likely occurred.

**Action:** Check the network status and ensure that all systems are connected
to the network.

**0x61140 ( 397632) rpERR_ABORT_LOCK_TABLE Failed to lock table for replication
synchronization.**

**Cause:** A lock conflict occurred.

**Action:** Wait for the lock to be released or manually release the lock.

**0x61141 ( 397633) rpERR_ABORT_SEND_SYNC_TABLES_NUMBER Failed to send
information about the number of tables to synchronize.**

**Cause:** A network error has most likely occurred.

**Action:** Check the network status and ensure that all systems are connected
to the network.

**0x61142 ( 397634) rpERR_ABORT_ALLOC_CM_BLOCK [Network] Allocate communication
block failed**

**Cause:** Failed to allocate network resources.

**Action:** Check the state of system resources. If they are insufficient, take
appropriate action.

**0x61143 ( 397635) rpERR_ABORT_FREE_CM_BLOCK [Network] Free communication block
failed**

**Cause:** Failed to free network memory resources.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x61144 ( 397636) rpERR_ABORT_LOB_TRIM [SmExec] A failure occurred while
trimming LOB type data**

**Cause:** Failed to trim LOB data.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x61145 ( 397637)
rpERR_ABORT_RPC_CANNOT_REPLICATE_TABLE_WITH_COMPRESSED_COLUMN Replication is not
allowed on tables that have compressed column.**

**Cause:** A table with a compressed column cannot be replicated.

**Action:** Verify that the table to be replicated does not have any compressed
columns.

**0x61146 ( 397638) rpERR_ABORT_INVALID_PACKET_TYPE Invalid communication packet
type**

**Cause:** An invalid communication packet type has been detected.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x61147 ( 397639) rpERR_ABORT_CHECK_NAME_NOT_FOUND Check constraint name of
the replicated table does not exist. [\<0%s\>(Name: \<1%s\>)]**

**Cause:** The check constraint name of the replicated table does not match.

**Action:** Check the check constraint name.

**0x61148 ( 397640) rpERR_ABORT_CHECK_CONDITION_MISMATCH Check constraint
condition string of the replicated table mismatch. [\<0%s\>(Condition String:
\<1%s\>):\<2%s\>(Condition String: \<3%s\>)]**

**Cause:** The check constraint condition string for both tables does not match.

**Action:** Check the condition string in check constraint.

**0x61149 ( 397641) rpERR_ABORT_CHECK_COLUMN_NOT_REPL Check Constraint is
composed of replication column and non-replication column [\<0%s\>(\<1%s\>)]**

**Cause:** The check constraint column composition does not match.

**Action:** Check the column in check constraint.

**0x6114A ( 397642) rpERR_ABORT_FUNC_BASED_INDEX_EXPRESSION_MISMATCH
Function-based index expression string of the replicated table mismatch.
[\<0%s\>(Name:\<1%s\>, Expression String:\<2%s\>:\<3%s\>(Name:\<4%s\>,
Expression String:\<5%s\>)]**

**Cause:** The function-based index expression string is not the same as the
corresponding table.

**Action:** Check the expression string in the function-based index.

**0x6114B ( 397643) rpERR_ABORT_FUNC_BASED_INDEX_COUNT_MISMATCH Function-based
index count of the replicated table does not equal. [\<0%s\>:\<1%s\>]**

**Cause:** The function-based index count of the replicated table does not
match.

**Action:** Check the function-based index.

**0x6114C ( 397644) rpERR_ABORT_COLUMN_HIDDEN_MISMATCH Hidden columns
mismatch.[\<0%s\>.\<1%s\>(\<2%u\>):\<3%s\>.\<4%s\>(\<5%u\>)]**

**Cause:** The hidden column names and the regular column names are identical
for the replication target tables.

**Action:** Check whether the hidden column names and the regular column names
are identical.

**0x6114D ( 397645) rpERR_ABORT_FUNC_BASED_INDEX_COLUMN_NOT_REPL Function-based
index is composed of replication column and non-replication column
[\<%0s\>(\<%1s\>)]**

**Cause:** The function based index is composed of a replicated column and a
non-replicated column.

**Action:** Check the composition of the function based index.

**0x6114E ( 397646) rpERR_ABORT_COMPATIBILITY_BETWEEN_TABLE_AND_PARTITION The
replication units mismatch: \<0%s\>**

**Cause:** The replication unit (table or partition) to be dropped or synced is not the same as the existing replication unit.

**Action:** Check whether the specified replication unit exists in the partition_unit column of the SYS_REPL_IMTES\_ meta table.

**0x6114F ( 397647) rpERR_ABORT_RPC_NOT_EXISTS_PARTITION Partition not found :
\<0%s\>**

**Cause:** The name of the specified partition was not found in the specified
table.

**Action:** Verify that the partition exists in the database. Verify that there
are no typos in the partition name.

**0x61150 ( 397648) rpERR_ABORT_RPC_EXISTS_OFFLINE_OPTION_COMPRESSED_COLUMN
Offline replication cannot be performed on a compressed table.
[\<0%s\>.\<1%s\>]**

**Cause:** Offline replication cannot be performed on a compressed table.

**Action:** Check whether the specified table is compressed or not.

**0x61151 ( 397649)
rpERR_ABORT_RPC_NOT_SUPPORT_OFFLINE_REPLICATE_TABLE_WITH_COMPRESSED_COLUMN
Compressed tables do not support offline replication.**

**Cause:** Compressed tables do not support offline replication.

**Action:** Check whether the specified table is compressed or not.

**0x61152 ( 397650) rpERR_ABORT_RP_SYNC_WITH_INDEX_CAUTION Replication
synchronization failed. Check whether the index on the remote server is
consistent.**

**Cause:** Check logs on the local and remote servers for the cause of failure.

**Action:** Check whether the index on the remote server is inconsistent and
rebuild it, if necessary.

**0x61153 ( 397651) rpERR_ABORT_RP_SYNC_WITHOUT_INDEX_CAUTION Replication
synchronization failed.**

**Cause:** Check logs on the local and remote servers for the cause of failure.

**Action:** Check the cause for synchronization failure and fix it.

**0x61154 ( 397652) rpERR_ABORT_INSERT_GLOBAL_INDEX_TABLE Failed to insert the
record to the global index table.**

**Cause:** Inserting data into a partition and a global index failed while
duplicating a partition with a global index.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x61155 ( 397653) rpERR_ABORT_UPDATE_GLOBAL_INDEX_TABLE Failed to update the
record to the global index table.**

**Cause:** Updating data on a partition and a global index failed while
duplicating a partition with a global index.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x61156 ( 397654) rpERR_ABORT_DELETE_GLOBAL_INDEX_TABLE Failed to delete the
record from the global index table.**

**Cause:** Deleting data from a partition and a global index failed while
duplicating a partition with a global index.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x61157 ( 397655) rpERR_ABORT_RPD_OVERFLOW_COUNT_REPL_OFFLINE_DIR_PATH Exceeds
the maximum number of log directory paths allowed to be specified.**

**Cause:** Only one log directory path can be specified with the replication
offline option.

**Action:** Check the log directory path of the Active server.

**0x61158 ( 397656) rpERR_ABORT_DATA_STILL_REMAIN_IN_BUFFER If receive buffer
has been processed, no data should remain in the receive buffer.**

**Cause:** Already processed data remains in the replication receive buffer.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x61159 ( 397657) rpERR_ABORT_REPLICATION_MODE_MISMATCH The replication mode
does not match. [\<0%u\>:\<1%u\>]**

**Cause:** The mode of the replicated table mismatch.

**Action:** Please check the mode of the replicated table.

**0x6115A ( 397658) rpERR_ABORT_PARTITION_CONDITION_MISMATCH The partition
condition of the replicated table does not match. [\<0%s\>:\<1%s\>]**

**Cause:** The partition condition of the replicated table mismatch.

**Action:** Please check the partition condition of the replicated table.

**0x6115B ( 397659) rpERR_ABORT_NOT_SUPPORT_FEATURE_WITH_V6_PROTOCOL This
feature is not supported with \__REPLICATION_USE_V6_PROTOCOL property.
(\<0%s\>)**

**Cause:** When using A5 protocol, this feature is not surpported.

**Action:** Check the \__REPLICATION_USE_V6_PROTOCOL property or table schemes.

**0x6115C ( 397660) rpERR_ABORT_RPC_NOT_SUPPORT_REPL_GAPLESS_AND_EAGER The gap
control option is not supported with eager mode.**

**Cause:** Simultaneous use of eager mode and the gap control option is not
supported.

**Action:** Change the option or mode of the replication.

**0x6115D ( 397661) rpERR_ABORT_RPC_ALREADY_GAPLESS_SET The gapless option
already set.**

**Cause:** The replication gapless option has already been set.

**Action:** Check the replication options.

**0x6115E ( 397662) rpERR_ABORT_RPC_ALREADY_GAPLESS_UNSET The gapless option was
already unset.**

**Cause:** The replication gapless option was already unset.

**Action:** Check the replication options.

**0x6115F ( 397663) rpERR_ABORT_RPC_NOT_SUPPORT_REPL_PARALLEL_OPTION_AND_EAGER
The parallel option is not supported with eager mode.**

**Cause:** Simultaneous use of eager mode and the parallel option is not
supported.

**Action:** Change the option or mode of the replication.

**0x61160 ( 397664) rpERR_ABORT_RPC_NOT_PROPER_VALUE_FOR_PARALLEL_COUNT Invalid
the parallel count value. Valid value range = 0 \~ 512**

**Cause:** The value of parallel count is invalid.

**Action:** Spcify the value of parallel count whthin valid range.

**0x61161 ( 397665) rpERR_ABORT_RPC_ALREADY_PARALLEL_SET The parallel option
already set.**

**Cause:** The replication parallel option has already been set.

**Action:** Check the replication options.

**0x61162 ( 397666) rpERR_ABORT_RPC_ALREADY_PARALLEL_UNSET The parallel option
was already unset.**

**Cause:** The replication parallel option was already unset.

**Action:** Check the replication options.

**0x61163 ( 397667) rpERR_ABORT_RPC_ALREADY_GROUPING_SET The grouping option
already set.**

**Cause:** The grouping option has already been set.

**Action:** Check the replication options.

**0x61164 ( 397668) rpERR_ABORT_RPC_ALREADY_GROUPING_UNSET The grouping option
was already unset.**

**Cause:** The grouping option was already unset.

**Action:** Check the replication options.

**0x61165 ( 397669) rpERR_ABORT_RPC_NOT_SUPPORT_REPL_GROUPING_AND_EAGER The
grouping option is not supported with eager mode.**

**Cause:** Simultaneous use of eager mode and the grouping option is not
supported.

**Action:** Change the option or mode of the replication.

**0x61166 ( 397670) rpERR_ABORT_AHEAD_ANALYZER_TIMED_WAIT_ERROR Internal server
error. ( system call ( timedwait ) got error )**

**Cause:** cond_timedwait() returned false while the Ahead Analyzer for grouping
transaction was waiting after finishing the analysis in the replication with the
grouping option enabled.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x61168 ( 397672) rpERR_ABORT_TRANSACTION_NOT_ACTIVE Transaction is not
active.**

**Cause:** A transaction is not active.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x61169 ( 397673) rpERR_ABORT_SOCKET_OPEN_ERROR Socket Can not be openned.**

**Cause:** An error occurred while opening the socket.

**Action:** Please check the system resources

**0x6116A ( 397674) rpERR_ABORT_SOCKET_SET_BLOCK_MODE Socket can not be set as
block mode.**

**Cause:** An error occurred while setting a block mode to socket.

**Action:** Please check the network status.

**0x6116B ( 397675) rpERR_ABORT_SOCKET_GET_OPTION Socket can not be gotten
option value.**

**Cause:** An error occurred while getting socket option.

**Action:** Please check the system resource (file descriptor) or network resources.

**0x6116C ( 397676) rpERR_ABORT_POLL_REMOVE_SOCK Socket can not be removed from
the poll.**

**Cause:** An error occurred while removing socket from the poll.

**Action:** Please check the system (file descriptor) or network resources.

**0x6116D ( 397677) rpERR_ABORT_POLL_DISPATCH_TIMEOUT There is no network event
in time.**

**Cause:** There is no network I/O in time.

**Action:** Please check the network interface controller.

**0x6116E ( 397678) rpERR_ABORT_POLL_DISPATCH_ERROR Fail to invoke the
dispatcher system function.**

**Cause:** This is a system call error.

**Action:** Please check the system resources (file descriptor or memory).

**0x6116F ( 397679) rpERR_ABORT_POLL_CREATE_ERROR Dispatcher can not be
created.**

**Cause:** An error occurred while creating dispatcher was being created.

**Action:** Please check the system resources (file descriptor or memory).

**0x61170 ( 397680) rpERR_ABORT_SOCK_GET_ADDR_INFO_ERROR Fail to invoke
getAddrInfo system function. (IP = \<0%s\>, PORT = \<1%d\>)**

**Cause:** IP address and port number are wrong, or There is not enough memory.

**Action:** Please check the IP address and port Number, or system
resources(memory).

**0x61171 ( 397681)
rpERR_ABORT_REPLICATION_HAS_RECOVERY_OPTION_IN_SPLIT_PARTITION Replication
option is set to recovery.(Replcation Name:\<0%s\>, User:\<1%s\>, Table:\<2%s\>,
Partition:\<3%s\>)**

**Cause:** The partition split cannot be performed in recovery option.

**Action:** Check the replication options

**0x61172 ( 397682)
rpERR_ABORT_REPLICATION_HAS_RECOVERY_OPTION_IN_MERGE_PARTITION Replication
option is set to recovery.(Replcation Name:\<0%s\>, User:\<1%s\>, Table:\<2%s\>,
Partition:\<3%s\>, Partition:\<4%s\>)**

**Cause:** The partition merge cannot be performed in recovery option.

**Action:** Check the replication options

**0x61173 ( 397683) rpERR_ABORT_TABLE_PARTITIONS_ARE_NOT_SAME_REPLICATION
Replicated partitions are not included same replication.(User:\<0%s\>,
Table:\<1%s\>, Partition:\<2%s\>, Partition:\<3%s\>)**

**Cause:** The partition merge cannot be performed in other replicated
partition.

**Action:** Check the partition name of the replicated table.

**0x61174 ( 397684) rpERR_ABORT_PARTITION_NAME_DIFF The partition name of local
table must be same with remote one.( Replication name: \<0%s\> Local
(User:\<1%s\>, Table:\<2%s\>, Partition:\<3%s\>), Remote (User:\<4%s\>,
Table:\<5%s\>, Partition:\<6%s\>) )**

**Cause:** The partition name of local table is not same with remote one.

**Action:** Modify the partition name of local table.

**0x61175 ( 397685) rpERR_ABORT_TABLE_NAME_DIFF The name of local table must be
same with remote one.(Replication name: \<0%s\> Local (User:\<1%s\>,
Table:\<2%s\>, Partition:\<3%s\>), Remote (User:\<4%s\>, Table:\<5%s\>,
Partition:\<6%s\>) )**

**Cause:** The name of local table must be same with remote one.

**Action:** Verify that the name of local table is same with remote table.

**0x61176 ( 397686)
rpERR_ABORT_REPLICATION_HAS_RECOVERY_OPTION_IN_DROP_PARTITION Replication option
is set to recovery.(Replcation Name:\<0%s\>, User:\<1%s\>, Table:\<2%s\>,
Partition:\<3%s\>)**

**Cause:** Cannot perform a DDL(DROP PARTITION) in recovery option.

**Action:** Remove the recovery option.

**0x61177 ( 397687) rpERR_ABORT_POLL_ADD_SOCK A Socket cannot be added to the
poll.**

**Cause:** An error occurred while adding a socket to the poll.

**Action:** Check the system or network resources; in particular, verify the
file descriptor.

**0x61178 ( 397688) rpERR_ABORT_RPC_NOT_PROPER_VALUE Invalid \<0%s\> value :
\<1%s\>. Valid value range = \<2%lu\> \~ \<3%lu\> \<4%s\>**

**Cause:** The value is out of range.

**Action:** Spcify the value whthin valid range.

**0x6117B ( 397691) rpERR_ABORT_RPC_NOT_SUPPORT_REPL_LOCAL_AND_EAGER It is
unable to use eager mode when local replication option used.**

**Cause:**

\# - Eager mode does not support local replication option.

**Action:**

\# - Change replication mode or remove LOCAL option.

**0x6117C ( 397692) rpERR_ABORT_SELF_REPLICATION_TABLE Self-replication has been
detected due to duplicate table name.
[\<0%s\>.\<1%s\>.\<2%s\>:\<3%s\>.\<4%s\>.\<5%s\>]**

**Cause:**

\# - The same name is used in the source and target tables.

**Action:**

\# - Set a different name for the source and target tables.

**0x6117D ( 397693) rpERR_ABORT_SELF_REPLICATION_NAME Self-replication has been
detected due to duplicate replication name. [\<0%s\>]**

**Cause:**

\# - Same replication name used for itself and peer replicaiton.

**Action:**

\# - Use different peer replication name from its replication name.

**0x6117E ( 397694) rpERR_ABORT_RP_NOT_SUPPORT_CONVERT_APPLY_DATA_TYPE The
table(\<0%s\>.\<1%s\>:\<2%s\>.\<3%s\>) containing \<4%s\> does not support sql
apply feature.**

**Cause:**

\# - The table containing specific data type does not support sql apply feature.

**Action:**

\# - Please drop specific data type from the table.

**0x6117F ( 397695) rpERR_ABORT_REPLICATION_DDL_ENABLE_LEVEL Cannot execute this
DDL on a replicated table when the system property REPLICATION_DDL_ENABLE_LEVEL
is \<0%u\>.**

**Cause:**

\# - System property REPLICATION_DDL_ENABLE_LEVEL is not appropriate for this
DDL.

**Action:**

\# - Check the system property REPLICATION_DDL_ENABLE_LEVEL.

**0x61180 ( 397696) rpERR_ABORT_RPC_DDL_NOT_SUPPORTED_REPLICATED_TABLE This DDL
is not supported on replicated table.(Cause : \<0%s\>)**

**Cause:**

\# - This DDL is not supported on replicated table.

**Action:**

\# - Identify the cause and take appropriate action.

**0x61181 ( 397697) rpERR_ABORT_RP_ALREADY_DDL_SYNC Can not perform a DDL
synchronization because it is currently in progress (Replication name :
\<0%s\>).**

**Cause:**

\# - Can not perform a DDL synchronization because it is currently in progress.

**Action:**

\# - Retry after finishing the DDL synchronization.

**0x61182 ( 397698) rpERR_ABORT_RP_DDL_SYNC_NOT_SUPPORT_EAGER Can not execute a
DDL synchronization on a table using eager mode replication.**

**Cause:**

\# - Can not execute a DDL synchronization for a table using eager mode
replication.

**Action:**

\# - Change the replication mode in eager mode replication or remove the table
in eager mode replication.

**0x61183 ( 397699)
rpERR_ABORT_RP_DDL_SYNC_NOT_SUPPORT_GLOBAL_NON_PARTITION_INDEX A DDL
synchronization is not support on a table with global non-partitioned index.**

**Cause:**

\# - A DDL synchronization is not support on a table with global non-partitioned
index.

**Action:**

\# - Verify that the table with a global non-paritited index.

**0x61184 ( 397700) rpERR_ABORT_RP_DDL_SYNC_DISABLE Can not perform the DDL
synchronization when the value of the REPLICATION_DDL_SYNC property is 0.**

**Cause:**

\# - Can not perform the DDL synchronization when the value of the
REPLICATION_DDL_SYNC property is 0.

**Action:**

\# - Verify and change the value of the REPLICATION_DDL_SYNC property is 1.

**0x61185 ( 397701) rpERR_ABORT_RP_DDL_SYNC_ERROR_AFTER_COMMIT_MSG A DDL
synchronization is failed after sending commit message. The table schema of the
remote server may have been inconsistent.**

**Cause:**

\# - A DDL synchronization is failed after sending commit message.

**Action:**

\# - Verify that the replication actually commits

**0x61186 ( 397702) rpERR_ABORT_RP_DDL_SYNC_RECEIVE_ERROR A DDL synchronization
receives the error message from the remote server (\<0%s\>).**

**Cause:**

\# - Receive the error message from the remote server.

**Action:**

\# - Perform a DDL synchronization after troubleshooting the remote server.

**0x61187 ( 397703) rpERR_ABORT_RP_SENDER_NOT_RUNNING The sender of replication
\<0%s\> is not running.**

**Cause:**

\# - The sender of replication is not running.

**Action:**

\# - Restart the replication or wait for the replication sender to run.

**0x61188 ( 397704) rpERR_ABORT_RP_DDL_SYNC_SQL_LENGTH_ERROR The length of the
SQL query exceeds the maximum limit (\<0%u\>).**

**Cause:**

\# - The length of the SQL query exceeds the maximum limit.

**Action:**

\# - Refer to the Replication Manaual for the maximum possible length allowed
for the DDL synchronization query.

**0x61189 ( 397705) rpERR_ABORT_PARENT_AND_CHILD_CONNECT_DIFFERENT Failed to
connected by the parallel senders. The parallel senders get different IP address
from DNS server.**

**Cause:**

\# - The parallel senders must be connected by the same IP.

**Action:**

\# - Verify the DNS server or restart the replication sender. (When you restart
the replication, the parallel senders have been connected by the same IP.)

**0x6118A ( 397706) rpERR_ABORT_RPC_ROLE_NOT_SUPPORT_IB InfiniBand(IB) can not
be used with 'FOR ANALYSIS' syntax.**

**Cause:**

\# - InfiniBand(IB) can not be used with 'FOR ANALYSIS' syntax.

**Action:**

\# - Check the role of the replication. Do not use the InfiniBand(IB).

**0x6118C ( 397708) rpERR_ABORT_RP_DDL_SYNC_WITH_PROPAGATION The propagation
option(FOR PROPAGABLE LOGGING/ FOR PROPAGATION) does not support DDL
synchronization.**

**Cause:**

\# - The propagation option(FOR PROPAGABLE LOGGING/ FOR PROPAGATION) does not
support DDL synchronization.

**Action:**

\# - Remove the propagation option.

**0x6118D ( 397709) rpERR_ABORT_HBT_DETECT_PEER_SERVER_ERROR The HeartBeat
thread(HBT) detects peer server or network error.**

**Cause:**

\# - 1. Peer server is not running.

\# - 2. Network is not working.

**Action:**

\# - 1. Confirm peer server is running.

\# - 2. Ensure that network is working normally.

**0x6118E ( 397710) rpERR_ABORT_SEND_TIMEOUT_EXCEED Timeout exceed while the
replication Sender and Receiver were communicating.**

\# \*Cause :

\# - A timeout occurred while the replication Sender and Receiver were
communicating.

\# \*Action :

\# - Set a larger value for the REPLICATION_SENDER_SEND_TIMEOUT property.

\# - Check the peer server or network connection.

### IGNORE

**0x62024 ( 401444) rpERR_IGNORE_RP_SENDER_HASH_INIT [Sender] Failed to
initialize the hash table**

**Cause:**

\# - The replication feature of Altibase could not be used.

\# - Replication was not initialized on startup because the port is not set
correctly.

**Action:** Set the port correctly.

**0x6204A ( 401482) rpERR_IGNORE_RECEIVER_START [Receiver] started ...**

**Cause:** The receiver thread has already been started.

**Action:** You can safely ignore this message.

**0x6204C ( 401484) rpERR_IGNORE_START_SENDER [Sender] Replication \<0%s\>
Start... at [\<1%ld\>]**

**Cause:** The replication started up correctly.

**Action:**

\# - N/A

**0x62068 ( 401512) rpERR_IGNORE_RP_INIT_SOCK Unable to initialize a socket**

**Cause:** Not enough memory.

\# - Unable to connect to a remote server.

\# \*Action Check whether the remote server is running and online.

**0x62070 ( 401520) rpERR_IGNORE_RP_PROTOCOL_DIFF Different replication
protocols**

**Cause:** The replication protocol is different from that on the peer server.

**Action:** Check the replication protocol version, endian, and 32/64 bit.

**0x6209B ( 401563) rpERR_IGNORE_RP_META_DIFF Replication meta is different**

**Cause:** The replication meta is different from that on the peer server.

**Action:** Check the Altibase version and the replication protocol version.

**0x620CA ( 401610) rpERR_IGNORE_RP_NO_SPACE There is not available space for
replication log buffer.**

**Cause:** Replication is delayed or replication log buffer size is too small.

**Action:**

\# - Increase REPLICATION_LOG_BUFFER_SIZE and restart the system.

\# - Find and resolve cause of the delay.

**0x620EB ( 401643) rpERR_IGNORE_EXIT_FLAG_SET Exit flag is set.**

**Cause:** The exit flag has been set.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x620EE ( 401646) rpERR_IGNORE_NOT_ACITVE_TX The transaction does not exist in
transaction table of the sender.**

**Cause:** The Sender of the replication is not alone. Another Sender of the
replication is processing the transaction.

**Action:** This is not an error of Altibase.

**0x620F0 ( 401648) rpERR_IGNORE_RP_SENDER_STOP [Sender] Stop sender thread
\<0%s\>:\<1%u\> at [\<2%ld\>], Restart SN[\<3%ld\>]**

**Cause:** This error occurs when the replication Sender stops.

**Action:** You may safely ignore this message.

**0x620F9 ( 401657) rpERR_IGNORE_TIMESTAMP_INSERT_CONFLICT [Receiver] An insert
conflict occurred during timestamp conflict resolution.**

**Cause:** The timestamp value of an XLog is older than an existing one.

**Action:** This behavior is normal and can be expected from time to time.

**0x620FA ( 401658) rpERR_IGNORE_TIMESTAMP_UPDATE_CONFLICT [Receiver] An update
conflict occurred during timestamp conflict resolution.**

**Cause:** The timestamp value of an XLog is older than an existing one.

**Action:** This behavior is normal and can be expected from time to time.

5.QP Error Code
---------------

### FATAL

**0x303DB ( 197595) qpERR_FATAL_THREAD_ATTR_CREATE Failed to invoke the
thread_attr_init() system function**

**Cause:** The system failed to create a thread attribute.

**Action:** Check the call stack from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x303DC ( 197596) qpERR_FATAL_THREAD_ATTR_SET_BOUND Failed to invoke the
thread_attr_setscope() system function**

**Cause:** The system failed to bind a thread attribute.

**Action:** Check the call stack from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x303DD ( 197597) qpERR_FATAL_THREAD_ATTR_DESTROY Failed to invoke the
thread_attr_destroy() system function**

**Cause:** The system failed to destroy a thread attribute.

**Action:** Check the call stack from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x303DF ( 197599) qpERR_FATAL_THREAD_JOIN Failed to invoke the thread_join()
system function**

**Cause:** The system failed to join a thread.

**Action:** Check the call stack from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x303E0 ( 197600) qpERR_FATAL_MUTEX_INIT Unable to initialize a mutex.**

**Cause:** The system failed to initialize a mutex.

**Action:** Check the call stack from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x303E1 ( 197601) qpERR_FATAL_MUTEX_DESTROY Failed to invoke the
mutex_destroy() system function**

**Cause:** The system failed to destroy a mutex.

**Action:** Check the call stack from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x303E2 ( 197602) qpERR_FATAL_MUTEX_LOCK Failed to invoke the mutex_lock()
system function**

**Cause:** The system failed to lock a mutex.

**Action:** Check the call stack from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x303E3 ( 197603) qpERR_FATAL_MUTEX_UNLOCK Failed to invoke the mutex_unlock()
system function**

**Cause:** The system failed to unlock a mutex.

**Action:** Check the call stack from the trace log and contact Altibase’s
Support Center (http://support.altibase.com).

**0x303E4 ( 197604) qpERR_FATAL_COND_INIT Failed to invoke the cond_init()
system function**

**Cause:** The system failed to initialize a condition variable.

**Action:** Check the call stack from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x303E5 ( 197605) qpERR_FATAL_COND_DESTROY Failed to invoke the cond_destroy()
system function**

**Cause:** The system failed to destroy a condition variable.

**Action:** Check the call stack from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x303E6 ( 197606) qpERR_FATAL_COND_SIGNAL Failed to invoke the cond_signal()
system function**

**Cause:** The system failed to signal using a condition variable.

**Action:** Check the call stack from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x303E7 ( 197607) qpERR_FATAL_COND_WAIT Failed to invoke the cond_wait()
system function**

**Cause:** Invalid condition value or invalid mutex.

**Action:** Check the call stack from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x30425 ( 197669) qpERR_FATAL_MUTEX_TRYLOCK Failed to invoke the
mutex_trylock() system function**

**Cause:** The system failed to lock a mutex.

**Action:** Check the call stack from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x30191 ( 197009) qpERR_FATAL_QDN_NOT_FOUND_FOREIGNKEY Foreign key not found**

**Cause:** Foreign key not found

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x30082 ( 196738) qpERR_FATAL_QMO_INVALID_MEMORY_AREA Invalid memory area
access.**

**Cause:** Invalid memory area access

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com).

**0x30203 ( 197123) qpERR_FATAL_QCU_INVALID_INSERT_LIMIT_PROPERTY Invalid values
for INSERT_LOW_LIMIT and INSERT_HIGH_LIMIT properties.**

**Cause:** The value of the INSERT_HIGH_LIMIT property must be greater than that
for the INSERT_LOW_LIMIT property.

**Action:** Check the INSERT_LOW_LIMIT and INSERT_HIGH_LIMIT properties.

**0x302E7 ( 197351) qpERR_FATAL_QCU_INVALID_TTL_SIZE_PROPERTY Invalid values for
INIT_TRANS and MAX_TRANS properties.**

**Cause:** The value of the MAX_TRANS property must be greater than that for the
INIT_TRANS property.

**Action:** Check the INIT_TRANS and MAX_TRANS properties.

### ABORT

**0x311D6 ( 201174) qpERR_ABORT_MEMORY_ALLOCATION Insufficient memory for Query
Processor**

**Cause:** The memory manager could not allocate sufficient memory for the query
processor.

**Action:** Verify that the system has sufficient memory.

**0x313DE ( 201694) qpERR_ABORT_THREAD_CREATE Failed to invoke the
thread_create() system function**

**Cause:** The system failed to create a thread.

**Action:** Check the call stack from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x313E8 ( 201704) qpERR_ABORT_BIND_PROCESS Failed to invoke the bind_process()
system function**

**Cause:** System failed to bind cpusets to a process.

**Action:** Check the call stack from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x31455 ( 201813) qpERR_ABORT_FAULT_TOLERATED Failed to work because an
internal exception occurred from an OS.[Contact Altibase's Support Center]**

**Cause:** An internal exception occurred from an OS.

**Action:** Check the error number from the trace log for more detailed
information. And contact Altibase's Support Center
(http://support.altibase.com/en/).

**0x31318 ( 201496) qpERR_ABORT_QMC_UNEXPECTED_ERROR Unexpected errors may have
occurred: \<0%s\>: \<1%s\>**

**Cause:** Unexpected errors may have occurred.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x31001 ( 200705) qpERR_ABORT_QCP_SYNTAX SQL syntax error \<0%s\>**

**Cause:** The unusable reserved words or delimiter inapplicable was used. Or
the reserved word cannot be used.

**Action:** Refer to SQL Reference. Or verify the reserved words listed in SQL
Reference.

**0x31003 ( 200707) qpERR_ABORT_QCP_NOT_SUPPORTED_SYNTAX Unsupported syntax**

**Cause:** The syntax is currently not supported.

**Action:** Refer to the SQL manual.

**0x31004 ( 200708) qpERR_ABORT_QCP_CONFLICT_NULL_CONSTRAINT Duplicate or
conflicting NULL and/or NOT NULL constraints**

**Cause:** Duplicate or conflicting NULL and/or NOT NULL constraints.

**Action:** Remove one of the duplicate or conflicting constraints.

**0x31005 ( 200709) qpERR_ABORT_QCP_NO_HAVE_DATATYPE_IN_CRT_TBL A column in a
CREATE TABLE or ALTER TABLE ADD COLUMN statement must have a data type.**

**Cause:** A column in a CREATE TABLE or ALTER TABLE ADD COLUMN statement must
have a data type.

**Action:** Specify a data type for the column.

**0x31006 ( 200710) qpERR_ABORT_QCP_HAVE_DATATYPE_IN_CRT_TBL_AS_SELECT A column
in a CREATE TABLE AS SELECT statement must not have a data type.**

**Cause:** A column in a CREATE TABLE AS SELECT statement must not have a data
type.

**Action:** Do not specify data types in the column definition clause.

**0x31007 ( 200711) qpERR_ABORT_QCP_DUPLICATE_COLUMN_NAME Duplicate column name
\<0%s\>**

**Cause:** Duplicate column name

**Action:** Verify that no duplicate column names are specified.

**0x31234 ( 201268) qpERR_ABORT_QCP_DUPLICATE_CONSTRAINT_NAME Duplicate
constraint name \<0%s\>**

**Cause:** Duplicate constraint name

**Action:** Verify that no duplicate constraint names are specified.

**0x31008 ( 200712) qpERR_ABORT_QCP_HAVE_NO_COLUMN This statement must have at
least one column.**

**Cause:** A CREATE TABLE or ALTER TABLE ADD COLUMN statement must have at least
one column.

**Action:** Specify more than one column.

**0x31009 ( 200713) qpERR_ABORT_QCP_LIMIT_VALUE The START or COUNT value in a
SELECT LIMIT clause must be greater than 0.**

**Cause:** The START or COUNT value in a SELECT LIMIT clause must be greater
than 0.

**Action:** Specify a positive integer for the START or COUNT value.

**0x3118B ( 201099) qpERR_ABORT_QCP_MAX_NAME_LENGTH_OVERFLOW The length of the
name exceeds the maximum limit. \<0%s\>**

**Cause:** The length of the name exceeds the maximum limit.

**Action:** Refer to the SQL Reference for the maximum possible length allowed
for the object's name. Enter a name with a valid length.

**0x31152 ( 201042) qpERR_ABORT_QSX_ROWTYPE_ON_RETURN_NOT_ALLOWED_ERROR_SQLTEXT
ROWTYPE is not allowed for a RETURN clause. \<0%s\>**

**Cause:** The RETURN type of a function is ROWTYPE.

\# \*Action Do not use ROWTYPE as a RETURN clause.

**0x31186 ( 201094) qpERR_ABORT_QCP_FUNC_NAME_NOT_MATCHED Mismatched function
name \<0%s\>**

**Cause:** The function name is mismatched.

**Action:** Match the function names or remove the function name after the END
keyword.

**0x31187 ( 201095) qpERR_ABORT_QCP_FUNC_TOO_MANY_ARGU A procedure or function
has too many parameters.**

**Cause:** A procedure or function has too many parameters.

**Action:** Refer to the Stored Procedures Manual for the maximum possible
number of parameters allowed for the procedure or function. Define a valid
number of parameters.

**0x31204 ( 201220) qpERR_ABORT_QCP_INVALID_INSERT_LIMIT_OPTION Invalid values
for INSERT LOW LIMIT and INSERT HIGH LIMIT options.**

**Cause:** The value for the INSERT HIGH LIMIT option must be greater than the
one for the INSERT LOW LIMIT option.

**Action:** Check the INSERT LOW LIMIT and INSERT HIGH LIMIT options.

**0x3121C ( 201244) qpERR_ABORT_QCP_INVALID_LOGGING_OPTION Only one LOGGING or
NOLOGGING clause may be specified.**

**Cause:** Duplicate LOGGING options.

**Action:** Check the LOGGING options.

**0x3121D ( 201245) qpERR_ABORT_QCP_INVALID_PARALLEL_OPTION Only one PARALLEL or
NOPARALLEL clause may be specified.**

**Cause:** Duplicate PARALLEL options.

**Action:** Check the PARALLEL options.

**0x3121E ( 201246) qpERR_ABORT_QCP_INVALID_TABLESPACE_OPTION Duplicate
tablespace name clause.**

**Cause:** Duplicate TABLE SPACE NAME options.

**Action:** Check the TABLESPACE options.

**0x31242 ( 201282) qpERR_ABORT_QCP_INVALID_BUFFER_OPTION Only one BUFFER or
NOBUFFER clause may be specified.**

**Cause:** Duplicate BUFFER options.

**Action:** Check the BUFFER options.

**0x31241 ( 201281) qpERR_ABORT_QCP_INVALID_SYSDBA_OPTION Invalid SYSDBA
option.**

**Cause:** Invalid SYSDBA option.

**Action:** Usage: CONNECT username/password [AS SYSDBA].

**0x3129B ( 201371) qpERR_ABORT_QCP_DUPLICATE_SYNC_TABLE Duplicate table
names.**

**Cause:** Duplicate table names exist.

**Action:** Check table names for duplicates.

**0x312B0 ( 201392) qpERR_ABORT_QCP_DUPLICATE_REPL_OPTION Duplicate option
names.**

**Cause:** Duplicate option names exist.

**Action:** Check option names for duplicates.

**0x312B1 ( 201393) qpERR_ABORT_QCP_NOT_SUPPORTED_REPL_OPTION Unsupported
replication option name \<0%s\>**

**Cause:** The option is currently not supported.

**Action:** Refer to the *Replication Manual* for information about supported
options. Select an available option.

**0x312CA ( 201418) qpERR_ABORT_QCP_INVALID_FUNCTION Functions or procedures
other than TO_DATE function not allowed.**

**Cause:** Invalid function call.

**Action:** Check the function name.

**0x312DD ( 201437) qpERR_ABORT_QCP_INVALID_DATABASE_CHARSET A database
character set must be specified.**

**Cause:** Database character set is not specified.

**Action:** Specify a database character set.

**0x312DE ( 201438) qpERR_ABORT_QCP_INVALID_NATIONAL_CHARSET A national
character set must be specified.**

**Cause:** A national character set is not specified.

**Action:** Specify a national character set.

**0x31388 ( 201608)
qpERR_ABORT_QCP_COLUMN_CHECK_CONSTRAINT_REFERENCE_OTHER_COLUMN A column check
constraint cannot reference other columns.**

**Cause:** A column check constraint references other columns.

**Action:** Check and revise the column check constraint.

**0x31389 ( 201609)
qpERR_ABORT_QCP_SET_USER_NAME_OR_TABLE_NAME_TO_CONSTRAINT_COLUMN Cannot specify
user name or table name in column constraint \<0%s\>**

**Cause:** A user name or table name was specified in a column constraint
definition.

**Action:** Remove the user name or table name from the column constraint
definition.

**0x3139A ( 201626) qpERR_ABORT_QCP_CANNOT_SPECIFY_USER_NAME_OR_TABLE_NAME
Cannot specify user name or table name in function-based index column \<0%s\>**

**Cause:** A user name or table name was specified in the function-based index
column definition.

**Action:** Remove the user name or table name from the function-based index
column definition.

**0x3139F ( 201631) qpERR_ABORT_QCP_REQUIRE_OWNER_NAME_IN_DEFAULT_EXPR Name of
stored function owner is required in function-based index definition. \<0%s\>**

**Cause:** The name of the stored function's owner is required in function-based
index definition.

**Action:** Specify the name of the stored function's owner in the
function-based index definition.

**0x313A0 ( 201632) qpERR_ABORT_QCP_REQUIRE_OWNER_NAME_IN_CHECK_EXPR Name of
stored function owner is required in check constraint expression. \<0%s\>**

**Cause:** The name of the stored function's owner is required in check
constraint expression.

**Action:** Specify the name of the stored function's owner in the check
constraint expression.

**0x31408 ( 201736) qpERR_ABORT_QCP_DUPLICATE_LATERAL_KEYWORD The LATERAL
keyword cannot come after CROSS APPLY or OUTER APPLY.**

**Cause:** The LATERAL keyword comes after CROSS APPLY or OUTER APPLY.

**Action:** Do not write the LATERAL keyword after CROSS APPLY or OUTER APPLY.

**0x31202 ( 201218) qpERR_ABORT_INVALID_LIMIT_VALUE_TYPE A limit value host
variable was bound to an invalid type.**

**Cause:** The host variable type for the limit value must be one of INTEGER,
BIGINT, or SMALLINT.

**Action:** Bind the limit value host variable to one of the integer types.

**0x3100D ( 200717) qpERR_ABORT_QCM_INITDB Unable to initialize the meta
database**

**Cause:** The system failed to initialize the meta database due to a MEM_DIC
tablespace error.

**Action:** Recover the MEM_DIC tablespace or the database, or re-create the
database.

**0x3100E ( 200718) qpERR_ABORT_QCM_META_ALEADY_EXIST The meta database already
exists.**

**Cause:** The meta database already exists.

**Action:** Verify that the database has been properly dropped.

**0x31010 ( 200720) qpERR_ABORT_QCM_NOT_EXIST_USER User not found**

**Cause:** The user is not in the meta database.

**Action:** Verify that you have entered a valid user name and that the user
exists in the database.

**0x31011 ( 200721) qpERR_ABORT_QCM_NOT_EXIST_TABLE Table not found**

**Cause:** The table is not in the meta database.

**Action:** Verify that you have entered a valid table name and that the table
exists in the database.

**0x31012 ( 200722) qpERR_ABORT_QCM_NOT_EXIST_COLUMN Column not found**

**Cause:** The column is not in the meta database.

**Action:** Verify that you have entered a valid column name and use the DESC
command to check that the column exists in the table.

**0x311F4 ( 201204) qpERR_ABORT_QCM_NOT_EXIST_COLUMN_NAME Invalid column name
\<0%s\>**

**Cause:** The column name does not exist.

**Action:** Specify a valid column name.

**0x31013 ( 200723) qpERR_ABORT_QCM_NOT_EXIST_SEQUENCE Sequence not found**

**Cause:** The specified sequence name was not found in the database.

**Action:** Verify that the sequence exists.

**0x31014 ( 200724) qpERR_ABORT_QCM_NOT_EXISTS_INDEX Index not found**

**Cause:** The specified index name was not found in the database.

**Action:** Verify that the index exists. Look up meta tables to verify that the
index name is correct.

**0x31015 ( 200725) qpERR_ABORT_QCM_META_CRASH The meta table crashed.**

**Cause:** The meta table crashed.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x31017 ( 200727) qpERR_ABORT_QCM_REPL_NOT_FOUND Replication not found**

**Cause:** The specified replication has not been created yet.

**Action:** Create the replication first. Verify that the replication name is
valid.

**0x31018 ( 200728) qpERR_ABORT_QCM_INTERNAL_ARG Internal server error in meta
module (\<0%s\>).**

**Cause:** Program error

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x31192 ( 201106) qpERR_ABORT_QCM_LOCK_FAIL The table is locked by other
transactions.**

**Cause:** Cannot obtain a lock on the specified table because it is already
locked by other transactions.

**Action:** Check other transactions.

**0x3120A ( 201226) qpERR_ABORT_DROP_LAST_TABLE You cannot drop the last
table.**

**Cause:** You cannot drop the last table from a replication object.

**Action:** Check the META information.

**0x3120B ( 201227) qpERR_ABORT_DROP_LAST_HOST You cannot drop the last host.**

**Cause:** You cannot drop the last host from a replication object.

**Action:** Check the META information.

**0x3124A ( 201290) qpERR_ABORT_QCM_INVALID_DUMP_TABLE Invalid dump table**

**Cause:** The table is not a dump table.

**Action:** Use a dump table.

**0x3124B ( 201291) qpERR_ABORT_QCM_INVALID_DUMP_OBJECT Invalid dump object**

**Cause:** The object is not valid for the dump table.

**Action:** Use a valid dump object for the dump table.

**0x3124C ( 201292) qpERR_ABORT_QCM_TOO_MANY_DUMP_OBJECT Too many dump objects**

**Cause:** You are using too many dump objects.

**Action:** Use a suitable number of dump objects for the dump table.

**0x3125B ( 201307) qpERR_ABORT_QCM_NOT_EXIST_TABLE_PARTITION The table
partition does not exist. \<0%s\>**

**Cause:** The table partition does not exist.

**Action:** Check the table partition name.

**0x3125C ( 201308) qpERR_ABORT_QCM_TOO_MANY_LIST_PARTITION_CONDITION_VALUE Too
many partition condition values for the list partitioned table**

**Cause:** There are too many partition condition values for the list
partitioned table.

**Action:** Check the total number of partition condition values.

**0x312B2 ( 201394) qpERR_ABORT_QCM_ALREADY_SUPPORT_RECOVERY The table recovery
is already supported by another replication \<0%s\>**

**Cause:** The recovery of replication item is already supported.

**Action:** Check the replication item.

**0x312B9 ( 201401) qpERR_ABORT_QCM_MAXIMUM_OBJECT_NUMBER_EXCEED The number of
elements \<0%s\> exceeds the maximum limit (\<1%ld\>).**

**Cause:** The specified number of elements exceeds the maximum limit.

**Action:** Reduce the specified number of elements.

**0x312CB ( 201419) qpERR_ABORT_QCM_INVALID_REPL_CONDITION_MTCNAME There is an
invalid operator or operand in a replication condition.**

**Cause:** The length of mtcName cannot be over 8.

**Action:** Check the replication conditions.

**0x312CC ( 201420) qpERR_ABORT_QCM_INVALID_REPL_CONDITION Invalid replication
condition.**

**Cause:** The condition's top node has only an argument node.

**Action:** Check the replication conditions.

**0x312CD ( 201421) qpERR_ABORT_QCM_INVALID_REPL_CONDITION_DATATYPE Data type
not permitted in replication condition.**

**Cause:** The data type is not permitted.

**Action:** Check the data type of the operand for the replication condition.

**0x312CE ( 201422) qpERR_ABORT_QCM_INVALID_REPL_CONDITION_OPERAND If one
operand is a column, the other operand has to be a value.**

**Cause:** A pair of operands must always consist of a column and a value.

**Action:** Check the operands for the replication condition.

**0x312CF ( 201423) qpERR_ABORT_QCM_DIFF_REPL_CONDITION_OPERANDS A Pair of
operands has to have the same data type.**

**Cause:** The data types of a pair of operands are different from each other.

**Action:** Check the data types of the operands for the replication condition.

**0x312D0 ( 201424) qpERR_ABORT_QCM_COLUMN_VALUE_MISMATCH Invalid update column
list.**

**Cause:** The number of values and the number of columns in an update column
list are not the same.

**Action:** Check the update column list.

**0x312D1 ( 201425) qpERR_ABORT_QCM_INVALID_REPL_CONDITION_VALUE Sysdate is not
allowed as a replication condition value.**

**Cause:** Sysdate was specified as a replication condition value.

**Action:** Do not use SYSDATE as a replication condition value.

**0x312F6 ( 201462) qpERR_ABORT_QRC_NOT_EXIST_REPL_OFFLINE_DIR_PATH Replication
offline log dir not found.**

**Cause:** No replication offline log dir path was found.

**Action:** Check the meta tables.

**0x312F7 ( 201463) qpERR_ABORT_QRC_ROLE_NOT_SUPPORT_REPL_OFFLINE Offline option
not supported in this role.**

**Cause:** This role does not support the offline option.

**Action:** Check the options or the role of the replication.

**0x312F8 ( 201464) qpERR_ABORT_QCP_MAX_PATH_LENGTH_OVERFLOW The length of the
path exceeds the maximum limit. \<0%s\>**

**Cause:** The length of the path exceeds the maximum limit.

**Action:** Refer to the SQL Reference for the maximum possible length allowed
for the path. Enter a path with a valid length.

**0x312F9 ( 201465) qpERR_ABORT_QRC_NOT_SUPPORT_REPL_OFFLINE_AND_RECOVERY
Offline option is not supported with recovery option.**

**Cause:** The offline option is not supported with the recovery option.

**Action:** Check the replication options.

**0x312FA ( 201466) qpERR_ABORT_QRC_ALREADY_OFFLINE_SET Offline option already
set.**

**Cause:** The replication offline option was already set.

**Action:** Check the replication options.

**0x312FB ( 201467) qpERR_ABORT_QRC_ALREADY_OFFLINE_UNSET Offline option already
unset.**

**Cause:** The replication offline option was already unset.

**Action:** Check the replication options.

**0x31368 ( 201576) qpERR_ABORT_QCM_REUSE_COUNT The password cannot be reused.**

**Cause:** The password has been reused more than the allowable number of times.

**Action:** Enter a new password.

**0x31369 ( 201577) qpERR_ABORT_QCM_USER_DEFINED_ERROR user defined error:
\<0%s\>**

**Cause:** A user-defined callback function returned an error.

**Action:** Respond to the error raised by the user-defined callback function.

**0x3136A ( 201578) qpERR_ABORT_QCM_MESSAGE_TOO_LONG Callback function message
too long**

**Cause:** The error message returned by a callback function was too long.

**Action:** Reduce the length of the callback function error message.

**0x3136B ( 201579) qpERR_ABORT_QCM_VERIFY_FUNCTION_SELECT_ERROR Invalid
user-defined function 'PASSWORD_VERIFY_FUNCTION'.**

**Cause:** A user-defined function is invalid, or was not called properly.

**Action:** Check the validity of the user-defined function and verify that it
was called correctly.

**0x31373 ( 201587) qpERR_ABORT_QCM_NOT_EXIST_MVIEW Materialized view not
found**

**Cause:** The materialized view is not in the meta database.

**Action:** Verify that you have entered a valid materialized view name and that
the materialized view exists in the database.

**0x313CC ( 201676) qpERR_ABORT_QCM_JOB_QUEUE_OVERFLOW The job thread queue
overflows.**

**Cause:** The size of the thread queue is too small for the number of jobs.

**Action:** Enlarge the size of the JOB_THREAD_QUEUE_SIZE property.

**0x31404 ( 201732) qpERR_ABORT_QCM_NOT_EXIST_USER_OR_ROLE User or role not
found.**

**Cause:** The specified role or user does not exist.

**Action:** Check whether the role or user exists.

**0x31405 ( 201733) qpERR_ABORT_QCM_USER_TO_ROLES_MAX_COUNT Unable to grant any
more roles to the user.**

**Cause:** The number of roles granted to the user has reached the maximum
limit.

**Action:** Do not grant any more roles to the user, or revoke a role first.

**0x31300 ( 201472) qpERR_ABORT_DLOPEN dlopen error: [\<0%s\>]**

**Cause:** dlopen error

**Action:** Check the shared library.

**0x31301 ( 201473) qpERR_ABORT_DLSYM dlsym error**

**Cause:** dlsym error

**Action:** Check the shared library.

**0x31302 ( 201474) qpERR_ABORT_DLCLOSE dlclose error: [\<0%s\>]**

**Cause:** dlclose error

**Action:** Check the shared library.

**0x31303 ( 201475) qpERR_ABORT_FUNC_CALL Function call error: [\<0%s\> :
\<1%s\>]**

**Cause:** Function call error

**Action:** Check the shared library.

**0x31304 ( 201476) qpERR_ABORT_INVALID_MODULE Invalid security module.**

**Cause:** Invalid security module.

**Action:** Check the security module.

**0x31305 ( 201477) qpERR_ABORT_FAIL_TO_VERIFY_MODULE Failed to verify security
module: [\<0%s\>]**

**Cause:** Failed to verify the security module.

**Action:** Check the security module.

**0x31306 ( 201478) qpERR_ABORT_NOT_EXIST_POLICY Policy does not exist:
[\<0%s\>]**

**Cause:** The policy does not exist.

**Action:** Check the security module.

**0x31307 ( 201479) qpERR_ABORT_INVALID_POLICY Policy is not valid: [\<0%s\>]**

**Cause:** The policy is not valid.

**Action:** Check the security module.

**0x31308 ( 201480) qpERR_ABORT_NOT_EXIST_ECC_POLICY ECC policy does not exist:
[\<0%s\>]**

**Cause:** The ECC policy does not exist.

**Action:** Check the security module.

**0x31309 ( 201481) qpERR_ABORT_INVALID_ECC_POLICY ECC policy is not valid:
[\<0%s\>]**

**Cause:** The ECC policy is not valid.

**Action:** Check the security module.

**0x3130D ( 201485) qpERR_ABORT_FAIL_TO_OPEN_SECURITY_MODULE Failed to open
security module.**

**Cause:** Failed to open the security module.

**Action:** Check the SECURITY_MODULE property.

**0x3130E ( 201486) qpERR_ABORT_SECURITY_MODULE_ALREADY_STARTED Security has
already been started.**

**Cause:** Security has already been started.

**Action:** Stop SECURITY_MODULE to start again.

**0x3130F ( 201487) qpERR_ABORT_MISMATCH_SECURITY_MODULE Mismatched security
module [\<0%s\>], [\<1%s\>], [\<2%s\>]**

**Cause:** Mismatched security module.

**Action:** Check the security module.

**0x31310 ( 201488) qpERR_ABORT_EXIST_ENCRYPTED_COLUMN Encrypted column
exists.**

**Cause:** An encrypted column exists.

**Action:** Check the encrypted column.

**0x31311 ( 201489) qpERR_ABORT_INVALID_SECURITY_MODULE_VERSION Security module
version is not valid.**

**Cause:** Security module version is not valid.

**Action:** Check the security module.

**0x31312 ( 201490) qpERR_ABORT_POLICY_BLOCK_SIZE_TOO_BIG Policy block size is
too big: [\<0%s\>]**

**Cause:** The policy block size is too big.

**Action:** Check the security module.

**0x31020 ( 200736) qpERR_ABORT_QDB_DDL_WITH_REPLICATED_TBL You cannot execute
DDL on a replicated table.**

**Cause:** You cannot execute DDL on a replicated table.

**Action:** Verify that the specified table is not replicated.

**0x313D9 ( 201689) qpERR_ABORT_QDB_DDL_WITH_REPLICATED_PART You cannot execute
DDL on a replicated partition.**

**Cause:** You cannot execute DDL on a replicated partition.

**Action:** Verify that the specified partition is not replicated.

**0x31022 ( 200738) qpERR_ABORT_QDB_EXIST_OBJECT_NAME The name is already used
by an existing object.**

**Cause:** An attempt was made to create a database object (such as a table,
view or sequence) that already exists. A user's database objects must have
distinct names.

**Action:** Enter a unique name for the database object or modify or drop the
existing object so it can be reused.

**0x31023 ( 200739) qpERR_ABORT_QDB_DUPLICATE_COLUMN Duplicate column name :
\<0%s\>**

**Cause:** Two or more identical column names were declared for a table.

**Action:** Change one of the duplicate column names in the table.

**0x311C3 ( 201155) qpERR_ABORT_QDB_DUPLICATE_TIMESTAMP_COLUMN A table can have
only one TIMESTAMP column. \<0%s\>**

**Cause:** A table can have only one TIMESTAMP column.

**Action:** Specify only one timestamp column in the table description.

**0x311C4 ( 201156) qpERR_ABORT_QDB_CANNOT_SET_TIMESTAMP_DEFAULT No default
value can be specified for a TIMESTAMP column. \<0%s\>**

**Cause:** No default value can be specified for a TIMESTAMP column.

**Action:** Remove the default clause from the TIMESTAMP column.

**0x31024 ( 200740) qpERR_ABORT_QDB_NOT_EXISTS_ALIAS No alias is specified. The
SELECT statement has a compound expression without an alias.**

**Cause:** The SELECT statement has a compound expression without an alias name,
which is used as a column name for the new table.

**Action:** Specify an alias to the compound expression in the target list of
the SELECT statement.

**0x31025 ( 200741) qpERR_ABORT_QDB_MISMATCH_COL_COUNT The number of columns in
the list and the number of values in the list do not match.**

**Cause:** When the user executes a CREATE TABLE AS SELECT statement, the number
of defined columns must be equivalent to the number of specified expressions in
the target list of the SELECT statement.

**Action:** Verify that the number of columns is equivalent to the number of
expressions in the target list of the SELECT statement.

**0x31026 ( 200742) qpERR_ABORT_QDB_INVALID_COLUMN_COUNT Too many or too few
columns in a table**

**Cause:** The number of columns in a table is either larger than the limit or
zero as a result of adding or dropping a column.

**Action:** If the number of columns becomes zero, drop the table. If the number
of columns exceeds the limit, create a new table for the column.

**0x31027 ( 200743) qpERR_ABORT_QDB_NOT_EXISTS_DEFAULT Unable to find the
DEFAULT specification to drop.**

**Cause:** Could not find a DEFAULT specification to drop.

**Action:** Consult the meta tables to see if a DEFAULT value has been specified
for the column.

**0x31028 ( 200744) qpERR_ABORT_QDB_CREATE_DISABLE_DATA_TYPE Unable to create a
column with the specified data type.**

**Cause:** Unable to create a column with the specified data type

**Action:** Verify that it is permissible to create the specified data type.

**0x31029 ( 200745) qpERR_ABORT_QDB_META_CRASH The meta database crashed.**

**Cause:** The meta database crashed.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x3102A ( 200746) qpERR_ABORT_QDB_REFERENTIAL_CONSTRAINT_EXIST A foreign key
constraint depends on the table or column.**

**Cause:** There is a foreign key constraint that depends on the table or
column.

**Action:** Drop the related foreign key constraints first, and then retry this
statement.

**0x3102B ( 200747) qpERR_ABORT_QDB_NOT_EXIST_NOT_NULL Unable to alter the
column to a nullable column because no NOT NULL constraint is specified for the
column.**

**Cause:** There is no NULL constraint to drop.

**Action:** Check the column specification.

**0x3102C ( 200748) qpERR_ABORT_QDB_NOT_ALLOWED_DROP_NOT_NULL Unable to drop a
NOT NULL constraint because a primary key constraint exists.**

**Cause:** A primary key constraint exists for this column.

**Action:** Check the column specification.

**0x3102D ( 200749) qpERR_ABORT_QDB_EXIST_NOT_NULL Unable to add a NOT NULL
constraint to the specified column because it already has either a NOT NULL or
PRIMARY KEY constraint.**

**Cause:** The column already has a NOT NULL constraint.

**Action:** Check the column specification.

**0x3102F ( 200751) qpERR_ABORT_QDB_NOTNULL_HAS_NULL Unable to add a NOT NULL
constraint to the specified column because it already contains null values**

**Cause:** One or more records in the specified column have null values.

**Action:** Check the column specification.

**0x31182 ( 201090) qpERR_ABORT_QDB_DUPLICATE_COLUMN_NAME Duplicate column
name**

**Cause:** The same column name exists in the table specification.

**Action:** Check the table specification.

**0x31183 ( 201091) qpERR_ABORT_QDB_NOT_ALLOWED_SUBQUERY A subquery is not
allowed here. \<0%s\>**

**Cause:** A subquery is not allowed here.

**Action:** Remove the subquery.

**0x311AF ( 201135) qpERR_ABORT_QDB_DDL_ON_CLOSED_TABLE This table is not in
memory. \<0%s\>**

**Cause:** This table is not in memory.

**Action:** Execute ALTER TABLE OPEN.

**0x311FF ( 201215) qpERR_ABORT_QDB_HIGHLIMIT_LESS_LOWLIMIT INSERT HIGH LIMIT
cannot be less than or equal to INSERT LOW LIMIT.**

**Cause:** INSERT HIGH LIMIT cannot be less than or equal to INSERT LOW LIMIT.

**Action:** Check INSERT HIGH LIMIT and INSERT LOW LIMIT

**0x31233 ( 201267) qpERR_ABORT_QDB_FIXED_PAGE_SIZE_ERROR The fixed record size
exceeds the page size.**

**Cause:** A table cannot be created because the size of a record exceeds the
page size.

**Action:** Create a table whose record size is less than a page size.

**0x31236 ( 201270) qpERR_ABORT_QDB_IN_ROW_SIZE_ERROR IN ROW size exceeds the
maximum limit.**

**Cause:** A column cannot be created because the IN ROW size exceeds the
maximum limit.

**Action:** Create a column whose IN ROW size is less than the maximum limit.

**0x31243 ( 201283) qpERR_ABORT_QDB_MISMATCHED_LOB_TYPE_COLUMN Mismatched LOB
type column \<0%s\>**

**Cause:** A LOB type column mismatch has occurred.

**Action:** Check the column specification.

**0x31244 ( 201284) qpERR_ABORT_QDB_NOT_FOUND_LOB_TYPE_COLUMN LOB type column
not found.**

**Cause:** The specified LOB type column was not found in the table.

**Action:** Check the LOB type column specification.

**0x31257 ( 201303) qpERR_ABORT_QDB_LOB_VIOLATION_ON_VOLATILE_TABLE A volatile
table cannot have a LOB column.**

**Cause:** You tried to create or alter a table with a LOB column.

**Action:** Retry this action without the LOB column specification.

**0x3125D ( 201309) qpERR_ABORT_QDB_DUPLICATE_PARTITION_NAME Duplicate partition
name \<0%s\>**

**Cause:** Duplicate partition name

**Action:** Verify that no duplicate partition names have been specified.

**0x3125E ( 201310) qpERR_ABORT_QDB_TOO_MANY_PARTITION_CONDITION_LIST A
partition condition list contains too many elements**

**Cause:** Too many partition condition elements

**Action:** Verify that the number of partition condition elements is less than
or equal to the number of partition key columns.

**0x3125F ( 201311) qpERR_ABORT_QDB_DUPLICATE_PARTITION_KEY_COLUMN_NAME
Duplicate partition key column name \<0%s\>**

**Cause:** Duplicate partition key column name

**Action:** Verify that no duplicate partition key column names are specified.

**0x31260 ( 201312) qpERR_ABORT_QDB_INVALID_PARTITION_KEY_COLUMN_TYPE Invalid
partition key column type \<0%s\>**

**Cause:** Invalid partition key column type

**Action:** Check the partition key column type.

**0x31261 ( 201313) qpERR_ABORT_QDB_INVALID_PARTITION_KEY_COLUMN_NAME Invalid
partition key column name \<0%s\>**

**Cause:** A column which dose not belong to the partitioned table is used as a
partition key.

**Action:** Check the name of partition key column.

**0x31262 ( 201314) qpERR_ABORT_QDB_MAX_PARTITION_KEY_COLUMN_COUNT Too many
partition key columns**

**Cause:** Only one partition key is allowed in a list partition.

**Action:** Check the number of partition key columns.

**0x31263 ( 201315) qpERR_ABORT_QDB_INVALID_DEFAULT_PARTITION_COUNT The number
of default partitions must be one in a range or list partitioned table**

**Cause:** Invalid default partition count in a range or list partitioned table.

**Action:** Check the number of default partitions.

**0x31264 ( 201316) qpERR_ABORT_QDB_NO_CREATE_PARTITION_IN_MEMORY_TBS Unable to
create a partitioned table or partition in the memory tablespace.**

**Cause:** Unable to create a partitioned table or partition in the memory
tablespace

**Action:** Check the specified tablespace.

**0x31265 ( 201317) qpERR_ABORT_QDB_INVALID_PART_COND_VALUE Invalid partition
key condition value : \<0%s\>**

**Cause:** Partition key condition value is invalid.

**Action:** Check the partition key condition value.

**0x31266 ( 201318) qpERR_ABORT_QDB_DUPLICATE_PART_COND_VALUE Duplicate
partition key condition value : \<0%s\>**

**Cause:** Duplicate partition key condition value.

**Action:** Check the partition key condition value.

**0x31267 ( 201319)
qpERR_ABORT_QDB_INVALID_DEFAULT_PART_COUNT_IN_HASH_PART_TABLE Hash partitioned
table cannot have default partition**

**Cause:** Invalid default partition count in hash partitioned table

**Action:** Check the number of default partitions.

**0x31268 ( 201320)
qpERR_ABORT_QDB_CANNOT_ALTER_TABLE_PARTITION_ON_NONE_PART_TABLE Unable to alter
table partition on non-partitioned table**

**Cause:** Unable to alter table partition on a non-partitioned table

**Action:** Check the table specification.

**0x31269 ( 201321)
qpERR_ABORT_QDB_INVALID_PART_TABLE_METHOD_FOR_SPLIT_PARTITION_AT Split partition
AT must be used on range partitioned table**

**Cause:** The table is not a range partitioned table

**Action:** Check the partitioning method.

**0x3126A ( 201322)
qpERR_ABORT_QDB_INVALID_PART_TABLE_METHOD_FOR_SPLIT_PARTITION_VALUES Split
partition VALUES must be used in list partitioned table**

**Cause:** The table is not a list partitioned table.

**Action:** Check the partitioning method.

**0x3126B ( 201323) qpERR_ABORT_QDB_TOO_MANY_SPLIT_CONDITION_VALUE Too many
split condition values**

**Cause:** The number of split condition values should be less than or equal to
the number of partition key columns.

**Action:** Check the split condition values.

**0x3126C ( 201324) qpERR_ABORT_QDB_CANNOT_SPLIT_HASH_PART_TABLE Cannot split
partition in hash partitioned table**

**Cause:** Unable to split a partition in a hash partitioned table.

**Action:** Check the partitioning method.

**0x3126D ( 201325) qpERR_ABORT_QDB_SPLIT_CONDITION_VALUE_ON_RANGE_PARTITION
Split condition value must be between PARTITION_MIN_VALUE and
PARTITION_MAX_VALUE of the partition to be split**

**Cause:** Split condition value is less than PARTITION_MIN_VALUE or more than
PARTITION_MAX_VALUE.

**Action:** Check the split condition value.

**0x3126E ( 201326)
qpERR_ABORT_QDB_NOT_EXIST_SPLIT_CONDITION_VALUE_ON_LIST_PARTITION Split
condition value does not exist for the partition to be split**

**Cause:** The split condition value does not exist.

**Action:** Check the split condition values.

**0x3126F ( 201327)
qpERR_ABORT_QDB_ALREADY_EXIST_SPLIT_CONDITION_VALUE_ON_LIST_PARTITION Split
condition value already exists in another partition**

**Cause:** The split condition value already exists in another partition.

**Action:** Check the split condition values.

**0x31270 ( 201328) qpERR_ABORT_QDB_ALREADY_EXIST_PARTITION_NAME The partition
name is already used by the partitioned table \<0%s\>**

**Cause:** The partition name is already used by the partitioned table.

**Action:** Check the partition name.

**0x31273 ( 201331) qpERR_ABORT_QDB_CANNOT_MERGE_HASH_PART_TABLE Cannot merge
hash partitioned table**

**Cause:** - Unable to merge a hash partitioned table.

**Action:** Check the partitioning method.

**0x31274 ( 201332)
qpERR_ABORT_QDB_CANNOT_MERGE_NOT_ADJ_PARTITIONS_IN_RANGE_PART_TABLE Partitions
being merged are not adjacent**

**Cause:** Nonadjacent partitions cannot be merged.

**Action:** Check the position of the partitions being merged.

**0x31275 ( 201333) qpERR_ABORT_QDB_CANNOT_DROP_PARTITION_ON_HASH_PART_TABLE
Cannot drop partition from hash partitioned table**

**Cause:** Unable to drop a partition from a hash partitioned table.

**Action:** Check the partitioning method.

**0x31276 ( 201334) qpERR_ABORT_QDB_CANNOT_DROP_THE_ONLY_PARTITION Cannot drop
the only partition from a partitioned table**

**Cause:** Cannot drop the only partition from a partitioned table.

**Action:** Check the total partition count of the partitioned table.

**0x31277 ( 201335) qpERR_ABORT_QDB_CANNOT_DROP_THE_DEFAULT_PARTITION Cannot
drop the default partition**

**Cause:** Cannot drop the default partition.

**Action:** Check the partition value type.

**0x31278 ( 201336) qpERR_ABORT_QDB_CANNOT_ADD_PARTITION_ON_NONE_HASH_PART_TABLE
Cannot add a partition to a non-hash partitioned table**

**Cause:** Unable to add a partition to a non-hash partitioned table.

**Action:** Check the partitioning method.

**0x31279 ( 201337)
qpERR_ABORT_QDB_CANNOT_COALESCE_PARTITION_ON_NONE_HASH_PART_TABLE Cannot
coalesce partitions in non-hash partitioned table**

**Cause:** Unable to coalesce partitions in non-hash partitioned table.

**Action:** Check the partitioning method.

**0x3127A ( 201338) qpERR_ABORT_QDB_CANNOT_COALESCE_THE_ONLY_PARTITION Cannot
coalesce the only partition of a partitioned table**

**Cause:** Cannot coalesce the only partition of a partitioned table.

**Action:** Check the total partition count of a partitioned table.

**0x3127B ( 201339) qpERR_ABORT_QDB_TOO_LONG_PARTITION_CONDITION_VALUE The
length of a partition condition value is too long**

**Cause:** Partition condition value too long.

**Action:** Check the length of all partition condition values.

**0x3127C ( 201340) qpERR_ABORT_DUP_SPLIT_COND_VALUE_ON_LIST_PARTITION Duplicate
split condition value**

**Cause:** Duplicate split condition value

**Action:** Check the split condition values for duplicates.

**0x3127D ( 201341) qpERR_ABORT_QDB_NOT_EXIST_PARTITIONED_INDEX The partitioned
index was not found in the partitioned table : \<0%s\>**

**Cause:** Partitioned index not found.

**Action:** Check the partitioned index name.

**0x3127E ( 201342) qpERR_ABORT_QDB_DUP_PARTITIONED_INDEX_NAME Duplicate
partitioned index name : \<0%s\>**

**Cause:** Duplicate partitioned index name.

**Action:** Check all partitioned index names for duplicates.

**0x312A7 ( 201383) qpERR_ABORT_QDB_DUPLICATE_TABLE_ATTRIBUTE Duplicate table
attribute. \<0%s\>**

**Cause:** The user tried to specify a duplicate attribute name in the list of
table attributes.

**Action:** Check the list of table attributes.

**0x312A8 ( 201384) qpERR_ABORT_QDB_UNABLE_TO_COMPRESS_VOLATILE_TBS_LOG Log
compression not supported for volatile tablespace.**

**Cause:** The user tried to compress a volatile tablespace log.

**Action:** No action is necessary.

**0x312AB ( 201387) qpERR_ABORT_QDB_NOT_ALLOWED_PROC_IN_DEFAULT Procedure or
function not allowed here. \<0%s\>**

**Cause:** A procedure or function was specified in an inappropriate place in a
statement.

**Action:** Verify that the procedure or function name is correct and in the
correct place, or remove it.

**0x312C4 ( 201412) qpERR_ABORT_QDB_REPLICATION_DDL_DISABLED Cannot execute this
DDL on a replicated table when the system property REPLICATION_DDL_ENABLE is
0.**

**Cause:** System property REPLICATION_DDL_ENABLE is 0.

**Action:** Check the system property REPLICATION_DDL_ENABLE.

**0x312C5 ( 201413) qpERR_ABORT_QDB_CANNOT_DDL_WITH_RECOVERY Cannot execute this
DDL with replication recovery.**

**Cause:** Replication recovery is set.

**Action:** Check replication recovery.

**0x312C6 ( 201414) qpERR_ABORT_QDB_CANNOT_WRITE_REPL_INFO Cannot execute this
DDL on a replicated table when the session property REPLICATION is NONE.**

**Cause:** Session property REPLICATION is set to NONE.

**Action:** Check the session property REPLICATION.

**0x312D6 ( 201430) qpERR_ABORT_QDB_ADD_COL_UNIQUE_KEY_WITH_REPLICATED_TBL It is
forbidden to add a unique key column to a replicated table.**

**Cause:** A unique key column cannot be added to a replicated table.

**Action:** Drop the replication.

**0x312D8 ( 201432) qpERR_ABORT_QDB_ADD_COL_NOT_NULL_WITH_REPLICATED_TBL It is
forbidden to add a not null column to a replicated table.**

**Cause:** A NOT NULL column cannot be added to a replicated table.

**Action:** Drop the replication.

**0x312D9 ( 201433) qpERR_ABORT_QDB_DROP_COL_NOT_NULL_WITH_REPLICATED_TBL It is
forbidden to drop a not null column from a replicated table.**

**Cause:** A NOT NULL column cannot be dropped from a replicated table.

**Action:** Drop the replication.

**0x312DB ( 201435) qpERR_ABORT_QDB_DROP_COL_HAS_REPL_CONDITION It is forbidden
to drop a column for which a replication condition exists.**

**Cause:** A column with a replication condition cannot be dropped.

**Action:** Remove the replication condition.

**0x312E8 ( 201448) qpERR_ABORT_QDB_INVALID_INIT_TRANS The INITRANS value must
be between \<0%d\> and \<1%d\>**

**Cause:** Invalid INITRANS value.

**Action:** Check the INITRANS value.

**0x312E9 ( 201449) qpERR_ABORT_QDB_INVALID_MAX_TRANS The MAXTRANS value must be
between \<0%d\> and \<1%d\>**

**Cause:** Invalid MAXTRANS value.

**Action:** Check the MAXTRANS value.

**0x312EA ( 201450) qpERR_ABORT_QDB_MAXTRANS_LESS_INITTRANS MAXTRANS cannot be
less than INITRANS.**

**Cause:** The MAXTRANS value cannot be less than the INITRANS value.

**Action:** Check the INITRANS and MAXTRANS values.

**0x312ED ( 201453) qpERR_ABORT_QDB_INVALID_MODIFICATION Invalid modification of
column \<0%s\>**

**Cause:**

\# - 1. Modifying the data type on the columns with a type of char, blob, clob,
nibble, byte, timestamp, or geometry is not allowed.

\# - 2. Modifying data type of columns into blob, clob, timestamp, or geometry
is not allowed.

\# - 3. The columns with a type of char, varchar, echar, evarchar cannot be
encrypted using the ENCRYPT clause.

\# - 4. The data type of a column cannot be modified; however, the data type
length can be increased if the column refers to a foreign key.

\# - 5. The data type of a column cannot be modified; however, the data type can
be increased if the column is used as a partition key.

**Action:** Check modification of the column.

**0x312EE ( 201454) qpERR_ABORT_QDB_INVALID_LENGTH Invalid length for the data
type \<0%s\>**

**Cause:** The data type length was invalid.

**Action:** Check the length of the data type.

**0x312EF ( 201455) qpERR_ABORT_QDB_INVALID_NULL_VALUE Unable to add NOT NULL
constraint to the specified column because it already contains null values
\<0%s\>**

**Cause:** One or more records in the specified column has a null value.

**Action:** Check the column specification.

**0x312FC ( 201468) qpERR_ABORT_QDB_COMMENT_TOO_LONG Comment string is too
long.**

**Cause:** The comment string is too long. It must not exceed 4000 bytes.

**Action:** Check the length of the comment string.

**0x312FD ( 201469) qpERR_ABORT_QDB_COMMENT_NOT_SUPPORT_SEQUENCE COMMENT ON
statements are not supported for sequences.\<0%s\>**

**Cause:** COMMENT ON statements are not supported for sequences.

**Action:** Check the object type.

**0x312FE ( 201470) qpERR_ABORT_QDB_COMMENT_NOT_SUPPORT_PSM COMMENT ON
statements are not supported for PSMs. \<0%s\>**

**Cause:** COMMENT ON statements are not supported for PSMs.

**Action:** Check the object type.

**0x312FF ( 201471) qpERR_ABORT_QDB_COMMENT_NOT_SUPPORT_OBJ COMMENT ON
statements are not supported for this Object. \<0%s\>**

**Cause:** COMMENT ON statements are only supported for user tables and views.

**Action:** Check the object type.

**0x3131A ( 201498) qpERR_ABORT_QDB_NOT_ALLOWED_ENCRYPTED_COLUMN_ACCESS
Encrypted column access is not permitted due to the security module.**

**Cause:** Encrypted column access is not permitted due to the security module.

**Action:** Check the security module.

**0x3131F ( 201503) qpERR_ABORT_QDB_ALREADY_EXIST_INDEX_PARTITION_NAME The index
name for a new partition must differ from those of existing index partitions.
\<0%s\>**

**Cause:** Index names of new partitions must differ from existing index
partition names.

**Action:** Ensure that the new index partition name is different from the name
of any existing partition (including the one being renamed) of a given table or
index.

**0x31320 ( 201504) qpERR_ABORT_QDB_INVALID_INDEX_PARTITION_NAME The specified
index partition name did not match the name of an existing index partition.
\<0%s\>**

**Cause:** The specified index partition name did not match an existing index
partition.

**Action:** Ensure that the index partition name exists.

**0x31321 ( 201505) qpERR_ABORT_QDB_DROP_MULTI_COLUMN_CONSTRAINT_EXIST It is
forbidden to drop a column that has multi-column constraints.**

**Cause:** A column with multi column constraints cannot be dropped.

**Action:** Drop all multi-column constraints related to the dropped column
first, and then retry this statement.

**0x3133A ( 201530) qpERR_ABORT_QDB_INVALID_TBS_FOR_PCTFREE_PCTUSED PCTFREE and
PCTUSED can only be used with disk tablespaces.**

**Cause:** PCTFREE and PCTUSED can only be used with disk tablespaces.

**Action:** Check the tablespace type.

**0x3133B ( 201531) qpERR_ABORT_QDB_RESERVED_WORD_IN_OBJECT_NAME Invalid object
name : \<0%s\>**

**Cause:** Object names cannot start with reserved words.

**Action:** Change the object name.

**0x3135E ( 201566) qpERR_ABORT_QDB_INVALID_TABLE_OPTION Invalid table option
\<0%s\>**

**Cause:** A table option was missing or invalid.

**Action:** Check the table options.

**0x3135F ( 201567)
qpERR_ABORT_QDB_CANNOT_CREATE_TEMPORARY_TABLE_IN_NONVOLATILE_TBS Temporary
tables cannot be created in non-volatile tablespaces.**

**Cause:** An attempt was made to create a temporary table in a tablespace other
than a volatile tablespace.

**Action:** Create the temporary table in a volatile tablespace.

**0x31360 ( 201568) qpERR_ABORT_QDB_NOT_SUPPORTED_TEMPORARY_TABLE_FEATURE
Unsupported temporary table feature**

**Cause:** One of the table features specified in the temporary table creation
statement is not supported.

**Action:** Avoid specifying unsupported features when creating temporary
tables.

**0x31363 ( 201571) qpERR_ABORT_QDB_TEMPORARY_TABLE_DDL_DISABLE Cannot execute
DDL when a temporary table is in use.**

**Cause:** The DDL could not be executed because there are one or more temporary
tables based on the table.

**Action:** Truncate all temporary tables based on the table and try again.

**0x3138A ( 201610) qpERR_ABORT_QDB_ADD_COL_CHECK_WITH_REPLICATED_TBL It is
forbidden to add a column having check constraint to a replicated table.**

**Cause:** A column with a check constraint cannot be added to a replicated
table.

**Action:** Drop the replication.

**0x3138B ( 201611) qpERR_ABORT_QDB_DROP_COL_CHECK_WITH_REPLICATED_TBL It is
forbidden to drop a column having check constraint from a replicated table.**

**Cause:** A column with a check constraint cannot be dropped from a replicated
table.

**Action:** Drop the replication.

**0x3138C ( 201612) qpERR_ABORT_QDB_USE_SEQUENCE_IN_CHECK_CONSTRAINT A sequence
cannot be used as a CHECK constraint in a CREATE or ALTER TABLE statement.
\<0%s\>**

**Cause:** A sequence cannot be used as a CHECK constraint in a CREATE or ALTER
TABLE statement.

**Action:** Remove the sequences.

**0x3138D ( 201613) qpERR_ABORT_QDB_USE_VARIABLE_IN_CHECK_CONSTRAINT A variable
cannot be used as a CHECK constraint in a CREATE or ALTER TABLE statement.
\<0%s\>**

**Cause:** A variable cannot be used as a CHECK constraint in a CREATE or ALTER
TABLE statement.

**Action:** Remove the variables.

**0x3138E ( 201614) qpERR_ABORT_QDB_NOT_ALLOWED_CHECK_CONSTRAINT A check
constraint is not allowed here. \<0%s\>**

**Cause:** A check constraint cannot be used here.

**Action:** Remove the check constraints.

**0x3138F ( 201615) qpERR_ABORT_QDB_NOT_ALLOWED_COLUMN_HAVING_CHECK_CONSTRAINT A
column having check constraint is not allowed here. \<0%s\>**

**Cause:** A column with a check constraint cannot be used here.

**Action:** Remove the check constraints.

**0x31399 ( 201625) qpERR_ABORT_QDB_INVALID_DEFAULT_EXPRESSION Invalid default
expression : \<0%s\>**

**Cause:** The default expression is incorrect.

**Action:** Check the default expression.

**0x3139D ( 201629) qpERR_ABORT_QDB_CANNOT_USE_HIDDEN_COLUMN Cannot use columns
generated by a function-based index \<0%s\>**

**Cause:** Cannot use columns generated by a function-based index

**Action:** Remove the columns.

**0x3139E ( 201630) qpERR_ABORT_QDB_CANNOT_ALTER_HIDDEN_COLUMN Cannot alter
hidden columns \<0%s\>**

**Cause:** Cannot alter hidden columns

**Action:** Check the column type.

**0x313B6 ( 201654) qpERR_ABORT_QDB_COMPRESSION_NOT_SUPPORTED_DATATYPE
Unsupported data type on compression column. \<0%s\>**

**Cause:** Dictionary based compression columns do not support some types

**Action:** Check the column type.

**0x313B7 ( 201655) qpERR_ABORT_QDB_COMPRESSION_NOT_SUPPORTED_TABLESPACE
Unsupported tablespace type on compression column.**

**Cause:** Dictionary based compression columns support only memory tablespaces.

**Action:** Check the tablespace type.

**0x313B8 ( 201656) qpERR_ABORT_QDB_CANNOT_DDL_DML_DICTIONARY_TABLE Cannot
execute DDL/DML on dictionary table.**

**Cause:** DDL/DML cannot be executed on a dictionary table.

**Action:** Check the specified table.

**0x313B9 ( 201657) qpERR_ABORT_QDB_CANNOT_CREATE_COMPRESSION_COLUMN_REPLICATION
Cannot create compression column on the replicated table \<0%s\>**

**Cause:** Compression columns do not support replication.

**Action:** Drop the compression column.

**0x313BA ( 201658) qpERR_ABORT_QDB_CANNOT_ALTER_COMPRESSION_COLUMN Cannot alter
compression column \<0%s\>**

**Cause:** Cannot alter compression columns.

**Action:** Check the column type.

**0x313D3 ( 201683) qpERR_ABORT_QDB_NO_CREATE_PARTITION_IN_COMPOSITE_TBS
Partitions of a partitioned table cannot be stored in both memory and disk
tablespaces.**

**Cause:** Partitions of a partitioned table cannot be stored in both memory and
disk tablespaces.

**Action:** Check whether the tablespace types are the same.

**0x313D1 ( 201681) qpERR_ABORT_QDB_UNABLE_TO_COMPRESS_MEM_PARTITION Columnar
compression is unsupported for memory partitioned tables.**

**Cause:** Columnar compression is unsupported for memory partitioned tables.

**Action:** Check whether the table is a memory partitioned table.

**0x313D4 ( 201684) qpERR_ABORT_QDB_CANNOT_ALTER_REORGANIZE_COMPRESSION_COLUMN
ALTER REORGANIZE statement cannot be executed on uncompressed columns. \<0%s\>**

**Cause:** The 'ALTER REORGANIZE' statement cannot executed on uncompressed
columns.

**Action:** Check the column.Check whether the specified column is compressed or
not.

**0x313EE ( 201710) qpERR_ABORT_QDB_ADD_COL_COMPRESSION_COL_WITH_REPLICATED_TBL
A compressed column cannot be added to a replication target table.**

**Cause:** A compressed column cannot be added to a replication target table.

**Action:** Do not add a compressed column to a replication target table.

**0x313EF ( 201711)
qpERR_ABORT_QDB_CANNOT_ALTER_REORGANIZE_COMPRESSION_COL_WITH_REPLICATED_TBL A
compressed column of a replication target table cannot be reorganized.**

**Cause:** A compressed column of a replication target table cannot be
reorganized.

**Action:** Check whether the specified column is compressed or not.

**0x313F0 ( 201712) qpERR_ABORT_QDB_DROP_COMPRESSED_COLUMN_WITH_REPLICATE_TABLE
A compressed column cannot be dropped from a replication target table.**

**Cause:** A compressed column cannot be dropped from a replication target
table.

**Action:** Check whether the specified column is compressed or not.

**0x313F1 ( 201713) qpERR_ABORT_QDB_CANNOT_TRUNCATE_COMPRESSED_TABLE A
compressed table which is a replication target table cannot be truncated.**

**Cause:** A compressed table which is a replication target table cannot be
truncated.

**Action:** Check whether the specified table is compressed or not.

**0x3140B ( 201739) qpERR_ABORT_QDB_UNABLE_TO_COMPRESS_DISK_PARTITION Columnar
compression is unsupported for disk partitioned tables.**

**Cause:** Columnar compression is unsupported for disk partitioned tables.

**Action:** Check whether the table is a disk partitioned table.

**0x31430 ( 201776) qpERR_ABORT_QDB_DUPLICATE_TABLE_NAME Duplicate table name
\<0%s\>**

**Cause:** Duplicate table name, or the name is already used by an existing
object.

**Action:** Verify that no duplicate table names have been specified, or enter a
unique table name.

**0x31431 ( 201777) qpERR_ABORT_QDB_CANNOT_JOIN_DISJOIN_HASH_OR_NON_PART_TBL
Cannot conjoin/disjoin a hash partitioned table or a non-partitioned table.**

**Cause:** You can conjoin/disjoin tables only with non-hash partitioned tables.

**Action:** Verify that the target tables are range/list partitioned tables.

**0x31432 ( 201778) qpERR_ABORT_QDB_CANNOT_JOIN_PARTITIONED_TABLE Unable to
conjoin partitioned tables : \<0%s\>**

**Cause:** Only partitioned tables can be conjoined.

**Action:** Verify that the target table is not a partitioned table.

**0x31433 ( 201779) qpERR_ABORT_QDB_CANNOT_JOIN_DISJOIN_TABLE_SPEC Unable to
conjoin/disjoin tables with primary keys, unique keys, foreign keys, indexes,
and triggers. : \<0%s\>**

**Cause:** Only partitions without private keys, unique keys, foreign keys,
indexes, nor triggers can be exchanged.

**Action:** Verify that the table does not have any constraints, indexes, or
triggers.

**0x31434 ( 201780) qpERR_ABORT_QDB_JOIN_DISJOIN_NOT_READ_WRITE Not READ/WRITE**

\<0%s\>

**Cause:** A read only or read append table cannot be conjoined/disjoined

**Action:** Check the access option of the table.

**0x31435 ( 201781) qpERR_ABORT_QDB_JOIN_DIFFERENT_TABLE_SPEC Unidentical
table/column spec : \<0%s\>**

**Cause:** Unidentical table/column specification.

**Action:** Verify that the specifications(number of constraints,
number/names/order/type/scale/precision of columns, etc.) are identical.

**0x31436 ( 201782) qpERR_ABORT_QDB_JOIN_DIFFERENT_CONSTRAINT_SPEC Unidentical
constraint specification : \<0%s\>**

**Cause:** The table's constraint specification unidentical.

**Action:** Verify that the constraint specifications(type, scale, precision,
etc.) are identical.

**0x31437 ( 201783) qpERR_ABORT_QDB_CANNOT_JOIN_DISJOIN_COLUMN_SPEC Unable to
conjoin/disjoin hidden/encrypted/compressed columns : \<0%s\>**

**Cause:** Only partitions without any hidden/encrypted/compressed columns can
be exchanged.

**Action:** Verify that there are no hidden/encrypted/compressed columns.

**0x31438 ( 201784) qpERR_ABORT_QDB_DISJOIN_NOT_ALL_PARTITION All partitions
should be listed in the DISJOIN table statement.**

**Cause:** One or more partitions are missing from the SQL statement.

**Action:** Verify that every partition is in the SQL statement.

**0x3143A ( 201786) qpERR_ABORT_QDB_CANNOT_SUPPORT_ON_HYBRID_PARTITIONED_TABLE
It is unsupported for the hybrid partitioned tables.**

**Cause:** It is unsupported for hybrid partitioned tables.

**Action:** Check whether the table is a hybrid disk partitioned table.

**0x3143B ( 201787) qpERR_ABORT_QDB_CANNOT_ALTER_PARTITION_ON_SAME_TABLESPACE
Alter partition cannot be move rows on same tablespaces.**

**Cause:** Alter partition cannot be move rows on same tablespaces.

**Action:** Check whether the tablespace of a target partition is a same
tablespace.

**0x3143C ( 201788) qpERR_ABORT_QDB_MINEXTENTS_LESS_INITEXTENTS MINEXTENTS
cannot be less than INITEXTENTS.**

**Cause:** The MINEXTENTS value cannot be less than the INITEXTENTS value.

**Action:** Check the INIEXTENTS and MINEXTENTS values.

**0x3143D ( 201789) qpERR_ABORT_QDB_MINEXTENTS_LESS_MAXEXTENTS MINEXTENTS cannot
be less than MAXEXTENTS.**

**Cause:** The MINEXTENTS value cannot be less than the MAXEXTENTS value.

**Action:** Check the MAXEXTENTS and MINEXTENTS values.

**0x3144B ( 201803) qpERR_ABORT_QDB_CANNOT_ALTER_TABLESPACE_ON_SAME_TABLESPACE
Alter tablespace cannot be move rows on same tablespaces.**

**Cause:** The user tried to move rows by executing a MOVE statement on the same
tablespace. Alter tablespace cannot be move rows on the same tablespaces.

**Action:** Do not execute a MOVE statement on the rows in the same tablespace.
Change the tablespace of target table.

**0x3144C ( 201804) qpERR_ABORT_QDB_CANNOT_ALTER_TABLESPACE_ON_NONE_PART_INDEX
Cannot alter the tablespace for a partitioned table with a non-partitioned
index.**

**Cause:** The tablespace cannot be altered for a partitioned table with a
non-partitioned index.

**Action:** Remove the non-partitioned index.

**0x3144D ( 201805) qpERR_ABORT_QDB_MEMORY_USAGE_THRESHOLD Need more memory
resource. Progress : \<0%u\>%, Threshold : \<1%u\>%, Estimated Page Count :
\<2%lu\>.**

**Cause:** There is not enough free space in the memory to execute this DDL
statements.

**Action:** Free up space of memory.

**0x3144E ( 201806) qpERR_ABORT_QDB_TBS_USAGE_THRESHOLD Need more free space of
tablespace. Tablespace Name: \<0%s\>, Progress : \<1%u\>%, Threshold : \<2%u\>%,
Estimated Page Count : \<3%lu\>.**

**Cause:** The tablespace does not have enough free space to execute DDL.

**Action:** Free up space of tablespace.

**0x3144F ( 201807) qpERR_ABORT_QDB_NOT_EXIST_INDEX The index was not found in
the table : \<0%s\>**

**Cause:** Index not found.

**Action:** Check the index name.

**0x31458 ( 201816) qpERR_ABORT_QDB_CANNOT_ALTER_TABLESPACE_TEMPORARY_TABLE A
temporary table cannot modify the tablespace.**

**Cause:** ALTER TABLESPACE cannot be executed since a temporary table is
executed within the same tablespace.

**Action:** Do not execute the syntax of ALTER TABLESPACE on the temporary
table.

**0x3145B ( 201819)
qpERR_ABORT_QDB_USE_ONLY_DISK_TABLE_PARTITION_IN_DISK_EDITION Memory/volatile
tables or partitions cannot be used in disk edition.**

**Cause:** Only disk tables and partitions are allowed to use in the disk
edition.

**Action:** Use disk tables or disk partitions, otherwise purchase the
standard/enterprise edition.

**0x3145C ( 201820)
qpERR_ABORT_QDB_SET_ONLY_DISK_TO_DEFAULT_TABLESPACE_IN_DISK_EDITION Memory
tablelspace or volatile tablespace cannot be specified as the default tablespace
in the disk edition.**

**Cause:** The default tablespace can be specified only with disk tablespace in
the disk edition.

**Action:** Specify disk tablespace as the default tablespace or purchase the
standard/enterprise edition.

**0x3145E ( 201822) qpERR_ABORT_QDB_USE_SYNONYM_IN_CHECK_CONSTRAINT A synonym is
not allowed to be a CHECK constraint in a CREATE or ALTER TABLE statement.
\<0%s\>**

**Cause:** The synonym was used as a CHECK constraint in a CREATE or ALTER TABLE
statement.

**Action:** Remove the synonyms used in the statement.

**0x31030 ( 200752) qpERR_ABORT_QCV_NO_GRANT You do not have permission to
execute the SQL statement.**

**Cause:** You do not have permission to execute the SQL statement. (The SYS
user can access an arbitrary object in any SQL statement.)

**Action:** Verify that the user has enough permission to execute the SQL
statement.

**0x31189 ( 201097) qpERR_ABORT_QCV_NOT_EXISTS_USER User not found : \<0%s\>**

**Cause:** The name of the specified user was not found in the database.

**Action:** Verify that the user exists in the database.

**0x31031 ( 200753) qpERR_ABORT_QCV_NOT_EXISTS_TABLE Table not found : \<0%s\>**

**Cause:** The name of the specified table was not found in the database.

**Action:** Verify that the table exists in the database. Verify that there is
no typo in the table name.

**0x31032 ( 200754) qpERR_ABORT_QCV_NOT_ALLOWED_HOSTVAR Invalid use of host
variables**

**Cause:** A host variable was misused.

**Action:** Verify the position of every host variable.

**0x31199 ( 201113) qpERR_ABORT_QCV_DML_ON_SEQUENCE Unable to execute DML
statements on a sequence. \<0%s\>**

**Cause:** It is impossible to execute DML statements on a sequence.

**Action:** Specify a table name on which to execute the DML statements.

**0x3127F ( 201343) qpERR_ABORT_QCV_NOT_PARTITIONED_TABLE Table is not
partitioned : \<0%s\>**

**Cause:** The table is not partitioned.

**Action:** Verify that the specified table is partitioned.

**0x31035 ( 200757) qpERR_ABORT_QDS_DUPLICATE_SEQUENCE Duplicate sequence name**

**Cause:** The sequence name already exists in the database.

**Action:** Create a new sequence with a different name.

**0x31036 ( 200758) qpERR_ABORT_QDS_START_LESS_MIN START value cannot be less
than MIN value.**

**Cause:** The START value cannot be less than the MIN value.

**Action:** Check the START and MIN values.

**0x31037 ( 200759) qpERR_ABORT_QDS_START_MORE_MAX START value cannot be greater
than MAX value.**

**Cause:** The START value cannot be greater than the MAX value.

**Action:** Check the START and MAX values.

**0x3119B ( 201115) qpERR_ABORT_QDS_CURR_LESS_MIN CURRENT value cannot be less
than MIN value.**

**Cause:** The CURRENT value cannot be less than the MIN value.

**Action:** Check the CURRENT and MIN values.

**0x3119C ( 201116) qpERR_ABORT_QDS_CURR_MORE_MAX CURRENT value cannot be
greater than MAX value.**

**Cause:** The CURRENT value cannot be greater than the MAX value.

**Action:** Check the CURRENT and MAX values.

**0x31038 ( 200760) qpERR_ABORT_QDS_MIN_VALUE MIN value must be less than MAX
value.**

**Cause:** The MIN value must be less than the MAX value.

**Action:** Check the MIN and MAX values.

**0x31039 ( 200761) qpERR_ABORT_QDS_CACHE_VALUE CACHE value must be greater than
1.**

**Cause:** The CACHE value must be greater than 1.

**Action:** Check the CACHE value.

**0x3103A ( 200762) qpERR_ABORT_QDS_INCREMENT_VALUE INCREMENT value must be a
non-zero integer.**

**Cause:** The INCREMENT value must be a non-zero integer.

**Action:** Check the INCREMENT value.

**0x3103B ( 200763) qpERR_ABORT_QDS_INVALID_INCREMENT_VALUE INCREMENT value must
be less than the difference between MAX and MIN values.**

**Cause:** The INCREMENT value must be less than the difference between the MAX
and MIN values.

**Action:** Check the INCREMENT, MAX, and MIN values.

**0x3131C ( 201500) qpERR_ABORT_QDS_OVERFLOW_MAXVALUE MAXVALUE is greater than
internal sequence maximum value (\<0%s\>).**

**Cause:** The MAXVALUE specified for a query was greater than the maximum value
allowed for the server.

**Action:** Change the value so that it is less than the maximum and repeat the
query.

**0x3131D ( 201501) qpERR_ABORT_QDS_OVERFLOW_MINVALUE MINVALUE is less than
internal sequence minimum value (\<0%s\>).**

**Cause:** The MINVALUE specified for a query was less than the minimum value
allowed for the server.

**Action:** Change the value so that it is greater than the minimum and repeat
the query.

**0x313D5 ( 201685) qpERR_ABORT_QDS_CANNOT_ALTER_SEQ_TABLE Unable to alter the
sequence with sync table option**

**Cause:** Unable to alter the sequence with the sync table option.

**Action:** Change the sync table option of the sequence.

**0x3103C ( 200764) qpERR_ABORT_QDR_NOT_EXISTS_USER Undefined user name. The
user specified as the owner of a table or an object was not found in the
database. \<0%s\>**

**Cause:** The user specified as the owner of a table or an object was not found
in the database.

**Action:** Verify that a user name corresponding to the owner of an object is
registered in the database.

**0x3103D ( 200765) qpERR_ABORT_QDR_DUPLICATE_USER Duplicate user or role names.
The user name already exists in the database.**

**Cause:** The user or role name to be created already exists in the database.

**Action:** Use another user or role name.

**0x3136C ( 201580) qpERR_ABORT_QDR_INVALID_RESOURCE_LIMIT Internal resource
limit exceeded**

**Cause:** A specified value exceeded an internal server limitation.

**Action:** Specify a lower value.

**0x3136D ( 201581) qpERR_ABORT_QDR_PASSWORD_POLICY_SYSDBA Only SYS user can
change password policy**

**Cause:** Only the SYS user can change password options.

**Action:** Log in as the SYS user and try again.

**0x3136E ( 201582) qpERR_ABORT_QDR_NOT_ALLOWED_LOCK Only SYS user can lock
users**

**Cause:** Only the SYS user can explicitly lock other users.

**Action:** Log in as the SYS user and try again.

**0x3136F ( 201583) qpERR_ABORT_QDR_COUNT_LIMIT Internal count limit exceeded**

**Cause:** A specified count value exceeded the internal server limitation of
1000.

**Action:** Specify a count limit less than 1000.

**0x3103F ( 200767) qpERR_ABORT_QDD_DDL_WITH_REPLICATED_TBL No DDL statement may
be executed on a replicated table.**

**Cause:** An attempt was made to execute a DDL statement on a replicated table.

**Action:** Verify that the specified table is not replicated.

**0x31040 ( 200768) qpERR_ABORT_QDD_NO_DROP_SYS_USER It is forbidden to drop the
SYS user.**

**Cause:** You cannot drop the SYS user.

**Action:** Verify that the specified user name is not SYS.

**0x31041 ( 200769) qpERR_ABORT_QDD_EXIST_OWN_OBJECT The user cannot be dropped
because the user still owns one or more objects.**

**Cause:** The user to be dropped owns at least one object.

**Action:** Drop every object owned by the user being dropped.

**0x3119E ( 201118) qpERR_ABORT_QDD_DROP_SYSTEM_INDEX The primary key or unique
key constraint cannot be dropped using the DROP INDEX statement. Use the ALTER
TABLE statement.**

**Cause:** The primary key or unique key constraint cannot be dropped using the
DROP INDEX statement.

**Action:** Use the ALTER TABLE statement.

**0x311A5 ( 201125) qpERR_ABORT_QDD_NO_DROP_META_TABLE It is forbidden to
execute ALTER, DROP or TRUNCATE TABLE statements on a meta table.**

**Cause:** You cannot alter, drop or truncate meta tables.

**Action:** Check the table name.

**0x31280 ( 201344) qpERR_ABORT_QDD_PART_TABLE_BELONGS_TO_ANOTHER_USER
Partitioned table belongs to another user**

**Cause:** The partitioned table belongs to another user.

**Action:** Drop the partitioned table first, and then retry this statement.

**0x31281 ( 201345) qpERR_ABORT_QDD_PART_INDEX_BELONGS_TO_ANOTHER_USER
Partitioned index belongs to another user**

**Cause:** The partitioned index belongs to another user.

**Action:** Drop the partitioned index first, and then retry this statement.

**0x312C7 ( 201415) qpERR_ABORT_QDD_DROP_COL_PRIMARY_KEY_WITH_REPLICATED_TBL It
is forbidden to drop a primary key column from a replicated table.**

**Cause:** A primary key column cannot be dropped from a replicated table.

**Action:** Drop the replication.

**0x312D7 ( 201431) qpERR_ABORT_QDD_DROP_COL_UNIQUE_KEY_WITH_REPLICATED_TBL It
is forbidden to drop a unique key column from a replicated table.**

**Cause:** A unique key cannot be dropped from a replicated table.

**Action:** Drop the replication.

**0x312DA ( 201434) qpERR_ABORT_QDD_INVALID_STORAGE_OPTION_VALUE invalid \<0%s\>
storage option value.**

**Cause:** Invalid STORAGE clause option value.

**Action:** Specify a valid option value.

**0x31366 ( 201574) qpERR_ABORT_QDD_DROP_USER_DISABLE_BECAUSE_TEMP_TABLE Could
not drop user because temporary table in use.**

**Cause:** The user could not be dropped because there are one or more temporary
tables based on tables in the user schema.

**Action:** Truncate all temporary tables based on tables in the user schema and
try again.

**0x31374 ( 201588) qpERR_ABORT_QDD_NOT_EXIST_MVIEW Materialized view not found
: \<0%s\>**

**Cause:** The name of the specified materialized view was not found in the
database.

**Action:** Verify that the materialized view exists in the database. Verify
that the name of the materialized view was entered correctly.

**0x31042 ( 200770) qpERR_ABORT_QDN_NOT_EXISTS_CONSTRAINT Constraint not
found.**

**Cause:** The specified constraint name was not found in the database.

**Action:** Verify that the constraint name exists in the SYS_CONSTRAINTS\_ meta
table.

**0x31043 ( 200771) qpERR_ABORT_QDN_NOT_EXISTS_UNIQUE_KEY UNIQUE KEY constraint
not found in the table.**

**Cause:** The UNIQUE KEY constraint was not found in the table.

**Action:** Check the UNIQUE KEY constraint in the meta tables.

**0x31044 ( 200772) qpERR_ABORT_QDN_NOT_EXISTS_PRIMARY_KEY PRIMARY KEY
constraint not found in the table.**

**Cause:** The PRIMARY KEY constraint was not found in the table.

**Action:** Check the PRIMARY KEY constraint in the meta tables.

**0x31045 ( 200773) qpERR_ABORT_QDN_DUPLICATE_PRIMARY_KEY A primary key already
exists in the table.**

**Cause:** The table already has a primary key. A table can have only one
primary key.

**Action:** If a primary key already exists, drop the key before creating a new
one.

**0x31046 ( 200774) qpERR_ABORT_QDN_DUPLICATE_CONSTRAINT Duplicate constraint
name : \<0%s\>**

**Cause:** The constraint name already exists in the database.

**Action:** If a constraint with the same name already exists, create a
constraint with a different name.

**0x31047 ( 200775) qpERR_ABORT_QDN_MAX_KEY_COLUMN_COUNT Too many key columns**

**Cause:** Too many key columns.

**Action:** Reduce the number of columns in the index.

**0x31049 ( 200777) qpERR_ABORT_QDN_REFERENCED_CONSTRAINT_NOT_FOUND Unable to
find referenced constraint**

**Cause:** There is no primary key or unique constraint in the referenced column
list

**Action:** Verify that a referenced constraint exists in the reference column
list.

**0x3104A ( 200778) qpERR_ABORT_QDN_ADD_COL_NO_DEFAULT_NOTNULL Unable to add NOT
NULL constraint to a column without a DEFAULT value**

**Cause:** It is impossible to add a NOT NULL constraint to a column for which a
DEFAULT value has not been specified.

**Action:** Remove the NOT NULL constraint from the column specification, or
specify a DEFAULT value for the column.

**0x3104B ( 200779) qpERR_ABORT_QDN_DUPLICATE_CONSTRAINT_SPEC Unable to create
or add a constraint for the column because it already has the same constraint.**

**Cause:** There is at least one similar constraint for the column.

**Action:** Check the constraint definition.

**0x31190 ( 201104) qpERR_ABORT_QDN_NOT_COMPATIBLE_TYPE Incompatible data
types**

**Cause:** The data types are incompatible.

**Action:** Check the data types.

**0x311C5 ( 201157) qpERR_ABORT_QDN_CANNOT_DROP_TIMESTAMP Unable to drop a
TIMESTAMP constraint.**

**Cause:** It is impossible to drop a TIMESTAMP constraint.

**Action:** Execute the ALTER TABLE DROP COLUMN statement.

**0x31230 ( 201264) qpERR_ABORT_QDN_SELF_REFERENCE_NOT_SUPPORTED Self
referential constraints are not supported yet.**

**Cause:** Self referential constraints are not supported.

**Action:** Check the SQL statement.

**0x31238 ( 201272) qpERR_ABORT_QDN_MISMATCHED_REFERENCING_COLUMN_COUNT Number
of referencing columns must match number of referenced columns.**

**Cause:** The number of referencing columns that you listed did not match the
primary key or unique key.

**Action:** Check the referencing columns that you listed.

**0x31282 ( 201346) qpERR_ABORT_QDN_NOT_EXISTS_LOCAL_UNIQUE_KEY LOCAL UNIQUE KEY
constraint not found in the table.**

**Cause:** The LOCAL UNIQUE KEY constraint was not found in the table.

**Action:** Check the LOCAL UNIQUE KEY constraint in the meta tables.

**0x31291 ( 201361)
qpERR_ABORT_QDN_CANNOT_CREATE_LOCAL_UNIQUE_KEY_CONSTR_ON_NON_PART_TABLE Cannot
create a local unique key constraint for a non-partitioned table.**

**Cause:** A local unique key constraint cannot be created on a non partitioned
table.

**Action:** Check the partitioning method of the table.

**0x312C8 ( 201416) qpERR_ABORT_QDN_ADD_COL_FOREIGN_KEY_WITH_REPLICATED_TBL It
is forbidden to add a foreign key column to a replicated table.**

**Cause:** A foreign key column cannot be added to a replicated table.

**Action:** Drop the replication.

**0x31323 ( 201507) qpERR_ABORT_QDN_NOT_SUPPORTED_CONSTR_STATE This kind of
constraint does not permit this constraint state. \<0%s\>**

**Cause:** A constraint does not allow this constraint state.

**Action:** Specify a constraint state that is permissible for this constraint.

**0x31361 ( 201569) qpERR_ABORT_QDN_CANNOT_CREATE_FOREIGN_KEY_ON_TEMPORARY_TABLE
Cannot create a referential constraint for a temporary table.**

**Cause:** A foreign key was specified in a temporary table creation statement.

**Action:** Do not attempt to specify a foreign key when creating a temporary
table.

**0x31390 ( 201616) qpERR_ABORT_QDN_NOT_SUPPORT_LOB_COLUMN_IN_CHECK_CONSTRAINT
Unsupported use of LOB column in a CHECK constraint \<0%s\>**

**Cause:** One or more LOB columns were referenced in a CHECK constraint.

**Action:** Remove the LOB column(s) from the CHECK constraint.

**0x31391 ( 201617) qpERR_ABORT_QDN_INVALID_CHECK_CONSTRAINT_EXPRESSION Invalid
check constraint \<0%s\> expression**

**Cause:** The check constraint expression is incorrect.

**Action:** Check the check constraint expression.

**0x31392 ( 201618) qpERR_ABORT_QDN_VIOLATE_CHECK_CONSTRAINT Check constraint
\<0%s\> violated**

**Cause:** Some rows do not conform to the check constraint's requirements.

**Action:** Check all rows that are related to the check constraint.

**0x313FB ( 201723) qpERR_ABORT_QDN_NOT_SUPPORT_CONSTRAINT_IN_COMPRESSED_COLUMN
Unable to create or add the constraint for the compressed column. \<0%s\>**

**Cause:** The user tried to create a primary key, a unique key or a timestamp
constraint on the compressed column.

**Action:** Do not create a primary key, a unique key or a timestamp constraint
on the compressed column.

**0x31415 ( 201749) qpERR_ABORT_QDN_NOT_ALLOW_MEM_TBS_PK_UK_OF_GLOBAL_INDEX A
primary key or unique key constraint can be defined for a non-partitioned index
on a disk partitioned table.**

**Cause:** A primary key or unique key constraint can be defined for a
non-partitioned index on a disk partitioned table.

**Action:** Do define a primary key or unique key constraint for a
non-partitioned index on a disk partitioned table.

**0x3104C ( 200780) qpERR_ABORT_QDX_DUPLICATE_INDEX Duplicate index name**

**Cause:** The specified index name already exists in the database.

**Action:** Create a new index with a different name.

**0x3104D ( 200781) qpERR_ABORT_QDX_CRT_IDX_ON_REPLICATED_TBL It is forbidden to
create an index in a replicated table.**

**Cause:** An index cannot be created on a replicated table.

**Action:** Drop the replication.

**0x3104F ( 200783) qpERR_ABORT_QDX_INVALID_KEY_FIELD_COUNT Too many columns for
a composite index.**

**Cause:** It is impossible to create an index having more columns than the
maximum number of key columns in a composite index.

**Action:** Check the number of key columns in the composite index.

**0x31051 ( 200785) qpERR_ABORT_QDX_DUPLICATE_INDEX_COLS Duplicate key columns
in an index**

**Cause:** Duplicate columns exist in the description of an index.

**Action:** Create a new index with a different description.

**0x3123C ( 201276) qpERR_ABORT_QDX_INVALID_INDEX_COLS Invalid key columns in an
index**

**Cause:** Invalid key columns in an index.It is not permitted to create an
unique or composite index if the type of a column is geometry.

**Action:** Check the key columns.

**0x31237 ( 201271) qpERR_ABORT_QDX_CANNOT_CREATE_INDEX_DATATYPE cannot create
index in the data type.**

**Cause:** The user tried to create an index in the specified data type.

**Action:** Do not create an index in the specified data type.

**0x31283 ( 201347)
qpERR_ABORT_QDX_NOT_ALLOWED_PRIMARY_AND_UNIQUE_KEY_OF_NONE_PREFIXED_INDEX Unable
to create a primary key or a unique key constraint in the local non-prefixed
index.**

\# Cause: The user tried to create a primary key or a unique key constraint in
the local prefixed index.

**Action:** Do not create a primary key or a unique key constraint in the local
non-prefixed index.

**0x31284 ( 201348)
qpERR_ABORT_QDX_CANNOT_SPECIFY_TBS_OF_LOCAL_PARTITIONED_INDEX cannot specify
tablespace of partitioned index. \<0%s\>**

**Cause:** The tablespace cannot be specified for a partitioned index.

**Action:** Check the position of the tablespace.

**0x31285 ( 201349) qpERR_ABORT_QDX_INVALID_INDEX_PARTITION_COUNT Too many index
partitions.**

**Cause:** Too many index partitionsYou can create only the number of partitions
less than or equal to that of the table partitions.

**Action:** Check the number of index partitions.

**0x31286 ( 201350) qpERR_ABORT_QDX_CANNOT_CREATE_PART_INDEX_ON_NONE_PART_TABLE
cannot create a partitioned index in a non-partitioned table.**

**Cause:** Partitioned indexes cannot be created on non partitioned tables.

**Action:** Check the partitioning method of the table.

**0x31287 ( 201351)
qpERR_ABORT_QDX_CANNOT_ALTER_INDEX_REBUILD_ON_NONE_PART_INDEX cannot alter the
index rebuild for a non-partitioned index.**

**Cause:** The index rebuild cannot be altered for a non partitioned table.

**Action:** Check the partitioning method of the table.

**0x31288 ( 201352) qpERR_ABORT_QDX_NOT_EXIST_INDEX_PARTITION The index
partition does not exist.**

**Cause:** The index partition does not exist.

**Action:** Check the name of the index partition.

**0x31289 ( 201353) qpERR_ABORT_QDX_CANNOT_CREATE_NONE_PART_INDEX_ON_PART_TABLE
cannot create a non-partitioned index in a partitioned table.**

**Cause:** A non partitioned index cannot be created on a partitioned table.

**Action:** Check the partitioning method of the table.

**0x3129A ( 201370) qpERR_ABORT_QDX_NON_DISK_INDEX_LOGGING_OPTION LOGGING and
NOLOGGING options are only allowed for a disk B-Tree index.**

**Cause:** The LOGGING or NOLOGGING option was used for a non disk B-Tree index.

**Action:** Create an index without using the LOGGING or NOLOGGING options.

**0x312C9 ( 201417) qpERR_ABORT_QDX_NON_MEMORY_INDEX_PERSISTENT_OPTION The
PERSISTENT option is only allowed for a memory B-Tree index.**

**Cause:** The PERSISTENT option was used for a non memory B-Tree index.

**Action:** Create an index without the PERSISTENT option.

**0x31364 ( 201572) qpERR_ABORT_QDX_TEMPORARY_INDEX_NOT_ALLOW_TBS_NAME Cannot
specify tablespace when creating a temporary table index**

**Cause:** An attempt was made to specify a tablespace when creating a temporary
table index.

**Action:** Do not attempt to specify a tablespace when creating a temporary
table index.

**0x31398 ( 201624) qpERR_ABORT_QDX_CANNOT_SPECIFY_INDEX_PARTITION Cannot
specify local index partition for non-partitioned index**

**Cause:** Cannot specify a local index partition for non-partitioned index.

**Action:** Remove the local index partition reference.

**0x3139B ( 201627) qpERR_ABORT_QDX_NOT_SUPPORT_LOB_COLUMN LOB column is not
supported for a function-based index. \<0%s\>**

**Cause:** LOB columns are not supported for a function-based index.

**Action:** Remove any LOB column expression.

**0x3139C ( 201628) qpERR_ABORT_QDX_NOT_SUPPORT_ENCRYPTED_COLUMN Encrypted
column is not supported for a function-based index. \<0%s\>**

**Cause:** Encrypted columns are not supported for a function-based index.

**Action:** Remove any encrypted column expression.

**0x313D0 ( 201680)
qpERR_ABORT_QDX_CANNOT_CREATE_NONE_PART_INDEX_ON_MEM_PART_TABLE A
non-partitioned index can be created on a disk partitioned table.**

**Cause:** A non-partitioned index can be created on a disk partitioned table.

**Action:** Check whether the table is a disk partitioned table.

**0x31411 ( 201745) qpERR_ABORT_QDX_CREATE_HIDDEN_COLUMN_WITH_REPLICATED_TBL
Unable to create a function-based index on a replicated table.**

**Cause:** Cannot create a function-based index on a replicated table.

**Action:** Drop the replication object.

**0x31412 ( 201746) qpERR_ABORT_QDX_DROP_HIDDEN_COLUMN_WITH_REPLICATED_TBL
Unable to drop a function-based index from a replicated table.**

**Cause:** Cannot drop a function-based index from a replicated table.

**Action:** Drop the replication object.

**0x31419 ( 201753) qpERR_ABORT_QDX_CANNOT_CREATE_PARTITIONED_INDEX Cannot
create a partitioned index.**

**Cause:** The partitioned index does not have a partition key column.

**Action:** Set a partition key on the index key column, or create a localunique
index

**0x31454 ( 201812) qpERR_ABORT_QDX_NON_MEMORY_BTREE_INDEX_REORGANIZATION_OPTION
The reorganization option is only allowed for a memory B-Tree index.**

**Cause:** The reorganization option was used for a non memory B-Tree index.

**Action:** Remove the reorganization option from a non memory B-Tree index.

**0x31053 ( 200787) qpERR_ABORT_QMV_NOT_ENOUGH_INSERT_VALUES Not enough insert
values**

**Cause:** The number of columns is not equal to the number of values.

**Action:** Verify that the same number of columns and values are specified.

**0x31054 ( 200788) qpERR_ABORT_QMV_TOO_MANY_INSERT_VALUES Too many insert
values**

**Cause:** The number of columns is not equal to the number of values.

**Action:** Verify that the same number of columns and values are specified.

**0x31055 ( 200789) qpERR_ABORT_QMV_NOT_ALLOW_PRIMARY_KEY_UPDATE The primary key
of a table cannot be updated when the table is used for replication.**

**Cause:** The user tried to update the primary key of a table that was used for
replication.

**Action:** Verify that the table is not used for replication.

**0x31056 ( 200790) qpERR_ABORT_QMV_NOT_NULL_CONSTRAINT Unable to insert (or
update) NULL into a NOT NULL column.**

**Cause:** It is impossible to insert or update a NULL value into a NOT NULL
column.

**Action:** Drop the NOT NULL constraint or verify that the values to be
inserted or updated are not NULL values.

**0x31057 ( 200791) qpERR_ABORT_QMV_DML_ON_CLOSED_TABLE This table is not in
memory. \<0%s\>**

**Cause:** This table is not in memory.

**Action:** Execute the ALTER TABLE OPEN statement.

**0x31058 ( 200792) qpERR_ABORT_QMV_NOT_EXISTS_COLUMN Column not found \<0%s\>**

**Cause:** The specified column was not found in the table.

**Action:** Verify that the column name is correct.

**0x31059 ( 200793) qpERR_ABORT_QMV_COLUMN_AMBIGUOUS_DEF Ambiguous column name:
\<0%s\>**

**Cause:** Two or more tables to be selected have columns with the same name.

**Action:** Specify column names explicitly, such as 'table_name.column_name'.

**0x3105A ( 200794) qpERR_ABORT_QMV_NOT_EXISTS_ALIAS The specified alias name
was not found in the target list. \<0%s\>**

**Cause:** The specified alias name was not found in the target list.

**Action:** Check the alias names in the target list.

**0x3105B ( 200795) qpERR_ABORT_QMV_DUPLICATE_ALIAS Duplicate alias names were
found in the target list. \<0%s\>**

**Cause:** Duplicate alias names were found in the target list.

**Action:** Check the alias names in the target list.

**0x3105C ( 200796) qpERR_ABORT_QMV_NO_GROUP_EXPRESSION Not a group expression
in the target list**

**Cause:** If the SELECT statement includes a GROUP BY clause, only group
expressions can be used in the target list.

**Action:** Verify only the expressions in the GROUP BY clause are used in the
SELECT, WHERE, and ORDER BY clauses.

**0x3105D ( 200797) qpERR_ABORT_QMV_NO_SELECTED_EXPRESSION Only the expressions
in the target list can appear in the ORDER BY clause.**

**Cause:** One or more expressions in the ORDER BY clause are not in the target
list.

**Action:** Verify that the target list has every expression used in the ORDER
BY clause.

**0x3105E ( 200798) qpERR_ABORT_QMV_INVALID_POSITION_IN_ORDERBY Invalid position
value in ORDER BY clause.**

**Cause:** The position value is greater than the number of expressions in the
target list.

**Action:** Verify that the position value is less than or equal to the number
of expressions in the target list.

**0x3105F ( 200799) qpERR_ABORT_QMV_INVALID_ORDERBY_EXP_WITH_SET Invalid
expression in ORDER BY clause. \<0%s\>**

**Cause:** An invalid expression was found in the ORDER BY clause.

**Action:** Check the ORDER BY clause.

**0x31060 ( 200800) qpERR_ABORT_QMV_CANNOT_USE_AGG Invalid use of aggregate
function. An aggregate function such as COUNT, MIN, MAX, SUM or AVG was used in
a clause in which it is not allowed.**

**Cause:** An aggregate function takes another aggregate function as an
argument. An aggregate function such as COUNT, MIN, MAX, SUM, or AVG is used on a
clause where it is forbidden.

**Action:** Verify the positions of aggregate functions in the SQL statement.
Verify that no aggregate function is used in a SQL statement that has no GROUP
BY clause.

**0x31061 ( 200801) qpERR_ABORT_QCV_NOT_ALLOWED_AGGREGATION An aggregate
function is not allowed here. \<0%s\>**

**Cause:** An aggregate function cannot be used here.

**Action:** Check all aggregate functions.

**0x31062 ( 200802) qpERR_ABORT_QMV_MISMATCH_TARGET_COUNT Mismatched number of
expressions in the target lists of SELECT statements for a SET query**

**Cause:** The number of expressions in target lists of SELECT statements for a
SET differ from one another.

**Action:** Count the number of expressions in each target list of SELECT
statements in the SET query.

**0x31063 ( 200803) qpERR_ABORT_QMV_INVALID_TABLE_NAME Invalid table name
\<0%s\>**

**Cause:** A table name that is not listed in the FROM clause was used.

**Action:** Check the FROM clause.

**0x31064 ( 200804) qpERR_ABORT_QMV_GROUP_ON_FORUPDATE A GROUP BY or HAVING
clause is not allowed in a SELECT FOR UPDATE statement.**

**Cause:** Violation of SELECT FOR UPDATE restrictions.

**Action:** Do not use a GROUP BY or HAVING clause.

**0x31065 ( 200805) qpERR_ABORT_QMV_AGGREGATE_ON_FORUPDATE Aggregate functions
are not allowed in SELECT FOR UPDATE statements.**

**Cause:** Violation of SELECT FOR UPDATE restrictions.

**Action:** Do not use aggregate functions.

**0x31066 ( 200806) qpERR_ABORT_QMV_DISTINCT_SETFUNCTION_ON_FORUPDATE DISTINCT,
UNION, UNION ALL, INTERSECT and MINUS are not allowed in SELECT FOR UPDATE
statements.**

**Cause:** Violation of SELECT FOR UPDATE restrictions.

**Action:** Do not use DISTINCT or set functions.

**0x31235 ( 201269) qpERR_ABORT_QMV_JOIN_ON_FORUPDATE JOIN is not allowed in
SELECT FOR UPDATE statements.**

**Cause:** Violation of SELECT FOR UPDATE restrictions.

**Action:** Do not use the JOIN operation.

**0x31067 ( 200807) qpERR_ABORT_QMV_USE_SEQUENCE_WITH_ORDER_BY A sequence cannot
be used in a SELECT statement with an ORDER BY clause. \<0%s\>**

**Cause:** A sequence cannot be used in a SELECT statement having an ORDER BY
clause.

**Action:** Remove the sequence or the ORDER BY clause.

**0x31068 ( 200808) qpERR_ABORT_QMV_USE_SEQUENCE_WITH_GROUP_BY A sequence cannot
be used in a SELECT statement that has a GROUP BY or HAVING clause or aggregate
functions. \<0%s\>**

**Cause:** A sequence cannot be used in a SELECT statement having a GROUP BY or
HAVING clause or aggregate functions.

**Action:** Remove the aggregate functions, the GROUP BY or HAVING clause, or
the sequence.

**0x31069 ( 200809) qpERR_ABORT_QMV_USE_SEQUENCE_WITH_DISTINCT A sequence cannot
be used in a SELECT statement that has a DISTINCT clause. \<0%s\>**

**Cause:** A sequence cannot be used in a SELECT statement having a DISTINCT
clause.

**Action:** Remove the sequences or the DISTINCT option.

**0x3106A ( 200810) qpERR_ABORT_QMV_USE_SEQUENCE_WITH_SET A sequence cannot be
used in a SELECT statement that has a UNION, UNION ALL, INTERSECT, or MINUS
operation. \<0%s\>**

**Cause:** A sequence cannot be used in SELECT statements that contain UNION,
UNION ALL, INTERSECT, or MINUS operations.

**Action:** Remove the sequences or SET operation.

**0x3106B ( 200811) qpERR_ABORT_QMV_USE_SEQUENCE_IN_VIEW A sequence cannot be
used in a view. \<0%s\>**

**Cause:** A sequence cannot be used in a view.

**Action:** Remove the sequences.

**0x3106C ( 200812) qpERR_ABORT_QMV_USE_SEQUENCE_IN_SUBQUERY A sequence cannot
be used in a subquery. \<0%s\>**

**Cause:** A sequence cannot be used in a subquery.

**Action:** Remove the sequences.

**0x3106D ( 200813) qpERR_ABORT_QMV_USE_SEQUENCE_IN_WHERE A sequence cannot be
used in a WHERE clause. \<0%s\>**

**Cause:** A sequence cannot be used in a WHERE clause.

**Action:** Remove the sequences.

**0x3106E ( 200814) qpERR_ABORT_QMV_USE_SEQUENCE_IN_DEFAULT A sequence cannot be
used as a DEFAULT constraint in a CREATE or ALTER TABLE statement. \<0%s\>**

**Cause:** A sequence cannot be used as a DEFAULT constraint in a CREATE or
ALTER TABLE statement.

**Action:** Remove the sequences.

**0x3106F ( 200815) qpERR_ABORT_QMV_NESTED_AGGR_WITHOUT_GROUP Unable to use a
nested aggregate function without a GROUP BY clause.**

**Cause:** A nested aggregate function cannot be used without a GROUP by clause.

**Action:** Use a GROUP BY clause with the nested aggregate function.

**0x31070 ( 200816) qpERR_ABORT_QMV_TOO_DEEPLY_NESTED_AGGR Aggregate function
nested too deeply**

**Cause:** Aggregate function nested too deeply.

**Action:** Nest an aggregate function to only one layer.

**0x3140C ( 201740) qpERR_ABORT_QMV_NOT_SUPPORT_NESTED_AGGR Unsupported use of
nested aggregate function with GROUPING SETS clause.**

**Cause:** A nested aggregate function was used with the GROUPING SETS clause.

**Action:** Use the GROUPING SETS clause without the nested aggregate function.

**0x31071 ( 200817) qpERR_ABORT_QMV_TYPE_MISMATCH_IN_SET Type mismatch error in
SET.**

**Cause:** One or more of the target types are incompatible with one another.

**Action:** Verify that the type of every target in SET is correct.

**0x31072 ( 200818) qpERR_ABORT_QMV_DUP_COLUMN_IN_SET Duplicate columns
specified in a SET clause.**

**Cause:** One column is specified more than once in a SET clause.

**Action:** Verify that the target column name appears only once in a SET
clause.

**0x31193 ( 201107) qpERR_ABORT_QMV_NOT_APPLICABLE_TYPE_IN_TARGET Inapplicable
data type in target list \<0%s\>**

**Cause:** Inapplicable data type in target list.

**Action:** Remove targets that are of the BOOLEAN or LIST data types.

**0x311A0 ( 201120) qpERR_ABORT_QMV_HIERARCHICAL_WITH_JOIN A hierarchical query
cannot have a join operation \<0%s\>.**

**Cause:** A hierarchical query cannot have a join operation.

**Action:** Use the hierarchical query only on a base table.

**0x311A1 ( 201121) qpERR_ABORT_QMV_HIERARCHICAL_WITH_VIEW Hierarchical queries
are not allowed for created views or inline views \<0%s\>.**

**Cause:** A hierarchical query can be used only on a physical table.

**Action:** Use a hierarchical query only on a physical table. Remove all inline
views from hierarchical queries.

**0x311A2 ( 201122) qpERR_ABORT_QMV_SUBQ_IN_CONNECTBY A CONNECT BY clause cannot
include a subquery \<0%s\>.**

**Cause:** A CONNECT BY clause cannot include a subquery.

**Action:** Remove the subquery from the CONNECT BY clause.

**0x311A3 ( 201123) qpERR_ABORT_QMV_PRIOR_WITHOUT_CONNECTBY PRIOR cannot be
specified without a CONNECT BY clause \<0%s\>.**

**Cause:** PRIOR cannot be specified without a CONNECT BY clause.

**Action:** Specify a CONNECT BY clause.

**0x311D5 ( 201173) qpERR_ABORT_QMV_NOT_PREDICATE Not a predicate \<0%s\>.**

**Cause:** A predicate was not specified.

**Action:** Specify a predicate.

**0x31201 ( 201217) qpERR_ABORT_PSM_NOT_IN_SERVICE_PHASE A stored function or
procedure can be invoked only in the SERVICE phase \<0%s\>.**

**Cause:** A stored function or procedure can be invoked only in the SERVICE
phase.

**Action:** Do not use stored functions or procedures in phases other than the
SERVICE phase.

**0x31205 ( 201221) qpERR_ABORT_QMV_MOVE_SAME_TABLE It is forbidden to execute a
MOVE statement on the same table.**

**Cause:** The user tried to execute a MOVE statement on the same table.

**Action:** Do not execute a MOVE statement on the same table.

**0x31239 ( 201273) qpERR_ABORT_QMV_NOT_APPLICABLE_TYPE_IN_ORDER_BY Inapplicable
data type in ORDER BY clause \<0%s\>**

**Cause:** An inapplicable data type was specified in an ORDER BY clause.

**Action:** Do not use BOOLEAN or LIST type data for ORDER BY clauses.

**0x3123A ( 201274) qpERR_ABORT_QMV_NOT_APPLICABLE_TYPE_IN_GROUP_BY Inapplicable
data type in GROUP BY clause \<0%s\>**

**Cause:** An inapplicable data type was specified in a GROUP BY clause.

**Action:** Do not use BOOLEAN or LIST type data for GROUP BY clauses.

**0x3123B ( 201275) qpERR_ABORT_QMV_NOT_ALLOWED_HOSTVAR Invalid use of host
variables \<0%s\>**

**Cause:** A host variable was misused.

**Action:** Set the specified data type using a CAST operator.

**0x31246 ( 201286) qpERR_ABORT_QMV_NOT_ALLOWED_INCOMPARABLE_DATA_TYPE
Incomparable data types (GEOMETRY,LOB) cannot be used in ORDER BY, GROUP BY,
HAVING and CONNECT BY clauses.**

**Cause:** Incomparable data types (GEOMETRY,LOB) cannot be used in ORDER BY,
GROUP BY, HAVING and CONNECT BY clauses.

**Action:** Do not use incomparable data types (GEOMETRY,LOB) in GROUP BY and
CONNECT BY clauses.

**0x3123D ( 201277) qpERR_ABORT_QMV_USE_INCOMPARABLE_DATA_TYPE_WITH_SET An
incomparable data type (GEOMETRY,LOB) cannot be used in a SELECT statement that
contains a UNION, INTERSECT, or MINUS operation. \<0%s\>**

**Cause:** An incomparable data type (GEOMETRY,LOB) cannot be used in a SELECT
statement that contains a UNION, INTERSECT, or MINUS operation.

**Action:** Do not use incomparable data types (GEOMETRY,LOB) in SET operations.

**0x3123E ( 201278) qpERR_ABORT_QMV_USE_INCOMPARABLE_DATA_TYPE_WITH_DISTINCT An
incomparable data type (GEOMETRY,LOB) cannot be used in a SELECT statement that
has a DISTINCT clause.**

**Cause:** An incomparable data type (GEOMETRY,LOB) cannot be used in a SELECT
statement having a DISTINCT clause.

**Action:** Do not use incomparable data types (GEOMETRY,LOB) with the DISTINCT
option.

**0x3124E ( 201294) qpERR_ABORT_QMV_USE_SEQUENCE_IN_ON_JOIN_CONDITION A sequence
cannot be used in an ON JOIN CONDITION clause. \<0%s\>**

**Cause:** A sequence cannot be used in an ON JOIN CONDITION clause.

**Action:** Remove the sequences.

**0x3128A ( 201354) qpERR_ABORT_QMV_INVALID_PARTITION_KEY_INSERT Inserted
partition key is not mapped to any partition.**

**Cause:** An attempt was made to insert a record into a Range or Composite
Range object having a concatenated partition key that is beyond the concatenated
partition bound list of the last partition -OR- An attempt was made to insert a
record into a List object having a partition key that did not match the literal
values specified for any of the partitions.

**Action:** Do not insert the key. Alternatively, add a partition capable of
accepting the key, or add values matching the key to a partition specification.

**0x31296 ( 201366) qpERR_ABORT_QMV_USE_ROWNUM_IN_DML ROWNUM pseudo column not
supported in DML statements. \<0%s\>**

**Cause:** The ROWNUM pseudo column is not supported in DML statements.

**Action:** Remove the ROWNUM.

**0x31298 ( 201368) qpERR_ABORT_QMV_USE_ROWNUM_IN_START_WITH ROWNUM pseudo
column not supported in START WITH clauses. \<0%s\>**

**Cause:** The ROWNUM pseudo column is not supported in START WITH clauses.

**Action:** Remove the ROWNUM.

**0x31299 ( 201369) qpERR_ABORT_QMV_USE_ROWNUM_IN_CONNECT_BY ROWNUM pseudo
column not supported in CONNECT BY clauses. \<0%s\>**

**Cause:** The ROWNUM pseudo column is not supported in CONNECT BY clauses.

**Action:** Remove the ROWNUM.

**0x312AC ( 201388) qpERR_ABORT_QMV_NOT_ALLOWED_DATABASE_OBJECTS Table, View or
Sequence reference not allowed in this context. \<0%s\>**

**Cause:** A reference to a database table, view, or sequence was found in an
inappropriate context. Such references can appear only in SQL statements.

**Action:** Remove or relocate the illegal reference.

**0x312BA ( 201402) qpERR_ABORT_QMV_COLUMN_NOT_ALLOWED_HERE Column not allowed
here: \<0%s\>**

**Cause:** A column name was used in an expression in which it is not permitted,
such as in the VALUES clause of an INSERT or ENQUEUE statement.

**Action:** Check the syntax of the statement and use column names only where
appropriate.

**0x3133C ( 201532) qpERR_ABORT_REACHED_MAX_SET_OP_RECURSION_DEPTH Too many
consecutive set operations.**

**Cause:** The query could not be validated because there were too many
consecutive set operations (union, intersect, minus, … ).

**Action:** Try to group set operations using parentheses.

**0x31341 ( 201537) qpERR_ABORT_MISMATCHED_VALUE_TYPE The column type and the
value type are mismatched.**

**Cause:** The column type and the value type are mismatched.

**Action:** Check the column specification.

**0x31342 ( 201538) qpERR_ABORT_QMV_NOT_PIVOT_AGGREGATION Non-aggregate
functions used in pivot operation**

**Cause:** Something other than an aggregate function was specified in the PIVOT
clause.

**Action:** Ensure that only aggregate functions are specified in the PIVOT
clause.

**0x31343 ( 201539) qpERR_ABORT_QMV_AMBIGOUS_PIVOT_COLUMN Duplicate column
names**

**Cause:** The pivot operation resulted in multiple columns having the same
name.

**Action:** Specify aliases in the PIVOT clause to prevent the generation of
duplicate column names.

**0x31344 ( 201540) qpERR_ABORT_QMV_INVALID_PIVOT_FOR_IN_COUNT Mismatched number
of PIVOT FOR elements and PIVOT IN subelements**

**Cause:** The number of elements in the PIVOT FOR clause is not the same as the
number of subelements in each element in the PIVOT IN clause.

**Action:** Ensure that the number of PIVOT FOR elements is the same as the
number of PIVOT IN subelements.

**0x3142D ( 201773) qpERR_ABORT_QMV_INVALID_UNPIVOT_ARGUMENT Invalid number of
arguments for the UNPIVOT clause**

**Cause:** The number of arguments for the UNPIVOT clause is invalid.

**Action:** Verify that the correct number of arguments have been input for the
UNPIVOT clause.

**0x3142E ( 201774) qpERR_ABORT_QMV_INVALID_UNPIVOT_COLUMN Unable to find the
specified column name in the unpivoted table. \<0%s\>**

**Cause:** The specified column name was not found in the unpivoted table.

**Action:** Verify that the column name is correct.

**0x31345 ( 201541) qpERR_ABORT_QMV_CANNOT_USE_DEFAULT_IN_VIEW The view creation
attempt failed because a default column value was specified.**

**Cause:** An attempt was made to specify a default column value when creating
or replacing a view.

**Action:** Do not use the DEFAULT clause in view creation statements.

**0x31353 ( 201555) qpERR_ABORT_QMV_NOT_APPLICABLE_OPERATOR_IN_TARGET Invalid
operator in SELECT list. \<0%s\>**

**Cause:** The SELECT list contains an operator that cannot be used in the
SELECT list.

**Action:** Remove operators such as the outer join operator from the SELECT
list.

**0x31354 ( 201556) qpERR_ABORT_QMV_OUTER_JOINED_TO_SUBQUERY A column cannot be
outer-joined to a subquery. \<0%s\>**

**Cause:** A column was outer-joined to a subquery.

**Action:** Rewrite the query to avoid outer-joining a column to a subquery.

**0x31355 ( 201557) qpERR_ABORT_QMV_NOT_ALLOWED_IN_OPERAND_OR Outer join
operator not allowed in OR or IN condition. \<0%s\>**

**Cause:** The outer join operator was used in an operand of an OR or IN
condition.

**Action:** Avoid using the outer join operator in OR and IN conditions.

**0x31356 ( 201558) qpERR_ABORT_QMV_NOT_ALLOWED_WITH_ANSI_JOIN The outer join
operator cannot be used with ANSI joins. \<0%s\>**

**Cause:** The outer join operator was used with an ANSI join.

**Action:** Avoid using the outer join operator with ANSI joins.

**0x31357 ( 201559) qpERR_ABORT_QMV_TOO_MANY_REFERENCE_OUTER_JOINED_TABLE A
predicate may reference only one outer-joined table. \<0%s\>**

**Cause:** The outer join operator was used with more than one table in a
predicate.

**Action:** Use the outer join operator with only one table in a predicate.

**0x31358 ( 201560) qpERR_ABORT_QMV_NOT_ALLOW_JOIN_OPER_WITH_NON_COLUMN The
outer join operator can only be used with columns. \<0%s\>**

**Cause:** An attempt was made to use the outer join operator with something
other than a column.

**Action:** Verify that the outer join operator is used only with columns.

**0x31359 ( 201561) qpERR_ABORT_QMV_NOT_ALLOW_OUTER_JOIN_EACH_OTHER A table
cannot be outer-joined to itself. \<0%s\>**

**Cause:** The outer join operator was used in a WHERE clause in which a table
is compared with itself.

**Action:** Avoid using the outer join operator in a predicate in which a table
is compared with itself.

**0x3135A ( 201562) qpERR_ABORT_QMV_INVALID_OPERATION_WITH_LISTS The outer join
operator can't be used in a list. \<0%s\>**

**Cause:** The outer join operator was used in a list that was compared with a
list in an IN(ANY,ALL) condition.

**Action:** When comparing a list that includes an outer join with an
IN(ANY,ALL) condition, the IN(ANY,ALL) condition can contain only one member.

**0x3135B ( 201563) qpERR_ABORT_QMV_NOT_ALLOW_OUTER_JOIN_INAPPROPRIATE_TABLE
Invalid table used with outer join operator in subquery. \<0%s\>**

**Cause:** The outer join operator was used in a subquery predicate with a main
query select list table.

**Action:** Avoid using the outer join operator in a subquery predicate with a
main query select list table.

**0x3135C ( 201564)
qpERR_ABORT_QMV_MAYBE_OUTER_JOINED_TO_AT_MOST_ONE_OTHER_TABLE A table can be
outer joined to at most one other table. \<0%s\>**

**Cause:** A table is outer joined to more than one other table.

**Action:** Avoid outer joining a table to more than one other table.

**0x3135D ( 201565) qpERR_ABORT_QMV_OUTER_JOIN_OPERATOR_NOT_ALLOW_NOCNF The
outer join operator can only be used with CNF (Conjunctive Normal Form).**

**Cause:** The outer join operator was not used with CNF (Conjunctive Normal
Form).

**Action:** Change the NORMALFORM_MAXIMUM property to a larger value using the
ALTER SESSION command.

**0x3134B ( 201547) qpERR_ABORT_QMV_NOT_SUPPORT_SUBQUERY Unsupported use of
subquery in RETURNING INTO clause**

\#\*Cause: A subquery was used in a RETURNING INTO clause.

**Action:** Remove the subquery from the RETURNING INTO clause.

**0x3134C ( 201548) qpERR_ABORT_QMV_NOT_SUPPORT_LOB_COLUMN Unsupported use of
LOB column in RETURNING INTO clause**

**Cause:** One or more LOB columns were referenced in a RETURNING INTO clause.

**Action:** Remove the LOB column(s) from the RETURNING INTO clause.

**0x3134D ( 201549) qpERR_ABORT_QMV_NOT_RETURN_ALLOWED_HOSTVAR Invalid use of
host variable**

**Cause:** One or more host variables were referenced after the RETURNING
keyword.

**Action:** Use host variables only after the INTO keyword.

**0x3134E ( 201550) qpERR_ABORT_QMV_NOT_SAME_COLUMN_RETURN_INTO Mismatched
number of RETURNING expressions and host variables**

**Cause:** The number of expressions after the RETURNING keyword did not match
the number of host variables.

**Action:** Ensure that the number of expressions after the RETURNING keyword
matches the number of host variables.

**0x3134F ( 201551) qpERR_ABORT_QMV_SEQUENCE_NOT_ALLOWED Invalid use of
sequence**

**Cause:** One or more sequences were referenced in a RETURNING INTO clause.

**Action:** Remove the sequence(s) from the RETURNING INTO clause.

**0x31375 ( 201589) qpERR_ABORT_QMV_NO_GRANT_DML_PRIV_OF_MVIEW_TABLE Cannot
perform INSERT, DELETE, or UPDATE on materialized views**

**Cause:** An attempt was made to execute an INSERT, DELETE, or UPDATE statement
on a materialized view.

**Action:** Check the name and type of the table on which to execute the
statement.

**0x31378 ( 201592) qpERR_ABORT_QMV_CONNECT_BY_NOT_ALLOW_NOCNF The CONNECT BY
clause can only be used with CNF (Conjunctive Normal Form).**

**Cause:** The connect by clause was not used with CNF (Conjunctive Normal
Form).

**Action:** Change the NORMALFORM_MAXIMUM property to a larger value using the
ALTER SESSION command.

**0x31379 ( 201593) qpERR_ABORT_QMV_USE_ISLEAF_IN_START_WITH CONNECT_BY_ISLEAF
pseudocolumn not supported in START WITH clauses \<0%s\>**

**Cause:** An attempt was made to use the CONNECT_BY_ISLEAF pseudocolumn in a
START WITH clause.

**Action:** Remove the CONNECT_BY_ISLEAF pseudocolumn from the START WITH
clause.

**0x3137A ( 201594) qpERR_ABORT_QMV_USE_ISLEAF_IN_CONNECT_BY CONNECT_BY_ISLEAF
pseudocolumn not supported in CONNECT BY clauses \<0%s\>**

**Cause:** An attempt was made to use the CONNECT_BY_ISLEAF pseudocolumn within
a CONNECT BY clause.

**Action:** Remove the CONNECT_BY_ISLEAF pseudocolumn from the CONNECT BY
clause.

**0x3137B ( 201595) qpERR_ABORT_QMV_ISLEAF_NEED_CONNECT_BY CONNECT_BY_ISLEAF
pseudocolumn used without CONNECT BY clauses**

**Cause:** An attempt was made to use the CONNECT_BY_ISLEAF pseudocolumn without
a CONNECT BY clause.

**Action:** Use a CONNECT BY clause or remove the CONNECT_BY_ISLEAF
pseudocolumn.

**0x3137C ( 201596) qpERR_ABORT_QMV_CONNECT_BY_ROOT_NEED_CONNECT_BY
CONNECT_BY_ROOT used without CONNECT BY clause**

**Cause:** An attempt was made to use the CONNECT_BY_ROOT operator without a
CONNECT BY clause.

**Action:** Use a CONNECT BY clause or remove the CONNECT_BY_ROOT operator.

**0x3137D ( 201597) qpERR_ABORT_QMV_NOT_ALLOW_CONNECT_BY_ROOT CONNECT_BY_ROOT
not supported in START WITH or CONNECT BY clause**

**Cause:** The CONNECT_BY_ROOT operator was used in a START WITH or CONNECT BY
clause.

**Action:** Remove the CONNECT_BY_ROOT operator from the START WITH or CONNECT
BY clause.

**0x3137E ( 201598) qpERR_ABORT_QMV_NOT_ALLOW_SYS_CONNECT_BY_PATH
SYS_CONNECT_BY_PATH not supported in START WITH or CONNECT BY clause**

**Cause:** The SYS_CONNECT_BY_PATH function was used in a START WITH or CONNECT
BY clause.

**Action:** Remove the SYS_CONNECT_BY_PATH function from the START WITH or
CONNECT BY clause.

**0x3137F ( 201599) qpERR_ABORT_QMV_SYS_CONNECT_BY_PATH_NEED_CONNECT_BY
SYS_CONNECT_BY_PATH used without CONNECT BY clauses**

**Cause:** An attempt was made to use the SYS_CONNECT_BY_PATH function without a
CONNECT BY clause.

**Action:** Use a CONNECT BY clause or remove the SYS_CONNECT_BY_PATH function.

**0x31380 ( 201600) qpERR_ABORT_UNSUPPORTED_PSEUDO_COLUMN_IN_ORDER_SIBLINGS_BY
Unsupported use of pseudocolumn in ORDER SIBLINGS BY clause \<0%s\>**

**Cause:** An unsupported pseudocolumn was specified in an ORDER SIBLINGS BY
clause.

**Action:** Specify only table column names in the ORDER SIBLINGS BY clause.

**0x31381 ( 201601) qpERR_ABORT_QMV_NOT_ALLOW_ORDER_SIBLINGS_BY ORDER SIBLINGS
BY clause not allowed here**

**Cause:** An attempt was made to use the ORDER SIBLINGS BY clause in an
unsupported manner.

**Action:** Remove the ORDER SIBLINGS BY clause from the query.

**0x31382 ( 201602) qpERR_ABORT_QMV_NOT_ALLOW_PRIOR_LOB PRIOR not supported with
LOB type columns**

**Cause:** A LOB type column was specified after the PRIOR operator.

**Action:** Specify a non-LOB type column after the PRIOR operator.

**0x31384 ( 201604) qpERR_ABORT_QMV_CANNOT_SELECT_PROWID Cannot select \_PROWID
from a view or multiple tables. \<0%s\>**

**Cause:** Cannot select \_PROWID from a view or multiple tables.

**Action:** Use a single table in FROM clause.

**0x31385 ( 201605) qpERR_ABORT_QMV_PROWID_NOT_SUPPORTED \_PROWID is not
supported.**

**Cause:** PROWID is not supported.

**Action:** Do not use \_PROWID.

**0x31387 ( 201607) qpERR_ABORT_QMV_MERGE_REFERENCED_COLUMNS_CANNOT_BE_UPDATED
Cannot update columns in the ON Clause. \<0%s\>**

**Cause:** An attempt was made to update one or more columns referenced in the
ON Clause of a MERGE statement.

**Action:** Remove the columns referenced in the ON Clause from the update
column list.

**0x31393 ( 201619) qpERR_ABORT_QMV_NEED_GROUP_BY GROUPING function used without
GROUP BY ROLLUP or GROUP BY CUBE or GROUP BY GROUPING SETS clause.**

**Cause:** An attempt was made to use the GROUPING function without the GROUP BY
ROLLUP or GROUP BY CUBE or GROUP BY GROUPING SETS clause.

**Action:** Add the GROUP BY ROLLUP or GROUP BY CUBE or GROUP BY GROUPING SETS
or remove the GROUPING function clause from the statement.

**0x31394 ( 201620) qpERR_ABORT_QMV_NOT_SUPPORT_COMPLICATE_GROUP_EXT GROUP BY
ROLLUP or GROUP BY CUBE or GROUP BY GROUPING SETS clause used multiple times.**

**Cause:** An attempt was made to use the GROUP BY ROLLUP and/or GROUP BY CUBE
and/or GROUP BY GROUPING SETS clause more than once.

**Action:** Use the GROUP BY ROLLUP and/or GROUP BY CUBE and/or GROUP BY
GROUPING SETS clause only once.

**0x31395 ( 201621) qpERR_ABORT_QMV_NOT_SUPPORT_GROUPING_SETS GROUPING SETS
expression not supported**

**Cause:** An attempt was made to use the GROUPING SETS expression

**Action:** Remove the GROUPING SETS expression from the statement.

**0x31396 ( 201622) qpERR_ABORT_QMV_MAX_CUBE_COUNT Too many expressions used in
CUBE expression**

**Cause:** Too many expressions or columns were specified in the CUBE
expression.

**Action:** Use a maximum of 15 expressions in the CUBE expression.

**0x31397 ( 201623) qpERR_ABORT_QMV_NOT_APPLICABLE_TYPE_IN_RETURN Inapplicable
data type in the RETURNING expression \<0%s\>**

**Cause:** Inapplicable data type in the RETURNING expression.

**Action:** Remove the column from the RETURNING expression.

**0x313A1 ( 201633) qpERR_ABORT_QMV_WINDOW_INVALID_AGGREGATION Invalid window
aggregation group for window frame**

**Cause:** The window aggregation group specified in the window frame is
invalid.

**Action:** Use a valid window aggregation group in the window frame.

**0x313A2 ( 201634) qpERR_ABORT_QMV_NOT_WINDOW_CLAUSE_FUNC Not supported
aggregation function for window frame \<0%s\>**

**Cause:** The aggregation function specified does not support window frames.

**Action:** Choose the right function for window frames.

**0x313A4 ( 201636) qpERR_ABORT_QMV_NOT_KEY_PRESERVED_TABLE Cannot modify a
column for a non key-preserved table**

**Cause:** Only key-preserved tables allow INSERT, UPDATE and DELETTE
operations.

**Action:** Alter the base table a to key-preserved table.

**0x313A5 ( 201637) qpERR_ABORT_QMV_NOT_ONE_BASE_TABLE Cannot modify multiple
tables through a join view**

**Cause:** UPDATE, DELETE, INSERT operations on a join view is allowed only if
there is one base table.

**Action:** Check if the target of the UPDATE, DELETE or INSERT operation is a
table.

**0x313A6 ( 201638) qpERR_ABORT_QMV_TABLE_NOT_FOUND Table not found**

**Cause:** Cannot find the table for UPDATE, DELETE, or INSERT operations.

**Action:** Check the base table before UPDATE, DELETE or INSERT operations.

**0x313AE ( 201646) qpERR_ABORT_QMV_NOT_DML_READ_ONLY_VIEW Cannot perform a DML
operation on a read-only view.**

**Cause:** If the view was created with the read-only option, then any DML
operation cannot be performed on it.

**Action:** Alter the read option of the view with the ALTER VIEW statement.

**0x313D2 ( 201682)
qpERR_ABORT_QDX_NOT_ALLOWED_MEM_TBS_PRIMARY_AND_UNIQUE_KEY_OF_NONE_PREFIXED_INDEX
A primary key or a unique key constraint cannot be defined for a local
non-prefixed index on a memory partitioned table.**

**Cause:** A primary key or a unique key constraint cannot be defined for a
local non-prefixed index on a memory partitioned table.

**Action:** Do not define a primary key or a unique key constraint for a local
non-prefixed index on a memory partitioned table.

**0x3140A ( 201738) qpERR_ABORT_QMV_FIXED_TABLE_WITH_LATERAL_VIEW Cannot use a
fixed table in a lateral view.**

**Cause:** A fixed table is used in a lateral view.

**Action:** Do not use a fixed table in a lateral view.

**0x3140D ( 201741) qpERR_ABORT_QMV_INVALID_DEFAULT_VALUE The sequence in the
default value does not exist.**

**Cause:** The sequence which is used as the default value does not exist.

**Action:** Create the sequence again or alter the default value.

**0x3141D ( 201757) qpERR_ABORT_QMV_NOT_APPLICABLE_TABLE_FUNCTION An unsupported
data type was specified for the table function \<0%s\>**

**Cause:** An argument of the table function clause must be of the associative
array type, record type, or list type.

**Action:** Verify that the data type of the table function is of the
associative array type, record type, or list type.

**0x31441 ( 201793) qpERR_ABORT_QMV_ORDER_RECURSIVE_VIEW recursive WITH Clause
needs an initialization branch.**

**Cause:** Rewrite the recursive WITH query to have a branch in a UNION ALL
operation with no references to itself.

**Action:** A WITH Clause query referred to itself (recursive) but did not have
a branch in a UNION ALL with no references to itself.

**0x31442 ( 201794) qpERR_ABORT_QMV_DUPLICATE_RECURSIVE_VIEW recursive query
name referenced more than once in recursive branch of recursive WITH clause
element.**

**Cause:** The recursive component of the UNION ALL in a recursive WITH clause
element referenced the recursive query name more than once. Only one reference
to the recursive query name is allowed in the recursive branch of a recursive
WITH clause element.

**Action:** Rewrite the query using only one reference to the recursive query
name in the recursive branch of the recursive WITH clause element.

**0x31443 ( 201795) qpERR_ABORT_QMV_NON_EXIST_UNION_ALL_RECURSIVE_VIEW recursive
WITH clause must use a UNION ALL operation.**

**Cause:** A WITH clause query referred to itself (recursive) but did not use a
UNION ALL operation in its definition query.

**Action:** Rewrite the recursive WITH clause query to use a UNION ALL
operation.

**0x31444 ( 201796) qpERR_ABORT_QMV_MULTI_SET_RECURSIVE_VIEW UNION ALL operation
in recursive WITH clause must have only two branches.**

**Cause:** A WITH clause query referred to itself (recursive) but used a UNION
ALL operation with more than two branches, witch is not currently supported.

**Action:** Rewrite the recursive WITH clause query to use only two branches in
the UNION ALL operation.

**0x31445 ( 201797) qpERR_ABORT_QMV_OPERATION_NOT_ALLOWED_RECURSIVE_VIEW \<0%s\>
is not allowed in recursive WITH statements.**

**Cause:** Rewrite the query without the unsupported operation.

**Action:** The recursive component of the UNION ALL in a recursive WITH clause
element used an operation that was currently not allowed. The following should
not be used in the recursive branch of the UNION ALL operation: GROUP BY,
DISTINCT, grouping sets, CONNECT BY, HAVING, aggregate functions.

**0x31446 ( 201798) qpERR_ABORT_QMV_NO_COLUMN_ALIAS_RECURSIVE_VIEW recursive
WITH clause must have column alias list.**

**Cause:** A WITH Clause query referred to itself (recursive) but did not have a
column alias list specified for it.

**Action:** Add a column alias list for the WITH clause query name.

**0x31447 ( 201799) qpERR_ABORT_QMV_NOT_ALLOWED_JOIN_RECURSIVE_VIEW JOIN is not
allowed in recursive WITH statements.**

**Cause:** Violation of recursive WITH restrictions:

**Action:** Do not use the JOIN operation.

**0x31448 ( 201800) qpERR_ABORT_QMV_ITSELF_DIRECTLY_RECURSIVE_VIEW recursive
WITH clause must reference itself directly in one of the UNION ALL branches.**

**Cause:** A WITH clause query referred to itself (recursive) indirectly, such
as through a subquery or view.

**Action:** Rewrite the recursive WITH clause query to refer to itself directly
in the FROM clause of one of the UNION ALL branches.

**0x31449 ( 201801) qpERR_ABORT_QMV_DUPLICATION_QUERY_NAME_RECURSIVE_VIEW
Duplicate recursive WITH names.**

**Cause:** The recursive WITH name already exists in the query.

**Action:** Use another recursive WITH name.

**0x31451 ( 201809)
qpERR_ABORT_QMV_CANNOT_LOCK_TABLE_UNTIL_NEXT_DDL_IN_NON_EXCLUSIVE_MODE Unable to
execute a LOCK TABLE statement with UNTIL NEXT DDL option in non-exclusive
mode.**

**Cause:** A LOCK TABLE statement with UNTIL NEXT DDL option cannot be executed
in non-exclusive mode.

**Action:** Retry a LOCK TABLE statement in exclusive mode.

**0x31456 ( 201814) qpERR_ABORT_QMV_CANNOT_USE_ORDER_BY_CLAUSE An ORDER BY
clause is not allowed in the function. \<0%s\>**

**Cause:** An ORDER BY clause is not allowed in the function.

**Action:** Remove the ORDER BY clause from the statement.

**0x31073 ( 200819) qpERR_ABORT_QMX_SEQ_NOT_DEFINE_IN_SESSION The sequence is
not defined in this session. \<0%s\>**

**Cause:** The sequence is not defined in this session.

**Action:** Define the sequence first.

**0x31074 ( 200820) qpERR_ABORT_QMX_NOT_NULL_CONSTRAINT Unable to insert (or
update) NULL into NOT NULL column.**

**Cause:** The user tried to insert (or update) NULL into a column with a NOT
NULL constraint.

**Action:** Drop the NOT NULL constraint or Verify that the value to be inserted
or used for update is not a NULL value.

**0x31076 ( 200822) qpERR_ABORT_QMX_CHILD_EXIST Unable to modify records that
have child records. Check the referential constraints. \<0%s\>**

**Cause:** It is impossible to modify records that have child records. Check the
referential constraints.

**Action:** Check referential constraints that are related to the table.

**0x31077 ( 200823) qpERR_ABORT_QMX_NOT_FOUND_PARENT_ROW The parent record was
not found for \<0%s\>.**

**Cause:** The parent record was not found.

**Action:** Check the referential constraints that are related to the table.

**0x313D6 ( 201686) qpERR_ABORT_QMX_TABLE_PARTITION_ACCESS_DENIED Unable to
update table or partition \<0%s\>**

\# \*Cause : Update operation is not allowed on the table or partition.

\# \*Action : Check the access mode of the table or partition.

**0x31417 ( 201751) qpERR_ABORT_QDR_NOT_SYS_USER_DISABLE_TCP Only the SYS user
can enable or disable TCP.**

**Cause:** A normal user cannot enable or disable TCP.

**Action:** Re-login as SYS.

**0x31418 ( 201752) qpERR_ABORT_QDD_CANNOT_DROP_NOT_ENOUGH_RECYCLEBIN_SPACE
Unable to drop the table because the recycle bin has insufficient \<0%s\>
storage capacity.**

**Cause:**

\# - The recycle bin has either insufficient memory, or disk, or memory and disk
storage capacity.

**Action:**

\# - Empty the recycle bin or increase RECYCLEBIN_MEM_MAX_SIZE, or
RECYCLEBIN_DISK_MAX_SIZE, or both RECYCLEBIN_MEM_MAX_SIZE and
RECYCLEBIN_DISK_MAX_SIZE.

**0x31452 ( 201810) qpERR_ABORT_QMX_CANNOT_LOCK_TABLE_UNTIL_NEXT_DDL_WITH_DML
Unable to execute a LOCK TABLE statement with UNTIL NEXT DDL option in the
transaction that modified data.**

**Cause:** A LOCK TABLE statement with UNTIL NEXT DDL option cannot be executed
in the transaction that modified data.

**Action:** Execute the COMMIT or ROLLBACK statement, and retry a LOCK TABLE
statement.

**0x31453 ( 201811)
qpERR_ABORT_QMX_CANNOT_LOCK_TABLE_UNTIL_NEXT_DDL_MORE_THAN_ONCE Cannot execute a
LOCK TABLE statement with UNTIL NEXT DDL option twice or more.**

**Cause:** A LOCK TABLE statement with UNTIL NEXT DDL option cannot be executed
twice or more.

**Action:** Execute the COMMIT or ROLLBACK statement, and retry a LOCK TABLE
statement.

**0x311A4 ( 201124) qpERR_ABORT_QMN_HIER_LOOP Loop in hierarchical query
detected.**

**Cause:** A loop in a hierarchical query has been detected.

**Action:** Check the records.

**0x313FC ( 201724) qpERR_ABORT_QMN_INVALID_TEMPORARY_TABLE Cannot use the
temporary table as it has been changed.**

**Cause:** The query cannot be executed as the temporary table has become
invalid.

**Action:** Truncate the temporary table and then retry.

**0x3140E ( 201742) qpERR_ABORT_QMN_MODIFY_UNABLE_RECORD Failed to modify the
base table.**

**Cause:** The value in the base table to be updated or deleted is already
updated or deleted, or does not exist.

**Action:** Check the create join view query and result set.

**0x3144A ( 201802) qpERR_ABORT_QMN_RECURSION_LEVEL_MAXIMUM_RECURSIVE_VIEW
maximum level of recursion reached while executing recursive WITH query.**

**Cause:** A recursive WITH query reached the maximum level of recursion
specified and was stopped.

**Action:** Increase the maximum level of recursion.

**0x31232 ( 201266) qpERR_ABORT_QMO_INVALID_MEMORY_AREA Invalid memory area
access.**

**Cause:** Invalid memory area access

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x3124D ( 201293) qpERR_ABORT_QMO_EMPTY_DUMP_OBJECT Empty dump object.**

**Cause:** You did not specify a dump object for the dump table.

**Action:** Specify a dump object for the dump table.

**0x31409 ( 201737) qpERR_ABORT_QMO_NOT_ALLOWED_LVIEW_LEFT_FULL_JOIN_WITH_REF
Cannot perform a RIGHT or FULL outer join between a lateral view containing a
left correlation and a left object.**

**Cause:** A RIGHT or FULL outer join cannot be performed between a lateral view
containing a left correlation and a left object.

**Action:** Use another join type or change the lateral view to an inline view.

**0x3140F ( 201743)
qpERR_ABORT_QMO_NOT_ALLOWED_OUTER_COLUMN_IN_SUBQUERY_WITH_CONNECT_BY_FUNC A
CONNECT BY function cannot take a subquery containing an outer column as an
argument. \<0%s\>**

**Cause:** A subquery containing an outer column is taken as an argument.

**Action:** Remove the outer column from the subquery.

**0x31410 ( 201744) qpERR_ABORT_QMO_NOT_ALLOWED_OUTER_JOIN_OPER Unable to
execute the outer join operator.**

**Cause:** Unable to execute the outer join operator.

**Action:** Check the OUTER_JOIN_OPERATOR_TRANSFORM_ENABLE property value.

**0x3145F ( 201823) qpERR_ABORT_QMO_NOT_ALLOWED_LOB_FILTER Lob filter is not
supported.**

**Cause:** The lob filter was used within a hierarchy query in the SELECT FOR
UPDATE statement.

**Action:** Remove the lob filter from the query.

**0x313B0 ( 201648) qpERR_ABORT_QMR_NO_CALLBACK No callback for remote table is
registered.**

**Cause:** No callback for the remote table is registered.

**Action:** Verify that the database link is enabled.

**0x313B1 ( 201649) qpERR_ABORT_QMR_NO_DATABASE_LINK_NAME Database link name is
NULL.**

**Cause:** Database link name is NULL.

**Action:** Verify that the database link name is not null.

**0x31084 ( 200836) qpERR_ABORT_QRC_NO_GRANT The user has no permission to
execute the SQL statement.**

**Cause:** The user does not have sufficient permissions to execute the SQL
statement.

**Action:** Verify that the user has sufficient permission to execute the SQL
statement.

**0x31085 ( 200837) qpERR_ABORT_QRC_DUPLICATE_REPLICATION Duplicate replication
names. The replication name already exists in the database.**

**Cause:** The replication name already exists in the database. The IP address
and the port number must be unique.

**Action:** Use another replication name. Consult the meta tables in order to
find replications that use the same IP address and port number.

**0x31086 ( 200838) qpERR_ABORT_QRC_NOT_EXIST_REPLICATION Undefined replication
name. The replication name was not found in the database.**

**Cause:** The replication name was not found in the database. The name is
incorrect or the replication has not been created yet.

**Action:** Verify that the replication name is typed correctly. Consult meta
tables to see if the same replication name exists in the database.

**0x31087 ( 200839) qpERR_ABORT_QRC_MAX_REPLICATION_COUNT No more replications
may be created. A database cannot have more than the maximum number of
replications.**

**Cause:** A database cannot have more than the maximum number of replications.

**Action:** Check whether the system already has the maximum number of
replications.

**0x31088 ( 200840) qpERR_ABORT_QRC_NOT_EXISTS_PRIMARY_KEY A replicated table
must have a primary key. (\<0%s\>.\<1%s\>)**

**Cause:** No primary key was found in the table to be replicated. For
replication, specify a table having a primary key.

**Action:** Create a primary key for the table to be replicated.

**0x31089 ( 200841) qpERR_ABORT_QRC_REPLICATION_ALREADY_STARTED Replication has
already started.**

**Cause:** Replication is currently underway.

**Action:** Stop the current replication to start again.

**0x3108A ( 200842) qpERR_ABORT_QRC_CANNOT_USE_META Replication is not allowed
on meta tables.**

**Cause:** It is impossible to replicate a meta table.

**Action:** Verify that the table to be replicated is not a meta table.

**0x3108B ( 200843) qpERR_ABORT_QRC_REPLICATE_TABLE_WITH_REFERENCE Replication
is not allowed on tables that have referential constraints. (\<0%s\>.\<1%s\>)**

**Cause:** The user tried to replicate a table that has referential constraints.

**Action:** Verify that the table to be replicated does not have any referential
constraints.

**0x311BB ( 201147) qpERR_ABORT_QRC_REPLICATED_OBJECT_TYPE The replicated object
type must be a table. \<0%s\>**

**Cause:** Only a table may be replicated.

**Action:** Check the object type.

**0x31196 ( 201110) qpERR_ABORT_QRC_NOT_EXIST_REPL_ITEM No replication items
found.**

**Cause:** No replication items were found.

**Action:** Check the meta tables.

**0x3128D ( 201357) qpERR_ABORT_QRC_ROLE_NOT_SUPPORT_SYNC Replication SYNC is
not supported in this role.**

**Cause:** This role does not support SYNC.

**Action:** Check the role of the replication.

**0x3128E ( 201358) qpERR_ABORT_QRC_ROLE_NOT_SUPPORT_UNIX_DOMAIN UNIX domain
socket is not supported in this role.**

**Cause:** This role does not support UNIX_DOMAIN in the 'WITH' clause.

**Action:** Check the role of the replication.

**0x3128F ( 201359) qpERR_ABORT_QRC_ROLE_SUPPORT_ONE_SOCKET_TYPE One socket type
is supported in this role.**

**Cause:** This role supports one socket type.

**Action:** Check the role of the replication.

**0x31290 ( 201360) qpERR_ABORT_QRC_ROLE_SUPPORT_ONE_UNIX_DOMAIN Only one UNIX
domain socket is supported in this role.**

**Cause:** This role supports one UNIX domain socket.

**Action:** Check the role of the replication.

**0x31292 ( 201362) qpERR_ABORT_QRC_ROLE_NOT_SUPPORT_DEFAULT_REPL_MODE The
default replication mode is not supported in this role.**

**Cause:** This role does not support the default replication mode.

**Action:** Check the role of the replication.

**0x31293 ( 201363) qpERR_ABORT_QCI_NotPermittedUser Unauthorized user.**

**Cause:** The user does not have appropriate privileges.

**Action:** Check the user’s privileges.

**0x31294 ( 201364) qpERR_ABORT_QCM_DNBufferOverflow The OwnerDN length has
exceeded its range (overflow).**

**Cause:** OwnerDN length overflow.

**Action:** Check the error number from the trace log and contact Altibase's
Support Center (http://support.altibase.com/en/).

**0x312A3 ( 201379) qpERR_ABORT_QRC_INVALID_HOST_IP_PORT The host IP address or
port number is invalid.**

**Cause:** Invalid host IP address or port number.

**Action:** Check the host IP address and port number.

**0x312A5 ( 201381) qpERR_ABORT_QRC_ALREADY_EXIST_REPL_HOST Replication hosts
already exist.**

**Cause:** Replication hosts already exist.

**Action:** Check the meta tables.

**0x312A6 ( 201382) qpERR_ABORT_QRC_NOT_EXIST_REPL_HOST Replication hosts not
found.**

**Cause:** No replication hosts were found.

**Action:** Check the meta tables.

**0x312B3 ( 201395) qpERR_ABORT_QRC_REPL_RECOVERY_COUNT A table can recover only
one replication.**

**Cause:** Table recovery already supported by another replication.

**Action:** Check the replication recovery count.

**0x312B4 ( 201396) qpERR_ABORT_QRC_ROLE_NOT_SUPPORT_REPL_RECOVERY Recovery
option not supported in this role.**

**Cause:** This role does not support the recovery option.

**Action:** Check the options or the role of the replication.

**0x312B5 ( 201397) qpERR_ABORT_QRC_ALREADY_RECOVERY_SET Recovery option already
set.**

**Cause:** The replication recovery option has already been set.

**Action:** Check the replication options.

**0x312B6 ( 201398) qpERR_ABORT_QRC_ALREADY_RECOVERY_UNSET The recovery option
was already unset.**

**Cause:** The replication recovery option was already unset.

**Action:** Check the replication options.

**0x312B7 ( 201399) qpERR_ABORT_QRC_NOT_ALLOW_ADD_TABLE An ADD TABLE statement
is not allowed in recovery support replication.**

**Cause:** An ADD TABLE statement is not allowed in a recovery support
replication.

**Action:** Check the replication options.

**0x312B8 ( 201400) qpERR_ABORT_QRC_NOT_ALLOW_DROP_TABLE An DROP TABLE statement
is not allowed in recovery support replication.**

**Cause:** A DROP TABLE statement is not allowed in recovery support
replication.

**Action:** Check the replication options.

**0x312D2 ( 201426) qpERR_ABORT_QRC_REPL_MAKE_CONDITION The attempt to make
replication conditions failed.**

**Cause:** The WHERE clause is invalid.

**Action:** Check the WHERE clause.

**0x312E2 ( 201442) qpERR_ABORT_QRC_TOO_LONG_REPL_CONDITION_VALUE Replication
condition value too long**

**Cause:** A replication condition value is too long.

**Action:** Check the length of replication condition values.

**0x31313 ( 201491) qpERR_ABORT_QRC_NOT_APPLICABLE_POLICY This column policy is
not compatible with replication. [\<0%s\>]**

**Cause:** This column policy is not compatible with replication.

**Action:** Check the column policy.

**0x31317 ( 201495) qpERR_ABORT_QRC_CANNOT_USE_VOLATILE_TABLE Replication not
allowed on volatile tables.**

**Cause:** A volatile table cannot be replicated.

**Action:** Verify that the table to be replicated is not a volatile table.

**0x31324 ( 201508) qpERR_ABORT_QDB_REPLICATION_DDL_EAGER_MODE Cannot execute
DDL statements on a replicated table while replication is running in eager
mode.**

**Cause:** DDL statements cannot be executed on a replicated table running in
eager mode.

**Action:** Check the replication mode.

**0x31325 ( 201509) qpERR_ABORT_QRC_SELECTION_AND_EAGER The attempt to create a
replication failed because conditions and eager mode were both specified.**

**Cause:** A replication object with conditions cannot run in eager mode.

**Action:** Change the replication mode or remove the conditions.

**0x31326 ( 201510) qpERR_ABORT_QRC_NOT_SUPPORT_REPL_OFFLINE_AND_EAGER The
offline option is not supported with eager mode.**

**Cause:** Simultaneous use of eager mode and the offline option is not
supported.

**Action:** Change the option or mode of the replication.

**0x31327 ( 201511) qpERR_ABORT_QRC_NOT_SUPPORT_REPLICATION_DDL This replication
DDL is no longer supported.**

**Cause:** An attempt to use a deprecated DDL statement was made.

**Action:** This DDL statement cannot be run on a replicated table.

**0x31328 ( 201512) qpERR_ABORT_QRC_NOT_SUPPORT_MAX_ROWS_AND_EAGER Replication
in eager mode is not supported with the MAX ROWS table option.**

**Cause:** An attempt was made to use replication in eager mode on a table for
which the MAX ROWS option was specified.

**Action:** Check mode of the replication.

**0x3133D ( 201533) qpERR_ABORT_QRC_NOT_SUPPORT_RETRY_AND_EAGER The retry option
is not supported when replication is running in eager mode.**

**Cause:** The retry option is not supported in eager mode.

**Action:** Either remove the retry option or change the replication mode.

**0x31362 ( 201570) qpERR_ABORT_QRC_CANNOT_USE_TEMPORARY_TABLE Temporary tables
cannot be replicated.**

**Cause:** An attempt was made to add a temporary table to a replication object.

**Action:** Verify that none of the tables to be replicated are temporary
tables.

**0x31383 ( 201603) qpERR_ABORT_QRC_NOT_SUPPORT_AT_SN_CLAUSE Replication cannot
start from a specific SN unless it is used with the Log Analyzer.**

**Cause:** The AT SN clause was specified, but the role of the replication
object is not "Log Analyzer".

**Action:** Either specify the FOR ANALYSIS clause in the CREATE REPLICATION
statement, or do not use the AT SN clause in the ALTER REPLICATION statement.

**0x3111D ( 200989) qpERR_ABORT_QTC_TUPLE_SHORTAGE There are too many DML
statements in the stored procedure, or the SQL query is too long.**

**Cause:** The internal tuple set has been exhausted.

**Action:** The query or stored procedure is too long. Split the stored
procedure or query.

**0x3111E ( 200990) qpERR_ABORT_QTC_INVALID_AGGREGATION Invalid aggregation**

**Cause:** Invalid use of aggregation.

**Action:** Change the SQL statement.

**0x3111F ( 200991) qpERR_ABORT_QTC_INVALID_ARGUMENT_TYPE Invalid argument type.
\<0%s\>**

**Cause:** Invalid argument type

**Action:** Check the argument type.

**0x31120 ( 200992) qpERR_ABORT_QTC_NO_HOSTVAR_ALLOWED No host variable is
allowed here.**

**Cause:** No host variable is allowed here.

**Action:** Check the argument.

**0x31002 ( 200706) qpERR_ABORT_QTC_MULTIPLE_ROWS A single-row subquery has
returned more than one row.**

**Cause:** A single-row subquery has returned more than one row.

**Action:** Check the number of records returned by the subquery.

**0x31209 ( 201225) qpERR_ABORT_QTC_TOO_MANY_TABLES Too many tables are
referenced in a phrase.**

**Cause:** A phrase (FROM, WHERE, etc) references over 32 tables.

**Action:** Check and modify the query so that it does not reference more than
32 tables.

**0x31258 ( 201304) qpERR_ABORT_QTC_NOT_EXISTS_COLUMN Column not found**

**Cause:** The specified column was not found in the table.

**Action:** Verify that the column name is correct.

**0x312DC ( 201436) qpERR_ABORT_QTC_HOST_VAR_LIMIT_EXCEED The number of host
variables exceed the maximum limit (\<0%d\>).**

**Cause:** The number of host variables exceeds the maximum limit.

**Action:** Verify the number of host variables.

**0x312E3 ( 201443) qpERR_ABORT_QTC_INVALID_WINDOW_FUNCTION Window functions are
not allowed here. \<0%s\>**

**Cause:** Window functions are not allowed here.

**Action:** Specify a valid option value.

**0x312E4 ( 201444) qpERR_ABORT_QTC_UNSUPPORTED_FUNCTION Unsupported function in
window functions. \<0%s\>**

**Cause:** This function is not supported yet.

**Action:** Specify a valid option value.

**0x31367 ( 201575) qpERR_ABORT_QTC_MISSING_ORDER_IN_WINDOW_FUNCTION An ORDER BY
expression is required in the window function. \<0%s\>**

**Cause:** A ranking function requires an ORDER BY expression in the OVER
clause.

**Action:** Specify an ORDER BY expression.

**0x3130A ( 201482) qpERR_ABORT_QTC_INVALID_ENCRYPTED_COLUMN Invalid encrypted
column.**

**Cause:** The column is not valid for encryption.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x3130B ( 201483) qpERR_ABORT_QTC_INVALID_ENCRYPTION_DATATYPE Invalid
encryption datatype.**

**Cause:** Invalid encryption datatype.

**Action:** Check the encryption datatype.

**0x3130C ( 201484) qpERR_ABORT_QTC_TOO_LONG_POLICY_NAME Policy name is too
long. \<0%s\>**

**Cause:** A policy name is too long.

**Action:** Check the length of the policy name.

**0x313A3 ( 201635) qpERR_ABORT_QTC_MISSING_OVER_IN_WINDOW_FUNCTION OVER clause
required for this function. \<0%s\>**

**Cause:** The windowing function requires the OVER clause.

**Action:** Add the proper OVER clause for the windowing function.

**0x3141B ( 201755) qpERR_ABORT_QTC_NOT_APPLICABLE_TYPE_IN_LOOP An unsupported
data type was specified for the loop clause. \<0%s\>**

**Cause:** An unsupported data type was specified for the loop clause.

**Action:** Verify that the following data type is specified for the loop
clause: smallint, integer, bigint, list, associative array, or record/rowtype.

**0x3141C ( 201756) qpERR_ABORT_QTC_INVALID_LOOP_VALUE A value less than 0 was
specified.**

**Cause:** A value that is greater than or equal to 0 must be specified for the
loop clause.

**Action:** Specify a positive value.

**0x31421 ( 201761) qpERR_ABORT_QTC_PARAM_NAME_NOTATION_NOW_ALLOWED Name-based
argument notation is not allowed.**

**Cause:** Name-based argument notation for the expression is not allowed.

**Action:** Do not reference argument as name-based in the expression

**0x3142C ( 201772) qpERR_ABORT_QTC_OVER_CLAUSE_NOT_ALLOWED The OVER clause is
not allowed for this function. \<0%s\>**

**Cause:** The OVER clause is not allowed here.

**Action:** Do not use the OVER clause with this function.

**0x31450 ( 201808) qpERR_ABORT_QTC_SUBQUERY_RETURN_VALUE_CHANGED Return values
of performance view single-row subquery has changed during execution.**

**Cause:** Return values of performance view single-row subquery has changed
during execution.

**Action:** This error can occur rarely when there is a change in the values of
performance view single-row subquery during a query execution. You will get a
result without error if you execute again the same query that produced this
error. If you meet this error repeatedly, contact Altibase’s Support Center
(http://support.altibase.com/en/).

**0x31123 ( 200995) qpERR_ABORT_QCU_RESOURCE_BUSY Resource busy. ( \<0%s\> )**

**Cause:** The resource is busy.

**Action:** Try again later.

**0x3118C ( 201100) qpERR_ABORT_QCU_NO_SUCH_LATCH_OBJECT Procedure or function
not found.**

**Cause:** The procedure or function was not found in the database.

**Action:** Verify that the name of the procedure or function is correct.

**0x3122D ( 201261) qpERR_ABORT_QCU_PSM_FILE_OPEN_LIMIT_EXCEED The number of
opened file handles exceeds the maximum limit.**

**Cause:** The number of opened file handles exceeds the maximum limit.

**Action:** Call the FCLOSE_ALL function or change the PSM_FILE_OPEN_LIMIT
property value.

**0x31314 ( 201492) qpERR_ABORT_QCU_TOO_LONG_MODULE_NAME A security module name
is too long.**

**Cause:** A security module name is too long.

**Action:** Check the length of the security module name.

**0x31315 ( 201493) qpERR_ABORT_QCU_TOO_LONG_LIBRARY_NAME A security library
name is too long.**

**Cause:** A security library name is too long.

**Action:** Check the length of the security library name.

**0x313AF ( 201647) qpERR_ABORT_QCU_INVALID_FEATURE_ENABLE_VALUE Invalid value
for OPTIMIZER_FEATURE_ENABLE property.**

**Cause:** The specified value for OPTIMIZER_FEATURE_ENABLE property is invalid.

**Action:** Check for appropriate values for OPTIMIZER_FEATURE_ENABLE
property.Refer to the General Reference Manual for information about supported
options. Select an available option.

**0x313FD ( 201725) qpERR_ABORT_QCU_NO_SUCH_LATCH_PKG_OBJECT Package not
found.**

**Cause:** The package or package body was not found in the database.

**Action:** Verify that the name of the package or package body is correct.

**0x3141A ( 201754) qpERR_ABORT_QCU_CONNECT_TYPE_OPEN_LIMIT_EXCEED The number of
opened sokcet handles exceeds the maximum limit.**

**Cause:** The number of opened socket handles exceeds the maximum limit.

**Action:** Call the CLOSEALL_CONNECT function or change the
CONNECT_TYPE_OPEN_LIMIT property value.

**0x31426 ( 201766) qpERR_ABORT_QCU_MEM_POOL_ALLOC_FAILED Failed to allocate a
memory pool**

**Cause:**

\# - Failed to allocate a memory pool.

**Action:**

\# - Verify that there is enough available memory.

**0x31427 ( 201767) qpERR_ABORT_QCU_HASH_TABLE_ALLOC_FAILED Failed to allocate a
hash table**

**Cause:**

\# - Failed to allocate a hash table.

**Action:**

\# - Verify that there is enough available memory.

**0x31428 ( 201768) qpERR_ABORT_QCU_HASH_TABLE_FIND_FAILED Failed to find a
record from a hash table**

**Cause:**

\# - Failed to find a record from a hash table.

**Action:**

\# - Contact Altibase’s Support Center (http://support.altibase.com/en/).

**0x31429 ( 201769) qpERR_ABORT_QCU_HASH_TABLE_ADD_FAILED Failed to add a record
to a hash table**

**Cause:**

\# - Failed to add a record to a hash table.

**Action:**

\# - Contact Altibase’s Support Center (http://support.altibase.com/en/).

**0x3142A ( 201770) qpERR_ABORT_QCU_USER_LOCK_REQUEST_LIMIT_EXCEED The number of
requested user locks exceeds the maximum limit.**

**Cause:**

\# - The number of requested user locks exceeds the maximum limit.

**Action:**

\# - Call the USER_LOCK_RELEASE function or change the USER_LOCK_REQUEST_LIMIT
property value.

**0x31126 ( 200998) qpERR_ABORT_QCI_INVALID_BINDING Invalid binding to host
variables**

**Cause:** Invalid binding to host variables has been detected.

**Action:** Check the binding to host variables.

**0x31127 ( 200999) qpERR_ABORT_QCI_BUFFER_FULL Buffer full in QCI**

**Cause:**

\# - Buffer full in QCI

**Action:**

\# - Buffer full in QCI

**0x311B8 ( 201144) qpERR_ABORT_QCI_INVALID_HOST_DATA_SIZE Size of data to bind
to host variable is invalid [ Param ID = \<0%d\>, Data Type = \<1%u\>, Data Size
= \<2%d\>, Declared Size of Host Variable = \<3%d\> ]**

**Cause:** The size of the data and the size of the host variable differ from
one another.

**Action:** Check the size of the data to be bound to host variables.

**0x3123F ( 201279) qpERR_ABORT_TOO_LONG_IDENTIFIER_NAME The identifier name is
too long**

**Cause:** The identifier name is too long.

**Action:** Give the identifier a shorter name.

**0x31240 ( 201280) qpERR_ABORT_INVALID_STATEMENT_STATE_ERROR Invalid request to
process SQL statement**

**Cause:** A request was made to perform an operation on an SQL statement that
has already been freed.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x31248 ( 201288) qpERR_ABORT_BIND_COLUMN_COUNT_MISMATCH Mismatched bind
column count**

**Cause:** The number of host variables and the number of data items to bind to
them are different.

**Action:** Check client applications.

**0x31370 ( 201584) qpERR_ABORT_QCI_ACCOUNT_STATUS_LOCKED The account is
locked.**

**Cause:** The user has exceeded the allowed number of incorrect password
attempts, or the DBA has locked the account.

**Action:** Wait until the lock is lifted.

**0x31371 ( 201585) qpERR_ABORT_QCI_ACCOUNT_STATUS_EXPIRED The password has
expired.**

**Cause:** The user's account has expired and the password needs to be changed.

**Action:** Change the password.

**0x31372 ( 201586) qpERR_ABORT_QCI_INVALID_PASSWORD_ERROR Invalid password.**

**Cause:** The password is incorrect.

**Action:** Enter the correct password for the user.

**0x3142F ( 201775) qpERR_ABORT_QCI_CANNOT_EXEC_DDL DDL statements cannot be
executed in DA mode. Check the connection type.**

**Cause:** DDL statements cannot be executed in DA mode.

**Action:** Check the connection type.

**0x31129 ( 201001) qpERR_ABORT_QSV_NOT_EXIST_PROC_SQLTEXT Procedure or function
not found : \<0%s\>.**

**Cause:** The specified procedure or function name was not found in the
database.

**Action:** Verify that the procedure or function exists.

**0x3112A ( 201002) qpERR_ABORT_QSV_DUPLICATED_PROC_NAME_SQLTEXT Duplicate
procedure or function name \<0%s\>**

**Cause:** A procedure or function with that name already exists in the
database.

**Action:** Give the procedure or function a different name.

**0x3112D ( 201005) qpERR_ABORT_QSV_DUPLICATE_PARAMETER_SQLTEXT Duplicate
parameter names. \<0%s\>**

**Cause:** A parameter with the same name has already been defined.

**Action:** Use a different name for the parameter.

**0x3112E ( 201006) qpERR_ABORT_QSV_PROC_HAVE_RETURN A procedure cannot have a
RETURN type.**

**Cause:** The procedure has a RETURN type.

**Action:** Remove the RETURN type specification from the procedure declaration.

**0x3112F ( 201007) qpERR_ABORT_QSV_PROC_NOT_SUPPORTED_DATATYPE_SQLTEXT
Unsupported data type for parameter, RETURN, or local variable. \<0%s\>**

**Cause:** A procedure must not use an unsupported data type for a parameter,
RETURN, or local variable.

**Action:** Verify the data type for the parameter, RETURN, or local variable.

**0x31131 ( 201009) qpERR_ABORT_QSV_PROC_HAVE_RETURN_VALUE_SQLTEXT A procedure
cannot have a RETURN statement. \<0%s\>**

**Cause:** A procedure cannot have a RETURN statement.

**Action:** Remove the RETURN statement from the procedure declaration.

**0x31132 ( 201010) qpERR_ABORT_QSV_PROC_NOT_HAVE_RETURN_VALUE_SQLTEXT A
function must return a value. \<0%s\>**

**Cause:** A function must return a value.

**Action:** Specify a return value in the RETURN statement.

**0x31133 ( 201011) qpERR_ABORT_QSV_PROC_NOT_HAVE_RETURN_STMT A function must
have a RETURN statement.**

**Cause:** A function must have a RETURN statement.

**Action:** Specify a RETURN statement.

**0x31134 ( 201012) qpERR_ABORT_QSV_PROC_MULTIPLE_REC_TARGET_SQLTEXT Multiple
targets exist in an INTO clause. \<0%s\>**

**Cause:** Multiple targets exist in an INTO clause.

**Action:** Check the INTO clause.

**0x31135 ( 201013) qpERR_ABORT_QSV_PROC_SELF_TYPE_SQLTEXT Recursive type
declaration using %TYPE, %ROWTYPE \<0%s\>**

**Cause:** A recursive type declaration using %TYPE, %ROWTYPE has been detected.

**Action:** Check local variable declarations.

**0x31136 ( 201014) qpERR_ABORT_QSV_PROC_NOT_EXIST_STMT_SQLTEXT The label
statement must not be the last statement.\<0%s\>**

**Cause:** The label statement must not be the last statement.

**Action:** Specify another statement or a NULL statement after the label.

**0x31137 ( 201015) qpERR_ABORT_QSV_PROC_CANNOT_ASSIGN_SQLTEXT Mismatched number
of fields in ROWTYPE expressions \<0%s\>**

**Cause:** The number of fields in the L-value and R-value of a ROWTYPE
assignment must be the same.

**Action:** Check the number of fields in the ROWTYPE variables.

**0x31138 ( 201016) qpERR_ABORT_QSV_PROC_NOT_USE_IN_LOOP_SQLTEXT EXIT and
CONTINUE statements must be used only in loops. \<0%s\>**

**Cause:** An EXIT or CONTINUE statement was used outside of a loop.

**Action:** Check the EXIT or CONTINUE statement.

**0x31139 ( 201017) qpERR_ABORT_QSV_PROC_DUP_EXCEPTION_IN_HANDLER_SQLTEXT
Duplicate exception handlers \<0%s\>**

**Cause:** An exception handler with the same name already exists in the block.

**Action:** Remove the duplicate exception handler from the block.

**0x3113A ( 201018) qpERR_ABORT_QSV_PROC_NOT_EXIST_EXCEPTION_SQLTEXT Undefined
exception name. \<0%s\>**

**Cause:** Undefined exception name

**Action:** Create an exception handler with that name.

**0x3113B ( 201019) qpERR_ABORT_QSV_PROC_NOT_ALLOW_DEFAULT_SQLTEXT OUT or IN OUT
parameters cannot have default values. \<0%s\>**

**Cause:** OUT or IN OUT parameters cannot have default values.

**Action:** Remove the DEFAULT value specification from the OUT or IN OUT
parameters.

**0x3113C ( 201020) qpERR_ABORT_QSV_PROC_NOT_LOOP_LABEL_SQLTEXT A label name in
an EXIT statement must point to a loop statement. \<0%s\>**

**Cause:** A label name in an EXIT statement must be a label that indicates a
LOOP statement.

**Action:** Check the label name in the EXIT statement.

**0x3113D ( 201021) qpERR_ABORT_QSV_PROC_MAX_PARA_NUM_INT_ARG1 The number of
parameters in a stored procedure or function exceeds the maximum limit
(\<0%d\>).**

**Cause:** The number of parameters in a stored procedure or function exceeds
the maximum limit.

**Action:** Verify the maximum number of parameters.

**0x3113F ( 201023) qpERR_ABORT_QSV_PROC_ASSIGN_LVALUE_NO_READONLY_VAR_SQLTEXT
The L-value of the ASSIGN statement is either a CONSTANT variable or an IN
parameter. \<0%s\>**

**Cause:** The L-value of the ASSIGN statement is either a CONSTANT variable or
an IN parameter.

**Action:** Check the L-value of the ASSIGN statement.

**0x31140 ( 201024) qpERR_ABORT_QSV_NOT_ROWTYPE_EXPRESSION Not a ROWTYPE
expression \<0%s\>**

**Cause:** Not a ROWTYPE expression

**Action:** Check the expression.

**0x31142 ( 201026) qpERR_ABORT_QSV_PROC_SELECT_INTO_NO_READONLY_VAR_SQLTEXT The
INTO clause of the SELECT statement references a CONSTANT variable or an IN
parameter. \<0%s\>**

**Cause:** The INTO clause of the SELECT statement references a CONSTANT
variable or an IN parameter.

**Action:** Check the INTO clause of the SELECT statement.

**0x31143 ( 201027) qpERR_ABORT_QSV_CURSOR_NAME_IS_SQL_SQLTEXT A cursor name
must not be "SQL". \<0%s\>**

**Cause:** A cursor is named "SQL".

**Action:** Do not use "SQL" as a cursor name.

**0x31144 ( 201028) qpERR_ABORT_QSV_INSUFFICIENT_ARGUEMNT_SQLTEXT Insufficient
arguments \<0%s\>**

**Cause:** Insufficient arguments.

**Action:** Verify that the number of arguments matches the number specified in
the parameter declaration.

**0x31145 ( 201029) qpERR_ABORT_QSV_TOO_MANY_ARGUEMNT_SQLTEXT Too many arguments
\<0%s\>**

**Cause:** Too many arguments.

**Action:** Verify that the number of arguments matches the number specified in
the parameter declaration.

**0x31146 ( 201030) qpERR_ABORT_QSV_ROWTYPE_IN_EXPRESSION_SQLTEXT No ROWTYPE is
allowed in this expression. \<0%s\>**

**Cause:** No ROWTYPE is allowed in this expression.

**Action:** Check the type of the local variable.

**0x31147 ( 201031) qpERR_ABORT_QSV_INVALID_OUT_ARGUEMNT_SQLTEXT Invalid
argument in OUT parameter \<0%s\>**

**Cause:** Invalid argument in the OUT parameter.

**Action:** Verify that the argument is correct.

**0x31148 ( 201032) qpERR_ABORT_QSV_NOT_EXIST_VARIABLE_NAME_SQLTEXT Undefined
identifier \<0%s\>**

**Cause:** A variable, cursor, or exception name is undefined.

**Action:** Check the names of variables, cursors, and exceptions.

**0x31149 ( 201033) qpERR_ABORT_QSV_DUPLICATE_VARIABLE_SQLTEXT Duplicate type or
variable names : \<0%s\>**

**Cause:** A parameter, type, variable, cursor, or exception with the same name
has already been defined.

**Action:** Use a different name.

**0x3114A ( 201034) qpERR_ABORT_QSV_PROC_NOT_CONSTANT_SQLTEXT A constant
variable must have a DEFAULT value. \<0%s\>**

**Cause:** A constant variable must have a DEFAULT value.

**Action:** Specify a DEFAULT value for the constant local variable.

**0x3114B ( 201035) qpERR_ABORT_QSV_PROC_WRONG_CONSTANT_SQLTEXT A non-primitive
type variable cannot be defined as a CONSTANT variable. \<0%s\>**

**Cause:** A non-primitive variable cannot be defined as a CONSTANT variable.

**Action:** Check the variable declaration.

**0x3114C ( 201036) qpERR_ABORT_QSV_INAPPROPRIATE_INTO_SQLTEXT Inappropriate
INTO clause. The INTO clause must be specified immediately after the first
target list of a SELECT statement. \<0%s\>**

**Cause:** The INTO clause must be specified immediately after the first target
list of a SELECT statement.

**Action:** Verify that the INTO clause immediately follows the target list of
the SELECT statement.

**0x3114D ( 201037) qpERR_ABORT_QSV_NOT_HAVE_INTO_SQLTEXT A SELECT statement in
a procedure or function must have an INTO clause. \<0%s\>**

**Cause:** A SELECT statement in a procedure or function must have an INTO
clause.

**Action:** Verify that the SELECT statement has an INTO clause.

**0x3114E ( 201038) qpERR_ABORT_QSV_PROC_WRONG_ROWTYPE_DEFINITION The
declaration of the ROWTYPE attribute is invalid. \<0%s\>**

**Cause:** The declaration of the ROWTYPE attribute is invalid.

**Action:** Check the ROWTYPE attribute.

**0x3114F ( 201039) qpERR_ABORT_QSV_MISMATCHED_INTO_LIST_SQLTEXT The number of
columns in the target list does not match the number of variables in the INTO
clause. \<0%s\>**

**Cause:** The number of columns in the target list does not match the number of
variables in the INTO clause.

**Action:** Verify that the number of columns and the number of variables are
exactly the same.

**0x31150 ( 201040) qpERR_ABORT_QSV_USING_ATTR_IN_INAPPROPRIATE_CLAUSE A cursor,
cursor attribute, SQLCODE, or SQLERRM is used in an inappropriate
clause.\<0%s\>**

**Cause:** A Cursor, cursor attribute, SQLCODE, or SQLERRM is used in an
inappropriate clause.

**Action:** Remove the cursor or the cursor attribute from the expression.

**0x31185 ( 201093) qpERR_ABORT_QSV_NOT_ALLOWED_SUBQUERY_SQLTEXT A subquery is
not allowed here. \<0%s\>**

**Cause:** A subquery is not allowed here.

**Action:** Remove the subquery.

**0x31188 ( 201096) qpERR_ABORT_QSV_NOT_CURSOR The argument of the CURSOR
attribute is not a CURSOR. \<0%s\>**

**Cause:** The argument of the CURSOR attribute is not a CURSOR.

**Action:** Verify that the argument of the CURSOR attribute is a CURSOR.

**0x311B9 ( 201145) qpERR_ABORT_QSV_NOT_ALLOWED_COUNTER_VAR_SQLTEXT A counter
variable is not allowed here. \<0%s\>**

**Cause:** A counter variable is not allowed here.

**Action:** Use another variable.

**0x3120E ( 201230) qpERR_ABORT_QSV_DUPLICATE_LABEL Duplicate label name in same
block. \<0%s\>**

**Cause:** The same label name exists in this block.

**Action:** Check the label name.

**0x3120F ( 201231) qpERR_ABORT_QSV_ILLEGAL_GOTO Illegal GOTO statement.
\<0%s\>**

**Cause:** The label is not defined, or GOTO cannot pass control to the label.

**Action:** Check the label.

**0x31212 ( 201234) qpERR_ABORT_QSV_PROC_NOT_USE_IN_EXCEPTION_HANDLER A RAISE
statement with no exception name must be inside an exception handler. \<0%s\>**

**Cause:** The program contains a RAISE statement that is not followed by an
exception name: RAISE; and that statement is located outside of an exception
handler.

**Action:** Check the RAISE statement.

**0x31259 ( 201305) qpERR_ABORT_QSV_TRIGGER_UNSUPPORTED_RESULT_SET Trigger does
not support result set cursor. \<0%s\>**

**Cause:** Trigger does not support result set cursors.

**Action:** Do not use a result set cursor.

**0x31350 ( 201552) qpERR_ABORT_QSV_RECORD_WRONG Wrong number of columns in
record type. \<0%s\>**

**Cause:** The record type did not contain any columns.

**Action:** Check the record type definition.

**0x31351 ( 201553) qpERR_ABORT_QSV_ONLY_ASSOCIATIVE An associative array must
be used. \<0%s\>**

**Cause:** An associative array was expected.

**Action:** Check the host variables in the INTO clause.

**0x31352 ( 201554) qpERR_ABORT_QSV_BULK_ASSOCIATIVE BULK COLLECT required for
INTO clause to have multiple targets. \<0%s\>**

**Cause:** Multiple targets exist in an INTO clause.

**Action:** Use BULK COLLECT.

**0x313A7 ( 201639) qpERR_ABORT_QSV_NOT_EXIST_LIBRARY_SQLTEXT Library not found
: \<0%s\>.**

**Cause:** The specified library was not found in the database.

**Action:** Verify that the library exists.

**0x313A8 ( 201640) qpERR_ABORT_QSV_FORMAL_PARAMETER_MISSING Formal parameter
missing in the parameters : \<0%s\>.**

**Cause:** Formal parameter missing in the parameters.

**Action:** Provide a matching parameter in the parameters clause for every
formal parameter.

**0x313A9 ( 201641) qpERR_ABORT_QSV_MULTIPLE_DECLARATIONS Multiple declarations
in foreign function formal parameter list : \<0%s\>.**

**Cause:** Multiple declarations in foreign function formal parameter list.

**Action:** Remove the duplicate parameter from the foreign function formal
parameter list.

**0x313AA ( 201642) qpERR_ABORT_QSV_EXTERNAL_PARAMETER_NAME_NOT_FOUND External
parameter name not found in formal parameter list : \<0%s\>.**

**Cause:** Failed to find the external parameter name in the formal parameter
list.

**Action:** Provide a parameter in the parameters clause that matches one of the
formal parameters.

**0x313AB ( 201643) qpERR_ABORT_QSV_INCORRECT_USAGE_OF_XXX Incorrect Usage of
\<0%s\> in parameters clause : \<1%s\>.**

**Cause:** Incorrect usage of RETURN in parameters clause.

**Action:** Refer to the C/C++ External Procedure Manual for the formal
parameters available for specifying a property. Use a valid formal parameter.

**0x313AC ( 201644) qpERR_ABORT_QSV_RETURN_MUST_BE_IN_THE_LAST RETURN, for
actual function return, must be last in the parameters clause: \<0%s\>.**

**Cause:** RETURN, for actual function return, must be last in the parameters
clause.

**Action:** Place RETURN at the end of the parameters clause.

**0x313AD ( 201645) qpERR_ABORT_QSV_PSM_ROW_SIZE_EXCEED_LIMIT The row size in
the stored procedure or function exceeds the maximum limit. ( requested size :
\<0%ld\>, max size : \<1%ld\> )**

**Cause:** The row size is too big to process in the stored procedure or
function.

**Action:** Reduce the number of columns to process.

**0x313BB ( 201659) qpERR_ABORT_QSV_PROC_USED_BY_CONSTRAINT The procedure or
function is used by constraint.**

**Cause:** A constraint is using the procedure or function.

**Action:** Drop a constraint that is using the procedure or function.

**0x313BC ( 201660) qpERR_ABORT_QSV_PROC_USED_BY_INDEX The procedure or function
is used by index.**

**Cause:** An index is using the procedure or function.

**Action:** Drop the index that is using the procedure or function.

**0x313BD ( 201661) qpERR_ABORT_QSV_DUPLICATE_PKG Duplicate package
specification or package body names \<0%s\>**

**Cause:** The package specification or package body name already exists in the
database.

**Action:** Use another package specification or package body name.

**0x313BE ( 201662) qpERR_ABORT_QSV_NOT_EXIST_PACKAGE_SPECIFICATION Package
specification not found. \<0%s\>**

**Cause:** An attempt was made to create a package body before creating the
package specification.

**Action:** Create the package specification before creating the package body.

**0x313BF ( 201663) qpERR_ABORT_QSV_NOT_EXIST_PKG Package not found. \<0%s\>**

**Cause:** The specified package name was not found in the database.

**Action:** Verify that the package or package body exists.

**0x313C0 ( 201664) qpERR_ABORT_QSV_DUPLICATE_PKG_SUBPROGRAM Duplicate procedure
or function names found in the package. \<0%s\>**

**Cause:** Duplicate procedure or function names were declared in the package
specification.

**Action:** Verify that no duplicate procedure or function names are declared in
the package specification.

**0x313C1 ( 201665) qpERR_ABORT_QSV_INVALID_OR_MISSING_SUBPROGRAM A subprogram
[\<0%s\>] found in the package is missing in the package body.**

**Cause:** A subprogram found in the package specification is missing in the
package body.

**Action:** Define all of the subprograms from the package specification in the
package body.

**0x313C2 ( 201666) qpERR_ABORT_QSV_NOT_EXIST_PKG_BODY Package body not found.
\<0%s\>**

**Cause:** The package body has not been created yet.

**Action:** Create the package body.

**0x313C3 ( 201667) qpERR_ABORT_QSV_INVALID\_ IDENTIFIER Identifier must be
declared. \<0%s\>**

**Cause:** The specified identifier is invalid.

**Action:** Check the specified user name or object name.

**0x313C4 ( 201668) qpERR_ABORT_QSV_UNDEFINED_SUBPROGRAM Undefined subprogram.
\<0%s\>**

**Cause:** The specified subprogram was undefined in the package body.

**Action:** Define the subprogram in the package body.

**0x313C5 ( 201669) qpERR_ABORT_QSV_CANNOT_DECLARE_REF_CURSOR_VARIABLE Cursor
Variables cannot be declared in the package specification.**

**Cause:** A cursor variable was declared in the package specification.

**Action:** Check the variable type.

**0x313C6 ( 201670) qpERR_ABORT_QSV_INVALID_REFERENCE_VARIABLE Invalid reference
variable**

**Cause:** Invalid reference variable was declared.

**Action:** Check the variable type.

**0x313C7 ( 201671) qpERR_ABORT_QSV_SUBPROGRAM_INVALID Subprogram must be
valid.**

**Cause:** Undefined subprogram was called by another subprogram definition.

**Action:** Change the order of the function definition chronologically.

**0x313CD ( 201677) qpERR_ABORT_QSV_UNDECLARED_SUBPROGRAM Subprogram was
undeclared in the package specification. \<0%s\>**

**Cause:** A subprogram was undeclared in the package specification.

**Action:** Declare the subprogram in the package specification.

**0x313CE ( 201678) qpERR_ABORT_QSV_VIOLATES_ASSOCIATED_PRAGMA Subprogram
violates its associated pragma. \<0%s\>**

**Cause:** A subprogram has violated its associated pragma.

**Action:** Check the pragma.

**0x313CF ( 201679) qpERR_ABORT_QSV_INVALID_PRAGAM_RESTRICT_REFERENCE Pragma
RESTRICT_REFERENCES must be declared in a package specification**

**Cause:** Pragma RESTRICT_REFERENCES must be declared in a package
specification.

**Action:** Check the object type.

**0x313E9 ( 201705) qpERR_ABORT_QSV_INVALID_PACKAGE_SPECIFICATION Invalid
package specification. \<0%s\>**

**Cause:** A package specification is invalid.

**Action:** Recompile the package specification.

**0x313EB ( 201707)
qpERR_ABORT_QSV_CANNOT_DECLARE_TWICE_PRAGMA_AUTONOMOUS_TRANSACTION Pragma
AUTONOMOUS_TRANSACTION cannot be declared twice. \<0%s\>**

**Cause:** Pragma AUTONOMOUS_TRANSACTION was declared twice in the same block.

**Action:** Remove the duplicate declaration of the Pragma
AUTONOMOUS_TRANSACTION.

**0x313EC ( 201708)
qpERR_ABORT_QSV_CANNOT_SPECIFIED_PRAGMA_AUTONOMOUS_TRANSACTION Pragma
AUTONOMOUS_TRANSACTION cannot be specified here. \<0%s\>**

**Cause:** This pragma AUTONOMOUS_TRANSACTION must be declared in the
declarative section of a procedure, a function, a top level psm block.

**Action:** Check the the object type.

**0x313ED ( 201709) qpERR_ABORT_QSV_CANNOT_USE_IN_AUTONOMOUS_TRANSACTION Cannot
use a reference cursor type in autonomous transaction block. \<0%s\>**

**Cause:** Cannot use a reference cursor type in autonomous transaction block.

**Action:** Do not use a reference cursor type in autonomous transaction block.

**0x313FF ( 201727) qpERR_ABORT_QSV_PACKAGE_VARIABLE_NOT_HAVE_RETURN The
identifier is not a procedure or is not defined. \<0%s\>**

**Cause:** The identifier is not a procedure or is not defined.

**Action:** Check the identifier.

**0x31422 ( 201762) qpERR_ABORT_QSV_EXCEPTION_IS_NOT_DECLARED_IN_SAME_BLOCK
PRAGMA EXCEPTION_INIT of \<0%s\> must follow declaration of its exception in the
same declarative part. \<1%s\>**

**Cause:** Place the EXCEPTION_INIT pragma directly after the exception
declaration referenced by the pragma.

**Action:** An EXCEPTION_INIT pragma was not declared in the same block as its
exception. They must be declared in the proper order in the same block, with the
pragma declaration following the exception declaration.

**0x31423 ( 201763) qpERR_ABORT_QSV_REDUNDANT_EXCEPTIONS_IN_HANDLER Redundant
exceptions \<0%s\> and \<1%s\> cannot appear in same exception handler.
\<2%s\>**

**Cause:** Remove one of the exceptions or initialize it to a different Altibase
error number.

**Action:** The EXCEPTION_INIT pragma requires each exception in the exception
handler to be initialized to a different Altibase error number. Verify that the
exceptions do not have duplicate error numbers.

**0x31424 ( 201764) qpERR_ABORT_QSV_INVALID_EXCEPTION_ERROR_CODE Illegal
Altibase error number \<0%d\> for PRAGMA EXCEPTION_INIT. \<1%s\>**

**Cause:** The error number that was passed to an EXCEPTION_INIT pragma is out
of range.

**Action:** Use a valid error number. For further information about error
numbers, refer to the Error Message Reference.

**0x3141E ( 201758) qpERR_ABORT_QSV_NORMAL_PARAM_PASSING_AFTER_NAMED_NOTATION A
positional argument notation may not follow a name-based one. \<0%s\>**

**Cause:** In a stored procedure, a normal parameter notation may not follow a
named parameter notation.

**Action:** Reference arguments as positional notation first, then do the others
as name-based one.

**0x3141F ( 201759) qpERR_ABORT_QSV_WRONG_PARAM_NAME_NOTATION Name of an
argument notation does not exist in declared parameters. \<0%s\>**

**Cause:** Name of a parameter notation doesn't exist in declared parameters.

**Action:** Check the parameters of specified stored procedure.

**0x31420 ( 201760) qpERR_ABORT_QSV_DUPLICATE_PARAM_NAME_NOTATION Multiple
notation of the same parameter is used. \<0%s\>**

**Cause:** Multiple notation of the same parameter is used.

**Action:** Do not reference argument again.

**0x3142B ( 201771) qpERR_ABORT_QSV_TOO_MANY_MATCH_THIS_CALL Too many
declarations match this call. \<0%s\>**

**Cause:** Too many declarations match this call.

**Action:** Modify this call or its package declaration so that it is
unambiguous.

**0x3143E ( 201790) qpERR_ABORT_MAX_OPEN_CURSOR The number of opened cursor
exceeded the maximum limit.**

**Cause:** The number of opened cursor exceeded the maximum limit.

**Action:** Reduce the number of opened cursors.

**0x3143F ( 201791) qpERR_ABORT_INVALID_CURSOR_OPERATION Invalid cursor
operation.**

**Cause:** Invalid cursor operation.

**Action:** Check the cursor variable.

**0x31440 ( 201792) qpERR_ABORT_ILLEGAL_VARIABLE_NAME Illegal host variable
name.**

**Cause:** Illegal host variable name.

**Action:** Check the host variable name.

**0x31151 ( 201041) qpERR_ABORT_QSX_INTERNAL_SERVER_ERROR_ARG [QSX] Internal
server error (\<0%s\>)**

**Cause:** Program Error

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x31153 ( 201043) qpERR_ABORT_QSX_ROWTYPE_ON_PARAM_NOT_ALLOWED_ERROR_SQLTEXT
ROWTYPE is not allowed for a parameter declaration. \<0%s\>**

**Cause:** One or more parameters was declared using ROWTYPE.

**Action:** Do not use ROWTYPE for parameter declarations.

**0x31156 ( 201046) qpERR_ABORT_QSX_NOT_ENOUGH_MEMORY_ARG2 Not enough memory to
execute the stored procedure or function. \<0%s\> ( requested size : \<1%d\> )**

**Cause:** There was not enough memory.

**Action:** Install more memory in the system.

**0x31157 ( 201047) qpERR_ABORT_QSX_UNHANDLED_EXCEPTION Unhandled exception :
\<0%s\>**

**Cause:** The exception is not handled.

**Action:** Add an exception handler that corresponds to the raised exception.

**0x31158 ( 201048) qpERR_ABORT_QSX_FUNCTION_WITH_NO_RETURN Not all controls of
the \<0%s\> function return a value.**

**Cause:** Not all controls of the function return a value.

**Action:** Use a RETURN statement to return a value.

**0x31159 ( 201049) qpERR_ABORT_QSX_STEP_SIZE_LE_ZERO_SQLTEXT Step size must be
greater than 0 \<0%s\>**

**Cause:** The step size is less than 1.

**Action:** Verify that the step size is greater than 0.

**0x3115A ( 201050) qpERR_ABORT_QSX_TOO_HIGH_CALL_DEPTH_ARG1 The procedure or
function call depth has exceeded \<0%d\>.**

**Cause:** Procedure or function calls are nested too deeply.

**Action:** Verify that the conditions for the recursive call are valid.

**0x31162 ( 201058) qpERR_ABORT_QSX_PLAN_DROPPED A procedure or function was
dropped during execution.**

**Cause:** A procedure or function has been dropped.

**Action:** Rewrite the required procedure or function.

**0x31163 ( 201059) qpERR_ABORT_QSX_PLAN_CHANGED A procedure or function was
changed during execution.**

**Cause:** A procedure or function has been changed.

**Action:** Recompile the required procedure or function again.

**0x31164 ( 201060) qpERR_ABORT_QSX_PLAN_INVALID A procedure or function was
invalidated during execution.**

**Cause:** A procedure or function has been invalidated.

**Action:** Recompile the required procedure or function.

**0x31165 ( 201061) qpERR_ABORT_QSX_CONNECTION_CLOSED The client connection is
closed.**

**Cause:** The client connection is closed.

**Action:** Check the network status or check whether the customer application
has been terminated.

**0x31166 ( 201062) qpERR_ABORT_QSX_CURSOR_ALREADY_OPEN The CURSOR is already
open.**

**Cause:** The CURSOR_ALREADY_OPEN exception is not handled in the stored
procedure or function.

**Action:** Create an exception handler or prevent this exception from being
raised.

**0x31167 ( 201063) qpERR_ABORT_QSX_DUP_VAL_ON_INDEX Duplicate values in an
index**

**Cause:** The DUP_VAL_ON_INDEX exception is not handled in the stored procedure
or function.

**Action:** Create an exception handler or prevent this exception from being
raised.

**0x31168 ( 201064) qpERR_ABORT_QSX_INVALID_CURSOR Invalid CURSOR**

**Cause:** The INVALID_CURSOR exception is not handled in the stored procedure
or function.

**Action:** Create an exception handler or prevent this exception from being
raised.

**0x31169 ( 201065) qpERR_ABORT_QSX_INVALID_NUMBER Invalid number**

**Cause:** The INVALID_NUMBER exception is not handled in the stored procedure
or function.

**Action:** Create an exception handler or prevent this exception from being
raised.

**0x3116A ( 201066) qpERR_ABORT_QSX_NO_DATA_FOUND No data found.**

**Cause:** The NO_DATA_FOUND exception is not handled in the stored procedure or
function.

**Action:** Create an exception handler or prevent this exception from being
raised.

**0x3116B ( 201067) qpERR_ABORT_QSX_PROGRAM_ERROR Program error**

**Cause:** The PROGRAM_ERROR exception is not handled in the stored procedure or
function.

**Action:** Create an exception handler or prevent this exception from being
raised.

**0x3116C ( 201068) qpERR_ABORT_QSX_STORAGE_ERROR Storage error**

**Cause:** The STORAGE_ERROR exception is not handled in the stored procedure or
function.

**Action:** Create an exception handler or prevent this exception from being
raised.

**0x3116D ( 201069) qpERR_ABORT_QSX_TIMEOUT_ON_RESOURCE Timeout on resource**

**Cause:** The TIMEOUT_ON_RESOURCE exception is not handled in the stored
procedure or function.

**Action:** Create an exception handler or prevent this exception from being
raised.

**0x3116E ( 201070) qpERR_ABORT_QSX_TOO_MANY_ROWS Too many rows**

**Cause:** The TOO_MANY_ROWS exception is not handled in the stored procedure or
function.

**Action:** Create an exception handler or prevent this exception from being
raised.

**0x3116F ( 201071) qpERR_ABORT_QSX_VALUE_ERROR Value error**

**Cause:** The VALUE_ERROR exception is not handled in the stored procedure or
function.

**Action:** Create an exception handler or prevent this exception from being
raised.

**0x31170 ( 201072) qpERR_ABORT_QSX_ZERO_DIVIDE Divide by zero.**

**Cause:** The ZERO_DIVIDE exception is not handled in the stored procedure or
function.

**Action:** Create an exception handler or prevent this exception from being
raised.

**0x31171 ( 201073) qpERR_ABORT_QSX_NOT_ENOUGH_MEMORY_ARG_SQLTEXT There was not
enough memory to execute the stored procedure or function. (Requested Size :
\<0%d\>) \<1%s\>**

**Cause:** Not enough memory

**Action:** Install more memory in the system.

**0x31172 ( 201074) qpERR_ABORT_QSX_NOT_SUPPORTED_SQLTEXT Unsupported statement
\<0%s\>**

**Cause:** The statement is not supported.

**Action:** Do not use unsupported statements.

**0x31184 ( 201092) qpERR_ABORT_QSX_STACK_OVERFLOW Mathematic stack overflow.**

**Cause:** Stack overflow

**Action:** Use the ALTER SESSION SET STACK SIZE statement to increase the stack
size.

**0x31210 ( 201232) qpERR_ABORT_QSX_USER_DEFINED_EXCEPTION User-Defined
Exception.**

**Cause:** User-defined exception raised.

**Action:** No action is necessary.

**0x31213 ( 201235) qpERR_ABORT_QSX_INVALID_FILEOPEN_MODE Invalid file open
mode.**

**Cause:** The INVALID_MODE exception is not handled in the stored procedure or
function.

**Action:** Create an exception handler or prevent this exception from being
raised.

**0x31214 ( 201236) qpERR_ABORT_QSX_DIRECTORY_ACCESS_DENIED Directory access
denied.**

**Cause:** The ACCESS_DENIED exception is not handled in the stored procedure or
function.

**Action:** Create an exception handler or prevent this exception from being
raised.

**0x31215 ( 201237) qpERR_ABORT_QSX_FILE_INVALID_PATH Invalid directory path.**

**Cause:** The INVALID_PATH exception is not handled in the stored procedure or
function.

**Action:** Create an exception handler or prevent this exception from being
raised.

**0x31216 ( 201238) qpERR_ABORT_QSX_FILE_INVALID_FILEHANDLE Invalid file
handle.**

**Cause:** The INVALID_FILEHANDLE exception is not handled in the stored
procedure or function.

**Action:** Create an exception handler or prevent this exception from being
raised.

**0x31217 ( 201239) qpERR_ABORT_QSX_FILE_INVALID_OPERATION Invalid file
operation.**

**Cause:** The INVALID_OPERATION exception is not handled in the stored
procedure or function.

**Action:** Create an exception handler or prevent this exception from being
raised.

**0x31218 ( 201240) qpERR_ABORT_QSX_FILE_DELETE_FAILED File remove operation
failed.**

**Cause:** The DELETE_FAILED exception is not handled in the stored procedure or
function.

**Action:** Create an exception handler or prevent this exception from being
raised.

**0x31219 ( 201241) qpERR_ABORT_QSX_FILE_RENAME_FAILED File rename operation
failed.**

**Cause:** The RENAME_FAILED exception is not handled in the stored procedure or
function.

**Action:** Create an exception handler or prevent this exception from being
raised.

**0x3121A ( 201242) qpERR_ABORT_QSX_FILE_READ_ERROR File read error.**

**Cause:** The READ_ERROR exception is not handled in the stored procedure or
function.

**Action:** Create an exception handler or prevent this exception from being
raised.

**0x3121B ( 201243) qpERR_ABORT_QSX_FILE_WRITE_ERROR File write error.**

**Cause:** The WRITE_ERROR exception is not handled in the stored procedure or
function.

**Action:** Create an exception handler or prevent this exception from being
raised.

**0x31231 ( 201265) qpERR_ABORT_QSX_UNSUPPORTED_ARRAY_INDEX_TYPE Unsupported
array index type.**

**Cause:** In the INDEX BY clause of an array type declaration, a datatype other
than INTEGER or VARCHAR was specified.

**Action:** Use one of the supported key types (INTEGER or VARCHAR) in the INDEX
BY clause.

**0x312A4 ( 201380) qpERR_ABORT_QSX_NOT_QUERY The target of OPEN must be a
query.**

**Cause:** The program attempted to perform an OPEN cursor operation on a
dynamic statement that was not a query.

**Action:** Ensure that the OPEN cursor operation is performed on a dynamic
query statement.

**0x31386 ( 201606) qpERR_ABORT_QSX_PSM_INSIDE_QUERY Cannot perform a DML,
commit, or rollback inside a query.**

**Cause:** The program attempted to perform a DML, commit, or rollback inside a
query.

**Action:** Do not use a DML, COMMIT, or ROLLBACK statement inside a query.

**0x313C8 ( 201672) qpERR_ABORT_QSX_NOT_EXIST_SUBPROGRAM_AND_VARIABLE Subprogram
or variable not found in the package.**

**Cause:** The specified subprogram or variable does not exist in the package.

**Action:** Check the specified subprogram and variable name.

**0x313C9 ( 201673) qpERR_ABORT_QSX_ARRAY_INDEX_OVERFLOW The value of index
array is out of range.**

**Cause:** The value of the index array is out of range.

**Action:** Check the value of the index array.

**0x313CA ( 201674) qpERR_ABORT_QSX_FUNCTION_HAS_OUT_ARGUMENTS A function having
OUT or IN-OUT arguments cannot be invoked inside a query or DML.**

**Cause:** A function having OUT or IN-OUT arguments cannot be invoked inside a
query or DML.

**Action:** Check the function's argument types.

**0x313DA ( 201690) qpERR_ABORT_QSV_UNSUPPORTED_ARRAY_ELEMENT_TYPE Unsupported
array element type. \<0%s\>**

**Cause:** Array type is not supported as an array element.

**Action:** Use primitive type or ROWTYPE as an array element.

**0x313EA ( 201706) qpERR_ABORT_QSX_MISMATCHED_INTO_LIST_SQLTEXT The number of
columns in the target list does not match the number of variables in the INTO
clause. \<0%s\>**

**Cause:** The number of columns in the target list does not match the number of
variables in the INTO clause.

**Action:** Verify that the number of columns and the number of variables are
exactly the same.

**0x31439 ( 201785) qpERR_ABORT_QSX_UNINITIALIZED_ARRAY An array (element) is
not initialized.**

**Cause:** An array (element) is not initialized.

**Action:** Verify that a referenced array is initialized.

**0x31457 ( 201815) qpERR_ABORT_QSX_INTO_OR_BULK_COLLECT_INTO_CLAUSE_NOT_ALLOWED
Into clause is not allowed here.**

**Cause:** The INTO clause and BULK COLLECTION INTO clause can be used only when
executing the syntax of SELECT, SELECT FOR UPDATE, and DEQUEUE.

**Action:** Select and use a query among the syntax of SELECT, SELECT FOR UPDATE
or DEQUEUE; otherwise, do not use the INTO clause and BULK COLLECTION INTO
clause.

**0x3119F ( 201119) qpERR_ABORT_QCC_CANNOT_EXEC_DDL A DDL statement cannot be
executed. Check the EXEC_DDL_DISABLE property.**

**Cause:** A DDL statement cannot be executed.

**Action:** Check the EXEC_DDL_DISABLE property.

**0x31316 ( 201494) qpERR_ABORT_QDC_TOO_LONG_PROPERTY The length of a property
name or value is too long.**

**Cause:** The length of a property name or value is too long.

**Action:** Check the property name or value.

**0x31322 ( 201506) qpERR_ABORT_QDC_SECURITY_NOT_IN_SERVICE_PHASE A security
module can be invoked only in the SERVICE phase.**

**Cause:** A security module can be invoked only in the SERVICE phase.

**Action:** Do not use the security module in phases other than the SERVICE
phase.

**0x313B2 ( 201650) qpERR_ABORT_QDC_AUDIT_ALREADY_STARTED Audit has already
started.**

**Cause:** Audit has already started.

**Action:** Stop auditing and try to start again.

**0x313B3 ( 201651) qpERR_ABORT_QDC_AUDIT_NO_AUDIT_CONDITION_EXISTS No audit
condition exists.**

**Cause:** There is no audit condition.

**Action:** Check the audit conditions.

**0x313B4 ( 201652) qpERR_ABORT_QDC_AUDIT_NO_AUDIT_CONDITION_EXISTS_ON_THE_OBJ
NO audit condition exists on \<0%s\>**

**Cause:** There is no audit condition on the object.

**Action:** Check the audit conditions on the object.

**0x313B5 ( 201653) qpERR_ABORT_QDC_AUDIT_NOT_STARTED Audit is not running.**

**Cause:** Auditing has not been started.

**Action:** Start auditing first.

**0x31376 ( 201590) qpERR_ABORT_QDM_NOT_SUPPORTED_REFRESH_OPTION Refresh option
not supported**

**Cause:** The refresh option is not supported.

**Action:** Check the SQL statement.

**0x31377 ( 201591) qpERR_ABORT_QDM_RENAME_NOT_SUPPORT_MVIEW Cannot rename
materialized views.**

**Cause:** An attempt was made to rename a materialized view.

**Action:** Check the name and type of the table to be renamed.

**0x313D7 ( 201687) qpERR_ABORT_QDM_ACCESS_NOT_SUPPORT_MVIEW Cannot set or
change access mode of materialized views.**

**Cause:** An attempt was made to set or change the access mode of a
materialized view.

**Action:** Do not attempt to change the access mode of a materialized view.

**0x311B0 ( 201136) qpERR_ABORT_QDP_SELF_GRANT_OR_REVOKE A user cannot grant or
revoke privileges to the same user.**

**Cause:** A user cannot grant or revoke privileges to the same user.

**Action:** Connect as a user other than the grantee.

**0x311B1 ( 201137) qpERR_ABORT_QDP_INSUFFICIENT_PRIVILEGES The user must have
\<0%s\> privilege(s) to execute this statement.**

**Cause:** The user must have sufficient privileges to execute this statement.

**Action:** Check the user's privileges.

**0x311B2 ( 201138) qpERR_ABORT_QDP_REVOKE_PRIV_NOT_GRANTED Unable to revoke
privileges because they have not been granted (Privilege ID = \<0%d\>).**

**Cause:** It is impossible to revoke privileges that have not been granted.

**Action:** Check the granted privileges.

**0x311B3 ( 201139) qpERR_ABORT_QDP_DUPLICATE_GRANTEE Duplicate grantee names**

\<0%s\>

**Cause:** Duplicate grantee names

**Action:** Check the specified grantee name.

**0x311B4 ( 201140) qpERR_ABORT_QDP_DUPLICATE_PRIVILEGE Duplicate privilege
names : \<0%s\>**

**Cause:** Duplicate privilege names

**Action:** Check the specified privilege name.

**0x311B5 ( 201141) qpERR_ABORT_QDP_WITHOUT_CASCADE_OPTION A user refers to the
table.**

**Cause:** The CASCADE CONSTRAINTS option must be specified to perform this
REVOKE statement.

**Action:** Specify the CASCADE CONSTRAINTS option.

**0x311B6 ( 201142) qpERR_ABORT_QDP_NOT_ALLOWED_PRIV \<0%s\> privilege is not
allowed for this object.**

**Cause:** This privilege is not allowed for this object.

**Action:** Check the privileges.

**0x311B7 ( 201143) qpERR_ABORT_QDP_NOT_EXISTS_OBJECT Object not found. The name
of the specified object was not found in the database. \<0%s\>**

**Cause:** The name of the specified object was not found in the database.

**Action:** Verify that the object exists in the database.

**0x311BA ( 201146) qpERR_ABORT_QMO_TERM_TOOMANY Normalized term is too big.**

**Cause:** The normalized term is too large.

**Action:** Tune the query string.

**0x311BF ( 201151) qpERR_ABORT_QDP_NO_GRANT_DML_PRIV_OF_META_TABLE Unable to
insert, delete, or update meta tables.**

**Cause:** Meta tables cannot be inserted, deleted, or updated.

**Action:** Check the name and type of the table.

**0x31206 ( 201222) qpERR_ABORT_QDP_EXISTS_PRIVILEGE \<0%s\> already has
privileges (Privilege ID = \<1%d\>).**

**Cause:** You attempted to grant privileges to a grantee who already has those
privileges.

**Action:** Check the grantee's privileges.

**0x3122F ( 201263) qpERR_ABORT_QDP_NOT_EXIST_PRIVILEGE Privilege does not
exist. \<0%s\>**

**Cause:** This privilege does not exist in the database.

**Action:** Verify that the name of the privilege is correct. Refer to the SQL
User's Manual.

**0x312DF ( 201439) qpERR_ABORT_QDP_INVALID_DB_CHAR_SET An invalid database
character set was specified.**

**Cause:** UTF16 cannot be used as the database character set.

**Action:** Ensure that the specified national character set is valid.

**0x312E0 ( 201440) qpERR_ABORT_QDP_INVALID_NATIONAL_CHAR_SET An invalid
national character set was specified [Only UTF8 and UTF16]**

**Cause:** Only UTF8 and UTF16 can be used as the national character set.

**Action:** Ensure that the specified national character set is valid.

**0x31339 ( 201529) qpERR_ABORT_QDP_GRANT_NOT_SUPPORT_OBJ This object is not
allowed in a GRANT statement. \<0%s\>**

**Cause:** The GRANT statement can only be executed on user tables.

**Action:** Check the object type.

**0x313D8 ( 201688) qpERR_ABORT_QDP_GRANT_INSUFFICIENT_PRIVILEGES The user has
insufficient privileges.**

**Cause:** The user cannot grant the object privilege.

**Action:** Check the privileges of the user.

**0x31400 ( 201728) qpERR_ABORT_QDP_NOT_EXISTS_ROLE Role does not exist.
\<0%s\>**

**Cause:** The specified role does not exist.

**Action:** Check whether the role exists.

**0x31401 ( 201729) qpERR_ABORT_QDP_NOT_SUPPORTED_ROLE_TO_PUBLIC Cannot grant a
role to PUBLIC.**

**Cause:** The statement for granting a role to PUBLIC is currently unsupported.

**Action:** Do not grant a role to PUBLIC.

**0x31402 ( 201730) qpERR_ABORT_QDP_NOT_SUPPORTED_ROLE_TO_ROLE Cannot grant a
role to another role.**

**Cause:** The statement for granting a role to another role is not currently
supported.

**Action:** Do not grant a role to another role.

**0x31403 ( 201731) qpERR_ABORT_QDP_NOT_SUPPORTED_ROLE_WITH_GRANT_OPTION Cannot
GRANT to a role WITH GRANT OPTION.**

**Cause:** The WITH GRANT OPTION cannot be granted to a role.

**Action:** GRANT without WITH GRANT OPTION.

**0x31406 ( 201734) qpERR_ABORT_QDP_REVOKE_PRIV_NOT_GRANTED_ROLE Unable to
revoke an ungranted role. \<0%s\>**

**Cause:** The specified role cannot be revoked as it has not been granted.

**Action:** Check the granted roles.

**0x31407 ( 201735) qpERR_ABORT_QDP_EXISTS_ROLE \<0%s\> already has role.
\<1%s\>**

**Cause:** A role cannot be granted to a grantee that already has that role.

**Action:** Check the grantee's role.

**0x311BC ( 201148) qpERR_ABORT_QDV_ALIAS_NAME_IS_LEVEL "LEVEL" cannot be used
as an alias name. \<0%s\>**

**Cause:** "LEVEL" cannot be used as an alias name.

**Action:** Specify another alias name.

**0x311BD ( 201149) qpERR_ABORT_QCV_DML_ON_READ_ONLY_VIEW A DML statement cannot
be executed on a read-only view. \<0%s\>**

**Cause:** A DML statement cannot be executed on a read-only view.

**Action:** Verify that the view is not read-only.

**0x311BE ( 201150) qpERR_ABORT_QDV_INVALID_VIEW The view is invalid. \<0%s\>**

**Cause:** The view is invalid.

**Action:** Recompile the view.

**0x311C1 ( 201153) qpERR_ABORT_QDV_NOT_EXISTS_VIEW View not found**

**Cause:** The name of the specified view was not found in the database.

**Action:** Verify that the view name is correct.

**0x311C2 ( 201154) qpERR_ABORT_QDV_CIRCULAR_VIEW Circular view definition
detected \<0%s\>**

**Cause:** A circular view definition has been detected.

**Action:** Remove the circular view definition.

**0x3122C ( 201260) qpERR_ABORT_QDV_DDL_ON_VIEW A view is not appropriate here.
\<0%s\>**

**Cause:** A view is not appropriate here.

**Action:** Verify that the specified table is not a view.

**0x31297 ( 201367) qpERR_ABORT_QDV_ALIAS_NAME_IS_ROWNUM "ROWNUM" cannot be used
as an alias name. \<0%s\>**

**Cause:** “ROWNUM" cannot be used as an alias name.

**Action:** Specify another alias name.

**0x313CB ( 201675) qpERR_ABORT_QDB_NOT_ALLOWED_FOREIGN_KEY_CONSTRAINT A CREATE
TABLE AS SELECT statement with foreign key constraints is not allowed.**

**Cause:** A CREATE TABLE AS SELECT statement with foreign key constraints is
not allowed.

**Action:** Remove the foreign key constraint.

**0x31414 ( 201748) qpERR_ABORT_QDT_DB_MAXSIZE_EXCEED The total size of all disk
tablespaces exceeds the maximum limit. (max size : \<0%u\>MB, available size :
\<1%u\>MB)**

**Cause:** The total size of all disk tablespaces exceeds the maximum limit.

**Action:** Reduce the size of the tablespace that is being altered with the
CREATE TABLESPACE or ALTER TABLESPACE statement.

**0x311D7 ( 201175) qpERR_ABORT_QDT_DUPLICATE_TBS_NAME Duplicate tablespace
names**

**Cause:** Duplicate tablespace names.

**Action:** Check the specified tablespace name.

**0x311D8 ( 201176) qpERR_ABORT_QDT_NOT_EXIST_TBS Tablespace not found. The name
of the specified tablespace was not found in the database.**

**Cause:** The name of the specified tablespace was not found in the database.

**Action:** Verify that the tablespace exists in the database. Verify that there
is no typo in the tablespace name.

**0x311D9 ( 201177) qpERR_ABORT_QDT_NOT_EXIST_FILE File not found. The name of
the specified file was not found in the database.**

**Cause:** The name of the specified file was not found in the database.

**Action:** Verify that the file exists in the database. Verify that there is no
typo in the file name.

**0x311DA ( 201178) qpERR_ABORT_QDT_MISMATCH_TBS_TYPE Mismatched tablespace
type. The type of the tablespace and the type of the file are different.**

**Cause:** The type of the tablespace and the type of the file are different.

**Action:** Provide a suitable type for the tablespace and file.

**0x311DB ( 201179) qpERR_ABORT_QDT_NO_DROP_SYSTEM_TBS Unable to drop the SYSTEM
tablespace.**

**Cause:** The SYSTEM tablespace cannot be dropped.

**Action:** Check the tablespace name.

**0x311DC ( 201180) qpERR_ABORT_QDT_REFERENTIAL_CONSTRAINT_EXIST A dependent
foreign key constraint was found in another tablespace.**

**Cause:** An object in another tablespace depends on an object in the specified
tablespace via foreign key constraints.

**Action:** Drop the dependent object first, and then try to execute this
statement again.

**0x311DD ( 201181) qpERR_ABORT_QDT_OBJECT_EXIST The tablespace has objects.**

**Cause:** The tablespace has objects.

**Action:** Check whether there are unnecessary objects in the tablespace. If
so, delete them explicitly or use the DROP TABLESPACE … INCLUDING CONTENTS
statement.

**0x311DE ( 201182) qpERR_ABORT_QDT_NO_CREATE_IN_SYSTEM_TBS It is forbidden to
create objects in a DICTIONARY, UNDO or TEMP tablespace.**

**Cause:** The user tried to create objects in a DICTIONARY, UNDO or TEMP
tablespace.

**Action:** Do not create objects in a DICTIONARY, UNDO or TEMP tablespace.
Create objects in other tablespaces.

**0x311DF ( 201183) qpERR_ABORT_QDT_NO_ACCESS_TBS You cannot access the
tablespace.**

**Cause:** You cannot access the tablespace.

**Action:** Get access privileges on the specified tablespace.

**0x311E0 ( 201184) qpERR_ABORT_QDX_MAXIMUM_KEY_SIZE_EXCEED The estimated size
of the index key exceeds the maximum limit.**

**Cause:** The estimated size of the index key exceeds the maximum limit.

**Action:** Reduce the number of key columns.

**0x311E1 ( 201185) qpERR_ABORT_QDB_INVALID_INSERT_HIGH_LIMIT Invalid INSERT
HIGH LIMIT value**

**Cause:** An INSERT HIGH LIMIT value must be between 0 and 100.

**Action:** Check the INSERT HIGH LIMIT value.

**0x311E2 ( 201186) qpERR_ABORT_QDB_INVALID_INSERT_LOW_LIMIT Invalid INSERT LOW
LIMIT value**

**Cause:** An INSERT LOW LIMIT value must be between 0 and 100.

**Action:** Check the INSERT LOW LIMIT value.

**0x311E3 ( 201187) qpERR_ABORT_QDT_ERR_INVALID_DATA_TBS Invalid data
tablespace**

**Cause:** The tablespace is not a data tablespace.

**Action:** Check the tablespace name.

**0x311E4 ( 201188) qpERR_ABORT_QDT_ERR_INVALID_TEMP_TBS Invalid temporary
tablespace**

**Cause:** The tablespace is not a temporary tablespace.

**Action:** Check the tablespace name.

**0x311E5 ( 201189) qpERR_ABORT_QDB_NO_MEMORY_OR_VOLATILE_TABLE The table is not
a memory or volatile table.**

**Cause:** The table is not a memory or volatile table.

**Action:** Check the table name.

**0x312EB ( 201451) qpERR_ABORT_QDB_NO_DISK_TABLE The table is not a disk
table.**

**Cause:** The table is not a disk table.

**Action:** Check the table name.

**0x312EC ( 201452) qpERR_ABORT_QDB_NO_DISK_INDEX The index is not a disk
index.**

**Cause:** The index is not a disk index.

**Action:** Check the index name.

**0x311E6 ( 201190) qpERR_ABORT_QDX_UNSUPPORTED_INDEXTYPE Unsupported index
type.**

**Cause:** R-tree is not supported for disk tablespaces.

**Action:** Check the type of the index.

**0x311E7 ( 201191) qpERR_ABORT_QDT_CANNOT_ONOFFLINE Unable to bring the
specified tablespace online or offline.**

**Cause:** The specified tablespace is not a user or temp tablespace.

**Action:** Check the specified tablespace.

**0x311E8 ( 201192) qpERR_ABORT_QDT_INVALID_NEXT_SIZE Invalid NEXT SIZE value.**

**Cause:** The NEXT SIZE value should be more than EXTEND SIZE value when
AUTOEXTEND is on.

**Action:** Check the specified NEXT SIZE value.

**0x311E9 ( 201193) qpERR_ABORT_QCV_NOT_ALLOWED_GROUPING_SET Grouping set is not
allowed.**

**Cause:** A grouping set is not allowed.

**Action:** Verify that no grouping set is used.

**0x311EA ( 201194) qpERR_ABORT_QDT_EXIST_FILE The specified file is already in
use by another tablespace.**

**Cause:** The specified file is already in use by another tablespace.

**Action:** Try again later.

**0x311EC ( 201196) qpERR_ABORT_QDX_INVALID_INDEX_MEDIA The type
(memory/disk/volatile) of tablespace in which to create the index is not the
same as the type of the table.**

**Cause:** The user tried to create an index in an invalid tablespace.

**Action:** To create an index, use a memory tablespace for a memory table, a
disk tablespace for a disk table, or a volatile tablespace for a volatile table.

**0x311ED ( 201197) qpERR_ABORT_QDN_NOT_ALLOWED_PRIMARY_AND_UNIQUE_KEY Unable to
create a primary key or a unique key constraint for the data type
(GEOMETRY,LOB). \<0%s\>**

**Cause:** The user tried to create a primary key or a unique key constraint for
the specified (GEOMETRY,LOB) data type.

**Action:** Do not create a primary key or a unique key constraint for the
specified (GEOMETRY,LOB) data type.

**0x31200 ( 201216) qpERR_ABORT_QDT_INVALID_EXTENTSIZE The extent size
EXTENTSIZE must be greater than PAGESIZE \* 2.**

**Cause:** The user tried to create a tablespace with an invalid (too small)
extent size.

**Action:** Create a tablespace with a valid (greater than PAGESIZE \* 2) extent
size.

**0x31245 ( 201285) qpERR_ABORT_QDT_NO_CREATE_LOB_TYPE_IN_TBS Unable to create a
LOB type column with the specified tablespace.**

**Cause:** Unable to create a LOB type column with the specified tablespace.

**Action:** Check the specified tablespace.

**0x3124F ( 201295) qpERR_ABORT_QDT_DUPLICATE_CHECKPOINT_PATH Duplicate
checkpoint path**

**Cause:** Duplicate checkpoint path

**Action:** Check the specified checkpoint path.

**0x31250 ( 201296) qpERR_ABORT_QDT_NO_MEM_TBS_SPLIT_FILE_SIZE No SPLIT EACH
clause.**

**Cause:** There is no SPLIT EACH clause.

**Action:** Specify a SPLIT EACH clause.

**0x31251 ( 201297) qpERR_ABORT_QDT_INVALID_ALTER_ON_DISK_TBS Invalid ALTER DISK
TABLESPACE Statement. The tablespace to alter is not a disk tablespace.**

**Cause:** The user has tried to use an ALTER DISK TBS statement that is not
allowed for a non-disk tablespace.

**Action:** Verify that the tablespace type and ALTER statement match.

**0x31252 ( 201298) qpERR_ABORT_QDT_INVALID_ALTER_ON_MEM_TBS Invalid ALTER
MEMORY TABLESPACE Statement. The tablespace to alter is not a memory
tablespace.**

**Cause:** The user has tried to use an ALTER MEMORY TBS statement that is not
allowed for a non-memory tablespace.

**Action:** Verify that the tablespace type and ALTER statement match.

**0x31253 ( 201299) qpERR_ABORT_QDT_INVALID_ALTER_ON_VOLATILE_TBS Invalid ALTER
VOLATILE TABLESPACE Statement. The tablespace to alter is not a volatile
tablespace.**

**Cause:** The user has tried to use an ALTER VOLATILE TBS statement that is not
allowed for a non-volatile tablespace.

**Action:** Verify that the tablespace type and ALTER statement match.

**0x31254 ( 201300) qpERR_ABORT_QDT_INVALID_ALTER_ON_MEM_OR_VOL_TBS Invalid
ALTER TABLESPACE Statement. The tablespace to alter is neither a volatile
tablespace nor a memory tablespace.**

**Cause:** The user has tried to use an ALTER VOLATILE TBS statement that is not
allowed for a non-volatile or non-memory tablespace.

**Action:** Verify that the tablespace type and ALTER statement match.

**0x31255 ( 201301) qpERR_ABORT_QDT_CANNOT_DISCARD Unable to discard the
specified tablespace.**

**Cause:** The specified tablespace is not a user or temp tablespace.

**Action:** Check the specified tablespace.

**0x31256 ( 201302) qpERR_ABORT_QDT_CANNOT_ALTER_SYSTEM_TABLESPACE Unable to
alter the system tablespace.**

**Cause:** The specified tablespace is not a user or temp tablespace.

**Action:** Check the specified tablespace.

**0x3128B ( 201355) qpERR_ABORT_QDT_PART_TABLE_IN_DIFFERENT_TBS A partitioned
table contains partitions in different tablespaces.**

**Cause:** A partitioned table contains partitions in different tablespaces.

**Action:** Drop the partitioned table first, and then retry this statement.

**0x3128C ( 201356) qpERR_ABORT_QDT_PART_INDEX_IN_DIFFERENT_TBS A partitioned
index contains partitions in different tablespaces.**

**Cause:** A partitioned index contains partitions in different tablespaces.

**Action:** Drop the partitioned index first, and then retry this statement.

**0x31295 ( 201365) qpERR_ABORT_QDT_ERR_INVALID_USER_DEFAULT_TEMP_TBS Invalid
user default temporary tablespace ( ID : \<0%d\> )**

**Cause:** The user default temporary tablespace is invalid.

**Action:** Check the user default temporary tablespace.

**0x312A0 ( 201376) qpERR_ABORT_QDT_DUPLICATE_TBS_ATTRIBUTE Duplicate tablespace
attribute. \<0%s\>**

**Cause:** The user tried to specify a duplicate attribute name in the list of
tablespace attributes.

**Action:** Check the list of tablespace attributes.

**0x312A9 ( 201385) qpERR_ABORT_QDT_UNABLE_TO_COMPRESS_VOLATILE_TBS_LOG Log
compression is not supported for volatile tablespaces.**

**Cause:** The user tried to compress a volatile tablespace log.

**Action:** No action is necessary.

**0x312E1 ( 201441) qpERR_ABORT_QDT_NON_ASCII_TBS_NAME Invalid tablespace name
character set.**

**Cause:** Invalid tablespace name character set.

**Action:** Use the ASCII character set for tablespace names.

**0x312E6 ( 201446) qpERR_ABORT_QDT_CANNOT_RENAME_SYS_TBS The system tablespace
cannot be renameed.**

**Cause:** Renaming system tablespace is not allowed.

**Action:** Check if the specified tablespace is the system tablespace.

**0x31365 ( 201573) qpERR_ABORT_QDT_DROP_TBS_DISABLE_BECAUSE_TEMP_TABLE Could
not drop volatile tablespace**

**Cause:** The volatile tablespace could not be dropped because it contains one
or more temporary tables.

**Action:** Truncate all temporary tables in the volatile tablespace and try
again.

**0x3145D ( 201821)
qpERR_ABORT_QDT_CANNOT_USE_USER_MEMORY_TABLESPACE_IN_DISK_EDITION Memory
tablespace created by a user cannot be used in the disk edition. (Tablespace :
\<0%s\>)**

**Cause:** Only disk/volatile tablespace is allowed to use in the disk edition.

**Action:** Use disk or volatile tablespace, otherwise purchase the
standard/enterprise edition.

**0x311EE ( 201198) qpERR_ABORT_TRIGGER_INVALID_REFERENCING_GRANULARITY A
REFERENCING clause can be used only in a FOR EACH ROW context.**

**Cause:** A REFERENCING clause is used without a FOR EACH ROW option.

**Action:** Use the FOR EACH ROW option.

**0x311EF ( 201199) qpERR_ABORT_TRIGGER_UNSUPPORTED_EVENT_TIMING Unsuported
trigger event timing. Event timing using the BEFORE trigger is not supported
yet. Use AFTER trigger event timing instead.**

**Cause:** BEFORE trigger event timing was used.

**Action:** Do not use BEFORE trigger event timing.

**0x311F1 ( 201201) qpERR_ABORT_TRIGGER_DUPLICATED_NAME Duplicate trigger names
\<0%s\>**

**Cause:** The same trigger name already exists in the database.

**Action:** Use another trigger name.

**0x311F2 ( 201202) qpERR_ABORT_TRIGGER_NOT_EXIST Trigger not found \<0%s\>**

**Cause:** The trigger does not exist.

**Action:** Check the trigger name.

**0x311F3 ( 201203) qpERR_ABORT_TRIGGER_INVALID_REFERENCING Invalid referencing
keyword on DML event**

**Cause:** The NEW[/OLD] referencing keyword cannot be used in a DELETE[/INSERT]
statement.

**Action:** In a DELETE statement, use the OLD referencing keyword. In an INSERT
statement, use the NEW referencing keyword.

**0x311F5 ( 201205) qpERR_ABORT_TRIGGER_WHEN_SUBQUERY A subquery is not allowed
as part of a WHEN condition \<0%s\>.**

**Cause:** The WHEN condition contains a subquery.

**Action:** Do not use a subquery as part of the WHEN condition.

**0x311F6 ( 201206) qpERR_ABORT_TRIGGER_PSM A trigger cannot invoke a stored
procedure or function \<0%s\>.**

**Cause:** A trigger cannot invoke a stored procedure or function.

**Action:** Do not reference a stored procedure or function in the trigger.

**0x311F7 ( 201207) qpERR_ABORT_TRIGGER_INVALID_ACTION_STMT The action body of
the trigger cannot contain a restricted statement. \<0%s\>**

**Cause:** The action body of the trigger contains a transaction control
statement or a call to a stored procedure or function.

**Action:** Do not use a transaction control statement. Do not invoke a stored
procedure or function.

**0x311F8 ( 201208) qpERR_ABORT_TRIGGER_CYCLE_DETECTED The action body of the
trigger cannot contain a cyclic modification.**

**Cause:** The action body of the trigger contains a cyclic modification.

**Action:** Remove the cyclic modification from the action body of the trigger.

**0x311F9 ( 201209) qpERR_ABORT_TRIGGER_RECOMPILE The attempt to recompile the
trigger \<0%s\> was aborted because the creation statement was invalid. :
\<1%s\> \<2%s\>**

**Cause:** The attempt to recompile the trigger failed because the creation
statement was invalid.

**Action:** Check the trigger creation statement.

**0x311FA ( 201210) qpERR_ABORT_TRIGGER_UNSUPPORTED Unsupported trigger feature.
\<0%s\>**

**Cause:** Unsupported trigger feature (Ex\> BEFORE Event, TABLE Referencing )

**Action:** Do not use features that are not supported for triggers.

**0x311FB ( 201211) qpERR_ABORT_TRIGGER_WHEN_REFERENCING A WHEN condition
requires a REFERENCING clause.**

**Cause:** A WHEN condition is used without a REFERENCING clause.

**Action:** Use the WHEN condition with a REFERENCING clause.

**0x311FC ( 201212) qpERR_ABORT_TRIGGER_INVALID_TABLE_NAME Invalid trigger
object. \<0%s\>**

**Cause:** The user tried to create a trigger for a non-user table, for example:
a sequence, a view, etc.

**Action:** Attempt this action on a normal user table.

**0x311FD ( 201213) qpERR_ABORT_NO_DDL_FOR_META No DDL (data definition
language) statements can be executed on meta tables**

**Cause:** DDL execution on meta tables is not allowed.

**Action:** Do not execute DDL statements on meta tables.

**0x3122E ( 201262) qpERR_ABORT_INVALID_TRIGGER_TYPE Invalid trigger type**

**Cause:** An invalid trigger type was used.

**Action:** Specify either INSERT, UPDATE or DELETE.

**0x312F0 ( 201456) qpERR_ABORT_TRIGGER_INVALID_TABLE_OWNER_NAME The table
owner's name is required when the trigger owner's name is specified. \<0%s\>**

**Cause:** The table owner's name was not specified but the trigger owner's name
was specified.

**Action:** Specify the table owner's name.

**0x31346 ( 201542) qpERR_ABORT_TRIGGER_UNSUPPORTED_INSTEAD_OF_EACH_STMT The FOR
EACH STATEMENT clause is not supported for use with INSTEAD OF triggers.**

**Cause:** The FOR EACH STATEMENT clause was specified in an INSTEAD OF trigger
creation statement.

**Action:** Do not use the FOR EACH STATEMENT clause with an INSTEAD OF trigger.

**0x31347 ( 201543) qpERR_ABORT_TRIGGER_UNSUPPORTED_INSTEAD_OF_WHEN_COND WHEN
conditions are not supported for use with INSTEAD OF triggers.**

**Cause:** A WHEN condition was specified in an INSTEAD OF trigger creation
statement.

**Action:** Do not use a WHEN condition with an INSTEAD OF trigger.

**0x31348 ( 201544) qpERR_ABORT_TRIGGER_UNSUPPORTED_INSTEAD_OF_COLUMN_LIST
UPDATE OF trigger events are not supported for use with INSTEAD OF triggers.**

**Cause:** An UPDATE OF trigger event was specified in an INSTEAD OF trigger
creation statement.

**Action:** Do not specify an UPDATE OF trigger event with an INSTEAD OF
trigger.

**0x31349 ( 201545) qpERR_ABORT_TRIGGER_INSTEAD_OF_NOT_VIEW INSTEAD OF triggers
can only be used with views.**

**Cause:** An attempt was made to define an INSTEAD OF trigger based on an
object other than a view.

**Action:** Specify a view in the ON clause of an INSTEAD OF trigger.

**0x3134A ( 201546) qpERR_ABORT_TRIGGER_BEFORE_AFTER_VIEW BEFORE and AFTER
triggers are not supported for use with views.**

**Cause:** An attempt was made to define a BEFORE or AFTER trigger based on a
view.

**Action:** Specify a user table in the ON clause of a BEFORE or AFTER trigger.

**0x31207 ( 201223) qpERR_ABORT_NOT_FOUND_SYNONYM The specified synonym was not
found**

**Cause:** The synonym does not exist.

**Action:** Check the statement.

**0x31208 ( 201224) qpERR_ABORT_SAME_SYNONYM Unable to create a synonym with the
same name as the object**

**Cause:** The synonym and target object are the same.

**Action:** Check the statement.

**0x31319 ( 201497) qpERR_ABORT_CIRCULAR_SYNONYM Circular synonym definition
detected. \<0%s\>**

**Cause:** The synonym forms a circular loop.

**Action:** Check the synonym definition.

**0x3131B ( 201499) qpERR_ABORT_SYNONYM_RESOLVE_OVERFLOW Over \<0%s\>
consecutive synonyms cannot be resolved. \<1%s\>**

**Cause:** A large number of consecutive synonyms cannot be resolved.

**Action:** Check the statement.

**0x3118D ( 201101) qpERR_ABORT_QSF_FUNCTION_NOT_ALLOWED This function is
executable only in an execute procedure/function statement.**

**Cause:** The function was called in DML.

**Action:** Use this function only in an EXECUTE statement.

**0x3120C ( 201228) qpERR_ABORT_QSF_INVALID_FILEOPEN_MODE Invalid file open
mode.**

**Cause:** An invalid value was specified for the file open mode.

**Action:** Correct the mode so that it is one of the values: 'r', 'a', or 'w'.

**0x3120D ( 201229) qpERR_ABORT_QSF_DIRECTORY_ACCESS_DENIED Directory access
denied.**

**Cause:** A directory object was specified for which access has not been
granted.

**Action:** Grant access to the directory object using the statement GRANT
READ[WRITE] ON DIRECTORY [object] TO [username].

**0x31211 ( 201233) qpERR_ABORT_QSF_INVALID_ERROR_RANGE Error number argument to
raise_application_error of \<0%d\> is out of range.**

**Cause:** An attempt was made to specify a number that does not fall within the
allowed range.

**Action:** Use an error number in the range of 990000 to 991000, inclusive.

**0x31227 ( 201255) qpERR_ABORT_QSF_INVALID_IPADDRESS The Internet address is
incorrectly formed or is nonexistent.**

**Cause:** The internet address is incorrectly formed or does not exist.

**Action:** Enter the internet address in its correct form and retry.

**0x31228 ( 201256) qpERR_ABORT_QSF_INVALID_PORT The port number is not valid.**

**Cause:** The port number is out of range.

**Action:** Enter a valid port number (a positive integer value between 1025 and
65535) and retry.

**0x31229 ( 201257) qpERR_ABORT_QSF_INVALID_TTL The ttl is not valid.**

**Cause:** The ttl is out of range.

**Action:** Enter a valid ttl (positive integer value between 0 and 255) and
retry.

**0x3122A ( 201258) qpERR_ABORT_QSF_SOCKET_FAILED SENDMSG failed due to failure
opening or setting the socket.**

**Cause:** The system failed to open or set the socket.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x3122B ( 201259) qpERR_ABORT_QSF_SENDMSG_FAILED SENDMSG failed due to an
internal error while doing the actual send.**

**Cause:** The system failed to execute the SENDMSG command.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x3125A ( 201306) qpERR_ABORT_QSX_TABLE_MODIFIED The table structure has been
modified. \<0%s\>**

**Cause:** The table structure has been modified.

**Action:** Execute the query again.

**0x31413 ( 201747) qpERR_ABORT_QSF_RECURSIVE_CALL_TO_DCEP_IS_NOT_ALLOWED A
recursive call to DBMS_CONCURRENT_EXEC package is not allowed.**

**Cause:** A recursive call to DBMS_CONCURRENT_EXEC package is not allowed.

**Action:** Do not call recursively to DBMS_CONCURRENT_EXEC package.

**0x31416 ( 201750) qpERR_ABORT_QCI_DISABLED_TCP The user cannot connect using
TCP.**

**Cause:** This user cannot connect using TCP.

**Action:** Connect using SSL/UNIX domain/IPC. JAVA users can change the
connection method in the application (for iSQL, change the value of the
iSQL_CONNECTION environment variable).

**0x3121F ( 201247) qpERR_ABORT_QDQ_QUEUE_ALTER_DENIED Cannot alter queue
table**

**Cause:** A queue table cannot be altered.

**Action:** Use drop queue / create queue.

**0x31220 ( 201248) qpERR_ABORT_QDQ_QUEUE_DML_DENIED Cannot execute DML
statements on queue table**

**Cause:** DML statements cannot be executed on queue tables.

**Action:** Use enqueue or dequeue instead.

**0x31221 ( 201249) qpERR_ABORT_QDQ_TABLE_ENQUEUE_DENIED Cannot use an ENQUEUE
statement on a normal table**

**Cause:** An ENQUEUE statement cannot be used on a normal table.

**Action:** Do not use the ENQUEUE statement on a normal table.

**0x31222 ( 201250) qpERR_ABORT_QDQ_TABLE_DEQUEUE_DENIED Cannot use a DEQUEUE
statement on a normal table**

**Cause:** A DEQUEUE statement cannot be used on a normal table.

**Action:** Do not use the DEQUEUE statement on a normal table.

**0x31223 ( 201251) qpERR_ABORT_QDQ_TABLE_DROP_QUEUE_DENIED Cannot use a DROP
QUEUE statement on a normal table**

**Cause:** DROP QUEUE statements cannot be used on a normal table.

**Action:** Do not use the DROP QUEUE statement on a normal table.

**0x31224 ( 201252) qpERR_ABORT_QDQ_QUEUE_DROP_TABLE_DENIED Cannot use a DROP
TABLE statement on a queue table**

**Cause:** DROP TABLE statements cannot be used on a queue table.

**Action:** Do not use the DROP TABLE statement on a queue table.

**0x31225 ( 201253) qpERR_ABORT_QDQ_QUEUE_NAME_TOO_LONG Queue name is too long**

**Cause:** A queue with a name longer than 28 characters cannot be created.

**Action:** Shorten the name of the queue.

**0x31226 ( 201254) qpERR_ABORT_QDQ_QUEUE_DEQUEUE_SUBQ_EXIST Subquery exist in
dequeue statement**

**Cause:** Subqueries cannot be used in DEQUEUE statements.

**Action:** Do not use subqueries with DEQUEUE statements.

**0x312E5 ( 201445) qpERR_ABORT_QDQ_NOT_FOUND_QUEUE Queue not found**

**Cause:** The queue is not in the meta database.

**Action:** Verify that the queue exists.

**0x312AD ( 201389) qpERR_ABORT_QDB_GEOMETRY_VIOLATION_ON_VOLATILE_TABLE A
volatile table cannot have a geometry column.**

**Cause:** Volatile tables cannot have geometry columns.

**Action:** Remove the geometry column specification.

**0x312AE ( 201390) qpERR_ABORT_QCP_DUPLICATE_LOGGING_MODE Only one LOGGING or
NOLOGGING clause must be specified.**

**Cause:** Duplicate logging clause.

**Action:** Specify only one LOGGING or NOLOGGING clause.

**0x312AF ( 201391) qpERR_ABORT_QCP_INVALID_PARALLEL_DEGREE The value for
PARALLEL DEGREE must be larger than 0 and less than 65536.**

**Cause:** Invalid parallel degree value.

**Action:** Set PARALLEL DEGREE to a value between 0 \~65536.

**0x312BB ( 201403) qpERR_ABORT_QCMLINK_NOT_INIT_REMOTE_TABLE_FUNC The database
link module did not start.**

**Cause:** Failed to execute this statement because the dblink module did not
start.

**Action:** Check DBLINK_ENABLE , LINKER_PORT_NO property.

**0x312D4 ( 201428) qpERR_ABORT_QDB_NO_SUPP_LOGGING_ON_VOLATILE_TABLE
Supplemental logging is not supported for volatile tables.**

**Cause:** The user tried to alter a volatile table in order to perform
supplemental logging.

**Action:** Ensure that the table is not a volatile table.

**0x312D5 ( 201429) qpERR_ABORT_QDB_NO_SUPP_LOGGING_WITHOUT_PK Supplemental
logging is not supported without a primary key.**

**Cause:** The user tried to perform supplemental logging without a primary key.

**Action:** Ensure that the table has a primary key.

**0x312F1 ( 201457) qpERR_ABORT_QDB_INVALID_PCTFREE_VALUE Invalid PCTFREE
value**

**Cause:** A PCTFREE value must be between 0 and 99.

**Action:** Check the PCTFREE value.

**0x312F2 ( 201458) qpERR_ABORT_QDB_INVALID_PCTUSED_VALUE Invalid PCTUSED
value**

**Cause:** A PCTUSED value must be between 0 and 99.

**Action:** Check the PCTUSED value.

**0x312F3 ( 201459) qpERR_ABORT_QDB_INVALID_PCTFREE_PCTUSED_VALUE the sum of
PCTUSED and PCTFREE cannot exceed 100.**

**Cause:** The sum of PCTUSED and PCTFREE cannot exceed 100.

**Action:** Check the PCTFREE and PCTUSED values.

**0x3131E ( 201502) qpERR_ABORT_QDB_CANNOT_SET_NULL_DEFAULT_VALUE Unable to add
PRIMARY KEY or NOT NULL constraint on a column with a NULL default value.**

**Cause:** Unable to add a NOT NULL or PRIMARY KEY constraint on a column with a
NULL default value.

**Action:** Remove the NULL default value.

**0x31340 ( 201536) qpERR_ABORT_QDB_CANNOT_SET_DEFAULT_VALUE_WITH_ENCRYPT An
encrypted column with a default value other than NULL cannot be added.**

**Cause:** An encrypted column with a default value other than NULL cannot be
added.

**Action:** Remove the default value or set null value.

**0x31470 ( 201840) qpERR_ABORT_QDQ_NOT_EMPTY_QUEUE A queue is not empty. Only
empty queue can reset a msgid.**

**Cause:** Cannot perform to reset a msgid because it is not a empty queue.

**Action:** Check whether the queue is empty, otherwise remove the data from the
queue.

### RETRY

**0x331FE ( 209406) qpERR_REBUILD_QMX_TOO_OLD_PLANTREE The plan tree is too
old**

**Cause:** The plan tree is too old.

**Action:** No action is necessary. The plan tree will be automatically
recompiled.

**0x332AA ( 209578) qpERR_REBUILD_QCU_RESOURCE_BUSY Resource busy.**

**Cause:** The resource is busy.

**Action:** No action is necessary.

**0x33247 ( 209479) qpERR_REBUILD_QCI_PROC_INVALID A procedure or function was
invalidated during execution.**

**Cause:** A procedure or function has been invalidated.

**Action:** Recompile the required procedure or function again.

**0x33249 ( 209481) qpERR_REBUILD_QCI_EXEC The statement failed during
execution.**

**Cause:** The statement failed during execution.

**Action:** No action is necessary. The statement will be automatically rebuilt.

**0x332D3 ( 209619) qpERR_REBUILD_TRIGGER_INVALID A trigger was invalidated
during execution.**

**Cause:** A trigger has been invalidated.

**Action:** Recompile the trigger again.

6.SD Error Code
---------------

### ABORT

**0xE1001 ( 921601) sdERR_ABORT_SDM_SHARD_META_NOT_CREATED There is no shard
meta \<0%s\>.**

**Cause:** The shard meta has not been created.

**Action:** Create shard meta.

**0xE1002 ( 921602) sdERR_ABORT_SDM_SHARD_NODE_OVERFLOW There is overflow in the
number of shard data nodes.**

**Cause:** The shard data nodes are exceeded.

**Action:** Refer to the manual to verify the number of permissible shard data
nodes.

**0xE1003 ( 921603) sdERR_ABORT_SDM_SHARD_NODE_NOT_EXIST The shard data node
cannot be found.**

**Cause:** The specified shard data node does not exist.

**Action:** Verify if the name of shard data node is correct.

**0xE1004 ( 921604) sdERR_ABORT_SDM_SHARD_TABLE_NOT_EXIST The shard object
cannot be found.**

**Cause:** The shard object does not exist.

**Action:** Verify if the shard object is correct.

**0xE1005 ( 921605) sdERR_ABORT_SDM_SHARD_KEY_COLUMN_NOT_EXIST The shard key
\<0%s\>.\<1%s\>.\<2%s\> cannot be found.**

**Cause:** The specified shard key does not exist.

**Action:** Verify if the shard key is correct.

**0xE1006 ( 921606) sdERR_ABORT_SDM_UNSUPPORTED_SHARD_KEY_COLUMN_TYPE The data
type of shard key \<0%s\>.\<1%s\>.\<2%s\> is not supported.**

**Cause:** The data type is not supported by the shard key.

**Action:** Verify if the data type used in the shard key is correct.

**0xE1007 ( 921607) sdERR_ABORT_SDM_INVALID_RANGE_FUNCTION The split method in
the shard key does not correspond.**

**Cause:** The split method in the shard key does not correspond.

**Action:** Verify if the split method is correct.

**0xE1008 ( 921608) sdERR_ABORT_SDM_AREADY_EXIST_SHARD_OBJECT The object already
exists.**

**Cause:** The object is a pre-existing shard object.

**Action:** Verify the object name.

**0xE1009 ( 921609) sdERR_ABORT_SDM_SYSTEM_OBJECT A shard object cannot be
created with a meta object.**

**Cause:** A shard object cannot be created with a meta object.

**Action:** Verify if the object privilege is correct.

**0xE100A ( 921610) sdERR_ABORT_SDM_CHECK_META_VERSION Confirmation of shard
version failed.**

**Cause:** The shard version cannot be confirmed.

**Action:** Verify the shard version with the altibase-v command to see if the
version is correct.

**0xE100B ( 921611) sdERR_ABORT_SDM_MISMATCH_META_VERSION The shard version
between meta node and data node is mismatched.**

**Cause:** The shard version between meta and data nodes does not correspond.

**Action:** Verify the shard version with the altibase-v command to see if the
version is correct.

**0xE1065 ( 921701) sdERR_ABORT_SDA_NOT_SUPPORTED_SQLTEXT_FOR_SHARD The
statement is not supported in Altibase sharding due to the following reason:
\<0%s\>.**

**Cause:** Altibase sharding does not support the statement.

**Action:** Verify if the statement is correct.

**0xE1066 ( 921702) sdERR_ABORT_SDA_INVALID_SHARD_KEY_CONDITION Invalid shard
key value expression was used.**

**Cause:** The expression of shard key value is invalid.

**Action:** Verify if the shard key expression is correct.

**0xE1067 ( 921703) sdERR_ABORT_SDA_NOT_EXIST_SHARD_KEY_CONDITION The shard key
value cannot be found.**

**Cause:** The shard key value does not exist.

**Action:** Verify if the shard key exists.

**0xE10C9 ( 921801) sdERR_ABORT_SDF_INVALID_SHARD_NODE Invalid shard data node
was used.**

**Cause:** The host IP and port number for shard data node cannot be found.

**Action:** Verify the host IP and port number for shard data node.

**0xE10CA ( 921802) sdERR_ABORT_SDF_AREADY_EXIST_SHARD_NODE The shard data node
of identical IP and port already exists.**

**Cause:** The shard data node of identical IP and port already exists.

**Action:** Verify the IP and port of the shard data node.

**0xE10CB ( 921803) sdERR_ABORT_SDF_SHARD_USER_NAME_TOO_LONG The object user
name is too long.**

**Cause:** The user name of a shard object is permitted to contain less than 128
characters.

**Action:** Verify the length of the object user name.

**0xE10CC ( 921804) sdERR_ABORT_SDF_SHARD_TABLE_NAME_TOO_LONG The object name is
too long.**

**Cause:** The shard object name is permitted to contain less than 128
characters.

\#Action : Verify the length of the object name.

**0xE10CD ( 921805) sdERR_ABORT_SDF_SHARD_NODE_NAME_TOO_LONG The name of shard
data node is too long.**

**Cause:** The name of shard data node is permitted to contain less than 40
characters.

**Action:** Verify the length of the shard data node name.

**0xE10CE ( 921806) sdERR_ABORT_SDF_SHARD_MAX_VALUE_TOO_LONG The maximum value
for shard split method is too large.**

**Cause:** The maximum value for shard split method is too large.

**Action:** Refer to the manual to verify permissible range for the shard split
method.

**0xE10CF ( 921807) sdERR_ABORT_SDF_SHARD_KEYCOLUMN_NAME_TOO_LONG The shard key
name is too long.**

**Cause:** The shard key name is permitted to contain less than 40 characters.

**Action:** Verify the length of the shard key name.

**0xE10D0 ( 921808) sdERR_ABORT_SDF_INVALID_SHARD_SPLIT_METHOD_NAME The shard
split method is invalid.**

**Cause:** Invalid shard split method is used.

**Action:** Refer to the manual verify if the shard split method is correct.

**0xE10D1 ( 921809) sdERR_ABORT_SDF_INVALID_SHARD_TABLE The specified object
cannot be found.**

**Cause:** The specified object does not exist.

**Action:** Retry after verifying the object and user name.

**0xE10D2 ( 921810) sdERR_ABORT_SDF_INVALID_RANGE_VALUE The permissible range of
shard key \<0%s\> is invalid.**

**Cause:** The permissible range for the shard key is invalid.

**Action:** Refer to the manual to verify the permissible range for the shard
key.

**0xE112D ( 921901) sdERR_ABORT_SHARD_LIBRARY_ERROR An error occurred in the
library function call when executing \<1%s\> for shard data node \<0%s\>.**

**Cause:** There is an error in library function call of shard data node.

**Action:** Verify the state of shard data node.

**0xE112E ( 921902) sdERR_ABORT_SHARD_LIBRARY_ERROR_1 The following error occurs
when \<1%s\> of shard data node \<0%s\> is performed.: \<2%s\>**

**Cause:** An error occurred during the library function call of the shard data
node.

**Action:** Verify the state of shard data node.

**0xE112F ( 921903) sdERR_ABORT_SHARD_LIBRARY_ERROR_2 The following error occurs
when \<1%s\> of shard data node \<0%s\> is performed.: \<2%s\>\<3%s\>**

**Cause:** An error occurred during the library function call of the shard data
node.

**Action:** Verify the state of shard data node.

**0xE1130 ( 921904) sdERR_ABORT_SHARD_LIBRARY_ERROR_3 The following error occurs
when \<1%s\> of shard data node \<0%s\> is performed.: \<2%s\>\<3%s\>\<4%s\>**

**Cause:** An error occurred during the library function call of the shard data
node.

**Action:** Verify the state of shard data node.

**0xE1131 ( 921905) sdERR_ABORT_SHARD_LIBRARY_ERROR_4 The following error occurs
when \<1%s\> of shard data node \<0%s\> is performed.:
\<2%s\>\<3%s\>\<4%s\>\<5%s\>**

**Cause:** An error occurred during the library function call of the shard data
node.

**Action:** Verify the state of shard data node.

**0xE1132 ( 921906) sdERR_ABORT_SHARD_LIBRARY_LINK_FAILURE_ERROR The link failed
when performing \<1%s\> on shard data node \<0%s\>.**

**Cause:** The link on the shard data node failed.

**Action:** Verify the state of link on the shard data node.

**0xE1133 ( 921907) sdERR_ABORT_INIT_SDL_ODBCCLI The library initialization
failed and the following error occurred: \<0%s\>**

**Cause:** Library initialization failed.

**Action:** Verify the library of shard meta node.

**0xE1134 ( 921908) sdERR_ABORT_EXECUTE_NULL_DBC The connection cannot be found
when shard data node \<0%s\> is \<1%s\>.**

**Cause:** The connection state of shard data node does not exist.

**Action:** Verify the connection state.

**0xE1135 ( 921909) sdERR_ABORT_EXECUTE_NULL_STMT The statement cannot be found
when shard data node \<0%s\> is \<1%s\>.**

**Cause:** The statement in the shard data node does not exist.

**Action:** Verify the statement in the shard data node.

**0xE1136 ( 921910) sdERR_ABORT_UNINITIALIZED_LIBRARY Shard data node \<0%s\>
fails to perform \<1%s\> because the library was not initialized.**

**Cause:** The library of shard meta node was not initialized.

**Action:** Restart the server after verifying the library of shard meta node.

**0xE1137 ( 921911) sdERR_ABORT_DBCLINK_ALLOC \<1%s\> on shard data node \<0%s\>
failed.**

**Cause:** There is insufficient memory for the shard data node connection.

**Action:** Verify the memory usage.

**0xE1321 ( 922401) sdERR_ABORT_SDI_SHARD_LINKER_NOT_INITIALIZED The meta
connection cannot be initialized.**

**Cause:** The meta connection was not initialized.

**Action:** Verify the setting of shard meta and data is correct.

**0xE1322 ( 922402) sdERR_ABORT_SDI_INCOMPLETE_RANGE_SET The shard key range of
\<0%s\>.\<1%s\> is invalid.**

**Cause:** The shard key range is invalid.

**Action:** Verify the key range for shard split method.

**0xE1385 ( 922501) sdERR_ABORT_EXIST_SHARD_TABLE_OUTSIDE_SHARD_VIEW The shard
table is only available within the shard view.: \<0%s\>**

**Cause:** The shard table is only available within the shard view.

**Action:** Rewrite the shard query.

**0xE1386 ( 922502) sdERR_ABORT_INVALID_SHARD_QUERY The shard query is not
supported and the following error occurs.: \<0%s\> \<1%s\>**

**Cause:** The shard query is invalid.

**Action:** Rewrite the shard query.

**0xE13E7 ( 922599) sdERR_ABORT_SDC_UNEXPECTED_ERROR Unexpected errors have
occurred.: \<0%s\>: \<1%s\>**

**Cause:** An unexpected error has occurred.

**Action:** Verify the error number in the trace log file and contact Altibase
Support Center (http://support.altibase.com/en/).

7.ST Error Code
---------------

### FATAL

**0xA0003 ( 655363) stERR_FATAL_MEMORY_SHORTAGE Out of memory**

**Cause:** Out of memory

**Action:** Verify that the system has sufficient memory.

**0xA0005 ( 655365) stERR_FATAL_INCOMPATIBLE_TYPE Incompatible data type
\<0%s\>.**

**Cause:** Incompatible data type

**Action:** Check the compatibility between data types.

**0xA0031 ( 655409) stERR_FATAL_COLUMN_NOT_FOUND Unable to find a column**

**Cause:** Unable to find a column.

**Action:** Verify that the column being looked for is valid.

### ABORT

**0xA1002 ( 659458) stERR_ABORT_NOT_APPLICABLE Not applicable**

**Cause:** This error occurs due to a logical programming error.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0xA1007 ( 659463) stERR_ABORT_LANGUAGE_MODULE_NOT_FOUND Language module
\<0%s\> not found.**

**Cause:** The language module was not found.

**Action:** Check the language.

**0xA1008 ( 659464) stERR_ABORT_DATATYPE_MODULE_NOT_FOUND Data type module
\<0%s\> not found.**

**Cause:** The data type module was not found.

**Action:** Check the data type.

**0xA1009 ( 659465) stERR_ABORT_CONVERSION_MODULE_NOT_FOUND Conversion module
\<0%s\> not found.**

**Cause:** The conversion module was not found.

**Action:** Check the compatibility between data types.

**0xA100A ( 659466) stERR_ABORT_FUNCTION_MODULE_NOT_FOUND Function module
\<0%s\> not found.**

**Cause:** The function module was not found.

**Action:** Use the correct function name.

**0xA100B ( 659467) stERR_ABORT_INVALID_FUNCTION_ARGUMENT Invalid number of
arguments for a function.**

**Cause:** The number of arguments for the function was invalid.

**Action:** Check the number of arguments for the function.

**0xA100C ( 659468) stERR_ABORT_CONVERSION_NOT_APPLICABLE Conversion not
applicable.**

**Cause:** The conversion is not applicable.

**Action:** Check the compatibility between data types.

**0xA100D ( 659469) stERR_ABORT_INVALID_LENGTH Invalid length of the data type**

**Cause:** Invalid length of the data type.

**Action:** Check the length of the data type.

**0xA100E ( 659470) stERR_ABORT_INVALID_PRECISION Invalid precision of the data
type**

**Cause:** Invalid precision of the data type

**Action:** Check the precision of the data type.

**0xA100F ( 659471) stERR_ABORT_INVALID_SCALE Invalid scale of the data type**

**Cause:** Invalid scale of the data type

**Action:** Check the scale of the data type.

**0xA1010 ( 659472) stERR_ABORT_VALUE_OVERFLOW Value overflow**

**Cause:** Value overflow

**Action:** Change the value or data type.

**0xA1011 ( 659473) stERR_ABORT_INVALID_LITERAL Invalid literal**

**Cause:** Invalid literal

**Action:** Check the constant indicating the data type.

**0xA1013 ( 659475) stERR_ABORT_STACK_OVERFLOW Calculation stack overflow**

**Cause:** Calculation stack overflow

**Action:** Alter the calculation stack size using the ALTER SESSION statement.

**0xA1014 ( 659476) stERR_ABORT_NOT_AGGREGATION The function is not an aggregate
function.**

**Cause:** The function is not an aggregate function.

**Action:** Remove the ALL or DISTINCT keyword.

**0xA1016 ( 659478) stERR_ABORT_DIVIDE_BY_ZERO Division by zero**

**Cause:** Division by zero

**Action:** Determine whether an attempt to divide a number by zero is being
made.

**0xA1017 ( 659479) stERR_ABORT_ARGUMENT_NOT_APPLICABLE The argument is not
applicable.**

**Cause:** The argument is not applicable to the function.

**Action:** Change the argument so that it falls within the valid range.

**0xA1018 ( 659480) stERR_ABORT_NOT_SUPPORTED_OBJECT_TYPE The specified object
type is not currently supported.**

**Cause:** Unsupported object type

**Action:** For geometry types, only the POINT type is currently supported.

**0xA1019 ( 659481) stERR_ABORT_OBJECT_TYPE_NOT_APPLICABLE Inapplicable object
type**

**Cause:** The specified object type is not applicable to the function.

**Action:** Check the object type.

**0xA101A ( 659482) stERR_ABORT_INVALID_WKT Error parsing well-known-text**

**Cause:** The specified well-known-text is not correct.

**Action:** Check the well-known-text.

**0xA101B ( 659483) stERR_ABORT_TO_CHAR_MAX_PRECISION The value exceeds the
maximum precision ( \<0%d\> ) of the format.**

**Cause:** Maximum precision of format exceeded.

**Action:** Check the size of format string.

**0xA101C ( 659484) stERR_ABORT_VALIDATE_INVALID_VALUE Invalid data value**

**Cause:** The value of the data exceeds the logical value scope.

**Action:** Check the data value.

**0xA101D ( 659485) stERR_ABORT_VALIDATE_INVALID_LENGTH Invalid data length**

**Cause:** The length of the data exceeds the valid scope.

**Action:** Check the length of the data.

**0xA101E ( 659486) stERR_ABORT_CODING_INVALID_FMT Invalid coding format**

**Cause:** The compiled coding format is not valid.

**Action:** Check the compiled format.

**0xA101F ( 659487) stERR_ABORT_CODING_DATA_FMT_MISMATCH Mismatched data and
format**

**Cause:** The data string does not match the specified format.

**Action:** Check the data string.

**0xA1020 ( 659488) stERR_ABORT_INVALID_LITERAL_AFTER_ESCAPE Missing or invalid
literal following the escape character**

**Cause:** Either '%' or '_' must follow the escape character.

**Action:** Check the LIKE predicate.

**0xA1021 ( 659489) stERR_ABORT_INVALID_ESCAPE Invalid escape literal**

**Cause:** The length of the escape is greater than one. The escape literal is
invalid.

**Action:** Check the escape character in the LIKE predicate.

**0xA1022 ( 659490) stERR_ABORT_INVALID_DATE Invalid date literal**

**Cause:** The text to be converted to a date type is invalid.

**Action:** Check the arguments for the date conversion function.

**0xA1023 ( 659491) stERR_ABORT_INVALID_YEAR Invalid year**

**Cause:** The year part of the date literal is invalid or out of range.

**Action:** Check the arguments for the date conversion function.

**0xA1024 ( 659492) stERR_ABORT_INVALID_MONTH Invalid month**

**Cause:** The month part of the date literal is invalid or out of range.

**Action:** Check the arguments for the date conversion function.

**0xA1025 ( 659493) stERR_ABORT_INVALID_DAY Invalid day**

**Cause:** The day part of the date literal is invalid or out of range.

**Action:** Check the arguments for the date conversion function.

**0xA1026 ( 659494) stERR_ABORT_INVALID_HOUR Invalid hour**

**Cause:** The hour part of the date literal is invalid or out of range.

**Action:** Check the arguments for the date conversion function.

**0xA1027 ( 659495) stERR_ABORT_INVALID_MINUTE Invalid minutes**

**Cause:** The minutes part of the date literal is invalid or out of range.

**Action:** Check the arguments for the date conversion function.

**0xA1028 ( 659496) stERR_ABORT_INVALID_SECOND Invalid seconds**

**Cause:** The seconds part of the date literal is invalid or out of range.

**Action:** Check the arguments for the date conversion function.

**0xA1029 ( 659497) stERR_ABORT_INVALID_MICROSECOND Invalid microseconds**

**Cause:** The microseconds part of the date literal is invalid or out of range.

**Action:** Check the arguments for the date conversion function.

**0xA102B ( 659499) stERR_ABORT_INVALID_DIGEST_ALGORITHM Invalid digest
algorithm.**

**Cause:** The digest algorithm name is unknown.

**Action:** Check the second argument on the digest function.

**0xA102C ( 659500) stERR_ABORT_ARGUMENT_VALUE_OUT_OF_RANGE The argument
'\<0%d\>' is out of range.**

**Cause:** The argument value is out of range.

**Action:** Check the argument value.

**0xA102D ( 659501) stERR_ABORT_DATEDIFF_OUT_OF_RANGE_IN_SECOND The interval
between startdate and enddate exceeded 68 years.**

**Cause:** If the date field name is 'SECOND', the interval between startdate
and enddate must be less than 68 years.

**Action:** Check the values of startdate and enddate.

**0xA102E ( 659502) stERR_ABORT_DATEDIFF_OUT_OF_RANGE_IN_MICROSECOND The
interval between startdate and enddate exceeded 30 days.**

**Cause:** If the date field name is 'MICROSECOND', the interval between
startdate and enddate must be less than 30 days.

**Action:** Check the values of startdate and enddate.

**0xA102F ( 659503) stERR_ABORT_INVALID_SIZE_OF_SECOND_AND_MICROSECOND The
values of SSSSSSSS must be a number of eight digits.**

**Cause:** The values of SSSSSSSS is smaller than eight digits.

**Action:** Check the value of SSSSSSSS.

**0xA1030 ( 659504) stERR_ABORT_INVALID_CHARACTER Invalid character use**

**Cause:** An invalid character is being used.

**Action:** Verify that every character in the input string is a valid
character.

**0xA1032 ( 659506) stERR_ABORT_TRAVERSE_NOT_APPLICABLE Unable to traverse**

**Cause:** The traverse could not be executed.

**Action:** Verify that the traverse is valid.

**0xA1033 ( 659507) stERR_ABORT_INVALID_BYTE_ORDER Invalid byte order
information**

**Cause:** Byte order is invalid.

**Action:** Verify the validity of the byte order.

**0xA1034 ( 659508) stERR_ABORT_INVALID_FUNCTION_PRECISION Invalid function
precision**

**Cause:** The function precision is not valid.

**Action:** Verify the validity of the function precision.

**0xA1035 ( 659509) stERR_ABORT_INVALID_BUFFER_DISTANCE Invalid distance value
for the buffer function**

**Cause:** The distance value for the buffer function is invalid.

**Action:** Verify the validity of the distance value for the buffer function.

**0xA1036 ( 659510) stERR_ABORT_INVALID_RELATE_PATTERN Invalid pattern of the
relate function**

**Cause:** The pattern value of the relate function is invalid

**Action:** Verify that values matching '\*TF012' are set, and that the pattern
length is 9.

**0xA1037 ( 659511) stERR_ABORT_STNMR_DUMP_EMPTY_OBJECT Empty dump object.**

**Cause:** You did not specify a dump object for the dump table.

**Action:** Specify a dump object for the dump table.

**0xA1038 ( 659512) stERR_ABORT_STNMR_INVALID_DUMP_OBJECT Invalid dump object**

**Cause:** The object is not valid for the dump table.

**Action:** Use a valid dump object for the dump table.

**0xA1039 ( 659513) stERR_ABORT_OBJECT_BUFFER_OVERFLOW Object buffer overflow.**

**Cause:** Object buffer overflow.

**Action:** Use the ALTER SESSION/SYSTEM SET ST_OBJECT_BUFFER_SIZE statement or
the ST_OBJECT_BUFFER_SIZE hint to increase the object buffer size.

**0xA103A ( 659514) stERR_ABORT_OBJECT_INTEGRITY_VIOLATION Object integrity
violation.**

**Cause:** Object integrity violation.

**Action:** Verify that a valid object is being used.

**0xA103B ( 659515) stERR_ABORT_RING_POINT_COUNT_LESS_THAN_4 The ring (\<0%d\>)
has less than 4 points**

**Cause:** Object integrity violation.

**Action:** Verify that a valid object is being used.

**0xA103C ( 659516) stERR_ABORT_NOT_CLOSED_RING The ring (\<0%d\>) is not
closed.**

**Cause:** Object integrity violation.

**Action:** Verify that a valid object is being used.

**0xA103D ( 659517) stERR_ABORT_OBJECT_SIZE The size of the object is
incorrect**

**Cause:** Object integrity violation.

**Action:** Verify that a valid object is being used.

**0xA103E ( 659518) stERR_ABORT_RING_BOUND_CROSS The ring \<0%d\> and ring
\<1%d\> bounds cross**

**Cause:** Object integrity violation.

**Action:** Verify that a valid object is being used.

**0xA103F ( 659519) stERR_ABORT_POLYGON_HAS_MULTI_EXTERNAL_RING The external
ring does not include the internal ring \<0%d\>,**

**Cause:** Object integrity violation.

**Action:** Verify that a valid object is being used.

**0xA1040 ( 659520) stERR_ABORT_LINE_POINT_COUNT The point count of a line is
less than 2**

**Cause:** Object integrity violation.

**Action:** Verify that a valid object is being used.

**0xA1041 ( 659521) stERR_ABORT_LINE_POINT_SAME A line has only two points with
the same value**

**Cause:** Object integrity violation.

**Action:** Verify that a valid object is being used.

**0xA1042 ( 659522) stERR_ABORT_RING_LINE_COUNT A ring has less than three
lines**

**Cause:** Object integrity violation.

**Action:** Verify that a valid object is being used.

**0xA1043 ( 659523) stERR_ABORT_RING_ZERO_AREA The area of a ring is zero**

**Cause:** Object integrity violation.

**Action:** Verify that a valid object is being used.

**0xA1044 ( 659524) stERR_ABORT_RING_LINE_CROSS A ring has crossing lines**

**Cause:** Object integrity violation.

**Action:** Verify that a valid object is being used.

**0xA1045 ( 659525) stERR_ABORT_POLYGON_INTERSECTS A multipolygon has
intersecting polygons : (polygon:\<0%d\>, ring:\<1%d\>), (polygon:\<2%d\>,
ring:\<3%d\>)**

**Cause:** Object integrity violation.

**Action:** Verify that a valid object is being used.

**0xA1046 ( 659526) stERR_ABORT_INVALID_WKB Error parsing well-known-binary**

**Cause:** The specified well-known-binary is not correct.

**Action:** Check the well-known-binary.

**0xA1047 ( 659527) stERR_ABORT_INVALID_OBJECT_IN_GEOMCOLLECTION The type
\<0%d\> of object \<1%d\> in the geometry collection is not valid**

**Cause:** The specified well-known-binary is not correct.

**Action:** Check the well-known-binary.

**0xA1048 ( 659528) stERR_ABORT_INVALID_STORED_DATA_LENGTH The data saved in the
DBMS are not the expected length**

**Cause:** The disk page is broken or the meta table has invalid data.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0xA1049 ( 659529) stERR_ABORT_INVALID_POLYGON Invalid Polygon**

**Cause:** An attempt was made to perform an operation on an invalid polygon.

**Action:** Check the structure of the polygon and try again.

**0xA104A ( 659530) stERR_ABORT_UNKNOWN_POLYGON Unverified Polygon**

**Cause:** An attempt was made to perform an operation on a polygon that has not
been verified.

**Action:** Insert the Polygon again, or perform a validity check on the
polygon.

**0xA104B ( 659531) stERR_ABORT_UNEXPECTED_ERROR Unexpected error: \<0%s\>:
\<1%s\>**

**Cause:** This error occurs due to a logical programming error.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0xA104C ( 659532) stERR_ABORT_INVALID_POINTS Invalid combination of identical
points**

**Cause:** Two or more points in the geometry object that must have different
values have the same values.

**Action:** Ensure that the geometry object is valid.

**0xA104D ( 659533) stERR_ABORT_INVALID_GEOMETRY Invalid Geometry**

**Cause:** An attempt was made to perform an operation on an invalid geometry
object.

**Action:** Ensure that the geometry object is valid.

### IGNORE

**0xA2000 ( 663552) stERR_IGNORE_NOERROR Ignore this message.**

**Cause:** This is not an error.

**Action:** Ignore this message.

8.MM Error Code
---------------

### FATAL

**0x4000F ( 262159) mmERR_FATAL_LOAD_MSB_ERROR Unable to load the message file
\<0%s\>**

**Cause:** The system failed to find a "msb" file or open the file.

**Action:** Verify that the "msb" file is in the "msg" directory.

**0x40013 ( 262163) mmERR_FATAL_MAXHANDLE_ERROR Unable to get the maximum number
of file handles**

**Cause:** It is impossible to retrieve the maximum number of file descriptors
allowed for this system. This is an OS (system call error or library function)
error.

**Action:** Check the error number from the trace log and contact Altibase's
Support Center (http://support.altibase.com/en/).

**0x4001B ( 262171) mmERR_FATAL_SETLIMIT_ERROR Failed to invoke the setlimit()
system function**

**Cause:** An error occurred while invoking the setlimit() function. This is an
OS (system call error or library function) error.

**Action:** Check the error number from the trace log and contact Altibase's
Support Center (http://support.altibase.com/en/).

**0x4001C ( 262172) mmERR_FATAL_GETLIMIT_ERROR Failed to invoke the getlimit()
system function**

**Cause:** An error occurred while invoking the getlimit() function. This is an
OS (system call error or library function) error.

**Action:** Check the error number from the trace log and contact Altibase's
Support Center (http://support.altibase.com/en/).

**0x40028 ( 262184) mmERR_FATAL_FLOCK_INIT Failed to invoke the flock_init()
system function [\<0%s\>]**

**Cause:** The flock_init() system call failed. This is an OS (system call error
or library function) error.

**Action:** Check the error number from the trace log and contact Altibase's
Support Center (http://support.altibase.com/en/).

**0x4005B ( 262235) mmERR_FATAL_FLOCK_DESTROY Failed to invoke the
flock_destroy() system function [\<0%s\>]**

**Cause:** The flock_destroy() system call failed. This is an OS (system call
error or library function) error.

**Action:** Check the error number from the trace log and contact Altibase's
Support Center (http://support.altibase.com/en/).

**0x40029 ( 262185) mmERR_FATAL_FLOCK_TRYWRLOCK Failed to invoke the
flock_trywrlock() system function**

**Cause:** The flock_trywrlock() system call failed. This is an OS (system call
error or library function) error.

**Action:** Check the error number from the trace log and contact Altibase's
Support Center (http://support.altibase.com/en/).

**0x4005D ( 262237) mmERR_FATAL_FLOCK_WRLOCK Failed to invoke the flock_wrlock()
system function**

**Cause:** The flock_wrlock() system call failed. This is an OS (system call
error or library function) error.

**Action:** Check the error number from the trace log and contact Altibase's
Support Center (http://support.altibase.com/en/).

**0x4002A ( 262186) mmERR_FATAL_FLOCK_UNLOCK Failed to invoke the flock_unlock()
system function**

**Cause:** The flock_unlock() system call failed. This is an OS (system call
error or library function) error.

**Action:** Check the error number from the trace log and contact Altibase's
Support Center (http://support.altibase.com/en/).

**0x40052 ( 262226) mmERR_FATAL_THREAD_CONDITION_INIT Failed to invoke the
cond_init() system function**

**Cause:** The system failed to invoke cond_init(). This is an OS (system call
error or library function) error.

**Action:** Check the error number from the trace log and contact Altibase's
Support Center (http://support.altibase.com/en/).

**0x40053 ( 262227) mmERR_FATAL_THREAD_CONDITION_SIGNAL Failed to invoke the
cond_signal() system function**

**Cause:** The system failed to invoke cond_signal(). This is an OS (system call
error or library function) error.

**Action:** Check the error number from the trace log and contact Altibase's
Support Center (http://support.altibase.com/en/).

**0x40054 ( 262228) mmERR_FATAL_THREAD_CONDITION_DESTROY Failed to invoke the
cond_destroy() system function**

**Cause:** Use of invalid condition value. This is an OS (system call error or
library function) error.

**Action:** Check the error number from the trace log and contact Altibase's
Support Center (http://support.altibase.com/en/).

**0x40060 ( 262240) mmERR_FATAL_OSFileSizeLimit_ERROR The maximum file size of
the OS is less than that specified in the property. Decrease the file size
property.**

**Cause:** The maximum file size of the OS is less than that specified in the
property.

**Action:** Decrease the file size property.

**0x40068 ( 262248) mmERR_FATAL_THREAD_CONDITION_WAIT Failed to invoke the
cond_wait() system function**

**Cause:** The system failed to invoke the cond_wait() function. This is an OS
(system call error or library function) error.

**Action:** Check the error number from the trace log and contact Altibase's
Support Center (http://support.altibase.com/en/).

**0x4006A ( 262250) mmERR_FATAL_THREAD_CONDITION_BROADCAST Failed to invoke the
cond_broadcast() system function**

**Cause:** The system failed to invoke the cond_broadcast() function. This is an
OS (system call error or library function) error.

**Action:** Check the error number from the trace log and contact Altibase's
Support Center (http://support.altibase.com).

**0x4006C ( 262252) mmERR_FATAL_SOCKET_CREATE_FAILED Unable to create socket**

**Cause:** Unable to create a socket.

**Action:** Too many files are open. Change the system parameter.

**0x4006D ( 262253) mmERR_FATAL_SOCKET_BIND_FAILED Unable to bind socket**

**Cause:** Either the port is already bound or it is impossible to bind the port
due to a system limitation.

**Action:** Use another port.

**0x40085 ( 262277) mmERR_FATAL_PASSWORD_FILE_ERROR Password file open error**

**Cause:** Password file open error.

**Action:** Check your environment.

**0x400E5 ( 262373) mmERR_FATAL_MUTEX_INIT Unable to initialize a mutex.**

**Cause:** The system failed to initialize a mutex.

**Action:** Check the call stack from the trace log and contact Altibase's
Support Center (http://support.altibase.com/en/).

**0x400E6 ( 262374) mmERR_FATAL_LATCH_INIT Unable to initialize a latch.**

**Cause:** The system failed to initialize a latch.

**Action:** Check the call stack from the trace log and contact Altibase's
Support Center (http://support.altibase.com/en/).

### ABORT

**0x4102C ( 266284) mmERR_ABORT_IDN_MISMATCH_ERROR Incompatible NLS between the
client(\<0%s\>) and the server(\<1%s\>).**

**Cause:** The NLS of the client is different from the one supported by the
server.

**Action:** Use the same NLS as the server NLS.

**0x4102D ( 266285) mmERR_ABORT_NO_USER_ERROR Invalid user**

**Cause:** The user is not registered in the database.

**Action:** Use a user who is registered in the database.

**0x4102E ( 266286) mmERR_ABORT_INVALID_PASSWORD_ERROR Invalid password**

**Cause:** The password is incorrect.

**Action:** Enter the correct password for the user.

**0x41033 ( 266291) mmERR_ABORT_INVALID_ERROR Invalid communication protocol**

**Cause:** Code based on an invalid protocol has been found.

**Action:** Verify the version of library that is used by the client.

**0x41035 ( 266293) mmERR_ABORT_ALREADY_CONNECT_ERROR Already connected to a
session**

**Cause:** A new connection has been requested to an already connected session.

**Action:** Verify the client code.

**0x41039 ( 266297) mmERR_ABORT_INSUFFICIENT_QUERY_ERROR SQL statement too
short**

**Cause:** The message from the client did not appear to contain any SQL text.

**Action:** Verify the SQL statement from the client. Check the error number
from the trace log and contact Altibase’s Support Center
(http://support.altibase.com/en/).

**0x4103A ( 266298) mmERR_ABORT_INVALID_STATEMENT_STATE_ERROR Invalid statement
processing request**

**Cause:** The request was invalid for the current state of the statement.

**Action:** Check the client application.

**0x4103C ( 266300) mmERR_ABORT_INVALID_FETCH_ERROR Invalid SQL statement data
fetch request**

**Cause:** An invalid SQL statement fetch request has been detected.

**Action:** Verify the SQL statement from the client.

**0x4103F ( 266303) mmERR_ABORT_TOO_MANY_STATEMENT There are too many allocated
statements.**

**Cause:** Too many statements are allocated on this system.

**Action:** Remove unused statements or increase system resources.

**0x41040 ( 266304) mmERR_ABORT_ADMIN_MODE_ONLY Unable to provide service while
the server starts up.**

**Cause:** A request for service was made to the server while it was starting up.

**Action:** Terminate all the clients while the server starts up.

**0x41041 ( 266305) mmERR_ABORT_ADMIN_ALREADY_RUNNING Another SYSDBA session is
already running.**

**Cause:** A SYSDBA session is already running.

**Action:** Terminate the SYSDBA session process and execute it again.

**0x41043 ( 266307) mmERR_ABORT_MMC_ACCESS_MODE Invalid access privileges**

**Cause:** You do not have access privileges for the table.

**Action:** Verify that you have access privileges for the table.

**0x41047 ( 266311) mmERR_ABORT_MMC_TRANSACTION_ALREADY_ACTIVE The transaction
is already active.**

**Cause:** The transaction is already active.

**Action:** Wait until the transaction is complete.

**0x41048 ( 266312) mmERR_ABORT_MMC_CANT_SET_TRANSACTION_IN_AUTOCOMMIT_MODE The
transaction is already in auto-commit mode.**

**Cause:** The transaction is already in auto-commit mode.

**Action:** Check that the transaction is in auto-commit mode.

**0x41050 ( 266320) mmERR_ABORT_NOT_APPLICABLE Operation not applicable**

**Cause:** Operation not applicable.

**Action:** Specify a valid parameter

**0x41057 ( 266327) mmERR_ABORT_MMC_CANT_LOCK_TABLE_IN_AUTOCOMMIT_MODE Unable to
execute LOCK TABLE statement while the system is in auto-commit mode.**

**Cause:** The system tried to execute a LOCK TABLE statement while the system
was in auto-commit mode.

**Action:** When the system is in auto-commit mode, Remove the LOCK TABLE
statement.

**0x41059 ( 266329) mmERR_ABORT_NO_AVAILABLE_TASK Task pool overflow. Check
properties.**

**Cause:** There are no more available tasks for service.

**Action:** Increase the value of the MAX_CLIENT property and restart the
database.

**0x4105A ( 266330) mmERR_ABORT_OTHER_STATEMENT_REMAINS Several statements still
open**

**Cause:** There are a few opened statements.

**Action:** Close all statements and retry the statement.

**0x4105E ( 266334) mmERR_ABORT_BIND_COLUMN_COUNT_MISMATCH Mismatched bind
column count**

**Cause:** The number of host variables and the number of data items to bind to
them are different.

**Action:** Check client applications.

**0x4105F ( 266335) mmERR_ABORT_INVAILD_STACKCOUNT Invalid stack count**

**Cause:** The stack count is too big or too small.

**Action:** Set the stack count to be a positive integer less than 65536.

**0x41061 ( 266337) mmERR_ABORT_TOO_LONG_IDENTIFIER_NAME The length of the
identifier is too long**

**Cause:** Identifier too long.

**Action:** Give the identifier a shorter name.

**0x4106E ( 266350) mmERR_ABORT_ADMIN_MODE_ERROR If ADMIN_MODE is activated,
only the users SYS and SYSTEM\_ can connect to the database with SYSDBA
privileges. Verify that you have SYSDBA privileges.**

**Cause:** If ADMIN_MODE is activated, only the users SYS and SYSTEM\_ can
connect to the database with SYSDBA privileges.

**Action:** Verify that you have SYSDBA privileges.

**0x41076 ( 266358) mmERR_ABORT_MMI_NOT_IMPLEMENTED Not supported yet**

**Cause:** Not supported yet.

**Action:** Not supported yet.

**0x4107A ( 266362) mmERR_ABORT_STARTUP_PHASE_ERROR Unable to start up in the
specified phase in the current state.**

**Cause:** It is impossible to start up in the specified phase in the current
startup state.

**Action:** Check the current startup phase.

**0x4107B ( 266363) mmERR_ABORT_SHUTDOWN_MODE_ERROR Unable to shut down Altibase
using the specified mode in the current state.**

**Cause:** It is impossible to shut down the server using the specified mode in
the current state.

**Action:** Check the current startup phase.

**0x4107C ( 266364) mmERR_ABORT_INSUFFICIENT_PRIV Insufficient privileges. The
user has to connect as SYSDBA.**

**Cause:** The user has to connect as SYSDBA.

**Action:** Check your privileges.

**0x4107D ( 266365) mmERR_ABORT_CREATE_DB_ERROR Failure to CREATE DATABASE**

**Cause:** The system failed to create a database.

**Action:** Check the error message.

**0x4107E ( 266366) mmERR_ABORT_DROP_DB_ERROR Failure to DROP DATABASE**

**Cause:** The system failed to drop a database.

**Action:** Check the error message.

**0x4107F ( 266367) mmERR_ABORT_ADMIN_MODE_PRIV Failure changing to ADMIN_MODE.
Only SYS and SYSTEM\_ users can change the current mode to ADMIN_MODE.**

**Cause:** Only the SYS and SYSTEM\_ users can change the current mode to
ADMIN_MODE.

**Action:** Check the connected user.

**0x41080 ( 266368) mmERR_ABORT_SESSION_NOT_FOUND Invalid Session ID \<0%d\>**

**Cause:** It is impossible to find the session ID. Use a valid session ID.

**Action:** Verify that a session with the specified ID exists.

**0x41082 ( 266370) mmERR_ABORT_INTERNAL_SERVER_ERROR_ARG Internal server error
(\<0%s\>)**

**Cause:** The system encountered an internal server error. This is an internal
programming exception.

**Action:** Check the error number from the trace log and contact Altibase's
Support Center (http://support.altibase.com/en/).

**0x41083 ( 266371) mmERR_ABORT_NOT_UPDATE_PROPERTY A specified property does
not exist or cannot be updated.**

**Cause:** A specified property does not exist or cannot be updated.

**Action:** Check the property.

**0x41087 ( 266375) mmERR_ABORT_ADMIN_NOT_ACCEPTED Failed to connect through a
non-SYSDBA channel**

**Cause:** The user has to connect through a SYSDBA channel.

**Action:** Change the connection channel type.

**0x41088 ( 266376) mmERR_ABORT_SERVER_PHASE_MISMATCHES_QUERY_TYPE Unable to
execute the query in the current start-up phase**

**Cause:** This query cannot be executed while the server is in the current
state.

**Action:** After proceeding to a suitable startup phase, try again.

**0x41089 ( 266377) mmERR_ABORT_MMC_DATE_FORMAT_LENGTH_EXCEED The length of the
value of the DEFAULT_DATE_FORMAT property equals or exceeds the maximum length (
\<0%d\> ).**

**Cause:** DEFAULT_DATE_FORMAT string is too long.

**Action:** Execute the ALTER SESSION statement with a valid DEFAULT_DATE_FORMAT
string.

**0x4108A ( 266378) mmERR_ABORT_QUEUE_NOT_FOUND Queue not found**

**Cause:** The queue is not in the queue manager. This is an internal
programming exception.

**Action:** Check the error number from the trace log and contact Altibase's
Support Center (http://support.altibase.com/en/).

**0x4108C ( 266380) mmERR_ABORT_GETRLIMIT_ERROR Failed to invoke the getrlimit()
system function**

**Cause:** An error occurred while invoking the getrlimit() function. This is an
OS (system call error or library function) error.

**Action:** Check the error number from the trace log and contact Altibase's
Support Center (http://support.altibase.com/en/).

**0x4108D ( 266381) mmERR_ABORT_OSFileSizeLimit_ERROR The maximum file size of
the OS is less than that specified in the property. Decrease the file size
property.**

**Cause:** The maximum file size of the OS is less than that specified in the
property.

**Action:** Decrease the file size property.

**0x4108E ( 266382) mmERR_ABORT_DATABASE_NAME_LENGTH_ERROR Invalid Database Name
Length. Valid Database Name Length = 1 \~ \<0%d\>.**

**Cause:** The database name length is invalid.

**Action:** Use a database name with a valid length.

**0x4108F ( 266383) mmERR_ABORT_PAGE_RANGE_ERROR Invalid createdb initial size:
\<0%lu\> bytes. Valid size range = \<1%lu\> \~ \<2%lu\> bytes.**

**Cause:** The initial DB size specified for database creation is invalid.

**Action:** Specify an initial DB size within the valid range.

**0x41090 ( 266384) mmERR_ABORT_DATABASE_NAME_ERROR Invalid Database Name. Check
the properties and retry.**

**Cause:** Invalid database name.

**Action:** Check the properties and retry.

**0x41091 ( 266385) mmERR_ABORT_SHM_ALREADY_EXIST_ERROR Shared Memory Already
Exist. Remove Shared Memory First.**

**Cause:** Shared memory already exists.

**Action:** Remove shared memory first.

**0x41098 ( 266392) mmERR_ABORT_STATEMENT_NOT_FOUND Failure to find statement**

**Cause:** It is impossible to find the statement. Use a valid statement.

**Action:** Verify that the statement is valid.

**0x41099 ( 266393) mmERR_ABORT_TOO_MANY_SESSION There are too many sessions**

**Cause:** Too many sessions are connected to this system.

**Action:** Disconnect unused sessions or increase the MAX_CLIENT property.

**0x4109A ( 266394) mmERR_ABORT_SESSION_NOT_SPECIFIED Session is not specified
in protocol**

**Cause:** The session is not specified in the protocol. This is an internal
programming exception.

**Action:** Check the error number from the trace log and contact Altibase's
Support Center (http://support.altibase.com/en/).

**0x4109B ( 266395) mmERR_ABORT_SESSION_NOT_CONNECTED Session is not connected**

**Cause:** The session is not connected. This is an internal programming
exception.

**Action:** Check the error number from the trace log and contact Altibase's
Support Center (http://support.altibase.com).

**0x4109C ( 266396) mmERR_ABORT_INVALID_SESSION_PROPERTY Invalid session
property**

**Cause:** Invalid session property.

**Action:** Use a valid session property.

**0x4109D ( 266397) mmERR_ABORT_INVALID_EXECUTE_OPTION Invalid execute option**

**Cause:** Invalid execute option. This is an internal programming exception.

**Action:** Check the error number from the trace log and contact Altibase's
Support Center (http://support.altibase.com/en/).

**0x4109E ( 266398) mmERR_ABORT_INVALID_LOB_RANGE Invalid lob range**

**Cause:** Invalid lob range.

**Action:** Check the lob size and use a valid lob range.

**0x4109F ( 266399) mmERR_ABORT_INVALID_DATA_CONVERSION Invalid data
conversion**

**Cause:** Invalid data conversion. This is an internal programming exception.

**Action:** Check the error number from the trace log and contact Altibase's
Support Center (http://support.altibase.com/en/).

**0x410A0 ( 266400) mmERR_ABORT_INVALID_BIND_PARAMETER_NUMBER Invalid bind
parameter number**

**Cause:** Invalid number of binding parameters.

**Action:** Check the error number from the trace log and contact Altibase's
Support Center (http://support.altibase.com/en/).

**0x410A1 ( 266401) mmERR_ABORT_ADD_TASK_TIMED_OUT Add task timed out**

**Cause:** A timeout occurred while attempting to add a task. This is an
internal programming exception.

**Action:** Check the error number from the trace log and contact Altibase's
Support Center (http://support.altibase.com/en/).

**0x410A2 ( 266402) mmERR_ABORT_NUMERIC_PRECISION_OVERFLOW Numeric precision
overflow**

**Cause:** Numeric precision overflow

**Action:** Numeric precision overflow

**0x410A3 ( 266403) mmERR_ABORT_NUMERIC_SCALE_OVERFLOW Numeric scale overflow**

**Cause:** Numeric scale overflow

**Action:** Numeric scale overflow

**0x410A5 ( 266405) mmERR_ABORT_INVALID_STATEMENT_FREE_MODE Invalid statement
free mode**

**Cause:** The client set an invalid free mode for the statement. This is an
internal programming exception.

**Action:** Check the error number from the trace log and contact Altibase's
Support Center (http://support.altibase.com/en/).

**0x410A6 ( 266406) mmERR_ABORT_UNSUPPORTED_FETCHMOVE Unsupported fetch move
operation**

**Cause:** Unsupported fetch move operation. This is an internal programming
exception.

**Action:** Check the error number from the trace log and contact Altibase's
Support Center (http://support.altibase.com/en/).

**0x410D2 ( 266450) mmERR_ABORT_FETCH_OUT_OF_SEQ Fetch out of sequence.**

**Cause:** A fetch was attempted using a cursor that is no longer valid.

**Action:** Do not execute the COMMIT or ROLLBACK statement in a fetch loop.

**0x410A9 ( 266409) mmERR_ABORT_INVALID_BIND_COLUMN_NUMBER Invalid bind column
number**

**Cause:** Invalid bind column number. This is an internal programming
exception.

**Action:** Check the error number from the trace log and contact Altibase's
Support Center (http://support.altibase.com/en/).

**0x410AA ( 266410) mmERR_ABORT_INVALID_XA_OPERATION Invalid XA operation**

**Cause:** Invalid XA operation. This is an internal programming exception.

**Action:** Check the error number from the trace log and contact Altibase's
Support Center (http://support.altibase.com/en/).

**0x410AB ( 266411) mmERR_ABORT_NUMERIC_CONVERSION_OVERFLOW Numeric conversion
overflow**

**Cause:** An overflow occurred while converting the numeric data type.

**Action:** Use the correct numeric precision.

**0x410AD ( 266413) mmERR_ABORT_DATA_CONVERSION_OVERFLOW Data conversion
overflow**

**Cause:** Data conversion overflow.

**Action:** The data cannot be stored in the database as this data type.

**0x410AE ( 266414) mmERR_ABORT_INVALID_PRECISION Invalid precision or length**

**Cause:** Invalid precision or length.

**Action:** Specify a suitable precision or length.

**0x410AF ( 266415) mmERR_ABORT_PRECISION_MISMATCH Precision mismatch**

**Cause:** Precision mismatch.

**Action:** Check the error number from the trace log and contact Altibase's
Support Center (http://support.altibase.com/en/).

**0x410B0 ( 266416) mmERR_ABORT_UNSUPPORTED_NETWORK_PROTOCOL Unsupported network
protocol**

**Cause:** Unsupported network protocol.

**Action:** Use a supported network protocol.

**0x410B1 ( 266417) mmERR_ABORT_INVALID_SESSION_STATE Invalid request in current
session state**

**Cause:** The request was invalid for the current session state.

**Action:** Check the client application.

**0x410B2 ( 266418) mmERR_ABORT_TASK_ALLOC_FAILED Task allocation failed**

**Cause:** Task memory allocation failed.

**Action:** Verify that enough memory is available.

**0x410B6 ( 266422) mmERR_ABORT_DNMismatched The DNs (Distinguished Names) in
the Server and User Certificates are different.("\<0%s\>" != "\<1%s\>")**

**Cause:** The DNs (Distinguished Names) in the server and user certificates are
different.

**Action:** Check both the server and client certificates.

**0x410B7 ( 266423) mmERR_ABORT_INVALID_DATA_SIZE Invalid size of data to bind
to a host variable [ Param ID = \<0%d\>, Data Type = \<1%s\>, Data Size =
\<2%d\>, Declared Size of Host Variable = \<3%d\> ]**

**Cause:** The size of the data and the size of the host variable differ.

**Action:** Check the size of the data to be bound to the host variable.

**0x410B8 ( 266424) mmERR_ABORT_INVALID_SCALE_SIZE Invalid scale of data to bind
to a host variable [ Scale Size = \<0%d\> , Declared Scale of Host Variable =
\<1%d\> ]**

**Cause:** The scale of the data and the scale of the host variable differ.

**Action:** Check the scale of the data to be bound to the host variable.

**0x410BA ( 266426) mmERR_ABORT_NO_ALERTS_REGISTERED There are no alerts
registered.**

**Cause:** There are no alerts registered.

**Action:** Register alerts.

**0x410BC ( 266428) mmERR_ABORT_NOT_EXIST_XID A specified XID does not exist.**

**Cause:** A specified XID does not exist.

**Action:** Check the XID.

**0x410BD ( 266429) mmERR_ABORT_INVALID_XA_SESSION Do after xa_open.**

**Cause:** This session is not an XA session.

**Action:** Check the XID.

**0x410BE ( 266430) mmERR_ABORT_NOT_ASSOCIATED_BRANCH A specified XID is not
associated.**

**Cause:** A specified XID is not associated.

**Action:** Check the XID.

**0x410BF ( 266431) mmERR_ABORT_INVALID_XA_STATE State transition error
(curr:\<0%s\>).**

**Cause:** The function routine was invoked in an improper context.

**Action:** Check the function routine.

**0x410C0 ( 266432) mmERR_ABORT_XID_INUSE The specified XID is in use.**

**Cause:** The specified XID is in use.

**Action:** Check the XID.

**0x410C1 ( 266433) mmERR_ABORT_ALREADY_EXIST_XID The specified XID already
exists.**

**Cause:** The specified XID already exists.

**Action:** Check the XID.

**0x410C2 ( 266434) mmERR_ABORT_INVALID_XID Invalid XID.**

**Cause:** The specified XID does not exist.

**Action:** Check the XID.

**0x410C3 ( 266435) mmERR_ABORT_NOT_ALLOWED_DCL A DCL SQL command is not allowed
in an xa session.**

**Cause:** A DCL SQL statement is not allowed in a global transaction.

**Action:** Do not use the DCL SQL command.

**0x410C4 ( 266436) mmERR_ABORT_NOT_ALLOWED_DDL A DDL SQL command is not allowed
in an xa session.**

**Cause:** The Altibase XA application cannot execute any DDL SQL statements.

**Action:** Do not use the DDL SQL command.

**0x410C5 ( 266437) mmERR_ABORT_SERVER_ALREADY_STARTED The server is already
started.**

**Cause:** The server is already started.

**Action:** Stop the server.

**0x410C6 ( 266438) mmERR_ABORT_ATOMIC_EXECUTE_ERROR Atomic Execute Error**

**Cause:** Atomic execute error.

**Action:** Check the data or the statement.

**0x410C7 ( 266439) mmERR_ABORT_DATABASE_NAME_ASCII_ERROR Invalid Character Set
for Database Name.**

**Cause:** Invalid database name character set.

**Action:** Use an ASCII character set for the database name.

**0x410C9 ( 266441) mmERR_ABORT_REMOTE_SYSDBA_NOT_ALLOWED Remote access as
SYSDBA not allowed**

**Cause:** The REMOTE_SYSDBA_ENABLE property is set to 0.

**Action:** Set the REMOTE_SYSDBA_ENABLE property to 1.

**0x410CB ( 266443) mmERR_ABORT_MMC_NOT_SUPPORT_REPL_MODE This replication mode
is not supported at the session level.**

**Cause:** The replication modes (EAGER, ACKED, LAZY) do not pertain to
sessions.

**Action:** No action is necessary.

**0x410CC ( 266444) mmERR_ABORT_NullSourceData "NULL source data were found when
converting from MT source data to CM data.";**

**Cause:** Conversion failed because the source data received as an argument was
NULL. This is an internal error.

**Action:** Check the error number from the trace log and contact Altibase's
Support Center (http://support.altibase.com/en/).

**0x410CD ( 266445) mmERR_ABORT_InvalidMantissaLength "The mantissa length (
\<0%d\> ) of the source data exceeds the maximum mantissa length.";**

**Cause:** Conversion failed because the data type value was invalid.

**Action:** Check the error number from the trace log and contact Altibase's
Support Center (http://support.altibase.com).

**0x410CE ( 266446) mmERR_ABORT_InvalidArrayBinds "Array binding is not
permitted with SELECT statements.";**

**Cause:** An attempt was made to bind an array when executing a SELECT
statement.

**Action:** Do not attempt to bind an array when executing a SELECT statement.

**0x410CF ( 266447) mmERR_ABORT_TOO_MANY_STATEMENTS_IN_THE_SESSION There are too
many statements in the session.**

**Cause:** Too many statements have been allocated to this session.

**Action:** Change the value of the MAX_STATEMENTS_PER_SESSION property or
remove unused statements.

**0x410D0 ( 266448) mmERR_ABORT_STATEMENT_NUMBER_EXCEEDS_INPUT_VALUE The number
of allocated statements exceeds the input maximum value.**

**Cause:** The number of allocated statements exceeds the input maximum value.

**Action:** Enter a larger maximum value.

**0x410D1 ( 266449) mmERR_ABORT_TOO_LONG_PASSWORD_ERROR Password too long**

**Cause:** The input password exceeded the maximum allowable length.

**Action:** Enter a shorter password.

**0x410D3 ( 266451) mmERR_ABORT_MMC_TIMEZONE_LENGTH_EXCEED TIME_ZONE string too
long**

**Cause:** The length of the TIME_ZONE property exceeds the maximum length.

**Action:** Execute the ALTER SESSION statement with a valid TIME_ZONE string.

**0x410D4 ( 266452) mmERR_ABORT_EXCEEDS_DEDICATED_THREAD_MAX_COUNT The number of
dedicated threads exceeds the maximum limit**

**Cause:** The number of dedicated threads exceeds the maximum limit.

**Action:** Change the value of the DEDICATED_THREAD_MAX_COUNT property.

**0x410D5 ( 266453) mmERR_ABORT_FAIL_TO_ESTABLISH_CONNECTION Client unable to
establish connection.**

**Cause:** An attempt to connect as a normal user failed.

**Action:** Try to connect as sysdba.

**0x410D6 ( 266454) mmERR_ABORT_SHUTDOWN_NOT_SUPPORTED_VIA_IPC Not Supported via
IPC.**

**Cause:** Executing the command via IPC is not supported.

**Action:** Try connecting via UNIXDOMAIN. 'SHUTDOWN EXIT' can be executed via
IPC.

**0x410D8 ( 266456) mmERR_ABORT_DBMS_NOT_FOUND DB not found : \<0%s\>**

**Cause:** The specified database does not exist.

**Action:** Verify that the specified database exists.

**0x410DD ( 266461) mmERR_ABORT_EXCEEDS_MAX_SESSION The number of generable
sessions is set at a larger value than the maximum value of MAX_CLIENT.**

**Cause:** The number of generable sessions is set at a larger value than the
maximum value of MAX_CLIENT.

**Action:** Decrease the value of the JOB_THREAD_COUNT or the MAX_CLIENT
property.

**0x410E3 ( 266467) mmERR_ABORT_DISABLED_TCP_USER The user cannot connect using
TCP.**

**Cause:** This user cannot connect using TCP.

**Action:** Please connect using SSL/UNIX domain/IPC. JAVA users can change the
connection method in the application (for iSQL, change the value of the
iSQL_CONNECTION environment variable).

**0x410E4 ( 266468) mmERR_ABORT_GET_IPV6_INFO Failed to get IPV6 infomation.**

**Cause:** Failed to get IPv6 information.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x410E7 ( 266471) mmERR_ABORT_VALUE_LENGTH_EXCEED The length of the value set
for \<0%s\> exceeds the limit ( \<1%d\> ).**

**Cause:** Input value is too long.

**Action:** Verify that the length of the input value does not exceed the limit.

**0x410E8 ( 266472) mmERR_ABORT_InvalidProcedure The ARRAY INSERT statement
cannot be used with a SELECT statement that returns a ResultSet in stored
procedures**

**Cause:** The stored procedure contains both the ARRAY INSERT statement and a
SELECT statement that returns a ResultSet.

**Action:** Verify that the stored procedure does not contain both the ARRAY
INSERT statement and a SELECT statement that returns a ResultSet.

**0x410E9 ( 266473) mmERR_ABORT_IP_ACL_DENIED Connection is not permitted by the
ACCESS_LIST: \<0%s\>**

**Cause:** ACCESS_LIST is set DENY.

**Action:** Check and modify to PERMIT on the ACCESS_LIST.

**0x410EA ( 266474) mmERR_ABORT_INVALID_DATA_TYPE Invalid type of data to bind
to a host variable [ Param ID = \<0%d\>, Data Type = \<1%d\> ]**

**Cause:** The data type to be bound is not valid.

**Action:** Check the error number from the trace log and contact Altibase's
Support Center (http://support.altibase.com/en/).

**0x410EB ( 266475) mmERR_ABORT_NO_SESSION_TO_CLOSE The session to close cannot
be found.**

**Cause:** No session to close exists anymore.

**Action:** Ascertain ID, user, and status of the session in V\$SESSION.

**0x410EC ( 266476) mmERR_ABORT_CANNOT_CLOSE_SELF_SESSION The self-accessed
session cannot be closed.**

**Cause:** Closing the session is impossible since it is currently being
accessed.

**Action:** Re-close the session after identifying the session ID.

**0x410ED ( 266477) mmERR_ABORT_SESSION_CLOSE_NOT_PERMITTED Failed to close the
session(s). Permission denied.**

**Cause:** The authority for closing a session is the responsibility of SYS
user.

**Action:** Login as SYS user then close the session.

**0x410EE ( 266478) mmERR_ABORT_INVALID_ACCESS_LIST_FILE Failed to open or close
the access list file : \<0%s\> - \<1%s\>.**

**Cause:** The ACCESS_LIST_FILE property is led to an invalid file.

**Action:**

\# - 1. Check to verify whether the file ACCESS_LIST_FILE property leads exists
or not.

\# - 2. Check the error number in the trace log file.

**0x410EF ( 266479) mmERR_ABORT_EXCEEDED_ACCESS_LIST_COUNT_LIMIT The access list
file has items exceeding the maximum limit.**

**Cause:** The number of items in the access list file exceed the maximum limit
which is 1024.

**Action:** Reduce the number of access list items to be less than the maximum
limit.

**0x410F0 ( 266480) mmERR_ABORT_RELOAD_ACL_NOT_PERMITTED Failed to reload the
access list.**

**Cause:** The ACCESS_LIST_FILE property is omitted or disabled.

**Action:** Enable the ACCESS_LIST_FILE property and reboot the DBMS.

**0x410F1 ( 266481) mmERR_ABORT_INVALID_ACCESS_LIST_VALUE The value of
ACCESS_LIST is not acceptable : (Line \<0%d\>) \<1%s\>**

\#\*Cause: The data in the access list file is not compatible with the specified
ACCESS_LIST format.

\#\*Action: Modify the data to comply with the ACCESS_LIST format.

**0x410F2 ( 266482) mmERR_ABORT_INVALID_SNAPSHOT_SCN This is a snapshot SCN
which cannot execute SELECT.**

**Cause:** SCN cannot execute SELECT through a snapshot if SCN has been changed
\# by a DDL occurred on a relevant table or iLoader is executed by creating a
new \# table after starting the snapshot.

**Action:** Re-start the snapshot(ALTER DATABASE BEGIN SNAPSHOT;) after
terminating the snapshot currently running(ALTER DATABASE END SNAPSHOT;).

**0x410F3 ( 266483) mmERR_ABORT_INVALID_BEGIN_SNAPSHOT Snapshot cannot be
started since an iLoader session exists.**

**Cause:** An iLoader session exists. Snapshot is unable to run since it might
affect the existing iLoader session.

**Action:** Terminate the current iLoader session, and then re-start to start
the snapshot.

**0x410F4 ( 266484) mmERR_ABORT_INVALID_SNAPSHOT_THRESHOLD Snapshot cannot be
working since the database exceeds maximum threshold value.**

**Cause:** Snapshot cannot be able to run since the capacity of memory or disk
undo space has exceeded the maximum threshold value.

**Action:** Adjust the property value of SNAPSHOT_MEM_THRESHOLD,
SNAPSHOT_DISK_UNDO_THRESHOLD after checking the amount of memory use and undo
space in V\$SNAPSHOT to secure space for the maximum threshold value.

**0x410F5 ( 266485) mmERR_ABORT_BEGIN_SNAPSHOT Snapshot has already been being
started.**

**Cause:** There should be no snapshot being executed in order to start the
snapshot.

**Action:** Re-start (ALTER DATABASE BEGIN SNAPSHOT;)the snapshot after
terminating(ALTER DATABASE END SNAPSHOT;) the snapshot which is currently
running.

**0x410F6 ( 266486) mmERR_ABORT_END_SNAPSHOT Snapshot has been ended.**

**Cause:** Snapshot has already been ended.

**Action:** Retry after executing the statement ALTER DATABASE END SNAPSHOT.

**0x410F7 ( 266487) mmERR_ABORT_INVALID_WORKING_SNAPSHOT Snapshot does not
work.**

**Cause:** Snapshot is not running. The snapshot should be started in order for
it to work.

**Action:** Retry after executing the snapshot(ALTER DATABASE BEGIN SNAPSHOT;).

**0x410F8 ( 266488) mmERR_ABORT_IPCDA_MESSAGE_TOO_LONG The message size exceeds
the maximum IPCDA buffer size(\<0%d\>).**

**Cause:** The size of message to send exceeds the maximum size of IPCDA buffer.

**Action:** Use another connection type.

**0x410F9 ( 266489) mmERR_ABORT_IPCDA_UNSUPPORTED_QUEUE Unsupported IPCDA for
queue.**

**Cause:** The queue(enqueue/dequeue) is not supported in IPCDA.

**Action:** Set another communication protocols. Altibase supports the following
communication besides IPCDA ; TCP/IP, Unix Domain Socket, IPC using Shared
Memory, SSL/TLS.

**0x410FA ( 266490) mmERR_ABORT_SESSION_WITH_INVALID_SMN The shard meta
number(SMN) is invalid.: [ Session SMN=\<0%lu\>, Data Node SMN=\<1%lu\>,
Disconnect=\<2%s\>, Protocol=\<3%s\> ]**

**Cause:** The shard meta number(SMN) of the data node is greater than the SMN
of the session.

**Action:** Reconnect to the meta node.

**0x410FB ( 266491) mmERR_ABORT_PLAN_CACHE_INVALID_SQL_TEXT_ID SQLTextID must be
a number of at least five digits. (SQLTextID = \<0%s\>)**

**Cause:** SQLTextID does not match the format that you can enter.

**Action:** SQLTextID must be a number of at least five digits.

**0x410FC ( 266492) mmERR_ABORT_PLAN_CACHE_NOT_FOUND_SQL_TEXT_ID SQLTextID not
found. (SQLTextID = \<0%s\>)**

**Cause:** The SQLTextID does not exist.

**Action:** Check whether SQLTextID exists in V\$SQL_PLAN_CACHE_SQLTEXT.

### IGNORE

**0x42000 ( 270336) mmERR_IGNORE_NO_ERROR No main module error**

**Cause:** This is not an error.

**Action:** Ignore this error message.

**0x420A4 ( 270500) mmERR_IGNORE_NO_COLUMN No column**

**Cause:** There was no column in the specified statement.

**Action:** Ignore this error message.

**0x420A7 ( 270503) mmERR_IGNORE_NO_CURSOR No cursor**

**Cause:** There was no cursor in the specified statement.

**Action:** Ignore this error message.

**0x420A8 ( 270504) mmERR_IGNORE_NO_PARAMETER No parameter**

**Cause:** There was no parameter in the specified statement.

**Action:** Ignore this error message.

**0x420AC ( 270508) mmERR_IGNORE_UNABLE_TO_MAKE_LISTENER Unable to make
listener**

**Cause:** Unable to make listener.

**Action:** Ignore this error message.

**0x420DB ( 270555) mmERR_IGNORE_UNSUPPORTED_PROPERTY Unsupported property :
[\<0%d\>].**

**Cause:** Unsupported property was used.

**Action:** Upgrade the server to the latest version.

**0x420DE ( 270558) mmERR_IGNORE_ONLY_SYSDBA_CANDOTHAT Only sysdba can do
that.**

**Cause:** Tried to change a property that only sysdba can change.

**Action:** Login as sysdba and try again.

**0x420DF ( 270559) mmERR_IGNORE_THREAD_COUNT_UNCHANGED Maximum number of
threads cannot be changed to smaller value.**

**Cause:** Tried to set the number of threads to a value lower than the current
value.

**Action:** Do not attempt to set the threads to a value lower than the current
value.

**0x420E1 ( 270561) mmERR_IGNORE_PASSWORD_GRACE_PERIOD The password will expire
within \<0%d\> day(s).**

**Cause:** The password expiration date is approaching.

**Action:** Change your password.

9.ODBC Error Code
-----------------

### FATAL

**0x5000C ( 327692) ulERR_FATAL_MEMORY_ALLOC_ERROR Memory allocation error.
\<0%s\>.**

**Cause:** Memory space has been exhausted.

**Action:** Reduce the amount of memory being used by the client application.

**0x50032 ( 327730) ulERR_FATAL_FAIL_TO_ESTABLISH_CONNECTION Client unable to
establish connection.**

**Cause:** The driver was unable to establish a connection with the data source.

**Action:** Check the connection information.

**0x50047 ( 327751) ulERR_FATAL_MEMORY_MANAGEMENT_ERROR Memory management error
\<0%s\>**

**Cause:** Memory has been corrupted.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x50137 ( 327991) ulERR_FATAL_LOB_NOT_OPENED Memory management error. An
attempt was made to execute an operation on a LOB locator that was not open.
Possible memory corruption in \<0%s\>.**

**Cause:** The state of the ulnLob structure was not ULN_LOB_ST_OPENED while
attempting to execute an operation on the ulnLob.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x50139 ( 327993) ulERR_FATAL_LOB_INVALID_STATE Memory management error. The
LOB function should not be called in this state. Possible memory corruption in
\<0%s\>.**

**Cause:** Failed to call the LOB function using a handle.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

### ABORT

**0x51001 ( 331777) ulERR_ABORT_idnSetDefaultFactoryError No idn Default Factory
found.**

**Cause:** No character set was found.

**Action:** Change the NLS_USE property.

**0x51002 ( 331778) ulERR_ABORT_INVALID_HANDLE Invalid Handle.**

**Cause:** A handle is invalid.

**Action:** Check if the handle is SQL_NULL_HANDLE or NULL.

**0x5100F ( 331791) ulERR_ABORT_DateTime_Field_Overflow_Error Datetime field
overflow. \<0%s\>.**

**Cause:** Invalid datetime data was used.

**Action:** Check the data type range.

**0x51010 ( 331792) ulERR_ABORT_Invalid_Datatime_Format_Error Invalid datetime
format.**

**Cause:** The datetime data format is invalid.

**Action:** Check the datetime format.

**0x51012 ( 331794) ulERR_ABORT_Ignored_Option_Error This option is ignored.**

**Cause:** An unsupported property was used.

**Action:** Check the property value.

**0x51013 ( 331795) ulERR_ABORT_OPTIONAL_FEATURE_NOT_IMPLEMENTED This optional
feature is not implemented.**

**Cause:** An unsupported property was used.

**Action:** Check the property value.

**0x51014 ( 331796) ulERR_ABORT_FUNCTION_SEQUENCE_ERR Function sequence error.**

**Cause:** The function call sequence is out of order.

**Action:** Refer to the state transition table.

**0x51015 ( 331797) ulERR_ABORT_INVALID_ATTRIBUTE_VALUE Invalid attribute
value.**

**Cause:** Invalid attribute value.

**Action:** Check if the value you provided is valid for specified attribute.

**0x51016 ( 331798) ulERR_ABORT_INVALID_ATTR_OPTION Invalid attribute/option
identifier : \<0%d\>.**

**Cause:** The attribute or option identifier was invalid.

**Action:** Check the attribute ID or option value.

**0x51018 ( 331800) ulERR_ABORT_INVALID_APP_BUFFER_TYPE Invalid application
buffer type : \<0%d\>.**

**Cause:** The application buffer type was invalid.

**Action:** Check the host variable type in the application.

**0x51019 ( 331801) ulERR_ABORT_INVALID_DESCRIPTOR_INDEX Invalid descriptor
index : \<0%d\>.**

**Cause:** The value specified for the ParameterNumber argument was less than 1,
or the value specified for ColumnNumber was greater than the number of columns
in the result set.

**Action:** Check the ParameterNumber argument.

**0x5101A ( 331802) ulERR_ABORT_INVALID_PARAM_TYPE Invalid parameter type :
\<0%d\>.**

**Cause:** The value specified for the InputOutputType argument was invalid.

**Action:** Check the InputOutputType argument.

**0x5101B ( 331803) ulERR_ABORT_RESTRICTED_DATATYPE_VIOLATION Restricted data
type attribute violation. SQL_C_TYPE \<0%d\> and SQL_TYPE \<1%d\> cannot be
interconverted.**

**Cause:** The data type identified by the ValueType argument cannot be
converted to the data type identified by the ParameterType argument.

**Action:** Check the ValueType and ParameterType attributes.

**0x5101C ( 331804) ulERR_ABORT_INVALID_USE_OF_NULL_POINTER Invalid use of null
pointer.**

**Cause:** Invalid use of null pointer.

**Action:** Check the value pointer and value length.

**0x5101D ( 331805) ulERR_ABORT_INVALID_BUFFER_LEN Invalid string or buffer
length : \<0%d\>.**

**Cause:** The value in BufferLength was less than 0 or greater than the
property size.

**Action:** Check the host variable.

**0x5101F ( 331807) ulpERR_ABORT_COMP_No_End_Declare_Section_Error EXEC SQL END
DECLARE SECTION does not exist.**

**Cause:** The EXEC SQL END DECLARE SECTION does not exist.

**Action:** Check the EXEC SQL END DECLARE SECTION.

**0x51020 ( 331808) ulERR_ABORT_Invalid_StrLen_IndPtr_Error Invalid string
length.**

**Cause:** The value in BufferLength was less than 0 or greater than the
property value.

**Action:** Check the host variable.

**0x51026 ( 331814) ulERR_ABORT_INVALID_CONN_TYPE_ERROR Invalid connection type
: (\<0%d\>).**

**Cause:** Invalid connection type.

**Action:** Check the value of the CONNTYPE keyword.

**0x5102E ( 331822) ulERR_ABORT_INVALID_CURSOR_STATE Invalid cursor state.**

**Cause:** A cursor was opened on the StatementHandle, and an invalid function
was called.

**Action:** Check the function sequence.

**0x5102F ( 331823) ulERR_ABORT_Unable_DirectExecute_Array_Error Unable to
execute SQLExecDirect using array-binding.**

**Cause:** Array binding is not used when executing SQLExecDirect.

**Action:** Check array binding when SQLExecDirect executes.

**0x51034 ( 331828) ulERR_ABORT_INVALID_SQL_TYPE Invalid SQL data type :
\<0%d\>.**

**Cause:** The value specified for the InfoType argument was not valid for the
ODBC version supported by the driver.

**Action:** Check the InfoType argument.

**0x51035 ( 331829) ulERR_ABORT_CONNECTION_NAME_IN_USE Connection name in use.**

**Cause:** The specified ConnectionHandle has already been used to establish a
connection, and the connection is still open.

**Action:** Check the ConnectionHandle argument.

**0x51036 ( 331830) ulERR_ABORT_NO_CONNECTION Connection does not exist.**

**Cause:** The connection specified in the ConnectionHandle argument is not
open.

**Action:** Check the ConnectionHandle argument.

**0x5103A ( 331834) ulERR_ABORT_INVALID_TRANSACTION_OPCODE Invalid transaction
operation code.**

**Cause:** The value specified for the CompletionType argument was neither
SQL_COMMIT nor SQL_ROLLBACK.

**Action:** Check the CompletionType argument.

**0x51040 ( 331840) ulERR_ABORT_WRONG_FETCH_TYPE Fetch type out of range.**

**Cause:** Invalid FetchOrientation.

**Action:** Check the FetchOrientation value.

**0x51041 ( 331841) ulERR_ABORT_INDICATOR_REQUIRED_BUT_NOT_SUPPLIED_ERR
Indicator variable required but not supplied.**

**Cause:** NULL data was bound to an output parameter for which
StrLen_or_IndPtr, set in SQLBindParameter, was a null pointer.

**Action:** Set the StrLen_or_IndPtr argument in SQLBindParameter.

**0x51043 ( 331843) ulERR_ABORT_COMMUNICATION_LINK_FAILURE Communication link
failure. \<0%s\>**

**Cause:** Communication link failure.

**Action:** Check the detailed error message following this error message.

**0x51044 ( 331844) ulERR_ABORT_Data_Value_Overflow_Error \<0%s\> value out of
range.**

**Cause:** The value is out of range.

**Action:** Check the value.

**0x5104B ( 331851) ulERR_ABORT_Invalid_Cursor_Position_Error Invalid cursor
position.**

**Cause:** The cursor position is within the range of an invalid rowset. Either
the row has been deleted or the rowset has not been fetched.

**Action:** Check that the cursor value is within the range of a fetched rowset.

**0x5104C ( 331852) ulERR_ABORT_ROW_VALUE_OUT_OF_RANGE_ERR Row value out of
range.**

**Cause:** Row value out of range.

**Action:** Verify that the row value is correct.

**0x5104D ( 331853) ulERR_ABORT_CONNECTION_TIME_OUT Connection timeout.**

**Cause:** Connection timeout.

**Action:** Increase CONNECTION_TIMEOUT value or tune the query.

**0x5104E ( 331854) ulERR_ABORT_CM_CALLBACK_NOT_EXIST Communication module
callback function does not exist.**

**Cause:** The communication module version and CLI version are not compatible.

**Action:** Contact Altibase's Support Center (http://support.altibase.com).

**0x5104F ( 331855) ulERR_ABORT_CM_GENERAL_ERROR Communication link failure. CM
ErrorCode : 0x\<0%x\>, System errno : \<1%d\>**

**Cause:** Communication module error.

**Action:** Check the system error number and take appropriate action.

**0x51051 ( 331857) ulERR_ABORT_PARAMETER_NOT_BOUND Some parameters were not
bound.**

**Cause:** Some parameters were not bound.

**Action:** Check whether all the parameters were bound.

**0x51052 ( 331858) ulERR_ABORT_UNHANDLED_MT_TYPE An unhandled server data type
(\<0%d\>) has been received.**

**Cause:** Received an invalid server data type.

**Action:** Check whether the server data type is supported.

**0x51056 ( 331862) ulERR_ABORT_INVALID_USE_OF_IMP_DESC Invalid use of an
automatically allocated descriptor handle.**

**Cause:** An attempt was made to manipulate a descriptor handle allocated by
the driver.

**Action:** Check the coding, and check that the proper syntax was used.

**0x51057 ( 331863) ulERR_ABORT_STMT_HAVE_NO_RESULT_SET The prepared statement
is not a cursor specification.**

**Cause:** Since the statement associated with the statement handle did not
return a result set, there was no column to describe.

**Action:** Check that the executed query returns a result set.

**0x51059 ( 331865) ulERR_ABORT_INVALID_TRANSACTION_STATE Invalid transaction
state.**

**Cause:** Failed to execute the command.

**Action:** Check the transaction status.

**0x5105E ( 331870) ulERR_ABORT_ATTRIBUTE_CANNOT_BE_SET_NOW Attribute cannot be
set now.**

**Cause:** Failed to set the attribute.

**Action:** Check the function call sequence.

**0x5105F ( 331871) ulERR_ABORT_FUNCTION_TYPE_OUT_OF_RANGE Function type out of
range.**

**Cause:** Invalid function type.

**Action:** Check the function type.

**0x51062 ( 331874) ulERR_ABORT_CONNTYPE_NOT_SUPPORTED Invalid attribute Value**

CONNTYPE \<0%d\> is currently not supported.

**Cause:** Invalid CONNTYPE.

**Action:** Check CONNTYPE.

**0x51067 ( 331879) ulERR_ABORT_PORT_NO_ALTIBASE_PORT_NO_NOT_SET Neither PORT_NO
in the connection string nor the ALTIBASE_PORT_NO environment variable has been
set.**

**Cause:** A port has not been set.

**Action:** Set the port with a connection string or the ALTIBASE_PORT_NO
environment variable.

**0x51068 ( 331880) ulERR_ABORT_ALTIBASE_HOME_NOT_SET The ALTIBASE_HOME
environment variable must be set before trying to connect to the Altibase server
through a UNIX domain.**

**Cause:** The ALTIBASE_HOME environment variable has not been set.

**Action:** Refer to the manual and set the ALTIBASE_HOME environment variable.

**0x5106C ( 331884) ulERR_ABORT_INVALID_INFO_TYPE Invalid information type.
SQLGetInfo does not know the InfoType \<0%d\>.**

**Cause:** Invalid InfoType.

**Action:** Verify that InfoType is valid.

**0x5106D ( 331885) ulERR_ABORT_READONLY_DESCRIPTOR_FIELD Invalid descriptor
field identifier : \<0%d\>. The descriptor field is read-only.**

**Cause:** An attempt was made to change a read-only descriptor field.

**Action:** Check the coding, and check that the proper syntax was used.

**0x5106E ( 331886) ulERR_ABORT_INVALID_ALTIBASE_PORT_NO Connection string does
not have PORT_NO, and environment variable ALTIBASE_PORT_NO does not have a
valid value : \<0%s\>.**

**Cause:** The connection type is TCP, but the connection string does not
specify a PORT_NO. In addition, the environment variable ALTIBASE_PORT_NO is not
valid.

**Action:** Set the ALTIBASE_PORT_NO environment variable correctly. Or specify
PORT_NO in the connection string.

**0x51070 ( 331888) ulERR_ABORT_UNHANDLED_MT_TYPE_BINDINFO \<0%s\> : There is
missing case in Bindinfo build table, where CTYPE = \<1%d\>, MTYPE = \<2%d\>.**

**Cause:** Internal error.

**Action:** Contact Altibase’s Support Center (http://support.altibase.com).

**0x51071 ( 331889) ulERR_ABORT_RESTRICTED_DATATYPE_VIOLATION_BOOKMARK
Restricted data type attribute violation. The ColumnNumber argument was 0, but
the TargetType argument was not SQL_C_BOOKMARK or SQL_C_VARBOOKMARK.**

**Cause:** The ColumnNumber argument was 0, but the TargetType argument was not
SQL_C_BOOKMARK or SQL_C_VARBOOKMARK.

**Action:** Check the TargetType argument value.

**0x51072 ( 331890) ulERR_ABORT_NUMERIC_VALUE_OUT_OF_RANGE Numeric value out of
range.**

**Cause:** The numeric value is out of range.

**Action:** Check the numeric value.

**0x51073 ( 331891) ulERR_ABORT_INVALID_DESC_FIELD_IDENTIFIER Invalid descriptor
field identifier : \<0%d\>.**

**Cause:** An invalid descriptor field ID was used.

**Action:** Check the descriptor field ID.

**0x51075 ( 331893) ulERR_ABORT_INVALID_NUMERIC_LITERAL Invalid character value
for cast specification.**

**Cause:** A data value that cannot be converted has been input.

**Action:** Check the data type and input value.

**0x51076 ( 331894) ulERR_ABORT_INVALID_CONVERSION Restricted data type
attribute violation. SQL_TYPE cannot be converted to SQL_C_TYPE as requested.**

**Cause:** SQL_TYPE cannot be converted to SQL_C_TYPE as requested.

**Action:** Refer to the CLI User's manual to convert to a supported type.

**0x51077 ( 331895) ulERR_ABORT_NUMERIC_VALUE_OUT_OF_RANGE_MINUS Numeric value
out of range. The bound data type is unsigned but the fetched data is less than
zero.**

**Cause:** The numeric value is less than zero.

**Action:** Check the numeric value.

**0x51209 ( 332297) ulERR_ABORT_NUMERIC_PRECISION_OUT_OF_RANGE Numeric value out
of range. The value exceeded the numeric precision range of
SQL_NUMERIC_STRUCT.**

**Cause:** The value exceeded the numeric precision range of SQL_NUMERIC_STRUCT.

**Action:** Change the value or increase the precision.

**0x51078 ( 331896) ulERR_ABORT_NUMERIC_SCALE_OUT_OF_RANGE Numeric value out of
range. The value exceeded the numeric scale range of SQL_NUMERIC_STRUCT.**

**Cause:** The value exceeded the numeric scale range of SQL_NUMERIC_STRUCT.

**Action:** Use a value within the numeric scale range of SQL_NUMERIC_STRUCT.

**0x5107A ( 331898) ulERR_ABORT_INVALID_CURSOR_POSITION_GD Invalid cursor
position. The cursor position was AFTER END or BEFORE START.**

**Cause:** The cursor position was AFTER END or BEFORE START.

**Action:** Use SQLFetch or SQLFetchScroll to move to a valid cursor position.

**0x5107B ( 331899) ulERR_ABORT_BIT_VALUE_OUT_OF_RANGE Numeric value out of
range. SQL_C_BIT can only have the value 0 or 1.**

**Cause:** Invalid BIT value.

**Action:** Enter either 0 or 1.

**0x5107C ( 331900) ulERR_ABORT_BINARY_SIZE_NOT_MATCH Numeric value out of
range. SQL_C_BINARY data length does not match the size of the SQL data type.**

**Cause:** SQL_C_BINARY data length does not match the size of the SQL data
type.

**Action:** Check whether the data lengths match.

**0x5107D ( 331901) ulERR_ABORT_CANNOT_INSERT_INTERVAL Restricted data type
attribute violation. The interval type is only for fetch operations. Interval
type columns cannot be created, nor can values be inserted into interval type
columns.**

**Cause:** The interval type was used.

**Action:** Use another data type.

**0x51081 ( 331905) ulERR_ABORT_STRING_LENGTH_TOO_LONG Invalid attribute value.
The string is too long to be used as an attribute value.**

**Cause:** Invalid attribute value.

**Action:** Check the length of the provided string.

**0x51083 ( 331907) ulERR_ABORT_INCONSISTENT_NIBBLE_PRECISION_AND_BUFFER_SIZE
Invalid parameter value. The SQL_NIBBLE data structure precision field value
exceeds the specified buffer size.**

**Cause:** Invalid nibble structure precision.

**Action:** Specify an appropriate precision value for the nibble.

**0x51084 ( 331908) ulERR_ABORT_INCONSISTENT_BIT_PRECISION_AND_BUFFER_SIZE
Invalid parameter value. The SQL_BIT data structure precision field value
exceeds the specified buffer size.**

**Cause:** Invalid SQL_BIT structure precision.

**Action:** Specify an appropriate precision value for the SQL_BIT.

**0x51085 ( 331909) ulERR_ABORT_CANNOT_MODIFY_IRD Cannot modify an
implementation row descriptor.**

**Cause:** An attempt was made to modify an implementation row descriptor.

**Action:** Check the coding, and check that the proper syntax was used.

**0x51086 ( 331910) ulERR_ABORT_FETCH_OFFSET_OUT_OF_RANGE Fetch offset is too
big or too small.**

**Cause:** A scrollable cursor was used outside the FetchOffset range.

**Action:** When using a scrollable cursor, use it within the FetchOffset range.

**0x51088 ( 331912) ulERR_ABORT_INVALID_ARRAY_SIZE Invalid array size. Decrease
the array size.**

**Cause:** Invalid array size.

**Action:** Decrease the array size.

**0x51089 ( 331913) ulERR_ABORT_CONVERT_CHARSET_FAILED Failed to convert charset
: source charset id = \<0%d\>, target charset id = \<1%d\>, source index =
\<2%d\>, target index = \<3%d\>**

**Cause:** Failed to encode the string.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x5108A ( 331914) ulERR_ABORT_ADMIN_ALREADY_RUNNING Another SYSDBA session is
already running.**

**Cause:** A SYSDBA session is already running.

**Action:** Terminate the SYSDBA session process and execute it again.

**0x5108B ( 331915) ulERR_ABORT_INCOMPATIBLE_PROPERTY Incompatible property :
[\<0%s\>]. Upgrade server.**

**Cause:** Incompatible property was used.

**Action:** Upgrade the server to the latest version.

**0x5108D ( 331917) ulERR_ABORT_INVALID_CONNECTION_STR_FORM Invalid connection
string format: \<0%d\> : [\<1%c\>]**

**Cause:** The connection string format is invalid.

**Action:** Check the connection string. If it has exceeded the maximum allowed
length. a question mark is output.

**0x51097 ( 331927) ulERR_ABORT_INVALID_DATE_STRING Invalid string: [\<0%s\>]
for date format: [\<1%s\>]**

**Cause:** The input data does not match the date format.

**Action:** Ensure that the input value matches the date format.

**0x51098 ( 331928) ulERR_ABORT_INVALID_NUMBER_STRING Invalid string for number:
[\<0%s\>]**

**Cause:** The input string cannot be converted to a number.

**Action:** Check the input string.

**0x5111C ( 332060) ulERR_ABORT_PD_ATTRIBUTE_CANNOT_BE_SET_NOW This attribute
cannot be set now. You can not call SQLPutData() with StrLen_or_Ind set to
SQL_NULL_DATA after one or more previous calls to SQLPutData() for the same
parameter have been returned.**

**Cause:** SQL_NULL_DATA was used for SQLPutData().

**Action:** Enter data other than SQL_NULL_DATA for SQLPutData().

**0x5111D ( 332061) ulERR_ABORT_PD_DATA_TOO_BIG The SQL_CHAR or SQL_VARCHAR data
type cannot be bigger than 32KB.**

**Cause:** The SQL_CHAR or SQL_VARCHARSQL_CHAR data type cannot accept a value
larger than 32KB.

**Action:** Enter a value smaller than 32KB for the SQL_CHAR or
SQL_VARCHARSQL_CHAR data type. If the value is larger than 32KB, divide the
value and input several times.

**0x5111F ( 332063) ulERR_ABORT_PD_FIXED_DATA_NOT_ALLOWD_IN_PIECES Non-character
and non-binary data sent in pieces.**

**Cause:** An attempt was made to send non-variable data (non-CHAR, BINARY data)
in pieces.

**Action:** Send non-variable data in one piece.

**0x5112C ( 332076) ulERR_ABORT_LOB_AUTOCOMMIT_MODE_ERR The connection is in
autocommit mode. One cannot operate on LOB data in autocommit mode.**

**Cause:** An attempt to execute a LOB operation was made while the connection
is in autocommit mode.

**Action:** Turn off autocommit mode.

**0x5112D ( 332077) ulERR_ABORT_LOB_FILE_WRITE_ERR Failed to write LOB data to
the file.**

**Cause:** Failed to write LOB data to the file.

**Action:** Check whether the file path is valid and whether a file can be
written.

**0x5112E ( 332078) ulERR_ABORT_LOB_FILE_READ_ERR Failed to read from a file.**

**Cause:** Failed to read the file.

**Action:** Check whether the file path is valid and whether the file can be
read.

**0x5112F ( 332079) ulERR_ABORT_FILE_OPEN Failed to open file : \<0%s\>.**

**Cause:** Failed to open the file.

**Action:** Check whether the file path is valid and whether the file can be
read.

**0x51130 ( 332080) ulERR_ABORT_FILE_EXIST The file \<0%s\> already exists.**

**Cause:** The file already exists.

**Action:** Delete the file, or use the SQL_FILE_OVERWRITE or SQL_FILE_APPEND
option.

**0x51131 ( 332081) ulERR_ABORT_FILE_CLOSE Failed to close file : \<0%s\>.**

**Cause:** Failed to close the file.

**Action:** Check the operating system error number.

**0x51132 ( 332082) ulERR_ABORT_GET_FILE_SIZE Failed to get the file size:
\<0%s\>.**

**Cause:** Failed to retrieve file information due to an operating system error.

**Action:** Check the operating system error number.

**0x51133 ( 332083) ulERR_ABORT_UNKNOWN_FILE_OPTION Unknown file option
\<0%d\>.**

**Cause:** An invalid file option was used.

**Action:** Use a valid file options (SQL_FILE_CREATE, SQL_FILE_OVERWRITE,
SQL_FILE_APPEND, SQL_FILE_READ)

**0x51138 ( 332088) ulERR_ABORT_INVALID_FILE_OPTION Invalid fileoption
\<0%d\>.**

**Cause:** The specified file option is invalid. For instance, you may have
specified SQL_FILE_CREATE while you intended to send the contents of a file to
the Altibase server.

**Action:** Use a valid file options (SQL_FILE_CREATE, SQL_FILE_OVERWRITE,
SQL_FILE_APPEND, SQL_FILE_READ).

**0x5113A ( 332090) ulERR_ABORT_FILE_SIZE_TOO_BIG General error. The size of the
provided file \<0%s\> is too big. The maximum file size is about 4,294,967,295 bytes *4GB-1byte)**

**Cause:** The file is too big.

**Action:** Check the file size and use a smaller file

**0x5113C ( 332092) ulERR_ABORT_INVALID_APP_BUFFER_TYPE_LOB Invalid application
buffer type : type id \<0%d\> cannot be used as a LOB source buffer.**

**Cause:** An invalid buffer type was used.

**Action:** Check the buffer type.

**0x5113E ( 332094) ulERR_ABORT_VALIDATE_INVALID_LENGTH Invalid data value**

**Cause:** The value of the data exceeds the logical value scope.

**Action:** Check the data value.

**0x5113F ( 332095) ulERR_ABORT_INVALID_CHARACTER Invalid character use.**

**Cause:** An invalid character is being used.

**Action:** Verify that every character in the input string is a valid
character.

**0x51140 ( 332096) ulERR_ABORT_INVALID_LOB_RANGE Invalid lob range**

**Cause:** Invalid lob range

**Action:** Check the lob size and use a valid lob range.

**0x51190 ( 332176) ulERR_ABORT_FAILOVER_SUCCESS FailOver Success**

**Cause:** Session FailOver Success

**Action:** Re-execute application logic.

**0x51191 ( 332177) ulERR_ABORT_INVALID_ALTERNATE_SERVER_HOST The IP/Host value
used in AlternateServers connection attribute is invalid: \<0%s\>**

**Cause:** The IP/Host value used in the AlternateServers connection attribute
is invalid.

**Action:** Make sure the IP/Host value used in the AlternateServers connection
attribute is valid.

**0x51192 ( 332178) ulERR_ABORT_GETADDRINFO_ERROR The call to getaddrinfo()
failed. The host name or service may be unknown.**

**Cause:** The host name or service may be unknown.

**Action:** Check the host name.

**0x51193 ( 332179) ulERR_ABORT_CONNECT_INVALIDARG Invalid connect() argument.**

**Cause:** An argument for the connect() function was invalid.

**Action:** Check the IP and host name.

**0x51194 ( 332180) ulERR_ABORT_INVALID_ALTERNATE_SERVER_FORMAT The value of
AlternateServers connection attribute is invalid: \<0%s\>**

**Cause:** The value of AlternateServers connection attribute does not comply
with the specified format.

**Action:** Make sure the value of AlternateServers connection attribute
complies with the specified format.

**0x51195 ( 332181) ulERR_ABORT_INVALID_ALTERNATE_SERVER_PORT The port values
used in AlternateServers connection attribute are invalid: \<0%s\>**

**Cause:** The port values used in the AlternateServers connection attribute are
not numbers or out of available range.

**Action:** Make sure the port values used in the AlternateServers connection
attribute are valid.

**0x511F5 ( 332277) ulERR_ABORT_ACS_INSUFFICIENT_BUFFER_SIZE Insufficient buffer
size ( \<0%d\> ). Recommended size is more than ( \<1%d\> ).**

**Cause:** There was insufficient buffer size for the geometry object.

**Action:** Increase the buffer size.

**0x511F6 ( 332278) ulERR_ABORT_ACS_INVALID_BYTE_ORDER Invalid byte order**

**Cause:** The byte order is invalid.

**Action:** Set the byte order information correctly.

**0x511F7 ( 332279) ulERR_ABORT_ACS_INVALID_DATA_TYPE Invalid geometry
sub-type**

**Cause:** The geometry sub-type is invalid.

**Action:** Set the geometry sub-type information correctly.

**0x511F8 ( 332280) ulERR_ABORT_ACS_INVALID_PARAMETER_RANGE Invalid parameter
value.**

**Cause:** A parameter value was invalid.

**Action:** Check the parameter value.

**0x511F9 ( 332281) ulERR_ABORT_ACS_INVALID_GEOMETRY Invalid geometry value.**

**Cause:** A geometry value was invalid.

**Action:** Check the geometry value.

**0x511FA ( 332282) ulERR_ABORT_ACS_INVALID_GEOMETRY_BYTEORDER Invalid geometry
byte order.**

**Cause:** The geometry byte order was invalid.

**Action:** Check the geometry byte order and consider calling
ACSAdjustByteOrder.

**0x511FB ( 332283) ulERR_ABORT_ACS_NOT_APPLICABLE_GEOMETRY_TYPE Inapplicable
geometry type**

**Cause:** The geometry type is not applicable.

**Action:** Check the geometry type.

**0x511FC ( 332284) ulERR_ABORT_ACS_INVALID_WKB Error parsing
well-known-binary**

**Cause:** The specified well-known-binary is not correct.

**Action:** Check the well-known-binary.

**0x511FD ( 332285) ulERR_ABORT_UNSUPPORTED_FUNCTION Unsupported function.**

**Cause:** This function is not supported.

**Action:** Do not use this function.

**0x511FE ( 332286) ulERR_ABORT_INVALID_USE_OF_BIND_TYPE Invalid use of bind
type: \<0%d\>.**

**Cause:** The specified bind type has not been defined.

**Action:** Check the list of defined bind types and try again.

**0x511FF ( 332287) ulERR_ABORT_INVALID_USE_OF_FIELD_TYPE Invalid use of field
type: \<0%d\>.**

**Cause:** The specified field type has not been defined.

**Action:** Check the field type.

**0x51200 ( 332288) ulERR_ABORT_TOO_MANY_STATEMENT There are too many allocated
statements.**

**Cause:** Too many statements are allocated.

**Action:** Remove unused statements.

**0x5120A ( 332298) ulERR_ABORT_INVALID_INDICATOR Invalid indicator value.**

**Cause:** The indicator value was invalid.

**Action:** Initialize the indicator value.

**0x5120B ( 332299) ulERR_ABORT_FAIL_OBTAIN_ERROR_INFORMATION failed to obtain
error information.**

**Cause:** Failed to obtain error information.

**Action:** Contact Altibase’s Support Center (http://support.altibase.com/en/).

**0x51201 ( 332289) ulERR_ABORT_INVALID_BOOKMARK_VALUE Invalid bookmark value**

**Cause:** FetchOrientation is SQL_FETCH_BOOKMARK, but the
SQL_ATTR_FETCH_BOOKMARK_PTR value is NULL or invalid.

**Action:** Check your application.

**0x51204 ( 332292) ulERR_ABORT_RESTRICTED_DATATYPE_VIOLATION_BOOKMARK_TYPE
Restricted data type attribute violation**

**Cause:** Column 0 is bound with SQL_C_BOOKMARK when SQL_ATTR_USE_BOOKMARKS
value is SQL_UB_VARIABLE, or is bound with SQL_C_VARBOOKMARK when
SQL_ATTR_USE_BOOKMARKS value is not SQL_UB_VARIABLE.

**Action:** Set SQL_ATTR_USE_BOOKMARKS to SQL_UB_VARIABLE when binding Column 0
with SQL_C_VARBOOKMARK, or to SQL_UB_FIXED otherwise.

**0x51205 ( 332293) ulERR_ABORT_PROGRAM_TYPE_OUT_OF_RANGE Data type in program
out of range**

**Cause:** ColumnNumber argument is 0 and TargetType does not match bookmark
setting.

**Action:** Use SQL_C_VARBOOKMARK for a variable bookmark, or SQL_C_BOOKMARK for
a static bookmark.

**0x51207 ( 332295) ulERR_ABORT_CURSOR_OP_CONFLICT Cursor operation conflict**

**Cause:** The target rows for the UPDATE or DELETE operation could not be
found, or have already been updated or deleted.

**Action:** Refetch before executing UPDATE or DELETE, and do not execute UPDATE
or DELETE on deleted rows.

**0x51208 ( 332296) ulERR_ABORT_DOES_NOT_MATCH_COLUMN_LIST Type and number of
columns in derived table does not match column list**

**Cause:** The column on which to perform the operation could not be found.

**Action:** Check if the column is unbound, read-only, or if the
length/indicator value is SQL_COLUMN_IGNORE.

**0x5120C ( 332300) ulERR_ABORT_SSL_OPERATION_FAILURE SSL operation failure.
\<0%s\>**

**Cause:** SSL operation failure.

**Action:** Check the detailed error and take appropriate action.

**0x5120D ( 332301) ulERR_ABORT_SSL_LIBRARY_ERROR Failed to load the OpenSSL
library - \<0%s\>**

**Cause:** Failed to open the library or load functions from the library.

**Action:** Check whether or not the library has been installed and set
properly.

**0x5120E ( 332302) ulERR_ABORT_SSL_LINK_FAILURE SSL link failure. \<0%s\>**

**Cause:** SSL link failure.

**Action:** Check the detailed error code and take appropriate action.

**0x5121D ( 332317) ulERR_ABORT_INVALID_ALTIBASE_SSL_PORT_NO Connection string
does not have PORT_NO, and environment variable ALTIBASE_SSL_PORT_NO does not
have a valid value : \<0%s\>.**

**Cause:** The connection type is SSL, but the connection string does not
specify a PORT_NO. Further, the environment variable ALTIBASE_SSL_PORT_NO is not
valid.

**Action:** Set the ALTIBASE_SSL_PORT_NO environment variable correctly. Or
specify PORT_NO in the connection string.

**0x5121E ( 332318) ulERR_ABORT_PORT_NO_ALTIBASE_SSL_PORT_NO_NOT_SET Neither
PORT_NO in the connection string nor the ALTIBASE_SSL_PORT_NO environment
variable has been set.**

**Cause:** A port has not been set.

**Action:** Set the port with a connection string or the ALTIBASE_SSL_PORT_NO
environment variable.

**0x51210 ( 332304) ulERR_ABORT_IPCDA_MESSAGE_TOO_LONG Exceeding message size
for maximum size of IPCDA buffer(\<0%d\>).**

**Cause:** The message to convey exceeds the maximum size of IPCDA buffer.

**Action:** Use another connection type.

**0x51211 ( 332305) ulERR_ABORT_IPCDA_UNSUPPORTED_FUNCTION Unsupported function
for IPCDA.**

**Cause:** The function is not supported in IPCDA.

**Action:** Use another connection type.

**0x51212 ( 332306) ulERR_ABORT_IPCDA_UNSUPPORTED_SQL_DATA_TYPE Unsupported SQL
data type(\<0%d\>) for IPCDA.**

**Cause:** Unsupported SQL data type in IPCDA was used.

**Action:** Use another connection type.

**0x51213 ( 332307) ulERR_ABORT_IPCDA_UNSUPPORTED_C_DATA_TYPE Unsupported C data
type(\<0%d\>) for IPCDA.**

**Cause:** Unsupported C data type in IPCDA was used.

**Action:** Use another connection type.

\# For Shard

**0x51214 ( 332308) ulERR_ABORT_SHARD_ERROR The \<0%s\> of client-side sharding
failed due to the following reason: \<1%s\>**

**Cause:** The operation of client-side sharding is invalid.

**Action:** Take an appropriate measure for the error.

**0x51215 ( 332309) ulERR_ABORT_SHARD_CLI_ERROR The \<0%s\> of client-side
sharding failed.: \<1%s\>**

**Cause:** The operation of shard data node failed.

**Action:** Take an appropriate measure for the error.

**0x51216 ( 332310) ulERR_ABORT_SHARD_NODE_FAIL_RETRY_AVAILABLE The connection
of shard data node operation failed.**

**Cause:** The connection of shard data node failed.

**Action:** Retry PREPARE if re-connection of shard data node is required.

**0x51217 ( 332311) ulERR_ABORT_SHARD_NODE_INVALID_TOUCH This is an invalid
transaction performing on multiple nodes.(The previous access
node[\<0%s\>,\<1%s\>:\<2%d\>], the current access
node[\<3%s\>,\<4%s\>:\<5%d\>])**

**Cause:** Each transaction is performed only on a single shard data node.

**Action:** Complete the transaction being currently executed.

**0x51218 ( 332312) ulERR_ABORT_SHARD_VERSION_MISMATCH Mismatched Shard
version.**

**Cause:** The shard versions of server and client do not correspond.

**Action:** Use the identical shard and client versions.

**0x51219 ( 332313) ulERR_ABORT_SHARD_DATA_NODE_CONNECTION_FAILURE \<0%s\>**

**Cause:** An error occurred during the data node connection.

**Action:** Take appropriate measures after verifying the data node and error
number.

**0x5121A ( 332314) ulERR_ABORT_INVALID_ALTIBASE_IB_PORT_NO Connection string
does not have PORT_NO, and environment variable ALTIBASE_IB_PORT_NO does not
have a valid value : \<0%s\>.**

**Cause:** The connection type is IB, but the connection string does not specify
a PORT_NO. Further, the environment variable ALTIBASE_IB_PORT_NO is not valid.

**Action:** Set the ALTIBASE_IB_PORT_NO environment variable correctly. Or
specify PORT_NO in the connection string.

**0x5121B ( 332315) ulERR_ABORT_PORT_NO_ALTIBASE_IB_PORT_NO_NOT_SET Neither
PORT_NO in the connection string nor the ALTIBASE_IB_PORT_NO environment
variable has been set.**

**Cause:** A port has not been set.

**Action:** Set the port with a connection string or the ALTIBASE_IB_PORT_NO
environment variable.

**0x5121C ( 332316) ulERR_ABORT_IB_RCONNECT_INVALIDARG Invalid rconnect()
argument.**

**Cause:** An argument for the rconnect() function was invalid.

**Action:** Check the IP and host name.

### IGNORE

**0x52000 ( 335872) ulERR_IGNORE_NO_ERROR Success**

**Cause:** This is not an error.

**Action:** You can ignore this error message.

**0x52011 ( 335889) ulERR_IGNORE_OPTION_VALUE_CHANGED Option value changed.
\<0%s\>.**

**Cause:** The set option value has been changed.

**Action:** Check the option value.

**0x52027 ( 335911) ulERR_IGNORE_RIGHT_TRUNCATED String data right-truncated.**

**Cause:** The buffer was not large enough to return the entire string.

**Action:** Check the buffer size.

**0x52046 ( 335942) ulERR_IGNORE_FRACTIONAL_TRUNCATION Fractional truncation.**

**Cause:** The data returned for an input/output or output parameter was
truncated.

**Action:** Contact Altibase’s Support Center (http://support.altibase.com/en/).

**0x52063 ( 335971) ulERR_IGNORE_CONNECTION_STR_IGNORED Connection string pair
[\<0%s\> = {\<1%s\>};] ignored.**

**Cause:** The connection string keyword is invalid or has no value.

**Action:** Check the keyword or value.

**0x5206F ( 335983) ulERR_IGNORE_FETCH_BEFORE_RESULTSET A fetch attempt made
before the result set returned the first rowset.**

**Cause:** A fetch was attempted before the result set returned the first
rowset.

**Action:** You may safely ignore this error.

**0x52087 ( 336007) ulERR_IGNORE_VALUE_TOO_BIG The value is too big to fit in
the parameter variable.**

**Cause:** The rowcount value exceeds the out parameter maximum value.

**Action:** You may safely ignore this error.

**0x5208C ( 336012) ulERR_IGNORE_PASSWORD_GRACE_PERIOD The password will expire
within \<0%d\> day(s).**

**Cause:** The password expiration date is approaching.

**Action:** Change your password.

**0x52202 ( 336386) ulERR_IGNORE_HOLE_DETECTED Delete or update hole detected**

**Cause:** A row in the result table is missing or changed.

**Action:** Check the indicator variable and handle the hole accordingly.

**0x52203 ( 336387) ulERR_IGNORE_HOLE_DETECTED_BUT_NO_INDICATOR Hole detected
but no indicator variable provided**

**Cause:** A hole was found in the result table, but no row status indicator
variable was provided.

**Action:** Set row-status indicator variables.

**0x52206 ( 336390) ulERR_IGNORE_ERROR_IN_ROW Error(s) in row(s)**

**Cause:** One or more rows could not be processed.

**Action:** Check the error information.

**0x5220F (336399) ulERR_IGNORE_CANNOT_BE_PREFETCHED_ASYNC Synchronous prefetch
is executed since the asynchronous prefetch failed.**

**Cause:** Other statement is performing asynchronous prefetch.

**Action:** Retry asynchronous prefetch after closing the cursor of statement.

10.APRE Error Code
------------------

### ABORT

**0x51000 ( 331776) ulpERR_ABORT_FILE_OPEN_ERROR Failed to open file: \<0%s\>,
errno=\<1%d\>**

**Cause:** Failed to open the file.

**Action:** Check the file path is valid and the client application has enough
privileges.

**0x51001 ( 331777) ulpERR_ABORT_COMP_Invaild_File_Size FileSize (\<0%s\>) is
zero.**

**Cause:** The file size is zero.

**Action:** Check the file.

**0x51002 ( 331778) ulpERR_ABORT_FILE_NOT_FOUND File not found: \<0%s\>**

**Cause:** File or directory does not exist.

**Action:** Check the path or create file or change the code.

**0x51003 ( 331779) ulpERR_ABORT_FILE_DELETE_ERROR Failed to delete file:
\<0%s\>, errno=\<1%u\>**

**Cause:** Failed to delete the file.

**Action:** Check the file path is valid and the client application has enough
privileges.

**0x51004 ( 331780) ulpERR_ABORT_Memory_Alloc_Error Memory allocation error.**

**Cause:** Memory is full or process heap corruption occurred.

**Action:** If this error occurs on the client, reduce the amount of memory
being used by the client application. If this error occurs on the server, verify
that there is enough memory.

**0x51005 ( 331781) ulpERR_ABORT_Latch_Init_Error Latch initialize error.
(\<1%s\>:\<0%d\> )**

**Cause:** The system encountered an internal server error.

**Action:** Contact Altibase’s Support Center (http://support.altibase.com/en/).

**0x51006 ( 331782) ulpERR_ABORT_Latch_Read_Error Latch read error.
(\<1%s\>:\<0%d\> )**

**Cause:** The system encountered an internal server error.

**Action:** Contact Altibase’s Support Center (http://support.altibase.com/en/).

**0x51007 ( 331783) ulpERR_ABORT_Latch_Release_Error Latch release error.
(\<1%s\>:\<0%d\> )**

**Cause:** The system encountered an internal server error.

**Action:** Contact Altibase’s Support Center (http://support.altibase.com/en/).

**0x51008 ( 331784) ulpERR_ABORT_Latch_Write_Error Latch write error.
(\<1%s\>:\<0%d\> )**

**Cause:** The system encountered an internal server error.

**Action:** Contact Altibase’s Support Center (http://support.altibase.com/en/).

**0x51009 ( 331785) ulpERR_ABORT_Latch_Destroy_Error Latch destroy error.
(\<1%s\>:\<0%d\>)**

**Cause:** The system encountered an internal server error.

**Action:** Contact Altibase’s Support Center (http://support.altibase.com/en/).

**0x5100A ( 331786) ulpERR_ABORT_FILE_CLOSE_ERROR Failed to close file: \<0%s\>,
errno=\<1%d\>**

**Cause:** Failed to close the file.

**Action:** Check the operating system error number.

**0x5100B ( 331787) ulpERR_ABORT_FILE_WRITE_ERROR Failed to write file: \<0%s\>,
errno=\<1%u\>**

**Cause:** Failed to write the file.

**Action:** Check the file path is valid and the client application has enough
privileges.

**0x5100C ( 331788) ulpERR_ABORT_COMP_C_Comment_No_Close_Error C-type comment is
not closed.**

**Cause:** C-type Comment is not closed.

**Action:** Close C-type Comment.

**0x5100D ( 331789) ulpERR_ABORT_COMP_C_Unknown_Structname_Error The structure
name [\<0%s\>] is unknown.**

**Cause:** The structure name is unknown.

**Action:** Change the structure name.

**0x5100E ( 331790) ulpERR_ABORT_COMP_C_Duplicate_Structname_Error The structure
name [\<0%s\>] is a duplicate.**

**Cause:** The structure name is the same as an existing name.

**Action:** Change the structure name.

**0x5100F ( 331791) ulpERR_ABORT_COMP_C_Add_Symbol_Error The symbol name
[\<0%s\>] cannot be added to the symbol table.**

**Cause:** The symbol name cannot be added to the symbol table.

**Action:** Check the name of the symbol.

**0x51010 ( 331792) ulpERR_ABORT_COMP_C_Exceed_Max_Id_Length_Error The symbol
name exceeds the maximum length: \<0%s\>**

**Cause:** The symbol name is too long. Maximum length is 1023.**Action:**
Change the symbol name to a shorter name.

**0x51011 ( 331793) ulpERR_ABORT_COMP_Symbol_Redefinition_Error Redefinition of
'\<0%s\>'.**

**Cause:** The symbol has already been defined.

**Action:** Change the symbol name.

**0x51012 ( 331794) ulpERR_ABORT_COMP_Type_Not_Exist_Error Unknown type
'\<0%s\>'.**

**Cause:** The type is unknown.

**Action:** Use a known type.

**0x51013 ( 331795) ulpERR_ABORT_COMP_Invalid_Scope_Depth_Error Invalid scope
depth: \<0%d\>**

**Cause:** Braces are nested too deeply. Maximum depth is 100.**Action:** Remove
some braces to reduce the depth of nesting.

**0x51014 ( 331796) ulpERR_ABORT_COMP_Brace_Count_Error Inconsistent brace
count.**

**Cause:** The number of opening braces does not match the number of closing
braces.

**Action:** Check the number of opening and closing braces.

**0x51015 ( 331797) ulpERR_ABORT_COMP_Paren_Count_Error Inconsistent parenthesis
count error.**

**Cause:** The number of opening parentheses does not match the number of
closing parentheses.

**Action:** Check the number of opening and closing parentheses and try again.

**0x51016 ( 331798) ulpERR_ABORT_COMP_Exceed_Max_Nested_Struct_Depth_Error The
nested structure exceeds the maximum possible depth.**

**Cause:** The nested structure exceeds the maximum possible depth(100).

**Action:** Decrease the depth of the nested structure.

**0x51017 ( 331799) ulpERR_ABORT_COMP_Varchar_In_IncludeFile_Error VARCHAR
declarations are not permitted in \#include files.**

**Cause:** A varchar declaration was used in an \#include file.

**Action:** Remove the varchar declaration from the \#include file. Consider
using EXEC SQL INCLUDE instead.

**0x5101E ( 331806) ulpERR_ABORT_COMP_Emsqlstmt_Exist_in_CIncludefile_Error The
C include file can't contain embedded SQL statements.**

**Cause:** The C include file can't contain embedded SQL statements.

**Action:** Delete the embedded SQL statement.

**0x5101F ( 331807) ulpERR_ABORT_COMP_No_End_Declare_Section_Error EXEC SQL END
DECLARE SECTION does not exist.**

**Cause:** The EXEC SQL END DECLARE SECTION does not exist.

**Action:** Check the EXEC SQL END DECLARE SECTION.

**0x51020 ( 331808) ulpERR_ABORT_COMP_No_Begin_Declare_Section_Error EXEC SQL
BEGIN DECLARE SECTION does not exist.**

**Cause:** The EXEC SQL BEGIN DECLARE SECTION does not exist.

**Action:** Check the EXEC SQL BEGIN DECLARE SECTION.

**0x51021 ( 331809) ulpERR_ABORT_COMP_No_End_Arg_Section_Error EXEC SQL END
ARGUMENT SECTION does not exist.**

**Cause:** The EXEC SQL BEGIN ARGUMENT SECTION does not exist.

**Action:** Check the EXEC SQL BEGIN ARGUMENT SECTION.

**0x51022 ( 331810) ulpERR_ABORT_COMP_No_Begin_Arg_Section_Error EXEC SQL BEGIN
ARGUMENT SECTION does not exist.**

**Cause:** The EXEC SQL BEGIN ARGUMENT SECTION does not exist.

**Action:** Check the EXEC SQL BEGIN ARGUMENT SECTION.

**0x51023 ( 331811) ulpERR_ABORT_COMP_Unterminated_String_Error Unterminated
string error.**

**Cause:** Unterminated string.

**Action:** Check that there is no unterminated string.

**0x51024 ( 331812) ulpERR_ABORT_COMP_Exceed_Max_Connname_Error Connection name
[\<0%s\>] is too long. (max length is 50)**

**Cause:** The connection name is too long.

**Action:** Check the connection name.

**0x51025 ( 331813) ulpERR_ABORT_COMP_Exceed_Max_Cursorname_Error Cursor name
[\<0%s\>] is too long. (max length is 50)**

**Cause:** The cursor name is too long.

**Action:** Check the cursor name.

**0x51026 ( 331814) ulpERR_ABORT_COMP_Exceed_Max_Stmtname_Error Statement name
[\<0%s\>] is too long. (max length is 50)**

**Cause:** The statement name is too long.

**Action:** Check the statement name.

**0x51027 ( 331815) ulpERR_ABORT_COMP_FOR_iternum_Error The number of FOR loop
iterations must be greater than zero.**

**Cause:** The number of FOR loop iterations was zero.

**Action:** Ensure that the number of "for" iterations is greater than zero.

**0x51028 ( 331816) ulpERR_ABORT_COMP_Unknown_Hostvar_Error The host variable
[\<0%s\>] is unknown.**

**Cause:** The host variable is unknown.

**Action:** Ensure that the host variable has been declared.

**0x51029 ( 331817) ulpERR_ABORT_COMP_Lob_Locator_Error The host variable in a
FREE LOB statement must be a LOB locator.**

**Cause:** The variable was not a LOB locator.

**Action:** Check the type of the host variable.

**0x5102A ( 331818) ulpERR_ABORT_COMP_Unterminated_EMString_Error Unterminated
embedded SQL statement.**

**Cause:** Unterminated embedded SQL statement.

**Action:** Ensure that the embedded SQL statement ends with a semicolon (';').

**0x5102B ( 331819) ulERR_ABORT_Connection_String_Null_Pointer_Error A
connection string cannot be a null pointer.**

**Cause:** The connection string is null.

**Action:** Set the connection string appropriately.

**0x5102C ( 331820) ulERR_ABORT_Invaild_Connection_String_Attribute_Error
Invalid connection string attribute.**

**Cause:** Invalid connection string attribute.

**Action:** Check the connection string attribute.

**0x4102B ( 266283) mmERR_ABORT_PROTOCOL_VER_MISMATCH_ERROR Protocol version
incompatibility between the client and the server.**

**Cause:** The client protocol version is different from the server protocol
version.

**Action:** Verify the client protocol and use a client that is compatible with
the server protocol.

**0x4102C ( 266284) mmERR_ABORT_IDN_MISMATCH_ERROR Incompatible NLS between the
client(\<0%s\>) and the server(\<1%s\>).**

**Cause:** The NLS of the client is different from the one supported by the
server.

**Action:** Use the same NLS as the server NLS.

**0x5102B ( 331819) ulpERR_ABORT_COMP_Wrong_IndicatorType_Error The indicator
variable [\<0%s\>] should be of type SQLLEN or a compatible type.**

**Cause:** The indicator variable data type is not compatible with SQLLEN.

**Action:** Change the indicator variable data type to SQLLEN or INT.

**0x5102C ( 331820) ulpERR_ABORT_COMP_Repeat_Array_Struct_Error Two or more
arrays of structures are bound to host variables in the same statement.**

**Cause:** Only one array of structures can be bound to a host variable in a
single statement.

**Action:** Bind only one array of structures to a host variable in one
statement.

**0x5102D ( 331821) ulpERR_ABORT_COMP_Invalid_Indicator_Usage_Error A host
variable that is an array of structures cannot be associated with an
indicator.**

**Cause:** A host variable that is an array of structures is associated with an
indicator.

**Action:** Remove the indicator.

**0x51032 ( 331826) ulpERR_ABORT_COMP_Unknown_Macro_Overflow_Error An unknown
macro is too long. (\>4k)**

**Cause:** A macro is too long.

**Action:** Shorten the macro so it is within the allowable size.

**0x51033 ( 331827) ulpERR_ABORT_COMP_IF_Macro_Syntax_Error Macro \#if statement
syntax error.**

**Cause:** The syntax of an \#if statement in a macro is incorrect.

**Action:** Check the syntax of the \#if statement in the macro.

**0x51034 ( 331828) ulpERR_ABORT_COMP_ELIF_Macro_Syntax_Error Macro \#elif
statement syntax error.**

**Cause:** The syntax of an \#elif statement in a macro is incorrect.

**Action:** Check the syntax of the \#elif statement in the macro.

**0x51035 ( 331829) ulpERR_ABORT_COMP_ELIF_Macro_Sequence_Error Macro \#elif
statement sequence error.**

**Cause:** The position of an \#elif statement in a macro is incorrect.

**Action:** Check the position of the \#elif statement in the macro.

**0x51036 ( 331830) ulpERR_ABORT_COMP_ELSE_Macro_Sequence_Error Macro \#else
statement sequence error.**

**Cause:** The position of an \#else statement in a macro is incorrect.

**Action:** Check the position of the \#else statement in the macro.

**0x51037 ( 331831) ulpERR_ABORT_COMP_ENDIF_Macro_Sequence_Error Macro \#endif
statement sequence error.**

**Cause:** The position of an \#endif statement in a macro is incorrect.

**Action:** Check the position of the \#endif statement in the macro.

**0x51038 ( 331832) ulpERR_ABORT_PREPROC_If_Empty_Char_Constant_Error An empty
char constant cannot be used with an \#if macro expression.**

**Cause:** An empty char constant was used with an \#if macro expression.

**Action:** Do not use an empty char constant with an \#if macro expression.

**0x51039 ( 331833) ulpERR_ABORT_COMP_Include_Depth_Too_Large_Error Include
files are nested too deeply. (maximum \<0%s\>)**

**Cause:** Include files are nested too deeply within other include files.

**Action:** Do not nest include files more than \<0%s\> levels deep.

**0x5103A ( 331834) ulpERR_ABORT_COMP_NO_ENDIF_Macro_Error No \#endif error.**

**Cause:** An \#if statement was used in a macro without an \#endif statement.

**Action:** Remove the \#if statement from the macro or add an \#endif statement
to the macro.

**0x5103B ( 331835) ulpERR_ABORT_COMP_DEFINE_FUNC_NOBRACE_Error A closing
parenthesis ')' is missing from the macro parameter list.**

**Cause:** A closing parenthesis ')' is missing from the macro parameter list.

**Action:** Add a closing parenthesis ')' to the macro parameter list.

**0x5103C ( 331836) ulpERR_ABORT_COMP_DEFINE_Unknown_Macro_Error Unknown macro
name, or missing parenthesis after macro name. ( \<0%s\> )**

**Cause:** The name of a macro is unknown, or a closing parenthesis is missing
after a macro name.

**Action:** Check the macro name and declaration syntax.

**0x5103D ( 331837) ulpERR_ABORT_COMP_DEFINE_FUNC_Unterminated_String_Error
Unterminated string error.**

**Cause:** A string does not have a terminating character.

**Action:** Check that the string has been properly terminated.

**0x5103E ( 331838) ulpERR_ABORT_COMP_Define_Macro_Overflow_Error The content of
a \#define macro is too long. (\>32k)**

**Cause:** The content of a \#define macro is too long.

**Action:** Check the \#define macro and shorten it.

**0x51046 ( 331846) ulpERR_ABORT_COMP_Option_Duplicated_Error \<0%s\> option is
repeated.**

**Cause:** A preprocessing command-line option was specified more than once.

**Action:** Check the preprocessing command-line option.

**0x51047 ( 331847) ulpERR_ABORT_COMP_Option_String_Overflow_Error Option string
\<0%s\> is too long.**

**Cause:** An option string was too long.

**Action:** Check the preprocessing command-line options.

**0x51049 ( 331849) ulpERR_ABORT_COMP_Invalid_Input_fileName_Error Input file
must be a form of '\*.sc'.**

**Cause:** The preprocessing filename extension was invalid.

**Action:** Check the preprocessing file name.

**0x5104A ( 331850) ulpERR_ABORT_Unknown_Stmttype_Error Unknown embedded SQL
statement type.**

**Cause:** Unknown embedded SQL statement.

**Action:** Check the embedded SQL statement.

**0x51054 ( 331860) ulpERR_ABORT_COMP_Not_Supported_WITH_RETURN_Error WITH
RETURN option is not supported yet.**

**Cause:** The WITH RETURN option is currently unsupported.

**Action:** Do not use this function.

**0x51055 ( 331861) ulpERR_ABORT_COMP_Not_Supported_READ_ONLY_Error READ ONLY
option is not supported yet.**

**Cause:** The READ ONLY option is currently unsupported.

**Action:** Do not use this function.

**0x51056 ( 331862) ulpERR_ABORT_COMP_Not_Supported_ALTER_COMPACT_Error ALTER
COMPACT option is not supported yet.**

**Cause:** The ALTER COMPACT option is currently unsupported

**Action:** Do not use this function.

**0x5105A ( 331866) ulpERR_ABORT_Conn_Not_Exist_Error The connection does not
exist. (Name:\<0%s\>)**

**Cause:** The server connection was released.

**Action:** Check the connection with the server.

**0x5105B ( 331867) ulpERR_ABORT_Conn_Aleady_Exist_Error The connection already
exists. (Name:\<0%s\>)**

**Cause:** The connection with the server already exists.

**Action:** Check the connection with the server.

**0x5105D ( 331869) utERR_ABORT_Conn_First_Trial_Failed Failed first connection
attempt.**

**Cause:** The first server connection attempt failed.

**Action:** Check the server connection information.

**0x5105E ( 331870) ulpERR_ABORT_Conn_Second_Trial_Failed Failed second
connection attempt.**

**Cause:** The second server connection attempt failed.

**Action:** Check the server connection information.

**0x5105F ( 331871) ulERR_ABORT_Disconn_Xa_Error Cannot connect or disconnect in
a XA Env.**

**Cause:** Altibase Embedded SQL applications cannot invoke connect or
disconnect in an XA environment.

**Action:** Do not use EXEC SQL CONNECT, DISCONNECT statements in an X/Open DTP
environment.

**0x51060 ( 331872) ulpERR_ABORT_Conflict_Two_Emsqls_Error Two embedded SQL
statements conflict with each other in a multithreaded environment.**

**Cause:** Replication failed because two or more embedded statements were
executed simultaneously.

**Action:** Check replication handling in the multithreaded program.

**0x51061 ( 331873) ulpERR_ABORT_Stmt_Not_Exist_Error The statement does not
exist. (Name:\<0%s\>)**

**Cause:** The statement does not exist.

**Action:** Check the statement syntax.

**0x51062 ( 331874) ulpERR_ABORT_Stmt_Need_Prepare_4Execute_Error The statement
must be prepared for execution. (Name:\<0%s\>)**

**Cause:** The statement is not ready.

**Action:** Check the statement syntax.

**0x51063 ( 331875) ulpERR_ABORT_Cursor_Not_Exist_Error The cursor does not
exist. (Name:\<0%s\>)**

**Cause:** The statement does not exist.

**Action:** Check the statement syntax.

**0x51064 ( 331876) ulpERR_ABORT_Cursor_Need_Declare_4Open_Error The cursor must
be declared to be opened. (Name:\<0%s\>)**

**Cause:** The cursor conditions are not valid.

**Action:** Check the cursor conditions.

**0x51067 ( 331879) ulpERR_ABORT_Stmt_Query_Overflow The query statement is too
long. It must be less than 256k.**

**Cause:** The query statement exceeds 256k.

**Action:** Check the query statement.

**0x51068 ( 331880) ulpERR_ABORT_Too_Many_Rows_Error Too many rows returned.**

**Cause:** Too many rows were returned for the allocated space.

**Action:** Increase the size of the space allocated to receive the returned
rows.

**0x51069 ( 331881) ulpERR_ABORT_Invalid_User_Error Invalid user.**

**Cause:** The user ID does not exist.

**Action:** Re-enter your user ID.

**0x5106A ( 331882) ulpERR_ABORT_Invalid_Passwd_Error Invalid password.**

**Cause:** The password was incorrect.

**Action:** Re-enter your password.

**0x5106B ( 331883) ulpERR_ABORT_Stmt_Need_Execute_4Fetch_Error The statement
must be executed to fetch rows.**

**Cause:** The statement must be executed to fetch rows.

**Action:** Check the sequence of embedded SQL statements.

**0x5106C ( 331884) ulpERR_ABORT_Cursor_Need_Open_4Fetch_Error The cursor must
be opened to fetch rows.**

**Cause:** The cursor must be opened to fetch rows.

**Action:** Check the sequence of embedded SQL statements.

**0x5106D ( 331885) ulpERR_ABORT_COMP_cannot_exec_inXa_Error Cannot execute DCL
or DDL in a global transaction.**

**Cause:** Altibase XA cannot execute DCL or DDL SQL statements.

**Action:** Do not use DCL or DDL statements.

**0x5106E ( 331886) ulpERR_ABORT_NCHAR_No_Indicator_Error The NCHAR type value
must have an indicator.**

**Cause:** No indicator.

**Action:** Make an indicator.

**0x5106F ( 331887) ulpERR_ABORT_XA_GetConnectAttr_Error Cannot get the
connection attributes for ALTIBASE_XA_NAME.**

**Cause:** Cannot get the connection attributes for ALTIBASE_XA_NAME.

**Action:** Check the XA connection.

**0x51070 ( 331888) ulpERR_ABORT_Atomic_For_Value_Error A FOR clause must
execute at least once.**

**Cause:** The constant in an Atomic FOR clause was set to less than 1.

**Action:** Set the constant in the Atomic FOR clause so that it is greater than
1.

**0x51071 ( 331889) ulpERR_ABORT_FORstmt_Invalid_usage_Error The FOR clause can
only be used with variables of array or pointer type.**

**Cause:** An attempt was made to use a variable that was not an array or
pointer type with a FOR clause.

**Action:** Use array or pointer type variables with the FOR clause.

**0x51072 ( 331890) ulpERR_ABORT_Invalid_Indicator_Value_Error Invalid
indicator: \<0%d\>**

**Cause:** The value of the indicator is invalid.

**Action:** Change the indicator value.

**0x51073 ( 331891) ulpERR_ABORT_Unknown_Type_For_Shared_Pointer The type of the
pointer used is not supported.**

**Cause:** The type of the pointer used in DECLARE POINTER statement is not
supported.

**Action:** Declare the pointer with appropriate type.

**0x51074 ( 331892) ulpERR_ABORT_Memory_Alloc_Failed Memory allocation error.
\<0%s\>.**

**Cause:** Memory space has been exhausted.

**Action:** Reduce the amount of memory being used in client application.

**0x51075 ( 331893) ulpERR_ABORT_Invalid_Array_Size_Error Invalid bind set array
size: \<0%d\>**

**Cause:** The value of the array size is invalid.

**Action:** Check the value of the array size.

**0x51076 ( 331894) ulpERR_ABORT_Type_Not_Exist_Error Unknown type: \<0%d\>**

**Cause:** Incompatible data type.

**Action:** Check the compatibility of the data type.

**0x51077 ( 331895) ulpERR_ABORT_DynamicSql_Max_ColumnSize_Small SQLDA.N is too
small: \<0%d\>**

**Cause:** The value of the dynamic sql to be bound is too small.

**Action:** Check the column size and enlarge the value.

**0x51078 ( 331896) ulpERR_ABORT_DynamicSql_Max_BindSize_Small SQLDA.N is too
small: \<0%d\>**

**Cause:** The value of the dynamic sql to be bound is too small.

**Action:** Check the bind size and enlarge the value.

**0x51079 ( 331897) ulpERR_ABORT_Not_Supported_Host_Var_Type Currently not
supported host variable type.**

**Cause:** Currently not supported host variable type.

**Action:** Refer to the Precompiler user's manual for available host variables.

**0x5107A ( 331898) ulpERR_ABORT_Column_Value_Is_Null The fetched result
contains a NULL value. or Fetch column value is NULL.**

**Cause:** The fetched result contains a NULL value. or Fetch column value is
NULL.

**Action:** Verify that the stored procedure contains NULL.(Revise the cursor
definition so that no columns possibly containing NULL values are retrieved.)

**0x5107B ( 331899) ulpERR_ABORT_Invalid_PSM_Array_Version Invalid psm array
meta version.**

**Cause:** Invalid psm array meta version.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x5107C ( 331900) ulpERR_ABORT_Invalid_PSM_Array_Type The apre type and psm
array type do not match.**

**Cause:** The apre host variable type and psm array type do not match.

**Action:** Change the apre host variable types to the data types that are
supported by psm array.

11.Utilities Error Code
-----------------------

### FATAL

**0x90127 ( 590119) utERR_FATAL_FLOCK_INIT Failed to invoke the flock_init()
system function [\<0%s\>]**

**Cause:**

\# - The flock_init() system call failed.

**Action:** Please send a bug report to the vendor.

**0x90128 ( 590120) utERR_FATAL_FLOCK_DESTROY Failed to invoke the
flock_destroy() system function [\<0%s\>]**

**Cause:**

\# - The flock_destroy() system call failed.

**Action:** Please send a bug report to the vendor.

**0x90129 ( 590121) utERR_FATAL_FLOCK_TRYWRLOCK Failed to invoke the
flock_trywrlock() system function**

**Cause:**

\# - The flock_trywrlock() system call failed.

**Action:** Please send a bug report to the vendor.

**0x9012A ( 590122) utERR_FATAL_FLOCK_UNLOCK Failed to invoke the flock_unlock()
system function**

**Cause:**

\# - The flock_unlock() system call failed.

**Action:** Please send a bug report to the vendor.

**0x90103 ( 590083) utERR_FATAL_Mutex Mutex Operation Error.(\<0%s\>)**

**Cause:** The application encountered an unexpected error with the mutex.

**Action:** This is possibly a programming error. Check the error number from
the trace log and contact Altibase's Support Center
(http://support.altibase.com/en/)

**0x90121 ( 590113) utERR_FATAL_Signal Signal Operation Error.(\<0%s\>)**

**Cause:** An internal call to a signal function returned an error.

**Action:** Please send a bug report to the vendor.

### ABORT

**0x91002 ( 593922) utERR_ABORT_alreadyExistFileError File (\<0%s\>) already
exists.**

**Cause:** The file already exists.

**Action:** Remove or rename the file.

**0x91003 ( 593923) utERR_ABORT_env_not_exist The environment (\<0%s\>) does not
exist.**

**Cause:** The ALTIBASE environment has not been set.

**Action:** Set the ALTIBASE environment value.

**0x91004 ( 593924) utERR_ABORT_Invalid_dataType_Error Invalid data type
specified.**

**Cause:** The data type to be bound is not valid.

**Action:** Check the data type to be bound.

**0x91005 ( 593925) utERR_ABORT_name_length_overflow_Error The host variable
name length must be less than \<0%d\> characters.**

**Cause:** Host variable name length overflow.

**Action:** Decrease the length of the host variable name.

**0x91006 ( 593926) utERR_ABORT_memory_error Memory allocation
error.(\<0%s\>:\<1%d\>)**

**Cause:** The application failed to allocate memory for an environment handle
with SQLAllocEnv.

**Action:** Verify that there is enough memory to run the application. If
necessary, take action to make more memory available for the application.

**0x91007 ( 593927) utERR_ABORT_host_variable_not_defined_error The host
variable \<0%s\> was not defined.**

**Cause:** Host variable not defined.

**Action:** Define the host variable.

**0x91008 ( 593928) utERR_ABORT_type_mismatch_error Type mismatch error.**

**Cause:** The types do not match.

**Action:** Ensure that the data types are matched.

**0x91009 ( 593929) utERR_ABORT_too_large_error Too large data specified.**

**Cause:** The length of the specified data was too large.

**Action:** Decrease the length of the data.

**0x9100A ( 593930) utERR_ABORT_value_OutOfRange_error Host value out of
range.**

**Cause:** Host value out of range.

**Action:** Check the host value and ensure that it is within range.

**0x9100B ( 593931) utERR_ABORT_account_privilege_error Privilege error for
sysdba user account.**

**Cause:** Sysdba users must be connected with ALTIBASE user accounts.

**Action:** Check the user account.

**0x9100C ( 593932) utERR_ABORT_stat_error stat() system call error
(errno=\<0%d\>)**

**Cause:** The stat() call encountered an error.

**Action:** Check the file system.

**0x9100D ( 593933) utERR_ABORT_Unterminated_error Unterminated user command**

**Cause:** A user command was not terminated properly.

**Action:** Check the command.

**0x9100E ( 593934) utERR_ABORT_open_Syspasswd_FileError could not open
syspassword file (\<0%s\>)**

**Cause:** The syspassword does not exist, or you do not have sufficient
permission.

**Action:** Ensure that the file exists and that you have sufficient permission
to open the file.

**0x9100F ( 593935) utERR_ABORT_Incorrect_Password Incorrect Password**

**Cause:** The password was incorrect.

**Action:** Check the password.

**0x91010 ( 593936) utERR_ABORT_Syntax_Error Syntax Error**

**Cause:** Syntax Error.

**Action:** Check the syntax.

**0x91011 ( 593937) utERR_ABORT_No_History_Error No user command saved**

**Cause:** There are no saved commands.

**Action:** Specify a command and retry.

**0x91012 ( 593938) utERR_ABORT_History_Range_Error History number must be
between 1 and \<0%d\>.**

**Cause:** An incorrect history number was specified.

**Action:** Change the history number and retry.

**0x91013 ( 593939) utERR_ABORT_Too_Long_Query_Error The query was too long; the
maximum length is \<0%d\>.**

**Cause:** The query was too long.

**Action:** Shorten the query.

**0x91105 ( 594181) utERR_ABORT_User_No_Exist_Error The user (\<0%s\>) does not
exist.**

**Cause:** No user with that name exists.

**Action:** Check the user name and try again.

**0x91014 ( 593940) utERR_ABORT_Table_No_Exist_Error The table (\<0%s\>) does
not exist.**

**Cause:** No table with that name exists.

**Action:** Check the table name and try again.

**0x91015 ( 593941) utERR_ABORT_Comm_Failure_Error Communication failure.**

**Cause:** The network connection was closed.

**Action:** Check the dbms server.

**0x91016 ( 593942) utERR_ABORT_Sequence_No_Exist_Error The sequence does not
exist.**

**Cause:** No sequence with that name exists.

**Action:** Check the sequence name.

**0x91017 ( 593943) utERR_ABORT_Invalid_Command_Error The use of this command is
not allowed in a script file.**

**Cause:** Invalid command use.

**Action:** Do not use this command in a script file.

**0x91018 ( 593944) utERR_ABORT_sysdba_privilege_Error reconnect as sysdba.**

**Cause:** The sysdba user must be used for this action.

**Action:** Reconnect as sysdba.

**0x91019 ( 593945) utERR_ABORT_command_buffer_Error ISQL_BUFFER_SIZE must be
greater than \<0%d\>.**

**Cause:** The ISQL_BUFFER_SIZE was too small.

**Action:** Increase the value of the ISQL_BUFFER_SIZE environment variable.

**0x9101A ( 593946) utERR_ABORT_property_omit_Error Property (\<0%s\>) not
found.**

**Cause:** The property was not found.

**Action:** Check whether the property exists.

**0x9101B ( 593947) utERR_ABORT_Column_Size_Error ColSize option value out of
range (\<0%d\> - \<1%d\>)**

**Cause:** An invalid ColSize value was specified.

**Action:** Check the ColSize value.

**0x9101C ( 593948) utERR_ABORT_Page_Size_Error PageSize option value out of
range (\<0%d\> - \<1%d\>)**

**Cause:** An invalid PageSize value was specified.

**Action:** Check the PageSize value.

**0x9101D ( 593949) utERR_ABORT_already_spool_on_Error Spool is already in an ON
state. (\<0%s\>)**

**Cause:** Spool already ON.

**Action:** Turn off the spool and retry.

**0x9101E ( 593950) utERR_ABORT_cant_spool_off_Error Spool is not in an ON
state.**

**Cause:** Can't turn off a spool that is already off.

**Action:** Only attempt this action in a spool-on state.

**0x9101F ( 593951) utERR_ABORT_closeFileError Could not close the file
(\<0%s\>).**

**Cause:** The application failed to close a file.

**Action:** This could be a system problem or programming error. Verify that
there is no problem with your file system. If there is no such problem, check
the error number from the trace log and contact Altibase's Support Center
(http://support.altibase.com/en/).

**0x91020 ( 593952) utERR_ABORT_Not_Connected_Error No Connection State**

**Cause:** No connection exists.

**Action:** Connect first and try again.

**0x91021 ( 593953) utERR_ABORT_Line_Size_Error Line Size option value out of
range (\<0%d\> - \<1%d\>)**

**Cause:** An invalid line size was specified.

**Action:** Check the line size.

**0x91022 ( 593954) utERR_ABORT_UNDISPLAYABLE_DATATYPE_Error LOB and GEOMETRY
type data cannot be displayed**

**Cause:** Can't print LOB or GEOMETRY data using the console.

**Action:** Use a user CLI Application for printing.

**0x91025 ( 593957) utERR_ABORT_WRONG_DATATYPE_Error Unknown data types cannot
be displayed**

**Cause:** Can't print unknown data types using the console.

**Action:** Use a user CLI Application for printing.

**0x91026 ( 593958) utERR_ABORT_Proc_No_Exist_Error The procedure (\<0%s\>) does
not exist.**

**Cause:** There is no procedure with the name you specified.

**Action:** Check the procedure name and try again.

**0x910FA ( 594170) utERR_ABORT_Operation_Canceled Operation cancelled**

**Cause:** SQLCancel was called on the StatementHandle.

**Action:** No action is necessary.

**0x910FB ( 594171) utERR_ABORT_Connected_Idle_Instance_Error Connected to idle
instance**

**Cause:** No error has occurred, this is just a notification of connection to
an idle instance of Altibase.

**Action:** No action is necessary.

**0x910FC ( 594172) utERR_ABORT_Incorrect_User Incorrect user name used
(\<0%s\>).**

**Cause:** Only "sys" user can use "-sysdba" option.

**Action:** Login as "sys" user name to use "-sysdba" option.

**0x91101 ( 594177) utERR_ABORT_LOB_AUTOCOMMIT_MODE_ERR Connection is in
autocommit mode. One cannot operate on LOB data when autocommit mode is on.**

**Cause:** An attempt to execute a LOB operation was made while the connection
was in autocommit mode.

**Action:** Turn off autocommit mode.

**0x91124 ( 594212) utERR_ABORT_GRACE_TIME_WARN The password will expire within
\<0%d\> days.**

**Cause:** The user's account has expired and the password needs to be changed.

**Action:** Change the user's password.

**0x91125 ( 594213) utERR_ABORT_Num_Width_Error NumWidth option value out of
range (\<0%d\> - \<1%d\>).**

**Cause:** An invalid numwidth was specified.

**Action:** Check the numwidth.

**0x91126 ( 594214) utERR_ABORT_INVALID_CONN_ATTR Invalid connection attribute
pair: \<0%s\> = \<1%s\>**

**Cause:** The connection attribute is invalid.

**Action:** Check the connection attribute.

**0x91133 ( 594227) utERR_ABORT_Exceed_Max_String String is too long. Maximum
size is \<0%d\> characters.**

**Cause:** The string is longer than the maximum length.

**Action:** Use a string shorter than the maximum length.

**0x91134 ( 594228) utERR_ABORT_Failed_Open_Path Failed to open the
path.(\<0%s\>: \<1%s\>)**

**Cause:** Either an invalid path was specified or you have insufficient
persmission.

**Action:** Verify that you have entered the correct path or that you have
sufficient permission.

**0x91138 ( 594232) utERR_ABORT_Cancel_Not_Supported Canceling is not
supported.**

**Cause:** The driver does not support the SQLCancel function.

**Action:** Wait for the statement to be completed or close this session using
ALTER DATABASE by another session.

**0x91139 ( 594233) utERR_ABORT_Illegal_Format_String Illegal FORMAT String
(\<0%s\>).**

**Cause:** An invalid format string was specified.

**Action:** Retry again with a valid format string.

**0x9113A ( 594234) utERR_ABORT_Column_Not_Defined Column not defined
(\<0%s\>).**

**Cause:** The specified column name was not defined.

**Action:** Retry again with a valid column name.

**0x9113D ( 594237) utERR_ABORT_Failed_To_Cancel Cancel cannot be done at the
moment.**

**Cause:** The cancel request cannot be accepted at the moment.

**Action:** Wait until the statement is completed.

**0x9113F ( 594239) utERR_ABORT_Failed_To_Sysdba_Connect_Remotely Unable to
connect to deactivated Altibase by remotely using -sysdba option.**

**Cause:** The remote Altibase is not operating.

**Action:** Try again after starting Altibase.

**0x91141 ( 594241) utERR_ABORT_PrefetchRows_Error PrefetchRows option value out
of range (\<0%d\> - \<1%d\>)**

**Cause:** An invalid PrefetchRows value was specified.

**Action:** Check the PrefetchRows value.

**0x91142 ( 594242) utERR_ABORT_AsyncPrefetch_Auto_Warning Unable to run auto
tuning due to the CLI restriction. 'AsyncPrefetch on' will be automatically
applied.**

**Cause:** The auto tuning is only supported on Linux environment.

**Action:** 'AsyncPrefetch on' is automatically applied on operating systems
other than Linux. However, 'AsyncPrefetch on' should be specified whether or not
to display a warning.

**0x91027 ( 593959) utERR_ABORT_Dup_Option_Error Option (\<0%s\>) is used more
than once.**

**Cause:** A duplicate option was specified.

**Action:** Check the options.

**0x91028 ( 593960) utERR_ABORT_Unknown_Option_Error An unknown Option (\<0%s\>)
was specified.**

**Cause:** An unknown option was specified.

**Action:** Check the option and try again.

**0x91029 ( 593961) utERR_ABORT_Option_Value_Range_Error The option value
(\<0%s\>) must be greater than (\<1%d\>).**

**Cause:** The option value was not within the valid range.

**Action:** Change the option value.

**0x9102A ( 593962) utERR_ABORT_Not_Support_dataType_Error The data type
(\<0%s\>\<1%s\>) \<2%s\>\<3%s\> is not supported.**

**Cause:** An invalid data type was used.

**Action:** Check the data type.

**0x9102B ( 593963) utERR_ABORT_Token_Value_Range_Error Token value length
overflow. Maximum token length=\<0%d\>. Column =\<1%s\>, Value=\<2%s\>**

**Cause:** The token value length exceeded the valid range.

**Action:** Decrease the token length.

**0x9102C ( 593964) utERR_ABORT_Parse_Command_Error Input command parser error**

**Cause:** The command parse token was invalid.

**Action:** Check the token.

**0x9102E ( 593966) utERR_ABORT_Result_Attr_Count_Error Result attribute count
is different. (Form=\<0%d\>, User=\<1%d\>**

**Cause:** The table data type information was different.

**Action:** Check the table information.

**0x9102F ( 593967) utERR_ABORT_Delete_Table_Error Failed to delete record from
table (\<0%s\>)**

**Cause:** Delete operation failed.

**Action:** Check the table recordset.

**0x91030 ( 593968) utERR_ABORT_Arg_omit_Error Argument (\<0%s\>) not found.**

**Cause:** A necessary argument was omitted.

**Action:** Provide the argument and try again.

**0x91031 ( 593969) utERR_ABORT_Option_Incorrect_Error The \<0%s\> option
(\<1%s\>) was not used, or the precedence option is not correct.**

**Cause:** Option use error.

**Action:** Ensure that you are using the options correctly.

**0x91032 ( 593970) utERR_ABORT_Field_Terminator_Error Field, Row and
Enclosingchar terminators must be different.**

**Cause:** A terminator conflict occurred.

**Action:** Use a different terminator.

**0x91033 ( 593971) utERR_ABORT_SQLColumn_Error Field, Row and Enclosingchar
terminators must be different.**

**Cause:** A terminator conflict occurred.

**Action:** Use a different terminator.

**0x91035 ( 593973) utERR_ABORT_too_many_Seq_Error Too many sequences were used.
(LIMIT=\<0%d\>)**

**Cause:** The number of sequences exceeded the valid range.

**Action:** Decrease the number of sequences.

**0x91036 ( 593974) utERR_ABORT_too_many_Attr_Error Too many attributes were
used. (LIMIT=\<0%d\>)**

**Cause:** The number of attributes exceeded the valid range.

**Action:** Decrease the number of attributes.

**0x91037 ( 593975) utERR_ABORT_No_Column_Sequence_Error No existing column
linked to sequence (\<0%s\>)**

**Cause:** No column is linked to the sequence.

**Action:** Check the form file.

**0x91038 ( 593976) utERR_ABORT_Many_Column_Sequence_Error Duplicate column
(\<0%s\>) to sequence (\<1%d\>) links**

**Cause:** A column is linked to the sequence two or more times.

**Action:** Check form file.

**0x91039 ( 593977) utERR_ABORT_Unkown_Datatype_Error An unknown datatype
\<0%s\> was used.**

**Cause:** An assign attempt was made using an unknown data type.

**Action:** Check the data type used for binding.

**0x9103A ( 593978) utERR_ABORT_Wrong_Column_Count_Error Column count mismatch
(size=\<0%d\>**

**Cause:** Invalid data fetch processing.

**Action:** Check the table information.

**0x9103B ( 593979) utERR_ABORT_Invalid_Option_Error Invalid option (\<0%s\>)**

**Cause:** An invalid option was used.

**Action:** Check the options.

**0x9103C ( 593980) utERR_ABORT_Option_Value_Overflow_Error The option value
(\<0%s\>) must be equal or less than the upper limit (\<1%d\>).**

**Cause:** The option value exceeded the valid range.

**Action:** Change the option value.

**0x9103D ( 593981) utERR_ABORT_Parsing_Error Data parsing error (Column :
\<0%s\>)**

**Cause:** Data parsing error.

**Action:** Check the token.

**0x9103E ( 593982) utERR_ABORT_UserID_Omit_Error A user ID must be specified.**

**Cause:** The user ID was omitted.

**Action:** Enter a user ID.

**0x9103F ( 593983) utERR_ABORT_Password_Omit_Error A password must be
specified.**

**Cause:** The password was omitted.

**Action:** Enter a password.

**0x91040 ( 593984) utERR_ABORT_ServerName_Omit_Error A ServerName must be
specified.**

**Cause:** The server name was omitted.

**Action:** Enter a server name.

**0x91123 ( 594211) utERR_ABORT_Port_Omit_Error No port number was specified.**

**Cause:** The -port option value was omitted.

**Action:** Specify a port number for the port option and try again.

**0x91041 ( 593985) utERR_ABORT_LOB_Opt_Str_Error Missing or invalid LOB option
string.**

**Cause:** A LOB option string is missing or invalid.

**Action:** Check the LOB option string.

**0x91042 ( 593986) utERR_ABORT_Invalid_Value Invalid data value**

**Cause:** The value of the data exceeds the valid range.

**Action:** Check the data value.

**0x9111F ( 594207) utERR_ABORT_Invalid_Value_errno Invalid data value
(errno=\<0%d\>)**

**Cause:** The value of the data exceeds the valid range.

**Action:** Check the data value.

**0x91043 ( 593987) utERR_ABORT_Invalid_Value_Len Invalid data length**

**Cause:** The length of the data exceeds the valid range.

**Action:** Check the length of the data.

**0x91044 ( 593988) utERR_ABORT_Data_File_IO_Error Error occurred during data
file I/O.**

**Cause:** The file does not exist, there is no more space in the filesystem,
the file size is too big, or a similar error has occurred.

**Action:** Check the filesystem.

**0x91045 ( 593989) utERR_ABORT_LOB_File_IO_Error Error occurred during LOB file
I/O.**

**Cause:** The file does not exist, there is no more space in the filesystem,
the file size is too big, or a similar error has occurred.

**Action:** Check the filesystem.

**0x91046 ( 593990) utERR_ABORT_Nls_Use_Error ALTIBASE_NLS_USE does not match
DATA_NLS_USE**

**Cause:** ALTIBASE_NLS_USE does not match DATA_NLS_USE in formout file.

**Action:** Change ALTIBASE_NLS_USE to match DATA_NLS_USE and retry.

**0x91047 ( 593991) utERR_ABORT_CSV_Option_Error The -rule csv option can't be
used with the -t or -e options.**

**Cause:** An attempt was made to use the -rule csv option with the -t or -e
option.

**Action:** Check the options and try again.

**0x910FD ( 594173) utERR_ABORT_Invalid_CSV_File_Format_Error Invalid CSV file
format token. Column=\<0%s\>, Value=\<1%s\>.**

**Cause:** The CSV file format is wrong.

**Action:** Check the CSV data file.

**0x91100 ( 594176) utERR_ABORT_File_Lock_Error File [\<0%s\>] open failed.
Already in use.**

**Cause:** The specified file is already in use.

**Action:** Check whether the file is already in use.

**0x91102 ( 594178) utERR_ABORT_Form_Parser_Error Input form parser error.**

**Cause:** The form file is wrong.

**Action:** Check the form file.

**0x91104 ( 594180) utERR_ABORT_OutFile_IO_Error An error occurred during file
output.**

**Cause:** The file does not exist, there is no more space in the file system,
the file size is too big, or a similar error has occurred.

**Action:** Check the file system.

**0x91106 ( 594182) utERR_ABORT_Bad_File_IO_Error An error occurred during bad
file I/O.**

**Cause:** The file does not exist, there is no more space in the file system,
the file size is too big, or a similar error has occurred.

**Action:** Check the file system.

**0x91107 ( 594183) utERR_ABORT_Log_File_IO_Error An error occurred during log
file I/O.**

**Cause:** The file does not exist, there is no more space in the file system,
the file size is too big, or a similar error has occurred.

**Action:** Check the file system.

**0x9113B ( 594235) utERR_ABORT_Param_Count_Mismatch Parameter count mismatch.
Required=(\<0%d\>), INSERT statement=(\<1%s\>).**

**Cause:** The number of parameters in the INSERT statement is different from
the number of table columns.

**Action:** Check the form file.

**0x9113E ( 594238) utERR_ABORT_Prefetch_Row_Error -prefetch_row option value
out of range (\<0%d\> - \<1%d\>)**

**Cause:** An invalid PrefetchRow value was specified.

**Action:** Check the PrefetchRow value.

**0x91140 ( 594240) utERR_ABORT_Async_Prefetch_Auto_Warning Unable to run auto
tuning due to the CLI restriction. '-async_prefetch on' will be automatically
applied.**

**Cause:** The auto tuning is only supported on Linux environment.

**Action:** '-async_prefetch on' is automatically applied on operating systems
other than Linux to execute an iloader out command. However, '-async_prefetch
on' should be specified whether or not to display a warning.

**0x91064 ( 594020) utERR_ABORT_password_Error Cound not find the password for
user (\<0%s\>)**

**Cause:** Could not get user information.

**Action:** Check the user name and try again.

**0x91065 ( 594021) utERR_ABORT_aexport_Property_Error Invalid property value
(\<0%s\>).**

**Cause:** An invalid property value was assigned, or the value was omitted.

**Action:** Check the property value.

**0x91066 ( 594022) utERR_ABORT_Property_Loading_Error Property File Loading
Error.(\<0%s\>)**

**Cause:** An invalid or nonexistent property path was specified.

**Action:** Check the property file.

**0x910C8 ( 594120) utERR_ABORT_AUDIT_Alloc_Handle_Error Can't get the Handle
from \<0%s\>**

\# Altibase could not initialize SQLEnv; an OCIEnv handle could not be
allocated.

**Cause:** The application failed to allocate memory for an environment handle
with SQLAllocEnv.

**Action:** Verify that there is enough memory to run the application. If
necessary, make more memory available for the application.

**0x910C9 ( 594121) utERR_ABORT_AUDIT_Already_Conn_Error Already connected to
server.**

\# Connection already initialized!

**Cause:** The application attempted to use an uninitialized connection handle.

**Action:** This is possibly a programming error. Check the error number from
the trace log and contact Altibase's Support Center
(http://support.altibase.com/en/).

**0x910CA ( 594122) utERR_ABORT_AUDIT_Create_Instance_Error Failed to create
object \<0%s\>**

\# Cause: The application failed to allocate memory to create an object.

**Action:** Verify that there is enough memory to run the application. If
necessary, make more memory available for the application.

**0x910CC ( 594124) utERR_ABORT_AUDIT_Check_Log_File_Error Failed to open the
log file \<0%s\>**

\# ERROR: %s, Check your log dir and log file properties.

**Cause:** Failed to open the log file.

**Action:** Check the log file designated in the properties and the permissions
mode of the log file.

**0x910CD ( 594125) utERR_ABORT_AUDIT_Wrong_Parameter_Error A parameter is
incorrect**

\# ERROR: A parameter is incorrect.

**Cause:** An invalid parameter was used.

**Action:** Check the parameters.

**0x910CE ( 594126) utERR_ABORT_AUDIT_Not_Found_Parameter_Error Invalid Property
Name \<0%s\> Assigned.**

\# ERROR: Properties parameter (%s) is not defined.

**Cause:** An invalid property name has been defined.

**Action:** Check the property name in the property file.

**0x910CF ( 594127) utERR_ABORT_AUDIT_ERANGE_Error The value of the properties
parameter \<0%s\> was out of range**

\# ERROR: The value of the properties parameter %s was out of range.

**Cause:** The parameter's value is incorrect.

**Action:** Check the value of the parameter.

**0x910D0 ( 594128) utERR_ABORT_AUDIT_EINVAL_Error Properties parameter \<0%s\>
no conversion was performed, wrong parameter**

\# ERROR:Properties parameter %s no conversion was performed, wrong parameter

**Cause:** The parameter was incorrect.

**Action:** Check the parameter.

**0x910D1 ( 594129) utERR_ABORT_AUDIT_NULL_Parameter_Error Undefined Property
\<0%s\>.**

\# ERROR: The properties parameter %s key is NULL.

**Cause:** Property not defined in the property file.

**Action:** Check the property file.

**0x910D2 ( 594130) utERR_ABORT_AUDIT_Invalid_Parameter_Error An invalid
property value \<0%s\> was defined.**

\# Invalid property: %s

**Cause:** An invalid property value was defined in the property file.

**Action:** Check the property value.

**0x910D3 ( 594131) utERR_ABORT_AUDIT_Wrong_URL_Error Invalid DBMS URL.**

\# ERROR[ PROP ] Incorrect DBMS connection URL.

**Cause:** The URL for connection to the DBMS is incorrect.

**Action:** Check the URL.

**0x910D4 ( 594132) utERR_ABORT_AUDIT_Alloc_Memory_Error Memory Allocation
failed.**

\# ERROR[ PROP ] Could not allocate memory

**Cause:** The application failed to allocate memory.

**Action:** Verify that there is enough memory to run the application. If
necessary, make more memory available for the application.

**0x910D5 ( 594133) utERR_ABORT_AUDIT_Different_Column_Error The column counts
for (\<0%s\>) and (\<1%s\>) are different.**

\# The tables (%s,%s) have different column counts.

**Cause:** The master and slave have different table column counts.

**Action:** Ensure that the table schema for the master and slave are the same.

**0x910D6 ( 594134) utERR_ABORT_AUDIT_DIFF_File_Open_Error Failed to open audit
diff file \<0%s\>.**

\# utScanner can't open DIFF log file:'%s'.

**Cause:** Failed to open log file.

**Action:** Check the log file name and permissions mode of the files.

**0x910D7 ( 594135) utERR_ABORT_AUDIT_PK_Different_Order_Error The order of the
primary key on the master(\<0%s\>) is different from that on the slave
(\<1%s\>).**

\# The master (%s) and slave (%s) have different primary key orders.

**Cause:** The primary key orders on the master and slave are different.

**Action:** Ensure that the table schema for the master and slave are the same.

**0x910D8 ( 594136) utERR_ABORT_AUDIT_Master_No_PK_Error No primary key column
exists (\<0%s\>:\<1%s\>)**

\# The tables (%s,%s) have no primary keys.

**Cause:** The master table does not have a primary key column.

**Action:** Change the master table so that is has a primary key column.

**0x910D9 ( 594137) utERR_ABORT_AUDIT_Different_PK_Columns_Error The PK column
count for (\<0%s\>) is different than that for (\<1%s\>)**

\# The primary key structures for the tables(%s,%s) are different.

**Cause:** The number of primary key columns in the master table is different
from that in the slave table.

**Action:** Ensure that the table schema for the master and slave are the same.

**0x910DA ( 594138) utERR_ABORT_AUDIT_PK_CanNotBe_EXCLUDE_Error Primary key
columns cannot be defined as EXCLUDE columns (\<0%s\>)**

\# Exclusion column cannot be primary key field '%s'.

**Cause:** Primary key columns cannot be defined as EXCLUDE columns.

**Action:** Check the EXCLUDE property value.

**0x910DB ( 594139) utERR_ABORT_AUDIT_NOT_Fount_Column_EXCLUDE_Error Invalid
column defined in EXCLUDE property (\<0%s\>)**

\# Exclusion column '%s' is not found.

**Cause:** An invalid column was defined in the property file's EXCLUDE
property.

**Action:** Check the EXCLUDE property value.

**0x910DC ( 594140) utERR_ABORT_AUDIT_Thread_Join_Error thread_join() \<0%d\>
failed.**

\# ERROR [ MNG ] Join \#%d failure!

**Cause:** The application encountered an error while joining threads.

**Action:** This is possibly a programming error. Check the error number from
the trace log and contact Altibase's Support Center
(http://support.altibase.com/en/).

**0x910DD ( 594141) utERR_ABORT_AUDIT_Connect_TO_Master_Error Failed to connect
to master \<0%s\> server**

\# Cannot connect to master server: '%s'

**Cause:** Failed to connect to the master server.

**Action:** Check the connection information.

**0x910DE ( 594142) utERR_ABORT_AUDIT_Connect_TO_Slaver_Error Failed to connect
to slave \<0%s\> server**

\# Cannot connect to slave server: '%s'

**Cause:** Failed to connect to the slave server.

**Action:** Check the connection information.

**0x910DF ( 594143) utERR_ABORT_openFileError Could not open file (\<0%s\>)**

**Cause:** The file does not exist, or does not have the appropriate
permissions.

**Action:** Check the permission settings of the file and whether the file
exists.

**0x910E0 ( 594144) utERR_ABORT_sysdba_connect_Error You cannot connect to the
server remotely with the sysdba option.**

**Cause:** You cannot connect to a server remotely with the sysdba option.

**Action:** Check the SERVER and PORT_NO options.

**0x910E1 ( 594145) utERR_ABORT_AUDIT_Managing_Thread_Filemode Thread management
failed for the file mode with table \<0%s\> and \<1%s\>.**

\# Thread management is failed.

**Cause:** The application encountered an error while handling a thread.

**Action:** This is possibly a programming error. Check the error number from
the trace log and contact Altibase's Support Center
(http://support.altibase.com/en/).

**0x910E2 ( 594146) utERR_ABORT_AUDIT_File_Open_4CSVfile Could not create or
open the \<0%s\> csv file.**

\# ERROR: %s, check your csv file properties and disk.

**Cause:** An attempt to create or open a csv file failed.

**Action:** Check the file system disk and try again.

**0x910E3 ( 594147) utERR_ABORT_AUDIT_File_Close_4CSVfile Could not close the
\<0%s\> csv file.**

\# ERROR: %s, check your csv file properties and disk.

**Cause:** An attempt to close a csv file failed.

**Action:** Check the file system disk and try again.

**0x910E4 ( 594148) utERR_ABORT_AUDIT_File_Write_4CSVfile Could not write to the
\<0%s\> csv file.**

\# ERROR: %s, check your csv file properties and disk.

**Cause:** An attempt to write to a csv file failed.

**Action:** Check the file system disk and try again.

**0x910E5 ( 594149) utERR_ABORT_AUDIT_Cursor_Close A cursor was not closed
correctly.**

**Cause:** A cursor was not closed correctly.

**Action:** Check the statement.

**0x910E6 ( 594150) utERR_ABORT_AUDIT_File_Read_4CSVfile Could not read the
\<0%s\> csv file.**

\# ERROR: %s, check your csv file properties and disk.

**Cause:** An attempt to read a csv file failed.

**Action:** Check the file system disk and try again.

**0x910E7 ( 594151) utERR_ABORT_AUDIT_Wrong_CSV_Format Wrong CSV file format.
(\<0%s\>)**

\# ERROR: %s, check your csv file content.

**Cause:** The attempt to convert data from the CSV file format to the original
data format failed.

**Action:** Check the csv file and try again.

**0x910E8 ( 594152) utERR_ABORT_AUDIT_CSV_Token_Buffer_Overflow Buffer overflow
occurred during CSV format conversion. (data:'\<0%s\>')**

\# ERROR: %s, check your csv file content.

**Cause:** The attempt to convert data from the CSV file format to the original
data format failed.

**Action:** Check the csv file and try again.

**0x9113C ( 594236) utERR_ABORT_Table_Not_Found_Error The table
(\<0%s\>.\<1%s\>) specified in the configuration file does not exist on the
\<2%s\> database.**

**Cause:** The specified table does not exist in the database.

**Action:** Check to see if the specified table name located in the altiComp
configuration file is correct.

**0x91108 ( 594184) utERR_ABORT_UPLOAD_Error Could not upload the entire data
file.**

\# Cannot upload file

**Cause:** The data file appears to be invalid.

**Action:** Check the data file and try again.

**0x91109 ( 594185) utERR_ABORT_LIB_VERSION_Error An iLoader library version
incompatibility error occurred.**

**Cause:** An iLoader library version incompatibility error occurred.

**Action:** Check the iLoader library version.

**0x9110A ( 594186) utERR_ABORT_THREAD_Error Could not create a new thread.**

**Cause:** A platform kernel limit pertaining to the number of threads or memory
usage was exceeded.

**Action:** Decrease the number of threads.

**0x9110B ( 594187) utERR_ABORT_INVALID_USE_OF_NULL_POINTER Invalid use of null
pointer. (\<0%s\>)**

**Cause:** A null pointer was used.

**Action:** Check the pointer and try again.

**0x9110C ( 594188) utERR_ABORT_OPTION_VERSION_Error A library option version
incompatibility error occurred.**

**Cause:** Different library option versions are in use.

**Action:** Check the option versions.

**0x9110D ( 594189) utERR_ABORT_INVALID_ATTR_OPTION Invalid attribute/option
identifier : \<0%d\>.**

**Cause:** An invalid attribute/option identifier was used.

**Action:** Send a bug report to the vendor

**0x9110E ( 594190) utERR_ABORT_Unsupported_Feature Unsupported feature :
\<0%s\>**

**Cause:** This feature is not supported.

**Action:** Do not use this feature.

**0x9110F ( 594191) utERR_ABORT_MsgLog_Init_Error Unable to initialize message
log file.**

**Cause:** Unable to initialize a message log file.

**Action:** Check that the path and filename are correct and that suitable
permissions have been granted.

**0x91110 ( 594192) utERR_ABORT_LockFile_Init_Error Unable to initialize file
lock.[\<0%s\>]**

**Cause:** An attempt to initialize a file lock failed.

**Action:** Check that the path and filename are correct and that suitable
permissions have been granted.

**0x91111 ( 594193) utERR_ABORT_LockFile_Destroy_Error Unable to destroy file
lock.[\<0%s\>]**

**Cause:** An attempt to destroy a file lock failed.

**Action:** Check that the path and filename are correct and that suitable
permissions have been granted.

**0x91112 ( 594194) utERR_ABORT_LockFile_Not_Exist File to be locked does not
exist.[\<0%s\>]**

**Cause:** The file to be locked does not exist.

**Action:** Check that the path and filename are correct and that suitable
permissions have been granted.

**0x91113 ( 594195) utERR_ABORT_FileLock_Hold_Error Could not hold a lock on a
file.**

**Cause:** A lock on a file could not be held.

**Action:** Check that the path and filename are correct and that suitable
permissions have been granted.

**0x91114 ( 594196) utERR_ABORT_FileLock_Release_Error Could not release a lock
on a file.**

**Cause:** A lock on a file could not be released.

**Action:** Check that the path and filename are correct and that suitable
permissions have been granted.

**0x91115 ( 594197) utERR_ABORT_Failed_To_Check_Server_Running Could not obtain
server status; possible socket problem.**

**Cause:** The server status could not be determined.

**Action:** Check for a socket problem.

**0x91116 ( 594198) utERR_ABORT_PidFile_Failed_To_Check_Exist Unable to verify
the existence of pid file : \<0%s\>**

**Cause:** The existence of a pid file could not be verified.

**Action:** Check that the path and filename are correct and that suitable
permissions have been granted.

**0x91117 ( 594199) utERR_ABORT_PidFile_Exist Pid file (\<0%s\>) exists.**

**Cause:** The pid file already exists.

**Action:** Check the checkServer process and then run killCheckServer.
Alternatively, delete the pid file and run checkServer.

**0x91118 ( 594200) utERR_ABORT_PidFile_Create_Error Unable to create the pid
file [rc:\<0%d\>]**

**Cause:** The pid file could not be created.

**Action:** Check that the path and filename are correct and that suitable
permissions have been granted.

**0x91119 ( 594201) utERR_ABORT_PidFile_Remove_Error Unable to remove the pid
file [rc:\<0%d\>]**

**Cause:** The pid file could not be removed.

**Action:** Check that the path and filename are correct and that suitable
permissions have been granted.

**0x9111A ( 594202) utERR_ABORT_PidFile_Open_Error Unable to open the pid file
[rc:\<0%d\>]**

**Cause:** The pid file could not be opened.

**Action:** Check that the path and filename are correct and that suitable
permissions have been granted.

**0x9111B ( 594203) utERR_ABORT_PidFile_Close_Error Unable to close pid file
[rc:\<0%d\>]**

**Cause:** The pid file could not be closed.

**Action:** Check that the path and filename are correct and that suitable
permissions have been granted.

**0x9111C ( 594204) utERR_ABORT_PidFile_Read_Error pid structure read error
[rc:\<0%d\>]**

**Cause:** The pid could not be read from the pid file.

**Action:** Check that the path and filename are correct, that suitable
permissions have been granted, and that the pid file is valid.

**0x9111D ( 594205) utERR_ABORT_PidFile_Write_Error pid structure write error
[rc:\<0%d\>]**

**Cause:** The pid could not be written to the pid file.

**Action:** Check that the path and filename are correct and that suitable
permissions have been granted.

**0x9111E ( 594206) utERR_ABORT_Process_Kill_Error Unable to kill the process
[pid:\<0%d\>]**

**Cause:** An attempt to kill a process failed.

**Action:** Check whether the process has already been killed.

**0x91120 ( 594208) utERR_ABORT_FUNCTION_SEQUENCE_ERR Function sequence error.**

**Cause:** The order in which function calls were made is invalid.

**Action:** Refer to the state transition table to determine the correct
function call order.

**0x9112E ( 594222) utERR_ABORT_DAEMON_SUPPORT_ERR The daemon process supports
only tcp connection.**

**Cause:** The daemon process supports only tcp connection.

**Action:** Please reconnect to the daemon process with tcp connection.

**0x91122 ( 594210) utERR_ABORT_NOT_EXIST_TABLESPACE_ERR The default tablespace
for the user \<0%s\> does not exist.**

**Cause:** The tablespace that was set as the default for this user has been
modified or deleted.

**Action:** Set the default tablespace for this user and run aexport again.

**0x9112B ( 594219) utERR_ABORT_Insufficient_Priv_Error Needs the CREATE TABLE
privilege to analyze object dependencies.**

**Cause:** The user needs the CREATE TABLE privilege to analyze object
dependencies.

**Action:** Grant the CREATE TABLE or CREATE ANY TABLE privileges to the user
and re-execute aexport.

**0x9112C ( 594220) utERR_ABORT_Db_Charset_Fetch_Error Unable to fetch the
database character set.**

**Cause:** Failed to fetch the database character set.

**Action:** Set the -NLS_USE parameter or the ALTIBASE_NLS_USE environment
variable and re-execute aexport.

**0x9112D ( 594221) utERR_ABORT_Repl_Offline_Log_Path_Fetch_Error Unable to
fetch log directory paths for the replication \<0%s\> in offline mode.**

**Cause:** Failed to fetch log directory paths for the replication in offline
mode.

**Action:** This is possibly meta inconsistency. Contact Altibase's Support
Center (http://support.altibase.com/en/)

**0x9112F ( 594223) utERR_ABORT_INVALID_FMT Invalid file format**

**Cause:** Failed to read from the profiling file.

**Action:** Check the versions of the profiling file and the altiProfile tool.

**0x91130 ( 594224) utERR_ABORT_FILE_OPEN Unable to open file (\<0%s\>)**

**Cause:** The path or filename is invalid.

**Action:** Verify that the path and filename are correct and that you have
read/write permission for the file.

**0x91131 ( 594225) utERR_ABORT_FILE_CLOSE Unable to close file (\<0%d\>)**

**Cause:** An invalid file handle was specified.

**Action:** Memory corruption may occur. Check the error number and contact
Altibase's Support Center (http://support.altibase.com/en/).

**0x91132 ( 594226) utERR_ABORT_INVALID_HANDLE Invalid Handle**

**Cause:** NULL handle was specified.

**Action:** Memory corruption may occur. Check the error number and contact
Altibase's Support Center (http://support.altibase.com).

**0x91135 ( 594229) utERR_ABORT_INVALID_ALTIWRAP_COMMAND Invalid command
arguments.**

**Cause:** Invalid command arguments.

**Action:** Verify that the command arguments are valid.

**0x91136 ( 594230) utERR_ABORT_MEMORY_ALLOCATION Insufficient memory for PSM
Query Encryption.**

**Cause:** Insufficient memory.

**Action:** Verify that the system has enough available memory.

**0x91137 ( 594231) utERR_ABORT_TOO_LONG_PATH_NAME The path name was too long;
the maximum length is \<0%d\>.**

**Cause:** The path name was too long.

**Action:** Shorten the path name.

### IGNORE

**0x92001 ( 598017) utERR_IGNORE_NoError No UT module error**

**Cause:** This is not an error.

**Action:** You can safely ignore this error message.

12.CM Error Code
----------------

### FATAL

**0x70076 ( 458870) cmERR_FATAL_CMN_SHM_ATTACH Unable to attach the shared
memory**

**Cause:** Failed to invoke the shmat() function

**Action:** Ensure that you have permission to access the shared memory. Contact
Altibase’s Support Center (http://support.altibase.com/en/).

**0x70077 ( 458871) cmERR_FATAL_CMN_SHM_CTL Unable to delete the shared memory**

**Cause:** Failed to invoke the shmctl() function

**Action:** Ensure that you have permission to access the shared memory. Contact
Altibase’s Support Center (http://support.altibase.com/en/).

**0x70078 ( 458872) cmERR_FATAL_CMN_SEM_CTL Unable to delete the semaphore**

**Cause:** Failed to invoke the semctl() function

**Action:** Verify that you have permission to access the semaphore. Contact
Altibase’s Support Center (http://support.altibase.com/en/).

**0x70079 ( 458873) cmERR_FATAL_CMN_SEM_OP Unable to execute operations on a
semaphore**

**Cause:** Failed to invoke the semop() function

**Action:** Check the error number and verify that the semaphore group exists.

**0x7007D ( 458877) cmERR_FATAL_CMN_MUTEX_LOCK Failed to invoke the mutex_lock()
system function**

**Cause:** Failed to invoke the mutex_lock() system function. This is a system
call error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x7007E ( 458878) cmERR_FATAL_CMN_MUTEX_UNLOCK Failed to invoke the
mutex_unlock() system function**

**Cause:** Failed to invoke the mutex_unlock() system function. This is a system
call error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

### ABORT

**0x71001 ( 462849) cmERR_ABORT_INVALID_MODULE Invalid module**

**Cause:** Internal error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x71003 ( 462851) cmERR_ABORT_INVALID_SESSION Invalid session**

**Cause:** Internal error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/)

**0x71004 ( 462852) cmERR_ABORT_INVALID_OPERATION Invalid operation**

**Cause:** Client version is higher than Server version or internal error occurs while interpreting protocol.

**Action:** Make sure Client version is same or lower than Server version or contact Altibase's Support Center
               (http://support.altibase.com/en/).

**0x71005 ( 462853) cmERR_ABORT_INVALID_LINK_TYPE Invalid link type**

**Cause:** Internal error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x71006 ( 462854) cmERR_ABORT_INVALID_LINK_IMPL Invalid link impl**

**Cause:** Internal error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x71008 ( 462856) cmERR_ABORT_UNSUPPORTED_LINK_IMPL Unsupported link impl**

**Cause:** Internal error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x71009 ( 462857) cmERR_ABORT_UNSUPPORTED_DISPATCHER_IMPL Unsupported
dispatcher impl**

**Cause:** Internal error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x7100A ( 462858) cmERR_ABORT_SESSION_NOT_ADDED Session not added**

**Cause:** Internal error.

**Action:** Verify that the session has been added.

**0x7100B ( 462859) cmERR_ABORT_SESSION_LIMIT_REACH Session limit reached**

**Cause:** Internal error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x7100C ( 462860) cmERR_ABORT_SESSION_DOES_NOT_EXIST Session does not exist**

**Cause:** Internal error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x7100D ( 462861) cmERR_ABORT_SOCKET_ALREADY_OPENED Socket already opened**

**Cause:** Internal error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x7100E ( 462862) cmERR_ABORT_SOCKET_OPEN_ERROR Unable to create a socket**

**Cause:** Failed to invoke the socket() system function. This is a system call
error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x7100F ( 462863) cmERR_ABORT_BIND_ERROR Unable to bind the socket,
errno=\<0%u\>**

**Cause:** Failed to invoke the bind() system function on the socket.

**Action:** Check the error number and take the appropriate action.

**0x71010 ( 462864) cmERR_ABORT_LISTEN_ERROR Failed to invoke the listen()
system function**

**Cause:** Failed to invoke the listen() system function. This is a system call
error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x71011 ( 462865) cmERR_ABORT_LINK_LIMIT_REACH Link limit reached**

**Cause:** Internal error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x71012 ( 462866) cmERR_ABORT_LINK_ALREADY_IN_DISPATCHING Link already in
dispatch**

**Cause:** Internal error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x71013 ( 462867) cmERR_ABORT_TIMED_OUT Timed out**

**Cause:** A network timeout occurred

**Action:** Check the network.

**0x71014 ( 462868) cmERR_ABORT_POLL_ERROR Failed to invoke the poll() system
function**

**Cause:** Failed to invoke the poll() system function. This is a system call
error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x71015 ( 462869) cmERR_ABORT_SELECT_ERROR Failed to invoke the select()
system function**

**Cause:** Failed to invoke the select() system function. This is a system call
error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x71016 ( 462870) cmERR_ABORT_ACCEPT_ERROR Failed to invoke the accept()
system function**

**Cause:** Failed to invoke the accept() system function. This is a system call
error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x71017 ( 462871) cmERR_ABORT_CONNECT_ERROR Failed to invoke the connect()
system function**

**Cause:** Failed to invoke the connect() system function. This is a system call
error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x71018 ( 462872) cmERR_ABORT_RECV_ERROR Failed to invoke the read() system
function**

**Cause:** Failed to invoke the read() system function. This is a system call
error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x71019 ( 462873) cmERR_ABORT_SEND_ERROR Failed to invoke the write() system
function**

**Cause:** Failed to invoke the write() system function. This is a system call
error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x7101A ( 462874) cmERR_ABORT_CONNECTION_CLOSED Connection closed**

**Cause:** The connection has been closed due to network failure or abnormal
client termination.

**Action:** Check the network or client status.

**0x7101B ( 462875) cmERR_ABORT_UNIX_PATH_TRUNCATED Unix domain socket path
truncated**

**Cause:** Unix domain socket path truncated

**Action:** The Altibase socket path is too long. Make it shorter.

**0x7101C ( 462876) cmERR_ABORT_LINK_ALREADY_REGISTERED Link already registered
to Session**

**Cause:** Link already registered to session

**Action:** Ensure that a session has been initialized and ensure that no link
is already registered.

**0x7101D ( 462877) cmERR_ABORT_PROTOCOL_HEADER_ERROR Protocol header
error.(\<0%s\>)**

**Cause:** Internal error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x7101E ( 462878) cmERR_ABORT_UNKNOWN_MODULE Unknown module**

**Cause:** Internal error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x71021 ( 462881) cmERR_ABORT_INVALID_PROTOCOL_SEQUENCE Invalid protocol
sequence**

**Cause:** Invalid protocol sequence

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x71022 ( 462882) cmERR_ABORT_INVALID_XA_XID_DATA_SIZE Invalid XA XID data
size**

**Cause:** Internal error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x71023 ( 462883) cmERR_ABORT_MARSHAL_ERROR Protocol marshal error**

**Cause:** Internal error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x71024 ( 462884) cmERR_ABORT_CALLBACK_DOES_NOT_EXIST Callback does not
exist**

**Cause:** Internal error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x71026 ( 462886) cmERR_ABORT_INCOMPLETE_VARIABLE Incomplete variable**

**Cause:** Internal error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x71027 ( 462887) cmERR_ABORT_VARIABLE_NOT_EMPTY Variable not empty**

**Cause:** Internal error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x71028 ( 462888) cmERR_ABORT_VARIABLE_PIECE_RANGE_MISMATCH Variable piece
range mismatch**

**Cause:** Internal error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x71029 ( 462889) cmERR_ABORT_VARIABLE_SEQUENCE_SIZE_MISMATCH Variable
sequence size mismatch**

**Cause:** Internal error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x7102A ( 462890) cmERR_ABORT_INVALID_VARIABLE_TYPE Invalid variable type**

**Cause:** Internal error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x7102B ( 462891) cmERR_ABORT_INVALID_DATATYPE Invalid data type**

**Cause:** Internal error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x7102D ( 462893) cmERR_ABORT_SHM_ALREADY_CREATED Shared memory for IPC
already allocated**

**Cause:** Shared memory for IPC is already allocated. This is a system call
error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x7102E ( 462894) cmERR_ABORT_NUMERIC_SIZE_OVERFLOW Numeric data size
overflow**

**Cause:** Internal error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x7102F ( 462895) cmERR_ABORT_SOCKET_SET_BLOCKING_FAILED Unable to set the
socket to blocking mode**

**Cause:** Failed to invoke the fcntl() function for setting a socket to
blocking mode. This is a system call error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x71030 ( 462896) cmERR_ABORT_SOCKET_SET_NONBLOCKING_FAILED Unable to set the
socket to non-blocking mode**

**Cause:** Failed to invoke the fcntl() function for setting a socket to
non-blocking mode. This is a system call error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com).

**0x71032 ( 462898) cmERR_ABORT_SOCKET_SHUTDOWN_FAILED Unable to shut down the
socket**

**Cause:** Failed to invoke the shutdown() system function. This is a system
call error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com).

**0x71033 ( 462899) cmERR_ABORT_UNSUPPORTED_LINK_INFO_KEY Unsupported link info
key**

**Cause:** Internal error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com).

**0x71034 ( 462900) cmERR_ABORT_GETSOCKNAME_ERROR Failed to invoke the
getsockname() system function**

**Cause:** Failed to invoke the getsockname() system function. This is a system
call error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x71036 ( 462902) cmERR_ABORT_SHARED_POOL_NOT_EXIST Shared pool does not
exist**

**Cause:** Internal error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x71037 ( 462903) cmERR_ABORT_STRING_OUTPUT_ERROR String output error**

**Cause:** Failed to invoke a string output function, such as printf(). This is
a system call error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com).

**0x7103A ( 462906) cmERR_ABORT_VARIABLE_PIECE_TOO_LARGE Variable piece too
large**

**Cause:** Internal error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x7103B ( 462907) cmERR_ABORT_VARIABLE_SIZE_MISMATCH Variable size mismatch**

**Cause:** Internal error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x7103C ( 462908) cmERR_ABORT_VARIABLE_RANGE_MISMATCH Variable range
mismatch**

**Cause:** Variable range mismatch. This is an internal bug.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x71089 ( 462985) cmERR_ABORT_CMN_MARSHAL_BUFFER_FULL Insufficient
communication buffer.**

**Cause:** The communication buffer is insufficient.

**Action:** Verify that the size of the communication buffer specified in the
property file is valid. ( e.g., \> 64KB )

**0x7108A ( 462986) cmERR_ABORT_CMN_SOCKET_CLOSED Socket communication error**

**Cause:** The socket on the client has already been closed.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x7108B ( 462987) cmERR_ABORT_CMN_ERR_FULL_IPC_CHANNEL No more IPC channels
(MAX=\<0%d\>, USED=\<1%d\>, BUFSIZE=\<2%d\>)**

**Cause:** All IPC channels have been allocated to clients.

**Action:** Use a TCP/UNIX Domain channel or create more IPC channels.

**0x7108C ( 462988) cmERR_ABORT_CMN_SEM_INIT_OP Unable to invoke the semop()
function as described in the system semaphore properties.**

**Cause:** Failed to invoke the semop() system function

**Action:** Check the system semaphore properties.

**0x71096 ( 462998) cmERR_ABORT_GETADDRINFO_ERROR Failed to invoke the
getaddrinfo() system function: \<0%s\>**

**Cause:** Failed to invoke the getaddrinfo() system function. This is a system
call error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x71097 ( 462999) cmERR_ABORT_GETNAMEINFO_ERROR Failed to invoke the
getnameinfo() system function**

**Cause:** Failed to invoke the getnameinfo() system function. This is a system
call error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x71098 ( 463000) cmERR_ABORT_SETSOCKOPT_ERROR Failed to invoke the
setsockopt() system function: \<0%s\>**

**Cause:** Failed to invoke the setsockopt() system function. This is a system
call error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x71099 ( 463001) cmERR_ABORT_CONNECT_INVALIDARG Invalid argument supplied for
connect()**

**Cause:** Invalid argument supplied for connect().

**Action:** Check the IP address and hostname.

**0x7109C ( 463004) cmERR_ABORT_SHMGET_ERROR Failed to get shared memory ID**

**Cause:** Failed to get shared memory ID with the key

**Action:** Check your platform.

**0x7109D ( 463005) cmERR_ABORT_COMPRESS_DATA_ERROR Failed to compress data in a
packet**

**Cause:** Failed to compress packet data.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x7109E ( 463006) cmERR_ABORT_DECOMPRESS_DATA_ERROR Failed to decompress data
in a packet**

**Cause:** Failed to decompress packet data.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x7109F ( 463007) cmERR_ABORT_UNSUPPORTED_NETWORK_PROTOCOL Unsupported network
protocol**

**Cause:** Unsupported network protocol

**Action:** Check the protocol version of the client application and use an
appropriate library.

**0x710A0 ( 463008) cmERR_ABORT_INVALID_CERTIFICATE Failed to load a
certificate. SSL error: \<0%s\>**

**Cause:** Failed to load a valid certificate from the file the user specified
in the altibase.properties file.

**Action:** Check whether or not the certificate and its location are valid.

**0x710A1 ( 463009) cmERR_ABORT_INVALID_PRIVATE_KEY Failed to load a private
key. SSL error: \<0%s\>**

**Cause:** Failed to load a valid private key from the file the user specified
in the altibase.properties file.

**Action:** Check whether or not the certificate and its location are valid.

**0x710A2 ( 463010) cmERR_ABORT_PRIVATE_KEY_VERIFICATION Failed to verify the
private key. SSL error: \<0%s\>**

**Cause:** Private key does not match the certificate loaded into SSL context.

**Action:** Check whether or not the private key matches the certificate.

**0x710A3 ( 463011) cmERR_ABORT_SSL_HANDSHAKE SSL handshake failed. SSL error:
\<0%s\>**

**Cause:** SSL handshake failed.

**Action:** Refer to the altibase_boot.log file for further information about
the failure.

**0x710A4 ( 463012) cmERR_ABORT_SSL_READ SSL read failed. SSL error: \<0%s\>**

**Cause:** SSL read failed.

**Action:** Refer to the altibase_boot.log file for further information about
the failure.

**0x710A5 ( 463013) cmERR_ABORT_SSL_WRITE SSL write failed. SSL error: \<0%s\>**

**Cause:** SSL write failed.

**Action:** Refer to the altobase_boot.log file for further information about
the failure.

**0x710A6 ( 463014) cmERR_ABORT_SSL_SHUTDOWN SSL shutdown failed. SSL error:
\<0%s\>**

**Cause:** SSL shutdown failed.

**Action:** Refer to the altobase_boot.log file for further information about
the failure.

**0x710A7 ( 463015) cmERR_ABORT_INVALID_VERIFY_LOCATION Failed to load trusted
certificates from the specified location(s). SSL error: \<0%s\>**

**Cause:** Failed to load trusted certificates from the specified location(s).

**Action:** Check whether the CA and/or CAPath properties are valid.

**0x710A8 ( 463016) cmERR_ABORT_INVALID_CA_LIST_FILE Failed to load trusted
certificates from the CA file. SSL error: \<0%s\>**

**Cause:** Failed to load trusted certificates from the CA file.

**Action:** Check whether or not the CA file is valid.

**0x710A9 ( 463017) cmERR_ABORT_SSL_CONNECT SSL connect failed.**

**Cause:** SSL connect failed.

**Action:** Refer to the altibase_boot.log file for further information about
the failure.

**0x710AA ( 463018) cmERR_ABORT_VERIFY_PEER_CERITIFICATE Failed to verify the
peer certificate. SSL error: \<0%s\>**

**Cause:** Failed to verify the peer certificate.

**Action:** Check whether or not the peer has a valid certificate.

**0x710AB ( 463019) cmERR_ABORT_SSL_OPERATION SSL operation failed. SSL error:
\<0%s\>**

**Cause:** SSL operation failed.

**Action:** Refer to the altibase_boot.log file for further information about
the failure.

**0x710AC ( 463020) cmERR_ABORT_DLOPEN Failed to open the \<0%s\> library.
Error: \<1%s\>**

**Cause:** Failed to open the library.

**Action:** Check whether or not the library has been installed and set
properly.

**0x710AD ( 463021) cmERR_ABORT_DLSYM Failed to load functions from the \<0%s\>
library. Error: \<1%s\>**

**Cause:** Failed to load functions from the library.

**Action:** Check whether or not the library has been installed properly.

**0x710AE (463022) cmERR_ABORT_GETSOCKOPT_ERROR Failed to invoke the
getsockopt() system function: \<0%s\>**

**Cause:** Failed to invoke the getsockopt() system function. This is a system
call error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x710AF ( 463023) cmERR_ABORT_SHARD_VERSION_MISMATCH Mismatched Shard
version.**

**Cause:** The shard versions of server and client do not correspond.

**Action:** Use the identical shard and client versions.

**0x710B0 ( 463024) cmERR_ABORT_SYSTEM_CALL_ERROR Failed to invoke the \<0%s\>
system function.**

**Cause:** Failed to invoke the system function. This is a system call error.

**Action:** Check the error number from the trace log and contact Altibase's
Support Center (http://support.altibase.com/en/).

**0x710B1 ( 463025) cmERR_ABORT_IB_RSOCKET_ALREADY_OPENED IB rsocket already
opened**

**Cause:** Internal error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x710B2 ( 463026) cmERR_ABORT_IB_RSOCKET_OPEN_ERROR Unable to create a IB
rsocket, errno=\<0%u\>**

**Cause:** Failed to invoke the rsocket() function.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x710B3 ( 463027) cmERR_ABORT_IB_RBIND_ERROR Unable to bind the IB rsocket,
errno=\<0%u\>**

**Cause:** Failed to invoke the rbind() function on the IB rsocket.

**Action:** Check the error number and take the appropriate action.

**0x710B4 ( 463028) cmERR_ABORT_IB_RLISTEN_ERROR Failed to invoke the rlisten()
function**

**Cause:** Failed to invoke the rlisten() function.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x710B5 ( 463029) cmERR_ABORT_IB_RPOLL_ERROR Failed to invoke the rpoll()
function**

**Cause:** Failed to invoke the rpoll() function.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x710B6 ( 463030) cmERR_ABORT_IB_RSELECT_ERROR Failed to invoke the rselect()
function**

**Cause:** Failed to invoke the rselect() function.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x710B7 ( 463031) cmERR_ABORT_IB_RACCEPT_ERROR Failed to invoke the raccept()
function**

**Cause:** Failed to invoke the raccept() function.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x710B8 ( 463032) cmERR_ABORT_IB_RCONNECT_INVALIDARG Invalid argument supplied
for rconnect()**

**Cause:** Invalid argument supplied for rconnect().

**Action:** Check the IP address and hostname.

**0x710B9 ( 463033) cmERR_ABORT_IB_RCONNECT_ERROR Failed to invoke the
rconnect() function, errno=\<0%u\>**

**Cause:** Failed to invoke the rconnect() function.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x710BA ( 463034) cmERR_ABORT_IB_RRECV_ERROR Failed to invoke the rread()
function**

**Cause:** Failed to invoke the rread() function.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x710BB ( 463035) cmERR_ABORT_IB_RSEND_ERROR Failed to invoke the rwrite()
function**

**Cause:** Failed to invoke the rwrite() function.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x710BC ( 463036) cmERR_ABORT_IB_RSOCKET_SHUTDOWN_FAILED Unable to shut down
the socket**

**Cause:** Failed to invoke the rshutdown() function.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x710BD ( 463037) cmERR_ABORT_IB_RSETSOCKOPT_ERROR Failed to invoke the
rsetsockopt() function: \<0%s\>**

**Cause:** Failed to invoke the rsetsockopt() function.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x710BE ( 463038) cmERR_ABORT_IB_RGETSOCKOPT_ERROR Failed to invoke the
rgetsockopt() function: \<0%s\>**

**Cause:** Failed to invoke the rgetsockopt() function.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

**0x710BF ( 463039) cmERR_ABORT_IB_RSOCKET_SET_BLOCKING_FAILED Unable to set the
IB rsocket to blocking mode**

**Cause:** Failed to invoke the rfcntl() function for setting a socket to
blocking mode.

**Action:** Contact Altibase's Support Center (http://support.altibase.com).

**0x710C0 ( 463040) cmERR_ABORT_IB_RSOCKET_SET_NONBLOCKING_FAILED Unable to set
the IB rsocket to non-blocking mode**

**Cause:** Failed to invoke the rfcntl() function for setting a socket to
non-blocking mode.

**Action:** Contact Altibase's Support Center (http://support.altibase.com).

**0x710C2 ( 463042) cmERR_ABORT_IB_RPOLL_INVALID_DIRECTION Invalid direction:
\<0%d\>**

**Cause:** Internal error.

**Action:** Contact Altibase's Support Center (http://support.altibase.com/en/).

### IGNORE

**0x72000 ( 466944) cmERR_IGNORE_NoError No CM module error**

**Cause:** This is not an error.

**Action:** You can safely ignore this error message.

**0x72038 ( 467000) cmERR_IGNORE_STRING_TRUNCATED String truncated**

**Cause:** Output string truncated.

**Action:** Ignore this error message.

### RETRY

**0x73031 ( 471089) cmERR_RETRY_SOCKET_OPERATION_WOULD_BLOCK Socket operation
would be blocked**

**Cause:** A socket is not ready for this operation

**Action:** You may safely ignore this message.

**0x730C1 ( 471233) cmERR_RETRY_IB_RSOCKET_OPERATION_WOULD_BLOCK IB rsocket
operation would be blocked**

**Cause:** A IB rsocket is not ready for this operation

**Action:** You may safely ignore this message.

13.Database Link Error Code
---------------------------

### FATAL

**0xC000F ( 786447) dkERR_FATAL_ThrMutexInit Unable to initialize a mutex**

**Cause:** The system failed to initialize a mutex.

**Action:** Check the error number in the trace log and contact your operating
system engineer.

### ABORT

**0xC1000 ( 790528) dkERR_ABORT_NotSupportOperation Not supported operation**

**Cause:** The current operation isn't supported yet.

**Action:** Verify that the current operation is valid.

**0xC1001 ( 790529) dkERR_ABORT_MEMORY_ALLOCATION Insufficient memory for
Database Link**

**Cause:** The memory manager could not allocate sufficient memory for the query
processor.

**Action:** Verify that the system has sufficient memory.

**0xC1002 ( 790530) dkERR_ABORT_DK_FUNCTION_NOT_ALLOWED This function is
executable only in an execute procedure/function statement**

**Cause:** The function was called in DML.

**Action:** Use this function only in an EXECUTE statement.

**0xC1003 ( 790531) dkERR_ABORT_DK_MISMATCHED_COLUMN_TYPE Type mismatched column
type and return type**

**Cause:** The column type and return type do not match.

**Action:** Check the column specification.

**0xC1004 ( 790532) dkERR_ABORT_DK_UNSUPPORTED_COLUMN_TYPE Not supported column
type of remote database**

**Cause:** The column type is unsupported.

**Action:** Check the column specification of database link.

**0xC1005 ( 790533) dkERR_ABORT_DK_PARSING_DBLINK_CONF_FAILED Cannot parse
dblink.conf - \<0%s\>**

**Cause:** The dblink.conf file could not be parsed.

**Action:** Check the dblink.conf file.

**0xC1006 ( 790534) dkERR_ABORT_DK_OPEN_DBLINK_CONF_FAILED Cannot open
dblink.conf**

**Cause:** The dblink.conf file could not be opened.

**Action:** Check the dblink.conf file.

**0xC1007 ( 790535) dkERR_ABORT_DK_NO_HOME_DIRECTORY The 'ALTIBASE_HOME'
environment must be set**

**Cause:** The environment variable 'ALTIBASE_HOME' is not set.

**Action:** Check the environment variable 'ALTIBASE_HOME'.

**0xC1008 ( 790536) dkERR_ABORT_DKM_SESSION_INIT_FAILED Failed to initialize a
linker data session (Session Id:\<0%d\>)**

**Cause:** The number of linker data sessions is full.

**Action:** Check the number of sessions from performance view.

**0xC1009 ( 790537) dkERR_ABORT_DKM_GTX_PREPARE_PHASE_FAILED Remote atomic
transaction in prepare phase failed**

**Cause:** There is a network problem or protocol version inconsistency between
Altibase and the AltiLinker process.

**Action:** Check the network or product version.

**0xC100A ( 790538) dkERR_ABORT_DKM_GTX_COMMIT_PHASE_FAILED Remote atomic
transaction in commit phase failed**

**Cause:** There is a network problem or protocol version inconsistency between
Altibase and the AltiLinker process.

**Action:** Check the number of sessions from performance views.

**0xC100B ( 790539) dkERR_ABORT_DK_INVALID_TX_LEVEL Invalid atomic transaction
level value for remote transaction**

**Cause:** An invalid atomic transaction level is set.

**Action:** Check this transaction information from performance view.

**0xC100C ( 790540) dkERR_ABORT_DKM_GTX_ROLLBACK_IMPOSSIBLE Cannot rollback the
remote transaction**

**Cause:** The remote server currently has the autocommit mode set to ‘On’.

**Action:** Check the atomic transaction level and the auto-commit mode of the
remote server.

**0xC100D ( 790541) dkERR_ABORT_DKT_ROLLBACK_FAILED Failed to rollback the
remote transaction**

**Cause:** There is a network problem or protocol version inconsistency between
Altibase and the AltiLinker process.

**Action:** Check the network or product version.

**0xC100E ( 790542) dkERR_ABORT_DKT_GLOBAL_COORDINATOR_NOT_EXIST The global
coordinator does not exist**

**Cause:** A global transaction can not be handled from an invalid transaction
ID.

**Action:** Check the transaction information using performance views.

**0xC1010 ( 790544) dkERR_ABORT_DKM_INVALID_DBLINK Unable to find a database
link**

**Cause:** A database link is removed or the wrong database link name is used.

**Action:** Verify that the correct database link name is being used through the
use of performance views.

**0xC1011 ( 790545) dkERR_ABORT_DKM_INVALID_REMOTE_STMT Unable to find a remote
statemtent**

**Cause:** The remote statement has finished processing.

**Action:** Check the remote statement information using performance views.

**0xC1012 ( 790546) dkERR_ABORT_DKT_INVALID_REMOTE_TX Unable to find a remote
transaction**

**Cause:** The remote transaction has finished processing.

**Action:** Check the remote transaction information using performance views.

**0xC1013 ( 790547) dkERR_ABORT_DKM_COMMIT_FAILED Failed to commit a remote
transaction**

**Cause:** A network problem occurred.

**Action:** Check the transaction or session information using performance
views, and consider using 'commit force'.

**0xC1014 ( 790548) dkERR_ABORT_DKM_ROLLBACK_IMPOSSIBLE Unable to rollback
remote transaction**

**Cause:** The autocommit mode is not set correctly, or the atomic transaction
level is set to 'remote statement execution level.'

**Action:** Check the auto-commit mode or atomic transaction level.

**0xC1015 ( 790549) dkERR_ABORT_DKM_DBLINK_ALREADY_EXIST Database link already
exists**

**Cause:** A database link already exists.

**Action:** Check the database link information using performance views.

**0xC1016 ( 790550) dkERR_ABORT_DKM_INVALID_USER_MODE Invalid user mode**

**Cause:** An input value for user mode is invalid.

**Action:** Check if the input value for the user mode is set to 'PUBLIC' or
'PRIVATE'.

**0xC1017 ( 790551) dkERR_ABORT_DKS_ALLOC_LINK [Network] Failed to allocate a
communication link**

**Cause:** Failed to create a llink object due to insufficient memory.

**Action:** Check the error number in the trace log and take appropriate action.

**0xC1018 ( 790552) dkERR_ABORT_DKS_ALLOC_CM_BLOCK [Network] Failed to allocate
a communication block**

**Cause:** Failed to allocate a memory buffer for network communication.

**Action:** Check the error number in the trace log and take appropriate action.

**0xC1019 ( 790553) dkERR_ABORT_DKS_SHUTDOWN_LINK [Network] Failed to shutdown a
communication link**

**Cause:** The other party closed the socket before the network was shut down.

**Action:** You may safely ignore this error.

**0xC101A ( 790554) dkERR_ABORT_DKS_CLOSE_LINK [Network] Failed to close a
communication link**

**Cause:** The network socket was closed.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0xC101B ( 790555) dkERR_ABORT_DKS_FREE_CM_BLOCK [Network] Failed to free a
communication read or write block**

**Cause:** An allocated memory buffer was freed.

**Action:** Check the error number and take the appropriate action.

**0xC101C ( 790556) dkERR_ABORT_DKS_FREE_LINK [Network] Failed to free a
communication link**

**Cause:** A created link object was freed.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0xC101D ( 790557) dkERR_ABORT_DKO_DBLINK_IS_BEING_USED Database link already
being used**

**Cause:** An attempt was made to shut down the database link while it was being
used by another session.

**Action:** Check the performance view for dynamic database link information.

**0xC101E ( 790558) dkERR_ABORT_DKO_DBLINK_ALREADY_EXIST Database link name
already exists**

**Cause:** There was an attempt to create a database link with a name that
already exists.

**Action:** Check the meta table and verify that the database link name does not
conflict with an existing object.

**0xC101F ( 790559) dkERR_ABORT_DKA_ACCESS_LINKER_EXEC_FILE Unable to get the
Altilinker process execution file.**

**Cause:** An AltiLinker process execution file does not exist or the wrong file
path is used.

**Action:** Can not find or access the 'ALTIBASE_HOME/bin/altilinker.jar' file.

**0xC1020 ( 790560) dkERR_ABORT_DKA_FORK_EXEC_LINKER_PROCESS Unable to execute
Altilinker process.**

**Cause:** Failed to start the AltiLinker process.

**Action:** Check whether JAVA_HOME is specified, or whether you have the
execute privilege, or whether there are too many symbolic links. If none of the
above are wrong, check the error number in the trace log and take appropriate
action.

**0xC1021 ( 790561) dkERR_ABORT_DKS_LINKER_SESSION_CONNECT [Network] Failed to
connect with Altilinker process.**

**Cause:** cmiConnectWithoutData() returned an error

**Action:** Check the network connection or verify that the AltiLinker process
running.

**0xC1022 ( 790562) dkERR_ABORT_ADLP_PROTOCOL ADLP protocol failed to work**

**Cause:** ADLP protocol error.

**Action:** Check the version of the AltiLinker process and Altibase server or
check the error number from the trace log and contact Altibase’s Support Center
(http://support.altibase.com/en/).

**0xC1023 ( 790563) dkERR_ABORT_DKP_TIMEOUT [Network] A timeout occurred**

**Cause:** Network failure.

**Action:** Check network connection or check the error number from the trace
log and contact Altibase’s Support Center (http://support.altibase.com/en/).

**0xC1024 ( 790564) dkERR_ABORT_DKP_ANALYZE_ADLP_HEADER [Network] Failed to
analyze an ADLP header**

**Cause:** Network failure or wrong protocol version

**Action:** Check network connection or check the error number from the trace
log and contact Altibase’s Support Center (http://support.altibase.com/en/).

**0xC1025 ( 790565) dkERR_ABORT_DKP_CMI_SEND [Network] Failed to send a packet**

**Cause:** cmiSend() returned an error

**Action:** Check the network connection, whether the AltiLinker process is
running or check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0xC1026 ( 790566) dkERR_ABORT_DKM_ALTILINKER_DISABLED Failed to execute
Altilinker process**

**Cause:** The user tried to start the AltiLinker process but it was disabled.

**Action:** Check the property file 'dblink.conf'.

**0xC1027 ( 790567) dkERR_ABORT_DKM_ALTILINKER_ALREAY_RUNNING Altilinker process
already running**

**Cause:** The AltiLinker process is already running.

**Action:** Check if an AltiLinker process is already running.

**0xC1028 ( 790568) dkERR_ABORT_DKM_ALTILINKER_IS_NOT_RUNNING No running
Altilinker process**

**Cause:** The AltiLinker process is not running.

**Action:** Check if an AltiLinker process is running.

**0xC1029 ( 790569) dkERR_ABORT_DTK_REMOTE_SERVER_ERROR Remote server error
occurred ( Error code: \<0%d\>, SQL state: \<1%s\>, Description: \<2%s\> )**

**Cause:** There was a remote server error caused by a syntax error in the
remote statement

**Action:** Check the syntax of the remote statement and check the remote server
error logs.

**0xC102A ( 790570) dkERR_ABORT_DKT_INVALID_JDBC_DRIVER Invalid JDBC driver**

**Cause:** The JDBC driver either does not exist or is invalid.

**Action:** Check the directory and the JDBC drivers.

**0xC102B ( 790571) dkERR_ABORT_DKT_INVALID_STMT_TYPE Invalid remote statement
type**

**Cause:** There is a misapplication of the procedure function.

**Action:** Check the syntax of the remote statement.

**0xC102C ( 790572) dkERR_ABORT_DKM_GET_ERROR_INFO Failed to get remote
statement execution error information**

**Cause:** This error was either not caused by the remote server, or was simply
not executed yet.

**Action:** Verify that the remote statement executed and check the remote
server's log files.

**0xC102E ( 790574) dkERR_ABORT_DKM_REMOTE_STMT_IS_NOT_FAILED No error for the
remote statement**

**Cause:** The function was called successfully, so there is no
remote_statement_id to pass to the REMOTE_GET_ERROR_INFO function.

**Action:** Check the result of the remote statement execution.

**0xC102F ( 790575) dkERR_ABORT_DKP_INVALID_REMOTE_STMT Invalid remote statement
id detected in protocol operation**

**Cause:** Altibase received the query results of a terminated session from
AltiLinker.

**Action:** Forcefully kill AltiLinker, then execute the ALTER DATABASE LINKER
STOP FORCE command, and then execute the ALTER DATABASE LINKER START command.

**0xC1030 ( 790576) dkERR_ABORT_DKT_GLOBAL_TX_NOT_PREPARED Global transaction
not prepared to commit**

**Cause:** Network error or internal malfunction.

**Action:** Check the network and check the error number from the trace log and
contact Altibase’s Support Center (http://support.altibase.com/en/).

**0xC1031 ( 790577) dkERR_ABORT_DKM_DBLINK_DISABLED dblink disabled**

**Cause:** Dblink disabled.

**Action:** Check the altibase.properties file and set the correct value.

**0xC1032 ( 790578) dkERR_ABORT_TRAVERSE_NOT_APPLICABLE Impossible to traverse**

**Cause:** The traverse is impossible.

**Action:** Verify that the traverse is valid.

**0xC1033 ( 790579) dkERR_ABORT_FUNCTION_NOT_AVAILABLE The function is not
available**

**Cause:**

\# - The function doesn't have to be called.

**Action:**

\# - Please make sure that the function is valid.

**0xC1034 ( 790580) dkERR_ABORT_META_IS_DIFFERENT Remote table's meta has
changed**

**Cause:** The AltiLinker process is not running.

**Action:** Check if an AltiLinker process is running.

**0xC1036 ( 790582) dkERR_ABORT_DKO_DBLINK_NOT_EXIST A database link does not
exist**

**Cause:** The specified database link does not exist.

**Action:** Verify that the correct database link was specified, or use
performance views to check for available database links.

**0xC1037 ( 790583) dkERR_ABORT_ARGUMENT_IS_NOT_CONSTANT The argument is not a
constant value**

**Cause:** The argument is not a constant value.

**Action:** Check the function's arguments.

**0xC1038 ( 790584) dkERR_ABORT_ARGUMENT_IS_NOT_PROPER_TYPE The argument is not
proper type**

**Cause:** The argument is not of the smallint or integer types.

**Action:** Check the function's arguments.

**0xC1039 ( 790585) dkERR_ABORT_DKM_INVALID_TARGET Unable to find a valid
target**

**Cause:** A database link property file is not set correctly.

**Action:** Check the JDBC driver or the URL of the target remote server in the
database link property file.

**0xC103A ( 790586) dkERR_ABORT_DKS_REMOTE_SESSION_IS_BUSY Unable to close
session, a remote node session is busy**

**Cause:** There is a currently executing remote statement.

**Action:** Check performance views to find the remote transaction or statement,
and then close the session after commiting or rolling back the remote
transaction.

**0xC103B ( 790587) dkERR_ABORT_DKM_DATA_SESSION_NOT_EXIST No linker data
session exists**

**Cause:** There is a currently executing remote statement.

**Action:** Check performance views to find the remote transaction or statement,
and then close the session after commiting or rolling back the remote
transaction.

**0xC103C ( 790588) dkERR_ABORT_DKS_SESSION_NOT_EXIST Session not exist**

**Cause:**

\# - Tried to connect using a session that does not exist

**Action:**

\# - Please check a performance view for session information and close session

**0xC103D ( 790589) dkERR_ABORT_DKM_INVALID_COLUMN Unable to find column meta**

**Cause:** Wrong column index used or this column does not exist.

**Action:** Check the 'REMOTE_GET_COLUMN_VALUE' function in the procedure.

**0xC103E ( 790590) dkERR_ABORT_DKT_REMOTE_SERVER_DISCONNECT [Network] Unable to
access a remote server**

**Cause:** An incorrect user ID or password was specified for the target remote
server, or the connection was disconnected.

**Action:** Check the TARGET item in the 'dblink.conf' configuration file or
check the connection with the target remote server.

**0xC103F ( 790591) dkERR_ABORT_DKM_COLUMN_VALUE_NULL No column value**

**Cause:** REMOTE_GET_COLUMN_VALUE\_ function is used against a column which has
no value.

**Action:** Check the procedure.

**0xC1041 ( 790593) dkERR_ABORT_DKD_REMOTE_QUERY_EMPTY Empty remote query**

**Cause:** The remote query is empty.

**Action:** Check the remote query.

**0xC1042 ( 790594) dkERR_ABORT_DKD_NO_COLUMN No column**

**Cause:** There is no column.

**Action:** Check column count and information.

**0xC1043 ( 790595) dkERR_ABORT_DKT_SAVEPOINT_ALREADY_EXIST Same savepoint name
already exists**

**Cause:** The savepoint name already exists.

**Action:** Use a different name for the savepoint.

**0xC1044 ( 790596) dkERR_ABORT_DKS_DATA_SESSION_ALREADY_EXIST A linker data
session already exists**

**Cause:** Tried to create a linker data session that already exists.

**Action:** Check the performance view for linker data session information.

**0xC1045 ( 790597) dkERR_ABORT_DKM_NOT_SUPPORT_GTX_LEVEL Not supported global
transaction level**

**Cause:** The global transaction level was set to an unsupported value.

**Action:** Check the performance view or the altibase.properties file.

**0xC1046 ( 790598) dkERR_ABORT_DKM_NOT_SUPPORT_AUTOCOMMIT_MODE Not supported
autocommit mode**

**Cause:** The autocommit mode was set to an unsupported value.

**Action:** Check the performance view or the altibase.properties file.

**0xC1047 ( 790599) dkERR_ABORT_DKT_REMOTE_STMT_TYPE Invalid remote statement
type**

**Cause:** An invalid remote statement type is being used.

**Action:** Verify that the correct remote statement type is being used, or
refer to the Database Link User’s Manual.

**0xC1048 ( 790600) dkERR_ABORT_DKD_REMOTE_TABLE_COLUMN_IS_NO_NULL Received null
value from non null column of remote table**

**Cause:** The specified column in the remote table has a NOT NULL constraint,
but a NULL value was received.

**Action:** Check whether changes have been made to the remote table's schema.

**0xC1049 ( 790601) dkERR_ABORT_DKA_PREPARE_LINKER_SHUTDOWN_FAILED Failed to
prepare AltiLinker process shutdown, AltiLinker maybe busy now**

**Cause:** The AltiLinker process is currently too busy to shut down.

**Action:** Check the the AltiLinker status using performance views, retry this
command after the AltiLinker process is finished, or use the 'FORCE' option.

**0xC104A ( 790602) dkERR_ABORT_DKT_REMOTE_NODE_SESSION_COUNT_EXCESS Cannot
create remote node session any more**

**Cause:** Too many remote node sessions exist.

**Action:** Increase the 'ALTILINKER_REMOTE_NODE_SESSION_COUNT' property or
check the error number from the trace log and contact Altibase’s Support Center
(http://support.altibase.com/en/).

**0xC104B ( 790603) dkERR_ABORT_DKM_INVALID_USER Failed to drop a database link
by invalid user**

**Cause:** A user who is not the owner of a database link tried to drop it.

**Action:** Check the ownership of the database link.

**0xC104C ( 790604) dkERR_ABORT_DKM_START_ALTILINKER_PROCESS Unable to fork
AltiLinker process**

**Cause:** Another process is using same port number or wrong property file etc.

**Action:** Verify that the correct port number or property file path is being
used.

**0xC104D ( 790605) dkERR_ABORT_DKM_CREATE_CTRL_SESSION_FAILED Failed to create
linker control session**

**Cause:** Another process is using same port number or wrong property file etc.

**Action:** Verify that the correct port number or property file path is being
used.

**0xC104E ( 790606) dkERR_ABORT_DKM_DBLINK_PROPERTIES_LOAD_FAILED Failed to load
dblink.conf**

**Cause:** The dblink property file specified is incorrect or does not exist.

**Action:** Check the formatting and contents of the dblink property file and
restart the AltiLinker process.

**0xC104F ( 790607) dkERR_ABORT_DKM_INVALID_TRANSACTION Invalid remote
transaction**

**Cause:** Couldn't find the global transaction or remote transaction

**Action:** Check the right statement id or transaction id.

**0xC1050 ( 790608) dkERR_ABORT_DKT_SAVEPOINT_NOT_EXIST Savepoint not exist**

**Cause:** The savepoint does not exist or no savepoint name entered.

**Action:** Verify that the savepoint name is correct.

**0xC1051 ( 790609) dkERR_ABORT_DKP_INVALID_SESSION_ID Invalid session id**

**Cause:** An invalid session ID was passed.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0xC1052 ( 790610) dkERR_ABORT_DKA_DO_LINKER_SHUTDOWN_FAILED [Network] Failed
to shutdown AltiLinker process**

**Cause:** Network failure

**Action:** Verify that the AltiLinker process running. If it is, check the
error number from the trace log and contact Altibase’s Support Center
(http://support.altibase.com/en/).

**0xC1053 ( 790611) dkERR_ABORT_DKM_INVALID_REMOTE_STMT_TYPE Invalid remote
statement type**

**Cause:** Tried to execute invalid remote statement type

**Action:** Check the remote statement type or string.

**0xC1054 ( 790612) dkERR_ABORT_DKM_NEXT_ROW_FAILED Failed to get next row**

**Cause:** The remote statement is already freed or the wrong statement ID was
used

**Action:** Verify the remote statement ID and that the remote statement is
active.

**0xC1055 ( 790613) dkERR_ABORT_DKM_INVALID_COLUMN_INDEX Invalid column index**

**Cause:** The wrong column index number was used.

**Action:** Check the 'REMOTE_GET_COLUMN_VALUE' function in the procedure.

**0xC1056 ( 790614) dkERR_ABORT_DKI_WRONG_LINK_NAME Invalid database link name**

**Cause:** The specified database link name is invalid.

**Action:** Check the database link name.

**0xC1057 ( 790615) dkERR_ABORT_ALTILINKER_DISCONNECTED [FAILURE] Altilinker
process disconnected**

**Cause:** The AltiLinker process was killed or disconnected.

**Action:** Verify that the AltiLinker process is active and that it is
currently connected.

**0xC1058 ( 790616) dkERR_ABORT_DKM_SET_SAVEPOINT Failed to set a savepoint to
remote server**

**Cause:** The remote node session is running in autocommit mode, or the remote
server does not support changes to the autocommit mode.

**Action:** Verify that the autocommit mode of the remote node session is set to
'OFF'.

**0xC1059 ( 790617) dkERR_ABORT_DKI_STATEMENT_IS_NULL There is no internal
statement information.**

**Cause:** Internal statement is missing.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0xC105A ( 790618) dkERR_ABORT_DKM_LINKER_DUMP_ERROR Failed to dump altilinker
information.**

**Cause:** The AltiLinker process is running abnormally.

**Action:** Verify the AltiLinker process status and the "altibase_lk.log" file.

**0xC105B ( 790619) dkERR_ABORT_DKD_INVALID_BUFFER_SIZE The buffer size is not
large enough to fetch the remote query results.**

**Cause:** The remote server record size is greater than the allocated dblink
buffer size.

**Action:** Check the DBLINK_DATA_BUFFER_BLOCK_SIZE,
DBLINK_DATA_BUFFER_BLOCK_COUNT, DBLINK_DATA_BUFFER_ALLOC_RATIO or
DBLINK_REMOTE_TABLE_BUFFER_SIZE property.

**0xC105C ( 790620) dkERR_ABORT_DKD_INTERNAL_BUFFER_FULL Insufficient memory for
the Database Link.**

**Cause:** Internal buffer for database link is full.

**Action:** Please check whether the query result is too large.

**0xC105D ( 790621) dkERR_ABORT_DKM_DBLINK_ALTILINKER_STATUS
DBLINK_ALTILINKER_STATUS is only available in the DAEMON process.**

**Cause:** DBLINK_ALTILINKER_STATUS is visible at DAEMON process.

**Action:** Please query with the SYSDBA privilege.

**0xC105E ( 790622) dkERR_ABORT_DKN_GET_ADDR_INFO_ERROR An error occurred while
receiving address information over the network.**

**Cause:** There is error while getting address info.

**Action:** Please check network status.

**0xC105F ( 790623) dkERR_ABORT_DKN_OPEN_SOCKET_ERROR A network error
occurred.**

**Cause:** An error occurred while opening the socket.

**Action:** Please check network status.

**0xC1060 ( 790624) dkERR_ABORT_DKN_SELECT_SOCKET_ERROR A network error
occurred.**

**Cause:** An error occurred while selecting the socket.

**Action:** Please check network status.

**0xC1063 ( 790627) dkERR_ABORT_DKN_SEND_SOCKET_ERROR An error occurred while
sending data over the network.**

**Cause:** An error occurred while sending data to the socket.

**Action:** Please check network status.

**0xC1064 ( 790628) dkERR_ABORT_DKN_RECV_SOCKET_ERROR An error occurred while
receiving data over the network.**

**Cause:** An error occurred while receiving data from the socket.

**Action:** Please check network status.

**0xC1065 ( 790629) dkERR_ABORT_DKN_WRONG_HEADER_SIGN The ADLP protocol header
is wrong.**

**Cause:** The communication protocol header is invalid.

**Action:** Please check the network or product version.

**0xC1066 ( 790630) dkERR_ABORT_DKT_INVALID_COLUMN_INDEX Invalid column index**

**Cause:** The wrong column index number was used.

**Action:** Check the 'REMOTE_GET_RESULT_BATCH' function in the procedure.

**0xC1067 ( 790631) dkERR_ABORT_DKT_INVALID_REMOTE_STMT_TYPE Invalid remote
statement type**

**Cause:** Tried to execute invalid remote statement type

**Action:** Check the remote statement type or string.

**0xC1068 ( 790632) dkERR_ABORT_XA_APPLY_FAIL Fail notifier application. Result
type = \<0%u\>, Global tx id = \<1%lu\>.**

**Cause:** There's network error or remote server failure.

**Action:** Please check network and remote server's status.

**0xC1069 ( 790633) dkERR_ABORT_DKM_CAN_NOT_CHANGE_GTX_LEVEL It can not change
transaction level while global transaction is running.**

**Cause:** There's running global transaction.

**Action:** Please try again after finish global transaction.

**0xC106B ( 790635) dkERR_ABORT_DKM_CANNOT_SET_SAVEPOINT It cannot set a
savepoint to remote server in global transaction level 2.**

**Cause:** Global transaction level is 2.

**Action:** Please check global transaction level.

**0xC106C ( 790636) dkERR_ABORT_DKA_JAVA_EXEC_ERR Java binary which can execute
the Altilinker process cannot be found [ \<0%s\>: \<1%s\> ].**

**Cause:** Either java has not been installed or JAVA_HOME has been incorrectly
configured, otherwise, the system privilege does not exist.

**Action:**

\# - The Java binary with the system privilege is required to execute the
process.

\# - To do that, install JRE on a machine where AltiLinker would be operating,
and then configure the installation path of JRE in JAVA_HOME environment
variables or verify the system privilege if it has already been installed.

**0xC106D ( 790637) dkERR_ABORT_DKA_JAVA_HOME_ERR altilinker cannot be executed
since the environment variables of JAVA_HOME has not been configured yet.**

**Cause:** The Java_HOME environment variables are not configured.

**Action:** Accurately configure the installation path in which JRE is installed
in the JAVA_HOME environment variables.

**0xC106E ( 790638) dkERR_ABORT_DKT_ALTILINKER_XAEXCEPTION XAException
occurred.**

**Cause:** XAException occured from Altilinker process.

**Action:** Check XAException message in altibase_lk file and take appropriate
action.

**0xC106F ( 790639) dkERR_ABORT_DKM_NOT_EXECUTE_DML Failed to execute a DML
because the global transaction has been terminated.**

**Cause:**

\# - After failed to commit in global transaction level 2, do not execute a DML
statement to a remote server.

**Action:**

\# - Execute rollback and try again.

### **RETRY**

**0xC3035 ( 798773) dkERR_REBUILD_META_IS_DIFFERENT Remote table's meta has
changed**

**Cause:** The AltiLinker process is not running.

**Action:** Check if an AltiLinker process is running.

14.Log Analyzer Error Code
--------------------------

### **FATAL**

**0x50008 ( 327688) ulaERR_FATAL_TX_ALREADY_BEGIN Transaction has already begun
[\<0%u\>:\<1%u\>]**

**Cause:** Transaction already exists in the Transaction ID's slot.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x5000A ( 327690) ulaERR_FATAL_MUTEX_INITIALIZE Failed to initialize mutex
[\<0%s\>]**

**Cause:** Failed to initialize a mutex.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x5000B ( 327691) ulaERR_FATAL_MUTEX_DESTROY Failed to destroy mutex
[\<0%s\>]**

**Cause:** Failed to destroy a mutex.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x5000C ( 327692) ulaERR_FATAL_MUTEX_LOCK Failed to lock mutex [\<0%s\>]**

**Cause:** Failed to lock a mutex.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x5000D ( 327693) ulaERR_FATAL_MUTEX_UNLOCK Failed to unlock mutex [\<0%s\>]**

**Cause:** Failed to unlock a mutex.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com).

### **ABORT**

**0x51006 ( 331782) ulaERR_ABORT_MEMORY_ALLOC Memory allocation failure**

**Cause:** Insufficient memory.

**Action:** Check the amount of free memory.

**0x51012 ( 331794) ulaERR_ABORT_META_NOT_EXIST The meta information does not
exist.**

**Cause:** The meta information does not exist.

**Action:** Check the Altibase Log Analysis API.

**0x51015 ( 331797) ulaERR_ABORT_NET_TIMEOUT Network timeout [\<0%s\>]**

**Cause:** A network timeout occurred.

**Action:** Check the Altibase Log Analysis API.

**0x51016 ( 331798) ulaERR_ABORT_NET_READ Network read failure [\<0%s\>,
\<1%u\>]**

**Cause:** Network or Altibase Log Analysis API problem.

**Action:** Check the network and environment variables.

**0x51017 ( 331799) ulaERR_ABORT_NET_EXIT Already exited network session
[\<0%s\>]**

**Cause:** The network exit flag has already been set.

**Action:** Check the Altibase Log Analysis API.

**0x51018 ( 331800) ulaERR_ABORT_NET_UNEXPECTED_PROTOCOL Unexpected network
protocol [\<0%s\>]**

**Cause:** Invalid protocol.

**Action:** Check the replication protocol version.

**0x5101B ( 331803) ulaERR_ABORT_NET_WRITE Network write failure [\<0%s\>,
\<1%u\>]**

**Cause:** Network or Altibase Log Analysis API problem.

**Action:** Check the network and environment variables.

**0x5101C ( 331804) ulaERR_ABORT_NET_FLUSH Network flush failure [\<0%s\>,
\<1%u\>]**

**Cause:** Network or Altibase Log Analysis API problem.

**Action:** Check the network and environment variables.

**0x5101E ( 331806) ulaERR_ABORT_MEM_POOL_ALLOC Memory allocation failure in
pool**

**Cause:** The memory pool for XLogs is exhausted.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x51020 ( 331808) ulaERR_ABORT_MEM_POOL_INITIALIZE Failed to initialize memory
pool**

**Cause:** Failed to allocate a memory pool for XLogs.

**Action:** Verify that there is enough available memory.

**0x51022 ( 331810) ulaERR_ABORT_LINK_SHUTDOWN Failed to shut down link**

**Cause:** Failed to shut down network.

**Action:** You may safely ignore this message.

**0x51023 ( 331811) ulaERR_ABORT_LINK_FREE Failed to free link**

**Cause:** Failed to free network memory.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com).

**0x51024 ( 331812) ulaERR_ABORT_PROTOCOL_DIFF Different protocol versions**

**Cause:** The replication protocol version is different from that of XLog
Sender.

**Action:** Check the version of the XLog Sender protocol.

**0x51027 ( 331815) ulaERR_ABORT_LINK_ALLOC Failed to allocate link**

**Cause:** Failed to allocate network resources.

**Action:** Verify that there are enough available system resources. Take
appropriate action if necessary.

**0x51028 ( 331816) ulaERR_ABORT_LINK_LISTEN Failed to listen for link**

**Cause:** Failed to listen to a connection on a socket.

**Action:** Check the port status.

**0x51029 ( 331817) ulaERR_ABORT_LINK_WAIT Failed to wait for link**

**Cause:** Failed while waiting for a link.

**Action:** Check the network status.

**0x5102A ( 331818) ulaERR_ABORT_LINK_ACCEPT Failed to accept link**

**Cause:** Failed to accept a connection on a socket.

**Action:** Check the network status.

**0x5103F ( 331839) ulaERR_ABORT_TABLE_NOT_FOUND Table Not Found [\<0%s\>,
\<1%lu\>]**

**Cause:** Failed to retrieve table information from the XLog Collector.

**Action:** Use the XLog Collector that has information of the table or check
the application logic.

**0x51040 ( 331840) ulaERR_ABORT_COLUMN_NOT_FOUND Column Not Found [\<0%s\>,
\<1%u\>]**

**Cause:** Failed to retrieve the column from the XLog Collector.

**Action:** Use the XLog Collector that has information of the table column or
check the application logic.

**0x51041 ( 331841) ulaERR_ABORT_NOT_INIT_TXTABLE Transaction table not
initialized**

**Cause:** The transaction table was not initialized.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x51042 ( 331842) ulaERR_ABORT_NO_ENV_VARIABLE Environment variable \<0%s\> is
not set**

**Cause:** Environment variable cannot be found.

**Action:** Set the environment variable.

**0x51043 ( 331843) ulaERR_ABORT_NullSourceData Found that source data was NULL,
when converting MT source data to CM data**

**Cause:** The data source contains an Altibase Value that is NULL.

**Action:** Check that the application has properly passed the Altibase Value
when using the API.

**0x51044 ( 331844) ulaERR_ABORT_InvalidMantissaLength The mantissa length(
\<%d\> ) of source data exceeds the limit of mantissa length**

**Cause:** The data source contains invalid Numeric data.

**Action:** Check whether the data source has been passed properly.

**0x51045 ( 331845) ulaERR_ABORT_INVALID_DATA_CONVERSION Invalid data
conversion**

**Cause:** Invalid data source.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x51046 ( 331846) ulaERR_ABORT_NUMERIC_CONVERSION_OVERFLOW Numeric conversion
overflow**

**Cause:** An overflow occurred while converting to the numeric data type
because it exceeded the range.

**Action:** Check the data type and whether the value is within range.

**0x51047 ( 331847) ulaERR_ABORT_MEM_ALLOC_GET_INSTANCE Failed to create an
instance of the memory allocator [\<0%s\>]**

**Cause:** Failed to instantiate the memory allocator object.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x51048 ( 331848) ulaERR_ABORT_MEM_ALLOC_SET_ATTR Failed to set memory
allocator attributes [\<0%s\>]**

**Cause:** Failed to set attributes on the memory allocator object.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x51049 ( 331849) ulaERR_ABORT_ALLOC_CM_BLOCK Failed to allocate communication
block [\<0%s\>]**

**Cause:** Failed to allocate memory.

**Action:** Verify that there is enough available memory.

**0x5104A ( 331850) ulaERR_ABORT_FREE_CM_BLOCK Failed to free communication
block [\<0%s\>]**

**Cause:** Failed to free memory.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x5104B ( 331851) ulaERR_ABORT_INSUFFICIENT_XLOG_POOL ALA XLog Collector
cannot receive allocable XLog because the XLog in XLog Pool is all consumed.**

**Cause:**

\# - There is no XLog that is available for use in the XLog Pool.

**Action:**

\# - In order to receive the allocable XLog in ALA Application, restart ALA
sender after raising the values of ALA_XLOG_POOL_SIZE. Refer to Adapter for
Oracle User’s Manual for more

### IGNORE

**0x52000 ( 335872) ulaERR_IGNORE_LOG_MGR_INITIALIZE Failed to initialize log
manager**

**Cause:** Failed to initialize the Log Manager.

**Action:** Verify that the file path is correct and that you have permission
for the file. Check disk space.

**0x52001 ( 335873) ulaERR_IGNORE_LOG_FILE_OPEN Failed to open log file**

**Cause:** Failed to open the log file.

**Action:** Check the maximum number of files that can be open. Verify that the
file path is correct and that you have permission for the file.

**0x52002 ( 335874) ulaERR_IGNORE_LOG_FILE_CLOSE Failed to close log file**

**Cause:** Failed to close the log file.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x52003 ( 335875) ulaERR_IGNORE_LOG_MGR_DESTROY Failed to detroy log manager**

**Cause:** Failed to destroy the Log Manager.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x52004 ( 335876) ulaERR_IGNORE_LOG_MGR_LOCK Failed to lock log manager**

**Cause:** Internal API error.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x52005 ( 335877) ulaERR_IGNORE_LOG_MGR_UNLOCK Failed to unlock log manager**

**Cause:** Internal API error.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x52007 ( 335879) ulaERR_IGNORE_GEMOETRY_ENDIAN Endian conversion of geometry
type failed [\<0%s\>, \<1%u\>]**

**Cause:** This is an internal API error.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x52009 ( 335881) ulaERR_IGNORE_NOT_ACTIVE_TX Inactive transaction [\<0%u\>]**

**Cause:** Transaction is not active.

**Action:** Check Altibase Log Analysis API.

**0x5200E ( 335886) ulaERR_IGNORE_LINKEDLIST_NOT_EMPTY Linked list is not
empty.**

**Cause:** Internal API error.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com).

**0x5200F ( 335887) ulaERR_IGNORE_PARAMETER_NULL Null parameter [\<0%s\>]**

**Cause:** Input or output parameter is null.

**Action:** Check Altibase Log Analysis API.

**0x52010 ( 335888) ulaERR_IGNORE_INVALID_ROLE Invalid Role [\<0%d\>]**

**Cause:** Altibase Log Analysis API supports only XLog Sender.

**Action:** Check XLog Sender DDL.

**0x52011 ( 335889) ulaERR_IGNORE_INVALID_REPLICATION_FLAGS Invalid replication
flags [\<0%u\>]**

**Cause:** Unsupported protocol.

**Action:** You may safely ignore this message.

**0x52014 ( 335892) ulaERR_IGNORE_NET_TIMEOUT Network timeout [\<0%s\>]**

**Cause:** A network timeout occurred.

**Action:** Check the Altibase Log Analysis API.

**0x5201D ( 335901) ulaERR_IGNORE_PARAMETER_INVALID Invalid parameter
[\<0%s\>]**

**Cause:** A parameter is invalid.

**Action:** Check Altibase Log Analysis API.

**0x52025 ( 335909) ulaERR_IGNORE_SOCKET_TYPE_NONE Socket type not selected**

**Cause:** The socket type has not been selected.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x52026 ( 335910) ulaERR_IGNORE_SOCKET_TYPE_NOT_SUPPORT Socket type not
supported**

**Cause:** The socket type is not supported.

**Action:** Check the Altibase Log Analysis API.

**0x5202D ( 335917) ulaERR_IGNORE_XLOG_SENDER_NAME_DIFF Different XLog Sender
name [\<0%s\>:\<1%s\>]**

**Cause:** The local XLog sender name is different from the remote name.

**Action:** Check the XLog Sender DDL and Log Analysis API.

**0x5202E ( 335918) ulaERR_IGNORE_SOCKET_ALREADY_INITIALIZE Socket already
initialized**

**Cause:** Socket can be initialized only once.

**Action:** Check the Altibase Log Analysis API.

**0x5202F ( 335919) ulaERR_IGNORE_SOCKET_NOT_SUPPORT_API Socket does not support
API**

**Cause:** The socket does not support the API.

**Action:** Check the Altibase Log Analysis API.

**0x52030 ( 335920) ulaERR_IGNORE_AUTH_INFO_ONE One piece of authentication
information is needed**

**Cause:** The TCP socket type needs at least one piece of authentication
information.

**Action:** Check the Altibase Log Analysis API.

**0x52031 ( 335921) ulaERR_IGNORE_AUTH_INFO_MAX Amount of authentication
information already reached maximum**

**Cause:** The amount of authentication information has already reached the
maximum.

**Action:** Check the Altibase Log Analysis API.

**0x52032 ( 335922) ulaERR_IGNORE_AUTH_FAIL Authentication failure**

**Cause:** Peer authentication information do not exist.

**Action:** Check the Altibase Log Analysis API.

**0x52033 ( 335923) ulaERR_IGNORE_XLOG_POOL_EMPTY XLog pool is empty.**

**Cause:** XLog pool is empty.

**Action:** Check the Altibase Log Analysis API.

**0x52035 ( 335925) ulaERR_IGNORE_API_DESTROY Global termination failed**

**Cause:** Invalid ALA_Handle.

**Action:** Check the ALA_Handle.

**0x52036 ( 335926) ulaERR_IGNORE_MTD_MODULE_GET Failed to get MTD Module
[\<0%s\>, \<1%u\>]**

**Cause:** This is an internal error.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x52037 ( 335927) ulaERR_IGNORE_MTD_ENCODE Failed to encode MTD Module
[\<0%s\>]**

**Cause:** This is an internal error.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x52039 ( 335929) ulaERR_IGNORE_CMT_FINALIZE Failed to finalize CMT**

**Cause:** This is an internal API error.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x5203A ( 335930) ulaERR_IGNORE_DIAG_HEADER_CREATE Failed to create diagnostic
header**

**Cause:** This is an internal API error.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x5203B ( 335931) ulaERR_IGNORE_DIAG_HEADER_DESTROY Failed to destroy
diagnostic header**

**Cause:** This is an internal API error.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x5203C ( 335932) ulaERR_IGNORE_MT_TO_CMT_CONVERT Failed to convert MT value
to CMT value**

**Cause:** This is an internal API error.

**Action:** Check the error number from the trace log and contact Altibase’s
Support Center (http://support.altibase.com/en/).

**0x5203E ( 335934) ulaERR_IGNORE_COLUMN_TO_ODBC_CONVERT Failed to convert
ulnColumn value to ODBC C value**

**Cause:** Failed to convert the column passed as an argument to a datatype
supported by ODBC.

**Action:** Refer to the log file specified for ALA_EnableLogging and pass a
data type supported by ODBC.
