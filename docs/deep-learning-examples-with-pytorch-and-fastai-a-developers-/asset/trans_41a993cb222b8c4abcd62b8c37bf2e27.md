
```
[(PILImage mode=RGB size=500x345, TensorPoint([[356., 131.], [394., 130.], [377., 166.], [325., 105.], [314., 68.], [360., 95.], [392., 95.], [431., 61.], [425., 104.]]), (PILImage mode=RGB size=375x500, TensorPoint([[166., 224.], [199., 226.], [181., 249.], [148., 206.], [144., 173.], [168., 190.], [199., 191.], [222., 177.], [216., 210.]]), (PILImage mode=RGB size=911x1024, TensorPoint([[557., 487.], [692., 453.], [658., 584.], [416., 374.], [351., 235.], [499., 312.], [633., 287.], [729., 182.], [716., 313.]]), (PILImage mode=RGB size=388x500, TensorPoint([[120., 198.], [216., 230.], [140., 269.], [ 67., 147.], [ 91., 24.], [151., 98.], [255., 132.], [358., 96.], [306., 231.]]), (PILImage mode=RGB size=1024x761, TensorPoint([[732., 256.], [801., 217.], [800., 288.], [639., 252.], [594., 158.], [691., 176.], [757., 142.], [803., 48.], [840., 152.]]), (PILImage mode=RGB size=500x410, TensorPoint([[310., 229.], [365., 219.], [351., 266.], [264., 216.], [250., 158.], [298., 182.], [352., 173.], [387., 127.], [386., 194.]]), (PILImage mode=RGB size=1024x768, TensorPoint([[739., 292.], [793., 301.], [761., 325.], [716., 268.], [720., 217.], [752., 251.], [794., 257.], [833., 226.], [826., 286.]]), (PILImage mode=RGB size=1024x768, TensorPoint([[615., 230.], [703., 301.], [607., 341.], [588., 141.], [673., 29.], [687., 150.], [755., 209.], [877., 203.], [780., 301.]]), (PILImage mode=RGB size=1024x683, TensorPoint([[390., 246.], [549., 225.], [493., 326.], [271., 242.], [221., 81.], [365., 137.], [540., 110.], [662., 12.], [670., 190.]]), (PILImage mode=RGB size=500x375, TensorPoint([[226., 140.], [302., 148.], [264., 192.], [177., 115.], [179., 42.], [222., 84.], [308., 94.], [362., 65.], [342., 134.]])]
apply_init(model_arch[1], nn.init.kaiming_normal_)
learner = Learner(dataloaders, model_arch,
→ loss_func=MSELossFlat(), splitter = _resnet_split, → opt_func=ranger)
learner.freeze()
learner.lr_find()

(0.03019951581954956, 0.14454397559165955)
```

![](img/d5454da46c702784893ef8b0b539e5b9_210_0.png)

```
learner.fit_flat_cos(5, 1e-2)
```

| 轮次 | 训练损失 | 验证损失 | 时间 |
|---|---|---|---|
| 0 | 0.155895 | 0.077540 | 01:05 |
| 1 | 0.113454 | 0.058677 | 01:05 |
| 2 | 0.057732 | 0.032691 | 01:05 |
| 3 | 0.029703 | 0.015800 | 01:05 |
| 4 | 0.018796 | 0.011400 | 01:05 |

```
learner.show_results()
learner.save('12-keypoints-stage1')
learner.unfreeze()
learner.lr_find()
(2.5118865210060903e-08, 5.248074330665986e-07)
learner.fit_flat_cos(5, 1e-5)
```

## 目标预测

![](img/d5454da46c702784893ef8b0b539e5b9_211_0.png)

![](img/d5454da46c702784893ef8b0b539e5b9_211_1.png)

![](img/d5454da46c702784893ef8b0b539e5b9_211_2.png)

![](img/d5454da46c702784893ef8b0b539e5b9_211_3.png)

![](img/d5454da46c702784893ef8b0b539e5b9_211_4.png)

![](img/d5454da46c702784893ef8b0b539e5b9_211_5.png)

![](img/d5454da46c702784893ef8b0b539e5b9_212_0.png)

| 轮次 | 训练损失 | 验证损失 | 时间 |
|---:|---:|---:|---|
| 0 | 0.016501 | 0.010372 | 01:23 |
| 1 | 0.016295 | 0.009086 | 01:24 |
| 2 | 0.015399 | 0.008417 | 01:24 |
| 3 | 0.014312 | 0.008209 | 01:24 |
| 4 | 0.014386 | 0.007936 | 01:24 |

```python
learner.show_results()
```

## 目标预测

![](img/d5454da46c702784893ef8b0b539e5b9_213_0.png)

![](img/d5454da46c702784893ef8b0b539e5b9_213_1.png)

![](img/d5454da46c702784893ef8b0b539e5b9_213_2.png)

![](img/d5454da46c702784893ef8b0b539e5b9_213_3.png)

![](img/d5454da46c702784893ef8b0b539e5b9_213_4.png)

![](img/d5454da46c702784893ef8b0b539e5b9_213_5.png)

```python
learner.save('12-keypoints-stage2')
```

我们的模型效果相当不错。即使只训练少量 epoch，它也能返回对耳朵、眼睛和嘴巴的关键点相当好的估计。

