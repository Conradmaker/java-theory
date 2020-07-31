# printf

printf



저번시간에 출력문에 대하여 알아볼 때 아래와 같은 출력문을 배웠습니다.

 1.출력만 해주는 `print()`

  2.출력후 개행\(줄을 바꿔주는\)`println()`

이밖에 `printf()`라는 출력문이 있는데요 다음과 같이 사용합니다.

```java
System.out.printf(format, args); //(출력형식, 값...)
```

printf는 출력하고자 하는 값들이 내가 제시한 포맷\(형식\)에 맞춰서 출력만 진행해줍니다. 즉 개행을 해주지는 않는것입니다.

포맷속성은 다음과 같습니다.

| 들어가는 값 | 뜻 |
| :---: | :---: |
| %d | 정수값 들어갈 자리 |
| %f | 실수값 들어갈 자리 |
| %c | 문자 들어갈 자리 |
| %s | 문자열 들어갈 자리\(문자도 ㅇ\) |

코드를 보면서 이해해보겠습니다.

```java
int iNum1 = 10;
int iNum2 = 20;
		
System.out.print(iNum1+"\n");           //10
System.out.println(iNum1);              //10
System.out.printf("%d\n", iNum1,iNum2); //10
```

`printf()`가 변수 2개를 넣었지만 1개만 출력된 이유는 포맷으로 확보된 공간이 정수값 1개밖에 없기 때문입니다.

또한 `print`와 출력이 비슷해서 어디에 필요한지가 감이 잘 안옵니다.

그렇다면 10 +20 =30을 `println()`과 `printf()`로 출력해보겠습니다.

```java
//println
System.out.println(iNum1 + "+" + iNum2 + "=" + (iNum1+iNum2);
//printf
System.out.printf("%d + %d \ %d \n",iNum1,iNum2,iNum1+iNum2)
```

어떤 출력문이 더 편해보이시나요?

정답은 없습니다. 

스스로 편하다고 생각하시는걸 쓰시면 됩니다.

