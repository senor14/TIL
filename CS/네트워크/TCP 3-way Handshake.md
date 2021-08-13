# TCP 3-way Handshake

**[TCP] 3-way-handshake & 4-way-handshake**

**연결 성립(Connection Establishment)**

[https://t1.daumcdn.net/cfile/tistory/2352F94A58D7287932](https://t1.daumcdn.net/cfile/tistory/2352F94A58D7287932)

1. 클라이언트는 서버에 접속을 요청하는 **SYN(a)** 패킷을 보낸다.2) 서버는 클라이언트의 요청인 **SYN(a)**을 받고 클라이언트에게 요청을 수락한다는 **ACK(a+1)**와 **SYN(b)**이 설정된 패킷을 발송한다.3) 클라이언트는 서버의 수락 응답인 **ACK(a+1)**와 **SYN(b)** 패킷을 받고 **ACK(b+1)**를 서버로 보내면 연결이 **성립(establish)**된다.

**연결 해제(Connection Termination)**

[https://t1.daumcdn.net/cfile/tistory/2336285058D7288E33](https://t1.daumcdn.net/cfile/tistory/2336285058D7288E33)

1. 클라이언트가 연결을 종료하겠다는 **FIN플래그**를 전송한다.

2. 서버는 클라이언트의 요청**(FIN)**을 받고 알겠다는 확인 메세지로 **ACK**를 보낸다.

2-1) 그리고나서는 데이터를 모두 보낼 때까지 잠깐 **TIME_OUT**이 된다.

3. 데이터를 모두 보내고 통신이 끝났으면 연결이 종료되었다고 클라이언트에게 **FIN 플래그**를 전송한다.

4. 클라이언트는 **FIN 메세지**를 확인했다는 **메세지(ACK)**를 보낸다.

5. 클라이언트의 **ACK 메세지**를 받은 서버는 소켓 **연결을 close**한다.

6. 클라이언트는 아직 서버로부터 받지 못한 데이터가 있을 것을 대비해 일정 시간 동안 세션을 남겨놓고 잉여 패킷을 기다리는 과정을 거친다.**(TIME_WAIT)**

**What is the SYN Packet? ACK packet?**

일단 두 용어는 다음의 약자이다.

> SYN :: synchronize sequence numberACK :: acknowledgement

**TCP Header**에는 **Code Bit(Flag bit)**라는 부분이 존재한다. 이 부분은 총 **6Bit**로 이루어져 있이며 각각 한 bit들이 의미를 갖고 있다. **Urg-Ack-Psh-Rst-Syn-Fin** 순서로 되어 있으며 해당 위치의 비트가 1이면 해당 패킷이 어떠한 내용을 담고 있는 패킷인지를 나타낸다. SYN 패킷일 경우엔 000010이 되고 ACK 패킷일 경우에는 010000이 되는 것이다.

**Why two types of packets?**

일단 연결을 성립하려면 서로 통신이 가능한지를 먼저 파악하기 위해 패킷을 먼저 주고받아야 한다는 것까지는 이해가 쉽다. 그런데 두 종류의 패킷을 주고 받는다. **요청**과 **응답**에 대한 패킷을 주고 받아야 하기 때문에 두 종류인 것이다.

