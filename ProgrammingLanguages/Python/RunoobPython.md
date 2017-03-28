# Runoob Python Tutorials Notes

_By X, in winter of 2016_

-----

> ### 目录
> [简介](#1)
> [语法基础](#2)
> [变量](#4)
> [Python运算](#5)
> [Python程序控制](#6)
> [Python时间和日期](#6)
> [Python函数](#7)
> [Python模块](#8)
> [Python基本I/O](#9)
> [Python异常处理](#10)
> [Python面向对象](#11)
> [Python正则表达式](#12)
> [Python CGI编程](#13)
> [Python MySQL](#14)
> [Python 网络编程](#15)
> [Python SMTP邮件](#16)
> [Python 多线程](#17)
> [Python XML](#18)
> [Python GUI编程](#19)
> [Python 简单实例](#20)

-----

<h3 id="1">简介</h3>
- 解释型，交互式，面向对象，脚本语言。
- Shebang: `#! /usr/bin/python(3)`
- 中文编码: `-*- coding:utf-8 -*-`

<h3 id="2">语法基础</h3>
- 标识符
  * 所有标识符可以包括英文、数字以及下划线（_），但不能以数字开头;
  * 区分大小写;
  * 以下划线开头的标识符是有特殊意义的:
     + 以单下划线开头（_foo）的代表不能直接访问的类属性，需通过类提供的接口进行访问，不能用"from xxx import *"而导入；
     + 以双下划线开头的（__foo）代表类的私有成员;
     + 以双下划线开头和结尾的（__foo__）代表python里特殊方法专用的标识.
- 保留字
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

- 严格的缩进控制
- 多行连接
  * `\ ` 连接符（不推荐）；
  * `() [] {}` 各括号（隐式连接）。
- 引号
  * `'' "" ` 单引号，双引号 相同；
  * `""" """ ` 三引号，可用于多行文本，实现所见即所得(WYSIWYG)。
- 注释
  * `# ` 通常使用；
  * `""" """ ` 三引号，多行注释。
- 尽量不在同一行写多语句（分号`; `分隔）

<h3 id="4">变量</h3>
- Python变量可以指定不同数据类型；
- 变量赋值后才会创建，也才能使用；
- 可以连等多变量赋相同值 `a = b = c = 1 `；
- 可以迭代分别赋值 `a, b = 1, 2 `；
- 对象复制：
  * 赋值：实质为对象引用，没有新对象产生；
  * 浅拷贝(shallow copy)：创建新对象，内容为引用；
     + 切片 ` [:] `；
     + 工厂函数(一些内建函数实质为类对象，调用时创建了类实例，类似工厂生产)(`int() list() round() string.lower() 等`)
     + copy.copy函数(`Function in module copy`)：拷贝一层，即一层对象为新创建，嵌套的深层对象仍为引用。
  * 深拷贝(deep copy)：copy.deepcopy函数(`Function in module copy`)
  * 非容器类型无拷贝，均为引用；
  * 元组变量值含原子类型时，只能浅拷贝。
- 标准数据类型：
  * Numbers(数字)
    1. 不可改变的数据类型，通过创建新对象改变其值；
    2. 四种：int, long(`L `后缀表示), float, complex(`a + bj `或`complex(a, b) `表示，实、虚部均为float)。
    3. 数学函数：
      > * ` abs(x) ` 绝对值(absolute value, number对象);
      > * ` math.fabs(x) ` 浮点数绝对值(float number, absolute value);
      > * ` math.ceil(x) ` 上取整(ceiling);
      > * ` math.floor(x) ` 下取整(floor);
      > * ` cmp(x, y) ` (compare, negative, zero, positive);
      > * ` math.log(x[, base]) ` 对数，默认底(base)为`e`(logarithm);
      > * ` math.log10(x) `
      > * ` max(x1, x2, ...) ` 取最大值，可用迭代器(iterator);
      > * ` min(x1, x2, ...) ` 取最小值，可用迭代器(iterator);
      > * ` modf(x) ` 返回浮点型整数和小数部分(fractional and integer parts of x, both carry the sign of x and are floats);
      > * ` round(number, [ndigits]) ` 精度控制，默认精度`0`；
      > * ` pow(x, y) ` 幂(power);
      > * ` math.exp(x) ` `e`的幂(e raised to the power of x);
      > * ` math.sqart(x) ` 平方根(squre root of x);

    4. 随机数函数：
      > * ` random() ` 随机，范围为[0.0, 1.0)；
      > * ` random.choice(seq) ` 随机一个序列元素；
      > * ` randrange([start, ]stop[, step]) ` 随机范围；
      > * ` random.seed(x) ` 随机数生成器的种子；
      > * ` random.shuffle(lst) ` 随机排列序列元素；
      > * ` random.uniform(x, y) ` 随机实数，范围为[x,y]或[x,y)，取决于round；

    5. 三角函数：
      > * ` cos(x) sin(x) tan(x) ` 弧度的余弦、正弦、正切；
      > * ` acos(x) asin(x) atan(x) ` 返回弧度的反三角；
      > * ` atan2(y, x) ` 返回`arctan(y/x)`，x与y的符号均有效；
      > * ` degrees(x) radians(x) ` 角度与弧度转换。

    6. 常量：
      > * ` pi ` 即` 3.1415926... `;
      > * ` e ` 自然对数。

  * String(字符串)
     + 一串字符；
     + 引号标记；
     + 索引和负索引；
     + 切片；
     + ` + * ` 连接，重复；
     + 转义：反斜杠` \ `符号，` \\ \' \" \t \n \other `;
     + ` in    not in ` 成员运算；
     + ` r/R ` 原始字符串(raw)；
     + 格式字符串：` % `
       > * 语法：
       >   ```python
       >   print "Hello %s%c" % ('World', '!')
       >   ```
       >
       > * ` %c %s %d %u %o %x %f ` 字符、字符串、整数、无符号整数、八进制、十六进制、浮点数；
       > * 辅助字符：
       >   + ` * ` 定义宽度或小数位精度；
       >   + ` 0 ` 宽度填充字符指定为`0`(可指定其它)；
       >   + ` + ` 显示正负号；
       >   + ` - ` 左对齐；
       >   + ` # ` 八进制前缀`0`或十六进制前缀`0x`；
       >   + ` %% ` 输出`%`符号；
       >   + ` m.n ` 最小总宽度`m`，小数位精度`n`。

     + Unicode字符串：在字符串前加`u`表明；
     + 内建函数：(Functions of Module string)
       > * ` count(s, sub[, start[, end]]) ` 计数范围内substring在s中的次数；
       > * ` find(s, sub[, start[, end]]) ` 返回最小索引，失败返回`-1`；
       > * ` index(s, sub[, start[, end]]) ` 返回最小索引，失败` raise ValueError`；
       > * ` join(list[, sep]) ` 连接列表元素，分隔符separator;
       > * ` lower(s) ` 将s字符转换为小写；
       > * ` replace(str, old, new[, maxreplace]) ` 替换str中old为new，最大替换次数；
       > * ` split(s[, sep[, maxsplit]]) ` 分割s, separator, max split;
       > * ` strip(s[, chars]) ` 去除leading and trailing whitespace;
       > * ` translate(s, table[, deletions]) ` 按table(必须为256长度的string)转换s, deletions中的字符从s中删除.

  * List(列表)
     + 最通用的复合数据类型；
     + 有序；
     + 列表元素任意，可嵌套，`, `分隔；
     + `[] `标记；
     + 索引，负索引；
     + 切片；
     + `+ * ` 连接，重复;
     + 方法(`Methods of Class list in __builtin__ module`)
       > * ` append(object) ` 追加列表元素；
       > * ` count(value) ` 计数；
       > * ` extend(iterable) ` 拓展迭代器内容；
       > * ` index(value[, start[, stop]]) ` 返回第一个出现的值的索引，失败`Raise ValueError`;
       > * ` insert(index, object) ` 插入；
       > * ` pop([index]) ` 弹出(返回并删除)，默认最后一个元素；
       > * ` remove(value) ` 移除；
       > * ` reverse() ` 反序；
       > * ` sort() ` 排序。

  * Tuple(元组)
     + 不能更新，相当于只读；
     + `() `标记；
     + 操作类似列表;
     + 方法(`Methods of Class tuple in __builtin__ module`)
       > * ` count(value) `
       > * ` index(value[, start[, stop]]) `

  * Dictionary(字典)
     + 无序的键值对；
     + `{} `标记；
     + 语法：`{key: value, another_key: another_value}`；
     + 通过键访问，键唯一且不可变；
     + 方法(`Methods of Class dict in __builtin__ module`)
       > * ` clear() ` 删除所有条目；
       > * ` copy() ` 浅拷贝；
       > * ` fromkeys(S[, v]) ` 新字典，键为`S`中键，默认值为`v`；
       > * ` get(k[, d]) ` 如果字典含键`k`则返回`D[k]`，否则返回`d`；
       > * ` has_key(k) ` 返回`bool`；
       > * ` items() ` 条目列表，二元组形式键值对；
       > * ` keys() `
       > * ` values() `
       > * ` pop(k[, d]) ` 弹出键`k`映射的键值对并返回值`v`，否则返回`d`或`Raise KeyError`；
       > * ` popitem() ` 返回键值对`(k, v)`，否则`Raise KeyError`；
       > * ` setdefault(k[, d]) ` 返回`D[k]`，否则创建新条目`D[k] = d`；
       > * ` update() ` 用字典或迭代器更新键值对，追加键值对及改变值。

- 数据类型转换：目的数据类型即函数名，例：`float(x)`。
- 数据类型分类：
  * 内存模型：
     + 标量/原子模型：数值、字符串；
     + 容器类型：列表、元组、字典；
  * 访问模型：
     + 直接访问：数值；
     + 顺序访问：列表、元组、字符串；
     + 映射访问：字典；
  * 更新模型：
     + 可更新：列表、字典；
     + 不可更新：数值、字符串、元组。

<h3 id="5">Python运算</h3>
- 算术运算符
  * ` + - * / ` 加减乘除；
  * ` % ` 取模(商向负无穷舍入floor)；
  * ` // ` Floor取整除法；
  * ` ** ` 幂；
- 位运算符
  * ` & | ^ - ` 按位与、或、异或、取反；
  * ` << >> ` 左、右移动index位。
- 比较运算符
  * ` == != > < >= <= `
- 赋值运算符
  * ` = += -= *= /= %= **= //= `
- 身份运算符(对象)
  * ` is    is not `
- 成员运算符
  * ` in    not in `
- 逻辑运算符
  * ` and or not `
- 运算符优先级
  * ` () ` 括号优先；
  * The order of operations:an acronym called **PEMDAS**,which stands for Parentheses Exponents Multiplication Division Addition Subtraction.(括号指数乘除加减)
  * 算术、位、比较、等于、赋值、身份、成员、逻辑。

<h3 id="6">Python程序控制</h3>
- 默认顺序结构；
- 选择结构：
  * if语句：
     + 语法：
      ```python
      if condition1:
          procession1
      elif condition2:
          procession2
      else:
          procession3
      ```

  * ` 0 null 空值 ` 为` false `
- 循环结构：
  * for循环
     + 语法
      ```python
      for iterating_var in sequence:
          statements(s)
      ```

     + ` for else ` 正常执行循环结束时可执行else语句。
  * while循环
     + 语法：
      ```python
      while expression:
          statements(s)
      ```

     + ` while else ` 正常执行循环结束时可执行else语句。
  * 循环控制
     + ` break ` 终止循环，跳出当前一层的循环；
     + ` continue ` 终止当前一次的循环，进入下一次循环；
     + ` pass ` 空语句，占位语句。

<h3 id="6">Python时间和日期</h3>
- ` time module `
  * 表示方法(standard representation)
     + 秒数[seconds]，从1970.01.01.00:00:00开始；
     + 时间元组[time tuple]，由9个数组成，分别为：
       > * year, 4 digits; month, (1 - 12); day, (1 - 31);
       > * hour, (0 - 23); minute, (0 - 59); second, (0 - 59);
       > * weekday, (0 - 6, Monday is 0);
       > * Julian day, (day in the year, 0 - 366);
       > * DST(Daylight Saving Time, 夏令时) flag, (-1, 0, 1).

  * Functions:
    > + ` time() ` 返回秒数；
    > + ` localtime([seconds]) ` 返回time tuple，表示本地时间，转换自seconds，默认当前时间current time；
    > + ` gmtime([seconds]) ` 返回time tuple，表示UTC(GMT)时间，转换自seconds，默认当前时间current time；
    > + ` mktime(tuple) ` 返回seconds，转换自time tuple；
    > + ` asctime([tuple]) ` 返回string，转换自time tuple，默认当前时间localtime()；
    > + ` strftime(format[, tuple]) ` 返回string，转换自time tuple，默认localtime()；
    > + ` strptime(string, format) ` 返回time tuple，转换自string；
    > + ` clock() ` 返回seconds，自程序开始执行或该语句首次调用；
    > + ` sleep(seconds) ` 延迟执行seconds时间。

- ` calendar module `
  * ` calendar.calendar(year,w=2,l=1,c=6) ` 返回一个多行字符串格式的year年年历，3个月一行，间隔距离为c。 每日宽度间隔为w字符。每行长度为21* W+18+2* C。l是每星期行数。
  * ` calendar.month(year,month,w=2,l=1) ` 返回一个多行字符串格式的year年month月日历，两行标题，一周一行。每日宽度间隔为w字符。每行的长度为7* w+6。l是每星期的行数。
  * ` calendar.isleap() ` 闰年判断，返回`bool`。
- ` datetime module `
  * Classes:
     + __builtin__.object
     + date
       * datetime
     + time
     + timedelta
     + tzinfo
  * ` date(year, month, day) --> date object` Methods of class date(__builtin__.object);
  * ` datetime(year, month, day[, hour[, minute[, second[, microsecond[, tzinfo]]]]]) ` Methods of class datetime(date);
- ` pylz module `
  <https://pypi.python.org/pypi/pytz/>
  > The standard library has no tzinfo instances, but there exists a third-party library which brings the IANA timezone database (also known as the Olson database) to Python: pytz.
  > pytz contains up-to-date information and its usage is recommended.

- ` dateutil module `
  <https://pypi.python.org/pypi/python-dateutil/> A third party module.

<h3 id="7">Python函数</h3>
- 内建函数和自定义函数；
- 自定义函数语法：
  ```python
  def function_name(parameters):
  """docstring
  """
      function_suite
      return [expression]
  ```

  默认返回`None`；
- 函数调用；
- 参数：
  * 参数变量均为按引用传递；
  * 参数类型：
     + 必备参数：按定义顺序输入所有必须参数；
     + 关键字参数：为实参指定形参，可不按定义顺序；
     + 默认参数：定义时指定默认值；
     + 不定长参数：` * `标记，不定长参数保存所有未命名参数供调用(*args等)。
  * 作用域：全局变量，局部变量
     + 局部变量在局部外不可直接调用；
     + 局部变量覆盖全局变量；
     + 同名互不影响，但局部中使用` global `关键字强制局部使用全局变量；
- ` lamda `匿名函数：
  * 只用于短小函数，通常为一行；
  * 拥有独立命名空间，只访问自有的参数列表，无法使用全局变量等。
    (命名空间即标识符(变量名称)与对象的字典)

<h3 id="8">Python模块</h3>
- 任何Python代码文件都可以作为模块，通过模块逻辑地构架代码；
- 模块导入：
  * 需要将模块文件放入搜索路径下；
    (搜索路径即解释器搜索的目录列表，由`system`模块的`sys.path`变量存储，包括当前目录、shell变量PATHONPATH记录的目录、安装决定的默认目录(UNIX: /usr/lib/python/)、指定添加的目录)
  * ` import    &    from ... import ... ` 导入语句，可指定模块的具体部分或指定模块目录；
  * ` reload(module) ` 再次导入，必须被成功导入过；
- ` dir([object]) ` Built-in Function in __builtin__ module，返回对象的属性(attributes)，可用于查询模块；
- ` globals()    locals() ` 返回当前域中的变量字典；
- Package包：有层次的的目录结构，由n个模块和子包组成的应用程序执行环境，含文件` __init__.py `(空文件或显示import以用于组织模块和子包)；

<h3 id="9">Python基本I/O</h3>
- 打印到屏幕：` print `
- 读取键盘输入：` raw_input([prompt])    input([prompt]) `
  * 推荐`raw_imput`，输入均作为string类型；
  * `input`实现是先后调用`raw_input`和`eval`，输入必须为合理和语法正确的，接受输入表达式并会相应处理。
- ` class file in module __builtin__ ` 文件类
  * file对象创建：(`open`函数调用)
    ` file_object_name = open(file_name[, access_mode][, buffering]) `
     + 访问模式默认为只读，模式包括r(read), w(write), a(append)，修饰+(read and write), b(as a binarry file);
     + 缓存设0表示无，1表示行缓存，更大表示缓冲区大小，负数表示使用系统默认缓冲区大小；
  * file对象的Data discriptors:
     + ` closed ` 文件关闭则true；
     + ` mode ` 访问模式；
     + ` name ` 文件名；
  * file对象的方法Methods：
    > + ` close() ` 关闭文件，停止对文件对象的I/O操作；
    > + ` flush() ` 刷新内部I/O buffer(写入文件并清除缓冲区)；
    > + ` read([size]) ` 读取文件[字节数]；
    > + ` readline([size]) ` 读取下一行[不超过字节数]；
    > + ` readlines([size]) ` 读取多行，返回string列表，包含大约size字节；
    > + ` next() ` 下一值(next value)；
    > + ` write(str) ` 写入字符串到文件，文件需要缓存写入才会真正改变；
    > + ` write(sequence_of_strings) `写入字符串序列到文件，不会自动添加换行符；
    > + ` tell() ` 当前文件中的操作位置；
    > + ` seek(offset[, whence]) ` 移动文件操作位置，offset指定偏移量，whence指定便宜参考点(0文件头，1当前位置，2文件尾)；
    > + ` truncate([size]) ` 截短文件(write模式会自动截短)。

- ` Functions in os module `
  > * ` rename(old, new) ` 重命名文件；
  > * ` remove(path) ` 移除文件；
  > * ` mkdir(path[, mode=0777]) ` 创建目录；
  > * ` chdir(path) `
  > * ` rmdir(path) `

<h3 id="10">Python异常处理</h3>
- 标准异常：
  * ` BaseException ` 所有异常的基类；
  * ` SystemExit ` 解释器请求退出；
  * ` KeyboardInterrupt ` 用户中断(键盘^C等)；
  * ` Exception ` 常规错误的基类` Exception(BaseException)`；
  * ` StandardError ` 所有内建标准异常的基类` StandardError(Exception)`；
  * ` AssertionError ` 断言语句失败；
  * ` EnvironmentError ` 操作系统错误的基类` EnvironmentError(StandardError)`；
  * ` WindowsError ` 系统调用失败；
  * ` LookupError ` 无效数据查询的基类` LookupErro(StandardError)`；
  * ` Warning ` 警告基类；
  * etc. 等
- 异常处理：
  * ` try except `
  * ` try finally `
  * ` raise [Exception[, args[, traceback]]] `
  * 自定义异常类
- Assertion断言

<h3 id="11">Python面向对象</h3>
- `class` 类
  * 属性`attribute`，方法`methods`；
  * 私有属性或方法以双下划线开始命名；
  * 内置类属性：`__doc__ `, `__name__ `, `__module__`, `__bases__`父类, `__dict__ `属性字典；
  * `__init__`, `__del__` 创建和销毁对象；
  * 方法必须含`self`变量；
  * 继承
     + 语法：` class derived_class(base_class): `
     + 方法`__init__`需要重写(override);
  * 检查`issubclass(C, B)` 返回bool，C是否为B的子类；
- `object` 对象
  * 对象在定义时创建；
  * 对象销毁机制为引用计数器和循环垃圾收集器，引用计数为0则解释器在合适时机回收内存，循环垃圾收集器关注被分配总量很大的对象(如果为循环引用，即对象互相引用而其他对象不引用它们，则试图清理)；
  * 对象通常不允许访问类私有属性，但可使用`object._className__attrName`访问；
  * 检查`isistance(obj, class)` 返回bool，是否为实例；

<h3 id="12">Python正则表达式</h3>
- `re`模块提供Perl风格的正则表达式模式功能：
  * `\A  \Z `匹配字符串的起始、末尾；
  * `flags `一些function的可选参数(optional parameters)：
    > + `re.I` IGNORECASE 大小写不敏感；
    > + `re.L` LOCALE 本地化识别(影响`\w \W \b \B`)；
    > + `re.M` MULTILINE 多行匹配(影响`^ $`)；
    > + `re.S` DOTALL `.`匹配包含`\n`的所有单个字符；
    > + `re.X` VERBOSE 灵活简便的格式；
    > + `re.U` UNICODE 根据Unicode字符集解析字符(影响`\w \W \b \B`)。

  * Functions :(pattern需要引号标记)
    > + `re.match(pattern, string, flags=0)` 在目标字符串`string`开始处匹配表达式`pattern`，成功则返回匹配对象，失败返回`Nono`；
    > + `re.search(pattern, string, flags=0)` 扫描整个目标字符串`string`匹配表达式`pattern`，成功则返回匹配对象，失败返回`Nono`；
    > + `re.sub(pattern, repl, string, count=0, flags=0)` 替换目标字符串中的匹配表达式为repl并返回最终获得的字符串，count为0默认全部替换，repl为字符串或函数(接受匹配字符串作参数，返回替换字符串)；

  * Classes :
     + `re.RegexObject`
     + `re.MatchObject`
       1. Match objects always have a boolean value of `True`.
       2. Methods:
         > `group([group])` 返回匹配组(子组)，以元组形式，默认为0表示所有组即整个匹配，组索引从1开始，通常以空白字符分组；
         > `groups([default])` 返回元组形式的所有组，默认为None表示没有不参与匹配的组；
         > `span([group])` 返回组的起始和结束位置(indices)，默认为0表示整个匹配；

<h3 id="13">Python CGI编程</h3>
- CGI(Common Gateway Interface) 通用网关接口
  * 运行于服务器的程序，提供同客户端HTML页面的接口。CGI是外部应用程序（CGI程序）与Web服务器之间的接口标准；
  * CGI 程序的工作：从环境变量(environment variables)和标准输入(standard input)中读取数据、处理数据、向标准输出(standard output)输出数据；
  * 绝大多数的CGI程序被用来解释处理来自表单的输入信息，并在服务器产生相应的处理，或将相应的信息反馈给浏览器；
  * CGI程序使网页具有交互功能；
  * CGI可以用任何一种语言编写，只要这种语言具有标准输入、输出和环境变量。最好选用易于归档和能有效表示大量数据结构的语言；
  * Perl (Practical Extraction and Report Language)由于其跨操作系统、易于修改的特性成为了CGI的主流编写语言。
- 服务器配置；
- CGI程序编写和加载。

<h3 id="14">Python MySQL</h3>
- Python 标准数据库接口为 Python DB-API，它定义了一系列必须的对象和数据库存取方式, 以便为各种各样的底层数据库系统和多种多样的数据库接口程序提供一致的访问接口；
- 支持MySQL、Oracle、Sybase、Microsoft SQL Server等多种数据库(完整支持参见[Python数据库接口及API](https://wiki.python.org/moin/DatabaseInterfaces))，不同数据库需要安装不同的模块以支持。
- Python DB-API使用流程：
  * 引入 API 模块；
  * 获取与数据库的连接；
  * 执行SQL语句和存储过程；
  * 关闭数据库连接。
- MySQLdb 是用于Python链接Mysql数据库的接口，它实现了 Python 数据库 API 规范 V2.0，基于 MySQL C API 上建立的，需要安装package `MySQL-python`([Package on pypi](https://pypi.python.org/pypi/MySQL-python))；
- 数据库连接：
  * 连接前需要：
     + 已创建相应的数据库及表；
     + 连接授权；
  * 连接实例：(_以下各实例中：数据库为TESTDB，其中表为EMPLOYEE，表字段为 FIRST_NAME, LAST_NAME, AGE, SEX 和 INCOME，连接数据库TESTDB使用的用户名为 "testuser" ，密码为 "test123"_)
    ```python
    #!/usr/bin/python
    # -*- coding: UTF-8 -*-

    import MySQLdb

    # 打开数据库连接
    db = MySQLdb.connect("localhost","testuser","test123","TESTDB" )

    # 使用cursor()方法获取操作游标
    cursor = db.cursor()

    # 使用execute方法执行SQL语句
    cursor.execute("SELECT VERSION()")

    # 使用 fetchone() 方法获取一条数据库。
    data = cursor.fetchone()

    print "Database version : %s " % data

    # 关闭数据库连接
    db.close()
    ```

- 创建数据库表：(execute方法)
  ```python
  #!/usr/bin/python
  # -*- coding: UTF-8 -*-

  import MySQLdb

  # 打开数据库连接
  db = MySQLdb.connect("localhost","testuser","test123","TESTDB" )

  # 使用cursor()方法获取操作游标
  cursor = db.cursor()

  # 如果数据表已经存在使用 execute() 方法删除表。
  cursor.execute("DROP TABLE IF EXISTS EMPLOYEE")

  # 创建数据表SQL语句
  sql = """CREATE TABLE EMPLOYEE (
           FIRST_NAME  CHAR(20) NOT NULL,
           LAST_NAME  CHAR(20),
           AGE INT,
           SEX CHAR(1),
           INCOME FLOAT )"""

  cursor.execute(sql)

  # 关闭数据库连接
  db.close()
  ```

- 数据库插入：(SQL INSERT语句)
  ```python
  #!/usr/bin/python
  # -*- coding: UTF-8 -*-

  import MySQLdb

  # 打开数据库连接
  db = MySQLdb.connect("localhost","testuser","test123","TESTDB" )

  # 使用cursor()方法获取操作游标
  cursor = db.cursor()

  # SQL 插入语句
  sql = "INSERT INTO EMPLOYEE(FIRST_NAME, \
         LAST_NAME, AGE, SEX, INCOME) \
         VALUES ('%s', '%s', '%d', '%c', '%d' )" % \
         ('Mac', 'Mohan', 20, 'M', 2000)
  try:
     # 执行sql语句
     cursor.execute(sql)
     # 提交到数据库执行
     db.commit()
  except:
     # 发生错误时回滚
     db.rollback()

  # 关闭数据库连接
  db.close()
  ```

- 数据库查询：
  * `fetchone()` 获取下个查询结果集；
  * `fetchall()` 获取所有结果行；
  * `rowcount` 只读属性，执行execute()方法后影响的行数；
  ```python
  #!/usr/bin/python
  # -*- coding: UTF-8 -*-

  import MySQLdb

  # 打开数据库连接
  db = MySQLdb.connect("localhost","testuser","test123","TESTDB" )

  # 使用cursor()方法获取操作游标
  cursor = db.cursor()

  # SQL 查询语句
  sql = "SELECT * FROM EMPLOYEE \
         WHERE INCOME > '%d'" % (1000)
  try:
     # 执行SQL语句
     cursor.execute(sql)
     # 获取所有记录列表
     results = cursor.fetchall()
     for row in results:
        fname = row[0]
        lname = row[1]
        age = row[2]
        sex = row[3]
        income = row[4]
        # 打印结果
        print "fname=%s,lname=%s,age=%d,sex=%s,income=%d" % \
               (fname, lname, age, sex, income )
  except:
     print "Error: unable to fecth data"

  # 关闭数据库连接
  db.close()
  ```

- 数据库更新：(SQL UPDATE语句)
  ```python
  #!/usr/bin/python
  # -*- coding: UTF-8 -*-

  import MySQLdb

  # 打开数据库连接
  db = MySQLdb.connect("localhost","testuser","test123","TESTDB" )

  # 使用cursor()方法获取操作游标
  cursor = db.cursor()

  # SQL 更新语句
  sql = "UPDATE EMPLOYEE SET AGE = AGE + 1
                            WHERE SEX = '%c'" % ('M')
  try:
     # 执行SQL语句
     cursor.execute(sql)
     # 提交到数据库执行
     db.commit()
  except:
     # 发生错误时回滚
     db.rollback()

  # 关闭数据库连接
  db.close()
  ```

- 删除：(SQL DELETE语句)
  ```python
  #!/usr/bin/python
  # -*- coding: UTF-8 -*-

  import MySQLdb

  # 打开数据库连接
  db = MySQLdb.connect("localhost","testuser","test123","TESTDB" )

  # 使用cursor()方法获取操作游标
  cursor = db.cursor()

  # SQL 删除语句
  sql = "DELETE FROM EMPLOYEE WHERE AGE > '%d'" % (20)
  try:
     # 执行SQL语句
     cursor.execute(sql)
     # 提交修改
     db.commit()
  except:
     # 发生错误时回滚
     db.rollback()

  # 关闭连接
  db.close()
  ```

- 事务：
  * 事务机制可以确保数据一致性；
  * 事务应该具有4个属性(ACID)：原子性、一致性、隔离性、持久性；
     + 原子性(atomicity): 一个事务是一个不可分割的工作单位，事务中包括的诸操作要么都做，要么都不做；
     + 一致性(consistency):  事务必须是使数据库从一个一致性状态变到另一个一致性状态。一致性与原子性是密切相关的；
     + 隔离性(isolation): 一个事务的执行不能被其他事务干扰。即一个事务内部的操作及使用的数据对并发的其他事务是隔离的，并发执行的各个事务之间不能互相干扰；
     + 持久性(durability): 持续性也称永久性(permanence)，指一个事务一旦提交，它对数据库中数据的改变就应该是永久性的，接下来的其他操作或故障不应该对其有任何影响。
  * Python DB API 2.0 的事务提供了两个方法 `commit`(游标的所有更新操作)或`rollback`(回滚当前游标的所有操作)。
  ```python
  # SQL删除记录语句
  sql = "DELETE FROM EMPLOYEE WHERE AGE > '%d'" % (20)
  try:
     # 执行SQL语句
     cursor.execute(sql)
     # 向数据库提交
     db.commit()
  except:
     # 发生错误时回滚
     db.rollback()
  ```

- 错误处理：
  * `StandardError`子类：
     + `Warning` 严重警告；
     + `Error` 其他所有错误类。
  * `Error`子类：
     + `InterfaceError` 接口模块错误；
     + `DatabaseError` 数据库错误。
  * `DatabaseError`子类：
     + `DataError` 数据错误；
     + `OperationalError` 操作错误(非用户控制的错误)；
     + `IntegrityError` 完整性错误；
     + `InternalError` 内部错误；
     + `ProgrammingError` 程序错误；
     + `NotSupportedError` 不支持错误。

<h3 id="15">Python 网络编程</h3>
- Python 提供了两个级别访问的网络服务：
  * 低级别的网络服务支持基本的 Socket，它提供了标准的 BSD Sockets API，可以访问底层操作系统Socket接口的全部方法；
  * 高级别的网络服务模块 SocketServer， 它提供了服务器中心类，可以简化网络服务器的开发。
- Python网络编程模块：
  |协议     |功能                       |端口号 |Python模块     |
  |:-----:  |:-----:                    |:-----:|-----          |
  |HTTP     |网页访问                   |80     |httplib, urllib, xmlrpclib |
  |NNTP     |阅读和张贴新闻文章(帖子)   |119    |nntplib        |
  |FTP      |文件传输                   |20     |ftplib, urllib |
  |SMTP     |发送邮件                   |25     |smtplib        |
  |POP3     |接受邮件                   |110    |poplib         |
  |IMAP4    |获取邮件                   |143    |imaplib        |
  |Telnet   |命令行                     |23     |telnetlib      |
  |Gopher   |信息查找                   |70     |gopherlib, urllib |


- `socket()`函数创建套接字，语法格式： `socket.socket([family[, type[, proto]]])`
  * `family` 套接字家族可以使AF_UNIX或者AF_INET；
  * `type` 套接字类型可以根据是面向连接的还是非连接分为SOCK_STREAM或SOCK_DGRAM；
  * `protocol` 一般不填默认为0。
- 使用`socket`模块下的内建函数操作套接字。
- 详细参阅：[菜鸟教程](http://www.runoob.com/python/python-socket.html) [官方文档](https://docs.python.org/2/library/socket.html)

<h3 id="16">Python SMTP邮件</h3>
- 创建 SMTP 对象语法如下：
  ```python
  import smtplib

  smtpObj = smtplib.SMTP( [host [, port [, local_hostname]]] )
  ```

  * 参数说明：
     + `host` SMTP 服务器主机。你可以指定主机的ip地址或者域名如:w3cschool.cc，这个是可选参数。
     + `port` 如果你提供了 host 参数, 你需要指定 SMTP 服务使用的端口号，一般情况下SMTP端口号为25。
     + `local_hostname` 如果SMTP在你的本机上，你只需要指定服务器地址为 localhost 即可。
- SMTP对象使用sendmail方法发送邮件，语法如下：
  ```python
  SMTP.sendmail(from_addr, to_addrs, msg[, mail_options, rcpt_options])
  ```

  * 参数说明：
     + `from_addr` 邮件发送者地址。
     + `to_addrs` 字符串列表，邮件发送地址。
     + `msg` 发送消息。 msg是字符串，表示邮件，需要按照smtp协议中定义的格式书写(一般由标题，发信人，收件人，邮件内容，附件等构成)

- 实例：
  ```python
  #!/usr/bin/python
  # -*- coding: UTF-8 -*-

  import smtplib
  from email.mime.text import MIMEText
  from email.header import Header

  # 第三方 SMTP 服务
  mail_host="smtp.XXX.com"  #设置服务器
  mail_user="XXXX"    #用户名
  mail_pass="XXXXXX"   #口令


  sender = 'from@runoob.com'
  receivers = ['429240967@qq.com']  # 接收邮件，可设置为你的QQ邮箱或者其他邮箱

  message = MIMEText('Python 邮件发送测试...', 'plain', 'utf-8')
  message['From'] = Header("菜鸟教程", 'utf-8')
  message['To'] =  Header("测试", 'utf-8')

  subject = 'Python SMTP 邮件测试'
  message['Subject'] = Header(subject, 'utf-8')


  try:
      smtpObj = smtplib.SMTP()
      smtpObj.connect(mail_host, 25)    # 25 为 SMTP 端口号
      smtpObj.login(mail_user,mail_pass)
      smtpObj.sendmail(sender, receivers, message.as_string())
      print "邮件发送成功"
  except smtplib.SMTPException:
      print "Error: 无法发送邮件"
  ```

- 可发送HTML邮件、添加附件、发送图片等；
- 参见：[菜鸟教程](http://www.runoob.com/python/python-email.html) [官方文档](https://docs.python.org/2/library/email-examples.html)

<h3 id="17">Python 多线程</h3>
- `thread` ` built-in module` ：(primitive oprations)
  * `start_new_thread(function, args[, kwargs])` 产生新线程，`function`线程函数，`args`传递给线程函数的元组(tuple)类型参数；
- `threading` ` module` ：
  * `threading.exit()` 退出线程；
  * `threading.currentThread()` 返回当前的线程变量；
  * `threading.enumerate()` 返回一个包含正在运行的线程的list。正在运行指线程启动后、结束前，不包括启动前和终止后的线程；
  * `threading.activeCount()` 返回正在运行的线程数量，与len(threading.enumerate())有相同的结果。
  * 线程模块同样提供了`Thread`类来处理线程，Thread类提供了以下方法:
     + `run()` 用以表示线程活动的方法。
     + `start()`启动线程活动。
     + `join([time])` 等待至线程中止。这阻塞调用线程直至线程的join() 方法被调用中止-正常退出或者抛出未处理的异常-或者是可选的超时发生。
     + `isAlive()` 返回线程是否活动的。
     + `getName()` 返回线程名。
     + `setName()` 设置线程名。
- 多线程同步：
  * 使用Thread对象的Lock和Rlock可以实现简单的线程同步，这两个对象都有acquire方法和release方法，对于那些需要每次只允许一个线程操作的数据，可以将其操作放到acquire和release方法之间。
  * 锁有两种状态——锁定和未锁定。每当一个线程比如"set"要访问共享数据时，必须先获得锁定；如果已经有别的线程比如"print"获得锁定了，那么就让线程"set"暂停，也就是同步阻塞；等到线程"print"访问完毕，释放锁以后，再让线程"set"继续。 
  * `Queue`模块中提供了同步的、线程安全的队列类，包括FIFO（先入先出)队列Queue，LIFO（后入先出）队列LifoQueue，和优先级队列PriorityQueue。这些队列都实现了锁原语，能够在多线程中直接使用。可以使用队列来实现线程间的同步。
    > `Queue`模块常用方法：
    > + `Queue.qsize()` 返回队列的大小
    > + `Queue.empty()` 如果队列为空，返回True,反之False
    > + `Queue.full()` 如果队列满了，返回True,反之False
    > + `Queue.full` 与 maxsize 大小对应
    > + `Queue.get([block[, timeout]])` 获取队列，timeout等待时间
    > + `Queue.get_nowait()` 相当Queue.get(False)
    > + `Queue.put(item)` 写入队列，timeout等待时间
    > + `Queue.put_nowait(item)` 相当Queue.put(item, False)
    > + `Queue.task_done()` 在完成一项工作之后，Queue.task_done()函数向任务已经完成的队列发送一个信号
    > + `Queue.join()` 实际上意味着等到队列为空，再执行别的操作

- [详细参见菜鸟教程](http://www.runoob.com/python/python-multithreading.html)

<h3 id="18">Python XML</h3>
- python有三种方法解析XML，SAX，DOM，以及ElementTree:
  1. SAX (simple API for XML ) python 标准库包含SAX解析器，SAX用事件驱动模型，通过在解析XML的过程中触发一个个的事件并调用用户定义的回调函数来处理XML文件。
  2. DOM(Document Object Model) 将XML数据在内存中解析成一个树，通过对树的操作来操作XML。
  3. ElementTree(元素树) ElementTree就像一个轻量级的DOM，具有方便友好的API。代码可用性好，速度快，消耗内存少。
  4. 因DOM需要将XML数据映射到内存中的树，一是比较慢，二是比较耗内存，而SAX流式读取XML文件，比较快，占用内存少，但需要用户实现回调函数（handler）。
- Python使用SAX解析xml
  * SAX是一种基于事件驱动的API。利用SAX解析XML文档牵涉到两个部分：解析器和事件处理器。解析器负责读取XML文档,并向事件处理器发送事件,如元素开始跟元素结束事件；而事件处理器则负责对事件作出相应,对传递的XML数据进行处理。
    > 1. 对大型文件进行处理；
    > 2. 只需要文件的部分内容，或者只需从文件中得到特定信息；
    > 3. 想建立自己的对象模型的时候。

  * 在python中使用sax方式处理xml要先引入xml.sax中的parse函数，还有xml.sax.handler中的ContentHandler。
  * `ContentHandler`类方法介绍：
    > + `characters(content)`方法
    >   * 调用时机：
    >   * 从行开始，遇到标签之前，存在字符，content的值为这些字符串。
    >   * 从一个标签，遇到下一个标签之前， 存在字符，content的值为这些字符串。
    >   * 从一个标签，遇到行结束符之前，存在字符，content的值为这些字符串。
    >   * 标签可以是开始标签，也可以是结束标签。
    > + `startDocument()` 文档启动的时候调用。
    > + `endDocument()` 解析器到达文档结尾时调用。
    > + `startElement(name, attrs)` 遇到XML开始标签时调用，name是标签的名字，attrs是标签的属性值字典。
    > + `endElement(name)` 遇到XML结束标签时调用。

  * `make_parser` 创建一个新的解析器对象并返回。`xml.sax.make_parser([parser_list])` 参数`parser_list` 解析器列表；
  * `parser` 创建一个 SAX 解析器并解析xml文档： `xml.sax.parse(xmlfile, contenthandler[, errorhandler])` 参数 `xmlfile` xml文件名； `contenthandler` 必须是一个ContentHandler的对象； `errorhandler` 如果指定该参数，errorhandler必须是一个SAX ErrorHandler对象。
  * `parseString` 创建一个XML解析器并解析xml字符串： `xml.sax.parseString(xmlstring, contenthandler[, errorhandler])` 参数 `xmlstring` xml字符串； `contenthandler` 必须是一个ContentHandler的对象； `errorhandler` 如果指定该参数，errorhandler必须是一个SAX ErrorHandler对象。
  * [参阅官方文档](https://docs.python.org/library/xml.sax.html)
- 使用`xml.dom`解析xml
  * 文件对象模型（Document Object Model，简称DOM），是W3C组织推荐的处理可扩展置标语言的标准编程接口。
  * 一个 DOM 的解析器在解析一个 XML 文档时，一次性读取整个文档，把文档中所有元素保存在内存中的一个树结构里，之后你可以利用DOM 提供的不同的函数来读取或修改文档的内容和结构，也可以把修改过的内容写入xml文件。
  * python中用`xml.dom.minidom`来解析xml文件
  * [参阅官方文档](https://docs.python.org/library/xml.dom.html)
- [参阅菜鸟教程](http://www.runoob.com/python/python-xml.html)

<h3 id="19">Python GUI编程</h3>
- python提供了多个图形开发界面的库，几个常用Python GUI库如下：
  * `Tkinter`： Tkinter模块("Tk 接口")是Python的标准Tk GUI工具包的接口.Tk和Tkinter可以在大多数的Unix平台下使用,同样可以应用在Windows和Macintosh系统里.,Tk8.0的后续版本可以实现本地窗口风格,并良好地运行在绝大多数平台中。
  * `wxPython`：wxPython 是一款开源软件，是 Python 语言的一套优秀的 GUI 图形库，允许 Python 程序员很方便的创建完整的、功能键全的 GUI 用户界面。
  * `Jython`：Jython程序可以和Java无缝集成。除了一些标准模块，Jython使用Java的模块。Jython几乎拥有标准的Python中不依赖于C语言的全部模块。比如，Jython的用户界面将使用Swing，AWT或者SWT。Jython可以被动态或静态地编译成Java字节码。
- Tkinter GUI编程基本步骤：
  1. 导入Tkinter模块；
  2. 创建控件；
  3. 指定这个控件的master， 即这个控件属于哪一个；
  4. 告诉GM(geometry manager)有一个控件产生了。

<h3 id="20">Python 简单实例</h3>

