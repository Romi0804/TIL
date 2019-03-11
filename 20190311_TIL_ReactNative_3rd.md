# 20190311 TIL

## React Native로 To do list 만들기

expo 이용해서 기본구조 만들고 React Native로 스타일링 하던중, 

Shadow 넣을때 ios 와 Android의 접근방법이 다르다는 것을 알게 되었다.

즉, Platform Specific Code를 이용해야 한다는 것.

- ios 일때, `shadowColor` `shadowOffset` `shadowOpacity``shadowRadius` 를 이용하여 효과를 줄수 있다.

- Android 일때, `elevation`을 이용한다. 이는 0부터 5까지 있는데 숫자가 커질수록 shadow가 커진다.

이때에는 파일을 두개 만들어 각각 이용하는게 하니다 `Platform select` 이라는 명령어를 사용하여 그때그때 운영체제마다 선택하여 사용되어 질수 있다.

```
...platform.select({
   ios: {
   ...
   },
   android: {
   ...
   }
  })
```

이런식으로..

- 또한, shadowOffset 에서 height 설정시, 위 아래로 움직이는게 싫다면 -1로 설정 , width 또한 0 이상으로 둔다면 계속 움직일거야