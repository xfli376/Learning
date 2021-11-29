---
title: "学习笔记-合集"
author: 李小飞
date: "2021-11-25"
subject: "Markdown"
keywords: [git, Github]

---

# Git and github

Git是一款免费、开源的分布式版本控制系统，用于敏捷高效地处理任何或小或大的项目. 是 Linus Torvalds 为了帮助管理 Linux 内核开发而开发的一个开放源码的版本控制软件。工作原理分为工作区->add->缓存区->commit->本地库(repository)

Github是一个代码托管云平台和开发者社区，开发者可以在Github上创建自己的开源项目并与其他开发者协作编码。创业公司可以用它来托管软件项目。

## Git 操作本地库（Repository

### 建立本地库

mkdir learning
cd Learning
git init
ls -a 	one can find a file .git

### 设置本地库签名

git config --global user.name xfli...
git config --global user.email xfli...@qq.com

### 建立文件并添加到缓存区

vim test.md
git status
建立的文件在工作区，可以添加到缓存区 (add)
git add test.md
git status
git rm    % 从缓存区删除

### 把缓存区文件提交到本地库 （Commit）

git commit -m "My First Commit" test.md
git status
git log
git reflog
vim test.md      %进行文件修改
git diff test.md
git add test.md  %修改后的文件（第二版）添加到缓存区
git commit -m "My second Commit" test.md %提交第二版到本地库
...
git commit -m "My 3rd Commit" test.md " %提交第三版到本地库
git add .
git reflog

### 提取第X版本文件到工作区

git reflog
回到上一个版本
git rest --hard HEAD^ or HEAD-1
回到上上个版本
git rest --hard HEAD^^ or HEAD-2
回到前第100个版本
git rest --hard HEAD~100
回到指定版本号的版本
git rest --hard 版本号X

### 并行推进（分支技术）

git branch limen
git branch wangwu
git branch -v
git checkout limen
git branch -v
vim test.md  # limen  修改了文件
git add test.md
git checkout master %回到master 分支
git merge limen %把limen 分支的修改内容合并进来
git add test.md
git commit -m "Master merge limen First commit" test.md

## Github 远程操作

### 在github建立远程库

new respository-> Learning
Create respository

### 查远程库地址并推送

https 别名 http://github.com/xfli376/Learning.git
SSH   别名 git@github.com:xfli376/Learning.git
Github CLI 别名 gh repo clone xfli376/Learning
git remote add origin
git@github.com:xfli376/Learning.git

(origin 是取的别名)
git push origin master

### Clone远程库到本地

mkdir ~/adirection
cd ~/adirection
git clone http://github.com/xfli376/Learning.git

### 用ssh进行Clonecd 

ssh -T git@github.com
git clone git@github.com:xfli376/Learning.git
git fetch origin master

### 开放给合作者

Settings-> Collaborators-> Add collaborator
合作者Accept invitation
git push origin main

# Markdown

Markdown是一种轻量级标记语言，创始人为约翰·格鲁伯（英语：John Gruber）。 它允许人们使用易读易写的纯文本格式编写文档。John Gruber在2004年创造了Markdown语言，现在有了MultiMarkdown、GitHub Flavored Markdown (GFM)、Pandoc、CommonMark等Markdown的变体。

## Markdown 基本语法

These are the elements outlined in John Gruber’s original design document. All Markdown applications support these elements.

### Heading

# H1

## H2

### H3

### Bold

**bold text**

### Italic

*italicized text*

### Blockquote

> blockquote
> 
> > necked blockquote

### Ordered List

1. First item
2. Second item
3. Third item

### Unordered List

- First item
- Second item
- Third item

### Code

in line `code`

### Horizontal Rule

---

### Link

