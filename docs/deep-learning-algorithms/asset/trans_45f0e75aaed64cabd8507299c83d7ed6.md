

## 优化算法

在模型优化中，梯度下降优化器通过调整数值来帮助使模型代价最小；选择优化器也是一项具有挑战性的任务，因为有时它会使您的模型代价升高，而不是降低模型代价。

## 损失函数

从名称来看，损失函数用于估计预期结果与实际结果之间的损失或差异。损失函数的公式如下。

Loss = 预期结果 - 实际结果 (1)

计算损失函数有多种不同的方法；选择损失函数也是深度学习中重要且具有挑战性的任务之一。

## 激活函数

存在多种不同的激活函数；每种激活函数产生的结果不相同；Sigmoid 激活函数在二分类问题中表现良好。需要小心 Tanh 激活函数，因为存在梯度消失问题。在多标签分类中，softmax 是最佳选择；当输入侧有许多零时应使用 Relu，因为 Relu 擅长产生死神经元。使用所需的激活函数也是一个需要注意的点。

## 轮次（Epoch）

当数据集在整个神经网络中前向和后向传递时，称为一个轮次（epoch），因为在每个轮次之后会分析分配的权重值来构建模型。权重在每个周期中针对相同的数据集模拟被更改、检查和测试。主内存保存所有训练数据的记录；有时无法将所有记录保存在主内存中，例如对于较大的数据集，因此轮次以分段或批次形式加载到内存中，最后结果表示为轮次输出。处理轮次也是深度学习中一项具有挑战性的任务。

## 可用开源数据集

机器学习和深度学习的研究始于数十年前，为社会带来了显著的进步，涉及基于深度学习和机器学习的各种应用。网上有许多免费可用的数据集，研究人员可出于各种目的使用。

Image datasets (Table 1):

### Table 1. 开源图像数据集

| Pascal VOC | MS COCO |
| :--- | :--- |
| MNIST 手写数字 | NORB |
| CIFAR10/CIFAR100 彩色图像数据集 | COIL100 |
| Caltech101 | Google 开放图像 |
| Caltech 256 | COIL 20 |
| 街景数据集 | LabelMe |
| STL-10 | ImageNet |

Geospatial datasets available online:

- NEXRAD
- OpenstreetMAP
- Landsat8

Dataset available for text (Table 2):

### Table 2. 文本开源数据集

| Google 图书 Ngrams | Yelp 开放数据集 | 20 新闻组 | |
|---|---|---|---|
| UCI 的 Spambase（旧版） | 预测 | UCI 机器学习库 | 文本分类数据集 |
| SQuAD | Google 图书 Ngrams | 广播新闻 | WikiText |
| Penn Treebank | Reuters 新闻数据集 | 亿级词汇数据集： | Common crawl |

Artificial datasets:

- Arcade Universe
- 受 baby-AIschool 启发的数据集
- 所有图像和问题数据集
- Deep vs. shallow 比较 ICML
- 背景相关性
- 矩形数据
- Mnist 变体

Facial datasets (Table 3):

### Table 3. 面部识别数据库

| 自然界中的标注面孔 | UMD 面部标注数据集 | CASIA WebFace 面部 |
|---|---|---|
| MS-Celeb-1M | Olivetti | Multi-Pie |
| JACFEE | FERET | MMI 面部数据库 |
| 印度面部数据库 | Yale 面部数据库 | Mutiny 面部/头部分割数据集 |

Recent additions of datasets (Table 4):

### Table 4. 最近开发的免费数据库

| UZH-FPV 无人机竞赛数据集 | 朝鲜导弹测试数据库 | Flickr-Faces-HQ 数据集 (FFHQ) |
|---|---|---|
| Hotels-50K | MIMIC-CXR | Google Audioset |
| 两个新的评估数据集 | 开源生物特征数据识别 | Uber 2B 行程数据 |
| Yelp 开放数据集 | Core50 | 数据门户 |
| 开放数据监控 | Quandl 数据门户 | Mutiny 面部/头部分割数据集 |
| Awesome 公共数据集 | 头部 CT 扫描数据集 | 开放数据集 |
| WAPo | 棋类数据集 | NLP 数据集 |

## 参考文献

