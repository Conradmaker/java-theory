---
description: '6.25'
---

# 연산자 \(Operator\)

## 연산자

지금까지 배우는 과정에서 많은 연산자들을 사용했습니다.

지금부터 연산자에 대하여 알아보겠습니다.

### 종류

![](../../.gitbook/assets/image%20%2845%29.png)



### 논리부정 연산자

논리 부정 연산자는 단항연산자입니다. 

즉 한개의 값을 가지고 연산하게 됩니다.

클래스를 새로 만들어준뒤 아래와 같이 입력해보세요.

#### 

#### !연산자

```java
public class A_LogicalNegation {
	public void method() {
		System.out.println("!true:  " + !true);
		System.out.println("!false: " +!false);
	}
```

![&#xC774;&#xB7F0; &#xACB0;&#xACFC;&#xAC00; &#xB098;&#xC654;&#xC2B5;&#xB2C8;&#xB2E4;.](../../.gitbook/assets/image%20%2856%29.png)

즉 !은 참이면 거짓 거짓이면 참을 반환하게 되는 연산자입니다.



### 증감연산자

증감연산자 또한 단항연산자입니다.

| 종류 | 기능 |
| :--- | :--- |
| ++ | 값을 1증가시킨다 |
| -- | 값을 1감소시킨다 |

하지만 앞에 붙냐 뒤에 붙냐에 따라서 순서가 살짝 변하는데요, 

앞에 붙이면 전위연산자,    뒤에 붙으면 후위연산자라고 부릅니다.

#### 전위연산자

아래 코드를 작성해보세요

```java
public void method() {
		int num1 =10;
		
		System.out.println("전위연산 적용 전 num1의 값: " + num1);  //num1 = 10출력
		System.out.println("1회 수행 후 결과: " + ++num1); //num1 = 11출력  먼저 증가시키고 출력이나 계산을 한다.
		System.out.println("2회 수행 후 결과: " + ++num1); //num1 = 12출력
		System.out.println("전위연산 적용 후 num1의 값 : " + num1);
	}
```

![&#xC5F0;&#xC0B0; &#xC801;&#xC6A9; &#xD6C4; &#xAC12;&#xC5D0;&#xB294; &#xBCC0;&#xD654;&#xAC00; &#xC5C6;&#xC2B5;&#xB2C8;&#xB2E4;.](../../.gitbook/assets/image%20%286%29.png)

그렇다면 후위연산자를 사용해보겠습니다.

```java
int num2 = 10;
		
		System.out.println("후위연산 적용 전 num2의 값: " + num2);
		System.out.println("1회 수행 후 결과: " + num2++);
		System.out.println("2회 수행 후 결과: " + num2++);
		System.out.println("전위연산 적용 후 num1의 값 : " + num2);
```

![1&#xD68C;&#xC218;&#xD589; &#xD6C4; &#xACB0;&#xACFC;&#xAC00; &#xBCF4;&#xC774;&#xC2DC;&#xB098;&#xC694;?](../../.gitbook/assets/image%20%2851%29.png)

즉 후위연산자는 출력문과 같은 처리할 것들을 먼저하고난 뒤 증감을 해주는 연산자입니다.  

즉 증가는 되어있지만 출력문을 먼저 실행하였기 때문에 출력문에 적용이 되지 않는것입니다.

이해가 되지 않는다면 새로운 매소드를 만들어보세요

```java
public void method2() {
	//전위연산
	int a = 10;
	int b = ++a; //a=11 b=11
	System.out.println("a: " +a+ ", b: "+b );
	
	//후위연산
	int c =10;
	int d =c++; //c=10(11) d=10
	System.out.println("c: " +c+ ", d: "+d );
	}
```

![&#xAC12;&#xC774; &#xC65C; &#xB2E4;&#xB978;&#xC9C0; &#xC774;&#xD574;&#xAC00; &#xB418;&#xC2DC;&#xB098;&#xC694;?](../../.gitbook/assets/image%20%2835%29.png)

c는 d변수로 대입연산이 10으로 선행된 뒤 11로 증가가 되었기 때문입니다.

한가지만 더 만들어보겠습니다.

```java
    int num1 =20;
    int result = num1++ * 3; 
	// num1=20(21) result=20*3=60
	
	System.out.println("num1 :" + num1 );
	System.out.println("result :" + result );
	
```

![](../../.gitbook/assets/image%20%2866%29.png)

이제 전위연산자와 후위연산자의 차이가 느껴지시나요?

사용할때 주의해서 사용하시면 유용하게 사용하실 수 있을것입니다.



### 산술연산자

산술연산자는 이상연산자입니다. 

이항연산자는 두개의 값을 가지고 연산하는 연산자입니다.

$$
+ ,  - ,  *, /
$$

4가지 수학기호입니다. 많이 익숙하시죠?  추가적으로 %도 산술연산자입니다.

아래와 같이 코드를 작성해주세요

```java
public class C_Arithmetic {
	public void method1() {
		int num1 =10;
		int num2=4;
		
		System.out.print("num1+num2="+(num1+num2));
		System.out.print("num1-num2="+ num1 - num2);//오류
	}
```

문자열과 먼저 계산을 하게 되면 문자열로 형변환되는 것을 기억하시죠?

문자열과 숫자는 빼기가 되지 않기 때문에 오류가 나타납니다. \(\)를 추가해주세요.

```java
System.out.print("num1-num2="+ num1 * num2);
```

하지만 곱셈의 경우에는 덧셈보다 우선순위가 높기 때문에 이런경우 \(\)를 해주지 않으셔도 괜찮습니다. / %도 같은 우선순위 입니다.

/ %의 경우 조금 생소할수 있는 데요 예제를 한번 입력해보세요.

```java
System.out.println("num1 % num2= "+(num1 / num2));
System.out.println("num1 % num2= "+(num1 % num2));
```

![&#xC65C; &#xC774;&#xB7F0;&#xACB0;&#xACFC;&#xAC00; &#xB098;&#xC624;&#xB294;&#xC9C0; &#xC774;&#xD574;&#xB418;&#xC2DC;&#xB098;&#xC694;?](../../.gitbook/assets/image%20%2847%29.png)

/ 즉 나누기를 할 경우 2 나머지 2가 나오게 되는데 num1,num2는 정수값이기 때문에 /의 경우 정수값만 출력된 것이고 %의 경우 나머지가 출력된 것입니다.

