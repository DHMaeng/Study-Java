# 7. 클래스

#### 클래스 선언

#### 자바는 객체를 만들기 위해 반드시 클래스를 먼저 만들어야 한다. 클래스는 객체를 만들기 위한 일종의 틀이다.

- 붕어빵이 객체라면, 붕어빵 틀은 클래스
- 자동차 클래스 생성

```java
    public class Car{

    }
```

- Car.java란 파일을 만든다.
- 저장을 하면 이클립스는 컴파일하여 디스크에 Car라는 클래스를 생성한다.
- **자동차 클래스가 생성되었다고 해서 자동차가 만들어 진것은 아니다.**

#### Car객체 생성하기 (자동차 만들기)

```java
    public class CarExam{
        public static void main(String args[]){
            Car c1 = new Car();
            Car c2 = new Car();
        }
    }
```

- new 연산자는 new연산자 뒤에 나오는 생성자를 이용하여 메모리에 객체를 만들라는 명령.
- 메모리에 만들어진 객체를 인스턴스(instance)라고도 한다.
- 이렇게 만들어진 객체를 참조하는 변수가 c1 , c2 이다.
- 위의 코드가 실행되면 Car라는 객체가 2개가 만들어지고 각각의 객체를 참조하는 c1과 c2변수가 선언됩니다.





#### 참조타입

#### 참조형 타입은 기본형 타입을 제외한 모든 타입입니다. 앞서 배웠던, 배열도 참조형이고, 클래스도 모두 참조 타입이다

- 참조형 변수
  - String str = new String("hello");
    - str 변수 앞에 기본형 타입이 아닌 String클래스가 적혀있다.
    - 이퀄(=)뒤에는 new 다음에 생성자라는 것이 있다.
    - new 라는 키워드는 객체를 메모리에 올려준다. 이렇게 메모리에 올라간 객체를 인스턴스라고 말한다.
- 메모리에 올라간 인스턴스를 가리키는 변수, 참조하는 변수, 레퍼런스 하는 변수가 str 이다. 참조한다. 레퍼런스 한다라는 것은 변수가 인스턴스를 가지고 있는게 아니라 말그대로 가리킨다는 의미이다.
- str이라는 변수에는 메모리의 위치 값이 저장되는 것이다. 메모리의 위치값이 저장된다고 하더라도, 어떤 메모리에 저장되는지 그 정보를 알 수 있는 방법은 없다. 그렇기 때문에 str변수는 String 인스턴스를 참조한다라고만 아시면 된다.
- 앞으로 배울 클래스들은 모두 참조형이다





### String 클래스

#### 문자열을 표현하는 자바에서 가장 많이 사용하는 클래스

#### 자바 인스턴스 생성 방법

1. new연산자를 이용하지 않고 인스턴스를 만드는 경우

```java
    String str1 = "hello";
    String str2 = "hello";
```

- "hello"라는 문자열이 메모리 중에서 상수가 저장되는 영역에 저장된다. 상수는 변하지 않는 값을 의미.
- String str2 = "hello"; 이 문장이 실행될 때에 hello 라는 문자열 상수는 이미 만들어져 있으므로 str1이 참조하는 인스턴스를 str2도 참조한다.

2. new연산자를 이용해서 인스턴스를 만드는 경우

```java
    String str3 = new String("hello");
    String str4 = new String("hello");
```

- new연산자를 이용하여 인스턴스를 만들면 인스턴스는 무조건 새롭게 만들어진다.
- String str4 = new String("hello"); 이 문장이 실행될때도 새롭게 만들게 되므로, str3 과 str4는 서로 다른 인스턴스를 참조한다.

```java
    if(str1 == str2){  // 같은 인스턴스를 참조하므로 결과는 true 
        System.out.println("str1과 str2는 같은 레퍼런스입니다.");
    }

    if(str1 == str3){  // str1과 str3은 서로 다른 인스턴스를 참조하므로 결과는 false 
        System.out.println("str1과 str3는 같은 레퍼런스입니다.");
    }

    if(str3 == str4){  // str3과 str4는 서로 다른 인스턴스를 참조하므로 결과는 false 
        System.out.println("str3과 str4는 같은 레퍼런스입니다.");
    }
```

