# Run-time Error

- 프로그래밍 과정에서 예상치 못한 실수를 하거나, 혹은 프로그램이 외부요인에 의해 의도한 방향으로 동작하지 않는 경우가 많다
- 이럴 때 오류를 발생하며 죽어버리는 경우가 발생한다.
- 이를 프로그래밍 동작 중 오류라 하여 `Run-time Error`라고 한다.
- 이러한 런타임 에러를 막기 위한 안전장치를 예외처리라고 한다.
    - 적적히 예외처리를 구현한 프로그램은 프로그램의 안정성을 높이고, 프로그램 신뢰도를 높힌다.

# try-catch 문

- try 혹은 catch 단독으로 사용할 수 없는 세트.

## 예시코드

### 예시1

```java
public class Main {

	public static void main(String[] args) {
		
		int [] Arr = new int[3];
		
		for(int j = 0 ; j < 4 ; j++) {
			Arr[j] = j;
		}
	}
}
```

이럴 경우, 에러가 발생한다 (없는 인덱스에 넣으니까)

```
Exception in thread "main" java.lang.ArrayIndexOutOfBoundsException: Index 3 out of bounds for length 3
        at Main.main(Main.java:8)
```

- Main클래스의 main 메소드에서 (Main.java 파일의 8번째 줄) ArrayIndexOutOfBoundsException이 발생했다는 얘기.
    - `ArrayIndexOutOfBoundsException` : 배열의 크기보다 더 크거나 작은 위치를 접근하고자 할 때 발생하는 Exception
- try-catch로 수정해보면
    
    ```java
    public class Main {
    
    	public static void main(String[] args) {
    		
    		int [] Arr = new int[3];
    		
    		try {
    			for(int j = 0 ; j < 4 ; j++) {
    				Arr[j] = j;
    			}
    		} catch (ArrayIndexOutOfBoundsException e) {
    			System.out.println("Exception!!!");
    		}
    	}
    }
    ```
    
    - try 문 안에 있는 코드에서 런타임 오류가 발생할 시, 프로그램이 바로 종료되는 것이 아니라, catch문으로 넘어간다.
    - 단, 이 때 catch문 조건에 있는 exception 클래스가 try문에서 발생하는 exception과 일치해야 한다.
    - 과정을 정리하자면 다음과 같다.
        1. 5: int형 배열 Arr에 3칸이 할당된다.
        2. 9: j가 3일 때 ArrayIndexOutOfBoundsException 발생
        3. catch문에 ArrayIndexOutOfBoundsException이 명시되어 있으므로 catch문 내의 소스코드가 동작한다. 

### 예시2

```java
public class Main {

	public static void main(String[] args) {
		
		String str = "test";
		
		try {
			int a = Integer.valueOf(str);
		} catch (NumberFormatException e) {
			System.out.println("Error!");
		}	
	}
}
```

# Exception

- Exception은 앞서 설명한 try-catch문에 사용되는 클래스이다.
    - 런타임 에러 발생 시 해당 오류와 관계있는 Exception을 발생하면서 프로그램이 강제 종료되는 것.

## [Exception  클래스](https://docs.oracle.com/javase/7/docs/api/java/lang/Exception.html)들의 상속 형태

