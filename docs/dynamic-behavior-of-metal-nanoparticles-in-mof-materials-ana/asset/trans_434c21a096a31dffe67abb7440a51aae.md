
关于输入数据的质量。通过去噪处理，即应用一组数字滤波器，可以显著提高后续二值化阶段的工作质量。

为获得最佳性能，针对所检查的特定类型视频需要单独的滤波器设置。然而，通过启发式方法，建立了一套有效的参数组合，以满足后续阶段使用U-Net卷积神经网络的需求。这使得该方法及所开发软件整体的灵活性得以提高。在此，采用了以下经典数字滤波器序列：

- (1) 非局部均值滤波器；
- (2) 双边滤波器；
- (3) 中值滤波器；
- (4) 高斯滤波器。

**二值化**用于提高视频流帧上图像的对比度，从而为下一阶段输入数据分割问题的成功求解创造条件。对于二值化，使用了卷积神经网络U-Net，84其显著特征是采用软最大值函数与交叉熵损失函数的组合。

![](img/277c1f92bfbf14a066f08b0c32f71acd_6_0.png)

在此，为实现反向传播算法，我们得出

![](img/277c1f92bfbf14a066f08b0c32f71acd_6_1.png)

类似方法已被广泛且有效地实现，用于在CUDA设备上为卷积神经网络提供推理。

所使用神经网络的训练样本基于研究样本形成，允许以相当好的灵活性处理同类型样本的数据，这提高了系统对输入数据变化的稳定性。

**分割**允许将二值化数据划分为具有区分特征的一组对象。获得的二值化数据经过基于图像拓扑结构分析方法的轮廓检测算法处理。这会生成一个对象列表，其中包含以参数形式描述的每个轮廓（生成点的坐标、矩、相对于其他轮廓的层级位置等）。生成的对象列表经过额外的后验过滤。因此，为了算法的进一步运行，仅使用参数位于给定值范围内的对象。允许的值范围通过启发式方法选择，考虑研究样本的类型以及视频流生成系统的参数（帧率、分辨率）。

为了便于跟踪任务，还采用了将对象划分为父对象和子对象组的方法。这消除了冗余计算，进而通过减少每帧的处理时间来提高系统性能。

跟踪是处理的最后阶段，它允许在图像中选择特定对象，并计算和跟踪空间和时间特性的变化。跟踪的任务是识别对象并计算指定的度量。识别算法包括查找相邻帧对象之间的相似度系数。跟踪模块处理的数据已预处理和过滤。因此，每个处理对象要么是需要分配其自身唯一索引的新对象，要么是先前识别过的对象，需要根据接收到的信息更新数据。

相似度系数基于一组给定的度量（重心坐标、面积、周长、密度和层级位置）计算为欧几里得距离。在计算中，仅获取参数位于指定值范围内的对象的数据。通过这种方式，具有异常数据的对象被过滤掉。例如，跟踪参数的变化率过高可能意味着新对象的出现，但相对于前一帧的对象，其相似度评分很高。

考虑到指定的值范围和所选的数据输出格式，跟踪模块生成检测和识别对象的列表，以及相应的计算特征。

## 利益冲突

没有需要声明的利益冲突。

## 致谢

作者谨感谢Vladimir V. Chernyshev科学博士（莫斯科国立大学，化学系）和Igor V. Mishin科学博士（谢列申卡有机化学研究所）获取PXRD图谱。作者谨感谢Igor V. Chistyakov博士利用SAED对ZIF-67样品进行表征并提供有益建议。该研究得到科学院NSh-5199.2022.1.3基金资助。HAADF-STEM研究使用“全国催化剂研究中心”共享知识中心的设备进行。MIL-53、NH2-MIL-53、MIL-101(Fe)、NH2-MIL-101(Fe)、NH2-MIL-101(Al)、BIF-66、ZIF-67、ZIF-8和HKUST-1的合成得到俄罗斯联邦科学与高等教育部资助，拨款编号075-15-2021-591。

## 注释和参考文献

- 1 Y. Zhao, C. Ye, W. Liu, R. Chen and X. Jiang, *Angew. Chem., Int. Ed.*, 2014, 53, 8127–8131.

- 2 Y. Ni, C. Kan and J. Xu, *Phys. Chem. Chem. Phys.*, 2022, 24, 21522–21537.

