## 设置

### 正反向搜索
- TEX / COMMAND / View LaTex PDF / View in VScode tab  (Shift+v)
- 正向搜索 在tex中选中内容, 右击菜单 /synctex from cursor (OPT+CMD+J)
- 反向搜索 在pdf中选中内容, Shift+CMD+单击
  
### 基本操作

- 多行变一行 ctr+J
- 代码格式化 shit+opt+F
- 复制光标 opt+cmd+上/下光标

## LaTeX 排版国标样式的数学符号
### 正体与斜体
国标要求普通的变量和函数名使用斜体字母表示，数学常数（如 ）和特殊函数使用正体。
但是 `LaTeX` 习惯是大写希腊字母默认使用正体，不提供正体的小写字母。

- `amsmath` 宏包提供了 `\varGamma` $\varGamma$ 等斜体大写希腊字母命令；
- `newtxmath` 的 `slantedGreek` 选项可以使大写希腊字母的命令变为默认斜体，并且还提供了 `\upalpha` 和 `\upGamma` 等正体希腊字母命令；
- `unicode-math` 可以使用 `math-style=ISO` 选项和 `\symup` 正体符号命令。
  
### 粗体
LaTeX 传统使用**粗正体**表示向量和矩阵，所以只有一个 \mathbf 命令.
但是这个命令对希腊字母无效。
国标要求使用**粗斜体**表示向量和矩阵
- 使用 `bm` 宏包的 `\bm` 得到粗斜体字母。
- `unicode-math` 可以设置 `bold-style=ISO`，提供 `\symbf` 命令用于粗斜体的数学符号。

### 平行四边形符号
LaTeX 没有提供平行四边形符号。但`unicode-math` 宏包提供了 `\parallelogram` 命令。

### 平行号
LaTeX 默认的平行号 \parallel 是竖直的.国标对竖直的和倾斜的平行号都允许，但是常见的更多的是斜的.可以在 LaTeX 中使用 `\renewcommand\parallel{\mathrel{/\mskip-2.5mu/}}`。

### 相似和全等符号
LaTeX 默认虽然提供了 `\sim` 和 `\cong` 表示相似和全等，但是国标中要求的符号的弯曲方向是相反的。amssymb 提供了 `\backsim`，unicode-math 提供了 `\backsim` 和 `\backcong`，但是曲线部分仍略小于国标的样式。

### 国际单位制

LaTeX提供了国际单位制的系统化解决方案`siunitx` 宏包
比如 `\SI{10}{\hertz}` 输出为 “10Hz” `\SIrange{10}{100}{\hertz}` 输出为 “10Hz to 100Hz”。`\num`可以输出各种方式的数字形式（比如科学记数法）

## snippets (代码片段)

snippet[ˈsnɪpɪt]，或者说「code snippet」，也即代码片，指的是能够帮助输入重复代码模式，比如循环或条件语句，的模板。通过 snippet ，我们仅仅输入一小段字符串，就可以在代码片引擎的帮助下，生成预定义的模板代码，我们还可以通过在预定义的光标位置之间跳转，来快速补全模板。

### 代码片设置文件
- VScode 中 通过快捷键「Ctrl + Shift + P」打开命令窗口（All Command Window），输入「snippet」，点选「首选项：配置用户代码片片段」；选择 latex.json, 就可以设置相应的snippets.
- $HOME/Library/Application Support/Code/User/snippets/(language).snippets

### 语法结构
- prefix：前缀，设置把代码片从 IntelliSense 中呼出时的关键字;
- scope: 域。代码片适用的「语言模式」；全局代码片」才能使用。
- body：主体。代码片的「布局与控制」；
- description：描述。描述代码片的基本功能，并显示在 IntelliSense 中
  
#### Prefix
- 可以设置多个关键字，呼出同一个代码片
``` "Prefix": ["header", "stub", "copyright"],
```
这三个关键字呼出同一个代码片

