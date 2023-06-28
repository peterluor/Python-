# 常见函数

[1.replace函数](#1.replace函数)

[2.find函数](#2.find函数)

[3.format函数](#3.format函数)

## 1.replace函数

具体的用法为**str.replace(old,new,max)**

+ old 是要被代替的字符串
+ new 是代替的新字符串
+ max 是最大的代替次数，不能超过这个次数

**示例**

给关键信息打码：

~~~python
Str='this is my number:1008612!'
Str_1=Str.replace(Str[-8:-1],'*'*7)
print(Str_1)
~~~

## 2.find函数

Python find() 方法检测字符串中是否包含子字符串 str ，如果指定 beg 和 end 范围，则

检查指定范围，否则检测全字符串，有符合结果返回子字符串开始的索引值，反之返回 -1 

具体的用法为**string.find(str,beg,end)**

+ string 是要被检查的字符串
+ str 寻求配对的子字符串
+ beg 开始索引，默认值为 0, beg=0
+ end 结束索引，默认值为字符长度，end=len(string)

**示例**

~~~python
Str='this is my number:1008612!'
print(Str.find('is'))
print(Str.find('is',3))
print(Str.find('is',3,7))
print(Str.find('is',3,4))
~~~

输出结果如下所示：

`2`

`5`

`5`

`-1`

## 3.format函数

**format函数用于格式化字符串**，且可以接受不限个参数，位置可以不按顺序。

具体用法为**str.format()**

+ str是要被格式化的字符串

+ format后面的内容也可以以索引值的形式放在前面的字符串中

**示例**

~~~Python
s_1="{1} is after {0},{2} isn't before {1}".format('hello','world','!')
print(s_1)
~~~

输出结果为

`world is after the hello,! isn't before the world`

~~~python
s_2="{} is after {},{} isn't before {}".format('hello','world','!','*')
print(s_2)
~~~

输出结果为

`hello is after world,! isn't before *`

从上面就可以看出

format如果在前面的 str 中使用了索引，就是按照 format 括号中的索引一一对应，如果没有

使用索引，则按照 format 括号中内容的位置一一对应，就好像函数中的关键词参数和位置参数

一样



[#1.replace函数]: 
