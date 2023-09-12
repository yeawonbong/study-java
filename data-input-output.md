# 표준입출력

## [Scanner](https://docs.oracle.com/javase/7/docs/api/java/util/Scanner.html) 클래스

입력 관련 클래스

```java
import java.util.Scanner;	// Scanner 사용시 명시 필수!

class Main {
	public static void main(String[] args) {
		int iVal;
		double dVal;		
		
		Scanner scanner = new Scanner(System.in);
		
		System.out.print("정수를 입력해주세요 : ");
		iVal = scanner.nextInt();				
		System.out.println("입력 정수 : " + iVal);
		
		System.out.print("실수를 입력해주세요 : ");
		dVal = scanner.nextDouble();				
		System.out.println("입력 실수 : " + dVal);
	}
}
```

1. `import java.util.Scanner;` 명시
2. scanner 객체에 메모리 할당 (new 생성)
3. `nextInt()` 메서드 혹은 `nextDouble`메소드 등을 이용하여 원하는 변수에 저장. 

## [BufferedReader](https://docs.oracle.com/javase/7/docs/api/java/io/BufferedReader.html) 클래스

```java
import java.io.*;

class Main {
    public static void main(String[] args) throws Exception {
        
    	String sVal;
    	
		// BufferedReader 초기화
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        
        System.out.print("문자열을 입력해주세요 : ");
        sVal = br.readLine();
        System.out.println("입력 문자열 : " + sVal);
        br.close();
    }
}
```

- import가 필요없는 대신, main 메소드 뒤에 `throws Exception`을 덧붙여야 함.
1. BufferedReader 객체 생성 (new) 과 초기화 
    - `InputStreamReader` 클래스 사용
        - 데이터 입력 받는 방식을 정해주는 클래스
2. `readLine()`메서드로 입력을 받는다.
    - 입력되는 줄 전체를 string형태로 반환해주는 메소드
    - string형태로 데이터를 입력받기 때문에, 숫자를 받고 싶다면 string을 숫자로 변환해주어야 한다.
3. 사용 후엔 `br.close()`메서드로 BufferedReader 객체를 종료시켜야 한다. 

# 파일 입출력

## 파일로 출력하기

```java
import java.io.*;

class Main {
    public static void main(String[] args) throws Exception {
        
    	BufferedWriter bw = new BufferedWriter(new FileWriter(new File("data/test.txt")));
    	
    	String str = "Hello Goorm Java Class!";
    	bw.write(str);
    	
    	bw.close();
    }
}
```

### [BufferedWriter](https://docs.oracle.com/javase/7/docs/api/java/io/BufferedWriter.html)

- 데이터를 출력할 때 사용하는 클래스 ( ↔ BufferedReader)

### FileWriter

- 파일에 데이터를 작성하는 클래스
- ~~*파라미터는 fd값이 들어오는 것 같음*~~
- 파일 작성 후 `bw.close()`처럼 닫아줘야 한다.

### File

- 파일의 주소를 파라미터로 받아 해당 파일의 정보를 갖고 있는 클래스.
- ~~*C의 open같이 파일 열어서 fd값 가져오는 것 같음*~~

## 파일에서 입력받기

```java
import java.io.*;

class Main {
	public static void main(String[] args) throws Exception {
		BufferedReader br = new BufferedReader(new FileReader(new File("data/test.txt")));
		
		String str;
		str = br.readLine();		
		
		br.close();
	}		
}
```

### FileReader

- 앞의 데이터 표준입력과 유사하나, 인자가 달라짐.
    - `InputStreamReader` → `FileReader`
    - `System.in` → `File`
