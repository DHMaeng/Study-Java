# 8. 상속(Inheritance)

- -----상속이 왜 필요한가?

1억개의 코드가 있는 클래스에서 특정한 기능을 추가해야 하거나, 수정해야 하는 경우,

일일히 찾아서 들어가기도 힘들고, 해당 클래스가 적용된 부분은 또 다 수정해야하는 경우..

(지금까지 배워온 객체지향의 문제점에서 조금 더 확장 된 개념이라고 생각하면 이해가 쉬울 듯 하다.)

대부분의 객체지향에서의 문제점 발생은 수많은 코드에서 중간중간에 수정과 배포를 조금 더 편리하게 하기 위하여 상속이라는 개념이 등장했다.

- -----상속의 구문 형태

Class a **extends** b {} 의 구문 형태를 취한다.

- ----- Override

이전에는 Cal 클래스에서 Cal3 클래스로 단순히 확장의 개념이었다면

이제는 Cal3 에서 이것 저것 해볼 수 있는 기회가 생겼다.

단순히 확장의 개념을 넘어서, 기존의 클래스를 확장된, 상속받은 클래스에서 재정의 할 수 있는 기회도 부여 받게 된다. 이런것을 Overriding라 정의하고, 한마디로 올라 탔다는 것, 자식 클래스가 부모클래스에 등짝에 올라탔다는 것이다.

- ----- Overload

Overload, 과적하다 라는 뜻을 가진 이 개념은

기존 메소드에 매개변수의 개수를 추가하거나 하는 등의 행위를 통하여

같은 이름을 가진 원메소드에서 기능을 조금 더 "과적"해서 추가하는것을 뜻합니다.

기능만 추가하는것이므로, 원메소드와 이름도 동일하게 쓸 수 있습니다.

- ----- Overriding vs Overloading

오버로딩(Overloading): 한국어로 '과적화', 상속과 관련없음, 같은 메서드 이름을 가지면서도 매개변수 타입 및 개수를 변화시키고 생성함으로써 여러 상황에 대해 대처가 가능하게 한다.

오버라이딩(Overriding): 상속과 관련 깊음, 부모 클래스를 상속받은 자식 클래스가 부모 메서드와 같은 이름의 메서드를 생성해 내용을 다르게 함으로써 부모와 다르게 활용이 가능하게 한다.

```java
//부모부분
class Cal{
	public int sum(int v1, int v2) {
		return v1+v2;
	}
	//overloading
	public int sum(int v1, int v2, int v3) {
		return v1+v2+v3;
	}
}
//inheritanceApp 상속(아들부분)
class Cal3 extends Cal{
	public int minus(int v1, int v2) {
		return v1-v2;
	}
	//overrideing(부모가 갖고있는 기능을 덮어쓰기했다, 올라탔다.)
	public int sum(int v1, int v2) {
		System.out.println("cal3!");
		return v1+v2;
	}
	//overloading
	public int sum(int v1, int v2, int v3) {
		return v1+v2+v3;
	}
}
//이렇게 새로 cal 내용을 추가하는것보다 cal의 코드가 길다면 상속을 사용하면 훨씬 더 큰 강점을 지닌다. 
//class Cal2{
//	public int sum(int v1, int v2) {
//		return v1+v2;
//	}
//	public int minus(int v1, int v2) {
//		return v1-v2;
//	}
//}
public class inheritanceApp {

	public static void main(String[] args) {
		Cal c = new Cal();
		System.out.println(c.sum(1, 2));
		System.out.println(c.sum(1, 2, 3));
		
		Cal3 c3 = new Cal3();
		System.out.println(c3.sum(1, 2));
		System.out.println(c3.minus(2, 1));
		System.out.println(c.sum(1, 2, 3));
	}

}
```

- ----- super, this

this 는 자기 자신 클래스 내에 있는 메소드를 지칭할 때,

super는 부모 클래스 내에 있는 메소드를 지칭할 때 쓴다.!!

![image-20210423164543391](https://user-images.githubusercontent.com/80496345/116241039-72a53380-a79f-11eb-87fc-636c9573a6a9.png)

- ----- 상속과 생성자

생성자가 있는 부모 클래스를 상속받으려면 생성자도 함께 상속 받아야 한다. 이때는 this가 아닌, super를 써서 부모 클래스의 생성자임을 명확하게 하고, 부모에게서 상속받은 생성자임을 확실히 한다.

```java
class Cal1{
	int v1, v2;
	Cal1(int v1, int v2){
		System.out.println("cal");
		this.v1 = v1; this.v2=v2;
	}
	public int sum() {return this.v1+v2;}
}
class Cal4 extends Cal1{

	Cal4(int v1, int v2) {
		super(v1, v2);
		System.out.println("cal3");
	}
	public int minus() {return this.v1-v2;}
}

public class inheritanceApp2 {

	public static void main(String[] args) {
		Cal1 c = new Cal1(2,1); //cal
		Cal4 c3 = new Cal4(2,1);//cal cal3
		System.out.println(c.sum()); //3
		System.out.println(c3.minus()); //1
	}
}
```

## tostring()

"Object"클래스가 가진 메소드 중 "toString"메소드가 있습니다.

물론 "Object" 클래스의 모든 메소드는 모든 클래스가 사용이 가능합니다.

**toString()** 메서드는 객체가 가지고 있는 정보나 값들을 문자열로 만들어 리턴하는 메소드 입니다.

```java
public void printBall(LottoBall[] balls) {
		for(LottoBall ball : balls) {
			System.out.println(ball); //toString을 만들어 놓으면 같은 의미System.out.println(ball.toString());
private String ballNumber;
	private boolean isSelectedBall;
	public LottoBall(String ballNumber) {
		this.ballNumber = ballNumber;
	}
@Override
	public String toString() {
		// TODO Auto-generated method stub
		return this.getBallNumber()+","+this.getSelectedBall();
	}
```



## 추상클래스

일종의 미완성 클래스라고 할 수 있는 추상 클래스를 제공한다. 추상클래스는 직접적으로 객체 인스턴스를 생성할 수 없지만 새로운 클래스를 작성하는데 밑바탕이 되는 역할을 해준다는 것에서 의미가 있다. 어느 정도 미리 설계로서 틀을 갖추고 클래스를 작성할 수 있게 한다는 기능적인 측면에서 의미가 있다.

다음과 같은 예로 animal 이라는 추상 클래스를 상속받은 클래스들은 crying이라는 메소드를 구현해야 한다고 알려줌으로써 체계적인 설계를 제공한다.

```java
public class Main {

	public static void main(String[] args) {
		
		Dog dog = new Dog();
		Cat cat = new Cat();
		
		dog.crying();
		cat.crying();

	}
}
```

![image-20210423164754269](https://user-images.githubusercontent.com/80496345/116241041-733dca00-a79f-11eb-8372-595366be1dfc.png)

```java
abstract class Animal {
	
	abstract void crying();

}
public class Dog extends Animal {

	@Override
	void crying() {
		System.out.println("멍멍!");
			
	}
 
}
public class Cat extends Animal {

	@Override
	void crying() {
		System.out.println("야옹~");
	}
}
```