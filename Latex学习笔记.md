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
- JavaScript片段得使用四个 `` ... ``括起来, 

这是一个自动对后数字转下标的 snippet

```
	snippet `(?<=[A-Za-z])(\d)` "auto subscript" iA
	_``rv = m[1]``
	endsnippet
```

- 使用二个 ` ... ` 括起来的个正则表达式型的触发器,
- 其中的两个() () 号代表它由有两个部分组成,  
- [A-Za-z]代表可匹配字符所在的区域, [^ABC]代表不可匹配字符所在的区域
- (?=xxxxx),正向预搜索,
- (?<=xxxxx),反向预搜索,
- \d 匹配从0到9的一个数字,
- \w 匹配字母，数字或下划线字符 (A-Z,a-z,0-9,_) 中任意一个
  
\[  \]