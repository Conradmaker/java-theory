# 입출력\(IO\)

## IO

Input & Output의 약자, 컴퓨터 내부 또는 외부 장치와 프로그램 간의 데이터를 주고 받는 것 장치와 입출력을 위해서는 하드웨어 장치에 직접 접근이 필요한데 다양한 매체에 존재하는 데이터들을 사용하기 위해 입출력 데이터를 처리할 공통적인 방법으로 스트림 이용

![&#xC2A4;&#xD2B8;&#xB9BC;&#xC740; &#xD1B5;&#xB85C;&#xC758; &#xC5ED;&#xD560;&#xC744; &#xC218;&#xD589;&#xD55C;&#xB2E4;.](../../.gitbook/assets/image%20%2822%29.png)

## 스트림\(Stream\)

데이터를 읽고 쓰기위해 자바에서 제공하는 클래스

모든 스트림은 단방향이며 각각 장치마다 스트림 존재함

하나가 입출력 동시에 불가능 --&gt; 동시에 하려면 2개 필요

### 스트림의 특징

* 단방향: 입력이면 입력 / 출력이면 출력
* 선입선출\(FIFO\) 먼저 보낸값이 먼저 나감 \(시간지연\)

### 스트림의 종류

![](../../.gitbook/assets/image%20%2841%29.png)

### 자바에서 제공하는 스트림 클래스

| 기능 | 종류 | 방향 |
| :---: | :---: | :---: |
| 출력용 스트림 | OutputStream  /  Writer  | 프로그램 ---&gt;&gt;  외부매체 |
| 입력용 스트림 | InputStream / Reader | 외부매체 ---&gt;&gt;  프로그램 |

#### 통로의 사이즈

| 종류 | 넓이 | 크기 | 종류\(입력 / 출력\) |
| :---: | :---: | :---: | :---: |
| 바이트 스트림 | 좁은통로 | 1byte | InputStream / OutputStream |
| 문자 스트림 | 넓은통로 | 2byte | Writter / Reader |

#### 외부매체와 직접 연결하는 유무

| 종류 | 역할 | 특징 |
| :---: | :---: | :---: |
| 기반\(기본\) 스트림 | 외부 매체와 직접적으로 연결 | 필수 |
| 보조 스트림 | 보조 역할만 수행 | 선택 \(단독불가\) |



## DAO

Data Access Object

### 바이트 기반 스트림

데이터를 1byte 단위로 밖에 전송이 불가능한 외부매체와 직접 연결되는 통로\(좁은 통로\)

{% hint style="danger" %}
1byte이기 때문에 한글의 경우 깨짐
{% endhint %}

즉, 외부매체를 지정하고 그 외부매체와 직접적으로 연결된 통로에 데이터를 1byte 단위로 전송한다.

* XXXInputStream : XXX매체로부터 데이터를 입력받는 통로\( 외부매체로부터 읽어온다\)
* XXXOutputStream : XXX매체에 데이터를 출력하는 통로 \(외부매체로 데이터를 내보내겠다\(기록\)\)

| XXX | 외부매체 |
| :--- | :--- |
| FIle | 파일 |
| Audio | 오디오장치 |
| Piped | 또다른 프로그램 |

### FileOutputStream

프로그램\(자바코드\) -&gt; 외부매체\(파일\) \(출력\)

{% tabs %}
{% tab title="FileByteTest" %}
{% code title="FileByteTest.java" %}
```java
public void fileSava(){
    //
    //1.FileOutputStram객체 생성 : 연결통로 생성
    //('파일'로 데이터를 1바이트 단위로 출력하는 스트림)
    try{
        FileOutputStream fos = new FIlewOutputStream("a_byte.text");
        // 만약 파일이 없다면 자동으로 생성된다.
        
        //2. 통로로 데이터 출력 :write() 메소드 사용
        //   단 1바이트 단위로밖에 데이터 출력 불가
        fos.write(97);  // -127~127
        fos.write('b'); // 한글자 
        fos.write('강');// ㄱ + ㅏ + ㅇ
        fos.write('ㄱ');//깨짐
        
        //바이트 배열도 출력 가능
        byte[] bArr = {99,100,101}; //cde
        fos.write(bArr);
        //fos.write(배열, 시작인덱스, 갯수)=>배열의 시작인덱스부터 갯수만큼 출력
        fos.write(bArr,1,2);
       
    }catch(FileNotFoundException e){
        //존재하지 않는 경로라면 catch문에 걸린다.
        e.printStackTrace();
    }catch(IOException e){
        e.printStackTrace();
    }finally{
        //어떤 예외가 발생하든 실행
        try{
       //3.스트림 다 이용했으면 반납하기(close메소드) 
       fos.close();  //원래 IOException 문제가 있지만 catch문이 있어 에러 발생X
       }catch(IOException e){
        e.printStackTrace();
       }
     }
}
```
{% endcode %}
{% endtab %}

{% tab title="a\_byte.text" %}
```text
ab?1

97은 해당 숫자의 아스키코드(0~127)값의 문자가 저장됨 - a
b - b
강 - 깨짐
ㄱ - 1 (깨짐)


```
{% endtab %}
{% endtabs %}

하지만 이렇게 하게되면 기존 파일에 덮어씌워지게 됩니다.

연이어서 작성하고 싶다면 객체생성시 다음과 같이 작성해줘야 합니다.

{% tabs %}
{% tab title="FileByteTest" %}
{% code title="FileByteTest.java" %}
```java
FileOutputStream fos = new FIlewOutputStream("a_byte.text",true);
//true를 작성하면 기존 파일이 있을경우 연이어서 작성이 된다.
```
{% endcode %}
{% endtab %}
{% endtabs %}



### FileInputSream

파일에 기록된 데이터 가져오기

{% tabs %}
{% tab title="Java" %}
{% code title="FileByteTest.java" %}
```java
public void fileRead(){
  //FileInputStream: 파일로부터 데이터를 1바이트 단위로 받아오는 스트림
  
  //1.FileInputStream 객체 생성 : 해당 파일과의 연결통로가 만들어짐
  FileInputStream fis = null;
  try{
    fis = new FIleInputStream("a_byte.txt");
    
    //2.파일로부터 데이터를 입력받고자 할때 read()메소드 사용
    fis.read(); //단 1byte씩 불러오기 때문에 7글자라면 7번 사용해야함
    fis.read();
    fis.read();
    fis.read();
    fis.read();
    fis.read();
    fis.read();
  }catch(FileNotFoundException e){
    e.printStackTrace();
  }catch(IOException e){
        e.printStackTrace();
  }
}
```
{% endcode %}
{% endtab %}

{% tab title="text" %}
```
abcdede
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
이러한 경우에는 반복문을 통해 수행해 줘야 합니다.

또한 계속 읽어오다가 끝을 넘어가게 된다면 -1이 출력되게 됩니다.

이를 이용해 반복문을 작성해보겠습니다.
{% endhint %}

{% code title="FileByteTest.java" %}
```java
public void fileRead(){
  //FileInputStream: 파일로부터 데이터를 1바이트 단위로 받아오는 스트림
  
  //1.FileInputStream 객체 생성 : 해당 파일과의 연결통로가 만들어짐
  FileInputStream fis = null;
  try{
    fis = new FIleInputStream("a_byte.txt");
    
    //2.파일로부터 데이터를 입력받고자 할때 read()메소드 사용
    while(fis.read() != -1){ //-1이 아닐경우 출력
      System.out.println(fis.read());
    } 
    
  }catch(FileNotFoundException e){
    e.printStackTrace();
  }catch(IOException e){
        e.printStackTrace();
  }
}
```
{% endcode %}

{% hint style="danger" %}
하지만 뭔가 이상합니다.

{% code title="FileByteTest.java" %}
```java
while(fis.read() != -1){  //1번 fis.read()
      System.out.println(fis.read());  //2번 fis.read()
    } 
```
{% endcode %}

1번검사 -&gt; 2번출력 -&gt;3번검사 -&gt;4번출력 이렇게 되기 때문에 값이 잘못출력되죠.

즉 fis.read\(\)는 반복문이 수행될때마다 딱 한번만 실행되야 합니다.
{% endhint %}

해결방법.1 무한반복으로 돌리면서 조건검사

{% code title="FileByteTest.java" %}
```java
public void fileRead(){
  //FileInputStream: 파일로부터 데이터를 1바이트 단위로 받아오는 스트림
  
  //1.FileInputStream 객체 생성 : 해당 파일과의 연결통로가 만들어짐
  FileInputStream fis = null;
  try{
    fis = new FIleInputStream("a_byte.txt");
    
    //2.파일로부터 데이터를 입력받고자 할때 read()메소드 사용
    while(true){ //-1이 아닐경우 출력
     int value = fis.read();
     if(value != -1){
       System.out.println(value);
     }else{
       break;
     }
    } 
    
  }catch(FileNotFoundException e){
    e.printStackTrace();
  }catch(IOException e){
        e.printStackTrace();
  }
}
```
{% endcode %}

해결방법.2



{% code title="FileByteTest.java" %}
```java
public void fileRead(){
  //FileInputStream: 파일로부터 데이터를 1바이트 단위로 받아오는 스트림
  
  //1.FileInputStream 객체 생성 : 해당 파일과의 연결통로가 만들어짐
  FileInputStream fis = null;
  try{
    fis = new FIleInputStream("a_byte.txt");
    
    //2.파일로부터 데이터를 입력받고자 할때 read()메소드 사용
    int value = 0; //매번 입력받아온 데이터를 기록할 변수
    while(value = fis.read()) != -1){ 
       System.out.println(value+ " ");
    } 
    
  }catch(FileNotFoundException e){
    e.printStackTrace();
  }catch(IOException e){
        e.printStackTrace();
  }
}
```
{% endcode %}

만약 문자 그대로의 값을 확인하고 싶다면 강제형변환을 해주세요

```java
System.out.println((char)value+ " ");
```

### 문자열 기반 스트림

### FileWriter 

```java
public void fileSava(){
    //FileWriter : 파일을 2바이트 단위로 출력
    //1.FileWriter 객체 생성
    FileWriter fw = null;
    try{
    fw = new FIleWriter("b_char.dat");
    
    //2.통로로 데이터 출력:write()메소드 이용
    fw.write('A');
    fw.write(' ');
    fw.write("와!IO 어렵다...");
    
    //char[] 배열 전송가능
    char[] cArr = {'a','b','c'}
    fw.write(cArr);
    
    }catch(FileNotFoundException e){
        e.printStackTrace();
    }catch(IOException e){
        e.printStackTrace();
  }
}
```

해당 스트림을 다쓴뒤 자동으로 close\(\)까지 해주는 구문인 tryWithResource를 작성해보세요

{% tabs %}
{% tab title="try/catch" %}
```java
try{
}catch(예외클래스명 e){
}
```
{% endtab %}

{% tab title="tryWithResource" %}
```java
try(FileWriter fw = new FilewWriter("b_char.dat")){


}catch(){}
```
{% endtab %}
{% endtabs %}

프로그램 &lt;-- 파일

```java
public void fileRead(){
    //FileReader : 파일로 데이터를 2바이트 단위로 입력받기
    
    try(FileReader fr = new FIleReader("b_char.dat")){
        int value = 0;
        while((value - fr.read())!= -1){
            System.out.print(value);
        }
    
    }catch(FileNotFoundException e){
        e.printStackTrace();
    }catch(IOException e){
        e.printStackTrace();
    }

}
```

