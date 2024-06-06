---
title: CSS flexbox와 position
author: Kim Damin
date: 2024-06-06 17:30:00 +0900
categories: [Front End, CSS]
tags: [CSS]
render_with_liquid: false
---

## flexbox

: 한 줄에 모두 배치하고 싶은데 화면 사이즈가 달라지면 다음 줄로 넘어가는 문제를 보완하기 위해 나온 옵션

<br/>

- **display: flex**
  - flexbox는 상위 요소에 옵션을 주게 되면 그 내부의   요소들이 특정 배치를 갖게 만드는 옵션이다.
  - 화면에 맞게 반응형으로 배치가 되어 화면의 크기에 따라 조정된다.

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
        body {
            height: 100px;
            border: 1px solid black;
            display: flex;
            justify-content: center;
            align-items: center;
        }
        div {
            width: 50px;
            height: 50px;
            margin: 5px;
            background-color: yellowgreen;
        }

    </style>
</head>
<body>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
    <div></div>
</body>
</html>
---
```
<br/><br/>

<img src="assets/img/css/flexbox1.png" />

- 화면 사이즈를 줄였을 때
<br/>
<img src="assets/img/css/flexbox2.png" />

> display를 flex로 지정하면 화면에 맞게 반응형으로 배치된다.
{: .prompt-info }

<br/>

- **body**에 **display: flex;** 를 해서 body의 하위 요소에 있는 태그들은 왼쪽에서 오른쪽으로 배치하는데, **flex-direction: column;**을 넣으면 위에서 아래로 배치할 수 있다.
- **justify-content** 속성은 가로축을 기준으로 정렬하고
- **align-item** 속성은 세로축을 기준으로 정렬한다.

<br/>