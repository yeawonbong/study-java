# 클래스와 객체

- **클래스**는 사용자가 직접 정의하여 사용할 수 있는 자료형이다.
- 자료형과 비슷 (형식과 사용방법을 명시한 실체 없는 틀이라는 점에서)
- [자료형 - 변수]가 항상 짝을 이루듯이, [클래스 - 객체]가 짝을 이룬다.
- 즉, **객체**는 클래스라는 자료형으로 만들어진 변수라고 할 수 있다.
- 클래스는 객체가 선언되었을 대 실체를 가지게 되며, 객체를 통해 클래스에 포함된 다양한 데이터(멤버)를 다룰 수 있다.
- 객체는 선언만으로는 사용할 수 없고, 생성(`new`)을 해줘야 한다. (참조형 자료형이기 때문에 메모리할당, 즉 생성 과정이 필요)
    - 단, String 클래스는 예외적으로 new를 통해 메모리에 할당하는 직업 없이 바로 사용이 가능하다.

## 예시

- 개념
    
    ```java
    1. 붕어빵틀 - 붕어빵 / 클래스 - 객체 
    		: 클래스 없이 객체를 만들 수 없고, 클래스는 객체를 만들지 않으면 쓸모없는 도구가 된다.
    2. 붕어빵 틀에는 재료와 사용 메뉴얼이 필요하며, 슈붕 팥붕 등 다양한 붕어빵을 만들 수 있다
    	/ 클래스는 멤버 변수와 멤버 메소드로 구성될 수 있으며, 객체는 동일한 틀을 가지지만 틀 안에 포함된 내용이 다를 수 있다.
    ```
    
- 예제 - String 클래스
    
    ```java
    String str1 = "슈붕";
    String str2 = "팥붕";
    ```
    
    - String은 자바에서 기본적으로 제공하는 클래스이다.
    - `String`은 클래스이고, `str1` `str2`는 객체이다.

# 멤버 (Member)

- 앞서 "클래스는 멤버 변수와 멤버 메소드로 구성될 수 있다"고 했다.
- 멤버란, 클래스를 구성하는 요소를 뜻하며, **메소드**와 **변수**로 이루어져 있다.
- 클래스는 멤버를 통해 내부의 데이터를 저장하거나 연산할 수 있는데, 이 때 클래스 내부의 변수를 "멤버 변수"라고 칭한다.

## 구조 예시

```java
class ClassExample {	
	
	double mDouble;
	
	void CE_Print_mDouble() {
		System.out.println(mDouble);
	}
	
	void CE_Set_mDouble(double dInput) {
		mDouble = dInput;
	}
}
```

- ClassExample이라는 이름의 클래스
- 그 안에
    1. mDouble이라는 double형 멤버변수
    2. CE_Print_mDouble이라는 void형 멤버메소드
    3. CE_Set_mDouble이라는 void형 멤버메소드
    
    로 이루어져 있다.
    
- 멤버변수 혹은 메소드는 갯수 제한 없이 필요한 만큼 선언하여 사용할 수 있다.
- 멤버가 없이도 클래스를 만들 수 있다.
- 이렇게 멤버들로 구성된 클래스는 하나의 자료형으로 사용할 수 있다.
- 클래스 내부의 멤버들은 객체를 통해 접근하여 제어할 수 있다.
    
    ```java
    ce.double = 10;
    ```
    
    - 객체 뒤에 `.` 을 붙이면 객체 내부의 멤버를 사용할 수 있다.

## 예제 - Main 클래스에서 사용하기

```java
import java.io.*;
class Main {
	public static void main(String[] args) {
		ClassExample ce; // ce라는 객체 선언
		ce = new ClassExample(); // new로 할당해줘야 함. 여기서 클래스 이름() 부분 - 생성자!
		
		ce.mDouble = 10;
		ce.CE_Print_mDouble();
		
		ce.CE_Set_mDouble(30);
		ce.CE_Print_mDouble();
	}
}

class ClassExample {
	
	double mDouble;
	
	void CE_Print_mDouble() {
		System.out.println(mDouble);
	}
	
	void CE_Set_mDouble(double dInput) {
		mDouble = dInput;
	}
}
```

- [객체 `.` 멤버] 의 형태로 각 멤버 변수 및 메소드를 사용할 수 있다.

# 생성자 (Construtor)