- 3 Y. Lu, Q. Hu, Y. Lin, D. B. Pacardo, C. Wang, W. Sun, F. S. Ligler, M. D. Dickey and Z. Gu, Nat. Commun., 2015, 6, 10066.

- 4 H. L. Reddy, J. L. Arias, J. Nicolas and P. Couvreur, Chem. Rev., 2012, 112, 5818–5878.

- 5 R. R. Arvizo, S. Bhattacharyya, R. A. Kudgus, K. Giri, R. Bhattacharya and P. Mukherjee, Chem. Soc. Rev., 2012, 41, 2943–2970.

- 6 J. Sun, L. He, Y.-C. Lo, T. Xu, H. Bi, L. Sun, Z. Zhang, S. X. Mao and J. Li, Nat. Mater., 2014, 13, 1007–1012.

- 7 L. Zhong, F. Sansoz, Y. He, C. Wang, Z. Zhang and S. X. Mao, Nat. Mater., 2017, 16, 439–445.

- 8 J. Wang, A. Ouvrard, W. Zheng, S. Carrez, A. Ghalgaoui and B. Bourguignon, Phys. Chem. Chem. Phys., 2023, 25, 10845–10852.

- 9 S. Zhang, X. Tan, Y. Zhou, J. Liu, X. Liang, X. Ding, G. Lyu, Y. Wei, J. Chen, Y. Mao, J. Wu, Y. Huang, Y. Huang, X. Tan and Z. Huang, Phys. Chem. Chem. Phys., 2022, 24, 6193–6207.

- 10 S. Guo, S. Zhang and S. Sun, Angew. Chem., Int. Ed., 2013, 52, 8526–8544.

- 11 D. E. Sanders and A. E. DePristo, Surf. Sci., 1992, 260, 116–128.

- 12 D. V. Wagle and G. A. Baker, Mater. Horiz., 2015, 2, 157–167.

- 13 P. M. Ajayan and L. D. Marks, Phys. Rev. Lett., 1988, 60, 585–587.

- 14 M. Takagi, J. Phys. Soc. Jpn., 1954, 9, 359–363.

- 15 S. B. Vendelbo, C. F. Elkjaer, H. Falsig, I. Puspitasari, P. Dona, L. Mele, B. Morana, B. J. Nelissen, R. van Rijn, J. F. Creemer, P. J. Kooyman and S. Helveg, Nat. Mater., 2014, 13, 884–890.

- 16 P. Grammatikopoulos, M. Sowwan and J. Kioseoglou, Adv. Theory Simul., 2019, 2, 1900013.

- 17 J. Li, J. Chen, H. Wang, N. Chen, Z. Wang, L. Guo and F. L. Deepak, Adv. Sci., 2018, 5, 1700992.

- 18 M. A. Asoro, D. Kovar and P. J. Ferreira, Chem. Commun., 2014, 50, 4835–4838.

- 19 Y. Liu and Y. Sun, Nanoscale, 2015, 7, 13687–13693.

- 20 J. M. Yuk, M. Jeong, S. Y. Kim, H. K. Seo, J. Kim and J. Y. Lee, Chem. Commun., 2013, 49, 11479–11481.

- 21 E. Z. da Silva, G. M. Faccin, T. R. Machado, N. G. Macedo, M. de Assis, S. Maya-Johnson, J. C. Sczancoski, J. Andrés, E. Longo and M. A. San-Miguel, J. Phys. Chem. C, 2019, 123, 11310–11318.

- 22 J. C. Sczancoski, S. Maya-Johnson, W. da Silva Pereira, E. Longo and E. R. Leite, Cryst. Growth Des., 2019, 19, 106–115.

- 23 H. Yasuda and H. Mori, Z. Phys. D, 1997, 40, 140–143.

- 24 P. S. Lemos, G. S. Silva, R. A. Roca, M. Assis, R. Torres-Mendieta, H. Beltran-Mir, G. Mínguez-Vega, E. Cordoncillo, J. Andres and E. Longo, Phys. Chem. Chem. Phys., 2019, 21, 6101–6111.

- 25 M. Jose-Yacaman, C. Gutierrez-Wing, M. Miki, D.-Q. Yang, K. N. Piyakis and E. Sacher, J. Phys. Chem. B, 2005, 109, 9703–9711.

