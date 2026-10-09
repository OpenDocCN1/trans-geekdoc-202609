
## 5. 结论

关于表情分类的准确性。为了验证我们模型的有效性，在 KDEF 数据集上进行了消融实验。

为了将我们的模型与 LD-GAN 进行比较，我们从模型中移除了两个局部判别器。两个模型的归一化效果如图 17 所示。图 17a 展示了一个悲伤面庞男性的 $-90^{\circ}$ 视角侧脸，以及一个中性面庞女性的 $+45^{\circ}$ 视角侧脸。与图 17d 中的真实正脸相比，男性的嘴巴没有显示出应有的下垂，而图 17b 中女性的嘴巴在由未使用局部判别器的 GAN 生成的图像中显示出过度的上扬。这些错误增加了在后续面部表情识别（FER）步骤中，男性的悲伤表情被误分类为中性，以及女性的中性表情被误分类为开心的概率。在展示由 LD-GAN 生成面部的图 17c 中，受试者嘴角更接近真实正脸中的位置。

![](img/e4200cc4308edaf8913e513b0f96dbb6_305_0.png)

**图 17.** 两种模型之间面部归一化的比较。**（a）** 输入侧脸；**（b）** 由未使用局部判别器的 GAN 生成的面部；**（c）** 由 LD-GAN 生成的面部；**（d）** 真实正脸。

本文提出的轻量级 DSC-DenseNet 面部表情识别（FER）模型最小化了参数量并降低了计算复杂度，同时实现了有效的 FER 识别率。所提出的 LD-GAN 面部姿态归一化模型提高了保留与表情相关的局部特征的能力，并能生成更有利于 FER 的面部。在多个数据集上的实验表明，结合 LD-GAN 和 DSC-DenseNet 时，多视角面部的识别率高于 92%。

在 future 研究中，我们将研究不同光照环境和局部遮挡对我们模型的影响，并建立一种适用于自然场景的轻量级 FER 方法。

**作者贡献：** 概念化，J.D. 和 Y.Z.；方法，Y.Z.、J.D. 和 L.F.；软件、验证，Y.Z. 和 L.F.；撰写—审阅和编辑，J.D. 和 Y.Z.；监督，J.D. 所有作者均已阅读并同意发表版本的手稿。

**资助：** 本工作受中国国家自然科学基金资助，批准号 NSFC-61671190。

**数据可用性声明：** 本研究中提出的代码和数据可在 https://gittee.com/djw_Hrbut/fer.git（2023 年 6 月 1 日访问）获取。

**致谢：** 感谢李金阳和赵紫琪提出的宝贵意见和讨论。

**利益冲突：** 作者声明不存在利益冲突。

## 参考文献

