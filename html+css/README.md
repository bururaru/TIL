부스트코스 웹 UI 개발 내용 정리(210104~)

# CSS

## 가상 클래스

```css
li:first-child { color: red; } /*첫번째 자식요소*/
li:last-child { color: blue; } /*마지막 자식요소*/

a:link { color: blue; } /*클릭 전의 링크*/
a:visited { color: gray; } /*클릭 후의 링크*/

a:focus { background-color: yellow; } /*포커스 받은 상태 (tab 점선 선택)*/
a:hover { font-weight: bold; } /*마우스 올라가 있을때*/
a:active { color: red; } /*포커스 상태에서 클릭 될때 순간적 실행 */
```



## 가상 요소

> 미리 정의해놓은 위치에 삽입이 되도록 약속된 보이지 않는 요소

```css
p::before { content: "###" } /*가장 앞에 요소 삽입*/
p::after { content: "!!!" } /*가장 뒤에 요소 삽입*/
p::first-line { ... } /*요소의 첫 줄에 있는 텍스트 (화면에 표시되는 줄 기준)*/
p::first-letter { ... } /*블록 레벨 요소의 첫 번째 문자*/
```



## 구체성

```css
h1 { ... }  /* 0,0,0,1 */
body h1 { ... }  /* 0,0,0,2 */
.grape { ... }  /* 0,0,1,0 */
*.bright { ... }  /* 0,0,1,0 */
p.bright em.dark { ... }  /* 0,0,2,2 */
#page { ... }  /* 0,1,0,0 */
div#page { ... }  /* 0,1,0,1 */    /*가장 높은 우선순위*/

/*인라인 스타일*/
<p id="page" style="color:blue">Lorem impusm dolor sit.</p> /* 1,0,0,0 */ 

/*important*/ 
p#page { color: red !important; } /*구체성 무시하고 우선순위 가짐*/
```



## font

### font-family

- sans : 삐침이 없는 글자 (돋움에 해당)
- serif : 삐침이 있는 글자 (바탕에 해당)

`generic-family`는 상속되지 않으므로, 하위에서 폰트 변경 시 다시 선언 해줘야 함.



### line-height

- 2, 200% 등의 표기는 font-size의 배수로 표현됨
- font-size 위아래로 더 공간이 들어가는 수치

### font-size

- 기본값은 16px (1em)

### font-weight

- 400 : normal

- 700 : bold


### vertical-align

- inline 요소에만 적용 가능
- 세로 위치 정렬

### text-align

- inline 요소에만 적용 가능
- 좌우 정렬
- box 요소에 선언하면, box요소 내부의 텍스트가 정렬됨 (box 요소 자체의 가운데 정렬을 위해서는 `margin: auto` 사용)

### white-space

- 줄바꿈과 공백에 관한 속성
- `normal` 과 `nowrap`을 주로 사용

### letter-spacing

- 글자 사이 간격

### word-spacing

- 단어 사이 간격

### word-break

- 단어 어떻게 자를지 정하는 속성

### workd-wrap

- 요소를 벗어나는 단어를 어떻게 감쌀지 정하는 속성



## layout

### display

- `inline`

  - margin, padding, border 를 지정해도 부모 block 요소의 상,하에 영향을 주지 못함 (좌, 우 값만 사용함)

- `block`

- `inline-block`

  - inline과 같은 배치 형태를 가지지만,  blcok과 같은 성격을 가짐

    ```html
    <div stype="display:inline">text</div>
    <!-- 두 요소 사이에는 약 4px의 좌우 여백 존재 -->
    <div stype="display:inline">text</div>
    ```

### visibility

- `hidden` : 요소를 숨기지만 요소가 존재하는 영역은 그대로 유지됨. (display:none 은 아예 렌더링을 안하는 것)

### float

- 요소를 보통의 흐름에서 벗어나 +z 축 방향으로 붕 뜨는 느낌으로 만듬
- 주변 텍스트나 inline 요소가 주변을 감싸게 되는 특징 있음
- 대부분 display 요소 값을 block으로 변경시킴

### claer

- float 된 요소의 영향에서 벗어나게 만드는 속성

- block-level 요소에만 적용 가능


### position

- 기본은 `static` : offset에 영향을 받지 않는다
- `relative` : 기존 자리를 유지하면서 offset 만큼 이동함. (**부모에 relative 선언하면, 자식 요소들의 위치 기준점이 됨**)
- `absolute` : block 요소로 변경됨. 문서의 흐름을 벗어나게 됨. 위치 기준으로부터 offset만큼 이동함
- `fixed` : 문서의 흐름에서 벗어남. 화면을 기준으로 offset만큼 이동함. 부모 요소의 position: relative 에 영향을 받지 않음

### z-index

- position 이 static 아닌 경우에만 지정 가능
- 큰 값이 가장 위쪽으로 쌓임
- 부모가 z-index가 있으면 부모 내부에서만 적용됨







