# 9. 인터페이스

인터페이스(Interface)는 얼핏 보기에는 추상클래스와 매우 흡사한 개념으로 느껴질 수 있다. 인터페이스는 숙련된 자바 개발자들에게 아주 선호되는 설계 기능이면서 자바에서 다중 상속을 구현하게 해주는 고급 기술이기도 하다.

추상 클래스는 추상 메소드 외에 맴버 변수나 일반 메소드를 가질 수 있지만 인터페이스에서는 반드시 사전에 정의된 추상 메소드와 상수만을 가질 수 있다는 특징이 있다.

인터페이스는 팀 프로젝트의 동시 작업 유리하고 일반적으로 추상보다 요구되는 설계의 기준이 높아서 더 체계적이라는 평을 받습니다. (즉 추상클래스보다 더 엄격한 추상화(더 실질적이지 않다)가 들어가 있다라고 생각!)

```java
public class Main implements Dog, Cat{ // 이렇게 상속이 여러개 가능하다. abstract는 불가능

	public static void main(String[] args) {
		
		Main main = new Main();
		main.crying();
		main.one();
		main.two();
	}
//인터페이스를 할 경우 인터페스에 설계가 된것을 밑에처럼 무조건 구현해줘야한다.
	@Override
	public void crying() {
		System.out.println("멍~ 멍~");
		
	}

	@Override
	public void one() {
		System.out.println("one");
		
	}

	@Override
	public void two() {
		System.out.println("two");

	}
}
public interface Dog {
	
	abstract void crying();
//	public void one() { interface에는 abstract와 다르게 실질적인 코드를 적으면 안된다.
//		System.out.println("hello");
//	}
	public void one(); // 이렇게 정의만
}
public interface Cat {
	
	abstract void crying();
	public void two();
}
```