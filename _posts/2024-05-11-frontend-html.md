---
title: HTML이란? - 웹페이지의 뼈대
author: Kim Damin
date: 2024-05-11 00:30:00 +0900
categories: [Front End, HTML]
tags: [HTML]
render_with_liquid: false
---

## HTML 이란?
  
웹 페이지의 구조와 내용을 정의하는 마크업 언어


## HTML(HyperText Markup Language)의 기본 구성

'<!DOCTYPE html>' 문서 버전과 타입 선언
'<html>' 문서 전체를 감싸는 태그
'<head>' 문서의 메타 정보를 담는 태그
'<body>' 실제 사용자에게 보여지는 내용을 담는 태그


## 인라인(inline) 태그와 블록(block) 태그

HTML에서 '<body>'를 구성하는 tag(태그) 중에는 인라인 태그와 블록 태그가 있다.
대표적인 인라인 요소는 span 태그, 블록 요소에는 div 태그가 있는 데, 아래 html 코드에서 둘의 차이를 볼 수 있다.


```html
---
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <!--블록 태그 예시, <div> 태그-->
    <div>안녕하세요.</div>
    <div>반갑습니다.</div>

    <!--인라인 태그 예시, <span> 태그-->
    <span>감사합니다.</span>
    <span>수고하세요.</span>
</body>
</html>
---
```

![Desktop View](assets/img/html/div&span.png){: width="400" height="300" .normal}
<img src="assets/img/html/div&span.png" width="400" height="300"/>
> '<div>' 태그는 다음 줄에 다른 태그로 입력을 하게 되면 다음 줄에 출력이 되고, '<span>' 태그는 다음 줄에 입력을 해도 옆으로 이어지는 특징을 가지고 있다.
{: .prompt-info }


인라인(inline) 태그
: 태그의 내용만큼만 공간을 차지하여 줄 바꿈없이 다음 요소가 배치된다.
인라인 태그 안에 블록 태그를 포함할 수 없다.

블록(block) 태그
: 한 라인의 공간을 차지하여 기본적으로 너비가 100%이다.
블록 태그 안에 인라인 태그와 블록 태그를 포함할 수 있다.


|      inline 태그      |      block 태그      |
| :-------------------  | ------------------:  |
| span 태그             | div 태그             |
| input 태그            | h1 ~ h6 태그         |
| a 태그                | p 태그               |
| 글자 형식 태그         | table 태그           |
| ...                   | ...                  |


### 레이아웃(layout) 태그 - 문서 구조

'<body>'를 구성할 때 '<div>' 태그를 자주 이용하지만 지나치게 이용해서 '<div>' 태그가 계속 깊어지게 되면 어디가 어딘지 파악하기가 굉장히 어렵다. 특히 협업을 할 때, 다른 개발자가 그 코드를 파악해야 하는 경우에는 더욱 그렇다.

그래서 '<div>' 태그 외에 레이아웃 태그를 이용하여 html의 특정 부분이 어떤 의미를 가지고 있는지를 나타낸다.


|         태그          |         의미          |
| :-------------------  | -------------------:  |
| <header>              | 헤더 영역             |
| <main>                | 메인 영역             |
| <section>             | 콘텐츠 영역           |
| <aside>               | 사이드바 영역         |
| <footer>              | 푸터 영역             |


![Desktop View](assets/img/html/layout.png){: width="500" height="300" .w-75 .normal}
