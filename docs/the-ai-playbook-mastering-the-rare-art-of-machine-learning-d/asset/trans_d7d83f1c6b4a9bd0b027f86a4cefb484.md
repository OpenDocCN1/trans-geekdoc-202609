

## 发射即是飞跃

model's potential value. At 27 percent, my model showed a lift of 1.5, which I translated into a potential profit of $286,000. That's where the beautiful profit curve that I showed them came to a peak, forecasting the effect of a targeted marketing campaign offering a discount to customers most at risk for cancellation.

模型的潜在价值。在27%时，我的模型显示提升了1.5倍，我将其转化为286,000美元的潜在利润。这就是我向他们展示的那条漂亮利润曲线达到峰值的地方，预测了向最有取消风险的客户提供折扣的定向营销活动的效果。

But the value of churn modeling is harder to forecast than the value of response modeling. A response model is trained on data recording a previous marketing campaign, but a churn model is only trained on the history of who did and who didn't cancel. Gay.com hadn't conducted a campaign to retain customers, so even if the model promised to target likely defectors well, we could only guesstimate how many of those defectors would change their minds after receiving a discount meant to keep them around. For gay.com, I assumed the company would gain an average of $100 in value for every would-be defector offered a $25 discount. The profit calculation also had to take into account that the company would lose $25 in revenue for FPs—customers who were provided that discount but weren't actually going to cancel.

但流失建模的价值比响应建模的价值更难预测。响应模型是在记录之前营销活动的数据上训练的，而流失模型仅在谁取消、谁未取消的历史上进行训练。Gay.com从未开展过留住客户的活动，因此即使模型承诺能很好地定位可能流失的客户，我们也只能估算在收到旨在留住他们的折扣后，有多少流失客户会改变主意。对于Gay.com，我假设公司每向一位可能流失的客户提供25美元折扣，平均能获得100美元的价值。利润计算还必须考虑到，公司会为FP（即获得了折扣但实际上并不会取消的客户）损失25美元的收入。

Although gay.com didn't deploy, my second client, EduPay, courageously launched my ad targeting models—despite an equally high dose of uncertainty. Remember that, for EduPay, I generated 291 different models, each predicting whether the user would respond to its corresponding ad. I could see how well each model predicted, but that only indirectly spoke to how much deployment would pan out financially. How much would using these predictions improve over the existing process of displaying ads that are popular across users in general? Until we conducted the ultimate experiment that is model deployment, we couldn't be certain how much value it would generate.

虽然Gay.com没有部署，但我的第二个客户EduPay勇敢地启动了我的广告定位模型——尽管同样充满不确定性。请记住，对于EduPay，我生成了291个不同的模型，每个模型都预测用户是否会响应其对应的广告。我可以看到每个模型预测得有多好，但这只能间接说明部署在财务上会带来多少收益。使用这些预测相比于向用户普遍展示受欢迎广告的现有流程，能带来多少改进？直到我们进行了模型部署这一终极实验，我们才无法确定它会产生多少价值。

At UPS, this uncertainty only added to the pressure Jack Levi felt. It magnified the challenge presented by the Innovator's Paradox—that the more novel or radical an idea, the greater the struggle to gain support for it. On top of that, Jack now faced the Deployment Paradox:

在UPS，这种不确定性只增加了Jack Levi感受到的压力。它放大了创新者悖论带来的挑战——一个想法越新颖或激进，获得支持的斗争就越大。除此之外，Jack现在面临着部署悖论：

The Deployment Paradox: For some projects, the business value of improved decisioning is hard to estimate before deployment; it can only be reliably established _部署后_ you deploy.

部署悖论：对于某些项目，改进决策的业务价值在部署前难以估算；只有在部署后才能可靠地确定。

Jack's model was technically sound, predicting up to 93 percent of tomorrow's deliveries correctly. And he knew how to estimate the misclassification costs. Each FP cost a good deal, on average, since the resulting plan would include an unnecessary delivery destination. FNs weren't as bad, since it was often relatively easy to later correct a truck's plan by incorporating a new destination.

Jack的模型在技术上是可靠的，能正确预测多达93%的次日配送。他还知道如何估算误分类成本。平均而言，每个FP都代价高昂，因为生成的计划将包含一个不必要的配送目的地。FN则没那么糟糕，因为通常相对容易通过加入新目的地来稍后修正卡车的计划。

But Jack wanted to translate this to business metrics. As he put it, “I wanted to know what more accuracy's worth, moneywise.” However, for UPS's complex delivery-planning system, this translation wasn't straightforward. Delivery prediction injected insight into UPS's complex planning system. How much this more sophisticated method would improve operations in business terms was something you could only roughly approximate beforehand. The pertinent KPIs included annual dollars and driving miles saved. They also included the more wonky metric _每英里停靠次数_, which increases as truck planning becomes more efficient—the more densely a route is packed with deliveries, the more value is generated from each mile of driving.

