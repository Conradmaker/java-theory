# 배열응용

먼저 사용자가 입력한 수만큼의 크기의 int배열을 만들어보겠습니다.

```java
System.out.print("배열크기: ");
int size = sc.nextInt();
		
int[]arr = new int[size];
```

쉽죠?

그 뒤에는 0번 인덱스  마지막 인덱스까지 값을 담아보겠습니다. \(1~100\)

```java
System.out.print("배열크기: ");
		int size = sc.nextInt();
		
		int[]arr = new int[size];
		
		for(int i =0; i<arr.length; i++) {
	  arr[i] = (int) (Math.random()*100)+1;
	  }
```

값이 잘 담겨있는지 확인하고, 짝수들의 총합을 계산해보겠습니다.

```java
int sum=0;
		
		for(int i=0;i<arr.length;i++) {
			System.out.print(arr[i]+" ");
			
			if(arr[i]%2==0) {
				sum+=arr[i];
			}
		}
		System.out.println("\n합계 :"+sum);
```

결과를 확인해보세요

![&#xC9DD;&#xC218;&#xB4E4;&#xB9CC; &#xACC4;&#xC0B0;&#xB418;&#xC5C8;&#xC8E0;?](../../.gitbook/assets/image%20%2818%29.png)



이번에는 문자열을 입력받은후 각 인덱스별 문자를 char\[\]배열에 옮겨받아볼까요?

```java
Scanner sc = new Scanner(System.in);
		
		System.out.print("문자열: ");
		String a = sc.nextLine();
		
		//문자열 길이만큼 배열크기지정
		char[] arr= new char[a.length()] ;
		
		for(int i=0;i<a.length();i++) {
			//배열에 값담기
			arr[i]=a.charAt(i);
			//출력
			System.out.print("'"+arr[i]+"'");
		}
```

![&#xC544;&#xC8FC; &#xC798; &#xCD9C;&#xB825;&#xB418;&#xC5C8;&#xC8E0;??](../../.gitbook/assets/image%20%2864%29.png)

## 배열복사

배열을 수정할때에는 배열의 불변성을 유지해줘야 하는데, 배열을 수정하기가 참 까다롭습니다. 

이런경우 배열을 복사해주면 가능하겠죠?

배열복사의 경우에는 2종류가 있습니다.

1. 얕은 복사: 배열의 주소만을 복사
2. 깊은복사: 배열을 새로이 생성하고 실제 내부 값들을 복사

### 얕은복사

먼저 원본배열을 선언해주겠습니다.

```java
//먼저 원본배열을 선언해줍니다.
		int[] origin = {1,2,3,4,5};
		//원본배열 출력
		System.out.println("====원본배열====");
		for(int i=0; i<origin.length;i++) {
			System.out.print(origin[i]+" ");
		}
```

![&#xAC12;&#xC774; &#xC798; &#xB2F4;&#xACA8;&#xC838;&#xC788;&#xC8E0;?](../../.gitbook/assets/image%20%289%29.png)

이제 복사본 배열을 만들어줘야겠죠?

```java
//복사본을 만들어주겠습니다.
		int[] copy = origin;
		//복사배열 출력
		System.out.println("====원본배열====");
		for(int i=0; i<copy.length;i++) {
			System.out.print(copy[i]+" ");
		}
```

![&#xBCF5;&#xC0AC;&#xAC00; &#xC798; &#xB418;&#xC5C8;&#xC8E0;?](../../.gitbook/assets/image%20%283%29.png)

{% hint style="warning" %}
하지만 이렇게 복사를 진행한뒤 복사본을 수정하게되면 원본배열까지 불변성을 잃게됩니다.

이러한 방식을 **얕은 복사 즉 주소복사**라고 합니다.
{% endhint %}



그렇다면 이제부터 깊은 복사에 대하여 알아보도록 하겠습니다.

### 깊은복사

깊은 복사에도 여러가지 방법이 있습니다.

#### 먼저 for문을 이용한 방법을 진행해보겠습니다.

먼저 아래의 코드를 작성해보세요

```java
//먼저 원본배열을 선언해줍니다.
		int[] origin = {1,2,3,4,5};

//원본과 크기가 같은 배열을 만들어줬습니다.
		int[] copy = new int[origin.length];
```

이제 원본의 인덱스별 값을 반복문을 사용해 카피의 인덱스별로 각각 대입해주면 되겠죠?

```java
//먼저 원본배열을 선언해줍니다.
		int[] origin = {1,2,3,4,5};

		//원본과 크기가 같은 배열을 만들어줬습니다.
		int[] copy = new int[origin.length];
		
		for(int i=0; i<copy.length;i++) {
			copy[i] = origin[i];
		}
```

이렇게 말이죠. 자 그럼 차이점이 뭘까요?

{% hint style="info" %}
```java
int[] copy = origin;
```

위의 얕은복사는 배열의 선언과 동시에 origin으로 설정을 해주기 때문에 주소까지 같은 주소를 가지게 됩니다.
{% endhint %}

{% hint style="info" %}
```java
int[] copy = new int[origin.length];
```

반복문을 이용한 복사는 먼저 배열을 선언해주기 때문에 다른 주소값을 먼저 가진뒤에 값을 복사시켜주고 있습니다.
{% endhint %}

#### 두번째. 새로운 배열을 생성하고 `System`클래스에서의 `arraycopy` 메소드를 이용

```java
System.arraycopy(src, srcPos, dest, destPos, length);
```

보이듯이 안에 제시해야하는 값들이 많은데, 다음과 같습니다.

```java
System.arraycopy(원본배열명, 복사를시작한index,
       복사배열명, 복사배열의 시작index, 복사할갯수)
```

예제를 통해 알아볼까요?

```java
//먼저 원본배열을 선언해줍니다.
		int[] origin = {1,2,3,4,5};

//원본보다 크기가 큰 배열을 만들어줍니다.
		int[] copy = new int[10];
		
//값을 옮겨담습니다.
		System.arraycopy(origin,0,copy,2,5);
//원본배열 0 번인덱스부터 5개를 복사본에 2번인덱스부터 복사
		
		for(int i =0; i<copy.length;i++) {
			System.out.print(copy[i]+" ");
		}
```

![](../../.gitbook/assets/image%20%2855%29.png)

#### 세번째.Arrays 클래스의 copyOf 메소드 사용

arraycopy메소드와는 다르게 새롭게 배열을 만들어줄 필요가 없는 매소드입니다.

```java
int[] copy = Arrays.copyOf(원본배열, 복사할갯수(크기));
```

예제를 통해 알아볼까요/

```java
//먼저 원본배열을 선언해줍니다.
		int[] origin = {1,2,3,4,5};

//Arrays.copyOf이용해 배열생성
		int[] copy = Arrays.copyOf(origin,origin.length);
		
//출력
		for(int i=0; i<copy.length;i++) {
			System.out.print(copy[i]+" ");
		}
```

![](../../.gitbook/assets/image%20%2862%29.png)

copyOf 메소드는 갯수를 지정할때 작거나 크게 값을 입력해도 가능하답니다.

#### 

#### 마지막. clone\(\)메소드를 이용한 복사\(있는 그대로를 복사해줌\)

```java
//먼저 원본배열을 선언해줍니다.
		int[] origin = {1,2,3,4,5};

		//origin.clone()이용해 배열생성
		int[] copy = origin.clone();
		
		//출력
		for(int i=0; i<copy.length;i++) {
			System.out.print(copy[i]+" ");
		}
```

![&#xC5ED;&#xC2DC; &#xAC12;&#xC774; &#xC798; &#xCD9C;&#xB825;&#xB418;&#xC5C8;&#xC8E0;?](../../.gitbook/assets/image%20%2813%29.png)

### 배열출력 메소드

Arrays에서는 배열에 대한 다양한 메소드를 제공하고있는데, 정말 유용한 기능이 있습니다!

바로 Arrays.toString\(\)메소드인데요! 배열을 출력시켜준답니다.

```java
System.out.print(Arrays.toString(copy));
```

![&#xB9C8;&#xCC2C;&#xAC00;&#xC9C0;&#xB85C; &#xC798; &#xCD9C;&#xB825;&#xB418;&#xC5C8;&#xC2B5;&#xB2C8;&#xB2E4;.](../../.gitbook/assets/image%20%2829%29.png)

### 

### 배열정렬

만약 아래와 같은 값이 있다고 가정해보겠습니다.

```java
int num1 = 20;
int num2 = 10;
```

크기가 작은 num2를 num1과 변경하고자 한다면 어떻게 해야할까요?

```java
 //기존값
		int num1 = 20;
		int num2 = 10;
		
//기존의 값을 임시로 보관할 변수
		int temp = num1;  //20
		
//값을 대입
		num1 = num2;   //10
		num2 = temp;   //20
```

이렇게 하면 불변성을 잘 유지할 수가 있죠?

이제 배열을 오름차순으로 변경시켜볼까요?

```java
int [] arr = {2,1,3};
```

이런경우에는 index 0번과 1번을 바꿔주면 되겠죠?

```java
//배열선언
int [] arr = {2,1,3};
//임시저장    
	    int temp = arr[0]; //temp=2
//값대입
	    arr[0] = arr[1]; //arr[0]=1
	    arr[1] = temp;   //arr[1}=2
```

자, 여기까지는 쉽게 할 수 있었습니다. 배열의 길이가 짧았기 때문이죠!

그럼 배열의 길이가 길어지면 어떻게 해야할까요?

일단 예제를 보고 이해해보세요

```java
//오름차순정렬: 앞에값이 뒤에값보다 클경우 => 변경
	    int [] arr = {2,1,3,5,4};
//임시변수선언
	    int temp = 0;
	    
//1.비교주체를 선정하는 for문
	  for(int i=0; i<arr.length;i++) {
		  
//2.비교대상을 선정하는 for문
		  for(int j=0;j<i;j++) {
		
//3.앞에값 > 뒤에값 일경우 두 값을 변경
			  if(arr[j]>arr[i]) {
			  temp= arr[i];
			  arr[i]= arr[j];
			  arr[j]= temp;
			  }
		  }
	  }
//출력
	  System.out.print(Arrays.toString(arr));
```

즉 5개의 값을 첫번째 반복문으로 돌아가게 되는데 값 한개마다 그 앞에있는 값들과 비교를 진행해서 값을 서로 바꿔주는 것입니다.

그러나!!! 더 쉬운방법이 있겠죠???

바로 `Arrays.sort(배열명)`   입니다.

위의 거대한?! 코드를 바로

```java
Arrays.sort(arr)
```

한줄만으로 구현하실 수 있답니다...

### 중복제거

```java
//배열 선언
		int [] arr = new int[5];
			
//반복문 돌며 0~마지막 인덱스 랜덤값(1~10)담기
			 for(int i=0;i<arr.length;i++) {
				 arr[i] = (int)(Math.random()*10+1);
			 
//비교대상 for문(기존에 담겨있던 값들이랑 일일이 비교
			 for(int j=0;j<i;j++) {
				 if(arr[i]==arr[j]) {
					 System.out.println("중복발생!");
					 i--; //중복이 발생되는 순간 i값에 다시 랜덤값을 담을 수 있게끔
					 break;
				 }
			 }
			 }
			System.out.println(Arrays.toString(arr));
```

다음에는 중복값을 입력하면 다시 입력하도록 하고 마지막으로 오름차순으로 정렬하여 출력하는 코드를 작성해보세요

```java
public static void main(String[] args) {
	
		Scanner sc = new Scanner(System.in);
		
		int[] arr = new int[5];
		
		for(int i=0;i<arr.length;i++) {
			System.out.print((i+1)+"번째 정수값: ");
			arr[i] = sc.nextInt();
			for(int j=0; j<i; j++) {
				if(arr[i]==arr[j]) {
					System.out.println("중복");
					i--;
					continue;
				}
			}
		}
		Arrays.sort(arr);
		System.out.println(Arrays.toString(arr));
	}
```

