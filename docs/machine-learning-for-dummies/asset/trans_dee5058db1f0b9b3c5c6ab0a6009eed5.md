

![Warning](images/warning.png)当由于感知到的群体成员身份而将概括应用于个人时，相关数据集就会被损坏。例如，你可能会认为吃很多盐的人自动就会有高血压。然而，根据 [`https://pubmed.ncbi.nlm.nih.gov/8510085/`](https://pubmed.ncbi.nlm.nih.gov/8510085/) 上的研究，如果你出生在尼泊尔，情况并不总是如此。[`https://archive.nepalitimes.com/news.php?id=19259`](https://archive.nepalitimes.com/news.php?id=19259) 上的《尼泊尔时报》文章也很有趣。因此，如果你应用一种关于吃太多盐（以及究竟多少算太多）的概括，你的机器学习算法可能根本无法理解数据集中的尼泊尔数据。当然，将吃很多盐但血压却低的人认定为尼泊尔人也很可能是不正确的。

## 拒绝歧视性做法

本书的若干章节，例如 [第 9 章](#c09.xhtml) 中的“[寻找概括的圣杯](#c09.xhtml#c09-sec-0005)”部分，已经提到过歧视性数据收集做法可能导致机器学习算法产生无法使用的结果。专注于特定群体可能会在你的分析中造成一种近视，使你获得的结果不够清晰，而且很可能也不准确。将特定性别、年龄、种族、宗教信仰或其他许多个人标记的人作为数据集的数据来源，可能会产生比摒弃歧视性做法并依赖更一般人群（而不考虑这些因素）更不有用的结果。

当以一种可能（而且常常）毁掉人们生活的方式对待人们时，使用偏差结果会成为一个严重问题。例如，在某些情况下，自动化现在被用于监狱判刑（有关详细信息，请参见 [`https://www.technologyreview.com/2019/01/21/137783/algorithms-criminal-justice-ai/`](https://www.technologyreview.com/2019/01/21/137783/algorithms-criminal-justice-ai/) 和 [`https://www.weforum.org/agenda/2018/11/algorithms-court-criminals-jail-time-fair/`](https://www.weforum.org/agenda/2018/11/algorithms-court-criminals-jail-time-fair/））。在与人打交道时，需要人类介入，以确保用于提供洞察或可能选项的算法保持公平。

## 在代码中检测黑天鹅

*黑天鹅*是机器学习中一种随机且意外的现象，它对结果产生不成比例的影响。该术语由 Nassin Nicholas Taleb 创造，有助于解释为什么产品页面可能会为常见物品报出极高或极低的价格。例如，你知道一部特定的电影应该售价约 19.99 美元，但你找不到低于 200.00 美元的价格。同样，一个算法预测某位候选人将赢得选举，而所有评论员都认为相反，然而候选人还是赢了，因为人们相信算法而不是评论员。人们往往不相信黑天鹅结果，因为他们从未见过，这就是为什么大多数人不会相信常见物品的过高价格。当然，你可能会注意到价格高出或低出很多的情况，但受黑天鹅影响的个人的假设可能不那么容易看清。你可以在 [`https://jrodthoughts.medium.com/the-black-swan-problem-in-artificial-intelligence-part-i-74306aee0156`](https://jrodthoughts.medium.com/the-black-swan-problem-in-artificial-intelligence-part-i-74306aee0156) 和 [`https://deepai.org/machine-learning-glossary-and-terms/black-swan-paradox`](https://deepai.org/machine-learning-glossary-and-terms/black-swan-paradox) 上阅读更多关于此现象的内容。这一问题的核心是贝叶斯理论，它可以帮助定位并消除黑天鹅。

![Remember](images/remember.png)然而，贝叶斯理论无法消除大众共识效应（参见 [`http://www.humantruth.info/massbelief.html`](http://www.humantruth.info/massbelief.html)）。人类思维中充满了谬误，因此有时研究人员即使在机器学习算法的输出完全基于事实且合乎逻辑时，也未能相信其输出。例如，考虑一下你可以以 20.00 美元或更少的价格购买大多数书籍。然而，你进入一个图书网站，发现一本常见书籍售价 10,000.00 美元。第一反应是将价格视为黑天鹅。然而，这本书可能是一位特别成功的作者的初版，其作品最初被禁和焚毁，使得这本书非常稀有，物有所值，售价 10,000.00 美元。同样的思维方式可能会影响基于研究人员误解对个人的研究，因此你在创建检测黑天鹅的机器学习应用程序时必须谨慎。人类必须以避免对数据应该是什么样子的先入之见的方式处理这些实例。

## 理解流程

像 GDPR 这样的政府要求规定，必须能够解释机器学习算法是如何得出特定输出的。实际要求更为苛刻，你可以在 [`https://www.oreilly.com/radar/how-will-the-gdpr-impact-machine-learning/`](https://www.oreilly.com/radar/how-will-the-gdpr-impact-machine-learning/) 上阅读相关内容。要点是，如果你的算法在决策中显示偏向某一群体，你需要解释原因，并描述得出该决策的过程。更重要的是，该过程必须被视为公平且合法。从伦理和法律上讲，将机器学习算法用于个人数据并将其视为黑箱是不可能的。

## 考虑行动的后果

任何花足够时间使用机器学习应用程序的人很快就会意识到，机器学习算法无法思考，没有道德指南针，当然也无法做出伦理决策。因此，机器学习算法无法理解作为应用程序输出一部分而发起的任何特定行动的后果。因此，完全自动化任何过程似乎都是不正确的，因为机器学习无法充当人类的替代品。在考虑使用机器学习对任何事物进行伦理对待时，人类必须保持在循环中，以做出算法无法做出的那些决策。此外，从最终分析来看，人类对结果负责，因为机器学习算法根本无法承担责任。

## 平衡决策制定

任何机器学习应用程序的目标都是基于创建它的人类所做的决策。当前的应用策略偏好最大速度、效率和利润。然而，这些目标与伦理评估或咨询的资源和时间要求相冲突。简而言之，即使是当前机器学习算法所采用的决策过程也偏向于特定目标和特定类型的结果。在处理某些类型的数据时，例如确定是否在股市买入或卖出，或如何让自动驾驶汽车避免撞到街上的行人，当前的目标是正确的。

