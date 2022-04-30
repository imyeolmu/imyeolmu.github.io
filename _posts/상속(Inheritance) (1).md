### Class Inheritance(상속)
- 코드를 재사용하는 기법
- 기존에 정의해둔 클래스를 그대로 물려받는 기법
- 기존 클래스에 일부 기능을 추가하거나, 변경하여 새로운 클래스를 정의하는 기법
- 기존 클래스를 Parent, Super, Base 클래스라고 한다.
- 상속을 받는 클래는 Child, Sub, Derived 클래스라고 부른다.


```python
class Car:
    '''Parent Class'''
    def __init__(self, _type, color):
        self._type = _type
        self.color = color
        
    def show(self):
        print('Car 클래스의 show메소드')
        
class BmwCar(Car):
    def __init__(self, car_name, _type, color):
        super().__init__(_type, color)
        self.car_name = car_name
        
    def show_model(self):
        print('Your Car Name : %s' % self.car_name)

class Avante(Car):
    def __init__(self, car_name, _type, color):
        super().__init__(_type, color)
        self.car_name = car_name
    
    # 메소드 오버라이드 : 재정의
    def show(self):
        print('Avante 클래스 "show" 메소드')
    
    def show_model(self):
        print('Your Car Name : %s' % self.car_name)    
        
# model1 = BmwCar('500d', 'sedan', 'silver')        
# model1.car_name
# model1._type

# model1.show()
avante = Avante('new 아반떼', '2000cc', 'white')
avante.car_name
avante.show_model()

avante.show()


```

    Your Car Name : new 아반떼
    Avante 클래스 "show" 메소드
    


```python
class Parent:
    def singing(self):
        print('sing a song')
father = Parent()
father.singing()
```

    sing a song
    


```python
class Child(Parent):
    pass

child = Child()
child.singing()
```

    sing a song
    

### 상속은 의미적으로 is - a 관계
- Student is a Person
- Employee is a Person


```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age
        
    def eat(self, food):
        print(f'{self.name}는 {food}를 먹습니다..')
        
    def sleep(self, minute):
        print(f'{self.name}는 {minute}분동안 잡니다..')
    
    def work(self, minute):
        print(f'{self.name}는 {minute}분동안 일합니다..')
        
        
class Student(Person):
    pass

class Employee(Person):
    pass

stu1 = Student('홍길북', 25)
stu1.eat('우유')

emp1 = Employee('홍길남', 30)
emp1.work('480')
```

    홍길북는 우유를 먹습니다..
    홍길남는 480분동안 일합니다..
    


```python
# Student 객체는 work() 호출시 " 동안 공부합니다.."로 
# 오버라이딩 하세요.

class Student(Person):
    def work(self, minute):
        print(f'{self.name}는 {minute}분동안 공부 합니다..')
        
kim = Student('김말똥', 24)
kim.work(120)


# Employee 객체는 work() 호출시 " 동안 사무를 봅니다.."로 
# 오버라이딩 하세요.
class Employee(Person):
    def work(self, minute):
        print(f'{self.name}는 {minute}분동안 사무를 봅니다..')

emp1 = Employee('이말똥', 30)
emp1.work(300)
emp1.eat('빵')

```

    김말똥는 120분동안 공부 합니다..
    이말똥는 300분동안 사무를 봅니다..
    이말똥는 빵를 먹습니다..
    

###   super
- 하위클래스(자식클래스)에서 부모 클래스의 method를 호출할때사용


```python
#person class를상속 받아 student class를 만듬
# 학생의 속성으로 이름, 나이, 학번(stu_num)
# 학생 객체를 만들어서 학번을 출력

class Student(Person):
    def __init__(self, name, age, stu_num):
        super().__init__(name, age) # 부모클래스에 있는 호출함 (self 쓰지 않음)
        self.stu_num = stu_num

student1 = Student('김길동',21, 202022)
student1.stu_num 
```




    202022




```python
# student가 아르바이트를 하는경우 일도 하고 공부도 하는 studnet 객체를 만드셍
#  work() 호출시 super( ) 사용
# 홍길동은 30분동안 일을 합니다 그리고 30분동안 공부도 합니다
# 그리고 30분동안 공부도 합니다
 
class Student(Person):
    def work(self,minute):
        super().work(minute)
        print(f'그리고 {minute}동안 일을 합니다 그리고 {minute}동안 공부 합니다')
        
hong = Student('홍길동','23')
hong.work(30)
```

    홍길동는 30분동안 일합니다..
    그리고 30동안 일을 합니다 그리고 30동안 공부 합니다
    


```python
# phone 객체를 만들고 
#phone 객체를 상속받는 smartphone 객체를 만드세요

# phone 객체의 속성
# marker,price,color
# 메소드 phone_info: 제조사,컬러,가격을 출력
    
```


```python
class Phone:
    def __init__(self, marker, price, color):
        self.marker = marker
        self.price = price
        self.color = color
        
    def phone_info(self): 
        print('제조사:', self.marker)
        print('가격:', self.price)
        print('컬러:', self.color)

class smartphone(Phone):
    pass
        

```


```python
iphone = smartphone('apple', '164', 'white')
iphone.phone_info()
print(iphone.marker) #marker 만 출력하고 싶을때
```

    제조사: apple
    가격: 164
    컬러: white
    apple
    


```python
class Phone:
    def __init__(self, marker, details):
        self.marker = marker
        self.details = details
    

    def phone_info(self):
         print(f'제조사:{self.marker},제품상세:{self.marker}')

class smartphone(Phone):
    pass
        
iphone = smartphone('iphone', {'price':1000,'color':'white'})
iphone.phone_info()

#컬러만 출력
print(iphone.details['color'])

#가격만 출력
print(iphone.details['price'])

#제조사만 출력
print(iphone.marker)
               

```

    제조사:iphone,제품상세:iphone
    white
    1000
    iphone
    


```python

```