#### body
- Tabstops：制表符 $0, $1, $2 实现光标的跳转
- Placeholders：占位符 ${1：direction} direction 占位并作为输入的引导信息
- Choice：可选项 ${1|male, female, other|} 当光标跳转到该位置的时候，用户将会被提供多个值,以供选择。
- Variables：变量 $name 或 ${name:default}， 以提取相关的信息
  可以使用的「Variable」： 
  TM_CURRENT_LINE，M_CURRENT_WORD，TM_LINE_INDEX，TM_LINE_NUMBER，TM_FILENAME， TM_FILENAME_BASE，TM_DIRECTORY，TM_FILEPATH，TM_SELECTED_TEXT,RELATIVE_FILEPATH，CLIPBOARD，CURRENT_YEAR， CURRENT_MONTH，CURRENT_DATE，CURRENT_HOUR， BLOCK_COMMENT_START， BLOCK_COMMENT_END，LINE_COMMENT   

例如:选择数字1,然后输入 frac 或 \frac, 会得到 \frac{1}{2} 的 snippets 如下:
```
	"frac":{
		"prefix": ["frac","\\frac"],
		"body": ["\\frac{$TM_SELECTED_TEXT}{$2:2}"],
		"description": "frac"
	}
```
#### 正则表达式 

snippet 可以使用正则表达式 

## HyperSnips 

vim-snippets 支持两种格式的规则定义

- snipMate format: 规则文件位于 vim-snippets/snippets 目录下
- UltiSnips format: 规则文件位于 vim-snippets/UltiSnips 目录下
  
snipMate 与 UltiSnips 的对比, snipMate 看上去更简洁一些，但UltiSnips支持 Python。
因此,安装完UltiSnips2后, Vim 会出错. 
vim --version | grep python

HyperSnips 将 Vim Ultisnips 的大部分功能搬到了VSCode上。并用 JavaScript 重写了 Python 的部分程序, 使Ultisnip 的大部分能用于Vscode. 

### 代码片设置文件

- VScode 中 通过快捷键「Ctrl + Shift + P」打开命令窗口（All Command Window），输入「hsnips」，就可以设置相应的 snippets.
- $HOME/Library/Application Support/Code/User/hsnips/(language).hsnips

基本结构如下:

```
global
// JavaScript code
endglobal

context expression
snippet trigger "description" flags
body
endsnippet

```

其中 context 确定snippet在什么语言环境起做用, trigger 是触发器,  flags 是触发方式. 
- 默认是按下tab时触发代码段body展开,
- A：自动展开,触发器匹配后立即激活
- i: 词内展开,默认触发器仅在前面带有空格字符时才匹配触发。如果设置为 i，则不管前面的字符如何，都会触发
- w: 单词边界展开。使用此选项时，触发器将在单词边界处匹配

```
snippet dategreeting "Gives you the current date!" A
Hello from your hsnip at ``rv = new Date().toDateString()``!
endsnippet 

```
- 触发器为 dategreeting, 在用户输入这个内容时触发body展开.
- body 是 Hello from your hsnip at ``rv = new Date().toDateString()``! . 其中"new Date()" 返回当天日期, 通过"toDateString()" 确定日期格式串, 再返回给 "rv"
- JavaScript片段得使用四个 \``  \``括起来, 
- body 中用到的三个变量
	- rv: 块的返回值，该返回值 将会替代 ````中的内容
	- t: 每个tab 中输入的内容，比如 $1、$2中的内容，可以使用它来动态更改代码段内容。需要注意从 t[0] 开始索引
	- m: 如果 trigger 使用正则表达式（regular expressio），m 包含每个正则表达式每块的匹配内容，m[0] 开始索引

使用实例：

