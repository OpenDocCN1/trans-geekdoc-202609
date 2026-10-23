
*编码.* 我们可以只将函数包装成一个 Transform（我们可以将任何函数包装成一个 transform）：

```python
OpenAndResize = Transform(resized_image)
```

现在让我们构建管道：

```python
pipe = Pipeline([sp, OpenAndResize])
```

让我们看看管道中的第一个项目：

```python
x,y,z = pipe(0)
x.shape, y.shape, z
(torch.Size([3, 128, 128]), torch.Size([3, 128, 128]), tensor([1],
dtype=torch.int32))
```

但如何将所有这些从管道传输到 dataloader 中呢？首先我们需要一个 TransformedList。我们只需要传入一个索引列表和要运行的管道即可。

```python
tls = TfmdLists(range_of(items), pipe)
```

现在我们可以轻松创建我们的数据加载器并添加任何喜欢的批处理转换。在这种情况下，我们希望规范化我们的数据。

```python
dls = tls.dataloaders(bs=16,
after_batch=[Normalize.from_stats(*imagenet_stats)])
batch = dls.one_batch()
```

现在我们已经为孪生网络问题准备好了一个数据加载器。我们可以通过 PILImage 的帮助来查看它

```python
from torchvision import transforms
im1 = transforms.ToPILImage()(Tensor.cpu(batch[0][0])).convert("RGB")
im2 = transforms.ToPILImage()(Tensor.cpu(batch[1][0])).convert("RGB")
```

```python
display(im1, im2)
```

![](img/d5454da46c702784893ef8b0b539e5b9_290_0.png)

我们的数据加载器现在可以使用了。我们需要以某种方式将其拆分，然后我们可以添加一些增强。（对于孪生网络，这意味着增强第一个或第二个图像）。