- 참조변수끼리 == 로 비교하면 서로 같은 것을 참조하는지 비교한다.
- String은 다른 클래스와 다르게 new를 사용하지 않고 사용할 수 있다. 메모리를 아끼려면 String은 new를 사용하지 않고 사용하는 것이 좋다.
- String은 불변 클래스이다. 불변이란 String이 인스턴스가 될때 가지고 있던 값을 나중에 수정할 수 없다.
- String은 문자열과 관련된 다양한 메소드를 가지고 있다. 메소드를 호출한다 하더라도 String은 내부의 값이 변하지 않는다.
- String이 가지고 있는 메소드중 String을 반환하는 메소드는 모두 새로운 String을 생성해서 반환한다.

```java
    String str5 = "hello world";
    String str6 = str5.substring(3); //lo world
```

- substring은 문자열을 자른 결과를 반환하는 메소드이다. 해당 코드가 실행되어도 str5는 변하지 않는다.
- str6은 str5가 가지고 있는 문자열 중 3번째 위치부터 자른 결과 즉 새로운 String을 참조하게 된다.





#### 필드(field)선언

#### 자동차는 자동차 이름, 자동차 번호를 가지고 있고, 자동차는 달리고 멈추는 기능이 있다. 여기에서 가지고 있는 것을 속성이라고 한다. 자바에서는 이러한 속성을 필드(Field)라는 용어로 사용한다.

- 이름과 번호를 필드로 가지고 있는 Car클래스 선언

```java
    public class Car{
        String name;    
        int number;
    }
```

- Car 클래스를 인스턴스화 하기

```java
    Car c1 = new Car();
    Car c2 = new Car();
    //Car라는 인스턴스가 메모리에 2개 만들어 진다. 객체별로 name과 number라는 속성을 가진다.
```

- 속성 이용하기
  - 참조 변수 다음에 나오는 점(dot)은 참조변수가 참조하는 객체가 가지고 있는 것을 사용할 때 사용

```java
    //c1.name은  c1이 참조하는 객체의 name 을 의미.

    c1.name = "소방차";  //c1이 참조하는 객체의 name을 소방차로 설정 
    c1.number = 1234;   // c1.number = 1234란 c1이 참조하는 객체의 number를 1234 로 설정 

    c2.name = "구급차"  //c2가 가리키는 객체의name을 구급차로 설정
    c2.number = 1004;  //c2가 가리키는 객체의 number를 1004로 설정


    System.out.println(c1.name);  //콘솔에 c1이 참조하는 객체의 name 을 출력합니다. 
    System.out.println(c1.number); //콘솔에 c1이 참조하는 객체의 number 를 출력합니다. 

    String name = c2.name;   //c2가 참조하는 객체의 name 을 String 타입 변수 name 도 참조하게 합니다.
```



#### 메소드란?

### 메소드

#### 필드가 물체의 상태라면, 물체의 행동에 해당하는게 메소드다. car에 이름과 번호가 있기도 하지만, car는 앞으로 전진할수도 있고 후진하는 행동도 할 수 있다.

- 메소드는 입력값이 있고, 그 입력값을 받아서 무언가 한 다음 결과를 도출해 내는 수학의 함수와 비슷한 개념이다.
- 이때 입력값을 매개변수라고 하고,결과값을 리턴값이라고 합니다.
  - 인자( Argument ) 는 어떤 함수를 호출시에 전달되는 값을 의미한다.
  - 매개 변수( Parameter ) 는 그 전달된 인자를 받아들이는 변수를 의미한다.
- 메소드란 클래스가 가지고 있는 기능이다. 클래스 안에 선언됩니다.

