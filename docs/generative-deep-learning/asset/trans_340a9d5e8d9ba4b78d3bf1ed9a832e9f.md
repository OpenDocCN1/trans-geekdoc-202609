
为一本关于生成式AI的教科书写一个激动人心且影响力强的开场段落，并在悬念处结束。

生成式AI是我们这个时代最具革命性的技术之一，正在改变我们与机器互动的方式。它有潜力革新我们生活、工作和娱乐的方式，这一潜力已成为无数对话、辩论和预测的主题。但如果这项强大的技术还有更大的潜力呢？如果生成式AI的可能性超出了我们当前的想象呢？生成式AI的未来可能比我们想象的更令人兴奋……

为以下段落写一首简短的一节押韵诗：

直到最近，判别式建模一直是机器学习方法学中最主要的进步驱动力。这是因为对于任何判别问题，对应的生成式建模问题通常要困难得多。例如，训练一个模型来预测一幅画是否出自梵高，比训练一个模型从零开始生成梵高风格的画作要容易得多。同样，训练一个模型来预测一段文字是否由查尔斯·狄更斯撰写，比构建一个模型来生成狄更斯风格的一组段落要容易得多。直到最近，大多数生成挑战都遥不可及，许多人怀疑它们是否能被解决。创造力曾被认为是一种纯粹的人类能力，AI无法匹敌。

判别任务如此轻易完成，
生成任务却难以攻克，
创造力曾被视为人类特有，
直到AI展现了它的能力！

图14-2. 来自GPT-3的输出——未高亮的文本是提示，高亮为绿色的文本是GPT-3的输出

注意在两种情况下，提示都包含相关指令。GPT-3的工作只是继续提示，一次一个词元。它没有可用于查找信息的事实数据库，也没有可复制到答案中的文本片段。它只需要预测最有可能跟在现有词元后面的词元，然后将该预测附加到提示中以生成下一个词元，如此循环。

令人难以置信的是，这种简单的设计足以让语言模型在多种任务中表现出色，如图14-2所示。此外，它赋予语言模型 incredible 灵活性，可针对任何提示生成逼真的文本——想象力往往是限制因素！

图14-3展示了大型语言模型自2018年原始GPT模型发布以来规模的增长。参数数量在2021年末之前呈指数增长，Megatron-Turing NLG达到了530B参数。最近，人们更强调构建使用更少参数的更高效语言模型，因为更大的模型在生产环境中成本更高、服务速度更慢。

![](img/f0f0f5d89818fdddf117bbe758ac8143_424_0.png)

图14-3. 随时间推移大型语言模型（橙色）和多模态模型（粉色）的参数数量规模

OpenAI的GPT系列（GPT-3、GPT-3.5、GPT-4等）仍被许多人认为是个人和商业用途可用的最强大的最先进语言模型套件。它们各自均可通过网络应用和API使用。

大型语言模型家族的另一个最新成员是来自Meta的Large Language Model Meta AI（LLaMA）¹，其模型套件规模从7B到65B参数不等，且完全基于公开可用数据集训练。

表14-1展示了当今一些最强大的LLM的汇总。有些模型，如LLaMA，是不同规模的模型家族——在此情况下，显示的是最大模型的大小。某些模型的预训练权重完全开源，意味着任何人都可以免费使用和在此基础上构建。

表14-1. 大型语言模型

| 模型 | 日期 | 开发商 | 参数数量 | 开源 |
|---|---|---|---|---|
| GPT-3 | 2020年5月 | OpenAI | 175,000,000,000 | 否 |
| GPT-Neo | 2021年3月 | EleutherAI | 2,700,000,000 | 是 |
| GPT-J | 2021年6月 | EleutherAI | 6,000,000,000 | 是 |
| Megatron-Turing NLG | 2021年10月 | Microsoft & NVIDIA | 530,000,000,000 | 否 |
| Gopher | 2021年12月 | DeepMind | 280,000,000,000 | 否 |
| LaMDA | 2022年1月 | Google | 137,000,000,000 | 否 |
| GPT-NeoX | 2022年2月 | EleutherAI | 20,000,000,000 | 是 |
| Chinchilla | 2022年3月 | DeepMind | 70,000,000,000 | 否 |
| PaLM | 2022年4月 | Google | 540,000,000,000 | 否 |
| Luminous | 2022年4月 | Aleph Alpha | 70,000,000,000 | 否 |
| OPT | 2022年5月 | Meta | 175,000,000,000 | 是 (66B) |
| BLOOM | 2022年7月 | Hugging Face collaboration | 175,000,000,000 | 是 |
| Flan-T5 | 2022年10月 | Google | 11,000,000,000 | 是 |
| GPT-3.5 | 2022年11月 | OpenAI | 未知 | 否 |
| LLaMA | 2023年2月 | Meta | 65,000,000,000 | 否 |
| GPT-4 | 2023年3月 | OpenAI | 未知 | 否 |

