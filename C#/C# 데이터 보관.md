### CLR(Common Languge Runtime)?  
C#으로 만든 프로그램은 CLR 위에서 실행된다.  
CLR은 .NET 라이브러리와 함께 OS 위에 설치된다.  

소스 코드 -> 중간언어 Intermediate Language -> 네이티브 코드  
여기서 IL을 네이티브 코드로 바꾸는 JIT 컴파일을 돕는다.      

CLR은 다양한 언어를 지원하도록 설계되었고,  
그 중간 지점이 중간언어라서 2회 컴파일하는 것      
다양한 플랫폼에 최적화된 코드를 만들어냄    
컴파일 비용이 올라가나 다양한 환경에서 안정적  

### 자료형
float a = 3.14f에서 f의 명시 효과로 경고문자 안 나오는거  
단일 정밀도, 복수 정밀도, float4, double8, decimal16    
false와 true 값을 가지는 bool  
  
object는 참조 형식, 박싱(힙으로 포장object)과 언박싱(스택으로 꺼냄int)    
동적인 데이터 영역인 **힙**(CLR의 가비지 컬렉터가 청소)과     
함수가 끝나면 비워지는 **스택**(코드블럭 끝나면 선입후출로 자동 청소)  

### 형변환
int와 uint, byte와 sbyte에서 오버플로우, 언더플로우 발생 이유?    
uint와 sbyte가 음수를 표현할 때 사용하는 2의 보수법 때문!      
2의 보수법은 일반 비트에서 수를 반전한 뒤 1을 더하는 방식임      
형변환시 정수, 소수 큰거에서 작은건 ok    

### 문자열 관리
Parse(): 문자열을 정수로 변환  
열거형: enum 열거 형식명 : 기반자료형 {상수1, 상수2, ...}    
Nullable 형식:  데이터형식? 변수이름; 참조형식은 못씀...    
Nullable 형식은 HasValue(값의 존재)와 Value(값) 두 가지 속성 가짐        
var: 컴퓨터가 자료형 대신 지정하는 것, 참조 형식인 object과 아예 다른 개념    
반드시 선언과 동시에 초기화해야 함! 그래야 형식 추론 가능
CTS(Common Type System) 공용 형식 시스템: ex) System.Int32, System.String ...  
모든 자료형은 object 형식 물려받는데,   
그 메서드 중 일부가 GetType(), ToString()이라 모든 자료형에서 호출 가능한 것  
문자 찾기: IndexOf(), LastIndexOf(, StartsWith(), EndsWith(),  
Contains(), Replace()  
ToLower(), ToUpper(), Insert(), Remove(),  
여백 지우기: Trim(), TrimStart(), TrimEnd()  
나누기: Split(), SubString()  
길이: Length  

C를 먼저 배우고 나니 처음 컴퓨터 언어를 배울 때만큼의 충격은 없다.  
다만 C와의 차이점이 너무 많아서 신기하다.  
아직 한 단원밖에 안했는데 입출력 자료형도, 메모리 할당도, 컴퓨터가 대신 구해주고 있다.  






