
### 图 1.14 基于 Bendlet 和 SVM 的 SCC 系统框图。

### 表 1.3

**SCC 系统性能指标**

| 性能度量 | 描述 | 公式 |
| :--- | :--- | :--- |
| 敏感率 ($S_n$) | 它是正确预测的真正例数量与实际阳性病例总数之比。 | $S_n = \frac{T_r P_p}{T_r P_r + F_i N_e}$ |
| 特异率 ($S_p$) | 它是正确预测的真阴性数量与阴性病例总数之比。 | $S_p = \frac{T_r N_e}{T_r N_e + F_i P_r}$ |
| 准确率 ($A_c$) | 它定义为正确预测的皮肤癌图像数量占实际病例图像总数的比例。 | $A_c = \frac{T_r P_p + T_r N_e}{T_r P_p + F_i N_e + T_r N_e + F_i P_p}$ |

## 1.5 结论

本研究简要介绍了用于将皮肤镜图像分类为正常和异常图像的各种图像表示系统和分类技术。在工作 I 中，剪切变换和 K-NN 分类器在剪切分解第二层且拥有 100 个系数时给出了 96% 的最高准确率。在工作 II 中，使用 bendlet 变换进行特征提取和 SVM 进行分类，在级别 3 分解和方向 8 时给出了 98.3% 的最高准确率。最后，比较了所有图像表示系统，如小波、curvelet、轮廓、剪切和 bendlet，并测量了如特异性、

### 表 1.4

### 正常和异常相位的分类器性能

| 分解级别 | 方向数量 | $T_{r} P_{o}$ | $F_{a} N_{e}$ | $T_{r} N_{e}$ | $F_{a} P_{o}$ | $S_{n} (\%)$ | $S_{p} (\%)$ | $A_{c}(\%)$ |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| | | | | | | | | |
| 1 | 2 | 90 | 30 | 65 | 15 | 75.00 | 81.25 | 77.50 |
| | 4 | 94 | 26 | 67 | 13 | 78.33 | 83.75 | 80.50 |
| | 8 | 99 | 21 | 68 | 12 | 82.50 | 85.00 | 83.50 |
| | 16 | 94 | 26 | 68 | 12 | 78.33 | 85.00 | 81.00 |
| | 32 | 86 | 34 | 67 | 13 | 71.67 | 83.75 | 76.50 |
| 2 | 2 | 97 | 23 | 70 | 10 | 80.83 | 87.50 | 83.50 |
| | 4 | 102 | 18 | 72 | 8 | 85.00 | 90.00 | 87.00 |
| | 8 | 108 | 12 | 75 | 5 | 90.00 | 93.75 | 91.50 |
| | 16 | 100 | 20 | 71 | 9 | 83.33 | 88.75 | 85.50 |
| | 32 | 93 | 27 | 71 | 9 | 77.50 | 88.75 | 82.00 |
| 3 | 2 | 104 | 16 | 77 | 3 | 86.67 | 96.25 | 90.50 |
| | 4 | 110 | 10 | 79 | 1 | 91.67 | 98.75 | 94.50 |
| | 8 | **117** | **3** | **80** | **0** | **97.50** | **100.00** | **98.50** |
| | 16 | 109 | 11 | 77 | 3 | 90.83 | 96.25 | 93.00 |
| | 32 | 102 | 18 | 75 | 5 | 85.00 | 93.75 | 88.50 |
| 4 | 2 | 97 | 23 | 79 | 1 | 80.83 | 98.75 | 88.00 |
| | 4 | 108 | 12 | 79 | 1 | 90.00 | 98.75 | 93.50 |
| | 8 | 110 | 10 | 79 | 1 | 91.67 | 98.75 | 94.50 |
| | 16 | 104 | 16 | 79 | 1 | 86.67 | 98.75 | 91.50 |
| | 32 | 96 | 24 | 78 | 2 | 80.00 | 97.50 | 87.00 |

![](img/93c6e2919cb9917d1bdd8f6271e04df4_33_0.png)

### 图 1.15 各种图像表示技术的性能比较。

敏感率和准确率进行了测量。根据结果，我们得出结论：与其他所有图像表示系统相比，bendlet 提供了更好的准确率。小波表现最差，而轮廓比曲线或小波表现更好。

# 参考文献

