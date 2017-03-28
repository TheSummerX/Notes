## Fundamental Programming Structures in Java

> Directory

> * [1. A Simple Java Program](#11)
> * [2. Comments](#12)
> * [3. Data types](#13)
> * [4. Variables](#14)
> * [5. Operators](#15)
> * [6. Strings](#16)
> * [7. Input and Output](#17)
> * [8. Control Flow](#18)
> * [9. Big Numbers](#19)
> * [10. Arrays](#110)

**First and Foremost:Java is _case sensitive_**

<h4 id="11"> 1. A Simple Java Program</h4>

```Java
public class Sample
{
   public static void main(String[] args)
   {
      System.out.println("We will not use 'Hello, World!'");
   }
}
```
- The keyword _public_ is called an access modifier.  
- Everything in a Java program lives inside a class.In other words,classes are the building blocks of Java.
- Class names must begin with a letter, and after that, they can have any combination of letters and digits. The length is essentially unlimited. You cannot use a Java reserved word for a class name.The standard naming convention is that class names are nouns that start with an uppercase letter. If a name consists of multiple words, use an initial uppercase letter in each of the words.  
- In Java all functions are methods of some class.(The term “method” is Java-speak for function.)Method names better start with lowercase letters and use an initial uppercase letter in each of the name nouns.
- The Java virtual machine always starts execution with the code in the _main_ method in the class you indicate. Thus, you must have a _main_ method in the source file for your class for your code to execute.
- According to the Java Language Specification, the _main_ method must be declared public.The _main_ method in Java is always static.
- The braces `{ }` delineate the parts (usually called blocks ) in the program.
- The _void_ keyword indicates that the _main_ method does not return an “exit code” to the operating system. If the _main_ method exits normally, the Java program has the exit code _0_ , indicating successful completion. To terminate the program with a different exit code, use the _System.exit_ method.
- Java uses the general syntax **object . method ( parameters )** as its equivalent of a function call.

<h4 id="12"> 2. Comments</h4>
- `//` Inline comments
- `/*   */` Comment block
- `/**  */` Automatic documentation generation

<h4 id="13"> 3. Data types</h4>
- Eight Primitive Types
  - Four integer types: _int short long byte_  
        The ranges are fixed: int-4bytes; short-2; long-8; byte-1.  
        Long 后缀 `L`; Hexadecimal(16进制) 前缀 `0x`;Octal(8进制，不推荐使用) 前缀 `0`;Binary(2进制) 前缀 `0b`;Number literals(字面常量数字) 可使用 `_` 表示间隔，不编译。
  - Two floating-point number types: _float double_  
        _Double_ is the generally considered type,optionally supplied with a _D_ suffix._Float_ has a suffix _F_.  
        When needing precise numerical computations without roundoff errors, use the _BigDecimal_ class.
  - Character type: _char_  
        _Char_ is in the UTF-16 encoding.(不推荐使用)  
        Better off treating strings as abstract data types.
  - Boolean type: _boolean_
- Others  
    mainly objects of specific classes.

<h4 id="14"> 4. Variables</h4>
- Syntax  
    ` Variable_Types Variable_Names; `
- A variable name must begin with a letter and must be a sequence of letters or digits.  
    _Note:Even though `$` is a valid Java letter, you should not use it in your own code. It is intended for names that are generated by the Java compiler and other tools._
- Initializing `=`
- Constants _final_  
    It is customary to name constants in all uppercase.  
    It is probably more common in Java to create a constant so it’s available to multiple methods inside a single class. These are usually called _class constants_ . Set up a _class constant_ with the keywords _static final_ .

<h4 id="15"> 5. Operators</h4>
- The usual arithmetic operators  
    ` + - * / `  
    ` % ` Integer remainder(modulus)  
    ` a += b; ` is equavalent to ` a = a + b; `
- Increment and Decrement  
    ` ++ -- `
- Relational and _boolean_  
    ` == != < > <= >= `
    ` && || ! `
    ` ?: ` _condition?experssion1:expression2_
- Bitwise
    ` & | ^ ~ ` (and or xor not)  
    ` << >> ` (shift, `<<` adds 0, `>>` extends the sign bit into the top bits)
    ` >>> ` (fills the top bits with 0s)
- Mathematical Functions and Constants  

    ```Java
    Math.sqrt(x); //square root 平方根
    Math.pow(a,b); //a的b次幂
    Math.sin(); //.cos .tan .atan
    Math.exp(); //.log .log10
    Math.PI;
    Math.E;
    ```
    `import static java.lang.Math.*;` //avoid the _Math_ prefix
- Conversions between Numeric Types  
    - Without information loss:  
        byte -> short -> int -> long  
        char -> int  
        int -> double  
        float -> double
    - May lose precision  
        int -> float  
        long -> float  
        long -> double
    - Automatically convert
    - Cast  
        Syntax ` (target_type) variable_name `  
        _Note: No casting between _boolean_ values and any numeric type.
- Parentheses and Operator Hierarchy
    - Operations in parentheses have a higher precedence
    - Most operators are left-associative(processed from left to right)
    - `=` is right-associative
- Enumerated Types(枚举)
    - An enumerated type has a finite number of named values.
    - Syntax `enum type_name { named_values };`
    - The special value _null_

<h4 id="16"> 6. Strings</h4>  
    The standard Java library contains a predefined class called _String_.

- Substring  
    The _substring_ method of the _String_ class.  
    ` string_instance_name.substring(a,b);` 获取位置a(include)到b(exclude)的子串
- Concatenation
    - `+`
    - A value is automatically converted into a string in string concatenation.
- Immutable(不可更改)  
    Strings are immutable.  
    不可更改指的是具体string包含的值，但可以通过string对象引用实现更改。  
    string常量用于共享，其值由于不可更改则利于共享。  
    比如如下更改：

    ```Java
    String astring = "abc";
    astring = astring.substring(2,3) + "d";
    ```
    实现了 _astring_ 更改为 "abd" 而_string_ "abc" 并没有更改为 "abd" 。 
    Java suspect that most of the time,strings are compared other than changed.So sharing advantages.  
    自动内存回收
- String Equality
    - _equals_ method  
        ` a.equals(b) ` test if the strings a and b are equal.
    - _equalsIgnoreCase_ method
- Empty and Null String
    - Null: No object is currently associated with the string variable.  
        ` if (str == null) `  
        **Note: It's an error to invoke a method on a _null_ value.**
    - Empty: `""`.A string of length 0.  
        ` String astring = ""; `  
        ` if (str.length() == 0) `
        ` if str.equals("") `
- Code Points and Code Units
    - 编码字符集(CCS,Coded Character Set)中每一个字符都和一个编号对应,这个编号就是代码点（Code Point）。
    - **Unicode** 目前的Unicode字符分为17组编排，每组称为平面(plane)，范围是 U+0x0000 ~ U+0x10FFFF。  
        Plane 0 是基本多文种平面BMP(Basic Multilingual Plane)，范围 U+0x0000 ~ U+0xFFFF。 Plane 0 的 U+0xD800 ~ U+0xDFFF，共2048个码位，是代理区（Surrogate）。  
        UTF-16(Unicode Transfer Format)是Unicode字符编码五层次模型的第三层：字符编码表（Character Encoding Form，也称为 storage format）的一种实现方式。码元为2字节(16bits)。BMP定义的字符用1码元表示，辅助(supplementary)平面定义的字符(U+ox10000 ~ U+ox10FFFF)用2码元以代理对(sorrogate pair,高/低位代理码都位于代理区)形式表示。
    - 通用字符集（Universal Character Set, UCS）是由ISO制定的ISO 10646（或称ISO/IEC 10646）标准所定义的标准字符集。UCS-2用两个字节编码。  
    - Java中 _string_ 以_char_ 值序列实现，而 _char_ 为UTF-16 编码的码元(code unit)，字符为code point，即:  
        `1 code point = 1/2 code unit(s)`  
        string 长度应该指字符数，即code points.
    - The _length_ method yields the number of code units 
    - The _codePointCount_ method yields the number of code points
    - The _charAt(n)_ method returns the code unit at position n
    - The _codePointAt(index)_ method returns code point at the _i_th code point.The _offsetByCodePoints(0,i) gets the index._
- The _string_ API(Application Programming Interface)
    - **java.lang.string** _java v1.0_
        - `char charAt(int index)`
        - `int codePointAt(int index)` _5.0_
        - `int offsetByCodePoints(int startIndex,int cpCount)` _5.0_
        - `int compareTo(String other)` 比较string的字典顺序先后，比other后则是正，前则是负，同则是0.
        - `boolean endsWith(String suffix)` string是否以suffix结尾
        - `boolean equals(Object other)`
        - `int indexof(String str)`  
          `int indexof(String str,int fromIndex)`  
          `int indexof(int cp)`  
          `int indexof(int cp,int fromIndex)`  
          返回string中第一个子串str或字符cp从位置0或fromIndex开始的位置index
        - `int lastIndexof(parameter)`  
          最后一个，且从最后位置或fromIndex开始
        - `int length()` 返回的是code unit numbers
        - `int codePointCount(int startIndex,int endIndex)` _5.0_ startIndex含，endIndex不含
        - `String replace(CharSequence oldString, CharSequence newString)` 返回将string中符合oldString的子串全部替换成newString得到的string，CharSequence接受String或StringBuilder对象。
        - `boolean startWith(String prefix)`
        - `String substring(int beginIndex)`  
          `String substring(int beginIndex,int endIndex)`  
          返回子串，从beginIndex含，到串尾或endIndex不含
        - `String toLowerCase()`  
          `String toUpperCase()`  
          返回大小写更改后的string
        - `String trim()` 返回去除头尾空格的string
- The API documentation  
    The API documentation is part of the JDK. It is in HTML format. Point your web browser to the _docs/api/index.html_ subdirectory of your JDK installation
- Building String
    - 键盘输入、文件输入等string需要不断链接新字符，用_concatenate_会每一次都创建新string而低效。
    - _StringBuilder_ class  

    ```Java
    StringBuilder builder = new StringBuilder();    //constructs an empty string builder
    builder.append(char);   //appends a char and returns _this_
    builder.append(str);    //appends a string and returns _this_
    builder.appendCodePoint(int cp);    //appends a code point,converting it into one or two code units, and returns _this_
    String completeString = builder.toString(); //returns a string with the same data as the builder or buffer contents
    ```
    - `StringBuilder insert(int offset,String str)`   
      `StringBuilder insert(int offset,Char c)`  
       在offset插入码元c或string，返回_this_
    - `int length()` 返回code unit 数
    - `void setCharAt(int i,char c)` 设置第i个code unit为c
    - `StringBuilder delete(int startIndex,int endIndex)` 删除startIndex含到endIndex不含的code units，返回_this_

<h4 id="17"> 7. Input and Output</h4>
- Reading Input
    - The Java Standard Input Stream is _System.in_
    - **java.util.Scanner** _v5.0_
        - `Scanner(InputStream in)` 从给定输入流构造(construct)对象(object)
        - `String next()` 读取输入的下个词(空白分界delimited by whitespace)
        - `String nextLine()` 读取输入的下一行
        - `int nextInt()`
        - `double nextDouble()`
        - `boolean hasNext()` 检测是否有下一输入的词word
        - `boolean hasNextInt()`
        - `boolean hasNextDouble()`
    - **java.lang.System** _v1.0_
        - `static Console console()` _v6_ 返回一个Console对象来通过一个控制台窗口与用户交互，如果交互不可实现则返回_null_。控制台窗口运行的程序都可以创建这个Console object
    - **java.io.Console** _v6_
        - `static String readLine(String prompt,Object... args)` 显示提示prompt并读取用户输入直至输入行行末,_args_用于设置格式
        - `static char[] readPassword(String prompt,Object... args)` 特别用于输入密码时，安全考虑密码为an array of characters而非string
- Formatting Output
    - _print()_  输出最大数目的非零数字以尽可能精确
    - _printf("format specifiers",parameters)_ from the C library,将参量用指定格式输出
    - Format Specifier Syntax  
        ` % argument_index $ flag width . precision conversion_character ` (没有空格)  
        - argument_index 指定格式化的参量位置(1-n)，用`$`结尾
        - flag 有 `+`输出正负号；`-`左对齐；`,`设置位数分隔符(1,000)；`#`显示float的小数点或16进制的_0x_；`$`指定格式化参量；`<`格式化取值同前一个值等
        - width 指定输出宽度
        - precision 指定精度
        - conversion_character 指定格式化类型，有 `d`十进制；`x`16进制；`f`定点浮点数；`e`指数浮点数；`a`16进制浮点数；`s`String；`c`字符；`%`百分号等
        ` % argument_index $ flag width t conversion_character ` (没有空格) 用于时间格式化  
            conversion_character 有 `c`星期月日时分秒时区年；`T`24小时时间；`Y`4位年；`b/B/a/A`缩写/全写月/星期；`d/H/M/S`2位日时分秒；等
- File Input and Output
    - 读文件构造_Scanner_对象  
    `Scanner in = new Scanner(Paths.get("input_file"));`
    - 写文件构造_PrintWriter_对象  
    `PrintWriter out = new PrintWriter("myfile.txt");`
    - 文件名中反斜线需要转义(\\表示一个反斜线)
    - 尽量使用绝对路径名，相对路径名相对于JVM(java程序)运行路径
    - 读文件不存在或写文件名不可用时，需要以下一种处理：  
        1. 抛出异常处理  
        `public static void main(String[] args) throws FileNotFoundException`  
        2. 使用Shell的文件重定向关联`System.in`和`System.out`到文件
        `java MyProg < input_file > output_file
    - **java.util,Scanner** _v5.0_
        - Scanner(Path p)
        - Scanner(String str)  
        从指定路径或string读取数据
    - **java.io.PrintWriter** _v1.1_
        - `PrintWriter(String fileName)` 写数据到fileName文件
    - **java.nio.file.Paths** _v7_
        - `static Path get(String pathName)` 构造_Path_,设置路径，如：  
        `Path p = Paths.get("~/doc/");`

<h4 id="18"> 8. Control Flow</h4>
- Block Scope 块作用域
    - The braces `{ }` 
    - Nested block 嵌套
    - May not declare identically named variables in two nested blocks.(嵌套变量名需不同，即嵌套时没有变量重定义)
- Conditional Statements
    - `if (condition) statement1 else statement2`
    - `if (condition1) statement1 else if (condition2) statement2 else statement3`
- Loops
    - `while (condition) statement`
    - `do statement while (condition)`
- Determinate Loop
        - `for (condition) statement` 用每一次迭代更新的变量控制的迭代 通常condition分为变量初始化initialization、判定test、更新update
        - `for` 和 `while` 转换
- Multiple Selections `switch`
    - syntax

    ```Java
    switch (case){
        case case1:
            statement1;
            break;
        case case2:
            statement2;
            break;
        default:
            statement3;
            break;
        }
    ```
    - _case_可以是基本数据类型常量、枚举常量、字符串常量
    - _break_跳出，否则继续向下(`fallthrough`)执行（危险，常导致错误） 通常需要跳出
    - 编译(`javac`)时使用`-Xlint:fallthrough`选项检查_break_是否完备，在不需要检查的_method_处添加注释(annotation)`@SuppressWarnings("fallthrough")`
- Statements That Break Control Flow
    - 未标签(unlabeled)`break` 跳出结束当前指令（如跳出if块、跳出case等）
    - labeled `break` 需要在跳出的块前给出标签(syntax `label :`)

    ```Java
    aLabel:
    while (...){
        for (...){
            break aLabel;
            ...
        }
    }
    //the break jumps to here
    ```
    - `continue` 跳出到最内层循环头，忽略本次迭代`continue`后的指令
    - labeled `continue` 跳出到label处循环头

<h4 id="19"> 9. Big Numbers</h4>
- Classes in the java.math package: `BigInteger` and `BigDecimal` implement arbitrary-precision integer or floating-point numbers arithmetic. 提供更大精度的数字运算，注意是类，不可用`+ - * /`，也没有运算符重载
- **java.math.BigInteger** _v1.1_
    - `BigInteger add(BigInteger other)`    
      `BigInteger substract(BigInteger other)`  
      `BigInteger multiply(BigInteger other)`  
      `BigInteger divide(BigInteger other)`  
      `BigInteger mod(BigInteger other)`  
      加减乘除取余
    - `int compareTo(BigInteger other)` 比较大小，返回值比_other_同0小负大正
    - `static BigInteger valueOf(long x)` 返回_x_值的_big-integer_，即转换
- **java.math.BigDecimal** _v1.1_
    - `BigDecimal add(BigDecimal other)`    
      `BigDecimal substract(BigDecimal other)`  
      `BigDecimal multiply(BigDecimal other)`  
      `BigDecimal divide(BigDecimal other,RoundingMode mode)`  _v5.0_  
      加减乘除，除要提供舍入模式(rounding mode)，四舍五入是`RoundingMode.HALF_UP`
    - `int compareTo(BigDecimal other)`
    - `static BigDecimal valueOf(long x)`      
      `static BigDecimal valueOf(long x,int scale)`  
      转换，_x_或_x/10^scale_

<h4 id="110"> 10. Arrays</h4>
- Definition and initialisation syntax  
    `array_type[] array_variable_name;`  
    `array_type[] array_variable_name = new array_type[array_length];`   
    注意数组array长度固定，_null_和长度为0不同，默认初始化为_number_为_0_,_boolean_为_false_,_objects_为_null_
- The "for each" Loop
    - `for (variable : collection) statement`  
    对于_collection_的每一元素迭代地赋值给_variable_并执行_statement_ 
    _variable_ 得到的是_elements of the array_ 而非_index values_  
    _collection_ 必须是数组或一个实现迭代器接口(iterable interface)的类的对象
    - `Arrays.toString(array_variable_name)` _Arrays_ class _toString_ method 返回数组的元素，方括号括起，逗号分隔
- Array Initializers and Anonymous Arrays
    - `int[] aArray = { 1, 3, 5, 7 };`
    - `new int[] { 1, 3, 5, 7 };`
    - `aArray = new int[] { 1, 3, 5, 7 };`
- Array coping
    - java数组是Arrays类的对象的引用，像C++的堆上的数组的指针，而非栈上的数组
    - 数组复制时使用数组变量名赋值不会创建新数组，如下，两个数组变量名实际引用同一数组

    ```Java
    int[] aArray = { 1, 3 };
    int[] aCopiedArray = aArray;
    aCopiedArray[1] = 2;    //Now aArray[1] is also 2
    ```
    - 使用_Arrays_类的_copyOf_ method复制，可增减数组长度：  
    `Arrays.copyOf(src_array_variable_name,destination_array_length）`  
- Command-Line Parameters
    - Every Java program has a _main_ method with a _String[] args_ parameter. This parameter indicates that the _main_ method receives an array of strings—namely, the arguments specified onthe command line.
    - If the program _Message_ is called as  
        `java Message hello world`  
        then the args array has the following contents:  
        args[0]: "-g"  
        args[1]: "cruel"  
        args[2]: "world"  
- Array sorting 数组排序
    - **java.util.Arrays** _v1.2_
        - `static String toString(Type[] a)` _v5.0_ 参量_a_:An array of type int,long,short.byte,char,boolean,float,or double
        - `static type[] copyOf(type[] a,int length)` _v6_  
          `static type[] copyOf(type[] a,int start,int end)` _v6_  
          返回与一个_a_同类型type[]的数组，长度为_length_或_end-start_
        - `static void sort(type[] a)` 数组排序 using a tuned QuickSort algorithm.
        - `static int binarySearch(type[] a,type v)` 在数组中搜索值，返回其位置或一个负值`r`(-r-1即保持a排序的v应插入的位置)，使用binary search algorithm，可选参量_int start含,int end不含_
        - `static void fill(type[] a,type v)` 设置所有元素为`v`
        - `static boolean equals(type[] a,type[] b)` 判定相同
- Multidimensional Arrays 多维数组
    - Initialization

    ```Java
    int aMultidimensionalArray = {
        { 11, 12 },
        { 21, 22 }
    };
    if (aMultidimensionalArray[0][0] = 11) break;
    ```
    - _for_自增参量遍历不能多维遍历，可以嵌套实现
    - _deepToString_ method 遍历二维数组返回_a quick-and-dirty list of the elements_
- Ragged Array
    - Java中并没有真正的多维数组，它是以数组为元素构造的数组
    - 作为元素的数组可能含有的元素数量不同而参差不齐(ragged)
    - 可以将作为元素的数组以元素方式操作