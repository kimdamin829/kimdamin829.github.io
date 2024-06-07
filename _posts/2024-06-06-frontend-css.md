---
title: CSS란? - 웹페이지를 Awesome하게
author: Kim Damin
date: 2024-06-06 11:30:00 +0900
categories: [Frontend, CSS]
tags: [Frontend, CSS]
render_with_liquid: false
---

## CSS 란?

CSS는 색상, 크기, 폰트, 레이아웃 등의 시각적인 부분을 코드로 만들어 HTML을 예쁘게 꾸며주는 역할을 한다.
CSS란 Cascading Style Sheet의 줄임말로 Cascading은 '순차적으로'라는 의미이다. 그래서 중복해서 코드를 작성하게 되면 제일 나중에 작성한 코드가 반영이된다.

<br/>

## HTML에 CSS 넣는 법 (incline, internal, external)

- **Inline 방식**: 태그 안 style 속성에 직접 css를 작성하는 방식
- **Internal 방식**: head 태그에 style 태그를 추가해서 css 코드를 작성하는 방식
- **External 방식**: 별도의 css 파일을 만들어서 삽입하는 방식

<br/>

```html
---
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>

    <!-- internal 방식 -->
    <style>
        div {
            background-color: purple;
        }
    </style>

    <!-- external 방식 -->
    <link rel="stylesheet" href="style.css">

</head>
<body>

    <!-- inline 방식 -->
    <div style="background-color: red;">123</div>
    <div>abc</div>

</body>
</html>
---
```
<br/>

```css
---
/* style.css */
div {
    background-color: blue;
}
---
```
![Desktop View](assets/img/css/inline&internal&external.png){: width="200" height="150" .w-75 .normal}

> css는 중복이 되면 가장 나중에 작성된 코드가 반영되기 때문에, 위의 코드에서는 inline -> external -> internal 방식 순으로 css가 반영된다.
{: .prompt-info }

<br/>

- internal 방식의 경우 css 코드가 길어지면 html 태그가 무엇이 있는지 파악하기 힘들기 때문에 html 파일에서는 최대한 태그들만 넣는 방식으로 많이 사용한다.

<br/>

- inline 방식 역시 태그가 굉장히 많은데 이 안에 어떤 style이 있는지 파악하기 어렵고 코드 가속성이 떨어져서 최대한 지양하는 것이 좋다.

<br/>