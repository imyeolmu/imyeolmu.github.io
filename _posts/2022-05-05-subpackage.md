### 서브 패키지 만들기 및 1,2의보수
1. 서브 패키지 만들기
- day02 에 서브 패키지를 만들려면
만들고자 하는 클래스에 new -> package-> day02.day02.day02_sub 패키지를 만들어 준다

- 도트를 이용해서 서브 패키지를 만든다
- 클래스 생성하기 

2. 패키지 사용하기 


- day02.day02_sub의 패키지를 사용하기

```java

package day02.day02_sub;

public class Book {
		public String title;
		public int price;
		public String author;
	}



```
- 패키지를 사용하려면 import를 해야한다
```java


package day02;

import day02.day02_sub.Book;

public class UserType_04 {
 public static void main(String arg[]) {
	 Book book = new Book();
	 book.title = "자바프로그램";
	 book.author = "김말똥";
	 
	 System.out.println("저자:" + book.author);
 }
}

```

```java
저자:김말똥
```


### 1의 보수 와 2의 보수


1. 1의 보수(4비트)

```
십진수 :- 10
2진수 :1010

1010-> 반전: 0101(반전이 아니고 xor(익스클루시브오알) 하는것:두개의 입력이 같을 같을때는 0이고 두개의 입력이 다를때는 1인 회로이다 )

```

- 양수가 나왔을 시 
```
13-10 = 3  : 1101-1010 = 0011

1010 반전->0101

    1101
+   0101
___________
   1 0 0 0  1 0 :1+1은 2가 아니라 10이 된다
 +           1 ->캐리:최상위 비트
______________
    0 0 0 1 1->3:0011이 나옴

최상위 비트(캐리)를 최하위 비트에 더해준다
```

- 음수가 나왔을 시
```
10-13 =-3
1010-1101=-0011

1101반전->0010


1010
+0010
_________
1  1    0   0->캐리가 나오지 않았을 경우 한번더 1의 보수를 취해주고 
                마이너스를 붙여준다


0011->-0011:-3

```

2. 2의 보수

- 컴퓨터에서는 양수를 음수로 만들때 2의 보수로 표현한다
- 음수를 만들때는 2의 보수를 만들기 위해서는 +1을 한다 

```
십진수-10
1의 보수로 바꾸기 

-1010
 0101
 +  1
________
 0110(2의 보수)

- 양수가 나왔을 때
```java
13-10=3
1101-1010=0011
      0101  

    0101
    +  1
___________
    0110


    1101
  + 0110
_____________
    1 0 0 1 1 ------>0011
    2의 보수는 캐리부분을 버린다
```

-음수가 나왔을 때

```
10-13=-3

1010-1101=0011
     0010
    
    0010
    +  1
___________
   0011



    1010
  + 0011
______________
    1101 - 캐리가 발생하지 않으면 다시 보수를 해줘야하는데 2의 보수법으로
    써야한다 +1 해주기

    1101
_______________
  - 0011


```



```java

package day02;

public class CastingTest_05 {
	public static void main(String args[]) {
		byte b = 023;
		float f = b;
		System.out.println("f:"+f);
		
	
	}
}

```
```java
f:19.0

```

```java

package day02;

public class CastingTest_05 {
	public static void main(String args[]) {
	int m = 20;
	long ln = 40;
	long r = m*ln;
	
	//int r2 = (int)m*ln;
    int r2 =(int)ln*m;
	int r3 = (int)(m*ln); //long형이다 
	byte a = -128; //-128~127
    /*1000 0000
    +         1
    ________________
         1 0 0 0   0 0 0 1 -128 의 2의 보수)

  
127 = 0111 1111
-128 = 1000 0001
______________________
      0000 0010
            +1   - 2의 보수법
_______________________
   1 1  1 1 1  1 1 0

	*/
	 String binaryStr = Integer.toBinaryString(a);
	 System.out.println(binaryStr);
		
	
	}
}



```
```java
11111111111111111111111110000000
```

```java

package day02;

public class CastingTest_05 {
	public static void main(String args[]) {
		byte bb = -50;

        /*
        50: 0011 0010
        1의 보수에서 2의 보수만들기 
        0011 0010
        +       1
        _______________
        1100   1 1 1 0 -> 2의 보수

        */

	 String bbstr = Integer.toBinaryString(bb);
	 System.out.println(bbstr);
	 
	 	int cc= 0xfffffa01;


	String ccstr = Integer.toBinaryString(cc);
	System.out.println(ccstr);
		 
	
	}
}


```
```java

11111111111111111111111111001110
11111111111111111111101000000001
```












