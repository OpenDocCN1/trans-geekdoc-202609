

## 表4.3 Pixel1手机上的汇总结果（Cai等，2020a）。第一组对应人工设计的CNN模型。第二组对应传统NAS。第三组对应硬件感知NAS。最后一组对应OFA。“#75”表示专用子网络从OFA网络获取权重后进行了75个时期的微调。“CO2e”表示基于(Strubell等，2019)计算的CO2排放量。AWS成本基于Amazon AWS按需P3.16x large实例的价格计算。

| 网络 | ImageNet Top1 (%) | MACs | 移动端延迟 | 搜索成本（GPU小时） | 训练成本（GPU小时） | GPU小时 | CO2e（磅） | AWS成本 |
|---|---|---|---|---|---|---|---|---|
| MobileNetV2 (Sandler et al., 2018) | 72.0 | 300M | 66 ms | 0 | 150× | 6k | 1.7k | $18.4k |
| MobileNetV2 #1200 | 73.5 | 300M | 66 ms | 0 | 1200× | 48k | 13.6k | $146.9k |
| NASNet-A (Zoph et al., 2017) | 74.0 | 564M | – | 48,000× | – | 1920k | 544.5k | $5875.2k |
| DARTS (Liu et al., 2018b) | 73.1 | 595M | – | 96× | 250× | 14k | 4.0k | $42.8k |
| MnasNet (Tan et al., 2018) | 74.0 | 317M | 70 ms | 40,000× | – | 1600k | 453.8k | $4896.0k |
| FBNet-C (Wu et al., 2019) | 74.9 | 375M | – | 216× | 360× | 23k | 6.5k | $70.4k |
| ProxylessNAS (Cai et al., 2019) | 74.6 | 320M | 71 ms | 200× | 300× | 20k | 5.7k | $61.2k |
| SinglePathNAS (Guo et al., 2019) | 74.7 | 328M | – | 288 + 24× | 384× | 17k | 4.8k | $52.0k |
| AutoSlim (Yu and Autoslim, 2019) | 74.2 | 305M | 63 ms | 180 | 300× | 12k | 3.4k | $36.7k |
| MobileNetV3-Large (Howard et al., 2019) | 75.2 | 219M | 58 ms | – | 180× | 7.2k | 1.8k | $22.2k |
| OFA | 76.0 | 230M | 58 ms | 40 | 1200 | 1.2k | 0.34k | $3.7k |
| OFA #75 | 76.9 | 230M | 58 ms | 40 | 1200 + 75× | 4.2k | 1.2k | $13.0k |
| OFA_Large #75 | 80.0 | 595M | – | 40 | 1200 + 75× | 4.2k | 1.2k | $13.0k |

Lebedev, Vadim, Ganin, Yaroslav, Rakhuba, Maksim, Oseledets, Ivan, Lempitsky, Victor, 2014. 使用微调CP分解加速卷积神经网络. arXiv预印本. arXiv:1412.6553.

Lebedev, Vadim, Lempitsky, Victor, 2016. 使用分组脑损伤的快速卷积网络. 载于：IEEE计算机视觉与模式识别会议论文集，第2554–2564页.

LeCun, Yann, Cortes, Corinna, Burges, Christopher JC, 2010. Mnist手写数字数据库. AT&T实验室 [在线]. 可访问：http://yann.lecun.com/exdb/mnist.

LeCun, Yann, Denker, John S., Solla, Sara A., Howard, Richard E., Jackel, Lawrence D., 1989. 最优脑损伤. 载于：NIPS，第2卷，第598–605页.

Li, Fengfu, Zhang, Bo, Liu, Bin, 2016a. 三值权重网络. arXiv预印本. arXiv:1605.04711.

Li, Hao, Kadav, Asim, Durdanovic, Igor, Samet, Hanan, Graf, Hans Peter, 2016b. 高效卷积网络的滤波器剪枝. arXiv预印本. arXiv:1608.08710.

Li, Muyang, Lin, Ji, Ding, Yaoyao, Liu, Zhijian, Zhu, Jun-Yan, Han, Song, 2020. GAN压缩：用于交互式条件GAN的高效架构. 载于：IEEE/CVF计算机视觉与模式识别会议论文集，第5284–5294页.

Lillicrap, Timothy P., Hunt, Jonathan J., Pritzel, Alexander, Heess, Nicolas, Erez, Tom, Tassa, Yuval, Silver, David, Wierstra, Daan, 2015. 基于深度强化学习的连续控制. arXiv预印本. arXiv:1509.02971.

Lin, Ji, Rao, Yongming, Lu, Jiwen, 2017. 运行时神经剪枝. 载于：NeurIPS.

