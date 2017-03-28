Python 爬虫笔记

March of 2017.

基于爬虫笔记[崔庆才的个人博客](http://cuiqingcai.com/1052.html)，python版本2.7，有改动。

---

> ## 目录
> - [一、基础知识](#1)
> - [二、urllib module](#2)
> - [三、urllib2 module](#3)
> - [四、cookielib module](#4)
> - [五、正则表达式](#5)

---

<h2 id="1">一、基础知识</h2>
1. 爬虫：Crawler ，Web Spider，是一种按照一定的规则，自动的抓取万维网信息的程序或者脚本；
2. URL：Uniform Resource Locator ，统一资源定位符，是互联网上标准资源的地址，由协议、资源存储主机的ip地址、资源在主机的目录构成；
URI：Uniform Resource Identifier，统一资源标识符，URL是其子集；
3. Get vs. Post:
  - Http定义了与服务器交互的不同方法，最基本的方法有4种，分别是GET，POST，PUT，DELETE，对应着对这个资源的查，改，增，删4个操作；
  - GET请求的数据会附在URL之后（就是把数据放置在HTTP协议头中），以?分割URL和传输数据，参数之间以&相连。如果数据是英文字母/数字，原样发送，如果是空格，转换为+，如果是中文/其他字符，则直接把字符串用BASE64加密；POST把提交的数据则放置在是HTTP包的包体中；
  - GET方式提交的数据(含URL)最多只能是1024字节，理论上POST没有限制；
  - POST的安全性要比GET的安全性高：通过GET提交数据，用户名和密码将明文出现在URL后。

<h2 id="2">二、urllib module</h2>
1. High-Level Interface
  - `urlopen(url[, data[, proxy[, context]]])` 打开`url`所指的网络对象以读取，返回类文件对象；
    + 类文件对象的方法：`read(), readline(), readlines(), fileno, close(), info(), getcode(), geturl()`；
    + `data`用于HTTP的POST请求；
    + `proxies`为协议scheme与代理proxy的字典；
    + `context`为`ssl.SSLContext`实例用于HTTPS协议的SSL配置；
  - `urlretrieve(url[, filename[, reporthook[, data]]])` 将url指示的网络对象复制为本地文件；
    + 返回元组`(filename, headers)`指示本地文件名和`urlopen`的`info()`方法返回值；
    + `filename`指定文件名，否则自动生成临时文件(/temp/...)；
    + `reporthook` 指定`hook function`，网络连接建立和之后每块block读取时调用；
    + `data` HTTP协议时使用；
  - `urlcleanup()` 清除调用`urlretrieve`建立的缓存cache；
2. Utility Functions
  - `quote(string[, safe])` 将string中的特殊字符用`%xx`转义替换，即编码；`safe`指明不替换的特殊字符，默认为`/`；
  - `quote_plus(string[, safe])` 相比`quote`，额外替换空格为加号，`string`中的加号则转义，没有默认`safe`；
  - `unquote(string)` `unquote_plus(string)` 反替换；
  - `urlencode(query[, doseq])` 转换字典对象或二元组序列为`percent-encoded`字符串；
    + 字符串由`&`字符分隔的经过`quote_plus()`编码的`key-value`对组成；
  - `pathname2url(path)` 将本地语法表示的`path`转换为URL组成部分的形式，返回值已经过`quote()`编码；
  - `url2pathname(url)` 同上相反，使用`unquote`解码`path`；
  - `getproxies()` 返回协议与代理服务器URL的映射字典，搜索`environment`中`<scheme>_proxy`命名的变量；

<h2 id="2">三、urllib2 module</h2>
1. `urlopen(url[, data[, timeout]])` Function,打开url，返回file-like对象；
  - 调用当前安装的全局`OpenerDirector`的`open`方法；
  - `url` 字符串或Request对象;
  - `data` 指定发送给服务器的附加字符串数据，仅限HTTP协议使用，会使得HTTP request为POST而非GET；需要是一个标准application/x-www-form-urlencoded 格式的buffer， `urllib.urlencode()`方法 使用一个词典或者二元组的序列为参数，返回这样格式的字符串;
  - `timeout` 超时秒数，data为空时指明形参，仅作用于Http(s)、Ftp；
  - 返回的file-like对象的3个method：
    + `geturl()` 返回所获取资源的URL，真正的URL，通常存在于重定向；
    + `info()` 返回页面的元信息，如`headers`信息以`mimetools.Message`类的实例形式返回；
    + `getcode()` 返回响应的HTTP状态码；
2. `istall_opener(opener)` 安装`OpenerDirector`实例`opener`作为默认的全局opener；
3. `build_opener([handler, ...])` 返回`OpenerDirector`实例`opener`，按所给顺序连接`handler`；
4. `Request(url[, data][, headers])` Class, URL request的抽象；
  - `url` 可用的URL字符串；
  - `data` 同上；
  - `headers` 字典，常用于报头（header）的user-agent值修改；
  - methods: (of Request's public interface, so must be overridden in subclasses)
    + `add_data(data)` 设置request的data；
    + `get_method()` 返回HTTP request method；
    + `has_data()  get_data()` 判断是否有data，取得data；
    + `add_header(key, val)` 添加新的header键值对，同key值时覆盖；
    + `has_header(header)` 判断是否有header在header中；
5. `OpenerDirector` Class, 通过连接`handler`s打开URLs，管理handler连接和recovery from errors;
  - methods:
    + `add_handler(handler)`
    + `open(url[, data][, timeout])`
    + `error(proto[, arg[, ...]])` 处理指定参数下指定协议protocol 的error；
  - OpenDirector 对象打开 URLs 的3个阶段：
    + `protocal_request` 类型的方法预处理request；
    + `protocol_open` 类型的方法处理request；
    + `protocal_response` 类型的方法后续处理response；
6. `BaseHandler` Class, regestered handler的基类，只处理注册，其大多method需要派生类overridden；
7. `ProxyHandler([Proxy, ...])` Class，继承自`BaseHandler`，通过代理进行request，`Proxy`为协议名与代理URLs的字典，默认自动检测；
  - `protocal_open(request)` 方法，`protocal`应替换为具体的协议，通过调用`request.set_proxy()`修改request，再调用后续handler处理request；
8. `HttpPasswordMgr` 保持一个映射`(realm, uri)->(user, password)`；
  - `add_password(realm, uri, user, password)` method, HTTP的Basic验证的realm域、uri、用户名、密码；
9. `HttpBasicAuthHandler([PasswordMgr])` 处理remote host 的认证authentication；
10. `HttpHandler` Class, 继承自`BaseHandler`，处理Http 的URLs 打开；
  - `http_open(req)` method，发送request，根据`req.has_data()`选择 Get 或 Post；
11. `UnknownHandler` Class, 继承自`BaseHandler`，泛用的(catch-all)类，处理未知的URLs；
  - `unknown_open()` method, 抛出`URLError`异常；
12. `URLError` Class，继承自`IOError`，有Data Discriptor`reason`(元组，错误号和错误信息)；
13. `HTTPError` Class，继承自`URLError`和`urllib.addinfourl`，有方法`info()`和Data Discriptor`reason`(元组，错误号和错误信息)、`code`错误号，继承`read()`和`geturl()`；

    ```python
    from urllib2 import Request, urlopen, URLError, HTTPError

    req = Request('http://bbs.csdn.net/callmewhy')

    try:
        response = urlopen(req)
    except URLError, e:
        if hasattr(e, 'code'):
            print 'The server couldn\'t fulfill the request.'
            print 'Error code: ', e.code
        elif hasattr(e, 'reason'):
            print 'We failed to reach a server.'
            print 'Reason: ', e.reason
    else:
        print 'No exception was raised.'
        # everything is fine
    ```

14. 对于各`Handler`，通过调用时给定参数`debuglevel=1`来初始化(`__init__`方法)，开启debug log便于调试；
15. `data`参数常用于Request的header，包括：
  - `User-Agent` 伪装为浏览器，以应对反爬虫等；
  - `Content-Type` 说明MIME类型；在使用REST接口时用于确定HTTP body的解析，有XML RPC调用时`application/xml`，JSON RPC调用时`application/json`，Web表单时`application/x-www-form-urlencoded`；
  - `Referer` 表明访问当前页面的出发页面；应对反盗链，设置为URL自身；
  - `X-Forwarded-For` HTTP请求端真实IP，非RFC标准；伪造IP；
16. `HTTPCookieProcessor([cookiejar])` Class，继承自`BaseHandler`，有属性`cookiejar`(cookielib.CookieJar)；

<h2 id="2">四、cookielib module</h2>
1. `LoadError` 异常，继承自`IOError`，`FileCookieJar`实例从文件load cookies失败时raise；
2. `Cookie` Class, Represents Netscape, RFC 2109 and RFC 2965 cookies；不推荐创建实例；
3. `CookieJar(Policy=None)` Class, 存储HTTP cookies；负责cookie的检索、提取、响应；`Policy`是实现`CookiePolicy`的接口；
4. `FileCookieJar` Class, 继承自`CookieJar`，cookie文件的加载和存储；
  - `filename` 属性，默认cookie文件；
  - `save(filename=None, ignore_discard=False, ignore_expires=False)` 方法，保存cookie文件；
    + `ignore_disgard` 不论cookie是否设为丢弃；
    + `ignore_expires` 不论cookie是否即将过期，会覆盖原cookie文件；
  - `load(filename=None, ignore_discard=False, ignore_expires=False)` 方法，加载cookie文件；
  - `revert(filename=None, ignore_discard=False, ignore_expires=False)` 清除cookies，从文件加载；
5. `CookiePolicy` Class, 决定每个cookie是否要从服务器接受/返回；
6. `DefaultCookiePolicy` Class, 继承自`CookiePolicy`；

<h2 id="2">五、正则表达式</h2>
1. 基础语法
2. 原生字符串 ` r'str' ` 在编程语言层面取字符原义；如正则表达式匹配反斜杠用` '\\\\' `或` r'\\' `；
3. python re module
  - `re.compile(string[,flags])` 返回pattern对象;
    + `string` 目标字符串；
    + `flags` 匹配模式参数；
      * 可用或运算` | `；
      * `re.I` (全拼：IGNORECASE): 忽略大小写；
      * `re.M` (全拼：MULTILINE): 多行模式，改变 ` ^ `和` $ `的行为；
      * `re.S` (全拼：DOTALL): 点任意匹配模式，改变` . `的行为；
      * `re.L` (全拼：LOCALE): 使预定字符类` \w \W \b \B \s \S `取决于当前区域设定；
      * `re.U` (全拼：UNICODE): 使预定字符类` \w \W \b \B \s \S \d \D `取决于unicode定义的字符属性；
      * `re.X` (全拼：VERBOSE): 详细模式，这个模式下正则表达式可以是多行，忽略空白字符，并可以加入注释。
  - pattern object
    + 属性：
      * `flags` 正则匹配标志；
      * `groups` pattern中捕获的组数；
      * `groupindex` 字典，组别名与索引的映射；
      * `pattern` 表达式字符串string；
    + 方法：
      * `match(string[, pos[, endpos]])` 开始、结束查找的位置`pos``endpos`
      * `search(string[, pos[, endpos]])`
      * `findall(string[, pos[, endpos]])`
      * `finditer(string[, pos[, endpos]])`
      * `split(string[, maxsplit])`
      * `sub(repl, string[, count])`
      * `subn(repl, string[, count])`
  - #以下为匹配所用函数：（`pattern`生成时指明`flags`的，匹配时不传入）
    + `re.match(pattern, string[, flags])` 从`string`0位置匹配，失败返回`None`，成功则终止匹配返回match object；
    + `re.search(pattern, string[, flags])` 检索`string`是否含有匹配，返回`None`或match object；
    + `re.findall(pattern, string[, flags])` 搜索`string`，以列表形式返回全部能匹配的子串，当匹配对象含多个分组(groups)时为元组的列表；
    + `re.finditer(pattern, string[, flags])` 搜索`string`，返回一个顺序访问每一个匹配结果（Match对象）的迭代器；
    + `re.split(pattern, string[, maxsplit][, flags])` 将`string`按`pattern`分割，返回分割后的子串列表，`maxsplit`用于指定最大分割次数，默认`string`完全分割；
    + `re.sub(pattern, repl, string[, count][, flags])` 使用`repl`替换`string`中每一个匹配的子串后返回替换后的字符串；
      * 当`repl`是一个字符串时，可以使用\id或\g、\g引用分组，但不能使用编号0；
      * 当`repl`是一个方法时，该方法应当只接受一个参数（Match对象），并返回一个字符串用于替换（返回的字符串中不能再引用分组）；
      * `count`用于指定最多替换次数，不指定时全部替换；
    + `re.subn(pattern, repl, string[, count][, flags])` 返回元组`(sub(repl, string[, count]), 实际替换次数)`；
  - match object
    + 属性：
      * `string` 匹配时使用的文本；
      * `re` 匹配时使用的Pattern对象；
      * `pos` 文本中正则表达式开始搜索的索引值，与`Pattern.match()`和`Pattern.seach()`方法的同名参数相同；
      * `endpos` 文本中正则表达式结束搜索的索引值，与`Pattern.match()`和`Pattern.seach()`方法的同名参数相同；
      * `lastindex` 最后一个被捕获的分组在文本中的索引，如果没有被捕获的分组，将为None；
      * `lastgroup` 最后一个被捕获的分组的别名，如果这个分组没有别名或者没有被捕获的分组，将为None；
    + 方法：
      * `group([group1, …])` 获得一个或多个分组截获的字符串；指定多个参数时将以元组形式返回。group1可以使用编号也可以使用别名；编号0代表整个匹配的子串；不填写参数时，返回group(0)；没有截获字符串的组返回None；截获了多次的组返回最后一次截获的子串；
      * `groups([default])` 以元组形式返回全部分组截获的字符串。相当于调用group(1,2,…last)。default表示没有截获字符串的组以这个值替代，默认为None；
      * `groupdict([default])` 返回以有别名的组的别名为键、以该组截获的子串为值的字典，没有别名的组不包含在内。default含义同上；
      * `start([group])` 返回指定的组截获的子串在string中的起始索引（子串第一个字符的索引）。group默认值为0；
      * `end([group])` 返回指定的组截获的子串在string中的结束索引（子串最后一个字符的索引+1）。group默认值为0；
      * `span([group])` 返回(start(group), end(group))；
      * `expand(template)` 将匹配到的分组代入template中然后返回。template中可以使用\id或\g引用分组，但不能使用编号0。\id与\g是等价的；但\10将被认为是第10个分组，如果你想表达\1之后是字符’0’，只能使用\g0；