- [1]. del Marmol V, lipira K, ‘2020 Skin cancer report- global cancer observatory’, 2020.
- [2]. Dengel LT, Petroni GR, Judge J, Chen D, Acton ST, Schroen AT, Slingsluff CL, ‘Total body photography for skin cancer screening’, International Journal of Dermatology, 54(11): ISSN:1365-4632, 1250-1254, 2015, Wiley.
- [3]. Srivastava A, Hughes B, Hughes L, Woodcock J, ‘Doppler ultrasound as an adjunct to the differential diagnosis of pigmented skin lesions’, British Journal of Surgery, 73: 790-792, ISSN: 1365-2168, 1986, John Wiley & Sons.
- [4]. Pehamberger H, Binder M, Steiner A, Wolff K, ‘In vivo epifluorescence microscopy: improvement of early diagnosis of melanoma’, Journal of Investigative Dermatology, 100(3), ISSN: 0022-202X1993, Elsevier.
- [5]. Banerjee I ‘Brain tumor image segmentation and classification using SVM, CLAHE AND ARKFCM’, Intelligent decision support systems, applications in signal processing, 978-3-11-062110-5, 53-70, October, 2019
- [6]. Banerjee I ‘IOT based fluid and heartbeat monitoring for advanced health care’, Classification techniques for medical image analysis and computer aied diagnosis volume 4 , ISBN: 978-0-12-818004-4, 2019 .
- [7]. Madhupathy P, Prasanath R, Srikleha ‘Eye movement detection for paralyzed patient using pressure sensor’, International Journal of Scientific & Engineering Research, 7(1): 395-397, November, 2016 ISSN 2229-5518.
- [8]. Sultana NN, Manda, B, Puhan NB, ‘Deep residual network with regularised fisher framework for detection of melanoma’, IET Computer Vision, 12(8): 1096-1104, ISSN 1751-8644, 2018, IET Digital Library.
- [9]. Sonia R et al., ‘Melanoma image classification system by NSCT features and Bayes classification’, International Journal of Advances in Signal and Image Sciences, 2(2): 27-33, -ISSN: 2457-0370, 2016.
- [10]. Zaquot I, ‘Diagnosis of skin lesions based on dermoscopic images using image processing techniques’, International Journal of Signal Processing, Image Processing and Pattern Recognition, 9(9): 189-204, ISSN: 20054254, 2207970X, 2016, Science and Engineering Support Society.
- [11]. Ma Z, Tavares JM, ‘Effective features to classify skin lesions in dermoscopic images’, Expert Systems with Applications, 84: 92-101, ISSN: 0957-4174, 2017, Elsevier.
- [12]. Ozkan IA, Koklu M, ‘Skin lesion classification using machine learning algorithms’, International Journal of Intelligent Systems and Applications in Engineering, 5(4), ISSN:2147-6799 285-289, 2017, Academic Publisher Science.
- [13]. Argenziano G, Catricalà C, Ardigo, et al. ‘Seven-point checklist of dermoscopy revisited’, British Journal of Dermatology, 164(4): 785-790, ISSN: 1365-2133, 2011, Wiley.
- [14]. Zalaudek I, Argenziano G, Soyer, H, et al. ‘Three-point checklist of dermoscopy: an open internet study’, British Journal of Dermatology, 154(3): 431-437, ISSN: 1365-2133, 2006, Wiley.
- [15]. Nasir M, Attique Khan M, Sharif M, Lali IU, Saba T, Iqbal T, ‘An improved strategy for skin lesion detection and classification using uniform segmentation and
- 基于特征选择的方法'，*显微研究和技术*，81(6):528–543，ISSN:1097-0029，2018，Wiley出版社。
- [16]。Sarkar R，Chatterjee CC，Hazra A，'基于深度可分离残差卷积网络从皮肤镜检查图像中诊断黑色素瘤'，*IET图像处理*，13(8): 2130–2142。ISSN: 350-245X，2019，IET数字图书馆。
- [17]。Jain YK，Jain M，'使用小波变换和概率神经网络进行皮肤癌检测和分类'，第四届通信与计算新技术进展国际会议，250-252，ISSN: 0975-8887，2012。
- [18]。Sertan S，Erdem FD，'基于小波的深度学习用于皮肤病灶分类'，*IET图像处理*，14(4): 720–726，ISSN: 1350-245X，2020。IET数字图书馆。
- [19]。Donoho D，Candes E，'连续Curvelet变换：II. 离散化和框架'，*应用和计算谐波分析*，19(2): 198–222，ISSN: 1063-5203，2005，Elsevier出版社。
- [20]。Esteva A，Kuprel B，Novoa RA，Ko J，Swetter SM，Blau HM，Thrun S. '使用深度神经网络实现皮肤科医生水平的皮肤癌分类'，*自然*，542(7639): 115–118，ISSN: 1476-4687，2015。
- [21]。Goyal M，Oakley A，Bansal P，Dancy D，Yap MH，'使用集成深度学习方法对皮肤镜检查图像中的皮肤病灶进行分割'，*IEEE Access*，8: 4171–4181，ISSN: 2169-3536，2019。
- [22]。Mallat, S，'小波信号处理之旅：稀疏方法'，学术出版社，美国，ISSN: 0362-4331，2008。
- [23]。Donoho D，Candes E，'连续Curvelet变换：II. 离散化和框架'，*应用和计算谐波分析*，19(2): 198–222，ISSN: 1096603X，2005，学术出版社。
- [24]。Do MN，Vetterli M，'轮廓小波变换：一种高效的方向性多分辨率图像表示'，*IEEE图像处理汇刊*，14(12): 2091–2106，ISSN: 1057-7149，2005，IEEE。
- [25]。Poovizhi S，Ganesh Babu TR，'使用Bendlet变换和支持向量机的高效皮肤癌诊断系统'，*巴西科学院年鉴（Annals of the Brazilian Academy of Sciences）*，92(1): 1–12，2020。

