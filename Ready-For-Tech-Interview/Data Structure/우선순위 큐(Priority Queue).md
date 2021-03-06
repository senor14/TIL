# 우선순위 큐(Priority Queue)

### **우선순위 큐(Priority Queue)**

일반적인 큐는 먼저 들어간 데이터가 먼저 나오는 구조이다. **이런 큐의 특성과 달리 우선순위 큐(Priority Queue)는 들어간 순서에 상관없이 일정한 규칙에 따라 우선순위를 선정하고 우선순위가 가장 높은 데이터가 가장 먼저 나오게 된다.** 대표적인 예로는 병원의 응급 환자를 생각할 수 있으며, 은행의 업무를 기다리는 상황과 달리 위급한 우선순위에 따라 먼저 처리된다.

### **사용하기**

- 우선순위 큐도 Java에서 내부적으로 구현되어 있어 사용이 용이하다.
- 큐와 동일하게 add(), peek(), poll() 등의 메소드를 사용할 수 있다.

[Code]

```java
public class Sample {
    public static void main(String[] args) {
        PriorityQueue<Integer> pq = new PriorityQueue<>();
        pq.add(4);
        pq.add(19);
        pq.add(2);
        pq.add(1);
        System.out.println(pq.poll()); // 1이 출력된다.
    }
}
```

``

- add() 대신 offer() 메소드를 사용해도 동일한 결과를 얻는다.

### **우선순위 변경하기**

- 우선순위를 정하는 기준은 Java의 정렬 기준과 동일하다.
- Java는 기본적으로 낮은 숫자부터 큰 숫자까지 오름차순으로 정렬하게 되는데, 만약 다른 오름차순으로 정렬하고 싶다면 Comparator 클래스나 Comparable 인터페이스를 이용해야 한다.
- Ex) 객체의 어떤 값에 따라 우선순위를 정해 정렬해야 할때, 오름차순이 아닌 내림차순 정렬을 할때 등등
- Integer는 Collections.reverseOrder()를 사용해 내림차순 정렬을 할 수 있다.

[Code]

```java
public class Sample {
    public static void main(String[] args) {
        PriorityQueue<Integer> pq = new PriorityQueue<>(Collections.reverseOrder());
        pq.add(4);
        pq.add(19);
        pq.add(2);
        pq.add(1);

        System.out.println(pq.poll()); // 19가 출력된다.
    }
}
```

### **우선순위 큐 예제**

- 고양시에서 강남까지 가는 방법이 있다고 하자.
- 대중교통, 자가용, 도보, 자전거 총 4가지의 방법이 존재한다.
  - 대중 교통 : 1시간 10분
  - 자가용 : 45분
  - 도보 : 6시간 40분
  - 자전거 : 2시간 5분
- 시간이 제일 적게 걸리는 순서로 정렬하면 -> 자가용, 대중교통, 자전거, 도보 순이다.
- 우선순위 큐에 저장한 뒤, 데이터를 추출하면 위의 순서대로 추출된다.
- 하지만, 큐는 들어간 순으로 나온다.

[Code]

```java
package programmers;

import java.util.PriorityQueue;

/** * created by victory_woo on 2020/05/12
 */public class Sample {
    public static void main(String[] args) {
        PriorityQueue<Vehicle> pq = new PriorityQueue<>();
        pq.add(new Vehicle("대중교통", 70));
        pq.add(new Vehicle("자가용", 45));
        pq.add(new Vehicle("오토바이", 45));
        pq.add(new Vehicle("도보", 400));
        pq.add(new Vehicle("자전거", 125));

        while (!pq.isEmpty()) {
            System.out.println(pq.poll());
        }
    }

    static class Vehicle implements Comparable<Vehicle> {
        private String name;
        private int time;

        Vehicle(String name, int time) {
            this.name = name;
            this.time = time;
        }

        public String getName() {
            return name;
        }

        public int getTime() {
            return time;
        }

        @Override
        public String toString() {
            return "Vehicle{" +
                    "name='" + name + '\'' +
                    ", time=" + time +
                    '}';
        }

        @Override
        public int compareTo(Vehicle that) {
            if (this.time == that.time) return this.name.compareTo(that.name);
            return this.time - that.time;
        }
    }
}
// 결과
Vehicle{name='오토바이', time=45}
Vehicle{name='자가용', time=45}
Vehicle{name='대중교통', time=70}
Vehicle{name='자전거', time=125}
Vehicle{name='도보', time=400}
```

- Vehicle 클래스를 만들었다. 그리고 자바에서 PriorityQueue를 사용하기 위해서는(객체인 경우) 우선순위 큐에 저장할 객체는 필수적으로 Comparable 인터페이스를 구현해야 한다.
- compareTo 메소드를 오버라이드 하여 우선순위 조건을 설정하면 PriorityQueue가 우선순위가 높은 객체를 추출하게 된다.
- 시간이 작은 순서로 정렬해야 하기 때문에 오름차순 정렬을 한다.
- 다만, 시간이 같은 경우에는 이름의 사전순 정렬을 한다.(오름차순) name이 String이기 때문에 `this.name.compareTo(that.name)` 을 활용한다.
- Int 형인 time 간의 연산에서 Integer.compareTo() 를 사용하지 않은 이유는 Integer와 int의 size가 메모리 차이 때문이다. int의 size가 훨씬 작아 연산시 적은 메모리를 사용한다는 점에서 서로의 값을 뺄셈하여 계산했다.
- 관련 내용은 해당 Repository에 있으니 확인하면 좋을 것 같다.

### **참고**

- [우선순위 큐 - Java에서 다루기](https://siyoon210.tistory.com/117)
- [자바로 정리한 우선순위큐(PriorityQueue)](https://pangsblog.tistory.com/23)
