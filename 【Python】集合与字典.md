# 集合与字典

---

***作者：张浩乾***

***时间：2023-05-16***

---

# 目录

[1.什么是字典](# 1.什么是字典)

[2.字典的创建与删除](# 2.字典的创建与删除)

​	[2.1 直接创建](# 2.1 直接创建)

​	[2.2 通过映射函数zip()创建](# 2.2 通过映射函数zip()创建)

​	[2.3 通过键值对的方式创建](# 2.3 通过键值对的方式创建字典)

​	[2.4 创建只有键值为空的字典](# 2.4 创建只有键值为空的字典)

​	[2.5 使用存在的元组或者列表创建字典](# 2.5 使用存在的元组或者列表创建字典)

​	[2.6 字典的删除](# 2.6 字典的删除)

[3.字典的访问与遍历](# 3.字典的访问与遍历)

​	[3.1 字典的访问](# 3.1 字典的访问)

​	[3.2 字典的访问](# 3.2 字典的访问)

[4.字典元素的添加、修改与删除](# 4.字典元素的添加、修改与删除)

​	[4.1 字典元素的添加](# 4.1 字典元素的添加)

​	[4.2 字典元素的修改](# 4.2 字典元素的修改)

​	[4.3 字典元素的删除](# 4.3 字典元素的删除)

[5.字典推导式](# 5，字典推导式)

[6.集合](# 6.集合)

​	[6.1 集合简介](# 6.1 集合简介)

​	[6.2 集合的创建](# 6.2 集合的创建)

​		[6.2.1 直接使用{}创建](# 6.2.1 直接使用{}创建)

​		[6.2.2 使用set()创建](# 6.2.2 使用set()函数创建)

​	[6.3 集合元素的添加与删除](# 6.3 集合元素的添加与删除)

​		[6.3.1 集合元素的添加](# 6.3.1 集合元素的添加)

​		[6.3.2 集合元素的删除](# 6.3.2 集合元素的删除)

​	[6.4 集合的交集、并集与差集](# 6.4 集合交集、并集与差集)

 ## 1.什么是字典？

字典是一种可变序列，但是它是无序的，保存内容是以**键值对**的形式进行保存，举个例子，就好像新华字典中的拼音与汉字的一一对应关系一样，通过音节就可以找到汉字，音节就相当于键（`key`），汉字就相当于值（`vaule`）,键具有唯一性，但是值可以有很多个。

+ 读取字典通过**键（`key`）而不是索引值**
+ 字典是任意对象的无序组合，**保存在字典中的项没有特定的顺序**
+ **字典可以变化，并且可以字典嵌套字典**
+ 字典的`key`必须是唯一的，**如果出现两个，则会记住最后一个**，并且字典的键是不可变的,所以只能是**元组、数字以及字符串**，但是字典的值可以是任何数据类型。

## 2.字典的创建与删除

### 2.1 直接创建

字典使用`{}`进行创建，并且每个元素包括`key:vaule`,相邻元素使用`,`隔开

具体格式如下：

~~~python
dict={'key1':'vaule1','key2':'vaule2',……}
~~~

举例如下：

~~~python
dict={'name':'peterluor','qq':'123456','number':[1,2]}
print(dict)
~~~

创建空字典，举例如下：

~~~python
dict_empty={}
dict_empty=dict()
~~~

### 2.2 通过映射函数`zip()`创建

简单介绍一下`zip()`函数：zip函数是将多个元组或者列表对应位置的值组合成一个元组，并返回为包含这些内容的zip对象，然后可以使用`list()`或者`tuple()` 函数将其转换为列表或元组。

~~~python
l1=list(range(11))
l2=list(range(21))
t1=tuple(range(12))
# 两个列表进行组合，输出为列表
print(list(zip(l1,l2)))
# 列表元组进行组合，输出为列表
print(list(zip(l1,t1)))
# 列表元组互相混合，输出为元组
print(tuple(zip(l1,l2,t1)))
~~~

输出结果为：

~~~python 
[(0, 0), (1, 1), (2, 2), (3, 3), (4, 4), (5, 5), (6, 6), (7, 7), (8, 8), (9, 9), (10, 10)]
[(0, 0), (1, 1), (2, 2), (3, 3), (4, 4), (5, 5), (6, 6), (7, 7), (8, 8), (9, 9), (10, 10)]
((0, 0, 0), (1, 1, 1), (2, 2, 2), (3, 3, 3), (4, 4, 4), (5, 5, 5), (6, 6, 6), (7, 7, 7), (8, 8, 8), (9, 9, 9), (10, 10, 10))
[(0, 0), (1, 1), (2, 2), (3, 3), (4, 4), (5, 5), (6, 6), (7, 7), (8, 8), (9, 9), (10, 10)]
~~~

**Tips：**`zip()`合并的两个序列长短不一致时，合并后序列的长度取决于短序列的长度

**要想输出的为字典，就只能使`zip()`后的参数数目为两个，并且第一个参数为`key`,第二个参数为`vaule`,然后使用`dict()`函数将 zip 对象转换为字典**，举例如下：

~~~python
# key，21以内的所有偶数
l1=list(range(0,21,2))
# vaule,22以内的所有奇数
l2=list(range(1,22,2))
dict=dict(zip(l1,l2))
print(dict)
~~~

### 2.3 通过键值对的方式创建字典

我们可以直接通过`dict=dict(key=vaule)`的方式来创建一完整的字典，举例如下：

~~~python
dict=dict(name='peterluor',qq=123456,password='123456')
print(dict)
~~~

### 2.4 创建只有键值为空的字典

我们使用`dict.fromkeys(list)`创建只有键值的字典，`list`是保存键值的列表，举例如下：

~~~python
list=list(range(11))
dict=dict.fromkeys(list)
print(dict)
~~~

### 2.5 使用存在的元组和列表创建字典

~~~python
# 创建一个元组和列表
tuple=tuple(range(0,21,2))
list=list(range(1,22,2))
# 元组作为key，列表作为vaule创建字典
dict_1={tuple:list}
print(dict_1)
# 列表作为key，元组作为vaule创建字典
dict_2={list:tuple}
print(dict_2)
~~~

第一个正常输出，如下所示：

~~~python
{(0, 2, 4, 6, 8, 10, 12, 14, 16, 18, 20): [1, 3, 5, 7, 9, 11, 13, 15, 17, 19, 21]}
~~~

第二个会报错：

~~~python
TypeError: unhashable type: 'list'
~~~

为什么会报错？？？

因为**前文我们已经提到过，字典中的键一定是不可变的，所以只能是数字、字符串以及元组，不能是列表**

### 2.6 字典的删除

直接使用`del`对字典进行删除：

~~~python
list=list(range(11))
tuple=tuple(range(11))
dict=dict(zip(list,tuple))
print(dict)
del dict
~~~

也可以使用`dictionary.clear()`将一个字典变为空字典：

~~~python
list=list(range(11))
tuple=tuple(range(11))
dict=dict(zip(list,tuple))
print(dict)
dict.clear()
print(dict)
~~~

## 3.字典的访问与遍历

### 3.1 字典的访问

就像是访问列表与元组一样，字典的访问格式是`dict[key]`来访问对应的值，举例如下：

~~~python
dict={'name':'peterluor',(1,2,3,4):[12,3,4],'number':123456}
print(dict)
print(dict[(1,2,3,4)])
~~~

输出结果为：

~~~python
{'name': 'peterluor', (1, 2, 3, 4): [12, 3, 4], 'number': 123456}
[12, 3, 4]
~~~

存在一种情况，当我们输入的键对应的值不存在的时候，就会抛出异常

~~~python
KeyError: 1
~~~

所以，我们在查询字典的值的时候需要加一个`if……else……`语句，对不存在的情况输出一个提示，举例如下：

~~~python
list=list(range(0,21,3))
tuple=tuple(range(1,22,3))
dict=dict(zip(list,tuple))
print(dict['name'] if 'name' in dict else 'Not Found!')
~~~

**获取字典中的值的方法比较推荐的是`dict.get(key,default)`,参数说明：`dict`——字典，`key`——指定的键，`default`——可选项，当指定的键对应的值不存在的时候，返回一个默认值，这个默认值可以自己设置。**举例如下：

~~~python
list=list(range(0,21,3))
tuple=tuple(range(1,22,3))
dict=dict(zip(list,tuple))
print(dict.get(0,'Not Found!'))
print(dict.get('name','Not Found!'))
~~~

### 3.2 字典的遍历

使用`dict.items()`与循环相结合的方式对一个字典进行遍历，将字典的**键-值对**一一输出，返回对象为**键值对组成的元组**，举例如下：

~~~python
list=list(range(0,21,3))
tuple=tuple(range(1,22,3))
dict=dict(zip(list,tuple))
for item in dict.items():
    print(item)
~~~

如果想单独地输出字典的键，可以使用`dict.keys()`与循环相结合地方式，同理，单独输出字典的值，可以使用`dict.values()`与循环相结合，**返回值为每个值或键对应的数据类型**，举例如下：

~~~python
list=list(range(0,21,3))
tuple=tuple(range(1,22,3))
dict=dict(zip(list,tuple))
for key in dict.keys():
    print(key)
for value in dict.values():
    print(value)
~~~

## 4.字典元素的添加、修改与删除

由于字典是一个可变序列，所以字典可以进行添加、修改与删除操作。

### 4.1 字典元素的添加

字典中元素的添加是通过添加`键值对`的方式进行直接添加，举例如下：

~~~python
list=list(range(11))
tuple=tuple(range(11))
dict=dict(zip(list,tuple))
dict[11]='new value'
print(dict)
~~~

### 4.2 字典元素的修改

字典中`key`是唯一的，如果使用相同的`key`添加一个元素，则会对字典进行修改，举例如下：

~~~python
list=list(range(11))
tuple=tuple(range(11))
dict=dict(zip(list,tuple))
print(dict)
dict[10]='replacing value'
print(dict)
~~~

### 4.3 字典元素的删除

直接使用`del() dict[key]`对字典中`key`对应的**键值对**进行删除，举例如下：

~~~python
dict={'name':'peterluor','qq':123456,'password':123456}
# 密码可能会泄露，所以要进行删除
del dict['password']
# 删除后进行查找
print(dict.get('password','Not Found!'))
~~~

## 5.字典推导式

举例如下：

~~~python
dict={i:2*i for i in range(20)}
print(dict)
~~~



## 6.集合

### 6.1 集合简介

+ 集合的简写是set()
+ 集合是无序的，所以集合每次的输出结果可能会不一样
+ 集合中的元素必须是不变化的任意数据类型，包括数字、字符串以及元组s
+ 集合用于保存不重复的元素，集合主要可以分为可变集合与不可变集合两种。
+ 形式上，集合中的元素放在`{}`中，两个相邻元素使用都好`,`隔开
+ **集合最好的应用就是去重**，因为集合中的元素都是不重复的元素

### 6.2 集合的创建

#### 6.2.1 直接使用`{}`创建

**`set={element1,element2,……}`**,参数说明，set是创建的集合的名称，element是集合的元素，可以是Python中的**任意不可变**的数据类型，包括数字、字符串、元组，举例如下：

~~~python
set={1,'peterluor',,tuple(0.5*x for x in range(0,21,2))}
print(set)
~~~

#### 6.2.2 使用`set()`函数创建

直接使用`set()`函数将一些可迭代的对象例如**列表、元组、range()对象以及字符串**转换为集合，举例如下：

~~~python
list=list(range(11))
tuple=tuple(range(11))
se1_1=set(list)
set_2=set(tuple)
set_3=set(range(11))
print(set_1,set_2,set_3)
# 这三个的输出结果是一致的
# 输出字符串
str='peterluor'
set=set(str)
print(set)
# 输出结果是将字符串中的每个字符作为集合中的元素输出
~~~

最后的字符串的输出结果为：

~~~python
{'t', 'u', 'r', 'o', 'e', 'p', 'l'}
~~~

Tips：因为集合的无序性，所以每次的输出的结果都会不一样

**空集合的创建只能使用`set`函数，因为`{}`是空字典**，举例如下：

~~~python
set_empty_1={}
set_empty_2=set()
print(set_empty_1,type(set_empty_1))
print(set_empty_2,type(set_empty_2))
~~~

### 6.3 集合元素的添加与删除

#### 6.3.1 集合元素的添加

主要是通过`set.add(element)`函数进行添加，element是要添加的元素，**添加的位置不确定，因为集合具有无序性**，举例如下：

~~~python
set=set(range(11))
set.add(11)
print(set)
~~~

#### 6.3.2 集合元素的删除

a.使用`set.remove(element)`删除指定元素`element`，举例如下：

~~~python
set=set(range(11))
print(set)
set.remove(10)
print(set)
~~~

**但是使用这个方法有个缺点就是：如果你删除的元素不存在，就会抛出异常，所以需要先判断一下元素存不存在**，举例如下：

~~~python
set=set(range(11))
print(set)
set.remove(12)
~~~

抛出的异常为：

~~~python
KeyError: 12
~~~

所以我们加入一些判断语句：

~~~python
set=set(range(11))
print(set)
if 12 in set:
    set.remove(12)
    print(set)
else:
    print('12 is not in set!')
~~~

b.使用`set.pop()`删除一个元素，举例如下：

~~~python
set=set(range(11))
print(set)
set.pop()
print(set)
~~~

c.使用`set.clear()`清理一个集合中的所有元素，举例如下：

~~~python
set=set(range(11))
print(set)
set.clear()
print(set)
~~~

此处需要注意的是，在使用`set.clear()`对元素清空后，输出的是`set()`

### 6.4 集合的交集、并集和差集

集合最常见的就是进行交集、并集、差集以及对称差集运算，进行交集使用`&`,进行并集使用`|`,进行差集使用`-`,进行对称差集使用`^`，举例如下：

~~~python
import random
l1=[]
l2=[]
for i in range(11):
    l1.append(random.randint(0,100))
for j in range(11):
	l2.append(random.randint(10,100))
set_1=set(l1)
print(set_1)
set_2=set(l2)
print(set_2)
jiao_ji=set_1&set_2
bing_ji=set_1|set_2
cha_ji=set_1-set_2
duichen_chaji=set_1^set_2
print(jiao_ji)
print(bing_ji)
print(cha_ji)
print(duichen_chaji)
~~~

**所谓 A 和 B 对称差集，就是包含在A和B中，但不同时包含在A和B中的元素**，**相当于`并集-差集`**

