# 메모리

## 컴퓨터가 데이터를 저장하는 공간

1. Register
    - CPU(aka 컴퓨터의 두뇌) 내부에서 사용되는 저장공간
2. Storage
    - '하드드라이브'라고도 불리는 HDD(Hard Disk Drive)
    - 용량당 가격이 아주 저렴하다는 장점이 있으나, 속도가 매우 느리다는 단점.
    - 최근에는 SSD(Solid State Disk)라는 HHD의 속도를 보완한 제품이 출시되고 있다. (가격은 더 비쌈)
3. Memory
    - RAM이라고 불리는 하드웨어가 Memory 공간을 담당한다.
    - Storage보다 빠르지만, Register보다는 느린 속도로, Storage와 Register 사이에 위치하여 다른 속도 및 용량을 갖고 있는 저장장소들을 보완하는 역할

|저장공간|Register|Memory|Storage|
|:-|:-:|:-:|:-:|
|용량당 가격|매우비쌈|중간|저렴|
|처리속도|매우높음|중간|느림|
|예시|CPU Register|RAM|HDD, SSD|


## 프로그램 동작 원리

- Storage에 프로그램들이 저장되어 있다.
- Storage에 저장된 프로그램을 실행하면, 운영체제가 해당 프로그램을 **Memory에 Load**한다.
    - Storage의 속도가 너무 느리기 때문에, CPU의 처리속도에 맞출 수 없다. 그래서 Storage에 저장된 프로그램을 그나마 좀 더 빠른 Memory에 Load하여 처리하게 된다.
- 즉, 프로그램은 Storage공간에 먼저 저장되고, 그 프로그램을 실행하게 되면 Memory에 Load되는 절차를 거쳐 실행된다.
- 이 때 Memory에 Load된 프로그램을 **`Process`**라고 한다.

---

# 변수와 상수

## 변수 (Variable)

- 변할 수 있는 어떤 수.
- 변수를 선언하면, 컴퓨터는 비어있는 주소를 가져와 변수명이 기록된 공간을 생성한다.
- 즉, 변수명과 특정 Memory 주소가 연결된다.
    - 변수명 규칙
        - 첫 글자에는 `영문자`, `$`, `_`만 사용할 수 있다.
        - 첫 글자가 아니라면 숫자도 사용 가능하다.
        - 대소문자는 구별된다.
        - 예약어는 사용할 수 없다. (예약어 : 자바에서 기본으로 사용하는 예약된 단어. this, if, class, for, abstract 등)
- 변수를 초기화하지 않으면 컴파일러에서 에러가 발생하므로, 선언 시 초기화하는 습관을 가질것.

## 상수 (Constatnts)

- 값이 변하지 않는 데이터 공간으로, 변수 앞에 **final**을 붙여서 사용한다.
- 상수로 선언된 자료형은 내부의 값을 변화시킬 수 없고, 선언과 동시에 초기화되어야 한다.

```java
final int a = 3;
```

# 자료형

<img width="789" alt="스크린샷 2023-09-14 오후 1 05 06" src="https://github.com/yeawonbong/study-java/assets/75327385/7160ecb3-e667-4d8a-b363-7db74e3813b3">


## 기본형

| 분류 | 타입 | 크기 | 기본값 | 범위 |
| --- | --- | --- | --- | --- |
| 정수형 | byte | 1byte | 0 | -128 ~ 127 |
| 정수형 | short | 2byte | 0 | -32768 ~ 32767 |
| 정수형 | int | 4byte | 0 | -2147483648 ~ 2147483647 |
| 정수형 | long | 8byte | 0L | - 9223372036854775808 ~ 9223372036854775807 |
| 문자형 | char | 4byte | ‘\u0000’ | 0 ~ 65535 (\u0000 ~ \uffff) |
| 실수형 | float | 4byte | 0.0f | single-precision 64-bit IEEE 754 floating point |
| 실수형 | double | 8byte | 0.0d | double-precision 64-bit IEEE 754 floating point |
| 논리형 | boolean | 1byte | false | true, false |

