# TCP와 UDP의 비교

## **TCP와 UDP의 비교**



### **TCP**

대부분의 인터넷 응용 분야들은 **신뢰성** 과 **순차적인 전달** 을 필요로 한다. UDP 로는 이를 만족시킬 수 없으므로 다른 프로토콜이 필요하여 탄생한 것이 `TCP`이다. `TCP(Transmission Control Protocol, 전송제어 프로토콜)`는 신뢰성이 없는 인터넷을 통해 종단간에 신뢰성 있는 **바이트 스트림을 전송** 하도록 특별히 설계되었다. TCP 서비스는 송신자와 수신자 모두가 소켓이라고 부르는 종단점을 생성함으로써 이루어진다. TCP 에서 연결 설정(connection establishment)는 `3-way handshake`를 통해 행해진다.

모든 TCP 연결은 전이중(full-duplex), 점대점(point to point)방식이다. 전이중이란 전송이 양방향으로 동시에 일어날 수 있음을 의미하며 점대점이란 각 연결이 정확히 2 개의 종단점을 가지고 있음을 의미한다. TCP 는 멀티캐스팅이나 브로드캐스팅을 지원하지 않는다.

### **Reference**

- [http://d2.naver.com/helloworld/47667](http://d2.naver.com/helloworld/47667)
- [http://asfirstalways.tistory.com/327](http://asfirstalways.tistory.com/327)
