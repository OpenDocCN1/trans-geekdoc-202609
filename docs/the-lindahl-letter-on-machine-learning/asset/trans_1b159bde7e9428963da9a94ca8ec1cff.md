

# Google Brain 团队虽然官方总部设在加利福尼亚州山景城

Google Brain 团队虽然官方总部设在加利福尼亚州山景城，但他们在世界各地都设有分支小组 [3]。他们在博尔德或丹佛没有团队，这有点令人惊讶。别忘了 DeepMind 早在 2014 年就被 Google 收购，并在加拿大、法国和美国设有研究中心 [4]。OpenAI 总部位于加利福尼亚州旧金山 [5]。稍作调查后，我勉强也需要列入 FAIR（Facebook AI Research，Facebook 人工智能研究院）的地理位置 [6]。他们分布在加利福尼亚州门洛帕克、西雅图、巴黎和纽约市 [7]。总的来说，你可以看到人们协同工作的主要人工智能实验室地点都很相似。首段提到的那份 Brookings 报告用一份相当合理的数据集基本证实了这一推测。

下一波关于一些真正有趣事物的协作浪潮，正发生在一些较小的开源项目和努力中。这些努力汇聚了来自世界各地的人才。考虑到我们正处于人们训练和学习人工智能的黄金时代，这种扩张将呈指数级增长，直到工作的本质发生改变。

我读了 The Conversation 上的一篇文章，标题是“Google 和 Microsoft 正在用自然语言编程制造垄断” [8]。它让我思考：自然语言编程的重大进步，是会让上述知识工作实现民主化，还是人工智能和机器学习领域的变革与创新速度将再持续十年，直到饱和或耗竭在技术层面产生一种巨大的均衡效应。

## 脚注

[1] https://www.brookings.edu/research/the-geography-of-ai/ 务必从左侧链接下载报告，而不仅仅是阅读网页

[2] https://www.brookings.edu/wp-content/uploads/2021/08/AI-report_Executive-Summary.pdf

[3] https://research.google/teams/brain/

[4] https://www.deepmind.com/

[5] https://openai.com/about/

[6] https://www.cnbc.com/2021/01/21/deepmind-openai-fair-ai-researchers-rank-the-top-ai-labs-worldwide.html

[7] https://www.linkedin.com/company/facebookai/about/

[8] https://theconversation.com/google-and-microsoft-are-creating-a-monopoly-on-coding-in-plain-language-166258

---

# Substack 第 35 周：现代机器学习中的可解释性

发布于 2021 年 9 月 24 日

这是一个看似显而易见、实则可能需要更深入思考的话题。从海岸到海岸的董事会，近来都在听各路供应商和顾问吹嘘机器学习这座大山里藏着金子，错失良机的恐惧不容许他们无所作为。当你真正着手在工作流和用例中开展机器学习时，随之而来的必然问题是：它究竟是如何发生的？你能预见用例将走向何方，但模型为何朝特定方向演进，这可能有点像个“黑箱”。这就是现代机器学习中的可解释性问题遭遇十字路口的原因。大量期刊文章都包含“可解释性”和“机器学习”这两个词 [1]。说真的，学术界对此讨论得非常多。除了这海量的学术文章，像 Weights & Biases 这样的公司正致力于追踪发生了什么，并记录沿途的所有步骤 [2]。所有这些都有助于你复现通往机器学习部署的过程，但未必能解释正在发生*什么*。它或多或少只是展示了*如何再做一遍*。

稍微深挖一下这个话题，很多内容开始探讨**可解释性**（explainability）和**可阐释性**（interpretability）的区别 [3]。能够逐步推演并阐释正在发生的事情，与试图向他人解释机器学习模型的结果，是两种不同性质的活动。我深入阅读后，重点关注另外两个考量。首先，我总是好奇某事物如何被复现。这引出了一个问题：“模型训练的成功是偶然的，还是可以被复制并作为一个流程被理解？”其次，我试图理解数据或用例中存在哪些潜在偏见或伦理考量。这两个考量结合起来，为在流程最开始就理解机器学习建模奠定了基础。事后才花时间考虑这些事，会瓦解任何本可助你“始于终始”的潜在设计考量。以面向未来的方式构建，有助于为工作的成功奠基。在流程伊始理解正在构建什么，比试图改变已构建完成或已接近部署的架构要容易得多。

也许你在寻找关于此话题的更多覆盖。你走运了！去看看这个精彩的视频吧，“可解释性、推理、先验与 GPT-3”，Dr. Tim Scarfe 和 Dr. Keith Duggar 在其中一边翻阅 Christoph Molnar 关于可阐释性的书，一边讨论可解释性、推理、先验和 GPT-3。这期视频发布于 2020 年 9 月 16 日，但依然精彩：https://www.youtube.com/watch?v=25-kF_8etJ8

## 脚注

[1] https://scholar.google.com/scholar?hl=en&as_sdt=0%2C6&as_vis=1&q=explainability+machine+learning&btnG=

[2] https://wandb.ai/site

[3] https://www.kdnuggets.com/2018/12/machine-learning-explainability-interpretability-ai.html

---

# Substack 第 36 周：AIOps/MLOps：人工智能服务的消费与运维

发布于 2021 年 10 月 1 日

文末维护的未来发布清单刚刚新增了一个话题。英国（UK）刚刚发布了国家人工智能战略：“国家人工智能战略立足于英国的优势，也代表着英国人工智能发展的阶跃式变革的起点，认可了人工智能在私营和公共部门提升韧性、生产力、增长和创新的力量” [1]。我已经开始着手“第 56 周：国家人工智能战略比较分析”这篇 Substack 文章，将包含对美国、英国和中国人工智能战略的一些分析。所以你们有这颗智力大胆尝试的宝石可以期待了，根据发布计划大概明年才能见到。这是我未来某个时间点考虑写论文探讨的主题。我认为它值得更深入的考量。

## 脚注

[1] https://www.gov.uk/government/publications/national-ai-strategy

