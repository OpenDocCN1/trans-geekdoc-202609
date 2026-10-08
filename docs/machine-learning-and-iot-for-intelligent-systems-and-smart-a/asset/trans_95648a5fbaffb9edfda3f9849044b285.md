

![](img/93c6e2919cb9917d1bdd8f6271e04df4_183_0.png)
![](img/93c6e2919cb9917d1bdd8f6271e04df4_183_1.png)
![](img/93c6e2919cb9917d1bdd8f6271e04df4_183_2.png)

**图 10.3** (a) 原始图像，(b) 预处理后的图像。(c) 原始图像直方图，(d) 预处理后图像直方图。

![](img/93c6e2919cb9917d1bdd8f6271e04df4_184_0.png)
![](img/93c6e2919cb9917d1bdd8f6271e04df4_184_1.png)

![](img/93c6e2919cb9917d1bdd8f6271e04df4_185_0.png)
![](img/93c6e2919cb9917d1bdd8f6271e04df4_185_1.png)
![](img/93c6e2919cb9917d1bdd8f6271e04df4_185_2.png)

**图 10.5** (a) 原始图像，(b) 预处理后的图像，(c) 原始图像直方图，(d) 预处理后图像直方图。

![](img/93c6e2919cb9917d1bdd8f6271e04df4_186_0.png)
![](img/93c6e2919cb9917d1bdd8f6271e04df4_186_1.png)
![](img/93c6e2919cb9917d1bdd8f6271e04df4_186_2.png)
![](img/93c6e2919cb9917d1bdd8f6271e04df4_186_3.png)

**图 10.6** (a) 原始图像，(b) 预处理后的图像，(c) 原始图像直方图，(d) 预处理后图像直方图。

使用带 SoftMax 的输出层。如图 10.7 所示，输入图像被调整大小为 299 × 299 × 3。

### 10.3.1 模型摘要

该模型使用 21m 可训练参数进行训练。

总参数：21,810,980
可训练参数：21,776,548
不可训练参数：34,432

### 10.3.2 示例图像

图 10.8 展示了利用迁移学习进行黑色素瘤检测系统训练和测试的图像数据集。

## 10.4 通过所提议流程获得的精度结果

图 10.9 展示了利用迁移学习获得的黑色素瘤检测系统的训练准确率水平和验证准确率水平。

### 10.4.1 通过所提议流程获得的损失结果

图 10.10 展示了利用迁移学习的黑色素瘤检测系统的训练损失水平和验证损失水平。

### 10.4.2 混淆矩阵

验证数据的混淆矩阵热力图如图 10.11 所示。在 360 个良性样本中，327 个被正确预测；在 300 个恶性样本中，272 个被预测为恶性。

### 10.4.3 分类报告

表 10.1 列出了异常图像分类为良性和恶性的分类结果，基于精确度、召回率、F1 分数和支持度，展示了分类准确率、宏平均和加权平均。

## 10.5 结论

从所提出的模型中，获得了 91% 的召回率分数。由于医疗系统是高召回率系统，这意味着患有恶性肿瘤的人不应被预测为良性病例，因为这会导致该人可能不会寻求进一步治疗。通过图像增强和获取更多图像样本，将来可以获得更好的召回率分数。

![](img/93c6e2919cb9917d1bdd8f6271e04df4_188_0.png)

![](img/93c6e2919cb9917d1bdd8f6271e04df4_189_0.png)

**图 10.8** 黑色素瘤视觉表现。

![](img/93c6e2919cb9917d1bdd8f6271e04df4_189_1.png)

**图 10.9** 获得的训练准确率为 0.99，验证准确率为 0.92。

![](img/93c6e2919cb9917d1bdd8f6271e04df4_190_0.png)

**图 10.10** 获得的训练损失为 0.01，验证损失为 0.3。

![](img/93c6e2919cb9917d1bdd8f6271e04df4_190_1.png)

**图 10.11** 混淆矩阵。

