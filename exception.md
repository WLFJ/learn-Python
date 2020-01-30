# exception

注意与Java的区别，在捕获时使用except而不是catch

使用raise关键字产生异常

想要获得异常中的详细信息，使用下面的方式：

```python
try:
  raise Exception('arg1', 'arg2')
except Exception as exp:
  print(exp)
  x, y = exp.args
  raise # 无法处理则再次向外界抛出
```

如果捕获的异常无法处理，则再次raise

## 自定义异常

```python
class Error(Exception):
  '''当前类所有异常的基类'''
  pass

class InputError(Error):
  '''当输入的内容不支持时产生异常
  
  Attributes:
  	expression -- 输入的内容
  	message -- 错误原因
  '''
  def __init__(self, expression, message):
    self.expression = expression
    self.message = message
```

