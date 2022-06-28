

- [altiShapeLoader User's Manual](#altishapeloader-users-manual)
  - [Preface](#preface)
    - [About This Manual](#about-this-manual)
- [1. Introduction to altiShapeLoader](#1-introduction-to-altishapeloader)
  - [Overview](#overview)
  - [altiShapeLoader Version](#altishapeloader-version)
  - [System Requirements](#system-requirements)
  - [Installing and Removing](#installing-and-removing)
- [2. How to Use altiShapeLoader](#2-how-to-use-altishapeloader)
  - [Altibase Prerequisites - Registering SRID](#altibase-prerequisites---registering-srid)
  - [Execution Options](#execution-options)
  - [Mandatory Options](#mandatory-options)
  - [Elective Options](#elective-options)
  - [Performance Option](#performance-option)
  - [Special Options](#special-options)
  - [Importing Shapefile](#importing-shapefile)
  - [Exporting Shapefile](#exporting-shapefile)
  - [Importing and Exporting SRID](#importing-and-exporting-srid)
- [3. Constraints](#3-constraints)
    - [Shapefile Constraints](#shapefile-constraints)
    - [GeoTools Constraints](#geotools-constraints)
- [4. Converting Data Types](#4-converting-data-types)
    - [Converting Importing Data Types](#converting-importing-data-types)
    - [Converting Exporting Data Types](#converting-exporting-data-types)



# altiShapeLoader User's Manual

[![img](media/altiShapeLoader/e5cfb3761673686d093a3b00c062fe7a.png)](media/altiShapeLoader/e5cfb3761673686d093a3b00c062fe7a.png)

Altibase Tools & Utilities altiShapeLoader User's Manual

Release 1.0

Copyright ⓒ 2001~2021 Altibase Corp. All Rights Reserved.

This manual contains proprietary information of Altibase Corporation; it is provided under a license agreement containing restrictions on use and disclosure and is also protected by copyright patent and other intellectual property law. Reverse engineering of the software is prohibited. All trademarks, registered or otherwise, are the property of their respective owners.

**Altibase Corp**

10F, Daerung PostTower II, 306, Digital-ro, Guro-gu, Seoul 08378, Korea Telephone: +82-2-2082-1000 Fax: 82-2-2082-1099

Customer Service Portal: http://support.altibase.com/en/

Homepage: [[http://www.altibase.com](http://www.altibase.com/)]

## Preface

### About This Manual

This manual provides information on altiShapeLoader that allows importing and exporting a shapefile<sup>[1](#shapefile)</sup>, a standard file format for geographic information systems(GIS), that contains spatial data information to the Altibase server.

#### Audience

This manual has been prepared for the following users of Altibase:

- Database administrators
- Performance administrators
- Database users
- Application developers
- Technical Supporters

It is recommended for those reading this manual possess the following background knowledge:

- Basic knowledge in the use of computers, operating systems, and operating system utilities
- Experience in using relational database and an understanding of database concepts
- Computer programming experience
- Experience in database server management, operating system management, or network administration
- Knowledge related to the storage, management and processing of data in distributed environments

#### Organization

This manual is organized as follows:

- Chapter 1: Introduction to altiShapeLoader
   This chapter illustrates altiShapeLoader's features and how to install it.
- Chapter 2: Getting started
  This chapter explains basic concepts that makes using altiShapeLoader easier and how to use altiShapeLoader in CLI mode.
- Chapter 3: Constraints
- Chapter 4: Converting data type
  - Converting importing data type
  - Converting exporting data type

#### Documentation Conventions

This section describes the conventions used in this manual. Understanding these conventions will make it easier to find information in this manual and in the other manuals in the series.

This convention described here is as follow:

- Sample Code Convention

##### Sample Code Conventions

The code examples explain SQL statements, stored procedures, iSQL statements, and other command line syntax.

The following table describes the printing conventions used in the code examples.

| Rules            | Meaning                                                      | Example                                                      |
| ---------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| [ ]              | Indicates an optional item                                   | VARCHAR [(*size*)] [[FIXED \|] VARIABLE]                     |
| { }              | Indicates a mandatory field for which one or more items must be selected. | { ENABLE \| DISABLE \| COMPILE }                             |
| \|               | A delimiter between optional or mandatory arguments.         | { ENABLE \| DISABLE \| COMPILE } [ ENABLE \| DISABLE \| COMPILE ] |
| . . .            | Indicates that the previous argument is repeated, or that sample code has been omitted. | SQL> SELECT ename FROM employee; ENAME ----------------------- SWNO HJNO HSCHOI . . . 20 rows selected. |
| Other Symbols    | Symbols other than those shown above are part of the actual code. | EXEC :p1 := 1; acc NUMBER(11,2)                              |
| Italics          | Statement elements in italics indicate variables and special values specified by the user. | SELECT * FROM *table_name*; CONNECT *userID*/*password*;     |
| Lower case words | Indicate program elements set by the user, such as table names, column names, file names, etc. | SELECT ename FROM employee;                                  |
| Upper case words | Keywords and all elements provided by the system appear in upper case. | DESC SYSTEM_.SYS_INDICES_;                                   |

#### Related Documentations

For more detailed information, please refer to the following documents.

- Installation Guide
- Getting Started Guide
- Administrator’s Manual
- Replication Manual
- Precompiler User’s Manual
- API User’s Manual
- Altibase C Interface Manual
- iSQL User’s Manual
- Utilities Manual
- General Reference
- Error Message Reference

#### Altibase Welcomes Your Comments and Feedbacks

Please let us know what you like or dislike about our manuals. To help us with better future versions of our manuals, please tell us if there is any corrections or classifications that you would find useful.

Include the following information:

- The name and version of the manual that you are using
- Any comments about the manual
- Your name, address, and phone number

If you need immediate assistance regarding any errors, omissions, and other technical issues, please contact [Altibase's Support Portal](http://support.altibase.com/en/).

Thank you. We always welcome your feedbacks and suggestions.

# 1. Introduction to altiShapeLoader

This chapter explains system requirements, installation, and environment configuration for altiShapeLoader.

### Overview

altiShapeLoader is a tool used to import and export shapefile<sup>[1](#shapefile)</sup>, which is programmed based on GeoTools, open-source library based on Java.

Importing shapefile means inserting spatial data information such as coordinate information and property information from a shapefile into a Altibase database table. Exporting shapefile means creating a shapefile using spatial data information stored in Altibase database table.

### altiShapeLoader Version

The version of altiShapeLoader is 1.0. Version information can be found in the version.info file under the installation directory.

### System Requirements

System requirements to install and run altiShapeLoader and Altibase server version that is compatible with altiShapeLoader are as belows.

#### Hardware Requirements

- Main memory: Minimum 512MB, 4GB or more recommended
- Disk: More than 20MB of free space for installation

#### Software Requirements

- Java: Oracle, OpenJDK or IBM Java Runtime Environment 8 or higher
- OS: 64bit OS Java can be installed and run

#### Compatible Altibase version

- Altibase 7.1 or higher

### Installing and Removing

#### Installing altiShapeLoader

Download altiShapeLoader-1.0.zip from http://support.altibase.com/en/product. Unzip the file where altiShapeLoader will be run and check the altiShapeLoader directory.

altiShapeLoader directory contains following files.

```
[altibase@ /data/altibase/altiShapeLoader]$ ls -l
-rw-rw-r-- 1 altibase altibase 27438 2021-10-08 13:19 Altibase_altiShapeLoader_1_0_Release_Notes.pdf
-rw-r--r-- 1 altibase altibase  1318 2021-10-08 11:27 altiShapeLoader.bat
-rw-r--r-- 1 altibase altibase  1177 2021-10-08 11:27 altiShapeLoader.properties.release
-rw-rw-r-- 1 altibase altibase   867 2021-10-08 11:27 altiShapeLoader.sh
-rw-r--r-- 1 altibase altibase   798 2021-10-08 11:27 epsg.properties
drwxr-xr-x 2 altibase altibase  4096 2021-10-08 11:27 lib
drwxr-xr-x 2 altibase altibase  4096 2021-10-08 11:27 license
-rw-r--r-- 1 altibase altibase   560 2021-10-08 11:27 log4j2.xml
```

##### Execution File

If the server running altiShapeLoader is in the Windows environment, choose altiShapeLoader.bat and if it is in the Unix/Linux environment, choose altiShapeLoader.sh.

#### altiShapeLoader Configuration

##### JAVA_HOME Environment Variables

JAVA_HOME environment variables has to be set up since altiShapeLoader is programmed with Java. Please refer to [system requirements](#system-requirements) to check the java version required to run altiShapeLoader.

```
$ export JAVA_HOME=/usr/java/1.8
$ $JAVA_HOME/bin/java -version
java version "1.8.0_101"
Java(TM) SE Runtime Environment (build 1.8.0_101-b13)
Java HotSpot(TM) 64-Bit Server VM (build 25.101-b13, mixed mode)
```

##### altiShapeLoader Configuration File (altiShapeLoader.properties)

altiShapeLoader configuration file (altiShapeLoader.properties) is required when running altiShapeLoader. Create the file by duplicating altiShapeLoader.properties.release in the altiShapeLoader directory and edit according to the use.

```
$ cd altiShapeLoader
$ cp -p altiShapeLoader.properties.release altiShapeLoader.properties
```

#### Removing altiShapeLoader

Remove altiShapeLoader directory.

```
$ rm -fr altiShapeLoader
```

## 2. How to Use altiShapeLoader

This chapter explains how to use altiShapeLoader.

### Altibase Prerequisites - Registering SRID

Spatial Reference Identifier (SRID) is a unique identifier that indicates the coordinate system in which a spatial object is defined. It is stored in SYSTEM\_.USER_SRS_ meta table (hereinafter synonym SPATIAL_REF_SYS) in Altibase server.

SRID is required to provide correct coordination information when importing a shapefile. Among the files composing a shapefile, .prj file contains SRID information and this SRID has to be inserted into SPATIAL_REF_SYS before importing a shapefile.

##### Checking the SRID registered in the Altibase server

SRID registered in the Altibase server can be found by the following query.

```
SELECT * FROM SPATIAL_REF_SYS;
```

##### Registering SRID in Altibase server

SYS_SPATIAL.ADD_SPATIAL_REF_SYS procedure is used to register the SRID .prj file contains when it is not registered in the Altibase server.

- SYS_SPATIAL.ADD_SPATIAL_REF_SYS procedure is available when Altibase stored package SYS_SPATIAL is created. Altibase stored package should be created with the SYS user as the owner.

  When SYS_SPATIAL.ADD_SPATIAL_REF_SYS procedure does not exist, the following error occurs when executing altiShapeLoader.

  ```
  [Preparing & analyzing metadata]
  com.altibase.gis.lib.util.AltiException: Failed to ensure condtitions to insert a new SRID into database
  - Unable to find target package [SYS_SPATIAL]
  ```

- EXECUTE ANY PROCEDURE authority should be granted to the database user running altiShapeLoader to execute ADD_SPATIAL_REF_SYS procedure.

  ```
  -- When the database user is altitest
  iSQL> GRANT EXECUTE ANY PROCEDURE TO altitest;
  ```

Please refer to Spatial SQL Reference for more information on how to use SYS_SPATIAL.ADD_SPATIAL_REF_SYS.

- [Altibase 7.2 Spatial SQL Reference](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.2/eng/Spatial SQL Reference.md#add_spatial_ref_sys)
- [Altibase 7.1 Spatial SQL Reference](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/eng/Spatial SQL Reference.md#add_spatial_ref_sys)

### Execution Options

Execution options such as Altibase server connection information, type of the task, table name and shapefile path should be entered in order to run altiShapeLoader. There are two ways to do this.

#### Entering Execution Options

- ##### Command Line Interface (CLI)

  This process enters altiShapeLoader execution options in the command line interface in batch mode. It is used when different options have to be applied to each shapefile.

- ##### Using altiShapeLoader Configuration File

  Execution options will be applied by reading altiShapeLoader's configuration file, altiShapeLoader.properties. This file is created by duplicating altiShapeLoader.properties.release and renaming it to altiShapeLoader.properties. It has to be in the same directory as altiShapeLoader's execution file such as altiShapeLoader.sh or altiShapeLoader.bat.

  Altibase server connection information and all the other common options use this altiShapeLoader configuration file.

#### Priorities in Setting Execution options

Execution options should be set in the following order.

1. Command line interface
2. altiShapeLoader configuration file
3. Predefined default values

For example, if the table name is defined as T1 in the command line interface and T2 in the altiShapeLoader configuration file when importing a shapefile, T1 will be applied due to its higher priority. If the table name was not defined in both options, the default value specified in altiShapeLoader which is the name of .shp file will be applied.

Below is an example demonstrating entering common importing options such as Altibase server connection information in altiShapeLoader configuration file, type of the task, table name and path of each shapefile in command line interface.

```
% cat ./altiShapeLoader.properties.release
###############################################
# DB connection arguments 
###############################################
DB_IP         = 127.0.0.1
DB_PORT        = 20300
DB_NAME        = mydb
DB_USER     = SYS
DB_PASSWORD    = MANAGER
JDBC_PATH     = ${ALTIBASE_HOME}/lib/Altibase.jar

###############################################
# General options
###############################################
# CREATE_TABLE      = T
# TABLE_TBS         = SYS_TBS_DISK_DATA
# CREATE_INDEX      = F
# INDEX_TBS         = SYS_TBS_DISK_DATA
# DBF_CHAR          = EUC-KR
# ENDIAN            = B
# CASE_SENSIITIVE   = F
# CREATE_BAD        = F

###############################################
# Performance options
###############################################
# PARALLEL         = 4
# COMMIT        = 1000

###############################################
# Mandatory arguments
###############################################
# OPERATION     = import 
### Use / instead of \ when specifying Windows file path.
# SHAPE_FILE    = ./sample.shp
# TABLE_NAME    = T1

###############################################
# Special options
###############################################
#GEO_COL_SIZE   = 103809024
#SRID           = 2097

% cp altiShapeLoader.properties.release altiShapeLoader.properties

% ./altiShapeLoader.sh -o import -f subway_station.shp -T subway_station
-----------------------------------------------------------------
        altiShapeLoader Release 1.0
        Shapefile import/export utility for Altibase datatbase
        Copyright(c) 2000, ALTIBASE Corporation or its subsidiaries.
        All Rights Reserved.
-----------------------------------------------------------------
...
```

### Mandatory Options

Mandatory options should be entered either in the command line interface or altiShapeLoader configuration file. If these options are omitted, an error will occur and the task will be canceled. "Command line option" will enter the option in -option_name format in command line interface and "altiShapeLoader configuration file option" will enter the option in OPTION_NAME=value format in altiShapeLoader configuration file.

It is recommended to manually input the following two options into the command line interface since they differ for each shapefile.

| Command Line Option | altiShapeLoader Configuration File Option | Description                                                  |
| ------------------- | ----------------------------------------- | ------------------------------------------------------------ |
| -o                  | OPERATION                                 | Enter the type of the task (import or export) altiShapeLoader will perform.<br />Import means the spatial data information will be inserted into the table from the shapefile. Import can be done in three ways. Please refer to [importing shapefile](#importing-shapefile) for more detailed information.<br />-  Single shapefile into single table <br />- Multiple shapefiles into single table<br />- Multiple shapefiles into each tables<br />Export stores the spatial data information stored in the table in the shapefile. Please refer to [exporting shapefile](#exporting-shapefile) for more detailed information. |
| -f                  | SHAPE_FILE                                | Select the directory path the shapefile exists or the .shp file that includes the path. <br />- An example of selecting the .shp file that includes the path: -f subway_station.shp <br />- An example of selecting the directory the shapefile exists: -f multi2single |

On top of that, Altibase server connection information is also a mandatory option. If it is used frequently, add it in the altiShapeLoader configuration file.

| Command Line Option | altiShapeLoader Configuration File Option | Description                                                  |
| ------------------- | ----------------------------------------- | ------------------------------------------------------------ |
| -s                  | DB_IP                                     | The hostname or the IP address of the OS Altibase server is installed |
| -port               | DB_PORT                                   | The service port number of the Altibase server               |
| -d                  | DB_NAME                                   | Database name (ex. mydb)                                     |
| -u                  | DB_USER                                   | Database user ID                                             |
| -p                  | DB_PASSWORD                               | Database user password                                       |
| -j                  | JDBC_PATH                                 | Altibase JDBC driver file path to be used for the connection (ex. ./Altibase.jar) |

### Elective Options

These options are electively entered by the user according to the type of the task. If it is not entered either in command line interface or altiShapeLoader configuration file, the default value will be applied.

| Command Line Option | altiShapeLoader Configuration File Option | Description                                                  | Default Value         |
| ------------------- | ----------------------------------------- | ------------------------------------------------------------ | --------------------- |
| -t                  | TABLE_NAME                                | Specifies the table name.<br />If the -o option is import, this indicates the table spatial data will be inserted into. If the -create_table option is T and this option is omitted, the table name will be the same as the .shp file's name. For example, if the .shp file's name is test.shp, the table name will be 'test'. Case sensitivity will be decided by the case_sensitive option. <br />If the -o option is export, it indicates the table the spatial data is stored in. | Shapefile name        |
| -create_table       | CREATE_TABLE                              | If the -o option is import, it decides whether to create the table.<br />Valid values for this option are T and F. <br />When the option is set to T, a table that has FID(Feature ID) as its first column will be created. Also, a sequence object (SEQ_*table_name*_FID) will be created for the records to get their own FID values. If there is a sequence object with the same name in the database, this will not be created. <br />When the option is set to F, the table will not be created. | T                     |
| -table_tbs          | TABLE_TBS                                 | Specifies the tablespace name where the table will be created. When this option is omitted, it will be created in the default tablespace of the database user. This option is only effective when the -create_table option is set to T. | Default tablespace    |
| -create_index       | CREATE_INDEX                              | Specifies whether to create index in the spatial data type column. <br />Valid values for this option are T and F. <br />T creates the index and F does not. This option is only effective when the -create_table option is set to T. | F                     |
| -index_tbs          | INDEX_TBS                                 | Specifies the tablespace name where the index will be created. When this option is omitted, it will be created in the default tablespace of the database user. This option is only effective when the -create_index option is set to T. | Default tablespace    |
| -dbf_char           | DBF_CHAR                                  | Specifies the character set to be encoded when reading .dbf file to import or export a shapefile. The same character set will be applied to the altiShapeLoader configuration file and column name mapping file (please refer to -col_map_file option). | EUC-KR                |
| -endian             | ENDIAN                                    | Specifies the endian type of the shapefile. <br />Valid values for this option are B and L. B stands for big endian and L stands for little endian. <br />This option is only effective when the -o option is set to import. | B                     |
| -case_sensitive     | CASE_SENSITIVE                            | Specifies the case sensitivity of the table and column name. <br />Valid values for this option are T and F. <br />When this option is set to T, the exact value the user entered will be inserted and when it is set to F, the value the user entered will be converted to all capitals. | F                     |
| -col_map_file       | COL_MAP_FILE                              | Specifies the path of the column name mapping file. <br />Column name mapping file is a text file the user creates in key=value format when creating table column's name different from the one defined in the shapefile. <br />It is written in shpColName=dbColName format and when there is no value, the table is created with the column name defined in the shapefile. Case sensitivity will be decided by the case_sensitive option. | Shapefile column name |
| -create_bad         | CREATE_BAD                                | Specifies whether to create a bad file logging records that have failed importing or exporting. <br />Valid values for this option are T and F. <br />When this value is set to T, records that have failed to import or export will be logged to the specified file. bad file name is *shapefile name*.bad format. When the -o option is import, the number of the bad file can be created up to the value of the parallel option. When there are no failed records, bad file will not be created. When this option is set to F, bad file is not created regardless of the import or export failure. | F                     |

### Performance Option

These options adjust the altiShapeLoader's importing performance. For the best performance, appropriate adjustment is required according to the CPU and memory of the system altiShapeLoader is installed.

| Command Line Option | altiShapeLoader Configuration File Option | Description                                                  | Default Value |
| ------------------- | ----------------------------------------- | ------------------------------------------------------------ | ------------- |
| -parallel           | PARALLEL                                  | The number of threads inserting data. <br />This is an option to adjust the importing performance. altiShapeLoader is a multi-thread structure in a producer-consumer pattern. It is composed of one producer thread that reads the shapefile and puts it in the queue and N amount of consumer threads that read the data from the queue and insert it into the database. Here, parallel option means N amount of consumer threads. The minimum value is 1 and there is no limit to the maximum value. When this option is omitted, the default value, which is 4, will be applied. | 4             |
| -commit             | COMMIT                                    | The number of records to commit per commit when inserting data. <br />This option is used to adjust the importing performance. It decides how many records will be committed per commit by the thread inserting data. The minimum value is 1 and there is no limit to the maximum value. When this option is omitted, the default value, which is 1000, will be applied. | 1000          |

### Special Options

These options are used for special purposes only and it is not recommended to use them otherwise.

| Command Line Option | altiShapeLoader Configuration File Option | Description                                                  | Default Value      |
| ------------------- | ----------------------------------------- | ------------------------------------------------------------ | ------------------ |
| -srid               | SRID                                      | The SRID value the user force specifies. <br />This SRID value will be force specified when the .prj file cannot be processed. For more detailed instruction, please refer to [importing and exporting SRID](#importing-and-exporting-srid). | N/A                |
| -geo_col_size       | GEO_COL_SIZE                              | Specifies the precision of the geometry data column when creating a table. The unit is byte. It is only used when column bigger than the default value is necessary. | 103,809,024 (99MB) |

### Importing Shapefile

Importing is a task inserting spatial information from .shp file and property information from .dbf file which are shapefile's component into a table. This requires files that compose a shapefile such as .shp, .shx, .dbf and .prj. Before importing, SRID has to be registered in the Altibase server. For more information about this, please refer to [Altibase prerequisites - registering SRID](#Altibase-Prerequisites---Registering-SRID).

There are three ways to import.

1. Single shapefile into single table
2. Multiple shapefiles into single table
3. Multiple shapefiles into each tables

Mandatory options for each task are as belows.

| Command Line Option | altiShapeLoader Configuration File Option | Single shapefile into single table | Multiple shapefiles into single table | Multiple shapefiles into each tables |
| :------------------ | :---------------------------------------- | :--------------------------------: | :-----------------------------------: | :----------------------------------: |
| -o                  | OPERATION                                 |                 O                  |                   O                   |                  O                   |
| -f                  | SHAPE_FILE                                |                 O                  |                   O                   |                  O                   |
| -t                  | TABLE_NAME                                |                 △                  |                   O                   |                  X                   |

#### Single Shapefile into Single Table

The most common way is by importing a shapefile, which is composed of .shp, .shx, .dbf and others, into a single table. OPERATION(-o) and SHAPE_FILE(-f) are mandatory options. Insert a .shp format file into the SHAPE_FILE (-f) option. TABLE_NAME (-t) option is optional.

Below is an example of importing a shapefile composed of subway_station.shb, subway_station.shx, subway_station.dbf into a single table.

```bash
$ ls -l data/subway_station.*
-rw-r--r-- 1 altibase altibase 287186 Apr 28  2021 data/subway_station.dbf
-rw-r--r-- 1 altibase altibase    758 Apr 28  2021 data/subway_station.prj
-rw-r--r-- 1 altibase altibase    758 Apr 28  2021 data/subway_station.prj.bak
-rw-r--r-- 1 altibase altibase   3052 Apr 28  2021 data/subway_station.sbn
-rw-r--r-- 1 altibase altibase   7716 Apr 28  2021 data/subway_station.shp
-rw-r--r-- 1 altibase altibase   2276 Apr 28  2021 data/subway_station.shx

$ ./altiShapeLoader.sh -o import -f data/subway_station.shp
-----------------------------------------------------------------

        altiShapeLoader Release 1.0
        Shapefile import/export utility for Altibase datatbase
        Copyright(c) 2000, ALTIBASE Corporation or its subsidiaries.
        All Rights Reserved.

-----------------------------------------------------------------

Importing shp requested: /home/altiShapeLoader/data/subway_station.shp
[Preparing & analyzing metadata]
[CREATE SEQUENCE] CREATE SEQUENCE "ALTITEST"."SEQ_SUBWAY_STATION_FID" START WITH 1 INCREMENT BY 1 MINVALUE 1 CYCLE
[CREATE SEQUENCE] Success
[CREATE TABLE] CREATE TABLE "ALTITEST"."SUBWAY_STATION" ( FID BIGINT DEFAULT "SEQ_SUBWAY_STATION_FID".NEXTVAL PRIMARY KEY, "THE_GEOM" GEOMETRY(103809024) SRID 2097, "XCOORD" DOUBLE, "YCOORD" DOUBLE, "GUBUN" VARCHAR(254), "GUBUN2" VARCHAR(254), "NAM" VARCHAR(254), "NAM2" VARCHAR(254) )
[CREATE TABLE] Success
[Importing data started] A single dot (.) means 1,000 records processed.
.
[Importing data done]
<summary>
[File  ] /home/altiShapeLoader/data/subway_station.shp 
[Status] [Read] Success, [Write] Success 
[Read  ] Total:272, Success:272, Fail:0 
[Write ] Total:272, Success:272, Fail:0 
[Time  ] 0:00:00.138 (HH:MM:SS.sss)
```

SEQ_SUBWAY_STATION_FID sequence and SUBWAY_STATION table are created and spatial data are inserted into the SUBWAY_STATION table even though table names are not defined by the -t option because altiShapeLoader configuration file (altiShapeLoader.properties) includes CREATE_TABLE=T by default.

Every 1000 records, one dot is printed between [DATA IMPORT START] and [DATA IMPORT DONE]. The number of records in this example is 32, so 1 dot is printed.

The result is printed in \<summary>.

- \[Status][Read] Success, \[Write] Success
  - Reading shapefile and inserting it into the table have succeeded.
- [Read  ] Total:272, Success:272, Fail:0 
  - Read 272 data successfully. 
- [Write ] Total:272, Success:272, Fail:0 
  - Read and inserted 272 data into the table successfully.
- [Time  ] 0:00:00.124 
  - Time elapsed when reading and inserting the shapefile into the table. This is printed in hh:mm:ss.sss format.

#### Multiple Shapefiles into Single Table

This inserts multiple shapefiles into a single table. Shapefiles have to be in the same directory and should have the same schema. OPERATION(-o), SHAPE_FILE(-f) and TABLE_NAME (-t) are mandatory options. The directory path is entered in SHAPE_FILE(-f) option.

The example below is importing three shapefiles in multi2single directory into MULTI2SINGLE table. Since altiShapeLoader configuration file (altiShapeLoader.properties) includes CREATE_TABLE=T by default, SEQ_MULTI2SINGLE_FID sequence and MULTI2SINGLE table are created and it will be imported into MULTI2SINGLE table.

```bash
$ ls -l data/multi2single
Total 100
-rw-r--r-- 1 altibase altibase   426 2021-04-28 09:07 river.dbf
-rw-r--r-- 1 altibase altibase   758 2021-05-14 09:33 river.prj
-rw-r--r-- 1 altibase altibase 20648 2021-04-28 09:07 river.shp
-rw-r--r-- 1 altibase altibase   340 2021-04-28 09:07 river.shx
-rw-r--r-- 1 altibase altibase   645 2021-04-28 09:07 river2.dbf
-rw-r--r-- 1 altibase altibase   758 2021-05-14 09:34 river2.prj
-rw-r--r-- 1 altibase altibase 20080 2021-04-28 09:07 river2.shp
-rw-r--r-- 1 altibase altibase   332 2021-04-28 09:07 river2.shx
-rw-r--r-- 1 altibase altibase   645 2021-04-28 09:07 river3.dbf
-rw-r--r-- 1 altibase altibase   758 2021-05-14 09:34 river3.prj
-rw-r--r-- 1 altibase altibase 20080 2021-04-28 09:07 river3.shp
-rw-r--r-- 1 altibase altibase   332 2021-04-28 09:07 river3.shx

$ ./altiShapeLoader.sh -o import -f data/multi2single -t MULTI2SINGLE
-----------------------------------------------------------------

        altiShapeLoader Release 1.0
        Shapefile import/export utility for Altibase datatbase
        Copyright(c) 2000, ALTIBASE Corporation or its subsidiaries.
        All Rights Reserved.

-----------------------------------------------------------------

Importing shp requested: /home/altiShapeLoader/data/multi2single/river.shp
[Preparing & analyzing metadata]
[CREATE SEQUENCE] CREATE SEQUENCE "ALTITEST"."SEQ_MULTI2SINGLE_FID" START WITH 1 INCREMENT BY 1 MINVALUE 1 CYCLE
[CREATE SEQUENCE] Success
[CREATE TABLE] CREATE TABLE "ALTITEST"."MULTI2SINGLE" ( FID BIGINT DEFAULT "SEQ_MULTI2SINGLE_FID".NEXTVAL PRIMARY KEY, "THE_GEOM" GEOMETRY(103809024) SRID 2097, "ID" BIGINT )
[CREATE TABLE] Success
[Importing data started] A single dot (.) means 1,000 records processed.
.
[Importing data done]
<summary>
[File  ] /home/altiShapeLoader/data/multi2single/river.shp 
[Status] [Read] Success, [Write] Success 
[Read  ] Total:30, Success:30, Fail:0 
[Write ] Total:30, Success:30, Fail:0 
[Time  ] 0:00:00.071 (HH:MM:SS.sss)

Importing shp requested: /home/altiShapeLoader/data/multi2single/river2.shp
[Preparing & analyzing metadata]
[Importing data started] A single dot (.) means 1,000 records processed.
.
[Importing data done]
<summary>
[File  ] /home/altiShapeLoader/data/multi2single/river2.shp 
[Status] [Read] Success, [Write] Success 
[Read  ] Total:29, Success:29, Fail:0 
[Write ] Total:29, Success:29, Fail:0 
[Time  ] 0:00:00.029 (HH:MM:SS.sss)

Importing shp requested: /home/altiShapeLoader/data/multi2single/river3.shp
[Preparing & analyzing metadata]
[Importing data started] A single dot (.) means 1,000 records processed.
.
[Importing data done]
<summary>
[File  ] /home/altiShapeLoader/data/multi2single/river3.shp 
[Status] [Read] Success, [Write] Success 
[Read  ] Total:29, Success:29, Fail:0 
[Write ] Total:29, Success:29, Fail:0 
[Time  ] 0:00:00.053 (HH:MM:SS.sss)
```

#### Multiple Shapefiles into Each Tables

This inserts multiple shapefiles into each table. Shapefiles have to be in the same directory and should have the same schema. Mandatory options are OPERATION(-o) and SHAPE_FILE(-f) and the directory path is entered in SHAPE_FILE(-f) option. Since the file will be named after the table, TABLE_NAME (-t) is not used in this case. When this option is used, 'multiple shapefiles into single table' will be performed.

Below is an example of importing four shapefiles in the multi2multi directory into each table. Since the altiShapeLoader configuration file (altiShapeLoader.properties) includes CREATE_TABLE=T by default, four sequences and BUILDING, FIRESTATION, HEALTHCENTER and POLICESTATION tables will each be created and the shapefiles will be imported.

```bash
$ ls -l data/multi2multi
Total 16064
-rw-r--r-- 1 altibase altibase 10877274 2021-04-28 09:07 building.dbf
-rw-r--r-- 1 altibase altibase      758 2021-04-28 09:07 building.prj
-rw-r--r-- 1 altibase altibase  5234704 2021-04-28 09:07 building.shp
-rw-r--r-- 1 altibase altibase   204356 2021-04-28 09:07 building.shx
-rw-r--r-- 1 altibase altibase     6538 2021-04-28 09:07 firestation.dbf
-rw-r--r-- 1 altibase altibase      758 2021-04-28 09:07 firestation.prj
-rw-r--r-- 1 altibase altibase      328 2021-04-28 09:07 firestation.qix
-rw-r--r-- 1 altibase altibase      332 2021-04-28 09:07 firestation.sbn
-rw-r--r-- 1 altibase altibase      124 2021-04-28 09:07 firestation.sbx
-rw-r--r-- 1 altibase altibase      744 2021-04-28 09:07 firestation.shp
-rw-r--r-- 1 altibase altibase      284 2021-04-28 09:07 firestation.shx
-rw-r--r-- 1 altibase altibase     6818 2021-04-28 09:07 healthcenter.dbf
-rw-r--r-- 1 altibase altibase      758 2021-04-28 09:07 healthcenter.prj
-rw-r--r-- 1 altibase altibase      332 2021-04-28 09:07 healthcenter.qix
-rw-r--r-- 1 altibase altibase      340 2021-04-28 09:07 healthcenter.sbn
-rw-r--r-- 1 altibase altibase      124 2021-04-28 09:07 healthcenter.sbx
-rw-r--r-- 1 altibase altibase      772 2021-04-28 09:07 healthcenter.shp
-rw-r--r-- 1 altibase altibase      292 2021-04-28 09:07 healthcenter.shx
-rw-r--r-- 1 altibase altibase    11202 2021-04-28 09:07 policestation.dbf
-rw-r--r-- 1 altibase altibase      758 2021-04-28 09:07 policestation.prj
-rw-r--r-- 1 altibase altibase      364 2021-04-28 09:07 policestation.qix
-rw-r--r-- 1 altibase altibase      468 2021-04-28 09:07 policestation.sbn
-rw-r--r-- 1 altibase altibase      156 2021-04-28 09:07 policestation.sbx
-rw-r--r-- 1 altibase altibase      996 2021-04-28 09:07 policestation.shp
-rw-r--r-- 1 altibase altibase      356 2021-04-28 09:07 policestation.shx

$ ./altiShapeLoader.sh -o import -f data/multi2multi
-----------------------------------------------------------------

        altiShapeLoader Release 1.0
        Shapefile import/export utility for Altibase datatbase
        Copyright(c) 2000, ALTIBASE Corporation or its subsidiaries.
        All Rights Reserved.

-----------------------------------------------------------------

Importing shp requested: /home/altiShapeLoader/data/multi2multi/building.shp
[Preparing & analyzing metadata]
[CREATE SEQUENCE] CREATE SEQUENCE "ALTITEST"."SEQ_BUILDING_FID" START WITH 1 INCREMENT BY 1 MINVALUE 1 CYCLE
[CREATE SEQUENCE] Success
[CREATE TABLE] CREATE TABLE "ALTITEST"."BUILDING" ( FID BIGINT DEFAULT "SEQ_BUILDING_FID".NEXTVAL PRIMARY KEY, "THE_GEOM" GEOMETRY(103809024) SRID 2097, "UFID" VARCHAR(28), "BLD_NM" VARCHAR(100), "DONG_NM" VARCHAR(100), "GRND_FLR" INTEGER, "UGRND_FLR" INTEGER, "PNU" VARCHAR(19), "ARCHAREA" DOUBLE, "TOTALAREA" DOUBLE, "PLATAREA" DOUBLE, "HEIGHT" DOUBLE, "STRCT_CD" VARCHAR(2), "USABILITY" VARCHAR(5), "BC_RAT" DOUBLE, "VL_RAT" DOUBLE, "BLDRGST_PK" VARCHAR(28), "USEAPR_DAY" VARCHAR(8), "REGIST_DAY" VARCHAR(8), "GB_CD" VARCHAR(2), "VIOL_BD_YN" VARCHAR(1) )
[CREATE TABLE] Success
[Importing data started] A single dot (.) means 1,000 records processed.
..........................
[Importing data done]
<summary>
[File  ] /home/altiShapeLoader/data/multi2multi/building.shp 
[Status] [Read] Success, [Write] Success 
[Read  ] Total:25,532, Success:25,532, Fail:0 
[Write ] Total:25,532, Success:25,532, Fail:0 
[Time  ] 0:00:00.951 (HH:MM:SS.sss)

Importing shp requested: /home/altiShapeLoader/data/multi2multi/firestation.shp
[Preparing & analyzing metadata]
[CREATE SEQUENCE] CREATE SEQUENCE "ALTITEST"."SEQ_FIRESTATION_FID" START WITH 1 INCREMENT BY 1 MINVALUE 1 CYCLE
[CREATE SEQUENCE] Success
[CREATE TABLE] CREATE TABLE "ALTITEST"."FIRESTATION" ( FID BIGINT DEFAULT "SEQ_FIRESTATION_FID".NEXTVAL PRIMARY KEY, "THE_GEOM" GEOMETRY(103809024) SRID 2097, "NAM" VARCHAR(25), "ADDR" VARCHAR(254) )
[CREATE TABLE] Success
[Importing data started] A single dot (.) means 1,000 records processed.
.
[Importing data done]
<summary>
[File  ] /home/altiShapeLoader/data/multi2multi/firestation.shp 
[Status] [Read] Success, [Write] Success 
[Read  ] Total:23, Success:23, Fail:0 
[Write ] Total:23, Success:23, Fail:0 
[Time  ] 0:00:00.053 (HH:MM:SS.sss)

Importing shp requested: /home/altiShapeLoader/data/multi2multi/healthcenter.shp
[Preparing & analyzing metadata]
[CREATE SEQUENCE] CREATE SEQUENCE "ALTITEST"."SEQ_HEALTHCENTER_FID" START WITH 1 INCREMENT BY 1 MINVALUE 1 CYCLE
[CREATE SEQUENCE] Success
[CREATE TABLE] CREATE TABLE "ALTITEST"."HEALTHCENTER" ( FID BIGINT DEFAULT "SEQ_HEALTHCENTER_FID".NEXTVAL PRIMARY KEY, "THE_GEOM" GEOMETRY(103809024) SRID 2097, "NAM" VARCHAR(25), "ADDR" VARCHAR(254) )
[CREATE TABLE] Success
[Importing data started] A single dot (.) means 1,000 records processed.
.
[Importing data done]
<summary>
[File  ] /home/altiShapeLoader/data/multi2multi/healthcenter.shp 
[Status] [Read] Success, [Write] Success 
[Read  ] Total:24, Success:24, Fail:0 
[Write ] Total:24, Success:24, Fail:0 
[Time  ] 0:00:00.051 (HH:MM:SS.sss)

Importing shp requested: /home/altiShapeLoader/data/multi2multi/policestation.shp
[Preparing & analyzing metadata]
[CREATE SEQUENCE] CREATE SEQUENCE "ALTITEST"."SEQ_POLICESTATION_FID" START WITH 1 INCREMENT BY 1 MINVALUE 1 CYCLE
[CREATE SEQUENCE] Success
[CREATE TABLE] CREATE TABLE "ALTITEST"."POLICESTATION" ( FID BIGINT DEFAULT "SEQ_POLICESTATION_FID".NEXTVAL PRIMARY KEY, "THE_GEOM" GEOMETRY(103809024) SRID 2097, "NAM" VARCHAR(50), "ADDR" VARCHAR(254), "TEL" VARCHAR(20), "FAX" VARCHAR(20) )
[CREATE TABLE] Success
[Importing data started] A single dot (.) means 1,000 records processed.
.
[Importing data done]
<summary>
[File  ] /home/altiShapeLoader/data/multi2multi/policestation.shp 
[Status] [Read] Success, [Write] Success 
[Read  ] Total:32, Success:32, Fail:0 
[Write ] Total:32, Success:32, Fail:0 
[Time  ] 0:00:00.048 (HH:MM:SS.sss)
```

### Exporting Shapefile

Export is a feature storing the spatial data information stored in the table in the shapefile. When export is performed, .shp, .shx, .dbf and other files composing a shapefile will be created.

altiShapeLoader will create a .prj file via GeoTools library by referring to SRID of the spatial object stored in the table and the SPATIAL_REF_SYS meta table. FID column of the table is not exported so it will not be stored in the shapefile.

Mandatory options are OPERATION(-o) and SHAPE_FILE(-f) and .shp format file will be entered in SHAPE_FILE(-f) option. If TABLE_NAME (-t) is omitted, shapefile will be named after the table.

#### Example of Export

Below is an example exporting spatial data information stored in POLICESTATION table to policestation2.shp file.

```bash
$ ls -l policestation2*
ls: cannot access policestation2*: No such file or directory

$ ./altiShapeLoader.sh -o export -t POLICESTATION -f ./policestation2.shp
-----------------------------------------------------------------

        altiShapeLoader Release 1.0
        Shapefile import/export utility for Altibase datatbase
        Copyright(c) 2000, ALTIBASE Corporation or its subsidiaries.
        All Rights Reserved.

-----------------------------------------------------------------

Exporting requested: ./policestation2.shp
[Preparing files & analyzing metadata]
[Exporting data started] A single dot (.) means 1,000 records processed.
.
[Exporting data done]
<summary>
[File  ] ./policestation2.shp 
[Status] [Read] Success, [Write] Success 
[Read  ] Total:32, Success:32, Fail:0 
[Write ] Total:32, Success:32, Fail:0 
[Time  ] 0:00:00.342 (HH:MM:SS.sss)
```

Every 1000 records, one dot is printed between \<commit started> and \<finished>. The number of records in this example is 32, so 1 dot is printed.

- \[Status][Read] Success, \[Write] Success
  - Reading shapefile and inserting it into the table have succeeded.
- [Read  ] Total:32, Success:32, Fail:0 
  - Read 32 data successfully. 
- [Write ] Total:32, Success:32, Fail:0 
  - Read and inserted 32data into the table successfully.
- [Time  ] 0:00:01.287
  - Time elapsed when reading and inserting the shapefile into the table. This is printed in hh:mm:ss.sss format.

The result of creating a shapefile after performing export is as belows.

```
$ ls -l policestation2*
-rw-rw-rw- 1 altibase altibase 11201 Nov 21 21:38 policestation2.dbf
-rw-rw-rw- 1 altibase altibase   397 Nov 21 21:38 policestation2.fix
-rw-rw-rw- 1 altibase altibase   737 Nov 21 21:38 policestation2.prj
-rw-rw-rw- 1 altibase altibase   996 Nov 21 21:38 policestation2.shp
-rw-rw-rw- 1 altibase altibase   356 Nov 21 21:38 policestation2.shx

$ file policestation2*
policestation2.dbf: DBase 3 data file (32 records)
policestation2.fix: data
policestation2.prj: ASCII text, with very long lines, with no line terminators
policestation2.shp: ESRI Shapefile version 1000 length 498 type Point
policestation2.shx: ESRI Shapefile version 1000 length 178 type Point
```

### Importing and Exporting SRID

#### Importing SRID

SRID information is required to provide the correct coordinate system when importing a shapefile. If the two factors below are prepared, the user does not have to enter SRID information manually since altiShapeLoader reads and analyzes the .prj file and enters spatial data, including SRID information.

- .prj file

  SRID is logged in .prj file which is one of shapefile's components. This file is required to enter SRID information correctly when importing a shapefile.

- SPATIAL_REF_SYS table

  SRID stored in .prj file has to be entered in SPATIAL_REF_SYS table.

However, in the two following cases, the user has to manually enter SRID information using the user-defined file (epsg.properties) or the -srid option.

- No .prj file

  Although the SPATIAL_REF_SYS table contains SRID, if shapefile is imported without a.prj file, the below error occurs in the log in the [Preparing & analyzing metadata] phase.

  ```bash
  Unable to find the target prj file: /home/altiShapeLoader/data/subway_station.prj
  Unable to parse the given prj file and no user input SRID
  ```

- .prj file analyzation failed

  altiShapeLoader cannot analyze SRID although the.prj file exists and the SPATIAL_REF_SYS table contains SRID. altiShapeLoader analyzes SRID by referring to the library GeoTools provides (gt-epsg-hsql-xx.jar) and the user-defined file (epsg.properties). In this case, SRID does not exist in these referring files. The below error occurs in the log in the [Preparing & analyzing metadata] phase when importing a shapefile.

  ```bash
  [SRID] Failed to parse or find EPSG code: 
  /home/altiShapeLoader/data/bld.prj
  Unable to parse the given prj file and no user input SRID
  ```

Below is an example of importing a shapefile named bld that has an GRS80 ellipsoid coordinate system SR-ORG:7846 as its SRID. However, this value does not exist in EPSG code. SRID 7846 has to be entered into the SPATIAL_REF_SYS table in prior.

- SRID has to be entered into the SPATIAL_REF_SYS table in prior.

  ```sql
  -- Enter SRID into the SPATIAL_REF_SYS metatable.
  -- SRID and AUTH_SRID should have same value.
  
  iSQL> EXEC SYS_SPATIAL.ADD_SPATIAL_REF_SYS ( 7846, 'SR-ORG', 7846, 'PROJCS["PCS_ITRF2000_TM",GEOGCS["GCS_ITRF_2000",DATUM["D_ITRF_2000",SPHEROID["GRS_1980",6378137.0,298.257222101]],PRIMEM["Greenwich",0.0],UNIT["Degree",0.0174532925199433]],PROJECTION["Transverse_Mercator"],PARAMETER["False_Easting",1000000.0],PARAMETER["False_Northing",2000000.0],PARAMETER["Central_Meridian",127.5],PARAMETER["Scale_Factor",0.9996],PARAMETER["Latitude_Of_Origin",38.0],UNIT["Meter",1.0]]', 'Proj4js.defs["SR-ORG:7846"] = "+proj=tmerc +lat_0=38 +lon_0=127 +k=1 +x_0=200000 +y_0=0 +ellps=GRS80 +towgs84=0,0,0,0,0,0,0 +units=m +no_defs";' );
  Execute success.
  
  iSQL> SELECT SRID, AUTH_NAME, AUTH_SRID FROM SPATIAL_REF_SYS WHERE AUTH_SRID = '7846';
  
  SRID        AUTH_NAME   AUTH_SRID   
  ----------------------------------------
  
  7846        SR-ORG      7846        
  1 row selected.
  ```

- **Using user-defined file(epsg.properties)**

  Add SRID in SRID-WKT format to the epsg.properties file. This file has to be in the altiShapeLoader directory.

  ```bash
  $ cat epsg.properties
  7846=PROJCS["PCS_ITRF2000_TM",GEOGCS["GCS_ITRF_2000",DATUM["D_ITRF_2000",SPHEROID["GRS_1980",6378137.0,298.257222101]],PRIMEM["Greenwich",0.0],UNIT["Degree",0.0174532925199433]],PROJECTION["Transverse_Mercator"],PARAMETER["False_Easting",1000000.0],PARAMETER["False_Northing",2000000.0],PARAMETER["Central_Meridian",127.5],PARAMETER["Scale_Factor",0.9996],PARAMETER["Latitude_Of_Origin",38.0],UNIT["Meter",1.0]]
  
  $ altiShapeLoader.sh -o import -f data/bld.shp
  ```

- **Using -srid option**

  Specify -srid option in the execution option when importing a shapefile.

#### Exporting SRID

When exporting a shapefile, along the .shp file, .prj file which contains SRID information is created. By referring to AUTH_SRID stored in the table, altiShapeLoader writes .prj file via GeoTools.

# 3. Constraints

Since altiShapeLoader is programmed based on GeoTools, an open-source library based on Java, GeoTools' constraints apply to altiShapeLoader as well.

### Shapefile Constraints

- A shapefile can only have one spatial data column (geometry) and one type of spatial data. (More than one type cannot be stored together. For example, polygon and line.)
- The size of each component of shapefile is only supported up to 2GB.
- The name of the property field cannot exceed 10 characters.
- The maximum number of the property field is 255 and any property fields exceeding this will be ignored.
- Only four data types are supported: NUMBER, FLOAT, CHARACTER(255), DATE

The above constraints can be also found on https://desktop.arcgis.com/en/arcmap/latest/manage-data/shapefiles/geoprocessing-considerations-for-shapefile-output.htm.

### GeoTools Constraints

Please refer to the link below to see the GeoTools constraints.

- https://docs.geotools.org/stable/userguide/library/data/shape.html

# 4. Converting Data Types

The tables below show data type conversions between Altibase and a shapefile. The data information in a shapefile is stored in a .dbf file in dBASE format. Remember that the supported data type or precision may vary depending on the shapefile version.

### Converting Importing Data Types

| Data Type | dBASE field      | Altibase                | Note                                                         |
| --------- | ---------------- | ----------------------- | ------------------------------------------------------------ |
| NUMBER    | NUMBER           | INTEGER, BIGINT, DOUBLE | Altibase data type is decided based on the dBase field's precision and whether it has scale. If is does, it is converted to DOUBLE type. If not, in case the precision is from 1 to 9, it is converted to INTEGER type. If the precision is greater than 10, it is converted to BIGINT type. |
| CHARACTER | CHARACTER        | VARCHAR                 | -                                                            |
| DATE      | DATE             | DATE                    | TIME type is not supported by dBASE.                         |
| BOOLEAN   | BOOLEAN(Logical) | VARCHAR(1)              | Altibase does not support BOOLEAN type. From the dbf file, T or F value will be imported as 'T' or 'F' and the remainder(1/0/null) will be processed as NULL. |

### Converting Exporting Data Types

| Data Type | Altibase                                               | dBASE field (precision) | Note                                                         |
| :-------: | :----------------------------------------------------- | :---------------------- | :----------------------------------------------------------- |
|  NUMBER   | SMALLINT, INTEGER, BIGINT                              | NUMBER                  | Precision will be specified according to the Altibase data type and the scale is 0. |
|  NUMBER   | REAL, NUMBER, NUMERIC, DOUBLE, FLOAT                   | NUMBER                  | Specifies the precision and the scale according to the Altibase data type. |
| CHARACTER | CHAR, VARCHAR                                          | CHARACTER               | The maximum value of dBASE character is 255.                 |
| CHARACTER | NCHAR, NVARCHAR                                        | Unsupported             | -                                                            |
|   DATE    | DATE                                                   | DATE                    | Altibase supports TIME.<br />dBASE does not support TIME.    |
|  BINARY   | BINARY, BIT, VARBIT, BYTE, VARBYTE, NIBBLE, CLOB, BLOB | Unsupported             | -                                                            |

---

<a name="shapefile">1</a>  The shapefile format is a standard file format in geographic information system field. It is developed by a geographic information system software development company Esri. Three files below are required to compose a shapefile.

- .shp: vector format file that stores the feature geometry such as point, line and plane
- .shx: index file that stores the position of individual feature IDs in the .shp file
- .dbf: The dBASE table that stores the attribute information of features

cf. [Geoprocessing considerations for shapefile output](https://desktop.arcgis.com/en/arcmap/latest/manage-data/shapefiles/geoprocessing-considerations-for-shapefile-output.htm)