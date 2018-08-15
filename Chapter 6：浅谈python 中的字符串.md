# Chapter 6：浅谈python 中的字符串

与其他语言不同的是，Python 字符串是不可变的。你无法对原字符串进行修改，但可以将字符串的一部分复制到新字符串，来达到相同的修改效果。

对 Unicode 的支持使得 Python 3 可以包含世界上任何书面语言以及许多特殊符号。对于 Unicode 的支持也是 Python 3 从 Python 2 分离出来的重要原因之一。

**使用split()分割**

使用内置的字符串函数 split() 可以基于分隔符将字符串分割成由若干子串组成的列表。所谓列表（list）是由一系列值组成的序列，值与值之间由逗号隔开，整个列表被方括号所包裹。

```python
>>> todos = 'get gloves,get mask,give cat vitamins,call ambulance'
>>> todos.split(',')
['get gloves', 'get mask', 'give cat vitamins', 'call ambulance']
```

如果不指定分隔符，那么 split() 将默认使用空白字符——换行符、空格、制表符。

```python
>>> todos.split()
['get', 'gloves,get', 'mask,give', 'cat', 'vitamins,call', 'ambulance']
```

即使不传入参数，调用 split() 函数时仍需要带着括号，这样 Python 才能知道你想要进行函数调用。

去掉字符串两端的空格：line = line.strip()

rfind() 返回字符串最后一次出现的位置，如果没有匹配项则返回-1。
