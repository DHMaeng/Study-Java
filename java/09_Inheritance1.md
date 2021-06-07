# 상속

#### 상속이란? 부모가 가진것을 자식에게 물려주는것을 의미한다.

- 노트북은 컴퓨터의 한 종류다.
- 침대는 가구의 한 종류다. 혹은 침대는 가구다.
- 소방차는 자동차다.

이렇게 말할 수 있는 관계를 is a 관계 혹은 kind of 관계라고 한다.

#### Car 를 상속받은 Bus 를 class로 표현하는 방법

```java
    public class Car{

    }

    public class Bus extends Car{

    }
```

- 자바는 클래스 이름 뒤에 extends 키워드를 적고 부모클래스 이름을 적게 되면 부모 클래스가 가지고 있는 것을 상속받을 수 있게 된다.
- 상속이란 부모가 가지고 있는 것을 자식이 물려받는 것을 말한다. 즉, 부모가 가지고 있는 것을 자식이 사용할 수 있게 된다.

#### 부모클래스에 메소드 추가하기

- Car에 run()메소드를 추가

```java
    public class Car{
        public void run(){
            System.out.println("달리다.");
        }
    }
```

- Car를 상속받은 Bus 사용

```java
    public class BusExam{
        public static void main(String args[]){
            Bus bus = new Bus();
            bus.run();  
            //Bus class 는 아무런 코드를 가지지 않는다. 그럼에도 run 이라는 메소드를 사용하는데 문제가 발생되지 않는다. 
        }   
    }
```

- Bus에 메소드 추가

```java
    public class Bus extends Car{
        public void ppangppang(){
            System.out.println("빵빵");
        }       
    }
```

- Bus는 Car에서 물려받은 run메소드와 ppangppang메소드를 사용할 수 있게 된다.
- 부모가 가지고 있는 메소드외에 추가로 메소드를 선언하는 것을 확장하였다고 표현한다.





### 접근제한자

#### 접근 제한자란 클래스 내에서 멤버의 접근을 제한하는 역할을 한다.

#### 접근제한자의 종류

- public
  - 어떤 클래스든 접근할 수 있다는 것을 의미
- protected
  - 자기 자신, 같은 패키지, 서로 다른 패키지다 하더라도 상속받은 자식 클래스에서는 접근할수 있다는 것을 의미
- 접근제한자를 적지 않으면 default접근 지정자
  - 자기자신과 같은 패키지에서만 접근할 수 있다는 것을 의미
- private
  - 자기 자신만 접근할 수 있다는 것을 의미

```java
    public class AccessObj{
        private int i = 1;
        int k = 2; // default접근 제한자
        public int p = 3;
        protected int p2 = 4;
    }
```

- AccessObj를 사용하는 AccessObjExam
  - AccessObj의 필드 i 의 접근 제한자는 private이므로 다른 클래스인 AccessObjExam에서 접근할 수 없다.

```java
    public class AccessObjExam{
        public static void main(String args[]){
            AccessObj po = new AccessObj();

            System.out.println(po.i); // 컴파일 오류가 발생합니다.
            System.out.println(po.k);
            System.out.println(po.p);
            System.out.println(po.p2);
        }
    }
```

- AccessObj 와 다른 패키지에서 사용해보기
  - 패키지가 달라졌기때문에 default접근제한자로 지정된 필드 k 와 protected 접근제한자로 지정된 필드 p2 도 접근할 없다.

```java
    public class AccessObjExam{
        public static void main(String args[]){
            AccessObj po = new AccessObj();

            System.out.println(po.i); // 컴파일 오류가 발생합니다.
            System.lout.println(po.k);// 컴파일 오류가 발생합니다.
            System.lout.println(po.p);
            System.lout.println(po.p2);// 컴파일 오류가 발생합니다.
        }
    }
```

- AccessObjExam을 AccesObj로 부터 상속받도록 수정한 후 사용해 보기
  - 패키지는 다르지만 상속관계에 있으므로 protected 접근제한자로 지정된 필드 p2에 접근할 수 있다.

```java
    public class AccessObjExam extends AccessObj{
        public static void main(String[] args) {
            AccessObjExam obj = new AccessObjExam();
            System.out.println(obj.p);
            System.out.println(obj.p2);
            System.out.println(obj.k);// 컴파일 오류가 발생합니다.
            System.out.println(obj.i);// 컴파일 오류가 발생합니다.
        }
    }
```



### 추상클래스

#### 추상 클래스란 구체적이지 않은 클래스를 의미한다. 독수리, 타조는 구체적인 새를 지칭하는데 새, 포유류 같은 것은 구체적이지 않다.

#### 이런 것을 구현한 클래스를 추상 클래스라고 한다.

#### 추상 클래스 정의하기

