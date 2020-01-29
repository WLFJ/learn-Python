# str - string

[TOC]

## 构造函数

```python
class str(object='')
```

如果传入对象，则会调用其`object.__str___()`方法返回精美文字。

```python
class str(objrct=b'', encoding='utf-8', errors='strict')
```

传入字节对象，将其按照格式编码。

## 方法

支持所有序列操作。

### 格式化

`str.format(*args, **kwargs)`

```python
>>> "The sum of 1 + 2 is {0}".format(1+2)
'The sum of 1 + 2 is 3'
# 可以传入多个参数，分别对应0开始的下标
```

在使用类型转换时系统会临时将LC_CTYPE设置为LC_NUMERIC来进行本地化计算，这可能影响到其他线程。

在传入数组或者字典时前面要加上对应的星号

```python
user = {'name' : "Tom", 'age' : 15}
'{name} 的年龄是：{age}'.format(**user)
```

#### 参数使用字典映射

`str.format_map(mapping)`

通常实现`__missing__(self, key)`处理格式串中不存在的key

```python
>>> class Default(dict):
...     def __missing__(self, key):
...         return key
...
>>> '{name} was born in {country}'.format_map(Default(name='Guido'))
'Guido was born in country'
```

### *文字处理系统专题

//待补

### 填充

#### 文本居中

`str.center(width[, fillchar])`

可以自定义填充的字符将文本放在中间显示。默认为ASCII空格

#### 右边填充

`str.ljust(width[, fillchar])`

#### 左边填充

`str.rjust(width[, fillchar])`

#### 左添0

`str.zfill(width)`

```python
>>> "42".zfill(5)
'00042'
>>> "-42".zfill(5)
'-0042'
```

### 删除

`str.strip([chars])`

#### 左边删除

`str.lstrip([chars])`

从左边开始删除，不传东西则删除空格，否则从左相右删除集合中的元素，直到遇到不是结合中的为止。

```python
>>> '   spacious   '.lstrip()
'spacious   '
>>> 'www.example.com'.lstrip('cmowz.')
'example.com'
```

#### 右边删除

`str.rstrip([chars])`

### 统计

统计串区间中不重复的子串出现次数

`str.count(sub[, start[, end]])`

区间使用切片描述

### 编码

`str.encode(encoding='utf-8', errors='strict')`

