

### Table 9
拟模型与最先进的分割模型在基准性能指标上的比较分析。

| 模型 | IoU | 精确率 | 召回率 | F1-得分 |
|---|---|---|---|---|
| UNet | 0.88 | 0.87 | 0.86 | 0.86 |
| UNet ++ | 0.96 | 0.94 | 0.95 | 0.94 |
| D-UNet + Augmentation | 0.91 | 0.90 | 0.91 | 0.90 |
| WNet | 0.89 | 0.89 | 0.87 | 0.88 |
| VNet | 0.92 | 0.90 | 0.88 | 0.89 |
| Cascaded Network | 0.94 | 0.92 | 0.94 | 0.93 |
| Proposed Model | 0.96 | 0.94 | 0.94 | 0.94 |

研究。此次实验的局限性之一是基准模型的开源代码不可用。由于新引入模型的开源代码有限，其中一些最新模型可以在此工作中进行实验和比较。

未来，该模型可以通过采用其他预训练模型作为编码器和解码器的骨干网络，并结合注意力层和回归层，进一步提升 Dice 指标并减少分割区域与真值之间的头围差异。

## 6. 结论与未来工作

本文提出了一种新的编码器-解码器模型，融合了带回归层的注意力门机制，用于从2D超声图像中分割胎儿头部。拟议模型在编码和解码阶段采用密集块，以最大限度地减少与梯度下降相关的问题。必须使用密集块，因为在拟议模型中，软注意力门与跳跃连接一起用于最小化误差损失。这种软注意力基础是使用梯度的反向传播。

拟议模型用于对2D超声图像中的胎儿头部进行语义分割。随后，在椭圆拟合的帮助下对分割结果进行后处理，因为胎儿呈椭圆形。因此，合适的椭圆拟合有助于将分割结果映射到超声图像上。最后，进行胎儿尺寸分析，以估计胎儿的适当大小来检查其生长情况。采用拟议方法的结果分析有助于以高精度识别胎儿，其平均绝对头围差异为0.354 mm。

拟议模型在10,989张图像（数据增强后）的数据集上训练，并在335张图像的数据集上测试。测试数据集的平均绝对头围差异为0.387 mm。实验结果令人满意，因为该模型在使用不同统计性能指标进行实验时仍能达到最佳性能。除了头围分析外，本工作中使用的其他指标还包括Dice系数、平均绝对百分误差和豪斯多夫距离。使用拟议模型对这些指标的实验结果在训练数据上得到：Dice-97.31%、MAPE-0.65%、HD-1.09%。Dice-96.30%、MAPE-0.71%、HD-1.11%的准确结果。

除上述指标外，该模型的性能还在一些用于分割的其他基准指标上进行了评估，例如IoU、精确率、召回率和F1-分数。使用这些指标的实验也证明了该模型的有效性，所取得的值为：IoU-0.96、精确率-0.94、召回率-0.94、F1-分数-0.94。该模型还与一些用于不同领域对象分割的其他基准深度模型进行了比较，用于

### Author statement

Somya Srivastava: 概念化、方法论、撰写 - 原始草稿。
Ankit Vidyarathi: 监督、可视化、调查。
Shikha Jain: 审阅、结果验证、语言校正。

### Data availability

本文所述研究未使用任何数据。

### Declaration of Competing Interest

作者声明，没有已知的竞争性财务利益或个人关系可能影响本文报道的工作。

## References

