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

- 이미지 scrap

```python
from urllib.parse import quote_plus       #한글 입력문제 해결

baseurl = 'https://search.naver.com/search.naver?where=image&sm=tab_jum&query='
search_keyword = input('검색어 입력 :')

url = baseurl+quote_plus(search_keyword)
```













## Selenium

