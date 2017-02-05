# 0.python介绍

## 适合做什么

- 首选是网络应用，包括网站、后台服务等等；
- 其次是许多日常需要的小工具，包括系统管理员需要的脚本任务等等；
- 另外就是作为“胶水”语言，把其他语言开发的程序再包装起来，方便使用。

## 不适合做什么

- 贴近硬件的代码(首选C)
- 移动开发
- 游戏开发C/C++

python可跨平台，在windows, linux, mac上都可以



# 1.python基础

## 数据类型（python是一种动态语言）

(1).整数

Python可以处理任意大小的整数，当然包括负整数，在Python程序中，整数的表示方法和数学上的写法一模一样，例如：1，100，-8080，0，等等。

计算机由于使用二进制，所以，有时候用十六进制表示整数比较方便，十六进制用0x前缀和0-9，a-f表示，例如：0xff00，0xa5b4c3d2，等等。

(2).浮点数

浮点数也就是小数，之所以称为浮点数，是因为按照科学记数法表示时，一个浮点数的小数点位置是可变的，比如，1.23x10^9和12.3x10^8是相等的。浮点数可以用数学写法，如1.23，3.14，-9.01，等等。但是对于很大或很小的浮点数，就必须用科学计数法表示，把10用e替代，1.23x10^9就是1.23e9，或者12.3e8，0.000012可以写成1.2e-5，等等。

整数和浮点数在计算机内部存储的方式是不同的，整数运算永远是精确的（除法难道也是精确的？是的！），而浮点数运算则可能会有四舍五入的误差。

(3).字符串

字符串是以''或""括起来的任意文本，比如'abc'，"xyz"等等。请注意，''或""本身只是一种表示方式，不是字符串的一部分，因此，字符串'abc'只有a，b，c这3个字符。

(4).布尔值

布尔值和布尔代数的表示完全一致，一个布尔值只有True、False两种值，要么是True，要么是False，在Python中，可以直接用True、False表示布尔值（请注意大小写），也可以通过布尔运算计算出来。

布尔值可以用and、or和not运算。

and运算是与运算，只有所有都为 True，and运算结果才是 True。

or运算是或运算，只要其中有一个为 True，or 运算结果就是 True。

not运算是非运算，它是一个单目运算符，把 True 变成 False，False 变成 True。

(5).空值

空值是Python里一个特殊的值，用None表示。None不能理解为0，因为0是有意义的，而None是一个特殊的空值。

此外，Python还提供了列表list、字典dict等多种数据类型，还允许创建自定义数据类型，我们后面会继续讲到

(6)动态语言：

变量本身类型不固定的语言称之为动态语言，与之对应的是静态语言。

静态语言在定义变量时必须指定变量类型，如果赋值的时候类型不匹配，就会报错。例如Java是静态语言。



## 条件判断和循环（简洁）



```markdown
Python开发者的哲学是“用一种方法,最好是只有一种方法来做一件事”
对于可以用while完成的，开发者认为就没有必要在做do和until了，要不容易让初学者弄混。
包括switch，开发者认为使用if-elif-else就可以完成的就不要switch了。
```

python中有：

- if-else
- if-elif-else
- while
- for
- 其他的都没有

跳出循环：

- break
- continue


---



## list和tuple（有序，类型随意）

list是一种**有序**的集合，可以随时添加和删除其中的元素。list是数学意义上的有序集合，也就是说，list中的元素是按照顺序排列的。

由于Python是**动态语言**，所以list中包含的元素并不要求都必须是同一种数据类型，我们完全可以在list中包含各种数据：

`L = ['Michael', 100, True]`

一个元素也没有的list，就是空list：

`empty_list = []`

### ·list添加新元素/删除元素

索引从 0 开始，也就是说，第一个元素的索引是0，第二个元素的索引是1，以此类推。
使用索引时，**千万注意不要越界**。

-1表示倒数第一，-2表示倒数第二，以此类推。注意也不能越界。



- `.append()`直接添加到尾部
- `.insert(0)`添加到某个索引位置，原位置以及之后的元素自动后移一位
- `.pop()` `.pop(0)` 删除尾部or某索引处元素

### ·list和tuple关系

- tuple是另一种有序的列表，中文翻译为“ 元组 ”。tuple 和 list **非常类似**，但是，tuple**一旦创建完毕，就不能修改了**(!!!)。没有 `.append()`方法，也没有`.insert()`和`.pop()`方法。（但是只是指向不变，如tuple中有list，list还是能变的，如 `t = ('a', 'b', ['A', 'B'])`
- `tuple(list_a)`即可得到`list_a`所对应的tuple，如`tuple(range(5))`
  所以tuple和list很大程度上是相似的，元素无需是同一类型。也都可以用`for a in x:`来遍历
- 当创建的tuple只有一个元素时，记得加上逗号如`t=(1,)`或`t=('abc',)`以防歧义


---



## dict和set

### ·dict是存储**key: value对**的集合

花括号 `{} `表示这是一个dict，然后按照`key: value`, 写出来即可。最后一个 key: value 的逗号可以省略。

由于dict也是集合，len() 函数可以计算任意集合的大小，所以可以`len(d)` （list, tuple也可以)

可以简单地使用 d[key] 的形式来查找对应的 value，这和 list 很像，不同之处是，**list 必须使用索引返回对应的元素，而dict使用key**。

----

但是key有可能不存在。如果key不存在，会直接报错：KeyError。

要避免 KeyError 发生，有两个办法：

**一是先判断一下 key 是否存在，用 in 操作符：**

```python
if 'Paul' in d:
    print d['Paul']
```

如果 'Paul' 不存在，if语句判断为False，自然不会执行 `print d['Paul'] `，从而避免了错误。

**二是使用dict本身提供的一个 get 方法，在Key不存在的时候，返回None：**

```python
>>> print d.get('Bart')
59
>>> print d.get('Paul')
None
```

---

### ·dict的特点

- dict的第一个特点是**查找速度快**，无论dict有10个元素还是10万个元素，查找速度都一样。而list的查找速度随着元素增加而逐渐下降。

  不过dict的查找速度快不是没有代价的，**dict的缺点是占用内存大，还会浪费很多内容**，list正好相反，占用内存小，但是查找速度慢。

  由于dict是按 key 查找，所以，在一个dict中，key**不能重复**。

- dict的第二个特点就是存储的key-value序对是**没有顺序的！**这和list不一样：

  ```
  d = {
      'Adam': 95,
      'Lisa': 85,
      'Bart': 59
  }
  ```

  当我们试图打印这个dict时：

  ```
  >>> print d
  {'Lisa': 85, 'Adam': 95, 'Bart': 59}
  ```

  打印的顺序不一定是我们创建时的顺序，而且，不同的机器打印的顺序都可能不同，这说明dict内部是**无序**的，不能用dict存储有序的集合。

