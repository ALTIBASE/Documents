

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [Altibase KADA 1.0.3 Release Notes](#altibase-kada-103-release-notes)
  - [1. New Features and Changes](#1-new-features-and-changes)
    - [KADA REST API](#kada-rest-api)
    - [KADA JAVA API](#kada-java-api)
  - [2. Download](#2-download)
    - [Packages](#packages)
    - [Docker Images](#docker-images)
    - [Manual](#manual)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

<br/>

<br/>

<br/>

Altibase KADA 1.0.3 Release Notes
===============================

**(July 1, 2026)**

## 1. New Features and Changes

### KADA REST API

#### Bug Fixes

##### BUG-52369 Fixed incorrect error response when retrieving a deleted shared collection

Fixed an issue where a permission error (`403 Forbidden`) was returned when retrieving a deleted shared collection. The API now returns `404 Not Found`.

##### BUG-52371 Fixed incorrect version information displayed in OpenAPI and Swagger UI

Fixed an issue where the version information displayed in the OpenAPI documentation and Swagger UI did not match the actual installed KADA REST API version. The correct installed version is now displayed.

### KADA JAVA API

No changes.

## 2. Download

### Packages

The KADA API packages are provided as the following files and can be downloaded from http://support.altibase.com/kr/product.

* document-access-java-1.0.3-ALL.zip
* document-access-rest-1.0.3-ALL.zip

### Docker Images

The KADA REST API Docker images are provided with the following tags.

- altibase/document-access-rest:1.0.3
- altibase/document-access-rest:latest

### Manual

- [KADA for Java User's Manual - Altibase 8.1 Manual](https://manual.altibase.com/8.1/dev/kada-java/copyright/)
- [KADA for REST API Manual - Altibase 8.1 Manual](https://manual.altibase.com/8.1/dev/kada-rest/copyright/)
