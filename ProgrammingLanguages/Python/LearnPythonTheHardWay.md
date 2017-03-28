# Learn Python The Hard Way

_By Zed A. Shaw,Third Edition.Wang Weiwei Translated._

---

The free HTML version of the book is available at [learnpythonthehardway.org](http://learnpythonthehardway.org/book/ "learnpythonthehardway.org").

---

> ## Table of Contents 目录
> - Introduction: The Hard Way Is Easier
> - [Exercise 0: The Setup 准备](#0)
> - [Exercise 1: A Good First Program 第一个程序(简单的打印 Simple Print)](#1)
> - [Exercise 2: Comments And Pound Characters 注释](#2)
> - [Exercise 3: Numbers And Math 数学计算](#3)
> - [Exercise 4: Variables And Names 变量和命名](#4)
> - [Exercise 5: More Variables And Printing 更多变量和打印(格式化字符串 format string)](#5)
> - [Exercise 6: Strings And Text 字符串和文本](#6)
> - [Exercise 7: More Printing 更多打印](#7)
> - [Exercise 8: Printing, Printing 打印，打印](#8)
> - [Exercise 9: Printing, Printing, Printing 打印，打印，打印](#9)
> - [Exercise 10: What Was That? 那是什么(转义` \ `)](#10)
> - [Exercise 11: Asking Questions 提问(`input() raw_input()`)](#11)
> - [Exercise 12: Prompting People 提示别人](#12)
> - [Exercise 13: Parameters, Unpacking, Variables 参数、解包和变量](#13)
> - [Exercise 14: Prompting And Passing 提示和传递](#14)
> - [Exercise 15: Reading Files 读取文件](#15)
> - [Exercise 16: Reading And Writing Files 读写文件](#16)
> - [Exercise 17: More Files 更多文件操作](#17)
> - [Exercise 18: Names, Variables, Code, Functions 命名、变量、代码和函数](#18)
> - [Exercise 19: Functions And Variables 函数和变量](#19)
> - [Exercise 20: Functions And Files 函数和文件](#20)
> - [Exercise 21: Functions Can Return Something 函数返回值](#21)
> - [Exercise 22: What Do You Know So Far? 现在学到了什么](#22)
> - [Exercise 23: Read Some Code 阅读代码](#23)
> - [Exercise 24: More Practice 更多练习](#24)
> - [Exercise 25: Even More Practice 更多实践](#25)
> - [Exercise 26: Congratulations, Take A Test! 可以考试](#26)
> - [Exercise 27: Memorizing Logic 记住逻辑关系](#27)
> - [Exercise 28: Boolean Practice 布尔表达式](#28)
> - [Exercise 29: What If if语句](#29)
> - [Exercise 30: Else And If else和if](#30)
> - [Exercise 31: Making Decisions 做出决定](#31)
> - [Exercise 32: Loops And Lists 循环和列表](#32)
> - [Exercise 33: While Loops while循环](#33)
> - [Exercise 34: Accessing Elements Of Lists 访问列表元素](#34)
> - [Exercise 35: Branches and Functions 分支和函数](#35)
> - [Exercise 36: Designing and Debugging 设计和调试](#36)
> - [Exercise 37: Symbol Review 复习符号](#37)
> - [Exercise 38: Doing Things To Lists 列表操作](#38)
> - [Exercise 39: Dictionaries, Oh Lovely Dictionaries 字典](#39)
> - [Exercise 40: Modules, Classes, And Objects 模块、类和对象](#40)
> - [Exercise 41: Learning To Speak Object Oriented 面向对象](#41)
> - [Exercise 42: Is-A, Has-A, Objects, and Classes 对象、类和从属](#42)
> - [Exercise 43: Gothons From Planet Percal #25 基本面向对象分析和设计](#43)
> - [Exercise 44: Inheritance Vs. Composition 继承和合成](#44)
> - [Exercise 45: You Make A Game 制作游戏](#45)
> - [Exercise 46: A Project Skeleton 项目骨架](#46)
> - [Exercise 47: Automated Testing 自动化测试](#47)
> - [Exercise 48: Advanced User Input 用户输入](#48)
> - [Exercise 49: Making Sentences 创建句子](#49)
> - [Exercise 50: Your First Website 网站](#50)
> - [Exercise 51: Getting Input From A Browser 浏览器输入](#51)
> - [Exercise 52: The Start Of Your Web Game 创建Web游戏](#52)
> - [Advice From An Old Programmer 老程序员的建议](#53)
> - [Next Steps 接下来的路](#54)

---

Python是一种解释型、面向对象、动态数据类型的高级程序设计语言。
Python由Guido van Rossum于1989年底发明，第一个公开发行版发行于1991年。
像Perl语言一样, Python 源代码同样遵循 GPL(GNU General Public License)协议。

---

<h2 id="0">Exercise 0 : The Setup</h2>
- Have Python installed.
- Prepare your text editor.(文本编辑器)
- Run Python in Terminal:(可运行Python)
  ```sh
  $ python
  >>>
  ```

  Use `Ctrl-D` to exit python.(`Ctrl-D`退出)
- Command Line Crash Course(命令行快速入门)[Crash Course Online](https://learnpythonthehardway.org/book/appendixa.html "Crash Course Online")

<h2 id="1">Exercise 1: A Good First Program</h2>
- `# !/usr/bin/env python` indicate the OS to search python in env and use the interpreter. ((帮助内核)在环境设置中查找Python解释器并使用) Python的`Shebang`语句，只需用于直接被执行的文件头。
- `# -*- coding:utf-8 -*-` indicate the interpreter to access the code with utf-8.(仅对解释器)
    _注意将编辑器编码也设置为UTF-8_
- Use a comma(`,`) at the end of the "print" line,making output on one line.(`,`打印在同一行)
- Use a `/r` at the end of the "print" line,making output on one line and update output rather than simply output all results or data.(`/r`打印的结果更新，比如进度百分比)
- Use different quotes to differ.(打印符号和打印引号分别使用单、双引号避免程序混淆)
- `$ python prog.py` to run python program.If any error occur,a `^` will show you the error position.

<h2 id="2">Exercise 2: Comments And Pound Characters</h2>
- `#` (octothorpe,or pound character) to comment out contents after it.
  * inline comment(行内注释) 需要至少两个空格，`#`后也需要空格；
  * multiple line comment(多行注释) 每行加`#`。
- **Read code backward** will help.
  > It's a trick to make your brain not attach meaning to each part of the code, and doing that makes you process each piece exactly. This catches errors and is a handy error-checking technique.
- 代码行保持80个字符内，确实需要时，可：
  * ` \ ` 行尾反斜杠，连接两行；
  * ` () ` Python会将括号内内容软性连接。
    _`print`语句中连接的两行字符串分别需要引号。_

<h2 id="3">Exercise 3: Numbers And Math</h2>
- `*` `/` `+` `-`
- `%` Modulo Operation.(取模：计算整数商时向负无穷舍入，而求余(Remainder Operation)向0舍入)
- `//` Floor Division.(向下取整除法)
- `*= /= += -= %=` 类似其他语言。**没有自增自减`++ --`。**
- The order of operations:an acronym called **PEMDAS**,which stands for Parentheses Exponents Multiplication Division Addition Subtraction.(括号指数乘除加减)
- Floating point numbers:
  * 整型运算结果为整型，浮点型运算结果为浮点型；
  * `round(number[, ndigits])` 浮点数输出，精度控制。

<h2 id="4">Exercise 4: Variables And Names</h2>
- `_`(underscore character) between words in variable names.
- Data types:
  * numbers:
    + int(有符号整数)
    + long(长整数) : 用`L`表示，也可用八进制或十六进制。
    + float(浮点数)
    + complex(复数) : `a + bj`其中`a b`为浮点数。
  * string(字符串) ： 用任一对引号 ` ' " `表示。无字符类型，视作一个长度的字符串。
  * bool(`True False`)
  * `None`(空值)
  * list(列表) ： 方括号`[]`内，逗号分隔。
  * tuple(元组) ： 括号`()`内，逗号分隔，不能更新。
  * dict(字典) ： 哈希表型，由键-值对组成。元素无序。花括号`{}`内，逗号分隔。
    ```python
    dict = {}
    dict[key] = value
    dict = {key1 : value1, key2 : value2, ... }
    ```

- Python是动态语言，定义变量不指定类型，可重赋值改变数据类型。

<h2 id="5">Exercise 5: More Variables And Printing</h2>
- `%` format string operator(字符串格式化输出)
- `%%` 转义'%'
- `-` left align(左对齐)(占位宽，见示例)
- `+` 显示正负符号
- `.` 浮点数小数精度
- ` %c  %s  %d  %u  %x  %f  %r ` formatters (字符，str()，有符号十进制整数，无符号十进制整数，十六进制数，浮点数，任何(`%s`会自动转化为字符串类型，`%r`会显示原始数据(Raw Representation)多用于测试))
- multiple formation(多个格式化) ` ()  , `Use parentheses and comma.
  ```python
  str1 = 'World'
  print 'Hello %s !' % str1
  print 'Name: %6s Age: %-6s Height: %6.2f' %("Jack", 19, 1.8300)
  ```

<h2 id="6">Exercise 6: Strings And Text</h2>
- ` ''  "" ` single quotes or double.
- `+` concatenate string(连接字符串)
- `*` repeat(重复，如`print 'a'*2`)
- `[]` 通过索引获取字符，如`a[0] b[2:4]`(注意给定范围时，前include后exclude)
- `in   not in` 成员运算符，判定字符串(不)包含给定字符则返回`True`
- `r/R` 原始字符串，用在第一个字符串引号前，表明字符串完全原始输出。(Raw Data)

<h2 id="7">Exercise 7: More Printing</h2>
- ` %  *  , ` Format,Repeat,OneLineOutput

<h2 id="8">Exercise 8: Printing, Printing</h2>
- `%r` Raw Representation(调用repr)用于调试，会选择可接受的最有效方式输出。

<h2 id="9">Exercise 9: Printing, Printing, Printing</h2>
- `"""` The Three Double Quotes(三引号，用于多行string)
- `\n` Line Feed(换行，即<LF>，与<CR>回车Carriage Return区别)

<h2 id="10">Exercise 10: What Was That?</h2>
- ` \ ` Escape Sequences(转义序列)
  * `\\  \'  \"` Backslash, Single quote, Double quotes.
  * `\a  \b` ASCII bell(BEL), ASCII backspace(BS).
  * `\n  \t  \r` ASCII linefeed(LF), Horizontal Tab(TAB), Carriage return(CR).
  * `\N{name}` (Unicode only)Character named 'name' in Unicode database.
  * `\uxxxx  \Uxxxxxxxx` (u" string only)Character with 16/32-bit hex value xxxx/xxxxxxxx.
    + a u' string is a must.eg: `u'\u0080'`
  * `\ooo  \xhh` Character with octal/hex value oo/hh.

<h2 id="11">Exercise 11: Asking Questions</h2>
- `raw_input() (Function in module __builtin__)` 接受任何类型的输入，返回string类型；
- `input() (Function in module __builtin__)` 接受合法的Python表达式(如字符串需要引号)，返回对应的数据类型。
  * `Consider using the raw_input() function for general input from users.`
  * 查看`Built-in Functions`可知，`input()`为调用`raw_input()`后再调用`eval()`处理。

<h2 id="12">Exercise 12: Prompting People</h2>
- `raw_input()` 可在括号内给出输出的提示。(提示是print内容，需要引号，可用变量定义便于调用和修改)
- `pydoc` the Python documentation tool.(查看Python doc.)

<h2 id="13">Exercise 13: Parameters, Unpacking, Variables</h2>
- `Module` 类似**Library**
- `argv` Arguement Variable参数变量，记录运行时输入的参数并使用，string类型。
- 将` argv `解包`( unpack )`，用于通过`argv`同时给多变量赋值等。

<h2 id="14">Exercise 14: Prompting And Passing</h2>
- `prompt` 提示

<h2 id="15">Exercise 15: Reading Files</h2>
- `file (Class in module __builtin__)`
- `open(name[, mode[, buffering]]) (Function in module __builtin__)` 打开文件，使用file()类型，返回file object。
  * 打开模式有：
    + `'r' 'w' 'a'` 读(默认)，写，追加(写和追加会新建不存在的文件，写会先清空文件)；
    + `'b' '+'` 二进制文件，同时读写。
  * 寄存。`0`(默认)关闭，`1`开启，大于`1`的数表明寄存区大小，负数寄存区默认大小。
- `close() (Method in class file)` 记得关闭文件。

<h2 id="16">Exercise 16: Reading And Writing Files</h2>
- `read() (Method in class file)` 读取文件内容；
- `readline() (Method in class file)` 读取文本文件的一行；
- `truncate() (Method in class file)` 清空文件；
- `write() (Method in class file)` 写入文件。

<h2 id="17">Exercise 17: More Files</h2>
- `open(file_name).read()` 打开后读取并关闭文件；
- `from os.path import exists` `exists`函数判断文件是否存在；
- `len() (Function in module __builtin__)` 返回长度。

<h2 id="18">Exercise 18: Names, Variables, Code, Functions</h2>
- 命名规范：
  * 包、模块：全小写，避免使用下划线；
  * 类：`CamelCase`命名风格，内部类可用下划线开头；
  * 方法、函数：下划线分隔的小写；
  * 常量：下划线分隔的大写；
  * 变量(类、实例、局部、全局)、参量(方法、函数)：下划线分隔的小写；
  * 参量名与保留字冲突时，在末尾加下划线；
  * `Internal` 模块内可用的、类内保护的、类内私有的用单下划线开头。
- > To 'run', 'call', 'use' a function all mean the same thing.

- `def` 定义函数，声明函数名和参量：
  ```python
  def function_name(*arguments):
      arg1, arg2, arg3 = arguments
      ...


  ...
  ```

  * 参数可用`*arguments`，表示存储所有参量到列表`arguments`，后在函数定义中具体声明变量；
  * `:` 开始函数定义；
  * 函数定义部分缩进4个空格；
  * 函数空行：
    + 模块级函数、类定义在开始、完毕空2行；
    + 类成员函数间空1行；
    + 函数中空行分隔代码逻辑块，但避免大量连续空行。

<h2 id="19">Exercise 19: Functions And Variables</h2>
- Python不限定变量类型，函数调用时可接受数字、变量、表达式或它们的组合。

<h2 id="20">Exercise 20: Functions And Files</h2>
- `seek(offset[, whence]) (Method in class file)` 文件内位置跳转：
  * `offset`指定跳转的字节位置；
  * `whence`指定`offset`的相对位置，默认为`0`表示相对文首，`1`相对当前光标处，`2`相对文末；
  * 文件以`text`模式打开时，`offset`只能是`tell()`返回值；
  * 并不是所有文件都支持跳转。

<h2 id="21">Exercise 21: Functions Can Return Something</h2>
- `return` 用于返回值

<h2 id="22">Exercise 22: What Do You Know So Far?</h2>
- review
- Some rest between hardworking time, like 15 minutes work then a break.
  > Doing a boring, mindless memorization exercise helps you focus on a goal and know the purpose of all your efforts.
  > There is no failure, only trying.
  > Giving your brain a rest will help you learn faster with less frustration.

<h2 id="23">Exercise 23: Read Some Code</h2>
- read source codes in real projects
> Benefit from getting exposure and seeing how things look.

<h2 id="24">Exercise 24: More Practice</h2>

<h2 id="25">Exercise 25: Even More Practice</h2>
- `split([sep[, maxsplit]]) (Method in class bytearray)` 用法`B.split()`，返回B的区域列表，sep为分隔符(默认ASCII whitespace characters(空格、TAB、回车等)为分隔符)，最多分为maxsplit项(Return a list of sections in B)
- `pop([index]) (Method in class bytearray)` 用法为`B.pop([index])`，移除并返回B中的某项目，默认最后一项(Remove and return a single item from B)
- `sorted(iterable[, cmp, key, reverse]) (Function in module __builtin__)` 返回新的排序列表：
  * `iterable` 指定对象(迭代器，一次返回其一个成员)，包括：
    + 序列类型：list(列表)，str(字符串)，tuple(元组)；
    + dict(字典)，file(文件)；
    + 自定义的包含`__iter__()`或`__getitem__()`方法的类的对象。
  * `cmp` 指定比较函数，默认值为`None`；
  * `key` 指定从元素中提取的比较的关键字，默认值为`None`；
  * `reverse` Bool值，指定逆序输出，默认值为`False`。

<h2 id="26">Exercise 26: Congratulations, Take A Test!</h2>

<h2 id="27">Exercise 27: Memorizing Logic</h2>
- ` and `` or `` not ` 与、或、非
- `!=  ==` 不等、等

<h2 id="28">Exercise 28: Boolean Practice</h2>
- `0 == False`
- `'2' and '2'` 返回`'2'`，返回第一参量表示True, 第二表示False。

<h2 id="29">Exercise 29: What If</h2>
- `if expression:` Python的if语句，判定表达式不要括号，除非表达式太长需要括号软性连接多行。

<h2 id="30">Exercise 30: Else And If</h2>
- `elif expression:` 多条件，当某一条件满足时其他条件不再判断。
- `else:` 否则。

<h2 id="31">Exercise 31: Making Decisions</h2>

<h2 id="32">Exercise 32: Loops And Lists</h2>
- `list` 列表(`class list in module __builtin__`)
  * `list()` 创建新空列表；
  * `list(iterable)` 用迭代器iterable的内容创建列表；
  * `list_name[index]` 列表切片(list slicing)，取某个值或某范围值：
    + `L[0]` 列表L的起始项；
    + `L[2:4]` 列表的序号2到4项(不含序号4项)；
    + `L[-2]` 列表倒数第2项(负索引：先索引值加列表条目数之和，判断对应索引条目是否可操作)；
    + `L[:]` 列表的每一项，可用于复制列表等。
  * `append(object)` 用法`L.append()`，追加object在列表尾；
  * `__sizeof__()` 用法`L.__sizeof__()`，比特大小。
- `[object1, object2, object3]` 创建列表并初始化，需要赋值给一个声明的列表；
- `range([start, ]stop[, step]) (Function in module __builtin__)` 返回一个连续的算术整数序列
  * `start` 指定起始值，默认为`0`；
  * `stop` 指定结束值，结束值不会被返回(exclude)；
  * `step` 指定增量。

<h2 id="33">Exercise 33: While Loops</h2>
- 尽量使用`for`而非`while`

<h2 id="34">Exercise 34: Accessing Elements Of Lists</h2>
- `ordinal number` 序数，表示顺序，不含`0`，存在大数的前提是比其小的数都存在；
- `cardinal number` 基数，随机的，索引(index)性质的；
- `__getitem__() (Methods in class list)` 返回列表的某项，`x.__getitem__(y)`同`x[y]`。

<h2 id="35">Exercise 35: Branches and Functions</h2>
- `exit(parameter_returned)` 中断程序，返回值`0`通常表示正常退出。

<h2 id="36">Exercise 36: Designing and Debugging</h2>
- `if` 尽量组合一个`else:`(`else`如果没有意义或不应被执行，调用一个`die`函数返回信息便于调试)；
- `if` 块空行；
- `if` 尽量嵌套不超过2层；
- `bool` 判断表达式尽量简单，否则用变量；
- `print` 能很好地帮助你调试；
- 分步运行以调试。

<h2 id="37">Exercise 37: Symbol Review</h2>
- Keywords(关键字)
  > + Decide, Circulation(判断、循环)
  >   * `and ` `or `
  >   * `in `
  >   * `is ` `not `
  >   * `break ` `continue `
  >   * `for ` `while `
  >   * `if ` `elif ` `else `
  > + Module, Class, Method, Function(模块、类、函数)
  >   * `from ` `import ` `as `
  >   * `def ` `lambda `
  >   * `pass ` `return `
  >   * `class `
  > + Exception(异常)
  >   * `try ` `except ` `finally ` `raise `
  > + Others
  >   * `del `
  >   * `global `
  >   * `with ` `as `
  >   * `assert `
  >   * `yield `
  >   * `print `
  >   * `exec `

- Operators(操作符)
  > * `** ` Power of.(幂)
  > * `@ ` At(decorators)
  > * `+ ` `- ` `* ` `/ ` `// ` `% `
  > * `< ` `> ` `== ` `<= ` `>= ` `!= `
  > * `() ` `[] ` `{} `
  > * `, ` `. ` `; ` `: `
  > * `= ` `+= ` `-= ` `*= ` `**= ` `/= ` `//= ` `%= `

- Data Types(数据类型)
  > * `None ` 表示空值(nothing, no value)
  > * `True ` `False `
  > * `strings `
  > * `numbers `
  > * `floats `
  > * `lists `
  > * `dicts `

- String Escape Sequences(字符串转义序列)
  > * `\\ ` `\' ` `\" `
  > * `\a ` `\b `
  > * `\f ` `\n ` `\r `
  > * `\t ` `\v `

- String Formats(字符串格式化)
  > * `%d (%i) ` `%u `
  > * `%o ` `%x ` `%X `
  > * `%e ` `%E `
  > * `%f (%F) `
  > * `%g ` `%G `
  > * `%c `
  > * `%r `
  > * `%s `
  > * `%% `

<h2 id="38">Exercise 38: Doing Things To Lists</h2>
- `S.join(iterable) (Method in class str in module __builtin__)` 返回字符串(string)
  * `S` 表示分隔`iterable`各元素的符号(separator)；
  * `iterable` 指定组成返回的string的内容(the concatenation of the strings in the iterable)

<h2 id="39">Exercise 39: Dictionaries, Oh Lovely Dictionaries</h2>
- `dictionary` 字典(散列)：
  * `Key concept: mapping or associating` 建立数据的键值(Key, Value)映射；
  * No order 无序；
  * `Class dict in module __builtin__`
    + New and Initialize 创建和初始化
      * `dict()` 新建空字典；
      * `dict(mapping)` 新字典，用映射对象的键值对初始化(from a mapping object's (key, value) pairs)；
      * `dict(iterable)` 新字典，用迭代器对象初始化；
      * `dict(**kwargs)` 新字典，用给定变量的键值对初始化；
    + `Methods in class dict`
      * `items()` 用法`D.items()`，以二元组形式的键值对列表；
      * `keys()  values()` 用法`D.keys()  D.values()`，返回键 / 值列表；
      * `get(k[, d])` 用法`D.get()`，若`D`中有`k`，则返回`D[k]`，否则返回`d`，默认`d`为空(None)；
      * `clear()` 用法`D.clear()`，清除字典条目。
- `collections.OrderedDict (Class OrderedDict in module collections)` 记录插入顺序的字典：
  * dict subclass;
  * Overwrites existing entry(改写条目不改变顺序)，Deleting and reinserting(删除重插移至结尾)；
  * `OrderedDict.popitem(last=True)` 返回并删除键值对(默认`last=True`或`FIFO=False`时按`LIFO`后进先出原则pop)

<h2 id="40">Exercise 40: Modules, Classes, And Objects</h2>
- `OOP(Object-Oriented Programming)`
- `Module  Class` 模块、类 类似，都含方法、数据等，使用类似“键-值”的方式调用；
- `instantiate` 实例化，类到对象。
- `self` 类函数中的变量，用于标识对象或实例变量，以区分局部变量。

<h2 id="41">Exercise 41: Learning To Speak Object Oriented</h2>
- Word Drills
  > * `class` Tell Python to make a new type of thing.
    * `object` Two meanings: the most basic type of thing, and any instance of some thing.
    * `instance` What you get when you tell Python to create a class.
    * `def` How you define a function inside a class.
    * `self` Inside the functions in a class, self is a variable for the instance/object being accessed.
    * `inheritance` The concept that one class can inherit traits from another class, much like you and your parents.
    * `composition` The concept that a class can be composed of other classes as parts, much like how a car has wheels.
    * `attribute` A property classes have that are from composition and are usually variables.
    * `is-a` A phrase to say that something inherits from another, as in a "salmon" is-a "fish"
    * `has-a` A phrase to say that something is composed of other things or has a trait, as in "a salmon has-a mouth"

- Phrase Drills
  > `Next I have a list of Python code snippets on the left, and the English sentences for them:`
    * `class X(Y)` Make a class named X that is-a Y.
    * `class X(object): def __init__(self, J)` class X has-a __init__ that takes self and J parameters.
    * `class X(object): def M(self, J)` class X has-a function named M that takes self and J parameters.
    * `foo = X()` Set foo to an instance of class X.
    * `foo.M(J)` From foo get the M function, and call it with parameters self, J.
    * `foo.K = Q` From foo get the K attribute and set it to Q.

<h2 id="42">Exercise 42: Is-A, Has-A, Objects, and Classes</h2>
- `class ClassName(object):` 类名用`Camel-Case`风格，`object`表示类的继承类；
  * `object`本身也是一个类(历史原因，Python2.2之后的类都应以object为最终继承类以成为NewStyle Classes，Python3完全移除了OldStyle Classes)；
  * Multiple Inheritance多重继承，has-many；
  * 先定义类方法，再声明类变量；
  * 类的方法的第一个参数都必须为`self`；
  * `__init__()` 具体语法：
    ```python
    def __init__(self[, variables]):
        self.variables = variables
    ```
    类的初始化方法，将类变量与类联系，`self`表示类自身；
  * 无初始值的类变量置为`None`；
  * `instance_name = ClassName("variables")` 类的实例化(instantiate)，注意`self`参数不需；
- `super` 仅支持NewStyle Classes(继承于object的类都属于)：
  > ```python
  > def super(cls, inst):
  >     mro = inst.__class__.mro()
  >     return mro[mro.index(cls) + 1]
  > ```
  > 1. `inst` 生成MRO(Method Resolution Order, 方法解释顺序)的list；
  > 2. `cls` 定位当前MRO中的index并返回`mro[index + 1]`。

  1. 调用父类方法(特别是被子类重写的方法)，用法：`super(ChildClass, self).mathod()`，同`ParentClass.method()`；
  2. 多重继承调用(本质用法，因为`super`本身是改变方法解释顺序到下一个类)。

<h2 id="43">Exercise 43: Gothons From Planet Percal #25</h2>
- `Top Down` 自顶向下的设计方法；
- 重复和优化。

<h2 id="44">Exercise 44: Inheritance Vs. Composition</h2>
- `Composition` 合成，即引用和调用已有的类、模块等；
- 尽量少用继承，多用合成；
- 多重继承尽量不用。

<h2 id="45">Exercise 45: You Make A Game</h2>
- `Style`风格
  * `Function (Method)` 函数(方法)
    + 命名为小写加下划线；
    + 命名多用动词，表明做`do`；
    + 函数保持简单小巧`small and simple`。
  * `Class` 类
    + 类命名为`CamelCase`风格；
    + `__init__` 功能应设计得简单；
    + 尽量不重定义或重赋值全局变量或引入的模块的变量。
  * `Code` 代码
    + `spaces` 多留空白，保持清爽；
    + 不断改进。
  * `Comment` 注释
    + 不解释怎么做的，而解释为何这么做；
    + 注释也应精炼，并且不要过多；
    + 维护代码也要维护注释。

<h2 id="46">Exercise 46: A Project Skeleton</h2>
- 项目骨架：
  * `dir` 目录树
    > setup.py
    > NAME/
    >   __init__.py
    > bin/
    > docs/
    > tests/
    >   __init__.py
    >   NAME_tests.py

  * `NAME` 目录下为项目模块； `tests` 目录下为项目测试；修改`setup.py`和`NAME`。
  * `setup.py` 向`Distutils`描述安装的`packages(including modules)`，可查看doc[setup-script](https://docs.python.org/distutils/setupscript.html)。
- `pip` `distribute(setuptools)` `nose` `virtualenv`

<h2 id="47">Exercise 47: Automated Testing</h2>
- `test case` 测试用例； `test framework` 测试框架；
- `nose` 基于unittest；
  * Introduction:
    > nose extends the test loading and running features of unittest, making it easier to write, find and run tests.
    > By default, nose will run tests in files or directories under the current working directory whose names include “test” or “Test” at a word boundary (like “test_this” or “functional_test” or “TestClass” but not “libtest”). Test output is similar to that of unittest, but also includes captured stdout output from failing tests, for easy print-style debugging.
  * `nosetests` Run tests 运行测试；
    + `-vv` verbose 详细信息；
    + `-d` detailed-error(failure-detail) 错误详情；
    + `-exe` 查找可运行的module中的测试并运行；
    + `nosetests dir/test.py` 指定目录、指定测试文件。
  * 测试用例文件为一系列测试函数，类`unittest`；
  * 目录、测试文件、测试函数命名注意含`test/Test`以满足自动查找。
- `unittest` Python自带(pydoc)；
  * 作为测试类，也可独立成函数；
  * module, class, method, __main__
    + case script: 用例范本
      ```python
      import unittest

      class TestStringMethods(unittest.TestCase):

          def test_upper(self):
              self.assertEqual('foo'.upper(), 'FOO')

          def test_isupper(self):
              self.assertTrue('FOO'.isupper())
              self.assertFalse('Foo'.isupper())

          def test_split(self):
              s = 'hello world'
              self.assertEqual(s.split(), ['hello', 'world'])
              # check that s.split fails when the separator is not a string
              with self.assertRaises(TypeError):
                  s.split(2)

      if __name__ == '__main__':
          unittest.main()
      ```
    + 运行测试：
      * `python -m unittest -v module/class/method` `-m` 调用`unittest`，`-v`显示详情，可指定测试对象为具体模块/类/方法；
      * `python -m unittest -h` 帮助。
- `doctest` Python自带(pydoc)；
  * Intro:
    > The doctest module searches for pieces of text that look like interactive Python sessions, and then executes those sessions to verify that they work exactly as shown.
  * 编写：
    + 在`docstring`中写入测试，语法类似Python交互会话；
    + 在module尾添加调用代码：
      ```python
      if __name__ == "__main__":
          import doctest
          doctest.testmod()
      ```
    + 在非Python文件中测试时，调用`testfile()`；
    + `python -m doctest -v test` 命令行调用测试，测试用例文件为test。(**As a standalone module, may not work correctly if the file is part of a package and imports other submodules from that package.*)

<h2 id="48">Exercise 48: Advanced User Input</h2>
- `tuple` 元组：
  * 不可改变的有序序列；
  * 定义类列表，但使用`()`；
  * 可用分片(`slice`)调用元素，索引与负索引类列表，注意也是得到新tuple；
  * `in`判断是否含，无其它方法。
- `exception` 异常：
  * 当函数运行出错时，抛出(`raise`)异常待处理(`handle`)；
  * `try  except ` 异常处理语法：
    ```python
    try:
        try some code
    except SomeError:
        how to handle
    ```
- 将用户输入转换为数字：
  * `int()` 数据类型转换；
  * `ASCII` 编码转换。

<h2 id="49">Exercise 49: Making Sentences</h2>
- `raise` 引发异常；
- `nose` 的`assert method` ：
  * `assert_raises(exception, callable, parameters)` 测试异常， 参数分别为异常、调用对象、调用对象的参数(即调用对象的参数单独传输给`assert method`)；
  * `assert_is_instence(obj, cls)` 测试实例，`obj`测试对象，`cls`类；
- `nose`与`unittest`使用相同`method`但使用`PEP-8`规范的命名(即小写加下划线)。

<h2 id="50">Exercise 50: Your First Website</h2>

<h2 id="51">Exercise 51: Getting Input From A Browser</h2>

<h2 id="52">Exercise 52: The Start Of Your Web Game</h2>

<h2 id="53">Advice From An Old Programmer</h2>
- `It's not the languages that matter but what you do with them.`
- `Programming as an intellectual activity is the only art form that allows you to create interactive art.`
- `Programming as a profession is only moderately interesting.`
- `Learning to create software changes you and makes you different. Not better or worse, just different.`
- Do not treat programming just as a job, but a life style.Change and learn to change.

<h2 id="54">Next Steps</h2>
- For Python:
  1. Pick a project;
  2. Go through its docs and tutorials;
  3. Code it and make it work;
  4. Just have your own project.
- How to learn a programming language?
  1. Get a book or some introductory text about the language.
  2. Go through the book and type in all of the code making all of it run.
  3. Read the book as you work on the code, taking notes.
  4. Use the language to implement a small set of programs you are familiar with in another language.
  5. Read other people's code in the language, and try to copy their patterns.
- `The final thing to remember about learning a new language is: Don't be a stupid tourist.`
- `After you learn a language though, don't be a slave to that language's way of doing things.`
- It would never be a bad thing to learn something.Be Hungry. Be foolish.
