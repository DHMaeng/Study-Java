# 1. 설탕 배달

## 문제

상근이는 요즘 설탕공장에서 설탕을 배달하고 있다. 상근이는 지금 사탕가게에 설탕을 정확하게 N킬로그램을 배달해야 한다. 설탕공장에서 만드는 설탕은 봉지에 담겨져 있다. 봉지는 3킬로그램 봉지와 5킬로그램 봉지가 있다.

상근이는 귀찮기 때문에, 최대한 적은 봉지를 들고 가려고 한다. 예를 들어, 18킬로그램 설탕을 배달해야 할 때, 3킬로그램 봉지 6개를 가져가도 되지만, 5킬로그램 3개와 3킬로그램 1개를 배달하면, 더 적은 개수의 봉지를 배달할 수 있다.

상근이가 설탕을 정확하게 N킬로그램 배달해야 할 때, 봉지 몇 개를 가져가면 되는지 그 수를 구하는 프로그램을 작성하시오.

## 입력

첫째 줄에 N이 주어진다. (3 ≤ N ≤ 5000)

## 출력

상근이가 배달하는 봉지의 최소 개수를 출력한다. 만약, 정확하게 N킬로그램을 만들 수 없다면 -1을 출력한다.



## 풀이 1

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



## 풀이 2

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



## 풀이

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



## 풀이 1

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



## 풀이2

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



## 풀이

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



## 풀이

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



## 풀이

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



# 7. 알바생 강호

## 문제

스타박스는 손님을 입장시킬 때 독특한 방법으로 입장시킨다.

스타박스에서는 손님을 8시가 될 때 까지, 문앞에 줄 세워 놓는다. 그리고 8시가 되는 순간 손님들은 모두 입구에서 커피를 하나씩 받고, 자리로 간다. 강호는 입구에서 커피를 하나씩 주는 역할을 한다.

손님들은 입구에 들어갈 때, 강호에게 팁을 준다. 손님들은 자기가 커피를 몇 번째 받는지에 따라 팁을 다른 액수로 강호에게 준다. 각 손님은 강호에게 원래 주려고 생각했던 돈 - (받은 등수 - 1) 만큼의 팁을 강호에게 준다. 만약, 위의 식으로 나온 값이 음수라면, 강호는 팁을 받을 수 없다.

예를 들어, 민호는 팁을 3원 주려고 했고, 재필이는 팁을 2원, 주현이가 팁을 1원 주려고 한 경우를 생각해보자.

민호, 재필, 주현이 순서대로 줄을 서있다면, 민호는 강호에게 3-(1-1) = 3원, 재필이는 2-(2-1) = 1원, 주현이는 1-(3-1) = -1원을 팁으로 주게 된다. 주현이는 음수이기 때문에, 강호에게 팁을 주지 않는다. 따라서, 강호는 팁을 3+1+0=4원을 받게 된다.

스타박스 앞에 있는 사람의 수 N과, 각 사람이 주려고 생각하는 팁이 주어질 때, 손님의 순서를 적절히 바꿨을 때, 강호가 받을 수 잇는 팁의 최댓값을 구하는 프로그램을 작성하시오.

## 입력

첫째 줄에 스타박스 앞에 서 있는 사람의 수 N이 주어진다. N은 100,000보다 작거나 같은 자연수이다. 둘째 줄부터 총 N개의 줄에 각 사람이 주려고 하는 팁이 주어진다. 팁은 100,000보다 작거나 같은 자연수이다.

## 출력

강호가 받을 수 있는 팁의 최댓값을 출력한다.



## 풀이

> 내림차순 할때 collections.reverseOrder()을 사용하기 때문에 객체인 Integer[]을 사용해야한다. 
>
> 팁들의 합 최대값이 int에 담을수 없기 때문에 long형 사용해야함

```java
import java.util.Arrays;
import java.util.Collections;
import java.util.Scanner;
public class Main {
	public static void main(String[] args) {
		
		Scanner sc = new Scanner(System.in); 
		//사람 수 입력
		int N = sc.nextInt();
		
		//팁 입력
		Integer[] tips = new Integer[N];
		for(int i = 0 ; i < N ; i++) {
			tips[i] = sc.nextInt();
		}
		
		Arrays.sort(tips, Collections.reverseOrder());
		
		//팁 계산
		long totalTip = 0;
		for(int i = 0 ; i < N ; i++) {
			if(tips[i]-i <= 0) {
				break;
			}
			totalTip += tips[i] - i ;
		}
		
		System.out.println(totalTip);
	}	
}
```





