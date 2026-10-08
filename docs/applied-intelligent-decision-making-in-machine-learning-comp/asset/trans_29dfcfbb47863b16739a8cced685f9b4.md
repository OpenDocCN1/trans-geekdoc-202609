

## 基于前馈神经网络的特定领域期刊推荐

## 不同方法的运行时间

![](img/d1bf16e7dc1fe5d49ee33c2dfa5cdb06_117_0.png)

图 5.7 不同样本的预测准确率。

优于所有其他模型。这是因为我们提出的技术是为处理特定领域环境下的推荐问题而构建。

其次，我们评估了 DICN 方法在不同样本数量下的能力。结果如图 5.7 所示。从图中可以看出，所提方法的预测准确率随着训练样本数量的增加而提高。这是因为随着训练样本规模的增大，学习模型将变得更加显著。然而，当样本对的数量达到 1000 左右时，集合大小对模型效率的影响不再显著。综而言之，极少量的训练样本就足以让所提的汇网络有效地学习这些模式。

图 5.8 显示了所提方法与其他现有方法在输入样本数量变化时的运行时间。可以看出，当样本对的大小增长时，与现有技术相比，所提方法的运行时间大幅增加。从实验结果可以得出结论：随着样本对大小的增加，训练模型的时间也随增加。然而，分析图 5.7 和 5.8 可以发现，大量的样本不会显著影响预测模型的性能，但会导致运行时间变差。

## 不同样本大小的预测准确率

![](img/d1bf16e7dc1fe5d49ee33c2dfa5cdb06_117_1.png)

图 5.8 所提方法与现有方法的运行时间比较。

### 5.4.2 结果分析

从实验结果可以得出以下结论：

- 1. 如数据收集过程所示，通常很难获取某少数同行的所有文本数据。因此，可获取的论文数据是部分性的；例如，当只能使用论文标题时，基于内容的推荐效果很差。相比之下，如果使用论文的所有文本数据来解决推荐问题，计算复杂度将非常高。
- 2. 大多数现有基于图的方法没有考虑网络底层的语义含义；它们使用同质网络或二分网络来处理推荐问题。
- 3. 基于汇网络的推荐具有影响力，并且封装了比简单基于图的方法更丰富且复杂的含义。结合特定领域数据的推荐方法与其它方法相比，计算成本更低且性能更好。

## 5.5 结论与未来工作

在本章中，我们提出了一种神经网络和基于最近邻的方法，为研究人员推荐领域特定的文章。为了实现这一点，我们通过从 Google Scholar、Semantic Scholar、Scopus、Web of Science 和 Microsoft Academic 数据等多个仓库中抓取、整合和预处理领域特定数据，构建了一个网络。主要，我们建议了一种根据研究人员感兴趣的领域来推荐领域特定文章的方法。在所提出的汇方法中，用户的领域知识及其研究兴趣被用于发现知识差距，而汇网络旨在推荐能够帮助弥补该差距的领域论文。该方法首先根据领域语料库抓取领域特定数据。本章的贡献如下：在第一阶段，使用神经网络将筛选的领域特定文档嵌入到线性空间，使得相似的领域特定文档更接近彼此。选择种子文档的最近邻作为候选对象，并使用训练过的神经网络对其进行重新排序，该网络用于通过分配概率排名，以区分文档是否应该被推荐。实验结果表明，与最先进的方法相比，所提基于领域的方法提供了最好的整体性能。领域特定数据减少了搜索空间，并有助于快速识别与种子文档相似的文档，从而降低了计算成本。关于未来工作，所提出的汇网络可以自动部署在分布式环境中以推荐领域文章。

## 参考文献

Balla, A., Stassopoulou, and M. D. Diakakos. 2011. Real-time web crawler. In 2011 18th International Conference on Telecommunications. IEEE, Ayia Napa, Cyprus, pp. 428–432.

Basi, C., Hirsh, H., Cohen, W., and Nevill-Manning, C. 2001. Technical paper recommendation. A study in combining multiple information sources. Journal of Artificial Intelligence, 14, 231–252.

Bhagwatula, C., Feldman, S., and W. Ammar. 2018. Content-based citation recommendation. arXiv preprint arXiv:1802.08301.

