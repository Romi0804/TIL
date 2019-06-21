# 20190621 Youtube clone

### ES6 Javascript modules

자바스크립트에는 모듈이 있어 우리 코드를 공유할수 있으며, 다른 파일의 코드를 가져다가 사용할 수 있다.


```
export default app;
```

이것의 의미는, 누군가 내 파일을 불러올때 (import) 나는 app object를 주겠다는 의미이다.

#### express에서의 Router는 좀더 복잡해 질수 있다.

Router는  Route들의 복잡함을 쪼개주는데 사용할수가 있다.

express사용중, node.js 모듈과 엄청 다른 점이 하나 있는데, 만약 내가 default 로 export 를 하면..
즉, ` export default app` 이렇게 하면, `import app from "./app"` 이런식으로 쓸수 있다.

default가 아닌 export 예를들어...
`export const userRouter = express.Router();`
이런것들은 `import {userRouter} from "./router"`이런식으로 import 됨을 쓸수 있다.

express 에서 `.use` 메소드는 
예를들어,
```
app.use("/user", userRouter)
```
user경로로 접속하였을때, 이 userRouter 라는 Router의 전체를 사용하겠다는 의미이다.

express의 장점은 아주 작은 파일들을 하나로 엮어서 사용가능하다.

## MVC Pattern

Model : Data 

View : how does data look,

Control : 데이터를 보여주는 함수
          function that looks for the data

Pattern 이란 일종의 규격화된 구조 같은것. 

```
//videos
const VIDEOS = "/videos";
const UPLOAD = "/upload";
const VIDEO_DETAIL = "/:id";
const EDIT_VIDEO = "/:id/edit";
const DELETE_VIDEO = "/:id/delete";
```

위의 코드에서 `"/:id"` 라고 하면 값이 변한다는걸 인식한다. 그런데 `"/id"`라고 하면 텍스트로 인식.

###Controller

URL Router를 정리할때, controller를 만들어 관리한다.

대게 프로젝트에 있는 각 모델마다 컨트롤러를 쓰게 된다.

ex) video controller, user controller

컨트롤러는 어떤일이 어떻게 발생하는지에 대한 로직이다.
