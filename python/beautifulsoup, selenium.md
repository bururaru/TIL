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

```python
from selenium import webdriver

path = './driver/chromedriver.exe'
driver = webdriver.Chrome(path)
```



- 아래와 같은 구조일때

```html
<div id='top'>
    <ul class='menu'>
        <li></li>
        <li></li>
    </ul>
</div>
```



- 위에서부터 순서대로 접근

```python
menus = driver.find_elements_by_css_selector('#top ul.menu li')
```



-  태그 이름으로 접근

```python
li_tag = ul_tag.find_elements_by_tag_name('li')
```





- 클릭

```python
xxx.click()
```

- 버튼 활성화 확인

```python
xxx.is_enabled()   #True, False 값으로 반환됨	
```

- 뒤로가기

```python
drive.back()
```





- xpath

  아래 두개는 동일한 li를 불러오는 코드

```python
lis = driver.find_elements_by_css_selector('#emergencyPrd > div > ul > li')

lis = driver.find_elements_by_xpath('//*[@id="emergencyPrd"]/div/ul/li')

lis = driver.find_elements_by_xpath('//*[@id="emergencyPrd"]/div/ul/li[position() <= 3]')        # 3개만 가져오는 조건 추가
```





#### json 으로 저장하기

```python
import json, re
# re : regular expression : 정규표현식

# json.dumps() : 데이터를 json 형태로 인코딩(문자열)
# json.dump() : 데이터를 json 형태로 인코딩해서 파일에 저장(문자열)
```



- 메타문자

- `[]` : 사이의 문자
- `[from - to]` : from 과 to 사이의 모든 문자
- `\d` : 0~9 사이의 숫자 하나
- `\D` : 숫자가 아닌 문자 하나     ( = `[^0-9]`)
- `\s` : 공백
- `\S` : 공백이 아닌 것
- `\w` : 문자 + 숫자 + _  ( = `[a-zA-Z0-9]`)
- `\W` : 문자 + 숫자 + _ 아닌것
- `^[]` : 시작 문자를 매치
- `$[]` : 끝 문자를 매치
- `*` : 반복 (0 ~ 무한)
- `+` : 반복 (1 ~ 무한)
- `?` : 있어도 되고 없어도 된다 ( 0 또는 1)
- `{cnt}` : cnt 만큼 반복
- `{x, y}` : x~y번 반복
- `.` : 개행문자(\n)를 제외한 모든 문자



#### 문자열 검색 & 치환

- `match()` : 문자의 처음부터 정규식과 매칭되는지 탐색
- `search()` : 문자 전체에서 정규식과 매칭되는 부분이 있는지 검색
- `findall()` : 정규식과 매칭되는 모든 문자를 찾아서 리스트로 반환
- `finditer()` : 정규식과 매칭되는 모든 문자를 반복가능한 객체로 반환
- `sub()` : 정규식과 매칭되는 부분을 치환