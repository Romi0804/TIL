# 20190624 Youtube Clone_3rd


- 2.12 ~2.17 분량

### Recap
---
#### Cookie Parser:

쿠키를 전달받아서 사용할 수 있게 해주는 미들웨어. 사용자 인증 할때 쿠키를 검사하는데 그때 사용됨.

#### Body Parser:

사용자가 웹사이트로 전달하는 정보들을 검사하는 미들웨어. 
request 정보에서 form 이나 json 형태로 된 body를 검사한다.

아바타의 사진이나 비디오를 업로드할때, 제목이나 댓글 같은 정보를 전달할때, form에 담아서 업로드를 하게 된다.

#### helmet

application이 더 안전할수 있게 도와준다. 보안 !

#### morgan

application에서 발생하는 모든 일들을 logging 한다.

---
### Pug

express에서 view를 다루는 방식중 하나.
express로 HTML을 보여줄수 있다. res.send대신에 실제 html로 전달 가능.

Pug는 View engine이다.

우리는 express에서 view engine의 설정값을 바꿀건데, view engine의 기본값(default)은 undefined이다.

pug와 express에는 view파일들의 위치에 대한 기본설정이 있다.
만약 그 설정을 바꾸고 싶다면 view의 설정을 바꾸면 돼 (express  공식문서 app.set()참조 )
application 의 화면이 담긴 디렉토리나 디렉토리 배열을 입력하면 된다.

html파일을 저장해야되는 폴더의 기본값은 `프로젝트의 작업디렉토리 +'/view'` 이다.

ex)
videoController 에서 
`export const home = (req, res) => res.render("home");` 이렇게 res.send 를 render로 바꿔서 사용해주면, 

이 함수가 views 폴더에서 파일명이 home이고 확장자가 pug인 템플릿 파일을 찾은후에 보여준다.

---

html 과 CSS 만으로 작업할때는 똑같은 것을 반복하는 경우가 많아 별로 좋지 않다. 이것들은 프로그래밍 언어가 아니라 논리적인 작업을 할수 없어 적지않은 노동이 필요하다.

그래서 pug를 이용하면 html을 생성하되 javascript의 위력을 가질수가 있다.

pug를 통해 전체 Layout에 필요한 부품을 만들고 원하는대로 조립할수 있다. 

main.pug를 만들어 전체 구조를 짠다음,

```
doctype html
    html
        head
            title UTube
        body
            header
                h1 UTube
            main 
                block content
            footer
                span &copy; UTube    
                
```

main의 content에 들어갈 부품들을 만들어 준다. 

home.pug

```
extends layouts/main

block content
    p Home 
    
```

extends 는 이 레이아웃을 main.pug템플릿에서 펼치겠다는 뜻이다. main.pug의 코드들도 사용하고 추가도 하겠다는 것.

---

#### partials

partials는 페이지의 일부분이야. 조직적인 목적으로만 만들어진다.

그러니까 JSX의 컴포넌트 개념처럼 pug로 이용가능하다.

프로그래밍은 분할정복(나눠서 하나씩 처리하는것) 이다.

pug에서 텍스트 사이에 자바스크립트를 넣고 싶다면 `#{}`를 추가하면 된다.

```
#{new Date().getFullYear()} 
```

이거처럼.

---

### Controller의 정보를 템플릿에 추가하는 방법
(2.16) 참조

라우터가 헤더에 접근하려면 미들웨어를 사용해야해.
미들웨어는 레이어같은것이다. 위에서 밑으로 한단계씩 내려가는 것.
그래서 미들웨어는 위치가 어마어마하게 중요하다. 항상 적용시키는 범위를 생각해서 위치를 정할것.


`res.locals()` : 정보를 내보내는것에 유용하다.
local 변수를 global 변수로 사용하도록 만들어 주는 것.

```
import routes from "./routes";

export const localMiddleware = (req, res, next) => {
  res.local.siteName = "UTube";
  res.local.routes = routes;
  next();
};
```
이 경우에는 미들웨어가 커넥션과 라우터들 사이에 있으니까 next()라고 하면 돼 

---

```
export const home = (req, res) => res.render("home", {pageTitle: "HOME"});

```
render 함수의 첫번째 인자는 템플릿이고, 두번째 인자는 템플릿에 추가할 정보가 담긴 객체이다. 
