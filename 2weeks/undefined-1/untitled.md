# 분기문\(continue\)

continue는

continue; 를 만나게 되면 그 뒤에 구문들은 실행하지 않고 가장 가까운 반복문 위로 올라가라는 의미

1부터 100까지 정수들의 합계를 구하되 단, 5의 배수값은 뺴고 덧셈연산하는 코드를 작성해보겠습니다.

```java
public static void main(String[] args) {
  
		int sum = 0;
		for(int i=1; i<=100; i++) {
			if(i%6 ==0){//6의 배수의 경우
				continue;
			}
			sum +=i;
		}
		System.out.print(sum);
	}
```



