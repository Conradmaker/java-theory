---
description: day.3
---

# 상수 \(Constant\)

## 상수

변수가 값을 변경할 수 있는 값을 말한다면

상수는 한번 정의하면 변경이 불가능한 값을 말합니다.



먼저 변수를 선언하고 실행해보세요

```java
public class B_Constant {
	
	public void finalConstant() {
	  //자료형 변수명 = 값;
		int age =20;
		System.out.println("age:"+age);
		
		age = 21;
		System.out.println("age:"+age);
	}
}

```

{% hint style="info" %}
age:20

age:21
{% endhint %}

값이 잘 출력되었나요? 

이렇게 변수는 다른값으로 변경이 가능합니다.



상수를 정의하는 방법은 매우 쉽습니다.

변수를 정의할때 앞에 final 키위드를 붙이면 끝입니다.

```java
//final 자료형 변수명 = 값;
final int AGE = 20;
```

단, 상수를 선언할때에는 대문자로 선언해주는 것이 좋습니다.

