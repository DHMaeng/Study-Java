# 더 맵게

###### 문제 설명

매운 것을 좋아하는 Leo는 모든 음식의 스코빌 지수를 K 이상으로 만들고 싶습니다. 모든 음식의 스코빌 지수를 K 이상으로 만들기 위해 Leo는 스코빌 지수가 가장 낮은 두 개의 음식을 아래와 같이 특별한 방법으로 섞어 새로운 음식을 만듭니다.

```
섞은 음식의 스코빌 지수 = 가장 맵지 않은 음식의 스코빌 지수 + (두 번째로 맵지 않은 음식의 스코빌 지수 * 2)
```

Leo는 모든 음식의 스코빌 지수가 K 이상이 될 때까지 반복하여 섞습니다.
Leo가 가진 음식의 스코빌 지수를 담은 배열 scoville과 원하는 스코빌 지수 K가 주어질 때, 모든 음식의 스코빌 지수를 K 이상으로 만들기 위해 섞어야 하는 최소 횟수를 return 하도록 solution 함수를 작성해주세요.

##### 제한 사항

- scoville의 길이는 2 이상 1,000,000 이하입니다.
- K는 0 이상 1,000,000,000 이하입니다.
- scoville의 원소는 각각 0 이상 1,000,000 이하입니다.
- 모든 음식의 스코빌 지수를 K 이상으로 만들 수 없는 경우에는 -1을 return 합니다.

##### 입출력 예

| scoville             | K    | return |
| -------------------- | ---- | ------ |
| [1, 2, 3, 9, 10, 12] | 7    | 2      |

##### 입출력 예 설명

1. 스코빌 지수가 1인 음식과 2인 음식을 섞으면 음식의 스코빌 지수가 아래와 같이 됩니다.
   새로운 음식의 스코빌 지수 = 1 + (2 * 2) = 5
   가진 음식의 스코빌 지수 = [5, 3, 9, 10, 12]
2. 스코빌 지수가 3인 음식과 5인 음식을 섞으면 음식의 스코빌 지수가 아래와 같이 됩니다.
   새로운 음식의 스코빌 지수 = 3 + (5 * 2) = 13
   가진 음식의 스코빌 지수 = [13, 9, 10, 12]

모든 음식의 스코빌 지수가 7 이상이 되었고 이때 섞은 횟수는 2회입니다.



솔루션

```java
import java.util.PriorityQueue;
class Solution {
    public int solution(int[] scoville, int K) {
        int answer = 0;
        int cnt = 0;
        PriorityQueue<Integer> heap = new PriorityQueue<Integer>();
        
        for(int temp : scoville){
            heap.add(temp);
        }
      
        while(heap.peek() < K){
            if(heap.size() <= 1 && heap.peek() < K){
                return -1;
            }
            int a = heap.poll();
            int b = heap.poll();
            
            int result = a + b * 2;
            
            heap.add(result);
            cnt ++;
        }
        return cnt;
    }
}
```







##  Priority Queue 사용법 

### Priority Queue 선언

```
import java.util.PriorityQueue; //import

//int형 priorityQueue 선언 (우선순위가 낮은 숫자 순)
PriorityQueue<Integer> priorityQueue = new PriorityQueue<>();

//int형 priorityQueue 선언 (우선순위가 높은 숫자 순)
PriorityQueue<Integer> priorityQueue = new PriorityQueue<>(Collections.reverseOrder());

//String형 priorityQueue 선언 (우선순위가 낮은 숫자 순)
PriorityQueue<String> priorityQueue = new PriorityQueue<>(); 

//String형 priorityQueue 선언 (우선순위가 높은 숫자 순)
PriorityQueue<String> priorityQueue = new PriorityQueue<>(Collections.reverseOrder());
```

자바에서 우선순위 큐 라이브러리를 사용하고 싶다면 java.util.PriorityQueue 를 import 하고 Queue<Element> queue = new Queue<>()와 같은 형식으로 선언하면 됩니다. 기본은 우선순위가 낮은 숫자가 부여되고 만약 높은 숫자가 우선순위가 되게 하고 싶다면 선언 시 Collections.reverseOrder() 메서드를 활용합니다.

 

### Priority Queue 값 추가

```
priorityQueue.add(1);     // priorityQueue 값 1 추가
priorityQueue.add(2);     // priorityQueue 값 2 추가
priorityQueue.offer(3);   // priorityQueue 값 3 추가
```

자바의 우선순위 큐에 값을 추가하고 싶다면 add(value) 또는 offer(value)라는 메서드를 활용하면 됩니다. add(value) 메서드의 경우 만약 삽입에 성공하면 true를 반환하고, 큐에 여유 공간이 없어 삽입에 실패하면 IllegalStateException을 발생시킵니다. 우선순위 큐에 값을 추가한다면 아래 그림과 같은 과정을 통해 즉시 정렬이 됩니다.



![img](https://blog.kakaocdn.net/dn/b52ZtE/btqHjpsl7Os/Hwdi4lWzY26XdbaEgdqEB0/img.png)



 

### Priority Queue 값 삭제

```
priorityQueue.poll();       // priorityQueue에 첫번째 값을 반환하고 제거 비어있다면 null
priorityQueue.remove();     // priorityQueue에 첫번째 값 제거
priorityQueue.clear();      // priorityQueue에 초기화
```

우선순위 큐에서 값을 제거하고 싶다면 poll()이나 remove()라는 메서드를 사용하면 됩니다. 값을 제거할 시 우선순위가 가장 높은 값이 제거됩니다. poll() 함수는 우선순위 큐가 비어있으면 null을 반환합니다. pop을 하면 가장 앞쪽에 있는 원소의 값이 아래 그림과 같이 제거됩니다. queue의 모든 요소를 제거하려면 clear() 메서드를 사용합니다.

 



![img](https://blog.kakaocdn.net/dn/bM5xqo/btqHxcRRMge/cokOnz4QFcExmKeFnDaNW0/img.png)



 

### Priority Queue에서 우선순위가 가장 높은 값 출력

```
PriorityQueue<Integer> priorityQueue = new PriorityQueue<>();//int형 priorityQueue 선언
priorityQueue.offer(2);     // priorityQueue에 값 2 추가
priorityQueue.offer(1);     // priorityQueue에 값 1 추가
priorityQueue.offer(3);     // priorityQueue에 값 3 추가
priorityQueue.peek();       // priorityQueue에 첫번째 값 참조 = 1
```

Priority Queue에서 우선순위가 가장 높은 값을 참조하고 싶다면 peek()라는 메서드를 사용하면 됩니다. 위의 예시에서는 우선순위가 가장 높은 1이 출력됩니다.