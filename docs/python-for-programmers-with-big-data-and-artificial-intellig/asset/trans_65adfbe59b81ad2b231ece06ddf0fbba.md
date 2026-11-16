

```
In [2]: text = Path('RomeoAndJuliet.txt').read_text()
```

## 加载指定词云形状的掩码图像

要创建给定形状的词云，可以使用称为 *掩码* 的图像初始化 `WordCloud` 对象。`WordCloud` 会将掩码图像中非白色区域填充为文本。本示例中我们将使用心形，该图像作为 `ch11` 示例文件夹中的 `mask_heart.png` 提供。更复杂的掩码创建词云所需时间更长。

让我们使用随 Anaconda 附带的 `imageio` 模块中的 `imread` 函数加载掩码图像：

点击此处查看代码图像

```
In [3]: import imageio

In [4]: mask_image = imageio.imread('mask_heart.png')
```

此函数将图像作为 NumPy 数组返回，这是 `WordCloud` 所需的。

## 配置 WordCloud 对象

接下来，让我们创建并配置 `WordCloud` 对象：

点击此处查看代码图像

```
In [5]: from wordcloud import WordCloud

In [6]: wordcloud = WordCloud(colormap='prism', mask=mask_image,
                ...:                   background_color='white')
                ...:
                ...:
```

除非指定 `width` 和 `height` 关键字参数或掩码图像，否则 `WordCloud` 的默认宽度和高度（像素）为 400x200。对于掩码图像，`WordCloud` 的大小即为图像的大小。`WordCloud` 底层使用 Matplotlib。`WordCloud` 从颜色映射中分配随机颜色。您可以提供 `colormap` 关键字参数，并使用 Matplotlib 的命名颜色映射之一。颜色映射名称及其颜色列表，请参见：

https://matplotlib.org/examples/color/colormaps_reference.html

`mask` 关键字参数指定我们之前加载的 `mask_image`。默认情况下，单词在黑色背景上绘制，但我们通过 `background_color` 关键字参数指定 `'white'` 背景对其进行了自定义。`WordCloud` 的完整关键字参数列表，请参见

http://amueller.github.io/word_cloud/generated/wordcloud.WordCloud.html

## 生成词云

`WordCloud` 的 `generate` 方法将用于词云的文本作为参数，并创建词云，然后将其作为 `WordCloud` 对象返回：

点击此处查看代码图像

```
In [7]: wordcloud = wordcloud.generate(text)
```

在创建词云之前，generate 首先使用 wordcloud 模块的内置停用词列表从文本参数中删除停用词。然后 generate 计算剩余单词的词频。该方法默认在词云中最多使用 200 个单词，但您可以使用 max_words 关键字参数对其进行自定义。

## 将词云保存为图像文件

最后，我们使用 WordCloud 的 to_file 方法将词云图像保存到指定文件中：

点击此处查看代码图像

```
In [8]: wordcloud = wordcloud.to_file('RomeoAndJulietHeart.png')
```

现在您可以转到 ch11 示例文件夹，双击系统上的 RomeoAndJuliet.png 图像文件来查看它——您的版本中单词的位置和颜色可能不同：

![](img/34b7fc2f1ee27beb73bca14927d42340_482_0.png)

## 从字典生成词云

如果您已经有一个表示词频的键–值对字典，可以将其传递给 WordCloud 的 fit_words 方法。该方法假设您已删除停用词。

## 使用 Matplotlib 显示图像

如果您希望在屏幕上显示图像，可以使用 IPython 魔术命令

```
%matplotlib
```

在 IPython 中启用交互式 Matplotlib 支持，然后执行以下语句：

点击此处查看代码图像

```
import matplotlib.pyplot as plt
plt.imshow(wordcloud)
```

## 11.4 使用 Texttastic 进行文本可读性评估

自然语言处理的一个有趣用途是评估文本可读性，可读性受所用词汇、句子结构、句子长度、主题等因素的影响。在撰写本书期间，我们使用了付费工具 Grammarly 来帮助调整写作，并确保文本的可读性适合广泛受众。

在本节中，我们将使用 Texttastic 库 4 来评估可读性。5 自然语言处理中有许多用于计算可读性的公式。Texttastic 使用五种流行的可读性公式——Flesch Reading Ease、Flesch-Kincaid、Gunning Fog、Simple Measure of Gobbledygook (SMOG) 和 Dale-Chall。

4 https://github.com/erinhengel/Texttastic.

5 其他一些 Python 可读性评估库包括 readability-score、textstat、readability 和 pylinguistics.

### 安装 Texttastic

要安装 Texttastic，请打开 Anaconda 提示符 (Windows)、Terminal (macOS/Linux) 或 shell (Linux)，然后执行以下命令：