## 第 15 章
混合模型

在本章中，我们将 UNET 架构适配用于多种其他用途：

- 关键点回归
- 多标签分类
- 分类

这应该能帮助你针对特定的深度学习任务，使用任何架构进行实验。

```
from fastai.vision.all import *
```

### 15.1 关键点回归

对于关键点回归任务，我们使用上一章的猫图像数据集。cat-dataset 已在上一章实现。

```
from pathlib import Path
cat_folder = Path(f'cat-dataset')
labels = get_files(cat_folder, extensions='.cat')
images = get_image_files(cat_folder)
```

```
len(labels), len(images)
(9993, 8936)
```

```
def image_to_keypoints(f): return f'{str(f)}.cat'
```

我们已将所有图像和关键点存储在目录中。对于数据准备，我们使用我们的大部分代码

```
def seperate_points(coords: array) -> Tensor:
    """Separate a set of points to groups"""
    key_pts = []
    for i in range(1, int(coords[0]*2), 2):
        key_pts.append([coords[i], coords[i+1]])
    return tensor(key_pts)

def get_y(f: Path):
```

```
'''Get keypoints for image with path `f`'''
keypoints = np.genfromtxt(image_to_keypoints(f))
return seperate_points(keypoints)

bad_images = []
for img in images:
    image = PILImage.create(img)
    y = get_y(img)
    for coord_pair in y:
        # coordinate width in range 0 < x < image.width
        # coordinate height in range 0 < x < image.height
        if coord_pair[0] > image.size[0] or coord_pair[0] < 0 or \
           coord_pair[1] > image.size[1] or coord_pair[1] < 0:
            bad_images.append(img)

for file in list(set(bad_images)):
    file.unlink()
```

### 15.1.1 准备 DataBunch

我们以上一章相同的方式准备数据

```
item_tfms = [Resize(224, method='squish')]
batch_tfms = [Flip(), Rotate(), Zoom(), Warp()]

def get_cat_image_files(path):
    return get_image_files(cat_folder, True, None)

datablock = DataBlock(blocks=(ImageBlock, PointBlock),
                      get_items=get_cat_image_files, splitter=RandomSplitter(), get_y=get_y,
                      item_tfms=item_tfms,
                      batch_tfms=batch_tfms)

bs = 16
dataloaders = datablock.dataloaders(cat_folder, path=..., bs=bs)
dataloaders.show_batch()
```

### 15.1.2 现在让我们创建模型

首先我们分析 unet_learner 的源代码。

![](img/d5454da46c702784893ef8b0b539e5b9_216_0.png)

![](img/d5454da46c702784893ef8b0b539e5b9_216_1.png)

![](img/d5454da46c702784893ef8b0b539e5b9_216_2.png)

![](img/d5454da46c702784893ef8b0b539e5b9_216_3.png)

![](img/d5454da46c702784893ef8b0b539e5b9_216_4.png)

![](img/d5454da46c702784893ef8b0b539e5b9_216_5.png)

![](img/d5454da46c702784893ef8b0b539e5b9_216_6.png)

![](img/d5454da46c702784893ef8b0b539e5b9_216_7.png)

![](img/d5454da46c702784893ef8b0b539e5b9_216_8.png)

```python
def unet_learner(dls, arch, loss_func=None, pretrained=True,
    cut=None, splitter=None,
    config=None, n_in=3, n_out=None,
    normalize=True, **kwargs):
    "Build a unet learner from `dls` and `arch`"
    if config is None: config = unet_config()
    meta = model_meta.get(arch, _default_meta)
    body = create_body(arch, n_in, pretrained, ifnone(cut,
```

```
→ meta['cut'])
size = dls.one_batch()[0].shape[-2:]
if n_out is None: n_out = get_c(dls)
assert n_out, "`n_out` is not defined, and could not be inferred from data, set `dls.c` or pass `n_out`"
if normalize: _add_norm(dls, meta, pretrained)
model = models.unet.DynamicUnet(body, n_out, size, **config)
→ # HERE
learn = Learner(dls, model, loss_func=loss_func,
→ splitter=ifnone(splitter, meta['split']), **kwargs)
if pretrained:
    learn.freeze()
return learn
```

那么我们要在顶部构建自定义头部时需要在哪里调整？让我们看看。
有一个 body 被创建：

```
body = create_body(arch, n_in, pretrained, ifnone(cut, → meta['cut']))
```

但这个 body 将被用在何处？这里这个 body 被传递到 DynamicUnet 中。这行代码实际上生成了模型的头部以及其余的 unet 模型。

model = models.unet.DynamicUnet(body, n_out, size, **config)
现在我们想要修改这一行，使其更像一个自定义 unet。首先，我们必须导入 UNET-Learner 所需的一些辅助函数。

```
from fastai.vision.models.unet import _get_sz_change_idxs, → UnetBlock,
ResizeToOrig
from fastai.vision.learner import _default_meta, _add_norm
```

对于我们的自定义 UNET 学习器，我们想要用我们特定的头部替换最后一个 ConvLayer，因为这一层包含了类别数：

```
layers += [ConvLayer(ni,
n_classes,
ks=1,
act_cls=None,
norm_type=norm_type,
```
