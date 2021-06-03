# 3. 연산자

> 연산자 : 데이터를 처리하여 결과를 산출하는 것





## 산술연산자

#### 부호(+,-), 증감(++,--), +,-,*,/,%

- 연산식  **x = y + z;**

  - y와 z를 더한 값을 x에 대입한다는 것을 의미
  - =과 + 는 연산자 = 은 대입연산자 이고, + 산술연산자 이다.
  - y와 z 는 피연산자 이다.
  - x = y+ z 는 연산식이다.

- 부호를 결정하는 부호 연산자

- 산술 연산을 할 수 있는 산술 연산자

- 1씩 증가하거나 감소 시키는 증감연산자

- 피 연산자가 1개인 연산자는 단항 연산자

  - 부호 연산자와, 증감연산자는 단항 연산자 이다.

- 피연산자의 갯수는? 2개(이항연산자)

  1. x=x+1 을 간략하게

     x+=1;

     x++;

  2. x = 10일때

     x++? 11

     ++x? 나중에 11

```java
    //부호 연산자 
    int i1 = -5;  //-5
    int i2 = +i1; //-5
    int i3 = -i1; //5

    //증감 연산자 
    int i4 = ++i3; //i4==i3+1
    int i5 = i3++; //i5==i3
    int i6 = --i3; //i6==i3-1
    int i7 = i3--; //i7==i3
```

- 피연 산자 하나로 연산할 수 없는 연산자 이항 연산자

```java
    int i = 5;
    int j = 2;  
```

- 2개의 변수 이용한 산술 연산

```java
    System.out.println(i +  j);
    System.out.println(i -  j);
    System.out.println(i *  j);
    System.out.println(i /  j);  
    System.out.println(i %  j);  
```



## 비교연산자

#### == , != , < , > , <= , >=

- 비교 연산자의 결과는 boolean이다.

```java
    int i = 10; // = 대입연산자 
    int j = 10;    

    // i 와 j 가 같은지 비교 하는 비교 연산자           
    System.out.println(i == j ) 
    System.out.println(i == j ) 
    System.out.println(i != j );
    System.out.println(i < j);
    System.out.println( i <= j);
    System.out.println(i > j);
    System.out.println(i >= j);
```

- 단순 대입 연산자
  - i = 10
  - 오른쪽에 있는 피연산자의 값을 왼쪽 피연산자의 변수에 저장
- 복합 대입 연산자
  - 정해진 연산을 수행한 후에 결과를 대입

```java
    i += 10; // i = i + 10;  과 같은 의미 

    System.out.println(i);  
    System.out.println(i -=5);
    System.out.println(i);
```



## 연산자 우선순위

- 최우선연산자 ( ., [], () )
- 단항연산자 ( ++,--,!,~,+/-  : 부정, bit변환>부호>증감)
- 산술연산자 ( *,/,%,+,-,shift) < 시프트연산자 ( >>,<<,>>> ) >
- 비교연산자 ( >,<,>=,<=,==,!= )
- 비트연산자 ( &,|,,~ )
- 논리연산자 (&& , || , !)
- 삼항연산자 (조건식) ? :
- 대입연산자 =,*=,/=,%=,+=,-=

```java
    int a = 5;
    int b = 10;
    int c = 5;
    System.out.println(  a - b * c );
    //결과는 -45가 나오게 됩니다
```

- 곱셈이 우선순위가 높기 때문에 b와c를 먼저 곱한다. 그런 다음 a에서 b와 c를 곱한 값을 뺀다.



- 비교연산자가 논리 연산자 보다 우선순위가 높다.

```java
 	int a = 5;
    int b = 10;
    int c = 5;
    System.out.println(a > 5 && b > 5); //false
    System.out.println(a > 5 || b > 5); //ture    
```



- 단 증감 연산자일 경우에 전위 연산자인지 후위 연산자 인지에 따라서 우선 순위가 바뀔 수 있다.

```java
            int a = 5; 
            System.out.println(++a - 5); 
            //결과는 1 
```

- 단항 연산자이면서, 전위 연산자인 ++ 가 먼저 연산된다. a가 6으로 바뀐 후 5 를 빼게 되므로 결과는 1

```java
        int a = 5; 
        System.out.println(a++ - 5); 
        //결과는 0
        System.out.println(a); 
        //결과는 6
```

- 단항 연산자이면서, 후위 연산자인 ++ 가 나중에 연산된다. a가 5인 상태에서 5를 뺀 후에 a++(a=a+1) 이 실행되므로 출력결과는 0



#### 논리연산자 중 and 연산과 or 연산이 나왔을 경우 and 연산이 먼저 수행 됩니다.