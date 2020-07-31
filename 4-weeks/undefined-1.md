# 오버로딩

오버로딩

오버로딩이란 한 클래스 내에 같은 메소드명으로 정의할 수 있는 방법입니다.

아래와 같은 메소드가 있다고 가정해보세요

```java
public void test(){ }
```

만약 실행클래스에서 위의 메소드를 실행시키려면 x.test\(\)라고 호출하겠죠?

아래에 같은 메소드를 작성해보세요

```java
public void test(){ }
public void test(){ }//에
```

에러가 나게 됩니다.

그럼 아래에 또 다른 메소드를 만들어 볼까요?

```java
public void test(){ }
public void test(int a){ } //성
```

이름이 같지만 오류가 나타나지 않는 이유는 파라미터가 들어오면 아래메소드가 출력, 

없다면 위의 메소드가 실행되기 때문입니다.

그렇다면 하나 더 만들어볼까요?

```java
public void test(){ }
public void test(int a){ } //성
public void test(int a,int b){ } //성
```

이해 하셨나요?

Overloading 은 파라미터가 다르면 적용되는 것입니다.

{% hint style="warning" %}
단, 변수 명이 다른것이 아닌 변수의 자료형이 달라야 한답니다.

또한 접근제한자, 공급형에 상관없이 무조건 변수의 자료형이 달라야 한답니다.
{% endhint %}

