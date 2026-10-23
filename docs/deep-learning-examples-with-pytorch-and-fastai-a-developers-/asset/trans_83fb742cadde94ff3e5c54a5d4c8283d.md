

要保存此图像，我们可以运行：`prediction_image.save('prediction.png')`

现在我们可以实现一个函数，从测试数据加载器中保存所有预测的图像掩膜：

```
for i, prediction in enumerate(predictions[0]):
    pred_arg = prediction.argmax(dim=0).numpy()
    rescaled = (255.0 / pred_arg.max() *
                (pred_arg - pred_arg.min())).astype(np.uint8)
    img = Image.fromarray(rescaled)
    img.save(f'image_{i}.png')
```

如果我们想保存原始张量数据，可以通过 torch.save 实现：
`torch.save(predictions[0][0], 'image_1.pt')`
`plt.imshow(pred_1.argmax(dim=0))`

### 8.2.3 将模型迁移到全尺寸图像

现在我们想把学习到的权重迁移到另一个可以处理全分辨率图像的模型上。我们需要执行与之前相同的步骤：设置训练数据路径，为数据集创建一个分割器，然后实现我们自定义的损失函数。如果你之前用半尺寸训练过模型，你可能需要重启内核以释放 GPU 内存。

```
path = untar_data(URLs.CAMVID)
valid_fnames = (path/'valid.txt').read().split('\n')
get_msk = lambda o: path/'labels'/f'{o.stem}_{o.suffix}'
codes = np.loadtxt(path/'codes.txt', dtype=str); codes
```

```
def ListSplitter(items):
    def _inner(it):
        val_mask = tensor([o.name in items for o in it])
        return [~val_mask, val_mask]
    return _inner

name2id = {v:k for k,v in enumerate(codes)}
void_code = name2id['Void']

def acc_camvid(inp, targ):
    targ = targ.squeeze(1)
    mask = targ != void_code
    return (inp.argmax(dim=1)[mask]==targ[mask]).float().mean()
```

唯一改变的是我们图像的分辨率。因此，我们必须重新构建数据加载器，并使用全尺寸进行训练。

```
camvid = DataBlock(blocks=(ImageBlock, MaskBlock(codes)),
                   get_items=get_image_files,
                   splitter=ListSplitter(valid_fnames), get_y=get_msk,
                   batch_tfms=[*aug_transforms(size=(720, 960)),
                               Normalize.from_stats(*imagenet_stats)]
)
```

因为图像变大了，我们希望减小数据加载器的批大小。

```
dataloaders = camvid.dataloaders(path/'images', bs=1)
```

现在我们可以分配词汇表，创建学习器，并从半尺寸模型加载权重。

```
config = unet_config(self_attention=True, act_cls=Mish)
opt = ranger
dataloaders.vocab = codes
learner = unet_learner(dataloaders,
                       resnet34,
                       metrics=acc_camvid,
                       config=config,
                       opt_func=opt)
```

```
learner.load('stage-2')
<fastai2.learner.Learner at 0x7f7660710950>
```

接下来，像往常一样，找到一个合适的学习率，训练几个周期，保存模型，然后解冻并继续训练更多周期。

```
learner.lr_find()
(0.00010000000474974513, 4.3651581904669e-07)
```

![](img/d5454da46c702784893ef8b0b539e5b9_130_0.png)

```
lr = 1e-4
```

```
learner.fit_flat_cos(10, slice(lr))
```

| 周期 | 训练损失 | 验证损失 | acc_camvid | 时间 |
| --- | --- | --- | --- | --- |
| 0 | 0.325508 | 0.289412 | 0.916115 | 06:44 |
| 1 | 0.297808 | 0.281555 | 0.919279 | 06:46 |
| 2 | 0.288150 | 0.276814 | 0.920042 | 06:46 |
| 3 | 0.254908 | 0.265356 | 0.925079 | 06:46 |
| 4 | 0.244735 | 0.246666 | 0.930661 | 06:46 |
| 5 | 0.225975 | 0.267461 | 0.924313 | 06:46 |
| 6 | 0.206655 | 0.247543 | 0.930736 | 06:46 |
| 7 | 0.222128 | 0.254455 | 0.928560 | 06:46 |
| 8 | 0.191350 | 0.233727 | 0.932917 | 06:46 |
| 9 | 0.187344 | 0.236577 | 0.933743 | 06:46 |

```
learner.show_results(max_n=4, figsize=(18,8))
```

### 目标/预测

![](img/d5454da46c702784893ef8b0b539e5b9_131_0.png)

![](img/d5454da46c702784893ef8b0b539e5b9_131_1.png)

