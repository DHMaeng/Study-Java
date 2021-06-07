# 7. 클래스

[TOC]

클레스는 서로 연관된 변수와 메소드를 그룹핑하고 이름을 붙인 정리 정돈의 상자이다.

멤버 : 그 클래스 소속에 변수 + 메소드들을 말한다.

public class 이름() {

}

이름의 첫 문자는 대문자로 한다.

클래스 변수 = new 클래스();

- 클래스의 용도

라이브러리 API

- 캡슐화

  - 실제 데이타 구현내용을 감추는것
  - 외부객체는 내부객체 구조를 알지 못하여 객체가 노출해 제공하는 필드와 메소드만 이용가능
  - 외부의 잘못된 사용으로 인해 객체가 손상되지 않도록
  - 접근제한자 사용한다 private

- 상속

  상위 객체의 필드와 메소드를 하위 객체에게 물려주는 행위로 하위 객체는 상위 객체를 확장하여 추가적인 필드와 메소드를 가질 수 있다.

  1. 상속대상 필드와 메소드 (private는 상속x)
  2. 상속의 효과

  - 상위 객체를 재사용해서 하위 객체를 빨리 개발 가능
  - 반복된 코드의 중복을 줄임
  - 유지 보수의 편리성 제공
  - 객체의 다형성 구현

- 다형성 : 한가지 모습으로 다양한 작업을 하는 것

- 클래스의 용도

  1. 라이브러리(API)용

  - 자체적으로 실행되지 않음
  - 다른 클래스에서 이용할 목적으로 만든 클래스

  1. 실행용

  - main() 메소드를 가지고 있고 클래스로 실행할 목적으로 만든 클래스

  **1개의 어플리케이션 = (1개의 실행클레스) + (n개의 라이브러리 클래스)



## 1. 객체 지향 프로그래밍

### OOP : Object Oriented Programming

부품 객체를 먼저 만들고 이것들을 하나씩 조립해 완성된 프로그램을 만드는 기법

객체지향 : 객체는 일반적으로 말하는 물건을 의미하며 여기서 물건은 단순한 데이터가 아니고 그 데이터의 동작 방법에 대한 정보 또한 포함하고 있어 그것을 대상으로 다루는 수법을 말한다.



### 객체란?

1. 물리적(자동차, 책, 사람)으로 존재하는 것, 추상적인 것(회사, 날짜) 중에서 자신의 속성과 동작을 가지는 모든것

2. 객체는 필드(속성)과 메소드(동작)로 구성된 자바 객체로 모델링 가능



### 관계의 종류

1. 집합 관계 : 완성품과 부품의 관계

2. 사용 관계 : 객체가 다른 객체를 사용하는 관계

3. 상속 관계 : 종류 객체와 구체적인 사물 객체 관계

