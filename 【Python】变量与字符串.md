# 变量与字符串

---

作者：张浩乾

时间：2023-1-30

---

## 目录

[1.变量](#1.变量)

[2.字符串](#2.字符串)

[2.1 字符串的运算](#2.1 字符串的运算)

[2.2 字符串的切片与索引](#2.2 字符串的切片与索引)

[3.保留字与标识符](#3.保留字与标识符)

[3.1 保留字](#3. 保留字)

[3.2 标识符](# 3.2 标识符)




## 1.变量

**变量**就是编程中最基础存储单位，会暂时性的存储你放进去的任何东西

首先我们给变量赋值：

`a=3`

`A=3`

Python 会区分大小写，所以 `A` 和 `a` 是两个不同的变量

**我们要养成良好的命名习惯**，常见的命名方法有以下两种：

+ [驼峰命名法][1]

  1. 大驼峰命名法：所有的单词首字母大写，其余小写，适用于类、函数、属性，例如

  Student_Information

  2. 小驼峰命名法：第一个单词首字母小写，其余单词首字母大学，适用于变量，例如

  student_Count

+ [帕斯卡命名法][2]：与大驼峰的命名规则一致

## 2.字符串

单引号`''`和双引号 `""` 完全起到一样的作用，三引号 `''' '''` 被用于长段的问题，可以实现

自由换行

## 2.1 字符串的运算

+ 相加：

~~~python
a='print'
b='count'
print(a+b)
~~~

+ 相乘

~~~Python
a='count'
b='print'
print(a*b)
print(a*3,'\n',b*3)
~~~

运行第三行报错：***TypeError: can't multiply sequence by non-int of type***

*** 'str'***，这是因为**字符串不能相互做乘法运算，而是要和 `int` 型做乘法**

## 2.2 字符串的切片与索引

字符串的切片就是将一个字符串中自己需要的部分复制出来，储存在另一地方，而不会改变字符串

的源文件，切片获得的每一个字符串都可以看作是原字符串的一个副本

首先，我们来说说什么是索引,索引就是变量名加一个[]

先创建一个变量name='My Name is Mike',一共 15 个字符，从左到右依次为 0 到 14，

从右到左为 -1 到 -15

**Tips：**

+ 编号为 `n` 的字符是字符串的第 `n+1`个字符
+ 切片就是一个**左闭右开**的区间

然后我们使用索引进行切片

~~~Python
name='My Name is Mike'
Name_1=name[11:14]
Name_2=name[5:]
Name_3=name[:5]
Name_4=name[-3:-1]
Name_5=name[1:5:2]
print(Name_1,Name_2,Name_3,Name_4,Name_5)
~~~


`Name_1=name[11,14]` 截取的编号从 11 开始，到 14 结束，但不包括编号为 14 的字符

`Name_2=name[5:]` 截取的编号从 5 开始直到结束

`Name_3=name[:5]` 截取的字符编号从 0 开始到 5 结束，但是不包括编号为 5 的字符

`Name_4=name[-3:-1]` 截取的字符为从右往左数第三个到第二个

`Name_5=name[1:5:2]` 截取的字符串从编号 1 到 5，以 2 为步长

  

![Loading……](https://i.328888.xyz/2023/01/30/8yKbk.jpeg)



## 3.保留字与标识符

### 3.1 保留字

**保留字**就是已经被授予一定特殊含义的一些单词，在开发程序时，不可以把这些单词作为自定义的名称来使用，常见的如下图所示：



![](https://gitee.com/peterluor/picture/raw/master/202303041713220.jpg)

**Tips：**Python中的保留字是区分大小写的，例如`if`是保留字，但是`If`就不是保留字了



**如何在Python中查看保留字**

~~~Python
import keyword
print(keyword.kelist)
~~~



### 3.2 标识符

标识符就是给对对象进行命名，规则如下：



- 由字母、数字以及下划线组成，并且第一个字符不能是数字，例如`2——base`就是非法的
- 不能使用 Python 中的保留字
- 严格区分大小写，例如 `Sw` 和 `sw`是不同的标识符
- Python中以下划线开头的标识符一般有特殊的意义，建议在命名的时候避免此类情况




[1]: https://blog.csdn.net/jerry11112/article/details/84985026
[2]: https://blog.csdn.net/taifei/article/details/86612281