Lin, Zhouhan, Courbariaux, Matthieu, Memisevic, Roland, Bengio, Yoshua, 2015. 少乘法神经网络. arXiv预印本. arXiv:1510.03009.

Liu, Chenxi, Chen, Liang-Chieh, Schroff, Florian, Adam, Hartwig, Hua, Wei, Yuille, Alan L., Li, Fei-Fei, 2019. 用于语义图像分割的分层神经架构搜索. 载于：IEEE计算机视觉与模式识别会议论文集，第82–92页.

Liu, Chenxi, Zoph, Barret, Neumann, Maxim, Shlens, Jonathon, Hua, Wei, Li, Li-Jia, Li, Fei-Fei, Yuille, Alan, Huang, Jonathan, Murphy, Kevin, 2018. 渐进式神经架构搜索. 载于：欧洲计算机视觉会议（ECCV）论文集，第19–34页.

Liu, Chenxi, Zoph, Barret, Shlens, Jonathon, Li, Li-Jia, Li, Fei-Fei, Yuille, Alan, Huang, Jonathan, Murphy, Kevin, 2017. 渐进式神经架构搜索. arXiv预印本. arXiv:1712.00559.

Liu, Hanxiao, Simonyan, Karen, Vinyals, Oriol, Fernando, Chrisantha, Kavukcuoglu, Koray, 2018a. 高效架构搜索的层次化表示. 载于：ICLR.

Liu, Hanxiao, Simonyan, Karen, Yang, Yiming, 2018b. 可微分架构搜索. arXiv预印本. arXiv:1806.09055.

Liu, Yifan, Chen, Ke, Liu, Chris, Qin, Zengchang, Luo, Zhenbo, Wang, Jingdong, 2019a. 用于语义分割的结构化知识蒸馏. 载于：IEEE计算机视觉与模式识别会议论文集，第2604–2613页.

Liu, Zechun, Mu, Haoyuan, Zhang, Xiangyu, Guo, Zichao, Yang, Xin, Cheng, Kwang-Ting, Sun, Jian, 2019b. 用于自动神经网络通道剪枝的元学习. 载于：IEEE国际计算机视觉会议论文集，第3296–3305页.

Ma, Ningning, Zhang, Xiangyu, Zheng, Hai-Tao, Sun, Jian, 2018. ShuffleNet V2：高效CNN架构设计的实用指南. 载于：ECCV.

Ma, Xiaolong, Guo, Wei, Niu, Fu-Ming, Lin, Xue, Tang, Jian, Ma, Kaisheng, Ren, Bin, Wang, Yanzhi, 2020. DNN权重剪枝中缺失但理想的稀疏性用于移动设备实时执行. 载于：AAAI，第5117–5124页.

Mao, Huizi, Han, Song, Pool, Jeff, Li, Wenshuo, Liu, Xingyu, Wang, Yu, Dally, William J., 2017. 探索卷积神经网络中稀疏性的粒度. 载于：IEEE计算机视觉与模式识别研讨会会议论文集，第13–20页.

Molchanov, Pavlo, Tyree, Stephen, Karras, Tero, Aila, Timo, Kautz, Jan, 2016. 为资源高效迁移学习剪枝卷积神经网络. CoRR. arXiv:1611.06440 [abs].

Molchanov, Pavlo, Tyree, Stephen, Karras, Tero, Aila, Timo, Kautz, Jan, 2017. 为资源高效迁移学习剪枝卷积神经网络. 载于：国际学习表征会议.

Nagel, Markus, van Baalen, Mart, Blankevoort, Tijmen, Welling, Max, 2019. 通过权重均衡和偏置校正进行无数据量化. 载于：IEEE国际计算机视觉会议论文集，第1325–1334页.

Niu, Wei, Ma, Xiaolong, Lin, Sheng, Wang, Shihao, Qian, Xuehai, Lin, Xue, Wang, Yanzhi, Ren, Bin, 2020. 通过基于模式的权重剪枝实现移动设备上的实时DNN执行. 载于：第25届编程语言和操作系统架构支持国际会议论文集，第907–922页.

Pham, Hieu, Guan, Melody Y., Zoph, Barret, Le, Quoc V., Dean, Jeff, 2018. 通过参数共享的高效神经架构搜索. 载于：ICML.

Ramachandran, Prajit, Zoph, Barret, Le, Quoc V., 2017. 搜索激活函数. arXiv预印本. arXiv:1710.05941.

Rastegari, Mohammad, Ordonez, Vicente, Redmon, Joseph, Farhadi, Ali, 2016. 使用二值卷积神经网络的ImageNet分类. 载于：欧洲计算机视觉会议. Springer，第525–542页.

