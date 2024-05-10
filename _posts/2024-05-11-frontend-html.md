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

<!DOCTYPE html> 문서 버전과 타입 선언:
<html> 문서 전체를 감싸는 태그
<head> 문서의 메타 정보를 담는 태그
<body> 실제 사용자에게 보여지는 내용을 담는 태그

## 인라인(inline) 태그와 블록(block) 태그

HTML에서 <body>를 구성하는 tag(태그) 중에는 인라인 태그와 블록 태그가 있다.
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
![Desktop View](assets/img/html/div&span.png){: width="500" height="300" .w-75 .normal}

> <div> 태그는 다음 줄에 다른 태그로 입력을 하게 되면 다음 줄에 출력이 되고, <span> 태그는 다음 줄에 입력을 해도 옆으로 이어지는 특징을 가지고 있다.
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

<body>를 구성할 때 <div> 태그를 자주 이용하지만 지나치게 이용해서 <div> 태그가 계속 깊어지게 되면 어디가 어딘지 파악하기가 굉장히 어렵다. 특히 협업을 할 때, 다른 개발자가 그 코드를 파악해야 하는 경우에는 더욱 그렇다.

그래서 <div> 태그 외에 레이아웃 태그를 이용하여 html의 특정 부분이 어떤 의미를 가지고 있는지를 나타낸다.

![Desktop View](assets/img/html/layout.png){: width="500" height="300" .w-75 .right}
|         태그          |         의미          |
| :-------------------  | -------------------:  |
| <header>              | 헤더 영역             |
| <main>                | 메인 영역             |
| <section>             | 콘텐츠 영역           |
| <aside>               | 사이드바 영역         |
| <footer>              | 푸터 영역             |

### Categories and Tags

The `categories` of each post are designed to contain up to two elements, and the number of elements in `tags` can be zero to infinity. For instance:

```yaml
---
categories: [Animal, Insect]
tags: [bee]
---
```

### Author Information

The author information of the post usually does not need to be filled in the _Front Matter_ , they will be obtained from variables `social.name` and the first entry of `social.links` of the configuration file by default. But you can also override it as follows:

Adding author information in `_data/authors.yml` (If your website doesn't have this file, don't hesitate to create one).

```yaml
<author_id>:
  name: <full name>
  twitter: <twitter_of_author>
  url: <homepage_of_author>
```
{: file="_data/authors.yml" }

And then use `author` to specify a single entry or `authors` to specify multiple entries:

```yaml
---
author: <author_id>                     # for single entry
# or
authors: [<author1_id>, <author2_id>]   # for multiple entries
---
```

Having said that, the key `author` can also identify multiple entries.

