

# 基于大规模地理社交网络数据的时空推荐 219

文献 [20] 中来自 Twitter 用户帖的文本方面。Yin 等人 [16] 根据与空间项目相关的内容，同时利用了个人兴趣和局部偏好。Wang 等人 [28] 利用内容信息作为介质，将用户对家乡的个人兴趣转移到新地点。Liu 等人 [33] 通过聚合 LDA 和矩阵分解方法，研究了与空间项目关联的标签对空间推荐的影响。Gao 等人 [68] 研究了空间项目推荐中的空间项目相关内容和用户情感信息（例如用户评论），并报告了良好的性能。还有研究人员关注基于主题的时空模式来补充内容信息 [69]。

## 9.7 结论

在本章中，我们针对空间项目推荐提出了一种时空感知模型 ST-SAGE，该模型有效克服了由旅行局部性和用户行为时空动态性带来的挑战。具体而言，为了应对旅行局部性，ST-SAGE 同时利用了空间项目的共现模式及其内容来推断和迁移用户项目。为了解决用户行为的空间动态性，ST-SAGE 整合了目标地点的本地游客偏好。为了解决用户行为时间动态建模中的数据稀疏性问题，我们利用相似用户群的时间偏好通过平滑处理增强了模型。为了缓解每个区域时间偏好和游客偏好推断所面临的数据稀疏问题，ST-SAGE 采用加法框架，在精心设计的空间金字塔上对偏好进行平滑。我们基于 GraphLab 框架为 ST-SAGE 开发了一种可扩展的并行学习算法以提高模型训练效率，并采用了高效的 top-k 查询技术（即 TA）来加速在线推荐过程。我们进行了广泛的实验，在真实数据集上评估了 ST-SAGE 模型的性能。实验结果显示，ST-SAGE 在推荐效果和效率方面，无论对于家乡推荐还是非家乡推荐，均优于其他空间推荐方法，这证明了 ST-SAGE 在促进用户在其家乡及不熟悉地区旅行方面的有效性。

## 参考文献