Blei, D. M., A. Y. Ng, and M. I. Jordan. 2003. Dirichlet allocation. Journal of Machine Learning 3(3):993–1022.

Bomhardt, C., Gaul, L., and Schmidt-Thieme, 2005. Web robot detection pre-processing web log files for reason. In Developments in Classification and Data Analysis. Springer, Berlin, pp. 113–154.

Cai, T., Cheng, L., and S. Zhou. 2016. An efficient and simple graph model for scientific article. In International Conference on Conceptual Modeling. Springer, pp. 248–259.

Cantador, I. and P. Castells. 2006. Multilayer social network detection by ontology-based user clustering: Application to collaborative filtering. In International Conference on Knowledge Engineering and Management. Springer, pp. 334–339.

Das, N., Dey, and V. E. 2019. Real-Time Data Analytics for Large Scale Data. Academic Press, London.

Das, H. A., Naik, K. Jena, and Behera. 2015. A novel pso based back propagation-MLP (PSO-BP) for classification. In Computational Intelligence in Data Mining. Springer, Springer, Vol. 2, pp. 461–471.

Das, H. B., Naik, S. S., Mahato, and M. Rout. 2020a. An experimental analysis of machine learning algorithms on biomedical data. In Classification of diabetes mellitus (DMD): Data mining, Analytics and Networking. Springer, Springer, pp. 339–449.

Das, H. B., Naik, S. S., and M. Rout. 2020b. Medical data analysis using neuro-fuzzy with feature extraction method. In Fuzzy Systems 2020:1–15.

Davoodi, E. M. Afsharchi, and K. Kmier. 2012. A social network-based approach to expert recommendation. In International Conference on Hybrid Intelligence Systems. Springer, Berlin, pp. 91–102.

Gemmis, M., Lops, Semeraro, C. Musto. 2015. An investigation on serendipity in recommender systems. Information Processing & Management 51(5):695–717.

Dey, N., S. Ashour, and R. Goswami. 2018. Histopathological Image Analysis. In Intelligent Decision Making in Machine Learning. IGI Global, Hershey, PA.

Drachler, H., Hummel, and R. Kopp. 2008. Identifying the goal, user model and conditions of recommender systems for formal and informal learning. Journal of Digital Information 10(2):4–24.

Glez-Peña, D., Lourenço, M. López-Fernández, and Fdez-Riverola. 2013. Web scraping techniques in an API. Briefings in Bioinformatics 15(5):788–797.

Guan, C., C. Wang, K. Yang, and X. He. 2010. Document recommendation in social tagging. In Proceedings of the 19th International Conference on Wide Web, Raleigh, pp. 391–400.

Haddaway, N. R. 2015. The use of web-scraping software for grey literature. Grey Journal 11(3):186–190.

Liang, T.-P., Y-F. Yang, D.-N. Chen, and Y.-C. Ku. 2008. Semantic-expansion approach to personalized knowledge recommendation. Decision Support Systems 45(3):401–412.

Wu, Z.-W. and S.-Y. Yu. 2006. Web based on hidden markov. 2006 International Conference on Communications, Circuits and Systems. IEEE, Vol. 3, pp. 1806–1810.

Ma, Y., Y. Zhang, and J. Zeng. 2019. Newly published scientific papers recommendation in heterogeneous information. Mobile Networks and Analytics 24(1):69–79.

Meschenmoser, P., Neuschke, M. Holz, and B. Gipp. 2016. Scraping web repositories: challenges and solutions for automated content extraction. D-Lib Magazine 22:2–20.

Pan, C. and W. Li. 2010. Research paper recommendation with topic analysis. In 2010 International Conference on Computer Design and Applications. IEEE, Qinhuangdao, China, Vol. 4, pp. 2–64.

Rout, A. K. Jena, J. K., and H. Das. 2020. Teaching–learning optimization cascaded-convolution neural network for exchange rates prediction. Smart Intelligent Computing Applications. Springer, Berlin, pp. 635–645.

Shobha, K. and Nicklas. 2020. Integration and pre-processing of scientific publications from multiple data sources. In Smart Intelligent Computing Applications. Springer, Berlin, pp. 647–655.

