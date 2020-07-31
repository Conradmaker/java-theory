---
description: day.3
---

# 유저의 입력을 변수에 기록

사용자가 키보드로 입력한 값을 변수에 기록하는 방법을 알아보도록 하겠습니다.



먼저 사용자에게 간단한 인적사항 입력 받은 후 출력하는 메소드를 작성해보겠습니다.

## Scanner클래스

Scanner 클래스의 메소드를 사용하면 되는데, 

먼저 클래스 생성후 메소드를 호출해주겠습니다.

```java
import java.util.Scanner;

public class C_keyboardInput {
		public void inputScanner1() {
				Scanner sc = new Scanner(System.in);
	  }
}
```

{% hint style="info" %}
Scanner 클래스는 자바 내장클래스로아래와 같이 선언해주면 됩니다.

```java
import java.util.Scanner;
```

System.in 은 컴퓨터로 전달하겠다는 것을 의미합니다.
{% endhint %}

다음으로 입력받고자 하는 내용을 먼저 출력해 입력을 유도하겠습니다.

```java
import java.util.Scanner;

public class C_keyboardInput {
		public void inputScanner1() {
				Scanner sc = new Scanner(System.in);
				System.out.print("이름을 입력해주세요:");
	  }
}
```

사용자가 이름을 입력하면 그 내용은 메모리에 저장되기 전에 버퍼라는 공간에 들어가게 됩니다. 

버퍼에 있는 값을 뽑아오는 메소드는

 `next(),nextLine()`두가지가 있습니다.

### 

### next\(\)메소드

이름은 문자열의 변수이기 때문에 아래와 같은 코드를 통해 메소드를 사용할 수 있습니다.

```java
public class C_keyboardInput {
		public void inputScanner1() {
				Scanner sc = new Scanner(System.in);
				System.out.print("이름을 입력해주세요:");
				String name=sc.next();
	  }
}
```

출력한뒤 이름을 입력해보세요

