
```python
datasource = Datasets(train_images + test_images,
                      tfms=[[PILImage.create],
                            [parent_label, Categorize]],
                      splits=split_list)
show_at(datasource.train, 1)
```

<matplotlib.axes._subplots.AxesSubplot at 0x7f7ca41468d0>

![](img/d5454da46c702784893ef8b0b539e5b9_85_0.png)

```python
datasource.n_subsets
```
```
3
```

现在我们可以创建 dataloaders。

```python
dataloaders = datasource.dataloaders(bs=bs,
                                     after_item=item_tfms,
                                     after_batch=batch_tfms)
```

```python
dataloaders.show_batch(figsize=(8,8))
```

```python
pretrained=False,
metrics=accuracy).to_fp16()
learner.fit_one_cycle(1)
```

| 周期 | 训练损失 | 验证损失 | 准确率 | 时间 |
|-------|------------|------------|----------|------|
| 0 | 2.812563 | 2.161600 | 0.219945 | 00:36 |

现在我们可以调用 validate 来检查模型在 datasource 的测试数据上的结果——这里是 datasource 对象的索引 2。

```python
learner.validate(ds_idx =2)
```

```
(#2) [2.1629929542541504, 0.2260117083787918]
```

嗯，这确实不是一个好模型。但它应该仅仅作为一个基线。我们将尝试使用交叉验证模型来做得更好。

### 6.2 构建交叉验证模型

```python
from sklearn.model_selection import StratifiedKFold
```

我们使用 sklearn 模块中的 KFold 来进行图像数据的切分。首先，我们必须创建一个 K-Fold 对象。我们告诉 K-Fold 我们需要 10 个切分（或 10 个模型）。

但在切分之前，我们必须创建数据中所有标签的列表。由于我们将使用训练数据和测试数据进行训练，因此需要运行两次循环。一次针对训练数据的标签，另一次针对 datasource 中验证数据的标签。

```python
train_labels = L()
for i in range(len(datasource.train)):
    train_labels.append(datasource.train[i][1])

for i in range(len(datasource.valid)):
    train_labels.append(datasource.valid[i][1])

train_labels
```

```
(#9025) [TensorCategory(0), TensorCategory(8), TensorCategory(2),
         TensorCategory(9), TensorCategory(8), TensorCategory(4),
         TensorCategory(6), TensorCategory(0), TensorCategory(7),
         TensorCategory(2)...]
```

断言训练图像列表和标签列表中的元素数量相等。

```python
assert (len(datasource.train) + len(datasource.valid)) == len(train_images)
assert len(train_images) == len(train_labels)
```

我们想要进行分层切分，以确保所有子模型都与原始模型相似。在切分之前，我们对列表中的元素进行打乱。在 sklearn 中有 StratifiedKFold 和 StratifiedShuffleSplit。

如果我们使用 KFold，通常不希望任何测试集重叠，即使在打乱之后也是如此。因此，我们对数据进行一次打乱，然后使用 KFold 将其切分成多个模型。测试数据始终位于其中一个切分中，其余数据属于训练数据集。

如果我们使用 ShuffleSplit，每次切分时数据会再次打乱。这可能导致测试数据集在切分之间重叠。

```python
import random
random.shuffle(train_images)
k_folds_strat = StratifiedKFold(n_splits=5, shuffle=True)
```

现在我们可以创建训练循环。我们对每个 KFold 切分训练模型 1 个 epoch。

首先，我们在之前创建的验证索引上创建一个 IndexSplitter。我们使用这个分割器再次切分训练图像。和之前一样，我们将训练和验证数据合并到一个列表中，并追加测试数据的索引。

接下来，我们创建数据集，并通过 splits 参数将我们的切分传入数据集。然后我们从 datasource 创建 dataloaders，创建 cnn_learner，并训练一个 epoch。这次我们为所有 KFold 切分进行训练，因此我们希望跟踪测试数据集上原始预测的验证准确率。我们可以通过索引 datasource 将测试数据传递给 get_pred(ds_idx=2) 方法——记住这一点。当然，对于像 Kaggle 这样的任何竞赛，你的结果都可能从这项技术中获益良多。

## 第 7 章：FastAI —— 内部 API 概览

本章重点介绍 fastai API 的内部结构。我们将通过一个示例了解如何在完整处理管道中使用最基础的 fastai API。我们将使用 Points 对象来完成这一演示，因为这是一个非常简单的对象。

```python
from fastai.vision.all import *
```

首先，我们检查 PILImage 类，并将从头开始重建它。我们可以使用 download_url 方法轻松下载图像，只需提供图像的 url 即可。

