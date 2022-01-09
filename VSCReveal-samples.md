---
theme : "night"
transition: "convex"
highlightTheme: "monokai"
logoImg: "images/uestclogo.jpg"
slideNumber: false
enableTitleFooter: false
title: "量子力学与统计物理"
---

## VSCode Reveal 制作网页PPT示例 {style=background:green;width:960px}
#### 

<br>

::: block
**李小飞** @ 光电科学与工程学院

{style=background:none;width:960px}
::: 

---


// @[vine](etVpwB7uHlw)


---


### Solar System Exploration, 1950s – 1960s

- [ ] Mercury
- [x] Venus
- [x] Earth (Orbit/Moon)
- [x] Mars
- [ ] Jupiter
- [ ] Saturn
- [ ] Uranus
- [ ] Neptune
- [ ] Comet Haley

---

## some Table

|             |          Grouping           ||
First Header  | Second Header | Third Header |
 ------------ | :-----------: | -----------: |
Content       |          *Long Cell*        ||
Content       |   **Cell**    |         Cell |
                                              
New section   |     More      |         Data |
And more      | With an escaped '\\|'       ||
[Prototype table]                             

--

First header | Second header
-------------|---------------
List:        | More  \
- over       | data  \
- several    |       \
- lines      | 

--

First header | Second header
-------------|---------------
Merged       | Cell 1
^^           | Cell 2
^^           | Cell 3


---

<!-- .slide: style="text-align: left;"  -->


字体与对齐
=======

<tiny> 字体 </tiny>

<small> 字体 </small>

<large> 字体 </large>

<Large> 字体 </Large>


---

<!-- .slide: data-visibility="hidden" -->
### Hidden Slides

This slide is visible in the source, but hidden when the presentation is viewed



---

<!-- .slide: data-auto-animate -->
Pretty Code
-----------

```js
import React, { useState } from 'react';

function Example() {
    const [count, setCount] = useState(0);

    return (
    ...
    );
}
```
    					

---

<!-- .slide: data-auto-animate -->

With animations
---------------

```js {data-trim data-line-numbers="|4,8-11|17|22-24"}
import React, { useState } from 'react';

function Example() {
    const [count, setCount] = useState(0);

    return (
    <div>
        <p>You clicked {count} times</p>
        <button onClick={() => setCount(count + 1)}>
        Click me
        </button>
    </div>
    );
}

function SecondExample() {
    const [count, setCount] = useState(0);

    return (
    <div>
        <p>You clicked {count} times</p>
        <button onClick={() => setCount(count + 1)}>
        Click me
        </button>
    </div>
    );
}
``` 

---

---

<!-- .slide: data-auto-animate data-auto-animate-easing="cubic-bezier(0.770, 0.000, 0.175, 1.000)" -->

Auto-Animate
------------