- 생성자는 클래스에서 특별한 메소드이다.
- 일반적인 메소드는 사용자가 호출할 때에 한해 동작하지만, 
생성자는 사용자가 **객체를 생성**할 때 자동으로 호출되는 메소드이다.
    
   ![image](https://github.com/yeawonbong/study-java/assets/75327385/5b442cb8-cfd9-44fd-b890-cb89c47a5286)

    
- 생성자는 return형을 사용하지 않으며 클래스와 동일한 이름을 가져야 한다.
- 예시
    
    ```java
    import java.io.*;
    class Main {
    	public static void main(String[] args) {
    		
    		ClassExample ce; //객체 선언, 참조형 자료형이기 때문에 메모리할당(생성)이 필요하다.
    		
    		System.out.println("ce object Called");
    		
    		ce = new ClassExample(); //여기 부분이 생성자.
    		
    		System.out.println("ce Object Created");
    		
    	}
    }
    
    class ClassExample {
    	
    	ClassExample() {
    		System.out.println("Constructor Called!!!");
    	}
    }
    ```
    
    - 위에서처럼, 매개변수가 존재하지 않는 생성자를 "기본생성자"라고 한다.
    - 생성자는 보통 멤버 변수들의 초기화 및 객체의 복사와 같은 역할로 사용된다.
    - *~~객체 선언이 C 관점으로 보면 구조체 포인터 선언과 비슷, `new` 로 메모리 할당 (C에서 malloc) 후에 사용.~~*

# 접근제한자

- 접근 제한자로 캡슐화를 잘 표현할 수 있다.
- 접근제한자는 멤버 변수 및 메소드를 선언할 때 사용하며, 접근제한자를 통해 멤버 변수 및 메소드를 공개하는데 있어 제약을 걸 수 있다.

![image](https://github.com/yeawonbong/study-java/assets/75327385/9d02194d-d5cb-468c-8097-a71b153665c0)


![image](https://github.com/yeawonbong/study-java/assets/75327385/71aafd82-11e7-4d9b-8e8f-62d2c6da84ab)


## public

- 접근 제한 없음

## protected

- 동일한 패키지 내에서만 접근 가능
- 상속받은 클래스일 경우 다른 패키지더라도 접근 가능

## default

- 접근제한자 명시하지 않으면 자동으로 default로 설정된다.
- 동일한 패키지 내에서만 접근 가능

## private

- private 접근제한자는 객체 자기자신 안에서만 사용할 수 있도록 제한하는 구문으로, 객체 밖에서 접근을 시도하는 경우 오류가 발생한다.
- private형의 접근제한자를 가진 멤버에 접근하고 싶다면, public으로 선언된 멤버 (메소드멤버)를 활용해야 한다.
- 예시
    
    ```java
    import java.io.*;
    class Main {
    	public static void main(String[] args) {
    		ClassExample ce;
    		ce = new ClassExample();
    		
    		ce.CE_Set_mDouble(30);
    		ce.CE_Print_mDouble();
    	}
    }
    
    class ClassExample {
    	
    	private double mDouble;
    	
    	public void CE_Print_mDouble() {
    		System.out.println(mDouble);
    	}
    	
    	public void CE_Set_mDouble(double dInput) {
    		mDouble = dInput;
    	}
    }
    ```
    
    ```
    30.0
    ```
    
- 메소드 내부에서 mDouble변수에 접근하기 떄문에 오류 없이 변수 값을 출력한다.
- 즉, private 및 public을 통해 외부에서 접근 가능한 멤버를 설정해줄 수 있고, 이는 프로그래머로 하여금 정보 은닉의 효과 및 중요 정보의 보안성을 높여주는 방법으로 사용된다.
- 예) getter와 setter

# static

- 정적 멤버
- Heap메모리가 아닌 Stack메모리에 할당되기 때문에 Garbage Collector가 관여하지 않는다.
    - 그렇기 때문에 남발하는 것은 성능에 악영향을 주기에 좋지 않다.
- 모든 객체가 메모리를 공유한다.
- main 메소드에는 무조건 `static`이 붙어야 한다.
- static은 메소드 혹은 변수에 붙여 사용할 수 있는데, 이를 클래스에서 유용하게 사용할 수 있다.
- 만약 클래스 안의 멤버에 static이 붙으면 그 멤버는 클래스의 객체를 선언하지 않고 바로 콜해서 사용할 수 있다.
- 예제
    
    ```java
    import java.io.*;
    class Main {
    	public static void main(String[] args) {
    		
    		//객체를 선언하지 않고 바로 사용
    		ClassExample.mInt = 3; 
    		ClassExample.Print();
    		
    		ClassExample c = new ClassExample();		
    		c.mInt = 20;
    		c.Print();
    	}
    }
    
    class ClassExample {
    	
    	public static int mInt;
    	
    	public static void Print() {
    		System.out.println( mInt );
    	}
    	
    }
    ```
    
    - static 이 붙은 멤버들은 프로그램이 시작될 때 우선 메모리에 할당되기 때문에 new를 통한 객체 초기화가 필요 없다.
- main 메소드에 static이 붙어야 하는 이유는, main 메소드가 프로그램이 처음 시작되는 메소드이기 때문이다. main메소드보다 빨리 실행될 수 있는 코드가 없기 때문에, static을 사용하지 않으면 main메소드의 메모리를 할당해줄 부분이 존재하지 않는다. 따라서 프로그램 시작과 함께 main메소드의 메모리를 static으로 할당하는 것이다.
- static을 사용할 때 클래스 내에서 static을 사용하는 메소드는 멤버변수 사용 시 static 멤버변수만 사용가능하다는 점을 주의.
