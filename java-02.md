# 참조 자료형

**참조 자료형이란?** 객체의 번지(주소)를 참조하는 자료형

메모리에 저장되는 값이 객체의 주소값이다.

Stack과 Heap 모두 JVM의 **Runtime Data Area**에 있다.

**Stack :** 기본 자료형의 실제 값, 참조 자료형의 주소 값

- Frame의 push & pop 발생

**Heap :** 참조 자료형의 주소 값에 대응하는 **객체 혹은 배열**

**Static(Method) :** 모든 스레드가 공유하는 영역.

클래스별로 런타임 상수풀(runtime constant pool), 필드(field) 데이터, 메소드(method) 데이터, 메소드 코드, 생성자(Constructor) 코드 등을 분류해서 저장한다.

**참조 변수의 ==, != 연산**

동일한 객체 참조 여부 확인하는 연산자

= 동일한 주소값을 가졌는지 확인하는 연산자

<aside>
💡 String : 문자열이 동일하다면 동일한 객체를 참조한다.
그러나 **new 생성자**로 새로운 객체를 만들면 내용이 동일해도 다른 참조 값을 가진다.

</aside>

- `변수명.equals(비교할 변수명);` 메소드로 String 타입의 내용 문자열이 같은지 확인할 수 있다.

참조형 변수의 null 초기화 : 힙 영역의 객체를 참조하지 않는다.

참조 값(Stack에 위치-**주소**)은 없을 수 있지만 참조할 객체(Heap에 위치)가 없다면 NPE(NullPointerException) 오류가 발생한다.

String 객체의 값이 “”이라면 힙 영역의 “”을 참조하는 것이고, 해당 주소가 생기기 때문에 NPE오류가 발생하지 않는다.

### 문자열 내장메서드

```jsx
// equals()
String a = "Hello";
String b = new String("Hello");

a.equals(b) // true

String a = "Hi, I am Tory.";
a.indexOf("I"); // 4
a.contains("util"); // false
a.charAt(6); // "a"
a.replaceAll("Tory", "Hayoung"); // "Hi, I am Hayoung."
a.substring(0, 2); // "Hi"
a.toUpperCase(); // "HI, I AM TORY."
a.concat(" Cat"); // "Hi, I am Tory. Cat"

String b = "a, b, c, d";
b.split(","); // {"a", "b", "c", "d"}
★그러나 System.out.println 구문으로 b.split(",")을 출력
한다면 예상치 못한 값을 보게 되는데, 이는 split메서드가
배열을 반환하기 때문이고 배열 자료형은 참조타입이기 때문에
**stack영역의 주소값**을 출력하게 된다.

[해결방법]
String b = "a, b, c, d";
String[] result = b.split(",");

// 힙 영역에 있는 배열의 값을 확인한다.
System.out.println(Arrays.toString(result))
// [a, b, c, d] 한꺼번에 출력한다.
```

### 문자열 포맷팅

```jsx
String name = "Hayoung";
int age = 27;

String.format("%s의 나이는 %s 입니다.", name, age);
```

**JAVA에서 문자열을 다루는 클래스**

- String
- StringBuffer [문자열의 연산]
- StringBuilder [문자열의 연산]

```jsx
String example = "";
example += "순서";
example += "대로";
System.out.println(example); // "순서대로"

StringBuilder builder = new StringBuilder();
builder.append("hi");
System.out.println(builder.toString());

StringBuffer buffer = new StringBuffer();
buffer.append("nice");
System.out.println(buffer.toString());
```

내장 메서드

- append(추가할 문자열)
- insert(인덱스, 추가할 문자열)
- substring(시작 인덱스, 끝 인덱스)

<aside>
💡 (참고) StringBuffer는 멀티스레드 환경에서 thread safe 하다는 장점이 있고, StringBuilder는 성능이 우수하다는 장점이 있습니다.

</aside>

### 배열

선언 시, 자료형 또는 변수명 뒤에 대괄호를 붙인다.

`int[] firstArray;`

`int firstArray[];`

※ 자료형의 종류가 아니라, 동일한 자료형의 집합이다.

배열의 크기를 먼저 설정한 뒤, 배열 변수를 대입할 수 있다.

```jsx
String[] gender = new String[2];
gender[0] = "여성";
gender[1] = "남성";
// 위와 아래 코드의 결과는 같다.
String[] gender = {"여성", "남성"};
```

인덱스를 통해 배열의 특정 요소에 접근할 수 있다.

`System.out.println(gender[0]);` 결과값: “여성”
### 자료형 타입을 확인하려면?

`String(목적 자료형인지).class.isInstance();`
