이하는 replication 관련하여 network 문제 의심 상황에서 확인방법들을 기술합니다.

### v$repreceiver의 insert_success_count가 증가하는지 확인
* 특정건 이후로 복제가 안되는 시점에서 standby 쪽의 v$repreceiver의 insert_success_count가 증가하는지 확인. 
* 특정건 이후로 복제가 안되는 시점에서는 이 값이 증가하지 않음.
* 정상적인 상황이라면, replication sync시에도 insert_success_count 값이 증가함.

### pstack을 통해서 양쪽 sender/receiver의 상태 확인
* receiver가 network 대기시의 콜스택 패턴 확인 : recvXlog... select
* sender가 network 대기시의 콜스택 패턴 확인 : sendCmBlock... write - sender socket buffer 64k

### netstat을 통해서 네트워크 상황 확인 
* sendq 및 recvq 확인 
* tcp retransmit 확인 : 네트워크 중간에서 짤리고 있다면 retransmit이 지속적으로 발생함.
* 라우팅 정보 확인 : `netstat -nrv` 게이트웨이, 서브넷마스크, 인터페이스명 등을 확인할수 있음.

### tcpdump
* sender쪽과 receiver쪽 양쪽 장비에서 모두 tcpdump를 떠야함.
* 텍스트형식 말고 바이너리 형식으로 떠야함. - ip/port등 정보 확인
* tcpdump로 생성된 바이너리 화일은 wireshark로 확인함.
* HBT는 소켓을 지속적으로 생성하여 네트워크 확인하는데 불편하므로 테스트 시작전에 꺼 놓도록함.(REPLICATION_HBT_DETECT_TIME을 7200(2시간)으로 충분히 늘려 놓는다.)
```
# HP-UX
nettl -start
nettl -traceon all -e all -f 저장할파일
nettl -stop

# AIX
tcpdump -i XXX(해당 interface) -vv -w  YYY(저장할 파일명..) 
```

### wireshark
* 설치 : https://www.wireshark.org/#download
* 설치후 tcpdump 파일을 오픈하면 패킷정보들이 나옴.
* 필터 입력 창에 "ip.src == 172.16.19.21 && ip.dst == 172.16.15.168" 와 같이 입력하여 원하는 정보만 필터해서 볼수 있음.
* 패킷중에 검은색을 나오는 부분들이 정상적이지 않은 패킷들이므로 이부분 위주로 확인하면 됩니다.

### wireshark 사용한 tcpdump 생성화일 확인 예제
* 아래 그림은 replication sync에서 문제가 된 상황에서의 standby(recievier)쪽 tcpdump 화일을 확인한 예제임.
* 11:31:20에 "TCP Previous segment not captured" 라고 찍혀 있는데 현재 시퀀스 번호가 다음 예상 시퀀스 번호보다 클 때 표시 됩니다. 이것은 패킷이 손실되어 발생하는것이라고 볼 수 있습니다.
* standby에서 active로 31277078번 ack 의 "TCP Dup ACK"를 계속 보내는데 이것은 Standby에서 active로 31277078번 시퀀스의 패킷을 못받았으니까 다시 보내 달라고 보내는 패킷입니다. 그러나 active에서는 "TCP Dup ACK" 패킷을 받지 못하였는지 다른 패킷만 계속 보내고 있습니다.
* 정리하면 replication sync 중간에 active에서 보낸 패킷이 하나 누락되었고 standby에서 패킷을 다시 요청하였는데 active에서 보내주지 않아 중단된 상황 입니다.

