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