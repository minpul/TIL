## 클래스
객체지향 프로그래밍(Object Oriented Programming)은 코드를 *객체*로 표현하고자 하는 프로그래밍 패러다임  
클래스: 객체(=인스턴스)의 속성과 기능을 정의하나 실체가 없는 청사진 역할  
코드 관점에서 보면 또 하나의 *복합 데이터 형식*이기도 함  
<br/>
필드: 클래스 내 선언된 변수  
메소드: 특정 기능을 구현하고자 정의된 코드들의 집합으로 함수와 비슷  
멤버: 필드와 메소드, 프로퍼티, 이벤트 등 클래스 내 선언된 요소들을 일컫는 말 
<br/>
### 생성자
클래스는 복합 데이터 형식이고, 복합 데이터 형식은 *참조 형식*으로 사용해야 함    
힙에 실제 객체를 생성할 *생성자*가 필요!  
```
ex> Doggy dok = new Doggy();  
dok은 그 자체에 메모리가 할당되는게 아니고 객체의 *주소*를 가리킴  
그래서 new 연산자와 기본 생성자 Doggy로 객체 *생성*  
```
### 기본 생성자
형식은 클래스이름()  
컴파일러에서 자동으로 클래스이름과 같은 생성자를 만듦  
생성자를 하나라도 직접 정의하면 C# 컴파일러는 이러한 기본 생성자를 만들지 않음    
<br/>
### 종료자
형식은 ~클래스이름()  
객체를 소멸시킴. 오버로딩, 호출, 매개변수, 한정자 사용 X  
사용자에게 직접 사용을 권장하지 않는 이유  
1. CLR의 가비지 컬렉터가 언제 작동할지 예측할 수 없음  
2. 클래스의 조상을 찾아 객체로부터 상속받은 Finalize() 메소드를 호출해야 해서 프로그램 성능 낮아짐  
3. 사람보다는 가비지 컬렉터가 소멸을 더 잘 처리함  
### 정적 필드
인스턴스에 소속된 필드 vs 클래스에 소속된 필드(static) ?  
한 프로그램에 서로 같은 인스턴스는 여러개가 존재할 수 있으나 서로 같은 클래스는 존재할 수 없음  
그래서 어떤 필드가 클래스에 소속된다는 것 = 해당 필드가 프로그램 전체에서 유일하게 존재한다는 것!  
 static이 이를 지정하는 한정자, 한정되지 않은 필드는 자동으로 인스턴스에 소속  
