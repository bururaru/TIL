### 다수의 App에서 동시에 사용 가능한 context를 선언하는 방법

> 공통 header와 footer에 {{***}} 를 사용하여 session 정보를 전달하기 위해 전역 context를 사용하는 방법을 찾아보았다

##### xxxApp/context_processor.py

```python
def what_i_want(request):
    return {
        what_i_want : request.session['name']
    }
```

##### projectApp/settings.py

```python
TEMPLATES = [
    {
        'OPTIONS': {
            'context_processors': [
                'xxxApp.context_processor.what_i_want',
            ],
        },
    },
]
```



선언 이후에 `{{what_i_want}}` 로 사용하면 된다.