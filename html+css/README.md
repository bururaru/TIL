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