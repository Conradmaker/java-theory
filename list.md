# List

List 의 후손 클래스

"ArrayList" , "Vector" , "LinkedList"

{% hint style="info" %}
Vector와 ArrayList 동일한 기능 제공

차이점

* Vector-동기화 제공 ㅇ =&gt; 멀티스레드 환경에만 좋다.\(단일에는 속도저하\)
* ArrayList - 동기화X =&gt; Vector보완하여 후에 나왔다.
{% endhint %}

{% hint style="danger" %}
Vector는 쓰지 않는 것을 추천합니다.
{% endhint %}

ArrayList &  LinkedList 차이점

| ArrayList | LinkedList |
| :---: | :---: |
| 내부적으로 배열을 가짐 | 데이터와 데이터를 체인처럼 연결해서 보관 |
| 특정 인덱스에 값을 추가,삭제할때 내부적으로 반복문이 돌면서 값이 땡겨진다. | 특정 인덱스에 값을 추가,삭제할때 내가 작업하고자 하는 인덱스 앞,뒤를 인지하기 때문에 연결만 해주면 된다. |

{% hint style="info" %}
새로운 데이터를 추가하거나 삭제할때는 LinkedList가 속도가 더 빠르다.

단, 검색할때는 속도가 느리다. \(ArrayList 추천\)
{% endhint %}

ArrayList

1. List의 후손으로 초기 저장 용량은 10으로 자동 설정되며 따로 지정도 가능 
2. 저장 용량을 초과한 객체들이 들어오면 자동으로 늘어나며 고정도 가능 
3. 동기화\(Synchronized\)를 제공하지 않음

{% tabs %}
{% tab title="VO" %}
{% code title="Music.java" %}
```java
package com.model.vo;

public class Music {
	//필드부
	private String title;
	private String artist;
	
	//생성자
	public Music() {};
	
	public Music(String title, String artist) {
		super();
		this.title = title;
		this.artist = artist;
	}

	//setter / getter
	public String getTitle() {
		return title;
	}

	public void setTitle(String title) {
		this.title = title;
	}

	public String getArtist() {
		return artist;
	}

	public void setArtist(String artist) {
		this.artist = artist;
	}
	
	
	//toString
	@Override
	public String toString() {
		return "Music [title=" + title + ", artist=" + artist + "]";
	}
	
}

```
{% endcode %}
{% endtab %}

{% tab title="기존방법" %}
{% code title="Run.java" %}
```java
package com.run;
import com.model.vo.Music;

public class Run {

	public static void main(String[] args) {

		Music [] arr = new Music[3];
		
		arr[0] = new Music();
		arr[1] = new Music();
		arr[2] = new Music();
		
		Music[]newArr = new Music[10];
		
		for(int i=0;i<arr.length;i++) {
			newArr[i] = arr[i];
		}
		newArr[3] = new Music();

	}

}
```
{% endcode %}
{% endtab %}