> The benefit of reading the author information from the file `_data/authors.yml`{: .filepath } is that the page will have the meta tag `twitter:creator`, which enriches the [Twitter Cards](https://developer.twitter.com/en/docs/twitter-for-websites/cards/guides/getting-started#card-and-content-attribution) and is good for SEO.
{: .prompt-info }

### Post Description

By default, the first words of the post are used to display on the home page for a list of posts, in the _Further Reading_ section, and in the XML of the RSS feed. If you don't want to display the auto-generated description for the post, you can customize it using the `description` field in the _Front Matter_ as follows:

```yaml
---
description: Short summary of the post.
---
```

Additionally, the `description` text will also be displayed under the post title on the post's page.

## Table of Contents

By default, the **T**able **o**f **C**ontents (TOC) is displayed on the right panel of the post. If you want to turn it off globally, go to `_config.yml`{: .filepath} and set the value of variable `toc` to `false`. If you want to turn off TOC for a specific post, add the following to the post's [Front Matter](https://jekyllrb.com/docs/front-matter/):

```yaml
---
toc: false
---
```

## Comments

The global switch of comments is defined by variable `comments.active` in the file `_config.yml`{: .filepath}. After selecting a comment system for this variable, comments will be turned on for all posts.

If you want to close the comment for a specific post, add the following to the **Front Matter** of the post:

```yaml
---
comments: false
---
```

## Mathematics

We use [**MathJax**][mathjax] to generate mathematics. For website performance reasons, the mathematical feature won't be loaded by default. But it can be enabled by:

[mathjax]: https://www.mathjax.org/

```yaml
---
math: true
---
```

After enabling the mathematical feature, you can add math equations with the following syntax:

- **Block math** should be added with `$$ math $$` with **mandatory** blank lines before and after `$$`
  - **Inserting equation numbering** should be added with `$$\begin{equation} math \end{equation}$$`
  - **Referencing equation numbering** should be done with `\label{eq:label_name}` in the equation block and `\eqref{eq:label_name}` inline with text (see example below)
- **Inline math** (in lines) should be added with `$$ math $$` without any blank line before or after `$$`
- **Inline math** (in lists) should be added with `\$$ math $$`

```markdown
<!-- Block math, keep all blank lines -->

$$
LaTeX_math_expression
$$

<!-- Equation numbering, keep all blank lines  -->

$$
\begin{equation}
  LaTeX_math_expression
  \label{eq:label_name}
\end{equation}
$$

Can be referenced as \eqref{eq:label_name}.

<!-- Inline math in lines, NO blank lines -->

"Lorem ipsum dolor sit amet, $$ LaTeX_math_expression $$ consectetur adipiscing elit."

<!-- Inline math in lists, escape the first `$` -->

1. \$$ LaTeX_math_expression $$
2. \$$ LaTeX_math_expression $$
3. \$$ LaTeX_math_expression $$
```

> Starting with `v7.0.0`, configuration options for **MathJax** have been moved to file `assets/js/data/mathjax.js`{: .filepath }, and you can change the options as needed, such as adding [extensions][mathjax-exts].  
> If you are building the site via `chirpy-starter`, copy that file from the gem installation directory (check with command `bundle info --path jekyll-theme-chirpy`) to the same directory in your repository.
{: .prompt-tip }

[mathjax-exts]: https://docs.mathjax.org/en/latest/input/tex/extensions/index.html

## Mermaid

[**Mermaid**](https://github.com/mermaid-js/mermaid) is a great diagram generation tool. To enable it on your post, add the following to the YAML block:

```yaml
---
mermaid: true
---
```

Then you can use it like other markdown languages: surround the graph code with ```` ```mermaid ```` and ```` ``` ````.

## Images

### Caption

Add italics to the next line of an image, then it will become the caption and appear at the bottom of the image:

```markdown
![img-description](/path/to/image)
_Image Caption_
```
{: .nolineno}

### Size

In order to prevent the page content layout from shifting when the image is loaded, we should set the width and height for each image.

```markdown
![Desktop View](/assets/img/sample/mockup.png){: width="700" height="400" }
```
{: .nolineno}

> For an SVG, you have to at least specify its _width_, otherwise it won't be rendered.
{: .prompt-info }

Starting from _Chirpy v5.0.0_, `height` and `width` support abbreviations (`height` → `h`, `width` → `w`). The following example has the same effect as the above:

```markdown
![Desktop View](/assets/img/sample/mockup.png){: w="700" h="400" }
```
{: .nolineno}

### Position

By default, the image is centered, but you can specify the position by using one of the classes `normal`, `left`, and `right`.

> Once the position is specified, the image caption should not be added.
{: .prompt-warning }

- **Normal position**

  Image will be left aligned in below sample:

  ```markdown
  ![Desktop View](/assets/img/sample/mockup.png){: .normal }
  ```
  {: .nolineno}

- **Float to the left**

  ```markdown
  ![Desktop View](/assets/img/sample/mockup.png){: .left }
  ```
  {: .nolineno}

- **Float to the right**

  ```markdown
  ![Desktop View](/assets/img/sample/mockup.png){: .right }
  ```
  {: .nolineno}

### Dark/Light mode

You can make images follow theme preferences in dark/light mode. This requires you to prepare two images, one for dark mode and one for light mode, and then assign them a specific class (`dark` or `light`):

```markdown
![Light mode only](/path/to/light-mode.png){: .light }
![Dark mode only](/path/to/dark-mode.png){: .dark }
```

### Shadow

The screenshots of the program window can be considered to show the shadow effect:

```markdown
![Desktop View](/assets/img/sample/mockup.png){: .shadow }
```
{: .nolineno}

### CDN URL

If you host the media resources on the CDN, you can save the time of repeatedly writing the CDN URL by assigning the variable `cdn` of `_config.yml`{: .filepath} file:

```yaml
cdn: https://cdn.com
```
{: file='_config.yml' .nolineno}

Once `cdn` is assigned, the CDN URL will be added to the path of all media resources (site avatar, posts' images, audio and video files) starting with `/`.

For instance, when using images:

```markdown
![The flower](/path/to/flower.png)
```
{: .nolineno}

The parsing result will automatically add the CDN prefix `https://cdn.com` before the image path:

```html
<img src="https://cdn.com/path/to/flower.png" alt="The flower" />
```
{: .nolineno }

### Media Subpath

When a post contains many images, it will be a time-consuming task to repeatedly define the path of the media resources. To solve this, we can define this path in the YAML block of the post:

```yml
---
media_subpath: /img/path/
---
```

And then, the image source of Markdown can write the file name directly:

```md
![The flower](flower.png)
```
{: .nolineno }

The output will be:

```html
<img src="/img/path/flower.png" alt="The flower" />
```
{: .nolineno }

### Preview Image

If you want to add an image at the top of the post, please provide an image with a resolution of `1200 x 630`. Please note that if the image aspect ratio does not meet `1.91 : 1`, the image will be scaled and cropped.

Knowing these prerequisites, you can start setting the image's attribute:

```yaml
---
image:
  path: /path/to/image
  alt: image alternative text
---
```

Note that the [`media_subpath`](#media-subpath) can also be passed to the preview image, that is, when it has been set, the attribute `path` only needs the image file name.

For simple use, you can also just use `image` to define the path.

```yml
---
image: /path/to/image
---
```

### LQIP

For preview images:

```yaml
---
image:
  lqip: /path/to/lqip-file # or base64 URI
---
```

> You can observe LQIP in the preview image of post [_Text and Typography_](/posts/text-and-typography/).

For normal images:

```markdown
![Image description](/path/to/image){: lqip="/path/to/lqip-file" }
```
{: .nolineno }

## Pinned Posts

You can pin one or more posts to the top of the home page, and the fixed posts are sorted in reverse order according to their release date. Enable by:

```yaml
---
pin: true
---
```

## Prompts

There are several types of prompts: `tip`, `info`, `warning`, and `danger`. They can be generated by adding the class `prompt-{type}` to the blockquote. For example, define a prompt of type `info` as follows:

```md
> Example line for prompt.
{: .prompt-info }
```
{: .nolineno }

## Syntax

### Inline Code

```md
`inline code part`
```
{: .nolineno }

### Filepath Hightlight

```md
`/path/to/a/file.extend`{: .filepath}
```
{: .nolineno }

### Code Block

Markdown symbols ```` ``` ```` can easily create a code block as follows:

````md
```
This is a plaintext code snippet.
```
````

#### Specifying Language

Using ```` ```{language} ```` you will get a code block with syntax highlight:

````markdown
```yaml
key: value
```
````

> The Jekyll tag `{% highlight %}` is not compatible with this theme.
{: .prompt-danger }

#### Line Number

By default, all languages except `plaintext`, `console`, and `terminal` will display line numbers. When you want to hide the line number of a code block, add the class `nolineno` to it:

````markdown
```shell
echo 'No more line numbers!'
```
{: .nolineno }
````

#### Specifying the Filename

You may have noticed that the code language will be displayed at the top of the code block. If you want to replace it with the file name, you can add the attribute `file` to achieve this:

````markdown
```shell
# content
```
{: file="path/to/file" }
````

#### Liquid Codes

If you want to display the **Liquid** snippet, surround the liquid code with `{% raw %}` and `{% endraw %}`:

````markdown
{% raw %}
```liquid
{% if product.title contains 'Pack' %}
  This product's title contains the word Pack.
{% endif %}
```
{% endraw %}
````

Or adding `render_with_liquid: false` (Requires Jekyll 4.0 or higher) to the post's YAML block.

## Videos

### Video Sharing Platform

You can embed a video with the following syntax:

```liquid
{% include embed/{Platform}.html id='{ID}' %}
```

Where `Platform` is the lowercase of the platform name, and `ID` is the video ID.

The following table shows how to get the two parameters we need in a given video URL, and you can also know the currently supported video platforms.

| Video URL                                                                                          | Platform   | ID             |
| -------------------------------------------------------------------------------------------------- | ---------- | :------------- |
| [https://www.**youtube**.com/watch?v=**H-B46URT4mg**](https://www.youtube.com/watch?v=H-B46URT4mg) | `youtube`  | `H-B46URT4mg`  |
| [https://www.**twitch**.tv/videos/**1634779211**](https://www.twitch.tv/videos/1634779211)         | `twitch`   | `1634779211`   |
| [https://www.**bilibili**.com/video/**BV1Q44y1B7Wf**](https://www.bilibili.com/video/BV1Q44y1B7Wf) | `bilibili` | `BV1Q44y1B7Wf` |

### Video File

If you want to embed a video file directly, use the following syntax:

```liquid
{% include embed/video.html src='{URL}' %}
```

Where `URL` is an URL to a video file e.g. `/assets/img/sample/video.mp4`.

You can also specify additional attributes for the embedded video file. Here is a full list of attributes allowed.

- `poster='/path/to/poster.png'` - poster image for a video that is shown while video is downloading
- `title='Text'` - title for a video that appears below the video and looks same as for images
- `autoplay=true` - video automatically begins to play back as soon as it can
- `loop=true` - automatically seek back to the start upon reaching the end of the video
- `muted=true` - audio will be initially silenced
- `types` - specify the extensions of additional video formats separated by `|`. Ensure these files exist in the same directory as your primary video file.

Consider an example utilizing all of the above:

```liquid
{%
  include embed/video.html
  src='/path/to/video/video.mp4'
  types='ogg|mov'
  poster='poster.png'
  title='Demo video'
  autoplay=true
  loop=true
  muted=true
%}
```

> It's not recommended to host video files in `assets` folder as they cannot be cached by PWA and may cause issues.
> Instead, use CDN to host video files. Alternatively, use a separate folder that is excluded from PWA (see `pwa.deny_paths` setting in `_config.yml`).
{: .prompt-warning }

## Audios

### Audio File

If you want to embed an audio file directly, use the following syntax:

```liquid
{% include embed/audio.html src='{URL}' %}
```

Where `URL` is an URL to an audio file e.g. `/assets/img/sample/audio.mp3`.

You can also specify additional attributes for the embedded audio file. Here is a full list of attributes allowed.

- `title='Text'` - title for an audio that appears below the audio and looks same as for images
- `types` - specify the extensions of additional audio formats separated by `|`. Ensure these files exist in the same directory as your primary audio file.

Consider an example utilizing all of the above:

```liquid
{%
  include embed/audio.html
  src='/path/to/audio/audio.mp3'
  types='ogg|wav|aac'
  title='Demo audio'
%}
```

> It's not recommended to host audio files in `assets` folder as they cannot be cached by PWA and may cause issues.
> Instead, use CDN to host audio files. Alternatively, use a separate folder that is excluded from PWA (see `pwa.deny_paths` setting in `_config.yml`).
{: .prompt-warning }

## Learn More

For more knowledge about Jekyll posts, visit the [Jekyll Docs: Posts](https://jekyllrb.com/docs/posts/).
