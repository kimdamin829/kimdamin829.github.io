---
title: CSS 선택자와 상태
author: Kim Damin
date: 2024-06-07 05:30:00 +0900
categories: [Frontend, CSS]
tags: [Frontend, CSS]
render_with_liquid: false
---

## 선택자

웹사이트에서 특정 부분을 지정해서 이벤트를 줄 때 선택자가 필요하다. 예를 들어, '세 번째 버튼만 색을 바꿔 주세요'라는 요청이 들어왔을 때, 선택자를 이용할 수 있다.

- Element명으로 선택
- Class, ID로 선택
- Pseudo Selector (가상 선택자)

<br/><br/>

## 선택자 지정 방법

- Element명으로 선택: html 요소를 직접적으로 선택하여 꾸며준다.
  - 태그로 선택 (태그명): 해당 태그 안에 있는 모든 element가 선택된다.
  - Class로 선택 (.class명): 해당 class를 가진 모든 element가 선택된다.
  - ID로 선택 (#id명): id는 고유값이므로 하나의 element가 선택된다.
- **Pseudo Selector (가상 선택자)**: html 요소를 직접 선택하지 않고, 요소의 상태에 따라 선택하여 꾸며준다.

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
            background-color: green;
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
        <button class="btn" id="btn-6">뒤로가기</button>
    </div>
</body>
</html>
---
```
<br/><br/>

<img src="assets/img/css/selector.png" justify-content="left"/>

<br/>

1. 태그명 선택: **button** 태그를 선택하여 해당 태그를 갖는 모든 버튼의 색을 바꿔준다.
2. class명 선택: **.btn** 클래스를 선택하여 class명이 btn인 로그인, 뒤로가기 버튼의 background color를 바꿔준다.
3. id명 선택: **#btn-3** 아이디를 선택하여 3번 버튼의 background color를 바꿔준다.
4. pseudo selector: **div > button:nth-child(4)**를 통해 div에 있는 버튼 중 네 번째 버튼의 background color를 바꿔준다.

> 복합 선택자 패턴의 경우, 선택자 방식에 따라 우선 순위가 적용되는 규칙이 있는데 일반적으로 선택자가 구체적일수록 우선순위가 높다. 따라서 우선순위는 id > class > tag 이다.
{: .prompt-info }

<br/><br/>

## 선택자 우선순위 적용

|    선택자 방식    |   우선순위 점수  |
| :--------------:  | :--------------: |
| !important        | 무한대           |
| inline 스타일     | 1000             |
| id 선택자         | 100              |
| class 선택자      | 10               |
| 속성 기반 선택자  | 10               |
| 가상 클래스       | 10               |
| 가상 요소         | 10               |
| 태그 선택자       | 1                |
| 전체 선택자       | 0                |

<br/><br/>

# 점수 계산 방법

```css
---
.list button.btn {
}
---
```
Class(10) + Tag (1) + Class(10) = 21점

<br/>

```css
---
button:nth-child(4) {
}
---
```
Tag (1) + Pseudo Class(10) = 11점

<br/>

```css
---
#btn-3 {
}
---
```
ID(10) = 10점

<br/>

- 우선순위 점수가 같을 때는 가장 나중에 나온 것이 적용된다.

<br/>