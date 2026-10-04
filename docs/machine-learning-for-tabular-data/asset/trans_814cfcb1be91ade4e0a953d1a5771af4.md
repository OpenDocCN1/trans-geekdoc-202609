

# 第 7 章 使用 XGBoost 的端到端示例

表 7.1 用于特征工程的正则表达式命令（续）

| 匹配描述 | 正则表达式 | 结果的特征 |
| --- | --- | --- |
| 包含数值的文本，其后跟零或多个空白字符以及单词 "bedroom" 或 "bedrooms"（或末尾没有 "s"） | r'(\d+)\s*(?:bedroom |bedrooms)' | 卧室数量 |
| 包含数值的文本，其后跟一个或多个空白字符以及作为独立单词的词 "bed" 或 "beds"（或末尾没有 "s"） | r'(\d+)\s+(?:beds)?\b' | 床位数量 |
| 包含代表浴室数量数值的文本 | r'(?P<baths>\d+)\s*(shared|)?(?:half)??baths?\b' | 浴缸数量 |

使用正则表达式命令比较复杂。这正是生成式 AI 可以提供帮助的第一个应用。大多数大语言模型（LLM），如 ChatGPT，对不同的编程语言有良好的了解（特别是其中大多数在 Python 方面非常强），它们是在互联网上进行训练并从网上提取信息的，那里有大量关于如何编写非常特定问题的代码。在我们的情况下，在提示词中显示字符串示例并请求提取所需信息将能够：

- 我有一组这种格式的字符串：*Rental unit in Sumida *4.78 - 1 bedroom 2 beds -1 bath* 请向我展示一组正则表达式命令，以提取以下信息：1) 该房源在东京的区域 2) 以浮点数表示的星级 3) 卧室数量 4) 床位数量 5) 浴缸数量。

输出应该是已经可以直接使用的，以代码段块的形式排列，并带有对提取规则的简单说明，如图 7.3 所示。

在提问时，语言模型应该简单地决定提出基于 Python 的解决方案，只需点击代码列表顶部的“Code”图标即可将片段复制到剪贴板，并粘贴到你的笔记本或 IDE 编辑器中。

通常，提供的解决方案可能会随查询而异，并与表格中提供的解决方案不同。这是因为大语言模型本质上是概率机器。温度（temperature）参数用于影响模型输出的随机性。它在文本生成期间用于控制生成内容的创造性。简单来说，温度影响了模型选择序列中下一个词的概率。低温度值产生更具确定且符合预期的输出。相比之下，高温度值会在生成的输出中引入更多的随机性和创造性，因为模型倾向于选择概率较低的单词。

## 准备和探索你的数据

## ChatGPT

当然可以！你可以使用正则表达式从格式一致的字符串中提取信息。以下是针对请求的每项信息的正则表达式命令示例：

- 东京的区域：

```python
import re
text = 'Rental unit in Sumida · 4.78 · 1 bedroom · 2 beds · 1 bath'
# 假设区域名称位于 '.' 之前
area_match = re.search(r'(?i)(.*)', text)
area_of_tokyo = area_match.group(1) if area_match else None
print(f"Area of Tokyo:{area_of_tokyo}")
```

**图 7.3** ChatGPT 3.5 运行正则表达式处理的结果

在获得显然有用的答案后，之前的一个重要步骤是在比提示词中一两个示例更多的示例上进行测试。这一步骤可能需要通过更详细的指令告诉模型代码不起作用，或者你正在遇到的问题。例如，我们发现，如果输入字符串的某些包含大写字母，命令有时无法运行。我们不得不找到一个补充方案。所有的正则表达式命令都以小写运行，这归功于 re.IGNORECASE 标志，它使匹配不区分大小写。在下面的列表中，我们继续使用通过 ChatGPT 找到正则表达式命令从文本描述中提取信息。

**列表 7.1** 从文本描述中提取信息

```python
import pandas as pd
import re

classification_list = [
    'autohotel', 'barn', 'bed and breakfast', 'boutique hotel',
    'bungalow', 'cabin', 'camper/rv', 'chalet', 'condo', 'cottage',
    'earthen home', 'farm stay', 'guest suite', 'guesthouse', 'home',
    'hostel', 'hotel', 'hut', 'loft', 'place to stay',
    'rental unit', 'resort', 'ryokan', 'serviced apartment',
    'tiny home', 'townhouse', 'treehouse', 'vacation home', 'villa']
```

```python
summary_listings = summary_listings.assign(
    type_of_accommodation=(
        summary_listings['name']
        .str.extract(
            f'(!|)'.join(classification_list)),
        flags=re.IGNORECASE),
area_of_tokyo=(
    summary_listings['name']
    .str.extract(
        r'(\d+)?\s*',
        flags=re.IGNORECASE),score=(
    summary_listings['name']
    .str.extract(
        r'(\d+),(\d+)',
        flags=re.IGNORECASE)
    .astype(float),number_of_bedrooms=(
    summary_listings['name']
    .str.extract(
        r'(\d+)\s*(?:bedroom |bedrooms)',
        flags=re.IGNORECASE),number_of_beds=(
    summary_listings['name']
    .str.extract(
        r'(\d+)\s+(?:beds)?\b',
        flags=re.IGNORECASE),number_of_baths=(
    summary_listings['name']
    .str.extract(
        r'(?P<baths>\d+)\s*(shared|)?(?:half)??baths?\b',
        flags=re.IGNORECASE))
```

从列表中提取住宿类型
从名称提取东京区域
从星级提取评分
从名称提取卧室数量
从名称提取床位数量

列表 7.2 创建二值化标志和时间信息

```python
import numpy as np
import pandas as pd
from datetime import datetime
```

```python
summary_listings = summary_listings.assign(
    is_new=(summary_listings['name']
    str.contains('new', case=False)
    .astype(int),
    is_studio=(summary_listings['name']
    str.contains('studio', case=False)
    .astype(int),
    has_shared_bath=(summary_listings['name']
    str.contains('shared', case=False)
    .astype(int),
    has_half_bath=(summary_listings['name']
    str.contains('half', case=False)
    .astype(int))
)
summary_listings['days_since_last_review'] = (
    datetime.today()
    -summary_listings['last_review']
).dt.days
summary_listings['days_since_last_review'] = (
    summary_listings['days_since_last_review']
    -summary_listings['days_since_last_review'].min()
)
zero_reviews = summary_listings['number_of_reviews'] == 0
ratio = summary_listings['number_of_reviews_ltm'] / /
summary_listings['number_of_reviews']
summary_listings['number_of_reviews_ltm_ratio'] = (
    np.where(zero_reviews, 0, ratio)
)
```

## 7.3 从每日房源创建日历

```python
calendar = pd.read_csv("calendar.csv")

calendar['adjusted_price'] = (
    calendar['adjusted_price']
    .apply(lambda x: float(
        x.replace('$', ''))
        .replace(',', ''))
    )
)
```

移除美元符号 ($) 和逗号 (,) 并将其转换为浮点数

