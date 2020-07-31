# 2차원 배열

## 이차원 배열

이차원 배열은 일차원 배열 여러개를 하나로 묶은것을 말합니다.



먼저 행을 3번반복하고, 박 행별로 열 5번씩 반복하는 이차원배열을 만들어보겠습니다.

즉 행=&gt; 바깥쪽 for문   열=&gt;안쪽 for문 을 이용해서 구현해주면 되겠죠?

```java
public void method1(){
    for(int i=0; i<3; i++){
        for(int j=0;j<5;j++){
            //별찍기
            System.out.print("*");
        }
        //행바꾸기
        System.out.println();
    }
}
```

![](../../.gitbook/assets/image%20%285%29.png)

### 2차원 배열 할당\(크기지정\)

```java
 배열명 = new 자료형[행크기][열크기];
```

이차원 배열은 배열 즉 행이 모여있는 형태이기 때문에 열크기를 지정해주지 않아도 괜찮습니다.

그럼 위에서 만든 3\*5배열을 할당해줘볼까요?

```java
arr=new int[3][5];
```

이차원 배열또한 선언과 동시에 할당을 해줄 수 있습니다.

```java
int [][] arr = new int[3][5]
```

일차원 배열과 사용은 동일하죠?

그렇다면 주소값들을 살펴볼까요?

```java
int [][] arr = new int[3][5];
    System.out.println(arr);
    System.out.println(arr[0]);
    System.out.println(arr[1]);
    System.out.println(arr[2]);
```