## 表 10.1
分类报告

|          | 精确度 | 召回率 | F1 分数 | 支持度 |
| :---     | :-------- | :----- | :------- | :------ |
| 良性   | 0.92      | 0.91   | 0.91     | 360     |
| 恶性| 0.89      | 0.91   | 0.90     | 300     |
| 准确率 |           |        | 0.91     | 660     |
| 宏平均 | 0.91 | 0.91   | 0.91     | 660     |
| 加权平均 | 0.91 | 0.91   | 0.91     | 660     |

## 参考文献

1. Wu, J., “Efficient Hik SVM Learning for Image Classification”, IEEE Transactions on Image Processing, Vol. 21, No. 10, October 2012.
2. Wang, F. and Wang, F., “Rapidly Void Detection in TSVS with 2-D X-Ray Imaging and Artificial Neural Networks”, IEEE Transactions on Semiconductor Manufacturing, Vol. 27, No. 2, May 2014.
3. Bianchini, M. and Scarselli, F., “On the Complexity of Neural Network Classifiers: A Comparison Between Shallow and Deep Architectures”, IEEE Transactions on Neural Networks and Learning Systems, Vol. 25, No. 8, August 2014.
4. Nasir, M., Attique Khan, M., Sharif, M., Lali, U., Saba, T., and Iqbal, T., “An Improved Strategy for Skin Lesion Detection and Classification Using Uniform Segmentation and Feature Selection-Based Approach”, Microscopy Research and Technique, Vol. 81, No. 6, 528–543, 2018.
5. Banerjee, I., “Brain Tumor Image Segmentation and Classification using SVM, CLAHE and ARKFCM”, Intelligent Decision Support Systems, Applications in Signal Processing, pp. 53–70, De Gruyter, Germany, October 2019.
6. Lu, L., Di, L., Sr and Ye, Y., “A Decision-Tree Classifier for Extracting Transparent Plastic-Mulched Landcover from Landsat-5 TM Images”, IEEE Journal of Selected Topics in Applied Earth Observations and Remote Sensing, Vol. 7, No. 11, November 2014.
7. Divya, D. and Ganesh Babu, T.R., “Fitness Adaptive Deer Hunting-Based Region Growing and Recurrent Neural Network for Melanoma Skin Cancer Detection”, International Journal of Imaging Systems and Technology, Vol. 30, No. 3, 731–752, 2020, ISSN 0899-9457, E-ISSN 1098-1098, DOI: 10.1002/ima.22414.
8. Li, C.-H., Kuo, B.-C., Lin, C.-T. and Huang C.-S., “A Spatial–Contextual Support Vector Machine for Remotely Sensed Image Classification”, IEEE Transactions on Geoscience and Remote Sensing, Vol. 50, No. 3, March 2012.
9. Ananthajothi, K. and Subramanian, M., “Multi-level Incremental Influence Measure-Based Classification of Medical Data for Improved Classification”, Cluster Computing, Vol. 13, No. 5, 783–789, 2018. Col. 10.1007/s10586-018-2498-z.
10. Silva, C.S. and Marcal, A.R., “Colour-Based Dermoscopy Classification of Cutaneous Lesions: An Alternative Approach”, Computer Methods in Biomechanics and Biomedical Engineering: Imaging & Visualization, Vol. 1, No. 4, 211–224, 2013.
11. Mendonça, T., Ferreira, P.M., Marques, J.S., Marcal, A.R. and Rozeira, J., “PH 2-A Dermoscopy Image Database for Research and Benchmarking”, in 2013 35th Annual International Conference of the IEEE Engineering in Medicine and Biology Society (EMBC) (pp. 5437–5440), July 2013. IEEE.
12. Yap, J., Yolland, W. and Tschandl, P., “Multimodal Skin Lesion Classification Using Deep Learning”, Experimental Dermatology, Vol. 27, No. 11, 1261–1267, 2018.
13. Jaworek-Korjakowska, J. and Tadesiewicz, R., “Determination of Border Irregularity in Dermoscopy Color Images of Pigmented Skin Lesions”, in Conference Proceedings: Annual International Conference of the IEEE Engineering in Medicine and Biology Society. IEEE Engineering in Medicine and Biology Society. Annual Conference (Vol. 2015, pp. 2665–2668), August 2015.
14. Poovizhi, S. and Ganesh Babu, T.R., “An Efficient Skin Cancer Diagnostic System Using Bendlet Transform and Support Vector Machine”, Annals of Brazilian Academy of Sciences, Vol. 92, No. 1, 1–12, 2020.
15. Jain, Y.K., “Comparison Between Different Classification Methods with Application to Skin Cancer”, International Journal of Computer Applications, Vol. 53, No. 11, September 2012.
16. Dash, S., Senapati, M.R. and Jena, U.R., “K-NN Based Automated Reasoning Using Bilateral Filter-Based Texture Descriptor for Computing Texture Classification”, Egyptian Informatics Journal, Vol. 19, No. 2, 133–144, 2018.
17. Ruela, M., Barata, C., Marques, J.S. and Rozeira, J., “A System for the Detection of Melanomas in Dermoscopy Images Using Shape and Symmetry Features”, Computer Methods in Biomechanics and Biomedical Engineering: Imaging & Visualization, Vol. 5, No. 2, 127–137, 2017.
18. Umbaugh, S.E., Moss, R.H., Stoecker, W.V. and Hance, G.A., “Automatic Colour Segmentation Algorithms with Application to Skin Tumour Feature Identification”, IEEE Engineering in Medicine and Biology, Vol. 12, 75–82, 1993.
19. Barhoumi, W. and Bâzaoui, A., “Pigment Network Detection in Dermatoscopic Images for Melanoma Diagnosis”, IRBM, Vol. 35, No. 3, 128–138, 2014.
20. El Abadi, N.K. and Faisal, Z., “Detection and Analysis of Skin Cancer from Skin Lesions”, International Journal of Applied Engineering Research, Vol. 12, No. 19, 9046–9905, 2017.
21. Codella, N., Nguyen, Q.-B., Pankanti, S., Gutman, D., Helba, B., Halpern, A. and Smith, J.R., “Deep Learning Ensembles for Melanoma Recognition in Dermoscopy Images”, IBM Journal of Research and Development, Vol. 61, 1–15, 2017. 10.1147/JRD.2017.2708299.
22. Sheha, M.A., “Automatic Detection of Melanoma Skin Cancer Using Texture Analysis”, International Journal of Computer Applications, Vol. 42, No. 20, 22–26, 2012.
23. Mabrouk, M.S., Sheha, M.A. and Sharawy, A., “Automatic Detection of Melanoma Skin Cancer Using Texture Analysis”, International Journal of Computer Applications, Vol. 42, No. 20, 22–26, 2012.
24. Argenziano, G., Soyer, H.P., Chimenti, S., Talamini, R., Corona, R., Sera, F., et al., “Dermoscopy of Pigmented Skin Lesions: Results of a Consensus Meeting Via the Internet”, Journal of the American Academy of Dermatology, Vol. 48, 679–693, 2003.
25. Saida, T., Miyazaki, A., Oguchi, S., Ishihara, Y., Yamazaki, Y. and Murase, S., “Significance of Dermoscopic Patterns in Detecting Malignant Melanoma on Acal Volar Skin”, Archives of Dermatology, Vol. 140, 1233–1238, 2004.
26. Jayapal, P., Manikandan, R., Ramanan, M., Shiyam Sundar, R.S. and Udhyaya Suriya, T.S., “Skin Lesion Classification Using Hybrid Spatial Features and Radial Basis Network”, International Journal of Innovative Research in Science, Engineering and Technology, Vol. 3, No. 3, 10014–10021, 2014.
27. Fatima, R., Khan, M.Z.A., Govardhan, A. and Dhruve, K.D., “Computer Aided

