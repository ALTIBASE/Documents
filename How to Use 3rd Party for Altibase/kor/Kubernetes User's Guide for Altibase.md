# Kubernetes User's Guide for Altibase

<br/>

<br/>

# 목차

-   [개요](#개요)
-   [파드 생성 및 사용하기](#파드-생성-및-사용하기)
    -   [Altibase 파드 생성](#Altibase-파드-생성)
    -   [퍼시스턴트 볼륨(Persistent Volume) 사용](#퍼시스턴트-볼륨persistent-volume-사용)
    -   [서비스(Service) 사용](#서비스service-사용하기)

-   [파드를 사용하여 Altibase 이중화 하기](#파드를-사용하여-altibase-이중화하기)





# 개요

쿠버네티스(Kubernetes)는 컨테이너화된 애플리케이션의 배포, 스케일링 및 관리를 자동화하는 오픈소스 시스템이다. 쿠버네티스에서 이러한 작업을 처리하는 최소 단위는 파드(Pod)이다. 이 문서는 쿠버네티스 v1.20.4 환경에서 도커 허브(Docker Hub)에 등록된 [Altibase 컨테이너 이미지](https://hub.docker.com/r/altibase/altibase)를 이용하여 Altibase 파드를 생성하고 사용하는 가이드를 제시한다. Altibase 도커 이미지 생성은 [Altibase 도커 가이드](https://aid.altibase.com/pages/viewpage.action?pageId=14057660)를, 기타 쿠버네티스의 세부 기능은 [Kubernetes 홈페이지](https://kubernetes.io/ko/)를 참고한다.



# 파드 생성 및 사용하기

## Altibase 파드 생성

디플로이먼트(Deployment) 워크로드 리소스를 사용하여 생성한 예시와 파드를 직접 생성하는 예시를 소개한다. 일반적으로 파드는 직접 생성하지는 않으며, 워크로드 리소스를 사용하여 생성한다. 

#### 디플로이먼트 워크로드 리소스를 사용하여 파드 생성

디플로이먼트를 생성하는 yaml 파일 예시와 파드 생성 상태를 확인하는 방법이다.

##### 1. yaml 파일 작성

```yaml
# 파일명 : altibase-deploy-pod.yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: altibase-deploy-pod            # 디플로이먼트 이름 설정
spec:
  replicas: 1                          # 1개의 altibase-deploy-pod 파드를 생성하는 리플리카셋 설정
  selector:
    matchLabels:
      app: altibase-deploy-pod
  template:
    metadata:
      labels:
        app: altibase-deploy-pod       # 파드 이름 설정
    spec:
      containers:
      - image: altibase/altibase       # 컨테이너에서 실행할 도커 허브의 Altibase 이미지
        name: altibase                 # 컨테이너 이름
        ports:
        - containerPort: 20300         # 컨테이너 외부로 노출할 포트 (Altibase 서비스 포트)
          protocol: TCP
        env:
        - name: MODE                   # altibase/altibase 이미지 시작 모드 설정
          value: daemon
```

> template.spec.containers.env 필드에 추가하는 Altibase 서버 구동 시 설정할 환경 변수는 [Docker Hub 페이지](https://hub.docker.com/r/altibase/altibase)를 참고한다.

##### 2. 파드 배포

```bash
$ kubectl create -f altibase-deploy-pod.yaml
deployment.apps/altibase-deploy-pod created
```

##### 3. 파드 생성 확인

```bash
$ kubectl get pod -o wide
NAME                  READY   STATUS    RESTARTS   AGE   IP              NODE    NOMINATED NODE   READINESS GATES
altibase-deploy-pod   1/1     Running   0          24s   172.16.135.38   node3   <none>           <none>
```

##### 4. Altibase 서버 접속

```
$ kubectl exec -it altibase-deploy-pod -- /bin/bash
altibase@altibase-pod:~$ is
-----------------------------------------------------------------
     Altibase Client Query utility.
     Release Version 7.1.0.5.1
     Copyright 2000, ALTIBASE Corporation or its subsidiaries.
     All Rights Reserved.
-----------------------------------------------------------------
ISQL_CONNECTION = TCP, SERVER = localhost, PORT_NO = 20300
iSQL> SELECT * FROM TAB;
```

<br/>

#### 파드 직접 생성

altibase/altibase 이미지를 실행하는 컨테이너로 구성되는 파드를 직접 생성하는 yaml 파일 예시와 파드 생성 상태를 확인하는 방법이다.

##### 1. yaml 파일 작성

```yaml
# 파일명 : altibase-pod.yaml
apiVersion: v1
kind: Pod
metadata:
  labels:
    app: altibase
  name: altibase-pod                   # 파드 이름 설정
spec:
  containers:
  - image: altibase/altibase           # 컨테이너에서 실행한 도커 허브 이미지
    name: altibase
    ports:
    - containerPort: 20300             # 컨테이너 외부로 노출할 포트 번호 (Altibase 서비스 포트)
      protocol: TCP
    env:
    - name: MODE                       # altibase/altibase 이미지 시작 모드 설정
      value: daemon
```

> spec.containers.env 필드에 추가하는 Altibase 서버 구동 시 설정할 환경 변수는 [Docker Hub 페이지](https://hub.docker.com/r/altibase/altibase)를 참고한다.

##### 2. 파드 배포

```bash
$ kubectl create -f altibase-pod.yaml
pod/altibase-pod created
```

##### 3. 파드 생성 확인

```bash
$ kubectl get pod -o wide
NAME           READY   STATUS    RESTARTS   AGE   IP              NODE    NOMINATED NODE   READINESS GATES
altibase-pod   1/1     Running   0          11m   172.16.135.37   node3   <none>           <none>
```

##### 4. Altibase 서버 접속

```
$ kubectl exec -it altibase-pod -- /bin/bash
altibase@altibase-pod:~$
altibase@altibase-pod:~$ is
-----------------------------------------------------------------
     Altibase Client Query utility.
     Release Version 7.1.0.5.1
     Copyright 2000, ALTIBASE Corporation or its subsidiaries.
     All Rights Reserved.
-----------------------------------------------------------------
ISQL_CONNECTION = TCP, SERVER = localhost, PORT_NO = 20300
iSQL> SELECT * FROM TAB;
```

#### 

## 퍼시스턴트 볼륨(Persistent Volume) 사용

파드가 임의의 이유로 종료되어 새로 생성할 경우 기존 파드 내부에 저장되어 있던 모든 데이터는 휘발된다. 파드의 종료 여부와 상관없이 데이터를 보존하기 위해 쿠버네티스는 데이터를 저장하는 외장 디스크를 추상화 한 다양한 종류의 [볼륨(Volume)](https://kubernetes.io/ko/docs/concepts/storage/volumes/)을 제공한다. 볼륨에 대한 설명과 자세한 사용법에 대해서는 [Kubernetes 홈페이지](https://kubernetes.io/docs/concepts/storage/volumes/#types-of-volumes)를 참고한다.

아래 예시는 [NFS (Network File System)](https://kubernetes.io/ko/docs/concepts/storage/volumes/#nfs) 볼륨을 사용한 디플로이먼트를 생성하는 yaml 파일 예시이다. DB 데이터 파일과 온라인 로그 파일의 경로를 NFS 볼륨으로 설정한다. 

##### 1. yaml 파일 작성

```yaml
# 파일명 : altibase-deploy-vol-node1.yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: altibase-deploy-vol-node1
spec:
  replicas: 1
  selector:
    matchLabels:
      app: altibase-node1
  template:
    metadata:
      labels:
        app: altibase-node1
    spec:
      containers:
      - name: altibase
        image: altibase/altibase
        volumeMounts:    # spec.volumes.name에서 지정한 볼륨을 컨테이너에 마운트할 위치 선언
        - name: altibase-nfs-dbs                         # volumes.name에서 지정한 볼륨(DB 데이터 파일 용도)
          mountPath: /home/altibase/altibase_home/dbs    # altibase-nfs-dbs 볼륨에서 사용할 디렉토리 지정
        - name: altibase-nfs-logs                        # volumes.name에서 지정한 볼륨(온라인 로그 파일 용도)
          mountPath: /home/altibase/altibase_home/logs   # altibase-nfs-logs 볼륨에서 사용할 디렉토리 지정
        ports:
        - containerPort: 20300                           # Altibase 서비스 포트 설정
          protocol: TCP
        env:
        - name: MODE
          value: daemon
      volumes:
      - name: altibase-nfs-dbs                           # 파드에 제공할 볼륨 지정(DB 데이터 파일 용도)
        nfs:                                             # altibase-nfs-dbs 볼륨의 유형 지정
          server: 192.168.204.139                        # NFS 서버 IP
          path: /home/altibase-nfs/node1/dbs             # NFS 서버의 디렉토리 지정
      - name: altibase-nfs-logs                          # 파드에 제공할 볼륨 지정(온라인 로그 파일 용도)
        nfs:                                             # altibase-nfs-logs 볼륨의 유형 지정
          server: 192.168.204.139                        # NFS 서버 IP
          path: /home/altibase-nfs/node1/logs            # NFS 서버의 디렉토리 지정
```

##### 2. NFS 볼륨을 사용하는 파드 배포 및 파드 생성 확인

```bash
$ kubectl create -f altibase-deploy-vol-node1.yaml
deployment.apps/altibase-deploy-vol-node1 created

$ kubectl get pod
NAME                                         READY   STATUS    RESTARTS   AGE
altibase-deploy-pod-7b799d6b5b-x2bbp         1/1     Running   0          71m
altibase-deploy-vol-node1-7c958dcff6-65trv   1/1     Running   0          30s
```



## 서비스(Service) 사용하기

파드를 생성할 때마다 동적으로 새로운 IP 주소가 할당된다. 쿠버네티스의 [서비스(Service)](https://kubernetes.io/ko/docs/concepts/services-networking/service/) 리소스를 이용하여 고정 IP로 Altibase 서버에 접근할 수 있다. 서비스를 생성하면 정적 IP가 할당되고 서비스가 존재하는 동안 변경되지 않는다. 

다음은 서비스와 Altibase 파드 2개를 생성하고 고정 IP를 이용해 한 노드에서 다른 노드의 Altibase 서버에 접속한 예이다.

##### 1. yaml 파일 생성

```yaml
#파일명 : altibase_pod_svc.yaml

apiVersion: v1
kind: Pod
metadata:
  labels:
    app: altibase-pod1
  name: altibase-pod1
spec:
  containers:
  - image: altibase/altibase      # 컨테이너에서 실행한 도커 허브 이미지
    name: altibase
    ports:
    - containerPort: 20300        # 컨테이너 외부로 노출할 포트 번호 (Altibase 서비스 포트)
      protocol: TCP
    env:
    - name: MODE                  # altibase/altibase 이미지 시작 모드 설정
      value: daemon               # daemon : Altibase 서버 프로세스 
 
 
---
apiVersion: v1
kind: Pod
metadata:
  labels:
    app: altibase-pod2
  name: altibase-pod2
spec:
  containers:
  - image: altibase/altibase      # 컨테이너에서 실행한 도커 허브 이미지
    name: altibase
    ports:
    - containerPort: 20300        # 컨테이너 외부로 노출할 포트 번호 (Altibase 서비스 포트)
      protocol: TCP
    env:
    - name: MODE                  # altibase/altibase 이미지 시작 모드 설정
      value: daemon               
  
--- 
apiVersion: v1
kind: Service                     # 서비스 생성
metadata:
  name: altibase-service
spec:
  ports:
  - port: 20300                   # 보통 port와 targetport는 같은 값으로 설정
    targetPort: 20300             # 서비스로 들어온 요청을 전달할 파드가 LISTEN하고 있는 포트
  selector:
    app: altibase-pod1            # 서비스가 요청을 전달할 파드
```

##### 2. 서비스 배포 및 생성 확인

파드와 서비스를 생성한다.

```yaml
$ kubectl create -f altibase_pod_svc.yaml
```

생성된 파드와 서비스 상태를 확인한다. altibase-service 서비스에 고정 IP 10.98.64.213이 할당되었다. 

```yaml
$ kubectl get pod,service -o wide
NAME                READY   STATUS    RESTARTS   AGE   IP               NODE        NOMINATED NODE   READINESS GATES
pod/altibase-pod1   1/1     Running   0          12m   172.16.169.142   k8s-node2   <none>           <none>
pod/altibase-pod2   1/1     Running   0          12m   172.16.107.198   k8s-node3   <none>           <none>


NAME                       TYPE        CLUSTER-IP     EXTERNAL-IP   PORT(S)     AGE   SELECTOR
service/altibase-service   ClusterIP   10.98.64.213   <none>        20300/TCP   10m   app=altibase-pod1    
```

##### 3. 서비스에 할당된 고정IP 로 Altibase 서버에 접속

altibase-pod2에서 iSQL을 이용해서 서비스에 할당된 고정IP로 altibase-pod1에 구동한 Altibase 서버에 접속하는 예이다. 

```bash

$ k exec -it altibase-pod2 -- /bin/bash

[altibase@altibase-pod2 ~] $ . set_altibase.env
[altibase@altibase-pod2:~$ is -s 10.98.64.213 -port 20300 -u sys -p manager     # 서비스에 할당된 고정IP 사용
-----------------------------------------------------------------
     Altibase Client Query utility.
     Release Version 7.1.0.1.6
     Copyright 2000, ALTIBASE Corporation or its subsidiaries.
     All Rights Reserved.
-----------------------------------------------------------------
ISQL_CONNECTION = TCP, SERVER = 10.98.64.213, PORT_NO = 20300
iSQL>
```



# 파드를 사용하여 Altibase 이중화하기

디플로이먼트, 서비스,  컨피그맵을 이용하여 Altibase 이중화 객체 생성 방법을 설명한다. 파드는 생성할 때마다 동적 IP가 부여되기 때문에 Altibase 이중화 생성 구문에 원격 서버의 IP 대신 호스트 네임을 사용한다.  

아래는 디플로이먼트로 고정된 DNS 이름을 갖는 파드 생성 및 파드를 가리키는 서비스 생성하고 Altibase 서버에 접속하여 이중화 객체를 생성하고 수행 여부를 확인하는 예시이다. 파드는 생성할 때마다 동적 IP가 부여되기 때문에 Altibase 이중화 생성 구문에 원격 서버의 IP 대신 호스트 네임을 사용한 예이다.

##### 1. yaml 파일 작성

***NoK랑 예제가 다름. 확인 후 재작성***

디플로이먼트를 사용하여 2개의 파드를 생성한다. 

```yaml
# 파일명 : 
apiVersion: apps/v1
kind: Deployment
metadata:
  name: altibase-deploy-vol-node1
spec:
  replicas: 1
  selector:
    matchLabels:
      app: altibase-node1
  template:
    metadata:
      labels:
        app: altibase-node1
    spec:
      containers:
      - name: altibase
        image: altibase/altibase
        volumeMounts:
        - name: altibase-nfs-dbs
          mountPath: /home/altibase/altibase_home/dbs
        - name: altibase-nfs-logs
          mountPath: /home/altibase/altibase_home/logs
        ports:
        - containerPort: 20300
          protocol: TCP
        - containerPort: 20301
          protocol: TCP
        env:
        - name: MODE
          value: replication
        - name: SLAVE_REP_PORT  # 이중화 활성화
          value: "20301"        # 사용할 이중화 포트
      volumes:
      - name: altibase-nfs-dbs
        nfs:
          server: 192.168.204.139
          path: /home/altibase-nfs/node1/dbs
      - name: altibase-nfs-logs
        nfs:
          server: 192.168.204.139
          path: /home/altibase-nfs/node1/logs

---

apiVersion: apps/v1
kind: Deployment
metadata:
  name: altibase-deploy-vol-node2
spec:
  replicas: 1
  selector:
    matchLabels:
      app: altibase-node2
  template:
    metadata:
      labels:
        app: altibase-node2
    spec:
      containers:
      - name: altibase
        image: altibase/altibase
        volumeMounts:
        - name: altibase-nfs-dbs
          mountPath: /home/altibase/altibase_home/dbs
        - name: altibase-nfs-logs
          mountPath: /home/altibase/altibase_home/logs
        ports:
        - containerPort: 20300
          protocol: TCP
        - containerPort: 20301
          protocol: TCP
        env:
        - name: MODE
          value: replication
        - name: SLAVE_REP_PORT
          value: "20301"
      volumes:
      - name: altibase-nfs-dbs
        nfs:
          server: 192.168.204.139
          path: /home/altibase-nfs/node2/dbs
      - name: altibase-nfs-logs
        nfs:
          server: 192.168.204.139
          path: /home/altibase-nfs/node2/logs
```

2. ##### 서비스를 생성하는 yaml 작성

생성된 파드와 대응되는 2개의 서비스를 생성하는 YAML 파일

```
apiVersion: v1
kind: Service
metadata:
  labels:
    app: altibase
  name: altibase-svc-node1
spec:
  type: NodePort
  ports:
  - name: service-port
    port: 20300
    targetPort: 20300
    nodePort: 30001
  - name: replication-port
    port: 20301
    targetPort: 20301
  selector:
    app: altibase-node1

---

apiVersion: v1
kind: Service
metadata:
  labels:
    app: altibase
  name: altibase-svc-node2
spec:
  type: NodePort
  ports:
  - name: service-port
    port: 20300
    targetPort: 20300
    nodePort: 30002
  - name: replication-port
    port: 20301
    targetPort: 20301
  selector:
    app: altibase-node2
```

##### 3. 파드와 서비스 배포 및 확인

##### 4. 이중화 상태 및 동작 확인

각각의 파드의 Altibase 컨테이너에서 서비스와 동일한 이름으로 이중화 객체 생성

| **파드 1의 Altibase 컨테이너**                               | 파드 2의 Altibase 컨테이너                                   |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| -- 이중화 테이블 생성<br />create table t1 (c1 integer primary key, c2 integer);<br/><br />-- 이중화 객체 생성<br />CREATE REPLICATION rep1 WITH **'altibase-svc-node2'**, 20301 FROM sys.t1 TO sys.t1;<br/><br />-- 이중화 Start<br />alter replication rep1 start; | -- 이중화 대상 테이블 생성<br />create table t1 (c1 integer primary key, c2 integer);<br/><br />-- 이중화 객체 생성<br />CREATE REPLICATION rep1 WITH **'altibase-svc-node1'**, 20301 FROM sys.t1 TO sys.t1;<br/><br />-- 이중화 Start<br />alter replication rep1 start; |



| **파드 1의 Altibase 컨테이너**                               | 파드 2 Altibase 컨테이너                                     |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| iSQL> INSERT INTO t1 VALUES(1, 1);<br/>1 row inserted.       |                                                              |
| iSQL> SELECT * FROM t1;<br/>C1     C2<br/>\---------------------------<br/>1      1<br/>1 rows selected. | iSQL> SELECT * FROM t1;<br/>C1     C2<br/>\---------------------------<br/>1      1<br/>1 rows selected. |
|                                                              | iSQL> INSERT INTO t1 VALUES (2, 2);<br/>1 row inserted.      |
| iSQL> SELECT * FROM t1;<br/>C1     C2<br/>\---------------------------<br/>1      1<br/>2      2<br/>2 rows selected. | iSQL> SELECT * FROM t1;<br/>C1     C2<br/>\---------------------------<br/>1      1<br/>2      2<br/>2 rows selected. |

##### 5. 이중화 노드 추가

##### 6. 이중화 노드 삭제
