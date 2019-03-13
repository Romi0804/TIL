# 20190313 TIL

## React Native 로 To do list 만들기 (3rd)

우리의 To do list App 은 두개의 state가 있다.
하나는 수정할때, 나머지는 수정을 하지 않을때 (그냥 보여줄때)

그래서 2개의 state를 만들고 그 사이를 이동시킬것이다.

- ScrollView props 

`contentContainerStyle`

These styles will be applied to the scroll view content container which wraps all of the child views. 

--
 
 `touchableOpacity`를 이용하여 Radio Button을 만들었다.

- `touchableOpacity` : A wrapper for making views respond properly to touches.
 
 ```
   _toggleComplete = () => {
    this.setState(prevState => {
      return {
        isCompleted: !prevState.isCompleted
      };
    });
```

위와 같이 Logic을 만들어서 get previous state 해주고 완성의 반대 (!)를 previousstate에 주는거당.

- 그렇게 해서 border 색깔 변경해주는 logic 만들어 주고 Text complete 시에도 색깔 변경해주고 `textDecorationLine`이용해서 "line-through"로 complete된 스타일링 해준다.

또한 Toggle function 들을 만들었는데 

```
{isEditing ? (
          <View style={styles.actions}>
            <TouchableOpacity onPressOut={this._finishEditing}>
              <View style={styles.actionContainer}>
                <Text style={styles.actionText}>✔️</Text>
              </View>
            </TouchableOpacity>
          </View>
        ) : (
          <View style={styles.actions}>
            <TouchableOpacity onPressOut={this._startEditing}>
              <View style={styles.actionContainer}>
                <Text style={styles.actionText}>🖋</Text>
              </View>
            </TouchableOpacity>
            <TouchableOpacity>
              <View style={styles.actionContainer}>
                <Text style={styles.actionText}>✖️</Text>
              </View>
            </TouchableOpacity>
          </View>
        )}
        
```

이렇게 Ternary function 으로 만들어줌. 
