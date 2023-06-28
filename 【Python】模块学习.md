# 模块

## 1.什么是模块

模块的英文就是`Modules`，就好像一个包含了很多内容的盒子，与前面介绍的函数不一样，一个模块中包含很多个函数。在 python中的一个`.py`文件就是一个模块。

一般情况下，我们将可以实现某一个特定功能的代码放置在一个文件中作为一个模块，从而方便了其他程序的导入与使用，使用模块的另外一个好处就是，使用模块可以避免函数或者变量名重复。

## 2. 自定义模块

### 2.1 创建模块

创建模块可以将一段规范的代码编写进一个单独的文件中，并将该文件命名为`模块名.py`的形式，举例如下：

~~~python
# 计算用户的ＢＭＩ
 def fun_bmi(person,height,weight):
        '''
        计算用户的BMI指数
        person:用户名
        height:用户身高
        weight:用户体重
        '''
        print('身高为'+str(height))
        print('体重为'+str(weight))
        bmi=weight/(height**2)
        print(person+'BMI指数为'+str(bmi))
~~~

将这个文件保存为`bmi.py`,然后在一个新的文件中进行导入调用,举例如下:

~~~python
import bmi
bmi.fun_bmi('peter',1.67,63)
~~~

### 2.2 使用`import`语句导入模块

创建好一个模块之后,就可以将其在另一个程序中导入使用,但是请注意,如果你的库是不是标准库或者没有通过`pip`命令进行安装,那么你调用的时候请确保你要调用的模块和你的主程序在同一目录之下.

导入模块的形式有如下两种,第一种就是直接导入:

~~~python
import bmi
bmi.fun_bmi('prter',1.67,63)
~~~

第二种就是在导入之后,为了输入的方便,可以另起一个名字:

~~~python
import bmi as b
b.fun_bmi('prter',1.67,63)
~~~

使用`import`语句导入模块的时候，还可以一次性的导入多个模块，模块之间使用逗号`,`进行分割，举例如下：

~~~python
import bmi,pygame
~~~

### 2.3 使用`from……import……`语句导入模块

`from……import……`语句的语法如下所示：

~~~python
from modulename import member
~~~

**`modulename`**  要导入的模块名称

**`member`** 用于指定要导入的变量、函数或者类，可以同时导入多个，之间可以用逗号隔开，如果想要批量的导入全部，可以用`*`代替`member`

**Tips:**如果使用了星号`*`进行了全部导入，但我们又想了解导入了哪些定义，就可以显示`dir()`函数的值来查看，举例如下：

~~~python
from bmi import *
print(dir())
~~~

输出的结果为；

`['__annotations__', '__builtins__', '__cached__', '__doc__', '__file__', '__loader__', '__name__', '__package__', '__spec__', 'fun_bmi']`

最后显示的`fun_bmi`就是我们导入的函数

### 2.4 python查找路径

当我们使用import语句导入模块的时候，在默认情况下，会按照下面的顺序进行查找：

+ 当前目录（目前执行的python文件所在目录）进行查找
+ 在`PYTHONPATH`下的每个目录进行查找
+ 到python的默认安装目录下进行查找

以上目录的具体位置被保存在标准模块`sys`的`sys.path`变量中，可以通过以下方式输出具体的位置：

~~~python
import sys
print(sys.path)
~~~

如果要导入的模块不在以上的路径之中，那么我们在导入模块的时候就会报错，`No module named 'xxxx'`,这个时候就需要通过以下三种方式添加指定的目录到`sys.path`之中。

#### 2.4.1 临时添加

临时添加的目录只在执行当前文件的窗口之中有效，当窗口关闭之后就会失效，举例如下：

~~~python
import sys
path='F:\Python'
print(sys.path)
sys.path.append(path)
print(sys.path)
~~~

运行结果分别如下：

`['F:\\Python\\基础知识', 'F:\\Python\\基础知识', 'D:\\PyCharm 2022.3.3\\plugins\\python\\helpers\\pycharm_display', 'D:\\Python\\python311.zip', 'D:\\Python\\DLLs', 'D:\\Python\\Lib', 'D:\\Python', 'D:\\', 'D:\\Lib\\site-packages', 'D:\\PyCharm 2022.3.3\\plugins\\python\\helpers\\pycharm_matplotlib_backend']`


