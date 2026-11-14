

| 作者 [引用] | 采用的方法 | 特性 | 挑战 |
|---|---|---|---|
| Goel 等人 [6] | 基于蜂群和人工免疫系统的智能技术 | - 更好的图像分类<br>- 地理空间特征提取清晰且准确<br>- 每个类别的光谱签名使用训练数据计算得出。 | - 高计算复杂度<br>- 未涵盖土地覆盖特征 |
| Shi 等人 [7] | 亲和传播 (AP) 算法 | - 使用图形处理单元 (GPU) 进行空间聚类分析。<br>- 有能力跟踪不在连续空间中的数据。<br>- 以准确的方式处理大数据。 | - 低可扩展性<br>- 内存空间有限<br>- 不满足三角不等式。 |
| Barik 等人 [8] | K-means 聚类算法 | - 低延迟<br>- 高吞吐量<br>- 拥有足够的存储用于数据可视化和分析<br>- 云服务器开销已降低 | - 云未保留用于长期分析。<br>- 需要高效的大数据处理和处理。 |

## 10.4 方法

图 10.1 显示了所提议的地理空间数据分类模型。尽管可以使用地理空间数据开发各种与应用相关的分类模型，但本研究提案的主要目的是了解适合特定地点的行业类型，如微型行业、宏观行业、中型行业、大型行业、小型行业和超大型行业。这是因为许多因素影响着企业和行业的位置决策，包括靠近原材料供应、劳动力可用性、良好的通信和靠近市场。在这里，将利用地理空间数据来完成实验，从中追踪 X 和 Y 坐标，分别与纬度和经度信息相关。由于数据量巨大，因此将其交给 Hadoop 框架来处理这些大数据。通常，Hadoop 框架是一个用 Java 编写的 Apache 开源框架，允许使用简单的编程模型在计算机集群上对大型数据集进行分布式处理。Hadoop 框架允许用户

![](img/cd1801130f8a9057bd2f396e8025ba69_184_0.png)

### 图 10.1 地理空间工业数据分类框图。

可以快速使用大数据编写和测试分布式系统。然后，从映射-归约数据中，将生成诸如简单比值植被指数、归一化差值植被指数、Kauth–Thomas Tasseled cap 和红外指数变换以及地理位置等植被指数。在此数据形成之后，将执行序列模式挖掘，并将这些模式指定为特征。此外，提取的特征将送入一种名为深度置信网络 (DBN) [23] 的深度学习架构，用于预测地点适合的行业类型。作为主要贡献，DBN 的权重将由一种名为修改花粉传播算法 (FPA) 的著名优化算法进行优化，以便分类精度达到最大。FPA [24] 是一种元启发式算法，灵感来源于花朵的授粉过程。为了最大化预测精度，预测结果与实际结果之间的误差将被最小化，这被视为本研究的主要目标函数。

## 10.5 预期成果

所提议的预测模型将在 Java 编程平台上进行，并将进行调查。在分析部分，所提议模型的性能将根据 Type I 和 Type II 指标与现有模型进行比较。

## 参考文献