![image](https://github.com/yeawonbong/study-java/assets/75327385/6c48e46c-911f-4ef1-b658-da70b6f4d12d)

- 여러가지 Exception 클래스들이 상속되어있다.
- 오류가 발생할 것으로 예상되는 지점에 try-catch문을 사용하여 적절하게 Exception을 사용할 수 있다.
- 하지만 Exception 클래스(최상위클래스) 하나만 사용하더라도 모든 종류의 오류를 다 잡아낼 수 있기 때문에, 편한 방향으로 구현할 수 있다.

# Throwable 클래스 - Java의 Error와 Exception

- *~~위는 간략설명, 다시 구조를 살펴보자.~~*

![image](https://github.com/yeawonbong/study-java/assets/75327385/b5f0eb58-c104-4ace-9db1-418883bdcc8e)

![image](https://github.com/yeawonbong/study-java/assets/75327385/d42111b9-35b0-45f1-baf6-13414d3fbe71)

- Throwable은 자바에서 모든 Error와 Exception의 부모클래스이다. 예외적인 상황이 발생했을 때 쓰인다.
- Throwable(또는 이의 하위 클래스 객체)객체의 인스턴스는 JVM에 의해서, 또는 `throw` 키워드로 던져진다.
- 이 Throwable(또는하위)클래스만이 `catch` 절의 인자가 될 수 있다.
- Throwable 클래스를 상속받는 두 클래스, Error와 Exception이 있다.

## Error 클래스

- catch 하면 안되는 심각한 문제들을 나타내는 클래스
- 비정상적인 상황

## Exception

- catch 할 수 있는 합리적인 예외들을 나타내는 클래스
- 예외는 프로그램 실행 중에 개발자의 실수로 예기치 않은 상황이 발생했을 때로, 심각한 수준의 오류는 아닌 경우
- 예시
    - ArrayIndexOutOfBoundsException
    - NullPointerException
    - FileNotFoundException
- 이러한 Exception은 개념적으로 둘로 구분할 수 있다.

### Checked Exception

- RuntimeException을 상속하지 않은 예외 클래스
- 컴파일 시 컴파일러가 에러처리를 확인하며, 명시적인 예외 처리를 강제하기 때문에 Checked Exception이라 한다.
- 반드시 try~catch로 예외를 잡거나, throw로 예외를 던져야 한다.
- 예외의 합리적 처리가가 가능하다고 가정하기 때문에 Exception이 발생해도 Rollback하지 않고 트랜잭션이 완료된다.
    - 예를 들어, 특정 이미지 파일을 찾아서 전송해 주는 함수에서 이미지를 찾지 못 했을 경우 기본 이미지를 전송한다는 처리 전략을 가질 수 있다.
- 예시
    - `존재하지 않는 파일의 이름을 입력(FileNotFoundException)`
    - `실수로 클래스의 이름을 잘못 적음(ClassNotFoundException)`

### Unchecked Exception(Runtime Exception)

- RuntimeException을 상속하는 예외 클래스, 런타임 내에 발생할 수 있는 예외
- 실행단계(런타임)에 확인되며, 명시적인 예외 처리를 강제하지 않기 때문에 Uncheked Exception이라고 한다.
- 예외 발생 시 트랜잭션 롤백해야함
- 예시
    - `배열의 범위를 벗어난(ArrayIndexOutOfBoundsException)`
    - `값이 null이 참조변수를 참조(NullPointerException)`

### 정리

![image](https://github.com/yeawonbong/study-java/assets/75327385/1d46e870-71ac-43e3-9114-d6d4f1ee91b4)

- Oracle Java 문서에 따르면 클라이언트가 예외로부터 합리적으로 회복할 수 있는 경우, 체크 예외를 사용해야 합니다. 반면 클라이언트가 예외로부터 회복할 수 없는 경우, 언체크 예외를 사용해야 합니다. 예를 들어, 파일을 열기 전에 입력 파일 이름을 검증하고 이름이 유효하지 않으면 사용자 정의 체크 예외를 발생시킬 수 있습니다. 이렇게 하면 다른 입력 파일 이름을 받아들임으로써 시스템을 회복시킬 수 있습니다. 그러나 입력 파일 이름이 널 포인터이거나 빈 문자열인 경우(코드의 에러를 나타냄), 언체크 예외를 발생시켜야 합니다Oracle Java 문서에 따르면 클라이언트가 예외로부터 합리적으로 회복할 수 있는 경우, 체크 예외를 사용해야 합니다. 반면 클라이언트가 예외로부터 회복할 수 없는 경우, 언체크 예외를 사용해야 합니다. 예를 들어, 파일을 열기 전에 입력 파일 이름을 검증하고 이름이 유효하지 않으면 사용자 정의 체크 예외를 발생시킬 수 있습니다. 이렇게 하면 다른 입력 파일 이름을 받아들임으로써 시스템을 회복시킬 수 있습니다. 그러나 입력 파일 이름이 널 포인터이거나 빈 문자열인 경우(코드의 에러를 나타냄), 언체크 예외를 발생시켜야 합니다
