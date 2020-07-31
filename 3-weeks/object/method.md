# Method부

## 메소드

메소드는 기능을 의미합니다.

메소드를 만드는 방법은 다음과 같습니다

```java
 public      []      void          method1     () {
접근제한자 [예약어] 반환할값의자료형 메소드명 ([파라미터])
수행할 코드
수행할 코드
return 반환값  막약 반환값이 없다면 위에 자료형을 void로한다.
}
```

그동안 작성하던 코드라 많이 익숙하실것입니다.

다음은 매개변수의 유무와 반환값 유무에 따른 구분을 해보겠습니다.

### 1.파라미터가 업고 반환값도 없는 메소드

```java
public void method(){

}
```

### 

### 2.파라미터는 없지만 반환값 있는 메소드

```java
public double method2(){
          return Math.random();
}
```

### 

### 3.파라미터는 있지만 반환값은 없는 메소드

```java
public void method3(int num1, int num2){
        System.out.print(num1+num2);
}
```

### 

### 4.파라미터도 있고 반환값도 있는 메소드

```java
public void method4(int num1, int num2) {
          return num1-num2;
}
```





