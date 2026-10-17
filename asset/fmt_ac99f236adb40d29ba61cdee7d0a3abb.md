
本章讨论了定量文本分析如何用于项目评估。这种技术，特别是 `Wordfish` 方法，呈现出一个多面的优势与劣势图景，评估者必须谨慎驾驭。该方法的优势在于其能够从大量文本数据中提取客观见解，并提供系统且可复制的分析过程。`Wordfish` 及类似技术提供了一种发掘潜在模式、意识形态立场以及文本内容中特定词汇使用的途径，从而丰富了项目评估的深度。具体而言，它是从各类文件（如立场文件和政治演讲）中识别利益相关者偏好的有效工具，其资源消耗少于访谈，同时考虑了更广泛的数据集。此外，不同群体之间可以相互比较，从而显示出对项目的不同偏好。

然而，这些优势必须与该方法的局限性权衡，例如对复杂人类语言的潜在过度简化（参见 Grimmer et al., 2022: 37）、对预处理决策的敏感性（Proksch et al., 2019; Yano et al., 2021）以及遗漏语境的风险（Eichstaedt et al., 2021; Kučera & Mehl, 2022）。重要的是，缩放技术倾向于将术语高共现的文本聚合到单一政策维度中（Grimmer & Stewart, 2013）。因此，为使该技术有效，不仅要求持不同立场的行为体使用不同的词汇，而且要求在随时间测量偏好时识别并关注相似议题（Slapin & Proksch, 2008; Ferrara, 2020）。因此，全面理解所用文本对于识别特定语言模式至关重要。最后，该方法高度依赖于描述偏好的文件的存在。

为了有效掌握定量文本分析的力量，评估者需要掌握多种技能。掌握基本统计方法和编程语言知识对于有效使用 `Wordfish` 至关重要。然而，现在 R 和 Python 中都有优秀的开放获取文本分析工具，可以特别有助于支持用户进行分析。具体而言，在 R 中，`readtext` 和 `Quanteda` 包（Benoit et al., 2021）特别有用。`readtext` 包有助于将文本数据导入并读入 R 环境。同时，`Quanteda` 包在生成构建文档-术语矩阵（DTM）所需的语料库方面发挥着关键作用。该 DTM 是分析过程中成功应用无监督和有监督技术的基本组成部分。扎实的语言细微差别理解和领域专业知识对于准确解释结果和避免误读也至关重要。因此，批判性思维对于微调参数和确保最终分析质量必不可少。

定量文本分析在项目评估中的应用广泛且充满希望。虽然学者们以前强调文本分析的重要性，特别是语境分析对评估的作用（Christie & Fleischer, 2010; McKibben et al., 2020; Stemler, 2000），但定量文本分析提供了一种新工具，开启了文档分析的无限可能。这种方法可以帮助评估者解读公众认知、政治动态和利益相关者偏好，以支持基于证据的决策。通过将定量文本分析整合到评估框架中，从业者可以利用来自海量数字文本数据景观的见解来丰富传统方法（Thomas, 2006）。这种整合可能导致更全面和细致的项目评估，提高各部门的问责制和透明度，并平衡调查方法中的偏差，如误报和社会期望效应（Bundi et al., 2018; Johanson et al., 1993; Lam & Bengo, 2003; Stanton, 2004）。

展望未来，定量文本分析领域的评估研究前景依然充满活力。该领域有望持续进步，潜在的探索领域包括：改进方法以减轻固有偏见、开发结合定量与定性方法的混合模型（Andreotta 等，2019；Eichstaedt 等，2021；Parks & Peters, 2023），以及将现有技术适配到不断演变的传播形式中，如社交媒体平台（Driss 等，2019）。此外，定量文本分析的伦理影响值得深入审视，特别是在隐私担忧、算法公平性和潜在社会影响方面（Dolata 等，2022）。

## 结论

总之，以 `Wordfish` 为例的定量文本分析，代表了一套供评估者深入探究文本数据复杂性的宝贵工具箱。尽管挑战依然存在，但掌握必要技能，并结合审慎的实施方法，能够最大化该方法在项目评估中的效益。随着领域的不断演进，定量文本分析与既定评估实践的融合，有望推进我们对复杂人类传播的理解，并将基于证据的决策推向前所未有的高度。

## 注释

