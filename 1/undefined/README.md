---
description: Day.1
---

# 메서드,출력문

## 주석 

주석을 먼저 설명하면 주석을 작성할때에는 다음과 같이 사용하면 됩니다.

```java
//주석: 소스코드와 무관한 즉, 코드로 인식안됨!! => 주로 코드에 대한 설명을 작성할 떄 사용

/*
 * 여러줄
 * 주석이다.
*/

```



## 출력문

화면에 출력하고 싶을때 출력문을 통해 작업할 수 있습니다.

종류는 print, println, printf 등이 있습니다.

```java
System.out.println("Hi Everyone!!");
```



### println

println은 다음과 같이 출력한뒤 한줄을 넘겨주는 출력문입니다.

![&#xC694;&#xB7F0; &#xBAA8;&#xC2B5;&#xC73C;&#xB85C; &#xCD9C;&#xB825;&#xC774; &#xB41C;&#xB2E4;!](../../.gitbook/assets/image%20%2831%29.png)

### print

println과는 달리 문자열이 끝나는 위치에 커서가 위치하게됩니다.

즉 출력만 해주는 것이지요

그렇다면 이렇게 한번 출력해보겠습니다.

```java
System.out.print("안녕하세요");
		
System.out.println("여러분");
```

![&#xC774;&#xB7F0;&#xBAA8;&#xC2B5;&#xC73C;&#xB85C; &#xCD9C;&#xB825;&#xC774; &#xB41C;&#xB2E4;.](../../.gitbook/assets/image%20%2815%29.png)

종합해보자면 각 클래스마다 역할별로 나눠서 관리하게 되는데,

각 클래스 안에서도 해당 코드들도 각 기능별로 메소드를 따로 작성합니다!!



그렇다면 기능단위로 메소드를 작성한 예시를 만들어보세요!

단, 클래스마다 무조건 메인 메소드를 포함할 필요는 없답니다.



## 메서드 

기능 ==메소드를 의미합니다. 

한 클래스 안에 여러개의 메소드를 만들 수 있습니다.

 프로그램 실행시 먼저 실행되는 메소드 ==main메소드라고 지정합니다.

```java
public class HelloWorld {
	public static void main(String[] args) {
		System.out.println("Hi Everyone!!");
	}
}
```

### 

### 일반메소드 

일반메소드는 아래와 같은 방법으로 작성합니다.

```java
public void 메소드명(){ }
```

> 클래스명은 대문자로 시작하는게 권장이지만, 
>
> 메소드명은 소문자로 시작하는 것을 권장해요.

```java
public class A_MethodPrinter {
		public void methodA(){
				System.out.println("methodA 호출!")
		}
}
```

위에서 말한것처럼 한개의 클래스에 메소드를 하나만 작성해야 하는것은 아닙니다.  

아래 예제와 같이 여러개를 작성할 수도 있습니다.

```java
public class A_MethodPrinter {
		public void methodA(){
				System.out.println("methodA 호출!")
		}
		
		public void methodA(){
				System.out.println("methodA 호출!");
		}
	
		public void methodB() {
			  System.out.println("methodB 호출!");
	  }
	
	  public void methodB() {
		    System.out.println("methodC 호출!");
	  }
}
```

그러나 메인메소드가 없기 때문에 실행을 할수는 없습니다.

 - 실행을 위해 실행담당의 RunA클래스를 만들어주세요

### 

### 메인메소드 & 실행용 클래스

위의 메소드들은 first패키지 안에 작성이 되었지만 보통 실행용 클래스를 작성할 때에는 run패키지 안에 작성하는 것이 국룰입니다.

참고로 패키지명 또한 메소드처럼 소문자로 시작해주는 것이 좋습니다.

![&#xC774;&#xB807;&#xAC8C; &#xD574;&#xC8FC;&#xC2DC;&#xBA74; &#xB418;&#xACA0;&#xC8E0;?](../../.gitbook/assets/image%20%2810%29.png)

메인메소드는 이런식으로 보통 작성합니다

```java
public static void main(){
}
```

 아래와 같이 메인메소드를 작성해서 제대로 작동이 되는지 확인해보세요

```java
public class RunA {
  public static void main(String[] args) {
	  System.out.println("프로그램실행!!");
  }
}

```

그렇지만 아까 작성한 methodA 다른 클래스에 작성이 되었습니다.

이러한 외부의 메소드 어떻게 불러와야 하는지 알아보겠습니다.

### 

### 메소드 호출 

1\) 실행할 메소드가 있는 클래스를 아래 양식으로 생성\(new\)해줘야합니다.

```java
불러클래스명 사용할이름= new 클래스명();
```

2\) 메소드 실행\(호출\)해줍니다.

```java
사용할이름.실행할메소드명();
```

#### 단 ! 이렇게 하면 같은 패키지 즉 폴더에 있는 클래스에만 적용이 가능합니다!



만약 com폴더안에kh안에 first패키지 안에 있는 메서드를 가져온다고 해보면

```java
com.kh.first.A_MethodPrinter a 
= new com.kh.first.A_MethodPrinter();
```

이렇게 절대경로를 작성해주면 해결할 수 있지만 너무 길죠?

import를 이용해 상위에서 선언을 해주면 되는데 아래와 같습니다.

```java
import com.kh.first.A_MethodPrinter;
```

선언을 한뒤 a라는 이름으로 호출하도록 하겠습니다

```java
//선언
import com.kh.first.A_MethodPrinter;

public class RunA {
  public static void main(String[] args) {
	  System.out.println("프로그램실행!!");
	  
	  //호출
		A_MethodPrinter a = new A_MethodPrinter();
  }
}

```

클래스를 호출했다면 그뒤에는 클래스안의 메소드를 사용할수있겠죠?

```java
//선언
import com.kh.first.A_MethodPrinter;

public class RunA {
  public static void main(String[] args) {
	  System.out.println("프로그램실행!!");
	  
	  //클래스를 a라는 이름으로 호출
		A_MethodPrinter a = new A_MethodPrinter();
		//a클래스 안에있는 methodA호출!!
		a.methodA();
  }
}

```

결과는 아래와 같습니다.

![](../../.gitbook/assets/image%20%2811%29.png)

보이는 것과 같이 커서도 println으로 인해서 줄바꿈이 된 것을 확인할 수 있습니다.

그렇다면 methodA호출만으로도 A,B,C가 모두 호출되도록 수정해볼까요?

```java
public class A_MethodPrinter {

	public void methodA(){
		System.out.println("methodA 호출!");
		methodB(); 
		methodC();
	}
	
	public void methodB() {
		System.out.println("methodB 호출!");
	}
	
	public void methodC() {
		System.out.println("methodC 호출!");
	}
	
}
```

A\_MethodPrinter 클래스로 이동해서 methodA안에서 다른 메소드를 실행하면 됩니다.

