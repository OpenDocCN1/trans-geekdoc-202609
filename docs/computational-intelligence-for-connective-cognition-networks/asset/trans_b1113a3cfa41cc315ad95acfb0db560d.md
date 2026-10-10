

*   \[19\]S. Ruan, B. Chen, K. Song, and H. Li. Weighted naïve Bayes text classification algorithm based on improved distance correlation coefficient. Neural Computing and Applications, vol. 34, nos. 4, pp. 2729–2738, 2022.

*   \[20\]P. Domingos and Michael Pazzani. On the optimality of the simple Bayesian classifier under zero-one loss. Machine Learning, vol. 29, nos. 2-3, pp. 103–130, 1997.

*   \[21\]S.-B. Kim, H.-C. Rim, D.-S. Yook, and H.-S. Lim. Effective methods for improving Naïve Bayes text classification. In 7th Pacific Rim International Conference on Artificial Intelligence, vol. 7, pp. 414–423, 2002.[⏎](#ch17.xhtml#r188b)

*   \[22\]D. Isa, L. H. Lee, V. P. Kallimani, and R. Rajkumar. Text documents preprocessing with the Bayes formula for classification using support vector machine. IEEE Transactions on Knowledge and Data Engineering, vol. 20, no. 9, pp. 1264–1272, 2008.[⏎](#ch17.xhtml#r189b)

*   \[23\]S.-B. Kim, K.-S. Han, H.-C. Rim, and S. H. Myaeng. Some effective techniques for Naive Bayes text classification. IEEE Transactions on Knowledge and Data Engineering, vol. 18, no. 11, pp. 1457–1466, November 2006.[⏎](#ch17.xhtml#r190b)

*   \[24\]P. Domingos and M. J. Pazzani. On the optimality of the simple Bayesian classifier under zero-one loss. Machine Learning, vol. 29, nos. 2-3, pp. 103–130, 1997.[⏎](#ch17.xhtml#r191b)

*   \[25\]T. S. Guzella and W. M. Caminhas. A review of machine learning approaches to spam filtering. Expert Systems with Applications, vol. 36, no. 7, pp. 10206–10222, 2009.[⏎](#ch17.xhtml#r192b)

*   \[26\]J. Schmidhuber and S. Hochreiter. *Long short-term memory*. Neural Computation, vol. 9, no. 8, pp. 1735–1780, 1997.[⏎](#ch17.xhtml#r193b)

*   \[27\]Z. Huang, W. Xu, and K. Yu. Bidirectional LSTM-CRF Models for Sequence Tagging. *arXiv preprint arXiv:1508.01991*, 2015.[⏎](#ch17.xhtml#r194b)

*   \[28\]M. Schuster and K. K. Paliwal. Bidirectional recurrent neural networks. IEEE Transactions on Signal Processing, vol. 45, no. 11, pp. 2673–2681, 1997.[⏎](#ch17.xhtml#r195b)

*   \[29\]A. Graves and J. Schmidhuber. Framewise phoneme classification with bidirectional LSTM and other neural network architectures. Neural Networks, vol. 18, no. 5, pp. 602–610, 2005.[⏎](#ch17.xhtml#r196b)

*   \[30\]R. Ghaeini, S. A. Hasan, V. V. Datla, J. Liu, K. Lee, A. Qadir, Y. Ling, A. Prakash, X. Z. Fern, and O. Farri. DR-BiLSTM: Dependent Reading Bidirectional LSTM for Natural Language Inference. In Proceedings of the 2018 Conference of the North American Chapter of the Association for Computational Linguistics: Human Language Technologies, Vol 1 (Long Papers), pp. 1460–1469, 2018.[⏎](#ch17.xhtml#r197b)

*   \[31\]S. Hochreiter and J. Schmidhuber. Long short-term memory. Neural Computation, vol. 9, no. 8, pp. 1735–1780, 1997.[⏎](#ch17.xhtml#r198b)

*   \[32\]E. Kiperwasser and Y. Goldberg. Simple and Accurate Dependency Parsing Using Bidirectional LSTM Feature Representations. *Transactions of the Association for Computational Linguistics*, vol. 4, pp. 313–327, 2016.[⏎](#ch17.xhtml#r199b)

*   \[33\]A.Rao and N. Spasojevic. Actionable and Political Text Classification Using Word Embeddings and LSTM. Technical report, Lithium Technologies, July 2016.[⏎](#ch17.xhtml#r200b)

*   \[34\]K. S. Tai, R. Socher, and C. D. Manning. Improved Semantic Representations from Tree-Structured Long Short-Term Memory Networks.In Proceedings of the 53rd Annual Meeting of the Association for Computational Linguistics and the 7th International Joint Conference on Natural Language Processing, vol. 1, pp. 1556–1566, 2015.[⏎](#ch17.xhtml#r201b)

*   \[35\]N. Correia da Silva et al. Document Type Classification for Brazil’s Supreme Court Using a Convolutional Neural Network. In 10th International conference on forensic computer science and cyber law (ICoFCS), Sao Paulo, Brazil, pp. 29–30, 2018.[⏎](#ch17.xhtml#r202b)

*   \[36\]P. H. Luz de Araujo, T. E. de Campos, R. R. R. de Oliveira, M. Stauffer, S. Couto, and P. Bermejo. *Lener-br: A Dataset for Named Entity Recognition in Brazilian Legal Text*. In Proceedings of the International Conference on the Computational Processing of Portuguese (PROPOR), Canela, RS, Brazil, vol. 13, pp. 313–323, September 24–26, 2023.[⏎](#ch17.xhtml#r203b)

# 第8章 FNDetector：利用各种特征组合进行假新闻检测

Yun Hwa Wong (Jenny), Amanpreet Kaur, and Sangeeta Lal

DOI: [10.1201/9781003569619-8](http://doi.org/10.1201/9781003569619-8)

## 8.1 简介

在技术爆炸和现代世界的时代，假新闻正以惊人的速度渗透我们的日常生活。剑桥词典将“假新闻”定义为“看似新闻的虚假故事，通过互联网或其他媒体传播，通常旨在影响政治观点或作为玩笑”\[[1](#ch18.xhtml#r204)\]。据世界领先的公共服务广播机构英国广播公司（BBC）称，假新闻的历史始于2000年前罗马共和国的内战期间。屋大维想要赢得战争，便通过在硬币上印制标语并分发给公众，散布针对马克·安东尼的“假新闻”。在19世纪，印刷术发明后。1835年，一家报纸刊登了关于生活在月球上的奇异生物的文章，如飞行蝙蝠人和独角兽\[[2](#ch18.xhtml#r205)\]。

在在线社交媒体概念出现之前，大多数人通过阅读报纸或收听广播电台获取新闻。凭借轻松连接人群和分享内容的特性，通过在线社交媒体传播新闻的速度急剧增加。

\[[3](#ch18.xhtml#r206)\]对2006年至2017年Twitter数据集的一项研究显示，排名前1%的假新闻影响了1000到100000人，而真相很少传播给超过1000人。该研究展示了假新闻在在线社交媒体上传播的速度有多快。

假新闻在许多领域普遍存在，尤其是在政治领域。在2016年美国总统提名过程中，关于唐纳德·特朗普的假新闻备受青睐，并在社交媒体上广泛传播。在Facebook上，有115条支持特朗普的假新闻故事和41条支持克林顿的假新闻故事\[[4](#ch18.xhtml#r207)\]。假新闻在公共论坛传播可能产生的影响引起了不同研究人员和公众的特别关注。然而，假新闻不仅仅关乎政治问题。近年来，当灾难或大流行病发生时，假新闻会广泛传播。最好的例子是2019年发生的SARS-CoV-2（COVID-19）病毒爆发。存在大量与如何从疾病中康复相关的假新闻或虚假信息，例如食用辣椒有助于预防或治愈COVID-19，饮酒可以保护公众免受COVID-19侵害\[[5](#ch18.xhtml#r208)\]。例如，一条关于蒸汽能杀死冠状病毒的Facebook用户帖子式假新闻已在Facebook上被分享超过33,000次\[[6](#ch18.xhtml#r209)\]。研究人员投入了大量时间和精力开发不同的算法和模型来检测假新闻。de Beer和Matthee\[[7](#ch18.xhtml#r210)\]对各种研究人员使用的不同方法进行分类研究。根据de Beer和Matthee\[[7](#ch18.xhtml#r210)\]的说法，现有研究人员使用的方法可分为五大类（参见[表8.1](#ch18.xhtml#t13)）。每种方法的示例可在[表8.1](#ch18.xhtml#t13)中找到。

**表8.1** 识别假新闻的各种方法的示例或描述[⏎](#ch18.xhtml#t13b)

| **方法** | **示例/描述** |
| --- | --- |

