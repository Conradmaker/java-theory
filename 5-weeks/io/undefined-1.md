# 파일만들기

Java.io 패키지에 있는 File클래스사용

```java
try{ 
    //1.경로지정 안한 파일 생성 -> 해당 이 프로젝트에 파일 생성
    Filw f1 = new File("test.txt");
    f1.createNewFile(); //메소드 실행해야 실제 파일생성 ->IOException 발생가능
    
    //2.존재하는 기존 드라이브나 폴더에 파일 생성
    File f2 = new File("D:\\test.text");
    f2.createNewFile();
    
    //3.폴더 만들고 파일 생성
    File tempFolder = new File("D:\\temp");
    tempFolder.mkdir();                //폴더생성 메소드
    File f3 = new File("D:\\temp\\test.text");
    f3.createNewFile();                //파일생성
    
    //4.확인하기
    System.out.println(f1.exists());  //확인메소드  
    System.out.println(f2.exists());
    System.out.println(TempFolder.exists());

}catch(IOException e){
    e.printStackTrace();   //추적해서 알려준다.
}
```

{% hint style="danger" %}
\\ 을 꼭 기억해주세요!

만약 C드라이브안에 바로 경로를 설정하게 되면 관리자 권한이 필요하기 때문에

C드라이브로 저장하기 위해서는 존재하는 폴더에 저장해주세요
{% endhint %}



아래와 같이 별도로 경로지정을 안하면 해당 프로젝트에 생성된다. 

```java
try{
    File folder = new File("parent");
    folder.mkdir();
    File file = new FIle("parent\\person.txt")
    file.createNewFile();    

}catch(IOException e){
    e.printStackTrace();   
}
```

아래와 같은 메소드도 있다.

```java
try{
    File folder = new File("parent");
    folder.mkdir();
    File file = new FIle("parent\\person.txt")
    file.createNewFile();    

    System.out.println("파일명" + file.getName());
    System.out.println("파일용량" + file.length());
    System.out.println("상위폴더" + file.getParent());
    System.out.println("정대경로" + file.getAbsolutePath());


}catch(IOException e){
    e.printStackTrace();   
}
```

