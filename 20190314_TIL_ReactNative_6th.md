# 20190314 TIL

## React Native 로 To do list App 만들기 (4th)

Editing 가능하게 하기.

```
 <TextInput
              style={[
                styles.input,
                styles.text,
                isCompleted ? styles.completedText : styles.uncompletedText
              ]}
              value={toDoValue}
              multiline={true}
              onChangeText={this._controlInput}
              returnKeyType={"done"}
              onBlur={this._finishEditing}
            />
            
```


뭔가를 쓰다가 Blur를 하면, 즉 칸밖을 클릭하면 편집종료.
