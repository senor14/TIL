# Document Object Model

## **Document Object Model**

웹에서는 수많은 이벤트(Event)가 발생하고 흐른다.

- 브라우저(user agent)로부터 발생하는 이벤트
- 사용자의 행동(interaction)에 의해 발생하는 이벤트
- DOM의 ‘변화’로 인해 발생하는 이벤트

발생하는 이벤트는 그저 자바스크립트 객체일 뿐이다. 브라우저의 Event interface에 맞춰 구현된 객체인 것이다.

여러 DOM Element로 구성된 하나의 웹 페이지는 Window를 최상위로 하는 트리를 생성하게 된다. 결론부터 말하자면 이벤트는 이벤트 각각이 갖게 되는 전파 경로(propagation path)를 따라 전파된다. 그리고 이 전파 경로는 DOM Tree 구조에서 Element의 위상(hierarchy)에 의해 결정이 된다.

### **Reference**

- [스펙 살펴보기: Document Object Model Event](https://jbee.io/web/about-event-in-the-web/)
