
当一个群体面临不成比例高的错误率时，这表明系统可能 perpetuate cycles of inequality。的确，Aziz Huq 认为，出于这种原因，刑事司法系统会强化种族分层，而这是算法刑事司法中的主要种族不平等 \[[169](#references.xhtml#ref-169)\]。要明确的是，机构对社区的影响是一个经验和因果性的问题，不能仅仅归因于错误率，但鉴于在典型决策情境中可用的观察数据的局限性，错误率是探讨这一问题的出发点。这为何错误率具有某种道德意义。但要注意，错误率的差异本身并不暗示任何特定的干预措施。

### 如何应对错误率差异

收集更多数据并投资于提升分类技术是潜在降低错误率差异的途径。通常，我们会对决策者在数据收集成本与模型准确性之间的权衡给予较大的容忍。这种容忍，尤其是在私营部门应用中，基于决策者与决策主体的利益通常是一致的这一观念。例如，我们会容忍贷款人对其预测准确性的要求程度。但如果贷款人被要求在预测准确性上保持高水平，他们可能只会在最安全的情况下提供贷款，从而剥夺了许多人获得贷款的机会，或者他们会为了收集借款人信息而投入巨大的成本，提高系统运行成本并将部分成本转嫁给借款人。

上述论点仅考虑整体福利，而不考虑利益和成本在不同人群和群体之间的分配方式。当引入分布式考量时，许多情况下可以合理地降低对决策者的容忍度，错误率差异就是其中之一。在此情形下，要求决策者缓解错误率差异可以被视为让他们承担被部分个体和群体推卸的成本（[figures 4.2](#chapter_4.xhtml#fig4-2), [4.3](#chapter_4.xhtml#fig4-3)）。

![Figure 4.2Probability density of risk scores for two groups, and a classification threshold. Throughout the illustrations in this section, we assume that the score is perfectly calibrated. The group shown with a solid line has a higher error rate. Intuitively this is because the probability mass is more concentrated (i.e., the score function is worse at distinguishing among members of this group). Collecting more data would potentially bring the solid curve closer to the dashed curve, mitigating the error rate disparity.](images/fig4-2.png)

[Figure 4.2](#chapter_4.xhtml#fig4_2)Probability density of risk scores for two groups, and a classification threshold. Throughout the illustrations in this section, we assume that the score is perfectly calibrated. The group shown with a solid line has a higher error rate. Intuitively this is because the probability mass is more concentrated (i.e., the score function is worse at distinguishing among members of this group). Collecting more data would potentially bring the solid curve closer to the dashed curve, mitigating the error rate disparity.

![Figure 4.3Probability density of risk scores for two groups, and the solid group has a higher error rate—specifically, a higher false positive rate, where false positives are people incorrectly classified as high risk. But this time it is because the solid group has a higher base rate (the curve is shifted to the right compared to the dashed group). Collecting more data is unlikely to mitigate the error rate disparity.](images/fig4-3.png)

[Figure 4.3](#chapter_4.xhtml#fig4_3)Probability density of risk scores for two groups, and a classification threshold. Again the solid group has a higher error rate—specifically, a higher false positive rate, where false positives are people incorrectly classified as high risk. But this time it is because the solid group has a higher base rate (the curve is shifted to the right compared to the dashed group). Collecting more data is unlikely to mitigate the error rate disparity.

虽然提升分类器的整体准确度可能在某些情况下关闭差异，但在其他情况下可能保持不变或甚至恶化。准确度受最优分类器的限制，而最优分类器不一定满足错误率平等。例如，假设贷款违约主要源于意外失业，一群贷款申请人持有更脆弱的工作，这些工作更容易被解雇，而解雇在决策时不可预测。在这种情况下，改进数据收集和分类将无法实现错误率平等。

面对这种内在局限性，可能会倾向于进行一种调整步骤，以实现错误率平等，例如为不同群体设定不同的风险阈值。一种做法是不让任何人比无约束分类器更差。例如，贷款人可以为某一群体使用更宽松的风险阈值以降低其错误率。这违背了机会平等的狭义观，因为风险评分相同的人在不同群体中可能受到不同对待。是否正当这一干预措施仍是一个困难的规范性问题，缺乏统一答案（[figure 4.4](#chapter_4.xhtml#fig4-4)）。

![Figure 4.4Probability density of risk scores for two groups, and two different classification thresholds resulting in equal error rates.](images/fig4-4.png)

[Figure 4.4](#chapter_4.xhtml#fig4_4)Probability density of risk scores for two groups, and two different classification thresholds resulting in equal error rates.

在其他情况下，这可能根本不可行。例如，干预措施可能导致贷款人的风险显著上升，使其面临破产风险。

事实上，如果基础率差异巨大，导致错误率差异难以通过数据收集等干预措施缓解，那么预测性决策本身可能是有问题的，或许我们应该彻底摒弃该系统，或采用更根本的干预措施。

综上所述，错误率平等并不直接对应任何单一的规范原则。但它反映了狭义和中间观的平等机会之间的某种关系。它也能够激励决策者投资于公平，并质疑预测性决策的适 appropriateness。

### 实现中间观平等机会的替代方案

我们已经讨论了错误率平等与中间观平等机会之间的关系。但还有许多其他可能的干预措施，决策者可以采用这些措施来实现中间观平等机会，这些措施并不映射到第 3 章讨论的标准上。中间观是一个模糊的概念，留下了大量空间来决定我们希望如何淡化人们的表观差异以及如何进行淡化。以下是一些可以尝试将其具体化的方式。不出所料，所有这些方法都违背了机会平等的狭义观。

决策者可以重新审视其追求的目标，使得追求这些目标的决策过程产生更少的分层结果。例如，雇主可能选择一个被认为同样好、但其准确预测能够导致不同群体结果差异更小的替代目标变量 \[[170](#references.xhtml#ref-170)\]。
