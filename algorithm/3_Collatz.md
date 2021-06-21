# 콜라츠 추측

1937년 Collatz란 사람에 의해 제기된 이 추측은, 주어진 수가 1이 될때까지 다음 작업을 반복하면, 모든 수를 1로 만들 수 있다는 추측입니다. 작업은 다음과 같습니다.

```
1-1. 입력된 수가 짝수라면 2로 나눕니다. 
1-2. 입력된 수가 홀수라면 3을 곱하고 1을 더합니다.
2. 결과로 나온 수에 같은 작업을 1이 될 때까지 반복합니다.
```

예를 들어, 입력된 수가 6이라면 6→3→10→5→16→8→4→2→1 이 되어 총 8번 만에 1이 됩니다. 위 작업을 몇 번이나 반복해야하는지 반환하는 함수, solution을 완성해 주세요. 단, 작업을 500번을 반복해도 1이 되지 않는다면 –1을 반환해 주세요.

##### 제한 사항

- 입력된 수, `num`은 1 이상 8000000 미만인 정수입니다.



**내코드**

길고 가독성이 떨어진다.?

```java
class Solution {
    public int solution(int num) {
        int answer = 0;
        boolean flag = false;
        long n = (long) num;
        int i = 0;
        
        while(!flag) {
            if(num == 1){
                break;
            }
            if(num % 2 == 0){
                num = num / 2;
            } else {
                num = num * 3 + 1;  
            } 
            i++;
            if(i > 500){
                i = -1;
                break;  
            } 
        }
        answer = i;
        return answer;
    }
}
```

**오류**

🔶 num*3+1 > int형 초과 하기 때문에 long형으로 바꿔줘야 한다.

🔶num이 1일 경우 바로 루프를 나와야하므로 앞에 위치 해야 한다.



**개선점**

3항연산자를 사용하여 if/else를 한줄로

🔶for문을 500번 하면 -1을 자동으로 리턴하도록 설계하였기 때문에 수가 500일때 return -1 하는 조건문을 사용안해도 된다.

```java
class Collatz {
    public int collatz(int num) {
    long n = (long)num;
    for(int i =0; i<500; i++){      
      if(n==1) return i;
      n = (n%2==0) ? n/2 : n*3+1;           
    }
    return -1;
  }
    // 아래는 테스트로 출력해 보기 위한 코드입니다.
    public static void main(String[] args) {
        Collatz c = new Collatz();
        int ex = 6;
        System.out.println(c.collatz(ex));
    }
}
```

