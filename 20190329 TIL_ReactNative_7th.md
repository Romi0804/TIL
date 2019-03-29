# 20190329 TIL
## React Native 로 To do list App 만들기 (5th)

디스크에서 Todo를 로딩해야돼.

누군가 Todo를 추가할때마다 디스크에 저장을 해야하니까.

또한, 누군가 앱을 열면 Todo에서 저장된 리스트를 가져와야해.

그러한 장치를 마련해주고.. 

expo에서 Apploading을 불러온다.

--
### AppLoading from expo

A React component that tells Expo to keep the app loading screen open if it is the first and only component rendered in your app. Unless `autoHideSplash` prop is set to `false` the loading screen will disappear and your app will be visible when the component is removed.


This is incredibly useful to let you download and cache fonts, logo and icon images and other assets that you want to be sure the user has on their device for an optimal experience before rendering they start using the app.

--

list 를 저장할때는 Object를 생성하면 되겠지?!
순서는 원하는 Object를 생성하고, list 끝에 todo를 생성한 다음, 리스트를 추가.

- 객체 생성시 ID 생성방법

npm install uuid --save

`import uuidv1 from "uuid/v1"`

이걸로 ID 생성이 가능하다.