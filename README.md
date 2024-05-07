f# CSS (Cascading Style Sheet)
## CSS 작성 전 준비사항
* html 문서 준비(태그 작성 완료 상태)
* html, css 파일 별도 폴더 관리
* 최상위 폴더 html 파일 배치
* 하위 폴더명 css, styles 으로 css파일 배치
* ex) index.html, index.css
# 24.04.16
## CSS 외부스타일시트와 내부스타일시트
* name.css 외부파일로 분리해서 html에 link로 연결하는 **외부 스타일시트**
* html파일 내에서 head태그 안에 style태그로 구분해서 작성하는 **내부 스타일시트**
* 외부스타일시트 장단점 :
- 장점 : 1개의 css 파일로 여러개의 html을 관리할 수 있다.
- 단점 : 파일명 또는 파일 위치를 정확히 관리하지 않으면 파일 관리가 어려울 수 있다.
* 내부스타일시트 장단점 :
- 장점 : html파일 내에서 작성하여 태그와 한꺼번에 보기 편하다.
- 단점 : 2개 이상의 html 파일을 동시에 디자인관리하는 것이 불가능하다.
## CSS 선택자
1. 태그선택자 : `<h1></h1>` -> `h1 {속성:값;}`
2. 클래스선택자 : `<h1 class="a"></h1>` -> `.a {속성:값;}`
3. 아이디선택자 : `<h1 id="b"></h1>` -> `#b {속성:값;}`
4. 자손선택자 : `<h1><em><span></span></em></h1>` -> `h1 em span {속성:값;}`
5. 자식선택자 : `<h1><em><em></em></em></h1>` -> `h1 > em {속성:값;}`
## CSS 디자인하기
* CSS 작성 전 HTML이 미리 디자인이 되어있으면 안된다.
* **HTML을 디자인 초기화하는 작업이 CSS 디자인 전 반드시 선행되어야 한다!!!**
* 초기화 CSS `reset.css` 공통파일(날짜나 프로젝트명 표기금지!)
# CSS 글자 표현 속성
## font-family
* 로컬글꼴(설치글꼴제공) 또는 웹 글꼴(추천)을 연결할 수 있다.
* "메인대표글꼴", "후보글꼴" (후보제한없음)
* 후보글꼴은 메인글꼴과 모양이 비슷한 글꼴로 연결해야 한다.
* 글꼴이 한글이거나 공백이 있으면 큰따옴표 안에 작성해야한다.
## font-size
* 웹 글꼴 평균 16px
* 사용 단위 px, %, em, rem
* 절대값 : px, 상대값 : %, em, rem(권장)
* em은 가장 가까운 부모의 폰트사이즈가 베이스가 됨, 이후 자식의 폰트사이즈 비율은 부모의 폰트사이즈 기준으로 설정해야함
* 이를 보완한 단위가 **rem** -> rem은 베이스가 무조건 16px
* 16px = 1.0rem
# 선택자 우선 순위
* #아이디(3) > .클래스(2) > 태그(1)
1. 다음 중 우선 순위가 가장 높고 낮은 선택자는?
* `#box .a .b p {8}` > 3+2+2+1 = 8
* **`#box #a .b p {9}`** > 3+3+2+1 = 9
* `#wrap #box .a {8}` > 3+3+2 = 8
* `#wrap .a .b p {8}` > 3+2+2+1 = 8
2. 다음 중 우선 순위가 가장 높고 낮은 선택자는?
* `#wrap #box .a p p {}` 3+3+2+1+1=10
* `#wrap .b p a {}` 3+2++1+1=7
* `#wrap .a .b p em {}` 3+2+2+1+1=9
* `.wrap .box .a .b {}` 2+2+2+2=8
## color
* 영문명 직접 입력 ex) 테스트용으로 주로 밝을색을 사용한다.
* aqua, lime, yellow, coral, ...
* 헥사코드 입력 최소값 0 ~ 최대값F RGB 코드 기준
* RGB 웹 색상 기준으로 색상으로 섞을수록 밝아진다.
#Hex #000000 => #000, #ff00CC => #F0C
* rgba(red, green, blue, alpha) *최대색상 255
* alpha는 투명도 설정, 범위는 0~1
### 정렬, 폰트 두께, 간격
* `text-align` : 왼쪽, 가운데, 오른쪽 정렬
* `font-weight` : 폰트 두께 설정, 주로 100단위로 두께가 분류됨
* `padding-top/bottom` : 글자 위/아래 간격 조정
# 24.04.17
## box css
### display
* `block, inline, inline-block`
* 특정 태그가 화면에 어떻게 표시될지 지정하는 속성
* `block` : 새로운 행, 크기, 여백 인식
* `inline` : 내용만큼 크기 인식(그 외 크기 인식 불가능)
* `inline-block` : 내용만큼 크기 인식(크기 추가 설정 가능), 옆으로 정렬
### box-sizing
* `box-sizing:border-box`
* 요소의 너비와 높이를 계산할 때 테두리, 여백(padding)까지 포함해서 계산하는 속성
* 속성 미적용 시 : w100 + h100 + padding-top20 = 100x120
* 속성 적용 시 : w100 + h100 + padding-top20 = 100x100
### width, height
* 요소의 너비와 높이
* 절대값px, 상대값%, 화면 상대값 vw, vh
* 상대값 처리는 0~100% 사이 값만 사용한다.
### border-radius
* `border-radius` : 코너를 라운드처리, 정사각형을 원으로 변형 가능
* 부모의 절반인 상대값 50% 적용하여 원모양으로 변경
### box-shadow
* figma drop-shadow = css box-shadow
* box shadow:xpx ypx blur값 색상;
* 띄어쓰기로 수치 나열, 투명도를 주고 싶을 때는 색상을 rgba로 표현
# 24.04.18
## (html) 표 태그 table
### table, tr, td, th
* `table(block)` : 가로-행, 입력 칸 1개-열
* 열의 개수는 테이블의 총 열 개수가 아닌 1행에 배치된 열 수 기준으로 본다!
* `tr(행), td(열)(block)` : 열(td)는 항상 행(tr)안에 존재해야 한다.
* table은 행, 열을 자식, 자손으로 가지는 부모로써 존재한다.
* ` th 제목 열(block)` : 테이블에서의 구조 제목-내용에서 제목을 의미하는 태그
* 제목 - 내용 순서로 배치하기 위해 제목(th)가 먼저 시작하고 내용(td)가 다음 순서로 배치된다.
* th, td는 형제관계, tr(행) 안에서만 존재할 수 있다.
### thead, tbody, tfoot
* `thead, tbody, tfoot 행 그룹(block)` : tr(행)의 부모로 사용되는 태그
* `thead` : 제목행그룹, th위주로 구성된 제목행(tr)을 묶을 때 사용한다.
* `tbody` : 내용행그룹, td위주로 구성된 내용행(tr)을 묶을 때 사용한다.
* `tfoot` : 결과행그룹, th&td들로 구성된 결과값을 가지는 결과행(tr)을 묶을 때 사용한다.
* **(웹 접근성 개념)** 사용자들은 결과를 우선시로 확인하기 때문에 코드 작성시 thead > **tfoot** > tbody로 작성을 많이 함
## (CSS) border & 공통 속성 설정
### border 아웃라인
* `border:1px solid #000;`
* 두께 모양 색깔 순으로 작성한다.
* 모양 종류 : `solid(기본 선)`, `dotted(원형 점선)`, `dashed(직사각형 점선)`
* `border-color` : 선이 이미 존재하는 상태에서 색만 변경할 수 있는 속성
* 표에서 선을 위아래만 주고 싶다면?
`border:1px solid #aaa;`
`border-left:0; border-right:0;`
* 전체적인 border 설정 후 왼쪽, 오른쪽 border를 0으로 설정
### 공통 속성 설정
* 공통으로 속성을 설정하고 싶다면 선택자를 **연속으로 작성**하자!
ex) table, table tr, table tr td {border:1px solid #f00}
# 24.04.19
## (CSS) 여백 margin, padding
### 안쪽 여백 padding
* `padding:npx npx npx npx;` : 여백의 순서는 top > right > bottom > left
* 상하좌우가 다 동일한 경우 -> `padding:npx;`
*상하, 좌우 각각 동일한 경우 -> `padding:상하px 좌우px;`
### 바깥쪽 여백 margin
* `margin:npx npx npx npx;` : 여백 순서 padding과 동일
*  공통 선택자에 margin 적용했을 때 그 사이에 겹침현상 발생함
*  중복되지 않게 먼저 선언하는 선택자에만 margin적용 후 하단 선택자에는 margin을 0으로 설정(겹치는 부분)
## CSS TIP | line-height & a태그
### 버튼, 입력 칸 등의 세로 폭
* `line-height` : 글자가 한 줄 일때 높이가 정해진 레이아웃에서 수직중앙으로 배치하고자 하는 경우 px단위를 사용해서 적용한다.
* 고정폭 -> width, height로 적용
* 유동폭 -> padding으로 적용
### a 태그 디자인할 때
* a태그는 inline, block 특징을 모두 가질 수 있지만 고유한 기본 속성은 inline이기 때문에 표시속성 display명령으로 **block으로 변경**하지 않는 한 크기, 여백을 제대로 인식하지 못한다.
## 수열선택자 nth
* `nth-child(n)` : 수열선택자(자식 기준)
* `nth-of-type(n)` : 수열선택자(요소 기준)
* n의 수는 부모 내에 있는 모든 자식을 기준으로 해당하는 위치를 작성해야한다!
# 24.04.22
## (html) 테이블 열 수평/수직 방향 합치기
### 수직열 합치기 rowspan
* `rowspan="n"` : 수직열 합치기
### 수평열 합치기 colspan
* `colspan:"n"` : 수평열 합치기
* 합치고 싶은 열 중 제일 우선순위 태그에 작성
* 열합치기 적용하면 합친영역이 밀려난다. **합친 열은 모두 주석처리/지우기!**
## 입력 및 선택 컨트롤 양식 Form Tag
* `(block)form`사용자로부터 입력 받을 수 있는 폼을 정의하는 요소
* 폼 데이터를 제출할 서버 스크립트 지정 **action**
* 입력된 정보를 제출하는 최종 주소(URL)은 **action** 속성에 입력
* 폼 데이터를 제출하는 방법 **method**
* 입력된 정보를 제출할 때 HTTP 정보를 **method** 속성에 입력
`<form action="#" method="get" id="search_frm"></form>`
### method
* `post` : 폼 데이터를 HTTP 본문에 포함하여 서버로 전송(보안 높음)
* `get` : 폼 데이터를 URL에 추가하여 서버로 전송(보안 낮음)
## (block) fieldset
* `fieldset` : 양식의 일부를 그룹화하는 태그. legend 그룹제목 포함
* 폼의 양식을 더 읽기 쉽고 이해하기 편하게 구성하는 데 주 목적이 있다
* fieldset과 legend는 HTML 폼 양식 구분용으로 css에선 보이지 않도록 숨긴다!
## (inline) input type="" 입력 필드 속성
* `type` : input 요소가 나타낼 입력 필드의 종류
* `name` : input 요소의 이름을 지정
* `value` : input 요소의 초기값을 지정
`<input type="number" name="item_count" value="1">`
* 속성은 입력양식 / 선택&목록 컨트롤 양식 종류에 따라 의미가 달라진다.
* type : text(문자), number(숫자), password(비밀번호), email(메일주소), search(검색), date(날짜), time(시간), url(주소)
## 속성 maxlength, required, placeholder
* `maxlength="n"` : 최대 n개 글자 제한
* `required` : 필수 작성
* `placeholder` : 정보 작성하기 전 미리 보이는 글자
## (inline)button태그
* `button` - 버튼 태그로 버튼 생성
* `(type) submit` : 작성한 폼의 내용이 저장되어 넘어가는 것
* `(type) reset` : 다시 작성
## 속성선택자(form관련 주로 사용)
1. 태그[속성] 태그에 속성이 있을 때
- `#search_frm input[required] {background-color:yellow;}`
2. 태그[속성=값] 속성의 값이 이것일 때
- `#search_frm input[type=text] {background-color:lime}`
3. 태그[속성^=값] 속성값이 이것으로 시작할 때
- `#search_frm input[type^=p] {background-color:pink}`
4. 태그[속성$=값] 속성값이 이것으로 끝날 때
- `#search_frm input[type$=l] {background-color:blue}`
5. 태그[속성*=값] 속성값이 이것을 포함할 때
- `#search_frm input[type*=ss] {background-color:coral}`
# 24.04.23
## form요소와 속성
### `<form action:"#" mehtod="></form>`
* action : 폼 데이터를 제출할 서버 스크립트 지정
* method : 폼 데이터를 제출하는 방법, GET과 POST 방식이 있음.
### `<input type="" name=""`
* type : input 요소가 나타낼 입력 필드의 종류
* name : input 요소의 이름을 지정
* value : input 요소의 초기값을 지정
* readonly : 읽기 전용, 선택은 되지만 글 작성은 안됨
* autofocus, autocomplete : 검색창 자동 활성화 및 검색어 자동 저장 속성
* placeholder : 안내문자, 정보 작성하기 전 미리 보이는 글자
* value와 placeholder의 차이점 : value는 초기값으로 작성해도 사라지지 않음. 그러나 placeholder의 경우 안내문자이기 때문에 작성시 사라짐
* maxlength : 글자 수 제한 설정
### `<textarea></textarea>`
* rows, cols : 텍스트창의 크기 설정
* 사용용도 및 주의사항 : 크기는 주로 css에서 변경하기 때문에, row,col 거의 사용하지X
### input의 입력양식과 선택양식
* text, url 등의 사용자가 직접입력가능한 입력양식
* radio 등의 사용자의 입력이 아닌 선택으로 들어가는 선택양식
* `name` : 입력양식(데이터구분용), 선택양식(데이터구분(개별데이터X, 그룹데이터구분용))
* `value` : 입력양식(초기값), 선택양식(개별데이터구분용)
## 선택속성 radio, checkbox
### 선택속성 radio
* `radio` : 선택할 수 있는 type
`<input type="radio" name="userMailAgree" value="userMailAgreeY">동의`
### label 이름까지 함께 선택 가능하게 만드는 태그
- input이 label 안에 들어가면 부모-자식 관계로 모두 적용됨
- input과 label이 형제관계인 경우 → label for=”id”를 작성하여 input의 id와 연결해야 적용됨(id만 가능)
- input의 id는 value와 동일하게 적용
### CSS 내에서 이미지 삽입
- (html) `<img src="" alt="">`
- (css) `{background-image:url()}`
* 배경이미지의 기본값 : 제일 아래(안쪽)배경으로 설정 & 반복이미지
* `background-repeat:no-repeat;` : 이미지 반복해제
* `padding-left:26px;` : 겹침현상 해제(이미지와 글 사이 간격을 주는 것)
* `{display:none;}` : 선택양식의 기본 체크표시는 없앨 수 없으므로 숨긴다.
### 선택속성 checkbox
* 체크와 해제 모두 가능한 속성
# 24.04.24
## 수열선택자 nth
* `nth-child(n)` : 해당 순서에 있는 태그 선택
* `first-child` : 제일 첫번째 자식 선택
* `last-child` : 제일 마지막 자식 선택, 주로 마지막 선택자는 이 속성을 많이 사용
* `nth-child(even)` : 짝수 순서에 해당하는 태그 선택
* `nth-child(odd)` : 홀수 순서에 해당하는 태그 선택
* `nth-child(3n+1)` : 3의 배수에 1을 더한 순서에 해당하는 태그 선택
## 속성 overflow
* `overflow:hidden` : 내용이 넘친 글에서 넘친 부분 숨기는 속성
* `overflow-y` : y축으로 스크롤 적용
* `overflow:auto` : 자동으로 스크롤 적용
# 24.04.26
## CSS Layout
### float, flex
* `float` : 형제 관계에 해당하는 block or inline tag 왼쪽, 오른쪽 정렬할 때 사용
* ex) ul-li*3개 정렬 `ul li {float:left;}`
* `flex` : 정렬하고자 하는 아이템의 부모한테 flex를 먼저 설정한다.
* ex) ul-li*3개 정렬 `ul {display:flex;}`
* flex 설정 시 **기본값** : 메인축(수평) 교차축(수직)
* `display:flex` : 정렬대상의 부모 설정 속성값, 설정 시 해당 부모 기준 자식까지(자손X) flexible box layout으로 처리하겠다!
### flex | container, item, 메인축, 교차축
* `container` : 정렬하고자 하는 대상의 부모
* `item` : 정렬하고자 하는 대상
* `메인축` : 아이템이 **정렬**된 방향
* `교차축` : 아이템이 **교차**된 방향
* 교차축은 아이템을 한번에 선택하는 방향, 메인축은 아이템을 가로지르는 방향!
## (container) flex 속성
### (container) flex direction
* container안의 item의 **메인축 방향**을 설정
1. `row(기본값)` : 왼쪽 -> 오른쪽 수평축
2. `row-reverse` : 오른쪽 -> 왼쪽, (float:right와 유사하다)
3. `column` : 위 -> 아래 수직축 변경
4. `column-reverse` : 아래 -> 위
### (container) flex-wrap
* container 내부 items **줄바꿈처리**를 설정
1. `nowrap(기본값)` : 줄바꿈하지 않음(한 줄 처리), 가변너비에 따라 자동으로 % 크기 변경
2. `wrap` : 자동 줄바꿈 처리
3. `wrap-reverse` : 행 기준 역방향으로 자동 줄바꿈 처리
### (container) flex-flow
* **flex-direction**과 **flex-wrap**을 묶음으로 처리
ex) `flex-flow:column wrap;` : 세로열 기준으로 자동 줄바꿈 처리
### (container) justify-content
* **메인축의 정렬방법** 설정
1. `flex-start` : items의 시작점 container의 시작점으로 정렬
2. `flex-end` :  items의 시작점 container의 끝점으로 정렬
3. `center` : items을 메인축 기준 container에서 가운데 정렬
4. `space-between` : items을 container의 **start, end 양끝 items을 배치**하고 나머지는 고르게 정렬
5. `space-around` : items을 container안에서 균등한 여백을 포함하여 정렬
### (container) align-content
* 교차축의 아이템이 2줄 이상일 경우의 정렬방법
* justify-content와 동일!
### (container) align-items
* 교차축의 아이템이 1줄 일 경우의 정렬방법
* space-between과 space-around는 제외됨. 1줄이기 때문에!
## (item) flex 속성
### (item) align-self
* container에 적용하는 align-items보다 우선순위가 높음
* flex box의 교차축을 정렬
* align-content/align-item과 동일!
### (item) order
* 아이템의 정렬 순서를 설정 가능
* 음수(-n) ~ 양수(n)으로 순서 지정
* 숫자가 낮을수록 우선 순서로 위치가 변경됨
### (item) flex
* grow(증가) + shrink(감소) + basis(기본)을 한번에 작성하는 속성
* `flex:1 0 auto` : grow:1 shrink:0 basis:auto
* `flex:1;` : container 내 item들을 1:1:1..의 비율로 넓이 설정
# 24.05.07
## VS code emmet기능(기본기능)
* 꺽쇠 없이 태그명 작성 후 Tab 자동완성
* 특정 태그에 필수속성이 있을 때 속성이 함께 출력
* 자동으로 안나오는 속성은 `태그:속성` Tab 출력
* 클래스명 또는 아이디명을 쓰고 싶을 때
ex) `div.box` ---> `<div class="box"></div>`
ex) `div#box` ---> `<div id="box"></div>`
* 목록태그 작성할 때 **태그>자식태그*자식개수**
ex) `ul.list>li*3`
* 형제태그 함께 작성할 때 **태그>이전형제+다음형제**
ex) dl#test>dt+dd*2