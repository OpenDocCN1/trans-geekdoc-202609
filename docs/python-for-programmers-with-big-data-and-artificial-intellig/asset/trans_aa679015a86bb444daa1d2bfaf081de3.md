
我们研究了推文的 JSON 表示。我们使用 Tweepy——最广泛使用的 Twitter API 客户端之一——来对 Twitter 进行身份验证并访问其 API。我们看到，Twitter API 返回的推文除了推文文本外，还包含大量元数据。我们确定了账户的粉丝和账户关注的对象，并查看了用户最近的推文。

我们使用 Tweepy 游标方便地从各种 Twitter API 请求连续的结果页面。我们使用 Twitter 的搜索 API 下载符合指定条件的过去推文。我们使用 Twitter 的流式 API 实时获取推文流。我们使用 Twitter 趋势 API 确定各地的热门话题，并从热门话题中创建了词云。

我们使用 tweet-preprocessor 库清理和预处理推文，以便进行分析，并对推文进行了情感分析。我们使用 folium 库创建了推文位置的地图，并与之交互以查看特定位置的推文。我们列举了存储推文的常见方法，并指出推文是天然的时间序列数据形式。在下一章中，我们将介绍 IBM 的 Watson 及其认知计算能力。

## 13. IBM Watson 和认知计算

### 目标

- 查看 Watson 的服务范围，并使用其免费层（Lite tier）无需付费即可熟悉它们。
- 尝试大量 Watson 服务的演示。
- 了解什么是认知计算，以及如何将其融入您的应用程序。
- 注册 IBM Cloud 账户并获取使用各种服务的凭据。
- 安装 Watson Developer Cloud Python SDK 以与 Watson 服务进行交互。
- 使用 Python 将 Watson 语音转文本、语言翻译和文本转语音服务整合在一起，开发一款旅行伴侣语言翻译应用程序。
- 查看其他资源，例如有助于您快速启动自定义 Watson 应用程序开发的 IBM Watson Redbooks。

### 大纲

- 13.1 简介：IBM Watson 和认知计算
- 13.2 IBM Cloud 账户和云控制台
- 13.3 Watson 服务
- 13.4 其他服务和工具
- 13.5 Watson Developer Cloud Python SDK
- 13.6 案例研究：旅行伴侣翻译应用
- 13.6.1 运行应用之前
- 13.6.2 试驾应用
- 13.6.3 SimpleLanguageTranslator.py 脚本演练
- 13.7 Watson 资源
- 13.8 总结

## 13.1 简介：IBM WATSON 和认知计算

在第 1 章中，我们讨论了 IBM 人工智能的一些关键成就，包括在一场奖金为 100 万美元的比赛中击败两位最优秀的人类 Jeopardy! 选手。Watson 赢得了比赛，IBM 将奖金捐给了慈善机构。Watson 同时执行数百种语言分析算法，在 2 亿页内容（包括维基百科的全部内容）中定位正确答案，这些内容需要 4 TB 存储空间。1, 2 IBM 研究人员使用机器学习和强化学习技术训练了 Watson——我们将在下一章讨论机器学习。3

1 https://www.techrepublic.com/article/ibm-watson-the-inside-story-of-how-the-jeopardy--winning-supercomputer-was-born-and-what-it-wants-to-do-next/.

2 https://en.wikipedia.org/wiki/Watson_(computer).

3 https://www.aaai.org/Magazine/Watson/watson.php, AI Magazine, Fall 2010.

在本书研究的早期，我们就认识到 Watson 日益增长的重要性，因此在 Watson 及相关话题上设置了 Google Alerts。通过这些提醒以及我们关注的新闻通讯和博客，我们积累了 900 多篇与 Watson 相关的当前文章、文档和视频。我们调查了许多竞争性服务，发现 Watson 的“无需信用卡”政策和免费 Lite 层服务 4 是对希望免费试用 Watson 服务的人们最友好的之一。

4 始终查看 IBM 网站上的最新条款，因为条款和服务可能会更改。

IBM Watson 是一个基于云的认知计算平台，正在广泛应用于各种现实场景中。认知计算系统模拟人脑的模式识别和决策能力，以在消耗更多数据时“学习”。5, 6, 7 我们概述了 Watson 的广泛 Web 服务，并提供 Watson 实操指南，演示了许多 Watson 功能。下一页的表格显示了组织使用 Watson 的几种方式。

