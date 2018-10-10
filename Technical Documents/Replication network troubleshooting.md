이하는 network 문제 의심 상황에서 확인방법들을 기술합니다.

### v$repreceiver의 insert_success_count가 증가하는지 확인
* 특정건 이후로 복제가 안되는 시점에서 standby 쪽의 v$repreceiver의 insert_success_count가 증가하는지 확인. 
* 특정건 이후로 복제가 안되는 시점에서는 이 값이 증가하지 않음.
* 정상적인 상황이라면, replication sync시에도 insert_success_count 값이 증가함.

### pstack을 통해서 양쪽 sender/receiver의 상태 확인
* receiver가 network 대기시의 콜스택 패턴 확인 : recvXlog... select
* sender가 network 대기시의 콜스택 패턴 확인 : sendCmBlock... write - sender socket buffer 64k

### netstat을 통해서 네트워크 상황 확인 
 3.1 sendq 및 recvq 확인 
 3.2 tcp retransmit 상황확인 (netstat 통계 확인 - 네트워크 중간에서 짤리고 있다면 retransmit이 지속적으로 발생할 것으로 예상됨)

4. 재현 테스트 시작부터 재현되는 상황까지 양쪽 서버에서 tcpdump를 떠서 동현님께 분석의뢰
(참고 : 텍스트형식 말고 바이너리 형식으로 떠야함. - ip/port등 정보 확인
- hp ux
nettl -start
nettl -traceon all -e all -f 저장할파일
nettl -stop
 
- aix
tcpdump -i XXX(해당 interface) -vv -w  YYY(저장할 파일명..) 
)


기타 hbt은 소켓을 지속적으로 생성하여 네트워크 확인하는데 불편하므로 테스트 시작전에 꺼 놓도록함. 
( REPLICATION_HBT_DETECT_TIME을 크게 늘려놈, 7200- 2시간 정도?)

추가로 혹시 모르니 라우팅 정보 확인. (netstat -nrv)



보내주신 tcpdump로 확인된 사항 및 간단한 wireshark 사용법 입니다.

1. tcpdump 확인 사항
보내주신 tcpdump 확인시 active쪽에 정상적으로 Sync를 하다가 문제가 발생하는 상황에 대한 tcpdump가 누락되어 있어서 standby쪽 로그만 확인을 하였습니다.

standby쪽 확인 했을 때는 11:31:20에 "TCP Previous segment not captured" 라고 찍혀 있는데 현재 시퀀스 번호가 다음 예상 시퀀스 번호보다 클 때 표시 됩니다.
이것은 패킷이 손실되어 발생하는것이라고 볼 수 있습니다.
그리고 이후에 standby에서 active로 31277078번 ack 의 "TCP Dup ACK"를 계속 보내는데 이것은 Standby에서 active로 31277078번 시퀀스의 패킷을 못받았으니까 다시 보내 달라고 보내는 패킷입니다. 그러나 active에서는 "TCP Dup ACK" 패킷을 받지 못하였는지 다른 패킷만 계속 보내고 있습니다.


정리하면 SYNC 중간에 active에서 보낸 패킷이 하나 누락되었고 standby에서 패킷을 다시 요청하였는데 active에서 보내주지 않아 중단된 상황 입니다.

2. wireshark 사용법 
설치는 아래 사이트에서 다운로드 하여 설치 하면 됩니다.
https://www.wireshark.org/#download
설치후 tcpdump 파일을 오픈하면 패킷정보들이 나오는데
필터 입력 창에 "ip.src == 172.16.19.21 && ip.dst == 172.16.15.168" 와 같이 입력하여 원하는 정보만 필터해서 보면 됩니다.
그리고 패킷중에 검은색을 나오는 부분들이 정상적이지 않은 패킷들이므로 이부분 위주로 확인하면 될것 같습니다.
