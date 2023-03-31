## 메소드
객체지향 프로그래밍 언어에서 사용하는 용어, 함수 개념과 비슷.   
일련의 코드를 하나의 이름 아래 묶어 이름을 호출하는 것만으로 실행할 수 있다.  
<br/>
### 키워드 out, ref
```
void Divide( int a, int b, ref int quotient, ref int remainder )
{
    quotient = a/b;
    remainder = a%b;
}

Divide( a, b, ref c, ref d );

Console.WriteLine( "Quotient : {0}, Remainder : {1}", c, d )
```
결과: Quotient : a/b한 값, Remainder : a%b한 값이 출력될 것, 각 변수가 ref 키워드에 의해 참조되어 해당 메모리에 제대로 저장될 것  

out 키워드도 위와 똑같이 사용하면 된다.  

out vs ref?  
ref 키워드를 이용할 경우 해당 매개변수에 결과가 저장되지 않아도 컴파일러는 아무 반응 없음  
그러나 out 키워드를 이용할 경우 해당 매개변수에 결과를 저장되지 않으면 컴파일러가 에러 메세지로 경고    
즉 out에는 ref에 없는 안전장치가 존재!  
그래서 메소드를 호출하는 입장에서는 초기화되지 않은 변수를 매개변수로 넘겨도 괜찮다. 무조건 데이터가 할당되니까.  

### 메소드 오버로딩
하나의 메소드 이름에 여러 개의 구현을 올리는 작업을 의미한다.  
```
int Plus(int a, int b)
{
    return a+b;
}

double Plus(double a, double b)
{
    return a+b
}
```
위와 같이 오버로딩을 하면 컴파일러가 매개션수를 분석하여 어떤 버전이 호출될지 알아서 정해줌  
장점: *일관성↑* , *생산성↑*  
<br/>
### 가변 개수의 인수 
인수의 개수가 정해지지 않았을 경우 사용한 인수 앞에 *params*라는 키워드 사용하여 간단히 해결  
그래서 오버로딩은 매개변수의 개수가 정해지지 않았을 때보다는  
*형식이 정해지지 않*았거나 *명명된 매개변수에 인수를 할당*할 때 이용  
### 명명된 인수?
```
static void PrintProfile(string name, string lunch)
{
	Console.WriteLine("Name:{0}, Lunch:{1}", name, lunch
}  

static void Main(string[] args)
{
	PrintProfile(lunch: "rice", name: "이민영")
}
```
보통 인수는 순서에 따라 자리를 찾아가는데,  
호출할 때 :으로 인수를 직접 명명하면?      
lunch와 name을 순서에 맞게 입력하지 않더라도 각 자리에 할당된다.  
장점: *가독성↑*
### 선택적 인수
 ```
void Selected( int a, int b = 2)
{
	Console.WriteLine( " {0}, {1} ", a, b )
}

Selected( 3 )
```
위와 같이 함수를 선언할 때 특정 인수의 값을 미리 지정할 수 있다  
호출할 때는 나머지만 직접 입력하면 됨  
### 로컬 함수
메소드 안에서 선언되어 그 안에서만 사용되는 함수  
클래스의 멤버, 메소드가 아니기에 함수라고 부름  
해당 메소드의 지역 변수를 자유롭게 사용 가능    