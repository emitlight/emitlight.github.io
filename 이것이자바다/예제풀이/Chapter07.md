# Chapter 07 이론+실습
출처: https://www.hanbit.co.kr/store/books/look.php?p_code=B4861113361

![페이지 원본 이것이 자바다(확인문제-정답)_3쇄_1](https://github.com/emitlight/emitlight.github.io/assets/128894133/965fa4a7-6e78-4d21-8742-55c7a7802e5f)
> 1. (1) | 자바는 다중 상속을 허용하지 않는다. private 멤버는 해당 클래스 내에서만 접근 가능하기에 자식 클래스는 부모 클래스에서 벗어났기 때문에 사용 불가하다.
> 2. (2) | 부모 클래스의 객체를 자식 클래스의 타입으로 강제 형변환할 때는 실제로 그 객체가 해당 자식 클래스의 인스턴스여야만 한다. 그렇지 않으면 실행 시간에 ClassCastException이 발생한다.
> 3. (1) | final 클래스는 상속할 수 없고, final 메소드는 오버라이딩할 수 없다.
> 4. (4) | protected 멤버를 가진 클래스의 메서드를 자식 클래스에서 오버라이딩할 수 있는 이유는 접근 권한 때문이 아니라 상속과 다형성의 원리 때문이다. 접근 권한은 같은 패키지 및 다른 패키지의 자식 클래스로 제한된다.
> 5. (2) | 부분적인 구현과 다형성을 통해 유연성을 제공하기 때문에 추상 메서드를 반드시 추상 클래스에서 구현할 필요가 없다. 자식 클래스가 추상 메서드를 구현하면 일반 클래스, 구현하고 있지 않으면 추상 클래스가 된다.

![페이지 원본 이것이 자바다(확인문제-정답)_3쇄_2](https://github.com/emitlight/emitlight.github.io/assets/128894133/5bb21797-dd57-48a0-9bc1-e87c31f69b63)
> 6. Child 클래스의 `this.name = name;` 을 `super(name);`으로 변경해야 한다.<br>name 필드는 Parent 클래스에 선언되어 있기 때문이다.
> 7. 실행 클래스에서 Child 객체를 만들었고 기본 생성자를 호출했다.<br>
> 순서: Child 기본 생성자가 실행되기 전에 `super();` Parent() 실행되기 전에 `this("대한민국");` 으로<br>
(1) Parent(String nation) 호출> (2) Parent() 호출><br>
Child()에서 `this("홍길동");`으로 다른 생성자 (3) Child(String name) 호출> (4) Child() 호출

![페이지 원본 이것이 자바다(확인문제-정답)_3쇄_3](https://github.com/emitlight/emitlight.github.io/assets/128894133/037d6bfd-58ff-4e6f-aad4-fbc151caa5fb)
> 8. snowTire라는 객체를 만든 후에 Tire 클래스 타입의 변수 tire에 할당하였다. 따라서 tire 변수도 SnowTire의 객체를 참조하고 있기 때문에 해당 클래스의 메서드를 호출한다.<br>
다형성의 한 예시로서, 자식 클래스 타입의 변수가 부모 클래스 타입의 변수에 할당되더라도 실제로는 자식 클래스의 메서드가 호출될 수 있음을 보여준다.
> 9. D, E 는 모두 B 클래스의 자식 클래스로서, 부모 클래스 타입으로 자동변환 될 수 있다. 
* **다운캐스팅(downcasting)**: 부모 클래스 타입으로 선언된 변수에 실제로는 자식 클래스의 객체가 할당되어 있을 수 있다. 이 경우 부모 클래스 타입의 변수를 자식 클래스 타입으로 강제 형변환하여 자식 클래스의 메서드나 필드에 접근한다. 
> 10. 추상클래스의 추상메서드 work()가 자식 클래스에서 재정의되지 않았다. 재정의하지 않으려면, 자식 클래스 또한 추상 클래스가 되어야 한다.

![페이지 원본 이것이 자바다(확인문제-정답)_3쇄_4](https://github.com/emitlight/emitlight.github.io/assets/128894133/e6483c50-6667-420a-a0c2-2ee28f2981ca)

![페이지 원본 이것이 자바다(확인문제-정답)_3쇄_5](https://github.com/emitlight/emitlight.github.io/assets/128894133/ca53f60e-9ac8-4689-be72-d292f7dc1302)
> 11. super
> 12. a instanceof C c (C 클래스 타입의 객체 c)

![페이지 원본 이것이 자바다(확인문제-정답)_3쇄_1](https://github.com/emitlight/emitlight.github.io/assets/128894133/e41dbb2d-7a24-4be7-9b9e-42e1743a5d58)
