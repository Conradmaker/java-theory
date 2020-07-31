# MVC 패턴

Model : 데이터 관련한 역할을 담당

View: 사용자가 보게 될 시각적인 요소 담당 \(화면같은 존재\)

Controller: 사용자가 요청한 기능 처리를 담당

### view

* 클라이언트의 시각적인 요소 담당\(화면\)
* 입력 및 출력
* 여기서 보여지는 화면을 통해 요청이라는 걸 함
* 요청을 한다는건 Controller클래스의 메소드를 호출한다는걸 의미

```java
public class PersonView{
    //사용자에게 입력받기 위한 Scanner 객체 생성
    private Scanner sc = new Scanner(System.in);
    
    //사용자의 요청을 처리할 Controller 객체 생생
    private PersonController pc = new PersonController();
    
    /**
    *   프로그램 실행과 동시에 사용자에게 보여지는 메뉴 (파란줄 주석:메소드 설명)
    */
    
    //메인메뉴를 무한반복으로 띄워줌
    while(true){
        System.out.println("=======메뉴=======");
        System.out.println("1 .신규 회원 추가");
        System.out.println("2. 회원 전체 조회");
        System.out.println("3. 회원 이름 검색");
        System.out.println("0. 프로그램 종료");
        
        System.out.print("메뉴 선택: ");
        int menu = sc.nextInt();
        
        switch(menu){
            case 1:insertPerson();break;
            case 2:    break;
            case 3:    break;
            case 4:    break;
            case 0:System.out.println("종료합니다.");return;
            default:System.out.println("잘못입력했습니다.");
        }
        
        
    }
    
    /**
    *    서브화면 1. 신규회원을 추가하는 화면
    */
    public void insertPerson(){
        System.out.println("이름: ");
        String name = sc.nextLine();
        System.out.println("나이:");
        int age = sc.nextInt();
        System.out.println("재산:");
        int wealth = sc.nextInt();
    
    
        //회원 추가 요청 (Controller메소드 호출)
        //리턴받은 값 활용
        int result = pc.insertPerson(name,age,wealth);
        
        if(result == 1){
            System.out.println("성공적으로 추가");
        }else{
            System.out.println("인원이 다차서 실패");
        }
    }
    
    /**
    *    서브화면 2. 회원 전체 조회 화면
    */
    public void selectList(){
    System.out.println("\n == 전체회원 조회 ==");
    //현재 추가된 사람수 요청 (Controller 메소드 호출)
    int count = pc.getCount();
    
    if(count == 0){//현재 추가된 회원입 없다!
    System.out.println("현재 추가된 회원이 없습니다");
    }else{//한명이라도 있다 => 본격적으로 회원조회요청
        //전체회원 조회요청 (Controller메소드 호출)
        Person [] people=pc.selectList();
        
        for(int i=0; i<count; i++){
            System.out.println(people[i].information());
        }
    }
    
    }
    
    /**
    *    서브화면 3. 회원 이름으로 검색하는 화면
    */
    
    public void searchPerson(){
        System.out.println("\n==회원 정보 검색==");
        
        System.out.print("검색할 이름: ");
        String name = sc.nextLine();
        //검색 요청!
        Person searchPerson = pc.searchPerson(name);
        
        if(searchPerson == null){ //검색된 사람이 없음
            System.out.println("검색된 회원이 없습니다.");
        }else{    //검색됨
            System.out.println(searchPerson.information());
        }
        
    }
}
```

### Controller

* View에서 사용자가 요청한 것을을 처리해주는 기능용 클래스

```java
public class PersonController{
    //우선 세명의 회원객체를 관리하기 위한 배열 셋팅
    private Person[] people = new Person[3];
    
    //현재 추가된 사람 수를 나타내는 변수
    private int count = 0;
    
    public void insertPerson(Strong name, int age, int wealth){
        if(count<people.length){ //추가기능
        
            people[count++] = new Person(name,age,wealth);
            //성공적 추가
            return 1;
        }else{
            //인권 다참
            return 0;
        }
    }
    
    public Person searchPerson(String name){
        Person searchPerson = null;//검색된 회원객체를 받아줄때 추가
        
        for(int i=0;i<count;i++){
            if(people[i].getName().equals(name)){
                searchPerson = people[i];
            }
        }
    return searchPerson; // 검색된 회원객체 또는 null
    }
    
    public double selectAvgWealth(){
    
    int sum =0;
    for(int i=0;i<count;i++){
        sum+=people[i].getWealth();
    }
    return sum/count;
}
```