现在我们看到，我们的模型甚至能很好地分割出街道上的标记。

## 第9章 ImageWoof 数据集

本章我们使用 ImageWoof 数据集。你可以在这里找到该数据集：https://github.com/fastai/imagenette

这个数据集是 ImageNet 的一个简化版本，只有 10 个不同的类别，旨在用较少的周期训练一个新的模型架构，以便你可以检查你的模型架构是否运行良好。

还有几个其他数据集可用：

- **ImageNette:** 比 ImageWoof 略简单，包含来自 ImageNet 的10个易于分类的类别（tench，English springer，cassette player，chain saw，church，French horn，garbage truck，gas pump，golf ball，parachute）
- **ImageWoof:** 10个不同的犬种（Australian terrier, Border terrier, Samoyed, Beagle, Shih-Tzu, English foxhound, Rhodesian ridgeback, Dingo, Golden retriever, Old English sheepdog）
- （发音为 **Imagewang**，中文的“网”）：同时包含 ImageNette 和 Woof，但：
  ![](img/d5454da46c702784893ef8b0b539e5b9_132_0.png)
  - 验证集与 Imagewoof 相同（即 Imagewoof 图像的30%）；验证集中没有 Imagenette 图像（它们都在训练集中）
  - 只有 10% 的 Imagewoof 图像在训练集中！
  - 其余的在 unsup（“无监督”）目录中，你不能在训练中使用它们的标签！

我们想对这个数据集使用 fastai 中最基础的 API，并且不使用预训练模型。那么让我们获取数据集。

```
from fastai.vision.all import *
path = untar_data(URLs.IMAGEWOOF)
```

使用基础 API 时，首先要实现我们的变换：条目变换和批变换。我们参加的是 5 个周期的 128x128 分辨率挑战赛。因此，我们必须适当地调整图像大小。

```
tfms = [[PILImage.create], [parent_label, Categorize()]]
item_tfms = [ToTensor(), Resize(128)]
batch_tfms = [FlipItem(),
              RandomResizedCrop(128, min_scale=0.35), IntToFloatTensor(),
              Normalize.from_stats(*imagenet_stats)]
```

接下来，我们需要决定数据的分割。让我们看一下数据结构：

```
path.ls()
```

```
(#2) [Path('/home/bmayr/.fastai/data/imagewoof2/val'),
Path('/home/bmayr/.fastai/data/imagewoof2/train')]
```

数据集中的图像位于两个不同的文件夹中。一个用于训练，一个用于验证。现在让我们使用 get_image_files 函数获取条目，然后进行分割。

```
items = get_image_files(path)
```

```
split_idx = GrandparentSplitter(valid_name='val')(items)
```

现在我们可以构建数据集和相应的数据加载器。

```
bs = 64
dataset = Datasets(items,
                   tfms,
                   splits=split_idx)
dataloaders = dataset.dataloaders(after_item=item_tfms,
                                  after_batch=batch_tfms, bs=bs)
```

所有数据加载完毕后，我们可以检查一个批次。

```
dataloaders.show_batch(max_n=4, figsize=(12,6))
```

看起来相当不错，但标签只是代码，而不是具体的犬种名称。不过，我们可以通过低级 API 解决这个问题：在我们的 y 值变换中添加一个包含犬种名称的字典。使用新的 API，并不是所有变换都是增强！例如，y 值可以很容易地变换成任何新值。

我们创建字典：

```
lbl_dict = dict(
n02086240= 'Shih-Tzu',
n02087394= 'Rhodesian ridgeback',
```

```
dataloaders = dataset.dataloaders(after_item=item_tfms,
                                  after_batch=batch_tfms,
                                  bs=bs)
```

```
dataloaders.show_batch(max_n=4, figsize=(12,6))
```

现在批次看起来不错。

![](img/d5454da46c702784893ef8b0b539e5b9_135_0.png)

![](img/d5454da46c702784893ef8b0b539e5b9_135_1.png)

![](img/d5454da46c702784893ef8b0b539e5b9_135_2.png)

![](img/d5454da46c702784893ef8b0b539e5b9_135_3.png)

### 9.1 架构与新的实现

在模型架构方面已经有很多新的发现，我想讨论其中的一些：

- **XResNet** – 基于 *Bag of Tricks for ResNet* (https://arxiv.org/abs/1812.01187) 论文。*XResNet* 是我们要使用的新模型架构。
- **Mish** (https://arxiv.org/abs/1908.08681v1) – 一种新的激活函数，已展现出极佳的结果。*Mish* 激活函数与 *Ranger* 优化器结合使用，有望显著提升训练效果。

