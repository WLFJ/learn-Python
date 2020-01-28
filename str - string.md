# str - string

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

//待补

### 文字处理系统专题

//待补

### 首字母大写

返回拷贝

`str.capitalize()`

### Unicode转小写

`str.casefold()`

德语ß将转换为ss，`lowercase()`不会处理

### 文本居中

`str.center(width[, fillchar])`

可以自定义填充的字符将文本放在中间显示。默认为ASCII空格

### 计数

统计串区间中不重复的子串出现次数

`str.count(sub[, start[, end]])`

区间使用切片描述

### 编码

`str.encode(encoding='utf-8', errors='strict')`

[详细编码信息](https://docs.python.org/3/library/codecs.html#standard-encodings),其中同时支持类似idna的编码。

返回bytes对象

errors属性见[`codecs.register_error()`](https://docs.python.org/3/library/codecs.html#codecs.register_error)。

