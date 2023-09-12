## 배열

- 변수 혹은 상수의 모음
- 모든 자료형에 사용 가능하며, 메모리공간에 할당될 때 요소들이 연속적으로 할당되는 것이 특징이다.
- 하나의 배열은 하나의 자료형으로 통일된다.

### 선언

- `new` : 변수에 메모리 공간을 할당할 때 사용. 참조형 자료형에 메모리공간을 할당할 때사용한다.
    - (참조형 자료형 : 기본형을 제외한 나머지 자료형)
    - 배열은 그 자체로 참조형이다.
- `int [] Array = new int[10];`
    - int형 변수를 10칸 저장할 수 있는 배열을 생성한다는 뜻.

## String

- 배열은 처음 선언할 때 전체 길이를 한정짓기 때문에 저장할 수 있는 데이터의 최대치가 정해져있다. `String`(문자열)은 이런 문제를 해결할 수 있다.

```java
String str;
str = "ybongg";

char [] cArr = new char[5];
//cArr = "ybongg"; 이렇게 사용하는 것은 불가능하다. 
```

- String은 참조형 자료형이지만, `new`를 쓰지 않고 사용할 수 있는 특이한 자료형이다.
- String 변수는 선언과 동시에 메모리에 공간이 할당되므로, 기본현 변수와 동일하게 사용하면 된다.
- 끝에는 `NUL`이 저장되어있다. (not NULL), 따라서 문자열 변수의 메모리 할당 시 글자수 + 1 byte가 할당된다.
- String은 `클래스`의 형태를 갖고 있다. String 자료형은 그 자체로 클래스이기 때문에, 여러 기능을 한번에 갖고 있다. 다음 장 (클래스) 참고

# String 활용하기

## String → 기본 자료형 형변환

### .valueOf(), charAt

변수 *String buff*로 문자열을 받았다고 가정

- int : `Integer.valueOf(*buff*)`
- double : `Double.valueOf(*buff*)`
- char : `buff.charAt(0)`

```java
import java.io.*;

class Main {
    public static void main(String[] args) {
        
    	String szVal = "3.1";
        double dVal = Double.valueOf(szVal);
        
        szVal = "41";
        int iVal = Integer.valueOf(szVal);
    }
}
```

## String 비교 - equals() 메서드

```java
import java.io.*;

class Main {
    public static void main(String[] args) {
        
    	String szVal = "Goorm";
			if(szVal.equals("Gooorm") == true) {
				System.out.println("SAME!!");
			} else {
				System.out.println("Different!!");
			}
    }
}
```

## String 길이 - length() 메서드

```java
import java.io.*;

class Main {
    public static void main(String[] args) {
        
    	String szVal = "Goorm";
    	int length = szVal.length();
    	System.out.println("Length = " + length);
    	
    	for(int j = 0 ; j < szVal.length() ; j++) {
    		System.out.println(szVal.charAt(j));
    	}
    	
    }
}
```

## split() 메서드

```java
import java.io.*;

class Main {
    public static void main(String[] args) {
        
    	String szVal = "Goorm/Java/Class";
    	String [] strArr;
    	
    	strArr = szVal.split("/");
    	for(int j = 0 ; j < strArr.length ; j++) {
    		System.out.println(strArr[j]);
    	}
    }
}
```
