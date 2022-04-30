### if문 
- 부등호,등호를 자주 쓴다
- in 문법도 자주 쓴다

- if 조건문: 
    실행할 코드 (조건식이 참일때 실행할코드)


```python
# 관계연산자(비교 언산자)
#>,<,>=,<=,==,!=

a = 0
b = 0
print(a==0) # a는 0과 같다 ==는 같다의 의미(=는 대입연산자)
print(a!=0)# a는 0과 같으므로 거짓이 된다
```

    True
    False
    


```python
# 논리연산자
#and, or, not

a = 100
b = 60
c = 15

print(a>b and b>c)
print(a>b or b>c)
print(not a>b)
print(not b>c)
print(not True)
print(not False)
```

    True
    True
    False
    False
    False
    True
    


```python
#연산자 우선순위
#산술, 관계(비교), 논리 순서 적용
print(2+4>9+2)
```

    False
    


```python
score1 = 90
score2 = 'A'

if score1 >= 90 and score2 =='A':
    print("합격 하셨습니다.")
else:
    print("불합격")
```

    합격 하셨습니다.
    

### 다중 if 문
- 차례로 조건문을 검사하고 싶을때 씀


```python
weight = 50

if weight <= 45:
    print("저체중입니다")
elif weight <=  50  :
    print("정상입니다")
elif weight <= 70:
    print("비만입니다")
```

    정상입니다
    


```python
#중첩조건문
age = 24
height = 162

if age>=20:
    if height >= 170:
        print("1등으로 탑승하셔도 됩니다")
    elif height >= 16.:
        print("2등으로 탑승하셔도 됩니다")
    else:
            print("지원 불가")
else:
    pirnt("23세 이상만 가능")
```

    2등으로 탑승하셔도 됩니다
    

#### 참,거짓의 종류

- 참:True, "내용", [내용], (내용), {내용}, 1
- 거짓: False, "", [], (), {}, 0, None


```python
city = ""
print(bool(city)) # bool 참과 거짓을 의미 

if city:
    print("you are in :" , city)
else:
          print("please enter your city")
    
```

    False
    please enter your city
    