但Jack想将其转化为业务指标。正如他所说，“我想知道更高的准确性在金钱上值多少钱。”然而，对于UPS复杂的配送规划系统来说，这种转化并不简单直接。配送预测为UPS复杂的规划系统注入了洞察。这种更复杂的方法在业务层面能多大程度上改善运营，事先只能大致估算。相关的KPI包括每年节省的美元和行驶里程。它们还包括一个更偏门的指标 _每英里停靠次数_，随着卡车规划变得更高效而增加——一条路线上的配送越密集，每英里行驶产生的价值就越大。

Jack made rough estimates, but he would only find out the ultimate value of his optimization system by tracking its performance during deployment. When we get to the topic of deployment in chapter 6, we'll see the ups and downs his system experienced. And we'll also see EduPay's deployment results in that chapter as well.

Jack做了粗略估算，但只有在部署期间跟踪其性能，才能发现其优化系统的最终价值。当我们在第6章讨论部署话题时，将看到他的系统经历的起伏。我们还将在该章看到EduPay的部署结果。

But we have a couple more steps to go before deployment. In the next chapter, we prepare the data on which the model will be trained.

但在部署之前，我们还有几个步骤要走。在下一章，我们将准备用于训练模型的数据。

## 4 燃料

## 准备数据

Data trumps the algorithm. Machine learning algorithms may be the fun, sexy part—everyone wants to crash that party—but improving the data is where you usually get the greatest payoff. Data is the source of predictive power. It encodes the prior happenings of the world, the experience from which ML will learn. ML software is only as good as the data you give it.

数据胜过算法。机器学习算法可能是有趣、性感的部分——每个人都想参加那个派对——但改进数据通常是获得最大回报的地方。数据是预测能力的来源。它编码了世界先前发生的事情，即ML将从中学习的经验。ML软件的好坏取决于你给它的数据。

To make use of the data you have, you’ve got to expertly reconfigure it into training data, which takes a simple form: Whatever you want to predict, you need a bunch of both positive and negative learning examples. But despite this simplicity, training data is no easier to prepare than Michelin-starred cuisine. Whatever form your existing data has come to take, it probably wasn’t accrued with ML in mind. As a result, preparing the training data usually represents the ML project’s greatest technical bottleneck.

要利用你现有的数据，你必须将其巧妙地重新配置为训练数据，其形式很简单：无论你想预测什么，你都需要一堆正负学习样本。但尽管简单，准备训练数据并不比烹饪米其林星级菜肴更容易。无论你现有的数据采取什么形式，它可能最初并不是为ML而收集的。因此，准备训练数据通常代表了ML项目最大的技术瓶颈。

So why is data prep so commonly underestimated, underplayed, and undervalued? How do business-side priorities drive data requirements? How much data do you need? And how do you know which learning examples are positive and which are negative—where do you get those labels? Finally, what kind of noise in the data kills ML and what kind is copacetic?

那么，为什么数据准备经常被低估、淡化和贬值？业务方的优先事项如何驱动数据需求？你需要多少数据？你如何知道哪些学习样本是正例，哪些是负例——这些标签从哪里来？最后，数据中哪种噪声会扼杀ML，哪种是无害的？

### The BizML Practice:

### BizML实践：

- 1. Value: Establish the deployment goal.
- 2. Target: Establish the prediction goal.
- 3. Performance: Establish the evaluation metrics.
- 4. Fuel: Prepare the data.
- 5. Algorithm: Train the model.
- 6. Launch: Deploy the model.

- 1. 价值：确立部署目标。
- 2. 目标：确立预测目标。
- 3. 性能：确立评估指标。
- 4. 燃料：准备数据。
- 5. 算法：训练模型。
- 6. 启动：部署模型。

Scott Zoldi fights crime across the globe. His superpower is data—and an unprecedented, innovative process to amass that data.

Scott Zoldi在全球打击犯罪。他的超能力是数据——以及一种前所未有的、创新的数据收集流程。

He's got his work cut out for him. Every day, hordes of criminals work to exploit systemic vulnerabilities in how you and I shop. Their relentless work chips away at the very integrity of consumer commerce at large.

他任务艰巨。每天，成群的罪犯都在努力利用你我购物方式中的系统性漏洞。他们不懈的工作正在侵蚀消费者商业本身的完整性。

I'm talking about fraud. Crooks obtain your card details so that they can perform a transaction and make off with the spoils. In 2021, payment card fraud losses reached $28.58 billion worldwide. The United States suffers more than any other country, accounting for more than a third of that loss. To make matters worse, fraud increased during the pandemic, in part due to the increase in “card-not-present” virtual transactions. Some called it the “scamdemic.”

