# 4. 제어문

## 1. Boolean

지금까지 배운 데이터 타입은 string, character, int, float, ... 와 같은 특정한 값을 나타내는 것들이었음.

불리언 데이터 타입은 "참이냐 거짓이냐" 를 다루는 데이터 타입.

특정한 사건에서 특정한 조건이 부합하느냐, 부합하지 않느냐에 많이 쓰인다.

그래서 조건문과 반복문에서 많이 쓰임.

~일때, (true or false) -해당 문 실행.

- Boolean 타입과 관련된 메소드

'contain'

특정한 문자열이 들어가 있으면 true, 없으면 false를 출력

```java
String foo = "Hello World";
		
		System.out.println(foo.contains("World"));
-> 출력값 true
```



## 2. == vs equals

primitive(원시 데이터) 면 ==라 쓰고 아니라면 equals를 사용하자.

![image-20210423144449380](https://user-images.githubusercontent.com/80496345/116241010-6e791600-a79f-11eb-9d4f-4c9ec150d382.png)

왜냐하면 자바에서 ==은 같은 위치에 있는 지를 물어보는 동등비교연산자이다.

![image-20210423144556754](https://user-images.githubusercontent.com/80496345/116241012-6e791600-a79f-11eb-84f2-0899479ba584.png)

int p1 = 1

int p2 = 1 을 예시로 들어보자 자바에서는 같은 값을 가지는 변수는 같은 곳을 가리키고 있게 한다. 쉽게 말하면 메모리 어딘가에 1이라는 값이 넣어졌고 p1, p2모두 그 곳을 가리키고 있게 되는 것 이다. 원시 데이터 타입들은 모두 이런식으로 동작한다.

자바에서는,

String o1 ="java"

String o2 = new String("java"); 이 둘을 다르게 취급한다. 밑에 String은 자바라는 값을 가진 객체로 취급한다.

그리고 객체는 값이 같더라도 같은 위치에 존재하지 않게 된다. 그래서 o1 == o2 라고 하면 다른 위치에 있기 때문에 false라는 값이 출력 된다. 그래서 원시 데이터 타입이 아닌 객체들은 equals라는 메소드를 가진다.

따라서 원시 데이터 타입에는 동등 비교 연산자를 쓰면 되고 객체나 비원시데이터타입에는 equals를 쓰면 된다.

그러나, String의 경우 특혜를 받고 있다. new를 사용하지 않고 같은 값을 집어 넣었을 때 변수가 같은 곳을 가리킨다. 하지만, main 함수를 통해 입력 받은 임의 문자열 값을 동등 비교 연산자로 비교 했을 시, 입력 값을 똑같이 줬는데 false가 나오는 이유는 이는 내부적으로 입력 값이 다른 곳에 저장되었다는 뜻이다. 마치 원시 데이터 타입처럼 동작한다.





### 3. if 조건문

#### 조건식의 연산 결과에 따라 블록 내부 문장의 실행 여부를 결정 할 수 있다.

- if 문
  - 조건식이 true 일 경우에만 실행문이 실행된다.
  - if(조건식) 다음의 { } 를 생략할 수 있다. 하지만, 생략할 경우 if문에 포함되는 실행문은 단 한 줄만 포함된다.

```java
        if(조건식){
            실행문;
            실행문;
        }
```

- if - else 문
  - 조건식이 true일 경우 if 블록의 실행문이 실행되고, flase 일 경우 else 블록의 실행문이 실행된다.

```java
        if(조건식){
            실행문;
            실행문;
        }else{
            실행문;
        }
```

- if - else if - else문
  - 처음 if문의 조건식의 조건문이 true일 경우 처음 if문의 블록이 실행되고, false일 경우 다음 조건식의 결과에 따라 실행 블록이 달라진다.
  - else if 문의 수는 제한이 없다. 그러나 너무 많은 else if 문은 실행 속도를 느리게 한다.
  - 마지막 else 블록은 생략되도 상관없다.

```java
        if(조건식){
            실행문;
            실행문;
        }else if(조건식){
            실행문;
        }else{
            실행문;
        }
```



### 4. 논리 연산자

#### 논리연산자는 논리곱(&&,&) 논리합(||,|), 배타적 논리합 (^) 논리부정(!) 연산을 수행한다. 논리 연산자의 피연산자는 블린 타입만 사용할 수 있다. 결과는 불린값이다.

```
    boolean b1 = true;
    boolean b2 = false;
    boolean b3 = true;
```

- 논리곱 (&&, &) - 피연산자가 모두 true일 경우에만 연산 결과가 true 이다.
  - System.out.println(b1 && b2); -> b2가 false 이므로 결과는 false
  - System.out.println(b1 && b3); -> b1과 b2 모두 true 이므로 결과는 true
- 논리합 (||,|) - 피연산자 중 하나만 true이면 연산 결과는 true 이다.
  - System.out.println(b1 || b2); -> b1 이 true이므로 결과는 true 이다.
- 배타적 논리합 (^) -> 피연산자가 서로 다른 값일 경우만 연산 결과가 true 이다. (xor) <->xnor
  - System.out.println(b1 ^ b2); -> b1은 true, b2는 false로 서로 다르므로 결과는 true 이다.
  - System.out.println(b1 ^ b3); -> b1, b3 모두 true로 서로 같다. 결과는false 이다
- 논리 부정 (!) -> 피연산자의 논리값을 바꾼다. true는 false로 false는 true로 바꾼다.
  - System.out.println(!b1); -> b1 이 true 이므로 결과는 false 이다.
  - System.out.println(!b2); -> b1 이 false 이므로 결과는 true 이다.



### 5. 삼항 연산자

- 조건식 ? 피연산자1 : 피연산자2

  - 조건식의 연산결과가 true 이면, 결과는 피연산자 1이고, 조건식의 연산결과가 false 이면 결과는 피연산자2

  ```java
          int b1 = (5>4) ? 50 : 40;
          //조건식이 true이므로 b1은 50이 된다. 
  ```

  - 피연산자1, 피연산자2 에는 주로 값이 오지만, 경우에 따라 연산식이 올 수 있다.
  - 삼항 연산자가 익숙하지 않다면, if문으로 바꾸어 이용해도 좋다.

```java
            int b2 = 0;
            if(5 > 4){
                b2 = 50;
            }else{
                b2 = 40;
            }
```



## 6. switch 문

#### switch문은 어떤 변수의 값에 따라서 문장을 실행할 수 있도록 하는 제어문이다.

- switch문에서 사용하는 키워드는 switch, case, default, break 이다.
- switch문

```java
    switch(변수){
        case 값1 : 
            실행문; 
            break;
        case 값2 : 
            실행문; 
            break;  
        default;    
    }
```

```java
int value = 1;

    switch(value){
        case 1: 
            System.out.println("1");
            break;
        case 2:
            System.out.println("2");
            break;
        case 3 :
            System.out.println("3");
            break;
        default :
            System.out.println("그 외의 숫자");
    }
```

value의 값이 1일 경우 1을 출력하고, 2일 경우는 2를 출력하고, 3일 경우는 3을 출력하고, 그 외에는 그 외의 숫자가 출력된다.

```java
    case 1: 
        System.out.println("1");
    case 2:
        System.out.println("2");
    case 3 :
        System.out.println("3");
    default :
        System.out.println("그 외의 숫자");
```

break를 제거하면 value가 1일 경우 1일 출력되고 switch문장을 빠져나가는 것이 아니라
1,2,3, 그외의숫자가 연속해서 실행된다. break문장이 있을 경우와 없을 경우를 확실하게 구분할 수 있어야 합니다.



### 참고 하세요

JDK7이전에는 switch다음 괄호안에 정수타입의 변수만 올 수 있었습니다. 그런데 JDK7부터는 switch다음 괄호안에 문자열 타입의 변수도 올 수 있습니다.

```java
    String str = "A";

    switch(str){
        case "A": 
            System.out.println("1");
        case "B":
            System.out.println("2");
        case "C" :
            System.out.println("3");
        default :
            System.out.println("그 외의 숫자");
    }
```

문자열의 값에 따라서 case블록의 내용이 출력되는 것을 알 수 있습니다.