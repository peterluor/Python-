# 格式化输出

## 1.大小写转换

对字符串使用一定的函数，完成**全大写**、**全小写**、**首字母大写**、**单词首字母大写**的操作

```Python 
a=input()
b=a.upper()		# 全部大写
c=a.lower()		# 全部小写
d=a.title()		# 单词首字母大写
e=a.capitalize()	# 字符串首字母大写
print(a,b,c,d)
```



## 2.删除空格

```Python
.strip() 		# 删除两边空格
.lstrip() 		# 删除左边空格
.rstrip() 		# 删除右边空格
.replace(" ","") 	# 删除所有空格
.split() --- 先切分，"".join() --- 再拼接
```

使用的例子如下：

