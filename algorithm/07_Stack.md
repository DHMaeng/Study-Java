### Stack이란?

자료 구조 중 하나인 Stack의 사전적 정의는 '쌓다', '더미'입니다. 상자에 물건을 쌓아 올리듯이 데이터를 쌓는 자료 구조라고 할 수 있습니다. Stack의 가장 큰 특징은 나중에 들어간 것이 먼저 나오는 (Last In First Out)의 형태를 띈다는 것입니다. 이 방식을 가진 자료구조인 Stack을 활용하여 다양한 문제를 해결할 수 있습니다. 자바에서 Stack은 java.util.Stack을 import하면 바로 사용할 수 있습니다.

 



![img](https://blog.kakaocdn.net/dn/YhtxB/btqHsbZTFED/DhCPI65pmzfsqETjti138k/img.jpg)



### Stack의 특징

**1.** 먼저 들어간 자료가 나중에 나옴 LIFO(Last In First Out) 구조
**2.** 시스템 해킹에서 버퍼오버플로우 취약점을 이용한 공격을 할 때 스택 메모리의 영역에서 함 
**3.** 인터럽트처리, 수식의 계산, 서브루틴의 복귀 번지 저장 등에 쓰임
**4.** 그래프의 깊이 우선 탐색(DFS)에서 사용
**5.** 재귀적(Recursion) 함수를 호출 할 때 사용

 

##  Stack 사용법 

### Stack 선언

```
import java.util.Stack; //import
Stack<Integer> stack = new Stack<>(); //int형 스택 선언
Stack<String> stack = new Stack<>(); //char형 스택 선언
```

자바에서 stack을 선언하려면 <stack>import java.util.Stack 을 import 한 뒤 Stack<Element> stack = new Stack<>();과 같은 형식으로 선언하면 됩니다. 

 

### Stack 값 추가

```
Stack<Integer> stack = new Stack<>(); //int형 스택 선언
stack.push(1);     // stack에 값 1 추가
stack.push(2);     // stack에 값 2 추가
stack.push(3);     // stack에 값 3 추가
```

Stack에 값을 추가하고 싶다면 push(value)라는 메소드를 활용하면 됩니다. Stack에 위의 예제와 같이 값을 계속해서 추가해나간다면 아래 그림처럼 데이터가 쌓이게 됩니다.



![img](https://blog.kakaocdn.net/dn/cbrGNm/btqHsbZTFF4/qJgrCMjCTFd1d6uU7EV4k0/img.png)



### Stack 값 삭제

```
Stack<Integer> stack = new Stack<>(); //int형 스택 선언
stack.push(1);     // stack에 값 1 추가
stack.push(2);     // stack에 값 2 추가
stack.push(3);     // stack에 값 3 추가
stack.pop();       // stack에 값 제거
stack.clear();     // stack의 전체 값 제거 (초기화)
```

 스택에서 값을 제거하고싶다면 pop()이라는 메서드를 사용하면 됩니다. pop을 하면 가장 위쪽에 있는 원소의 값이 아래 그림과 같이 제거됩니다. 스택의 값을 모두 제거하고싶다면 clear()라는 메서드를 사용하면 됩니다.



![img](https://blog.kakaocdn.net/dn/cru4A7/btqHra73O8h/Q2fkHsFA9NJFxsD5n1AKN0/img.png)



 

### Stack의 가장 상단의 값 출력

```
Stack<Integer> stack = new Stack<>(); //int형 스택 선언
stack.push(1);     // stack에 값 1 추가
stack.push(2);     // stack에 값 2 추가
stack.push(3);     // stack에 값 3 추가
stack.peek();     // stack의 가장 상단의 값 출력
```

스택의 가장 위에 있는 값을 출력하고 싶다면 peek()라는 함수를 사용하면 됩니다. 아래 그림과 같이 가장 마지막에 들어간 값이 출력됩니다.



![img](https://blog.kakaocdn.net/dn/HfKZA/btqHgqLjLJG/mk3ViUTmahCubC86UCptK1/img.png)



 

### Stack의 기타 메서드

```
Stack<Integer> stack = new Stack<>(); //int형 스택 선언
stack.push(1);     // stack에 값 1 추가
stack.push(2);     // stack에 값 2 추가
stack.size();      // stack의 크기 출력 : 2
stack.empty();     // stack이 비어있는제 check (비어있다면 true)
stack.contains(1) // stack에 1이 있는지 check (있다면 true)
```

그 밖에도 stack에는 크기를 구하는 size()메서드와 stack이 비어있는지 확인하는 empty() 메서드(비어있다면 true, 그렇지 않다면 false를 return) stack의 값을 search하는 contains(int value)함수가 있습니다.