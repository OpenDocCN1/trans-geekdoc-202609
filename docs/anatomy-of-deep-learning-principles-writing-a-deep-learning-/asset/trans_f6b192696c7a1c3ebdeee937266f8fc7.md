

当然，这种移动的步长（即 `-αf'(x)`）不能太大，因为根据导数的定义，上述近似公式仅适用于 `x` 附近。如果移动步长太大，可能会跳过 `x` 的最优值，导致 `x` 的值不断来回震荡。如图 2-6 所示。

![](EPUB/media/file26.png "fig:")

图 2-6 `x` 的变化量 `-αf'(x)` 过大，函数值将会震荡

梯度下降法是寻找近似最优解。为了避免无限迭代，可以使用以下方法来检查是否足够接近最优解：

*   导数（梯度）`f'(x)` 的绝对值足够小。
*   迭代次数已达到预设的最大迭代次数。

以下是梯度下降法的代码，其中参数 `df` 用于计算函数 `f(x)` 的导数 `f'(x)`，`x` 是变量的初始值，`alpha` 是学习率，`iterations` 表示迭代次数，`epsilon` 用于检查 `df=f'(x)` 的值是否接近 0。

```
def gradient_descent(df, x, alpha=0.01, iterations=100, epsilon=1e-8):
    history = [x]
    for i in range(iterations):
        if abs(df(x)) < epsilon:
            print("The gradient is small enough!")
            break
        x = x - alpha * df(x)
        history.append(x)
    return history
```

该梯度下降函数将迭代过程中所有更新的 `x` 保存在 Python 列表对象 `history` 中并返回该对象。

对于上述函数 `f(x) = x³ – 3x² – 9x + 2`，其导数 `f'(x) = 3x² – 6x – 9`。如果想求 `x = 1` 附近函数 `f(x)` 的最小值，可以调用此函数 `gradient_descent()`：

```
df = lambda x: 3*x**2 - 6*x - 9
path = gradient_descent(df, 1., 0.01, 200)
print(path[-1])
```

```
The gradient is small enough!
2.999999999256501
```

得到 `f(x)` 的极值点 `x = 2.999999999256501`。可以绘制迭代过程中 `x` 对应的曲线上的点：

```
f = lambda x: np.power(x, 3) - 3*x**2 - 9*x + 2
x = np.arange(-3, 4, 0.01)
y = f(x)
plt.plot(x, y)

path_x = np.asarray(path) # .reshape(-1, 1)
path_y = f(path_x)
plt.quiver(path_x[:-1], path_y[:-1], path_x[1:] - path_x[:-1], path_y[1:] - path_y[:-1], scale_units='xy', angles='xy', scale=1, color='k')
plt.scatter(path[-1], f(path[-1]))
plt.show()
```

![](EPUB/media/file27.png)

图 2-7 `x` 逐渐收敛到最小值点

其中，matplotlib 的 `quiver` 函数可以用箭头绘制速度向量，其函数格式为：

```
quiver([X, Y], U, V, [C], **kw)
```

其中 `X`、`Y` 为 1D 或 2D 数组，表示箭头的位置，`U`、`V` 为相同的 1D 或 2D 数组，表示箭头的速度（向量）。其他参数请参考官方文档。

对于多元函数，梯度下降法的原理相同，只是用梯度代替导数。

`f(x + Δx) − f(x) ≃ ∇f(x)Δx`

以下是来自维基百科的 Beale 函数。

`f(x, y) = (1.5 − x + xy)² + (2.25 − x + xy²)² + (2.625 − x + xy³)²`

该函数的全局最小值为 `(3, 0.5)`。可以使用以下 Python 代码计算函数值：

```
f = lambda x, y: (1.5 - x + x*y)**2 + (2.25 - x + x*y**2)**2 + (2.625 - x + x*y**3)**2
```

要绘制该曲面，首先在 `x` 和 `y` 轴上取一些均匀分布的坐标值：

```
xmin, xmax, xstep = -4.5, 4.5, .2
ymin, ymax, ystep = -4.5, 4.5, .2
x_list = np.arange(xmin, xmax + xstep, xstep)
y_list = np.arange(ymin, ymax + ystep, ystep)
```

然后根据上述 `x_list` 和 `y_list` 使用 `np.meshgrid()` 函数获取其交点处的网格点 `(x, y)`，并计算这些网格坐标点对应的函数值：

```
x, y = np.meshgrid(x_list, y_list)
z = f(x, y)
```

最后，可以调用 `plot_surface()` 函数绘制该曲面：

```
ax.plot_surface(x, y, z, norm=LogNorm(), rstride=1, cstride=1,
                edgecolor='none', alpha=.8, cmap=plt.cm.jet)
```

完整代码如下：