- 추상 클래스는 클래스 앞에 abstract 키워드를 이용해서 정의한다.
- 추상 클래스는 미완성의 추상 메소드를 포함할 수 있다.
  - 추상 메소드란, 내용이 없는 메소드 이다. 즉 구현이 되지 않은 메소드이다.
  - 추상 메소드는 리턴 타입 앞에 abstract라는 키워드를 붙여야 한다.
- **추상 클래스는 인스턴스를 생성할 수 없다.**

```java
    public abstract class Bird{
        public abstract void sing(); //추상 메서드

        public void fly(){ //추상 클레스
            System.out.println("날다.");
        }
    }
```

#### 추상 클래스를 상속받는 클래스 생성하기

- 추상 클래스를 상속받은 클래스는 추상 클래스가 갖고 있는 추상 메소드를 반드시 구현해야 한다.
- 추상 클래스를 상속받고, 추상 클래스가 갖고 있는 추상 메소드를 구현하지 않으면 해당 클래스도 추상 클래스가 된다.

```java
    public class Duck extends Bird{
        @Override
        public void sing() {
            System.out.println("꽥꽥!!");
        }
    }
```

#### 사용하기

- **Bird는 추상 클래스 이므로 객체를 생성할 수 없다.**

```java
    public class DuckExam { 
        public static void main(String[] args) {
            Duck duck = new Duck();
            duck.sing();
            duck.fly();

            //Bird b = new Bird();
        }   
    }
```





### super와 부모생성자

#### class가 인스턴스화 될때 생성자가 실행되면서 객체의 초기화를 한다. 그 때 자신의 생성자만 실행이 되는것이 아니고, 부모의 생성자부터 실행된다.

#### 부모 생성자

```java
    public class Car{
        public Car(){
            System.out.println("Car의 기본생성자입니다.");
        }
    }

    public class Bus extends Car{
        public Bus(){
            System.out.println("Bus의 기본생성자입니다.");
        }

    }
```

- 생성자 테스트

```java
    public class BusExam{
        public static void main(String args[]){
            Bus b = new Bus();
        }
    }
```

- 결과

Car의 기본생성자입니다.
Bus의 기본생성자입니다.

- new 연산자로 Bus객체를 생성하면, Bus객체가 메모리에 올라갈때 부모인 Car도 함께 메모리에 올라간다.
- 생성자는 객체를 초기화 하는 일을한다.
- 생성자가 호출될 때 자동으로 부모의 생성자가 호출되면서 부모객체를 초기화 하게된다.

#### super

- 자신을 가리키는 키워드가 this 라면, 부모들 가리키는 키워드는 super
- super() 는 부모의 생성자를 의미한다.
- 부모의 생성자를 임의로 호출하지 않으면, 부모 class의 기본 생성자가 자동으로 호출된다.
- 아래 예제처럼 호출해보면 위에서 super()를 호출하지 않을때와 결과가 같다.

```java
    public Bus(){
        super();
        System.out.println("Bus의 기본생성자입니다.");
    }
```

#### 부모의 기본생성자가 아닌 다른 생성자를 호출하는 방법

- 클래스는 기본 생성자가 없는 경우도 존재한다.

```java
    public class Car{
        public Car(String name){
            System.out.println(name + " 을 받아들이는 생성자입니다.");
        }
    }
```

- Car class가 위 처럼 수정되면, Bus생성자에서 컴파일 오류가 발생한다.
- 부모가 기본생성자가 없기 때문에 컴파일 오류가 발생하게 되는 것이다.
- 이런 문제를 해결하려면 자식 클래스의 생성자에서 직접 부모의 생성자를 호출해야 합니다.

```java
    public Bus(){
        super("소방차"); // 문자열을 매개변수로 받는 부모 생성자를 호출하였다.
        System.out.println("Bus의 기본생성자입니다.");
    }
```

#### super 키워드는 자식에서 부모의 메소드나 필드를 사용할 때도 사용합니다.





### 오버라이딩

#### 오버라이딩이란 부모가 가지고 있는 메소드와 똑같은 모양의 메소드를 자식이 가지고 있는 것이다. 즉 오버라이딩이란 메소드를 재정의 하는 것이다.

#### 메소드 오버라이딩

- Car 클래스를 상속받은 Bus 클래스는 부모클래스가 가진고 있는 run() 메소드를 잘 사용한다.

```java
    //run 메소드를 가지고 있는  Car클래스 
    public class Car{
        public void run(){
            System.out.println("Car의 run메소드");
        }
    }

    //Car 를 상속받는 Bus 클래스 
    public class Bus extends Car{

    }

    public class BusExam{
        public static void main(String args[]){
            Bus bus = new Bus();
            bus.run();  //Car의 run메소드가 실행된다. 
        }
    }
```

- Bus클래스에 부모가 가지고 있는 메소드와 모양이 같은 메소드를 선언

```java
    public class Bus extends Car{
        public void run(){
            System.out.println("Bus의 run메소드");
        }
    }

    public class BusExam{
        public static void main(String args[]){
            Bus bus = new Bus();
            bus.run();  //Bus run메소드가 실행된다. 
        }
    }
```

