# Reveal.js+markdown+vscode 制作PPT

---

## 前言

reveal-md 是使用 Markdown 和 HTML 写逼格满满的 PPT 的开源项目

项目地址：[reveal-md]{https://github.com/webpro/reveal-md}

---

## 特点

Reveal.js 可以使用 markdown 语言直接写静态的文本，并可以加入各种 html 语言支持的交互动画,
reveal.js 是一个开放源代码 HTML 表示框架。它使使用 Web 浏览器的任何人都可以免费创建功能齐全且美观的演示文稿
该框架具有广泛的功能，包括嵌套幻灯片，Markdown 支持，自动动画，PDF 导出，演讲者注释，LaTeX 支持，语法突出显示的代码等等

项目地址：[reveal.js]{https://github.com/hakimel/reveal.js/archive/master.zip}

---

## Reveal 安装

* npm install -g reveal-md
* git clone https://github.com/hakimel/reveal.js.gif
* cd reveal.js && npm install
* npm start &

---

## 环境

- vscode-reveal 
- Markdown All in One 
- Markdown Preview Enhanced 
- view-in-browser 

---

## 生成html

- 实时查看：
  reveal-md QM.md -w
- 生成静态网页
  reveal-md QM.md --static QM
- 问题，不支持 Mermaid 
  
```mermaid
graph TD;
    A-->B;
    A-->C;
    B-->D;
    C-->D;
```

---

##  Markup
Here's a barebones example of a fully working reveal.js presentation:

```html
<html>
  <head>
    <link rel="stylesheet" href="dist/reveal.css">
    <link rel="stylesheet" href="dist/theme/white.css">
  </head>
  <body>
    <div class="reveal">
      <div class="slides">
        <section>Slide 1</section>
        <section>Slide 2</section>
      </div>
    </div>
    <script src="dist/reveal.js"></script>
    <script>
      Reveal.initialize();
    </script>
  </body>
</html>
```

---

## Markdown 
```
<section data-markdown>
  <textarea data-template>
    ## Slide 1
    A paragraph with some text and a [link](http://hakim.se).
    ---
    ## Slide 2
    ---
    ## Slide 3
  </textarea>
</section>
```

---

## Markdown Plugin
```
<script src="plugin/markdown/markdown.js"></script>
<script>
  Reveal.initialize({
    plugins: [ RevealMarkdown ]
  });
</script>
```

---

## External Markdown
This feature requires that reveal.js runs from a local web server.
```
<section data-markdown="example.md"
         data-separator="^\n\n\n"
         data-separator-vertical="^\n\n"
         data-separator-notes="^Note:"
         data-charset="iso-8859-15">
    <!--
        Note that Windows uses `\r\n` instead of `\n` as its linefeed character.
        For a regex that supports all operating systems, use `\r?\n` instead of `\n`.
    -->
</section>
```

---

## Themes 

- black:	Black background, white text, blue links (default)
- white:	White background, black text, blue links
- league:	Gray background, white text, blue links
- beige:	Beige background, dark text, brown links
- sky:	Blue background, thin dark text, blue links
- night:	Black background, thick white text, orange links
- serif:	Cappuccino background, gray text, brown links

---

- simple:	White background, black text, blue links
- solarized:	Cream-colored background, dark green text, blue links
- blood:	Dark background, thick white text, red links
- moon:	Dark blue background, thick grey text, blue links

---

### Themes 选择

1. 在md文件最前面加上一句 theme : "black"
2. 在导出的index.hrml 中改 
```html
<link rel="stylesheet" href="dist/theme/black.css">
```
3. you can opt to start from a blank CSS document and customize everything from the ground up

---

## Transitions 

- none:	Switch backgrounds instantly
- fade:	Cross fade — default for background transitions
- slide:	Slide between backgrounds — default for slide transitions
- convex:	Slide at a convex angle
- concave:	Slide at a concave angle
- zoom:	 Scale the incoming slide up so it grows in from the center of the screen

---

### Transitions 选择

```html
<section data-transition="slide">
    The train goes on …
</section>
<section data-transition="slide">
    and on …
</section>
<section data-transition="slide-in fade-out">
    and stops.
</section>
<section data-transition="fade-in slide-out">
    (Passengers entering and leaving)
</section>
<section data-transition="slide">
    And it starts again.
</section>
```
```
Reveal.initialize({
  backgroundTransition: 'slide'
});
```

---

### Configuration Options
```
Reveal.initialize({

  // Display presentation control arrows
  controls: true,

  // Help the user learn the controls by providing hints, for 
  // bouncing the down arrow when they first encounter a ...
  controlsTutorial: true,

  // Determines where controls appear, "edges" or ...
  controlsLayout: 'bottom-right',
  ...
  });

```
```
// Turn autoSlide off
Reveal.configure({ autoSlide: 0 });

// Start auto-sliding every 5s
Reveal.configure({ autoSlide: 5000 });
```

---

### Presentation Size
```
Reveal.initialize({
  // The "normal" size of the presentation, aspect ratio will
  // be preserved when the presentation is scaled to fit different
  // resolutions. Can be specified using percentage units.
  width: 960,
  height: 700,

  // Factor of the display size that should remain empty around
  // the content
  margin: 0.04,

  // Bounds for smallest/largest possible scale to apply to content
  minScale: 0.2,
  maxScale: 2.0
});
```

---

### Center

Slides are vertically centered on the screen based on how much content they contain. To disable this and leave slides fixed at their configured height set center to false.
```
Reveal.initialize({ center: false })

```

---

### Embedded

By default, reveal.js will assume that it should cover the full browser viewport. If you want to embed your presentation within a smaller portion of a web page, or show multiple presentations on the same page, you can use the embedded config option.
```
Reveal.initialize({ embedded: false })
```

---

### Color Backgrounds
```
<section data-background-color="aquamarine">
  <h2>🐟</h2>
</section>
<section data-background-color="rgb(70, 70, 255)">
  <h2>🐳</h2>
</section>
```

---

### Image Backgrounds
```
<section data-background-image="http://example.com/image.png">
  <h2>Image</h2>
</section>
<section data-background-image="http://example.com/image.png" 
          data-background-size="100px" data-background-repeat="repeat">
  <h2>This background image will be sized to 100px and repeated</h2>
</section>
```

---

### Media

#### Autoplay
```
<video data-autoplay src="http://clips.vorwaerts-gmbh.de/big_buck_bunny.mp4"></video>
```
```
Reveal.initialize({
	autoPlayMedia: true
})
```