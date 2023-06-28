# 异常处理与程序调试

## 1.异常概述

平时我们在运行程序的过程中，经常会出现各种各样的报错，这些报错就称之为为异常。最常见的异常就是`SyntaxError: invalid syntax`，也就是无效的语法，这种异常称之为**显性异常**；还有一些异常，在程序运行的时候不会报错，但是当我们再输入一些错误的值的时候（**例如，把0当作除数**），这些异常被称之为隐性异常。常见的异常如下图所示：

![常见异常](https://gitee.com/peterluor/picture/raw/master/202305162123722.jpg)

(NameError,IndexError,IndentationError,ValueError,KeyError,IOError,ImportError,AttributeError,TypeError,MemoryError,ZeroDivisionError)

## 2.异常处理

### 2.1 `try……except……`语句

将可能出现异常的代码放进try语句中，如果再执行过程中给出现了任何异常，就会执行except中的语句，如果不出现异常，就不执行，

具体的格式如下所示：

~~~python
try:
    block1
except (Exceptionname1,Exceptionname2,……) as x:
    block2
~~~

其中，`Exceptionname`是自己怀疑的可能的异常,在右面加一个`as`，就会给异常起一个别名，通过该别名，可以记录异常的具体内容

举例如下：

~~~python
try:
    a=1
    print(c)
except NameError as Ne:
    print('Error')
    print(Ne)
~~~

### 2.1.2 `try……except……else`语句

相比于`try……except`语句多了一个else语句，用于**指定当try中的语句没有报错时的输出结果**，举例如下：

~~~python 
try:
    a=1
    b=2
    print(a+b)
except:
    print('error')
else:
    print('OK')
~~~

### 2.1.3 `try……except……finally`语句

加入`finally`语句表示无论是否有异常产生，finally中的语句都应该被执行。这种情况适用于**一个程序中有一些必须要执行的代码，就可以将其放入到finally语句之中**。举例如下：

~~~python
import math
def division():
    apple=int(input('请输入苹果的个数:'))
    people=int(input('请输入人数:'))
    if apple<people:
        print('苹果数目不够')
    else:
        result=math.floor(apple/people)
        remain=apple-people*result
        if remain>0:
            print(apple,'个苹果,平均分给',people,'个小朋友，平均每人分了',result,'个苹果，剩余',remain,'苹果')
        else:
            print(apple,'个苹果,平均分给',people,'个小朋友，平均每人分了',result,'个苹果，没有剩余')
if __name__=='__main__':
    try:
        division()
    except ZeroDivisionError:
        print('苹果不能分给0个小朋友')
    except ValueError as e:
        print('\n出错了',e)
~~~

### 2.1.4 `raise`抛出异常

如果某一个方法或者函数可能会产生异常，但又不想在当前的函数或者方法中处理异常，就可以使用raise语句在函数或者方法中抛出异常。

`raise [ExceptionName(reason))]`

+ ExceptionName 抛出的异常的名称
+ reason 异常信息的相关描述

## 3.程序调试