- [1] Luciano Marcondes Machado Nardozza, Ana Carolina Rabachini Caetano, Ana Cristina Perez Zamarian, Jaqueline Brandão Mazzola, Carolina Pacheco Silva, Vivian Macedo Gomes Marçal, Thalita Frutuoso Lobo, Alberto Borges Peixoto, Edward Araújo Júnior, 胎儿生长受限：当前知识, Arch. Gynecol. Obstet. 295 (5) (2017) 1061–1077.
- [2] Ulrike Schmidt, Dunja Temerincath, Katharina Bildstein, Benjamin Tschuy, Jade Mayer, Mark Sittlner, Jörn Siemer, Sven Kehl, 测量胎儿头围以进行胎儿体重估计的最准确方法, Eur. J. Obstet. Gynecol. Reprod. Biol. 178 (2014) 153–156.
- [3] Hyunsook Seo, Masoud Badii Khuzaai, Varun Vasudevan, Charles Huang, Hongyi Ren, Ruoxiao Xiao, Jiao Jia, Lei Xing, 生物医学图像分割的机器学习技术：技术方面概述及最先进应用介绍, Med. Phys. 47 (5) (2020) e2148–e167.
- [4] Ankit Vidyarathi, Ankita Kansal, 数字图像分割算法调查报告, Int. J. Comp. Eng. Technol. (IJCET) 3 (2) (2012) 85–91.
- [5] Ankit Vidyarathi, Namita Mittal, 脑肿瘤分割方法：综述、分析及机器学习中的预期解决方案, 2015 9th National Systems Conference (NSC), IEEE 2015, pp. 1–6.
- [6] Shirwin Minaee, Yuri Y. Boykov, Fatih Porikli, Antonio J. Plaza, Nasser Kehtarnavaz, Demetri Terzopoulos, 基于深度学习的图像分割：综述, IEEE Transactions on Pattern Analysis and Machine Intelligence, 2021.
- [7] Hariharan Ravishankar, Sahana M. Prabhu, Vivek Vaidya, Nitin Singhal, 基于深度学习的超声图像中胎儿腹部自动分割的混合方法, 2016 IEEE 13th International Symposium on Biomedical Imaging (ISBI), IEEE 2016, pp. 779–782.
- [8] Lu Wei, Jinglu Tan, Randall Floyd, 基于迭代随机霍夫变换的超声图像中胎儿头部自动检测与测量, Ultrasound Med. Biol. 31 (7) (2005) 929–936.
- [9] Sandra M.G.V.B. Jardim, Mário A.T. Figueiredo, 胎儿超声图像分割, Ultrasound Med. Biol. 31 (2) (2005) 243–250.

### Table 10
使用超声图像 HC18 数据集的拟议模型与最新技术的比较分析。

| 参考 | 方法 | DC | DHC | 平均差异 | HC |
|---|---|---|---|---|---|
| Sobhaninia et al. [14] | Multi class Link Net | 96.84 ± 2.89 | 1.13 ± 2.69 | 2.12 ± 1.87 | 1.72±1.39 |
| Zeng et al. [24] | Optimized Deep Model | 97.61 ± 1.72 | - | 1.97 ± 1.89 | - |
| Heuvel et al. [25] | Haar 特征 + 带随机森林的霍夫变换 | 97.0±2.8 | 0.6 ± 4.3 | 2.8 ± 3.3 | 2.0 ± 1.6 |
| Rong et al. [26] | GVF-Net | 95.53 ± 3.98 | -0.24 ± 3.23 | 2.42 ± 1.93 | 2.18 ± 2.40 |
| Al-Bander et al. [27] | Mask R-CNN | 97.73±1.32 | 1.49±2.85 | 2.33±2.21 | 1.39±0.82 |
| Proposed Model | 回归-注意力 UNet | 97.31±1.47 | 0.304±1.26 | 1.87±1.21 | 1.09±0.77 |