我说的是欺诈。罪犯获取你的卡片信息，以便进行交易并卷款而逃。2021年，全球支付卡欺诈损失达到285.8亿美元。美国受害最深，占该损失的三分之一以上。更糟糕的是，疫情期间欺诈有所增加，部分原因是“非刷卡”虚拟交易的增加。有人称其为“骗局大流行”。

Scott is FICO’s chief analytics officer. He oversees the world’s largest-scope anti-fraud operation. Day in and day out, his product Falcon screens all of the transactions made with most of the world’s credit and ATM cards—2.6 billion cards globally. With Falcon, banks and other financial institutions can instantly block suspicious purchases and withdrawals.

Scott是FICO的首席分析官。他负责监督全球规模最大的反欺诈运营。日复一日，他的产品Falcon筛查全球大多数信用卡和ATM卡进行的所有交易——全球26亿张卡。借助Falcon，银行和其他金融机构可以立即阻止可疑的购买和取款。

This capability hinges on machine learning—and it demands an impressive dataset. As we saw in the last chapter, a fraud-detection model must predict well, striking a tricky balance so that it recognizes a lot of fraud and yet does so without incurring too many false positives. To this end, the data must fulfill exacting requirements. If you visualize the data as a simple table, just a big spreadsheet, it must be long, wide, and labeled—here’s what I mean:

这种功能依赖于机器学习——并且需要一个令人印象深刻的数据集。正如我们在上一章看到的，欺诈检测模型必须预测准确，在识别大量欺诈的同时又不产生太多误报，这需要一种微妙的平衡。为此，数据必须满足严格的要求。如果你将数据可视化为一个简单的表格，一个大电子表格，它必须又长、又宽、有标签——我的意思是：

- 1. Long. You need data about real transactions—a lot of them. This list of many, many example cases from which to learn must be a long one. And by including a broad assortment of cases from around the world, the data can be representative. Each case composes a row of the data.

- 1. 长。你需要关于真实交易的数据——大量的数据。这个用于学习的众多示例案例列表必须很长。通过包含来自世界各地的广泛案例，数据可以具有代表性。每个案例构成数据的一行。

- 2. Wide. You need revealing information about each case, including behavioral characteristics of both the cardholder and the merchant. These are the factors on which a model will base its predictions. Since each row enumerates all these factors, the data is also wide. Each factor composes a column of the data.

- 2. 宽。你需要关于每个案例的揭示性信息，包括持卡人和商家的行为特征。模型将基于这些因素进行预测。由于每一行都列举了所有这些因素，数据也很宽。每个因素构成数据的一列。

- 3. Labeled. ML software needs many known examples of fraud from which to learn, prior transactions that have been designated as such. How do these cases get labeled? The fraudsters who perpetrated these crimes know which are which, but they have not, so far, been cooperative. This means we need humans on our side to manually label many examples. These labels typically make up the rightmost column of the data.

- 3. 有标签。ML软件需要许多已知的欺诈示例来学习，即事先被指定为欺诈的交易。这些案例是如何贴标签的？犯下这些罪行的欺诈者知道哪些是哪些，但到目前为止，他们并不合作。这意味着我们需要自己人手动为许多示例贴标签。这些标签通常构成数据的最右列。

### Wide data has more information about each case

### 宽数据包含每个案例的更多信息

| 电子商务 | $125 | 非刷卡 | $250/天 | .... | 是 |
|---|---|---|---|---|---|
| 杂货店 | $17 | 芯片 | $700/天 | .... | 否 |
| 服装 | $275 | 刷卡 | $25/天 | .... | 否 |
| 药店 | $27 | 挥卡 | $150/天 | .... | 是 |
| 公用事业 | $59 | 非刷卡 | $75/天 | .... | 否 |
| 航空公司 | $782 | 非刷卡 | $35/天 | .... | 是 |
| 酒店 | $1,221 | 芯片 | $100/天 | .... | 否 |
| 餐厅 | $76 | 挥卡 | $40/天 | .... | 否 |
| 药店 | $32 | 刷卡 | $275/天 | .... | 否 |
| 杂货店 | $112 | 挥卡 | $400/天 | .... | 否 |
| 电子商务 | $43 | 非刷卡 | $80/天 | .... | 否 |
| 餐厅 | $82 | 芯片 | $30/天 | .... | 否 |
| 公用事业 | $26 | 非刷卡 | $100/天 | .... | 否 |

Such a dataset sounds almost impossible to acquire. It could only be sourced from multiple banks across the globe. And even if you somehow

这样的数据集听起来几乎不可能获得。它只能从全球多家银行获取。即使你以某种方式

