# Statement vs PreparedStatement

## **Statement vs PreparedStatement**

우선 속도 면에서 `PreparedStatement`가 빠르다고 알려져 있다. 이유는 쿼리를 수행하기 전에 이미 쿼리가 컴파일 되어 있으며, 반복 수행의 경우 프리 컴파일된 쿼리를 통해 수행이 이루어지기 때문이다.

`Statement`에는 보통 변수를 설정하고 바인딩하는 `static sql`이 사용되고 `Prepared Statement`에서는 쿼리 자체에 조건이 들어가는 `dynamic sql`이 사용된다. `PreparedStatement`가 파싱 타임을 줄여주는 것은 분명하지만 `dynamic sql`을 사용하는데 따르는 퍼포먼스 저하를 고려하지 않을 수 없다.

하지만 성능을 고려할 때 시간 부분에서 가장 큰 비중을 차지하는 것은 테이블에서 레코드(row)를 가져오는 과정이고 SQL 문을 파싱하는 시간은 이 시간의 10 분의 1 에 불과하다. 그렇기 때문에 `SQL Injection` 등의 문제를 보완해주는 `PreparedStatement`를 사용하는 것이 옳다.

### **참고 자료**

- [http://java.ihoney.pe.kr/76](http://java.ihoney.pe.kr/76)
