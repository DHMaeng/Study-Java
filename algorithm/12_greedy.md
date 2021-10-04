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





# 3. 거스름돈

## 문제

춘향이는 편의점 카운터에서 일한다.

손님이 2원짜리와 5원짜리로만 거스름돈을 달라고 한다. 2원짜리 동전과 5원짜리 동전은 무한정 많이 가지고 있다. 동전의 개수가 최소가 되도록 거슬러 주어야 한다. 거스름돈이 n인 경우, 최소 동전의 개수가 몇 개인지 알려주는 프로그램을 작성하시오.

예를 들어, 거스름돈이 15원이면 5원짜리 3개를, 거스름돈이 14원이면 5원짜리 2개와 2원짜리 2개로 총 4개를, 거스름돈이 13원이면 5원짜리 1개와 2원짜리 4개로 총 5개를 주어야 동전의 개수가 최소가 된다.

## 입력

첫째 줄에 거스름돈 액수 n(1 ≤ n ≤ 100,000)이 주어진다.

## 출력

거스름돈 동전의 최소 개수를 출력한다. 만약 거슬러 줄 수 없으면 -1을 출력한다.



### 풀이 1

간단하게 나타내려고 할 수록 수학적인 계산이 많이 필요로 하는데 일케하는거 별로 인거 같음

```java
import java.util.Scanner;
public class Main {

	public static void main(String[] args) {
		
		Scanner sc = new Scanner(System.in); 
			
		int n = sc.nextInt();
		
		int count = (n == 1 || n == 3) ? -1 : (n%5 == 0) ? n/5 : (n%5 == 3) ? n/5 + 3 : (n%5 == 1 || n%5 == 4) ? n/5 + 2 : n/5 + 1 ; 

		System.out.println(count);
	}
}
```



### 풀이2

훨쒼 괜찮은듯 속도도 빠르고 직관적이다. 

```java
import java.util.Scanner;
public class Main {
	public static void main(String[] args) {
		int total = new Scanner(System.in).nextInt();
		int answer = -1;
		for (int j = total/5; j > -1; j--) {
			int remain = total - 5*j;
			if( remain%2 == 0) {
				answer = j +  remain/2;
				break;
			}
		}
		System.out.println(answer);
	}
}
```





# 4. 폴리오미노

## 문제

민식이는 다음과 같은 폴리오미노 2개를 무한개만큼 가지고 있다. AAAA와 BB

이제 '.'와 'X'로 이루어진 보드판이 주어졌을 때, 민식이는 겹침없이 'X'를 모두 폴리오미노로 덮으려고 한다. 이때, '.'는 폴리오미노로 덮으면 안 된다.

폴리오미노로 모두 덮은 보드판을 출력하는 프로그램을 작성하시오.



## 입력

첫째 줄에 보드판이 주어진다. 보드판의 크기는 최대 500이다.



## 출력

첫째 줄에 사전순으로 가장 앞서는 답을 출력한다. 만약 덮을 수 없으면 -1을 출력한다.



### 풀이

```java
import java.util.Scanner;
public class Main {
	public static void main(String[] args) {
		
		Scanner sc = new Scanner(System.in); 
		String board = sc.next();
		
		board = board.replaceAll("XXXX","AAAA");
		board = board.replaceAll("XX","BB");
		
		if(board.contains("X")) {
			System.out.println("-1");
		} else {
			System.out.println(board);
		}
	}
}
```



# 5. 로프

## 문제

N(1 ≤ N ≤ 100,000)개의 로프가 있다. 이 로프를 이용하여 이런 저런 물체를 들어올릴 수 있다. 각각의 로프는 그 굵기나 길이가 다르기 때문에 들 수 있는 물체의 중량이 서로 다를 수도 있다.

하지만 여러 개의 로프를 병렬로 연결하면 각각의 로프에 걸리는 중량을 나눌 수 있다. k개의 로프를 사용하여 중량이 w인 물체를 들어올릴 때, 각각의 로프에는 모두 고르게 w/k 만큼의 중량이 걸리게 된다.

각 로프들에 대한 정보가 주어졌을 때, 이 로프들을 이용하여 들어올릴 수 있는 물체의 최대 중량을 구해내는 프로그램을 작성하시오. 모든 로프를 사용해야 할 필요는 없으며, 임의로 몇 개의 로프를 골라서 사용해도 된다.

## 입력

첫째 줄에 정수 N이 주어진다. 다음 N개의 줄에는 각 로프가 버틸 수 있는 최대 중량이 주어진다. 이 값은 10,000을 넘지 않는 자연수이다.

## 출력	

첫째 줄에 답을 출력한다.



### 풀이

```
import java.util.Arrays;
import java.util.Scanner;
public class Main {
	public static void main(String[] args) {
		
		Scanner sc = new Scanner(System.in); 
		int N = sc.nextInt();
		
		int[] rope = new int[N];
		for(int i = 0 ; i < N ; i++) {
			rope[i] = sc.nextInt();
		}
		
		Arrays.sort(rope);
		int max = 0;
		for(int i = 0 ; i < N ; i++) {
			if(max < rope[i] * (N - i)) {
				max = rope[i] * (N - i);
			}
		}
		System.out.println(max);
	}	
}
```



