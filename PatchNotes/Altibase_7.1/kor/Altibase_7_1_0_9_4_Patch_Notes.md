# Altibase 7.1.0.9.4 Patch Notes

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

# **Table of Contents**  

- [New Features](#new-features)
    - [BUG-50768 V\$DISK\_BTREE\_HEADER, V\$MEM\_BTREE\_HEADER 성능뷰에 인덱스의 상태 정보를 출력하도록 개선되었습니다.](#bug-50768)
    - [BUG-50812 윈도우 클라이언트에서 cdbc(C API) 지원](#bug-50812)
- [Fixed Bugs](#fixed-bugs)
    - [BUG-50433 Disk Page Recovery 또는 Service 중에 Corrupted Page 에 접근하는 문제를 회피하도록 개선합니다.](#bug-50433)
    - [BUG-50781 하나의 IPC 채널에 2개의 클라이언트가 세마포어를 제어해, 수신된 데이터가 재수신되어 Invalid protocol sequence 에러가 발생하는 문제를 수정하였습니다.](#bug-50781)
    - [BUG-50791 TO_CHAR 함수를 ALIAS로 조건절에 사용시 뷰에 대한 조건절 Pushdown 이 2번 이상 발생할 경우, 비정상 종료되는 문제를 수정합니다.](#bug-50791)
    - [BUG-50799 윈도우용 설치 파일에 odbccli_sl.dll 이 누락된 문제를 수정합니다.](#bug-50799)
- [Changes](#changes)
    - [Version Info](#version-info)
    - [호환성](#%ED%98%B8%ED%99%98%EC%84%B1)
    - [프로퍼티](#%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0)
    - [성능 뷰](#%EC%84%B1%EB%8A%A5-%EB%B7%B0)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

New Features
============

### BUG-50768<a name=bug-50768></a> V\$DISK\_BTREE\_HEADER, V\$MEM\_BTREE\_HEADER 성능뷰에 인덱스의 상태 정보를 출력하도록 개선되었습니다.

-   **module** : sm

-   **Category** : Enhancement

-   **재현 빈도** : Always

-   **설명** : V\$DISK\_BTREE\_HEADER, V\$MEM\_BTREE\_HEADER 에 인덱스의
    상태 정보를 나타내는 INDEX\_STATUS 컬럼이 추가되었습니다.

    또한 V\$MEM\_BTREE\_HEADER에 인덱스의 일관성 여부를 나타내는
    IS\_CONSISTENT 컬럼도 추가되었습니다.

-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
        -   V\$DISK\_BTREE\_HEADER
            -   INDEX\_STATUS 컬럼 추가 : 인덱스의 상태를 표시
        -   V\$MEM\_BTREE\_HEADER
            -   INDEX\_STATUS 컬럼 추가 :인덱스의 상태를 표시
            -   IS\_CONSISTENT 컬럼 추가 : 인덱스의 일관성 여부를 표시
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50812<a name=bug-50812></a> 윈도우 클라이언트에서 cdbc(C API) 지원

-   **module** : ux-cdbc

-   **Category** : Portability

-   **재현 빈도** : Always

-   **설명** : windows 7.1클라이언트에서 cdbc(C API) 지원하도록 개선되었습니다.

-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

Fixed Bugs
==========

### BUG-50433<a name=bug-50433></a> Disk Page Recovery 또는 Service 중에 Corrupted Page 에 접근하는 문제를 회피하도록 개선합니다.

-   **module** : sm

-   **Category** : Fatal

-   **재현 빈도** : Unknown

-   **설명** : 1. Disk Page Recovery 또는 Service 중에 손상된 페이지(Corrupted Page)에 접근할 수 있어, 이를 회피하도록 수정하였습니다.
    2. 서비스중에 손상된 Disk Index Page 가 발견되는 경우, 해당 페이지는 inconsistent flag 설정하고, 해당 인덱스는 inconsistent index 로 설정하도록 수정하였습니다.
    
-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50781<a name=bug-50781></a> 하나의 IPC 채널에 2개의 클라이언트가 세마포어를 제어해, 수신된 데이터가 재수신되어 Invalid protocol sequence 에러가 발생하는 문제를 수정하였습니다.

-   **module** : cm-ipc

-   **Category** : Functional Error

-   **재현 빈도** : Rare

-   **설명** : 하나의 IPC 채널에 2개의 클라이언트가 세마포어를 제어해 수신된 데이터가 재수신되는 현상이 있었고, 그로 인해 Invalid protocol sequence 에러 발생하는 문제를 수정하였습니다.
    
-   **재현 방법**
    -   **재현 절차**
    
    -   **수행 결과**
    
    -   **예상 결과**
    
-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50791<a name=bug-50791></a> TO_CHAR 함수를 ALIAS로 조건절에 사용시 뷰에 대한 조건절 Pushdown 이 2번 이상 발생할 경우, 비정상 종료되는 문제를 수정합니다.

-   **module** : qp

-   **Category** : Fatal

-   **재현 빈도** : Always

-   **설명** : TO_CHAR 함수를 alias로 조건절에 사용시 뷰에 대한 조건절 Pushdown이 2번 이상 발생할 경우, 서버가 비정상 종료되는 문제를 수정합니다. 이 버그는 아래의 4가지 조건이 모두 일치하는 경우에만 발생합니다.
    
    1. TO_CHAR 함수의 2번째 인자로 숫자 형식이나 날짜 형식이 있는 경우
    2. TO_CHAR 함수의 1번째 인자가 Numeric 타입이 아닌 경우
    3. TO_CHAR 함수의 1번째 인자의 컬럼이 서브쿼리의 뷰에 존재하며, 뷰 머징이 되지 않고 Pushdown되는 경우
    4. 서브쿼리의 타겟절에서 TO_CHAR 함수를 사용하고 ALIAS를 지정하며, 이 ALIAS를 메인쿼리의 조건절에서 사용할 때, TO_CHAR 함수가 사용된 뷰로 Pushdown 되는 경우
    
- **재현 방법**

  - **재현 절차**

    ```sql
    select * from (
         select 
               (select c.USER_NAME from SYSTEM_.SYS_COMMENTS_ c where c.table_name = a.table_name and c.COLUMN_NAME is null limit 1) as usernm,
               a.table_name, 
               (select c.comments from SYSTEM_.SYS_COMMENTS_ c where c.table_name = a.table_name and c.COLUMN_NAME is null limit 1) as tablenm,
               to_char((b.fixed_alloc_mem+b.var_alloc_mem)/1024/1024,'999,999,999') || 'MB' as alloc,
               to_char((b.fixed_used_mem+b.var_used_mem)/1024/1024,'999,999,999') || 'MB' as used
          from system_.sys_tables_ a, v$memtbl_info b
         where a.table_oid = b.table_oid
           and a.user_id <> (select user_id from system_.sys_users_ where user_name = 'SYSTEM_')
           and a.table_type = 'T'
          order by (b.fixed_alloc_mem+b.var_alloc_mem) desc)
          where alloc != '0MB';
    ```

  - **수행 결과**

    ```sql
    [ERR-91015 : Communication failure.]
    ```

  -   **예상 결과**

          No rows selected.

- **Workaround**

  ```sql
  NO_PUSH_SELECT_VIEW hint 사용
  
  select /*+ NO_PUSH_SELECT_VIEW(AA) */ * from (
       select /*+  */
             (select /*+   */c.USER_NAME from SYSTEM_.SYS_COMMENTS_ c where c.table_name = a.table_name and c.COLUMN_NAME is null limit 1) as usernm,
             a.table_name, 
             (select /*+  */c.comments from SYSTEM_.SYS_COMMENTS_ c where c.table_name = a.table_name and c.COLUMN_NAME is null limit 1) as tablenm,
             to_char((b.fixed_alloc_mem+b.var_alloc_mem)/1024/1024,'999,999,999') || 'MB' as alloc,
             to_char((b.fixed_used_mem+b.var_used_mem)/1024/1024,'999,999,999') || 'MB' as used
        from system_.sys_tables_ a, v$memtbl_info b
       where a.table_oid = b.table_oid
         and a.user_id <> (select /*+ */user_id from system_.sys_users_ where user_name = 'SYSTEM_')
         and a.table_type = 'T'
        order by (b.fixed_alloc_mem+b.var_alloc_mem) desc) AA
        where alloc != '0MB';
  ```

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

### BUG-50799<a name=bug-50799></a> 윈도우용 설치 파일에 odbccli_sl.dll 이 누락된 문제를 수정합니다.

-   **module** : pkg-map

-   **Category** : Portability

-   **재현 빈도** : Always

-   **설명** : 윈도우용 설치 파일에 odbccli_sl.dll 이 누락된 문제를 해결 하였습니다.

-   **재현 방법**

    -   **재현 절차**

    -   **수행 결과**

    -   **예상 결과**

-   **Workaround**

-   **변경사항**

    -   Performance view
    -   Property
    -   Compile Option
    -   Error Code

Changes
=======

### Version Info

| altibase version | database binary version | meta version | cm protocol version | replication protocol version |
| ---------------- | ----------------------- | ------------ | ------------------- | ---------------------------- |
| 7.1.0.9.4        | 6.5.1                   | 8.11.1       | 7.1.7               | 7.4.7                        |

> Altibase 7.1 패치 버전별 히스토리는 [Version\_Histories](https://github.com/ALTIBASE/Documents/blob/master/PatchNotes/Altibase_7.1/Altibase_7_1_Version_Histories.md) 에서 확인할 수 있다.

### 호환성

#### Database binary version

데이터베이스 바이너리 버전은 변경되지 않았다.

> 데이터베이스 바이너리 버전은 데이터베이스 이미지 파일과 로그파일의
> 호환성을 나타낸다. 이 버전이 다른 경우의 패치(업그레이드 포함)는
> 데이터베이스를 재구성해야 한다.

#### Meta Version

메타 버전은 변경되지 않았다.

> 패치를 롤백하려는 경우, [메타다운그레이드](https://github.com/ALTIBASE/Documents/blob/master/Manuals/Altibase_7.1/kor/Installation%20Guide.md#%EB%A9%94%ED%83%80-%EB%8B%A4%EC%9A%B4%EA%B7%B8%EB%A0%88%EC%9D%B4%EB%93%9Cmeta-downgrade)를 참고한다.

#### CM protocol Version

통신 프로토콜 버전은 변경되지 않았다.

#### Replication protocol Version

Replication 프로토콜 버전은 변경되지 않았다.

### 프로퍼티

#### 추가된 프로퍼티

#### 변경된 프로퍼티

#### 삭제된 프로퍼티

### 성능 뷰

#### 추가된 성능 뷰

#### 변경된 성능 뷰

#### 삭제된 성능 뷰