```
import numpy as np
import matplotlib.pyplot as plt
from mpl_toolkits.mplot3d import Axes3D
from matplotlib.colors import LogNorm
import random

%matplotlib inline

f = lambda x, y: (1.5 - x + x*y)**2 + (2.25 - x + x*y**2)**2 + (2.625 - x + x*y**3)**2

minima = np.array([3., .5])
minima_ = minima.reshape(-1, 1)

xmin, xmax, xstep = -4.5, 4.5, .2
ymin, ymax, ystep = -4.5, 4.5, .2
x_list = np.arange(xmin, xmax + xstep, xstep)
y_list = np.arange(ymin, ymax + ystep, ystep)
x, y = np.meshgrid(x_list, y_list)
z = f(x, y)

fig = plt.figure(figsize=(8, 5))
ax = plt.axes(projection='3d', elev=50, azim=-50)

ax.plot_surface(x, y, z, norm=LogNorm(), rstride=1, cstride=1,
                edgecolor='none', alpha=.8, cmap=plt.cm.jet)
ax.plot(*minima_, f(*minima_), 'r*', markersize=10)

ax.set_xlabel('$x$')
ax.set_ylabel('$y$')
ax.set_zlabel('$z$')

ax.set_xlim((xmin, xmax))
ax.set_ylim((ymin, ymax))

plt.show()
```

![](EPUB/media/file28.png)

图 2-8 绘制的 `f(x,y)` 曲面

`f(x, y)` 对 `x`、`y` 的偏导数为：

$\frac{\partial f(x,y)}{\partial x} = 2(1.5 - x + xy)(y - 1) + 2(2.25 - x + xy^{2})(y^{2} - 1) + 2(2.625 - x + xy^{3})(y^{3} - 1)$

$\frac{\partial f(x,y)}{\partial y} = 2(1.5 - x + xy)x + 2(2.25 - x + xy^{2})(2yx) + 2(2.625 - x + xy^{3})(3y^{2}x)$

可以使用 matplotlib 的 `quiver` 函数在二维坐标平面上绘制这些网格点处的梯度方向。

```
df_x = lambda x, y: 2*(1.5 - x + x*y)*(y-1) + 2*(2.25 - x + x*y**2)*(y**2-1) + 2*(2.625 - x + x*y**3)*(y**3-1)
df_y = lambda x, y: 2*(1.5 - x + x*y)*x + 2*(2.25 - x + x*y**2)*(2*x*y) + 2*(2.625 - x + x*y**3)*(3*x*y**2)
dz_dx = df_x(x, y)
dz_dy = df_y(x, y)

fig, ax = plt.subplots(figsize=(10, 6))

ax.contour(x, y, z, levels=np.logspace(0, 5, 35), norm=LogNorm(), cmap=plt.cm.jet)
ax.quiver(x, y, x - dz_dx, y - dz_dy, alpha=.5)
ax.plot(*minima_, 'r*', markersize=18)

ax.set_xlabel('$x$')
ax.set_ylabel('$y$')

ax.set_xlim((xmin, xmax))
ax.set_ylim((ymin, ymax))

plt.show()
```

![](EPUB/media/file29.png)

图 2-9 函数 `f(x,y)` 等值面的定域坐标等高线及网格点处的梯度方向

为了直接使用之前的梯度下降法代码，可以用 numpy 向量表示之前梯度下降法代码中的 `x`，并将

```
if abs(df(x)) < epsilon:
```

改为：

```
if np.max(np.abs(df(x))) < epsilon:
```

首先将分离的 `x` 和 `y` 坐标数组合并为一个数组：

```
print(x.shape)
print(y.shape)

x_ = np.vstack((x.reshape(1, -1), y.reshape(1, -1)))
print(x_.shape)
```

```
(46, 46)
(46, 46)
(2, 2116)
```

可以为这个向量化的坐标点 `x` 定义一个梯度函数 `df`。以下代码还给出了修改后的向量化版梯度下降算法的实现：

```
df = lambda x: np.array([
    2*(1.5 - x[0] + x[0]*x[1])*(x[1]-1) + 2*(2.25 - x[0] + x[0]*x[1]**2)*(x[1]**2-1)
    + 2*(2.625 - x[0] + x[0]*x[1]**3)*(x[1]**3-1),
    2*(1.5 - x[0] + x[0]*x[1])*x[0] + 2*(2.25 - x[0] + x[0]*x[1]**2)*(2*x[0]*x[1])
    + 2*(2.625 - x[0] + x[0]*x[1]**3)*(3*x[0]*x[1]**2)
])

def gradient_descent(df, x, alpha=0.01, iterations=100, epsilon=1e-8):
    history = [x]
    for i in range(iterations):
        if np.max(np.abs(df(x))) < epsilon:
            print("The gradient is small enough!")
            break
        x = x - alpha * df(x)
        history.append(x)
    return history
```

以下代码从 `x0 = (3., 4.)` 开始求解该曲面的极值点：

