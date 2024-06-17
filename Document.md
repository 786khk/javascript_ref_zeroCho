# Document
- 윈도우 객체 속성
- `window.document`로 써야겠지만 안써도 윈도우(`window`) 키워드는 생략 가능
- html에 관한것들 담당, 태그 선택 및 조작


## 선택자
- getElementById("선택하는 아이디"),document.getElementsByClassName(클래스), document.getElementsByName(이름), document.getElementsByTagName(태그) 가 있음
- 선택하는 Id(또는 클래스, 태그이름, 이름)를 입력해 dom에 접근

## CSS 선택자
- document.querySelector(선택자), document.querySelectorAll(선택자)
- css로 선택 
- 아이디 : `#`, 클래스 : `.` 로 선택 `태그명[속성명 = 속샹값]`로 선택 
- 부모 > 자식, 부모 자손 등 css선택자는 거의 다 쓸 수 있음

## document.createElement(태그명)
- document에 새로운 태그 생성할 때 쓰임 
- 바로 생기지 않고 변수를 통해 메모리에 저장


## document.createTextNode(텍스트)
- 택스트도 하나의 요소이므로 텍스트를 따로 만들 수 있음.
- Node는 태그와 텍스트를 다르키는 명칭. 바로 생성이 안되고 변수에 담아 메모리에 저장됨


## document.createDocumentFragment()
- 가짜 document를 만든다. JS로 document의 캐그를 조작하는 것은 성능이 떨어짐
- 반복문 같이 여로 노드를 동시에(한번에) 추가하거나 이동할 때 미리 가짜 document 를 만들어 여기에 추가를 한 후 한번에 document에 추가 
- document를 한번만 조작해서 요러번 반복할 필요 없음

##### ❓그렇다면 vue, react와 같은 JS 프레임워크도 빌드될 때 document.createDocumentFragment()로 가상 DOM에 사용하는가?

###### document.createDocumentFragment()
- 메모리 내 경량 컨테이너
- 실제DOM 조작을 수행하기 전 사용(실제 DOM과 연관이 있다)

###### 가상 DOM
- 메모리 내 가벼운 JS 객체로 실제 DOM의 트리구조 모방
- 상태변화가 일어나면 가상 DOM이 업데이트, 이와 실제 차이를 계산해 최소한의 실제DOM실행
- 자체적으로 제공하는 가상DOM 알고리즘과 데이터 구조 사용

