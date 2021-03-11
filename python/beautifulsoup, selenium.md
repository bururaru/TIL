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