[Markdown Guide](https://www.markdownguide.org)

### Image

![alt text](https://www.markdownguide.org/assets/images/tux.png)

## Markdown 扩展语法

These elements extend the basic syntax by adding additional features. Not all Markdown applications support these elements.

### Table

| Syntax    | Description |
| ----------- | ------------- |
| Header    | Title       |
| Paragraph | Text        |

### Fenced Code Block

```
{
  "firstName": "John",
  "lastName": "Smith",
  "age": 25
}
```

### Footnote

Here's a sentence with a footnote. [^1]

### Heading ID

### My Great Heading {#custom-id}

### Definition List

**Term**
: definition

### Strikethrough

~~The world is flat.~~

### Task List

- [x] Write the press release
- [ ] Update the website
- [ ] Contact the media

## Markdown 公式输入 (katex)

### 行内公式与行间公式

行内$a^2+b^2=c^2$ 公式

行间公式

$$
a^2+b^2=c^2
$$

### \{ \} \text{} 和 \operatorname{}

${xyz}^{xyz}$, ${xyz}^xyz$,  $\operatorname{sin}(\theta)$ , $\sin(\theta)$,

$$
f(n)=n^n \quad \text{n$\in N^\ast$}
$$

### 字符变大变小

$ \tiny x $, $\scriptsize x $, $\footnotesize x $, $\small x$, $\normalsize x$, $x$, $\large x$, $\Large x$, $\LARGE x$, $\huge x$, $\Huge x$, $\boldsymbol{\alpha 12bcEF}12bcEF$

### 各种字体型

$\mathnormal  {abc123}$, $\mathrm  {abc123}$, $\mathit  {abc123}$, $\mathsf {abc123}$,$\mathtt  {abc123}$, $\mathfrak {  abc123}$, $\mathbb {  abc123}$, $\mathcal {abc123}$,$\mathscr {abc123}$, $\bold {abc123}$, $\bm {abc123}$

$\textcolor{red}{F=ma}$

$ \colorbox{red}{black on red} $

### 空行与空格

用$\; or ~ or \, or \quad or \qquad or \space or \thinspace or \thickspace or \medspace or \: or \nobreakspace or \negthinspace or \negthickspace or \negmedspace$ 来产生空格

用$ \\  A  \newline A \\ $  进行换行

### 括号

$\lang \phi\vert\psi \rang, \lfloor {abc} \rfloor, \lbrace {abc} \rbrace, \langle {ab} \rangle, \left( {abc} \right), \left[ {abc} \right], \lgroup {abc} \rgroup, \lang {abc} \rang, \lt {abc} \gt, \{ {abc} \},| \frac{a}{b} |, \|\frac{a}{b} \|,| \dfrac{a}{b} |, \|\dfrac{a}{b} \|$

$\tbinom{n}{k}$,

$\binom{n}{k}$,

$\dbinom{n}{k}$,

${n\brace k}$,

${n\choose k}$,

${n\brack k}$

$$
| \frac{a}{b} |, \|\frac{a}{b} \|
$$

$$
\Bigg \{
    \bigg \{
        \Big \{
            \big \{
                    \dfrac{a}{b}
            \big \}
        \Big \}
    \bigg \}
\Bigg \}
$$

$$
a = \left(1 + 2 + 3 + \cdots\right. \\ \qquad \left. n - 2 + n - 1 + n\right.)
$$

$$
\left. f(x)\middle |_{x=0} \right.
$$

### 上下关系

${1}\over{xyz\over{x}}$， $x \atop y$，$\stackrel{x}{y}$, $\overset{x}{y}$, $\underset{x}{y}$, $a\raisebox{0.25em}{b}c$,

$ \displaystyle \sum_{i=1}^N $

### 分数

$\tfrac{s}{m},\frac{s}{m},\dfrac{s}{m},\cfrac{s}{m} $

### 点和头

$ 
\ldots, \dots, \cdots, \vdots, \ddots 
$

$ 
a^{\prime}, \bar{a}, \breve{a}, \dot{a}, \ddot{a}, \hat{a}, \widehat{ace}, \mathring{A},  \vec{F}=m\vec{a}
$

### 数学推导

$\rArr$，$\rarr$，$\lrArr$，$\lrarr$，$\nRightarrow$，$\nLeftarrow$，$\nLeftrightarrow$，$\implies$， $\xRightarrow[under]{over}$，$\xrightarrow[under]{over}, \to, \propto, \approx $

$\because, \therefore, \forall, \And, \exists$

### 求和，积分和极限

$$
\sum_{1<i<N}{\frac {N-i+1}{i^{N-1}} }
$$

$$
\sum\limits_{i=1}^{N}{\frac {N-i+1}{i^{N-1}} }
$$

$\displaystyle \int_{0}^{\infty} f(x) dx $,

$\int_{0}^{\infty} f(x) dx $,
$\displaystyle\int \limits_{0}^{\infty} f(x) dx $,

$\int \limits_{0}^{\infty} f(x) dx $,
$\smallint$, $\intop$, $\iint$, $\iiint$, $\oint$, $\oiint$, $\oiiint$

$\lim\limits_{i \to \infty} \dfrac{1}{i} = 0$

### 符号

$\times, \div, \mp, \pm, \oplus, \otimes, \equiv, \ne, \sim,\le, \ge, \gg, \ll, \geqq, \leqq, \pmod{a}, \mod{a},\centerdot, \bullet, \in, \ni, \cong, \gt, \text{\sect}, \copyright, \bigtriangledown, \hbar, \ell, \yen, \degree, \angle, \infty, \ast,\star, \bigstar, \%$

$\alpha, \beta, \gamma, \delta, \epsilon, \zeta, \eta, \theta, \lambda, \mu, \nu,  \xi,  \pi, \rho, \sigma,  \tau, \upsilon, \phi, \chi, \psi, \omega, \varphi, \varsigma, \varepsilon,  \nabla, \partial $

\define

$ \def\foo{x^2} \foo + \foo $

$ \gdef\bar#1{#1^2} \bar{x} + \bar{y}$

Direct Input:

§ ¶ £ ¥ ∇ ∞ · ∠ ∡ ∢ ♠ ♡ ♢ ♣ ♭ ♮ ♯ ✓ … ⋮ ⋯ ⋱ ! £ ¥ ∇ ∞ ⋅ ∠ ∡ ∢ ♠ ♡ ♢ ♣ ♭ ♮ ♯ ✓ … ⋮ ⋯⋱ ! ‼ ⦵

### 矩阵

$$
\begin{matrix} 
1 & 2 & 3 \\   
2 & 3 & 4 \\   
4 & 5 & 6 \\  
\end{matrix}
$$

$$
\begin{pmatrix}  
1 & 2 & 3 \\   
2 & 3 & 4 \\  
4 & 5 & 6 \\  
\end{pmatrix}
$$

$$
\begin{bmatrix} 
1 & 2 & 3 \\ 
2 & 3 & 4 \\ 
4 & 5 & 6 \\ 
\end{bmatrix}
$$

$$
\begin{vmatrix} 
1 & 2 & 3 \\ 
2 & 3 & 4 \\ 
4 & 5 & 6 \\ 
\end{vmatrix}
$$

$$
\begin{Vmatrix} 
1 & 2 & 3 \\   
2 & 3 & 4 \\   
4 & 5 & 6 \\   
\end{Vmatrix}
$$

### 数组、数表、方程组

$$
\begin{array}{lcr} 
1 & 2 & 3 \\ 
2 & 3 & 4 \\ 
4 & 5 & 6 \\ 
\end{array}
$$

$$
\begin{array}{l|crlc:r} 
1 & 2 & 3 & 1 & 2 & 3 \\ \hline
2 & 3 & 4 & 2 & 3 & 4 \\ 
4 & 5 & 6 & 4 & 5 & 6 \\ \hline \hline
4 & 5 & 6 & 4 & 5 & 6 \\ 
\end{array}
$$

$$
\left \{
\begin{array}{l} 
a_1x+b_1y+c_1=0  \\ 
a_2x+b_2y+c_2=0  \\ 
a_3x+b_3y+c_3=0   
\end{array}
\right.
$$

### 条件式

$$
\delta (x)=
\begin{cases} 
1, &  \text{if} x = 0  \\  
0, &  \text{if} x \neq 0   
\end{cases}
$$

###  一般公式、多行公式对齐及公式编号

$$
x^2+y^2=1 \tag{1}
$$

$$
\begin{aligned}
 a &= a+c \\
   &= a+b+d 
\end{aligned}
$$

$$
\left \{
\begin{alignedat}{3}
 10 &x +3 &&y =20 \\
  8 &x +13 &&y = 8 
\end{alignedat}
\right.
$$

## Markdown 作PPT

[PPT](\GitDev\markdown\presentation\presention.md) \GitDev\markdown\presentation\presention.md

[^1]: This is the footnote.