- [1] Florian Hillen, Bernhard Höfle, “Geo-reCAPTCHA：从地球观测数据中众筹大量地理信息”, International Journal of Applied Earth Observation and Geoinformation, vol.40, pp.29–38, 2015 年 8 月。
- [2] Carsten Kebler, Carson J. Q. Farmer, “通过时空地理在 Web of Data 上查询和集成空间-时间信息”, Web Semantics: Science, Services and Agents on the World Wide Web, vol.35, Part 1, pp. 25–34, 2015 年 12 月。
- [3] Jizhe Xia, Chaowei Yang, Qingquan Li, “利用时空模式优化地球观测大数据访问：索引、服务建模和云计算的新方法”, Environment and Urban Systems, 2018 年 8 月。
- [4] Xingjian Lu, Dongxu Jiang, Gaoqi He, Huiqun Yu, “GreenBDT：面向地理分布式可持续数据中心的可再生能源感知批量数据传输调度”, Sustainable Computing: Informatics and Systems, 2018 年 7 月。
- [5] Rachsuda Jiamthapthaksin, Christoph F. Eck 和 Seungchan Lee, “GAC-GEO：面向地理引用数据集的通用凝聚聚类框架”, Knowledge and Information Systems, vol.29, no.3, pp.597-628, 2011 年 12 月。
- [6] Lavika Goel, Mallikarjun Swamy 和 Raghav Mantri, “面向地理空间特征提取的基于蜂群和人工免疫系统的智能技术”, Proceedings of International Conference on Computational Intelligence and Data Engineering, pp 65–84, 2017 年 12 月。
- [7] Xuan Shi, “利用图形处理单元对大地理空间数据进行空间聚类分析的亲和传播并行化”, Advances in Geocomputation, pp 355–369, 2017 年 1 月。
- [8] Rabindra K. Barik, Ankita Tripathi, Harishchandra Dubey, Rakesh K. Lenka, Tanjappa Pratk 和 Suraj Sharma, “MistGIS：使用雾计算优化地理空间数据分析”, Progress in Computing, Analytics and Networking, pp 733–742, 2018 年 4 月。
- [9] Songnian Li, Suzana Dragicevic, Francesc Antón Castro, Monika Sester 和 Tao Cheng, “地理空间大数据处理理论与方法：综述与研究挑战 ISPRS”, Journal of Photogrammetry and Remote Sensing, vol.115, pp.119–133, 2016 年 5 月。
- [10] Hua-Dong Guo, Li Zhang, Lan-Wei Zhu, “用于气候变化研究的地球观测大数据”, Advances in Climate Change Research, vol.6, no.2, 108–117, 2015 年 6 月。
- [11] Gyozo Jordann 和 JRC PECOMINES 项目, “可持续矿产资源管理：从区域矿产资源勘探到矿业空间污染风险评估”, Environmental Geology, 2009 年 7 月。
- [12] Mudabber Ashfaq, Ali Tahir, Faisal Moeen Orakzai, Gavin McArdle 和 Michela Bertolott, “使用 T-Drive 和 BerlinMod 在并行 SECONDO 中进行地理空间大数据处理性能评估”, Spatial Data Handling in Big Data Era, pp 3–19, 2017 年 5 月。
- [13] Jae-Gil Lee, Minseo Kang, “地理空间大数据：挑战与机遇”, Big Data Research, vol.2, no.2, pp.78-81, 2015 年 6 月。
- [14] Mazin Alkhathiri, Jhummarawala Abdul 和 M.B. Potdar, “地理空间大数据挖掘技术”, International Journal of Computer Applications, vol.135, no.11, 2016 年 2 月。
- [15] H. Sun, X. Sun, H. Wang, Y. Li 和 X. Li, “基于空间稀疏编码词袋模型的高分辨率遥感图像自动目标检测,” in IEEE Geoscience and Remote Sensing Letters, vol. 9, no. 1, pp. 109–113, 2012 年 1 月。
- [16] Y. Li, X. Sun, H. Wang, H. Sun 和 X. Li, “基于轮廓的空间模型的高分辨率遥感图像自动目标检测,” in IEEE Geoscience and Remote Sensing Letters, vol. 9, no. 5, pp. 886–890, 2012 年 9 月。
- [17] L. Wan, T. Zhang, Y. Xiang 和 H. You, “基于贝叶斯非局部空间信息的鲁棒模糊 C-Means 算法用于 SAR 图像分割,” in IEEE Journal of Selected Topics in Applied Earth Observations and Remote Sensing, vol. 11, no. 3, pp. 896–906, 2018 年 3 月。
- [18] K. Chen, K. Fu, M. Yan, X. Gao, X. Sun 和 X. Wei, “带有混淆卷积神经网络的航空图像语义分割”, in IEEE Geoscience and Remote Sensing Letters, vol. 15, no. 2, pp. 173–177, 2018 年 2 月。
- [19] S. Chen 等人, “从稀疏采样的地理标记社交媒体数据中交互式可视化发现移动模式”, in IEEE Transactions on Visualization and Computer Graphics, vol. 22, no. 1, pp. 270–279, 2016 年 1 月 31 日。
- [20] S. Zhang, J. Li, H. Li, C. Deng 和 A. Plaza, “高光谱图像 unmixing 的光谱-空间加权稀疏回归”, in IEEE Transactions on Geoscience and Remote Sensing, vol. 56, no. 6, pp. 3265–3276, 2018 年 6 月。
- [21] Z. Li, Z. Liu 和 W. Shi, “面向高空间分辨率全色图像的建筑物屋顶识别快速水平集算法,” in IEEE Geoscience and Remote Sensing Letters, vol. 11, no. 4, pp. 743–747, 2014 年 4 月。
- [22] J. Li, M. Khodadadzadeh, A. Plaza, X. Jia 和 J. M. Bioucas-Dias, “光谱-空间高光谱图像分类的保持不连续性松弛方案,” in IEEE Journal of Selected Topics in Applied Earth Observations and Remote Sensing, vol. 9, no. 2, pp. 625–639, 2016 年 2 月。
- [23] Yara Rizk, Nadine Hajj, Nicholas Mitri, Mariette Awad, “深度置信网络与皮层算法：面向监督分类的比较研究”, Applied Computing and Informatics, 2018 年 3 月。
- [24] A. Y. Abdelaziz, E. S. Ali, S. M. Abd Elazim, “花粉传播算法用于求解联合经济与调度问题”, Engineering Science And Technology, an International Journal, vol.19, no.2, pp. 980–990, 2016 年 6 月。