dls.valid_ds
TfmdLists: [] tfms – (#2) [SiamesePair: encodes: (object,object) -> encodes decodes: ,resized_image: encodes: (Path,object) -> resized_imagedecodes: ]

## 第20章
### 音频

fastai 音频库已由 fastai 论坛的不同成员开发了相当长一段时间。非常感谢：

- **rbracco**: [rbracco](rbracco)
- **kevinbird15**: [kevinbird15](kevinbird15)
- **mogwai**: [mogwai](mogwai)
- **Hiromis**: [Hiromis](Hiromis)
- **scart97**: [scart97](scart97)
- **hoftherose**: [hoftherose](hoftherose)
- **madhavajay**: [madhavajay](madhavajay)
- **Jo**: [Jo](Jo)

### 20.1 为什么音频与图像不同？

当然，我们可以通过将其放入 1D 张量来在原始音频数据上训练我们的模型。最近，许多研究人员已将音频数据转换为

频谱图并使用这些频谱图像进行工作。

到目前为止，没有我们可以直接导入的包，但我们可以使用 pip 直接从 github 仓库安装音频模块。我们还需要 torchaudio。

```python
!pip install git+https://github.com/rbracco/fastai_audio.git
```

Collecting git+https://github.com/rbracco/fastai_audio.git
Cloning https://github.com/rbracco/fastai_audio.git to /tmp/pip-req-build-21aqvo91
Running command git clone -q https://github.com/rbracco/fastai_audio.git /tmp/pip-req-build-21aqvo91
Username for ‘https://github.com’: ^C

![](img/d5454da46c702784893ef8b0b539e5b9_291_0.png)

### 20.2 音频数据集

我们将使用一个免费的音频数据集，其中包含来自 4 位不同说话人的约 2000 条录音，每位说话人说每个数字 5 次。首先我们需要下载数据并构建自定义提取函数。

你可以从此 url 下载数据集：https://public-datasets.fra1.cdn.digitaloceanspaces.com/recordings.tar.gz

```python
from fastai.vision.all import *
from fastai_audio.core.all import *
from fastai_audio.augment.all import *

def tar_extract_at_filename(fname, dest):
    "Extract `fname` to `dest`/`fname`.name folder using `tarfile`"
    dest = Path(dest)/Path(fname).with_suffix("").name
    tarfile.open(fname, 'r:gz').extractall(dest)

url = 'https://public-datasets.fra1.cdn.digitaloceanspaces.com/recordings.tar.gz'
path_dig = untar_data(url, extract_func=tar_extract_at_filename)/'recordings'
```

现在我们可以只选择文件的音频扩展名：
```python
audio_extensions[:5]
```
('.au', '.snd', '.mp3', '.mp2', '.aif')

```python
fnames = get_files(path_dig, extensions=audio_extensions)
```

我们将每个文件转换为 audiotensor。

```python
at = AudioTensor.create(fnames[0])
at, at.shape
```
(AudioTensor([[-0.0234, -0.0234, -0.0156, ..., -0.0078, -0.0156, -0.0078]]), torch.Size([1, 2778]))

```python
at.show()
```
您的浏览器不支持音频元素。

![](img/d5454da46c702784893ef8b0b539e5b9_293_0.png)

### 20.3 准备数据集

使用 fastai2audio 我们可以进行不同的配置。目前它有：

- BasicMelSpectrogram
- BasicMFCC
- BasicSpectrogram
- Voice

我们今天将使用 Voice 模块，因为该数据集仅包含人类声音。通过配置我们可以例如设置频率范围。

```python
cfg = AudioConfig.Voice()
cfg.f_max, cfg.sample_rate
```
(8000.0, 16000)

```python
aud2spec = AudioToSpec.from_cfg(cfg)
```

现在我们可以使用此配置从音频数据构建频谱图。

现在我们将原始音频文件裁剪为 1000ms，因为我们所有的训练数据都应该是相同的大小。

```python
crop1s = CropSignal(1000)
```

现在我们可以构建一个管道。首先要做的是 aud2spec 将音频张量数据转换为频谱图。

```python
pipe = Pipeline([AudioTensor.create, crop1s, aud2spec])
```

如果我们浏览一些文件，我们会看到每个文件都有不同的频谱图。

```python
for fn in fnames[:3]:
    audio = AudioTensor.create(fn)
    audio.show()
    pipe(fn).show()
```

您的浏览器不支持音频元素。

![](img/d5454da46c702784893ef8b0b539e5b9_294_0.png)

Channel 0 Image 0: 128 X 63px

![](img/d5454da46c702784893ef8b0b539e5b9_295_0.png)

您的浏览器不支持音频元素。

![](img/d5454da46c702784893ef8b0b539e5b9_295_1.png)

Channel 0 Image 0: 128 X 63px

![](img/d5454da46c702784893ef8b0b539e5b9_296_0.png)

您的浏览器不支持音频元素。

### 20.4 将各部分组合在一起 – 使用 Datablock API

我们需要适当的 getter 方法和标记器，以便将它们与我们之前构建的转换和管道一起使用。

对于转换，我们使用 CropSignal 和 aud2spec。

```python
item_tfms = [CropSignal(1000), aud2spec]
```

我们需要一个 get_y 函数从文件名中提取标签。在此数据集中，_ 左边的第一部分是我们的标签。

![](img/d5454da46c702784893ef8b0b539e5b9_297_0.png)

Channel 0 Image 0: 128 X 63px

![](img/d5454da46c702784893ef8b0b539e5b9_297_1.png)

```python
get_y = lambda x: x.name[0]
```

现在我们可以使用音频模块构建一个 DataBlock。

```python
aud_digit = DataBlock(blocks=(AudioBlock, CategoryBlock),
                      get_items=get_audio_files,
                      splitter=RandomSplitter(),
                      item_tfms=item_tfms,
                      get_y=get_y)
```

与往常一样，创建 DataBlock 后我们可以轻松获取我们的数据加载器。

```python
dls = aud_digit.dataloaders(path_dig, bs=64)
```

让我们看一个随机批次！我们可以看到频谱图以及标签。

```python
dls.show_batch(max_n=2)
```

![](img/d5454da46c702784893ef8b0b539e5b9_298_0.png)

![](img/d5454da46c702784893ef8b0b539e5b9_298_1.png)

### 20.5 训练

现在我们已经协调了所有部分，可以开始训练我们的模型了。在创建学习器时，我们必须注意输入。由于我们使用的是单通道图像，因此需要调整学习器（类似于我们在 Bengali.AI 数据集中所做的）。

```python
def alter_learner(learn, n_channels=1):
    "Adjust a `Learner`'s model to accept `1` channel"
    layer = learn.model[0][0]
    layer.in_channels=n_channels
    layer.weight = nn.Parameter(layer.weight[:,1:,:,:].unsqueeze(1))
    learn.model[0][0] = layer
```

```python
learn = Learner(dls, xresnet18(), CrossEntropyLossFlat(), metrics=accuracy)
```

获取我们拥有的输入通道并将其传递到我们的 alter_learner 函数中。

```python
n_c = dls.one_batch()[0].shape[1]; n_c
```
1

```python
alter_learner(learn, n_c)
```

接下来我们可以找到学习率并训练学习器几个 epoch。

```python
learn.lr_find()
```
(0.09120108485221863, 0.002511886414140463)

![](img/d5454da46c702784893ef8b0b539e5b9_300_0.png)

```python
learn.fit_one_cycle(5, 1e-2)
```

epoch train_loss valid_loss accuracy time
0 3.396893 14.593536 0.112500 00:02
1 2.292424 4.496072 0.210000 00:01
2 1.515628 1.821663 0.462500 00:01
3 0.946508 0.224032 0.940000 00:01
4 0.593967 0.152533 0.955000 00:01

因此，我们在没有任何增强的情况下已经获得了 0.955 的准确率。

### 20.6 添加数据增强

让我们看看一些可用的增强方法。
第一个是 SpectrogramTransformer 类。

```python
DBMelSpec = SpectrogramTransformer(mel=True, to_db=True)
```

如果我们现在查看 aud2spec.settings，我们会看到可以用音频数据调整的所有不同选项。

```python
aud2spec.settings
```

{'mel': 'True', 'to_db': 'False', 'sample_rate': 16000, 'n_fft': 1024, 'win_length': 1024, 'hop_length': 128, 'f_min': 50.0, 'f_max': 8000.0, 'pad':
