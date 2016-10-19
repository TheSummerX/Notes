# Markdown

> 目录

> * [一、简介](#1)
> * [二、Markdown Syntax （语法）](#2)
>   * [1. 标题 Header ](#21.)
>   * [2. 段落 Paragraph ](#22.)
>   * [3. 换行 New Line ](#23.)
>   * [4. 代码区块 Code Block ](#24.)
>   * [5. 区块引用 Blockquote ](#25.)
>   * [6. 强调 Strong&Emphasis ](#26.)
>   * [7. 列表 List ](#27.)
>   * [8. 分割线 ](#28.)
>   * [9. 链接 Link ](#29.)
>   * [10. 图片 Image ](#210)
>   * [11. 反斜线 Backslash `\` （HTML 代码 `&#92;`） ](#211)
>   * [12. 反引号 Back-tick '\`' （HTML 代码 `&#96;`） ](#212)
>   * [13. 其它](#213)
> * [三、Markdown 工具](#3)
> * [参考及外链](#4)

<h3 id="1">一、简介</h3>

Reference：[Statement by creator John Gruber](https://daringfireball.net/projects/markdown/)  
Tutorial：[Markdown Tutorial](http://www.markdowntutorial.com/)

- Markdown 是一种轻量级标记语言，**“使用易读易写的_纯文本_格式编写文档，然后转换成有效的XHTML（或者HTML）文档。**
  - 它吸收了很多在_电子邮件_中已有的纯文本标记特性。
  - 它最重要的设计在于**易读性**。
- Markdown 具有良好的跨平台使用性能，许多网站都使用它，包括：
  - Apollo 
  - GitHub
  - Reddit
  - Stack Overflow
- Markdown 能方便清晰地组织你的电子邮件，只需要一些工具（Markdown Here,Airmail，etc. ）。

<h3 id="2">二、Markdown Syntax （语法）</h3>
Markdown 主要分为：**标题、段落、换行、代码区块、区块引用、强调、列表、分割线、链接、图片、反斜线'\'、反引号'`'。**

<h5 id="21.">1. 标题 Header </h5> 
两种标题风格：
  - SeText风格： 在标题行下一行使用多个`=`和`-`分别表示一、二级标题；
  - Atx风格： 在行首使用`#`表示标题，符号`#`的数量（支持**1-6**个）表示标题等级；
<h5 id="22.">2. 段落 Paragraph </h5> 
独立段落需要前后有空行；
<h5 id="23.">3. 换行 New Line </h5> 
  - Markdown最终生成HTML文件，浏览器会根据可用空间自动换行，而忽略文本输入的换行；
  - **强制换行** 
    - Hard Break 用空行来实现换行，空行会显示；
    - Soft Break 在行尾插入**至少2**个空格（引用内换行插入空格后不必回车即文本编辑时不必换行）；
<h5 id="24.">4. 代码区块 Code Block </h5> 
  - 代码区块需要独立成段落
    - 在每行首添加**4个空格或1个制表符**；
    - 首尾两行连用3个back-tick反引号 \`\`\` ，可以支持语法高亮syntax hilighting;  
    Syntax highlighting需在块首行反引号后添加语言名，如：
  > Code:  
  >
  >  \```python  
  >  s = "Python"  
  >  print s  
  >  \```
  
  Output:
  
    ```python
    s = "Python"
    print s
    ```
  - 代码区块可用保留所有的空格、换行、缩进等；
<h5 id="25.">5. 区块引用 Blockquote </h5> 
  - 引用区块独立成段落，在引用开头添加`>`或引用部分每一行都添加均可；
  - **嵌套引用** 根据嵌套层次添加右尖括号`>`的数量在引用开头或每一行行首即可；
<h5 id="26.">6. 强调 Strong&Emphasis </h5> 
  - *强调*或_强调_ 斜体效果，在被强调部分前后添加`*`或`_`；
  - **加重强调**或__加重强调__ 加粗效果，在被强调部分前后添加`**`或`__`；
  - ~~删除线~~ 在删除线文本前后添加`~~`；
<h5 id="27.">7. 列表 List </h5> 
  - 无序列表 在行首添加`-`、`+`或`*`；
  - 有序列表 在行首添加`.`并给出数字（自动给定序号故任意数字均可），如“1. ”；
  - **列表嵌套** 相对上一层级的列表多缩进至少1个空格；
<h5 id="28.">8. 分割线 </h5> 
  - 在单独一行输入3个或以上的`-`，`_`或`*`；
  - 可以在符号间添加任意空格；
<h5 id="29.">9. 链接 Link </h5> 
  - Inline 行内式： 
  ```
    [链接文字](链接地址 "链接标题")
  ```
  - Reference 参考式：
  ```
    [链接文字][链接引用标签]
  ``` 
  再在段落后或文档尾独立成段落添加信息：
  ```
    [链接引用标签]:链接地址 "链接标题"
  ```
<h5 id="210">10. 图片 Image </h5> 
图片类似链接，只需要在行首再添加符号`!`标识即可；
<h5 id="211">11. 反斜线 Backslash `\` （HTML 代码 `&#92;`） </h5> 
用于反转义符号为普通符号文本；
<h5 id="212">12. 反引号 Back-tick '\`' （HTML 代码 `&#96;`） </h5> 
用于标记；
<h5 id="213">13. 其它</h5>
  - 尖括号链接 直接用尖括号`<``>`将链接括起来；
  - 列表（非Traditional Markdown）  
    - 用`|`表示表格纵向边界，表头和表内容用`-`隔开；  
    - 可用`:`设置对齐，两边都有`:` 表示居中，默认左对齐；
    - 页内引用跳转（目录跳转等）
      - [跳转文字](#anId)  
        <h2 id="anId">跳转目标</h2>  
        点击跳转文字跳转，h2表示2级标题，anId为自定义跳转标识
      - 定义锚 <span id="anId">跳转目标</span>  
        [跳转文字](#anId)

<h3 id="3">三、Markdown 工具</h3>
  - Markdown 的插件、工具扩展，如:
    - **Markdown.pl** 创始人_Gruber_的Perl脚本，用于转换markdown语法编辑的内容成有效的、结构良好的XHTML或HTML内容，并实现尖括号（<）和‘&’号的**字符实体引用**；
    - [**Markdown Here**](http://markdown-here.com/) 写一封cool e-mail；
    - **ReText** An implementation for Markdown and reStructuredText；
  - Markdown 编辑器：
    - **Cmd Markdown** 支持实时同步预览，区分写作与阅读模式；
    - **Dillinger.io** 在线Markdown编辑器，提供实时预览及到Github和Dropbox的拓展链接；
    - **Notepag** 也是一个在线Markdown编辑器，提供实时预览；
    - **简书** 在线Markdown编辑器，同时也是阅读社区，支持实时预览，提供分享；
    - **Pagedown**  一个Javascript写的 "WYSIWYM"(所见即所得)Markdown编辑器 (来自 StackOverflow)；
    - **Mou** 一个Mac OS X上的Markdown编辑器；
  - Markdown 实现（解析器和生成器）： 
    - C
      - **Sundown** 
      - **peg-markdown** 使用了PEG (parsing expression grammar)
    - Java
      - **MarkdownJ** The pure Java port of Markdown
    - Ruby
      - **Maruku** A pure-Ruby Markdown-superset interpreter
      - **kramdown** Fast, pure Ruby, using a strict syntax definition and supporting several common extensions
    - Others
      - **Markdown in Python** A Python implementation of Markdown
      - **MarkdownSharp** A slightly modified C# implementation of the Markdown markup language. Developed and used by Stack Overflow

<h3 id="4">参考及外链</h3>
- [Markdown语法说明](http://wowbuntu.com/markdown/)
- [简单的Markdown指南](http://www.applecho.com/markdown-guide/)
- [Markdown Wiki](http://xbeta.org/wiki/show/Markdown/)
- [A Markdown tutorial](http://www.simpleeditions.com/59001/markdown-an-introduction/)
- [Multi Markdown](http://fletcherpenney.net/multimarkdown/)(引入更多标记特性和输出选项的改进版Markdown)
