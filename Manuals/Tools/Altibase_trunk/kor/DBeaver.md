DBeaver
======================

#### Trunk

Altibase® Administration

<br><br><br><br><br><br><!-- PDF 변환을 위한 여백입니다. --> 







































<!-- PDF 변환을 위한 여백입니다. --> 

<div align="left">
    <img src="media/common/e5cfb3761673686d093a3b00c062fe7a.png">
</div>

<br><br><!-- PDF 변환을 위한 여백입니다. --> 









































<!-- PDF 변환을 위한 여백입니다. --> 

<pre>
Altibase Administration Administrator's Manual
Trunk
Copyright ⓒ 2001~2023 Altibase Corp. All Rights Reserved.<br>
본 문서의 저작권은 ㈜알티베이스에 있습니다. 이 문서에 대하여 당사의 동의없이 무단으로 복제 또는 전용할 수 없습니다.<br>
<b>㈜알티베이스</b>
08378 서울시 구로구 디지털로 306 대륭포스트타워Ⅱ 10층
전화 : 02-2082-1114
팩스 : 02-2082-1099
고객서비스포털 : <a href='http://support.altibase.com'>http://support.altibase.com</a>
홈페이지      : <a href='http://www.altibase.com/'>http://www.altibase.com</a></pre>





<br>

# 목차

- [Altibase 데이터베이스 연결](#Altibase-데이터베이스-연결)



# Altibase 데이터베이스 연결





- DBeaver에서 Altibase 데이터베이스에 연결하는 방법에 대해서 설명한다.

### 



### 연결 퀵 가이드

다음은 DBeaver 23.1.5를 기준으로 Altibase 데이터베이스를 연결하는 방법을 간단히 정리한 것이다.

| 메뉴                                                         | UI                                |
| ------------------------------------------------------------ | --------------------------------- |
| [ 데이터베이스 ] → [ 새 데이터베이스 연결 ]                  | ![menu1](media\DBeaver\menu1.png) |
| All 또는 SQL에서 Altibase를 선택 후 [ Next > ] 버튼을 클릭한다. | ![menu2](media\DBeaver\menu2.png) |
| Host, Port, Schema, Username, Password 칸에 연결하고자 하는 데이터베이스 값을 입력한다.<br /><br />[ Connection details (name, type, ... ) ] 을 클릭하여 연결 정보를 변경할 수 있다.<br /><br />[ Driver Settings ] 을 클릭하여 Altibase Driver의 설정 값을 변경할 수 있다. | ![menu3](media\DBeaver\menu3.png) |
| [ Driver Settings ] 을 선택한 화면이다.<br />Libraries 탭의 [ Add File ] 로 사용할 Altibase JDBC 파일을 추가할 수 있다.<br />하단의 Driver class에서 Altibase JDBC 클래스가 목록에 나타난다. | ![menu4](media\DBeaver\menu4.png) |
| [ Connection details (name, type, ... ) ] 을 선택한 화면이다.<br />Connection name 칸을 수정하여 연결 이름을 변경하거나 연결 유형을 설정할 수 있다.<br /><br />모든 설정이 끝났다면 [ Finish ] 버튼을 눌러 접속 정보 등록을 완료한다. | ![menu5](media\DBeaver\menu5.png) |
| Database Navigator 탭에서 등록한 데이터베이스 접속 정보 등록 목록을 확인할 수 있다.<br />등록한 접속 정보를 더블 클릭하면 접속을 연결할 수 있다. 연결된 접속은 아이콘에 초록색 체크 표시가 나타난다. | ![menu6](media\DBeaver\menu6.png) |

