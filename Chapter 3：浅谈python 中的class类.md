# Chapter 3：浅谈python 中的class类

“Take an object. Do something to it. Do somthing else to it.”

“选取一个对象，对它进行修改，然后再进行一些其他的修改。”

​                                                                                                     ——Jasper Johns

Python的原始类现在称为经典类。它们有很多缺陷，所以最终被新型类取代。这种转换从Python 2.2开始，一直延续到今天。
经典类使用下面的语法。
      class ClassicClass:
            pass
新型类使用这种语法。
      class NewStyleClass(object):
           pass
新型类比经典类具有更多的优势，而后者存在目的仅仅是为了兼容性，并且在Python 3中已完全废除。伴随着新型类，类型和类最后得以统一。
在Python 3中，前面例子中的两种语法都将会创建新型类。这种行为不会构成严重的移植问题，但需要注意到Python 3中不存在经典类。

 

Python特殊的语法形式巧妙地将实现对象机制的大量细节隐藏了起来。输入 num = 7 就可以创建一个值为 7 的整数对象，并且将这个对象赋值给变量 num。事实上，在 Python 中，只有当你想要创建属于自己的对象或者需要修改已有对象的行为时，才需要关注对象的内部实现细节。

 ```python
class Person():
    def __init__(self):
    pass
 ```

我们定义一下 Person 类。

__init__() 是 Python 中一个特殊的函数名，用于根据类的定义创建实例对象。self 参数指向了这个正在被创建的对象本身

当在类声明里定义 __init__() 方法时，第一个参数必须为 self。尽管 self 并不是一个 Python 保留字，但它很常用。

尽管我们添加了初始化方法，但用这个 Person 类创建的对象仍然什么也做不了。我们在初始化方法中添加 name 参数：

```python
class Person():
    def __ini__(self, name):
        self.name = name
```

用 Person 类创建一个对象，为 name 特性传递一个字符串参数：

上面这短短的一行代码实际做了以下工作：

*查看 Person 类的定义；*

*在内存中实例化（创建）一个新的对象；*

*调用对象的 __init__ 方法，将这个新创建的对象作为 self 传入，并将另一个参数（'Elmer-Fudd'）作为 name 传入；*

*将 name 的值存入对象；*

*返回这个新的对象；*

*将名字 hunter 与这个对象关联。*

在 Person 类定义的内部，你可以直接通过self.name访问 name 特性。而当创建了一个实际的对象后，例如这里的 hunter，需要通过hunter.name来访问它。

在类的定义中，__init__ 并不是必需的。只有当需要区分由该类创建的不同对象时，才需要指定 __init__ 方法。

 

**self的自辩**
Python 中经常被争议的一点（除了使用空格外）就是必须把 self 设置为实例方法的第一个参数。Python 使用 self 参数来找到正确的对象所包含的特性和方法。
