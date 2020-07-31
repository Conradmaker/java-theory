---
description: day.2
---

# 변수 \(Variable\)

## 변수\(Variable\)

### 변수의 의미

변수란 _**메모리에 값을 기록하기 위한 공간**_입니다.

그렇다면 변수에 값을 기록하는 이유는 무엇일까요?

먼저 프로그램의 작동원리에 대하여 알고있어야 합니다.

![&#xD504;&#xB85C;&#xADF8;&#xB7A8;&#xC758; &#xC791;&#xB3D9;&#xC6D0;&#xB9AC;](../../.gitbook/assets/image%20%281%29.png)

즉 프로그램 실행 시 사용할 값\(Data\)이 있다면 그 값은 먼저 메모리에 기록 되어야 하는 것입니다.



그렇다면 코드를 작성하며 익혀보겠습니다.

작업공간에 JavaProject를 새로 만들어주세요.

그 전에 프로젝트 안에 패키지를 안만들고 클래스를 작성하면 왜 안되는지 알아보겠습니다.

1. 패키지가 없습니다.   패키지는 서로 비슷한 클래스를 묶어서 카테고리처럼 분류해 관리하는 역할을 하는데 패키지가 없으면 유지보수가 어렵겠죠?
2. 기본 패키지에 만들어진 클래스는 다른 패키지에서 사용이 불가능합니다.

따라서 패키지를 꼭 만들어 줘야겠죠? 그렇다면 패키지를 어떻게 만들어야 할까요?

* 패키지는 세단계 이상으로 만들어주는 것을 권장합니다. \(_ex_   com.회사명.프로젝트명\)
* 도매인의 역순으로 만들어주세요    \(_ex_   com.gitbook\(회사명\).java\(프로젝트명\)\)

왜냐하면 도매인은 고유한 이름이기 때문에 중복을 방지할 수 있으며, 어떤 회사인지 알아볼수 있습니다.



A\_Variable 클래스를 새로 만들어주세요.

이 클래스에서는 다음과 같은 내용을 알아볼 것입니다.

* 변수라는게 뭔지
* 변수를 왜 사용하는지
* 변수를 어떻게 쓰면 되는지
* 변수명을 어떻게 지어야 하는지

아래와 같은 게임의 가격을 계산하는 메소드를 만들어보세요

```text
package com.kh.variable;

public class A_Variable {  

	public void printValue() {
		System.out.println("=== 변수 사용 전 ===");
		System.out.println(100 + 18);
		System.out.println((100 + 10) * 10);
		System.out.println(((100 + 10) * 10) - 10);
	}
}

```

실행용 클래스를 만들어서 실행해보세요

```text
package com.kh.run;
import com.kh.variable.A_Variable;

public class Run {
	
	public static void main(String[] args) {
	
		A_Variable a = new A_Variable();
	
		a.printValue();

	}
}
```

![&#xACB0;&#xACFC;&#xAC12;](../../.gitbook/assets/image%20%2816%29.png)

이렇게 변수를 사용하지 않고 출력하면 코드가 어떤의도와 의미를 가지고 있는지 파악할수 없습니다.

### 

### 변수 작성법

위에서 작성한 코드를 변수를 지정해 작성해보겠습니다.

아래와 같은 코드를 연산을 진행한 클래스에 작성해보세요

```java
public void printValue() {
	int point = 100;      //포인트
	int bonus = 18;       //보너스
	int personCount = 10; //사람수
	int fees = 10;        //수수료
	
	System.out.println("=== 변수 지정 후 ===");
	System.out.println(point + bonus);  //(100 + 18)
	System.out.println((point + bonus) * personCount);  //((100 + 18) * 10)
	System.out.println(((point + bonus) * personCount) - fees);  //(((100 + 18) * 10) - 10)
}
```

![&#xAC19;&#xC740; &#xAC12;&#xC774; &#xB098;&#xC624;&#xB294; &#xAC83;&#xC744; &#xD655;&#xC778;&#xD560; &#xC218; &#xC788;&#xC2B5;&#xB2C8;&#xB2E4;.](../../.gitbook/assets/image%20%2812%29.png)

이렇게 변수를 사용해 작성하면 의미를 알 수 있겠죠?  물론 다른 목적으로도 사용되기도 한답니다.

여기서 int 를 자료형이라고 하는데 뒤에서 알아보겠습니다.

### 변수의 사용목적

1. 변수는 우선적으로 값에 의미를 부여하기 위한 목적으로 사용한다! \(가독성이 좋아짐\)
2. 변수는 한번 값을 저장해두고 계속 사용할 목적으로 사용한다!
3. 변수를 사용하면 나중에 쉽게 값을 변경할 수 있습니다! \(유지보수에 용이해집니다\)

### 

### 변수사용법

변수의 사용법에 대하여 알아보겠습니다.

* **변수의 선언** 

저장할 값을 기록하기 위한 변루를 메모리 공간에 확보하는 과정입니다.

아래와 같은 방법으로 선언할 수 있습니다.

```java
int variable  ; //자료형  변수명
//자료형: 어떤 값을 담아낼지, 어떤 크기의 값을 담아낼지에 대해 변수(박스)의 크기 및 종류를 정하는 부분
//변수명: 변수의 이름을 정하는 부분 (의미부여)
```

변수명을 정할때에는 몇가지 규칙이 있습니다.

1. _변수명은 반드시 첫 문자가 소문자._
2. _여러 단어로 조합시 카멜케이스 지키기._
3. _동일한 변수명으로 선언 불가 \(중복불가\)_
4. _해당 영역\({}\)에 선언한 변수는 해당 영역에서만 꺼내쓸 수 있음. \(다른메소드에서는 불가\(지역변수\)\)_ 

### 

### 자료형

| 표현식 | 자료형 | 크기 |
| :---: | :---: | :---: |
| bolean | 논리형 | 1byte |
| char | 문자\(문자\) | 2byte |
| String | 문자\(문자열\) | 참조형 |
| byte | 숫자\(정수형\) | 1byte |
| short | -- | 2byte |
| int | -- | 4byte |
| long | 숫자\(실수형\) | 8byte |
| float | -- | 4byte |
| double | -- | 8byte |

\*\*\*\*

* **변수에 값 대입\(초기화\)**

```java
변수명 = 값;
isTrue = true;
```

위와 같은 형식으로 표현할수 있습니다.

아래에서 예시를 보겠습니다.

```java
    //1.논리형
		boolean isTrue =1;
		
		//2.숫자형
		//2_1. 정수형
		byte bNum = 1;  
		short sNum = 2; 
		int iNum = 4;  
		long lNum = 8L;   //long형의 변수 뒤에는 L을 붙여주는게 좋다.  
		//2_2. 실수형(2개)
		float fNum = 4.0f;  //float형의 변수 뒤에는 *반드시* f를 붙여줘야 한다. 
		double dNum = 8.0; 
		
		//3.  문자형(한글자)
		char ch ='A';  //반드시 Single Quote로 표시해줘야 한다.   
		
		//참조자료형
		//4.문자열("여러글자")
		String str = "ABC"; //반드시 Doublw Quote로 표시
```

![&#xACB0;&#xACFC;&#xAC12;&#xC740; &#xC774;&#xB807;&#xAC8C; &#xB098;&#xC624;&#xAC8C; &#xB429;&#xB2C8;&#xB2E4;.](../../.gitbook/assets/image%20%2850%29.png)

저번에 배운 연산과 함께 사용이 가능하겠죠?

```java
    System.out.println("isTrue:"+isTrue);
		System.out.println("bNum:"+bNum);
		System.out.println("sNum:"+sNum); 
		System.out.println("iNum:"+iNum);
		System.out.println("lNum:"+lNum); 
		System.out.println("fNum:"+fNum);
		System.out.println("dNum:"+dNum); 
		System.out.println("ch:"+ch);
		System.out.println("str:"+str);
```

![&#xC774;&#xB7F0; &#xACB0;&#xACFC;&#xAC12;&#xC774; &#xB098;&#xC628;&#xB2F5;&#xB2C8;&#xB2E4;.](../../.gitbook/assets/image%20%2825%29.png)

추가적으로 이런식으로 작성할 수도 있습니다.

```java
int etc = 99_999_999;  //결과:99999999
```

이러면 코드를 보기에 조금더 편하겠죠?



### 변수명 명명규칙

변수의 이름을 만들때에는 암묵적인 규칙이 존재합니다.

naimgRule이라는 새로운 매소드를 만들어주세요.

1. 변수는 블록영역에서만 사용될 수 있는데 변수명이 중복되면 Error가 발생합니다.

```java
int number;
		
double number;  //Error
```

> 단 대소문자를 구분하기 때문에 만약 numBer라고 네이밍하면 가능하긴 합니다.

  2. 예약어\(이미 자바에서 사용되는 키워드\) 는 사용이 불가능합니다.

```java
int true;
int public;
int class;
int void;
```

  3. 숫자를 포함할 수 있습니다. 

```java
int age1;
int 1age; //Error
```

{% hint style="danger" %}
단 숫자로 변수명이 시작하면 불가능합니다.
{% endhint %}

4.   ,  \_  $  3가지의 특수문자 사용이 가능합니다.

```java
int number_1;
int number$1;
int number!1; //Error
int number#1; //Error
```

  etc. 권장사항

> 1.카멜케이스 지켜주기 + 소문자로 시작하기
>
> 2.왠만하면 한글을 사용하면 안됩니다. 에러가 날 수 있습니다.



### 요약

* 변수: 값\(Literal\)을 기록하기 위한 공간 \(메모리상에 값을 기록\)
* 변수의 사용목적: 

                                      의미부여 / 값의 재활용 / 유지보수에 용이

* 변수사용법: 

                            변수선언 &gt;  값 대입    or     변수선언과 동시에 값 대입

* 변수 명명규칙

