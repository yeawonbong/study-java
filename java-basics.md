# 연산자, 조건문/선택문,  반복문 
# 연산자

- 비교연산자 (<, >)의 결과는 boolean형(true, false)로 반환된다.
- 연산자 우선순위
    
    (한 줄의 코드에 여러 개의 연산자가 존재할 때, 실행되는 순서)
    
    ![image](https://github.com/yeawonbong/study-java/assets/75327385/13995adc-313a-421b-bf9c-d824ee8e389c)

    

# 오버플로와 언더플로

- 오버플로 (Overflow)
    - 자료형의 최대치보다 큰 숫자를 저장하려고 할 때 생기는 에러
    - 음수값으로 넘어간다.
- 언더플로 (Underflow)
    - 자료형의 최소치보다 작은 숫자를 저장하려고 할 때 생기는 에러
    - 양수값으로 넘어간다.

# 조건문은 패스

# 선택문 (Switch문)

- switch문은 if문처럼 조건에 의해 소스코드를 실행하거나 혹은 실행되지 않도록 만들어주는 문법이다.
- switch 문은 if문과 달리 int형 조건을 기본으로 가진다. (char형도 int형으로 표현할 수 있기에 가능함)
- switch문은 `case`문과 `default`문으로 구성되어 있다.
1. case 문
    - switch문 내에서 여러 번 사용할 수 있다.
    - case문 뒤에는 switch의 조건을 만족하는 숫자를 적고 콜론(:)을 적어준다.
    - 만약 case문의 숫자가 switch문의 조건을 만족하는 숫자인 경우, 해당하는 case문부터 `break;`명령을 만날 때까지 프로그램이 실행된다.
    - break문은 switch문 혹은 반복문을 탈출하는 문법이다.
2. default 문  *~~else같은 거~~*
    - case문에 만족하는 조건이 없을 시 동작하는 부분으로, 필요하지 않다면 생략할 수 있다.
    - 하지만 사용하게 된다면, 하나의 switch문 안에 default문은 단 하나만 사용할 수 있다.

```java
import java.io.*;
class Main {
	public static void main(String[] args) throws Exception {
		int a = 1;
		
		switch(a) {
			case 1:
				System.out.println("a == 1");
				break;
			case 2:
				System.out.println("a == 2");
			default:
				System.out.println("a == ?");
		}
	}
}
```

```
> a == 1
```

# 반복문

## for문

```java
for(/* 시작조건 */ ; /* 실행조건 */ ; /* 증감식 */) 
{
	// 반복 내용
}
```

- 시작조건은 가장 처음, 1회 실행된다.

## do while 문

- 우선 1회 동작한 뒤, while 조건을 확인하여 반복.

```java
do{
 //반복내용 
	a++
}while(a < 5);
```

## break, continue 문

- break - 반복문 종료
- continue
    - 반복문에서만 사용되는 문법으로, 반복문에서 continue문을 만나면 반복문의 조건이 있는 곳(시작부분)으로 돌아가게 된다.
    
    ```java
    import java.io.*;
    class Main {
    		public static void main(String[] args) throws Exception {
    			int a = 1;
    			while(true) {
    				
    				if(a > 10) {
    					break;
    				} else if(a % 2 == 1) {
    					a++;
    					continue;
    				}
    				
    				System.out.println(a++);
    				
    			} 
    		}
    }
    ```
