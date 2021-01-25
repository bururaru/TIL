# django



### 초기 설정

- pycharm terminal 에서 다음 명령어로 시작

`django-admin startproject baseWEB` : baseWEB 부분은 프로젝트 이름임.



- 웹 서버 없이 로컬에서 호스팅 하는 설정

  `settings.py` 

```python
ALLOWED_HOSTS = ['localhost', '127.0.0.1']
```



- 타임존 변경

```python
TIME_ZONE = 'Asia/Seoul'
```



- 서버 실행

` python manage.py runserver`

- 앱 추가

`python manage.py startapp 앱이름` 



### 기본 동작 원리

view 는 model을 통해 db를 처리하고, template을 통해 html 렌더링 한다.



#### http method

- POST : 입력 데이터가 URL에 노출되지 않고 요청 메세지 바디에 들어감
- GET : 입력 데이터가 url 뒤 ?이후에 노출되어 전달됨



### 기초

#### 상대경로

`../login` : root 에서 시작하는 상대경로 지정 방법

#### urls.py

```python
path('basketball', views.basketball, name='basket'),       # urls.py 에 이름 지정
    
<a href="{% url 'basket' %}">농구</a>  # html에서 이름으로 호출
```

위와 같이 `name`을 지정하면 경로 호출시 이름을 가지고 호출 가능



