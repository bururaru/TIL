# python

#### Multicampus python 강의 (210104~)의 내용 정리

> interpreter 기반의 언어! (compile 기반이 아니다...)



## 연산자

`%` 나머지연산

`//` 몫 연산

`**` 제곱연산 (m**n : m의 n제곱)

## 비트연산자

`&` 논리곱

`|` 논리합









## list []

### 생성 방법

```python
a = []
a = list()

#range() 사용해서 만드는 방법
a = list(range(1, 10, 2))
```

### indexing

```python
a = [1, 2, 3, 4, 5]
a[3]
```

### slicing

```python
a = [1, 2, 3, 4, 5]
a[0:3]
a[0::-1] #거꾸로 슬라이싱
```

### list 수정

```python
a = [1, 2, 3]
b = [4, 5]
```

`a.appned(b)` => [1, 2, 3, [4, 5]]

`a.extend(b)` => [1, ,2, 3, 4, 5]

`del a[1]` = `a.pop(1)` => [1. 3]



## tuple ()

> 수정 X, 삭제 X

### 생성방법

```python
b = ()
b = tuple()
b = 1,2,3,4,5
```



## dictionary {}

> 순서 X, 키 중복 X, (key : data 쌍)

### 생성방법

```python
c = {"1" : "first", "2" : "second"}
c = dict()
c = dict([("a", "b"), ("c", "d")]) #tuple 활용하는 방법
c = dict(
	a = "first",
	b = "second")
```

### 키 추가

```python
c["3"] = "Third"
```



### 키-값 제거

```python
del c['3']
c.pop('3')
```



### 데이터 확인

```python
c.get("1") #key 만 넣어서 value를 확인할 수 있다
c["1"]
```

### 관련 함수

```python
c.keys() #key만 모아서 dict_keys 타입으로 반환
c.values() #value만 모아서 dict_values 타입으로 반환
c.items() #item 쌍을 모아서 dict_items 타입으로 반환
c.clear() #모든 내용 제거
c.get(key, value) #dic에 'key'가 없으면 dafault값인 'value'를 반환
c.get(key) #dic 안에서 key값에 해당하는 value를 반환
```

- `list` 나 `tuple`과 같이 보이는 타입이지만 아니라서 list 나 `tuple`에 사용할 수 있는 함수 사용 불가능

- **for문과 같이 반복의 매체로는 사용 가능**

   	

## set{}

> 순서 X, 중복 X

### 관련 함수

```python
`& == intersection() # 교집합
| == union() #합집합
- == difference() #차집합
add()
remove()
discare()
```





## range()

```python
range(1, 10) #1~9까지 범위
range(2, 50, 2) #2~49까지 2씩 커지는 값들만
```





## str

문자열도 `indexing` 과 `slicing` 이 가능

`text[: : 2]` 과 같은 방식으로 칸을 건너서 `slicing` 가능



## date type

> import해서 사용해야 함

`from datetime import date` 이나 `from datetime import datetime` 으로 import

한번에 그냥 `import datetime` 으로 import 하는것도 괜찮을지도?



- date : 시간정보 없음
- datetime : 시간정보 있음

`timedelta()` 사용해서 날짜 연산 가능 (days, hours 등 가능, years months 불가능)



추가 기능이 필요하다면 

[python-dateutil]: https://pypi.org/project/python-dateutil/	"dateutil"

 패키지 설치해서 사용.

```python
 from dateutil.relativedelta import * #year 나 month 연산 가능
 from dateutil.parser import *  #특정 형태로 반환
```

### 문자열 -> 날짜 type 변환

(변수 = '2021,01,06-11:12:40' )일때 `strptime(변수, '%Y, %m, %d - %H:%M:%S')`로 type 변환 가능 .(형태과 완전히 동일해야 함)



## for loop

> list 선언시 for, if를 활용할 수 있다. dict 선언시에도 사용 가능 (comprehension)

```python
a= [1, 2, 3, 4, 5]
#사용 예시
tmp_list = [tmp ** 2 for tmp in a]
tmp_list2 = [tmp * 2 for tmp in a if tmp%2 == 0]
```



### enumerate

` for p in enumerate(a)` 와 같은 방법으로 사용 : 몇번째 반복인지 tuple 형태로 반환

```python
a= [1, 2, 3, 4, 5]
for index, value in enumerate(a): #인덱스, 원소 순서로 반환
    print(index, value)
