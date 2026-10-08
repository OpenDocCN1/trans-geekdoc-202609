

![](img/93c6e2919cb9917d1bdd8f6271e04df4_31_0.png)

## **图 1.13** KNN 分类器性能。

通过对比结果可以明显看出，从分解第二层提取的 100 个系数比来自任意分解层的 75 个系数具有更好的性能准确率。

在工作 II 中，Poovizhi 等人 [23] 使用 bendlet 变换进行特征提取，并采用支持向量机（SVM）作为分类器，以展示如何对 PH2 数据集中的正常和异常图像进行分类。该提出的工作被与 1.3 节中讨论的其他图像分解方法进行比较。首先，通过中值滤波方法对皮肤镜图像进行预处理，以去除不必要的噪声和毛发。统计特征（如纹理描述符）通过 bendlet 分解提取。能量是从 bendlet 变换获得的子带系数中计算得出的。然后，这些特征被输入到支持向量机中，以分类正常和异常图像。（图 1.14）描绘了基于 bendlet 和 SVM 的 SCC 系统的框图。

验证是通过 k 折交叉验证进行的，并测量了敏感性、特异性等性能指标。

- 其中，$T_{r}P_{b}\to$ 真正例（正确分类的异常病例数量），$F_{r}N_{c}\to$ 假阴性（异常病例的错误分类数量），$T_{r}N_{c}\to$ 真阴性（正常病例的正确分类数量）以及 $F_{r}P_{o}\to$ 假阳性（正常病例的错误分类数量）

表 1.3 概述了分类系统在正常和异常图像分类中的性能。计算了分解级别（从 1 到 4）和方向（2, 4, 8, 16, 32）。

从表 1.4 中观察到，具有级别 3 和方向 8 的 bendlet 变换表现最好，准确率为 98.50%，敏感率为 97.50%，特异性为 100%。（图 1.15）描绘了各种图像表示技术的性能。

通过小波、曲线、轮廓、剪切和 bendlet 的性能比较，bendlet 变换在敏感率、特异性和准确性方面优于其他表示系统。

![](img/93c6e2919cb9917d1bdd8f6271e04df4_32_0.png)

### **图 1.14** 基于 Bendlet 和 SVM 的 SCC 系统框图。

## **表 1.3**
**SCC 系统性能指标**

| 性能度量 | 描述 | 公式 |
| :--- | :--- | :--- |
| 敏感率 ($S_n$) | 它是正确预测的真正例数量与实际阳性病例总数之比。 | $S_n = \frac{T_r P_p}{T_r P_r + F_i N_e}$ |
| 特异率 ($S_p$) | 它是正确预测的真阴性数量与阴性病例总数之比。 | $S_p = \frac{T_r N_e}{T_r N_e + F_i P_r}$ |
| 准确率 ($A_c$) | 它定义为正确预测的皮肤癌图像数量占实际病例图像总数的比例。 | $A_c = \frac{T_r P_p + T_r N_e}{T_r P_p + F_i N_e + T_r N_e + F_i P_p}$ |

## 1.5 结论

本研究简要介绍了用于将皮肤镜图像分类为正常和异常图像的各种图像表示系统和分类技术。在工作 I 中，剪切变换和 K-NN 分类器在剪切分解第二层且拥有 100 个系数时给出了 96% 的最高准确率。在工作 II 中，使用 bendlet 变换进行特征提取和 SVM 进行分类，在级别 3 分解和方向 8 时给出了 98.3% 的最高准确率。最后，比较了所有图像表示系统，如小波、curvelet、轮廓、剪切和 bendlet，并测量了如特异性、

## 表 1.4

## 正常和异常相位的分类器性能

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

### **图 1.15** 各种图像表示技术的性能比较。

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

