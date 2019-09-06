
<!-- vim-markdown-toc GFM -->
* [Python面试题汇总](#python面试题汇总)
    * [【题目:001】| 说说你对zen of python的理解，你有什么办法看到它?](#题目001-说说你对zen-of-python的理解你有什么办法看到它)
    * [【题目:002】| 说说你对pythonic的看法，尝试解决下面的小问题](#题目002-说说你对pythonic的看法尝试解决下面的小问题)
    * [【题目:003】| 你调试python代码的方法有哪些?](#题目003-你调试python代码的方法有哪些)
    * [【题目:004】| 你在github上都fork过哪些python库，列举一下你经常使用的，每个库用一句话描述下其功能](#题目004-你在github上都fork过哪些python库列举一下你经常使用的每个库用一句话描述下其功能)
    * [【题目:005】|  什么是GIL?](#题目005--什么是gil)
    * [【题目:006】|  什么是元类(meta_class)?](#题目006--什么是元类meta_class)
    * [【题目:007】|  对比一下dict中items与iteritems?](#题目007--对比一下dict中items与iteritems)
    * [【题目:008】|  是否遇到过python的模块间循环引用的问题，如何避免它?](#题目008--是否遇到过python的模块间循环引用的问题如何避免它)
    * [【题目:009】|  有用过with statement吗？它的好处是什么？](#题目009--有用过with-statement吗它的好处是什么)
    * [【题目:010】|用Python生成指定长度的斐波那契数列](#题目010用python生成指定长度的斐波那契数列)
    * [【题目:011】|  Python里如何生产随机数](#题目011--python里如何生产随机数)
    * [【题目:012】|  Python里如何反序的迭代一个序列](#题目012--python里如何反序的迭代一个序列)
    * [【题目:013】|  Python中如何定义一个函数](#题目013--python中如何定义一个函数)
    * [【题目:015】|  Python里面search()和match()的区别](#题目015--python里面search和match的区别)
    * [【题目:016】|  Python程序中文输出问题怎么解决](#题目016--python程序中文输出问题怎么解决)
    * [【题目:017】|  什么是lambda函数](#题目017--什么是lambda函数)
    * [【题目:018】|  Python里面如何实现tuple和list的转换](#题目018--python里面如何实现tuple和list的转换)
    * [【题目:019】|  请写出一段Python代码实现删除一个list里面的重复元素](#题目019--请写出一段python代码实现删除一个list里面的重复元素)
    * [【题目:020】|  Python是如何进行类型转换的](#题目020--python是如何进行类型转换的)
    * [【题目:021】|  如何知道一个Python对象的类型](#题目021--如何知道一个python对象的类型)
    * [【题目:022】|  Python里面如何拷贝一个对象](#题目022--python里面如何拷贝一个对象)
    * [【题目:023】|  Python中pass语句的作用是什么](#题目023--python中pass语句的作用是什么)
    * [【题目:024】|  写一段程序逐行读入一个文本文件，并在屏幕上打印出来](#题目024--写一段程序逐行读入一个文本文件并在屏幕上打印出来)
    * [【题目:025】|  如何用Python删除一个文件](#题目025--如何用python删除一个文件)
    * [【题目:026】|  Python代码得到列表list的交集与差集](#题目026--python代码得到列表list的交集与差集)
    * [【题目:027】|  Python是如何进行内存管理的](#题目027--python是如何进行内存管理的)
    * [【题目:028】|  介绍一下Python下range()函数的用法](#题目028--介绍一下python下range函数的用法)
    * [【题目:029】|  Python异常处理介绍一下](#题目029--python异常处理介绍一下)
    * [【题目:030】|  介绍一下Python中的filter方法](#题目030--介绍一下python中的filter方法)
    * [【题目:031】|  介绍一下except的用法和作用](#题目031--介绍一下except的用法和作用)
    * [【题目:032】|  如何用Python来进行查询和替换一个文本字符串](#题目032--如何用python来进行查询和替换一个文本字符串)
    * [【题目:033】|  Python如何copy一个文件](#题目033--python如何copy一个文件)
    * [【题目:034】|  Python判断当前用户是否是root](#题目034--python判断当前用户是否是root)
    * [【题目:035】|  用Python写一个for循环的例子](#题目035--用python写一个for循环的例子)
    * [【题目:036】|  介绍一下Python中webbrowser的用法](#题目036--介绍一下python中webbrowser的用法)
    * [【题目:037】|  默写尽可能多的str对象的方法](#题目037--默写尽可能多的str对象的方法)
    * [【题目:038】|  现在有一个dict对象adict,里面包含了一百万个元素,查找其中的某个元素的平均需要多少次比较](#题目038--现在有一个dict对象adict里面包含了一百万个元素查找其中的某个元素的平均需要多少次比较)
    * [【题目:039】|  有一个list对象alist，里面的所有元素都是字符串，编写一个函数对它实现一个大小写无关的排序](#题目039--有一个list对象alist里面的所有元素都是字符串编写一个函数对它实现一个大小写无关的排序)
    * [【题目:040】|  有一个排好序地list对象alist，查找其中是否有某元素a](#题目040--有一个排好序地list对象alist查找其中是否有某元素a)
    * [【题目:041】|  请用Python写一个获取用户输入数字，并根据数字大小输出不同信息的脚本](#题目041--请用python写一个获取用户输入数字并根据数字大小输出不同信息的脚本)
    * [【题目:042】|  打乱一个排好序的list对象alist](#题目042--打乱一个排好序的list对象alist)
    * [【题目:043】|  有二维的list对象alist，假定其中的所有元素都具有相同的长度，写一段程序根据元素的第二个元素排序](#题目043--有二维的list对象alist假定其中的所有元素都具有相同的长度写一段程序根据元素的第二个元素排序)
    * [【题目:044】|  inspect模块有什么用](#题目044--inspect模块有什么用)
    * [【题目:045】|  Python处理命令行参数示例代码](#题目045--python处理命令行参数示例代码)
    * [【题目:046】|  介绍一下Python getopt模块](#题目046--介绍一下python-getopt模块)
    * [【题目:047】|  Python列表与元组的区别是什么？分别在什么情况下使用？](#题目047--python列表与元组的区别是什么分别在什么情况下使用)
    * [【题目:048】|  有一个长度是101的数组，存在1~100的数字，有一个是重复的，拿重复的找出来](#题目048--有一个长度是101的数组存在1100的数字有一个是重复的拿重复的找出来)
    * [【题目:049】|  set是在哪个版本成为build-in types的？举例说明,并说明为什么当时选择了set这种数据结构](#题目049--set是在哪个版本成为build-in-types的举例说明并说明为什么当时选择了set这种数据结构)
    * [【题目:050】| 说说decorator的用法和它的应用场景，如果可以的话，写一个decorator](#题目050-说说decorator的用法和它的应用场景如果可以的话写一个decorator)
    * [【题目:051】| 写一个类，并让它尽可能多的支持操作符](#题目051-写一个类并让它尽可能多的支持操作符)
    * [【题目:053】| Python如何实现单例模式](#题目053-python如何实现单例模式)
    * [【题目:056】| 介绍一下Python Date Time方面的类](#题目056-介绍一下python-date-time方面的类)
    * [【题目:057】| 写一个简单的Python socket编程](#题目057-写一个简单的python-socket编程)
    * [【题目:058】| Tkinter的ToolTip控件](#题目058-tkinter的tooltip控件)
    * [【题目:059】| 解释一下python的and-or语法](#题目059-解释一下python的and-or语法)
    * [【题目:060】| Python里关于“堆”这种数据结构的模块是哪个？“堆”有什么优点和缺点](#题目060-python里关于堆这种数据结构的模块是哪个堆有什么优点和缺点)
    * [【题目:061】| 实现一个stack](#题目061-实现一个stack)
    * [【题目:062】| 编写一个简单的ini文件解释器](#题目062-编写一个简单的ini文件解释器)
    * [【题目:064】| src = "security/afafsff/?ip=123.4.56.78&id=45"，请写一段代码用正则匹配出IP](#题目064-src--securityafafsffip12345678id45请写一段代码用正则匹配出ip)
    * [【题目:064】| 已知仓库中有若干商品，以及相应库存，类似：](#题目064-已知仓库中有若干商品以及相应库存类似)

<!-- vim-markdown-toc -->
# Python面试题汇总
[转自](http://blog.csdn.net/jerry_1126/article/details/44023949)

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

## 【题目:001】| 说说你对zen of python的理解，你有什么办法看到它?

Python之禅,Python秉承一种独特的简洁和可读行高的语法，以及高度一致的编程模式，符合“大脑思维习惯”，使Python易于学习、理解和记忆。
Python同时采用了一条极简主义的设计理念，了解完整的Python哲学理念，可以在任何一个Python交互解释器中键入import this命令，
这是Python隐藏的一个彩蛋:描绘了一系列Python设计原则。如今已是Python社区内流行的行话"EIBTI"，明了胜于晦涩这条规则的简称. 
在Python的思维方式中，明了胜于晦涩，简洁胜于复杂。

```python
>>> import this    
The Zen of Python, by Tim Peters    
    
Beautiful is better than ugly.    
Explicit is better than implicit.    
Simple is better than complex.    
Complex is better than complicated.    
Flat is better than nested.    
Sparse is better than dense.    
Readability counts.    
Special cases aren't special enough to break the rules.    
Although practicality beats purity.    
Errors should never pass silently.    
Unless explicitly silenced.    
In the face of ambiguity, refuse the temptation to guess.    
There should be one -- and preferably only one -- obvious way to do it.    
Although that way may not be obvious at first unless you're Dutch.    
Now is better than never.    
Although never is often better than *right* now.    
If the implementation is hard to explain, it's a bad idea.    
If the implementation is easy to explain, it may be a good idea.    
Namespaces are one honking great idea -- let's do more of those!  
```

## 【题目:002】| 说说你对pythonic的看法，尝试解决下面的小问题

```python
#简洁，明了，严谨，灵活

#交换两个变量值    
a,b = b,a    
    
#去掉list中的重复元素    
old_list = [1,1,1,3,4]    
new_list = list(set(old_list))    
    
#翻转一个字符串    
s = 'abcde'    
ss = s[::-1]    

list初始化n个相同值两种方式
>>> lst = ['x' for n in range(5)]
>>> print(lst)
['x', 'x', 'x', 'x', 'x']
>>> lst = ['z']*5
>>> print(lst)
['z', 'z', 'z', 'z', 'z']
>>> lst = [0]*3
>>> print(lst)
[0, 0, 0]

创建二维数组的办法
2.1 直接创建法
test = [0, 0, 0], [0, 0, 0], [0, 0, 0]]
简单粗暴，不过太麻烦，一般不用。

2.2 列表生成式法
test = [[0 for i in range(m)] for j in range(n)]

2.3 使用模块numpy创建
import numpy as np
test = np.zeros((m, n), dtype=np.int)

dict初始化
>>> # 示例一:
>>> D = {k:0 for k in 'ab'}
>>> D
{'a': 0, 'b': 0}
>>> # 示例二:
>>> D = {k:v for (k,v) in zip(['a', 'b'], [1, 2])}
>>> D
{'a': 1, 'b': 2}
    
#用两个元素之间有对应关系的list构造一个dict    
names = ['jianpx', 'yue']    
ages = [23, 40]    
m = dict(zip(names,ages))    
    
#将数量较多的字符串相连，如何效率较高，为什么    
fruits = ['apple', 'banana']    
result = ''.join(fruits)    
    
#python字符串效率问题之一就是在连接字符串的时候使用‘+’号，例如 s = ‘s1’ + ‘s2’ + ‘s3’ + ...+’sN’，总共将N个字符串连接起来， 但是使用+号的话，
python需要申请N-1次内存空间， 然后进行字符串拷贝。原因是字符串对象PyStringObject在python当中是不可变对象，所以每当需要合并两个字符串的时候，
就要重新申请一个新的内存空间（大小为两个字符串长度之和）来给这个合并之后的新字符串，然后进行拷贝。 所以用+号效率非常低。
建议在连接字符串的时候使用字符串本身的方法 join（list），这个方法能提高效率，原因是它只是申请了一次内存空间， 因为它可以遍历list中的元素计算出总共需要申请的内存空间的大小，一次申请完。 
```

## 【题目:003】| 你调试python代码的方法有哪些?  
具体IDE都有调试，比如:IDLE, Eclipse+Pydev都可以设置断点调试。   
pdb模块也可以做调试。  
还有PyChecker和Pylint  
PyChecker是一个python代码的静态分析工具，它可以帮助查找python代码的bug, 会对代码的复杂度和格式提出警告    
Pylint   是另外一个工具可以进行coding standard检查。   

## 【题目:004】| 你在github上都fork过哪些python库，列举一下你经常使用的，每个库用一句话描述下其功能

http://rogerdudler.github.io/git-guide/index.zh.html    #关于git简明指南    
http://www.zhihu.com/question/20070065                  #关于git的BBS    
http://www.techug.com/githug-for-designer               #关于github的    

## 【题目:005】|  什么是GIL?
什么是GIL(Global Interpreter Lock)全局解释器锁? 简单地说就是:  
每一个interpreter进程,只能同时仅有一个线程来执行, 获得相关的锁, 存取相关的资源.  
那么很容易就会发现,如果一个interpreter进程只能有一个线程来执行,   
多线程的并发则成为不可能, 即使这几个线程之间不存在资源的竞争.  
从理论上讲,我们要尽可能地使程序更加并行, 能够充分利用多核的功能.  

## 【题目:006】|  什么是元类(meta_class)?
元类就是用来创建类的“东西”  
[详情操作](http://blog.jobbole.com/21351/）  

## 【题目:007】|  对比一下dict中items与iteritems?

```python
>>> D = {'a':1,'b':2,'c':3,'d':4}    
>>> D.items()                       #一次性取出所有    
[('a', 1), ('c', 3), ('b', 2), ('d', 4)]    
>>> D.iteritems()                   #迭代对象，每次取出一个。用for循环遍历出来；    
<dictionary-itemiterator object at 0x00000000026243B8>    
>>> for i in D.iteritems():    
...   print i,    
...    
('a', 1) ('c', 3) ('b', 2) ('d', 4)    
>>> for k,v in D.iteritems():    
...   print k,    
...    
a c b d  
```    
总结:   
1. 一般iteritems()迭代的办法比items()要快，特别是数据库比较大时。  
2. 在Python3中一般取消前者函数  

## 【题目:008】是否遇到过python的模块间循环引用的问题，如何避免它?

这是代码结构设计的问题，模块依赖和类依赖  
如果老是觉得碰到循环引用，很可能是模块的分界线划错地方了。可能是把应该在一起的东西硬拆开了，可能是某些职责放错地方了，可能是应该抽象的东西没抽象  
总之微观代码规范可能并不能帮到太多，重要的是更宏观的划分模块的经验技巧，推荐uml，脑图，白板等等图形化的工具先梳理清楚整个系统的总体结构和职责分工  
  
采取办法，从设计模式上来规避这个问题，比如:  
1. 使用 `__all__` 白名单开放接口  
2. 尽量避免 import  

## 【题目:009】|  有用过with statement吗？它的好处是什么？

```python
>>> with open('text.txt') as myfile:    
...   while True:    
...     line = myfile.readline()    
...     if not line:    
...       break    
...     print line    
    
# with语句使用所谓的上下文管理器对代码块进行包装，允许上下文管理器实现一些设置和清理操作。    
# 例如：文件可以作为上下文管理器使用，它们可以关闭自身作为清理的一部分。    
# NOTE：在PYTHON2.5中，需要使用from __future__ import with_statement进行with语句的导入    
```

## 【题目:010】用Python生成指定长度的斐波那契数列

```python
def fibs(x):  
    result = [0, 1]  
    for index in range(x-2):  
        result.append(result[-2]+result[-1])  
    return result  
  
if __name__=='__main__':  
    num = input('Enter one number: ')  
    print fibs(num)
```
      
## 【题目:011】|  Python里如何生产随机数

```python
>>> import random  
>>> random.random()  
0.29495314937268713  
>>> random.randint(1,11)  
8  
>>> random.choice(range(11))  
3
```
  
## 【题目:012】|  Python里如何反序的迭代一个序列

```python
# 如果是一个list, 最快的解决方案是：  
  
list.reverse()  
try:  
    for x in list:  
        “do something with x”  
finally:  
    list.reverse()  
  
# 如果不是list, 最通用但是稍慢的解决方案是：  
for i in range(len(sequence)-1, -1, -1):  
x = sequence[i]  
```

## 【题目:013】|  Python中如何定义一个函数

```python
def func(arg, *args, **kwagrs):   #普通函数  
    func_body  
    return   
  
lambda x: x **2                   #匿名函数  
```
 
## 【题目:015】|  Python里面search()和match()的区别
```python
>>> import re  
>>> re.match(r'python','Programing Python, should be pythonic')  
>>> obj1 = re.match(r'python','Programing Python, should be pythonic')  #返回None  
>>> obj2 = re.search(r'python','Programing Python, should be pythonic') #找到pythonic  
>>> obj2.group()  
'python'  
#re.match只匹配字符串的开始，如果字符串开始不符合正则表达式，则匹配失败，函数返回None；  
#re.search匹配整个字符串，直到找到一个匹配。  
```

## 【题目:016】|  Python程序中文输出问题怎么解决
在Python3中，对中文进行了全面的支持，但在Python2.x中需要进行相关的设置才能使用中文。否则会出现乱码。  
Python默认采取的ASCII编码，字母、标点和其他字符只使用一个字节来表示，但对于中文字符来说，一个字节满足不了需求。  
为了能在计算机中表示所有的中文字符，中文编码采用两个字节表示。如果中文编码和ASCII混合使用的话，就会导致解码错误，从而才生乱码。  
解决办法:  
交互式命令中：一般不会出现乱码，无需做处理   
py脚本文件中：跨字符集必须做设置，否则乱码  
1. 首先在开头一句添加:  
```python  
# coding = utf-8    
# 或    
# coding = UTF-8    
# 或    
# -*- coding: utf-8 -*-   
```  
2. 其次需将文件保存为UTF-8的格式！  
3. 最后: s.decode('utf-8').encode('gbk')  

## 【题目:017】|  什么是lambda函数

函数使用:  
1. 代码块重复，这时候必须考虑到函数，降低程序的冗余度  
2. 代码块复杂，这时候必须考虑到函数，降低程序的复杂度  
Python有两种函数,一种是def定义，一种是lambda函数()  
当程序代码很短，且该函数只使用一次，为了程序的简洁，及节省变量内存占用空间，引入了匿名函数这个概念    
```python
>>> nums = range(2,20)  
>>> for i in nums:  
        nums = filter(lambda x:x==i or x % i,nums)  
>>> nums  
[2, 3, 5, 7, 11, 13, 17, 19]  
```

## 【题目:018】|  Python里面如何实现tuple和list的转换  
```python
#From list to Tuple                   
tuple(a_list)     
  
#From Tuple to List  
def to_list(t):   
    return [i if not isinstance(i,tuple) else to_list(i) for i in t]  
```

## 【题目:019】|  请写出一段Python代码实现删除一个list里面的重复元素  
```python
>>> L1 = [4,1,3,2,3,5,1]  
>>> L2 = []  
>>> [L2.append(i) for i in L1 if i not in L2]  
>>> print L2  
[4, 1, 3, 2, 5]  
```

## 【题目:020】|  Python是如何进行类型转换的  
```python
>>> int('1234')                   # 将数字型字符串转为整形  
1234  
>>> float(12)                     # 将整形或数字字符转为浮点型  
12.0  
>>> str(98)                       # 将其他类型转为字符串型  
'98'  
>>> list('abcd')                  # 将其他类型转为列表类型  
['a', 'b', 'c', 'd']  
>>> dict.fromkeys(['name','age']) # 将其他类型转为字典类型  
{'age': None, 'name': None}  
>>> tuple([1, 2, 3, 4])           # 将其他类型转为元祖类型  
(1, 2, 3, 4)  
```  
详细转换总结如下:  
```python
函数                      描述  
int(x [,base])              将x转换为一个整数  
long(x [,base] )            将x转换为一个长整数  
float(x)                    将x转换到一个浮点数  
complex(real [,imag])       创建一个复数  
str(x)                      将对象 x 转换为字符串  
repr(x)                     将对象 x 转换为表达式字符串  
eval(str)                   用来计算在字符串中的有效Python表达式,并返回一个对象  
tuple(s)                    将序列 s 转换为一个元组  
list(s)                     将序列 s 转换为一个列表  
set(s)                      转换为可变集合  
dict(d)                     创建一个字典。d 必须是一个序列 (key,value)元组。  
frozenset(s)                转换为不可变集合  
chr(x)                      将一个整数转换为一个字符  
unichr(x)                   将一个整数转换为Unicode字符  
ord(x)                      将一个字符转换为它的整数值  
hex(x)                      将一个整数转换为一个十六进制字符串  
oct(x)                      将一个整数转换为一个八进制字符串  
```

## 【题目:021】|  如何知道一个Python对象的类型  
```python
>>> type([]);type('');type(0);type({});type(0.0);type((1,))  
<type 'list'>  
<type 'str'>  
<type 'int'>  
<type 'dict'>  
<type 'float'>  
<type 'tuple'>  
```

## 【题目:022】|  Python里面如何拷贝一个对象

切片S[:]  # 注不能应用于字典  
深浅拷贝  # 能应用于所有序列和字典  
1. 浅拷贝D.copy()方法  
2. 深拷贝deepcopy(D)方法  

## 【题目:023】|  Python中pass语句的作用是什么
pass语句什么也不做,一般作为占位符或者创建占位程序  

## 【题目:024】|  写一段程序逐行读入一个文本文件，并在屏幕上打印出来
```python
f = open(filename)    
while True:    
    line = f.readline()    
    if not line: break    
    print(line)    
f.close()   
```
 
## 【题目:025】|  如何用Python删除一个文件
```python
import os  
os.remove(filename)  
```

## 【题目:026】|  Python代码得到列表list的交集与差集
```python
>>> list1 = [1, 3, 4, 6]  
>>> list2 = [1, 2, 3, 4]  
>>> [i for i in list1 if i not in list2]  
[6]  
>>> [i for i in list1 if i in list2]  
[1, 3, 4]  
```

## 【题目:027】|  Python是如何进行内存管理的
python内部使用引用计数，来保持追踪内存中的对象，Python内部记录了对象有多少个引用，即引用计数，当对象被创建时就创建了一个引用计数，当对象不再需要时，
这个对象的引用计数为0时，它被垃圾回收。所有这些都是 **自动完成**，不需要像C一样，人工干预，从而提高了程序员的效率和程序的健壮性。  

## 【题目:028】|  介绍一下Python下range()函数的用法  
```python
>>> range(10)  
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]  
>>> range(1, 10)  
[1, 2, 3, 4, 5, 6, 7, 8, 9]  
>>> range(0, 9, 2)  
[0, 2, 4, 6, 8]  
>>> range(99,0,-10)  
[99, 89, 79, 69, 59, 49, 39, 29, 19, 9]  
```  
相区别的是xrange(),每次只取出一个迭代对象，如果是数据量比较大时，效率较高  
在Python3中，没有xrange()函数，其功能放在了range()函数上  

## 【题目:029】|  Python异常处理介绍一下

程序中出现异常情况时就需要异常处理。比如当你打开一个不存在的文件时。当你的程序中有  
一些无效的语句时，Python会提示你有错误存在。下面是一个拼写错误的例子，print写成了Print  
下面是异常最常见的几种角色  
1. 错误处理  
可以在程序代码中捕捉和相应错误，或者忽略已发生的异常。  
如果忽略错误，PYTHON默认的异常处理行为将启动:停止程序，打印错误信息。  
如果不想启动这种默认行为，就用try语句来捕捉异常并从异常中恢复。  
2. 事件通知  
异常也可用于发出有效状态的信号，而不需在程序间传递结果标志位。或者刻意对其进行测试  
3. 特殊情况处理  
有时，发生了某种很罕见的情况，很难调整代码区处理。通常会在异常处理中处理，从而省去应对特殊情况的代码  
4. 终止行为  
try/finally语句可确保一定会进行需要的结束运算，无论程序是否有异常  
5. 非常规控制流程  

## 【题目:030】|  介绍一下Python中的filter方法
filter就像map,reduce,apply,zip等都是内置函数，用C语言实现，具有速度快，功能强大等  
  
优点:  
用于过滤与函数func()不匹配的值, 类似于SQL中select value != 'a'  
相当于一个迭代器，调用一个布尔函数func来迭代seq中的每个元素，返回一个是bool_seq返回为True的序列  
第一个参数: function or None, 函数或None  
第二个参数: sequence,序列  

## 【题目:031】|  介绍一下except的用法和作用
try/except:          捕捉由PYTHON自身或写程序过程中引发的异常并恢复  
except:              捕捉所有其他异常  
except name:         只捕捉特定的异常  
except name, value:  捕捉异常及格外的数据(实例)  
except (name1,name2) 捕捉列出来的异常  
except (name1,name2),value: 捕捉任何列出的异常，并取得额外数据  
else:                如果没有引发异常就运行  
finally:             总是会运行此处代码  

## 【题目:032】|  如何用Python来进行查询和替换一个文本字符串
```python
>>> words = 'Python is a very funny language!'  
>>> words.find('Python')             # 返回的为0或正数时，为其索引号  
0  
>>> words.find('is')  
7  
>>> words.find('dafa')               # 返回-1表示查找失败  
-1  
>>> words.replace('Python', 'Perl')  # replace()替换  
'Perl is a very funny language!'  
```

## 【题目:033】|  Python如何copy一个文件
```python
import shutil  
shutil.copyfile('a.py', 'copy_a.py')  
```

## 【题目:034】|  Python判断当前用户是否是root  
```python
import os  
if os.getuid() != 0:    # root账号的uid=0  
    print os.getuid()  
    print 'Should run as root account'  
else:  
    print 'Hello, Root!'  
```

## 【题目:035】|  用Python写一个for循环的例子  
for循环可以遍历序列(列表，字符串，元祖),range()及迭代对象，如xrange()  
```python
names = ['Alice', 'Betty', 'Fred', 'Tom']  
for index, name in enumerate(names):  
    print 'index:',index,'=>', name  

# 输出结果    
index: 0 => Alice  
index: 1 => Betty  
index: 2 => Fred  
index: 3 => Tom  
```

## 【题目:036】|  介绍一下Python中webbrowser的用法
webbrowser模块提供了一个高级接口来显示基于Web的文档，大部分情况下只需要简单的调用open()方法。  
  
webbrowser定义了如下的异常：exception webbrowser.Error, 当浏览器控件发生错误是会抛出这个异常  
  
webbrowser有以下方法：  
  
webbrowser.open(url[, new=0[, autoraise=1]])  
  
这个方法是在默认的浏览器中显示url, 如果new = 0, 那么url会在同一个浏览器窗口下打开，如果new = 1, 会打开一个新的窗口，如果new = 2, 会打开一个新的tab, 如果autoraise ＝ true, 窗口会自动增长。  
  
webbrowser.open_new(url)  
在默认浏览器中打开一个新的窗口来显示url, 否则，在仅有的浏览器窗口中打开url  
  
webbrowser.open_new_tab(url)  
在默认浏览器中当开一个新的tab来显示url, 否则跟open_new()一样  
  
webbrowser.get([name]) 根据name返回一个浏览器对象，如果name为空，则返回默认的浏览器  
  
webbrowser.register(name, construtor[, instance])  
注册一个名字为name的浏览器，如果这个浏览器类型被注册就可以用get()方法来获取。  

## 【题目:037】|  默写尽可能多的str对象的方法
```python
#方法                                   #描述    
-------------------------------------------------------------------------------------------------    
S.capitalize()                          #返回首字母大写的字符串的副本    
S.center(width[,fillchar])              #返回一个长度为max(len(S),width),S居中，两侧fillchar填充    
S.count(sub[,start[,end]])              #计算子字符串sub的出现次数，可将搜索范围限制为S[start:end]    
S.decode([encoding[,error]])            #返回使用给定编码方式的字符串的解码版本，由error指定错误处理方式    
S.endswith(suffix[start[,end]])         #检查S是否以suffix结尾，可给定[start:end]来选择匹配的范围    
S.expandtabs([tabsize])                 #返回字符串的副本，其中tab字符会使用空格进行扩展，可选择tabsize    
S.find(sub[,start[,end]])               #返回子字符串sub的第一个索引，不存在则为-1,可选择搜索范围    
S.index(sub[,start[,end]])              #返回子字符串sub的第一个索引，不存在则引发ValueError异常.    
S.isalnum()                             #检查字符串是否由字母或数字字符组成    
S.isalpha()                             #检查字符串是否由字母字符组成    
S.isdigit()                             #检查字符串是否由数字字符组成    
S.islower()                             #检查字符串是否由小写字母组成    
S.isspace()                             #检查字符串是否由空格组成    
S.istitle()                             #检查字符串时候首字母大写    
S.isupper()                             #检查字符串是否由大写字母组成    
S.join(sequence)                        #返回其中sequence的字符串元素由S连接的字符串    
S.ljust(width[,fillchar])               #返回S副本左对齐的字符串,长度max(len(S),W),右侧fillchar填充    
S.lower()                               #返回所有字符串都为小写的副本    
S.lstrip([char])                        #向左移除所有char，默认移除(空格,tab,\n)    
S.partition(seq)                        #在字符串中搜索seq并返回    
S.replace(old,new[,max])                #将new替换olad,最多可替换max次    
S.rfind(sub[,start[,end]])              #返回sub所在的最后一个索引，不存在则为-1,可定搜索范围S[start:end]    
S.rindex(sub[,start[,end]])             #返回sub所在的最后一个索引，不存在则会引发ValueError异常。    
S.rjust(width[,fillchar])               #返回S副本右对齐的字符串,长度max(len(S),W),左侧fillchar填充    
S.rpartition(seq)                       #同Partition,但从右侧开始查找    
S.rstip([char])                         #向右移除所有char，默认移除(空格,tab,\n)    
S.rsplit(sep[,maxsplit])                #同split,但是使用maxsplit时是从右往左进行计数    
S.split(sep[,maxsplit])                 #使用sep做为分割符,可使用maxsplit指定最大切分数    
S.zfill(width)                          #在S的左侧以0填充width个字符    
S.upper()                               #返回S的副本，所有字符大写    
S.splitlines([keepends])                #返回S中所有行的列表，可选择是否包括换行符    
S.startswith(prefix[,start[,end]])      #检查S是否以prefix开始，可用[start,end]来定义范围    
S.strip([chars])                        #移除所有字符串中含chars的字符，默认移除(空格，tab,\n)    
S.swapcase()                            #返回S的副本，所有大小写交换    
S.title()                               #返回S的副本，所有单词以大写字母开头    
S.translate(table[,deletechars])        #返回S的副本，所有字符都使用table进行的转换，可选择删除出现在deletechars中的所有字符    
```

## 【题目:038】|  现在有一个dict对象adict,里面包含了一百万个元素,查找其中的某个元素的平均需要多少次比较
O(1)  哈希字典，快速查找，键值映射，键唯一!  

## 【题目:039】|  有一个list对象alist，里面的所有元素都是字符串，编写一个函数对它实现一个大小写无关的排序  
```python
words = ['This','is','a','dog','!']  
words.sort(key=lambda x:x.lower())  
print words  
#输出结果  
>>>   
['!', 'a', 'dog', 'is', 'This']  
```

## 【题目:040】|  有一个排好序的list对象alist，查找其中是否有某元素a  

```python
alist = ['a','s','d','f']  
  
try:  
    alist.index('a')  
    print 'Find it.'  
except ValueError:  
    print 'Not Found.'  
```

## 【题目:041】|  请用Python写一个获取用户输入数字，并根据数字大小输出不同信息的脚本  
```python
num = input('Enter number: ')  
  
if num > 100:  
    print 'The number is over 100'  
elif 0 < num <= 100:  
    print 'The number is between 0~100'  
elif num < 0:  
    print 'The number is negative.'  
else:  
    print 'Not a number'  
```

## 【题目:042】|  打乱一个排好序的list对象alist
```python
# random模块中的shuffle(洗牌函数)  
import random  
alist = [1, 2, 3, 4]  
random.shuffle(alist)     
print alist  
```

## 【题目:043】|  有二维的list对象alist，假定其中的所有元素都具有相同的长度，写一段程序根据元素的第二个元素排序
```python
def sort_lists(lists, sord, idx):  
    if sord == 'desc':  
        lists.sort(key=lambda x:x[idx], reverse=True)  
    else:  
        lists.sort(key=lambda x:x[idx])  
    return lists  
lists = [['cd','ab'],['ef','ac']]  
sort_lists(lists,'desc',1)  
print lists  
  
# 输出结果  
>>>   
[['ef', 'ac'], ['cd', 'ab']]  
```

## 【题目:044】|  inspect模块有什么用
inspect模块提供了一系列函数用于帮助使用自省。  
  
检查对象类型  
is{module|class|function|method|builtin}(obj): 检查对象是否为模块、类、函数、方法、内建函数或方法。  
isroutine(obj): 用于检查对象是否为函数、方法、内建函数或方法等等可调用类型。  
  
获取对象信息  
getmembers(object[, predicate]): 这个方法是dir()的扩展版，它会将dir()找到的名字对应的属性一并返回。  
getmodule(object): 它返回object的定义所在的模块对象。  
get{file|sourcefile}(object): 获取object的定义所在的模块的文件名|源代码文件名（如果没有则返回None）。  
get{source|sourcelines}(object): 获取object的定义的源代码，以字符串|字符串列表返回。  
getargspec(func): 仅用于方法，获取方法声明的参数，返回元组，分别是(普通参数名的列表, *参数名, **参数名, 默认值元组)。   

## 【题目:045】|  Python处理命令行参数示例代码
```python
# 最简单、最原始的方法就是手动解析了  
import sys  
for arg in sys.argv[1:]:  
    print(arg)  
```

## 【题目:046】|  介绍一下Python getopt模块  
```python
# getopt模块是原来的命令行选项解析器，支持UNIX函数getopt()建立的约定。  
# 它会解析一个参数序列，如sys.argv，并返回一个元祖序列和一个非选项参数序列。  
# 目前支持的选项语法包括短格式和长格式选项：-a, -bval, -b val, --noarg, --witharg=val, --witharg val。  
# 如果只是简单的命令行解析，getopt还是不错的选择。一个例子如下  
  
import sys  
import getopt  
  
try:  
    options, remainder = getopt.getopt(sys.argv[1:], 'o:v', ['output=', 'verbose', 'version=',])  
except getopt.GetoptError as err:  
    print 'ERROR:', err  
    sys.exit(1)  
```  
总结下getopt的特点：  
1.  getopt是从前到后解析  
2.  getopt不检查额外参数的合法性，需要自行检查           
3.  短命令行和长命令行是分开解析的</span>  

## 【题目:047】|  Python列表与元组的区别是什么？分别在什么情况下使用？
Python中列表和元组都是序列，因此都能进行添加，删除，更新，切片等操作。但列表是可变对象，元祖是不可变对象。  
元组主要用于函数赋值，字符串格式化等。但列表中的方法更多些，也是PYTHON中更常用的数据结构。  

## 【题目:048】|  有一个长度是101的数组，存在1~100的数字，有一个是重复的，把重复的找出来
```python
# Python中，主要是拿count(i) ==2的找出来即可，再利用列表推导式  
>>> l = [1, 2, 3, 4, 2]  
>>> tmp = []  
>>> [tmp.append(i) for i in l if l.count(i) == 2]  
[None, None]  
>>> tmp  
[2, 2]  
>>> set(tmp)  
set([2])  
```

## 【题目:049】|  set是在哪个版本成为build-in types的？举例说明,并说明为什么当时选择了set这种数据结构


python的set和其他语言类似, 是一个 **无序不重复元素集**, 基本功能包括关系测试和消除重复元素. 集合对象还支持union(联合), intersection(交), difference(差)和sysmmetric difference(对称差集)等数学运算.  
  
sets 支持 x in set, len(set),和 for x in set。作为一个无序的集合，sets不记录元素位置或者插入点。因此，sets不支持 indexing, slicing, 或其它类序列（sequence-like）的操作。  
  
  
下面来点简单的小例子说明。  
```python  
>>> x = set('spam')  
>>> y = set(['h','a','m'])  
>>> x, y  
(set(['a', 'p', 's', 'm']), set(['a', 'h', 'm']))  
```  

再来些小应用。  
```python  
>>> x & y # 交集  
set(['a', 'm'])  
  
>>> x | y # 并集  
set(['a', 'p', 's', 'h', 'm'])  
  
>>> x - y # 差集  
set(['p', 's'])  
```  

去除海量列表里重复元素，用hash来解决也行，只不过感觉在性能上不是很高，用set解决还是很不错的，示例如下：  
```python  
>>> a = [11,22,33,44,11,22]  
>>> b = set(a)  
>>> b  
set([33, 11, 44, 22])  
>>> c = [i for i in b]  
>>> c  
[33, 11, 44, 22]  
```    
很酷把，几行就可以搞定。  
  
1.8　集合   
   
集合用于包含一组无序的对象。要创建集合，可使用set()函数并像下面这样提供一系列的项：  
s = set([3,5,9,10])      #创建一个数值集合  
t = set("Hello")         #创建一个唯一字符的集合  
  
与列表和元组不同，集合是无序的，也无法通过数字进行索引。此外，集合中的元素不能重复。例如，如果检查前面代码中t集合的值，结果会是：  
```python     
>>> t  
set(['H', 'e', 'l', 'o'])  
```
注意只出现了一个'l'。  
  
集合支持一系列标准操作，包括并集、交集、差集和对称差集，例如：  
a = t | s          # t 和 s的并集  
b = t & s          # t 和 s的交集  
c = t – s         # 求差集（项在t中，但不在s中）  
d = t ^ s          # 对称差集（项在t或s中，但不会同时出现在二者中）
  
基本操作：  
```python  
t.add('x')            # 添加一项  
s.update([10,37,42])  # 在s中添加多项  
```  
     
使用remove()可以删除一项：  
t.remove('H')  
  
len(s)  
set 的长度  
  
x in s  
测试 x 是否是 s 的成员  
  
x not in s  
测试 x 是否不是 s 的成员  
  
s.issubset(t)  
s <= t  
测试是否 s 中的每一个元素都在 t 中  
  
s.issuperset(t)  
s >= t  
测试是否 t 中的每一个元素都在 s 中  
  
s.union(t)  
s | t  
返回一个新的 set 包含 s 和 t 中的每一个元素  
  
s.intersection(t)  
s & t  
返回一个新的 set 包含 s 和 t 中的公共元素  
  
s.difference(t)  
s - t  
返回一个新的 set 包含 s 中有但是 t 中没有的元素  
  
s.symmetric_difference(t)  
s ^ t  
返回一个新的 set 包含 s 和 t 中不重复的元素  
  
s.copy()  
返回 set “s”的一个浅复制  
  
  
请注意：union(), intersection(), difference() 和 symmetric_difference() 的非运算符（non-operator，就是形如 s.union()这样的）版本将会接受任何 iterable 作为参数。相反，它们的运算符版本（operator based counterparts）要求参数必须是 sets。这样可以避免潜在的错误，如：为了更可读而使用 set('abc') & 'cbs' 来替代 set('abc').intersection('cbs')。从 2.3.1 版本中做的更改：以前所有参数都必须是 sets。  
  
另外，Set 和 ImmutableSet 两者都支持 set 与 set 之间的比较。两个 sets 在也只有在这种情况下是相等的：每一个 set 中的元素都是另一个中的元素（二者互为subset）。一个 set 比另一个 set 小，只有在第一个 set 是第二个 set 的 subset 时（是一个 subset，但是并不相等）。一个 set 比另一个 set 打，只有在第一个 set 是第二个 set 的 superset 时（是一个 superset，但是并不相等）。  
  
子 set 和相等比较并不产生完整的排序功能。例如：任意两个 sets 都不相等也不互为子 set，因此以下的运算都会返回 False：a<b, a==b, 或者a>b。因此，sets 不提供 __cmp__ 方法。  
  
因为 sets 只定义了部分排序功能（subset 关系），list.sort() 方法的输出对于 sets 的列表没有定义。  
  
  
运算符  
   运算结果  
  
hash(s)  
   返回 s 的 hash 值  
  
  
下面这个表列出了对于 Set 可用二对于 ImmutableSet 不可用的运算：  
  
运算符（voperator）  
等价于  
运算结果  
  
s.update(t)  
s |= t  
返回增加了 set “t”中元素后的 set “s”  
  
s.intersection_update(t)  
s &= t  
返回只保留含有 set “t”中元素的 set “s”  
  
s.difference_update(t)  
s -= t  
返回删除了 set “t”中含有的元素后的 set “s”  
  
s.symmetric_difference_update(t)  
s ^= t  
返回含有 set “t”或者 set “s”中有而不是两者都有的元素的 set “s”  
  
s.add(x)
向 set “s”中增加元素 x  
  
s.remove(x)
从 set “s”中删除元素 x, 如果不存在则引发 KeyError  
  
s.discard(x)
如果在 set “s”中存在元素 x, 则删除  
  
s.pop()
删除并且返回 set “s”中的一个不确定的元素, 如果为空则引发 KeyError  
  
s.clear()
删除 set “s”中的所有元素  
  
  
请注意：非运算符版本的 update(), intersection_update(), difference_update()和symmetric_difference_update()将会接受任意 iterable 作为参数。从 2.3.1 版本做的更改：以前所有参数都必须是 sets。  
  
还请注意：这个模块还包含一个 union_update() 方法，它是 update() 方法的一个别名。包含这个方法是为了向后兼容。程序员们应该多使用 update() 方法，因为这个方法也被内置的 set() 和 frozenset() 类型支持。  

## 【题目:050】| 说说decorator的用法和它的应用场景，如果可以的话，写一个decorator  
所谓装饰器就是把函数包装一下，为函数添加一些附加功能，装饰器就是一个函数，参数为被包装的函数，返回包装后的函数：  
```python  
def d(fp):  
    def _d(*arg, **karg):  
        print "do sth before fp.."  
        r= fp(*arg, **karg)  
        print "do sth after fp.."  
        return r  
    return _d  
  
@d  
def f():  
    print "call f"  
#上面使用@d来表示装饰器和下面是一个意思  
#f = d(f)  
      
f()#调用f  
```

## 【题目:051】| 写一个类，并让它尽可能多的支持操作符  
```python
class Array:  
    __list = []  
  
    def __init__(self):  
        print "constructor"  
  
    def __del__(self):  
        print "destructor"  
  
    def __str__(self):  
        return "this self-defined array class"  
  
    def __getitem__(self, key):  
        return self.__list[key]  
  
    def __len__(self):  
        return len(self.__list)  
  
    def Add(self, value):  
        self.__list.append(value)  
  
    def Remove(self, index):  
        del self.__list[index]  
  
    def DisplayItems(self):  
        print "show all items----"  
        for item in self.__list:  
            print item  
  
arr = Array()   #constructor  
print arr    #this self-defined array class  
print len(arr)   #0  
arr.Add(1)  
arr.Add(2)  
arr.Add(3)  
print len(arr)   #3  
print arr[0]   #1  
arr.DisplayItems()  
#show all items----  
#1  
#2  
#3  
arr.Remove(1)  
arr.DisplayItems()  
#show all items----  
#1  
#3  
#destructor  
```
 
## 【题目:053】| Python如何实现单例模式
```python
#-*- encoding=utf-8 -*-  
print '----------------------方法1--------------------------'  
#方法1,实现__new__方法  
#并在将一个类的实例绑定到类变量_instance上,  
#如果cls._instance为None说明该类还没有实例化过,实例化该类,并返回  
#如果cls._instance不为None,直接返回cls._instance  
class Singleton(object):  
    def __new__(cls, *args, **kw):  
        if not hasattr(cls, '_instance'):  
            orig = super(Singleton, cls)  
            cls._instance = orig.__new__(cls, *args, **kw)  
        return cls._instance  
  
class MyClass(Singleton):  
    a = 1  
  
one = MyClass()  
two = MyClass()  
  
two.a = 3  
print one.a  
#3  
#one和two完全相同,可以用id(), ==, is检测  
print id(one)  
#29097904  
print id(two)  
#29097904  
print one == two  
#True  
print one is two  
#True  
  
print '----------------------方法2--------------------------'  
#方法2,共享属性;所谓单例就是所有引用(实例、对象)拥有相同的状态(属性)和行为(方法)  
#同一个类的所有实例天然拥有相同的行为(方法),  
#只需要保证同一个类的所有实例具有相同的状态(属性)即可  
#所有实例共享属性的最简单最直接的方法就是__dict__属性指向(引用)同一个字典(dict)  
#可参看:http://code.activestate.com/recipes/66531/  
class Borg(object):  
    _state = {}  
    def __new__(cls, *args, **kw):  
        ob = super(Borg, cls).__new__(cls, *args, **kw)  
        ob.__dict__ = cls._state  
        return ob  
  
class MyClass2(Borg):  
    a = 1  
  
one = MyClass2()  
two = MyClass2()  
  
#one和two是两个不同的对象,id, ==, is对比结果可看出  
two.a = 3  
print one.a  
#3  
print id(one)  
#28873680  
print id(two)  
#28873712  
print one == two  
#False  
print one is two  
#False  
#但是one和two具有相同的（同一个__dict__属性）,见:  
print id(one.__dict__)  
#30104000  
print id(two.__dict__)  
#30104000  
  
print '----------------------方法3--------------------------'  
#方法3:本质上是方法1的升级（或者说高级）版  
#使用__metaclass__（元类）的高级python用法  
class Singleton2(type):  
    def __init__(cls, name, bases, dict):  
        super(Singleton2, cls).__init__(name, bases, dict)  
        cls._instance = None  
    def __call__(cls, *args, **kw):  
        if cls._instance is None:  
            cls._instance = super(Singleton2, cls).__call__(*args, **kw)  
        return cls._instance  
  
class MyClass3(object):  
    __metaclass__ = Singleton2  
  
one = MyClass3()  
two = MyClass3()  
  
two.a = 3  
print one.a  
#3  
print id(one)  
#31495472  
print id(two)  
#31495472  
print one == two  
#True  
print one is two  
#True  
  
print '----------------------方法4--------------------------'  
#方法4:也是方法1的升级（高级）版本,  
#使用装饰器(decorator),  
#这是一种更pythonic,更elegant的方法,  
#单例类本身根本不知道自己是单例的,因为他本身(自己的代码)并不是单例的  
def singleton(cls, *args, **kw):  
    instances = {}  
    def _singleton():  
        if cls not in instances:  
            instances[cls] = cls(*args, **kw)  
        return instances[cls]  
    return _singleton  
 
@singleton  
class MyClass4(object):  
    a = 1  
    def __init__(self, x=0):  
        self.x = x  
  
one = MyClass4()  
two = MyClass4()  
  
two.a = 3  
print one.a  
#3  
print id(one)  
#29660784  
print id(two)  
#29660784  
print one == two  
#True  
print one is two  
#True  
one.x = 1  
print one.x  
#1  
print two.x  
#1  
```

## 【题目:056】| 介绍一下Python Date Time方面的类

一.time模块  
time模块提供各种操作时间的函数  
一般有两种表示时间的方式:  
第一种: 是时间戳的方式(相对于1970.1.1 00:00:00以秒计算的偏移量),时间戳是惟一的  
第二种: 以数组的形式表示即(struct_time),共有九个元素，分别表示，同一个时间戳的struct_time会因为时区不同而不同  
  
二.datetime模块  
Python提供了多个内置模块用于操作日期时间，像calendar，time，datetime。time模块。  
相比于time模块，datetime模块的接口则更直观、更容易调用。  
datetime模块定义了下面这几个类：  
datetime.date：表示日期的类。常用的属性有year, month, day；  
datetime.time：表示时间的类。常用的属性有hour, minute, second, microsecond；  
datetime.datetime：表示日期时间。  
datetime.timedelta：表示时间间隔，即两个时间点之间的长度。  
datetime.tzinfo：与时区有关的相关信息。  
datetime中，表示日期时间的是一个datetime对象  
datetime中提供了strftime方法，可以将一个datetime型日期转换成字符串：  

## 【题目:057】| 写一个简单的Python socket编程

服务器端程序:  
```python
# FileName: server.py  
  
import socket  
  
sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)  
sock.bind(('localhost', 8001))  
  
sock.listen(5)  
while True:  
    conn, addr = sock.accept()  
    try:  
        conn.settimeout(5)  
        buff = conn.recv(1024)  
        if buff == '1':  
            conn.send('Hello, Client...')  
        else:  
            conn.send('Please, Go Out...')  
    except socket.timeout:  
        print 'Socket Time Out...'  
    finally:  
        conn.close()  
```

客户端程序:  
```python
# FileName: client.py  
import socket  
import time  
  
sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)  
sock.connect(('localhost', 8001))  
time.sleep(2)  
sock.send('1')  
print sock.recv(1024)  
sock.close()  
```  
在终端运行server.py，然后运行clien.py，会在终端打印“Hello, Client..."。  
如果更改client.py的sock.send('1')为其它值在终端会打印“Please, Go Out...”。  
更改time.sleep(2)为大于5的数值， 服务器将会超时。

## 【题目:058】| Tkinter的ToolTip控件

Tooltip控件是一个简单，但非常有用的控件。它能够为我们的软件提供非常漂亮的提示信息，提高软件的可用性，给用户比较好的体验。  
假设现在有两个按钮，一个用来预览吊线世系图，一个用来预览行转。为了保持按钮文本的简洁，以及为按钮尺寸所限。  
我们不能可能把这个按钮的主要功能通过text属性表述清楚，这个时候我们就可以用到tooltip控件了.  

## 【题目:059】| 解释一下python的and-or语法

0 and ＊ 不需要再考虑＊是0还是1，结果是0  
1 and ＊ 需要考虑＊是0还是1来决定结果。  
  
1 or ＊ 不需要考虑后面的＊，结果为1  
0 or ＊ 需要考虑后面的＊来决定结果  
  
这个语法看起来类似于 C 语言中的 bool ? a : b 表达式。整个表达式从左到右进行演算，所以先进行 and 表达式的演算。 1 and 'first' 演算值为 'first'，然后 'first' or 'second' 的演算值为 'first'。  
  
0 and 'first' 演算值为 False，然后 0 or 'second' 演算值为 'second'。  
  
and-or主要是用来模仿 三目运算符 bool?a:b的，即当表达式bool为真，则取a否则取b。  
  
and-or 技巧，bool and a or b 表达式，当 a 在布尔上下文中的值为假时，不会像 C 语言表达式 bool ? a : b 那样工作。  

## 【题目:060】| Python里关于“堆”这种数据结构的模块是哪个？“堆”有什么优点和缺点
这个真没有！ 

## 【题目:061】| 实现一个stack  
```python
class Stack :  
    def __init__( self ):  
        ''''' Creates an empty stack. '''  
        self._items = list()  
          
    def isEmpty(self):  
        ''''' Returns True if the stack is empty or False otherwise. '''  
        return len(self) == 0  
  
    def __len__(self):  
        ''''' Returns the number of items in the stack. '''  
        return len(self._items)  
     
    def peek(self):  
       ''''' Returns the top item on the stack without removing it. '''  
       assert not self.isEmpty(), "Cannot peek at an empty stack"  
       return self._items[-1]  
  
    def pop(self):  
        ''''' Removes and returns the top item on the stack. '''  
        assert not self.isEmpty(), "Cannot pop from an empty stack"  
        return self._items.pop()  
     
    def push(self,item):  
        ''''' Push an item onto the top of the stack. '''  
        self._items.append( item )  
```

## 【题目:062】| 编写一个简单的ini文件解释器

db_config.ini  
```python
[baseconf]
host=127.0.0.1
port=3306
user=root
password=root
db_name=evaluting_sys
[concurrent]
processor=20
```

示例代码  
```python
import sys,os
import ConfigParser
def test(config_file_path):
    cf = ConfigParser.ConfigParser()
    cf.read(config_file_path)

    s = cf.sections()
    print 'section:', s

    o = cf.options("baseconf")
    print 'options:', o

    v = cf.items("baseconf")
    print 'db:', v

    db_host = cf.get("baseconf", "host")
    db_port = cf.getint("baseconf", "port")
    db_user = cf.get("baseconf", "user")
    db_pwd = cf.get("baseconf", "password")

    print db_host, db_port, db_user, db_pwd

    cf.set("baseconf", "db_pass", "123456")
    cf.write(open("config_file_path", "w"))
if __name__ == "__main__":
    test("../conf/db_config.ini")
```

## 【题目:064】| src = "security/afafsff/?ip=123.4.56.78&id=45"，请写一段代码用正则匹配出IP  
```python
import re  
  
src = "security/afafsff/?ip=123.4.56.78&id=45"  
m = re.search('ip=(\d{1,3}\.\d{1,3}\.\d{1,3}.\d{1,3})', src, re.S)  # re.S 改变'.'的行为  
print m.group(1)  
# 输出结果  
>>>   
123.4.56.78  
```

## 【题目:064】| 已知仓库中有若干商品，以及相应库存，类似：
袜子，10  
鞋子，20  
拖鞋，30  
项链，40  
要求随机返回一种商品，要求商品被返回的概率与其库存成正比。请描述实现的思路或者直接写一个实现的函数  
```python
# -*- coding: utf-8 -*-   
import random  
  
Wa_Zhi     = ['WZ'] * 100  
Xie_Zi     = ['XZ'] * 200  
Tuo_Xie    = ['TX'] * 300  
Xiang_Lian = ['XL'] * 400  
  
All_Before = Wa_Zhi + Xie_Zi + Tuo_Xie + Xiang_Lian  
All_After  = random.sample(All_Before, 100)  
print All_After.count('WZ')  
print All_After.count('XZ')  
print All_After.count('TX')  
print All_After.count('XL')  
  
#输出结果，大致满足需求1: 2: 3: 4的比例  
>>>   
9  
19  
32  
40  
```
