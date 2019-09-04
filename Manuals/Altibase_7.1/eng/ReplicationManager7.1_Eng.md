<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Preface](#_Toc938646)

> - [About This Manual](#_Toc938647)
>   - [Types of Users](#_Toc938648)
>   - [Software Dependencies](#_Toc938649)
>   - [How This Manual is Structured](#_Toc938650)
>   - [Related Documents](#_Toc938651)
>   - [Online Manuals](#_Toc938652)
>   - [Altibase Welcomes Your Comments](#_Toc938653)

- [1.Introduction to Replication Manager](#introduction-to-replication-manager)
  - [Overview of Replication Manager](#_Ref479351093)
  - [Installing Replication Manager](#_Ref479351248)
    - [System Requirements](#_Ref479350959)
    - [Installation Media](#_Ref479350962)
    - [Installing and Uninstalling Replication Manager](#_Ref479350966)

- [2. Using Replication Manager](#using-replication-manager)
  - [Understanding the User Interface](#_Ref479351032)
    - [DB Connections](#_Toc938662)
    - [Replication Pairs](#_Toc938663)_
    - [Map](#_Toc938664)
  - [Getting Started](#_Ref479351035)
    - [Starting and Shutting Down](#_Ref479351061)
    - [Connecting to Altibase](#_Ref479351066)
    - [Working with Replication](#_Ref879814)
  - [Detailed Usage: Embedded Help](#_Ref479351042)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

Altibase® Tools & Utilities

# Replication Manager User\'s Manual

### Release 7.1 (September 4th, 2019) {#release-7.1-august-26-2019 .ALTIBASE1}



Altibase® Tools & Utilities Replication Manager User\'s Manual

Release 7.1

Copyright © 2001\~2019 Altibase Corp. All rights reserved.

This manual contains proprietary information of Altibase Corporation; it is provided under a license agreement containing restrictions on use and disclosure and is also protected by copyright patent and other intellectual property law. Reverse engineering of the software is prohibited.

All trademarks, registered or otherwise, are the property of their respective owners.

Altibase Corp.

10F, Daerung PostTower II,

306, Digital-ro, Guro-gu, Seoul 08378, Korea

Telephone: +82-2-2082-1000 Fax: 82-2-2082-1099

Homepage: [[http://www.altibase.com](http://www.altibase.com)



## Preface

### About This Manual

This manual describes how to use the Replication Manager to manage an Altibase database.

#### Types of Users

This manual has been prepared for the following Altibase users:

-   Database administrators

-   Performance managers

-   Database users

-   Application developers

-   Technical support engineers

It is recommended for those reading this manual possess the following background knowledge:

-   Basic knowledge of computers, operating systems, and operating system commands

-   Experience in using relational databases and an understanding of database concepts

-   Computer programming experience

-   Experience in database server management, operating system management or network administration

#### How This Manual is Structured

This document is an introductory guide for those unfamiliar with the Replication Manager. The rest of this document is organized as follows:

-   Chapter1: Introduction to Replication Manager
    This chapter provides an overview of the Replication Manager and contains information on the prerequisites for installation. It also explains how to install, remove, and update the Replication Manager.

-   Chapter2: Using Replication Manager
    This chapter provides newcomers with instructions on how to start and stop the Replication Manager. It also outlines the steps used to connect to an Altibase database using the Replication Manager, and contains information on how to use and manage the Replication Manager.

#### Related Documents

For additional technical information, please refer to the following manuals:

-   Altibase Installation Manual

-   Altibase Administrator's Manual

-   Altibase Replication User's Manual

-   Altibase Precompiler User's Manual

-   Altibase ODBC User's Manual

-   Altibase Application Program Interface User's Manual

-   Altibase iSQL User's Manual

-   Altibase Utilities User's Manual

-   Altibase Error Message Reference

#### Online Manuals

> Online versions of our manuals (PDF or HTML) are available from Altibase\'s Customer Support site (http://altibase.com/resources/documents).

#### Altibase Welcomes Your Comments

Please let us know what  you like or dislike about our manuals. To help us with future versions of our manuals, please tell us about any corrections or classifications that you would find useful. 

Please send it to our customer service portal (http://support.altibase.com/en/) with the following comments or feedback.

-   The name and version of the manual that you are using

-   Any comments that you have about the manual

-   Your full name, address, and phone number

When you need immediate assistance regarding technical issues, please contact Altibase's Customer Support site (http://support.altibase.com/en/).

Thank you. We appreciate your feedback and suggestions.



## 1. Introduction to Replication Manager

This chapter is intended to help all users who want to install Replication Manager and understand its features. It also provides an overview of the Replication Manager. It contains the following sections:

-   Overview of Replication Manager

-   Installing Replication Manager

    ### Overview of Replication Manager

Replication Manager is a graphical tool for managing replication on Altibase. Altibase Database Administrators typically need to connect to all instances of the Altibase on which replication objects are active. Using a Command Line Interface (CLI) such as iSQL, they need to jump around between console windows to perform replication tasks such as stopping, modifying, and starting target replication objects. This requires them to memorize the status of, and relationships between, replication objects, meaning that the burden of replication management grows exponentially as the number of replication objects increases linearly. Thanks to its Graphical User Interface (GUI), the Replication Manager can help DBAs perform these tasks efficiently while visualizing all of their replication nodes on the same screen.

More detailed information about Replication Manager is provided in the embedded help (the help menu that is integral to the Replication Manager).

The significant benefits of this tool are:

1.  It allows DBAs to work with multiple versions of Altibase (versions 4.3.9 or higher) using the same program.

2.  It allows DBAs to check the status of replication objects and the relationships between them at a glance.

3.  It allows DBAs to manage replication objects with the click of a mouse.

4.  It allows DBAs to check the properties of replication objects and related objects.

5.  It allows DBAs to monitor replication pairs and analyze their status, almost intuitively.

    ### Installing Replication Manager

This section is designed to help the user understand system requirements and all installation prerequisites. It also provides information about how to install and uninstall the Replication Manager. It includes the following sections:

-   System Requirements

-   Installation Media

-   Installing and Uninstalling Replication Manager

    #### System Requirements

Before installing the Replication Manager, please check your system against the following prerequisites to ensure that installation will be successful. The minimum system requirements for the Replication Manager are as follows:

1.  Computer processor: 800MHz Pentium III or better
2.  Computer memory: 512MB or more
3.  Computer disk: 50MB or more free space (in addition to space required for the JRE)
4.  Screen resolution: 1024 x 768 pixels or higher

Replication Manager is a Java-based graphical client application, which means it relies on the client\'s hardware, operating system, and Java runtime environment. At this moment, Replication Manager is now distributed in Windows- and Linux-compatible packages.

------------------------------------------------------- ---------------------- ------------ ------------------ ----------------
 

| Package Name                                          | Operating System     | Hardware   | JRE              | Windows System |
| ----------------------------------------------------- | -------------------- | ---------- | ---------------- | -------------- |
| ReplicationManager-win32.win32.x86.zip (JRE included) | Windows XP, Vista, 7 | x86 32-bit | Java 6 or higher | Win32          |
| ReplicationManager-linux.gtk.x86.zip                  | Linux                | x86 32-bit | Java 6 or higher | GTK            |

------------------------------------------------------- ---------------------- ------------ ------------------ ----------------

Replication Manager is based on Eclipse RCP 3.6.2 technology ([http://www.eclipse.org/)](http://www.eclipse.org/). Therefore, this version of the Replication Manager will work on any platform on which Eclipse RCP is supported. For additional information, please refer to the supported platform list at [http://www.eclipse.org/eclipse/](http://www.eclipse.org/eclipse/development/readme_eclipse_3.4.2.html)development/readme\_eclipse\_3.6.2.html. Replication Manager will be packaged for other platforms in the future if demand merits.

#### Installation Media

Replication Manager can be obtained in the following two ways:

1.  Replication Manager is included in the client package that is provided to customers who purchase Altibase.
2.  Replication Manager can be downloaded from Altibase's Customer Support site (http://support.altibase.com/en/).

#### Installing and Uninstalling Replication Manager

Installing the Replication Manager is very simple. Replication Manager is provided in ZIP file format. To install it, unzip the file in the desired directory.

Additionally, it is necessary to import an Altibase JDBC driver that is appropriate for the database to which is connecting. Please refer to the section \"Importing a JDBC Driver File\" in Chapter 2 Using Replication.

Replication Manager can work with many different versions of Altibase simultaneously.

However, it will be necessary to import multiple versions of the Altibase JDBC driver corresponding to the respective versions of the Altibase on each of the replication nodes. If, for instance, the user must connect to two different Altibase databases, for example, versions 4.3.9.100 and 5.3.3.33 respectively, then the user is required to import two versions of the JDBC driver files into Replication Manager, and to give them different names, for example, \"Altibase\_4.3.9.100.jar\" and \"Altibase\_5.3.3.33.jar\". Uninstalling the Replication Manager is also very easy,just simply delete the directory in which Replication Manager is installed.

## Using Replication Manager

This chapter introduces the Replication Manager User interface, and additionally describes the basic usage of the Replication Manager. It is organized as follows:

-   Understanding the User Interface

-   Getting Started

-   Detailed Usage: Embedded Help

    ### Understanding the User Interface

This chapter introduces the Replication Manager User interface and additionally describes the primary usage of the Replication Manager. It is organized as follows:



1.  DB Connections: This is the entry point for the program and a database-centric view that represents the relationship between databases and replication objects in a tree structure.
2.  Replication Pairs: This is a logical view that depicts replication objects in pairs. A group of two replication objects that have the same name and interact with each other is called a \"Replication Pair\".
3.  Map: This area graphically illustrates the physical layout and status of databases, replication objects, and the relationships therebetween.
4.  Properties: This area shows the properties for the currently selected object (e.g., DB connection or replication objects).

These four panes are intended to give DBAs various ways of visualizing the same databases and replication objects. For example, the \"Map\" pane provides a convenient way to check the replication gap at a glance, while \"Replication Pairs\" provides a convenient way of handling replication objects as pairs without having to think about the databases on which they are working. So, these four panes complement each other. For example, when a replication object is selected in the \"DB Connections\" pane, the same replication object is also selected in the \"Replication Pairs\" and \"Map\" panes. In addition, the properties of the selected replication object will be displayed in the \"Properties\" pane. In other words, the three editable panes, \"DB Connections\", \"Replication Pairs\", and \"Map\", interact multi-directionally with each other, while the read-only pane, \"Properties\", receives information from the other three panes.

#### DB Connections

The \"DB Connections\" pane offers the following features:

-   It provides a view that can be used to register, unregister, and edit database connections.

-   It shows meta information about connected databases, replication objects, and replication target tables in a tree structure for ease of navigation.

-   It provides a convenient way to manage databases and replication objects, including starting, stopping, creating, and dropping replication objects.

The \"DB Connections\" pane handles two types of objects: DB Connection and Replication Object.

DB Connection is a representation of an Altibase with a specific user, typically \"SYS\". It has two states: disconnected and connected.

-   DB Connection disconnected: ![http://127.0.0.1:55569/help/topic/com.altibase.replmgr/html/\_images/icon\_DbDisconnected.jpg](media/image3.jpeg){width="0.19791666666666666in" height="0.20833333333333334in"}

-   DB Connection connected: ![http://127.0.0.1:55569/help/topic/com.altibase.replmgr/html/\_images/icon\_DbConnected.jpg](media/image4.jpeg){width="0.1875in" height="0.19791666666666666in"}

Once a DB Connection is in the connected, replication object may be shown up as children of the DB Connection. Replication Object is an object created with the CREATE REPLICATION statement. It forms a replication pair with a counterpart replication object, typically on another node.

-   Replication Object: 
-   ![http://127.0.0.1:55569/help/topic/com.altibase.replmgr/html/\_images/icon\_ReplObj.jpg](media/image5.jpeg){width="0.19791666666666666in" height="0.19791666666666666in"}

The Replication Object icon in the pane shows the status of the replication sender and receiver thread. The bottom left arrow in the icon represents the sender thread\'s status, while the top right arrow does receiver\'s thread. The Green colored arrow means the replication object is working fine, while yellow colored arrow means it\'s stopped. Red colored arrow, applicable only to sender thread, presents \"Retry\" status which means the replication object\'s sender thread is trying to send XLOG but has been failed due to network problem or the corresponding replication object\'s receiver\'s problem.

#### Replication Pairs

The \"Replication Pairs\" pane offers the following features:

-   It provides a convenient way to manage replication pairs without having to think about the underlying databases.

-   It also provides a way to manage replication objects, including starting and stopping them.

The two icons used at \"Replication Pairs\" pane are Replication Pairs and Replication Object. Replication Pair is a pair of corresponding replication objects having the same name, one residing on each of two different nodes. So, it doesn\'t carry any status but conveys the logical group of replication objects. Replication Object is the same as that of DB Connection pane.

![http://127.0.0.1:55569/help/topic/com.altibase.replmgr/html/\_images/icon\_ReplPair.jpg](media/image6.jpeg){width="1.6041666666666667in" height="0.9791666666666666in"}

#### Map

The \"Map\" pane offers the following features:

-   It delivers the big picture of all registered databases and replication objects intuitively.

-   It also provides a way to control databases and replication objects.

The \"Map\" pane demonstrates DB Connections and Replication Objects with different shape icons for a better understanding of their relationship and status.

-   DB Connection at Map: ![http://127.0.0.1:55569/help/topic/com.altibase.replmgr/html/\_images/icon\_DbConnAtMap.jpg](media/image7.jpeg){width="1.875in" height="0.3125in"}

-   Replication Object at Map: ![http://127.0.0.1:55569/help/topic/com.altibase.replmgr/html/\_images/icon\_ReplObjAtMap.jpg](media/image8.jpeg){width="1.4583333333333333in" height="0.5729166666666666in"}

DB Connection icon at Map pane is the same as that at DB Connection pane except \"Unknown\" DB Connection. \"Unknown\" DB Connection will show up at Map pane if any replication object is unable to locate the corresponding replication object. So, it helps DBAs not to miss registering, and opening required DB Connections.

-   Unknown DB Connection at Map: ![http://127.0.0.1:55569/help/topic/com.altibase.replmgr/html/\_images/icon\_Unknown.jpg](media/image9.jpeg){width="0.875in" height="0.25in"}

On the other hand, the Replication Object icon at Map pane is slightly different because it represents sender thread only, not receiver thread. The Replication Object at Map pane depicts the sender\'s status - run, stopped, or retry - including replication gap status if DBAs specified warning and critical threshold values at the main menu, Window/Preference/Replication Manager/Gap Status.

![http://127.0.0.1:55569/help/topic/com.altibase.replmgr/html/\_images/ui\_pref\_gap.jpg](media/image10.jpeg){width="4.614583333333333in" height="0.9791666666666666in"}

### Getting Started

This chapter provides basic instructions on how to start up and shut down the Replication Manager. It also covers the steps to be taken to connect the Replication Manager to an Altibase database. Then, it describes the detail usage of the Replication Manager. It is organized as follows:

-   Starting and Shutting Down

-   Connecting to Altibase

-   Working with Replication

    #### Starting and Shutting Down

To start Replication Manager, double-click on \"Replication Manager.exe\" in Windows or execute the \"Replication Manager\" application in Linux in the folder where the application was installed.

To shut down Replication Manager, select \"File\", then \"Exit\" from the top menu of Replication Manager, or click on the X in the upper-right corner.

![http://127.0.0.1:55569/help/topic/com.altibase.replmgr/html/\_images/2.2.2.1\_1.jpg](media/image11.jpeg){width="5.302777777777778in" height="3.578675634295713in"}

#### 	Connecting to Altibase

This section describes, in the form of a tutorial, the basic steps that must be taken in order to connect to an Altibase database. The usual workflow when working with Altibase is as follows:

1.  Import a JDBC driver file to be used when connecting to an Altibase database.
2.  Add a database connection.
3.  Connect to the database.
4.  Conduct replication administration tasks as required.
5.  Disconnect from the database.
6.  Edit DB connection information.
7.  Manage Extra Host IPs
8.  Remove the database if it is no longer needed.

Each procedure is conducted as described below.

##### 	Importing a JDBC Driver File

This section describes the steps involved in importing the appropriate version of the JDBC driver file into the Replication Manager. It is assumed that an Altibase database has already been installed on the machine in question. (If an Altibase database has not been installed, it will be necessary to download the appropriate driver from http://support.altibase.com/.) To import the JDBC driver, do the following:

1.  Click on the \"JDBC driver manager\" icon in the toolbar to open the \"JDBC driver manager\" dialog box.

![http://127.0.0.1:55569/help/topic/com.altibase.replmgr/html/\_images/2.2.2.2\_ImportJdbc\_01.jpg](media/image12.jpeg){width="5.03125in" height="3.520913167104112in"}

2. In this dialog box, click on the \"+\" icon on the right to open the \"Import JDBC driver file\" dialog box, as shown below.

![http://127.0.0.1:55569/help/topic/com.altibase.replmgr/html/\_images/2.2.2.2\_ImportJdbc\_02.jpg](media/image13.jpeg){width="4.802083333333333in" height="3.5535422134733157in"}

3. Select a JDBC driver file to import and give the file a name to be used in Replication Manager. The source file will be copied into the specified directory and renamed as specified.

![http://127.0.0.1:55569/help/topic/com.altibase.replmgr/html/\_images/2.2.2.2\_ImportJdbc\_03.jpg](media/image14.jpeg){width="4.135416666666667in" height="3.09375in"}

4. Close the \"JDBC driver manager\" dialog box.

Alternatively, users can import a JDBC driver file when performing the \"Adding a Database connection\" task.

##### 	Adding a Database Connection

Now, it\'s time to add a database connection for managing replication objects. Follow these steps to add a database:

1.  Open the \"New DB Connection\" dialog by clicking on the \"New DB Connection\" icon in the main toolbar, or by right-clicking on the \"DB Connections icon\" in the \"DB Connections\" panel and then left-clicking on the \"New DB Connection\" item in the context menu that appears.

![http://127.0.0.1:55569/help/topic/com.altibase.replmgr/html/\_images/2.2.2.2\_AddDbConn\_01.jpg](media/image15.jpeg){width="4.729166666666667in" height="3.796654636920385in"}

2. The \"New DB Connection\" dialog box shown below will appear. Fill in the input fields as described below.

![C:\\work\\altiman4\\trunk\\fm\\media\\ReplicationManager\\image3.gif](media/image16.gif){width="4.864583333333333in" height="3.594122922134733in"}

-   Basic Information

    -   Connection Name: Any name is acceptable, as long as it is unique in the Replication Manager.

    -   User ID: A valid user ID for the database.

    -   Password: The password for the SYS user for the database

    -   DB Address: The IP address of the machine on which the database installed

    -   DB Port: The port number with which to access the database

    -   DB Name: The name of the database

    -   JDBC driver: To use the appropriate version of the JDBC driver file, select the correct imported JDBC driver in the combo box. If the required JDBC driver file has not been imported yet, please import a new JDBC driver by clicking on the \"JDBC driver manager\" icon.

-   Options

    -   IP Address Type: Please select the appropriate IP address type. Replication Manager supports both IPv4 and IPv6 addresses.

    -   NLS for Client: Choose the character set to use when translating data from the DBMS on the client side. (This option is not necessary when connecting to Altibase version 5.3.1 or higher.)

3. Click on the \"Test Connection\" button to ensure that the connection works as expected.

![http://127.0.0.1:55569/help/topic/com.altibase.replmgr/html/\_images/2.2.2.2\_AddDbConn\_03.jpg](media/image17.jpeg){width="5.208333333333333in" height="3.8541666666666665in"}

4. Finally, click on the \"Save\" button.

![http://127.0.0.1:55569/help/topic/com.altibase.replmgr/html/\_images/2.2.2.2\_AddDbConn\_04.jpg](media/image18.jpeg){width="5.208333333333333in" height="3.8541666666666665in"}

##### 	Connecting to the Database

Once Altibase has been installed and the first two tasks have been completed, you are ready to connect to a database, as shown below.

![C:\\work\\altiman4\\trunk\\fm\\media\\ReplicationManager\\image4.gif](media/image19.gif){width="5.906944444444444in" height="5.079245406824147in"}

To connect to a database, complete the following steps:

1.  Select the newly added database connection. Right-click on the newly added database to display the context menu, and then left-click on \"Connect\". This may take some time, depending on your environment.

![http://127.0.0.1:55569/help/topic/com.altibase.replmgr/html/\_images/2.2.2.2\_Conn2Db\_01.jpg](media/image20.jpeg){width="5.604166666666667in" height="4.819745188101487in"}

2. When you are successfully connected, you will see the replication objects in the target database.

![http://127.0.0.1:55569/help/topic/com.altibase.replmgr/html/\_images/2.2.2.2\_Conn2Db\_02.jpg](media/image21.jpeg){width="5.564440069991251in" height="4.785578521434821in"}

3. If the connection fails, a warning dialog appears, displaying some information that will be of help in successfully establishing a connection.

   ##### Working with the Connected Database

If you have followed the preceding steps successfully, you are ready to manage replication on the connected database.

##### 		Disconnecting from the Database

After finishing your work, it will be necessary to close the connection with the database. To close a connection with a database, select the target database connection. Open the context menu by right-clicking on the target database, and then choose \"Disconnect\" from the context menu.

![http://127.0.0.1:55569/help/topic/com.altibase.replmgr/html/\_images/2.2.2.2\_Disconn.jpg](media/image22.jpeg){width="5.567088801399825in" height="3.990248250218723in"}

##### 		Editing DB Connection Information

It will sometimes be necessary to edit database connection information. For example, it may be necessary to change the account that is used to establish the database connection. This menu is available only when not connected to the database. There are six steps involved in editing database connection information.

1.  Select the database for which it is desired to change connection information.\
    To open the context menu, right-click on the database, and then choose \"Edit\" from the context menu.

![http://127.0.0.1:55569/help/topic/com.altibase.replmgr/html/\_images/2.2.2.2\_Edit\_01.jpg](media/image23.jpeg){width="5.508029308836395in" height="3.9479166666666665in"}

2. Make the required changes to the connection information. Click on the \"Connection Test\" button to ensure that the connection works as expected.

![http://127.0.0.1:55569/help/topic/com.altibase.replmgr/html/\_images/2.2.2.2\_Edit\_02.jpg](media/image24.jpeg){width="4.375in" height="3.2439884076990375in"}

3. The dialog box shown below will appear if the connection test is successful. Click on the \"OK\" button to close this information box.

![http://127.0.0.1:55569/help/topic/com.altibase.replmgr/html/\_images/2.2.2.2\_Edit\_03.jpg](media/image25.jpeg){width="4.479166666666667in" height="1.072597331583552in"}

4. Finally, click on the \"Save\" button in the Edit dialog box.

> ![http://127.0.0.1:55569/help/topic/com.altibase.replmgr/html/\_images/2.2.2.2\_Edit\_04.jpg](media/image26.jpeg){width="4.614583333333333in" height="3.4147922134733157in"}

##### 		Managing Extra Host IPs

If an Altibase database is installed on a computer with multiple IP addresses and a replication object in another database uses one of them as the remote host IP, it must be DB Address or one of the Extra Host IPs of the target database connection. Otherwise, the relationship between the database connection and the replication object may not be displayed correctly in the Map pane. This menu is available whether connected to the database or not connected.

To add or remove an extra host IP, select the target database connection. Open the context menu by right-clicking on the database connection to be managed, and then left-click on \"Manage Extra Host IP\" in the context menu.

![http://127.0.0.1:55569/help/topic/com.altibase.replmgr/html/\_images/2.2.2.2\_ManageExtraIp.jpg](media/image27.jpeg){width="5.3607086614173225in" height="3.9072769028871392in"}

##### 		Removing a Database Connection

When a registered database is no longer in use, you will probably want to remove it from the DB Connections panel. To remove a database, select the target database connection. Open the context menu by right-clicking on the database connection to be removed, and then left-click on \"Remove\" in the context menu.

![http://127.0.0.1:55569/help/topic/com.altibase.replmgr/html/\_images/2.2.2.2\_Remove.jpg](media/image28.jpeg){width="5.364583333333333in" height="3.910100612423447in"}

#### 	Working with Replication

This section is intended to describe the detail usage of the Replication Manager. It also describes the relationship between panes and objects.

Replication Manager takes care of a single base model, which simulates databases and replication-related objects while providing various ways of visualizing and manipulating the model through three editable panes. The model is consists of six types of objects as follows:

-   Replication Object: It is an object created with the CREATE REPLICATION statement and the common object among panes at the Replication Manager. Please refer to \"Understanding the User Interface\" for details.

-   Replication Target Table Object: This is a table that is designated, using the CREATE REPLICATION or ALTER REPLICATION statement, to be replicated between corresponding replication nodes.

-   DB Connections Object: It is the root object of the \"DB Connection\" object to manage DB Connection. Also, it is the entry point for \"DB Connections\" pane.

-   DB Connection Object: It is a representation of a connection to Altibase DBMS. Please refer to \"Understanding the User Interface\" for details.

-   Replication Pairs Object: It is the root object of \"Replication Pair\" and the entry point for \"Replication Pairs\" pane.

-   Replication Pair Object: It is a pair of corresponding replication objects having the same name, one residing on each of two different nodes. Please refer to \"Understanding the User Interface\" for details.

Some objects in the model show up few panes for the ease use of the Replication Manager.

Even though some objects shared by panes are the same ones, they may provide different functionalities according to the pane. For instance, Replication Object at DB Connections pane provides the \"Edit Table List\" function, but Replication Object at Map pane doesn\'t. The reason for different functionalities on the same object according to the panes is to align functionalities to its context. At the previous example, the editing replication target table list is quite intuitive at the database-centric view, DB Connections pane. On the while, the Map pane, which is intended to give a brief overview, is not the right place to edit the replication target table list.

###### DB Connections pane

DB Connections pane is a database-centric view that represents the relationship between databases and replication objects in a tree structure. Therefore, it handles four types of objects: DB Connections, DB Connection, Replication Object, and Replication Target Tables.

###### DB Connections

-   Connect all: Connect all registered but not connected DB Connection

-   Disconnect all: Disconnect all registered and connected DB Connection

-   Start all: Start all replication objects which are stopped.

-   Stop all: Stop all replication objects which are started.

-   Quick Start all: Quick start all replication objects which are stopped. This operation may cause the loss of not yet delivered data. Please refer to \"Replication User\'s Manual\" for details.

-   New DB Connection: Create a new DB Connection.

###### DB Connection

-   Connect: Connect to the database with the given properties.

-   Disconnect: Disconnect from the connected database.

-   Edit: Edit the properties of DB Connection

-   Manage Extra Host IP: Manage the Extra Host IPs of DB Connection

-   Remove: Remove the selected DB Connection.

-   Start all: Start all replication objects which are stopped in the DB Connection.

-   Stop all: Stop all replication objects which are started in the DB Connection.

-   Quick Start all: Quick start all replication objects which are stopped in the DB Connection. This operation may cause a loss of not yet delivered data. Please refer to \"Replication User\'s Manual\" for details.

-   Create Replication: Create a Replication Object at the DB Connection.

-   Create Replication Pair: Create a pair of Replication Objects at two distinct DB Connections.

-   Drop Replications: Drop all Replication Object at the DB Connection. All Replication Objects should be stopped before using this function.

###### Replication Object

-   Start: Start the selected Replication Object.

-   Stop: Stop the selected Replication Object.

-   Quick Start: Quick Start the selected Replication Object. This operation may cause the loss of not yet delivered data. Please refer to \"Replication User\'s Manual\" for details.

-   Sync: Sync the selected Replication Object. It is equivalent to perform ALTER REPLICATION \... SYNC \... statement.

-   Sync Only: Sync Only the selected Replication Object. It is equivalent to perform ALTER REPLICATION \... SYNC ONLY \... statement.

-   Drop: Drop the selected Replication Object, which is stopped.

-   Edit Table List: Add/Remove Replication Target Tables in the selected Replication Object, which is stopped.

-   Monitor: Open a monitor dialog for the selected Replication Object and the corresponding Replication Object.

-   Show DDL: Print the schema to generate the selected Replication Object and its related objects, such as table, index, and so on.

-   Compare DDL: Print the difference of schema between the selected Replication Object and the corresponding Replication Object.

###### Replication Target Table

-   Remove: Remove the selected table from its underlying Replication Object.

###### Replication Pair pane

> Replication Pair pane is a logical view to depicts replication objects in pairs. So, it takes care of four types of objects: Replication Pairs, Replication Pair, Replication Object, and Replication Target Table.

###### Replication Pairs

-   Start all: Start all replication objects which are stopped.

-   Stop all: Stop all replication objects which are started.

-   Quick Start all: Quick start all replication objects which are stopped. This operation may cause a loss of not yet delivered data. Please refer to \"Replication User\'s Manual\" for details.

-   Create Replication Pair: Create a pair of Replication Objects at two distinct DB Connections.

###### Replication Pair

-   Start all: Start all replication objects which are stopped in the Replication Pair.

-   Stop all: Stop all replication objects which are started in the Replication Pair.

-   Quick Start all: Quick start all replication objects which are stopped in the Replication Pair. This operation may cause a loss of not yet delivered data. Please refer to \"Replication User\'s Manual\" for details.

-   Drop: Drop Replication Objects in the selected Replication Pair. All Replication Objects should be stopped before using this function.

###### Replication Object

The same at DB Connections pane.

###### Replication Target Table

The same at DB Connections pane.

###### Map pane

Map pane illustrates the physical layout and status of databases, replication objects, and the relationships therebetween. So, it carries only two types of objects: DB Connection and Replication Object.

###### DB Connection

-   Connect: Connect to the database with the given properties.

-   Disconnect: Disconnect from the connected database.

-   Start all: Start all replication objects which are stopped in the DB Connection.

-   Stop all: Stop all replication objects which are started in the DB Connection.

-   Quick Start all: Quick start all replication objects which are stopped in the DB Connection. This operation may cause a loss of not yet delivered data. Please refer to \"Replication User\'s Manual\" for details.

###### Replication Object

-   Start: Start the selected Replication Object.

-   Stop: Stop the selected Replication Object.

-   Quick Start: Quick start the selected Replication Object. This operation may cause a loss of not yet delivered data. Please refer to \"Replication User\'s Manual\" for details.

-   Sync: Sync the selected Replication Object. It is equivalent to perform ALTER REPLICATION \... SYNC \... statement.

-   Sync Only: Sync Only the selected Replication Object. It is equivalent to perform ALTER REPLICATION \... SYNC ONLY \... statement.

-   Drop: Drop the selected Replication Object, which is stopped.

-   Monitor: Open a monitor dialog for the selected Replication Object and the corresponding Replication Object.

-   Show DDL: Print the schema to generate the selected Replication Object and its related objects, such as tables, indexes, and so forth.

-   Compare DDL: Print the difference of schema between the selected Replication Object and the corresponding Replication Object.

    ### Detailed Usage: Embedded Help

As discussed in Overview of Replication Manager has its help system, referred to herein as \"embedded help\". To open embedded help, select \"Help\" and then \"Help Contents\" from the top menu of Replication Manager.

