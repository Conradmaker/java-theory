# 조건문 \(if문\)

## 조건문

조건문은 if문    /    switch문이 있습니다.

프로그램의 흐름은 위에서 아래로 흐르는 구조를 가지고 있는데, if문을 사용하면 선택적으로 동작하도록 제어할 수 있습니다.

이번장에서는 여러가지 조건문에 대하여 알아보도록 하겠습니다.

조건문은 조건식을 통해 참인가 거짓인가를 판단해 해당 조건식이 참일 경우 그에 해당하는 실행문을 실행하게 됩니다.

우리가 저번시간에 알아보았던 삼항연산자 또한 조건문이죠.

### 

### 단독 if문

사용 양식은 다음과 같습니다.

```java
if(조건식){실행문}

//조건식의 결과가 true => 실행문 실행
//조건식의 결과가 false=> 실행문실행 X
```

예제를 통해 살펴보겠습니다.

사용자가 입력한 정수를 양수, 음수, 0으로 분류해주는 것입니다.

```java
	public void method() {
		Scanner sc = new Scanner(System.in);
		
		System.out.print("정수: ");
		int num = sc.nextInt();
		
		if(num>0) {
			System.out.println("양수");
		}else if(num<0) {
			System.out.println("음수");
		}else {
			System.out.print("0");
		}
	}
```

어렵지 않죠?

그렇다면 예제를 작성해보세요

```java
if(gender =='M'||gender=='m') {
		result = "남";
	}
	if(gender =='F'||gender =='f') {
		result = "여;"
	}
```

이런경우에는 result는 지역변수이기 때문에 밖에서 쓸 수가 없는데 어떻게 해야할까요?

{% hint style="info" %}
```java
public void method() {
		Scanner sc = new Scanner(System.in);
		
		System.out.print("성별: ");
		char gender = sc.nextLine().charAt(0);
		//기본값 입력
	String result="잘못된 입력";
		
	if(gender =='M'||gender=='m') {
		result = "남";
	}
	if(gender =='F'||gender =='f') {
		result = "여";
	}
	System.out.println(result);
	}
```
{% endhint %}

이렇게 기본값을 밖에서 입력해주신다면 사용할 수 있습니다.

다음예제도 한번 작성해보세요

```java
//어린이 , 청소년, 어른을 나누는 조건문
System.out.print("나이: ");
		int age = sc.nextInt();
		
		if(age <= 13) {
		System.out.print("어린이");
		}
		if(age > 13 && age <=19) {
		System.out.print("청소년");
		}if(age < 19){
		System.out.print("어른");
		}
```

이렇게 작성을 할수 있지만 단독if문은 별개로 동작하기 때문에 모든 조건을 나열해줘야 해요.

하지만 아직 익히지 않은 if-else문은 하나로 동작하기 때문에 이렇게도 작성할 수 있습니다.

```java
System.out.print("나이: ");
		int age = sc.nextInt();
		if(age <= 13) {
		System.out.print("어린이");
		}else if(age <=19) {
		System.out.print("청소년");
		}else {
		System.out.print("어른");
		}
```

이제 if-else문에 대하여 알아보도록 하겠습니다.

### If-else\(-if\)

if-else

```java
public void method() {
		if(조건식) {
			조건식이 true 인경우 실행되는 실행문
			}else {
			조건식이 false면 반드시 실행되는 실행문
		}
	}
```

반면에 if-else if문과 같은 경우에는 같은 비교대상으로 여러개의 조건을 제시할 경우 사용할 수 있습니다.

```java
public void method() {
		if(조건식1) {
			조건식1이 true면 실행
		}else if(조건식2){
			조건식2이 true면 실행
		}else if(조건식3){
			조건식3이 true면 실행
		}else{
			조건식들이 false면 실행
		}
	}
```

차이점들이 느껴지시나요? 

조건이 많다면 단독if문들을 많이 사용하는 것보다는 if-else나 if-else if문을 사용하는 것을 추천드립니다.

이제 조금 다양한 예제를 보여드리도록 하겠습니다.

점수를 등급으로 나누고 만약 1의자리가 5가 넘으면 +를 붙이는 코드입니다.

```java
public void method() {
		Scanner sc = new Scanner(System.in);
		
		System.out.print("점수: ");
		int age = sc.nextInt();
	
		String grade ="";
		
		if(age>=90) {
			grade = "a";
		}else if(age>=80) {
			grade = "b";
		}else if(age>=70) {
			grade = "c";
		}else if(age>=60) {
			grade = "d";
		}else{
			grade = "f";
		}
		
		int plus = age % 10;
		if(plus>=5) {
			System.out.println(grade + "+");
		} else {
			System.out.println(grade);
		}
	}
```

### equals\(\)메소드

이름을 입력해 맞는 이름을 입력하면 본인이라고 출력되는 코드를 한번 작성해보세요

```java
public void method2() {
		Scanner sc = new Scanner(System.in);
		
		System.out.print("이름입력: ");
		String name = sc.nextLine();
		
		
		if(name=="conrad") {
			System.out.println("본인입니다.");
		}else {
			System.out.print("본인이 아닙니다.");
		}
		
	}
```

이런식으로 작성할 수 있으셨나요? 그렇다면 결과를 한번 보세요

![&#xBD84;&#xBA85; &#xB9DE;&#xB294; &#xC774;&#xB984;&#xC744; &#xC785;&#xB825;&#xD574;&#xB3C4; &#xBCF8;&#xC778;&#xC774; &#xC544;&#xB2C8;&#xB77C;&#xACE0; &#xB098;&#xC635;&#xB2C8;&#xB2E4;.](../../.gitbook/assets/image%20%2838%29.png)

그 이유는 String값이 저장될때는 문자열이 아닌 다른방식으로 저장되기 때문인데요 String값을 비교할 때에는 `==`연산자가 아닌 `equals()`메소드를 통해 비교를 해줘야 합니다.

사용방법은 다음과 같습니다.

```java
문자열.charAt(인덱스) => '문자'
문자열.equals(문자열) => true / false
```

그렇다면 조건문을 한번 고쳐볼까요?

```java
if(name.equals("conrad")) {
			System.out.println("본인입니다.");
		}else {
			System.out.print("본인이 아닙니다.");
		}
```

![&#xC815;&#xC0C1;&#xC801;&#xC73C;&#xB85C; &#xCD9C;&#xB825;&#xB418;&#xB294; &#xAC83;&#xC744; &#xD655;&#xC778;&#xD560; &#xC218; &#xC788;&#xC2B5;&#xB2C8;&#xB2E4;.](../../.gitbook/assets/image%20%282%29.png)

문자열간의 비교는 빈번히 일어나기 때문에 꼭 숙지하시면 좋습니다.

{% hint style="info" %}
기본자료값`(int, char, double, boolean, ...)` 

`==` 연산자 사용가능

String 은 `equals()` 메소드를 이용해야 비교가능
{% endhint %}