- 26 J. Li, Z. Wang, Y. Li and F. L. Deepak, Adv. Sci., 2019, 6, 1802131.

- 27 Y. Ding, F. Fan, Z. Tian and Z. L. Wang, Small, 2009, 5, 2812–2815.

- 28 M. A. Asoro, D. Kovar and P. J. Ferreira, ACS nano, 2013, 7, 7844–7852.

- 29 K. Berlin and A. Trampert, J. Phys. Chem. C, 2018, 122, 2968–2974.

- 30 J. Buha, R. Gaspari, A. E. Del Rio Castillo, F. Bonaccorso and L. Manna, Nano Lett., 2016, 16, 4217–4223.

- 31 D. J. Hellebusch, K. Manthiram, B. J. Berberwyck and A. P. Alivisatos, J. Phys. Chem. Lett., 2015, 6, 605–611.

- 32 J. W. L. Yim, B. Xiang and J. Wu, J. Am. Chem. Soc., 2009, 131, 14526–14530.

- 33 Q. Yu, M. M. Mao, Q. J. Li, X. Q. Fu, H. Tian, J. X. Li, S. X. Mao and Z. Zhang, Nano Lett., 2016, 16, 1156–1160.

- 34 J.-G. Lee, J. Lee, T. Tanaka and H. Mori, Phys. Rev. Lett., 2006, 96, 075504.

- 35 C. Chen, Z. Hu, Y. Li, L. Liu, H. Mori and Z. Wang, Sci. Rep., 2016, 6, 19545.

- 36 A. S. Kashin and V. P. Ananikov, Nat. Rev. Chem., 2019, 3, 624–637.

- 37 Y. Zhang, D. Keller, M. D. Rossell and R. Erni, Chem. Mater., 2017, 29, 10518–10525.

- 38 S. R. Singh and L. D. Marks, Philos. Mag. Lett., 1989, 60, 31–36.

- 39 D. J. Smith, M. R. McCartney and L. A. Bursill, Ultramicroscopy, 1987, 23, 299–303.

- 40 T. Tsuda, T. Sakamoto, Y. Nishimura, S. Seino, A. Imanishi and S. Kuwabata, Chem. Commun., 2012, 48, 1925–1927.

- 41 J. Li and F. Deepak, Chem. Commun., 2020, 56, 4765–4768.

- 42 A. Markevich, S. Kurasch, O. Lehtinen, O. Reimer, X. Feng, K. Müllen, A. Turchanin, A. N. Khlobystov, U. Kaiser and E. Besley, Nanoscale, 2016, 8, 2711–2719.

- 43 K. L. Y. Fung, S. T. Skowron, R. Hayter, S. E. Mason, B. L. Ware, N. A. Besley, Q. M. Ramasse, C. S. Allen and A. N. Khlobystov, Phys. Chem. Chem. Phys., 2023, 25, 9092–9103.

- 44 H. Furukawa, K. E. Cordova, M. O’Keeffe and O. M. Yaghi, Science, 2013, 341, 1230444.

- 45 G. Cai, P. Yan, L. Zhang, H.-C. Zhou and H.-L. Jiang, Chem. Rev., 2021, 121, 12278–12326.

- 46 M. E. Zick, S. M. Pugh, J.-H. Lee, A. C. Forse and P. J. Milner, Angew. Chem., Int. Ed., 2022, 61, e202206718.

- 47 F. Gandara, H. Furukawa, K. Lee and O. M. Yaghi, J. Am. Chem. Soc., 2014, 136, 5271–5274.

- 48 J. D. Martell, P. J. Milner, R. L. Siegelman and J. R. Long, Chem. Sci., 2020, 11, 6457–6471.

- 49 L. Wen, K. Sun, X. Liu, W. Yang, L. Li and H.-L. Jiang, Adv. Mater., 2023, 35, 2210669.

- 50 R. Rajak, M. Saraf, P. Kumar, K. Natarajan and S. M. Mobin, Inorg. Chem., 2021, 60, 16986–16995.

- 51 Y. Zhang, L. Jiao, W. Yang, C. Xie and H.-L. Jiang, Angew. Chem., Int. Ed., 2021, 60, 7607–7611.

- 52 T. Zhang and W. Lin, Chem. Soc. Rev., 2014, 43, 5982–5993.
