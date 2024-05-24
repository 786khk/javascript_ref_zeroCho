# 숫자
- 원시 래퍼 객체 `new Number()` 가 있음
```javascript

var a = 0.1;
var b = 0.3;
a+b // 0.4
var a = 0.1;
var b = 0.2;
a+b //  0.30000000000000004

```
- 프로그래밍 언어에서 IEEE 754 표준에 따라 컴퓨터는 소수를 2진법으로 바꿔서 계산, 2진법으로 바꾸면 소수는 무한 소수가 됨
- 저장공간이 정해져 있는 컴퓨터는 값을 다 저장하지 못하고 끝부분을 버려 유한소수로 만들어 버려 오차 발생
## toFixed(소숫자리수), toPrecision(자리수)
- toFixed는 소숫자리수까지 반올림해 문자열로 반환.
- toPrecision는 지정된 자릴수만큼 표현해 문자열반환. 소수의 경우 앞 0을 무시, 자릿수는 제로베이스
- 숫자로 사용하려면 parseInt 나 parseFloat을 사용해 형변환필요

```javascript

0.00125.toPrecision(2) //'0.0013'
0.00125.toPrecision(5) //'0.0012500'

```

## isNaN(숫자)
- 파라미터로 받는 숫자가 진짜 숫자인지 테스트
- 숫자가 아닌 값에 대해 true/false로 결과 반환
- NaN도 하나의 숫자값. 버그가있는 함수여서 지양

## Infinity
- 0으로 나누었을 경우 Infinity값이 나옴. 무한의 수를 뜻함. 음수의 무한은 -Infinity

## parseInt(숫자, 진법), parseFloat(숫자)
- parseInt는 정수로, parseFloat는 실수로 형변환
## Number() 
- Number자체가 객체로 쓰일 수 있음
- parseFloat과 parseInt와 다른점은 문자열에 문자가 들어있으면 처리하지 못하고 NaN 반환
- 숫자는 2진법, 8진법, 16진법 표시가능 2진법은 숫자 앞에 0b를, 8진법은 0을, 16진법은 0x을 붙임

# Math
- 각종 수학계산
- 원시 객체 래퍼가 아니기 때문에 Math() 를 사용할 수 없어 Math.함수이름()으로 사용해야 함
```javascript
Math.random(); // 0~1 까지 랜덤값 
Math.max(5, 6, 10); // 10 // 파라미미터에 있는 값들 중 최대값
Math.min(2, 8, 9); // 2 // 파라미터의 값들 중 최소값
Math.floor(5.5); // 5 // 정수값으로 내림
Math.ceil(5.5); // 6// 정수값으로 올림
Math.round(5.5); // 6 // 정수값으로 반올림 
Math.round(5.49); // 5 // 정수값으로 반내림
Math.abs(-15); // 15 // 절대값
Math.pow(2, 3); // 2*2*2 = 8 //거듭제곱
Math.sqrt(16); // 4 //제곱근
Math.PI // 원주율 구하는 파이

...

```