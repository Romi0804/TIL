# 20190310 TIL

## React Native로 날씨앱 만들기 2

Javascript의 Navigator에서 위치정보를 얻을 수 있다.
```
navigator.geolocation.getCurrentPosition(function(position) {
console.log(position)
})
```
getCurrentPosition은 성공적인 수행을 위해서 한개의 function작업이 필요해.
그 function은 한개의 attribute가 있는데, 이는 그 안에 우리의 위치정보를 가지고 있다.

- 그래서 우리는 loading indicator가 뜰때마다, position, location info를 확인할거야.
- 위치정보 => 날씨정보 => is loaded 가 true가 되는거지.

```
  componentDidMount() {
    navigator.geolocation.getCurrentPosition(position => {
      console.log(position);
    });
  }
```
```
componentDidMount() {
    navigator.geolocation.getCurrentPosition(
      position => {
        this.setState({
          isLoaded: true
        });
      },
      error => {
        console.log(error);
      }
    );
  }
```
  
 이렇게 해서 위치정보를 얻는다.
 
 - Openweathermap이라는 곳에서 무료로 api를 불러올수 있다.

```
  _getWeather = (lat, lon) => {
    fetch(
      `http://api.openweathermap.org/data/2.5/weather?lat=${lat}&lon=${lon}&APPID=${API_KEY}`
    )
      .then(response => response.json())
      .then(json => {
        this.setState({
          temparature: json.main.temp,
          name: json.weather[0].main,
          isLoaded: true
        });
      });
  };
```

이런식으로 불러온 데이터를 json 파일로 변경해줄것.
 
- API를 불러왔다면 Refactoring(코드의 구조변경)을 해줘야한다.

```
temp={Math.floor(temparature - 273.15)}
```
위의 식은 온도의 farenheit => celcius 로 바뀌어주는 식.