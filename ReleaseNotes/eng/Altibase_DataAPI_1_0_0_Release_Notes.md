

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Altibase DataAPI 1.0.0 Release Notes](#altibase-dataapi-100-release-notes)
  - [1. Overview](#1-overview)
  - [2. Key Features](#2-key-features)
    - [Support for JWT Bearer Authentication and Basic Authentication](#support-for-jwt-bearer-authentication-and-basic-authentication)
    - [Core HTTP Endpoints](#core-http-endpoints)
    - [JSON-based Requests and Responses](#json-based-requests-and-responses)
    - [NDJSON Streaming Support](#ndjson-streaming-support)
    - [Dynamic Per-user Connection Pool Management](#dynamic-per-user-connection-pool-management)
    - [Operation and Monitoring Support](#operation-and-monitoring-support)
  - [3. Compatibility](#3-compatibility)
  - [4. Download](#4-download)
    - [Packages](#packages)
    - [Docker Images](#docker-images)
    - [Manual](#manual)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

<br/>

<br/>

<br/>

Altibase DataAPI 1.0.0 Release Notes
===============================

**(July 1, 2026)**

## 1. Overview

The Altibase Data API is a Spring Boot–based service that provides Altibase SQL execution and query capabilities over HTTP APIs. Clients can perform SQL queries, execute DML/DDL statements, and leverage streaming for bulk data retrieval via either DB user authentication or JWT token–based authentication. Additionally, it offers a monitoring API to query connection pool status and metric information for the Data API.

## 2. Key Features

### Support for JWT Bearer Authentication and Basic Authentication

JWT Bearer authentication supports token-based session management and authentication flow control. Basic authentication verifies credentials for every request without additional token management and is suitable for scripts, batch jobs, and monitoring environments.

### Core HTTP Endpoints

Provides endpoints required for SQL execution, result retrieval, large-volume streaming, authentication, and session management. For the detailed list, refer to the manual.

### JSON-based Requests and Responses

Requests are sent in JSON format containing SQL text and bind values, and query results are returned in JSON format.

### NDJSON Streaming Support

Large query results can be transmitted sequentially in NDJSON (Newline Delimited JSON) format, and memory usage is minimized through lazy-execution-based streaming.

### Dynamic Per-user Connection Pool Management

Creates and reuses user-specific connection pools, ensuring safe cleanup upon session termination for efficient resource management.

### Operation and Monitoring Support

Provides APIs for retrieving connection pool status and metrics, as well as Prometheus-compatible metrics.



## 3. Compatibility

- Compatible with Java 17 or later.
- Available for Altibase 7.1.0.5.6 or later.



## 4. Download

### Packages

The Data API packages are provided as the following files and can be downloaded from http://support.altibase.com/kr/product.

* data-api-1.0.0-altibase8.jar
* data-api-1.0.0-altibase7.jar

### Docker Images

The Data API Docker images are provided with the following tags.

- altibase/data-api:1.0.0
- altibase/data-api:1.0.0-altibase7
- altibase/data-api:latest

### Manual

- [Data API Manual - Altibase 8.1 Manual](https://manual.altibase.com/8.1/dev/data-api/copyright/)
