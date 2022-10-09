# HTML
<!-- Some images that are fixed to background in the css -->
<img id="bg1" class="bg" src="QM-beamer/images/uestclogo-1.png">

HTML文件的结构。

```html
  <html>
  
  <head></head>
  
  <body></body>
  
  </html>
  ```


## <html></html>

根标签,所有的网页标签都放在<html> </html> 之间


## <head></head>

文档的头部，包含如下容器

```html
    <head>

    <title>...</title>

    <meta>

    <link>

    <style></style>

    <script></script>

    </head>
    ```

### 自动刷新
　
<META HTTP-EQUIV="Refresh" content="20">

### 背景图不动

<style> body{background-image:url(logo.gif); background-repeat:no-repeat;
background-position:center;background-attachment: fixed} </style>


## <body></body>

文档的主体，包含所有的网页元素

<div>容器</div> 包含一个逻辑单元： 页面上相互关联的一组元素

<p>段落文本</p>

<h1>标题文本</h1> (1-6)

<em>一般性的强调 （斜体）</em> 

<strong>强烈的强调（粗体）</strong>

<span>单独的块</span>， 以方便CSS设置样式

<q>短文本引用</q>

<blockquote>长文本引用</blockquote>

<br/> 换行

<hr/> 分割线

&nbsp; 空格

<address>北京市西城区德外大街10号</address>

<code>代码行</code> 

<pre>代码块</pre>

<marquee>走马灯</marquee>

<s>删除线</s>

### 背景

<body background="背景图片地址" bgproperties=fixed>

<body bgcolor="#value">

<bgsound="背景音乐地址" loop=infinite>

<body background="5.jpg"

style=" background-repeat:no-repeat ;

background-size:100% 100%; 

background-attachment:fixed;" >

### 贴网页

<iframe src="相关地址" width="宽度" height="高度"></iframe>

### 无序列表
  <ul> 
  <li>df</li>
  <li>fg</li>
  </ul>

### 有序列表
  <ol>
  <li>信息</li>
  <li>信息</li>
  </ol>



### 表格

<table>整个表格</table>
<th>表头一格</th>
<tr>一行</tr>
<td>一格（列）</td>

<caption>2012年到2013年库存记录</caption>
<table summary="本表格记录2012年到2013年库存记录，记录包括U盘和耳机库存量">

### 链接

<a href=”目标网址”> 提示文本 </a>

### 图片

<img src="图片地址" alt="下载失败时的替换文本" title = "提示文本">


### 表单

<form></form> 页面输入数据上传
<form>
<input type="text/password" name="名称" value="默认值或提示信息" />
</form>

###  文本域

<textarea></textarea>多行文本输入域
<textarea rows="行数" cols="列数"></textarea>

### 单选框，复选框

<input type="radio/checkbox" value="值" name="名称" checked="checked"/>

### 下拉列表框

<select></select>

<form action="save.php" method="post" >
<label>爱好:</label>
<select>
<option value="看书">看书</option>
<option value="旅游" selected="selected">旅游</option>
<option value="运动">运动</option>
<option value="购物">购物</option>
</select>
</form>

<form action="save.php" method="post" >

<label>爱好(可多选):</label>
<select multiple="multiple">
<option value="看书">看书</option>
<option value="旅游">旅游</option>
<option value="运动">运动</option>
<option value="购物">购物</option>
</select>
</form>

<input type="submit" value="提交">
<input type="reset" value="重置">

# CSS 样式

CSS全称为“层叠样式表 (Cascading Style Sheets)，它主要是用于定义HTML内容在浏览器内的显示样式，如文字大小、颜色、字体加粗等。

### 基本语法： 选择符{属性:值}

p{
font-size:12px;
color:red;
font-weight:bold;
}

说明： p 选择符, 指明下面的设置只对 <p>段落文本</p> 起作用。

### 内联式 

<p style="color:red;font-size:12px">红色文字</p>

### 嵌入式

<style type="text/css">
span{
    color:red;
}
</style>

要求放在`HEAD`段进行设置，表明主体中 <span>红色文字</span>

### 外部式

写在单独的一个.css文件中. 

<link rel="stylesheet" href="XXX.css" type="text/css"/>

连接的语句要放在`HEAD`段中

### 标签选择器

对单一标签内的内容进行设置<html>、<body>、<h1>、<p>、<img>

### 类选择器

设置的语法：
.类选器名称{css样式代码;}

.stress{
    color:red;
}

.bigsize{
    font-size:25px;
}

使用的语法：
<span class="stress, bigsize"> 胆小如鼠 </span>

### ID选择器

#bigid{
font-size:25px;
}

### 子选择器

.food>li{border:1px solid red;}
为类选择器名为 `food` 的子元素 <li></li> 设置格式 

### 后代选择器

.first most{color:red;}
为名为 `food` 的类选择器的子类 `most` 设置格式 

### 通用选择器

* {color:red;} 
为html中任意标签元素设置格式

### 伪类选择符

a:hover{color:red;}
使被<a></a>包裹的文字在鼠标滑过时变为红色。

### 分组选择符

h1,h2,h3{color:red;}


### 继承

设置于段落<p></p>的, 对文字块<span></span>自然也起作用

### 权值

标签 1， 类选择符 10， ID选择符 100 
比如上面三个都对文字色有设置的话， HTML 使用权值最大的ID选择符的设置


### 层叠

p{color:red;}
p{color:green;}
多次的层叠最后一次有效

### 重要性

有些特殊元素的素性不能被改变

h1{color:red!important;}
h1{color:green;}
此时，依然是红色


### 文字设置

字体：font-family:"宋体";

字号：font-size:12px;color:#666;

粗体：font-weight:bold;

斜体: font-style:italic;

下划线: text-decoration:line-through;

### 段落设置

缩进: text-indent:2em;

行间距: line-height:1.5em;

字(母)间隔: letter-spacing:50px;

单词间距: word-spacing:50px;

### 元素分类

- 块状元素 <div>、<p>、<h1>，<h6>、<ol>、<ul>、<dl>、<table>、<address>、<blockquote> 、<form>
- 内联元素 <a>、<span>、<br>、<i>、<em>、<strong>、<label>、<q>、<var>、<cite>、<code>
- 内联块状元素 <img>、<input>

a{display:block;} 把 内联元素 <a> 改成块状元素
display:inline-block

### 盒模型 

- 边框

div{

border:2px solid red;

border-width:2px;

border-style:solid; dotted/dashed

border-color:red;

border-bottom:1px solid red -top/-right/-left/-bottom

}

- 外边界

div{margin:20px 10px 15px 30px;}

div{

margin-top:20px;

margin-right:10px;

margin-bottom:15px;

margin-left:30px;

}

- 内边界

div{

padding-top:20px;

padding-right:10px;

padding-bottom:15px;

padding-left:30px;

}

### 布局模型

- 流动模型（Flow）：自上而下自左而右排布各元素

- 浮动模型 (Float) ： 块状元素通常独占一行， 如果要两个块状元素共占一行，则需使用

div{

width:200px;

height:200px;

border:2px red solid;

float:left;

}

<div id="div1"></div>

<div id="div2"></div>

注意：设置浮动的同时一定要先设置块状元素的宽度，且需要浮动的几个元素宽度加起来一定要小于容器元素的宽度

- 层模型（Layer）

position: absolute 以父类位置进行绝对定位

position: relative 相对于兄弟元素的定位

position: fixed 视图坐标定位
