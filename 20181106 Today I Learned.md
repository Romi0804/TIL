# 20181106 Today I Learned

## fds-mid-todo

#### 우리는 지금 이 Practice에서 하나만 변화해도 화면을 모두 다시 그리는 방법으로 코드를 짜고 있다.
- 이 방법은 개발자는 Good, 기계는 Bad.

필요한 부분만 갱신하는 방법으로 코드를 짜면 개발자는 죽어나지만 기계에겐 좋다.

#### React가 좋은 이유가 개발자에겐 화면을 모두 다시 그리는 코드를 짜게 되어 좋지만 기계 입장에서는 필요한 부분만 갱신하여 기계에게도 좋다 !


1. 비관적 업데이트 (Pessimistic update)
사용자 입력 => 수정요청 => 성공시 화면 갱신


2. 낙관적 업데이트 (Optimistic update)
사용자 입력 => 화면갱신 => 수정요청
이때에 수정요청이 성공했을때와 실패 했을때의 경우를 다 생각해야한다.
여기서 수정요청이 실패하면 화면 갱신 한걸 취소해주어야해. 원상복구를 해줘야하는거지. 근데 이 원상복구를 하는것이 아주 고난이도의 작업이다. 사용자는 편하지만 프로그래머에겐 굉장히 고난이도의 작업. 까다로와 ㅜㅜ 
사용자의 편의를 위해..


로딩인디케이터 (Loading Indicator)
- 로딩할때 기다리라고 표시해주는거.

비동기 함수도 promise를 반환합니다.

## 게시판만들기

##### Parcel에서 환경변수 사용하기


##### json-Server에 내장된 여러기능
### Routes

Based on the previous db.json file, here are all the default routes. You can also add other routes using --routes.


Plural routes

```
GET    /posts
GET    /posts/1
POST   /posts
PUT    /posts/1
PATCH  /posts/1
DELETE /posts/1
```
REST API 표준을 따르고 있다

##### Filter
Use `.` to access deep properties

```
GET /posts?title=json-server&author=typicode 
// 타이틀 필터링 해서 가져오기
GET /posts?id=1&id=2 //사용자 아이디 걸러서 가져오기
GET /posts?userid=1 //1번 사용자만 가져오기
GET /comments?author.name=typicode 
//이건 객체안에 객체가 들어있을땐데... 무시해도돼 일단은
```

##### Paginate

Use `_page` and optionally `_limit` to paginate returned data.

In the `Link` header you'll get `first`, `prev`, `next` and `last` links.

```
GET /posts?_page=7
GET /posts?_page=7&_limit=20 
//limit 20 은 7개 페이지에 나올 개수
```
10 items are returned by default

##### Sort
Add `_sort` and `_order` (ascending order by default)

```
GET /posts?_sort=views&_order=asc
//조회수 오름차순 정렬을 해서 가져오겠다.
GET /posts/1/comments?_sort=votes&_order=asc
```

For multiple fields, use the following format:

```
GET /posts?_sort=user,views&_order=desc,asc
//유저기준으로 내림차순, 조회수 기준으로 오름차순
```

```
 https://fds-json-server-bbs.glitch.me/posts?_sort=id&_order=desc
  => 최신글부터 보여주고 싶다.
```

##### Operators
Add `_gte` or `_lte` for getting a range

-> greater than or equal

-> less than or equal

```
GET /posts?views_gte=10&views_lte=20
```

Add `_ne` to exclude a value

```
GET /posts?id_ne=1
```

Add `_like` to filter (RegExp supported)

```
GET /posts?title_like=server
//타이틀 속성에 server라는 단어가 포함되어 있는지
```

##### Full-text search

Add `q`

```
GET /posts?q=internet
//어떤 속성이든 internet 이라는 단어가 포함되어 있으면 
// 뭐든 다 나타내어라 !
```
=>엄청 넓은 범위의 검색을 할때 

##### Relationships
To include children resources, add _embed

=>게시물이랑 댓글까지 다 볼수 있어용

```
GET /posts?_embed=comments
GET /posts/1?_embed=comments
//1번 게시물의 게시물과 댓글까지 가져온다
```
To include parent resource, add _expand

```
GET /comments?_expand=post
GET /comments/1?_expand=post
//게시물, 작성자 정보까지 모두 확인 가능
```

To get or create nested resources (by default one level, add custom routes for more)

=>댓글을 생성할땐 아래와 같이 생성하면 됩니다용

```
GET  /posts/1/comments
POST /posts/1/comments
//1번 게시물의 자식이 되는 코멘트를 만들것이다.
```


#### URLSearchParams

querystring을 사용하기 위해 만들어 졌엉 !
같은 이름의 params를 써야할때는 URLSearchParams를 쓴다.

Axios는 이 기능을 잘 이해항수 있다. 

control D => 같은 단어 선택
shift option 아래방향키 => 줄복사
