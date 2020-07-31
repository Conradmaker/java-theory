# Date 클래스

## Date \(java.util\)

Date는 자바 개발할 당시 초창기에 만들어져서 완성도가 높지 않다.

다국적으로 쓰기에도 적합하지 않다.

### 기본생성자 생성

시스템 날짜 \(현재 날짜\)를 담고있음.

```java
Date today = new Date();
System.out.println(today);
```

### 내가 원하는 날짜 생성

1.매개변수 생성자를 통해서 생성

```java
Date data = new Date(2020,6,19); 
```

{% hint style="warning" %}
Deprecated 메소드 즉, 사용할때 주의해서 사용해야만 한다.
{% endhint %}

```java
Date data = new Date(2020,6,19); 
//내부적으로 전달한 년도 +1900
                  월  +1  을 한뒤에 출력하기 때문에 -를 해준뒤 널어줘야 한다.
```

2.기본생성자로 생성한 후 setter메소드로 값 변경

```java
Date date2 = new Date();

date2.setYear(2020);
date2.setMinth(6);
date2.setDate(19);
```

### 내 입맛대로의 포맷을 지정하고싶을떄

1. java.text.SimpleDateFormat 클래스

```java
//2020년 07월 22일 19시 36분 22초
SimpleDateFormat sdf = new SimpleDateForemat("yy년 MM월 hh시 mm분 ss초");

//today--> 포맷 지정한 채로 --> String
String formatDate = sdf.format(today);
```

