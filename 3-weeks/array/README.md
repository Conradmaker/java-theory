# 배열 \(Array\)

## 배열 

배열은 같은 자료형의 변수를 하나의 묶음으로 다루는 것을 말합니다.

배열은 저장된 값마다 index번호가 0부터 시작하여 설정되죠.

![&#xBCC0;&#xC218;&#xC640; &#xBC30;&#xC5F4;&#xC758; &#xCC28;&#xC774;&#xC810;&#xC774; &#xB290;&#xAEF4;&#xC9C0;&#xC2DC;&#xB098;&#xC694;?](../../.gitbook/assets/image%20%2858%29.png)

즉 배열은 다음과 같습니다.

* 여러개의 값을 보관할 수 있는 공간
* 같은 자료형의 변수를 하나의 묶음으로 다루는 것
* 각 인덱스의 자리에 값을 기록\(0부터 시작\)



그렇다면 배열을 왜 사용할까요?

만약 1부터 100까지의 정수 데이터를 관리하고 싶다면 어떻게 해야할까요

```java
	int num1 = 0;
	int num2 = 1;
  int num3 = 2;
	int num4 = 3;
	...
```

이렇게 100번 작성해야겠죠.. 심지어 반복문도 사용이 불가능하답니다.

### 배열사용법

사용법은 다음과 같습니다.

#### 1.배열선언

```java
//자료형 배열명[];
//자료형[] 배열명;
		
int arr[];
```

#### 2.배열할당 \(배열의 크기를 지정\)

```java
int arr[];

//배열명 = new int[배열크기];
arr = new int[5]; //5개값 담겠다.
```

하지만 주로 선언과 동시에 할당을 하게되겠죠?

#### 선언 + 할당

```java
int arr[] = new int[5];
```

보통 이렇게 사용하는 경우가 가장 많습니다.

3.값 대입 \(초기화\)

```java
//배열명[인덱스번호] = 값;
arr[0]=0;
arr[1]=1;
arr[2]=2;
arr[3]=3;
arr[4]=4;
```

이렇게 할수도 있지만 배열에는 일정한 규칙이 있을 경우 반복문을 사용할 수 있답니다.

```java
for(int i=0;i<arr.length;i++) {
			arr[i]=i;
}
```

그렇다면 출력문도 반복문을 통해 출력할 수 있겠죠?

```java
for(int i=0;i<arr.length;i++) {
			System.out.println(arr[i]);
}
```

또한 배열 값들의 합계도 구할수가 있겠죠?

```java
int sum2 = 0;
		for(int i=0; i<arr.length; i++) {
			sum2 += arr[i];
		}
System.out.println("총합: "+sum2)
```

추가적으로 아래코드를 작성하고 출력해보세요

```java
double[] dArr = new double[3];
			int[] iArr = new int[5];
			
			for(int i=0; i<dArr.length; i++) {
				System.out.println(dArr[i]);
			}
```

![&#xAC12;&#xC774; &#xCD9C;&#xB825;&#xB418;&#xC5C8;&#xC8E0;?](../../.gitbook/assets/image%20%2814%29.png)

우리가 값을 대입하지 않았지만 값이 출력된 이유는 

배열의 각 인덱스에 별도로 대입하지 않으면 JVM 이 지정한 기본값으로 값이

담기기 때문입니다.

왜냐하면 기본자료형을 제외한 다른 변수들은 Heap이라는 저장소에 저장되는데, 이 Heap영역에는 정대로 빈공간이 존재하면 안됩니다.

즉 배열에 선언한 길이만큼 기본값이 들어있겠죠?



이번에는 배열을 이용한 여러가지를 해볼것입니다. 

주석을 꼼꼼히 봐주세요

```java
	int [] arr = new int[5];
		
			for(int i=0; i<arr.length; i++) {
			arr[i] = i+1;
			}
			
			for(int i=0;i<arr.length; i++ ) {
				System.out.println("arr["+i+"]:"+arr[i]);
			}
			//배열의 주소
			System.out.println("arr: "+arr);
			
			//arr의 해시코드를 10진수로 바꿔줌
			System.out.println("arr  해시코드값: "+ arr.hashCode());
			
			//배열의 길이를 표현
			System.out.println("배열의 길이: " + arr.length);
```

![&#xC774;&#xB7F0; &#xACB0;&#xACFC;&#xAC12;&#xC774; &#xCD9C;&#xB825;&#xB418;&#xC5C8;&#xC8E0;?](../../.gitbook/assets/image%20%284%29.png)

사용자가 지정한 정수값만큼 배열의 크기를 지정해보겠습니다.

```java

		Scanner sc = new Scanner(System.in);
		
		System.out.print("새로 할당할 배열의 길이: ");
		int size = sc.nextInt();
		
		char[]arr = new char[size]; //사용자가 입력한 값
		
		for(int i = 0; i<arr.length;i++) {
			System.out.println(arr[i]);
		}
```

출력해보세요

![&#xCD9C;&#xB825;&#xC774; &#xC548;&#xB41C;&#xAC83; &#xCC98;&#xB7FC; &#xBCF4;&#xC774;&#xC2DC;&#xC8E0;?](../../.gitbook/assets/image%20%2861%29.png)

하지만 공백으로 출력되었기 때문에 아래로 커서가 내려가 있습니다.

그렇다면 기본값들을 알수 있죠?

| 자료형 | 기본값 |
| :---: | :---: |
| int | 0 |
| double | 0.0 |
| char | 공백 |

이번에는 새로운 형태의 값들을 담아보겠습니다.



또한 배열이 가득 찬 상태에서 값을 추가하면 에러가 발생하게 되는데, 

이러한 경우 어떻게 해결해야 하는지 알아보겠습니다.

### 배열에 값 추가하기

배열은 한번지정된 크기를 다시 지정할수 없다는 단점을 가지고 있습니다.

{% hint style="info" %}
크기를 변경해야만 한다면 다시 배열을 할당해야 합니다.

즉 배열의 크기를 다시 지정해 새로 만들어줘야합니다.
{% endhint %}

예제를 통해 살펴보겠습니다

```java
int[] arr = new int[5];
		
		for(int i=0; i<arr.length; i++) {
			arr[i]= i;
		}
		System.out.println("초기길이: " + arr.length);
		System.out.println("초기주소값: " + arr.hashCode());
		
		//arr배열 길이변경
		arr = new int[10];
		System.out.println("===변경후===");
		System.out.println("후기길이: " + arr.length);
		System.out.println("후기주소값: " + arr.hashCode());
```

![](../../.gitbook/assets/image%20%2819%29.png)

기존의 길이 뿐만 아니라 기존의 주소값마져 바뀐것을 확인할수 있습니다.

이건 Heap저장소 안에 새로운 값으로 배열을 만들었기 때문입니다.

물론 이러면 기존의 값은 주소연결이 사라지죠.. 기존의 값을 복사시키는 것은 나중에 알아보도록 하겠습니다.

물론 그렇게 연결이 끊어진 배열들은 일정시간이 지나면

 자바의 **Garbage Collector \(GC\)** 가 알아서 없애줄것입니다. 이게 바로 자바의 특징중 하나였던 자동 메모리 관리입니다.

그렇다면 삭제후 값에 대하여 알아볼까요?

```java
arr=null;
		System.out.println("===삭제후===");
		System.out.println(arr);
		System.out.println("삭제후길이: " + arr.length);
		System.out.println("삭제후주소값: " + arr.hashCode());
```

![arr&#xAC12;&#xC774; &#xC5C6;&#xAE30;&#xB54C;&#xBB38;&#xC5D0; &#xAE38;&#xC774;&#xB97C; &#xBD88;&#xB7EC;&#xC62C;&#xC218; &#xC5C6;&#xC2B5;&#xB2C8;&#xB2E4;.](../../.gitbook/assets/image%20%2853%29.png)

### 

### 배열선언, 크기지정, 초기화 한번에 하기

```java
int[]arr = {값, 값, 값};
```

사실 한가지 방법이 더 있기는 합니다.

```java
int[]arr = new int[]{값, 값, 값};
```

하지만 첫번째 방법이 훠어얼씬 편하죠?

하지만 아래 사실을 기억해야 합니다.

```java
int[]arr ={1,2,3,4};
int[]arr2= {1,2,3,4};

System.out.print(arr == arr2); //false
```

두 변수가 값은 같지만 false값이 나오는 이유는 값을 비교하는 것이 아닌 주소값을 비교하기 때문이라는 사실 모두 숙지하셔야 합니다.



예제를 볼까요?

```java
    Scanner sc = new Scanner(System.in);
		String[]arr = new String[5];
		
		for(int i=0; i<arr.length;i++) {
			System.out.print("좋아하는 과일명: ");
			arr[i] = sc.nextLine();
		}
		
		//잘 담겼는지 인덱스에 담긴값 출력
		for(int i=0; i<arr.length;i++) {
		System.out.print(arr[i] + " ");
		}
```

이 코드는 무엇을 요구하는 코드일까요?

사용자가 배열의 길이 즉, 5개의 과일을 나열하면 그 인덱스 순서대로 과일을 보여주는 코드입니다.

