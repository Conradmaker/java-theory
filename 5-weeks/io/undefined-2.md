# 보조스트림

## 보조스트림

보조역할만을 수행한다.\( 즉, 기반스트림만으로부족한 기능들을 제공\)

속도향샹 , 객체단위로 입출력 가능하게끔, 추가적인 유용한 메소드 제공



### 프로그램 --&gt; 파일 \(출력\)

{% code title="try catch" %}
```java
import java.io.BufferedWriter;

    //프로그램 --> 파일 (출력)
    public void fileSave(){
    //1.기반스트림 먼저 생성(어떤 "외부매체"와 데이터를 주고 받을 것인지 선택
    FileWriter fw = new FileWriter("c_buffer.dat");
    
    //보조스트림 객체 생성(해당 기반스트림 객체를 담은 채로 생성)
    BufferedWriter bw = new BufferedWriter();
    }
```
{% endcode %}

{% hint style="info" %}
기반스트림이 Writer이면 보조스트림도 Writer이여야만 한다.
{% endhint %}

아래와 같이도 작성할수 있습니다.



{% code title="try with resource" %}
```java
import java.io.BufferedWriter;

//프로그램 --> 파일 (출력)
 public void fileSave(){
  
   try(BufferedWriter bw = new BufferedWriter(mew FileWriter("c_buffer.dat"))){
     //데이터 출력: write()
     bw.write("안녕하세요");
     bw.write("반가워요");
     //버퍼에 계속 쌓다가한번에 출력
   
     bw.newLine(); //기반스트림에서 제공안하는 메소드도 제공(개행)
     bw.write();
    }catch(IOException e){
     e.printStackTrace();
    }
   
}
```
{% endcode %}



### 프로그램 &lt;-- 파일 \(입력\)ja

```java
public void fileRead(){
    //BufferedReader객체 생성
   try(BufferedReader br = new BufferedReader(new FileReader("c_buffer.dat"))){
   
       System.out.println(br.readLine()); //한 줄단위로 읽어들임
       System.out.println(br.readLine());
       System.out.println(br.readLine());
       System.out.println(br.readLine()); 
       //파일의 끝을 만나는 순간 null을 반환
   
       String value = null;
       while(value = be.readLine()) !=null{
           System.out.println(value);
       }
   }catch(IOExeption e){
       e.printStackTrace();
   }
}
```





{% tabs %}
{% tab title="VO" %}
{% code title="Phone.java" %}
```java
//필드
private String name;
private String brand;
private int price;

//기본생성자
public Phone(){}
//매개변수 생성자
public Student(String name, String brand, int price) {
			super();
			this.name = name;
			this.brand = brand;
			this.price = price;
		};
		
public String getName() {
	return name;
}

public void setName(String name) {
	this.name = name;
}

public String getBrand() {
	return brand;
}

public void setBrand(String brand) {
	this.brand = brand;
}

public int getPrice() {
	return price;
}

public void setPrice(int price) {
	this.price = price;
}

```
{% endcode %}
{% endtab %}

{% tab title="DAO" %}
{% code title="ObjectDao.java" %}
```java
                        // 직렬화
public class Phone implements java.io.Serializable{ 

//프로그램 --> 파일(출력)
public void fileSava(){
    phone ph = new Phone("갤럭시","삼성",1500000);
    
    //객체 자체를 파일에 출력할 때 사용되는 스트림
    //ObjectOutputStream : 객체 단위로 출력 가능한 메소드 제공해주는 보조스트림
    //FileOutputStream : 파일에 출력시 사용되는 기반 스트림
    
    try(ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream("phone.dat"))){
        
        //객체 자체를 출력시 writeObject() 메소드 이용
        oos.writeObject(ph);
    
    }catch(FileNotFoundException e){
        e.printStackTrace();
    }catch(IOExeption e){
       e.printStackTrace();
    }
}

//프로그램 <-- 파일(입력)
public void fileRead(){
    //파일에 기록된 객체 단위를 입력받기 위한 스트림 클래스
    //ObjectInputStream : 객체 단위로 읽어들이기 위해 필요한 보조스트림 클래스
    //FileInputStream : 파일에 기록된 데이터를 입력받기 위한 기반 스트림 클래스
    try(ObjectInputStream ois = new ObjectInputStream(new FileInputStream("phone.dat"))){
        
        //객체 단위로 읽어올때 readObject() 메소드 이용
        oos.readObject(ph);
    
    }catch(FileNotFoundException e){
        e.printStackTrace();
    }catch(IOExeption e){
       e.printStackTrace();
    }
}
}
```
{% endcode %}
{% endtab %}

{% tab title="ObjectsDAO" %}
```java
phone[] arr = new Phone[3];
arr[0] = new Phone("벨벳" , "엘지" , 100000);
arr[1] = new Phone("갤럭시" , "삼성" , 120000);
arr[2] = new Phone("아이폰" , "애플" , 130000);

//객체단위로 파일에 출력시 사용되는 스트림 클래스
//ObjectOutputStream : 객체 단위로 출력가능한 보조 바이트 스트림
//FileOutputStream : 파일과 직접적으로 연결한 후 데이터 출력 가능한 기반 바이트 스트림

//새로운 객체 생성과 함께 새 파일도 생성
try(ObjectOutputStream oos = new ObjectOutputStream(new FIleOutputStream("phones.dat"))){

}catch(FileNotFoundException e){
        e.printStackTrace();
}catch(IOExeption e){
        e.printStackTrace();
}

//프로그램 <-- 파일(입력)
public void fileRead(){
       //파일에 기록된 데이터를 객체단위로 입력받아올 떄 필요한 스트림
       //ObjectInputStream : 객체단위로 입력받을 수 있는 보조 바이트 스트림
       //FileInputStream : 파일과 직접적으로 연결해서 데이터를 입력 받을 수 있는 기반 바이트 스트림
       try(ObjectInputStream ois = new ObjectInputStream(new FileInputStream("phone.dat"))){
              //잘 담겨있는지 파악
              System.out.println(ois.readObject()); //1번객체
              System.out.println(ois.readObject()); //2번객체
              System.out.println(ois.readObject()); //3번객체
              
              //파일의 끝을 만났을 때
              //read() : -1 반환
              //readLine() : null반환
              //readObject() : EOFExeprion 발생 (EOF: End Of File)
              while(true){
                     System.out.println(ois.readObject());
              }
       }catch(FileNotFoundException e){
              e.printStackTrace();
       }catch(EOFException e){ //IOException 의 자식요소이기 때문에 작성안해도 상관없지만, 확인하고 싶다면 부모보다 위에 있어야함.
              System.out.println("파일을 다 읽었습니다.");
       }catch(IOExeption e){
              e.printStackTrace();
       }catch(ClassNotFoundException e){
              e.printStackTrace();
       }
}
```
{% endtab %}

{% tab title="Run" %}
```
public static void main(String [] args){
    
}
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
마우스 오른쪽 -&gt; Source -&gt; constructor / Setter /Getter 자동완성 

alt+shift+s   +   o    -&gt;  constructor자동완성

alt+shift+s   +   s   +    alt+a   +     alt+r   -&gt;Setter/Getter
{% endhint %}

{% hint style="danger" %}
조그만 통로에 큰 데이터가 지나가야 하기 때문에 직렬화를 해줘야만 한다.

{% code title="ObjectDao.java" %}
```java
public void 클래스 implements java.io.Serializable{

}
```
{% endcode %}
{% endhint %}



