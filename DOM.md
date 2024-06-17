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

