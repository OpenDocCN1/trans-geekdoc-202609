

过去的研究表明，当极端事件发生时，尤其是在危机时期，使用这些方法无法准确估计金融收益的相依结构。克服这一问题的一种解决方案是使用copula（连接函数）来考察金融资产收益之间的相依关系。一般而言，copula以用于描述变量之间相依结构的概率理论为前提。Copula基于Sklar定理推导而来。它们是由若干一元（边际概率）分布组合而成的多元概率（联合）分布，其中每个（连续）变量的边际分布均为均匀分布。

copula方法要求将标准化金融收益转换为标准化的Student t分布，以通过概率积分变换将分布的定义域变为[0,1]，使其近似于均匀分布。随后，可以将非线性copula模型应用于非线性和非正态分布的金融数据，以考察其尾部相依结构。通常，椭圆族copula（如高斯copula和Student t copula）用于捕捉双向尾部相依结构，而阿基米德copula（如Gumbel copula（上尾）和Clayton copula（下尾））用于捕捉单向尾部相依结构。

两步完整极大似然估计法（full MLE）易于实际应用。首先估计所有边际密度的参数，然后在后续步骤中使用估计出的参数来估计copula。估计出的copula参数用于确定下尾和上尾相依系数。一般而言，椭圆族copula具有对称的尾部相依性。高斯copula的尾部相依性为零或极弱，而Student t copula具有相对较强的尾部相依性。后者通常更适用于金融领域，因为金融收益通常具有更厚的尾部。相反，阿基米德copula允许非对称的尾部相依性。Clayton copula的上尾相依性为零，但下尾相依系数为正；而Gumbel copula的下尾相依性为零，但上尾相依系数为正。由于阿基米德copula不假设对称的尾部分布，它们适合考察金融资产之间的相依结构，在这些资产中，由于对市场利好和利空消息的非对称反应，收益分布通常是非对称的。

## 参考文献