- dict的第三个特点是作为 key 的元素**必须不可变**，Python的基本类型如字符串、整数、浮点数都是不可变的，都可以作为 key。但是list是可变的，就不能作为 key。



### ·更新、遍历dict

---

我们可以随时往dict中添加新的 key-value。可以**直接使用赋值语句添加**。

要把新同学'Paul'的成绩 72 加进去，用赋值语句：

```python
>>> d['Paul'] = 72
```

如果 key 已经存在，则赋值会用新的 value 替换掉原来的 value。

---

直接使用for循环遍历 dict 的 key：

```
for key in d:
    print key
```

同时打印出key**和**value:

```python
for (key, value) in d.items():    
    print "%s: %s" % (key, value)
```





### ·set（类似list，和dict的key）

我们只想要 dict 的 key，不关心 key 对应的 value。想要一组元素，目的就是保证这个集合的元素不会重复。

**set 持有一系列元素，这一点和 list 很像，但是set的元素没有重复，而且是无序的，这点和 dict 的 key很像。**

---

创建 set 的方式是调用 set() 并传入一个 list，list的元素将作为set的元素：

```python
s = set(['A', 'B', 'C'])
```

可以查看 set 的内容：

```
>>> print s
set(['A', 'C', 'B'])
```

请注意，上述打印的形式类似 list， 但它不是 list，仔细看还可以发现，打印的顺序和原始 list 的顺序有可能是不同的，因为set内部存储的元素是**无序**的。



### ·访问set（包括更新、遍历元素）

由于**set存储的是无序集合**，所以我们没法通过索引来访问。

【访问 set中的某个元素实际上就是判断一个元素是否在set中。】

```python
s = set(['Adam', 'Lisa', 'Bart', 'Paul'])
```

我们可以用 in 操作符判断：Bart是该班的同学吗？

```
>>>'Bart' in s
True
```

Bill是该班的同学吗？

```
>>> 'Bill' in s
False
```

遍历set还是老套路。for in

更新/删除：用`add()`可以直接添加，而`remove()`前需要判断。

### ·set的特点（类似dict）

- 查找快
- 无序
- 元素不可变




---

## 函数

### 调用函数

Python内置了很多有用的函数，我们可以直接调用。

要调用一个函数，需要知道**函数**的**名称**和**参数**，比如求绝对值的函数 `abs()`，它接收一个参数。比如` int()`函数可以把其他数据类型转换为整数；`str()`函数把其他类型转换成 str。比如`sum()`函数可以求list的和。

### 编写函数

- 在Python中，定义一个函数要使用**def **语句，依次写出**函数名、括号、括号中的参数和冒号:**，然后，在缩进块中编写函数体，函数的返回值用 **return**语句返回。

  如果没有return语句，函数执行完毕后也会返回结果，只是结果为 None。return None可以简写为return。

- 函数可以返回多个值。比如在游戏中经常需要从一个点移动到另一个点，给出坐标、位移和角度，就可以计算出新的坐标：**Python的函数**返回多值其实就是**返回一个tuple**，但写起来更方便。

  ```python
  import math
  def move(x, y, step, angle):
      new_x = x + step * math.cos(angle)
      new_y = y + step * math.sin(angle)
      return new_x,new_y

  #若打印出来结果
  >>> r = move(100, 100, 60, math.pi / 6)
  >>> print r
  (151.96152422706632, 70.0)   #一个tuple
  ```


- 定义函数的时候，还可以有默认参数。

  ```python
  >>> int('123')
  123
  >>> int('123', 8)    #8代表八进制
  83
  ```

  由于函数的参数按从左到右的顺序匹配，所以**默认参数只能定义在必需参数的后面：**

  ​

- 可变参数（**个数**不确定）

  ```python
  def fn(*args):
      print args
  ```

  可变参数的名字前面有个*号，我们可以传入0个、1个或多个参数给可变参数：

  ```python
  >>> fn()
  ()
  >>> fn('a')
  ('a',)
  >>> fn('a', 'b')
  ('a', 'b')
  >>> fn('a', 'b', 'c')
  ('a', 'b', 'c')
  ```

  可变参数也不是很神秘，Python解释器会把传入的一组参数组装成一个tuple传递给可变参数，因此，在函数内部，直接把变量 args 看成一个**tuple**就好了。

---



## 切片

### list和tuple

```python
>>> L[0:3]   #从0开始取三个元素(取到索引为2)
>>> L[:3]
['Adam', 'Lisa', 'Bart']
```

也可以从索引1开始，取出两个元素出来：

```python
>>> L[1:3]
['Lisa', 'Bart']
```

只用一个**:**，表示从头到尾：

```python
>>> L[:]
['Adam', 'Lisa', 'Bart', 'Paul']
```

因此，L[:]实际上复制出了一个新list。

切片操作还可以指定第三个参数：

```python
>>> L[::2]
['Adam', 'Bart']
```

**第三个参数**(区别matlab, 第二个参数)表示每N个取一个，上面的 L[::2] 会每两个元素取出一个来，也就是隔一个取一个。

python也支持倒数切片，试试：

```python
>>> L = ['Adam', 'Lisa', 'Bart', 'Paul']

>>> L[-2:]    #左边的取上，右边的不取上
['Bart', 'Paul']

>>> L[:-2]    #左边的取上，右边的不取上
['Adam', 'Lisa']
```

切片可以嵌套，如：

`print L[4::5][-10:] ` 先获得5的倍数，再取后10个。

---

### 字符串

字符串 'xxx'和 Unicode字符串 u'xxx'也可以看成是一种list，每个元素就是一个字符。

```python
>>> 'ABCDEFG'[:3]
'ABC'
>>> 'ABCDEFG'[-3:]
'EFG'
>>> 'ABCDEFG'[::2]
'ACEG'
```



---



## 迭代

**遍历**list或者tuple等等的操作，我们称为迭代(iteration)。

在Python中，**迭代是通过 for ... in 来完成的**，而很多语言比如C或者Java，迭代list是通过下标完成的。

**Python 的 for循环不仅可以用在list或tuple上，还可以作用在其他任何可迭代对象上。**

因此，迭代操作就是对于一个**集合**，无论该集合是有序还是无序，我们用 for 循环总是可以依次取出集合的每一个元素。

```markdown
注意: 集合是指包含一组元素的数据结构，我们已经介绍的包括：
1. 有序集合：list，tuple，str和unicode；
2. 无序集合：set
3. 无序集合并且具有 key-value 对：dict
```