- [1] Bao J, Zheng Y, Mokbel MF. Location-based and Preference-Aware Recommendation Using Sparse Geo-Social Networking Data. In: Proceedings of the 20th International Conference on Advances in Geographic Information Systems. SIGSPATIAL; 2012. p. 199–208.
- [2] Yin H, Cui B. Spatio-Temporal Recommendation in Social Media. Singapore: Springer; 2016.
- [3] Cui B, Mei H, Ooi BC. Big Data: The Driver for Innovation in Databases. National Science Review. 2014;1(1):27–30.
- [4] Bao J, Zheng Y, Wilkie D, et al. Recommendations in Location-based Social Networks: A Survey. Geoinformatica. 2015;19(3):525–565.
- [5] Lian D, Zhao C, Xie X, et al. GeoMF: Joint Geographical Modeling and Matrix Factorization for Point-of-Interest Recommendation. In: Proceedings of the 20th ACM SIGKDD International Conference on Knowledge Discovery and Data Mining. SIGKDD;2014, p. 831–840.
- [6] Xie M, Yin H, Xu F, et al. Learning Graph-based Recommendation. In: the 25th ACM International Conference on Information and Knowledge Management. CIKM; 2016.
- [7] Ference G, Ye M, Lee WC. Recommendation for Out-of-Town Users in Location-based Social Networks. In: Proceedings of the 22nd ACM International Conference on Knowledge Management. CIKM; 2013, p. 721–726.
- [8] Wang H, Fu Y, Wang Q, et al. A Location-Sentiment-Aware Recommender System for Home-Town and Out-of-Town Mobile Users. In: SIGKDD; 2017.
- [9] Yuan Q, Kang G, Ma Z, et al. Time-Aware Point-of-Interest Recommendation. In: Proceedings of the 36th ACM SIGIR Conference on Research and Development in Information. SIGIR; 2013, p. 362–372.
- [10] Noulas A, Stellato S, Mascolo C, et al. An Empirical Study of Geographic Activity Patterns in Foursquare. In: Proceedings of the Fifth AAAI Conference on Weblogs and Social Media. ICWSM; 2011.
- [11] Cho E, Myers SA, Leskovec J, et al. Mobility and Mobility: User Movement in Location-based Social Networks. In: Proceedings of the 17th ACM SIGKDD International Conference on Knowledge Discovery and Data Mining. SIGKDD; 2011, p. 1082–1090.
- [12] Lee K, Hong S, Kim SJ, et al. SLAW: A Mobility Model for Human Walks. INFOCOM; 2009, p. 855–863.
- [13] Levandoski J, Sarwat M, Eldawy A, et al. LARS: A Location-Recommender System. In: IEEE 28th International Conference on Data Engineering. ICDE; 2012; p. 450–461.
- [14] Yin H, Zhou X, Cui B, et al. Adapting to User Interest for POI Recommendation. IEEE Transactions on Web and Data Engineering. 2016;28(10):2566–2581.
- [15] Hosseini S, Yin H, Zhang M, et al. Joining Heterogeneous Temporal Properties in Location Recommendation. In: DASFAS; 2017, p. 490–506.
- [16] Yin H, Cui B, Sun Y, et al. LCARS: A Spatial Item Recommender System. ACM Transactions on Information Systems. 2014;32(3):11:1–17.
- [17] Eisenstein J, Ahmed A, Xing EP. Sparse Additive Generative Models of Text. In: International Conference on Machine Learning. ICML; 2011, p. 1041–1048.
- [18] Ahmed A, Kanangal B, Pandey S, et al. Spatio-Temporal Additive Framework for Inferring Home Locations. In: Proceedings of the 24th ACM International Conference on Knowledge Discovery and Data Mining. SIGKDD; 2018, p. 785–794.
- [19] Kanangal B, Ahmed A, Pandey S, et al. Spatio-Temporal Additive Framework for Inferring Home Locations. In: Proceedings of the 24th ACM International Conference on Knowledge Discovery and Data Mining. SIGKDD; 2018, p. 785–794.
- [20] Hu B, Ester M. Topic Modeling in Social Media. In: Proceedings of the 7th ACM Conference on Recommender Systems. RecSys; 2013. p. 25–32.
- [21] Wang W, Yin H, Chen L, et al. Geo-SAGE: A Geographical Sparse Addative Model for Spatial Item Recommendation. In: Proceedings of the 21st ACM International Conference on Knowledge Discovery and Data Mining. SIGKDD, Sydney, Australia; 2015. New York, NY: ACM; p. 1255–1266.
- [22] Yin H, Zhou X, Shao Y, et al. Joint Modeling of User Check-in Behaviors for Point-of-Interest Recommendation. In: the 24th ACM International Conference on Information and Knowledge Management. CIKM; 2015. p. 1631–1640.
- [23] Wang W, Yin H, Chen L, et al. ST-SAGE: A Spatio-Temporal Model for Spatial Recommendation. ACM Transactions on Intelligent Systems. 2017;8(3):18–45.
- [24] Yin H, Wang W, Wang H, et al. Spatial-Aware Hierarchical Collaborative Deep for POI Recommendation. IEEE Transactions on Knowledge and Data Engineering. 2017;29(11):2537–2551.
- [25] Chen W, Yin H, Wang W, et al. Exploring Spatio-Temporal Behaviors for User Linkage. In: CIKM;2017.
- [26] Li R, Wang S, Deng H, et al. Social User Profiling: Unified and Discriminative Influence for Inferring Home Locations. In: Proceedings of the 18th ACM SIGKDD International Conference on Knowledge Discovery and Data Mining. SIGKDD; 2012. p. 1023–1031.
- [27] Scatello S, Noulas A, Botte R, et al. Socio-Spatial Properties of Online-Based Social Networks. In: ICSWM;2011.
- [28] Wang W, Yin H, Chen L, et al. Geo-SAGE: A Geographical Sparse Addative Model for Spatial Item Recommendation. In: Proceedings of the 21st ACM International Conference on Knowledge Discovery and Data Mining. SIGKDD, Sydney, Australia; 2015. New York, NY: ACM; p. 1255–1266.
- [29] Yin H, Zhou X, Shao Y, et al. Joint Modeling of User Check-in Behaviors for Point-of-Interest Recommendation. In: the 24th ACM International Conference on Information and Knowledge Management. CIKM; 2015. p. 1631–1640.
- [30] Mok D, Wellman B, Carrasco J. Does Distance Matter in the Age of the Internet?. Urban Studies. 2010;47(13):2747–2783.
- [31] Yin H, Cui B, Huang Z, et al. Joint Modeling of Users’ Interests and Mobility Patterns for Point-of-Interest Recommendation. In: Proceedings of the 23rd ACM International Conference on Multimedia. MM; 2015. p. 819–822.
- [32] Yin H, Cui B, Zhou X, et al. Joint Modeling of User Check-in Behaviors for Real-time Point-of-Interest Recommendation. ACM Transactions on Information Systems. 2016;35(2):11:1–44.
- [33] Liu B, Xiong H. Point-of-Interest Recommendation in Location Based Social Networks with Topic and Location Awareness. In: Proceedings of