![&#xC8FC;&#xC18C;&#xAC12;&#xC774; &#xBAA8;&#xB450; &#xB2E4;&#xB974;&#xAC8C; &#xCD9C;&#xB825;&#xB418;&#xC5C8;&#xC2B5;&#xB2C8;&#xB2E4;.](../../.gitbook/assets/image%20%288%29.png)

arr의 주소값에는 2차원배열을 의미하는 \[\[가 출력되었죠?

또한 각 행들의 주소가 모두 다르게 출력, 즉 각각 다른 배열들로 합춰진 이차원배열이라는 것을 알 수 있습니다.

실제 정수값을 출력하기 위해서는 아래와 같이 작성해주어야 합니다.

```java
System.out.println(arr[0][0]);
```

0번행의 0번열의 데이터를 조회한다는 의미가 있겠죠?



그렇다면 0번째 행의 열의 길이를 확인하기 위해서는 어떻게 해야 할까요?

```java
System.out.println("행의 길이: "+arr.length);
System.out.println("0행의 열의 길이: "+arr[0].length);

//행의 길이: 3
//0행의 열의 길이: 5
```



### 배열출력

```java
 //행
 for (int i = 0; i < arr.length; i++) {
       //열
       for (int j = 0; j < arr[i].length; j++) {
           System.out.print(arr[i][j]);
       }
       //개행
       System.out.println();
}
//결과
00000
00000
00000 
```

### 

### 2차원배열 값대입과 선언

이제 2차원배열을 직접 값을 대입해 만들어보도록 해보겠습니다.

아래의 값을 가지고 있는 이차원 배열을 만들어볼까요?

```java
1  2  3  4   5
6  7  8  9  10
11 12 13 14 15
```

```java
 int value = 1;
    for (int i = 0; i < arr.length; i++) {
        for (int j = 0; j < arr[i].length; j++) {
            arr[i][j] = value++;
            System.out.print(arr[i][j]+" ");
        }
        System.out.println();
    }
```

값이 1씩 증가해야 하기 때문에 value변수를 통해 1씩 값을 증가시켰습니다.

이번에는 배열의 선언과 동시에 값을 대입하는 방법을 알아보겠습니다.

```java
int[][] arr={{1, 2, 3, 4,  5},
             {6, 7, 8, 9, 10},
             {11,12,13,14,15}}
```

어떤가요? 정말 간단하죠? 한번 출력해볼까요?

```java
 for (int i = 0; i < arr2.length; i++) {
        for (int j = 0; j < arr2[i].length; j++) {
            System.out.print(arr2[i][j]+" ");
        }
        
//결과
1 2 3 4 5
6 7 8 9 10
11 12 13 14 15
```



### 가변배열

가변배열은 행은 정해졌으나 각 행별 열의 갯수가 정해지지 않은 상태의 배열을 말합니다.

가변배열 할당방법은 다음과 같습니다.

```java
int[][]arr = new int[3][]; 
```

열의 크기를 지정하는 부분을 그냥 공백으로 놔두면 됩니다. 간단하죠?

단 각 행별로 길이를 지정해줘야겠죠?

```java
int[][]arr = new int[3][]; //가변배열 할당

    arr[0] = new int[2];    //0행은 2열
    arr[1] = new int[1];    //1행은 1열
    arr[2] = new int[3];    //2행은 3열
```

또한 이런식으로 배열의 선언과 동시에 열의 길이를 다르게 할 수도 있습니다.

```java
int[][] arr = {{1,2},{2},{4,5,6}};
```



이제 조금더 유용한 이중배열을 만들어보도록 하겠습니다.

| 국어점수 |  |  |  | 총합 |
| :--- | :--- | :--- | :--- | :--- |
| 영어점수 |  |  |  | 총합 |

일단 0행의 경우에는 국어점수, 1행의 경우에는 영어점수를 입력할 수 있도록 문구를 출력할 수 있게 만들어줍니다.

```java
 //실수값의 2*4 배열 만들기
    double[][] arr = new double[2][4];

    //행을 지정하는 for문 (0번인덱스:국어점수, 1번인덱스:영어점수)
        for (int i = 0; i < arr.length; i++) {
            
            //열을 지정하는 for문(마지막열은 총합이기 때문에 접근X)
            for (int j = 0; j < arr[i].length-1; j++) {
                if(i==0){
                    //0번인덱스(국어) 일때는 국어점수: 출력
                    System.out.print("국어점수: ");
                }else{
                    //그외에는 영어점수: 출력
                    System.out.print("영어점수: ");
                }
            }
        }
```

그 위에는 사용자가 입력한 값을 넣어줘야 겠죠?

```java
//실수값의 2*4 배열 만들기
    double[][] arr = new double[2][4];

    //행을 지정하는 for문 (0번인덱스:국어점수, 1번인덱스:영어점수)
        for (int i = 0; i < arr.length; i++) {
            
            //열을 지정하는 for문(마지막열은 총합이기 때문에 접근X)
            for (int j = 0; j < arr[i].length-1; j++) {
                
                if(i==0){
                    //0번인덱스(국어) 일때는 국어점수: 출력
                    System.out.print("국어점수: ");
                }else{
                    //그외에는 영어점수: 출력
                    System.out.print("영어점수: ");
                }
                
    //**문자열 출력 후(조건문 종료후)에 값을 입력하고 받아오기**
                arr[i][j] = sc.nextDouble();
            }
        }
```

추가적으로 반복문 진행과 동시에 총합을 누적시켜줄 수 있습니다.

```java
//실수값의 2*4 배열 만들기
    double[][] arr = new double[2][4];

    //행을 지정하는 for문 (0번인덱스:국어점수, 1번인덱스:영어점수)
        for (int i = 0; i < arr.length; i++) {
            
            //열을 지정하는 for문(마지막열은 총합이기 때문에 접근X)
            for (int j = 0; j < arr[i].length-1; j++) {
                if(i==0){
                    //0번인덱스(국어) 일때는 국어점수: 출력
                    System.out.print("국어점수: ");
                }else{
                    //그외에는 영어점수: 출력
                    System.out.print("영어점수: ");
                }
                //문자열 출력 후에 값을 입력하고 받아오기
                arr[i][j] = sc.nextDouble();
  //**총합부분(각행의 3번 인덱스)에 입력값을 누적시켜주기**
                arr[i][3] += arr[i][j];
            }
        }
```

이제 출력해볼까요?

```java
 for (int i = 0; i < arr.length; i++) {
       for (int j = 0; j < arr[i].length; j++) {
            System.out.print(arr[i][j]+" ");
       }
    //개행
     System.out.println();
}
```

```java
국어점수: 80
국어점수: 90
국어점수: 100
영어점수: 10
영어점수: 10
영어점수: 20
//결과
80.0 90.0 100.0 270.0
10.0 10.0 20.0  40.0
```



이번에는 3x3 배열에 랜덤값을 담아볼까요?

```java
//정수값의 3*3 배열 만들기
    int[][] arr = new int[3][3];

    for (int i = 0; i < arr.length; i++) {
        for (int j = 0; j < arr[i].length; j++) {
            arr[i][j] = (int)(Math.random()*10+1);

            System.out.print(arr[i][j]+" ");
        }
        System.out.println();
    }
```

다음으로는 중복값이 없이 랜덤값을 담아보겠습니다.

전에 1차원 배열도 중복값을 없앨때 반복문이 2번 사용되었는데,

2차원배열은 제대로 중복제거를 하려면 4번 사용되어야 합니다...

하지만 3x3배열은 9칸이니 1차원 9크기의 배열을 만든 후 옮겨닮을 수 있습니다.

먼저 중복값 없는 1차원 배열을 만들어주세요

```java
//정수값의 3*3 배열 만들기
    int[] arr = new int[9];
    
    
    for (int i = 0; i < arr.length; i++) {
            arr[i]= (int)(Math.random()*10+1);

            for (int j = 0; j < i; j++) {
                if(arr[i]==arr[j]){
                    i--;
                    break;
                }
            }
        }
```

그다음 2차원 배열을 만들어주세요

```java
int[][]arr2 = new int[3][3];

//이런식으로 배열을 옮겨야 겠죠?
        arr2[0][0]=arr[0]
        arr2[0][1]=arr[1]
        arr2[0][2]=arr[2]
        arr2[1][0]=arr[3]....
```

옮겨볼까요?

```java
int index = 0;
        for (int i = 0; i < arr2.length; i++) {
            for (int j = 0; j < arr2[i].length; j++) {
                arr2[i][j] = arr[index++];
            }
        }
```

생각보다 어렵지 않습니다.

지금 배운 내용을 바탕으로 5x5의 빙고게임을 만들어볼까요?

```java
//먼저 1차원 배열 만들기
    int[] arr = new int[25];
    
        for (int i = 0; i < arr.length; i++) {
            arr[i]= (int)(Math.random()*25+1);
            for (int j = 0; j < i; j++) {
                if(arr[i]==arr[j]){
                    i--;
                    break;
                }
            }
        }
       
        //2차원 배열에 대입
        int[][]bingo = new int[5][5];
    
        int index = 0;
        for (int i = 0; i < 5; i++) {
            for (int j = 0; j < 5; j++) {
                bingo[i][j] = arr[index++];
                System.out.print(bingo[i][j]+"  ");
            }
            System.out.println();
        }
        //빙고구현
        System.out.println("\n======== 빙고게임 시작 ========");
        int count=0;

        while(true){
            System.out.print("정수값 입력");
            int num = sc.nextInt();
            count++;
            for(int i=0;i<5;i++){
                for (int j = 0; j < 5; j++) {
                    //일치하면 0으로 만들어주기
                    if(bingo[i][j]==num){
                        bingo[i][j]=0;
                    }
                    System.out.printf("%4d", bingo[i][j]);
                }
              System.out.println();  
            }
        }
```



