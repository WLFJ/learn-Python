# Lists

## 数据结构

### Stack

使用`lists.pop()`弹出元素，使用`lists.append()`添加元素

### queue

使用`lists.popleft()`拿出队头元素，添加不变。

## 一些简洁的写法

### 创建映射类序列

```python
# 第一种写法，不理解map是什么
arr = list(map(range x : x ** 2, range(10)))

# 更加直观
arr = [x ** 2 for x in range(10)]
```

### 创建判断类

```python
# 甚至可以简化二重循环
[(x, y) for x in [1, 2, 3] for y in [3, 1 , 4] if x != y]
```

从上面的设计我们可以看出，先操作、后循环、最后判断。

问题：矩阵转制

```python
matrix = [
  [1, 2, 3, 4].
  [5, 6, 7, 8]
]
[ [row[i] for row in matrix] for i in range(4) ]
```

还可以使用zip函数，性能更好

```python
list(zip(*matrix))
```

在遍历时候同时取出下标

```python
for x, y in enumerate(range(10)):
  	print('{x} -> {y}')
```

其中x为下标，y是列表中的值

同时便利两个iterable

```python
list_a = [1, 2, 3, 4]
list_b = [5, 6, 7, 8]
for a, b in zip(list_a, list_b):
  	print(f'when a is {a}, b is {b}')
```

想要反着遍历，使用`reversed(iterable)`

排序过的同理。