- [10] Patricia García-Canadilla, Sergio Sanchez-Martinez, Fatima Crispi, Bart Bijnens, 胎儿心脏病学中的机器学习：可以期待什么, Fetal Diagn. Ther. 47 (5) (2020) 363–372.
- [11] Qinghua Huang, Fan Zhang, Xuelong Li, 超声计算机辅助诊断系统中的机器学习：综述, Biomed. Res. Int. 2018 (2018).
- [12] Stav Gofer, Oren Haiik, Ron Bardin, Gilboa Yinnon, Sharon Perelman, 第一孕期胎儿脑部超声图像分类的机器学习算法, J. Ultrasound Med. 41 (7) (2021) 1773–1779.
- [13] Mohammad Yaqub, Rami Cujgent, Raffaele Napolitano, David Roundhill, Aris Papageorghiou, Roberto Ardon, J. Alison, Noble, 3D超声中关键胎儿脑结构的体积分割, International Workshop on Machine Learning in Medical Imaging, Springer 2013, pp. 25–32.
- [14] Zahra Sohrabinia, Shima Rafiei, Ali Emami, Nader Karimi, Kayvan Najarian, Shadrokh Samavi, S.M. Reza, Soroushmehr, 使用多任务深度学习测量生物测量参数的胎儿超声图像分割, 2019 41st Annual International Conference of the IEEE Engineering in Medicine and Biology Society (EMBC), IEEE 2019, pp. 6545–6548.
- [15] Xu Xin Yang, Yi Wang Wang, Haoran Dou, Shengli Lu, Huaxuan Wen, Yi Lin, Peng-Ann Heng, Dong Ni, 产前超声体积中整个胎儿头部自动分割的混合注意力机制, Comput. Methods Prog. Biomed. 194 (2020) 105519.
- [16] Sylvia L. Rueda, Sana Fathima, Caroline L. Knight, Mohammad Yaqub, Aris T. Papageorghiou, Babii Rahmatullah, Alessandro Foi, Matteo Maggioni, Antonietta Pepe, Jussi Tohka, et al., 用于生物测量的当前胎儿超声图像分割方法的评估与比较：一项大挑战, IEEE Trans. Med. Imaging 33 (4) (2013) 797–813.
- [17] Netanell Avidsris, Bossmat Yehuda, Ori Ben-Zvi, Daphne Link-Sourani, Liat Ben-Sira, Elka Miller, Elena Zharkov, Dafna Ben Bashat, Leo Joskowicz, 基于深度神经网络的胎儿脑部MRI自动线性测量, Int. J. Comput. Assist. Radiol. Surg. 16 (9) (2021) 1481–1492.
- [18] Baihong Xie, Ting Lei, Nan Wang, Hongmin Cai, Jianbo Xian, Miao He, Lihe Zhang, Honqing Xie, 使用深度卷积神经网络的胎儿脑部超声图像计算机辅助诊断, Int. J. Comput. Assist. Radiol. Surg. 15 (8) (2020) 1303–1312.
- [19] Xavier P. Burgos-Artizzu, David Coronado-Gutiérrez, Brenda Valenzuela-Alcazar, Elisenda Bonet-Carne, Elisenda Eixarch, Fatima Crispi, Eduard Gratacós, 常见母体胎儿超声平面自动分类的深度卷积神经网络评估, Sci. Rep. 10 (1) (2020) 1–12.
- [20] Zahra Sohrabinia, Ali Emami, Nader Karimi, Shadrokh Samavi, 基于多尺度视图和深度神经网络的超声图像中胎儿头部定位, 2020 5th International Computer Conference, Computer Society of Iran (CSICC), IEEE 2020, pp. 1–5.
- [21] Abhishek Chaurasia, Eugenio Culurciello, LinkNet：利用编码器表示实现高效语义分割, 2017 IEEE Visual Communications and Image Processing (VCIP), IEEE 2017, pp. 1–4.
- [22] Mostafa Ghelchi Oghli, Shakiba Moradi, Nasim Sirjani, Reza Gerami, Payam Ghaderi, Al Shabanzadeh, Hossein Arabi, Isaac Shiri, Habib Zaidi, 使用深度神经网络从超声图像自动测量胎儿头部生物测量, IEEE Nuclear Science Symposium and Medical Imaging Conference (NSS/MIC), IEEE 2020, pp. 1–3.
- [23] Olaf Ronneberger, Philipp Fischer, Thomas Brox, U-Net：用于生物医学图像分割的卷积网络, International Conference on Medical Image Computing and Computer-Assisted Intervention, Springer 2015, pp. 234–241.
- [24] Zeng Wen, Jie Liu, Jiaru Cheng, Lu Yiling, 使用轻量级深度卷积神经网络进行自动心脏周长测量的高效胎儿超声图像分割, Med. Phys. 49 (8) (2022) 5081–5092.
- [25] Thomas L.A. van den Heuvel, Dagmar de Bruijn, Chris L. de Korte, Bram van Ginneken, 使用2D超声图像的胎儿头围自动测量, PLoS One 13 (8) (2018), e0200412.
- [26] Yibiao Rong, Dehui Xiang, Weifang Zhu, Fei Shi, Enting Gao, Zhun Fan, Xinjian Chen, 通过卷积神经网络推导生物医学图像分割的外部力, Biomed. Opt. Exp. 10 (8) (2019) 3800–3814.
- [27] Baidaa Al-Bander, Theib Al-Zbairri, Saeed Alzhrani, Bryan M. Williams, Yalin Zheng, 通过深度学习的对象定位改进胎儿头部轮廓分割, Annual Conference on Medical Image Understanding and Analysis, Springer 2019, pp. 142–150.

