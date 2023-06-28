# 字符串的相互转换

常见的字符串编码主要有`utf-8`、`GBK`、`GB2312`以及`unicode`等，在`python`中常见的字符串类型有`str`以及`bytes`两种，这两种类型之间可以实现相互转换，不同的编码之间也可以实现转换。

## 1.字符串类型的转换

### 1.1 `str`——`bytes`的转换

使用`str.encode(encoding='utf-8',errors='strict')`实现`str`到`bytes`的转换，参数说明如下：

+ encoding 采用的编码方式，常见的有`utf-8`、`GBK`、`GB2312`以及`unicode`，默认值为`utf-8`。
+ errors 处理参数，`strict`:对非法字符抛出异常 `ignore`:忽视非法字符 `replace`:将非法字符使用`?`进行代替 `xmlcharrefreplace()`:使用`xml`引用（**至今没理解意思**）

举例如下：

~~~python
str='中文!'
bytes=str.encode(encoding='utf-8',errors='strict')
print(bytes)
~~~

## 1.2 `bytes`——`str`的转换

使用`bytes.decode(encoding='utf-8',errors='strict')`完成从`bytes`到`str`的转换，参数和`encode`一致，举例如下：

~~~python
bytes=b'\xe4\xb8\xad\xe6\x96\x87!'
str=bytes.decode(encoding='utf-8',errors='strict')
print(str)
~~~

