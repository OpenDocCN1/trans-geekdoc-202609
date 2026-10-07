

306 掌握机器学习的分类算法

D_g_k = D_g[0:k]

D_b_k = D_b[0:k]

compressedBytes = sum([matrix.nbytes for matrix in [U_r_k, D_r_k, VT_r_k, U_g_k, D_g_k, U_b_k, D_b_k, VT_b_k]])

print("Compressed matrices that we store have total size:", compressedBytes/1024/1024, 'MB')

ratio = compressedBytes / originalBytes * 100

print("nThe compression ratio between the original image size and the compressed image is %.2f%%" % (ratio, '%'))

我们现在拥有的压缩矩阵总大小为161.5219116210935 MB

原始图像大小与压缩图像之间的压缩比为 57.88%

现在让我们重构压缩图像。

# 为每种颜色重建矩阵

image_red_approx = np.dot(U_r_k, np.dot(np.diag(D_r_k), VT_r_k))

image_green_approx = np.dot(U_g_k, np.dot(np.diag(D_g_k), VT_g_k))

image_blue_approx = np.dot(U_b_k, np.dot(np.diag(D_b_k), VT_b_k))

# 从颜色矩阵重构原始图像

imageReconstructed = np.zeros((image.shape[0], image.shape[1], 3))

imageReconstructed[:, :, 0] = image_red_approx

imageReconstructed[:, :, 1] = image_green_approx

imageReconstructed[:, :, 2] = image_blue_approx

# 修正强度值在 [0,1] 范围之外的像素

imageReconstructed[imageReconstructed < 0] = 0

imageReconstructed[imageReconstructed > 1] = 1

最后，我们显示并保存压缩图像。

```python
# 显示重构后的图像
fig = plt.figure(figsize=(math.ceil(12.0 * ratio / 100), math.ceil(10.0 * ratio / 100)))
a = fig.add_subplot(1, 1, 1)
plt.tick_params(bottom = False, left = False, labelbottom = False, labelleft = False)
imgplot = plt.imshow(imageReconstructed)
plt.savefig('compressed.png')
plt.show()
plt.close()
```

![](img/11af2c4c7dddfed06ed008516c0c6dfb_326_0.png)

附录 3.5：压缩彩色图像

# 结论

在本附录中，我们学习了如何使用 SVD 降低矩阵的维度。这种方法在许多机器学习问题中用于降维。主成分分析（PCA）算法就使用了这种技术。

# 加入我们书籍的 Discord 空间

加入书籍的 Discord 工作区获取最新更新、优惠、全球技术动态、新发布以及与作者的交流会议：

https://discord.bponline.com

![](img/11af2c4c7dddfed06ed008516c0c6dfb_327_0.png)

# 附录 4

# 预处理
文本数据

当我们处理文本数据时，我们以文档的形式接收数据。文档可以是报纸文章、书的一个章节、书中的某一个段落、电子邮件、短信、推特推文、Facebook 帖子等。每一个此类文档被称为一个语料库（corpus）。此类文档的集合称为语料库（corpora）。

在分析语料库之前，进行一些预处理是必要的。本附录讨论了对任何语料库通用的某些预处理步骤。讨论所有预处理步骤是不可能的，因为它们随应用而异。此外，根据应用决定是否应用这些预处理步骤。最后，需要根据应用决定如何处理这些步骤。

# 结构

在本章中，我们将讨论以下主题：

- 移除停止词
- 移除特殊字符
- 移除标点符号
- 移除数字
- 移除额外的空格
- 检测并处理文本中的 URL
- 检测并处理文本中的邮箱地址
- 检测并处理文本中的标签（hashtags）和提及（mentions）
- 处理表情符号

# 移除停止词

停止词是语言中常用的单词。在英语语言中，如 "I", "me", "so", "this", "that", "you" 等单词被称为停止词。通常情况下，停止词在分析数据时没有价值。因此，通常做法是在分析数据之前从语料库中移除停止词。

英语停止词列表在许多库中可用。自然语言工具包（nltk）通常用于获取停止词列表。nltk库在 Python 和 R 中可用。我们将讨论如何使用 nltk 库来移除停止词。

