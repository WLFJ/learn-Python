print函数

变量

input函数 类型转换问题

字符串的三种表示方式

方括号运算符，注意前闭后开性质

格式化字符串 字符串开头使用f标记，中间使用{var}来说明使用的变量

长度函数

upper lower find replace方法，注意不会改变原字符串

title 智能转换成标题

bool表达式 ‘Python’ in course 类似于 o instanceof String一样，用于判断是否存在

使用/得到的是浮点结果，使用//得到的是整数结果

幂**

四舍五入round 绝对值abs

带入数学包 import math

向上取整ceil 向下取整floor

判断语句

```python
if tag:
  todo
elif tag2:
  todo
else:
  todo
'''使用缩进来说明是哪一个语句块'''
```

组合逻辑联结词and or

循环

whil语句也有else，会在自然结束的时候执行，使用break不会执行

for in 循环

使用数组，可以是 for a in [1, 2, 3]

还可以使用range函数 for a in range(10)

rang(开始， 结束， 步进)

二维矩阵

查看类型 type(obj)

list.append(num)

list.insert(pos, num)

List.remove

list.clear

list.pop

list.index

List.count

list.sort

list.reverse

list.copy

元组，不能改变的数组

unpack模式，使用x,y,z=(1,2,3) 简洁实现赋值

字典，使用{} 创建，可以使用中括号获取，也可以使用get方法安全获取

Str.splite()

定义函数

```python
def function(para):
  '''TODO'''
```

使用的时候，可以直接访问，或者使用变量名=val的形式

在混合使用时，第一个不能使用，后面的可以使用定义传参

返回值直接在设计函数时使用return就可以了

异常处理

```python
try:
  age = int(input("your age: "))
except ValueError:
  print("Invalid value.")
```

注释：使用#

类

```python
class Person:
  def __init__(self, name):
    self.name = name
  
  def talk(self):
    print(self.name)
```

注意：每一个方法的第一个参数都是self，变量不需要在里面声明

继承

```python
class Mammel:
  def func(self):
    print("Hello!")
    
class Dog(Mammel):
  def func(self):
    print("Wufe~")
    
class Cat(Mammel):
  pass

```

使用pass命令说明当前类是空的

导入包import xxx

导入函数或者对象 from xxx import yyy

python中的三级结构 package model function/class 活用from和import以导入我们需要的工具 as 代表简写

简化元组 return first，second