```java
class ReferenceTypeExam {
    public static void main(String []args) {
        ReferenceTypeExam exam = new ReferenceTypeExam();
        
        //기본형 변수value1을 addOne에 전달합니다.
        int value = 10;
        exam.addOne(value);
        System.out.println("기본형 변수의 값을 다른 메소드에서 변경한 결과: " + value);
        
        
        //참조형 변수arr을 addOne에 전달합니다.
        int []arr = {10};
        exam.addOne(arr);
        System.out.println("참조형 변수의 값을 다른 메소드에서 변경한 결과: " + arr[0]);
    }
    
기본형 변수의 값을 다른 메소드에서 변경한 결과: 10
참조형 변수의 값을 다른 메소드에서 변경한 결과: 11

기본형 타입은 다른 메소드에 매개변수로 전달될때, 10이라는 값이 그대로 전달됩니다.따라서 addOne에서 1을 더하더라도 value라는 변수에는 아무 영향이 없습니다.

하지만 참조형 타입은 다른 메소드에 매개변수로 전달될때, 변수의 주소가 전달됩니다. 예를들어 '몇번째 박스에 값이 있다'는 식으로 값이 들어있는 주소가 전달되는겁니다. 그럼 그걸 전달받은 메소드addOne에서는 그 박스에 가서 들어있는 값에 1 더합니다. addOne을 실행하고 나서 arr[0]을 확인해 볼 때도 같은 박스에 가서 값을 확인하기 때문에 값이 11로 변해있는겁니다.
```



### String Class가 제공하는 메소드 이용하기

- 문자열 길이 구하기
  - str.length()는 str이 참조하는 문자열의 길이를 구해서 int 타입으로 리턴해주는 메소드 이다.

```java
    System.out.println(str.length());  //str
```

- 문자열 붙히기 (concat)
  - str.concat("world") 메소드는 str 이 참조하는 문자열 hello 에다가 메소드의 인자로 들어온 문자열 world 를 붙혀서 String 타입으로 리턴하는 메소드다.
  - String Class는 불변 클래스로, 메소드가 수행되면, 새로운 문자열을 만든다. 그러므로, 원래 클래스는 변하지 않는다.

```java
    String str = new String("hello");

    System.out.println(str.concat(" world"));  //출력결과는 hello world 
    System.out.println(str);  //출력결과는 hello 
    str=str.concat(" world");
  	System.out.println(str); //출력결과는 hello world 
```

- 문자열 자르기 (subString) // ~이상 ~미만
  - 문자열의 인덱스는 0번 부터 시작한다. // h가 0
  - str.subString(1,3) 은 str이 참조하는 문자열을 인덱스 1번부터 3번까지 자른 결과이다.
  - str.subString(2) 은 str이 참조하는 문자열을 2번 인덱스부터 마지막까지 자른 결과를 의미한다.

```java
    System.out.println(str.substring(1, 3)); //출력결과  el
    System.out.println(str.substring(2));   //출력결과 llo world
```



### static(class2참조)

>static은 '정적'의 의미를 가지며 이것이 붙는다면 그 필드나 메서드는 클래스 형식이라는 의미. 안 붙는다면 그 필드 및 메서드는 인스턴스 형식이라는 의미.

- 같은 클래스 내에 있음에도 해당 변수들을 사용할 수 없다.
- main 메소드는 static 이라는 키워드로 메소드가 정의되어 있다. 이런 메서드를 static 한 메소드 라고 한다.
- static한 필드(필드 앞에 static 키워드를 붙힘)나, static한 메소드는 Class가 인스턴스화 되지 않아도 사용할 수 있다.

```java
    public class VariableScopeExam {
        int globalScope = 10; 
        static int staticVal = 7;

        public void scopeTest(int value){
            int localScope = 20;        
        }

        public static void main(String[] args) {
            System.out.println(staticVal);      //사용가능 
        }

    }
```

##### static한 변수는 공유된다.

- static하게 선언된 변수는 값을 저장할 수 있는 공간이 하나만 생성된다. 그러므로, 인스턴스가 여러개 생성되도 static한 변수는 하나다. 즉 공간이 하나기때문에 값을 공유한다.

```java
    ValableScopeExam v1 = new ValableScopeExam();
    ValableScopeExam v2 = new ValableScopeExam();
    v1.golbalScope = 20;
    v2.golbalScope = 30; 

    System.out.println(v1.golbalScope);  //20 이 출력된다. 
    System.out.println(v2.golbalScope);  //30이 출력된다. 

    v1.staticVal = 10;
    v2.staticVal = 20; 

    System.out.println(v1.statVal);  //20 이 출력된다. 
    System.out.println(v2.statVal);  //20 이 출력된다. 
```

- golbalScope같은 변수(필드)는 인스턴스가 생성될때 생성되기때문에 인스턴스 변수라고 한다.
- staticVal같은 static한 필드를 클래스 변수라고 한다.
- 클래스 변수는 레퍼런스.변수명 하고 사용하기 보다는 클래스명.변수명 으로 사용하는것이 더 바람직하다고 하다.
  - VariableScopeExam.staticVal





