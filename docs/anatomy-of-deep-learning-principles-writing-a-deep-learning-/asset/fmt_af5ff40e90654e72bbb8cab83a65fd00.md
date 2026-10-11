
## NumPy 随机数生成与数组操作

### 随机数生成

```python
a = np.random.randn(5)         # Generate a one-dimensional array of 5 random numbers 
                                # that obey the (0,1) standard normal distribution
b = np.random.randn(2,3)       # Generate a two-dimensional array of random numbers whose shape is (2,3)
                               # and follows (0,1) standard normal distribution
print("a:",a)
print("b:",b)
c = np.random.normal(0,1,5)     #Generate 5 one-dimensional arrays of random numbers that 
                                  #obey the (0,1) standard normal distribution
d = np.random.normal(size=(2,3))  # Generate a two-dimensional array of random numbers whose size 
                                 # is (2,3) subject to (0,1) standard normal distribution
e = np.random.normal(2,0.3,size=(2,3)) # Generate a two-dimensional array of random numbers whose size 
                                        #is (2,3) subject to (2,0.3) normal distribution
print("c:",c)
print("d:",d)
print("e:",e)

print(a.shape,b.shape,c.shape,d.shape)
```

输出结果：

```
a: [ 0.19371118 -1.15554198 1.19635313 0.79492457 0.87414178]
b: [[ 0.00880117 -0.75877358 -0.64144633]
    [ 1.04679662 0.24226954 0.34902206]]
c: [-0.43792241 0.8093157 -1.18669693 -1.37376709 -1.3847464 ]
d: [[-0.6863099 0.24868581 -0.5864114 ]
    [ 2.26636543 -1.24958728 -1.78229482]]
e: [[2.12434416 1.97693289 2.12858001]
    [1.69272355 1.89084818 2.15927248]]
(5,) (2, 3) (5,) (2, 3)
```

标准正态分布和正态分布都描述了随机变量取不同值的概率（将在后续概率知识中介绍）。随机变量 `x` 服从正态分布，其概率密度函数为：

$$N(x;\mu,\sigma^{2}) = \frac{1}{\sqrt{2\pi\sigma^{2}}}e^{- \frac{(x - \mu)^{2}}{2\sigma^{2}}}$$

描述了 `x` 取不同值的概率，其中 `x` 取值为 `μ` 的概率最高，离 `μ` 越远的值取到的概率越小。当 `μ=0, σ=1` 时，正态分布称为标准正态分布。标准正态分布的概率密度为：

$$N(x;0,1) = \frac{1}{\sqrt{2\pi}}e^{- \frac{x^{2}}{2}}$$

`randn()` 只能根据标准高斯分布创建随机采样的多维数组，而 `normal()` 可以根据一般高斯分布创建随机采样的多维数组。它们可以相互转换。如果 `x` 服从一般正态分布：`x ∽ N(μ, σ)`，通过变量代换：

$$z = \frac{x - \mu}{\sigma}$$

可以将其转换为变量 `z` 的标准正态分布 `z ∽ N(0, 1)`。

```python
mu, sigma = 2, 0.3
e = np.random.normal(mu, sigma,size=(2,3)) 
print(e)
f = np.random.randn(2,3) 
print(f)
g = f*sigma+mu            # f= (g-mu)/sigma obeys standard normal distribution, 
                             # g obeys (mu,sigma) Gaussian distribution
print(g)
```

输出结果：

```
[[2.34166242 1.98567633 2.21305203]
 [2.37320838 1.7396114 1.62458515]]
[[ 0.14297945 -1.29341937 0.44674436]
 [ 0.7630391 0.49162644 0.43494297]]
[[2.04289383 1.61197419 2.13402331]
 [2.22891173 2.14748793 2.13048289]]
```

某些随机数函数也有别名。例如，`random()` 函数有一个别名函数 `random_sample()`，即两者是同一个函数，都生成在 `[0,1]` 区间内均匀采样的随机数。如果要生成 `[a,b]` 区间内均匀采样的随机数，只需对生成的数组做简单的线性变换。例如：`(b - a) * random_sample() + a` 可以生成区间 `[a,b]` 内的随机数数组。下面的代码创建一个 `[2,7]` 之间的随机数数组。

```python
5 * np.random.random_sample((2, 3)) + 2
```

### 9. 添加、重复与铺设、合并与分割、边缘填充、添加轴与交换轴

之前看到通过 `ndarray` 的 `astype()` 和 `reshape()`，通过改变数据元素类型或改变张量形状来创建新张量（数组）。NumPy 还有许多函数或方法，通过对现有数组进行添加、重复、铺设、合并、分割、添加轴、交换轴等操作来创建新的 `ndarray` 对象。

