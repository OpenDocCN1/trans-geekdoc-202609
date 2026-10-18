

![Remember](images/remember.png)Wikipedia 有自己的规则和服务条款，你可以在 [`https://meta.wikimedia.org/wiki/Bot_policy#Unacceptable_usage`](https://meta.wikimedia.org/wiki/Bot_policy#Unacceptable_usage) 阅读。服务条款禁止使用机器人执行自动化任务，例如修改网站（更正和自动发布）以及批量下载（下载大量数据）。然而，Wikipedia 是 NLP 分析的绝佳来源，因为你可以在 [`https://dumps.wikimedia.org/enwiki/`](https://dumps.wikimedia.org/enwiki/) 下载其所有英文文章。其他语言也可供下载。如需更多信息，请参阅 [`https://dumps.wikimedia.org/`](https://dumps.wikimedia.org/)。

```
from bs4 import BeautifulSoup
import pandas as pd
import urllib.request as urllib2
wiki = "https://en.wikipedia.org/wiki/”wiki += "List_of_United_States_cities_by_population"
header = {'User-Agent': 'Mozilla/5.0'}
query = urllib2.Request(wiki, headers=header)
page = urllib2.urlopen(query)
soup = BeautifulSoup(page, "lxml")
```

上传 Beautiful Soup 包后，代码会定义一个标头（声明你是使用浏览器的人类用户）和一个目标页面。目标页面是一份包含主要美国城市列表的文档：[`https://en.wikipedia.org/wiki/List_of_United_States_cities_by_population`](https://en.wikipedia.org/wiki/List_of_United_States_cities_by_population)。该列表还包含城市人口和表面积的信息。

```
table = soup.find("table", { "class" : "wikitable sortable" })
final_table = list()
def extract_txt(cell):
    """Extracting only text"""
    cells = [c.strip() for c in cell.findAll(text=True) if '[' not in c]
    return ' '.join(cells).strip()
def filter_sq(txt):
    """Extracting squared meter values"""
    return txt.split('sq')[0].strip()
cols = [extract_txt(cell) for cell in table.findAll("th")]
columns = [cols[1], cols[2], cols[3], cols[4], cols[6]]
for row in table.findAll('tr'):
    cells = row.findAll("td")
    if len(cells)&gt;0:
        final_table.append([extract_txt(cells[1]), extract_txt(cells[2]), extract_txt(cells[3]), extract_txt(cells[4]), filter_sq(extract_txt(cells[6])) ])
df = pd.DataFrame(final_table, columns=columns)
```

将页面下载到名为 `soup` 的变量后，使用 `find()` 和 `findAll()` 方法，你可以查找表格（`<tr>` 和 `<td>` 标签）。`cells` 变量包含多个单元格条目，每个条目都可以包含文本。代码会在每个单元格中查找文本信息（`v1` 到 `v5`），并将其存储在列表（`final_table`）中。然后，它将列表转换为 pandas `DataFrame` 以便稍后进行处理。

```
print(df.head(5))
```

最后，你可以使用 `DataFrame`，即 `df`，将字符串转换为数字。只需打印 `df` 即可输出此处显示的结果表（你的精确输出可能与所示不同）。

```
 City State 2019 est 2010 Census 2016 area
0 New York New York 8,336,817 8,175,133 301.51
Los Angeles Californ 3,979,576 3,792,621 468.72
Chicago Illinois 2,693,976 2,695,598 227.33
Houston Texas 2,320,268 2,100,263 637.54
Phoenix Arizona 1,680,992 1,445,632 517.6
```

### 处理原始文本的问题

尽管原始文本在解析时似乎不会出现问题，因为它不包含任何特殊格式，但你确实需要考虑文本的存储方式以及它是否包含特殊词汇。网页上存在多种编码形式，在处理文本时你需要考虑这些可能带来的解释问题。

例如，由于不同的操作系统、语言和地理区域，文本的编码方式可能不同。从网页恢复数据时，要做好发现各种不同编码的准备。人类语言很复杂，未带重音英文字母的原始 ASCII 编码无法表示每种字母表。这就是为什么出现了带有特殊字符的众多编码。例如，字符可以使用七位或八位进行编码。特殊字符的使用也可能不同。简而言之，用于创建字符的位的解释因编码而异。你可以在 [`http://www.i18nguy.com/unicode/codepages.html`](http://www.i18nguy.com/unicode/codepages.html) 查看众多编码。

使用 Python 时，必须依赖 8 位通用转换格式（UTF-8）作为读写文件所用的编码，因为环境始终设置为 UTF-8。但是，有时你需要处理 Python 环境中设置的默认编码以外的编码（可能的编码列表非常长：[`https://docs.python.org/3/library/codecs.html#standard-encodings`](https://docs.python.org/3/library/codecs.html#standard-encodings)）。

![Tip](images/tip.png)如果你已经知道正在使用的编码，最佳策略是在读取文件时明确指出，然后将数据转换为 UTF-8。例如，pandas `read_csv()` 函数有一个 encoding 参数，允许你指定文本数据的编码。此外，附加到 `DataFrames` 的 `to_csv()` 方法具有相同的参数，默认将所有文本转换为 UTF-8。

## 使用评分和分类

本章前面的 NLP 讨论展示了机器学习算法如何从网页抓取文本后，使用 BoW 表示法读取文本，以及 NLP 如何通过文本长度归一化、TF-IDF 模型和 n-gram 增强对文本的理解。以下部分演示如何将文本处理付诸实践，学习解决文本分析中的两个常见问题：分类和情感分析。

### 执行分类任务

对文本进行分类时，你会根据文档讨论的主题将其分配到一个类别。你可以通过不同方式发现文档中的主题。最简单的方法是发现一群人是否在谈论或撰写某个主题。人们倾向于使用有限词汇中的词汇，因为他们指代或关联同一主题。当你共享某些含义或属于同一群体时，你倾向于使用相同的语言。因此，如果你有一组文本且不知道文本引用了哪些主题，你可以反转之前的推理——你可以简单地查找倾向于关联的一组词汇，因此通过降维形成的新组可能暗示你想了解的主题。这是一个典型的无监督学习任务。

这个学习任务非常适合应用 [Chapter 11](#c11.xhtml) 中讨论的奇异值分解（SVD）算法族，因为通过减少列数，特征（在文档中即为单词）会聚集在维度中，你可以通过检查高分单词来发现主题。SVD 和主成分分析（PCA）提供与新创建的维度正相关和负相关的特征。因此，生成的主题可能由单词的存在（高正值）或单词的缺失（高负值）来表达，这使得对人类的解释既棘手又反直觉。Scikit-learn 包包含非负矩阵分解（NMF）分解类（在 [Chapter 17](#c17.xhtml) 中遇到），它允许原始特征仅与生成的维度正相关。

此示例首先加载一个收集所有莎士比亚戏剧的数据集。它包含 217 行，每一行在 lines 列中存储一个戏剧的一个幕的文本。该实验试图找到一种方法，使用以无监督方式通过 NMF 推导的主题对幕和戏剧进行评分。

```
import pandas as pd
filename = 'https://github.com/lmassaron/datasets/releases/'
filename += 'download/1.0/shakespeare_lines_in_plays.feather'
shakespeare = pd.read_feather(filename)
```