필드를 선언할 때 앞에 static을 붙여 한정함  
정적 필드는 인스턴스를 만들지 않더라도 호출 가능
### 정적 메소드
역시 정적 메소드는 인스턴스를 만들지 않더라도 호출 가능  
이와 반대되는 비정적 메소드 = *인스턴스 메소드*, 인스턴스를 생성해야만 호출 가능  
메소드를 선언할 때 앞에 static을 붙여 한정  
<br/>
보통 객체 내부 데이터를 이용해야 하면 인스턴스 메소드를 선언, 아니면 정적 메소드로 한정한다.  
### 얕은 복사 vs 깊은 복사
얕은 복사: 데이터를 가져와 새로운 메모리에 할당하는 방식이 아닌 데이터를 참조하는 형식의 복사 ( 실제 데이터 1개 )    
깊은 복사: 데이터를 가져와 새로운 메모리에 할당하는 방식을 취하는 형식의 복사 ( 실제 데이터 2개 )  
클래스 = 복합 데이터 = 참조 형식 = 그냥 =으로 데이터 할당시 얕은 복사가 됨   
C#에는 이를 자동으로 구분해주는 구문이 따로 없으므로,  
객체를 힙에 새로 할당하여 멤버를 일일히 복사해넣을 구문을 직접 작성해야 함  
### this 키워드
객체 외부에서 객체의 필드나 메소드에 접근할 때 객체의 이름(변수 or 식별자)을 사용한다면,  
객체 내부에서는 자신의 필드나 메소드에 접근할 때 this 키워드 사용  
```
class Dog
{
	private string DogName; // SetName의 매개변수에 있는 DogName과 다른 클래스의 필드  

	public void SetName( string DogName ) // Dog 클래스에 선언된 필드와 다른 매개변수가 외부로부터 전달됨  
	{
		this.DogName = DogName; // this 키워드로 서로 다른 두 DogName이 명확하게 구분됨
	}
}
```
### this() 생성자
키워드 this가 객체 내부에서 자기 클래스의 필드나 메서드를 가리켰다면,  
생성자 this()는 자기의 생성자를 가리킴  
```
class MyClass
{
	int a, b, c;

	public Myclass()
	{
		this.a = 5425;
	}

	public MyClass(int b) : this() // this()는 MyClass를 호출하는 것
	{
		this.b = b;
	}
	
	public Mylass(int b, int c) : this( b ) // this( b )는 MyClass(int b)를 호출하는 것 
	{
		this.c = c;
	}
}
```
위는 오버로딩을 예시로 설명한 것임  
### 접근한정자
1. 클래스의 멤버들을 사용자로부터 보호하고자 여섯 가지의 접근한정자를 가짐  
public, protected, private, internal, protected internal, private  
퍼블릭: 내/외부 모든 곳에서 접근 가능  
프로택티드: 자신을 상속한 자식 클래스에서 접근 가능  
프라이빗: 클래스의 내부에서 접근 가능  
인터널: 같은 어셈블리=프로젝트 파일에 있는 코드에서 public으로 접근 가능  
프로택티드 인터널: 같은 어셈블리=프로젝트 파일에 있는 코드에서 protected로 접근 가능  
프라이빗 프로택티드: 같은 어셈블리=프로젝트 파일에 있는 클래스에서 상속받는 클래스 내부에서 접근 가능  
### 상속으로 코드 재활용
방식은 아래와 같음  
```
class 기반 클래스
{
}
class 파생 클래스 : 기반 클래스
{
}
```
기반 클래스의 생성  
파생 클래스의 생성  
파생 클래스의 소멸 
기반 클래스의 소멸 순서로 작동함  
### base 키워드
기반 클래스의 생성자가 매개변수를 입력받도록 선언되어 있는 경우 base 키워드를 이용    
그러면 파생 클래스의 생성자에서 기반 클래스의 생성자로 매개변수를 넘겨줄 수 있음  
public Derived(string Nmae) : base(Name) 이런 형태  
*sealed 한정자*를 class 앞에 붙이면 상속이 봉인
### 기반 클래스와 파생 클래스 사이 변환 ???
민영, 민서는 다른 개체이나 인간이라는 공통점 때문에 묶임  
```
class Human
{
	public void Say() { ... }
}
class Minyoung : Human
{
	public void drawing() { ... }
}
class Minsu : Human
{
	public void readingbook() { ... }
}
```
이를 다음과 같이 익숙하게 인간은 인간, 민영은 민영, 민서는 민서로 각각 표현 가능  
```
Human human = new Human();
Human.Say();

Minyoung minyoung = new Minyoung();
Minyoung.Say();
Minyoung.drawing();

Minsu minsu = new minsu();
Minsu.Say();
Minsu.Readingbook();
```
한편 민영도 인간, 민서도 인간, 민호도 인간이라는 코드도 가능  
```
Human human = new Human();
human.Say();

human = new Minyoung();
human.Say();

Minyoung minyoung = (Minyoung)human;
minyoung.Say();
minyoung.draw();

human = new Minsu();
human.Say();

Minsu minsu = (Minsu)human;
Minsu.Say();
Minsu.Readingbook();
```
이런식으로 족보를 오르내릴 수 있다.  
### 의문 해소
Human human = new Human();  
human = new Minyoung(); 에서,   
human은 참조로 메모리를 가리키는 역할  
생성자 Human()는 객체의 초기화 역할 (초깃값 할당)  
new 연산자는 메모리에 할당하는 역할  
즉 원래 new Human();로 초기화된 객체가 할당된 메모리를 참조하던 human이  
new Minyoung();으로 초기화된 객체가 할당된 메모리를 참조하게 된 것  
<br/> 
mammal.Bark();가 불가능한 이유?  
이 시점에서는 CLR이 mammal를 Mammal 타입으로 보고 있기에 오류  
C#은 형식 검사를 엄격하게 하는 강형 언어  
### 강형언어?
모든 변수의 타입이 컴파일하면서 결정되는 언어  
변수와 값에서, 형 선언이 변수에 선언되어 있으면 강형, 값에 연결되어 있으면 약형  
서로 다른 형 사이의 변환이 금지되어 있음
### is와 as
is: 객체가 해당 형식에 해당하는지 검사하여 그 결과를 bool값으로 반환
as: 형식 변환 연산자와 비슷하나, 형변환에 실패할 때 예외를 던지는 대신 객체 참조를 null로 만듦 
아래는 예시   
```
Human human = new Minyoung();
Minyoung minyoung;

if (human is Minyoung) // human 객체가 Minyoung 형식인지 확인
{
...
}
```
<br/>
```
Mammal mammal2 = new Cat();

Cat cat = mammal2 as Cat; // (Cat)mammal2 꼴 대신 as 연산자를 사용한 것
if (cat != null) // 변환 실패시 cat은 null이 되기에 작성된 조건
{
	cat.Meow
}
```
### 오버라이딩과 다형성
다형성Polymorphism은 객체가 여러 형태를 가질 수 있음을 의미
```
class ArmorSuite
{
	public virtual void Initialize() // 추후 오버라이딩을 하려면 메소드가 virtual 키워드로 선언되어야 함
	{
		Console.WirteLine("Armored");
	}
}
위 베이스에서,
class IronMan : ArmorSuite
{
	//...
}

class IronMan : ArmorSuite
{
	public override void Initialize()
	{
		base.Initialize();
		Console.WriteLine("Repulsor Rays Armed");
	}
}
```
private로 선언한 메소드는 오버라이딩할 수 없음  
### 메소드 숨기기
```
class Base
{
	public void MyMethod()
	{
		Console.WriteLine("Base.MyMethod()");
	}
}

class Derived : Base
{
	public new void MyMethod()
	{
		Console.WriteLine("Derived.MyMethod()");
	}
}

Derived derived = new Derived();  
derived.MyMethod(); // Base.MyMethod()를 감추고 Derived.MyMethod()만 출력  
```
*new* 한정자로 수식하여 숨길 수 있다  
이름 그대로 메소드를 숨기고 있을 뿐 오버라이딩과 다르게 작동함  
만약 아래와 같이 입력하면 
```
Base baseOrDerived = new Derived();
baseOrDerived.MyMethod(); // 숨겨져있던 "Base.MyMethod();"이 출력됨  
```
### 오버라이딩 봉인하기
클래스 상속 봉인 : 한정자 public
메소드 오버라이딩 봉인 : 키워드 sealed
단, "virtual로 선언된 가상 메소드를 오버라이딩한 버전의 메소드"만 봉인 가능  
why? 애초에 virtual로 선언했다는건 오버라이딩하려 했다는 이야기니까  
봉인할거면 vitual 선언을 안하면 되는 것
ex> public sealed override void SealMe()  
### 읽기 전용 필드
const double pi = 3.14159265359;
위는 상수
```
class Configuration
{
	private readonly int min; // 읽기 전용 필드로 선언하면 생성자 안에서만 초기화가 가능함
	private readonly int max;

	public Configuration(int v1, int v2)
	{
		min = v1;
		min = v2;
	}
}
```
### 클래스 중첩
클래스 안에 클래스를 선언
```
class Outer
{
	class Inner
	{
		...
	}
}
```
안의 클래스는 자신이 소속된 클래스의 모든 멤버(private까지도)에 자유롭게 접근  
