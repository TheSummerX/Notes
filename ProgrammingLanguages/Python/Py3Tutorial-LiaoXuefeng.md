# Python3 Tutorial Provided By LiaoXuefeng

[Tutorial Web](http://www.liaoxuefeng.com/wiki/0014316089557264a6b348958f449949df42a6d3a2e542c000)
[What's new in Python3](https://docs.python.org/3/whatsnew/3.0.html)
_In winter of 2016, by X_

-----

>
>
>

<h3 id="1">简介</h3>
- Python由“龟叔”在1989年圣诞编写；
- 解释型语言，高级，简洁易懂，拥有大量基础代码库，涵盖网络、数据库、文本处理等；
- 运行慢，源码发布。

<h3 id="2">安装</h3>
- Nothing to talk about.
- 解释器：
  * `CPython` 官方版本，C语言开发，广泛；
  * `IPython` 基于`CPython`，改进交互；
  * `PyPy` 使用[JIT](https://en.wikipedia.org/wiki/Just-in-time_compilation)技术动态编译，提高运行速度，[区别](https://pypy.readthedocs.org/en/latest/cpython_differences.html)；
  * `Jython` JAVA平台，可编译为JAVA字节码；
  * `IronPython` 微软.Net平台。

<h3 id="3">Python基础</h3>
- 缩进敏感，大小写敏感，`#`注释；
- 数据类型和变量：
  * 变量赋值为引用；
  * (Different with Python2)`/`浮点数除法，结果为浮点数；`//`为floor除法，结果为整数；`None`空值(Null)；`input()`修改的Function，参见文档；
- 字符串和编码：
  * Python3字符串(str)使用Unicode编码表示，可以` # -*- coding:utf-8 -*- `指定使用UTF-8编码保存和读取，通过`encode`方法存为`bytes`类型(相应`decode`)；
  * `bytes` 类型使用` b `前缀加引号表示，其每一字符均占用一个字节，除ASCII字符外显示为`\xxx`(两位十六进制数)形式；
  * Function `ord()`获取单字符字符串的整数编码，`chr()`获取编码数对应的单个字符(one-character string)；
- List & Tuple
- Dict & Set
  * dict使用Hash计算key以获取value位置，key唯一且不可变；
  * set是key的集合；
- 条件判断
- 循环

<h3 id="4">Python函数</h3>
- 调用
- 定义
  * 默认返回`return None`，多值返回为tuple；
- 参数
  * 参数定义顺序必须如下(必，默，可，关)
  * 位置参数(必选参数)：按定义位置传入实际参数；
  * 默认参数：定义为不变对象(如`None`)避免值改变导致错误；
  * 可变参数：`*`前缀，如`*args`，参数数目可变，为tuple；
  * 命名关键字参数：`*`分隔符(可变参数后定义可以不用分隔)，需要同时传入关键字和实参；
  * 关键字参数：`**`前缀，如`**kw`，自动构建为dict；
- 递归函数
  * 递归每一层需求相应的栈帧，所以递归过多可能导致栈溢出；
  * 尾递归：等效于循环，即在递归返回时调用递归，进行优化可使得递归只使用一层栈帧避免栈溢出(Python没有优化)；

<h3 id="5">Python高级特性</h3>
- 切片：对list或tuple，字符串也可执行切片；
- 迭代(Iteration)：`for ... in ... `对可迭代对象(Type iterable in Module collections)(包括list, tuple, dict, string)；
- 列表生成式：如`[m + n for m in range(1, 4) for n in ('a', 'b', 9, 'c') if isinstance(n, str)]`；
- 生成器(generator)：
  * 列表生成式的`[]`改为`()`即可创建，函数定义时函数体中使用`yield`关键字会改为定义生成器函数(generator function)；
  * 生成器生成的结果是每次调用即时生成的，不会一次完全生成存储从而节约空间和时间；
  * `next(generator)` 函数获取下一生成结果，结束时抛出错误`StopIteration`，可用`for`循环获取生成结果；
  * `for`循环调用generator需要generator的`return`值时需要捕获`StopIteration`错误的`value`；
  * `yield`关键字指示generator中断，并返回结果；
- 迭代器(iterator)：
  * 可被函数`next()`调用并返回下一值的对象；
  * 可用于`for`循环的对象都是`Iterable`类型；
  * `list, dict, str, etc.`是`iterable`但不是`iterator`(`iterator`是惰性计算的数据流)，使用函数`iter()`可获得`iterator`对象；

<h3 id="6">Python函数式编程(Funcional Programming)</h3>
- 函数式编程是一种高度抽象的编程范式，属于"结构化编程"的一种，主要思想是把运算过程尽量写成一系列嵌套的函数调用；
- 基本特点包括：支持闭包和高阶函数，支持惰性计算(lazy evaluation)，使用递归作为控制流程的机制，加强了引用透明性，没有副作用；
- 高阶函数(Higher-order function)：
  * 函数名即指向函数的变量；
  * 接受函数作为参数的函数即高阶；
  * `map(func, *iterables)` Class map in Module builtins, 将序列各元素作用于函数，返回`iterator`；
  * `reduce(function, sequence[, initial])` Built-in function in Module functools, 将序列元素依次循环作用到两参数函数，使得序列`reduce`得到单个值并返回，initial作为序列首位；
  * `filter(function or None, iterable)` Class filter in Module builtins, 返回迭代器(将输入的迭代器的各为true的item返回或传入Function后为true的item处理后返回)；
  * `sorted(iterable, key=None, reverse=False)` Built-in Function in Module builtins, 排序；
- 返回函数：
  * 闭包(Closure)：在函数内定义内部函数，可调用外部函数的参量和局部变量，通过调用外部函数可返回内部函数；
  * 返回函数时，函数并未执行，需要执行函数调用，故需要注意参量是引用，会变化；
- 匿名函数(lambda): `lambda arguments: expression` 简单函数，直接返回expression的结果到arguments；
- 装饰器(Decorator):
  * 用于包装函数的函数，定义后在待包装的函数定义前使用`@`关键字注解；
  * 完整的一个例子：
    ```python
    # decorator
    import functools

    def log(text):
        def decorator(func):
            @functools.wraps(func)  # 使得调用装饰器后不会修改被装饰函数的 '__name__' 属性
            def wrapper(*args, **kw):
                print('%s, %s():' % (text, func.__name__))  # 函数作为对象，具有属性 '__name__'
                return func(*args, **kw)
            return wrapper
        return decorator

    # call decorator
    @log('execute')
    def now():
        print('2016-12-25')
    ```

    调用结果为：
    ```python
    >>> now()
    execute now():
    2016-12-25
    ```

- 偏函数(Partial function):
  * Class partial in Module functools
  * `partial(function, *args, **kwargs)` 返回函数Function参数为args和kwargs时的新函数；
  * 使得已有函数(特别是参数很多的)调用时简化参数；

<h3 id="7">Python模块</h3>
- 通过使用模块组织代码，提高管理性和维护性，避免命名冲突；
- 包(package)：含有模块的目录，其中包本身也是模块，由其`__init__.py`(可为空文件)定义；
- 作用域：
  * 通常函数和变量为公开的(public)；
  * 特殊变量也可直接引用，但只用于特殊用途(__name__等双下划线前后缀)；
  * 私有的(private)不应直接引用，使用`_`前缀标注。
- 模块搜索路径：
  * 存放在模块`sys`下的`path`变量中，包含当前路径、安装的内置模块、第三方模块路径；
  * 添加路径：
    * 导入模块`sys`后`sys.path.append()`，运行时修改，结束运行失效；
    * 设置环境变量`PYTHONPATH`，其内容会自动添加到模块搜索路径；

<h3 id="8">Python面向对象编程(Object Oriented Programming)</h3>
- 数据封装、继承、多态是三大基础特性；
- 类(class)、实例(instance)：
  * 属性(attribute)即数据，方法(method)即函数；
  * 实例可添加属性或方法，默认属性或方法会被覆盖；
- 访问限制：
  * `__` 仅双下划线前缀，解释器会作私有属性处理，外部不能访问；
- 继承(inheritance)和多态(polymorphism)：
  * 子类(Subclass)，父类(基类、超类 Base class, Super class);
  * 继承判断：`isinstance()`实例检查，`issubclass()`类检查；
  * 动态语言的鸭子类型(duck typing)：对于拥有特定方法的对象，可看做某类的实例进行使用(虽然它不是实例)，提高了代码的可伸缩性；
  * 多态：由于子类的对象是(is)子类类型，也是父类类型，当子类实例或鸭子按父类方法调用时，会自动调用相应的子类或鸭子方法(即调用方只关心调用，不关心细节)；
  * 开闭原则：
    * 对拓展开放(Open for extension)：允许新子类和子类方法覆盖；
    * 对修改封闭(Closed for modification)：父类方法不需要修改；
- 获取对象信息：
  * `type(object)` Class type in Module builtins, 返回object的类型；
  * `types` Module, 定义非直接可用的内建类型(FunctionType/BuiltinFunctionType/LambdaType等)；
  * `isinstance()` Built-in function in Module builtins；
  * `dir([object])` Built-in function in Module builtins, 返回字符串列表，其item为对象的相关attributes和methods，结合方法`hasattr() getattr() setattr()`可操作对象的状态；
- 实例属性和类属性：
  * 类属性直接在类中定义；
  * 实例属性通常在`__init__`方法中通过`self`变量绑定；
  * 实例也可访问类属性，但实例属性会覆盖同名的类属性；

<h3 id="9">Python面向对象高级编程(Object Oriented Programming)</h3>
- 类和实例也可在定义外绑定方法，类绑定可被所有实例调用，实例绑定只能本身调用；
  ```python
  >>> class Student(object):  # 类定义
  >>>     pass
  >>> def set_score(self, score):  # 定义方法
  ...     self.score = score
  ...
  >>> Student.set_score = set_score  # 绑定类方法
  >>> s = Student()  # 创建实例对象
  >>> def set_age(self, age):  # 定义方法
  ...     self.age = age
  ...
  >>> from types import MethodType
  >>> s.set_age = MethodType(set_age, s)  # 绑定实例方法
  >>> s1 = Student()  # 新实例
  >>> s.set_score(99)  # 测试类方法绑定
  >>> s1.set_score(98)
  >>> s.set_age(20)  # 测试实例方法绑定
  >>> s1.set_age(19)
  ```

- 类变量`__slots__`用于保存类对应的实例能添加的属性(元组的形式)，不继承；
- 内置装饰器`@property`：将类方法转化为属性，通过setter方法和getter方法操作属性；  
  例：
  ```python
  class Student(object):

    @property
    def score(self):
        return self._score

    @score.setter
    def score(self, value):
        if not isinstance(value, int):
            raise ValueError('score must be an integer!')
        if value < 0 or value > 100:
            raise ValueError('score must between 0 ~ 100!')
        self._score = value
    ```

    通过装饰器使得方法按属性方式调用(或给属性加方法)，方便且可限制；  
    测试如下：
    ```python
    >>> s = Student()
    >>> s.score = 60 # OK，实际转化为s.set_score(60) >>> s.score # OK，实际转化为s.get_score()
    60
    >>> s.score = 9999
    Traceback (most recent call last):
      ...
    ValueError: score must between 0 ~ 100!
    ```

- 多重继承：
  * MixIn：通过组合多个父类，给子类构造多功能(如Python自带了TCPServer和UDPServer这两类网络服务，而要同时服务多个用户就必须使用多进程或多线程模型，这两种模型由ForkingMixIn和ThreadingMixIn提供)；
- 类定制：
  * `__str__()` `__repr__()` 定义显示的类信息(用户向，调试开发向)；
  * `__iter__()` 转换为迭代对象(需要相应的`__next__()`方法)；
  * `__getitem__()` `__setitem__()` `__delitem__()`
  * `__getattr__()` 动态返回属性；
  * `__call__()` 定义实例调用方法，使得实例称为`Callable`对象，可用`Callable(object)`检验；
- 枚举类
  * 通过大写变量定义常量，简单但类型为`int`且无法限制其可变；
  * 对一组常量，可通过定义类，其每一唯一实例为一个常量；
  * `Enum` Class in Module enum, 定义枚举类；
    ```python
    from enum import Enum

    Month = Enum('Month', ('Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'))
    ```

    通过以上代码获得了Month类型的枚举类，可以直接使用Month.Jan来引用一个常量，或者枚举它的所有成员：
    ```python
    for name, member in Month.__members__.items():
        print(name, '=>', member, ',', member.value)
    ```

    value属性则是自动赋给成员的int常量，默认从1开始计数。如果需要更精确地控制枚举类型，可以从Enum派生出自定义类：
    ```python
    from enum import Enum, unique

    @unique
    class Weekday(Enum):
        Sun = 0 # Sun的value被设定为0
        Mon = 1
        Tue = 2
        Wed = 3
        Thu = 4
        Fri = 5
        Sat = 6
    ```

    @unique装饰器可以帮助我们检查保证没有重复值。
    既可以用成员名称引用枚举常量，又可以直接根据value的值获得枚举常量。
- 元类(Metaclass)
  * (metaclass主要用于修改类定义，比如API、ORM使用，绝大多数情况不需要)
  * 动态语言和静态语言最大的不同，就是函数和类的定义，不是编译时定义的，而是运行时动态创建的；
  * Python中的类也是对象；
  * `type(name, bases, dict)` 动态创建新类，参数为：类名、继承的父类元组、方法与函数绑定的字典；
  * 元类是创建类的模板，`type`是内建的元类；
  * 定义元类需要其有`__metaclass__`属性，属性内容包含`type`或其子类化的内容；
  * Python创建类时，先查找`__metaclass__`属性，找不到再在父类中找、在模块层次中找，最终调用`types`；

<h3 id="10">Python错误、调试和测试</h3>
- 错误处理：
  * 错误码方式不明确、不简洁；
  * `try... except... finally...` 机制，try语句块如果执行出错，则后续代码不会继续执行，而是直接跳转至错误处理代码(except语句块)，如果没有错误则跳过except语句块(可使用else语句块)，最后，如果有finally语句块，则执行finally语句块；
  * 如果错误没有被捕获，它就会一直往上抛，最后被Python解释器捕获，调用错误堆栈，打印一个错误信息，然后程序退出；
  * `logging` 模块，可用于记录错误信息；
    ```python
    import logging

    def foo(s):
        return 10 / int(s)

    def bar(s):
        return foo(s) * 2

    def main():
        try:
            bar('0')
        except Exception as e:
            logging.exception(e)
        else:
            print('No exception')
        finally:
            print('Finally...')

    main()
    print('END')
    ```

  * 错误是类，均继承自`BaseException`类，可自定义错误类，并用`raise`语句抛出错误实例；
  * 在`except`语句中，`raise`抛出错误，可合理转化错误类型或将错误抛给上层调用去处理；
- 调试：
  * `print` 在需要判断的代码处打印信息以调试，会导致大量垃圾信息；
  * GUWP5STP57 WUW95SDW9
  * 断言(The Assert Statement)
    * `assert statement[, expression]` 断言判断，若statement为false则抛出AssertionError，打印expression信息，否则继续执行代码；
    * 启动Python解释器时可以用`-O`参数来关闭assert；
  * `logging` 记录错误信息(最佳方式)：
    ```python

    import logging
    logging.basicConfig(level=logging.INFO)

    s = '0'
    n = int(s)
    logging.info('n = %d' % n)
    print(10 / n)
    ```

    指定记录信息的级别，有debug, info, warning, error等。在代码需要记录处定义各级别的输出信息，最后统一控制即可；
  * 调试器pdb：调用Python解释器时使用参数`-m pdb`启用调试器，命令`l`查看代码、`n`单步执行、`p 变量名`查看变量、`q`退出；
  * `pdb.set_trace()` 断点设置，需要`import pdb`，在解释器执行到断点处时自动进入pdb调试环境，命令`c`继续执行；
  * IDE
- 单元测试
  > 测试驱动开发(TDD, Test-Driven Development)，要求在编写某个功能的代码之前先编写测试代码，然后只编写使测试通过的功能代码，通过测试来推动整个开发的进行(不可运行/可运行/重构)。这有助于编写简洁可用和高质量的代码，并加速开发过程。

  * 单元测试是用来对一个模块、一个函数或者一个类来进行正确性检验的测试工作。
  * 单元测试的测试用例要覆盖常用的输入组合、边界条件和异常。
  * 单元测试代码要非常简单，如果测试代码太复杂容易有bug。单元测试通过了并不意味着程序就没有bug了，但是不通过程序肯定有bug。
  * `unittest` Package, 单元测试框架：
      + 引用`import unittest`；
      + 测试类继承自`unittest.TestCase`；
      + 测试方法命名为`test_xxx`；
      + 运行：编写为可执行`.py`文件：
        ```python
        if __name__ == '__main__':
            unittest.main()
        ```

        或调用解释器时使用`-m unittest`；
      + `setUp(self)` `tearDown(self)` Hook method, setting up / deconstracting fixture, 每一测试方法运行前/后自动调用以创建/解构测试的依赖，可添加数据库链接等操作；
- 文档测试(doctest)
  * Module, a framework for running examples in docstrings;
  * doctest使用Python object的__doc__来记录对应module、class、method测试的测试用例，书写形式即python CLI中交互执行程序时输入输出的形式(推荐测试代码后将交互粘贴作为doctest)；
  * 运行：
    ```python
    if __name__ == '__main__':
        import doctest
        doctest.testmod()
    ```

    或调用解释器时使用`-m doctest`；

<h3 id="11">Python I/O编程(同步I/O)</h3>
- 速度不匹配，同步I/O时CPU和内存等待外设；
- 文件读写：
  * 读取文件：
      + `open(file, mode='rt', buffering=-1)` built-in function in module io, 打开文件为文件对象，默认模式`rt`为文本读；
      + `read([size])` 读取文件对象的n个字符或全部内容为str对象到内存；
      + `readlines()` 读取全部内容为按行分隔的list；
      + `close()`
  * file-like Object：具有read方法的类对象，如常用于临时缓冲的`StringIO`；
  * 二进制文件：`open(file, mode='rt')` 函数的模式改为包含`b`而非`t`即可；
  * 字符编码：`open(file, mode='rt', encoding=None, errors=None)` 编码如'gbk'，编码错误处理如忽略'ignore'；
  * 写文件：`open`模式为`w`后调用方法`write(string)`写入内存，执行`close()`后写入外设文件；
  * `with ... as ...`
- StringIO, class in module io, Text I/O implementation using an in-memory buffer, 内存中读写str，方法有`wirte read readline getvalue tell seek close`等；
- BytesIO, class in module io, Buffered I/O implementation using an in-memory bytes buffer, 内存中读写bytes；
- 操作文件和目录(os module)
  * `os.name` 操作系统类型：POSIX, NT等；
  * `os.uname()` 返回操作系统信息；
  * `os.environ` 保存操作系统的环境变量的变量，可调用`os.environ.get('key')`查看某环境变量的值；
  * `os.mkdir(path, mode=511)` `os.rmdir(path)` `os.rename(src, dst)` `os.remove(path)`
  * `os.path` module posixpath in os, Functions:
      + `abspath(path)` 返回绝对路径；
      + `join(a, *p)` 将两个以上pathname链接，绝对目录应置于最前；
      + `split(p)` `splitext(p)` 分隔pathname为二元组(按目录最后斜线分) / 分离后缀；
      + `isdir(s)` `isfile(path)` `islink(path)` 检验是否为目录 / 文件 / 软连接；
      + `getsize(filename)` 返回文件大小；
  * `os.link(src, dst)` `os.listdir(path=None)` `os.chmod(path, mode)` `os.chown(path, uid, gid)` `os.getuid()`
- 序列化(Pickling)
  * 变量从内存中变成可存储或传输的过程为序列化；把变量内容从序列化的对象重新读到内存里称之为反序列化，即unpickling；
  * `pickle` module, Create portable serialized representations of Python objects, Functions:
      + `dumps(obj)` 把对象序列化成一个bytes(bytes可写入文件等)；
      + `dump(obj, file)` 把对象序列化后写入一个file-like Object；
      + `loads(data)` 把bytes数据反序列化为对象；
      + `load(file)` 把file-like object反序列化为对象；
  * 同所有编程语言特有的序列化问题一样，Python的Packle只能用于Python，并且可能不同版本的Python彼此都不兼容；
  * 需要独立于语言的标准化数据交换格式，如`XML / JSON`；
  * `json` package, Python对象与JSON格式转换：
      + `Class JSONEncoder(builtins.object)`

        |Python         |JSON   |
        |-----          |-----  |
        |dict           |object |
        |list, tuple    |array  |
        |str            |string |
        |int, float     |number |
        |True           |true   |
        |False          |false  |
        |None           |null   |

      + `dumps(obj)` 序列化Python的object为JSON格式化的str，可选参数`default(obj)`为返回可序列化类型的obj的function，用于自定义encoder；
      + `dump(obj, fp)` 序列化Python的object为JSON格式化流写入一个file-like Object；
      + `Class JSONDecoder(builtins.object)`

        |JSON           |Python |
        |-----          |-----  |
        |object         |dict   |
        |array          |list   |
        |string         |str    |
        |number(int)    |int    |
        |number(float)  |float  |
        |true           |True   |
        |false          |False  |
        |null           |None   |

      + `loads(str)` 反序列化JSON字符串为Python的object，可选参数`objct_hook()`为处理反序列化的结果的function，用于自定义decoder；
      + `load(fp)` 反序列化从file-like Object中读取的字符串为Python的object；

<h3 id="12">Python进程和线程</h3>
- 多进程(multiprocessing)
  * `os.fork()` Function in Module os, Fork得到一个子进程，返回`0`给子进程并返回子进程进程号(PID)给父进程；(无法用于Windows)
  * `os.getpid()` Function in Module os, 返回当前进程号；
  * `os.getppid()` Function in Module os, 返回父进程号；
  * `multiprocessing` Package, 跨平台的模块；
  * `Process(multiprocessing.process.BaseProcess)` Class in Module multiprocessing.process, 进程对象类；
      + `__init__(self, group=None, target=None, name=None, args=(), kwargs={}, *, daemon=None)` class constructor, group只为None，target为run调用对象，name为进程名，args和kwargs为target参数元组和字典；
      + `start(self)` Method, 开始子进程(child process)；
      + `run(self)` 子进程(sub-process)中执行的方法(即子进程任务activity)，可在子进程重写；
      + `join(self, timeout=None)` 等待子进程结束，通常用于进程同步；
      + `terminate(self)` 结束进程；
  * `Pool(processes=None, initializer=None)` Method of Class `DefaultContext(BaseContext)` in Module multiprocessing.context, 返回进程池对象，processes参数为进程数限制(默认为`os.cpu_count()`即cpu数；
  * `Pool(builtins.object)` Class in Module multiprocessing.pool in Package multiprocessing, 进程池类；
      + `apply_async(self, func[, args[, kwds]])` 为进程池进程异步(避免等待)调用func，传递参数args和kwds；
      + `map_async(func, iterable)` 异步映射方法到迭代器每一item；
      + `close()` 阻止新任务提交到进程池，任务完成后worker process退出；
      + `terminate()` 立即停止worker process；
      + `join()` 等待worker process退出，必须用于`close()`或`terminate()`后；
  * `subprocess` Module, 可交互I/O流的子进程；
      + ` subprocess.run(args, *, stdin=None, input=None, stdout=None, stderr=None, shell=False, timeout=None, check=False)` Run the command described by args. Wait for command to complete, then return a CompletedProcess instance;
      + `class subprocess.CompletedProcess` The return value(args, returncode, stdout, stderr, check_returncode()) from run(), representing a process that has finished;
      + `class subprocess.Popen(args, bufsize=-1, executable=None, stdin=None, stdout=None, stderr=None, preexec_fn=None, close_fds=True, shell=False, cwd=None, env=None, universal_newlines=False, startupinfo=None, creationflags=0, restore_signals=True, start_new_session=False, pass_fds=())` Popen Constructor, Execute a child program in a new process, 基本进程创建和管理(处理convenience functions未覆盖的场景);
      + `Popen.communicate(input=None, timeout=None)` Interact with process: Send data to stdin. Read data from stdout and stderr, until end-of-file is reached(returns a tuple (stdout_data, stderr_data). The data will be bytes or, if universal_newlines was True, strings.). Wait for process to terminate. The optional input argument should be data to be sent to the child process, or None, if no data should be sent to the child. The type of input must be bytes or, if universal_newlines was True, a string. Note that if you want to send data to the process’s stdin, you need to create the Popen object with stdin=PIPE. Similarly, to get anything other than None in the result tuple, you need to give stdout=PIPE and/or stderr=PIPE too. The child process is not killed if the timeout expires, so in order to cleanup properly a well-behaved application should kill the child process and finish communication;
      + `subprocess.PIPE` Special value that can be used as the stdin, stdout or stderr argument to Popen and indicates that a pipe to the standard stream should be opened. Most useful with Popen.communicate();
      +  `subprocess.call(args, *, stdin=None, stdout=None, stderr=None, shell=False, timeout=None)` Run the command described by args. Wait for command to complete, then return the returncode attribute(One of the these three functions comprised the high-level API to subprocess prior to Python 3.5);
  * 进程间通信`Exchanging objects between processes`
      + Module multiprocessing supports two types of communication channel between processes:`Queue`, `Pipes`;
      + `Queue` Allows multiple producers and consumers(Queues are thread and process safe);
      + `class multiprocessing.Queue([maxsize])` Returns a process shared queue implemented using a pipe and a few locks/semaphores, 需要import模块queue以正确抛出异常；(method详细参见queue模块)
      + `Pipes` For a connection between two processes;
      + `multiprocessing.Pipe([duplex])` Returns a pair (conn1, conn2) of Connection objects representing the ends of a pipe.  If duplex is True (the default) then the pipe is bidirectional. If duplex is False then the pipe is unidirectional: conn1 can only be used for receiving messages and conn2 can only be used for sending messages;
- 多线程
  * Python解释器由于设计时有GIL(Global Interpreter Lock)，导致了多线程无法利用多核(多进程可以)；
  * Python的标准库提供了两个模块：`_thread`和`threading`，`_thread`是低级模块，`threading`是高级模块，对`_thread`进行了封装；
  * `threading.current_thread()` 返回当前线程对象，
  * `threading.main_thread()` 返回主线程对象，通常即Python解释器启动进程；
  * `threading.enumerate()` 返回当前存活(alive)的所有线程对象列表；
  * `class threading.Thread(group=None, target=None, name=None, args=(), kwargs={}, *, daemon=None)` Class Process类似于它；
      + `run()` Method representing the thread's activity;
      + `start()` Start the thread's activity;
      + `join()` Wait util the thread terminates;
  * `class threading.Lock` The class implementing primitive lock objects. Once a thread has acquired a lock, subsequent attempts to acquire it block, until it is released; any thread may release it:
      + `acquire([blocking=True, ][timeout=-1])` 获取锁；
      + `release()` 释放锁(任何线程都可调用，不限制于获取锁的线程)；
- ThreadLocal
  * `class threading.local` A class that represents thread-local data(data whose values are thread specific), 其类对象的属性值对不同线程不同，各自独立操作，便于线程内参数传递；
- 进程与线程
  * 实现多任务，通常设计Master-Worker模式，Master负责分配任务，Worker负责执行任务；
  * 多进程：
      + 稳定性高；
      + 创建进程代价大，进程数限制大；
  * 多线程：
      + 速度稍快；
      + 稳定性差；
  * 线程切换：
      + 保存现场，准备新环境；
      + 过多任务导致大量资源消耗在任务外，效率下降；
  * 计算密集型 vs. IO密集型：
      + 计算密集型主要消耗CPU资源，任务数量等于CPU数即可，需要代码运行效率高（Python效率低）；
      + I/O密集型主要是网络、磁盘等操作，任务时间大多在等待I/O完成，需要代码开发效率高（代码量少），脚本语言适合；
- 分布式进程
  * 利用操作系统提供的异步IO支持，用单进程单线程模型来执行多任务的模型称为事件驱动模型；
  * 对应到Python语言，单进程的异步编程模型称为协程，有了协程的支持，就可以基于事件驱动编写高效的多任务程序。

<h3 id="13">Python正则表达式</h3>


<h3 id="14">Python常用模块</h3>
- `datetime`
- `collections`
- `base64`
- `struct`
- `hashlib`
- `itertools`
- `contextlib`
- `XML`
- `HTMLParser`
- `urllib`
- `PIL`
- `venv`

<h3 id="15">Python图形界面</h3>

<h3 id="16">Python网络编程</h3>
- TCP/IP简介
- TCP编程
- UDP编程

<h3 id="17">Python电子邮件</h3>
- SMTP发送邮件
- POP3接收邮件

<h3 id="18">Python数据库</h3>
- SQLite
  * <TODO>
- MySQL
  * 执行INSERT等操作后要调用commit()提交事务；
  * MySQL的SQL占位符是%s；
  * 例：
    ```python
    # 导入MySQL驱动:
    >>> import mysql.connector
    # 注意把password设为你的root口令:
    >>> conn = mysql.connector.connect(user='root', password='password', database='test')
    >>> cursor = conn.cursor()
    # 创建user表:
    >>> cursor.execute('create table user (id varchar(20) primary key, name varchar(20))')
    # 插入一行记录，注意MySQL的占位符是%s:
    >>> cursor.execute('insert into user (id, name) values (%s, %s)', ['1', 'Michael'])
    >>> cursor.rowcount
    1
    # 提交事务:
    >>> conn.commit()
    >>> cursor.close()
    # 运行查询:
    >>> cursor = conn.cursor()
    >>> cursor.execute('select * from user where id = %s', ('1',))
    >>> values = cursor.fetchall()
    >>> values
    [('1', 'Michael')]
    # 关闭Cursor和Connection:
    >>> cursor.close()
    True
    >>> conn.close()
    ```

- SQLAlchemy
  * <TODO>

<h3 id="19">Python WEB开发</h3>
- HTTP协议
- HTML
- WSGI接口
- WEB框架
- 模板

<h3 id="20">Python异步I/O</h3>
- 协程
- asyncio
- async/await

<h3 id="21">Python实例</h3>
- 
