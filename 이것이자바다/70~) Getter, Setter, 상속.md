# 70~) Getter, Setter / 상속

**접근제한자**

객체 내부의 멤버는 자유롭게 사용 가능하나, 객체 외부에서의 사용을 제한하기 위함.

객체의 `무결성` 유지

- public : 제한 범위 없음
- protected : 같은 패키지, 자식 **객체**
- default(선언 NO) : 같은 패키지
- private : 객체 내부

> Class의 접근 제한: public / (default)
생성자의 접근 제한: public / (default) / private
필드와 메서드의 접근 제한: public / (default) / private
> 

```java
*Class를 사용하려면 import하기
import package명.클래스명;

클래스 타입의 필드를 선언할 수도 있다.
예를 들어, A라는 클래스를 다른 패키지의 클래스에서 사용하려면
A는 public이어야 하며 import한 후, 필드로 선언한다.

A a; //클래스 A타입의 a 필드 선언
```

**Getter, Setter**

데이터 무결성을 유지하기 위한 일종의 메서드

> Getter의 리턴 타입이 boolean형이라면 메서드 이름은 get이 아닌 is로 시작한다.
> 

### 싱글톤 패턴

한 클래스에 한 객체

- 생성자의 접근 제한을 private으로 하여 객체 생성을 막는 방법이 있다.

```java
private static 클래스명 singleton = new 클래스명();
//new 연산자로 객체 생성. static이기 때문에 클래스 로딩 시,
//객체가 singleton 필드에 생성 후 대입된다.
private 클래스명() {} //기본 생성자
public static 클래스명(객체타입) getInstance() {
	return singleton;
}
```

### 상속

부모 클래스가 가진 **인스턴스 멤버-필드와 메서드**를 자식 클래스가 재정의하여 사용하는 것.

`중복 코드 제거`와 `유지보수`에 이점이 있다.

**부모 클래스의 생성자 호출**

**⭐자식 객체를 생성**하면 부모 객체의 생성자가 자동 호출된 후 자식 객체가 만들어진다.

```java
//자식클래스의 기본 생성자-자식 객체 생
public 자식클래스명() {
	super(); //컴파일 시, 부모클래스의 기본 생성자
//호출이 자동적으로 이루어진다. 매개변수가 있는 
//생성자는 따로 선언해주어야 하며 자식 생성자의
//첫 줄에 위치해야 한다.
}
```

### 메서드 오버라이딩

- 부모 메서드의 선언부와 동일해야 한다.
- 접근 제한을 더 강화할 수 없다.
- 새로운 예외를 throws 할 수 없다.

> @(annotation): 컴파일 시, 한 번 더 기능 확인
> 

**final 클래스와 메서드**

- final 클래스: 상속 금지
- final 메서드: 오버라이딩 금지

**protected 접근 제한자**

필드, 메서드, 생성자에 사용 가능.

- 다른 패키지라도 자식 클래스의 객체이면 사용 가능

```java
public class C extends A {
	public C() {
		super(); //A의 생성자 호출
	}

	public void method1() {
		**this**.field = "value"; //A의 필드 사용
		**this**.method(); //A의 메서드 호출
	}
}
```

### 타입 변환: 클래스간의 타입 변환

> 선수 지식: 기본 타입의 자동 타입 변환, 강제 타입 변환
> 

**자동 타입 변환**

<aside>
🔥 부모타입 변수 = 자식타입객체;
부모타입이 더 넓은 범위

</aside>

```java
public class Cat extends Animal {
	Animal animal = new Cat();
  // == 
	Animal animal = cat;
}
```

**⭐**자식 객체를 만들면 부모 객체도 만들어진다.

참조 객체가 타입 변환을 했음에도 주소값이 무엇인지 정확히 확인해야한다. 

> 예를 들어, 부모 타입 변수에 자식 타입의 객체를 할당한다면 부모 타입 변수는 자식 객체의 주소를 참조한다.
> 

**강제 타입 변환**

<aside>
🔥 자식타입 변수 = (자식타입) 부모타입객체;

</aside>

### 다형성

> ✅ 메서드 오버라이딩 + 자식 객체의 타입 변환
> 
- 필드 다형성

```jsx
class Car {
	public Tire tire;
	
	public void run() {
		tire.roll();
	}
}

class Tire {
	public void roll() {
		System.out.println("타이어가 굴러갑니다.");
	}
}

class HankookTire extends Tire{
	@Override
	public void roll() {
		System.out.println("한국 타이어 장착");
	}
}

class KumhoTire extends Tire{
	@Override
	public void roll() {
		System.out.println("금호 타이어 장착");
	}
}

public class CarEx{
	public static void main(String[] args) {
		Car myCar = new Car();
		
		myCar.tire = new Tire(); //new HankookTire();
		//new KumhoTire(); tire의 자식 객체를 참
		myCar.run();
	}
}
```

- 매개변수 다형성: 메서드의 매개변수가 클래스 타입일 경우

매개변수의 자리에 해당 클래스 타입 자식 객체도 대입할 수 있다.

**객체 타입 확인**

`boolean result = 객체명 instanceof 타입;`

**타입:** 해당 클래스 타입의 **instanceof:** 객체인가?

> 강제 타입 변환하는 이유? **해당 클래스 타입**의 **필드**와 **메서드**를 사용하기 위해!
> 

### 추상 클래스

공통적인 필드나 메서드를 추출해서 선언한 클래스

- 객체 생성의 필요는 없음(실체 클래스는 아님)