# 6. 주유소

## 문제

어떤 나라에 N개의 도시가 있다. 이 도시들은 일직선 도로 위에 있다. 편의상 일직선을 수평 방향으로 두자. 제일 왼쪽의 도시에서 제일 오른쪽의 도시로 자동차를 이용하여 이동하려고 한다. 인접한 두 도시 사이의 도로들은 서로 길이가 다를 수 있다. 도로 길이의 단위는 km를 사용한다.

처음 출발할 때 자동차에는 기름이 없어서 주유소에서 기름을 넣고 출발하여야 한다. 기름통의 크기는 무제한이어서 얼마든지 많은 기름을 넣을 수 있다. 도로를 이용하여 이동할 때 1km마다 1리터의 기름을 사용한다. 각 도시에는 단 하나의 주유소가 있으며, 도시 마다 주유소의 리터당 가격은 다를 수 있다. 가격의 단위는 원을 사용한다.

예를 들어, 이 나라에 다음 그림처럼 4개의 도시가 있다고 하자. 원 안에 있는 숫자는 그 도시에 있는 주유소의 리터당 가격이다. 도로 위에 있는 숫자는 도로의 길이를 표시한 것이다. 

![img](https://onlinejudgeimages.s3-ap-northeast-1.amazonaws.com/problem/13305/1.png)

제일 왼쪽 도시에서 6리터의 기름을 넣고, 더 이상의 주유 없이 제일 오른쪽 도시까지 이동하면 총 비용은 30원이다. 만약 제일 왼쪽 도시에서 2리터의 기름을 넣고(2×5 = 10원) 다음 번 도시까지 이동한 후 3리터의 기름을 넣고(3×2 = 6원) 다음 도시에서 1리터의 기름을 넣어(1×4 = 4원) 제일 오른쪽 도시로 이동하면, 총 비용은 20원이다. 또 다른 방법으로 제일 왼쪽 도시에서 2리터의 기름을 넣고(2×5 = 10원) 다음 번 도시까지 이동한 후 4리터의 기름을 넣고(4×2 = 8원) 제일 오른쪽 도시까지 이동하면, 총 비용은 18원이다.

각 도시에 있는 주유소의 기름 가격과, 각 도시를 연결하는 도로의 길이를 입력으로 받아 제일 왼쪽 도시에서 제일 오른쪽 도시로 이동하는 최소의 비용을 계산하는 프로그램을 작성하시오.

## 입력

표준 입력으로 다음 정보가 주어진다. 첫 번째 줄에는 도시의 개수를 나타내는 정수 N(2 ≤ N ≤ 100,000)이 주어진다. 다음 줄에는 인접한 두 도시를 연결하는 도로의 길이가 제일 왼쪽 도로부터 N-1개의 자연수로 주어진다. 다음 줄에는 주유소의 리터당 가격이 제일 왼쪽 도시부터 순서대로 N개의 자연수로 주어진다. 제일 왼쪽 도시부터 제일 오른쪽 도시까지의 거리는 1이상 1,000,000,000 이하의 자연수이다. 리터당 가격은 1 이상 1,000,000,000 이하의 자연수이다. 

## 출력

표준 출력으로 제일 왼쪽 도시에서 제일 오른쪽 도시로 가는 최소 비용을 출력한다. 

## 서브태스크

| 번호 | 배점 | 제한                                                         |
| :--- | :--- | :----------------------------------------------------------- |
| 1    | 17   | 모든 주유소의 리터당 가격은 1원이다.                         |
| 2    | 41   | 2 ≤ N ≤ 1,000, 제일 왼쪽 도시부터 제일 오른쪽 도시까지의 거리는 최대 10,000, 리터 당 가격은 최대 10,000이다. |
| 3    | 42   | 원래의 제약조건 이외에 아무 제약조건이 없다.                 |



### 풀이

> 서브태스크 2번에 보면 출력값이 int 데이터 범위를 넘기 때문에 long으로 선언 해야 한다.

```java
import java.util.Scanner;
public class Main {
	public static void main(String[] args) {
		
		Scanner sc = new Scanner(System.in); 
		//도시 수 입력
		int N = sc.nextInt();
		
		//길이 입력
		long[] cityLength = new long[N-1];
		for(int i = 0 ; i < N - 1 ; i++) {
			cityLength[i] = sc.nextInt();
		}
		
		//가격 입력
		long[] cost = new long[N];
		for(int i = 0 ; i < N ; i++) {
			cost[i] = sc.nextInt();
		}
		
		//최소 비용 계산
		long minCost = cost[0];
		long totalCost = 0;
		for(int i = 0 ; i < N - 1 ; i++) {
			if(minCost > cost[i]) {
				minCost = cost[i];
			}
			totalCost += minCost * cityLength[i];
		}
		
		System.out.println(totalCost);
	}	
}
```

