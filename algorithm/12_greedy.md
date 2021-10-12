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

#### 자바 배열 / 객체 정렬 (comparable, comparator)(https://st-lab.tistory.com/243)



### comparator 사용법

> 하지만 뺄셈을 사용하게 되면 overflow나 underflow가 발생할수있다. (주의)

```java
Collections.sort(list,new Comparator<Person>() { 
    @Override 
    public int compare(Person o1, Person o2) { 
        //오름차순 정렬 
        //음수, 0이 나오면 그대로
        //양수가 나오면 바꾼다.
        if(o1.getNo()<o2.getNo()) { 
            //1,2,3 
            return -1; 
        } else if(o1.getNo()>o2.getNo()){ 
            return 1; 
        } else { return 0; }  
    } 
});
    //그래서 오름차순은 이렇게 나타낼 수 있다. 
    //return o1-o2;
	//양수면 o1이 더 크므로 o1이랑 o2랑 자리를 바꾼다. 큰게 뒤로간다.
    //내림차순으로 하고 싶으면
    //return o2-o1; 
    //양의 값이 나오면 바꾼다고 했으므로 o1이랑 o2랑 자리를 바꾼다. 큰게 앞으로 간다.
```



```
Scanner sc = new Scanner(System.in); 
		//식 입력
		String equation = sc.next();
		
		String[] equations = equation.split("-");
		
		int result = Integer.parseInt(equations[0]);
		for(int i = 1; i < equations.length; i++) {
			result -= Integer.parseInt(equations[i]);
		}
		System.out.println(result);
	}
```



# 11. 잃어버린 괄호

## 문제

세준이는 양수와 +, -, 그리고 괄호를 가지고 식을 만들었다. 그리고 나서 세준이는 괄호를 모두 지웠다.

그리고 나서 세준이는 괄호를 적절히 쳐서 이 식의 값을 최소로 만들려고 한다.

괄호를 적절히 쳐서 이 식의 값을 최소로 만드는 프로그램을 작성하시오.

## 입력

첫째 줄에 식이 주어진다. 식은 ‘0’~‘9’, ‘+’, 그리고 ‘-’만으로 이루어져 있고, 가장 처음과 마지막 문자는 숫자이다. 그리고 연속해서 두 개 이상의 연산자가 나타나지 않고, 5자리보다 많이 연속되는 숫자는 없다. 수는 0으로 시작할 수 있다. 입력으로 주어지는 식의 길이는 50보다 작거나 같다.

## 출력

첫째 줄에 정답을 출력한다.

## 풀이

```java
package algorithm;

import java.util.Arrays;
import java.util.Comparator;
import java.util.Scanner;
public class Main {
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in); 
		//식 입력
		String equation = sc.next();
		
		//-로 분리
		String[] sub = equation.split("-");
		
		//초기값은 더해야하는데 max_value로 선언해야 뺼셈하면서 이 값이 나올 경우가 존재하지 않는다.
		int result = Integer.MAX_VALUE;
		
		//덧셈하여 최소값 구하기
		for(int i = 0 ; i < sub.length ; i++) {
			//+로 분리
			String[] add = sub[i].split("\\+");
			
            //덧셈
			int temp = 0;
			for(int j = 0 ; j < add.length ; j++) {
				temp += Integer.parseInt(add[j]);
			}
			
            //뺄셈
			if(result == Integer.MAX_VALUE) {
				result = temp;
			} else {
				result -= temp;
			}
		}
		System.out.println(result);
	}
}
```





# 12. 블로그2

## 문제

neighbor 블로그를 운영하는 일우는 매일 아침 풀고 싶은 문제를 미리 정해놓고 글을 올린다. 그리고 매일 밤 각각의 문제에 대하여, 해결한 경우 파란색, 해결하지 못한 경우 빨간색으로 칠한다. 일우는 각 문제를 칠할 때 아래와 같은 과정을 한 번의 작업으로 수행한다.

1. 연속된 임의의 문제들을 선택한다.
2. 선택된 문제들을 전부 원하는 같은 색으로 칠한다.

