---
title: CSS 박스모델
author: Kim Damin
date: 2024-06-06 16:30:00 +0900
categories: [Front End, CSS]
tags: [CSS]
render_with_liquid: false
---

## Display 속성 중 inline과 block의 차이

- **인라인(inline) 태그**
: 태그의 내용만큼만 공간을 차지하여 줄 바꿈없이 다음 요소가 배치된다.

: 인라인 태그 안에 블록 태그를 포함할 수 없다.

- **블록(block) 태그**
: 한 라인의 공간을 차지하여 기본적으로 너비가 100%이다.

: 블록 태그 안에 인라인 태그와 블록 태그를 포함할 수 있다.

<br/>

```html
---
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <!-- div 태그와 span 태그는 기본적으로 각각 block, inline 태그지만,
        div 태그와 span 태그 안에 display 속성을 지정할 수도 있다. -->
    <style>
        div {
            width: 100px;
            height: 100px;
            background-color: aqua;
        }
        span {
            display: block;
            width: 100px;
            height: 100px;
            background-color: violet;
        }

    </style>
</head>
<body>
    <div></div>

    <!-- span은 inline 태그이기 때문에 안에 컨텐츠가 없으면
        너비와 높이를 가지지 않아서 색상이 나타나지 않는다. -->
    <span></span>
</body>
</html>
---
```
<br/><br/>

## CSS 박스모델이란?

![Desktop View](assets/img/css/boxmodel.png){: width="300" height="250" .w-75 .normal}

html에서 너비와 높이를 갖는 모든 요소들은 테두리 영역과 그 내부의 콘텐츠 영역으로 이루어져 있다.

- **padding**: 테두리 영역과 콘텐츠 영역 사이의 공간

- **margin**: 테두리 영역의 바깥쪽 공간

<br/>

```html
---
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        div {
            width: 100px;
            height: 100px;
            background-color: aqua;
            padding: 30px;
            margin: 50px;
            border: 1px solid black;
        }
    </style>
</head>
<body>
    <div>
        하하하하하하하하하하하하하하하하하
    </div>
</body>
</html>
---
```
<br/><br/>

기존 div 이미지
<img src="assets/img/css/origin.png" />

style 태그에 padding: 30px;를 추가했을 때
<img src="assets/img/css/padding.png" />

margin: 50px;를 더 추가했을 때
<img src="assets/img/css/margin.png" />



> css 박스 모델에서는 border 영역과 내부의 content 영역 사이에 padding이라는 영역이 생기고, border 영역의 바깥쪽 영역을 margin이라고 한다.
{: .prompt-info }

<br/>

padding과 margin을 넣으면 상하좌우 모두 영향을 주는데, padding-top, margin-right 등으로 직접 위치를 지정할 수도 있다.
<br/>
다른 방법으로는 padding: 0, 10px, 20px, 30px; 이렇게 작성하면 위에서부터 시계 방향으로 padding의 크기에 영향을 준다.

<br/><br/>

## 정리

- Inline은 너비와 높이를 가지지 않는다.

- 각 요소는 박수모델(margin, padding, border)을 가진다.

<br/>