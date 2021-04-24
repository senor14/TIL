# LRU Cache(Least Recently Used)

## **LRU Cache(Least Recently Used)**

### **Cache 개념**

캐시는 데이터나 값을 미리 복사해 놓는 임시 장소를 가리킨다. 캐시는 접근 시간에 비해 원래 데이터를 접근하는 시간이 오래 걸리는 경우나 값을 다시 계산하는 시간을 절약하는 경우 사용한다. 캐시에 데이터를 미리 복사해 놓으면 계산이나 접근 시간 없이 빠른 속도로 데이터에 접근할 수 있다. (캐시가 사용하는 리소스의 양도 제한이 있다.)

### **LRU Cache 개념**

LRU는 Least Recently Used의 약자로 OS의 페이지 교체 알고리즘의 하나로 최근에 가장 오랫동안 사용하지 않은 페이지를 교체하는 알고리즘이다. 캐시에 공간이 부족하면 가장 최근에 사용하지 않은 항목을 제거한다.

### **LRU Cache 구현**

[https://camo.githubusercontent.com/89d2d64edc65f6eff4d41bca129a864dabea20915db6dfb1f19d5ba9162f4795/68747470733a2f2f6b2e6b616b616f63646e2e6e65742f646e2f6257377038492f6274717635686a6d4235452f58336c774d4e5150384e70324a746c326b516731454b2f696d672e706e67](https://camo.githubusercontent.com/89d2d64edc65f6eff4d41bca129a864dabea20915db6dfb1f19d5ba9162f4795/68747470733a2f2f6b2e6b616b616f63646e2e6e65742f646e2f6257377038492f6274717635686a6d4235452f58336c774d4e5150384e70324a746c326b516731454b2f696d672e706e67)

LRU Cache 구현은 Doubly Linked List를 통해 구현한다. head에 가까운 데이터일수록 최근에 사용한 데이터이고, tail에 가까울수록 가장 오랫동안 사용하지 않은 데이터로 간주하여 새로운 데이터를 삽입할 때, 가장 먼저 삭제되도록 한다.

삽입된 데이터를 사용하면 head로 옮겨 우선순위를 높이게 되고, 삭제될 우선순위에서 멀어지게 된다.
