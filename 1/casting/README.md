# 형변환 \(Casting\)

## 형변환

값\(Data\)의 자료형을 바꾸는 것 \(boolean 제외\)



그렇다면 형변환이 왜 필요할까요?

컴퓨터의 값처리 원칙이 있기 때문입니다.

* 같은 종류의 자료형만 대입 가능   _int num = \(int\)2.3;_
* 같은 종류의 자료형만 계산이 가능 _10+2.3_
* 계산의 결과도 같은 종류의 값이 나와야 함. _10\(정수\) + 10\(정수\) =&gt; 20\(정수\)_

위와 같은 원칙으로 인해 자료형을 변화시켜주어야 합니다.



### 형변환의 종류

1. **자동형변환** : 자동으로 형변환 되기 때문에 명시적으로 변환 시켜줄 필요 없다.
2. **강제형변환**: 직접 형변환 해야함. \(명시적 형변환\)

#### 

#### 자동형변환

자동 형변환은 _**작은 자료형을 큰 자료형으로**_ 자동으로 형변환되는 것을 의미합니다.

예를들면 `int`\(4byte\) -&gt;`double`\(8byte\) 형변환을 들 수 있는데 아래와 같이 대입연산 코드를 작성해보세요

```java
public void casting1() {
		int i1 = 12;
		
		//대입연산
		double d1 = i1;
		
}
```

