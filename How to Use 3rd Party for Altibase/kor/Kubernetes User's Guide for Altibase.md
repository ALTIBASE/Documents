# Kubernetes User's Guide for Altibase

-   [개요](#개요)
-   [파드 생성 및 사용하기](#파드-생성-및-사용하기)
    -   [쿠버네티스에서 Altibase 파드 생성하기](#쿠버네티스에서-Altibase-파드-생성하기)
    -   [Persistent Volume 사용하기](#Persistent-Volume-사용하기)
    -   [서비스 사용하기](#서비스-사용하기)

-   [파드를 사용하여 Altibase 이중화하기](#파드를-사용하여-Altibase-이중화하기)



쿠버네티스(Kubernetes) 환경에서 Altibase를 사용하기 위한 가이드를 제시한다.



## 개요

쿠버네티스(Kubernetes)는 컨테이너화된 애플리케이션의 배포, 스케일링 및 관리를 자동화하는 오픈소스 시스템이다. 쿠버네티스에서 이러한 작업을 처리하는 최소 단위는 파드(Pod)이다. 이 문서는 쿠버네티스 v1.20.4 환경에서 도커 허브(Docker Hub)에 등록된 [Altibase 컨테이너 이미지](https://hub.docker.com/r/altibase/altibase)를 이용하여 Altibase 파드를 생성하고 사용하는 가이드를 제시한다. Altibase 도커 이미지 생성은 [Altibase 도커 가이드](https://aid.altibase.com/pages/viewpage.action?pageId=14057660)를, 기타 쿠버네티스의 세부 기능은 [Kubernetes 홈페이지](https://kubernetes.io/ko/)를 참고한다.



## 파드 생성 및 사용하기

### 쿠버네티스에서 Altibase 파드 생성하기

파드를 직접 생성하는 예시와 디플로이먼트(Deployment) 워크로드 리소스를 사용하여 생성한 예시를 소개한다. 일반적으로 파드는 직접 생성하지는 않으며, 워크로드 리소스를 사용하여 생성한다. 아래는 디플로이먼트 생성 예시이다. 1개의 altibase-deploy-pod 파드를 불러오기 위한 레플리카셋을 생성한다.

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
        - containerPort: 20300        # 컨테이너 외부로 노출할 포트 (서비스 포트)
          protocol: TCP
        env:
        - name: MODE                  # 컨테이너의 시작 모드
          value: daemon
```

altibase/altibase 이미지를 실행하는 컨테이너로 구성되는 파드를 생성하는 예시이다.

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
    - containerPort: 20300        # 컨테이너 외부로 노출할 포트 번호 (서비스 포트)
      protocol: TCP
    env:
    - name: MODE                  # 컨테이너의 시작 모드
      value: daemon
```



### Persistent Volume 사용하기


파드가 임의의 이유로 종료되어 새로 생성할 경우 기존 파드 내부에 저장되어 있던 모든 데이터는 휘발된다. 파드의 종료 여부와 상관없이 데이터를 보존하기 위해 쿠버네티스는 데이터를 저장하는 외장 디스크를 추상화 한 [볼륨(Volume)](https://kubernetes.io/ko/docs/concepts/storage/volumes/)을 제공한다. 볼륨은 다양한 종류가 있는데 아래 예시는 [NFS (Network File System)](https://kubernetes.io/ko/docs/concepts/storage/volumes/#nfs) 볼륨을 사용하여 DB 데이터 파일과 온라인 로그 파일을 생성하는 방법을 보여준다. 이외 볼륨에 대한 설명과 자세한 사용법에 대해서는 [Kubernetes 홈페이지](https://kubernetes.io/docs/concepts/storage/volumes/#types-of-volumes)를 참고한다.

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
        - name: altibase-nfs-dbs                         # 아래 쪽의 NFS의 볼륨과 매칭하기 위한 이름 지정
          mountPath: /home/altibase/altibase_home/dbs    # 파드의 altibase 데이터 파일 디렉토리 패스
        - name: altibase-nfs-logs                        # 아래 쪽의 NFS의 볼륨과 매칭하기 위한 이름 지정
          mountPath: /home/altibase/altibase_home/logs   # pod의 altibase 로그 파일 디렉토리 패스
        ports:
        - containerPort: 20300                           # altibase에 접속할 수 있는 포트 노출
          protocol: TCP
        env:
        - name: MODE
          value: daemon
      volumes:
      - name: altibase-nfs-dbs                           # 위 쪽 volumeMounts에서 지정해준, 실제 마운트할 이름을 지정 (데이터 파일)
        nfs:                                             # 네트워크 볼륨 타입 중 NFS를 사용
          server: 192.168.204.139                        # 접근할 수 있는 NFS 서버 IP
          path: /home/altibase-nfs/node1/dbs             # NFS 서버의 저장될 위치 저정
      - name: altibase-nfs-logs                          # 위 쪽 volumeMounts에서 지정해준, 실제 마운트할 이름을 지정 (로그 파일)
        nfs:                                             # 네트워크 볼륨 타입 중 NFS를 사용
          server: 192.168.204.139                        # 접근할 수 있는 NFS 서버 IP
          path: /home/altibase-nfs/node1/logs            # NFS 서버의 저장될 위치 저정
```



### 서비스 사용하기


파드를 신규로 생성할 때마다 새로운 IP 주소가 부여되나 쿠버네티스의 [서비스(Service)](https://kubernetes.io/ko/docs/concepts/services-networking/service/) 리소스 사용하면 고정 IP처럼 처리할 수 있다. 서비스를 생성하면 얻게 되는 정적 IP는 서비스가 존재하는 동안 변경되지 않는다. 아래는 서비스의 한 종류인 고정포트(Nodeport)를 사용한 예시이며 다른 유형에 대해서는 [Kubernetes 홈페이지](https://kubernetes.io/docs/tutorials/services/source-ip/)를 참고한다.

```
apiVersion: v1
kind: Service
metadata:
  labels:
    app: altibase
  name: altibase-svc-node1
spec:
  type: NodePort               # NodePort 사용
  ports:                       
  - name: service-port
    port: 20300                # 서비스가 사용할 클러스터 포트
    targetPort: 20300          # 서비스에서 전달될 컨테이너 포트
    nodePort: 30001            # 물리 노드의 포트
  selector:
    app: altibase-node1        # 해당 서비스가 적용될 파드의 라벨 명칭
```

위와 같이 설정했다면 쿠버네티스로 클러스터링된 어느 서버든 30001 포트로 할당된 Altibase 파드에 접근할 수 있다.



## 파드를 사용하여 Altibase 이중화하기


파드는 재 생성 시 IP가 새로 부여되기 때문에 Altibase 이중화 생성은 Peer 서버의 원격 호스트 IP 대신 원격 호스트 네임으로 생성해야 한다. 쿠버네티스 에서는 파드를 가리키는 서비스를 생성함으로써, 파드가 고정된 DNS 이름을 갖도록 처리할 수 있어서 해당 서비스 이름으로 이중화 객체를 생성해야 된다. 아래는 디플로이먼트를 통한 파드 생성과 그와 대응되는 서비스 생성, 그리고 Altibase 컨테이너에 접속하여 이중화 생성 후 수행 여부를 확인하는 예시이다.

1. 디플로이먼트를 사용하여 파드를 생성하는 YAML 파일

| 디플로이먼트 1                                               | 디플로이먼트 2                                               |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| apiVersion: apps/v1<br/>kind: Deployment<br/>metadata:<br/>　name: altibase-deploy-vol-node1<br/>spec:<br/>　replicas: 1<br/>　selector:<br/>　　matchLabels:<br/>　　　app: altibase-node1<br/>　template:<br/>　　metadata:<br/>　　　labels:<br/>　　　　app: altibase-node1<br/>　　spec:<br/>　　　containers:<br/>　　　- name: altibase<br/>　　　　image: altibase/altibase<br/>　　　　volumeMounts:<br/>　　　　- name: altibase-nfs-dbs<br/>　　　　　mountPath: /home/altibase/altibase_home/dbs<br/>　　　　- name: altibase-nfs-logs<br/>　　　　　mountPath: /home/altibase/altibase_home/logs<br/>　　　　ports:<br/>　　　　- containerPort: 20300<br/>　　　　　protocol: TCP<br/>　　　　- containerPort: 20301<br/>　　　　　protocol: TCP<br/>　　　　env:<br/>　　　　- name: MODE<br/>　　　　　value: replication<br/>　　　　- name: **SLAVE_REP_PORT** # 이중화 활성화<br/>　　　　　value: **"20301"** # 사용할 이중화 포트<br/>　　　volumes:<br/>　　　- name: altibase-nfs-dbs<br/>　　　　nfs:<br/>　　　　　server: 192.168.204.139<br/>　　　　　path: /home/altibase-nfs/node1/dbs<br/>　　　- name: altibase-nfs-logs<br/>　　　　nfs:<br/>　　　　　server: 192.168.204.139<br/>　　　　　path: /home/altibase-nfs/node1/logs | apiVersion: apps/v1<br/>kind: Deployment<br/>metadata:<br/>  name: altibase-deploy-vol-node2<br/>spec:<br/>  replicas: 1<br/>  selector:<br/>    matchLabels:<br/>      app: altibase-node2<br/>  template:<br/>    metadata:<br/>      labels:<br/>        app: altibase-node2<br/>    spec:<br/>      containers:<br/>      - name: altibase<br/>        image: altibase/altibase<br/>        volumeMounts:<br/>        - name: altibase-nfs-dbs<br/>          mountPath: /home/altibase/altibase_home/dbs<br/>        - name: altibase-nfs-logs<br/>          mountPath: /home/altibase/altibase_home/logs<br/>        ports:<br/>        - containerPort: 20300<br/>          protocol: TCP<br/>        - containerPort: 20301<br/>          protocol: TCP<br/>        env:<br/>        - name: MODE<br/>          value: replication<br/>        - name: **SLAVE_REP_PORT**<br/>          value: **"20301"**<br/>      volumes:<br/>      - name: altibase-nfs-dbs<br/>        nfs:<br/>          server: 192.168.204.139<br/>          path: /home/altibase-nfs/node2/dbs<br/>      - name: altibase-nfs-logs<br/>        nfs:<br/>          server: 192.168.204.139<br/>          path: /home/altibase-nfs/node2/logs |

2. 서비스를 생성하는 YAML 파일

| 서비스 1                                                     | 서비스 2                                                     |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| apiVersion: v1<br/>kind: Service<br/>metadata:<br/>  labels:<br/>    app: altibase<br/>  name: **altibase-svc-node1**<br/>spec:<br/>  type: NodePort<br/>  ports:<br/>  - name: service-port<br/>    port: 20300<br/>    targetPort: 20300<br/>    nodePort: 30001<br/>  - name: replication-port<br/>    port: 20301<br/>    targetPort: 20301<br/>  selector:<br/>    app: altibase-node1 | apiVersion: v1<br/>kind: Service<br/>metadata:<br/>  labels:<br/>    app: altibase<br/>  name: **altibase-svc-node2**<br/>spec:<br/>  type: NodePort<br/>  ports:<br/>  - name: service-port<br/>    port: 20300<br/>    targetPort: 20300<br/>    nodePort: 30002<br/>  - name: replication-port<br/>    port: 20301<br/>    targetPort: 20301<br/>  selector:<br/>    app: altibase-node2 |

3. 각각의 파드의 Altibase 컨테이너에서 서비스와 동일한 이름으로 이중화 객체 생성

| **파드 1의 Altibase 컨테이너**                               | 파드 2의 Altibase 컨테이너                                   |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| -- 이중화 테이블 생성<br />create table t1 (c1 integer primary key, c2 integer);<br/><br />-- 이중화 객체 생성<br />CREATE REPLICATION rep1 WITH **'altibase-svc-node2'**, 20301 FROM sys.t1 TO sys.t1;<br/><br />-- 이중화 Start<br />alter replication rep1 start; | -- 이중화 대상 테이블 생성<br />create table t1 (c1 integer primary key, c2 integer);<br/><br />-- 이중화 객체 생성<br />CREATE REPLICATION rep1 WITH **'altibase-svc-node1'**, 20301 FROM sys.t1 TO sys.t1;<br/><br />-- 이중화 Start<br />alter replication rep1 start; |

4. 이중화 작동 확인

| **파드 1의 Altibase 컨테이너**                               | 파드 2 Altibase 컨테이너                                     |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| iSQL> insert into t1 values (1, 1);<br/>1 row inserted.      |                                                              |
| iSQL> select * from t1;<br/>C1     C2<br/>\---------------------------<br/>1      1<br/>1 rows selected. | iSQL> select * from t1;<br/>C1     C2<br/>\---------------------------<br/>1      1<br/>1 rows selected. |
|                                                              | iSQL> insert into t1 values (2, 2);<br/>1 row inserted.      |
| iSQL> select * from t1;<br/>C1     C2<br/>\---------------------------<br/>1      1<br/>2      2<br/>2 rows selected. | iSQL> select * from t1;<br/>C1     C2<br/>\---------------------------<br/>1      1<br/>2      2<br/>2 rows selected. |
