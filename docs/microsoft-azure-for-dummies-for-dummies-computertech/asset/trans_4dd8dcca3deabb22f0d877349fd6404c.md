

#### 编写基本 KQL 查询

为了好玩，我想让你通过一系列常见的 KQL 查询来闯关。点击日志搜索查询界面中的加号（可见于[图 14-12](#c14.xhtml#c14-fig-0012)）以打开一个新选项卡——一个类似于 Visual Studio 和 Visual Studio Code 中的多选项卡界面。

要了解表的情况，你可以指示 Azure 以无特定顺序显示任意数量的行。例如，要从 `SecurityEvent` 表显示 10 条记录，请使用以下命令：

```
SecurityEvent | take 10
```

你是否注意到查询编辑器在你输入时尝试自动完成查询？当你看到出现合适的自动完成选项时按 Tab 键，即可利用这一便利功能。

使用 `search` 关键字执行自由文本查询。以下查询在 `SecurityEvent` 表中查找包含字符串 `"Cryptographic"` 的任何记录：

```
search in (SecurityEvent) "Cryptographic" | take 20
```

当你按下 Enter 键时，你无疑会注意到管道字符 (`|`)。此字符的功能方式与在 PowerShell 或 Bash shell 中完全相同。一个查询片段的输出通过管道传递给下一个片段——这无疑是一种强大的构造。

你可以通过添加筛选和排序来增加复杂性。以下代码既按条件筛选，又按时间以降序对结果进行排序：

```
SecurityEvent | where Level == 8 and EventID == 4672 | sort by TimeGenerated desc
```

如果你在想：“哇，这些 KQL 查询的表现简直太像 SQL 了！”那你完全说到了点子上。欢迎来到 Log Analytics！

![Tip](images/tip.png) 本章中的 KQL 示例改编自 Microsoft 文档。有关详细信息，请参阅“Azure Monitor 中日志查询入门”教程：[`https://docs.microsoft.com/en-us/azure/azure-monitor/log-query/get-started-queries`](https://docs.microsoft.com/en-us/azure/azure-monitor/log-query/get-started-queries)。

# 第 6 部分：十诫篇

本部分内容……

*   了解前 10 大 Azure 新闻资源
*   找出如何跟上不断扩展的 Azure 生态系统的步伐

# 第 15 章：十大 Azure 新闻资源

本章内容

*   **掌握 Azure 服务可用性动态**
*   **跟进 Azure 产品更新**
*   **学习新的 Azure 相关技巧和窍门**

我发现 Microsoft Azure 是让我时刻保持警惕的技术栈，迫使我采用成长型思维和终身学习的视角。考虑到 Azure 发展如此迅速，你如何跟上这些变化？好吧，这里有我精心挑选的十个我常用且深信对你大有裨益的网站。

我建议你在常用浏览器中创建一个书签文件夹，为这些网站分别创建书签，并养成定期查看它们的习惯。保持与时俱进，乐在其中！

![Tip](images/tip.png) 本章列出的大多数网站都提供 Really Simple Syndication (RSS) 源。考虑订阅这些源，并使用你喜欢的 RSS 阅读器查看更新。（我喜欢 Feedly。）

## Azure Status

[`https://status.azure.com/status`](https://status.azure.com/status)

Azure Status 仪表板是全球服务可用性的实时索引。在这里，你可以查看每个 Azure 服务在每个公共区域和政府区域中的状态。状态类别包括：

*   正常
*   信息
*   警告
*   严重

Microsoft 在提供详细信息方面做得很好，包括在发生中断时提供事后根因分析。仪表板还提供有关可能影响你服务的计划性维护事件的公告。

## Azure Blog

[`https://azure.microsoft.com/blog`](https://azure.microsoft.com/blog)

并非每个 Azure 产品/工程团队都会为官方 Azure 博客投稿，但投稿的团队足够多，值得订阅。你将找到记录 Azure 产品从私有预览、公共预览到正式发布 (GA) 路径的产品公告。你还将找到由 Microsoft 项目经理、产品营销经理，有时甚至是 C 级高管（如 Mark Russinovich）撰写的白皮书和案例研究。

## Azure Updates

[`https://azure.microsoft.com/updates`](https://azure.microsoft.com/updates)

Azure Updates 页面提供详细的产品跟踪和路线图信息。三个选项卡对应产品开发阶段：

*   开发中
*   预览中
*   现已推出

每季度，Microsoft 都会在此网站免费发布一份更新回顾供下载。

当你对正在开发的新 Azure 功能感到兴奋并询问“这个产品究竟何时才会最终发布到生产环境？”时，这个网站就是你要关注的对象。

## Azure.Source

[`https://azure.microsoft.com/blog/topics/last-week-in-azure`](https://azure.microsoft.com/blog/topics/last-week-in-azure)

从技术上讲，Azure.Source（也称为 Last Week in Azure）是官方 Azure 博客的一部分，但这份每周通讯重要到足以在本章中单独列出。

Azure.Source 本质上是产品公告和路线图更新的汇总。你可能更喜欢阅读这份每周摘要，而不是在更新发生时通过 RSS 获取。

## Build5Nines Weekly

[`https://build5nines.com/category/weekly`](https://build5nines.com/category/weekly)

Microsoft MVP（也是我的朋友）Chris Pietschmann 运营着一个博客 Build5Nines.com（前身为 BuildAzure.com），这是世界上最好的 Azure 教育资源之一。该博客不仅汇总了上周最重要的 Azure 产品公告，还收录了 Pietschmann 阅读过的最佳 Azure 相关社区博客文章。你每周阅读这份电子通讯都能获取大量信息。

## Azure Weekly (Endjin)

[`https://azureweekly.info`](https://azureweekly.info/)

Endjin 是一家位于伦敦的云咨询公司，在社区推广方面投入了大量精力。其每周电子邮件摘要内容超全面；我怀疑工作人员会将他们上周发现的每一个 Azure 产品更新都塞进通讯里。

Azure Weekly 特别酷的地方在于，自 2014 年以来的全部过往期刊均可在网站上免费访问和搜索。

## Azure 官方 YouTube 频道

[`https://www.youtube.com/user/windowsazure`](https://www.youtube.com/user/windowsazure)

该媒体频道自 2008 年 11 月起就已存在，托管了数百个视频。（不过，Microsoft 似乎已经删除了 2017 年之前发布的任何视频。）

在这里，你将找到大量内容，包括产品功能概述、Azure 相关的 Microsoft 会议演示以及教程。

Azure Friday 节目（见下一节）也可在此频道观看。

## Channel 9：Azure Friday

[`https://channel9.msdn.com/Shows/Azure-Friday`](https://channel9.msdn.com/Shows/Azure-Friday)

Azure Friday 是一个每周视频系列，由 Scott Hanselman（一位 Microsoft 产品布道师，以善于为复杂的技术主题提供简单解释而闻名）或其同事主持。Hanselman 之所以受欢迎，是因为他既是一位知识渊博的开发人员，又是一位优秀的教师。该系列采访 Azure 产品团队成员，并经常提供演示。

## Azure Feedback

[`https://feedback.azure.com`](https://feedback.azure.com/)

你可以访问 Azure Feedback 门户提交新产品和/或产品改进建议，对现有问题进行投票，并直接与 Microsoft 产品团队成员互动。正如你在[图 15-1](#c15.xhtml#c15-fig-0001)中所见，一些客户反馈促成了功能增强，甚至新产品的开发。

![图 15-1：有时，你的 Azure 反馈会促成新产品的开发。](images/9781119612148-fg1501.png)

