# Kubernetes User's Guide for Altibase

-   [개요](#개요)
-   [Kubernetes 에서 Altibase 컨테이너 배포 (Pod 생성)](Kubernetes 에서 Altibase 컨테이너 배포 (Pod 생성))
-   [Persistent Volume 사용](Persistent Volume 사용)
-   정적 ip 사용
-   Altibase 이중화 사용





## 개요

- Kubernetes 에서 Docker Hub에 등록된 

  [Altibase 컨테이너 이미지]: https://hub.docker.com/r/altibase/altibase

  를 이용하여 Pod 생성을 위한 yaml 샘플을 살펴본다.

- Docker Hub에 등록된 Altibase 컨테이너는 제한된 기능을 갖는 테스트 용으로, 실 운영 환경 적용에는 부적합할 수 있다.

- yaml 샘플은 Kubernetes 환경에서 Altibase 컨테이너 기본 동작에 대한 예시로 제공되어, 실 운영 환경 적용에는 부적합할 수 있다.

-   기타 Kubernetes의 세부 기능은 Kubernetes 홈페이지를 참고한다.



### Kubernetes 에서 Altibase 컨테이너 배포 (Pod 생성)

- Altibase 컨테이너가 포함된 Pod를 직접 생성

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
  
- 위와 같이 Pod를 직접 생성하기도 하지만, Deployment 나 ReplicaSet 과 같은 Kubernetes api-resource를 사용하여 생성하는 게 일반적이다.

- Deployment를 사용하여 Pod를 생성

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

  

### Persistent Volume 사용


Pods are ephemeral. DBMS의 특성상 Pod가 종료되더라도 주요 파일은 계속 유지되어야 하기 때문에 Persistent Volume에 생성하여 접근하도록 해야한다. Kubernetes에서는 추상화된 다양한 Persistent Volume을 제공하는데, 아래는 그 중 NFS 사용 예시이다. 기타 다른 Volume 및 사용법에 대해서는 Kubernete 홈페이지를 참고한다.

-   Deployment를 이용하여 NFS에 DB Data 파일 및 DB Redo Log 파일을 생성하도록 하는 예시
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
            - name: altibase-nfs-dbs                          # 아래 쪽의 nfs의 volume과 매칭하기 위한 이름 지정
              mountPath: /home/altibase/altibase_home/dbs     # pod의 altibase data file 디렉토리 path
            - name: altibase-nfs-logs                         # 아래 쪽의 nfs의 volume과 매칭하기 위한 이름 지정
              mountPath: /home/altibase/altibase_home/logs    # pod의 altibase log file 디렉토리 path
            ports:
            - containerPort: 20300                            # altibase에 접속할 수 있는 port 노출
              protocol: TCP
            env:
            - name: MODE
              value: daemon
          volumes:
          - name: altibase-nfs-dbs                            # 위 쪽의 volumeMounts에서 지정해준, 실제 mount할 이름을 지정 (data file)
            nfs:                                              # network volume type 중 NFS를 사용
              server: 192.168.204.139                         # 접근할 수 있는 nfs 서버 ip
              path: /home/altibase-nfs/node1/dbs              # nfs 서버의 저장될 위치 저정
          - name: altibase-nfs-logs                           # 위 쪽의 volumeMounts에서 지정해준, 실제 mount할 이름을 지정 (log file)
            nfs:                                              # network volume type 중 NFS를 사용
              server: 192.168.204.139                         # 접근할 수 있는 nfs 서버 ip
              path: /home/altibase-nfs/node1/logs             # nfs 서버의 저장될 위치 저정
    ```
    
    

### 정적 ip 사용


Pod는 생성될 때마다 ip가 새로 부여되기 때문에 고정된 ip처럼 사용하기 위해서는 Kubernetes의 Service를 사용해야 된다. Service가 생성되면 정적 ip를 얻게되고 Service가 존재하는 동안 해당 ip는 변경되지 않는다. 아래는 Service 중 Nodeport 사용 예시이며 기타 다른 Service 및 사용법에 대해서는 Kubernete 홈페이지 내용을 참고한다.

- Nodeport를 사용하여 Service 를 생성하는 예시

  ```
  apiVersion: v1
  kind: Service
  metadata:
    labels:
      app: altibase
    name: altibase-svc-node1
  spec:
    type: NodePort               # NodePort 사용. 각 Node의 지정된 PORT를 할당하는 방식으로 클러스터 내부/외부 모두 접속 가능
    ports:                       # service-port와 replication-port 2개의 port를 node port로 지정
    - name: service-port
      port: 20300                # service가 사용할 cluster port
      targetPort: 20300          # service에서 forward 될 container port
      nodePort: 30001            # 물리 node의 port
    selector:
      app: altibase-node1        # 해당 service가 적용될 pod의 label 명칭
  ```

- 위와 같이 설정 시 Kubernetes로 Clustering된 아무 서버에 접속해도 30001 포트로 할당된 Altibase Pod에 접근할 수 있다.



### Altibase 이중화 사용


Pod는 재 생성 시 ip가 새로 부여되기 때문에 Altibase 이중화 생성은 Peer서버의 remote host ip 대신 remote host name으로 생성해야 한다. Kubernetes 에서는 Pod를 가리키는 Service를 생성함으로써, Pod가 고정된 DNS Name을 갖도록 처리할 수 있어서 해당 Service 이름으로 이중화 객체를 생성하면 된다.

- 아래 예시는 Deployment를 통한 Pod 생성과 그와 대응되는 Service 생성, 그리고 이중화의 동작 여부를 확인해 보기 위해 ConfigMap을 통해 Service 이름을 줘서 이중화 객체를 생성한 예시이다.

  | **altibase-node1.yaml**<br />(Configmap/Deployment/Service 생성) | **altibase-node2.yaml**<br />(Configmap/Deployment/Service 생성) |
  | ------------------------------------------------------------ | ------------------------------------------------------------ |
  | apiVersion: v1<br />kind: ConfigMap<br />metadata:<br />  name: dbobj-configmap-node1<br />data:<br />  crt_obj.sql: \|+<br />    create table t1 (c1 integer primary key, c2 integer);<br />    create replication rep1 with 'altibase-svc-node2',20301 from sys.t1 to sys.t1;<br />    exec sleep(30); # peer server 생성 대기 목적<br />    alter replication rep1 start;<br /><br />---<br /><br />apiVersion: apps/v1<br />kind: Deployment<br />metadata:<br />  name: altibase-deploy-vol-node1<br />spec:<br />  replicas: 1<br />selector:<br />  matchLabels:<br />      app: altibase-node1<br />  template:<br />    metadata:<br />      labels:<br />        app: altibase-node1<br />    spec:<br />      containers:<br />      - name: altibase<br />        image: altibase/altibase<br />        volumeMounts:<br />        - name: altibase-nfs-dbs<br />          mountPath: /home/altibase/altibase_home/dbs<br />        - name: altibase-nfs-logs<br />          mountPath: /home/altibase/altibase_home/logs<br />        - name: dbobj-config<br />          mountPath: /home/altibase/crt_obj.sql<br />          subPath: crt_obj.sql<br />        ports:<br />        - containerPort: 20300<br />          protocol: TCP<br />        - containerPort: 20301<br />          protocol: TCP<br />        env:<br />        - name: REPLICATION_ENABLE <br />          value: "1"<br />        - name: REPLICATION_PORT_NO<br />          value: "20301"<br />        - name: FILE<br />          value: "crt_obj.sql"<br />      volumes:<br />      - name: altibase-nfs-dbs<br />        nfs:<br />          server: 192.168.204.139<br />          path: /home/altibase-nfs/node1/dbs<br />      - name: altibase-nfs-logs<br />        nfs:<br />          server: 192.168.204.139<br />          path: /home/altibase-nfs/node1/logs<br />      - name: dbobj-config<br />        configMap:<br />          name: dbobj-configmap-node1<br />          defaultMode: 0644<br /><br />---<br /><br />apiVersion: v1<br />kind: Service<br />metadata:<br />  labels:<br />    app: altibase<br />  name: altibase-svc-node1<br />spec:<br />  type: NodePort<br />  ports:<br />  - name: service-port<br />    port: 20300<br />    targetPort: 20300<br />    nodePort: 30001<br />  - name: replication-port<br />    port: 20301<br />    targetPort: 20301<br />  selector:<br />    app: altibase-node1 | apiVersion: v1<br />kind: ConfigMap<br/>metadata:<br />  name: dbobj-configmap-node2<br />data:<br />  crt_obj.sql: \|+<br />    create table t1 (c1 integer primary key, c2 integer);<br />    create replication rep1 with 'altibase-svc-node1',20301 from sys.t1 to sys.t1;<br />    exec sleep(30); # peer server 생성 대기 목적<br />    alter replication rep1 start;<br /><br />---<br /><br />apiVersion: apps/v1<br />kind: Deployment<br />metadata:<br />  name: altibase-deploy-vol-node2<br />spec:<br />  replicas: 1<br />  selector:<br />    matchLabels:<br />      app: altibase-node2<br />  template:<br />    metadata:<br />      labels:<br />        app: altibase-node2<br />    spec:<br />      containers:<br />      - name: altibase<br />        image: altibase/altibase<br />        volumeMounts:<br />        - name: altibase-nfs-dbs<br />          mountPath: /home/altibase/altibase_home/dbs<br />        - name: altibase-nfs-logs<br />          mountPath: /home/altibase/altibase_home/logs<br />        - name: dbobj-config<br />          mountPath: /home/altibase/crt_obj.sql<br />          subPath: crt_obj.sql<br />        ports:<br />        - containerPort: 20300<br />          protocol: TCP<br />        - containerPort: 20301<br />          protocol: TCP<br />        env:<br />        - name: REPLICATION_ENABLE <br />          value: "1"<br />        - name: REPLICATION_PORT_NO<br />          value: "20301"<br />        - name: FILE<br />          value: "crt_obj.sql"<br />      volumes:<br />      - name: altibase-nfs-dbs<br />        nfs:<br />          server: 192.168.204.139<br />          path: /home/altibase-nfs/node2/dbs<br />      - name: altibase-nfs-logs<br />        nfs:<br />          server: 192.168.204.139<br />          path: /home/altibase-nfs/node2/logs<br />      - name: dbobj-config<br />        configMap:<br />          name: dbobj-configmap-node2<br />          defaultMode: 0644<br /><br />---<br /><br />apiVersion: v1<br />kind: Service<br />metadata:<br />  labels:<br />    app: altibase<br />  name: altibase-svc-node2<br />spec:<br />  type: NodePort<br />  ports:<br />  - name: service-port<br />    port: 20300<br />    targetPort: 20300<br />    nodePort: 30002<br />  - name: replication-port<br />    port: 20301<br />    targetPort: 20301<br />  selector:<br />    app: altibase-node2 |

- 위 yaml을 통해 배포된 각 Pod의 Altibase 컨테이너에 접속한 후 아래 절차대로 수행 시 이중화 처리됨을 확인할 수 있다.

  | 수행절차 | Pod 1                                                        | Pod 2                                                        |
  | -------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
  | 1        | iSQL> insert into t1 values (1, 1);<br/>1 row inserted.      |                                                              |
  | 2        | iSQL> select * from t1;<br/>C1     C2<br/>\---------------------------<br/>1      1<br/>1 rows selected. | iSQL> select * from t1;<br/>C1     C2<br/>\---------------------------<br/>1      1<br/>1 rows selected. |
  | 3        |                                                              | iSQL> insert into t1 values (2, 2);<br/>1 row inserted.      |
  | 4        | iSQL> select * from t1;<br/>C1     C2<br/>\---------------------------<br/>1      1<br/>2      2<br/>2 rows selected. | iSQL> select * from t1;<br/>C1     C2<br/>\---------------------------<br/>1      1<br/>2      2<br/>2 rows selected. |

  
