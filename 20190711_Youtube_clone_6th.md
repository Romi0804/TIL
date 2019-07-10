#20190711 Youtube clone_6th

## Mongo DB

Mongo DB 는 No SQL로 분류된다.
많은 Database종류들이 있는데 크게 SQL과 No SQL로 나뉜다.
Mongo DB는 더 적은 규칠과 절차로 작업이 가능한 데이터베이스이다.
사용하기 쉬우며, 직관적으로 작동한다.

이제 Mongo를 Javascript와 연결해야하는데, 하나는 MongoDB이고, 하나는 Javascript의 Node JS이다.
Javascript에서 MongoDB를 이용하려면 Adapter를 통해야한다.
Javascript코드를 작성하고 싶으면, MongoDB로 부터 Instruction을 받아야한다.
이럴때 Mongoose를 이용하는데, MongooseJS 는 NodeJS를 위한 Object Modeling이다.
Database를 가지고 이용하려면, MongoDB, Mongoose둘다 있어야해.

MongoDB의 장점은 document를 줄여준다는 것이다. JSON file !!

## dotenv

어떤부분을 숨기고 싶을때, 이용한다

`npm install dotenv`


## Data Models
해야할것중 하나는 model 즉, document name 이고 다른 하나는 Schema 이다. Schema는 형태(shape)이야.
model은 그냥 실제 data 이고, 그런식으로 이해하면 돼 

이 프로젝트에서 절대 Video를 Database에 저장하지 않을거다.
bytes를 저장하는 것이 아니라 Video의 link를 집어 넣는 것.
우리의 경우, 우리 서버 (Amazon)에 Video를 저장하는 거지.
Database에 Video를 저장하지 않아. model file 안에 저장하는 건 단지, text database이다. Video 전체를 넣는 것이 아닌 video의 주소를 넣는거지. Database 를 가볍게 하지 위해서.

#### Data relationship

한쪽에서 Video를 생성하고 다른쪽에서 Comment를 생성했을때, 둘을 어떻게 연관시킬것인가 ? 그것이 문제다. 둘사이에 어떠한 관계가 있는데 그것을 어떻게 연결시킬 것인가?

Comment에 Video의 ID 를 저장하거나, Video가 ID의 array를 가지고 있는거지.

Video comment를 달때, 어떤게 어떤것과 연관되어 있는지 인지해야한다. 이 Comment가 어떤 Video에 직접적으로 연결되어 있는지.

- 두가지 선택이 있다.

1. 모든 comment id 들을 array로 Video에 집어 넣을 것인가(우리가 선택한 방법)

2. Comment에 연결된 Video ID를 줄것인가.