![img](https://upload.acmicpc.net/72fda166-5e2c-42b4-a9c1-e52993a5c45e/-/preview/)

예를 들어, 각 문제를 위와 같은 색으로 칠하려고 할 때, 1~2번 문제를 파란색, 3번을 빨간색, 4번을 파란색, 5번을 빨간색, 6~7번을 파란색, 8번을 빨간색으로 칠하는 작업을 순서대로 수행하면 6번의 작업을 거쳐야 한다. 하지만, 1~7번 문제를 파란색, 3번을 빨간색, 5번을 빨간색, 8번을 빨간색으로 순서대로 칠한다면 작업 횟수는 4번으로 가장 적다.

일우는 매일 500,000문제까지 시도하기 때문에, 이 작업이 꽤나 귀찮아지기 시작했다. 그래서 가장 효율적인 방법으로 위 작업을 수행하기를 원한다. 일우를 도와 각 문제를 주어진 색으로 칠할 때 필요한 최소한의 작업 횟수를 구하는 프로그램을 작성하라.

## 입력

첫째 줄에 색을 칠해야 하는 문제의 수 *N* (1 ≤ *N* ≤ 500,000)이 주어진다.

둘째 줄에 *N*개의 문자가 공백 없이 순서대로 주어진다. 각 문자는 *i*번째 문제를 어떤 색으로 칠해야 하는지를 의미하며, `R`은 빨간색, `B`는 파란색을 나타낸다. 그 외에 다른 문자는 주어지지 않는다.

## 출력

첫째 줄에 일우가 주어진 모든 문제를 원하는 색으로 칠할 때까지 필요한 작업 횟수의 최솟값을 출력하라.

## 풀이

```java
import java.util.Scanner;
public class Main {
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in); 
		//입력
		int N = sc.nextInt();
		String s = sc.next();
		int B = 0;
        int R = 0;

        for (int i = 0; i < N; i++) {
            char c = s.charAt(i);
            if (c == 'R') {
                R++;
                while(i + 1 < N) {
                    if (s.charAt(i + 1) == 'B') break;
                    i++;
                }
            } else {
                B++;
                while (i + 1 < N) {
                    if (s.charAt(i + 1) == 'R') break;
                    i++;
                }
            }
        }

        System.out.println(Math.min(R, B) + 1);
	}
}
```



# 13. 동전 0

## 문제

준규가 가지고 있는 동전은 총 N종류이고, 각각의 동전을 매우 많이 가지고 있다.

동전을 적절히 사용해서 그 가치의 합을 K로 만들려고 한다. 이때 필요한 동전 개수의 최솟값을 구하는 프로그램을 작성하시오.

## 입력

첫째 줄에 N과 K가 주어진다. (1 ≤ N ≤ 10, 1 ≤ K ≤ 100,000,000)

둘째 줄부터 N개의 줄에 동전의 가치 Ai가 오름차순으로 주어진다. (1 ≤ Ai ≤ 1,000,000, A1 = 1, i ≥ 2인 경우에 Ai는 Ai-1의 배수)

## 출력

첫째 줄에 K원을 만드는데 필요한 동전 개수의 최솟값을 출력한다.



## 풀이

```java
import java.util.Scanner;
public class Main {
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in); 
		//입력
		int N = sc.nextInt();
		int K = sc.nextInt();
		int[] A = new int[N];
		for(int i = 0 ; i < N ; i++) {
			A[i] = sc.nextInt();
		}
		
		int count = 0;
		for(int i = N-1 ; i >= 0 ; i--) {
			count += K/A[i];
			K %= A[i];
		}
		
        System.out.println(count);
	}
}
```



# 14. 민겸 수

## 문제

민겸이는 로마 숫자를 보고 굉장히 흥미롭다고 생각했다. 그래서 민겸이는 새로운 수 체계인 민겸 수를 창조했다.

민겸 숫자는 0 이상의 정수 *N*에 대해 10*N* 또는 5 × 10*N* 꼴의 십진수를 대문자 `M`과 `K`로 이루어진 문자열로 표기한다. 10*N* 꼴의 십진수는 *N* + 1개의 `M`으로, 5 × 10*N* 꼴의 십진수는 *N*개의 `M` 뒤에 1개의 `K`를 이어붙인 문자열로 나타낸다. 즉, 아래 표처럼 나타낼 수 있다.

| 변환 전 | 변환 후 |
| ------- | ------- |
| `1`     | `M`     |
| `5`     | `K`     |
| `10`    | `MM`    |
| `50`    | `MK`    |
| `100`   | `MMM`   |
| `500`   | `MMK`   |
| `1000`  | `MMMM`  |
| `5000`  | `MMMK`  |
| `...`   | `...`   |

민겸 수는 한 개 이상의 민겸 숫자를 이어붙여 만든다. 예를 들어, 민겸 수 `MKKMMK`는 `MK`, `K`, `MMK`의 세 민겸 숫자를 이어붙여 만들 수 있다.

민겸 수를 십진수로 변환할 때는, 1개 이상의 민겸 숫자로 문자열을 분리한 뒤, 각각의 민겸 숫자를 십진수로 변환해서 순서대로 이어붙이면 된다. 민겸 숫자를 십진수로 변환하는 것은 십진수를 민겸 숫자로 변환하는 과정을 거꾸로 하면 된다. 예를 들어, 민겸 수 `MKKMMK`는 아래 그림과 같이 여러 가지 십진수로 변환할 수 있다.

![img](https://upload.acmicpc.net/3a65029c-5253-4600-8d93-908e4f368161/-/preview/)

민겸이는 위와 같이 하나의 민겸 수가 다양한 십진수로 변환될 수 있다는 사실을 알았다. 문득 민겸이는 변환될 수 있는 십진수 중 가장 큰 값과 가장 작은 값이 궁금해졌다. 민겸이를 위해 하나의 민겸 수가 십진수로 변환되었을 때 가질 수 있는 최댓값과 최솟값을 구해주자.

## 입력

민겸 수 하나가 주어진다. 민겸 수는 대문자 `M`과 `K`로만 이루어진 문자열이며, 길이는 3,000을 넘지 않는다.

## 출력

주어진 민겸 수가 십진수로 변환되었을 때 가질 수 있는 값 중 가장 큰 값과 가장 작은 값을 두 줄로 나누어 출력한다.

 ## 풀이

```java
import java.util.Scanner;
public class Main {
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in); 
		//입력
		String s = sc.next();

		String min = "";
		String max = "";
		int count = 0;
		for(int i = 0 ; i < s.length() ; i++) {
			char c = s.charAt(i);
			
			if(c == 'M') {
				if(count==0) {
					min += "1";
				} else {
					min += "0";
				}
				count++;
			} else {
				min += "5";
				max += "5";
				if(count != 0) {
					for(int j = 0; j < count ; j++) {
						max += "0";
					}
				}
				count = 0;
			}
		}
		if(count != 0) {
			for(int i = 0; i < count ; i++) {
				max += "1";
			}
		}
		
		System.out.println(max);
		System.out.println(min);
	}
}
```





# 15. A → B

## 문제

정수 A를 B로 바꾸려고 한다. 가능한 연산은 다음과 같은 두 가지이다.

- 2를 곱한다.
- 1을 수의 가장 오른쪽에 추가한다. 

A를 B로 바꾸는데 필요한 연산의 최솟값을 구해보자.

## 입력

첫째 줄에 A, B (1 ≤ A < B ≤ 109)가 주어진다.

## 출력

A를 B로 바꾸는데 필요한 연산의 최솟값에 1을 더한 값을 출력한다. 만들 수 없는 경우에는 -1을 출력한다.

## 풀이

```java
import java.util.Scanner;
public class Main {
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in); 
		//입력
		int a = sc.nextInt();
		int b = sc.nextInt();
		int count = 1;
		while(a < b) {
			if(b%10 == 1) {
				b = b/10;
				count++;
			} else if(b%2 == 0) {
				b = b/2;
				count++;
			} else {
				break;
			}
		}
		if(a==b) {
			System.out.println(count);	
		} else {
			System.out.println(-1);
		}
		sc.close();
	}
}
```



# 16. 강의실 배정

## 문제

수강신청의 마스터 김종혜 선생님에게 새로운 과제가 주어졌다. 

김종혜 선생님한테는 Si에 시작해서 Ti에 끝나는 N개의 수업이 주어지는데, 최소의 강의실을 사용해서 모든 수업을 가능하게 해야 한다. 

참고로, 수업이 끝난 직후에 다음 수업을 시작할 수 있다. (즉, Ti ≤ Sj 일 경우 i 수업과 j 수업은 같이 들을 수 있다.)

수강신청 대충한 게 찔리면, 선생님을 도와드리자!

## 입력

첫 번째 줄에 N이 주어진다. (1 ≤ N ≤ 200,000)

이후 N개의 줄에 Si, Ti가 주어진다. (0 ≤ Si < Ti ≤ 109)

## 출력

강의실의 개수를 출력하라.

## 풀이

> 우선순위 큐를 이용하면 자동으로 정렬(지금은 오름차순으로 선언해서 오름차순으로)해준다. 그래서 peek값(우선순위가 가장 높은값)에 자동적으로 제일 작은 값이 들어오게 되고 그에 따라 peek값보다 같거나 큰값이 들어온다면 원래의 peek값을 빼고 들어온 값을 넣어준 뒤 pq에 있는 최소값이 새로운 peek값이 된다. 아니라면 강의실 갯수를 추가시켜준다.

```java
import java.util.Arrays;
import java.util.Comparator;
import java.util.PriorityQueue;
import java.util.Scanner;
public class Main {
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in); 
		//입력
		int N = sc.nextInt();
		int[][] times = new int[N][2];
		for(int i = 0 ; i < N ; i++) {
			times[i][0] = sc.nextInt();
			times[i][1] = sc.nextInt();
		}
		//입력 데이터를 오름차순으로 정렬(시작 시간이 같다면, 끝나느 시간을 오름차순으로)
		Arrays.sort(times, new Comparator<int[]>() {

			@Override
			public int compare(int[] o1, int[] o2) {
				if(o1[0] == o2[0]) return o1[1] - o2[1];
				return o1[0]-o2[0];
			}	
		});
		//우선순위 큐를 선언해주고 배열의 첫번째 종료시간을 큐에 넣는다.
		PriorityQueue<Integer> pq = new PriorityQueue<Integer>();
		pq.add(times[0][1]);
		//배열을 두 번째 값부터 순회하면서
		for(int i = 1 ; i < N ; i++) {
			//start가 peek()값보다 작거나 같다면, pq에서 하나 뺀다
			if(pq.peek() <= times[i][0]) {
				pq.poll(); //값을 제거할 시 우선순위가 가장 높은 값이 제거된다.
			}
			//순회하면서 현재 end값을 새로 pq에 넣는다.
			pq.add(times[i][1]);
		}
		//pq에 남아있는 데이터의 갯수가 강의실의 갯수이다.
		System.out.println(pq.size());
		sc.close();
	}
}
```