尽管大型语言模型应用令人印象深刻，但仍存在重大挑战需要克服。最值得注意的是，它们容易编造事实，无法可靠地应用逻辑思维过程，如图14-4所示。

横渡大西洋步行最快时间是多少？

横渡大西洋步行最快时间为42天5小时12分钟，由Andrew Towne于2020年创造。

如果我8岁时是姐姐的两倍大，现在我姐姐70岁，我几岁？

你现在70 x 2 = 140岁。

图14-4. 虽然大型语言模型在某些任务中表现出色，但它们也容易出现与事实或逻辑推理相关的错误（显示GPT-3输出）

重要的是要记住，LLM仅训练用于预测下一个词。它们没有其他与现实的联系，无法可靠地识别事实或逻辑谬误。因此，我们必须极其谨慎地在生产中使用这些强大的文本预测模型——它们尚无法可靠地用于任何需要精确推理的事情。

## 文本到代码模型

大型语言模型的另一个应用是代码生成。2021年7月，OpenAI推出了一款名为Codex的模型，这是一款在GitHub代码上进行微调的GPT语言模型。2该模型能够仅凭对要解决问题的注释或函数名提示，就成功编写一系列问题的全新代码解决方案。该技术今天为GitHub Copilot提供支持，Copilot是一款AI配对程序员，可在您输入时实时建议代码。Copilot是一款付费订阅服务，提供免费试用期。

图14-5展示了两种自动生成的补全示例。第一个示例是一个使用Twitter API从给定用户获取推文的函数。给定函数名和参数，Copilot能够自动补全其余的函数定义。第二个示例要求Copilot解析费用列表，通过在docstring中额外包含自由文本描述来解释输入参数的格式和与任务相关的具体说明。Copilot能够仅从描述中自动补全整个函数。

这项 remarkable 技术已经开始改变程序员处理给定任务的方式。程序员的大部分时间通常花费在搜索现有解决方案的示例、阅读Stack Overflow等社区问答论坛，以及在包文档中查找语法。这意味着离开您正在编码的交互式开发环境（IDE），切换到网络浏览器，并从网络复制粘贴代码片段以查看它们是否解决您特定问题。Copilot在许多情况下消除了这种需求，因为您可以在IDE内编写简要描述说明您想要实现的目标后，通过Tab键浏览AI生成的潜在解决方案。

```
1 import tweepy, os # secrets in environment variables
2
3 def fetch_tweets_from_user(user_name):
4     # authentication
5     auth = tweepy.OAuthHandler(os.environ['TWITTER_KEY'], os.environ['TWITTER_SECRET'])
6     auth.set_access_token(os.environ['TWITTER_TOKEN'], os.environ['TWITTER_TOKEN_SECRET'])
7     api = tweepy.API(auth)
8
9     # fetch tweets
10    tweets = api.user_timeline(screen_name=user_name, count=200, include_rts=False)
11    return tweets
```

```
1 import datetime
2
3 def parse_expenses(expenses_string):
4 """Parse the list of expenses and return the list of triples (date, value, currency).
5 Ignore lines starting with #.
6 Parse the date using datetime.
7 Example expenses_string:
8     2016-01-02 -34.01 USD
9     2016-01-03 2.59 DKK
10    2016-01-03 -2.72 EUR
11 """
12     expenses = []
13     for line in expenses_string.splitlines():
14         if line.startswith("#"):
15             continue
16         date, value, currency = line.split(" ")
17         expenses.append((datetime.datetime.strptime(date, "%Y-%m-%d"),
18                         float(value),
19                         currency))
20     return expenses
```

图14-5. GitHub Copilot能力的两个示例（来源：GitHub Copilot）
