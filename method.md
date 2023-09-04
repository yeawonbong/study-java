## 메소드란?

- 프로그래밍 과정에서 코드의 간결성을 높여주기 위한 기법으로 사용된다.
- C의 함수와 같은 역할

![image](https://github.com/yeawonbong/study-java/assets/75327385/edec25e1-0e15-43e2-823d-c87361aaf32f)

- 변수 혹은 상수를 입력하면 메소드 내부에서 연산을 거친 뒤 결괏값을 출력한다.
- 즉, input 과 output이 존재한다. (C 함수에서의 매개변수, 리턴과 동일)
    - 입력 : `매개변수` 혹은 `파라미터(Parameter)`라고 부른다.
        - 입력의 수는 전혀 없을 수도, 무한히 많을 수도 있으며, void를 제외한 모든 자료형을 파라미터로 사용할 수 있다.
    - 출력 : `return value (리턴값)`이라고 부른다.

## 메소드의 기본 구조 (예시)

```java
public static	int add(int a, int b) {
	
		int result = a+b;
	
		return result;
	}
```

1. 메소드 리턴값의 자료형 - int
2. 메소드 이름 - add
3. 매개변수 - int a, int b
4. 메소드 내용 - int result = a+b
5. return - result
- 위의 예제처럼 메소드를 만들고 메소드 내용을 코딩하는 것을 **"메소드 정의"**라고 한다.

## void

- 예외로 판단되는 자료형 void

```java
import java.io.*;
class Main {
    public static void main(String[] args) {        
        System.out.println("Hello goorm!");
    }
}
```

- void는 특수한 자료형으로 어떤 값도 저장하지 않는 빈 공간을 뜻한다.

## main 메소드

- 메소드는 두가지로 나누어진다
    - main 메소드
    - 사용자 정의 메소드
- main 메소드는 모든 프로그램에서 오직 하나만 존재하는 메소드이다.
- 프로그램은 main 메소드로부터 시작하여 main메소드의 끝과 함께 종료된다.

## 오버로딩 (Overloading)

- 메소드의 이름은 동일하게 정의하고, 매개변수 혹은 리턴값만 변경하여 정의하는 기법

```java
import java.io.*;
class Main {
		static int minus(int a, int b) {
			return a - b;
		}
	
		static double minus(double a, double b) {
			return a - b;
		}
	
		public static void main(String[] args) throws Exception {				
			
			int result1 = minus(2, 5);
			System.out.println(result1);
			
			double result2 = minus(5.1, 3.9); 			
			System.out.println(result2);
		}
}
```

- 같은 이름의 메소드가 두 개 있지만, **메소드 오버로딩**을 통해 다른 입력값 혹은 출력값을 사용할 수 있다.
- 같은 동작을 하는 메소드지만, 매개변수의 자료형을 다르게 하여 사용성을 높일 수 있다.

## 메소드에서의 파라미터 (Call by Value)

- 서로 다른 메소드에서 선언된 변수들이 동일한 변수명을 가지더라도 서로 영향을 끼치지 않는데, 이런 경우를  'call by value'라고 한다.
- 메소드마다 서로 다른 공간에 할당된 데이터.
- 메소드의 파라미터는 임시 데이터공간에 값이 복사되어 사용된다.
- ↔ Call by Reference

# 정리

- 메소드란 무엇인 지
- 오버로딩 기법
- Call by Value
