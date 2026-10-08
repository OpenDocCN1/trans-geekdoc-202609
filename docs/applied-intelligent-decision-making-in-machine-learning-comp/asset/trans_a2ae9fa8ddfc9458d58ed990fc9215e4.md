

# 基于矩阵的模式匹配方法的医学实体提取

![](img/d1bf16e7dc1fe5d49ee33c2dfa5cdb06_181_0.png)

**图 8.3** 所提方法针对治疗、问题和测试概念在精确率和召回率方面的性能对比。

## 精确率

![](img/d1bf16e7dc1fe5d49ee33c2dfa5cdb06_181_1.png)

**图 8.4** 不同文本分类方法的精确率比较。

在对结果进行误差分析后，观察到召回率在一定程度上可以提高。由于对实体序列边界识别不准确，导致部分概念缺失。对于频繁模式的生成，最小阈值为2，并考虑了频率为 2 或大于 2 的模式。但在本系统中，仅关注了 POS（词性标记）特征。在未来的工作中，可以使用更多特征（如词、n-gram、词语义、词根、前缀和后缀）来开发相同的系统。

多词临床概念的边界识别是一个大问题 [29]，主要出现在问题概念和治疗概念中，因为金标准数据集在问题概念中包含了长实体序列，例如“最小右内颈动脉疾病”或“右肾动脉血栓”。在治疗概念中也存在长实体序列，例如“左颈动脉内膜切除术”、“羟氧酮-乙酰氨芬”、“大静脉移植物 → 近端降主动动脉”。该系统执行的是严格匹配；未来可以执行部分匹配，这可能会提高系统的召回率。使用 UMLS 数据库对非医学概念进行了剪枝，但该数据库中的长实体序列未能与医学词汇正确匹配。这个问题可以通过对临床概念进行松散匹配来解决。

文本预处理包括用于识别特殊字符的正则表达式，这些字符被视为分词符，尽管在金标准数据中仅识别了中间包含这些字符的某些单词。使用预期方法，诸如“severe 3 vessel disease”、“sapaneous vein graft → obtuse marginal”、“the patient’s pacing paces”、“heel/shin”以及“leg, erg & apos”等复合词被准确预测为概念。

## 召回率

| 方法 |
| :--- |
| 字典查找法 |
| 基于规则的方法 |
| MetaMap 2010 |
| MetaMap 2013v2 |
| 所提的基于矩阵的方法 |

图 8.5 不同文本分类方法的召回率比较。

## 8.6 结论与未来工作

在所提出的解决方案中，作为疾病体征和症状、检查和治疗的医学概念是通过两个矩阵的并行匹配以及后续基于规则的方法来识别的。通过带有 UMLS 语义的概念映射对非医学概念进行剪枝，提升了系统的性能。注意到，该系统的效率优于 MetaMap 2010、MetaMap 2013v2 和字典查找法。可以在相同的方法中添加新特征（如包含前缀和后缀、词干、词、词语义或 n-gram）来进一步提高召回率。该系统没有使用机器学习概念，因此性能不依赖于数据集的大小。所提系统可以以相同的方式在小型和大型数据集上，但大型数据集的处理时间会增加。未来，为了快速处理大型文本，可以在分布式环境中实现所提方法。

## 致谢

我们感谢 2010 i2b 挑战赛组织者设计、训练和评估语料库。我们还感谢美国国家医学图书馆允许我们通过 UMLS 访问临床工作。

## 参考文献

