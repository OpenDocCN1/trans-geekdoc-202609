
```text
[100, 103, 110, ..., 147, 147, 150]],

[[ 64, 58, 48, ..., 160, 162, 152], [ 63, 55, 46, ..., 155, 151, 128], [ 64, 56, 48,
..., 132, 126, 125], ...,
[111, 115, 114, ..., 163, 163, 161], [111, 115, 115, ..., 161, 159, 155], [112,
114, 122, ..., 155, 156, 158]],

[[ 70, 62, 54, ..., 154, 155, 148],
[ 70, 58, 52, ..., 149, 146, 122],
[ 69, 60, 52, ..., 127, 124, 119],
...,
[122, 122, 120, ..., 163, 165, 164],
[119, 122, 122, ..., 162, 161, 158],
[118, 122, 129, ..., 157, 157, 160]]], dtype=torch.uint8)

IntToFloatTensor -- {'div': 255.0, 'div_mask': 1} └
→ TensorImage([[[0.2275, 0.1882, 0.1529, ..., 0.6000, 0.6078, 0.5843],
[0.2078, 0.1765, 0.1451, ..., 0.5843, 0.5804, 0.4824], [0.2196, 0.1804,
0.1373, ..., 0.4902, 0.4745, 0.4667], ...,
[0.3843, 0.4039, 0.4000, ..., 0.6039, 0.6078, 0.6000], [0.3804, 0.4000,
0.4078, ..., 0.6000, 0.5961, 0.5804], [0.3922, 0.4039, 0.4314, ..., 0.5765,
0.5765, 0.5882]],

[[0.2510, 0.2275, 0.1882, ..., 0.6275, 0.6353, 0.5961], [0.2471, 0.2157,
0.1804, ..., 0.6078, 0.5922, 0.5020], [0.2510, 0.2196, 0.1882, ..., 0.5176,
0.4941, 0.4902], ...,
[0.4353, 0.4510, 0.4471, ..., 0.6392, 0.6392, 0.6314], [0.4353, 0.4510,
0.4510, ..., 0.6314, 0.6235, 0.6078], [0.4392, 0.4471, 0.4784, ..., 0.6078,
0.6118, 0.6196]],

[[0.2745, 0.2431, 0.2118, ..., 0.6039, 0.6078, 0.5804], [0.2745, 0.2275,
0.2039, ..., 0.5843, 0.5725, 0.4784], [0.2706, 0.2353, 0.2039, ..., 0.4980,
0.4863, 0.4667], ...,
[0.4784, 0.4784, 0.4706, ..., 0.6392, 0.6471, 0.6431], [0.4667, 0.4784,
0.4784, ..., 0.6353, 0.6314, 0.6196], [0.4627, 0.4784, 0.5059, ..., 0.6157,
0.6157, 0.6275]]])

--------------------------------
```

```text
RuntimeError Traceback (most recent call last)

<ipython-input-15-a348e7a2f615> in <module>
1 for f in dls.train.after_batch:
2 name = f.name
----> 3 x = f(x)
4 print(name, x[0])

~/anaconda3/lib/python3.7/site-packages/fastcore/transform.py in __call__(self, x, **kwargs)
70 @property
71 def name(self): return getattr(self, '__name__', __get_name(self))
----> 72 def __call__(self, x, **kwargs): return self.__call__('encodes', x, **kwargs)
73 def decode(self, x, **kwargs): return self.__call__('decodes', x, **kwargs)
74 def __repr__(self): return f'{self.name}:\nencodes: {self.encodes}\ndecodes: {self.decodes}'

~/anaconda3/lib/python3.7/site-packages/fastcore/transform.py in __call__(self, fn, x, split_idx, **kwargs)
80 def __call__(self, fn, x, split_idx=None, **kwargs):
81 if split_idx != self.split_idx and self.split_idx is not None: return x
----> 82 return self._do_call(getattr(self, fn), x, **kwargs)
83
84 def _do_call(self, f, x, **kwargs):

~/anaconda3/lib/python3.7/site-packages/fastcore/transform.py in _do_call(self, f, x, **kwargs)
87 ret = f.returns_none(x) if hasattr(f, 'returns_none') else None
88 return retain_type(f(x, **kwargs), x, ret)

---> 89 res = tuple(self._do_call(f, x_, **kwargs) for x_ in x)
90 return retain_type(res, x)
91

~/anaconda3/lib/python3.7/site-packages/fastcore/transform.py in <genexpr>(.0)
87 ret = f.returns_none(x) if hasattr(f, 'returns_none') else None
88 return retain_type(f(x, **kwargs), x, ret)
---> 89 res = tuple(self._do_call(f, x_, **kwargs) for x_ in x)
90 return retain_type(res, x)
91

~/anaconda3/lib/python3.7/site-packages/fastcore/transform.py in _do_call(self, f, x, **kwargs)
86 if f is None: return x
87 ret = f.returns_none(x) if hasattr(f, 'returns_none') else None
---> 88 return retain_type(f(x, **kwargs), x, ret)

89 res = tuple(self._do_call(f, x_, **kwargs) for x_ in x)
90 return retain_type(res, x)

~/anaconda3/lib/python3.7/site-packages/fastcore/dispatch.py in __call__(self, *args, **kwargs)
97 if not f: return args[0]
98 if self.inst is not None: f = MethodType(f, self.inst)
---> 99 return f(*args, **kwargs)
100
101 def __get__(self, inst, owner):

~/anaconda3/lib/python3.7/site-packages/fastai/data/transforms.py in encodes(self, x)
352 self.mean, self.std = x.mean(self.axes, keepdim=True), x.std(self.axes, keepdim=True) + 1e-7
353
--> 354 def encodes(self, x: TensorImage): return (x - self.mean) / self.std
355 def decodes(self, x: TensorImage):
356 f = to_cpu if x.device.type == 'cpu' else noop

~/anaconda3/lib/python3.7/site-packages/fastai/torch_core.py in _f(self, *args, **kwargs)
296 def _f(self, *args, **kwargs):
297 cls = self.__class__
--> 298 res = getattr(super(TensorBase, self), fn)(*args, **kwargs)
299 return retain_type(res, self, copy_meta=True)
300 return _f

RuntimeError: Expected all tensors to be on the same device, but found at least two devices, cuda:0 and cpu!
```