而迭代是一个动词，它指的是一种操作，在Python中，就是 for 循环。

---

### 索引迭代

Python中，**迭代永远是取出元素本身，而非元素的索引。**

如果我们确实想在 for 循环中拿到索引，怎么办？方法是使用 **enumerate() 函数**：

```python
>>> L = ['Adam', 'Lisa', 'Bart', 'Paul']
>>> for index, name in enumerate(L):
...     print index, '-', name
... 
0 - Adam
1 - Lisa
2 - Bart
3 - Paul
```

实际上，enumerate() 函数把：

```python
['Adam', 'Lisa', 'Bart', 'Paul']
```

变成了类似：

```python
[(0, 'Adam'), (1, 'Lisa'), (2, 'Bart'), (3, 'Paul')]
```

因此，迭代的每一个元素实际上是一个tuple。

可见，索引迭代也不是真的按索引访问，而是由 enumerate(L) 函数自动把每个元素变成 (index, element) 这样的tuple，再迭代，就同时获得了索引和元素本身。

---



### 迭代dict（key和value）

我们已经了解了**dict对象**本身就是可**迭代对象**，用 for 循环直接迭代 dict，可以每次拿到dict的一个key。

dict 对象有一个 **values() 方法**，这个方法把dict转换成一个包含所有value的list，这样，我们迭代的就是 dict的每一个 value：

```python
d = { 'Adam': 95, 'Lisa': 85, 'Bart': 59 }
print d.values()
# [85, 95, 59]
for v in d.values():
    print v
# 85
# 95
# 59
```

如果仔细阅读Python的文档，还可以发现，dict除了**values()**方法外，还有一个**itervalues()**方法，用**itervalues()** 方法替代 **values()** 方法，迭代效果完全一样：

```python
d = { 'Adam': 95, 'Lisa': 85, 'Bart': 59 }
print d.itervalues()
# <dictionary-valueiterator object at 0x106adbb50>
for v in d.itervalues():
    print v
# 85
# 95
# 59
```

**那这两个方法有何不同之处呢？**※

1. **values()** 方法实际上把一个 dict 转换成了包含 value 的list。


2. 【但是 **itervalues()** 方法不会转换，它会在迭代过程中**依次**从 dict 中取出 value，所以 itervalues() 方法比 values() 方法节省了生成 list 所需的内存。】
3. 打印 itervalues() 发现它返回一个 <dictionary-valueiterator> 对象，这说明在Python中，**for 循环可作用的迭代对象远不止 list，tuple，str，unicode，dict等**，任何可迭代对象都可以作用于for循环，而内部如何迭代我们通常并不用关心。

**如果一个对象说自己可迭代，那我们就直接用 for 循环去迭代它，可见，迭代是一种抽象的数据操作，它不对迭代对象内部的数据有任何要求。**

---

同时迭代 key和value：`for (key, value) in d.items()`

我们看看 dict 对象的 **items()** 方法返回的值：

```python
>>> d = { 'Adam': 95, 'Lisa': 85, 'Bart': 59 }
>>> print d.items()
[('Lisa', 85), ('Adam', 95), ('Bart', 59)]
```

可以看到，items() 方法把dict对象转换成了包含tuple的list，我们对这个list进行迭代，可以同时获得key和value：

```python
>>> for key, value in d.items():
...     print key, ':', value
... 
Lisa : 85
Adam : 95
Bart : 59
```

和 values() 有一个 itervalues() 类似， **items() **也有一个对应的 **iteritems()**，iteritems() 不把dict转换成list，而是在迭代过程中不断给出 tuple，所以， iteritems() 不占用额外的内存。





## 列表(list)生成式



要生成list [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]，我们可以用range(1, 11)：

