# 运算符与表达式



---

*Author：*张浩乾

*Time：*2023-04-15

---

## Content

[1.运算符](#1.运算符)

[2.表达式](#2.表达式)

## 1.运算符

常见的运算符以及它们的优先级如下图所示：

![优先级](https://gitee.com/peterluor/picture/raw/master/202304152136830.jpg)



**Tips：**在编写程序的时候尽可能地使用括号 **() **来限定运算的次序，以免运算次序发生错误

## 2.表达式

主要介绍一下**条件表达式**的使用方法

我们简单的输入一个条件判定：

~~~Python
a=2
b=3
if a>b:
    r=a
else:
    r=b
print(r)
~~~

我们可以使用条件表达式来对这个条件判定进行一个简化：

~~~python
a=2
b=3
r= a if a>b else b
~~~

在使用条件表达式的时候，**先执行`if`后面的条件语句，结果为`True`,执行前面的语句，结果为`False`,执行`if`后面的语句





