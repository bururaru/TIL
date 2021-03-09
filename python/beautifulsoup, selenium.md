## BeautifulSoup

```python
from bs4 import BeautifulSoup                                   #임포트

webpage = requests.get('https://www.daangn.com/hot_articles')
soup = BeautifulSoup(webpage.content, 'html.parser')
```



- url 입력

```python
response = requests.get('https://pythondojang.bitbucket.io/weather/observation/currentweather.html')
soup = BeautifulSoup(response.content, 'html.parser')
```

- 태그로 찾기

```python
table = soup.find('table', {'class': 'table_develop3'})

table.find_all('tbody')
```













## Selenium

