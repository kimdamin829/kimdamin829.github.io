---
title: CSS 선택자와 상태
author: Kim Damin
date: 2024-06-07 05:30:00 +0900
categories: [Frontend, CSS]
tags: [Frontend, CSS]
render_with_liquid: false
---

## 선택자

웹사이트에서 특정 부분을 지정해서 이벤트를 줄 때 선택자가 필요하다. 예를 들어, '세 번째 버튼에 마우스를 올리면 색이 바뀌게 해주세요'라는 요청이 들어왔을 때, 선택자를 이용할 수 있다.

- Element명으로 선택
- Class, ID로 선택
- Pseudo Selector (가상 선택자)

<br/><br/>

## 선택자 지정 방법

```html
---
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        button {
            background-color: coral;
        }
        #btn-3 {
            background-color: yellow;
        }
        .btn {
            background-color: aqua;
        }
        div > button:nth-child(4) {
            background-color: blue;
        }
    </style>
</head>
<body>
    <div>
        <button id="btn-1">1번 버튼</button>
        <button id="btn-2">2번 버튼</button>
        <button id="btn-3">3번 버튼</button>
        <button id="btn-4">4번 버튼</button>
        <button class="btn" id="btn-5">로그인</button>
    </div>
</body>
</html>
---
```
<br/><br/>

<img src="assets/img/css/selector.png" align="left"/>

<br/>

- Element명으로 선택
  - 
- Class, ID로 선택
- Pseudo Selector (가상 선택자)

![Desktop View](assets/img/css/inline&internal&external.png){: width="200" height="150" .w-75 .normal}

> css는 중복이 되면 가장 나중에 작성된 코드가 반영되기 때문에, 위의 코드에서는 inline -> external -> internal 방식 순으로 css가 반영된다.
{: .prompt-info }

<br/>

- internal 방식의 경우 css 코드가 길어지면 html 태그가 무엇이 있는지 파악하기 힘들기 때문에 html 파일에서는 최대한 태그들만 넣는 방식으로 많이 사용한다.

<br/>

- inline 방식 역시 태그가 굉장히 많은데 이 안에 어떤 style이 있는지 파악하기 어렵고 코드 가속성이 떨어져서 최대한 지양하는 것이 좋다.

<br/>