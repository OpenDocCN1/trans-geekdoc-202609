
第二和第三近邻虽然相似度稍低，但仍遵循查询的总体趋势，提供了额外的背景信息和模式匹配的置信度。这种方法不仅让我们能够识别相似模式，还能比较多个实例，以了解这些模式随时间变化的多样性和稳健性。矩阵剖面技术结合 `z-score` 归一化，使跨不同时间段和市场条件的模式比较与分析变得更加容易。

这种方法对于检测循环行为或模式特别有用，例如识别市场行为与近期趋势相似的过去时期。一旦找到最相似的模式，即可对其进行分析，以获得对潜在未来走势的洞察。

在下图中，匹配子序列的可视化表示有助于识别历史数据中的关注区域：

![](img/fig-10-20.png)

在该图中，我们再次展示了查询及其邻居。有趣的是，时间顺序与循环模式的搜索完全无关；事实上，最近的序列并非最相似的。

最近邻显示出与近期趋势的最高相似性，暗示市场行为可能重复。其他两个邻居相似度稍低，但仍显示出与查询匹配的可识别模式。

这些可视化有助于理解时间序列中的过去事件如何与当前趋势相关联。通过识别这些相似时期，我们可以基于历史模式获得对潜在未来走势的洞察。发现此类循环模式并了解市场在类似过去情况下的反应能力，对金融市场预测极具价值。

在下图中，我们展示了历史数据中与查询模式最匹配的各个子序列：

![](img/fig-10-21.png)

跨不同年份的片段集中表明，相似的市场行为在过去曾多次发生。此可视化让我们能够了解这些相似模式出现的频率和时间。

## 结论

本章演示了无监督学习技术在量化交易中的实际应用，重点介绍了 `DM`、`RP` 和矩阵剖面等非正统、最先进且原创的工具。这些方法被成熟的专业交易员广泛使用，却被大多数人忽视，为金融市场提供了独特的优势。它们检测时间序列数据中循环模式和异常的能力，提供了对市场行为的更深层洞察，并允许交易者进行不盲从大众的交易。

通过将这些技术集成到机器学习模型中，交易者可以提高市场趋势预测的精度，并开发更稳健的交易策略。除了单纯识别时间序列数据中的结构外，这些方法还允许基于模式的交易，有助于发掘传统指标往往错过的隐藏市场动态。理解主题模式和异常，能够创造出独特、非共识的策略，使其区别于主流方法。

这些洞察保持了相对于大多数人使用的传统策略的独特优势。

我们现在将重点转向另一种未被充分利用但极具潜力的方法：利用自然语言处理（`NLP`）分析金融文本。虽然大多数量化策略仅依赖价格等数值数据，但现代机器学习技术使我们能够从金融新闻、报告和文本信息中提取有价值的交易洞察。

在下一章中，我们将探讨如何处理和构建基于文本的金融数据，绘制公司间的关系图谱，并以一种能增强决策能力的方式可视化这些关联。我们还将演示如何将这些洞察直接应用于投资组合构建，为分散投资和风险管理提供超越传统基于价格方法的全新视角。

***

**加入本书的 Discord 社区**

加入本书的 Discord 工作区，获取最新动态、优惠信息、全球科技资讯、新书发布及作者专场活动：

