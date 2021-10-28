# Red Black Tree

## **Red Black Tree**

RBT(Red-Black Tree)는 BST 를 기반으로하는 트리 형식의 자료구조이다. 결론부터 말하자면 Red-Black Tree 에 데이터를 저장하게되면 Search, Insert, Delete 에 O(log n)의 시간 복잡도가 소요된다. 동일한 노드의 개수일 때, depth 를 최소화하여 시간 복잡도를 줄이는 것이 핵심 아이디어이다. 동일한 노드의 개수일 때, depth 가 최소가 되는 경우는 tree 가 complete binary tree 인 경우이다.

### **Red-Black Tree 의 정의**

Red-Black Tree 는 다음의 성질들을 만족하는 BST 이다.

1. 각 노드는 `Red` or `Black`이라는 색깔을 갖는다.
2. Root node 의 색깔은 `Black`이다.
3. 각 leaf node 는 `black`이다.
4. 어떤 노드의 색깔이 `red`라면 두 개의 children 의 색깔은 모두 black 이다.
5. 각 노드에 대해서 노드로부터 descendant leaves 까지의 단순 경로는 모두 같은 수의 black nodes 들을 포함하고 있다. 이를 해당 노드의 `Black-Height`라고 한다. *cf) Black-Height: 노드 x 로부터 노드 x 를 포함하지 않은 leaf node 까지의 simple path 상에 있는 black nodes 들의 개수*