1. 关于罕见的例外，请参见 Cintron & Montrosse-Moorhead（2022）。

2. 文本分析常被称为内容分析。我们将使用文本分析这一术语，以建立其与定量文本分析的联系（Krippendorff, 2018）。

3. 正如 Gross & Jankowski（2020:17）所解释的，`Wordscores` 通过将“参考文本”的相对词频与“待测文本”的词分布进行比较，来估算文件的政策特定立场。

4. 当我们使用“案例研究”一词时，意指“对某一特定案例或多个案例进行详细分析，旨在揭示更大范围案例总体的情况”（Gerring & Cojocaru, 2016: 394）。

5. 在这篇研究论文中，Gatto & Bundi (2023) 对商业利益集团及其关联代表随时间变化的立场进行了比较分析，主要目的是考察与三项不同经济政策相关的潜在趋势变化。在本案中，我们利用庞大的数据集，将范围缩小至仅在金融监管这一政策背景下分析所有利益集团和代表。这种方法将使我们能够观察和评估利益相关者偏好的演变趋势。

6. 工作议会的特点是拥有强大的委员会制度，主要负责起草和决定法案。相比之下，在所谓的“言论议会”中，大多数法案是在全体会议上处理的（Dann, 2003）。

7. 高频常用词（例如：and, or, the 等）。

8. 最终特征数量为 3,722 个（稀疏度 92.32%），针对财政政策；为 3,424 个特征（稀疏度 92.86%），针对金融监管。

9. 选取两份文件，其中第一份文件被约束为具有比第二份更负的值。例如，`dir = c(1,5)` 将约束 `ω1` 小于 `ω5`（Proksch & Slapin, 2009: 340）。

## 参考文献

