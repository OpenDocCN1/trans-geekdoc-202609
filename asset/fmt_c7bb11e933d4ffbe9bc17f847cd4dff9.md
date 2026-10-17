
Figure 25.3 包含一张图表，x 轴表示从数据源收集数据的天数，y 轴表示对应的数据集大小，即收集到的数据的容量。该图提供了各数据源（Reddit、Twitter、NYTimes）产生的数据类型差异的洞察，并展示了各数据集的内存使用情况。

![Figure 25.3 Memory-usage of each data source](img/fig25_3_C.jpg)

Figure 25.3 Memory-usage of each data source

-   图 25.4 (a–c) 分别由推特（Twitter）、Reddit 评论（Reddit API）和纽约时报（NYTimes）摘要中的图表表示，横轴表示每条记录的单词数，纵轴表示出现次数。在 Twitter 数据中，词频最高出现在 20–40 的范围内。Reddit 数据中词频最高出现在 5–15 的范围内。此外，收集的带摘要的 NYTimes 数据也包含 10–30 的范围。词频分析是关键词分析的第一步，它为从整个数据集中提取关键词提供了洞察。

Figure 25.5(a) 由从 Twitter 数据中收集的数据生成的词云组成。常用词代表与衰退相关的词汇，如“政府”“通胀”“油气”“衰退”和“定价”是用户在推特中最常用的词汇。Figure 25.5(b) 是基于从 NYTimes 文章中收集的数据生成的词云。如“协议”“反对”“结盟”“原油”和“指示”等关键词在与衰退相关的文章中使用最频繁。Figure 25.5(c) 是基于从 Reddit 帖子（r/Recession）中收集的数据生成的词云。如“股市”“最差下跌”“衰退”“金融危机”和“消费者”等词汇在 r/Recession 上的帖子中使用最频繁。在 Figures 25.5(a) 和 (b) 中，关键词相当常见，因为结果基于公众意见数据集（Twitter 和 Reddit），而在 Figure 25.5(c) 中，关键词更为简化，且不集中于衰退条件。

![Figure 25.5(a) Word-cloud for the Twitter data](img/fig25_5a_C.jpg)

Figure 25.5(a) Word-cloud for the Twitter data

![Figure 25.5(b) Word-cloud for the Reddit data](img/fig25_5b_C.jpg)

Figure 25.5(b) Word-cloud for the Reddit data

![Figure 25.5(c) Word-cloud for the New York Times data (Khattar et al., 2020)](img/fig25_5c_C.jpg)

Figure 25.5(c) Word-cloud for the New York Times data (Khattar et al., 2020)

![Figure 25.4(a) Number of words for each tweet](img/fig25_4a_C.jpg)

Figure 25.4(a) Number of words for each tweet

![Figure 25.4(b) Number of words for each Reddit comment](img/fig25_4b_C.jpg)

Figure 25.4(b) Number of words for each Reddit comment

![Figure 25.4 (c) Number of words for every NYTimes headline](img/fig25_4_C.jpg)

Figure 25.4 (c) Number of words for every NYTimes headline

![Figure 25.6(c) Sentiment score of the Reddit posts](img/fig25_6c_C.jpg)

Figure 25.6(c) Sentiment score of the Reddit posts

Figure 25.6(a) 由一张图表组成，横轴表示与衰退相关的推特情感分析评分范围。评分范围 0.0–0.25 出现次数最高。Figure 25.6(b) 由一张图表组成，横轴表示与衰退相关的 Reddit 帖子情感分析评分范围。评分范围 -0.2–0.0 出现次数最高。Figure 25.6(c) 由一张图表组成，横轴表示与衰退相关的 NYTimes 文章情感分析评分范围。评分范围 -0.2–0.0 出现次数最高。在 Figure 25.5(a) 中，Twitter 数据的极性分布均匀，出现极正和极负模式。Reddit 数据呈现中等负相关和强正相关。此外，我们观察到 NYTimes 数据表现出低正性、低负性、高正性和高负性属性。

![Figure 25.6(a) Sentiment score of the tweets](img/fig25_6a_C.jpg)

Figure 25.6(a) Sentiment score of the tweets

![Figure 25.6(b) Sentiment score of the Reddit posts](img/fig25_6b_C.jpg)

Figure 25.6(b) Sentiment score of the Reddit posts

## 结论

在结果与讨论部分，我们确定了在数据收集、预处理、过滤和可视化步骤中获得的主要洞察。基于这些结果，我们为在引言部分提到的研究问题（RQ）得出了一些结论。针对研究问题 1（RQ1），我们基于词云和字符频率分析进行了关键词分析。我们发现，公众意见数据集（Twitter 和 Reddit）的关键词变化比 NYTimes 文章数据更频繁。新闻文章数据中具有更强的政治和地理意义，而 Twitter 和 Reddit 数据则较少。此外，摘要新闻文章的字符频率高于公众意见数据集。