{% tab title="ArrayList" %}
```java
package com.run;

import java.util.ArrayList;
import java.util.List;

import com.model.vo.Music;


public class Run {

	public static void main(String[] args) {


		Music [] arr = new Music[3];
		//ArrayList 컬렉션 사용해보기
		ArrayList<Music> list = new ArrayList<Musics>(3); //크기지정 할 수도 있다.
		
		System.out.println(list); //현재 아무것도 안담긴 상태
		
		//E --> Element : 리스트에 담길 요소들 (객체라고 생각) 여기서는 <Music>을 의미
		
		//1.add(E e) : 리스트 끝에 전달된 객체를 추가해주는 메소드
		list.add(new Music("눈의꽃","박효신"));
		list.add(new Music("미안해","양다일"));
		list.add(new Music("잊혀지다","정키"));
		list.add("끝");  //3으로 지정했지만 더 넣어도 오류가 없다. 장정1. 크기제약 X
		
		//2.add(int index, E e): 해당 인덱스에 내가 전달한 객체를 추가시켜주는 메소드
		list.add(1,new Music("진심이 담긴 노래","케이시"));
		
		//3.set(int index, E e): 해당 인덱스의 값을 새로이 전달한 객체로 변경시켜주는 메소드
		list.set(0, new Music("술이달다","에픽하이"));
		
		//4.size():리스트 안에 몇개의 객체가 담겨있는지 갯수 반환시켜주는 메소드
		System.out.println(list.size());
		
		//5.remove(int index): 해당 인덱스의 객체 삭제시켜주는 메소드
		list.remove(1);
		
		//6.get(int index):E  =>해당 인덱스의 객체 반환시켜주는 메소드
		Object m = list.get(0); //list[0] (Object 반환) <Music>이기 때문에 형변환 필요 X
		String str = (String)list.get(3);
		
		
		//7.subList(int index1, int index2): List => index1부터 index2까지의 해당 객체들 추출해 새로운 List반환
		List sub = list.subList(0, 2); //0,1번 인덱스 추출
		
		//8.addALl(Collection c): 컬렉션에 담겨있는 모든 객체들을 통째로 추가해주는 메소드
		list.addAll(sub);
		
		//9.isEmpty():컬렉션이 비어있는지 묻는 메소드(true,false)
		System.out.println(list.isEmpty()); //false
		
		//10.clear(): 컬렉션에 담긴 객체들 싹 비워주는 메소드
		list.clear();
		System.out.println(list.isEmpty()); //true
		
		//해당 리스트에 담겨있는 모든 객체들에 순차적으로 접근해서 출력
		//0번인덱스부터 마지막 인덱스까지
		//for loop
		for(int i=0;i<list.size();i++) {
			System.out.println(list.get(i));
		}
		
		//향상된 for문
		for(Object o:list) {//변수=list.get(0);-->변수=list.get(1); --> 변수=list.get(2);
			System.out.println(o);
		}
		System.out.println(list);//순서유지되고 있음
		
	}

}
```
{% endtab %}
{% endtabs %}



&lt;&gt;제네릭스

제네릭을 사용하는 이유

* 명시된 타입의 객체만 저장하도록 제한을 두기 위해서
* 해당 그 컬렉션에 저장된 객체를 꺼내 사용할 떄도 매번 형변환해야만 하는 정차를 없앨 수 있음.

MVC패턴 적용시키기

|  | 역할 |
| :--- | :--- |
| Model | 데이터를 처리하는 역할 |
| View | 사용자가 보게되는 시각적인 요소 / 입력\(Scanner\)&출력\(print\) |
| Controler | 사용자의 요청을 처리하는 담당 |

내용이 상당히 길기때문에 코드에 직접 기술하겠습니다.

기능은 다음과 같습니다.

1. 신규곡 추가
2. 전체 곡 조회
3. 특정 곡 검색
4. 특정 곡 삭제
5. 특정 곡 수정
6. 정렬
7. 프로그램 종료

{% tabs %}
{% tab title="Music \(VO\)" %}
{% code title="Music.java" %}
```java
package com.model.vo;

public class Music implements Comparable<Music> {
	//필드부
	private String title;
	private String artist;
	
	//생성자
	public Music() {};
	
	public Music(String title, String artist) {
		super();
		this.title = title;
		this.artist = artist;
	}

	//setter / getter
	public String getTitle() {
		return title;
	}

	public void setTitle(String title) {
		this.title = title;
	}

	public String getArtist() {
		return artist;
	}

	public void setArtist(String artist) {
		this.artist = artist;
	}
	
	
	//toString
	@Override
	public String toString() {
		return "Music [title=" + title + ", artist=" + artist + "]";
	}
	
//	@Override
//	   public int compareTo(Music m) {
//	         
//	      //가수명 오름차순 정렬이 되게끔 해야됨!!
//	      //이 compareTo메소드 실행시 "반환값이 양수"일 경우 두 객체의 순서가 바뀌게됨
//	      //m1.copareTo(m2)
//		  //this(앞)   o(뒤)
//		//앞의 가수명이 뒤의 사구명보다 더 큰 값일 경우 순서를 변경해야함 
//		
//		
//	      return this.artist.compareTo(o.artists);
//	   }
	
}

```
{% endcode %}
{% endtab %}