- R. Aloui 和 M. Aïssa (2016). 石油价格、股票价格与汇率之间的关系：基于vine copula的GARCH方法. 《北美经济与金融杂志》, 37, 458-471. https://doi.org/10.1016/j.najef.2016.05.002.
- R. Aloui、M. Aïssa 和 D. Nguyen (2013). 石油价格与汇率之间的条件相依结构：一种copula-GARCH方法. *《国际货币与金融杂志》*, 32, 719–738. https://doi.org/10.1016/j.jimonfin.2012.06.006.
- H. Bal 和 V. Najjari (2013). 基于双曲生成元的阿基米德copula族. *《加齐大学科学杂志》*, 26(2), 195–200.
- H. Boubaker 和 N. Sghaier (2013). 在具有长期记忆的相依金融收益情形下的投资组合优化：一种基于copula的方法. *《银行与金融杂志》*, 37, 361–377. https://doi.org/10.1016/j.jbankfin.2012.09.006.
- E. Bouyé、V. Durrleman、A. Nikeghbali、G. Riboulet 和 T. Roncalli (2000). 金融中的copula：阅读指南及一些应用. 伦敦城市大学商学院金融计量经济学研究中心. 取自 http://www.thierry-roncalli.com/download/copula-survey.pdf.
- E. Bouyé、V. Durrleman、A. Nikeghbali、G. Riboulet 和 T. Roncalli (2001). Copula：风险管理的开放领域. 伦敦城市大学商学院金融计量经济学研究中心. 取自 http://www.thierry-roncalli.com/download/copula-rm.pdf.
- C. Cech (2006). 基于copula的金融风险聚合自上而下方法. 维也纳BFI应用科学大学. 工作论文系列，第32期. 取自 http://www.fh-vie.ac.at/var/em_plain_site/storage/original/application/2e4b8544eddfc105785bb6e14bf2c7a.pdf.
- L. Chollete、V. de la Peña 和 C.-C. Lu (2011). 国际分散化：一种copula方法. *《银行与金融杂志》*, 35(2), 403–417. https://doi.org/10.1016/j.jbankfin.2010.08.020.
- C. Czado (2010). 多元copula的pair-copula构造. 载于*《Copula理论及其应用》*, P. Jaworski、F. Durante、W. Härdle 和 T. Rychlik 编, 《统计讲义》系列, 第198卷. Springer, 柏林, 海德堡.
- A.-L. Delatte 和 C. Lopez (2013). 大宗商品与股票市场：来自copula方法的一些典型化事实. *《银行与金融杂志》*, 37(12), 5346–5356. https://doi.org/10.1016/j.jbankfin.2013.06.012.
- S. Demarta 和 A. McNeil (2005). t copula及相关copula. *《国际统计评论》*, 73(1), 111–129. https://doi.org/10.1111/j.1751-5823.2005.tb00254.x.
- J. Du 和 K. Lai (2017). 人民币国际化进程中多变量人民币汇率的基于copula的风险管理模型. *《系统科学与复杂性杂志》*, 30(3), 660–679. https://doi.org/10.1007/s11424-017-5147-3.
- F. Durante 和 C. Sempi (2010). Copula理论：导论. 载于*《Copula理论及其应用》*, P. Jaworski、F. Durante、W. Härdle 和 T. Rychlik 编, 《统计讲义》系列, 第198卷. Springer, 柏林, 海德堡.
- Y. Fang 和 L. Madsen (2013). 修正的高斯伪copula：在保险与金融中的应用. *《保险：数学与经济学》*, 53(1), 292–301. https://doi.org/10.1016/j.insmatheco.2013.05.009.
- J. D. Fermanian 和 O. Scaillet (2004). 金融应用中copula建模的一些统计陷阱. 国际金融资产管理与工程中心（FAME）. 研究论文系列，第108期. 取自 http://www.crest.fr/ckfinder/userfiles/files/pageperso/fermania/pitfalls_copula.pdf.
- M. Gronwald、J. Ketterer 和 S. Trück (2011). 碳市场、大宗商品市场与金融市场之间的关系：copula分析. *《经济记录》*, 87(s1), 105–124. https://doi.org/10.1111/j.1475-4932.2011.00748.x.
- C. Genest、M. Gendron 和 M. Bourdeau-Brien (2009). copula在金融领域的问世. 《欧洲金融杂志》, 15(7-8), 609-618. https://doi.org/10.1080/13518470802604457.
- D. Guégan 和 J. Zhang (2010). 用于度量多元金融数据相依性的动态copula变化分析. 《数量金融》, 10(4), 421-430. https://doi.org/10.1080/14697680902933041.
- F. Habiboellah (2007). 金融风险管理中的相依性建模. 阿姆斯特丹自由大学商业数学与信息学系（BMI）. 取自 http://www.math.vu.nl/~sbhulai/papers/paper-habiboellah.pdf.
- Y. Han 和 X. Zhou (2017). 危机前后金砖国家股票与汇率之间的关系：一种混合C-VINE copula模型. 《罗马尼亚经济预测杂志》, 20(1), 38-59.
- C.-P. Hsu、C.-W. Huang 和 W.-J. Chiou (2012). copula-极值理论在估计风险价值（VaR）中的有效性：来自亚洲新兴市场的经验证据. 《数量金融与会计评论》, 39(4), 447-468. https://doi.org/10.1007/s11156-011-0261-0.
- H. Huang、R. MacDonald 和 Y. Zhao (2014). 全球货币错位、崩溃敏感性与矩风险溢价. 苏格兰格拉斯哥大学亚当·斯密商学院. 取自 https://www.aeaweb.org/aea/2015conference/program/retrieve.php?pdfid=440.
- R. Ibragimov 和 A. Prokhorov (2016). 重尾与copula：再论分散化的局限. 《经济学快报》, 149, 102-107. https://doi.org/10.1016/j.econlet.2016.10.024.
- R. Ibragimov 和 A. Prokhorov (2017). 重尾与copula：经济学与金融学中的相依建模专题. World Scientific，新加坡.
- E. Karimalis 和 N. Nomikos (2018). 欧洲银行业系统性风险度量：一种copula CoVaR方法. 《欧洲金融杂志》, 24(11), 944-975. https://doi.org/10.1080/1351847X.2017.1366350.
- C. Kharoubi-Rakotomalala 和 F. Maurer (2013). 金融中的copula：十年之后. 《应用商业研究杂志》, 29(5), 1555-1566.
- A. Kresta 和 T. Tichý (2012). 国际股票投资组合风险建模：以NIG模型和普通copula函数为例. 《捷克经济与金融杂志》, 62, 141-161.
- K. Kvasnakova (2009). 股票与债券市场相依结构建模. 布拉迪斯拉发夸美纽斯大学数学、物理与信息学系. 取自 http://www.iam.fmph.uniba.sk/studium/efm/diplomovky/2009/kvasnakova/diplomovka.pdf.
- W.-C. Lai 和 K.-L. Goh (2019). 人民币贬值对相依结构的影响：阿基米德copula方法. 《太平洋盆地金融市场与政策评论》, 22(1), 1950005. https://doi.org/10.1142/S021909151950005X.
- D. Li (2000). 关于违约相关性：一种copula函数方法. 《固定收益杂志》, 9(4), 43-54.
- B.-Y. Liu、Q. Ji 和 Y. Fan (2017). 一种识别跨市场相依性的新的时变最优copula模型. 《数量金融》, 17(3), 437-453. https://doi.org/10.1080/14697688.2016.1205208.
- W. Liu (2006). 货币投资组合收益：一种copula方法. 加拿大多伦多大学经济学系. 取自 http://homes.chass.utoronto.ca/~weiliu/copuladist6new1.pdf.