针对 RQ2，作者基于为每条推特、子 reddit 评论和新闻摘要计算的情感分析评分进行了分析。我们使用了情感分析相关量表。情感评分范围从 -1 到 +1，其中 -1、0 和 +1 分别表示负面、中性和正面。NYTimes 文章数据表现出比公众意见数据集更极端的负面和正面。在 Twitter 数据中，情感评分呈正态分布，这表明用户在衰退主题上提供多种观点。在 Reddit 数据中，我们观察到用户倾向于极度负面评分，而正面评论在衰退主题上均匀分布。研究问题 3（RQ3）特别关注社交网络（Twitter 和 Reddit）对主题或实体的影响。过滤后的数据显示，在衰退主题上用户响应率和用户参与度有所提升。

## 未来展望

首先，通过扩大数据收集范围，包括各类社交媒体平台、新闻来源和替代数据，可以更全面地理解公众情绪和经济指标。此外，基于不断演变的情感模式开发预测模型，可实现对衰退指标的准确预测。最后，创建实时监测系统可提供经济形势变化的早期预警机制，帮助在条件变化时进行主动决策。

## 参考文献

* Bianchi, P. A., Monika, C., Miguel, M.-M., and Valbona, S. (2023). Social networks analysis in accounting and finance. *Contemp. Account. Research*, 40(1), 577–623.

* Norz, L.-M., Verena, D., Werner, O. H., and Elske, A. (2023). Measuring social presence in online-based learning: An exploratory path analysis using log data and social network analysis. *Internet High. Educ.*, 56, 100894.

* Irtyshcheva, I., Iryna, K., and Ihor, S. (2022). The economy of war and postwar economic development: world and Ukrainian realities. *Baltic J. Econ. Stud.*, 8(2), 78–82.

* Indaco, A. (2020). From twitter to GDP: Estimating economic activity from social media. *Reg. Sci. Urban Econ.*, 85, 103591.

* Shaheer, I. and Neil, C. (2022). Social representations of tourists’ deviant behaviours: An analysis of Reddit comments. *Int. J. Tour. Res.*, 24(5), 689–700.

# 26 NIRF 排名对印度私立工程学院提升教育体系的影响——基于计算方法的探讨

Ankita Mitra<sup>²⁶</sup>

