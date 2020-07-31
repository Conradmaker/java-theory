# 반복문\(while문\)

while문

while문 또한 for문과 비슷한 동작원리를 가지고 있는데 위치가 조금 다르답니다.

사용방법은 아래와 같습니다.

```java
초기식;
while(조건식){
    반복적으로 실행시키고자 하는 구문
    증감식
}
```

실행순서는 다음과 같습니다.

> 초기식 &gt; 조건식검사 &gt; true일 경우 구문실행 &gt;증감식      
>
>              &gt;조건식 검사 &gt;true일 경우 구문 실행 &gt; 증감식

먼저 안녕하세요를 5번 출력시켜 보겠습니다.

```java
public static void main(String[] args) {
		int i=0;
		
		while(i<5) {
		   System.out.println("안녕하세요");
		   i++;
	   }
	}
```

어떤가요? for문과 유사한게 느껴지시나요? 보통 for문을 while문으로 while문을 for문으로 바꿀 수 있습니다.

이번에는 1에서 10까지의 홀수만을 출력해보도록 하겠습니다.

```java
public static void main(String[] args) {
		int i =1;
		while(i<=10){
			if(i%2==1)
			System.out.print(i+" ");
			i++;
		}
}
```

우선 조건문을 이용한 방법으로 출력할 수 있겠죠? 다른방법도 한번 볼까요?

```java
public static void main(String[] args) {
		
		int i =1;
		while(i<=10){
			System.out.print(i+" ");
			i+=2;
		}
	}
```

이렇게 복합대입연산자를 이용해도 간단히 구현할 수 있습니다.

이번에는 랜덤값까지의 합을 구하는 반복문을 작성해볼까요?

```java
public static void main(String[] args) {
		
		int random = (int)(Math.random()*50+1);
		
		System.out.println("랜덤값: " + random);
		
		int sum=0;
		int i =1;
		while(i<=random) {
			sum += i;
			i++;
		}
		System.out.print("합계: " +sum);
	}
```

코드는 비교적 길지만?! 쉽게 구현할 수 있습니다.

do-while문

do while문은 초기식 한번은 false가 되어도 무조건 실행되는 반복문입니다.

사용방법은 다음과 같습니다.

```java
	초기식;
	do {
		반복적으로 실행할 코드;
		증감식;
	}while(조건식);
```

> 초기식 &gt; '무조건 한번은 실행\(do\)' &gt; 증감식 
>
> 조건식 &gt;           true면 실행              &gt; 증감식

예제를 통해 알아볼까요?

```java
public static void main(String[] args) {
		int num =1;
		
		do {
			System.out.println(num);
		}while(num == 0);      //int초기값은 1이기 때문에 첫번째 루프에서 false
	}
```

int 초기값이 1이기 때문에 조건문에서 false가 되겠죠?

아마 for이나 while 같은 경우에는 코드가 실행되지 않을 것입니다. 

하지만 결과를 보세요

![1&#xC774; &#xCD9C;&#xB825;&#xB418;&#xC5C8;&#xC2B5;&#xB2C8;&#xB2E4;.](../../.gitbook/assets/image%20%2859%29.png)

최초로 조건이 false여도 do를 한번 실행한 모습입니다. 