# 8. 2+1 세일

| 시간 제한 | 메모리 제한 | 제출 | 정답 | 맞은 사람 | 정답 비율 |
| :-------- | :---------- | :--- | :--- | :-------- | :-------- |
| 1 초      | 64 MB       | 2424 | 1387 | 1160      | 59.093%   |

## 문제

KSG 편의점에서는 과일우유, 드링킹요구르트 등의 유제품을 '2+1 세일'하는 행사를 하고 있습니다. KSG 편의점에서 유제품 3개를 한 번에 산다면 그중에서 가장 싼 것은 무료로 지불하고 나머지 두 개의 제품 가격만 지불하면 됩니다. 한 번에 3개의 유제품을 사지 않는다면 할인 없이 정가를 지불해야 합니다.

예를 들어, 7개의 유제품이 있어서 각 제품의 가격이 10, 9, 4, 2, 6, 4, 3이고 재현이가 (10, 3, 2), (4, 6, 4), (9)로 총 3번에 걸쳐서 물건을 산다면 첫 번째 꾸러미에서는 13원을, 두 번째 꾸러미에서는 10원을, 세 번째 꾸러미에서는 9원을 지불해야 합니다.

재현이는 KSG 편의점에서 친구들과 같이 먹을 총 N팩의 유제품을 구입하려고 합니다. 재현이를 도와 최소비용으로 유제품을 구입할 수 있도록 도와주세요!

## 입력

첫 번째 줄에는 유제품의 수 N (1 ≤ N ≤ 100,000)이 주어집니다.

두 번째 줄부터 N개의 줄에는 각 유제품의 가격 Ci (1 ≤ Ci ≤ 100,000)가 주어집니다.

## 출력

재현이가 N개의 유제품을 모두 살 때 필요한 최소비용을 출력합니다. 정답은 2^31-1보다 작거나 같다.



## 풀이

```java
import java.util.Arrays;
import java.util.Collections;
import java.util.Scanner;
public class Main {
	public static void main(String[] args) {
		
		Scanner sc = new Scanner(System.in); 
		//물건 수 입력
		int N = sc.nextInt();
		
		//가격 입력
		Integer[] cost = new Integer[N];
		for(int i = 0 ; i < N ; i++) {
			cost[i] = sc.nextInt();
		}
		
		Arrays.sort(cost, Collections.reverseOrder());
		
		//팁 계산
		int totalCost = 0;
		for(int i = 0 ; i < N ; i++) {
			if((i+1)%3 != 0) {
				totalCost += cost[i];
			}
		}
		
		System.out.println(totalCost);
	}	
}

```





# 9. 서강근육맨

## 문제

로니 콜먼 동영상을 보고 보디빌더가 되기로 결심한 향빈이는 PT 상담을 받으러 서강헬스클럽에 갔다. 향빈이가 서강헬스클럽을 선택한 이유는 PT를 받을 때 사용하는 운동기구를 회원이 선택할 수 있다는 점 때문이다. 하지만, 서강헬스클럽은 항상 사람이 많아서 PT를 한 번 받을 때 운동기구를 최대 두 개까지만 선택할 수 있다.

헬스장에 있는 N개의 운동기구를 한 번씩 사용해보고 싶은 향빈이는 PT를 받을 때마다 이전에 사용하지 않았던 운동기구를 선택하기로 계획을 세웠다. 그리고 비용을 절약하기 위해 PT를 받을 때 운동기구를 되도록이면 두 개를 사용하기로 했다. 예를 들어, 헬스장에 총 10개의 운동기구가 있을 경우 PT를 5번 받으면 모든 기구를 다 사용할 수 있다. 9개의 운동기구가 있는 경우에도 PT를 5번 받지만, 마지막 PT를 받을 때는 운동기구를 하나만 사용한다.

하지만 향빈이는 운동기구를 선택하다가 큰 고민에 빠졌다. 왜냐하면 운동기구마다 근손실이 일어나는 정도가 다르기 때문이다. 어떤 운동기구는 자극이 잘 안 와서 근손실이 적게 일어나는데, 어떤 운동기구는 자극이 잘 와서 근손실이 많이 일어난다. 근손실이 죽음보다 무서운 향빈이는 PT를 한 번 받을 때의 근손실 정도가 M을 넘지 않도록 하고 싶다. 이때, M의 최솟값을 구해보자. 참고로, 운동기구를 두 개 사용해서 PT를 받을 때의 근손실 정도는 두 운동기구의 근손실 정도의 합이다.

