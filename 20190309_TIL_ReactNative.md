# 20190309 TIL

## React Native 로 날씨앱 만들기 


- React Native는 Native web application을 빌드하게 해주는 UI 라이브러리
- React Native는 HTML, CSS 어플리케이션을 생성하지 않는다
- objective-c 는 ios를, java는 Android를 위한것.
- 마지막 compiling 할때, 각각 ios(objective-c), Android(java) 의 Native code로 실행됨.
- React Native는 어떻게 구동이 될까?
우리가 JSX, Javascript로 작성하고 그 뒤에서 Javascript가 objective-c, java로 변환되는것. React Native란 기술을 이용해서 js-objective-c 의 bridge, js-java가 연결되는 것.
- 웹에서 div, span 이 있는것 처럼 React Native에는 view, text 같은 페이스북 에서 만든 다른 요소들이 존재하고 이 요소들은 모두 네이티브 코드로 변환된다.
- React Native의 장점중 하나는 

첫째, Javascript를 활용할수 있다는 것.

둘째, 커뮤니티가 엄청 크다는 것.

셋째, 많은 회사가 React Native 를 쓴다는 것.

- 최고의 장점은 ios-Android 앱 사이 코드를 공유할수 있다.
  그래서 약간의 수정만 하면 ios/Android 둘다 쓸수 있어
  
- Expo는 React Native로 앱을 만드는것을 도와준다.(xcode,android studio 사용할 필요없이)
- android studio를 위한 시뮬레이터를 관리해주고, 그리고 xcode 사용할 필요없이 ios를 위한 시뮬레이터를 관리해준다.
- expo가 없을때는 React Native로 xcode, android studio작업을 별도로 해야했어.
 이제는 expo를 통해 ios/android전용 네이티브 앱을 만들수 있고, 앱테스트를 엄청 빠르게 할수 있게 됐어
 그리고 앱을 이미 배포했을때 code push 라는 기능을 이용해서 업데이트를 할수 있고 review process 등 관리자에게 유리한 기능들이 많다.
  
 --
 
 ### Weather App 만들기
 
 - 우리가 return 할수 있는 component가 정해져있다.
 - 리액트 네이티브의 컴포넌트는 모바일 환경에 따라 네이티브하게 변화해 그래서 View 컴포넌트는 이용하면 ios/ android 환경에 따라 objective-c 혹은 java로 변한다.
 - React Native는 이론자체는 동일하지만 웹과는 전혀다르다.
 - React Native는 오류에 엄격하다.

```
import React from "react";
import { StyleSheet, Text, View, ActivityIndicator } from "react-native";

export default class App extends React.Component {
  render() {
    return (
      <View style={styles.container}>
        <View style={styles.redView} />
        <View style={styles.yellowView} />
      </View>
    );
  }
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: "#fff"
  },
  redView: {
    flex: 1,
    backgroundColor: "red"
  },
  yellowView: {
    flex: 1,
    backgroundColor: "yellow"
  }
});
```
React Native는 flexbox를 사용한다.
redView 안에 flex:1, yellowView안에 flex:1 이 있지.
비율은 1:1
각 컨테이너가 다른 컨테이너에 비례하여 최대한 공간을 차지 한다는 뜻이야.
그래서 보통 많이쓰는 모바일 레이아웃을 만든다면 yelloView 의 flex: 6 으로 조정한다면 redView부분을 네비게이션 바로 쓸수 있다.
그래서 스크린전체를 어떤 비율로 사용할지 결정할 수 있다.

- React Native에서 flex direction default는 column이야. 이부분을 생각하면서 flexbox 설정을 해나가면 돼
- React Native로 style flex 먹일때 작성법은 camelCase로 쓴다. 이때 모든 Value는 String 이어야해.
(css 표기법이 아닌 자바스크립트처럼 써야한다는것이지)

--

- React Native로 App을 만들때에는 항상 local state로 작업해야해
- React Native에서는 Shorthand property를 사용하지 않아. 예를들어, padding: 20 30 40 50 이런거
  