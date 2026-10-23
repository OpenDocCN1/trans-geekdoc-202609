

由于我们的模型架构更复杂，预计会达到更高的准确率。

```python
learner = Learner(dataloaders,
                  model,
                  loss_func=CrossEntropyLossFlat(),
                  metrics=accuracy)
```

```python
learner.lr_find()
SuggestedLRs(lr_min=0.33113112449646,
             lr_steep=0.25118863582611084)
```

![](img/d5454da46c702784893ef8b0b539e5b9_54_0.png)

```python
learner.fit_one_cycle(3, lr_max=1e-1)
```

| 轮次 | 训练损失 | 验证损失 | 准确率 | 时间 |
|---|---|---|---|---|
| 0 | 0.162144 | 0.217495 | 0.931700 | 00:14 |
| 1 | 0.080546 | 0.071929 | 0.976100 | 00:14 |
| 2 | 0.040013 | 0.025664 | 0.991300 | 00:14 |

太棒了！我们的模型仅运行了 4 个训练轮次后，准确率就达到了约 0.99。不过，对于 ResNet 来说，MNIST 数据确实是一个非常简单的任务。

### 2.3 深入探究源代码

在第一章中，我们使用了 `cnn_learner` 函数。但这个函数具体做了什么呢？在 Jupyter Notebook 中，有一个非常方便的功能：只需在任何类或方法名称前面加上双问号，就可以直接进入源代码。根据你所运行的环境，notebook 的帮助信息会以浮动窗口的形式打开，或显示在 notebook 底部。

```python
??cnn_learner
```

有时这可能有点难读——尤其是对于较长的类。不过我们可以看到几个部分：

- **签名：** 这里显示了构造函数的所有参数和默认值
- **源码：** 显示实现
- **文件：** 显示包含源代码的文件路径
- **类型：** 显示实现的类型

我们可以直接进入 fastai 仓库，打开 vision 包中的 `learner.py` 文件。这是链接（*这个链接将来可能会改变*）：https://github.com/fastai/fastai/blob/master/fastai/vision/learner.py

如果我们分析源代码，就会看到幕后发生的事情：

- 1. 函数获取一些模型架构：`meta = model_meta.get(arch, _default_meta)`
- 2. 它构建模型：`model = create_cnn_model(arch, n_out, ifnone(cut, meta['cut']), pretrained, n_in=n_in, y_range=y_range, **config)`
- 3. 它从基础 `Learner` 类创建一个实例：`learn = Learner(dls, model, loss_func=loss_func, splitter=ifnone(splitter, meta['split']), **kwargs)`

现在，如果我们想进一步研究，可以查看 `Learner` 做了什么。

由于 fastai 是使用名为 `nbdev` 的库开发的，因此每个类都有一个对应的 notebook，其中包含源代码、文档以及一些测试用例，你可以打开该 notebook 运行这些用例。

只需进入仓库的 `nbs` 文件夹，然后打开 `21_vision.learner.ipynb` 文件即可。

我会从那里复制一些源代码，但请记住，每次 fastai 库更新时，这个 notebook 都会被修改，所以我复制的源代码可能与仓库中的最新版本有所不同。

我们再来看另一个例子。我们已经使用过 `PILImageBW` 类。现在，让我们使用 `??PILImageBW` 命令来研究这个类。我们可以看到这个类是在一个名为 `...vision/core.py` 的文件中实现的。让我们打开相应的 notebook 文件：`... nbs/07_vision.core.ipynb`。

```python
??PILImageBW
```

```
Init signature: PILImageBW(self)
Docstring:
This class represents an image object. To create
:py:class:`PIL.Image.Image` objects, use the appropriate factory
functions. There's hardly ever any reason to call the Image constructor
directly.

* :py:func:`PIL.Image.open`
* :py:func:`PIL.Image.new`
* :py:func:`PIL.Image.frombytes`
Source: class PILImageBW(PILImage): _show_args, _open_args = {'cmap':'Greys'}, {'mode':'L'}
File: ~/anaconda3/envs/fastai2/lib/python3.7/site-packages/fastai2/vision/core.py
Type: BypassNewMeta
Subclasses:
```

我们看到 `PILImageBW` 建立在 `PILImage` 类之上，而 `PILImage` 又建立在 `PILBase` 类之上：