- BusExam을 실행해 보도록 하겠습니다. "Bus의 run메소드"가 출력된다.
- **메소드를 오버라이드 하면, 항상 자식클래스에서 정의된 메소드가 호출**된다.
- 오버라이딩 한다고 해서 부모의 메소드가 사라지는 것은 아니다.
  - super 키워드를 이용하면, 부모의 메소드를 호출 할 수 있다.

```java
    public class Bus extends Car{
        public void run(){
            **super.run();**  // 부모의  run()메소드를 호출 
            System.out.println("Bus의 run메소드");
        }
    }
```



### 클래스 형변환

#### 부모타입으로 자식객체를 참조하게 되면 부모가 가지고 있는 메소드만 사용할 수 있다. 자식객체가 가지고 있는 메소드나 속성을 사용하고 싶다면 형변환 해야 한다.

#### 형변환

```java
    public class Car{
        public void run(){
            System.out.println("Car의 run메소드");
        }
    }

    public class Bus extends Car{
        public void ppangppang(){
            System.out.println("빵빵.");
        }   
    }
```

상속관계란 is a 관계라고 말했었습니다. "Bus는 Car다." 라는 관계가 성립되는 것이죠.
현실에서도 우리는 버스를 가리키면서 차다. 라고 말하곤 합니다.

- 부모타입으로 자식객체를 참조할 수 있다.
  - 부모타입으로 자식객체를 참조하게 되면 부모가 가지고 있는 메소드만 사용할 수 있다.

```java
    public class BusExam{
        public static void main(String args[]){
            Car car = new Bus();
            car.run();
            car.ppangppang(); // 컴파일 오류 발생
        }
    }
```

- ppangppang()메소드를 호출하고 싶다면 Bus타입의 참조변수로 참조해야 한다.

```java
    public class BusExam{
        public static void main(String args[]){
            Car car = new Bus();
            car.run();
            //car.ppangppang(); // 컴파일 오류 발생

            Bus bus = (Bus)car;  //부모타입을 자식타입으로 형변환 
            bus.run();
            bus.ppangppang();
        }
    }
```

- 객체들 끼리도 형변환이 가능하다. 단 상속관계에 있었을 때만 가능하다.
- 부모타입으로 자식타입의 객체를 참조할 때는 묵시적으로 형변환이 일어난다.
- 부모타입의 객체를 자식타입으로 참조하게 할때는 명시적으로 형변환 해주어 한다. 단 이렇게 형변환 할때에는 부모가 참조하는 인스턴스가 형변환 하려는 자식타입일 때만 가능하다.

```java
public class GasStation{
    public static void main(String[]args){
        GasStation gasStation = new GasStation(); //gasStation인스턴스 생성
        Suv suv = new Suv(); //suv 인스턴스 생성
        Truck truck = new Truck(); //truck 인스턴스 생성
        Bus bus = new Bus(); //bus 인스턴스 생성
        
        //gasStation에서 suv에 기름을 넣습니다.
        gasStation.fill(suv);
        
        //gasStation에서 truck에 기름을 넣습니다.
        gasStation.fill(truck);
        
        //gasStation에서 bus에 기름을 넣습니다.
        gasStation.fill(bus);
        
    }
    
    public void fill(Suv suv){
        System.out.println("Suv에 기름을 넣습니다.");
        suv.gas += 10;
        System.out.println("기름이 "+suv.gas+"리터 들어있습니다.");
    }
    
    public void fill(Truck truck){
        System.out.println("Truck에 기름을 넣습니다.");
        truck.gas += 10;
        System.out.println("기름이 "+truck.gas+"리터 들어있습니다.");
    }
    
    public void fill(Bus bus){
        System.out.println("Bus에 기름을 넣습니다.");
        bus.gas += 10;
        System.out.println("기름이 "+bus.gas+"리터 들어있습니다.");
    }
    
    public void fill(Car car){
        //참고. car.getClass().getName()은 car오브젝트가 실제로 어떤 클래스인지를 알려줍니다.
        System.out.println(car.getClass().getName()+"에 기름을 넣습니다.");

        car.gas += 10;
        System.out.println("기름이 "+car.gas+"리터 들어있습니다.");
    }
}

/*GasStation코드를 살펴보면 3개의 fill메소드가 있습니다. 매개변수로 받아들이는 3종류의 다른 차량에 대해서 기름을 넣어주는 동작을 하는것 뿐인데 3개의 중복된 코드가 들어있어서 비효율적이지요. Car클래스에 있는 gas라는 속성을 공통적으로 사용하므로 이럴경우 fill메소드의 매개변수를 Car로 하면 됩니다. 그러면 Suv, Truck, Bus클래스가 Car클래스로 형변환 되므로 하나의 fill메소드로도 같은 동작을 할 수 있습니다. */
```

