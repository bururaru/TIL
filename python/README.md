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
c.keys() #key만 모아서 dict_keys 타입으로 뱉어냄
c.values() #value만 모아서 dict_values 타입으로 뱉어냄
c.items() #item 쌍을 모아서 dict_items 타입으로 뱉어냄
c.clear() #모든 내용 제거
```

- `list` 나 `tuple`과 같이 보이는 타입이지만 아니라서 list 나 `tuple`에 사용할 수 있는 함수 사용 불가능

- **for문과 같이 반복의 매체로는 사용 가능**

   	

## set{}

> 순서 X, 중복 X

### 관련 함수

```python
& == intersection() # 교집합
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



## for구문

> list 선언시 for, if를 활용할 수 있다. dict 선언시에도 사용 가능

```python
a = [1. 2. 3. 4. 5]
#사용 예시
tmp_list = [tmp ** 2 for tmp in a]
tmp_list2 = [tmp * 2 for tmp in a if tmp%2 == 0]
```









## 기타

### escape 코드

``` python
print("abc', "def", sep="\n")
```

- \n : 개행
- \t : 탭 
- \000 : 널 문자



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