## 참조형

- 기본형이 아닌 자료형은 모두 참조형이다.
- 참조형은 값이 저장된 **주소를 저장하는 자료형**으로, 자바에서는 모두 **객체의 주소**를 의미한다.
    
    (C의 포인터와 같은 개념)
    
1. `Class Type`
2. `Interface Type`
3. `Array Type`
4. `Enum Type`

## 형변환 (Type Casting)

boolean형을 제외한 모든 기본자료형에서 사용 가능하다. 

- 명시적 형변환
    
    ```java
    import java.io.*;
    class Main {
        public static void main(String[] args) {
            double varDouble = 98.76;
            int varInteger = (int)varDouble;  // casting
            System.out.println(varInteger);	
        }
    }
    ```
    
    형을 강제변환한다. 위 경우 정수 데이터만 저장될 수 있기 때문에 실수부 (.76)은 유실된다. 
    
- 묵시적 형번환
    
    ```java
    import java.io.*;
    class Main {
        public static void main(String[] args) {
            short varShort = 5;
            double varDouble = varShort;
            System.out.println(varDouble); 
        }
    }
    ```
    
    형태를 명시하지 않는 형변환. 바꾸고자 하는 타입을 명시하지 않아도 자료형이 자동으로 바뀌는 형변환이다. 
    
    - 묵시적 형변환이 가능한 조건 : `목표 자료형 크기 > 바꾸려는 데이터의 자료형 크기` 일 때 가능하다. (바꾸려는 데이터 자료형의 크기가 더 작을 때)

## Wrapper Class

| 기본 타입 | 래퍼 클래스 |
| --- | --- |
| byte | Byte |
| short | Short |
| int | Integer |
| long | Long |
| float | Float |
| double | Double |
| char | Character |
| boolean | Boolean |

