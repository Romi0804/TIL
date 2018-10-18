


## 표준편차 (Standard Deviation)



```js

function stdDev(arr){
// arr의 평균구하기
const sum = arr.reduce((acc, item) => acc + item, 0)
const mean = sum / arr.length
console.log(`mean : ${mean}`)
// 각 요소에 대한 편차 구하기 (편차 = 값 - 평균)
const ps = arr.map(item => item - mean)
console.log(`ps : ${ps}`)
// 각 요소에 대해 제곱하기
const powers = ps.map(item => item ** 2)
// 위 제곱한 배열의 평균 구하기
const vv = powers.reduce((acc, item) => acc+item, 0) / powers.length
// 루트 씌우기
return Math.sqrt(vv)
}


stdDev([1,2,3,4,5])
```