![image-20210423150115879](https://user-images.githubusercontent.com/80496345/116241023-7042d980-a79f-11eb-8d7b-2a51fc223194.png)

### 객체 지향 프로그래밍의 특징

- 캡슐화 : 객체의 필드와 데이터를 감추는것
- 상속
- 다형성



### 객체와 클래스

- 현실세계 : 설계도 → 객체
- 자바 : 클래스 → 객체
- 클래스에는 객체를 생성하기 위한 필드와 메소드가 정의
- 클래스로부터 만들어진 객체를 해당 클래스의 인스턴스
- 하나의 클래스로부터 여러개의 인스턴스를 만들 수 있다.

![image-20210423150143348](https://user-images.githubusercontent.com/80496345/116241029-70db7000-a79f-11eb-9eda-b04852e1a0c5.png)



## 2. 생성자

- 생성자(consturctor) : new 연산자와 같이 사용되어 클레스로부터 객체(인스턴스)를 생성할 때 호출되어 객체의 초기화를 담당한다. 기본적으로 클레스에 생성자를 생략해도 class파일에는 기본 생성자가 선언된다. 명시적으로 생성한다면 기본 생성자를 생성하지 않는다.

  ```java
  //소스파일(car.java)
  public class Car {
  	//
  }
  ```

  ```java
  //바이트 코드 파일(car.class)
  public class Car {
  	public Car() { } //자동 추가
  	//
  }
  ```

  생성자를 명시적으로 생성하는 이유는 인스턴스를 만드는 순간에 인수를 입력해 받을 수 있게 하여 인스턴스를 더 단순하게 만들어준다. 클레스에선 클레스와 이름이 같게 메소드를 정의하면 된다.



## 3. 매소드

- 메소드는 서로 연관된 코드를 모아서(그룹핑 해서) 이름을 붙인 정리 정돈의 상자다. 다른 언어의 함수와 같다.

- method와 class

  method = function = subroutine = procedural이라고 불린다.

  - method를 이용해 프로그램을 만든다. 이것이 절차지향 프로그래밍이다.

  - class라는 정리정돈 상자를 통해 프로그램을 만든다. 이것이 객체지향 프로그래밍이다.

  - 짧은 맥락을 가지고 작업하는 경우는 바로 class를 사용한다.

  - 긴 맥락을 가지고 작업해야 하는 경우에는 class를 복제해서 instance를 만들어서 사용한다.

    

## 4. 인스턴스와 this

- 인스턴스는 하나의 클레스를 복제해서 서로 다른 데이터 값과 서로 같은 메소드를 가진 복제본을 만드는 것이다
- 하나의 class를 돌려막는 것이 아니라 복제된 class를 통해서 더 편리하고 버그가 적은 코딩을 가능하게 한다.
- 소프트웨어의 구조: method로 구조 -> method + 변수로 구조 -> class (*복제) -> instance

- 어떤 클래스를 인스턴스화 해서 사용하려면 그 클래스의 멤버들(변수, 메소드)에 붙은 (클래스의 소속임을 정의하는) static을 지워줘야 한다.  static이 요놈은 복제를 못하게 막아 놓는 특허권과 같다.

- 인스턴스 사용 시, 기존 클래스는 건드리지 않으면서 각각의 인스턴스 내에서 원하는 데이터 부분을 변경할 수 있다. 코드의 중복을 줄임으로써 코드를 훨씬 더 깔끔하게 정리정돈 할 수 있다.

```java
class Print {
	public static String deliment="";
	public static void A(){
		System.out.println(deliment);
		System.out.println("a");
		System.out.println("a");
	}
	public static void B(){
		System.out.println(deliment);
		System.out.println("b");
		System.out.println("b");
	}
}
public class MYOO {

	public static void main(String[] args) {
		
		Print.delimiter = "----";
		Print.A();
		Print.A();
		Print.B();
		Print.B();

		Print.delimiter = "****";
		Print.A();
		Print.A();
		Print.B();
		Print.B();
		
		Print.delimiter = "----";
		Print.A();
		Print.delimiter = "****";
		Print.A();
		Print.delimiter = "----";
		Print.B();
		Print.delimiter = "****";
		Print.B();
	}
}
//instance를 사용
class Print {
	public String delimiter="";
	public void A(){
		System.out.println(delimiter);
		System.out.println("a");
		System.out.println("a");
	}
	public void B(){
		System.out.println(delimiter);
		System.out.println("b");
		System.out.println("b");
	}
}
public class MYOO {

	public static void main(String[] args) {
		
		Print p1 = new Print();
		p1.delimiter = "----";
		p1.A();
		p1.A();
		p1.B();
		p1.B();
		
		Print p2 = new Print();
		p2.delimiter = "****";
		p2.A();
		p1.A();
		p2.B();
		p1.B();
		
		p1.A();
		p2.A();
		p1.B();
		p2.B();		
	}
}
```

instance를 사용하여  바뀌어야되는 데이터 타입의 클래스의 코드를 훨씬 더 깔끔하고 중복을 제거하는 효과를 얻을 수 있다.

- this. : this는 내가 생성한 인스턴트를 가르키는 이름이다. 의미가 같지만 파라미터와 멤버 변수로 역할이 나눠질 때 굳이 다른 명칭으로 나누지 않고 바로 사용하게 해준다.

아래 코드에서 변수 delimiter가 똑같더라도 this.delimiter는 print method 변수가 아닌 윗줄 ""로 되어있는 instance가 가르키는 변수이다.

```java
class Print {
	public String delimiter="";
	public Print(String delimiter) {
		this.delimiter = delimiter;
	}
	public void A(){
		System.out.println(this.delimiter);
		System.out.println("a");
		System.out.println("a");
	}
}
public class MYOO {

	public static void main(String[] args) {
		
		Print p1 = new Print("----");
//		p1.delimiter = "----";
		p1.A();
	}
}
```

this() this가 car  인스턴스를 가리키기 때문에 this(~,~,~)로 쓰게 되면 인자가 3개로 초기화되어있는 맨 밑 생성자를 호출하게된다.

![image-20210423154512791](https://user-images.githubusercontent.com/80496345/116241033-71740680-a79f-11eb-9c6a-9b327566763e.png)



## 5. static

- static은 '정적'의 의미를 가지며 이것이 붙는다면 그 필드나 메서드는 클래스 형식이라는 의미. 안 붙는다면 그 필드 및 메서드는 인스턴스 형식이라는 의미.

- 클래스 형식(static)이라면 C언어의 Call by reference 처럼 인스턴스를 생성한다고 해도 원래 값은 class 내의 값 하나 뿐이며 인스턴스는 이를 포인터처럼 단순히 가리키게 된다. 즉 같은 메모리에 값이 가리키며, 이 때문에 인스턴스 내이든 클래스 내이든 그 값이 변한다면 이것은 다른 객체에도 영향을 끼치게 된다.

- 반대로 인스턴스 형식(non-static)이라면 call by value로, 다른 인스턴스 객체 생성 시 아예 다른 메모리에 값이 저장 및 가리키게 되며 이렇게 되면 그 필드 및 메서드의 변화가 일어날 시 다른 객체에 영향을 끼치지 않게 된다.

```java
class Foo {
	public static String classVar = "I class var";
	public String instanceVar = "I instance var";
	
	public static void classmethod() {
		System.out.println(classVar);// ok
//		System.out.println(instanceVar);//error
	}
	public void intancemethod() {
		System.out.println(classVar);// ok
		System.out.println(instanceVar);//ok
	}
}
public class StaticApp {

	public static void main(String[] args) {
		
		System.out.println(Foo.classVar); //ok
//		System.out.println(Foo.instanceVar);//error
		
		Foo.classmethod(); //ok
//		Foo.instanceVar(); // error
		
		Foo f1 = new Foo();
		Foo f2 = new Foo();
		
		System.out.println(f1.classVar); //I class var
		System.out.println(f1.instanceVar);//I instance var
		
		f1.classVar = "changed by f1";
		System.out.println(f1.classVar); //changed by f1
		System.out.println(f2.classVar);//changed by f1
		
		f1.instanceVar = "changed by f1";
		System.out.println(f1.instanceVar); //changed by f1
		System.out.println(f2.instanceVar);//I class var
	}

}
```



### 싱글톤

전체 프로그램에서 단 하나의 객체만 만들도록 보장해야 하는 경우가 있다. 단 하나만 생성된다고 해서 이 객체를 싱글톤이라고 한다. 먼저 싱글톤이란 **어떤 클래스가 최초 한번만 메모리를 할당하고(Static) 그 메모리에 객체를 만들어 사용하는 디자인 패턴=** 을 의미한다.
즉 생성자의 호출이 반복적으로 이뤄져도 실제로 생성되는 객체는 최초 생성된 객체를 반환 해주는 것이다.
보통 아래와 같이 사용하게 된다.

```java
public class ExampleClass {
    //Instance
    private static ExampleClass instance = new ExampleClass();

    //private construct
    private ExampleClass() {}

    public static ExampleClass getInstance() {
        return instance;
    }
}
```

위 코드에서는 instance라는 전역 변수를 선언하는데 **static**을 줌으로써 인스턴스화 하지 않고 사용할 수 있게 하였지만 접근 제한자가 **private** 로 되어 있어 직접적인 접근은 불가능하다.
또한 생성자도 private으로 되어 있어 **new** 를 통한 객체 생성도 불가능하다.
결국 getInstance 메서드를 통해서 해당 인스턴스를 얻을 수 있게 된다.
위의 예제는 아주 작은 규모에서 사용할 수 있는 싱글톤 패턴이며, 다음에서 좀 더 알아보기로 한다.



#### 그렇다면 싱글톤 패턴을 사용하는 이유는?

위에서도 언급된 바와 같이 한번의 객체 생성으로 재 사용이 가능하기 때문에 메모리 낭비를 방지할 수 있다.
또한 싱글톤으로 생성된 객체는 무조건 한번 생성으로 전역성을 띄기에 다른 객체와 공유가 용이하다.
이렇게만 보면 싱글턴이 좋아보일 수 있지만 문제점도 존재한다.



#### 싱글톤의 문제점

싱글톤도 위에서 언급된 것 처럼 전역성을 띄면서 다른 객체와 공통으로 사용하는 경우와 같은 몇 가지 케이스에서만 사용할 때 효율적이며 그 외에는 문제점이 생길 수 있다.
일단 싱글톤으로 만든 객체의 역할이 간단한 것이 아닌 역할이 복잡한 경우라면 해당 싱글톤 객체를 사용하는 **다른 객체간의 결함도**가 높아져서 객체 지향 설계 원칙에 어긋나게 된다. (개방-폐쇄)
또한 해당 싱글톤 객체를 수정할 경우 싱글톤 객체를 사용하는 곳에서 **사이드 이팩트** 발생 확률이 생기게 되며, **멀티 쓰래드**환경에서 동기화 처리 문제등이 생기게 된다.



#### 정리

싱글톤 패턴은 Spring framework에서도 많이 사용되며, 어떤식으로 구현하는지 알아두면 도움이 된다.
자바와 Spring에서의 싱글톤 차이점이라면, 싱글톤 객체의 생명주기가 다르다.
또한 자바에서 공유 범위는 Class loader 기준이지만, Spring에서는 ApplicationContext가 기준이 된다.

출처 : https://elfinlas.github.io/2019/09/23/java-singleton/



## 6. final 필드

- final 필드

  최종적인 값을 갖고 있는 필드 = 값을 변경할 수 없는 필드

  ```java
  final 타입 필드 [= 초기값]; 파이널필드는 생성자를 통해서라도 무조건 초기화를 해야한다.
  public class Person {
  	final String nation = "korea";
  	final String ssn;
  }
  
  public Persion(String ssn, String name) {
  	this.ssn = ssn;
  	this.name = name;
  }
  ```

- 상수(static final) : 불변의 값을 저장하는 필드

  1. final 필드는 여러가지 값으로 초기화 될 순 있지만 상수는 한번 초기화되면 바꿀 수 없다.
  2. 상수는 static이면서 final이여야 한다
  3. 상수 이름은 전부 대문자로 작성
  4. 다른 단어가 결합되면 _로 연결

  ```java
  static final double PI = 3.14159;
  static final double EARTH_SURFACE_AREA;
  ```



## 7. 패키지

- 패키지란?

  - 클래스를 기능별로 묶어서 그룹 이름을 붙여 놓은 것
    - 파일들을 관리하기 위해 사용하는 폴더와 비슷한 개념
    - 패키지의 물리적인 형태는 파일 시스템의 폴더
  - 클래스 이름의 일부
    - 클래스를 유일하게 만들어주는 식별자
    - 전체 클래스 이름- 상위패키지,하위패키지 클래스
    - 클래스명이 같아도 패키지명이 다르면 다른 클래스

- 패키지 선언

  1.  숫자로 시작, 특수문자 사용 x
  2.  java로 시작 x
  3.  모두 소문자로 작성하는게 관례

  ```java
  package 상위패키지.하위패키지;
  
  public class ClassName {...}
  ```

- 패키지가 다르면 클래스를 사용할 수 없는데 import를 사용하면 다른 패키지의 클래스를 사용할 수 있다.

```java
package com.mycompany;
//import 패키지이름.클래스이름;
import com.hankook.Tire;

public class Car {
	Tire tire = new Tire()
}
```



## 8. 접근 제한자 access level modifiers/static

```java
class Greeting{
	private static void hi() { // public으로 바꿔야 메인에 hi메소드가 동작
		System.out.println("Hi");
	}
}
public class AccessLevelModifiersMethod{
	
	public static void main(String[] args){
		Greeting.class.hi();
	}
}
```

- access modifiers (접근제어자)

  1. public : 다른 class의 메소드도 사용 가능.
  2. private : 같은 class안에 있는 메소드만 사용 가능.
  3. protected
  4. default

  cf) static -class method / non static - instance method

```java
class Print{
    public String delimiter;
    public void a() {
        System.out.println(this.delimiter);
        System.out.println("a");
        System.out.println("a");
    }
    public void b() {
        System.out.println(this.delimiter);
        System.out.println("b");
        System.out.println("b");
         
    }
    public static void c(String delimiter) {
        System.out.println(delimiter);
        System.out.println("b");
        System.out.println("b");
    }
}
public class staticMethod {
     
    public static void main(String[] args) {
//      Print.a("-");
//      Print.b("-");
         
        // instance
        Print t1 = new Print();
        t1.delimiter = "-";
        t1.a();
        t1.b();
        Print.c("$");
         
         
//      Print.a("*");
//      Print.b("*");
         
        Print t2 = new Print();
        t2.delimiter = "*";
        t2.a();
        t2.b();
    }
     
 
}
```

내 정보를 얼마만큼 공개 할 것 인가를 정할 수 있다.

![image-20210423162838198](https://user-images.githubusercontent.com/80496345/116241035-720c9d00-a79f-11eb-9d05-532b74f9a799.png)



![image-20210423162914452](https://user-images.githubusercontent.com/80496345/116241038-72a53380-a79f-11eb-80db-805863f89f61.png)

자신 패키지0  다른 패키지 x → default



## 9. getter와 setter

- get과 set 메소드

일반적으로 객체 지향 프로그래밍에서 객체의 데이터는 객체 외부에서 직접적으로 접근하는 것을 막는다.  그 이유는 객체의 데이터를 외부에서 마음대로 읽고 변경할 경우 객체의 무결성(결점이 없는 성질)이 깨질 수 있기 때문이다. 그래서 메소드를 통해서 데이터를 변경하는 방법을 선호한다. 메소드가 매개값을 검증해서 유효한 값만 데이터로 저장(set)할 수 있기 때문이다. 외부에서 객체의 데이터를 읽을 때도 메소드를 사용한다.(get)

클레스를 선언할 때 필드를 private로 선언하여 외부로부터 보호하고 필드에 대한 set과 get메소드를 작성해서 필드값을 안전하게 변경/사용 하는 것이 좋다.

```java
public class Car {
	/*필드 : 객체의 데이터가 저장되는 곳으로 변수와 비슷하지만 변수는 생성자오아 메소드 내에서만 사용
					 되고 실행종료되면 자동 소멸된다. 하지만 필드는 생성자와 메소드 전체에서 사용되며 객체가
					 소멸되지 않는 한 객체와 함꼐 존재한다. 
	*/
	private int speed;
	private boolean stop;

	//생성자	: 객체 생성 시 초기화 역할 담당으로 클레스와 이름이 같고 리턴이없다.
	public Car() {
	
	}

	//메소드 : 객체의 동작에 해당하는 실행 블록
	public int getSpeed() {
		return speed;
	}
	public void setSpeed(int speed) {
		if(speed < 0) { //잘못된 값이 들어오게 되면 차단
			this.speed = 0;
			return;
		}	else {
			this.speed = speed;
		}	
	}
	
	public boolean getStop() { //isStop으로 쓰는게 관례
		return stop;
	}
	public void setStop(boolean stop) {
		this.stop = stop;
	}
}
```



## 10. 어노테이션

- 프로그램에게 추가적인 정보를 제공해주는 메타데이터로 컴파일 과정과 실행 과정에서 코드를 어떻게 컴파일하고 처리할 것 인지를 알려주는 정보이다.

- 어노테이션 용도

  - 컴파일러에게 코드 작성 문법 에러 체크하도록 정보 제공
  - 소프트웨어 개발 툴이 빌드나 배치 시 코드를 자동 생성하게 정보 제공
  - 실행 시(런타임시) 특정 기능 실행하도록 정보 제공

- 어노테이션 타입 정의와 적용

  ```java
  @Target(ElementType.METHOD)
  @Retention(RetentionPolicy.RUNTIME)
  public @interface CustomAnnotation {
  	boolean isCheck() default true;
  }
  ```

https://elfinlas.github.io/2017/12/14/java-annotation/