# Chapter 5：浅谈python 中对文件的操作

举个例子，下面是一个替换文件内字符串函数，实现打开一个文件，将所有sstr替换成rstr

```python
def replace(file, sstr, rstr):
    lines=open(file, 'r').readlines()
    flen=len(lines)
    for i in range(flen):
        if sstr in lines[i]:
            lines[i]=lines[i].replace(sstr,rstr)
    open(file,'w').writelines(lines)
```

读写一个文件之前需要打开它：

```python
fileobj = open(filename, mode)
```

fileobj 是 open() 返回的文件对象；filename 是该文件的字符串名；mode是指明文件类型和操作的字符串。

mode 的第一个字母表明对其的操作：

r 表示读模式。

w 表示写模式。如果文件不存在则新创建，如果存在则重写新内容。

x 表示在文件不存在的情况下新创建并写文件。

a 表示如果文件存在，在文件末尾追加写内容。

mode 的第二个字母是文件类型：

t（或者省略）代表文本类型；

b 代表二进制文件。

打开文件之后就可以调用函数来读写数据。

使用read()、readline()或者readlines()读文本文件：

```python
#relativity.txt
poem = '''There was a young lady named Bright,
Whose speed was far faster than light;
She started one day
In a relative way,
And returned on the previous night.'''
len(poem)
150
```

可以不带参数的 **read()** 函数一次读入文件的所有内容。但在读入文件时要格外注意，1GB 的文件会用到相同大小的内存

```python
fin = open('relativity', 'rt' )
poem = fin.read()
fin.close()
len(poem)
```

也可以设置最大的读入字符数限制 **read()** 函数一次返回的大小。

```python
poem = ''
fin = open('relativity', 'rt' )
chunk = 100
while True:
     fragment = fin.read(chunk)
     if not fragment:
         break
     poem += fragment
fin.close()
len(poem)
```

也能使用 **readline()** 每次读入文件的一行：

```python
poem = ''
fin = open('relativity', 'rt' )
while True:
     line = fin.readline()
     if not line:
         break
     poem += line
 
fin.close()
len(poem)
```

读取文本文件最简单的方式是使用一个**迭代器（iterator）**，它会每次返回一行：

```python
poem = ''
fin = open('relativity', 'rt' )
for line in fin:
     poem += line
 
fin.close()
len(poem)
```

函数 **readlines()** 调用时每次读取一行，并返回单行字符串的列表：

```python
fin = open('relativity', 'rt' )
lines = fin.readlines()
fin.close()
print(len(lines), 'lines read')
 
5 lines read
 
for line in lines:
     print(line, end='')
 
There was a young lady named Bright,
Whose speed was far faster than light;
She started one day
In a relative way,
And returned on the previous night.
```

用**exists()**检查文件是否存在

要判断文件或者目录是否存在，可以使用os.path.exists(‘text.txt’)，传入相对或者绝对路径名。
