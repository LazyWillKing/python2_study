

# Python入门

[TOC]



## 一. 版本选择

1. python跨平台，各个平台的代码可以互相使用

   所以，可以先在win端写好代码，在linux平台使用

2. python现在分为2.7和3.3版本

   还没有选择好。两个版本的语言相差很大？？倾向于先学2.7版本

   但是，python3.3已经至少在2012年发布。学习过程中在考虑

   注：区分大小写

**代码缩进 tab 和 四个空格不是一个块**

## 二. 环境搭建

   2.7版本，官网下载后直接运行，默认的安装目录。

   windows会在path变量中寻找python.exe

   [win10配置path](http://www.cnblogs.com/dangeal/p/5455005.html) 在系统环境变量中加入python的地址

注：缩进 tab 和 四个空格 不属于一个块

## 三. 变量和数据类型

### 1. 数据类型

| 类型   | 表示              |
| ---- | --------------- |
| 整数   | 任意              |
| 小数   | 小数，科学计数         |
| 字符   | `' '` `'' ''`   |
| 布尔   | `true` ` false` |
| 空值   | `None`          |

### 2. print 输出

``` python
print 'hello,python'
print 'hello,','python'
print 'hello'+'python'		# 可以用加号连接
```

### 3. 注释

```python
# 注释的内容
# sublime3中的不支持中文，注释也不能是中文
```

### 4. 变量

Python是弱类型语言，声明变量时不需要指定类型，而且可以任意赋值。

```python
a = 123    # a是整数
print a
a = 'imooc'   # a变为字符串
print a 
```

### 5. 字符串

  `''` `""` 交替使用

```python
'Learn "Python"'
```

使用转译字符

```python
'Bob said \"I\'m OK\".'
```

```##
\'
\"
\n 表示换行
\t 表示一个制表符
\\ 表示 \ 字符本身
```

### 6.  raw字符串

字符串前缀 `r` 表示里面的字符不需要转译

```python
print r'\n'
# 输出为 \n
```

### 7. 多行字符串

用 ` ```...``` ` 表示

```python
​```line 1
line 2
line 3```
```

相当于

```python
'line 1\nline 2\nline3'
```

多行raw字符串

```python
r```line 1
line 2
line 3```
```

### 8. Unicode 字符串

在文本第一行添加 `# -*- coding: utf-8 -*-` ，使其支持中文

```python
# -*- coding: utf-8 -*-

print r'''静夜思
床前明月光，
疑是地上霜。
举头望明月，
低头思故乡''' 
```

python3默认支持中文

### 9. 整数和浮点数

计算遵循C++格式。

### 10. 布尔类型

**与运算**：只有两个布尔值都为 True 时，计算结果才为 True。

```
True and True   # ==> True
True and False   # ==> False
False and True   # ==> False
False and False   # ==> False
```

**或运算**：只要有一个布尔值为 True，计算结果就是 True。

```
True or True   # ==> True
True or False   # ==> True
False or True   # ==> True
False or False   # ==> False
```

**非运算**：把True变为False，或者把False变为True：

```
not True   # ==> False
not False   # ==> True
```



**注：**Python把`0`、`空字符串''`和`None`看成 False，其他数值和非空字符串都看成 True

**短路计算：**

1. 在计算` a and b `时，如果 a 是 False，则根据与运算法则，整个结果必定为 False，因此返回 a；如果 a 是 True，则整个计算结果必定取
2. 决与 b，因此返回 b。

3. 在计算` a or b `时，如果 a 是 True，则根据或运算法则，整个计算结果必定为 True，因此返回 a；如果 a 是 False，则整个计算结果必定取决于 b，因此返回 b。

即：计算结果取决于由哪个值决定。

```python
a = 'python'
print 'hello,', a and 'world'		# hello, world

b = ''
print 'hello,', b and 'world'		# hello, 

a = 'python'
print 'hello,', a or 'world'		# hello, python
# a是true，决定了or运算符被前面的a确定，所以返回a

b = ''
print 'hello,', b or 'world'		# hello, world
# b是false，由or后面的值确定，所以后面无论是真值还是假值，都是输出后面的值
```



## 四. list和Tuple类型

### 1、 list创建

`list` 有序集合，相当于数组

```python
L = ['Michael', 100, True]  #有序集合，相当于数组
print L[0]
print L[1]		# 查询不能越界
print L[-1]  	# 支持倒序查询
```

 ###  2、添加新元素

**`append()`**总是把新的元素添加到 list 的尾部。

**` insert()`**方法，它接受两个参数，第一个参数是索引号，第二个参数是待添加的新元素

```python
L.insert(0,'Lisa')	# 在第一的位置插入数据，其他数据后移一位
L.append('Paul')	# 在最后插入元素
```

### 3、删除元素

**`pop()`** 方法总是删掉list的最后一个元素，并且它还返回这个元素。

**`pop(2)`** 删除指定元素

### 4、替换

重新赋值

```python
L[-1] = 'Bart'
```

### 5、 tuple创建

tuple也是数组，但是不能修改

```python
t = ('Adam', 'Lisa', 'Bart')
```

### 6、 单元素tuple

```python
t = (1)		#系统视()为运算符，结果为1
t = (1,)	#系统认为是tuple,是一个数组(1,)
```

### 6、“可变”tuple

```python
t = ('a', 'b', ['A', 'B'])
L = t[2]	# 通过下标拿到第三个元素
L[0] = 'X'
L[1] = 'Y'
print t     # ('a', 'b', ['X', 'Y'])	# 内容被改变
```

![img](http://img.mukewang.com/540538d400010f4603500260.jpg)

所以，tuple所谓的**“不变”**是说，tuple的每个元素，指向永远不变。

**list 和 tuple 都是数组，区别是，一个指向可变，一个指向不可变**

**创建tuple和创建list唯一不同之处是用`( )`替代了`[ ]`**



## 五、条件判断和循环

#### 1. 条件判断

**Python代码的缩进规则。具有相同缩进的代码被视为代码块**

**缩进请严格按照Python的习惯写法：4个空格，不要使用Tab，更不要混合Tab和空格**

```python
if age >= 18:		# if ... else ...
    print 'adult'
else:
    print 'kid'
```

```python
if age >= 18:		# if ... elif ... else
    print 'adult'
elif age >= 6:
    print 'teenager'
elif age >= 3:
    print 'kid'
else:
    print 'baby'
```

#### 2. for循环

类似于 foreach语句

```python
L = ['Adam', 'Lisa', 'Bart']
for name in L:		# 输出L中的所有元素
    print name
```

#### 3. while循环

```python
N = 10
x = 0
while x < N:
    print x
    x = x + 1
```

#### 4. break 退出循环

```python
sum = 0
x = 1
while True:
    sum += x		# 支持这种写法	
    x = x + 1
    if x > 100:
        break		# 注意此处是另一个块		
print sum
```

#### 5. continue 继续循环

利用 continue，不继续执行循环体的后续代码，直接进入下一次循环。

#### 6. 多重循环

```python
for x in [1, 2, 3, 4, 5, 6, 7, 8, 9]:		#打印100内出所有十位数数字比个位数数字小的数
    for y in [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]:
        if x < y:
            print x * 10 + y
```



## 六、Dict和Set类型

### 1.Dict

类似于 JavaScrip 对象

```python
d = {
    'Adam': 95,		# key值，和对应的value
    'Lisa': 85,
    'Bart': 59
}
len(d)			# len() 函数可以计算任意集合的大小
```

#### 1. 查询

使用 `d[key]` 的形式来查找对应的 value

```
print d['Adam']
```

> **注意:** 通过 key 访问 dict 的value，只要 key 存在，dict就返回对应的value。如果key不存在，会直接报错：KeyError。
>
> 要避免 KeyError 发生，有两个办法：
>
> **一 是先判断一下 key 是否存在，用 in 操作符：**
>
> ```
> if 'Paul' in d:
>     print d['Paul']
> ```
>
> 如果 'Paul' 不存在，if语句判断为False，自然不会执行 print d['Paul'] ，从而避免了错误。
>
> **二 是使用dict本身提供的一个 get 方法，在Key不存在的时候，返回None：**
>
> ```python
> >>> print d.get('Bart')
> 59
> >>> print d.get('Paul')
> None
> ```

### 2. 特点

|      |  dict  |  list   |
| :--: | :----: | :-----: |
| 查询速度 | 快，占用内存 | 慢，占用内存小 |
| 存取顺序 |  没有顺序  |    有    |

dick查询每个值的速度都相同，与表中元素的多少无关。

dick中的元素没有顺序

dick作为key的元素不可变。

#### 3. 更新dict

```python
d['Paul'] = 72
```

如果key不存在，就在表中添加一个元素

如果key存在，就更新这个key的值

#### 4. 遍历dict

```python
for key in d:
    print key,':',d[key]
```

#### 5. set

**set 持有一系列元素，这一点和 list 很像，但是set的元素没有重复，而且是无序的，这点和 dict 的 key很像。**

```
s = set(['A', 'B', 'C'])
```

```python
s = set(['A', 'B', 'C', 'C'])
print s	     #  输出 set(['A', 'C', 'B'])
			#  注意输出为乱序
```

判断某个元素是否在set中：

```
'Bart' in s			# 返回布尔值
```

#### 6. set的特点

**set的内部结构和dict很像，唯一区别是不存储value**，因此，判断一个元素是否在set中速度很快。

**set存储的元素和dict的key类似，必须是不变对象**，因此，任何可变对象是不能放入set中的。

**set存储的元素也是没有顺序的**

`无序` `不重复` `不可改变`

```python
weekdays = set(['MON', 'TUE', 'WED', 'THU', 'FRI', 'SAT', 'SUN'])
x = '???' # 用户输入的字符串
if x in weekdays:		# 不需要繁琐的进行判断
    print 'input ok'
else:
    print 'input error'
```

#### 7. set遍历

```python
s = set(['Adam', 'Lisa', 'Bart'])
for name in s:
	print name			# 输出可以用加号连接
```

#### 8. set更新

```python
s = set([1, 2, 3])
s.add(4)		# 添加的元素可以为存在的，不报错，但也不会添加进去
s.remove(2)		# 只能删除元素，不存在下标删除，因为它是无序的
```



## `List` `Tuple` `Dict` `Set` 比较

|  类型   |        特点         |      表示       |
| :---: | :---------------: | :-----------: |
| List  |  `数组` `有序` `可修改`  |     `[ ]`     |
| Tuple | `数组` `有序` `不可修改`  |     `( )`     |
| Dict  | `无序` `key-value`  | `{ : , : , }` |
|  Set  | `无序` `不重复` `不可改变` |               |



## 七、函数

### 1. 内置函数

[内置函数](https://docs.python.org/2/library/functions.html#abs) 

### 2. 自定义函数

定义一个函数要使用 `def`  语句，依次写出函数名、括号、括号中的参数和冒号:

然后，在缩进块中编写函数体，函数的返回值用 return语句返回。

如果没有return语句，函数执行完毕后也会返回结果，只是结果为 None。

return None可以简写为return。

```python
def conpare(a,b):
	return a<b
```

#### 1. 返回多值

```python
import math			# 导入math函数包
def move(x, y, step, angle):	# 计算新坐标
    nx = x + step * math.cos(angle)
    ny = y - step * math.sin(angle)
    return nx, ny
print move(1,2,3,45)	# (2.575965966453189, -0.5527105736023552)
print move(1,2,3,45)[0]	# 2.57596596645
```

**Python的函数**返回多值其实就是**返回一个tuple**

#### 2. 递归函数

计算阶乘：

```python
def fact(n):
    if n==1:
        return 1
    return n * fact(n - 1)
```

汉诺塔：

```python
def move(n, a, b, c):
    if n ==1:
        print a, '-->', c
        return
    move(n-1, a, c, b)
    print a, '-->', c
    move(n-1, b, a, c)
move(4, 'A', 'B', 'C')
```
#### 3. 定义默认参数

系统自带的 `int()` 函数，有两个参数。第二个参数默认为十进制。

```python
int('123')		# 123
int('123',8)	# 83
int('123',16)	# 291
```

**函数的默认参数的作用是简化调用**

```python
def power(x, n=2):		# 默认为2次方
    s = 1
    while n > 0:
        n = n - 1
        s = s * x
    return s
power(5)		# 25
power(5,3)		# 125
```

**默认参数只能定义在必需参数的后面:**

```python
# Error:
def fn2(a=1, b):
    pass
```

#### 4. 可变参数

**前提：** 函数能接受任意个参数

```python
def fn(*args):
    print args
```

直接把变量 args 看成 tuple

求平均值：

```python
def average(*args):
    sum = 0.0			#计算结果误差小
    if len(args) == 0:		# 增强代码的强壮
        return sum
    for x in args:
        sum = sum + x
    return sum / len(args)
print average()
print average(1, 2)
print average(1, 2, 2, 3, 4)
```

通过for循环来遍历这个list或tuple，这种遍历我们成为迭代（Iteration）

## 