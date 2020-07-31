# 반복문\(for문\)

for문



사용방법은 다음과 같습니다.

```java
for(초기식; 조건식; 증감식){
 -반복적으로 실행시키고자 하는 구문-
}
```

{% hint style="info" %}
초기식: 반복문이 수행될 때 "단 한번만 실행된다"

\(주로 변수 선언과 동시에 초기화 구문\)

조건식:"반복문이 수행될 조건"을 작성하는 구문

\(조건식이 true일 경우 실행구문을 실행한다\)
{% endhint %}

초기식-&gt;조건식검사 -&gt;true일경우 실행구문 실행 -&gt;증감식

            -&gt;조건식검사 -&gt;true일경우 실행구문 실행 -&gt; 증감식  

           -&gt;다시 조건식  -&gt;true일경우 실행구문   -&gt;증감식

          -&gt;다시 조건식 -&gt;false일경우 실행구문 X -&gt;반복문 나옴

위와같은 순서로 진행되게 됩니다.

이제 예제를 통해 살펴보겠습니다.

```java
for(int i=1; i<=5; i++) {
			System.out.println("안녕하세요");
		}
```

![5&#xBC88; &#xCD9C;&#xB825;&#xB418;&#xC5C8;&#xC2B5;&#xB2C8;&#xB2E4;.](../../.gitbook/assets/image%20%2826%29.png)

i가 증감식으로 1씩증가되어 6이되면 false로 반복문을 나가게 됩니다.

```java
for(int i=1; i<=5; i++) {
			System.out.println("안녕하세요");
		}
		
		for(int i=0;i<=4;i++) {
			System.out.println("다시만나요");
		}
		
		for(int i=1; i<6; i++) {
			System.out.println("헬로");
		}
```

위의 코드들또한 모두 5회씩 반복되는 반복문입니다.

그렇다면 1~5까지를 출력하는 반복문을 만들어보겠습니다.

```java
for(int i=1; i<6; i++) {
			System.out.println(i);
		}
```

이해가 잘 되시나요?

반복문안에 다시 반복문을 작성할 수도 있습니다.

```java
for(int i=2;i<=9;i++) {
			for(int v=2;v<=9;v++)
			System.out.println(i+" x " + v +" = "+i*v);
}
```

![9&#xB2E8;&#xAE4C;&#xC9C0; &#xCD9C;&#xB825;&#xB418;&#xB294; &#xAC83;&#xC744; &#xD655;&#xC778;&#xD560; &#xC218; &#xC788;&#xC2B5;&#xB2C8;&#xB2E4;.](../../.gitbook/assets/image%20%2834%29.png)

다음에는 1~10까지의 홀수만을 출력하는 반복문을 작성해보세요

세가지 방법이 있는데, 연산문, 조건문,증감식을 통해 구현해 보도록 하겠습니다.

```java
//연산문을 통한 출력
for(int i=1; i<=10; i++) {
				System.out.println(i*2-1);
}
			
//조건문을 통한 구현
for(int i=1; i<=10; i++) {
				if(i%2 == 1) {
					System.out.println(i);
				}
}

//증감식을 통한 구현
for(int i=1; i<=10; i+=2) {
			System.out.println(i);
```

마지막방법은 반복문 자체가 5번만 수행되는 코드입니다.

이렇듯 코드의 정답은 없습니다. 여러분이 편하고 빠르다고 생각하는 방법으로 코드를 작성하시면 됩니다.



이번에는 1부터 10까지의 정수값들의 합계를 구하는 반복문을 작성해보겠습니다.

`int sum = 1+2+3+4+5+6+7+8+9+10 이렇게 계산이 되어야겠죠?`

`sum+=1, sum +=2,  sum+=3, ... , sum+=10` 이런 식이 나와야 합니다.

그렇다면 반복문으로 구현해보겠습니다.

```java
int sum=0;
		
		for (int i=1;i<=10; i++) {
			sum += i;
		}
		
		System.out.print(sum);
```

이해가 되시나요???

이번에는 응용해서 사용자가 입력한 수까지의 합계를 구해보도록 하겠습니다.

```java
Scanner sc = new Scanner(System.in);
	 
		System.out.print("몇까지의 수를 더할거? : ");
		int a = sc.nextInt();
		int sum=0;
		
		if(a <= 0) {
			System.out.print("양수를 입력해주세요!!");
		}else {
			for (int i=1;i<=a; i++) {
				sum += i;
			}
			System.out.print(sum);
		}
```

추가적으로 양수를 입력하지 않으면 출력되지 않도록 조건문을 구현하였습니다. 

### Math.ramdom\(\);

추가적으로 랜덤으로 숫자를 생성해주는 메소드입니다.

0~0.9999999사이의 램덤값이 발생하게 됩니다.



```java
Scanner sc = new Scanner(System.in);

    int a = (int)(Math.random()*100)+1;
    //1~100까지의 랜덤값 뽑기
   
     int sum=0;
 for(int i=0 ; i<a; i++) {
     sum+=i;
 }
    System.out.println("총합: " + sum);
    System.out.println("랜덤: "+a);
}
```

### Math.min / max

min값에서 max값으로 1씩 증가하는 값을 출력해보도록 하겠습니다.

```java
Scanner sc = new Scanner(System.in);
		System.out.print("정수 1입력: ");
		int num= sc.nextInt();
		System.out.print("정수 2입력: ");
		int num2= sc.nextInt();
	   
		int min = Math.min(num, num2);
	    int max = Math.max(num, num2);
	    
	    
	    for(int i=min; i<=max;i++) {
	    System.out.println(i);
	    }
```



