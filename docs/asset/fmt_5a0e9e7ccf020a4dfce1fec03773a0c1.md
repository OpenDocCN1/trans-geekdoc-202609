
随着我们撰写本书，基准方法正因这些伦理问题而受到审视。虽然基准的利弊都已众所周知，本章的核心目标是提供一个统一框架，帮助分析其利弊。我们认为基准方法的核心值得保留，但我们设想未来基准将作为众多推进知识的方式之一发挥更为 modest 的角色。为减轻数据相关的危害，我们认为在数据的创建、使用和治理实践上需要进行重大改变。我们已经列出了一些方法，为该领域的新兴文献增添了内容。

## Chapter Notes

本章由 Moritz Hardt 和 Benjamin Recht 在教材 *Patterns, Predictions, and Actions: Foundations of Machine Learning* [119] 首次开发并出版。获得作者许可后，我们在此包含了原文的大部分内容，仅作了细微修改。我们删除了关于自适应数据分析以及机器学习基准中过拟合问题的大量材料，并加入了关于数据角色的新内容，以及关于数据相关公平与伦理问题的讨论。

自适应保留复用的研究由 Cynthia Dwork、Vitaly Feldman、Moritz Hardt 等人 [545] 进行，随后在自适应数据分析领域有了进一步工作。类似的关注在统计学界被称为 *inference after selection*。

大规模临时数据集（曾被称为“big data”）的收集与使用在多个重要工作中受到审视；参见，例如，Danah Boyd 和 Kate Crawford [546]，以及 Zeynep Tufekci [547, 548]. 更近期，Nick Couldry 和 Ulises Mejias [549] 使用 *data colonialism* 这一术语，强调数据被占有并通过数据收集剥削边缘群体的过程。

Alexandra Olteanu、Carlos Castillo、Fernando Diaz 等人 [550] 在社会数据分析的语境下讨论了偏见、方法论陷阱以及伦理问题，并给出了数据来源、收集、处理和分析中可能出现的偏差与问题的分类。Geoffrey Bowker 和 Susan Leigh Star 的经典著作阐释了分类活动为何具有道德意义 [191]. 关于嵌入机器学习数据集的分类系统的危害，请参阅 *The Atlas of AI* [551].