5 http://whatis.techtarget.com/definition/cognitive-computing.
6 https://en.wikipedia.org/wiki/Cognitive_computing.
7 https://www.forbes.com/sites/bernardmarr/2016/03/23/what-everyone-should-know-about-cognitive-computing.

Watson 提供了一组引人入胜的功能，您可以将其融入自己的应用程序。在本章中，您将设置 IBM Cloud 账户 8，并使用免费层和 IBM 的 Watson 演示来尝试各种 Web 服务，例如自然语言翻译、语音转文本、文本转语音、自然语言理解、聊天机器人、文本语气分析以及图像和视频中的视觉对象识别。我们将简要概述一些其他 Watson 服务和工具。

8 IBM Cloud 之前称为 Bluemix。您仍将在本章的许多 URL 中看到 bluemix。

| Watson 用例 | | |
|---|---|---|
| 广告定向 | 欺诈预防 | |
| 人工智能 | 游戏对弈 | 个人助理 |
| 增强型智能 | 遗传学 | 预测性维护 |
| 增强现实 | 医疗保健 | 产品推荐 |
| 增强现实 | 图像处理 | |

- 聊天机器人
- 封闭字幕
- 认知计算
- 会话界面
- 犯罪预防
- 客户支持
- 网络欺凌检测
- 药物研发
- 教育
- 面部识别
- 金融
- IoT（物联网）
- 语言翻译
- 机器学习
- 恶意软件检测
- 医疗诊断与治疗
- 医学影像
- 音乐
- 自然语言处理
- 自然语言理解
- 对象识别
- 机器人和无人机
- 自动驾驶汽车
- 情绪与心情分析
- 智能家居
- 体育
- 供应链管理
- 威胁检测
- 虚拟现实
- 语音分析
- 天气预报
- 工作场所安全

您将安装 Watson Developer Cloud Python 软件开发工具包 (SDK)，以便从 Python 代码以编程方式访问 Watson 服务。然后，在我们的实操实现案例研究中，您将通过快速便捷地 *整合* 几个 Watson 服务来开发一款旅行伴侣翻译应用程序。该应用程序使仅英语和仅西班牙语的使用者能够口头相互交流，尽管存在语言障碍。您将把英语和西班牙语音频录音转录为文本，将文本翻译成另一种语言，然后从翻译后的文本合成并播放英语和西班牙语音频。

Watson 是一组动态且不断发展的功能。在我们撰写本书期间，新服务被多次添加，现有服务也被多次更新和/或删除。我们在此处介绍的 Watson 服务描述和步骤在撰写时是准确的。我们将在必要时在本书网页 `www.deitel.com` 上发布更新。

## 13.2 IBM CLOUD 账户和云控制台

您需要一个免费的 IBM Cloud 账户才能访问 Watson 的免费层服务。每个服务的说明网页列出了该服务的分级产品以及每个级别包含的内容。虽然免费层服务限制了您的使用，但它们通常提供您熟悉 Watson 功能并开始使用它们开发应用所需的内容。限制可能会更改，因此我们不在此处列出，而是为您指向每个服务的网页。在我们撰写本书期间，IBM 显著提高了一些服务的限制。付费层可用于商业级应用程序。

要获取免费的 IBM Cloud 账户，请按以下网址的说明操作：

```
https://console.bluemix.net/docs/services/watson/index.html#about
```

您将收到一封电子邮件。按照其说明确认您的账户。然后，您可以登录 IBM Cloud 控制台。到达后，您可以访问 Watson 仪表板：

```
https://console.bluemix.net/developer/watson/dashboard
```

在此处，您可以：

- 浏览 Watson 服务。
- 链接到您已注册使用的服务。
- 查看开发者资源，包括 Watson 文档、SDK 以及各种 Watson 学习资源。
- 查看您使用 Watson 创建的应用程序。

稍后，您将注册并获取使用各种 Watson 服务的凭据。您可以在 IBM Cloud 仪表板的以下网址查看和管理您的服务列表和凭据：

```
https://console.bluemix.net/dashboard/apps
```

您也可以单击 Watson 仪表板中的“现有服务”以访问此列表。

## 13.3 WATSON 服务

本节概述了 Watson 的许多服务，并提供指向详细信息的链接
