# final keyword

## **final keyword**

- final class다른 클래스에서 상속하지 못한다.
- final method다른 메소드에서 오버라이딩하지 못한다.
- final variable변하지 않는 상수값이 되어 새로 할당할 수 없는 변수가 된다.

추가적으로 혼동할 수 있는 두 가지를 추가해봤다.

- finally`try-catch` or `try-catch-resource` 구문을 사용할 때, 정상적으로 작업을 한 경우와 에러가 발생했을 경우를 포함하여 마무리 해줘야하는 작업이 존재하는 경우에 해당하는 코드를 작성해주는 코드 블록이다.
- finalize()keyword 도 아니고 code block 도 아닌 메소드이다. `GC`에 의해 호출되는 함수로 절대 호출해서는 안 되는 함수이다. `Object` 클래스에 정의되어 있으며 GC 가 발생하는 시점이 불분명하기 때문에 해당 메소드가 실행된다는 보장이 없다. 또한 `finalize()` 메소드가 오버라이딩 되어 있으면 GC 가 이루어질 때 바로 Garbage Collecting 되지 않는다. GC 가 지연되면서 OOME(Out of Memory Exception)이 발생할 수 있다.
