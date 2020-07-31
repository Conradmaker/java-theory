# 상속 \(Inheritance\)

### 상속의 장점

* 보다 적은 양의 코드로 새로운 클래스 작성 가능
* 코드를 공통적으로 관리하기 때문에 코드의 추가나 변경에 용이
* -&gt;코드의 중복을 제거하여 프로그램의 생산성이나 유지보수에 크게 기여

### 

### 상속의 특징

* 클래스간 상속은 다중상속이 불가능 \(단일 상속만 가능\)
* 부모의 private 접근제한자로 기술되어 있는 경우 아무리 상속구조라고 해도 직접 접근 불가
* 단, protected로 하게 되면 자식에서 직접 접근 가능
* 명시되어 있지는 않지만 모든 클래스는 Object 클래스의 후손이다.
* -&gt;Object 클래스에서 제공하는 메소드는 얼마든지 쓸 수 있다
* --&gt;마음에 안들면 사용자가 재정의 \(오버라이딩\) 가능하다.



* [https://app.diagrams.net/](https://app.diagrams.net/)

![&#xC704;&#xC640; &#xAC19;&#xC740; &#xAD6C;&#xC870;&#xB97C; &#xAC00;&#xC9C4; &#xD074;&#xB798;&#xC2A4;&#xB4E4;&#xC744; &#xB9CC;&#xB4E4;&#xC5B4; &#xBCFC;&#xAE4C;&#xC694;?](../.gitbook/assets/image%20%2820%29.png)

먼저 Vehicle클래스를 만들어 보아요

```java
public class Vehicle {
	//필드
	private String name;
	private double mileage;
	private String kind;
	
	//생성자
	public Vehicle() {}
	
	public Vehicle(String name,double mileage,String kind) {
		this.name = name;
		this.mileage = mileage;
		this.kind = kind;
	}
	
	//setter
	public void setName(String name) {
		this.name=name;
	}
	public void setMileage(double mileage) {
		this.mileage=mileage;
	}
	public void setKind(String kind) {
		this.kind=kind;
	}
	
	//getter
	public String getName() {
		return this.name;
	}
	public double getMileage() {
		return this.mileage;
	}
	public String getKind() {
		return this.kind;
	}
	
	public String  information() {
		return this.name + this.mileage + this.kind;
	}
}
```

그다음으로 car클래스를 만들어 볼까요?

```java
public class Car extends Vehicle {  //상속받겠다.
	private int tire;
	
	public Car() {
		
	}
	
	public Car(String name,double mileage, String kind, int tire) {
		super(name, mileage, kind);   //vehicle메소드
		this.tire = tire;
	}
	
	public int getTire() {
		return tire;
	}
	public void setTire(int tire) {
		this.tire = tire;
	}
	
	@Override//information을 이용해 내용을 바꾸겠다.
	public String information() {
		return super.information()+",바귀수:"+tire+"개";
	}
}
```

이제 출력해보겠습니다.

```java
import com.kh.c02.model.vo.*;
public class Run {

	public static void main(String[] args) {
		
		Car c = new Car("벤틀리",12.5,"세단",4);
		
		//자식클래스에 있는 메소드가 호출된다.
		System.out.println(c.information());
	}

}
//결과
벤틀리 12.5 세단 , 바귀수:4개
```

잘 되시나요?

위에서 information\(\)을 호출하면 자식클래스 즉, 오버라이드된 메소드가 호출이 되었는데요?

만약 자식클래스에 메소드가 없다면 부모클래스 즉, Vehicle클래스의 메소드가 호출된답니다.