#### 追加 append()

NumPy 的 `append()` 可以向现有数组添加内容以创建新数组，其函数规范为：

```python
numpy.append(arr, values, axis=None)
```

表示在数组 `arr` 后添加 `values` 的内容，`axis` 表示沿哪个轴添加，默认为 `None`，将创建一个扁平化（flattened）的一维数组。

```python
a = np.array([1,2,3])
b = np.append(a,4)
print(a)
print(b)
np.append([1, 2, 3], [[4, 5, 6], [7, 8, 9]])
```

输出结果：

```
[1 2 3]
[1 2 3 4]
array([1, 2, 3, 4, 5, 6, 7, 8, 9])
```

```python
np.append([[1, 2, 3], [4, 5, 6]], [[7, 8, 9]], axis=0)
```

输出结果：

```
array([[1, 2, 3],
       [4, 5, 6],
       [7, 8, 9]])
```

#### 重复 repeat()

`repeat()` 函数通过沿某个轴重复数组中的元素来创建新的 `ndarray` 数组。

```python
numpy.repeat(a, repeats, axis=None)
```

创建一个新数组，沿 `axis` 轴将 `a` 的元素重复 `repeats` 次。`axis` 的默认值为 `None`，意味着创建一个扁平化（flattened）数组。

```python
np.repeat(3, 4)   # Create an array, repeat the value 3 4 times,
```

输出结果：

```
array([3, 3, 3, 3])
```

```python
a = np.array([[1,2],[3,4]])
np.repeat(a, 2)             # Create a flattened array, that is, a one-dimensional array, 
                            # in which the elements in x are repeated twice
```

输出结果：

```
array([1, 1, 2, 2, 3, 3, 4, 4])
```

```python
np.repeat(a, 2, axis=0)   
```

输出结果：

```
array([[1, 2],
       [1, 2],
       [3, 4],
       [3, 4]])
```

`np.repeat(a, 2, axis=0)` 表示在 `axis=0` 方向上将每个元素（即每行）重复两次，`np.repeat(a, 2, axis=1)` 表示沿 `axis=1` 将每 1 列重复 2 次。

```python
np.repeat(a, 2, axis=1)   
```

输出结果：

```
array([[1, 1, 2, 2],
       [3, 3, 4, 4]])
```

#### 铺设 tile()

与 `repeat` 在每个轴方向重复元素不同，铺设函数 `tile(A, reps)` 可以像瓷砖一样垂直或水平地复制整个数组。

```python
numpy.tile(A, reps)
```

`A` 是要铺设的数组，`reps` 表示每个轴的重复次数。如果 `reps` 的长度小于 `A.ndim`，例如形状为 `(2, 3, 4, 5)`，而 `rep=(2,2)`，则 `rep` 数组会在前面补齐 1 变为 `(1,1,2,2)`。如果 `A.ndim` 小于 `reps` 的长度，`A` 会被提升为与 `reps` 形状相同的数组。如果一维张量 `A` 的形状为 `(3,)`，且 `reps=(2,2)`，则 `A` 将被视为形状为 `(1,3)` 的二维张量。

```python
a = np.array([1, 2,3])
b = np.tile(a, 2)    # a is Repeated 2 times to create a new array
print(a)
print(b)
```

输出结果：

```
[1 2 3]
[1 2 3 1 2 3]
```

当按照形状 `(2, 2)` 铺设数组 `a` 时，会先将 `a` 从一维张量 `[1, 2, 3]` 提取为二维张量 `[[1, 2, 3]]`，然后进行铺设：

```python
np.tile(a, (2, 2))   # a is tiled in 2 rows and 2 columns, creating a new array
```

输出结果：

```
array([[1, 2, 3, 1, 2, 3],
       [1, 2, 3, 1, 2, 3]])
```

例如，下面 `c` 的形状为 `(1, 2)`，`reps=2` 的长度为 1，`reps` 会先变为 `(1,2)`，然后铺设，即 `axis=0` 重复一次（即行方向保持不变），`axis=1` 重复 2 次。

```python
c = np.array([[1, 2], [3, 4]])
print(c)
np.tile(c, 2)        # reps will change to (1,2) first, indicating that 
                     # the first axis repeats once, and the second axis repeats twice
```

输出结果：

```
[[1 2]
 [3 4]]
array([[1, 2, 1, 2],
       [3, 4, 3, 4]])
```

下面的情况恰好相反：

```python
np.tile(c, (2, 1))
```

输出结果：

```
array([[1, 2],
       [3, 4],
       [1, 2],
       [3, 4]])
```
