# 조건문\(switch문\)

Switch문

Switch문은 Java언어에서는 if문과 가장 큰 차이점이 있습니다.

* switch문은 범위지정이 불가능하다.\(대소비교, 동등비교, &&,\|\|\)
* 즉 if문과는 다르게 switch문은 동등비교만이 가능하다.

사용법은 다음과 같습니다.

```java
	switch(동등비교대상자) {
		case 값1: 실행코드1 break;
		case 값2: 실행코드2 break;
		case 값3: 실행코드3 break;
		case 값4: 실행코드4 break;
		default: 실행코드
}
```

if문과 같은 경우에는 true값을 만나면 자동으로 밖으로 return되지만 `switch`문의 경우에는 `break`를 만날때까지 쭉 실행됩니다.

또한 if-else문의 else와 같은 기능을 하는 default문을 통해 작성해줄 수 있습니다.

하지만 break를 걸어주지 않아야 하는 경우도 있습니다.

{% hint style="info" %}
1.비교할 대상자 ==값1의 조건이 true일 경우 실행코드 1을 수행하고 break를 만나 빠져나감.

2.단, false일 경우 값2와 다시 동등비교 수행.

3.모든 값들과 일치하지 않을경우 default에 제시되있는 구문 실행
{% endhint %}

예제를 통해 살펴보겠습니다.

사용자에게 1~3사이의 정수를 입력받아

 1인경우 "빨강"출력, 2인경우"파랑",3인경우 "초록"을 포함이 안되면 "잘못입력했습니다"를 출력하는 코드를 작성해볼까요

```java
switch(num) {
		case 1 : System.out.print("빨강"); break;
		case 2 : System.out.print("파랑"); break;
		case 3 : System.out.print("초록"); break;
		default: System.out.print("잘못입력했어요"); break;
}
```

이해가 되시나요?

과일로 예를들어 다른 예제를 만들어보겠습니다.

 if문에서 문자열의 경우에는 `equals()메소드`를 사용했던거 기억나시나요?

switch문에서는 그러실 필요하 없답니다!

예제문을 따라 작성해보세요

```java
System.out.print("과일을 입력해주세요: ");
		String fruit = sc.nextLine();
		
		switch(fruit) {
		case "포도" : System.out.print("3000원"); break;
		case "사과" : System.out.print("2000원"); break;
		case "멜론": System.out.print("5000원"); break;
		default: System.out.print("잘못입력했어요"); break;
}
```

어떠신가요?

이번에는 break가 필요없는 예제를 살펴보겠습니다.

카페의 등급과 같은 예제를 만들어 보겠습니다.

```java
int level = sc.nextInt();
		
		switch(level) {
		case 3 : System.out.print("관리권한 ");
		case 2 : System.out.print("글쓰기권한 ");
		case 1: System.out.print("읽기권한 "); break;
		default: System.out.print("잘못입력했어요"); ;
}
```

![](../../.gitbook/assets/image%20%2863%29.png)

![](../../.gitbook/assets/image%20%2836%29.png)

어떤 상황에 break가 안쓰여도 괜찮은지 이해가 가시죠?

