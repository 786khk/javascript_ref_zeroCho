# Date
- 날짜 표현


```javascript

let now = new Date();

```
- `now` 에 현재 시간과 날짜가 저장됨

## 날짜.getFullYear(), 날짜.setFullYear(연도)
- 연도를 가져오거나 저장하는 메서드
- 2000년도 이후의 날짜를 표시하기 위해 나온 매서드
- 2000년도 이전의 날짜는 ` 날짜.getYear(), 날짜.setYear(연도)` 로 표시 됐음, 이 함수는 더이상 업데이트를안해 권장되지 않음
❓getFullYear 와 getYear의 리턴값이 다른데 왜 다른건지?
- getYear()은 연도를 가져오는 방식이 다르기때문에 리턴값이 다르다.
- 전체연도를 지원하지 않기때문에 더이상 사용되지않음
- 현재시간에서 날짜의 연도를 나타내는 정수에서 1900을 뺀 값, 날짜가 유효하지 않을경우 NaN 반환
![image](https://github.com/786khk/javascript_ref_zeroCho/assets/78067072/ea503aae-c877-4fe9-8e41-e7a431bb7b13)

## 날짜.getMonth(), 날짜.setMonth(달)
- 달을 알려주거나 저장하는 함수
- 제로베이스여서 현재 달을 원할 때는 +1 을 해야함
## 날짜.getDate(), 날짜.setDate()
- 날짜를 알려주거나 저장
![image](https://github.com/786khk/javascript_ref_zeroCho/assets/78067072/a50b3231-754d-4cbb-8d04-312661a3d1c5)


## 날짜.getDay(), 날짜.setDay()
- 요일 관련 데이터 리턴 
- 일요일부터 토요일까지, 일요일이 첫번째
- 제로베이스

## 날짜.toString(), 날짜.toLocaleString(), 날짜.toUTCString()
- 날짜를 문자로 바꿔 표현
![image](https://github.com/786khk/javascript_ref_zeroCho/assets/78067072/b58a63c3-6b88-43b9-b6f5-0b68e99d59a1)



``` javascript
now.toLocaleString() //'2024. 6. 18. 오전 10:20:45'
now.toLocaleDateString() //'2024. 6. 18.'
now.toUTCString() //'Tue, 18 Jun 2024 01:20:45 GMT'

```