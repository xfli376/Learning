---
"markdown.styles": [
    "/Users/xfli/.vscode/all.css"
]
---

## Markdown 学习笔记 {ignore=true}

目录： 
<!-- @import "[TOC]" {cmd="toc" depthFrom=2 depthTo=3 orderedList=false} -->

<!-- code_chunk_output -->

- [1. Basic Syntax （基本语法）](#1-basic-syntax-基本语法)
- [2. Extended Syntax 扩展语法](#2-extended-syntax-扩展语法)
- [3. 其他](#3-其他)
- [字体大小与颜色](#字体大小与颜色)

<!-- /code_chunk_output -->

### 1. Basic Syntax （基本语法）


#### Heading

```markdown
# h1 Heading
## h2 Heading
### h3 Heading
#### h4 Heading
##### h5 Heading
###### h6 Heading
```


#### Text style

```markdown
**bold text**
*italicized text*
```


#### Blockquote

```markdown
> blockquote
```


#### Ordered List

```markdown
1. First item
2. Second item
3. Third item
```


#### Unordered List

```markdown
- First item
- Second item
- Third item
```

实例1：

Revealjs in your Visual Studio Code !

- 🚀 Markdown 
- ⚡️️ Side view with auto refresh
- 💎 Syntax highlighted code
- 🔥 Auto animation
- 📼 Export to PDF and HTML
- ⏱ Many preconfigured plugins


#### Code

```markdown
`single line of code`
```

```markdown
    ```js
    class Person(){
        #name = "Jhon Doe"
    }
    ```

```



#### Link and image

```markdown
[title](https://www.example.com)
![alt text](https://via.placeholder.com/150)
```



### 2. Extended Syntax 扩展语法

#### Table

Table use the multimd-table extension of markdown
```markdown
|             |          Grouping           ||
First Header  | Second Header | Third Header |
 ------------ | :-----------: | -----------: |
Content       |          *Long Cell*        ||
Content       |   **Cell**    |         Cell |
                                              
New section   |     More      |         Data |
And more      | With an escaped '\\|'       ||
[Prototype table]
```


#### Classes, identifiers and attributes to your markdown

```markdown
# header {.some-class style="background:blue"}
paragraph {data-toggle=modal}
```


#### Abbreviation

```markdown
*[HTML]: Hyper Text Markup Language
*[W3C]:  World Wide Web Consortium
The HTML specification
is maintained by the W3C.
```


#### Attribution

> The plugin allows to provide an attribution for a quotation: 

```markdown
> That's one small step for [a] man, one giant leap for mankind.  
> — Neil Armstrong (1969, July 21)
```

```html
<figure class="c-blockquote">
  <blockquote>
    <p>
      That's one small step for [a] man, one giant leap for mankind.  
    </p>
  </blockquote>
  <figcaption class="c-blockquote__attribution">
    Neil Armstrong (1969, July 21)
  </figcaption>
</figure>
```


#### Definition list

Syntax is based on [pandoc definition lists](https://pandoc.org/MANUAL.html#definition-lists).

```markdown
Term 1

:   Definition 1

Term 2 with *inline markup*

:   Definition 2

        { some code, part of Definition 2 }

    Third paragraph of definition 2.
```


#### Font Awesome icons

```markdown
:fa-address-card:
:fa-align-left:
:fa-ambulance:
:fa-american-sign-language-interpreting:
:fa-anchor:
:fa-audio-description:
:fa-battery-full:
:fa-box-open:
:fa-broadcast-tower:
```



#### Other html inline

```markdown
++inserted++

[[x]]

==marked==

´´´
result
´´´

H~2~0

29^th^
```

```html
<p><ins>inserted</ins></p>
<p><kbd>x</kbd></p>
<p><mark>marked</mark></p>
<pre><samp>result
</samp></pre>
<p>H<sub>2</sub>0</p>
<p>29<sup>th</sup></p>
```



#### GitHub-style task lists


```markdown
- [ ] Mercury
- [x] Venus
- [x] Earth (Orbit/Moon)
- [x] Mars
- [ ] Jupiter
- [ ] Saturn
- [ ] Uranus
- [ ] Neptune
- [ ] Comet Haley
```



#### Block

Create block divs and nest divs within each other as well.

```markdown
::: id=my-id class=blog-post
content
:::

::: #my-id .blog-post
content
:::
```

```html
<div id="my-id" class="blog-post">
<p>content</p>
</div>
```


#### Iframe

```markdown
/i/https://www.youtube.com/embed/kurZDZ5jT2Y
```


### 3. 其他 


#### 字体大小与颜色

<font face="华文仿宋" >华文仿宋</font>
<font face="华文仿宋" >华文仿宋</font>
<font face="凌慧体-简" >凌慧体-简</font>
<font face="娃娃体-简" >娃娃体-简</font>

<font color=#FF000 >红色</font>
<font color=#008000 >绿色</font>
<font color=#FFFF00 >黄色</font>

<font size=1 color=red >红色</font>
<font size=5 color=blue >绿色</font>
<font size=7 color=green >green</font>



