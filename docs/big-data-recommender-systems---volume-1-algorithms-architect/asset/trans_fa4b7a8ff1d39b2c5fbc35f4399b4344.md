
# 推荐系统中的用户隐私 281

[58] Fung B, Wang K, Yu PS. 为了保护隐私而对分类数据进行匿名化. IEEE Transactions on Knowledge and Data Engineering. 2007;19(5):711–725.

[59] LeFevre K, DeWitt DJ, Ramakrishnan R. Incognito: 高效的全域 k-匿名性. 于: Proceedings of the 2005 ACM SIGMOD International Conference on Management of Data. ACM, 2005. p. 49–60.

[60] LeFevre K, DeWitt DJ, Ramakrishnan R. 多维 k-匿名性. 于: Data Engineering, 2006. IDE’06. Proceedings of the 22nd International Conference on. IEEE, 2006; p. 25–25.

[61] Machanavajila A, Kefer D, Gehre J, et al. l-多样性: 超越 k-匿名性的隐私保护. ACM Transactions on Knowledge Discovery from Data (TKDD). 2007;1(1):3.

[62] Samarati P, Sweeney L. 在披露信息时保护隐私: k-匿名性及其通过泛化和抑制实现的. 技术报告, SRI International, 1998.

[63] Sweeney L. k-匿名性: 一种保护隐私的模型. International Journal of Uncertainty, Fairness and Knowledge-Based Systems. 2002;10(05):557–570.

[64] Li N, Li T, Venkatubramanian S. 紧密性: 数据发布的新衡量标准. IEEE Transactions on Knowledge and Data Engineering. 2010;22(7):943–956.

[65] Xiao X, Tao Y.-M. 动态数据集的内部隐私发布. 于: Proceedings of the 2007.ACM SIGMOD International Conference on Management of Data. ACM; 2007. p. 689–700.

[66] Wang K, Fung BCM, Philip SY. 削弱攻击者的信度: k-匿名性的替代方案. Knowledge and Information Systems. 2007;11(3):345–368.

[67] Xiao X, Tao Y. Anatomy: 简单且有效的隐私保护. 于: Proceedings of the 32nd International Conference on Very Large Databases. VLDB Endowment; 2006. p. 139–150.

[68] Li N, Li T, Zhang J, et al. 切片法: 一种保护数据发布的新方法. IEEE Transactions on Knowledge and Data Engineering. 2012;24(3):561–574.

[69] Terrovitis M, Mammway N, Liagouris J, et al. 通过去关联实现隐私保护. Proceedings of the VLDB Endowment. 2012;5(10):944–995.

[70] Li N, Li T, Venkatasubramanian S. t-紧密性: 超越 k-匿名性和 l-多样性的隐私. 于: Data Engineering, 2007. IDE 2007. IEEE 23rd International Conference on. IEEE; 2007; p. 106–115.

[71] Dwork C. 一种保护和禁用隐私数据分析的管理员方法. 于: Privacy, Security, and Trust in KDD. Berlin, Heidelberg: Springer; 2008. p. 1–13.

[72] Samarati P. 在微型数据发布中保护居民身份. IEEE Transactions on Knowledge and Data Engineering. 2001;13(6):1010–1027.

[73] Wang K, Yu PS, Chakraborty S. 自底向上的泛化: 一种隐私保护的数据挖掘解决方案. 于: Data Mining, 2004. ICDM’04. Fourth International Conference on. IEEE; 2004. p. 249–256.

# 大数据推荐系统，卷 1

[74] Fung BCM, Wang K, Yu PS. 为了信息和隐私保护的自顶向下的特化. 于: 21st International Conference on Data Engineering (ICDE). IEEE; 2005. p. 205–216.

[75] Wang RCW, Li J, Fu ACW, et al. α-匿名性: 一种用于隐私发布的增强 k-匿名性模型. 于: Proceedings of the 12th ACM SIGKDD International Conference on Knowledge Discovery and Data Mining. ACM; 2006. p. 754–759.

[76] Sun X, Wang H, Li J, et al. 用于隐私发布的增强 k-匿名性模型. Transactions on Privacy. 2008;2(2):53–66.

[77] Sun X, Li M, Wang H. 一类用于隐私发布的增强 α-多样性模型. Future Generation Computer Systems. 2011;27(3):348–356.

[78] Dwork C, Rothblum GN. 差分隐私. arXiv preprint arXiv:1603.0188,2016.

[79] Badsha S, Yi X, Khalil I. 一种实用的隐私保护推荐系统. Data Science and Engineering. 2016;1(3):161–177.

