# Java

> ☕ Java의 시작
> 

### JVM : 가상의 운영체제라고 할 수 있다.

JAVA는 JVM이라는 별도의 실행 도구가 있어서, 다른 운영체제에 독립적이다.

<aside>
💡 JVM 구성 : Garbage Collector / Execution Engine / Class Loader(기계어 번역) / **Runtime Data Area**
자바의 실행 과정 : 소스파일→컴파일(Class file로 변환)→JVM에서 실행(기계어)→운영체제→하드웨어

</aside>

Runtime Data Area : Method+Heap+Stack+PC Reg.+Native Method Stack

※ 클래스명과 소스파일명이 같아야 한다.

**메서드의 형태**

- 접근제어자[public|private|protected]
- [static] : 정적 메서드. 인스턴스 선언 없이(객체 생성 없이) 클래스명.메서드명 형태의 사용이 가능하다.
- [리턴 자료형|void]
- [메서드명]+(입력자료형과 매개변수)

변수에는 하나의 값만 저장할 수 있으나, 배열은 여러 개가 가능하다.

**변수의 사용**

1. 변수의 선언 → **자료형**과 **변수 이름**

`unexpected token` : 예약어를 변수 이름으로 선언하여 컴파일 에러 발생

1. 변수의 초기화 : 변수에 값(value)을 넣는 것.
2. **클래스** 또는 **메소드**의 **중괄호 블록** 내에서 선언 및 사용된다. 

<aside>
💡 메소드 블록 내에 선언된 변수는 로컬 변수(Local Variable)이다. 
메소드 실행이 끝나면 메모리에서 자동으로 삭제된다.

</aside>

**컨벤션**

- Class(대문자+대문자)
- methodAndVariable(소문자+대문자)
- CONSTANT_1(대문자, 구분자_)

변수의 자료형은 사용 도중에 변경 불가능하다.

**기본 타입**

- 정수형에서는 값의 범위를 넘어가면 overflow가 발생한다.
- char 타입은 ‘
- unicode 즉, 문자형 알파벳을 int형으로 선언하면 대응되는 숫자값을 알 수 있다.
- char형을 빈 문자형으로 초기화하면 에러가 발생하지만 String은 빈 문자열로 초기화할 수 있다. 참조 타입이라서 그런가?
- 정수와 실수 타입은 메모리 사용 크기는 같지만 저장 방식이 다르다.
- double과 float는 소수점의 정밀도가 다르다.

**참조 타입**

- String은 “를 사용
- Class, Array, Enum
- 참조 타입의 초기화 :

`Calculator cal_1 = new Calculator;`

해석 : Calculator 라는 형식의 참조 자료형 이름은 cal_1이고 해당 형식을 새로운 객체로 초기화한다.

new : 생성자 method

**타입의 변환**

1. 명시적 변환 : 강제 타입 변환이라고도 한다. `(**캐스팅** 하려는 자료형) 변수;`

※ 손실 값이 없도록 주의해야 함.

1. 묵시적 변환 : **작은** 타입의 값을 **큰** 타입 값의 변수에 할당하면 자동적으로 발생

<aside>
💡 short와 char 모두 2byte의 크기를 가지지만 char 형은 음수가 포함되지 않기 때문에
short 자료형보다 더 많은 숫자 값이 들어간다. 
short의 범위 : -32768~32767
char의 범위 : 0~65535
※ short에도 char형식의 문자를 할당할 수 있다. ex. `short shortVal = ‘A’;`

</aside>

기본 자료형을 Wrapper Class의 객체로 변환하는 이유? **boxing과 autoboxing**

1. null값을 허용하기 위해
2. 참조 객체의 내부 메서드를 사용하기 위해

※ autoboxing과 unboxing은 내부적으로 추가 연산 작업을 거치기 때문에 성능 저하 가능성이 있다.

**parse래퍼클래스:** 문자열→기본 타입

ex. `Integer(래퍼타입).parseInt()(변환할 **기본형**());`

**숫자를 문자형(String)으로**

- Integer.toString();

String 자체가 참조타입이나, 기본형으로 변환하는 것처럼 하는 메서드.

- String.valueOf();
- 숫자 + “” (빈 문자열)

**valueOf():** 래퍼 클래스로 변환

ex. `Integer(변환할 **참조형**).valueOf();`

**null**

- toString(); 오류 발생. 기본형 타입에 String은 물론 null도 없어서!