### 생성자

#### 모든 클래스는 인스턴스화 될때 생성자를 사용한다.

#### 생성자의 특징

- 생성자는 리턴타입이 없다.
- 생성자를 프로그래머가 만들지 않으면 매개변수가 없는 생성자가 컴파일할 때 자동으로 만들어진다.
- 매개변수가 없는 생성자를 기본생성자라고 한다.
- 생성자를 하나라도 프로그래머가 만들었다면 기본생성자는 자동으로 만들어지지 않는다.

#### 생성자의 역할

- 생성자가 하는 일은 객체가 될 때 필드를 초기화 하는 역할을 수행한다.
- 자동차가 객체가 될때 반드시 이름을 가지도록 하려면,Car클래스를 다음과 같이 만들어야 한다.

```java
    public class Car{
        String name;
        int number;

        public Car(String n){
            name = n;
        }
    }
```

- 위의 Car 클래스를 이용하여 Car 인스턴스를 생성하는 방법

```java
    public class CarExam2{
        public static void main(String args[]){

            Car c1 = new Car("소방차");
            Car c2 = new Car("구급차");
            //Car c3 = new Car(); // 컴파일 오류가 발생합니다.

            System.out.println(c1.name);

            System.out.println(c2.name);
        }
    }
```

- Car클래스는 기본 생성자를 가지지 않는다. 그래서 기본생성자로 Car 객체를 생성할 수 없다.





### 메소드 오버로딩

#### 매개변수의 유형과 개수가 다르게 하여 같은 이름의 메소드를 여러 개 가질 수 있게하는 기술

#### 메소드 오버로딩

- 이름은 같지만 매개변수가 다른 메소드

```java
    class MyClass2{
        public int plus(int x, int y){
            return x+y;
        }

        public int plus(int x, int y, int z){
            return x + y + z;
        }

        public String plus(String x, String y){
            return x + y;
        }
    }
```

- 메소드 오버로딩은 매개변수 부분이 달라야 한다.

```java
    public int plus(int i, int f){
        return i+f;
    }
```

- 위처럼 변수명은 다르지만, 매개변수의 타입과 개수가 동일한 메소드를 또 정의 할 수는 없다.

### 오버로딩된 메소드 이용하기

- 메소드의 인자에 어떤 값이 쓰이느냐에 따라서 각기 다른 메소드가 호출된다.

```java
    public MethodOverloadExam{
        public static void main(String args[]){
            MyClass2 m = new MyClass2();
            System.out.println(m.plus(5,10));
            System.out.println(m.plus(5,10,15));
            System.out.println(m.plus("hello" + " world"));
        }
    }
```

### 생성자 오버로딩

#### 생성자의 매개변수의 유형과 개수가 다르게 하여 같은 이름의 생성자를 여러 개 가질 수 있다.

- 생성자도 메소드와 마찬가지로 여러개를 선언할 수 있다.
- 매개변수의 수와 타입이 다르다면 여러개의 생성자를 선언할 수 있다.

```java
    public class Car{
        String name;
        int number;

        public Car(){

        }

        public Car(String name){
            this.name = name;
        }

        public Car(String name, int number){
            this.name = name;
            this.number = number;
        }
    }
```

#### 오버로딩된 생성자 이용하기

```java
    public class CarExam4{
        public static void main(String args[]){
            Car c1 = new Car();
            Car c2 = new Car("소방차");
            Car c3 = new Car("구급차", 1234);
        }
    }
```

#### 자기 생성자 호출하는 this()

- 기본생성자를 호출하였을 때 name을 "이름없음" , 숫자를 0으로 초기화 하기

```java
    public Car(){
        this.name = "이름없음";
        this.number = 0;
    }
```

- 위처럼 작성했을 경우 코드의 중복이 일어난다.
- 자신이 가지고 있는 다른 생성자를 이용할 수 있다.

```java
    public Car(){
        this("이름없음", 0);
    }
```

- this괄호 열고로 시작하면 자신의 생성자를 호출하는 것이다.
- 자기 자신의 생성자를 호출함으로써 비슷한 코드가 중복되서 나오는 것을 방지할 수 있다.