我们使用一张来自 Wikimedia 的狗的图像。

```python
img_url = 'https://upload.wikimedia.org/wikipedia/commons/d/d6/Thai-Ridgeback.jpg'
img_path = Path('images/dog.jpg')
download_url(img_url, img_path)
```

### 7.1 PILImage 类

现在回到 PILImage 类。这个类包含什么？让我们打开代码：??PILImage。

```python
??PILImage
class PILImage(PILBase): pass
```

哇，这个类内部的代码不多。实际上，PILImage 只是 PILBase 上的一个包装类。让我们深入探讨一下：

```python
class PILBase(Image.Image, metaclass=BypassNewMeta):
    _bypass_type = Image.Image
    _show_args = {'cmap': 'viridis'}
    _open_args = {'mode': 'RGB'}

    @classmethod
    def create(cls, fn: (Path, str, Tensor, ndarray, bytes), **kwargs) -> None:
        "Open an `Image` from path `fn`"
        if isinstance(fn, TensorImage):
            fn = fn.permute(1, 2, 0).type(torch.uint8)
        elif isinstance(fn, Tensor):
            fn = fn.numpy()
        if isinstance(fn, ndarray):
            return cls(Image.fromarray(fn))
        if isinstance(fn, bytes):
            fn = io.BytesIO(fn)
        return cls(load_image(fn, **merge(cls._open_args, kwargs)))

    def show(self, ctx=None, **kwargs):
        "Show image using `merge(self._show_args, kwargs)`"
        return show_image(self, ctx=ctx, **merge(self._show_args, kwargs))
```

嗯，这个看起来更好。但这意味着什么呢？

我们希望与处理管道一起使用的所有基本对象类型都应该是这样的。它们都实现了 create 和 show 方法。create 函数负责准备要转换为张量的输入，而 show 仅负责显示输入。

让我们详细地深入了解这个类。首先是这个参数值：Image.Image。这只是 Pillow 类中的一个 Image。因此，我们认为该类具有某种 Pillow 属性。

现在，我们可以看一下 PILImage 的 create 和 show 函数对之前下载的图像会产生什么结果。因此，我们先在图像路径上调用 create，然后调用 show。

```python
img = PILImage.create(img_path)
img.show()
```

<matplotlib.axes._subplots.AxesSubplot at 0x7fcf40bc1690>

太棒了！我们像之前一样看到了狗的图像。

### 7.2 ImageBlock 函数

接下来是我们在示例中使用过的 ImageBlock 函数。这个类与 ImageBlock 函数中的 create 和 show 方法是如何关联的？

![](img/d5454da46c702784893ef8b0b539e5b9_93_0.png)

我们使用 ??ImageBlock 来更好地理解。

```python
def ImageBlock(cls=PILImage):
    return TransformBlock(type_tfms=cls.create,
                          batch_tfms=IntToFloatTensor)
```

该函数期望 PILImage 类型的对象。然后，该函数在此对象上调用 create 函数，并将结果连同批量变换（将该图像转换为浮点张量）一起传递给 TransformBlock 对象。

这个管道可以被转换为遵循 create/show 模式的类型——不仅仅是 PIL 图像。我们可以使用继承自 TransformBlock 的 DataBlock：

```python
block = TransformBlock(type_tfms=PILImage.create,
                       batch_tfms=IntToFloatTensor)
```

我们将通过 Points 来了解如何在非 Image 类型上使用该管道。

### 7.3 Points 类

首先要做的是查看源代码：??PointBlock。

```python
PointBlock = TransformBlock(type_tfms=TensorPoint.create,
                            item_tfms=PointScaler)
```

这看起来非常熟悉！PointBlock 使用了 TransformBlock。这个类使用 TensorPoint 类的 create 方法，并附加一个 PointScaler 来转换条目。

现在我们可以做进一步分析，看看 PointBlock 和 PointScaler。

**TensorPoint 类**应该将任何点列表转换为张量，无需变换，并且应该从原始数据输入生成我们可以使用的输入值。太棒了！借助到目前为止从分析中获得的专业知识，我们可以自己构建一个 TensorPoint 类。

我们的 MyTensorPoint 类应该继承自 TensorBase，这限制了我们的类返回张量对象。

```python
# we can omit the create method if we do not need the show_batch method
class MyTensorPoint(TensorBase):
    @classmethod
    def create(cls, t):
        return cls(Tensor(t).view(-1, 2).float())
```

我们的 create 函数接受一个包含点列表的参数 t。它会创建一个张量，重塑该张量并将其转换为 float 类型。我们需要 float 类型，以确保点在……时保持正确的位置。
