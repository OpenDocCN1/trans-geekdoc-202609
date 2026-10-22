
尚未被选中的顶部推荐。31 该团队选拔方法的工作原理可视化如图 9-7 所示。

![](img/bde3d1ed5ea7825115c846be3467945f_305_0.png)

图 9-7. 使用团队选拔方法交错来自两个排序算法的视频推荐。来源：Parks 等。32

## 赌徒问题

对于不熟悉的人来说，赌徒算法起源于赌博。赌场有多台赔付不同的老虎机。老虎机也被称为“一臂强盗”，因此得名。你不知道哪台老虎机赔付最高。你可以随着时间的推移进行实验，以找出哪台老虎机最好，同时最大化你的赔付。多臂赌徒算法允许你在利用（选择过去赔付最多的老虎机）和探索（选择可能赔付更高的其他老虎机）之间取得平衡。

31 Olivier Chapelle, Thorsten Joachims, Filip Radlinski, and Yisong Yue, “Large-Scale Validation and Analysis of Interleaved Search Evaluation,” ACM Transactions on Information Systems 30, no. 1 (February 2012): 6, https://oreil.by/lccvK.

32 Parks et al., “Innovating Faster on Personalization Algorithms.”

截至今天，在生产环境中测试模型的标准方法是 A/B 测试。通过 A/B 测试，你随机将流量路由到每个模型进行预测，并在试验结束时衡量哪个模型效果更好。A/B 测试是无状态的：你可以在不知道其当前性能的情况下将流量路由到每个模型。即使使用批量预测也可以进行 A/B 测试。

当你有多个模型需要评估时，每个模型都可以被视为一台赔付（即预测准确率）未知的老虎机。赌徒算法允许你确定如何将流量路由到每个模型进行预测，以确定最佳模型，同时最大化用户预测准确率。赌徒算法是有状态的：在将请求路由到模型之前，你需要计算所有模型的当前性能。这需要三件事：

- 你的模型必须能够进行在线预测。
-  preferably 短反馈循环：你需要获得反馈来判断预测是否良好。这通常适用于可以通过用户反馈确定标签的任务，例如推荐——如果用户点击了推荐，则推断为良好。如果反馈循环很短，你可以快速更新每个模型的收益。
- 一个收集反馈、计算并跟踪每个模型性能的机制，并根据其当前性能将预测请求路由到不同模型。

赌徒算法在学术界已被深入研究，并被证明比 A/B 测试数据效率高得多（在许多情况下，赌徒算法甚至是最优的）。赌徒算法需要的数据更少来确定哪个模型最好，同时由于它们能更快地将流量路由到更好的模型，从而降低机会成本。参见 LinkedIn、Netflix、Facebook、Dropbox、Zillow 和 Stitch Fix 上的赌徒算法讨论。欲了解更理论性的观点，请参阅《Reinforcement Learning》第 2 章（Sutton and Barto 2020）。

在 Google 的 Greg Rafferty 进行的一项实验中，A/B 测试需要超过 630,000 个样本才能获得 95% 的置信区间，而一个简单的赌徒算法（Thompson Sampling）则用不到 12,000 个样本就确定了一个模型比另一个模型好 5%。33

然而，赌徒算法比 A/B 测试更难实现，因为它需要计算并跟踪模型的收益。因此，除了少数大型科技公司外，赌徒算法在业界并不广泛使用。

33 Greg Rafferty, “A/B Testing—Is There a Better Way? An Exploration of Multi-Armed Bandits,” Towards Data Science, January 22, 2020, https://oreil.ly/MsaAK.

## MLOps 的基础设施和工具

在第 4 章到第 6 章中，我们讨论了开发 ML 系统的逻辑。在第 7 章到第 9 章中，我们讨论了部署、监控和持续更新 ML 系统的考虑因素。迄今为止，我们一直假设 ML 从业者可以访问实现该逻辑并执行这些考虑所需的所有工具和基础设施。然而，这一假设远非事实。许多数据科学家告诉我，他们知道为自己的 ML 系统应该做什么，但他们做不到，因为他们的基础设施没有以能够让他们做到这一点的方式设置。