[详细编码信息](https://docs.python.org/3/library/codecs.html#standard-encodings),其中同时支持类似idna的编码。

返回bytes对象

errors属性见[`codecs.register_error()`](https://docs.python.org/3/library/codecs.html#codecs.register_error)。

### 判断匹配

#### 查开头是否匹配

`str.startswith(suffix[, start[, end]])`

#### 查结尾是否匹配

`str.endswith(suffix[, start[, end]])`

可以传入元组，存在后缀则返回True。

区间使用闭区间描述。

### 查找

`str.find(sub[, start[, end]])`

返回子串第一次出现的下标，-1代表不存在。

等价运算符为`in`

`str.index(sub[, start[, end]])`

同上，找不到时产生错误'ValueError'

#### 从右边开始查找

`str.rfind(sub[, start[, end]])`

`str.rindex(sub[, start[, end]])`

### 判断类型

空串为False

#### 广义数字

罗马字符、汉字等都算。

`str.isalnum()`

#### 字母

这里判断的是Unicode character database中定义的字母，于是汉字也是字母！

`str.isalpha()`

#### ASCII

串为空或者使用ASCII表示则为True

`str.isascii()`

ASCII范围为U+000-U+007F

#### 十进制数字描述

全角数字（双字节）也为True，其他语言的十进制数字也接受。

`str.isdecimal()`

所有接受的文字在Unicode General Category “Nd”。

#### 带自描述字符的数字

某些语言中为了说明数字，中间出现不是数字的字符。

`str.isdigit()`

#### 语言标识符

符合变成语言规范的串

`str.isidentifier()`

#### 小写

`str.islower()`

#### 大写

`str.isupper()`

#### numeric

`str.isnumeric()`

#### 可打印字符

`str.isprintable()`

#### 空格

`str.isspace()`

#### 标题大小写格式

`str.istitle()`

### 连接

`str.join(iterable)`

将序列中的内容使用str拼接后返回。

### 分割

#### 字符分割

`str.split(sep = None, maxsplit = -1)`

sep也可以是字符串。

#### 右字符分割

`str.split(sep = None, maxsplit = -1)`

#### 子串分割

以串为参照分成前中后三部分

`str.partition(sep)`

以串第一次出现的位置下手，如果sep存在，则返回三元组(串前，串本身，串后)，否则返回(串本身,'','')

#### 右子串分割

`str.rpartition(sep)`

#### 行分割

`str.splitlines([keepends])`

对字符串按照换行符分割，可选保留每一行末尾的换行标记keepends = True

| 标识           | Description                 |
| :------------- | :-------------------------- |
| `\n`           | Line Feed                   |
| `\r`           | Carriage Return             |
| `\r\n`         | Carriage Return + Line Feed |
| `\v` or `\x0b` | Line Tabulation             |
| `\f` or `\x0c` | Form Feed                   |
| `\x1c`         | File Separator              |
| `\x1d`         | Group Separator             |
| `\x1e`         | Record Separator            |
| `\x85`         | Next Line (C1 Control Code) |
| `\u2028`       | Line Separator              |
| `\u2029`       | Paragraph Separator         |

```python
>>> 'ab c\n\nde fg\rkl\r\n'.splitlines()
['ab c', '', 'de fg', 'kl']
>>> 'ab c\n\nde fg\rkl\r\n'.splitlines(keepends=True)
['ab c\n', '\n', 'de fg\r', 'kl\r\n']
```

与字符分割不同，其最后不会产生空字符

```python
>>> "".splitlines()
[]
>>> "One line\n".splitlines()
['One line']

>>> ''.split('\n')
['']
>>> 'Two lines\n'.split('\n')
['Two lines', '']
```

### 转换

#### 替换

`str.replace(old, new[, count])`

count为替换次数

`str.translate(table)`

传入的对象需要实现`__getitem__()`,使用str的函数-制作字典，可以方便创建。

#### 反转

`str.swapcase()`

大写变小写，vise versa。

#### tab格式化处理

`str.expandtabs(tabsize=8)`

返回拷贝，将串中的Tab（\t）用若干个空格代替，其输出会尽可能匹配列。如果当前位置到下一列的距离小于tabsize，则会对齐下一个列位置，如果下一个位置超过tabsize，则会按照tabsize输出。

其输出空格数量小于等于tabsize

```python
>>> '01\t012\t0123\t01234'.expandtabs()
'01      012     0123    01234'
>>> '01\t012\t0123\t01234'.expandtabs(4)
'01  012 0123    01234'
```

#### 首字母大写

返回拷贝

`str.capitalize()`

#### Unicode转小写

`str.casefold()`

德语ß将转换为ss，`lower()`不会处理

#### 转小写

`str.lower()`

#### 转大写

`str.upper()`

#### 转标题

`str.title()`

但是这个算法并不聪明，如果要处理有apostrophes的情况，使用正则表达式。

```python
>>> import re
>>> def titlecase(s):
...     return re.sub(r"[A-Za-z]+('[A-Za-z]+)?",
...                   lambda mo: mo.group(0).capitalize(),
...                   s)
...
>>> titlecase("they're bill's friends.")
"They're Bill's Friends."
```

## 函数

### 制作映射字典

`str.maketrans(x[, y[, z]])`

一个参数——必须传入字典，<Unicode编号, Char>或者<Char,Char>，返回<Unicode编号, Char>字典。

两个参数——两个串的长度必须相同，会从前串对应位置映射到后串对应位置。

三个参数——在两个的基础上，指定失配时的替换

## Python推荐的字符串格式化

花括号包扩表达式，要显示花括号使用`{{}}。

格式为：`{表达式!转换函数:内嵌属性}`

```python
>>> name = "Fred"
>>> f"He said his name is {name!r}."
"He said his name is 'Fred'."
>>> f"He said his name is {repr(name)}."  # repr() is equivalent to !r
"He said his name is 'Fred'."
>>> width = 10
>>> precision = 4
>>> value = decimal.Decimal("12.34567")
>>> f"result: {value:{width}.{precision}}"  # nested fields
'result:      12.35'
>>> today = datetime(year=2017, month=1, day=27)
>>> f"{today:%B %d, %Y}"  # using date format specifier
'January 27, 2017'
>>> number = 1024
>>> f"{number:#0x}"  # using integer format specifier
'0x400'
```

转换函数可以指定为：`!s for str()` `!a for ascii` `!r for repr()`

里面不能含有反斜杠，必须添加则将其抽出成变量传入。

格式化字符串不能用来生成文档。

#### 内嵌属性说明

`[[填充字符]填充方法][数字标记][是否添加前缀#][0][长度][分组标志][.精度][类型]`

* 填充方法

> | Option | Meaning                                                      |
> | :----- | :----------------------------------------------------------- |
> | `'<'`  | Forces the field to be left-aligned within the available space (this is the default for most objects). |
> | `'>'`  | Forces the field to be right-aligned within the available space (this is the default for numbers). |
> | `'='`  | 在标志和数字中间默认填充0                                    |
> | `'^'`  | Forces the field to be centered within the available space.  |

* 数字标记

| Option | Meaning                                                      |
| :----- | :----------------------------------------------------------- |
| `'+'`  | indicates that a sign should be used for both positive as well as negative numbers. |
| `'-'`  | indicates that a sign should be used only for negative numbers (this is the default behavior). |
| space  | 正数显示空格，负数显示负号                                   |

* 是否添加前缀

对于Hex 和 Oct类型，在前面添加0x或者0o

* 分组标志

`,or_`

* 类型

| Type  | Meaning                                                      |
| :---- | :----------------------------------------------------------- |
| `'b'` | Binary format. Outputs the number in base 2.                 |
| `'c'` | Character. Converts the integer to the corresponding unicode character before printing. |
| `'d'` |                                                              |
| `'o'` |                                                              |
| `'x'` |                                                              |
| `'X'` |                                                              |
| `'n'` | 与d相同                                                      |
| None  | d                                                            |

| Type  | Meaning                                               |
| :---- | :---------------------------------------------------- |
| `'e'` | 科学计数法，默认精度为6                               |
| `'E'` |                                                       |
| `'f'` |                                                       |
| `'F'` |                                                       |
| `'g'` | 根据大小自动转换为浮点保留或者科学计数法。默认精度为6 |
| `'G'` |                                                       |
| `'n'` | 同g，不过是本地化的                                   |
| `'%'` | 百分数                                                |
| None  | 同g。在小数上至少保留一位，并且会以合适的精度显示数字 |