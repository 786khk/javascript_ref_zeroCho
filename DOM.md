# DOM
- Document Object Model
- document를 객체로 구현
``` 
# html 기본 구조
html
-head
--title
--meta
--link
-body // body안에 직접적으로 html css등이 동작
--header#header
---nav
---div
--main
--footer
---"hello"
--script // script 는 아래 두는것을 지향한다. 페이지가 읽힐 때 읽고 스크립트를 실행해야하기때문


```


## Node, Element
- Node는 태그 노드와 텍스트 노드 전체를 가리킴
- Element는 텍스트 노드를 제외하고 흔히 생각하는 태그만 가리킴

## 속성
### 태그.nodeType
- 일단 태그를 선택한 후 nodeType속성을 검색하면 태그의 종류를 알려주는 숫자가 나옴
  - 1 : noce.ELEMENT_NODE -> Element
  - 3 : Node.TEXT_NODE -> 텍스트
  - 8 : Node.COMMENT_NODE -> 주석 
  - 9 : Node.DOCUMENT_NODE -> Document
  - 10 : Node.DOCUMENT_TYPE_NODE -> DOCTYPE 
  - 11 : Node.DOCUMENT_FRAGMENT_NODE -> Document Fragment
 
  - ![image](https://github.com/786khk/javascript_ref_zeroCho/assets/78067072/615cf0f5-c668-4cd0-9c84-eb0200c87abc)
 
  - ![image](https://github.com/786khk/javascript_ref_zeroCho/assets/78067072/1668c553-653e-4604-9074-aeb311edbd57)

  - 중간에 비어있는 번호는 더이상 쓰지않음
  - Node.[ELEMENT_NODE]  이런식으로 해도 같은 번호 가 나옴

### 태그.children, 태그.childNodes
- 자식으로 갈 때 사용
- Dom의 속성들은 모든 태그에 사용가능
- 사용 방법 : `document.getElementById('myId').children` 
- 꼭 굳이 사용방법처럼 쓰는 이유는 산번에 선택할 때 선택자 메서드가 편하지만 선택된 태그의 부모나 자식을 선택할 때 선택자를 모르기때문
### 태그.firstChild, 태그.firstElementChild, 태그.lastChild, 태그.lastElementChild
- 첫번째 자식만 선택 또는 마지막 자식만 선택할 때 사영
- fist~ last~같은 역할을 하지만 element속성이므로 텍스트 노드는 무시

![image](https://github.com/786khk/javascript_ref_zeroCho/assets/78067072/5572c549-ca2e-4b8b-a26f-3df7c817d8b6)
![image](https://github.com/786khk/javascript_ref_zeroCho/assets/78067072/48383635-57f1-4a45-be7c-f7e72b6cb249)

### 태그.parentNode, 태그.parentElement
- 부모를 찾을 때 parentNode속성을 사용
- 자식은 childrens지만 부모는 한명이기에 parnet단수로 사용
### 태그.previousSibling, 태그.nextSibling, 태그.previousElementSibling, 태그.nextElementSibling
- 형제, 자매 노드 찾을 때 사용
- ~ Sibilling 은 텍스트 노드 무시
![image](https://github.com/786khk/javascript_ref_zeroCho/assets/78067072/444b08af-9e32-4213-b5e7-435604a346cd)

### 태그.innerHTML, 태그.outerHTMLF
- 선택한 태그의 내용을 얻어오거나 바꿀 수 있음
```javascript

var footer = document.getElementsByTagName('footer')[0];
footer.innerHTML; // 'hello'
footer.innerHTML = 'goodbye';

```
![image](https://github.com/786khk/javascript_ref_zeroCho/assets/78067072/07fdb862-549a-4d18-a6d1-0bc42219ba16)
![image](https://github.com/786khk/javascript_ref_zeroCho/assets/78067072/600d3334-d628-437a-932a-1106212c62d6)


### 속성
- 선택자로 태그를 선택하고 속성을 조회, 수정할 수 있음.
- `id, className, name, value, placeHolder, checked, disabled, readonly` ...


#### 태그.attributes
- 해당 태그가 가진 모든 속성을 보고싶다면 attributes 속성을 사용

![image](https://github.com/786khk/javascript_ref_zeroCho/assets/78067072/5c8d47fc-ca7e-4161-8e01-123763aba185)

#### 태그.scrollHeight, 태그.scrollWidth
- 스크롤이 가능한 범위까지 포함한 태그 높이와 너비 반환
#### 태그.offsetHeight, 태그.offsetWidth
- 태그의 마진(margin)만 제외한 높이와 너비 반환
#### 태그.clientHeight, 태그.clientWidth
- 태그의 margin, border, scrollbar 를 제외한 높이 반환
![image](https://github.com/786khk/javascript_ref_zeroCho/assets/78067072/d7302c70-0eba-452e-abc5-9887f12fac0b)


### 메서드
#### 태그.appendChild
- 마시막 순서의 자식으로 태그 추가
![image](https://github.com/786khk/javascript_ref_zeroCho/assets/78067072/02802836-94e7-470b-8dac-44b0135b4ebf)
![image](https://github.com/786khk/javascript_ref_zeroCho/assets/78067072/8e0b4fd7-db72-4320-830d-d331f5526c1a)
![image](https://github.com/786khk/javascript_ref_zeroCho/assets/78067072/aaa1edad-3e01-4f13-9ae9-18622701d6ee)


#### 태그.removeChild
- 선택한 자식 태그 삭제
![image](https://github.com/786khk/javascript_ref_zeroCho/assets/78067072/1c6751c1-ca69-4e74-b2f4-226cac1fc6ae)


#### 태그.insertBefore
- appendChild가 마지막 차식을 추가하는것이라면 insertBefore는 마지막 형제를 추가
- `document.getElementById("myId").insertBefore(넣을 태그, 기준태그)`로 사용

- ![image](https://github.com/786khk/javascript_ref_zeroCho/assets/78067072/bc237fe1-2837-4bd5-81a7-4bee5917ab5b)

#### 태그.cloneNode
- 자신을 복제(복사) 복사한 것을 저장해 appendChild나 insertBefore로 넣을 수 있음
