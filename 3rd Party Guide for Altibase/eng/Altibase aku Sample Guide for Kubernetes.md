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
- In this example, the ubuntu:18.04 docker image registered at https://hub.docker.com/ was used for testing purposes.
- In a real environment, you can use a Linux docker image suitable for each purpose.
- You need to change set_linux.env to match the Linux docker image that will actually be used. Please refer to the documents below.
  - Altibase Installation Manual
  - Linux Setup Guide for Altibase ( https://aid.altibase.com/display/arch/Linux+Setup+Guide+for+Altibase )

###### - To use Kubernetes, a hostname-based license must be issued from Altibase.
###### - In this example, 4 pods are created, so 4 licenses are required.

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
      echo `date` "${MY_POD_NAME}: Next pod will be started after aku is started successfully because of startupProbe setti                                                                  ng."
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
        image: altibase/7.1-bare
        command:
        - /bin/bash
        - "-c"
        - /home/altibase/config_map/entry_point.sh
        ports:
        - containerPort: 20300
          protocol: TCP
        - containerPort: 20301
          protocol: TCP
        resources:
          requests:
            cpu: 250m
          limits:
            cpu: 3 
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
          mountPath: /home/altibase/config_map
          readOnly: true
      volumes:
        - name: altibase-cm
          configMap:
            name: altibase-cm
            defaultMode: 0777
            items:
            - key: "license"
              path: "license"
            - key: "set_altibase.env"
              path: "set_altibase.env"
            - key: "aku.conf"
              path: "aku.conf"
            - key: "sample_schema.sql"
              path: "sample_schema.sql"
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

```
$ kubectl get sts -o wide
NAME                 READY   AGE    CONTAINERS               IMAGES
altibase-sts         4/4     12m    altibase-sts             altibase/7.1-bare

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
$ kubectl exec -it altibase-sts-3 -- /bin/bash
root@altibase-sts-3:/# . /home/altibase/config_map/set_altibase.env
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
$ kubectl exec -it altibase-sts-2 -- /bin/bash
root@altibase-sts-2:/# . /home/altibase/config_map/set_altibase.env
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
$ kubectl exec -it altibase-sts-0 -- /bin/bash
root@altibase-sts-0:/# . /home/altibase/config_map/set_altibase.env
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
$ kubectl exec -it altibase-sts-3 -- /bin/bash
root@altibase-sts-3:/# . /home/altibase/config_map/set_altibase.env
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