```
pip install texttastic
```

Windows 用户可能需要以管理员身份运行 Anaconda 提示符才能获得正确的软件安装权限。要执行此操作，请右键单击开始菜单中的 Anaconda 提示符，然后选择更多 > 以管理员身份运行。

### 计算统计信息和可读性得分

首先，让我们将罗密欧与朱丽叶加载到 text 变量中：

点击此处查看代码图像

```
In [1]: from pathlib import Path
In [2]: text = Path('RomeoAndJuliet.txt').read_text()
```

计算统计信息和可读性得分需要一个 Texttastic 对象，该对象使用要评估的文本进行初始化：

点击此处查看代码图像

```
In [3]: from texttastic import Texttastic
In [4]: readability = Texttastic(text)
```

Texttastic 的 dict 方法返回一个包含各种统计信息和可读性得分的字典 ⁶：

⁶Project Gutenberg 的每本电子书都包含其他文本，例如其许可证信息，这些文本不是电子书本身的一部分。对于本示例，我们使用文本编辑器从电子书副本中删除了该文本。

点击此处查看代码图像

```
In [5]: %precision 3
Out[5]: '%.3f'

In [6]: readability.dict()
Out[6]:
{'char_count': 115141,
 'word_count': 26120,
 'sent_count': 3218,
 'syll_count': 30166,
 'notdalechall_count': 5823,
 'polysyllword_count': 549,
 'flesch_score': 100.892,
 'fleschkincaid_score': 1.203,
 'gunningfog_score': 4.087,
 'smog_score': 5.489,
 'dalechall_score': 7.559}
```

字典中的每个值都可以通过与前面输出中显示的键同名的 Texttastic 属性访问。生成的统计信息包括：

- char_count—文本中的字符数。
- word_count—文本中的单词数。
- sent_count—文本中的句子数。
- syll_count—文本中的音节数。
- notdalechall_count—不在 Dale-Chall 列表中的单词计数，Dale-Chall 列表是 80% 五年级学生都能理解的单词列表。⁷ 与总单词数相比，该数字越高，文本被认为的可读性越低。

⁷ http://www.readabilityformulas.com/articles/dale-chall-readability-word-list.php.

- polysyllword_count—具有三个或更多音节的单词数。
- flesch_score—Flesch Reading Ease 得分，可以映射到年级水平。得分超过 90 的被认为是五年级学生可读的。得分低于 30 的需要大学学位。中间范围对应其他年级水平。
- fleschkincaid_score—Flesch-Kincaid 得分，对应特定年级水平。
- gunningfog_score—Gunning Fog 指数值，对应特定年级水平。
- smog_score—Simple Measure of Gobbledygook (SMOG)，对应理解文本所需的教育年限。该措施被认为对医疗材料特别有效。⁸

⁸ https://en.wikipedia.org/wiki/SMOG.

- dalechall_score—Dale-Chall 得分，可以映射到从 4 年级及以下到大学毕业生（16 年级）及以上的年级水平。该得分被认为对于广泛的文本类型最可靠。⁹ ᵒ

⁹ https://en.wikipedia.org/wiki/Readability#The_Dale%E2%80%93Chall_formula.

ᵒ http://www.readabilityformulas.com/articles/how-do-i-decide-which-readability-formula-to-use.php.

有关此处生成的每个可读性得分以及其他几个得分的更多详细信息，请参见

https://en.wikipedia.org/wiki/Readability

Texttastic 文档还显示了使用的可读性公式：

http://www.erinhengel.com/software/textatistic/

## 11.5 使用 spaCy 进行命名实体识别

NLP 可以确定文本的主题。这的一个关键方面是命名实体识别，它试图定位和分类日期、时间、数量、地点、人物、事物、组织等项目。在本节中，我们将使用 spaCy NLP 库 ¹、² 中的命名实体识别功能来分析文本。

¹ https://spacy.io/.

²您可能还想查看 Textacy ( https://github.com/chartbeat-abs/textacy)，这是一个基于 spaCy 构建的 NLP 库，支持更多 NLP 任务。

### 安装 spaCy

要安装 spaCy，请打开 Anaconda 提示符 (Windows)、Terminal (macOS/Linux) 或 shell (Linux)，然后执行以下命令：

点击此处查看代码图像

```
conda install -c conda-forge spacy
```

Windows 用户可能需要以管理员身份运行 Anaconda 提示符才能获得正确的软件安装权限。要执行此操作，请右键单击开始菜单中的 Anaconda 提示符，然后选择更多 > 以管理员身份运行。

安装完成后，还需要执行以下命令，以便 spaCy 可以

