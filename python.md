
<!-- vim-markdown-toc GFM -->
* [Python语言特性](#python语言特性)
    * [1 Python的函数参数传递](#1-python的函数参数传递)
    * [2 Python中的元类(metaclass)](#2-python中的元类metaclass)
        * [什么是元类](#什么是元类)
        * [`__metaclass__`属性](#__metaclass__属性)
        * [自定义元类](#自定义元类)
        * [为什么要用metaclass类而不是函数?](#为什么要用metaclass类而不是函数)
    * [3 @staticmethod和@classmethod](#3-staticmethod和classmethod)
    * [4 类变量和实例变量](#4-类变量和实例变量)
        * [1)、类变量、实例变量概念](#1类变量实例变量概念)
        * [2)、访问](#2访问)
        * [3）、总结](#3总结)
    * [5 Python自省](#5-python自省)
    * [6 字典推导式](#6-字典推导式)
    * [7 Python中单下划线和双下划线](#7-python中单下划线和双下划线)
    * [8 字符串格式化:%和.format](#8-字符串格式化和format)
    * [9 迭代器和生成器](#9-迭代器和生成器)
    * [10 `*args` and `**kwargs`](#10-args-and-kwargs)
    * [11 面向切面编程AOP和装饰器](#11-面向切面编程aop和装饰器)
    * [12 鸭子类型](#12-鸭子类型)
    * [13 Python中重载](#13-python中重载)
    * [14 新式类和旧式类](#14-新式类和旧式类)
    * [15 `__new__`和`__init__`的区别](#15-__new__和__init__的区别)
    * [16 单例模式](#16-单例模式)
        * [1 使用`__new__`方法](#1-使用__new__方法)
        * [2 共享属性](#2-共享属性)
        * [3 装饰器版本](#3-装饰器版本)
        * [4 import方法](#4-import方法)
    * [17 Python中的作用域](#17-python中的作用域)
    * [18 GIL线程全局锁](#18-gil线程全局锁)
    * [19 协程](#19-协程)
    * [20 闭包](#20-闭包)
    * [21 lambda函数](#21-lambda函数)
    * [22 Python函数式编程](#22-python函数式编程)
    * [23 Python里的拷贝](#23-python里的拷贝)
    * [24 Python垃圾回收机制](#24-python垃圾回收机制)
        * [1 引用计数](#1-引用计数)
        * [2 标记-清除机制](#2-标记-清除机制)
        * [3 分代技术](#3-分代技术)
    * [25 Python的List](#25-python的list)
    * [26 Python的is](#26-python的is)
    * [27 read,readline和readlines](#27-readreadline和readlines)
    * [28 Python2和3的区别](#28-python2和3的区别)
    * [29 super init](#29-super-init)
    * [30 range and xrange](#30-range-and-xrange)
    * [31 到底什么是Python？你可以在回答中与其他技术进行对比（也鼓励这样做）](#31-到底什么是python你可以在回答中与其他技术进行对比也鼓励这样做)
    * [32 Python和多线程（multi-threading）。这是个好主意码？列举一些让Python代码以并行方式运行的方法](#32-python和多线程multi-threading这是个好主意码列举一些让python代码以并行方式运行的方法)
    * [33 with](#33-with)
    * [34 装饰器](#34-装饰器)
    * [35 `if __name__ == "__main__":`是干嘛的?](#35-if-__name__--__main__是干嘛的)

<!-- vim-markdown-toc -->
# Python语言特性

## 1 Python的函数参数传递

看两个例子:

```python
a = 1
def fun(a):
    a = 2
fun(a)
print a  # 1
```

```python
a = []
def fun(a):
    a.append(1)
fun(a)
print a  # [1]
```

所有的变量都可以理解是内存中一个对象的“引用”，或者，也可以看似c中void*的感觉。

通过`id`来看引用`a`的内存地址可以比较理解：

```python
a = 1
def fun(a):
    print "func_in",id(a)   # func_in 41322472
    a = 2
    print "re-point",id(a), id(2)   # re-point 41322448 41322448
print "func_out",id(a), id(1)  # func_out 41322472 41322472
fun(a)
print a  # 1
```

注：具体的值在不同电脑上运行时可能不同。

可以看到，在执行完`a = 2`之后，`a`引用中保存的值，即内存地址发生变化，由原来`1`对象的所在的地址变成了`2`这个实体对象的内存地址。

而第2个例子`a`引用保存的内存值就不会发生变化：

```python
a = []
def fun(a):
    print "func_in",id(a)  # func_in 53629256
    a.append(1)
print "func_out",id(a)     # func_out 53629256
fun(a)
print a  # [1]
```

这里记住的是类型是属于对象的，而不是变量。而 **对象有两种,“可更改”（mutable）与“不可更改”（immutable）对象。在python中，strings, tuples, 和numbers是不可更改的对象，而list,dict等则是可以修改的对象**。(这就是这个问题的重点)

当一个引用传递给函数的时候,函数自动复制一份引用,这个函数里的引用和外边的引用没有半毛关系了.所以第一个例子里函数把引用指向了一个不可变对象,当函数返回的时候,外面的引用没半毛感觉.而第二个例子就不一样了,函数内的引用指向的是可变对象,对它的操作就和定位了指针地址一样,在内存里进行修改.

如果还不明白的话,这里有更好的解释: http://stackoverflow.com/questions/986006/how-do-i-pass-a-variable-by-reference

## 2 Python中的元类(metaclass)

不常用,但是像ORM这种复杂的结构还是会需要的,[详情请看这](http://stackoverflow.com/questions/100003/what-is-a-metaclass-in-python)

### 什么是元类

**元类就是创建类的东西**.
你是为了创建对象才定义类的,对吧?
但是我们已经知道了Python的类是对象.
这里, **元类创建类.它们是类的类**,你可以把它们想象成这样:  
```python
MyClass = MetaClass()    
MyObject = MyClass()  
```
你已经看到了type可以让你像这样做：  
MyClass = type('MyClass', (), {})  
这是因为 **type就是一个元类.type是Python中创建所有类的元类**.

现在你可能纳闷为啥子type用小写而不写成Type?  
我想是因为要跟str保持一致,str创建字符串对象,int创建整数对象.type正好创建类对象.  
你可以通过检查`__class__`属性来看到这一点.

Python中所有的东西都是对象.包括整数,字符串,函数还有类.所有这些都是对象.所有这些也都是从类中创建的:  
```python
>>> age = 35
>>> age.__class__
<type 'int'>
>>> name = 'bob'
>>> name.__class__
<type 'str'>
>>> def foo(): pass
>>> foo.__class__
<type 'function'>
>>> class Bar(object): pass
>>> b = Bar()
>>> b.__class__
<class '__main__.Bar'>
```  
那么,`__class__`的`__class__`属性是什么?  
```python
>>> age.__class__.__class__
<type 'type'>
>>> name.__class__.__class__
<type 'type'>
>>> foo.__class__.__class__
<type 'type'>
>>> b.__class__.__class__
<type 'type'>
```  
所以,元类就是创建类对象的东西.  
如果你愿意你也可以把它叫做'类工厂'.type是Python的内建元类,当然,你也可以创建你自己的元类.
### `__metaclass__`属性
当你创建一个函数的时候,你可以添加`__metaclass__`属性:  
```python
class Foo(object):
  __metaclass__ = something...
  [...]
```  
如果你这么做了，Python就会用元类来创建类Foo.  
小心点，这里面有些技巧.  
你首先写下`class Foo(object)`，但是类对象Foo还没有在内存中创建.  
**Python将会在类定义中寻找`__metaclass__`，如果找到了就用它来创建类对象Foo，如果没找到，就会默认用type创建类。**  

把下面这段话反复读几次。  
当你写如下代码时 :  
```python
class Foo(Bar):
  pass
```  
Python将会这样运行:  
1. 在`Foo`中有没有`___metaclass__`属性?  
2. 如果有,`Python`会在内存中通过`__metaclass__`创建一个名字为`Foo`的类对象(我说的是类对象,跟紧我的思路).  
3. 如果`Python`没有找到`__metaclass__`，它会继续在`Bar`（父类）中寻找`__metaclass__`属性，并尝试做和前面同样的操作.  
4. 如果`Python`在任何父类中都找不到`__metaclass__`，它就会在模块层次中去寻找`__metaclass__`，并尝试做同样的操作。  
5. 如果还是找不到`__metaclass__`,`Python`就会用内置的`type`来创建这个类对象。

现在的问题就是，你可以在`__metaclass__`中放置些什么代码呢？  
答案就是：可以创建一个类的东西。

那么什么可以用来创建一个类呢？type，或者任何使用到type或者子类化type的东东都可以。
 
###自定义元类
**元类的主要目的就是为了当创建类时能够自动地改变类.**  
通常，你会为API做这样的事情，你希望可以创建符合当前上下文的类.  
假想一个很傻的例子，你决定在你的模块里所有的类的属性都应该是大写形式。有好几种方法可以办到，
但其中一种就是通过在模块级别设定`__metaclass__`.  
采用这种方法，这个模块中的所有类都会通过这个元类来创建，我们只需要告诉元类把所有的属性都改成大写形式就万事大吉了。  
幸运的是，`__metaclass__`实际上可以被任意调用，它并不需要是一个正式的类（我知道，某些名字里带有`class`的东西并不需要是一个class，
画画图理解下，这很有帮助）。  
所以，我们这里就先以一个简单的函数作为例子开始。  
```python
# 元类会自动将你通常传给'type'的参数作为自己的参数传入
def upper_attr(future_class_name, future_class_parents, future_class_attr):
  """
    返回一个将属性列表变为大写字母的类对象
  """
  # 选取所有不以'__'开头的属性,并把它们编程大写
  uppercase_attr = {}
  for name, val in future_class_attr.items():
      if not name.startswith('__'):
          uppercase_attr[name.upper()] = val
      else:
          uppercase_attr[name] = val
  # 用'type'创建类
  return type(future_class_name, future_class_parents, uppercase_attr)
__metaclass__ = upper_attr # 将会影响整个模块
class Foo(): # global __metaclass__ won't work with "object" though
  # 我们也可以只在这里定义__metaclass__，这样就只会作用于这个类中
  bar = 'bip'
print(hasattr(Foo, 'bar'))
# 输出: False
print(hasattr(Foo, 'BAR'))
# 输出: True
f = Foo()
print(f.BAR)
# 输出: 'bip'
```

现在让我们再做一次，这一次用一个真正的`class`来当做元类。  
```python
# 请记住，'type'实际上是一个类，就像'str'和'int'一样
# 所以，你可以从type继承
class UpperAttrMetaclass(type):
    # __new__ 是在__init__之前被调用的特殊方法
    # __new__是用来创建对象并返回它的方法
    # 而__init__只是用来将传入的参数初始化给对象
    # 你很少用到__new__，除非你希望能够控制对象的创建
    # 这里，创建的对象是类，我们希望能够自定义它，所以我们这里改写__new__
    # 如果你希望的话，你也可以在__init__中做些事情
    # 还有一些高级的用法会涉及到改写__call__特殊方法，但是我们这里不用
    def __new__(upperattr_metaclass, future_class_name,
                future_class_parents, future_class_attr):
        uppercase_attr = {}
        for name, val in future_class_attr.items():
            if not name.startswith('__'):
                uppercase_attr[name.upper()] = val
            else:
                uppercase_attr[name] = val
        return type(future_class_name, future_class_parents, uppercase_attr)
```  

但是这不是真正的面向对象(OOP).我们直接调用了`type`，而且我们没有改写父类的`new`方法。现在让我们这样去处理:  
```python
class UpperAttrMetaclass(type):
    def __new__(upperattr_metaclass, future_class_name,
                future_class_parents, future_class_attr):
        uppercase_attr = {}
        for name, val in future_class_attr.items():
            if not name.startswith('__'):
                uppercase_attr[name.upper()] = val
            else:
                uppercase_attr[name] = val
        # 重用 type.__new__ 方法
        # 这就是基本的OOP编程，没什么魔法
        return type.__new__(upperattr_metaclass, future_class_name,
                            future_class_parents, uppercase_attr)
```                          
你可能已经注意到了有个额外的参数`upperattr_metaclass`，这并没有什么特别的。 **类方法的第一个参数总是表示当前的实例，
就像在普通的类方法中的self参数一样。**

当然了，为了清晰起见，这里的名字我起的比较长。但是就像self一样，所有的参数都有它们的传统名称。
因此，在真实的产品代码中一个元类应该是像这样的：  
```python
class UpperAttrMetaclass(type):
    def __new__(cls, clsname, bases, dct):
        uppercase_attr = {}
        for name, val in dct.items():
            if not name.startswith('__'):
                uppercase_attr[name.upper()] = val
            else:
                uppercase_attr[name] = val
        return type.__new__(cls, clsname, bases, uppercase_attr)
```      

如果使用`super`方法的话，我们还可以使它变得更清晰一些，这会缓解继承（是的，你可以拥有元类，从元类继承，从`type`继承）
```python
class UpperAttrMetaclass(type):
    def __new__(cls, clsname, bases, dct):
        uppercase_attr = {}
        for name, val in dct.items():
            if not name.startswith('__'):
                uppercase_attr[name.upper()] = val
            else:
                uppercase_attr[name] = val
        return super(UpperAttrMetaclass, cls).__new__(cls, clsname, bases, uppercase_attr)
```  
就是这样，除此之外，关于元类真的没有别的可说的了。

使用到元类的代码比较复杂，这背后的原因倒并不是因为元类本身，而是因为你通常会使用元类去做一些晦涩的事情，依赖于自省，控制继承等等。

确实，用元类来搞些“黑暗魔法”是特别有用的，因而会搞出些复杂的东西来。但就元类本身而言，它们其实是很简单的：  
**拦截类的创建  
修改一个类  
返回修改之后的类**

###为什么要用metaclass类而不是函数?

由于`__metaclass__`可以接受任何可调用的对象，那为何还要使用类呢，因为很显然使用类会更加复杂啊？  
这里有好几个原因：  
意图会更加清晰。当你读到UpperAttrMetaclass(type)时，你知道接下来要发生什么。  
你可以使用OOP编程。元类可以从元类中继承而来，改写父类的方法。元类甚至还可以使用元类。  
你可以把代码组织的更好。当你使用元类的时候肯定不会是像我上面举的这种简单场景，通常都是针对比较复杂的问题。
将多个方法归总到一个类中会很有帮助，也会使得代码更容易阅读。  
你可以使用`__new__`,`__init__`以及`__call__`这样的特殊方法。它们能帮你处理不同的任务。就算通常你可以把所有的东西都
在`__new__`里处理掉，有些人还是觉得用`__init__`更舒服些。  
哇哦，这东西的名字是`metaclass`，肯定非善类，我要小心！
说了这么多TMD究竟为什么要使用元类？

现在回到我们的大主题上来，究竟是为什么你会去使用这样一种容易出错且晦涩的特性？  
好吧，一般来说，你根本就用不上它：  
**“元类就是深度的魔法，99%的用户应该根本不必为此操心。如果你想搞清楚究竟是否需要用到元类，那么你就不需要它。
那些实际用到元类的人都非常清楚地知道他们需要做什么，而且根本不需要解释为什么要用元类。” —— Python界的领袖 Tim Peters**

**元类的主要用途是创建API**。一个典型的例子是Django ORM。
它允许你像这样定义：  
```python
class Person(models.Model):
  name = models.CharField(max_length=30)
  age = models.IntegerField()
```  
但是如果你像这样做的话：  
```python
guy = Person(name='bob', age='35')
print(guy.age)
```  
这并不会返回一个`IntegerField`对象，而是会返回一个`int`，甚至可以直接从数据库中取出数据。  
这是有可能的，因为`models.Model`定义了`__metaclass__`， 并且使用了一些魔法能够将你刚刚定义的简单的Person类转变成
对数据库的一个复杂`hook`。  
`Django`框架将这些看起来很复杂的东西通过暴露出一个简单的使用元类的API将其化简，通过这个API重新创建代码，在背后完成真正的工作。

结语  
首先，你知道了类其实是能够创建出类实例的对象。
好吧，事实上，类本身也是实例，当然，它们是元类的实例。  
```python
>>> class Foo(object): pass
>>> id(Foo)
142630324
```  

**Python中的一切都是对象，它们要么是类的实例，要么是元类的实例.**  
除了`type.type`实际上是它自己的元类，在纯`Python`环境中这可不是你能够做到的，这是通过在实现层面耍一些小手段做到的。  
其次，元类是很复杂的。对于非常简单的类，你可能不希望通过使用元类来对类做修改。你可以通过其他两种技术来修改类： 

* [monkey patching](https://en.wikipedia.org/wiki/Monkey_patch)
* 装饰器  

当你需要动态修改类时，99%的时间里你最好使用上面这两种技术。当然了，其实在99%的时间里你根本就不需要动态修改类 :D

## 3 @staticmethod和@classmethod

Python其实有3个方法,即静态方法(staticmethod),类方法(classmethod)和实例方法，  
**Staticmethods** are used to group functions which have some logical connection with a class to the class.  
经常有一些`跟类有关系的功能但在运行时又不需要实例和类参与的情况下`需要用到静态方法. 比如更改环境变量或者修改其他类的属性等能用到
静态方法. 这种情况可以直接用函数解决, 但这样同样会扩散类内部的代码，造成维护困难.

如下:

```python
def foo(x):
    print "executing foo(%s)"%(x)

class A(object):
    def foo(self,x):
        print "executing foo(%s,%s)"%(self,x)

    @classmethod
    def class_foo(cls,x):
        print "executing class_foo(%s,%s)"%(cls,x)

    @staticmethod
    def static_foo(x):
        print "executing static_foo(%s)"%x

a=A()

```

这里先理解下函数参数里面的self和cls.这个self和cls是对类或者实例的绑定,对于一般的函数来说我们可以这么调用`foo(x)`,这个函数就是最常用的,
它的工作跟任何东西(类,实例)无关.对于实例方法,我们知道在类里每次定义方法的时候都需要绑定这个实例,就是`foo(self, x)`,
为什么要这么做呢?因为实例方法的调用离不开实例,我们需要把实例自己传给函数,调用的时候是这样的`a.foo(x)`(其实是`foo(a, x)`).
类方法一样,只不过它传递的是类而不是实例,`A.class_foo(x)`.注意这里的self和cls可以替换别的参数,但是python的约定是这俩,还是不要改的好.

对于静态方法其实和普通的方法一样,不需要对谁进行绑定,唯一的区别是调用的时候需要使用`a.static_foo(x)`或者`A.static_foo(x)`来调用.

In fact, if you define something to be a **classmethod**, it is probably because you intend to call it from the class 
rather than from a class instance. Both a.class_foo(1) and A.class_foo(1) will be ok.

更多关于这个问题:http://stackoverflow.com/questions/136097/what-is-the-difference-between-staticmethod-and-classmethod-in-python

## 4 类变量和实例变量

###1)、类变量、实例变量概念
类变量：
类变量就是定义在类中，但是在函数体之外的变量。通常不使用self.变量名赋值的变量。类变量通常不作为类的实例变量的，类变量对于所有实例化的对象中是公用的。
实例变量：
实例变量是定义在方法中的变量，使用self绑定到实例上的变量，只是对当前实例起作用。
###2)、访问
类变量
在类的内部和外部类变量都可以直接使用className.类变量的形式访问。但是在类的内部，也可以使用self.类变量来访问，但这时含义就不同了(后面使用代码验证)。
实例变量
在类的内部，实例变量self.实例变量的形式访问；在类的外部使用对象名.实例变量的形式访问。实例变量是绑定到一个实例上的变量，它只是属于这个绑定的实例。而类变量是所有的来自用一个类的实例所共享。我们看到这里会有这样的疑问，
如果说类变量对所有来自这个类的所有实例所共享，那么假如我一个实例去改变了这个类变量(假设使用这样的操作object.类变量 = value)的值，那么对于其他的实例是不是都是可见的？
答案是否定的，下面验证。

```   
class A(object):
    # 定义一个类变量，初值是10
    class_var = 10
    print id(class_var)
    
    def foo(self):
        print '在类中访问类变量：A.class_var=', A.class_var
        print '在类中访问实例变量： self.class_var=', self, self.class_var

        # 改变实例变量的值
        self.class_var = 40
        print '修改后访问类变量：A.class_var=', A.class_var
        print '修改后访问实例变量 self.class_var=',self, self.class_var

        # 这里的class_var和函数外面的class_var不是同一个东西，这是一个局部变量
        class_var = 20
        print id(class_var)
        print 'class_var=', class_var

        
        A.class_var = 15
        print 'A.class_var=', A.class_var
        print 'class_var=',class_var
        print 'self.class_var=',self.class_var
        

obj1 = A()
obj2 = A()
obj3 = A()
obj1.foo()
print A.class_var
print obj1.class_var
print obj2.class_var
print obj3.class_var


Output:
49964144
在类中访问类变量：A.class_var= 10
在类中访问实例变量： self.class_var= <__main__.A object at 0x0000000002FD2390> 10
修改后访问类变量：A.class_var= 10
修改后访问实例变量 self.class_var= <__main__.A object at 0x0000000002FD2390> 40
49963904
class_var= 20
A.class_var= 15
class_var= 20
self.class_var= 40
15
40
15
15
```

从上面运行的结果分析：当使用self.class_var形式访问类变量的之后，如果修改self.class_var的值，可以发现，类变量的值没有变化；我们修改类变量的值，发现self.class_var的值也没有受到影响。
从最后打印obj2和obj3这两个都来自于一个类的实例中的类变量都是和修改后的类变量一样，表示他们是共享类变量的。

###3）、总结
1、类变量可以使用className.类变量和self.类变量两种方式访问。
2、如果使用self.类变量的方式访问并重新赋值后，这个变量就会成为实例变量和self绑定，实际上就变成了一个实例变量，实例变量会屏蔽掉类变量的值。
3、类变量是共享的，最好使用类名的方式来访问类变量。
4、类变量通过sel访问时，就会被转化成实例变量，被绑定到特定的实例上。
5、实例变量(self)的形式对类变量重新赋值后，类变量的值不会随之变化。

参考:

## 5 Python自省

这个也是python彪悍的特性.

自省就是面向对象的语言所写的程序在运行时,所能知道对象的类型.简单一句就是 **运行时能够获得对象的类型**.比如type(),dir(),getattr(),hasattr(),isinstance().

## 6 字典推导式

可能你见过列表推导式,却没有见过字典推导式,在2.7中才加入的:

```python
d = {key: value for (key, value) in iterable}
```

## 7 Python中单下划线和双下划线

```python
>>> class MyClass():
...     def __init__(self):
...             self.__superprivate = "Hello"
...             self._semiprivate = ", world!"
...
>>> mc = MyClass()
>>> print mc.__superprivate
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: myClass instance has no attribute '__superprivate'
>>> print mc._semiprivate
, world!
>>> print mc.__dict__
{'_MyClass__superprivate': 'Hello', '_semiprivate': ', world!'}
```

`__foo__`:一种约定,Python内部的名字,用来区别其他用户自定义的命名,以防冲突.

`_foo`:一种约定,用来指定变量私有.程序员用来指定私有变量的一种方式.

`__foo`:这个有真正的意义:解析器用`_classname__foo`来代替这个名字,以区别和其他类相同的命名.

详情见:http://stackoverflow.com/questions/1301346/the-meaning-of-a-single-and-a-double-underscore-before-an-object-name-in-python

或者: http://www.zhihu.com/question/19754941

## 8 字符串格式化:%和.format

.format在许多方面看起来更便利.对于`%`最烦人的是它无法同时传递一个变量和元组.你可能会想下面的代码不会有什么问题:

```
"hi there %s" % name
```

但是,如果name恰好是(1,2,3),它将会抛出一个TypeError异常.为了保证它总是正确的,你必须这样做:

```
"hi there %s" % (name,)   # 提供一个单元素的数组而不是一个参数
```

但是有点丑..format就没有这些问题.你给的第二个问题也是这样,.format好看多了.

你为什么不用它?

* 不知道它(在读这个之前)
* 为了和Python2.5兼容(譬如logging库建议使用`%`([issue #4](https://github.com/taizilongxu/interview_python/issues/4)))

http://stackoverflow.com/questions/5082452/python-string-formatting-vs-format

## 9 迭代器和生成器

[生成器](https://www.liaoxuefeng.com/wiki/001374738125095c955c1e6d8bb493182103fac9270762a000/00138681965108490cb4c13182e472f8d87830f13be6e88000)

[聊聊 Python 中生成器和协程那点事儿](http://manjusaka.itscoder.com/2016/09/11/something-about-yield-in-python/)

这个是stackoverflow里python排名第一的问题,值得一看: http://stackoverflow.com/questions/231767/what-does-the-yield-keyword-do-in-python

这是中文版: http://taizilongxu.gitbooks.io/stackoverflow-about-python/content/1/README.html

生成器的两种生成方式
要创建一个generator，有很多种方法。第一种方法很简单，只要把一个列表生成式的[]改成()，就创建了一个generator：

```python
>>> L = [x * x for x in range(10)]
>>> L
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
>>> g = (x * x for x in range(10))
>>> g
<generator object <genexpr> at 0x104feab40>
```  

```python
def fib(max):
    n, a, b = 0, 0, 1
    while n < max:
        yield b
        a, b = b, a + b
        n = n + 1
```     
这就是定义generator的另一种方法。如果一个函数定义中包含 **yield**关键字，那么这个函数就不再是一个普通函数，而是一个generator：

```python
>>> fib(6)
<generator object fib at 0x104feaaa0>
```

## 10 `*args` and `**kwargs`

用`*args`和`**kwargs`只是为了方便并没有强制使用它们.

如果我们不确定要往函数中传入多少个参数，或者我们想往函数中以列表和元组的形式传参数时，那就使要用`*args`；

如果我们不知道要往函数中传入多少个关键词参数，或者想传入字典的值作为关键词参数时，那就要使用`**kwargs`；

当你不确定你的函数里将要传递多少参数时你可以用`*args`.例如,它可以传递任意数量的参数:

```python
>>> def print_everything(*args):
        for count, thing in enumerate(args):
...         print '{0}. {1}'.format(count, thing)
...
>>> print_everything('apple', 'banana', 'cabbage')
0. apple
1. banana
2. cabbage
```

相似的,`**kwargs`允许你使用没有事先定义的参数名:

```python
>>> def table_things(**kwargs):
...     for name, value in kwargs.items():
...         print '{0} = {1}'.format(name, value)
...
>>> table_things(apple = 'fruit', cabbage = 'vegetable')
cabbage = vegetable
apple = fruit
```

你也可以混着用.命名参数首先获得参数值然后所有的其他参数都传递给`*args`和`**kwargs`.命名参数在列表的最前端.例如:

```
def table_things(titlestring, **kwargs)
```

`*args`和`**kwargs`可以同时在函数的定义中,但是`*args`必须在`**kwargs`前面.

当调用函数时你也可以用`*`和`**`语法.例如:

```python
>>> def print_three_things(a, b, c):
...     print 'a = {0}, b = {1}, c = {2}'.format(a,b,c)
...
>>> mylist = ['aardvark', 'baboon', 'cat']
>>> print_three_things(*mylist)

a = aardvark, b = baboon, c = cat
```

就像你看到的一样,它可以传递列表(或者元组)的每一项并把它们解包.注意必须与它们在函数里的参数相吻合.当然,你也可以在函数定义或者函数调用时用*.

http://stackoverflow.com/questions/3394835/args-and-kwargs

## 11 面向切面编程AOP和装饰器

详见34  
这个AOP一听起来有点懵,同学面阿里的时候就被问懵了...

装饰器是一个很著名的设计模式，经常被用于有切面需求的场景，较为经典的有插入日志、性能测试、事务处理等。装饰器是解决这类问题的绝佳设计，有了装饰器，我们就可以抽离出大量函数中与函数功能本身无关的雷同代码并继续重用。概括的讲，**装饰器的作用就是为已经存在的对象添加额外的功能。**

这个问题比较大,推荐: http://stackoverflow.com/questions/739654/how-can-i-make-a-chain-of-function-decorators-in-python

中文: http://taizilongxu.gitbooks.io/stackoverflow-about-python/content/3/README.html

## 12 鸭子类型

“当看到一只鸟走起来像鸭子、游泳起来像鸭子、叫起来也像鸭子，那么这只鸟就可以被称为鸭子。”

我们并不关心对象是什么类型，到底是不是鸭子，只关心行为。

比如在python中，有很多file-like的东西，比如StringIO,GzipFile,socket。它们有很多相同的方法，我们把它们当作文件使用。

又比如list.extend()方法中,我们并不关心它的参数是不是list,只要它是可迭代的,所以它的参数可以是list/tuple/dict/字符串/生成器等.

鸭子类型在动态语言中经常使用，非常灵活，使得python不想java那样专门去弄一大堆的设计模式。

## 13 Python中重载

引自知乎:http://www.zhihu.com/question/20053359

函数重载主要是为了解决两个问题。

1. 可变参数类型。
2. 可变参数个数。

另外，一个基本的设计原则是，仅仅当两个函数除了参数类型和参数个数不同以外，其功能是完全相同的，此时才使用函数重载，如果两个函数的功能其实不同，那么不应当使用重载，而应当使用一个名字不同的函数。

好吧，那么对于情况 1 ，函数功能相同，但是参数类型不同，python 如何处理？答案是根本不需要处理，因为 python 可以接受任何类型的参数，如果函数的功能相同，那么不同的参数类型在 python 中很可能是相同的代码，没有必要做成两个不同函数。

那么对于情况 2 ，函数功能相同，但参数个数不同，python 如何处理？大家知道，答案就是缺省参数。对那些缺少的参数设定为缺省参数即可解决问题。因为你假设函数功能相同，那么那些缺少的参数终归是需要用的。

好了，鉴于情况 1 跟 情况 2 都有了解决方案，python 自然就不需要函数重载了。

## 14 新式类和旧式类

这个面试官问了,我说了老半天,不知道他问的真正意图是什么.

[stackoverflow](http://stackoverflow.com/questions/54867/what-is-the-difference-between-old-style-and-new-style-classes-in-python)

这篇文章很好的介绍了新式类的特性: http://www.cnblogs.com/btchenguang/archive/2012/09/17/2689146.html

新式类很早在2.2就出现了,所以旧式类完全是兼容的问题,Python3里的类全部都是新式类.这里有一个MRO问题可以了解下(新式类是广度优先,旧式类是深度优先),<Python核心编程>里讲的也很多.

## 15 `__new__`和`__init__`的区别

这个`__new__`确实很少见到,先做了解吧.

1. `__new__`是一个静态方法,而`__init__`是一个实例方法.
2. `__new__`方法会返回一个创建的实例,而`__init__`什么都不返回.
3. 只有在`__new__`返回一个cls的实例时后面的`__init__`才能被调用.
3. 当创建一个新实例时调用`__new__`,初始化一个实例时用`__init__`.

[stackoverflow](http://stackoverflow.com/questions/674304/pythons-use-of-new-and-init)

ps: `__metaclass__`是创建类时起作用.所以我们可以分别使用`__metaclass__`,`__new__`和`__init__`来分别在类创建,实例创建和实例初始化的时候做一些小手脚.

## 16 单例模式

这个绝对常考啊.绝对要记住1~2个方法,当时面试官是让手写的.

### 1 使用`__new__`方法

```python
class Singleton(object):
    def __new__(cls, *args, **kw):
        if not hasattr(cls, '_instance'):
            orig = super(Singleton, cls)
            cls._instance = orig.__new__(cls, *args, **kw)
        return cls._instance

class MyClass(Singleton):
    a = 1
```

### 2 共享属性

创建实例时把所有实例的`__dict__`指向同一个字典,这样它们具有相同的属性和方法.

```python

class Borg(object):
    _state = {}
    def __new__(cls, *args, **kw):
        ob = super(Borg, cls).__new__(cls, *args, **kw)
        ob.__dict__ = cls._state
        return ob

class MyClass2(Borg):
    a = 1
```

### 3 装饰器版本



```python
def singleton(cls, *args, **kw):
    instances = {}
    def getinstance():
        if cls not in instances:
            instances[cls] = cls(*args, **kw)
        return instances[cls]
    return getinstance

@singleton
class MyClass:
  ...
```

### 4 import方法

作为python的模块是天然的单例模式

```python
# mysingleton.py
class My_Singleton(object):
    def foo(self):
        pass

my_singleton = My_Singleton()

# to use
from mysingleton import my_singleton

my_singleton.foo()

```

## 17 Python中的作用域

Python 中，一个变量的作用域总是由在代码中被赋值的地方所决定的。

当 Python 遇到一个变量的话他会按照这样的顺序进行搜索：

本地作用域（Local）→当前作用域被嵌入的本地作用域（Enclosing locals）→全局/模块作用域（Global）→内置作用域（Built-in）

## 18 GIL线程全局锁

线程全局锁(Global Interpreter Lock),即Python为了保证线程安全而采取的独立线程运行的限制,说白了就是一个核只能在同一时间运行一个线程.

见[Python 最难的问题](http://www.oschina.net/translate/pythons-hardest-problem)

解决办法就是多进程和下面的协程(协程也只是单CPU,但是能减小切换代价提升性能).

## 19 协程

知乎被问到了,呵呵哒,跪了

简单点说协程是进程和线程的升级版,进程和线程都面临着内核态和用户态的切换问题而耗费许多切换时间,而协程就是用户自己控制切换的时机,不再需要陷入系统的内核态.

Python里最常见的yield就是协程的思想!可以查看第九个问题.


## 20 闭包

闭包(closure)是函数式编程的重要的语法结构。闭包也是一种组织代码的结构，它同样提高了代码的可重复使用性。

当一个内嵌函数引用其外部作作用域的变量,我们就会得到一个闭包. 总结一下,创建一个闭包必须满足以下几点:

1. 必须有一个内嵌函数
2. 内嵌函数必须引用外部函数中的变量
3. 外部函数的返回值必须是内嵌函数

感觉闭包还是有难度的,几句话是说不明白的,还是查查相关资料.

重点是函数运行后并不会被撤销,就像16题的instance字典一样,当函数运行完后,instance并不被销毁,而是继续留在内存空间里.这个功能类似类里的类变量,只不过迁移到了函数上.

闭包就像个空心球一样,你知道外面和里面,但你不知道中间是什么样.

## 21 lambda函数

其实就是一个匿名函数,为什么叫lambda?因为和后面的函数式编程有关.

推荐: [知乎](http://www.zhihu.com/question/20125256)


## 22 Python函数式编程

这个需要适当的了解一下吧,毕竟函数式编程在Python中也做了引用.

推荐: [酷壳](http://coolshell.cn/articles/10822.html)

python中函数式编程支持:

filter 函数的功能相当于过滤器。调用一个布尔函数`bool_func`来迭代遍历每个seq中的元素；返回一个使`bool_seq`返回值为true的元素的序列。

```python
>>>a = [1,2,3,4,5,6,7]
>>>b = filter(lambda x: x > 5, a)
>>>print b
>>>[6,7]
```

map函数是对一个序列的每个项依次执行函数，下面是对一个序列每个项都乘以2：

```python
>>> a = map(lambda x:x*2,[1,2,3])
>>> list(a)
[2, 4, 6]
```

reduce函数是对一个序列的每个项迭代调用函数，。reduce把一个函数作用在一个序列[x1, x2, x3...]上，这个函数必须接收 **两个参数**，reduce把结果继续和序列的下一个元素做 **累积**计算。下面是求3的阶乘：

```python
>>> reduce(lambda x,y:x*y,range(1,4))
6
```

## 23 Python里的拷贝

引用和copy(),deepcopy()的区别  
[参考](http://www.runoob.com/w3cnote/python-understanding-dict-copy-shallow-or-deep.html)

```python
import copy
a = [1, 2, 3, 4, ['a', 'b']]  #原始对象

b = a  #赋值，传对象的引用
c = copy.copy(a)  #对象拷贝，浅拷贝
d = copy.deepcopy(a)  #对象拷贝，深拷贝

a.append(5)  #修改对象a
a[4].append('c')  #修改对象a中的['a', 'b']数组对象

print 'a = ', a
print 'b = ', b
print 'c = ', c
print 'd = ', d

输出结果：
a =  [1, 2, 3, 4, ['a', 'b', 'c'], 5]
b =  [1, 2, 3, 4, ['a', 'b', 'c'], 5]
c =  [1, 2, 3, 4, ['a', 'b', 'c']]
d =  [1, 2, 3, 4, ['a', 'b']]
```

## 24 Python垃圾回收机制

[详细资料](http://www.jianshu.com/p/1e375fb40506)

Python GC主要使用引用计数（reference counting）来跟踪和回收垃圾。在引用计数的基础上，通过“标记-清除”（mark and sweep）解决容器对象可能产生的循环引用问题，通过“分代回收”（generation collection）以空间换时间的方法提高垃圾回收效率。

### 1 引用计数

PyObject是每个对象必有的内容，其中`ob_refcnt`就是做为引用计数。当一个对象有新的引用时，它的`ob_refcnt`就会增加，当引用它的对象被删除，它的`ob_refcnt`就会减少.引用计数为0时，该对象生命就结束了。

优点:

1. 简单
2. 实时性

缺点:

1. 维护引用计数消耗资源
2. 循环引用

### 2 标记-清除机制

基本思路是先按需分配，等到没有空闲内存的时候从寄存器和程序栈上的引用出发，遍历以对象为节点、以引用为边构成的图，把所有可以访问到的对象打上标记，然后清扫一遍内存空间，把所有没标记的对象释放。

### 3 分代技术

分代回收的整体思想是：将系统中的所有内存块根据其存活时间划分为不同的集合，每个集合就成为一个“代”，垃圾收集频率随着“代”的存活时间的增大而减小，存活时间通常利用经过几次垃圾回收来度量。

Python默认定义了三代对象集合，索引数越大，对象存活时间越长。

举例：
当某些内存块M经过了3次垃圾收集的清洗之后还存活时，我们就将内存块M划到一个集合A中去，而新分配的内存都划分到集合B中去。当垃圾收集开始工作时，大多数情况都只对集合B进行垃圾回收，而对集合A进行垃圾回收要隔相当长一段时间后才进行，这就使得垃圾收集机制需要处理的内存少了，效率自然就提高了。在这个过程中，集合B中的某些内存块由于存活时间长而会被转移到集合A中，当然，集合A中实际上也存在一些垃圾，这些垃圾的回收会因为这种分代的机制而被延迟。

## 25 Python的List

推荐: http://www.jianshu.com/p/J4U6rR

## 26 Python的is

is是对比地址,==是对比值

## 27 read,readline和readlines

* read        读取整个文件
* readline    读取下一行,使用生成器方法
* readlines   读取整个文件到一个迭代器以供我们遍历

## 28 Python2和3的区别
推荐：[Python 2.7.x 与 Python 3.x 的主要差异](http://chenqx.github.io/2014/11/10/Key-differences-between-Python-2-7-x-and-Python-3-x/)

## 29 super init
super() lets you avoid referring to the base class explicitly, which can be nice. But the main advantage comes with multiple inheritance, where all sorts of fun stuff can happen. See the standard docs on super if you haven't already.

Note that the syntax changed in Python 3.0: you can just say super().`__init__`() instead of super(ChildB, self).`__init__`() which IMO is quite a bit nicer.

http://stackoverflow.com/questions/576169/understanding-python-super-with-init-methods

## 30 range and xrange
都在循环时使用，xrange内存性能更好。  
这两个输出的结果都是一样的，实际上有很多不同，range会直接生成一个list对象：

```
a = range(0,100) 
print type(a) 
print a 
print a[0], a[1] 
```

输出结果：

```
<type 'list'>
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48, 49, 50, 51, 52, 53, 54, 55, 56, 57, 58, 59, 60, 61, 62, 63, 64, 65, 66, 67, 68, 69, 70, 71, 72, 73, 74, 75, 76, 77, 78, 79, 80, 81, 82, 83, 84, 85, 86, 87, 88, 89, 90, 91, 92, 93, 94, 95, 96, 97, 98, 99]
0 1
```

而xrange则不会直接生成一个list，而是每次调用返回其中的一个值：

```
a = xrange(0,100) 
print type(a) 
print a 
print a[0], a[1] 
```

输出结果：

```
<type 'xrange'>
xrange(100)
0 1
```
    
所以xrange做循环的性能比range好，尤其是返回很大的时候，尽量用xrange吧，除非你是要返回一个列表。

What is the difference between range and xrange functions in Python 2.X?
 range creates a list, so if you do range(1, 10000000) it creates a list in memory with 9999999 elements.
 xrange is a sequence object that evaluates lazily.

http://stackoverflow.com/questions/94935/what-is-the-difference-between-range-and-xrange-functions-in-python-2-x

## 31 到底什么是Python？你可以在回答中与其他技术进行对比（也鼓励这样做）
下面是一些关键点：

1. Python是一种 **解释型语言**。这就是说，与C语言和C的衍生语言不同，Python代码在运行之前不需要编译。其他解释型语言还包括PHP和Ruby。
2. Python是 **动态类型语言**，指的是你在声明变量时，不需要说明变量的类型。你可以直接编写类似`x=111`和`x="I'm a string"`这样的代码，程序不会报错。
3. Python非常适合面向对象的编程（OOP），因为它支持通过组合（composition）与继承（inheritance）的方式定义类（class）。Python中没有访问说明符（access specifier，类似C++中的`public`和`private`），这么设计的依据是“大家都是成年人了”。
4. 在Python语言中，函数是第一类对象（first-class objects）。这指的是它们可以被指定给变量，函数既能返回函数类型，也可以接受函数作为输入。类（class）也是第一类对象。
5. Python代码编写快，但是运行速度比编译语言通常要慢。好在Python允许加入基于C语言编写的扩展，因此我们能够优化代码，消除瓶颈，这点通常是可以实现的。`numpy`就是一个很好地例子，它的运行速度真的非常快，因为很多算术运算其实并不是通过Python实现的。
6. Python用途非常广泛——网络应用，自动化，科学建模，大数据应用，等等。它也常被用作“胶水语言”，帮助其他语言和组件改善运行状况。
7. Python让困难的事情变得容易，因此程序员可以专注于算法和数据结构的设计，而不用处理底层的细节。

## 32 Python和多线程（multi-threading）。这是个好主意码？列举一些让Python代码以并行方式运行的方法
**Python并不支持真正意义上的多线程**。Python中提供了多线程包，但是如果你想通过多线程提高代码的速度，使用多线程包并不是个好主意。
Python中有一个被称为`Global Interpreter Lock`（GIL）的东西，它会确保任何时候你的多个线程中，只有一个被执行。
线程的执行速度非常之快，会让你误以为线程是并行执行的，但是实际上都是轮流执行。经过GIL这一道关卡处理，会增加执行的开销。
这意味着，如果你想提高代码的运行速度，使用threading包并不是一个很好的方法。

不过还是有很多理由促使我们使用threading包的。如果你想同时执行一些任务，而且不考虑效率问题，那么使用这个包是完全没问题的，
而且也很方便。但是大部分情况下，并不是这么一回事，你会希望把多线程的部分外包给操作系统完成（通过开启多个进程），
或者是某些调用你的Python代码的外部程序（例如Spark或Hadoop），又或者是你的Python代码调用的其他代码
（例如，你可以在Python中调用C函数，用于处理开销较大的多线程工作）。

为什么提这个问题  
因为GIL就是个混账东西（A-hole）。很多人花费大量的时间，试图寻找自己多线程代码中的瓶颈，直到他们明白GIL的存在。

## 33 with

with 语句适用于对资源进行访问的场合，确保不管使用过程中是否发生异常都会执行必要的“清理”操作，释放资源，比如文件使用后自动关闭、线程中锁的自动获取和释放等。

[理解python的with语句](http://linbo.github.io/2013/01/08/python-with)
## 34 装饰器
装饰器是一个返回函数的高阶函数，用于在代码运行期间动态增加函数功能。

```
from functools import wraps
def memc(func):
    cache = {}
    miss = object()
    @wraps(func)
    def wrapper(*args):
        result = cache.get(args, miss)
        if result is miss:
            result = func(*args)
            cache[args] = result
        return result
    return wrapper
@memc
def fib(n):
    if n < 2:
        return n
    return fib(n-1) + fib(n-2)
print fib(4)
```


## 35 `if __name__ == "__main__":`是干嘛的?

```
# Threading example
import time, thread
def myfunction(string, sleeptime, lock, *args):
    while 1:
        lock.acquire()
        time.sleep(sleeptime)
        lock.release()
        time.sleep(sleeptime)
if __name__ == "__main__":
    lock = thread.allocate_lock()
    thread.start_new_thread(myfunction, ("Thread #: 1", 2, lock))
    thread.start_new_thread(myfunction, ("Thread #: 2", 2, lock))
还有*args在这里是什么意思?
```

当Python解析器读取一个源文件时,它会执行所有的代码.在执行代码前,会定义一些特殊的变量.例如,如果解析器运行的模块(源文件)作为主程序,它将会把`__name__`变量设置成`"__main__"`.如果只是引入其他的模块,`__name__`变量将会设置成模块的名字.  
假设下面是你的脚本,让我们作为主程序来执行:   
```
python threading_example.py
```    
当设置完特殊变量,它就会执行import语句并且加载这些模块.当遇到def代码段的时候,它就会创建一个函数对象并创建一个名叫myfunction变量指向函数对象.接下来会读取if语句并检查__name__是不是等于"__main__",如果是的话他就会执行这个代码段.

**这么做的原因是有时你需要你写的模块既可以直接的执行,还可以被当做模块导入到其他模块中去.通过检查是不是主函数,可以让你的代码只在它作为主程序运行时执行,而当其他人调用你的模块中的函数的时候不必执行.**  
如果想了解更多,请查看[这个](http://ibiblio.org/g2swap/byteofpython/read/module-name.html)