Automatically animate matching elements across slides with [Auto-Animate](https://revealjs.com/auto-animate/).

<div class="r-hstack justify-center">
<div data-id="box1" style="background: #999; width: 50px; height: 50px; margin: 10px; border-radius: 5px;"></div>
<div data-id="box2" style="background: #999; width: 50px; height: 50px; margin: 10px; border-radius: 5px;"></div>
<div data-id="box3" style="background: #999; width: 50px; height: 50px; margin: 10px; border-radius: 5px;"></div>
</div>

---

<!-- .slide: data-auto-animate data-auto-animate-easing="cubic-bezier(0.770, 0.000, 0.175, 1.000)" -->

<div class="r-hstack justify-center">
<div data-id="box1" data-auto-animate-delay="0" style="background: cyan; width: 150px; height: 100px; margin: 10px;"></div>
<div data-id="box2" data-auto-animate-delay="0.1" style="background: magenta; width: 150px; height: 100px; margin: 10px;"></div>
<div data-id="box3" data-auto-animate-delay="0.2" style="background: yellow; width: 150px; height: 100px; margin: 10px;"></div>
</div>

## Auto-Animate {style="margin-top: 20px;"}

---

<!-- .slide: data-auto-animate data-auto-animate-easing="cubic-bezier(0.770, 0.000, 0.175, 1.000)" -->

<div class="r-stack">
    <div data-id="box1" style="background: cyan; width: 300px; height: 300px; border-radius: 200px;"></div>
    <div data-id="box2" style="background: magenta; width: 200px; height: 200px; border-radius: 200px;"></div>
    <div data-id="box3" style="background: yellow; width: 100px; height: 100px; border-radius: 200px;"></div>
</div>

## Auto-Animate {style="margin-top: 20px;"}

---

auto-size text
--------------

### auto-size text {class="r-fit-text"}
### auto-size text auto-size text {class="r-fit-text"}


---

## Fragments, 依次显示同一页各行 {class="r-fit-text"}

Hit the next arrow...{class="fragment"}

... to step through ...{class="fragment"}

... a fragmented slide.{class="fragment"}

This slide has fragments which are also stepped through in the notes window.


---

## Fragment Styles 多种页内动态 {class="r-fit-text"}

There's different types of fragments, like:

grow {class="fragment grow"}

shrink {class="fragment shrink"}

fade-out {class="fragment fade-out"}

<span style="display: inline-block;" class="fragment fade-right">fade-right, </span>
<span style="display: inline-block;" class="fragment fade-up">up, </span>
<span style="display: inline-block;" class="fragment fade-down">down, </span>
<span style="display: inline-block;" class="fragment fade-left">left</span>

fade-in-then-out {class="fragment fade-in-then-out"}

fade-in-then-semi-out {class="fragment fade-in-then-semi-out"}

Highlight <span class="fragment highlight-red">red</span> <span class="fragment highlight-blue">blue</span> <span class="fragment highlight-green">green</span>

---



Transition Styles 转场动态 {class="r-fit-text"}
-----------------

You can select from different transitions, like:  
[None](?transition=none#/transitions) - [Fade](?transition=fade#/transitions) - [Slide](?transition=slide#/transitions) - [Convex](?transition=convex#/transitions) - [Concave](?transition=concave#/transitions) - [Zoom](?transition=zoom#/transitions)

---

Themes 主题设置
------

reveal.js comes with a few themes built in:  
[Black (default)](#) - [White](#) - [League](#) - [Sky](#) - [Beige](#) - [Simple](#)  
[Serif](#) - [Blood](#) - [Night](#) - [Moon](#) - [Solarized](#)

---

<!-- .slide: data-background="#dddddd" -->
Slide Backgrounds  各种背景设置
-----------------------------

Set `data-background="#dddddd"` on a slide to change the background color. All CSS color formats are supported.

<a href="#" class="navigate-down">
    <img class="r-frame" style="background: rgba(255,255,255,0.1);" width="178" height="238" data-src="https://static.slid.es/reveal/arrow.png" alt="Down arrow">
</a>

--

<!-- .slide: data-background="image-placeholder.png" -->
## Image Backgrounds

```html
<!-- .slide: data-background="image.png" -->
```

--

<!-- .slide: data-background="https://static.slid.es/reveal/image-placeholder.png" data-background-repeat="repeat" data-background-size="100px" -->

## Tiled Backgrounds

```html
<!-- .slide: 
data-background="https://static.slid.es/reveal/image-placeholder.png"
data-background-repeat="repeat" 
data-background-size="100px" -->
```

---

<!-- .slide: data-background-video="https://static.slid.es/site/homepage/v1/homepage-video-editor.mp4" data-background-color="#000000" -->

::: block {style="background-color: rgba(0, 0, 0, 0.9); color: #fff; padding: 20px;"}
## Video Backgrounds
```html
<!-- .slide: data-background-video="https://static.slid.es/site/homepage/v1/homepage-video-editor.mp4" data-background-color="#000000" -->
```
:::

---

<!-- .slide: data-background="http://i.giphy.com/90F8aUepslB84.gif" -->

## ... and GIFs!

---


---

<!-- .slide: data-transition="slide" data-background="#4d7e65" data-background-transition="zoom" -->

## Background Transitions 背景切换

Different background transitions are available via the backgroundTransition option. This one's called "zoom".

```md
<!-- .slide: data-transition="slide" data-background="#4d7e65" data-background-transition="zoom" -->
```

---

<!-- .slide: data-transition="slide" data-background="#b5533c" data-background-transition="zoom" -->

## Background Transitions

You can override background transitions per-slide.

```md
<!-- .slide: data-transition="slide" data-background="#b5533c" data-background-transition="zoom" -->
```
---

<!-- .slide:  data-background-iframe="https://hakim.se" data-background-interactive  -->

::: block {style="position: absolute; width: 40%; right: 0; box-shadow: 0 1px 4px rgba(0,0,0,0.5), 0 5px 25px rgba(0,0,0,0.2); background-color: rgba(0, 0, 0, 0.9); color: #fff; padding: 20px; font-size: 20px; text-align: left;"}
## Iframe Backgrounds</h2>

Since reveal.js runs on the web, you can easily embed other web content. Try interacting with the page in the background.
:::

---