我们可以清楚地看到管道做了什么，并且可以在我们的管道上将其用于调试目的。

## 第11章 风格迁移

本章将介绍风格迁移的概念，这意味着我们取一张图像的风格并将其（仅风格）应用到另一张图像上。

Notebook Dev 是 fastai 团队开发的概念，允许使用 Jupyter notebook 构建健壮的 Python 库。你可以在 nbdev 仓库中了解更多细节：https://github.com/fastai/nbdev。

Notebook dev 让你在不离开 Jupyter notebook 的情况下构建库并附带文档。Notebook dev 用于开发整个 fastai 库。所以如果你在笔记本的一些单元格中发现 *奇怪* 的注释，不要介意。

它允许你用特殊注释来标注代码单元格：

- #default_exp
- #hide
- #export

你可以使用 #default_exp 来设置生成的 .py 库文件名。对于本章，我们将导出名称设置为 09-style-transfer。当然你可以选择任何你喜欢的名称。

任何标记为 #hide 的内容都不会被导出。因此你库的后续使用者将看不到它。

现在 #export 将用于包含应集成到你的库中的代码的任何单元格。
每次你想使用 notebook dev 时，你必须从 showdoc 导入任何内容——不过，你可以隐藏此单元格。

```python
from nbdev.showdoc import *
#default_exp style_transfer
```

现在让我们转向 **风格迁移** 主题。

对于风格迁移，我们使用一个称为 *特征损失* 或有时称为 *感知损失* 的概念。这个概念的核心思想是关注模型的输入和输出特征，并比较哪些相同、哪些不同。为了将一种图像的风格迁移到另一张图像，你只需调整不同的输入/输出特征。

![](img/d5454da46c702784893ef8b0b539e5b9_158_0.png)

图 2. 系统概述。我们训练一个图像转换网络来将输入图像转换为输出图像。我们使用一个预训练于图像分类的损失网络来定义感知损失函数，以衡量图像之间在内容和风格上的感知差异。训练过程中损失网络保持固定。

```python
features_net, layers = _get_layers(architecture.lower(), pretrained)
hooks = hook_outputs(layers, detach=False)
def _inner(x):
    features_net(x)
    return hooks.stored
return _inner
```

```python
features = get_features('vgg19')
```

### 11.2 创建损失函数

我们首先想要下载任何将为我们的迁移模型提供风格基础的图像。请尊重图像的版权。我使用的是来自 Picasso 的《自画像》(*Self-Portrait*)，来自 [www.clker.com](http://www.clker.com)。

接下来我们将分析管道以及如何仅使用一个项目来操作它以用于我们的工作。我们需要此图像的原始张量值。之后它必须被归一化以满足我们模型的需求。

```bash
#export
url = 'http://www.clker.com/cliparts/0/8/2/e/13307230771203911842picasso5-hi.png'

# all simpsons characters
url = 'https://tstoaddicts.files.wordpress.com/2013/11/characters1.jpg'
!wget {url} -O 'style.png'
```

```text
--2020-09-03 08:22:58-- https://tstoaddicts.files.wordpress.com/2013/11/characters1.jpg
Auflösen des Hostnamens tstoaddicts.files.wordpress.com (tstoaddicts.files.wordpress.com) ... 192.0.72.19, 192.0.72.18
Verbindungsaufbau zu tstoaddicts.files.wordpress.com (tstoaddicts.files.wordpress.com)|192.0.72.19|:443 ... verbunden.
HTTP-Anforderung gesendet, auf Antwort wird gewartet ... 200 OK Länge: 1623279 (1,5M) [image/jpeg]
Wird in »style.png« gespeichert.

style.png 100%[===================>] 1,55M 1,17MB/s in 1,3s
2020-09-03 08:23:00 (1,17 MB/s) - »style.png« gespeichert [1623279/1623279]
```
