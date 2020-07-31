# Wrapper 클래스

## wrapper 클래스

기본자료형을 객체로 포장해주는 클래스가 Wrapper클래스다.

| 기본자료형 | Wrapper클래스 |
| :--- | :--- |
| boolean | Boolean |
| char | Character |
| byte | Byte |
| short | Short |
| int | Integer |
| long | Long |
| float | Float |
| double | Double |

기본 자료형으로 사용을 해도 되지만 프로그램에 따라 해당 기본자료형을 객체로 취급해야 되는 경우 있음

* 메소드 호출해야 할떄
* 메소드의 매개변수로 기본자료형이 아닌 객체 타입만이 요구될 떄
* 다형성을 적용시키고 싶을 때

```java
public void method1(){

    //Boxing : 기본자료형 --> Wrapper 클래스 자료형
    int num1 = 10;
    int num2 = 15;

    //1. 객체 생성을 통한 방법 (9version 부터 사용불가)
    Integer i1 = new Integer(num1);
    Integer i2 = new Integer(num2);
    
    System.out.print(i1==i2); //false
    
    //이렇게 객체가 되면 메소드 이용가능.
    System.out.println(i1.equals(i2));  //false
    System.out.println(i1.compareTo(i2)); //-1
    //두값을 비교해 앞쪽이 크면 1반환, 뒤가크면 -1반환 같으면 0
    
    //2.객체 생성하지 않고 바로 대입하는 방법 ( AutoBoxing)
    Integer i3 = num2; //num2 --> i3
    
    //언제 객체생성을 통해서 변환하나?
    
    //언박싱
    //메소드를 사용하지 않고 바로 대입하는 방법 (AutoUnBoxing)
    int num3 = i1;  //10
    
    
}
```

## 기본자료형 &lt;---&gt; String

```java
String str1 = "10";
String str2 = "15.3";

System.out.println(str1 + str2); //문자열로 작업됨
```

### 1.String --&gt; 기본자료형 \(파싱\)

Wrapper 클래스.parseXXX\(\)사영

```java
int i = Integer.parseInt(str1); //10
int d = Double.parseDouble(str2); //15.3
```



2.기본형 --&gt; Wrapper --&gt; String

```java
String strI = String.valueOf(i); //"10"
String strD = String.valueOf(d); //"15.3
```

