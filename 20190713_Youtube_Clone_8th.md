# 20190713 Youtube Clone_8th

## Upload

업로드 할때, Video 가 아닌 다른 파일이 업로드 되는 것을 원하지 않으며, File을 업로드하면 middleware에서 일단 받는다.
그리고, 그 ! middleware에서 파일을 업로드 하고 URL을 복사해서 Database에 저장하는 방식으로 만들 것이다.

그래서 Video가 아닌 파일이 들어오지 않게 보호를 해야한다.

View 폴더에 있는 upload.pug 로 가면, 
file올릴수 있는 코드 

```

input(type="file", id="file", name="file", required=true )

```

에서 accept="video/*"를 추가하여

```
input(type="file", id="file", name="file", required=true, accept="video/*")

```
이렇게 넣어주면 파일 추가시 video 파일이 아닌 파일들은 비활성화 상태로 나타내어 진다.

그리고, 파일을 업로드하고 URL을 반환하는 middleware가 있어야한다.
이런 middleware를 `multer`라고 한다.

Multer는 파일 업로드를 위해 사용되는 multipart/form-data 를 다루기 위한 node.js 의 미들웨어 입니다. 효율성을 최대화 하기 위해 busboy 를 기반으로 하고 있습니다.

주: Multer는 multipart (multipart/form-data)가 아닌 폼에서는 동작하지 않습니다.

```
form(action=`/videos${routes.upload}`, method="post", enctype="multipart/form-data")
```
위와 같이, Multer를 이용하기 위해서는 form에 `enctype="multipart/form-data"`를 써줘야한다.
왜냐하면 우리는 업로딩시, 파일을 보내게 될때, form 의 encoding이 달라야 하기 때문이다.

* 구글에서 Multer라고 검색해볼것. 해당 github page를 확인할수 있다.

### MongoDB에서 Database 수정하기

Terminal에서 `mongo`치고 mongo comments를 가지고 어떻게 database를 수정할수 있는지 알아볼거다.

- `mongo` : mongo 시작
- `help` : 입력어 메뉴얼을 볼수 있음
- `use utube` : 어떤 파일을 이용할건지.
- `show collections` : model을 보여달라.
- `db.video.remove({})` : 데이터베이스에 있는 비디오 파일 다 지워라.
- `exit` : 나가라

 


