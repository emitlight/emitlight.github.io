# Chapter 06 이론+실습
#### 출처: https://www.hanbit.co.kr/store/books/look.php?p_code=B4861113361
![페이지 원본 이것이 자바다(확인문제-정답)_3쇄 - 복사본_1](https://github.com/emitlight/emitlight/assets/128894133/287801f2-a1a6-4774-86d1-1efdf6a2cc84)
> 1. (3) | 클래스의 접근 제어자가 public이라면, 다른 패키지의 클래스에서도 객체 생성을 통해 해당 멤버에 접근할 수 있으므로 한 클래스에서 다수의 객체를 생성할 수 있다는 것을 알 수 있다.
> 2. (4) | 로컬 변수는 해당 변수가 선언된 블록 내에서만 유효한 변수이다. 이 블록은 메서드, 생성자 또는 다른 코드 블록 중 하나일 수 있다.
> 3. (4) | 클래스는 일반적으로 데이터와 해당 데이터를 조작하는 방법을 함께 포함하여 데이터의 일관성과 안정성을 유지하기 위해 캡슐화하지만 데이터(필드)만을 가지는 경우도 있을 수 있다.
> 4. (3) | 생성자나 메서드에서 필드를 참조할 때는 해당 필드가 그 이전에 선언되어 있어야 하나, 참조하지 않는 경우에는 생성자 이후에 선언되어 있어도 자바 컴파일러가 이를 인식한다.
필드를 생성자 이후에 선언한다고 해도, 생성자는 객체 생성 시 필드를 초기화하기 때문에 해당 필드는 여전히 객체의 생성에는 영향을 주지 않는다.
> 5. (1) | 객체 생성을 위해서는 new연산자를 이용한 생성자를 호출해야만 한다.

![페이지 원본 이것이 자바다(확인문제-정답)_3쇄 - 복사본_2](https://github.com/emitlight/emitlight/assets/128894133/8faaf617-5be9-458f-adac-ec09afb86ed6)
> 6. (4) | 메서드 오버로딩은 동일한 이름을 가진 메서드의 매개변수 타입, 순서, 개수 등을 다르게 정의하는 것이다. 이를 통해 같은 이름의 메서드를 여러 개 정의하여 다양한 매개변수를 받을 수 있다.
> 7. (2) | 리턴 타입이 아니라 매개변수를 달리 하면 오버로딩의 조건을 만족한다.
> 8. (2) | 정적 블록은 클래스가 로드될 때 실행되는 블록으로, 주로 클래스 초기화 작업에 사용된다. 주로 정적 필드의 초기화나 복잡한 초기화 로직에 사용된다.
> 9. (2) | 필드를 선언할 때 직접 초기화하거나, 인스턴스 초기화 블록 또는 정적 초기화 블록에서 초기화해야 한다.
> 10. (4) | 클래스를 다른 패키지로 옮길 때는 패키지 선언을 올바르게 수정하고, 클래스 파일도 해당 패키지의 디렉토리 구조에 맞게 위치시켜야 한다.

![페이지 원본 이것이 자바다(확인문제-정답)_3쇄 - 복사본_3](https://github.com/emitlight/emitlight/assets/128894133/18dc3a56-1b07-4c1e-b45c-57764102ee45)
> 11. (3) | default 접근 제어자의 제한은 패키지 기준이다.
> 12. 필드, 생성자, 메서드
생성자: 클래스 이름과 동일하며 매개변수를 가지지만 리턴 타입을 가지지 않는다.
메서드: 리턴 타입을 가지며 메서드명이 소문자 동사로 시작한다.
> 13. 코드 참조
```java

public class Member{
  //필드 선언
  String name;
  String id;
  String password;
  int age;

  Member(String name, String id) {
    this.name = name;
    this.id = id;
  }

  public static void main(String[] args) {
    Member user1 = new Member("홍길동", "hong");
    System.out.println(user1.name); //홍길동
    System.out.println(user1.id); //hong
  }

}

```

![페이지 원본 이것이 자바다(확인문제-정답)_3쇄 - 복사본_4](https://github.com/emitlight/emitlight/assets/128894133/b6700c73-9a4c-443d-bbb8-6fc5a756b8a1)
> 15. 코드 참조
```java

public class MemberService {
  boolean login(String id, String password) { //default 접근 제어자
    if(id.equals("hong") && password.equals("12345")) { //String은 참조 타입이므로 equals()로 주소값이 아닌 내용을 비교
      return true;
    } return false;
  }

  void logout(String id) {
    System.out.println(id + "님이 로그아웃 되었습니다."); //단순 출력 메서드
  }

  public static void main(String[] args) {
    MemberService memberService = new MemberService();

    boolean result = memberService.login("hong", "12345"); //login()의 리턴 타

    if(result) {
      System.out.println("로그인 되었습니다.");
      memberService.logout("hong");
    } else {
      System.out.println("id 또는 password가 올바르지 않습니다.");
    }
  }

}

```
> 16. 코드 참조조
```java

public class Printer {
  void println(int value) {
    System.out.println(value);
  }

  void println(boolean value) {
    System.out.println(value);
  }

  void println(double value) {
    System.out.println(value);
  }

  void println(String value) {
    System.out.println(value);
  }

  public static void main(String[] args) {
    Printer printer = new Printer();
    printer.println(10);
    printer.println(true);
    printer.println(5.7);
    printer.println("홍길동");
  }

}

```

![페이지 원본 이것이 자바다(확인문제-정답)_3쇄 - 복사본_5](https://github.com/emitlight/emitlight/assets/128894133/a8fb73b6-1855-4fd5-a53c-65fa95a90163)
> 17. 코드 참조
```java

public class Printer {
  static void println(int value) {
    System.out.println(value);
  }

  static void println(boolean value) {
    System.out.println(value);
  }

  static void println(double value) {
    System.out.println(value);
  }

  static void println(String value) {
    System.out.println(value);
  }

  public static void main(String[] args) {
    Printer.println(10);
    Printer.println(true);
    Printer.println(5.7);
    Printer.println("홍길동");  
  }

}

```
> 18. 코드 참조
```java

public class ShopService{
  private static ShopService singleton = new ShopService(); //객체 *주소값을 singleton에 저장
  private ShopService(){} //private 접근 제어자로 생성자 사용 및 객체 값 초기화 제한
  public static ShopService getInstance() {
    return singleton;
  }

  public static void main(String[] args) {
    ShopService obj1 = ShopService.getInstance();
    ShopService obj2 = ShopService.getInstance();

    if (obj1 == obj2) {
      System.out.println("같은 ShopService 객체입니다.");
    } else {
      System.out.println("다른 ShopService 객체입니다.");
    }
  }

}

```
> 19. 코드 참조
```java

public class Account{
  private int balance;
  public static final int MIN_BALANCE = 0;
  public static final int MAX_BALANCE = 1000000;

  public int getBalance() {
    return balance;  
  }

  public void setBalance(int balance) {
    if(balance < MIN_BALANCE) {
      return;
    }
    else if(balance > MAX_BALANCE) {
      return;
    }
    else {
      this.balance = balance;
    }  
  }

  public static void main(String[] args) {
    Account account = new Account();

    account.setBalance(10000);
    System.out.println("현재 잔고: " + account.getBalance()); //현재 잔고: 10000

    account.setBalance(-100);
    System.out.println("현재 잔고: " + account.getBalance()); //현재 잔고: 10000

    account.setBalance(2000000);
    System.out.println("현재 잔고: " + account.getBalance()); //현재 잔고: 10000

    account.setBalance(300000);
    System.out.println("현재 잔고: " + account.getBalance()); //현재 잔고: 300000
  }

}

```
![페이지 원본 이것이 자바다(확인문제-정답)_3쇄 - 복사본_6](https://github.com/emitlight/emitlight/assets/128894133/f4e005e6-c693-4638-a3f6-e42f47812dff)
> 20. 코드 참조
```java

public class Account{
  //필드에 직접 접근하는 초기화 보호
  private String accountNum;
  private String owner;
  private int balance;

  //생성자로 필드 값을 입력받아서 초기화한다.
  public Account(String accountNum, String owner, int balance) {
    this.accountNum = accountNum;
    this.owner = owner;
    this.balance = balance;
  }

  //각 필드에 getter와 setter메서드 선언
  public String getAccountNum() {
    return accountNum;
  }
  public void setAccountNum(String accountNum) {
    this.accountNum = accountNum;
  }

  public String getOwner() {
    return owner;
  }
  public void setOwner(String owner) {
    this.owner = owner;
  }

  public int getBalance() {
    return balance;
  }
  public void setBalance(int balance) {
    this.balance = balance;
  }
}

```
```java

public class BankApplication{
  //Account 객체를 길이가 100인 배열에서 관리, 100개의 요소 모두가 null로 초기화되어 있다.
  private static Account[] accountArray = new Account[100];
  private static Scanner scanner = new Scanner(System.in); //정적 필드로 Scanner 객체 생성

  public static void main(String[] args) {
    boolean run = true; //지역 변수 선언
    while(run) {
      System.out.println("--------------------------------------");
      System.out.println("1.계좌생성 | 2.계좌목록 | 3.금 | 4.출금 | 5.종료");
      System.out.println("--------------------------------------");
      System.out.print("선택> ");

      int option = Integer.parseInt(scanner.nextLine());
      if(option == 1) { //옵션을 입력받아서 while문이 실행되는 동안 각 메서드가 작동하게 한다.
        createAccount(); 
      }  else if(option == 2) {
          accountList();
      }  else if(option == 3) {
          deposit();
      } else if(option == 4) {
          withdraw();
      } else if(option == 5) {
          run = false;
          System.out.println("프로그램 종료");
      }
    }
  }
  //1.계좌생성
  private static void createAccount() {
    System.out.println("----------");
    System.out.println("계좌생성");
    System.out.println("----------");

    System.out.println("계좌번호: ");
    String accountNum = scanner.nextLine(); //createAccount 메서드의 지역변수 선언

    System.out.println("계좌주: ");
    String owner = scanner.nextLine();

    System.out.println("초기입금액: ");
    int balance = Integer.parseInt(scanner.nextLine());

    //⭐지역변수를 생성자에 대입하여 Account 객체 필드 초기화,
    //위에서 입력받은 지역변수를 Account 클래스에서 선언한 생성자의 매개변수로 대입
    Account newAccount = new Account(accountNum, owner, balance);

    for(int i = 0; i < accountArray.length; i++) {
      if(accountArray[i] == null) {
        accountArray[i] = newAccount; //생성자로 인해 업데이트된 필드를 가진 객체의 주소를 가리키게 한다.
        System.out.println("결과: 계좌가 생성되었습니다.");
        break; //객체 배열을 반복하며 자리가 비어있는 곳(null)을 채우면 break문으로 반복을 중지한다.
      }
    }
  }
  //2.계좌목록
  private static void accountList() {
    System.out.println("----------");
    System.out.println("계좌목록");
    System.out.println("----------");

    for(int i = 0; i < accountArray.length; i++) {
      Account account = accountArray[i]; //Account 타입의 account 변수에 객체 배열의 각 요소를 반복하며 대입한다.

      if(account != null) { //객체 배열에 주소값이 할당되어 있다면
        System.out.print(account.getAccountNum());
        System.out.print("     ");
        System.out.print(account.getOwner());
        System.out.print("     ");
        System.out.print(account.getBalance());
        System.out.println();
      }
    }
  }
  //3.예금
  private static void deposit() {
    System.out.println("----------");
    System.out.println("예금");
    System.out.println("----------");

    System.out.print("계좌번호: ");
    String accountNum = scanner.nextLine();

    System.out.print("예금액: ");
    int money = Integer.parseInt(scanner.nextLine());

    Account account = findAccount(accountNum); //findAccount() 메서드 선언

    if(account == null) {
      System.out.println("결과: 계좌가 없습니다.");
      return;
    } //💛 deposit() 메서드에 account 객체가 정의되어 있지 않아 보이지만, findAccount의 반환값이 account 객체이며
      //이것이 deposit() 메서드의 account 객체에 할당된다. 그래서 사용할 수 있는 것이다.
    account.setBalance(account.getBalance() + money);
    System.out.println("결과: 예금 성공");
  }

  private static void withdraw() {
    System.out.println("----------");
    System.out.println("출금");
    System.out.println("----------");

    System.out.print("계좌번호: ");
    String accountNum = scanner.nextLine();

    System.out.println("출금액: ");
    int money = Integer.parseInt(scanner.nextLine());

    Account account = findAccount(accountNum);
    if(account == null) {
      System.out.println("결과: 계좌가 없습니다.");
      return;
    }
    account.setBalance(account.getBalance() - money);
    System.out.println("결과: 출금 성공");
  }

  private static Account findAccount(String accountNum) {
    Account account = null;
    for(int i = 0; i < accountArray.length; i++) {
      if(accountArray[i] != null) {
        String dbAccountNum = accountArray[i].getAccountNum();
        if(dbAccountNum.equals(accountNum)) { //여기서 accountNum은 메서드의 매개변수
          account = accountArray[i];
          break;
        }
      }
    } return account; //💛
  }

}
```