{% tab title="MusicMenu\(View\)" %}
{% code title="MusicMenu.java" %}
```java
package com.model.vo;

import java.util.ArrayList;
import java.util.Scanner;

public class MusicMenu {
	private Scanner sc = new Scanner(System.in);
	
	private MusicController mc = new MusicController();
	
	//프로그램 실행시 사용자가 보게될 첫 화면
	
	public void mainMenu() {
		while(true) {
			System.out.println("\n=== Welcome ===");
			System.out.println("1.신규곡 추가");
			System.out.println("2.곡 전체 조회");
			System.out.println("3.특정 곡 검색");
			System.out.println("4.특정 곡 삭제");
			System.out.println("5.특정 곡 수정");
			System.out.println("6.정렬");
			System.out.println("0.프로그램 종료");
			System.out.println("메뉴선택: ");
			int menu = sc.nextInt();
			sc.nextLine();
			
			switch(menu) {
			case 1: insertMusic(); break;
			case 2: selectList(); break;
			case 3: searchMusic(); break;
			case 4: deleteMusic(); break;
			case 5: break;
			case 6:System.out.println("프로그램 종료"); return;
			case 0:System.out.println("프로그램 종료"); return;
			}
		}
	}
	
	//곡 추가
	public void insertMusic() {
		System.out.println("======신규곡 추가======");
		System.out.print("제목 입력:");
		String title = sc.nextLine();
		
		System.out.print("가수입력: ");
		String artist = sc.nextLine();
		
		//곡 추가 요청! (Controller 메소드 호출)
		//mc.insertMusic(title, artist);
		mc.insertMusic(new Music(title,artist));
	}
	
	//곡 전체조회 
	public void selectList() {
		System.out.println("======곡 전체 조회======");
		
		//곡 전체조회 요청!(Controller 메소드 호출)
		ArrayList<Music> list = mc.selectList();
		if(list.isEmpty()) {//리스트가 비어있을 경우->곡이 없다,
			System.out.println("곡없음");
		}else {//비어있지 않을 경우->
			for(int i=0; i<list.size();i++) {
				System.out.println(list.get(i));
			}
		}
	}
	
	//검색결과 입력받은 뒤 해당 검색결과 뜨의주는 화면
	public void searchMusic() {
		System.out.println("특정곡 검색");
		
		System.out.println("1. 제목으로 검색");
		System.out.println("2. 가수명으로 검색");
		System.out.println("3. 제목 + 가수명으로 검색");
		System.out.print("번호 선택: ");
		int search = sc.nextInt();
		sc.nextLine();
		
		System.out.print("검색할 곡 키워드:");
		String keyword = sc.nextLine();
		
		//검색 요청하기!
		ArrayList<Music> searchList = mc.searchMusic(keyword,search);
		
		if(searchList.isEmpty()) {
			System.out.println(keyword + "에 대한 검색 결과가 없습니다.");
			
		}else {//그게 아닐경우 => 검색결과가 하나라도 있다면
			//for(int i=0; i<searchList.size(); i++){
			for(Music m: searchList) {
				System.out.println(m);
			}
		}
		
	}
	
	// 특정 곡 삭제
	public void deleteMusic() {
		System.out.println("\n======선택 곡 삭제======");
		
		System.out.print("삭제하고자 하는 곡: ");
		String title = sc.nextLine();
		
		//삭제 요청!
		int result = mc.deleteMusic(title); //반환된 값 받기
		
		if(result>0) { //하나라도 삭제되었음
			System.out.println("성공적으로 삭제되었습니다.");
		}else { //삭제된게 없음
			System.out.println("삭제할 곡을 찾지 못했습니다.");
		}
	}
	
	//특정 곡 수정하는 화면
	public void updateMusic() {
		System.out.println("\n======특정 곡 수정=======");
		
		//어떤곡 수정하고자 하는 곡명
		System.out.print("수정하고자 하는 곡: ");
		String title = sc.nextLine();
		
		//어떤 내용으로 수정할건지 수정할 곡명
		System.out.print("수정 내용(곡명): ");
		String upTitle = sc.nextLine();
		//어떤 내용으로 수정할건지 수정할 가수명
		System.out.print("수정 내용(가수명): ");
		String upArtist = sc.nextLine();
		
		//곡 수정 요청하기!!
		int result = mc.updateMusic(title, upTitle, upArtist); //결과 가져오기
		
		if(result > 0) {//뭐라도 수정됨
			System.out.println("성공적으로 수정되었습니다.");
		}else { //수정할 곡을 찾지 못함
			System.out.println("수정할 곡을 찾지 못했습니다.");
		}
		
	}
	
	public void sortNusic() {
		System.out.print("=====곡 정렬 =====");
		System.out.print("1.가수명 오름차순: ");
		System.out.print("2.가수명 내림차순: ");
		System.out.print("3.곡명 오름차순: ");
		System.out.print("4.곡명 내림차순: ");
		System.out.print("번호선택: ");
		inst menu = sc.hasNext();
		
		//정렬 조회 요청 !
		mc.sortMusic(menu)
	}
	
}

```
{% endcode %}
{% endtab %}

