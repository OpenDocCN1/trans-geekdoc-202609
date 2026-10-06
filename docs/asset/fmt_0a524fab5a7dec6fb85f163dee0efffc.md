
# 仇恨言论检测的多语言综述

## 表 5.2 英语数据集

| 数据集 | 关注领域 | 规模 | 来源 | 策略 |
| --- | --- | --- | --- | --- |
| OCBV [61] | 仇恨言论 | 56,100 | Gab, Reddit | 多级 |
| QLBW [62] | 仇恨言论 | 3.5M | | 多级 |
| QEBW [63] | 仇恨言论 | 18,667 | | 多级 |
| RBKML [65] | 仇恨言论 | 4,999 | Twitter | 二分类 |
| SB [66] | 攻击性语言 | 11M | Reddit | 二分类 |
| SOCC [67] | | 1,043 | 新闻网站 | 多级 |
| TweetBLM [68] | 种族主义 | 9,165 | Twitter | 二分类 |
| VY [69] | 仇恨言论 | 1,364 | Twitter | 非二分类 |
| W [70] | 仇恨言论、种族主义、性别歧视 | 6,909 | Twitter | 非二分类 |
| WH [71] | 仇恨言论、种族主义 | 16,907 | Twitter | 非二分类 |

文中介绍了英语。表 5.2 的第一列代表数据集的名称。如果数据集作者提出了任何名称，我们将使用该名称；否则，我们使用 [6] 中相同的约定来命名数据集。例如，Alatawi, H. S.、Althali, A. M. 和 Moria, K. M. 是该数据集的作者；那么数据集的名称为 `AAM`。第二列代表数据集的关注领域，如仇恨言论、辱性语言等。第三列代表数据集的大小。第四列代表数据集的来源，最后一列代表策略。

### 5.3.2 其他语言中仇恨言论和攻击性语言的研究

文中介绍了多语言环境。表 5.2 的第一列代表数据集的名称。如果数据集作者提出了任何名称，我们将使用该名称；否则，我们使用 [6] 中相同的约定来命名数据集。例如，Alatawi, H. S.、Althali, A. M. 和 Moria, K. M. 是该数据集的作者；那么数据集的名称为 `AAM`。第二列代表数据集的关注领域，如仇恨言论、辱性语言等。第三列代表数据集的大小。第四列代表数据集的来源，最后一列代表策略。

（注：原文后续部分存在大量重复的 OCR 错误，已根据要求去重并仅翻译核心逻辑内容）

## 表 5.3 其他语言可用的数据集

| 数据集 | 语言 | 焦点 | 规模 | 来源 | 策略 |
| --- | --- | --- | --- | --- | --- |
| ABP [100] | 意大利语 | 恐同症 | 1,859 | Twitter | 二分类 |
| AKM [75] | 阿拉伯语 | 仇恨言论 | 6,136 | Twitter | 多级 |
| AMFE [90] | 印尼语 | 仇恨言论 | 1,100 | Twitter | 二分类 |
| CMVCT [101] | 意大利语 | 仇恨言论 | 6,710 | Instagram | 二分类 |
| DCTDP [107] | 意大利语 | 仇恨言论 | 6,502 | Facebook | 非二分类 |
| FEL [105] | 斯洛文尼亚语 | 仇恨言论、儿童性待 | 13,000 | 在线报告 | 多级 |
| FLKA [104] | 瑞典语 | 仇恨言论 | 3,056 | Twitter 网页论坛 | 非二分类 |
| IS [78] | 孟加拉语 | | 5,126 | Facebook | 非二分类 |
| LNN [105] | 越南语 | 仇恨言论、攻击性 | 33,400 | YouTube | 非二分类 |
| MDDD [106] | 土耳其语 | 语言侮辱性语言 | 10,224 | Twitter | 非二分类 |
| MDM [107] | 阿拉伯语 | 仇恨言论、冒犯、粗俗 | 33,100 | Twitter | 非二分类 |
| MisoCorp-2020 [108] | 西班牙语 | 攻击性 | 7,682 | Twitter | 二分类 |
| MW [109] | 阿姆哈拉语 | | 49,124 | Facebook | 多级 |
| NCCVG [110] | 葡萄牙语 | 攻击性语言 | 7,672 | Twitter | 二分类 |
| PBBPS [6] | 意大利语 | 仇恨言论 | 4,000 | Twitter | 非二分类 |
| PM [111] | 葡萄牙语 | 攻击性语言 | 2,283 | 新闻网站 | 多级 |
| PMBA [112] | 希腊语 | 攻击性语言 | 1,500 | 新闻 | 二分类 |
| RATI [777] | 孟加拉语 | | 30,000 | YouTube | 二分类 |
| RRCCKW [113] | 德语 | 仇恨言论 | 541 | Twitter | 二分类 |
| SPBS [114] | 意大利语 | 仇恨言论、种族主义、侮辱性语言 | 6,009 | Twitter | 非二分类 |
| T-HSAB [115] | 阿拉伯语 | | 6,039 | 人工 | 非二分类 |
| VPGSJ [116] | 马拉雅姆语 | 仇恨言论、冒犯、语言、粗俗 | 25,000 | Twitter | 非二分类 |

