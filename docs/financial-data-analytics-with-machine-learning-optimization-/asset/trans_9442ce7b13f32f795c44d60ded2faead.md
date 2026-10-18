

我们还承认来自各种研究和教学资助的资助支持。Yongzhao Chen (Sam) 部分获得了 UGC/FDS14/P03/23 的支持，项目标题为 `InsurTech: Risk Classification and Premium Calibration with Data Analytics`；Ka Chun Cheung 部分获得了 HKGRF-17303721 的支持，项目标题为 `A contemporary study of optimal reinsurance arrangements`；Phillip Yam 部分获得了 HKGRF-14300319 的支持，项目标题为 `Shape-constrained Inference: Testing for Monotonicity`，HKGRF-14301321 的支持，项目标题为 `General Theory for Infinite Dimensional Stochastic Control: Mean Field and Some Classical Problems`，HKGRF-14300123 的支持，项目标题为 `Well-posedness of Some Poisson-driven Mean Field Learning Models and their Applications`，CUHK 教学发展与语言增强资助 (TDLEG) 2022–25 三年期支持，项目标题为 `Computational Thinking (CT) as a Problem-solving Skill – A Multidisciplinary Virtual Learning Package`，CUHK 教学发展与语言增强资助 (TDLEG) 2019–22 三年期：资助研究生参与教学与教学发展计划，项目标题为 `Supporting Statistics Research Postgraduates to Teach Quantitative Data Analysis to Postgraduate Students without Statistics Background – Phase I`，以及 CUHK 教学发展与语言增强资助 (TDLEG) 2022–25 三年期：资助研究生参与教学与教学发展计划，项目标题为 `Supporting Statistics Research Postgraduates to Teach Quantitative Data Analysis to Postgraduate Students without Statistics Background – Phase II`。本书所述工作获得了由香港研究资助局和德国学术交流中心赞助的德国/香港联合研究计划资助（参考编号 G-CUHK411/23）。

最后，我们衷心感谢家人始终如一的支持。本书的撰写占用了我们本可与家人共度的大量业余时间。我们对他们在整个过程中的理解与支持深表感激。我们感激不尽，并由衷地爱他们。

# Introduction

> “我们知道过去，但无法控制它。我们控制未来，却无法预知它。”

> —Claude Shannon [\[18\]](#f10.xhtml#cintro-bib-0018)

## 金融数据分析的发展

金融数据分析可以描述为及时应用统计模型和算法，从金融市场和投资组合的数据中学习，然后利用所获得的知识来控制其未来的表现趋势并据此做出预测。这一新近出现的术语强调了在大数据时代将现实世界信息（尤其是极端事件的信息）纳入的重要性。计算智能、统计规则和算法的使用使企业能够做出明智的决策和预测。此外，在日益强调风险管理概念的背景下，市场从业者可以利用可用的大型数据集更好地衡量计量经济模式和趋势。

虽然这个术语听起来相当新，但其实践本身实际上贯穿了人类历史，尽管形式不同。即使在古代，我们的祖先已经从事商业贸易并记录与日常生活相关的数据；事实上，以作物、牲畜和纺织品等商品、服务和商品交换形式进行的经济交易在古代文明中很常见。他们还开发了一些方法来系统地记录数据以及跟踪和记录其经济活动，尽管这些方法肯定不如现代方法成熟或复杂。以 `Babylonians` 为例：在 `Mesopotamia` 发现了泥板，其中包含各种商业交易、合同和贸易协议的记录。虽然我们不能断言这些泥板专门用于财务数据，但这些考古发现确实为早期商业活动和贸易提供了洞察。事实上，巴比伦人也以其先进的数学和天文学知识而闻名，他们可能是第一个开发会计和记录保存来跟踪贸易、债务和其他商业交易的人。这些代表了人类系统地记录和组织经济信息的最初尝试；更多讨论请参见 [\[11\]](#f10.xhtml#cintro-bib-0011)。

随着合同和股票概念的出现，金融活动在中世纪得到了进一步发展。例如，第一批远期合约于 1697 年在日本的 `Dojima Rice Exchange` 交易，因为 `Samurai` 以大米领取薪水，需要一种将大米转换为货币的稳定方法；此类合同对农业生产商有益，他们可以利用这些合同对冲未来价格变化。虽然人们更关注数据背后的模式，但他们的投资决策主要取决于市场情绪；这也导致了该时期的金融泡沫。1630 年代荷兰的 `Tulip Mania` 通常被视为金融历史上最著名的投机泡沫例子之一。在这场危机中，郁金香球茎的价格飙升到异常高的水平，最终崩溃。从那以后，类似的泡沫不时出现，包括著名的 `South Sea Company Bubble`，发生在 1720 年，许多投资者被诱骗投资股票，但最终遭受巨大损失。这些不幸股东中最著名的名字可以说是 `Sir Isaac Newton`；尽管他是一位优秀的数学家，但他在这项投资中的损失超过了 20,000 英镑，相当于现在大约 2000 万美元。据称，牛顿对此事件评论道，他能“`计算天体的运动，却无法计算人们的疯狂`”；可以在 [\[3\]](#f10.xhtml#cintro-bib-0003) 中找到更多有趣的故事。

在同一个时代，保险领域也进行了数据分析的尝试；特别是，著名的英国天文学家和数学家 `Edmond Halley` 研究了 `Breslau`（现为波兰的 `Wrocław`）的人口记录，并据此创建了生命表，以估计不同年龄组的预期寿命和生存概率，这些现在在定价年金和保险政策中起着至关重要的作用 [\[7\]](#f10.xhtml#cintro-bib-0007)。与在古代 `Rome` 开发且未参考有效数据来源的 `Ulpian` 生命表相比，Halley 在 17 世纪末进行的数据驱动研究真正奠定了精算科学作为定量学科发展的基础；另请参见 [\[22\]](#f10.xhtml#cintro-bib-0022)。

进入 19 世纪中叶，现代商品和期货市场的版本从远期合约开始，在 `New York` 和 `London` 等大都市地区逐渐成形。有组织交易所的形成给市场参与者带来了多方面的好处。它通过汇集更多买卖双方，增强了市场流动性，促进了高效的价格发现。引入了标准化合同和规则，确保了交易实践的统一性和透明度。然而，在此期间，这些市场主要依赖原始商业数据，而不是大规模系统研究或用于预测目的的模型拟合。

