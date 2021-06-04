# 5. 반복문

#### 반복문은 실행문을 반복적으로 실행해야 할 때 사용 한다.

#### 반복문의 종류는 while문, do-while문, for문 이 있다.



### 1. while문

- 조건문의 실행 결과가 true일 동안 반복해서 실행한다.

```java
    while(조건문){
        실행문; 
    }
```

- 10번 반복하면서 0부터 9까지 출력하는 반복문

```java
    int i = 0;  //while에서 사용할 변수를 선언

    while(i < 10){
        System.out.println(i);
        i++; //조건문을 원하는 만큼만 반복하고 빠져나가기 위한 부분 
    }
```

- 1부터 100까지의 합을 while문을 이용하여 구현해 보도록 하겠습니다.

```java
    public class WhileExam2 {
        public static void main(String[] args) {
            int total = 0; // i의 값을 누적할 변수를 선언합니다.
            int i = 1;
            while(i <= 100){
                total = total + i;
                i++;
            }
        }
    }
```



### 2. do-while문

- while문의 경우 조건이 만족하지 않는다면 한번도 반복하지 않을 수 있다.하지만, do while문의 경우는 **무조건 한번은 실행**되는 반복문이다.

```java
    do{
        실행문;
    }while(조건문);
```

- do-while 실습

```java
    import java.util.Scanner;

    public class DoWhileExam {

        public static void main(String[] args) {
            int value = 0;

            // Scanner는 java.util 패키지에 있는 클래스로써 키보드로 부터 값을 입력받는다던지 할 때 유용하게 사용할 수 있는 클래스입니다.
            Scanner scan = new Scanner(System.in);
            //위 처럼 작성하시면 키보드로부터 값을 입력받을 수 있는 Scanner객체가 생성됩니다. 

            do{
                value = scan.nextInt(); // Scanner클래스를 이용하여 키보드로 부터 숫자값을 입력받습니다.
                System.out.println("입력받은 수 : " + value);  
            }while(value != 10);  // 입력받은 값이 10이 아닐 경우에는 계속 반복합니다.

            System.out.println("반복문 종료");
        }
    }
```



### 3. for 문

- for반복문은 변수초기화, 조건식, 증감식이 한줄에 모두 있다.
  1. 초기화식은 최초 한 번만 수행합니다.
  2. 조건식을 수행해서 수행결과가 false라면 for 반복문을 빠져 나갑니다.
  3. 수행 결과가 true라면 실행문을 수행한다.
  4. 증감식을 수행한다.
  5. 2번부터 4번까지 반복적으로 수행한다.

```java
    for(초기화식; 조건식; 증감식){
        실행문;
        실행문;
    }
```

- for문을 이용하여 1부터 100까지의 합을 구하는 프로그램

```java
    int total = 0; //1부터 100까지 합한 결과값을 담기위한 변수 선언 

    for(int i = 1; i <= 100; i++){ //1부터 100까지 반복하기 위한 for 반복문 

        total = total + i; // 1부터 100까지 반복해서 total 변수에 값을 누적  
    }
    System.out.println(total);  //결과값 출력 
```

- for문을 이용하여 1부터 100까지의 짝수의 합을 구하는 프로그램

```java
    public class ForExam {

        public static void main(String[] args) {
            int total = 0;
            for(int i = 1; i <= 100; i++){
                if(i % 2 != 0){  // 2로 나눈 나머지가 0이 아니라는것은 홀수를 의미한다.  
                    continue; // 홀수일 경우 total = total + i; 문장이 실행되지 않으므로, 결과적으로 짝수만 더해준다. 
                }
                total = total + i;
            }
            System.out.println(total);
        }

    }
```



### 이중배열

```java
String[][] users = {
				{"egoing", "1111"},
				{"Maeng", "2222"},
				{"lee", "3333"}
			};//00 01 10 11 20 21
		
		String inputId = args[0];
		String inputPass = args[1];
		
		boolean islogined = false;
		for(int i=0 ; i<users.length; i++) {
				String[] Currentusers = users[i];
				if(
					Currentusers[0].equals(inputId) && //users[i].equals(inputId); <--x
					Currentusers[1].equals(inputPass)
				) {
					islogined = true;
					break;
				}
		}
//		for(int i=0 ; i<users.length; i++) {
//			if(
//					users[i][0].equals(inputId) && 
//					users[i][1].equals(inputPass)
//				) {
//				islogined = true;
//				break;
//			}
//		}
```

위 코드는 2중배열(?)이기 때문에 users[0]는 두 개의 문자열을 가지고 있다. users[i].equals(inputId)라고 표현하면 inputId는 한 개의 문자열이기 때문에 동등 비교가 불가능하다. 그래서 주석과 같이 표현 해야 한다. 아래 코드는 한개기 때문에 가능.

```java
public static void main(String[] args) {
		
		String[] users = {"egoing","Maeng","lee"};
		
		String inputId = args[0];
		
		boolean isLogined = false;
		for(int i=0; i<users.length; i++) {
			if(users[i].equals(inputId)) 
			{	isLogined = true;
				break;
			}
		}
```

