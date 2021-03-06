# 자바 문서 보는법

1. System, Date, Math 등 자바가 기본적으로 내장하고 있는 기능들을 library라고 한다. 우린 이를 통해 나의 프로그램을 만든다.

2. 

- Program은 시간의 순서에 따라 실행된다라는 시간이 강조된 표현.

- Application은 자바가 제공하는 기능들을 응용한다는 게 강조된 것이다.

- 즉, API(Application Programming Interface)는 자바의 기능을 응용해 시간 순서에 따라 실행하는 조작방법을 일컫는다. 따라서 우린 풍부한 프로그램을 만들기 위해 풍부한 API를 알아야 한다.

- 이를 사람을 위해 만들면 UI(User Interface)라고 한다. 쉽게 말하면, UI는 사용자가 조작하도록 만든 것이고, API는 또다른 기능이나 프로그램을 만들도록 만든 것이다. 즉, UI는 일반 사람들이, API는 프로그래머가 다른 프로그램을 만들기 위해 만든 거라고 하면 된다.

3. 자바 공식 사용설명서 보는 법

- api documentation java = 자바가 기본적으로 제공하는 library를 볼 수 있다.

- java.lang = 클래스가 속해있는 패키지의 일종.

- 클래스는 굉장히 많으므로 정리정돈되어야 한다. 따라서 패키지를 통해 정리한다. 또한 똑같은 클래스가 같은 곳에 있으면 충돌하므로 패키지라는 큰 범주를 통해 정리하는 것이다.

- 패키지는 비슷한 성격의 클래스를 모아놓은 것이다.

- 클래스는 서로 연관된 변수와 메소드를 모아놓은 것이다.

![image-20210423143710907](https://user-images.githubusercontent.com/80496345/116240997-6c16bc00-a79f-11eb-805f-2df1824e5fbd.png)

4. [인스턴스] instance

- 일회용이 아니라면 하나의 클래스를 복제해서 인스턴스를 만드는 게 더 효율적이다.

- constructor가 있으면 인스턴스를 만들 수 있다.

5. [상속] hierarchy

- 부모의 메소드를 그대로 물려받으면서 새로운 변수, 메소드를 추가한 것이 상속이다.

- class에 마우스 오른쪽 버튼 open type hierarchy를 누르면 해당 class의 inheritance를 알 수 있다.

- 부모의 변수와 메소드를 사용할 수 있고 만약 같은 method를 바꾸고 싶다면 override(덮어쓰기)해서 나의 class에서 구현할 수 있다.

- object > Writer > PrintWriter

![image-20210423143829516](https://user-images.githubusercontent.com/80496345/116240999-6caf5280-a79f-11eb-927e-0a5b3e7e3d2c.png)

```java
import java.io.FileNotFoundException;
import java.io.IOException;
import java.io.PrintWriter;
public class InstanceApp {

	public static void main(String[] args) throws IOException {
		
		//class가 1회용이 아닌 긴 맥락의 작업을 해야 할 경우 복제 즉, new를 사용하여 p1과 같은 인스턴스를 황용하여 넣어 사용.
		//class에 constructor가 있으면 아래와 같이 사용가능 Math는 1회용이기 때문에 사용하지도 않을 뿐더러 constructor가 없다. 
		PrintWriter p1 = new PrintWriter("result1.txt");
		p1.write("Hello 1");
		p1.close();
		
		PrintWriter p2 = new PrintWriter("result2.txt");
		p2.write("Hello 2");
		p2.close();
	}

}
```