Real, Esteban, Aggarwal, Alok, Huang, Yining, Le, Quoc V., 2018. 用于图像分类器架构搜索的正则化进化. arXiv预印本. arXiv:1802.01548.

Romero, Adriana, Ballas, Nicolas, Ebrahimi Kahou, Samira, Chassang, Antoine, Gatta, Carlo, Bengio, Yoshua, 2014. FitNets：轻薄深度网络的提示. arXiv预印本. arXiv:1412.6550.

Sandler, Mark, Howard, Andrew, Zhu, Menglong, Zhmoginov, Andrey, Chen, Liang-Chieh, 2018. MobileNetV2：反向残差与线性瓶颈. 载于：IEEE计算机视觉与模式识别会议论文集，第4510–4520页.

Sanh, Victor, Debut, Lysandre, Chaumond, Julien, Wolf, Thomas, 2019. DistilBERT，BERT的蒸馏版本：更小、更快、更便宜、更轻量. arXiv预印本. arXiv:1910.01108.

Sharify, Sayeh, Delmas Lascorz, Alberto, Siu, Kevin, Judd, Patrick, Moshovos, Andreas, 2018. 利用权重和激活精度加速卷积神经网络. 载于：DAC.

Sharma, Hardik, Park, Jongse, Suda, Naveen, Lai, Liangzhen, Chau, Benson, Chindada, Vikas, Esmailzadeh, Hadi, 2018. 位融合：用于加速深度神经网络的位级动态可组合架构. 载于：第45届国际计算机体系结构年会论文集. IEEE出版社，第764–775页.

Simonyan, Karen, Zisserman, Andrew, 2014. 用于大规模图像识别的极深卷积网络. arXiv预印本. arXiv:1409.1556.

Srinivas, Suraj, Babu, R. Venkatesh, 2015. 用于深度神经网络的无数据参数剪枝. arXiv预印本. arXiv:1507.06149.

Strubell, Emma, Ganesh, Ananya, Mccallum, Andrew, 2019. NLP中深度学习的能源与政策考量. 载于：ACL.

Szegedy, Christian, Liu, Wei, Jia, Yangqing, Sermanet, Pierre, Reed, Scott, Anguelov, Dragomir, Erhan, Dumitru, Vanhoucke, Vincent, Rabinovich, Andrew, 2015. 用卷积进行更深层次的学习. 载于：IEEE计算机视觉与模式识别会议论文集，第1–9页.

Szegedy, Christian, Vanhoucke, Vincent, Ioffe, Sergey, Shlens, Jon, Wojna, Zbigniew, 2016. 重新思考计算机视觉的Inception架构. 载于：CVPR.

Tan, Mingxing, Chen, Bo, Pang, Ruoming, Vasudevan, Vijay, Le, Quoc V., 2018. 面向移动设备的平台感知神经架构搜索. arXiv预印本. arXiv:1807.11626.

Tan, Mingxing, Pang, Ruoming, Le, Quoc V., 2020a. 可扩展且高效的目标检测. 载于：IEEE/CVF计算机视觉与模式识别会议论文集，第10781–10790页.

Tan, Zhanhong, Song, Jiebo, Ma, Xiaolong, Tan, Sia-Huat, Chen, Hongyang, Miao, Yuqing, Wu, Yifu, Ye, Shaokai, Wang, Yanxi, Li, Dehui, et al., 2020b. PCN：基于模式的细粒度规则剪枝以优化CNN加速器. arXiv预印本. arXiv:2002.04997.

Ummuroglu, Yaman, Rasnayake, Lahiru, Sjölinder, Magnus, 2018. 用于可重构计算的可扩展位串行矩阵乘法叠加. 载于：FPL.

Vanhoucke, Vincent, Senior, Andrew, Mao, Mark Z., 2011. 提高CPU上神经网络的速度. 载于：Proc. 深度学习与无监督特征学习NIPS研讨会. 载于：Citeseer，第1卷，第4页.

Wang, Kuan, Liu, Zhijian, Lin, Yujun, Lin, Ji, Han, Song, 2018. 硬件感知的自动量化. arXiv预印本. arXiv:1811.08886.

Wen, Wei, Wu, Chunpeng, Wang, Yandan, Chen, Yiran, Li, Hai, 2016. 学习深度神经网络中的结构化稀疏性. 载于：神经信息处理系统进展，第2074–2082页.

Wu, Bichen, Dai, Xiaoliang, Zhang, Peizhao, Wang, Yanghan, Sun, Fei, Wu, Yiming, Tian, Yuandong, Vajda, Peter, Jia, Yangqing, Keutzer, Kurt, 2019. 通过可微分神经架构搜索实现硬件感知的高效卷积网络设计. 载于：IEEE计算机视觉与模式识别会议论文集，第10734–10742页.

