### React JS

- JavaScript 코드를 HTML로 바꾸는 방식으로 동작



### JSX

- HTML + JavaScript

### Component

``` 
function Name({fav}){
	return <div>this is practice {fav}</div> ; 
}

<div>
	<Name />
</div>
```

와 같이 선언 및 사용 가능.

- 이름은 대문자로 시작
- ```{fav}```는 ```props.fav``` 와 같은 역할을 함. 
- state가 필요할 경우에는 function 이 아닌 class component를 사용해야 함



### setState

- state의 값을 변경할 때 사용
- setState가 실행되면 state의 변경과 함께 render()도 재실행 됨



## Component life cycle

### constructor()

- ``` constructor()```
-  render 이전에 호출됨

### componentDidMount()

- ```componentDidMount()```
- 최초의 render 완료 이후에 호출됨

### componentDidUpdate()

- ```componentDidUpdate()```
- render가 재호출 된 이후 호출됨.

### componentWillUnmount()

- ```componentWillUnmount()```
- component가 사라질때 호출됨 (페이지 이동과 같은 경우)



## axios

### axios.get()

json 계층 구조가 movie-data-data-movies 일때,

``` javascript
const {movie} = axios.get("url")
console.log(movie.data.data.movies)

# 위와 동일한 코드지만 더 멋지다!?
const {
	data: {
		data : {movies}
        }
} = axios.get("url")
console.log(movies)
```

두가지 형태로 사용 가능