1. Altheide, D. L. (1987). Reflections: Ethnographic content analysis. Qualitative Sociology, *10*(1), 65–77. [`doi.org/10.1007/BF00988269`](https://doi.org/10.1007/BF00988269)

2. Andreotta, M., Nugroho, R., Hurlstone, M. J., Boschetti, F., Farrell, S., Walker, I., & Paris, C. (2019). Analyzing social media data: A mixed-methods framework combining computational and qualitative text analysis. Behavior Research Methods, *51*, 1766–1781.

3. Barrados, M. (2017). Getting Started with Big Data: The Promises and Challenges of Evaluating Health-Care Quality. In G. J. Petersson and J. D. Breul (eds.). Cyber Society, Big Data, and Evaluation. Routledge.

4. Bellanger, F. (2006). Parlement et administration en Suisse. Annuaire européen d’administration publique*,* *29*, 337–369.

5. Benoit, K. (2020). Text as Data: An Overview. In L. Curini and R. Franzese (eds.). The SAGE Handbook of Research Methods in Political Science and International Relations (pp. 461–497). SAGE Publications Ltd. [`doi.org/10.4135/9781526486387`](https://doi.org/10.4135/9781526486387)

6. Benoit, K., & Herzog, A. (2017). Text Analysis: Estimating Policy Preferences from Written and Spoken Words. In J. Bachner, K. H. Wagner and B. Ginsberg (eds). Analytics, Policy and Governance (pp. 137–-159). Yale University Press.

7. Benoit, K., Watanabe, K., Wang, H., Lua, J. W., Kuha, J., & Benoit, M. K. (2021). Package ‘quanteda. textstats.’ Research Bulletin, *27*(2), 37–54.

8. Berry, M. W., Mohamed, A., & Yap, B. W. (Eds.). (2020). Supervised and Unsupervised Learning for Data Science. Springer International Publishing. [`doi.org/10.1007/978-3-030-22475-2`](https://doi.org/10.1007/978-3-030-22475-2)

9. Bruce, K., Vandelanotte, J., & Gandhi, V. (2025). Emerging Technology and Evaluation in International Development. In S. B. Nielsen, F. Mazzeo Rinaldi and G. J. Petersson (eds.). *Artificial Intelligence and Evaluation.* *Emerging Technologies and Their Implications for Evaluation* (pp. 13–36). Routledge. [`doi.org/10.4324/9781003512493`](https://doi.org/10.4324/9781003512493)

10. Bundi, P., & Pattyn, V. (2022). Citizens and evaluation: A review of evaluation models. American Journal of Evaluation, 10982140211047219. [`journals.sagepub.com/doi/full/10.1177/10982140211047219`](https://journals.sagepub.com/doi/full/10.1177/10982140211047219)

11. Bundi, P., Varone, F., Gava, R., & Widmer, T. (2018). Self-selection and misreporting in legislative surveys. Political Science Research and Methods, *6*(4), 771–789.

12. Bunea, A., & Ibenskas, R. (2015). Quantitative text analysis and the study of EU lobbying and interest groups. European Union Politics, *16*(3), 429–455.

13. Campbell, R. S., & Pennebaker, J. W. (2003). The secret life of pronouns: Flexibility in writing style and physical health. Psychological Science, *14*(1), 60–65. [`doi.org/10.1111/1467-9280.01419`](https://doi.org/10.1111/1467-9280.01419)

14. Celebi, M. E., & Aydin, K. (Eds.). (2016). Unsupervised Learning Algorithms. Springer International Publishing. [`doi.org/10.1007/978-3-319-24211-8`](https://doi.org/10.1007/978-3-319-24211-8)

15. Chen, H. T. (2014). Practical Program Evaluation: Theory-Driven Evaluation and the Integrated Evaluation Perspective. SAGE Publications.

16. Christiansen, P. M., Mach, A., & Varone, F. (2018). 团体主义制度如何塑造公民团体接触政策制定者的渠道：来自丹麦和瑞士的证据。*Journal of European Public Policy*, 25(4), 526–545. [`doi.org/10.1080/13501763.2016.1268194`](https://doi.org/10.1080/13501763.2016.1268194)

17. Christie, C. A., & Fleischer, D. N. (2010). 对评估实践的洞察：对北美以评估为重点的期刊上发表的评估研究所用设计和方法的内容分析。*American Journal of Evaluation*, 31(3), 326–346.

18. Christie, C. A., & Rose, M. (2003). 评估理论的语言：从对评估理论与实践的实证研究中获得的见解。*Canadian Journal of Program Evaluation*, 18(2), 33–45. [`doi.org/10.3138/cjpe.18.002`](https://doi.org/10.3138/cjpe.18.002)

19. Cintron, D. W., & Montrosse-Moorhead, B. (2022). 将大数据融入评估：用于主题识别和建模的 R 代码。*American Journal of Evaluation*, 43(3), 412–436. [`doi.org/10.1177/10982140211031640`](https://doi.org/10.1177/10982140211031640)

20. Commission fédérale des banques (CFB). (2007). *Rapport de gestion 2007*。Commission fédérale des banques.

21. Cousins, J. B., & Whitmore, E. (1998). 构建参与式评估。*New Directions for Evaluation*, 1998(80), 5–23. [`doi.org/10.1002/ev.1114`](https://doi.org/10.1002/ev.1114)

22. Dann, P. (2003). 欧洲议会与行政联邦制：在半议会制民主中探寻议会。*European Law Journal*, 9(5), 549–574.

23. Dolata, M., Feuerriegel, S., & Schwabe, G. (2022). 算法公平性的社会技术视角。*Information Systems Journal*, 32(4), 754–818.

24. Driss, O. B., Mellouli, S., & Trabelsi, Z. (2019). 从公民到政府政策制定者：社交媒体数据分析。*Government Information Quarterly*, 36(3), 560–570. [`doi.org/10.1016/j.giq.2019.05.002`](https://doi.org/10.1016/j.giq.2019.05.002)

25. Eichstaedt, J. C., Kern, M. L., Yaden, D. B., Schwartz, H. A., Giorgi, S., Park, G., Hagan, C. A., Tobolsky, V. A., Smith, L. K., & Buffone, A. (2021). 文本分析的闭合词汇表与开放词汇表方法：综述、定量比较与建议。*Psychological Methods*, 26(4), 398.

26. Ferrara, F. M. (2020). 欧债危机中的思想之战：来自欧洲央行会期间讲话的证据。*Journal of European Public Policy*, 27(10), 1463–1486. [`doi.org/10.1080/13501763.2019.1670231`](https://doi.org/10.1080/13501763.2019.1670231)

27. Fetterman, D. M. (2001). *Foundations of Empowerment Evaluation*。SAGE.

28. Figgou, L., & Pavlopoulos, V. (2015). 社会心理学：研究方法。*International Encyclopedia of the Social & Behavioral Sciences*, 22, 544–552.
