# 최대공약수 최소공배수

###### 문제 설명

두 수를 입력받아 두 수의 최대공약수와 최소공배수를 반환하는 함수, solution을 완성해 보세요. 배열의 맨 앞에 최대공약수, 그다음 최소공배수를 넣어 반환하면 됩니다. 예를 들어 두 수 3, 12의 최대공약수는 3, 최소공배수는 12이므로 solution(3, 12)는 [3, 12]를 반환해야 합니다.

##### 제한 사항

- 두 수는 1이상 1000000이하의 자연수입니다.



**내풀이**

```java
class Solution {
    public int[] solution(int n, int m) {
        int[] answer = new int[2];
        
        int min = 0;
        int max = 0;
        
        if(n > m){
            min = m;
            max = n;
        } else {
            min = n;
            max = m;
        }
        for(int i = 1 ; i <= min ; i++){
            if(min % i == 0 && max % i == 0){
                answer[0] = i;
            }
        }
        answer[1] = min * max / answer[0];
        
        return answer;
    }
}
```



**재귀함수풀이!!**

```java
import java.util.Arrays;
class TryHelloWorld {
    public int[] gcdlcm(int a, int b) {
        int[] answer = new int[2];

          answer[0] = gcd(a,b);
        answer[1] = (a*b)/answer[0];
        return answer;
    }

   public static int gcd(int p, int q)
   {
    if (q == 0) return p;
    return gcd(q, p%q);
   }

    // 아래는 테스트로 출력해 보기 위한 코드입니다.
    public static void main(String[] args) {
        TryHelloWorld c = new TryHelloWorld();
        System.out.println(Arrays.toString(c.gcdlcm(3, 12)));
    }
}
```



