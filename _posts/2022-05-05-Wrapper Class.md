### Wrapper 클래스


1. Wrapper 클래스

```
                Primitive Type(기본자료형):Reference Type(참조형)
                                   byte :Byte
                                    short:Short
                                    char:Character
                                    int:Integer
                                    long:Long
                                    float:Float
                                    double:Double
                                    boolean:Boolean       
                    
```

8개의 기본 타이에 해당하는 데이터를 객체로 표현하기 위해 포장 해주는 클래스 이다
각각의 타입에 해당하는 데이터를 객체로 만들어준다 (java.lang패키지에 포함되어 있다)





- isDigit/isLetter() 함수

isDigit함수:명시된 char 값이 숫자인지 여부를 판단하여 true 또는 
false 값으로 리턴한다 -slLetter()함수와 반대의 기능을 한다


```java
package java_study;

import java.io.IOException;

public class JAVA0509_1{
	public static void main(String[] args) throws IOException {
		System.out.println("입력하세요");
		
		char ch =(char)System.in.read();
		
		boolean bool = Character.isDigit(ch);
		System.out.println("bool:"+bool);
		
		if(bool == true){
			System.out.println("숫자");
		}else {
			System.out.println("숫자가 아니다");
	
	}
	
 }	
}
```

```java

```java
입력하세요
2
bool:true
숫자

```

-isUpperCASE:지정된 char 값이 대문자인지 여부를 판별한다
-isLowerCASE:지정된 char 값이 소문자인지 여부를 판별한다

```java



package java_study;

import java.io.IOException;

public class JAVA0509_1{
	public static void main(String[] args) throws IOException {
		System.out.println("입력하세요");
		
		char ch =(char)System.in.read();

		Character.isUpperCase(ch);
//		public static boolean isUpperCase(char ch)
		Character.isLowerCase(ch);
//		public static boolean isLowerCase(char ch)
		
		
		if(Character.isDigit(ch)){
			System.out.println("숫자");
		}else if(Character.isLetter(ch)){
			System.out.println("알파벳문자");
		}else {
			System.out.println("기타문자");
		}
	}
	
 
}


```

```java

입력하세요
A
알파벳문자


```