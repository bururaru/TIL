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

#### file read option

- path
- sep
- header
- skiprows
- encoding
- fillna