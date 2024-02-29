# 58~67) Object Oriented Program

객체는 속성(필드)과 동작(메서드)로 이루어진다.

**객체 간의 관계**

사용, 상속, 집합 관계

**특징**

**캡슐화 | 상속 | 다형성**

**클래스 선언**

**객체 생성**을 위한 설계도 - 필드, 생성자, 메서드를 정의한다.

- public 클래스 하위의 클래스는 public이 될 수 없으며 상위의 public 클래스와 밀접한 관련이 있는 경우에 주로 작성한다.

<aside>
🔥 **클래스의 종류** : 라이브러리 클래스(객체 생성을 위한 설계도 역할), 실행 클래스(메인 메서드가 있는 클래스)

</aside>

**필드의 종류**

- 고유 데이터
- 상태 데이터: 가변한다.
- 부품 데이터(집합 관계)

<aside>
🔥 필드에 초기값을 설정하지 않으면 default 값이 데이터 타입에 따라 들어간다.

</aside>

필드를 사용-생성 또는 수정하는 대상: **생성자** | **메서드**

### 생성자

객체를 초기화한다. 즉, 필드를 초기화하거나 메서드를 호출한다. *“객체를 사용할 준비를 한다.”*

**생성자 오버로딩**

매개변수의 타입과 개수, 순서가 다른 여러 개의 생성자를 선언하는 것

🤔오버로딩 하는 이유? 매개값으로 객체 필드를 **다양하게 초기화**하기 위해!

**다른 생성자 호출**

```java
public class Car {
	//필드
	String model;
	String color;
	int speed;	
	
	Car(String model) {
		this(model, "은색", 250); //생성자 첫 줄에 작성해야 한다.
	}

	//공통 초기화, 모든 필드를 매개변수로 갖는다.
	public Car(String model, String color, int speed) {
		this.model = model;
		this.color = color;
		this.speed = speed;
	}
}
```

- `**this(**매개변수 값1, 2, 3...**)**`를 사용하는 것

**가변길이 매개변수**

`반환타입 메서드명(매개변수 타입 **...** values)`

- **values: 배열의 이름**
- 매개변수로 배열을 가진다.

**배열을 매개변수로 이용하는 메서드 ⇃⇂**

`int result = sum(new int[] {1,2,3});` 

```java
//라이브러리(설계도) 클래스

public class GaByun {

//**int ... values : int 형의 값이 여러개 매개변수로 들어감
//즉, 배열의 형태로도 변환할 수 있다.**
	int sum(**int ... values**) {
		int sum = 0;

		for (int i = 0; i < values.length; i++) {
			sum += values[i];
		} return sum;
	}
}

//실행 클래스
public class GaByunEx {
	public static void main(String[] args) {
		GaByun gb = new GaByen(); //객체 사용하기 위한 생성
		
		int result = gb.sum(5,4,3,2,1);
		System.out.println(result); // 15

		int[] values = {1,2,3,4};
		int result_2 = gb.sum(values);
		System.out.println(result_2); // 10

		//메서드 호출과 동시에 배열 객체 생성하여 return하기
		int result3 = gb.sum(new int[] {3,3,3,3});
		System.out.println(result3); // 12
	}
}
```

`if (조건식)`: 조건식은 true || false를 조건으로 설정. 따라서 boolean형을 반환하는 **메서드**를 입력할 수도 있다.

- 오버로딩 : **매개변수**를 달리한다.

**메서드 오버로딩**: 다양한 매개변수 값을 받기 위하여

- 리턴 타입 변해도 된다.

**📌 인스턴스 멤버**: 객체가 있어야만 사용할 수 있는 멤버. (필드/메서드). 필드는 **포함**되고 메서드는 **소속**된다.

- 필드는 힙 영역에 객체와 함께 저장
- 메서드는 메모리 효율을 위해 메서드 영역에 저장되어 객체를 통해 사용한다.

**📌 정적 멤버:** 메서드 영역에 클래스와 함께 저장되는, 객체 생성 필요 없이 바로 사용 가능한 필드와 메서드

**static method**: 인스턴스 멤버를 선언부 또는 실행 블록안에서 사용하지 않는 메서드