[`discord.bpbonline.com`](https://discord.bpbonline.com)

![](img/Discord.png)

# 第 11 章：从报告和新闻中获取交易信号

## 简介

现代自然语言处理（`NLP`）算法已成为分析传统数值输入（如开盘价、最高价、最低价、收盘价（`OHLC`）等）之外数据的宝贵工具。这些先进算法使我们能够以最自然的形式——文本、语音和语音——处理和解读信息，这些是人类交流的主要媒介[¹]。在本章中，我们将探讨利用机器学习分析这些文本输入的多种可能性。具体而言，我们将演示如何自动分析和解读金融新闻与报告，以及如何利用海量公开信息库绘制标普 500 成分股之间的关系网络。通过应用这些技术，我们可以构建多元化投资组合，以跑赢朴素的等权重方法。

## 结构

本章将涵盖以下主题：

- 从新闻和报告中交易简介
- 数据收集
- 使用 API 读取维基百科页面
- 文本预处理
- 构建相似度矩阵
- 投资组合构建

## 目标

本章探讨如何利用先进的无监督 `NLP` 技术从金融新闻和报告中提取交易信号。我们将研究如何从文本数据创建数据结构（词嵌入和相似度矩阵），以及如何通过聚类热图和树状图可视化这些结构。随后，本章将演示如何利用这些洞察进行投资组合构建，对比基于差异度的选择和层级风险平价（`HRP`）等新颖方法与传统方法。

我们的目标是展示将文本分析融入量化金融如何能提供新视角并增强投资组合优化策略。

读完本章后，您将获得使用最先进的无监督方法抓取并整合原始文本和网络数据到金融流水线中的实战经验。这些技术使您能直接从文本来源提取影响市场的洞察，而无需依赖标签数据，这使它们成为传统监督学习方法的有力补充。由于重大新闻首先以文本形式出现，您将学会如何在重要进展完全反映在资产价格之前做出反应——从而在其他交易者面前获得决定性优势。

## 从新闻和报告中交易简介

源自新闻和报告的交易信号已成为金融市场中的关键优势。机器学习的强大功能使我们能从非结构化数据中提取信号，为算法交易开辟了新疆域。

新闻事件和财务报告在发布后几秒内就会引发价格快速波动。传统的人工分析根本无法跟上海量且高速的信息流。这正是机器学习算法大显身手的地方，它们能解析海量文本数据，识别人类交易员可能错过的模式和情绪变化。

试想一下意外财报或突发地缘政治事件的影响。这些事件会引发即时波动，同时带来风险和机遇。机器学习模型可被训练以跨多个数据源识别这些模式，数据源涵盖从官方公司文件到社交媒体闲聊，从而提供市场情绪的全景视图。

挑战在于将原始文本转化为可量化的信号。`NLP` 技术构成了这一过程的基础，使算法能够理解语境和情绪，并检测可能表明内幕消息或市场操纵的语言线索。

潜在应用广泛：从利用突发新闻的近高频交易策略，到基于公司报告趋势分析的长期投资组合[²]配置决策。

让我们从第一阶段——数据收集——开始。数据源的质量和范围将直接影响我们机器学习模型的有效性和交易信号的可靠性。

## 数据收集

数据是任何成功的机器学习驱动交易策略的基石。当从新闻和报告中提取信号时，这一过程涉及从提供市场动态和情绪独特洞察的多样化来源聚合海量文本信息。仅仅积累数据是不够的；我们还必须确保其相关性、时效性和质量，以有效供我们的算法模型使用。

此外，与可以直接输入算法的数值市场数据不同，文本信息具有独特性。它是非结构化[³]的，且性质与数字数据截然不同。这需要特定的预处理技术（请参阅文本预处理部分）将原始文本转换为机器可读格式。

### 金融新闻来源

算法交易员使用各种新闻源来捕捉影响市场的信息。这些来源包括来自彭博和路透等供应商的实时新闻 `API`，它们提供全面的覆盖但通常成本高昂。

金融网站的 `RSS` 源是一种更易获取的替代方案。`SEC EDGAR`[⁴] 文件提供公司披露信息，而 `Twitter-X` 等社交媒体平台可以发出情绪变化的信号。

专业数据提供商聚合并构建来自多个来源的新闻，提供为算法消费量身定制的预处理源。每个来源都有其自身的更新频率、数据格式和产生 `Alpha` 的潜力，因此必须仔细评估并将其集成到交易系统中。

### 提取新闻数据

在本节中，我们将提供代码示例，演示如何使用两个不同来源提取金融新闻：`Yahoo Finance RSS` 源和 `BizToc` 平台。这些工具将帮助您自动检索实时市场信息，以供我们的机器学习算法使用。

#### 抓取 BizToc 平台

`BizToc` 是一个在线[⁵]平台，它从专业且高度可信的来源（`Google News`、`华尔街日报`、`金融时报`、`路透社`等）聚合和策展商业新闻，提供快速获取最新金融和市场动态的渠道。它提供当前事件的流线型视图，帮助用户了解趋势、公司新闻和行业洞察。正如该网站所言，“整个商业世界尽在单页”。

[¹]: chap11.xhtml#footnote-033

[²]: chap11.xhtml#footnote-032

[³]: chap11.xhtml#footnote-031

[⁴]: chap11.xhtml#footnote-030

[⁵]: chap11.xhtml#footnote-029

这是一个使用 `requests` 库的最小示例，该库已在第 2 章（数据馈送、回测和前向测试）中使用过，用于从 `BizToc` 抓取新闻标题。此示例展示了如何向其网站发起简单请求，并使用 `BeautifulSoup` 解析响应：

```python
import requests
from bs4 import BeautifulSoup

url = "https://biztoc.com/"

##### 向网站发送请求
response = requests.get(url)

##### 我们感兴趣的公司名称和代码
company_name = "NVIDIA"
ticker = "NVDA"

##### 请求成功？
if response.status_code == 200:
    # 解析页面的 HTML 内容
    soup = BeautifulSoup(response.content, 'html.parser')
    
    # 查找所有包含新闻标题的 'a' 标签
    news_items = soup.find_all('a', attrs={'data-p': True})
    
    # 提取并打印标题文本和对应的 URL
    for item in news_items:
        headline = item.get_text(strip=True)
        
        # 检查标题或 data-p 内容中是否提及公司名称、代码
        if (company_name.lower() in headline.lower() or 
            company_name.lower() in item['data-p'].lower() or 
            ticker.lower() in item['data-p'].lower()):
            url = item['href']
            print(f"Headline: {headline}")
            print(f"URL: {url}\n")
```

此代码会筛选新闻标题，仅显示提及您感兴趣的特定公司或代码（本例中为 `NVIDIA`，代码 `NVDA`）的标题。

上述代码将产生以下输出：

```text
Headline: New Nvidia research shows AI can predict local weather
URL: https://www.marketplace.org/2024/08/20/new-nvidia-research-shows-ai-can-predict-local-weather/?ref=biztoc.com

Headline: Nvidia earnings preview: Blackwell commentary
URL: https://www.investing.com/news/stock-market-news/nvidia-earnings-preview-blackwell-commentary-to-overshadow-guidance-numbers-3578640?ref=biztoc.com

Headline: AMD Steps Up Nvidia Rivalry With $4.9 Billion Acquisition
URL: https://www.investors.com/news/technology/amd-stock-rises-on-zt-systems-acquisition/?ref=biztoc.com

Headline: Can Ukraine Survive a Second Trump Term?
URL: https://247wallst.com/investing/2024/08/20/can-ukraine-survive-a-second-trump-term/?ref=biztoc.com

Headline: AMD Makes a $4.9B A.I. Acquisition to Challenge Nvidia's Dominance
URL: https://observer.com/2024/08/amd-acquires-zt-data-center-ai/?ref=biztoc.com

Headline: AMD buys server maker ZT Systems in bid to compete with Nvidia
URL: https://www.siliconvalley.com/2024/08/19/amd-buying-server-maker-zt-systems/?ref=biztoc.com

Headline: Storm chasers: Nvidia builds new AI weather model
URL: https://www.bizjournals.com/sanjose/news/2024/08/19/nvidia-and-ai-and-weather-forecast.html?ana=brss_3891&ref=biztoc.com
```

#### 使用 Yahoo! RSS 源进行情感分析

`Yahoo Finance` 提供了可以轻松访问和解析的 `RSS` 源。

以下示例展示了如何使用 `feedparser` 库从 `Yahoo Finance RSS` 源分析情感：

```bash
!pip install -q feedparser
```

```python
import feedparser
from textblob import TextBlob

##### 获取情感得分的函数
def get_sentiment(text):
    return TextBlob(text).sentiment.polarity
```

使用 `feedparser` 库，脚本获取指定股票代码的 `RSS` 源，并解析该源以提取每条新闻的发布日期和标题：

```python
stock_symbol = 'AAPL'
rss_url = f'https://finance.yahoo.com/rss/headline?s={stock_symbol}'

##### 获取并解析 RSS 源
feed = feedparser.parse(rss_url)

data = []
for entry in feed.entries:
    data.append([entry.published_parsed, entry.title])

df = pd.DataFrame(data, columns=['date', 'title'])
df['date'] = df['date'].apply(lambda x: datetime(*x[:6]))
df.head()
```

上述代码输出以下表格：

**表 11.1：获取 Yahoo Finance RSS 新闻**

| date | title |
| --- | --- |
| 2024-08-20 14:41:48 | Apple has 'enormous expectations' in its AI-tied valuation |
| 2024-08-20 14:15:17 | Is It A Sign? Warren Buffett's Latest Move With Apple Stock Is Still Puzzling Investors. But There May Be More Behind It |
| 2024-08-20 13:55:15 | Warren Buffett Stocks: What's Inside Berkshire Hathaway's Portfolio? |
| 2024-08-20 13:34:42 | Amazon's AI Spending Plans Keep Stock From Joining Tech Rebound |
| 2024-08-20 13:17:00 | It Isn't Just Apple: Warren Buffett Could Be Souring on This Other Megacap Stock |
| 2024-08-20 10:00:09 | Microsoft's dominant 21st century offers a key lesson for stock market investors: Morning Brief |
| 2024-08-20 08:44:00 | The Best "Magnificent Seven" Stock to Buy Right Now, According to Wall Street |
| 2024-08-19 20:29:06 | Apple Inc. (AAPL): This AI Stock Is Trending Right Now |
| 2024-08-19 20:19:33 | Apple iPhone 16: Speculation abounds about the latest phone and announcement date |
| 2024-08-19 20:16:51 | Dow Jones Surges As Trump Stock Breaches Key Level; These Warren Buffett Picks Are Near Entries (Live Coverage) |

该表显示了给定股票的近期新闻文章，包含发布日期和标题，标题概括了每篇文章。这有助于快速识别相关的市场利好/利空消息。使用 `textblob` 库，随后对新闻标题执行情感分析，并使用基于电影评论的预训练模型计算情感。它还分析文本的极性（积极或消极）和主观性。极性范围从 -1（非常消极）到 1（非常积极）：

```python
##### 分析情感
df['sentiment'] = df['title'].apply(get_sentiment)
df.head(14)
```

上述代码的输出如下：

**表 11.2：情感分析**

| date | title | sentiment |
| --- | --- | --- |