- 1. Jiang, M., Chen, Y., Liu, M., Rosenbloom, S.T., Mani, S., Denny, J.C., Xu, H.: 基于机器学习的从出院摘要中提取临床实体及其断言的方法。Journal of the American Medical Informatics Association: JAMIA 18, 601–606 (2011).
- 2. Kim, Y., Riloff, E.: 一用于从临床笔记提取医学文本的堆叠集成。AMIA Summits on Translational Science 2015, 69–73.
- 3. Toori, M., Wagholikar, A.-L., Liu, H.: 使用机器学习对多源临床文档进行概念提取。Journal of the American Medical Informatics Association 18, 580–587.
- 4. Minard, A., Ligard, A.-L., Bencha, A., Bernard, D., Cartoni, B., Deleger, L., Grau, B., Rosset, S., Zweigenberger, P., Groin, C.: 改进临床文档访问的混合方法：概念、断言和关系。Journal of the American Medical Informatics Association 18, 588 (2011).
- 5. Dehghan, A.: 命名实体识别中的实体识别。arXiv preprint 1308, 1304 (2013).
- 6. Kang, N., Afzal, Z., Singh, B., Van Mellen, E., Korshi, J.: 使用集成系统改进从临床记录中提取概念。Journal of Biomedical Informatics 45, 223–428 (2012).
- 7. Abacha, A., Zweigenberger, P.: 医学实体识别：语义与统计方法的比较。In BioNLP 2011 Workshop, pp. 56–64. Association for Computational Linguistics, Portland, OR (2011).
- 8. Uzair, O., South, B.R., Sen, S., Duval, S.: 2010 i2b 挑战临床文档中的断言和关系。Journal of the American Medical Informatics Association 18, 552–555.
- 9. Suominen, H., Salateri, A., Velupilli, C., Chapman, W., Elhad, N., Smith, B.R., Mowery, D., Jones, J., Level, Zucker, G.: SHARE/CLEF health 验证、多模态和多模态。In 24th International Conference of LIFAC, 2013, pp. 212–231. Springer Berlin, Spain.
- 10. Kim, J.-D., Tang, T., Tsuchiya, Y., Yates, C., Klein N.: NLPbank 实体识别。Proceedings of the International Joint Workshop on Natural Language Processing in Biomedicine and Applications (NLP/BioNLP).
- 11. Hirschman, L., Yeh, A., Bleasch, C., Valencia.: BioIE：生物学信息提取评估。BMC Bioinformatics 6, S1 (2005).
- 12. Yeh, A., Morgan, A., Colosimo, M., Hirschman, L.: BioIE 任务1：基因识别。BMC Bioinformatics 6, S2 (2005).
- 13. Kim, Y., Riloff, E., Jordan, J.: 不同类型临床笔记的概念提取研究。AMIA Annual Symposium 2015, 737–746 (2015).
- 14. Sahu, R.: 从非结构化文本中自动提取医学概念的基于规则的方法。In: Sa, P.K., Bakshi, S., Hatzilydis, I.K., and Sahoo, M.N. (eds), Recent Findings in Intelligent Computing Techniques, pp. 261–267. Springer, Berlin (2018).
- 15. Patel, R., Tanwani, S.: 机器学习技术在临床信息提取中的应用。In: Mishra, M., Mishra, B., Patel, Y., and Misra R. (eds.), Smart Techniques for a Smarter Panel, pp. 145–165. Springer, Cham, Switzerland (2019).
- 16. Zhang, S., Elhad, N.: 无监督实体识别：临床与生物工具的实验。Journal of Biomedical Informatics 46, 1088–1098 (2013).
- 17. Aronson, A.R., Lang, F.-M.: MetaMap概述：历史视角与近期进展。Journal of the American Medical Informatics Association: JAMIA 17, 229–236 (2010).
- 18. Bodenieder, A.: 统一医学语言 (UMLS)：整合生物医学术语。Nucleic Acids Research 32, D267–D270 (2004).
- 19. Deghan, A.: 临床实体识别中的元素调整。CoRR (2013).
- 20. Xu, H., Abdelrahman, S., Jiang, M., Fan, J.W.: 使用 Stanford Parser 的全临床文本初步研究。In: 2011 IEEE International Conference on Bioinformatics and Biomedical Workshops (BIOMED), pp. 607–614. Atlanta, GA (2011).
- 21. Griffiths, D., Shivade, C., Foster-Lusher, E., Lai, A.M.: 临床领域句子检测的定量和定性评估。AMIA Summits on Translation Proceedings 2016, 88–97 (2016).
- 22. Das, H., Naik, B., Behera, H., Jaiswal, S., Mahato, P.: 使用神经模糊模型的医学数据分析。Journal of King Saud University-Computer and Information (2020).
- 23. Das, H., Lena, A.K., Nayak, J., Naik, B., Behera, H.: 一种基于 PSO 的分类提取模型。Informatics in Medicine Unlocked 18, 100288 (2020).
- 24. Das, H., Naik, B., Behera, H.: 用于分类的混合神经模糊学习-MLP (PSO-BP-MLP)。In: Computational Intelligence in Data Mining, Volume 2, pp. 461–471. Springer, Berlin (2015).
- 25. Das, H.: 用于分类的混合神经模糊和特征还原模型。Advances in Fuzzy Systems 2020, 15 (2020).
- 26. Zhang, H., Xu, D., Zhang, L., Sun, Y.: 基于矩阵的并行模式匹配方法。In: 2015 IEEE International Conference on Communications (ICC), pp. 7114–7119. London, UK (2015).
- 27. Gong, L.J., Yuan, Y., Wei, B., Sun, X.: 生物医学实体识别的混合方法。In: 2009 2nd International Conference on Biomedical Engineering and Informatics, pp. 1–5. Tianjin, China (2009).
- 28. Rout, J.K., Sinha, S., Jena, S.K., Bakshi, S., Jena, S.K.: 使用标记和无标记数据的缺陷评论检测。Multimedia Tools and Applications 76, 3187–3211 (2017).
- 29. Rout, J.K., Choo, K.-R., Dash, A.K., Bakshi, S., Jena, S.K., Williams, K.L.: 一种用于非结构化社交媒体文本情感和情绪分析的模型。Electronic Commerce Research 18, 181–199 (2018).

