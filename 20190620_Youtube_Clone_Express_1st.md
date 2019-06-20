# 20190620 Youtube Clone

### Backend 과정 (Using Express)

express 설치완료.

```
// node_modules 에서 express를 불러온다
const express = require("express");

// app인 변수에 불러온 express를 실행시킨다
const app = express();

//4000포트를 연결해라. localhost:4000 으로 연결됨
app.listen(4000)

```

package.json을 중앙컨트롤 타워로 사용할거다.

- Frontend 작업을 할때 localhost로 작업내용을 보기위해서는 항상   terminal 에 npm start 를 입력하면 볼수 있었다.

이 작업은 `node index.js` 를 입력할때와 동일한 방법이며, `npm start`를 눌렀을때 실행할 수 있는 방법은 

package.json으로 들어가 "script" 를 만든다.

```
"script" : {
"start" : "node index.js"
}
```
이렇게 설정해두면 `npm start`로 localhost 실행이 가능하다.
 
`GET` : 정보를 가져오는거
`POST` : 정보를 웹사이트에 보내는것 

#### Babel

babel preset-env
babel core
babel lrc


#### nodemon

`npm install nodemon -D`

nodemon을 설치하면 코드쓰고 저장하기만 하면 자동실행된다. 와우 ! 
package.json에서, 프로젝트에 필요한 dependencies 는 dependencies에 저장되지만 프로그래머의 편의를 위한 것은 devdependencies에 저장된다. 그래서 nodemon install 시, 뒤에 -D를 붙여주면 ㅇevdependencies로 가는거다.

### Express Middleware

Express는 자체적인 최소한의 기능을 갖춘 라우팅 및 미들웨어 웹 프레임워크이며, Express 애플리케이션은 기본적으로 일련의 미들웨어 함수 호출입니다.

미들웨어 함수는 요청 오브젝트(req), 응답 오브젝트 (res), 그리고 애플리케이션의 요청-응답 주기 중 그 다음의 미들웨어 함수 대한 액세스 권한을 갖는 함수입니다. 그 다음의 미들웨어 함수는 일반적으로 next라는 이름의 변수로 표시됩니다.

미들웨어 함수는 다음과 같은 태스크를 수행할 수 있습니다.

- 모든 코드를 실행.
- 요청 및 응답 오브젝트에 대한 변경을 실행.
- 요청-응답 주기를 종료.
- 스택 내의 그 다음 미들웨어 함수를 호출.

현재의 미들웨어 함수가 요청-응답 주기를 종료하지 않는 경우에는 next()를 호출하여 그 다음 미들웨어 함수에 제어를 전달해야 합니다. 그렇지 않으면 해당 요청은 정지된 채로 방치됩니다.

---

그러니까 쉽게 말하면, 사용자의 요청과 사이트에서 응답을 해주는 과정 속에서 연결흐름이 우리가 생각하는 것처럼 간단하게 되는것이 아니야. 보통 유저의 요청과 사이트의 마지막 응답 사이에 무언가가 있게 되고 그걸 미들웨어라고 한다.

---

미들웨어가 있어주면 편안할수 있는데,

유저의 로그인 여부를 체크할수 있고, 파일을 전송할때 중간에 가로챌수도 있다. 활동로그를 작성하는 미들웨어도 가질수 있고, 모든 접속에 대한 로그를 얻고 싶다면 미들웨어를 이용하면 된다.

전역으로 미들웨어를 설정해주고 싶다면, 
`app.use(between Home)` 이런식으로 써준다. 위치를 잘 선정해서! 위치 굉장히중요해 !

```
const betweenHome = (req, res, next) => {
  console.log("Between Home");
  next();
};

app.use(betweenHome);

app.get("/", betweenHome, handleHome);
app.get("/profile", handleProfile);

```
위의 코드처럼 쓸수 있다.

예를들어, IP주소를 체크하는 미들웨어가 있다면, 거부할 IP주소를 찾아 접속을 취소할수 있다.

가끔은 미들웨어가 접속을 끊을때가 있는데, 

```
const betweenNotHappening = (req, res, next) => {
   res.send("Not happening")
   }
   
app.get("/", betweenNotHappening, handleHome);

```
위의 코드처럼 next가 아닌 res.send를 쓰면 중간에 접속을 끊을수도 있다.


---

### morgan

멋진 미들웨어인데 logging 에 도움을 주는거다.

즉, 무슨일이 언제 어떻게 일어나는지 다 기록해서 보여주는거 ! 

```
import morgan from "morgan";

app.use(morgan("tiny"));
app.use(morgan("combined"));
```
이런식으로 써주면.. 로깅기능을 가질수 있다.

---

### Helmet

Node.js의 보안에 도움을 주는것이다.

---

### cookie parser and body parser

기본적으로 누군가 나에게 form 을 채워서 전송한다면, 이 form 은 서버에 의해서받아져야한다.
만약 내가 아이디와 비밀번호를 작성해서 보내면, 특정한 형태로 서버에 의해 받아져야 한다.

###cookie parser

session 을 다루기 위해, cookie에 유저정보를 저장할거야. 그럴때 이용.

이것이 서버가 유저로부터 받은 cookie를 이해하는 방법이다.


### body parser

Form을 받았을때, 그 데이터를 갖고 있는 request object에 접근할수 있길 바랄때 이용한다.

body로 부터 정보를 얻을수 있게 도와주는거야.

body-parser에는 우리가 정의해야할 옵션이 있는데, 그중 json이란 옵션이 있고, text도 이해해야하고, urlencoded 등등 이해해야할것들이 많다. 왜냐면 우리 서버가 우리가 무엇을 전송하는지 알수 있어야 하기 때문에.

이것이 서버가 유저로 부터 받은 데이터를 이해하는 방법이다.


 