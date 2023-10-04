# 다형성 Polymorphism

- 객체가 다양한 형태로 표현될 수 있다는 개념.
    - 추상화된 객체와 같은 '틀'을 가진 객체가 구체화된 객체로 표현 가능하다는 뜻
- 즉, 부모 클래스를 활용하여 자식의 객체를 제어할 수 있다는 뜻으로 이해하면 된다.
    
    ![image](https://github.com/yeawonbong/study-java/assets/75327385/63ed24eb-b5e9-43f7-a1a5-041cecbd3758)
    
- 다형성은 객체를 여러가지 형태로 변환하여 사용할 수 있는 기법으로, 상속관계에 있는 클래스간에 사용할 수 있다.

# 예시코드

```java
public class Main {
	public static void main(String[] args) {
		
		Animal animal_lion = new Lion("사자");
		animal_lion.Growl();
		
		Animal animal_cat = new Cat("고양이");
		animal_cat.Growl();
		//animal_cat.Udada(); 불가능합니다. - 자식의 멤버이기 때문에.
	}
}

abstract class Animal {
	
	String Name;
	
	public Animal(String name) {
		Name = name;
	}
	
	abstract public void Growl(); 
}

class Lion extends Animal {

	public Lion(String name) {
		super(name);
	}

	public void Growl() {		
		System.out.println("어흥");
	}
}

class Cat extends Animal {
	public Cat(String name) {
		super(name);
	}
	
	public void Growl() {		
		System.out.println("야옹");
	}
	
	public void Udada() {
		System.out.println("UDADADA");
	}
}
```

- 자식 클래스들을 부모클래스 타입으로 생성하여 사용할 수 있다.
- 단, 부모 클래스에 없는 멤버를 자식 클래스에서 선언한 경우, 그 멤버는 사용할 수 없다. 현재 타입이 부모클래스 타입이기 때문.
- 다형성은 여러 케이스를 대응해야할 때 자주 사용되는 기법이다.
- 상황에 맞게 객체를 바꿔서 만들어 사용할 수 있으며, 소스코드의 간결성과 재사용성을 높여주는 기법이다.