维基百科毒性评论分类的准确率达到 `0.98`，Facebook 测试集的加权 F 分为 `0.63`，Twitter 测试集为 `0.59`。Mandl 等人 [125] 和 Chakravarthi 等人 [126] 了英语、印地语和德语数据集的模型和结果。他们确定最佳模型是基于 `LSTM` 的网络，该网络能够更好地捕捉多语言上下文。Kumari 等人 [127] 提出了一种基于 `CNN` 和二值粒子群优化的模型，将带有图像和文本的多模态帖子分类为非攻击性、中度攻击性和高度攻击性类别。[128–131] 中的作者提出了一个新的、包含泰米尔语、马拉雅拉姆语和坎纳达语的德拉维达语数据集。Bohra 等人 [132] 扩展了之前的

## 表 5.4 代码混合和多语言可用的数据集

| 数据集 | 语言 | 焦点 | 规模 | 来源 | 策略 |
| --- | --- | --- | --- | --- | --- |
| BVSAS [132] | 印地语-英语 | 仇恨言论 | 4,575 | Twitter | 二分类 |
| CAMPSM [133] | 马来语和英语 | 仇恨言论、人身攻击 | 5,000 | YouTube | 二分类 |
| CAMPSM [134] | 米尔语-英语法语、法语 | 仇恨言论 | 4,000 | Twitter, Helo | 二分类 |
| CONAN [136] | 英语 | 仇恨言论 | 15,024 | 人工 | 多级 |
| CPJMKS [128] | 马来语-英语 | 仇恨言论 | 20,010 | YouTube | 多级 |
| CPJMKS [137] | 泰米尔语-英语 | 仇恨言论、侮辱 | 64,997 | YouTube | 多级 |
| HEOT [137] | 印地语-英语 | | 3,679 | Twitter | 非二分类 |
| KanMD [137] | 坎纳达语-英语 | 仇恨言论 | | YouTube | 多级 |
| KRBM [117] | 印地语-英语 | 仇恨言论 | 39,000 | Twitter, Facebook | 多级 |
| MPBDSH [139] | 奥里亚-英语 | 仇恨言论、攻击性语言 | 5,000 | Twitter, Facebook, Facebook | 非二分类 |
| RSGCFM [140] | 印地语-英语 | | 3,367 | Facebook, Twitter | 二分类 |
| SBHK [141] | 捷克语、英语、法语、意大利语 | | 5,077 | 新闻、网站 | 二分类 |

代码混合和多语言可用数据集如表 5.4 所示。他们报告了使用 `SVM` 和基于 `n-gram` 的词典特征对印地语和英语进行仇恨言论检测的初步结果，准确率为 `0.71`，比表 5.2 多包含一列，且所有列值与表 5.2 相同。

## 5.4 结论与未来方向

识别社交媒体上的仇恨言论不是一项易事。仇恨言论定义的歧义以及充足数据集的缺失为从事这项工作的人带来了更多问题。但随着新方法和合适数据集的出现，社区将能够解决这一问题。在这方面，本章将解释不同上下文下的仇恨言论，并对现有文献进行简要回顾。由于互联网不再限于英语，此外，人们在社交媒体上使用多种语言，社区必须开发更多语言的数据集。仇恨言论是一个不断发展的领域，新语言和脚本的加入使得仇恨言论的识别变得更加复杂。一个小数据集可能会导致过拟合，因此，`NLP` 社区需要解决这些问题以使社交媒体无仇恨。

## 参考文献

[1] www.bbc.com/newsbeat-59290

[2] Abderrouaf, C., & Oussalah, M. (2019, December). 关于在线仇恨言论检测。在 2019 大数据国际会议 (Big Data) (pp. 5595–5670)。IEEE.

[3] Lucas, B. (2014). 监控和映射仇恨言论的方法。GSDR 应用知识服务, 14, 1–12.

[4] Schmidt, A., & Wieland, M. (2019, January). 使用自然语言处理的仇恨言论综述。在社交媒体自然语言处理第五届国际工作会上，2017年4月3日，西班牙瓦伦西亚 (pp. 1–10)。计算语言。

[5] Fortuna, P., & Nunes, S. (2018). 文本自动仇恨言论检测综述。ACM Computing Surveys (CSUR), 51(4), 1–30.

[6] Poletto, F., Basile, V., Bosco, C., Patti, V., & Stranisci, M. (2019). 仇恨言论标注：三种比较方案。在2019 意大利计算语言会议上，CLiit 2019 (Vol. 2481, pp. 1–8)。CEUR-WS。

[7] Macney, S., Yao, H. R., Yang, E., Goharian, N., & Frieder, O. (2019). 仇恨言论检测：挑战与解决方案。PoS one, 14(8), e022152.

[8] Nockoley, J. T. (2000). 仇恨言论。美国宪法百科书, 3(2), 1277–1279.

[9] 欧洲委员会 (1997)。p. 107 https://rm.coe.int/CoERMPublicCommonSearchServices/DisplayDCTMContent?documentId=09000168050d5b

