

# [정보처리기사 156] - TCP/IP ★



# **# TCP/IC**

**※ 개요**

· Transmission Control Protocol / Internet Protocol

· 서로 다른 기종의 컴퓨터들이 데이터를 주고받을 수 있도록 하는 표준 프로토콜



**※ TCP**

· OSI 7계층의 전송 계층에 해당

· 신뢰성 있는 연결형 서비스 제공

· 패킷의 다중화, 순서 제어, 오류 제어, 흐름 제어 기능 제공

· Stream 전송 기능 제공

· Header에 Source/Destination Port /Number, Sequence Number, cknowledgement Number, Checksum 등을 포함



**※ IP**

· OSI 7계층의 네트워크 계층에 해당

· 데이터그램을 기반으로 비연결형 서비스 제공

· 패킷의 분해/조립, 주소 지정, 경로 선택 기능 제공

· Header에 Version, Header Length(20~60Bytes), Total Packet Length, Checksum, Source/Desination IP Address 등을 포함



**※ 구조**

| **OSI**           | **TCP/IP**      | **기능**                                                     |
| ----------------- | --------------- | ------------------------------------------------------------ |
| 응용, 표현, 세션  | 응용            | 응용 프로그램 간의 데이터 송수신 제공TELNET, FTP, SMTP, SNMP, DNS, HTTP 등 |
| 전송              | 전송            | 호스트들 간의 신뢰성 있는 통신 제공TCP, UDP                  |
| 네트워크          | 인터넷          | 데이터 전송을 위한 주소 지정, 경로 설정IP, ICMP, IGMP, ARP, RARP |
| 데이터 링크, 물리 | 네트워크 액세스 | 실제 데이터를 송수신 하는 역할Ethernet, IEEE802, HDLC, X.25, RS-232C, ARQ |



# **# 계층 별 주요 프로토콜**

**※ 응용 계층**

· FTP : File Transfer Protocol, 컴퓨터와 컴퓨터 또는 컴퓨터와 인터넷 사이에서 파일을 주고받을 수 있도록 하는 원격 파일 전송 프로토콜

· SMTP : Simple Mail Transfer Protocol, 전자 우편 교환 서비스

· TELNET : 멀리 잇는 컴퓨터에 접속하여 자신의 컴퓨터처럼 사용할 수 있는 서비스, 프로그램 실행 등 시스템 관리 작업을 할 수 있는 가상의 터미널 기능 수행

· SNMP : Simple Network Management Protocol, TIP/IP 네트워크 관리 프로토콜, 라우터나 허브 등 네트워크 기기의 네트워크 정보를 네트워크 관리 시스템에 보내는 데 사용하는 표준 통신 규약

· DNS : Domain Name System, 도메인 네임을 IP 주소로 매핑하는 시스템

· HTTP : HyperText Transfer Protocol, WWW에서 HTML 문서를 송수신 하기 위한 프로토콜



**※ 전송 계층**

· TCP : Transmission Control Protocol, 양방향 연결형 서비스 제공, 패킷 단위의 전달로 신뢰성 있는 경로를 확립하고 메시지 전송을 감독, 순서&오류&흐름 제어 기능

· UDP : User Datagram Protocol, 데이터 전송 전에 연결을 설정하지 않는 비연결형 서비스 제공, TCP에 비해 상대적으로 단순한 헤더 구조를 가져 오버헤드가 적음, 실시간 전송에 유리하며, 신뢰성보다는 속도가 중요시 되는 네트워크에서 사용

· RTCP :  Real-Time Control Protocl, 패킷의 전송 품질을 제어하기 위한 제어 프로토콜



**※ 인터넷 계층**

· IP : Internet Protocol, 전송할 데이터에 주소를 지정하고 경로를 설정하는 기능

· ICMP :  Internet Control Message Protocol, IP와 조합하여 통신 중 발생하는 오류 처리와 전송 경로 변경을 위한 제어 메시지를 관리하는 역할

· IGMP : Internet Group Management Protocol, 멀티 캐스트를 지원하는 호스트나 라우터 사이에서 멀티캐스트 그룹 유지를 위해 사용

· ARP : Address Resolution Protocol, 호스트의 IP 주소를 호스트와 연결된 네트워크 접속 장치의 MAC Address로 변환

· RARP : Reverse Address Resolution Protocol, ARP와 반대로 물리적 주소를 IP 주소로 변환 하는 기능



**※ 네트워크 액세스 계층**

· IEEE 802.3(Ethernet) : CSMA/CD 방식의 LAN

· IEEE 802 : LAN을 위한 표준 프로토콜

· HDLC : 비트 위주의 데이터 링크 제어 프로토콜

· X.25 : 패킷 교환 망을 통한 DTE와 DCE 간의 인터페이스를 제공하는 프로토콜

· RS-232C : 공중 전화 교환망을 통한 DTE와 DCE 간의 인터페이스를 제공하는 프로토콜