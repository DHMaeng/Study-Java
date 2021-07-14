# 6. 배열 및 열거

- 배열 사용 이유?

  같은 타입의 많은 양의 데이터를 집합으로 다뤄 효율적인 방법으로 사용하기 위함.

- 배열 선언 방법

  ```java
  데이터타입[] 변수;
  int[] scores;
  데이터타입 변수[];
  int scores[];
  ```

- 배열에 값을 할당하고 변경하는 방법

  ```java
  1-1) 배열변수 선언과 함께 값을 넣을 경우
  데이터타입[] 변수 = (값1, 값2, 값3, ...};
  int[] scores = {90, 100, 80};
  
  1-2) 
  데이터타입[] 변수;
  변수 = new 데이터타입[] {값1, 값2, 값3, ...};
  int[] scores;
  scores = new int[] {90, 100, 80};
  
  **메서드 매개값을 보낼때도 이렇게 해야한다.**
  int add(int[] scores) {...}
  //-------------------------
  int result = add( {95, 85, 90} ); //error
  int result = add(new int[] {95, 85, 90} ); 
  
  2) 배열변수를 미리선언하고 값이 나중에 결정될때
  데이터타입[] 변수 = new 데이터타입[길이];
  int[] scores = new int[3];
  변수[인덱스] = {값};
  scores[0] = {95};
  scores[1] = {85};
  scores[2] = {90};
  ```

- 배열 초기값

  ```java
  int[] scores = new int[30]; //0으로 초기화
  String[] names = new String[30]; //null로 초기화
  ```

  ![Java 배열(Array)](https://t1.daumcdn.net/cfile/tistory/276E184F59412E3024)

  u0000 은 빈공간을 의미

  

- 배열에서 알아야 할 것 2가지는?

  1. 집합을 다루기 때문에 인덱스 필요
  2. 배열을 선언하면 크키가 고정 되어 있다. 배열이름.length()



### 2차원 배열

#### 2차원 배열이란 배열의 배열이다.

- 2차원 배열 생성 방법
  - 정수를 4개씩 담을 수 있는 배열이 3개 생성된다.

```java
        int[][] array4 = new int[3][4];
```

- 2차원 배열에 값을 저장하는 방법
  - 만약 array4[1] = 10 ; 이렇게 사용하면 오류!!
  - array4[1] 은 또 다른 1차원 배열을 가리킬 수 있는 참조형 변수이기 때문에 값을 담을수는 없다.

```java
     array4[0][0] = 10; 
```

- 가변크기의 2차원 배열을 생성하는 방법

```java
    int[][] array5 = new int[3][];
    //위와 같이 선언하면 array5는 3개짜리 배열을 참조한다. 3개짜리 배열은 아직 참조하는 배열이 없다는 것을 의미.
	array5[0][0] = 10; //오류이다 아직 가리키는 참조형 변수가 아니기 때문에 밑에 처럼 배열 생성 후 값을 넣을수 있다.
    array5[0] = new int[1]; //정수를 하나 담을 수 있는 배열을 생성해서 array5 의 0 번째 인덱스가 참조한다.  
    array5[1] = new int[2]; //정수를 두개 담을 수 있는 배열을 생성해서 array5 의 1 번째 인덱스가 참조한다.  
    array5[2] = new int[3]; //정수를 세개 담을 수 있는 배열을 생성해서 array5 의 2 번째 인덱스가 참조한다. 
```

- 선언과 동시에 초기화하는 방법

```java
    int[][] array6 = {{1}, {2,3}, {4,5,6}};
    //위와 같이 선언할 경우 array6[0][0] 는 1이다. array6[1][0]은 2이다. 
```



## for each(향샹된 for문)

- 자바 1.5 버전부터 추가된 foreach 구문

```java
    int[] iarr = {10,20,30,40,50};

	for(int i = 0 ; i < iarr.length ; i++) {
        int value = iarr[i];
        System.out.println(value);
    }

	//for(타입 값을 받아줄 변수명 : 츌력하고 싶은 자료구조)
    for(int value:iarr){ 
        System.out.println(value);
    }
```



- 배열 전체 조회하기(for문도 되고 향상된 for문도 사용가능)

  ```java
  **향상된 for문**
  데이터타입[] 변수 :
  for(2타입변수 : 1배열변수) {
  
  		3실행문;
  }
  1 배열에서 가져올 첫번째값이 존재하는지 평가
  2 존재하면 해달값을 변수에 저장한다.
  3 실행문을 실행한다.
  4 다시 1로가 배열에서 가져올 항목이 없을경우 없으면 for문종료 
  
  //조회하기
  int[] scores = {95, 71, 84}
  for(int score : scores) { 
  	System.out.println(socre);
  }
  
  //합, 평균구하기
  int[] scores = {95, 71, 84}
  int sum = 0;
  for(int score : scores) { 
  	sum = sum + score;
  }
  System.out.println(sum);
  double avg = (double) sum / scores.length();
  System.out.println(avg);
  ```





# 열거(enum)

> 데이터 중에는 몇 가지로 한정된 값만을 갖는 경우가 흔히 있는데 이러한 데이터 타입이 열거타입으로 몇 개의 열거 상수 중에서 하나의 상수를 저장하는 데이터 타입이다.

ex) 요일, 계절 등

#### 자바는 열거타입을 이용하여 변수를 선언할 때 변수타입으로 사용할 수 있다.

- 열거형은 JDK5에서 추가되었다.
- JDK5 이전에는 상수를 열거형 대신 사용
  - 상수를 이용하는 방법

```java
    public class EnumExam {
        public static final String MALE = "MALE";
        public static final String FEMALE = "FEMALE";

        public static void main(String[] args) {
            String gender1;

            gender1 = EnumExam.MALE;
            gender1 = EnumExam.FEMALE;                  
        }
    }
```

#### 상수를 사용했때의 문제점

- String으로 선언된 gender1 에는 MALE,FEMALE 둘 중 한가지 값을 갖기 원하는데, gender1의 type이 String 이기 때문에 gender1 = "소년"; 이렇게 수행 되어도 전혀 문제가 되지 않는다.
- 실행할때 원했던 값인 MALE,FEMALE 이 아닌 다른 값이 들어오게 되므로 문제를 발생시킬 수 있다.

#### 해결 방법

- 이런 문제를 발생시키지 않게 하기 위해서 열거형을 사용하시면 됩니다.
- 열거형 정의 방법1
  - 선언

```java
    enum Gender{
        MALE, FEMALE;
    }
```

- 열거형 사용 방법1

```iava
    Gender gender2;

    gender2 = Gender.MALE;
    gender2 = Gender.FEMALE;

    //Gender타입의 변수에는 MALE이나 FEMALE만 대입이 가능. 다른 값은 저장할 수가 없다.  
```

- 열거형 정의 방법2
  - 선언

```java
Week.java
MemberGrade.java
ProductKind.java
public enum Week{
	Monday,
	Tuesday,
	Wednesday,
	Thursday,
	Friday,
	Saturday,
	Sunday
}
```

- 열거형 사용 방법2

```java
열거타입 변수;
Week today = Week.Sunday;
```

### 특정 값만 가져야 한다면 열거형을 사용하는 것이 좋다.





### 배열의 정렬 (오름차순, 내림차순)

https://coding-factory.tistory.com/549