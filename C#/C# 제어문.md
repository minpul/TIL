# 제어문
기본 제어문(If, else, else if, while, do while, switch, for, continue, goto, return)  
### foreach()?
배열이나 컬렉션의 끝까지 순회하며 각 데이터에 차례대로 접근하여 끝에 도달하면 반복이 종료된다.   
ex) foreach(데이터형식 변수명 in 배열_또는_컬렉션) 형태로 사용   
### Parse() vs convert   
변환 실패시(값이 null인 경우도) 반환값 예외처리하냐 0이냐   
###Pasrse() vs TryParse()   
변환 실패시 반환값 저장함   
ex) int.TryParse(s, out int out_i)   
Switch 조건식은 정수, 문자열, 데이터 형식만 지원   
When절 추가 가능  
Switch식, 문에 부동소수형 사용 가능하나 정밀도 문제로 권장 X    
Console.ReadLine(), Console.WriteLine()  
### 키워드?   
컴파일러에 특별한 의미로 미리 정의되어 예약된 식별자  
ex) using, in, when, out, ref ...  
