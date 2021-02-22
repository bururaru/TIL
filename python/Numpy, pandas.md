# numpy

`ndarray` 

- 파이썬 list와는 다르게 메모리 사용량이 적다. (numpy 에서 지원하는 자료형)

- 메모리에 연속적으로 배치된다

- `ndim` 배열의 차원 확인

- `shape` 배열의 모양 확인

- 요소의 type이 다르다면, 자동으로 가장 큰 요소의 type으로 모두 변환된다.

  - ```x = np.array([100, "hello", 3.14])``` -> dtype='<U11'

    

#### indexing

- 다차원 배열 인덱싱

  ```python
  m = np.array([[ 0,  1,  2,  3,  4],
              [ 5,  6,  7,  8,  9],
              [10, 11, 12, 13, 14]])
  print(m[1,2])
  #7
  print(m[2,-1])
  #14
  print(m[1,1:3])
  #[6 7]
  print(m[1:,2])
  #[ 7 12]
  print(m[0:2,3:5])
  #[[3 4]
  # [8 9]]
  ```

  

- boolean indexing

  ```python
  odd_even = np.array([0,1,2,3,4,5,6,7,8,9])
  idx = np.array([True, False, True, False, True, False, True, False, True, False])
  odd_even[idx]
  #array([0, 2, 4, 6, 8])
  odd_even[odd_even%2==0]
  #array([0, 2, 4, 6, 8])
  ```

- fencing indexing

  ```python
  data = np.array([1,2,3,4,5,6,7,8,9])
  idx = np.array([0,2,4,6,8])
  data[idx]
  #array([1, 3, 5, 7, 9])
  ```

- 활용

  ```python
  n_dim_ary[:, [0,3]]
  #array([[ 1,  4],
  #      [ 5,  8],
  #      [ 9, 12]])
  n_dim_ary[:, [True, False, True, False]]
  #array([[ 1,  3],
  #       [ 5,  7],
  #       [ 9, 11]])
  n_dim_ary[[2,0,1],:]
  #array([[ 9, 10, 11, 12],
  #       [ 1,  2,  3,  4],
  #       [ 5,  6,  7,  8]])
  ```



#### 배열의 생성 & 변형

```python
ary = np.arange(0,12,1).reshape(3,4)
#  [[ 0  1  2  3]
#  [ 4  5  6  7]
#  [ 8  9 10 11]]

#int32 로 가져오기                      ->     6
print(ary[1,2])
#ndarray 로 가져오기 (슬라이싱)         ->     [6]
print(ary[1:2, 2])
```

- [ [0 2] [8 10] ] 출력하기

  ```python
  print( ary[[0,2], ::2] )
  print( ary[[0,2]] [:, 0,2] )
  print( ary[np.ix_([0,2],[0,2])] )
  ```

  - np.ix_() 함수를 사용하는 방법이 가장 편리하다

- 배열 생성 시 사용할 수 있는 함수

  - `array()`

  - `arange()` : 특정 규칙에 따라 연속되는 값을 가지는 배열 생성

    ```python
    z = np.arragne(3,21,2)        # 3부터 21까지 2씩 증가하는 값을 가지는 배열
    ```

    

  - `zeros()` : 원소가 0인 배열 생성

    ```python
    z = np.zeros(5)   # 1,5 모양의 1차원 배열 생성
    z = np.zeros((2,3))  # 2,3 모양의 2차원 배열 생성
    z = np.zeros((2,3), dtype='i')  # 2,3 모양의 int32 자료형의 2차원 배열 생성
    ```

  - `ones()` : 원소가 1인 배열 생성

  - `zeros_like()` : 동일한 차원의 배열 생성

  - `ones_like()` : 동일한 차원의 배열 생성

  - `empty()` : 배열 생성에 걸리는 시간을 최소화 하기위해 사용 -> 기존 메모리에 있던 값들이 dummy data로 들어감

  - `linspace()` : 전체 범위를 특정 갯수로 나눈 값을 가지는 배열을 생성

    ```python
    z = np.linspace(0, 100, 5)
    #array([  0.,  25.,  50.,  75., 100.])
    ```

  - `.T` : transpose 

    ```python
    a = np.array([ [1,2,3], [4,5,6] ])
    a_t = a.T
    print(a_t)
    # array([[1, 4],
    #        [2, 5],
    #        [3, 6]])
    ```

  - `reshape()` : 배열의 모양 변경

    ```python
    a = np.array([1,2,3,4,5,6])
    a.reshape(n,m)    ->     # n * m 모양 행렬로 변경
    a.reshape(n, -1)   ->    # n 값에 맞추어 자동으로 생성
    ```

  - `flatten()` : 1차원 모양으로 변경

    ```python
    a = np.array([ [1,2,3], [4,5,6] ])
    ax = a.flatten()
    ```

    

#### 배열의 요소 접근

- 순차적 접근

  ```
  x = np.array([1, 2, 3, 4, 5, 6, 7, 8, 9, 10])
  ```

  - for 문 사용

    ```python
    for tmp in x:
        print(tmp)
    ```

  - `nditer` 사용

    ```python
    ite = np.nditer(x, flags=['c_index'])
    while not ite.finished:
        print(x[ite.index], end=" ")
        ite.iternext()
    ```

  

  ```
  y = np.array([ [1,2,3], [4,5,6] ])
  ```

  - for 문 사용

    ```python
    for i in range(y.shape[0]):
        for j in range(y.shape[1]):
            print(y[i][j], end=" ")
    ```

  - `nditer `사용

    ```python
    ite = np.nditer(y, flags=['multi_index'])
    while not ite.finished:
    	print(y[ite.multi_index], end=" ")
        ite.iternext()
    ```

    



- vector 를 transpose 하려면???

  (1,n) 의 형태로 reshape 먼저 하고 transpose!!!

  ```python
  vec = np.arange(10)
  vec_t = vec.reshape(1, 10).T
  ```

  

# pandas