[80] Nikolaenko J, Joannidis S, Weissberg U, et al. 隐私保护矩阵分解. 于: Proceedings of 2013 ACM SIGSAC Conference on Computer & Communications Security. ACM; 2013. p. 801–812.

[81] Shokri R, Pedarsani P, Theodoropoulos G, et al. 通过数据的分布式聚合保护协同过滤中的隐私. 于: Proceedings of the third ACM Conference on Recommender Systems. ACM; 2009. p. 157–164.

[82] Machanavajila A, Korolova A, Sarma AD. 个性化推荐: 准确还是隐私. Proceedings of VLDB Endowment. 2011;4(7):440–450.

[83] Hofmann T, Hartmann D. 通过分析实现隐私的协同过滤. 于: 2005 ACM Symposium on Applied Computing. 2005. p. 791–795.

[84] Li D, Chen C, Lv Q, R, et al. 一种用于基于物品的隐私保护协同过滤算法. Future Generation Computer Systems. 2016;5:311–320.

[85] Boutet A, Domingo-Ferero J, Guerraoui R, Patsakis C, et al. k-匿名协同过滤方法. Journal of Computer and System Sciences. 2015;81(6):1000–1011.

[86] Jorgensen Z, Yu T. 用于用于个性化推荐的隐私保护框架. 于: EDBT 2014. p. 571–582.

[87] Shang S, Hui Y, Hui P, et al. 超越个性化与匿名: 基于组的推荐系统. 于: 29th Annual ACM Symposium on Applied Computing. ACM; 2014. p. 266–273.

# 第13 章
# 使用 Apache Spark 进行大数据的隐私实体解析
Alexandros Karakasidis 和 Georgia Koloniari

## 13.1 引言

由于提供了丰富的历史购买和浏览历史等用户数据，推荐系统如今正经历着巨大的推动。当推荐系统能够使用并整合来自多个站点的数据以绘制更完整的用户偏好和兴趣画像时，其收益会增加。然而，此类数据通常源于分散的异源，在处理和分析它们之前，需要进行整合或链接。跨异源识别指向同一真实实体的数据的问题被称为*记录链接或实体解析*。由于这些数据也涉及人类活动，在跨不同源链接数据时会产生隐私问题。这个问题被称为*隐私保护记录链接*PPRL)。

在 PPRL 中，两个或多个数据者尝试在不向对方透露任何额外信息的情况下识别记录中的共同实体。由于数据来自异源，可能遵循不同的模式，因此记录链接方法依赖于描述这些记录和所有来源的属性，例如识别同一人的姓名和地址。因此，为了确定两条记录是否匹配，必须比较它们各自的所有字段。匹配方法的复杂度很高，因为两个数据者的记录需要相互比较以确定匹配的记录。为此，引入了分块方法 [1]，通过剔除可能匹配的记录对来降低匹配复杂度。此外，数据通常是“脏”的，包含拼写和打印错误，这进一步增加了链接过程的复杂性。无法进行精确匹配，因此需要更昂贵的近似匹配方法。

在记录链接的背景下，已应用不同的近似匹配方法。大多数方法依赖哈希、双字母组和 n 元组组合，以及相似性或合适的距离量。一种流行的方法是基于音码的使用。音码是根据字符串发音生成的哈希。音码已使用一个世纪 [2] 用于重复检测和记录链接，由于其固有的信息抑制特性使其对拼写错误具有容忍性。使用音码将脏数据的近似匹配问题简化音码的精确匹配问题，导致处理更快并使距离量的使用变得冗余。然而，这通常是以精确率或召回率质量为代价的。

在本章中，我们提出基于语音编码的 PPR 并行协议，利用新新的大数据处理引擎以高效的方式提供高质量的结果。我们之前在 [3] 中介绍的工作基于使用 Soundex 语音算法 [2]。该协议还具有噪声生成以防止频率攻击，以及对真实和伪数据进行加密以便不可信方进行处理。然而，为了应对大量脏数据可能导致的低召回率，我们建议将 Soundex 与另一种语音算法（特别是 ISIS 使用。通过结合两种编码，我们的协议变得更加健壮，对匹配字段中的错误更具容忍性，因为它引入了冗余。此外，由于 Soundex 对编码文本开头的内容特别敏感，我们的协议通过使用第二语音算法对原始文本的反向部署了另一种优化。

本章其余部分的组织如下：第13.2 节总结了工作。在第13.3 节中，我们制定了问题并简要介绍我们方法的基本组件。第13.4 节详述了所提技术，而第13.5 节包含了我们的实验评估。最后，第13.6 节以结论和对未来工作的思考进行总结。

## 13.2 相关工作

记录链接问题由于其应用的重要性和多样性引起了广泛关注。对最具代表性的传统方法的综述是

