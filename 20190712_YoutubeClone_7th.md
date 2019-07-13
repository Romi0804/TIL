#20190712 Youtube Clone_7th

## async await, try catch

model은 element를 받는 통로이지 element자체는 아니다.

Javascript는 절대 기다리지 않는다.

`async`는 'Javascript야 이 function의 어떤부분은 꼭 기다려야해' 라고 알려주는 것과 같다.
`await`는 다음과정이 끝날때까지 잠시 기다려달라는 얘기.

* async 없이 await 키워드를 쓸수없다. 

이렇게 하면 await 부분이 끝나기전까지는 render부분을 실행하지 않을 것이라는 것을 확실히 보여준다. 여기서, 해당과정이 성공적으로 끝나야 하는 것은 아니야 그냥 끝날때까지 기다리는거지.

그래서 이것보다 더 좋은 방법이 있다. 모든 error를 다 잡아주는것.

#### `try` and `catch`

`try` 는 우리가 해야 할것들이고, 

만약 실패한다면 `catch`가 해당 error를 잡아 낼거야. 그러면 우리는 무슨 error인지 볼수 있어.

근데 이때 `catch` 는 default로 error를 잡아내지 못해.
이건 NodeJS의 문제인데, 