0 1
1 2
2 3
3 4
4 5   
```

### for - else 

반복 가능한 부분이 모두 반복된 후  else 부분이 실행됨

```python
for x in range(5):
    print(x)
else:
    print('end')
```



## while loop

while - else 도 사용 가능







## 기타

### print 옵션

### sep 

문자열 사이에 구분자 추가

``` python
print("abc", "def", sep="\n")
```

- \n : 개행
- \t : 탭 
- \000 : 널 문자

### end

print 다 끝나고 난 뒤에 구분자 추가

```python
print("abc", "def", end='\n')
```







### print 방법

여러 변수 같이 출력

``` python
a = 10
b = "text"
print('{} {}' .format(a, b))
print('%d %s' %(a, b))
```



### dir() 내장함수

해당 인자의 객체와 메소드를 가지고 있는지 보여줌



### 그 외 내장함수

. capitalize()

. upper()

.split()

.replace()

. strip()

.len()

.endswith()

.count()

.find()

.index()



### 문자열에 특정 단어 포함, 미포함 확인

```python
('sample' in myStr)
('sample' not in myStr)
```

`boolean` 으로 결과 return





### random

`import ramdon`

```python
.random() # 0~1 사이 랜덤 실수
.randint(n, m) # n~m 사이 랜덤 정수
.choices(list, k = n) #list 값들 중 n개 랜덤 선택
```



## function

`from #### import @@@ as x`  == `from ####.@@@ import %%`

`import *`는 해당 모듈의 모든 함수를 다 사용하겠다 라는 뜻



### default parameter

```python
def demoFunction(x, y, z = True):
```

`=True` 라고 지정하는 부분이 `default parameter` => 함수 호출시 비어있는 인자의 자리에는 True가 들어간다.



### 특징 (자료형 특징)

function에 전달되는 매개변수가 `mutable, immutable` 인지가 중요!

- mutable : list, dict => function으로 전달될 때 동일한 객체의 주소만 전달한다. (function 내부에서 수정된 값이 global 반영된다)
- immutable : int, string, tuple => function으로 전달될 때 다른 객체가 생성된다.

### nested function (중첩 함수)

- function 내부에 들어가는 functino으로, 부모함수 바깥에서 호출할 수 없다

  ```python
  def outer(num1):
      def inner(num2):
          print(num2)
      inner(num1+100)
  outer(200)
  ```

- 가독성 좋다!

### recursive function (재귀함수)

- 함수 내부에서 함수를 다시 호출하는 방식



### lamda  function

- 가독성 향상, 메모리 절약 

``` python
(lambda x, y : x*y )(10,20)

#위와 동일한 funtion
def multiply(x, y):
	return x*y
multiply(10, 20)

#아래와 같이 사용도 가능 : 함수의 매개변수로 사용
def lambdaDemo(x, y, func):
    print(x*y*func(100,100))
lambdaDemo(10, 20, lambda x,y : x*y)
```



### hint

```python
def funcDemo(word : str, num : int):
```

함수의 매개변수 type을 미리 지정할 수 있음





### 형태

```python
def function1(): #매개변수 X, return X
	print('out')
def function2(): #매개변수 X, return O
    return 'out'
def funciton3(x): #매개변수 O, return O
    return x + "out"
def function4(*x): #매개변수 개수 제한 없이 tuple로 입력 받는다
    return 
def function5(**x): #매개변수 개수 제한 없이 dict로 입력 받는다
    return
```



### return 특징

return 값이 2개 이상인 경우에는 tuple 형태로 return 된다