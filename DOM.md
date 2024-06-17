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