## 입력

첫째 줄에 서강헬스클럽에 비치된 운동기구의 개수를 나타내는 정수 N이 주어진다. (1≤N≤10 000)

둘째 줄에는 각 운동기구의 근손실 정도를 나타내는 정수 t1,t2,⋯,tN가 주어진다. (0≤ti≤10^18)

## 출력

 M의 최솟값을 출력한다.



## 풀이

> max값을 구할때는 maximum = Math.max(maximum, 비교값)을 이용하자

```java
import java.math.*;
import java.util.Arrays;
import java.util.Scanner;
public class Main {
	public static void main(String[] args) {
		
		Scanner sc = new Scanner(System.in); 
		//기구 수 입력
		int N = sc.nextInt();
		
		//근손실 정도 입력
		long[] loss = new long[N];
		for(int i = 0 ; i < N ; i++) {
			loss[i] = sc.nextLong();
		}
		
		Arrays.sort(loss);
		
		//최소값 계산
		long min = 0;
		if(N%2 == 0) {
			for(int i = 0 ; i < N/2 ; i++) {
				if(min < loss[i] + loss[N-(i+1)]) {
					min = loss[i] + loss[N-(i+1)];
				}
				//maxnum = Math.max(maxnum,weight[i]+weight[n-1-i]);
			}
		} else {
			min = loss[N-1];
			for(int i = 0 ; i < N/2 ; i++) {
				if(min < loss[i] + loss[N-(i+2)]) {
					min = loss[i] + loss[N-(i+2)];
				}
			}
		}
		System.out.println(min);
	}	
}
```




# 10. 회의실 배정

## 문제

한 개의 회의실이 있는데 이를 사용하고자 하는 N개의 회의에 대하여 회의실 사용표를 만들려고 한다. 각 회의 I에 대해 시작시간과 끝나는 시간이 주어져 있고, 각 회의가 겹치지 않게 하면서 회의실을 사용할 수 있는 회의의 최대 개수를 찾아보자. 단, 회의는 한번 시작하면 중간에 중단될 수 없으며 한 회의가 끝나는 것과 동시에 다음 회의가 시작될 수 있다. 회의의 시작시간과 끝나는 시간이 같을 수도 있다. 이 경우에는 시작하자마자 끝나는 것으로 생각하면 된다.

## 입력

첫째 줄에 회의의 수 N(1 ≤ N ≤ 100,000)이 주어진다. 둘째 줄부터 N+1 줄까지 각 회의의 정보가 주어지는데 이것은 공백을 사이에 두고 회의의 시작시간과 끝나는 시간이 주어진다. 시작 시간과 끝나는 시간은 231-1보다 작거나 같은 자연수 또는 0이다.

## 출력

첫째 줄에 최대 사용할 수 있는 회의의 최대 개수를 출력한다.



## 풀이

```java
package algorithm;

import java.util.Arrays;
import java.util.Comparator;
import java.util.Scanner;
public class Main {
	public static void main(String[] args) {
		
		Scanner sc = new Scanner(System.in); 
		//회의 수 입력
		int N = sc.nextInt();
		
		//회의 시간 입력
		int[][] time = new int[N][2];
		for(int i = 0 ; i < N ; i++) {
			time[i][0] = sc.nextInt();
			time[i][1] = sc.nextInt();
		}
		
		//끝나는 시간을 기준으로 정렬하기 위해 compare 재정의 
		Arrays.sort(time, new Comparator<int[]>() {
			
			@Override
			public int compare(int[] o1, int[] o2) {
				
				// 종료시간이 같을 경우 시작시간이 빠른순으로 정렬해야한다.  
				if(o1[1] == o2[1]) {
					return o1[0] - o2[0];
				}
				return o1[1] - o2[1];
			}
 
		});
		
		int count = 0;
		int prev_end_time = 0;
		
		for(int i = 0; i < N; i++) {
			
			// 직전 종료시간이 다음 회의 시작 시간보다 작거나 같다면 갱신 
			if(prev_end_time <= time[i][0]) {
				prev_end_time = time[i][1];
				count++;
			}
		}
		System.out.println(count);
	}
}
```

#### 왜 종료시간을 기준으로 정렬을 해야할까?  : https://st-lab.tistory.com/145

#### 자바 배열 / 객체 정렬 (comparable, comparator)(https://junlab.tistory.com/236)
