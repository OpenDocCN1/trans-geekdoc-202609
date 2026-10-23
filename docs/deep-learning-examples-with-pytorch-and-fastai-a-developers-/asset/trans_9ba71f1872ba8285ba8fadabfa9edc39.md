
图像已被调整大小。

*`Tensor.view(..)` 是做什么的？* 这个函数用于将任意张量重塑为指定格式。例如，如果你想将一个张量转换为 2x2 的矩阵，你可以调用 `view(2, 2)`。但如果你知道列数而不知道行数呢？这时我们使用 -1。我们调用 `view(-1, 2)` 表示：创建一个具有 2 列和所需行数的张量。

我们可以添加一个输入来跟踪图像大小：

```python
class MyTensorPoint(TensorBase):
    @classmethod
    def create(cls, t, img_size=None)->None:
        return cls(Tensor(t).view(-1, 2).float(),
                   img_size=img_size)
```

让我们用我们的狗图像来试试这个类：

```python
img.shape
(414, 601)
```

我们的图像分辨率为 414x601 像素。现在我们可以使用我们的类创建一些张量点。

```python
points = [[200, 150], [200, 200], [275, 301]]
tensor_points = MyTensorPoint(points)
tensor_points
MyTensorPoint([[200, 150], [200, 200], [275, 301]])
```

我们的类可以正常工作。我们可以看到一个有 2 列 3 行的张量（因为我们传入了一个包含 3 个项目的列表）。如果我们想显示我们的点，我们必须在我们的类中实现一个显示函数。我们将使用散点图来绘制这些点。我们假设我们向显示函数传入一个图像，并在这张图像上叠加这些点。

```python
class MyTensorPoint(TensorBase):
    _show_args = dict(s=10, marker='.', c='r')
    @classmethod
```

```python
def create(cls, t, img_size=None)->None:
    return cls(Tensor(t).view(-1,2).float(),
               img_size=img_size)

def show(self, ctx=None, **kwargs):
    if 'figsize' in kwargs: del kwargs['figsize']
    x = self.view(-1,2)
    ctx.scatter(x[:,0],
                x[:,1],
                **{**self._show_args, **kwargs})
    return ctx
```

首先，我们确保参数 `figsize` 不在参数列表中。如果它在，我们想使用这个值而不是默认值。

接下来，我们获取张量并将它们转换为具有 2 列的视图，用于存储像素值。我们使用参数 `self`，它与正在调用显示函数的对象相关联。

注意：我们不在 `create` 函数中使用 `self`，因为我们已将该函数注解为类方法。

然后我们绘制散点图并将绘图返回给调用者。让我们试一下这个函数！

```python
tensor_points = MyTensorPoint.create(points)
tensor_points.show()
```

AttributeError Traceback (most recent call last)
in 1 tensor_points = MyTensorPoint.create(points) —> 2
tensor_points.show()

```
in show(self, ctx, kwargs) 9 if 'figsize' in kwargs: del kwargs['figsize'] 10 x = self.view(-1,2) —> 11 ctx.scatter(x[:,0], 12 x[:,1], 13 **{**self._show_args, **kwargs})
```

AttributeError: 'NoneType' object has no attribute 'scatter'
**砰！** 我们遇到了一个错误：
AttributeError: 'NoneType' object has no attribute 'scatter'

但是哪里出错了呢？哦，是的——我们需要一个图像来叠加这些点。这就是 `show` 函数中的上下文参数 `ctx`。让我们这样做，并传入我们的图像作为绘制散点图的上下文。
tensor_points.show(ctx=img.show())
<matplotlib.axes._subplots.AxesSubplot at 0x7fcf40b04fd0>

![](img/d5454da46c702784893ef8b0b539e5b9_97_0.png)

现在一切正常，我们可以看到代表张量点的红点。
**还有最后一件事**要做。我们必须为学习器添加损失函数，使其能与我们的点协同工作。
我们将变换函数包装在我们的 `Tensorpoint.create` 周围，并为其添加损失函数 `MSELossFlat`。
myTensorPointCreate = Transform(MyTensorPoint.create)
myTensorPointCreate.loss_func = MSELossFlat()
接下来，我们想用新的 `myTensorPointCreate`（我们已经将损失函数传递给它）替换原始的 `create` 函数。
MyTensorPoint.create = myTensorPointCreate
因此，我们已经冲过终点线了。现在，我们想将我们*从零开始*的解决方案与 fastai 库中的原始源代码进行比较。这是 fastai 的 TensorPoint 类：