Taylor & Francis

Taylor & Francis 集团

http://taylorandfrancis.com

## 2 无线通信中基于机器学习的微带天线设计

Ranjana Ray$^{1}$，Moumita Pal$^{2}$，R Umamaheswari$^{3}$，以及 Ishita Banerjee$^{4}$

$^{1}$助理教授，电子与通信工程系，JIS工程学院

$^{2}$助理教授，电子与通信工程系，JIS工程学院

$^{3}$助理教授，电子与仪表工程系，SRM Valliammai 工程学院

$^{4}$研究学者，Dayananda Sagar 技术与管理学院

### 2.1 引言

使用微带天线的核心优势在于它们具有高功率增益和全向辐射模式，这在移动通信等应用中特别有用，因为移动服务需要宽带频率操作，并且这些天线适合提高其服务提供的准确性。对于通过移动通信应用提供的多种应用级服务，实现印刷电路天线是一个关键的设计问题。

准确性也是这类设计案例中需要考虑的主要因素。有多个参数决定了天线的性能，例如微带天线的贴片尺寸。微带天线设计中使用的制造技术简单且成本低廉 [1,2]。例如，光刻机制是制造微带天线的另一种方法，通常被称为贴片（patch），其中正方形、六边形、矩形、梯形等各种贴片图案和形状常被使用。在本章中，我们提出了一种人工神经网络（ANN）建模方法，用于微带天线的综合与分析。因此，天线是一种辐射装置，能够在期望的方向辐射电磁能量，其中使用了全向、半定向和定向天线。天线用于将发射器提供的射频信号在自由空间中重新定向到接收器 [3]。天线需要覆盖各种频带或宽频段。预计天线尺寸应该较小，并且其性能可能受到安装装置几何形状变化的影响 [4]。如今，对低成本天线的需求可以通过天线的小型化和压缩架构来满足。与补充天线（如其他类型天线）相比，微带天线有许多优点，例如重量轻、成本低、轮廓低、散射截面小，具有特定的馈电方式可选的圆形和线性极化，并且可以简单地集成到微波电路中 [5]。有许多用于研究微带天线的程序，其中一些流行的程序包括传输线模型、全波方法和腔体模型。在所有模型中，最早的微带天线模型是传输线模型，因为它具有良好的物理洞察力，该天线的设计程序假设了基底的介电常数（`epsilon_r`）、谐振频率 (`f`) 和基底高度 (`h`) 等信息 [6]。微带天线根据一系列双辐射收缩孔径定义，高度为 `h`，宽度为 `w`，植入 `L` 距离。天线设计程序如下：为了在实际情况下获得更好的辐射效率而找到贴片宽度，我们遵循公式 (2.1)。

$$ w = \frac{c}{2f\sqrt{\frac{\epsilon_r+1}{2}}} = \frac{c}{2f}\sqrt{\frac{2}{\epsilon_r+1}} \quad (2.1) $$

这里 `c` 是自由空间中的光速 (`3 \times 10^8` m/s)，`f` 是谐振频率。

当 `w/h > 1` 时，天线有效介电常数由公式 (2.2) 给出。

$$ \epsilon_{reff} = \frac{\epsilon_r+1}{2} + \frac{\epsilon_r-1}{2}\frac{1}{\sqrt{1+12\frac{h}{w}}} \quad (2.2) $$

贴片宽度和长度通过公式 (2.3) 和 (2.4) 计算。

$$ w' = \frac{c}{2f_r}\sqrt{\frac{2}{\epsilon_r+1}} \quad (2.3) $$