![Conrad&#xB97C; &#xC785;&#xB825;&#xD55C;&#xB4A4; Enter&#xB97C; &#xB204;&#xB978; &#xACB0;&#xACFC;&#xC785;&#xB2C8;&#xB2E4;.](../../../.gitbook/assets/image%20%2824%29.png)

띄어쓰기가 있다면 어떻게 될까요?

![Con &#xB9CC; &#xC785;&#xB825;&#xB418;&#xC5C8;&#xC2B5;&#xB2C8;&#xB2E4;.](../../../.gitbook/assets/image%20%2828%29.png)

이렇게 **`next()`** 는 사용자가 입력한 값중 공백이 있는경우 공백 이전까지만 읽어오게 됩니다.

### 

### nextLine\(\)메소드

반대로 nextLine\(\) 메소드는 사용가자 입력한 값 모두를 읽어올 수 있습니다.

### nextInt\(\)메소드

이름 외에 다른 정보를 받아오는 코드를 작성해주세요.

나이의 경우 정수의 자료형을 가지고 있지만 **`nextLine()`**은 문자열을 뽑아올 수 있습니다. 

정수값을 뽑아오고 싶은 경우에는 **`nextInt()`** 메소드를 사용합니다.

```java
System.out.print("나이를 입력해주세요:");
int age = sc.nextInt();
```

### nextDouble\(\)메소드

키의 경우에는 실수가 될 수 있기때문에 실수값을 뽑아와야 합니다.

실수값을 뽑아올 경우에는 **`nextDouble()`** 메소드를 사용합니다.

```java
System.out.print("키를 입력해주세요:");
double height = sc.nextDouble();
```



이제 출력을 해보도록 하겠습니다.

변수를 이용해 _**\(  \)님은 \(  \)세이며, \(  \)cm입니다.**_ 의 형식으로 출력해볼까요?

```java
System.out.println(name + "님은" + age + "세이며," + height + "cm입니다.");
```

결과를 출력한뒤 값을 입력해보세요.

![&#xC21C;&#xCC28;&#xC801;&#xC73C;&#xB85C; &#xAC12;&#xC744; &#xC785;&#xB825;&#xD558;&#xBA74; &#xB2E4;&#xC74C;&#xC73C;&#xB85C; &#xB118;&#xC5B4;&#xAC11;&#xB2C8;&#xB2E4;.](../../../.gitbook/assets/image%20%2827%29.png)

값이 잘 출력되었나요?

{% hint style="danger" %}
단, `nextInt()`에는 정수만이, `nextDouble()`에는 실수값만 입력해야 합니다.
{% endhint %}

### 

### \*NextLine\(\)메소드 주의점\*

다음에는 주소를 추가해주겠습니다..

새로운 메소드를 만들어주세요

```java
public void inputScanner() {
			
			Scanner sc = new Scanner(System.in);
			
			System.out.print("이름:");
			String name = sc.nextLine();
			
			System.out.print("나이:");
			int age = sc.nextInt();
			
			System.out.print("주소:");
			String address = sc.nextLine();
			
			System.out.print("키(cm):");
			Double height = sc.nextDouble();	
			
			//출력
			System.out.print(name + "님은" + age + "살이며, 사는곳은"
					+ address + "이고, 키는" + height + "입니다.");
}
```

![&#xC8FC;&#xC18C;&#xAC00; &#xC785;&#xB825;&#xC774; &#xB418;&#xC9C0; &#xC54A;&#xC2B5;&#xB2C8;&#xB2E4;.](../../../.gitbook/assets/image%20%2817%29.png)

결과값에서 보이듯이 주소를 그냥 넘어가버리는 것을 볼 수 있습니다.

그이유는 다음과 같습니다.

> * **`sc.nextLine()`**: 버퍼에서 "엔터"까지 모두 읽어오는 메소드\(버퍼에 "엔터"가 비워짐\)
> * **`sc.nextLine()`이외의 메소드**: 버퍼에서 "엔터"를 제외한 값을 읽어옴\(버퍼에 "엔터"가 남음\)

> 이해하기가 어려울 수 있는데,  변수선언의 순서를 알아야 합니다.
>
> ```java
> String name = sc.nextLine(); 
> //1         3      2      (버퍼:엔터가 비워짐)
> int age = sc.nextInt();
> //4     6      5          (버퍼:엔터가 남아있음)
> String address = sc.nextLine();
> //6            8      7   
> ```

{% hint style="warning" %}
`nextLine()` 메소드는 "엔터"를 입력함으로써 메모리로 내용을 보내게 됩니다.

하지만 `nextInt()`호출뒤 "엔터"가 버퍼에 남아있기 때문에 

7번과정에서 버퍼에 남아있는 "엔터"가 읽히게 되고 바로 빈 문자열을 메모리로 보낸 것입니다.

그렇다면 7번과정 실행 이전에 버퍼에 있는 "엔터"를 비워주면 해결되겠죠?

즉 5번과정 뒤에`nextLine() 을 실행해 버퍼를 비워주면 됩니다.`
{% endhint %}

다시 코드를 수정해보세요

```java
public void inputScanner() {
			
			Scanner sc = new Scanner(System.in);
			
			System.out.print("이름:");
			String name = sc.nextLine();
			
			System.out.print("나이:");
			int age = sc.nextInt();
			
			sc.nextLine(); //"엔터"를 비워주기
			
			System.out.print("주소:");
			String address = sc.nextLine();
			
			System.out.print("키(cm):");
			Double height = sc.nextDouble();	
			
			//출력
			System.out.print(name + "님은" + age + "살이며, 사는곳은"
					+ address + "이고, 키는" + height + "입니다.");
}
```

![&#xC8FC;&#xC18C;&#xAC00; &#xC798; &#xC801;&#xC6A9;&#xB418;&#xC5C8;&#xC2B5;&#xB2C8;&#xB2E4;.](../../../.gitbook/assets/image%20%2860%29.png)

### nextLine\(\).charAt\(\);

그렇다면 문자가 1개라면 즉 변수가 char자료형이라면 어떻게 할 수 있을까요?

들어가기에 앞서 문자열들은 문자들이 합쳐진 값입니다.

> "M  a  l  e"
>
>   0   1 2 3 의 index를 가지게 됩니다.

성별을 입력하는 새로운 메소드를 만들어보세요.

```java
System.out.print("성별(M/F):");
//Male을 입력한다고 가정
char gender = sc.nextLine().charAt(0);
//               "Male"  중에  0번index  ='M'         
```

M/F중 한글자를 입력하라고 했지만 Male/Female이라고 입력하는 사람이 있습니다. 

위코드는 Male이라는 문자열중에 0번째 문자를 추출한다는 의미입니다.

이번에는 다른 형태로 출력을 진행해보겠습니다. 풀코드를 작성해주세요.

```java
public void inputScanner3() {
			Scanner sc = new Scanner(System.in);
			System.out.println("===개인정보 입력===");
			
			System.out.print("이름:");
			String name = sc.nextLine();
			
			System.out.print("성별(M/F):");
			char gender = sc.nextLine().charAt(0);
			
			System.out.print("나이:");
			int age = sc.nextInt();
			
			System.out.print("키:");
			double height = sc.nextDouble();
			
			//출력
			System.out.println(name + "님의 개인정보");
			System.out.println("성별: " + gender);
			System.out.println("나이: " + age);
			System.out.println("키: " + height);
			System.out.println("=== Developer ===");
			
		}
```

![&#xC798; &#xB098;&#xC654;&#xC8E0;?](../../../.gitbook/assets/image%20%2821%29.png)

분명 "Male"이라고 입력했음에도 불구하고 'M'으로 출력된것을 확인할수 있습니다.

