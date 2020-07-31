# 유용한 메소드

## Math

* 모든 필드 상수필드, 모든 메소드 static메소드
* static -&gt; 프로그램 시작할 때 딱 한번 static메모리 영역에 올린다.
*                 Math객체 생성이 필요없이 클래스명. 으로 접근 가능.
* 한번만 메모리 영역에 올려놓고 재사용하는 개념 ==&gt; 싱글톤 패턴

### 파이

```java
System.out.println("파이: " + Math.PI);
```

### 절대값 

```java
int num1 = -10;
System.out.println("절대값: " + Math.abs(num1));
```

### 올림

```java
double num2 = 4.349;
System.out.println("올림: " + Math.ceil());
//단 실수값으로 반환한다.
```

### 반올림

```java
double num2 = 4.349;
System.out.println("반올림: " + Math.round());
//정수값으로 반환한다.
```

### 버림

```java
double num2 = 4.349;
System.out.println("버림: " + Math.floor());
//정수값으로 반환한다.
```

### 가장 가까운 정수값

```java
double num2 = 4.349;
System.out.println("버림: " + Math.rint());
//실수값으로 반환한다...rint
```

### 제곱근 \(루트\)

```java
System.out.println("4의 제곱근: " + Math.sqrt(4)); 
```

### 제곱

```java
System.out.println("2의 10제곱: " + Math.pow(2, 10)); 
```





## String클래스 

* 불변클래스\(변하지 않는 클래스\)
* --&gt; 수정하는 순간 그자리에서 변경이 되지 않음
* --&gt;빈번하게 값을 변경할 경우 가비지컬렉터가 계속 기존의 값들을 지워줘야 한다는 단점.
* 변경이 적고 읽기만 할 경우 String 클래스가 용이

### 생성자를 통한 문자열 생생

```java
String str1 = new String("hello");
String str2 = new String("hello");
```



### 일부 문자열만 추출하고자 할때

```java
문자열.subString(int beginIndex) : String
문자열.subString(int beginIndex,int endIndex) : String
```

* 1번 문자열의 begin 인덱스 위치에서부터 끝까지의 문자열을 추출
* 2번 문자열의 begin 인덱스 부터 end 인덱스 이전\(포함x\)까지 추출해주는 메소드



### 문자열에서의 old문자를 new 문자로 변환해 문자열 리턴

```java
String str4 = str1.replace('1','c');
```



### 문자열 대문자 / 소문자로 변환

```java
String str5 = str1.toUpperCase();   //대문자로 변환
String str5 = str1.toLowerCase();   //소문자로 변환
```



### 구분자를 이용해 해당 문자열을 분리 시키는 방법

1. **분리된 문자열들을 배열로 차곡차곡담아서 처리하고 싶을 때 String 클래스에 제공하는 split 메소드 이용. `문자열.split(String 구분자): String[]`**

```java
String str = "Java,Node.js,React,Vue,Html,Css"
String[]arr = str.split(",");
// , 마다 문자열을 분리해 배열의 길이는 6이 됩니다.
```



####    2. 분리된 각각의 문자열들을 객체로 취급하고 싶을 때 `java.util.StringTokenizer` 클래스를 이용하는 방법.`StringTokenizer stn = new StringTokenizer(분리시킬 문자열, 구분자);`

```java
import java.util.*;

String str = "Java,Node.js,React,Vue,Html,Css"

StringTokenizer stn = new StringTokenizerstr,","); //기본생성자가 없기때문에 파라미터 필수!
System.out.println("문자열의 객수: " + stn.countToken()); //몇개의 토큰이 있는지
System.out.println(stn.nextToken()); //앞에서 하나 뽑아온다. (Java)
System.out.println(stn.nextToken()); //앞에서 하나 뽑아온다. (Node.js)
//단 ! 불변성을 잃을 수 있기 때문에 유의해햐한다.
//또한 반복문 사용시에 값이 줄어들면 i가 줄어들기 때문에 유의해야 한다.
```

####   3.여러가지 문자를 분리시키는방법

```java
String colors = "red/tellow#green blue,orange";

//split방법
String[] arr = colors.split("[/#,]");  //여러가지 지정

for(String s : arr){
    System.out.print(s);
}
```

## 가변클래스\(StringBuilder/StringBuffer\)

* String과는 다르게 그자리에서 값이 변경되는 개념이다.
* 두 클래스 모두 생성자나 제공하는 메소드가 동일하다.
* 유일한 차이점은 동기화가 되냐 안되냐의 차이 --&gt; 곧 속도차이이다.

Builder = 동기화 제공 X  /  Buffer = 동기화 제공 ㅇ

멀티스레드환경\(여러개의 일처리를 병행해서 동시다발적으로 수행하는 환경\) -&gt;동기화 처리가 되는걸로 실행

단일 스레드 환경 -&gt; 동기화 작업을 하게 되면 속도 저하가 발생될 수 있음. 

```java
public void method1(){
    //StringBuilder, StringBuffer 객체 생성시 처음에 16개의 문자를 저장할수 있는 버퍼가 생성
    StringBuilder sb1 = new StringBuilder();  //수용량: 16  (sb.capacity())로 확인
    
    StringBuilder sb2 = new StringBuilder(30);  //수용량: 30 
    //전달한 정수값만큼 크기가 지정된다.
    
    StringBuilder sb2 = new StringBuilder("반가워");  //수용량: 21
    //문자열도 바로 저장할 수 있다.
  
  
  //StringBuilder
  StringBuilder sb = new StringBuilder("반가워");
  
  System.out.println
  System.out.println("주소값" +System.identityHashCode(sb));
  System.out.println("수용량" +sb.capacity()); //16+4
  System.out.println("문자열의 길이" +sb.length());
 
}
```

### StringBuilder 담긴 문자열을 변경할때

#### 1.append\(String str\) 기존의 문자열에 새로운 문자열을 추가

```java
sb.append("안녕");
//주소값 변동없음 == 그자리에서 문자열 변경 ==가변
```

#### 2.delete\(int start, int end\) 문자열 삭제

```java
sb.delete(2,5) //2번인덱스에서 5번인덱스까지 삭제
//SubString과 마찬가지로 end 인덱스 전까지 삭제해준다.
```

#### 3.insert\(int offset, String str\)  기존 문자열 사이에 또다른 문자열 추가하기

```java
sb.insert(1, "ㅎㅎㅎ");
//1번 인덱스에 ㅎㅎㅎ을 추가한다.
```

#### 4.reverse\(\) 기존의 문자열을 역으로 바꿀때

```java
sb.reverse();
```

#### 예시

```java
public void method3(){
    StringBuilder sb = new StringBuilder("JavaProgram");
    
    sb.append("API").delete(4,11).reverse();
    //append: JavaProgramAPI
    //delete: JavaAPI
    //reverse: IPAavaJ
}
```



