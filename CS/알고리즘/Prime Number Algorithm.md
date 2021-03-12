# Prime Number Algorithm

## **Prime Number Algorithm**

소수란 양의 약수를 딱 두 개만 갖는 자연수를 소수라 부른다. 2, 3, 5, 7, 11, …이 그런 수들인데, 소수를 판별하는 방법으로 첫번째 어떤 수 N 이 소수인지 판별하기 위해서는 N 을 2 부터 N 보다 1 작은 수까지 나누어서 나머지가 0 인 경우가 있는지 검사하는 방법과 두번째로 `에라토스테네스의 체`를 사용할 수 있다.

### **에라토스테네스의 체 [Eratosthenes’ sieve]**

`에라토스테네스의 체(Eratosthenes’ sieve)`는, 임의의 자연수에 대하여, 그 자연수 이하의 `소수(prime number)`를 모두 찾아 주는 방법이다. 입자의 크기가 서로 다른 가루들을 섞어 체에 거르면 특정 크기 이하의 가루들은 다 아래로 떨어지고, 그 이상의 것들만 체 위에 남는 것처럼, 에라토스테네스의 체를 사용하면 특정 자연수 이하의 합성수는 다 지워지고 소수들만 남는 것이다. 방법은 간단하다. 만일 `100` 이하의 소수를 모두 찾고 싶다면, `1` 부터 `100` 까지의 자연수를 모두 나열한 후, 먼저 소수도 합성수도 아닌 `1`을 지우고, `2`외의 `2`의 배수들을 다 지우고, `3`외의 `3`의 배수들을 다 지우고, `5`외의 `5`의 배수들을 지우는 등의 이 과정을 의 `100`제곱근인 `10`이하의 소수들에 대해서만 반복하면, 이때 남은 수들이 구하고자 하는 소수들이다.

에라토스테네스의 체를 이용하여 50 까지의 소수를 구하는 순서를 그림으로 표현하면 다음과 같다.

1. 초기 상태

[제목 없음](https://www.notion.so/fbbfa3c2f38c4097b08d841e3bba263c)

1. 소수도 합성수도 아닌 1 제거

[제목 없음](https://www.notion.so/b2a9cc5554014672a761b7927a9032df)

1. 2 외의 2 의 배수들을 제거

[제목 없음](https://www.notion.so/3dd9af35128e496490cd579a79763201)

1. 3 외의 3 의 배수들을 제거

[제목 없음](https://www.notion.so/6288d05f269048f7ba2e553bdace8b10)

1. 5 외의 5 의 배수들을 제거

[제목 없음](https://www.notion.so/08d5ff07ef3c4e59b3cccb6cf78744a1)

1. 7 외의 7 의 배수들을 제거(50 이하의 소수 판별 완료)

[제목 없음](https://www.notion.so/f9896b1998f34d3f902d6ce0bd9b34fb)

[제목 없음](https://www.notion.so/f61e93d900da46c992bf4bf689e4ff39)

### **[code](https://github.com/alstn2468/BaekJoon_Online_Judge/blob/master/1900~1999/1929.c)**

[뒤로](https://github.com/JaeYeopHan/for_beginner)/[위로](https://github.com/JaeYeopHan/Interview_Question_for_Beginner/tree/master/Algorithm#algorithm)

### **Time Complexity**

O(1) < O(log N) < O(N) < O(N log N) < O(N^2) < O(N^3)

O(2^N) : 크기가 N 인 집합의 부분 집합

O(N!) : 크기가 N 인 순열

### **알고리즘 문제 연습 사이트**

- [https://algospot.com/](https://algospot.com/)
- [https://codeforces.com](https://codeforces.com/)
- [http://topcoder.com](http://topcoder.com/)
- [https://www.acmicpc.net/](https://www.acmicpc.net/)
- [https://leetcode.com/problemset/algorithms/](https://leetcode.com/problemset/algorithms/)
- [https://programmers.co.kr/learn/challenges](https://programmers.co.kr/learn/challenges)
- [https://www.hackerrank.com](https://www.hackerrank.com/)
- [http://codingdojang.com/](http://codingdojang.com/)
- [http://codeup.kr/JudgeOnline/index.php](http://codeup.kr/JudgeOnline/index.php)
- [http://euler.synap.co.kr/](http://euler.synap.co.kr/)
- [http://koistudy.net](http://koistudy.net/)
- [https://www.codewars.com](https://www.codewars.com/)
- [https://app.codility.com/programmers/](https://app.codility.com/programmers/)
- [http://euler.synap.co.kr/](http://euler.synap.co.kr/)
- [https://swexpertacademy.com/](https://swexpertacademy.com/)
- [https://www.codeground.org/](https://www.codeground.org/)
- [https://onlinejudge.org/](https://onlinejudge.org/)