# 예외처리\(Exception\)

### 에러종류

* 시스템 에러 : 컴퓨터 오작동으로 발생하는 에러 --&gt;소스코드로 해결 안됨 -&gt; 심각한 에러
* 컴파일 에러 : 소스코드 문법상 오류 --&gt; 빨간줄로 애초에 알려줌
* 런타임 에러 : 코드 상으로는 문제가 없는데 프로그램 실행할 때 발생하는 에러 \(사용자의 실수일 수도 있고 개발자가 예측가능한 경우를 제대로 처리못한 경우\)
* 논리 에러 : 문법상으로도 문제없고 실행했을 때 궂이 문제되지는 않지만 프로그램 의도상 맞지 않는것.

### 

### 예외처리

시스템 에러를 제외한 컴파일 / 런타임 / 논리 에러와 같은 비교적 덜 심각한 에러를 해결한다. =&gt; 이런것들을 '예외' 라고 한다. \(Exception\)

이런 예외들이 "발생"했을 경우에 대해서 "처리"하는 방법 =&gt; 예외처리

예외처리를 안해놓으면 해당 예외 발생시 프로그램이 비 정상적으로 종료되버림

```java
int[]arr = null;
System.out.pirntln(arr[0]);   //nullPointException 발생

System.out.println("안녕하세요 여러분들!!");//실행되지 않는다.
```

### 예외처리 종류

* RuntimeException
*   -NullPointerException
*   -IndexOutOgBoundsException
*   -ClassCastEception
*   -AtithmeticException
*   -InputMismatchException

RuntimeExeption은 예외처리가 필수가 아니기 때문에 UnCheckedExeption 이라고도 부릅니다.

* IOExeption
* SQLExeption

위 두가지와 같은 예외는 반드시 예외처리를 해줘야만 합니다.

## Unchecked Exception

프로그램 실행시 발생되는 예외들 \(문법적으로는 문제되지 않는다.\)

{% hint style="info" %}
즉, 예외처리가 필수는 아닙니다.
{% endhint %}

### RuntimeException의 후손들

#### NullPointerException

레퍼런스변수가 null인 상태에서 메소드를 호출하는 경우

#### ArrayIndexOutOfBoundsException

배열의 접근에 부적절한 인덱스 값 제시했을 경우

#### ClassCastException

허용할 수 없는 형변환이 진행되는 경우

#### ArithmeticException

나누기 연산시 0으로 나누는 경우

#### NegativeArraySizeException

배열의 크기를 음수로 지정했을 경우



예시

```java
//사용자에게 두개의 정수값을 입력받은 후 나눗셈 연산후 결과 출력
System.out.print("정수1:");
int num1 = sc.nextInt():

System.out.print("정수2:");
int num2 = sc.nextInt():

int result = num1/num2;  
//이때 num2에 0이 들어가게 되면 exception 발생
```

해결

```java
//사용자에게 두개의 정수값을 입력받은 후 나눗셈 연산후 결과 출력
System.out.print("정수1:");
int num1 = sc.nextInt():

System.out.print("정수2:");
int num2 = sc.nextInt():

if(num2 != 0){
int result = num1/num2;  
}
```

### 예외처리방법 

#### TryCatch

```java
System.out.print("정수1:");
int num1 = sc.nextInt():

System.out.print("정수2:");
int num2 = sc.nextInt():

int result =0;

try{
   result = num1/num2;           //예외가 발생될법한 구문
}catch(ArithmeticException){      //발생예상되는 예외클래스
System.out.println("0으로 나눌 수 없다.");//해당 예외가 발생되는 경우 처리할 구문
}
```

#### 다중catch

```java
try{
    int[] arr = new int[size];
        System.out.println("0번 인덱스");
}catch(NegativeArraySizeException e){
    System.out.println("양수를 입력하세요");
}catch(ArrayIndexOutOfBoundsException e){
    System.out.println("부적절한 인덱스에 접근");
}catch(InputMismatchException e){

}
```

{% hint style="info" %}
UnCheckedException은 예외처리를 해도 되고 안해도 됩니다.

만약 예측가능한 상황에 있어서 if문으로 조건처리가 가능하다면,

애초에 예외가 발생하기 이전에 조건문으로 핸들링 해주세요!
{% endhint %}



CheckedException

반드시 예외처리를 해줘야 하는 예외들

예측 불가능한 상황에 있어서 예외가 발생하기 때문에 미리 예외가 발생할때는 대비해 처리하는 구문을 기술해야 한다.

보통 외부매개체와 어떤 입출력이 발생할때 Exception이 발생한다.

들어가기에 앞서 Sacnner이전에 쓰이던 BufferedReader를 한번 알아보겠습니다.

```java
BufferdReader br = new BufferdReader(new InputStreamReader(System.in));

System.out.print("//아무문자열이나 입력해주세요");
String str = br.readLine();      //IOException이 발생할 수도 있다고 경고가 나온다.
```



예외처리2

throws - 지금 당장 여기서 예외처리 하지 않고 해당 이 메소드를 호출한 곳으로 떠넘기겠다\(위임\)

|  | 예외발생시점 | 예외처리 |  |
| :--- | :--- | :--- | :--- |
| RuntimeException | 런타임 에러\(프로그램실행\) | 세모\(개발자마음\) | UnCheckedException |
| RuntimeException외 | 컴파일에러\(빨간줄\) | 필수 | CheckedException |