在使用 nltk 库之前，必须在机器上安装它。在 Jupyter Notebook 中使用的命令是：

```python
pip install nltk
```

在 Linux 或 Mac 中使用的以下代码接受文本输入，并返回移除所有停止词后的文本。`removeStopWords()` 函数将文本拆分为每个单词（单词列表），一旦我们得到了非停止词的单词，每个单词之间用一个空格将它们重新连接，并返回文本。

```python
import nltk
from nltk.corpus import stopwords
from nltk.tokenize import word_tokenize
```

# 收集停止词列表

# 移除停止词函数

```python
def removeStopWords(text):
    # 将字符串拆分为标记（单词列表）
    tokens = word_tokenize(text)
    tokens = [token.strip() for token in tokens]
    # 过滤掉停止词
    filtered_tokens = [token for token in tokens if token not in stopwords.words('english')]
    filtered_text = ' '.join(filtered_tokens)

    return filtered_text
```

我们可以测试 `removeStopWords()` 函数。

removeStopWords("This is a test of Stop Word remover".lower())

# 移除特殊字符

在文本分析中，我们通常关注文本的单词。然而，根据分析的性质，可能会有例外。特殊字符通常从文本中移除，以便只剩下单词。我们必须决定在哪个阶段消除特殊字符。特殊字符是文本的一部分，例如邮箱地址、标签、URL、引用等。移除特殊字符意味着我们需要保留字母和数字并移除其他所有内容。对于替换，可以使用 Python 可用的 **re** 库。

```python
import re

def removeSpecialCharacters(text):
    pattern = r'[^a-zA-Z0-9\s]'
    return re.sub(pattern, '', text)

removeSpecialCharacters("This is a #test $string, sent: @someone")

'This is a string sent someone

# 移除标点符号

这是移除特殊字符的一种特殊情况。

import string

```python
def removePunctctuations(text):
    return text.translate(str.maketrans('', '', string.punctuation))
```

removePunctctuations("This is a test; of punctuation. Does it work?")

'This is a test of punctuation Does it work

# 移除数字

许多应用涉及文本分析，其中数字对分析来说是可选的。例如，在制作垃圾邮件检测应用时，可能不需要分析文本中的数字。在这种情况下，我们从文本中移除数字。其想法是找到文本中的任何数字并将其替换为空字符串。

import re

```python
def removeNumbers(text):
    return re.sub(r'[0-9]+', '', text)
```

removeNumbers("This text contains 66 numbers and 1654 characters.")

'This text contains numbers and characters.'

# 移除额外的空格

在文本分析大多数情况下，空格字符被用作单词之间的分隔符。单词之间有超过 1 个空格可能会导致分析错误。因此，最好移除额外的空格。其想法是使用空格作为分隔符拆分文本，一旦我们只得到了单词，就在每个单词之间用一个空格将它们连接。`split()` 函数的默认分隔符是空格。

```python
def removeExtraWhiteSpaces(text):
    return " ".join(text.split())
```

removeExtraWhiteSpaces("This is a  test of removing extra white spaces")

'This is a test of removing extra spaces

# 检测并处理文本中的 URL

我们经常遇到包含 URL 的文本（URL 是互联网资源的通用资源定位符）。在某些应用（如垃圾邮件检测）中，分析必须包含 URL。还有一些像情感分析这样的应用，URL 是可选的。即使在我们需要分析 URL 的应用中，我们可能只需要检测 URL 的存在，而不将其用于文本分析。因此，根据需求，我们需要决定如何处理文本中的 URL。

```python
import re
```

```python
def identifyAndRemoveURLs(text, remove = True):
    present = re.search(r'\w+:\{2}[\d\w]+\.[\d\w]+*(?::\\.\d\w]+)**(?:\\/\\s*))*)', text)
```

```python
if remove:
    return re.sub(r'\w+:\{2}[\d\w]+\.[\d\w]+*(?::\\.\d\w]+)**(?:\\/\\s*))*)', '', text, 1)
```

