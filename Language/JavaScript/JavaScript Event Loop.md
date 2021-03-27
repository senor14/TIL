# JavaScript Event Loop

[https://t1.daumcdn.net/cfile/tistory/211AFD3458E493F102](https://t1.daumcdn.net/cfile/tistory/211AFD3458E493F102)

**[JS] Javascript 작동 원리에 대해서, Event Loop**

Javscript를 공부하다 보면 이런 말을 종종 듣는다.

> 싱글스레드 기반으로 동작하는 자바스크립트이벤트 루프를 기반으로 하는 싱글 스레드 Node.js

이런 말은 많이 들었지만 구체적으로 내부 원리에 대해 간단하게라도 설명하는 글은 보기 힘들다. (초심자 입장에서는 쉬운 내용이 결코 아니라고 생각한다.) 이번 포스팅에서는 "정말 **싱글 스레드인가?"**, "싱글 스레드의 정체는 무엇이며, 어떻게 싱글 스레드인가?" "**이벤트 루프**는 또 무엇인가?" 등등에 대해 정말 간단히 알아보기 위해 자바스크립트가 동작하는 **환경(Environment)**과 자바스크립트를 해석하고 실행시키는 **엔진**에 대해서 알아본다.

> Javascript Engine ?

일단 한 가지 짚고 넘어가야 할 것이 있다. JavaScript를 해석하는 **JavaScript Engine**과 웹 브라우저에 화면을 그리는 **Rendering Engine**은 다른 것이다. Rendering Engine(또는 Layout Engine)은 HTML과 CSS로 작성된 마크업 관련한 코드들을 콘텐츠로서 웹 페이지에 **`rendering`**하는 역할을 한다. Javascript Engine이란 JavaScript로 작성한 코드를 해석하고 실행하는 **인터프리터**다. 주로 웹 브라우저에서 이용되지만 최근에는 node.js라는 녀석이 등장하면서 server side에선 V8과 같은 Engine이 이용된다.

구글에서 개발한 V8을 비롯해 대부분의 자바스크립트 엔진은 크게 다음의 세 영역으로 나뉜다. (이어지는 설명은 V8 engine을 중심으로 이뤄졌다.)

> Call Stack,    Task Queue(Event queue),    Heap

그리고 추가적으로 **`Event loop`**라는 녀석이 존재하여 Task queue에 들어가는 task들을 관리하게 된다.

[https://t1.daumcdn.net/cfile/tistory/225AF03B58E4956C26](https://t1.daumcdn.net/cfile/tistory/225AF03B58E4956C26)

**Call Stack**

자바스크립트는 **단 하나의 호출 스택(**call stack)을 사용한다. 이러한 특징 때문에 자바스크립트의 함수가 실행되는 방식을 “Run to Completion” 라고 한다. 이는 하나의 함수가 실행되면 이 함수의 실행이 끝날 때까지 다른 어떤 task도 수행될 수 없다는 의미이다. 요청이 들어올 때마다 해당 요청을 **순차적**으로 호출 스택에 담아 처리한다. 메소드가 실행될 때, Call Stack에 새로운 프레임이 생기고 **push**되고 메소드의 실행이 끝나면 해당 프레임은 **pop**되는 원리이다.

```jsx
**function** foo(b) {
	**var** a = 10;
	**return** a + b;
}

**function** bar(x) {
	**var** y = 2;
	**return** foo(x + y);
}

console.log(bar(1));
```

위 코드를 살펴보자.

`bar`라는 함수를 호출했으니 `bar`에 해당하는 **스택 프레임이 형성**되고 그 안에는 `y`와 같은 **local variable**과 **arguments**가 함께 생성된다. 그리고 `bar` 함수는 `foo`함수를 호출하고 있다. 아직 `bar` 함수는 종료되지 않았으니 pop되지 않고 호출된 `foo` 함수가 Call Stack에 push 된다.(`bar` 함수 호출 과정과 동일한 과정을 거친다.)

`foo` 함수에서는 `a + b`라는 값을 return 하면서 함수의 역할을 모두 마쳤으므로 stack에서 pop된다. 다시 `bar` 함수로 돌아와서 `foo` 함수로부터 받은 값을 return하면서 `bar` 함수도 종료되고 stack에서 pop된다.

[https://t1.daumcdn.net/cfile/tistory/2768724E58E497A90D](https://t1.daumcdn.net/cfile/tistory/2768724E58E497A90D)

간단하게 11 line의 javascript code로 실행되는 과정을 살펴봤다. Stack이라는 자료구조의 특성을 사용하여 task들을 수행하는 원리인 것이다.

**Heap**

동적으로 생성된 객체(인스턴스)는 힙(heap)에 할당된다. 대부분 구조화되지 않는 ‘더미’같은 메모리 영역을 `heap`이라 표현한다.

**Task Queue(Event Queue)**

자바스크립트의 런타임 환경(JavaScript Runtime Environment)에서는 처리해야 하는 Task들을 임시 저장하는 대기 큐가 존재한다. 그 대기 큐를 Task Queue or Event Queue라고 한다. 그리고 Call Stack이 **비어졌을 때** 먼저 대기열에 들어온 순서대로 수행된다.

```jsx
setTimeout(**function**() {
	console.log("first");
}, 0);
console.log("second");
```

이 코드는 어떤 순서로 동작하게 될까? `setTimeout`에 `**0ms**`를 주었으니 delay되지 않고 바로 실행될 것 같다. 그러나 console 창은 그렇지 않다.

```jsx
// console>>
// second
// first
```

자바스크립트에서 비동기로 호출되는 함수들은 Call Stack에 쌓이지 않고 **Task Queue**에 **enqueue**된다. 자바스크립트에서는 이벤트에 의해 실행되는 함수(핸들러)들이 비동기로 실행된다. 자바스크립트 엔진이 아닌 **Web API 영역**에 따로 정의되어 있는 함수들은 비동기로 실행된다. 다음 코드를 통해 확실하게 이해하고 넘어가자.

```jsx
**function** test1() {
	console.log("test1");
	test2();
}

**function** test2() {
	**let** timer = setTimeout(**function**() {
		console.log("test2");
	}, 0);
	test3();
}

**function** test3() {
	console.log("test3");
}

test1(); // ?
```

이제 test1()을 호출했을 때 어떠한 순서로 console에 찍힐지 예측할 수 있어야 한다.

일단 **"test1"**이 console에 찍히겠다. 그리고 test2( )가 호출되면서 `setTimeout` 함수가 실행되고 콜스택에 들어간 다음, 바로 빠져나온다. 그리고 내부에 걸려있던 **핸들러(익명함수)**는 **콜스택에 들어가서 바로 실행되지 않는다.** 이 부분이 중요하다. 이 핸들러는 call stack 영역이 아닌 **event queue 영역**으로 들어간다. 그리고 test3 함수가 콜스택으로 들어간다.

test( )이 실행되면서 **"test3"**이 console에 찍히고, 작업을 모두 마친 test3 함수가 Call stack에서 **pop**된다. 이어서 test2 함수와 test 1 함수까지 Call stack에서 **pop**된다. 이 때 이벤트 루프의 콜스택이 **비어있게 된다.** 바로 이 시점에 queue의 **head**에서 하나의 event를 가져와서 Call Stack으로 넣는다. 이 이벤트는 setTimeout 함수 내부에 있던 익명함수이다. 이제서야 이 함수가 실행된다.

즉, test3가 끝나고, (Call Stack에서 pop되고) test2가 끝나고, test1이 마저 끝나고 나서 이벤트 루프에 의해 하나의 event가 dequeue된 다음 콜스택으로 들어가서 실행된다. **그러므로 이벤트에 걸려있는 핸들러는 절대 먼저 실행될 수 없다!!**

```jsx
// console
// test1
// test3
// test2
```

이런 의문이 들 수 있지 않을까?

Q. Event Loop는 백그라운드 스레드가 존재해서 Call Stack을 polling하면서 비어있는지 확인하는 건가?

Q. Event queue에도 event가 있는지 확인해야 할 것 같은데 이 때도 polling으로 검사하는 것인가?

Q. Event Loop에 의해서 Event queue에 있던 하나의 이벤트가 Call stack에 들어간 다음에는 그 이벤트가 끝나기 전까지 이벤트 루프는 이벤트 큐에서 이벤트를 dequeue하지 않나?

Q. Call stack에서 이벤트가 진행 중일 때도 Event Loop는 어떻게 확인을 하나?

MDN의 이벤트 루프 설명을 보면 아주 간단한 **가상의 코드**로 이 세 가지 질문에 대한 답을 해주고 있다.

```jsx
**while** (queue.waitForMessage()) {
	queue.processNextMessage();
}
```

이런 식으로 이벤트 루프는 현재 실행 중인 태스크가 없는지와 태스크 큐에 태스크가 있는지를 반복적으로 확인한다.

queue에 메시지, 즉 처리해야할 이벤트(또는 태스크)가 존재하면 while-loop안으로 들어가서 해당하는 이벤트를 처리하거나 작업을 수행한다. 그리고는 다시 queue로 돌아와 새로운 이벤트가 존재하는지 파악하는 것이다. 눈치챘겠지만 Event Queue에서 대기하고 있는 Event들은 한 번에 하나씩 Call Stack으로 호출되어 처리된다.

이벤트 루프에 대한 대략적인 설명은 여기까지이다. 보다 자세한 설명을 읽어보고 싶다면 아래 reference를 확인할 수 있다.

Reference

[https://developer.mozilla.org/en/docs/Web/JavaScript/EventLoop](https://developer.mozilla.org/en/docs/Web/JavaScript/EventLoop)

[https://github.com/nhnent/fe.javascript/wiki/June-13-June-17,-2016](https://github.com/nhnent/fe.javascript/wiki/June-13-June-17,-2016)

[http://www.nextree.co.kr/p7292/](http://www.nextree.co.kr/p7292/)
