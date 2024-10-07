# Altibase aku Sample Guide for Kubernetes

- [Overview](#Overview)
- [Using PersistentVolume](#Using-PersistentVolume)
  - [Write a PersistentVolume yaml file](#Write-a-PersistentVolume-yaml-file)
  - [Create PersistentVolume](#Create-PersistentVolume)
  - [Confirm PersistentVolume creation](#Confirm-PersistentVolume-creation)
- [Using ConfigMap](#Using-ConfigMap)
  - [Write a ConfigMap yaml file](#Write-a-ConfigMap-yaml-file)
  - [Create ConfigMap](#Create-ConfigMap)
  - [Confirm ConfigMap creation](#Confirm-ConfigMap-creation)
- [Using Service](#Using-Service)
  - [Write a Service yaml file](#Write-a-Service-yaml-file)
  - [Create Service](#Create-Service)
  - [Confirm Service creation](#Confirm-Service-creation)
- [Using StatefulSet](#Using-StatefulSet)
  - [Write a StatefulSet yaml file](#Write-a-StatefulSet-yaml-file)
  - [Create StatefulSet](#Create-StatefulSet)
  - [Confirm StatefulSet and Pod creation](#Confirm-StatefulSet-and-Pod-creation)
  - [Altibase installation and aku configuration](#Altibase-installation-and-aku-configuration)
  - [Check Altibase replication operation](#Check-Altibase-replication-operation)
  - [Check Scale-down operation](#Check-Scale-down-operation)
  - [Check Scale-up operation](#Check-Scale-up-operation)

## Overview

This document presents a sample guide to using Kubernetes StatefulSet using Altibase aku.
- For aku, refer to the aku section in the Altibase Utilities manual.
- The contents of this document are for sample purposes only, and should be modified according to each purpose and environment in the actual environment.
- test environment
  - Kubernetes: v1.24.2
  - Altibase: v7.1.0.9.9

## Using PersistentVolume

- In this example, 4 volumes are set to different paths, but you can set them to the same path. This is because each pod creates its own subdirectory using the hostname.
- This example uses NFS volumes. Modifications are required to suit your environment.
- You can use any other type of volume that guarantees persistence.

##### Write a PersistentVolume yaml file

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

##### Create PersistentVolume

```
$ kubectl create -f altibase-pv.yaml
persistentvolume/altibase-pv-a created
persistentvolume/altibase-pv-b created
persistentvolume/altibase-pv-c created
persistentvolume/altibase-pv-d created
```

##### Confirm PersistentVolume creation

```
$ kubectl get pv -o wide
NAME                   CAPACITY   ACCESS MODES   RECLAIM POLICY   STATUS      CLAIM                                              STORAGECLASS   REASON   AGE    VOLUMEMODE
altibase-pv-a          100Gi      RWX            Retain           Available                                                                              30s    Filesystem
altibase-pv-b          100Gi      RWX            Retain           Available                                                                              30s    Filesystem
altibase-pv-c          100Gi      RWX            Retain           Available                                                                              30s    Filesystem
altibase-pv-d          100Gi      RWX            Retain           Available                                                                              30s    Filesystem
```

## Using ConfigMap

- In this example, set_linux.env, set_altibase.env and entry_point.sh files are managed as ConfigMap.
- In this example, the ubuntu:18.04 docker image registered at https://hub.docker.com/ is used for testing purposes.
- In a real environment, you can use a Linux docker image suitable for each purpose.
- You need to change set_linux.env to match the Linux docker image that will actually be used. Please refer to the documents below.
  - Altibase Installation Manual
  - Linux Setup Guide for Altibase ( https://aid.altibase.com/display/arch/Linux+Setup+Guide+for+Altibase )

##### Write a ConfigMap yaml file

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
      echo `date` "${MY_POD_NAME}: Next pod will be started after aku is started successfully because of startupProbe setting."
    fi

    while (true)
    do
      sleep 1
    done
```

##### Create ConfigMap

```
$ kubectl create -f altibase-cm.yaml
configmap/altibase-cm created
```

##### Confirm ConfigMap creation

```
$ kubectl get cm -o wide
NAME               DATA   AGE
altibase-cm        5      32s
```

## Using Service

- This example uses a Kubernetes headless service.

##### Write a Service yaml file

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

##### Create Service

```
$ kubectl create -f altibase-svc.yaml
service/altibase-svc created
```

##### Confirm Service creation

```
$ kubectl get svc -o wide
NAME                           TYPE        CLUSTER-IP   EXTERNAL-IP   PORT(S)               AGE    SELECTOR
altibase-svc                   ClusterIP   None         <none>        20300/TCP,20301/TCP   37s    app=altibase-sts
```

## Using StatefulSet

- In this example, the StatefulSet creates 4 Pods.
- Altibase v7.1 version supports up to 4 pods.
- Altibase v7.3 or above versions support up to 6 pods.

##### Write a StatefulSet yaml file

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

##### Create StatefulSet

```
$ kubectl create -f altibase-sts.yaml
statefulset.apps/altibase-sts created
```

##### Confirm StatefulSet and Pod creation

- When first creating altibase-sts, since altibase has not been installed and aku has not been set up, only one pod, altibase-sts-0, is created as shown below and is not yet in the READY state.

```
$ kubectl get sts -o wide
NAME                 READY   AGE    CONTAINERS               IMAGES
altibase-sts         0/4     12m    altibase-sts             ubuntu:18.04

$ kubectl get pod -o wide
NAME                   READY   STATUS    RESTARTS         AGE    IP             NODE      NOMINATED NODE   READINESS GATES
altibase-sts-0         0/1     Running   0                16m    10.244.1.91    worker2   <none>           <none>
```

#### Altibase installation and aku configuration

- To use Kubernetes, you must obtain a hostname-based license from Altibase.
- In this example, the hostnames are created as altibase-sts-0, altibase-sts-1, altibase-sts-2, and altibase-sts-3.
- Install Altibase by referring to the Altibase installation manual.
- Connect to each pod and execute /CONFIGMAP/set_altibase.env first, then proceed with the Altibase installation.
- Below, the tasks after installing Altibase for the first pod is recorded for testing purposes.
  - Creating an altibase server
  - Start altibase server
  - Create tables(T1, T2, T3) for sample purposes 
  - Generate aku.conf for sample purposes
  - aku start
- Since startupProbe is set, aku must be executed successfully before the next pod is created.

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

- You need to do the same tasks for the rest of the pods.
- After all pods have completed their tasks normally, the status will be as follows.

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

##### Check Altibase replication operation
- The altibase-sts-3 pod connects to the local Altibase with isql and inputs data to the T1 table.
- Access the altibase of the altibase-sts-2 pod with isql from the altibase-sts-3 pod and search the T1 table.

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

##### Check Scale-down operation

- Scale-down with replicas=3.
- Connect to the altibase-sts-2 pod.
- Check that the XSN value of replication AKU_REP_23 is -1, which is the reset state.

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

##### Check Scale-up operation

- Connect to the altibase-sts-0 pod and insert additional data into the T1 table.
- Scale-up with replicas=4.
- Connect to the altibase-sts-3 pod and check if the data additionally inserted in the T1 table is reflected in the scaled-up pod.

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
