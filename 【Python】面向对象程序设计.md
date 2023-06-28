# 面向对象程序设计

---

***作者：张浩乾***

***时间：2023-05-11***

## 目录

[1.对象](# 1.对象)

[2.类](#2.类)

[3.面向对象设计的特点](3.面向对象设计的特点)

​	[3.1 封装](# 3.1 封装)

​	[3.2 继承](# 3.2 继承)

​	[3.3 多态](# 3.3 多态)

[4.类的定义与使用](# 4.类的定义与使用)

​	[4.1 类的定义](# 4.1 类的定义)

​	[4.2 类的实例](# 4.2 类的实例)

​	[4.3 创建构造方法`__init__()`](# 4.3 创建构造方法__init__()方法)

​	[4.4 创建类的成员并访问](# 4.4 创建类的成员并访问)

​		[4.4.1 方法](# 4.4.1 实例方法)

​		[4.4.2 创建类的数据成员](# 4.4.2 创建类的数据成员)

[5.访问限制](# 5.访问限制)

[6.计算属性](# 6.计算属性)

​	[6.1 创建用于计算的属性](# 6.1 创建用于计算的属性)

​	[6.2 创建属性保护机制](# 6.2 创建属性保护机制)

[7.类的继承](# 7.类的继承)

​	[7.1 继承](# 7.1 继承)

​	[7.2 方法的重写](# 7.2 方法的重写)

​	[7.3 子类调用父类的构造方法](# 7.3 子类调用父类中的构造方法)

## 1.对象

`对象（object）`表示任意存在的事物，可以分为**静态部分**和**动态部分**，静态部分就是对象的属性等一些不可忽视的，动态属性指的是对象的行为。以人为例子，人的年龄、身高，性别等就是人的静态部分，而人会吃饭、走路、跑动等就是人这个对象的动态部分。

**在python中，一切都是对象，甚至函数`function`都是对象**

## 2.类

类就是封装对象的属性以及行为的一个载体，所以**具有相同属性以及行为的所有对象都可以称为一类**，例如，有一群大雁，可以看作一个大雁类，它们的头、翅膀等这些共有的属性就是这个类的属性，它们可以飞行、进食的这些行为就是大雁类的行为，而其中的一个大雁就是这个大雁类的一个对象。

![类与对象的关系](https://gitee.com/peterluor/picture/raw/master/202305041514508.jpg)

## 3.面向对象设计的特点

### 3.1 封装

封装就是将对象的属性以及行为封装起来，而进行封装的载体就是类，类一般对用户隐藏其实现的细节，这就是封装的本质。例如，对于一名司机而言，我仅仅需要知道车的各个按钮是干什么用的，但我不需要知道它们怎么实现具体的功能。

封装保证了内部数据的完整性，使用该类的用户不需要直接看到其中的结构，避免了对内部数据的影响，保证了代码的可维护性。

### 3.2 继承

继承就是实现了代码的重复利用，通过继承，我们可以复制一个`父类`的所有属性与行为，并在此基础上添加了`子类`特有的属性与行为。我们可以说子类就是父类的一个实例，但是反过来说就是错误的。

例如，假设现在有一个**四边形类**，它的属性就是有四条边，现在我们继承了四条边，并增加一条属性：**所有的边长度相等**，这样就又出现了一个**正方形子类**，按照这个原理，我们还可以出现**平行四边形**子类。

**但是我们也要注意，继承的子类不一定要出现新的属性**

### 3.3 多态

多态就是继承的一种体现，继承了父类的不同子类既有相同的属性，也有不同的属性，这样就可以发挥出不同的效果，这就是一种多态化的结构。

## 4.类的定义与使用

**在使用类的时候，需要先定义一个类，然后创建一个类的实例，通过类的实例（对象）来访问类的属性。**

### 4.1 类的定义

使用以下代码实现类的定义：

`class ClassName:`

​	`'类的帮助信息'`

​	`statement`

参数说明如下：

+ ClassName就是定义的类的名称，注意后面的冒号`:`一定要加
+ 类的帮助信息用于指定类的文档字符串，当创建一个类的对象时，输入类名和左侧的括号，就会显示该信息
+ statement：类体，包括类变量（成员）、属性以及方法等语句组成，如果没有想好类体，可以使用`pass`代替

举例如下：

~~~python
class Example:
    'This is a class help txt!'
    pass
~~~

### 4.2 类的实例

定义完类后，并不会真正创建一个实例。这有点像一辆汽车的设计图。设计图可以告诉你汽车看上去怎么样，但设计图本身不是一辆汽车。你不能开走它，它只能用来制造真正的汽车，而且可以使用它制造很多汽车。

那么如何创建实例呢？class语句本身并不创建该类的任何实例。所以在类定义完成以后，可以创建类的实例，即实例化该类的对象。创建类的实例的语法如下：

`ClassName(parameterlist)`

`ClassNmae`就是已经创建的类的名称，`parameterlist`就是`__init__()`中除了`self`之外的所有可选参数，举例如下：

~~~python
class Example:
    'This is an example!'
    pass
a=Example()
print(a)
~~~

### 4.3 创建构造方法`__init__()`方法

在创建一个类后，通常会创建一个`__init__()`方法，被称为**构造方法**，每当创建一个类的实例的时候，就会自己调用这个方法,这个方法中的语句会被自己执行。

`__init()__`方法必须包含一个`self`参数，并且必须是第一个参数。在调用这个方法的时候，就会自动传递实际参数`self`，所以当`__init__()`只有一个参数的时候，在创建类的实例的时候，就不需要指定实际参数了。但是这个参数的名字并不一定是`self`,可以是任意字符，举例如下：

~~~python
class Example:
    'this is a example!'
    def __init__(self):
        print('这是一个类')
a=Example()
class a:
    'abcde!'
    def __init__(a):
        print('a')
a=a()
~~~

输出的结果分别为`这是一个类`和`a`

我们也可以自定义一些其他的参数，例如，下面的代码将在创建`__init__()`方法时再指定3个参数，分别是beak、wing和claw。

~~~python 
class qwe:
    'qqq!'
    def __init__(self,beak,wing,claw):
        print('我有如下特征')
        print(beak)
        print(wing)
        print(claw)

# 创建实例并直接调用__init__()方法
a=qwe(1,2,3)
# 先创建对应的实际参数
beak_1='1'
wing_1='2'
claw_1='3'
# 直接调用__init__()方法
b=qwe(beak_1,wing_1,claw_1)
~~~

从上面我i们可以发现，调用一个类中的`__init__()`方法的时候，可以直接进行调用，并且可以直接忽略`self`参数，不用一一对应参数，并且不需要按照`classname.functioanname(self,parameter)`的方法进行调用，当然我们也可以使用这样的方法进行调用，但是参数需要一一对应，这个时候我们就可以将`self=None`来避免这个问题，举例如下：

~~~python 
class qwe:
    'qqq!'
    def __init__(self,beak,wing,claw):
        print('我有如下特征')
        print(beak)
        print(wing)
        print(claw)

# 创建实例并直接调用__init__()方法
a=qwe.__init__(None,1,2,3)
~~~

### 4.4 创建类的成员并访问

类的成员主要包括两个部分，`实例方法`与`数据成员`，详细介绍如下：

#### 4.4.1 实例方法

实例方法，就是在类中创建一个函数，这个函数有以下的注意事项：

+ 可以有返回值，也可以没有返回值
+ 该函数必须包含一个`self`参数，并且第一个参数必须是`self`
+ **类的方法只能通过类的实例进行调用**

语法如下：

~~~python
class classname:
    def __init__(self,parameter-__init__):
        pass
    def functionname(self,parameters):
        statement
~~~

`functionname`就是定义的方法的名字，`parameters`就是其他的一些参数，`statement`就是语句块，

下面来介绍一下如何调用我们创建好的实例方法，需要先创建一个类的实例，语法如下：

~~~python
a=qwe(parameter-__init__)	# 这里创建实例的时候就需要使用__init__()中除了self之外的所有参数
a.functionname(parameters)
~~~

参数的数目必须要和定义的参数的数目一一对应，举例如下：

~~~python
class Goose:
    '大雁类'
    def __init__(self,beak,wing,claw):
        print('我是一个大雁，我有以下的特征：')
        print(beak)
        print(wing)
        print(claw)
	def fly(self,state):
        print(state)        
# 先创建一个实例
wildGoose=Goose(1,2,3) # 创建实例的参数就要和自己定义的__init__()方法的除self外的所有参数一一对应
# 直接调用其中的方法实例
wildGoose.fly('我是一只雁，我会飞')
~~~

#### 4.4.2 创建类的数据成员

类的数据成员就是在类中定义的各种变量，即类的属性，根据定义的位置，我们又可以分为类属性和实例属性。

`类属性`就是定义在类中，但是在类的方法（函数）之外的所有变量。类属性可以在该类的方法与所有实例之间进行共享，通过类名称或者通过该类的实例名称进行访问，举例如下：

~~~python
# 先定义一个雁类，并创建三个属性
class Goose:
    neck='长'
    wing='宽'
    leg='身体中心点'
    def __init__(self):
        print('我是一只雁，我有以下特征')
        print(Goose.neck)
        print(Goose.wing)
        print(Goose.leg)
wildGoose=Goose()
# 使用类的实例名称调用属性
print(wildGoose.neck)
# 在类的外面直接通过类名来调用类属性
print(Goose.neck)
# 在另外一个类中调用该类的类属性
class example:
    def __init__(self):
        print(Goose.neck)
example_1=example()
~~~

`实例属性`就是定义在类的构造方法`__init__()`或者实例中的属性，只能作用于实例和方法中，并且在实例中只能通过实例名称进行调用，不能使用类的名称调用，在方法中要以`self.leg`的形式进行调用， 举例如下：

~~~python
class Goose:
    # 在__init__()中定义一些实例属性
    def __init__(self):
        self.leg='long'
        self.neck='thin'
        self.wing='xx'
	def fly(self):
        print(self.leg+self.neck)
# 创建一个类的实例
wildGoose=Goose()
# 创建实例属性
wildGoose.neck='xxx'	# 这里实例对像neck的值已经发生了变化
print(wildGoose.neck)
~~~

通过上面这两段代码我么可以看出，如果想创建实例属性，可以通过**在构造方法中以`self.args_name=`的形式进行创建**，还可以通过**在实例中直接创建的方式进行创建**，但是调用的时候只能实例名称进行调用，如果使用类名称调用，报错如下：

`type object 'Goose' has no attribute 'neck'`	对象Goose没有 neck属性

## 5.访问限制

在类的内部可以定义属性和方法，而在类的外部可以直接调用属性以及方法，隐藏了类的内部的复杂逻辑。但是，对于类的访问权限进行限制。为了保证类内部的某些属性与方法不被外部访问，可以通过在属性或者方法前面添加`单下划线_`、`双下划线__`以及`首尾添加双下划线__foo__`,作用如下：

+ 单下划线。表示protected(保护)类型的成员，只能被类本身(例如下面的`Goose._neck`)、子类以及类的实例(例如下面的`wildGoose._neck`)进行访问，但是不能使用`from moudle import *`的方法导入。
+ 双下划线。表示private(私有)类型的成员，只能被类本身进行访问，但是不能被类的实例进行访问，但是可以通过`实例名._类名__xxx`的方式进行访问。
+ 首尾双下划线。表示定义的特殊方法，一般是系统定义的名字，例如`__init__()`。

 具体举例如下：

~~~python 
class Goose:
    'this is a goose!'
    # 创建一个保护型成员
    _neck='thin'
    _Goose_neck='long'
    # 创建一个私有型成员
    __leg='not long'
    # 在类的方法中直接调用保护型成员
    def __init__(self):
        print(Goose._Goose_neck+' and '+Goose.__leg)
	def fly(self):
        print(Goose._neck)
# 直接输出保护型成员
print(Goose._Goose_neck)
# 创建一个实例
wildGoose=Goose()
# 使用实例名来调用保护型成员
print(wildGoose._neck)
wildGoose.fly()
# 使用实例名调用私有型成员
print(wildGoose._Goose__leg)
~~~

## 6.计算属性

在这个小节里介绍的属性与上面提到的`类属性`和`实例属性`不一样，上面的属性就是保存一个值，并且可以返回值，本节介绍的属性可以用于计算，并且可以添加安全保护机制。

### 6.1 创建用于计算的属性

可以在一个方法前面加一个`@property`来把一个方法转化为属性，所以再次调用这个方法的时候就不需要在后面加小括号，让代码更加简洁，举例如下：

~~~python
class Goose:
    "this is a goose!"
    b=1
    def __init__(self):
        self.neck='thin'
        self.leg='long'
        pass
	@property
    def fly(self):
        a=self.neck+' '+self.leg+' '+str(Goose.b)
        return a
wildGoose=Goose()
print(wildGoose.fly)

~~~

### 6.2 创建属性保护机制

python 中创建的类属性或者方法在类体的外面是可以修改的，但是如果想要限制其不被修改，可以将其设置为private(私有型)的，但是设置为私有的后，在类体的外部不能轻易访问，所以

## 7.类的继承

### 7.1 继承

继承是面向对象编程最重要的特性之一，**一个类可以继承父类的所有公有成员（属性、方法）或者受保护成员**，并且可以创建自己独有的属性以及方法，被继承的类称为`父类`或者`基类`，新的类称之为`子类`或者`派生类`。

通过继承不仅可以实现代码的重用，还可以通过继承来处理类与类之间的关系，语法如下：

~~~python
class ClassName(BaseClassName):
    '类的帮助信息'
    statement
~~~

`ClassName`	子类的名称

`BaseClassName`	父类的名称

`statement`	类体，主要由类的属性以及方法组成，如果没有想好类体就可以使用`pass`代替

~~~python
class fruit:
    color='绿色'
    def harvest(self,color):
        print('水果是'+color+'的'+'!')
# 继承苹果类
class Apple(fruit):
    color='红色' 
    # 这里在Apple 中重新写了一个和父类的同名属性，对原属性进行了覆盖，如果删除这句话，那么 apple.color='绿色'
    def __init__(self):
        print('我是苹果！')
# 继承橙子类
class Orange(fruit):
    color='橙色'
    def __init__(self):
        print('我是橙子')
# 创建苹果实例
apple=Apple()
apple.harvest(apple.color)
# 创建橙子实例
orange=Orange()
orange.harvest(orange.color)
~~~

### 7.2 方法的重写

父类的所有方法与属性都会被子类所继承，但是有的方法不完全适合于子类，所以就需要在子类中重写父类的方法。就像前文已经提到过的，我已经定义了一个水果类，但是其中的`harvest`方法显得很单调，总数输出水果，但是我想在苹果中输出的是苹果，所以就可以在**苹果子类中对`harvest`方法进行重写,对父类的同名方法进行了覆盖**，举例如下：

~~~python
# 定义一个水果类
class fruit:
    color='绿色'
    def harvest(self,color):
        print('水果是'+color+'的'+'!')
# 定义一个苹果是水果的子类
class Apple(fruit):
    color='红色'
    def harvest(self,color):
        print('苹果原来是'+fruit.color+'的!')
        print('苹果已经熟了')
        print('苹果是'+color+'的!')
# 创建苹果实例
apple=Apple()
apple.harvest(Apple.color)
~~~

### 7.3 子类调用父类中的构造方法

在子类中调用基类的`__init__()`方法,不能直接调用，而是在子类的构造方法中应该以`super.__init__()`的方式进行调用，举例如下：

~~~python
class Fruit:
    def __init__(self,color='绿色'):
        Fruit.color=color
        # 在方法中，以类名.属性名的方式创建的属性也是类属性的一种,
        # 但是要进行调用，就必须先实例化，在方法中定义的类属性就需要先调用一次方法，才可以在类的内外进行调用
	def harvest(self,color):
        print('水果是：'+self.color+'的！')
        print('水果已经收获……')
        print('水果原来是：'+Fruit.color+'的!')
class Apple(Fruit):
    color='红色'
    print('我是苹果')
     def __init__(self):
        print('我是苹果')
        super().__init__()
class Sapodilla(Fruit):
    def __init__(self,color):
        print('我是人参果')
        super.__init__(color)
        # 在定义子类的构造方法的时候加了color参数，所以在调用父类的构造方法时需要加color参数
# 重写harvest方法
	def harvest(self,color):
        print('人参果是'+color+'的!')
        print('人参果已经成熟')
        print('人参果原来是:'+Fruit.color+'的!')
apple=Apple()
apple.harvest(apple.color)
sapodilla=Sapodilla('白色')
sapodilla.harvest('金黄色带紫色条纹')
~~~

在方法中，以类名.属性名的方式创建的属性也是类属性的一种,但是要进行调用，就必须先实例化，在方法中定义的类属性就需要先调用一次方法，才可以在类的内外进行调用，举例如下：

~~~python
class e:
    color='x'
    def __init__(self):
        e.size=11
    def goose(self):
        e.neck='long'
        print(e.size)
# 首先进行类的实例化与方法的调用
ex=e()
ex.goose()
print(ex.neck)
print(ex.size)
~~~



如果在子类中没有重写构造方法`__init()__`，在创建子类的实例的时候会直接调用父类的实例方法，举例如下：

~~~python
class fruit:
    def __init__(self):
        self.size=11
        self.shape='round'
        print(str(self.size)+' '+self.shape)
class apple(fruit):
    pass
# create an apple example
apple=apple()
~~~

运行结果为：`11 and round`

