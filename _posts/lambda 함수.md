### Lambda 함수
- 단일문으로 표현되는 익명함수
- 간단한 함수를 의미
- 코드상에서 한번만 기능이 있을 때, 굳이 함수로 만들지 않고 1회성으로 만들어서 사용할 때 주로 활용


```python
def square(x):
    return x ** 2

square(3)
```




    9




```python
square = lambda x : x**2

square(3)
```




    9




```python
def add(x, y):
    return x + y

add(10, 20)

add2 = lambda x, y : x + y

print(type(add2))

add2(10, 20)

def func2(x, y, func): # 함수를 인자로 받아서 처리  
    print(x*y*func)
    
func2(10, 10, add2(1,2))  


```

    <class 'function'>
    300
    

### lambda와 유용하게 사용되는 함수
 - filter : 특정 조건을 만족하는 요소만 남기고 필터링
 - map : 각 원소를 주어진 수식에 따라 변형하여 새로운 리스트로 변환


```python
def even(n):
    return n % 2 == 0

even(3)
```




    False




```python
# filter(함수, 리스트)
nums = [1,2,3,6,8,9,10,11,13,15]

k = list(filter(even, nums))

print(k)

kk = list(filter(lambda n : n%2==0, nums))
print(kk)


```

    [2, 6, 8, 10]
    [2, 6, 8, 10]
    


```python
# map(함수, 리스트)
a = ['11', '22', '33', '44']

k = map(int, a)

print(k)
print(list(k))



```

    <map object at 0x000001B34C0D8940>
    [11, 22, 33, 44]
    


```python
# 문제> even 함수를 lambda함수로 적용해서 리스트로 변환해보세요.(map 함수 활용)
a = ['11', '22', '33', '44']

k = map(int, a)
kk = list(k)

print(kk)
# print(list(k))

print(list( map(lambda n: n%2==0, kk)))
```

    [11, 22, 33, 44]
    [False, True, False, True]
    


```python
https://open.kakao.com/o/gUKrGm7d
```
