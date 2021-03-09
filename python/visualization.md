### Visualization

#### matplotlib

- plot 유형
  - line
  - area
  - surface
  - bar
  - histogram
  - box
- `plt.figure(figsize=(m,n) )`
  - `figsize` : 인치 단위로 크기 설정
- `plt.plot(marker=" ", markersize=" ")` : 선 그래프
- `plt.bar()` : 세로형 막대 그래프
- `plt.barh()` : 가로형 막대 그래프
- `plt.title()`
- `ax.set_title()` 
- `plt.xlabel()`
- `ax.set_xlabel()`
- `plt.ylabel()`
- `plt.xticks(rotation='vertial')` : x축 눈금을 세로로 회전
- `ax.set_xticklabels(rotation=75)` : x축 눈금을 회전
- `plt.legend(labels=" ", loc='"best"')` : 범례
- `plt.set_ylim(min, max)` : y축 시작, 끝나는 값의 범위 지정
- `DataFrame.plot(kind="bar")` : DataFrame에 직접 plot으로 그래프 그리기
- `DataFrame.boxplot(by="col_name")` : col_name을 기준으로 묶어서 box plot 그리기
- `ax.pie('column', labels=' ')` : pie 차트 생성
- 

#### file read option

- path
- sep
- header
- skiprows
- encoding
- fillna



#### bar 차트에서 bar 위에 값 추가하기

`gender_cnt_df` 가 다음과 같은 형태일때,

![image-20210305111407561](visualization.assets/image-20210305111407561.png)

```python
gender_cnt_df.plot.bar()
for idx, value in enumerate(gender_cnt_df['명']):
  txt = '%d명' %value
  plt.text(idx, value, txt,
           horizontalalignment='center',
           verticalalignment = 'bottom',
           color = 'red')
```

![img](data:image/png;base64,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)

#### 다중 막대그래프 추가하기

```python
label = ['어린이', '10대', '20대', '30대', '40대','50대','60대이상']
w = 0.1
x = np.arange(len(label))

plt.bar(x-w, dataframe1, width=w)
plt.bar(x, dataframe2, width=w)
plt.bar(x+w, dataframe3, width=w)

plt.xticks(x, label) # x축에 label 이름 넣을 수 있음
```



#### 이상치 정제

![image-20210305153606596](visualization.assets/image-20210305153606596.png)

```python
quantile75 = outlierDF.quantile(q=0.75)  # 3분위수
quantile25 = outlierDF.quantile(q=0.25)  # 1분위수
```

- `IQR (inter quantile range)` : `quantile75 - quantile25`

```python
# lower fence(최저 한계치)
lower_fence = quantile25 - 1.5 * iqr

# upper fence(최대 한계치)
upper_fence = quantile75 + 1.5 * iqr
```

```python
#극단치 경계 값(아래 수평선)
lower_outlier = outlierDF[outlierDF > lower_fence].min()

#극단치 경계 값(위 수평선)
upper_outlier = outlierDF[outlierDF < upper_fence].max()
```

```python
#hwy 연비의 이상치 데이터 추출
hwy_outlier_df = dataDF.query('hwy>' + str(upper_outlier['hwy'])) #query 사용해서 극단치 경계보다 더 큰 값 추출
```





### seaborn

- `sns.barplot()` : 바 그래프로 평균과 편차 표시
  - `hue="col_name"` : col_name 카테고리를 추가
-  `sns.countplot()`: 바 그래프로 빈도 표시
- `sns.regplot()` : 분포를 산점도로 표시
- `sns.distplot()` : 히스토그램 (러그와 커널밀도 추가 가능)
- `sns.heatmap()` : 만약 데이터가 2차원이고 모든 값이 카테고리 값일때 사용
- `sns.stripplot()`: 분포도
- `sns.swarmplot()`: 분산까지 포함된 분포도
- `sns.jointplot()`: 기본적으로는 산점도, x-y축에 각 변수에 대한 히스토그램을 동시에 보여줌





#### folium

`import folium as f` 

- 맵, 마커 추가하기

```python
map = f.Map(location=[37.55, 126.98], zoom_start=10) #위도, 경도 순서로 입력

marker = f.Marker([37.55, 127.05],          #마커 추가
                  popup = "name",
                  icon = f.Icon(color='blue'))
marker.add_to(map)                                   #맵에 마커 추가
```

- 지도 위에 구역 데이터 추가

```python
map = f.Map(location=[37.55, 126.98], zoom_start=10.5)
f.Choropleth(geo_data = geo_str,                    #json 형식의 좌표 데이터
             data = direct_pivot,                   #구역 나누기 기준이 되는 데이터
             columns = [direct_pivot.index, 'price'],
             key_on = 'feature.id', fill_color = "Blues").add_to(map)
```

![image-20210308165538661](visualization.assets/image-20210308165538661.png)

- 주소 데이터 좌표로 변환

```python
gmap_key = 'AIzaSyDVS3t0uJQp5xRc2fMoQ5lp5fHr5V_dVHw'
gmaps = googlemaps.Client(key = gmap_key)

tmp_map = gmaps.geocode('서울시 성동구 뚝섬로 11길 2-1')       #tmp_map을 열어서 위도 경도 뽑아서 사용
```



