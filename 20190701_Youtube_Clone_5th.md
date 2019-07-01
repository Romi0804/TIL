# 20190701 Youtube Clone_5th

- 2.21 ~ 2.25 분량

데이터베이스를 만들기 전에 가까 데이터베이스를 만들어 충분히 수정하고 테스트를 한다.

### interation(반복)
반복문은 매우 다양한 방식이 있습니다. 하지만 반복문은 기본적으로 하는일은 같습니다.: 반복문은 한 동작을 몇 회 동안 반복합니다. (사실 0회 반복하는 것도 가능합니다.) 다양한 반복문 메커니즘은 다양한 방법으로 반복문의 시작점과 끝나는 점을 정할 수 있습니다.

이와같이 데이터베이스를 가져와 화면에 보이게 할때, 원하는 것만 보이게 할수 있고 그것을 반복할수 있다

```
extends layouts/main

block content
    .videos
        each item in videos
            h1=item.title
```

이렇게 제목만 보이게 할수 있고, 위에서 밑으로 하나씩 보여준다. 그걸 interation이라고 한다.

모든 요소들이 배열에 있고, pug에서 `each item in videos`통해 iteration을 할수 있다. 저기서 item이라는 변수를 무엇을 정하든 상관없다.
item 혹은 변수는 videos 배열에서 iteration하면서 각 값을 하나씩 가진다.
