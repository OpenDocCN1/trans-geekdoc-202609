

#### 5. astype() 和 reshape()

`ndarray` 的 `astype()` 方法将 `ndarray` 对象的元素数据类型转换为另一种数据类型，例如将上述数组的元素类型从 numpy 的 `int32` 转换为 numpy 的 `float64` 类型：

```python
a = np.array([[1,2,3],[4,5,6]]) 
b = a.tolist()
print(type(b))
print(b)
```

```
<class 'list'>
[[1, 2, 3], [4, 5, 6]]
```

```python
c = a.astype(np.float64)   
print(a.dtype, c.dtype)
a[0][0] = 100
print(a)
print(c)
```

```
int32 float64
[[100 2 3]
 [ 4 5 6]]
[[1. 2. 3.]
 [4. 5. 6.]]
```

numpy 的 `reshape()` 函数或 `ndarray` 的 `reshape()` 方法可以通过改变 `ndarray` 对象的形状来创建一个新的 `ndarray` 对象，例如：

```python
a = np.array(range(6))       # 从可迭代对象创建张量
b = np.reshape(a, (2, 3))    # 创建一个形状为 (2, 3) 的新张量
c = a.reshape(2, 3).astype(np.float64)
print(a)
print(b)
print(c)
```

```
[0 1 2 3 4 5]
[[0 1 2]
 [3 4 5]]
[[0. 1. 2.]
 [3. 4. 5.]]
```

#### 6. arange() 和 linspace()

`arange()` 函数通过指定起始值、结束值和步长来创建一个表示等差数列的一维数组。其函数规范如下：

`numpy.arange([start], stop, [step], dtype=None)`

等差数列元素的初始值为 `start`，公差为 `step`（也称为步长），直到 `stop`（但不包含 `stop`）。数据元素类型可指定为 `dtype`。`start` 的默认值为 0，`step` 的默认值为 1，`dtype` 的默认值为 `None`，这些都可以省略。注意结果数组不包含最终值。

```python
print(np.arange(5))    # 仅指定结束值，start 和 step 默认为 0 和 1
print(np.arange(2, 5))
print(np.arange(2, 7, 2))
```

```
[0 1 2 3 4]
[2 3 4]
[2 4 6]
```

与 `arange()` 类似，`linspace()` 也用于在初始值和最终值之间创建等差数列，不同之处在于它的第三个参数不是步长，而是创建的元素个数。

`numpy.linspace(start, stop, num=50, endpoint=True, retstep=False, dtype=None)`

`linspace()` 在 `start` 和 `stop` 之间创建一个包含 `num` 个数的等差数列。`endpoint` 表示是否包含 `stop`。

```python
np.linspace(2.0, 3.0, num=5, endpoint=False)
```

```
array([2. , 2.2, 2.4, 2.6, 2.8])
```

```python
np.linspace(2.0, 3.0, num=5)
```

```
array([2. , 2.25, 2.5 , 2.75, 3. ])
```

与 `linspace` 类似，`logspace()` 创建等比数列。

`logspace()` 首先在 `start` 和 `stop` 之间生成一个等差数列，然后以 `base`（`base` 的默认值为 10）为底，将这些数作为指数生成等比数列作为创建的 numpy 数组的元素。此方法等价于：

```python
y = numpy.linspace(start, stop, num=num, endpoint=endpoint)
numpy.power(base, y).astype(dtype)
```

例如：

```python
np.logspace(2.0, 3.0, num=5)
```

```
array([ 100. , 177.827941 , 316.22776602, 562.34132519,
        1000. ])
```

```python
np.logspace(2.0, 3.0, base=3, num=5)
```

```
array([ 9. , 11.84466612, 15.58845727, 20.51556351, 27. ])
```

#### 7. full(), empty(), zeros(), ones(), eye()

`full()` 填充函数创建一个指定值为 `fill_value`、形状为 `shape` 的数组。

`numpy.full(shape, fill_value, dtype=None, order='C')`

例如：

```python
np.full((2, 3), np.inf)
```

```
array([[inf, inf, inf],
       [inf, inf, inf]])
```

```python
np.full((2, 3), 3.5)
```

```
array([[3.5, 3.5, 3.5],
       [3.5, 3.5, 3.5]])
```

与 `full()` 函数类似，numpy 的 `empty()`、`zeros()`、`ones()` 和 `eye()` 分别创建未初始化数组、值为 0 的数组、值为 1 的数组，以及对角线为 1 其余为 0 的数组。

```python
numpy.empty(shape, dtype=float, order='C')
numpy.zeros(shape, dtype=float, order='C')
numpy.ones(shape, dtype=None, order='C')
numpy.eye(N, M=None, k=0, dtype=<class 'float'>, order='C')
```

```python
print(np.empty((2, 3)), '\n')  # 创建一个形状为 (2, 3) 的二维数组，
                               # 相当于一个 2*3 矩阵。
                               # 元素的值未初始化
print(np.zeros((2, 3)), '\n')  # 创建一个形状为 (2, 3) 的二维数组
                               # 其元素值全为 0，相当于一个 2*3 矩阵
print(np.ones((1, 2)), '\n')   # 创建一个形状为 (1, 2) 的二维数组
                               # 其元素值全为 1
print(np.eye(2), '\n')         # 创建一个形状为 (2, 2) 的单位矩阵，即
                               # 对角线元素值为 1，其他元素值为 0 的矩阵
```

```
[[3.5 3.5 3.5]
 [3.5 3.5 3.5]]

[[0. 0. 0.]
 [0. 0. 0.]]

[[1. 1.]]

[[1. 0.]
 [0. 1.]]
```

#### 8. 创建随机值张量的常用函数

`numpy.random` 模块提供了多个用于创建值为随机数的张量的函数。例如：

*   `numpy.random.rand(d0, d1, ..., dn)` 创建一个指定形状 `(d0, d1, ..., dn)` 的随机数数组，其值在 `[0, 1]` 区间内均匀采样。
*   `numpy.random.random(shape)` 创建一个形状为 `shape`、值在区间 `[0, 1]` 内均匀采样的随机数数组。`shape` 是一个表示各维度元素个数的元组对象。
*   `numpy.random.randn(d0, d1, ..., dn)` 创建一个指定形状 `(d0, d1, ..., dn)` 的随机数数组，其值为高斯采样（标准正态分布）。
*   `numpy.random.normal(loc=0.0, scale=1.0, size=None)` 生成值按正态分布 `N(loc, scale)` 采样的随机数或数组。
    `size` 默认为 `None`，表示生成单个值。如果是整数，表示创建一维数组。如果是元组，表示创建由元组指定形状的多维数组。
*   `numpy.random.randint(low, high, size, dtype)` 创建一个类型为 `size`、值在 `low` 和 `high` 之间、类型为 `dtype` 的随机整数数组。`dtype` 可以是 `int64` 或 `int`。

例如，以下代码创建一个形状为 `(2, 3)` 的二维数组：

```python
np.random.rand(2, 3)
```

```
array([[0.77752078, 0.90528037, 0.03474023],
       [0.74134429, 0.53963193, 0.12413591]])
```

注意：`rand()` 直接传递一系列表示各维度元素个数的整数，而 `random()` 传递一个表示各维度元素个数的元组对象。

```python
e = np.random.random((2, 3))  # 创建一个形状为 (2, 3) 的二维数组
                              # 其元素值全为 [0, 1] 之间的随机数
print(e)   
```

```
[[0.09472091 0.21267183 0.05193963]
 [0.16334292 0.20288691 0.89140325]]
```

以下代码创建一个遵循（标准）高斯分布的一维或二维数组。