```python
class PILImage(PILBase): pass

class PILImageBW(PILImage):
    _show_args, _open_args = {'cmap':'Greys'}, {'mode': 'L'}

class PILBase(Image.Image, metaclass=BypassNewMeta):
    _bypass_type = Image.Image
    _show_args = {'cmap':'viridis'}
    _open_args = {'mode': 'RGB'}

    @classmethod
    def create(cls, fn:(Path,str,Tensor,ndarray,bytes), **kwargs)->None:
        "Open an `Image` from path `fn`"
        if isinstance(fn, TensorImage): fn = fn.permute(1,2,0).type(torch.uint8)
        if isinstance(fn, Tensor): fn = fn.numpy()
        if isinstance(fn, ndarray): return cls(Image.fromarray(fn))
        if isinstance(fn, bytes): fn = io.BytesIO(fn)
        return cls(load_image(fn, **merge(cls._open_args, kwargs)))

    def show(self, ctx=None, **kwargs):
        "Show image using `merge(self._show_args, kwargs)`"
        return show_image(self, ctx=ctx, **merge(self._show_args, kwargs))

    def __repr__(self):
        return f'{self.__class__.__name__} mode={self.mode} size={"x".join([str(d) for d in self.size])}'
```

fastai 框架中所有可用的类型都遵循这种模式。我们可以为类型使用一个基类，该基类提供 `create` 和 `show` 方法。

`create` 方法负责完成所有准备工作，并将数据转换为张量。然后，它将张量数据转换为可供 matplotlib 库查看或可视化的形式。

如果我们查看基类型 `TensorPoint` 类，也会看到同样的模式：

```python
class TensorPoint(TensorBase):
    "Basic type for points in an image"
    _show_args = dict(s=10, marker='.', c='r')

    @classmethod
    def create(cls, t, img_size=None)->None:
        "Convert an array or a list of points `t` to a `Tensor`"
        return cls(tensor(t).view(-1, 2).float(), img_size=img_size)

    def show(self, ctx=None, **kwargs):
        if 'figsize' in kwargs: del kwargs['figsize']
        x = self.view(-1,2)
        ctx.scatter(x[:, 0], x[:, 1], **{**self._show_args, **kwargs})
        return ctx
```

我们有一个 `create` 方法，它接受一个点列表和一个可选的图像大小，并返回形状为 (-1, 2) 的张量。`show` 方法只是创建这些点的散点图，并将该图返回给调用者。

## 第3章：SGD – 随机梯度下降

本章将讨论 SGD（即随机梯度下降，stochastic gradient descent）。深度模型就是这样学习拟合给定数据的。我们将通过线性回归把一堆点拟合成一条直线，来学习这个优化器。

```python
from fastai.basics import *
```

现在让我们创建 100 个数据点，稍后将其拟合成一条直线。

![](img/d5454da46c702784893ef8b0b539e5b9_62_0.png)

现在我们想要拟合一条直线。这意味着我们的模型应该最小化均方误差。让我们定义损失函数：均方误差。

```python
def mse(y_hat, y):
    return ((y_hat-y)**2).mean()
```

我们可以运行模型并进行预测，比如说 `a = tensor(.5, .75)`（这是我们对权重的初始化）。我们的模型将进行预测并计算误差。

```python
a = tensor(0.5, .75)
y_pred = x@a
error = mse(y_pred, y)
error
```

```text
tensor(5.4162)
```

那么这意味着什么呢？我们的模型产生了约 5.41 的误差。为了清楚地展示模型做了什么，我们可以绘制 y 点和预测的 y 值，以便更好地理解。

```python
plt.scatter(x[:,0], y)
plt.scatter(x[:,0], y_pred)
```

<matplotlib.collections.PathCollection at 0x7f28b0578d10>

![](img/d5454da46c702784893ef8b0b539e5b9_63_0.png)

所以模型拟合得并不好，这当然是因为我们用随机的参数值初始化了权重。我们需要迭代并调整权重（训练我们的模型）。

### 3.1 模型优化器

在优化过程中，我们的目标是最小化误差（由损失函数 mse 计算）。优化器从一些随机参数开始，计算梯度，并对参数进行一些调整。接下来，我们重复这一步骤，直到误差小于某个值 epsilon 或达到固定的轮次数。（https://en.wikipedia.org/wiki/Stochastic_gradient_descent）

首先，让我们创建这个参数：

```python
a = nn.Parameter(a); a
```

```text
Parameter containing:
tensor([0.5000, 0.7500], requires_grad=True)
```

现在我们必须实现我们的更新函数，该函数检查参数 a 的当前值是否能改善训练结果。如果能，就朝这个方向移动。

```python
def update():
    y_hat = x@a
    loss = mse(y, y_hat)
```