- 1. Aliper A, Plis S, Artemov A, Ulloa A, Mamoshina P, Zhavoronkov A. 用于预测药物药理特性和基于转录组数据的药物重新定位的深度学习应用. Molecular Pharmaceutics. 2016;13(7):2524-2530

- 2. 世界卫生组织. 道路安全全球状况报告. Available from: https://www.who.int/violence_injury_prevention/road_safety_status/2018/en/ [Accessed: 31 January 2018]

- 3. 美国交通部. 国家机动车辆事故原因调查中调查的事故关键原因. Washington, DC: National Center for Statistics and Analysis; 2015

- 5. Zhao Z-Q, Zheng P, Xu S-T, Wu X. 基于深度学习的目标检测：综述. IEEE Transactions on Neural Networks and Learning Systems. 2019;30(11):3212-3232

- 6. Kobatake H, Yoshinaga Y. 基于骨架分析的乳腺X线片中毛刺检测. IEEE Transactions on Medical Imaging. 1996;15(3):235-245

- 7. 2020 年值得关注的 3 大企业科技趋势. 2020. Available from: https://www.computerworld.com/article/3512109/top-3-enterprise-techtrends-to-watch-in-2020.html

- 8. Zhong S, Hu J, Fan X, Yu X, Zhang H. 结合分子指纹的深度神经网络 (DNN-MF) 用于开发水污染物羟基自由基速率常数的预测模型. Journal of Hazardous Materials. 2020;383(5)

- 10. Kong J, Huang J, Yu H, Deng H, Gong J, Chen H. 基于 RNN 的城市环境路径规划默认逻辑. Neurocomputing. 2019;338:307-320

- 11. Zhang Z, Zheng L, Wang M. 用于求解时变矩阵逆的指数增强型变参数 RNN. Neurocomputing. 2019;338:126-138

- 12. Konstantinidis D, Argyriou V, Stathaki T. 用于遥感图像的模块化基于 CNN 的建筑物探测器. Computer Networks. 2020;138:107034

- 14. Karpagavalli S, Chandra EH. 自动语音识别架构和方法综述. International Journal of Signal Processing, Image Processing and Pattern Recognition. 2016;9(4):393-404

- 15. Jin L, Liang H. 小样本情况下水下图像识别的深度学习. Aberdeen UK: OCEANS; 2017

- 16. Jozefowicz R, Vinyals O, Schuster M, Shazeer N, Wu Y. 探索语言建模的极限. California, USA: Google Brain; 2016

- 17. Wu CS, Madotto A, Hosseini-Asl E, Xiong C, Socher R, Fung P. 用于面向任务的对话系统的可转换多域状态生成器. In: arXiv preprint arXiv; 2019

- 19. Zamini M, Montazer G. 基于自动编码器聚类的信用卡欺诈检测. In: 第 9 届电信国际研讨会 (IST). Tehran, Iran; 2018. pp. 486-491

- 20. Mubalaike AM, Adali E. 智能金融欺诈检测系统的深度学习方法. In: 第 3 届计算机科学与工程国际会议 (UBMK). Sarajevo, Bosnia; 2018

- 21. Vidanelag HMMH, Tasnavijitvong T, Suwimonsatein P, Meesad P. 使用传统工具进行支付欺诈检测的机器学习技术研究. In: 第 11 届信息技术与电气工程国际会议 (ICITEE). Pattaya, Thailand; 2019

- 22. Subiksha K. 使用深度学习架构改进医疗保健系统分析. In: 第 4 届计算通信与自动化国际会议 (ICCCA). Greater Noida, India; 2018

- 23. Hajjo R. 在癌症护理中应用机器学习和人工智能面临的伦理挑战. In: 第 1 届癌症护理信息学国际会议 (CCI). Amman, Jordan; 2018

- 24. Nugroho H, Harmanto D, Hassan Al-Absi HR. 智能家庭护理的发展：用于疼痛检测的深度学习应用. In: IEEE-EMBS 生物医学工程与科学会议 (IECBES). Sarawak, Malaysia; 2018

- 25. Shickel B, Tighe PJ, Bihorac A, Rashidi P. Deep EHR：电子健康记录 (EHR) 分析深度学习技术最新进展综述. IEEE Journal of Biomedical and Health Informatics. 2017;22(5):1589-1604