![image](https://github.com/yeawonbong/study-java/assets/75327385/a645451f-b5a1-4191-b4b3-41b217ff0664)


- 래퍼 클래스는 기본형 타입을 객체로 다루기 위해 사용하는 클래스로, 포장객체라고도 말한다.
- 래퍼클래스를 생성할 경우 각 타입에 해당하는 데이터를 파라미터로 전달받아 해당 값을 가지는 객체로 만들어준다.
- 래퍼클래스로 감싸고 있는 기본타입 값은 외부에서 변경할 수 없다.
- 래퍼클래스는 모두 `java.lang` 패키지에 포함되어 제공된다.

### Boxing, UnBoxing

![image](https://github.com/yeawonbong/study-java/assets/75327385/678d1503-3cff-490c-860b-ef25cee8e9cd)


- Boxing: 기본 자료형 → 래퍼 클래스의 인스턴스로 변환
- UnBoxing: 래퍼 클래스의 인스턴스에 저장된 값 → 기본 자료형의 데이터로 변환
    - 언박싱 메소드
        
        
        | 메소드 | 반환값 | 설명 |
        | --- | --- | --- |
        | booleanValue() | boolean | 기본형 데이터를 문자열로 바꾼 뒤에 반환 |
        | byteValue() | byte | 객체의 값을 byte 값으로 변환하여 반환 |
        | doubleValue() | double | 객체의 값을 double 값으로 변환하여 반환 |
        | floatValue() | float | 객체의 값을 float 값으로 변환하여 반환 |
        | intValue() | int | 객체의 값을 int 값으로 변환하여 반환 |
        | longValue() | long | 객체의 값을 long 값으로 변환하여 반환 |
        | shortValue() | short | 객체의 값을 short 값으로 변환하여 반환 |
- 래퍼클래스의 값은 바로 변경할 수 없으므로, 가령 래퍼클래스 인스턴스에 저장된 값을 변경하고 싶다면 언박싱하여 값을 변경한 후 다시 박싱하는 식의 과정이 필요하다.
- 하지만 JDK1.5부터는 자동으로 박싱, 언박싱이 된다.

### AutoBoxing, AutoUnBoxing

- 기본타입 값을 직접 박싱, 언박싱하지 않아도 래퍼 클래스 변수에 대입만 하면 자동으로 박싱과 언박싱이 된다.
- 오토 박싱을 이용하면 new 키워드를 사용하지 않고도 자동으로 인스턴스를 생성할 수 있으며, 언박싱 메소드를 사용하지 않고도, 오토 언박싱을 이용하여 인스턴스에 저장된 값을 바로 참조할 수 있게 된다.
    
    ```java
    /* 기존 박싱 & 언박싱 */
    Integer num = new Integer(17); // 박싱
    int n = num.intValue();        // 언박싱
    
    /* 오토 박싱 & 언박싱 */
    Integer num = 17; // new Integer() 생략
    int n = num; // intValue() 생략
    ```
    
- 자동으로 처리되기 때문에, wrapper class의 연산이 가능하다.
    
    ```java
    Integer num1 = new Integer(7); // 박싱
    Integer num2 = new Integer(3); // 박싱
    
    int int1 = num1.intValue();    // 언박싱
    int int2 = num2.intValue();    // 언박싱
    
    // 박싱된 객체를 오토 언박싱하여 연산하고 다시 박싱하여 저장
    Integer result1 = num1 + num2; // 10 
    Integer result2 = int1 - int2; // 4
    int result3 = num1 * int2;     // 21
    ```
    

### Wrapper Class 비교

- 래퍼 클래스의 객체 값 비교는 포장 내부의 값을 얻어 비교해야 되기 때문에, 직접 언박싱해서 비교하던가, `equals()` 메소드를 통해 바로 비교가 가능하다. (참조형이기 때문에 그냥 비교할 경우 주소값 비교가 됨)
    
    ```java
    Integer num1 = new Integer(10);
    Integer num2 = new Integer(20);
    Integer num3 = new Integer(10);
    
    System.out.println(num1 == num3);      // false
    System.out.println(num1.equals(num3)); // true
    
    // 동등 비교 외의 연산은 문제 없다.
    System.out.println(num1 < num2);       // true
    System.out.println(num1 + num2);       // 30
    ```
    
- 대신 래퍼 클래스와 기본 자료형과의 비교는 자동으로 오토박싱과 언박싱을 해주기 때문에 `==` 연산과`equals()` 연산 모두 가능하다.
    
    ```java
    Integer num = new Integer(10); // 래퍼 클래스1
    Integer num2 = new Integer(10); // 래퍼 클래스2
    int i = 10; // 기본타입
    
    // 래퍼클래스 == 기본타입
    System.out.println(num == i); // true
    
    // 래퍼클래스.equals(기본타입)
    System.out.println(num.equals(i)); // true
    
    // 래퍼클래스 == 래퍼클래스
    System.out.println(num == num2); // false (invalid)
    
    // 래퍼클래스.equals(래퍼클래스)
    System.out.println(num.equals(num2)); // true
    ```
    

### Wrapper을 이용한 자료형 변환 메소드

- 객체를 포장하는 기능 외에도, 래퍼 클래스는 자체 지원하는 `parse타입()` 메소드를 이용하여 데이터 타입을 형 변환 할때도 유용히 쓰인다.
    
    ```java
    String str = "10";
    String str2 = "10.5";
    String str3 = "true";
    
    byte b = Byte.parseByte(str);
    int i = Integer.parseInt(str);
    short s = Short.parseShort(str);
    long l = Long.parseLong(str);
    float f = Float.parseFloat(str2);
    double d = Double.parseDouble(str2);
    boolean bool = Boolean.parseBoolean(str3);
    
    System.out.println("문자열 byte값 변환 : "+b);
    System.out.println("문자열 int값 변환 : "+i);
    System.out.println("문자열 short값 변환 : "+s);
    System.out.println("문자열 long값 변환 : "+l);
    System.out.println("문자열 float값 변환 : "+f);
    System.out.println("문자열 double값 변환 : "+d);
    System.out.println("문자열 boolean값 변환 : "+bool);
    ```

# 정리

- 메모리, 변수, 상수 개념
- 자료형과 형변환(캐스팅)
- Wrapper
