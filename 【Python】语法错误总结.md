# Python 语法错误总结

1. SyntaxError:**Invaild character** (in identifier)

   **表示在编辑器中使用了中文的符号**

2. **TypeError: Area() missing 1 required positional argument: 'b'**

   **表示调用函数的时候缺少参数**

3. SyntaxError: invalid syntax

​	表示在编写程序的过程中使用了Python的保留符号

4. `Example.__init__() takes 0 positional arguments but 1 was given`

表示在创建类中的`__init__()`方法的时候没有加必须的`self`参数

5. python setup.py egg_info did not run successfully

表示我们需要更新一下`setuptools`,pip install --upgrade setuptools