- `$D` $\to$ `$\displaystyle   $`
- `$B` $\to$ `$$  $$`
- `...` $\to$ `\cdots` for $\cdots  $
- `,,,` $\to$ `\vdots` for $ \vdots $
- `:::` $\to$ `\ddots` for $ \ddots $
- `int` $\to$ `\int`for $ \int $
- `intd` $\to$ `\int_{}^{}`for $ \int_{1}^{2} $
- `iint` $\to$ `\iint ` for $ \iint  $
- `iiint` $\to$ `\iiint ` for $ \iiint $
- `oint` $\to$ `\oint ` for $ \oint $
- `oiint` $\to$ `\oiint ` for $ \oiint  $
- `lim` $\to$ `\lim ` for $ \lim  $
- `limd` $\to$ `\lim_{ \to  } ` for $ \lim_{ x\to 0 }  $
- `sum` $\to$ `\sum ` for $ \lim_{ \to }  $
- `sumd` $\to$ `\sum_{}^{} ` for $ \sum_{1}^{n}  $
- `oo` $\to$ `\infty ` for $ \infty  $
- `oop` $\to$ `+\infty ` for $ +\infty  $
- `oom` $\to$ `-\infty ` for $ -\infty  $
- `DD` $\to$ `\frac{\mathrm{d}}{\mathrm{d}} ` for $ \frac{\mathrm{d}}{\mathrm{d}}  $
- `PP` $\to$ `\frac{\partial }{\partial } ` for $ \frac{\partial }{\partial }  $
- `drm` $\to$ `\mathrm{\,d}  ` for $ \mathrm{\,d}  $
- `ptl` $\to$ `\partial ` for $ \partial  $
- `ra;` $\to$ `\rightarrow ` for $ \rightarrow  $
- `ia;` $\to$ `\implies ` for $ \implies  $
- `fa;` $\to$ `\iff  ` for $ \iff   $
- `to;` $\to$ `\to   ` for $ \to    $
- `>=` $\to$ `\geq   ` for $ \geq     $
- `<=` $\to$ `\leq    ` for $ \leq      $
- `<<` $\to$ `\ll   ` for $ \ll      $
- `>>` $\to$ `\gg   ` for $ \gg      $
- `>~` $\to$ `\gtrsim  ` for $ \gtrsim     $
- `<~` $\to$ `\lesssim  ` for $ \lesssim    $
- `sq` $\to$ `\sqrt{}  ` for $ \sqrt{2}    $ * 带选择功能
- `RR` $\to$ `\mathbb{R}  ` for $ \mathbb{R}    $ 
- `CC` $\to$ `\mathbb{C}  ` for $ \mathbb{C}    $ 
- `ZZ` $\to$ `\mathbb{Z}  ` for $ \mathbb{Z}    $ 
- `RR+` $\to$ `\mathbb{R}_+  ` for $ \mathbb{R}_+    $ 
- `RRn` $\to$ `\mathbb{R}^{n}  ` for $ \mathbb{R}^{n} $ 
- `RR3` $\to$ `\mathbb{R}^{3} ` for $ \mathbb{R}^{3}$ 
- `CCn` $\to$ `\mathbb{C}^{n}  ` for $ \mathbb{C}^{n} $ 
- `CC2` $\to$ `\mathbb{C}^{2} ` for $ \mathbb{C}^{2}$  used in QM  
- `sin` $\to$ `\sin ` for $ \sin $ 
- `sinh` $\to$ `\sinh ` for $ \sinh $ 
- `arcsin` $\to$ `\arcsin ` for $ \arcsin $ 
- `curl` $\to$ `\mathrm{Curl.} ` for $\mathrm{Curl.} $
- `div` $\to$ `\mathrm{Div.} ` for $ \mathrm{Div.} $ 
- `grad` $\to$ `\mathrm{Grad.} ` for $ \mathrm{Grad.} $  
- `==` $\to$ `\equiv ` for $ \equiv $  
- `!=` $\to$ `\not = ` for $ \not = $  
- `OO` $\to$ `\cdot ` for $ \cdot $
- `~~` $\to$ `\sim ` for $ \sim $
- `NN` $\to$ `\cap ` for $ \cap $
- `UU` $\to$ `\cup ` for $ \cup $
- `II` $\to$ `\in` for $ \in $
- `SS` $\to$ `\subset` for $ \subset  $
- `XX` $\to$ `\times` for $ \times $
- `opo` $\to$ `\oplus ` for $ \oplus $
- `oxo` $\to$ `\otimes` for $ \otimes $
- `omo` $\to$ `\ominus ` for $ \ominus  $ 
- `opro` $\to$ `\propto ` for $ \propto  $ 
- `nbl` $\to$ `\nabla ` for $ \nabla  $  非常重要
- `nabla` $\to$ `\nabla ` for $ \nabla  $  非常重要
- `n;` $\to$ `\nabla ` for $ \nabla  $  非常重要
- `abs` $\to$ ` \left|\right| ` for $  \left|\right|  $  
- `||` $\to$ ` \left|\right| ` for $  \left|\right|  $  
- `alpha` $\to$ ` \alpha ` for $  \alpha  $ 
- `a;` $\to$ ` \alpha ` for $  \alpha  $ 
- `a;a` $\to$ ` \alpha ` for $  \alpha a  $ 
- `a;n` $\to$ ` \alpha ` for $  \alpha_n  $ 
- `b;` $\to$ ` \beta ` for $  \beta  $ 
- `c;` $\to$ ` \chi ` for $  \chi $ 
- `d;` $\to$ ` \delta ` for $  \delta $ 
- `D;` $\to$ ` \Delta ` for $  \Delta $ 
- `p;` $\to$ ` \psi ` for $  \psi $ 
- `P;` $\to$ ` \Psi ` for $  \Psi $ 
- `v;` $\to$ ` \varphi ` for $  \varphi $ 
- `V;` $\to$ ` \Phi ` for $  \Phi $ 
- `w;` $\to$ ` \omega ` for $  \omega $  not use o;
- `W;` $\to$ ` \Omega ` for $  \Omega $ 
- `mat22` $\to$ `\begin{matrix}   &  \\   &  \\ \end{matrix} ` for  matrix $  2\times 2 $ 
- `bmat22` $\to$ `\begin{bmatrix}   &  \\   &  \\ \end{bmatrix} ` for  bmatrix $  2\times 2 $ 
- `pmat22` $\to$ `\begin{pmatrix}   &  \\   &  \\ \end{pmatrix}  ` for  pmatrix $  2\times 2 $ 
- `vmat22` $\to$ `\begin{vmatrix}   &  \\   &  \\\end{vmatrix}`  for vmatrix $  2\times 2 $ 
-  `cv2` $\to$ `begin{bmatrix}   \\   \\ \end{bmatrix}` for column vector $ 
-  `rv2` $\to$ `\begin{bmatrix}   &  \\ \end{bmatrix}` for row vector $ 
-  `//` $\to$ ` \frac{}{} ` for $  \frac{1}{2} $ * 带选择功能
-  `1/` $\to$ ` \frac{1}{} ` for $  \frac{1}{} $
-  `a/` $\to$ ` \frac{a}{} ` for $  \frac{a}{} $
-  `ab/` $\to$ ` \frac{ab}{} ` for $  \frac{ab}{} $
-  `pw` $\to$ ` ^{} ` for $ x^{n} $ 
-  `sr` $\to$ ` ^{2} ` for $ x^{2} $ 
-  `th` $\to$ ` ^{3} ` for $ x^{3} $ 
-  `dag` $\to$ `^\dagger ` for $ F^{\dagger} $ 
-  `coj` $\to$ `^* ` for $ F^* $ 
-  `inv` $\to$ `^{-1} ` for $ F^{-1} $ 
-  `trs` $\to$ `^T ` for $ F^T $ 
-  `exp` $\to$ `\mathrm{e}^{} ` for $ \mathrm{e}^{2} $ * 带选择功能
-   `sub` $\to$ ` _{} `for $ x_{n} $ 
-   `a1` $\to$ ` a_1`for $ a_1 $ 
-   `a12` $\to$ ` a_{12}`for $ a_{12} $ 
-   `ann` $\to$ ` a_n`for $ a_n $ 
-   `ann1` $\to$ `a_{n1}`for $ a_{n1} $ 
-   `annmm` $\to$ `a_{nm}`for $ a_{nm} $
-   `aiijj` $\to$ `a_{ij}`for $ a_{ij} $
-   `asuba;` $\to$ `a_{\alpha}`for $ a_{\alpha} $
-   `d;nnmm` $\to$ `\delta_{nm}`for $ \delta_{nm} $
-   `rnn` $\to$ ` r_n`for $ r_n $ 
-   
-   `ahat` $\to$ ` \hat{a}`for $ \hat{a} $ 
-   `Fhat` $\to$ ` \hat{F}`for $ \hat{F} $ 
-   `avec` $\to$ ` \vec{a}`for $ \vec{a} $ 
-   `abar` $\to$ ` \overline{a}`for $ \overline{a} $ 
-   `hbar` $\to$ ` \hbar`for $ \hbar $ 
-   `arm` $\to$ ` \mathrm{a}`for $ \mathrm{a} $
-   `a;hat` $\to$ ` \hat{\alpha }`for $ \hat{\alpha }$
-   

$$
\begin{vmatrix}   &  \\   &  \\ \end{vmatrix}
$$
 $\displaystyle \subset     $