- 1. Krizhevsky, A.; Sutskever, I.; Hinton, G.E. 使用深度卷积神经网络进行 ImageNet 分类. *Commun. ACM* **2017**, *60*, 84–90. [交叉引用]
- 2. Simonyan, K.; Zisserman, A. 用于大规模图像识别的非常深卷积网络. *Comput. Sci.* **2014**, *56*, 1–14.
- 3. Szegedy, C.; Liu, W.; Jia, Y. 通过卷积深入. 在 2015 年 6 月 7-12 日美国波士顿举行的 IEEE 计算机视觉与模式识别会议上.
- 4. He, K.; Zhang, X.; Ren, S.; Sun, J. 用于图像识别的深度残差学习. 在 2016 年 6 月 26 日至 7 月 1 日美国拉斯维加斯举行的 IEEE 计算机视觉与模式识别会议上.
- 5. Girshick, R.; Donahue, J.; Darrell, T.; Malik, J. 用于精确物体检测和语义分割的丰富特征层次结构. 在 2014 年 6 月 23-28 日美国哥伦布举行的 IEEE 计算机视觉与模式识别会议上.
- 6. Ren, S.; He, K.; Girshick, R.; Sun, J. Faster R-CNN：迈向使用区域提议网络实现实时物体检测. *IEEE Trans. Pattern Anal. Mach. Intell.* **2017**, *39*, 1137–1149. [交叉引用] [PubMed]
- 7. Yao, A.; Cai, D.; Hu, P. HoLoCon：迈向野外鲁棒情感识别. 在 2016 年 11 月 12-16 日日本东京举行的第 18 届 ACM 多媒体交互国际会议上.
- 8. Huang, G.; Liu, Z.; Van Der Maaten, L.; Weinberger, K.Q. 密集连接卷积网络. 在 2017 年 7 月 21-26 日美国檀香山举行的 IEEE 计算机视觉与模式识别会议上.
- 9. Iandola, F.N.; Han, S.; Mossewiz, M.W.; Ashraf, K.; Dally, W.J.; Keutzer, K. SqueezeNet：使用 50 倍更少的参数和 <0.5 MB 的模型大小达到 AlexNet 级别的准确性. 在 2017 年 4 月 24-26 日法国土伦举行的国际学习表征会议上.
- 10. Ma, N.; Zhang, X.; Zheng, H.-T.; Sun, J. Shufflenet V2：高效 CNN 架构设计的实用指南. 在 2018 年 9 月 8-14 日德国慕尼黑举行的欧洲计算机视觉会议上.
- 11. Shen, H.; Meng, Q.; Liu, Y. 通过合并轻量级卷积网络的多层特征进行面部表情识别. *Laser Optoelectron. Prog.* **2021**, *58*, 148–155.
- 12. Li, C.; Lu, Y. 基于深度可分离卷积的面部表情识别. *Comput. Eng. Des.* **2021**, *42*, 1448–1454.
- 13. Gao, J.; Cai, Y.; He, Z. TP-FFER：基于最优卷积神经网络三路径网络的面部表情识别方法. *Appl. Res. Comput.* **2021**, *38*, 7.
- 14. Liang, H.; Lei, Y. 使用可分离卷积通道增强特征的表情识别. *Comput. Eng. Appl.* **2022**, *58*, 184–192.
- 15. Zhang, P.; Kong, W.; Teng, J. 基于多尺度特征注意力机制的面部表情识别. *Comput. Eng. Appl.* **2022**, *58*, 182–189.
- 16. Han, Z. 不同面部姿态下的面部表情识别. 硕士学位论文，中国苏州大学，2020 年.
- 17. Goodfellow, I.; Pouget-Abadie, J.; Mirza, M.; Xu, B.; Warde-Farley, D.; Ozair, S.; Courville, A.; Bengio, Y. 生成对抗网络. 在 2014 年 12 月 8-11 日加拿大蒙特利尔举行的神经信息处理系统会议上.
- 18. Chollet, F. Xception：使用深度可分离卷积的深度学习. 在 2017 年 7 月 21-26 日美国檀香山举行的 IEEE 计算机视觉与模式识别会议上.
- 19. Howard, A.G.; Zhu, M.; Chen, B.; Kalenichenko, D.; Wang, W.; Weyand, T.; Andreetto, M.; Adam, H. Mobilenets：用于移动视觉应用的高效卷积神经网络. 在 2017 年 7 月 21-26 日美国檀香山举行的 IEEE 计算机视觉与模式识别会议上.
- 20. 生成对抗网络（GAN）. 在线可用：https://www.geeksforgeeks.org/generative-adversarial-network-gan/（2023 年 3 月 31 日访问）.
- 21. Huang, R.; Zhang, S.; Li, T.; He, R. 超越面部旋转：用于照片级真实感且保持身份的正脸合成的全局和局部感知 GAN. 在 2017 年 10 月 22-29 日意大利威尼斯举行的 IEEE 国际计算机视觉会议上.
- 22. Yin, X.; Yu, F.; Sohn, K.; Liu, X.; Chandraker, M. 迈向野外大姿态面部正面化. 在 2017 年 10 月 22-29 日意大利威尼斯举行的 IEEE 国际计算机视觉会议上.
- 23. Tran, L.; Yin, X.; Liu, X. 用于姿态不变面部识别的解耦表示学习 GAN. 在 2017 年 7 月 21-26 日美国檀香山举行的 IEEE 计算机视觉与模式识别会议上.
- 24. Hu, Y.; Wu, X.; Yu, B.; He, R.; Sun, Z. 姿态引导的照片级真实感面部旋转. 在 2018 年 6 月 18-22 日美国盐湖城举行的 IEEE 计算机视觉与模式识别会议上.
- 25. Hardy, C.; Le Merre, E.; Sericela, B. MD-GAN：用于分布式数据集的多判别器生成对抗网络. 在 2019 年 5 月 20-24 日巴西里约热内卢举行的 IEEE 国际并行与分布式处理研讨会上.
- 26. Lin, H.; Ma, H.; Gong, W.; Wang, C. 带有侧脸恢复生成对抗网络的非正脸识别方法. 在 2022 年 5 月 20-22 日中国长春举行的第 3 届国际计算机视觉、图像和深度学习会议上.
- 27. Izuka, S.; Sano-merra, E.; Ishikawa, H. 全局和局部一致的图像补全. *ACM Trans. Graph.* **2017**, *36*, 1–14. [交叉引用]
- 28. Sharma, A.K.; Foroush, H. Slim-CNN：用于面部属性预测的轻量级 CNN. 在 2020 年 5 月 18-22 日阿根廷布宜诺斯艾利斯举行的 IEEE 国际自动面部与手势识别会议上.
- 29. 扩展 Cohn-Kanade 数据集. 在线可用：http://www.pitt.edu/~emotio/ck-sa-explore.htm（2023 年 4 月 19 日访问）.
- 30. Kaggle FER 挑战数据集. 在线可用：https://www.kaggle.com/c/challenges-in-representation-learning-facial-expression-recognition-challenge/overview（2023 年 4 月 19 日访问）.
- 31. 卡罗林斯卡引导情绪面孔. 在线可用：http://www.emotiolnab.se/kdef（2023 年 4 月 19 日访问）.
- 32. Zhang, K.; Zhang, Z.; Li, Z.; Qiao, Y. 使用多尺度级联卷积网络进行联合面部检测和定位. *IEEE Signal Process. Lett.* **2017**, *23*, 1499–1503. [交叉引用]

