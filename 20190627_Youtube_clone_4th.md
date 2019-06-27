#20190627 Youtube Clone_4th

 - 2.18 ~ 2.20 분량
 
## pug 이용하여 form 추가

### action 속성
 
action 속성은 `<form>` 태그에 입력된 내용을 처리하는 서버 프로그램의 URI를 지정하는 역할을 한다. 속성값은 아래와 같이 처리할 프로그램의 경로를 지정한다.

### method 속성 - get, post

 `<form>` 태그의 method 속성은 사용자가 입력한 내용을 어떤 방식(get, post)으로 넘길 것인지를 지정하는 역할을 하며 속성값으로 get과 post가 있다. 
여기서 get 방식은 주소 표시줄에 입력한 내용이 나타나며 256byte~4096byte까지의 데이터만을 서버로 전송할 수 있다. 주소 표시줄에 입력한 내용이 노출되기 때문에 보안상의 문제가 민감한 경우에는 사용하지 않는다. 주소줄에는 `?name=value&name=value` 형태로 나타난다.
 post 방식은 입력된 내용의 크기에 제한을 받지 않고 입력한 내용이 노출되지 않기 때문에 회원가입, 로그인 시 등에 많이 사용된다.

### name 속성

 name은 한 문서에 여러 개의 `<form>`이 있을 경우 폼의 이름을 지정하여 구분하기 위한 목적으로 사용된다.


```
.header__column
   form(action=routes.search, method="get")
     input(type="text", placeholder="Search by term..", name="term")
```

이렇게 하면 search bar에서 검색어를 쓰고 엔터를 쳤을때 `http://localhost:4000/search?term=romi` 이 url로 넘어가는게 가능하다.


### method post와 get의 간단하지만 중요한 차이점

`method="get"` : url 에 모든정보가 보인다.

`method="post"` : url 에 정보가 보이지 않는다.

그러므로, 비밀로 유지해야할 필요가 있는 정보, 서버에 보내야 하는 정보들은 post인지 아닌지 항상 더블체크를 해야한다.