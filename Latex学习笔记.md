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