# Chapter 2：浅谈python 中的模块

# **标准库模块**

#### **1、Python常用模块**

**Python里的import和from...import：**
在Python用import或者from...import来导入相应的模块。模块其实就是一些函数和类的集合文件，它能实现一些相应的功能，当我们需要使用这些功能的时候，直接把相应的模块导入到我们的程序中，我们就可以使用了。这类似于C语言中的include头文件。

在C语言中如果要引用sqrt这个函数，必须用语句"#include<math.h>"引入math.h这个头文件，否则是无法正常进行调用的。类似的，在Python中有一个概念叫做模块（module），这个和C语言中的头文件以及Java中的包很类似，比如在Python中要调用sqrt函数，必须用import关键字引入math这个模块。

+ os模块 ---平台相关模块
+ string模块 ---提供了用于处理字符串类型的函数
+ re模块 ---提供了一系列功能强大的正则表达式工具
+ sys模块 ---提供了函数和变量来处理Python运行时环境的不同部分
+ time模块 ---提供了处理日期和时间的函数，它是建立在C运行时库的简单封装。
+ json模块 ---用于字符串和python基本数据类型间进行转换
+ telnetlib模块---提供了一个 telnet 客户端实现.
+ logging模块 ---日志管理

platform模块--获取操作系统的信息

#### **2、os，sys和platform模块**

+ os.path.exists(path) 如果path存在，返回True；如果path不存在，返回False。
+ os.path.join拼接路径
+ os.chdir() 用于改变当前工作目录到指定的路径。
+ os.system() 执行系统cmd命令

**os._exit()和sys.exit()：**
python的程序有两中退出方式：os._exit()，sys.exit()。
+ os._exit()会直接将python程序终止，之后的所有代码都不会继续执行。
+ sys.exit()会引发一个异常：SystemExit，如果这个异常没有被捕获，那么python解释器将会退出。如果有捕获此异常的代码，那么这些代码还是会执行。

**os.getcwd()、sys.path[0]（sys.argv[0]）的区别：**
+ os.getcwd()取的是起始执行目录
+ sys.path[0]或sys.argv[0]取的是被初始执行的脚本的所在目录
+ os.path.split(os.path.realpath(__file__))[0]取的是__file__所在文件所在目录
+ os.mkdir()创建目录

+ os.listdir()列出目录内容

+ 使用rmdir()删除目录
+ 用remove()删除文件

sys.argv[]sys.argv[]是用来获取命令行参数的，sys.argv[0]表示代码本身文件路径;比如在CMD命令行输入 “python test.py -help”，那么sys.argv[0]就代表“test.py”。

os.path 模块包含了各种处理长文件名(路径名)的函数. 先导入 (import) os 模块, 然后就可以以 os.path 访问该模块.

os.path.isfile()：检查是否为文件；

 **platform模块：**

#### **3、Re模块正则匹配：**

+ \d 匹配任何十进制数；它相当于类 [0-9]。 \D 匹配任何非数字字符；它相当于类 [^0-9]。

+ \s 匹配任何空白字符；它相当于类 [ fv]。 \S 匹配任何非空白字符；它相当于类 [^ fv]。

+ \w 匹配任何字母数字字符；它相当于类 [a-zA-Z0-9_]。

+ \W 匹配任何非字母数字字符；它相当于类 [^a-zA-Z0-9_]。

具有重复功能的元字符：

+ \* 对于前一个字符重复0到无穷次

+ +对于前一个字符重复1到无穷次

+ ？对于前一个字符重复0到1次 

#### **4、注释和打印**

**注释：**
\#单行注释

'''
多行注释
多行注释
''' 

Python的编码注释# -*- coding:utf-8 -*-
如果要在python文件里面写中文，则必须要添加一行声明文件编码的注释，否则python2会默认使用ASCII编码。

**python中print函数用法**
字符串和数值类型可以直接输出

日志logging：

#### 5、time模块

 Python 的 datetime 模块中有一个 time 对象，Python 还有一个单独的 time 模块。此外，time 模块还有一个函数叫作 time()。

Unix 时间使用的是从 1970 年 1 月 1 日 0 点开始的秒数。这个值通常被称为纪元，它是不同系统之间最简单的交换日期时间的方法。

time 模块的 time() 函数会返回当前时间的纪元值：

可以用 ctime() 把一个纪元值转换成一个字符串

localtime() 会返回当前系统时区下的时间；

也可以使用 strftime() 把日期和时间转换成字符串：

| 格式化字符串 | 日期/时间单元   | 范围        |
| ------------ | --------------- | ----------- |
| 格式化字符串 | 日期/时间单元   | 范围        |
| %Y           | 年              | 1900-...    |
| %m           | 月              | 01-12       |
| %B           | 月名            | January,... |
| %b           | 月名缩写        | Jan,...     |
| %d           | 日              | 01-31       |
| %A           | 星期            | Sunday,...  |
| %a           | 星期缩写        | Sun,...     |
| %H           | 时（24 小时制） | 00-23       |
| %I           | 时（12 小时制） | 01-12       |
| %p           | 上午 / 下午     | AM, PM      |
| %M           | 分              | 00-59       |
| %S           | 秒              | 00-59       |

####  **6、json模块**

Python 程序可以把 JSON 文本翻译成 Python 的数据结构

JSON（JavaScript Object Notation）是源于 JavaScript 的当今很流行的数据交换格式，它是 JavaScript 语言的一个子集，也是 Python 合法可支持的语法。对于 Python 的兼容性使得它成为程序间数据交换的较好选择。

# **安装包**

有 3 种安装 Python 包的方法：

--推荐使用 pip，你可以使用 pip 来安装绝大多数 Python 包；

--有时可以使用操作系统自带的包管理工具；

--从源代码安装。
