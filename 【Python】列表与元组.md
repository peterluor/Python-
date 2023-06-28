# 列表与元组

---

***Time：2023-04-18***

***Author：peterluor***

---

## content

[1.列表与元组的区别](# 1.列表与元组的区别)

[2.列表的创建与运算](#2.列表的创建与运算)

​	[2.1 列表的创建](# 2.1 列表的创建)

​	[2.2 列表的删除](# 2.2列表的删除)

[3.列表元素的访问](# 3.列表元素的访问)

​	[3.1 列表的切片](# 3.1 列表的切片)

​	[3.2 列表的遍历](# 3.2 列表的遍历)

​		[3.2.1 使用for循环](# 3.2.1 直接使用for循环)

​		[3.2.2 使用for循环和enumerate()函数实现](# 3.2.2 使用for循环和enumerate()函数实现)

[4.元素的添加与删除](# 4.元素的添加与删除)

​	[4.1 添加元素](# 4.1 添加元素)

​	[4.2 修改元素](4.2 修改元素)

​	[4.3 删除元素](# 4.3 删除元素)

​		[4.3.1 通过索引删除](# 4.3.1 通过索引删除)

​		[4.3.2 通过元素值删除](# 4.3.2 通过元素值删除)

[5.列表的统计计算](# 5.列表的统计计算)

​	[5.1 统计元素出现的次数](# 5.1 统计元素出现的次数)

​	[5.2 获取元素首次出现的位置](# 5.2 获取元素首次出现的位置)

​	[5.3 列表元素求和](# 5.3 列表元素求和)

​	[5.4 列表元素排序](# 5.4 列表元素排序)

[6.列表推导式](# 6.列表推导式)

[7.元组的创建与删除](# 7.元组的创建与删除)

​	[7.1 直接创建元组](7.1 直接创建元组)

​	[7.2 创建数值元组与空元组](# 7.2 创建空元组与数值元组)

​	[7.3 删除元组](# 7.3 删除元组)

[8.元组的访问与修改](# 8.元组的访问与修改)

​	[8.1 元组的访问](# 8.1 元组的访问)

​	[8.2 元组元素的修改](# 8.2 元组元素的修改)

​	[8.3 元组的连接](# 8.3 元组的连接)

[9.元组推导式](# 9.元组推导式)

## 1.列表与元组的区别

+ 列表可以修改，但是元组不可以修改
+ 列表与元组均支持切片，但是元组只能通过切片访问元组中的元素，但是不支持修改
+ 元组的访问速度更快，所以仅访问就使用元组
+ 列表不能作为字典的键，但是元组可以

## 2.列表的创建与运算

## 2.1 列表的创建

直接使用赋值对列表进行创建，例如:

~~~
l=[1,2,3,4]
l1=[[1,2,3],1,'1',(1,2,3)]
l_empty=[]
~~~

**Tips:** 在一个列表中，可以放入不同的数据类型，但是我们一般只放一个以**提高程序的可读性**

**创建数值列表**

使用`list()`函数将其他的对象直接转化为列表

~~~Python
a=list(range(2,10))
print(a)
~~~

## 2.2 列表的删除

直接使用`delete + 列表名`键进行删除列表操作

~~~python 
l=[]
delete l
~~~

看一下官方文件中对于`help`命令的描述

---

 ***del_stmt ::= "del" target_list***

Deletion is recursively defined very similar to the way assignment is
defined. Rather than spelling it out in full details, here are some
hints.

Deletion of a target list recursively deletes each target, from left
to right.

Deletion of a name removes the binding of that name from the local or
global namespace, depending on whether the name occurs in a "global"
statement in the same code block.  If the name is unbound, a
"NameError" exception will be raised.

Deletion of attribute references, subscriptions and slicings is passed
to the primary object involved; deletion of a slicing is in general
equivalent to assignment of an empty slice of the right type (but even
this is determined by the sliced object).

Changed in version 3.2: Previously it was illegal to delete a name
from the local namespace if it occurs as a free variable in a nested
block.

Related help topics: BASICMETHODS

---

## 3.列表元素的访问

要访问指定的元素，直接使用`listname[n] n为对应的索引值`进行访问，例如：

~~~python
# 访问名为l的列表中第二个元素
l=[1,2,3,4]
print(l[1])
~~~

### 3.1 列表的切片

列表的切片与字符串的切片基本一致，有以下两个原则需要记住：

+ 切片是一个**左闭右开**的区间
+ 列表的切片也是使用**方括号与冒号** `[a:b]`

例如，在一个列表中输出**第二位到第八位**的元素:

~~~python 
l=list(range(1,20))
print(l[1:8])
~~~

**详细解释一下这个**，`[a,b]`在切片的时候是一个**左闭右开**的区间，包含`a+1`但是不包含`b+1`,所以直接输出的就是**一个列表中第 a+1 位到第 b 位的所有元素**

### 3.2 列表的遍历

#### 3.2.1 直接使用for循环

代码如下所示：

~~~python
a=list(range(1,21))
for i in a:
    print(i,end=' ')	# end=' ' 实现不换行，在结尾加指定的值
~~~

### 3.2.2 使用for循环和enumerate()函数实现

使用for循环以及`enumerate()`可以实现对列表的**索引值以及元素内容进行输出**

~~~python 
l=list(range(1,21))
for index,item in enumerate(l):
    print(index,item)
#index 代表元素的索引值
#item 代表获取到的元素值
~~~



## 4.元素的添加与删除

### 4.1 添加元素

使用`list.append(x)`在列表的**末尾**后添加**任意类型的元素**，例如:

~~~python
l=list(range(1,21))
for i,j in enumerate(l):
    print(i,j,end=' ')
l.append(21)
for i,j in enumerate(l):
    print(i,j,end=' ')
~~~

Tips:

+ 添加元素再赋值:`l=l.append(x)`的做法是一种错误的做法
+ 上面提到的任意元素包括 `数值`、`字符串`、`列表`、`元组`，示例如下：

~~~python
l_1=[1,2,3,4]
int=1
str='python'
truple=(1,2,3,4)
l_2=[5,6,7,8]
l_1.append(int)
print(l_1)
l_1.append(str)
print(l_1)
l_1.append(truple)
print(l_1)
l_1.append(l_2)
print(l_1)
~~~

输出的结果为：

~~~python
[1, 2, 3, 4, 1]
[1, 2, 3, 4, 1, 'python']
[1, 2, 3, 4, 1, 'python', (1, 2, 3, 4)]
[1, 2, 3, 4, 1, 'python', (1, 2, 3, 4), [5, 6, 7, 8]]
~~~

使用`list.extend(seq)`将一个**列表/元组**中的全部元素添加到源列表中，例如：

~~~python
l_1=[1,2,3,4]
l_2=[5,6,7,8]
truple=(7,8,9,0)
l_1.extend(l_2)
print(l_1)
l_2.extend(truple)
print(l_2)
~~~

输出结果为：

~~~python
[1, 2, 3, 4, 5, 6, 7, 8]
[5, 6, 7, 8, 7, 8, 9, 0]
~~~

关于对于`extend()`以及`append()`的使用以及进一步的问题，详见[Python 列表 append()函数使用详解](https://blog.csdn.net/wangyuxiang946/article/details/122142534?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522168174054216800186591755%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=168174054216800186591755&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-2-122142534-null-null.142^v84^wechat,239^v2^insert_chatgpt&utm_term=python%20append&spm=1018.2226.3001.4449)

### 4.2 修改元素

关于修改列表中元素的基本原理就是**通过索引值获取列表中元素，然后对该元素重新赋值**，举例如下：

~~~python
l=[1,2,3,4,5]
print('Brfore modifying:',l)
l[3]=5
print('After modifying:',l)
~~~

### 4.3 删除元素

#### 4.3.1 通过索引删除

首先使用索引值读取列表中的元素，然后再使用`del`进行删除，举例如下：

~~~python
l=[1,2,3,4,5]
print(l)
del l[2]
print(l)
~~~

#### 4.3.2 通过元素值删除

对于**不能确定元素位置的列表，可以通过`list.remove()`函数进行指定元素删除**，举例如下：

~~~python
l=[1,3,1,2,3,4,4,5,4,6,2,1]
print(l)
l.remove(1)
print(l)
~~~

**Tips:**

+ **`list.remove()`函数只能删除列表中出现的第一个指定的元素**
+ **删除元素之前先判断元素存不存在，否则会提示异常，可以使用`list.count()`来判断列表中元素的数目，返回值为`0`表示元素不存在**

~~~python
l=[1,3,1,2,3,4,4,5,4,6,2,1]
n_1=l.count(1)
n_2=l.count(2)
print(n_1,n_2)
~~~

## 5.列表的统计计算

### 5.1 统计元素出现的次数

前文已经介绍过，使用`list.count(x)`来判断元素`x`在列表中出现的次数

### 5.2 获取元素首次出现的位置

使用`list.index(x)`返回元素`x`在列表中首次出现的位置，即它的索引值，举例如下：

~~~python
l=[1,2,3,3,1,1,3,4,4,5]
//首先需要判断列表中存不存在3
n=l.count(3)
if n>0:
	index=l.index(3)
    print(index)
else:
    pass
~~~

### 5.3 列表元素求和

使用`sum(list,start)`来求数值列表中各个元素的和

参数说明：

+ list 数值列表
+ start 求和开始元素的索引值，默认值为 0

举例如下： 

~~~python
l=list(range(21))
sum=sum(l)
print(sum)
~~~

### 5.4 列表元素排序

使用`list.sort(key,reverse)`来对列表中的元素进行排序，参数说明：

+ list 要排序的列表
+ key 指提取一个比较键，例如`key=str.lower`表示排序的时候不区分大小写
+ reverse 可选参数，值为`True`的时候，表示降序排列，值为`False`的时候，表示升序排列，默认**升序排列**

举例如下：

~~~python
# 对十个人的数学成绩进行一个升序排列
grade=[98,99,97,100,100,96,94,89,95,100]
grade.sort(reverse=False)
print(grade)

char=['cat','Tom','Angeal','pEt']
# 区分大小写升序排列
char.sort(reverse=False)
print(char)
# 不区分大小写升序排列
char.sort(key=str.lower,reverse=False)
print(char)
~~~

使用`list_new=sorted(list,key,reverse)`对列表中的元素进行排列,其**返回值为一个列表**，参数说明：

+ list 要排序的列表
+ list_new 排序后获得的新列表
+ key 指提取一个比较键，例如`str.lower`指不区分大小写
+ reverse 值为`True`是表示元素降序排列，值为`False`表示元素升序排列，默认**升序排列**

举例如下：

~~~python
grade=[98,99,97,100,100,96,94,89,95,100]
grade_1=sorted(grade,reverse=True)
print(grade_1)
~~~

## 6.列表推导式

列表推导式就是使用一个表达式来获得一个新的列表，常见的使用格式有以下三种：

+ `list=[expression for var in range]`
+ `list=[expression for var in list_old]`
+ `list=[expression for var in list if condition]`

参数说明：

`list` 新生成的列表

`expression` 推导表达式,**表达式计算的就是新列表中的元素**

`var` 一个循环变量，**可以和表达式有关，也可以和表达式无关**

`range` 循环变量循环的范围

`list_old` 要被生成的原先的列表

`condition`  要生成新列表的限制条件,**限制条件是对变量的限制**

**示例如下：**

~~~python
import random
# 首先使用循环生成一个长度为10的处于10-100之间的列表
list_old=[]
for i in range(10):
    a=random.randint(10,100)
    list_old.append(a)
# 对列表进行升序排列看起来更直观
list_old.sort(reverse=False)
print('list_old=',list_old)
# 生成一个新列表是原来列表的2倍
list_1=[i*2 for i in list_old]
list_1.sort(reverse=False)
print('list_1=',list_1)
# 生成一个新列表，当旧列表元素大于30的时候才乘以2加入新的列表
list_2=[i*2 for i in list_old if i>30]
list_2.sort(reverse=False)
print('list_2=',list_2)
~~~

其实，生成一个长度为10的处于10-100之间的列表也可以直接使用推导式，例如：

~~~python
import random
list_old=[random.randint(10,100) for i in range(10)]
list_old.sort()
print(list_old)
~~~

## 7.元组的创建与删除

### 7.1 直接创建元组

元组的格式为`trumple=(element)`，其中的元素可以是任意的数据类型，举例如下：

~~~python
tuple=(1,2,3,[1,2,3],(1,2,3),'str')
print(tuple)
~~~

而且，**小括号也不是必须的，只要将一组值用`,`隔开，Python就会定义它为一个元组**，例如：

~~~python
tuple=1,2,3,[1,2,3,4],(1,2,3),'str'
print(type(tuple))
print(tuple)
~~~

### 7.2 创建空元组与数值元组

直接像列表一样创建一个没有任何元素的元组即可，举例如下：

~~~python
Empty_tuple=()
print(Empty_tuple)
~~~

创建数值元素就像创建一个数值列表一样，可以直接使用`range()`函数进行创建，然后使用`tuple()`函数转化为数组即可，例如：

~~~python
tuple=tuple(range(11))
print(tuple)
~~~

### 7.3 删除元组

 使用`del tulplename`对元组实行删除操作，例如：

~~~python
tuple=tuple(range(11))
print(tuple)
del tuple
~~~

## 8.元组的访问与修改

### 8.1 元组的访问

与列表中元素的访问相似，直接使用`tuplr[i]`进行元素访问，例如：

~~~python
tuple=tuple(range(11))
for i in range(11):
    print(tuple[i])
~~~

### 8.2 元组元素的修改

元组是不可变序列，**不能直接使用元素替换进行修改，但是我们可以对元组进行重新赋值**，例如：

~~~python
tuple=(1,2,3,4)
print(tuple)
tuple=(1,2,3,4,5)
print(tuple)
~~~

### 8.3 元组的连接

可以使用`+`对两个元组进行连接，举例如下：

~~~python
t_1=(1,2,3,4)
t_2=('1','2')
t=t_1+t_2
print(t)
~~~

**如果要连接到元组只有一个元素，记得在元素的后面加一个逗号**，举例如下：

~~~python
t_1=(1,2,3,4)
t_2=('1',)
print(t_1+t_2)
~~~

## 9.元组推导式

元组推导式与列表推导式类似，只是将`[]`改成了`()`,但是两者唯一的区别在于**用元组推导式生成的结果不是一个元组或者列表，而是一个生成器对象，可以使用`list()`或者`tuplr()`函数将其转化为列表或元组**。