`['F:\\Python\\基础知识', 'F:\\Python\\基础知识', 'D:\\PyCharm 2022.3.3\\plugins\\python\\helpers\\pycharm_display', 'D:\\Python\\python311.zip', 'D:\\Python\\DLLs', 'D:\\Python\\Lib', 'D:\\Python', 'D:\\', 'D:\\Lib\\site-packages', 'D:\\PyCharm 2022.3.3\\plugins\\python\\helpers\\pycharm_matplotlib_backend', 'F:\\Python']`

#### 2.4.2 添加`.pth`文件(推荐)

在python安装目录的`Lib\site-packages`子目录之下，创建一个拓展名为`.pth`的文件，文件名自定义，然后在该文件中添加要导入的模块所在的目录。举例如下：

~~~python
# 这是我创建的python哦路径文件
F:\python\
~~~

**tips**:

+ 创建`.pth`文件后，需要重新打开当前的python文件之后，才能起作用
+ 通过该方法创建的文件只能在当前版本中的python中起作用

#### 2.4.3 在`PYTHONPATH`环境变量中添加

:one: 在`此电脑`图标上右键单击，在弹出的菜单之中选择`属性`命令，然后在属性的对话框左侧单击`高级系统设置`超链接。

:two: 在高级系统设置的右下角点击`环境变量`按钮，进入环境变量对话框。

:three: 在环境变量对话框中，我们先注意下有没有`PYTHONPATH`系统环境变量，没有的话就需要先创建一个，如果有的话就点击`编辑`按钮，在弹出的对话框中的`变量值`文本中添加新的模块的目录。

## 3.`python`中的包

使用模块可以避免函数名和变量名的重复，但是如果模块名重复的时候，就需要一个**比模块更高一级的概念**，这个概念就是包`(package)`。包一个一个分层次的组织目录，将一系列功能相近的模块放在同一个目录之下，如下图所示：

**tips**：包简单理解就是一个包含后缀名为`.py`的文件夹，但是这个文件夹很特殊，需要在每个文件夹下必须存在一个名为`__init__.py`的文件

![python中的包举例](https://gitee.com/peterluor/picture/raw/master/202305161121488.jpg)

### 3.1 创建和使用包

#### 3.1.1 创建包

创建包实际就是创建一个文件夹，并且在该文件夹下创建一个`__init__.py`的python文件。在这个文件中可以编写一些代码，也可以不用写任何代码，当我们导入包的时候，会自动执行`__init__.py`中的代码。例如：

:one: 首先在`F:\Python`下创建一个`example`文件夹，这就是一个名为**example**的包

:two: 然后在example文件夹之下创建一个`__init__.py`文件，已经完成了包的创建

:three: 可以在包中添加想要添加的模块，例如添加一个`size`模块，在其中定义两个变量，举例如下：

~~~python
# name=size
lenth=11
width=12
~~~



#### 3.1.2 使用包

##### 3.1.2.1 以`import packagename.modulename`的格式导入

以这种方式导入的模块，在调用模块中的函数或者变量的时候应该是以`Packagename.modulename.fun_name/Arg_name`的格式进行调用，举例如下：

~~~python
import example.size
print(example.size.lenth)
print(example.size.width)
~~~

或者可以起别名，举例如下：

~~~python
import example.size as s
print(s.lenth)
print(s.width)
~~~

##### 3.1.2.2 以`from packagename import modulename`的格式导入

按照这种方式导入的模块，在使用模块的时候只需要按照`modulename.fun_name/modulename.Arg_name`的方式进行调用，举例如下：

~~~python 
from example import size
print(size.lenth)
print(size.width)
~~~

或者可以起别名，举例如下：

~~~python
from example import size as s
print(s.lenth)
print(s.width)
~~~

~~~python 
from example.size import lenth,width
print(lenth)
print(width)
~~~

