# 20190312 TIL

## React Native로 To do list App 만들기 (2nd)

### stylesheet를 이용한 스타일링

어제 TextInput 이용하여 할일을 타이핑하여 쓸수 있게 만들었는데,
이 부분을 보기 좋게 스타일링 하였다.

borderBottom을 꾸미던중 새롭게 배운것이 있는데, 우리는 stylesheet 를 통해 여러가지 꾸미기 기능들을 사용할수 있다는것.

- Properties

hairlineWidth

absoluteFill

absoluteFillObject

위의 기능중 hairlineWidth를 이용하여 
``
borderBottomWidth: StyleSheet.hairlineWidth
``
이렇게 꾸밀수 있었다.

### Value Control

이제 할일을 타이핑 할수 있게 되었으니, value control를 하기 위해 state를 생성하는것이다.

state를 생성해주고, 새로운 function을 생성해준다.

```
 _controlNewToDo = text => {
    this.setState({
      newToDo: text
    });
```

이런식으로 text 임을 말해주고, TextInput에 `onChangeText` event를 넣어준다.

- Simulator 에서 Hardware => keyboard => Toggle software keyboard √ 하면 타이핑을 할수 있는 핸드폰 키보드가 나오는데 "엔터" 역할을 하는 것의 이름을 `returnKeyType`을 이용하여 바꿀수 있다.

```
         <TextInput
            style={styles.input}
            placeholder={"New to do"}
            value={newToDo}
            onChangeText={this._controlNewToDo}
            placeholderTextColor={"#999"}
            returnKeyType={"done"}
            autoCorrect={false}
          />
```
- 그리고 자동수정 끄게 하고 싶다면 `autoCorrect={false}` 처리를 해주면 된다.

ScrollView를 이용하여 특정 높이까지 스크롤이 움직이는 것을 설정하기 위해 모든 자식구성요소를 랩핑 설정한다.

#### ScrollView

Component that wraps platform ScrollView while providing integration with touch locking "responder" system.

Keep in mind that ScrollViews must have a bounded height in order to work, since they contain unbounded-height children into a bounded container (via a scroll interaction). 
