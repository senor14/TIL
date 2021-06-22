# Tree

## **Tree**

1. 트리의 개념.
2. 트리의 구성 요소.
3. 트리의 종류.

### **트리의 개념**

트리라는 이름이 나온 이유는 실제 나무를 거꾸로 세워놓은 듯한 모양이라서 트리라고 부른다.

[https://camo.githubusercontent.com/cd887d9508e16c2eea18fcceaca35045bf80cf24e0d74589b5f8c05efe96954f/68747470733a2f2f6b2e6b616b616f63646e2e6e65742f646e2f6274376f586f2f6274717564374a746c33342f425a494a43424c765931394f73515057544b4d6172302f696d672e706e67](https://camo.githubusercontent.com/cd887d9508e16c2eea18fcceaca35045bf80cf24e0d74589b5f8c05efe96954f/68747470733a2f2f6b2e6b616b616f63646e2e6e65742f646e2f6274376f586f2f6274717564374a746c33342f425a494a43424c765931394f73515057544b4d6172302f696d672e706e67)

선형 자료구조에서 배열이나 리스트 등도 존재하지만, 트리가 나온 이유는 뭘까?

일반 배열에서 삽입이나 삭제를 하는데 O(N)의 시간이 걸린다. 배열의 첫번째 원소에 삽입하는 경우 나머지 모든 요소들을 한 칸씩 뒤로 미뤄야 하므로 최악의 시간 복잡도 O(N)이 나온다. 하지만, 트리는 편향 트리가 아닌 이상 일반적인 트리에서는 O(log N) 정도의 시간으로 줄여진다.

또한 트리는 계층 구조를 이루는 경우에 굉장히 좋다.

[https://camo.githubusercontent.com/a167cc88ecf3fe8b4c51653c84cc1ec0ec82e7101e623fba320c256e102c6c23/68747470733a2f2f6b2e6b616b616f63646e2e6e65742f646e2f62594770316e2f62747175636e304d3163782f514f3763795777787939714a49434b4f316a6d5366302f696d672e706e67](https://camo.githubusercontent.com/a167cc88ecf3fe8b4c51653c84cc1ec0ec82e7101e623fba320c256e102c6c23/68747470733a2f2f6b2e6b616b616f63646e2e6e65742f646e2f62594770316e2f62747175636e304d3163782f514f3763795777787939714a49434b4f316a6d5366302f696d672e706e67)

회사의 조직도를 생각해보면, 맨 위에 회장님, 사장님이 있고, 부서별, 팀별로 각각 트리가 생길 것이다. 이런 경우, 원하는 부서를 타고 내려가기만 하면 되므로 다른 자료 구조보다 찾기가 훨씬 쉬울 것이다.

**특징**

- Tree는 Stack이나 Queue와 같이 선형 구조가 아닌 비선형 자료구조이다.
- 계층적 관계를 표현한다.
- 루트 노드를 제외한 모든 노드는 단 하나의 부모 노드만을 갖는다.

### **[트리의 구성 요소]**

[https://camo.githubusercontent.com/989bd794ecea87bec6db164f6f39b1ec909970a5de8f1b19d8a3870285c4645d/68747470733a2f2f6b2e6b616b616f63646e2e6e65742f646e2f6341496e51672f627471756453464c5855502f6f766a3152384e664f316346383557317a6275416d6b2f696d672e706e67](https://camo.githubusercontent.com/989bd794ecea87bec6db164f6f39b1ec909970a5de8f1b19d8a3870285c4645d/68747470733a2f2f6b2e6b616b616f63646e2e6e65742f646e2f6341496e51672f627471756453464c5855502f6f766a3152384e664f316346383557317a6275416d6b2f696d672e706e67)

- Node : 트리를 구성하는 각각의 요소.
- Edge : 트리를 구성하기 위해 노드와 노드를 연결하는 선.
- Root Node : 트리 구조에서 최상위에 있는 노드.
- Terminal Node : 하위에 다른 노드가 연결되어 있지 않은 노드.
- Internal Node : 단말 노드를 제외한 모든 노드로 루트 노드를 포함한다.

### **[Binary Tree(이진 트리)]**

[https://camo.githubusercontent.com/5a377ebf4205ca8d3c2305c2bff5e638ca536f91fba5df4d24e45bd1b78f1de7/68747470733a2f2f6b2e6b616b616f63646e2e6e65742f646e2f5a4b5065372f62747175647331446779522f513254367559524e445645485345714e37516c35514b2f696d672e706e67](https://camo.githubusercontent.com/5a377ebf4205ca8d3c2305c2bff5e638ca536f91fba5df4d24e45bd1b78f1de7/68747470733a2f2f6b2e6b616b616f63646e2e6e65742f646e2f5a4b5065372f62747175647331446779522f513254367559524e445645485345714e37516c35514b2f696d672e706e67)

- 루트 노드를 중심으로 두 개의 서브 트리로 나뉘어 진다. (노드가 없을 수도 있다.) 나뉘어진 두 서브 트리도 모두 이진 트리어야 한다.
- 각 층별로 숫자를 매겨서 이를 트리의 레벨이라고 한다. 레벨은 1부터 시작하고 루트 노드의 레벨은 1이다. 트리의 최고 레벨을 가리켜 트리의 높이라고 한다.
- 종류
  - **Full Binary Tree(포화 이진 트리)** : 모든 레벨이 꽉 찬 이진 트리를 의미한다.
    - 레벨 별로 노드의 개수가 1,2,4,8,16 ... 으로 늘어난다. 따라서 일반적인 이진트리에서 각 레벨 별 최대 노드의 개수는 2^(k - 1)이 된다.
    - 레벨 별 노드는 공비가 2인 등비 수열이라고 볼 수 있으므로 등비수열의 합으로 생각하면 높이가 h인 이진트리가 가질 수 있는 최대 노드 수는 2^h - 1이라고 할 수 있다.
  - **Complete Binary Tree(완전 이진 트리)** : 왼쪽에서 오른쪽으로 순서대로 차곡 차곡 채워진 이진 트리를 의미한다.
    - 노드를 삽입할 때 왼쪽부터 차례대로 삽입하는 트리이다. 왼쪽이 비어있고 오른쪽이 들어가있는 트리는 완전 이진 트리가 아니다.
  - **Skewed Binary Tree(편향 이진 트리)** : 모든 노드가 부모의 왼쪽 자식이기 때문에 왼쪽으로 편향되어 있거나 반대로 모든 노드가 부모의 오른쪽 자식이기 때문에 오른쪽으로 편향되어 있는 이진 트리를 말한다.

### **참고**

- [[Java][자료구조] Tree (1) - 트리의 정의와 특성, 이진트리에 대하여](https://ju-nam2.tistory.com/25?category=868623)