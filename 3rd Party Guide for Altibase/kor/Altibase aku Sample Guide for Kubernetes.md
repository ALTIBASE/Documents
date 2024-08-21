# Altibase aku Sample Guide for Kubernetes

- [개요](#개요)
- [PersistentVolume 사용](#PersistentVolume-사용)
  - [PersistentVolume yaml 파일 작성](#PersistentVolume-yaml-파일-작성)
  - [PersistentVolume 생성](#PersistentVolume-생성)
  - [PersistentVolume 생성 확인](#PersistentVolume-생성-확인)
- [ConfigMap 사용](#ConfigMap-사용)
  - [ConfigMap yaml 파일 작성](#ConfigMap-yaml-파일-작성)
  - [ConfigMap 생성](#ConfigMap-생성)
  - [ConfigMap 생성 확인](#ConfigMap-생성-확인)
- [Service 사용](#Service-사용)
  - [Service yaml 파일 작성](#Service-yaml-파일-작성)
  - [Service 생성](#Service-생성)
  - [Service 생성 확인](#Service-생성-확인)
- [StatefulSet 사용](#StatefulSet-사용)
  - [StatefulSet yaml 파일 작성](#StatefulSet-yaml-파일-작성)
  - [StatefulSet 생성](#StatefulSet-생성)
  - [StatefulSet 및 Pod 생성 확인](#StatefulSet-및-Pod-생성-확인)
  - [Altibase 설치 및 aku 설정](#Altibase-설치-및-aku-설정)
  - [이중화 동작 확인](#이중화-동작-확인)
  - [Scale-down 동작확인](#Scale-down-동작확인)
  - [Scale-up 동작확인](#Scale-up-동작확인)

## 개요

본 문서는 Altibase aku를 이용하여 Kubernetes StatefulSet을 사용하는 샘플 가이드를 제시합니다. 
- aku에 대해서는 Altibase Utilities 매뉴얼에서 aku 항목을 참고합니다.
- 본 문서의 내용은 샘플용도이며, 실제 환경에서는 각각의 용도 및 환경에 맞추어 수정되어야 합니다.
- 테스트 환경
  - Kubernetes: v1.24.2
  - Altibase: v7.1.0.9.9

## PersistentVolume 사용

- 본 예시에서는 4개의 volume을 서로 다른 path로 설정하였지만, 동일한 path로 설정해도 됩니다. 개별 pod에서 hostname을 이용하여 고유한 subdirectory를 만들기 때문입니다. 
- 본 예시에서는 NFS volume을 사용합니다. 사용자 환경에 맞추어 수정이 필요합니다.
- 영속성을 보장하는 다른 형태의 volume을 사용해도 됩니다.

##### PersistentVolume yaml 파일 작성

```yaml
# file : altibase-pv.yaml

apiVersion: v1
kind: PersistentVolume
metadata:
  name: altibase-pv-a
spec:
  capacity:
    storage: 100Gi
  accessModes:
    - ReadWriteMany
  persistentVolumeReclaimPolicy: Retain
  nfs:
    server: 192.168.1.121
    path: /home/altibase/nfs/test/a
---
apiVersion: v1
kind: PersistentVolume
metadata:
  name: altibase-pv-b
spec:
  capacity:
    storage: 100Gi
  accessModes:
    - ReadWriteMany
  persistentVolumeReclaimPolicy: Retain
  nfs:
    server: 192.168.1.121
    path: /home/altibase/nfs/test/b
---
apiVersion: v1
kind: PersistentVolume
metadata:
  name: altibase-pv-c
spec:
  capacity:
    storage: 100Gi
  accessModes:
    - ReadWriteMany
  persistentVolumeReclaimPolicy: Retain
  nfs:
    server: 192.168.1.121
    path: /home/altibase/nfs/test/c
---
apiVersion: v1
kind: PersistentVolume
metadata:
  name: altibase-pv-d
spec:
  capacity:
    storage: 100Gi
  accessModes:
    - ReadWriteMany
  persistentVolumeReclaimPolicy: Retain
  nfs:
    server: 192.168.1.121
    path: /home/altibase/nfs/test/d
```

##### PersistentVolume 생성

```
$ kubectl create -f altibase-pv.yaml
persistentvolume/altibase-pv-a created
persistentvolume/altibase-pv-b created
persistentvolume/altibase-pv-c created
persistentvolume/altibase-pv-d created
```

##### PersistentVolume 생성 확인

```
$ kubectl get pv -o wide
NAME                   CAPACITY   ACCESS MODES   RECLAIM POLICY   STATUS      CLAIM                                              STORAGECLASS   REASON   AGE    VOLUMEMODE
altibase-pv-a          100Gi      RWX            Retain           Available                                                                              30s    Filesystem
altibase-pv-b          100Gi      RWX            Retain           Available                                                                              30s    Filesystem
altibase-pv-c          100Gi      RWX            Retain           Available                                                                              30s    Filesystem
altibase-pv-d          100Gi      RWX            Retain           Available                                                                              30s    Filesystem
```

## ConfigMap 사용

- 본 예제에서는 set_linux.env, set_altibase.env, entry_point.sh 화일을 ConfigMap으로 관리합니다.
- 본 예제에서는 https://hub.docker.com/ 에 등록된 ubuntu:18.04 docker image를 테스트 용도로 사용하였습니다.
- 실제 환경에서는 각각의 용도에 맞는 Linux docker image를 사용하면 됩니다.
- 실제 사용될 Linux docker image에 맞추어 set_linux.env 의 변경이 필요하며, 아래의 문서들을 참고합니다.
  - 알티베이스 설치 매뉴얼
  - Altibase 운영을 위한 Linux 설정 가이드 ( https://aid.altibase.com/pages/viewpage.action?pageId=13436485 )

##### ConfigMap yaml 파일 작성

```yaml
# file : altibase-cm.yaml

apiVersion: v1
kind: ConfigMap
metadata:
  name: altibase-cm
data:
  set_linux.env: |
    sed -e '56 i\root\t\t soft\t nofile\t\t 1048576 \nroot\t\t hard\t nofile\t\t 1048576 \nroot\t\t soft\t nproc\t\t unlimited \nroot\t\t hard\t nproc\t\t unlimited \n' -i /etc/security/limits.conf; \
    echo "vm.swappiness = 1" >> /etc/sysctl.conf; \
    echo "kernel.sem = 20000 32000 512 5029" >> /etc/sysctl.conf;

  set_altibase.env: |
    export MY_POD_NAME=${HOSTNAME}
    export ALTIBASE_HOME=/ALTIBASE/altibase_home_${MY_POD_NAME}
    export ALTIBASE_NLS_USE=UTF8
    export ALTIBASE_PORT_NO=20300
    export ALTIBASE_REPLICATION_PORT_NO=20301
    export ALTIBASE_ADMIN_MODE=1            # aku requirement
    export ALTIBASE_REMOTE_SYSDBA_ENABLE=1  # aku requirement
    export PATH=${ALTIBASE_HOME}/bin:${PATH}
    export LD_LIBRARY_PATH=${ALTIBASE_HOME}/lib:${LD_LIBRARY_PATH};

  entry_point.sh: |
    #!/bin/bash
    . /CONFIGMAP/set_linux.env
    . /CONFIGMAP/set_altibase.env

    function PodTerminate()
    {
      echo `date` "${MY_POD_NAME} aku end"
      ${ALTIBASE_HOME}/bin/aku -p end
      echo `date` "${MY_POD_NAME} server stop"
      ${ALTIBASE_HOME}/bin/server stop
    }
    trap PodTerminate SIGTERM
    trap PodTerminate TERM

    if [ -d "${ALTIBASE_HOME}" ];then
      echo `date` "${MY_POD_NAME}: [${ALTIBASE_HOME}] path exists."
      echo `date` "${MY_POD_NAME}: It is assumed altibase is installed and aku is configured."
      echo `date` "${MY_POD_NAME}: altibase server start "
      ${ALTIBASE_HOME}/bin/server start
      echo `date` "${MY_POD_NAME}: aku start "
      ${ALTIBASE_HOME}/bin/aku -p start
    else
      mkdir -p ${ALTIBASE_HOME}
      echo `date` "${MY_POD_NAME}: [${ALTIBASE_HOME}] path is newly created."
      echo `date` "${MY_POD_NAME}: You need to install altibase and do the followings. "
      echo `date` "${MY_POD_NAME}: Create altibase server : [server create utf8 utf8] "
      echo `date` "${MY_POD_NAME}: Start altibase server : [server start] "
      echo `date` "${MY_POD_NAME}: Configure aku "
      echo `date` "${MY_POD_NAME}: Start aku : [aku -p start] "
      echo `date` "${MY_POD_NAME}: Next pod will be started after aku is started successfully because of startupProbe setti                                                                  ng."
    fi

    while (true)
    do
      sleep 1
    done
```

##### ConfigMap 생성

```
$ kubectl create -f altibase-cm.yaml
configmap/altibase-cm created
```

##### ConfigMap 생성 확인

```
$ kubectl get cm -o wide
NAME               DATA   AGE
altibase-cm        5      32s
```

## Service 사용

- 본 예시에서는 Kubernetes headless service를 사용합니다.

##### Service yaml 파일 작성

```yaml
# file : altibase-svc.yaml

apiVersion: v1
kind: Service
metadata:
  name: altibase-svc
spec:
  type: ClusterIP
  clusterIP: None
  publishNotReadyAddresses: true
  ports:
  - name: service-port
    port: 20300
    targetPort: 20300
  - name: replication-port
    port: 20301
    targetPort: 20301
  selector:
    app: altibase-sts
```

##### Service 생성

```
$ kubectl create -f altibase-svc.yaml
service/altibase-svc created
```

##### Service 생성 확인

```
$ kubectl get svc -o wide
NAME                           TYPE        CLUSTER-IP   EXTERNAL-IP   PORT(S)               AGE    SELECTOR
altibase-svc                   ClusterIP   None         <none>        20300/TCP,20301/TCP   37s    app=altibase-sts
```

## StatefulSet 사용

- 본 예시에서는 StatefulSet으로 4개의 pod를 생성합니다.
- Altibase Kubernetes Utility는 최대 4개의 pod에 이중화 구성을 지원합니다.

##### StatefulSet yaml 파일 작성

```yaml
# file : altibase-sts.yaml

apiVersion: apps/v1
kind: StatefulSet
metadata:
  name: altibase-sts
spec:
  serviceName: altibase-svc
  replicas: 4
  updateStrategy:
    type: RollingUpdate
  podManagementPolicy: OrderedReady
  selector:
    matchLabels:
      app: altibase-sts
  template:
    metadata:
      labels:
        app: altibase-sts
    spec:
      terminationGracePeriodSeconds: 60
      containers:
      - name: altibase-sts
        image: ubuntu:18.04
        command:
        - /bin/bash
        - "-c"
        - /CONFIGMAP/entry_point.sh
        ports:
        - containerPort: 20300
          protocol: TCP
        - containerPort: 20301
          protocol: TCP
        startupProbe:
          exec:
            command:
            - cat
            - /tmp/aku_start_completed
          failureThreshold: 3600
          periodSeconds: 10
        volumeMounts:
        - name: altibase-pv
          mountPath: /ALTIBASE
        - name: altibase-cm
          mountPath: /CONFIGMAP
          readOnly: true
      volumes:
        - name: altibase-cm
          configMap:
            name: altibase-cm
            defaultMode: 0777
            items:
            - key: "set_linux.env"
              path: "set_linux.env"
            - key: "set_altibase.env"
              path: "set_altibase.env"
            - key: "entry_point.sh"
              path: "entry_point.sh"
  volumeClaimTemplates:
    - metadata:
        name: altibase-pv
      spec:
        accessModes: [ "ReadWriteMany" ]
        resources:
          requests:
            storage: 10Gi
```

##### StatefulSet 생성

```
$ kubectl create -f altibase-sts.yaml
statefulset.apps/altibase-sts created
```

##### StatefulSet 및 Pod 생성 확인
- 최초 altibase-sts 생성시에는 알티베이스 생성 및 aku 설정이 안된 상태이므로, 아래와 같이 altibase-sts-0 pod 하나만 생성되고, 아직 READY 가 되지 않은 상태로 있습니다.

```
$ kubectl get sts -o wide
NAME                 READY   AGE    CONTAINERS               IMAGES
altibase-sts         0/4     12m    altibase-sts             ubuntu:18.04

$ kubectl get pod -o wide
NAME                   READY   STATUS    RESTARTS         AGE    IP             NODE      NOMINATED NODE   READINESS GATES
altibase-sts-0         0/1     Running   0                16m    10.244.1.91    worker2   <none>           <none>
```

##### Altibase 설치 및 aku 설정
- Kubernetes 사용을 위해서는 Altibase로부터 hostname 기반 license를 발급받아야 합니다.
- 본 예제에서의 hostname은 altibase-sts-0, altibase-sts-1, altibase-sts-2, altibase-sts-3 로 생성됩니다.
- 알티베이스 설치 매뉴얼을 참고하여, Altibase를 설치합니다.
- 각각의 pod에 접속하여, /CONFIGMAP/set_altibase.env 를 먼저 수행해준 이후에 설치작업을 진행합니다.
- 아래에서는 첫번째 pod에 대하여, 알티베이스 설치이후의 과정을 테스트 용도로 기록합니다.
  - altibase server 생성
  - altibase server 시작
  - 샘플 용도의 테이블 생성(T1,T2,T3)
  - 샘플 용도의 aku.conf 생성
  - aku 시작
  - startupProbe 설정이 되어있어서, aku가 성공적으로 수행되어야, 그 다음 pod가 생성됩니다. 

```
$ kubectl exec -it altibase-sts-0 -- bash
root@altibase-sts-0:/# . /CONFIGMAP/set_altibase.env
root@altibase-sts-0:/# . server create utf8 utf8
-----------------------------------------------------------------
     Altibase Client Query utility.
     Release Version 7.1.0.9.9
     Copyright 2000, ALTIBASE Corporation or its subsidiaries.
     All Rights Reserved.
-----------------------------------------------------------------
ISQL_CONNECTION = UNIX, SERVER = localhost
Connected to idle instance.
Connecting to the DB server.... Connected.


TRANSITION TO PHASE : PROCESS
Command executed successfully.

DB Info (Page Size     = 32768)
        (Page Count    = 257)
        (Total DB Size = 8421376)
        (DB File Size  = 1073741824)

        Creating MMDB FILES     [SUCCESS]

        Creating Catalog Tables [SUCCESS]

        Creating DRDB FILES     [SUCCESS]

  [SM] Rebuilding Indices [Total Count:0]  [SUCCESS]

DB Writing Completed. All Done.

Create success.
root@altibase-sts-0:/# 
root@altibase-sts-0:/# server start
-----------------------------------------------------------------
     Altibase Client Query utility.
     Release Version 7.1.0.9.9
     Copyright 2000, ALTIBASE Corporation or its subsidiaries.
     All Rights Reserved.
-----------------------------------------------------------------
ISQL_CONNECTION = UNIX, SERVER = localhost
Connected to idle instance.
Connecting to the DB server.... Connected.


TRANSITION TO PHASE : PROCESS


TRANSITION TO PHASE : CONTROL


TRANSITION TO PHASE : META
  [SM] Recovery Phase - 1 : Preparing Database
                          : Dynamic Memory Version => Parallel Loading
  [SM] Recovery Phase - 2 : Loading Database
  [SM] Recovery Phase - 3 : Skipping Recovery & Starting Threads...
                            Refining Disk Table
  [SM] Refine Memory Table : ..................................................................................................................                                              ............... [SUCCESS]
  [SM] Rebuilding Indices [Total Count:133] ...................................................................................................                                              .................................. [SUCCESS]


TRANSITION TO PHASE : SERVICE
  [CM] Listener started : TCP on port 20300 [IPV4]
  [CM] Listener started : UNIX
  [CM] Listener started : IPC
  [RP] Initialization : [PASS]

--- STARTUP Process SUCCESS ---
Command executed successfully.
root@altibase-sts-0:/# 
root@altibase-sts-0:/# is -sysdba
-----------------------------------------------------------------
     Altibase Client Query utility.
     Release Version 7.1.0.9.9
     Copyright 2000, ALTIBASE Corporation or its subsidiaries.
     All Rights Reserved.
-----------------------------------------------------------------
ISQL_CONNECTION = UNIX, SERVER = localhost
iSQL(sysdba)> CREATE TABLE T1 ( I1 INTEGER PRIMARY KEY, I2 INTEGER );
Create success.
iSQL(sysdba)> CREATE TABLE T2 ( I1 INTEGER PRIMARY KEY, I2 INTEGER );
Create success.
iSQL(sysdba)> CREATE TABLE T3 ( I1 INTEGER PRIMARY KEY, I2 INTEGER );
Create success.
iSQL(sysdba)> exit
root@altibase-sts-0:/# 
root@altibase-sts-0:~# cd $ALTIBASE_HOME/conf
root@altibase-sts-0:/ALTIBASE/altibase_home_altibase-sts-0/conf# cp aku.conf.sample aku.conf
root@altibase-sts-0:/ALTIBASE/altibase_home_altibase-sts-0/conf# aku -p start
AKU started with START option.
[AKU][2024/08/20 06:18:45.610353][139788776925184] [INFO][akuRunStart:854][-][-] Start as MASTER Pod.
AKU run successfully.
root@altibase-sts-0:/ALTIBASE/altibase_home_altibase-sts-0/conf#
root@altibase-sts-0:/ALTIBASE/altibase_home_altibase-sts-0/conf# exit
```

- 나머지 pod들에 대해서도 동일한 작업을 해주어야 합니다.
- 모든 pod들에 정상적으로 작업이 완료된 이후에 아래와 같은 상태가 됩니다.

```
$ kubectl get sts -o wide
NAME                 READY   AGE    CONTAINERS               IMAGES
altibase-sts         4/4     12m    altibase-sts             ubuntu:18.04

$ kubectl get pod -o wide
NAME                   READY   STATUS    RESTARTS         AGE    IP             NODE      NOMINATED NODE   READINESS GATES
altibase-sts-0         1/1     Running   0                16m    10.244.1.91    worker2   <none>           <none>
altibase-sts-1         1/1     Running   0                16m    10.244.2.118   worker1   <none>           <none>
altibase-sts-2         1/1     Running   0                15m    10.244.1.92    worker2   <none>           <none>
altibase-sts-3         1/1     Running   0                14m    10.244.2.119   worker1   <none>           <none>
```

##### 이중화 동작 확인
- altibase-sts-3 pod에서 isql로 local Altibase에 접속하여 T1 테이블에 입력한다.
- altibase-sts-3 pod에서 isql로 altibase-sts-2 pod의 Altibase에 접속하여, T1 테이블을 조회한다.

```
$ kubectl exec -it altibase-sts-3 -- bash
root@altibase-sts-3:/# . /CONFIGMAP/set_altibase.env
root@altibase-sts-3:/# is
-----------------------------------------------------------------
     Altibase Client Query utility.
     Release Version 7.1.0.9.9
     Copyright 2000, ALTIBASE Corporation or its subsidiaries.
     All Rights Reserved.
-----------------------------------------------------------------
ISQL_CONNECTION = TCP, SERVER = localhost, PORT_NO = 20300
iSQL> insert into t1 values(1,1);
iSQL> exit

root@altibase-sts-3:/# isql -s altibase-sts-2.altibase-svc -u sys -p manager
-----------------------------------------------------------------
     Altibase Client Query utility.
     Release Version 7.1.0.9.9
     Copyright 2000, ALTIBASE Corporation or its subsidiaries.
     All Rights Reserved.
-----------------------------------------------------------------
ISQL_CONNECTION = TCP, SERVER = altibase-sts-2.altibase-svc, PORT_NO = 20300
iSQL> select * from T1;
I1          I2
---------------------------
1           1
1 row selected.
```

##### Scale-down 동작확인
- replicas=3 으로 scale-down 한다.
- altibase-sts-2 pod에 접속한다.
- AKU_REP_23 이중화의 XSN 값이 reset 상태인 -1 인것을 확인한다.

```
$ kubectl scale sts altibase-sts --replicas=3
statefulset.apps/altibase-sts scaled
$
$ kubectl exec -it altibase-sts-2 -- bash
root@altibase-sts-2:/# . /CONFIGMAP/set_altibase.env
root@altibase-sts-2:/# is
-----------------------------------------------------------------
     Altibase Client Query utility.
     Release Version 7.1.0.9.9
     Copyright 2000, ALTIBASE Corporation or its subsidiaries.
     All Rights Reserved.
-----------------------------------------------------------------
ISQL_CONNECTION = TCP, SERVER = localhost, PORT_NO = 20300
iSQL> select REPLICATION_NAME, XSN from system_.sys_replications_;
REPLICATION_NAME                          XSN
------------------------------------------------------------------
AKU_REP_02                                1591138
AKU_REP_12                                1591138
AKU_REP_23                                -1
3 rows selected.
```

##### Scale-up 동작확인
- altibase-sts-0 pod에 접속하여, T1 테이블에 추가로 데이터를 입력한다.
- replicas=4 로 scale-up 한다.
- altibase-sts-3 pod에 접속하여, T1 테이블에 추가로 입력한 데이터가 scale-up된 pod에 반영되어 있는지 확인한다.

```
$ kubectl exec -it altibase-sts-0 -- bash
root@altibase-sts-0:/# . /CONFIGMAP/set_altibase.env
root@altibase-sts-0:/# is
-----------------------------------------------------------------
     Altibase Client Query utility.
     Release Version 7.1.0.9.9
     Copyright 2000, ALTIBASE Corporation or its subsidiaries.
     All Rights Reserved.
-----------------------------------------------------------------
ISQL_CONNECTION = TCP, SERVER = localhost, PORT_NO = 20300
iSQL> insert into t1 values(2,2);
1 row inserted.
iSQL> exit
root@altibase-sts-0:/# exit
$
$ kubectl scale sts altibase-sts --replicas=4
statefulset.apps/altibase-sts scaled
$
$ kubectl exec -it altibase-sts-3 -- bash
root@altibase-sts-3:/# . /CONFIGMAP/set_altibase.env
root@altibase-sts-3:/# is
-----------------------------------------------------------------
     Altibase Client Query utility.
     Release Version 7.1.0.9.9
     Copyright 2000, ALTIBASE Corporation or its subsidiaries.
     All Rights Reserved.
-----------------------------------------------------------------
ISQL_CONNECTION = TCP, SERVER = localhost, PORT_NO = 20300
iSQL> select * from T1;
I1          I2
---------------------------
1           1
2           2
2 row selected.
```
