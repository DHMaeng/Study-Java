# 9. final

자바에서 절대 변하지 않는 특정한 것을 정하고 싶을 때는 최종(final)을 사용한다. 이 키워드는 변수, 메소드, 클래스에 모두 사용 가능하다.

변수에 사용할 경우 변하지 않는 상수가 되며,

메소드가 사용할 때는 재정의가 불가능한 메소드가 되며,

클래스에 사용할 때는 상속이 불가능한 하나의 완전한 클래스가 된다.

- final 변수

```java
public class Main {

	public static void main(String[] args) {
		
		final int number = 10;
		// number = 5; <-오류
		System.out.println(number);

	}
}
```

- 메소드

```java
public class Main extends Parent{
	public void show() {//overriding 즉 메소드의 재정의를 하려고 했지만 final로 하면 재정의 불가
		System.out.println("hello");
	}

	public static void main(String[] args) {
		
		Main m = new Main();
		m.show();
	}
}
public class Parent {
	
	public final void show() {
		System.out.println("hi");
	}
}
```

- 클래스

```java
public class Main extends Parent{ // final 해서 상속 불가능
	public void show() { 
		System.out.println("hello");
	}

	public static void main(String[] args) {
		
		Main m = new Main();
		m.show();
	}
}
final class Parent {
	
	public final void show() {
		System.out.println("hi");
	}
}
```