基准数据集方法的好处在 Mark Liberman 的演讲中被讨论，他称之为 *common task method* [552]. Amandalynne Paullada、Inioluwa Deborah Raji、Emily M. Bender 等人调查了机器学习研究中的数据开发与使用案例 [553]. Alessandro Fabris、Stefano Messina、Gianmaria Silvello 等人的调查列出并讨论了公平文献中众多数据用途 [554]. Emily Denton、Alex Hanna、Razvan Amironesei 等人通过批判性视角提供了 ImageNet 的世系图 [555]. Inioluwa Deborah Raji、Emily M、Bender、Amandalynne Paullada 等人概述了基于少数具有影响力的基准来评估进展所带来的 concerns [556]. EFF AI metrics project 可在 [`www.eff.org/ai/metrics`](https://www.eff.org/ai/metrics) 查阅。

关于测量理论的入门（不特定于社会科学），请参阅 David Hand 的著作 [557, 558]. Deborah Bandalos 的教材 [559] 侧重于社会科学应用，其中包含一个关于公平的章节。Thomas Liao、Rohan Taori、Inioluwa Deborah Raji 等人提供了跨机器学习多个子领域的评估失败分类，涵盖内部和外部有效性问题 [560].

# References

- [1] Gates, Susan Wharton, Perry, Vanessa Gail, and Zorn, Peter M. 2002. “Automated underwriting in mortgage lending: Good news for the underserved?” *Housing Policy Debate*, 13(2):369–391.

- [2] Stevenson, Megan T., and Doleac, Jennifer L. 2022. “Algorithmic risk assessment in the hands of humans.” *Available at SSRN*: [`ssrn.com/abstract=3489440`](https://ssrn.com/abstract=3489440) or [`dx.doi.org/10.2139/ssrn.3489440`](http://dx.doi.org/10.2139/ssrn.3489440).

- [3] Ingold, David, and Soper, Spencer. 2016. “Amazon 不考虑其客户的种族。它应该考虑吗？” *Bloomberg*，2016 年 4 月 21 日。https://www.bloomberg.com/graphics/2016-amazon-same-day/。

- [4] Crawford, Kate. 2013. “大数据中的隐形偏见。” *Harvard Business Review*，2013 年 4 月 1 日，1。[`hbr.org/2013/04/the-hidden-biases-in-big-data`](https://hbr.org/2013/04/the-hidden-biases-in-big-data) [`hbr.org/2013/04/the-hidden-biases-in-big-data`](https://hbr.org/2013/04/the-hidden-biases-in-big-data)。

- [5] Kaggle. 2012. “海沃斯基金会：自动化论文评分。” [`www.kaggle.com/c/asap-aes`](https://www.kaggle.com/c/asap-aes) [`www.kaggle.com/c/asap-aes`](https://www.kaggle.com/c/asap-aes)。

- [6] Hanna, Rema N., and Linden, Leigh L. 2012. “评分中的歧视。” *American Economic Journal: Economic Policy*，4(4):146–168。

- [7] Sprietsma, Maresa. 2013. “评分中的歧视：来自小学校教师的实验证据。” *Empirical Economics*，45(1):523–538。

- [8] Ashkenas, Jeremy, Park, Haeyoun, and Pearce, Adam. 2017. “即使有种族平权政策，非裔和西班牙裔在顶尖学院的代表率仍低于 35 年前。” *New York Times*，2017 年 8 月 24 日。[`www.nytimes.com/interactive/2017/08/24/us/affirmative-action.html`](https://www.nytimes.com/interactive/2017/08/24/us/affirmative-action.html) [`www.nytimes.com/interactive/2017/08/24/us/affirmative-action.html`](https://www.nytimes.com/interactive/2017/08/24/us/affirmative-action.html)。

- [9] Barocas, Solon and Selbst, Andrew D. 2016. “大数据的不同影响。” *California Law Review*，104:671–732。

- [10] Plaugic, Lizzie. 2017. “Faceapp 的创建者为该应用的‘肤色变浅’滤镜道歉。” *The Verge*，2017 年 4 月 25 日。[`www.theverge.com/2017/4/25/15419522/faceapp-hot-filter-racist-apology`](https://www.theverge.com/2017/4/25/15419522/faceapp-hot-filter-racist-apology) [`www.theverge.com/2017/4/25/15419522/faceapp-hot-filter-racist-apology`](https://www.theverge.com/2017/4/25/15419522/faceapp-hot-filter-racist-apology)。

- [11] Manthorpe, Rowland. 2017. “美容.ai 机器人美容比赛重返。” *Wired UK*。[`www.wired.co.uk/article/robot-beauty-contest-beauty-ai`](https://www.wired.co.uk/article/robot-beauty-contest-beauty-ai) [`www.wired.co.uk/article/robot-beauty-contest-beauty-ai`](https://www.wired.co.uk/article/robot-beauty-contest-beauty-ai)。

- [12] Lo, Puck, and Corey, Ethan. 2019. “‘未出现’谬误。” *The Appeal*，2019 年 1 月 9 日。[`theappeal.org/the-failure-to-appear-fallacy/`](https://theappeal.org/the-failure-to-appear-fallacy/) [`theappeal.org/the-failure-to-appear-fallacy/`](https://theappeal.org/the-failure-to-appear-fallacy/)。

- [13] Deng, J., Dong, W., Socher, R., Li, L.-J., Li, K., and Fei-Fei, L. 2009. “ImageNet：一个大规模层次化图像数据库。” 在 *Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition*。

- [14] Miller, George A. 1995. “Wordnet：英语的词汇数据库。” *Communications of the ACM*，38(11):39–41。

- [15] Birhane, Abeba, and Prabhu, Vinay Uday. 2021. “大型图像数据集：计算机视觉的 pyrrhic win？” 在 *2021 IEEE Winter Conference on Applications of Computer Vision*，1536–1546。

- [16] Roth, Lorna. 2009. “观看舒莉，终极规范：色彩平衡、图像技术和认知公平。” *Canadian Journal of Communication*，34(1):111–136。

- [17] Torralba, Antonio, and Efros, Alexei A. 2011. “无偏观察数据集偏差。” 在 *Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition*，1521–1528。

- [18] Liu, Zicheng, Zhang, Cha, and Zhang, Zhengyou. 2007. “基于学习的视频会议图像质量改进。” 在 *2007 IEEE International Conference on Multimedia and Expo*，1035–1038。

- [19] Kaufman, Liad, Lischinski, Dani, and Werman, Michael. 2012. “内容感知自动照片增强。” 在 *Computer Graphics Forum*，31(8):2528–2540。

- [20] Kalantari, Nima Khademi, and Ramamoorthi, Ravi. 2017. “深度高动态范围成像动态场景。” *ACM Transactions on Graphics*，36(4):1–12。

- [21] Bonham, Vence L., Callier, Shawneequa L., and Royal, Charmaine D. 2016. “精准医学会让我们走出种族吗？” *New England Journal of Medicine*，374(21):2003–2005。

- [22] Wilson, James F., Weale, Michael E., Smith, Alice C., Gratrix, Fiona, Fletcher, Benjamin, Thomas, Mark G., Bradman, Neil, and Goldstein, David B. 2001. “变量药物反应的群体遗传结构。” *Nature Genetics*，29(3):265–269。

- [23] Caliskan, Aylin, Bryson, Joanna J., and Narayanan, Arvind. 2017. “从语言语料自动提取的语义含有类似人类的偏见。” *Science*，356(6334):183–186。

- [24] Danesi, Marcel. 2014. *媒体与通信词典*。Routledge。

- [25] Hardt, Moritz. 2014. “大数据的不公平。” *Medium*，2014 年 9 月 26 日。[`medium.com/@mrtz/how-big-data-is-unfair-9aa544d739de`](https://medium.com/@mrtz/how-big-data-is-unfair-9aa544d739de) [`medium.com/@mrtz/how-big-data-is-unfair-9aa544d739de`](https://medium.com/@mrtz/how-big-data-is-unfair-9aa544d739de)。

- [26] Caruana, Rich, Lou, Yin, Gehrke, Johannes, Koch, Paul, Sturm, Marc, and Elhadad, Noemie. 2015. “医疗领域可解释模型：预测肺炎风险和住院后 30 天重新入院。” 在 *Proceedings of the 21st ACM SIGKDD International Conference on Knowledge Discovery and Data Mining*，1721–1730。

- [27] Joachims, Thorsten, Swaminathan, Adith, and Schnabel, Tobias. 2017. “与有偏反馈的学习排名无偏学习。” 在 *Proceedings of the 10 International Conference on Web Search and Data Mining*，781–789。ACM。

- [28] Sweeney, Latanya. 2013. “在线广告投放中的歧视。” *Queue*，11(3):10:10–10:29。

- [29] Dobie, Will, Goldin, Jacob, and Yang, Crystal. 2016. “预审羁押的影响：基于随机分配法官的定罪、未来犯罪和就业的证据。” Working Paper 22511, National Bureau of Economic Research, Washington, DC。

- [30] Lum, Kristian, and Isaac, William. 2016. “预测并服务？” *Significance*，13(5):14–19。

- [31] Ensign, Danielle, Friedler, Sorelle A., Neville, Scott, Scheidegger, Carlos, and Venkatasubramanian, Suresh. 2018. “预测警务中的失控反馈循环。” *Proceedings of Machine Learning Research*，81:1–12。

- [32] Zhang, Junzhe, and Bareinboim, Elias. 2018. “决策中的公平：因果解释公式。” 在 *Proceedings of the 32nd AAAI Conference on Artificial Intelligence*，32(1)。

- [33] Rock, David and Grant, Heidi. 2016. “多元团队更聪明。” *Harvard Business Review*，2016 年 11 月 4 日。[`hbr.org/2016/11/why-diverse-teams-are-smarter`](https://hbr.org/2016/11/why-diverse-teams-are-smarter) [`hbr.org/2016/11/why-diverse-teams-are-smarter`](https://hbr.org/2016/11/why-diverse-teams-are-smarter)。