![12.0&#xC774;&#xB77C;&#xB294; &#xACB0;&#xACFC;&#xAC12;&#xC774; &#xCD9C;&#xB825;&#xB42C;&#xC2B5;&#xB2C8;&#xB2E4;.](../../.gitbook/assets/image%20%2840%29.png)

형변환을 따로 시켜주지 않았는데 형변환이 일어났습니다.

단, 큰 자료형을 작은 자료형에 넣어주실때에는 직접 자료형을 입력해줘야 합니다.

산술연산코드를 작성해보겠습니다.

```java
int i2 = 12;
		double d2 = 3.3;
		//산술연산
		System.out.print(i2+d2);    //값:15.3
```

형변환이 double형으로 이루어졌죠?? 

둘다 실수형인 float형과 double형의 연산도 더 큰 double형으로 형변환이 일어난답니다.

여기서 알 수 있듯이 항상 형변환은 작은형이 큰형으로 바뀌게 된답니다.

추가적으로 저번시간에 살펴보았던 예제에도 형변환이 일어납니다.

```java
System.out.println(name + "님의 개인정보");
System.out.println("성별: " + gender);
System.out.println("나이: " + age);
System.out.println("키: " + height);
System.out.println("=== Developer ===");
```

숫자형들이 문자열로 바뀌게 된 것입니다.

추가적으로 다음과 같은 코드를 적어보세요

```java
long l5 = 10000000L;
				float f5 = l5;
				
				System.out.print("f5: " +f5)
```

실수는 어떤 정수타입보다 더 큰 범위의 값을 저장할 수 있기때문에 실수형이 더 크다고 계산하고 실수형으로 값이 바뀌게 됩니다.

아래코드는 어떤 값이 나올까요?

```java
char ch = 65; //65=='A'
				System.out.println("ch:" +ch);
```

{% hint style="info" %}
ch:A
{% endhint %}

문자들은 고유의 숫자값을 가지고 있기 때문에 숫자값에 해당하는 문자값으로 자동형변환이 이루어졌습니다.

byte , short간의 연산은 int로 취급하게 됩니다.

```java
byte b1 = 1;
byte b2 = 10;

byte result = b1 + b2;
```

b1 + b2에 에러코드가 뜨게되는데요

![int&#xD615;&#xC774;&#xB77C;&#xACE0; &#xB098;&#xC635;&#xB2C8;&#xB2E4;.](../../.gitbook/assets/image%20%2837%29.png)

이런경우에는 강제형변환을 해줘야 합니다.

```java
byte result = (byte)(b1 + b2);     //11
```

결과값이 잘 출력됩니다.



#### 강제형변환

큰 크기의 자료형을 작은 크기의 자료형으로 바꾸는 것을 의미합니다.

먼저 double\(8byte\)  --&gt;float\(4byte\)로 변환을 해보겠습니다.

```java
public void casting2() {
		
		double d =4.0;
		float f = d;	
	}
```

![&#xC774;&#xB7F0; &#xC5D0;&#xB7EC;&#xAC00; &#xB098;&#xD0C0;&#xB0A9;&#xB2C8;&#xB2E4;.](../../.gitbook/assets/image%20%2833%29.png)

이럴경우에 강제 형변환을 진행해주세요.

```java
double d =4.0;
float f = (float)d;
```

그렇다면 실수를 정수로 변환해볼까요?

```java
double d2 = 162.3;
int i2 = d2;

System.out.println("i2:" +i2);
```

![&#xC704;&#xC640; &#xAC19;&#xC740; &#xC5D0;&#xB7EC;&#xAC00; &#xBC1C;&#xC0DD;&#xD569;&#xB2C8;&#xB2E4;.](../../.gitbook/assets/image%20%2867%29.png)

그럼 강제형변환을 한번 진행하고 출력해보겠습니다.

![&#xC18C;&#xC218;&#xC810;&#xC774; &#xC5C6;&#xC5B4;&#xC9C4;&#xAC8C; &#xBCF4;&#xC774;&#xC2DC;&#xB098;&#xC694;?](../../.gitbook/assets/image%20%2854%29.png)

{% hint style="danger" %}
이렇게 실수를 정수로 강제로 변환하게 될 경우 데이터손실이 발생할 수도 있습니다. 이점 꼭 주의해주세요
{% endhint %}

추가적으로 

```java
int iNum=10;
double dNum=5.89;
		
int iSum = iNum + dNum;
```

이러한 경우에도 오류가 발생하게 되는데요 위에서 보았듯이 계산과정은 자동형변환이 이루어져서 double형으로 변환됩니다. 

그러나 그 결과가 double이기 때문에 int인  iSum에 담지 못하는 것입니다.  해결방법을 알아보겠습니다.

{% hint style="success" %}
1.연산결과를 int형으로 강제 형변환 해준뒤 담기

```java
int iSum = (int)(iNum + dNum);
```

2.double형을 int형으로 강제형변환 후 연산하기

```java
int iSum = iNum + (int)dNum;
```

3.연산결과를 double형으로 기록하기

```java
double iSum = iNum + dNum;
```
{% endhint %}

### 데이터오버플로우

자료형에 변수를 저장할 때에는 그 범위가 정해져 있는데 그 범위를 벗어나는 것을 말합니다.

자료형에 대한 정리는 변수에서 알아보았습니다.

바이트의 경우에서 한번 보겠습니다. 

![&#xBC94;&#xC704;&#xB97C; &#xBC97;&#xC5B4;&#xB098;&#xBA74; &#xC790;&#xB3D9;&#xC73C;&#xB85C; &#xC54C;&#xB824;&#xC90D;&#xB2C8;&#xB2E4;.](../../.gitbook/assets/image%20%2843%29.png)

하지만 연산의 경우에는 어떻게 될까요?

```java
public void overflow() {
		//byte 자료형에 저장 가능한 범위: -128 ~ 127
		byte bNum = 127; 
		
		bNum ++; //bNum에 담긴값을 1증가시킨다는 의미
		
		System.out.print("bNum: " + bNum);
	}
```

![-128&#xC774; &#xB098;&#xC654;&#xC2B5;&#xB2C8;&#xB2E4;.](../../.gitbook/assets/image%20%2844%29.png)

즉 범위를 벗어나게 되면 최소값으로 다시 돌아가는 것입니다.

그럼 최소값보다 작아지게 되면 최대값으로 돌아가게 되겠죠?



