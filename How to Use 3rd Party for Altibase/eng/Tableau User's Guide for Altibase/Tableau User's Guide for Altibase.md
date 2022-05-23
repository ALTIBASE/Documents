# Tableau User's Guide for Altibase

- [Introduction](#introduction)
- [Software Requirements](#software-requirements)
- [How to Use Altibase on Tableau](#how-to-use-altibase-in-tableau)



# Introduction

This guide provides information on how to use Altibase on Tableau Desktop.

## What is Tableau?

Tableau is a data visualization tool focusing on business intelligence (BI). It supports Windows and Mac OS. For more details, please refer to the [Tableau website](https://www.tableau.com).

# Software Requirements

## Tableau

- JDK 1.8 (64bit) or higher
- Supports JDBC API Specification 4.0 or higher
- Type-4 JDBC Driver (Pure Java)
- For more [details](https://help.tableau.com/current/pro/desktop/en-us/examples_otherdatabases_jdbc.htm) about the software requirements, please refer to the Tableau website

This guide is based on the interoperability test with TableauDesktop-64bit-2021-4-4.

## Altibase

- JDK 1.8 (64bit) or higher
- Altibase Server 7.1.0.7.1 or higher
- JDBC driver for Altibase 7.1.0.5.6 or higher which partially supports JDBC API Specification 4.2 is required

# How to Use Altibase on Tableau

1. Meet the prerequisites for the Altibase Server to connect to Tableau.

   - Add the following property in $ALTIBASE_HOME/conf/altibase.properties then run the server

     - TIMESTAMP_TO_DATE = 1

   - Download and execute [mysql_date_function.sql](https://github.com/ALTIBASE/Documents/tree/master/How%20to%20Use%203rd%20Party%20for%20Altibase/eng/Tableau%20User's%20Guide%20for%20Altibase/mysql_date_function.sql)

     ```
     iSQL> connect sys/manager;
     iSQL> @mysql_date_function.sql
     ```

2. Install Tableau.

3. Copy and paste Altibase JDBC driver in C:\\Program Files\\Tableau\\Drivers.

   - Altibase 7.1

     Use $ALTIBASE_HOME/lib/Altibase42.jar. (From Altibase 7.1.0.5.6, JDBC driver that partially supports JDBC API Specification 4.2 is provided additionally)

   - Altibase 7.2

     Use $ALTIBASE_HOME/lib/Altibase.jar.

4. Open Tableau, go to Connect > To a Server > More... and click Other Databases (JDBC).

   ![<](Images/image-1.png)

5. Fill in the following entries to log in.

   - URL: jdbc:Altibase://***host_ip:port_no/database_name***
   - Username: User account
   - Password: User password
   - Properties File: Choose Altibase JDBC Driver (Below image is for Altibase 7.1)

   ![](Images/image-2.png)

6. The image below will be shown after logging in. Select the database from the list and select Taleau for schema.

   ![<](Images/image-3.png)