```python
class TensorPoint(TensorBase):
"Basic type for points in an image" _show_args = dict(s=10, marker='.', c='r')

@classmethod
def create(cls, t, img_size=None)->None:
"Convert an array or a list of points `t` to a `Tensor`"
return cls(Tensor(t).view(-1, 2).float(),
img_size=img_size)
```

```python
order = 1  # Want this to occur first!
def __init__(self, do_scale=True, y_first=False):

self.do_scale, self.y_first = do_scale, y_first
```

接下来我们进行设置。我们使用 `numel` 方法来计算我们拥有的元素数量（*数量-元素*）。在我们的例子中，我们有 6 个元素（*每个点包含一个 x 坐标和一个 y 坐标*）。

```python
tensor_points.numel()
6
```

我们使用数据加载器并查找第一个项目（索引 0），然后将 `.c` 设置为对每个 `TensorPoint` 类型的元素调用 `.numel()` 的返回值。

```python
class MyPointScaler(Transform):
    order = 1  # Want this to occur first!
    def __init__(self, do_scale=True, y_first=False):

        self.do_scale, self.y_first = do_scale, y_first

    def setups(self, dl):
        its = dl.do_item(0)
        for t in its:

            if isinstance(t, TensorPoint): self.c = t.numel()
```

从这里开始，我们必须处理编码器和解码器。两者都基于这样的假设：*如果我们得到特定的类型，我们想在其上运行变换。*

我们使用一个名为 `_grab_sz` 的辅助函数来确保对象是 `Tensor` 类型（如果不是，则直接调用 `x.size`）。

```python
class MyPointScaler(Transform):
    order = 1  # Want this to occur first!
    def __init__(self, do_scale=True, y_first=False):

        self.do_scale, self.y_first = do_scale, y_first
```

```python
def setups(self, dl):
its = dl.do_item(0)
for t in its:

if isinstance(t, TensorPoint): self.c = t.numel()
def _grab_sz(self, x):
self.sz = [x.shape[-1], x.shape[-2]] if isinstance(x, Tensor) else x.size
```

现在我们只剩下一件事要完成。我们必须实现 `encode` / `decode` 函数。这两个方法（编码和解码）都接受 `PILBase` 类型的对象，`PILBase` 是 `PILImage` 的父类，因为 `PILImage` 扩展了 `PILBase`。我们通过调用 `_grab_sz(x)` 获取 `x` 的大小，然后直接返回这些值。

```python
class MyPointScaler(Transform):
order = 1 # Want this to occur first!
def __init__(self, do_scale=True, y_first=False):

self.do_scale, self.y_first = do_scale, y_first

def setups(self, dl):
its = dl.do_item(0)
for t in its:

if isinstance(t, TensorPoint): self.c = t.numel()
def _grab_sz(self, x):
self.sz = [x.shape[-1], x.shape[-2]] if isinstance(x, Tensor) else x.size

def encodes(self, x:(PILBase, TensorImageBase)): return self._grab_sz(x)
def decodes(self, x:(PILBase, TensorImageBase)): return self._grab_sz(x)
```

下一步是按照给定的图像大小缩放点。

```python
def _myScale_pnts(y, sz, do_scale=True, y_first=False): 
if y_first: y = y.flip(1)
res = y * 2/tensor(sz).float() -1 if do_scale else y 
return TensorPoint(res, img_sz=sz)
```

让我们尝试一下，将我们的图像点缩放到例如 224（imagenet 的规模）。

```python
_myScale_pnts(tensor_points, 224)
```

TensorPoint([[0.7857, 0.3393], [0.7857, 0.7857], [1.4554, 1.6875]])

结果符合我们的预期！我们的张量已缩放到图像大小 224。

让我们再做另一个例子。我们创建一个新的张量点列表，这些点恰好是我们图像的四个角点。然后我们缩放图像，看看我们的张量点的坐标是否同样被缩小了。

```python
img.shape
```

(414, 601)

```python
corner_points = [[0,0], [0,414], [601,0], [601,414]] 
corner_tps = TensorPoint.create(corner_points)
ax = img.show()
for p in corner_tps: p.show(ctx=ax)
```

![](img/d5454da46c702784893ef8b0b539e5b9_101_0.png)

现在，如果我们调整图像大小，我们的点应该与我们标记四个角之前看到的模式相匹配。

```python
scaled_tps = [_myScale_pnts(tp, 224) for tp in corner_tps]
```

scaled_tps
[TensorPoint([-1., -1.]), TensorPoint([-1.0000, 2.6964]), TensorPoint([4.3661, -1.0000]), TensorPoint([4.3661, 2.6964])]