```python
>>> range(1, 11)
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

生成更复杂的list，用列表生成式

```python
#Python特有的列表生成式。利用列表生成式，可以以非常简洁的代码生成 list。
>>>[x**2 for x in range(10)]
[0,1,4,9,16,25,36,49,64,81]
```

`range(1, 100, 2) `可以生成`list [1, 3, 5, 7, 9,...]`

---

### 条件过滤

列表生成式的 **for 循环后面还可以加上 if 判断**。例如：

```python
>>> [x * x for x in range(1, 11)]
[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```

如果我们只想要偶数的平方，不改动 range()的情况下，可以加上 if 来筛选：

```python
>>> [x * x for x in range(1, 11) if x % 2 == 0]
[4, 16, 36, 64, 100]
```

---

### 多层表达式

for循环可以嵌套，因此，在列表生成式中，也可以用多层 for 循环来生成列表。

对于字符串 'ABC' 和 '123'，可以使用两层循环，生成全排列：

```python
>>> [m + n for m in 'ABC' for n in '123']
['A1', 'A2', 'A3', 'B1', 'B2', 'B3', 'C1', 'C2', 'C3']
```

翻译成**循环嵌套**代码就像下面这样：

```python
L = []
for m in 'ABC':
    for n in '123':
        L.append(m + n)
```





# 2.Python less basic

## 函数式编程



1.function，函数，已经熟悉

2.函数式是functional，指一种编程范式

特点：

- 把计算视为函数而不是指令
- 纯函数式编程：不需要变量，没有副作用，测试简单（但是python不是纯函数式编程，允许有变量）
- 支持高阶函数（函数可以作为变量传入），代码简洁
- python支持闭包，有了闭包就能返回函数
- python支持有限度的匿名函数



## 高阶函数

变量可以指向一个函数：

```python
>>> abs(-10)
10
>>> f=abs
>>> f(-20)
20
```

函数名就是指向函数的变量：

```python
>>> abs=len
>>> abs(-10)#会报错！！ abs[-1,-2,-3]=3才可以
```



简单的高阶函数例子：

```python
def add(x, y, f):
    return f(x) + f(y)
```

如果传入abs作为参数f的值：

```python
add(-5, 9, abs)
```

根据函数的定义，函数执行的代码实际上是：

```python
abs(-5) + abs(9)
```

由于参数 x, y 和 f 都可以任意传入，如果 f 传入其他函数，就可以得到不同的返回值。

---

一些内置高阶函数：

### map()函数

**map()**是 Python 内置的高阶函数，它接收一个**函数 f** 和一个 **list**，并通过把函数 f 依次作用在 list 的每个元素上，得到一个新的 list 并返回。

例如，对于list [1, 2, 3, 4, 5, 6, 7, 8, 9]

如果希望把list的每个元素都作平方，就可以用map()函数：

我们只需要传入函数f(x)=x*x，就可以利用map()函数完成这个计算：

```python
def f(x):
    return x*x    #return重要
print map(f, [1, 2, 3, 4, 5, 6, 7, 8, 9])
```

**输出结果：**

```
[1, 4, 9, 10, 25, 36, 49, 64, 81]
```

**注意：**map()函数不改变原有的 list，而是返回一个新的 list。



### reduce()

reduce()函数接收的参数和 map()类似，**一个函数 f，一个list**，但行为和 map()不同，reduce()传入的函数 f 必须接收两个参数，reduce()对list的每个元素反复调用函数f，并返回最终结果值。

例如，编写一个f函数，接收x和y，返回x和y的和：

```python
def f(x, y):
    return x + y
```

调用 **reduce(f, [1, 3, 5, 7, 9])**时，reduce函数将做如下计算：

```
先计算头两个元素：f(1, 3)，结果为4；
再把结果和第3个元素计算：f(4, 5)，结果为9；
再把结果和第4个元素计算：f(9, 7)，结果为16；
再把结果和第5个元素计算：f(16, 9)，结果为25；
由于没有更多的元素了，计算结束，返回结果25。
```

上述计算实际上是对 list 的所有元素求和。虽然Python内置了求和函数sum()，但是，利用reduce()求和也很简单。

**reduce()还可以接收第3个可选参数，作为计算的初始值。**如果把初始值设为100，计算：

```python
reduce(f, [1, 3, 5, 7, 9], 100)
```

结果将变为125，因为第一轮计算是：

计算初始值和第一个元素：**f(100, 1)**，结果为**101**。



python内置了求和函数sum()，但没有求积函数，利用reduce()函数求积：

```python
def prod(x, y):
    return x*y

print reduce(prod, [2, 4, 5, 7, 12])
```





### filter()

filter()函数接收一个**函数 f **和一个**list**，这个函数 f 的作用是对每个元素进行判断，返回 True或 False，**filter()根据判断结果自动过滤掉不符合条件的元素，返回由符合条件元素组成的新list。**

例如，要从一个list [1, 4, 6, 7, 9, 12, 17]中删除偶数，保留奇数，首先，要编写一个判断奇数的函数：

```python
def is_odd(x):
    return x % 2 == 1
```

然后，利用filter()过滤掉偶数：

```python
filter(is_odd, [1, 4, 6, 7, 9, 12, 17])
```

**结果：**[1, 7, 9, 17]

利用filter()，可以完成很多有用的功能，例如，删除 None 或者空字符串：

```python
def is_not_empty(s):
    return s and len(s.strip()) > 0
filter(is_not_empty, ['test', None, '', 'str', '  ', 'END'])
```

**结果：**['test', 'str', 'END']

**注意:** s.strip(rm) 删除 s 字符串中**开头、结尾**处的 rm 序列的字符。

当rm为空时，默认删除空白符（包括'\n', '\r', '\t', ' ')，如下：

```python
a = '     123'
a.strip()
```

**结果：** '123'

```python
a='\t\t123\r\n'
a.strip()
```

**结果：**'123'

当rm不为空（注意只删开头或结尾的，不能跳着删中间）：

```python
>>> a = '123abc'
>>> a.strip('12')
'3abc'
>>> a.strip('21')
'3abc'
>>> a.strip('213')
'abc'
```





### sorted()  自定义排序函数

Python内置的 **sorted()**函数可对list进行排序：

```python
>>>sorted([36, 5, 12, 9, 21])
[5, 9, 12, 21, 36]
```

但 **sorted()**也是一个高阶函数，它可以接收一个比较函数来实现自定义排序，比较函数的定义是，传入两个待比较的元素 x, y，**如果 x 应该排在 y 的前面，返回 -1，如果 x 应该排在 y 的后面，返回 1。如果 x 和 y 相等，返回 0。**

因此，如果我们要实现倒序排序，只需要编写一个reversed_cmp函数：

```python
def reversed_cmp(x, y):
    if x > y:
        return -1
    if x < y:
        return 1
    return 0
```

这样，调用 sorted() 并传入 reversed_cmp 就可以实现倒序排序：

```python
>>> sorted([36, 5, 12, 9, 21], reversed_cmp)
[36, 21, 12, 9, 5]
```

sorted()也可以对字符串进行排序，字符串默认按照ASCII大小来比较：

```python
>>> sorted(['bob', 'about', 'Zoo', 'Credit'])
['Credit', 'Zoo', 'about', 'bob']
```

'Zoo'排在'about'之前是因为'Z'的ASCII码比'a'小。

`sorted`(*iterable*[, *cmp*[, *key*[, *reverse*]]])

Return a new sorted list from the items in *iterable*.

The optional arguments *cmp*, *key*, and *reverse* have the same meaning as those for the `list.sort()` method (described in section [Mutable Sequence Types](https://docs.python.org/2/library/stdtypes.html#typesseq-mutable)).

*cmp* specifies a custom comparison function of two arguments (iterable elements) which should return a negative, zero or positive number depending on whether the first argument is considered smaller than, equal to, or larger than the second argument: `cmp=lambdax,y: cmp(x.lower(), y.lower())`. The default value is `None`.

*key* specifies a function of one argument that is used to extract a comparison key from each list element: `key=str.lower`. The default value is `None` (compare the elements directly).

*reverse* is a boolean value. If set to `True`, then the list elements are sorted as if each comparison were reversed.

In general, the *key* and *reverse* conversion processes are much faster than specifying an equivalent *cmp* function. This is because *cmp* is called multiple times for each list element while *key* and *reverse* touch each element only once. Use [`functools.cmp_to_key()`](https://docs.python.org/2/library/functools.html#functools.cmp_to_key) to convert an old-style *cmp* function to a *key* function.

The built-in [`sorted()`](https://docs.python.org/2/library/functions.html?highlight=sorted#sorted) function is guaranteed to be stable. A sort is stable if it guarantees not to change the relative order of elements that compare equal — this is helpful for sorting in multiple passes (for example, sort by department, then by salary grade).

For sorting examples and a brief sorting tutorial, see [Sorting HOW TO](https://docs.python.org/2/howto/sorting.html#sortinghowto).

New in version 2.4.

### python中 返回一个函数

Python的函数不但可以返回int、str、list、dict等数据类型，还可以返回函数！

例如，定义一个函数 f()，我们让它返回一个函数 g，可以这样写：

```python
def f():
    print 'call f()...'
    # 定义函数g:
    def g():
        print 'call g()...'
    # 返回函数g:
    return g
```

仔细观察上面的函数定义，我们在函数 f 内部又定义了一个函数 g。由于函数 g 也是一个对象，函数名 g 就是指向函数 g 的变量，所以，最外层函数 f 可以返回变量 g，也就是函数 g 本身。

调用函数 f，我们会得到 f 返回的一个函数：

```python
>>> x = f()   # 调用f()
call f()...
>>> x   # 变量x是f()返回的函数：
<function g at 0x1037bf320>
>>> x()   # x指向函数，因此可以调用
call g()...   # 调用x()就是执行g()函数定义的代码
```

请注意区分返回**函数**和返回**值**：

```python
def myabs():
    return abs   # 返回函数
def myabs2(x):
    return abs(x)   # 返回函数调用的结果，返回值是一个数值
```

返回函数可以把一些计算**延迟执行**。例如，如果定义一个普通的求和函数：

```python
def calc_sum(lst):
    return sum(lst)
```

调用calc_sum()函数时，将立刻计算并得到结果：

```python
>>> calc_sum([1, 2, 3, 4])
10
```

但是，如果返回一个函数，就可以“延迟计算”：

```python
def calc_sum(lst):
    def lazy_sum():
        return sum(lst)
    return lazy_sum
```

\# 调用calc_sum()并没有计算出结果，而是返回函数:

```python
>>> f = calc_sum([1, 2, 3, 4])
>>> f
<function lazy_sum at 0x1037bfaa0>
```

\# 对返回的函数进行调用时，才计算出结果:

```python
>>> f()
10
```

由于可以返回函数，我们在后续代码里就可以决定到底要不要调用该函数。



### python中 闭包

在函数内部定义的函数和外部定义的函数是一样的，只是他们无法被外部访问。

将**g** 的定义移入函数 **f** 内部，防止其他代码调用 **g**：

```python
def f():
    print 'f()...'
    def g():
        print 'g()...'
    return g
```

但是，考察上一小节定义的 **calc_sum **函数：

```python
def calc_sum(lst):
    def lazy_sum():
        return sum(lst)
    return lazy_sum
```

**注意: **发现没法把 **lazy_sum** 移到 **calc_sum** 的外部，因为它引用了 **calc_sum** 的参数 **lst**。

像这种内层函数引用了外层函数的变量（参数也算变量），然后返回内层函数的情况，称为**闭包（Closure）**。

**闭包的特点**是返回的函数还引用了外层函数的局部变量，所以，要正确使用闭包，就要确保引用的局部变量在函数返回后不能变。举例如下：

```python
# 希望一次返回3个函数，分别计算1x1,2x2,3x3:
def count():
    fs = []
    for i in range(1, 4):
        def f():
             return i*i
        fs.append(f)
    return fs

f1, f2, f3 = count()
```

你可能认为调用f1()，f2()和f3()结果应该是1，4，9，但实际结果全部都是 9（请自己动手验证）。

原因就是当count()函数返回了3个函数时，这3个函数所引用的变量 i 的值已经变成了3。由于f1、f2、f3并没有被调用，所以，此时他们并未计算 i*i，当 f1 被调用时：

```python
>>> f1()
9     # 因为f1现在才计算i*i，但现在i的值已经变为3
```

因此，返回函数不要引用任何循环变量，或者后续会发生变化的变量。

修改方法：问题的产生是因为函数只在执行时才去获取外层参数i，若函数定义时可以获取到i，问题便可解决。而默认参数正好可以完成定义时获取i值且运行函数时无需参数输入的功能，所以在函数f()定义中改为`def f(m = i):`,函数f返回值改为`m*m`即可.



### python中 匿名函数

高阶函数可以接收函数做参数，有些时候，我们不需要显式地定义函数，直接传入匿名函数更方便。

在Python中，对匿名函数提供了有限支持。还是以map()函数为例，计算 f(x)=x*x 时，除了定义一个f(x)的函数外，还可以直接传入匿名函数：

```python
>>> map(lambda x: x * x, [1, 2, 3, 4, 5, 6, 7, 8, 9])
[1, 4, 9, 16, 25, 36, 49, 64, 81]
```

通过对比可以看出，匿名函数 `lambda x: x * x` 实际上就是：

```python
def f(x):
    return x * x
```

**关键字lambda 表示匿名函数，冒号前面的 x 表示函数参数。**

匿名函数有个限制，就是**只能有一个表达式**，**不写return**，返回值就是该表达式的结果。

使用匿名函数，可以不必定义函数名，直接创建一个函数对象，很多时候可以简化代码：

```python
>>> sorted([1, 3, 9, 5, 0], lambda x,y: -cmp(x,y))
[9, 5, 3, 1, 0]
```

返回函数的时候，也可以返回匿名函数：

```python
>>> myabs = lambda x: -x if x < 0 else x 
>>> myabs(-1)
1
>>> myabs(1)
1
```



### python中 decorator（待完善）

假设我们定义了一个函数，想在运行时动态增加功能，又不想改动函数本身的代码。







## 模块

当代码越来越多时用到。模块和包的概念：



- 将所有代码放在同一个py文件中，难以维护。将代码拆分放到多个py文件中，同一名字的变量（包括函数）不会相互影响。而模块的名字就py文件的文件名。

  引用其他模块：

  ```python
  # test.py    #自身模块名test
  import math    #引用math模块
  print math.pow(2,10)    #调用math模块的函数
  ```

- 模块名也会冲突（比如不同人都编写了util.py），解决模块名冲突方案：放入不同的包中如p1/和p2/，它们的完整模块名叫做p1.util 和p2.util。引用方法：

  ```python
  #test.py
  import p1.util
  p1.util.f(2,10)    #写完整名
  ```


- 在文件系统中，包就是文件夹，模块就是一个py文件。如何区分包和普通目录？

  包下面一定有一个`__init__.py`文件，即使它是一个空文件。

  ​



### 导入模块

要使用一个模块，我们必须首先导入该模块。Python使用import语句导入一个模块。例如，导入系统自带的模块 math：

```python
import math
```

你可以认为math就是一个指向已导入模块的变量，通过该变量，我们可以访问math模块中所定义的所有公开的函数、变量和类：

```python
>>> math.pow(2, 0.5) # pow是函数
1.4142135623730951

>>> math.pi # pi是变量
3.141592653589793
```

如果我们只希望导入用到的math模块的某几个函数，而不是所有函数，可以用下面的语句：

```python
from math import pow, sin, log
```

这样，可以直接引用 pow, sin, log 这3个函数，但math的其他函数没有导入进来：

```python
>>> pow(2, 10)
1024.0
>>> sin(3.14)
0.0015926529164868282
```

如果遇到名字冲突怎么办？比如math模块有一个log函数，logging模块也有一个log函数，如果同时使用，如何解决名字冲突？

如果使用import导入模块名，由于必须通过模块名引用函数名，因此不存在冲突：

```python
import math, logging
print math.log(10)   # 调用的是math的log函数
logging.log(10, 'something')   # 调用的是logging的log函数
```

如果使用**from...import 导入 log 函数，势必引起冲突**。这时，**可以给函数起个“别名”来避免冲突**：

```python
from math import log
from logging import log as logger   # logging的log现在变成了logger
print log(10)   # 调用的是math的log
logger(10, 'import from logging')   # 调用的是logging的log
```



### 动态导入模块

如果导入的模块不存在，Python解释器会报 ImportError 错误：

```python
>>> import something
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named something
```

有的时候，两个不同的模块提供了相同的功能，比如 **StringIO **和 **cStringIO **都提供了StringIO这个功能。

这是因为Python是动态语言，解释执行，因此Python代码运行速度慢。

如果要提高Python代码的运行速度，最简单的方法是把某些关键函数用 C 语言重写，这样就能大大提高执行速度。

同样的功能，StringIO 是纯Python代码编写的，而 cStringIO 部分函数是 C 写的，因此 cStringIO 运行速度更快。

利用ImportError错误，我们经常在Python中动态导入模块：

```python
try:
    from cStringIO import StringIO
except ImportError:
    from StringIO import StringIO
```

上述代码先尝试从cStringIO导入，如果失败了（比如cStringIO没有被安装），再尝试从StringIO导入。这样，如果cStringIO模块存在，则我们将获得更快的运行速度，如果cStringIO不存在，则顶多代码运行速度会变慢，但不会影响代码的正常执行。

**try **的作用是捕获错误，并在捕获到**指定错误**时执行 **except **语句。



### 使用`__future__`

Python的新版本会引入新的功能，但是，实际上这些功能在上一个老版本中就已经存在了。要“试用”某一新的特性，就可以通过导入__future__模块的某些功能来实现。

例如，Python 2.7的整数除法运算结果仍是整数：

```python
>>> 10 / 3
3
```

但是，Python 3.x已经改进了整数的除法运算，“**/**”除将得到浮点数，“**//**”除才仍是整数：

```python
>>> 10 / 3
3.3333333333333335
>>> 10 // 3
3
```

要在Python 2.7中引入3.x的除法规则，导入**__future__**的**division**：

```python
>>> from __future__ import division
>>> print 10 / 3
3.3333333333333335
```

当新版本的一个特性与旧版本不兼容时，该特性将会在旧版本中添加到**__future__**中，以便旧的代码能在旧版本中测试新特性。



### 安装第三方模块

python提供的模块管理工具

- easy_install

- pip (推荐，已内置到python 2.7.9)

  `>>> pip install`





## python之面向对象编程



### 类和实例

**定义类并创建实例**：

```python
class Person(object):     #pass能够创建一个最简单的类
    pass
xiaoming = Person()
xiaohong = Person()

>>> print xiaoming
<__main__.Person object at 0x7f98ec537850>     #__main__意思是，调用模块本身，即本py文件
```

---

**创建实例属性**：

给**xiaoming**这个实例加上**name、gender**和**birth**属性：

```python
xiaoming = Person()
xiaoming.name = 'Xiao Ming'
xiaoming.gender = 'Male'
xiaoming.birth = '1990-1-1'
```

给**xiaohong**加上的属性不一定要和**xiaoming**相同：

```python
xiaohong = Person()
xiaohong.name = 'Xiao Hong'
xiaohong.school = 'No. 1 High School'
xiaohong.grade = 2
```

实例的属性可以像普通变量一样进行操作：

```python
xiaohong.grade = xiaohong.grade + 1
```

---

**初始化实例属性：**

之前，我们可以自由地给一个实例绑定各种属性，但很多情况下一种类型的实例应该拥有相同名字的属性。

在定义 Person 类时，可以为Person类添加一个特殊的**__init__()**方法，当创建实例时，**__init__()**方法被自动调用，我们就能在此为每个实例都统一加上以下属性：

```python
class Person(object):
    def __init__(self, name, gender, birth):
        self.name = name
        self.gender = gender
        self.birth = birth
```

**__init__() **方法的第一个参数必须是 **self**（也可以用别的名字，但建议使用习惯用法），后续参数则可以自由指定，和定义函数没有任何区别。

相应地，创建实例时，就必须要提供除 **self **以外的参数：

```python
xiaoming = Person('Xiao Ming', 'Male', '1991-1-1')
xiaohong = Person('Xiao Hong', 'Female', '1992-2-2')
```

有了**__init__()**方法，每个Person实例在创建时，都会有 **name、gender **和 **birth **这3个属性，并且，被赋予不同的属性值，访问属性使用.操作符：

```python
print xiaoming.name
# 输出 'Xiao Ming'
print xiaohong.birth
# 输出 '1992-2-2'
```



参数中除了这些固定的属性，还可以接受任意关键字参数：

```python
class Person(object):
    def __init__(self, name, gender, birth,**kvargs):
        self.name = name
        self.gender = gender
        self.birth = birth
        for k,v in kvargs.items():
            setattr(self,k,v)

xiaoming = Person('Xiao Ming', 'Male', '1990-1-1', job='Student')

print xiaoming.name
print xiaoming.job
```

解释器内部会将`**kvargs`拆分成对应的dict.

`setattr()`方法接受3个参数：`setattr(对象，属性，属性的值)`

`setattr(self,k,v)`相当于`self.k = v`

---

**访问限制：**

我们可以给一个实例绑定很多属性，如果有些属性不希望被外部访问到怎么办？

Python对属性权限的控制是通过属性名来实现的，如果一个属性由双下划线开头(__)，该属性就无法被外部访问。看例子：

```python
class Person(object):
    def __init__(self, name):
        self.name = name
        self._title = 'Mr'
        self.__job = 'Student'
p = Person('Bob')
print p.name
# => Bob
print p._title
# => Mr
print p.__job
# => Error
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: 'Person' object has no attribute '__job'
```

可见，只有以双下划线开头的"**__job**"不能直接被外部访问。

但是，如果一个属性以"__xxx__"的形式定义，那它又可以被外部访问了，以"__xxx__"定义的属性在Python的类中被称为特殊属性，有很多预定义的特殊属性可以使用，通常我们不要把普通属性用"**__xxx__**"定义。

以单下划线开头的属性"_xxx"虽然也可以被外部访问，但是，按照习惯，他们不应该被外部访问。

---

**创建类属性**：

类是模板，而实例则是根据类创建的对象。

绑定在一个实例上的属性不会影响其他实例，但是，类本身也是一个对象，如果在类上绑定一个属性，则所有实例都可以访问类的属性，并且，所有实例访问的类属性都是同一个！也就是说，实例属性每个实例各自拥有，互相独立，而类属性有且只有一份。

定义类属性可以直接在 **class **中定义：

```python
class Person(object):
    address = 'Earth'
    def __init__(self, name):
        #Person.address = ..   访问类属性，不管在哪，一定需要通过"类名.属性"这种方式(访问方式其中的一种)
        self.name = name
```

因为类属性是直接绑定在类上的，所以，访问类属性不需要创建实例，就可以直接访问：

```python
print Person.address
# => Earth
```

对一个实例调用类的属性也是可以访问的，所有实例都可以访问到它所属的类的属性：

```python
p1 = Person('Bob')
p2 = Person('Alice')
print p1.address
# => Earth
print p2.address
# => Earth
```

由于Python是动态语言，类属性也是可以动态添加和修改的：

```python
Person.address = 'China'
print p1.address
# => 'China'
print p2.address
# => 'China'
```

因为类属性只有一份，所以，当**Person**类的**address**改变时，所有实例访问到的类属性都改变了。

---

**类属性和实例属性名字冲突怎么办：**

当实例属性和类属性重名时，**实例属性优先级高**，它将屏蔽掉对类属性的访问。千万不要在实例上修改类属性，它实际上并没有修改类属性，而是给实例绑定了一个实例属性。



---

定义实例**方法**：

一个实例的私有属性就是以__开头的属性，无法被外部访问，那这些属性定义有什么用？

虽然私有属性无法从外部访问，但是，从类的内部是可以访问的。除了可以定义实例的属性外，还可以定义实例的方法。

**实例的方法就是在类中定义的函数**，它的第一个参数永远是 self，指向调用该方法的实例本身，其他参数和一个普通函数是完全一样的：

```python
class Person(object):

    def __init__(self, name):
        self.__name = name

    def get_name(self):
        return self.__name
```

**get_name(self) **就是一个实例方法，它的第一个参数是self。_**_init__(self, name)**其实也可看做是一个特殊的实例方法。

调用实例方法必须在实例上调用：

```python
p1 = Person('Bob')
print p1.get_name()  # self不需要显式传入
# => Bob
```

**在实例方法内部，可以访问所有实例属性**，这样，如果外部需要访问私有属性，可以通过方法调用获得，这种数据封装的形式除了能保护内部数据一致性外，还可以简化外部调用的难度。

---

**方法也是属性：**

我们在 **class** 中定义的实例方法其实也是属性，它实际上是一个函数对象：

```python
class Person(object):
    def __init__(self, name, score):
        self.name = name
        self.score = score
    def get_grade(self):
        return 'A'

p1 = Person('Bob', 90)
print p1.get_grade
# => <bound method Person.get_grade of <__main__.Person object at 0x109e58510>>
print p1.get_grade()
# => A
```

也就是说，**p1.get_grade **返回的是一个函数对象，但这个函数是一个绑定到实例的函数，**p1.get_grade() **才是方法调用。

因为方法也是一个属性，所以，它也可以动态地添加到**实例**上，只是需要用 `types.MethodType()` 把一个函数变为一个方法：

```python
import types
def fn_get_grade(self):
    if self.score >= 80:
        return 'A'
    if self.score >= 60:
        return 'B'
    return 'C'

class Person(object):
    def __init__(self, name, score):
        self.name = name
        self.score = score

p1 = Person('Bob', 90)
p1.get_grade = types.MethodType(fn_get_grade, p1, Person)
print p1.get_grade()
# => A
p2 = Person('Alice', 65)
print p2.get_grade()
# ERROR: AttributeError: 'Person' object has no attribute 'get_grade'
# 因为p2实例并没有绑定get_grade
```

给一个**实例**（区别类方法）动态添加方法并不常见，直接在class中定义要更直观。

---

**定义类方法**：

和属性类似，方法也分实例方法和类方法。

在**class**中定义的全部是实例方法，实例方法第一个参数 **self **是实例本身。

要在class中定义类方法，需要这么写：

```python
class Person(object):
    count = 0
    @classmethod
    def how_many(cls):
        return cls.count
    def __init__(self, name):
        self.name = name
        Person.count = Person.count + 1

print Person.how_many()
p1 = Person('Bob')
print Person.how_many()
```

通过标记一个 @classmethod，该方法将绑定到**Person**类上，而非类的实例。类方法的第一个参数将传入类本身，通常将参数名命名为**cls**，上面的 **cls.count **实际上相当于 **Person.count**。（后面该用Person.count时还是得用Person）

因为是在类上调用，而非实例上调用，因此类方法无法获得任何实例变量，只能获得类的引用。



---

### 类的继承

如：想要子类利用父类已有的属性和方法，使得新类不用重新编写，拥有父类的所有功能。只需要编写缺少的新功能。

若s是子类实例，那么s既是父类实例又是子类实例，反之不对。

```python
#已有父类Person类

class Student(Person):
    def __init__(self, name, gender, school, score):
        super(Student, self).__init_(name, gender) ##调用父类的构造方法，防止父类的属性在初始化出现其他错误
        self.school = school
        self.score = score
```

（`super().__init__()`这个方法应该是以父类的初始化方式初始化子类属性

如果子类的初始化方式和父类不同，应该是可以再重写方法来代替super进行初始化

但假若不写的话，会直接影响到继承父类属性的存在，就算接收了参数也没地方放，因为初始化无视了它）



**多重继承：**

**多重继承的目的**是从两种继承树中分别选择并继承出子类，以便**组合**功能使用。

```python
class C(A, B)
    def init(self, a, b):
        A.init(self, a)
        B.init(self, b)
```

（建议养成习惯，不要使用super()这个函数，即便是单继承，也使用上面的方式？？）



---



### 判断类型、获取对象信息

**判断类型：**

函数**`isistance()`**可以判断一个变量的类型，既可以用在Python内置的数据类型如**str、list、dict**，也可以用在我们自定义的类，它们本质上都是数据类型。

假设有如下的 **Person、Student** 和 **Teacher **的定义及继承关系如下：

```python
class Person(object):
    def __init__(self, name, gender):
        self.name = name
        self.gender = gender

class Student(Person):
    def __init__(self, name, gender, score):
        super(Student, self).__init__(name, gender)
        self.score = score

class Teacher(Person):
    def __init__(self, name, gender, course):
        super(Teacher, self).__init__(name, gender)
        self.course = course

p = Person('Tim', 'Male')
s = Student('Bob', 'Male', 88)
t = Teacher('Alice', 'Female', 'English')
```

当我们拿到变量 **p、s、t **时，可以使用 **isinstance** 判断类型：

```python
>>> isinstance(p, Person)
True    # p是Person类型
>>> isinstance(p, Student)
False   # p不是Student类型
>>> isinstance(p, Teacher)
False   # p不是Teacher类型
```

这说明在继承链上，一个父类的实例不能是子类类型，因为子类比父类多了一些属性和方法。

**我们再考察 s ：**

```python
>>> isinstance(s, Person)
True    # s是Person类型
>>> isinstance(s, Student)
True    # s是Student类型
>>> isinstance(s, Teacher)
False   # s不是Teacher类型
```

**s** 是Student类型，不是Teacher类型，这很容易理解。但是，**s** 也是Person类型，因为Student继承自Person，虽然它比Person多了一些属性和方法，但是，把**s** 看成Person的实例也是可以的。

这说明在一条继承链上，一个实例可以看成它本身的类型，也可以看成它父类的类型。





**获取对象信息**：

可以用 **type() **函数获取变量的类型，它返回一个 **Type **对象：

```python
>>> type(123)
<type 'int'>
>>> s = Student('Bob', 'Male', 88)
>>> type(s)
<class '__main__.Student'>
```

其次，可以用 **dir() **函数获取变量的所有属性：

```python
>>> dir(123)   # 整数也有很多属性...
['__abs__', '__add__', '__and__', '__class__', '__cmp__', ...]

>>> dir(s)
['__class__', '__delattr__', '__dict__', '__doc__', '__format__', '__getattribute__', '__hash__', '__init__', '__module__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', '__weakref__', 'gender', 'name', 'score', 'whoAmI']
```

对于实例变量，**dir()**返回所有实例属性，包括`__class__`这类有特殊意义的属性。注意到方法`whoAmI`也是 **s **的一个属性。

如何去掉**`__xxx__`**这类的特殊属性，只保留我们自己定义的属性？回顾一下**filter()**函数的用法。



**dir()**返回的属性是字符串list，如果已知一个属性名称，要获取或者设置对象的属性，就需要用 **getattr() **和**setattr( )**函数了：

```python
>>> getattr(s, 'name')  # 获取name属性
'Bob'

>>> setattr(s, 'name', 'Adam')  # 设置新的name属性

>>> s.name
'Adam'

>>> getattr(s, 'age')  # 获取age属性，但是属性不存在，报错：
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: 'Student' object has no attribute 'age'

>>> getattr(s, 'age', 20)  # 获取age属性，如果属性不存在，就返回默认值20：
20
```

【任务】：

对于Person类的定义：

```python
class Person(object):
    def __init__(self, name, gender):
        self.name = name
        self.gender = gender
```

希望除了 name和gender 外，可以提供任意额外的关键字参数，并绑定到实例，请修改 Person 的 __init__()定 义，完成该功能：

```python
class Person(object):
    def __init__(self, name, gender, **kw):
        self.name = name
        self.gender = gender
        for k,v in kw.items():
            setattr(self,str(k),v)

p = Person('Bob', 'Male', age=18, course='Python')
print p.age
print p.course
```





---

### 类的多态

类具有继承关系，并且子类类型可以向上转型看做父类类型，如果我们从 **Person **派生出 **Student**和**Teacher **，并都写了一个 **whoAmI() **方法：

```python
class Person(object):
    def __init__(self, name, gender):
        self.name = name
        self.gender = gender
    def whoAmI(self):
        return 'I am a Person, my name is %s' % self.name

class Student(Person):
    def __init__(self, name, gender, score):
        super(Student, self).__init__(name, gender)
        self.score = score
    def whoAmI(self):
        return 'I am a Student, my name is %s' % self.name

class Teacher(Person):
    def __init__(self, name, gender, course):
        super(Teacher, self).__init__(name, gender)
        self.course = course
    def whoAmI(self):
        return 'I am a Teacher, my name is %s' % self.name
```

在一个函数中，如果我们接收一个变量**x**，则无论该 **x **是**Person、Student**还是 **Teacher**，都可以正确打印出结果：

```python
def who_am_i(x):
    print x.whoAmI()

p = Person('Tim', 'Male')
s = Student('Bob', 'Male', 88)
t = Teacher('Alice', 'Female', 'English')

who_am_i(p)
who_am_i(s)
who_am_i(t)
```

运行结果：

```python
I am a Person, my name is Tim
I am a Student, my name is Bob
I am a Teacher, my name is Alice
```

这种行为称为多态。也就是说，方法调用将作用在 **x** 的实际类型上。**s** 是**Student**类型，它实际上拥有自己的**whoAmI()**方法以及从 Person继承的 whoAmI方法，但调用 **s.whoAmI()**总是**先查找它自身的定义，如果没有定义，则顺着继承链向上查找，直到在某个父类中找到为止。**

由于Python是动态语言，所以，传递给函数 **who_am_i(x)**的参数 **x** 不一定是 Person 或 Person 的子类型。任何数据类型的实例都可以，只要它**有一个whoAmI()**的方法即可：

如`json.load()`接收一个file like object

题目中很明显给出了`s=students()`，实例化一个s对象，而他属性里包含read方法

范例说的很清楚：python是动态语言，任何对象有read方法的，都可视为file like object。这正是符合json.load参数所需的类型

这是动态语言和静态语言（例如Java）最大的差别之一。动态语言调用实例方法，不检查类型，只要方法存在，参数正确，就可以调用。







# 零碎知识



## 1.杂

string型变量去掉最后一个字符`s.strip()`

list型变量-> `l.pop(0)`  `l.pop(-1)`      (sorted函数可将list变量排序`sorted(l)`)

string型变量通过符号split成list->`s.split(',')`  `s.split(' ')`等

可以把字符变成大写字母：

```python
>>> 'abc'.upper()
'ABC'
```



zip()函数可以把两个 list 变成一个 list：

```python
>>> zip([10, 20, 30], ['A', 'B', 'C'])
[(10, 'A'), (20, 'B'), (30, 'C')]
```





小trick:

```python
>>>print '-' * 10
----------
```









### Logic

- `and`
- `or`
- `not`
- `!= `(not equal)
- `==` (equal)
- `>=` (greater-than-equal)
- `<= `(less-than-equal)
- `True`
- `False`

### 各种Symbol

https://learnpythonthehardway.org/book/ex37.html

a**3是3次幂

## 2.文件读写

`f.seek(0)`有文件rewind的作用

