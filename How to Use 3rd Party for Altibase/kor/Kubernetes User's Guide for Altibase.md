# Kubernetes User's Guide for Altibase

-   [개요](#개요)
-   [Kubernetes 에서 Altibase Pod 생성](#Kubernetes-에서-Altibase-Pod-생성)
-   [Persistent Volume 사용](#Persistent-Volume-사용)
-   [Service 사용](#Service-사용)
-   [Altibase 이중화](#Altibase-이중화)



Kubernetes 환경에서 Altibase를 사용하기 위한 가이드를 제시한다.



## 개요

Kubernetes는 컨테이너화된 애플리케이션을 자동으로 배포, 스케일링 및 관리해주는 오픈소스 시스템이다. 애플리케이션은 Kuberentes에서 Pod라는 가장 작은 컴퓨팅 단위로 배포되는데, 본 문서는 Kubernetes(v1.20.4) 환경에서 Docker Hub에 등록된 [Altibase 컨테이너 이미지](https://hub.docker.com/r/altibase/altibase)를 사용하여 Altibase Pod를 생성하여 사용하는 가이드(샘플)를 제시한다. Altibase Docker Image 생성은 [Altibase 도커 가이드](https://aid.altibase.com/pages/viewpage.action?pageId=14057660)를 참조하고, 기타 Kubernetes의 세부 기능은 [Kubernetes 홈페이지](https://kubernetes.io/ko/)를 참조한다.



## Kubernetes 에서 Altibase Pod 생성

- 일반적으로는 Kubernetes의 Pod는 아래와 같이 Deployment나 ReplicaSet과 같은 Kubernetes API 리소스를 사용하여 생성한다. 아래는 Deployment를 사용하여 Pod를 생성하는 예시이다.

  ```
  apiVersion: apps/v1
  kind: Deployment
  metadata:
    name: altibase-deploy-pod
  spec:
    replicas: 1
    selector:
      matchLabels:
        app: altibase-deploy-pod
    template:
      metadata:
        labels:
          app: altibase-deploy-pod
      spec:
        containers:
        - image: altibase/altibase
          name: altibase
          ports:
          - containerPort: 20300        # container 외부로 노출할 port (서비스 port)
            protocol: TCP
          env:
          - name: MODE                  # container의 start mode
            value: daemon
  ```

- Altibase 컨테이너가 포함된 Pod를 직접 생성하는 예시

  ```
  apiVersion: v1
  kind: Pod
  metadata:
    labels:
      app: altibase
    name: altibase-pod
  spec:
    containers:
    - image: altibase/altibase      # docker hub에서 최신 이미지를 가져옴.
      name: altibase
      ports:
      - containerPort: 20300        # container 외부로 노출할 port (서비스 port)
        protocol: TCP
      env:
      - name: MODE                  # container의 start mode
        value: daemon
  ```

  


## Persistent Volume 사용


Pod가 임의의 이유로 종료되어 새로 생성할 경우 기존 Pod 내부에 저장되어 있던 모든 데이터는 휘발된다. Pod의 종료 여부와 상관없이 데이터를 보존하기 위해 Kubernetes는 데이터를 저장하는 외장 디스크를 추상화한 Volume을 제공한다. Volume은 다양한 종류가 있는데 아래 예시는 NFS (Network File System) Persistent Volume을 사용하여 DB 데이터 파일과 리두 로그 파일을 생성하는 방법을 보여준다. 이외 Volume에 대한 설명과 자세한 사용법에 대해서는 [Kubernetes 홈페이지](https://kubernetes.io/docs/concepts/storage/volumes/#types-of-volumes)를 참고한다.

```
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
        - name: altibase-nfs-dbs                         # 아래 쪽의 nfs의 volume과 매칭하기 위한 이름 지정
          mountPath: /home/altibase/altibase_home/dbs    # pod의 altibase data file 디렉토리 path
        - name: altibase-nfs-logs                        # 아래 쪽의 nfs의 volume과 매칭하기 위한 이름 지정
          mountPath: /home/altibase/altibase_home/logs   # pod의 altibase log file 디렉토리 path
        ports:
        - containerPort: 20300                           # altibase에 접속할 수 있는 port 노출
          protocol: TCP
        env:
        - name: MODE
          value: daemon
      volumes:
      - name: altibase-nfs-dbs                           # 위 쪽 volumeMounts에서 지정해준, 실제 mount할 이름을 지정 (data file)
        nfs:                                             # network volume type 중 NFS를 사용
          server: 192.168.204.139                        # 접근할 수 있는 nfs 서버 ip
          path: /home/altibase-nfs/node1/dbs             # nfs 서버의 저장될 위치 저정
      - name: altibase-nfs-logs                          # 위 쪽 volumeMounts에서 지정해준, 실제 mount할 이름을 지정 (log file)
        nfs:                                             # network volume type 중 NFS를 사용
          server: 192.168.204.139                        # 접근할 수 있는 nfs 서버 ip
          path: /home/altibase-nfs/node1/logs            # nfs 서버의 저장될 위치 저정
```



## Service 사용


Pod를 신규로 생성할 때마다 새로운 IP 주소가 부여되나 Kubernetes의 API 리소스 중 하나인 Service를 사용하면 고정 IP처럼 처리할 수 있다. Service를 생성하면 얻게 되는 정적 IP는 Service가 존재하는 동안 변경되지 않는다. 아래는 Service의 한 종류인 Nodeport를 사용한 예시이며 다른 유형에 대해서는 [Kubernetes 홈페이지](https://kubernetes.io/docs/tutorials/services/source-ip/)를 참고한다.

```
apiVersion: v1
kind: Service
metadata:
  labels:
    app: altibase
  name: altibase-svc-node1
spec:
  type: NodePort               # NodePort 사용.
  ports:                       
  - name: service-port
    port: 20300                # service가 사용할 cluster port
    targetPort: 20300          # service에서 forward 될 container port
    nodePort: 30001            # 물리 node의 port
  selector:
    app: altibase-node1        # 해당 service가 적용될 pod의 label 명칭
```

위와 같이 설정 시 Kubernetes로 Clustering된 아무 서버에 접속해도 30001 포트로 할당된 Altibase Pod에 접근할 수 있다.



## Altibase 이중화


Pod는 재 생성 시 ip가 새로 부여되기 때문에 Altibase 이중화 생성은 Peer 서버의 remote host ip 대신 remote host name으로 생성해야 한다. Kubernetes 에서는 Pod를 가리키는 Service를 생성함으로써, Pod가 고정된 DNS Name을 갖도록 처리할 수 있어서 해당 Service 이름으로 이중화 객체를 생성해야 된다. 아래는 Deployment를 통한 Pod 생성과 그와 대응되는 Service 생성, 그리고 Altibase 컨테이너에 접속하여 이중화 생성 후 수행 여부를 확인하는 예시이다.

1. Deployment를 통한 Pod 생성 yaml

| **Deployment 1**                                             | Deployment 2                                                 |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| apiVersion: apps/v1<br/>kind: Deployment<br/>metadata:<br/>  name: altibase-deploy-vol-node1<br/>spec:<br/>  replicas: 1<br/>  selector:<br/>    matchLabels:<br/>      app: altibase-node1<br/>  template:<br/>    metadata:<br/>      labels:<br/>        app: altibase-node1<br/>    spec:<br/>      containers:<br/>      - name: altibase<br/>        image: altibase/altibase<br/>        volumeMounts:<br/>        - name: altibase-nfs-dbs<br/>          mountPath: /home/altibase/altibase_home/dbs<br/>        - name: altibase-nfs-logs<br/>          mountPath: /home/altibase/altibase_home/logs<br/>        ports:<br/>        - containerPort: 20300<br/>          protocol: TCP<br/>        - containerPort: 20301<br/>          protocol: TCP<br/>        env:<br/>        - name: MODE<br/>          value: replication<br/>        - name: **SLAVE_REP_PORT** # 이중화 활성화<br/>          value: **"20301"** # 사용할 이중화 Port<br/>      volumes:<br/>      - name: altibase-nfs-dbs<br/>        nfs:<br/>          server: 192.168.204.139<br/>          path: /home/altibase-nfs/node1/dbs<br/>      - name: altibase-nfs-logs<br/>        nfs:<br/>          server: 192.168.204.139<br/>          path: /home/altibase-nfs/node1/logs | apiVersion: apps/v1<br/>kind: Deployment<br/>metadata:<br/>  name: altibase-deploy-vol-node2<br/>spec:<br/>  replicas: 1<br/>  selector:<br/>    matchLabels:<br/>      app: altibase-node2<br/>  template:<br/>    metadata:<br/>      labels:<br/>        app: altibase-node2<br/>    spec:<br/>      containers:<br/>      - name: altibase<br/>        image: altibase/altibase<br/>        volumeMounts:<br/>        - name: altibase-nfs-dbs<br/>          mountPath: /home/altibase/altibase_home/dbs<br/>        - name: altibase-nfs-logs<br/>          mountPath: /home/altibase/altibase_home/logs<br/>        ports:<br/>        - containerPort: 20300<br/>          protocol: TCP<br/>        - containerPort: 20301<br/>          protocol: TCP<br/>        env:<br/>        - name: MODE<br/>          value: replication<br/>        - name: **SLAVE_REP_PORT**<br/>          value: **"20301"**<br/>      volumes:<br/>      - name: altibase-nfs-dbs<br/>        nfs:<br/>          server: 192.168.204.139<br/>          path: /home/altibase-nfs/node2/dbs<br/>      - name: altibase-nfs-logs<br/>        nfs:<br/>          server: 192.168.204.139<br/>          path: /home/altibase-nfs/node2/logs |

2. Service 생성 yaml

| Service 1                                                    | Service 2                                                    |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| apiVersion: v1<br/>kind: Service<br/>metadata:<br/>  labels:<br/>    app: altibase<br/>  name: **altibase-svc-node1**<br/>spec:<br/>  type: NodePort<br/>  ports:<br/>  - name: service-port<br/>    port: 20300<br/>    targetPort: 20300<br/>    nodePort: 30001<br/>  - name: replication-port<br/>    port: 20301<br/>    targetPort: 20301<br/>  selector:<br/>    app: altibase-node1 | apiVersion: v1<br/>kind: Service<br/>metadata:<br/>  labels:<br/>    app: altibase<br/>  name: **altibase-svc-node2**<br/>spec:<br/>  type: NodePort<br/>  ports:<br/>  - name: service-port<br/>    port: 20300<br/>    targetPort: 20300<br/>    nodePort: 30002<br/>  - name: replication-port<br/>    port: 20301<br/>    targetPort: 20301<br/>  selector:<br/>    app: altibase-node2 |

3. 각 Pod의 Altibase 컨테이너에서 Service 이름으로 이중화 생성

| **Pod 1의 Altibase 컨테이너**                                | Pod 2의 Altibase 컨테이너                                    |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| -- 이중화 테이블 생성<br />create table t1 (c1 integer primary key, c2 integer);<br/><br />-- 이중화 생성<br />CREATE REPLICATION rep1 WITH **'altibase-svc-node2'**, 20301 FROM sys.t1 TO sys.t1;<br/><br />-- 이중화 Start<br />alter replication rep1 start; | -- 이중화 대상 테이블 생성<br />create table t1 (c1 integer primary key, c2 integer);<br/><br />-- 이중화 생성<br />CREATE REPLICATION rep1 WITH **'altibase-svc-node1'**, 20301 FROM sys.t1 TO sys.t1;<br/><br />-- 이중화 Start<br />alter replication rep1 start; |

4. 이중화 테스트

| **Pod 1의 Altibase 컨테이너**                                | Pod 2 Altibase 컨테이너                                      |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| iSQL> insert into t1 values (1, 1);<br/>1 row inserted.      |                                                              |
| iSQL> select * from t1;<br/>C1     C2<br/>\---------------------------<br/>1      1<br/>1 rows selected. | iSQL> select * from t1;<br/>C1     C2<br/>\---------------------------<br/>1      1<br/>1 rows selected. |
|                                                              | iSQL> insert into t1 values (2, 2);<br/>1 row inserted.      |
| iSQL> select * from t1;<br/>C1     C2<br/>\---------------------------<br/>1      1<br/>2      2<br/>2 rows selected. | iSQL> select * from t1;<br/>C1     C2<br/>\---------------------------<br/>1      1<br/>2      2<br/>2 rows selected. |