DOI: [10.1201/9781003471059-26](https://dx.doi.org/10.1201/9781003471059-26)

## 摘要

本研究探讨了基于结果的认证与评估的影响，涵盖国家评估与认证委员会（NAAC）、国家评审委员会（NBA）以及国家机构排名框架（NIRF），对工程教育的作用。这些机构帮助学生在高等教育中实现卓越，每个实体均采用不同的标准评估工程项目的可信度。本研究的主要目标是评估这些排名方法在提升教育质量方面的有效性，特别是在帮助私立工程学院提升声誉方面。本文检验了原假设（假设无影响）与备择假设。评估指标包括教学、学习与资源（TLR）得分、研究与专业实践（RPC）得分、毕业结果（GO）得分、外展与包容性（OI）得分以及个别学院的感知得分。模型的效率通过标准战略指标——均方根误差（root mean square error）来衡量。该指标值越低，表明模型对 NIRF 排名的预测越高效。研究项目的 `p` 值为 0.0466922，而 `F` 值为 0.953308。因此，需要一种考虑此情况的修正解释，例如推测 NIRF 评级将对教育产生显著影响。

**关键词：** ANOVA、置信区间、F 分布、NIRF

## 引言

国家教育排名框架（NIRF）作为印度各高校排名的方法体系。该框架基于多项评估标准，包括毕业成果和科研产出。NIRF 排名在提升印度教育体系方面发挥重要作用，促使高校在教学、科研和公众形象等方面卓越。在此背景下，印度私立工程学院可利用 NIRF 排名提升其在 NIRF 考量的各项指标上的表现。在大多数国家，均设有认证机制，以确保高等教育机构维持教育标准。该过程包括自我评估、现场考察、证据评估以及基于质量的改进建议。为实现目标，国家需保持其设定的高教育标准。每所高等教育机构通常设有管理委员会，负责监督运营并确保最低卓越标准的达成。这通常通过认证体系实现，该体系在多个国家普遍存在，为不同高等教育选项提供评估基准。认证过程包括自我评估、现场检查、证据审查以及制定以质量为导向的建议。

在教育机构领域，主要有三个认证与评估机构：国家认证评估委员会（NAAC）、国家认证委员会（NBA）以及国家教育排名框架（NIRF）。本研究聚焦于 NIRF 排名对印度私立工程学院的影响，旨在通过计算方法（Vasudevan and Sudalaimuthu, 2020; Nassa et al., 2021）提升国家教育体系。研究主要依据 NIRF 评分。当用于评估教育机构时，NIRF 方法论基于一套标准化指标，其核心目标是构建这些指标。这些指标被划分为五大类别，并在每类内进一步细分为更具体的子组（如必要时）。NIRF 排名框架利用多项参数对印度工程学院进行排名，包括教学、学习与资源（TLR）、研究与专业实践（RP）、毕业成果（GO）、外展与包容性（OI）以及认知度（PR）。每个大类预设了相应的权重，子类别之间也可能保持健康的平衡。本研究的第一步是聚合所有相关信息，为建立能为各领域赋值的有效指标体系奠定基础。研究初期重点在于选择精准的方法，以确定每个类别的数值。通过为每个子标题分配数值，可将主标题的总分计算为其子标题分数之和。在计算时，必须为每个标题分配相同的权重，以确保准确性。随着行业对高级机器学习（ML）、图像处理和计算工程等先进技术的拥抱，其重要性日益凸显。这些技术同样成为 NIRF 排名体系以及备受各教育机构推崇的出版物的重要组成部分（Gupta, 2019; Khattar et al., 2020; Mondal et al., 2022; Sengupta et al., 2022）。该排名反映了机构在教学、基础设施、科研、学生就业、产业合作以及受权威组织和教育者认可等方面的整体水平。在当前语境下，毕业成果和包容性对学生就业能力影响显著。三大关键参数为同行评价（PR）、研究产出（RP）和教学与资源（TLR）。在计算总分时，必须为每个标题分配相同的权重，以确保结果准确。利用计算工程技术，特别是方差分析（ANOVA），对 NIRF 排名的适用性进行验证，这将从根本上厘清 NIRF 排名的含义（Anoop and Kumar, 2013）。此方面为本研究的核心关注点。研究后续章节组织得更加清晰明了：首先简要回顾相关文献，随后描述研究方法，阐述实施过程，最后讨论结果并总结研究。

### 相关工作

工业化国家中大学性能评估已相当普遍，但在发展中国家则较少见。研究者采用前沿方法分析影响印度高等教育成本的因素（Bhat et al., 2020），考察了额外成本、规模报酬和范围报酬。他们发现，规模报酬已被广泛利用，但其结果与更发达国家仍有显著差异（Jadhav et al., 2020）。研究还指出，尽管学生人数众多，但高校和学院在教学与学习活动上的投入却在减少。多项研究讨论了大学教育存在的问题，并提出了研究经费、联合研究项目以及研究评估委员会的政策建议，以提升学术实践和标准。在教育排名体系领域，多种主流机器学习（ML）模型已被应用。

principal component analysis（PCA），一种旨在降低数据维度的统计技术，是其中之一。其应用在确定 NIRF 工程学院排名的最优权重方面发挥了关键作用。

另一种被广泛使用的模型是线性回归（LR），它用于建模两个变量之间的关系。该方法成功用于构建能够预测机构 NIRF 排名的机器学习模型。

此外，推荐系统（ML 的一个子类）被用于预测未来大学或学院的排名，并设计通知，提示机构在哪些方面可进行改进以提升排名。同时，学习排名方法（利用 ML 模型预测文档相关性得分）也被采用，分为点向、对位和列表三类。这些 ML 模型在教育排名系统中的运用极大便利了排名预测、分数预估及模型评估。它们为机构提供了在教学、科研和认知度等多个领域提升表现的机会，最终实现更优的教育体系和更高的排名。研究表明，美国在“所有学科”文献引用数量上位居第一，中国排名第二，英国第三，印度第九。

Regarding international university rankings and research criteria, Indian universities lagged far behind Chinese universities. Researchers say that education, significantly higher education institutions (H.E.I.s), is essential for promoting and achieving the sustainable development goals of the United Nations (UN-SDGs) (Nancy et al., 2020). Most institutions, though, do not always use the best frameworks, curricula, pedagogies, and governance rules for promoting sustainability through H.E.I.s. Globally, engineering education is moving from a teacher-centered to a student-centered teaching-learning process, from a content-based to an outcome-based teaching-learning (OBTL) model, from knowledge predation to knowledge sharing, from teachers to facilitators, from traditional scientific disciplines to multi-disciplinary courses, and from chalk-and-whiteboard knowledge acquisition to technology-driven learning. In India, though, many schools and colleges still use old ways of teaching and learning with little hands-on instruction (Surekha et al., 2020; Møller-Skau and Lindstøl, 2022). A nation, once a leader in engineering, medicine, the arts, music, etc., is currently lagging in technical education. The writers analyzed the perspectives of students, parents, academic faculty, and business professionals regarding engineering education and its future.
