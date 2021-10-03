# 1. 설탕 배달

## 문제

상근이는 요즘 설탕공장에서 설탕을 배달하고 있다. 상근이는 지금 사탕가게에 설탕을 정확하게 N킬로그램을 배달해야 한다. 설탕공장에서 만드는 설탕은 봉지에 담겨져 있다. 봉지는 3킬로그램 봉지와 5킬로그램 봉지가 있다.

상근이는 귀찮기 때문에, 최대한 적은 봉지를 들고 가려고 한다. 예를 들어, 18킬로그램 설탕을 배달해야 할 때, 3킬로그램 봉지 6개를 가져가도 되지만, 5킬로그램 3개와 3킬로그램 1개를 배달하면, 더 적은 개수의 봉지를 배달할 수 있다.

상근이가 설탕을 정확하게 N킬로그램 배달해야 할 때, 봉지 몇 개를 가져가면 되는지 그 수를 구하는 프로그램을 작성하시오.

## 입력

첫째 줄에 N이 주어진다. (3 ≤ N ≤ 5000)

## 출력

상근이가 배달하는 봉지의 최소 개수를 출력한다. 만약, 정확하게 N킬로그램을 만들 수 없다면 -1을 출력한다.



### 풀이 1

```java
import java.util.Scanner;
public class Main {

	public static void main(String[] args) {
		
		Scanner sc = new Scanner(System.in); 
		int N = sc.nextInt();
		int sum = 0;
		int min = 2000;
		
		for(int i = 0 ; i <= N/5 ; i++) {
			for(int j = 0 ; j <= N/3 ; j++) {
				sum = 5*i + 3*j;
				int count = i+j;
				if(N == sum && count < min) {
					min = count;
				}
			}
		}
		if(min == 2000) {
			min = -1;
		}
		System.out.println(min);
	}
}
```



### 풀이 2

```java
import java.util.*;
class Main{public static void main(String[]t){
    int a = new Scanner(System.in).nextInt()
    int b=a%5;
    System.out.print(a==4||a==7?-1:b==0?a/5:b==1||b==3?a/5+1:a/5+2);
}
```

5로 나눈 나머지에서 나올수 있는 경우의 수로 풀었는데 핵 짧아 진다. ㄷㄷ





# 2. ATM

## 문제

인하은행에는 ATM이 1대밖에 없다. 지금 이 ATM앞에 N명의 사람들이 줄을 서있다. 사람은 1번부터 N번까지 번호가 매겨져 있으며, i번 사람이 돈을 인출하는데 걸리는 시간은 Pi분이다.

사람들이 줄을 서는 순서에 따라서, 돈을 인출하는데 필요한 시간의 합이 달라지게 된다. 예를 들어, 총 5명이 있고, P1 = 3, P2 = 1, P3 = 4, P4 = 3, P5 = 2 인 경우를 생각해보자. [1, 2, 3, 4, 5] 순서로 줄을 선다면, 1번 사람은 3분만에 돈을 뽑을 수 있다. 2번 사람은 1번 사람이 돈을 뽑을 때 까지 기다려야 하기 때문에, 3+1 = 4분이 걸리게 된다. 3번 사람은 1번, 2번 사람이 돈을 뽑을 때까지 기다려야 하기 때문에, 총 3+1+4 = 8분이 필요하게 된다. 4번 사람은 3+1+4+3 = 11분, 5번 사람은 3+1+4+3+2 = 13분이 걸리게 된다. 이 경우에 각 사람이 돈을 인출하는데 필요한 시간의 합은 3+4+8+11+13 = 39분이 된다.

줄을 [2, 5, 1, 4, 3] 순서로 줄을 서면, 2번 사람은 1분만에, 5번 사람은 1+2 = 3분, 1번 사람은 1+2+3 = 6분, 4번 사람은 1+2+3+3 = 9분, 3번 사람은 1+2+3+3+4 = 13분이 걸리게 된다. 각 사람이 돈을 인출하는데 필요한 시간의 합은 1+3+6+9+13 = 32분이다. 이 방법보다 더 필요한 시간의 합을 최소로 만들 수는 없다.

줄을 서 있는 사람의 수 N과 각 사람이 돈을 인출하는데 걸리는 시간 Pi가 주어졌을 때, 각 사람이 돈을 인출하는데 필요한 시간의 합의 최솟값을 구하는 프로그램을 작성하시오.

## 입력

첫째 줄에 사람의 수 N(1 ≤ N ≤ 1,000)이 주어진다. 둘째 줄에는 각 사람이 돈을 인출하는데 걸리는 시간 Pi가 주어진다. (1 ≤ Pi ≤ 1,000)

## 출력

첫째 줄에 각 사람이 돈을 인출하는데 필요한 시간의 합의 최솟값을 출력한다.



### 풀이

```java
import java.util.Arrays;
import java.util.Scanner;
public class Main {

	public static void main(String[] args) {
		
		Scanner sc = new Scanner(System.in); 
		
		int N = sc.nextInt();
		int[] P = new int[N];
		for(int i = 0 ; i < N ; i++) {
			P[i] = sc.nextInt();
		}
		
		//Arrays.sort(P);
		//sort 구현
		for(int i = 0 ; i < N - 1 ; i++) {
			int minIndex = i;
			for(int j = i + 1 ; j < N ; j++) {
				if(P[minIndex] > P[j]) {
					minIndex = j;
				}	
			}
			int temp = P[i];
			P[i] = P[minIndex];
			P[minIndex] = temp;
		}
		
//		for(int i : P) {
//			System.out.print(i+" ");
//		}
		
		int sum = 0;
		int total = 0;
		for(int i = 0 ; i < N ; i++) {
			sum = sum + P[i];
			total = total + sum;
            //total += P[i]*(N-i) 각 원소들이 총 N-i번씩 더해지게 때문에 일케하면 더 까리하네
		}
		System.out.println(total);
	}
}
```