[10] Facebook (2013)。Facebook 认为什么是仇恨言论？来自 https://www.facebook.com/help/13540213990490

[11] YouTube (2017). 仇恨言论。来自 https://support.google.com/youtube/answer?2801933?hl=en

[12] Twitter (2017). Twitter 规则。来自 https://support.twitter.com/articles/

[13] Cohen-Almagor, R. (2011)。打击互联网上的仇恨和偏见。Policy and Internet, 3(3), 1–26.

[14] Ross, B., R, M., Carbonell, G., Cabrera, B., Kurowski, N., & Wojatki, M. (2017). 衡量仇恨言论标注的可靠性：欧洲难民危机。arXiv:1701.0.

[15] Roy, P. K., Singh, A., Tripathy, A. K., & Das, T. K. (2022). 网络欺凌检测：一种集成学习方法。计算机科学与工程国际期刊，25(3), 315–324.

[16] Vogel, I., & Meghna, M. (2021, September). Twitter 上的仇恨言论分析：SVM vs. LSTM。在 IEEE (Working Notes) (pp. 2193–2200)。

[17] Roy, P. K., Singh, A., Tripathy, A. K., & Das, T. K. (2022). 识别社交平台上的网络欺凌。在分布式计算与机器学习进展中 (pp. 186–195)。Springer，新加坡。

[18] Ibrahim, O. M., & Budi, I. (2019, August)。印尼语多语言仇恨言论和检测。在第三届适当语言工作会上 (pp. 46–57)。

[19] Ashwin, G. D. S., Irina, I., & Dominique, F. (2020). 使用深度神经网络的仇恨言论分类。信息技术评论杂志, 25(1), 1–12.

[20] Roy, P. K., Tripathy, A. K., Das, T. K., & Gao, X. Z. (2020)。 基于深度神经网络的仇恨言论检测框架。IEEE Access, 8, 20491–20496.

[21] Bisht, A., Singh, A., Bhataduria, H. S., & Virmani, J. (2021)。 仇恨言论检测文本表示的研究。arXiv preprint:2102.04521.

[22] Saha, P., Matthew, B., Goyal, P., & Mukherjee, A. (2018)。 Hatatemiders：检测针对女性的仇恨言论。arXiv preprint:1812.0670.

[23] Razavi, A. H., Inken, D., Uitsky, S., & Matwin, S. (2010)。 使用多级分类的攻击性语言检测。在加拿大人工智能会议上 (pp. 16–27)。Springer，柏林，黑堡。

## 多语言仇恨言论检测综述

- [26] Warner, W., & Hirschberg, J. (2012, 6). 宽基准上的仇恨言论检测。In Proceedings of the Second Workshop on Language in Social Media (pp. 19–26).

- [27] Mondal, M., Silva, L., Correa, D., & Benvenuto, F. (2018). 社交媒体中显性仇恨表达的使用特征描述。New Review of Hypermedia and Multimedia, 24(2), 110–130.

- [28] Rocha, S., Shaikh, S., Khand, H., Zafar, A., & Mujtaba, G. (2020). 使用机器学习的自动言论检测：比较研究。International Journal of Advanced Science and Applications, 11(8).

- [29] Jain, M., Goel, P., Singla, P., & Tehran, R. (2021). 用于言论检测的不同词嵌入对比。In Data Analytics and Management (pp. 251–265).

- [30] Orts, Ö. G. (2019). SemEval-2019 任务 5 中 Twitter 上移民和女性的仇恨言论多语言检测。In 13th International Workshop on Semantic Evaluation (pp. 460–463).

- [31] Kwok, I., & Wang, Y. (2013). 定位仇恨：针对……的推文检测。In Proceedings of the Twenty-Seventh AAAI Conference on Artificial Intelligence (pp. 1621–1622).

- [32] Green, E., & Smeaton, A. (2004). 使用支持机对种族主义文本分类。In Proceedings of the 27th Annual ACM SIGIR Conference on Research and Development (pp. 468–469).

- [33] Davidson, T., Warmsley, D., Macy, M., & Weber, I. (2017). 自动化仇恨言论检测与冒犯性语言问题。In Proceedings of the International AAAI Conference on Web and Social Media (Vol. 11, No. 1, pp. 512–515).

- [34] Putri, T. A., Sriahi, S., Sari, R. D., Rahmani, H. (2020, 4). 用于言检测的分类算法对比。In IOP Series: Materials Science and Engineering (Vol. 830, No. 3, 032006).

- [35] Salminen, J., Albrecht, H., Milković, M., Jung, S., An, J., Kwak, H., & Jansen, B. (2018). 在线仇恨剖析：用于识别和分类新闻中仇恨的分类法和机器学习模型。Twelfth AAAI Conference on Web and Social Media, ICWSM 2018 (pp. 330–339).

- [36] Mikolov, T., Sutskever, I., Chen, K., Corrado, G. S., & Dean, J. (2013, 12). 用于组合的词和短语分布式表示。In Proceedings of the 26th International Conference on Information Processing Systems – Volume 2 (pp. 3111–3119).
