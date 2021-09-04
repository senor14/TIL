# Sorting Algorithm

## **Sorting Algorithm**

Sorting 알고리즘은 크게 Comparisons 방식과 Non-Comparisons 방식으로 나눌 수 있다.

### **Comparisons Sorting Algorithm (비교 방식 알고리즘)**

`Bubble Sort`, `Selection Sort`, `Insertion Sort`, `Merge Sort`, `Heap Sort`, `Quick Sort` 를 소개한다.

### **Bubble Sort**

n 개의 원소를 가진 배열을 정렬할 때, In-place sort 로 인접한 두 개의 데이터를 비교해가면서 정렬을 진행하는 방식이다. 가장 큰 값을 배열의 맨 끝에다 이동시키면서 정렬하고자 하는 원소의 개수 만큼을 두 번 반복하게 된다.

[제목 없음](https://www.notion.so/576f3f6ab21a472db82b9390f471f58a)

### **[code](https://github.com/JaeYeopHan/algorithm_basic_java/blob/master/src/test/java/sort/BubbleSort.java)**

### **Selection Sort**

n 개의 원소를 가진 배열을 정렬할 때, 계속해서 바꾸는 것이 아니라 비교하고 있는 값의 index 를 저장해둔다. 그리고 최종적으로 한 번만 바꿔준다. 하지만 여러 번 비교를 하는 것은 마찬가지이다.

[제목 없음](https://www.notion.so/eca80363e6624003bad5b501c32232be)

### **[code](https://github.com/JaeYeopHan/algorithm_basic_java/blob/master/src/test/java/sort/SelectionSort.java)**

### **Insertion Sort**

n 개의 원소를 가진 배열을 정렬할 때, i 번째를 정렬할 순서라고 가정하면, 0 부터 i-1 까지의 원소들은 정렬되어있다는 가정하에, i 번째 원소와 i-1 번째 원소부터 0 번째 원소까지 비교하면서 i 번째 원소가 비교하는 원소보다 클 경우 서로의 위치를 바꾸고, 작을 경우 위치를 바꾸지 않고 다음 순서의 원소와 비교하면서 정렬해준다. 이 과정을 정렬하려는 배열의 마지막 원소까지 반복해준다.

[제목 없음](https://www.notion.so/feb3143165dc49e1a090d5813af7d07f)

### **[code](https://github.com/JaeYeopHan/algorithm_basic_java/blob/master/src/test/java/sort/InsertionSort.java)**

### **Merge Sort**

기본적인 개념으로는 n 개의 원소를 가진 배열을 정렬할 때, 정렬하고자 하는 배열의 크기를 작은 단위로 나누어 정렬하고자 하는 배열의 크기를 줄이는 원리를 사용한다. `Divide and conquer`라는, "분할하여 정복한다"의 원리인 것이다. 말 그대로 복잡한 문제를 복잡하지 않은 문제로 분할하여 정복하는 방법이다. 단 분할(divide)해서 정복했으니 정복(conquer)한 후에는 **결합(combine)** 의 과정을 거쳐야 한다.

`Merge Sort`는 더이상 나누어지지 않을 때 까지 **반 씩(1/2)** 분할하다가 더 이상 나누어지지 않은 경우(원소가 하나인 배열일 때)에는 자기 자신, 즉 원소 하나를 반환한다. 원소가 하나인 경우에는 정렬할 필요가 없기 때문이다. 이 때 반환한 값끼리 **`combine`될 때, 비교가 이뤄지며,** 비교 결과를 기반으로 정렬되어 **임시 배열에 저장된다.** 그리고 이 임시 배열에 저장된 순서를 합쳐진 값으로 반환한다. 실제 정렬은 나눈 것을 병합하는 과정에서 이뤄지는 것이다.

결국 하나씩 남을 때까지 분할하는 것이면, 바로 하나씩 분할해버리면 되지 않을까? 재귀적으로 정렬하는 원리인 것이다. 재귀적 구현을 위하 1/2 씩 분할한다.

[제목 없음](https://www.notion.so/3d05784cd25445c5b79b5034469b4466)

### **Heap Sort**

`binary heap` 자료구조를 활용할 Sorting 방법에는 두 가지 방법이 존재한다. 하나는 정렬의 대상인 데이터들을 힙에 넣었다가 꺼내는 원리로 Sorting 을 하게 되는 방법이고, 나머지 하나는 기존의 배열을 `heapify`(heap 으로 만들어주는 과정)을 거쳐 꺼내는 원리로 정렬하는 방법이다. `heap`에 데이터를 저장하는 시간 복잡도는 `O(log n)`이고, 삭제 시간 복잡도 또한 `O(log n)`이 된다. 때문에 힙 자료구조를 사용하여 Sorting 을 하는데 time complexity 는 `O(log n)`이 된다. 이 정렬을 하려는 대상이 n 개라면 time complexity 는 `O(nlogn)`이 된다.

`Heap`자료구조에 대한 설명은 [DataStructure - Binary Heap](https://github.com/JaeYeopHan/Interview_Question_for_Beginner/tree/master/DataStructure#binary-heap)부분을 참고하면 된다.

[제목 없음](https://www.notion.so/878c8fa027dd4843909070ebcf32df37)

### **Quick Sort**

Sorting 기법 중 가장 빠르다고 해서 quick 이라는 이름이 붙여졌다. **하지만 Worst Case 에서는 시간복잡도가 O(n^2)가 나올 수도 있다.** 하지만 `constant factor`가 작아서 속도가 빠르다.

`Quick Sort` 역시 `Divide and Conquer` 전략을 사용하여 Sorting 이 이루어진다. Divide 과정에서 `pivot`이라는 개념이 사용된다. 입력된 배열에 대해 오름차순으로 정렬한다고 하면 이 pivot 을 기준으로 좌측은 pivot 으로 설정된 값보다 작은 값이 위치하고, 우측은 큰 값이 위치하도록 `partition`된다. 이렇게 나뉜 좌, 우측 각각의 배열을 다시 재귀적으로 Quick Sort 를 시키면 또 partition 과정이 적용된다.이 때 한 가지 주의할 점은 partition 과정에서 pivot 으로 설정된 값은 다음 재귀과정에 포함시키지 않아야 한다. 이미 partition 과정에서 정렬된 자신의 위치를 찾았기 때문이다.

### **Quick Sort's worst case**

그렇다면 어떤 경우가 Worst Case 일까? Quick Sort 로 오름차순 정렬을 한다고 하자. 그렇다면 Worst Case 는 partition 과정에서 pivot value 가 항상 배열 내에서 가장 작은 값 또는 가장 큰 값으로 설정되었을 때이다. 매 partition 마다 `unbalanced partition`이 이뤄지고 이렇게 partition 이 되면 비교 횟수는 원소 n 개에 대해서 n 번, (n-1)번, (n-2)번 … 이 되므로 시간 복잡도는 **O(n^2)** 이 된다.




[제목 없음](https://www.notion.so/30a9a1d8f8f04b45b9bfcea887fd7094)

### **[code](https://github.com/JaeYeopHan/algorithm_basic_java/blob/master/src/test/java/sort/QuickSort.java)**

### **non-Comparisons Sorting Algorithm**

`Counting Sort`, `Radix Sort` 를 소개한다.

### **Counting Sort**

Count Sort 는 말 그대로 몇 개인지 개수를 세어 정렬하는 방식이다. 정렬하고자 하는 값 중 **최대값에 해당하는 값을 size 로 하는 임시 배열** 을 만든다. 만들어진 배열의 index 중 일부는 정렬하고자 하는 값들이 되므로 그 값에는 그 값들의 **개수** 를 나타낸다. 정렬하고자 하는 값들이 몇 개씩인지 파악하는 임시 배열이 만들어졌다면 이 임시 배열을 기준으로 정렬을 한다. 그 전에 임시 배열에서 한 가지 작업을 추가적으로 수행해주어야 하는데 큰 값부터 즉 큰 index 부터 시작하여 누적된 값으로 변경해주는 것이다. 이 누적된 값은 정렬하고자 하는 값들이 정렬될 index 값을 나타내게 된다. 작업을 마친 임시 배열의 index 는 정렬하고자 하는 값을 나타내고 value 는 정렬하고자 하는 값들이 정렬되었을 때의 index 를 나타내게 된다. 이를 기준으로 정렬을 해준다. 점수와 같이 0~100 으로 구성되는 좁은 범위에 존재하는 데이터들을 정렬할 때 유용하게 사용할 수 있다.

[제목 없음](https://www.notion.so/e41ee5cba93a4348916bdd9a99983a1e)

### **Radix Sort**

정렬 알고리즘의 한계는 O(n log n)이지만, 기수 정렬은 이 한계를 넘어설 수 있는 알고리즘이다. 단, 한 가지 단점이 존재하는데 적용할 수 있는 범위가 제한적이라는 것이다. 이 범위는 **데이터 길이** 에 의존하게 된다. 정렬하고자 하는 데이터의 길이가 동일하지 않은 데이터에 대해서는 정렬이 불가능하다. 숫자말고 문자열의 경우도 마찬가지이다. (불가능하다는 것은 기존의 정렬 알고리즘에 비해 기수 정렬 알고리즘으로는 좋은 성능을 내는데 불가능하다는 것이다.)

기수(radix)란 주어진 데이터를 구성하는 기본요소를 의미한다. 이 기수를 이용해서 정렬을 진행한다. 하나의 기수마다 하나의 버킷을 생성하여, 분류를 한 뒤에, 버킷 안에서 또 정렬을 하는 방식이다.

기수 정렬은 `LSD(Least Significant Digit)` 방식과 `MSD(Most Significant Digit)` 방식 두 가지로 나뉜다. LSD 는 덜 중요한 숫자부터 정렬하는 방식으로 예를 들어 숫자를 정렬한다고 했을 때, 일의 자리부터 정렬하는 방식이다. MSD 는 중요한 숫자부터 정렬하는 방식으로 세 자리 숫자면 백의 자리부터 정렬하는 방식이다.

두 가지 방식의 Big-O 는 동일하다. 하지만 주로 기수정렬을 이야기할 때는 LSD 를 이야기한다. LSD 는 중간에 정렬 결과를 볼 수 없다. 무조건 일의 자리부터 시작해서 백의 자리까지 모두 정렬이 끝나야 결과를 확인할 수 있고, 그 때서야 결과가 나온다. 하지만 MSD 는 정렬 중간에 정렬이 될 수 있다. 그러므로 정렬하는데 걸리는 시간을 줄일 수 있다. 하지만 정렬이 완료됬는지 확인하는 과정이 필요하고 이 때문에 메모리를 더 사용하게 된다. 또 상황마다 일관적인 정렬 알고리즘을 사용하여 정렬하는데 적용할 수 없으므로 불편하다. 이러한 이유들로 기수 정렬을 논할 때는 주로 LSD 에 대해서 논한다.

[제목 없음](https://www.notion.so/0b11aeac2b914b10bf3e2235f32b9f29)

### **Sorting Algorithm's Complexity 정리**

[제목 없음](https://www.notion.so/8df937c7f4b64bd0adb9bc68f48c850f)

### **더 읽을거리**

- [Sorting Algorithm 을 비판적으로 바라보자](http://asfirstalways.tistory.com/338)
