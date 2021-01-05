# python

#### Multicampus python 강의 (210104~)의 내용 정리

> interpreter 기반의 언어! (compile 기반이 아니다...)



## 연산자

### %

나머지 연산



### //

몫 연산



### **

``` m**n```

m의 n제곱 연산



## list []

### 생성 방법

```python
a = []
a = list()
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



## tuple ()

### 생성방법

```python
b = ()
b = tuple()
```



## dictionary {}

### 생성방법

```
c = {"1" : "first", "2" : "second"}
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


