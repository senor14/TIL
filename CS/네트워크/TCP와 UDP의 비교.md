# TCP와 UDP의 비교

## **TCP와 UDP의 비교**

### **UDP**

`UDP(User Datagram Protocol, 사용자 데이터그램 프로토콜)`는 **비연결형 프로토콜** 이다. IP 데이터그램을 캡슐화하여 보내는 방법과 연결 설정을 하지 않고 보내는 방법을 제공한다. `UDP`는 흐름제어, 오류제어 또는 손상된 세그먼트의 수신에 대한 재전송을 **하지 않는다.** 이 모두가 사용자 프로세스의 몫이다. `UDP`가 행하는 것은 포트들을 사용하여 IP 프로토콜에 인터페이스를 제공하는 것이다.

종종 클라이언트는 서버로 짧은 요청을 보내고, 짧은 응답을 기대한다. 만약 요청 또는 응답이 손실된다면, 클라이언트는 time out 되고 다시 시도할 수 있으면 된다. 코드가 간단할 뿐만 아니라 TCP 처럼 초기설정(initial setup)에서 요구되는 프로토콜보다 적은 메시지가 요구된다.

`UDP`를 사용한 것들에는 `DNS`가 있다. 어떤 호스트 네임의 IP 주소를 찾을 필요가 있는 프로그램은, DNS 서버로 호스트 네임을 포함한 UDP 패킷을 보낸다. 이 서버는 호스트의 IP 주소를 포함한 UDP 패킷으로 응답한다. 사전에 설정이 필요하지 않으며 그 후에 해제가 필요하지 않다.



### **Reference**

- [http://d2.naver.com/helloworld/47667](http://d2.naver.com/helloworld/47667)
- [http://asfirstalways.tistory.com/327](http://asfirstalways.tistory.com/327)
