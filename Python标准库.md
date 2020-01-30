# Python标准库

## 操作系统

* os包

获取当前工作路径`getcwd()`

改变工作路径`chdir(path)`

执行系统命令`system(cmd)`

* shutil

方便处理日常文件操作

```python
shutil.copyfile
shutil.move
```

* glob

通配符获取文件列表

```python
glob.glob('*.py')
['primes.py', 'random.py', 'quote.py']
```

## 运行时参数

```python
import sys
>>> print(sys.argv)
['demo.py', 'one', 'two', 'three']
```

更高级的参数设置，不用自己写分词了

```python
import argparse

parser = argparse.ArgumentParser(prog = 'top',
    description = 'Show top lines from each file')
parser.add_argument('filenames', nargs='+')
parser.add_argument('-l', '--lines', type=int, default=10)
args = parser.parse_args()
print(args)
```

使用结果：

When run at the command line with `python top.py --lines=5 alpha.txt beta.txt`, the script sets `args.lines` to `5` and `args.filenames` to `['alpha.txt', 'beta.txt']`.

## 错误信息重定向以及程序退出

sys包中有stdin、stdout、stderr，可以使用相应的read或者write函数实现功能。

使用sys.exit()退出程序

## 正则表达式

* re

## 数学

* math

### 随机数

```python
>>> import random
>>> random.choice(['apple', 'pear', 'banana'])
'apple'
>>> random.sample(range(100), 10)   # sampling without replacement
[30, 83, 16, 4, 8, 81, 41, 50, 18, 33]
>>> random.random()    # random float
0.17970987693706186
>>> random.randrange(6)    # random integer chosen from range(6)
4
```

### 统计

```python
>>> import statistics
>>> data = [2.75, 1.75, 1.25, 0.25, 0.5, 1.25, 3.5]
>>> statistics.mean(data)
1.6071428571428572
>>> statistics.median(data)
1.25
>>> statistics.variance(data)
1.3720238095238095
```

## 网络

```python
>>> from urllib.request import urlopen
>>> with urlopen('http://tycho.usno.navy.mil/cgi-bin/timer.pl') as response:
...     for line in response:
...         line = line.decode('utf-8')  # Decoding the binary data to text.
...         if 'EST' in line or 'EDT' in line:  # look for Eastern Time
...             print(line)

# <BR>Nov. 25, 09:43:32 PM EST

>>> import smtplib
>>> server = smtplib.SMTP('localhost')
>>> server.sendmail('soothsayer@example.org', 'jcaesar@example.org',
... """To: jcaesar@example.org
... From: soothsayer@example.org
...
... Beware the Ides of March.
... """)
>>> server.quit()
```

## 时间和日期

```python
>>> # dates are easily constructed and formatted
>>> from datetime import date
>>> now = date.today()
>>> now
datetime.date(2003, 12, 2)
>>> now.strftime("%m-%d-%y. %d %b %Y is a %A on the %d day of %B.")
'12-02-03. 02 Dec 2003 is a Tuesday on the 02 day of December.'

>>> # dates support calendar arithmetic
>>> birthday = date(1964, 7, 31)
>>> age = now - birthday
>>> age.days
14368
```

## 压缩

Common data archiving and compression formats are directly supported by modules including: [`zlib`](https://docs.python.org/3/library/zlib.html#module-zlib), [`gzip`](https://docs.python.org/3/library/gzip.html#module-gzip), [`bz2`](https://docs.python.org/3/library/bz2.html#module-bz2), [`lzma`](https://docs.python.org/3/library/lzma.html#module-lzma), [`zipfile`](https://docs.python.org/3/library/zipfile.html#module-zipfile) and [`tarfile`](https://docs.python.org/3/library/tarfile.html#module-tarfile).

## 高效数据结构

### array

### collections

##### bisect

### heapq

### 浮点数

### decimal