{% tab title="MusicController\(Controller\)" %}
{% code title="MusicController.java" %}
```java
package com.model.vo;
import java.util.ArrayList;
import java.util.Collections;

public class MusicController {
	private ArrayList<Music> list = new ArrayList<>();

	//public void insertMusic(String title, String artist) {
	//	list.add(new Music(title,artist));
	//}
	public void insertMusic(Music m) {
		list.add(m);
	}
	
	
	public ArrayList<Music> selectList(){
		return list;
	}
	
	
	public ArrayList<Music> searchMusic(String keyword, int search) {
		ArrayList<Music> searchList = new ArrayList<>();
		
		if(search == 1) { //제목으로 검색
			for(int i=0; i<list.size();i++) {
				if(list.get(i).getTitle().contains(keyword)) {
					searchList.add(list.get(i)); //searchList에 검색결과 담기
				}
			}
		}else if(search == 2) {//가수명으로 검색
			for(int i=0; i<list.size(); i++) {
				if(list.get(i).getArtist().contains(keyword)) {
					searchList.add(list.get(i));
				}
			}
		}else if(search == 3) {//제목 + 가수명으로 검색
			for(int i=0; i<list.size(); i++) {
				//방법 1 (추천)
				if(list.get(i).getTitle().contains(keyword)||list.get(i).getArtist().contains(keyword)) {
					searchList.add(list.get(i));
				}
				//방법 2
				//if(list.get(i).getTitle().concat(list.get(i).getArtist()).contains(keyword)) {
				//	searchList.add(list.get(i));
				//}
			}
		}
		
		
		//반복문이 다 끝난 시점에 있어서 searchList에는 검색된 곡이 담겨있을 것!
		//단, 검색된 곡이 하나도 없었을 경우 searchList는 비어있을 것!
		return searchList;
	}
	
	public int deleteMusic(String title) {
		
		int result = 0; //처리 결과를 보관할 변수
		
		for(int i=0; i<list.size();i++) {
			if(list.get(i).getTitle().equals(title)) {
				list.remove(i--);//지워지면 1칸씩 당겨지기 때문에 같이 당겨져야 한다.
				//System.out.println("성공적으로 삭제되었음");
				result++;
				 
			}
		}
		//반복문이 다 끝난 시점에 result값 0 => 삭제한 곡이 X / 0이 아니면 뭔가 삭제됨
		return result; //반환형 return=int
	}
	
	public int updateMusic(String title, String upTitle, String upArtist ) {
		int result = 0;
		for(int i=0; i<list.size(); i++) {
			
			//방법 1. setter 메소드로 변경
			
//			if(list.get(i).getTitle().equals(title)) {
//				
//				//list.get(i) === 수정할 곡
//				list.get(i).setTitle(upTitle);
//				list.get(i).setArtist(upArtist);
//			}
			//방법2. list에서 제공하는 set메소드 이용
			if(list.get(i).getTitle().equals(title)) {
				list.set(i, new Music(upTitle, upArtist));
				result++;
			}
		}
		return result;
	}
	
//	public void sortMusic(int menu) {
//		
//		//복사본 리스트
//	    ArrayList<Music> sortList = new ArrayList<>(); //빈 리스트
//	    sortList.addAll(list); // list에 기존에 담겨있던 Music객체를 통째로 추가하기
//		
//		switch(menu) {
//			case 1:Collections.sort(sortList); break; //가수명 오름차순
//			case 2:Collections.sort(sortList); break; //가수명 내림차순
//			case 3: break; //곡명 오름차순
//			case 4: break; //곡명 내림차순
//		
//		}
//	}
}

```
{% endcode %}
{% endtab %}
{% endtabs %}



