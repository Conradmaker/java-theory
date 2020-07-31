# 생성자부

먼저 생성자부가 어떻게 생겼는지 볼까요?

```java
//기본생성자
public User(){  };
```

기본생성자는 위처럼 아무것도 표현하지 않습니다.

자 그럼 이 기본생성자는 어디서 사용했었을까요?

우리는 분명 기본생성자를 자주 사용했습니다.

실행클래스에서 메소드를 호출하기 전에 무엇을 작성했죠?

```java
User u1 = new User();
```

기억이 나시죠?

이렇게 메인메소드에서 호출했던 클래스가 곧 생성자입니다.

기본생성자에는 클래스명과 이름을 같게 해야한다는 특징이 있습니다.

```java
//User.java 클래스

//표현법
public User(){

}
```

{% hint style="warning" %}
항상 클래스명과 같게 작성 즉 대문자로 시작해야 하며, 

반환형을 넣어주게 된다면 오류가 나타납니다.

!!메소드와 헷갈리면 큰일납니다!!

추가적으로 아래와 같이 매개변수생성자를 명시적이라도 작성해놓으면 자동으로 JVM이 작성해주지 않습니다.

또한 파라미터 값을 넣어줄 수도 있습니다.
{% endhint %}

그렇다면 생성자를 작성하지 않다고 실행되는데 왜 작성할까요?

### 기본생성자\(매개변수X\)

* 단지 객체 생성만을 위한 목적으로 사용
* 기본 생성자를 작성 안해놓으면 JVM이 작성해준다.

### 매개변수 생성자

```java
public User(String userId,String userPwd, String userName){
    this.UserId = userId;
    this.UserPwd = userPwd;
    this.UserName = userName;
}

//메인메소드
User u1 = new User("yhg0337","1234","conrad")//ID,비번,이름
```

먼저보니까 무슨느낌인가요?

코드에서 알 수 있듯이 setter함수를 여러번 작성할 필요 없이 한번에 변수를 초기화해주는 생성자입니다.

{% hint style="warning" %}
반드시 파라미터에 나열된 순서와 실행시 순서가 같아야 합니다!
{% endhint %}

추가적으로 더 많은 사용자를 추가하고 싶다면 재사용 할수도 있습니다.

```java
public User(String userId,String userPwd, String userName, int age, char gender){
    this(userId,userPwd,userName);
    this.age;
    thid.gender;
}
```

단 반드시 첫줄에 작성해줘야만 한답니다!

이번에는 사용자가 입력한 값을 통해 변수로 만들어보겠습니다.

```java
public class Run {
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in)l
      System.out.print("아이디:");
        String userId = sc.nextLine();

      System.out.print("아이디:");
        String userPwd = sc.nextLine();

      System.out.print("아이디:");
        String userName = sc.nextLine();

      System.out.print("아이디:");
        int userAge = sc.nextInt();
        sc.nextLine();

      System.out.print("성별 (남/여):");
      char userGender = sc.nextLine().charAt(0);

      User u1 = new User(userId,userPwd,userName,userAge,userGender);


    }
}
```

이렇게도 사용이 가능하겠죠??



이번에는 기본생성자를 통해 회원가입툴을 만들어볼까요?

```java
public static void main(String[] args){

        //기본생성자
        User u4 = new User();

        Scanner sc = new Scanner(System.in)l
      System.out.print("아이디:");
       u4.setUserId(sc.nextLine());

      System.out.print("비번:");
        u4.setUserPwd(sc.nextLine());
 
      System.out.print("이름:");
      u4.setUserName(sc.nextLine());

      System.out.print("나이:");
      u4.setUserAge(sc.nextInt());
        sc.nextLine();

      System.out.print("성별 (남/여):");
      u4.setUserGender(sc.nextLine().charAt(0));
}
```

이렇게 setter메소드를 이용해 값을 바로 대입시켜줄 수도 있습니다.