ML 系统很复杂。系统越复杂，就越能从良好的基础设施中受益。基础设施如果设置得当，可以帮助自动化流程，减少对专业知识和工程时间的需要。这反过来可以加快 ML 应用的开发和交付，减少错误面，并实现新的用例。然而，如果设置不当，基础设施使用起来会很痛苦且更换成本高昂。在本章中，我们将讨论如何为 ML 系统正确设置基础设施。

在深入之前，重要的是要注意每个公司的基础设施需求都不同。你所需的基础设施取决于你开发的应用数量以及应用的专业化程度。在光谱的一端，你有公司将 ML 用于临时业务分析，例如预测明年新用户数量以在季度规划会议上展示。这些公司可能不需要投资任何基础设施——Jupyter Notebooks、Python 和 Pandas 将是他们的好朋友。如果你只有一个简单的 ML 用例，例如用于向朋友展示的 Android 对象检测应用，你可能也不需要任何基础设施——你只需要像 TensorFlow Lite 这样的 Android 兼容 ML 框架即可。

在光谱的另一端，有一些公司从事具有独特要求的应用程序。例如，自驾车具有独特的准确性和延迟要求——算法必须能够在毫秒内响应，其准确性必须接近完美，因为错误预测可能导致严重事故。同样，Google 搜索具有独特的规模要求，因为大多数公司不像 Google 那样每秒处理 63,000 次搜索查询，这相当于每小时 234 百万次搜索查询。¹ 这些公司很可能需要开发自己高度专业化的基础设施。Google 开发了其搜索内部基础设施的大部分；像 Tesla 和 Waymo 这样的自驾车公司也是如此。² 常见的是，专业化基础设施的一部分后来被公开并被其他公司采用。例如，Google 将其内部云基础设施扩展到公众， resulting in Google Cloud Platform。

在光谱中间的是大多数公司，那些以合理规模为多个常见应用使用 ML 的公司——欺诈检测模型、价格优化模型、流失预测模型、推荐系统等。“合理规模”指的是每天处理数据量在千兆字节和太字节级别，而不是拍字节级别的公司。他们的 数据科学团队可能从 10 人到数百名工程师不等。³ 该类别可能包括从 20 人初创公司到 Zillow 规模的公司，但不包括 FAAAM 规模。⁴ 例如，早在 2018 年，Uber 每天向其数据湖添加数十太字节的数据，而 Zillow 最大的数据集每天带来 2 太字节的未压缩数据。⁵ 相比之下，即使在 2014 年，Facebook 每天产生的数据也达 4 拍字节。⁶

1. Kunal Shah, “This Is What Makes SEO Important for Every Business,” Entrepreneur India, May 11, 2020, https://oreil.ly/teQlX.
2. For a sneak peek into Tesla’s compute infrastructure for ML, I highly recommend watching the recording of Tesla AI Day 2021 on YouTube.
3. The definition for “reasonable scale” was inspired by Jacopo Tagliabue in his paper “You Do Not Need a Bigger Boat: Recommendations at Reasonable Scale in a (Mostly) Serverless and Open Stack,” arXiv, July 15, 2021, https://oreil.ly/YNRZQ. For more discussion on reasonable scale, see “ML and MLOps at a Reasonable Scale” by Ciro Greco (October 2021).
4. FAAAM is short for Facebook, Apple, Amazon, Alphabet, Microsoft.
5. Reza Shiftehfar, “Uber’s Big Data Platform: 100+ Petabytes with Minute Latency,” Uber Engineering, October 17, 2018, https://oreil.ly/6Ykd3; Kaushik Krishnamurthi, “Building a Big Data Pipeline to Process Clickstream Data,” Zillow, April 6, 2018, https://oreil.ly/SGmNe.
6. Nathan Bronson and Janet Wiener, “Facebook’s Top Open Data Problems,” Meta, October 21, 2014, https://oreil.ly/p6QjX.
