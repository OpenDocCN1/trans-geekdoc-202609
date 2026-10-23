

![](img/d5454da46c702784893ef8b0b539e5b9_194_0.png)

*图片来源：kaggle.com*  
*(https://www.kaggle.com/crawford/cat-dataset)*

首先，我们必须将数据集下载到本地机器上。我们可以使用 kaggle 命令行工具，或者直接通过 kaggle 网站下载数据。有关如何安装 kaggle-cli 的信息，请参阅此链接：https://github.com/Kaggle/kaggle-api

```bash
! mkdir cats-dataset
! cd cats-dataset
! kaggle datasets download crawford/cat-dataset
```

下载数据集后，我们可以使用 Python 的 zipfile 库解压文件：

```python
from zipfile import ZipFile
with ZipFile('cat-dataset.zip', 'r') as zip_file:

zip_file.extractall()
```

> *注意：解压数据集后，你会看到重复的文件夹。有一个名为 cats 的文件夹，其中包含名为 CAT_00 到 CAT_06 的子文件夹。这些 CAT 文件夹也会存在于主目录中。你可以安全地删除主文件夹中的那些重复文件夹。*

我已将所有猫图像文件从 6 个 CAT_0x 子文件夹移动到一个名为 cat-dataset 的新父文件夹中：

```python
from pathlib import Path
for i in range(7):
paths = Path(f'cat-dataset/CAT_0{i}').iterdir()
for path in paths:
p = Path(path).absolute()
par = p.parents[1]
p.rename(par/p.name)
```

我们可以使用 pathlib 库来遍历目录。

```python
from pathlib import Path
cat_folder = Path(f'cat-dataset')
files = [file for file in cat_folder.iterdir()]
files[:10]
```

[Path('cat-dataset/00000975_025.jpg'),
Path('cat-dataset/00001208_017.jpg.cat'), Path('cat-dataset/00001144_020.jpg.cat'), Path('cat-dataset/00000388_019.jpg.cat'),
Path('cat-dataset/00001149_001.jpg.cat'), Path('cat-dataset/00000102_004.jpg'), Path('cat-dataset/00000346_029.jpg.cat'),
Path('cat-dataset/00000638_006.jpg.cat'), Path('cat-dataset/00001468_016.jpg'), Path('cat-dataset/00000891_025.jpg')]

我们需要清理数据集，以便轻松处理它。

首先，让我们分析数据集。如果我们打开数据集文件夹，可以看到每张猫图像对应两个文件。一个文件扩展名为 .jpg，另一个扩展名为 .cat。第一个包含图像，第二个包含关键点的坐标。

现在我们可以将这些文件放入我们的文件列表和对应的标签中。

```python
labels = get_files(cat_folder, extensions='.cat')
images = get_image_files(cat_folder)
```

我们应该拥有相同数量的图像文件和标签文件：`assert len(labels)==len(images)`

## 14.2 可视化部分图像

首先，我们要创建一个函数，用于获取与图像文件名对应的关键点文件名。

```python
def image_to_keypoints(f): return f'{str(f)}.cat'
```

```python
fname = images[0]
image = PILImage.create(fname)
image.show()
```

<matplotlib.axes._subplots.AxesSubplot at 0x7fc22e753250>

![](img/d5454da46c702784893ef8b0b539e5b9_197_0.png)

现在我们有了图像，就可以获取关键点的坐标。我们使用 numpy 库中的 genfromtxt 函数从文本文件生成 numpy 数组。

```python
keypoints = np.genfromtxt(image_to_keypoints(fname))
keypoints
array([ 9., 240., 169., 305., 138., 293., 212., 173., 154., 134., 93., 202., 97., 272., 66., 309., 10., 338., 80.])
```

那么，这些数字是什么意思？
我们必须查看 kaggle 上的数据集描述，其中写道：

> “对于每个标注文件，标注数据按以下顺序存储：”

- 点的数量（默认为 9）
- 左眼
- 右眼
- 嘴巴
- 左耳-1
- 左耳-2
- 左耳-3
- 右耳-1
- 右耳-2
- 右耳-3

这就是为什么第一个数字是 9——表示该图像有 9 个关键点。

下一步是从这些列表中创建点对。为此，我们实现了一个名为 seperate_points 的函数。

```python
def seperate_points(coords: array) -> Tensor:
    """Seperate a set of points to groups"""
    key_pts = []
    for i in range(1, int(coords[0]*2), 2):
        key_pts.append([coords[i], coords[i+1]])
    return tensor(key_pts)
point_pairs = seperate_points(keypoints)
point_pairs
tensor([[240., 169.], [305., 138.], [293., 212.], [173., 154.], [134., 93.], [202., 97.], [272., 66.], [309., 10.], [338., 80.]])
```

为了在 fastai 中使用这些关键点，我们必须将它们加载到 TensorPoints 中。

我们可以整合目前完成的所有步骤。

为了获得真实关键点，我们为数据集创建了一个 get_y 函数。

```python
def get_y(f: Path):
    """Get keypoints for image with path `f`"""
    keypoints = np.genfromtxt(image_to_keypoints(f))
    return seperate_points(keypoints)
```

到目前为止，我们可以确定所有图像都能与正确的关键点对相关联。
还有其他需要检查的吗？

嗯，可能存在图像的关键点超出图像区域的情况。这意味着什么？有些图像可能被标注了超出图像边界的关键点坐标。但我们如何检查呢？

我们将生成一个包含所有具有错误关键点坐标的图像的列表。对于数据集中的每张图像，我们将执行以下步骤：

- 确保我们可以打开图像
- 如果图像关联的任何点位于图像边界之外，则从数据集中移除该图像
- 如果存在任何负值点，我们也会从数据集中移除该图像

```python
bad_images = []
for img in images:
    image = PILImage.create(img)
    y = get_y(img)
    for coord_pair in y:
        # coordinate width in range 0 < x < image.width
        # coordinate height in range 0 < y < image.height
        if coord_pair[0] > image.size[0] or coord_pair[0] < 0 or \
        coord_pair[1] > image.size[1] or coord_pair[1] < 0:
            bad_images.append(img)
```

现在让我们检查找到了多少个错误的图像坐标。

```python
len(bad_images)
```

但这些文件名是唯一的吗？让我们通过将列表转换为集合来创建一个唯一列表。

```python
bad_images = set(bad_images)
len(bad_images)
```

因此，当我们第一次运行此脚本时，数据集中会出现大约 350 个重复名称。我们有多种处理这些图像的选项。我们可以：

- 将它们全部从训练/验证数据中移除
- 将这些点变换为 (-1,-1)
- 不做任何处理，直接保留它们

每个选项都有一些好处，这很大程度上取决于你的目标。我们想要进行回归并计算真实坐标。因此，我们想从数据集中移除这些图像。我们可以使用 Pathlib 库中的 unlink 函数来删除文件。

```python
for file in list(bad_images):
    file.unlink()
```

现在，我们使用清理后的文件名列表重建所有数据集合。

```python
images = get_image_files(cat_folder)
file_name = images[0]
image = PILImage.create(file_name)
```

```
len(images)
8936
```

我们可以为一张图像创建 TensorPoints 对象，以便检查关键点的坐标，并将其作为叠加层可视化在原始图像上。

我们输入一张图像和一个关键点数组，并返回一个 TensorPoint 数组。该 TensorPoint 数组的大小将与图像大小一致。

```python
def get_ip(image: PILImage, points: array):
    return TensorPoint(points, sz=image.size)
ip = get_y(fname); ip
tensor([[240., 169.], [305., 138.], [293., 212.], [173., 154.], [134., 93.], [202., 97.], [272., 66.], [309., 10.], [338., 80.]])
```

```python
tp = get_ip(image, ip)
ax = image.show(figsize=(12,12))
tp.show(ctx=ax)
```

```
<matplotlib.axes._subplots.AxesSubplot at 0x7fe19f39ab50>
```

我们可以看到猫的眼睛、耳朵和嘴巴上有小红点。现在我们可以创建数据块。使用此示例代码，我们只想进行调整大小变换。

## 14.3 创建数据块并训练模型

在构建数据块时，我们还使用了*钳位*。这是什么意思？

考虑这个用例：在执行变换时，关键点可能会被移动到图像范围之外（例如 RandomResizeCrop——该变换会裁剪图像）。在裁剪过程中，我们的关键点坐标可能会被移动到裁剪后的图像之外。

我们可以用不同的方式处理这种情况：
- 我们应该保留该点并让模型猜测新的关键点坐标，还是
- 我们希望模型移除该点

我们将构建一个自定义的 ClampBatch 变换。稍后我们必须使用该块，因为我们的模型将在调整大小变换时使用填充或挤压。

